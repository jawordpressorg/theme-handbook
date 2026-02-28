<!-- 
# Advanced Usage
 -->

# 高度な使い方

<!-- 
The customize API is actively developed; this page contains additional more advanced topics. Additional discussion of advanced topics cab be found by searching the archives for the [#core-customize](https://wordpress.slack.com/messages/core-customize/) channel in [Slack](https://chat.wordpress.org/).
 -->

カスタマイズ API は、活発に開発中です; 本ページには、追加の高度なトピックが含まれています。高度なトピックに関する追加の議論は、[Slack](https://chat.wordpress.org/) 内の [#core-customize](https://wordpress.slack.com/messages/core-customize/) チャンネルのアーカイブを検索することで、見つけることができます。

<!-- 
## Allow Non-administrators to Access the Customizer
 -->

## 非管理者に、「カスタマイザー」へのアクセスの許可

<!-- 
Customizer access is controlled by the customize meta capability (mapped to edit\_theme\_options by default), which is assigned only to administrators by default. This allows for wider use of the Customizer’s extensive capability-access options, which are built into panels, sections, and settings. Additionally, this makes it possible to allow non-administrators to use the customizer for, for example, customizing posts. This change is an important step toward expanding the scope of the Customizer beyond themes.
 -->

「カスタマイザー」へのアクセスは、カスタマイズメタ権限 (デフォルトでは `edit_theme_options` にマッピング) によって制御され、デフォルトでは管理者だけに割り当てられます。これにより、パネル、セクション、設定に組み込まれた、「カスタマイザー」の広範な権限アクセスオプションをより広く利用できます。さらに、これにより、非管理者でも、たとえば投稿のカスタマイズなどに、カスタマイザーを使用できます。この変更は、「カスタマイザー」の適用範囲をテーマを超えて拡大するための重要な一歩です。

```php
<?php
function allow_users_who_can_edit_posts_to_customize( $caps, $cap, $user_id ) {
	$required_cap = 'edit_posts';
	if ( 'customize' === $cap && user_can( $user_id, $required_cap ) ) {
		$caps = array( $required_cap );
	}
	return $caps;
}
add_filter( 'map_meta_cap', 'allow_users_who_can_edit_posts_to_customize', 10, 3 );
```

<!-- 
Note that it is currently necessary to manually add links to the Customizer in the admin menu, admin bar, or elsewhere if you are granting the customize meta capability to non-administrator users.
 -->

管理者以外のユーザーにカスタマイズメタ権限を付与する場合、現時点では、管理メニュー、管理バー、またはその他の場所に、「カスタマイザー」へのリンクを手動で追加する必要があることに注意してください。