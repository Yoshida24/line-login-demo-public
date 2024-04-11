# これは何？
LIFFを使ったLINEログインを手軽に試すためのリポジトリ。
個人でLINEログインの学習のために作成した。


## セットアップ

### 下準備
- LINEアカウントをとっておく。普段使っているものでOK。
- https://account.line.biz/login などにアクセスし、LINE Business IDをとっておく。
- Webページが必要になるので、[Netlify](https://www.netlify.com/) など適当なホスティングサービスを使えるようにしておく。


### LINEログインチャネルのURLを取得する
- https://developers.line.biz/ja/services/line-login/ から設定し、URLを入手する。  
- 入力するパラメータは下記テーブルを参考にする。  

    | Name | Value |
    | --- | --- |
    | LIFF app name | demo liff |
    | Endpoint URL | https://your-site-for-example-netlify.com/ |
    | LIFF app name | demo liff |
    | LIFF ID | {チャネルを表す10桁の数値}-{LIFFアプリを表す8文字の英数字} |
    | LIFF URL | https://liff.line.me/{チャネルを表す10桁の数値}-{LIFFアプリを表す8文字の英数字} |
    | Size | Full |
    | Scopes | openid |
    | Bot link feature | On |

- URLを入手したら完了。  
- URL例: https://developers.line.biz/console/channel/{チャネルを表す10桁の数値}

### LIFFアプリを作成する
- https://developers.line.biz/ja/services/liff/ からLIFFアプリを作成する。  
- 入力するパラメータは先ほどと同じテーブルを参考にする。

- URLを入手したら完了。  
- https://developers.line.biz/console/channel/{チャネルを表す10桁の数値}/liff/

### 取得したパラメータを `index.heml` に転記する
- `liffId` を `index.html` に転記する。

### サイトをホスティングする
- `/public` 以下のファイルを適当なホスティングサービスにホストする。

## 動作を検証する
- `index.html` にアクセスする
- `login.html` にアクセスし、1秒待つとLINEログインが実行されることを確認する。この際、`idToken` が表示される。
- ログインするとリダイレクトすることを確認する

## 今後：検証のために
- `liff.init().then` の中で色々なログインデータが取得できるので、ここを触ってみてフロントの動作に目星をつける
- LINEログイン側の設定値を変更し、何が起きるかを検証する
