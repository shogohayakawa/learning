# DBデータの表示

## 開発要件
1. DBからユーザ名及びメールアドレスを取得し、ブラウザに表示してください。
2. URLは以下の```ルーティング定義```通りとなるよう設定してください。
3. DB及び```users```テーブルを作成し、事前にデータを投入してください。DB名は任意とします。

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
||created_at|DATETIME|-|NULLABLE|-|登録日|
||updated_at|DATETIME|-|NULLABLE|-|更新日|

## ルーティング定義
|機能|HTTPメソッド|URL|コントローラ名|メソッド名|備考|
|:---:|:---:|:---:|:---:|:---:|:---:|
|テスト画面表示|GET|/test|TestController|test|テスト画面を表示する|

## ファイル構成
|ファイル分類|クラス名|メソッド名|引数|戻り値|備考|
|:---:|:---:|:---:|:---:|:---:|:---:|
|Controller|TestController.java|test|Model|String|test画面のリクエスト受付<br>userテーブルよりユーザ名及びメールアドレスを取得<br>ブラウザ表示情報をViewへ渡す|
|View|test.html|-|-|-|test画面|
