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
ie-love depends on [jQuery 1.x.x](https://jquery.com/download/). We don't include this in the package because there's a pretty decent chance you're already including it. If you're not though, you'll need to.

The following would load jQuery 1.x.x and ie-love for IE8 and below, and load jQuery 2.x.x for IE9 and above.

```html
<!doctype html>
<html>
  <head>
    <title>ie-love</title>
  </head>
  <body>

    <div>Hello World</div>

    <!--[if lt IE 9]>
      <script src="http://code.jquery.com/jquery-1.12.0.min.js"></script>
      <script src="ie-love.min.js">
    <![endif]-->

    <!--[if gt IE 8]>
      <script src="http://code.jquery.com/jquery-2.2.0.min.js">
    <![endif]-->
  </body>
</html>
```

### Included Polyfills (ordered)
- [Selectivizr 2](https://github.com/corysimmons/selectivizr2)
- [Respond.js](https://github.com/scottjehl/Respond)
- [html5shiv](https://github.com/aFarkas/html5shiv)
- [calc-polyfill](https://github.com/closingtag/calc-polyfill)

### Isn't this a huge download?
Not really. It's around a 30kb download and if the user happens to have it cached (by getting it from somewhere like CDNjs) then they won't even download it.

To put it in perspective jQuery is around 100kb and takes about 300ms to load the first time, and 100ms to load every time after that, on my crappy cable connection.

I think most IE8 and below users would prefer the small wait time to the unviewable experience they're used to from most websites.

### But I don't need all those polyfills!
Okay, so build/maintain/CDN-cache your own package. The links to the polyfills are above.

This package was just created so I could offer decentish support to old-ie users without having to do any work.

### Wasn't this already done?
This project was definitely inspired by [lt-ie-9](https://github.com/shinnn/lt-ie-9) but lt-ie-9 isn't maintained anymore and didn't have all the polyfills ie-love has. In particular I needed [calc-polyfill](https://github.com/closingtag/calc-polyfill) on almost every site I made so it didn't make sense to have 2 http requests (ie-lt-9 and calc-polyfill).

That got me thinking about all the times I've had to track down a polyfill and create a new http request or bundle all my polyfills or xyz, and it upset me to the point of just making one polyfill to rule them all.
