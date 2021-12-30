# Svelte Heroicons Component

This is a heroicons in svelte component


### Installing

```bash
$ npm install -D svelte-heroicons-component
```

### Usage

```js
import { HomeIcon} from 'svelte-heroicons-component'

// to add click event you can do like this
<HomeIcon on:click={callFunction}>

```

```js
// default size is 1.5rem but you can customized the size like this
<HomeIcon size={4}>

```

```js

// to add class name
<HomeIcon size={4} className="hidden lg:block">

```

```js

// the default strokewidth is 2 but you can change like this
<HomeIcon strokeWidth={5}>

```

```js

// If you want to fill the color you can do like this
<HomeIcon fill="#87CEEB">

```
All icons will available very soon along with my current project.

Available Icons are:
ArrowExpand
BookMark
BookOpen
ChevronDoubleDown
ChevronDoubleLeft
ChevronDoubleRight
ChevronDoubleUp
ChevronDown
ChevronLeft
ChevronRight
ChevronUp
Eye
EyeOff
Home
Menu
MenuAlt1
MenuAlt2
MenuAlt3
MenuAlt4
Star
Search
SearchCircle
User
UserCircle
UserGroup
Users
XIcon
ZoomIn
ZoomOut