<h1 align="center">ie-love</h1>

<p align="center">
  Combo polyfill for IE8 and below.
</p>

### Why?
IE8 and below are intentionally getting shafted. It's silly. I'm sure people on those older browsers either don't have the means or aren't tech savvy enough to upgrade their browser.

I'm not saying we should go out of our way to develop for them - we did that :poop: for years - but if giving them a viewable experience means adding one polyfill in a conditional comment (they're the only ones who will download it) then why not?

### Installation

##### Bower
- `bower install --save ie-love`

##### Node
- `npm install --save ie-love`

### Usage
ie-love goes at the bottom of the page (right before the `</body>` closing tag). As such, we can't bundle [html5shiv](https://github.com/aFarkas/html5shiv) (support for HTML5 elements) with it. Unfortunately html5shiv **has** to go in the `<head>`.

The [best way](https://github.com/Modernizr/Modernizr/issues/878#issuecomment-41448059) to include html5shiv in your project is to plop [this one line](https://github.com/aFarkas/html5shiv/blob/master/dist/html5shiv.min.js#L4) in between some `<script>` tags in your `<head>` after all your stylesheets. I like to add a little comment in front of it notating what it is and what version it's on.

ie-love also depends on [jQuery 1.x.x](https://jquery.com/download/). We don't include this in the package because there's a pretty decent chance you're already including it. If you're not though, you'll need to.

### Example

The following would load html5shiv, jQuery 1.x.x, and ie-love for IE8 and below, and load jQuery 2.x.x for IE9 and above.

**Note:** If you're not using jQuery for anything, you don't need to load it for IE9 and above.

```html
<!doctype html>
<html>
  <head>
    <title>ie-love</title>
    <link rel="stylesheet" href="style.css">
    <!--[if lt IE 9]>
      <script> /* html5shiv - 3.7.3 */ !function(a,b){function c(a,b){var c=a.createElement("p"),d=a.getElementsByTagName("head")[0]||a.documentElement;return c.innerHTML="x<style>"+b+"</style>",d.insertBefore(c.lastChild,d.firstChild)}function d(){var a=t.elements;return"string"==typeof a?a.split(" "):a}function e(a,b){var c=t.elements;"string"!=typeof c&&(c=c.join(" ")),"string"!=typeof a&&(a=a.join(" ")),t.elements=c+" "+a,j(b)}function f(a){var b=s[a[q]];return b||(b={},r++,a[q]=r,s[r]=b),b}function g(a,c,d){if(c||(c=b),l)return c.createElement(a);d||(d=f(c));var e;return e=d.cache[a]?d.cache[a].cloneNode():p.test(a)?(d.cache[a]=d.createElem(a)).cloneNode():d.createElem(a),!e.canHaveChildren||o.test(a)||e.tagUrn?e:d.frag.appendChild(e)}function h(a,c){if(a||(a=b),l)return a.createDocumentFragment();c=c||f(a);for(var e=c.frag.cloneNode(),g=0,h=d(),i=h.length;i>g;g++)e.createElement(h[g]);return e}function i(a,b){b.cache||(b.cache={},b.createElem=a.createElement,b.createFrag=a.createDocumentFragment,b.frag=b.createFrag()),a.createElement=function(c){return t.shivMethods?g(c,a,b):b.createElem(c)},a.createDocumentFragment=Function("h,f","return function(){var n=f.cloneNode(),c=n.createElement;h.shivMethods&&("+d().join().replace(/[\w\-:]+/g,function(a){return b.createElem(a),b.frag.createElement(a),'c("'+a+'")'})+");return n}")(t,b.frag)}function j(a){a||(a=b);var d=f(a);return!t.shivCSS||k||d.hasCSS||(d.hasCSS=!!c(a,"article,aside,dialog,figcaption,figure,footer,header,hgroup,main,nav,section{display:block}mark{background:#FF0;color:#000}template{display:none}")),l||i(a,d),a}var k,l,m="3.7.3",n=a.html5||{},o=/^<|^(?:button|map|select|textarea|object|iframe|option|optgroup)$/i,p=/^(?:a|b|code|div|fieldset|h1|h2|h3|h4|h5|h6|i|label|li|ol|p|q|span|strong|style|table|tbody|td|th|tr|ul)$/i,q="_html5shiv",r=0,s={};!function(){try{var a=b.createElement("a");a.innerHTML="<xyz></xyz>",k="hidden"in a,l=1==a.childNodes.length||function(){b.createElement("a");var a=b.createDocumentFragment();return"undefined"==typeof a.cloneNode||"undefined"==typeof a.createDocumentFragment||"undefined"==typeof a.createElement}()}catch(c){k=!0,l=!0}}();var t={elements:n.elements||"abbr article aside audio bdi canvas data datalist details dialog figcaption figure footer header hgroup main mark meter nav output picture progress section summary template time video",version:m,shivCSS:n.shivCSS!==!1,supportsUnknownElements:l,shivMethods:n.shivMethods!==!1,type:"default",shivDocument:j,createElement:g,createDocumentFragment:h,addElements:e};a.html5=t,j(b),"object"==typeof module&&module.exports&&(module.exports=t)}("undefined"!=typeof window?window:this,document);</script>
    <![endif]-->
  </head>
  <body>

    <article>Hello World</article>

    <!--[if lt IE 9]>
      <script src="https://code.jquery.com/jquery-1.12.3.min.js"></script>
      <script src="bower_components/ie-love/dist/ie-love.min.js"></script>
    <![endif]-->

    <!--[if gt IE 8]>
      <script src="https://code.jquery.com/jquery-2.2.3.min.js">
    <![endif]-->
  </body>
</html>
```

### Included Polyfills (ordered)
- [html5shiv](https://github.com/aFarkas/html5shiv)
- [calc-polyfill](https://github.com/closingtag/calc-polyfill)
- [Selectivizr 2](https://github.com/corysimmons/selectivizr2)
- [Respond.js](https://github.com/scottjehl/Respond)

### How can I test my site in IE7-IE8?
- Use a Virtual Machine
  - Learn how to install and setup VMs with [VirtualBox](https://www.virtualbox.org/). It's cross-platform and there are probably lots of [YouTube videos](https://www.youtube.com/results?search_query=virtualbox) on it so grab a :coffee: and enjoy.
  - Microsoft offers [Windows images](https://dev.windows.com/en-us/microsoft-edge/tools/vms) specifically so you can try out old browsers.
  - [IEVMS](https://github.com/xdissent/ievms) is the incredibly easy way to get/maintain these VMs.
- [BrowserStack](http://browserstack.com) is expensive and **slow**, but if you can't figure out the other techniques you can use it. I highly suggest you figure out how to use VMs though. It's a skill worth learning.

> I'm not even sure how to test in IE6 anymore, but... seriously?

### Isn't this a huge download?
Not really. It's around 25kb. If the user happens to have it cached (by getting it from somewhere like CDNjs) then they won't even download it.

To put it in perspective jQuery is around 100kb and takes about 300ms to load the first time, and 100ms to load every time after that, on my crappy 15Mbps cable connection.

I think most IE8 and below users would prefer the small wait time to the unviewable experience they're used to from most websites.

> It should be stressed that IE8 and below users are the only ones who will even experience this small download.

### But I don't need all those polyfills!
Okay, so build/maintain/CDN-cache your own package. The links to the polyfills are above.

This package was just created so I could offer decentish support to old-ie users without having to do any work.

### Wasn't this already done?
This project was definitely inspired by [lt-ie-9](https://github.com/shinnn/lt-ie-9) but lt-ie-9 isn't maintained anymore and didn't have all the polyfills ie-love has. In particular I needed [calc-polyfill](https://github.com/closingtag/calc-polyfill) on almost every site I made so it didn't make sense to have 2 http requests (ie-lt-9 and calc-polyfill).

That got me thinking about all the times I've had to track down a polyfill and create a new http request or bundle all my polyfills or xyz, and it upset me to the point of just making one polyfill to rule them all.

### Caveats
The goal of this project isn't to fix everything, but you should probably be aware of a few things that polyfills just can't do. If you're particularly awesome, head over to the repos and see if you can fix some of their problems. I update ie-love's polyfills regularly.

- calc-polyfill doesn't work with [media queries](https://github.com/closingtag/calc-polyfill#media-queries)
