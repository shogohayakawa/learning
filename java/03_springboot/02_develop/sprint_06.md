# Bootstrapの実装

## 開発要件

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

## ファイル構成

## 各画面イメージ
あくまでイメージなので、近いデザインとなっていれば問題ありません。
以下の画像を参考に実装してください。