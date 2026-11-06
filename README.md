# MDRT 2027 平台 App 外殼（PWA）部署說明

這個資料夾是一個小網站，放上 GitHub Pages 後，平台就能「安裝」到手機與電腦：有自訂圖示與名稱、全螢幕開啟，並由外殼保管「記住我」的登入狀態。

## 一、上傳到 GitHub Pages（約 5 分鐘）

1. 登入 GitHub，新增一個 **Public** 儲存庫，名稱填 `mdrt2027-app`（免費方案只有公開儲存庫能用 Pages；這裡只放外殼，不含任何平台資料）。
2. 在儲存庫頁面點「Add file → Upload files」，把本資料夾內的 `index.html`、`manifest.webmanifest`、`sw.js` 與整個 `icons` 資料夾拖進去，按「Commit changes」。
3. 點「Settings → Pages」，Source 選「Deploy from a branch」，Branch 選 `main`、資料夾 `/ (root)`，按 Save。
4. 約 1～2 分鐘後，網址 `https://a24615-justin.github.io/mdrt2027-app/` 就能開啟。

## 二、平台端（Apps Script）

1. 用這次提供的 `Index.html` 整份覆蓋（已加入外殼代管登入的功能，只會把登入憑證交給 `https://a24615-justin.github.io`）。
2. 「部署 → 管理部署作業 → 編輯 → 版本：新版本」重新部署。**請務必選「新版本」，不要建立新的部署**，否則平台網址會改變，外殼就連不到。
3. 若平台網址真的變了：打開 `index.html`，把最上方 `APP_URL` 換成新的 `/exec` 網址，再上傳一次。
4. 若 GitHub 帳號或儲存庫網址不同：把平台 `Index.html` 的 `WRAPPER_ORIGINS` 改成你的 GitHub Pages 網域（只填到 `.github.io` 為止）。

## 三、使用者安裝方式

- **iPhone**：用 Safari 開啟網址 → 點下方「分享」→「加入主畫面」。從 LINE 點開時，請先選「以 Safari 開啟」。
- **Android**：用 Chrome 開啟，畫面下方會出現「安裝」按鈕；或點右上角「⋮ → 安裝應用程式」。
- **電腦**：用 Chrome 或 Edge 開啟，網址列右側點「安裝」圖示。
- 推廣時可直接使用 `MDRT2027_平台QRCode.png`。

## 四、注意事項

- 平台資料仍全部存放在 Google 試算表，外殼只負責開啟畫面，沒有網路時會顯示「目前沒有網路連線」。
- 一般 Gmail 帳號部署的 Apps Script 網頁，上方可能會出現 Google 的提醒列，屬於正常現象；使用 Google Workspace 公司帳號部署則不會出現。
- 圖示放在 `icons/`，要換成公司標誌時，替換同尺寸的 PNG 檔即可（192、512、180、32 像素）。
