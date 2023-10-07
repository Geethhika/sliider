<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Slider | by Asish</title>
    <style>
        *
{
    margin:0;
    padding:0;
    box-sizing: border-box;
}

body{
    background: linear-gradient(to right,  orange ,rgb(231, 99, 99));
    display: flex;
    justify-content: center;
    align-items: center;
    height:100vh;

}

.container
{
       
   position:relative;
}
 button{
     position:absolute;
     height:50px;
     width:50px;
     font-size:40px;
     color:red;
     background-color: rgba(0,0,0,.1);
    border:none;
    outline: none;
     cursor:pointer;
     top:45%;
     border-radius:50%;

 }
 button:hover{
     box-shadow: 0px 0px 5px rgb(117, 76, 76);
     background-color: rgba(0,0,0,.5);
     transition: .2s linear;
 }

#right{
     right:5px;  z-index: 1;
   
 }

 #left{
    left:5px;
  z-index: 1;
}

.image_container{
    height:100%;
    overflow: hidden;
    /* border: 2px solid red; */
}

.image{
    display:none;
}

.active
{
    display:block;
    animation: asish 5s linear;
    
}

@keyframes asish
{
    0%{
        opacity: 0;
        transform: scale(1.5);
    }
    100%{
        opacity: 1;
        transform: scale(1);
    }

  
}

img{
     max-width: 100%;
     max-height: 100%;
     display: block;
}

.footer
{
    position: absolute;
    height: 60px;
    width: 100%;
    background-color: rgba(0,0,0,.3);
    bottom: 0;
    left:0;
    text-align: center;
    font-size:30px;
    color:white;
    padding:5px;
    
}


    </style>
</head>

<body>

    <div class="container">
        <button id="left" onclick="move()"> <</button>
                <div class="image_container">

                    <div class="image active" data-iamge-type="Flower">
                        <img src="https://img.freepik.com/free-photo/purple-osteospermum-daisy-flower_1373-16.jpg?size=626&ext=jpg&uid=R119719380&ga=GA1.2.109696452.1691767165&semt=sph">
                    </div>

                    <div class="image" data-iamge-type="Mountain"><img src="https://img.freepik.com/free-photo/mesmerizing-scenery-green-mountains-with-cloudy-sky-surface_181624-27189.jpg?w=900&t=st=1696700706~exp=1696701306~hmac=3eeb5734da0702d4592981e0bf36e97e3614c13864e6c1684ecc8339d3dc5eaf"></div>

                    <div class="image" data-iamge-type="Fish"><img src="https://img.freepik.com/free-photo/beautiful-fish-undersea_23-2150737651.jpg?size=626&ext=jpg&uid=R119719380&ga=GA1.2.109696452.1691767165&semt=sph"></div>

                    <div class="image" data-iamge-type="Dragon-fly"><img src="https://img.freepik.com/free-vector/vector-realistic-gomphus-vulgatissimus-dragonfly-close-up-top-view-isolated-white-background_1284-46438.jpg?size=626&ext=jpg&uid=R119719380&ga=GA1.2.109696452.1691767165&semt=ais"></div>

                    <div class="image" data-iamge-type="Nature"><img src="https://img.freepik.com/free-photo/wide-angle-shot-single-tree-growing-clouded-sky-during-sunset-surrounded-by-grass_181624-22807.jpg?w=900&t=st=1696693102~exp=1696693702~hmac=be96b3476d7da673c07b5d6e6faed86cce3088051c86e8fce0a60d63f586405a"></div>
                </div>

        <button id="right"  onclick="move()" > > </button>

        <div class="footer">Flower</div>
    </div>



</body>
<script>
    let image = document.querySelectorAll('.image');
let btn = document.querySelectorAll('button');
let footer = document.getElementsByClassName('footer')[0];

let no_of_image = image.length;
let curr_image_index = 0;

for( b of btn)
b.addEventListener('click',move)

function move(e)
{
    if(e.target.id =='left')
    {
        if(curr_image_index>0)
        {
            image[curr_image_index].classList.remove("active");
            curr_image_index--;
            image[curr_image_index].classList.add("active");
            
        }
        else{
            return;
        }
        
    }
  


   if(e.target.id =='right')
    {
        if(curr_image_index < no_of_image-1)
        {
            image[curr_image_index].classList.remove("active");
            curr_image_index++;
            image[curr_image_index].classList.add("active");
        }
        else{
            return;
        }
    }

    // footer.innerHTML = curr_image_index+1;
    footer.innerHTML = image[curr_image_index].getAttribute('data-iamge-type');
}






</script>
</html>
