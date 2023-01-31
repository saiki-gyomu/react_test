# MEMO

## 参考URL

[YouTube](https://youtu.be/m9ZjW1md_OQ)

## コマンド

```shell
PS C:\Users\saiki\Documents\GitHub\econ> cd ../
PS C:\Users\saiki\Documents\GitHub> mkdir react_test  // 別にmkdirしなくてよかった汗


    ディレクトリ: C:\Users\saiki\Documents\GitHub


Mode                 LastWriteTime         Length Name


PS C:\Users\saiki\Documents\GitHub> cd .\react_test\
PS C:\Users\saiki\Documents\GitHub\react_test> npx create-react-app test  // プロジェクトディレクトリを生成していく

  - - - - -

Success! Created test at C:\Users\saiki\Documents\GitHub\react_test\test
Inside that directory, you can run several commands:

  npm start
    Starts the development server.

  npm run build
    Bundles the app into static files for production.

  npm test
    Starts the test runner.

  npm run eject
    Removes this tool and copies build dependencies, configuration files
    and scripts into the app directory. If you do this, you can’t go back!

We suggest that you begin by typing:


Happy hacking!
PS C:\Users\saiki\Documents\GitHub\react_test> cd test
PS C:\Users\saiki\Documents\GitHub\react_test\test> code .   // これでvscodeのワークスペースを開くことができる
```

## AWS

検索で「amp」を入力しAWS Amplifyを起動
ウェブアプケーションをホスト をクリック
GitHub をクリックしてgithubを連携
GitHubにアクセスし新規リポジトリを作成
「Quick setup — if you’ve done this kind of thing before」と表示されるので、
「…or create a new repository on the command line」の内容をコピーし、
プロジェクトディレクトリのコマンドラインに貼り付けて実行
コマンドラインに git add . と入力
コマンドラインに git status と入力 
コマンドラインに git commit -m と入力 ブランチがクリーンであると確認

```shell
PS C:\Users\saiki\Documents\GitHub\react_test\test> git add .  // とりあえずのadd
PS C:\Users\saiki\Documents\GitHub\react_test\test> git status  // ブランチがクリーンであると確認
On branch main
Your branch is up to date with 'origin/main'.      

Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        new file:   memo.md

PS C:\Users\saiki\Documents\GitHub\react_test\test> git commit -m "deploy"  // コミット
[main 3b3435d] deploy
 1 file changed, 47 insertions(+)
 create mode 100644 memo.md      
PS C:\Users\saiki\Documents\GitHub\react_test\test> git push  // プッシュ
Enumerating objects: 4, done.
Counting objects: 100% (4/4), done.
Delta compression using up to 4 threads
Compressing objects: 100% (3/3), done.
Writing objects: 100% (3/3), 924 bytes | 924.00 KiB/s, done.
Total 3 (delta 1), reused 0 (delta 0), pack-reused 0        
remote: Resolving deltas: 100% (1/1), completed with 1 local object.
To https://github.com/saiki-gyomu/react_test.git
   3d22d4b..3b3435d  main -> main
PS C:\Users\saiki\Documents\GitHub\react_test\test> 
```

GItHubをリロードしてソースがアップされていることを確認

AWSの「リポジトリブランチの追加」→「最近更新されたリポジトリ」のりろー度ボタンをクリック
先程作成したリポジトリを選択

適当に次へ 次へ 保存してデプロイ ボタンを押下

時間置くとデプロイが完了する

git push すると自動的にデプロイされる

```shell
PS C:\Users\saiki\Documents\GitHub\react_test\test> git add .
warning: LF will be replaced by CRLF in src/App.js.
The file will have its original line endings in your working directory
PS C:\Users\saiki\Documents\GitHub\react_test\test> git commit -m "mod"
[main ab4026c] mod
 2 files changed, 48 insertions(+), 11 deletions(-)
PS C:\Users\saiki\Documents\GitHub\react_test\test> git push
Enumerating objects: 9, done.
Counting objects: 100% (9/9), done.
Delta compression using up to 4 threads
Compressing objects: 100% (5/5), done.
Writing objects: 100% (5/5), 1.95 KiB | 997.00 KiB/s, done.
Total 5 (delta 3), reused 0 (delta 0), pack-reused 0
remote: Resolving deltas: 100% (3/3), completed with 3 local objects.
To https://github.com/saiki-gyomu/react_test.git
   3b3435d..ab4026c  main -> main
```

AWS プロビジョン状態 時間置くとデプロイされる

## 初期化

### CLIでデプロイとかできるようにする

```shell
PS C:\Users\saiki\Documents\GitHub\react_test\test> npm install -g @aws-amplify/cli
C:\Program Files\nodejs\amplify -> C:\Program Files\nodejs\node_modules\@aws-amplify\cli\lib\run.js

> @aws-amplify/cli@10.6.2 postinstall C:\Program Files\nodejs\node_modules\@aws-amplify\cli   
> node ./lib/install.js || echo "failed to install amplify binary"

Downloading release from https://package.cli.amplify.aws/10.6.2/amplify-pkg-win-x64.tgz       
amplify has been installed!
10.6.2
+ @aws-amplify/cli@10.6.2
added 26 packages from 16 contributors in 41.251s
```

（ルートユーザーでサインイン）

```shell
PS C:\Users\saiki\Documents\GitHub\react_test\test> amplify configure
Follow these steps to set up access to your AWS account:

Sign in to your AWS administrator account:
https://console.aws.amazon.com/
Press Enter to continue

Specify the AWS Region
? region:  ap-northeast-1
Specify the username of the new IAM user:
? user name:  testuser
Complete the user creation using the AWS console
https://console.aws.amazon.com/iam/home?region=ap-northeast-1#/users$new?step=final&accessKey&userNames=testuser&permissionType=policies&policies=arn:aws:iam::aws:policy%2FAdministratorAccess-Amplify
Press Enter to continue

Enter the access key of the newly created user:
? accessKeyId:  ********************
? secretAccessKey:  ****************************************
This would update/create the AWS Profile in your local machine
? Profile Name:  testuser2

Successfully set up the new user.
```


Backend environments

バックエンド環境の初期化...（時間かかる）

```shell
PS C:\Users\saiki\Documents\GitHub\react_test\test> amplify init
Note: It is recommended to run this command from the root of your app directory
? Enter a name for the project test
The following configuration will be applied:

Project information
| Name: test
| Environment: dev
| Default editor: Visual Studio Code
| App type: javascript
| Javascript framework: react
| Source Directory Path: src
| Distribution Directory Path: build
| Build Command: npm.cmd run-script build
| Start Command: npm.cmd run-script start

? Initialize the project with the above configuration? Yes
Using default provider  awscloudformation
? Select the authentication method you want to use: AWS profile

For more information on AWS Profiles, see:
https://docs.aws.amazon.com/cli/latest/userguide/cli-configure-profiles.html

? Please choose the profile you want to use testuser2
Adding backend environment dev to AWS Amplify app: d1sps4tczosid7

Deployment completed.
Deployed root stack test [ ======================================== ] 4/4
        amplify-test-dev-162841        AWS::CloudFormation::Stack     CREATE_COMPLETE         
        UnauthRole                     AWS::IAM::Role                 CREATE_COMPLETE         
        AuthRole                       AWS::IAM::Role                 CREATE_COMPLETE         
        DeploymentBucket               AWS::S3::Bucket                CREATE_COMPLETE         

√ Help improve Amplify CLI by sharing non sensitive configurations on failures (y/N) · no
Deployment state saved successfully.
√ Initialized provider successfully.
✅ Initialized your environment successfully.

Your project has been successfully initialized and connected to the cloud!

Some next steps:
"amplify status" will show you what you've added already and if it's locally configured or deployed
"amplify add <category>" will allow you to add features like user login or a backend API      
"amplify push" will build all your local backend resources and provision it in the cloud      
"amplify console" to open the Amplify Console and view your project status
"amplify publish" will build all your local backend and frontend resources (if you have hosting category added) and provision it in the cloud

Pro tip:
Try "amplify add api" to create a backend API and then "amplify push" to deploy everything    
```

※ctrl + l でコマンドラインの現在の行を一番上にできる


## 認証をつける

```shell
PS C:\Users\saiki\Documents\GitHub\react_test\test> npm i aws-amplify @aws-amplify/ui-react
npm WARN deprecated querystring@0.2.0: The querystring API is considered Legacy. new code should use the URLSearchParams API instead.
npm WARN deprecated uuid@3.4.0: Please upgrade  to version 7 or higher.  Older versions may use Math.random() in certain circumstances, which is known to be problematic.  See https://v8.dev/blog/math-random for details.

> maplibre-gl@2.1.9 postinstall C:\Users\saiki\Documents\GitHub\react_test\test\node_modules\maplibre-gl
> node ./postinstall.js

npm WARN @apideck/better-ajv-errors@0.3.6 requires a peer of ajv@>=8 but none is installed. You must install peer dependencies yourself.
npm WARN fork-ts-checker-webpack-plugin@6.5.2 requires a peer of typescript@>= 2.7 but none is installed. You must install peer dependencies yourself.
npm WARN tsutils@3.21.0 requires a peer of typescript@>=2.8.0 || >= 3.2.0-dev || >= 3.3.0-dev 
|| >= 3.4.0-dev || >= 3.5.0-dev || >= 3.6.0-dev || >= 3.6.0-beta || >= 3.7.0-dev || >= 3.7.0-beta but none is installed. You must install peer dependencies yourself.
npm WARN react-native-get-random-values@1.8.0 requires a peer of react-native@>=0.56 but none 
is installed. You must install peer dependencies yourself.
npm WARN optional SKIPPING OPTIONAL DEPENDENCY: fsevents@2.3.2 (node_modules\fsevents):       
npm WARN notsup SKIPPING OPTIONAL DEPENDENCY: Unsupported platform for fsevents@2.3.2: wanted 
{"os":"darwin","arch":"any"} (current: {"os":"win32","arch":"x64"})

+ aws-amplify@5.0.12
+ @aws-amplify/ui-react@4.3.5
added 731 packages from 146 contributors and audited 2215 packages in 176.693s

254 packages are looking for funding
  run `npm fund` for details        

found 1 high severity vulnerability
  run `npm audit fix` to fix them, or `npm audit` for details
```

```shell
PS C:\Users\saiki\Documents\GitHub\react_test\test> amplify add auth
Using service: Cognito, provided by: awscloudformation

 The current configured provider is Amazon Cognito. 

 Do you want to use the default authentication and security configuration? Default configuration
 Warning: you will not be able to edit these selections. 
 How do you want users to be able to sign in? Username   
 Do you want to configure advanced settings? No, I am done.
✅ Successfully added auth resource testab5c2d55 locally

✅ Some next steps:
"amplify push" will build all your local backend resources and provision it in the cloud      
"amplify publish" will build all your local backend and frontend resources (if you have hosting category added) and provision it in the cloud
```

```shell

```

C:\Users\saiki\Documents\GitHub\react_test\test\src\App.jsを編集

編集前

```js
import logo from './logo.svg';
import './App.css';

function App() {
  return (
    <div className="App">
      <header className="App-header">
        <img src={logo} className="App-logo" alt="logo" />
        <p>
          Edit <code>src/App.js</code> and save to reload.
        </p>
        <a
          className="App-link"
          href="https://reactjs.org"
          target="_blank"
          rel="noopener noreferrer"
        >
          Learn React
        </a>
      </header>
    </div>
  );
}

export default App;
```

編集後

```js
import logo from './logo.svg';
import './App.css';
import { Amplify } from 'aws-amplify';
import { withAuthenticator } from '@aws-amplify/ui-react';
import "@aws-amplify/ui-react/styles.css";

import awsExports from "./aws-exports";
Amplify.configure(awsExports);

function App({signOut, user}) {
  return (
    <div className="App">
      <header className="App-header">
        <img src={logo} className="App-logo" alt="logo" />
        <h2>Hello</h2>
        {user ? (
          <>
            <h3>私は権限を持っています:{user.username}</h3>
            <button onClick={signOut}>サインアウト</button>
          </>
        ) : (
          <h3>権限がありません</h3>
        )}
      </header>
    </div>
  );
}

export default withAuthenticator(App);
```

認証アカウント作成しサインイン実行

