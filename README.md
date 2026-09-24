# ANAWAK — The Heart of Europe

ドバイ沖の人工島 The Heart of Europe のレジデンス販売LP（ANAWAK Real Estate L.L.C / JWDグループ）。
静的サイトです。ビルド工程はありません。`index.html` をブラウザで開けばそのまま表示されます。

## 公開（正式・唯一）

**🌐 https://miyagenesis.github.io/anawak-hoe-site/**

- このリポジトリが本サイトの唯一の正式ソース（2026-09-25にGitHub Pagesへ一本化）。
- 公開方式: GitHub Pages（deploy from branch: `main` / `/`）。`main` へ push すると1〜2分後に自動で反映されます。
- `.nojekyll` 済み。リンク・アセットは全て相対パスなのでサブパス配信でそのまま動作します。

## 構成

```
index.html                  投資案内（メイン）
news/index.html             ニュース一覧
ibiza/index.html            娯楽エリア「イビサ・フェスティバル」（日英切替）
assets/img/*.jpg            メインの写真（ファイル名＝コード内の画像キー）
assets/video/*.mp4          動画3本
ibiza/assets/img/*.jpg      娯楽エリアの写真
```

## 画像の差し替え方

`index.html` 末尾の `const IMG = { キー: "assets/img/xxx.jpg", ... }` が画像の一覧です。
同じ名前で差し替えるか、キーの値を書き換えれば反映されます。表示位置は以下の配列が参照しています。

| 配列 | 表示場所 |
| --- | --- |
| `propSlides` | 物件カードのスライドショー（`mSeahorse` / `mPortofino` / `mGermany` / `mCazur`） |
| `pfItems` | 物件マーキー（自動横スクロール） |
| `lifeItems` | 島の情景マーキー（逆方向） |
| `gal` | ギャラリーのグリッド |

## 動画

| ファイル | 使用箇所 |
| --- | --- |
| `assets/video/hero.mp4` | ファーストビュー |
| `assets/video/underwater.mp4` | 水中セクション |
| `assets/video/film-duo.mp4` | 「海の上に、ヨーロッパが広がる。」（縦動画2本を半々に並べた合成） |
| `ibiza/assets/video/party.mp4` | 娯楽エリアのファーストビュー（フォームパーティ） |
| `ibiza/assets/img/poster-*.jpg` | 娯楽エリアの公式ポスター3点（プログラム / DJラインナップ / キービジュアル） |
| `ibiza/assets/video/v*.mp4` | 娯楽エリアの会場タイル6本・現地映像5本（各5〜8秒・音声なし） |

## 素材の出所

写真は JWD 提供素材（JWD-Material）と Seahorse & Honeymoon Island のブローシュアPDF、
および提供動画から切り出した静止画です。

## ニュースの追加方法

`news/index.html` の `<article class="news-item">` をコピーして、日付・本文・ボタンのリンク先を差し替えてください。
ボタンの行き先は外部URL（Instagram等）でも、`../ibiza/` のような内部ページでも構いません。

## 娯楽エリアの映像タイル

`ibiza/index.html` の会場・現地映像は `<video autoplay muted loop playsinline>` のタイルです。
画面内に入ったものだけを再生する IntersectionObserver を入れてあるので、同時再生による負荷は抑えられています。
差し替えるときは `assets/video/` の同名ファイルを置き換え、`assets/img/p_◯◯.jpg`（ポスター）も併せて更新してください。

## 写真の帰属について

各物件のスライドに使う写真は、素材のファイル名（`Seahorse…` / `Portofino…` / `Germany Island…` / `Cote d'Azur…`）と
ブローシュアの掲載ページで物件を確認したうえで割り当てています。
別物件の写真を混ぜないよう、キーの接頭辞を物件に対応させています（`sh`/`pVilla`＝Seahorse、`po`＝Portofino、`g`＝Germany、`cz`/`cazur`＝Côte d'Azur）。

## 注意

- 問い合わせフォームはデモ動作です（送信は行われません）。
- 価格・仕様は変更される場合があります。確定情報は個別案内。
