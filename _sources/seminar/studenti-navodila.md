# Navodila za pripravo seminarske naloge

## Splošne informacije
Na seminarjih **vsak posamezno** predstavi strukturo proteina (lahko multiproteinskega kompleksa, tudi kompleksa protein:NA ipd.), pri tem pa se osredotoči na:
- pripravo proteina,
- metode, neposredno ali posredno uporabljene pri določanju strukture oz. pridobivanju strukturnih podatkov,
- povezavo med določeno strukturo in funkcijo proteina (*Kaj struktura razloži?*).

Navodila za pripravo, predstavitev in vodenje predstavitve seminarske naloge so zbrana na tej strani, v [spletni učilnici UL FKKT](https://ucilnica.fkkt.uni-lj.si) (predmet Struktura proteinov, razdelek Seminar) pa najdete še:
- tabelo z izbranimi temami/članki, razporedom predstavitev, roki za oddajo in razporedom vodij predstavitev,
- povezavo za oddajo predstavitve in spremljajočih datotek,
- zbirko vseh predstavitev in datotek s sejami za interaktivni ogled struktur in
- seznam seminarjev, ki pridejo v poštev kot [snov za izpit](seminar-izpit).

### Ocena seminarske naloge
Vse seminarske naloge bodo ocenjene, k oceni pa prispeva tako vsebina naloge (besedilo in slikovni material na drsnicah, še posebej [slikovni material, ki ste ga pripravili sami](vizualizacija-struktur)) kot tudi sama predstavitev pred publiko in odgovori med diskusijo. Ocena seminarske naloge je del končne ocene pri predmetu.

```{admonition} Pomembno
:class: attention
K oceni lahko (med drugim) **negativno** prispeva slabo vodenje predstavitve seminarske naloge vašega kolega.
```

(seminar-izpit)=
### Snov za izpit
**Predavatelj izbere za vsak izpitni rok po 4 seminarske naloge** (na vsakem izpitnem roku bodo tako druge 4 seminarske naloge). Seznam izbranih seminarskih nalog bo objavljen po vseh predstavitvah, najkasneje pa do začetka izpitnega obdobja.

### Prisotnost na predstavitvah
**Vsak mora biti aktivno prisoten na vsaj 70 % terminov predstavitev seminarskih nalog** (na 30 % terminov lahko torej manjkate brez opravičila). Prisotnost se bo preverjala. Neizpolnitev tega pogoja se šteje kot neopravljena seminarska obveznost (enako kot neoddaja seminarske naloge in/ali neizvedena predstavitev), posledično ne morete pristopiti k izpitu. V primeru večkratne odsotnosti zaradi zdravstvenih težav, treningov (status športnika) ipd. kontaktirajte predavatelja. *Opomba: ne izkoriščajte po nepotrebnem možnosti 30 % odsotnosti, nato pa še dodatno manjkate na seminarjih zaradi slabega počutja ipd.*

## Priprava in predstavitev seminarske naloge
Celoten proces zgleda tako:
1. [Izberite izhodiščni članek](izbira-clanka), ki opisuje neko nedavno določeno strukturo – **do roka, navedenega na uvodnem predavanju pri predmetu**.
2. [Pripravite predstavitev](priprava-predstavitve), pri tem pa vam kot osnova služi izbrani članek.
   - Za vizualizacijo struktur obvezno uporabite strukturne podatke iz članka, ki so deponirani v javno dostopnih zbirkah.
   - **Vse slike struktur, ki jih boste prikazali, morate [narisati sami](vizualizacija-struktur)!**
3. [Zahtevane datoteke oddajte](oddaja-datotek) **najkasneje 3 dni pred predstavitvijo** preko povezave v [spletni učilnici UL FKKT](https://ucilnica.fkkt.uni-lj.si).
   - Potrebno je oddati tako predstavitev kot tudi datoteke s sejami, uporabljene za pripravo slik.
4. [Izvedite predstavitev](izvedba-predstavitve) na dogovorjeni datum, pri tem pa za [**najavo in vodenje**](vodenje-predstavitve) poskrbi eden izmed vaših kolegov.

(izbira-clanka)=
### Izbira članka
Osnova za pripravo seminarja je en izhodiščni članek, ki si ga vsak izbere sam. Smernice za izbiro:
- Članek mora biti objavljen v času od **1. junija preteklega koledarskega leta naprej**.
- Članek mora biti **raziskovalen** (*research article*), pregledni članki (*review article*) ne pridejo v poštev.
- Eden izmed glavnih rezultatov članka naj bo **struktura** proteina oz. kompleksa.
- Članke naj bo objavljen v reviji s čim višjim faktorjem vpliva (IF).

Če niste prepričani, da je izbrani članek primeren, se posvetujte s predavateljem.

Izbran članek (naslov članka in povezava do članka v obliki `https://doi.org/DOI`, npr. `https://doi.org/10.1038/s41594-023-01144-y`) čimprej oz. najkasneje do dogovorjenega roka vpišite v razpored seminarjev  – s tem ste si članek "rezervirali".

```{admonition} Namig za izbiro članka
:class: hint
Nekatere revije kot so [Nature Structural & Molecular Biology](https://www.nature.com/nsmb/), [Acta Crystallographica Section D](https://journals.iucr.org/d/) in [Structure](https://www.cell.com/structure/home) so "specializirane" za objavljanje člankov s področja strukturne biologije, odlične in za seminar primerne članke pa seveda najdete tudi v drugih revijah (posebej odmevni so v revijah *ala* [Nature](https://www.nature.com/) in [Science](https://www.science.org/)).

Uporabite lahko tudi **"obratno" iskanje** – najprej izberite strukturo, le-ta pa vas nato pripelje do članka. Pri tem načinu v zbirki PDB izberite napredno iskanje ter ustrezno nastavite leto objave primarnega članka (*Primary Citation Publication Year*), po želji pa dodate (operator `AND`) velikost makromolekule (npr. *Molecular Weight per Deposited Model*) ali druge parametre). Primer iskanja: strukture, pri katerih je bil primarni članek objavljen v letu 2024, molekulska masa deponiranega modela pa je vsaj 500 kDa $\rightarrow$ [klik](https://www.rcsb.org/search?request={"query":{"type":"group","logical_operator":"and","nodes":[{"type":"group","logical_operator":"and","nodes":[{"type":"group","nodes":[{"type":"terminal","service":"text","parameters":{"attribute":"rcsb_primary_citation.year","operator":"equals","negation":false,"value":2024}}],"logical_operator":"and"},{"type":"group","nodes":[{"type":"terminal","service":"text","parameters":{"attribute":"rcsb_entry_info.molecular_weight","operator":"greater_or_equal","negation":false,"value":500}}],"logical_operator":"and"}],"label":"text"}]},"return_type":"entry","request_options":{"paginate":{"start":0,"rows":25},"results_content_type":["experimental"],"sort":[{"sort_by":"score","direction":"desc"}],"scoring_strategy":"combined"}})! Izberite kakšno zanimivo strukturo ter preverite, ali primarna referenca ustreza smernicam.
```

```{admonition} Drugi viri
:class: note
Priporočam, da kot dodatno gradivo pri pripravi seminarske naloge uporabite še druge vire, na primer članke, citirane v izhodiščnem članku. To je pogosto celo nujno – priprava proteina je opisana v drugem članku, morda boste uporabili še kakšno drugo (podobno) strukturo za ilustracijo ipd., ali pa boste želeli razložiti in ponazoriti delovanje uporabljene metode (pri tem lahko kot vir uporabite tudi Wikipedijo).
```

```{admonition} Orodja "umetne inteligence"
:class: attention
Neposredna uporaba besedila, zgeneriranega z orodji "umetne inteligence" kot je ChatGPT, **ni dovoljena**. Potrudite se, da tematiko dejansko preštudirate, saj se bo nepoznavanje pokazalo med diskusijo (če ne že prej).
```

(priprava-predstavitve)=
### Priprava predstavitve
#### Vsebina
Vsebinsko razdelite predstavitev na:
- **uvod**, kjer predstavite proučevano makromolekulo ter problem, ki ga raziskava naslavlja,
- **metodološke pristope** (20–40 % predstavitve), pri tem pa opišite:
  - pripravo vzorca (navedite in razložite morebitne posebnosti, npr. ekspresijski sistem, uporaba fuzijskih proteinov, skrajšanih oblik, izolacija kompleksov in membranskih proteinov, ...),
  - uporabljene metode in sicer tako tiste, ki so bile neposredno uporabljene pri določitvi strukture, kot tudi morebitne druge komplementarne metode (modeliranje, SAXS, ...), pri tem pa poudarite in razložite morebitne posebnosti,
- **rezultate** (30–50 % predstavitve), kjer ne prikažete samo določene strukture ampak tudi razložite, na katera biokemijska/molekularna-biološka vprašanja struktura odgovarja, torej povežite strukturo s funkcijo,
- **kratek zaključek**, kjer povzamete ugotovitve in navedete nova raziskovalna vprašanja, ki jih struktura odpira.

Zgoraj je večkrat uporabljena beseda 'razložite' – pri navajanju metodoloških pristopov, posebnih korakov pri pripravi vzorca ipd. navedite, **zakaj** so bili uporabljeni ravno ti.

```{admonition} Razumevanje tematike
:class: note
Pomembno je, da tematiko, ki jo predstavljate, tudi sami **razumete**, saj boste le tako lahko predstavitev izvedli dobro, na razumljiv način in bodo tudi kolegi od nje nekaj imeli (kar je na koncu koncev tudi eden od namenov seminarja). Če pri razumevanju izbranega članka in metod naletite na težave se obrnite na predavatelja, ki vam bo z veseljem pomagal (ne odlašajte in ne čakajte do zadnjega trenutka!).
```

```{admonition} Uporaba znanj in veščin pri predmetih Biokemijska informatika in Struktura proteinov
:class: hint
Še zdaleč ne bo nič narobe, če pri pripravi predstavitve uporabite znanje in veščine, pridobljene pri Biokemijski informatiki! **Seveda to velja tudi za zanje, posredovano tekom predavanj, vaj in seminarskih delavnic pri predmetu Stuktura proteinov!** Primeri: prikaz posebnosti kot so $\pi$ vijačnica, pakiranje v kristalu, karta (elektronske) gostote, simetrija, ...
```

#### Predstavitev
Pripravite "klasično" predstavitev, kot ste to do sedaj že vajeni, pri tem pa upoštevajte smernice in navodila:
- Za pripravo lahko izberite poljuben program, upoštevajte le praktično omejitev glede [izvedbe predstavitve](izvedba-predstavitve).
- Predstavitev naj bo v slovenskem jeziku, prav tako vso besedilo na drsnicah.
  - Pri iskanju slovenskih ustreznic si pomagajte z [Angleško-slovenskim slovarjem izbranih izrazov iz biokemije in molekularne biologije](https://www.termania.net/slovarji/336/Anglesko_slovenski_slovar_izbranih_izrazov_iz_biokemije_in_molekularne_biologije), ki ga ureja Terminološka komisija [Slovenskega biokemijskega društva](https://sbd.si/). V njem zelo specializiranih izrazov včasih ne boste našli – v teh primerih se posvetujte s predavateljem, na drsnice pa lahko vključite primeren opis v slovenščini ter dodatno izvoren zapis v angleščini.
- Na naslovni drsnici navedite:
  - univerzo in fakulteto, študijsko smer, letnik in predmet,
  - vaše ime in priimek,
  - naslov seminarske naloge (to ni nujno zgolj prevod naslova članka!),
  - referenco na osnovni članek (avtorji, naslov, revija, leto, DOI).
- Drsnice naj vsebujejo **zadostno količino besedila**, da bodo lahko služile kot študijsko gradivo kolegom pri pripravi na izpit. Besedila seveda naj ne bo preveč.
  - Po potrebi lahko kot pomoč kolegom pri študiju vključite dodatno besedilo kot opombe k drsnicam, predstavitev pa nato shranite kot datoteko PDF na način, da bo končna datoteka vsebovala tudi te opombe.
- Vključite **primerno količino slikovnega materiala**, lahko tudi iz druge literature (če ni vzeto iz osnovnega članka obvezno navedite vire ločeno na zadnji drsnici v obliki seznama).
- **Slike iz osnovnega članka in druge literature lahko uporabite le v uvodu in opisu metodoških pristopov** (npr. pri razlagi neke metode), pri rezultatih pa le takrat, ko ne gre neposredno za prikaze struktur, določenih v izbranem članku.
- **Vse prikaze struktur, katerih določitev je opisana v izbranem članku, morate pripraviti sami z uporabo izbranega [orodja za vizualizacijo struktur](vizualizacija-struktur).**
  - **K vsaki tako pripavljeni sliki morate pripisati [ime datoteke s sejo](oddaja-datotek), ki je bila uporabljena za izris.**

```{admonition} Opomba
:class: note
Pripravite samo predstavitev! Datoteke, ki bi vsebovala predvsem besedilo s spremljajočimi slikami (kot ste to delali pri npr. Temeljih biokemije), ni potrebno pripravljati!
```

(vizualizacija-struktur)=
#### Vizualizacija struktur
```{admonition} Zelo pomembno!
:class: danger
**Vse slike struktur, katere določitev je opisana v izbranem članku, morate pripraviti sami z uporabo zbirk strukturnih podatkov in orodij za njihovo vizualizacijo, pri tem pa morate zraven predstavitve oddati točno tiste datoteke s sejami (*session files*), ki so bile uporabljene za pripravo teh slik.**

**Neupoštevanje tega navodila se šteje kot neopravljena seminarska naloga.**
```

V člankih, ki opisujejo določitev neke strukture, so navedene zbirke in kode zapisov (*accession codes*) za dostop do deponiranih podatkov, dotičen članek pa je pogosto t.i. primarna referenca (v zbirki PDB se imenuje *Primary Citation*). Strukturni podatki so torej prosto dostopni (to je tudi pogoj za objavo članka!) in jih lahko uporabite za pripravo slik, ob tem pa obvezno navedite uporabljeno zbirko in kodo zapisa.

Nemogoče je točno predpisati, koliko različnih sej morate pripraviti, pri tem pa se kot različna seja šteje na različen način vizualizirana struktura, interakcije ipd. To je odvisno od samega članka. Naj vas vodi to, da v seminarski nalogi **v obliki slik predstavite vse pomembne vidike strukture, opisane v članku**. Neupoštevanje te smernice lahko negativno vpliva na oceno seminarske naloge.

Za vizualizacijo struktur (slike za predstavitev, priprava datotek s sejami) lahko uporabite naslednje programe: [MolStar](https://molstar.org/), [ChimeraX](https://www.cgl.ucsf.edu/chimerax/), [UCSF Chimera](https://www.cgl.ucsf.edu/chimera/) (pozor, razvoj UCSF Chimera je ustavljen, priporoča se ChimeraX, ki jo v osnovi razvija ista skupina). Razmislite, če želite med predstavitvijo strukture prikazati [interaktivno](interaktivni-prikaz-struktur).

```{admonition} Joj, ne znam uporabljati zbirk in programov!
:class: tip
Zbirka PDB bo na kratko predstavljena med predavanji, podrobneje pa na enem izmed uvodnih seminarjev. Med predavanji bo na kratko predstavljena tudi zbirka EMDB.

Programa za vizualizacijo struktur MolStar in PyMOL bosta predstavljena med uvodnimi seminarji, s programom UCSF Chimera pa se boste spoznali na vajah (ChimeraX ima enako sintakso za izbiro, tudi možnosti za vizualizacijo ipd. so zelo podobne tistim v UCSF Chimera). Če se boste srečali s težavami pri instalaciji katerega od programov poprosite za pomoč predavatelja.

Udeležba na treh uvodnih seminarjih (PDB, MolStar, PyMOL) je obvezna.
```

(oddaja-datotek)=
### Oddaja datotek
Datoteke s predstavitvijo v formatu PDF, izhodiščni članek (prav tako PDF) ter spremljajoče datoteke s sejami do dogovorjenega roka oddajte preko povezave, objavljene v [spletni učilnici UL FKKT](https://ucilnica.fkkt.uni-lj.si).

Datoteke, ki jih boste oddali, **obvezno** poimenujte po ključu `SP-S##-Priimek-oznaka` + ustrezna končnica, ki je lahko:
- `.pdf` (predstavitev, članek),
- `.py` (seja v UCSF Chimera),
- `.cxs` (seja v ChimeraX),
- `.pse` (seja v PyMOL) oz.
- `.molx` (seja v MolStar).

Upoštevajte velike oz. male črke, kot so prikazane v ključu. Operacijski sistemi končnic pogosto ne prikazujejo (čeprav so prisotne v imenih datotek), zato pazite, da jih ne boste po nepotrebnem dodajali sami.

**Ne nalagajte predstavitev v formatu PowerPoint** ipd. temveč jih tam shranite kot datoteko PDF; če želite vključiti komentarje k drsnicam za kolege, izberite ustrezno postavitev (*layout*) ob izvozu.

Pri ključu za poimenovanje je `##` zaporedna številka vaše seminarske naloge, če gre za številko v rangu 1–9 dodajte vodilno ničlo (npr. `9` $\rightarrow$ `09`). Dovoljeni znaki v imenih datotek so le:
- znaki za številke 0–9,
- črke angleške abecede (torej črke osnovne kodne tabele ASCII, šumniki tako odpadejo) ter
- znaka za minus (`-`) in podčrtaj oz. *underscore* (`_`), ki ju lahko uporabljate namesto presledka (slednji ni dovoljen).

```{admonition} Primer poimenovanja
:class: note
Miha Pavšič, katerega seminar ima zaporedno številko 7 in bi predstavljal strukturo s kortaktinom stabiliziranega kompleksa Arp2/3, sje pa je pripravil v MolStar, bi na primer oddal datoteke:
- `SP-S07-Pavsic-Arp23-kortaktin.pdf` (vsebuje predstavitev s slikami, katerim je dodan pripis imen datotek s sejami),
- `SP-S07-Pavsic-Arp23-kortaktin-clanek.pdf` (izhodiščni članek)
- `SP-S07-Pavsic-Arp23-kortaktin_kompleks.molx` (seja za prikaz kompleksa v MolStar),
- `SP-S07-Pavsic-Arp23-kortaktin_hidrofobnost.molx` (prikaz hidrofobnosti površine Arp2/3),
- `SP-S07-Pavsic-Arp23-kortaktin_interakcije.molx` (prikaz medmolekulskih interakcij med Arp2/3 in kortaktinom).
```

(izvedba-predstavitve)=
### Izvedba predstavitve
- Za predstavitev vam bo na voljo računalnik z operacijskim sistemom Microsoft Windows in paketom Microsoft Office (ena izmed novejših verzij), brskalnikom in prikazovalnikom datotek PDF.
  - Po želji lahko prinesete svoj računalnik in pri predstavitvi uporabite poljuben program.
- **Ne berite z drsnic, iz opomb k drsnicam ali drugih beležk.** Besedilo na drsnicah naj vam služi kot oporne točke med predstavitvijo, vsekakor pa naj to ne bo edino besedilo, ki ga na predstavitvi izgovorite.
- Strukture lahko med predstavitvijo [prikažete interaktivno](interaktivni-prikaz-struktur).
- **Upoštevajte časovno omejitev**:
  - predstavitev: 14 min,
  - diskusija: 4 min.

(interaktivni-prikaz-struktur)=
```{admonition} Interaktivni prikaz struktur
:class: note
Če želite med predstavitvijo **interaktivno prikazati strukture na platnu** si pripravite ustrezne seje v [MolStar](https://molstar.org/) in jih pred predstavitvijo odprite v brskalniku. Če želite za prikaz sej uporabiti UCSF Chimera/ChimeraX ali PyMOL morate prinesti svoj računalnik z nainstaliranim ustreznim programom.
```

(vodenje-predstavitve)=
## Vodenje predstavitve
Vsak mora voditi predstavitev enega izmed kolegov. Razpored vodij po seminarskih nalogah bo objavljen v spletni učilnici takrat, ko bo določen datumski razpored vseh predstavitev.

Naloge vodje predstavitve so:
- najava kolega in navedba naslova predstavitve ter vsebine (ena poved),
- skrb za upoštevanje časovne omejitve za predstavitev,
- vodenje diskusije, pri čemer po koncu predstavitve najprej pozove občinstvo k postavljanju vprašanj, na koncu pa tudi sam_a postavi najmanj eno vprašanje.

