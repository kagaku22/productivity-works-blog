---
title: "FX利益20万円超えたら確定申告が必要？サラリーマン向けに税額を実計算"
date: 2026-05-12
draft: false
slug: "fx-rieki-20man-kakuteishinkoku"
description: "FXで利益が20万円を超えた会社員は確定申告が必要です。申告分離課税20.315%の計算方法と、実際の税額シミュレーションを解説。"
categories: ["投資・資産運用"]
tags: ["FX", "確定申告", "税金", "サラリーマン", "20万円"]
author: "Productivity Works編集部"
ShowToc: true
TocOpen: false
ShowReadingTime: true
ShowBreadCrumbs: true
ShowWordCount: true

cover:
  image: "images/covers/fx-rieki-20man-kakuteishinkoku.png"
  alt: "FX利益20万円超えたら確定申告が必要？サラリーマン向けに税額を実計算"
  relative: false
---

※本記事にはアフィリエイト広告が含まれています。


FXを始めてしばらくたち、ようやく利益が出るようになってきた。でも、ふと気になるのが「これ、確定申告しなきゃいけないの？」という疑問ではないでしょうか。

会社員であれば、毎年勤務先が年末調整をしてくれるため、自分で税務署に行く機会はほとんどありません。だからこそ、FXで利益が出たとき「20万円以下なら申告不要と聞いたけど、本当？」「申告が必要な場合、どうやって計算すればいい？」と頭を抱える人は少なくありません。

この記事では、**FXの利益に適用される税率**、**20万円ルールの正確な意味**、そして**実際の税額シミュレーション**を順を追って解説します。確定申告が初めての方でも理解できるよう、具体的な数字を使って丁寧に説明します。

<div style="max-width:620px;margin:1.8em auto;text-align:center;">
<svg viewBox="0 0 620 340" xmlns="http://www.w3.org/2000/svg" style="width:100%;height:auto;" aria-label="FX利益が出たら確定申告が必要？判定フロー">
  <style>text { font-family: 'Noto Sans JP', 'Hiragino Kaku Gothic ProN', 'Yu Gothic', sans-serif; }</style>
  <!-- 背景 -->
  <rect width="620" height="340" rx="12" fill="#f8fafc" stroke="#e2e8f0" stroke-width="1.5"/>
 <text x="310" y="28" text-anchor="middle" fill="#1e293b" font-size="13" font-weight="bold">FX利益が出たら確定申告が必要？</text>

  <!-- スタートノード -->
  <rect x="210" y="44" width="200" height="44" rx="22" fill="#4a9eff"/>
 <text x="310" y="70" text-anchor="middle" fill="white" font-size="13" font-weight="bold">FX利益が発生した</text>

  <!-- 矢印↓ -->
  <line x1="310" y1="88" x2="310" y2="108" stroke="#94a3b8" stroke-width="2" marker-end="url(#arr)"/>

  <!-- 菱形：会社員？ -->
  <polygon points="310,112 420,148 310,184 200,148" fill="white" stroke="#4a9eff" stroke-width="2"/>
 <text x="310" y="144" text-anchor="middle" fill="#1e293b" font-size="12">年末調整済みの</text>
 <text x="310" y="162" text-anchor="middle" fill="#1e293b" font-size="12">会社員？</text>

  <!-- YES → 右 -->
  <line x1="420" y1="148" x2="500" y2="148" stroke="#94a3b8" stroke-width="2" marker-end="url(#arr)"/>
 <text x="458" y="140" text-anchor="middle" fill="#10b981" font-size="11" font-weight="bold">YES</text>

  <!-- 菱形：20万超？ -->
  <polygon points="540,148 590,186 540,224 490,186" fill="white" stroke="#4a9eff" stroke-width="2"/>
 <text x="540" y="182" text-anchor="middle" fill="#1e293b" font-size="11">20万円</text>
 <text x="540" y="198" text-anchor="middle" fill="#1e293b" font-size="11">超え？</text>

  <!-- YES → 下（申告必要） -->
  <line x1="540" y1="224" x2="540" y2="264" stroke="#94a3b8" stroke-width="2" marker-end="url(#arr)"/>
 <text x="555" y="248" fill="#f59e0b" font-size="11" font-weight="bold">YES</text>
  <rect x="470" y="268" width="140" height="44" rx="8" fill="#f59e0b"/>
 <text x="540" y="287" text-anchor="middle" fill="white" font-size="12" font-weight="bold">確定申告が必要</text>
 <text x="540" y="304" text-anchor="middle" fill="white" font-size="10">（所得税20.315%）</text>

  <!-- NO → 右側（住民税のみ） -->
  <line x1="590" y1="186" x2="610" y2="186" stroke="#94a3b8" stroke-width="2"/>
  <line x1="610" y1="186" x2="610" y2="310" stroke="#94a3b8" stroke-width="2"/>

  <!-- 会社員でない → 下 -->
  <line x1="310" y1="184" x2="310" y2="224" stroke="#94a3b8" stroke-width="2" marker-end="url(#arr)"/>
 <text x="325" y="210" fill="#f59e0b" font-size="11" font-weight="bold">NO</text>
  <rect x="190" y="228" width="240" height="44" rx="8" fill="#f59e0b"/>
 <text x="310" y="247" text-anchor="middle" fill="white" font-size="12" font-weight="bold">確定申告が必要</text>
 <text x="310" y="264" text-anchor="middle" fill="white" font-size="10">（20万円ルール適用外）</text>

  <!-- NO（20万以下） 結果 -->
  <line x1="490" y1="186" x2="430" y2="186" stroke="#94a3b8" stroke-width="2"/>
  <line x1="430" y1="186" x2="430" y2="290" stroke="#94a3b8" stroke-width="2" marker-end="url(#arr)"/>
 <text x="440" y="220" fill="#10b981" font-size="11" font-weight="bold">NO</text>
  <rect x="330" y="292" width="200" height="36" rx="8" fill="#10b981"/>
 <text x="430" y="307" text-anchor="middle" fill="white" font-size="11" font-weight="bold">所得税申告は不要</text>
 <text x="430" y="322" text-anchor="middle" fill="white" font-size="10">※住民税申告は別途必要</text>

  <!-- 矢印マーカー定義 -->
  <defs>
    <marker id="arr" markerWidth="8" markerHeight="8" refX="6" refY="3" orient="auto">
      <path d="M0,0 L0,6 L8,3 z" fill="#94a3b8"/>
    </marker>
  </defs>
</svg>
<p style="font-size:12px;color:#64748b;margin-top:4px;">※年収2,000万円超の会社員は20万円ルール適用外。住民税申告は利益額に関わらず必要。</p>
</div>

---

## FXの利益にかかる税金の基本

FXで得た利益は、給与所得とは別に**申告分離課税**の対象となります。税率は利益の額にかかわらず一律で、以下の3つを合算した **20.315%** が適用されます。

| 税目 | 税率 |
|------|------|
| 所得税 | 15% |
| 復興特別所得税（所得税の2.1%） | 0.315% |
| 住民税 | 5% |
| **合計** | **20.315%** |

「申告分離課税」とは、給与など他の所得と合算せず、FXの利益だけを切り離して課税する仕組みです。給与が高くても低くても、FX利益への税率は変わりません。この点は、給与・賞与に対する所得税（5〜45%の累進課税）とは大きく異なります。

---

## 20万円ルールとは？

「FXは20万円以下なら確定申告しなくていい」という話を聞いたことがある方は多いでしょう。これは所得税法上の規定に基づいたものですが、**正確に理解しておく必要があります**。

### 20万円ルールが適用される条件

所得税法では、以下の条件をすべて満たす場合に限り、確定申告が不要とされています。

- **給与所得者（会社員）である**
- **年末調整が済んでいる**
- **給与所得・退職所得以外の所得の合計が年間20万円以下**

FXの利益はこの「給与所得・退職所得以外の所得」に該当するため、**FX利益が20万円以下であれば所得税の確定申告は不要**です。

### ただし、住民税の申告は別問題

重要な点として、20万円ルールはあくまで**所得税（国税）の確定申告が不要になる規定**です。住民税（地方税）については別途、**お住まいの市区町村への申告が必要**です。

FX利益が20万円以下でも住民税申告をしていない場合、後から市区町村より申告を求められる可能性があります。確定申告書を提出した場合は自動的に住民税にも反映されますが、確定申告を省略した場合は自分で住民税申告の手続きを行う必要があります。

---

## 確定申告が必要なケース・不要なケース

会社員のFX利益に関する申告要否を整理すると、以下のようになります。

| ケース | 所得税の確定申告 | 住民税の申告 |
|--------|----------------|-------------|
| FX利益が20万円以下（年末調整済み） | **不要** | 必要 |
| FX利益が20万円超（年末調整済み） | **必要** | 確定申告で自動反映 |
| 年収2,000万円超の給与所得者 | **必要**（20万円ルール適用外） | 確定申告で自動反映 |
| 2箇所以上から給与を受けている | **必要**（条件による） | 確定申告で自動反映 |
| FXで損失が出た（損失の繰越をしたい場合） | 申告することを推奨 | 確定申告で自動反映 |

まとめると、**年末調整済みの会社員でFX利益が20万円超の場合は必ず確定申告が必要**です。申告を忘れると、後から延滞税や無申告加算税が課される可能性があります。

---

## FX利益の税額を実際に計算してみよう

税率が20.315%と分かれば、計算自体はシンプルです。

**計算式: FX利益 × 20.315% = 税額（概算）**

ただし、所得税と住民税では申告・納付のタイミングが異なります。以下では、代表的な3つのケースで概算税額を確認してみましょう。

### パターン1: FX利益が25万円の場合

```text
所得税: 250,000円 × 15% = 37,500円
復興特別所得税: 37,500円 × 2.1% = 787円（端数切捨）
住民税: 250,000円 × 5% = 12,500円
合計税額: 約50,787円
```

**概算税額: 約50,787円**（税率20.315%で計算すると250,000 × 0.20315 = 50,787円）

### パターン2: FX利益が50万円の場合

```text
50万円 × 20.315% = 101,575円
```

**概算税額: 約101,575円**

### パターン3: FX利益が100万円の場合

```text
100万円 × 20.315% = 203,150円
```

**概算税額: 約203,150円**

利益が増えるほど、当然ながら税額も増えます。FXで稼いだ金額の約5分の1が税金として持っていかれるイメージです。利益確定のタイミングで「そのうち税金で払う分」を取り分けておく習慣をつけておくと、申告時に慌てずに済みます。

なお、より正確な税額（復興特別所得税の端数処理なども含む）は、[FX利益計算ツール](/ja/tools/fx-profit-calculator/)で即座に計算できます。

---

## 確定申告の手順

確定申告は難しそうに聞こえますが、手順を理解すれば会社員でも対応可能です。FXの申告は以下の流れで進めます。

### ステップ1: 年間取引報告書を取得する

FX口座を開設している証券会社・FX業者のマイページから「年間取引報告書」をダウンロードします。通常、翌年1月下旬〜2月上旬に発行されます。この書類には年間の損益合計が記載されています。

### ステップ2: 申告書を作成する

確定申告書の作成方法は主に2つです。

**e-Tax（国税庁の電子申告システム）を使う方法**
国税庁の確定申告書等作成コーナー（https://www.nta.go.jp/）から、画面の案内に従って入力します。マイナンバーカードがあればそのままオンラインで申告まで完了できます。

**会計ソフトを使う方法**
確定申告書類の作成は[freee会計](https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP)を使えばガイドに沿って入力するだけです。FXの雑所得の入力項目も用意されており、年間取引報告書の数字を転記するだけで申告書が完成します。税務の知識がなくても手順通りに進めることができるため、初めての確定申告にも適しています。

### ステップ3: 申告分離課税を選択して申告する

FXの利益を入力する際は、「先物取引に係る雑所得等」として**申告分離課税**を選択します。給与所得と混同して「総合課税」で申告しないよう注意してください。

### 申告・納付の期限

- 確定申告期間: 毎年2月16日〜3月15日（土日祝日の場合は翌営業日）
- 所得税の納付期限: 3月15日まで（口座振替は4月下旬）
- 住民税: 確定申告の内容をもとに市区町村が計算し、6月以降に通知が来ます

---

## FXの損失が出た場合も確定申告すべき理由

FXで損失が出た年は「申告しなくていいや」と思うかもしれませんが、**損失を確定申告しておくことで大きなメリット**があります。

<div style="max-width:600px;margin:1.6em auto;text-align:center;">
<svg viewBox="0 0 600 180" xmlns="http://www.w3.org/2000/svg" style="width:100%;height:auto;" aria-label="FX税額シミュレーション">
  <style>text { font-family: 'Noto Sans JP', 'Hiragino Kaku Gothic ProN', 'Yu Gothic', sans-serif; }</style>
  <rect width="600" height="180" rx="10" fill="#f8fafc" stroke="#e2e8f0" stroke-width="1.5"/>
 <text x="300" y="24" text-anchor="middle" fill="#1e293b" font-size="13" font-weight="bold">FX利益別 税額シミュレーション（税率20.315%）</text>

  <!-- バーチャート -->
  <!-- 25万円 -->
  <rect x="60" y="130" width="80" height="30" rx="4" fill="#e2e8f0"/>
  <rect x="60" y="100" width="80" height="30" rx="4" fill="#4a9eff"/>
 <text x="100" y="96" text-anchor="middle" fill="#4a9eff" font-size="11" font-weight="bold">約5万円</text>
 <text x="100" y="150" text-anchor="middle" fill="#64748b" font-size="11">利益25万円</text>

  <!-- 50万円 -->
  <rect x="200" y="130" width="80" height="30" rx="4" fill="#e2e8f0"/>
  <rect x="200" y="70" width="80" height="60" rx="4" fill="#4a9eff"/>
 <text x="240" y="66" text-anchor="middle" fill="#4a9eff" font-size="11" font-weight="bold">約10万円</text>
 <text x="240" y="150" text-anchor="middle" fill="#64748b" font-size="11">利益50万円</text>

  <!-- 100万円 -->
  <rect x="340" y="130" width="80" height="30" rx="4" fill="#e2e8f0"/>
  <rect x="340" y="40" width="80" height="90" rx="4" fill="#f59e0b"/>
 <text x="380" y="36" text-anchor="middle" fill="#f59e0b" font-size="11" font-weight="bold">約20万円</text>
 <text x="380" y="150" text-anchor="middle" fill="#64748b" font-size="11">利益100万円</text>

  <!-- 凡例 -->
  <rect x="460" y="60" width="14" height="14" rx="2" fill="#4a9eff"/>
 <text x="480" y="72" fill="#64748b" font-size="11">税額</text>
  <rect x="460" y="84" width="14" height="14" rx="2" fill="#e2e8f0"/>
 <text x="480" y="96" fill="#64748b" font-size="11">手取り益（概算）</text>

 <text x="300" y="170" text-anchor="middle" fill="#94a3b8" font-size="10">※税率20.315%で概算。実際の税額は端数処理等で若干異なる場合があります。</text>
</svg>
</div>

### 損失の繰越控除（3年間）

FXの損失は、確定申告することで**翌年以降3年間にわたって利益と相殺（繰越控除）**できます。

例えば、2025年に30万円の損失が出て確定申告した場合、2026年に50万円の利益が出たとき、繰越損失30万円を差し引いた**20万円分にのみ課税**されます。

```text
2026年FX利益: 50万円
2025年繰越損失: △30万円
課税対象: 20万円
税額: 20万円 × 20.315% = 40,630円
（繰越控除なしの場合: 50万円 × 20.315% = 101,575円）
```

この例では、損失の繰越申告をしていたことで**約61,000円の節税**になります。損失が出た年に確定申告を怠ると、この繰越控除の権利は失われてしまいます。

損失が出た年でも、必ず確定申告して損失を記録しておくことを強くおすすめします。

---

> FX取引と並行して、NISAでの長期投資も検討してみませんか？**[楽天証券]()**ならNISA口座も同時に開設でき、FXとNISAを一括管理できます。

## まとめ

FXの利益と確定申告について、重要なポイントをまとめます。

- FXの利益には**申告分離課税20.315%**が一律で適用される
- **年末調整済みの会社員**は、FX利益が**20万円以下なら所得税の確定申告は不要**
- ただし**住民税の申告は20万円以下でも必要**
- FX利益が20万円を超えたら**確定申告が必須**（申告忘れはペナルティあり）
- 損失が出た年も申告しておけば、**3年間の繰越控除**で将来の節税につながる
- 確定申告書の作成は[freee会計](https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP)が便利

FXで利益が出始めた段階から、税金のことを把握しておくことが大切です。「知らなかった」では済まされないのが税務の世界。この記事を参考に、早めに準備を進めておきましょう。

---

### 関連記事

- [FX確定申告に必要な書類一覧と取得方法｜初心者向け完全手順](/ja/posts/fx-kakuteishinkoku-shorui-ichiran/)
- [FXの損失は3年繰り越せる？繰越控除の申告手順を図解で解説](/ja/posts/fx-sonshitsu-kurikoshi-koujo/)
- [FXのスワップポイントに税金はかかる？計算方法と確定申告の注意点](/ja/posts/fx-swap-point-zeikin/)
- [iDeCo節税シミュレーション｜年収別に実際いくら得するか計算](/ja/posts/ideco-tax-saving-simulation/)
- [NISA iDeCo どっちを先に始めるべき？優先順位を徹底解説【2026年最新版】](/ja/posts/nisa-ideco-docchi-saki/)

---

### 関連ツール

確定申告の準備に役立つツールを用意しています。

- [副業税金計算ツール](/ja/tools/fukugyou-tax-calculator/) — FX・副業の所得税・住民税を素早く試算
- [手取り計算シミュレーター](/ja/tools/salary-tedori-calculator/) — 給与から税金・社会保険料を差し引いた手取り額を確認

---

*本記事の内容は2026年5月時点の税制に基づいています。税法は改正される場合があります。個別の申告については税理士等の専門家にご相談ください。*
