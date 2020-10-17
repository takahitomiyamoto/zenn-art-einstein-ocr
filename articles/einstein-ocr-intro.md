---
title: 'Einstein OCR を試してみよう'
emoji: '🔎'
type: 'tech' # tech: 技術記事 / idea: アイデア
topics: ['ai', 'salesforce', 'einstein']
published: false
---

# はじめに

こんにちは。2019 年より [Salesforce Einstein Champion](https://www.salesforce.com/campaign/einstein-champions/trailblazers/#!page=1&sort=alphaSort&tags=architect_technical) をやらしてもらってる Heat です。
Salesforce 歴は 7 年目くらいです。

今回は、2020 年 5 月に GA (正式リリース) となった、[Einstein OCR](https://releasenotes.docs.salesforce.com/ja-jp/summer20/release-notes/rn_einstein_vision_ocr_ga.htm) について紹介します。

## OCR とは

**O**ptical **C**haracter **R**ecognition、日本語では **光学式文字認識** と呼ばれています。
たとえば紙の申込書をスキャンして、そこに記載されている文字をデータ化してくれるような技術です。

## Einstein OCR とは

Salesforce が提供する、画像中の英数字テキストを検出する OCR モデルです。

> [Einstein OCR を使用した画像内のテキストの検出 (正式リリース)](https://releasenotes.docs.salesforce.com/ja-jp/summer20/release-notes/rn_einstein_vision_ocr_ga.htm)

REST API エンドポイントからモデルにアクセスできるため、呼び出し元が必ずしも Salesforce Platform 上のアプリである必要はありません。

# 何ができるの？

いまのところ 2 つのモデルが用意されています。

1. OCRModel
   - Text : 画像の中で比較的無秩序に並べられている文字列を読み取るとき
   - Contact : 名刺のような一定のルールで並らべられている文字列を読み取るとき
2. tabulatev2
   - Table : 縦横の表形式で並んでいる文字列を読み取るとき

:::message
それぞれのモデルのアクセス方法は、[こちら](https://metamind.readme.io/docs/what-is-einstein-ocr) のガイドに記載されています ✨
:::

:::message alert
本エントリを執筆している 2020 年 10 月 17 日時点では、日本語の読み取りについて正式にはサポートされていません。今後のアップデートを注視していきましょう 👀
:::

あとはアイディア次第でいろいろなことができると思います。
Salesforce にデータをためる時に、これまではパソコンのキーボードを叩いて入力していました。あるいは、メールの文面を取り込んで入力するような機能[^1]もありました。
[^1]: **メール-to-ケース** です。詳細は[こちら](https://trailhead.salesforce.com/ja/content/learn/modules/service_basics/service_basics_create_customer_channels)

今度は、画像のアップロードで入力できるとしたら、、、と考えることになります。しかも、不正確なデータが入力されることも事前に想定しておく必要がありますよね。
何か思いついたらぜひ教えてください。私もそのうち作って公開します 😎

# どうやったら試せるの？

上述のガイドには、Einstein Platform Services の Vision API をコマンドラインから試す方法が記載されていました。
今回は Salesforce Platform 上のアプリ **Einstein Playground** から試す方法を紹介します。

## 事前準備

半年前くらいに主催したワークショップにて手順をまとめてありましたので今回も流用します。
[こちら](https://github.com/takahitomiyamoto/einstein-platform-services-basic/wiki/Prerequisite) を完了させてください。

Salesforce の画面に Einstein Playground アプリが表示できていれば OK です。

![Einstein Playground - OCR](https://raw.githubusercontent.com/takahitomiyamoto/zenn-art-einstein-ocr/main/articles/einstein-playground-ocr.png)

この事前準備を完了させることがいちばんのハードルだと思います。もし自力でできない場合は、後述の勉強会でサポートできますよ 😉

## 実行

読み取りたい画像を何枚か用意します。今回は、「PC に貼ったステッカー」と「名刺」と「手書きの表」の画像でやってみます。
使うモデルを選択して、画像をアップロードしてください。自動的に API が呼ばれ、結果が表示されます。

### Text

小さいフクロウ (Hootie) の胸に書かれている小さい文字も正確に読み取っていました。やはり英数字には強いですね。

![Text](https://raw.githubusercontent.com/takahitomiyamoto/zenn-art-einstein-ocr/main/articles/einstein-playground-ocr-text.png)

### Contact

けっこう正確に認識できていますね。1 つの文字列だけどそれが改行されてる場合は別々のデータとして認識されています。やはり日本語は変な英数字として認識されてました。

![Contact](https://raw.githubusercontent.com/takahitomiyamoto/zenn-art-einstein-ocr/main/articles/einstein-playground-ocr-contact.png)

### Table

手書きの表なのに、何行目の何列目のデータなのかも認識できているのはすごいですね。もちろん日本語は変な英数字として認識されてました。

![Table](https://raw.githubusercontent.com/takahitomiyamoto/zenn-art-einstein-ocr/main/articles/einstein-playground-ocr-table.png)

あっという間に試せてしまいました。コマンドラインで試すよりも直感的にできたと思います。
これらの解析結果のデータは JSON 構造で取得できていますので、次のビジネスロジックへデータを渡すことが容易です。

...何かいいアイディア浮かびましたか？ 🤔

# さいごに

本エントリを通じて Einstein Platform に興味を持っていただけたら幸いです。
このほかにも Salesforce 公式の学習教材がたくさんありますので、ぜひ触ってみてください 💪🏽

:::message
おすすめの Einstein コンテンツは [こちら](https://trailhead.salesforce.com/ja/users/takahito0508/trailmixes/road-to-einstein-champion) にまとめてあります。
:::

それではまたお会いしましょう。どうぞお元気で。

# おまけ

定期的に開催している土曜日のもくもく会で一緒に勉強しませんか？
一人で進めるもよし、私たちメンターに質問するもよし。本エントリのフィードバックもお待ちしております。
お気軽にご参加ください 🌈

@[tweet](https://twitter.com/takahito0508/status/1315938589826379776)
