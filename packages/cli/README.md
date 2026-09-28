# @open-slide/cli

@open-slide/cli 是 open-slide 的「建立專案工具」。

它不是投影片編輯器，也不是可以直接安裝到 ChatGPT 的 Skill。它的工作是幫你準備好一個可以製作投影片的資料夾。

## 最簡單的用法

在終端機輸入：

~~~bash
npx @open-slide/cli init my-slide
~~~

這會建立 my-slide 資料夾，並放入：

- 一張可以參考的範例投影片。
- @open-slide/core，負責顯示、播放和建置。
- open-slide.config.ts，可選的設定檔。
- .claude/skills/ 和 .agents/skills/，給程式 AI 使用的 Skill。
- CLAUDE.md，告訴程式 AI 如何製作投影片。

建立完成後，進入資料夾並啟動：

~~~bash
cd my-slide
npm run dev
~~~

npx 執行時，CLI 會自動安裝相依套件。如果安裝沒有成功，再手動執行：

~~~bash
npm install
~~~

## 這個工具會做什麼？

可以把它想成「幫你整理好空房間的人」：

1. 建立專案資料夾。
2. 放入範例投影片。
3. 放入 React 和 open-slide 核心套件。
4. 放入 AI Skill。
5. 視需要初始化 Git。
6. 安裝專案需要的套件。

完成後，真正的投影片會放在：

~~~text
slides/<投影片名稱>/index.tsx
~~~

## 指令

| 指令 | 用途 |
| --- | --- |
| open-slide init [dir] | 在指定資料夾建立專案；沒有指定時使用目前資料夾。 |
| open-slide init --force | 允許在不是空的資料夾裡建立專案。 |
| open-slide init --name <name> | 指定產生的 package.json 專案名稱。 |
| open-slide init --use-npm | 使用 npm 安裝套件。 |
| open-slide init --use-pnpm | 使用 pnpm 安裝套件。 |
| open-slide init --use-yarn | 使用 Yarn 安裝套件。 |
| open-slide init --use-bun | 使用 Bun 安裝套件。 |
| open-slide init --no-install | 只建立檔案，不安裝套件。 |
| open-slide init --no-git | 不建立 Git 儲存庫。 |

如果資料夾裡已經有檔案，CLI 會先提醒你。除非你真的知道自己要做什麼，不要使用 --force，避免覆蓋或混合現有專案。

## 產生的專案裡有什麼？

你不會看到 Vite、React 或 TypeScript 的大量設定檔，因為這些東西已經藏在 @open-slide/core 裡。一般使用者不需要碰它們。

使用者只要記得：

- npm run dev：開始製作和預覽。
- npm run build：建立可以發布的版本。
- npm run preview：預覽正式版本。
- npm run sync:skills：更新專案裡的 AI Skill。

## 給 AI 的使用方式

在專案資料夾裡開啟 Claude Code、Codex 或 Cursor，然後說：

~~~text
請幫我做一份關於「我的主題」的簡報。
~~~

CLI 已經準備好 AI 需要的 Skill，AI 會讀取 create-slide 和 slide-authoring 的說明來製作投影片。
