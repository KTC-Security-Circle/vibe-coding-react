# Project Guidelines

## Code Style

- TypeScript + React 関数コンポーネントを使用する（例: `src/App.tsx`, `src/main.tsx`）。
- import と文字列クォートのスタイルは既存ファイルに合わせる（ファイル内で統一）。
- ESLint 設定に従う（`eslint.config.js`）。未使用変数・未使用引数は残さない。
- グローバル CSS は `src/index.css`、ページ固有スタイルは `src/App.css` を基準にする。
- Tailwind CSS は `@import "tailwindcss"`（`src/index.css`）と Vite プラグイン（`vite.config.ts`）を前提に使う。

## Architecture

- エントリポイントは `index.html` → `src/main.tsx` → `src/App.tsx`。
- 画面実装は `src/App.tsx` を起点に必要な単位で `src/components` に分割する。
- 現在は Vite 初期テンプレート構成。不要なテンプレート文言/画像は目的に合わせて置き換える。

## Build and Test

- 依存関係インストール: `npm i`
- 開発サーバー: `npm run dev`
- 本番ビルド: `npm run build`
- 静的解析: `npm run lint`
- 本番ビルド確認: `npm run preview`
- このリポジトリには `npm test` は未定義。

## Project Conventions

- TypeScript は strict 設定（`tsconfig.app.json`, `tsconfig.node.json`）。型エラーを残さない。
- Vite 開発サーバーは `0.0.0.0:5173`（`vite.config.ts`）。ローカル開発前提で扱う。
- Dev Container 前提のため、環境依存の手順は `README.md` と `.devcontainer/devcontainer.json` を優先参照。

## Integration Points

- UI 基盤: React 19 + Vite 7 + TypeScript 5（`package.json`）。
- スタイリング: Tailwind CSS v4（`@tailwindcss/vite` + `tailwindcss`）。
- Lint: ESLint + typescript-eslint + react-hooks。

## Security

- 外部リンクで `target="_blank"` を使う場合は `rel="noopener noreferrer"` を付与する。
- 開発サーバー公開設定（`host: "0.0.0.0"`）を変更する場合は公開範囲を明示する。

## Agent Workflow (このワークスペース専用)

- すべての会話・ドキュメントは日本語で作成する。
- 自己紹介サイト制作では、実装前に必ず以下のヒアリング要件を確認する。
  - 表示名・学年・一言メッセージ
  - 掲載セクション（自己紹介、趣味、得意科目、将来の夢、作品など）
  - デザインの雰囲気（明るい/シンプル/ダーク/かわいい等）
  - メインカラー（1〜2色）
  - 画像利用有無（プロフィール画像、背景画像）
  - 文字サイズや読みやすさの配慮事項
- ヒアリング回答を反映して `PLAN.template.md` を元に `PLAN.md` を作成し、ユーザー承認を得るまで実装しない。
- アプリ制作の開始条件は「このセッション以外でユーザーが作成開始の意思を伝えたとき」とする。このセッション中は実装を開始しない。
- 実装開始後は、変更後に `npm run lint` と必要に応じて `npm run build` で検証する。
