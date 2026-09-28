<img width="1280" height="640" alt="open-slide github cover" src="https://github.com/user-attachments/assets/da535284-f7a9-4834-b281-f9ac6fe416e8" />

<br />
<br />
<a href="https://vercel.com/open-source-program">
  <img alt="Vercel OSS Program" src="https://vercel.com/oss/program-badge-2026.svg" />
</a>

# open-slide

[![GitHub stars](https://img.shields.io/github/stars/open-slide/open-slide?style=for-the-badge)](https://github.com/open-slide/open-slide/stargazers)
[![GitHub forks](https://img.shields.io/github/forks/open-slide/open-slide?style=for-the-badge)](https://github.com/open-slide/open-slide/network/members)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg?style=for-the-badge)](https://opensource.org/licenses/MIT)

**用文字和 AI 做出真正可以播放的簡報。**

open-slide 是一個簡報製作工具。你先用一句話告訴 AI 想做什麼，AI 會幫你寫出 React 投影片；open-slide 負責把投影片放到畫布上、切換頁面、即時更新和播放。

它不是一個 Skill，也不是下載一個檔案後就能直接打開的簡報軟體。

正確用法是：

1. 用指令建立一個 open-slide 專案。
2. 在這個專案裡使用 Claude Code、Codex、Cursor 等程式 AI。
3. 讓 AI 幫你建立和修改投影片。
4. 用瀏覽器預覽，用全螢幕模式播放，最後匯出或部署。

每一頁投影片都是一個 React 元件，畫布固定為 **1920 × 1080**。你可以自由控制文字、圖片、影片、動畫和版面，不必被傳統簡報模板綁住。

## 先記住一件事：它不是 Skill

看到 .agents/skills/ 或 .claude/skills/，不代表 open-slide 本身就是 Skill。

| 名稱 | 它是什麼 | 作用 |
| --- | --- | --- |
| open-slide | 簡報框架和命令列工具 | 建立專案、啟動網站、預覽和匯出簡報 |
| @open-slide/cli | 建立專案的工具 | 執行 npx @open-slide/cli init my-slide |
| @open-slide/core | 專案裡的核心套件 | 顯示投影片、切換頁面、播放和建置 |
| create-slide、apply-comments | 建立專案時附帶的 AI Skill | 讓程式 AI 更懂得如何做和修改投影片 |

open-slide 本身要先用 npx 建立專案；Skill 會跟著專案一起放進資料夾，不是把 open-slide 當成 Skill 上傳到 ChatGPT 裡。

## 五歲小孩也能照做的最短流程

### 第一步：準備 Node.js

先安裝 Node.js 20.19 以上版本，或 Node.js 22.12 以上版本：

[下載 Node.js](https://nodejs.org/)

安裝完成後，打開終端機：

- macOS：打開「終端機」。
- Windows：打開 PowerShell 或 Windows Terminal。

輸入下面這行，確認 Node.js 已經可以使用：

~~~bash
node -v
~~~

畫面出現版本號就可以，例如：

~~~
v22.12.0
~~~

### 第二步：建立一個簡報資料夾

輸入：

~~~bash
npx @open-slide/cli init my-slide
~~~

這句話的意思是：

- npx：取得並執行工具。
- @open-slide/cli：open-slide 的建立工具。
- init：建立新專案。
- my-slide：新資料夾的名字，可以改成你喜歡的名字。

這個指令會自動建立專案、放入範例投影片、安裝套件、建立 AI Skill，並視需要建立 Git 儲存庫。

如果畫面詢問套件管理工具，第一次使用可以直接選 npm。

### 第三步：走進資料夾

~~~bash
cd my-slide
~~~

cd 的意思是「走進這個資料夾」。

### 第四步：打開簡報網站

如果剛才已經安裝完成，輸入：

~~~bash
npm run dev
~~~

終端機會出現一個網址，通常像這樣：

~~~
http://localhost:5173
~~~

把這個網址貼到瀏覽器，就能看到簡報。

如果剛才安裝失敗，先輸入：

~~~bash
npm install
npm run dev
~~~

### 第五步：請 AI 幫你做投影片

在同一個 my-slide 資料夾裡，用 Claude Code、Codex 或 Cursor 開啟專案，直接說：

~~~text
請幫我做一份「AI 如何改變美容產業」的 8 頁簡報。
對象是完全不懂 AI 的美容師。
風格要乾淨、明亮、有高級感。
每頁只放一個重點，請直接建立投影片。
~~~

如果程式 AI 看得到這個專案裡的 Skill，它會使用 /create-slide 來建立簡報。

### 操作畫面：AI 正在建立投影片

下面這張是真實的操作畫面。左邊是 AI 對話區，AI 會先詢問簡報主題、頁數和視覺風格；中間是 open-slide 的簡報預覽；右邊是專案檔案。

![AI 使用 create-slide Skill 建立簡報](apps/demo/slides/open-slide-on-replit/assets/create-slide-skill.webp)

你要做的事情很簡單：回答 AI 的問題，等待它建立投影片，接著在中間的預覽區檢查結果。

### 操作畫面：建立專案的指令

這張圖顯示建立 open-slide 專案時使用的指令。實際操作時，請直接複製 README 上方的中文指令：

~~~bash
npx @open-slide/cli init my-slide
~~~

![建立 open-slide 專案的指令](apps/demo/slides/open-slide-on-replit/assets/init-command.webp)

這張圖裡的文字是英文，但真正需要記住的只有上面的那一行指令。

你不需要自己先寫 React，也不需要先學會 1920 × 1080 的程式寫法。先用自然語言說你想要的內容，之後再請 AI 修改。

## 你到底要安裝什麼？

一般使用者只需要執行：

~~~bash
npx @open-slide/cli init my-slide
~~~

你不需要先安裝 Vite、React、TypeScript、@open-slide/core 或 open-slide 的 Skill。建立工具會把這些東西放進專案裡。

如果使用 npx，建立完成後通常使用：

~~~bash
npm run dev
npm run build
npm run preview
~~~

如果平常使用 pnpm，也可以這樣建立：

~~~bash
pnpm dlx @open-slide/cli init my-slide
cd my-slide
pnpm dev
~~~

## 你可以用哪些 AI？

open-slide 不綁定某一個 AI。只要 AI 能讀取和修改專案檔案，就可以使用：

- Claude Code
- Codex
- Cursor
- Gemini CLI
- 其他可以操作程式碼的 AI 工具

ChatGPT 網頁版的一般對話，不會自動變成可以操作你電腦資料夾的程式代理人。你需要使用 Codex、Cursor、Claude Code，或其他能開啟本機專案的工具。

## 最常用的三個 AI Skill

### /create-slide

告訴 AI 你想做什麼簡報，AI 會詢問主題和風格、規劃頁數、建立投影片、完成版面，並視需要加上動畫、圖片、講者備註或轉場。

### /apply-comments

你可以在瀏覽器裡點選某個文字或圖形，留下意見，例如「請把這個標題改成紅色」。open-slide 會把意見記在程式碼裡。

接著對 AI 說：

~~~text
/apply-comments
~~~

AI 就會找到這些意見，修改投影片，再清掉已經完成的標記。

最簡單的循環是：

**打開簡報 → 點選問題 → 留下意見 → 執行 /apply-comments → 再看一次。**

### /slide-authoring

這是投影片的技術說明，告訴 AI 畫布大小、文字大小、顏色、留白、素材位置、轉場、動畫和講者備註的規則。

## 不想用 AI，也可以自己改嗎？

可以。投影片通常放在：

~~~text
slides/投影片名稱/index.tsx
~~~

你可以直接修改這個檔案。每一頁投影片就是一個 React 元件，最後輸出一個頁面陣列。

完全不會寫程式的話，建議先用 AI 建立第一版，再用自然語言要求 AI 修改。

## 投影片怎麼預覽和播放？

啟動開發伺服器：

~~~bash
npm run dev
~~~

在瀏覽器裡：

- 左右方向鍵：切換上一頁和下一頁。
- PageUp、PageDown：切換頁面。
- F：進入全螢幕播放。
- Esc：離開全螢幕。
- 全螢幕播放時按空白鍵或右方向鍵：下一頁。
- 全螢幕播放時按左方向鍵：上一頁。

每頁都會放在固定的 1920 × 1080 畫布裡，open-slide 會依照瀏覽器視窗大小自動縮放。

### 操作畫面：編輯投影片

啟動網站後，你會看到左邊的頁面縮圖、中間的投影片、右邊的設計和檢查工具。你可以先點選左邊的頁面，再查看或修改中間的內容。

![open-slide 投影片編輯畫面](apps/web/public/assets/screenshots/open-slide-cover.webp)

### 操作畫面：檢查文字並留下修改意見

點選投影片上的文字或圖形後，右側會出現檢查面板。你可以在下方留下修改意見，再請 AI 執行 /apply-comments。

![open-slide 檢查器和留言畫面](apps/web/public/assets/screenshots/inspector.webp)

### 操作畫面：簡報者模式

按下 F 進入全螢幕播放；如果需要一邊看目前頁面、一邊看下一頁和講者備註，可以使用簡報者模式。

![open-slide 簡報者模式](apps/web/public/assets/screenshots/presenter.webp)

## 圖片、影片和字型放在哪裡？

每一份簡報可以有自己的素材資料夾：

~~~text
slides/
└── my-slide/
    ├── index.tsx
    └── assets/
        ├── cover.jpg
        ├── demo.mp4
        └── font.woff2
~~~

把圖片、影片和字型放到 assets，再請 AI 把它們放進投影片。

open-slide 也提供素材管理面板，並整合 [svgl](https://svgl.app/) 搜尋品牌 SVG Logo。

## 如何匯出？

完成後建立正式版本：

~~~bash
npm run build
~~~

結果會放在 dist 資料夾。你可以輸出成靜態 HTML、PDF 或 PPTX，也可以部署到 Vercel、Cloudflare Pages、Zeabur、Netlify 或其他靜態網站空間。

預覽正式版本：

~~~bash
npm run preview
~~~

PPTX 匯出會在瀏覽器裡完成，不需要另外準備伺服器或無頭瀏覽器。

## 常見問題

### 這是 Skill 嗎？

不是。open-slide 是簡報框架和命令列工具。建立專案時，它會把幾個配套 Skill 一起放進專案，讓 Claude Code、Codex 或 Cursor 更容易做簡報。

### 我可以只下載 GitHub ZIP 嗎？

可以下載原始碼，但那是給想研究或開發 open-slide 本身的人。一般使用者不要下載 ZIP，直接執行：

~~~bash
npx @open-slide/cli init my-slide
~~~

### 我需要先會 React 嗎？

不需要。使用 AI 建立投影片時，不需要先學 React。只有想自己手動修改投影片程式碼時，才需要基本的 React 和 TypeScript 知識。

### 為什麼 npm run dev 找不到？

通常是因為你還不在專案資料夾裡，或套件還沒安裝完成。請確認：

~~~bash
cd my-slide
npm install
npm run dev
~~~

### 為什麼 AI 沒有看到 /create-slide？

請確認你是從 my-slide 專案資料夾啟動 AI 工具。Skill 放在專案裡，不是放在 GitHub 網頁或 ChatGPT 對話裡。

### 為什麼畫面變成空白？

先回到執行 npm run dev 的終端機，看有沒有錯誤訊息。把完整錯誤訊息貼給你的程式 AI，並告訴它：

~~~text
請檢查這個 open-slide 專案為什麼畫面空白。
先找出錯誤原因，再修改檔案並重新確認。
~~~

## 專案裡有哪些東西？

這個 GitHub 儲存庫本身是 open-slide 的開發原始碼：

| 路徑 | 用途 |
| --- | --- |
| packages/core | @open-slide/core，負責顯示、播放、檢查器、Vite 外掛和開發指令。 |
| packages/cli | @open-slide/cli，負責用 npx 建立新專案。 |
| apps/demo | 開發用的範例專案。 |
| apps/web | open-slide 的官方網站。 |

一般使用者不需要先研究這些資料夾。先用 CLI 建立自己的專案，只有要參與 open-slide 開發時，才需要進入這個 GitHub 儲存庫。

## 想參與開發？

這個儲存庫使用 pnpm 和 Turbo：

~~~bash
pnpm install
pnpm dev
pnpm build
pnpm check
pnpm lint
~~~

- pnpm dev：啟動開發用範例。
- pnpm build：建置所有套件。
- pnpm check：檢查格式和程式碼。
- pnpm lint：執行程式碼檢查。

## 支援作者

如果 open-slide 對你有幫助，可以支持開發：

<a href="https://buymeacoffee.com/1weiho"><img src="https://cdn.buymeacoffee.com/buttons/v2/default-yellow.png" alt="Buy Me a Coffee" height="40"></a>

## 授權

MIT © [Yiwei Ho](https://github.com/1weiho)
