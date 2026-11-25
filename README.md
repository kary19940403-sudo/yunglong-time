# 簽到表產生器

純前端（GitHub Pages）＋ Firebase（Google 登入 + Firestore 雲端同步）。
沒設定 Firebase 時，資料只存在瀏覽器 localStorage，功能照常可用。

## 一、Firebase 設定（約 10 分鐘）
1. https://console.firebase.google.com → 新增專案（Analytics 可關）。
2. **Build → Authentication → Sign-in method** → 啟用 **Google**。
3. **Authentication → Settings → Authorized domains** → 新增 `你的帳號.github.io`。
4. **Build → Firestore Database** → 建立資料庫（正式模式，地區選 `asia-east1` 台灣）。
5. **Firestore → 規則** → 貼上 `firestore.rules`，把允許名單改成你們的 Email → 發布。
6. **專案設定 → 一般 → 您的應用程式 → 新增網頁應用程式（`</>`）** → 複製 `firebaseConfig`，貼進 `firebase-config.js`。

## 二、上 GitHub Pages
1. 在 GitHub 建立新 repo，把本資料夾四個檔案上傳（index.html、firebase-config.js、firestore.rules、README.md）。
2. Repo → **Settings → Pages** → Source 選 `Deploy from a branch`，Branch 選 `main` / `(root)` → Save。
3. 約一分鐘後網址為 `https://你的帳號.github.io/repo名稱/`。

## 注意
- Pages 網址是公開的，**不要把真實人員資料寫進程式碼或 commit**；資料只放在 Firebase。
- 若公司需要不對外公開，建議用 GitHub 付費方案的私有 Pages，或改放 Firebase Hosting。
- 同步方式是「後寫入者覆蓋」：登入時會以雲端資料為準；兩人同時編輯時，後存的會蓋掉先存的。
- 規則是真正的防線，請務必確認已發布，且沒有使用「測試模式」。
