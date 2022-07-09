# Pythonでの指導の補足資料

NOTICE: **当repoは作成途中であり不完全です。フォルダ構成などは変更の可能性があります**

TODOs:

- プログラミングの一般用語、Python用語、Minecraft機能の解説を個別ページに分離する
- 分離の粒度を整える
- 各解説の相互リンクを貼る
  - Build a static website
  - Relative links between markdowns

---

## 基礎用語解説

### 「代入 (だいにゅう)」・「 `OO` を `XX` に代入する」

- `OO` というものに、 `XX` という名前 (変数名) を付けてプログラムの中で再利用できるようにすること
- Pythonでは、 `XX = OO`  と書く
- `OO` をプログラムの中で何度も使う (かもしれない) ときに毎回 `OO` と書くのは面倒。そんなときに `XX` という変数名を付ければ、分かりやすく・使いやすくなる
- 変数への代入を使わずに `OO` を自分で何度も打っていると、間違えて打つこともあるかもしれない。そんなときにPythonは「うーん、この行が間違ってるのかな?🤔」と自分で判断してはくれない ❌
  - → 原因が良く分からないエラーや間違った結果になってしまう😢
- 変数を使っていれば、たとえば「17行目で `XX` を `XY` と打ち間違えた」ときには、Pythonは「17行目で使っている `XY` という変数は存在しませんよー」と親切に教えてくれる ⭕
  - → エラーの原因が分かりやすくてプログラムを直しやすい😁
- 例: 「 3.14159265 を pi に代入する」
  - `pi = 3.14159265`
  - 円周率の近似値 (ずっと続く円周率の数字の最初の数桁だけのこと) `3.14159265` に `pi` (円周率の英語での言い方) という名前を付けることで、プログラムの中ではたった2文字 `pi` と打つだけで `3.14159265` という小数を使うことができる
  - `3.14159265` だと10文字打たないといけなかったのが、 `pi` なら2文字で済む
    - → 8文字分も楽ができる😆
  - `3.14159265` は長いために `3.14159365` , `3.14149265` のように打ち間違えることがあるかもしれない😓
  - 一方で `pi` ならば最初に一度だけ正しく `pi = 3.14159265` と打っていれば、プログラムは自分で正しく `3.14159265` を当てはめてくれる😊
    - → 打ち間違いのようなケアレスミスに集中力をすり減らすことなく、「どういうプログラムを組みたいか」という一番大事なことに集中できる😄

### 「同様に (どうように)」

- 「**前に**やったこと・ものを**繰り返す**・**真似する**」という意味
- この言葉が出てきたときには、その少し**前**の説明をよく確認する
- そこで説明されているのと**同じこと**を、今度は別の変数などに当てはめて**繰り返す**

---

## 各個解説

```python
from mcpi.minecraft import Minecraft
```

### `from XX`

- 「XXから」という意味の英語
- 例: "from home"
  - お家から
- 例: `from math`
  - `math` という数学のための機能を集めたPythonのモジュールから

### `mcpi`

- `mcpi` という名前のPythonの外部ライブラリ (モジュール)
- 「Pythonでマイクラを遊びたい!」という人たちがボランティアで作ったもの
- `mcpi` を使うためには、プログラムを書く前に `pip install mcpi` というコマンドを打ってインストールする必要がある

### `mcpi.minecraft`

- `mcpi` フォルダの中にある `minecraft.py` ( `mcpi/minecraft.py` )

[github.com/martinohanlon/mcpi](https://github.com/martinohanlon/mcpi) の構造

```text
mcpi/
 __init__.py
 block.py
 connection.py
 entity.py
 event.py
 minecraft.py
 util.py
 vec3.py
```

### `import XX`

- 「XXを輸入する」・「XXを持ってくる」という意味の英語
- 例: "import banana"
  - バナナを輸入する
- 例: `import time`
  - `time` モジュールを今書いているプログラムに持ってくる
  - 持ってきた `time` モジュールに含まれるものは、 `time.sleep()` のように `time.` を付けて呼び出せる
- 例: `from time import sleep`
  - `time` モジュールから `sleep()` 関数のみを今書いているプログラムに持ってくる
  - `sleep()` は `time.` などを付けずにそのまま使うことができる
  - `time` モジュール全てを `import` してはいないため、 `sleep()` 以外の `time.perf_counter()` などは `time.` を付けても使うことはできない (エラーになる)

### `from mcpi.minecraft import Minecraft` の意味は?

- `mcpi` というライブラリ (モジュール) の中の
- `minecraft.py` というPythonのファイルから
- `Minecraft` というもの (Pythonのクラス) を持ってくる

---

```python
mc = Minecraft.create()
```

### `x = ooo`

- 『「代入 (だいにゅう)」とは』を参照
- Pythonや他のプログラミング言語では、「 `x` という変数に `ooo` というものを代入する」という意味
  - 例: `n = 12`
    - 変数 `n` に `12` という数字 ( `int` ) を代入する
  - 例: `s = "Hello World!"`
    - 変数 `s` に `Hello World!` という文字列 ( `str` ) を代入する

### `Minecraft.create()`

- `Minecraft` クラスの `create()` メソッドを呼び出す
- 「Pythonのプログラムからマイクラの世界にアクセスする (つなげる) ためのカギ」を返す
- マイクラが起動している必要がある

### `mc = Minecraft.create()` の意味は?

- `Minecraft` というクラスの
- `create()` というメソッドを実行した結果として得られる「マイクラにつながるカギ」を
- `mc` という変数に代入する
- そうすることで、 `mc.setBlock()` , `mc.postToChat()` のようにマイクラの中の世界をいじることができる🔧

---

```python
pos = mc.player.getTilePos()
```

### `position` / `pos`

- 「位置・場所・立場」という意味の英語
- プログラミングの世界では英単語を省略して最初の数文字のみを変数名にすることが多いため、よく `pos` として使われる
- 例: "position of the moon"
  - 月の位置
- 例: "his position"
  - 彼の立場

### `mc.player`

- `player` はプレーヤーの英語でのスペル
- `mc.player` は `mc = Minecraft.create()` で `mc` に代入したマイクラへのカギを経由してゲーム内のプレーヤーを操作するためのインスタンス変数
- `mc.player.getTilePos()`, `mc.player.setPos()` のように `mc.player.` を付けるとプレーヤーを操作するためのメソッドを使える

### `get`

- 「得る・取ってくる」という意味の英語
- 例: "get"
  - 助けを得る / 援助を得る
- 例: "get a call"
  - 電話をもらう
- 例: "get something to drink"
  - 何か飲み物を取ってくる

### `tile`

- 「タイル」の英語でのスペル

### `mc.player.getTilePos()`

- マイクラの ( `mc` ) プレーヤーが ( `player` ) 立っている場所 ( `tile` ) の座標 ( `pos` ) を取得する ( `get` ) ためのメソッド

### `pos = mc.player.getTilePos()` の意味は?

- `mc.player.getTilePos()` メソッドの結果として得られる「プレーヤーが立っている場所の座標」を
- `pos` という変数に代入する

---

```python
mc.postToChat("Hello")
```

### `post`

- 「届ける」という意味の英語

### `to ~`

- 「~に」という意味の英語
- 例: "to home"
  - 家に
- 例: "to elementary school"
  - 小学校に

### `chat`

- 「会話・雑談・おしゃべり」という意味の英語

### `postToChat("Hello")` の意味は?

- Minecraftのチャット欄に
- "Hello" (こんにちは)という文章を
- 表示する

---
