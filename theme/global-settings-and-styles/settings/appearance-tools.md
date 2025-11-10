<!-- 
# Appearance Tools
 -->

# 外観ツール

<!-- 
`settings.appearanceTools` is a unique property in `theme.json` that behaves as a catchall for multiple other properties. Compared to other settings that you can configure, this one makes it easy to enable several design-related settings in one go.
 -->

`settings.appearanceTools` は `theme.json` 内のユニークなプロパティであり、他の複数のプロパティを包括的に扱う役割を果たします。他の設定項目と比較して、この設定項目を使用すると、デザイン関連の複数の設定を一度に簡単に有効化できます。

<!-- 
## Opting into appearance tools
 -->

## 外観ツールの有効化

<!-- 
`settings.appearanceTools` enables several features related to the design or the *appearance* of a site. By default, the value is set to `false`, so if you choose to not use this property, you can simply not add it to your `theme.json`.
 -->

`settings.appearanceTools` は、サイトのデザインや *外観* に関連するいくつかの機能を有効にします。デフォルトでは、値は `false` に設定されているので、このプロパティを使用しない場合は、`theme.json` に追加しないだけで済みます。

<!-- 
However, if you want to enable it, you can set it to `true`:
 -->

ただし、有効にしたい場合は、`true` に設定できます:

```json
{
	"version": 2,
	"settings": {
		"appearanceTools": true
	}
}
```

<!-- 
This is the equivalent of setting these properties individually in `theme.json`:
 -->

これは、`theme.json` でこれらのプロパティを個別に設定するのと同じです:

```json
{
	"version": 2,
	"settings": {
		"border": {
			"color": true,
			"radius": true,
			"style": true,
			"width": true
		},
		"color": {
			"link": true
		},
		"dimensions": {
			"minHeight": true
		},
		"position": {
			"sticky": true
		},
		"spacing": {
			"blockGap": true,
			"margin": true,
			"padding": true
		},
		"typography": {
			"lineHeight": true
		}
	}
}
```

<!-- 
As you can see, it can be a major time-saver and create much less work for you. With `settings.appearanceTools` enabled, you can skip setting those properties individually.
 -->

ご覧の通り、大幅な時間短縮となり、作業量を大幅に削減できます。`settings.appearanceTools` を有効にすると、これらのプロパティを個別に設定する手間を省けます。

<!-- 
You can learn more about what each does via its documentation here in the handbook:
 -->

各機能の詳細については、ハンドブック内のそれぞれのドキュメントで確認できます:

<!-- 
*   [Border](https://developer.wordpress.org/themes/global-settings-and-styles/border)
*   [Color](https://developer.wordpress.org/themes/global-settings-and-styles/color)
*   [Dimensions](https://developer.wordpress.org/themes/global-settings-and-styles/dimensions)
*   [Position](https://developer.wordpress.org/themes/global-settings-and-styles/position)
*   [Spacing](https://developer.wordpress.org/themes/global-settings-and-styles/spacing)
*   [Typography](https://developer.wordpress.org/themes/global-settings-and-styles/typography)
 -->

*   [枠線](https://developer.wordpress.org/themes/global-settings-and-styles/border)
*   [色](https://developer.wordpress.org/themes/global-settings-and-styles/color)
*   [寸法](https://developer.wordpress.org/themes/global-settings-and-styles/dimensions)
*   [位置](https://developer.wordpress.org/themes/global-settings-and-styles/position)
*   [間隔](https://developer.wordpress.org/themes/global-settings-and-styles/spacing)
*   [タイポグラフィ](https://developer.wordpress.org/themes/global-settings-and-styles/typography)

<!-- 
## Overwriting appearance tools
 -->

## 外観ツールの上書き

<!-- 
Just because you’ve enabled `appearanceTools` doesn’t mean that you cannot disable some features. You can do both.
 -->

`appearanceTools` を有効にしたからといって、一部の機能を無効にできないわけではありません。両方とも可能です。

<!-- 
Suppose that you wanted to enable all appearance tools but disable sticky positioning. You would use this code in your `theme.json` to do this:
 -->

すべての外観ツールを有効にしつつ、位置の固定指定を無効にしたい、としましょう。その場合は、あなたの `theme.json` に以下のコードを使用します:

```json
{
	"version": 2,
	"settings": {
		"appearanceTools": true,
		"position": {
			"sticky": false
		}
	}
}
```

<!-- 
This gives you the best of both worlds. You can use `appearanceTools` to enable a large selection of settings but disable others on a case-by-case basis.
 -->

これにより、両方の長所を兼ね備えた状態を実現できます。`appearanceTools` を使用すれば、多数の設定を有効にしながら、ケースバイケースで他の設定を無効にできます。

<!-- 
## Should I enable appearance tools?
 -->

## 外観ツールを有効にすべき ?

<!-- 
There is one caveat to setting `appearanceTools` to `true` in your `theme.json` file: it can automatically opt your theme into design tools in the future. Sometimes, WordPress enables new features when this setting is enabled.
 -->

`theme.json` ファイルで `appearanceTools` を `true` に設定する際の注意点があります: この設定により、あなたのテーマが将来的にデザインツールを自動的に有効にする可能性があります。時々、この設定が有効になっていると、WordPress は新機能を有効にします。

<!-- 
Because no one can reliably predict the future, you need to decide whether you want your theme to support unknown design features that you haven’t tested today. 
 -->

未来を確実に予測できる者はいないことを考えると、あなたのテーマが、現時点でテストしていない未知のデザイン機能をサポートすべきかどうかを、判断する必要があります。

<!-- 
For many publicly-distributed themes, this will not typically be an issue if you want to provide a lot of flexibility for your theme’s users. By enabling `appearanceTools`, you can give users new design features without updating your theme.
 -->

多くの公開配布テーマでは、あなたのテーマのユーザーに高い柔軟性を提供したい場合、これは通常問題になりません。`appearanceTools` を有効にすることで、あなたのテーマを更新せずに、ユーザーに新しいデザイン機能を提供できます。

<!-- 
For agencies and freelancers, this could create issues for your clients. Often, these projects are meant to limit the user interface to only specific design tools that the client needs. If WordPress adds new appearance tools in a future update, it’s possible the client will see new and unfamiliar features. For this reason, leaving `appearanceTools` disabled will often make sense.
 -->

代理店やフリーランサーにとって、これはあなたのクライアントに問題を引き起こす可能性があります。多くの場合、これらのプロジェクトは、UI をクライアントが必要とする特定のデザインツールのみに制限することを、目的としています。WordPress が将来のアップデートで新しい外観ツールを追加した場合、クライアントが新しく見慣れない機能に遭遇する可能性があります。こうした理由から、`appearanceTools` を無効にしたままにしておくことが、多くの場合は合理的です。