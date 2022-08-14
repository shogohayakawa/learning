# つぶやき削除機能の実装

## 開発要件
1. 登録済みのつぶやき情報が削除できる`つぶやき削除機能`を実装してください。
2. `つぶやき詳細画面`からつぶやき情報を削除し、`タイムライン画面`へリダイレクトしてください。
3. URLは以下の`ルーティング定義`通りとなるよう設定してください。
4. 各アクションは以下の`画面定義`通りとなるよう実装してください。
5. 画面は`Bootstrap`を適用し、以下の`画面イメージ`を参考にデザインを調整してください。  
※`画面イメージ`と全く同じデザインとしなくても構いません

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
|-|タイムライン画面表示|GET|/board/index|BoardController|index|つぶやき情報を全件取得し「タイムライン画面」を表示する。|
|-|つぶやき詳細画面表示|GET|/board/show/{id}|BoardController|show|つぶやき情報を1件取得し「つぶやき詳細画面」を表示する。|
|-|つぶやき登録画面表示|GET|/board/create|BoardController|create|「つぶやき登録画面」を表示する。|
|-|つぶやき登録確認画面表示|POST|/board/create/confirm|BoardController|createConfirm|「つぶやき登録画面」で入力されたつぶやき情報を「つぶやき登録確認画面」へ表示する。|
|-|つぶやき登録画面へ戻る|POST|/board/create|BoardController|createGoBack|入力されたつぶやき情報を引き継いで「つぶやき登録画面」を表示する。|
|-|つぶやき登録処理|POST|/board/store|BoardController|store|つぶやき情報を登録し「タイムライン画面」へリダイレクトする。|
|-|つぶやき編集画面表示|GET|/board/edit/{id}|BoardController|edit|「つぶやき編集画面」を表示する。|
|-|つぶやき編集確認画面表示|POST|/board/edit/confirm|BoardController|editConfirm|「つぶやき編集画面」で入力されたつぶやき情報を「つぶやき編集確認画面」へ表示する。|
|-|つぶやき編集画面へ戻る|POST|/board/edit/{id}|BoardController|editGoBack|入力されたつぶやき情報を引き継いで「つぶやき編集画面」を表示する。|
|-|つぶやき更新処理|POST|/board/update|BoardController|update|つぶやき情報を更新し「タイムライン画面」へリダイレクトする。|
|★|つぶやき削除処理|POST|/board/delete|BoardController|delete|つぶやき情報を削除し「タイムライン画面」へリダイレクトする。|

## ファイル構成
|対象|MVC|クラス名|メソッド名|引数|戻り値|備考|
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
|-|Controller|BoardController.java|index|Model|String|全てのboardsテーブルのレコードを「タイムライン画面」のViewへ渡す。|
|-|||show|int, Model|String|選択されたboardsテーブルのレコードを「つぶやき詳細画面」のViewへ渡す。|
|-|||create|Model|String|「つぶやき登録画面」のViewを呼び出す。|
|-|||createConfirm|BoardForm, BindingResult, Model|String|「つぶやき登録画面」で入力されたデータをバリデーションチェックする。<br>「つぶやき登録画面」で入力されたデータを「つぶやき登録確認画面」のViewへ渡す。|
|-|||createGoBack|BoardForm, Model|String|「つぶやき登録確認画面」に設定されたデータを「つぶやき登録画面」のViewへ渡す。|
|-|||store|BoardForm, BindingResult, Model, RedirectAttributes|String|「つぶやき登録確認画面」に設定されたデータをバリデーションチェックする。<br>「つぶやき登録確認画面」に設定されたデータをboardsテーブルに登録する。<br>「タイムライン画面」へリダイレクトする。|
|-|||edit|int, Model|String|「つぶやき編集画面」のViewを呼び出す。|
|-|||editConfirm|BoardForm, BindingResult, int, Model|String|「つぶやき編集画面」で入力されたデータをバリデーションチェックする。<br>「つぶやき編集画面」で入力されたデータを「つぶやき編集確認画面」のViewへ渡す。|
|-|||editGoBack|BoardForm, int, Model|String|「つぶやき編集確認画面」に設定されたデータを「つぶやき編集画面」のViewへ渡す。|
|-|||update|BoardForm, BindingResult, int, Model, RedirectAttributes|String|「つぶやき編集確認画面」に設定されたデータをバリデーションチェックする。<br>「つぶやき編集確認画面」に設定されたデータをboardsテーブルへ更新する。<br>「タイムライン画面」へリダイレクトする。|
|★|||delete|int, Model, RedirectAttributes|String|「つぶやき詳細画面」に設定されたデータをboardsテーブルから削除する。<br>「タイムライン画面」へリダイレクトする。|
|-|Model|BoardService.java<br>（インターフェース）|getAll|-|List\<Board>|boardsテーブルのレコードを全件取得するようdaoに指示する。|
|-|||getBoard|int|Board|つぶやきIDを元にboardsテーブルのレコードを1件取得するようdaoに指示する。|
|-|||save|Board|void|Boardエンティティのデータをboardsテーブルへ1件登録するようdaoに指示する。|
|-|||update|Board|void|Boardエンティティのデータをboardsテーブルへ1件更新するようdaoに指示する。|
|★|||delete|int|void|つぶやきIDを元にboardsテーブルのレコードを1件削除するようdaoに指示する。|
|-||BoardServiceImpl.java<br>（インターフェース実装クラス）|getAll|-|List\<Board>|boardsテーブルのレコードを全件取得するようdaoに指示する。|
|-|||getBoard|int|Board|つぶやきIDを元にboardsテーブルのレコードを1件取得するようdaoに指示する。|
|-|||save|Board|void|Boardエンティティのデータをboardsテーブルへ1件登録するようdaoに指示する。|
|-|||update|Board|void|Boardエンティティのデータをboardsテーブルへ1件更新するようdaoに指示する。|
|★|||delete|int|void|つぶやきIDを元にboardsテーブルのレコードを1件削除するようdaoに指示する。|
|-||BoardDao.java<br>（インターフェース）|findAll|-|List\<Board>|boardsテーブルのレコードを全件取得する。|
|-|||findById|int|Board|つぶやきIDを元にboardsテーブルのレコードを1件取得する。|
|-|||insert|Board|void|Boardエンティティのデータをboardsテーブルへ1件登録する。|
|-|||update|Board|void|Boardエンティティのデータをboardsテーブルへ1件更新する。|
|★|||deleteById|int|void|Boardエンティティのデータをboardsテーブルから1件削除する。|
|-||BoardDaoImpl.java<br>（インターフェース実装クラス）|findAll|-|List\<Board>|boardsテーブルのレコードを「更新日/降順」で全件取得する。|
|-|||findById|int|Board|つぶやきIDを元にboardsテーブルのレコードを1件取得する。|
|-|||insert|Board|void|Boardエンティティのデータをboardsテーブルへ1件登録する。|
|-|||update|Board|void|Boardエンティティのデータをboardsテーブルへ1件更新する。|
|★|||deleteById|int|void|Boardエンティティのデータをboardsテーブルから1件削除する。|
|-||BoardForm.java|-|-|-|boardsモデルのformクラス<br>フィールド変数、コンストラクタ、getter・setterを定義する。<br>入力項目のバリデーションチェック内容は以下の「バリデーション」参照。|
|-||Board.java|-|-|-|boardsテーブルのEntityクラス<br>フィールド変数、コンストラクタ、getter・setterを定義する。|
|-|View|index.html|-|-|-|タイムライン画面|
|★||show.html|-|-|-|つぶやき詳細画面|
|-||create.html|-|-|-|つぶやき登録画面|
|-||create_confirm.html|-|-|-|つぶやき登録確認画面|
|-||edit.html|-|-|-|つぶやき編集画面|
|-||edit_confirm.html|-|-|-|つぶやき編集確認画面|

## 画面定義
### つぶやき詳細画面
- 画面イメージ（初期表示）

![01](/java/images/03_springboot/02_develop/sprint_05/01.PNG)

- 画面イメージ（つぶやき削除確認ダイアログ）

![02](/java/images/03_springboot/02_develop/sprint_05/02.PNG)

- 画面項目

|対象|画面項目1|画面項目2|種別|備考|
|:---:|:---:|:---:|:---:|:---:|
|-|ヘッダ|ページタイトル|テキスト出力|「Simple Board」と表示する。<br>クリックすると「タイムライン画面」へ遷移する。|
|-||「つぶやき登録」ボタン|ボタン|クリックすると「つぶやき登録画面」へ遷移する。<br>※現段階では実装不要|
|-|画面タイトル|-|テキスト出力|「つぶやき詳細」と表示する。|
|-|つぶやき詳細表示部|タイトルヘッダ|テキスト出力|「タイトル」と表示する。|
|-||タイトル|テキストボックス|「タイムライン画面」で選択されたレコードのタイトルを表示する。<br>画面から編集できないよう「非活性」とする。|
|-||つぶやきヘッダ|テキスト出力|「つぶやき」と表示する。|
|-||つぶやき|テキストエリア|「タイムライン画面」で選択されたレコードのつぶやきを表示する。<br>画面から編集できないよう「非活性」とする。|
|-|「一覧へ戻る」ボタン|-|ボタン|クリックすると「タイムライン画面」へ遷移する。|
|-|「編集」ボタン|-|ボタン|クリックすると「つぶやき編集画面」へ遷移する。|
|-|「削除」ボタン|-|ボタン|クリックすると「つぶやき削除ダイアログ」を表示する。|
|★|つぶやき削除確認ダイアログ|ダイアログヘッダ|テキスト出力|「つぶやきの削除確認」と表示する。|
|★||ダイアログテキスト|テキスト出力|「つぶやきを本当に削除しますか？」と表示する。|
|★||「戻る」ボタン|ボタン|「つぶやき削除確認ダイアログ」を閉じる。|
|★||「削除」ボタン|ボタン|設定されたデータをboardsテーブルから削除し、「タイムライン画面」へリダイレクトする。|

### タイムライン画面
- 画面イメージ（フラッシュメッセージ）

![03](/java/images/03_springboot/02_develop/sprint_05/03.PNG)

- 画面項目

|対象|画面項目1|画面項目2|種別|備考|
|:---:|:---:|:---:|:---:|:---:|
|-|ヘッダ|ページタイトル|テキスト出力|「Simple Board」と表示する。<br>クリックすると「タイムライン画面」へ遷移する。|
|-||「つぶやき登録」ボタン|ボタン|クリックすると「つぶやき登録画面」へ遷移する。|
|-|画面タイトル|-|テキスト出力|「タイムライン」と表示する。|
|★|フラッシュメッセージ|-|テキスト出力|フラッシュメッセージが存在する場合は表示する（※1）|
|-|つぶやき一覧ヘッダ|タイトル|テキスト出力|-|
|-||つぶやき|テキスト出力|-|
|-||更新日|テキスト出力|-|
|-||詳細|テキスト出力|-|
|-|つぶやき一覧レコード|取得されたタイトル|テキスト出力|-|
|-||取得されたつぶやき|テキスト出力|-|
|-||取得された更新日|テキスト出力|日本時間<br>yyyy/MM/dd hh:mm形式|
|-||「みる」ボタン|ボタン|クリックすると「つぶやき詳細画面」へ遷移する。|

※1）表示されるメッセージは、以下の`フラッシュメッセージ`参照

### フラッシュメッセージ

|対象|画面|表示契機|フラッシュメッセージ|
|:---:|:---:|:---:|:---:|
|-|タイムライン画面|つぶやき登録成功時|つぶやきの登録に成功しました|
|-||つぶやき更新成功時|つぶやきの更新に成功しました|
|★||つぶやき削除成功時|つぶやきの削除に成功しました|
