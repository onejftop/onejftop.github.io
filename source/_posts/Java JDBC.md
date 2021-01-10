---
title: Java JDBC
tags:
  - Java
categories:
  - Java
abbrlink: 92858b10
date: 2020-12-22 12:13:16
---

## Java与SQL对应数据类型转换表

| Java类型           | SQL类型                  |
| ------------------ | ------------------------ |
| boolean            | BIT                      |
| byte               | TINYINT                  |
| short              | SMALLINT                 |
| int                | INTEGER                  |
| long               | BIGINT                   |
| String             | CHAR,VARCHAR,LONGVARCHAR |
| byte   array       | BINARY  ,    VAR BINARY  |
| java.sql.Date      | DATE                     |
| java.sql.Time      | TIME                     |
| java.sql.Timestamp | TIMESTAMP                |

## jdbc.properties配置文件(位于src下)

```java
url=jdbc:mysql://localhost:3306/jdbc?serverTimezone=GMT
username=root
password=onejftop
driver=com.mysql.cj.jdbc.Driver
```

## JdbcUtils.class

```java
public class JdbcUtils {

    /**
     * 获取连接
     * @return 连接
     */
    public static Connection getConnection(){
       Connection connection = null;
        try {
            // 加载配置文件
            InputStream is = JdbcUtils.class.getClassLoader().getResourceAsStream("jdbc.properties");
            Properties properties = new Properties();
            properties.load(is);
            // 读取配置文件信息
            String driverName = properties.getProperty("driverName");
            String url = properties.getProperty("url");
            String username = properties.getProperty("username");
            String password = properties.getProperty("password");
            // 加载驱动
            Class.forName(driverName);
            // 获取连接
            connection = DriverManager.getConnection(url,username,password);
        } catch (Exception e) {
            e.printStackTrace();
        }
        return connection;
    }

    /**
     * 关闭所有资源
     * @param connection
     * @param statement
     * @param rs
     */
    public static void closeAll(Connection connection, Statement statement, ResultSet rs){
        if (rs != null){
            try {
                rs.close();
            } catch (SQLException e) {
                e.printStackTrace();
            }
        }
        if (statement != null){
            try {
                statement.close();
            } catch (SQLException e) {
                e.printStackTrace();
            }
        }
        if (connection != null){
            try {
                connection.close();
            } catch (SQLException e) {
                e.printStackTrace();
            }
        }
    }
}
```

## BaseDao接口

```java
public interface BaseDao {

    /**
     * 通用的增、删、改操作（体现一：增、删、改 ； 体现二：针对于不同的表）
     * @param sql
     * @param args
     */
    public void update(String sql,Object ... args);
    
    /**
     * 针对一个表的通用查询操作
     */
    public User queryForUser(String sql,Object ... args);
}
```

## BaseDaoImpl实现类

```Java
public class BaseDaoImpl implements BaseDao {
    @Override
    public void update(String sql, Object... args) {
        Connection connection = null;
        PreparedStatement ps = null;
        try {
            // 获取连接
            connection = JdbcUtils.getConnection();
            // 获取PreparedStatement的实例
            ps = connection.prepareStatement(sql);
            // 填充占位符
            for (int i=0;i<args.length;i++){
                ps.setObject(i+1,args[i]);
            }
            // 执行sql语句
            ps.execute();
        } catch (SQLException e) {
            e.printStackTrace();
        }finally {
            JdbcUtils.closeAll(connection,ps,null);
        }
    }
    
    @Override
    public User queryForUser(String sql, Object... args) {
        Connection connection = null;
        PreparedStatement ps = null;
        ResultSet rs = null;
        try {
            // 获取连接
            connection = JdbcUtils.getConnection();
            // 获取PreparedStatement的实例
            ps = connection.prepareStatement(sql);
            // 填充占位符
            for (int i=0;i<args.length;i++){
                ps.setObject(i+1,args[i]);
            }
            // 执行sql语句
            rs = ps.executeQuery();
            // 获取结果集的元数据
            ResultSetMetaData rsmd = rs.getMetaData();
            // 通过ResultSetMetaData获取结果集中的列数
            int columnCount = rsmd.getColumnCount();
            if (rs.next()){
                User user = new User();
                // 处理结果集一行数据中的每一个列
                for (int i=0;i<columnCount;i++){
                    // 获取列值
                    Object columnValue = rs.getObject(i+1);
                    // 获取每个列的列名
                    String columnName = rsmd.getColumnName(i+1);
                    // 给user对象指定的columnName属性，赋值为columnValue：通过反射
                    Field field = User.class.getDeclaredField(columnName);
                    field.setAccessible(true);
                    field.set(user,columnValue);
                }
                return user;
            }
        } catch (Exception e) {
            e.printStackTrace();
        } finally {
            JdbcUtils.closeAll(connection,ps,rs);
        }
        return null;
    }
}
```