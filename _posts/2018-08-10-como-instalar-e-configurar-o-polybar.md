---
layout: post
title:  "Como instalar e configurar o Polybar"
date:   2018-08-10 14:38:00 +0000
categories: Dicas
tags: instalacao
comments: 1
---

Se você estiver procurando por um aplicativo que lhe permita liberdade para personalizá-la ao seu gosto, conheça o Polybar, uma ferramenta rápida e fácil de usar para criar barras de status no seu sistema.

O objetivo é ajudar os usuários a criar barras de status bonitas e altamente personalizáveis ​​para seu ambiente de desktop, sem a necessidade de ser um especialista em linguagem de script de shell. Eu forneci abaixo um exemplo de captura de tela, para que você tenha uma ideia de como é o resultado de uma personalização feita com o polybar.

<p align="center">
<img class="materialboxed responsive-img" src="https://i.imgur.com/01IuuKc.png">
</p>

O principal objetivo desta ferramenta é ajudar os usuários do Linux a criar barras de status impressionantes. Ele tem funcionalidade interna para exibir informações sobre os serviços mais comuns usados. Alguns dos recursos incluídos até o momento estão listados abaixo:

-   Ícones do Systray
-   Título da janela
-   Controles de reprodução e exibição de status para o MPD usando libmpdclient
-   Controles de volume ALSA
-   Área de trabalho e painel de área de trabalho para o bspwm e i3
-   Módulo do espaço de trabalho para gerenciadores de janelas compatíveis com o EWMH
-   Layout do teclado e status do indicador
-   Indicador de carga da CPU e memória
-   Exposição da bateria
-   Detalhes da conexão de rede
-   Nível de luz de fundo
-   Rótulo de data e hora
-   Execução de script de shell baseada no tempo
-   Saída de comando
-   Árvore de menu definida pelo usuário
-   Mensagens entre processos
-   E mais…

<br/>

### INSTALAÇÃO
Vamos instalar agora o polybar no Arch Linux, caso você use algum outro sistema, basta procurar por ele no seu gerenciador de pacotes da sua distribuição, ou se caso preferir você pode compilar o polybar através do [repositório oficial](https://github.com/jaagr/polybar)

> O Polybar se encontra no AUR do Arch Linux, então para isso vamos usar algum helper para instalar esse pacote, irei usar o **yay** mas existem outros como: **trizen, packer, pacaur** etc, caso você use outro basta substituir o **yay** por um da sua preferência.
```
$ yay -S polybar
```
> Ok instalamos o polybar é somente isso? O Polybar ele nos da uma configuração de exemplo que é bastante interessante e possui muitas informações bacanas, hoje vou mostrar para vocês a como usar essa configuração de exemplo, mas primeiro devemos instalar algumas dependências importantes para o funcionamento completo dessa configuração, essas dependências são as **fontes** para obtermos uma visualização completa dos ícones e textos dessa barra.

> Uma das fontes a ser instaladas é a [Powerline](https://github.com/powerline/fonts), pois são um excelente pacote de fontes, e ela vai servir para a parte de texto da nossa barra.
```
$ sudo pacman -S git
$ git clone https://github.com/powerline/fonts.git
$ cd fonts
$ ./install.sh
```
> Agora vamos instalar um outro pacote de fonte, a [Siji](https://github.com/stark/siji), ela vai nos fornecer os ícones para nossa barra.
```
$ yay -S siji-git
```

<br/>

### E AGORA?
Ok Polybar instalado, fontes instaladas, agora precisamos configurar essa barra, e fiquem calmos eu [Magno Tutor](https://youtube.com/MagnoTutor?sub_confirmation=1), como sou uma pessoa muito generosa haha, modifiquei a configuração de exemplo para vocês no ponto de somente aplicar e usar essa barra, de nada.

> Primeiro precisamos criar o diretório para guardar essa configuração
```
$ mkdir -p ~/.config/polybar
```
> Agora vamos baixar a configuração modificada
```
$ curl https://pastebin.com/raw/43qRQQje -o config
$ mv config ~/.config/polybar
```

<br/>

### EXECUTANDO A BARRA
Pronto se você chegou até aqui quer dizer que você conseguiu, agora para finalizar precisamos executar essa barra, só uma observação, essa barra vai funcionar em WM/TWM ela possui módulos internos para o funcionamento do **I3wm - Bspwm** claro que você pode modificar, e adequar para a sua realidade, chega de enrolação e vamos ao que interessa.

> Para iniciar a barra basta executar
```
$ polybar -r mybar
```

<br/>

### INICIAR BARRA COM A INTERFACE
Existem algumas formas de fazer isso, vou mostrar alguns exemplos.

> Colocar a barra para iniciar no arquivo **~/.xinitrc**

> obs: vai funcionar somente se a pessoa inicia sua interface através do "startx"
```
$ echo "polybar -r mybar &" > ~/.xinitrc
```
> Iniciando a barra no aquivo **~/.config/i3/config**

> obs: necessita usar o i3wm para realizar esse processo.
```
exec polybar -r mybar
```
> Iniciando a barra no aquivo **~/.config/bspwm/bspwmrc**

> obs: necessita usar o Bspwm para realizar esse processo.
```
polybar -r mybar
```

<br/>

### CONSIDERAÇÕES FINAIS
Para poder personalizar a barra, e obter maiores informações é necessário e importante ler a [documentação oficial](https://github.com/jaagr/polybar/wiki), e para detalhes como dependências, e como obter o polybar para as demais distribuições você encontra na [página oficial.](https://github.com/jaagr/polybar)


<br/><br/>

<p align="center">  
<b>NÃO ESQUEÇA DE COMPARTILHAR ESTE POST</b>
<br>
<div class="sharethis-inline-share-buttons"></div>
</p>

<br/><br/>
