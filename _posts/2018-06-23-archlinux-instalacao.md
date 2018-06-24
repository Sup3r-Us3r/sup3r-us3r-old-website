---
layout: post
title:  "Instalação Arch Linux"
date:   2018-06-23 13:40:00 +0000
categories: Linux
tags: archlinux instalacao
comments: 1
---
### INSTALAÇÃO ARCH LINUX

Este guia destina-se a ajudar alguém a instalar a distribuição Arch Linux  em seu Computador. O guia pressupõe que você tenha alguma familiaridade com o sistema linux e esteja confortável, trabalhando a partir da linha de comando, mas não exige que você seja um especialista. Aprendemos muito fazendo e se você quiser saber mais sobre como o linux opera, o Arch Linux é uma excelente opção por muitas razões.

**Porquê Arch ?**

Uma das maiores vantagens da distribuição Arch Linux é a sua simplicidade na abordagem e atitude. O [Arch Linux Beginner's Guide](https://wiki.archlinux.org/index.php/Installation_guide_(Portugu%C3%AAs)) descreve esta atitude muito bem isso, ele lhe dá a capacidade de construir o seu sistema a partir do zero.


**Os princípios de design por trás do Arch são destinados a mantê-lo simples:**

> "Simples", neste contexto, significa sem adições, modificações ou complicações desnecessárias. Em resumo; Uma abordagem elegante e minimalista.


**Alguns pensamentos a ter em mente ao considerar a simplicidade:**

> "Simples" é definido de um ponto de vista técnico, não um ponto de vista de usabilidade. É melhor ser tecnicamente elegante com uma curva de aprendizado mais alta, do que ser fácil de usar e tecnicamente [inferior]. "- Aaron Griffin

> "A parte extraordinária de [meu método] reside em sua simplicidade ... A altura do cultivo sempre corre para a simplicidade". - Bruce Lee

------

Faça o download do Arch Linux: [Baixar](https://www.archlinux.org/download/)

| USB BOOTABLE | DOWNLOAD | VIA COMANDO DD LINUX |
|--|--|--|
| LINUX | [Etcher](https://etcher.io) - [RosaImageWriter](http://wiki.rosalab.com/en/index.php/ROSA_ImageWriter) | dd bs=4M if=/lugar_onde_esta_sua_iso of=/dev/sdX status=progress && sync |
| WINDOWS | [Rufus](https://rufus.akeo.ie) - [Win32DiskImager](https://sourceforge.net/projects/win32diskimager) |

**(Substitua o X pela letra do seu dispositivo ex: "sdc, sdd") use: lsblk**

------

### OBSERVAÇÕES:
* Caso você necessite instalar via UEFI os comandos estão com o simbolo: 🔶
* No particionamento BIOS e UEFI, faça como segue o exemplo, modifique apenas o tamanho das partições, em seguida monte as partições de acordo com o particionamento feito.
* Preste muita atenção em relação a sua unidade do disco rígido, pois isso vai variar de computador parar computador.

------
<br/><br/>

### 🔶 VERIFIQUE O MODO DE INICIALIZAÇÃO: (UEFI)
> Se este comando a seguir listar as **variáveis EFI**, isso significa que você iniciou a operação com sucesso no modo **EFI**. Caso contrário, reinicie no **menu de boot** novamente e selecione o item correto lá, e não o item **legacy-mode**.
```
# efivar -l
```
> Se o diretório não existir, o sistema pode ser inicializado no modo **BIOS** ou **CSM**.

### TECLADO EM ABNT2
> Setar layout br-abnt2 para o teclado
```
# loadkeys br-abnt2
```

### CONEXÃO COM A INTERNET
> Ethernet:
```
# systemctl start dhcpcd
# ping -c3 google.com
```
> Wifi:
```
# wifi-menu
# ping -c3 www.google.com
```

### PARTICIONAMENTO DE DISCO
#### Particionar Disco **(BIOS)**

![bios](https://raw.githubusercontent.com/Sup3r-Us3r/Arch-Install/master/Particionamento%20de%20Disco/parti%C3%A7%C3%B5es%20bios.gif)

> Aconselha-se dar
> * /swap = 4gb
> * /raiz = Todo o restante do HD
```
# fdisk -l
# cfdisk /dev/sdX
```
**(Substitua o X pela letra do seu disco rígido ex: "sda, sdb")**

#### 🔶 Particionar Disco **(UEFI)**

![uefi](https://raw.githubusercontent.com/Sup3r-Us3r/Arch-Install/master/Particionamento%20de%20Disco/parti%C3%A7%C3%B5es%20uefi.gif)

> Aconselha-se dar
> * /boot = 300mb
> * /swap = 4gb
> * /raiz = Todo o restante do HD
```
# fdisk -l
# sgdisk --zap-all /dev/sdX
```
**(Substitua o X pela letra do seu disco rígido ex: "sda, sdb")**

> Primeiro, devemos criar uma nova tabela de partição, no caso será **GPT**, para o suporte à **UEFI**.
Vamos utilizar o **gdisk** para a criação das partições `/boot` `/swap` `/root`
```
# gdisk /dev/sdX
```
**(Substitua o X pela letra do seu disco rígido ex: "sda, sdb")**

> Logo em seguida você entrará na interface do gdisk, onde deverá particionar o disco, ele possui uma interface simples mas eficaz, basta seguir o exemplo abaixo:

```
Command (? for help): o
Proceed? (Y/N): Y

Para criar nova partição:

Command (? for help): n
Partition number: Aperte Enter
First sector: Enter
Last sector: +300M
Hex Code or GUID: EF00
```
> Acima criamos uma partição com 300Mb de espaço **(não precisa mais que 300mb para essa partição)** do tipo EFI, para nossa partição de boot.
```
Command (? for help): n
Partition number: Aperte Enter
First sector: Enter
Last sector: +2G
Hex Code or GUID: 8200
```
> Acima, criamos a nossa partição SWAP com 2gb de espaço, **(o swap é uma memória virtual recomendo dar no máximo 4gb)**.
```
Command (? for help): n
Partition number: Aperte Enter
First sector: Aperte Enter
Last sector: Aperte Enter
Hex Code or GUID: 8300
```
> Esta última partição criada é a root, não daremos tamanho para ela, só aperte ENTER, que o gdisk entenderá que é pra aproveitar todo o restante do HD **(essa partição servirá para a instalação do sistema, seus arquivos pessoais, programas etc)**.


### FORMATAR AS PARTIÇÕES
Após o particionameto do disco rígido, devemos formatar as partições.
#### Formatar `/root` `/swap` **(BIOS)**
> Root:
```
# mkfs.ext4 /dev/sda1
```
> Swap:
```
# mkswap /dev/sda2
# swapon /dev/sda2
```

> #### 🔶 Formatar `/boot` `/swap` `/root` **(UEFI)**
> Boot:
```
# mkfs.vfat -F32 /dev/sda1
```
> Swap:
```
# mkswap /dev/sda2
# swapon /dev/sda2
```

### MONTAGEM DAS PARTIÇÕES
> Antes de podermos baixar, e instalar os pacotes base do Arch Linux, precisamos montar nossas partições, e mudar para o nosso diretório root. Afinal, é nele onde vamos instalar o Arch Linux.

#### Montar `/root` **(BIOS)**
> Root:
```
# mount -t ext4 /dev/sda1 /mnt
```

#### 🔶 Montar `/boot` `/root` **(UEFI)**
> Boot:
```
# mkdir -p /mnt/boot/efi
# mount /dev/sda1 /mnt/boot/efi
```
> Root:
```
# mount /dev/sda3 /mnt
```

### ESCOLHER O ESPELHO DE DOWNLOAD
> Escolher a lista de espelhos mais próxima
```
# pacman -Sy reflector
# reflector --verbose -l 5 --sort rate --save /etc/pacman.d/mirrorlist
```

### INSTALAR OS PACOTES BASE DO ARCH LINUX
> Esta na hora de instalar a base do sistema
```
# pacstrap -i /mnt base base-devel
```

### CONFIGURAR O FSTAB
> Para configurar fstab (tabela de sistemas de arquivos) execute:
```
# genfstab -U -p /mnt >> /mnt/etc/fstab
```
> Você deve sempre verificar se a entrada fstab está correta ou não, que será capaz de inicializar em seu sistema. Para verificar a entrada fstab, execute:
```
# cat /mnt/etc/fstab
```
Se tudo estiver OK você deve ver o root montado.


### NOVO SISTEMA
> Agora é hora de mudar para o diretório root recém-instalado para configurá-lo.
```
# arch-chroot /mnt
# loadkeys br-abnt2 (para usar o layout abnt2)
```

### CONFIGURAR KEYMAP
> A variável KEYMAP é especificada no arquivo /etc/vconsole.conf . Ele define qual layout de teclado, será usado nos consoles virtuais. Execute este comando:
```
# echo -e 'KEYMAP="br-abnt2.map.gz"' > /etc/vconsole.conf
```

### CONFIGURAÇÕES DE IDIOMA E FUSO HORÁRIO
> Para configurar o idioma do sistema, execute o seguinte comando:
```
# sed -i '/pt_BR/,+1 s/^#//' /etc/locale.gen
# locale-gen
# echo LANG=pt_BR.UTF-8 > /etc/locale.conf
# export LANG=pt_BR.UTF-8
```
> Para ver todos os fusos horários disponíveis da América:
```
# ls /usr/share/zoneinfo/America
```
> Agora você pode configurar a sua zona:
```
# ln -sf /usr/share/zoneinfo/America/Sao_Paulo /etc/localtime
```
> Vamos agora configurar o relógio do hardware, apenas no caso de termos uma data errada:
```
# hwclock --systohc --utc
```
> Para conferir se a hora está certa:
```
# date
```

### CONFIGURAR REPOSITÓRIO
> Com este comando habilitamos o repositório multilib:
```
# sed -i '/multilib\]/,+1 s/^#//' /etc/pacman.conf
# pacman -Sy
```

### DEFINIR HOSTNAME
> Agora você vai setar o nome que você deseja ter na sua maquina, basta trocar o "arch" pelo nome que quiser, mas ele não pode conter espaços.
```
# echo arch > /etc/hostname
```

### CONFIGURANDO A CONEXÃO
> Ethernet:
```
# systemctl enable dhcpcd
```
> Wifi:
```
# pacman -S wpa_supplicant wpa_actiond dialog iw networkmanager
# systemctl enable NetworkManager
```

### CRIAR USUÁRIO
> useradd -m -g [initial_group] -G [additional_groups] -s [login_shell] [username]
```
# useradd -m -g users -G wheel,storage,power -s /bin/bash ghost
```
> Em seguida, forneça a senha para este novo usuário executando:
```
# passwd ghost
```
> Não se esqueça de definir também a senha para o usuário **root**:
```
# passwd
```
> Permitir que os usuários no grupo wheel, sejam capazes de executar tarefas administrativas com o sudo:
```
# sed -i '/%wheel ALL=(ALL) ALL/s/^#//' /etc/sudoers
```

### INSTALAR BOOT-LOADER (GRUB)

> Instalar e configurar o boot-loader **(BIOS)**
```
# mkinitcpio -p linux
# pacman -S grub
# grub-install /dev/sdX
# pacman -S os-prober (Se você estiver inicializando em dual boot)
# pacman -S intel-ucode (Se você tiver uma CPU Intel, instale o pacote intel-ucode)
# grub-mkconfig -o /boot/grub/grub.cfg
```
> 🔶 Instalar e configurar o boot-loader **(UEFI)**
```
# mkinitcpio -p linux
# pacman -S grub efibootmgr
# grub-install /dev/sdX
# pacman -S os-prober (Se você estiver inicializando em dual boot)
# pacman -S intel-ucode (Se você tiver uma CPU Intel, instale o pacote intel-ucode)
# grub-mkconfig -o /boot/grub/grub.cfg
```
> 🔶 Caso der erro ao tentar instalar o grub, tente outro modo: **(UEFI)**
```
# grub-install --target=x86_64-efi --efi-directory=/boot --bootloader-id=grub --recheck
```

### DESMONTAR AS PARTIÇÕES E REINICIAR
> Desmonte as partições e reinicie para poder ir para o próximo passo, a pós instalação.
```
# exit
# umount -R /mnt
# poweroff
```

### PÓS INSTALAÇÃO
> Após a instalação do Arch Linux a única coisa que os usuários vêem é uma linha de comando sem qualquer servidor X, então o usuário deve instalar o X server, uma área de trabalho e alguns outros aplicativos para fazer seu trabalhos diários.

> Logue com seu **usuário** e **senha**:
```
$ su
# loadkeys br-abnt2 (para usar o layout abnt2)
```
> Conecte a sua rede wireless (Caso tenha)
```
# nmtui
```
> Verificar a conectividade com a internet:
```
# ping -c3 www.google.com
```

### INSTALAR DISPLAY SERVER

> Um display server ou servidor de janela é um programa cuja principal tarefa é coordenar a entrada e saída de seus clientes para o sistema operacional, o hardware e entre eles. Em outras palavras, o display server controla e gerencia os recursos de baixo nível para ajudar a integrar as partes da GUI. Por exemplo, os display server gerenciam o mouse e ajudam a combinar os movimentos do mouse com o cursor e os eventos GUI causados pelo cursor. Mas não se confunda, o servidor de exibição não desenha nada. Eles apenas gerenciam a interface, as bibliotecas, os toolkits e, como você pode ver, eles se comunicam diretamente com o kernel. Vamos usar o [XORG](https://wiki.archlinux.org/index.php/Xorg_(Portugu%C3%AAs))
```
# pacman -S xorg-server xorg-xinit xorg-apps mesa ttf-dejavu gvfs-mtp
```

### INSTALAR DRIVERS GRÁFICOS

> É hora de instalar drivers de vídeo. Eu suponho que você sabe qual GPU você está usando. Se você não sabe qual drive de vídeo você possui, descubra com esse comando:
```
# lspci -k | grep -A 2 -i "VGA"
```
> Instale o que for referente ao seu:
```
# pacman -S virtualbox-guest-utils (para Virtualbox)
# pacman -S xf86-video-amdgpu (para placas Amd Radeon)
# pacman -S xf86-video-intel (para placas da Intel)
# pacman -S xf86-video-nouveau (para placas Nvidia) #OpenSource
```
Espera!!! Eu quero instalar o driver proprietário da **Nvidia/ATI**, qual driver devo instalar?

### Nvidia
#### ✅ Instale o driver apropriado para a sua placa:

  * Para placas da série **GeForce 400 ou mais recentes** [NVCx ou mais recente], instale o pacote `nvidia` ou `nvidia-lts` disponível nos repositórios oficiais.
  
  * Para placas da série **GeForce 8/9 e 100-300** [NV5x, NV8x, NV9x e NVAx], instale o pacote `nvidia-340xx` ou `nvidia-340xx-lts` disponível nos repositórios oficiais.
  
  * Para placas da série **GeForce 6/7** [NV4x e NV6x], instale o pacote `nvidia-304xx` ou `nvidia-304xx-lts` disponível nos repositórios oficiais.
  
  * Para os modelos GPU `mais recentes`, pode ser necessário instalar `nvidia-beta` do `Arch User Repository`, uma vez que os drivers estáveis podem não suportar os recursos recém-introduzidos.
  
  * Se você estiver com sistema de `64 bits` você também precisa de um suporte OpenGL de 32 bits, você também deve instalar o pacote lib32 equivalente do repositório multilib (e.g. `lib32-nvidia-libgl`, `lib32-nvidia-340xx-libgl` ou `lib32-nvidia-304xx-libgl` ).
  
### Ati
#### ✅ O driver xf86-video-ati (radeon):

  * Funciona com chipsets Radeon até HD 6xxx e 7xxxM (latest Northern Islands chipsets).
   
  * Radeons no HD 77xx  (Southern Islands) as séries são principalmente suportadas. Verifique a matriz de recursos para recursos não suportados.
   
  * Radeons até a série X1xxx são totalmente suportados, estáveis e a aceleração completa 2D e 3D são fornecidas.
   
  * Radeons de HD 2xxx a HD 6xxx têm aceleração 2D completa e aceleração 3D funcional, mas não são suportados por todos os recursos que o driver proprietário oferece.
   
  * Suporta DRI1, RandR 1.2 / 1.3 / 1.4, Glamour, aceleração do EXA e configuração do modo kernel / DRI2.
   
  * Geralmente, o **xf86-video-ati** deve ser sua primeira escolha, independentemente do driver AMD / ATI que você possui. No caso de você precisar usar um driver para drivers AMD mais novos, você deve considerar o driver de catalisador proprietário.
   
 > Nota: xf86-video-ati é especificado como radeon para o kernel em xorg.conf
 
### ADVANCED LINUX SOUND ARCHITECTURE (ALSA)

> Agora, vamos instalar os aplicativos para placa de som:
```
# pacman -S alsa-utils alsa-lib pulseaudio pulseaudio-alsa pavucontrol
```

### INSTALAR AMBIENTE DE TRABALHO
> Depois de instalar o servidor X você precisa de um ambiente seja ele um Gerenciador de Janelas ou Desktop Environment para fazer seus trabalhos diários!

#### `Gerenciadores de Janelas`

> I3wm:
```
# pacman -S i3
```
> Bspwm:
```
# pacman -S bspwm sxhkd
```
> Dwm:
```
# pacman -S dwm
```
> Awesome:
```
# pacman -S awesome
```

#### `Interfaces Gráficas`

> Xfce4 Desktop Environment:
```
# pacman -S xfce4 
```
> Budgie Desktop Environment:
```
# pacman -S budgie-desktop
```
> GNOME Desktop Environment:
```
# pacman -S gnome gnome-extra
```
> Cinnamon Desktop Environment:
```
# pacman -S cinnamon nemo-fileroller
```
> KDE Desktop Environment:
```
# pacman -S plasma-desktop kdebase
```
> Mate Desktop Environment:
```
# pacman -S mate mate-extra
```
> Deepin Desktop Environment:
```
# pacman -S deepin deepin-extra
```
> Enlightenment Desktop Environment:
```
# pacman -S enlightenment
```
> LXDE Desktop Environment:
```
# pacman -S lxde
```

### DISPLAY MANAGER OU LOGIN MANAGER
> Por exemplo, se você estiver instalando o Xfce (DE) você notará que não existe um ambiente de login gráfico. Então, isso significa que você pode fazer login usando a linha de comando e, em seguida, iniciar o Xfce ou instalar um gerenciador de login como o LXDM, que - após um login bem-sucedido - iniciará o Xfce para você.

> Exemplo: Lxdm
```
# pacman -S lxdm
# systemctl enable lxdm.service
# reboot
```
Existem outras alternativas como: **Gdm**, **Sddm** etc.

### YAOURT
> Alguns pacotes não podem ser encontrados no repositório principal, por isso temos o AUR onde possamos encontra-los e instalá-los, e para fazer isto precisamos adicionar o endereço AUR no final do arquivo /etc/pacman.conf.
```
# echo -e "[archlinuxfr]\nSigLevel = Never\nServer=http://repo.archlinux.fr/\$arch" >> /etc/pacman.conf
# pacman -Sy yaourt
```

### RECOMENDAÇÕES FINAIS
> Caso use um notebook, você deve instalar os drivers do seu touchpad:
```
# pacman -S xf86-input-synaptics
```
