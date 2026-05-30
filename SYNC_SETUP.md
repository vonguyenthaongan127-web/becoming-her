# Huong dan dong bo Becoming Her ban hien tai

Day la folder can deploy len Netlify:

`C:\Users\THIS PC\Downloads\becoming-her-deploy_2\becoming-her`

Folder `C:\Users\THIS PC\Downloads\becoming-her` la ban cu, khong phai ban dang chay tren link Netlify hien tai.

## Viec da lam trong file app

- Da thay Firebase config moi cua project `becomgingher`.
- Da giu nguyen cac chuc nang hien tai cua app.
- Da them ban luu du phong tren thiet bi. Neu mang hoac Firebase bi loi, du lieu vua nhap van duoc giu tren may do.

## Can lam trong Firebase

1. Vao https://console.firebase.google.com
2. Mo project `becomgingher`
3. Vao `Firestore Database`
4. Neu chua tao database, bam `Create database`
5. Vao tab `Rules`
6. Dan rules nay:

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

7. Bam `Publish`

## Deploy lai tren Netlify

Neu ban deploy bang cach keo-tha folder:

1. Vao Netlify
2. Mo site `beoming-her`
3. Vao `Deploys`
4. Keo-tha folder nay vao Netlify:

`C:\Users\THIS PC\Downloads\becoming-her-deploy_2\becoming-her`

Neu Netlify yeu cau zip file, hay zip **cac file ben trong folder `becoming-her`**, khong zip folder cha `becoming-her-deploy_2`.

## Kiem tra

1. Mo https://beoming-her.netlify.app/ tren laptop
2. Viet mot entry moi, bam `Save`
3. Mo cung link do tren dien thoai
4. Doi vai giay
5. Entry phai hien tren dien thoai

Cham tron nho goc phai:

- Xanh: da dong bo
- Vang: dang dong bo
- Hong/do: Firebase config hoac Rules chua dung

## Luu y rieng tu

Rules o tren giup app chay nhanh va de test, nhung ai co link app cung co the doc/sua journal neu biet cach. Neu muon chi rieng ban xem duoc, can them dang nhap Firebase Authentication sau.

