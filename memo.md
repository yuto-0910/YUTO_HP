# Coding memo

## about Files (May-08)

### 📂 プロジェクト全体構成の解説（YUTO-HP）

✅ **1. .next/**

- ✅ **Next.jsがビルド時に生成するディレクトリ（キャッシュ・静的ファイルなど）**
- 基本的にGitに含めないし、ユーザーが触ることはほぼない

---

✅ **2. node_modules/**

- ✅ **npmでインストールされたライブラリの本体**
- ここも触らない。Gitに含めない（.gitignoreで除外済）

---

✅ **3. public/**

- ✅ **画像・フォント・faviconなどの静的ファイル置き場**
- 例：public/avatar.jpg → https://〜/avatar.jpg で直接参照可

---

✅ **4. src/**

- ✅ **アプリのコード本体（app/, components/, styles/ などがここに）**
- App Routerを選んだことで、src/app/ がメインのルーティングディレクトリになる

### 🔎 特に最初に触るべきは

- src/app/page.tsx：トップページの中身
- src/app/about/page.tsx：プロフィールなど追加ページ
- src/components/：共通パーツ（Header, Footerなど）を置く場所を自分で作る
- tailwind.config.js（表示されてないけどあるはず）：Tailwindカスタマイズ

## about .tsx

TypeScript + JSX（JavaScript XML）の組み合わせで書かれたReactコンポーネントのファイル拡張子

### 🔍 詳しく言うと

- .ts → 通常の TypeScript ファイル
（型付きJavaScript。Reactを使わない関数やロジック系のコードに使う）
- .tsx → Reactのコンポーネント を TypeScriptで書く場合に使う
（JSX構文＝HTMLライクなタグを書くには .tsx が必須）

### 📘 JSXってなに？

~~~tsx
return (
  <main>
    <h1>YUTO AOKI</h1>
  </main>
);
~~~

↑これってまるでHTMLに見えるけど、**これは「JSX構文」**って呼ばれるReact特有の書き方で、
JavaScriptの中にHTMLっぽい記述を埋め込んでいる。

## tsx 書き出し〜中身の基本構造

### 書き出し

~~~tsx
export default function Home() {

}
~~~

- export : このファイルは外でも使えるよ！って宣言。
- default : ファイルのメインですよ！って宣言。
- function Home() : 関数宣言。`Home`は関数名。

### 中身の基本構造

~~~tsx
return()
~~~

要は返り値。関数だからね。

- この`return`の中身でJSXを返す。(React要素)
- Reactがその返されたJSXを元にHTMLを構成して表示する。

### つまり、関数を作り、返り値をReactに渡す

~~~jsx
export default function Home() {
  return (
    <main>
      <h1>こんにちは！</h1>
    </main>
  );
}
~~~

- home関数でreturn内のHTMLをReactに渡している。
- その結果、ReactがHTMLに書き直し、Webへ公開している。
