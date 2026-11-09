# Umeščanje majhne molekule v protein

## Namen

Namen vaje je spoznati osnove molekulskega umeščanja (angl. *docking*) ter ovrednotiti vpliv izbrane strukture proteina na napoved vezave liganda. Isti ligand bomo umeščali v protein iz eksperimentalno določenega kompleksa, iz katerega bomo ligand predhodno odstranili, v neodvisno eksperimentalno določeno strukturo in v model AlphaFold. Napovedane položaje in orientacije liganda bomo primerjali z eksperimentalnim vezavnim načinom ter presodili, kako razlike v strukturi/konformaciji vezavnega mesta vplivajo na uspešnost umeščanja.

*V literaturi boste namesto izraza 'umeščanje' zasledili tudi izraz 'sidranje'.*

## Pregled pristopov umeščanja

Pri umeščanju majhnih molekul v proteine se danes uporablja več komplementarnih pristopov. Razlikujejo se predvsem v načinu iskanja vezavnih poz, obravnavi konformacijski fleksibilnosti proteina in ocenjevanju/rangiranju rezultatov. Na splošno jih lahko razdelimo v skupine:

| pristop | osnovni princip | primeri programov |
|---|---|---|
| **klasično molekulsko umeščanje** | išče položaje, orientacije in konformacije liganda v večinoma togem proteinu ter jih razvrsti s približno ocenjevalno funkcijo | [AutoDock Vina](https://vina.scripps.edu/), [Glide](https://www.schrodinger.com/platform/products/glide/), DOCK (precej star program) |
| **umeščanje z upoštevanjem konformacijske fleksibilnosti proteina** | ligand umešča v več različnih konformacij proteina (*ensemble docking*) ali med postopkom prilagaja vezavno mesto ligandu (*induced-fit docking*) | sidranje v zbirko struktur (različne konformacije), [Glide/Prime](https://www.schrodinger.com/platform/products/glide/), [IFD-MD](https://www.schrodinger.com/products/ifd-md) (Induced-Fit Docking Molecular Dynamics)|
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

Proteini BET delujejo kot "bralci" epigenetskih oznak – prek bromodomen prepoznavajo acetilirane regije kromatina ter sodelujejo pri povezovanju teh oznak z uravnavanjem transkripcije. BRD2 med drugim sodeluje pri začetku transkripcije, saj povezuje acetilirane nukleosome s transkripcijskim kompleksom TFIID. S tem vpliva na izražanje genov, pomembnih za celično delovanje, proliferacijo in odzivanje na zunanje signale. Zaradi vloge proteinov BET pri rakavih in vnetnih procesih so njihove bromodomene zanimive tarče za razvoj zaviralcev, ki preprečujejo prepoznavanje acetiliranih proteinov.

### Ligand

Nimesulid (angl. *nimesulide*(https://en.wikipedia.org/wiki/Nimesulide)) je majhna organska molekula iz skupine nesteroidnih protivnetnih zdravil (NSAIDs, *nonsteroidal anti-inflammatory drugs*). Poleg njegovega uveljavljenega protivnetnega delovanja so raziskovalci pokazali tudi neposredno vezavo na bromodomeni BRD2 in BRD4.

<iframe src="https://molstar.org/viewer/?snapshot-url=https://raw.githubusercontent.com/mpavsic/sbio/main/sbio/vaje/seje/nimesulid-NIM.molx&snapshot-url-type=molx&hide-controls=1" style="width: 75%; height: 500px; border: 0px"></iframe>

Zapis za nimesulid kot ligand v zbirki PDB je dostopen pod kodo [NIM](https://www.rcsb.org/ligand/NIM).

### Medicinska relevantnost

Nimesulid se uporablja za lajšanje akutnih menstrualnih bolečin; njegovo običajno delovanje je povezano z zaviranjem ciklooksigenaz in zmanjšano tvorbo prostaglandinov. Zaradi tveganja za poškodbe jeter je njegova sistemska uporaba v EU na kratkotrajno uporabo. Vezava na bromodomene BET predstavlja raziskovalno ugotovitev in izhodišče za razvoj novih spojin, ne pa sicer uveljavljene uporabe nimesulida kot epigenetskega ali protirakavega zdravila.

## 


https://www.moldraw.com/tools/free-chem-tools/pdb-to-pdbqt-converter.html

---

## Viri

Za pripravo datotek za vaje so bili uporabljeni javno dostopni podatki iz članka **BET Bromodomain Targeting by NSAIDs: Structural, Biophysical, and Computational Insights** {cite:p}`Sridhar2026aaa`.

