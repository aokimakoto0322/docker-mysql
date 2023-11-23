# mysql 環境構築

# 導入するソフト
 - visual studio code  
 (ソースコードを編集するソフトです。特に編集はしないですが、あるにこしたことはないのでインストールする）
 - git  
   (dropboxなどファイル共有ソフトなどありますが、それのソースコードに特化した共有ソフトです。　環境構築のためのソースをダウンロードするのに使います）
 - docker desktop  
  (仮想の環境を構築できるソフトです。1コマンドで構築＆本番環境と同様の環境構築できるので便利です。）
 - 

# visual studio codeのインストール

1. 下記URLより、visual studio codeをダウンロード  
https://code.visualstudio.com/download

2. ダウンロードしたファイルを実行し、インストール  
※すべて「はい」でインストールしてOKです

3. インストール完了し、この画面が出ればとりあえず完了

# gitのインストール

1. 下記URLより、「download」gitのダウンロード  
https://gitforwindows.org/

2. ダウンロードしたファイルを実行し、インストール  
※すべて「Next」でインストールしてOKです

## gitがインストールできたか確認
1. Visual Studio Codeを開く
2. 上の「terminal」→「New Terminal」を押し、Terminalを開く
3. Terminalを開いたら、下記コマンドを入力  
`git`
4. 下記のように、グダグダ出てきたら成功  
※うまくいかない時は、visual studio codeを一回閉じて、再度開いたのちに行うとうまくいくかも
```
usage: git [-v | --version] [-h | --help] [-C <path>] [-c <name>=<value>]     
           [--exec-path[=<path>]] [--html-path] [--man-path] [--info-path]    
           [-p | --paginate | -P | --no-pager] [--no-replace-objects] [--bare]
           [--git-dir=<path>] [--work-tree=<path>] [--namespace=<name>]       
           [--config-env=<name>=<envvar>] <command> [<args>]

These are common Git commands used in various situations:

start a working area (see also: git help tutorial)
   clone     Clone a repository into a new directory
   init      Create an empty Git repository or reinitialize an existing one   

work on the current change (see also: git help everyday)
   add       Add file contents to the index
   mv        Move or rename a file, a directory, or a symlink
   restore   Restore working tree files
   rm        Remove files from the working tree and from the index

examine the history and state (see also: git help revisions)
   bisect    Use binary search to find the commit that introduced a bug
   diff      Show changes between commits, commit and working tree, etc
   grep      Print lines matching a pattern
   log       Show commit logs
   show      Show various types of objects
   status    Show the working tree status

grow, mark and tweak your common history
   branch    List, create, or delete branches
   commit    Record changes to the repository
   merge     Join two or more development histories together
   rebase    Reapply commits on top of another base tip
   reset     Reset current HEAD to the specified state
   switch    Switch branches
   tag       Create, list, delete or verify a tag object signed with GPG

collaborate (see also: git help workflows)
   fetch     Download objects and refs from another repository
   pull      Fetch from and integrate with another repository or a local branch
   push      Update remote refs along with associated objects

'git help -a' and 'git help -g' list available subcommands and some
concept guides. See 'git help <command>' or 'git help <concept>'
to read about a specific subcommand or concept.
See 'git help git' for an overview of the system.
```

# docker desktopのインストール
※基本はこのページをもとにインストールを進めて行きます  
https://chigusa-web.com/blog/windows%E3%81%ABdocker%E3%82%92%E3%82%A4%E3%83%B3%E3%82%B9%E3%83%88%E3%83%BC%E3%83%AB%E3%81%97%E3%81%A6python%E7%92%B0%E5%A2%83%E3%82%92%E6%A7%8B%E7%AF%89/

1. 下記URLより、「Docker Desktop for Windows」を押してdocker desktopをダウンロード  
https://docs.docker.com/desktop/install/windows-install/  

2. ダウンロードしたファイルを実行し、インストール  
※全部「OK」でインストールしてOKです

3. ダウンロード完了したら、「Close and Restart」で再起動します