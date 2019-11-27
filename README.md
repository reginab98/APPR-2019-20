# Analiza potovanj prebivalcev Slovenije

## Osnovna ideja
Analizirala bom potovanja prebivalcev Slovenije. Preučevala bom vzroke za odhod oziroma neodhod na pot, kdo potuje(starost, izobrazba, finančno stanje) in s kom, vrste potovanj in izdatki za potovanja.
Nekoliko bolj se bom osredotočila na potovanja z letali. Zanimale me bodo destinacije in pa kakšen delež prebivalstva Slovenije potuje z letali v primerjavi z drugimi državami sveta.

## Opis podatkovnih virov
Podatke bom iskala na dveh spletnik straneh:
* SURS
Podatki so na voljo v CSV, XML, JSON, PX obliki.

* gapminder
Podatki so na voljo v CSV in XLSX obliki.

## Zasnova podatkovnega modela

Podatki (SURS):
* enodnevni izleti(povprečni izdatki, struktura izdatkov, vrsta izleta, država izleta)
https://pxweb.stat.si/SiStatDb/pxweb/sl/20_Ekonomsko/20_Ekonomsko__21_gostinstvo_turizem__06_potovanja__35_21703_enodnevni_izleti_cetrt/?tablelist=true

* razlogi za neodhod(spol, starost, izobrazba, zaposlitveni status, velikost gospodinjstva, mesečni neto dohodek, stopnja urbanizacije)
https://pxweb.stat.si/SiStatDb/pxweb/sl/20_Ekonomsko/20_Ekonomsko__21_gostinstvo_turizem__06_potovanja__15_21699_razlogi_neodhod_cetrt/?tablelist=true

* značilnosti potovanj(občine, glavni razlog za potovanje, destinacija in cilj, udeleženost otrok)
https://pxweb.stat.si/SiStatDb/pxweb/sl/20_Ekonomsko/20_Ekonomsko__21_gostinstvo_turizem__06_potovanja__25_21701_znacilnosti_cetrt/?tablelist=true

* udeleženost prebivalcev na turističnih potovanjih(spol, starost, izobrazba, zaposlitveni status, velikost gospodinjstva, mesečni neto dohodek, stopnja urbanizacije)
https://pxweb.stat.si/SiStatDb/pxweb/sl/20_Ekonomsko/20_Ekonomsko__21_gostinstvo_turizem__06_potovanja__05_21697_udelezenost_cetrt/?tablelist=true

* letališki potniški glede na prihod/odhod letal ter redne/posebne prevoze po državah prihoda/odhoda letal (Ljubljana, Letališče Jožeta Pučnika)
https://pxweb.stat.si/SiStatDb/pxweb/sl/20_Ekonomsko/20_Ekonomsko__22_transport__05_22219_zracni_transport/2221901s.px/

Podatki (gapminder):
https://www.gapminder.org/data/
* število letalskih potnikov po državah sveta
* število prebivalcev po državah sveta
(da bom lahko izračunala delež potujočih)

## Plan dela
Uvoz podatkov, odstranitev podatkov, ki jih ne bom analizirala, analiza podatkov in prikaz rezultatov. 

# Analiza podatkov s programom R, 2019/20

Repozitorij z gradivi pri predmetu APPR v študijskem letu 2019/20

* [![Shiny](http://mybinder.org/badge.svg)](http://mybinder.org/v2/gh/jaanos/APPR-2019-20/master?urlpath=shiny/APPR-2019-20/projekt.Rmd) Shiny
* [![RStudio](http://mybinder.org/badge.svg)](http://mybinder.org/v2/gh/jaanos/APPR-2019-20/master?urlpath=rstudio) RStudio

## Tematika

Izbrali si boste temo, s katero se bo vaš projekt ukvarjal.
Tukaj boste napisali, kje ste dobili podatke, ter kakšen je vaš cilj.

## Program

Glavni program in poročilo se nahajata v datoteki `projekt.Rmd`.
Ko ga prevedemo, se izvedejo programi, ki ustrezajo drugi, tretji in četrti fazi projekta:

* obdelava, uvoz in čiščenje podatkov: `uvoz/uvoz.r`
* analiza in vizualizacija podatkov: `vizualizacija/vizualizacija.r`
* napredna analiza podatkov: `analiza/analiza.r`

Vnaprej pripravljene funkcije se nahajajo v datotekah v mapi `lib/`.
Podatkovni viri so v mapi `podatki/`.
Zemljevidi v obliki SHP, ki jih program pobere,
se shranijo v mapo `../zemljevidi/` (torej izven mape projekta).

## Potrebni paketi za R

Za zagon tega vzorca je potrebno namestiti sledeče pakete za R:

* `knitr` - za izdelovanje poročila
* `rmarkdown` - za prevajanje poročila v obliki RMarkdown
* `shiny` - za prikaz spletnega vmesnika
* `DT` - za prikaz interaktivne tabele
* `rgdal` - za uvoz zemljevidov
* `rgeos` - za podporo zemljevidom
* `digest` - za zgoščevalne funkcije (uporabljajo se za shranjevanje zemljevidov)
* `readr` - za branje podatkov
* `rvest` - za pobiranje spletnih strani
* `tidyr` - za preoblikovanje podatkov v obliko *tidy data*
* `dplyr` - za delo s podatki
* `gsubfn` - za delo z nizi (čiščenje podatkov)
* `ggplot2` - za izrisovanje grafov
* `mosaic` - za pretvorbo zemljevidov v obliko za risanje z `ggplot2`
* `maptools` - za delo z zemljevidi
* `extrafont` - za pravilen prikaz šumnikov (neobvezno)

## Binder

Zgornje [povezave](#analiza-podatkov-s-programom-r-201819)
omogočajo poganjanje projekta na spletu z orodjem [Binder](https://mybinder.org/).
V ta namen je bila pripravljena slika za [Docker](https://www.docker.com/),
ki vsebuje večino paketov, ki jih boste potrebovali za svoj projekt.

Če se izkaže, da katerega od paketov, ki ji potrebujete, ni v sliki,
lahko za sprotno namestitev poskrbite tako,
da jih v datoteki [`install.R`](install.R) namestite z ukazom `install.packages`.
Te datoteke (ali ukaza `install.packages`) **ne vključujte** v svoj program -
gre samo za navodilo za Binder, katere pakete naj namesti pred poganjanjem vašega projekta.

Tako nameščanje paketov se bo izvedlo pred vsakim poganjanjem v Binderju.
Če se izkaže, da je to preveč zamudno,
lahko pripravite [lastno sliko](https://github.com/jaanos/APPR-docker) z želenimi paketi.

Če želite v Binderju delati z git,
v datoteki `gitconfig` nastavite svoje ime in priimek ter e-poštni naslov
(odkomentirajte vzorec in zamenjajte s svojimi podatki) -
ob naslednjem zagonu bo mogoče delati commite.
Te podatke lahko nastavite tudi z `git config --global` v konzoli
(vendar bodo veljale le v trenutni seji).
