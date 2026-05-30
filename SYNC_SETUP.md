# Huong dan dong bo Becoming Her tren nhieu thiet bi

App nay la mot website tinh. De du lieu viet tren laptop hien tren dien thoai, app can 2 phan:

1. Firebase Firestore: noi luu nhat ky tren may chu.
2. GitHub Pages hoac Firebase Hosting: noi dua app len mang de mo bang dien thoai.

## Cach app dang dong bo

- File chinh: `index.html`
- Du lieu duoc luu vao Firebase Firestore tai:
  - Collection: `becoming-her`
  - Document: `journal`
- App cung giu mot ban du phong tren may dang dung. Neu Firebase chua san sang, nhat ky khong bi mat tren thiet bi do.

Luu y quan trong: cach nay la mot cuon nhat ky dung chung cho link app. Neu ai co link va Firebase Rules dang mo, ho co the doc/sua du lieu. Muon rieng tu hon thi can them dang nhap, nhung nhu vay se la them mot tinh nang moi.

## Buoc 1: Tao Firebase project

1. Vao https://console.firebase.google.com
2. Bam `Add project`
3. Dat ten, vi du: `becoming-her`
4. Tat Google Analytics neu Firebase hoi va ban khong can
5. Bam tao project

## Buoc 2: Tao database de luu nhat ky

1. Trong Firebase project, chon `Build`
2. Chon `Firestore Database`
3. Bam `Create database`
4. Chon `Start in test mode` neu ban muon app chay nhanh de thu
5. Chon vi tri gan ban nhat, roi tao database

## Buoc 3: Lay thong tin Firebase de dan vao app

1. Trong Firebase, bam hinh banh rang gan `Project Overview`
2. Chon `Project settings`
3. Keo xuong phan `Your apps`
4. Bam icon web `</>`
5. Dat ten app, vi du: `becoming-her-web`
6. Firebase se hien doan `firebaseConfig`
7. Mo `index.html`
8. Tim doan:

```js
const firebaseConfig = {
  apiKey: "...",
  authDomain: "...",
  projectId: "...",
  storageBucket: "...",
  messagingSenderId: "...",
  appId: "..."
};
```

9. Thay toan bo thong tin trong do bang thong tin Firebase cua ban.

## Buoc 4: Mo quyen doc/ghi cho dung mot cuon nhat ky

1. Trong Firebase, vao `Firestore Database`
2. Chon tab `Rules`
3. Dan doan nay vao:

```js
rules_version = '2';

service cloud.firestore {
  match /databases/{database}/documents {
    match /becoming-her/journal {
      allow read, write: if true;
    }

    match /{document=**} {
      allow read, write: if false;
    }
  }
}
```

4. Bam `Publish`

Ghi chu: rules tren chi mo dung document `becoming-her/journal`, khong mo toan bo database. Tuy nhien, ai co link app van co the doc/sua cuon nhat ky nay.

## Buoc 5A: Dua app len GitHub Pages

1. Vao https://github.com
2. Tao repository moi, vi du: `becoming-her`
3. Upload cac file trong thu muc nay len repository:
   - `index.html`
   - `manifest.json`
   - `_redirects`
   - `netlify.toml`
   - cac file icon, favicon
4. Vao repository tren GitHub
5. Chon `Settings`
6. Chon `Pages`
7. O `Build and deployment`, chon:
   - Source: `Deploy from a branch`
   - Branch: `main`
   - Folder: `/root`
8. Bam `Save`
9. Doi vai phut, GitHub se cho ban link dang:
   - `https://ten-cua-ban.github.io/becoming-her/`

Mo link do tren laptop va dien thoai. Neu Firebase dung, du lieu se giong nhau.

## Buoc 5B: Dua app len Firebase Hosting

Dung cach nay neu ban muon tat ca nam trong Firebase.

1. Cai Node.js neu may chua co: https://nodejs.org
2. Mo terminal trong thu muc app
3. Dang nhap Firebase:

```bash
npm install -g firebase-tools
firebase login
```

4. Khoi tao hosting:

```bash
firebase init hosting
```

Khi Firebase hoi:

- `Use an existing project`: chon project vua tao
- `What do you want to use as your public directory?`: nhap `.`
- `Configure as a single-page app?`: chon `Yes`
- Neu hoi co ghi de `index.html` khong: chon `No`

5. Dua app len mang:

```bash
firebase deploy
```

Firebase se hien link web sau khi deploy xong.

## Cach kiem tra dong bo

1. Mo app tren laptop
2. Viet mot entry moi va bam `Save`
3. Mo cung link app tren dien thoai
4. Doi vai giay
5. Entry do phai hien tren dien thoai

Cham tron nho goc tren ben phai la trang thai dong bo:

- Xanh: da dong bo
- Vang: dang dong bo
- Hong/do: Firebase chua ket noi duoc hoac rules/config sai

