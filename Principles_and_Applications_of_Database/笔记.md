# 第一章 绪论

## 1.数据库概念

数据库是一种依照特定**数据模型**， **组织、 存储和管理数据的文件集合**。

## 2.数据模型概念

数据模型是指描述事物对象的**数据结构组成**、**数据语义联系**、**数据约束的抽象结构及其说明**。

**数据模型构成：数据结构、数据操作、数据约束**

## 3.**经典数据模型**

① 层次模型（树）②网状模型（网）③ 关系模型（**表**）

## 4.数据库系统

数据库系统是由**数据库**、**数据库管理系统**（DBMS）、**应用程序**、数据库管理员和**数据库用户**组成的集成系统。

## 5.数据库应用系统

### 1.类型

业务处理系统，管理信息系统，决策支持系统

### 2.结构

单机用户结构，集中式结构，客户/服务器结构，分布式结构

### 3.生命周期

需求分析，系统设计，系统实现，系统测试，系统运行与维护

## 6.数据库管理系统

数据库管理系统（DBMS）是用于管理和操作数据库的软件工具，它们提供了<u>数据库定义、数据操作访问、数据库运行控制、数据组织与存储、数据库运维、数据库通信和数据库安全</u>等方面的支持，以满足不同应用场景和需求的数据库管理需求

### 类型

按用途分类：通用，专用领域

按用户数分类：单用户，多用户

按系统部署分类：集中式，分布式

按使用场景分类：桌面级，企业级

按软件版权分类：产品，开源

# 第二章 关系数据模型

## 1.关系的概念

**关系**（relation）——是指具有关系特征、用于存放实体数据的**二维表**。关系也常被称为关系表。

<img src="\Snipaste_2024-05-12_14-57-45.png" style="zoom:60%;" /> 

## 2.关系特征

表中**每行**存储**一个**数据
表中**每列**包含**一项**数据
表中单元格只能存储单个值
**不允许有重复的行**
**不允许有重复的列**
列顺序可任意
行顺序可任意

<img src="\Snipaste_2024-05-12_15-03-31.png" style="zoom:60%;" /> 未满足每行一个数据

<img src="\Snipaste_2024-05-12_15-03-59.png" style="zoom:60%;" /> 未满足一列中条目类型一致

## 3.笛卡尔积

设D1、D2、…、Dn是n个域, 则它们的笛卡尔积为
D1xD2x…xDn={(d1，d2，…，dn) | di 属于 Di， i=1,2,…,n}
其中每一个元素称为一个n元组(n-tuple), 简称元组;元组中的每个值di称为一个分量(component)

<img src="\Snipaste_2024-05-12_15-12-02.png" style="zoom:60%;" /> <img src="\Snipaste_2024-05-12_15-12-11.png" style="zoom:60%;" /> 

## 4.键

复合键（Compound Key）——是指关系中用来**唯一标识**元组的**<u>多列</u>**作为键

候选键（Candidate Key）——关系中可能有**多个列均适合作为键**，将其中每个都称为候选键。

主键（Primary key）是关系表中最有代表性的一个候选键，每个关系表中只能定义**一个**主键。

代理键——采用DBMS**自动生成**的数字序列作为关系表的**主键**（可替代复合主键，以便获得更高性能的数据访问操作处理。 ）

主键作用：
 唯一标识关系表的**每行**（元组）
 与关联表的**外键**建立联系，实现关系表之间连接
 数据库文件使用主键值来**组织**关系表的数据存储
 数据库使用主键索引快速**检索**数据

## 5.关系模式语句

关系名（主键属性，属性2，…，属性x）

## 6.完整性约束

### 1.实体完整性

使每个元组都是可识别和唯一的------通过设置**主键**，主键应非空且唯一

### 2.参照完整性

若关系R中的外键F与关系S中的主键K相关联，则R中**外键F值必须与S中主键K值一致**

### 3.用户自定义完整性

指**用户**根据具体业务对数据处理规则要求所**定义**的数据约束。

## 7.数据操作（关系运算）

相容：有相同属性组成

### 1.并（相容）

<img src="\Snipaste_2024-05-12_16-08-58.png" style="zoom:60%;" /> 

### 2.差（相容）

<img src="\Snipaste_2024-05-12_16-09-48.png" style="zoom:60%;" /> 

### 3.交（相容）

<img src="\Snipaste_2024-05-12_16-10-15.png" style="zoom:60%;" /> 

### 4.笛卡尔积

<img src="\Snipaste_2024-05-12_16-11-49.png" style="zoom:60%;" /> 

<img src="\Snipaste_2024-05-12_16-11-55.png" style="zoom:60%;" /> 

### 5.选择，投影

<img src="\Snipaste_2024-05-12_16-20-40.png" style="zoom:60%;" /> 

### 6.连接

<img src="\Snipaste_2024-05-12_16-29-45.png" style="zoom:60%;" /> 

<img src="\Snipaste_2024-05-12_16-29-54.png" style="zoom:60%;" /> 

<img src="\Snipaste_2024-05-12_16-30-01.png" style="zoom:60%;" /> 

<img src="\Snipaste_2024-05-12_16-30-06.png" style="zoom:60%;" /> 

### 7.除

<img src="\Snipaste_2024-05-12_16-48-41.png" style="zoom:60%;" /> 

# 第三章 数据库SQL语言

## 1.SQL语言特点

一体化
使用方式灵活
非过程化
语言语句简单

## 2.SQL语言语句类型

### 1.数据定义语言

CREATE DATABASE - 创建新数据库
DROP DATABASE – 删除数据库
ALTER DATABASE - 修改数据库属性 
CREATE TABLE - 创建新表 
ALTER TABLE – 修改数据库表结构
DROP TABLE - 删除表
CREATE INDEX - 创建索引
DROP INDEX - 删除索引 

#### (1)数据库

1).**CREATE DATABASE** CourseDB;
2).**ALTER DATABASE** CourseDB **RENAME TO** CourseManageDB;
3).**DROP DATABASE** CourseManageDB；

#### (2)表

##### 1).创建表

**CREATE  TABLE**  Course
( CourseID  		char(4)     	 **PRIMARY  Key**,
  CourseName  	varchar(20) 	 **NOT  NULL**  **UNIQUE**,
  CourseType  	varchar(10) 	 NULL **CHECK(CourseType IN('基础课','专业课','选修课'))**,
  CourseCredit  	smallint   	 NULL,
  TestMethod  	char(4)    		 NOT  NULL  **DEFAULT  '闭卷考试**'
);

##### 2).表约束定义主键

###### 使用表约束定义主键的优点：

便于定义**复合主键**
可命名主键约束
便于定义代理键

CREATE  TABLE  Plan
( CourseID  	char(4)  	NOT  NULL,
  TeacherID  	char(4)  	NOT  NULL,
  **CONSTRAINT**	CoursePlan_PK	**PRIMARY Key(CourseID,TeacherID)**
);

##### 3).表约束定义代理键

CREATE  TABLE  Plan
( CoursePlanID	<u>***serial***</u>		NOT  NULL,
  **CONSTRAINT**	CoursePlan_PK	**PRIMARY Key(CoursePlanID)**
);

##### 4).表约束定义外键

CREATE  TABLE  Register
( CourseRegID  	serial	NOT  NULL,
  CoursePlanID  	Int  		NOT  NULL,
  CONSTRAINT	CourseRegID_PK	PRIMARY Key(CourseRegID),
  **CONSTRAINT**	CoursePlanID_FK	**FOREIGN Key**(CoursePlanID)
  **REFERENCES  Plan(CoursePlanID)**         ///来自  表名（属性名）
  **ON DELETE CASCADE,**              ///同删关系
 );

##### 5).修改表

ALTER TABLE <表名> **ADD** <新列名称><数据类型>|[完整性约束];
ALTER TABLE<表名> **DROP COLUMN** <列名>；
ALTER TABLE<表名> **DROP CONSTRAINT**<完整性约束名>;
ALTER TABLE <表名> **RENAME TO** <新表名>；
ALTER TABLE <表名> **RENAME** <原列名> **TO** <新列名>；
ALTER TABLE <表名> **ALTER COLUMN** <列名> **TYPE**<新的数据类型>;

##### 6).删除表

**DROP TABLE** Register;

#### (3)索引

**CREATE  INDEX**  Birthday_Idx  **ON**  STUDENT （Birthday）；
**ALTER  INDEX**  <索引名> **RENAME TO** <新索引名>；
**DROP  INDEX** bday_idx；

#### (4)视图

**CREATE VIEW** 视图名 **AS**  SELECT查询语句；			//创建视图
**DROP VIEW** 视图名；													//删除视图
**SELECT * FROM** 视图名   [ORDER BY ·······];              //使用视图

##### 视图应用

1.使用视图**简化**复杂SQL查询操作
2.使用视图提高数据访问**安全性**
3.提供一定程度的数据逻辑**独立性**
4.**集中展示**用户所感兴趣的特定数据

补充：

1. 逻辑视图（CREATE VIEW AS ）
不存储实际的数据，而是根据定义的查询语句在查询时动态生成结果。
2. 物化视图（CREATE MATERAILIZED VIEW AS）
创建时会将视图的查询结果实际存储在数据库中，而不是在查询时动态生成。

#### (5)用户

1)**CREATE USER** "userA" **WITH**
    LOGIN
	NOSUPERUSER
	NOCREATEDB
	NOCREATEROLE
	INHERIT
	NOREPLICATION                //数据库复制权限
	CONNECTION LIMIT -1      //连接后保持时间（-1为无限）
	PASSWORD '123456';
2)ALTER USER <用户名> [ [ WITH ] option [ ... ] ];               //修改属性
	ALTER USER <用户名> RENAME TO <新用户名>;          //修改名称
	ALTER USER <用户名> SET <参数项> { TO | = } { value | DEFAULT };     //修改参数
3)DROP USER userA;

#### (6)角色

定义和修改方式和用户一样，表示**一类权限相同的用户集合**

### 2.数据操纵语言

INSERT - 向数据库表中插入数据 
UPDATE - 更新数据库表中的数据
DELETE - 从数据库表中删除数据 

**INSERT INTO** Student   **VALUES**('2017220101105','柳因','女','1999-04-23','软件工程','liuyin@163.com');
**UPDATE** Student  **SET** Email='zhaodong@163.com'  **WHERE** StudentName='赵东';
**DELETE FROM** STUDENT  **WHERE** StudentName='张亮';

### 3.数据查询语言

SELECT - 从数据库表中获取数据

#### (1)单表查询

1.
SELECT [ALL|DISTINCT] <目标列>[，<目标列>…] [ INTO <新表> ]
FROM <表名|视图名>[，<表名|视图名>…]
[ WHERE <条件表达式> ]              				   	 **//WHERE A BETWEEN ··· AND ···/WHERE A LIKE '%@163.com'(>=1)/_(=1)/**                  [ GROUP BY 列名 [HAVING 条件 ]]						**WHERE   A=··· AND B=···/OR/NOT/     WHERE A IN ('···','···')**
[ ORDER BY 列名  [ASC|DESC] ];
2.
SELECT **统计函数(目标列) AS 新名**/目标列 AS 新名        //**使用内置函数**
FROM 表名
[WHERE 条件]
**GROUP BY** 目标列 [Having 条件];                        //**group by和内置函数的使用对应，目标列为select中所有非内置函数使用项** 
3.
SELECT TeacherID, TeacherName, TeacherTitle
FROM Teacher
WHERE CollegeID <u>***IN***</u>     //**子查询**
( SELECT CollegeID
  FROM College
  WHERE CollegeName=‘计算机学院’ );

#### (2)多表查询

1.
SELECT TeacherID, TeacherName, TeacherTitle      //全部来自Teacher
**FROM**          Teacher [AS] **T**,          College [AS] **C**
WHERE T.CollegeID = C.CollegeID and C.CollegeName = ‘计算机学院’);
2.
SELECT **B.**CollegeName AS 学院名称, **A.**TeacherID AS 编号   //**来自两个表，必须加限定**
**FROM**          Teacher [AS] **A**，        College [AS] **B**
WHERE A.CollegeID = B.CollegeID
3.
SELECT        B.CollegeName AS 学院名称,         A.TeacherID AS 编号
FROM         Teacher [AS] A           <u>***JOIN***</u>             College [AS] B        <u>***ON* **</u>          A.CollegeID=B.CollegeID    //**ON后的即为前面WHERE内																																									容**，最后实现的和前面一样
ORDER BY B.CollegeName, A.TeacherID;
4.
SELECT        C.CourseName AS 课程名称,       T.TeacherName AS 教师,         COUNT (R.CoursePlanID) AS 选课人数
FROM             Course AS C              **<u>*JOIN*</u>**             Plan AS P           **<u>*ON*</u>**               C.CourseID=P.CourseID
                                                          *<u>**JOIN**</u>*           Teacher AS T         **<u>*ON*</u>**              P.TeacherID=T.TeacherID
                                                     *<u>**LEFT JOIN**</u>*      Register AS R        **<u>*ON*</u>**          <u>P</u>.CoursePlanID=R.CoursePlanID    //**即使右边的Register																																								没有对应项，左边的Plan也会输出**
GROUP BY C.CourseName, T.TeacherName;

### 4.数据控制语言（权限授予）

GRANT – 授予用户对数据库对象的权限
DENY – 拒绝授予用户对数据库对象的权限
REVOKE – 撤消用户对数据库对象的权限

**GRANT**          SELECT, INSERT, UPDATE, DELETE            **ON**          数据库名           **TO**          用户名/角色名;
**REVOKE**                          DELETE                                         **ON**         数据库名         **FROM**       用户名/角色名;
**DENY**                               DELETE                                         **ON**         数据库名            **TO**          用户名/角色名;

### 5.事务处理语言

BEGIN TRANSACTION – 开始事务
COMMIT – 提交事务
ROLLBACK – 回滚事务

### 6.游标控制语言

DECLARE CURSOR – 定义游标
FETCH INTO – 提交游标数据
CLOSE CURSOR– 关闭游标

## 3.SQL语言基本数据类型

字符：CHAR、VARCHAR、TEXT
整数：SMALLINT、INTEGER
浮点数：NUMBER(n,d)、FLOAT(n,d)
日期：DATE、DATETIME
货币：MONEY

# 第四章 数据库设计与实现

## 1.数据库设计概述

### 1).数据库设计方案

数据库应用架构设计，数据库结构模型设计，数据库应用访问方式设计

### 2).数据库结构模型（建模）

#### 1.概念数据模型CDM

是一种**面向用户**的系统数据模型，用来描述现实世界的系统概念化数据结构

<img src="\Snipaste_2024-05-19_16-15-12.png" style="zoom:60%;" /> 

#### 2.逻辑数据模型LDM

从系统设计角度描述系统的数据对象组成及其**关联结构**，并考虑这些数据对象符合数据库对象的逻辑表示。 <img src="\Snipaste_2024-05-19_16-14-52.png" style="zoom:60%;" />

#### 3.物理数据模型PDM

描述系统数据模型在具体DBMS中的数据对象**组织、存储方式**、索引方式、访问路径等实现信息。 <img src="\Snipaste_2024-05-19_16-14-39.png" style="zoom:60%;" /> 

### 3).数据库开发过程

数据**需求分析**阶段，数据库**设计**阶段（数据库**建模**），数据库**实现**阶段，数据库**测试**阶段

### 4).设计策略

自底向上设计
自顶向下设计
自内向外设计
混合策略设计

## 2.E-R模型（实体联系模型）

### 1.基本元素

基本元素包括**实体**、**属性**、**标识符**和**联系**。

标识符与主键的区别是标识符是一个逻辑概念，主键是物理概念。

鸟足版的E-R模型

<img src="\Snipaste_2024-05-14_10-55-26.png" style="zoom:60%;" /> 

### 2.弱实体

弱实体是指存在**依赖于其他实体的实体**。与强实体相对，弱实体没有足够的属性来构成一个唯一的标识符，因此它的存在依赖于与其相关联的强实体。

强弱是**相对**于其它实体**而言的**，某个实体（A实体）可能对于B实体而言是强实体，对于C实体而言是弱实体，在一个关系中非强即弱。

### 3.继承联系

<img src="\Snipaste_2024-05-14_11-14-45.png" style="zoom:60%;" /> 

### 4.合并优化

局部合为全局时，要消除**命名冲突**：包括同名异义或异名同义等

**1 : 1 联系**的或具有相同键的两个实体集根据实际情况可以**合并**。

## 3.规范化设计

### 1.原因

1）减少数据库中的**冗余**数据，尽量使同一数据在数据库中仅保存一份，有效降低维护数据一致性的工作量。
2）设计合理的表间依赖关系和约束关系，便于实现数据**完整性和一致性**。
3）设计合理的数据库结构，便于系统对数据**高效**访问处理。

### 2.函数依赖

定义1：设X、Y是关系表R的属性（组），如果对于R的所有元组都有：X的每一具体值都只有一个Y的值与之对应，则称X函数决定Y，或Y函数依赖于X，记作X->Y。
换句话说，如果知道了X的值，就可以在表中确定与之对应的Y的值（只有一个）。

定义2：对于R的任意实例r，r中任意两个元组t1和t2，如果t1[X]=t2[X] 则t1[Y]=t2[Y]，

如果X、Y是 1 : 1 的联系，则X<->Y。
如果X、Y是 n : 1 的联系，则X->Y。
如果X、Y是 1:n / m : n的联系，则X和Y不存在函数依赖关系。

#### 1）平凡依赖，非平凡依赖

定义：设X、Y是关系表R的属性（组），且X->Y，若Y**被包含于X**，则称为平凡依赖，否则称为非平凡依赖。

#### 2）部分依赖，完全依赖

定义：设X、Y是关系表R的属性（组），且X->Y，若X**存在某个子集X1，使X1->Y成立**，则称Y部分依赖于X，否则称Y完全依赖于X。

#### 3）传递依赖，非传递依赖

定义：设X、Y、Z是关系表R的属性（组），若X->Y，Y->Z，且**Y-/>X**，则称X传递决定Z，或Z传递依赖于X，否则称Z非传递依赖于X 。

(如果不满足**Y-/>X**那就是直接依赖了，就不是传递依赖了)

#### 4）多值依赖

若X->->Y，则X的一个值唯一**决定一组Y值**，且这组值与X、Y**之外的属性值无关**

多值依赖的性质：
（1）对称性：若 X->->Y， Z=U-X-Y，则 X->->Z。
（2）函数依赖可看成是多值依赖的特例：若 X->Y，则 X->->Y
（3）若U=XY（表示X 并 Y），则 X->->Y显然成立。
（这种多值依赖无任何实际意义，故称为 平凡的多值依赖 ）
  (4)若X->->Y在U上成立，则在W（ XY 属于 W 属于 U）上也成立， 但反之不然。
（可缩小范围但不一定能扩大范围）

### 3.规范化范式

#### 1）第一范式  1NF

如果关系表R**不存在复合属性及多值属性**，即：**属性是不可再分**，则称R满足第一范式，记作R∈1NF。

① 将**复合属性**用各子属性代替，称为简单属性
② 将含有**多值属性**的表**分解成两张表**，一张表由主键和简单属性构成，另外一张表由多值属性和主键构成。

#### 2）第二范式 2NF

如果关系表R满足1NF，且所有非主属性都**完全依赖**于任一候选键，则称R满足第二范式，记作R∈2NF。

① 将**部分依赖**的非主属性和它**所依赖的属性**构成新的模式（表）          //关系模式表示：表名(主键，属性1，属性2)
② 将**完全依赖**的非主属性与候选键构成新模式

#### 3）第三范式 3NF

如果关系表R满足2NF，且所有非主属性都**非传递依赖**于R的任一候选键，则称R满足第三范式，记作R∈3NF。

①将**传递依赖**的属性及其**中间属性**移出构成**新表**
② 将不存在传递依赖的属性及候选键构成新表。

#### 4）BCNF

如果关系表R满足3NF，且R的**任一函数依赖关系的左部都是R的一个候选键**，则称R满足BCNF，记作R∈BCNF。

即R中不存在主属性对键的传递函数依赖或部分依赖。

#### 5）第四范式 4NF

如果关系满足BCNF范式，并消除了**多值函数依赖**，该关系满足第4范式。

#### 6）第五范式 5NF（了解）

若对于R的每一JD: ⨝(X1,…,Xn)，或是平凡连接依赖，或每个Xi包含R的候选键，则称R∈5NF，或称投影连接范式

<img src="\Snipaste_2024-05-14_15-58-05.png" style="zoom:60%;" /> <img src="\Snipaste_2024-05-14_15-59-04.png" style="zoom:60%;" /> 

![](\Snipaste_2024-05-14_16-00-42.png) 

### 4.反规范化处理方法

（1）增加冗余列或派生列
（2） 表的合并和分割

# 第五章 数据库管理

## 1.概述

### 1).为什么需要数据库管理

数据库系统随**规模增大**,系统会变得异常复杂
**多用户数据库应用**带来数据库访问复杂性
数据**安全**和数据**隐私**对机构和用户都非常重要
数据库系统随**数据量增加**和使用时间增长其**性能会降低**
系统遭遇意外事件，数据库**损坏或数据丢失**

### 2)数据库管理目标

保障数据库系统**正常稳定运行**
**充分发挥**数据库系统的**软硬件处理能力**
确保数据库系统安全和用户数据**隐私性**
有效管理数据库**用户及其角色权限**
解决数据库系统**性能优化、系统故障与数据损坏**等问题
最大程度地发挥数据库对其所属机构的作用

### 3)数据库管理内容

① DBMS系统**运行管理**与数据库**性能监控**
② 数据库**存储、索引与查询优化**
③ 数据库**事务并发控制**
④ 数据库**角色、用户管理**
⑤ 数据库**对象权限管理**
⑥ 数据库**安全管理**
⑦ 数据库**备份与恢复**

## 2.存储管理和索引

## 3.事务管理

### 1).事务定义

事务是指由构成单个业务处理单元的**一组数据库访问操作**，要求它们要么都成功执行，要么都不执行。

### 2).事务状态

事务状态有：初始状态、正常状态、失败状态、回滚状态、事务提交、事务结束。

<img src="\Snipaste_2024-05-14_17-01-11.png" style="zoom:100%;" /> 

### 3).事务特征（ACID）

**原子性**（Atomicity）：事务所有操作在数据库中要么全部执行，要么全部不执行。
**一致性**（Consistency）：事务多次执行，其结果应一致。
**隔离性**（Isolation）：事务与事务之间隔离，并发执行透明。
**持续性**（Durability ）：事务完成后，数据改变必须是永久的(提交结果持久化到磁盘中，确保即使系统崩溃或断电，数据也能够恢复到提																																																	交后的状态)

### 4).事务并发执行

定义：事务并发执行是指**多个事务**程序在数据库系统中**同一时段运行**。

事务并发执行原因：
(1)改善系统的**资源利用率**
(2)减少事务运行的**平均等待时间**
(3)提高系统性能
(4)提高系统吞吐量
(5)支持大规模应用

**BEGIN**  或 START TRANSACTION	                ；事务开始语句
**ROLLBACK**(TO SAVEPOINT 保存点名)			 ；事务回滚语句
**COMMIT**					  					                	；事务提交语句		
**SAVEPOINT**  保存点名										；事务保存点语句

事务中不能使用的SQL语句：数据库操作，日志操作，授权操作

## 4.并发控制

### 1).并发可能错误

#### 1.丢失更新

是指当**两个事务同时读取**同一数据并进行修改时，后提交的事务可能会覆盖先提交的事务所做的修改，导致数据的**更新操作丢失**。

#### 2.不可重复读取

是指在**一个事务内**，**两次读取**同一数据，第二次查询返回的结果集比第一次查询时**更少**，

#### 3.幻读

是指在**一个事务内**，**多次查询**同一范围的数据时，第二次查询返回的结果集比第一次查询时**更多**。

#### 4.脏读

当一个事务对数据进行了修改但尚未提交时，另一个事务**读取了**这个**未提交的数据**

### 2).事务调度

并发事务调度就是控制多个事务的数据操作语句**按照恰当的顺序**访问共享数据，使这些事务执行之后，**避免造成数据的不一致性**，即解决“丢失更新数据”、“不可重复读”、“脏数据读”等问题。

#### 可串行化调度

可串行化调度：对一事务集，如一个**并发调度与一个串行调度等价**，则称此并发调度是可串行化的
注意： ① 对n个事务有n！种串行调度。每个串行调度执行结果可能不一样，可串行化只要求调度和**其中某一个串行调度等价**。
② 不同的可串行化调度是不一定等价的。
③如果调度**是可串行化的**，系统认为其调度**是一个正确的调度**，保持了数据库的**一致性**

### 3).锁机制（对数据加锁）

#### 1.锁种类

**排它锁**(X锁)——锁定后，不允许其它事务对共享数据再加锁        <img src="\Snipaste_2024-05-14_17-42-23.png" style="zoom:80%;" />
**共享锁**(S锁)——锁定后，只允许其它事务对共享数据添加读取锁 

#### 2.加锁协议

##### (1)一级封锁协议

**写**某数据前，加上**X锁**，该事务结束后才释放。
**读**某数据前，**不加锁**。

可避免**更新丢失**。但不能解决**“不可重复读取”、“脏读”**等数据不一致问题。

##### (2)二级封锁协议

**写**某数据前，加上**X锁**，该事务结束后才释放。
**读**某数据前，加上**S锁**，**读完后就释放**

可避免**更新丢失**，**脏读**。但不能解决**“不可重复读取”**等数据不一致问题。

##### (3)三级封锁协议

**写**某数据前，加上**X锁**，该事务结束后才释放。
**读**某数据前，加上**S锁**，**该事务结束后才释放。**

可避免**更新丢失**，**脏读**，**不可重复读取**

<img src="\Snipaste_2024-05-14_19-36-01.png" style="zoom:60%;" /> 

##### (4)两阶段加锁协议 2PL->保证可串行化

规定每个事务**必须分两个阶段提出加锁和解锁申请**:
增长阶段，事务只能获得锁，但不能释放锁。
缩减阶段，事务只能释放锁，但不能获得新锁。

**如果事务符合两阶段锁定协议，则可实现串行化调度**

• 严格两阶段锁：除要求满足两段锁协议规定外，还要求事务的排它锁必须在事务提交之后释放。
解决**级联回滚**问题；避免了脏读和丢失更新的问题。
• 强两阶段锁：除要求满足两段锁协议规定外，还要求事务的所有锁都必须在事务提交之后释放。
进一步解决了不能重复读的问题

##### (5)(S,U,X)协议（了解）

事务要**更新**数据对象时，先申请该对象的**U锁**。对象加了U锁，允许其他事务对它加S锁。在最后写入时，再将U锁升级为X锁。不必在全过程中加X锁，可提高并发度。

<img src="\Snipaste_2024-05-14_19-49-23.png" style="zoom:80%;" /> 

### 4).死锁

死锁：在多个事务**竞争共享资源**的情况下，出现的**相互永远等待**的封锁请求，若无外力作用，这些事务永远不能向前推进，称为死锁。

### 5).事务隔离

<img src="\Snipaste_2024-05-14_20-13-09.png" style="zoom:60%;" /> 

事务隔离级别设置越高，出现数据不一致的可能性越小，但系统吞吐量也越小。

## 5.安全管理

### 1).数据库系统安全模型

<img src="\Snipaste_2024-05-14_20-24-43.png" style="zoom:60%;" /> 

### 2).数据库存取权限控制安全模型

<img src="\Snipaste_2024-05-14_20-23-54.png" style="zoom:60%;" /> 

## 6.数据库备份和恢复

备份内容——包括数据文件、日志文件等。
备份介质——包括**磁盘阵列**、**磁带**库、光盘库等。
备份时机——当系统数据库重要数据被修改、日志被清理、用户数据库创建、用户数据库加载等事件出现时。

@备份方法：
1.**<u>*完全备份*</u>**:将数据库中的所有**数据和结构**完整地备份到另一个位置或介质中
2.**<u>*差异备份*</u>**:指在**全量备份的基础上**，备份自上次全量备份以来**发生变化的数据**。
3.**<u>*事务日志备份*</u>**:只备份自**上一次日志备份至今**的事务日志数据的方式
4.**<u>*文件备份*</u>**:将**系统文件、数据文件和日志文件**复制到另一个位置或存储介质
@备份方式：
1.**<u>*热备份*</u>**：是指在数据库**运行时**进行备份操作，**不会中断**数据库的正常运行
2.**<u>*冷备份*</u>**：是指在数据库**停止运行时**进行备份操作，可以确保备份的数据完整性和一致性，但**会中断**数据库的正常服务

@恢复方式
1.通过**<u>*备份文件*</u>**进行恢复
2.利用**<u>*事务日志*</u>**按**前滚**(对已提交的事务)或**回滚**(对未提交的事务)方式进行数据库恢复

@使用SQL语句进行备份和恢复
**BACKUP DATABASE** SAMPLE     
**TO DISK** = ‘G:\Sample.bak'; 
**RESTORE DATABASE** SAMPLE 
**FROM DISK** = ‘G:\Sample.bak'; 
@使用shell语句进行备份和恢复
cd \program files\PostgreSQL\12\bin
**pg_dump** -h localhost -U postgres -p 5432 -d coursedb -c –C -f f:\databackup\coursedb.backup
**psql** -h 127.0.0.1 -U postgres -p 5432 -f f:\databackup\coursedb.backup

# 第六章 数据库编程

## 0.数据库函数编程的优点

1.通过PL/pgSQL编写函数存储在数据库服务器，既具有SQL语言**简单易用**的优点，又具有**处理复杂逻辑**过程的能力；
2.由于存储数据库服务器，因此调用执行数据库服务器的函数，能**消除客户端和服务器之间的额外通信**，户端不需要的中间结果不必由服务器向客户端传送；
3.能够**避免多次调用**的重复编译或解析。

## 1.语法和函数

声明变量：

变量名 INTEGER := 1;
变量名 表名% ROWTYPE；//定义行类型
变量名 RECORD; //定义记录类型
变量名 变量名%TYPE; //用已有类型定义

控制语句：

**IF**           条件      **THEN**       语句
**ELSIF**    条件      THEN       语句
**ELSE**                                   语句
**END IF;**

**CASE**
**WHEN** 条件 **THEN**   语句
WHEN 条件 THEN   语句
WHEN 条件 THEN   语句
**ELSE**                        语句
**END CASE;**

**LOOP**
语句（用EXIT/RETURN退出）
**END LOOP;**

**WHILE 条件 LOOP**
语句
**END LOOP;**

**FOR i IN 1..max LOOP**
语句
**END LOOP;**

**BEGIN**
语句
**EXCEPTION WHEN** division_by_zero **THEN**
处理语句
**END;**

**CREATE** [ OR REPLACE ] **FUNCTION 函数名**( [ [ argmode ] [ **参数名** ] **参数类型** [ { DEFAULT | = } default_expr ] [, ...] ] )
[ **RETURN<u>S</u> 返回值类型**]                            // RETURNS TABLE ( column_name column_type [, ...] ) 
**AS $$**                                                           //$$用于声明函数的实际代码的开始
**DECLARE**
-- 声明段
**BEGIN**
--函数体语句
**END;**
**$$** 
**LANGUAGE plpgsql;** 

select 函数名（参数）；
select * from 函数名（参数）；
select into 自定义变量 from 函数名（参数）;          //函数中执行，关心返回值
PERFORM countRecords();				               	//函数中执行，不关心返回值

## 2.游标

（1）游标（Cursor）是一种**临时**的数据库对象；
（2）用来**存放**从数据库表中**查询返回的数据记录**；
（3）提供了从结果集中提取并分别处理每一条记录的机制；
（4）游标总是与一条SQL查询语句相关联；(绑定)
（5）游标包括：SQL语言的查询结果，指向特定记录的指针。

使用游标技术的主要原因
① **逐行处理数据**： 游标允许逐行遍历结果集
② 控制数据访问： 可以在需要时随时获取下一行数据，而不是一次性将整个结果集加载到内存中。
③ 支持复杂逻辑： 在遍历结果集的过程中进行条件判断、数据更新或数据插入等操作。
④ 数据导航： 游标提供了对查询结果集的导航功能，可以在结果集中前进、后退或定位到特定位置，以便对数据进行操作或分析。
⑤ 存储过程和触发器： 游标技术通常用于存储过程和触发器中，以实现对数据的逐行处理和
操作。存储过程和触发器可以使用游标来处理复杂的业务逻辑或数据操作。

游标名 **refcursor**;                                                                   //声明未绑定游标
1.游标名 **CURSOR** [ 参数名 参数类型 ] **FOR query语句**;        //声明绑定游标
**OPEN** 游标名 **FOR query语句**;					                        //打开游标，游标未绑定
**OPEN** 游标名 **FOR EXECUTE query-string**;   				   //打开游标，游标未绑定（动态查询）
2.**OPEN** 游标名 (‘20160230302001’);                    				  //打开游标，游标已绑定
3.**FETCH** 游标名 **INTO** 行变量/列属性集(sex,name);		  //从游标获取数据(每用一次自动前移,可用if found then..else判断是否取得数据)
4.**CLOSE** 游标名;																	//关闭游标

## 3.存储过程

• 存储过程（Stored Procedure）是一种数据库的对象；
• 由一组能完成特定功能的**SQL 语句集构成**；
• 是把经常会被重复使用的SQL语句逻辑块封装起来，经编译后，存储在数据库服务器端；
• 当被再次调用时，而不需要再次编译；
• 当客户端连接到数据库时，用户通过指定存储过程的名字并给出参数，数据库就可以找到相应的存储过程予以调用

CREATE OR REPLACE **PROCEDURE** procedureName([**IN | OUT | INOUT**] Pname dataType, ... )         **//in,out替代renturns**
AS $$
DECLARE
变量1 数据类型 := 初始值1;
变量2 数据类型 := 初始值2;
BEGIN
-- 程序执行体语句写在这里;
END;
$$
LANGUAGE plpgsql

### 并发编程

**<u>*在SELECT语句最后加上子句来实现*</u>**

① **FOR UPDATE**：用于**排他锁**定，防止其他事务同时修改或锁定相同的数据。在SELECT语句中使用FOR UPDATE子句来实现。
② **FOR SHARE**：用于**共享锁**定，允许多个事务同时读取相同的数据，但阻止其他事务对数据进行更新。在SELECT语句中使用FOR SHARE子句来实现。
③ **FOR NO KEY UPDATE**：这种锁与FOR UPDATE类似，但它**不会阻止**其他事务**对非键列进行更新**。在SELECT语句中使用FOR NO KEY UPDATE子句来实现。
④ **FOR KEY SHARE**：用于共享锁定，允许多个事务同时读取相同的数据，但**阻止**其他事务**对键列进行更新**。在SELECT语句中使用FOR KEY SHARE子句来实现。

## 4.触发器

触发器是**特殊类型的*<u>存储过程</u>***

触发器的特点
Ø 与表相关联：必须定义在表或视图上。
Ø 自动触发：由执行INSERT、DELETE、UPDATE操作时触发
Ø 不能直接调用，也不能传递或接受参数
Ø 是事务的一部分：触发器和触发语句作为可在触发器内回滚的单个事务。

（1）**语句级**触发器：由关键字FOR EACH STATEMENT声明，在触发器作用的表上执行一条SQL语句时，该触发器只执行一次（默认值）
（2）**行级**触发器：由关键字FOR EACH ROW标记的触发器，当触发器作用的表的数据发生变化时，每变化一行就会执行一次触发器

（1）**BEFORE**触发器：在触发事件之前执行触发器。
（2）**AFTER**触发器：在触发事件之后执行触发器。
（3）**INSTEAD OF**触发器：当触发事件发生后，执行触发器中指定的函数，而不是执行产生触发事件的SQL 语句，从而替代产生触发事件的SQL操作。

触发器相关的特殊变量
（1）**NEW**
数据类型是RECORD。对于行级触发器，它存有INSERT或UPDATE操作**产生的新的数据行**。对于语句级触发器，它的值是NULL。
（2）**OLD**
数据类型是RECORD。对于行级触发器，它存有被UPDATE或DELETE操作**修改或删除的旧的数据行**。对于语句级触发器，它的值是NULL。
（3）**TG_OP**
数据类型是text；是值为INSERT、UPDATE、DELETE 的一个字符串，它**说明触发器是为哪个操作引发**。

**CREATE TRIGGER** 触发器名
{ BEFORE | AFTER | INSTEAD OF SQL操作名}
**ON 表名**
[ FOR [ EACH ]     { ROW | STATEMENT } ]
**EXECUTE PROCEDURE** 存储过程名 ( 参数列表 )               //该函数返回值类型必须为TRIGGER

<u>ALTER</u> TRIGGER name <u>ON table_name</u> RENAME TO new_name;
<u>DROP</u> TRIGGER [ IF EXISTS ] name <u>ON table_name</u>;

补充：事件触发器

针对特定的数据库的全局触发器，并且可以捕获DDL事件，只有超级用户才能创建和修改事件触发器，使用的函数不带参数并且返回 event_trigger类型，CREATE EVENT TRIGGER name ON event(例drop table).....

## 5.JDBC

**0**.导入 java.sql包
import java.sql.Connection/DriverManager/ResultSet/Statement;
**1**.**Class.forName**("org.postgresql.Driver")；   //加载驱动
**2**.String URL = "jdbc:postgresql://localhost:5432/testdb";String userName = "myuser";String passWord = "sa";
**connection** conn = **DriverManager.getConnection**(URL,userName,passWord);     //建立连接
**3**.Statement stmt = conn.**createStatement**();    //创建stmt
**4**.String sql = "SQL语句"+"SQL语句";
stmt.**executeUpdate**(sql);      //使用SQL更新数据库
ResultSet rs = stmt.**executeQuery**(sql);     //使用SQL查询，rs接收结果,rs.next()下一记录,rs.getString(属性名)
**5**.① rs.close(); //关闭结果集对象
② stmt.close(); //关闭执行对象
③ conn.close(); //关闭连接对象

### 嵌入式SQL

**3**.PreparedStatement stmt = conn.**prepareStatement**(SQL语句);    //创建动态stmt,**SQL中用?代表未知量**
loop语句
stmt.setString/setInt(1,80);         //1代表第一个?处
stmt.**addBatch**();            //添加批处理记录
loop语句结束
**4**.stmt.**executeBatch**();         //批处理执行记录











**数据库存储结构、数据库文件组织、数据库索引原理、B+树索引、哈希索引**？
