<!-- 
# Theme security issues
 -->

# テーマ・セキュリティ課題

<!-- 
Please do not report security issues with WordPress Core to the themes team. To report an issue with WordPress itself, [follow the directions for reporting security vulnerabilities.](https://make.wordpress.org/core/handbook/testing/reporting-security-vulnerabilities/)
 -->

WordPress コアのセキュリティ課題を、テーマチームに報告しないでください。WordPress 本体に関する課題を報告するには、[セキュリティ脆弱性の報告手順に従ってください](https://make.wordpress.org/core/handbook/testing/reporting-security-vulnerabilities/)。

<!-- 
If you have found a **plugin** with a security issue, please read [Reporting Plugin Security Issues](https://developer.wordpress.org/plugins/wordpress-org/plugin-security/reporting-plugin-security-issues/)
 -->

セキュリティ上の課題を発見した **プラグイン** については、[プラグインのセキュリティ課題の報告](https://developer.wordpress.org/plugins/wordpress-org/plugin-security/reporting-plugin-security-issues/) をご覧ください。

<!-- 
## How to report a theme
 -->

## テーマの報告方法

<!-- 
If you find a theme with a security issue, please **do not** post about it publicly anywhere. Even if there’s a report filed on one of the official security tracking sites, bringing more awareness to the security issue tends to increase people being hacked, and rarely speeds up the fixing.
 -->

セキュリティ上の課題が発見されたテーマについては、いかなる場所でも公には投稿 **しないで** ください。公式のセキュリティ追跡サイトに報告が提出されている場合でも、セキュリティ課題への認知度を高めることは、ハッキング被害の増加につながる傾向があり、修正が早まることはほとんどありません。

<!-- 
To report a theme that is in the WordPress.org theme directory, please go to the theme’s directory listing (For example, [https://wordpress.org/themes/twentytwentythree/](https://wordpress.org/themes/twentytwentythree/)) and use the “**Report this theme**” button in the sidebar, and complete the form.
 -->

WordPress.org テーマ・ディレクトリに掲載されているテーマを報告するには、当該テーマのディレクトリ・ページ (たとえば、[https://wordpress.org/themes/twentytwentythree/](https://wordpress.org/themes/twentytwentythree/)) に移動し、サイドバーにある「**このテーマを報告する**」ボタンをクリックして、フォームに必要事項を入力してください。

<!-- 
[![](https://i0.wp.com/make.wordpress.org/themes/files/2023/09/report_theme.jpg?ssl=1)](https://i0.wp.com/make.wordpress.org/themes/files/2023/09/report_theme.jpg?ssl=1)
 -->

[![](https://i0.wp.com/make.wordpress.org/themes/files/2023/09/report_theme.jpg?ssl=1)](https://i0.wp.com/make.wordpress.org/themes/files/2023/09/report_theme.jpg?ssl=1)

  
  
<!-- 
You can also send reports of security issues to `themes@wordpress.org`. Include the following:
 -->

セキュリティ課題の報告は `themes@wordpress.org` 宛てに送信もできます。以下の情報を含めてください:

<!-- 
*   a clear and concise description of the issue
*   a link to the specific theme
*   whether or not you have validated the security issue yourself
*   **optional** – links to any public disclosures on 3rd party sites
 -->

*   課題の、明確かつ簡潔な説明
*   当該テーマへのリンク
*   セキュリティ課題を自身で検証したか否か
*   **任意** – 第三者サイトにおける、公表情報へのリンク

<!-- 
## For developers
 -->

## 開発者向け

<!-- 
### What to do when you receive a request to update your theme
 -->

### あなたのテーマの更新リクエストを受けた場合の対応方法

<!-- 
If your theme has been reported and the Themes Team decides that action needs to be taken, you will receive an email from the Themes Team with information and instructions.  
– You may be asked to solve an issue within a specific time frame. This depends on the severity of the issue.  
– The Themes Team may need to suspend your theme to prevent new downloads until the issue is resolved.  
**  
You must reply to the email if you have any questions, need more information, or need more time.**
 -->

あなたのテーマが報告され、テーマチームが対応が必要と判断した場合、テーマチームから情報と指示が記載されたメールが届きます。
– 特定の期間内に課題を解決するよう、求められる場合があります。これは課題の深刻度によって異なります。
– 課題が解決されるまで新規ダウンロードを防止するため、テーマチームがあなたのテーマの利用停止措置を取る場合があります。
**質問がある場合、追加情報が必要な場合、または猶予期間が必要な場合は、必ずメールに返信してください。**

<!-- 
Test your theme update carefully and submit it through the [upload form on the theme directory page](https://wordpress.org/themes/upload/).
 -->

あなたのテーマの更新を慎重にテストし、[テーマ・ディレクトリ・ページのアップロード・フォーム](https://wordpress.org/themes/upload/) から提出してください。

<!-- 
[Learn more about how the Themes team works with theme suspensions and delisting](https://make.wordpress.org/themes/handbook/review/theme-suspension/).
 -->

[テーマチームがテーマの一時停止および削除を、どのように扱うかについて、詳しくご覧ください](https://make.wordpress.org/themes/handbook/review/theme-suspension/)。

<!-- 
### Resources
 -->

### リソース

<!-- 
To learn more about theme security, please see the [Security chapter of the common APIs handbook](https://developer.wordpress.org/apis/security/).
 -->

テーマのセキュリティについてさらに詳しく知りたい場合は、[共通 API ハンドブックのセキュリティ章](https://developer.wordpress.org/apis/security/) をご覧ください。

<!-- 
https://developer.wordpress.org/themes/theme-security/common-vulnerabilities
 -->

https://developer.wordpress.org/themes/theme-security/common-vulnerabilities

<!-- 
> [A Guide to Writing Secure Themes – Part 1: Introduction](https://make.wordpress.org/themes/2015/05/19/a-guide-to-writing-secure-themes-part-1-introduction/)
 -->

> [セキュアなテーマ作成ガイド – Part 1: はじめに](https://make.wordpress.org/themes/2015/05/19/a-guide-to-writing-secure-themes-part-1-introduction/)

<!-- 
> [A Guide to Writing Secure Themes – Part 2: Validation](https://make.wordpress.org/themes/2015/05/26/a-guide-to-writing-secure-themes-part-2-validation/)
 -->

> [セキュアなテーマ作成ガイド – Part 2: バリデーション](https://make.wordpress.org/themes/2015/05/26/a-guide-to-writing-secure-themes-part-2-validation/)

<!-- 
> [A Guide to Writing Secure Themes – Part 3: Sanitization](https://make.wordpress.org/themes/2015/06/02/a-guide-to-writing-secure-themes-part-3-sanitization/)
 -->

> [セキュアなテーマ作成ガイド – Part 3: サニタイズ](https://make.wordpress.org/themes/2015/06/02/a-guide-to-writing-secure-themes-part-3-sanitization/)

<!-- 
> [A Guide to Writing Secure Themes – Part 4: Securing Post Meta](https://make.wordpress.org/themes/2015/06/09/a-guide-to-writing-secure-themes-part-4-securing-post-meta/)
 -->

> [セキュアなテーマ作成ガイド – Part 4: 投稿メタデータの保護](https://make.wordpress.org/themes/2015/06/09/a-guide-to-writing-secure-themes-part-4-securing-post-meta/)