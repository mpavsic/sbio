# Modeliranje proteinskega kompleksa z uporabo XL-MS podatkov

**Prevideno trajanje:** približno 2 uri  
**Programi:** UCSF ChimeraX z dodatkom XMAS, [HADDOCK 2.4](https://wenmr.science.uu.nl/haddock2.4/), [DisVis](https://wenmr.science.uu.nl/disvis/)  
**Vhodne datoteke:** `IL7.pdb`, `IL7R.pdb`, `BS3.tsv`, `EDC.tsv`

## Namen vaje

Namen vaje je sezaniti se z uporabo kemijskih prečnih povezav (XL, angl. *cross-links*) kot prostorskih omejitev pri modeliranju medproteinskih kompleksov in sicer na primeru modeliranja kompleksa med interlevkinom-7 (IL-7) in njegovim receptorjem (IL-7Rα).

---

## Biološko ozadje

**Interlevkin 7 (IL-7)** je citokin, ki sodeluje pri razvoju, preživetju in homeostazi limfocitov, zlasti celic T. Ima značilno zgradbo citokinov s štirimi α-vijačnicami.

**Receptor IL-7Rα** je podenota receptorja, ki prepozna IL-7. Pri signalizaciji sodeluje še receptorska podenota γc, ki je **ne bomo** vključili v naše modeliranje. Vezava citokina omogoča aktivacijo signalnih poti JAK/STAT. Spremembe v delovanju receptorsko-signalnega sistema so povezane z motnjami razvoja in delovanja imunskega sistema.

V tej vaji modeliramo **interakcijo dveh proteinov**, IL-7 in zunajceličnega dela IL-7Rα. Datoteki s strukturo posameznih komponent kompleksa sta bili pripravljeni na osnovi eksperimentalno določenih struktur (zbirka PDB). Referenčna struktura njunega kompleksa je sicer znana (PDB 3DI2), vendar je ne bomo uporabili kot vhodni podatek za modeliranje, temveč le za namen preverjanja pravilnosti napovedi kompleksa.

> **O podatkih:** Prečne povezave izhajajo iz literature, a so bile rekonstruirane za uporabo v XMAS.

---

## XL-MS

### Splošno

**Kemijsko prečno povezovanje proteinov v povezavi z masno spektrometrijo (XL-MS)** omogoča odkrivanje medproteinskih interakcij v vzorcih čistih proteinov, celičnih lizatih, izoliranih organelih in tudi neposredno v celicah. Pri tej metodi s kemičnim reagentom kovalentno povežemo reaktivne skupine aminokislinskih ostankov, ki so med reakcijo dovolj blizu v prostoru. Če povezava nastane med dvema različnima proteinoma, lahko z identifikacijo povezanih peptidov ugotovimo, katera proteina sta bila v neposredni prostorski bližini. Tako lahko prepoznamo tudi šibke ali prehodne interakcije, ki se pri izolaciji proteinskih kompleksov, ki niso tako povezani, pogosto izgubijo. Pri analizi na ravni proteoma identificirane povezave združimo v mrežo proteinskih stikov ter raziskujemo organizacijo kompleksov in povezave med celičnimi procesi. Za prečno povezovanje znotraj nepoškodovanih celic moramo uporabiti reagent, ki prehaja skozi celično membrano, medtem ko te zahteve pri analizi lizatov ni. Pomembna prednost XL-MS je, da poleg identitete proteinskih partnerjev pogosto določi tudi konkretna aminokislinska ostanka, med katerima je nastala povezava. Vendar prostorska bližina sama po sebi še ne dokazuje stabilne ali funkcionalno pomembne interakcije, saj lahko zajamemo tudi kratkotrajna "srečanja" proteinov. Pri kompleksnih vzorcih je zato posebej pomembno ustrezno omejiti delež napačnih identifikacij, in sicer tako na ravni povezanih peptidov kot na ravni sklepov o proteinskih interakcijah.

Pri raziskovanju izbranega proteinskega kompleksa je glavni cilj običajno določiti medsebojno razporeditev podenot in preveriti predlagane strukturne modele. Medproteinske povezave omejujejo možne lege in orientacije podenot, povezave znotraj posameznega proteina pa dajejo informacije o njegovi konformaciji in razporeditvi domen. Če poznamo strukture posameznih komponent, lahko te podatke uporabimo za njihovo sestavljanje v model kompleksa. XL-MS je posebej uporabna pri velikih, gibljivih ali heterogenih kompleksih, pri katerih je določanje celotne strukture z eno samo metodo zahtevno. V integrativni strukturni biologiji jo zato povezujemo s krioelektronsko mikroskopijo, rentgensko kristalografijo, NMR, SAXS in računskimi napovedmi struktur. Z njo lahko preverjamo tudi napovedane vezavne površine ter razlikujemo med alternativnimi modeli kompleksa. Primerjava povezav v različnih razmerah, na primer ob prisotnosti liganda ali po mutaciji, lahko razkrije konformacijske spremembe in preurejanje podenot. Ker eksperiment zajame populacijo molekul, lahko različne povezave izvirajo iz različnih konformacij, zato ni nujno, da jih lahko pojasnimo z eno samo strukturo. XL-MS zato praviloma ne zagotovi popolne atomske strukture, temveč omejeno število prostorskih informacij, ki pomagajo pri gradnji, izbiri in vrednotenju modelov.

### Prečni povezovalci

Pri XL-MS se uporabljajo različni povezovalci, ki reagirajo z različnimi skupinami in imajo različne dolžine "ročice". Kot aminski povezovalec z daljšim mostičkom (ročico) se pogosto uporablja BS3, kot povezovalec z "ničelnim" mostičkom pa najpogosteje EDC.

![BS3 in EDC](slike/BS3-EDC.png)

**BS3 oziroma bis(sulfosukcinimidil)suberat** je vodotopen homobifunkcionalni reagent, kar pomeni, da ima na obeh koncih enaki reaktivni skupini. Njegova sulfo-NHS-estra reagirata predvsem s primarnimi aminskimi skupinami stranskih verig lizinskih ostankov in prostih N-koncev proteinov ter tvorita stabilni amidni vezi. V nastali povezavi ostane vgrajen povezovalni mostiček z dolžino približno 11,4 Å, ki določa razdaljo med povezanima aminskima skupinama, ne pa med atomoma Cα. BS3 slabo prehaja skozi celične membrane, zato je primeren predvsem za vzorce izoliranih proteinov, lizate in dostopne površine celic. **EDC oziroma 1-etil-3-(3-dimetilaminopropil)karbodiimid** deluje drugače, saj aktivira karboksilne skupine aspartatnih ali glutamatnih ostankov ali celo prostega C-konca proteina. Aktivirana karboksilna skupina lahko nato reagira s primarno aminsko skupino lizinskih ostankov ali N-konca in tvori neposredno amidno vez. EDC se ne vgradi v končni produkt, zato ga označujemo kot povezovalec z ničelno dolžino mostička, čeprav razdalja med atomoma Cα povezanih ostankov seveda ni nič. Pogosto ga uporabljamo skupaj z NHS ali sulfo-NHS, ki stabilizira aktivirani intermediat in izboljša učinkovitost povezovanja. BS3 tako praviloma povezuje dve aminski skupini, EDC pa karboksilno in aminsko skupino, zato reagenta dajeta komplementarne informacije o proteinskih stikih.

![mehanizem EDC](slike/EDC-mehanizem.png)

### Splošni potek eksperimenta

1. Pripravo vzorca v pogojih, ki čim bolje ohranjajo relevantno strukturo in interakcije proteinov ter omogočajo izbrano kemijsko reakcijo.
2. Po dodatku povezovalca reakcijo časovno omejimo in ustavimo (npr. pri BS3 pogosto z dodatkom spojine s primarno amino skilino, npr. Tris), saj lahko pretirano povezovanje povzroči nastanek neželenih produktov oz. nespecifične povezave.
3. Proteine nato običajno denaturiramo, reduciramo in alkiliramo cisteinske ostanke ter jih s proteazami, najpogosteje s tripsinom (cepi za lizinskimi in argininskimi ostanki), razgradimo v peptide.
4. Ker so prečno povezani peptidi navadno maloštevilni v primerjavi z nepovezanimi, jih lahko pred analizo obogatimo oziroma vzorec frakcioniramo. Ta korak je možen pri uporabi posebnih povezovalcev, ki imajo ustrezno "oznako", npr. pri fosforilni skupini povezovalca PhoX lahko uporabimo IMAC z Fe<sup>3+</sup> ioni.
5. Sledi ločevanje s tekočinsko kromatografijo in tandemska masna spektrometrija, pri kateri iz mas prekurzorskih ionov in njihovih fragmentov določimo zaporedji obeh peptidov ter mesti povezave.
6. Specializirana programska oprema pri iskanju upošteva zaporedja proteinov (+ izrbane modifikacije), reaktivnost in masni prispevek povezovalca, rezultate pa filtriramo glede na zanesljivost identifikacije.
7. Dobljene aminokislinske pare preslikamo na strukture ali modele in jih pretvorimo v prostorske omejitve, običajno zgornje meje dovoljenih razdalj. Pri določanju teh meja upoštevamo dolžino povezovalca, dolžino in gibljivost stranskih verig, konformacijsko gibljivost proteina ter izbiro merjenih atomov, zato se za BS3 pogosto uporabljajo meje okoli 25–30 Å med atomoma Cα, odvisno od modelirnega pristopa. Upoštevamo lahko tudi pot povezovalca po površini, saj kratka ravna razdalja skozi notranjost proteina še ne pomeni, da je povezava fizično izvedljiva.
8. Omejitve nato uporabimo pri računalniškem umeščanju in vrednotenju podenot, pri čemer odsotnost določene povezave ne dokazuje velike razdalje, njena kršitev v modelu pa lahko kaže na napačen model, alternativno konformacijo ali napačno identifikacijo.

---

## Navodila

Prečne povezave bomo najprej vizualizirali na strukturi z orodjem XMAS. Model kompleksa bomo pripravili z makromolekularnim umeščanjem na strežniku HADDOCK. V vmesnem času bomo z orodjem DisVis vizualizirali interakcijski prostor, ki je dostopen omejitvam razdalj. Primerjali bomo prostor, ki ga omejujejo prečne povezave z BS3 in prostor, ki ga omejujejo prečne povezave z BS3 in EDC.

### 1. Namestitev XMAS

1. V **Tools → More tools** poiščite XMAS in ga inštalirajte. Uspešna inštalacija se izpiše v log.
2. Po inštalaciji orodja XMAS bo verjetno potrebno spremeniti inštalacije pandas in numpy, ki jih uporablja ChimeraX. **Tools → General → Shell**: `devel pip install pandas==2.2.3 --no-deps` in `devel pip install pytz`.
3. Zaprite in ponovno zaženite ChimeroX.

### 2. Vizualizacija prečnih povezav

1. V ChimeraX odprite [IL7.pdb](datoteke/IL7.pdb) in [IL7R.pdb](datoteke/IL7R.pdb).
2. **Tools → Structure Analysis → XMAS**.
2. V **Evidence files → Import files** uvozite [BS3.tsv](datoteke/BS3.tsv) in [EDC.tsv](datoteke/EDC.tsv).
3. V **Molecular models** izberite oba proteina, v **Evidence files** obe tabeli in uporabite **Map crosslinks**.
4. V **Crosslink models** poiščite povezave iz obeh datotek. Pričakujemo **4 povezave BS3** in **1 povezavo EDC**. 
5. Pokažite najprej samo BS3, nato samo EDC in nazadnje vse povezave. Ali povezave nakazujejo, preko katere površine protein interagirata?

**Pomembno:** Proteina zaenkrat nimata pravilne medsebojne orientacije. Trenutna dolžina črtkane povezave v ChimeraX zato **še ne pomeni**, da je eksperimentalna povezava napačna.

### 3. HADDOCK

1. Odprite in zaženite [HADDOCK 2.4](https://wenmr.science.uu.nl/haddock2.4/).
> **Opomba:** Na strežniku je uporaba omejitev razdalj omejena za uporabnike Expert ali Guru.
2. Naložite `IL7R.pdb` in `IL7.pdb`.
3. Aminokislinske ostanke, ki so bili med proteinoma prečno povezani, označite kot **active residues**.

### 4. Priprava vhodnih podatkov za DISVIS

1. V XMAS izberite samo **BS3** povezave in odprite **Integrate → Create DisVis input**.
2. Izberite **IL-7Rα kot fixed chain** in **IL-7 kot scanning chain**. Pri vseh izvozih ohranite ta vrstni red.
3. Nastavite omejitve **5–28 Å** in shranite datoteko kot `disvis_BS3.txt`.
4. V urejevalniku preverite, da vsebuje **4 vrstice**, vsaka z osmimi polji: oznaka verige, številka ostanka, atom prvega proteina; nato isto za drugi protein; nato spodnja in zgornja meja.
5. Zaprite prejšnje okno za izvoz, izberite **samo EDC** povezavo in ponovno odprite **Integrate → Create DisVis input**.
6. Fixed in scanning chain naj sta enaka kot pri točki 2. Uporabite **5–17 Å**, izvozite kot `disvis_EDC.txt` (**1 vrstica**).
7. Izdelajte `disvis_BS3_EDC.txt` tako, da na konec štirih vrstic BS3 dodate vrstico EDC.
8. Preverite: **5 vrstic**, od tega **4 z mejama 5 in 28 Å** in **1 z mejama 0 in 17 Å**. Ne spreminjajte številčenja ostankov med datotekami.

### 5. DISVIS

1. Na [DisVis](https://wenmr.science.uu.nl/disvis/) kot **fixed chain** naložite IL-7Rα in kot **scanning chain** IL-7. Uporabite izvorna PDB-modela z **istim številčenjem, kot ga vsebuje datoteka `disvis_BS3.txt`**.
2. Za prvi izračun naložite `disvis_BS3.txt` in oddajte opravilo **BS3**.
3. Za drugi izračun uporabite enaki strukturi in enake ostale nastavitve, vendar naložite `disvis_BS3_EDC.txt`. Oddajte opravilo **BS3_EDC**.
4. Ko sta opravili končani, prenesite in razširite vsak arhiv rezultatov **v svojo mapo**.

### 6. Vizualizacija DISVIS

1. V XMAS izberite **Integrate → Analyze DisVis output**.
2. Izberite mapo z razširjenimi rezultati **BS3** in kliknite **Use folder**. Oglejte si naložena proteina, vizualizirane omejitve in volumenski zemljevid `accessible_interaction_space.mrc`.
3. Z orodjem za prikaz volumskih podatkov (**Volume Viewer**) prilagodite prikaz prostorskega območja. Zapišite, za koliko skladnih omejitev je prikazan posamezni nivo.
4. Odprite še rezultate **BS3_EDC**, najbolje v **ločeni seji ChimeraX**, da se volumni in modeli ne pomešajo.
5. Primerjajte velikost in obliko **dostopnega interakcijskega prostora**, število skladnih omejitev in morebitne kršitve. V oknu XMAS lahko pregledate tudi rezultate, povezane z **z-vrednostmi (*z-scores*)** posameznih omejitev.

**Kaj je ta volumen?** Predstavlja možne položaje težišča premičnega proteina, skladne z določenim številom razdaljnih omejitev. **Ni** elektronska gostota in **ni** ena določena atomska struktura kompleksa. DisVis vrednoti omejitve in prostor mogočih orientacij, HADDOCK pa ustvarja konkretne strukturne modele.

### 7. Če je izračun HADDOCK končan...

Če so rezultati na voljo med vajami, odprite najbolje ocenjeni model oziroma predstavnika vodilnega grozda v ChimeraX. Primerjajte lego povezav, vmesno površino in skladnost modela s podatki XL-MS. Če izračun še ni končan, ta korak izpustite; ne nadomešča analize DisVis.

---

## Vprašanja

1. Kakšna je kemijska razlika med povezovalnima reagentoma BS3 in EDC? Zakaj uporabimo različno velike razdaljne omejitve?
2. Zakaj povezave, prikazane med dvema še neporavnanima proteinoma, ne moremo oceniti zgolj po trenutni dolžini v ChimeraX?
3. Zakaj je pri kombiniranju obeh tipov podatkov pomembno, da vsak *cross-link* ohrani svojo lastno razdaljno mejo?
4. Ali manjši dostopni interakcijski prostor sam po sebi dokazuje, da je napovedana orientacija pravilna?
5. Kaj pomenijo kršitve posameznih omejitev? Ali je vsaka kršitev dokaz napačne eksperimentalne identifikacije?
6. V čem se izhodna podatka programov HADDOCK in DisVis bistveno razlikujeta?
7. Kako bi lahko preverili pravilnost najboljšega modela, če bi imeli na voljo neodvisno eksperimentalno strukturo kompleksa?


---

*Vajo sta pripravila Jošt Hočevar in Miha Pavšič*.