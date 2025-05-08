# Theme Handbook

こちらは [Theme Handbook](https://developer.wordpress.org/themes/) の翻訳用リポジトリです。

theme ディレクトリ内にある英文を翻訳していきます。

ブラウザ上で翻訳したいmdファイルをクリックし、鉛筆マークの「Edit this file」をクリックすることでブラウザ上でも更新（プルリクエスト）できます。

## 翻訳の始め方

1. 翻訳したいページに該当する原文に該当するURLを明記して翻訳を開始する旨のIssueを立ててください。
2. 翻訳開始の前に原文が更新されてないか目視でざっくりで良いので確認してから作業を始めていただけると助かります。

## 翻訳方法

__原文例：__

```
# Welcome
```

__手順：__

1.  __原文をコメントアウトします。__
    ```
    <!--
    # Welcome
     -->
    ```
    _`<!--` の後ろと、`-->` の前には半角スペースと改行を入れてください。翻訳の最小単位 (コメントアウトの単位) は段落 (空行から空行まで) でお願いします。_
2.  __コメントアウトした原文の下に翻訳を追加します。__
    ```
    <!--
    # Welcome
     -->
    # ようこそ
    ```
3.  __`main` ブランチにプルリクエストします。__
  * プルリクエストを送る際の説明欄に、"fixes #[Issue 番号]" (`[]` は不要) というフォーマットで作成した Issue を記述すると、プルリクエストがマージされる際に自動で Issue が閉じられるので便利です。

GitHub が初めての方も [翻訳開始から提案までの流れ](https://github.com/jawordpressorg/community-handbook/wiki/%E7%BF%BB%E8%A8%B3%E9%96%8B%E5%A7%8B%E3%81%8B%E3%82%89%E6%8F%90%E6%A1%88%E3%81%BE%E3%81%A7%E3%81%AE%E6%B5%81%E3%82%8C) を参考に、是非ご参加ください。

## 翻訳のルール

翻訳を始める前に、[WordPress 翻訳ハンドブック](https://ja.wordpress.org/team/handbook/translation/) に目をお通しください。

翻訳の表記ゆれなど、その他迷った時は Issue を立てるか、 [WordPress 日本語 Slack](http://bit.ly/join-wordslack) の docs チャンネルまでご相談ください。

## 原文の更新・反映方法

### en ブランチでの原文更新

**注意: `en` ブランチには、日本語訳は含めないでください。**

まずは `en` ブランチで、[wp-handbook-converter](https://github.com/mirucon/wp-handbook-converter) を使用し、原文を更新します。

1. `en` ブランチをチェックアウトします。

    ```
    git fetch origin en
    git checkout en
    ```

2. [wp-handbook-converter](https://github.com/mirucon/wp-handbook-converter)を使って原文を更新します。また `--regenerate` オプションで、出力先ディレクトリを一度削除するようにします。
    ```
    npx wp-handbook-converter --handbook theme-handbook --sub-domain developer --output-dir theme --regenerate
    ```

3. `git diff` コマンドなどを使って、原文の差分を確認します。

4. 問題がなければ、`en` ブランチで原文の更新を commit し、リモートブランチに push します。

    ```
    git add .
    git commit -m "原文を更新"
    git push origin en
    ```

### 日本語化ファイルの反映

日本語化済みの情報を最新の原文に反映させます。

1. `en` ブランチから、作業用のブランチ (例: update-document) をチェックアウトします。
    ```
    git checkout -b update-document
    ```

2. `main` ブランチにある、日本語化済の情報を取り込みます。
    ```
    git merge main
    ```

3. コンフリクトが発生した場合は解消します。コンフリクトが発生しているファイルは、`git status` コマンドを実行した時に、`Unmerged paths` として表示されています。または、「`<<<<<<< HEAD`」などのコマンドでコンフリクトが発生している箇所を探します。

4. 全てのコンフリクトを解消したら、commit し、リモートブランチに push します。
    ```
    git add .
    git commit -m "原文を更新"
    git push origin update-document
    ```

### プルリクエストの作成

1. 最新の原文、および日本語化済の情報を含んだブランチ (例: `update-document`) から、プルリクエストを作成します。

2. 差分を確認し、問題なければ `main` ブランチにマージします。

**注意: 作業用のリモートブランチ (例: `update-document`)は削除しても構いませんが、`en` ブランチは削除しないでください。**

