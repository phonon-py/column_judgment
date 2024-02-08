# 事業区分判定プログラム

このプログラムは、Pandas DataFrameの特定の列（この例では`a`列）の値に基づいて事業区分を判定し、新たなカラムとしてその判定結果をDataFrameに追加します。

## 概要

`determine_business`関数は、`a`列の各値を引数として受け取り、その値が`a`または`b`の場合は`A事業`を、`c`または`d`の場合は`B事業`を返します。これにより、新しい`事業区分`カラムが作成され、各行がどの事業に分類されるかが明確になります。

## 使用方法

プログラムを使用するには、以下のステップに従ってください。

1. 必要なデータを含むPandas DataFrameを準備します。
2. `determine_business`関数をDataFrameの適用したい列に対して`apply`メソッドを用いて実行します。
3. 新しい`事業区分`カラムが追加されたDataFrameを確認します。

## コード例

以下は、実際のコードの使用例です。

```python
import pandas as pd

# 例として適当なデータを持つDataFrameを作成
df = pd.DataFrame({
    'a': ['a', 'b', 'c', 'd'],
    'b': [1, 5, 6, 4],
    'c': [3, 8, 9, 4],
    'd': [3, 11, 12, 6]
})

# '事業区分'カラムを追加し、'a'列の値に基づいて'A事業'または'B事業'と判定する関数を定義する
def determine_business(x):
    if x in ['a', 'b']:
        return 'A事業'
    elif x in ['c', 'd']:
        return 'B事業'
    else:
        return '不明'

# apply関数を使って、'a'列の各値に対して判定関数を適用する
df['事業区分'] = df['a'].apply(determine_business)

# 結果を表示
print(df)
