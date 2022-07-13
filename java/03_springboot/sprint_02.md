# 開発概要

## 開発要件
1. DBからユーザ名及びメールアドレスを取得し、ブラウザに表示してください。
2. URLは```http://localhost:8080/test```としてください。
3. MySQLにDB及びテーブルを作成し、事前にデータを投入してください。DB名は任意とします。

## 使用ツール
|概要|ツール|
|:---:|:---:|
|フレームワーク|Springboot|
|テンプレートエンジン|Thymeleaf|
|DB|MySQL（XAMPP / MAMP）|
|ビルドツール|Gradle|
|エディタ|Eclipse|

## テーブル定義
|テーブル名|カラム名|データ型|サイズ|必須|制約|備考|
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
|user|id|INTEGER|-|NOT NULL|PRIMARY KEY<br>AUTO_INCREMENT|ユーザID|
||name|VARCHAR|20|NOT NULL|-|氏名|
||email|VARCHAR|100|NOT NULL|-|メールアドレス|
||created_at|DATETIME|-|NULLABLE|-|登録日|
||updated_at|DATETIME|-|NULLABLE|-|更新日|

## ファイル構成
|ファイル分類|クラス名|メソッド名|引数|戻り値|備考|
|:---:|:---:|:---:|:---:|:---:|:---:|
|Controller|TestController.java|test|Model|String|testページのリクエスト受付<br>userテーブルよりユーザ名及びメールアドレスを取得<br>ブラウザ表示情報をViewへ渡す|
|View|test.html|-|-|-|testページ表示|
