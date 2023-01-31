# MEMO

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


