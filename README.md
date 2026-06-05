# AlDiscore_data
Collection of sequence sets, published MSAs and generated alignments used in the article [Quantifying and Predicting the Difficulty of Multiple Sequence Alignment with AlDiScore](https://www.biorxiv.org/content/10.64898/2026.05.29.727837v1.full.pdf)

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

We define an MSA ensemble as a collection of alternative MSAs inferred on the same unaligned sequence set via distinct alignment methods and parameter settings. The following table describes the alignment tools and parameter settings used. 

| Parameter                                     | Value                            | Reference                  |
| --------------------------------------------- | -------------------------------- | -------------------------- |
| **ClustalO v1.2.4**                                                                                    |
| `max-guidetree-iterations`                    | [1, 2, 3, 4]                     | Sievers et al. (2011)      |
| `max-hmm-iterations`                          | [1, 2]                           |                            |
| **MAFFT v7.525 (FFT-NS-2, G-INS-i, L-INS-i)**                                                        |
| `op`                                          | [1.1475, 1.4025, 1.6575, 1.9125] | Katoh et al. (2002)        |
| `ep`                                          | [0.0922, 0.1538]                 |                            |
| **Muscle v3.8.31**                                                                                          |
| `weight1`                                     | ["clustalw", "none"]             | Edgar and Batzoglou (2006) |
| `weight2`                                     | ["clustalw", "none"]             |                            |
| `objscore`                                    | ["spf", "xp"]                    |                            |
| **Muscle v5.1**                                                                                            |
| `replicates`                                  | 2                                | Edgar (2022)               |
| `stratified`                                  |                                  |                            |

