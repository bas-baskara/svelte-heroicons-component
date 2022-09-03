# Svelte Heroicons Component

Heroicons component for Svelte. Support Heroicons v1 and v2.
Available props are: className, size, strokeWidth, and fill(solid icon only). You can also add on:click event.

### Installing

```bash
npm install -D svelte-heroicons-component
```

### Usage

```js

//Example: to use heroicons home just import the HomeIcon component. If you want to use a solid icon import HomeSolidIcon.

import { HomeIcon, HomeSolidIcon} from 'svelte-heroicons-component'


<HomeIcon />
<HomeSolidIcon />

```

```js
// to add click event you can do like this
<HomeIcon on:click={callFunction} />

<HomeSolidIcon on:click={callFunction} />


```

```js

// to add class name
<HomeIcon className="hidden lg:block" />

```

```js
// default size is 1.5rem but you can customized the size like this example bellow
<HomeIcon size="10px" />
<HomeIcon size="20pt" />
<HomeIcon size="3em" />
<HomeIcon size="2rem" />
<HomeIcon size="4" /> # "The default unit size is rem, so this will be 4rem"


```

```js
// If you use tailwindcss the classname w-* will override the size value
<HomeIcon size="4rem" className="w-6 h-6 xl:w-8 h-8" />

```

```js

// the default strokewidth is 2 but you can change like this. Props strokeWidth only exists in outline icons
<HomeIcon strokeWidth="5" />

```

```js

// If you use tailwindcss the classname stroke-* will override the strokeWidth value
<HomeIcon strokeWidth="5" className="stroke-2" />

```

```js

// If you want to fill the color you can do like this. Props fill only exists in outline icons
<HomeIcon fill="#87CEEB" />

```

Available Icons:
[https://heroicons.com](https://heroicons.com/)
[https://v1.heroicons.com/](https://v1.heroicons.com/)


```js
Note: Add Icon to the end of component name (e.g., AcademicCapIcon) . For solid icon add SolicIcon to the end of component name (e.g., AcademicCapSolidIcon).

```