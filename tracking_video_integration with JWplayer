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

