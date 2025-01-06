# Analiza struktur idr.

Spodaj je zbranih nekaj uporabnih povezav do zbirk in orodij, ki omogočajo analizo makromolekulskih struktur.

## Sekundarna struktura

Orodja za **pripis (*asignacijo*) sekundarne strukture** posameznim aminokislinskim ostankom na osnovi 3D strukture (pogosto jih najdemo integrirana v programe za vizualizacijo struktur ipd.):
- [STRIDE](https://webclu.bio.wzw.tum.de/cgi-bin/stride/stridecgi.py) (STRuctural IDEntification), ki kombinira vodikove vezi in njihovo energetiko (glede na geometrijo, s prilagoditvami na osnovi empiričnih podatkov iz znanih struktur) s torzijskimi koti ogrodja {cite:p}`Frishman1995aaa`;
- [DSSP](https://pdb-redo.eu/dssp) (Dictionary of Secondary Structure of Proteins), ki, podobno kot STRIDE, kombinira vodikove vezi in njihovo energetiko (glede na geometrijo, na osnovi enačbe za izračun elektrostatskega potenciala) {cite:p}`Kabsch1983aaa`.



## Lastnosti

- [APBS](https://server.poissonboltzmann.org/): Strežnik na osnovi programa Adaptive Poisson-Boltzmann Solver, ki omogoča izračun **elektrostatskih lastnosti** molekul in ob tem upošteva solvatacijo {cite:p}`Jurrus2018aaa`.

## Validacija

- [MolProbity](http://molprobity.biochem.duke.edu/help/about.html): Orodje za **validacijo/evaluacijo makromolekulskih struktur**, določenih z rentgensko difrakcijo, krio-elektronsko mikroskopijo itd., do določene mere deluje tudi za ansamble struktur, določenih z NMR {cite:p}`Williams2018aaa`. Med drugim vam izpiše/izriše podatke o geometriji, neugodnih stikih, rotamerah ter Ramachandranov diagram.

## Oligomeri

- [PDBePISA (Proteins, Interfaces, Structures and Assemblies)](https://www.ebi.ac.uk/msd-srv/prot_int/pistart.html): Orodje za interaktiven prikaz interakcijskih površin med makromolekulami, kar je uporabno pri analizi oligo- ali multi-mernih proteinov. Orodje je izjemno uporabno za analizo vseh možnih simetrij v strukturh, določenih s kristalografijo, kar nam lahko pomaga identificirati biološko relevantne medmolekulske stike v kristalu.

(analiza-podobne-strukture)=
## Podobne strukture

- [Pairwise Structure Alignment](https://www.rcsb.org/alignment): **Poravnava dveh struktur** direktno na strežniku RCSB v povezavi z zbirko PDB, lahko naložimo tudi svoje datoteke. Na voljo več algoritmov (od zaporedja odvisni ter od zaporedja neodvisni).

- [PDBeFold](https://www.ebi.ac.uk/msd-srv/ssm/): Orodje za **iskanje podobnih struktur** preko ujemanja prostorske razporeditve elementov sekundarne strukture (algoritem *secondary structure matching* (SSM)) {cite:p}`Krissinel2004aaa`.

- [DALI](http://ekhidna2.biocenter.helsinki.fi/dali/): Orodje za iskanje podobnih struktur po principu lokalne podobnosti v kontaktih/bližinah aminokislinskih ostankov.

## Razno

- [PDBsum](https://www.ebi.ac.uk/thornton-srv/databases/pdbsum/): **poenostavljen grafični prikaz struktur** v zbirki PDB ter tudi AlphaFold modelov, med drugim izriše topološki diagram, prikaže različne elemente sekundarne strukture, ligande ter interakcije protein:ligand, žepe in tunele v proteinu itd.

## Nukleinske kisline

- [X3DNA-DSSR web](http://wdssr.x3dna.org/): spletna oblika orodja [X3DNA-DSSR](https://x3dna.org/) za **analizo in vizualizacijo strukturnih značilnosti 3D struktur nukleinskih kislin**, med drugim izpiše bazne pare in z njimi povezane parametre, parametre vijačnih delov strukture, nalaganje baz (*stacking*), lasnice, konformacije sladkorjev ...