# Airflow Quick Start Guide

このプロジェクトはApache Airflowのクイックスタートガイドです。

## セットアップ手順

### 1. 仮想環境の作成
```bash
# Python 3.11の仮想環境を作成
python3.11 -m venv venv

# 仮想環境をアクティベート
source venv/bin/activate
```

### 2. Airflowのインストール
```bash
# 環境変数の設定
# AIRFLOW_VERSION: インストールするAirflowのバージョン
# PYTHON_VERSION: 使用するPythonのバージョン
# CONSTRAINT_URL: 依存関係の制約ファイルのURL
export AIRFLOW_VERSION=2.8.1 && export PYTHON_VERSION="3.11" && export CONSTRAINT_URL="https://raw.githubusercontent.com/apache/airflow/constraints-${AIRFLOW_VERSION}/constraints-${PYTHON_VERSION}.txt"

# Airflowのインストール
pip install "apache-airflow==${AIRFLOW_VERSION}" --constraint "${CONSTRAINT_URL}"
```

### 3. Airflowの初期設定
```bash
# AIRFLOW_HOME環境変数の設定（現在のディレクトリを指定）
export AIRFLOW_HOME=$(pwd)

# データベースの初期化
airflow db init

# 管理者ユーザーの作成
# ユーザー名: admin
# パスワード: admin
# メールアドレス: admin@example.com
airflow users create --username admin --firstname admin --lastname admin --role Admin --email admin@example.com --password admin
```

### 4. DAGsディレクトリの作成
```bash
# DAGファイルを格納するディレクトリを作成
mkdir -p dags
```

### 5. Airflowの起動
```bash
# スケジューラーの起動（別のターミナルで実行）
airflow scheduler

# Webサーバーの起動（別のターミナルで実行）
airflow webserver
```

## アクセス方法
- Webインターフェース: http://localhost:8080
- ログイン情報:
  - ユーザー名: admin
  - パスワード: admin

## 注意事項
- スケジューラーとWebサーバーは別々のターミナルで実行する必要があります
- 初回起動時はデータベースの初期化に時間がかかる場合があります
- 本番環境では、より安全なパスワードを使用してください