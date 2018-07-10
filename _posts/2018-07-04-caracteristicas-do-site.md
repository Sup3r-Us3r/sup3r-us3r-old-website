---
layout: post
title:  "Características do site"
date:   2018-07-04 21:20:00 +0000
categories: Dicas
tags: site caracteristicas
---

Esse post é voltado somente para demonstração de todas as características que este website possui.


<div class="carousel">
  <a class="carousel-item" href="#one!"><img src="https://s5.favim.com/orig/54/bubble-bubbles-clouds-colours-Favim.com-522009.jpg" height="200"></a>
  <a class="carousel-item" href="#two!"><img src="https://s5.favim.com/orig/54/bubble-bubbles-clouds-colours-Favim.com-522009.jpg" height="200"></a>
  <a class="carousel-item" href="#three!"><img src="https://s5.favim.com/orig/54/bubble-bubbles-clouds-colours-Favim.com-522009.jpg" height="200"></a>
  <a class="carousel-item" href="#four!"><img src="https://s5.favim.com/orig/54/bubble-bubbles-clouds-colours-Favim.com-522009.jpg" height="200"></a>
  <a class="carousel-item" href="#five!"><img src="https://s5.favim.com/orig/54/bubble-bubbles-clouds-colours-Favim.com-522009.jpg" height="200"></a>
</div>

<div class="carousel carousel-slider">
  <a class="carousel-item" href="#one!"><img src="https://s5.favim.com/orig/54/bubble-bubbles-clouds-colours-Favim.com-522009.jpg" height="200"></a>
  <a class="carousel-item" href="#two!"><img src="https://s5.favim.com/orig/54/bubble-bubbles-clouds-colours-Favim.com-522009.jpg" height="200"></a>
  <a class="carousel-item" href="#three!"><img src="https://s5.favim.com/orig/54/bubble-bubbles-clouds-colours-Favim.com-522009.jpg" height="200"></a>
  <a class="carousel-item" href="#four!"><img src="https://s5.favim.com/orig/54/bubble-bubbles-clouds-colours-Favim.com-522009.jpg" height="200"></a>
  <a class="carousel-item" href="#five!"><img src="https://s5.favim.com/orig/54/bubble-bubbles-clouds-colours-Favim.com-522009.jpg" height="200"></a>
</div>

<div class="carousel carousel-slider center">
  <div class="carousel-fixed-item center">
    <a class="btn waves-effect white grey-text darken-text-2">Ver</a>
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
    $('.carousel').carousel();
  });
  
    $('.carousel.carousel-slider').carousel({
    fullWidth: true,
    indicators: true,
    duration: 100
  });
</script>

