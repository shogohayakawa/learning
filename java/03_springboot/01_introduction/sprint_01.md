# Hello Worldの表示

## 開発要件
1. Springbootを使用し、ブラウザに`Hello World`を表示してください。
2. URLは以下の`ルーティング定義`通りとなるよう設定してください。
3. 画面は以下の`画面定義`を参考に作成してください。
4. ViewにはThymeleafを導入してください。

## 使用ツール
|概要|ツール|
|:---:|:---:|
|フレームワーク|Springboot|
|テンプレートエンジン|Thymeleaf|
|ビルドツール|Gradle|
|エディタ|Eclipse|

## ルーティング定義
|対象|機能|HTTPメソッド|URL|コントローラ名|メソッド名|備考|
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
|★|テスト画面表示|GET|/test|TestController|test|テスト画面を表示する。|

## ファイル構成
|対象|MVC|クラス名|メソッド名|引数|戻り値|備考|
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
|★|Controller|TestController.java|test|Model|String|文字列「Hello World」をViewへ渡す。|
|★|View|test.html|-|-|-|テスト画面|

## 画面定義
### テスト画面
- 画面イメージ

![01](/java/images/03_springboot/01_introduction/sprint_01/01.PNG)