# simpleMathEdit

MathJax v3 と marked を読み込み、左側のテキストエリアに入力した Markdown + TeX 形式の内容を右側でライブプレビューするシンプルなエディタです。Markdown を HTML に変換して差し込み、デバウンスしながら MathJax で再レンダリングする構成になっています。

## グラフプロットの使い方

Markdown 内にカスタムタグを記述することで 2D / 3D の関数プロットを表示できます。

## よく使う Markdown / MathJax 記法一覧

### Markdown

- **見出し**

  ```md
  # 見出し1
  ## 見出し2
  ### 見出し3
  ```

- **強調**

  ```md
  *イタリック* / **太字** / ~~取り消し~~
  ```

- **箇条書き / 番号付きリスト**

  ```md
  - 箇条書き1
  - 箇条書き2

  1. 番号付き1
  2. 番号付き2
  ```

- **リンク / 画像**

  ```md
  [リンクテキスト](https://example.com)
  ![代替テキスト](画像のURL)
  ```

- **コード**

  ```md
  `inline code`

  ~~~js
  const x = 1;
  ~~~
  ```

- **引用**

  ```md
  > 引用文
  ```

### MathJax（TeX 記法）

- **インライン / ブロック数式**

  ```md
  インライン: $a^2 + b^2 = c^2$

  ブロック:
  $$
  \int_0^1 x^2 dx = \frac{1}{3}
  $$
  ```

- **分数 / ルート**

  ```tex
  \frac{a}{b}, \sqrt{x}, \sqrt[n]{x}
  ```

- **上付き / 下付き**

  ```tex
  x^2, a_{n+1}
  ```

- **ギリシャ文字**

  ```tex
  \alpha, \beta, \gamma, \Delta
  ```

- **総和 / 積分**

  ```tex
  \sum_{i=1}^n i, \int_a^b f(x)\,dx
  ```

- **行列**

  ```tex
  \begin{bmatrix}
  a & b \\
  c & d
  \end{bmatrix}
  ```

- **場合分け**

  ```tex
  f(x) =
  \begin{cases}
  x^2 & (x \ge 0) \\
  -x & (x < 0)
  \end{cases}
  ```

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

### 3D パラメトリック曲面 (x = f(u, v), y = g(u, v), z = h(u, v))

```html
<plots3d>
  <axis u="0 6.283" v="0 3.1415" step="0.2"></axis>
  <parametric x="cos(u) * sin(v)"
              y="sin(u) * sin(v)"
              z="cos(v)"></parametric>
</plots3d>
```

- `axis` の `u`, `v` はパラメータの範囲を `min max` の順で指定します。
- `parametric` は `x`, `y`, `z` それぞれの式を指定します。

## Demo (GitHub Pages)

https://pun2beam.github.io/simpleMathEdit/
