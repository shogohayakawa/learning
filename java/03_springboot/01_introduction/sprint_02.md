# DBデータの表示

## 開発要件
1. DBからユーザ情報を全て取得し、ブラウザに表示してください。
2. URLは以下の`ルーティング定義`通りとなるよう設定してください。
3. DB及び`users`テーブルを作成し、事前にデータを投入してください。DB名は任意とします。
4. 画面は以下の`画面定義`を参考に作成してください。

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
|users|id|INTEGER|-|NOT NULL|PRIMARY KEY<br>AUTO_INCREMENT|ユーザID|
||name|VARCHAR|20|NOT NULL|-|氏名|
||email|VARCHAR|100|NOT NULL|-|メールアドレス|
||created_at|DATETIME|-|NOT NULL|-|登録日|
||updated_at|DATETIME|-|NOT NULL|-|更新日|

## ルーティング定義
|対象|機能|HTTPメソッド|URL|コントローラ名|メソッド名|備考|
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
|-|テスト画面表示|GET|/test|TestController|test|テスト画面を表示する。|

## ファイル構成
|対象|MVC|クラス名|メソッド名|引数|戻り値|備考|
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
|★|Controller|TestController.java|test|Model|String|全てのusersテーブルのレコードをViewへ渡す。|
|★|View|test.html|-|-|-|テスト画面|

## 画面定義
### テスト画面
- 画面イメージ

![01](/java/images/03_springboot/01_introduction/sprint_02/01.PNG)