---
layout: post
title:  "Características do site"
date:   2018-07-04 21:20:00 +0000
categories: Dicas
tags: site caracteristicas
---

Esse post é voltado somente para demonstração de todas as características que este website possui.


 <!-- Dropdown Trigger -->
 <a class='dropdown-button btn' data-belloworigin="true" href='#' data-activates='dropdown1'>Drop Me!</a>

 <!-- Dropdown Structure -->
 <ul id='dropdown1' class='dropdown-content'>
   <li><a href="#!">one</a></li>
   <li><a href="#!">two</a></li>
   <li class="divider" tabindex="-1"></li>
   <li><a href="#!">three</a></li>
   <li><a href="#!"><i class="material-icons">view_module</i>four</a></li>
   <li><a href="#!"><i class="material-icons">cloud</i>five</a></li>
 </ul>
 
<script>
$('.dropdown-button').dropdown();
</script>


---

<div class="carousel carousel-slider center">
  <div class="carousel-fixed-item center">
    <a class="btn waves-effect white grey-text darken-text-2">button</a>
  </div>
  <div class="carousel-item red white-text" href="#one!">
    <h2>First Panel</h2>
    <p class="white-text">This is your first panel</p>
  </div>
  <div class="carousel-item amber white-text" href="#two!">
    <h2>Second Panel</h2>
    <p class="white-text">This is your second panel</p>
  </div>
  <div class="carousel-item green white-text" href="#three!">
    <h2>Third Panel</h2>
    <p class="white-text">This is your third panel</p>
  </div>
  <div class="carousel-item blue white-text" href="#four!">
    <h2>Fourth Panel</h2>
    <p class="white-text">This is your fourth panel</p>
  </div>
</div>

<script>
$(document).ready(function(){
  
  $('.carousel.carousel-slider').carousel({
    fullWidth: true,
    indicators: true
  });

});
</script>
