<!-- 
# Updating Your Theme
 -->

# あなたのテーマのアップデート

<!-- 
There are two ways to update your theme, by uploading a Zip file or using subversion (SVN).
 -->

あなたのテーマをアップデートするには、Zip ファイルをアップロードする方法と、Subversion (SVN) を使用する方法の2通りがあります。

<!-- 
## Uploading a Zip file
 -->

## Zip ファイルのアップロード

<!-- 
While your theme is in the queue and waiting for review, you can update your theme by [uploading a Zip file](https://wordpress.org/themes/getting-started/). Just as you initially uploaded. Be sure to update the version number on style.css before uploading.
 -->

あなたのテーマが審査待ちのキューに入っている間、[Zip ファイルのアップロード](https://wordpress.org/themes/getting-started/) によってあなたのテーマをアップデートできます。最初にアップロードしたときと同じように。アップロード前に style.css のバージョン番号を更新するのを忘れないでください。

<!-- 
Updating the version number will NOT change the queue position of your theme while waiting for the review.
 -->

審査待ちの間、バージョン番号を更新しても、あなたのテーマの待機列の順番は変化「しません」。

<!-- 
If you already have your themes in the repository, you can either update by uploading a Zip file or via SVN.
 -->

リポジトリにあなたのテーマがすでに存在する場合、Zip ファイルをアップロードするか、SVN 経由でアップデートできます。

<!-- 
## Subversion GUI clients
 -->

## Subversion GUI クライアント

<!-- 
Several GUI clients are available for Windows users. [TortoiseSVN](https://tortoisesvn.net/) is one of the popular Free clients. [SmartSVN](https://www.smartsvn.com/) is a paid application that works on Windows, Linux, and macOS.
 -->

Windows ユーザー向けにいくつかの GUI クライアントが利用可能です。[TortoiseSVN](https://tortoisesvn.net/) は人気の無料クライアントの一つです。[SmartSVN](https://www.smartsvn.com/) は Windows、Linux、macOS で動作する有料アプリケーションです。

<!-- 
For Mac users, SVN helps streamline the automation process, including removing `*.DS_Store*` and `*__MACOSX*` hidden files and folders that often trigger the theme check errors.
 -->

Mac ユーザーにとって、SVN は自動化プロセスを効率化するのに役立ちます。これには、テーマチェック・エラーの原因となることが多い隠しファイルや隠しフォルダーである `*.DS_Store*` や `*__MACOSX*` の削除も含まれます。

<!-- 
### Important notes:
 -->

### 重要な注意事項:

<!-- 
**(1) Directory naming guidelines**
 -->

**(1) ディレクトリ命名ガイドライン**

<!-- 
The theme author must create a new directory before uploading the theme. It is important to name the new directory with the new version number. For example, if the current theme is version `*1.0.1*`, the name for the new directory must be *`1.0.2`*.
 -->

テーマ作者は、テーマをアップロードする前に新規ディレクトリを作成する必要があります。新しいバージョン番号で新規ディレクトリを命名することが重要です。たとえば、現在のテーマがバージョン *`1.0.1`* の場合、新規ディレクトリ名は *`1.0.2`* である必要があります。

<!-- 
**(2) Version numbering**
 -->

**(2) バージョン番号付け**

<!-- 
Version numbering must follow a standard version naming convention. New version must be higher than the current version. For example, if your current theme is `*1.2.3*`, the new version must be `*1.2.4*`.
 -->

バージョン番号は、標準のバージョン命名規則に従う必要があります。新規バージョンは、現行バージョンよりも大きい番号にする必要があります。たとえば、現在のテーマが *`1.2.3`* の場合、新規バージョンは *`1.2.4`* にする必要があります。

<!-- 
**(3) SVN is not a development tool**
 -->

**(3) SVN は開発ツールではない**

<!-- 
Unlike Github, SVN is not a development tool. You should upload your theme only when you are ready to release a new version. Once you commit, the changes cannot be overwritten. If you find a mistake, even a small typo, there is no way to make changes. The only way to make corrections is to create another directory with a newer version number and upload it again.
 -->

GitHub とは異なり、SVN は開発ツールではありません。あなたのテーマは、新バージョンをリリースする準備が整ったときのみアップロードすべきです。一度コミットすると、変更は上書きできません。誤りを見つけた場合、たとえ小さな typo であっても、変更を加える方法はありません。修正する唯一の方法は、別のディレクトリを新しいバージョン番号で作成し、再度アップロードすることです。

<!-- 
### Uploading your themes using SVN on MacOS
 -->

### macOS で SVN を使用した、あなたのテーマのアップロード

<!-- 
**What you will need**
 -->

**必要なものは以下の通りです。**

<!-- 
*   MacOS
*   VS code
*   SVN extension for VS code
 -->

*   macOS
*   VS code
*   VS code 用 SVN 拡張機能

<!-- 
To check whether you have svn installed, type `svn --version` in the terminal.
 -->

svn がインストールされているかどうかを確認するには、terminal で `svn --version` と入力してください。

<!-- 
(1) Create a copy of the repository on your local machine. Replace */NameOfYourTheme/* with your theme name. `*svn co https://themes.svn.wordpress.org/NameOfYourTheme/*`
 -->

(1) リポジトリのコピーをローカルマシンに作成します。*/NameOfYourTheme/* をあなたのテーマ名に置き換えてください。`*svn co https://themes.svn.wordpress.org/NameOfYourTheme/*`

<!-- 
For example, if your theme name is Hello World,  
use `*svn co https://themes.svn.wordpress.org/hello-world/*`
 -->

たとえば、あなたのテーマ名が「Hello World」の場合、`*svn co https://themes.svn.wordpress.org/hello-world/*` を使用します。

<!-- 
**Tips:** If you are not sure about the exact name of your theme (e.g. hyphen, underscore), you can find it at [this link](https://themes.svn.wordpress.org/).
 -->

**ヒント:** あなたのテーマの正確な名前 (例: ハイフン、アンダースコア) がわからない場合は、[このリンク](https://themes.svn.wordpress.org/) で確認できます。

<!-- 
(2) The next step is to create a new directory and copy all theme files, including the history from the current version of the theme. In the example below, we are creating a new directory 1.0.2, and copying all files from the version 1.0.1. `*svn cp 1.0.1 1.0.2*`
 -->

(2) 次のステップは、新規ディレクトリを作成し、現在のテーマバージョンから、履歴を含むすべてのテーマファイルをコピーすることです。以下の例では、新規ディレクトリ「1.0.2」を作成し、バージョン「1.0.1」からすべてのファイルをコピーしています。`*svn cp 1.0.1 1.0.2*`

<!-- 
(3) Make changes to your theme.
 -->

(3) あなたのテーマを変更してください。

<!-- 
**Note:** Make sure to update the version number on style.css, and the changelog on readme.txt
 -->

**注:** style.css のバージョン番号と、readme.txt の changelog を必ず更新してください。

<!-- 
(4) Remove *.DS\_Store* hidden file. `*find . -name ".DS_Store" -print -delete*`
 -->

(4) 隠しファイル *.DS\_Store* を削除します。`*find . -name ".DS_Store" -print -delete*`

<!-- 
(5) Next, remove `*__MACOSX*` folder. `*rm -R __MACOSX*`
 -->

(5) 次に、`*__MACOSX*` フォルダーを削除します。`*rm -R __MACOSX*`

<!-- 
(6) Finally, you are ready to commit.
 -->

(6) 漸く、コミットする準備が整いました。

<!-- 
`*svn commit -m “Fix typo on readme.txt”*`
 -->

`*svn commit -m "readme.txt の typo を修正"*`

<!-- 
**Note:** Once you commit, there is no way to change or modify what you just committed. If you find a mistake, Repeat the process from step 2.
 -->

**注:** いったんコミットすると、コミットした内容を変更または修正する方法はありません。間違いを見つけた場合は、手順2からプロセスを繰り返してください。

<!-- 
### What to expect next
 -->

### 次に期待されること

<!-- 
Once you successfully upload the new update, you will receive a confirmation email from WordPress.org. It may take some time to reflect on the WordPress.org directory.
 -->

新しいアップデートを正常にアップロードすると、WordPress.org から確認メールが届きます。WordPress.org ディレクトリに反映されるまで、少し時間がかかる場合があります。