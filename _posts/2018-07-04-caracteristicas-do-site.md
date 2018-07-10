---
layout: post
title:  "Características do site"
date:   2018-07-04 21:20:00 +0000
categories: Dicas
tags: site caracteristicas
---

Esse post é voltado somente para demonstração de todas as características que este website possui.

<div class="fixed-action-btn">
 <!-- Element Showed -->
 <a id="menu" class="waves-effect waves-light btn-large btn-floating" ><i class="material-icons">menu</i></a>
</div>

<!-- Tap Target Structure -->
<div class="tap-target red white-text" data-activates="menu">
  <div class="tap-target-content">
    <h5>Por favor</h5>
    <p>A bunch of text</p>
  </div>
</div>

<a class="btn" id="abrir">Abrir</a>
<a class="btn" id="fechar">Fechar</a>

<script>
$("#abrir").click(function(){
 $('.tap-target').tapTarget('open');
});
 
$("#fechar").click(function(){
 $('.tap-target').tapTarget('close');
});
</script>
