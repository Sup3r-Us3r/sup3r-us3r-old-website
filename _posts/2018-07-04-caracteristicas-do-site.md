---
layout: post
title:  "Características do site"
date:   2018-07-04 21:20:00 +0000
categories: Dicas
tags: site caracteristicas
---

Esse post é voltado somente para demonstração de todas as características que este website possui.


<div class="row">
  <form class="col s12">

  <div class="input-field col s12">
  	<select>
  		<option value="" disabled selected>Selecione um valor</option>
  		<option value="1">Opção 1</option>
  		<option value="2">Opção 2</option>
  		<option value="3">Opção 3</option>
  	</select>
  </div>
  
  </form>
</div>


<script>
  $(document).ready(function(){
    $('select').formSelect();
  });
</script>
