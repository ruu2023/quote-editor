# Quote Editor

[Hotrails](https://www.hotrails.dev/)でTrubo Rails / Hotwire を学習するためのレポジトリです。

## dependencies

- Ruby 3.4.7
- Rails 7.0.8
- Node 24系推奨
- Yarn
- PostgreSQL
- Configuration

## setup

### 1. Yarn 有効化

```bash
npm install -g corepack
corepack enable
corepack prepare yarn@stable --activate
yarn -v
```

### 2. Rails 7.0.x の logger 問題を回避

```bash
export RUBYOPT="-rlogger"
```

### 3. アプリ作成

```bash
rails _7.0.8_ new quote-editor --css=sass --javascript=esbuild --database=postgresql
```

### 4. turbo-rails のバージョン固定

```bash
gem "turbo-rails", "~> 1.0"
```

### 5. セットアップ

```bash
bundle install
bin/setup
bin/dev
```

### 想定される問題

- Yarn 未導入のまま rails new --javascript=esbuild すると JS 依存が不完全になる
- Node 25系では EBADF に当たる可能性があるため Node 24系推奨

```bash
Error: EBADF: bad file descriptor, fstat
...
```

- minitest 6 で system test が壊れることがあり

```bash
'run': wrong number of arguments (given 3, expected 1..2) (ArgumentError)
...in Minitest::Runnable.run_suite'
```

- minitest < 6 を Gemfileに指定する

```Gemfile
group :test do
  gem "minitest", "< 6"
end
```

```bash
bundle update minitest
bin/rails test:system
```

### テスト

- How to run the test suite

```bash
bin/rails test:system
```

- Services (job queues, cache servers, search engines, etc.)

```bash
WIP
```

- Deployment instructions

```bash
WIP
```
