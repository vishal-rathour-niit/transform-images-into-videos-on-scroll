# Dynamic Video Creation: Transform Images into Videos on browser Scroll

Library to convert a series of images into a video and play it on window scroll, either as a single video or multiple.

 **Note: All rendered images (for desktop and mobile) should be named like smog (1).jpg, smog (2).jpg, and so on.**

# install by NPM/Yarn

NPM
```
npm i images-to-video-convert-on-window-scroll
```
YARN
```
yarn add images-to-video-convert-on-window-scroll
```
import

```
import videoMaker from 'images-to-video-convert-on-window-scroll'
```

## HTML

add js file 

```
 <script src="lib/videomaker.min.js"></script>
```

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
    type:'.png',
    rootMargin:'0%  0px -100% 0px',
    root:null,
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
call obj.refresh(); for hard refresh.

## options {}

```
containerID # pass container for rendering element
canvasID # canvas id or class of HTML canvas
live_url # image URL 
responsiveStart # responsive start position default is 767px
imagePreLoader  # image pre loader container for loading images
type:'.png' #  pass image type default is '.jpg'
rootMargin:'0%  0px -100% 0px'  # set animaton start offset default is '0px'
root:null  #  pass root as html element defalut is body, if you pass null by defalut set root to html body
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
## isDyanamicId
If you want to set a dynamic ID for images, pass it as a parameter ```isDyanamicId:true``` and ```dyanamicIDPrefic:'smog_id_'```

## contentData
If you want to add text data between images, include it accordingly.

```
contentSetHeight:500,  // size for text container
contentData:[
{
        "key":'5',  // for desktop
        "mobile_key":'6',  // for mobile 
        "content":'<p>demo 1</p>'
    },
    {
        "key":"20",
        "mobile_key":'27',
        "content":'<p class="caps">demo 2<p>'
    },
],
```

## ON method 
If you want to check if the reload has started, this method works like the render method but returns an extra parameter: ```view```, which specifies the current view (desktop or mobile).

```
obj.on('re-loading',function({status,view}){
   
});

```

The ```on``` method returns two parameters: status (either 'start' or 'end') and view (either 'mobile' or 'desktop').

# Live Demo
  1:- https://www.indiatoday.in/interactive/immersive/chandrayaan-3-landing-india-isro-historic-moment-on-the-moon/
  2:- https://www.indiatoday.in/interactive/immersive/ram-mandir-darshan-ramjanmabhoomi-ayodhya-2024-travel-guide
  3:- https://www.indiatoday.in/interactive/immersive/delhi-air-quality-smog-capital/


