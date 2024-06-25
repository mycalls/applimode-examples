# Configure Applimode for Windows

<!--
1. Install Git
2. Install VSCode and the Flutter SDK
3 Install Android Studio
4. Configure Firebase
5. Install Node.js and the Firebase CLI and the Futterfire CLI
6. Configure your project
7. Test drive
8. Add administrator
9. Admin settings and custom settings
10. Build an Android app
11. Build a web app
12. Configure Cloudflare R2 (Optional)
13. Configure Cloudflare D1 (Optional)
14. Configure Cloudflare CDN (Optional)
15. Configure Youtube image proxy (Optional)
16. Configure Youtube video proxy (Optional)
17. Configure push notification (Optional)
18. Use your custom domain (Optional)
19. Upgrade your project with the new Applimode version
20. Configure Cloud Firestore Security Rules 
21. Troubleshooting
-->

> [!IMPORTANT]
> * This guide is written in detail for beginners. Skip the unnecessary parts.
> * To install your applimode app on an iOS device, you need a device with macOS installed. For more details visit [Configure Applimode for macOS]().
<!--Todos 링크 추가해 줄것-->


## 1. Install Git
* Download and install [Git](https://gitforwindows.org/).
<!--
* Press ```Window key``` + ```S```, type **PowerShell** and click.
* Run the following command.
```sh
git --version
```
* Close **PowerShell**.
-->


## 2. Install VSCode and the Flutter SDK
* Download and install and launch [VSCode](https://code.visualstudio.com/).
* Click **View** (on the top menu of VSCode) and select **Extensions**. (or ```Ctrl``` + ```Shift``` + ```X```)
* Type *flutter*, click **Install**.
* Click **View** (on the top menu of VSCode) and select **Command Palette...**. (or ```Ctrl``` + ```Shift``` + ```P```)
* In the **Command Palette**, type *flutter*.
* Select **Flutter: New Project**.
* Click **Download SDK** on the bottom right.
* Click **New folder** (or ```Ctrl``` + ```Shift``` + ```N```) and name it *dev*.
* Click **Clone Flutter**.
* Click **Add SDK to PATH**
<!--
* To open the **VScode**'s built-in terminal, click **View** (on the top menu of VSCode) and select **Terminal**.
* Run the following command.
```sh
flutter doctor
```
-->
* Close **VScode**


## 3. Install Android Studio
* Download and install and launch [Android Studio](https://developer.android.com/studio).
* Click **Pulgins** (on the left sidebar) and type *flutter* and click **Install**.
* Click **Projects** (on the left sidebar) and **More Actions** (on the Center) and **SDK Manager**.
* Click **SDK Tools** (on the top menu).
* Check **Android SDK Command-line Tools**, **Google USB Driver** and click **Apply** on the bottom right.
* Open **VSCode** and click **View** (on the top menu of VSCode) and select **Terminal**.
* Run the following commands and press ```y``` to all questions.
```sh
flutter doctor --android-licenses
```
<!--
```sh
flutter doctor
```
-->
* Close **Android Studio** and **VSCode**


## 4. Configure Firebase
* Sign up or log in [Firebase](https://firebase.google.com).
* Click [Go to console](https://console.firebase.google.com).
* Click **Add project**.
* Enter a project name and click **Continue**.
* Disable **Google Analytics** and click **Create project**. (You can change this setting later.)
* Click **Build** (on the left sidebar) and click **Authentication**.
* Click **Get started** and click **Email/Password**.
* Enable the **Email/Password** and click **Save**.
* Click **Build** (on the left sidebar) and click **Firestore Database**.
* Click **Create database** and select a location for your database.
* Click **Next** and click **Create**.
* Click **Build** (on the left sidebar) and click **Storage**.
* Click **Get started** and click **Next** and click **Done**.


## 5. Install Node.js and the Firebase CLI and the Futterfire CLI
* Download and install [Node.js](https://nodejs.org).
* Press ```Window key``` + ```S``` or the search button and type *Powershell* and click.
* Run the following command.
```sh
Set-ExecutionPolicy Unrestricted
```
```sh
npm install -g firebase-tools
```
* Close **PowerShell** and reopen it.
* Run the following command.
```sh
firebase login
```
```sh
dart pub global activate flutterfire_cli
```
* Press ```Window key``` + ```S``` or the search button and type *ENV*.
* Select **Edit the system environment variables**.
* Click **Environment Variables...** on the **Advanced** tap.
* In the **User variables for (username) section**, double-click **Path**.
* Click **New** and type *%USERPROFILE%\AppData\Local\Pub\Cache\bin*
* Click **OK** three times.


## 6. Configure your project
* Open **PowerShell**.
* Run the following commands.
```sh
mkdir projects; cd projects;
```
```sh
git clone https://github.com/mycalls/applimode-tool.git
```
```sh
git clone https://github.com/mycalls/applimode.git
```
* Close **PowerShell**.
* Open **VSCode**
* Click **File** (on the top menu of VSCode) and select **Open Folder** and select **applimode-tool** (in the **projects** folder) and click **Open**.
* Click **View** (on the top menu of VSCode) and select **Terminal**.
* Modify and run the following command.
```sh
npm run init -- --project-name="project name" --full-name="App Full Name" --short-name="App Short Name" --organization-name="myhome" --firebase-name="firebaseProjectId" --worker-key="yourWorkerKey" --main-color="FCB126"
```
<!--Todos
각 parameter에 대한 설명을 별도의 페이지로 만들어 직접 변경을 원하는 사람들에 대한 가이드도 제공할 것
-->
> [!NOTE]
> * If the project name, full name, and short name are all the same, you can enter only the project name.
> * The project name can only be alphabets, and a combination of two words is recommended.
> * To find the firebase project ID, go to your firebase project page -> click the settings button on the left -> select Project settings -> copy Project ID.
> * The worker key is used to store media files using Cloudflare's R2. This is optional and enter your desired password.
> * The default media file storage is Firebase Cloud Storage, and no separate settings are required.
> * You can set up Cloudflare R2 as your media file storage, follow [this guide](#9-configure-cloudflare-r2-optional).
> * The full name, short name, worker key, main color ​​can be changed later.

* Prepare images to be used for the app icon and launch screen.
<!--Todos 피그마 공유 템플릿 파일 만들고 링크 제공할 것-->
> [!NOTE]
> * app-bar-logo.png - 128 * 128 (Margin of about 4 px, no background)
> * app-icon-512.png - 512 * 512 (Use an image of 1024 px)
> * app-icon-1024.png - 1024 * 1024 (Margin of about 160 px)
> * app-logo-android12.png - 960 * 960 (Margin of about 240, no background)
> * app-logo.png - 720 * 720 (Margin of about 8 px, no background)
* Open File Explorer. (press ```Window key``` + ```E```)
* Open your project folder (maybe in the projects folder), open the assets folder, and then open the images folder.
* Replace the image files in the folder with the image files you prepared.
* Go back to **VSCode**.
* Click **File** (on the top menu of VSCode) and select **Open Folder** and select your project folder (maybe in the **projects** folder) and click **Open**.
* Click **View** (on the top menu of VSCode) and select **Terminal**.
* Run the following commands in order:
```sh
flutter pub get
```
```sh
dart run flutter_native_splash:create
```
```sh
flutter pub run flutter_launcher_icons
```
```sh
dart run build_runner build -d
```
```sh
flutterfire configure (n to the question.)
```
```sh
firebase deploy --only firestore
```
```sh
firebase deploy --only storage
```
* If you want to enter commands at once, run the following command:
```sh
flutter pub get; dart run flutter_native_splash:create; flutter pub run flutter_launcher_icons; dart run build_runner build -d; flutterfire configure; firebase deploy --only firestore; firebase deploy --only storage;
```
* Open [Google Cloud console](https://console.cloud.google.com/) in your web browser.
* Sign up or log in.
* Select your project on the top left.
* Click **Activate Cloud Shell** on the top right.
![gcp-console-head](https://github.com/mycalls/applimode-examples/blob/main/assets/gcp-console-head.png?raw=true)
* Run the following command in the shell on the bottom.
```sh
echo '[{"origin": ["*"],"method": ["GET"],"maxAgeSeconds": 3600}]' > cors.json
```
<!--
> touch cors.json
> nano cors.json
[
  {
    "origin": ["*"],
    "method": ["GET"],
    "maxAgeSeconds": 3600
  }
]
-->
* Open your [Firebase console](https://console.firebase.google.com/) in your web browser. 
* Click your project.
* Click **Storage** (on the left siedbar).
* Click the Copy folder path icon (on the right of the url starting with **gs://**) to copy your cloud storage bucket.
![fb-storage-head](https://github.com/mycalls/applimode-examples/blob/main/assets/fb-storage-head.png?raw=true)
* Go back to your Google Cloud console.
* Run the following command in the shell on the bottom.
```sh
gsutil cors set cors.json gs://<your-cloud-storage-bucket>
```


## 7. Test drive
* Click **View** (on the top menu of VSCode) and select **Command Palette**. (or press ```Ctrl``` + ```Shift``` + ```P```)
* Type *flutter* and select the **Flutter: Select Device**.
> [!IMPORTANT]
> To install your applimode app on an iOS device, you need a device with macOS installed. For more details visit [Configure Applimode for macOS]().
<!--Todos 링크 추가해 줄것-->
* Select a target device from Select Device prompt.
* Click Run (on the top menu of VSCode) and select **Start Debugging**. (or press ```F5``` or ```Fn``` + ```F5```)
* After the app build completes, click the write button on the bottom right.
* Click **Register** in the login screen and complete your signup.
* Click the write button and write the first post. (if you test Cloudflare R2 or CDN, write the post with a image or a video)
> [!NOTE]
> * In debugging mode, the performance of most apps becomes very slow. Don't worry about the performance because Applimode in release mode is very fast.
> * Select Chrome or Edge for web apps.
> * To enable Developer options and USB debugging on your android device, refer to [this page](https://developer.android.com/studio/debug/dev-options).
> * If you connect an Android device but it does not appear in the device list, try changing the USB Preferences to Charging or File transfers.
<!-- * To enable them, go to Settings > About phone > Software information (there may not be) > Build number, click 7 times in a row. Return to the previous screen to find Developer options on the bottom. Then turn on USB debugging.-->


## 8. Add administrator
* Open your [Firebase console](https://console.firebase.google.com/) in your web browser. 
* Click your project.
* Click **Authentication** (on the left siedbar).
* Click the **Copy UID** button next to your **User UID**. (Move your mouse cursor over your **User UID** to display the button)
![fb-auth-head](https://github.com/mycalls/applimode-examples/blob/main/assets/fb-auth-head.png?raw=true)
* Click **Firestore Database** (on the left sidebar).
* Click the users collection and select your uid.
* Click the **Edit field** button (pencil shape) next to the **isAdmin** field. (Move your mouse cursor over the **isAdmin** field to display the **Edid field** button)
![fb-firestore-isadmin](https://github.com/mycalls/applimode-examples/blob/main/assets/fb-firestore-isadmin.png?raw=true)
* Change the value from **false** to **true** and click **Update**.
* Click **Rules** (on the top menu).
* Change the first word **adminUid** in line 8 (or near it) to your uid. (paste your uid)
> ex) return request.auth.uid in ["9a6sIEiAldOzFIZ9hO2SxaG6Db63", "adminUid"];
![fb-firestore-rules](https://github.com/mycalls/applimode-examples/blob/main/assets/fb-firestore-rules.png?raw=true)
* Click **Publish**
> [!CAUTION]
> If you designate someone as an administrator, the user can change admin settings in the app, edit, delete or block all posts, and even block all posts from a specific user.


## 9. Admin settings and custom settings
> [!NOTE]
> * If you change the custom settings file, you must rebuild it to apply it to your app.
> * When changing Admin settings, users fetch the values ​​on your app's the first startup, and the values ​​are applied on your app's the second startup.
> * The default minimum fetch interval for Admin settings is 600 seconds (10 minutes) and you can change it in the custom settings file.

* [Add administrator](#8-add-administrator) is required first to activate the Admin Settings tab in your app.
* Open your applimode app.
* Click the menu button on the top left of the home screen.
* Click **Admin settings**. (If you can't find the Admin settings tap, restart your app.)
* After changing the settings, click Save on the bottom.
<!--todos 각 설정에 대한 상세 설명 페이지 만들고 여기에 링크 추가-->
* To change the custom settings, open VSCode.
* Click **File** (on the top menu of VSCode) and select **Open Folder** and select your project folder (maybe in the **projects** folder) and click **Open**.
* Press ```Ctrl``` + ```P``` and type *custom_settings.dart* and click.
* Change appCreator and appVersion to your desired value.
> [!IMPORTANT]
> fullAppName, shortAppName, underbarAppName, camelAppName, androidBundleId, appleBundleId, and firebaseProjectName are values ​​used when upgrading your project. Do not change them. If you want to make changes, refer to [this chapter](#6-configure-your-project) and configure your project again.
* The values ​​with **spare** in front of the name are ​​used when users first run your app after installing it. (when Admin settings are not yet activated). You can change it to whatever value you want.
* If you want to register your app on the App Store or Play Store, add the corresponding links to **termsUrl** and **privacyUrl**.
* If you change the value of **isInitialSignIn** to true, only logged in users will be able to use your app. You can also use Cloud Firestore Security Rules for even stronger security. Please read [this chapter](#20-configure-cloud-firestore-security-rules) for more details.
* If you change the value of **adminOnlyWrite** to true, only users designated as administrators can write posts.
* Read [this chapter](#17-configure-push-notification-optional) to change the values ​​of **useFcmMessage**, **fcmVapidKey**, and **useApns** to true.
* We will prepare more detailed information of all values ​​of Admin settings and Custom settings soon.

## 10. Build an Android app
* Open **VSCode**.
* Click **File** (on the top menu of VSCode) and select **Open Folder**.
* Select your project folder and click **Open**.
* Click **View** (on the top menu of VSCode) and select **Terminal**.
* Run the following command:
```sh
flutter build apk --release --target-platform=android-arm64
```
> [!IMPORTANT]
> If you change the custom settings file, you need to re-run the command to update your app.
* You can find your apk file: **\<your-applimode-project-folder\>/build/app/outputs/apk/release**
> For more details, visit [this link](https://docs.flutter.dev/deployment/android#build-the-app-for-release).


## 11. Build a web app
<!--
// build/web
> firebase init
> flutter build web --release
> flutter build web --release --web-renderer=html
> flutter build web --release --web-renderer=canvaskit
> firebase deploy
> firebase deploy --only hosting
-->
* Open **VSCode**.
* Click **File** (on the top menu of VSCode) and select **Open Folder**.
* Select your project folder and click **Open**.
* Click **View** (on the top menu of VSCode) and select **Terminal**.
* Run the following command:
```sh
flutter build web --release --web-renderer=html
```
```sh
firebase deploy --only hosting
```
> [!IMPORTANT]
> If you change the custom settings file, you need to re-run the commands to update your app.
* Open your [Firebase console](https://console.firebase.google.com/) in your web browser. 
* Click your project.
* Click **Hosting** (on the left siedbar).
* Scroll down and you can find the **Domains** section.
* Click the domain address.
* If you want to use your custom domain, read [this chapter](#18-use-your-custom-domain-optional).
* Please visit [this page]() for how to install a PWA(Progressive Web App) on your phone and computer.
<!--todos pwa 설치 방법 페이지 만들고 링크 추가-->


## 12. Configure Cloudflare R2 (Optional)
> [!NOTE]
> * The biggest advantage of R2 is that transfer fees are free. (Firebase Cloud Storage is free for transfers up to 1 GB per day, after which a fee of $0.12 is charged for each GB)
> * You can also use Cloudflare's CDN for free by registering a domain and connecting it with R2.
> * If you are building a video-centric app, I highly recommend using Cloudflare R2.
> * [R2 pricing plans](https://developers.cloudflare.com/r2/pricing/)
> * [Workers pricing plans](https://developers.cloudflare.com/workers/platform/pricing/)
* Go to the [Cloudflare console](https://dash.cloudflare.com/sign-up).
* Sign up or log in.
* Click **R2** (on the left sidebar).
* Fill the **R2** subscription form, complete the **R2** subscription.
* Open **PowerShell**.
* Run the following commands.
```sh
cd projects
```
```sh
npm create cloudflare@latest <your_r2_worker_name>
```
> ex) npm create cloudflare@latest applimode-r2-worker
* Select default values ​​for all questions.
* Open **VSCode**.
* Click **File** (on the top menu of VSCode) and select **Open Folder**.
* Select the <your_r2_worker_name> folder and click **Open**.
* Click **View** (on the top menu of VSCode) and select **Terminal**.
* Run the following command:
```sh
npx wrangler r2 bucket create <your_r2_bucket_name>
```
> ex) npx wrangler r2 bucket create applimode-bucket
* Press ```Ctrl``` + ```P``` and type *wrangler.toml* and click.
* Add the following to the end of your wrangler.toml file.
```
account_id = "YOUR_ACCOUNT_ID" # ← Replace with your Account ID.
workers_dev = true

[[r2_buckets]]
binding = "MY_BUCKET"
bucket_name = "YOUR_BUCKET_NAME" # ← Replace with your bucket name.
```
* Update **account_id** and **bucket_name**.
> * To find your account ID and bucket name go to [Cloudflare dashboard](https://dash.cloudflare.com/) and click R2 (on the left sidebar).
> * Click the **Click to copy** button below **Account ID** on the right side.
> * Copy your bucket name below **Buckets** on the center side.
![cf-r2-overview](https://github.com/mycalls/applimode-examples/blob/main/assets/cf-r2-overview.png?raw=true)
<!-->
> * Or you can also find them using the following commands
```sh
npx wrangler whoami 
```
```sh
npx wrangler r2 bucket list
```
-->
* To save, press ```Ctrl``` + ```S```. (or **File** > **Save**)
<!--
* Click **File** (on the top menu of VSCode) and select **New Window**.
* Click **File** (on the top menu of VSCode) and select **Open Folder**.
* Select the <your_applimode_project_name> folder and click **Open**. (maybe in your **projects** folder)
* Press ```Ctrl``` + ```P``` and type *r2_worker.index.ts* and click.
* Press ```Ctrl``` + ```A``` and press ```Ctrl``` + ```C```.
 -->
* Open this [page](https://github.com/mycalls/applimode-examples/blob/main/r_two_Worker/r2_worker.index.ts) and click the **Copy raw file** button (next to the **Raw** button) on the upper-right corner of the file view.
![copy-raw-file](https://github.com/mycalls/applimode-examples/blob/main/assets/gh-copy-raw-file.png?raw=true)
* Go back to VSCode.
* Press ```Ctrl``` + ```P``` and type *index.ts* and click.
* Press ```Ctrl``` + ```A``` and press ```Ctrl``` + ```V```.
* To save, press ```Ctrl``` + ```S```. (or **File** > **Save**)
* Click **Terminal** on the bottom of VSCode and run the following commands. (<your_worker_key> is the one you entered in the [Configure your project](#6-configure-your-project) section.)
```
npx wrangler secret put <your_worker_key>
```
```
npx wrangler deploy
```
* Click **File** (on the top menu of VSCode) and select **Open Folder** and select your project folder (maybe in the **projects** folder) and click **Open**.
* Press ```Ctrl``` + ```P``` and type *custom_settings.dart* and click.
* Press ```Ctrl``` + ```S``` and type *useRTwoStorage*.
* Change the useRTwoStorage value from **false** to **true**.
> ex) const bool useRTwoStorage = true;
* Go to the [Cloudflare dashboard](https://dash.cloudflare.com/).
* Go to Workers & Pages (on the left sidebar) and in Overview, select your Worker.
* Go to Settings > Triggers > Routes.
* Copy your route.
![cf-workers-triggers](https://github.com/mycalls/applimode-examples/blob/main/assets/cf-workers-triggers.png?raw=true)
* Go back to VSCode.
* Press ```Ctrl``` + ```S``` and type *rTwoBaseUrl*.
* Change the rTwoBaseUrl value from **yourR2WorkerUrl** to the route you copied.
> ex) const String rTwoBaseUrl = 'applimode-r2-worker.yourID.workers.dev';
* Press ```Ctrl``` + ```S```. (or **File** > **Save**)
* To make sure it works well, follow the [Test drive](#7-test-drive) chapter.


## 13. Configure Cloudflare D1 (Optional)
> [!NOTE]
> * Applimode supports hashtag search by default. Search is possible only if the user adds # in front of the word when writing a post.
> * If you only want to use hashtag search, skip this chapter, or if you want to use full-text search, follow this chapter.
> * [D1 pricing plans](https://developers.cloudflare.com/d1/platform/pricing/)
* Open **PowerShell**.
* Run the following commands.
```sh
cd projects
```
```sh
npm create cloudflare@latest <your_d1_worker_name>
```
> ex) npm create cloudflare@latest applimode-d1-worker
* Select default values ​​for all questions.
* Open **VSCode**.
* Click **File** (on the top menu of VSCode) and select **Open Folder**.
* Select the <your_d1_worker_name> folder and click **Open**.
* Click **View** (on the top menu of VSCode) and select **Terminal**.
* Run the following command:
```sh
npx wrangler d1 create <db-name>
```
> ex) npx wrangler d1 create applimode-d1
* Copy the following part of the output.
```
[[d1_databases]]
binding = "DB" # i.e. available in your Worker on env.DB
database_name = "applimode-d1"
database_id = "<unique-ID-for-your-database>"
```
* Press ```Ctrl``` + ```P``` and type *wrangler.toml* and click.
* Add the part you copied to the end of your wrangler.toml file.
* To save, press ```Ctrl``` + ```S```. (or **File** > **Save**)
* Open this [page](https://github.com/mycalls/applimode-examples/blob/main/d_one_worker/d1.posts.sql) and click the **Copy raw file** button (next to the **Raw** button) onn the upper-right corner of the file view.
* Go back to VSCode.
* Click **File** and click **New File...**. (or click the New File button)
![vscode-new-file](https://github.com/mycalls/applimode-examples/blob/main/assets/vs-create-file.png?raw=true)
* Type posts.sql and press **Enter** and click **Create File**. (on your project root folder)
* To paste and save, press **Ctrl** + **V** and **Ctrl** + **S**.
* Open this [page](https://github.com/mycalls/applimode-examples/blob/main/d_one_worker/d1_worker.index.ts) and click the **Copy raw file** button (next to the **Raw** button) onn the upper-right corner of the file view.
* Go back to VSCode.
* Press ```Ctrl``` + ```P``` and type *index.ts* and click.
* Press ```Ctrl``` + ```A``` and press ```Ctrl``` + ```V```.
* To save, press ```Ctrl``` + ```S```.
* Click **Terminal** on the bottom of VSCode and run the following commands. (To find your your-d1-db-name, go to the **wrangler.toml** file, refer to **database_name**)
```
npx wrangler d1 execute <your-d1-db-name> --remote --file=./posts.sql
```
```
npx wrangler deploy
```
* Click **File** (on the top menu of VSCode) and select **Open Folder** and select your project folder (maybe in the **projects** folder) and click **Open**.
* Press ```Ctrl``` + ```P``` and type *custom_settings.dart* and click.
* Press ```Ctrl``` + ```S``` and type *useDOneForSearch*.
* Change the useDOneForSearch value from **false** to **true**.
> ex) const bool useDOneForSearch = true;
* Go to the [Cloudflare dashboard](https://dash.cloudflare.com/).
* Go to Workers & Pages (on the left sidebar) and in Overview, select your Worker.
* Go to Settings > Triggers > Routes.
* Copy your route.
* Go back to VSCode.
* Press ```Ctrl``` + ```S``` and type *dOneBaseUrl*.
* Change the dOneBaseUrl value from **yourD1WorkerUrl** to the route you copied.
> ex) const String rTwoBaseUrl = 'applimode-d1-worker.yourID.workers.dev';
* Press ```Ctrl``` + ```S```. (or **File** > **Save**)
* To make sure it works well, follow the [Test drive](#7-test-drive) chapter.


## 14. Configure Cloudflare CDN (Optional)
> [!IMPORTANT]
> * To use Cloudflare's CDN, your domain must be registered with Cloudflare.
> * If you don't have a domain, go to the [Cloudflare console](https://dash.cloudflare.com/) and click **Domain Registration** (on the left sidebar) and click **Register Domain**.
> * If you need to transfer your domain to cloudflare, go to the [Cloudflare console](https://dash.cloudflare.com/) and click **Domain Registration** (on the left sidebar) and click **Transfer Domain**.
> * [Domain registration documentation](https://developers.cloudflare.com/registrar/get-started/register-domain)
> * [Domain transfer documentation](https://developers.cloudflare.com/registrar/get-started/transfer-domain-to-cloudflare/)

* Go to the [Cloudflare console](https://dash.cloudflare.com/).
* Click **R2** (on the left sidebar) and in **Overview**, select the bucket you want.
* Click **Settings** on the top, scroll down until you see the **Public access** section.
* In **Custom Domains**, click **Connect Dommain**.
* Type the domain for CDN and click Continue.
> If you have a domain called applimode.com, type a sub domain like *<n>media.<n>applimode.<n>com* or *<n>cdn.<n>applimode.<n>com* or *<n>content.<n>applimode.<n>com*.
* Click **Websites** (on the left sidebar) and click your domain.
* Click **Rules** (on the left sidebar) and **Transform Rules** and **Modify Response Header** (on the tap menu).
* Click **+ Create rule**.
* Type the rule name like *applimode-r2-cors*.
* Select **Custom filter expression**.
* In **Field**, select **Hostname** and in **Operator**, select **equals** and in **Value, type the sub domain you connected to your R2 bucket. (like *<n>media.<n>applimode.<n>com* or *<n>cdn.<n>applimode.<n>com* or *<n>content.<n>applimode.<n>com*)
* In **Select item**, select **Add**.
* In Header name, copy and paste the following expression.
```
access-control-allow-origin
```
* In Value, type __*__.
* Click **Deploy**.
![cf-websites-rules](https://github.com/mycalls/applimode-examples/blob/main/assets/cf-websites-rules.png?raw=true)
* Open or go back to VSCode.
* Click **File** (on the top menu of VSCode) and select **Open Folder** and select your project folder (maybe in the **projects** folder) and click **Open**.
* Press ```Ctrl``` + ```P``` and type *custom_settings.dart* and click.
* Press ```Ctrl``` + ```S``` and type *useCfCdn*.
* Change the useCfCdn value from **false** to **true**.
> ex) const bool useCfCdn = true;
* Press ```Ctrl``` + ```S``` and type *cfDomainUrl*.
* Change the cfDomainUrl value from **yourCustomDomainUrl** to the sub domain you connected to your R2 bucket. (like *<n>media.<n>applimode.<n>com* or *<n>cdn.<n>applimode.<n>com* or *<n>content.<n>applimode.<n>com*)
> ex) const String cfDomainUrl = 'media.applimod.com';
* Press ```Ctrl``` + ```S```. (or **File** > **Save**)
* To make sure it works well, follow the [Test drive](#7-test-drive) chapter.


## 15. Configure Youtube image proxy (Optional)
> [!NOTE]
> * In posts containing YouTube links, there are cases where the preview image cannot be retrieved due to CORS issues.
> * You can solve this problem by configuring a proxy worker for YouTube images.
* Open **PowerShell**.
* Run the following commands.
```sh
cd projects
```
```sh
npm create cloudflare@latest yt-thumbnail-worker
```
* Select default values ​​for all questions.
* Open this [page](https://github.com/mycalls/applimode-examples/blob/main/yt_thumbnail_worker/yt_thumbnail_worker.index.ts) and click the **Copy raw file** button (next to the **Raw** button) on the upper-right corner of the file view.
* Open **VSCode**.
* Click **File** (on the top menu of VSCode) and select **Open Folder**.
* Select the **yt-thumbnail-worker** folder and click **Open**.
* Press ```Ctrl``` + ```P``` and type *index.ts* and click.
* Press ```Ctrl``` + ```A``` and press ```Ctrl``` + ```V```.
* To save, press ```Ctrl``` + ```S```.
* Click **View** (on the top menu of VSCode) and select **Terminal**.
* Run the following command.
```
npx wrangler deploy
```
* Go to the [Cloudflare dashboard](https://dash.cloudflare.com/).
* Go to Workers & Pages (on the left sidebar) and in Overview, click **yt-thumbnail-worker**.
* Go to Settings > Triggers > Routes.
* Copy your route.
* Go back to VSCode.
* Click **File** (on the top menu of VSCode) and select **Open Folder** and select your project folder (maybe in the **projects** folder) and click **Open**.
* Press ```Ctrl``` + ```P``` and type *custom_settings.dart* and click.
* Press ```Ctrl``` + ```S``` and type *youtubeImageProxyUrl*.
* Change the youtubeImageProxyUrl value from **yt-thumbnail-worker.jongsukoh80.workers.dev** to the route you copied.
> ex) const String rTwoBaseUrl = 'yt-thumbnail-worker.yourID.workers.dev';
* Press ```Ctrl``` + ```S```. (or **File** > **Save**)


## 16. Configure Youtube video proxy (Optional)
> [!NOTE]
> * When opening a YouTube video in a post, the page where the video is embedded is sent.
> * If not configured, <n>youtube-nocookie.<n>com will be used.
* Open **PowerShell**.
* Run the following commands.
```sh
cd projects
```
```sh
npm create cloudflare@latest yt-iframe-wroker
```
* Select default values ​​for all questions.
* Open this [page](https://github.com/mycalls/applimode-examples/blob/main/yt_iframe_worker/yt_iframe_worker.index.ts) and click the **Copy raw file** button (next to the **Raw** button) on the upper-right corner of the file view.
* Open **VSCode**.
* Click **File** (on the top menu of VSCode) and select **Open Folder**.
* Select the **yt_iframe_worker** folder and click **Open**.
* Press ```Ctrl``` + ```P``` and type *index.ts* and click.
* Press ```Ctrl``` + ```A``` and press ```Ctrl``` + ```V```.
* To save, press ```Ctrl``` + ```S```.
* Click **View** (on the top menu of VSCode) and select **Terminal**.
* Run the following command.
```
npx wrangler deploy
```
* Go to the [Cloudflare dashboard](https://dash.cloudflare.com/).
* Go to Workers & Pages (on the left sidebar) and in Overview, click **yt-iframe-wroker**.
* Go to Settings > Triggers > Routes.
* Copy your route.
* Go back to VSCode.
* Click **File** (on the top menu of VSCode) and select **Open Folder** and select your project folder (maybe in the **projects** folder) and click **Open**.
* Press ```Ctrl``` + ```P``` and type *custom_settings.dart* and click.
* Press ```Ctrl``` + ```S``` and type *youtubeIframeProxyUrl*.
* Paste the route you copied in the youtubeIframeProxyUrl value.
> ex) const String youtubeIframeProxyUrl = 'yt-iframe-worker.yourID.workers.dev';
* Press ```Ctrl``` + ```S```. (or **File** > **Save**)


## 17. Configure push notification (Optional)
> [!NOTE]
> * Firebase has two pricing plans: the Spark Plan (aka the free plan) and the Blaze Plan (aka the pay-as-you-go plan).
> * To use push notifications, you must use Firebase's Blaze Plan.
> * For more details, visit this [page](https://firebase.google.com/docs/projects/billing/firebase-pricing-plans).
> * To use APNs (Apple Push Notification service), you must register for [Apple Developer Program](https://developer.apple.com/programs/). (99 USD)
> * To use APNs, you need a device with macOS installed. and for more details, visit [Configure Applimode for macOS]().
> * Currently Safari on iOS and macOS does not support push notifications. (web app and PWA on iOS and macOS)
* Go to the [Firebase console](https://console.firebase.google.com/).
* Click your project.
* Click **Upgrade** on the bottom of the left sidebar.
* Click **Select plan**.
* Click the settings button on the top of the left sidebar.
* Click **Project settings**.
![fb-project-settings](https://github.com/mycalls/applimode-examples/blob/main/assets/fb-project-settings.png?raw=true)
* Open or go back to VSCode.
* Click **File** (on the top menu of VSCode) and select **Open Folder** and select your project folder (maybe in the **projects** folder) and click **Open**.
* Click **View** (on the top menu of VSCode) and select **Terminal**.
* Run the following commands.
<!--
```
firebase init functions
```
-->
```
cd functions
```
```
npm install
```
```
firebase deploy --only functions
```
```
cd ..
```
* Press ```Ctrl``` + ```P``` and type *index.html* and click.
* Change lines 111 to 125 with the following content.
```html
<!--
<script src="flutter_bootstrap.js" async=""></script>
-->
<!--When using push notification for web app-->
<script src="flutter_bootstrap.js" async="">
  if ('serviceWorker' in navigator) {
    // Service workers are supported. Use them.
    window.addEventListener('load', function () {
      // Register Firebase Messaging service worker.
      navigator.serviceWorker.register('firebase-messaging-sw.js', {
        scope: '/firebase-cloud-messaging-push-scope',
      });
    });
  }
</script>
```
* To save, press ```Ctrl``` + ```S```.
* Press ```Ctrl``` + ```P``` and type *custom_settings.dart* and click.
* Press ```Ctrl``` + ```S``` and type *useFcmMessage*.
* Change the useFcmMessage value from **false** to **true**.
> ex) const bool useFcmMessage = true;
* Go to your web browser with the project settings page open.
* Click Cloud Messaging on the top tap menu and scroll to the bottom.
* Copy Key pair of Web Push certificates.
![fb-cloud-message-web](https://github.com/mycalls/applimode-examples/blob/main/assets/fb-cloud-message-web.png?raw=true)
* Go back to VSCode.
* Paste the Key pair you copied in the fcmVapidKey value.
> ex) const String fcmVapidKey = 'very-long-key-pair';
* Press ```Ctrl``` + ```S```. (or **File** > **Save**)
* Go to your web browser with the project settings page open.
* Click General on the top tap menu and scroll down.
* In the Your apps section, click the Web apps part.
* Copy all content of the **firebaseConfig** part.
```
apiKey: "project-api-key",
authDomain: "your-project.firebaseapp.com",
projectId: "your-project-id",
storageBucket: "your-project.appspot.com",
messagingSenderId: "000000000000",
appId: "0:000000000000:web:0000000000000000000000",
measurementId: "0-0000000000"
```
<!--![fb-general-firebase-config](https://github.com/mycalls/applimode-examples/blob/main/assets/fb-general-firebase-config.png?raw=true)-->
* Go back to VSCode.
* Press ```Ctrl``` + ```P``` and type *firebase-messaging-sw.js* and click.
* Select the content from apiKey to measurementId (maybe lines from 7 to 13) and paste the content you copied.
* Press ```Ctrl``` + ```S```. (or **File** > **Save**)
<!--Todos
iOS APNS 사용하기 위해서
https://firebase.flutter.dev/docs/messaging/apple-integration
custom_settings 에서 useApns 변경
-->


## 18. Use your custom domain (Optional)
* Open your [Firebase console](https://console.firebase.google.com/) in your web browser. 
* Click your project.
* Click **Hosting** (on the left siedbar).
* Scroll down and you can find the **Domains** section.
* Click **Add custom domain**.
<!--todos 내용 추가해줄 것-->
<!--
// 확인하는 동안 Records 항목의 Proxy 꺼줄것
// SSL/TLS 설정 Flexible 에서 Full 로 변경할 것
-->

## 19. Upgrade your project with the new Applimode version
* Delete your existing **applimode**(or **applimode-main**) and **applimode-tool** folders. (If they are in your **projects** folder)
* Open **PowerShell**.
* Run the following commands.
```sh
cd projects;
```
```sh
git clone https://github.com/mycalls/applimode-tool.git
```
```sh
git clone https://github.com/mycalls/applimode.git
```
```sh
flutter upgrade
```
* Close **PowerShell**.
* Open **VSCode**
* Click **File** (on the top menu of VSCode) and select **Open Folder** and select **applimode-tool** (in the **projects** folder) and click **Open**.
* Click **View** (on the top menu of VSCode) and select **Terminal**.
* Modify and run the following command.
```sh
node index.js upgrade --directory-name="your_project_folder_name"
```
> ex) node index.js upgrade --directory-name="my_applimode"
```sh
flutter pub get; dart run flutter_native_splash:create; flutter pub run flutter_launcher_icons; dart run build_runner build -d; flutterfire configure;
```
* Delete your old project folder.


## 20. Configure Cloud Firestore Security Rules 
* If you change the **isInitialSignIn** value to true in the **custom_settings.dart** file, you can enhance security further by modifying your Firestore rules.
* Open this [page](https://github.com/mycalls/applimode-examples/blob/main/fs_authed.firestore.rules) and click the **Copy raw file** button (next to the **Raw** button) on the upper-right corner of the file view.
![copy-raw-file](https://github.com/mycalls/applimode-examples/blob/main/assets/gh-copy-raw-file.png?raw=true)
* Open your [Firebase console](https://console.firebase.google.com/) in your web browser. 
* Click your project.
* Click **Firestore Database** (on the left siedbar).
* Click **Rules** on the top.
* Paste the content you copied.
* Add admin IDs. If you have forgotten how to do this, please follow the [this page](#8-add-administrator).
* Click **Publish**.
* To configure the rules so that only users you have authorized, not just logged-in users, can access the app, follow these instructions.
* Open this [page](https://github.com/mycalls/applimode-examples/blob/main/fs_verified.firestore.rules) and click the **Copy raw file** button (next to the **Raw** button) on the upper-right corner of the file view.
* Paste the content you copied into the Firestore Rules.
* Add admin IDs and verified IDs.
* Click **Publish**.


## 21. Troubleshooting
* ###### If you don't see images or videos in your uploaded post, follow these steps. (CORS issue)
1. Open [Google Cloud console](https://console.cloud.google.com/) in your web browser.
2. Sign up or log in.
3. Select your project on the top left.
4. Click **Activate Cloud Shell** on the top right.
![gcp-console-head](https://github.com/mycalls/applimode-examples/blob/main/assets/gcp-console-head.png?raw=true)
1. Run the following command in the shell on the bottom.
```sh
echo '[{"origin": ["*"],"method": ["GET"],"maxAgeSeconds": 3600}]' > cors.json
```
<!--
> touch cors.json
> nano cors.json
[
  {
    "origin": ["*"],
    "method": ["GET"],
    "maxAgeSeconds": 3600
  }
]
-->
1. Open your [Firebase console](https://console.firebase.google.com/) in your web browser.
2. Click your project.
3. Click **Storage** (on the left siedbar).
4. Click the Copy folder path icon (on the right of the url starting with **gs://**) to copy your cloud storage bucket.
![fb-storage-head](https://github.com/mycalls/applimode-examples/blob/main/assets/fb-storage-head.png?raw=true)
5.  Go back to your Google Cloud console.
6.  Run the following command in the shell on the bottom.
```sh
gsutil cors set cors.json gs://<your-cloud-storage-bucket>
```

* ###### If an error occurs when building with an Android device, follow these steps.
1. Open **VSCode**
2. Click **File** (on the top menu of VSCode) and select **Open Folder** and select your project folder (maybe in the **projects** folder) and click **Open**.
3. Click **View** (on the top menu of VSCode) and select **Terminal**.
4. Run the following commands in order.
```sh
flutter clean
```
```sh
flutter pub cache repair
```
```sh
flutter pub get
```

* ###### If you don't see your Android device in the target device list, follow these steps.
1. Enable Developer options and USB debugging on your android device.
2. To enable Developer options and USB debugging on your android device, refer to [this page](https://developer.android.com/studio/debug/dev-options).
3. Try changing the USB Preferences to Charging or File transfers.
4. Connet again.

* ###### If you cannot upload a post with images or videos attached when using Cloudflare R2, follow these steps.
1. Open **VSCode**
2. Click **File** (on the top menu of VSCode) and select **Open Folder** and select your project folder (maybe in the **projects** folder) and click **Open**.
3. Click **View** (on the top menu of VSCode) and select **Terminal**.
4. Run the following commands in order.
```sh
dart run build_runner clean
```
```sh
dart run build_runner build --delete-conflicting-outputs
```


<!--
// xcode 에서 열기
> open ios/Runner.xcworkspace

// xcode 빌드 에러

// [Xcode] The sandbox is not in sync with the Podfile.lock. Run 'pod install' or update your CocoaPods installation.
* Xcode 종료
* VSCode 에서 프로젝트 열고 터미널 열기
> cd ios
> rm -rf Pods
> rm -rf Podfile.lock
> pod install --repo-update
> cd ..
> open ios/Runner.xcworkspace
* xcode에서 product -> clean 을 해주고 실행
> cd ios; rm -rf Pods; rm -rf Podfile.lock; pod install --repo-update; cd ..; open ios/Runner.xcworkspace;

// error: Unable to load contents of file list
* Xcode 종료
* VSCode 에서 프로젝트 열고 터미널 열기
> cd ios
> pod deintegrate
> pod update
> cd ..
> open ios/Runner.xcworkspace
* xcode에서 product -> clean 을 해주고 실행
> cd ios; pod deintegrate; pod update; cd ..; open ios/Runner.xcworkspace;
-->