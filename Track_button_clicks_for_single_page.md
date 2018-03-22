# realtime_analytics_with_google_analytics



### Page tracking

For single page, just include :
```
<a href="http://your_button_url.com/" target="_blank" onclick="trackOutboundLink('http://your_button_url.com/')" ><button>click</button></a>
```

to your index.html

### JavaScript tracking snippet

then incluce:
```
/*Global site tag (gtag.js) - Google Analytics*/


	(function(i,s,o,g,r,a,m){i['GoogleAnalyticsObject']=r;i[r]=i[r]||function(){
	(i[r].q=i[r].q||[]).push(arguments)},i[r].l=1*new Date();a=s.createElement(o),
	m=s.getElementsByTagName(o)[0];a.async=1;a.src=g;m.parentNode.insertBefore(a,m)
	})(window,document,'script','https://www.google-analytics.com/analytics.js','ga');

	ga('create', 'UA-XXXXX-Y', 'auto'); // <--- CLIENT GGAA CODE
	ga('send', 'pageview');

	var trackOutboundLink = function(url) {
	  ga('send', 'event', 'outbound', 'click', url, {
	     'transport': 'beacon',
	     'hitCallback': function(){}
	   });

	};

```
to your script.js
