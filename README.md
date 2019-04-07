# MySQL_Lerning4

4.1 MySQL 实战

## 学习任务

数据导入导出 将之前创建的任意一张MySQL表导出,且是CSV格式 再将CSV表导入数据库

导出:


![WeChat Image_20190407234348](https://user-images.githubusercontent.com/43989688/55690274-68812400-598f-11e9-81a3-76e922a68853.png)


### 项目七: 各部门工资最高的员工（难度：中等）

创建Employee 表，包含所有员工信息，每个员工有其对应的 Id, salary 和 department Id。

+----+-------+--------+--------------+

| Id | Name  | Salary | DepartmentId |

+----+-------+--------+--------------+

| 1  | Joe   | 70000  | 1            |

| 2  | Henry | 80000  | 2            |

| 3  | Sam   | 60000  | 2            |

| 4  | Max   | 90000  | 1            |

+----+-------+--------+--------------+

创建Department 表，包含公司所有部门的信息。

+----+----------+

| Id | Name     |

+----+----------+

| 1  | IT       |

| 2  | Sales    |

+----+----------+

编写一个 SQL 查询，找出每个部门工资最高的员工。例如，根据上述给定的表格，Max 在 IT 部门有最高工资，Henry 在 Sales 部门有最高工资。

+------------+----------+--------+

| Department | Employee | Salary |

+------------+----------+--------+

| IT         | Max      | 90000  |

| Sales      | Henry    | 80000  |

+------------+----------+--------+

答案:

![WeChat Image_20190407205700](https://user-images.githubusercontent.com/43989688/55688366-036e0400-5978-11e9-8c1c-fa52a94f1cc0.png)

### 项目八: 换座位（难度：中等）
小美是一所中学的信息科技老师，她有一张 seat 座位表，平时用来储存学生名字和与他们相对应的座位 id。其中纵列的 id 是连续递增的 小美想改变相邻俩学生的座位。你能不能帮她写一个 SQL query 来输出小美想要的结果呢？请创建如下所示seat表：

示例：

+---------+---------+

|    id   | student |

+---------+---------+

|    1    | Abbot   |

|    2    | Doris   |

|    3    | Emerson |

|    4    | Green   |

|    5    | Jeames  |

+---------+---------+

假如数据输入的是上表，则输出结果如下：

+---------+---------+

|    id   | student |

+---------+---------+

|    1    | Doris   |

|    2    | Abbot  |

|    3    | Green   |

|    4    | Emerson |

|    5    | Jeames  |

+---------+---------+

注意：如果学生人数是奇数，则不需要改变最后一个同学的座位。

项目九:  分数排名（难度：中等）

编写一个 SQL 查询来实现分数排名。如果两个分数相同，则两个分数排名（Rank）相同。请注意，平分后的下一个名次应该是下一个连续的整数值。换句话说，名次之间

不应该有“间隔”。创建以下score表：

+----+-------+

| Id | Score |

+----+-------+

| 1  | 3.50  |

| 2  | 3.65  |

| 3  | 4.00  |

| 4  | 3.85  |

| 5  | 4.00  |

| 6  | 3.65  |

+----+-------+

例如，根据上述给定的 Scores 表，你的查询应该返回（按分数从高到低排列）：

+-------+------+

| Score | Rank |

+-------+------+

| 4.00  | 1    |

| 4.00  | 1    |

| 3.85  | 2    |

| 3.65  | 3    |

| 3.65  | 3    |

| 3.50  | 4    |

+-------+------+

答案: ![WeChat Image_20190407221301](https://user-images.githubusercontent.com/43989688/55689236-61074e00-5982-11e9-9f13-7713f683bb69.png)

注意: 用as新命名rank的时候 加单引号 否则会syntax报错！！！！！！！！！！！

## 4.2 MySQL 实战 - 复杂项目

### 作业

项目十：行程和用户（难度：困难）

Trips 表中存所有出租车的行程信息。每段行程有唯一键 Id，Client_Id 和 Driver_Id 是 Users 表中 Users_Id 的外键。Status 是枚举类型，枚举成员为 

(‘completed’, ‘cancelled_by_driver’, ‘cancelled_by_client’)。

+----+-----------+-----------+---------+--------------------+----------+

| Id | Client_Id | Driver_Id | City_Id |        Status      |Request_at|

+----+-----------+-----------+---------+--------------------+----------+

| 1  |     1     |    10     |    1    |     completed      |2013-10-01|

| 2  |     2     |    11     |    1    | cancelled_by_driver|2013-10-01|

| 3  |     3     |    12     |    6    |     completed      |2013-10-01|

| 4  |     4     |    13     |    6    | cancelled_by_client|2013-10-01|

| 5  |     1     |    10     |    1    |     completed      |2013-10-02|

| 6  |     2     |    11     |    6    |     completed      |2013-10-02|

| 7  |     3     |    12     |    6    |     completed      |2013-10-02|

| 8  |     2     |    12     |    12   |     completed      |2013-10-03|

| 9  |     3     |    10     |    12   |     completed      |2013-10-03| 

| 10 |     4     |    13     |    12   | cancelled_by_driver|2013-10-03|

+----+-----------+-----------+---------+--------------------+----------+

Users 表存所有用户。每个用户有唯一键 Users_Id。Banned 表示这个用户是否被禁止，Role 则是一个表示（‘client’, ‘driver’, ‘partner’）的枚举类型。

+----------+--------+--------+

| Users_Id | Banned |  Role  |

+----------+--------+--------+

|    1     |   No   | client |

|    2     |   Yes  | client |

|    3     |   No   | client |

|    4     |   No   | client |

|    10    |   No   | driver |

|    11    |   No   | driver |

|    12    |   No   | driver |

|    13    |   No   | driver |

+----------+--------+--------+

写一段 SQL 语句查出 2013年10月1日 至 2013年10月3日 期间非禁止用户的取消率。基于上表，你的 SQL 语句应返回如下结果，取消率（Cancellation Rate）保留
两位小数。

+------------+-------------------+

|     Day    | Cancellation Rate |

+------------+-------------------+

| 2013-10-01 |       0.33        |

| 2013-10-02 |       0.00        |

| 2013-10-03 |       0.50        |

+------------+-------------------+

答案(sqly语句); 
select request_at,round(sum(case when status="completed" then 0 else 1 end)/count(*),2) from

(select * from Trips

where client_id not in (select users_id from Users where banned = "yes" and role = "client") and request_at >= "2013-10-01" and 

request_at <= "2013-10-03") t

group by request_at order by request_at asc;

![WeChat Image_20190407233105](https://user-images.githubusercontent.com/43989688/55690108-4ab2bf80-598d-11e9-9049-99509811931c.png)




