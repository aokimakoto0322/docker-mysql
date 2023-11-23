# mysql 環境構築

# 導入するソフト
 - visual studio code  
 (ソースコードを編集するソフトです。特に編集はしないですが、あるにこしたことはないのでインストールする）
 - docker desktop  
  (仮想の環境を構築できるソフトです。1コマンドで構築＆本番環境と同様の環境構築できるので便利です。）
 - A-5:SQL Mk-2  
   (SQLクライアントという、取得したデータを簡単に閲覧できたりする便利なソフトです)

# visual studio codeのインストール

1. 下記URLより、visual studio codeをダウンロード  
https://code.visualstudio.com/download

2. ダウンロードしたファイルを実行し、インストール  
※すべて「はい」でインストールしてOKです

3. インストール完了し、この画面が出ればとりあえず完了

# docker desktopのインストール
※基本はこのページをもとにインストールを進めて行きます  
https://chigusa-web.com/blog/windows%E3%81%ABdocker%E3%82%92%E3%82%A4%E3%83%B3%E3%82%B9%E3%83%88%E3%83%BC%E3%83%AB%E3%81%97%E3%81%A6python%E7%92%B0%E5%A2%83%E3%82%92%E6%A7%8B%E7%AF%89/

1. 下記URLより、「Docker Desktop for Windows」を押してdocker desktopをダウンロード  
https://docs.docker.com/desktop/install/windows-install/  

2. ダウンロードしたファイルを実行し、インストール  
※全部「OK」でインストールしてOKです

3. ダウンロード完了したら、「Close and Restart」で再起動します

4. 再起動後、`Docker Subscription Service Agreement`みたいな画面が出てくるので「Accept」を押す

5. `Finish settings up Docker Desktop`の画面が出てくるので「Finish」で完了

6. 完了後、Sign upの画面が出るが、`Continue without signing in`を押す  
SignInすると、便利な機能みたいなのが使えるが、今回特に使わないのでよい

7. `Tell us about the work you do`という画面からrole(職業)、`What will you use Docker for?`より目的を選択し「Continue」を押す  
※今回は、mysqlのローカル環境構築なので、下記のように設定した。
   - What’s your role?: Back-end developer
   - What will you use Docker for? : Learning or teaching  

8. 下記のような画面が出ればとりあえず成功  
![docker](https://github.com/aokimakoto0322/docker-mysql/assets/43976208/83779629-68ee-4769-a84d-d2b2d1eca929)

## dockerがインストールできたか確認  
1. visual studio codeのターミナルから、下記コマンドを入力  
`docker ps`

2. 画像のように文字が出ればOK  
![docker-ps](https://github.com/aokimakoto0322/docker-mysql/assets/43976208/3744fa2b-8133-4390-a6ca-e791a2f74313)

# mysql環境構築
1. docker desktopを開く
1. 下記URLの`Code`から、環境構築用のZipファイルをダウンロードする  
![download_dockerfile](https://github.com/aokimakoto0322/docker-mysql/assets/43976208/e56a492a-8e69-43f0-b430-738f0d4fb9f6)
1. ダウンロードしたファイルを解凍し、任意の場所に配置する
1. 配置後、docker/db/my.cnfを読み取り専用にする
![setup_mycnf](https://github.com/aokimakoto0322/docker-mysql/assets/43976208/a1497073-4dea-4bbb-8b49-8b3a9ccc2fb8)
1. visual studio codeを開く
1. `open folder...`より、2で配置したフォルダを選択し、`「フォルダを選択」`を押す
1. 開いた後、terminalを開き下記コマンドを入力し、エンターを押す  
`docker compose up -d`
![docker_compose_up](https://github.com/aokimakoto0322/docker-mysql/assets/43976208/82421740-5554-4755-8df1-d47c5176ccd8)
1. docker desktopが下記画像のようになっていたら、環境構築成功  
![dockerdesktop_mysql](https://github.com/aokimakoto0322/docker-mysql/assets/43976208/5de0a0e9-79d2-4b8e-ab0e-983dc0474afe)

# 軽く動作チェック
1. docker desktopより、mysql-1を押す
![docker_exec](https://github.com/aokimakoto0322/docker-mysql/assets/43976208/7892a20a-4443-49fc-a497-9b73b38bae21)
1. `exec`タブを開く  
![docker_exec2](https://github.com/aokimakoto0322/docker-mysql/assets/43976208/fdcaa7eb-93a5-41fc-a24f-ee8ccdc09525)
1. mysqlログインする  
※ユーザー名: user、パスワード: password  
※docker-compose.ymlで設定してあるやつです。  
![mysql_login](https://github.com/aokimakoto0322/docker-mysql/assets/43976208/50e8dfec-2c41-42e8-a29c-323f948a31b4)
1. `SHOW DATABASES;`でデータベースを確認する  
※ここにある`dockerTestDb`というデータベースは、docker-compose.ymlで定義したデータベースです。
![show_databases](https://github.com/aokimakoto0322/docker-mysql/assets/43976208/4ae6068b-52f5-4692-b7c6-bdce02f19cd8)
1. `use dockerTestDb`でデータベースの中に入って、`show tables;`でテーブルを確認する  
※ここにあるテーブル３つは、テスト用のテーブルです。MySQL公式のサンプルです。
![show_tables](https://github.com/aokimakoto0322/docker-mysql/assets/43976208/9bcd767a-3c81-41dc-ac58-d4e76153fb3a)
1. ちょっとテーブルの中身を見てみる  
![select_table](https://github.com/aokimakoto0322/docker-mysql/assets/43976208/ab7fbe70-b178-49de-884b-b4b697c87c9f)

# 応用：SQLクライアントを使う
- 軽く動作チェックの項目でもデータベースの動きを確認できますが、ログインなど結構面倒なので、SQLクライアントを使ってデータをみたりすることが多いです。
- なので、SQLクライアントからテーブル操作できるようさらにソフトをインストール＆環境構築をします。

1. A-5:SQL Mk-2を下記URLからダウンロードする(MicroSoft Storeからダウンロードが便利かも)  
https://a5m2.mmatsubara.com/
1. 「入手」を押してダウンロード&インストールする
1. インストール完了後、A-5:SQL Mk-2を開き、「追加」を押してワークスペースを作成する  
![a5sql1](https://github.com/aokimakoto0322/docker-mysql/assets/43976208/bd773fb2-f7c8-4957-a463-ca794cbb57dd)
1. 起動を押して、初期画面から「追加」→「MySQL/MariaDB(直接接続)を押しデータベース接続設定を行う
![a5sql2](https://github.com/aokimakoto0322/docker-mysql/assets/43976208/bbaf6c77-5add-4c88-9dc5-c3104fcc7a1e)
1. root権限で設定し、設定を行う  
![a5_mysql_connect](https://github.com/aokimakoto0322/docker-mysql/assets/43976208/f401cc52-f535-450d-9732-8976590c2744)
1. 接続後、クエリを打つといい感じにデータが取れて、Excelに出力できたりする
![a5_query](https://github.com/aokimakoto0322/docker-mysql/assets/43976208/9c959510-4589-42e9-94ef-8e822c0d3d3c)


# 備考
テスト用にあるテーブルはMySQL公式からダウンロードしてきたやつなので、テーブルの解説などは下記を参照
- https://dev.mysql.com/doc/index-other.html
- https://qiita.com/yukibe/items/fc6016348ecf4f3b10bf