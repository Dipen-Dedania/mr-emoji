
## Mr Emoji 
It's a fork of emoji-mart. A main purpose of using this package is to reduce your package size. 
With emoji-mart, bundle sizes will be around <b>600kb+ (minified)</b>. 
With mr-emoji, bundle sizes will be around <b>250kb (minified)</b>. And you will have pretty icons too.
We have removed few things like, there will be only Apple icons available and you can not change the skin of emoji. 
We have added Parser to detect text with emoji.

[![Known Vulnerabilities](https://snyk.io/test/github/dipen-dedania/mr-emoji/badge.svg?targetFile=package.json)](https://snyk.io/test/github/dipen-dedania/mr-emoji?targetFile=package.json)
[![NPM](https://img.shields.io/npm/v/mr-emoji.svg)](https://www.npmjs.com/package/mr-emoji) 

### Smile, you are saving 350kb+ bundle size :)

## Installation

<div align="center">
  <br><b>Mr Emoji</b> is a Slack-like customizable<br>emoji picker component for React
  <br><a href="https://missive.github.io/emoji-mart">Demo</a> • <a href="https://github.com/missive/emoji-mart/releases">Changelog</a>
  <br><br><img width="338" alt="picker" src="https://user-images.githubusercontent.com/436043/32532554-08be471c-c400-11e7-906a-c745dc3ec630.png">
  <br><br><a title="Team email, team chat, team tasks, one app" href="https://missiveapp.com"><img width="30" alt="Missive | Team email, team chat, team tasks, one app" src="https://user-images.githubusercontent.com/436043/32532559-0d15ddfc-c400-11e7-8a24-64d0157d0cb0.png"></a>
  <br>Brought to you by the <a title="Team email, team chat, team tasks, one app" href="https://missiveapp.com">Missive</a> team
</div>


`npm install --save mr-emoji`

## Components
### Picker
```jsx
import { Picker } from 'mr-emoji'

<Picker set='emojione' />
<Picker onClick={this.addEmoji} />
<Picker title='Pick your emoji…' emoji='point_up' />
<Picker style={{ position: 'absolute', bottom: '20px', right: '20px' }} />
<Picker i18n={{ search: 'Recherche', categories: { search: 'Résultats de recherche', recent: 'Récents' } }} />
```

| Prop | Required | Default | Description |
| ---- | :------: | ------- | ----------- |
| **autoFocus** | | `false` | Auto focus the search input when mounted |
| **color** | | `#ae65c5` | The top bar anchors select and hover color |
| **emoji** | | `department_store` | The emoji shown when no emojis are hovered, set to an empty string to show nothing |
| **include** | | `[]` | Only load included categories. Accepts [I18n categories keys](#i18n). Order will be respected, except for the `recent` category which will always be the first. |
| **exclude** | | `[]` | Don't load excluded categories. Accepts [I18n categories keys](#i18n). |
| **custom** | | `[]` | [Custom emojis](#custom-emojis) |
| **recent** | | | Pass your own frequently used emojis as array of string IDs |
| **emojiSize** | | `24` | The emoji width and height |
| **onClick** | | | Params: `(emoji, event) => {}` |
| **perLine** | | `9` | Number of emojis per line. While there’s no minimum or maximum, this will affect the picker’s width. This will set *Frequently Used* length as well (`perLine * 4`) |
| **i18n** | | [`{…}`](#i18n) | [An object](#i18n) containing localized strings |
| **native** | | `false` | Renders the native unicode emoji |
| **set** | | `apple` | The emoji set: `'apple', 'google', 'twitter', 'emojione', 'messenger', 'facebook'` |
| **sheetSize** | | `64` | The emoji [sheet size](#sheet-sizes): `16, 20, 32, 64` |
| **backgroundImageFn** | | ```((set, sheetSize) => …)``` | A Fn that returns that image sheet to use for emojis. Useful for avoiding a request if you have the sheet locally. |
| **emojisToShowFilter** | | ```((emoji) => true)``` | A Fn to choose whether an emoji should be displayed or not |
| **showPreview** | | `true` | Display preview section |
| **emojiTooltip** | | `false` | Show emojis short name when hovering (title) |
| **skin** | | `1` | Default skin color: `1` |
| **style** | | | Inline styles applied to the root element. Useful for positioning |
| **title** | | `Emoji Mart™` | The title shown when no emojis are hovered |

#### I18n
```js
search: 'Search',
notfound: 'No Emoji Found',
categories: {
  search: 'Search Results',
  recent: 'Frequently Used',
  people: 'Smileys & People',
  nature: 'Animals & Nature',
  foods: 'Food & Drink',
  activity: 'Activity',
  places: 'Travel & Places',
  objects: 'Objects',
  symbols: 'Symbols',
  flags: 'Flags',
  custom: 'Custom',
}
```

### Parser
```jsx
import { Parser } from 'mr-emoji'

<Parser data="Hello there!" />
<Parser data="Hello there! :grinning:" />
<Parser data="Hello there! :grinning: Nice to meet you." />

```

#### Sheet sizes
Sheets are served from [unpkg](https://unpkg.com), a global CDN that serves files published to [npm](https://www.npmjs.com).

| Set       | sheetSize | Size     |
| --------- | --------- | -------- |
| apple     | 16        | 334 KB   |
| apple     | 20        | 459 KB   |
| apple     | 32        | 1.08 MB  |
| apple     | 64        | 2.94 MB  |

#### Examples of `emoji` object:
```js
{
  id: 'smiley',
  name: 'Smiling Face with Open Mouth',
  colons: ':smiley:',
  text: ':)',
  emoticons: [
    '=)',
    '=-)'
  ],
  skin: null,
  native: '😃'
}

{
  id: 'santa',
  name: 'Father Christmas',
  colons: ':santa::skin-tone-3:',
  text: '',
  emoticons: [],
  skin: 3,
  native: '🎅🏼'
}

{
  id: 'octocat',
  name: 'Octocat',
  colons: ':octocat',
  text: '',
  emoticons: [],
  custom: true,
  imageUrl: 'https://assets-cdn.github.com/images/icons/emoji/octocat.png?v7'
}

```

### Emoji
```jsx
import { Emoji } from 'mr-emoji'

<Emoji emoji={{ id: 'santa', skin: 3 }} size={16} />
<Emoji emoji=':santa::skin-tone-3:' size={16} />
<Emoji emoji='santa' set='emojione' size={16} />
```

| Prop | Required | Default | Description |
| ---- | :------: | ------- | ----------- |
| **emoji** | ✓ | | Either a string or an `emoji` object |
| **size** | ✓ | | The emoji width and height. |
| **native** | | `false` | Renders the native unicode emoji |
| **onClick** | | | Params: `(emoji, event) => {}` |
| **onLeave** | | | Params: `(emoji, event) => {}` |
| **onOver** | | | Params: `(emoji, event) => {}` |
| [**fallback**](#unsupported-emojis-fallback) | | | Params: `(emoji) => {}` |
| **sheetSize** | | `64` | The emoji [sheet size](#sheet-sizes): `16, 20, 32, 64` |
| **backgroundImageFn** | | ```((set, sheetSize) => `https://unpkg.com/emoji-datasource@3.0.0/sheet_${set}_${sheetSize}.png`)``` | A Fn that returns that image sheet to use for emojis. Useful for avoiding a request if you have the sheet locally. |
| **tooltip** | | `false` | Show emoji short name when hovering (title) |
| [**html**](#using-with-dangerouslysetinnerhtml) | | `false` | Returns an HTML string to use with `dangerouslySetInnerHTML` |

#### Unsupported emojis fallback
Certain sets don’t support all emojis (i.e. Messenger & Facebook don’t support `:shrug:`). By default the Emoji component will not render anything so that the emojis’ don’t take space in the picker when not available. When using the standalone Emoji component, you can however render anything you want by providing the `fallback` props.

To have the component render `:shrug:` you would need to:

```js
<Emoji
  emoji={'shrug'}
  size={24}
  fallback={(emoji) => {
    return `:${emoji.short_names[0]}:`
  }}
/>
```

#### Using with `dangerouslySetInnerHTML`
The Emoji component being a [functional component](https://medium.com/missive-app/45-faster-react-functional-components-now-3509a668e69f), you can call it as you would call any function instead of using JSX. Make sure you pass `html: true` for it to return an HTML string.

```js
<span dangerouslySetInnerHTML={{
  __html: Emoji({
    html: true
    set: 'apple'
    emoji: '+1'
    size: 24
  })
}}></span>
```

## Custom emojis
You can provide custom emojis which will show up in their own category.

```js
import { Picker } from 'mr-emoji'

const customEmojis = [
  {
    name: 'Octocat',
    short_names: ['octocat'],
    text: '',
    emoticons: [],
    keywords: ['github'],
    imageUrl: 'https://assets-cdn.github.com/images/icons/emoji/octocat.png?v7'
  },
]

<Picker custom={customEmojis} />
```

## Headless search
The `Picker` doesn’t have to be mounted for you to take advantage of the advanced search results.

```js
import { emojiIndex } from 'mr-emoji'

emojiIndex.search('christmas').map((o) => o.native)
// => [🎄, 🎅🏼, 🔔, 🎁, ⛄️, ❄️]
```

## Storage
By default MrEmoji will store user chosen skin and frequently used emojis in `localStorage`. That can however be overwritten should you want to store these in your own storage.

```js
import { store } from 'mr-emoji'

store.setHandlers({
  getter: (key) => {
    // Get from your own storage (sync)
  },

  setter: (key, value) => {
    // Persist in your own storage (can be async)
  }
})
```

Possible keys are:

| Key | Value | Description |
| --- | ----- | ----------- |
| skin | `1, 2, 3, 4, 5, 6` | |
| frequently | `{ 'astonished': 11, '+1': 22 }` | An object where the key is the emoji name and the value is the usage count |
| last | 'astonished' | (Optional) Used by `frequently` to be sure the latest clicked emoji will always appear in the “Recent” category |

## Features
### Powerful search
#### Short name, name and keywords
Not only does **Emoji Mart** return more results than most emoji picker, they’re more accurate and sorted by relevance.

<img width="338" alt="summer" src="https://user-images.githubusercontent.com/436043/32532567-179f1be4-c400-11e7-885e-df6e9b52c665.png">

#### Emoticons
The only emoji picker that returns emojis when searching for emoticons.

<img width="338" alt="emoticons" src="https://user-images.githubusercontent.com/436043/32532570-1be0dd28-c400-11e7-90cd-f33396277602.png">

#### Results intersection
For better results, **Emoji Mart** split search into words and only returns results matching both terms.

<img width="338" alt="high-five" src="https://user-images.githubusercontent.com/436043/32532573-1f4a9d1e-c400-11e7-8656-921bc6c09732.png">

### Fully customizable
#### Anchors color, title and default emoji
<img width="338" alt="customizable-color" src="https://user-images.githubusercontent.com/436043/32532582-302dc9e4-c400-11e7-9b97-f37c447231ca.png"><br><img width="338" alt="pick-your-emoji" src="https://user-images.githubusercontent.com/436043/32532585-34546faa-c400-11e7-9c9d-fbbe830d4368.png">

#### Emojis sizes and length
<img width="296" alt="size-and-length" src="https://user-images.githubusercontent.com/436043/32532590-381f67de-c400-11e7-86f6-328e30d6b116.png">

#### Default skin color
As the developer, you have control over which skin color is used by default.

<img width="205" alt="skins" src="https://user-images.githubusercontent.com/436043/32532858-0a559560-c402-11e7-8680-f77f780a5a49.png">

It can however be overwritten as per user preference.

<img width="98" alt="customizable-skin" src="https://user-images.githubusercontent.com/436043/32532883-2c620e7c-c402-11e7-976c-50d32be0566c.png">

#### Multiple sets supported
Apple / Google / Twitter / EmojiOne / Messenger / Facebook

<img width="214" alt="sets" src="https://user-images.githubusercontent.com/436043/33786868-d4226e60-dc38-11e7-840a-e4cf490f5f4a.png">

## Not opinionated
**Emoji Mart** doesn’t automatically insert anything into a text input, nor does it show or hide itself. It simply returns an `emoji` object. It’s up to the developer to mount/unmount (it’s fast!) and position the picker. You can use the returned object as props for the `EmojiMart.Emoji` component. You could also use `emoji.colons` to insert text into a textarea or `emoji.native` to use the emoji.

## Development
```sh
$ yarn build
$ yarn start
$ yarn storybook
```

## 🎩 Hat tips!
Powered by [iamcal/emoji-data](https://github.com/iamcal/emoji-data) and inspired by [iamcal/js-emoji](https://github.com/iamcal/js-emoji).<br>
🙌🏼  [Cal Henderson](https://github.com/iamcal) & https://github.com/missive/emoji-mart.
