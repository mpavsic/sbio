# Primarna struktura

## Aminokislinski ostanki

````{card} Označevanje atomov aminokislinskih ostankov

::::{grid} 1 1 2 2
:reverse:

:::{grid-item}
```{image} ../seje/ak-abeceda.png
:name: ak-abeceda
:target: https://molstar.org/viewer/?snapshot-url=https://raw.githubusercontent.com/mpavsic/sbio/main/sbio/seje/ak-abeceda.molx&snapshot-url-type=molx&hide-controls=1
```
:::

:::{grid-item}
Elementnim oznakam atomov aminokislin(skih ostankov) po dogovoru dodajamo majhne črke grške abecede začenpi z $\alpha$ ter eventuelno še arabske številke, s čimer vsak atom dobi unikatno oznako. Programi za vizualizacijo grške črke ponavadi pretvorijo kar v latinske in na tak način so atomi označeni tudi v datotekah PDB in (mm)CIF – pri tem npr. $\alpha$ postane A itd. (vse pretvorbe so zbrane v [tabeli](tabela-grske-latinske-oznake)).

V seji je peptid z aminokislinskim zaporedjem GASTCDNEQHPLIVMKRFYW (torej vseh 20 standarnih aminokislinskih ostankov), kjer so atomi označeni v skladu z zgoraj omenjeno nomenklaturo.
:::
::::

Za ogled je na voljo tudi [seja](https://molstar.org/viewer/?snapshot-url=https://raw.githubusercontent.com/mpavsic/sbio/main/sbio/seje/ak-abeceda_H.molx&snapshot-url-type=molx&hide-controls=1), kjer so prikazani in označeni vodikovi atomi. Bodite pozorni na protonacijsko stanje N- ter C-konca in aspartatnega, glutamatnega, argininskega, lizinskega in histidinskega ostanka.

(tabela-grske-latinske-oznake)=
**Tabela pretvorb iz grških v latinske oznake**

| grška oznaka | latinska oznaka | ime     | primer                                    |
| :----------- | :-------------- | :------ | :---------------------------------------- |
| $\alpha$     | A               | alfa    | CA (vse ak)                               |
| $\beta$      | B               | beta    | CB (Ala)                                  |
| $\gamma$     | G               | gama    | CG (Glu), OG (Ser)                        |
| $\delta$     | D               | delta   | CD (Lys), CD (Glu), OD1 (Asp), SD (Met)   |
| $\epsilon$   | E               | epsilon | CE1 (Tyr), OE2 (Glu), NE2 (His), CE (Met) |
| $\zeta$      | Z               | zeta    | CZ (Tyr), CZ3 (Trp), CZ (Arg)             |
| $\eta$       | H               | eta     | NH1 (Arg), CH2 (Trp), OH (Tyr)            |



```{dropdown} Povezave
```{image} ../seje/ak-abeceda-qr.png
:width: 200px
:target: https://molstar.org/viewer/?snapshot-url=https://raw.githubusercontent.com/mpavsic/sbio/main/sbio/seje/ak-abeceda.molx&snapshot-url-type=molx&hide-controls=1
```
````

````{card} Kiralnost aminokislinskih ostankov

::::{grid} 1 1 2 2
:reverse:

:::{grid-item}
```{image} ../seje/ak-D-ak.png
:name: vijacnica-beta-2
:target: https://molstar.org/viewer/?snapshot-url=https://raw.githubusercontent.com/mpavsic/sbio/main/sbio/seje/ak-D-ak.molx&snapshot-url-type=molx&hide-controls=1
```
:::

:::{grid-item}
Nekateri peptidi in proteini vsebujejo D-aminokislinske ostanke, ki so lahko ključni za samo strukturo, hkrati pa pogosto omogočajo odpornost peptidne vezi, v kateri so udeleženi, na "napad" s strani peptidaz, ki so večinoma prilagojene za hidrolizo peptidnih vezi med L-aminokislinskimi ostanki. Primer je antibiotik gramicidin A iz *Bacillus brevis* (PDB [1BDW](https://www.rcsb.org/structure/1BDW)), pri katerem si alternirajoče sledijo D- in L-aminokislinski ostanki.
:::
::::

*Naj vas razlika v imenu gramicidin A (na tej strani) in gramicidin D (na strani RCSB PDB) ne zmoti – gramicidin A je ime za točno določeno obliko, medtem ko je gramicidin D mešanica gramicidina A, B in C, od tega pa ima vsak 2 izoobliki ...*

> **V razmislek**: Aktivna oblika gramicidina A je dimer dveh kratkih verig. Prepoznate kak poseben vzorec vodikovih vezi med glavnima verigama v dimeru?

```{dropdown} Povezave
```{image} ../seje/ak-D-ak-qr.png
:width: 200px
:target: https://molstar.org/viewer/?snapshot-url=https://raw.githubusercontent.com/mpavsic/sbio/main/sbio/seje/ak-D-ak.molx&snapshot-url-type=molx&hide-controls=1
```
````
## Peptidna vez

````{card} Izopeptidna vez

::::{grid} 1 1 2 2
:reverse:

:::{grid-item}
```{image} ../seje/peptidna_vez-izopeptidna.png
:name: peptidna_vez-izopeptidna
:target: https://molstar.org/viewer/?snapshot-url=https://raw.githubusercontent.com/mpavsic/sbio/main/sbio/seje/peptidna_vez-izopeptidna.molx&snapshot-url-type=molx&hide-controls=1
```
:::

:::{grid-item}
Primer izopeptidne vezi, ki nastane v naravi spontano, je izopeptidna vez med Asp in Lys v domeni CnaB2 proteina FbaB iz organizma *Streptococcus pyogenes*, pri čemer sta udeležena ostanka del iste polipeptidne verige. Za uporabo v laboratorijske in druge namene so verigo CnaB2 razdružili v peptid SpyTag in majhen protein SpyCatcher, med katerima pa ob tvorbi njunega kompleksa še vedno spontano nastane izopeptidna vez. Ta sistem je zelo uporaben za konjugacijo rekombinantnih proteinov. Osnovno varianto so z uvedbo mutacij in ob pomoči usmerjene evolucije še izboljšali, tako da reakcija poteče hitreje.
:::
::::

```{dropdown} Povezave
```{image} ../seje/peptidna_vez-izopeptidna-qr.png
:width: 200px
:target: https://molstar.org/viewer/?snapshot-url=https://raw.githubusercontent.com/mpavsic/sbio/main/sbio/seje/peptidna_vez-izopeptidna.molx&snapshot-url-type=molx&hide-controls=1
```
````

````{card} Cis konfiguracija peptidne vezi

::::{grid} 1 1 2 2
:reverse:

:::{grid-item}
```{image} ../seje/peptidna_vez-cis.png
:name: peptidna_vez-cis
:target: https://molstar.org/viewer/?snapshot-url=https://raw.githubusercontent.com/mpavsic/sbio/main/sbio/seje/peptidna_vez-cis.molx&snapshot-url-type=molx&hide-controls=1
```
:::

:::{grid-item}
Cis konfugiracija peptidne vezi je v proteinih relativno redka – ne ravno pogosta je že pri {Pro}–Pro, prava redkost pa je pri {Pro}–{Pro} vezeh. V strukturi človeškega koagulacijskega faktorja XIII (PDB [1F13](https://www.rcsb.org/structure/1F13), dimer), določeni pri ločljivosti 2,1 Å, sta razvidni obe! Cis konfiguracija vezi Arg310–Tyr311 je pomemben faktor pri strukturi v bližini funkcionalnega mesta, Gln425–Phe426 pa pri dimerizaciji. Zanimivo, v predhodno določenih strukturah tega proteina so zaradi slabše ločljivosti ti dve vezi zmodelirali v trans konfiguraciji (strukturi [1GGT](https://www.rcsb.org/structure/1GGT) pri 2,65 Å in [1FIE](https://www.rcsb.org/structure/1FIE) pri 2,5 Å). V strukturi 1F13 je lepo razvidno, da CO in NH skupini cis peptidne vezi Arg310–Tyr311 sodelujeta v vodikovih vezeh z ogrodjem drugega dela iste polipeptidne verige, pri 1FIE pa tega ni.
Posamezna podenota dimera v strukturi 1F13 vsebuje tudi dve cis peptidni vezi, pri katerih je udeležen prolinski ostanek, primer je vez Gly410–Pro411.

:::
::::

Priložena seja vsebuje več posnetkov in sicer posamični prikaz cis peptidnih vezi Arg310–Tyr311, Gln425–Phe426 in Gly410–Pro411, superpozicijo Arg310–Tyr311 iz PDB 1F13 (cis) in 1FIE (trans), zraven tega pa še ločen prikaz okoliških ostankov z nekovalentimi interakcijami za Arg310–Tyr311 v cis (1F13) in trans (1FIE) konfiguraciji.

```{dropdown} Povezave
```{image} ../seje/peptidna_vez-cis-qr.png
:width: 200px
:target: https://molstar.org/viewer/?snapshot-url=https://raw.githubusercontent.com/mpavsic/sbio/main/sbio/seje/peptidna_vez-cis.molx&snapshot-url-type=molx&hide-controls=1
```
````