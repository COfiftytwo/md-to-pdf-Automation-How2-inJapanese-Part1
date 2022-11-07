# mdファイル→PDF変換を自動化する方法（丁寧解説）

> ～対象者～ <br>
> ・ある程度のGithub・Gitの知識を知っている人。(リポジトリ、READMEファイルの作成やGitBashのコマンド等)<br>
mdファイルからPDFファイルに変換する「md-to-pdf」パッケージをつかって、pushされるたびにPDFの更新を自動化していく。

今回はnpmを使ってインストールしたいが、その前にNodejsがインストールされているかどうかを確認してください。
もしない場合は記事の一番下の引用リンクからインストールしてください。npmはNodejsを入れてない限り使えません…

インストールが完了したら下のコマンドでバージョンを確認する。
```
$ node -v
$ npm -v
```

バージョンの確認も終わったので、次にどのカレントディレクトリ(作業中のフォルダ)内でプログラムを動かすか、またはPDFファイルを作るのかを決めたい。
ちなみにフォルダ内ならどこでもいいですが、今回はGithubのリモートリポジトリ内で動かしたいので、そのリポジトリと連携したローカルリポジトリ内で作業していきます。

cdコマンドでローカルリポジトリに移動してください。移動したらその状態で下の「npmを初期化」コマンドを実行。
```
$ npm init
```

すると下のような結果が変えてくる。
```
This utility will walk you through creating a package.json file.
It only covers the most common items, and tries to guess sensible defaults.
See `npm help json` for definitive documentation on these fields
and exactly what they do.
Use `npm install <pkg> --save` afterwards to install a package and
save it as a dependency in the package.json file.
Press ^C at any time to quit.
package name: (パッケージ名)
```

今回は何もせず、下のような表示が出るまでEnterキーを押す。
最後に「Is this ok? (yes)」とあるので`yes`と打ってEnterキーを押す。
```
This utility will walk you through creating a package.json file.
It only covers the most common items, and tries to guess sensible defaults.
See `npm help json` for definitive documentation on these fields
and exactly what they do.
Use `npm install <pkg> --save` afterwards to install a package and
save it as a dependency in the package.json file.
Press ^C at any time to quit.
package name: (パッケージ名)
version: (1.0.0)
description:
entry point: (index.js)
test command:
git repository:
keywords:
author:
license: (ISC)
About to write to ディレクトリ/package.json:
{
  "name": "contents",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "author": "",
  "license": "ISC"
}
Is this ok? (yes)
```

長くなりましたが下のコマンドで「md-to-pdf」をインストール…（少し時間がかかります）
```
$ npm install md-to-pdf
```

下のような表示が出たらインストール完了。
```
added 180 packages, and audited 181 packages in 26s
15 packages are looking for funding
  run `npm fund` for details
found 0 vulnerabilities
```
また下のようにカレントディレクトリ内にjsonファイルやそれに関係するフォルダが追加されている思うので確認してください。
```
├── .git
├── node_modules
├── package-lock.json
├── package.json
└── README.md
```

次にこのカレントディレクトリにあるREADMEファイルをPDFに変換できるかどうかを下のコマンドで確かめます。
```
$ npx md-to-pdf README.md
```
成功したらしたら下のような表示が出るはず。また下の表示があれば「README.pdf」ができているはず。
```
√ generating PDF from README.md
```

次にGithubで自動化を行う作業に進みたいと思いますが、記事が長くなったので続きは<a href="#">こちら</a>から。


引用：<br>
npmについて：https://www.youtube.com/watch?v=1XADZvNlfy8 <br>
Nodejsのインストール方法について：https://miya-system-works.com/blog/detail/179 <br>
npmのインストールについて（npm initコピペ用）：https://qiita.com/Esfahan/items/067fc366d6a6e7b8690d
