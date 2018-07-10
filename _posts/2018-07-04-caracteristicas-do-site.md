---
layout: post
title:  "Características do site"
date:   2018-07-04 21:20:00 +0000
categories: Dicas
tags: site caracteristicas
---

Esse post é voltado somente para demonstração de todas as características que este website possui.

 <a class="waves-effect waves-light btn" onclick="$('.tap-target').tapTarget('open')">Open tap target</a>&nbsp;&nbsp;&nbsp;&nbsp;
 <a class="waves-effect waves-light btn" onclick="$('.tap-target').tapTarget('close')">Close tap target</a>
 <br>
 <br>

 <div class="fixed-action-btn" style="bottom: 45px; right: 24px;">
   <a id="menu" class="btn btn-floating btn-large cyan">
     <i class="material-icons">menu</i>
   </a>
 </div>

 <div class="tap-target cyan" data-target="menu">
   <div class="tap-target-content white-text">
     <h5>I am here</h5>
     <p class="white-text">Provide value and encourage return visits by introducing users to new features and functionality at contextually
       relevant moments.</p>
   </div>
 </div>
 
 <script>
   $(document).ready(function(){
    $('.tap-target').tapTarget();
  });
 </script>
