# SQLAlchemy 简单介绍

参考官方文档(1.3)：[SQLAlchemy Documentation — SQLAlchemy 1.3 Documentation](https://docs.sqlalchemy.org/en/13/index.html)

[TOC]

三大组件：

- SQLAlchemy ORM
    对象关系映射器
- SQLAlchemy Core
    对SQLAlchemy的SQL和数据库集成和描述服务的广度进行了记录，其核心是SQL表达式语言。SQL表达式语言是一个完全独立于ORM包的工具箱，它可以用来构造可操作的SQL表达式，可以通过编程方式构造、修改和执行这些表达式，并返回类似于光标的结果集。与ORM以域为中心的使用模式不同，表达式语言提供了以模式为中心的使用模式
- Dialects
    所有提供的数据库和DBAPI后端

主要组件依赖关系

![_images/sqla_arch_small.png](https://docs.sqlalchemy.org/en/13/_images/sqla_arch_small.png)

## SQLAlchemy ORM

 ###  [对象关系教程 Object Relational Tutorial](SQLAlchemy ORM\对象关系教程 Object Relational.md)

### Mapper Configuration

### Relationship Configuration

### Loading Object

### Loading Objects

### Using the session

### Events and Internals

### ORM Exaples





## SQLAlchemy Core





## Dialects

支持类型

- [PostgreSQL](https://docs.sqlalchemy.org/en/13/dialects/postgresql.html)
- [MySQL](https://docs.sqlalchemy.org/en/13/dialects/mysql.html)
- [SQLite](https://docs.sqlalchemy.org/en/13/dialects/sqlite.html)
- [Oracle](https://docs.sqlalchemy.org/en/13/dialects/oracle.html)
- [Microsoft SQL Server](https://docs.sqlalchemy.org/en/13/dialects/mssql.html)

