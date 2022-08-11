# モデルの作成

## 開発要件
1. `sprint_02`と同じ開発要件で、モデルからユーザ情報が取得されるよう改修してください。
2. モデルは以下の構造となるよう作成してください。

    - Service
    - Repository（dao）
    - Entity

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
|★|Model|UserService.java<br>（インターフェース）|getAll|-|List\<User>|usersテーブルのレコードを全件取得するようdaoに指示する。|
|★||UserServiceImpl.java<br>（インターフェース実装クラス）|getAll|-|List\<User>|usersテーブルのレコードを全件取得するようdaoに指示する。|
|★||UserDao.java<br>（インターフェース）|findAll|-|List\<User>|usersテーブルのレコードを全件取得する。|
|★||UserDaoImpl.java<br>（インターフェース実装クラス）|findAll|-|List\<User>|usersテーブルのレコードを全件取得する。|
|★||User.java|-|-|-|usersテーブルのEntityクラス<br>フィールド変数、コンストラクタ、getter・setterを定義する。|
|★|View|test.html|-|-|-|テスト画面|

## 画面定義
### テスト画面
- 画面イメージ

![01](/java/images/03_springboot/01_introduction/sprint_03/01.PNG)
※）`sprint_02`と同様です