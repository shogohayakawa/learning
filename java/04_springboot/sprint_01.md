# 開発概要

## 開発要件
1. Springbootを使用し、ブラウザに```Hello World```を表示してください。
2. URLは```http://localhost:8080/test```としてください。
3. ViewにはThymeleafを導入してください。

## 使用ツール
|概要|ツール|
|:---:|:---:|
|フレームワーク|Springboot|
|テンプレートエンジン|Thymeleaf|
|ビルドツール|Gradle|
|エディタ|Eclipse|

## ファイル構成
|概要|クラス名|メソッド名|引数|戻り値|備考|
|:---:|:---:|:---:|:---:|:---:|:---:|
|Controller|TestController.java|test|Model|String|testページのリクエスト受付<br>ブラウザ表示情報をViewへ渡す|
|View|test.html|-|-|-|testページ表示|
