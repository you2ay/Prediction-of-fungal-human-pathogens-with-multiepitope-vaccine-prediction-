In Silico Multi-Epitope Vaccine Design Against Human Fungal Pathogens

**Author:** Youssef Ayman Ibrahim  
**Degree:** B.Sc. Applied Biotechnology — Ain Shams University  
**Grade:** A | **GPA:** 3.843 / 4.0  
**Year:** 2024  

[![Status](https://img.shields.io/badge/Status-Completed-brightgreen)]()
[![Approach](https://img.shields.io/badge/Approach-In%20Silico-blue)]()
[![Domain](https://img.shields.io/badge/Domain-Immunoinformatics-purple)]()
[![Scope](https://img.shields.io/badge/Organisms-14%20WHO%20Priority-red)]()

📋 Table of Contents

1. [Project Overview](#overview)
2. [Background](#background)
3. [Target Pathogens](#pathogens)
4. [Methodology Pipeline](#methodology)
5. [Secretome Results](#secretome)
6. [Clustering Results](#clustering)
7. [Novel Virulence Factors](#virulence)
8. [Tools and Databases](#tools)
9. [Repository Structure](#structure)
10. [Publications](#publications)

Project Overview <a name="overview"></a>

This project presents a **comprehensive in silico pipeline**
for the design of a multi-epitope vaccine candidate targeting
**14 WHO-priority human fungal pathogens** simultaneously.

The pipeline integrates:
- **Secretome prediction** to identify fungal effector proteins
- **Orthologous clustering** across 14 organisms
- **Conservation analysis** to identify cross-species targets
- **Immunoinformatics** for epitope prediction and vaccine construct design
- **Structural biology** for 3D modeling and validation
- **Comparative proteomics** for novel virulence factor discovery

> This project introduces a **novel deep learning-assisted pipeline**
> for in silico vaccine design based on secretome analysis and
> structural comparative proteomics.
>
> Background <a name="background"></a>

Fungal infections represent a growing global health crisis:

- **~1 billion people** affected by fungal infections annually
- **>300 million** severe fungal infections per year globally
- **~1.6 million deaths** attributed to fungal infections annually
- **\$7.2 billion** spent on treatment in the USA alone (2017)
- Increasing antifungal drug resistance across multiple species
- Climate change driving emergence of new pathogenic fungal species
- **No approved broad-spectrum multi-pathogen fungal vaccine exists**

The WHO classified fungal pathogens into **critical, high, and moderate
priority groups** in 2022 — the first time fungi received this level
of global health attention.

Target Pathogens <a name="pathogens"></a>

Selection criteria:
- WHO 2022 priority classification
- Human respiratory system involvement
- Clinical relevance post-COVID-19

|
 Pathogen 
|
 WHO Priority 
|
 Respiratory Involvement 
|
|
---
|
---
|
---
|
|
*
Candida auris
*
|
 🔴 Critical 
|
 Secondary (skin → systemic) 
|
|
*
Aspergillus fumigatus
*
|
 🔴 Critical 
|
 Direct respiratory 
|
|
*
Cryptococcus neoformans
*
|
 🔴 Critical 
|
 Primary (inhalation) 
|
|
*
Nakaseomyces glabratus
*
|
 🔴 Critical 
|
 Secondary (mucosal) 
|
|
*
Histoplasma capsulatum
*
|
 🟠 High 
|
 Primary (inhalation) 
|
|
*
Mucor circinelloides
*
|
 🟠 High 
|
 Secondary (skin) 
|
|
*
Lomentospora prolificans
*
|
 🟠 High 
|
 Primary (inhalation) 
|
|
*
Coccidioides immitis
*
|
 🟠 High 
|
 Primary (inhalation) 
|
|
*
Talaromyces marneffei
*
|
 🟠 High 
|
 Direct respiratory 
|
|
*
Paracoccidioides brasiliensis
*
|
 🟡 Moderate 
|
 Primary (inhalation) 
|
|
*
Blastomyces dermatitidis
*
|
 🟡 Moderate 
|
 Primary (inhalation) 
|
|
*
Sporothrix schenckii
*
|
 🟡 Moderate 
|
 Secondary (skin) 
|
|
*
Scedosporium apiospermum
*
|
 🟡 Moderate 
|
 Direct respiratory 
|
|
*
Pneumocystis jirovecii
*
|
 🟡 Moderate 
|
 Primary (inhalation) 
|

---
Methodology Pipeline <a name="methodology"></a>

### Phase 1 — Proteome and Secretome Analysis

**Step 1 — Proteome Retrieval**
- Source: Ensembl Fungi Database (fungi.ensembl.org)
- Retrieved complete proteomes for all 14 organisms
- Total proteins retrieved: 114,615

**Step 2 — Secretome Prediction**
- SignalP 5.0 → signal peptide detection
- DeepTMHMM v1.0.24 → transmembrane helix exclusion
- DeepLoc 2.0 → subcellular localization confirmation
- Logic: signal peptide present + no TM helix = secreted protein
- Result: 6,281 secreted proteins identified

---

### Phase 2 — Clustering and Conservation

**Step 3 — Orthologous Clustering**
- OrthoMCL (Markov Clustering Algorithm)
- Selection: clusters present in more than 5 organisms
- Clustal Omega MSA — conservation threshold: 5 amino acids minimum

**Step 4 — Human Homology Exclusion**
- BLASTp vs Homo sapiens (taxid: 9606)
- Threshold: less than 37% identity = non-homologous
- Ensures no cross-reactivity with human proteins

**Step 5 — Structural Conservation Confirmation**
- ConservFold web server
- Maps conserved regions to selected peptides

---

### Phase 3 — Pre-Vaccine Screening

**Step 6 — Multi-Criteria Protein Screening**

Each candidate evaluated for:
- Antigenicity → VaxiJen v2.0 (threshold: 0.5 or above)
- Allergenicity → AllerTOP v2.0 (non-allergens only)
- Toxicity → ToxinPred2 (non-toxic only)
- Human homology → BLASTp (less than 37% identity)

---

### Phase 4 — Epitope Prediction

**Step 7 — B-Cell Epitope Prediction**
- BepiPred-3.0
- Mode: higher confidence (top 20%)

**Step 8 — MHC-I T-Cell Epitope Prediction**
- IEDB + NetMHCpan v4.1
- 27 most frequent A and B alleles
- Peptide lengths: 8-mer and 9-mer

**Step 9 — MHC-II T-Cell Epitope Prediction**
- IEDB + NetMHCpan v4.1 + Consensus v2.22
- 26 most frequent pre-selected alleles
- All DQ, DP, DR alleles included
- Peptide length: 15-mer

---

### Phase 5 — Vaccine Construct Design

**Step 10 — Multi-Epitope Construction**

Construct components:
- Adjuvant: RS09 (N-terminal, EAAAK linker)
- CTL epitope linker: AAY
- HTL epitope linker: GPGPG
- LBL epitope linker: KK
- Stability: 60 alanine residues added
- Final construct length: 255 amino acids

**Step 11 — Physicochemical Characterization**
- ProtParam (ExPASy) → MW, pI, half-life, stability
- Protein-sol → solubility prediction (threshold: 0.45)

**Step 12 — Secondary Structure Prediction**
- PSIPRED (primary prediction)
- NetSurf 2.0 (confirmation)

---

### Phase 6 — Structural Modeling

**Step 13 — Tertiary Structure Prediction**
- AlphaFold2 / ColabFold2
- Selection: pTM above 0.5, pLDDT above 70%

**Step 14 — Structure Refinement**
- GalaxyRefine server
- 10 refined models generated and compared

**Step 15 — Structure Validation**
- PDBsum (Ramachandran plot analysis)
- Quality factor and error plot assessment

---

### Phase 7 — Advanced Analysis

**Step 16 — Discontinuous B-Cell Epitope Prediction**
- ElliPro (IEDB server)
- Input: refined 3D vaccine model

**Step 17 — Disulfide Engineering**
- Disulfide by Design 2.13
- Criteria: chi3 angle between -87 and +97 degrees
- Energy threshold: below 2.2 kcal/mol

**Step 18 — Molecular Docking**
- ClusPro 2.0
- Receptor: TLR-4 (PDB ID: 4G8A)
- LigPlot for bond diagram generation

**Step 19 — Immune Response Simulation**
- C-ImmSim server
- 3 injections at weeks 0, 4, and 8

---

### Phase 8 — Expression Optimization

**Step 20 — Codon Optimization**
- VectorBuilder web server
- Host: E. coli strain K12
- Parameters: CAI score and GC content

**Step 21 — In Silico Cloning**
- SnapGene 7.0
- Vector: pET28a (+)
- Restriction sites: HindIII and BamHI

---

### Phase 9 — Comparative Proteomics

**Step 22 — Full Secretome Structure Prediction**
- ColabFold2 batch prediction
- All 6,281 secretome proteins modeled
- Signal peptides removed before modeling

**Step 23 — Sequential Structural Comparison**
- Level 1: BLASTP (sequence to sequence)
- Level 2: HHblits (sequence to profile)
- Level 3: HHsearch (profile to profile)
- Level 4: TM-align via Rupee (structure to structure)
- Databases: SCOPe v2.07, CATH v4.3.0, PDB chains
- InterPro for domain characterization

**Step 24 — Virulence Factor Prediction**
- PHI-base 4.15 database
- DeepLoc 2.0 confirmation for unidentified proteins

---
 Secretome Analysis Results <a name="secretome"></a>

|
 Organism 
|
 Secretome 
|
 Proteome 
|
 Percentage 
|
|
---
|
---
|
---
|
---
|
|
*
Mucor circinelloides
*
|
 545 
|
 12,226 
|
 4.46% 
|
|
*
Candida auris
*
|
 227 
|
 3,340 
|
 6.80% 
|
|
*
Aspergillus fumigatus
*
|
 666 
|
 6,660 
|
 10.00% 
|
|
*
Cryptococcus neoformans
*
|
 247 
|
 6,900 
|
 3.58% 
|
|
*
Histoplasma capsulatum
*
|
 357 
|
 9,254 
|
 3.86% 
|
|
*
Paracoccidioides brasiliensis
*
|
 263 
|
 8,326 
|
 3.16% 
|
|
*
Scedosporium apiospermum
*
|
 726 
|
 8,375 
|
 8.67% 
|
|
*
Blastomyces dermatitidis
*
|
 399 
|
 11,443 
|
 3.49% 
|
|
*
Sporothrix schenckii
*
|
 620 
|
 16,008 
|
 3.87% 
|
|
*
Talaromyces marneffei
*
|
 709 
|
 4,578 
|
 15.49% 
|
|
*
Nakaseomyces glabratus
*
|
 269 
|
 5,293 
|
 5.08% 
|
|
*
Lomentospora prolificans
*
|
 772 
|
 8,558 
|
 9.02% 
|
|
*
Coccidioides immitis
*
|
 381 
|
 9,908 
|
 3.85% 
|
|
*
Pneumocystis jirovecii
*
|
 100 
|
 3,761 
|
 2.66% 
|
|
**
TOTAL
**
|
**
6,281
**
|
**
114,615
**
|
**
5.48% avg
**
|

---
Clustering Results <a name="clustering"></a>
114,615 total proteins
↓ Secretome prediction
6,281 secreted proteins
↓ OrthoMCL clustering (more than 5 organisms)
100 clusters
↓ Clustal Omega MSA (5 AA conservation threshold)
16 conserved clusters
↓ BLASTp vs Homo sapiens (less than 37% identity)
16 non-homologous clusters
↓ Pre-vaccine screening
4 FINAL CLUSTERS selected for vaccine construction

🔍 Novel Virulence Factors <a name="virulence"></a>

Comparison against PHI-base 4.15 identified
**20 proteins** with no homology to known virulence factors.

| Organism | Novel Proteins |
|---|---|
| *Mucor circinelloides* | 5 |
| *Aspergillus fumigatus* | 4 |
| *Lomentospora prolificans* | 3 |
| *Nakaseomyces glabratus* | 3 |
| *Paracoccidioides brasiliensis* | 2 |
| *Sporothrix schenckii* | 2 |
| *Cryptococcus neoformans* | 1 |
| **Total** | **20** |

Phylogenetic analysis revealed evolutionary relationships
between these novel proteins across species — suggesting
previously undescribed fungal virulence factor families
with potential as future drug targets or vaccine antigens.

---

## 🛠️ Tools and Databases <a name="tools"></a>

**Databases:**
Ensembl Fungi | NCBI | UniProt | PDB | IEDB | PHI-base 4.15 | SCOPe v2.07 | CATH v4.3.0 | InterPro

**Secretome Prediction:**
SignalP 5.0 | DeepTMHMM v1.0.24 | DeepLoc 2.0

**Clustering and Alignment:**
OrthoMCL | Clustal Omega | BLASTP | HHblits | HHsearch | TM-align | Rupee

**Epitope Prediction:**
BepiPred-3.0 | IEDB | NetMHCpan v4.1 | Consensus v2.22 | VaxiJen v2.0 | AllerTOP v2.0 | ToxinPred2 | ElliPro | ConservFold

**Structure Prediction:**
AlphaFold2 | ColabFold2 | GalaxyRefine | PDBsum | PSIPRED | NetSurf 2.0 | PyMOL | LigPlot

**Docking and Simulation:**
ClusPro 2.0 | C-ImmSim | Disulfide by Design 2.13

**Expression:**
ProtParam | Protein-sol | VectorBuilder | SnapGene 7.0

---

## 📁 Repository Structure <a name="structure"></a>
fungal-multiepitope-vaccine-design/
├── README.md
├── 01_secretome_prediction/
├── 02_clustering_analysis/
├── 03_epitope_prediction/
├── 04_vaccine_construct_design/
├── 05_structure_prediction/
├── 06_comparative_proteomics/
├── 07_novel_virulence_factors/
└── figures/

Publications <a name="publications"></a>

**First Author — Book Chapter:**
Youssef Ayman Ibrahim et al.
*Neurodegeneration, Microglia, and Neuroinflammation*
Essential Guide to Neurodegenerative Disorders — Elsevier 2024
DOI: https://doi.org/10.1016/B978-0-443-15702-8.00005-1

**Co-Author — Review Article:**
*Harnessing Nature's Microscopic Messengers: Cutting-Edge
Viral and Bacterial Vectors Revolutionize Targeted Therapies*
DOI: https://doi.org/10.1016/j.addn.2025.106660

---

## 👤 Contact

**Youssef Ayman Ibrahim**
📧 youselay247@gmail.com
🔗 [LinkedIn](https://linkedin.com/in/you-sef-67a638230)
