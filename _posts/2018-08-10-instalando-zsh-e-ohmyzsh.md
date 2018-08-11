---
layout: post
title:  "Instalando ZSH e Oh-My-ZSH"
date:   2018-08-10 00:40:00 +0000
categories: Dicas
tags: instalacao
comments: 1
---

[Zsh](http://www.zsh.org/) é um shell de login interativo que também pode ser usado como um poderoso intérprete de linguagem de script. Hoje vamos deixar o bash descansar, e conhecer um shell que vai te dar muitas possibilidades e usabilidade.

##### INSTALANDO ZSH
Para instalar o ZSH em seu sistema, basta usar seu gerenciador de pacotes de sua distribuição e assim instalar este pacote, irei dar alguns exemplos.

> Arch Linux/Derivados
```
$ sudo pacman -S zsh
```
> Debian/Derivados
```
$ sudo apt-get install zsh
```
------

<br/>

<p align="center">
<img class="responsive-img" src="https://ohmyz.sh/img/OMZLogo_BnW.png">
</p>

Oh my ZSH é um framework open-source dirigido pela comunidade, para gerenciar a configuração do ZSH (Terminal feito para uso interativo) e melhorar o workflow de desenvolvimento. Ele inclui mais de 200 plugins opcionais (rails, git, OSX, hub, capistrano, brew, ant, php, python, etc), e mais de 140 temas.

#### PRÉ-REQUISITOS

**Aviso**: Oh My Zsh funciona melhor no macOS e Linux.

-   Sistema operacional baseado no Unix (macOS or Linux)
-   ZSH instalado
-   curl ou wget devem estar instalados
-   git deve estar instalado

#### INSTALAR OH-MY-ZSH
> Via curl
```
$ sh -c "$(curl -fsSL https://raw.github.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"
```
> Via wget
```
$ sh -c "$(wget https://raw.github.com/robbyrussell/oh-my-zsh/master/tools/install.sh -O -)"
```

#### TEMAS
<p align="center">
<img class="responsive-img" src="https://cloud.githubusercontent.com/assets/2618447/6316862/70f58fb6-ba03-11e4-82c9-c083bf9a6574.png">
</p>

Nesse  [link](https://github.com/robbyrussell/oh-my-zsh/wiki/themes)  tem os temas do oh-my-zsh. Para mudar de tema é preciso entrar no arquivo **.zshrc**  que fica na sua home, e alterar a linha  **ZSH_THEME="robbyrussell"**  pelo tema que preferir, bastando apenas alterar o nome **robbyrussell** que é o tema padrão para qual você desejar.
> Abra o arquivo com o nano, ou com qualquer editor de texto de sua preferência
```
$ nano ~/.zshrc
```
> Vou usar como exemplo o tema **ys**
```
ZSH_THEME="ys"
```
Após editar o nome do tema, basta salvar o arquivo.


##### ALTERANDO O SHELL DE BASH PARA ZSH
> Para alterar do bash para o zsh basta rodar o comando
```
$ chsh -s /bin/zsh
```
> Ao encerrar a sessão e entrar novamente, o shell já estará mudado.


<br/><br/>

<p align="center">  
<b>NÃO ESQUEÇA DE COMPARTILHAR ESTE POST</b>
<br>
<div class="sharethis-inline-share-buttons"></div>
</p>

<br/><br/>
