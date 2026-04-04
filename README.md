# Quote Editor

[Hotrails](https://www.hotrails.dev/)でTurbo Rails / Hotwireを学習するためのレポジトリです。

## Goal

Hotwire（Turbo / Stimulus）を使ったCRUDアプリの実装理解

## Dependencies

- Ruby 3.4.7
- Rails 7.0.8
- Node 24系（推奨）
- Yarn
- PostgreSQL

## Setup

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

```ruby
gem "turbo-rails", "~> 1.0"
```

### 5. セットアップ

```bash
bundle install
bin/setup
bin/dev
```

## Known Issues（ハマりポイント）

### Yarn未導入問題

- `rails new --javascript=esbuild` 実行前に Yarn が必要
- 未導入だと Turbo / Stimulus の依存が壊れる

---

### Node 25 問題

- Node 25系で以下エラーが発生することがある

```bash
Error: EBADF: bad file descriptor, fstat
```

Node 24系を推奨します。

---

### minitest 6 問題

- system test 実行時にエラー

```bash
'run': wrong number of arguments (given 3, expected 1..2)
```

#### 対処

```ruby
group :test do
  gem "minitest", "< 6"
end
```

```bash
bundle update minitest
bin/rails test:system
```

## Test

```bash
bin/rails test:system
```

## Services

WIP

## Deployment

WIP
