# @open-slide/core

@open-slide/core 是 open-slide 的核心套件。

它負責：

- 顯示投影片。
- 讓投影片可以切換和全螢幕播放。
- 啟動開發伺服器。
- 即時重新載入修改。
- 把投影片建置成可以發布的網站。
- 讀取 slides/<id>/index.{tsx,jsx,ts,js} 裡的投影片。

一般使用者不需要單獨安裝它。執行：

~~~bash
npx @open-slide/cli init my-slide
~~~

建立專案時，CLI 會自動把它裝好。只有在你自己手動建立既有 React 專案時，才需要直接安裝：

~~~bash
pnpm add @open-slide/core
~~~

## 這個套件裡有什麼？

- 執行環境：首頁、投影片檢視器、縮圖列、鍵盤切換和全螢幕播放。
- Vite 外掛：自動找到投影片檔案。
- 命令列工具：提供 open-slide dev、open-slide build 和 open-slide preview。

每頁固定使用 **1920 × 1080** 畫布，畫面大小由框架自動縮放。

## 指令

在已建立的 open-slide 專案裡，可以使用：

| 指令 | 用途 |
| --- | --- |
| open-slide dev | 啟動開發伺服器。 |
| open-slide build | 建立正式的靜態網站，預設輸出到 dist。 |
| open-slide preview | 在本機預覽正式版本。 |
| open-slide sync:skills | 更新專案裡的 Skill。 |

通常不需要直接輸入這些指令，使用專案提供的指令即可：

~~~bash
npm run dev
npm run build
npm run preview
npm run sync:skills
~~~

## 設定檔

如果需要調整資料夾或連接埠，可以在專案根目錄建立 open-slide.config.ts：

~~~ts
import type { OpenSlideConfig } from '@open-slide/core';

const openSlideConfig: OpenSlideConfig = {
  slidesDir: 'slides',
  port: 5173,
};

export default openSlideConfig;
~~~

所有欄位都是可選的。

如果要把網站放在子路徑，例如 GitHub Pages 的專案網址，可以設定：

~~~ts
const openSlideConfig: OpenSlideConfig = {
  base: '/my-slides/',
};
~~~

base 的前後都要有 /。

## 手動寫一頁投影片

投影片通常放在 slides/<投影片名稱>/index.tsx：

~~~tsx
import type { Page } from '@open-slide/core';

const Cover: Page = () => (
  <div className="flex h-full w-full items-center justify-center">
    <h1 className="text-[120px] font-bold">Hello, open-slide</h1>
  </div>
);

const pages: Page[] = [Cover];
export default pages;

export const meta = { title: 'Hello' };
~~~

進階使用者也可以從核心套件匯入 Page、SlideMeta、SlideModule、SlideTransition 和 OpenSlideConfig 等型別，或直接使用 @open-slide/core/vite 的 Vite 外掛。

## 什麼時候看這份文件？

- 只是想做簡報：看根目錄的中文 README。
- 想建立專案：看 @open-slide/cli 的說明。
- 想修改框架本身：看這份說明和原始碼。

## 授權

MIT
