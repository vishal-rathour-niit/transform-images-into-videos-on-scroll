# video generator from images on window scroll

library for to convert images series to video and play on window scroll, in single or multple. 

 **Note :-all rendering image(desktop and mobile) should be name like - smog (1).jpg ,  smog (2).jpg**

## HTML

```
<canvas id="video_pls"></canvas> #canvas
<div class="screen-play-area" id="canvasPlay"></div> #canvas container
<div id="image_pre_loader"></div>  # image pre loader container
            
```
## JS Code

```
## options

const options = {
    containerID:'#canvasPlay',
    canvasID:'#video_pls',
    live_url:'assest/img/',
    responsiveStart:767,
    imagePreLoader:'#image_pre_loader',
    desktop:{
        folderName:'fire-desktop',
        image_Prefix:'video',
        startPos:1,
        endPos:601,
        animationGap:50
    },
    mobile:{
        folderName:'fire-mobile',
        image_Prefix:'video',
        startPos:1,
        endPos:601,
        animationGap:50
    },
    render: function(data) {
        console.log(data.status) # retrun start and end while resize rendering start
    }
}
            
  ```
  ## Initialize library
  ```
   const video = new videoMaker(options);
   video.init();
   ```

## video.refresh();
call obj.refresh(); on window resize for rerendiring.

## options {}

```
containerID # pass container for rendering element
canvasID # canvas id or class of HTML canvas
live_url # image URL 
responsiveStart # responsive start position default is 767px
imagePreLoader  # image pre loader container for loading images
desktop:{}  # for desktop rendering
mobile:{} # for mobile rendering call if you pass responsive value larger than 0px

desktop:{
    folderName:'fog',  # image folder name for desktop  {assest/img/`fog`}
    image_Prefix:'smog', # image prefix name image stating like `smog (1)`
    startPos:1,   # start pos from rendering start
    endPos:100,   # end pos from rendering end
    animationGap:30  # video animation space default is 60px
}

desktop:{
    folderName:'fog-mobile',  # image folder name for mobile  {assest/img/`fog-mobile`}
    image_Prefix:'smog', # image prefix name image stating like `smog (1)`
    startPos:1,   # start pos from rendering start
    endPos:100,   # end pos from rendering end
    animationGap:30  # video animation space default is 60px
}

```

** Live Demo [https://www.indiatoday.in/interactive/immersive/delhi-air-quality-smog-capital/]
