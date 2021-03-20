Vueとnginxのdocker開発環境  
クローンしたら以下を実行  
  
docker-compose build  
docker-compose up -d  
  
vueコンテナの中に入る。(nginxコンテナではないので注意。)  
docker exec -it [コンテナ名] sh  
  
// コンテナ内に入れたら  
(/app <= 現在のディレクトリを表す)  
  
/app # vue init webpack  
/app # npm install  
/app # npm run build  
  
localhost:9000にアクセスし、表示されるか確認。  
  
nginx上でvueにcssが反映されないため、nginx/server.confに以下を追加。  
参考サイト：  
https://motomichi-works.hatenablog.com/entry/2020/08/09/002839  
  
```
http {
  〜略〜
  include /etc/nginx/mime.types;
  default_type application/octet-stream;
  〜略〜
}
```  
  
※vue-cli · Failed to write the file at: /app/.babelrc  
というエラーが出た場合、docker-compose downでコンテナを削除して、buildからやり直したらちゃんと動いた。

  
参考サイト：  
https://qiita.com/akashixi/items/2ebe9404c64a8854b4e5
