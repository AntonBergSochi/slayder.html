const images = ["11.jpg","12.jpg","13.jpg","14.jpg","15.jpg","16.jpg"];


let activImage = 0;
const sliderPlace = document.querySelector(".slider-line");
const widthOffset = document.querySelector(".slider").clientWidth;
sliderPlace.style.width = 3 * widthOffset + "px";
sliderPlace.style.height =  widthOffset + "px";
sliderPlace.style.left = '-'+widthOffset + "px";
let flag = true;

const initSlayder = () => {
const img = document.createElement("img");
img.alt = "";
img.src = './images/'+ images[activImage];
sliderPlace.append(img);
nextImageGenerate();
prevImageGenerate();
}

const nextImageGenerate = () => {
    let textImage = activImage + 1;
    if(textImage >= images.length)textImage = 0;
    const img = document.createElement("img");
    img.alt = "";
    img.src = './images/'+ images[textImage];
    sliderPlace.append(img);
}

const prevImageGenerate = (w = false) => {
    let prevImage = activImage - 1;
    if(prevImage < 0) prevImage = images.length - 1;
    const img = document.createElement("img");
    img.alt = "";
    img.src = './images/'+ images[prevImage];
    if(w) img.style.width = 0;
    sliderPlace.prepend(img);
}

const nextSlide = () => {
    if(!flag)return;
    flag = !flag;
    activImage++;
    if(activImage >= images.length)activImage = 0;
    //document.querySelector(".slayder-line img").remove();
    nextImageGenerate();
    animation({
        duration:1000,
        draw:function(progress){
            document.querySelector(".slider-line img").style.width = (widthOffset * (1-progress)) +"px";
        },
        removeElement:document.querySelector(".slider-line img")
    })
}

const prevSlide =()=>{
    if(!flag)return;
    flag = !flag;
    activImage--;
    if(activImage < 0) activImage = images.length - 1;
    //document.querySelector(".slayder-line img:last-child").remove();
    prevImageGenerate(true);
    animation({
        duration:1000,
        draw:function(progress){
            document.querySelector(".slider-line img").style.width = (widthOffset * progress) +"px";
        },
        removeElement:document.querySelector(".slider-line img:last-child")
    })
}

initSlayder();


document.querySelector(".next-button").addEventListener("click",nextSlide);
document.querySelector(".prev-button").addEventListener("click",prevSlide);



const animation = ({duration,draw,removeElement}) => {
    const start = performance.now();
    requestAnimationFrame(function animation(time){
        let step = (time - start) / duration;
        if(step > 1)step = 1;
        draw(step);
        if(step < 1){
            requestAnimationFrame(animation);
        }else{
            removeElement.remove();
            flag = true;
        }

    });
}
