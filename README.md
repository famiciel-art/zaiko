# 家の在庫管理アプリ

Firebase Authentication と Realtime Database を使った、家庭用の在庫管理アプリです。

## 構成

- `index.html`: アプリ本体
- `firebase.json`: Firebase CLI 用の設定
- `database.rules.json`: Realtime Database のセキュリティルール

## Firebase で使っている機能

- Authentication: Googleログイン
- Realtime Database: `users/{uid}` 配下に在庫データを保存

## 公開前に必要な確認

1. Realtime Database Rules をFirebaseへ反映してください。

   ```sh
   firebase deploy --only database
   ```

2. Firebase Authentication の承認済みドメインに公開先を追加してください。

   例:

   - `localhost`
   - `ユーザー名.github.io`
   - 独自ドメイン

3. Google Cloud Console でFirebase Web APIキーにHTTPリファラ制限を設定してください。

   許可するリファラ例:

   - `http://localhost/*`
   - `https://ユーザー名.github.io/*`
   - `https://独自ドメイン/*`

## セキュリティメモ

- Firebase Webアプリの `apiKey` はブラウザに配布される前提の識別子です。
- 実際のアクセス制御は `database.rules.json` で行います。
- `ALLOWED_UIDS` はクライアント側の表示・操作補助であり、単独では保護になりません。
- サービスアカウント鍵や秘密鍵は、このリポジトリに入れないでください。

