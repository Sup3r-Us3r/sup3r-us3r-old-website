---
layout: post
title:  "Aprenda a usar o Pac-Man"
date:   2018-06-29 22:51:00 +0000
categories: Linux
tags: archlinux pacman
comments: 1
---

O gerenciador de pacote pacman é uma das grandes vantagens do Arch Linux. Combina um simples pacote no formato binário, com um fácil uso de sistema de compilação. A meta do pacman é tornar o mais fácil possível gerenciar pacotes, sejam eles dos repositórios oficiais ou das próprias compilações do usuário.
O pacman mantém o sistema atualizado, listas de pacotes de sincronização com o servidor mestre. Este modelo servidor/cliente também permite o usuário baixar/instalar pacotes com um simples comando, completo com todas as dependências requeridas.
O pacman é escrito na linguagem de programação C e usa o formato tar para empacotamento.

#### APRENDA COMO UTILIZAR ESSE INCRIVÉL GERENCIADOR DE PACOTES

> Sincroniza os repositórios
```
sudo pacman -Sy
```
> Procura por atualização
```
sudo pacman -Su
```
> Sincroniza os repositórios/procura por atualização
```
sudo pacman -Syu
```
> Sincroniza os repositórios do Arch/Derivados
```
sudo pacman -Syy
```
> Sincronização total/procura por atualização
```
sudo pacman -Syyu
```
> Instala um pacote
```
sudo pacman -S pacote
```
> Remove um pacote
```
sudo pacman -R pacote
```
> Remove o pacote junto com as dependências não usadas por outros pacotes
```
sudo pacman -Rs pacote
```
> Remove o pacote junto com as dependências não usadas por outros pacotes e junto com os arquivos de configuração.
```
sudo pacman -Rsn pacote
```
> Procura por um pacote
```
sudo pacman -Ss pacote
```
> Apenas baixa o pacote e não o instala
```
sudo pacman -Sw pacote
```
> Mostra informações de um pacote não instalado
```
sudo pacman -Si pacote
```
> Mostra informações do pacote já instalado
```
sudo pacman -Qi pacote
```
> Instala apenas as dependências
```
sudo pacman -Se pacote
```
> Mostra todos os arquivos pertencentes ao pacote
```
sudo pacman -Ql pacote
```
> Mostra os pacotes que serão atualizados
```
sudo pacman -Qu
```
> Lista todos os pacotes instalados
```
sudo pacman -Q
```
> Mostra a qual pacote aquele arquivo pertence
```
sudo pacman -Qo arquivo
```
> Lista pacotes desnecessários, sem dependências
```
sudo pacman -Qdt
```
> Apaga pacotes desnecessários, sem dependências
```
sudo pacman -Rns $(pacman -Qqdt)
```
> Instala um pacote local
```
sudo pacman -A pacote.pkg.tar.gz
```
> Deleta do cache todos os pacotes antigos
```
sudo pacman -Sc
```
> Limpa o cache, removendo todos os pacotes existentes no /var/cache/pacman/pkg/
```
sudo pacman -Scc
```
> Otimiza a base de dados do pacman
```
sudo pacman-optimize
```
> Instala ignorando as dependências
```
sudo pacman -Sdd
```
> Elimina um pacote ignorando as dependências
```
sudo pacman -Rdd
```
> Para gerenciar pacman.conf
```
sudo pacman-mirrors.conf
```
> Para gerar um novo mirrorlist
```
sudo pacman-mirrors -g
```
> Instalar pacotes baixados no sistema
```
sudo pacman -U home/user/arquivo.tar.xz
```
> Instalar pacotes baixados via download
```
sudo pacman -U http://www.site.com/arquivo.tar.xz
```
> Lista pacotes instalados do repo AUR
```
sudo pacman -Qem
```
> Desinstala pacotes e suas dependências e seus registros, tudo
```
sudo pacman -Rscn
```
> Instala o pacote sem precisar confirmar com "yes/no - S/N"
```
sudo pacman -S pacote –noconfirm
```
> Sincroniza os repositórios/procura por atualização e ignora os grupos dos pacotes solicitados
```
sudo pacman -Syu –ignoregroup pacote1 , pacote2…
```
> Sincronizar a base de dados
```
yaourt -Syua –devel
```
> Atualizar o repo AUR
```
yaourt -Syyuua
```
> Pesquisar no repo AUR
```
yaourt -Ss nome
```
> Instalar pacotes do repo AUR
```
yaourt -S nome
```
> Remover pacotes do repo AUR
```
yaourt -R nome
```
> Remover pacotes + dependências do repo AUR
```
yaourt -Rsn nome
```
> Sincronizar a base de dados e atualiza pacotes
```
yaourt -Syu –devel –aur
```
