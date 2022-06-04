# Question8

## 開発要件
1. キーボードから入力された整数の数及び整数の各値を元に、入力値の一覧及び入力値の平均を出力するプログラムを作成してください。（※Question7と同様の処理内容）
2. 複数の整数の格納は、```ArrayList```を使用してください。
3. キーボードから入力された値が整数以外の場合、```整数以外の値が入力されました```と出力してください。
4. プログラムの実行結果は、下記と同様になるよう作成してください。

## コンソール出力結果
```bash
# 整数が入力された場合（整数の数："3"）
整数の数を入力してください
3 # キーボード入力
整数の各値をを入力してください
1個目：10 # キーボード入力
2個目：20 # キーボード入力
3個目：30 # キーボード入力
入力された値は 10 20 30 です
入力された整数の平均は 20 です

# 整数が入力された場合（整数の数："5"）
整数の数を入力してください
5 # キーボード入力
整数の各値をを入力してください
1個目：10 # キーボード入力
2個目：15 # キーボード入力
3個目：20 # キーボード入力
4個目：25 # キーボード入力
5個目：30 # キーボード入力
入力された値は 10 15 20 25 30 です
入力された整数の平均は 20 です

# 整数以外の値が入力された場合（整数の数）
整数の数を入力してください
aaa # キーボード入力
整数以外の値が入力されました

# 整数以外の値が入力された場合（整数の各値）
整数の数を入力してください
3 # キーボード入力
整数の各値をを入力してください
1個目：10 # キーボード入力
2個目：aaa # キーボード入力
整数以外の値が入力されました
```