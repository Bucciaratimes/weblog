---
title: 「なんかテアシュテーゲン調子悪くね？」問題をデータで紐解く
date: 2021-12-10T15:08:06+09:00
lastmod: 2021-12-10T15:08:06+09:00
author: "Bucciarati"
avatar: /images/author.jpg
authorlink: https://twitter.com/Bucciaratimes
cover: /images/report/terStegenNow/cover.jpg
categories:
    - "Barcelona"
tags: 
    - "Report"
draft: false
toc: true # table of contents 目次
autoCollapseToc: false
eyecatch: /images/report/terStegenNow/cover.jpg
---

先月、こんなツイートをしました。

{{<tweet 1457040886571810817>}}

正直あれ以降も思うことはあって、これが感覚的なものなのか現実的な問題なのか、データ的に確かめたいなと思いました。

ということで今回は、テアの調子の良し悪しをデータから判断して、その結果から「バルサのGKはテアのままでいいのか、それとも補強が急務なのか」を考えていこう！という回です。

<hr>
**ソース：[fbref](https://fbref.com/en/)＆[whoscored](https://whoscored.com/)**

**対象コンペティション：<font color="#D64413">国内リーグ</font>**
<hr>

# テアシュテーゲン、不調？問題

まず初めに一般的なGKスタッツで17/18〜21/22のテアを比較してみます。

<details>
<summary>各項目の説明はこちら(Clickで開きます)</summary>
<div>

1. PSxG -> シュート後xG
2. PSxG-GA -> セービング能力
3. GA90 -> 90分あたりの失点数(+50した数字から-100した数字になってます)
4. Saves -> 90分あたりのセーブ数
5. Save% -> セーブ率
6. Save% PK -> PKストップ率
7. Stp% Crosses -> クロスを止めた割合
8. #OPA Sweeper -> 90分あたりのペナルティーエリア外でのディフェンスアクション数
9. AvgDist Sweeper -> 平均ペナルティーエリアからどんくらい離れてディフェンスしたか（90分あたり）
10. Att Passes -> 90分あたりのパス試行数
11. AvgLen_Passes -> パスの長さの平均値（90分あたり）

</div>
</details>

### GKスタッツ比較

最初の図では今シーズンのスタッツ。2番目の図では左上、右上、左下、右下の順に17/18、18/19、19/20、20/21のスタッツを示してます。

※単位がパーセンテージじゃないものは見栄えを良くするために本来の数字に「＋５０」してます。実際の数字は「ー５０」したものになりますので、詳細に見てくれる方は適宜脳内変換していただければと思います。また、21/22シーズンは計１3試合での数字です。

![figure1](/images/report/terStegenNow/image5.png)
![figure2](/images/report/terStegenNow/image6.jpg)

色々な指標を用意しましたが、ぶっちゃけ今回注目するのは「セーブ率」と「PSxG-失点数」だけです。

### セーブ率

セーブ率から見ていきます。以下のようになってます。

- 17/18　79.8％
- 18/19　73.3％
- 19/20　72.7％
- 20/21　71.6％
- 21/22　62.9％

今シーズンが最も低い数字になってます。最もセーブ率が高かったシーズンでは79.8％だったこと、過去４シーズン最低でも70％は超えていたことを考慮すると、この62.９％という数字は際立って悪い数字だということが分かります。

以下は過去４シーズンのラリーガGKの平均値です。

- 17/18　71％
- 18/19　72％
- 19/20　70％
- 20/21　69％

これを見ると、テア（17/18）の79.8％という数字が如何に凄く、テア（21/22）の62.9％という数字が如何に寂しいのかよりいっそう分かると思います。

（ちなみにオブラクは平均80％くらいのセーブ率でした。）

このセーブ率の低下は少なからず「不調に陥ってる！？」という感覚値に影響を及ぼしていそうです。

しかし、セーブ率の低下だけで不調と判断するのは若干強引な気がします。理由は「ゴラッソ級のシュートばかり飛んできてる」とか「失点のシチュエーションが１対１ばかり」とか、そういう可能性があるにも関わらず考慮されてないからです。

ということで、次はそういった可能性を考慮するために「PSxG-失点数」という指標を使って見ることにします。

### PSxG-失点数？

まず、PsxGとは「シュート後のゴール期待値」のことです（ そういう意味でxGは「シュート前のゴール期待値」と解釈できますね ）。

このPSxGの強さは「シュートの質」が考慮されることです（ 普通のxGモデルだとシューターの能力が考慮されないよう設計されてます ）。

「シュートの質」が考慮されることよって、GKにとってそのシュートが止めるべきものだったのかノーチャンスだったのかがハッキリするため、GKのセービング能力をより正確に測れるんじゃん！？という訳です。

具体例としては、PSxGが「0.7」なら「70％の確率で得点が入る凄いシュート」ということになるので、「止めなくても悪くない。セーブできたら凄い！」となり、逆に「0.03」とかなら「3％の確率でしかゴールにならないヘボシュート」ということなので、「止めないとヤバい！アセンシオにカリウスって言われる！」という感じです。

そして、そのPSxGから実際の失点数を引くことで（「0.7」のシュートで失点０だったら＋0.7ポイント！「0.03」のシュートで失点１だったらー0.97ポイント！みたいな感じで ）「セーブした凄さとか、セーブできなかったヤバさ」を数値化し、「PSxGがプラスの値ならパラドンしてる可能性が高いし、マイナスの値なら簡単なシュートもセーブできてない可能性が高い」という情報を得ることができるのです。

ここまで読んで良く分からなかったら（ 正直僕も書いててよくわからなくなってます笑 ）、
結局のところ期待値というのは実質「平均値」なので「PSxGー失点数」の値がプラスなら平均以上、マイナスなら平均以下ということを示してると考えればいいと思います。

<hr>

以上の説明を踏まえて「PSxG-失点数(90分あたり)」の値をみていきます。下記のようになってました。

```
PSxG
・ 17/18　＋0.21
・ 18/19　＋0.09
・ 19/20　-0.03
・ 20/21　-0.03
・ 21/22　-０.12
```

上記の数字は、「90分プレーした場合、17/18〜18/19シーズン頃のテアは本来0.21失点、0.09失点してるところを無失点に抑えてくれていたが、19/20〜20/21シーズンは逆に0.03失点、20/21シーズンは0.12失点ほど献上してしまってる」ということを示しています。

先ほど説明した通り、PSxGの性能上ゴラッソの場合は大きくマイナスされません。今シーズンのバルセロナの失点ペースは１試合1.15点ペースですし、１試合の被シュート数も１０本前後ですから、ゴラッソでマイナスされた分は普通にシュートをセーブしていれば賄える（０周りに収束する）と考えていいでしょう。何ならパラドンがあるならプラスを狙えたかもしれません。

そういう意味で、今シーズンの「-0.12」という数字はちょっとマイナス過ぎるのです。この場合、シュートのセーブ難易度が平均的もしくは平均以下のシュートが失点になってると考えるのが妥当なように思います。

このことから「テア、不調説」は感覚的なものではなく現実に起きてる問題なのだと僕は判断しました。

ちなみに、この状態が１シーズン続くと、以下のようになります（３７試合出場したと仮定）。

```
PSxG
・ 17/18　＋7.7
・ 18/19　＋3.48
・ 19/20　-1.23
・ 20/21　-1.23
・ 21/22　-4.43
```

つまりこれは、「17/18のテアなら実質7ゴールしてくれるが、21/22（今シーズン）は実質4オウンゴール決めるようなもの」ということです。これを見るとテアの不調がこのまま続けば如何に由々しき事態になるのか実感できるのではないでしょうか。

この具合だと正GKの交代は急務に思えますが、これはあくまで現時点の数字で「ちりつも」した場合の話です。残り約25試合の中で17/18、18/19のような活躍を見せてくれればいいのです。

ということで、「バルサのGKはテアのままでいいのか、それとも補強が急務なのか」問題に回答するためには「テアのこの「弱い状態」いつまで続きそうなん？」ということを知る必要がありそうです。

# 疑問：テアの不調はいつまで続く？？

いつまで続くのか？ということを考えるために「過去４シーズンのPSxGの変遷との比較」をしてみることは結構有益そうです。

そもそも17/18だって最初不調だったけど中盤から終盤にかけて卍解したのかもしれませんからね。

ということで、過去５シーズンの変遷をみてみます。

以下のグラフは全て３試合の平均値をプロットしたものです（３試合の平均なのでプロット数は最初と最後は2つずつ消えて全体のマイナス４個分プロットされてます）。

まずは全てのシーズンを一つのグラフにプロットしたものから。

![figure3](/images/report/terStegenNow/image7.jpg)

上図のグラフを見ると、PSxG的には意外にも６節終了時点では今シーズンが最も良いシーズンとなってることが分かります。しかし以降は大きく下がっており中々浮上できてない事が分かります。

パッと見で変遷の仕方が似てるのは20/21シーズンですね。20/21シーズンは膝の怪我というエクスキューズがありますが。

次に１対１の比較をしたものを見てみます。

![figure4](/images/report/terStegenNow/image8.jpg)

#### 17/18

17/18シーズンは、基本的にシーズンを通してプラス値を維持しており、好調のほどが分かります。しかし、変遷としては微妙に下り坂でした。もちろんこのレベルならシーズンを通して好調を維持したと考えていいと思います。

#### 18/19

18/19シーズンは、最初の１５試合くらいはマイナス値を記録してますが、それ以降で大きく回復しており、上り坂のシーズンであることが分かります。終盤にかけてマイナス値を記録していますが、先ほど書いた通りこのシーズンはPSxG「＋3.48」を記録した過去5年間の中では2番目に良いシーズンです。もしかしたら、今シーズンの復活のモデルケース？かもしれません。

#### 19/20

19/20シーズンは、多くの時間をマイナスから0周りを彷徨ったシーズンのようです。成績的には上り坂のシーズンではあるのですが、良くなったというよりは普通になったという感じです。

#### 20/21

20/21シーズンは、最初は調子良くて後は悪いという下り坂のシーズンのようです。昨シーズンはバルセロナ自体は後半にかけて調子を上げた印象があるのでバルセロナのxGの遷移を見たらテアの波と逆な説はありますね。

最後の図は、過去５シーズンを並べたやつです。

![figure5](/images/report/terStegenNow/image9.jpg)

当然ながら下り坂ですね。

正直、テアが18/19シーズンのように「好調」に回復するのか、19/20シーズンのように「普通」に回復するのか、20/21シーズンのように失速を続けるのかは分かりません。身体的な衰えを考えるには早過ぎる年齢ですし。

しかし過去４シーズンで「好調を維持」したシーズンが１回のみ、回復した19/20シーズンは「ゆーて普通に戻っただけ」ということを考えても、18/19シーズンのように「好調の時もある」レベルまで戻る可能性は高くないと思いますし、まして17/18シーズンのような「好調を維持」レベルまで持っていくのは至難の業のように思えますし、常時好調をキープした17/18シーズンがレアケースという見方が正しいのかな？と僕は思っちゃいました。

最後に参考として、先日ヤシン賞を受賞したドンナルンマと現世界最高GKオブラクをみてみましょう。
#### ドンナルンマ

![figure6](/images/report/terStegenNow/image10.jpg)

#### オブラク

![figure7](/images/report/terStegenNow/image11.jpg)

ドンナルンマは若干波がありますが基本的にはプラス値がデフォルトな事が分かります。17/18〜19/20シーズンに関しては10代になると思うので、正直半端ないと思いました。

オブラクはやばいですね。マイナス値がレアケースです。てか今年はあんま調子良くないんですね。

# 結論：「バルサのGKはテアのままでいいのか、それとも補強が急務なのか」

ここまで「テアの不調って現実として起きてることなの？」→「起きてるくさい」、「じゃあいつまで続きそうなん？」→「ぶっちゃけテア神だった17/18がレアケースだった可能性がある」という流れできました。

これを踏まえて僕は「補強資金に限りがあることを考えると優先して補強すべきポジは他にもあるが、GKの補強もなる早で必要。チャビ、大変そうだな。。。」という感想になりました。

僕はドリブラ→サイドバック→退部という変遷をたどった人間で、GKを技術的にあーだこーだ言うことが全くできませんので、今回は100％数字の世界の話です。
もしかしたら数字に現れないところでテアはめちゃくちゃ重要な役割を果たしてるのかもしれません。そもそもテアの長所は足元ですし。

ただ今回色々調べてみて、足元重視のバルサといえどシュートストップ能力が普通より下がデフォルトなのは流石に無視できない問題だと思いました。「金あるの？、誰にするの？」と聞かれると困りますが、「交代するタイミング」は既に訪れてるように思いす。

ここまで読んでいただいた皆さんはどう思いましたか。

テアの復活を信じますか？それとも補強を望みますか？

以上です。読んでいただきありがとうございました。