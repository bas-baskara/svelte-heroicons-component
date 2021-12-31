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

// If you use tailwindcss the classname stroke-* will override strokeWidth value
<HomeIcon strokeWidth={5} className="stroke-2">

```

```js

// If you want to fill the color you can do like this
<HomeIcon fill="#87CEEB">

```

Available Icons are:

AcademicCapIcon<br>
AdjustmentIcon<br>
AnnotationIcon<br>
ArchiveIcon<br>
ArrowCircleDownIcon<br>
ArrowCircleLeftIcon<br>
ArrowCircleRightIcon<br>
ArrowCircleUpIcon<br>
ArrowDownIcon<br>
ArrowExpandIcon<br>
ArrowLeftIcon<br>
ArrowNarrowDownIcon<br>
ArrowNarrowLeftIcon<br>
ArrowNarrowRightIcon<br>
ArrowNarrowUpIcon<br>
ArrowRightIcon<br>
ArrowSmDownIcon<br>
ArrowSmLeftIcon<br>
ArrowSmRightIcon<br>
ArrowSmUpIcon<br>
ArrowUpIcon<br>
AtSymbolIcon<br>
BackspaceIcon<br>
BadgeCheckIcon<br>
BanIcon<br>
BeakerIcon<br>
BellIcon<br>
BookMarkIcon<br>
BookMarkAltIcon<br>
BookOpenIcon<br>
BriefcaseIcon<br>
CalculatorIcon<br>
CalendarIcon<br>
CameraIcon<br>
CaseIcon<br>
CashIcon<br>
ChartBarIcon<br>
ChartPieIcon<br>
ChartSquareBarIcon<br>
ChatIcon<br>
ChatAltIcon<br>
ChatAlt2Icon<br>
CheckIcon<br>
CheckCircleIcon<br>
ChevronDoubleDownIcon<br>
ChevronDoubleLeftIcon<br>
ChevronDoubleRightIcon<br>
ChevronDoubleUpIcon<br>
ChevronDownIcon<br>
ChevronLeftIcon<br>
ChevronRightIcon<br>
ChevronUpIcon<br>
ChipIcon<br>
ClipboardIcon<br>
ClipboardCheckIcon<br>
ClipboardCopyIcon<br>
ClipboardListIcon<br>
ClockIcon<br>
CloudIcon<br>
CloudDownloadIcon<br>
CloudUploadIcon<br>
CodeIcon<br>
CogIcon<br>
CollectionIcon<br>
ColorSwatchIcon<br>
CreditCardIcon<br>
CubeIcon<br>
CubeTransparentIcon<br>
CurrencyBangladeshiIcon<br>
CurrencyDollarIcon<br>
CurrencyEuroIcon<br>
CurrencyPoundIcon<br>
CurrencyRupeeIcon<br>
CurrencyYenIcon<br>
CursorClickIcon<br>
DatabaseIcon<br>
DesktopComputerIcon<br>
DeviceMobileIcon<br>
DeviceTabletIcon<br>
DocumentIcon<br>
DocumentAddIcon<br>
DocumentDownloadIcon<br>
DocumentDuplicateIcon<br>
DocumentRemoveIcon<br>
DocumentReportIcon<br>
DocumentSearchIcon<br>
DocumentTextIcon<br>
DotsCircleHorizontalIcon<br>
DotsHorizontalIcon<br>
DotsVerticalIcon<br>
DownloadIcon<br>
DuplicateIcon<br>
EmojiHappyIcon<br>
EmojiSadIcon<br>
ExclamationIcon<br>
ExclamationCircleIcon<br>
ExternalLinkIcon<br>
EyeIcon<br>
EyeOffIcon<br>
FastForwardIcon<br>
FilmIcon<br>
FilterIcon<br>
FingerPrintIcon<br>
FireIcon<br>
FlagIcon<br>
FolderIcon<br>
FolderAddIcon<br>
FolderDownloadIcon<br>
FolderOpenIcon<br>
FolderRemoveIcon<br>
GiftIcon<br>
GlobeIcon<br>
GlobeAltIcon<br>
HandIcon<br>
HastagIcon<br>
HeartIcon<br>
HomeIcon<br>
IdentificationIcon<br>
InboxIcon<br>
InboxInIcon<br>
InformationCircleIcon<br>
KeyIcon<br>
LibraryIcon<br>
LightBulbIcon<br>
LightningBoltIcon<br>
LinkIcon<br>
LocationMarkerIcon<br>
LockClosedIcon<br>
LockOpenIcon<br>
LoginIcon<br>
LogoutIcon<br>
MailIcon<br>
MailOpenIcon<br>
MapIcon<br>
MenuIcon<br>
MenuAlt1Icon<br>
MenuAlt2Icon<br>
MenuAlt3Icon<br>
MenuAlt4Icon<br>
MicrophoneIcon<br>
MinusIcon<br>
MinusCircleIcon<br>
MinusSmIcon<br>
MoonIcon<br>
MusicNoteIcon<br>
NewspaperIcon<br>
OfficeBuildingIcon<br>
PaperAirplaneIcon<br>
PaperClipIcon<br>
PauseIcon<br>
PencilIcon<br>
PencilAltIcon<br>
PhoneIcon<br>
PhoneIncomingIcon<br>
PhoneMissedCallIcon<br>
PhoneOutgoingIcon<br>
PhotographIcon<br>
PlayIcon<br>
PlusIcon<br>
PlusCircleIcon<br>
PlusSmIcon<br>
PresentationChartBarIcon<br>
PresentationChartLineIcon<br>
PrinterIcon<br>
PuzzleIcon<br>
QrcodeIcon<br>
QuestionMarkCircleIcon<br>
ReceiptRefundIcon<br>
ReceiptTaxIcon<br>
RefreshIcon<br>
ReplyIcon<br>
RewindIcon<br>
RssIcon<br>
SaveIcon<br>
SaveAsIcon<br>
ScaleIcon<br>
ScissorsIcon<br>
SearchIcon<br>
SearchCircleIcon<br>
SelectorIcon<br>
ServerIcon<br>
ShareIcon<br>
ShieldCheckIcon<br>
ShieldExclamationIcon<br>
ShoppingBagIcon<br>
ShoppingCartIcon<br>
SortAscendingIcon<br>
SortDescendingIcon<br>
SparklesIcon<br>
SpeakerPhoneIcon<br>
StarIcon<br>
StatusOfflineIcon<br>
StopIcon<br>
SunIcon<br>
SupportIcon<br>
SwitchHorizontalIcon<br>
SwitchVerticalIcon<br>
TableIcon<br>
TagIcon<br>
TemplateIcon<br>
TerminalIcon<br>
ThumbDownIcon<br>
ThumbUpIcon<br>
TicketIcon<br>
TranslateIcon<br>
TrashIcon<br>
TrendingDownIcon<br>
TrendingUpIcon<br>
TruckIcon<br>
UploadIcon<br>
UserIcon<br>
UserAddIcon<br>
UserCircleIcon<br>
UserGroupIcon<br>
UserRemoveIcon<br>
UsersIcon<br>
VariableIcon<br>
VideoCameraIcon<br>
ViewBoardsIcon<br>
ViewGridIcon<br>
ViewGridAddIcon<br>
ViewListIcon<br>
VolumeOffIcon<br>
VolumeUpIcon<br>
WifiIcon<br>
XIcon<br>
XCircleIcon<br>
XIconIcon<br>
ZoomInIcon<br>
ZoomOutIcon<br>