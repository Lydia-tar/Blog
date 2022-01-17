# Database

## SQL (relationship model)

### PL/SQL block

``` SQL
DECLARE
--Declares internal program objects, such as variables.

--Marks the beginning of the program logic.
BEGIN
--This is the actual PL/SQL and SQL statements.

    FOR I IN 1..1000 Loop
        INSERT INTO employee(ssn, name)
        VALUES(900000000 + I, 'John Doe');
    END LOOP;
    COMMIT;

EXCEPTION
--Marks the beginning of exception logic.
    WHEN OTHERS THEN
        ROLLBACK;

END;
--Marks the end of the program logic.
```


### Triggers

Row-level Triggers

``` SQL
CREATE OR REPLACE TRIGGER TriggerName
    BEFORE | AFTER
    INSERT OR DELETE OR UPDATE OF Column1, ColumnN
    ON TableName
    FOR EACH ROW
    REFERENCING OLD AS OldName
        NEW AS NewName
    WHEN (condition expression)
DECLARE

BEGIN

EXCEPTION

END;

```

### indexing

理解：index的作用像书本的目录一样，因为数据是有序的，所以可以由目录去索引

但实际上index分为*顺序索引*，*散列索引（根据hash function）*两种。在顺序索引中，分为*dense index*，*sparse index*两种。

![Dense index](/_static/Dense_index.png)
![sparse index](/_static/sparse_index.png)

single level index **vs** Multi-Level Index

![multi-level index](/_static/multi-level_index.png)

SQL Syntax

``` 
Create Index IndexName on T(A)
Create Index IndexName on T(A1,A2,…,An)
Create Unique Index IndexName on T(A)
Drop Index IndexName
```

#### B+ tree indexing

B+ tree indexing 是为了解决当数据越来越大时，索引查找性能下降的问题，虽然这个问题可以通过从组索引来解决，但是我们并不希望频繁重新重组索引。所以使用B+ tree。

B+ tree indexing 怎么做到的：B+ tree 采用平衡树（balance tree）结构，也就是说root（树根）到 each leaf（树叶）的路径是相等的。假设每个node最多可以有n个children，那么每个node存储了n个pointer和（n-1）个search-key values

![node structure](/_static/node_structure.png)
![b+tree example](/_static/B+tree_example.png)

#### basic search method

1. Linear search (sequential scan)

Average search time = $ \frac{b}{2} $


2. Binary search
Average search time =$ \log_2(b) $

[https://www.cs.usfca.edu/~galles/visualization/Algorithms.html](https://www.cs.usfca.edu/~galles/visualization/Algorithms.html)

### query optimization

## Transaction Management

Transaction properties: 

A(Atomicity): Transaction是不可分割的单位，要么全部执行，要么都不执行。
C(Consistency): Transaction必须将数据库从一个一致状态转换到另一种一致状态。
I(Isolation): Transaction之间的执行是互相独立的，也就是说未完成事物导致的中间结果对其他事物来说是不可见的。
D(Durability):结果将被永久记录在数据库中。

### Isolation

isolation levels
- Serializability(可串行化): Operations may be interleaved, but execution must be equivalent to some sequential (serial) order of all transactions.

- repeatable read：只允许读取**已提交数据**，而且在一个事物读取一个数据项期间，其他事物不得更新该数据。但该事物不要求与其他事物串行化。

- read committed：只允许读取**已提交数据**，但不要求可重复读。即在事物两次读取一个数据项期间，另一个事务更新了该数据并提交。

- read uncommitted：允许读取**未提交数据**。

serializability concepts



> Exercise
>
> Consider a relation R(A) containing {(4),(8)} and two transactions:
>
>T1: Update R set A = A+2;
>
>T2: Update R set A = 2*A.
>
>Suppose both transactions are submitted under the isolation and atomicity properties. Provide all possible final states of R by considering all possible serializable schedules.


## On_line Analytical Processing (OLAP)

OLAP的基本操作

在多维数据模型中，数据组织在多维空间，每维包含由概念分层定义的多个抽象层。这种组织为用户从不同角度观察数据提供了灵活性。

上卷:roll-up  drill-up

通过一个维的概念分层向上攀升或者通过维归约在数据立方体上进行聚集。比如城市统计数据维度到省级统计数据维度。

下钻:drill-down 

 下钻是上卷的逆操作，由不太详细的数据到更详细的数据。下钻可以通过沿维的概念分层向下或引入附加的维来实现。

切片和切块:slice and dice

切片（slice）1是在给定的立方体的一个维上进行选择，从而定义一个子立方体。切块（dice）操作通过两个或多个维上进行选择，定义一个子立方体。

转轴:pivot 

是一种目视操作，就像是一个二维表的行列转换，两个维度的互换。

钻过:drill-across 

其执行会涉及多个事实表的查询

钻透:drill-through

下钻透过多维数据立方直达RDMS表。


## XML Concepts, Models, Languages, and Standards

use EditX XML editor for XML [download](https://www.editix.com/download.html)

XPath:Path expression + conditions

XQuery: Xpath +full featured QL
``` xml
For $var in expr
Let $var := expr
Where condition
Order By expr
Return expr
```

- All except Returnare optional

- Forand Letcan be repeated and interleaved


## Object-Relational Database

use Django tool

``` Python
#install
pip install django
#verfy
django-admin --version
```
Django Project: An Application is a Part of Django Project.

Create Django Project
``` python
django-admin startproject projectname
```

run server
``` 
Steps:-

❑Go to Project Folder

❑Then run command python manage.py runserver (port:8000 can self-definition)

❑Server Started

❑Visit http://127.0.0.1:8000 or http://localhost:8000

ctrl + c is used to stop Server
```

Start/Create Application
```
Creating One Application inside Project:-
❑Go to Project Folder
❑Run Command python manage.py startapp course
```

Install Application in Our Project
```
We install application in our project using settings.py file.
settings.py file is available at Project Level which means we can install all the application of
project.
This is compulsory otherwise Application won’t be recognized by Django.
Open settings.py file
INSTALLED_APPS = [
‘django.contrib.admin’,
‘application_name1’,
‘application_name2’,
]
Save settings.py File
```

makemigrations – This is responsible for creating new migrations based on the changes you have made to your models.

> Syntax:- python manage.py makemigrations


migrate – This is responsible for applying and unapplying migrations.
> Syntax:- python manage.py migrate

Display SQL Statement

> We can retrieve SQL Statement by using below command:-
> Syntax:-
> python manage.py sqlmigrate application_name dbfile_name
> Example:-
> python manage.py sqlmigrate enroll 0001

## Data warehousing and data integration

