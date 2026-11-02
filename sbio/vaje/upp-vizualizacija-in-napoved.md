# Vaje pri predmetu Uporaba proteomskih podatkov
## Vizualizacija in analiza proteinskih struktur s programom UCSF ChimeraX

**Predvideno trajanje:** približno 3 ure  
**Program:** UCSF ChimeraX  
**Podatkovna zbirka:** [Protein Data Bank (RCSB PDB)](https://www.rcsb.org/)

### Namen vaje

Namen vaje je spoznati osnovna orodja za pregledovanje in analizo tridimenzionalnih struktur proteinov ter povezati opažene strukturne značilnosti z biološko funkcijo proteinov. Študenti se bodo naučili poiskati in naložiti eksperimentalno določene strukture iz zbirke PDB, spreminjati njihove prikaze, izbirati posamezne verige, aminokislinske ostanke in atome ter preučevati molekularne površine in interakcije. Primerjali bodo različni konformaciji istega proteina in na dveh primerih bolezenskih mutacij pojasnili njune strukturne posledice.

**Po koncu vaj boste znali:**
- poiskati strukturo v zbirki PDB in razbrati njene osnovne podatke;
- razlikovati med asimetrično enoto, kristalografsko osnovno celico in biološko sestavo proteina;
- prikazati sekundarno strukturo, posamezne atome, ligande, površino in interakcije;
- uporabiti sekvenčni pregledovalnik in povezavo na anotacije UniProt;
- poravnati dve strukturi in izdelati animiran prehod (*morph*) med konformacijama;
- razložiti strukturni učinek izbranih bolezenskih mutacij.

> **Opomba:** Ukazi predpostavljajo, da na začetku vsakega sklopa zaprete prejšnje modele. Številke modelov (`#1`, `#2` itd.) vedno preverite v oknu **Models**, saj se lahko razlikujejo.

---

## 1. Osnove ChimeraX: zunajcelični del proteina EpCAM (PDB: 4MZV)

**Struktura:** [4MZV – zunajcelični del človeškega EpCAM](https://www.rcsb.org/structure/4MZV)

### Namen

Spoznati uporabniški vmesnik, načine izbire in prikaza posameznih delov strukture ter osnovne metode analize proteinskih površin in medatomskih interakcij. Na primeru EpCAM spoznati razliko med kristalografsko asimetrično enoto, osnovno celico kristala in biološkim dimerom ter uporabo sekvenčnih anotacij.

### Navodila

**1. Nalaganje in orientacija v programu**

1. Odprite program ChimeraX in naložite strukturo:
   ```chimerax
   open 4mzv
   ```
2. Z miško preizkusite rotacijo, premikanje in povečavo modela. Poiščite menije **File**, **Select**, **Actions** in **Tools** ter zavihke **Home**, **Molecule Display**, **Graphics** in **Right Mouse**.
3. V oknu **Models** preverite številko modela in njegovo vsebino. Oglejte si tudi stran 4MZV v zbirki PDB: metodo določitve strukture, ločljivost, verige in prisotne majhne molekule.

**2. Načini prikaza in izbira atomov**

4. Preizkusite skrivanje in prikaz atomov ter prikaz proteina kot traku (*cartoon*). Primeri ukazov:
   ```chimerax
   hide atoms
   show ligand
   hide :HOH
   ```
5. Vključite oziroma izključite prikaz posameznih aminokislinskih ostankov. Preizkusite izbiro verige ali ostanka s klikom v strukturi in z ukazom, npr.:
   ```chimerax
   select #1/A:50
   show sel atoms
   label sel residues
   select clear
   ```
6. Preizkusite barvanje celotnega proteina, posameznih verig in atomov glede na kemijski element. Uporabite **Actions → Color** ali zavihke na orodni vrstici.
7. Prikažite cisteinske ostanke in poiščite disulfidne vezi. Po potrebi skrijte preostale atome, da bo preglednejše.

**3. Ligand, površine in medatomske razdalje**

8. Poiščite prisotno majhno molekulo **DMU** (decyl-β-D-maltopyranoside). Gre za detergent in **ne za fiziološki ligand EpCAM**.
9. Označite DMU in poiščite bližnje aminokislinske ostanke z izbiro območja okoli liganda (*zone*) oziroma z orodjem **Contacts**.
10. Prikažite molekularno površino in nastavite prosojnost:
    ```chimerax
    surface
    transparency 60 target s
    ```
11. Z orodjem **Side View** preizkusite rezanje pogleda (*clipping*). Oglejte si še nastavitev globinskega učinka (*depth cue*).
12. Izberite dva atoma in izmerite njuno razdaljo z načinom **Right Mouse → Distance** ali ukazom `distance sel` (če sta izbrana natanko dva atoma).
13. Z orodjem **Tools → Structure Analysis → H-Bonds** poiščite vodikove vezi, na primer znotraj α-vijačnice. Oglejte si, kateri atomi sodelujejo pri teh vezeh.

**4. Kristalografska osnovna celica, biološki dimer in interakcije med podenotami**

14. V zbirki PDB preverite, koliko proteinskih verig vsebuje **asimetrična enota** in koliko jih vsebuje **biološka sestava** EpCAM. Poiščite tudi podatke o kristalografski prostorski skupini.
15. Iz izhodiščne asimetrične enote (`#1`) ustvarite vse simetrijsko povezane kopije, ki sestavljajo eno kristalografsko **osnovno celico**, in prikažite njen obris:
    ```chimerax
    unitcell #1
    unitcell outline #1
    ```
16. Oglejte si **štiri asimetrične enote** znotraj prikazane osnovne celice. Preverite, kako so razporejene in ali kateri dve sestavljata biološki dimer. Razmislite, ali mora biološka sestava nujno ležati v mejah ene osnovne celice.
17. Iz izhodiščne asimetrične enote nato ustvarite **biološki dimer**:
    ```chimerax
    sym #1 assembly 1
    ```
    Po potrebi v oknu **Models** začasno skrijte model osnovne celice in njen obris, da boste dimer bolje videli. Pri strukturi 4MZV dimer poveže izhodiščno podenoto s simetrijsko povezano podenoto, ki v prikazani postavitvi osnovne celice leži v **sosednji celici**.
18. V oknu **Models** preverite številko nastalega modela in njegovih podenot ter obe podenoti pobarvajte različno. Številka modela se po ukazih `unitcell` lahko razlikuje od prejšnjih primerov.
19. Poiščite stično površino med podenotama dimera. Uporabite **Contacts** in/ali **H-Bonds**. Če sta podenoti v ločenih podmodelih (npr. `#4.1` in `#4.2`), pri iskanju vodikovih vezi omogočite tudi **intermodel** interakcije; po potrebi omejite iskanje na izbrani podenoti.

**5. Zaporedje in anotacije**

20. Odprite **Sequence Viewer**, poiščite ostanek, ki ste ga predhodno izbrali v tridimenzionalnem prikazu, in preverite, kako se izbira odraža v zaporedju.
21. Poiščite povezavo na **UniProt (P16422)** in preglejte razpoložljive anotacije proteina EpCAM.

**Dodatno, če ostane čas:** preizkusite barvanje površine po hidrofobnosti (`mlp`) in približnem elektrostatskem potencialu (`coulombic`); z orodjem **Find Cavities** poiščite vdolbine v molekularni površini.

### Vprašanja

1. Katere osnovne informacije o strukturi dobimo v zbirki PDB in kaj pomeni njena ločljivost?
2. Kakšna je razlika med **asimetrično enoto**, **osnovno celico kristala** in **biološko sestavo** proteina EpCAM?
3. Koliko asimetričnih enot je v prikazani osnovni celici? Ali kateri dve tvorita biološki dimer? Kako pojasnite, da lahko podenoti biološkega dimera ležita v dveh sosednjih osnovnih celicah?
4. Kaj ugotovite o prostorski razporeditvi cisteinskih ostankov in disulfidnih vezi? Zakaj so te vezi pomembne za zunajcelične proteine?
5. Kateri ostanki ležijo v bližini molekule DMU? Ali lahko zgolj na podlagi njene prisotnosti v kristalni strukturi sklepamo, da gre za fiziološki ligand?
6. Katere vrste interakcij opazite na stiku med podenotama dimera? Ali je vsaka medatomska bližina tudi vodikova vez?
7. Katere informacije o proteinu pridobimo s povezavo med tridimenzionalno strukturo, zaporedjem in zbirko UniProt?

---

## 2. Konformacijske spremembe: adenilat kinaza (PDB: 4AKE in 1AKE)

**Strukturi:** [4AKE – odprta konformacija](https://www.rcsb.org/structure/4AKE); [1AKE – zaprta, z inhibitorjem Ap5A stabilizirana konformacija](https://www.rcsb.org/structure/1AKE)

### Namen

Spoznati poravnavo proteinskih struktur (*superposition*) in izdelavo interpolacije med dvema konformacijama istega proteina (*morph*). Povezati premike proteinskih domen z vezavo substratov oziroma inhibitorja in encimsko funkcijo.

Adenilat kinaza katalizira reakcijo **ATP + AMP ⇌ 2 ADP**.

### Navodila

1. Zaprite predhodne modele in naložite obe strukturi:
   ```chimerax
   close
   open 4ake
   open 1ake
   ```
2. Preverite vsebino obeh struktur. Kaj je prisotno v 1AKE, česar ni v 4AKE?
3. Za preprostejšo primerjavo odstranite verigo B iz vsake strukture, tako da ostane po ena proteinska veriga:
   ```chimerax
   delete #1/B
   delete #2/B
   ```
4. Strukturi različno pobarvajte in poravnajte verigi A:
   ```chimerax
   matchmaker #2/A to #1/A
   ```
   Enako nalogo poskusite najti z orodjem **Matchmaker** v grafičnem vmesniku.
5. Opazujte, katere regije se najbolje prekrivajo in katere se razlikujejo. V oknu **Log** poiščite podatek o RMSD, če je izpisan.
6. Izdelajte animirani prehod med konformacijama:
   ```chimerax
   morph #1,2 frames 120 wrap true
   ```
7. S časovnim drsnikom predvajajte prehod in spremljajte premikanje domen. Po potrebi poskusite spremeniti število sličic.

### Vprašanja

1. Katera struktura predstavlja bolj odprto in katera bolj zaprto konformacijo adenilat kinaze?
2. Katere regije proteina se pri prehodu med konformacijama najbolj premaknejo? Ali je celoten protein enako gibljiv?
3. Kako bi lahko zapiranje domen pripomoglo k vezavi substratov in katalizi?
4. Kaj pove RMSD in zakaj je pri primerjavi dveh konformacij pomembno, katere atome vključimo v poravnavo?
5. Ali *morph* prikazuje dejansko eksperimentalno izmerjeno pot gibanja proteina ali matematično interpolacijo med dvema določenima strukturama?

---

## 3. Bolezenska mutacija, ki spremeni medmolekulske interakcije: hemoglobin (PDB: 2HHB in 2HBS)

**Strukturi:** [2HHB – običajni deoksihemoglobin](https://www.rcsb.org/structure/2HHB); [2HBS – deoksihemoglobin S](https://www.rcsb.org/structure/2HBS)

### Namen

Na primeru anemije srpastih celic razumeti, kako lahko sprememba ene aminokisline spremeni kemijske lastnosti površine proteina in povzroči patološko povezovanje proteinskih kompleksov, tudi če se celotna struktura posameznega tetramera bistveno ne spremeni.

### Navodila

1. Zaprite prejšnje modele in naložite strukturo običajnega deoksihemoglobina:
   ```chimerax
   close
   open 2hhb
   ```
2. Pobarvajte verige različno in določite, koliko α- in β-verig vsebuje tetramer. Oglejte si hemske skupine.
3. V β-verigi B poiščite aminokislinski ostanek **Glu6 (E6)**:
   ```chimerax
   select #1/B:6
   show sel atoms
   label sel residues
   ```
4. Premislite, kakšne lastnosti ima glutamat: kakšen je njegov naboj in ali je hidrofilen oziroma hidrofoben?
5. Naložite strukturo hemoglobina S:
   ```chimerax
   open 2hbs
   ```
6. V β-verigi B poiščite **Val6 (V6)**:
   ```chimerax
   select #2/B:6
   show sel atoms
   label sel residues
   ```
7. Primerjajte položaj in kemijske lastnosti obeh stranskih verig. Po potrebi poravnajte ustrezni β-verigi:
   ```chimerax
   matchmaker #2/B to #1/B
   ```
8. Oglejte si še druge verige v 2HBS. Kristalna struktura vsebuje več hemoglobinskih tetramerov in omogoča raziskovanje stikov, povezanih s polimerizacijo HbS. Poiščite hidrofobni žep na sosednjem tetrameru, s katerim lahko interagira Val6.

### Vprašanja

1. Koliko α- in β-verig sestavlja en hemoglobinski tetramer? Kakšno vlogo ima hem?
2. Katere kemijske lastnosti se spremenijo pri substituciji **E6V**?
3. Zakaj lahko zamenjava hidrofilne, negativno nabite aminokisline s hidrofobno aminokislino povzroči nove interakcije med proteini?
4. Ali mora mutacija povzročiti veliko spremembo terciarne strukture, da ima resne fiziološke posledice?
5. Zakaj hemoglobin S pri deoksigenaciji tvori vlakna in kako to vpliva na obliko eritrocitov?

---

## 4. Bolezenska mutacija, ki vpliva na koordinacijo kovine: SOD1 (PDB: 2C9V in 1OEZ)

**Strukturi:** [2C9V – človeška Cu/Zn superoksid dismutaza (nemutirana)](https://www.rcsb.org/structure/2C9V); [1OEZ – mutant SOD1 H46R](https://www.rcsb.org/structure/1OEZ)

### Namen

Spoznati vlogo kovinskih ionov v zgradbi in funkciji encimov ter na primeru bolezenske mutacije SOD1 H46R raziskati, kako zamenjava aminokislinskega ostanka vpliva na koordinacijsko okolje bakra. Primer povezati z družinsko obliko amiotrofične lateralne skleroze (ALS).

### Navodila

1. Zaprite predhodne modele in naložite nemutirano strukturo SOD1:
   ```chimerax
   close
   open 2c9v
   ```
2. Poiščite **Cu** in **Zn** ter si oglejte aminokislinske ostanke v njuni okolici. Kovinske ione in koordinirajoče stranske verige prikažite kot atome oziroma paličice.
3. Poiščite **His46 (H46)** in določite, kateri njegov atom je usmerjen proti bakrovemu ionu. Izmerite razdaljo med ustreznim atomom histidina in bakrom.
4. Naložite mutirano strukturo:
   ```chimerax
   open 1oez
   ```
5. Za primerjavo poravnajte ustrezni proteinski verigi (po potrebi izberite po eno verigo iz vsakega modela):
   ```chimerax
   matchmaker #2/A to #1/A
   ```
6. V mutirani strukturi poiščite **Arg46 (R46)**. Primerjajte stranski verigi histidina in arginina ter okolico kovinskega vezavnega mesta.
7. Ugotovite, kateri kovinski ion je prisoten v mutirani strukturi in kateri manjka. Upoštevajte, da na prisotnost ionov v eksperimentalni strukturi vplivajo tudi pogoji priprave vzorca.

### Vprašanja

1. Kakšna je biološka funkcija encima SOD1 in zakaj sta zanj pomembna kovinska iona?
2. Kako histidin sodeluje pri koordinaciji bakra? Kateri atomi njegovih stranskih verig omogočajo takšno interakcijo?
3. Kako se histidin in arginin razlikujeta po zgradbi in kemijskih lastnostih?
4. Kakšna je razlika med kovinsko koordinacijsko vezjo in običajno vodikovo vezjo?
5. Kaj opazite pri primerjavi kovinskih mest v strukturah 2C9V in 1OEZ? Ali iz same strukture lahko povsem razložimo mehanizem nastanka ALS?

---

# Drugi sklop vaj (2 uri)

## Napovedovanje proteinskih struktur in kompleksov: AlphaFold Server in SWISS-MODEL

**Predvideno trajanje:** približno 2 uri  
**Orodja:** [UniProt](https://www.uniprot.org/), [AlphaFold Server](https://alphafoldserver.com/), [AlphaFold Protein Structure Database](https://alphafold.ebi.ac.uk/), [SWISS-MODEL](https://swissmodel.expasy.org/interactive), UCSF ChimeraX, [RCSB PDB](https://www.rcsb.org/).

**Glavni protein:** človeški **endophilin-B2 (SH3GLB2)**, UniProt **[Q9NR46](https://www.uniprot.org/uniprotkb/Q9NR46/entry)**, 395 aminokislin. Gre za naravni večdomenski protein, za katerega pri pregledu UniProt/PDB nismo našli eksperimentalne strukture. Zanj pa obstaja že računska napoved v [AlphaFold DB](https://alphafold.ebi.ac.uk/entry/Q9NR46). To **ni** eksperimentalna struktura.

**Zgradba:** domena **BAR (24–287)**, povezovalna regija približno **288–334**, domena **SH3 (335–395)**. Meje so po anotacijah UniProt, ne po neposredni analizi nove napovedi.

> **Opomba za izvedbo:** Ta protein je strukturno *obetaven* primer za razlikovanje med pLDDT in PAE, vendar **močna meddomenska negotovost v rezultatu AlphaFold Server ni vnaprej zagotovljena**. Pred vajami preverite dejanski PAE in shranite ustrezno napoved. Zanesljiv rezervni prikaz koncepta je primer **RAD23A (UniProt P54725)** iz uradne predstavitve AlphaFold: posamezne regije so napovedane z visoko lokalno zanesljivostjo, medsebojna lega pa je manj zanesljiva. Ta rezervni primer ni nadomestilo za osrednjo praktično nalogo.

### Namen

Spoznati postopek pridobivanja aminokislinskega zaporedja in napovedovanja strukture proteina, ki **nima znane eksperimentalne strukture celotne molekule**. Na večdomenskem proteinu razlikovati med **lokalno zanesljivostjo** napovedanih domen (pLDDT) in **zanesljivostjo njihove medsebojne lege** (PAE). Nato spoznati modeliranje na podlagi homolognih strukturnih predlog (SWISS-MODEL), modeliranje homooligomerov in primerjavo modelov s strukturno superpozicijo v ChimeraX.

**Po koncu vaj boste znali:**

- v UniProt poiskati in prenesti kanonično aminokislinsko zaporedje ter identificirati domene;
- pripraviti napoved monomera in homodimera v AlphaFold Server;
- interpretirati pLDDT, PAE, pTM in ipTM ter ločiti zanesljivost posamezne domene od zanesljivosti njene lege glede na druge domene/verige;
- poiskati eksperimentalno določene homologe in izbrati predloge v SWISS-MODEL;
- primerjati modelske domene z orodjem Matchmaker v ChimeraX, ne da bi superpoziciji pripisali več, kot je mogoče sklepati.

---

## 1. UniProt: zaporedje in domene proteina SH3GLB2

### Namen

Spoznati UniProt kot vir zaporedja in funkcionalnih anotacij ter razumeti, zakaj je poznavanje organizacije domen pomembno pri napovedovanju proteinov.

### Navodila

1. V UniProt poiščite **Q9NR46**. Zabeležite ime proteina, organizem, dolžino in osnovno funkcijo.
2. Prenesite **kanonično zaporedje** v obliki FASTA in ga shranite kot `SH3GLB2.fasta`.
3. V razdelku **Family & Domains** poiščite domeni **BAR** in **SH3** ter njune meje.
4. Oglejte si tudi področje med domenama in preverite morebitne anotacije, povezane s sekundarno strukturo, urejenostjo in oligomerizacijo.
5. Preverite povezave s PDB in AlphaFold DB. **Ločite eksperimentalne strukture od računsko napovedanih.**

### Vprašanja

1. Kako sta funkciji BAR in SH3 domene različni?
2. Ali lahko iz zaporedja in domenske organizacije vnaprej zagotovo določimo njuno medsebojno orientacijo?
3. Zakaj obstoj napovedi v AlphaFold DB **ne pomeni**, da je eksperimentalna struktura proteina že znana?

---

## 2. AlphaFold Server: napoved monomera

### Namen

Spoznati vhodne podatke za AlphaFold 3 in pripraviti novo napoved celotnega večdomenskega proteina.

### Navodila

1. Odprite [AlphaFold Server](https://alphafoldserver.com/) in ustvarite novo napoved z imenom `SH3GLB2_monomer`.
2. Vnesite celotno kanonično zaporedje Q9NR46 in nastavite **eno kopijo** proteinske verige.
3. Oddajte nalogo. Med izračunom nadaljujte z nalogo SWISS-MODEL.
4. Ko je napoved na voljo, preglejte **vseh pet modelov**, ne samo najvišje uvrščenega, in prenesite rezultate (mmCIF in spremljajoči JSON z ocenami zanesljivosti).

### Vprašanja

1. Kaj je izhod napovedi poleg atomskih koordinat?
2. Zakaj lahko različne napovedi istega zaporedja kažejo različne medsebojne lege domen?

---

## 3. SWISS-MODEL: modeliranje na podlagi homolognih struktur

### Namen

Spoznati modeliranje na podlagi predloge in razliko med **zanesljivostjo zvitja posamezne domene** ter neznano **razporeditvijo celotnega večdomenskega proteina**.

### Navodila

1. Odprite [SWISS-MODEL](https://swissmodel.expasy.org/interactive) in vnesite celotno zaporedje Q9NR46.
2. Zaženite **Search for Templates**. Poiščite predloge, določene **eksperimentalno**, ter zabeležite PDB-identifikator, identiteto zaporedja in pokritost.
3. Posebej preverite, ali najdene predloge pokrivajo predvsem **BAR** ali **SH3** domeno. Ne predpostavljajte, da ena predloga določa pravilno lego obeh domen.
4. Izberite primerno eksperimentalno predlogo za vsaj eno domeno in izdelajte model. Če samodejno modeliranje izdela samo del proteina, to **ni napaka naloge** — zabeležite, kateri ostanki so modelirani.
5. Če je smiselno, ponovite modeliranje za **izolirani segment SH3 (ostanki 335–395)**; pri primerjavi upoštevajte, da ima izrezano zaporedje drugačno oštevilčenje kot celoten protein.
6. Prenesite pripravljene modele in zabeležite oceno kakovosti (npr. QMEANDisCo, kjer je na voljo).

> **Pozor:** SWISS-MODEL lahko kot predlogo predlaga tudi računski model iz **AlphaFold DB**. Za poučno primerjavo dveh različnih pristopov izberite predlogo, določeno **z eksperimentalno metodo**, kadar je to mogoče. Model iz homologije je še vedno računska napoved, ne eksperimentalni rezultat.

### Vprašanja

1. Zakaj je v večdomenskem proteinu lahko napoved ene domene dobra, čeprav celoten model ni zanesljiv?
2. Kakšna je razlika med pokritostjo zaporedja (*coverage*) in identiteto zaporedja (*sequence identity*)?
3. Kako bi ovrednotili primerjavo, če SWISS-MODEL pokriva samo eno domeno, AlphaFold pa celoten protein?

---

## 4. Lokalna in globalna zanesljivost: pLDDT in PAE

### Namen

Pojasniti, zakaj **visok pLDDT obeh domen ne zagotavlja pravilne medsebojne orientacije**.

### Navodila

1. Odprite rezultat napovedi monomera `SH3GLB2_monomer` in strukturo obarvajte po **pLDDT**.
2. Poiščite regije BAR, SH3 in povezovalno regijo. Zabeležite, ali so strukturirane domene napovedane z višjim pLDDT kot povezovalna regija.
3. Odprite **PAE (Predicted Aligned Error)** in po zaporednih položajih poiščite območja, ki približno ustrezajo obema domenama.
4. Primerjajte **diagonalna bloka** (pari ostankov znotraj iste domene) in **zunajdiagonalna bloka** (pari ostankov iz različnih domen). Nižji PAE pomeni zanesljivejšo napoved medsebojne lege, višji pa večjo negotovost.
5. Primerjajte več napovedanih modelov. Ali sta domeni podobno zviti, vendar drugače medsebojno orientirani?
6. Preverite skupno oceno **pTM** in premislite, zakaj ta ne nadomesti pregleda matrike PAE.

### Vprašanja

1. Kaj pomeni **pLDDT > 90** za strukturo posamezne regije? Česa nam ne pove?
2. Kaj pomeni visok **PAE med dvema domenama**, če ima vsaka domena zase visok pLDDT?
3. Ali visok meddomenski PAE **dokazuje**, da sta domeni v celici gibljivi, ali kaže predvsem na **negotovost napovedi**?
4. Kako bi preverili, ali je povezovalna regija res intrinzično neurejena?

---

## 5. AlphaFold Server: napoved homodimera

### Namen

Razlikovati med vprašanjem, kako sta domeni razporejeni **znotraj ene verige**, in vprašanjem, kako sta postavljeni **dve proteinski podenoti v kompleksu**.

### Navodila

1. V AlphaFold Server ustvarite novo nalogo `SH3GLB2_dimer` z **dvema kopijama** istega zaporedja Q9NR46.
2. Ko je rezultat na voljo, primerjajte strukturi obeh verig in ocenite, kateri del proteina tvori stik med podenotama.
3. Oglejte si **medverižni PAE**, **ipTM** in morebitne razlike med petimi napovedmi.
4. Razlikujte med **znotrajverižnim meddomenskim PAE** in **medverižnim PAE**. Oba se nanašata na relativno razporeditev, vendar na različni strukturni vprašanji.
5. Ne sklepajte, da je vsak napovedan stik dokaz fiziološke oligomerizacije; v pomoč naj bodo tudi podatki o proteinu in znane interakcije.

### Vprašanja

1. Ali visok pLDDT obeh verig dokazuje, da je model dimera pravilen?
2. Kakšno dodatno informacijo pri kompleksu prispeva **ipTM**?
3. Ali bi lahko isti protein tvoril drugačen dimer ali interagiral z drugo proteinsko verigo?

---

## 6. ChimeraX: superpozicija AlphaFold in SWISS-MODEL

### Namen

Primerjati modela **ustrezajočih domen** in razumeti omejitve interpretacije RMSD pri delno modeliranih večdomenskih proteinih.

### Navodila

1. V ChimeraX naložite napoved AlphaFold 3 in izdelani model SWISS-MODEL. Zabeležite njuni številki v **Models**.
2. S programom **Matchmaker** poravnajte model SWISS-MODEL z ustrezno regijo napovedi AlphaFold. Pred primerjavo preverite, ali obe strukturi predstavljata **isto zaporedno območje**.
3. Oglejte si lokalne razlike v sekundarni strukturi, zankah in RMSD. Zabeležite **število primerjanih aminokislinskih ostankov**.
4. Če imate ločen model SH3 domene, primerjajte tudi tega, vendar ne poskušajte iz dveh ločenih domenskih superpozicij neposredno rekonstruirati zanesljive orientacije celotnega proteina.
5. Primerjajte **napovedi različnih metod**, vendar upoštevajte, da podoben zvitek domene ne potrjuje pravilne prostorske razporeditve domen.

### Vprašanja

1. Ali sta AlphaFold in SWISS-MODEL napovedala podoben zvitek izbrane domene?
2. Zakaj nizek RMSD poravnanih domen še ne potrjuje celotne strukture večdomenskega proteina?
3. Kaj nam več pove o medsebojnem položaju domen: dobra lokalna superpozicija ali interdomenski PAE?
4. Kje je vsaka od obeh metod najmočnejša in kakšne omejitve ima uporabljeni strukturni dokaz?

---

## Zaključna naloga

V največ treh stavkih pojasnite, zakaj lahko za isti proteinski model velja: **»Obe domeni sta zelo zanesljivo napovedani, celotna struktura pa ni.«** V odgovoru uporabite izraza **pLDDT** in **PAE**.

---

### Viri

- [UniProt: SH3GLB2, Q9NR46](https://www.uniprot.org/uniprotkb/Q9NR46/entry)
- [AlphaFold Database: Q9NR46](https://alphafold.ebi.ac.uk/entry/Q9NR46)
- [EMBL-EBI: Interpretacija rezultatov AlphaFold Server](https://www.ebi.ac.uk/training/online/courses/alphafold/alphafold-3-and-alphafold-server/alphafold-server-your-gateway-to-alphafold-3/interpreting-results-from-alphafold-server/)
- [SWISS-MODEL dokumentacija](https://swissmodel.expasy.org/docs/help)
- [DeepMind: primer visoke lokalne zanesljivosti in nezanesljive meddomenske orientacije](https://deepmind.google/blog/enabling-high-accuracy-protein-structure-prediction-at-the-proteome-scale/)
