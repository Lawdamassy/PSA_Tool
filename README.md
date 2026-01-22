# ParticleArchive (PSA.MK1) / ParticleArchiveSummoner (PSA_S.MK1)

Unity向け **パーティクル作業効率化ツールセット** のREADMEです。

---

## 📦 概要

### ParticleArchive (PSA.MK1)

**ParticleArchive** は、Unityシーン上に存在する複数の `ParticleSystem` を
**一括で Preset（.preset）形式として保存** するためのエディタ拡張ツールです。

手動で1つずつプリセットを作成する手間を省き、
**リスト管理 → 一括保存** という流れで効率的に作業できます。

---

### ParticleArchiveSummoner (PSA_S.MK1)

**ParticleArchiveSummoner** は、保存済みの `.preset` を「書庫」から読み込み、
**プレビューしながら即座にシーンへ召喚（生成）** するためのツールです。

マテリアル差し替え・スケール調整・親設定などを
**召喚時にまとめて適用** できます。

---

## ✨ 主な機能

### ParticleArchive (保存側)

* **ドラッグ & ドロップ一括登録**

  * ヒエラルキー上のGameObjectをまとめて登録可能
* **自動フィルタリング**

  * `ParticleSystem` を持たないオブジェクトは自動除外
* **個別リネーム保存**

  * 書き出し時のファイル名をツール上で指定可能
* **一括プリセット生成**

  * 指定フォルダへまとめて `.preset` を生成

---

### ParticleArchiveSummoner (召喚側)

* **書庫ブラウズ**

  * 指定フォルダ内の `.preset` を自動スキャン
* **リアルタイムプレビュー**

  * 選択中のプリセットをシーンビュー中央に即表示
* **召喚カスタマイズ**

  * オブジェクト名指定
  * 親オブジェクト自動設定
  * 原点 / シーンビュー位置への召喚
  * スケール・回転の調整
  * マテリアル上書き適用
* **Undo対応**

  * Ctrl + Z で召喚オブジェクトを削除可能

---

## 🛠 使用方法

### ParticleArchive (PSA.MK1)

#### 1. ウィンドウを開く

```
Unityメニュー > LawTool > Particleプリセット一括保存ツール
```

#### 2. オブジェクトを登録

1. ヒエラルキーでプリセット化したいオブジェクトを選択
2. ウィンドウ上部の **DRAG & DROP** エリアにドラッグ
3. リストに追加されたことを確認

#### 3. 名前の設定

* **Name**：プリセットのファイル名
* **✕ボタン**：個別削除
* **Clear All List**：全リセット

#### 4. プリセット作成

1. **[プリセットを作成]** をクリック
2. `Assets` 配下の保存先フォルダを選択
3. 完了ダイアログが表示されれば成功

---

### ParticleArchiveSummoner (PSA_S.MK1)

#### 1. ウィンドウを開く

```
Unityメニュー > LawTool > Particle召喚ツール
```

#### 2. 書庫を選択

* **[書庫を選択]** から `.preset` が保存されているフォルダを指定
* 新規追加後は **[更新]** をクリック

#### 3. プレビュー & 設定

* プリセットをクリック → 即プレビュー表示
* 以下の項目を調整可能：

  * 召喚名
  * 親オブジェクト
  * スケール / 回転
  * 適用マテリアル

#### 4. 召喚

* **[召喚 (Summon)]** をクリック
* 正式なGameObjectとしてシーンに生成
* プレビュー用オブジェクトは自動破棄

---

## ⚙ 技術仕様

### ParticleArchive

* `UnityEditor.Presets.Preset` を使用
* 対象：`ParticleSystem` 本体のみ
* ファイル名重複時：`AssetDatabase.GenerateUniqueAssetPath` により自動回避

### ParticleArchiveSummoner

* プレビュー用オブジェクト：

  * `HideFlags.HideAndDontSave`
* シーン保存・ビルド時に残らない安全設計

---

## ⚠ 制約事項

* 対象コンポーネント：

  * **ParticleSystem 本体のみ**
* 以下はプリセット対象外：

  * `ParticleSystemRenderer`
  * SubEmitter / 子階層設定
* 保存先は **Assetsフォルダ以下のみ**
* ParticleSystem自体にはマテリアル情報は含まれません

  * Summoner側で指定してください

---

## 🧠 開発者メモ

* Undo（リスト操作）は非対応（軽量化重視）
* 複雑なParticle（SubEmitter付き）はPrefab運用を想定
* パス区切り文字は `/` に統一（Windows / Mac両対応）

---

## 🖥 動作環境

* **Unity 2018.1 以上**（Preset機能依存）
* **推奨：Unity 2022.3 LTS**

---

## 📄 ライセンス

* 個人・商用利用可(法人利用はご連絡ください。)
* 再配布・コードの改変は禁止です。
* 再販売も禁止です。

---

## ✉ お問い合わせ

不具合報告・改善要望は GitHub Issues または作者までご連絡ください。
