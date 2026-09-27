# Tarot Table 塔羅牌桌

整個網站只有一個檔案：`index.html`。不需要安裝任何東西，也不需要後端，直接上傳就能用。

## 方法一：Netlify Drop（最簡單，約 1 分鐘）

1. 打開 https://app.netlify.com/drop
2. 把整個資料夾（裡面有 `index.html`）拖進網頁。
3. 完成後會得到一個網址，例如 `https://xxxx.netlify.app`。
4. 想保留網站、改網址的話，註冊一個免費帳號，在 Site settings 裡修改網站名稱。

## 方法二：GitHub Pages

1. 在 GitHub 建立一個新的 repository（例如 `tarot`），設成 Public。
2. 按 **Add file → Upload files**，上傳 `index.html`，再按 Commit。
3. 進入 **Settings → Pages**，Source 選 **Deploy from a branch**，Branch 選 `main`、資料夾選 `/ (root)`，按 Save。
4. 等一兩分鐘，網址會是 `https://你的帳號.github.io/tarot/`。

## 方法三：放到你已經有的網站

把 `index.html` 上傳到主機上的任何資料夾即可。
例如上傳到 `/tarot/index.html`，網址就是 `https://你的網域/tarot/`。

## 綁定自己的網域

Netlify、GitHub Pages 和 Vercel 都可以免費綁定自己的網域，在各平台的網域（Domain）設定裡照著步驟做就可以了。

## 之後要修改

- 修改 `index.html` 後，重新上傳覆蓋舊檔案就好。
- 牌義資料在檔案裡的 `ZH_MAJORS`、`ZH_MINORS`（中文）和 `EN_MAJORS`、`EN_MINORS`（英文），可以直接改文字。
- 綜合解讀的句子在 `SUM` 這一段。

## 備註

- 網站會用瀏覽器記住上次選的語言，不會收集任何使用者資料。
- 字型從 Google Fonts 載入，連不上時會自動改用系統字型，功能不受影響。
