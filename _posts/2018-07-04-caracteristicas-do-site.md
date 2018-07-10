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
