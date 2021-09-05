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

## 原文更新方法

1.  `en` ブランチから `en20210905` などのブランチを作成します。
2.  原文を更新します。[wp-handbook-converter](https://github.com/mirucon/wp-handbook-converter)を使うことをオススメします。

`npx wp-handbook-converter themes --handbook theme-handbook --sub-domain developer`

3.  `en` ブランチにプルリクエストします。差分を確認して問題なければマージしてください。

_`en` ブランチには翻訳を含めないでください。_

4. `en` から `main` にプルリクをおくります。差分を確認し、問題なければ、 `main` にマージし、更新完了です。`en`ブランチは削除しないでください。
