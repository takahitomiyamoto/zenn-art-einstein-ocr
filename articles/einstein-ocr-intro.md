---
title: 'Einstein OCR を試してみよう'
emoji: '🔎'
type: 'tech' # tech: 技術記事 / idea: アイデア
topics: ['ai', 'salesforce', 'einstein']
published: false
---

# はじめに

こんにちは。2019 年より [Salesforce Einstein Champion](https://www.salesforce.com/campaign/einstein-champions/trailblazers/#!page=1&sort=alphaSort&tags=architect_technical) をやらしてもらってる Heat です。

今回は、2020 年 5 月に GA (正式リリース) となった、[Einstein OCR](https://releasenotes.docs.salesforce.com/ja-jp/summer20/release-notes/rn_einstein_vision_ocr_ga.htm) について紹介します。

> OCR = Optical Character Recognition (光学文字認識)

:::message
[こちら](https://metamind.readme.io/docs/what-is-einstein-ocr) のガイドに沿って解説していきます。
:::

:::message alert
本エントリを執筆している 2020 年 10 月 xx 日時点では、日本語の読み取りについて正式にはサポートされていません。今後のアップデートを注視していきましょう 👀
:::

# 何ができるの？

# どうやったら試せるの？

## 事前準備

Einstein Platform Services の Vision API をコールするために、まずは事前準備をします。
半年前くらいに主催したワークショップにて手順をまとめてありますので、[こちら](https://github.com/takahitomiyamoto/einstein-platform-services-basic/wiki/Prerequisite) を完了させてください。
Salesforce の画面に Einstein Playground アプリが表示できていれば OK です。

![Einstein Playground - OCR](https://raw.githubusercontent.com/takahitomiyamoto/zenn-art-einstein-ocr/main/articles/einstein-playground-ocr.png)

次に、読み取りたい画像を何枚か用意します。今回は、「名刺」と「手書きの表」の画像にしてみます。

API を実行

# さいごに

本エントリを通じて Einstein Platform に興味を持っていただけたら幸いです。
このほかにも Salesforce 公式の学習教材がたくさんありますので、ぜひ触ってみてください 💪🏽

:::message
おすすめのコンテンツは [こちら](https://trailhead.salesforce.com/ja/users/takahito0508/trailmixes/road-to-einstein-champion) にまとめまています。
:::

# おまけ

定期的に開催している土曜日のもくもく会で一緒に勉強しませんか？
一人で進めるもよし、私たちメンターに質問するもよし。お待ちしてますー
@[tweet](https://twitter.com/takahito0508/status/1315938589826379776)
