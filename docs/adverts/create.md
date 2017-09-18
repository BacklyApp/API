`POST /adverts`<br>
`POST /advert/<advert-id>`

Create a new advert or update an existing one.

# Parameters

| Name | Type | Required | Plans | Description | Example |
|---|---|---|---|---|---|
| style | String | Yes | Free | Advert style.<br><br>Choose from Social `social_v2` or Banner `full_width`. | `'social_v2'`|
| " | " | " | Premium | Choose from the styles above plus Hidden `hidden`. | `'full_width'` |

Used by all styles

| Name | Type | Required | Default | Plans | Description | Example |
|---|---|---|---|---|---|---|
| brand | String | Yes | | | |
| css | String | | `''` | Premium | Custom page CSS. | `'.ad { opacity: 0.5; }'` |
| pixles | String | | `''` | Premium | Custom HTML inserted into HEAD. | `'<script>...'` |
| scripts | String | | `''` | Premium | Custom JavaScript run on page load. | `'alert("Hello")'`|

Used by Social, Social simple, Full Width and Popup message formats.

| Name | Type | Required | Plans | Description | Example |
|---|---|---|---|---|---|
| colors | Array | Yes | | See below.<br><br>Colors used in your advert. | |
| content | Array | Yes | | See below. | |
| cta | Array | | | See below.<br><br>An optional, but recommended call-to-action for your advert. | |
| entry | Array | Yes | | See below. | |

Used by Social, Social simple and Full Width message formats.

| position | String | Yes | | Advert page position.<br><br>`top` or `bottom` when style is Banner<br><br>`top_left`, `top_right`, `bottom_left` or `bottom_right` when style is Social or Social simple. | `'bottom_left'` |

## Colors

| Name | Type | Required | Plans | Description | Example |
|---|---|---|---|---|---|
| background | String | Yes | | Advert background color as a 6 digit hex code. | `'000000'` |
| text | String | Yes | | Advert text color. | `'333333'` |
| button.background | String | When `cta` is present or `style` is `social_v2`. | | Advert button background color / link color. | `'2196f3'` |
| button.text | String | When `cta` is present. | | Advert button text color. | `'e2f1fe'` |

## Content

| Name | Type | Required | Plans | Description | Example |
|---|---|---|---|---|---|
| body | String | When style is Social. | | Text visible when the Social style advert is expanded.<br><br>Can include HTML. | `'Lorem ipsum...'` |
| description | String | When style is Social or Banner. | | Also known as _teaser_.<br><br>Used as the introduction for the Social advert style or as the text on Banner adverts.<br><br>Plain text only. | `'Lorem ipsum...'` |

## Call-to-action

| Name | Type | Required | Plans | Description | Example |
|---|---|---|---|---|---|
| type | String | Yes | Free | The only avaialable option, `button_link`. | `'button_link'` |
| " | " | " | Premium | One of `button_link`, `facebook_like` or `email`, or leave null for no CTA. | `null` |

Button link

| Name | Type | Required | Plans | Description | Example |
|---|---|---|---|---|---|
| target | String | Yes | | Either `blank` to open the link in a new tab or `self` to open in the current tab. | |
| text | String | Yes | | Button label text. | `'Click Here'` |
| url | String | Yes | | URL to navigate visitor to. Must be a valid URL. | `'http://example.com/?r=123'` |
| wiggle | Boolean | Yes | | Whether to wiggle the button or not. Can only be used with Banner adverts. | `true` |

Facebook Like

| Name | Type | Required | Plans | Description | Example |
|---|---|---|---|---|---|
| show_count | Boolean | Yes | | Whether to show the number of likes. | | `true` |
| show_share_button | Boolean | Yes | | Whether to add a share button. | | `true` |
| url | String | Yes | | URL of the page / Facebook page for visitors to like. Must be a valid URL. | | `http://facebook.com/backlyapp` |

Email

| Name | Type | Required | Plans | Description | Example |
|---|---|---|---|---|---|
| text | String | Yes | | Button label text. | `'Click to Subscribe'` |
| submit_text | String | Yes | | Submit button label text. | `'Submit'` |
| placeholder | String | Yes | | E-mail input placeholder text. | `'Enter your e-mail'` |
| webhook_url | String | Yes | | URL of the webhook where to send submissions.<br><br>This could be a Zapir or IFTTT webhook. | `'https://hooks.zapier.com/hooks/catch/abc123/xyz789/'` |

## Entry

| Name | Type | Required | Plans | Description | Example |
|---|---|---|---|---|---|
| animation | String | Yes | | One of `none`, `slide`, `fade` or `flash`. | `'slide'` |
| conditions | Array | | | See below. | |

## Entry conditions

| Name | Type | Required | Plans | Description | Example |
|---|---|---|---|---|---|
| time_on_page | Integer | | Premium | An optional time to delay the entrance of the advert by in seconds. Minimum of 1s, maximum of 60s. | `10` |
