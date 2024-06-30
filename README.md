# auth-scheduled-backup-import

This script is to backup the Firebase users that were exported by the [Backup Users to Cloud Storage extension](https://extensions.dev/extensions/50fifty/auth-scheduled-backup)

## 1. Pre-requisites

> [!IMPORTANT] 
> This script is requires the following pre-requisites to be set up before running the script.

### 1.1. Edit the `index.ts` file
Edit the `hash` parameter in the `importUsers` method in the `index.ts` file to match the key and salt separator that was used in your Firebase project. 

Use the signer key and salt separator from the Firebase Console under Firebase Authentication -> Users -> Click on the three dots -> password hash parameters.

If you were using the default Firebase configuration, just fill in the signer key and salt separator. If you used a custom configuration, see this [Firebase documentation](https://firebase.google.com/docs/auth/admin/import-users) for more information.

### 1.2. Download the service account key from your Firebase project
1. Go to the Firebase Console
2. Click on the gear icon next to Project Overview
3. Click on Project Settings
4. Click on the Service Accounts tab
5. Click on the Generate new private key button (Node.js is the default option, so you can just click Generate Key)
6. Save the file to the root of this repository and name it `service-account-key.json`

## 2. Running the script
1. Clone this repository
2. Run `npm install`
3. Edit the `index.ts` file as described in the pre-requisites
4. Download and place the service account key in the root of this project as described in the pre-requisites
5. Run `npm run start`