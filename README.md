# Mobian-PinePhone-setup
How I set up my PinePhone (amended).

# Basics

``sudo apt install openssh-server``

``ip addr # to get ip address``

``ssh mobian@YOURPINEPHONEIP`` # it's easier to ssh in for the set up

``sudo apt update``

``sudo apt upgrade``

``apt install linux-image-5.11-sunxi64`` # upgrade to 5.11

``sudo reboot``

# Utils

``sudo apt -y install git pandoc xlsx2csv ghostscript poppler-utils mosh zathura feh ncdu exfat-fuse exfat-utils`` 

# Latex

Download latest texlive:

``wget "http://mirror.ctan.org/systems/texlive/tlnet/install-tl-unx.tar.gz"``

``tar -xzf install-tl-unx.tar.gz``

``cd install-tl-20210321/``

``sudo ./install-tl``

press ``I``

(Time used for installing the packages: 132:10)

``vim ~/.bashrc``

Add to file:

``MANPATH=/usr/local/texlive/2020/texmf-dist/doc/man``

``INFOPATH=/usr/local/texlive/2020/texmf-dist/doc/info``

``PATH=$PATH:/usr/local/texlive/2020/bin/aarch64-linux``

``export PATH``

exit then:

``source ~/.bashrc``

# R

## Required for packages

``sudo apt -y install libxml2-dev libssl-dev libcurl4-openssl-dev libgdal-dev libgit2-dev``

libssl-dev # for openssl for R
libcurl4-openssl-dev # for curl for R
libgdal-dev # for rgdal for R
libgit2-dev # for devtools in R

## Install (This will take a very long time)

``sudo apt -y install r-base``

``sudo R``

Then from within R:

``install.packages(c("ggplot2","tidyverse","knitr","ggthemes","scales","ggmap","plotly","ggfortify","leaflet","leaflet.extras","rgdal","forecast","treemapify","dbscan","survival","googleVis","rmarkdown","flexdashboard","highcharter","devtools","maptools","treemap","networkD3","visNetwork","DiagrammeR","DT","ggcorrplot", "Hmisc", "anomalize", "fpp2", "h2o", "sweep", "timetk", "xgboost","survminer","ggwordcloud","this.path","mapproj"), repo = 'https://mac.R-project.org')``

Decided not to install mapview and prophet.

# Python stuff

``sudo apt install python3-pip``

``sudo apt install python3-pandas``

``pip3 install boto3``

# Set up Git and SSH keys

``git config --global user.name "John Doe"``

``git config --global user.email john.doe@emailprovider.com``

``ssh-keygen -t rsa -b 4096 -C "john.doe@emailprovider.com"``

``cat ~/.ssh/id_rsa.pub``

Add to git settings in web git service.

Add some aliases to short cut commands, e.g.:

Add public key to any servers you need to access:

``ssh-copy-id -i ~/.ssh/id_rsa.pub YOURUSERNAMEE@SERVERIPADDRESS``

``vim .bashrc``

and add:

alias work='ssh YOURUSERNAME@SERVERIPADDRESS'

(note doesn't work if add to bash_profile)

# Chromium

Obviously optional.  See https://forum.pine64.org/showthread.php?tid=12497&page=2

``flatpak remote-add --if-not-exists flathub https://flathub.org/repo/flathub.flatpakrepo``

``flatpak search Chromium``

``flatpak install org.chromium.Chromium``

Then:

``scale-to-fit Chromium on``

Then head to the webstore and install the ``Mobile View`` extension.

# Tweaks

https://wiki.mobian-project.org/doku.php?id=themes

## Prevent Sleep in an SSH session

``if [[ -n $SSH_CONNECTION ]]; then
  : $(gnome-session-inhibit --inhibit suspend \
        --reason "SSH connection is active" \
        --inhibit-only) &
fi``

## Prefer dark themes

`` ~/.config/gtk-3.0/settings.ini ``

and add this to file:

``[Settings]
gtk-application-prefer-dark-theme = true``

## Change icons

Icons that work well on the phone:

- Uniform+ (a few missing bits on the keyboard though)
- Tela-circle
- Numix-Circle
- Cupertino-BigSur-iCons

Get icon names from ``/usr/share/icons/``

or from ``~/.local/share/icons``

Change with for example: ``gsettings set org.gnome.desktop.interface icon-theme 'Cupertino-BigSur-iCons'``
