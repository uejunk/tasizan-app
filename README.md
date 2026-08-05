# べんきょうランド (tasizan-app)

子供向け学習アプリのランチャー兼アプリ群。バニラJS + Tailwind CSS で構築。ビルド不要・GitHub Pages 直接公開。

## ディレクトリ構成

```
tasizan-app/
├── index.html                # ランチャー(アプリ一覧ホーム画面)
├── apps/
│   ├── tasizan/index.html    # １けたのたしざん (足し算アプリ)
│   └── eitango/index.html    # えいたんご (英単語アプリ)
├── shared/
│   └── common.js             # 共通: SoundEngine / SaveManager / StarCounter
├── data/
│   └── eitango-words.json    # 英単語データ (外部ファイル)
└── README.md
```

## アプリ一覧

| アプリ | パス | 機能 |
|--------|------|------|
| １けたのたしざん | `apps/tasizan/` | 1桁の足し算、繰り上がりヒント、冒険マップ(無限伸長) |
| えいたんご | `apps/eitango/` | 4択の英単語クイズ、10問1ラウンド |

## 共通機能 (`shared/common.js`)

- **SoundEngine**: 正解/不正解/キー/ステップ効果音 (Web Audio API)
- **SaveManager**: localStorage のアプリ別管理 (`study_app_<id>_save`)
- **StarCounter**: 星カウントの共通UI更新

## 新しいアプリの追加手順

1. `apps/<new-app>/index.html` を作成
2. `<script src="../../shared/common.js"></script>` を読み込む
3. 必要に応じて `data/<new-app>-data.json` に問題データを分離
4. ルート `index.html` の `apps` 配列にエントリを追加:
   ```javascript
   { id: 'new-app', title: '...', description: '...', emoji: '🎮', bg: 'from-...-to-...', url: 'apps/<new-app>/index.html' }
   ```

## 配信 (GitHub Pages)

1. リポジトリ Settings → Pages → Source: `main` / root
2. `https://<user>.github.io/tasizan-app/` で公開

## ローカル確認

```bash
python3 -m http.server 8000
# ブラウザで http://localhost:8000 を開く
```
