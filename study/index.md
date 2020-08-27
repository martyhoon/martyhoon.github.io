---
layout: default
title: Study
main : true
---

<ul class ="study-navi"  >

<li id="all">All</li>
<li id="Web">Web</li>
<li id="javaScript">JavaScript</li>

</ul>

<ul class="catalogue">
{% assign sorted = site.pages | sort: 'order' | reverse %}
{% for page in sorted %}
{% if page.study == true %}

{% include post-list.html %}

{% endif %}
{% endfor %}
</ul>

<script>

const studyNavi = document.querySelector(".study-navi");
const all = document.querySelector(".study-navi #all");
const contents = document.querySelectorAll(".catalogue-item");
const list =document.querySelectorAll(".study-navi li")


function init(){

    all.style.color = "white";
    all.style.background ="#495057";

}

studyNavi.addEventListener("click",  function(event){

    const type = event.target.id;
    
    //선택된 버튼 색칠   
    for(let value of list){

        if(value.id === type){

            value.style.color = "white";
            value.style.background ="#495057";

        } else{

            value.style.color = "#495057";
            value.style.background ="white";

        }
       
    }

    //해당 버튼의 contents 출력
    if(type === "all"){
        for(let value of contents){
            value.style.display = "block";

        }
    }else{

        for(let value of contents){

                 if(value.id === type){
                     //display : block;
    
                     value.style.display = "block";

                 }
                 else{
                       value.style.display = "none";
                     //display : none;
                 }
        }
    }
   
});




init();

</script>