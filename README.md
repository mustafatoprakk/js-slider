# html

```
<!doctype html>
<html lang="en">
  <head>
    <!-- Required meta tags -->
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1">

    <!-- Bootstrap CSS -->
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.1.3/dist/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-1BmE4kWBq78iYhFldvKuhfTAU6auU8tT94WrHftjDbrCEXSU1oBoqyl2QvZ6jIW3" crossorigin="anonymous">
    <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/bootstrap-icons@1.7.2/font/bootstrap-icons.css">

    <title>Slider</title>
  </head>
  <body>

    <div class="container mt-5 mb-5">
      <div class="card">
        <img src="" id="image" class="card-img-top" alt="...">
        <div class="card-body">
          <h5 class="card-title" id="cars_name"></h5>
          <p class="card-text" id="cars_explanation"></p>
          <a href="#" class="btn btn-primary" id="read_more">Read More</a>
        </div>
        <div class="text-center mb-3">
          <a href="#" class="" id="go_left" ><i class="bi bi-arrow-left-circle-fill" style="font-size: 50px;"></i></a>
          <a href="#" class="" id="go_right" ><i class="bi bi-arrow-right-circle-fill" style="font-size: 50px;"></i></a>
        </div>
      </div>
    </div>

    <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.1.3/dist/js/bootstrap.bundle.min.js" integrity="sha384-ka7Sk0Gln4gmtz2MlQnikT1wXgYsOg+OMhuP+IlRH9sENBO0LRn5q+8nbTov4+1p" crossorigin="anonymous"></script>
    <script src="app.js"></script>
  </body>
</html>
```



# js #
```
let cars=[
    {
        name:"Togg",
        explanation:"Dünyanın en iyi elektirikli arabası karşınızda TOGG!!!",
        image:"https://picsum.photos/id/1037/400/200",
        id:1
    },
    {
        name:"BMW",
        explanation:"Lorem ipsum dolor sit amet consectetur adipisicing elit. Eos, provident.Lorem ipsum dolor sit amet consectetur adipisicing elit. Eos, provident.Lorem ipsum dolor sit amet consectetur adipisicing elit. Eos, provident.",
        image:"https://picsum.photos/id/835/600/300",
        id:2
    },
    {
        name:"Audi",
        explanation:"Lorem ipsum dolor sit amet consectetur adipisicing elit. Eos, provident.",
        image:"https://picsum.photos/id/637/600/300",
        id:3
    }
]

const carsImage=document.querySelector("#image")
const carsName=document.querySelector("#cars_name")
const carsExplanation=document.querySelector("#cars_explanation")
const readMore=document.querySelector("#read_more")
const goRight=document.querySelector("#go_right")
const goLeft=document.querySelector("#go_left")

var index=0
var carsCount=cars.length
var settings={
    duration: 2000,
    random: true
}

slide(settings)

// buton ile yönlendirme
goRight.addEventListener("click",function(){
    index++;
    showSlide(index)
})
goLeft.addEventListener("click",function(){
    index--;
    showSlide(index)
})

function showSlide(i){

    // index değeri 0 olduğunda araba sayısında 1 çıkartılıp indexine 2 yazılır
    if(i < 0){
        index=carsCount-1
    }
    if(i >= carsCount){
        index=0
    }

    carsName.textContent=cars[index].name
    carsImage.setAttribute("src",cars[index].image)
    carsExplanation.textContent=cars[index].explanation
}

// otomatik yönlendirme
function slide(s){

    var prev;
    // setInterval - belli bir süreden sonra hep devam eder
    setInterval(function(){
        if(settings.random){
            do{ // tekrarı gelmeyecek
                index=Math.floor(Math.random() * carsCount)
            }while(index==prev){
                prev=index
            }
        }else{

        }
        showSlide(index)
    },settings.duration)
}
```
