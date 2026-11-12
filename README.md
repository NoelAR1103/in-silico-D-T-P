# In-Silico Drug Target Identification & Structure-Based Lead Optimization against *Acinetobacter baumannii*

An end-to-end computational biology and structure-based drug discovery pipeline built in Python (`Biopython`, `NCBI BLAST+`, `AutoDock Vina`, `RDKit`, `py3Dmol`, `Pandas`) to identify novel, non-homologous, pan-spectrum antibacterial drug targets and optimize small-molecule inhibitors against WHO Priority Pathogen ***Acinetobacter baumannii***.

## Pipeline Overview & Key Findings

1. **Subtractive Genomics Filtering (`1,845` $\rightarrow$ `29` Unique Targets)**
   - **Proteome Retrieval:** `1,845` reviewed *A. baumannii* proteins retrieved from UniProt.
   - **Length & Redundancy Filtering:** `1,676` proteins ($\ge 100$ aa) deduplicated to `766` non-redundant sequences.
   - **Host Non-Homology (`BLASTP`, $E \le 10^{-4}$):** `398` human-homologous proteins eliminated to prevent off-target toxicity, leaving `368` pathogen-specific proteins.
   - **Essentiality & Gene Collapse:** `56` essential survival hits collapsed to `29` unique essential gene targets across peptidoglycan synthesis, DNA replication, lipid A biosynthesis, and ribosomal translation.

2. **Target Prioritization & Pan-Pathogen Conservation**
   - **`MurG` (`UniProt: A3M9Y1`, `PDB: 7D1I`)** emerged as the top lead: biochemically stable (Instability Index `39.12`), structurally resolved, and **conserved across *A. baumannii*, *K. pneumoniae*, and *S. aureus* (MRSA)**.

3. **Virtual Screening, ADMET & Rational SAR Optimization**
   - Docked reference substrates and inhibitors into *A. baumannii* `MurG` Chain A (`AutoDock Vina`) and evaluated Lipinski/Veber drug-likeness (`RDKit`).
   - Rational SAR modification of the **Murgocil** scaffold (`-7.330 kcal/mol`, `cLogP = 5.02`, 1 Lipinski violation) yielded **`Analog-3` (Fluoro-Carboxamide Lead)** with improved binding affinity (**`-7.685 kcal/mol`**), balanced lipophilicity (**`cLogP = 3.30`**), and **0 Lipinski violations**.

![Subtractive Genomics Funnel](figures/subtractive_genomics_summary.png)
![SAR Lead Structures](figures/sar_lead_structures.png)
