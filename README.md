# Svelte Heroicons Component

This is a heroicons in svelte component


### Installing

```bash
$ npm install -D svelte-heroicons-component
```

### Usage

```js


import { HomeIcon, HomeSolidIcon} from 'svelte-heroicons-component'

// to add click event you can do like this
<HomeIcon on:click={callFunction}>

<HomeSolidIcon on:click={callFunction}>


```

```js

// to add class name
<HomeIcon size={4} className="hidden lg:block">

```

```js
// default size is 1.5rem but you can customized the size like this (unit size is rem)
<HomeIcon size={4}>

```

```js
// If you use tailwindcss the classname w-* will override the size value
<HomeIcon size={4} className="w-6 h-6 xl:w-8 h-8">

```

```js

// the default strokewidth is 2 but you can change like this. Props strokeWidth only exists in outline icons
<HomeIcon strokeWidth={5}>

```

```js

// If you use tailwindcss the classname stroke-* will override the strokeWidth value
<HomeIcon strokeWidth={5} className="stroke-2">

```

```js

// If you want to fill the color you can do like this. Props fill only exists in outline icons
<HomeIcon fill="#87CEEB">

```

Available Icons:

<pre>
AcademicCap         CloudDownload         Home                   Save
Adjustment          Cloud                 Identification         Scale
Annotation          CloudUpload           InboxIn                Scissors
Archive             Code                  Inbox                  SearchCircle
ArrowCircleDown     Cog                   InformationCircle      Search
ArrowCircleLeft     Collection            Key                    Selector
ArrowCircleRight    ColorSwatch           Library                Server
ArrowCircleUp       CreditCard            LightBulb              Share
ArrowDown           Cube                  LightningBolt          ShieldCheck
ArrowLeft           CubeTransparent       Link                   ShieldExclamation
ArrowNarrowDown     CurrencyBangladeshi   LocationMarker         ShoppingBag
ArrowNarrowLeft     CurrencyDollar        LockClosed             ShoppingCart
ArrowNarrowRight    CurrencyEuro          LockOpen               SortAscending
ArrowNarrowUp       CurrencyPound         Login                  SortDescending
ArrowRight          CurrencyRupee         Logout                 Sparkles
ArrowsExpand        CurrencyYen           MailOpen               SpeakerPhone
ArrowSmDown         CursorClick           Mail                   Star
ArrowSmLeft         Database              Map                    StatusOffline
ArrowSmRight        DesktopComputer       MenuAlt1               StatusOnline
ArrowSmUp           DeviceMobile          MenuAlt2               Stop
ArrowUp             DeviceTablet          MenuAlt3               Sun
AtSymbol            DocumentAdd           MenuAlt4               Support
Backspace           DocumentDownload      Menu                   SwitchHorizontal
BadgeCheck          DocumentDuplicate     Microphone             SwitchVertical
Ban                 DocumentRemove        MinusCircle            Table
Beaker              DocumentReport        MinusSm                Tag
Bell                DocumentSearch        Minus                  Template
BookmarkAlt         Document              Moon                   Terminal
Bookmark            DocumentText          MusicNote              ThumbDown
BookOpen            DotsCircleHorizontal  Newspaper              ThumbUp
Briefcase           DotsHorizontal        OfficeBuilding         Ticket
Cake                DotsVertical          PaperAirplane          Translate
Calculator          Download              PaperClip              Trash
Calendar            Duplicate             Pause                  TrendingDown
Camera              EmojiHappy            PencilAlt              TrendingUp
Cash                EmojiSad              Pencil                 Truck
ChartBar            ExclamationCircle     PhoneIncoming          Upload
ChartPie            Exclamation           PhoneMissedCall        UserAdd
ChartSquareBar      ExternalLink          PhoneOutgoing          UserCircle
ChatAlt2            EyeOff                Phone                  UserGroup
ChatAlt             Eye                   Photograph             UserRemove
Chat                FastForward           Play                   Users
CheckCircle         Film                  PlusCircle             User
Check               Filter                PlusSm                 Variable
ChevronDoubleDown   FingerPrint           Plus                   VideoCamera
ChevronDoubleLeft   Fire                  PresentationChartBar   ViewBoards
ChevronDoubleRight  Flag                  PresentationChartLine  ViewGridAdd
ChevronDoubleUp     FolderAdd             Printer                ViewGrid
ChevronDown         FolderDownload        Puzzle                 ViewList
ChevronLeft         FolderOpen            Qrcode                 VolumeOff
ChevronRight        FolderRemove          QuestionMarkCircle     VolumeUp
ChevronUp           Folder                ReceiptRefund          Wifi
Chip                Gift                  ReceiptTax             XCircle
ClipboardCheck      GlobeAlt              Refresh                X
ClipboardCopy       Globe                 Reply                  ZoomIn
ClipboardList       Hand                  Rewind                 ZoomOut
Clipboard           Hastag                Rss
Clock               Heart                 SaveAs
</pre>