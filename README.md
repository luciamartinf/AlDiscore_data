# AlDiscore_data
Collection of sequence sets, published MSAs and generated alignments used in the article [Quantifying and Predicting the Difficulty of Multiple Sequence Alignment with AlDiScore](https://www.biorxiv.org/content/10.64898/2026.05.29.727837v1.full.pdf)

## Databases

| Source              | # Sets | Description                                                                              | Reference                                      |
| ------------------- | ------ | ---------------------------------------------------------------------------------------- | ---------------------------------------------- |
|** HOMSTRAD **           | 193    | Data from HOMSTRAD, used for benchmarking in Formatt.                                    | Daniels et al. (2012), Stebbings et al. (2004) |
| **SABmark-Twilight   ** | 158    | Data from the Twilight subset of SABmark, used for benchmarking in Formatt.              | Daniels et al. (2012), Van Walle et al. (2005) |
| **SABRE**               | 272    | Compiled by Robert Edgar. Consistent multiple alignments constructed from SABMARK v1.65. | Edgar (benchmark), Van Walle et al. (2005)     |
| **BAliBASEv3**          | 386    | Compiled by Robert Edgar. BAliBASE v3.                                                   | Edgar (benchmark), Thompson et al. (2005)      |
| **PREFABv4**            | 1665   | Compiled by Robert Edgar. PREFAB v4.                                                     | Edgar (benchmark), Edgar (2004)                |
| **OXBench**             | 274    | Compiled by Robert Edgar. OXBench.                                                       | Edgar (benchmark), Raghava et al. (2003)       |
| **Arthropods-P450s**    | 281    | Cytochrome P450 gene family (CYP genes) of arthropods.                                   | Charamis et al. (2025)                         |
| **TreeBASEv1 - AA**     | 622    | Sampled from TreeBASE.                                                                   | Piel et al. (2000)                             |
| **TreeBASEv1 - DNA**    | 2497   | Sampled from TreeBASE.                                                                   | Piel et al. (2000)                             |
| **BAliBASE (mdsa_all)** | 498    | Back-translated AA datasets using tBLASTn hits (E-value > 0.001).                        | Carroll et al. (2007)                               |
| **OXBench (mdsa_all)**  | 276    | Back-translated AA datasets using tBLASTn hits (E-value > 0.001).                        | Carroll et al. (2007)                               |
| **SMART (mdsa_all)**    | 690    | Back-translated AA datasets using tBLASTn hits (E-value > 0.001).                        | Carroll et al. (2007)                                 |
| **RobLanf**             | 1839   | Single-locus DNA alignments.                                                             | GitHub: [roblanf/BenchmarkAlignments](https://github.com/roblanf/BenchmarkAlignments)            |
| **PANDIT - AA**             | 6447   | Protein sequence from the Pfam-A database v17                                                             | Whelan et al. (2006)            |
| **PANDIT - DNA**             | 6447   | Nucleotide sequence derived from the AA sequences.                                                             | Whelan et al. (2006)         |


## Structure 

Each database follows the same directory structure. 

```text
work_dir/
└── database/
    └── dataset/
        ├── ClustalO/
        │   ├── done
        │   ├── ensemble.log
        │   └── msa.[0-7].fasta
        │
        ├── MAFFT_FFT-NS-2/
        │   ├── ...
        │   └── msa.[0-7].fasta
        │
        ├── MAFFT_G-INS-i/
        │   ├── ...
        │   └── msa.[0-7].fasta
        │
        ├── MAFFT_L-INS-i/
        │   ├── ...
        │   └── msa.[0-7].fasta
        │
        ├── Muscle3/
        │   ├── ...
        │   └── msa.[0-7].fasta
        │
        ├── Muscle5/
        │   ├── ...
        │   └── msa.[0-7].fasta
        │
        ├── ensemble/
        │   ├── ClustalO.[0-7].fasta
        │   ├── MAFFT_FFT-NS-2.[0-7].fasta
        │   ├── MAFFT_G-INS-i.[0-7].fasta
        │   ├── MAFFT_L-INS-i.[0-7].fasta
        │   ├── Muscle3.[0-7].fasta
        │   └── Muscle5.[0-7].fasta
        │
        ├── reference.fasta
        ├── sequences.fasta
        └── stats.parquet
```


## MSA ensemble

We define an MSA ensemble as a collection of alternative MSAs inferred on the same unaligned sequence set via distinct alignment methods and parameter settings. For each tool, we describe the parameters used to generate 8 different MSAs for each tool [0-7] using [ensemblify](https://github.com/MaBody/ensemblify/tree/main)

### ClustalO v1.2.4

| Parameter                  | Value        | Reference             |
| :------------------------- | :----------- | :-------------------- |
| `max-guidetree-iterations` | [1, 2, 3, 4] | Sievers et al. (2011) |
| `max-hmm-iterations`       | [1, 2]       |                       |

### MAFFT v7.525 (FFT-NS-2, G-INS-i, L-INS-i)

| Parameter | Value                            | Reference           |
| :-------- | :------------------------------- | :------------------ |
| `op`      | [1.1475, 1.4025, 1.6575, 1.9125] | Katoh et al. (2002) |
| `ep`      | [0.0922, 0.1538]                 |                     |

### Muscle v3.8.31

| Parameter  | Value                | Reference                  |
| :--------- | :------------------- | :------------------------- |
| `weight1`  | ["clustalw", "none"] | Edgar and Batzoglou (2006) |
| `weight2`  | ["clustalw", "none"] |                            |
| `objscore` | ["spf", "xp"]        |                            |

### Muscle v5.1

| Parameter    | Value | Reference    |
| :----------- | :---- | :----------- |
| `replicates` | 2     | Edgar (2022) |
| `stratified` |       |              |


## References

Carroll H, Beckstead W, O’Connor T, Ebbert M, Clement M, Snell Q, McClellan D. 2007. DNA reference alignment benchmarks based on tertiary structure of encoded proteins. Bioinformatics 23:2648–2649.

Charamis J, Dermauw W, Van Leeuwen T, Vontas J, Feyereisen R. 2025. The arthropod P450 Enchiridion: An integrated web resource for research on P450s. Insect Biochem Mol Biol 183:104377.

Daniels NM, Nadimpalli S, Cowen LJ. 2012. Formatt: Correcting protein multiple structural alignments by incorporating sequence alignment. BMC Bioinformatics 13:259.

Edgar RC, Batzoglou S. 2006. Multiple sequence alignment. Curr Opin Struct Biol 16:368–373. 

Edgar RC. 2004. MUSCLE: multiple sequence alignment with high accuracy and high throughput. Nucleic Acids Res 32:1792–1797.

Edgar RC. 2022. Muscle5: High-accuracy alignment ensembles enable unbiased assessments of sequencehomology and phylogeny. Nat Commun 13:6968. 

Edgar RC. n.d. Benchmark collection: BALIBASE, PREFAB, OXBENCH, SABRE.

Katoh K, Misawa K, Kuma K, Miyata T. 2002. MAFFT: a novel method for rapid multiple sequence alignment based on fast Fourier transform. Nucleic Acids Res 30:3059–3066. 

Raghava G, Searle SM, Audley PC, Barber JD, Barton GJ. 2003. OXBench: a benchmark for evaluation of protein multiple sequence alignment accuracy. BMC Bioinformatics 4:47

Sievers F, Wilm A, Dineen D, Gibson TJ, Karplus K, Li W, Lopez R, McWilliam H, Remmert M, Söding J, et al. 2011. Fast, scalable generation of high-quality protein multiple sequence alignments using Clustal Omega. Mol Syst Biol 7.

Stebbings LA, Mizuguchi K. 2004. HOMSTRAD: recent developments of the homologous protein structure alignment database. Nucleic Acids Res 32:D203–D207.

Thompson JD, Koehl P, Ripp R, Poch O. 2005. BAliBASE 3.0: latest developments of the multiple sequence alignment benchmark. Proteins Struct. Funct. Bioinf. 61:127–136.

Van Walle I, Lasters I, Wyns L. 2005. SABmark—a benchmark for sequence alignment that covers the entire known fold space. Bioinformatics 21:1267–1268.

Whelan S, de Bakker PIW, Quevillon E, Rodriguez N, Goldman N. 2006. PANDIT: an evolution-centric database of protein and associated nucleotide domains with inferred trees. Nucleic Acids Res 34:D327–D331.
