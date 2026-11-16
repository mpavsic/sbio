# Vaje pri predmetu Uporaba proteomskih podatkov
## Integrativno modeliranje kompleksa IL-7–IL-7Rα

**Prevideno trajanje:** približno 2 uri  
**Programi:** UCSF ChimeraX z dodatkom XMAS, [HADDOCK 2.4](https://wenmr.science.uu.nl/haddock2.4/), [DisVis](https://wenmr.science.uu.nl/disvis/)  
**Vhodne datoteke:** `IL7.pdb`, `IL7R.pdb`, `BS3.tsv`, `EDC.tsv`

### Namen vaje

Spoznati, kako z masno spektrometrijo prečnih povezav (XL-MS) pripišemo omejitve razdalj in jih uporabimo pri napovedovanju kompleksov. Prečne povezave bomo najprej vizualizirali na strukturi z orodjem XMAS. Model kompleksa bomo pripravili z makromolekularnim sidranjem na strežniku HADDOCK. V vmesnem času bomo z orodjem DisVis vizualizirali interakcijski prostor, ki je dostopen omejitvam razdalj. Primerjali bomo prostor, ki ga omejujejo prečne povezave z BS3 in prostor, ki ga omejujejo prečne povezave z BS3 in EDC.

> **Opomba:** Po inštalaciji orodja XMAS bo verjetno potrebno spremeniti inštalacije pandas in numpy, ki jih uporablja ChimeraX. 
>
><code>devel pip install pandas==2.2.3 --no-deps</code>
>
><code>devel pip install pytz</code>

---

### Biološko ozadje

**Interlevkin 7 (IL-7)** je citokin, ki sodeluje pri razvoju, preživetju in homeostazi limfocitov, zlasti celic T. Ima značilno zgradbo citokinov s štirimi α-vijačnicami.

**Receptor IL-7Rα** je podenota receptorja, ki prepozna IL-7. Pri signalizaciji sodeluje še receptorska podenota γc, ki je **ne bomo** vključili v naše modeliranje. Vezava citokina omogoča aktivacijo signalnih poti JAK/STAT. Spremembe v delovanju receptorsko-signalnega sistema so povezane z motnjami razvoja in delovanja imunskega sistema.

V tej vaji modeliramo **interakcijo dveh proteinov**, IL-7 in zunajceličnega dela IL-7Rα. Posamezni strukturi sta bili pripravljeni iz eksperimentalnih PDB-struktur. Referenčna struktura njunega kompleksa je sicer znana (PDB 3DI2), vendar je ne bomo uporabili kot vhod v modeliranje.

> **O podatkih:** Prečne povezave izhajajo iz literature, a so bile rekonstruirane za uporabo v XMAS.

---

### Navodila

**1. Inštalacija XMAS**

1. V **Tools → More tools** poiščite XMAS in ga inštalirajte. Uspešna inštalacija se izpiše v log.
2. Po inštalaciji orodja XMAS bo verjetno potrebno spremeniti inštalacije pandas in numpy, ki jih uporablja ChimeraX. **Tools → General → Shell**. `devel pip install pandas==2.2.3 --no-deps` in `devel pip install pytz`.
3. Zaprite in ponovno zaženite ChimeroX.

**2. Vizualizacija prečnih povezav**

1. V ChimeraX odprite [IL7.pdb](datoteke/IL7.pdb) in [IL7R.pdb](datoteke/IL7R.pdb).
2. **Tools → Structure Analysis → XMAS**.
2. V **Evidence files → Import files** uvozite [BS3.tsv](datoteke/BS3.tsv) in [EDC.tsv](datoteke/EDC.tsv).
3. V **Molecular models** izberite oba proteina, v **Evidence files** obe tabeli in uporabite **Map crosslinks**.
4. V **Crosslink models** poiščite povezave iz obeh datotek. Pričakujemo **4 povezave BS3** in **1 povezavo EDC**. 
5. Pokažite najprej samo BS3, nato samo EDC in nazadnje vse povezave. Ali povezave nakazujejo, preko katere površine protein interagirata?

**Pomembno:** Proteina zaenkrat nimata pravilne medsebojne orientacije. Trenutna dolžina črtkane povezave v ChimeraX zato **še ne pomeni**, da je eksperimentalna povezava napačna.

**3. HADDOCK**

1. Odprite in zaženite [HADDOCK 2.4](https://wenmr.science.uu.nl/haddock2.4/).
> **Opomba:** Na strežniku je uporaba omejitev razdalj omejena za uporabnike Expert ali Guru.
2. Naložite `IL7R.pdb` in `IL7.pdb`.
3. Aminokislinske ostanke, ki so bili med proteinoma prečno povezani, označite kot **active residues**.

**3. Priprava vhodnih podatkov za DISVIS**

1. V XMAS izberite samo **BS3** povezave in odprite **Integrate → Create DisVis input**.
2. Izberite **IL-7Rα kot fixed chain** in **IL-7 kot scanning chain**. Pri vseh izvozih ohranite ta vrstni red.
3. Nastavite omejitve **5–28 Å** in shranite datoteko kot `disvis_BS3.txt`.
4. V urejevalniku preverite, da vsebuje **4 vrstice**, vsaka z osmimi polji: oznaka verige, številka ostanka, atom prvega proteina; nato isto za drugi protein; nato spodnja in zgornja meja.
5. Zaprite prejšnje okno za izvoz, izberite **samo EDC** povezavo in ponovno odprite **Integrate → Create DisVis input**.
6. Fixed in scanning chain naj sta enaka kot pri točki 2. Uporabite **5–17 Å**, izvozite kot `disvis_EDC.txt` (**1 vrstica**).
7. Izdelajte `disvis_BS3_EDC.txt` tako, da na konec štirih vrstic BS3 dodate vrstico EDC.
8. Preverite: **5 vrstic**, od tega **4 z mejama 5 in 28 Å** in **1 z mejama 0 in 17 Å**. Ne spreminjajte številčenja ostankov med datotekami.

**4. DISVIS**

1. Na [DisVis](https://wenmr.science.uu.nl/disvis/) kot **fixed chain** naložite IL-7Rα in kot **scanning chain** IL-7. Uporabite izvorna PDB-modela z **istim številčenjem, kot ga vsebuje datoteka `disvis_BS3.txt`**.
2. Za prvi izračun naložite `disvis_BS3.txt` in oddajte opravilo **BS3**.
3. Za drugi izračun uporabite enaki strukturi in enake ostale nastavitve, vendar naložite `disvis_BS3_EDC.txt`. Oddajte opravilo **BS3_EDC**.
4. Ko sta opravili končani, prenesite in razširite vsak arhiv rezultatov **v svojo mapo**.

**5. Vizualizacija DISVIS**

1. V XMAS izberite **Integrate → Analyze DisVis output**.
2. Izberite mapo z razširjenimi rezultati **BS3** in kliknite **Use folder**. Oglejte si naložena proteina, vizualizirane omejitve in volumenski zemljevid `accessible_interaction_space.mrc`.
3. Z orodjem za prikaz volumskih podatkov (**Volume Viewer**) prilagodite prikaz prostorskega območja. Zapišite, za koliko skladnih omejitev je prikazan posamezni nivo.
4. Odprite še rezultate **BS3_EDC**, najbolje v **ločeni seji ChimeraX**, da se volumni in modeli ne pomešajo.
5. Primerjajte velikost in obliko **dostopnega interakcijskega prostora**, število skladnih omejitev in morebitne kršitve. V oknu XMAS lahko pregledate tudi rezultate, povezane z **z-vrednostmi (*z-scores*)** posameznih omejitev.

**Kaj je ta volumen?** Predstavlja možne položaje težišča premičnega proteina, skladne z določenim številom razdaljnih omejitev. **Ni** elektronska gostota in **ni** ena določena atomska struktura kompleksa. DisVis vrednoti omejitve in prostor mogočih orientacij, HADDOCK pa ustvarja konkretne strukturne modele.

**5. Če je izračun HADDOCK končan**

Če so rezultati na voljo med vajami, odprite najbolje ocenjeni model oziroma predstavnika vodilnega grozda v ChimeraX. Primerjajte lego povezav, vmesno površino in skladnost modela s podatki XL-MS. Če izračun še ni končan, ta korak izpustite; ne nadomešča analize DisVis.

---

### Vprašanja

1. Kakšna je kemijska razlika med povezovalnima reagentoma BS3 in EDC? Zakaj uporabimo različno velike razdaljne omejitve?
2. Zakaj povezave, prikazane med dvema še neporavnanima proteinoma, ne moremo oceniti zgolj po trenutni dolžini v ChimeraX?
3. Zakaj je pri kombiniranju obeh tipov podatkov pomembno, da vsak *cross-link* ohrani svojo lastno razdaljno mejo?
4. Ali manjši dostopni interakcijski prostor sam po sebi dokazuje, da je napovedana orientacija pravilna?
5. Kaj pomenijo kršitve posameznih omejitev? Ali je vsaka kršitev dokaz napačne eksperimentalne identifikacije?
6. V čem se izhodna podatka programov HADDOCK in DisVis bistveno razlikujeta?
7. Kako bi lahko preverili pravilnost najboljšega modela, če bi imeli na voljo neodvisno eksperimentalno strukturo kompleksa?

