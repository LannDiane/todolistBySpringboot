# todolistBySpringboot

Spring Boot ToDo アプリケーション
Spring Bootを使用した初心者向けのシンプルなToDoアプリケーションです。
使用技術

Spring Boot
Thymeleaf
PostgreSQL
MyBatis

機能一覧

ToDoアイテムのCRUD操作
ステータス管理（完了/未完了）
完了済みタスクの一括削除
期限日設定

クイックスタート
必要環境

JDK 8以上
PostgreSQL
Maven

データベースの設定

データベースとユーザーの作成：

sql
CREATE ROLE todo_user LOGIN PASSWORD 'todo_pass';
CREATE DATABASE todo_db WITH OWNER = todo_user;

テーブルの作成：

sql
CREATE TABLE todo_items(
    id serial,
    title varchar(40),
    done_flg numeric(1) default 0,
    time_limit date
);
アプリケーションの設定
application.propertiesにデータベース接続情報を設定：
properties
spring.datasource.driver-class-name=org.postgresql.Driver
spring.datasource.url=jdbc:postgresql://localhost:5432/todo_db
spring.datasource.username=todo_user
spring.datasource.password=todo_pass
実行方法

プロジェクトをクローン
Mavenでビルド：mvn clean install
実行：mvn spring-boot:run
アクセス：http://localhost:8080

プロジェクト構成
src/main/java/com/todo/app/
├── controller/
│   └── TodoController.java
├── entity/
│   └── Todo.java
├── mapper/
│   └── TodoMapper.java
└── resources/
    ├── mapper/
    │   └── TodoMapper.xml
    ├── templates/
    │   └── index.html
    └── application.properties
主要なエンドポイント

GET / - ToDoリストの表示
POST /add - 新規ToDo追加
POST /update - ToDo更新
POST /delete - 完了済みToDoの削除
