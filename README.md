# Teff Rotation — Rhizosphere Microbiome & Root System Architecture

**Author:** Alessandra Learmount 

**Institution:** Niab

**Period:** January – March 2026

---

## Overview

This repository contains data, analysis scripts, and rendered outputs from a rotation project investigating the root system architecture (RSA) and rhizosphere microbiome of *Eragrostis tef* (teff). Six teff accessions (Addisie, Beten, Dabbi, Karadebi, Manyi, Tsedey) obtained from Niab were used across three experimental components: RSA phenotyping of agar-grown seedlings (all six genotypes), RSA phenotyping of soil-grown plants (Addisie, Dabbi, Karadebi, Tsedey), and shotgun metagenomic profiling of rhizosphere microbial communities (Dabbi and Tsedey).

---

## 1. Plant Material

Seeds from six *Eragrostis tef* accessions were obtained from Niab (Table 1). Genotype usage across experiments is summarised below:

| Genotype | RSA Agar (Day 16/17) | RSA Soil (6-week) | Microbiome Sequencing |
|---|---|---|---|
| Addisie | ✓ | ✓ | — |
| Dabbi | ✓ | ✓ | ✓ |
| Karadebi | ✓ | ✓ | — |
| Tsedey | ✓ | ✓ | ✓ |
| Beten | ✓ | — | — |
| Manyi | ✓ | — | — |

Seed germination rate was assessed for all six genotypes at three days post-sowing in Petri dishes. Germination was uniformly high (88.9–100%), confirming seed viability across genotypes.

---

## 2. Root System Architecture — Day 16/17 (Agar)

### 2.1 Growth Conditions

Seeds were surface sterilised in a laminar flow hood:
1. 70% ethanol — 30 seconds
2. 10% sodium hypochlorite — 5 minutes
3. Washed 5× with sterile distilled water (SDW)

Sterilised seeds were plated onto square agar plates (Sigma-Aldrich, 120 × 120 × 17 mm) with up to four seeds per plate, equally spaced along a horizontal line 30 mm below the top wall. Each plate contained approximately 50 mL of media:

| Media Component | Details |
|---|---|
| Base media | Half-strength Murashige and Skoog (Duchefa Biochemie) |
| Agar concentration | 0.8% |
| pH | 5.6 |
| Sealing | Micropore tape (3M) |
| Orientation | Vertical (to direct root growth along gravitropic vector) |
| Temperature | 22°C |
| Photoperiod | 16 h light / 8 h dark |

### 2.2 Scanning and Image Analysis

Each plate was scanned at 16–17 days post-germination using a **Desktop Flatbed Scanner (Epson Perfection V850 Pro)** in colour at **800 DPI**.

Root scans were segmented in **FIJI (ImageJ-FIJI v2.16.0)** using the **LabKit plugin**, then analysed using **RhizoVision Explorer v2.0.3** with the following parameters:

| Parameter | Value |
|---|---|
| Thresholding level | 200 |
| Analysis type | Whole root |
| Background noise filter | < 5 components |
| Root pruning threshold | 15 |

### 2.3 Traits Analysed

| Trait | Abbreviation | Definition | Units | Agar | Soil |
|---|---|---|---|---|---|
| Root tips | RT | Pixels in identified root topology with only one neighbouring skeletal pixel | count | ✓ | ✓ |
| Root length | RL | Sum of Euclidean distances between connected skeletal pixels | mm | — | ✓ |
| Average root diameter | ARD | Mean diameter computed across all skeleton pixels from distance transform | mm | ✓ | ✓ |
| Root volume | RV | Length × cross-sectional area, summed across all skeletal pixels | mm³ | ✓ | ✓ |
| Root surface area | RA | Length × circumference of cross-section, summed across all skeletal pixels | mm² | ✓ | ✓ |
| Network area | NA | Total number of pixels in segmented image | mm² | ✓ | ✓ |
| Convex area | CA | Area of convex hull encompassing the entire root crown system | mm² | ✓ | — |
| Root solidity | RS | Ratio of Network Area to Convex Area | 0–1 | ✓ | ✓ |
| Steep angle frequency | SF | Frequency of skeletal pixels in steep (60–90°) angular bin within 40×40 px locality windows | 0–1 | ✓ | ✓ |
| Root depth | RD | Maximum vertical distance the root crown grew at time of imaging | mm | ✓ | — |
| Width-to-depth ratio | WDR | Ratio of maximum width to depth | ratio | ✓ | — |
| Shoot dry mass | SM | Total dry mass of above-ground plant tissue after drying to constant mass | g | — | ✓ |
| Root dry mass | RM | Total dry mass of below-ground plant tissue after drying to constant mass | g | — | ✓ |
| Root system spread angle | RSS | Angle subtended between the two outermost crown roots at the crown node | ° | — | ✓ |
| Number of crown roots | CR | Count of total number of >0.1 mm roots growing from the crown | count | — | ✓ |
| Root tissue density | RTD | Ratio of root dry mass (RM) to root volume (RV) | g cm⁻³ | — | ✓ |
| Root-to-shoot mass ratio | RSM | Ratio of root dry mass (RM) to shoot dry mass (SM) | ratio | — | ✓ |

### 2.4 Analysis Script

[rsa_day1617_agar.qmd](RSA_agar/rsa_day1617_agar.qmd) — Full Quarto R script for trait extraction, statistical modelling, and visualisation.

---

## 3. Root System Architecture — 6-Week-Old Plants, Batch 4 (Soil)

### 3.1 Growth Conditions

Seeds of **Addisie, Dabbi, Karadebi, and Tsedey** (3–4 per pot) were sown into pots (69 × 67 × 150 mm; 2520 tree tray 28, Modiform) containing **Sinclair Potting & Bedding Growing Medium**. Pots were thinned to one plant after one week (8 replicates per genotype) and watered every other day with RO water.

### 3.2 Harvesting and Scanning

At **six weeks post-germination**, whole root systems were extracted and submerged in water to remove loosely bound soil. Tightly bound particles were removed under pressurised water spray. Roots were scanned in colour at **400 DPI** using a water tray (Epson Perfection V850 Pro). Crown roots were counted and whole plants were dried to constant mass to record root and shoot dry mass.

Root scans were segmented and analysed using the same pipeline described in Section 2.2.

### 3.3 Analysis Script

[rsa_6week_soil_batch4.qmd](RSA_soil_batch4/rsa_6week_soil_batch4.qmd) — Full Quarto R script for soil RSA analysis.

---

## 4. Rhizosphere Microbiome — Shotgun Metagenomics

### 4.1 Seed Sterilisation and Germination

Seeds of **Dabbi** and **Tsedey** were surface sterilised following the protocol in Section 2. Approximately 20 seeds per dish were evenly spaced on autoclaved filter paper dampened with 2.5 mL RO water in 90-mm circular Petri dishes.

| Stage | Conditions |
|---|---|
| Germination | 28°C, 16 h light / 8 h dark, 48 h |
| Post-germination transfer | 22°C tissue culture room, 16 h light / 8 h dark |
| Transplantation | 7-day-old seedlings into individual pots |
| Soil | Baileys Renovation Mix (50:50 Norfolk loam:sports sand, screened to 4 mm) |
| Pots | 69 × 67 × 150 mm (2520 tree tray 28, Modiform) |
| Growth chamber | PGR15 (Conviron) |
| Light/temperature | 16 h light (23°C) / 8 h dark (18°C) |
| Light intensity | 300 μmol photons m⁻² s⁻¹ |
| Watering | RO water, from above and below as required |

### 4.2 Root Sampling

At **five weeks post-transplantation**, whole plants were removed from pots and roots shaken for 1 minute to remove loosely bound bulk soil. The uppermost 2 cm of root adjacent to the shoot was removed (to exclude tissue affected by desiccation and surface algal contamination), as was any tissue protruding through drainage holes.

Three 2 cm sections were excised per plant:

| Section | Location |
|---|---|
| **Root base** | 2 cm immediately below the shoot excision point (closest to shoot) |
| **Root mid-section** | 2 cm section at the midpoint of the remaining root |
| **Root tip** | Terminal 2 cm furthest from the shoot |

Each section was transferred to a 2 mL microcentrifuge tube, flash frozen in liquid nitrogen, and stored at −80°C until DNA extraction.

**Total extractions:** 24 (2 genotypes × 3 root sections × 4 replicates)

### 4.3 DNA Extraction

| Parameter | Details |
|---|---|
| Input mass | 250 mg root tissue per sample |
| Kit | DNeasy PowerLyzer PowerSoil Kit (Cat. No. 12855; Qiagen) |
| Concentration step | Vacuum centrifugation (SpeedVac) for samples yielding <25 ng µL⁻¹ |

### 4.4 Library Preparation and Sequencing

| Parameter | Details |
|---|---|
| Kit | Ligation Sequencing gDNA Native Barcoding Kit 24 V14 (SQK-NBD114.24; Oxford Nanopore Technologies) |
| Sequencer | PromethION P24 — Cambridge Genomic Services (Pathology) |

### 4.5 Basecalling and Demultiplexing

| Software | Version | Setting |
|---|---|---|
| Dorado | v7.11.2+85fc2b9f5 | Super accuracy |
| Basecalling model | dna_r10.4.1_e8.2_400bps_sup@v5.2.0 | 400 bps |
| MinKNOW | v25.09.16 | Demultiplexing |

### 4.6 Taxonomic Classification

Reads were classified on an HPC cluster via **SLURM** using **Kraken2**, employing a k-mer (k = 35) based approach. The entire database was preloaded into memory on an HPC node prior to classification for efficiency.

#### Kraken2 Command

```bash
kraken2 --use-names \\
        --threads 4 \\
        --confidence 0.1 \\
        --db [database] \\
        --report barcodeX.krakenreport.txt \\
        --gzip-compressed barcodeX.fastq.gz \\
        > barcodeX.kraken2.txt
```

| Parameter | Description |
|---|---|
| `--use-names` | Print scientific names instead of taxids |
| `--threads 4` | Use 4 CPUs per job |
| `--confidence 0.1` | Confidence score threshold |
| `--db` | Reference database (see Section 4.7) |
| `--report` | Save read mapping report to file |
| `--gzip-compressed` | Read from gzip-compressed FASTQ |


#### Post-Classification Filtering

| Filter | Threshold | Reference |
|---|---|---|
| Confidence threshold | 0.1 | — |
| Minimum relative abundance | 0.00055 | Van Uffelen et al. (2024) |

### 4.7 Reference Databases

#### Fungal Database (MycoCosm)

| Parameter | Details |
|---|---|
| Source | [JGI MycoCosm](https://mycocosm.jgi.doe.gov/) |
| Build date | December 2025 |
| Scope | All available fungal genomes at JGI MycoCosm |
| Type | Custom database |

#### Prokaryotic Database (GTDB)

| Parameter | Details |
|---|---|
| Source | Genome Taxonomy Database (GTDB) |
| Version | v226 |
| Reference | Parks et al. (2022) |
| Scope | Bacteria and archaea |

### 4.8 Downstream R Analysis

Diversity and community composition analyses were performed in **R v4.5.2**. Analysis scripts:

- [teff_mycocosm_analysis.qmd](microbiome/teff_mycocosm_analysis.qmd) — Fungal community analysis (MycoCosm database)
- [teff_gtdb_analysis.qmd](microbiome/teff_gtdb_analysis.qmd) — Prokaryotic community analysis (GTDB database)

---

## 5. Software and Package Versions

### Bioinformatics Tools

| Software | Version | Purpose |
|---|---|---|
| Dorado | v7.11.2+85fc2b9f5 | Basecalling |
| MinKNOW | v25.09.16 | Sequencing control and demultiplexing |
| Kraken2 | 2.1.x | Taxonomic classification |
| Bracken | 2.9 | Abundance estimation |
| FIJI / ImageJ | v2.16.0 | Image segmentation (LabKit plugin) |
| RhizoVision Explorer | v2.0.3 | Root trait extraction |

### R Packages

| Package | Version | Source | Purpose |
|---|---|---|---|
| R | 4.5.2 | — | Statistical computing |
| vegan | — | CRAN | Community ecology and diversity analysis |
| phyloseq | — | Bioconductor | Microbiome data handling |
| ggplot2 | — | CRAN | Data visualisation |
| dplyr | — | CRAN | Data manipulation |
| tidyr | — | CRAN | Data tidying |




