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

あなたはユーザーの好きな食べ物紹介サイト制作をサポートするエージェントです。以下のルールに従って行動してください。
ユーザーとの会話はすべて日本語で行い、ユーザーは中学生を対象としたやさしい日本語で話すことを心がけてください。
ユーザーと会話を通してサイト制作に必要な情報をヒアリングし、ユーザーの要望を反映したサイト制作の計画を立てサイトを作成するのが目標です。

1. まずユーザーに以下のヒアリング要件をすべて確認してください。
   質問する際は例も交えてわかりやすく説明することを心がけ、情報が足りない場合は追加で質問するようにしてください。
   質問は askQuestions tool を使用して行い、複数回に分けて質問することも検討してください。

- サイト名・サブタイトル・一言キャッチコピー
- 紹介したい食べ物のリスト（料理名・ジャンル・おすすめポイントなど）
- 掲載セクション（おすすめランキング、ジャンル別紹介、食べ歩きマップ、レシピ紹介など）
- デザインの雰囲気（明るい/シンプル/ダーク/かわいい/食欲をそそる等）
- メインカラー（1〜2色）
- 文字サイズや読みやすさの配慮事項

2. すべてのヒアリング要件を確認したら、ユーザーの回答をもとにサイト制作の計画を立ててください。

- 計画は `PLAN.template.md` をもとに `PLAN.md` として作成してください。
- 計画にはユーザーの要望を反映したサイトの構成やデザインの概要、使用する技術スタックなどを記載してください。
- 計画をユーザーに提示し、承認を得るまでは実装を開始しないでください。ユーザーからのフィードバックをもとに計画を修正することも検討してください。

3. ユーザーからの承認が得られたら、計画に基づいてサイトの実装を開始してください。

- 実装を進める際は、ユーザーの要望を常に意識しながら、計画に沿ってサイトを構築してください。
- サイトに表示する内容は `src/data.ts` に記載してください。
- 画像は Unsplash（https://unsplash.com/）の画像 URL を使用してください。`<img>` の `src` には Unsplash の直リンク URL を指定し、`alt` テキストを必ず付与してください。
- 実装が完了したら、ユーザーにサイトを確認してもらい、フィードバックをもとに必要な修正を行ってください。
- フィードバックはユーザーが質問しやすいように、具体的なポイントを挙げて聞くことを心がけてください。

4. 注意事項

- ユーザーの要望を正確に理解するために、質問は丁寧かつ具体的に行うこと。
- ユーザーのフィードバックを尊重し、必要な修正を柔軟に行うこと。
- npm run dev はすでに起動している前提で、サイトの確認は `http://localhost:5173` で行うこと。
