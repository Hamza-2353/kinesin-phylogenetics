# Kinesin Motor Proteins — Phylogenetic Analysis

[![Open Notebook A in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/YOUR_USERNAME/kinesin-phylogenetics/blob/main/notebooks/kinesin_motor_proteins_phylo.ipynb)
[![Open Notebook B in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/YOUR_USERNAME/kinesin-phylogenetics/blob/main/notebooks/kinesin14_family_phylo.ipynb)

> **Replace `YOUR_USERNAME`** with your GitHub username in the badge URLs above after creating the repo.

---

## Overview

This repository contains two Google Colab notebooks for phylogenetic analysis of **kinesin motor proteins** — a superfamily of microtubule-dependent motors found in all eukaryotes.

| Notebook | Scope | Sequences | Key Outputs |
|----------|-------|-----------|-------------|
| `kinesin_motor_proteins_phylo.ipynb` | All 14 kinesin families (Kin-1 → Kin-14) | 16 representative proteins across human, fly, yeast, nematode | Coloured phylogeny, branch-length histogram |
| `kinesin14_family_phylo.ipynb` | Kinesin-14 family deep-dive | 18 members across 5 taxonomic groups | Phylogeny, conservation plot, pairwise heatmap, iTOL export |

### Methods (following Neher Lab Auspice tutorial + pb3lab ibm3202 Lab 03)

```
NCBI Entrez fetch  →  MUSCLE alignment  →  Gap trimming  →  NJ tree (BioPython)
                                                          →  ML tree  (FastTree WAG+Γ)
                                                          →  Figures  (Matplotlib)
                                                          →  Export   (Newick / iTOL)
```

---

## Repository Structure

```
kinesin-phylogenetics/
│
├── notebooks/
│   ├── kinesin_motor_proteins_phylo.ipynb   # Notebook A — full superfamily
│   └── kinesin14_family_phylo.ipynb         # Notebook B — Kinesin-14 family
│
├── results/                                 # Generated after running notebooks
│   ├── superfamily/
│   │   ├── kin_raw.fasta                    # Unaligned sequences
│   │   ├── kin_aln.fasta                    # MUSCLE alignment
│   │   ├── kin_trim.fasta                   # Trimmed alignment
│   │   ├── kin_nj.nwk                       # Neighbour-Joining tree
│   │   ├── kin_ml.nwk                       # ML tree (FastTree)
│   │   ├── kin_phylogeny.pdf                # Publication-quality figure
│   │   └── kin_bl_hist.png                  # Branch-length histogram
│   │
│   └── kinesin14/
│       ├── k14_raw.fasta
│       ├── k14_aln.fasta
│       ├── k14_trim.fasta
│       ├── k14_nj.nwk
│       ├── k14_ml.nwk
│       ├── k14_phylogeny.pdf
│       ├── k14_conservation.png             # Alignment conservation plot
│       ├── k14_heatmap.png                  # Pairwise distance heatmap
│       └── k14_itol_colors.txt              # iTOL colour annotation file
│
├── environment.yml                          # Conda environment (local use)
├── requirements.txt                         # pip requirements (local use)
├── .gitignore
└── README.md
```

---

## Biological Background

### Kinesin Superfamily
Kinesins are ATP-dependent motor proteins that move cargo along microtubules. The superfamily comprises **14 families (Kinesin-1 to Kinesin-14)** classified by their conserved ~360 aa motor domain.

| Family | Direction | Key member | Function |
|--------|-----------|-----------|----------|
| Kinesin-1 | Plus-end | KIF5A/KHC | Axonal transport |
| Kinesin-2 | Plus-end | KIF3A | Intraflagellar transport |
| Kinesin-3 | Plus-end | KIF1A | Fast vesicle transport |
| Kinesin-5 | Plus-end | KIF11 (Eg5) | Bipolar spindle assembly |
| Kinesin-13 | — (depolymeriser) | MCAK | MT catastrophe |
| **Kinesin-14** | **Minus-end** | **KIFC1/NCD/KAR3** | **Spindle organisation** |

### Kinesin-14 Highlights
- Unique **C-terminal motor domain** (all others are N-terminal)
- Only consistently **minus-end directed** family
- **KIFC1/HSET** (human): clusters supernumerary centrosomes in cancer cells — selective drug target
- **NCD** (*Drosophila*): prototype member; essential for meiotic spindle
- **KAR3** (*S. cerevisiae*): karyogamy and mitotic spindle morphogenesis
- **KCBP** (*Arabidopsis*): unique calmodulin-binding domain; trichome morphogenesis
- Largest kinesin family in plant genomes

---

## How to Run

### Option 1 — Google Colab (recommended, no installation needed)
1. Click the **Open in Colab** badge at the top of this README
2. In the notebook, change `your_email@example.com` to your real email (NCBI requires this)
3. **Runtime → Run all**
4. Download results zip when prompted in the final cell

### Option 2 — Local (requires conda or pip)

```bash
# Clone the repo
git clone https://github.com/YOUR_USERNAME/kinesin-phylogenetics.git
cd kinesin-phylogenetics

# Create environment
conda env create -f environment.yml
conda activate kinesin-phylo

# Install system tools
sudo apt-get install muscle fasttree   # Linux
# brew install muscle fasttree         # macOS

# Launch Jupyter
jupyter notebook notebooks/
```

---

## What the Notebooks Produce

### Notebook A — Kinesin Superfamily

| Step | Output |
|------|--------|
| NCBI fetch | `kin_raw.fasta` — 16 sequences |
| MUSCLE + trim | `kin_aln.fasta`, `kin_trim.fasta` |
| NJ tree | `kin_nj.nwk` |
| ML tree | `kin_ml.nwk` (FastTree WAG+Γ) |
| Figure | `kin_phylogeny.pdf` — tips coloured by family |
| Stats | `kin_bl_hist.png` — branch-length distribution |

### Notebook B — Kinesin-14 Family

| Step | Output |
|------|--------|
| NCBI fetch | `k14_raw.fasta` — 18 sequences across 5 groups |
| MUSCLE + trim | `k14_aln.fasta`, `k14_trim.fasta` |
| Conservation plot | `k14_conservation.png` — per-column conservation |
| NJ + ML trees | `k14_nj.nwk`, `k14_ml.nwk` |
| Coloured phylogeny | `k14_phylogeny.pdf` — tips coloured by organism group |
| Distance heatmap | `k14_heatmap.png` — all-vs-all BLOSUM62 distances |
| iTOL export | `k14_itol_colors.txt` — upload to [itol.embl.de](https://itol.embl.de) |

---

## Suggested Next Steps

- [ ] Add bootstrap support values (RAxML-NG: `raxml-ng --bootstrap --msa k14_trim.fasta --model WAG+G`)
- [ ] Expand taxon sampling (more plant Kinesin-14 members — *Oryza*, *Zea*, *Selaginella*)
- [ ] Add outgroup sequences (myosin motor domain as distant outgroup)
- [ ] Map functional domains onto tree (N-terminal tail, coiled-coil, motor domain boundaries)
- [ ] Ancestral sequence reconstruction (FastML or PAML)
- [ ] Interactive visualisation with [Nextstrain/Auspice](https://auspice.us)
- [ ] Molecular evolution analysis (dN/dS ratios, positive selection — PAML/HyPhy)

---

## Tools & References

### Software
| Tool | Version | Purpose |
|------|---------|---------|
| BioPython | ≥1.80 | NCBI fetch, alignment I/O, NJ tree, Phylo |
| MUSCLE | 3.x or 5.x | Multiple sequence alignment |
| FastTree | 2.x | Maximum-likelihood tree inference |
| Matplotlib | ≥3.5 | Figures |

### References
1. Miki H et al. (2005) Analysis of the kinesin superfamily. *Trends Cell Biol* 15(9):467–76
2. Wickstead B & Gull K (2006) A "holistic" kinesin phylogeny reveals new kinesin families. *Mol Biol Cell* 17(4):1897–907
3. Richardson DN et al. (2006) Comparative analysis of the kinesins. *Trends Plant Sci* 11(8):395–402
4. Neher R (2019) Exploring interactive phylogenies with Auspice. https://neherlab.org/201901_krisp_auspice.html
5. pb3lab/ibm3202 Lab 03: Phylogenetic analysis. https://colab.research.google.com/gist/tahashmi/f6bf9c8b3dc9f719289c9ddc0b4f25e3/lab03_phylo.ipynb

---

## License

MIT License — free to use, modify, and distribute with attribution.
