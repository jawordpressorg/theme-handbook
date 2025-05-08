# Appearance Tools

`settings.appearanceTools` is a unique property in `theme.json` that behaves as a catchall for multiple other properties. Compared to other settings that you can configure, this one makes it easy to enable several design-related settings in one go.

## Opting into appearance tools

`settings.appearanceTools` enables several features related to the design or the *appearance* of a site. By default, the value is set to `false`, so if you choose to not use this property, you can simply not add it to your `theme.json`.

However, if you want to enable it, you can set it to `true`:

```json
{
	"version": 2,
	"settings": {
		"appearanceTools": true
	}
}
```

This is the equivalent of setting these properties individually in `theme.json`:

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

As you can see, it can be a major time-saver and create much less work for you. With `settings.appearanceTools` enabled, you can skip setting those properties individually.

You can learn more about what each does via its documentation here in the handbook:

*   [Border](https://developer.wordpress.org/themes/global-settings-and-styles/border)
*   [Color](https://developer.wordpress.org/themes/global-settings-and-styles/color)
*   [Dimensions](https://developer.wordpress.org/themes/global-settings-and-styles/dimensions)
*   [Position](https://developer.wordpress.org/themes/global-settings-and-styles/position)
*   [Spacing](https://developer.wordpress.org/themes/global-settings-and-styles/spacing)
*   [Typography](https://developer.wordpress.org/themes/global-settings-and-styles/typography)

## Overwriting appearance tools

Just because you’ve enabled `appearanceTools` doesn’t mean that you cannot disable some features. You can do both.

Suppose that you wanted to enable all appearance tools but disable sticky positioning. You would use this code in your `theme.json` to do this:

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

This gives you the best of both worlds. You can use `appearanceTools` to enable a large selection of settings but disable others on a case-by-case basis.

## Should I enable appearance tools?

There is one caveat to setting `appearanceTools` to `true` in your `theme.json` file: it can automatically opt your theme into design tools in the future. Sometimes, WordPress enables new features when this setting is enabled.

Because no one can reliably predict the future, you need to decide whether you want your theme to support unknown design features that you haven’t tested today. 

For many publicly-distributed themes, this will not typically be an issue if you want to provide a lot of flexibility for your theme’s users. By enabling `appearanceTools`, you can give users new design features without updating your theme.

For agencies and freelancers, this could create issues for your clients. Often, these projects are meant to limit the user interface to only specific design tools that the client needs. If WordPress adds new appearance tools in a future update, it’s possible the client will see new and unfamiliar features. For this reason, leaving `appearanceTools` disabled will often make sense.