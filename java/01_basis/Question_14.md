# Question14

## 開発要件
1. キーボードから入力された2つの整数を元に、掛け算結果及び掛け算結果を2で割った整数を出力するプログラムを作成してください。（※Question11と同様の処理内容）
2. クラス、インターフェース及びメソッドの構成は以下となるようにしてください。

|クラス名<br>インターフェース名|メソッド名|引数|戻り値|概要|
|:---:|:---:|:---:|:---:|:---:|
|Question14|main|String[]|void|メインメソッド|
|Calculate<br>（インターフェース）|multiplication|int, int|int|抽象メソッド|
||division|int, int|int|抽象メソッド|
|CalculateImpl<br>（インターフェース実装クラス）|multiplication|int, int|int|引数の掛け算結果を返却する|
||division|int, int|int|引数の掛け算結果を2で割った結果を返却する|
3. ```Calculate```のプログラムは以下を使用してください。プログラムの修正は不可とします。
```java
/**
 * java基礎 Question14 Calculateインターフェース
 * @author Your name
 */
public interface Calculate {
	/**
	 * 掛け算処理
	 * @param num1 整数1
	 * @param num2 整数2
	 * @return 掛け算結果
	 */
	int multiplication(int num1, int num2);

	/**
	 * 割り算処理
	 * @param num1 整数1
	 * @param num2 整数2
	 * @return 割り算結果
	 */
	int division(int num1, int num2);
}
```
4. キーボードから入力された値が整数以外の場合、```整数以外の値が入力されました```と出力してください。
5. プログラムの実行結果は、以下と同様になるよう作成してください。

## コンソール出力結果
```bash
# 整数が入力された場合
整数を入力してください
1個目：10 # キーボード入力
2個目：20 # キーボード入力
10 と 20 の掛け算結果の値は 200 です
10 と 20 の掛け算結果を2で割った値は 100 です

# 整数以外の値が入力された場合
整数を入力してください
1個目：10 # キーボード入力
2個目：aaa # キーボード入力
整数以外の値が入力されました
```
