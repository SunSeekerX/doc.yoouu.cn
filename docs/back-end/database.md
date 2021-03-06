# 💿 Data base

## Common

### SQL naming convention

- **小写**。标识符应该全部用小写字母来书写，使用`first_name`，不是`"First_Name"或者"FirstName"`。
- **数据类型不是名称**。避免使用仅为数据类型的名字（如`text`或`timestamp`）。
- **强调单独的单词**。由多个单词组成的对象名称应该用下划线分隔，例如使用`word_count`或`team_member_id`，而不是`wordcount`或`wordCount`。
- **完整的单词，而不是缩写**。例如使用`middle_name`，不是`mid_nm`。
- **使用常用缩写**。对于几个长词而言，缩写词比词本身更为常见，比如`i18n`和`l10n`，这时使用缩写。

## mysql

> 关于`MySQL`

### 开放远程连接

```bash
# 登录mysql
mysql -u root -p
mysql -u root -p

　　mysql>use mysql;

　　mysql>select 'host' from user where user='root';

　　mysql>update user set host = '%' where user ='root';

　　mysql>flush privileges;

　　mysql>select 'host'　 from user where user='root';

　　第一句是以权限用户root登录

　　第二句：选择mysql库

　　第三句：查看mysql库中的user表的host值（即可进行连接访问的主机/IP名称）

　　第四句：修改host值（以通配符%的内容增加主机/IP地址），当然也可以直接增加IP地址

　　第五句：刷新MySQL的系统权限相关表

　　第六句：再重新查看user表时，有修改。。
```

## mariaDB

### 开放远程链接

```sql
GRANT ALL PRIVILEGES ON *.* TO 'root'@'%'IDENTIFIED BY '123456' WITH GRANT OPTION;

-- 说明：root是登陆数据库的用户，123456是登陆数据库的密码，*就是意味着任何来源任何主机反正就是权限很大的样子。

-- 最后配置好权限之后不应该忘记刷新使之生效

flush privileges;
```
