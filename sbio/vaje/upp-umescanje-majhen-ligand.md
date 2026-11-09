# Umeščanje majhne molekule v protein

## Namen

Namen vaje je spoznati osnove molekulskega umeščanja (angl. *docking*) ter ovrednotiti vpliv izbrane strukture proteina na napoved vezave liganda. Isti ligand bomo umeščali v protein iz eksperimentalno določenega kompleksa, iz katerega bomo ligand predhodno odstranili, v neodvisno eksperimentalno določeno strukturo in v model AlphaFold. Napovedane položaje in orientacije liganda bomo primerjali z eksperimentalnim vezavnim načinom ter presodili, kako razlike v strukturi/konformaciji vezavnega mesta vplivajo na uspešnost umeščanja.

*V literaturi boste namesto izraza 'umeščanje' zasledili tudi izraz 'sidranje'.*

## Pregled pristopov umeščanja

Pri umeščanju majhnih molekul v proteine se danes uporablja več komplementarnih pristopov. Razlikujejo se predvsem v načinu iskanja vezavnih poz, obravnavi konformacijski fleksibilnosti proteina in ocenjevanju/rangiranju rezultatov. Na splošno jih lahko razdelimo v skupine:

| pristop | osnovni princip | primeri programov |
|---|---|---|
| **klasično molekulsko umeščanje** | išče položaje, orientacije in konformacije liganda v večinoma togem proteinu ter jih razvrsti s približno ocenjevalno funkcijo | [AutoDock Vina](https://vina.scripps.edu/), [Glide](https://www.schrodinger.com/platform/products/glide/), DOCK (precej star program) |
| **umeščanje z upoštevanjem konformacijske fleksibilnosti proteina** | ligand umešča v več različnih konformacij proteina (*ensemble docking*) ali med postopkom prilagaja vezavno mesto ligandu (*induced-fit docking*) | umeščanje v zbirko struktur (različne konformacije), [Glide/Prime](https://www.schrodinger.com/platform/products/glide/), [IFD-MD](https://www.schrodinger.com/products/ifd-md) (Induced-Fit Docking Molecular Dynamics)|
| **umeščanje z ocenjevanjem z UI** | klasično iskanje poz dopolnjuje z nevronskimi mrežami za njihovo ocenjevanje oziroma optimizacijo | [GNINA](https://github.com/gnina/gnina) |
| **generativno umeščanje z UI** | naučen model neposredno generira možne vezavne poze liganda v podani strukturi proteina | [DiffDock](https://github.com/gcorso/DiffDock), DiffDock-L |
| **skupno napovedovanje strukture kompleksa** | iz zaporedja proteina in strukture liganda napove strukturo celotnega kompleksa, vključno s konformacijo proteina | [AlphaFold 3](https://github.com/google-deepmind/alphafold3) ([strežnik](https://alphafoldserver.com/)), [Boltz-2](https://github.com/jwohlwend/boltz), [Chai-1](https://github.com/chaidiscovery/chai-lab) oz. [Chai-2](https://www.chaidiscovery.com/) |

Klasični in nekateri pristopi z UI torej uporabljajo že "pripravljeno" strukturo proteina (eksperimentalno določeno ali napovedano vnaprej ločeno brez liganda), medtem ko modeli za skupno napovedovanje kompleksa napovedujejo strukturo proteina hkrati z vezanim ligandom. Za kovalentne inhibitorje, koordinacijo kovin, pomembne vezavne vode in makrociklične ligande so pogosto potrebni posebni protokoli.

**Pri tej vaji boste spoznali na nek način obe skrajnosti**:
- **klasično umeščanje** z uporabo programa AutoDock Vina, ki išče možne položaje, orientacije in konformacije majhne molekule v izbranem območju proteina. Pri običajnem postopku je protein tog, ligand pa lahko spreminja konformacijo z vrtenjem okoli izbranih vezi. Program dobljene vezavne poze razvrsti z ocenjevalno funkcijo, ki približno ovrednoti ugodnost vezave. Dobljene ocene omogočajo primerjavo napovedanih poz, vendar same po sebi ne dokazujejo vezave in ne predstavljajo zanesljive vezavne afinitete;
- **napovedovanje strukture kompleksa** z AlphaFold 3.

## Tarča in ligand

### Tarča

Kot tarčo (t.j. protein, v katerega umeščamo ligand) bomo uporabili človeški protein [**BRD2**] (*Bromodomain-containing protein 2*, UniProt [P25440](https://www.uniprot.org/uniprotkb/P25440/)). Spada v družino BET (*bromodomain and extra-terminal*), kamor uvrščamo zraven BRD2 še paraloge BRD3, BRD4 in BRDT (več o njih v [preglednem članku](https://doi.org/10.1038/s41392-020-00384-4)). Vsebuje dve bromodomeni, BD1 in BD2, ki prepoznavata acetilirane lizinske ostanke na histonih in drugih proteinih. Model strukture BRD2 je na voljo v [AlphaFold Protein Structure Database](https://alphafold.ebi.ac.uk/entry/AF-P25440-3-F1).

Proteini BET delujejo kot "bralci" epigenetskih oznak – prek bromodomen (BD) prepoznavajo acetilirane regije kromatina ter sodelujejo pri povezovanju teh oznak z uravnavanjem transkripcije. BRD2 med drugim sodeluje pri začetku transkripcije, saj povezuje acetilirane nukleosome s transkripcijskim kompleksom TFIID. S tem vpliva na izražanje genov, pomembnih za celično delovanje, proliferacijo in odzivanje na zunanje signale. Zaradi vloge proteinov BET pri rakavih in vnetnih procesih so njihove bromodomene zanimive tarče za razvoj zaviralcev, ki preprečujejo prepoznavanje acetiliranih proteinov.

### Ligand

Nimesulid (angl. *nimesulide*(https://en.wikipedia.org/wiki/Nimesulide)) je majhna organska molekula iz skupine nesteroidnih protivnetnih zdravil (NSAIDs, *nonsteroidal anti-inflammatory drugs*). Poleg njegovega uveljavljenega protivnetnega delovanja so raziskovalci pokazali tudi neposredno vezavo na bromodomeni BRD2 in BRD4.

<iframe src="https://molstar.org/viewer/?snapshot-url=https://raw.githubusercontent.com/mpavsic/sbio/main/sbio/vaje/seje/nimesulid-NIM.molx&snapshot-url-type=molx&hide-controls=1" style="width: 75%; height: 500px; border: 0px"></iframe>

Zapis za nimesulid kot ligand v zbirki PDB je dostopen pod kodo [NIM](https://www.rcsb.org/ligand/NIM).

### Medicinska relevantnost

Nimesulid se uporablja za lajšanje akutnih menstrualnih bolečin; njegovo običajno delovanje je povezano z zaviranjem ciklooksigenaz in zmanjšano tvorbo prostaglandinov. Zaradi tveganja za poškodbe jeter je njegova sistemska uporaba v EU na kratkotrajno uporabo. Vezava na bromodomene BET predstavlja raziskovalno ugotovitev in izhodišče za razvoj novih spojin, ne pa sicer uveljavljene uporabe nimesulida kot epigenetskega ali protirakavega zdravila.

## Potek vaje

### AutoDock Vina

#### Namestitev programa

Posebna namestitev ni potrebna, prenesite si le prevedeno obliko zadnje verzije z GitHub za [običajno poganjanje](https://github.com/ccsb-scripps/AutoDock-Vina) ali [poganjanje z GPU pospešitvijo](https://github.com/ccsb-scripps/AutoDock-GPU); izberite ustrezno arhitekturo.

Če boste program poganjali na novejših verzijah macOS morate omogočiti zaganjanje programa, na primer: `xattr -d com.apple.quarantine vina_1.2.7_mac_aarch64` in `chmod a+x vina_1.2.7_mac_aarch64` (slednje je potrebno tudi na Linux).

#### Priprava vhodnih sturktur

Najprej je potrebno pripraviti strukturo tarče (proteina) in liganda v primernem formatu, npr. PDB, in sicer v ločenih datotekah. Datoteke lahko pripravite sami s pomočjo kakšne skripte, UCSF ChimeraX, ... (pač, pobrišete vse neproteinske molekule), za večjo prikladnost so spodaj na voljo naslednje že "očiščene" strukture tarče: 
- [`BRD2_BD2-pdb24KN-clean.pdb`](datoteke/BRD2_BD2-pdb24KN-clean.pdb) (gre za kristalno strukturo domene BD2 proteina BRD2, določeno v kompleksu z našim ligandom, nimesulidom, iz katere pa je bil slednji odstranjen; PDB [24KN](https://www.rcsb.org/structure/24KN))
- [`BRD2_BD2-modaf3.pdb`](datoteke/BRD2_BD2-modaf3.pdb) (AlphaFold 3 model domene BD2 proteina BRD2 in sicer z identičnim aminokislinskim zaporedjem kot v zapisu PDB [24KN](https://www.rcsb.org/structure/24KN); izmed petih izračunanih modelov je bil izbran prvi, ostali so imeli izredno podobno konformacijo)
- [`BRD_DB2-pdb5IBN-clean.pdb`](datoteke/BRD2_BD2-pdb5IBN-clean.pdb) (kristalna struktura apo-oblike domene BD2 proteina BRD2, t.j. brez liganda; PDB [5IBN](https://www.rcsb.org/structure/5IBN))
- **dodatno še sami pripravite in shranite dva modela strukture mutiranega BD2 BRD2** na osnovi `BRD2_BD2-pdb24KN-clean.pdb`, pri čemer v ChimeraX (uporabite znanje s [prejšnje vaje](upp-vizualizacija-analiza-struktur.md)) ločeno zmutirate:
   - N429A (UniProt številčenje) – ta mutacija je opažena "v naravi", tako zmutirana DB2 ne veže več acetiliranega K12 histona H4
   - L381F (UniProt številčenje) – tudi na tem mestu je znana mutacija in sicer L381A, ki zmanjša jakost vezave acetiliranega K12 histona H4, vi pa boste za namen vaje ta leucinski ostazenk zmutirali v fenilalaninskega

```{admonition} Shranjevanje koordinat
:class: hint
Za lažjo pripravo parametrov za umeščanje in primerjavo rezultatov je priporočljivo, da imate vse modele struktur tarče odprte hkrati v ChimeraX, jih poravnate, ter nato shranite v ločene datoteke in pri tem omogočite shranjevanje koordinat relativno glede na eno od struktur (`Save relative to model...`). Tako so bile strukture `BRD2_BD2-modaf3.pdb` in `BRD_DB2-pdb5IBN-clean.pdb` poravnane in shranjene relativno glede na `BRD2_BD2-pdb24KN-clean.pdb`.
```

Naslednji korak je dodajanje vodikovih atomov na strukture proteina (pri določeni vrednosti pH, ponavadi je to 7 ali 7.4) in liganda ter določitev, okoli katerih vezi v ligandu je možna rotacija (privzeto se pusti vse, okoli katerih je rotacija teoretično možna) – pri tem iz datotek formata PDB dobimo datoteke formata PDBQT. To lahko naredimo na več načinov oz. z različnimi programi, mi bomo uporabili kar spletni [PDB-to-PDBQT converter](https://www.moldraw.com/tools/free-chem-tools/pdb-to-pdbqt-converter.html). **Torej, vse vhodne datoteke pretvorite in si jih shranite (najbolje z istim imenom, le končnica naj bo `.pdbqt`).**

#### Priprava parametrov za umeščanje

Katere parametre AutoDock Vina potrebuje lahko izvemo enostavno tako, da program začenemo brez parametrov: `./vina_1.2.7_linux_x86_64`. Nekaj najbolj pogostih je navedenih tukaj:
- datoteka s strukturo tarče (receptor)
- datoteka z ligandom
- središče iskalne škatle (*box center*) – koordinate središča območja, v katerem program išče vezavne poze liganda (če približno vemo, kam ciljamo, lahko z ustrezno prilagoditvijo tega parametra in velikostjo škatle pohitrimi iskanje)
- velikost iskalne škatle (*box size*) – dolžine robov iskalnega območja v smereh x, y in z, izražene v Å
- temeljitost iskanja  (*exhaustiveness*) – uravnava obseg iskanja; večja vrednost praviloma poveča računski čas in možnost, da program najde ugodne poze; parameter ima lahko vrednosti med 1 in 8
- razmik mreže (*grid spacing*, `spacing`) – razdalja med sosednjimi točkami mreže za predizračun interakcij, izražena v Å; za vajo ohranimo privzeto vrednost 0,375 Å
- število procesorskih jeder (`cpu`)
- izhodna datoteka (`out`) – ime izhodne PDBQT datoteke, ki bo vsebovala poze liganda (če jo odpremo skupaj z vhodno strukturo tarče/receptorja, bo ligand pravilno postavljen relativno glede na tarčo)

Položaj središča škatle in njeno velikost lahko določimo v UCSF ChimeraX in sicer tako, da najprej instaliramo vtičnik Vinardock (preko `Tools > More Tools...`), nato pa:
1. Naložimo strukturo tarče oz. receptorja (lahko kar PDBQT datoteko).
2. Ustrezno premaknemo središče in prilagodimo velikost škatle. Če želimo zajeti celoten protein lahko kar kliknemo na `Autobox`.
3. Središče in velikost škatle vidimo pod `Center` in `Size`, skopiramo si jih lahko s `Copy config`.

AutoDock Vina lahko poganjamo tako, da zahtevane parametre določimo kar v ukazni vrstici, lahko pa si pripravimo konfiguracijsko datoteko, na primer `BRD2_BD2-pdb24KN.txt`:
```
receptor = BRD2_BD2-pdb24KN-clean_receptor.pdbqt
ligand = NIM.pdbqt
cpu = 8
exhaustiveness = 8
center_x = 10
center_y = 1
center_z = -1
size_x = 60
size_y = 60
size_z = 60
out = BRD2_BD2-pdb24KN-NIM.pdbqt
```

#### Umeščanje 

Če ste parametre zapisali v konfiguracijsko datoteko lahko umeščanje zaženemo kot `./vina_1.2.7_linux_x86_64 --config BRD2_BD2-pdb24KN.txt`, sicer pač uporabite zapis navedbo parametrov neposredno v ukazni vrstici.

Pazite, da za posamezna poganjanja z različnimi parametri določite novo izhodno datoteko; privzeto (če ni posebej določeno) dobi izhodna datoteka ime `${ligand}_out.pdbqt`.

Rezultate umeščanja si ogledate tako, da v UCSF ChimeraX hkrati odprete strukturo tarče in pa izhodno PDBQT datoteko; avtomatsko se vam odpre okno, v katerem lahko izbirate posamezne poze in si ogledate nekaj statistike.

**Zaženite vsa umeščanja, pri tem pa pazite, da boste imeli izhodne datoteke smiselno poimenovane (da boste prepoznali, kaj je kaj).**

### AlphaFold 3

Izračun strukture kompleksa tarče in liganda lahko enostavno naredimo na [strežniku AlphaFold 3](https://alphafoldserver.com/):
1. Kot protein vnesemo aminokislinsko zaporedje tarče.
2. Dodamo še eno "entiteto", katere tip nastavimo na `CCD Code` in v primeru nimesulida vnesemo kodo `NIM`.
3. Posel pošljemo na strežnik, počakamo ... in nato prenesemo datoteko z modeli strukture kompleksa in ocenami zanesljivosti).

Zraven zaporedja divjega tipa naredite umeščanje tudi z mutirano obliko BD2 BRD2 z mutacijo L381F.

### Analiza modelov kompleksov

Rezultate vseh sedmih umeščanj primerjajte med seboj ter s kristalno strukturo kompleksa (PDB [24KN](https://www.rcsb.org/structure/24KN)) z uporabo UCSF ChimeraX (rezultate iz AlphaFold 3 poravnajte z MatchMaker-jem) in odgovorite na vprašanja:
1. **Kako dobro umeščanje v kristalno strukturo BRD2 BD2 reproducira eksperimentalno vezavno pozo nimesulida?** Primerjajte položaj, orientacijo in konformacijo liganda. Ali je eksperimentalni pozi najbolj podobna prav najbolje ocenjena poza?
2. **Kako izbira strukture receptorja vpliva na rezultate umeščanja?** Primerjajte rezultate za kristalno strukturo kompleksa z odstranjenim ligandom, neodvisno določeno apo-strukturo in model AlphaFold 3. Katere razlike v vezavnem mestu bi lahko pojasnile opažene razlike, če sploh so kakšne?
3. **Katere interakcije stabilizirajo nimesulid v eksperimentalnem kompleksu in katere se ohranijo v napovedanih pozah?** Ocenite vodikove vezi, hidrofobne stike in morebitne sterične ovire. Ali podobna ocena AutoDock Vina vedno pomeni tudi podoben vzorec interakcij?
4. **Kako mutacija N429A vpliva na napovedano vezavo nimesulida?** Ali izguba vezave acetiliranega Lys12 histona H4 nujno pomeni tudi izgubo vezave nimesulida? Odgovor utemeljite s primerjavo kemijskih skupin in njihovih interakcij z vezavnim mestom.
5. **Kako se rezultat umeščanja spremeni pri mutaciji L381F?** Ali večja stranska skupina prepreči prvotno vezavno pozo, povzroči premik liganda ali omogoči drugačne ugodne stike? Kako bi na rezultat vplivala možnost spremembe rotamera Phe381?
6. **Kako se kompleks, neposredno napovedan z AlphaFold 3, razlikuje od rezultatov umeščanja z AutoDock Vina in eksperimentalne strukture?** Primerjajte tako ligand kot bližnje aminokislinske ostanke. Ali je morebitna boljša namestitev liganda povezana tudi z drugačno konformacijo vezavnega mesta?
7. **Ali AlphaFold 3 pri napovedi kompleksa mutante L381F z nimesulidom predvidi prilagoditev vezavnega mesta, ki omogoči vezavo liganda?** Primerjajte rotamer Phe381, položaj nimesulida in morebitne sterične ovire z rezultatom umeščanja z AutoDock Vina ter eksperimentalnim kompleksom izhodnega proteina. Ali napoved kompleksa brez steričnih ovir že dokazuje, da mutanta veže nimesulid?
8. **Kaj lahko na podlagi teh izračunov sklepate o dejanski vezavi in afiniteti nimesulida?** Ali ugodna ocena AutoDock Vina oziroma visoka zanesljivost modela AlphaFold 3 dokazujeta vezavo? Predlagajte eksperimentalno metodo za preverjanje napovedanih razlik med izhodnim proteinom in mutantama.

---

## Viri

Za pripravo datotek za vaje so bili uporabljeni javno dostopni podatki iz članka **BET Bromodomain Targeting by NSAIDs: Structural, Biophysical, and Computational Insights** {cite:p}`Sridhar2026aaa`.

Drugi programi, uporabljeni med pripravo datotek:
- [UCSF ChimeraX](https://www.cgl.ucsf.edu/chimerax/)