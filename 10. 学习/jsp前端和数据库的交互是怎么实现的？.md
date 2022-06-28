jsp前端和数据库的交互是怎么实现的？

JDBC是用于连接数据库的程序接口，主要功能有：与数据库建立连接、向数据库发送SQL语句、处理发送的SQL语句、将处理的结果进行返回。具体步骤为：
1、通过Class类中的forName()方法加载数据库驱动程序，加载驱动后用DriverManager类的getConnection()的方法获取数据库的连接；
2、取得数据库连接对象后，就可以通过Statement类的execteQuery()或execteUpdate()方法发送SQL语句；
3、创建一个Java文件，定义与数据库中对应的属性；
4、前端输入数据后发送给另一个文件，该文件创建一个JavaBean对象和几个属性，并将上一个文件的数据赋值给JavaBean对象中的属性；
5、最后让该JavaBean对象调用execteQuery("sql语句")或execteUpdate("sql语句")方法，实现对数据库的增删改，这样一个前后端交互就实现了。