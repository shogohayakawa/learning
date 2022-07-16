# Hello Worldの表示

## 開発要件
1. Springbootを使用し、ブラウザに```Hello World```を表示してください。
2. URLはは以下の```ルーティング定義```通りとなるよう設定してください。
3. ViewにはThymeleafを導入してください。

## 使用ツール
|概要|ツール|
|:---:|:---:|
|フレームワーク|Springboot|
|テンプレートエンジン|Thymeleaf|
|ビルドツール|Gradle|
|エディタ|Eclipse|

## ルーティング定義
|新規|機能|HTTPメソッド|URL|コントローラ名|メソッド名|備考|
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
|★|テスト画面表示|GET|/test|TestController|test|テスト画面を表示する|

## ファイル構成
|新規|MVC|クラス名|メソッド名|引数|戻り値|備考|
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
|★|Controller|TestController.java|test|Model|String|文字列「Hello World」をViewへ渡す|
|★|View|test.html|-|-|-|テスト画面|
