# Gradnja modela strukture z uporabo elektronske gostote

## Namen

Namen delavnice je spoznati osnove ročne gradnje in piljenja modela strukture proteina z uporabo eksperimentalnih podatkov, v konkretnem primeru gre za elektronsko gostoto, izračunano iz difrakcijskih podatkov (makromolekulska X-žarkovna kristalografija), podobni principi pa veljajo tudi v primeru elektronske difrakcije in krio-elektronske mikroskopije.

Pri delu bomo uporabljali program [Moorhen](https://moorhen.org/), ki predstavlja spletno različico programa [COOT](https://www2.mrc-lmb.cam.ac.uk/personal/pemsley/coot/) (Crystallographic Object-Oriented Toolkit), danes najpogosteje uporabljanega programa za gradnjo, piljenje in validacijo modelov struktur makromolekul {cite:p}`Emsley2010aaa`. Isti program se lahko uporablja tako za gradnjo modelov struktur na osnovi podatkov, pridobljenih z difrakcijo (rentgenska, elektronska difrakcija), kot tudi s krio-elektronsko mikroskopijo.

## Vaša naloga

- Z uporabo Morheen dogradite in izboljšajte model strukture $\beta$-laktamaze KPC-2 z vezanim inhibitorjem avibaktamom, pri tem pa uporabite karto elektronske gostote, izračunano na osnovi difrakcijskih podatkov (ločljivost 1.8 Å).
    - 'Dogradite' pomeni, da v trenutnem modelu strukure nekateri deli (aminokislinski ostanki, ligandi, ...) manjkajo in jih morate dodati, 'izboljšajte' pa, da prilagodite koordinate dodatnih ter v modelu že prisotnih atomov/ostankov tako, da bodo kar se da skladni z eksperimentalnimi podatki (elektronska gostota) kot tudi stereokemijskimi parametri (Ramachandranov diagram, dolžine vezi, koti med vezmi, rotameri itd.) in bo končen model imel tudi kemijski smisel.
- Na koncu vaš dograjen in izboljšan model primerjajte z izpiljenim modelom strukture, deponiranim v zbirko PDB.

## Postavimo protein v kontekst (= nekaj malega o KPC-2)

### Splošno o $\beta$-laktamazah

$\beta$-laktamaze so bakterijski encimi, ki s hidrolizo odprejo $\beta$-laktamski obroč antibiotikov in jih tako inaktivirajo. S tem preprečijo, da bi antibiotiki zavirali sintezo bakterijske celične stene, zato so pomemben vzrok odpornosti proti penicilinom, cefalosporinom in drugim $\beta$-laktamskim antibiotikom (več: [Betalaktamski_antibiotik @ Wikipedia](https://sl.wikipedia.org/wiki/Betalaktamski_antibiotik)).

![Betalaktamski antibiotiki](slike/betalaktmski-antibiotiki.png)

Po Amblerjevi klasifikaciji jih delimo v štiri razrede, A, B, C in D: razredi A, C in D imajo v aktivnem mestu katalitični serin, razred B pa obsega metalo-$\beta$-laktamaze, ki za delovanje potrebujejo cinkove ione. Med značilne predstavnike sodijo encimi TEM, SHV, CTX-M in KPC v razredu A, NDM, VIM in IMP v razredu B, AmpC v razredu C ter encimi OXA v razredu D. Posebej problematične so $\beta$-laktamaze razširjenega spektra (*Extended-Spectrum Beta-Lactamases*, ESBL) in karbapenemaze, saj zmanjšujejo izbor učinkovitih antibiotikov, njihovi geni pa se lahko med bakterijami širijo s plazmidi.

Njihovo delovanje lahko obidemo s kombiniranjem $\beta$-laktamskega antibiotika z zaviralcem (inhibitorjem) $\beta$-laktamaz, ki antibiotik zaščiti pred encimsko razgradnjo. Klasični primeri so **amoksicilin s klavulansko kislino, ampicilin s sulbaktamom in piperacilin s tazobaktamom**, pri čemer ti zaviralci delujejo predvsem proti številnim encimom razreda A. Novejše kombinacije vključujejo **ceftazidim z avibaktamom, meropenem z vaborbaktamom in imipenem z relebaktamom**, ki omogočajo zaščito tudi pred nekaterimi $\beta$-laktamazami, odpornimi proti starejšim zaviralcem. Avibaktam zavira številne encime razredov A in C ter nekatere razreda D, vaborbaktam in relebaktam pa predvsem encime razredov A in C; nobeden od teh treh zaviralcev ne zavira metalo-$\beta$-laktamaz razreda B. Pri bakterijah z metalo-$\beta$-laktamazami je uporabna kombinacija **aztreonama z avibaktamom**, saj je aztreonam praviloma odporen proti hidrolizi s temi encimi, avibaktam pa ga zaščiti pred drugimi $\beta$-laktamazami, ki jih bakterija lahko proizvaja hkrati.

### KPC-2

KPC-2 (*Klebsiella pneumoniae* karbapenemaza tipa 2) je serinska $\beta$-laktamaza razreda A, ki hidrolizira številne $\beta$-laktamske antibiotike, vključno s karbapenemi, in tako bakterijam omogoča odpornost tudi proti tem pomembnim zdravilom. **Avibaktam jo zavira tako, da s katalitičnim serinom v njenem aktivnem mestu tvori reverzibilno kovalentno vez in prepreči razgradnjo antibiotika.** Kombinacija ceftazidima z avibaktamom je pomembna možnost zdravljenja okužb z bakterijami, ki proizvajajo KPC-2, saj hkratna administracija omogoča učinkovito delovanje ceftazidima. Težavo lahko predstavljajo mutacije KPC-2, ki zmanjšajo občutljivost za avibaktam in povzročijo odpornost tudi proti tej kombinaciji. Razumevanje podrobnosti vezave avibaktama na KPC-2 je tako pomembno z vidika načrtovanja novih tovrstnih inhibitorjev.

## Vhodni podatki

### Protein

Gre za encim KPC-2 iz *Klebsiella pneumoniae* (UniProt [Q9F663](https://www.uniprot.org/uniprotkb/Q9F663)), rekombinantno pripravljen v **Escherichia coli**. Za izražanje je bila uporabljena nekoliko skrajšana oblika proteina z naslednjim aminokislinskim zaporedjem:

```text
TNLVAEPFAKLEQDFGGSIGVYAMDTGSGATVSYRAEERFPLCSSFKGFLAAAVLARSQQ
QAGLLDTPIRYGKNALVPWSPISEKYLTTGMTVAELSAAAVQYSDNAAANLLLKELGGPA
GLTAFMRSIGDTTFRLDRWELELNSAIPGDARDTSSPRAVTESLQKLTLGSALAAPQRQQ
FVDWLKGNTTGNHRIRAAVPADWAVGDKTGTCGVYGTANDYAVVWPTGRAPIVLAVYTRA
PNKDDKHSEAVIAAAARLALEGLG
```

### Kristalizacija in ligand

Protein je bil kristaliziran z uporabo metode z difuzijo vodne pare na način sedeče kapljice, raztopina rezervoarja je imela naslednjo sestavo: 20 % (w/v) PEG 6000, 100 mM kalijev tiocianat, 100 mM citrat pH 4,0. Dobljeni kristali so bili inkubirani 8 min v raztopini avibaktama (koncentracija 5 mM) v nekoliko spremenjeni matični raztopini (25 % PEG 6000, 100 mM citrat pH 5.0, 20 % etilen glikol), nato pa zamrznjeni v tekočem dušiku.

Kemijsko ime za avibaktam je (2S,5R)-1-formil-5-[(sulfooksi)amino]piperidin-2-karboksamid, najdemo ga v zbirki ligandov na RCSB PDB (koda [NXL](https://www.rcsb.org/ligand/NXL)).

<iframe src="https://molstar.org/viewer/?snapshot-url=https://raw.githubusercontent.com/mpavsic/mpavsic.github.io/sbio/vaje/seje/structure/avibaktam-NXL.molx&snapshot-url-type=molx&hide-controls=1" style="width: 100%; height: 300px; border: 0px"></iframe>

(difrakcijski-podatki)=
### Difrakcijski podatki in začetni model

Difrakcijski podatki so bili posneti pod krio-pogoji, sprocesirani (prostorska skupina $P 2_1 2_1 2_1$), za faziranje z molekulsko zamenjavo ([*molecular replacement*](https://en.wikipedia.org/wiki/Molecular_replacement)) pa je bila uporabljena znana (eksperimentalno določena) struktura podobne $\beta$-laktamaze. Po molekulski zamenjavi je bil ta začetni model uporabljen za začetno gradnjo modela strukture KPC-2. V asimetrični enoti je ena molekula proteina, KPC-2 pa je sicer znan kot monomeren protein.

- datoteka z elektronsko gostoto (karti $2F_o – F_c$ in $F_o – F_c$): [KPC2avi.mtz](datoteke/KPC2avi.mtz)
- datoteka z delno zgrajenim modelom strukture: [KPC2avi.pdb](datoteke/KPC2avi.pdb)

## Potek vaje

1. Pojdite na spletno stran [Moorhen.org](https://moorhen.org/).
2. Naložite PDB (koordinate) in MTZ (strukturni faktorji, karte elektronske gostote) datoteki (`"hamburger menu" > File > Open Files`), [prenešeni s te spletne strani](difrakcijski-podatki).
3. Spremenite prikaz proteina iz načina 'Ribbons' v 'Bonds': `Models` >  ikona svinčnika...
4. Koordinate povežite s kartami: `"hamburger menu" > File > Associate reflections to map...`.
5. 




Vklopite prikaz simetrijsko povezanih molekul v drugih asimetričnih enotah.