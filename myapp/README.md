# 環境構築
①'docker-compose run web rails new . --force --no-deps --database=mysql --skip-test --webpacker'

②’docker-compose run web rails new . --force --no-deps --database=mysql --skip-test --webpacker’

③'docker-compose build'

# rails new で作成された config/database.yml を編集します
④'default: &default
  adapter: mysql2
  encoding: utf8mb4
  pool: <%= ENV.fetch("RAILS_MAX_THREADS") { 5 } %>
  username: <%= ENV.fetch("MYSQL_USERNAME", "root") %>
  password: <%= ENV.fetch("MYSQL_PASSWORD", "password") %>
  host: <%= ENV.fetch("MYSQL_HOST", "db") %>

development:
  <<: *default
  database: myapp_development

test:
  <<: *default
  database: myapp_test

production:
  <<: *default
  database: myapp_production
  username: myapp
  password: <%= ENV['MYAPP_DATABASE_PASSWORD'] %>'

# データベース作成
⑤'docker-compose run web rake db:create'

# コンテナ起動
⑥'docker-compose up'
