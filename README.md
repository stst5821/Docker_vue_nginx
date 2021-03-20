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
  
※vue-cli · Failed to write the file at: /app/.babelrc  
というエラーが出た場合、docker-compose downでコンテナを削除して、buildからやり直したらちゃんと動いた。

  
参考サイト：  
https://qiita.com/akashixi/items/2ebe9404c64a8854b4e5
