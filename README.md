import-html.js
===

![](https://circleci.com/gh/yfxie/import-html.svg?style=svg)
[![npm version](https://badge.fury.io/js/import-html.js.svg)](https://badge.fury.io/js/import-html.js)
![](http://img.badgesize.io/yfxie/import-html/master/import-html.min.js.svg?compression=gzip)

for frontend beginners who didn't know framework to use the import feature in HTML.

*Read this in other languages: [English](README.md), [繁體中文](README.zh-TW.md).*

Usage
---

1. load the script in HTML:
```
<body>
  ...
  <!-- place before the end of body tag is suggested -->
  <script src="import-html.min.js"></script>
</body>
```

2. prepare template HTML:
```
<header>
  <h1>Awesome Page</h1>
</header>
```
```
<footer>
  <p>© 2018 UXabc.</p>
</footer>
```

3. import the template by using HTML comment with special syntax `<!-- import file.html -->`:
```
<body>
  <!-- import header.html -->
  Page content
  <!-- import footer.html -->
</body>
```

4. the page will be:
```
<body>
  <header>
    <h1>Awesome Page</h1>
  </header>
  Page content
  <footer>
    <p>© 2018 UXabc.</p>
  </footer>
</body>
```


Features
---
- **Light-weight**: ![](http://img.badgesize.io/yfxie/import-html/master/import-html.min.js.svg)
![](http://img.badgesize.io/yfxie/import-html/master/import-html.min.js.svg?compression=gzip)
- support nested import.
- when all templates loaded, `import-html-loaded` class will be added to `<html>`.
- JS callback by using `ImportHTML.ready(callback)`

Tips
---
for some situations, you probably encounter flicker issue.
for that, set opacity to 0 to hide all HTML elements and reset opacity after all templates loaded by using `ImportHTML.ready`:

```
<head>
  <!-- import include/head.html -->
  <script>document.documentElement.style.opacity = 0;</script>
</head>
<body>
  ...
  <script src="import-html.min.js"></script>
  <script>
    ImportHTML.ready(function() {
      document.documentElement.style.removeProperty('opacity');
    });
  </script>
</body>

```

Q&A
---

**Why not use browser native Promise?**

to support legacy browsers like IE.

Todo
---
- [ ] demo page
- [ ] more detail description
- [ ] can pass variables
