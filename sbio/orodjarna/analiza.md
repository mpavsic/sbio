# Analiza struktur idr.

Spodaj je zbranih nekaj uporabnih povezav do zbirk in orodij, ki omogočajo analizo makromolekulskih struktur.

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