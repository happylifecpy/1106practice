# 日序 Daybook

日序 Daybook 是以今天為中心的個人行程與任務管理單頁原型。

## 使用方式

使用 HTTPS 網址開啟網站。Firebase Google 登入使用 Firebase Web SDK（ES modules），請勿以 `file://` 方式測試。

## 功能

- 今日行程、待辦、日期切換與月曆
- 新增／編輯任務與行程、全天行程和截止日期
- 任務完成、所有任務、七日行事曆及已完成清單
- 依標題或備註搜尋
- Firebase Authentication Google 登入／登出
- 登入後依 Firebase UID 在此瀏覽器分開保存資料；未登入資料保存在訪客 localStorage
- 桌面及手機自適應版面

## Firebase Google 登入設定

1. 在 Firebase Console 建立 Firebase 專案，新增 Web App。
2. 到 Authentication → Sign-in method，啟用 Google provider。
3. 到 Authentication → Settings → Authorized domains，加入部署網域：GitHub Pages 專案站通常是 `你的 GitHub 使用者名稱.github.io`。本機測試可加入 `localhost`。
4. 將 Firebase Console Web App 的設定值填入 `index.html` 的 `firebaseConfig`：`apiKey`、`authDomain`、`projectId`、`appId`。
5. 在 HTTPS 網站重新載入後按「使用 Google 登入」測試；若瀏覽器封鎖彈出視窗，請允許後重試。

Firebase Web 設定是用戶端識別值，不是服務帳戶私鑰；不要在前端放服務帳戶金鑰或管理員憑證。

## 資料與同步

登入僅提供 Google 身分驗證；行程仍保存在目前瀏覽器的 localStorage，登入帳戶之間分開保存，不會上傳 Firebase，也不會跨裝置同步。跨裝置同步需另行接 Firestore/Realtime Database 並設定安全規則。清除瀏覽器資料可能造成資料遺失。

## 部署更新

把 `index.html` 和 `README.md` 推送到 GitHub `main` 分支。GitHub Pages 從 repository root 發布時會重新部署。Firebase 授權網域仍需在 Firebase Console 設定。