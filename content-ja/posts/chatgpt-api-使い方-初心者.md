---
title: ChatGPT API初心者向け完全ガイド【2026年版・コピペで動くサンプルコード付き】
date: 2026-04-19
draft: false
slug: chatgpt-api-使い方-初心者
description: ChatGPT APIの使い方を初心者向けに解説。APIキーの取得から最初のリクエスト送信、実用的なアプリ作成まで、コピペで動くPythonサンプルコードとともに丁寧に説明します。
author: Productivity Works編集部
categories:
- AI活用
tags:
- ChatGPT
- OpenAI
ShowReadingTime: true
ShowWordCount: true
ShowToc: true
TocOpen: false
ShowBreadCrumbs: true
---

※本記事にはアフィリエイト広告が含まれています。

# ChatGPT API初心者向け完全ガイド【2026年版・コピペで動くサンプルコード付き】

「ChatGPTをプログラムから使いたい」「自分のサービスにAIを組み込みたい」——そう思ったときに必要なのがChatGPT APIです。

APIと聞くと難しそうに感じるかもしれませんが、基本的な使い方は意外とシンプルです。本記事では、プログラミング経験が少ない方でも理解できるよう、ステップバイステップで解説します。

---

## ChatGPT APIとは何か

APIとは「Application Programming Interface」の略で、ソフトウェア同士が通信するための接続口です。

ChatGPT APIを使うと：
- 自分のPythonプログラムからChatGPTに質問できる
- Webアプリ・Slackbot・業務ツールにAIを組み込める
- ChatGPTの画面を使わず、自動的に大量の処理ができる

つまり、**「ChatGPTを自分のプログラムの部品として使える」**ようになります。

---

## 料金の仕組みを先に理解する

ChatGPT APIは使った量に応じて課金される「従量課金制」です。

### 2026年現在の主な料金

| モデル | 入力（1Mトークン） | 出力（1Mトークン） |
|--------|------------------|------------------|
| GPT-4o mini | 約$0.15 | 約$0.60 |
| GPT-4o | 約$5.00 | 約$15.00 |
| GPT-4 Turbo | 約$10.00 | 約$30.00 |

※料金は変更される可能性があります。最新情報はopenai.com/pricing で確認してください。

**トークンとは：** 英語なら単語の一部、日本語なら数文字に相当する単位。「こんにちは」は約5〜7トークン程度。

**初心者が知っておくべき金額感：** 個人で試す程度なら月数百円〜1,000円以内に収まることがほとんどです。まず$5〜10のクレジットを購入して試してみましょう。

---

## ステップ1：APIキーを取得する

### 1. OpenAIアカウントを作成する
1. platform.openai.com にアクセス
2. 「Sign up」からアカウントを作成（メールアドレスかGoogleアカウントで登録）
3. 電話番号認証を完了させる

### 2. 支払い方法を設定する
1. ダッシュボードの「Billing」→「Add payment method」
2. クレジットカードを登録
3. 「Add credit」から最初のクレジットを購入（$5から）

### 3. APIキーを発行する
1. ダッシュボードの「API Keys」→「Create new secret key」
2. キーの名前を入力して作成
3. **表示されたキーをすぐコピーしてメモする（一度しか表示されない）**

APIキーは`sk-...`から始まる長い文字列です。このキーは他人に見せないでください。GitHubに公開するコードに直接書き込むのはNGです。

---

## ステップ2：Pythonの開発環境を準備する

### Pythonのインストール
Pythonが入っていない場合はpython.orgから3.10以上をインストールします。

### OpenAIライブラリのインストール
ターミナル（コマンドプロンプト）で以下を実行：

```bash
pip install openai
```

### 環境変数にAPIキーを設定する

APIキーをコードに直接書かず、環境変数として設定します。

**Mac/Linux:**
```bash
export OPENAI_API_KEY="sk-あなたのAPIキー"
```

**Windows（コマンドプロンプト）:**
```cmd
set OPENAI_API_KEY=sk-あなたのAPIキー
```

---

## ステップ3：最初のAPIリクエストを送る

以下のコードをコピーして`hello_gpt.py`として保存し、実行してみてください。

```python
from openai import OpenAI

# クライアントを初期化（APIキーは環境変数から自動読み込み）
client = OpenAI()

# ChatGPTにメッセージを送る
response = client.chat.completions.create(
    model="gpt-4o-mini",  # 低コストなモデルを使用
    messages=[
        {
            "role": "user",
            "content": "こんにちは！AIについて一言で説明してください。"
        }
    ]
)

# 返答を表示する
print(response.choices[0].message.content)
```

**実行コマンド:**
```bash
python hello_gpt.py
```

ChatGPTからの返答がターミナルに表示されれば成功です。

---

## ステップ4：応用サンプルコード集

### サンプル1：会話の文脈を保持するチャット

```python
from openai import OpenAI

client = OpenAI()

def chat_with_gpt(conversation_history, user_message):
    """会話履歴を維持しながらChatGPTと対話する関数"""

    # ユーザーのメッセージを履歴に追加
    conversation_history.append({
        "role": "user",
        "content": user_message
    })

    # APIリクエスト
    response = client.chat.completions.create(
        model="gpt-4o-mini",
        messages=conversation_history
    )

    # AIの返答を取得して履歴に追加
    assistant_message = response.choices[0].message.content
    conversation_history.append({
        "role": "assistant",
        "content": assistant_message
    })

    return assistant_message

# 会話を開始
history = [
    {"role": "system", "content": "あなたは親切なアシスタントです。日本語で答えてください。"}
]

print("ChatGPTと話してみましょう（終了するには 'exit' と入力）")

while True:
    user_input = input("\nあなた: ")
    if user_input.lower() == "exit":
        break

    reply = chat_with_gpt(history, user_input)
    print(f"\nChatGPT: {reply}")
```

---

### サンプル2：テキストファイルの要約ツール

```python
from openai import OpenAI

client = OpenAI()

def summarize_file(file_path, max_length=300):
    """テキストファイルを読み込んで要約する関数"""

    # ファイルを読み込む
    with open(file_path, 'r', encoding='utf-8') as f:
        content = f.read()

    print(f"元のテキスト: {len(content)}文字")

    # ChatGPTに要約を依頼
    response = client.chat.completions.create(
        model="gpt-4o-mini",
        messages=[
            {
                "role": "system",
                "content": f"以下のテキストを{max_length}字以内で要約してください。重要なポイントを3つ箇条書きで示した後、全体の要約を記載してください。"
            },
            {
                "role": "user",
                "content": content
            }
        ]
    )

    return response.choices[0].message.content

# 使用例
result = summarize_file("sample.txt")
print(result)
```

---

### サンプル3：CSVデータの分析・コメント生成

```python
import csv
from openai import OpenAI

client = OpenAI()

def analyze_sales_data(csv_file_path):
    """売上CSVデータをAIで分析してコメントを生成する関数"""

    # CSVを読み込んでテキスト形式に変換
    rows = []
    with open(csv_file_path, 'r', encoding='utf-8') as f:
        reader = csv.reader(f)
        for row in reader:
            rows.append(', '.join(row))

    csv_text = '\n'.join(rows)

    # AIに分析を依頼
    response = client.chat.completions.create(
        model="gpt-4o",  # 分析タスクにはより高性能なモデルを使用
        messages=[
            {
                "role": "system",
                "content": "あなたはデータアナリストです。売上データを見て、重要な傾向・問題点・改善提案を日本語で報告書形式でまとめてください。"
            },
            {
                "role": "user",
                "content": f"以下の売上データを分析してください:\n\n{csv_text}"
            }
        ]
    )

    return response.choices[0].message.content

# 使用例
analysis = analyze_sales_data("sales_data.csv")
print(analysis)
```

---

## ステップ5：コストを管理する

### 使用量のモニタリング
OpenAIのダッシュボード（platform.openai.com）の「Usage」ページで、API利用量と費用をリアルタイムで確認できます。

### 支出上限を設定する
ダッシュボードの「Billing」→「Usage limits」で月次の上限金額を設定できます。予期せぬ課金を防ぐため、最初は低い上限（例：$10）を設定しておきましょう。

### コスト削減のポイント
1. **モデルの使い分け：** 単純なタスクはgpt-4o-miniを使う。gpt-4oより10〜30倍安い
2. **システムプロンプトを短くする：** 毎回のリクエストに含まれるため、長すぎるとコストに響く
3. **不要な会話履歴を削る：** 長い会話ではトークン数が増えるため、古い履歴を削除する仕組みを作る

---

## よくあるエラーと対処法

**AuthenticationError**
APIキーが間違っているか、環境変数が読み込まれていません。キーを再確認してください。

**RateLimitError**
短時間にリクエストを送りすぎています。リクエスト間に少し間隔を空けてください（time.sleep(1)など）。

**BadRequestError: maximum context length exceeded**
送信しているテキストが長すぎます。長いテキストは分割して送るか、要約してからAPIに渡してください。

---

## まとめ：APIを使えばAIアプリが作れる

ChatGPT APIを使いこなせるようになると、ビジネスの可能性が大きく広がります。

- 社内の文書自動要約ツール
- 顧客メールの自動分類・返信案生成
- 商品説明文の一括生成
- ChatbotやFAQシステム

最初のステップは「hello_gpt.py」を実行すること。それだけです。一度動く実感を得れば、次のアイデアは自然と生まれてきます。

---

**関連記事**
- ChatGPTを仕事で使う具体的な活用法10選
- すぐ使えるChatGPTプロンプトテンプレート20選
- AIでExcel作業を自動化する方法

---

## 関連テンプレート

この記事で紹介したテクニックをすぐ実践できるテンプレートはこちら：

- [ChatGPTプロンプト集100選](https://prod-works.booth.pm/) — コピペで即使えるプロンプト集
- [AI仕事術 完全ガイド](https://prod-works.booth.pm/) — 50のAIワークフロー収録
- [AI副業スタートキット](https://prod-works.booth.pm/) — AIで副収入を得る実践ガイド
