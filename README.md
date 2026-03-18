# CHEM269Final-RibozymeAnalysis
CHEM 269 Final- Mapping a Mutational Ribozyme Fitness Landscape

The goal of this assignment is to use high-throughput sequencing (HTS) data from a mutational scan of a ribozyme to identify which nucleotides are functionally important and which positions covary with each other. Students will analyze mutants of a ribozyme (and their associated activity or enrichment) to detect conserved positions, epistatic interactions, and covarying base pairs that likely contribute to the ribozyme’s secondary or tertiary structure. Biologically, ribozymes are RNA molecules that catalyze chemical reactions, and their function depends sensitively on specific nucleotides and base pairs. Students can map a functional landscape of the ribozyme and infer structural and mechanistic constraints. This connects HTS data analysis, RNA structure, and evolutionary/functional inference.

I chose this problem because it sits at the intersection of RNA biochemistry, evolution, and quantitative data analysis, and it is directly inspired by modern experimental approaches to mapping sequence-function relationships. The assignment lets students work with realistic, noisy HTS data while still having a clear biological interpretation: understanding how a ribozyme sequence encodes its structure and activity. I am also personally interested in how covariation and mutational effects can reveal “hidden” structural features without directly solving a 3D structure. 

Primary dataset: Kobori & Yokobayashi (2016), Angew. Chem. Int. Ed. - High-throughput mutational scan of Osa-1-4 twister ribozyme (https://yokobayashilab.net/data.html)
​

Complete matrix of relative activities for ALL single + double nucleotide mutants (48 positions mutated)

Format: Symmetric Excel matrix where rows/columns = mutant labels ("A7U", "C15G"), values = relative activity (RA)

WT Sequence: 5'CCGCCUAACACTGCCAATGCCGGTCCCAAGCCCGGATAAAAGTGGAGGGGGCGG 3'

Secondary structure: Image from paper that data set was chosen from

1. DATA → Parse mutant labels → Long-form DataFrame (variant_id, pos1, pos2, RA)
2. SINGLE MUTANTS → Per-position: mean_RA, min_RA, sensitivity = 1-mean_RA
3. PURINE/PYRIMIDINE → Classify mutations → avg_purine_RA vs avg_pyrimidine_RA per position
4. EPISTASIS → For each (i,j): expected_RA = mean_RA[i] × mean_RA[j]
                      epistasis = observed_RA - expected_RA
                      → Position-pair matrix → Heatmap
Ran in Colab, I deleted the first two rows of the excel files to make file analysis easier. Actual file I processed and uploaded is in this repo. 

   

