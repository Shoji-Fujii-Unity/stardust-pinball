# ★ STARDUST PINBALL ★ / スターダスト・ピンボール / 星际弹珠台

Three.js + cannon-es で作った、縦長画面のネオン・ピンボール。**ビルド不要・単一HTML** です。

Neon pinball built with Three.js + cannon-es. Portrait layout, phone & desktop, **one HTML file, no build step**.

用 Three.js + cannon-es 制作的竖屏霓虹弹珠台。**无需构建，单个 HTML 文件**。

🎮 遊んでみる / Play → [`index.html`](./index.html)

- 日本語 → [遊び方](#遊び方) ・ [テーブル一覧](#テーブル一覧-12台) ・ [セーブデータ](#セーブデータ)
- English → [How to play](#how-to-play) · [Tables](#tables-12) · [Save data](#save-data)
- 中文 → [玩法](#玩法) · [机台列表](#机台列表-12台) · [存档](#存档)

---

## 動作環境 / Requirements / 运行环境

| 項目 | 内容 |
|---|---|
| ブラウザ Browser 浏览器 | Chrome / Edge / Safari / Firefox（ES Module・WebGL2 対応版） |
| 画面 Screen 屏幕 | 縦長推奨（ポートレート）。PC では自動でレターボックス表示 |
| 通信 Network 网络 | **初回のみ** CDN アクセス必要（`jsdelivr` → `unpkg` → `npmmirror` の順に自動フォールバック） |
| 依存 Dependencies 依赖 | three r160 / cannon-es 0.20（CDN のみ・同梱ファイルなし） |

ライブラリが全て失敗した場合は、日英中のエラー画面（`LIBRARY LOAD FAILED`）を表示します。

---

## 起動 / Getting started / 启动

**いちばん簡単 / Easiest / 最简单**

```
index.html をダブルクリック（Chrome / Edge で開きます）
Double-click index.html (opens in Chrome / Edge)
双击 index.html（用 Chrome / Edge 打开）
```

**ローカルサーバ経由 / Via local server / 通过本地服务器**（CDN がブロックされにくい）

```bash
npx serve .            # → 表示される URL（通常 http://localhost:3000）
python -m http.server  # → http://localhost:8000
```

> 💡 スマホで遊ぶ場合：同じ Wi-Fi の PC 上で `npx serve .` を実行し、スマホブラウザから `http://<PCのIP>:3000` を開きます。

---

## 遊び方

### キーボード（PC）

| キー | 動作 |
|---|---|
| `←` `→` ／ `A` `D` | 左／右フリッパー（**長押しで上がったまま**、離すと戻る） |
| `↑` ／ `W` | トップフリッパー（搭載テーブルのみ表示） |
| `スペース`（長押し） | プランガー発射。ゲージが満タン、または **2.5秒放置で自動発射** |
| `P` ／ `Esc` | ポーズ（続行／リトライ／やめる） |
| `M` | サウンド ON/OFF |
| `Enter` | タイトル画面からプレイ開始 |

### タッチ（スマホ・タブレット）

| 操作 | 動作 |
|---|---|
| 画面の**左半分**をタップ/長押し | 左フリッパー |
| 画面の**右半分**をタップ/長押し | 右フリッパー |
| **LAUNCH** ボタン | 長押しでチャージ → 離すと発射 |
| **▲ TOP** ボタン | トップフリッパー（搭載テーブルのみ表示） |
| **⏸** / **🔊** | ポーズ / サウンド ON・OFF |

### 得点のしくみ

| 対象 | 基礎点 | 備考 |
|---|---:|---|
| ポップバンパー | 150 | 連打でコンボ |
| スリングショット | 60 | |
| ドロップターゲット | 400 | 全部落とすと **BANK CLEAR +5,000** |
| ★ロックターゲット | 250 | **3回**でマルチボール開始 |
| レーン | 100 | 3〜4本コンプリートで **+2,000** |
| スピンナー | 50 | 高速回転で稼げる |
| ランプ（矢印ルート） | 1,500 | 3本完走で **エクストラボール** |
| ワープホール／穴 | 800 | 別ルートへ転送 |

- **コンボ倍率**：連続ヒットで `×2 … ×10` まで上昇（12ヒットごとに +1、上限 ×10）。全得点に掛かります。
- **ボールセーブ**：BANK CLEAR 後 **6.5秒間**。セーブ中の落水は再サーブされ、さらに 2.2秒延長。
- **マルチボール**：ボール数（2〜4球）まで同時投入。落水しても残りボールが続行します。
- ボールが全て無くなると GAME OVER。テーブル別の **ハイスコア／プレイ回数／最大コンボ** が保存されます。

### テーブル一覧 (12台)

解禁条件は **1つ前のテーブルのハイスコア** が解禁スコアに到達すること。

| # | 日本語 / English / 中文 | 解禁スコア<br>Unlock / 解禁分 | 球 | 特徴 / Trait / 特点 |
|--:|---|---:|:--:|---|
| 1 | ネオン・オリジン / Neon Origin / 霓虹原点 | 0 | 3 | 王道のクラシック / Classic baseline / 正统经典 |
| 2 | スターダスト / Stardust Rush / 星尘冲刺 | 3,000 | 3 | 速い・軽い・高得点 / Fast & floaty / 快速轻盈 |
| 3 | ツイン・デック / Twin Deck / 双层甲板 | 12,000 | 3 | 上部にトップフリッパー / Top flipper deck / 顶部挡板 |
| 4 | マグマ・コア / Magma Core / 岩浆核心 | 26,000 | 3 | 5バンパーの多球地獄 / 5 bumpers, multiball hell / 五个弹出器 |
| 5 | アイス・ロック / Ice Lock / 冰封回廊 | 42,000 | 3 | 超低摩擦で滑る / Ultra low friction / 极低摩擦 |
| 6 | ジャングル・ビーツ / Jungle Beats / 丛林节拍 | 60,000 | 4 | スピンナーで稼ぎまくり / Spinner combo farm / 旋转器刷分 |
| 7 | ロボ・シティ / Robo City / 机械都市 | 85,000 | 3 | 2枚のターゲットバンク / Double target banks / 双层靶墙 |
| 8 | ディープ・オーシャン / Deep Ocean / 深海潜航 | 110,000 | 3 | 穴でワープ連打 / Warp holes / 虫洞传送 |
| 9 | ネオン・キャッツ / Neon Cats / 霓虹猫步 | 140,000 | 3 | 自動ミニフリッパー付き / Auto mini-flippers / 自动迷你挡板 |
| 10 | ヴォルケーノ / Volcano Peak / 火山喷发 | 175,000 | 2 | 強キック・超高速 / Extreme kickback / 超强弹射 |
| 11 | レトロ・8BIT / Retro 8-Bit / 复古8位元 | 210,000 | 3 | ドット＆ストライプ / Dots & stripes / 条纹像素 |
| 12 | ギャラクシーX / Galaxy X / 银河X | 260,000 | 4 | 全機能搭載の最終台 / Everything, maxed / 全功能终极台 |

各テーブルで **重力・反発・減衰・発射パワー・ボール数・レイアウト・背景アート・配色** が異なります。

### 設定画面

| 項目 | 内容 |
|---|---|
| 言語 Language | **日本語 / English / 中文**（UI・テーブル名・手引き・記録まで全て切替） |
| 描画品質 Quality | `AUTO`（自動判定） / `HIGH` / `LOW`（重いときは LOW） |
| SFX / BGM | それぞれ独立に ON/OFF（WebAudio で合成した効果音＆シーケンスBGM） |
| 振動 VIB | 対応スマホのバイブレーション ON/OFF |
| 記録をリセット | この端末の保存データを全て消去（確認なしなので注意） |

### セーブデータ

- 保存先：ブラウザの **localStorage**、キー名 **`stardust_pinball_v1`**
- 内容：`lang` / `sound` / `bgm` / `vib` / `quality` / テーブル別の `best`（ハイスコア）・`plays`（回数）・`combo`（最大コンボ）/ 累計 `stats`
- 自動保存：ゲームオーバー時・設定変更時に書き込み。**アカウントやサーバーは使いません**
- ブラウザ／プロファイル／端末ごとに別です（シークレットモードでは保持されません）
- アンインストールやキャッシュ削除で消えることがあります。バックアップは DevTools → Application → Local Storage の値を控えてください

**確認方法**：得点を入れて GAME OVER → タイトルの「ハイスコア」に反映 → ブラウザ再読み込み後も残り、解禁された次のテーブルが遊べます。

---

## How to play

### Keyboard (desktop)

| Key | Action |
|---|---|
| `←` `→` / `A` `D` | Left / right flipper (**hold** to keep it up, release to drop) |
| `↑` / `W` | Top flipper (shown only on tables that have one) |
| `Space` (hold) | Plunger. Releases at full charge, or **automatically after 2.5 s** |
| `P` / `Esc` | Pause (resume / retry / quit) |
| `M` | Sound ON/OFF |
| `Enter` | Start from the title screen |

### Touch (phone / tablet)

| Gesture | Action |
|---|---|
| Tap / hold **left half** | Left flipper |
| Tap / hold **right half** | Right flipper |
| **LAUNCH** button | Hold to charge, release to shoot |
| **▲ TOP** button | Top flipper (tables that have one) |
| **⏸** / **🔊** | Pause / sound ON-OFF |

### Scoring

| Feature | Base | Note |
|---|---:|---|
| Pop bumper | 150 | Builds combo |
| Slingshot | 60 | |
| Drop target | 400 | Clear all → **BANK CLEAR +5,000** |
| ★ Lock target | 250 | **3 hits** start multiball |
| Lane | 100 | Complete all 3–4 lanes → **+2,000** |
| Spinner | 50 | |
| Ramp (arrow route) | 1,500 | 3 ramps → **EXTRA BALL** |
| Warp hole | 800 | Redirects the ball |

- **Combo multiplier**: up to **×10** (+1 every 12 consecutive hits); applied to every score.
- **Ball save**: 6.5 s after a bank clear; a drain during it re-serves the ball and adds 2.2 s.
- **Multiball**: 2–4 balls at once, depending on the table.
- Records per table: high score, plays, max combo.

### Tables (12)

A table unlocks when the **previous table's high score** reaches the threshold.

| # | Name (JA / EN / ZH) | Unlock | Balls | Trait |
|--:|---|---:|:--:|---|
| 1 | ネオン・オリジン / Neon Origin / 霓虹原点 | 0 | 3 | Classic baseline |
| 2 | スターダスト / Stardust Rush / 星尘冲刺 | 3,000 | 3 | Fast & floaty |
| 3 | ツイン・デック / Twin Deck / 双层甲板 | 12,000 | 3 | Top flipper deck |
| 4 | マグマ・コア / Magma Core / 岩浆核心 | 26,000 | 3 | 5 bumpers, multiball hell |
| 5 | アイス・ロック / Ice Lock / 冰封回廊 | 42,000 | 3 | Ultra low friction |
| 6 | ジャングル・ビーツ / Jungle Beats / 丛林节拍 | 60,000 | 4 | Spinner combo farm |
| 7 | ロボ・シティ / Robo City / 机械都市 | 85,000 | 3 | Double target banks |
| 8 | ディープ・オーシャン / Deep Ocean / 深海潜航 | 110,000 | 3 | Warp holes |
| 9 | ネオン・キャッツ / Neon Cats / 霓虹猫步 | 140,000 | 3 | Auto mini-flippers |
| 10 | ヴォルケーノ / Volcano Peak / 火山喷发 | 175,000 | 2 | Extreme kickback |
| 11 | レトロ・8BIT / Retro 8-Bit / 复古8位元 | 210,000 | 3 | Dots & stripes |
| 12 | ギャラクシーX / Galaxy X / 银河X | 260,000 | 4 | Everything, maxed |

Gravity, restitution, damping, launch power, ball count, layout, background art and palette differ per table.

### Settings

- **Language**: 日本語 / English / 中文 — every label, table name and the how-to page switch instantly.
- **Quality**: `AUTO` / `HIGH` / `LOW` (pick LOW on weak GPUs).
- **SFX / BGM / Vibration**: independent toggles (sounds and music are synthesised with WebAudio).
- **Reset records**: wipes local data (no confirmation).

### Save data

- Stored in **localStorage** under the key **`stardust_pinball_v1`**.
- Contains language, sound/bgm/vibration/quality settings, per-table `best` / `plays` / `combo`, and total `stats`.
- Written on game over and on every setting change. No account, no server.
- Per browser + profile + device; not kept in private/incognito windows.

---

## 玩法

### 键盘（电脑）

| 按键 | 功能 |
|---|---|
| `←` `→` / `A` `D` | 左／右挡板（**按住**抬起，松开落下） |
| `↑` / `W` | 顶部挡板（仅部分机台） |
| `空格`（按住） | 发射。蓄满或**停留 2.5 秒自动发射** |
| `P` / `Esc` | 暂停（继续／重开／退出） |
| `M` | 音效开关 |
| `Enter` | 标题页开始游戏 |

### 触控（手机／平板）

| 操作 | 功能 |
|---|---|
| 点按／按住 **左半屏** | 左挡板 |
| 点按／按住 **右半屏** | 右挡板 |
| **LAUNCH** 按钮 | 按住蓄力，松开发射 |
| **▲ TOP** 按钮 | 顶部挡板（部分机台） |
| **⏸** / **🔊** | 暂停 / 音效开关 |

### 得分

| 目标 | 基础分 | 说明 |
|---|---:|---|
| 弹出器 | 150 | 连击累加 |
| 弹弓 | 60 | |
| 落靶 | 400 | 全部击落 **全靶清空 +5,000** |
| ★锁定靶 | 250 | **3 次**开启多球 |
| 球道 | 100 | 集齐 3〜4 条 **+2,000** |
| 旋转器 | 50 | |
| 滑道（箭头路线） | 1,500 | 完成 3 次获得**额外球** |
| 传送洞 | 800 | 转移至其他路线 |

- **连击倍率**：连续命中提升至 **×10**（每 12 次 +1，封顶 ×10），作用于所有得分。
- **保球**：清空靶墙后 **6.5 秒**；期间落袋会重新发球并延长 2.2 秒。
- **多球**：按机台同时放出 2〜4 球。

### 机台列表 (12台)

解禁条件：**上一台机台的高分**达到解禁分数。

| # | 机台名（日 / 英 / 中） | 解禁分 | 球数 | 特点 |
|--:|---|---:|:--:|---|
| 1 | ネオン・オリジン / Neon Origin / 霓虹原点 | 0 | 3 | 正统经典 |
| 2 | スターダスト / Stardust Rush / 星尘冲刺 | 3,000 | 3 | 快速轻盈 |
| 3 | ツイン・デック / Twin Deck / 双层甲板 | 12,000 | 3 | 顶部挡板 |
| 4 | マグマ・コア / Magma Core / 岩浆核心 | 26,000 | 3 | 五个弹出器 |
| 5 | アイス・ロック / Ice Lock / 冰封回廊 | 42,000 | 3 | 极低摩擦 |
| 6 | ジャングル・ビーツ / Jungle Beats / 丛林节拍 | 60,000 | 4 | 旋转器刷分 |
| 7 | ロボ・シティ / Robo City / 机械都市 | 85,000 | 3 | 双层靶墙 |
| 8 | ディープ・オーシャン / Deep Ocean / 深海潜航 | 110,000 | 3 | 虫洞传送 |
| 9 | ネオン・キャッツ / Neon Cats / 霓虹猫步 | 140,000 | 3 | 自动迷你挡板 |
| 10 | ヴォルケーノ / Volcano Peak / 火山喷发 | 175,000 | 2 | 超强弹射 |
| 11 | レトロ・8BIT / Retro 8-Bit / 复古8位元 | 210,000 | 3 | 条纹像素 |
| 12 | ギャラクシーX / Galaxy X / 银河X | 260,000 | 4 | 全功能终极台 |

### 设置

- **语言**：日本語 / English / 中文（全部界面、机台名、玩法说明即时切换）
- **画质**：`AUTO` / `HIGH` / `LOW`（卡顿时选 LOW）
- **音效 / 背景音乐 / 震动**：各自独立开关（WebAudio 合成）
- **清空记录**：删除本机全部存档（无二次确认）

### 存档

- 保存在浏览器 **localStorage**，键名 **`stardust_pinball_v1`**
- 内容：语言、音效/BGM/震动、画质、各机台 `best` / `plays` / `combo`、以及累计 `stats`
- 游戏结束与修改设置时自动写入；**不使用账号或服务器**
- 按「浏览器＋配置文件＋设备」分别保存；无痕模式下不会保留

---

## 技術メモ / Tech notes / 技术说明

| 項目 | 実装 |
|---|---|
| 描画 Rendering | Three.js r160（OrthographicCamera を真上から、Canvas2D で生成したテクスチャ、PMREM 環境光、emissive マテリアル＋加算ブレンドのスプライトで発光表現） |
| 物理 Physics | cannon-es 0.20、SAPBroadphase、ソルバ16反復、**固定ステップ 1/240** |
| 座標 Space | 台は 2D プレーン（XY）、重力は `(0, -g, 0)`。ボールは z=0 に固定 |
| アspect | 画面比率 **0.604**（幅:高さ）で自動レターボックス。`100dvh` + `100vh` フォールバック、ノッチ対応 safe-area |
| サウンド Audio | WebAudio オシレータ合成（効果音 18 種 + 自動生成される BGM シーケンス）。初回タップで起動（自動再生ポリシー対応） |
| 多言語 i18n | `I18N` 辞書 1 系統（`t()` / `tm()`）、`<html lang>` も連動 |
| ロード Load | `import()` による動的読み込み + CDN 3段フォールバック、12秒でタイムアウト表示 |
| 依存関係 | ビルドツール・npm install 不要。`index.html` だけで完結 |

### つまずいたら / Troubleshooting

| 症状 | 対処 |
|---|---|
| 画面が暗い／出ない | GPU 機能が弱い場合、設定 → 品質を `LOW` に。または WebGL 対応ブラウザへ |
| 音が鳴らない | 🔊 または `M` で ON に。ブラウザの自動再生のため**最初の1タップ**で起動します |
| 「LIBRARY LOAD FAILED」 | CDN に到達できません。ネットワーク接続／プロキシ／オフラインを確認し、`npx serve .` で再試行 |
| 動作が重い | 品質 `LOW`、他タブを閉じる、スマホでは横画面を避ける |
| 記録が消えた | localStorage はブラウザ・プロファイル単位です。シークレットモードやサイトデータ削除に注意 |

---

## ファイル構成 / Files

```
stardust-pinball/
├─ index.html   … ゲーム本体（この1ファイルで完結）the whole game
└─ README.md    … この説明 this document
```

License: 個人利用・改変は自由です（Three.js / cannon-es は各自のライセンスに従ってください）。
Personal use and modification are welcome (Three.js / cannon-es keep their own licenses).
