Integer类作为int的包装类，能存储的最大整型值为2<sup>31</sup>-1，Long类也是有限的， 最大为2<sup>63</sup>-1。如果要表示再大的整数，不管是基本数据类型还是他们的包装类 都无能为力，更不用说进行运算了。

java.math包的BigInteger可以表示不可变的任意精度的整数。BigInteger 提供 所有 Java 的基本整数操作符的对应物，并提供 java.lang.Math 的所有相关方法。 另外，BigInteger 还提供以下运算：模算术、GCD 计算、质数测试、素数生成、 位操作以及一些其他操作。

