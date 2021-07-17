##### 测试连接

```java
public class JedisDemo1 {
    public static void main(String[] args) {
        Jedis jedis = new Jedis("101.132.79.245",6379);
        jedis.auth("wl14138");
        String ping = jedis.ping();
        System.out.println(ping);
    }
}
```





##### 手机验证码实例

```java
import redis.clients.jedis.Jedis;

import java.util.Random;

/**
 * @ProjectName: Redis
 * @Package: com.sm.jedis
 * @ClassName: PhoneCode
 * @Author: krato
 * @Description: 手机六位验证码
 * @Date: 2021/7/15 20:28
 * @Version: 1.0
 */
public class PhoneCode {

    public static void main(String[] args) {
        //模拟验证码发送
        verifyCode("12345678");
        //getRedisCode("12345678","164709");
    }

    //1.生成6位验证码
    public static String getCode(){
        Random random = new Random();
        String code = "";
        for (int i = 0; i < 6; i++) {
            int i1 = random.nextInt(10);
            code += i1;
        }
        return code;
    }
    //2.每个手机每天只能发三次，验证码放到redis中，设置过期时间
    public static void verifyCode(String phone){
        Jedis jedis = new Jedis("101.132.79.245",1113);
        jedis.auth("******");

        //手机发送次数key
        String countKey = "VerifyCode" + phone + ":count";
        //验证码key
        String codeKey = "VerifyCode" + phone + ":code";

        //一个手机号只能验证三次
        String count = jedis.get(countKey);
        if (count == null) {
            jedis.setex(countKey,24*60*60,"1");
        }else if (Integer.parseInt(count) <= 2){
            jedis.incr(countKey);
        }else if (Integer.parseInt(count) > 2){
            System.out.println("该手机号已经发送过三次");
            jedis.close();
        }
        //验证码存入redis
        jedis.setex(codeKey,120,getCode());
        jedis.close();
    }

    //3.验证码校验
    public static void getRedisCode(String phone,String inputCode){
        Jedis jedis = new Jedis("101.132.79.245",1113);
        jedis.auth("wl14138");

        String redisCode = jedis.get("VerifyCode" + phone + ":code");
        if (redisCode.equals(inputCode)) System.out.println("success");
        else System.out.println("failed");

        jedis.close();
    }
}

```

