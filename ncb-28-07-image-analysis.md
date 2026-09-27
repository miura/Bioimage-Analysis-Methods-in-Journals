---
title: "Nature Cell Biology, Volume 28, Issue 7 (12 articles)"
subtitle: "Bioimage analysis methods survey"
subject: Methods survey
date: 2026-09-27
---

```{note}
Methodology: each article PDF was converted to plain text with `pdftotext -layout` and searched for Methods subsections, software names, code-repository links, figure legends, and Data/Code availability statements. Figure and panel numbers were cross-checked against figure-legend text (authoritative over body-text parenthetical citations); Extended Data panels are distinguished from main-text Figures throughout. As in the previous *Nature Cell Biology* issue surveyed, several articles here have image-analysis content that is folded into a generic "quantified using [instrument acquisition software]" statement with no dedicated segmentation/quantification tool ever named — this is reported explicitly as a methods gap rather than guessed. The 4-way sample-image-data-availability classification is applied strictly: generic "data" or "Source data" language never counts as categories (a) or (b), even when the paper obviously contains microscopy images — only an explicit, resolvable public accession for image/microscopy data counts as (a), and only an explicit "available on request" statement naming images/microscopy data counts as (b).
```

## At a glance

| Article | DOI | Key imaging software | Version given? | Measurement target | Code repo | Sample image data |
|---|---|---|---|---|---|---|
| [Lysosome-derived ADMA controls the lipidome](#lysosome-adma-lipidome) | [doi:10.1038/s41556-026-01970-4](doi:10.1038/s41556-026-01970-4) | Fiji/ImageJ | Yes (v2.14.0 and v1.54p cited for different sub-tasks) | 1) ADMA–LAMP1/LAMP2A colocalization (PCC); 2) Lipid-droplet count/size; 3) Peroxisome number/diameter; 4) PLA puncta per cell | None | (c) |
| [SLC25A12 in mitochondrial stress signalling](#slc25a12-mito-stress) | [doi:10.1038/s41556-026-01973-1](doi:10.1038/s41556-026-01973-1) | Fiji + MiNA plugin | No | 1) Mitochondrial network morphology (branches/structure) | None | (c) |
| [Mitochondria–ER contacts as an iron supply hub](#mito-er-iron-hub) | [doi:10.1038/s41556-026-01974-0](doi:10.1038/s41556-026-01974-0) | Fiji/ImageJ (unversioned) | No | 1) Organelle co-localization (qualitative only — no Pearson's/Manders' computed despite dual/triple IF); 2) Immunoblot densitometry | None | (c) |
| [Short linear motifs drive actin filament binding](#slim-actin-binding) | [doi:10.1038/s41556-026-01979-9](doi:10.1038/s41556-026-01979-9) | Cryo-EM: RELION4/CryoSPARC/ChimeraX; cellular: Imaris + Poji | Yes (RELION 4.0; ChimeraX 1.7; cryolo 1.7) | 1) Cryo-EM structure of actin–ITPKA/USP54 complexes; 2) Podosome peptide/actin co-localization (radial intensity profile); 3) Co-sedimentation blot densitometry | GitHub + Zenodo (SLiMFold/PSFM pipelines — computational, not the fluorescence-microscopy pipeline) | **(a)\*** cryo-EM only; (c) for fluorescence micrographs |
| [ERO1α and glioblastoma mitochondria-associated membranes](#ero1a-glioblastoma-mam) | [doi:10.1038/s41556-026-01980-2](doi:10.1038/s41556-026-01980-2) | Fiji/ImageJ; Harmony (Opera-Phenix) | No | 1) ER–mitochondria contact by TEM; 2) Mitochondrial network morphology; 3) PLA dot count; 4) Ca²⁺-imaging ratio | None (custom TEM macro informally shared by collaborators, not deposited) | (c) |
| [CD44 restricts EGFR mobility in bleb-based migration](#cd44-egfr-bleb-migration) | [doi:10.1038/s41556-026-01981-1](doi:10.1038/s41556-026-01981-1) | Fiji/ImageJ (MTrackJ, OrientationJ) + PIVLab + EasyFRAP-web | No | 1) Cell trajectory/MSD; 2) EGFR/biosensor polarity index (line-scan); 3) FRAP diffusion coefficient; 4) PIV actin retrograde flow | None (mathematical model described in prose only, not deposited as code) | (c) |
| [Cis/trans regulation of extrachromosomal DNA segregation](#ecdna-segregation-mechanisms) | [doi:10.1038/s41556-026-01982-0](doi:10.1038/s41556-026-01982-0) | None named for the paper's core assay (ImageJ named only for a secondary RNA-dye readout) | N/A | 1) ecDNA "detachment" from mitotic chromosomes (dAUC/ECDF, FISH signal area) — quantification software never named | None | (c) |
| [MED4 enforces metastatic dormancy](#med4-metastatic-dormancy) | [doi:10.1038/s41556-026-01984-y](doi:10.1038/s41556-026-01984-y) | None named (all IF quantification described without a named tool) | N/A | 1) HP1α heterochromatin area fraction; 2) Focal-adhesion density/area; 3) Nuclear:cytoplasmic ratio (YAP/MRTF-A); 4) Pericellular Collagen I/α-SMA shell intensity | None ("No custom code was generated for this study") | (c) |
| [TEAD1 condensates on pericentromeric heterochromatin](#tead1-heterochromatin-condensates) | [doi:10.1038/s41556-026-01985-x](doi:10.1038/s41556-026-01985-x) | Fiji+BIOP-JACoP; Imaris v10.2.0; CellProfiler v4.2.8; DiAna; SLIMfast | Yes (Imaris v10.2.0; CellProfiler v4.2.8) | 1) Condensate count/localization; 2) Colocalization (Manders'); 3) 3D distance to CENP-A/TRF2; 4) Single-particle-tracking diffusion | **GitHub** (public, includes analysis code) | **(a)** |
| [DRP1/MID49 co-diffusion scans for fission](#drp1-mid49-fission) | [doi:10.1038/s41556-026-01986-w](doi:10.1038/s41556-026-01986-w) | Fiji/ImageJ; Imaris; MitoSkel; ASAP; custom Python (scikit-image/SciPy) | Mixed (GROMACS 2025.1, SciPy 1.11.4 versioned; Fiji/Imaris/MitoSkel/ASAP not) | 1) Mitochondrial diameter at fission (FWHM); 2) DRP1 particle-tracking/MSD; 3) Mitochondrial network morphology (MitoSkel); 4) Super-resolution structure classification (ASAP) | **GitHub** (public, custom Python SPT script) | (c) |
| [Integrated stress response and lineage reprogramming](#isr-mitochondrial-fitness) | [doi:10.1038/s41556-026-01991-z](doi:10.1038/s41556-026-01991-z) | QuPath (v0.5.0/v0.6.0, inconsistent); NIS-Elements | Yes (QuPath, inconsistently) | 1) TEM mitochondrial density/area (software unnamed); 2) DRP1–mitochondria colocalization (Manders', NIS-Elements); 3) IHC H-score (QuPath) | None | (c) |
| [CLiB: engineering lipid-binding probes by screening](#clib-lipid-probe-screening) | [doi:10.1038/s41556-026-01996-8](doi:10.1038/s41556-026-01996-8) | Fiji/ImageJ (named custom macros) + R scripts | No (macro files individually named instead) | 1) Vacuolar GFP intensity/localization pattern; 2) GFP dot/ring counts (blinded manual); 3) Colocalization (Pearson's/Manders', software unnamed) | **Zenodo** — explicitly "the codes used to analyse imaging data" | **(a)** |

(lysosome-adma-lipidome)=
## Lysosome-derived methylated arginine is a signalling metabolite controlling the lipidome

Steven T. Nguyen et al. — *Nature Cell Biology*, Volume 28, pages 1379–1392 (2026). [doi:10.1038/s41556-026-01970-4](doi:10.1038/s41556-026-01970-4)

1. Confocal immunofluorescence of ADMA/LAMP1/DAPI in human kidney biopsies and CTNSKO/WT HK-2 cells, colocalization via Pearson correlation coefficient (PCC) in Fiji. **→ Fig. 1g,h** (also Extended Data Fig. 3a–c, 4c,f).
2. Proximity ligation assay (PLA) of ADMA–LAMP2A interaction, quantified per cell with ImageJ "Analyze Particles." **→ Fig. 1i**.
3. Lipid-droplet (LD) quantification via BODIPY-493/503 staining and ImageJ particle counting, in biopsies and cultured cells. **→ Fig. 2a,b** (also Extended Data Fig. 5c–f).
4. Peroxisome (PMP70) immunofluorescence — number, diameter, mean fluorescence intensity quantified via ImageJ, with the specific segmentation method never detailed. **→ Fig. 4a,b**.
5. BODIPY-C11 lipid-peroxidation and DAF NOS-activity fluorescence quantification via Fiji. **→ Fig. 5b,c**.
6. Immunoblot acquisition (iBright FL1500) and densitometry via ImageJ. **→ Fig. 3e–g, Fig. 4e,j**.

```{note} Ambiguities and gaps
:class: dropdown
Two different Fiji version numbers are cited in the same "Image analysis" paragraph (v2.14.0 for colocalization/PCC; v1.54p for fluorescence intensity) with no explanation. GraphPad Prism is likewise cited inconsistently (Prism 10 for statistics; "Prism 7" for lipidomic data analysis). No PCC/colocalization algorithm or plugin (e.g., JACoP, Coloc2), background-subtraction method, or thresholding criterion is given beyond "the same brightness/contrast profile and threshold values," mentioned only for the PLA step. Peroxisome number/diameter segmentation (Fig. 4a,b) and NOS-activity (DAF) image quantification (Fig. 5c) are folded into the generic Fiji/ImageJ workflow without panel-specific detail.
```

```{admonition} Verbatim quotes
:class: note
"Colocalization and proximity sites were analysed using Fiji ImageJ (v 2.14.0) using Pearson correlation coefficient (PCC) colocalization tests." — "The ImageJ analyse particles feature was used for PLA quantification where over ten fields of view were used for each condition." — "ImageJ (National Institutes of Health (NIH)) was used to quantify the number of LDs."
```

- **Software named**: Fiji ImageJ v2.14.0 / v1.54p (two versions cited for different sub-tasks), ImageJ (NIH, unversioned), LipidSearch v4.2.21, GraphPad Prism 10 / Prism 7 (inconsistent), Clustvis, LION.
- **Code repository**: None found.
- **Sample image data**: Not stated for image data specifically (category c). GEO/MassIVE/Dryad accessions cover transcriptomics/metabolomics/lipidomics only; "Source data" and "all other data...on request" never name images.
- **Based on prior methods**: Lyso-IP technique, CTNSKO cell generation, and lipid-extraction protocol are all cited (refs. 32, 23, 91). The core Fiji/ImageJ-based PCC colocalization, LD counting, and PLA particle-analysis quantification are described without citation to a prior published image-analysis protocol.

(slc25a12-mito-stress)=
## A transport-independent role for SLC25A12 in mitochondrial stress signalling

Liu Jiang et al. — *Nature Cell Biology*, Volume 28, pages 1424–1436 (2026). [doi:10.1038/s41556-026-01973-1](doi:10.1038/s41556-026-01973-1)

1. Mitochondrial network morphology quantification — MitoTracker Red CMXRos, Zeiss LSM880 confocal, branches-per-structure quantified with the MiNA "Analyze Morphology" plugin in Fiji. **→ Fig. 3m,n**.
2. BiFC imaging of split-fluorescent-protein interaction constructs — representative images only, no separate quantification panel. **→ Extended Data Fig. 5c**.
3. Structured-illumination microscopy (SIM) of inner-membrane localization (HIS-SIM system, "Imager" v1.4.20c acquisition, "MicroscopeX FINER" v1.1.15e sparse deconvolution) — qualitative only. **→ Extended Data Fig. 5f**.
4. TUNEL apoptosis imaging in heart sections (VS200 Slide Scanner) — counting method for positive cells unstated. **→ Extended Data Fig. 3k,l**.

```{note} Ambiguities and gaps
:class: dropdown
No Code availability section/heading exists anywhere in the document at all. TUNEL-positive-cell quantification (Extended Data Fig. 3l) has no stated counting method or software. SIM analysis (Extended Data Fig. 5f) is qualitative-only, with no quantification panel or software named. The MiNA plugin version is not given (nor is Fiji's own version).
```

```{admonition} Verbatim quotes
:class: note
"Images were acquired using a Zeiss LSM880 confocal microscope equipped with a 63× oil-immersion objective. Mitochondrial morphology was quantified using the MiNA Analyze Morphology plugin in Fiji." — "Imaging was performed 24 h post transfection using the Imager software (v1.4.20c). ... Sparse deconvolution was applied using MicroscopeX FINER software (v1.1.15e)."
```

- **Software named**: Fiji + MiNA plugin (unversioned), Imager v1.4.20c, MicroscopeX FINER v1.1.15e, GraphPad Prism v10.1.1, HISAT2 v2.1.0, DESeq2 v1.34.0.
- **Code repository**: None found.
- **Sample image data**: Not stated for image data specifically (category c). GEO accession covers RNA-seq only; "all other data...on reasonable request" never names microscopy data.
- **Based on prior methods**: OMA1 cleavage assay and Mito-IP metabolite profiling cite prior methods (refs. 43, 62). The MiNA-based mitochondrial-morphology quantification and the SIM imaging/deconvolution protocol are presented without a citation for the quantification approach itself.

(mito-er-iron-hub)=
## Mitochondria–ER contacts function as an iron supply hub

Hijiri Oshio et al. — *Nature Cell Biology*, Volume 28, pages 1464–1479 (2026). [doi:10.1038/s41556-026-01974-0](doi:10.1038/s41556-026-01974-0)

1. Confocal immunofluorescence (Olympus FV3000, three z-slices reconstructed in Fiji/ImageJ) localizing TurboID-MITOL and HMOX1/HMOX2 relative to ER/mitochondria markers — presented only as qualitative representative images, with **no colocalization coefficient (Pearson's/Manders') computed** despite the experiments being explicitly designed to show organelle colocalization. **→ Extended Data Fig. 1a,b; Fig. 1j; Fig. 2d**.
2. Immunoblot band-intensity quantification via Fiji/ImageJ (general method, not tied to specific panels in Methods; inferred from figure-legend "quantified" language). **→ Fig. 5d,h; Fig. 6c,f** (also Extended Data Figs. 8, 9).
3. CN-PAGE + in-gel activity assay for respiratory supercomplex integrity — gel image, not quantified via named software. **→ Fig. 7c,d**.

```{note} Ambiguities and gaps
:class: dropdown
No colocalization analysis (Pearson's/Manders') is reported despite multiple dual/triple-immunofluorescence experiments explicitly aimed at showing organelle colocalization — a notable methodological gap for a paper centered on mitochondria–ER contact sites. No microscope acquisition software is named for the FV3000 confocal system (only Fiji for post-hoc reconstruction). No "Code availability" section exists in this Methods/end-matter at all — unusual for a Nature Cell Biology paper.
```

```{admonition} Verbatim quotes
:class: note
"Immunofluorescence was performed as previously described14. ... samples were mounted with fluorescence mounting medium ... and analysed using an FV3000 confocal laser scanning microscope (Olympus). Three z-stack slices were acquired every 0.2 μm and reconstructed using Fiji/ImageJ software." — "Band images were acquired using a LuminoGraph I imager (WSE-6100, ATTO), and relative band intensities were quantified using Fiji/ImageJ software."
```

- **Software named**: Fiji/ImageJ (unversioned, two purposes), FlowJo (unversioned), DatLab 7.4, Proteome Discoverer v2.4 SP1 / v3.0 SP1 (with Chimerys node).
- **Code repository**: None found.
- **Sample image data**: Not stated for image data specifically (category c). jPOST/PRIDE accessions cover proteomics only; "data...available from the corresponding authors" and "Source data" never name images.
- **Based on prior methods**: Immunofluorescence protocol, biotin-labelling/pulldown protocol, and CN-PAGE assay all cite prior published work (refs. 14, 64, 67). The Fiji/ImageJ-based band-intensity quantification and confocal reconstruction are presented without a specific quantification-method citation.

(slim-actin-binding)=
## Evolutionarily conserved short linear motifs drive actin filament binding

Themistoklis Paraschiakos et al. — *Nature Cell Biology*, Volume 28, pages 1437–1452 (2026). [doi:10.1038/s41556-026-01979-9](doi:10.1038/s41556-026-01979-9)

1. Cryo-EM structure determination of ITPKA–actin and USP54 M1–actin filament complexes (RELION 4.0, CryoSPARC, MotionCor2, CTFFIND4, crYOLO 1.7; atomic models built in ChimeraX 1.7, refined with ISOLDE/Phenix). **→ Fig. 1a, Fig. 4** (also Extended Data Figs. 1, 7) — structural renderings, not raw micrographs.
2. Cellular co-localization imaging of EGFP-tagged SFM peptides with phalloidin-568-stained F-actin (Olympus FV3000/IXplore Live), podosome-level quantification via Imaris 3D reconstruction plus the Poji plugin (prior-published, ref. 126) generating circular ROIs and 360° radial intensity profiles. **→ Fig. 2b** (also Extended Data Figs. 4, 5).
3. Optogenetic photoactivation (Opto-EGFR, PA-Rac1) with bleb-length measurement via a segmented-line ROI in Fiji; actin coherency via the OrientationJ Fiji macro. **→ Fig. 3d–h**.
4. In vitro actin co-sedimentation binding assay — SDS-PAGE/western blot band-intensity quantification in ImageJ, curve fitting in GraphPad Prism (two different versions cited — 10.2.3 and 8.0.2 — for different analyses). **→ Fig. 3b,f–h**.

```{note} Ambiguities and gaps
:class: dropdown
The cryo-EM data (EMDB/PDB depositions) are genuine public image-derived data meeting category (a), but this should not be conflated with the fluorescence-microscopy image data underlying the cell-biology figures (Fig. 2b; Extended Data Figs. 4–6), which are only covered by the generic "available...on reasonable request" clause and never explicitly named as images. GraphPad Prism version numbers are inconsistent (10.2.3 vs. 8.0.2) for different analyses in the same paper. The "phylogenicity" GitHub repository lacks a Zenodo archival DOI, unlike the paper's other two code repositories.
```

```{admonition} Verbatim quotes
:class: note
"Single-particle helical reconstruction was performed using Relion 4 (ref. 113)." — "Localization of peptides to actin filaments at podosomes was evaluated using Poji126. The Poji macro is a semi-automated ImageJ/Fiji plugin created to characterize protein distribution and enrichment at podosomes." — "Coordinates and cryo-EM maps for the actin filament structure have been deposited in the Electron Microscopy Data Bank (EMDB) under the accession code EMD-18866, with corresponding Protein Data Bank (PDB) entry 8R3H."
```

- **Software named**: RELION 4.0, CryoSPARC, ChimeraX 1.7, ImageJ, Poji (unversioned plugin), GraphPad Prism 10.2.3 / 8.0.2 (inconsistent), GROMACS 2022.4, IQ-TREE 2.
- **Code repository**: `github.com/thp42/slimfold` + Zenodo (SLiMFold pipeline); `github.com/thp42/psfm` + Zenodo (PSFM code); `github.com/thp42/phylogenicity` (GitHub only, no Zenodo). All computational/bioinformatic, not the fluorescence-microscopy pipeline.
- **Sample image data**: **Category (a) for cryo-EM data only.** EMDB/PDB accessions (EMD-18866/PDB 8R3H; EMD-53133/PDB 9QGK; EMD-54871/PDB 9SGK) explicitly name cryo-EM maps with resolvable accessions. The paper's fluorescence/confocal micrographs are not covered by any image-specific statement and would independently classify as (c).
- **Based on prior methods**: Nearly every computational tool (ColabFold, RELION, CryoSPARC, ChimeraX, ISOLDE, Phenix, PIVLab-equivalent tools) and the Poji plugin are cited to prior publications. The overall SLiMFold pipeline architecture, the PSFM generation code, and the RMSD/angle structural-comparison metrics are presented as the authors' own development.

(ero1a-glioblastoma-mam)=
## ERO1α fosters glioblastoma aggressiveness and metabolic flexibility by regulating mitochondria-associated membrane dynamics

Arthur Bassot et al. — *Nature Cell Biology*, Volume 28, pages 1496–1512 (2026). [doi:10.1038/s41556-026-01980-2](doi:10.1038/s41556-026-01980-2)

1. Immunofluorescence colocalization of ER (ERp57) and mitochondria (MitoTracker CMXRos) — confocal Zeiss 880/Opera-Phenix. **→ Fig. 3a,b**.
2. Mitochondrial network morphology (length, width, area) via Opera-Phenix + Harmony automated software. **→ Fig. 3i**.
3. TEM quantification of MAM ultrastructure (ER length, mitochondrial circumference, ER–mitochondria distance, contact number/length) using Fiji with a custom macro shared informally by collaborators (Rieusset/Hajnoczky/Csordas labs), not the authors' own published tool. **→ Fig. 3c–g; Fig. 7g,h,i** (also Extended Data Figs. 4a–c, 7e–h, 8a).
4. Proximity ligation assay (IP3R3–VDAC1) on Opera-Phenix, quantified automatically with Harmony. **→ Fig. 3j,k**.
5. Live-cell Ca²⁺ imaging (Fluo-8, Mito-R-GECO, erGAP1, 4mtD3cpv) — ratio/peak quantification via the Fiji "time series analyser" tool. **→ Fig. 4a,b; Fig. 6h–j; Fig. 7j,k**.
6. Zebrafish xenograft brain-tumour imaging (confocal ZEISS 980, Thunder 3D imager) — tumour area quantified with ImageJ. **→ Fig. 8f,g**.

```{note} Ambiguities and gaps
:class: dropdown
The custom TEM-analysis macro used for the paper's core MAM-quantification method is mentioned only in the Acknowledgements ("for sharing their macro to analyse ER–mitochondria interactions by TEM") — not in the Methods EM subsection, its exact algorithm/parameters are never described, and it is neither deposited nor offered on request. Fiji and ImageJ are used interchangeably across Methods subsections without version numbers for either. Three assays (FRET/FEMP imaging, CellROX/MitoSOX ROS measurement, roGFP2 redox imaging) are described in Methods but could not be tied to an explicit figure panel in the legends searched.
```

```{admonition} Verbatim quotes
:class: note
"Fiji software (NIH) was used to quantify ER length, mitochondria circumference, distance between ER and mitochondria (up to 50 nm), as well as contact number and length of contacts. Here, a minimum of 60 pictures were taken per condition, and at least 100 cells were analysed per group." — "Mitochondrial length, width and area were quantified automatically using Harmony software." — Acknowledgements: "we thank... J. Rieusset, G. Hajnoczky and G. Csordas (Thomas Jefferson Institute)... for sharing their macro to analyse ER–mitochondria interactions by TEM."
```

- **Software named**: Fiji/ImageJ (unversioned, used interchangeably), Harmony ("3.5" given once, otherwise unversioned), GraphPad Prism (unversioned), DIA-NN v1.8.1.
- **Code repository**: None found. The custom TEM macro is informally shared by collaborators, not deposited or offered on request.
- **Sample image data**: Not stated for image data specifically (category c). PRIDE/Zenodo accessions cover proteomics/lipidomics only; "Source Data" and "all other data...on reasonable request" never name images/microscopy/EM data.
- **Based on prior methods**: MAM subcellular fractionation and TEM sample prep cite the authors' own prior paper (ref. 69). The TEM contact-site quantification macro itself is informally sourced from collaborators rather than a formally cited published method. Most Opera-Phenix/Harmony-based quantification workflows are presented as the authors' own uncited protocol.

(cd44-egfr-bleb-migration)=
## CD44 restricts EGFR mobility to polarize cytoskeletal signalling modules driving bleb-based migration

Ankita Jha et al. — *Nature Cell Biology*, Volume 28, pages 1408–1423 (2026). [doi:10.1038/s41556-026-01981-1](doi:10.1038/s41556-026-01981-1)

1. Cell trajectory tracking from time-lapse phase-contrast images — manual tracking (MTrackJ in Fiji), MSD via the "Diper" Excel plug-in, persistence/diffusion coefficients in GraphPad Prism. **→ Fig. 1c–q; Fig. 7d–h**.
2. Normalized fluorescence-intensity line-scan/polarity-index analysis of EGFR–GFP and multiple biosensors — segmented-line ROI in Fiji, PI = (Ifront−Irear)/(Ifront+Irear). **→ Fig. 2c,e,g–i,k,m; Fig. 3b,c; Fig. 4d,i,j; Fig. 5h,i; Fig. 6b,i; Fig. 7b**.
3. Optogenetic photoactivation (Opto-EGFR, PA-Rac1) bleb-length measurement in Fiji; actin coherency via OrientationJ. **→ Fig. 3d–h**.
4. FRAP experiments (spot/rectangular/whole-bleb), normalized/fit via EasyFRAP-web; diffusion coefficient via the Soumpasis equation. **→ Fig. 4e–h; Fig. 5d–f; Fig. 6c–e**.
5. Particle image velocimetry (PIV) of actin retrograde flow via PIVLab in MATLAB, manual cell-body masking. **→ Fig. 4b,c**.

```{note} Ambiguities and gaps
:class: dropdown
No image-analysis software version numbers are given for Fiji/ImageJ, MTrackJ, Diper, OrientationJ, PIVLab, Origin, GraphPad Prism, or EasyFRAP-web — only ZenBlack (v2.3) carries a version. Immunoblot images (e.g., Extended Data Fig. 1L,M) are shown without a stated quantification method, unclear if densitometry was performed. The Code Availability statement defers the mathematical model's algorithm to the Methods/Supplementary text in prose form only, rather than depositing executable code — "Mathematical algorithms used are provided in the methods and in the supplementary text."
```

```{admonition} Verbatim quotes
:class: note
"Cell trajectories were manually tracked in Fiji using the Manual Tracking plug-in (MTrackJ77)... The tracking coordinates were exported to Diper78 (Microsoft Excel plug-in)." — "Fluorescence intensity profiles were measured using a segmented line ROI (10-pixel width) drawn from the base to the tip of each bleb." — "The extracted intensities from each ROI was then uploaded in EasyFRAP-web FRAP analysis tool79." — "The motion of the F-tractin–FR-labelled actin network was determined in consecutive frames ~6 s apart in PIVLab82 MATLAB (Mathworks)."
```

- **Software named**: Fiji/ImageJ, MTrackJ, Diper (Excel plug-in), Origin (Pro), GraphPad Prism, ZenBlack v2.3, NIS-Elements, OrientationJ, EasyFRAP-web, PIVLab in MATLAB.
- **Code repository**: None found. The Code Availability statement points only to the Methods/Supplementary text describing the mathematical model, not to deposited code.
- **Sample image data**: Not stated for image data specifically (category c). "Unprocessed immunoblots," "raw data," and "Source data" are all generic; images/micrographs are never explicitly named.
- **Based on prior methods**: MTrackJ, Diper, EasyFRAP-web, the Soumpasis equation, and PIVLab all cite prior published tools/equations (refs. 77–82). The segmented-line intensity profiling, polarity-index metric, and OrientationJ-based coherency workflow are presented as the authors' own uncited procedures.

(ecdna-segregation-mechanisms)=
## Cis and trans regulatory mechanisms of extrachromosomal DNA segregation

Yipeng Xie et al. — *Nature Cell Biology*, Volume 28, pages 1453–1463 (2026). [doi:10.1038/s41556-026-01982-0](doi:10.1038/s41556-026-01982-0)

1. **The paper's central and most-used readout — quantification of "detached ecDNAs" during mitosis by DNA FISH** (2-pixel-distance threshold from DAPI-stained chromosomes; dAUC/ECDF effect-size statistic) — acquired on a Zeiss Axio Observer 7 + Apotome 3, ZEN v3.4, but **no image-segmentation, spot-detection, or particle-analysis software is named anywhere in the text** for this core assay. **→ Fig. 1e** (schematic of the quantification strategy) **and used throughout Fig. 1f–i, Fig. 2b–h, Fig. 3b–g,j–n, Fig. 4b–d,f–g, Fig. 5e**, and numerous Extended Data figures.
2. Cellular/nuclear RNA-abundance quantification (RNase A dependency test) — Cell Navigator Live Cell RNA Imaging kit, quantified with ImageJ v1.54g. **→ Extended Data Fig. 7i,j**.
3. Live-cell time-lapse imaging of ecDNA segregation (TetR-mNeonGreen) on a Zeiss LSM 980 — no automated tracking software named, appears manual/representative-frame based. **→ Fig. 5a**.
4. Western blot band quantification — ImageQuant 800 imaging, Image Lab software v6.1.0. **→ multiple blot panels**.

```{note} Ambiguities and gaps
:class: dropdown
This is the most striking methods gap found across both NCB issues surveyed to date: the paper's single most-used analytical method — the "detached ecDNA" pixel-distance/FISH-signal-area/dAUC quantification underlying nearly every figure — has no dedicated Methods subsection and no named software/algorithm anywhere in the text; it is explained only conceptually in the Results and schematically in the Fig. 1e legend. There is also no Code availability heading in this article at all, and no statement that this custom pipeline's code is available even on request — a notable transparency gap for a paper whose quantitative claims rest almost entirely on this one method. No mention of blinding is made for the (implicitly manual) ecDNA-detachment or micronucleus scoring.
```

```{admonition} Verbatim quotes
:class: note
"Two orthogonal metrics were employed to assess ecDNA detachment per cell (Fig. 1e): (1) the number of detached ecDNAs and (2) the proportion of detached ecDNAs... calculating the difference in the area under the curve (dAUC), derived from the empirical cumulative distribution function." — "DNA FISH and immunofluorescence were imaged on the Zeiss Axio Observer 7 microscope equipped with the Apotome 3 optical sectioning module... processed using ZEN software (v3.4, Zeiss)." — "The RNA signal intensity was quantified with ImageJ (1.54 g)."
```

- **Software named**: fastp v0.22.0, HiC-Pro v3.1.0, HiCRep v0.2.6, FitHiC2 v2.0.8, deepTools v3.5.5, ZEN v3.4, ImageJ v1.54g, Image Lab v6.1.0, R v4.3.2 — every genomics tool is versioned, but **no** segmentation/spot-detection tool is named for the paper's central FISH-detachment assay.
- **Code repository**: None found; no Code availability heading exists in the article at all.
- **Sample image data**: Not stated for image data specifically (category c). SRA BioProject accession covers Hi-C/CUT&RUN/ChIP-seq only; "Source data are provided" never names images despite extensive FISH/immunofluorescence/live-cell imaging throughout.
- **Based on prior methods**: The Hi-C/ChIP-seq computational pipeline components are all cited to prior publications. The core ecDNA-detachment FISH quantification method (pixel threshold, A1/A2 signal-area metric, dAUC statistic) is presented entirely in the authors' own words with no citation to a prior published quantification method.

(med4-metastatic-dormancy)=
## Mediator subunit MED4 enforces metastatic dormancy in breast cancer

Seongyeon S. Bae et al. — *Nature Cell Biology*, Volume 28, pages 1513–1528 (2026). [doi:10.1038/s41556-026-01984-y](doi:10.1038/s41556-026-01984-y)

1. In vivo bioluminescence imaging (IVIS Spectrum, Living Image software) of metastatic burden. **→ Fig. 1e,i,j,k,l; Fig. 6f**.
2. HP1α heterochromatin-compaction quantification — "HP1α-positive area normalized to nuclear area" at the single-cell level; **no image-analysis software is named anywhere for this or any other immunofluorescence quantification step in the paper.** **→ Fig. 2d** (also Extended Data Fig. 2g,h).
3. Focal-adhesion density/area-fraction quantification (vinculin/paxillin/p-FAK). **→ Fig. 4c** (also Extended Data Fig. 6b–e).
4. Nuclear:cytoplasmic ratio (YAP, MRTF-A) via "DAPI-based nuclear masks" — masking/segmentation software unnamed. **→ Fig. 4g; Fig. 6a–d**.
5. Pericellular Collagen I and α-SMA shell-intensity quantification (5-µm and 2-µm shells around GFP+ lesions). **→ Fig. 5g–j** (also Extended Data Fig. 8a,b,d,e).

```{note} Ambiguities and gaps
:class: dropdown
No dedicated "Image acquisition" or "Image analysis" Methods subsection exists in this paper at all; every immunofluorescence quantification step (HP1α area, focal-adhesion metrics, nuclear:cytoplasmic ratios, pericellular shell intensities, radial gradients) is described only briefly with no attribution to any named software, macro, or algorithm — a striking omission given the paper's heavy reliance on such quantitative imaging metrics. Microscope hardware (confocal/widefield/slide-scanner make and model) is never specified anywhere, despite tile-scan/montage imaging being described. Colony/sphere/migration counting is explicitly manual throughout.
```

```{admonition} Verbatim quotes
:class: note
"Heterochromatin compaction was quantified as the HP1α-positive area normalized to nuclear area." — "The YAP and MRTF-A nuclear-to-cytoplasmic ratios were calculated using DAPI-based nuclear masks; a nuclear-to-cytoplasmic ratio > 1 was defined as nuclear accumulation." — "Pericellular Collagen I was quantified within a 5-µm shell surrounding GFP+ lesions. α-SMA redistribution was quantified as the ratio of α-SMA signal in a 2-µm pericellular shell to intracellular α-SMA signal." — Code availability: "All computational analyses were performed using publicly available tools... No custom code was generated for this study."
```

- **Software named**: Living Image (PerkinElmer), ChemiDoc (Bio-Rad), GraphPad Prism 8, Morpheus (online), and a standard genomics pipeline (BWA, MACS2, deepTools, ChromHMM, HOMER, DESeq2). **No dedicated microscopy/bioimage-analysis software (ImageJ, Fiji, QuPath, CellProfiler, Imaris, etc.) is named anywhere** for the extensive immunofluorescence/immunohistochemistry quantification.
- **Code repository**: None found; the Code Availability statement explicitly states no custom code was generated.
- **Sample image data**: Not stated for image data specifically (category c). GEO/EGA accessions cover RNA-seq/ATAC-seq/ChIP-seq only; "unprocessed blots and gels" and "Source data" never name images/microscopy data.
- **Based on prior methods**: The in vivo screening strategy, ATAC-seq, and ChIP-seq protocols are all cited to prior published work. Every image-quantification metric in the paper (HP1α area fraction, focal-adhesion metrics, nuclear:cytoplasmic ratio, pericellular shell intensities, radial stromal gradients) is presented without citation to a prior published method or software tool.

(tead1-heterochromatin-condensates)=
## TEAD1 condensates are transcriptionally inactive storage sites on the pericentromeric heterochromatin in cancer cells

Yiran Wang et al. — *Nature Cell Biology*, Volume 28, pages 1480–1495 (2026). [doi:10.1038/s41556-026-01985-x](doi:10.1038/s41556-026-01985-x)

1. TEAD1 condensate 3D nuclear/nucleolar/perinuclear localization — Zeiss LSM 900 + Airyscan 2, 3D analysis in Zeiss Zen. **→ Fig. 1c–f**.
2. TEAD1 condensate appearance-rate/count quantification — CellProfiler v4.2.8, Hoechst nuclear segmentation and TEAD1-condensate thresholding, manual false-positive screening. (Not explicitly cross-referenced to a specific panel in the Methods text.)
3. Colocalization (Manders' coefficient) of TEAD1 with heterochromatin/nuclear-body markers — Fiji with the BIOP-JACoP plugin. **→ Fig. 3c,d** (also Extended Data Figs. 3, 4).
4. 3D nearest-neighbour distance analysis (TEAD1 condensates to CENP-A or TRF2) — ImageJ plugin Distance Analysis (DiAna). **→ Fig. 3i–l**.
5. 3D object surface detection/classification — Imaris v10.2.0. **→ Fig. 2h,k,l; Fig. 6a–d**.
6. FRAP quantification with custom normalization and curve fitting via the third-party GitHub tool "frapplot." **→ Fig. 1g–j**.
7. Single-particle tracking of TEAD1-Halo molecules — nuclear masking via a custom ImageJ macro using Trainable Weka Segmentation; localization/tracking via SLIMfast (MTT algorithm). **→ Fig. 6e–h**.

```{note} Ambiguities and gaps
:class: dropdown
GraphPad Prism is cited with two different versions in the same paper (v10.1.1 and v10.6.0). CellProfiler-based condensate quantification is never tied to a specific figure/panel number in the Methods text. One instance of "Zeiss Zen software" is garbled by an apparent PDF-column-merge artifact ("1071 Zeiss Zen software"). Most core imaging tools (Fiji, ImageJ, DiAna, SLIMfast) lack version numbers despite the paper's ChIP-seq/RNA-seq pipeline components being consistently versioned.
```

```{admonition} Verbatim quotes
:class: note
"Cellprofiler (v.4.2.8) was used to identify both cell counts and the appearance of TEAD condensates. Using Hoechst as a nuclear marker, we used Cellprofiler to identify the nuclei as objects." — "3D distance analysis of TEAD1 condensates with CENP-A or TRF2 was performed using the ImageJ plugin Distance Analysis (DiAna)83." — "Localization and tracking of single molecules were performed using SLIMfast, a GUI implementation of a previously described MTT algorithm93." — "All codes associated with this manuscript have been deposited into GitHub (`https://github.com/BMBCaiLab/TEAD1-NCB-paper.git`)." — "Source imaging data have been published and available from the Johns Hopkins Research Data Repository (`https://doi.org/10.7281/T1LFLQL2`)."
```

- **Software named**: Fiji + BIOP-JACoP plugin, ImageJ + DiAna plugin, Imaris v10.2.0, CellProfiler v4.2.8, Trainable Weka Segmentation, SLIMfast, frapplot (third-party GitHub tool).
- **Code repository**: `github.com/BMBCaiLab/TEAD1-NCB-paper.git` — explicit, public, and covers "all codes associated with this manuscript."
- **Sample image data**: **Category (a)** — the Data Availability statement explicitly names "Source imaging data" deposited at the Johns Hopkins Research Data Repository with a resolvable DOI (`10.7281/T1LFLQL2`), distinct from the paper's separate sequencing (SRA/GEO) and proteomics (PRIDE) accessions.
- **Based on prior methods**: BIOP-JACoP, DiAna, frapplot, and the SPT/MTT tracking algorithm are all cited to prior published tools (refs. 81–85, 92–94). The CellProfiler-based condensate-counting pipeline and the Imaris-based 3D surface-classification workflow are presented as the authors' own settings/parameters without a specific quantification-method citation.

(drp1-mid49-fission)=
## DRP1 and MID49 co-diffusion scans mitochondria for fission

Cristiana Zollo et al. — *Nature Cell Biology*, Volume 28, pages 1393–1407 (2026). [doi:10.1038/s41556-026-01986-w](doi:10.1038/s41556-026-01986-w)

1. Mitochondrial diameter at fission sites — Fiji/ImageJ line-profile ROI, full-width-at-half-maximum (FWHM) calculation. **→ Fig. 1g**.
2. DRP1 particle tracking / 3D trajectory rendering — Imaris Surfaces segmentation + autoregressive motion-model tracking. **→ Fig. 1b,d,e,i; Fig. 2b**.
3. Tubular-model-based single-particle tracking and MSD calculation — custom Python (scikit-image/Otsu thresholding, Hungarian-algorithm linking via SciPy, cylindrical-coordinate projection). **→ Fig. 2a–c; Fig. 5d,i; Fig. 6a,f,h,m; Fig. 7l**.
4. Super-resolution structure classification (lines/arcs/rings/dots) via the Automated Structures Analysis Program (ASAP), a prior-published tool from the corresponding author's own lab. **→ Fig. 3d–h**.
5. Mitochondrial network morphology quantification (branch length, circularity, perimeter, area) via MitoSkel software (the authors' own prior-published tool), applied blinded. **→ Fig. 5e–h; Fig. 6b–e; Fig. 7b–e**.

```{note} Ambiguities and gaps
:class: dropdown
The mEOS photoconversion intensity-ratio tracking step (Fig. 2d–g) never names the software used to track particles or extract intensity ratios over time — only the acquisition instrument is given. The classification of DRP1 arrival events as "scanning" vs. "direct recruitment" (Fig. 5j–l) has no described segmentation/classification method. Several Methods-text reference numbers for computational steps (Hungarian algorithm, skeletonization, Savitzky–Golay filtering) appear to collide with reference numbers used elsewhere in the paper for unrelated DRP1-biology citations — likely a citation-numbering artifact rather than a genuine sourcing of these algorithms.
```

```{admonition} Verbatim quotes
:class: note
"The Python script developed for this study is available via GitHub at `https://github.com/YaPaKo/DRP1-Mito-Tracker`. DRP1 tracking was analysed using a cylindrical coordinate model, suitable for the tubular mitochondrial network." — "All mitochondrial morphology parameters, such as branch length, area, perimeter and circularity, were quantified using MitoSkel software." — "using automated structures analysis program (ASAP) analysis, classified as lines, arcs, rings and unresolved dots."
```

- **Software named**: Fiji/ImageJ, Imaris, MitoSkel (authors' own prior tool), ASAP (authors' own prior tool), scikit-image, SciPy v1.11.4, GROMACS 2025.1, GraphPad Prism v8.
- **Code repository**: `github.com/YaPaKo/DRP1-Mito-Tracker` — explicit, public, custom Python tracking/MSD code, named both in Methods and a dedicated Code availability statement.
- **Sample image data**: Not stated for image data specifically (category c). "Source data" and "all other data...on reasonable request" never name images/microscopy data explicitly, despite extensive SIM/STED content.
- **Based on prior methods**: MitoSkel and ASAP are both self-cited to the authors' own earlier published tools. The Otsu thresholding, Hungarian-algorithm linking, and `linear_sum_assignment` steps cite standard package documentation/methods papers. The FWHM diameter measurement, mEOS ratio analysis, and cross-correlation displacement analysis are presented as the authors' own uncited approaches.

(isr-mitochondrial-fitness)=
## Integrated stress response couples mitochondrial fitness with lineage reprogramming to drive cancer evolution

Shiqi Diao et al. — *Nature Cell Biology*, Volume 28, pages 1529–1544 (2026). [doi:10.1038/s41556-026-01991-z](doi:10.1038/s41556-026-01991-z)

1. TEM of mitochondrial ultrastructure (Hitachi H-7100, AMT Image Capture Engine v600.147) — mitochondrial density/area quantification, **with no image-analysis software named for the actual measurement** (only the acquisition software is given). **→ Fig. 5a,f; Extended Data Fig. 6h**.
2. Confocal DRP1–mitochondria colocalization (Nikon AX/R + NSPARC), quantified via Manders' coefficients in NIS-Elements. **→ Extended Data Fig. 6j**.
3. Immunohistochemistry (Ventana Discovery XT, Aperio AT Turbo scanner) of ONECUT2, 4E-BP1, CHCHD10, NKX2-1, ATF4 in mouse LUAD tumours — quantified in QuPath (version given as v0.5.0 in one section, v0.6.0 in another). **→ Fig. 3f; Extended Data Fig. 3d, 4g, 7d**.
4. p-eIF2α H-score-based stratification of a 469-patient human LUAD TMA cohort — **no antibody, staining protocol, scoring method, or software is described anywhere**, and this step is not tied to any single figure panel.

```{note} Ambiguities and gaps
:class: dropdown
QuPath's version is stated inconsistently (v0.5.0 vs. v0.6.0) between the Immunohistochemistry Methods paragraph and the Statistics section. GraphPad Prism is likewise given as both "v10.3.1" and simply "v10." The PDX-tumour IHC underlying Fig. 6f,g has no dedicated Methods paragraph at all (antibody, staining, and scoring are unstated). The p-eIF2α TMA stratification step is an orphaned analytical step with no described method and no figure-panel citation. No Code availability statement exists anywhere, despite an explicit mention of "custom scripts" for Scanpy/AnnData analysis.
```

```{admonition} Verbatim quotes
:class: note
"examined using a Hitachi H-7100 transmission electron microscope equipped with AMT Image Capture Engine software (version 600.147)." — "Colocalization was quantified in NIS-Elements using Manders' coefficients (M1 and M2)." — "Quantification was performed using QuPath (v0.5.0)." / "Statistical analyses were performed using R (v4.3.0), QuPath (v0.6.0) and GraphPad Prism (v10)." — "Samples were stratified into high and low p-eIF2α groups using the median H-score as a cut-off."
```

- **Software named**: AMT Image Capture Engine v600.147, NIS-Elements, Zen 3.2, QuPath v0.5.0/v0.6.0 (inconsistent), GraphPad Prism v10.3.1/v10 (inconsistent), GelCount, Cell Ranger, Seurat v5.0.0, Scanpy v1.11.0.
- **Code repository**: None found. No Code availability section exists despite explicit mention of "custom scripts" for single-cell analysis.
- **Sample image data**: Not stated for image data specifically (category c). GEO/PRIDE accessions cover RNA-seq/proteomics only; TMA cohort access is gated by a separate ethics/data-access committee, not a public accession; "Source data" and "all other data...on reasonable request" never name images.
- **Based on prior methods**: Ultrasound tumour imaging, AdV-Cre delivery, and the CellRank/pySCENIC single-cell pipeline all cite prior published methods. The TEM sample-prep protocol, confocal IF/Manders' colocalization workflow, and all IHC scoring protocols (mouse, KM-model, PDX, and human TMA) are presented without a citation for the imaging/quantification approach itself.

(clib-lipid-probe-screening)=
## Cell surface liposome binding (CLiB) allows lipid-binding probe engineering via high-throughput screening

Taki Nishimura et al. — *Nature Cell Biology*, Volume 28, pages 1574–1587 (2026, Technical Report). [doi:10.1038/s41556-026-01996-8](doi:10.1038/s41556-026-01996-8)

This paper's dominant quantitative pipelines are flow cytometry and NGS-based sequence counting; true bioimage (micrograph) analysis is a smaller, secondary component.

1. Confocal imaging of GFP-fused evolved probe clones in yeast (Olympus FV3000) — qualitative visual localization only, no quantitative pipeline. **→ Fig. 2b**.
2. Confocal imaging + a fully-named custom Fiji/ImageJ macro suite and R-script pipeline quantifying vacuolar-membrane GFP intensity and classifying ring-vs-punctate localization under hyperosmotic stress (Olympus FV4000). **→ Fig. 5a,c,d**.
3. Confocal/spinning-disk imaging of RAW264.7 macrophages under probe/drug treatment (Leica TCS SP8 / Olympus SpinSR10), with blinded manual counting of GFP-positive dot/ring structures in ImageJ/Fiji (files randomized before scoring). **→ Fig. 6, Fig. 7** (also Extended Data Figs. 7, 8).
4. Colocalization analysis (Pearson's correlation coefficient and Manders' M1) between probe and LAMP1-mRFP or MitoTracker/Dextran — **software used to compute the coefficients is never named**. **→ Fig. 6i** (also Extended Data Figs. 7e, 8e).

```{note} Ambiguities and gaps
:class: dropdown
Fig. 2b (confocal localization of evolved yeast clones) has no described quantitative pipeline — purely qualitative, unlike the more rigorous macro-based pipeline built for Fig. 5. The colocalization statistics reported in Fig. 6i and Extended Data Fig. 7e/8e never name the software/plugin used to compute Pearson's/Manders' coefficients. An "AlphaFold267" citation-superscript merge in the Extended Data Fig. 3 legend does not match any AlphaFold reference in the reference list — likely an OCR/typesetting artifact. Imaging-protocol parameter detail (light-microscopy conditions) is explicitly deferred to Supplementary Table 5, not included in this PDF.
```

```{admonition} Verbatim quotes
:class: note
"Confocal images were preprocessed and analysed using Fiji/ImageJ and R codes. Multichannel oir files were batch-converted to 16-bit calibrated TIFF images using the macro '0005_GR-DIC-file 16 bit.ijm'... Line-scan text files were then processed in R with the script '0013_Peak_analysis_Vac.R' to smooth vacuolar FM4-64 profiles, detect intensity peaks and calculate the mean GFP signal at each FM4-64 peak." — "The numbers of GFP dots and rings were analysed using the ImageJ software in Fiji (National Institutes of Health). For blinded quantification, the image files were randomly shuffled before analysis." — "The codes used to analyse imaging data are available via Zenodo at `https://doi.org/10.5281/zenodo.19718926` (ref. 68)."
```

- **Software named**: Fiji/ImageJ (unversioned, with individually-named custom macro files), Adobe Photoshop 2025 v26.0.0, FlowJo v10.10.0, GraphPad Prism 10, GROMACS 2022.6, PyMOL/APBS, Modeller, AlphaFold.
- **Code repository**: **Zenodo `https://doi.org/10.5281/zenodo.19718926`** — explicitly stated to include "the codes used to analyse imaging data," alongside FACS and MD simulation data. Public deposit, not "available upon request."
- **Sample image data**: **Category (a)** — the Data Availability statement explicitly names "imaging" data with a resolvable Zenodo DOI, distinct from the separately-accessioned lipidomics data (Metabolomics Workbench).
- **Based on prior methods**: The yeast electroporation protocol, MD-simulation workflow, and NGS read-processing steps (PEAR, Cutadapt) all cite prior published methods. The entire CLiB/HT-CLiB assay design, the custom Fiji-macro/R-script vacuolar-quantification pipeline, and the blinded dot/ring counting protocol are presented as the authors' own development, largely uncited beyond a self-citing footnote to the assay concept.

```{warning} Caveats
Unlike the previous NCB issue surveyed, this issue's papers are mostly genuine cell-biology/microscopy studies rather than genomics-heavy ones — but a distinct and recurring gap emerged instead: **several papers describe extensive quantitative immunofluorescence work (colocalization, area-fraction, intensity-ratio, and shell-based metrics) without ever naming the image-analysis software or algorithm used to compute it.** This is most severe in two papers: the MED4 metastatic-dormancy paper, where not a single dedicated bioimage-analysis tool (ImageJ, Fiji, QuPath, CellProfiler, Imaris, etc.) is named anywhere despite five distinct quantitative IF metrics being reported; and the ecDNA-segregation paper, where the single method underlying nearly every figure in the paper (the "detached ecDNA" pixel-distance/dAUC quantification) has no named software and no dedicated Methods subsection at all — only a conceptual description in the Results and a schematic in the Fig. 1e legend. The mitochondria–ER-iron-hub paper has a related but distinct gap: it performs multiple dual/triple-immunofluorescence experiments explicitly designed to demonstrate organelle colocalization, yet never computes or reports a colocalization coefficient (Pearson's/Manders') for any of them, relying only on qualitative representative images.

**Code availability**: three articles in this issue have genuine, publicly-posted code repositories that specifically cover bioimage-analysis pipelines — the TEAD1-condensates paper (GitHub, "all codes associated with this manuscript"), the DRP1/MID49-fission paper (GitHub, the custom Python single-particle-tracking script), and the CLiB paper (Zenodo, explicitly "the codes used to analyse imaging data"). A fourth article (short-linear-motifs/actin-binding) has three public code repositories, but all three cover computational/structural-biology pipelines (the SLiMFold and PSFM tools, a phylogenetics script) rather than the paper's fluorescence-microscopy quantification, which remains undeposited — consistent with the pattern already seen in the prior NCB issue where a public repository does not always mean the imaging pipeline itself is covered. The remaining eight articles have no code repository of any kind; two of these (MED4 dormancy; ecDNA segregation) have an explicit statement that no custom code was generated or simply omit a Code availability section altogether despite describing custom analytical formulas.

**Version-number gaps and inconsistencies** are widespread: three articles in this issue contain outright internal discrepancies between two different version numbers cited for the same software in different Methods subsections (lysosome-ADMA paper: Fiji v2.14.0 vs. v1.54p, and GraphPad Prism 10 vs. 7; short-linear-motifs paper: GraphPad Prism 10.2.3 vs. 8.0.2; TEAD1-condensates paper: GraphPad Prism v10.1.1 vs. v10.6.0; integrated-stress-response paper: QuPath v0.5.0 vs. v0.6.0, and GraphPad Prism v10.3.1 vs. v10). None of these discrepancies is explained or reconciled in the text.

**"Based on prior methods" scope**: as in prior issues, this designation is reserved for image-analysis or quantification steps with an explicit citation to a previously published protocol. Two articles in this issue (DRP1/MID49-fission; short-linear-motifs/actin-binding) notably self-cite the authors' own previously published tools (MitoSkel, ASAP; the Poji plugin is a genuine third-party prior tool) rather than presenting them as novel — a distinction from articles where the core quantification approach is entirely uncited.

**Figure-mapping ambiguities and gaps found**: the ERO1α/glioblastoma paper describes three assays (FRET/FEMP imaging, CellROX/MitoSOX ROS measurement, roGFP2 redox imaging) that could not be tied to any explicit figure panel in the legends searched. The integrated-stress-response paper has an orphaned analytical step (p-eIF2α H-score stratification of a 469-patient cohort) with no described method and no figure-panel citation at all. The DRP1/MID49 paper shows an apparent citation-numbering collision where computational-method reference numbers coincide with unrelated DRP1-biology citations elsewhere in the same reference list.

**Supplementary deferral check**: one article (CLiB) explicitly defers light-microscopy acquisition parameters to a Supplementary Table not included in this PDF ("Details of light microscopy conditions are provided in Supplementary Table 5") — a genuine methodological deferral. One article (CD44/EGFR bleb migration) defers parts of its mathematical-model derivation to a "Supplementary Note" and "Supplementary text 2." No other article in this issue defers image-analysis protocol detail specifically to Supplementary Information beyond generic table/figure/movie pointers.

**Sample image data availability tally for this issue**: 3 articles reach category (a) — the TEAD1-condensates paper (Johns Hopkins Research Data Repository, explicit "Source imaging data") and the CLiB paper (Zenodo, explicit "imaging" data) both fully qualify; the short-linear-motifs/actin-binding paper qualifies only for its cryo-EM structural data (EMDB/PDB), while its separate fluorescence-microscopy images remain in category (c) — this mixed case is flagged with an asterisk in the At-a-glance table rather than counted as a clean (a). 0 articles reach category (b). 9 articles fall into category (c) (a Data Availability statement exists but never explicitly names image/microscopy data, even where public accessions are given for sequencing, proteomics, or other omics data). 0 articles fall into category (d) — every article in this issue has at least a generic Data Availability statement.
```
