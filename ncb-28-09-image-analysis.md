---
title: "Nature Cell Biology, Volume 28, Issue 9 (10 articles)"
subtitle: "Bioimage analysis methods survey"
subject: Methods survey
date: 2026-09-27
---

```{note}
Methodology: each article PDF was converted to plain text with `pdftotext -layout` and searched for Methods subsections, software names, code-repository links, figure legends, and Data/Code availability statements. Figure and panel numbers were cross-checked against figure-legend text (authoritative over body-text parenthetical citations); Extended Data panels are distinguished from main-text Figures throughout. This issue of *Nature Cell Biology* skews heavily toward ChIP-seq/CUT&RUN-seq/RNA-seq/proteomics and computational structural modeling — several articles have little or no conventional bioimage (micrograph) analysis content, and this is reported explicitly (software/measurement target marked "None"/minimal) rather than omitted. The 4-way sample-image-data-availability classification is applied strictly: generic "data" or "Source data" language never counts as categories (a) or (b), even when the paper obviously contains microscopy images — only an explicit, resolvable public accession for image/microscopy data counts as (a), and only an explicit "available on request" statement naming images/microscopy data counts as (b).
```

## At a glance

| Article | DOI | Key imaging software | Version given? | Measurement target | Code repo | Sample image data |
|---|---|---|---|---|---|---|
| [Nuclear PI3K co-activates fasting chromatin remodelling](#pi3k-fasting-chromatin) | [doi:10.1038/s41556-026-02030-7](doi:10.1038/s41556-026-02030-7) | None named for quantified IF (ImageJ named only for blot densitometry, Reporting Summary only) | No (blot ImageJ: v2.1.0) | 1) Nuclear/total Vps15 intensity; 2) Vps15–RNAPII colocalization intensity | None | (c) |
| [PGAM1 as a metabolic–autophagy checkpoint](#pgam1-autophagy-checkpoint) | [doi:10.1038/s41556-026-02034-3](doi:10.1038/s41556-026-02034-3) | None named (puncta/co-localization scored by an unspecified method) | N/A | 1) % cells with ATG-puncta (GFP–Atg8, Atg9/13/14/38); 2) Gpm1/Atg9/Atg14/Atg17 co-localization; 3) mammalian ATG14 puncta per cell | None | (c) |
| [Nuclear-speckle periphery and long-lived intron-retained RNAs](#nuclear-speckle-periphery-introns) | [doi:10.1038/s41556-026-02040-5](doi:10.1038/s41556-026-02040-5) | ImageJ/Fiji; Big-FISH; Imaris (Bitplane) | Yes (v2.14.0/1.54f; v0.6.2; v11.0) | 1) smRNA FISH spot counts (nuclear/cytoplasmic fraction); 2) 3D distance of RNA signal to nuclear-speckle surface | GitHub (deep-learning/sequence-model code only — not the imaging pipeline) | (c) |
| [CLOCK/BMAL1 interactome and homeodomain factors](#clock-bmal1-interactome) | [doi:10.1038/s41556-026-02041-4](doi:10.1038/s41556-026-02041-4) | None (no microscopy at all; Image Lab Software for blot imaging only) | No (blot software version disputed — see Caveats) | None (ChIP–MS/ChIP-seq/RNA-seq paper; only AlphaFold3/ChimeraX structural renderings, not micrographs) | None | (c) |
| [OGDH defends against disulfidptosis via NRF2](#ogdh-disulfidptosis-nrf2) | [doi:10.1038/s41556-026-02042-3](doi:10.1038/s41556-026-02042-3) | ZEN 2.3 lite (Zeiss); Imaris (Bitplane); ImageJ | Yes (Imaris v9.2.0/X64 9.2.0; ImageJ v2.1.0) | 1) F-actin/phalloidin fluorescence; 2) Cell/cytoplasm volume (Imaris); 3) Tumour-microarray IHC score (manual, IRS) | None | (c) |
| [Mega-enhancers compartmentalize long genes in the brain](#mega-enhancers-long-genes) | [doi:10.1038/s41556-026-02043-2](doi:10.1038/s41556-026-02043-2) | ImageJ (custom 3D-FISH macros, undeposited); Cellpose-SAM | No | 1) 3D DNA-FISH spot detection and radial nuclear positioning; 2) Nucleus segmentation/volume; 3) Inter-spot 3D co-localization distance | GitHub (genome-modeling "IGM" software only — not the FISH imaging macros, which are undeposited) | (c) |
| [BRD4 recruitment into HP1 condensates desilences transcription](#brd4-hp1-condensates) | [doi:10.1038/s41556-026-02044-1](doi:10.1038/s41556-026-02044-1) | FIJI v1.53m (custom macro suite); MATLAB R2022b; Coloc2 | Yes (FIJI v1.53m; MATLAB R2022b) | 1) FXN active-transcription-site frequency and mRNA count per cell; 2) BRD4/HP1α intensity at transcription sites; 3) 3D BRD4–HP1α colocalization (Costes) | **Zenodo** — image processing code, image analysis code, **and raw microscopy images** | **(a)** |
| [Proportional mRNA/ribosome scaling controls cell growth](#mrna-ribosome-scaling) | [doi:10.1038/s41556-026-02045-0](doi:10.1038/s41556-026-02045-0) | ImageJ/TrackMate; Cell-ACDC (ACDC); scikit-image | No | 1) Single-ribosome/RNAP II diffusion coefficients (PALM/SMT); 2) Nuclear-to-cell volume fraction; 3) smFISH fluorescence concentration (mRNA) | GitHub (mathematical model/simulation code only — not the tracking/segmentation pipeline) | (c) |
| [Circadian control of tumour-derived EV secretion](#circadian-ctev-secretion) | [doi:10.1038/s41556-026-02047-y](doi:10.1038/s41556-026-02047-y) | ImageJ; SlideViewer | No | 1) FL intensity of ctEV-CLOCK signal on microfluidic chip; 2) Tumour-section IF/IHC quantification (CD31, HPSE, CD47, CD8+, Ki67) | None | (c) |
| [Elevated contractility drives implantation failure in aged-female embryos](#implantation-failure-aged-embryos) | [doi:10.1038/s41556-026-02052-1](doi:10.1038/s41556-026-02052-1) | ImageJ/FIJI; Imaris; ADAPT (FIJI plugin); custom Python (TFM) | No (except LuxBundle acquisition software v4.3.4) | 1) Trophectoderm spread area/velocity; 2) Cortical/junctional tension (micropipette + TFM); 3) Junctional and nuclear protein intensity (YAP, Cdx2/Sox2); 4) Cell-shape index; 5) Focal-adhesion length | **GitHub** (OakesLab/TFM — public, covers the traction-force-microscopy image-analysis code specifically) | **(b)** |

(pi3k-fasting-chromatin)=
## Nuclear class 3 PI3K co-activates fasting-specific chromatin remodelling

Nathaniel F. Henneman et al. — *Nature Cell Biology*, Volume 28, pages 1875–1889 (2026). [doi:10.1038/s41556-026-02030-7](doi:10.1038/s41556-026-02030-7)

This is predominantly a ChIP-seq/CUT&RUN-seq/RNA-seq chromatin-genomics study; genuine bioimage (micrograph) analysis is a minor component.

1. Genomic peak-calling, annotation and pathway analysis (Bowtie2, SAMtools, MACS2, DiffBind, ChIPseeker, clusterProfiler, deepTools2 heatmaps, IGV browser tracks) — computational tracks and heat maps, not micrographs. **→ Fig. 1a–f, Fig. 2, Fig. 4–6, Fig. 8b** (non-imaging).
2. Immunoblot acquisition (ChemiDoc™ Imager) and densitometric quantification (ImageJ v2.1.0, stated only in the Reporting Summary). **→ Fig. 2b, Fig. 3b,g, Fig. 7c,i** (western blots, not fluorescence micrographs).
3. Immunofluorescence microscopy of nuclear/total Vps15 intensity and Vps15–RNAPII colocalization — no microscope model, staining protocol, or quantification software is named anywhere in the Methods text; only the figure legend describes the readout. **→ Extended Data Fig. 1e** (nuclear/total Vps15 intensity, n=10 cells) **and Extended Data Fig. 1f** (colocalization intensity profile).
4. Custom bioluminescence live-cell imaging (split-luciferase complementation) on an Olympus IX-81 with a Hamamatsu ImagEM EM-CCD camera and MetaMorph acquisition software — representative images only; the quantitative luminescence values plotted throughout the paper were instead measured on a separate well-plate reader (TriStar LB941), not from the displayed images. **→ Fig. 1g, Extended Data Fig. 3b**.

```{note} Ambiguities and gaps
:class: dropdown
No dedicated "Immunofluorescence"/"Image acquisition" Methods subsection exists despite several IF panels — fixation, antibody dilutions, microscope model, objective and imaging software are never stated. The quantification method for the two genuinely quantified IF panels (Extended Data Fig. 1e,f — nuclear/total intensity and colocalization) is not described at all (no software, ROI definition, or normalization given). Fig. 1g and Extended Data Fig. 3b show representative bioluminescence *images*, but the actual plotted luminescence values come from a separate plate-reader measurement, not from image analysis of those images — a point easy to misread. Panels created in BioRender (e.g., Fig. 1a top, Fig. 3a top, Fig. 5a, Fig. 8a/f) are schematics, not image-analysis outputs.
```

```{admonition} Verbatim quotes
:class: note
"Images were acquired on ChemiDocTM Imager (BioRad)." — "For live imaging of bioluminescence, a custom-made imaging system based on an inverted fluorescence microscope (IX-81; Olympus) was used. All images were obtained using a cooled EM-CCD camera (ImagEM; Hamamatsu Photonics) with a 20× objective lens (UPLSAPO20XO; Olympus)... A Metamorph software (Molecular Devices) was used to control all image acquisition." — Figure legend only: "e, Immunofluorescent microscopy of Vps15 in MEFs. Image analysis to identity [sic] nuclear/total Vps15 levels... f, ...Plot shows co-localization intensity between Vps15 and RNAPII in cross section of the nucleus."
```

- **Software named**: MACS2 v2.2.7.1, Bowtie2 v2.4.4, SAMtools v1.13, DiffBind v3.10.0, ChIPseeker v1.30.3, clusterProfiler v4.2.2, deepTools2, HISAT2, DESeq2, GSEA v4.2.2, ImageJ v2.1.0 (Reporting Summary only, blot densitometry), MetaMorph, TraceFinder, MetaboAnalyst 5.0. Most bioinformatics tools carry version numbers; the immunofluorescence step names no software at all.
- **Code repository**: None found. No GitHub/GitLab/Zenodo link appears anywhere for original study code.
- **Sample image data**: Not stated for image data specifically (category c). The Data Availability statement gives GEO accessions for ChIP-seq/CUT&RUN-seq/RNA-seq data only; microscopy/immunofluorescence/bioluminescence images fall only under the generic "all other data...available from the corresponding author on reasonable request" and "Source data" language, which never names images explicitly.
- **Based on prior methods**: ChIP and CUT&RUN protocols cite prior published work (refs. 61–64); the bioinformatics pipeline (Bowtie2/MACS2/DiffBind/etc.) uses established, cited public tools. The immunofluorescence acquisition/quantification and the custom bioluminescence imaging setup are presented without a methodological citation for the imaging/quantification step itself.

(pgam1-autophagy-checkpoint)=
## The glycolytic enzyme PGAM1 functions as a metabolic–autophagy checkpoint to coordinate growth and stress tolerance

Yi Zhang et al. — *Nature Cell Biology*, Volume 28, pages 1830–1845 (2026). [doi:10.1038/s41556-026-02034-3](doi:10.1038/s41556-026-02034-3)

1. Vacuolar GFP–Atg8 delivery (autophagic flux, % cells with vacuolar puncta) — fluorescence microscopy (Olympus IX83), manual cell scoring (n=100 cells/experiment). **→ Fig. 1c,d** (also Extended Data Fig. 1c,d).
2. ATG puncta formation (Atg1/9/13/14/38) and Atg9–Atg17 co-localization — fluorescence microscopy, manual scoring. **→ Fig. 2a–c** (also Extended Data Fig. 2).
3. BiFC assay for direct Gpm1–Atg9 and Gpm1–Atg14 interaction, and Gpm1–mCherry puncta/co-localization with Atg9–GFP — fluorescence microscopy. **→ Fig. 3d,e–h,l,m; Fig. 4b** (also Extended Data Figs. 3, 4).
4. Mammalian ATG14 puncta formation (mCherry–ATG14 puncta per cell) in PGAM1-knockdown U2OS cells and PGAM1–LC3 co-localization — confocal microscopy (Zeiss LSM 800), manual per-cell counting (n=10 cells/experiment, pooled to 30). **→ Fig. 6g–j; Fig. 7f,g** (also Extended Data Figs. 6, 7).
5. LC3 immunohistochemistry of xenograft tumour sections — described narratively as showing reduced/increased LC3 puncta between genotypes, but the legend states only "Representative staining images are shown," with no accompanying quantification panel. **→ Extended Data Fig. 8f,j** — flagged as a qualitative call, not a measured value.
6. Colony-formation (crystal violet) and xenograft tumour photography — manual counting/caliper measurement, not computational image analysis. **→ Fig. 8c,d,k,l,p,q; Fig. 8f,g,m,n**.

```{note} Ambiguities and gaps
:class: dropdown
No image-analysis/quantification software is named anywhere in this paper despite dozens of puncta-count and co-localization panels — it is never stated whether counting was manual or software-assisted (the word "manually" appears only for colony counting). No "Image acquisition"/"Image analysis" Methods subsection exists; imaging detail is limited to two brief sentences (Olympus IX83 for yeast; Zeiss LSM 800 for mammalian cells), with no objective, laser lines, or z-stack method given. Extended Data Fig. 8f/j (LC3 IHC) is discussed as showing a puncta-density difference but has no corresponding quantification graph.
```

```{admonition} Verbatim quotes
:class: note
"Imaging was performed using an Olympus IX83 inverted fluorescence microscope." — "The coverslips were subsequently mounted and fluorescence images were acquired using a Zeiss LSM 800 laser-scanning confocal microscope." — "The percentage of GFP–Atg8 degradation was determined by calculating the ratio of free GFP to total GFP signal, defined as GFP / (GFP + GFP–Atg8), and then normalized to the WT control." — Fig. 1 legend: "Data are the mean ± s.d. of three biologically independent experiments (n = 100 cells quantified per experiment, with a pooled total of 300 cells)."
```

- **Software named**: GraphPad Prism (v10.0.1). No dedicated bioimage/fluorescence-quantification software (no ImageJ, Fiji, CellProfiler, Imaris, MetaMorph, NIS-Elements, Zen, etc.) is named anywhere, despite the extensive puncta-counting content.
- **Code repository**: None found. No custom code, script, or repository link anywhere in the text.
- **Sample image data**: Not stated for image data specifically (category c). Mass-spectrometry data are deposited (PRIDE/MassIVE accessions); "Source data are provided" and "all other data...available...on reasonable request" never name images or microscopy data explicitly.
- **Based on prior methods**: Yeast tagging (ref. 45), immunoblotting protocol (ref. 47), ALP assay (refs. 20, 48), BiFC methodology (ref. 23), PGAM1 activity assay (ref. 9) are all cited. The core fluorescence-microscopy puncta-scoring and co-localization procedures themselves are presented without a methodological citation for the imaging/quantification approach.

(nuclear-speckle-periphery-introns)=
## The periphery of nuclear speckles defines a spatially and temporally regulated compartment of long-lived intron-retained RNAs that resolves during mitosis

Josep Biayna et al. — *Nature Cell Biology*, Volume 28, pages 1857–1874 (2026). [doi:10.1038/s41556-026-02040-5](doi:10.1038/s41556-026-02040-5)

1. Single-molecule RNA FISH (exon+intron probes) to classify intron-retained vs. spliced transcripts — Nikon ECLIPSE Ti2 widefield microscope, NIS-Elements v5.11.03 acquisition, ImageJ v2.14.0/1.54f + DeconvolutionLab2 v2.1.2 deconvolution, Big-FISH v0.6.2 spot quantification (manual counting when spot number was low). **→ Fig. 1d–f** (also Extended Data Fig. 1b).
2. High-resolution widefield smRNA FISH + SC35/U2 immunofluorescence, with 3D spot/surface segmentation and shortest-distance-to-surface analysis in Imaris v11.0, mapping intron-retained-RNA localization relative to nuclear-speckle core/shell. **→ Fig. 4b–g** (also Extended Data Figs. 6, 7).
3. STED super-resolution imaging (Leica Stellaris 8 STED FALCON, 100×/1.4 NA), visualized/rendered in Imaris. **→ Fig. 4h** (maximum-intensity projection and 3D rendering).
4. siRNA knockdown of SON/SRRM2 followed by smRNA FISH + IF and Imaris-based quantification. **→ Fig. 5a–d** (also Extended Data Fig. 8a,c–e).
5. Cell-cycle-staged (PCNA-based) smRNA FISH across S/G2/M/early-G1 and kinase-inhibitor (DYRK3i/CLKi/CDK1i) perturbation imaging. **→ Fig. 6a–c; Fig. 7a,b** (also Extended Data Figs. 9, 10; Fig. 6a is a schematic, not a micrograph).
6. Deep-learning sequence model (Parnet, fine-tuned RBPNet) predicting intron half-life/retention, with CAM attribution and motif discovery (tf-modisco-lite, TomTom, UMAP) — entirely computational, no micrographs. **→ Fig. 3a–l** (non-imaging).

```{note} Ambiguities and gaps
:class: dropdown
A Zenodo DOI discrepancy exists between the Code-availability text (10.5281/zenodo.21135982) and the Reporting Summary's "Data analysis" field (zenodo.org/records/21135983) for what appears to be the same code deposit. Version numbers for several tools (ViennaRNA, trim_galore, STAR, samtools, MACS3, Bismark, tf-modisco-lite) appear only in the Reporting Summary, not the main-text Methods. The imaged retained intron for METTL3 could not be distinguished from an adjacent intron because probes were tiled across both — a caveat on quantification accuracy noted by the authors themselves. Fig. 2a and Fig. 6a are schematics, not micrographs, despite sitting among FISH-image-based figures.
```

```{admonition} Verbatim quotes
:class: note
"Vast-tools v2.5.1148 was used to calculate PIR and transcripts per million (TPM) values." — "Maximum intensity projections were generated using Nikon software (NIS-Elements version 5.11.03) and deconvolved in ImageJ (version 2.14.0/1.54f) using DeconvolutionLab2 plugin (version 2.1.2). Quantification of RNA FISH signal was performed using the 'Big-FISH' v0.6.2 Python package161 or manually when the number of RNA spots was low." — "The distances of intron smRNA FISH signals to the nearest nuclear speckle were measured in three dimensions in Imaris (Bitplane, version 11.0) using the 'Shortest Distance to Surfaces' function... SC35 or U2 signals were segmented independently as three-dimensional (3D) surfaces representing the SC35-positive nuclear speckle core and the U2-positive nuclear speckle shell."
```

- **Software named**: NIS-Elements v5.11.03, ImageJ v2.14.0/1.54f, DeconvolutionLab2 v2.1.2, Big-FISH v0.6.2, Imaris v11.0, Parnet 0.3.0, tf-modisco-lite v2.4.0, ViennaRNA v2.7.0, trim_galore v0.6.10, STAR v2.7.11b, samtools v1.23.1, MACS3 v3.0.4, Bismark v0.25.1. Nearly all core imaging and bioinformatics tools carry version numbers — one of the most completely versioned papers in this issue.
- **Code repository**: github.com/marsico-lab/IR_iPSCs (Zenodo-archived) and github.com/marsico-lab/parnet — but this covers only the Parnet deep-learning sequence model and its fine-tuning/attribution code, **not** the smFISH/Imaris imaging pipeline itself, for which no custom scripts or macros are separately deposited.
- **Sample image data**: Not stated for image data specifically (category c). The Data Availability statement gives accessions only for RNA-seq/TSA-seq/eCLIP/ssDRIP-seq data (GEO, ENCODE) and says generically "Source data are provided with this paper" — raw smRNA FISH or STED image files are never explicitly named.
- **Based on prior methods**: smRNA FISH protocol (refs. 147, 157–159), STED imaging "as previously described with several changes" (ref. 163), PCNA-based cell-cycle staging (ref. 145) are all cited. The Parnet fine-tuning/attribution pipeline, the intron half-life decay-fitting, and the Imaris-based 3D-distance-to-speckle analysis are presented as the authors' own approach.

(clock-bmal1-interactome)=
## CLOCK/BMAL1 interactome uncovers homeodomain factors as tissue regulators

Fatih Aygenli et al. — *Nature Cell Biology*, Volume 28, pages 1890–1900 (2026). [doi:10.1038/s41556-026-02041-4](doi:10.1038/s41556-026-02041-4)

This is a ChIP–MS/ChIP-seq/RNA-seq proteogenomics study with no conventional microscopy content at all.

1. Western blot band detection and densitometric quantification of BMAL1 normalized to ACTIN — ChemiDoc XRS+ acquisition, Image Lab Software. **→ Extended Data Fig. 7a–c** (immunoblots and bar-plot quantification; not tied to any main Figure).
2. AlphaFold 3 structure prediction of CLOCK/BMAL1 complexes with PROX1, HNF1B and HOXA5, visualized in ChimeraX — computational structural-model renderings, not micrographs. **→ Fig. 4g** (main-figure AlphaFold3 predictions with iPTM scores); **Extended Data Fig. 5a–c** (pLDDT-colored models and PAE matrices).
3. Genome-browser visualization of ChIP-seq occupancy (IGV v2.10.0) — image-like output, not bioimage analysis. **→ Extended Data Fig. 7e–g**.

```{note} Ambiguities and gaps
:class: dropdown
Software version discrepancy: the Methods body text states the gel images were "visualized using Image Lab Software 3.0," while the Reporting Summary instead lists "Bio-Rad ImageLab v6.1.0" — the two do not match. ChimeraX's version is given only in the Reporting Summary ("ChimeraX 1.9"), not the Methods text. The western blot band-intensity quantification (Extended Data Fig. 7c) has no described algorithm, ROI-selection method, or software distinct from the general acquisition/visualization mention. No "Code availability" section/heading exists at all in the main text (only the unfilled Reporting Summary template prompt about GitHub deposition is present).
```

```{admonition} Verbatim quote
:class: note
"Nitrocellulose membranes were blocked with 5% milk in TBS-T... Images were captured using the ChemidocTM XRS+ system and visualized using Image Lab Software 3.0." — "Protein complex structure predictions were carried out using AlphaFold 3... The best output model... was visualized and analysed using ChimeraX59."
```

- **Software named**: Image Lab Software 3.0 (Methods) / ImageLab v6.1.0 (Reporting Summary, discrepant), AlphaFold 3, ChimeraX (v1.9, Reporting Summary only), IGV v2.10.0, MaxQuant v2.1.1.0, DIA-NN 1.8.2/2.2.0, Perseus v1.6.15.0/v1.6.10.50, GraphPad Prism 8, Bowtie2 v2.5, Bedtools v2.31, HOMER v4.11, DESeq2 v1.38.2.
- **Code repository**: None found. No GitHub/GitLab/Zenodo link anywhere; no code availability statement of any kind beyond the generic, unfilled Reporting Summary boilerplate.
- **Sample image data**: Not stated for image data specifically (category c) — this paper is arguably not a bioimaging paper at all. The Data Availability statement gives PRIDE/ENA/GEO accessions for proteomics/RNA-seq/ChIP-seq data and states "Source data are provided," with no mention of images or micrographs anywhere.
- **Based on prior methods**: ChimeraX (ref. 59), AlphaFold 3 (ref. 43), MaxQuant (ref. 56) and StageTip (ref. 55) are all cited, established third-party tools. The western blot densitometry step and the overall ChIP–MS workflow are presented without a specific citation for the quantification step itself.

(ogdh-disulfidptosis-nrf2)=
## The mitochondria enzyme OGDH defends against disulfidptosis by licensing METTL3-regulated NRF2 translation

Xiao-yan Chen et al. — *Nature Cell Biology*, Volume 28, pages 1814–1829 (2026). [doi:10.1038/s41556-026-02042-3](doi:10.1038/s41556-026-02042-3)

1. F-actin cytoskeleton imaging (phalloidin/DAPI) — Zeiss LSM 780 confocal, ZEN 2.3 lite software. **→ Fig. 1f, Fig. 6d** (also Extended Data Fig. 1k–n, 3c,e).
2. Cell/cytoplasm volume quantification from confocal z-stacks of CM-H2DCFDA-labelled cells (Evident IXplore SpinSR microscope), volumes computed in Imaris (Bitplane) v9.2.0 — reported only as two summary numbers in the Methods text; **not tied to any numbered figure panel anywhere in the paper** — flagged as an orphaned method.
3. Immunohistochemistry of a melanoma tissue microarray and mouse tumour sections (Ki67) — Nikon ECLIPSE Ts2R/NIS-ElementsD v5.10 acquisition; quantified manually via the Immunoreactive Score (IRS, 0–12) by three blinded evaluators, not automated segmentation. **→ Fig. 7a,b,g,h; Fig. 8a–d** (also Extended Data Fig. 8d,n).
4. Western blot / RNA-EMSA gel densitometry quantified with ImageJ v2.1.0, explicitly named for the EMSA "fraction bound" Kd-determination curve. **→ Extended Data Fig. 5p**.

```{note} Ambiguities and gaps
:class: dropdown
GraphPad version discrepancy: Methods body text says "GraphPad v.9," while the Reporting Summary says "GraphPad Prism 10.3." The Imaris-based cell/cytoplasm-volume measurement is never tied to any figure panel anywhere in the text — a genuine orphaned-method gap. "Evidence IXplore SpinSR" is very likely an OCR/typo artifact for "Evident IXplore SpinSR" (an Evident/Olympus spinning-disk confocal system). No "Code availability" section/heading exists in the main text at all. ImageJ quantification of western blots is stated only generically in the Reporting Summary, without specifying which of the many blot-derived bar graphs across Figs. 1–8 it actually covers (only the EMSA Kd curve is explicitly tied to ImageJ in the Methods body).
```

```{admonition} Verbatim quotes
:class: note
"Images were acquired using a Zeiss LSM 780 confocal microscope and analysed with ZEN2.3 lite software." — "Average cell volumes (control sgRNA, 4,451 μm3; OGDH sgRNA1, 4,930 μm3) were determined using Imaris software (Bitplane) from axial image stacks of CM-H2DCFDA-labelled A375 cells acquired on an Evidence IXplore SpinSR." — "The immunohistochemistry (IHC) results were quantified using an IRS system63. IRSs (0–12) were calculated as the product of proportion (0–4) and intensity (0–3). Three blinded evaluators scored each sample, and the mean was used." — "Band intensities were quantified using ImageJ. The fraction of bound RNA was plotted against protein concentration and fitted with the binding model: Fbound = (Bmax × [protein])/(Kd + [protein])."
```

- **Software named**: ZEN2.3 lite, Imaris X64 9.2.0 (Bitplane), ImageJ v2.1.0, GraphPad (v9 in Methods / Prism 10.3 in Reporting Summary — discrepant), NIS-ElementsD v5.10, Proteome Discoverer v2.5, Skyline-daily v21.2.1.424, SynergyFinder (unversioned in Methods, "3.0" in the Fig. 7 legend), pySCENIC, AUCell, DESeq2 v1.48.1, clusterProfiler v4.16.0 (versions from Reporting Summary).
- **Code repository**: None found. No GitHub/GitLab/Zenodo link anywhere; no custom algorithm is claimed and none is described as available on request.
- **Sample image data**: Not stated for image data specifically (category c). RNA-seq (GEO), metabolomics (NMDR) and proteomics (PRIDE/OMIX) accessions are given; "all other data...on reasonable request" and "Source data are provided" never name images specifically.
- **Based on prior methods**: OGDH activity assay (ref. 57), CETSA (ref. 61), IRS scoring system (ref. 63), and ZIP synergy method (ref. 58) are all cited. The confocal imaging/ZEN quantification, the Imaris cell-volume measurement, and the ImageJ densitometry are described procedurally without a specific citation for the quantification approach itself.

(mega-enhancers-long-genes)=
## Mega-enhancers compartmentalize transcriptionally active long genes in the brain

Ziyu Zhao et al. — *Nature Cell Biology*, Volume 28, pages 1913–1926 (2026). [doi:10.1038/s41556-026-02043-2](doi:10.1038/s41556-026-02043-2)

1. Confocal DNA FISH + immunohistochemistry acquisition (Leica TCS SP8, ×63/1.40 NA, 0.3 µm z-stacks). **→ Fig. 3g (left), Fig. 4i, Fig. 6f** (micrographs); Extended Data Fig. 9a (descriptive only, not tied to quantification).
2. Automated 3D DNA-FISH spot detection with custom ImageJ macros ("previously described," refs. 22, 95); nucleus segmentation with Cellpose-SAM (mCherry–NLS marker, Otsu-thresholded). **→ Fig. 3g (right), Fig. 4j, Fig. 6g** (also Extended Data Fig. 5e,f).
3. Pairwise spot-distance/co-localization analysis (mutual-nearest-neighbour FISH centroid matching, <500 nm contact definition) and radial-positioning quantification (single mid-nucleus z-section, centroid-to-signal distance normalized 0–1). **→ Fig. 6g; Fig. 3g (right), Fig. 4j** (also Extended Data Fig. 6e).
4. seqFISH+ nuclear-envelope estimation (convex hull via the "alphashape" Python library) and homologous chromosome-copy tracing (Ward + Spectral clustering). **→ Fig. 3h,i** (also Extended Data Fig. 6a–d) — note: the "grey surface" nuclear envelope and point-cloud rendering here is a reconstructed/computed visualization, not a raw fluorescence micrograph.
5. Integrative Genome Modelling (IGM, custom software) generating 3D single-cell chromatin structures from Hi-C data, rendered in Chimera/ChimeraX. **→ Fig. 3e,f** (also Extended Data Fig. 5a–d) — simulated/modelled structures, not micrographs.

```{note} Ambiguities and gaps
:class: dropdown
The custom ImageJ macros used for all 3D DNA-FISH spot detection are never linked to a repository or stated as available on request — a genuine code-availability gap for a core image-analysis step. Many imaging tools lack version numbers (ImageJ, Cellpose-SAM, MATLAB, R, Python, scikit-learn, alphashape) while several genomics tools do (Seurat v4, DAVID v6.8, GENCODE vM11) — inconsistent version reporting. Fig. 3e and Fig. 3h are computationally rendered/reconstructed 3D structures (IGM-modelled or seqFISH+-derived point clouds), not raw fluorescence micrographs, and should not be mistaken for photographic images despite being figure "images."
```

```{admonition} Verbatim quotes
:class: note
"3D image stacks were acquired from lobule 4/5 or lobule 6a... DNA FISH spots were located using automated 3D spot identification with custom macros in ImageJ as previously described22,95." — "mCherry–NLS-labelled nuclei were segmented from 3D image stacks using Cellpose-SAM96... nuclei were retained if at least 20% of voxels exceeded a global Otsu threshold." — "The nuclear envelope for each cell was estimated by fitting a convex hull to all imaged loci in a single cell using the 'alphashape' Python library." — "Images were acquired at the Biological Imaging Facility on a confocal laser scanning microscope (Leica Microsystems, TCS SP8 confocal) using a ×63 objective lens (NA 1.40)."
```

- **Software named**: ImageJ (custom macros, unversioned), Cellpose-SAM (unversioned), alphashape (Python, unversioned), scikit-learn (AgglomerativeClustering/SpectralClustering), IGM software ("IGM_2.0"), Chimera/ChimeraX, HiC-Pro, Juicer/Juicebox, HiCCUPS, Arrowhead, MACS2, Homer, DAVID v6.8, Seurat v4.
- **Code repository**: github.com/alberlab/IGM_2.0 (authors' custom IGM genome-modeling code, publicly posted) — but this covers only the Hi-C-based structure-modeling software, **not** the custom ImageJ 3D-FISH spot-detection macros, which remain undeposited and unaddressed by the Code availability statement.
- **Sample image data**: Not stated for image data specifically (category c). The Data Availability statement names GEO/4DN accessions for sequencing data and generic "Source data are provided"; raw DNA-FISH/confocal image files are never explicitly addressed.
- **Based on prior methods**: The custom ImageJ 3D-FISH macros are cited as "previously described" (refs. 22, 95); Cellpose-SAM is a cited third-party tool (ref. 96); homologous-copy tracing follows "the original DNA seqFISH+ implementation" (ref. 63). The radial-position normalization scheme, the mutual-nearest-neighbour FISH matching, and the alphashape-based envelope estimation are presented as the authors' own approach.

(brd4-hp1-condensates)=
## BRD4 recruitment into HP1 condensates desilences transcription without erasure of repressive chromatin

Christopher J. Brandon et al. — *Nature Cell Biology*, Volume 28, pages 1846–1856 (2026). [doi:10.1038/s41556-026-02044-1](doi:10.1038/s41556-026-02044-1)

1. RNAScope multiplexed smFISH + immunofluorescence (BRD4, HP1α) of FXN active transcription sites (ATS) — Zeiss 980 Airyscan 2 (63×/1.40 NA, 16-bit, 0.2 µm z-step). **→ Fig. 2a** (also Extended Data Fig. 5a).
2. Custom FIJI v1.53m IJ1-macro pipeline for 3D nuclear/cytoplasm segmentation and RNA-spot counting (MakeMasks → EditMasks → CountSpots, using the "3D Maxima Finder" plugin). **→ Fig. 2b,c** ("cells with FXN ATS %" and "FXN mRNA per cell").
3. Per-spot protein-intensity measurement (SpotsConcentration1 macro, 7×7-pixel ROI at each RNA-spot coordinate vs. a random control ROI). **→ Fig. 2d–g** (BRD4 vs. HP1α intensity correlation at ATS).
4. 3D BRD4/HP1α colocalization pipeline (mcib3d "3D Nuclei Segmentation," "3D Simple Segmentation," Coloc2 plugin with Costes's regression threshold). **→ Extended Data Fig. 6** (BRD4/HP1α co-occurrence in puncta vs. non-punctate nucleoplasm).
5. Downstream FIJI-output quantification in MATLAB R2022b (background subtraction/normalization, RNA-intensity/ATS threshold calling, fold-change calculation). **→ Fig. 2b–g** (also Extended Data Figs. 5, 6).
6. Phase-separation/condensate live imaging (Nikon C2 confocal time-lapse; "Marianas 2" system for droplet imaging; Zeiss LSM980 Airyscan for super-resolution) — no image-analysis/segmentation software is named for the droplet-area/intensity quantification. **→ Fig. 3a,b,e,f,i,k,n,o** (Fig. 3c,h,l are explicit schematics, not micrographs) — flagged gap.
7. Custom "velocity/quiver plot" pseudo-velocity visualization of ChIP-seq signal (author-developed, matplotlib), later deposited on Zenodo as "SignalVelocity." **→ Fig. 1c (right)** — a computational vector-field visualization, not a micrograph.

```{note} Ambiguities and gaps
:class: dropdown
Main-text figure-citation error: the text states "A striking overlap in ChIP-seq profiles of BRD4 and HP1 was evident at these ZNF genes... (Extended Data Fig. 7)," but Extended Data Fig. 7's actual legend concerns droplet titration/MALDI-TOF/HPLC data, not ZNF gene ChIP-seq tracks — the ZNF333/ZNF77/RPL11 genome-browser panels described are actually in Extended Data Fig. 8. No image-analysis software is named for the in vitro condensate/droplet-area quantification in Fig. 3 (28,000+ and 15,000+ droplets counted) — only the imaging instruments are given. "Marianas 2" is an underspecified instrument name (likely a 3i Marianas spinning-disk confocal system) with no manufacturer stated. deepTools (multiBigwigSummary) is named only in a figure legend, never in the Methods body text.
```

```{admonition} Verbatim quotes
:class: note
"Automated 3D image analysis. Batch analysis was performed using FIJI (v.1.53m) IJ1 macros... Three-dimensional (3D) segmentation and 3D ROI plugins are from https://mcib3d.frama.io/3d-suite-imagej/ (ref. 64)." — "CountSpots_zeiss.ijm. Each image was opened along with its corresponding 2D composite ROI list... the '3D Maxima Finder' plugin was used to localize and count the spots within the nucleus and within the cytoplasm." — "The Coloc2 plugin was used to determine the colocalization coefficients of BRD4 and HP1α in either the HP1α punctaMask or the HP1α nonpunctaMask. For each analysis, Costes's regression was used to determine the threshold value." — "The image processing code, image analysis codes and raw microscopy images are available via Zenodo `https://doi.org/10.5281/zenodo.17592795` (ref. 73)."
```

- **Software named**: FIJI v1.53m, Bio-Formats plugin, mcib3d-suite/TANGO plugins ("3D Nuclei Segmentation," "3D Simple Segmentation," "3D Maxima Finder"), Coloc2, MATLAB R2022b, Prism, matplotlib. Core imaging software (FIJI, MATLAB) carries version numbers; individual plugins mostly do not.
- **Code repository**: **Zenodo `https://doi.org/10.5281/zenodo.17592795`** — explicitly stated to include "image processing code, image analysis codes and raw microscopy images"; a second Zenodo record (`10.5281/zenodo.17596297`) holds the separate ChIP-seq "SignalVelocity" code. No GitHub link is used anywhere in this paper.
- **Sample image data**: **Category (a)** — publicly deposited raw microscopy images with a resolvable DOI. Quote: "The image processing code, image analysis codes and raw microscopy images are available via Zenodo `https://doi.org/10.5281/zenodo.17592795`." This is the only article in this issue whose Data Availability statement explicitly names raw microscopy images alongside a public accession.
- **Based on prior methods**: RNAScope cites the original method (ref. 63); the RNA/protein image-quantification approach is "based off previously established protocols65–68" (Robinson-Thiewes 2020, Tsanov/Mueller FISH-quant papers, Raj 2008); the 3D segmentation plugins cite TANGO/mcib3d (ref. 64). The custom FIJI/MATLAB macro suite itself and the "velocity/quiver plot" algorithm are presented as the authors' own, novel development.

(mrna-ribosome-scaling)=
## The proportional scaling of mRNA and ribosome concentrations controls eukaryotic cell growth

Xin Gao et al. — *Nature Cell Biology*, Volume 28, pages 1901–1912 (2026). [doi:10.1038/s41556-026-02045-0](doi:10.1038/s41556-026-02045-0)

1. Live-cell PALM/single-molecule tracking (SMT) of Halo-tagged ribosomal subunits (RPS9A-Halo) on a Nikon N-STORM system. **→ Fig. 1c** (composite bright-field/fluorescence micrograph; Fig. 1b is an explicit schematic, not a micrograph).
2. Particle localization and trajectory tracking via TrackMate on ImageJ (Laplacian-of-Gaussian detection, max 2 µm inter-frame displacement, trajectories <9 steps discarded); diffusion coefficients from MSD, classified into active/inactive populations via a Gaussian mixture model (no package named). **→ Fig. 1d,e**; same pipeline applied to RPB1-Halo (**Fig. 4k,l**) and H2B-Halo (**Extended Data Fig. 6g**).
3. Widefield imaging of Pus1–eGFP nuclear marker (Zeiss Axio Observer.Z1, 63×/1.4 NA) with paired phase-contrast; automated cell-boundary segmentation (Cell-ACDC) and nuclear-region definition via a "custom Python algorithm"; cell volume modelled as a prolate spheroid (scikit-image for axis measurement). **→ Fig. 4i** (also Extended Data Fig. 6e,f).
4. Same ACDC-based segmentation applied to widefield smFISH images (T30 poly-dT probe) — fluorescence concentration = total cell fluorescence / cell volume. **→ Fig. 6e**.

```{note} Ambiguities and gaps
:class: dropdown
The Gaussian mixture model used to separate active/inactive ribosome diffusion populations is mentioned only in a figure legend, never described in the Methods body (no equations, package, or component count given). The public GitHub repository is explicitly scoped only to "modelling and simulations" — the actual image-analysis code (the custom Python nuclear-segmentation script, any TrackMate configuration, the GMM-fitting code) is not addressed by any code-availability statement, a real gap for non-trivial custom analysis steps. No version numbers are given for ImageJ, TrackMate, NIS-elements, Cell-ACDC, scikit-image, or MATLAB.
```

```{admonition} Verbatim quotes
:class: note
"Live-cell PALM was performed on a Nikon N-STORM microscope equipped with a Perfect Focus System and a motorized stage." — "After imaging, single-particle tracking was performed by Trackmate on ImageJ software. Molecules were localized in each frame using a Laplacian of Gaussian method with an estimated diameter of 1 µm." — "Cell boundaries were segmented automatically using ACDC software71 and manually calibrated, and nuclear regions were defined via a custom Python algorithm from fluorescence images." — "Cell boundaries were segmented automatically using ACDC software and then checked manually71. After background subtraction, T30 FISH fluorescence concentration was calculated as the sum of cellular fluorescence divided by cell volume."
```

- **Software named**: ImageJ/TrackMate, NIS-elements, Cell-ACDC (ref. 71), scikit-image, MATLAB (function fitnlm), FlowJo. None carry a version number in the main Methods text.
- **Code repository**: `https://github.com/skotheimlab/mRNA-ribosome-growth-ncb-2026.git` — explicitly scoped to "the modelling and simulations" only, **not** the image-analysis pipeline (TrackMate parameters, custom Python segmentation, GMM classification), which is described but not deposited or offered on request.
- **Sample image data**: Not stated for image data specifically (category c). The Data Availability statement covers RNA-seq/ribosome-footprinting/SLAM-seq (SRA) and proteomics (PRIDE) accessions plus generic "Source data are provided" — raw PALM/SMT movies and FISH micrographs are never mentioned.
- **Based on prior methods**: SMT approach cites prior work (ref. 29); Cell-ACDC is an explicitly cited third-party tool (ref. 71); SLAM-seq is "adapted from Alalam et al. with minor modifications" (ref. 54). The TrackMate tracking-parameter choices, the custom Python nuclear-segmentation algorithm, and the Gaussian mixture classification are presented without a specific prior-method citation.

(circadian-ctev-secretion)=
## Circadian control of circulating tumour-derived extracellular vesicle secretion affects targeted therapy efficacy

Mingying Chen et al. — *Nature Cell Biology*, Volume 28, pages 1927–1941 (2026). [doi:10.1038/s41556-026-02047-y](doi:10.1038/s41556-026-02047-y)

1. Fluorescence-intensity quantification of ctEV-CLOCK signal on a herringbone microfluidic capture chip — Nikon Ti−U fluorescence microscope, ImageJ for FL-intensity calculation (no version given). **→ Fig. 1e; Fig. 2a; Fig. 5g; Fig. 6a,b; Fig. 7c** (also Extended Data Figs. 2, 3, 4, 7, 8, 9).
2. Confocal imaging (Leica SP8-STED 3X) of EV-modified beads and tumour-tissue metabolic labelling (DBCO–Alexa 488), FL intensity via ImageJ. **→ Extended Data Fig. 1d–g; Fig. 6g**.
3. Immunofluorescence/IHC of tumour markers (CD31, HPSE, CD47, CD8+, Ki67) on tissue cryosections — viewed with SlideViewer software; the specific quantification algorithm for positive-area/cell counts is not named beyond "Data analysis was performed using SlideViewer software." **→ Fig. 5d–g; Fig. 7e–j,m–o; Fig. 8d–g**.
4. Flow cytometry (FlowJo) and nano-flow cytometry (Flow NanoAnalyzer U30E) of bead- and single-EV-level protein/particle signal. **→ Fig. 1a,b; Extended Data Fig. 5, 9**.
5. Scratch wound-healing (Nikon Ti−U) and crystal-violet Transwell migration/invasion imaging — instrument/software for area quantification not named; the wound-healing panel is not explicitly cross-referenced to a specific figure letter in the body text (flagged as an unclear figure tie). **→ Fig. 6e,f** (migration/invasion).

```{note} Ambiguities and gaps
:class: dropdown
No specific quantification algorithm/software is described for how the H&E/IHC positive-area or positive-cell counts were actually computed — "SlideViewer software" is a slide-viewing/scanning platform, not typically an automated quantification tool, and no thresholding/counting method is given. No ImageJ version number is stated anywhere. The scratch-assay figure attribution is ambiguous in the body text. A molecular-docking figure (AutoDock/PyMOL rendering of HPSE–OGT2115) is described in Methods but not tied to any main or Extended Data figure found in this PDF — likely a Supplementary Figure.
```

```{admonition} Verbatim quotes
:class: note
"Finally, the chip was imaged under a FL microscope (Nikon Ti−U), and the target EVs were identified on the basis of fluorescent signals. ImageJ was used to calculate FL intensity." — "Tumour sections were imaged using a confocal laser scanning microscope (Leica SP8-STED 3X). ImageJ was used to calculate the Alexa 488 FL intensity." — "After adding neutral gum to the slides, they were covered, and the sections were observed under a microscope. Data analysis was performed using SlideViewer software." — "The detailed experimental protocols have been deposited on protocols.io and are available at `https://doi.org/10.17504/protocols.io.5qpvojyj9g4o/v1`."
```

- **Software named**: ImageJ (unversioned), FlowJo, GraphPad Prism 10, SlideViewer, AutoCAD, AutoDock/AutoDockTools, PyMOL v2.5.0 (Schrödinger — the only versioned tool in this paper).
- **Code repository**: None found. No custom/in-house image-analysis code or script is described anywhere; all image-related tasks use named third-party commercial/free software with no bespoke pipeline.
- **Sample image data**: Not stated for image data specifically (category c). The Data Availability statement names a PRIDE accession for mass-spectrometry proteomics data only and says generically "Source data are provided with this paper" — images/microscopy data are never named.
- **Based on prior methods**: The herringbone microfluidic chip design and its surface functionalization are explicitly cited to the authors' own earlier work (ref. 50) and a protocols.io deposit (ref. 25). Molecular docking cites AutoDock4/AutoDockTools4 (ref. 55). The ctEV-CLOCK bioimage-readout steps themselves (ImageJ FL-intensity quantification, SlideViewer-based IHC quantification) are presented without a citation for the specific quantification approach.

```{note} Supplementary/external-protocol deferral
:class: dropdown
"The detailed experimental protocols have been deposited on protocols.io and are available at `https://doi.org/10.17504/protocols.io.5qpvojyj9g4o/v1`." This defers full step-by-step methodological detail — very likely including ImageJ ROI/threshold settings, exposure parameters, and the SlideViewer quantification workflow — to an external protocols.io document not included in this PDF. Functionally equivalent to the supplementary-methods deferrals seen in other issues' papers, though hosted on protocols.io rather than in a journal Supplementary Information PDF.
```

(implantation-failure-aged-embryos)=
## Elevated contractility drives implantation failure in mouse embryos from aged females

Kate E. Cavanaugh et al. — *Nature Cell Biology*, Volume 28, pages 1799–1813 (2026). [doi:10.1038/s41556-026-02052-1](doi:10.1038/s41556-026-02052-1)

1. Live confocal time-lapse imaging of blastocyst spreading (650-FastAct actin dye), thresholded/masked and particle-analysed in ImageJ, ROIs measured and exported to Excel. **→ Fig. 1d,e; Fig. 2b,c; Fig. 4f** (also Extended Data Figs. 1a,b, 4).
2. Trophectoderm perimeter/velocity kymograph analysis via the ADAPT ImageJ plugin. **→ Fig. 4b–d**.
3. Micropipette aspiration for cortical/surface tension (Fluigent system on a Leica DMi8; radius of curvature and Rp measured manually in FIJI; Young–Laplace calculation in Excel). **→ Fig. 3c; Fig. 5b** (also Extended Data Fig. 3a).
4. Traction force microscopy (TFM) on fluorescent-bead-embedded PAA gels — custom Python code (OpenCV optical-flow bead tracking; Fourier Transform Traction Cytometry, regularization 3.35×10⁻⁶). **→ Fig. 3d–g** (also Extended Data Fig. 3b,c).
5. Cell-shape-index (q) analysis of ZO-1-stained trophectoderm outlines — FIJI reslicing to orient the en-face plane, then custom Python code extracting cell perimeters/area. **→ Fig. 3i (mouse); Fig. 7c,d (human)** (also Extended Data Fig. 3f,g).
6. Junctional intensity quantification of tension markers (VD7, NMIIA/B, pMLC, α-catenin) — 3D surface rendering and "machine learning segmentation" in Imaris, ratiometric normalization in Excel. **→ Extended Data Fig. 2a–c**.
7. Nuclear intensity quantification (YAP, Cdx2/Sox2) — FIJI sum-intensity Z-projection, DAPI-based automated thresholding + watershed nuclear segmentation. **→ Fig. 6a–d**.
8. Focal-adhesion quantification from paxillin immunofluorescence — Imaris background subtraction/Gaussian smoothing, Surfaces-module segmentation, blinded to condition. **→ Fig. 4f**.

```{note} Ambiguities and gaps
:class: dropdown
The Methods text appears to duplicate a passage nearly verbatim (the "650-FastAct thresholded in ImageJ...exported to Excel" sentence) under two separate subsection headings — likely an editorial copy-paste artifact. Methods cites "Supplementary Fig. 2e" and "Supplementary Fig. 3c/e" for the model-fitting/traction-decay-length content, but this content corresponds to what the published figure legends call "Extended Data Fig. 3c/e" — a numbering mismatch that cannot be fully resolved from this PDF alone. No version numbers are given for FIJI/ImageJ, Imaris, GraphPad Prism, Matlab, Python, or OpenCV — only the LuxBundle acquisition software (v4.3.4) is versioned. Custom code for the cell-shape-index extraction, the TE-perimeter/velocity computation, and the physical-model fitting is not addressed in the Code availability section at all (only the TFM code and OpenCV are covered there).
```

```{admonition} Verbatim quotes
:class: note
"Traction forces were analysed using code written in Python (`https://github.com/OakesLab/TFM`) according to previously described work70... Bead displacement was calculated using an optical flow algorithm in OpenCV... with a window size of 8 pixels. Traction stresses were calculated using the Fourier Transform Traction Cytometry approach71 with a regularization parameter of 3.35 × 10−6." — "650-FastAct was then thresholded in ImageJ to generate an actin mask and then particle analysed to generate distinct ROIs for each timepoint." — "Nuclear protein intensities were quantified using FIJI (ImageJ, NIH)... Nuclei were identified on the basis of DAPI signal, and regions of interest (ROIs) corresponding to individual nuclei were generated using automated thresholding followed by watershed segmentation." — "All data supporting the findings of this study are available from the corresponding author on reasonable request. The raw live-imaging and microscopy datasets generated during the current study are several terabytes in size and therefore cannot be readily hosted in a public repository."
```

- **Software named**: ImageJ/FIJI, Imaris (Bitplane), ADAPT plugin, custom Python, OpenCV, Excel, GraphPad Prism, Matlab, LuxBundle software v4.3.4 (the only versioned tool named).
- **Code repository**: **`https://github.com/OakesLab/TFM`** — public, custom Python code for the traction-force-microscopy analysis specifically, explicitly named in both Methods and a dedicated Code-availability section. The cell-shape-index extraction code, the TE-perimeter/velocity code, and the physical-model-fitting code used elsewhere in this same paper are **not** covered by this or any other code-availability statement — a genuine gap alongside the one public repository.
- **Sample image data**: **Category (b)** — image data available on request only. Quote: "The raw live-imaging and microscopy datasets generated during the current study are several terabytes in size and therefore cannot be readily hosted in a public repository... available from the corresponding author on reasonable request." This explicitly names raw live-imaging/microscopy datasets as the subject of the on-request statement, meeting the (b) bar (no public accession is given, so it is not (a)).
- **Based on prior methods**: TFM analysis pipeline cites prior published work (refs. 70, 71); micropipette aspiration for cortical tension cites prior methodology (refs. 57, 62); the dimensionless cell-shape index q is a previously established metric (refs. 53, 54) applied here with the authors' own uncited segmentation code. The ImageJ actin-mask pipeline, the FIJI nuclear-intensity watershed pipeline, and the Imaris junctional/focal-adhesion pipelines are presented without a prior-method citation for the imaging steps themselves.

```{warning} Caveats
This issue is markedly more genomics/proteomics-heavy than the JCB and JCS issues surveyed previously in this series: three articles (CLOCK/BMAL1 interactome, PGAM1 checkpoint, and to a lesser extent the fasting-chromatin paper) have little to no true bioimage-analysis content — the CLOCK/BMAL1 paper is essentially a ChIP–MS/ChIP-seq/RNA-seq/AlphaFold-modeling study with no microscopy at all. This is reported explicitly in the At-a-glance table ("None"/minimal) rather than treated as an extraction gap.

**Code availability, more carefully distinguished than in prior issues**: three articles in this issue *do* have a public code repository, but in each case the deposited code does not cover the actual bioimage-analysis steps used in the paper — it is scoped instead to a deep-learning sequence model (nuclear-speckle-periphery paper, Parnet), a Hi-C-based genome-structure-modeling tool (mega-enhancers paper, IGM), or a mathematical growth model (mRNA/ribosome-scaling paper). Their genuine imaging pipelines (custom ImageJ/FISH macros, TrackMate configurations, custom Python segmentation) remain undeposited and are not addressed by any code-availability statement — a distinction worth flagging separately from "no code repository at all." Only two articles have a code repository that specifically covers bioimage-analysis code: the BRD4/HP1 condensates paper (Zenodo, explicitly bundling image processing/analysis code with raw microscopy images) and the implantation-failure paper (GitHub, for its traction-force-microscopy pipeline specifically, though several of that same paper's other custom image-analysis scripts are not covered).

**Version-number gaps** are widespread across this issue: core imaging tools such as ImageJ/FIJI, Imaris, TrackMate, Cellpose-SAM, Cell-ACDC and ADAPT are frequently used without any version number in the main Methods text, sometimes appearing versioned only in the Nature Portfolio Reporting Summary (a supplementary document that happened to be included at the end of several of these PDFs) rather than the article body itself. Two articles (CLOCK/BMAL1 interactome; OGDH/disulfidptosis) contain outright discrepancies between a software version stated in the Methods body and a different version stated in the Reporting Summary for the apparently same step (Image Lab Software 3.0 vs. ImageLab v6.1.0; GraphPad v.9 vs. GraphPad Prism 10.3).

**"Based on prior methods" scope**: as in prior issues, this designation is reserved for image-analysis or quantification steps with an explicit citation to a previously published protocol; established third-party software (ImageJ, Imaris, TrackMate, Cell-ACDC, AlphaFold, ChimeraX) used via its standard interface is treated as a cited tool, not as evidence the specific quantification approach was itself validated elsewhere, and several papers' core imaging-quantification steps (puncta scoring, colocalization thresholds, cell-shape extraction) are presented as the authors' own uncited approach even when using cited software.

**Figure-mapping ambiguities and errors found**: the BRD4/HP1 condensates paper contains a clear main-text figure-citation error (Extended Data Fig. 7 cited for ZNF-gene ChIP-seq tracks that actually appear in Extended Data Fig. 8). The implantation-failure paper's Methods cites "Supplementary Fig. 2e/3c/e" for content that the actual figure legends label "Extended Data Fig. 3c/e" — an apparent numbering mismatch not resolvable from this PDF. The OGDH/disulfidptosis paper's Imaris-based cell-volume measurement is never tied to any figure panel at all (an orphaned method). Several papers (nuclear PI3K/fasting-chromatin; mega-enhancers; mRNA/ribosome scaling) contain computationally rendered or reconstructed 3D structures (AlphaFold models, IGM/seqFISH+ point-cloud renderings) that appear as figure "images" but are not micrographs — these are flagged inline in each section so they are not miscounted as direct bioimage-analysis outputs.

**Supplementary/external-protocol deferral check**: no article in this issue defers image-analysis methodological detail to a journal Supplementary Information document specifically (all "Supplementary" pointers found are to data tables, reagent lists, or generic online-content boilerplate). One article (circadian ctEV secretion) instead defers its full experimental protocol — plausibly including image-acquisition and quantification parameters — to an external protocols.io deposit not included in this PDF, which is functionally the same kind of gap.

**Sample image data availability tally for this issue**: 1 article in category (a) (BRD4/HP1 condensates — Zenodo, explicit raw microscopy images with a public DOI); 1 article in category (b) (implantation failure in aged embryos — explicit on-request statement naming raw live-imaging/microscopy datasets); 8 articles in category (c) (Data Availability statement exists but never explicitly names image/microscopy data, using only generic "data"/"Source data" language even where public accessions are given for sequencing or proteomics data); 0 articles in category (d) (every article in this issue has at least a generic Data Availability statement).
```
