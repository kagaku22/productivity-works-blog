---
title: "Excel関数よく使うもの一覧【2026年版・コピペ即使える】仕事で役立つ厳選50選"
date: 2026-04-06
slug: "excel-kansu-yoku-tsukau-ichiran"
description: "仕事でよく使うExcel関数を50個厳選して一覧化。VLOOKUP・IF・SUMIF・COUNTIFなど基本から応用まで、使い方と例をセットで解説します。"
categories: ["ツール・テンプレート"]
tags: ["Excel", "Excel関数", "仕事術", "スプレッドシート", "業務効率化"]
author: "Productivity Works編集部"
draft: false
ShowReadingTime: true
ShowWordCount: true
ShowToc: true
TocOpen: false
ShowBreadCrumbs: true

cover:
  image: "images/covers/excel-kansu-yoku-tsukau-ichiran.png"
  alt: "Excel関数よく使うもの一覧【2026年版・コピペ即使える】仕事で役立つ厳選50選"
  relative: false
---

※本記事にはアフィリエイト広告が含まれています。

「Excelで使える関数が多すぎてどれを覚えればいいかわからない」という方のために、**仕事で本当によく使うExcel関数を50個厳選して一覧化**しました。コピペしてすぐ使えるよう、書式と実例をセットで解説します。

---

## Excel関数カテゴリ別一覧

### カテゴリ1：検索・参照系関数（必須中の必須）

ビジネスで最もよく使われるカテゴリです。

#### VLOOKUP（縦方向の検索）

```excel
=VLOOKUP(検索値, 範囲, 列番号, 検索方法)
```

**例：** 社員番号から氏名を取得
```excel
=VLOOKUP(A2, 社員マスタ!A:D, 2, FALSE)
```

使用頻度：★★★★★　最重要関数。まずこれをマスターしましょう。

#### XLOOKUP（VLOOKUPの進化版 ※Excel 2019以降）

```excel
=XLOOKUP(検索値, 検索範囲, 返す範囲, 見つからない場合)
```

**例：**
```excel
=XLOOKUP(A2, 社員マスタ!A:A, 社員マスタ!B:B, "該当なし")
```

VLOOKUPより柔軟で、左方向の検索もできます。

#### INDEX + MATCH（最強の組み合わせ）

```excel
=INDEX(返す範囲, MATCH(検索値, 検索範囲, 0))
```

**例：** 商品名から価格を取得
```excel
=INDEX(B:B, MATCH(D2, A:A, 0))
```

VLOOKUPが使えない状況や複雑な参照に使います。

#### HLOOKUP（横方向の検索）

```excel
=HLOOKUP(検索値, 範囲, 行番号, 検索方法)
```

横並びのデータから検索する場合に使用。

---

### カテゴリ2：条件判定・分岐系関数

#### IF（条件分岐の基本）

```excel
=IF(条件, 真の場合, 偽の場合)
```

**例：** 60点以上を「合格」、未満を「不合格」
```excel
=IF(B2>=60, "合格", "不合格")
```

#### IFS（複数条件の分岐）

```excel
=IFS(条件1, 値1, 条件2, 値2, ...)
```

**例：** 成績をランク分け
```excel
=IFS(B2>=90,"A", B2>=70,"B", B2>=60,"C", TRUE,"D")
```

ネストしたIFよりずっと読みやすくなります。

#### IF + AND / OR の組み合わせ

```excel
=IF(AND(B2>=60, C2>=80), "合格", "不合格")
=IF(OR(B2>=90, C2>=90), "優秀", "普通")
```

#### IFERROR（エラー時の代替値）

```excel
=IFERROR(数式, エラー時の値)
```

**例：**
```excel
=IFERROR(VLOOKUP(A2, マスタ!A:B, 2, FALSE), "データなし")
```

#N/Aや#DIV/0!などのエラーを非表示にしたいときに必須。

---

### カテゴリ3：集計・合計系関数

#### SUM（合計）

```excel
=SUM(A1:A100)
=SUM(A1,B1,C1)
```

#### SUMIF（条件付き合計）

```excel
=SUMIF(条件範囲, 条件, 合計範囲)
```

**例：** 部署が「営業部」の売上合計
```excel
=SUMIF(B:B, "営業部", C:C)
```

#### SUMIFS（複数条件の合計）

```excel
=SUMIFS(合計範囲, 条件範囲1, 条件1, 条件範囲2, 条件2)
```

**例：** 2026年1月の営業部売上合計
```excel
=SUMIFS(C:C, B:B, "営業部", D:D, "2026/1")
```

#### SUBTOTAL（フィルター後の集計）

```excel
=SUBTOTAL(9, A1:A100)  ※9=SUM
```

フィルターで絞り込んだデータだけを合計できます。通常のSUMはフィルター非表示行も合計してしまうため要注意。

---

### カテゴリ4：カウント系関数

#### COUNT（数値のカウント）

```excel
=COUNT(A1:A100)
```

#### COUNTA（空白以外のカウント）

```excel
=COUNTA(A1:A100)
```

文字列も含めてカウントしたい場合はCOUNTA。

#### COUNTIF（条件付きカウント）

```excel
=COUNTIF(範囲, 条件)
```

**例：** 「合格」の数をカウント
```excel
=COUNTIF(B:B, "合格")
```

#### COUNTIFS（複数条件のカウント）

```excel
=COUNTIFS(範囲1, 条件1, 範囲2, 条件2)
```

**例：** 営業部で売上100万以上の件数
```excel
=COUNTIFS(B:B, "営業部", C:C, ">=1000000")
```

---

### カテゴリ5：文字列操作系関数

#### LEFT / RIGHT / MID（文字列の切り出し）

```excel
=LEFT(A1, 3)       ※左から3文字
=RIGHT(A1, 4)      ※右から4文字
=MID(A1, 3, 5)     ※3文字目から5文字
```

**例：** 郵便番号の上3桁を取得
```excel
=LEFT(A2, 3)
```

#### LEN（文字数カウント）

```excel
=LEN(A1)
```

#### FIND / SEARCH（文字列の位置検索）

```excel
=FIND("@", A1)   ※大文字小文字区別あり
=SEARCH("@", A1) ※区別なし
```

メールアドレスからドメインを抽出するときなどに使います。

#### SUBSTITUTE（文字列置換）

```excel
=SUBSTITUTE(A1, "旧文字", "新文字")
```

**例：** スペースをすべて削除
```excel
=SUBSTITUTE(A1, " ", "")
```

#### TRIM（前後のスペース削除）

```excel
=TRIM(A1)
```

外部データ取り込み時のスペース問題を解決します。

#### CONCAT / TEXTJOIN（文字列の結合）

```excel
=CONCAT(A1, " ", B1)
=TEXTJOIN(", ", TRUE, A1:A10)
```

TEXTJOINは区切り文字を指定して範囲内の文字列をまとめて結合できます。

#### TEXT（数値を文字列に変換）

```excel
=TEXT(A1, "yyyy/mm/dd")
=TEXT(B1, "#,##0")
```

日付や数値を指定フォーマットで文字列化する際に必須。

---

### カテゴリ6：日付・時刻系関数

#### TODAY / NOW（現在の日付・時刻）

```excel
=TODAY()   ※今日の日付
=NOW()     ※現在の日時
```

#### YEAR / MONTH / DAY（年月日の抽出）

```excel
=YEAR(A1)
=MONTH(A1)
=DAY(A1)
```

#### DATEDIF（日数・月数・年数の計算）

```excel
=DATEDIF(開始日, 終了日, "D")  ※日数
=DATEDIF(開始日, 終了日, "M")  ※月数
=DATEDIF(開始日, 終了日, "Y")  ※年数
```

**例：** 入社日から勤続年数を計算
```excel
=DATEDIF(B2, TODAY(), "Y")
```

#### NETWORKDAYS（営業日数の計算）

```excel
=NETWORKDAYS(開始日, 終了日, 祝日リスト)
```

土日・祝日を除いた営業日数を計算します。

#### EOMONTH（月末日の取得）

```excel
=EOMONTH(A1, 0)   ※A1の月の月末
=EOMONTH(A1, 1)   ※翌月末
```

---

### カテゴリ7：統計・数学系関数

#### AVERAGE（平均）

```excel
=AVERAGE(A1:A100)
```

#### AVERAGEIF（条件付き平均）

```excel
=AVERAGEIF(範囲, 条件, 平均範囲)
```

#### MAX / MIN（最大値・最小値）

```excel
=MAX(A1:A100)
=MIN(A1:A100)
```

#### LARGE / SMALL（上位・下位N番目の値）

```excel
=LARGE(A1:A100, 3)  ※3番目に大きい値
=SMALL(A1:A100, 2)  ※2番目に小さい値
```

#### RANK（順位付け）

```excel
=RANK(A2, A:A, 0)  ※0=降順
```

#### ROUND / ROUNDUP / ROUNDDOWN（四捨五入・切り上げ・切り捨て）

```excel
=ROUND(A1, 2)      ※小数点2桁で四捨五入
=ROUNDUP(A1, 0)    ※整数に切り上げ
=ROUNDDOWN(A1, 0)  ※整数に切り捨て
```

---

### カテゴリ8：便利な新関数（Excel 365・2021以降）

#### FILTER（条件でデータを抽出）

```excel
=FILTER(配列, 条件, 空の場合)
```

**例：** 売上が100万以上の行を抽出
```excel
=FILTER(A2:D100, C2:C100>=1000000, "該当なし")
```

#### SORT（データを並び替え）

```excel
=SORT(配列, 並び替え列, 順序)
```

#### UNIQUE（重複を除いてリスト化）

```excel
=UNIQUE(A1:A100)
```

#### SEQUENCE（連番を自動生成）

```excel
=SEQUENCE(10)        ※1〜10
=SEQUENCE(5, 3)      ※5行3列の連番
```

---

## 覚えておくべき関数 優先度ランキング

| 優先度 | 関数 | 理由 |
|---|---|---|
| ★★★★★ | VLOOKUP / XLOOKUP | 最も使用頻度が高い |
| ★★★★★ | IF / IFS | 条件分岐は必須 |
| ★★★★★ | SUMIF / SUMIFS | 集計作業に必須 |
| ★★★★★ | COUNTIF / COUNTIFS | データ集計に必須 |
| ★★★★★ | IFERROR | エラー対策に必須 |
| ★★★★☆ | INDEX + MATCH | VLOOKUP の上位互換 |
| ★★★★☆ | TRIM / SUBSTITUTE | データクレンジングに重要 |
| ★★★★☆ | TEXT | 日付・数値の書式変換 |
| ★★★☆☆ | DATEDIF | 日数計算でよく使う |
| ★★★☆☆ | FILTER / UNIQUE | 365ユーザーなら必須 |

---

## よくある失敗と対処法

### 失敗1：VLOOKUPで#N/Aが出る

- 検索値に余分なスペースが入っている → TRIMで解決
- 検索値のデータ型が違う（数値vs文字列）→ VALUE()またはTEXT()で変換

### 失敗2：SUMIFが0になる

- 条件の記述ミス。文字列条件は"（ダブルクォーテーション）で囲む
- 合計範囲がズレている → 範囲の確認を

### 失敗3：日付が数値として表示される

- セルの書式設定が「数値」になっている → 「日付」に変更
- TEXT関数で書式を指定する

---

> **Excelスキルを強みに仕事の幅を広げる**  ExcelやデータスキルはOA事務・営業・経営企画・会計など多くの職種で求められる基本スキルです。スキルアップを機に求人市場を確認してみましょう。<a href="https://px.a8.net/svt/ejp?a8mat=3ZD3R9+DPXS1E+GDO+C03K1" rel="nofollow">dodaで求人を探す</a><img border="0" width="1" height="1" src="https://www12.a8.net/0.gif?a8mat=3ZD3R9+DPXS1E+GDO+C03K1" alt="">

## まとめ

Excelの関数は500種類以上ありますが、実務で使うのは30〜50種類程度です。まずはこの記事の**優先度★★★★★の5関数**から完全マスターして、徐々に範囲を広げていきましょう。

---

## 関連記事

- [AI×Excelで自動化する方法](/posts/ai-excel-自動化/)
- [飲食業向けExcel原価計算2026](/posts/insyoku-excel-genkaritu-keisan-2026/)

---

## Excel業務効率化テンプレートをBOOTHで配布中

よく使う関数をあらかじめ組み込んだ**業務用Excelテンプレート**をBOOTHで販売・配布しています。集計・分析・管理に即使えるテンプレートで、Excel作業時間を大幅に削減できます。

[Productivity Works BOOTHストアはこちら](https://prod-works.booth.pm/)

*本記事にはアフィリエイトリンクが含まれています。読者の皆様に追加費用は発生しません。*
