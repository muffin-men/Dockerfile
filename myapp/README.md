# 環境構築
①'docker-compose run web rails new . --force --no-deps --database=mysql --skip-test --webpacker'

②'docker-compose build'

# rails new で作成された config/database.yml を編集します
④
 'default: &default </br>
  adapter: mysql2 </br>
  encoding: utf8mb4 </br>
  pool: <%= ENV.fetch("RAILS_MAX_THREADS") { 5 } %> </br>
  username: root </br>
  password: password </br>
  host: localhost </br>
  host: db

development: </br>
  <<: *default </br>
  database: myapp_development </br>
  socket: '/tmp/mysql.sock' </br>
  
test:
  <<: *default </br>
  database: myapp_test </br>

production: </br>
  <<: *default </br>
  database: myapp_production </br>
  username: myapp </br>
  password: <%= ENV['MYAPP_DATABASE_PASSWORD'] %>' </br>

# データベース作成
⑤'docker-compose run web rails db:create'

# コンテナ起動
⑥'docker-compose up'
