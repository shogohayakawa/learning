# タイムライン表示機能の実装

## 開発要件
1. DBからつぶやき情報を全件取得し、`タイムライン画面`に一覧表示してください。
2. URLは以下の`ルーティング定義`通りとなるよう設定してください。
3. 画面項目や各アクションは以下の`画面定義`通りとなるよう実装してください。
4. 画面は`Bootstrap`を適用し、以下の`画面イメージ`を参考にデザインを調整してください。  
※`画面イメージ`と全く同じデザインとしなくても構いません
5. DBに```boards```テーブルを作成し、事前にデータを投入してください。

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
|boards|id|INTEGER|-|NOT NULL|PRIMARY KEY<br>AUTO_INCREMENT|つぶやきID|
||title|VARCHAR|20|NOT NULL|-|タイトル|
||content|VARCHAR|140|NOT NULL|-|つぶやき内容|
||created_at|DATETIME|-|NULLABLE|-|登録日|
||updated_at|DATETIME|-|NULLABLE|-|更新日|

## ルーティング定義
|対象|機能|HTTPメソッド|URL|コントローラ名|メソッド名|備考|
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
|★|タイムライン画面表示|GET|/board/index|BoardController|index|つぶやき情報の一覧を表示する。|

## ファイル構成
|対象|MVC|クラス名|メソッド名|引数|戻り値|備考|
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
|★|Controller|BoardController.java|index|Model|String|全てのboardsテーブルのレコードをViewへ渡す。|
|★|Model|BoardService.java<br>（インターフェース）|getAll|-|List\<Board>|boardsテーブルのレコードを全件取得するようdaoに指示する。|
|★||BoardServiceImpl.java<br>（インターフェース実装クラス）|getAll|-|List\<Board>|boardsテーブルのレコードを全件取得するようdaoに指示する。|
|★||BoardDao.java<br>（インターフェース）|findAll|-|List\<Board>|boardsテーブルのレコードを全件取得する。|
|★||BoardDaoImpl.java<br>（インターフェース実装クラス）|findAll|-|List\<Board>|boardsテーブルのレコードを「更新日/降順」で全件取得する。|
|★||Board.java|-|-|-|boardsテーブルのEntityクラス<br>フィールド変数、コンストラクタ、getter・setter定義する。|
|★|View|index.html|-|-|-|タイムライン画面|

## 画面定義
### タイムライン画面
- 画面イメージ

![01](/java/images/03_springboot/02_develop/sprint_01/01.PNG)

- 画面項目

|対象|画面項目1|画面項目2|種別|備考|
|:---:|:---:|:---:|:---:|:---:|
|★|ヘッダ|ページタイトル|テキスト出力|「Simple Board」と表示する。<br>クリックすると「タイムライン画面」へ遷移する。|
|★||「つぶやき登録」ボタン|ボタン|クリックすると「つぶやき登録画面」へ遷移する。<br>※現段階では実装不要|
|★|画面タイトル|-|テキスト出力|「タイムライン」と表示する。|
|★|つぶやき一覧ヘッダ部|タイトル|テキスト出力|-|
|★||つぶやき|テキスト出力|-|
|★||更新日|テキスト出力|-|
|★|つぶやき一覧レコード部|取得されたタイトル|テキスト出力|-|
|★||取得されたつぶやき|テキスト出力|-|
|★||取得された更新日|テキスト出力|日本時間<br>yyyy/MM/dd hh:mm形式|
