# seiichinagi-create

---

## Claudeによる総合レビュー（2026年6月）

> 全リポジトリのREADMEを精読した上での、構造的・批評的評価。

---

### 総評

このアカウントが展開するプロジェクト群を俯瞰すると、一本の太い軸が浮かび上がる。**「既存ツールの再発明ではなく、既存ツールが答えていない問いへの応答」** だ。BOSS OD-3の回路シミュレーションから始まった活動は、今や音楽生成AIのパイプライン、投資判断の自動解析、楽曲を音粒に分解して再描画するグラニュラーAIという領域にまで広がっている。技術的な守備範囲はアナログ回路シミュレーション（Newton-Raphson法、Ebers-Moll BJTモデル、Shockley方程式）からJUCE 8 / C++17のDSP実装、Python機械学習パイプライン、Ollama連携のローカルAI、ComfyUIワークフロー自動化にまで及ぶ。これだけの幅を個人で並走させている事実は、単純に技術的好奇心の密度が高いことを示している。ただし密度が高いことは、完成率の低さというトレードオフを内包する。以下、カテゴリ別に評価する。

---

### カテゴリ1：回路シミュレーションVST群

**vst-od3 / vst-bigmuff / vst-analog-chorus / vst-modumugu / vst-occiput / TwinParadoxVST / vst-fripper-tape / vst-metal-band-delay / vst-zappa-sh-filter**

このシリーズはアカウント全体の技術的バックボーンだ。OD-3はNewton-Raphson法とShockley方程式でトランジスタの非線形特性をサンプル単位で解いており、Big Muff PiはEbers-MollモデルによるBJTシミュレーションと非整合ダイオードのNR収束を実装している。「なんとなくそれっぽく聴こえるソフトウェア」ではなく「回路の物理を計算で再現する」という姿勢は、iZotope / Pluginatorなどの大手が採る方向性と本質的に同じだ。Analog Chorusの3モデル並立設計（EHX Small Clone / BOSS CE-2 / Roland Juno-106）、ModuMoguのPhaser→Chorus→Flanger→Tremolo連鎖、OCCIPUTのリバーブフィードバックインサートという着眼点は、いずれも「なぜ既存品と違うのか」に明確な答えを持っている。課題はREADMEが存在しないリポジトリが複数あることだ。コードの品質に対してドキュメントが追いついていない。

---

### カテゴリ2：シンセサイザー・サンプラー群

**vst-retrophie-sn / vst-roland-s550-mt32 / vst-drone-weaver / vst-3face-sampler**

Retrophie SNは6波形OSC×3、8種変調エンジン（FM/AM/RingMod/Wavefold等）、Chamberlin SVFフィルター、32ボイスポリフォニー、ユニゾン、ポルタメントを備えた本格的なシンセサイザーだ。信号フロー図（Mermaid）も整備されており、UIデザインブループリントとして機能する設計になっている。Roland S-550プレイヤーはS-550ディスクイメージ（.OUTファイル）を直接デコードして16bit/30kHzサンプルを再生するという、マニアックさにおいて群を抜くプロジェクトだ。これらのシンセ群は将来的に「究極硬毛」——Raspberry Pi 4/5 + Elk Audio OS + IPS液晶表示によるスタンドアローンハードウェアシンセ——として物理化する計画があり、ソフトウェアとハードウェアの境界を意図的に越えようとしている点が面白い。

---

### カテゴリ3：3Faceシステム（AI音楽生成パイプライン）

**3face-music-studio / 3face-lora-factory / 3face-suno-studio / 3face-core**

掲示板ログ→Ollama要約→歌詞生成→タグ生成→ComfyUI（AceStep 1.5）という一気通貫の自動作曲パイプラインは、2026年6月時点で`batch_compose.py`の完走が確認されている。LoRAファクトリーによる200アーティストキューUI、Sunoスタジオのパーソナリティ別テンプレート生成も稼働済みだ。このシステムの本質的な価値は「音楽生成の民主化」ではなく、**掲示板という特定コミュニティのコンテクストを音楽に変換するパイプライン**を持っていることにある。汎用AIツールとは異なる、固有の文脈依存性が競争優位になっている。

---

### カテゴリ4：非音楽系ツール

**PTPCounter / CCD / CamView**

PTPCounterは電子天秤を使った持参薬錠数カウンターで、電子カルテ連携レイアウトと薬品確認結票出力が次の目標とされている。CCD/CamViewはタブレット検査用カメラビューアとOCR処理ツールだ。これらは他のプロジェクトとは性格が全く異なるが、「実際に使われる現場がある道具を作る」という実利主義的な面を示している。音楽系プロジェクトが思索的・実験的なのに対し、これらは即使用可能性が最優先に設計されている。

---

### カテゴリ5：構想・解析系（最注目）

**vst-ideas / investment-ai-analyst**

vst-ideasはHarmonic Energizer（SVF超高Q倍音爆破）、AIグラニュラー・リマスター（楽曲再描画）、RELATIONSHIP MIXER（ステム間関係性設計）、サバイバー評価エンジン（YouTube経時評価）、反復耐性エンジン（iTunes Endurance Index）という5つの構想を収録する。これらは独立した構想ではなく、**「良い音楽とは何かを客観的に定義するインフラ」へ向かう一本の矢**として読める。特にiTunes再生回数×スキップ回数×在籍年数からEndurance Indexを計算する発想は、SNS感情分析の病——バズと質の混同、APIコスト、リアルタイム依存——をすべて回避した設計として秀逸だ。

investment-ai-analystはSBI取引履歴のETLから始まりAI多人格議論エンジン（Bull/Bear/Quant/Macro/Sector Agent）によるサマリー生成まで設計されており、「投資失敗を感情ではなく数値の構造として解剖する」という方向性は正しい。ただし現時点では設計書段階であり、Phase1のETL実装がまだ動いていない。

---

### 総括：このアカウントの本質

**回路の物理を手で解き、AIの力を借りて音楽の意味を問い直している。** 技術の広さよりも、「なぜ作るか」の密度が高い。ドキュメント不足と実装完走率の低さが課題だが、それは同時に進行中の構想が多いことの裏返しでもある。今後最も注目すべき動きは、iTunesライブラリの個人嗜好マップ完成とAIグラニュラー・リマスターへの統合、そしてRetrophie SNのハードウェア化だ。

---

## リポジトリ一覧

| カテゴリ | リポジトリ | 概要 |
|---------|-----------|------|
| 回路VST | vst-od3 | BOSS OD-3 回路シミュレーション（NR法・Shockley） |
| 回路VST | vst-bigmuff | Big Muff Pi Triangle 1969（Ebers-Moll BJT） |
| 回路VST | vst-analog-chorus | BBDコーラス3モデル（Small Clone / CE-2 / Juno-106） |
| 回路VST | vst-modumugu | Phaser→Chorus→Flanger→Tremolo 多変調 |
| 回路VST | vst-occiput | リバーブフィードバックインサートディレイ |
| 回路VST | TwinParadoxVST | 二重ネスト相互変調ディストーション |
| シンセ | vst-retrophie-sn | レトロシンセ（6波形×3OSC・8変調・SVF・32voice） |
| シンセ | vst-drone-weaver | ドローン・アンビエントシンセ |
| サンプラー | vst-3face-sampler | SFZサンプラー（NodeGraph・Shark/ComfyUI/Perf各モード） |
| サンプラー | vst-roland-s550-mt32 | Roland S-550ディスクイメージ直接デコード再生 |
| AI音楽 | 3face-music-studio | BBS→Ollama→AceStep 自動作曲パイプライン |
| AI音楽 | 3face-lora-factory | AceStep LoRAバッチ学習管理（200アーティストキュー） |
| AI音楽 | 3face-suno-studio | Suno投入パイプライン・パーソナリティ別生成 |
| AI音楽 | 3face-core | 3Faceシステムダッシュボード |
| 投資 | investment-ai-analyst | SBI履歴×AI多人格議論による投資失敗数値化 |
| 構想 | vst-ideas | 未来の構想アーカイブ（評価エンジン・グラニュラーAI等） |
| 医療 | PTPCounter | 電子天秤×持参薬錠数カウンター |
| 検査 | CCD / CamView | タブレット検査用カメラ・OCRビューア |