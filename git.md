# gitについて

## git とは
バージョン管理ツールのひとつ
研修で使用したSVNもバージョン管理ツールの一つ

## gitとsvnの違いは
gitはローカルコミットができる。
gitにはリモートリポジトリとローカルリポジトリの2つがあり、リモートリポジトリは複数人で共有するために利用し、ローカルリポジトリは各自の作業に利用する。

## git コマンド
以下に基本的なコマンドがまとまっているので参照<br>
 http://qiita.com/2m1tsu3/items/6d49374230afab251337


## mergeとrebase
### マージ（merge）を利用する方法の特徴

#### 良い点
* 比較的、簡単な操作
* 統合されるブランチのコミットを改変しない
　統合後もブランチの情報を分離して保持（後から確認するのが容易）
#### 悪い点
* （特に、複数人が並行して同じブランチ上で作業をする際には、）多数のブランチの情報が残存したり、マージコミットが散在したりすることで、履歴が複雑化する原因になる


### リベース（rebase）を利用する方法の特徴

#### 良い点
* 不要なコミットが入り込むことがないので、直感的かつシンプルに履歴を保つ
#### 悪い点
* 競合発生時の対処手順が、比較的、複雑
　統合されるブランチのコミットを改変するので注意が必要

### イメージ
https://liginc.co.jp/web/tool/79390


### サンプル実行
1. githubにテスト用のプロジェクトを作成
2. ローカルにテスト用のプロジェクトをclone
```
git clone http:// xxxx.git
```
3. 適当にファイルを作成してadd
```
git add xxx
```
4. コミット
```
git commit -m "initial commit"
```
5. masterにpush
```
git push origin master
```
6. ブランチを2つ作成
```
git checkout -b branch-A
```
7. branch-Aで適当に編集してpush
8. branch-Bで適当に編集してcommit
9. branch-Bで最新ソースを落としてrebase
```
git fetch origin
git rebase master branch-A
```
10. コンフリクトを解消
```
git rebase --contiune
```
