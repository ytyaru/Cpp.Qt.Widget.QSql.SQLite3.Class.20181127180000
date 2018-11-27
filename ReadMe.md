# このソフトウェアについて

　Qt5学習。QtでSQLite3を使ってみる。Class化した。

## 前回まで

* https://github.com/ytyaru/Cpp.Qt.Widget.QSql.SQLite3.Class.20181127170000
* https://github.com/ytyaru/Cpp.Qt.Widget.QSql.SQLite3.Class.20181127160000
* https://github.com/ytyaru/Cpp.Qt.Widget.QSql.SQLite3.Class.20181127130000

## コード抜粋

memodb.cpp
```cpp
void MemoDb::Open(QString path) {
    if (!QSqlDatabase::contains(this->dbName)) {
        QSqlDatabase db = QSqlDatabase::addDatabase("QSQLITE", "MemoDb");
        this->dbPath = QDir(path).filePath("memo.sqlite3");
        db.setDatabaseName(this->dbPath);
        this->CreateTable();
    }
}
void MemoDb::Close() {
    QSqlDatabase::removeDatabase(this->dbName);
}
void MemoDb::CreateTable() {
    QSqlDatabase db = QSqlDatabase::database(this->dbName);
    QSqlQuery query(db);
    query.exec("create table Memo(id INTEGER PRIMARY KEY AUTOINCREMENT, Memo text, DateTime text)");
}
```

1. `QSqlDatabase::addDatabase()`
1. `db.setDatabaseName()`
1. `db = QSqlDatabase::database()`
1. `QSqlDatabase::removeDatabase()`

# 参考

* http://tomokiit.hatenablog.jp/entry/Qt_SQLite
* https://blogs.yahoo.co.jp/hmfjm910/10815002.html
* https://forum.qt.io/topic/18700/sqlite-connection-qsqldatabaseprivate-adddatabase-duplicate-connection-name-qt_sql_default_connection-old-connection-removed/7

## Qt要素

* http://doc.qt.io/qt-5/qsql.html
    * http://doc.qt.io/qt-5/qsqldatabase.html
    * http://doc.qt.io/qt-5/qsqlquery.html

# 開発環境

* [Raspberry Pi](https://ja.wikipedia.org/wiki/Raspberry_Pi) 3 Model B+
    * [Raspbian](https://www.raspberrypi.org/downloads/raspbian/) GNU/Linux 9.0 (stretch) 2018-06-27
        * Qt 5.7.1

## 環境構築

* [Raspbian stretch で Qt5.7 インストールしたもの一覧](http://ytyaru.hatenablog.com/entry/2019/12/17/000000)

# ライセンス

　このソフトウェアはCC0ライセンスである。

[![CC0](http://i.creativecommons.org/p/zero/1.0/88x31.png "CC0")](http://creativecommons.org/publicdomain/zero/1.0/deed.ja)

## 利用ライブラリ

ライブラリ|ライセンス|ソースコード
----------|----------|------------
[Qt](http://doc.qt.io/)|[LGPL](http://doc.qt.io/qt-5/licensing.html)|[GitHub](https://github.com/qt)

* [参考1](https://www3.sra.co.jp/qt/licence/index.html)
* [参考2](http://kou-lowenergy.hatenablog.com/entry/2017/02/17/154720)
* [参考3](https://qiita.com/ynuma/items/e8749233677821a81fcc)
