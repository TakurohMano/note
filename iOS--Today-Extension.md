制限事項
---

- パーミッションはアプリ側のパーミッションが継承される。
- 画面サイズの制約
  * 1 スクロール大くらいの画面しか無理
- 位置情報の制約
  * Today Extension で位置を取るには、アプリ側で「Allow Location Always」という強いパーミッションを取る必要が有る。これは、アプリが裏側で位置情報取る場合のパーミッション。
- CALayer 弄れない
  * 角丸とかやりたいなら、GPUImage で強引にやる
- メモリの制約
  * iPhone5 iOS8.0 の場合、メモリ 6MB くらいで死ぬ。画面に何も表示されない。
  * また、何もしなくても 3MB くらいいく
  * PhotoKit を動かしたら + 1.7MB くらい。
- ジェスチャが取れない
  * TapGestureRecognizer は効く

http://qiita.com/koogawa/items/994878047f76cf125b2d

注意すること
---

- アプリと色々共有出来ない
  * `NSUserDefaults` はちょっとのコードで出来る `http://tapadoo.com/2014/sharing-nsuserdefaults-between-your-app-and-a-today-extension-on-ios-8/`
  * `UIPasteBoard` もちょっとのコードで出来る。
 
NSUserDefaults の共有
---

- AppGroup を作る
- AppGroup の Certificate を登録する

通知情報
---

http://hrk-ys.blogspot.jp/2014/06/whats-new-in-ios-notifications.html

あと某氏から教えてもらった（一応 NDA で伏せておく）

```
知見
・UIView ならだいたい何でも入る（なんでも出来る）
・タップはとれる。ジェスチャーは通知センターにとられる
・URL Request とか普通に出来る
・NSUserDefaults でアプリとデータ共有出来る

kaiinui [11:32 PM]
・入力とかは出来ない（そもそも表示用だし）
・デバイスのセンサーとか（傾き・音声）とれるかは試してない

kaiinui [11:32 PM]
タッチとれるから単純な入力系ならいけそう

kaiinui [11:32 PM]
（初音ミクにタッチしたらおはようウィジェットとか）

kaiinui [11:32 PM]
あとタッチでしか入力出来ないけど zaim の入力とかできそう

kaiinui [11:34 PM]
相当色んなこと出来るし、色んなアプリがここはいりそう（Gunosy, smartnews とかめっちゃやりたそう）

kaiinui [11:34 PM]
音声いけるなら乗り換え案内アプリとかいけるかも

kaiinui [11:34 PM]
・インストールされただけでは有効にならず、通知センターの「編集ボタン」で配置することで初めて表示されるようになる

kaiinui [11:35 PM]
・（だから、こうやって配置するんだてきなインストラクションみたいなのは必要）

kaiinui [11:35 PM]
・（ちなみに画面に飛ばす API はない）

kaiinui [11:35 PM]
・（NSUserDefaults 共有出来るので、有効にしたかどうかはわかる。）

・高さはおおよそ画面いっぱい分（1 スクロール分）くらい。

kaiinui [11:55 PM]
サイズは 3.5 inch と 4 inch でそれぞれ決まってる。

```

