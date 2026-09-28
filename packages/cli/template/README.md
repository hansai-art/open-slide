# open-slide 專案

這是一個可以直接執行的 open-slide 範例專案。

每一份投影片都放在 slides/<id>/index.tsx，並輸出一組頁面元件。你只需要寫頁面，@open-slide/core 會處理版面、縮放、頁面切換、縮圖和全螢幕播放。

## 開始使用

~~~bash
pnpm install
pnpm dev
~~~

啟動後，在瀏覽器打開終端機顯示的網址，再修改：

~~~text
slides/getting-started/index.tsx
~~~

## 指令

| 指令 | 用途 |
| --- | --- |
| pnpm dev | 啟動開發伺服器，修改後會即時更新。 |
| pnpm build | 建立可以部署的靜態網站。 |
| pnpm preview | 在本機預覽建置完成的網站。 |

## 手動寫一頁投影片

~~~tsx
// slides/my-slide/index.tsx
import type { Page, SlideMeta } from '@open-slide/core';

const Cover: Page = () => (
  <div style={{ width: '100%', height: '100%' }}>Hello</div>
);

export const meta: SlideMeta = { title: 'My slide' };
export default [Cover] satisfies Page[];
~~~

每頁都是固定的 **1920 × 1080** 畫布，設計時可以直接使用像素值。圖片、影片和字型請放在 slides/<id>/assets/，然後在投影片程式碼裡載入。

完整的投影片製作規則請看 CLAUDE.md。

## 操作方式

- 方向鍵、PageUp、PageDown：切換頁面。
- F：進入全螢幕播放。
- Esc：離開全螢幕。
- 播放時按空白鍵或右方向鍵：下一頁。
- 播放時按左方向鍵：上一頁。

## Claude Code 和其他程式 AI

這個專案裡已經準備好 .claude/skills/ 和 .agents/skills/。

在這個資料夾裡開啟 Claude Code、Codex 或 Cursor，說：

~~~text
請幫我做一份關於「我的主題」的簡報。
~~~

AI 會使用 create-slide Skill 來建立投影片。想根據瀏覽器裡留下的修改意見更新內容時，可以使用 apply-comments。

這些 Skill 是放在專案裡的輔助說明，不代表 open-slide 本身就是 Skill。

## 設定檔

可以在專案根目錄建立 open-slide.config.ts：

~~~ts
import type { OpenSlideConfig } from '@open-slide/core';

const openSlideConfig: OpenSlideConfig = {
  port: 5173,
};

export default openSlideConfig;
~~~

支援的欄位是：slidesDir、port。
