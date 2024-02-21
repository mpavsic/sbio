# Primarna struktura

````{card} Označevanje atomov aminokislinskih ostankov

::::{grid} 1 1 2 2
:reverse:

:::{grid-item}
```{image} ../seje/ak-abeceda.png
:name: ak-abeceda
:target: https://molstar.org/viewer/?snapshot-url=https://github.com/mpavsic/sbio/blob/main/sbio/seje/ak-abeceda.molx&snapshot-url-type=molx&hide-controls=1
```
:::

:::{grid-item}
Elementnim oznakam atomov aminokislin(skih ostankov) po dogovoru dodajamo majhne črke grške abecede začenpi z $\alpha$ ter eventuelno še arabske številke, s čimer vsak atom dobi unikatno oznako. Programi za vizualizacijo grške črke ponavadi pretvorijo kar v latinske in na tak način so atomi označeni tudi v datotekah PDB in (mm)CIF – pri tem npr. $\alpha$ postane A itd. (vse pretvorbe so zbrane v [tabeli](tabela-grske-latinske-oznake)).

V seji je peptid z aminokislinskim zaporedjem GASTCDNEQHPLIVMKRFYW (torej vseh 20 standarnih aminokislinskih ostankov), kjer so atomi označeni v skladu z zgoraj omenjeno nomenklaturo.
:::
::::

Za ogled je na voljo tudi [seja](https://molstar.org/viewer/?snapshot-url=https://github.com/mpavsic/sbio/blob/main/sbio/seje/ak-abeceda_H.molx&snapshot-url-type=molx&hide-controls=1), kjer so prikazani in označeni vodikovi atomi. Bodite pozorni na protonacijsko stanje N- ter C-konca in aspartatnega, glutamatnega, argininskega, lizinskega in histidinskega ostanka.

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
:target: https://molstar.org/viewer/?snapshot-url=https://github.com/mpavsic/sbio/blob/main/sbio/seje/ak-abeceda.molx&snapshot-url-type=molx&hide-controls=1
```
````

````{card} Kiralnost aminokislinskih ostankov

::::{grid} 1 1 2 2
:reverse:

:::{grid-item}
```{image} ../seje/ak-D-ak.png
:name: vijacnica-beta-2
:target: https://molstar.org/viewer/?snapshot-url=https://github.com/mpavsic/sbio/blob/main/sbio/seje/ak-D-ak.molx&snapshot-url-type=molx&hide-controls=1
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
:target: https://molstar.org/viewer/?snapshot-url=https://github.com/mpavsic/sbio/blob/main/sbio/seje/ak-D-ak.molx&snapshot-url-type=molx&hide-controls=1
```
````


