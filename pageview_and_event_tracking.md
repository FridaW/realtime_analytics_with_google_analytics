# realtime_analytics_with_google_analytics

Google Analytics has three code versions, one is ga.js ("traditional" asynchronous code) in which we have to use _gaq.push,
one is analytics.js in which we need to use ga send, one is gtag.js (2017, new code version) in which we use gtag.


This is a very simple example on how to analyze pageview and video tracking (which users are "playing videos") using ga.js.

### Get tracking ID of Google Analytics account

Sign into Analytics account
Click Admin
Select an account from the menu in the ACCOUNT column.
Select a property from the menu in the PROPERTY column.
User PROPERTY, click TRACKING INFO > TRACKING CODE. Your tracking ID is displayed at the top of the page.

### JavaScript tracking snippet

If working for wordpress, just add these code into the theme, after <head> of the page you want to track.
```
<!-- Google Analytics -->
<script>
(function(i,s,o,g,r,a,m){i['GoogleAnalyticsObject']=r;i[r]=i[r]||function(){
(i[r].q=i[r].q||[]).push(arguments)},i[r].l=1*new Date();a=s.createElement(o),
m=s.getElementsByTagName(o)[0];a.async=1;a.src=g;m.parentNode.insertBefore(a,m)
})(window,document,'script','https://www.google-analytics.com/analytics.js','ga');

ga('create', 'UA-XXXXX-Y', 'auto');
ga('send', 'pageview');
</script>
<!-- End Google Analytics -->
```

### Page tracking

```
ga('send', 'pageview', [page], [fieldsObject]);
```

### Event tracking

```
ga('send', 'event', [eventCategory], [eventAction], [eventLabel], [eventValue], [fieldsObject]);
```
For example:
```
ga('send', 'event', 'Videos', 'play', 'Fall Campaign');
```
Or
```
ga('send', {
  hitType: 'event',
  eventCategory: 'Videos',
  eventAction: 'play',
  eventLabel: 'Fall Campaign'
});
```

Tracking outbound links and forms can be tricky because most browsers will stop executing JavaScript on the current page once a new page starts to load. 
One solution to this problem is to set the transport field to beacon:
```
function handleOutboundLinkClicks(event) {
  ga('send', 'event', {
    eventCategory: 'Outbound Link',
    eventAction: 'click',
    eventLabel: event.target.href,
    transport: 'beacon'
  });
}
```
Also, To be notified when a hit is done sending, you set the hitCallback field. 
hitCallback is a function that gets called as soon as the hit has been successfully sent.

For example:
```
ga('send', 'pageview');
ga('send', 'event', 'Video', 'play', 'the label', { 'transport': 'beacon', 'hitCallback': function(){} });
```

### Integration with JWplayer

Make sure you have Google Analytics JS on your page. Then simply include the ga:{} block in your configuration options to enable it. 

Such like:
```
/*add these code to the place jwplayer will be placed*/
var playerInstance = jwplayer("myElement");
playerInstance.setup({
    file: "/uploads/example.mp4",
    image: "/uploads/example.jpg",
    ga: {} 
});
```
For example:
```
<div class="container container-16x9">
  <script src="">
  jwplayer("jwplayerid").setup({  
    "label" : "the label",
    "title" : "the title" ,
    "mediaid"  : "media id",     
    "flashplayer": "",
    "image": "",
    "ga" : {label : 'mediaid'},  
    "viral.oncomplete":"false",       
    "viral.onpause":"false"       
  });       
  </script>
</div>

<style>
/*Designed Video--make it responsive*/
.container {
  position: relative;
  overflow: hidden;
  margin-bottom: 15px;
}
 
/* 16x9 Aspect Ratio */
.container-16x9 {
  padding-bottom: 56.25%;
}
.jwplayer { width: 98% !important;height: 98% !important; position: absolute !important;} 

</style>
```

