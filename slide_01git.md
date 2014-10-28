# Gitのすゝめ

---

# はじめに

--

## 今日話すこと

* Gitとは
* 単語の説明
* つかいかた（基礎編）

--

## 参考

* サルでもわかるGit入門
 - どこぞの企業のページ
 - Gitを学ぶにはこれ以上ないくらい分かりやすい
* Qiita
 - 最近流行りのプログラマ用ブログサイト
 - GitHubと標準で連携しているので利用者はだいたいGitに詳しい
 - そのためGit関連の記事も多い

---

# Gitとは

--

## 特徴(1/2)

* 分散型バージョン管理システム
* 2005年開発開始
 - Linuxカーネルの開発用
 - Gitが導入される前は商用ツールを利用していた
 - 大勢が多数のパッチを次々と提供できる環境にするため開発された

--

## 特徴(2/2)

* リモートリポジトリを主、ローカルリポジトリを副とする運用がメイン
 - リモートには常に最新のソース(運開後などは完成品)
 - ローカルにはメインから枝分かれした各人の途中経過
* コミット単位で管理
 - それぞれのブランチの現在の状態は<span style="color:red">どこのコミットを指しているか</span>
 - タグもコミット単位でつけることができる


---

# 単語の説明

--

## ローカルでのお話(1/2)

* *コミット*：各時点のファイルの状態をリポジトリに記憶させること
 - SVNではコミット = サーバへの反映
 - Gitではコミット ≠ サーバへの反映
 - あくまでローカルにてファイルの世代管理をさせる
 - コメントをつけることができる(このコミットは何を変更したからなのか)
 - コメントは必須

[http://www.backlog.jp/git-guide/img/post/intro/capture_intro1_3_1.png](http://www.backlog.jp/git-guide/img/post/intro/capture_intro1_3_1.png)

--

## ローカルでのお話(2/2)

* *ワークツリー*：現在操作してるディレクトリ
 - ブランチの切り替えなどでその都度更新されていく
* *インデックス*：コミットする内容を一次保存して置く空間
 - コミットするものを選ぶことが出来る
 - これがあると一度に色々と変更しても変更した内容ごとにコミット出来る

[http://www.backlog.jp/git-guide/img/post/intro/capture_intro1_4_1.png](http://www.backlog.jp/git-guide/img/post/intro/capture_intro1_4_1.png)

--

## リモートとの連携(1/2)

* *クローン*：リモートリポジトリからローカルリポジトリを作成する
 - SVNでいうチェックアウトに感覚的には近い
 - Gitのチェックアウトは意味が違うので注意

--

## リモートとの連携(2/2)

* *プッシュ*：ローカルのコミット履歴 → リモート
* *プル*：リモートのコミット履歴 → ローカル


[http://www.backlog.jp/git-guide/img/post/intro/capture_intro3_1_1.png](http://www.backlog.jp/git-guide/img/post/intro/capture_intro3_1_1.png)

[http://www.backlog.jp/git-guide/img/post/intro/capture_intro3_3_1.png](http://www.backlog.jp/git-guide/img/post/intro/capture_intro3_3_1.png)

--

## ブランチ関連

* *ブランチ*：履歴の流れを記憶する道筋のこと
 - 枝
 - Gitは特にこの機能に秀でている
 - 作成や切り替えが早い
 - masterブランチと呼ばれるものが必ず存在する
* *チェックアウト*：作業するブランチを切り替えること
 - チェックアウトするとワーキングツリーの状態が更新される
* *マージ*：ブランチに別のブランチを統合すること
 - 基本的にはmasterに他の開発中のブランチをマージする

--

[http://www.backlog.jp/git-guide/img/post/stepup/capture_stepup1_1_2.png](http://www.backlog.jp/git-guide/img/post/stepup/capture_stepup1_1_2.png)


--

## 単語はまだまだあるけど<br>今回はここまで

---

# つかいかた<br>（基礎編）

--

## コミット

1. ファイルを作成・更新
2. インデックスに追加
3. コミット

```
$ touch example.txt
$ git add example.txt    // git add -AでもOK
$ git commit -m "テストです"
```

--

## コミット<br>(リモートに反映する場合)

1. ファイルを作成・更新
2. インデックスに追加
3. コミット
4. プッシュ

```
$ touch example.txt
$ git add example.txt    // git add -AでもOK
$ git commit -m "テストです"
$ git remote add origin foo@hoge.com:bar.git
$ git push -u origin master
```

--

## リモートから<br>ローカルを更新する

次のどちらか

* プル

* フェッチ → マージ



--

* 基本的な使い方はこの程度
* だがブランチが絡んでくると気をつけることや操作量が増える
* ブランチに関しては次回

