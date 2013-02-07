# Git Extensionsでおこなう、ふつうのコミット（とプッシュ）
Git Extensionsでコミットをしてみます。一部画面はまだ現在のリリース版のGit Extensions 2.43とは異なることがあります。

## リポジトリの準備
まずは図に示すようなREADME.mdファイル一個しかないリポジトリを用意してみます。
![commit01.png](https://raw.github.com/hogelog/gitextensions-tips/master/commit/commit01.png)

## 既存のファイルの編集
既にコミットされているファイル、README.mdを編集します。

```markdown:README.md
# Testing

testing repository

## Hello Git!
Hello, Git world!
こんにちはこんにちは！
```

Git Extensionsの画面を開くと「コミット (1)」と表示されており、コミット対象のファイルが
1個存在することがわかります。

![commit02.png](https://raw.github.com/hogelog/gitextensions-tips/master/commit/commit02.png)

## 新規ファイルの追加
「コミットする.txt」「コミットしない.txt」という2個のファイル追加してみます。

```markdown:コミットする.txt
コミットする
```

```markdown:コミットしない.txt
コミットしない
```

Git Extensionsの画面を開くと「コミット (3)」と表示されています。

![commit03.png](https://raw.github.com/hogelog/gitextensions-tips/master/commit/commit03.png)

## コミット
「コミット (3)」というボタンをクリックしてコミット画面を開いてみましょう。

![commit04.png](https://raw.github.com/hogelog/gitextensions-tips/master/commit/commit04.png)

「作業ディレクトリの変更点」という部分に「README.md」「コミットする.txt」「コミットしない.txt」という
3個の変更点が表示されています。
「README.md」は既にコミットしているファイル、「コミットする.txt」「コミットしない.txt」はまだコミット
したことがないファイルなので違うアイコンで表示されています。
ここでは「README.md」「コミットする.txt」の変更点をコミットしてみましょう。

![commit05.png](https://raw.github.com/hogelog/gitextensions-tips/master/commit/commit05.png)

「README.md」「コミットする.txt」を選択して「ステージに追加」をして、右下のコミットメッセージ欄に
コミットの概要を記述して「コミット」でコミットが完了します。

![commit06.png](https://raw.github.com/hogelog/gitextensions-tips/master/commit/commit06.png)

変更がコミットされ、ローカルリポジトリの内容がリモートより1個進んだ状態になりました。
「README.md」「コミットする.txt」はコミットしたので作業ディレクトリ（実際のファイルが存在するディレクトリ）と
リポジトリの内容が同期していますが「コミットしない.txt」は作業ディレクトリ内に存在しますが
リポジトリには反映されていません。
なので「コミット (1)」としてコミット対象としてカウントされています。

## プッシュ
ローカルのリポジトリへのコミットをリモートに反映させてみましょう。

![commit07.png](https://raw.github.com/hogelog/gitextensions-tips/master/commit/commit07.png)

ツールバー内の上矢印ボタンか、メニュー内の「Gitコマンド」の「Push (リモートへ反映)」をクリックします。

![commit08.png](https://raw.github.com/hogelog/gitextensions-tips/master/commit/commit08.png)

「リモート」と「Pushするブランチ」を確認して「Push」を押します。

![commit09.png](https://raw.github.com/hogelog/gitextensions-tips/master/commit/commit09.png)

画面中央のリビジョングラフ内の表示から「master (ローカルのmasterブランチ)」と
「origin/master (リモートリポジトリのmasterブランチ)」が同期されました。


## おまけの.gitignore
「コミットしない.txt」ファイルはコミットしたくないのに「コミット (1)」と表示されたり、
コミットダイアログでステージしないように注意しなければいけなくて、面倒です。
Gitでは.gitignoreファイルというものを用意することで、任意のファイルを監視対象から
外すことができます。

![commit10.png](https://raw.github.com/hogelog/gitextensions-tips/master/commit/commit10.png)

「設定」の「.gitignoreファイルの編集」を選びます。

![commit11.png](https://raw.github.com/hogelog/gitextensions-tips/master/commit/commit11.png)

編集画面に「コミットしない.txt」と入力して「保存」を押すと、変更を保存するか聞かれます。

![commit12.png](https://raw.github.com/hogelog/gitextensions-tips/master/commit/commit12.png)

「はい」と答えて.gitignoreの編集を終了します。

![commit13.png](https://raw.github.com/hogelog/gitextensions-tips/master/commit/commit13.png)

コミットダイアログを開いてみると「コミットしない.txt」がコミット対象から外れています。
このように無視ファイルの設定をうまく共有してみてください。


## .gitignoreしたものを無理やりコミット
.gitignoreしたファイルをコミットすることも実はできてしまいます。

![commit14.png](https://raw.github.com/hogelog/gitextensions-tips/master/commit/commit14.png)

「作業ディレクトリの変更点」から「無視ファイルの表示」にチェックを入れると「コミットしない.txt」
が表示されてしまいます。

![commit15.png](https://raw.github.com/hogelog/gitextensions-tips/master/commit/commit15.png)

そんなに滅多にすることではないかもしれませんが、たまに便利に使える機能かもしれませんね。
