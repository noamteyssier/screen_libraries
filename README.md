# screen_libraries

These are the H1-7 CRISPR Screening Libraries.

They were processed using [`fxtools`](https://noamteyssier.github.io/fxtools/)
to make compatible for sgRNA counts mapping with [`sgcount`](https://noamteyssier.github.io/sgcount/).

## Pipeline

Each library was mapped the following way - using H1 as an example:

```bash

# convert to upper case
fxtools upper -i h1_lib.fa -o h1_lib.upper.fa

# remove duplicate sgRNAs
fxtools unique -i h1_lib.upper.fa -o h1_lib.unique.fa

# extract variable region from library (remove adapters)
fxtools extract-variable -i h1_lib.unique.fa -o h1_lib.var.fa -z 0.5

# create a gene -> sgRNA mapping
fxtools sgrna-table -i h1_lib.var.fa -o h1_lib.g2s.txt
```
