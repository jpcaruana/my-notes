#Convertir à l'aide de LibreOffice --> PDF

````bash
libreoffice -headless -convert-to pdf  pres.ppt
````

#Convertir depuis un PDF en JPG
##image magick

PPT --> PDF --> JPEG en 3 résolutions (800 1024 1280)

````bash
for size in 800 1024 1280; do
    mkdir $size
    cd $size
    convert -quality 100 -density 150x150 -geometry ${size}x${size} ../pres.pdf pres-%00d.jpg
    cd -
done
````

prend 1 minute sur mon poste pour tout convertir (en 3 résolutions)

21s pour la résolution maximale

vignettes :

````bash
convert -quality 100  -geometry 256x256 pres.pdf vignette-pres-%00d.jpg
````

(14s)

##ghostscript
###Split d'un PDF en fichiers PNG

````bash
gs -dSAFER -dBATCH -dNOPAUSE -sDEVICE=png16m -dGraphicsAlphaBits=4 -dTextAlphaBits=4 -sOutputFile='page-%00d.png' -r150 pres.pdf
````
16s 

###Split d'un PDF en fichiers PDF (un par page)

Nécessite la présence du fichier "pdf_info.ps"  :http://svn.ghostscript.com/ghostscript/trunk/gs/toolbin/pdf_info.ps (5.6 ko)

````bash
NB_PAGES=`gs -q -dNODISPLAY -sFile=pres.pdf pdf_info.ps | grep pages | awk '{print $3}'` && 
for ((PAGE=1;PAGE<=$NB_PAGES;++PAGE))
    do echo "Processing page $PAGE on $NB_PAGES"
    gs -q -dNOPAUSE -dBATCH -sDEVICE=pdfwrite -sOutputFile="page-${PAGE}.pdf" -dFirstPage=$PAGE -dLastPage=$PAGE pres.pdf 2> /dev/null
done
````bash

10s (pour 37 pages)
