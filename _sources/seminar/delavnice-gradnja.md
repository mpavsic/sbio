# Delavnica: Gradnja in piljenje modela strukture

## Namen

Namen delavnice je spoznati osnove ročne gradnje in piljenja modela strukture proteina z uporabo eksperimentalnih podatkov. V tem primeru gre za elektronsko gostoto, izračunano iz difrakcijskih podatkov (makromolekulska X-žarkovna kristalografija), podobni principi pa veljajo tudi v primeru elektronske difrakcije in krio-elektronske mikroskopije.

## Potrebščine

Za izvedbo potrebujete:
- spletni brskalnik (najbolje na namiznem ali prenosnem računalniku, pogojno na tablici, na slednji je sicer malce težje manipulirati z modeli struktur; mobilni telefon ni primeren),
- povezavo v splet.

```{admonition} Miška
:class: hint
Priporočam uporabo miške, ki omogoča levi in desni klik ter kolešček (sredinski klik), saj to bistveno olajša manipulacijo struktur v 3D.
```

## Kratka navodila

Pri delu bomo uporabljali program [Moorhen](https://moorhen.org/), ki predstavlja spletno različico programa [COOT](https://www2.mrc-lmb.cam.ac.uk/personal/pemsley/coot/) (Crystallographic Object-Oriented Toolkit), danes najpogosteje uporabljanega programa za gradnjo, piljenje in validacijo modelov struktur makromolekul {cite:p}`Emsley2010aaa`. Isti program se lahko uporablja tako za gradnjo modelov struktur na osnovi podatkov, pridobljenih z difrakcijo, kot tudi s krio-elektronsko mikroskopijo.

### Začetni podatki

Za demonstracijo gradnje in piljenja modela bomo uporabili skoraj popolnoma zgrajen in izpiljen model strukuture človeškega estrogenskemu receptorju podobnega receptorja gama (ESRRG, UniProt [P62508](https://www.uniprot.org/uniprotkb/P62508)).

Aminokislinsko zaporedje kristaliziranega konstrukta je podano spodaj:

```
LGSPEFLNPQLVQPAKKPYNKIVSHLLVAEPEKIYAMPDPTVPDSDIKAL
TTLCDLADRELVVIIGWAKHIPGFSTLSLADQMSLLQSAWMEILILGVVY
RSLSFEDELVYADDYIMDEDQSKLAGLLDLNNAILQLVKKYKSMKLEKEE
FVTLKAIALANSDSMHIEDVEAVQKLQDVLHEALQDYEAGQHMEDPRRAG
KMLMTLPLLRQTSTKAVQHFYNIKLEGKVPMHKLFLEMLEAKVC
```

N-končni del zaporedja `LGSPEF` in C-končni ostanek `C` niso del zaporedja v UniProt, tako da le regija L220–V458 ustreza zaporedju pod zgoraj omenjenim UniProt zapisom.

Drugi relevantni podatki:
- kristalizacijski pufer: 0,05 M HEPES, 0,75 M natrijev citrat, 5 % glicerol, pH 7,5
- kokristalizacija z bisfenolom A
- ločljivost: 1,6 Å
- prostorska skupina: P 41 21 2 (tetragonalna), 8 asimetričnih enot na osnovno celico

Povezavi za prenos datotek, potrebnih za delo:
- model strukture: [esrrg_1p6_ref.pdb](https://raw.githubusercontent.com/mpavsic/sbio/main/sbio/seminar/podatki/esrrg_1p6_ref.pdb)
- strukturni faktorji, karte elektronske gostote: [esrrg_1p6_ref.mtz](https://raw.githubusercontent.com/mpavsic/sbio/main/sbio/seminar/podatki/esrrg_1p6_ref.mtz)

### Gradnja in piljenje modela

#### Nalaganje podatkov

1. Običite stran [moorhen.org](https://moorhen.org). Program je še v razvoju, zato se lahko delovanje v nekem časovnem obdobju spremeni.
2. Naložite podatke:
    - model strukture: *Menu* > *File* > *Coordinates* > *Choose Files* > `esrrg_1p6_ref.pdb`
    - strukturne faktorje ter karte elektronske gostote: *Menu* > *File* > *Auto open MTZ...* > `esrrg_1p6_ref.mtz` > *OK*
3. Povežite model strukture s strukturnimi faktorji in s tem omogočite osveževanje karte elektronske gostote v realnem času ter izračun faktorja R: *Menu* > *File* > *Connect mol. and map for updating...* > (preverite nastavitve) > *OK*
4. Razglejte se – identificirajte kanale topila in preverite "neskončnost" karte elektronske gostote.
5. Primerjajte običajno (2mFo–Fc, modre barve) ter diferečno (mFo-Fc, zelene in rdeče barve) karto elektronske gostote. Kaj nam kažeta?

**Pozor! Ko enkrat naložite podatke pazite, da ne osvežite strani ali zaprete brskalnika!**

![Moorhen z naloženim modelom strukture in kartami elektronske gostote](slike/delavnice-gradnja-Morheen-1.png)

#### Hitri tečaj za Moorhen

- vrtenje pogleda: pritisnite in držite levi miškin gumb ter vlevite v levo/desno/bavzgor/navzdol
- premikanje: pritisnite in držite sredinski miškin gumb ter vlevite v levo/desno/bavzgor/navzdol
- centriranje pogleda na nek atom: kliknite na atom s sredinskim miškinim gumbom
- odprite hitri meni za piljenje: kliknite na desni miškin gumn
- približevanje/oddaljevanje pogleda: miškin kolešček
- sprememba nivoja kontutiranja karte elektronske gostote: CTRL + miškin kolešček (pazite, katera karta je izbrana kot aktivna)

#### Gradnja in piljenje modela strukture

Model strukture ESRRG je skoraj dokončno zgrajen, kljub temu pa prisotnih nekaj napak in pomankljivosti, med drugim:
- nekateri deli so popolnoma napačno postavljeni (niso v skladu z eksperimentalnimi podatki),
- nekateri ostanki imajo dihedralne kote glavne verige izven dovoljenih območij,
- končni del verige ni zgrajen,
- nekateri ostanki bi morali imeti alternativno konformacijo,
- manjkajo ligandi,
- manjkajo molekule vode.

Nekaj namigov, kaj popraviti:
- [ ] Oglejte si ostanek Y315. Kaj je potrebno tu popraviti? (Glejte namig 1.)
    -  Za premikanje po zaporedju kliknite *Menu* > *Models* > *Sequences* ali pa pritisnite "SHIFT + g" in vnesite zaporedno številko ostanka.
- [ ] Oglejte si ostanek N235. Se vam zdi v redu glede na elektronsko gostoto in kemijsko okolje? (Glejte namig 2.)
- [ ] Oglejte si regijo V325–A327. (Glejte namig 3.)
- [ ] Oglejte si S428. Kaj manjka? (Glejte namig 4.)
- [ ] Oglejte si C-končni del. Bi lahko zgradili še kakšen del polipeptidne verige? (Glejte namig 5.)
- [ ] Analizirajte nezmodelirane "balončke" (*blobs*; *Menu* > *Validation* > *Unmodelled blobs...*). Prvi na seznamu je največji. Kaj bi lahko sem umestili? Poglejte, s čim je bil protein kristaliziran in kaj je bilo v pufru.
    - Ligand lahko dodate tako: *Menu* > *Ligand* > *Get monomer...* > vnesite Ligand Expo ID.
        - Po dodatku liganda je potrebno izpiliti ujemanje z elektronsko gostoto.
    - Druga možnost je avtomatsko iskanje liganda preko *Menu* > *Ligand* > *Find ligand...*, pri čemer pa moramo ligand že imeti naložen nekje v prostoru.

**Med gradnjo opazujte spreminjanje diferenčne karte elektronske gostote ter vrednosti faktorja R.**

Namigi za gradnjo:
1. Izberite drug rotamer, nato pa naredite še piljenje v realnem prostoru (*real space refinement*), včasih zadostuje zgolj piljenje v realnem prostoru.
2. Stransko skupino je potrebno obrniti za 180°. Kaj s tem dosežemo v smislu interakcij s sosednjimi skupinami?
3. Popraviti je potrebno položaj daljšega odseka, izberite vsaj regijo V325–A327. Za izbiro regije držite SHIFT in enkrat kliknite na katerikoli atom prvega ostanka v željenem odseku, nato pa še na katerikoli atom zadnjega. Popravek naredite tako, da najprej malce ročno povlečete regijo v elektronsko gostoto, na koncu pa naredite še piljenje v realnem prostoru.
4. Ta ostanek ima alternativno konformacijo. Dodajte jo, zanjo izberite drug konformer, ter zaključite s piljenjem v realnem prostoru.
5. Seveda, preverite aminokislinsko zaporedje kristaliziranega konstrukta in jih dodajte toliko, kolikor jih lahko glede na elektronsko gostoto ter jih lepo umestite vanjo. Lahko zgradite popolnoma ves C-konec?

### Analiza oligomernega stanja

Transkripcijsko aktivna oblika ESRRG je dimer.

- Koliko verig je v asimetrični enoti?
- So med verigami iz sosednjih asimetričnih enot obsežnejši kontakti, ki bi lahko kazali na to, da bi omogočali stabilno oligomerno stanje v raztopini? (Namig: uporabite strežnik [PDBePISA](https://www.ebi.ac.uk/pdbe/pisa/).)
    - Model strukture shranite (*Menu* > *Models* > kliknite ikono za prenos).

### Podatki pri nižji ločljivosti

Oglejte si še, kako izgleda elektronska gostota pri nižji ločljivosti in sicer pri 3,2 Å. Gre za strukturo mišjega ESRRG v kompleksu z neko drugo spojino.

1. Pobrišite vse, kar imate naloženo v Moorhen: *Menu* > *File* > *Delete everything*, ali preprosto ponovno naložite spletno stran.
2. Naložite v zbirki deponiran model strukture in že izračunane karte elektronske gostote: *Menu* > *File* > *Fetch from online services (PDBe)* > 1VJB (vključite *fetch data for map*) > *Fetch*
3. Oglejte si elektronsko gostoto in razmislite, kako je graditi model strukture pri taki ločljivosti...

## Drugi viri

- kratek opis različnih kart elektronske gostote na strani RCSB PDB: [X-ray Electron Density Maps](https://www.rcsb.org/docs/general-help/x-ray-electron-density-maps)

## Uporabljeni podatki

Pri pripravi delavnice so bili uporabljeni naslednji modeli struktur in pripadajoči podatki:
- PDB 2E2R, opisan v: A. Matsushima, Y. Kakuta, T. Teramoto, T. Koshiba, X. Liu, H. Okada, T. Tokunaga, S. Kawabata, M. Kimura, Y. Shimohigashi. 2007. Structural Evidence for Endocrine Disruptor Bisphenol A Binding to Human Nuclear Receptor ERRγ. The Journal of Biochemistry 142(4), 517–524. [10.1093/jb/mvm158](https://dx.doi.org/10.1093/jb/mvm158)
- PDB 1VJB, opisan v: H. Greschik, R. Flaig, J.-P. Renaud, D. Moras. 2004. Structural Basis for the Deactivation of the Estrogen-related Receptor γ by Diethylstilbestrol or 4-Hydroxytamoxifen and Determinants of Selectivity. Journal of Biological Chemistry 279, 33639–33646. [10.1074/jbc.M402195200](https://dx.doi.org/10.1074/jbc.M402195200)

Pri pripravi podatkov je bil uporabljen program [Phenix](https://phenix-online.org/) {cite:p}`Liebschner2019aaa`.