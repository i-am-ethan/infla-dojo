# お題
PCのDockerで起動したWebサーバーにスマホのブラウザでアクセスしてみましょう。


# 回答

## 1. nginxのdockerコンテナを起動する

docker hubに記載されている`How to use this image`を参考にしてnginxのコンテナを起動します。<br>
https://hub.docker.com/_/nginx

### 1-a. Dockerfileとstatic-html-directoryディレクトリを作成する。
以下のような構造になるように作成します。
```
.
├── Dockerfile
└── static-html-directory
```

### 1-b. Dockerfileを記述
```
FROM nginx
COPY ../static-html-directory /usr/share/nginx/html
```

### 1-c. buildのコマンドを実行
`docker build -t some-content-nginx .`

### 1-d. dockerコンテナを動かす
some-nginxという名前でnginxコンテナを起動する。<br>
8080をコンテナの80番ポートにマッピングする。<br>
`docker run --name some-nginx -d -p 8080:80 some-content-nginx`

### 1-e. PCのブラウザでhttp://localhost:8080を開く
`http://localhost:8080`<br>
nginxが立ち上がっていることを確認

## 2. ifconfigで自分のPCのIPを確認する
`ifconfig`<br>
※en0のところに書いてあるIPアドレスを確認する。<br>

今回は`192.168.142.45`でした。

## 3. スマホをPCと同じwifiに接続し、PCのIPと8080ポートにアクセスする。

`192.168.142.45:8080`

## 4. 表示される
<img src="./images/Image.jpeg">





