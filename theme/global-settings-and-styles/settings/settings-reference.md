<!-- 
# Settings Reference
 -->

# 設定リファレンス

<!-- 
The document is a reference to the available settings properties that you can configure via the `settings` object in `theme.json`. Each of the settings has an in-depth guide on how to use it within the [Settings documentation](https://developer.wordpress.org/themes/global-settings-and-styles/settings/).
 -->

このドキュメントは、`theme.json` 内の `settings` オブジェクトを介して設定可能なプロパティのリファレンスです。各設定項目については、[設定ドキュメント](https://developer.wordpress.org/themes/global-settings-and-styles/settings/) 内で詳細な使用方法が説明されています。

<!-- 
## Appearance Tools
 -->

## 外観ツール

<!-- 
`settings.appearanceTools` is a top-level property with no sub-properties nested beneath it. It is documented at [Settings: Appearance Tools](https://developer.wordpress.org/global-settings-and-styles/settings/appearance-tools/).
 -->

`settings.appearanceTools` は、最上位のプロパティであり、その下にネストされたサブ・プロパティは存在しません。これは [設定: 外観ツール](https://developer.wordpress.org/global-settings-and-styles/settings/appearance-tools/) でドキュメント化されています。

<!-- 
| Property | Type | Default |
| --- | --- | --- |
| `appearanceTools` | boolean | `false` |
 -->

| プロパティ | 型 | デフォルト |
| --- | --- | --- |
| `appearanceTools` | 真偽値 | `false` |

<!-- 
## Border
 -->

## 枠線

<!-- 
`settings.border` is an object that supports the nested properties listed in the below table. It is documented at [Settings: Border](https://developer.wordpress.org/global-settings-and-styles/settings/border/).
 -->

`settings.border` は、以下の表に列挙された、ネストされたプロパティをサポートする、オブジェクトです。これは [設定: 枠線](https://developer.wordpress.org/global-settings-and-styles/settings/border/) でドキュメント化されています。

<!-- 
| Property | Type | Default |
| --- | --- | --- |
| `color` | boolean | `false` |
| `radius` | boolean | `false` |
| `style` | boolean | `false` |
| `width` | boolean | `false` |
 -->

| プロパティ | 型 | デフォルト |
| --- | --- | --- |
| `color` | 真偽値 | `false` |
| `radius` | 真偽値 | `false` |
| `style` | 真偽値 | `false` |
| `width` | 真偽値 | `false` |

<!-- 
Enabling any one of the `color`, `style`, or `width` settings will automatically enable the other two since the properties are linked together.
 -->

`color`、`style`、`width` のいずれかの設定を有効にすると、これらのプロパティは相互に関連付けられているため、自動的に他の2つも有効になります。

<!-- 
## Color
 -->

## 色

<!-- 
`settings.color` is an object that supports the nested properties listed in the below table. It is documented at [Settings: Color](https://developer.wordpress.org/global-settings-and-styles/settings/color/).
 -->

`settings.color` は、以下の表に列挙された、ネストされたプロパティをサポートする、オブジェクトです。これは [設定: 色](https://developer.wordpress.org/global-settings-and-styles/settings/color/) でドキュメント化されています。

<!-- 
| Property | Type | Default | Props |
| --- | --- | --- | --- |
| `background` | boolean | `true` | — |
| `custom` | boolean | `true` | — |
| `customDuotone` | boolean | `true` | — |
| `customGradient` | boolean | `true` | — |
| `defaultDuotone` | boolean | `true` | — |
| `defaultGradients` | boolean | `true` | — |
| `defaultPalette` | boolean | `true` | — |
| `duotone` | array <object> | `array` | `colors`, `name`, `slug` |
| `gradients` | array <object> | `array` | `gradient`, `name`, `slug` |
| `link` | boolean | `false` | — |
| `palette` | array <object> | `array` | `color`, `name`, `slug` |
| `text` | boolean | `true` | — |
 -->

| プロパティ | 型 | デフォルト | プロパティ |
| --- | --- | --- | --- |
| `background` | 真偽値 | `true` | — |
| `custom` | 真偽値 | `true` | — |
| `customDuotone` | 真偽値 | `true` | — |
| `customGradient` | 真偽値 | `true` | — |
| `defaultDuotone` | 真偽値 | `true` | — |
| `defaultGradients` | 真偽値 | `true` | — |
| `defaultPalette` | 真偽値 | `true` | — |
| `duotone` | 配列 <オブジェクト> | `array` | `colors`、`name`、`slug` |
| `gradients` | 配列 <オブジェクト> | `array` | `gradient`、`name`、`slug` |
| `link` | 真偽値 | `false` | — |
| `palette` | 配列 <オブジェクト> | `array` | `color`、`name`、`slug` |
| `text` | 真偽値 | `true` | — |

<!-- 
## Custom
 -->

## カスタム

<!-- 
`settings.custom` is an object that supports any number of nested custom properties, as shown in the below table. It is documented at [Settings: Custom](https://developer.wordpress.org/global-settings-and-styles/settings/custom/).
 -->

`settings.custom` は、以下の表に示すように、任意の数のネストされたカスタム・プロパティをサポートする、オブジェクトです。これは [設定: カスタム](https://developer.wordpress.org/global-settings-and-styles/settings/custom/) でドキュメント化されています。

<!-- 
| Property | Type | Default |
| --- | --- | --- |
| `custom.<custom>` | any | — |
 -->

| プロパティ | 型 | デフォルト |
| --- | --- | --- |
| `custom.<custom>` | 任意 | — |

<!-- 
## Dimensions
 -->

## 寸法

<!-- 
`settings.dimensions` is an object that supports the nested properties listed in the below table. It is documented at [Settings: Dimensions](https://developer.wordpress.org/global-settings-and-styles/settings/dimensions/).
 -->

`settings.dimensions` は、以下の表に列挙された、ネストされたプロパティをサポートする、オブジェクトです。これは [設定: 寸法](https://developer.wordpress.org/global-settings-and-styles/settings/dimensions/) でドキュメント化されています。

<!-- 
| Property | Type | Default |
| --- | --- | --- |
| `minHeight` | boolean | `false` |
 -->

| プロパティ | 型 | デフォルト |
| --- | --- | --- |
| `minHeight` | 真偽値 | `false` |

<!-- 
## Layout
 -->

## レイアウト

<!-- 
`settings.layout` is an object that supports the nested properties listed in the below table. It is documented at [Settings: Layout](https://developer.wordpress.org/global-settings-and-styles/settings/layout/).
 -->

`settings.layout` は、以下の表に列挙された、ネストされたプロパティをサポートする、オブジェクトです。これは [設定: レイアウト](https://developer.wordpress.org/global-settings-and-styles/settings/layout/) でドキュメント化されています。

<!-- 
| Property | Type | Default |
| --- | --- | --- |
| `contentSize` | string | `""` |
| `wideSize` | string | `""` |
 -->

| プロパティ | 型 | デフォルト |
| --- | --- | --- |
| `contentSize` | 文字列 | `""` |
| `wideSize` | 文字列 | `""` |

<!-- 
## Lightbox
 -->

## ライトボックス

<!-- 
`settings.lightbox` is an object that supports the nested properties listed in the below table. It is documented at [Settings: Lightbox](https://developer.wordpress.org/global-settings-and-styles/settings/lightbox/).
 -->

`settings.lightbox` は、以下の表に列挙された、ネストされたプロパティをサポートする、オブジェクトです。これは [設定: ライトボックス](https://developer.wordpress.org/global-settings-and-styles/settings/lightbox/) でドキュメント化されています。

<!-- 
| Property | Type | Default |
| --- | --- | --- |
| `allowEditing` | boolean | `true` |
| `enabled` | boolean | `false` |
 -->

| プロパティ | 型 | デフォルト |
| --- | --- | --- |
| `allowEditing` | 真偽値 | `true` |
| `enabled` | 真偽値 | `false` |

<!-- 
This setting is only available as of WordPress 6.4 and is specific to the core Image block (`core/image`).
 -->

この設定は WordPress 6.4以降でのみ利用可能であり、コアの「画像」ブロック (`core/image`) に固有のものです。

<!-- 
## Position
 -->

## 位置

<!-- 
`settings.position` is an object that supports the nested properties listed in the below table. It is documented at [Settings: Position](https://developer.wordpress.org/global-settings-and-styles/settings/position/).
 -->

`settings.position` は、以下の表に列挙された、ネストされたプロパティをサポートする、オブジェクトです。これは [設定: 位置](https://developer.wordpress.org/global-settings-and-styles/settings/position/) でドキュメント化されています。

<!-- 
| Property | Type | Default |
| --- | --- | --- |
| `sticky` | boolean | `false` |
 -->

| プロパティ | 型 | デフォルト |
| --- | --- | --- |
| `sticky` | 真偽値 | `false` |

<!-- 
## Shadow
 -->

## シャドウ

<!-- 
`settings.shadow` is an object that supports the nested properties listed in the below table. It is documented at [Settings: Shadow](https://developer.wordpress.org/global-settings-and-styles/settings/shadow/).
 -->

`settings.shadow` は、以下の表に列挙された、ネストされたプロパティをサポートする、オブジェクトです。これは [設定: シャドウ](https://developer.wordpress.org/global-settings-and-styles/settings/shadow/) でドキュメント化されています。

<!-- 
| Property | Type | Default | Props |
| --- | --- | --- | --- |
| `defaultPresets` | boolean | `true` |  |
| `presets` | array <object> | `array` | `name`, `shadow`, `slug` |
 -->

| プロパティ | 型 | デフォルト | プロパティ |
| --- | --- | --- | --- |
| `defaultPresets` | 真偽値 | `true` |  |
| `presets` | 配列 <オブジェクト> | `array` | `name`、`shadow`、`slug` |

<!-- 
## Spacing
 -->

## 間隔

<!-- 
`settings.spacing` is an object that supports the nested properties listed in the below table. It is documented at [Settings: Spacing](https://developer.wordpress.org/global-settings-and-styles/settings/spacing/).
 -->

`settings.spacing` は、以下の表に列挙された、ネストされたプロパティをサポートする、オブジェクトです。これは [設定: 間隔](https://developer.wordpress.org/global-settings-and-styles/settings/spacing/) でドキュメント化されています。

<!-- 
| Property | Type | Default | Props |
| --- | --- | --- | --- |
| `blockGap` | boolean|null | `null` | — |
| `customSpacingSize` | boolean | `true` | — |
| `margin` | boolean | `false` | — |
| `padding` | boolean | `false` | — |
| `spacingScale` | object | `object` | `operator`, `increment`, `steps`, `mediumStep`, `unit` |
| `spacingSizes` | array <object> | `array` | `name`, `size`, `slug` |
| `units` | array <string> | `[ "px", "em", "rem", "vh", "vw", "%" ]` | — |
 -->

| プロパティ | 型 | デフォルト | プロパティ |
| --- | --- | --- | --- |
| `blockGap` | 真偽値|null | `null` | — |
| `customSpacingSize` | 真偽値 | `true` | — |
| `margin` | 真偽値 | `false` | — |
| `padding` | 真偽値 | `false` | — |
| `spacingScale` | object | `object` | `operator`、`increment`、`steps`、`mediumStep`、`unit` |
| `spacingSizes` | 配列 <オブジェクト> | `array` | `name`、`size`、`slug` |
| `units` | 配列 <文字列> | `[ "px", "em", "rem", "vh", "vw", "%" ]` | — |

<!-- 
## Typography
 -->

## タイポグラフィ

<!-- 
`settings.typography` is an object that supports the nested properties listed in the below table. It is documented at [Settings: Typography](https://developer.wordpress.org/global-settings-and-styles/settings/typography/).
 -->

`settings.typography` は、以下の表に列挙された、ネストされたプロパティをサポートする、オブジェクトです。これは [設定: タイポグラフィ](https://developer.wordpress.org/global-settings-and-styles/settings/typography/) でドキュメント化されています。

<!-- 
| Property | Type | Default | Props |
| --- | --- | --- | --- |
| `customFontSize` | boolean | `true` | — |
| `dropCap` | boolean | `true` | — |
| `fontFamilies` | array <object> | `array` | `fontFace`, `fontFamily`, `name`, `slug` |
| `fontSizes` | array <object> | `array` | `fluid`, `name`, `size`, `slug` |
| `fontStyle` | boolean | `true` | — |
| `fontWeight` | boolean | `true` | — |
| `fluid` | boolean | `false` | — |
| `letterSpacing` | boolean | `true` | — |
| `lineHeight` | boolean | `false` | — |
| `textColumns` | boolean | `false` | — |
| `textDecoration` | boolean | `true` | — |
| `textTransform` | boolean | `true` | — |
| `writingMode` | boolean | `false` | — |
 -->

| プロパティ | 型 | デフォルト | プロパティ |
| --- | --- | --- | --- |
| `customFontSize` | 真偽値 | `true` | — |
| `dropCap` | 真偽値 | `true` | — |
| `fontFamilies` | 配列 <オブジェクト> | `array` | `fontFace`、`fontFamily`、`name`、`slug` |
| `fontSizes` | 配列 <オブジェクト> | `array` | `fluid`、`name`、`size`、`slug` |
| `fontStyle` | 真偽値 | `true` | — |
| `fontWeight` | 真偽値 | `true` | — |
| `fluid` | 真偽値 | `false` | — |
| `letterSpacing` | 真偽値 | `true` | — |
| `lineHeight` | 真偽値 | `false` | — |
| `textColumns` | 真偽値 | `false` | — |
| `textDecoration` | 真偽値 | `true` | — |
| `textTransform` | 真偽値 | `true` | — |
| `writingMode` | 真偽値 | `false` | — |

<!-- 
## Use Root Padding Aware Alignments
 -->

## ルート・パディング対応配置の使用

<!-- 
`settings.useRootPaddingAwareAlignments` is a top-level property with no sub-properties nested beneath it. It is documented at [Settings: Use Root Padding Aware Alignments](https://developer.wordpress.org/global-settings-and-styles/settings/use-root-padding-aware-alignments/).
 -->

`settings.useRootPaddingAwareAlignments` は、最上位のプロパティであり、その下にネストされたサブ・プロパティは存在しません。これは [設定: ルート・パディング対応配置の使用](https://developer.wordpress.org/global-settings-and-styles/settings/use-root-padding-aware-alignments/) でドキュメント化されています。

<!-- 
| Property | Type | Default |
| --- | --- | --- |
| `useRootPaddingAwareAlignments` | boolean | `false` |
 -->

| プロパティ | 型 | デフォルト |
| --- | --- | --- |
| `useRootPaddingAwareAlignments` | 真偽値 | `false` |

<!-- 
This setting works together with `styles.spacing.padding` in `theme.json`. If enabled, `styles.spacing.padding` must be an object that defines the `top`, `right`,  `bottom`, and `left` styles separately.
 -->

この設定は、`theme.json` 内の `styles.spacing.padding` と連動します。有効化する場合、`styles.spacing.padding` は、`top`、`right`、`bottom`、`left` の各スタイルを個別に定義する、オブジェクトである必要があります。