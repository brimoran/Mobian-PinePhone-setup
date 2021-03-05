# Mobian-PinePhone-setup
How I set up my PinePhone

# Basics

``apt install openssh-server``

``ip addr # to get ip address``

``ssh mobian@YOURPINEPHONEIP`` # it's easier to ssh in for the set up

``sudo apt update``

``sudo apt dist-upgrade``

``sudo apt autoremove``

``cat /etc/issue`` # check version

# Utils

``sudo apt install git`` 

``sudo apt install pandoc``

``sudo apt install xlsx2csv``

``sudo apt install ghostscript``

``sudo apt install poppler-utils``

``sudo apt install mosh``

``sudo apt install zathura``

``sudo apt install feh``

``sudo apt install ncdu``

# Latex

Download latest texlive:

``wget "http://mirror.ctan.org/systems/texlive/tlnet/install-tl-unx.tar.gz"``


``tar -xzf install-tl-unx.tar.gz``

``cd install-tl-20210302/``

``sudo ./install-tl``

press ``I``

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

``sudo apt install libxml2-dev``

``sudo apt install libssl-dev # for openssl for R``

``sudo apt -y install libcurl4-openssl-dev # for curl for R``

``sudo apt -y install libgdal-dev # for rgdal for R``

``sudo apt -y install libgit2-dev # for devtools in R``

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

# Set up Git

``git config --global user.name "John Doe"``

``git config --global user.email john.doe@emailprovider.com``

``ssh-keygen -t rsa -b 4096 -C "john.doe@emailprovider.com"``

``cat ~/.ssh/id_rsa.pub``

Add to git settings in web git service.

# Chromium

Obviously optional.  See https://forum.pine64.org/showthread.php?tid=12497&page=2

``flatpak remote-add --if-not-exists flathub https://flathub.org/repo/flathub.flatpakrepo``

``flatpak search Chromium``

``flatpak install org.chromium.Chromium``

Then:

``scale-to-fit Chromium on``

Then head to the webstore and install the ``Mobile View`` extension.
