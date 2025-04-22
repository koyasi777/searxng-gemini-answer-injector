# SearXNGにGemini AIの回答を表示 ✨

## 📌 概要

オープンソース検索エンジン「SearXNG」の検索結果ページに、**Google Gemini** のAI回答を直接表示するユーザースクリプトです。  
検索ワードに応じて、Geminiが生成したHTML形式の簡潔かつ信頼性の高い情報を表示します。

- 🔐 APIキーはローカルストレージに保存（再入力可）
- 🌙 ダークモードにも自動対応
- ⚡ 表示位置は検索結果最上部、自然に溶け込むスタイル

<p>
  <img src=".github/images/searxng-gemini-answer-preview.png" alt="Searxngに表示されたGemini回答" width="600">
</p>

---

## ⚙️ インストール方法

1. お使いのブラウザに **[Violentmonkey](https://violentmonkey.github.io/) または [Tampermonkey](https://www.tampermonkey.net/)** をインストール
2. 下記リンクからスクリプトをインストール  
   👉 [このスクリプトをインストールする](https://raw.githubusercontent.com/koyasi777/searxng-gemini-answer-injector/main/searxng-gemini-answer.user.js)
3. 最初の利用時に **Gemini APIキー** の入力を求められます。以下のURLから取得してください：  
   https://aistudio.google.com/app/apikey?hl=ja

---

## 💡 主な機能

- クエリ文字列を自動取得し、Geminiに送信
- GeminiのHTML形式の回答を検索結果上部に追加
- APIキーはローカルに保存（`localStorage`）
- APIキーの再入力・変更にも対応
- CORSやGM_系のgrant不要（`fetch`使用）

---

## 🖼 対応サイト

多数のSearXNGインスタンスに対応するため、`@match` を以下のように広く指定しています：

```js
// @match        *://*/searx/search*
// @match        *://*/searxng/search*
// @match        *://searx.*/*
// @match        *://*.searx.*/*
```

⚠️ **ご自身の利用しているSearXNGのドメインによっては、このマッチ条件に含まれない場合があります。**  
その場合は `.user.js` ファイル内の `@match` 行を手動で修正し、ご自身の環境に合わせてください。

---

## 🧠 技術構成・実装ポイント

- `fetch` による Gemini API (`generateContent`) 呼び出し
- `localStorage` にAPIキーを保存／再取得
- 検索クエリを `input[name="q"]` から抽出
- ダークモード判定には `matchMedia('(prefers-color-scheme: dark)')`
- スタイルはネイティブUIに自然に溶け込むよう設計
- 応答がなければ再試行、401/403時は再入力を促す設計

---

## 🔗 関連リンク

- [Google Gemini API (PaLM) 公式ドキュメント](https://ai.google.dev/)
- [SearxNG GitHub](https://github.com/searxng/searxng)
- [Violentmonkey](https://violentmonkey.github.io/)
- [Tampermonkey](https://www.tampermonkey.net/)

---

## 📜 ライセンス

MIT License  
自由に改変・再配布いただけますが、利用は自己責任でお願いします。

---

> SearXNGを、GeminiでAI強化！  
> クエリに対して信頼できる情報を、即座に表示。
