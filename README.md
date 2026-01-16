# simpleMathEdit

MathJax v3 と marked を読み込み、左側のテキストエリアに入力した Markdown + TeX 形式の内容を右側でライブプレビューするシンプルなエディタです。Markdown を HTML に変換して差し込み、デバウンスしながら MathJax で再レンダリングする構成になっています。

## グラフプロットの使い方

Markdown 内にカスタムタグを記述することで 2D / 3D の関数プロットを表示できます。

### 2D プロット (y = f(x))

```html
<plots>
  <axis x="-10 10" y="-5 5"></axis>
  <plot y="sin(x)"></plot>
  <plot y="cos(x)"></plot>
</plots>
```

### 3D プロット (z = f(x, y))

```html
<plots3d>
  <axis x="-5 5" y="-5 5" z="-5 5" step="0.5"></axis>
  <surface z="sin(x) * cos(y)"></surface>
</plots3d>
```

- `axis` の `x`, `y`, `z` は `min max` の順で指定します。
- `step` はグリッドの刻み幅です（省略時は `0.5`）。
- `surface` は `z = f(x, y)` の形式で式を指定します。

## Demo (GitHub Pages)

https://pun2beam.github.io/simpleMathEdit/
