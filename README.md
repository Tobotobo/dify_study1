# dify_study1

## 概要
* Dify を Docker で構築してみる

Dify  
https://dify.ai/jp  
https://github.com/langgenius/dify  
先進的なAIアプリケーションのためのイノベーションエンジン  
> DifyはオープンソースのLLMアプリ開発プラットフォームです。RAGエンジンを使用して、エージェントから複雑なAIワークフローまでLLMアプリを編成します。
> LangChain よりも本番環境に適しています。

## 詳細

### Dify - Docker Compose デプロイ    
https://docs.dify.ai/ja-jp/getting-started/install-self-hosted/docker-compose  

```sh
git clone https://github.com/langgenius/dify.git --branch 1.3.1
```

```sh
cd dify/docker
cp .env.example .env
docker compose up -d
```

http://localhost/install  
![alt text](docs/images/1745590604199.png)

よくある質問  
https://docs.dify.ai/ja-jp/getting-started/install-self-hosted/faqs  
* http://localhost にアクセスすると Internal Server Error が表示される
  * [6. docker-api-1 でのデータベース接続エラーの解決方法とは？](https://docs.dify.ai/ja-jp/getting-started/install-self-hosted/faqs#id-6-docker-api-1-denodtabsuernotoha)  
    > 解決策：dbコンテナ内の/var/lib/postgresql/pgdata/pg_hba.confを変更し、エラーメッセージに記載されているネットワークセグメントを認証リストに追加します。

ローカルデプロイに関するFAQ  
https://docs.dify.ai/ja-jp/learn-more/faq/install-faq  

LLM設定と使用に関するFAQ  
https://docs.dify.ai/ja-jp/learn-more/faq/llms-use-faq  

## Dify で無料の Gemini を使用する

[初心者🔰] DifyでGemini Proを無料で利用する方法  
https://note.com/dify_lab/n/na69c2e7d05bb  

* 設定 > モデルプロバイダー > Gemini をインストール
* 設定中 > Gemini > API-KEY セットアップ

### 【重要】Gemini `0.2.0` は正常に動作しないため `0.1.5` にダウングレードする
* 右上プラグイン
* 左の Gemini を選択
* 右の Gemini のバージョンをクリック
* バージョンの切り替えで 0.1.5 を選択
![alt text](docs/images/1745899509390.png)

## Dify のバージョンアップ 
```sh
cd dify/docker 
docker compose down
git fetch origin tag 1.3.1
git checkout tags/1.3.1
sudo tar -cvf volumes-$(date +%s).tgz volumes
docker compose up -d
```

## ルー語
```
あなたはルー大柴AIです。回答は以下に記載するルー語を使用してください。
ルー語
・タレントのルー大柴が使用する怪しいカタカナ語を多く交えた文章を指す語である
・日本語から英単語に直せそうな単語をカタカナにする
例①
日本語→英単語に直せそうなワードをカタカナにする→ルーランゲージと言う変換でクリエイションされる。
そのチェンジでプロデュースした日本語とカタカナランゲージのレートによってルーランゲージ精度がデシジョンされる。
例②
・一緒にしようぜ → トゥギャザーしようぜ！ 
・一寸先は闇 → 一寸先はダーク 
・さじ加減 → スプーン加減 
・また行こう → アゲイン行こう 
・寝耳に水 → 寝耳にウォーター 
・八方美人 → 八方ビューティー 
・馬子にも衣装 → 馬子にもドレス 
・渡りに舟 → 渡りにシップ 
・高嶺の花 → 高嶺のフラワー 
・焼け石に水 → 焼け石にウォーター 
・鶴の一声 → 鶴のワンボイス 
・数から棒 → 数からスティック 
・合わせる顔がない → 合わせるフェイスがない 
・いい加減にしろ → いい加減にホワイト 
・言わぬが花 → 言わぬがフラワー 
・鯉の滝登り → カープの滝登り 
・苦しい時の神頼み → 苦しい時のゴッド頼み 
・逆鱗に触れる → 逆鱗にタッチ 
・三日坊主 → スリーデイズ坊主
```
https://www.weblio.jp/content/%E3%83%AB%E3%83%BC%E8%AA%9E  
https://dic.nicovideo.jp/a/%E3%83%AB%E3%83%BC%E8%AA%9E  
https://hana555.net/ru-oosiba-goroku-2297#i-3  

やばい AI ができた
![alt text](docs/images/1745900616778.png)

