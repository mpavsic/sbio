# Napovedovanje proteinskih struktur in kompleksov: AlphaFold Server in SWISS-MODEL

**Predvideno trajanje:** približno 2 uri  
**Orodja:** [UniProt](https://www.uniprot.org/), [AlphaFold Server](https://alphafoldserver.com/), [AlphaFold Protein Structure Database](https://alphafold.ebi.ac.uk/), [SWISS-MODEL](https://swissmodel.expasy.org/interactive), UCSF ChimeraX, [RCSB PDB](https://www.rcsb.org/).

**Glavni protein:** človeški **endophilin-B2 (SH3GLB2)**, UniProt **[Q9NR46](https://www.uniprot.org/uniprotkb/Q9NR46/entry)**, 395 aminokislin. Gre za naravni večdomenski protein, za katerega pri pregledu UniProt/PDB nismo našli eksperimentalne strukture. Zanj pa obstaja že računska napoved v [AlphaFold DB](https://alphafold.ebi.ac.uk/entry/Q9NR46). To **ni** eksperimentalna struktura.

**Zgradba:** domena **BAR (24–287)**, povezovalna regija približno **288–334**, domena **SH3 (335–395)**. Meje so po anotacijah UniProt, ne po neposredni analizi nove napovedi.

> **Opomba za izvedbo:** Ta protein je strukturno *obetaven* primer za razlikovanje med pLDDT in PAE, vendar **močna meddomenska negotovost v rezultatu AlphaFold Server ni vnaprej zagotovljena**. Pred vajami preverite dejanski PAE in shranite ustrezno napoved. Zanesljiv rezervni prikaz koncepta je primer **RAD23A (UniProt P54725)** iz uradne predstavitve AlphaFold: posamezne regije so napovedane z visoko lokalno zanesljivostjo, medsebojna lega pa je manj zanesljiva. Ta rezervni primer ni nadomestilo za osrednjo praktično nalogo.

## Namen

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

## Viri

- [UniProt: SH3GLB2, Q9NR46](https://www.uniprot.org/uniprotkb/Q9NR46/entry)
- [AlphaFold Database: Q9NR46](https://alphafold.ebi.ac.uk/entry/Q9NR46)
- [EMBL-EBI: Interpretacija rezultatov AlphaFold Server](https://www.ebi.ac.uk/training/online/courses/alphafold/alphafold-3-and-alphafold-server/alphafold-server-your-gateway-to-alphafold-3/interpreting-results-from-alphafold-server/)
- [SWISS-MODEL dokumentacija](https://swissmodel.expasy.org/docs/help)
- [DeepMind: primer visoke lokalne zanesljivosti in nezanesljive meddomenske orientacije](https://deepmind.google/blog/enabling-high-accuracy-protein-structure-prediction-at-the-proteome-scale/)
