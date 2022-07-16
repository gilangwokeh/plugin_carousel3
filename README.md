# plugin-jquery

# jQuery carousel v1.0.10
Jquery carousel and left button, right button using multiple images

# Options

# demo 
`below for plugin demo code`

### component FIle HTML:

`html code below :`

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8"name="viewport" content="width=device-width, initial-scale=1.0" meta http-equiv="X-UA-Compatible" content="IE=edge">
  <title>PLUGIN</title>
  <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/bootstrap@5.2.0-beta1/dist/css/bootstrap.min.css  ">
  <link rel="stylesheet" href="./demo/style/style.css">
</head>
<body>
  <header>
    <h1 class="slide-h1">Carousel Jquery</h1>
  </header>
    <div class="container">
      <button class="prev-span">
        <img src="./demo/image/back1.svg" alt="Prev" id="prev">
      </button>
      <div class="slider">
        <div id="slide">
          <div class="slide-copy">
          </div>
          <img src="./demo/image/image1.jpg">
        </div>
        <div id="slide">
          <div class="slide-copy">
          </div>
          <img src="./demo/image/image2.jpg">
        </div>
        <div id="slide">
          <div class="slide-copy">
          </div>
          <img src="./demo/image/image3.jpg">
        </div>
        <div id="slide">
          <div class="slide-copy">
          </div>
          <img src="./demo/image/image4.jpg">
        </div>
        <div id="slide">
          <div class="slide-copy">
          </div>
          <img src="./demo/image/image5.jpg">
        </div>
      </div>
      <button class="next-span">
        <img src="./demo/image/forward.svg" alt="Next" id="next">
      </button>
    </div>    
    <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.6.0/jquery.min.js"></script>
    <script src="https://cdn.jsdelivr.net/npm/jquery-validation@1.19.5/dist/jquery.validate.js"></script>
  <script src="./index.js"></script>
</body>
</html>

```
### Component File SCSS
`SCSS code below :`

```scss
body {
  margin: 0 auto;
  padding: 0;
  overflow-x: hidden;
  font-family: sans-serif;
  line-height:1.6em;
  .slide-h1{
    margin-top: 20px;
  }
  a{
    color:#fff;
    text-decoration:none;
  }
  h1{
    text-align:center;
    margin-bottom:20px;
  }
  h4{
    text-align: center;
    margin: 40px;
  }
  .paragraph-carousel{
    width: 1000px;
    height: 100px;
    text-align: justify;
    position: relative;
    left: 140px;
    font-family: sans-serif;
  }
  .container{
    width:980px;
    margin:20px auto;
    overflow:hidden;
    #slider{
      width:940px;
      height:350px;
      position:relative;
      overflow:hidden;
      float:left;
      padding:0px;
      border:#666 solid 2px;
      border-radius:5px;
      img {
        width:940px;
        height:350px;
      }
      .slide{
        position:absolute;
        .slide-copy{
          display: none;
        }
      }
    }
  }
  .prev-span {
    background-color: #666;
    width: 40px;
    height: 40px;
    position: absolute;
    float:right;
    left: 193px;
    margin-top:160px;
    border-radius:40px;
    z-index:100;
  }
  .prev-span:hover , .next-span:hover {
    cursor: pointer;
    background-color: rgb(161, 153, 153);
    transition: all 0.45s;
    width: 50px;
    border-radius: 50px;
  }
  .next-span {
    background-color: #666;
    width: 40px;
    height: 40px;
    position: absolute;
    float:left;
    right: 210px;
    margin-top:160px;
    border-radius:40px;
    z-index:100;
  }
}
```

### component File JQUERY:

`jquery code below :`


```javascript

$(document).ready(function(){
	let speed = 600;			
	let autoswitch = true;		
	let autoswitch_speed = 6000	d
	
	$('.slide').first().addClass('active');
	
	$('.slide').hide();
	
	$('.active').show();
	
	$('#next').on('click', nextSlide);
	
	$('#prev').on('click', prevSlide);
	
	if(autoswitch == true){
		setInterval(nextSlide,autoswitch_speed);
	}
	
	function nextSlide(){
		$('.active').removeClass('active').addClass('oldActive');
		if($('.oldActive').is(':last-child')){
			$('.slide').first().addClass('active');
		} else {
			$('.oldActive').next().addClass('active');
		}
		$('.oldActive').removeClass('oldActive');
		$('.slide').fadeOut(1000);
		$('.active').fadeIn(1000);
	}

	function prevSlide(){
		$('.active').removeClass('active').addClass('oldActive');
		if($('.oldActive').is(':first-child')){
			$('.slide').last().addClass('active');
		} else {
			$('.oldActive').prev().addClass('active');
		}
		$('.oldActive').removeClass('oldActive');
		$('.slide').fadeOut(1000);
		$('.active').fadeIn(1000);
	}
});


```
```
