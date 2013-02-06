# Git Extensionsでおこなう、こわくないマージ
Git Extensionsでマージ作業をしてみます。一部画面はまだ現在のリリース版のGit Extensions 2.43とは異なることがあります。

## まっすぐなリポジトリの準備
まずは図に示すような、README.mdファイル一個、masterブランチ一個しかないまっすぐなリポジトリを準備してみます。
![merge01.png](https://raw.github.com/hogelog/gitextensions-tips/master/merge/merge01.png)

## testブランチの作成
masterブランチからtestブランチを作成します。
![merge02.png](https://raw.github.com/hogelog/gitextensions-tips/master/merge/merge02.png)

まだ何もコミットしていないのでmasterブランチとtestブランチの内容は同一です。
![merge03.png](https://raw.github.com/hogelog/gitextensions-tips/master/merge/merge03.png)

## testブランチへのコミット
README.mdを以下のように編集してtestブランチにコミットします。

```markdown:README.md
# Testing

testing repository

## Hello Git!
Hello, Git world!
```

## masterブランチへのコミット
masterブランチをチェックアウトします。
![merge05.png](https://raw.github.com/hogelog/gitextensions-tips/master/merge/merge05.png)

README.mdを以下のように編集してmasterブランチにコミットします。

```markdown:README.md
# Testing

testing repository

## Hello Git
Hello, git world!
```

これでmasterブランチとtestブランチで内容が別れてしまいました。
![merge06.png](https://raw.github.com/hogelog/gitextensions-tips/master/merge/merge06.png)

## testブランチのマージ
現在いるmasterブランチに、testブランチをマージします。
![merge07.png](https://raw.github.com/hogelog/gitextensions-tips/master/merge/merge07.png)

現在のブランチ: master、マージ対象: testとしてマージします。
![merge08.png](https://raw.github.com/hogelog/gitextensions-tips/master/merge/merge08.png)

どちらのブランチもREADME.mdを変更しているため、競合 (CONFLICT) が発生してしまいましたが落ち着いて「OK」を押しましょう。
![merge09.png](https://raw.github.com/hogelog/gitextensions-tips/master/merge/merge09.png)

「マージ競合の解決をしますか？」と聞かれます。「はい」を押すとKDiff3を使ったマージツールが起動するのですがいまいち使いやすくないので、ここは「いいえ」を押してください。
![merge09-2.png](https://raw.github.com/hogelog/gitextensions-tips/master/merge/merge09-2.png)

## マージ作業
現在マージ作業中である警告がダイアログ右下に表示されているはずです。ここからエディタなどを用いて手作業でマージをおこなっていきましょう。
![merge10.png](https://raw.github.com/hogelog/gitextensions-tips/master/merge/merge10.png)

README.mdが以下のような状態になっています。

```markdown:README.md
# Testing

testing repository

<<<<<<< HEAD
## Hello Git
Hello, git world!
=======
## Hello Git!
Hello, Git world!
>>>>>>> test
```

これは``<<<<<<< HEAD``と``=======``に囲まれる部分がHEAD (現在のブランチ = master) の変更、
``=======``と``>>>>>>> test``に囲まれる部分がtestブランチの変更であるという意味です。

両方の変更を取り込み以下のように編集します。

```markdown:README.md
# Testing

testing repository

## Hello Git
Hello, Git world!
```

いつもどおりにコミットしてみましょう。
![merge15.png](https://raw.github.com/hogelog/gitextensions-tips/master/merge/merge15.png)

無事testブランチの内容がmasterブランチにマージされました。
![merge16.png](https://raw.github.com/hogelog/gitextensions-tips/master/merge/merge16.png)

コミットのグラフも「ここでマージしたよ」というのがわかりやすい表示になっていて、嬉しいですね。

## Tips
コミット画面から「ファイルの履歴」などを選ぶと、そのファイルに関連する変更を確認できてマージの参考になります。是非役立たせてください。
![merge13.png](https://raw.github.com/hogelog/gitextensions-tips/master/merge/merge13.png)
選択して、
![merge14.png](https://raw.github.com/hogelog/gitextensions-tips/master/merge/merge14.png)
各コミットの変更を確認したり。
