---
layout: post
title:  "Características do site"
date:   2018-07-04 21:20:00 +0000
categories: Dicas
tags: site caracteristicas
---

Esse post é voltado somente para demonstração de todas as características que este website possui.


<div class="input-field col s12 m6">
  <select class="icons">
    <option value="" disabled selected>Choose your option</option>
    <option value="" data-icon="https://www.linknacional.com.br/wp-content/uploads/2018/04/linux.jpg">example 1</option>
    <option value="" data-icon="https://www.linknacional.com.br/wp-content/uploads/2018/04/linux.jpg">example 2</option>
    <option value="" data-icon="https://www.linknacional.com.br/wp-content/uploads/2018/04/linux.jpg">example 3</option>
  </select>
  <label>Images in select</label>
</div>
<div class="input-field col s12 m6">
  <select class="icons">
    <option value="" disabled selected>Choose your option</option>
    <option value="" data-icon="https://www.linknacional.com.br/wp-content/uploads/2018/04/linux.jpg" class="left">example 1</option>
    <option value="" data-icon="https://www.linknacional.com.br/wp-content/uploads/2018/04/linux.jpg" class="left">example 2</option>
    <option value="" data-icon="https://www.linknacional.com.br/wp-content/uploads/2018/04/linux.jpg" class="left">example 3</option>
  </select>
  <label>Images in select</label>
</div>


<script>
  $(document).ready(function(){
    $('select').formSelect();
  });
</script>
