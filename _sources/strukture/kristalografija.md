# Kristalografija

Seje naslavljajo lastnosti makromolekulskih kristalov, ki se uporabljajo pri določanju strukture z X-žarkovno kristalografijo. Slike sej spremlja kratek opis, dodatne opombe pa so neposredno na sejah.

## Splošne lastnosti

````{card} Kanali topila v proteinskih kristalih

::::{grid} 1 1 2 2
:reverse:

:::{grid-item}
```{image} ../seje/kristali-kanali_topila.png
:name: kristali-kanali_topila
:target: https://molstar.org/viewer/?snapshot-url=https://raw.githubusercontent.com/mpavsic/sbio/main/sbio/seje/kristali-kanali_topila.molx&snapshot-url-type=molx&hide-controls=1
```
:::

:::{grid-item}
Del kristala glikolat oksidaze 2 iz špinače (PDB [1GOX](https://www.rcsb.org/structure/1GOX)), kjer le 27 % prostornine kristala predstavljajo molekule proteina, 73 % prostornine pa topilo. Molekul slednjega se zaradi neurejenosti "ne vidi", vidi se pa tiste molekule vode, ki so neposredno ob proteinskih molekulah in se tako kot le-te periodično ponavljajo v kristalu. Glikolat oksidaza sicer tvori močan tetramer, ki se preko šibkih interakcij poveže z drugim tetramerom v oktamer.
:::
::::

Nekateri kristali vsebujejo še večji delež topila, znani pa so tudi zelo na gosto pakirani kristali, kjer topilo predstavlja manj kot 1 % prostornine kristala. En tak primer je kristal 6. in 7. domene mišjega faktorja H, ki regulira delovanje komplementa (PDB [2YBY](https://www.rcsb.org/structure/2YBY)), predpripravljeno sejo si lahko ogledate [tukaj](https://molstar.org/viewer/?snapshot-url=https://raw.githubusercontent.com/mpavsic/sbio/main/sbio/seje/kristali-tesno_pakiranje.molx&snapshot-url-type=molx&hide-controls=1).

```{dropdown} Povezave
```{image} ../seje/kristali-kanali_topila-qr.png
:width: 200px
:target: https://molstar.org/viewer/?snapshot-url=https://raw.githubusercontent.com/mpavsic/sbio/main/sbio/seje/kristali-kanali_topila.molx&snapshot-url-type=molx&hide-controls=1
```
````

````{card} Ločljivost: primerjava elektronske gostote v kristalih istih proteinov pri različni ločljivosti

::::{grid} 1 1 2 2
:reverse:

:::{grid-item}
```{image} ../seje/kristali-locljivost-1.png
:name: kristali-locljivost-1
:target: https://molstar.org/viewer/?snapshot-url=https://raw.githubusercontent.com/mpavsic/sbio/main/sbio/seje/kristali-locljivost.molx&snapshot-url-type=molx&hide-controls=1
```
:::

:::{grid-item}
Različne kristalne strukture so določene pri različnih ločljivostih. Na ločljivost vpliva v prvi vrsti notranja urejenost v kristalu (ki pa je spet odvisna od številnih faktorjev kot so strukturna "urejenost" proteina, način zlaganja molekul v kristalno mrežo, kristalni kontakti, ...), odvisna je tudi čisto tehničnih karakteristik difraktometra (na sinhrotronih se dosega višje ločljivosti).

Primer proteina, katerega struktura je določena pri izredno visoki (0,77 Å) in pa ločeno pri srednji ločljivosti (2,67 Å), je mioglobin iz kita glavača (PDB [5YCE](https://www.rcsb.org/structure/5YCE) za 0,77 Å in [108M](https://www.rcsb.org/structure/108m) za 2,67 Å). Iz primerjave kart elektronske gostote je jasno razvidno, da v primeru atomske ločljivosti opazimo oblake elektronske gostote, ki ustrezajo posameznim atomom, jasno pa so razvidne tudi alternativne konformacije delov polipeptidne verige ali posameznih aminokislinskih ostankov. V primeru slabše ločljivosti take podrobnosti niso razvidne.

Drug primer je struktura C-končne DNA-vezavne domene OmpR iz bakterije *Escherichia coli*. Znanih je več struktur, od teh pa je ena bila določena pri ločljivosti 3,56 Å (PDB [6LXL](https://www.rcsb.org/structure/6LXL)), druga pa pri 1,95 Å (PDB [1OPC](https://www.rcsb.org/structure/1opc)).

:::
::::

Prikazi struktur in elektronskih gostot omenjenih struktur so na voljo v ločenih sejah:
- mioglobin iz kita glavača: [2,67 Å](https://molstar.org/viewer/?snapshot-url=https://raw.githubusercontent.com/mpavsic/sbio/main/sbio/seje/kristali-locljivost-1niz.molx&snapshot-url-type=molx&hide-controls=1) in [0,77 Å](https://molstar.org/viewer/?snapshot-url=https://raw.githubusercontent.com/mpavsic/sbio/main/sbio/seje/kristali-locljivost-1vis.molx&snapshot-url-type=molx&hide-controls=1);
- DNA-vezavna domena OmpR iz bakterije *E. coli*: [3,56 Å](https://molstar.org/viewer/?snapshot-url=https://raw.githubusercontent.com/mpavsic/sbio/main/sbio/seje/kristali-locljivost-2niz.molx&snapshot-url-type=molx&hide-controls=1) in [1,95 Å](https://molstar.org/viewer/?snapshot-url=https://raw.githubusercontent.com/mpavsic/sbio/main/sbio/seje/kristali-locljivost-2vis.molx&snapshot-url-type=molx&hide-controls=1).

Elektronska gostota okoli posameznih ostankov je bolje vidna, če izklopite prikaz traku.

````

## Simetrija

````{card} Kristalografska simetrija in proteinski oligomeri (primer 1)

::::{grid} 1 1 2 2
:reverse:

:::{grid-item}
```{image} ../seje/kristali-simetrija-1.png
:name: kristali-simetrija-1
:target: https://molstar.org/viewer/?snapshot-url=https://raw.githubusercontent.com/mpavsic/sbio/main/sbio/seje/kristali-simetrija-1.molx&snapshot-url-type=molx&hide-controls=1
```
:::

:::{grid-item}
Pri homo-oligomernih proteinih se pogosto zgodi, da je v asimetrični enoti kristala le ena podenota, celoten biološko relevanten oligomer pa dobimo z aplikacijo ustreznih simetrijskih operacij. Primer je kristalna struktura zunajceličnega dela proteina EpCAM, ki tvori biološko relevanten močan dimer (konstanta disociacije v raztopini je v nanomolarnem območju). Dimer ima dvoštevno os ciklične simetrije ($C2$), kar pomeni, da lahko iz ene kopije podenote dobimo drugo z rotacijo okoli te osi za 180°. V kristalu ta os sovpada z $2_1$ osjo prostorske skupine (v tej monoklinski $C_1 2_1$ prostorski skupini so v osnovni celici 4 asimetrične enote). Tako je v asimetrični enoti le ena kopija polipeptidne verige oz. ena podenota, biolološko relevanten dimer pa dobimo z aplikacijo rotacije za 180° okoli ustrezne osi. V osnovni celici tega kristala so 4 polipeptidne verige.

:::
::::

```{dropdown} Povezave
```{image} ../seje/kristali-simetrija-1-qr.png
:width: 200px
:target: https://molstar.org/viewer/?snapshot-url=https://raw.githubusercontent.com/mpavsic/sbio/main/sbio/seje/kristali-simetrija-1.molx&snapshot-url-type=molx&hide-controls=1
```
````

````{card} Kristalografska simetrija in proteinski oligomeri (primer 2)

::::{grid} 1 1 2 2
:reverse:

:::{grid-item}
```{image} ../seje/kristali-simetrija-2.png
:name: kristali-simetrija-2
:target: https://molstar.org/viewer/?snapshot-url=https://raw.githubusercontent.com/mpavsic/sbio/main/sbio/seje/kristali-simetrija-2.molx&snapshot-url-type=molx&hide-controls=1
```
:::

:::{grid-item}
Eden izmed mnogih primerov, kjer osi simetrije homo-oligomernega proteina sovpadajo z osmi prostorske skupine, je tudi kristal keto reduktaze iz žuželke *Bemisia argentifolii*, ki rada napada božične zvezde (PDB [1E3J](https://www.rcsb.org/structure/1E3J)). Biološko relevantna oligomerna oblika tega encima je homo-tetramer, a v asimetrični enoti kristala je le ena podenota. Med pari podenot tetramera so dvoštevne simetrijske osi – v tetrameru so take osi 3, druga na drugo so pravokotne, v takem primeru govorimo o dihedralni simetriji tipa $D2$.

:::
::::

```{dropdown} Povezave
```{image} ../seje/kristali-simetrija-2-qr.png
:width: 200px
:target: https://molstar.org/viewer/?snapshot-url=https://raw.githubusercontent.com/mpavsic/sbio/main/sbio/seje/kristali-simetrija-2.molx&snapshot-url-type=molx&hide-controls=1
```
````

````{card} Translacijska nekristalografska simetrija

::::{grid} 1 1 2 2
:reverse:

:::{grid-item}
```{image} ../seje/kristali-tncs.png
:name: kristali-ncs
:target: https://molstar.org/viewer/?snapshot-url=https://raw.githubusercontent.com/mpavsic/sbio/main/sbio/seje/kristali-tncs.molx&snapshot-url-type=molx&hide-controls=1
```
:::

:::{grid-item}
Primer posebne vrste nekristalografske simetrije, t.i. translacijske NCS (tNCS), je struktura kokošjega kalmodulina (PDB [1UP5](https://www.rcsb.org/structure/1UP5)), kjer sta v asimetrični enoti dve kopiji te molekule. Na hitro bi skoraj rekli, da bi lahko iz ene kopije dobili drugo zgolj z enostavno translacijo, a to ne bo šlo, saj se molekuli
razlikujeta v konformaciji. V seji so kopije molekul z isto konformacijo obarvane z enako barvo (oranžna oz. modra za vsako od konformacij). Razlike v konformaciji med molekulama v isti asimetrični enoti najbolje razkrije superpozicija, čeprav jih pozorno oko opazi že brez tega.

:::
::::

```{dropdown} Povezave
```{image} ../seje/kristali-tncs-qr.png
:width: 200px
:target: https://molstar.org/viewer/?snapshot-url=https://raw.githubusercontent.com/mpavsic/sbio/main/sbio/seje/kristali-tncs.molx&snapshot-url-type=molx&hide-controls=1
```
````
