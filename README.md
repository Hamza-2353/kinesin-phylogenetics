# 🧬 Kinesin Motor Proteins — Phylogenetic Analysis

[![Notebook A – Kinesin Superfamily](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1fkVHDvmiC706IAhVO9YiespUuGtUaceE?usp=sharing)
[![Notebook B – Kinesin-14 Family](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1dQ40fojDshxkzcfPBOUy02vYbQNU5ClK?usp=sharing)

---

## Overview

This repository contains two Google Colab notebooks for phylogenetic analysis of **kinesin motor proteins** — a superfamily of microtubule-dependent motors found in all eukaryotes.

| # | Notebook | Scope | Sequences |
|---|----------|-------|-----------|
| A | [Kinesin Superfamily](https://colab.research.google.com/drive/1fkVHDvmiC706IAhVO9YiespUuGtUaceE?usp=sharing) | All 14 kinesin families (Kin-1 to Kin-14) | 16 proteins — human, fly, yeast, nematode |
| B | [Kinesin-14 Family](https://colab.research.google.com/drive/1dQ40fojDshxkzcfPBOUy02vYbQNU5ClK?usp=sharing) | Kinesin-14 deep-dive | 18 members across 5 taxonomic groups |

---

## Methods

Both notebooks follow the pipeline from:
- [Neher Lab — Exploring interactive phylogenies with Auspice (2019)](https://neherlab.org/201901_krisp_auspice.html)
- [pb3lab / ibm3202 — Lab 03 Phylogenetics](https://colab.research.google.com/gist/tahashmi/f6bf9c8b3dc9f719289c9ddc0b4f25e3/lab03_phylo.ipynb)

```
NCBI Entrez fetch
      ↓
MUSCLE Multiple Sequence Alignment
      ↓
Gap-column trimming (50% gap threshold)
      ↓
Neighbour-Joining tree  (BioPython, BLOSUM62)
Maximum-Likelihood tree (FastTree, WAG+Gamma)
      ↓
Figures (Matplotlib) + Newick export + iTOL annotation
```

---

## Repository Structure

```
kinesin-phylogenetics/
│
├── notebooks/
│   ├── kinesin_motor_proteins_phylo.ipynb   # Notebook A
│   └── kinesin14_family_phylo.ipynb         # Notebook B
│
├── results/
│   ├── superfamily/
│   │   ├── kin_phylogeny.pdf                # Colour-coded superfamily tree
│   │   ├── kin_phylogeny.png
│   │   ├── kin_ml.nwk                       # ML tree (Newick)
│   │   └── kin_bl_hist.png                  # Branch-length histogram
│   │
│   └── kinesin14/
│       ├── k14_phylogeny.pdf                # Kinesin-14 tree
│       ├── k14_conservation.png             # Alignment conservation plot
│       ├── k14_heatmap.png                  # Pairwise distance heatmap
│       ├── k14_ml.nwk
│       └── k14_itol_colors.txt              # iTOL colour annotation
│
├── requirements.txt
├── environment.yml
├── .gitignore
└── README.md
```

---

## Biological Background

### Kinesin Superfamily

Kinesins are ATP-dependent motors that transport cargo along microtubules.
The superfamily has **14 families** classified by their conserved ~360 aa motor domain.

| Family | Direction | Key member | Function |
|--------|-----------|------------|----------|
| Kinesin-1 | Plus-end | KIF5A / KHC | Axonal transport |
| Kinesin-2 | Plus-end | KIF3A | Intraflagellar transport (IFT) |
| Kinesin-3 | Plus-end | KIF1A | Fast vesicle transport |
| Kinesin-5 | Plus-end | KIF11 (Eg5) | Bipolar spindle assembly |
| Kinesin-13 | Depolymeriser | MCAK | Microtubule catastrophe |
| **Kinesin-14** | **Minus-end** | **KIFC1 / NCD / KAR3** | **Spindle organisation** |

### Kinesin-14 Highlights

- Unique **C-terminal motor domain** (all other families are N-terminal)
- Only consistently **minus-end directed** kinesin family
- **KIFC1 / HSET** (human) — clusters supernumerary centrosomes in cancer cells — selective drug target
- **NCD** (*Drosophila*) — prototype member; essential for meiotic and mitotic spindle
- **KAR3** (*S. cerevisiae*) — karyogamy and spindle pole body morphogenesis
- **KCBP** (*Arabidopsis*) — unique calmodulin-binding domain; trichome morphogenesis
- Largest kinesin family in plant genomes (50+ genes in some species)

---

## How to Run

### Google Colab (no installation needed)

| Notebook | Link |
|----------|------|
| A — Kinesin Superfamily | [Open in Colab](https://colab.research.google.com/drive/1fkVHDvmiC706IAhVO9YiespUuGtUaceE?usp=sharing) |
| B — Kinesin-14 Family | [Open in Colab](https://colab.research.google.com/drive/1dQ40fojDshxkzcfPBOUy02vYbQNU5ClK?usp=sharing) |

1. Click a link above
2. Change `your_email@example.com` to your real email (required by NCBI Entrez)
3. Go to **Runtime → Run all**
4. Download the results zip from the final cell

### Local (conda)

```bash
git clone https://github.com/Hamza-2353/kinesin-phylogenetics.git
cd kinesin-phylogenetics

conda env create -f environment.yml
conda activate kinesin-phylo

jupyter notebook notebooks/
```

---

## Outputs

### Notebook A — Kinesin Superfamily

| File | Description |
|------|-------------|
| `kin_raw.fasta` | 16 unaligned protein sequences |
| `kin_aln.fasta` | MUSCLE alignment |
| `kin_trim.fasta` | Trimmed alignment |
| `kin_nj.nwk` | Neighbour-Joining tree |
| `kin_ml.nwk` | ML tree (FastTree WAG+Gamma) |
| `kin_phylogeny.pdf` | Tree figure — tips coloured by family |
| `kin_bl_hist.png` | Branch-length distribution histogram |

### Notebook B — Kinesin-14 Family

| File | Description |
|------|-------------|
| `k14_raw.fasta` | 18 sequences across 5 organism groups |
| `k14_trim.fasta` | Trimmed alignment |
| `k14_nj.nwk` | NJ tree |
| `k14_ml.nwk` | ML tree (FastTree WAG+Gamma) |
| `k14_phylogeny.pdf` | Tree coloured by organism group |
| `k14_conservation.png` | Per-column alignment conservation plot |
| `k14_heatmap.png` | All-vs-all BLOSUM62 distance heatmap |
| `k14_itol_colors.txt` | Colour file for [iTOL](https://itol.embl.de) |

---

## Suggested Next Steps

- [ ] Bootstrap support values via RAxML-NG: `raxml-ng --bootstrap --msa k14_trim.fasta --model WAG+G`
- [ ] Add outgroup (myosin motor domain) to root the tree
- [ ] Expand Kinesin-14 sampling (more plant species: *Oryza*, *Zea mays*, *Selaginella*)
- [ ] Upload Newick + iTOL file to [itol.embl.de](https://itol.embl.de) for interactive view
- [ ] Ancestral sequence reconstruction (FastML or PAML)
- [ ] Positive selection analysis (dN/dS — HyPhy or PAML)

---

## Tools

| Tool | Purpose |
|------|---------|
| [BioPython](https://biopython.org) >= 1.80 | NCBI fetch, alignment I/O, NJ tree, Phylo |
| [MUSCLE](https://www.drive5.com/muscle/) | Multiple sequence alignment |
| [FastTree](http://www.microbesonline.org/fasttree/) | Maximum-likelihood phylogeny (WAG+Gamma) |
| [Matplotlib](https://matplotlib.org) | Figures and heatmaps |

---

## References

1. Miki H et al. (2005) Analysis of the kinesin superfamily. *Trends Cell Biol* 15(9):467–76
2. Wickstead B & Gull K (2006) A "holistic" kinesin phylogeny reveals new kinesin families. *Mol Biol Cell* 17(4):1897–907
3. Richardson DN et al. (2006) Comparative analysis of the kinesins. *Trends Plant Sci* 11(8):395–402
4. Neher R (2019) Exploring interactive phylogenies with Auspice. https://neherlab.org/201901_krisp_auspice.html
5. pb3lab/ibm3202 Lab 03 Phylogenetics. https://colab.research.google.com/gist/tahashmi/f6bf9c8b3dc9f719289c9ddc0b4f25e3/lab03_phylo.ipynb

---

## License

MIT — free to use and modify with attribution.

---

*Made with BioPython, MUSCLE, FastTree, and Matplotlib*
