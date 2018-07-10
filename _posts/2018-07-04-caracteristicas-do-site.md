---
layout: post
title:  "Características do site"
date:   2018-07-04 21:20:00 +0000
categories: Dicas
tags: site caracteristicas
---

Esse post é voltado somente para demonstração de todas as características que este website possui.

<div class="input-field col s12">
  <select>
    <option value="" disabled selected>Choose your option</option>
    <option value="1">Option 1</option>
    <option value="2">Option 2</option>
    <option value="3">Option 3</option>
  </select>
  <label>Materialize Select</label>
</div>

<div class="input-field col s12">
  <select multiple>
    <option value="" disabled selected>Choose your option</option>
    <option value="1">Option 1</option>
    <option value="2">Option 2</option>
    <option value="3">Option 3</option>
  </select>
  <label>Materialize Multiple Select</label>
</div>

<div class="input-field col s12">
  <select>
    <optgroup label="team 1">
      <option value="1">Option 1</option>
      <option value="2">Option 2</option>
    </optgroup>
    <optgroup label="team 2">
      <option value="3">Option 3</option>
      <option value="4">Option 4</option>
    </optgroup>
  </select>
  <label>Optgroups</label>
</div>

<div class="input-field col s12 m6">
  <select class="icons">
    <option value="" disabled selected>Choose your option</option>
    <option value="" data-icon="images/sample-1.jpg">example 1</option>
    <option value="" data-icon="images/office.jpg">example 2</option>
    <option value="" data-icon="images/yuna.jpg">example 3</option>
  </select>
  <label>Images in select</label>
</div>
<div class="input-field col s12 m6">
  <select class="icons">
    <option value="" disabled selected>Choose your option</option>
    <option value="" data-icon="images/sample-1.jpg" class="left">example 1</option>
    <option value="" data-icon="images/office.jpg" class="left">example 2</option>
    <option value="" data-icon="images/yuna.jpg" class="left">example 3</option>
  </select>
  <label>Images in select</label>
</div>

<label>Browser Select</label>
<select class="browser-default">
  <option value="" disabled selected>Choose your option</option>
  <option value="1">Option 1</option>
  <option value="2">Option 2</option>
  <option value="3">Option 3</option>
</select>


<script>
  $(document).ready(function(){
    $('select').formSelect();
  });
</script>
