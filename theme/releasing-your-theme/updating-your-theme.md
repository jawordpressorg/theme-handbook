# Updating Your Theme

There are two ways to update your theme, by uploading a Zip file or using subversion (SVN).

## Uploading a Zip file

While your theme is in the queue and waiting for review, you can update your theme by [uploading a Zip file](https://wordpress.org/themes/getting-started/). Just as you initially uploaded. Be sure to update the version number on style.css before uploading.

Updating the version number will NOT change the queue position of your theme while waiting for the review.

If you already have your themes in the repository, you can either update by uploading a Zip file or via SVN.

## Subversion GUI clients

Several GUI clients are available for Windows users. [TortoiseSVN](https://tortoisesvn.net/) is one of the popular Free clients. [SmartSVN](https://www.smartsvn.com/) is a paid application that works on Windows, Linux, and macOS.

For Mac users, SVN helps streamline the automation process, including removing `*.DS_Store*` and `*__MACOSX*` hidden files and folders that often trigger the theme check errors.

### Important notes:

**(1) Directory naming guidelines**

The theme author must create a new directory before uploading the theme. It is important to name the new directory with the new version number. For example, if the current theme is version `*1.0.1*`, the name for the new directory must be *`1.0.2`*.

**(2) Version numbering**

Version numbering must follow a standard version naming convention. New version must be higher than the current version. For example, if your current theme is `*1.2.3*`, the new version must be `*1.2.4*`.

**(3) SVN is not a development tool**

Unlike Github, SVN is not a development tool. You should upload your theme only when you are ready to release a new version. Once you commit, the changes cannot be overwritten. If you find a mistake, even a small typo, there is no way to make changes. The only way to make corrections is to create another directory with a newer version number and upload it again.

### Uploading your themes using SVN on MacOS

**What you will need**

*   MacOS
*   VS code
*   SVN extension for VS code

To check whether you have svn installed, type `svn --version` in the terminal.

(1) Create a copy of the repository on your local machine. Replace */NameOfYourTheme/* with your theme name. `*svn co https://themes.svn.wordpress.org/NameOfYourTheme/*`

For example, if your theme name is Hello World,  
use `*svn co https://themes.svn.wordpress.org/hello-world/*`

**Tips:** If you are not sure about the exact name of your theme (e.g. hyphen, underscore), you can find it at [this link](https://themes.svn.wordpress.org/).

(2) The next step is to create a new directory and copy all theme files, including the history from the current version of the theme. In the example below, we are creating a new directory 1.0.2, and copying all files from the version 1.0.1. `*svn cp 1.0.1 1.0.2*`

(3) Make changes to your theme.

**Note:** Make sure to update the version number on style.css, and the changelog on readme.txt

(4) Remove *.DS\_Store* hidden file. `*find . -name ".DS_Store" -print -delete*`

(5) Next, remove `*__MACOSX*` folder. `*rm -R __MACOSX*`

(6) Finally, you are ready to commit.

`*svn commit -m “Fix typo on readme.txt”*`

**Note:** Once you commit, there is no way to change or modify what you just committed. If you find a mistake, Repeat the process from step 2.

### What to expect next

Once you successfully upload the new update, you will receive a confirmation email from WordPress.org. It may take some time to reflect on the WordPress.org directory.