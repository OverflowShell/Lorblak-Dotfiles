##  Tabla de Contenidos

* [Introducción](#introducción)
* [Prerrequisitos](#prerrequisitos)
  * [Paquetes Generales](#paquetes-generales)
  * [Instalando bspwm](#instalando-bspwm)
  * [Instalando Polybar](#instalando-polybar)
* [Instalación](#instalación)
* [Enlaces Útiles](#enlaces-útiles)
* [Fuentes](#fuentes)
* [Galería](#galería)


## Introducción

gusto, presento mis dotfiles, para todos aquellos que vieron mis capturas en `Linux Latinoamérica` y `XUnix`. La mayor parte del trabajo se hizo en AntiX, y estas configuraciones pretenden ser aplicables de distribuciones Debian y derivados.

## Prerrequisitos

Deben tener instalado lo siguiente:
## Paquetes Generales
	
	   sudo apt install build-essential valgrind manpages-dev gdb feh compton rofi i3lock-fancy cmatrix htop pcmanfm vim neofetch


## Instalando bspwm
Las configuraciones solo trabajan con `bspwm`, `sxhkd` y `polybar`

		sudo apt-get install bspwm sxhkd

**NOTA**: Para los que usen Debian 10 o derivados, deben tener en cuenta que la instalación les va a traer la versión `0.9.5`, el cuál viene con un bug que se resolvió en versiones posteriores. Por eso, antes de realizar la instalación de `bspwm`, asegúrense de tener habilitado el siguiente repositorio en su archivo `/etc/apt/sources.list`

		 deb http://ftp.de.debian.org/debian sid main 

Para hacer la instalación sin tener que agregar Sid, solamente ingresar en terminal `sudo apt-get update && sudo apt-get install bspwm`, y después borrar del repositorio la línea que agregaron en `sources.list`


## Instalando Polybar
Para la instalación de polybar, asegurarse de tener incluido el siguiente backport en `/etc/apt/sources.list`:

		deb http://deb.debian.org/debian buster-backports main contrib non-free

 Ingresar por terminal lo siguiente:

		sudo apt-get install polybar


- [Polybar](https://github.com/polybar/polybar)

## Instalación

De momento, la instalación es manual. Para realizar la instalación, debemos asegurarnos de tener instalado *bspwm*, *polybar*, *Rofi*, *Compton*. También necesitaremos tener descargado *st* (incluída sus dependencias). Vamos a realizar la instalación del tema *break*.

1. Abrimos la terminal y clonamos el repositorio con el siguiente comando:

```
  git clone https://github.com/kaibakev1984/Lorblak-Dotfiles
```

![git clone](https://i.postimg.cc/kMTLn6KV/capture1.png)

2. Una vez descargado, nos dirigimos al repositorio y accedemos al directorio *break*. Tendremos lo siguiente:

![break directory](https://i.postimg.cc/GmCnSBDH/capture2.png)

Estos los son archivos que necesitaremos para configurar nuestro *Riced*.

3. El archivo *bspwmrc* es el archivo que necesitaremos para configurar *bspwm*. Para instalarlo hacemos lo siguiente:

```
  mkdir ~/.config/bspwm
  cp bspwmrc ~/.config/bspwm
```

4. El archivo `sxhkdrc` nos permite configurar los atajos de nuestro teclado. Para instalarlo hacemos lo siguiente:

```
  mkdir ~/.config/sxhkd
  cp sxhkdrc ~/.config/sxhkd
```

5. Instalamos el tema `Break` para *Rofi* ingresando lo siguiente por terminal:
```
  sudo cp break.rasi /usr/share/rofi/themes
```

6. Tenemos el directorio *polybar*, en el cual se encuentran los archivos de configuración para dicha barra. Para instalarlo hacemos lo siguiente:
```
  cp -r polybar ~/.config
```

7. Para instalar las fuentes, tenemos el directorio `.fonts`. En mi caso, lo vamos a instalar en nuestro $HOME haciendo:
```
  cp -r .fonts ~/
```

8. Una vez terminado de copiar los archivos, reiniciamos *bspwm* haciendo `super + alt + r` 

9. Para configurar `st`, primero descargamos el archivo comprimido `st.0.8.4` de este [enlace](https://st.suckless.org/). 

![st suckless terminal](https://i.postimg.cc/43p52dzN/capture3.png)

10. Nos ubicamos en donde tenemos instalado *st* y descomprimimos haciendo:

```
  tar -xvf st.0.8.4.tar.gz
```
Nos debería quedar algo así:

![st ](https://i.postimg.cc/1R8LM089/capture4.png)

11. En nuestro directorio con el tema *break* hay un archivo llamado `st-break.diff`, que contiene nuestro tema para *st*. Para instalarlo, copiamos dicho documento en el directorio donde descomprimimos *st*. Nos debería quedar algo así:

![st ls](https://i.postimg.cc/Pf007LD1/capture5.png)

12. Para instalar nuestro tema, nos ubicaremos al directorio *st.0.8.4* e ingresamos lo siguiente:

```
  sudo make uninstall
  patch -i st-break.diff
  sudo make clean install
```

13. Para el fondo de pantalla, copiamos la imagen *break.jpg* en la ruta de nuestro gusto. En mi caso lo instalo en `~/Imágenes`. Para agregarle el fondo ingresamos por terminal:

```
  feh --bg-fill ~/Imágenes/break.jpg
```

14. Nuestro tema se debería ver así:

[![capture6.png](https://i.postimg.cc/GtPPzSY7/capture6.png)](https://postimg.cc/vxB6Zh0f)
[![capture7.png](https://i.postimg.cc/6q16sBdy/capture7.png)](https://postimg.cc/gL8b8FtW)

## Enlaces útiles

* [Repositorio de Rofi](https://github.com/davatorium/rofi)
	* **NOTA**: Se puede instalar mediante:
		
				sudo apt-get install rofi
		
  	El principal problema es que, desde la instlación por línea de comandos,
			se tiene problemas con el layout con algunos temas.
			Para ello, pueden instarlo a mano, y luego clonan el repositorio,
			para copiar todos los temas bajados del repositorio, en su carpeta
			de temas **themes** de rofi, que está en la siguiente ruta:
			
				/usr/share/rofi/themes
							
* [Mutt - Cliente de Mail por Terminal](https://www.thegeekdiary.com/how-to-install-and-configure-mutt-in-centos-rhel/)
* [Vimplug - Para poner plugins a VIM](https://www.ostechnix.com/vim-plug-a-minimalist-vim-plugin-manager/)
* [i3lock-fancy](https://github.com/meskarune/i3lock-fancy)
* [SimpleDesktops - Fondos de Pantalla Minimalistas](http://simpledesktops.com/)
* [Polybar](https://github.com/regolith-linux/regolith-desktop/wiki/HowTo:-Swap-out-i3bar-for-Polybar?fbclid=IwAR3QtWfotVnkvgwtbUYXKAi9mz7sSSTlZRTmkOnqf8-UwXbhp72Dj4Pe4TI)
* [Kthulu120 Themes](https://github.com/Kthulu120/i3wm-themes) (requiere i3-gaps instalado)
* [Font Awesome](https://fontawesome.com/cheatsheet)
* [Ranger - Terminal File Manager](https://wikimatze.de/ranger-a-terminal-browser-for-vim/)
* [Gtop](https://www.bleepingcomputer.com/forums/t/667825/how-to-install-gtop-on-ubuntu/)
* [Colorizer - Vim plugin](https://github.com/lilydjwg/colorizer)
* [st - Suckless Terminal](https://st.suckless.org/)
* [pfetch](https://github.com/dylanaraps/pfetch)
* [ZSH](https://linoxide.com/tools/install-zsh-on-linux/)

##	Fuentes
Se tienen algunas fuentes básicas dentro del repositorio. Para su instalación, abrir la terminal en el directorio del repositorio e ingresar lo siguiente por terminal:

		cp -r .fonts ~/

Se puede revisar el catálogo con los íconos para estas fuentes en [Font Awesome](https://fontawesome.com/cheatsheet).

##	ST (Suckless Terminal) con dependencias incompletas
Es posible recibir los siguientes mensajes durante la instalación de st:
	
		x.c:11:10: fatal error: X11/Xatom.h: No existe el fichero o el directorio
		#include <X11/Xatom.h>
				 ^~~~~~~~~~~~~~~
		compilation terminated.
		make: *** [Makefile:22: x.o] Error 1
	
		x.c:15:10: fatal error: X11/Xft/Xft.h: No existe el fichero o el directorio
		#include <X11/Xft/Xft.h>
				 ^~~~~~~~~~~~~~~
		compilation terminated.
		make: *** [Makefile:22: x.o] Error 1

Para ambos casos, ejecutar lo siguiente en terminal:

		sudo apt-get install libx11-dev libxft-dev

##	Neofetch con imagen
Ingresar por terminal lo siguiente:

		neofetch --w3m --loop <path-image>

**NOTA**: Se debe tener instalado `w3m`.

## Galería

Para acceder a un tema, hacer click sobre la imagen del tema deseado

[![night scheme](https://i.postimg.cc/kgf40wZ8/night-scheme.png)](https://github.com/kaibakev1984/Lorblak-Dotfiles/tree/master/night)
[![lofi-rain scheme](https://i.postimg.cc/ZRCpgx4r/lofi-rain-scheme.png)](https://github.com/kaibakev1984/Lorblak-Dotfiles/tree/master/lofi-rain)
[![robocity scheme](https://i.postimg.cc/YCyw5GBy/robocity-scheme.png)](https://github.com/kaibakev1984/Lorblak-Dotfiles/tree/master/robocity)
[![forest scheme](https://i.postimg.cc/90V3dyyz/forest-scheme.png)](https://github.com/kaibakev1984/Lorblak-Dotfiles/tree/master/forest)
[![autumn scheme](https://i.postimg.cc/6pFmVdXw/autumn-scheme.png)](https://github.com/kaibakev1984/Lorblak-Dotfiles/tree/master/autumn)
[![day-city scheme](https://i.postimg.cc/tCWfYN2Q/day-city-scheme.png)](https://github.com/kaibakev1984/Lorblak-Dotfiles/tree/master/day-city)
[![raining scheme](https://i.postimg.cc/qM5b08gn/raining-scheme.png)](https://github.com/kaibakev1984/Lorblak-Dotfiles/tree/master/raining)
[![sleepy-hollow scheme](https://i.postimg.cc/rmMggjY6/sleepy-hollow.png)](https://github.com/kaibakev1984/Lorblak-Dotfiles/tree/master/sleepy-hollow)
[![girl-glasses scheme](https://i.postimg.cc/x1wCF1YR/girl-glasses-scheme.png)](https://github.com/kaibakev1984/Lorblak-Dotfiles/tree/master/girl-glasses)
[![rem scheme](https://i.postimg.cc/vDF4Lq3f/rem-scheme.png)](https://github.com/kaibakev1984/Lorblak-Dotfiles/tree/master/rem)
[![books scheme](https://i.postimg.cc/MHkBdpGn/books-scheme.png)](https://github.com/kaibakev1984/Lorblak-Dotfiles/tree/master/books)
[![old-computer scheme](https://i.postimg.cc/4dZ9Fv23/old-computer-scheme.png)](https://github.com/kaibakev1984/Lorblak-Dotfiles/tree/master/old-computer)
[![keyboard scheme](https://i.postimg.cc/MKp6g8jH/keyboard-scheme.png)](https://github.com/kaibakev1984/Lorblak-Dotfiles/tree/master/keyboard)
[![retro-cat scheme](https://i.postimg.cc/yNF2hBSZ/retro-cat-scheme.png)](https://github.com/kaibakev1984/Lorblak-Dotfiles/tree/master/retro-cat)
[![flower scheme](https://i.postimg.cc/k4NSYdRw/flower-scheme.png)](https://github.com/kaibakev1984/Lorblak-Dotfiles/tree/master/flower-scheme)
[![sunset scheme](https://i.postimg.cc/qq71YWDt/sunset-scheme.png)](https://github.com/kaibakev1984/Lorblak-Dotfiles/tree/master/sunset)
[![umbrellas scheme](https://i.postimg.cc/YqR5KGwB/umbrellas-scheme.png)](https://github.com/kaibakev1984/Lorblak-Dotfiles/tree/master/umbrellas)
[![aesthetic-sea scheme](https://i.postimg.cc/DzJHXx47/aesthetic-sea-scheme.png)](https://github.com/kaibakev1984/Lorblak-Dotfiles/tree/master/aesthetic-sea)
[![lofi-fog scheme](https://i.postimg.cc/mD7ndhSq/lofi-fog-scheme.png)](https://github.com/kaibakev1984/Lorblak-Dotfiles/tree/master/lofi-fog)
[![traffic-lights scheme](https://i.postimg.cc/J01pPx0D/traffic-lights-scheme.png)](https://github.com/kaibakev1984/Lorblak-Dotfiles/tree/master/traffic-lights)
[![rain-at-night scheme](https://i.postimg.cc/MphthqX8/rain-at-night-scheme.png)](https://github.com/kaibakev1984/Lorblak-Dotfiles/tree/master/rain-at-night)
[![rose scheme](https://i.postimg.cc/6QnzKgG4/rose-scheme.png)](https://github.com/kaibakev1984/Lorblak-Dotfiles/tree/master/rose)
[![office scheme](https://i.postimg.cc/D0ycqzp1/office-scheme.png)](https://github.com/kaibakev1984/Lorblak-Dotfiles/tree/master/office)
[![powerlines scheme](https://i.postimg.cc/BQx1LXY5/powerlines-scheme.png)](https://github.com/kaibakev1984/Lorblak-Dotfiles/tree/master/powerlines)
[![john-wick scheme](https://i.postimg.cc/LXmkpXpG/john-wick-scheme.png)](https://github.com/kaibakev1984/Lorblak-Dotfiles/tree/master/john-wick)
[![sad scheme](https://i.postimg.cc/Gm2CDVhc/sad-scheme.png)](https://github.com/kaibakev1984/Lorblak-Dotfiles/tree/master/sad)
[![castle scheme](https://i.postimg.cc/G37FWdSS/castle-scheme.png)](https://github.com/kaibakev1984/Lorblak-Dotfiles/tree/master/castle)
[![metropolis scheme](https://i.postimg.cc/7YQkwVDf/metropolis-scheme.png)](https://github.com/kaibakev1984/Lorblak-Dotfiles/tree/master/metropolis)
[![futurist scheme](https://i.postimg.cc/4xxvqkWv/futurist-scheme.png)](https://github.com/kaibakev1984/Lorblak-Dotfiles/tree/master/futurist)
[![astronaut scheme](https://i.postimg.cc/wMy1887S/astronaut-scheme.png)](https://github.com/kaibakev1984/Lorblak-Dotfiles/tree/master/astronaut)
[![john wick 2 scheme](https://i.postimg.cc/kMzVN4H9/john-wick2-scheme.png)](https://github.com/kaibakev1984/Lorblak-Dotfiles/tree/master/john-wick2)
[![cyber-hunter scheme](https://i.postimg.cc/fRjJhvRT/cyber-hunter-scheme.png)](https://github.com/kaibakev1984/Lorblak-Dotfiles/tree/master/cyber-hunter)
[![win7 scheme](https://i.postimg.cc/V5PLxSyC/win7-scheme.png)](https://github.com/kaibakev1984/Lorblak-Dotfiles/tree/master/win7)
[![murder scheme](https://i.postimg.cc/KvTfS43v/murder-scheme.png)](https://github.com/kaibakev1984/Lorblak-Dotfiles/tree/master/murder)
[![hello-world scheme](https://i.postimg.cc/CKhsqNPz/hello-world-scheme.png)](https://github.com/kaibakev1984/Lorblak-Dotfiles/tree/master/hello-world)
[![lofi-city scheme](https://i.postimg.cc/FzLy4nRn/lofi-city-scheme.png)](https://github.com/kaibakev1984/Lorblak-Dotfiles/tree/master/lofi-city)
[![smoke scheme](https://i.postimg.cc/QxcQYPvF/smoke-scheme.png)](https://github.com/kaibakev1984/Lorblak-Dotfiles/tree/master/smoke)
[![ruiner scheme](https://i.postimg.cc/jj3PJrnF/ruiner-scheme.png)](https://github.com/kaibakev1984/Lorblak-Dotfiles/tree/master/ruiner)
[![chicago95 scheme](https://i.postimg.cc/SQMCj3Sg/chicago95-scheme.png)](https://github.com/kaibakev1984/Lorblak-Dotfiles/tree/master/chicago95)
[![focus scheme](https://i.postimg.cc/7LRJZMpv/focus-scheme.png)](https://github.com/kaibakev1984/Lorblak-Dotfiles/tree/master/focus)
[![break scheme](https://i.postimg.cc/vTF1W8Y3/break-scheme.png)](https://github.com/kaibakev1984/Lorblak-Dotfiles/tree/master/break)
[![triangles scheme](https://i.postimg.cc/2jhLCWGJ/triangles-scheme.png)](https://github.com/kaibakev1984/Lorblak-Dotfiles/tree/master/triangles)
[![404-error scheme](https://i.postimg.cc/qMGt3d9x/404-error-scheme.png)](https://github.com/kaibakev1984/Lorblak-Dotfiles/tree/master/404-error)
[![soft scheme](https://i.postimg.cc/T37ptJ2y/soft-scheme.png)](https://github.com/kaibakev1984/Lorblak-Dotfiles/tree/master/soft)
[![alley scheme](https://i.postimg.cc/C5v5H2Vf/alley-scheme.png)](https://github.com/kaibakev1984/Lorblak-Dotfiles/tree/master/alley)
[![diary scheme](https://i.postimg.cc/dtx3KFC7/diary-scheme.png)](https://github.com/kaibakev1984/Lorblak-Dotfiles/tree/master/diary)
[![futurist-city scheme](https://i.postimg.cc/5twMfsbz/futurist-city-scheme.png)](https://github.com/kaibakev1984/Lorblak-Dotfiles/tree/master/futurist-city)
[![qa scheme](https://i.postimg.cc/k4yrh4Qf/qa-scheme.png)](https://github.com/kaibakev1984/Lorblak-Dotfiles/tree/master/qa)
[![qa scheme](https://i.postimg.cc/s2xK9Xfk/samurai-scheme.png)](https://github.com/kaibakev1984/Lorblak-Dotfiles/tree/master/samurai)
[![fantasy scheme](https://i.postimg.cc/gJqzF5Jd/fantasy-scheme.png)](https://github.com/kaibakev1984/Lorblak-Dotfiles/tree/master/fantasy)
[![cobra kai scheme](https://i.postimg.cc/2Smd75H2/cobra-kai-scheme.png)](https://github.com/kaibakev1984/Lorblak-Dotfiles/tree/master/cobra-kai)
[![sentre scheme](https://i.postimg.cc/bJG45CKp/Captura-de-pantalla-de-2021-01-27-00-49-38.png)](https://github.com/kaibakev1984/Lorblak-Dotfiles/tree/master/sentre)
[![climbing scheme](https://i.postimg.cc/MKnQYznW/climbing-scheme.png)](https://github.com/kaibakev1984/Lorblak-Dotfiles/tree/master/climbing)
