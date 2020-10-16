---
title: 'Connecting PostgreSQL with QT and forming QTableView'
description: 'I started to develop one app for Desktop. Qt were the obvious choice for me, because I really like C++ and I’ve already made some apps using this framework.'
date: '2019-02-07T04:23:29+06:00'
template: 'post'
draft: false
slug: 'connecting-postgresql-with-qt-and-forming-qtableview'
category: 'Qt'
tags: ['C++', 'Linux', 'PostgreSQL', 'Qt']
socialImage: '/media/2019-02-07--qt-postgre.png'
---
![](/media/2019-02-07--qt-postgre.png)

I started to develop one app for Desktop. Qt were the obvious choice for me, because I really like C++ and I’ve already made some apps using this framework.

The app was needed to store information somewhere and show it in table view. I decided to use SQL database and read some material about PostgreSQL to be familiar with it. It wasn’t hard and I started development process immediately. I read official Qt docs about QSql, but had some issues which are not discussed there. That is why I want to write this post.

The most important thing is that you should install QtCreator only from [official website](https://www.qt.io/download) because only this version has QPSQL driver support.

I recommend you to create new class to include everything needed there.

First of all, you need to add this line to your project file (*.pro*) :

```makefile
QT += sql
```

And include this file to your header file (*.h)*:

```c++
#include <QtSql>
```

Then you need to create object of *QSqlDatabase* and initialize it:

```c++
    QSqlDatabase db = QSqlDatabase::addDatabase("PSQL"); / PostgreSQL driver
    db.setHostName(""); // set the name of your host
    db.setDatabaseName(""); // set the name of your database 
    db.setUserName(""); // set the name of user, who is owner of the database
    db.setPassword(""); // set the password of the user
    bool ok = db.open(); // checks connection status
```

The important thing here is *HostName.* It depends on usage scenario and it has different cases according this. You should execute **ifconfig** command and use local IP if you are going to install your application and database on the same computer or IP created by your wireless/ethernet adapter.

Then we are moving to table view of our database table. You need to include two headers:

```c++
#include <QSqlTableModel>
#include <QTableView>
```

This files are including some classes to create table model from database table and to show it as a table in Qt application. In order to do this, you need to add a new method which will contain this lines of code:

```c++
    QSqlTableModel *testDbModel = new QSqlTableModel;
    testDbModel->setTable(tableName);
    testDbModel->select();
```

You should write the name of your table from your database instead of *tableName.*

That is all what I wanted to write about in this post. Hope, this information will be useful for you.