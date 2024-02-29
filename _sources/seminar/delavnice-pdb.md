# Delavnica: PDB

## Namen

Namen delavnice je seznaniti se z najpomembnejšimi zbirkami struktur v smislu dostopa, iskanja in prikaza podatkov.

## Potrebščine

Za izvedbo potrebujete:
- spletni brskalnik (najbolje na namiznem ali prenosnem računalniku, pogojno na tablici, na slednji je sicer malce težje manipulirati z modeli struktur; mobilni telefon ni primeren),
- povezavo v splet.

## Shema delavnice

Na delavnici bodo predstavljeni spodaj navedeni vidiki [zbirke PDB ter nekaterih drugih zbirk](../orodjarna/zbirke-eksperimentalne.md) ter [zbirk modelov](../orodjarna/modeli.md).  Delavnico ste uspešno opravili če lahko za vsako od navedenih točk rečete "Vem, za kaj se gre in znam uporabiti!".

### Splošno

- **RCSB PDB**
  - [ ] "kje je kaj" na osnovni strani: [https://www.rcsb.org/](https://www.rcsb.org/)
  - [ ] brskanje po zbirki (pripisi): [https://www.rcsb.org/search/browse/atc](https://www.rcsb.org/search/browse/atc)
    - GO termini (biološki proces, celična komponenta, molekulska funkcija)
    - klasifikacija struktur (CATH, SCOP)
    - klasifikacija encimov (Enzyme Classification)
    - druge klasifikacije
  - [ ] osnovno iskanje
  - [ ] filtriranje zadetkov (metoda, ločljivost, ...)
  - [ ] napredno iskanje: [https://www.rcsb.org/search/advanced](https://www.rcsb.org/search/advanced)
	- atributi strukture
	- atributi majhnih molekul
	- podobnost po zaporedju/strukturi
	- strukturni motivi
	- kemijska podobnost
- **PDBe**
  - [ ] "kje je kaj"" na osnovni strani: [https://www.ebi.ac.uk/pdbe/](https://www.ebi.ac.uk/pdbe/)
  - [ ] osnovno in napredno iskanje: [https://www.ebi.ac.uk/pdbe/entry/search/index/](https://www.ebi.ac.uk/pdbe/entry/search/index/)
- **AlphaFold Protein Structure Database**: [https://alphafold.ebi.ac.uk/](https://alphafold.ebi.ac.uk/)
  - [ ] iskanje
  - [ ] struktura zapisa
  - (podrobneje o tem pri [Biokemijski informatiki](https://mpavsic.github.io/biokeminfo/naslovnica))
- **druge zbirke: BMRB, EMDB** → podrobnejša obravnava pri predavanjih (tema: določanje 3D strukture)

### Primeri zapisov v zbirki RCSB PDB in drugih zbirkah

- **splošno** (na primeru PDB ID 2OHA: [https://www.rcsb.org/structure/2OHA](https://www.rcsb.org/structure/2OHA)):
  - [ ] izvorni organizem
  - [ ] organizem, v katerem je protein bil rekombinantno pripravljen
  - [ ] morebitne mutacije glede na zaporedje divjega tipa
  - [ ] makromolekule v strukturi:
    - dolžina, aminokislinsko zaporedje, oznaka verige
  - [ ] majhne molekule v strukturi:
    - ime, struktura
    - 3D interakcije
  - [ ] pripisi (npr. klasifikacija CATH, SCOP): [https://www.rcsb.org/annotations/2oha](https://www.rcsb.org/annotations/2oha)
  - [ ] ogled zaporedja in pripisov v zaporedju: [https://www.rcsb.org/sequence/2OHA](https://www.rcsb.org/sequence/2OHA)
  - [ ] genomski podatki: [https://www.rcsb.org/genome/2OHA](https://www.rcsb.org/genome/2OHA)
  - [ ] vizualizacija strukture: [https://www.rcsb.org/3d-view/2oha](https://www.rcsb.org/3d-view/2oha)
  - [ ] kartiranje pripisov na strukturo: [https://www.rcsb.org/3d-sequence/2OHA?assemblyId=1](https://www.rcsb.org/3d-sequence/2OHA?assemblyId=1)
  - [ ] validacijsko poročilo:
    - podrobno poročilo (PDF): [https://files.rcsb.org/pub/pdb/validation_reports/oh/2oha/2oha_full_validation.pdf](https://files.rcsb.org/pub/pdb/validation_reports/oh/2oha/2oha_full_validation.pdf)
    - kartiranje na strukturo: [https://www.rcsb.org/3d-view/2OHA?preset=validationReport](https://www.rcsb.org/3d-view/2OHA?preset=validationReport)
  - [ ] primerjava z zapisom za isto strukturo v zbirki PDBe: [https://www.ebi.ac.uk/pdbe/entry/pdb/2oha](https://www.ebi.ac.uk/pdbe/entry/pdb/2oha)
- **struktura, določena z X-žarkovno kristalografijo** (na primeru PDB ID [1DCS](https://www.rcsb.org/structure/1DCS)):
  - [ ] razlika med deponiranim modelom strukture in biološko relevantno oligomerno obliko
  - [ ] elektronska gostota: [https://www.rcsb.org/3d-view/1DCS](https://www.rcsb.org/3d-view/1DCS)
  - [ ] podatki o eksperimentu: [https://www.rcsb.org/experimental/1dcs](https://www.rcsb.org/experimental/1dcs)
- **struktura, določena z NMR spektroskopijo** (na primeru PDB ID [7D2O](https://www.rcsb.org/structure/7D2O)):
  - [ ] osnovni podatki o eksperimentu ter primerjava s strukturo, določeno z X-žarkovno kristalografijo
  - [ ] ansambel modelov
  - [ ] prikaz posameznih modelov: [https://www.rcsb.org/3d-view/7D2O](https://www.rcsb.org/3d-view/7D2O)
  - [ ] podatki o eksperimentu: [https://www.rcsb.org/experimental/7D2O](https://www.rcsb.org/experimental/7D2O)
  - [ ] povezava na BMRB: [https://bmrb.io/data_library/generate_summary.php?bmrbId=36385](https://bmrb.io/data_library/generate_summary.php?bmrbId=36385)
- **struktura, določena s krio-elektronsko mikroskopijo** (na primeru PDB ID [2J9I](https://www.rcsb.org/structure/2J9I)):
  - [ ] osnovni podatki o eksperimentu ter primerjava s strukturo, določeno z X-žarkovno kristalografijo
  - [ ] podatki o eksperimentu: [https://www.rcsb.org/experimental/2J9I](https://www.rcsb.org/experimental/2J9I)
  - [ ] povezava na EMDB: [https://www.ebi.ac.uk/emdb/EMD-1290](https://www.ebi.ac.uk/emdb/EMD-1290)
  - [ ] prikaz gostote: [https://www.rcsb.org/3d-view/2J9I](https://www.rcsb.org/3d-view/2J9I)