# シン・アカデミアWebサイト

## メンバー紹介ページの運用方法

このプロジェクトでは、メンバーの情報を `data/members.yaml` で管理しています。
メンバーの追加・編集や画像の設定方法は以下の通りです。

---

### 1. メンバーの追加・編集

`data/members.yaml` をテキストエディタで開き、下記のようにメンバー情報を記載します。

```yaml
- name: 山田花子
  description: 数学に興味
  image: ""
  email: ""
  homepage: ""
- name: 木村太郎
  description: 物理に興味
  image: ""
  email: ""
  homepage: ""
- name: 田中智子
  description: 哲学に興味
  image: ""
  email: ""
  homepage: ""
- name: 佐藤一郎
  description: 生物学に興味
  image: "images/sato.jpg"
  email: "ichiro.sato@example.com"
  homepage: "https://ichiro.example.com"
```

- **name**: 名前（必須）
- **description**: 概要説明（必須）
- **image**: 画像パス（省略可、未指定ならプレースホルダー画像が表示されます）
- **email**: メールアドレス（省略可）
- **homepage**: ホームページURL（省略可）

> ※ メンバーの順番はYAMLファイルの記述順になります。

---

### 2. 画像の追加方法

1. `static/images/` フォルダに画像ファイル（例: `sato.jpg`）を保存します。
2. `image: "images/sato.jpg"` のようにYAMLの `image` 項目にパスを記載します。
   - パスは `static/` 以下を基準に記載してください。
3. サーバーを再起動するか、ページをリロードすれば反映されます。

---

### 3. 注意事項

- **個人情報（実際のメールアドレスやプライベートな連絡先）はこのREADMEや公開リポジトリには記載しないでください。**
- サンプルは必ずダミー情報（例: taro@example.com）で記載してください。
- 画像ファイル名は半角英数字推奨です（日本語やスペースは避けてください）。

---

### 4. サイトのローカル確認方法

```sh
hugo server -D
```
でローカルサーバーを起動し、
`http://localhost:1313/ja/members/` でメンバー紹介ページを確認できます。

---

## ヘッダーのナビゲーションメニューの編集方法

このサイトのヘッダーに表示されるメニューは、`hugo.toml` ファイルの `[languages.ja.menu.main]` および `[languages.en.menu.main]` セクションで管理されています。

### 例：日本語メニューに「メンバー」リンクを追加

```toml
[languages.ja.menu]
  [[languages.ja.menu.main]]
    identifier = "home-ja"
    name = "ホーム"
    url = "/ja/"
    weight = 1
  [[languages.ja.menu.main]]
    identifier = "about-ja"
    name = "概要"
    url = "/ja/about/"
    weight = 2
  [[languages.ja.menu.main]]
    identifier = "services-ja"
    name = "サービス"
    url = "/ja/services/"
    weight = 3
  [[languages.ja.menu.main]]
    identifier = "lab-ja"
    name = "ラボ"
    url = "/ja/lab/"
    weight = 4
  [[languages.ja.menu.main]]
    identifier = "members-ja"
    name = "メンバー"
    url = "/ja/members/"
    weight = 5
  [[languages.ja.menu.main]]
    identifier = "contact-ja"
    name = "お問い合わせ"
    url = "/ja/contact/"
    weight = 6
```

- `name`：表示名
- `url`：リンク先（日本語は `/ja/` から始まるパス）
- `weight`：表示順（数字が小さいほど左側）

### 英語メニューも同様に `[languages.en.menu.main]` で管理します

```toml
[languages.en.menu]
  [[languages.en.menu.main]]
    identifier = "members"
    name = "Members"
    url = "/en/members/"
    weight = 5
```

### 注意事項

- メニューの順番を変えたい場合は `weight` の値を調整してください。
- 多言語対応の場合、それぞれの言語ブロックで編集が必要です。
- 変更後はHugoサーバーを再起動するか、ページをリロードしてください。

---

## ライセンス

本リポジトリはMITライセンスです。
