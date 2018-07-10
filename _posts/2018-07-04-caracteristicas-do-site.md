---
layout: post
title:  "Características do site"
date:   2018-07-04 21:20:00 +0000
categories: Dicas
tags: site caracteristicas
---

Esse post é voltado somente para demonstração de todas as características que este website possui.


<a href="#teste" class="btn modal-trigger"> Abrir modal </a>
<div class="modal" id="teste">
 <div class="modal-content">
  <h4 class="light"> Teste </h4>
  <p> O hábito da leitura é um dos mais importantes para o desenvolvimento do intelecto e também o caminho mais curto para adquirir conhecimento. Em meio ao boom tecnológico das últimas décadas, esse hábito acabou ficando de lado, sendo substituído primeiro pela televisão, depois pelos computadores, pelos videogames e agora pelos smartphones.
  </p>
 </div>
 
 <div class="modal-footer">
  <a class="btn">Sair</a>
 </div>
</div>


<script>
$(document).ready(function(){
 $('.modal').modal();
});
</script>
