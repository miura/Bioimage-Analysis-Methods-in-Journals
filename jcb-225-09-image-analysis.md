---
title: "Journal of Cell Biology, Volume 225, Issue 9 (10 articles)"
subtitle: "Bioimage analysis methods survey"
subject: Methods survey
date: 2026-09-24
---

```{note}
This report was built by downloading each article's PDF, converting it to plain text with `pdftotext -layout`, and extracting the bioimage-analysis workflow for every paper by exact-string search (grep/sed) of the converted text — not by fetching the article live from the publisher. Figure/panel numbers were cross-checked against each figure's own legend (the legend is treated as authoritative when it conflicts with a body-text citation). Every article was also checked for (1) genuine deferral of image-analysis *methodological detail* to a separate supplementary-methods document not included in this PDF, and (2) whether the article's Data Availability statement specifically addresses sample/raw image data, versus generic "data" language, versus no such statement at all. Two of the ten articles in this issue ("Kinetochore clustering..." and "Meiotic CENP-C...") do not use conventional bioimage-analysis pipelines for every result shown — several data types (mass spectrometry, cryo-EM particle processing, molecular dynamics, flow cytometry) are included in the workflow lists below for completeness but are flagged as non-micrograph analyses where relevant.
```

## At a glance

| Article | DOI | Key imaging software | Version given? | Measurement target | Code repo | Sample image data |
|---|---|---|---|---|---|---|
| [EPHA2/CD44 endosomal trafficking](#epha2-cd44) | [doi:10.1083/jcb.202507217](doi:10.1083/jcb.202507217) | Fiji-ImageJ, Harmony, Imaris | Partial (discrepant between Methods text and reagent table) | 1) Tissue EPHA2/pEPHA2 intensity; 2) Spheroid volume/nuclei; 3) Vesicle colocalization (Pearson's); 4) Vesicle–nucleus distance binning; 5) ROS/lipid-peroxidation ratios; 6) 3D surface reconstruction; 7) G3BP1 condensates; 8) PLA spot counts | None found | Not stated for images |
| [CAST/ELKS–endophilin-A synaptic vesicle pools](#cast-elks-endophilin) | [doi:10.1083/jcb.202508077](doi:10.1083/jcb.202508077) | Fiji/ImageJ, SynActJ, MetaMorph, Coloc2 | No | 1) Ca2+ transients; 2) Glutamate release kinetics; 3) RRP/TRP pool size; 4) SV endocytosis/pH kinetics; 5) Condensate line-scan ratio; 6) FRAP; 7) STED puncta-to-AZ distance; 8) Colocalization (Pearson's) | None found | Not stated for images |
| [Piccolino tethers SVs to photoreceptor ribbons](#piccolino) | [doi:10.1083/jcb.202509110](doi:10.1083/jcb.202509110) | ImageJ/Fiji, GraphPad Prism, eTomo/3dmod | Partial (Prism 10 given; ImageJ/Fiji not) | 1) SR/AZ length; 2) SR height (TEM); 3) Vesicle-to-ribbon distance; 4) SV density (ribbon RP & reserve pool); 5) SV tethering classification (3D tomography); 6) Piccolino nanoscale localization; 7) Mitochondrial-targeting colocalization | None found | **On request** (explicit "imaging datasets") |
| [BIN1/SNX9 recruitment by junctional membrane curvature](#bin1-snx9) | [doi:10.1083/jcb.202509207](doi:10.1083/jcb.202509207) | Fiji 2.9.0, Ilastik 1.4.0, Imaris 10.2, TrackMate | Yes | 1) Membrane curvature mapping; 2) BAR-protein colocalization (Mander's); 3) BAR-GFP spot tracking; 4) AAJ recruitment delay/positivity %; 5) AAJ lifetime/length/straightness; 6) Wound closure/Golgi polarity; 7) CCV shape (zebrafish) | Third-party only (SIFT-alignment GitHub repo; adapted MATLAB File Exchange snippet) | **On request** (explicit "Source images") |
| [Intercellular mitochondrial transfer & trans-mitophagy](#mitochondrial-transfer) | [doi:10.1083/jcb.202511211](doi:10.1083/jcb.202511211) | Fiji/ImageJ (MIA plugin), Icy, FlowJo | No | 1) mitoTNT length/width; 2) Transferred-mitochondria size/MDB formation; 3) CLEM ultrastructure; 4) Ratiometric HyPer7 ROS; 5) Fluorescence decay kinetics; 6) LAMP1 colocalization (Mander's) | None found | **No Data Availability statement found** |
| [Meiotic CENP-C in spermatogenesis](#cenp-c-meiosis) | [doi:10.1083/jcb.202512053](doi:10.1083/jcb.202512053) | FIJI/ImageJ, softWoRx, GraphPad Prism | No | 1) Centromeric protein intensity; 2) FISH missegregation scoring; 3) Meiotic spindle morphology scoring; 4) Sperm nuclei assessment (qualitative) | None found | Not stated for images |
| [Mps1 phosphorylation of Stu1 MELT motifs](#stu1-mps1) | [doi:10.1083/jcb.202601143](doi:10.1083/jcb.202601143) | ImageJ (custom macro), PyMOL 3.0, AlphaFold2/3, cryoSPARC | Partial (PyMOL/Proteome Discoverer versioned; ImageJ macro not) | 1) Kinetochore (Mtw1) foci counts; 2) Kinetochore intensity/attachment status; 3) AlphaFold structural modeling; 4) MS phosphosite/kinase-motif mapping; 5) CryoEM particle processing | Third-party/adapted only (Zenodo phosphosite-parsing script; not image analysis) | Not stated for images |
| [GCL pruning of PIP3 at the soma–germline boundary](#gcl-pip3) | [doi:10.1083/jcb.202604036](doi:10.1083/jcb.202604036) | Cellpose-SAM/cyto3, Noise2Void, ImageJ Cell Counter | No (model names, not classic versions) | 1) PGC counting; 2) PIP3/PIP2/F-actin/myosin pole-bud intensity; 3) Myosin circumferential profile; 4) Pole bud height/width | None found | Not stated for images (borderline — see Caveats) |
| [Pi switches Arp2/3 branch stability](#arp23-phosphate) | [doi:10.1083/jcb.202605018](doi:10.1083/jcb.202605018) | None (no ImageJ/Fiji/MATLAB named); SciPy, lifelines, GROMACS 2023.2 | N/A for imaging | 1) Branch dissociation/renucleation scoring; 2) Survival curves (Kaplan–Meier); 3) Force-at-junction calculation; 4) MD residue-distance (Pi backdoor) | None found | Not stated for images |
| [Golgi–nucleus DNA-repair protein trafficking](#golgi-nucleus-repair) | [doi:10.1083/jcb.202605024](doi:10.1083/jcb.202605024) | CellProfiler, Fiji, OpenComet, GraphPad Prism 9 | Partial (Prism 9 given; CellProfiler/Fiji not) | 1) siRNA/antibody validation screen; 2) Golgi sub-compartment localization; 3) Golgi→nuclear redistribution ratio; 4) Foci colocalization; 5) Micronuclei scoring; 6) Comet assay; 7) DR-GFP reporter; 8) Colony-formation area | None found | Not stated for images |

(epha2-cd44)=
## EPHA2/CD44-directed trafficking enhances endosomal leakiness and antisense therapy delivery

Sergi Marco, Peter J. Walsh, Alexey S. Revenko, Tobias Schmidt, Peter A. Thomason, Lynn McGarry, A. Robert MacLeod, Sonam Ansel, Dina Tataran, Martin Bushell, Chiara Braconi, and Jim C. Norman — *Journal of Cell Biology*, Vol. 225, No. 9, e202507217 (2026). [doi:10.1083/jcb.202507217](doi:10.1083/jcb.202507217)

1. Mean-intensity quantification of EPHA2 and phospho-Ser897-EPHA2 immunofluorescence across patient/mouse tumor fields, using Fiji-ImageJ (2.6.0). **→ Fig. 1, A and B** (patient-sample quantification; the representative KPC-tumor image in Fig. 1 C is not itself stated as quantified).
2. High-content spheroid analysis of spheroid volume and nuclei count per spheroid, acquired on an Opera Phenix confocal and analyzed in Harmony High-Content Image analysis software (Revvity). **→ Fig. 1, F and G**.
3. Vesicle/endosome colocalization (Pearson's correlation coefficient) and fluorescence intensity line profiles between EPHA2/ASO and galectin-9/ASO, analyzed in Fiji-ImageJ from Zeiss Airyscan/Elyra7 SIM data. **→ Fig. 5, C and D**.
4. Vesicle-to-nucleus distance binning (proximal 0–1 µm vs. distal >1 µm) with log10-transformed pseudo-count density plots and z-scored fluorescence, using Harmony v5.2 acquisition/segmentation feeding a custom R/RStudio pipeline (R 4.5.0). **→ Fig. 2, B, C, F, and L; Fig. 5, E and F; Fig. S1 Q; Fig. S3, A–C, E–G.**
5. Nuclear/cytoplasmic CellROX ratio (ROS) and oxidized/reduced C11-BODIPY ratio (lipid peroxidation), quantified via the same Harmony + R/RStudio pipeline. **→ Fig. 4, A–D** (the representative Airyscan micrograph in Fig. 4 E is not itself stated as quantified).
6. 3D surface reconstruction of galectin-9/ASO/G3BP1-GFP overlap using Imaris (10.1.1) on SIM2-processed Elyra7 data. **→ Fig. 5 G; Fig. S3, D and L.**
7. G3BP1 stress-granule condensate quantification (percentage of cells with ≥1 condensate, foci per cell, condensate area). **→ Fig. 5, H and I; Fig. S3, E–G.**
8. Proximity ligation assay (PLA) spot counts per cell, analyzed in Fiji/ImageJ. **→ Fig. 3, J and K.**

```{note} Ambiguities and gaps flagged during extraction
:class: dropdown
- Fluorescence in situ hybridization (poly-d(T) probe, colocalization shown in Fig. 5 K) is named in Results and the figure legend, but Methods gives no dedicated protocol or software for it — the probe is listed only as a reagent.
- No step's Methods description specifies the actual segmentation/thresholding algorithm used to define a "vesicle" or "particle" in the Harmony/Fiji pipelines, nor the z-score normalization procedure.
- Fig. S3 N is an explicit hand-drawn "Diagram depicting the endocytic pathway" — a model schematic, not image-analysis output.
- Two software mentions carry conflicting version numbers between the Methods text and the reagents table: Harmony ("v5.2" in text vs. "4.9" in the table) and GraphPad Prism ("v10.5" in text vs. "10.3.1" in the table).
```

```{admonition} Verbatim quote
For distance/density-plot analysis: "For distance analysis, for each cell, vesicle distance to the nucleus was measured, and cells were binned into proximal groups (0–1 µm) and distal groups (from 1 µm to the maximum value). Then the mean fluorescence value for each particle was assessed for the corresponding markers such as EphA2, galectin-9, or ASO. Graphical representations and statistical analysis were performed using R version 4.5.0 within RStudio, running a custom pipeline for importing, harmonizing, and analyzing Opera Phenix/Harmony high-content imaging data."
```

- **Software named**: Fiji-ImageJ 2.6.0; Harmony High-Content Imaging and Analysis Software (v5.2 in text / 4.9 in reagents table); Columbus Image Data Storage and Analysis System 2.9.1 (reagents table only); Imaris 10.1.1; Zeiss Zen black 2.3 / Zen blue 2.3 / Zen Black 3.0; SIM2; GraphPad Prism (v10.5 in text / 10.3.1 in reagents table); R 4.5.0 with a named package stack (dplyr, readr, stringr, forcats, rlang, tidyr, ggplot2, ggridges, patchwork, colorspace, rstudioapi, rstatix, emmeans, lme4, lmerTest, multcomp); cBioPortal; GEPIA2.
- **Code repository**: None found. The custom R/RStudio pipeline for Opera Phenix/Harmony data is described narratively (with a package list) but is not stated to be deposited anywhere, nor offered upon request.
- **Sample image data**: Not stated for image data specifically (category c). Data Availability statement: "The data supporting the findings of this study are available within the article and its supplementary information files and from the corresponding author upon request." — generic "data" language with no mention of images/microscopy data specifically; a separate GEO accession (GSE179901) covers non-image RNA-seq data only.
- **Based on prior methods**: The fluorescence polarization binding assay is explicitly "adapted from previously established protocols (Bhattacharya et al., 2017)." All other quantification steps (tissue intensity measurement, spheroid volume/nuclei counting, vesicle colocalization/distance binning, ROS/lipid-peroxidation ratios, PLA counting, G3BP1 condensate counting, Imaris reconstruction, the custom R pipeline) are presented without citation to a prior quantification protocol.

(cast-elks-endophilin)=
## CAST/ELKS–endophilin-A interaction ensures synaptic vesicle pool size

Yasunori Mori, Hirokazu Sakamoto, Yeon-Jeong Kim, Shun Hamada, Fumihiro Kaku, Yamato Hida, Kenzo Hirose, and Toshihisa Ohtsuka — *Journal of Cell Biology*, Vol. 225, No. 9, e202508077 (2026). [doi:10.1083/jcb.202508077](doi:10.1083/jcb.202508077)

1. Presynaptic Ca²⁺ transients (Syn-GCaMP8s) and glutamate release (iGluSnFR3) quantified by automated analysis with the SynActJ plugin in Fiji (Schmied et al., 2021). **→ Fig. 1, B and C; Fig. 7, A and B.**
2. RRP size (iGluSnFR3 + sucrose), TRP size, surface SypHy fraction, and vesicular pH — manually analyzed in MetaMorph, as in the authors' own prior paper (Mori et al., 2021). **→ Fig. 1 D; Fig. 2, B and C; Fig. 8, B and C.**
3. SV release/endocytosis kinetics (SypHy fluorescence) via SynActJ/Fiji automated analysis. **→ Fig. 2 A; Fig. 7 A; Fig. 8 F.**
4. Co-condensate/phase-separation line-scan intensity ratio (condensate:cytosol) in HEK293T cells, quantified in FV1000 image software (Olympus). **→ Fig. 3, A and B; Fig. 6 C** (Fig. 6 A is an explicit schematic — "Cartoon image of the deletion and mutation constructs" — not image-analysis output).
5. FRAP of CAST/endophilin-A condensates, analyzed in Fiji. **→ Fig. 5 A.**
6. STED super-resolution distance quantification (endophilin-A1 puncta to the active-zone midline) via unsharp masking, binarization, and nearest-neighbor distance measurement — no software is named for this custom pipeline. **→ Fig. 5 C.**
7. Pearson's colocalization (ImageJ Coloc2 plugin) between CLC/dynamin-1/CHC/AP-2 and synaptophysin, endophilin-A1/synaptophysin, or CAST/Bassoon. **→ Fig. 7 C; Fig. 9, A–C; Fig. S1 B; Fig. S3 B; Fig. S4, D and E; Fig. S5, A–C.**
8. Western blot band-intensity quantification in Fiji. **→ Fig. 6 D; Fig. 8, A and E; Fig. 10, B and D.**

```{note} Ambiguities and gaps flagged during extraction
:class: dropdown
- The STED nanoscale-distance pipeline (unsharp masking/Gaussian blur/binarization/nearest-neighbor distance) is described step by step but no software platform is named for performing it.
- Fluorescence intensity line profiles "along the dotted lines" shown in several neuronal images (Fig. 7 C; Fig. 9, A and B; Fig. S3 B; Fig. S4 B) are named in figure legends but have no corresponding Methods description — the only line-scan method in Methods is specific to the HEK293T condensate assay.
- Bassoon puncta area (Fig. S4 D) and surface synaptotagmin-1 puncta counts (Fig. S1 B, "n = 225 puncta from 12 images") are both named in figure legends with no Methods description of the segmentation/detection method used.
```

```{admonition} Verbatim quote
"In the case of monitoring RRP size, TRP size, rise kinetics, surface expression level, and SV pH, acquired fluorescence images were manually analyzed using MetaMorph software, as described previously (Mori et al., 2021)."
```

- **Software named**: Fiji / ImageJ; SynActJ (Fiji plugin; Schmied et al., 2021); ImageJ Coloc2 plugin; MetaMorph (Molecular Devices); GraphPad Prism; FV1000 image software (Olympus); Leica LAS-X. No version numbers given for any of these.
- **Code repository**: None found. No custom analysis scripts are mentioned or linked anywhere in the document.
- **Sample image data**: Not stated for image data specifically (category c). Data Availability statement: "All relevant data that support the findings of this study are available from the corresponding authors upon request." — generic language, no explicit image/microscopy mention.
- **Based on prior methods**: SynActJ-based automated analysis cites Schmied et al., 2021 (the plugin's own paper); manual MetaMorph quantification is self-cited to the authors' prior paper (Mori et al., 2021); colocalization/statistical approach references Hamada et al., 2021. The condensate line-scan assay, FRAP protocol, STED distance pipeline, and western-blot quantification are all presented without a prior-methods citation.

(piccolino)=
## The missing link: Piccolino is essential for tethering synaptic vesicles to rod photoreceptor ribbons

Kaspar Gierke, Michalina Gadomska, Julia Breuer, Julius N. Bahr, Tanja M. Müller, Hanna Ehnis, Sina Zobel, Nancy Mejia Villagran, Sonja A. Kirsch, Alexandra Skrzypek, Renato Frischknecht, Anna Fejtová, Rainer A. Böckmann, Carolin Wichmann, Hanna Regus-Leidig, and Johann Helmut Brandstätter — *Journal of Cell Biology*, Vol. 225, No. 9, e202509110 (2026). [doi:10.1083/jcb.202509110](doi:10.1083/jcb.202509110)

1. Synaptic ribbon (SR) length (RIBEYE immunolabeling, CLSM) and active zone (AZ) length (Bassoon immunolabeling, CLSM) — no measurement software specified. **→ Fig. 1, F/F′/I (SR) and G/G′/K (AZ).**
2. SR height, measured manually on conventional TEM micrographs — no software specified. **→ Fig. 1, J/J′/J″.**
3. Distance of ribbon-associated synaptic vesicles (SVs) to the SR surface, via a straight-line fit through the ribbon center in ImageJ (points marked with the MultiPoint tool, coordinates exported via ROI Manager, distance computed by a point-to-line formula). **→ Fig. 2, A′, B, C, F, and G** (the same distance method, applied to immunogold puncta, underlies Fig. 3 E″).
4. SV density in the ribbon releasable pool (free-hand line marking the SR surface in ImageJ; SVs within 50 nm counted and divided by SR length, excluding the first 100 nm nearest the AZ) and in the cytoplasmic reserve pool (free-hand ROI around distant SVs, count divided by area). **→ Fig. 2, A″/B/C/H (ribbon pool) and A‴/D/E/I (reserve pool).**
5. SV tethering classification (tethered vs. non-tethered, scored by visual inspection for a continuous electron-dense link) using 3D electron tomography (SerialEM acquisition, eTomo reconstruction, 3dmod for 3D rendering). **→ Fig. 2, L/L′, M/M′, and N.**
6. Nanoscale localization of Piccolino relative to the SR, via STED line-intensity profiles (FWHM by Gaussian fitting in Lightbox software) and pre-embedding immuno-EM using the same distance-to-line method as step 3. **→ Fig. 3, C′/D′ (STED), C″/D″ (profiles), E/E′ (immuno-EM), E″ (quantification).**
7. Mitochondrial-targeting and SV-recruitment colocalization: Grp75 channel binarized by Otsu's thresholding ("Make Binary" in Fiji ImageJ) to define mitochondrial ROIs, mean intensity measured per ROI, Pearson's r computed (software for the correlation step itself not named). **→ Fig. S3, E/F (images), E′/F′ (targeting efficiency), E″/F″ (SV recruitment).**

```{note} Ambiguities and gaps flagged during extraction
:class: dropdown
- Neither the SR length, AZ length, nor SR height measurements (Fig. 1, I/K/J″) have any stated measurement software or tracing method in Methods.
- ONL thickness (Fig. S1 C) is quantified with no corresponding Methods description at all.
- Densitometric quantification of the liposome floatation dot blots (Fig. 5, E′/F′; Fig. S3 D′) names the imaging system (ChemiDoc XRS) but not the quantification software.
- Several panels are explicit schematics (Fig. 1 A/B; Fig. 2 A/A′–A‴; Fig. 3 A/B; Fig. 4 A; Fig. 5 A) and are excluded from bioimage-analysis scoring accordingly. The ALPS-motif structure prediction (Fig. 4, A/B/B′, via Heliquest/ColabFold/ChimeraX) and the membrane-curvature MD simulations (Fig. 4, C–H, via GROMACS/Martini) are computational renderings, not empirical image analysis of biological samples.
```

```{admonition} Verbatim quote
"For the analysis of SVs density in the ribbon RP, the surface of SRs was marked with a free-hand line. Next, SVs within 50 nm of the SR were counted and divided by the SR length to obtain the density of SVs/µm2. The first 100 nm of SRs perpendicular to the AZ were excluded from the analysis to eliminate docked SVs from the quantification."

"For the identification of tethered SVs in EM tomograms, SVs were classified as tethered if a continuous, electron-dense physical link was visible between the SV membrane and the surface of the SR. Tethers were identified by visual inspection in individual tomographic virtual sections."
```

- **Software named**: Fiji ImageJ / ImageJ (MultiPoint/straight-line/free-hand tools, "Make Binary," Otsu's thresholding); Lightbox software (Abberior); TRUESHARP (online deconvolution); DigitalMicrograph 3.1 (Gatan); SerialEM; eTomo; 3dmod; GraphPad Prism 10; CorelDRAW X9/2024; Heliquest; ColabFold (AlphaFold2); ChimeraX; GROMACS (v.5.0.5 and 2024.4); Martinize2; ChemiDoc XRS; iBright FL1500.
- **Code repository**: None found for custom image-analysis code (no GitHub/GitLab link). A Zenodo DOI (10.5281/zenodo.20762753) hosts numerical data only, not code or images.
- **Sample image data**: **On request** — image data explicitly named (category b). Data Availability statement: "The uncropped Blots displayed in Figs. 1, 5 and S3 are available in the data. The numerical data underlying each figure are openly available in Zenodo... Large imaging datasets are available from the corresponding author upon reasonable request." — the statement explicitly names "imaging datasets," gated behind a reasonable-request clause, distinct from the openly deposited numerical data.
- **Based on prior methods**: The core quantification subsections ("Topology of Piccolino," "SV analysis," "SV tethering analysis," "SV recruitment analysis") carry no citation — presented as this study's own methodology. Sample-preparation protocols are cited to prior work (Müller et al., 2019; Gierke et al., 2020; Möbius et al., 2010; Jung et al., 2015; Ryl et al., 2021; Anni et al., 2021).

(bin1-snx9)=
## Nanoscale junctional membrane curvatures recruit BIN1 and SNX9 for endothelial collective migration

Vera Janssen, Hannah de Kraker, Jesse S. Aaron, Annett de Haan, Iris de Heer, Satya Khuon, Jason Da Silva, Amber J.M. Driessen, Teng-Leong Chew, Josephine M.E. Tan, Anne K. Lagendijk, Ana Angulo-Urarte, and Stephan Huveneers — *Journal of Cell Biology*, Vol. 225, No. 9, e202509207 (2026). [doi:10.1083/jcb.202509207](doi:10.1083/jcb.202509207)

1. Cryo-SIM and FIB-SEM imaging/registration of adherens-junction (AAJ) ultrastructure: SIM reconstruction (Gustafsson et al., 2008 algorithm), FIB-SEM slice alignment via a third-party Python SIFT implementation, Ilastik random-forest segmentation of membrane/mitochondria, and BigWarp-based cryo-CLEM registration. **→ Fig. 1, a–c; Fig. S1, a–c; Videos 1–3.**
2. Plasma-membrane curvature mapping — Ilastik probability maps thresholded, isosurface computed per junction, average Gaussian curvature calculated over a ~60 nm radius, via custom MATLAB code adapted from a third-party MATLAB File Exchange snippet. **→ Fig. 1, d and e; Fig. S1 c.**
3. Colocalization of BAR proteins (BIN1/SNX9) and dynamin-2 with PACSIN2/EHD4/MICAL-L1 at AAJs >1 µm, both channels thresholded, Mander's split coefficient computed — the thresholding algorithm/value itself is not named. **→ Fig. 4 i; Fig. 5, c, d, and l.**
4. Spatiotemporal BAR-GFP spot tracking (background subtraction, Gaussian blur, Intermodes thresholding, TrackMate detection/linking, manual curation in TrackScheme) for residency time and subjunctional distribution. **→ Fig. 4, a–c; Videos 5 and 6.**
5. AAJ-protein recruitment-delay analysis (manual ROI, Z-axis mean-intensity profiling, first-frame-above-baseline detection) and AAJ "positivity" percentage scoring (criterion for calling an AAJ "positive" not defined in this subsection). **→ Fig. 4, g, h, k, and l; Fig. 5 i; Fig. S4, d and e; Videos 7 and 8.**
6. AAJ lifetime, length, and straightness measurement (manual first/last-frame identification; Fiji line and segmented-line tools). **→ Fig. 6, e–g and j–l; Fig. 7 l; Videos 11 and 12.**
7. Scratch-wound closure quantification and Golgi front-rear polarity (angle tool, % of follower cells with Golgi within 120° of the migration front). **→ Fig. 3 c; Fig. S4, c and f; Fig. 6 m.**
8. Zebrafish cerebral-vessel (CCV) shape analysis via a custom, undeposited Fiji script (rotation, thresholding, Particle Analyzer shape metrics) and Imaris-based cell tracking (leader/follower classification). **→ Fig. 7, e–j; Fig. S5, e–h and k and l.**

```{note} Ambiguities and gaps flagged during extraction
:class: dropdown
- The colocalization-thresholding algorithm/value for the Mander's split-coefficient step is never named.
- The criterion for scoring an AAJ as "positive" in the AAJ-protein-localization subsection is not defined there (it is not explicitly cross-referenced to the earlier, separate qualitative scoring rule used for the BAR-protein screen).
- SIM/Cryo-SIM acquisition/reconstruction software is not named beyond the reconstruction algorithm; confocal/widefield acquisition software for the Leica/Nikon/Zeiss systems is likewise unnamed.
- The custom Fiji script used for CCV shape analysis is described narratively but not shared as a linked/versioned script.
- The FIB-SEM slice-alignment code (GitHub, gleb-shtengel/FIB-SEM) and the MATLAB curvature snippet (MATLAB File Exchange, Claxton 2026) are both **third-party tools the authors adapted**, not their own deposited image-analysis code.
```

```{admonition} Verbatim quote
"Image regions containing endothelial asymmetric junctions were then analyzed to compute local plasma membrane curvature using custom MATLAB code adapted from Claxton (2026)... plasma membrane probability maps generated from ilastik were thresholded, and an isosurface was computed for each junction. The average Gaussian curvature at each point along the computed surface was calculated across an ∼60 nm search radius to create curvature maps for each asymmetric junction."

"The colocalization of SNX9-GFP and BIN1-GFP with PACSIN2, EHD4, and MICAL-L1 or the colocalization of dynamin-2 with SNX9 or PACSIN2 was analyzed by taking AAJs larger than 1 um and thresholding both channels of interest."
```

- **Software named**: Imaris 10.2; Fiji/FIJI 2.9.0; Ilastik 1.4.0; BigWarp (Fiji plugin); TrackMate; TrackScheme; GraphPad Prism 10; RStudio (with ComplexHeatmap, tidyverse, grid); MATLAB (custom, adapted); Python (SIFT implementation); BLAST.
- **Code repository**: The FIB-SEM slice-alignment code (`https://github.com/gleb-shtengel/FIB-SEM`) and the MATLAB curvature snippet (MATLAB File Exchange, ID 11168) are both third-party tools that were adapted, not the authors' own deposited pipeline. No repository is given for the colocalization pipeline, the TrackMate tracking pipeline, the AAJ-positivity scoring, or the custom CCV-shape Fiji script.
- **Sample image data**: **On request** — image data explicitly named (category b). Data Availability statement: "Source images and other data are available from the corresponding author... upon reasonable request." — explicitly names "Source images," gated behind an on-request clause; no public repository/accession is given.
- **Based on prior methods**: The overall Cryo-SIM/FIB-SEM workflow follows Bharathan et al. (2023) and Hoffman et al. (2020); the FIB-SEM instrument is per Xu et al. (2017); the SIM reconstruction algorithm is Gustafsson et al. (2008); the MATLAB curvature code is adapted from Claxton (2026, MATLAB File Exchange). The colocalization/Mander's protocol, the AAJ-positivity scoring, Golgi-orientation scoring, wound-closure quantification, AAJ lifetime/length/straightness, and the CCV shape script are all presented as uncited/in-house procedures.

(mitochondrial-transfer)=
## Intercellular mitochondrial transfer and trans-mitophagy in response to protein import dysfunction

Emily Glover, Beth Wiseman, Celyn Dugdale, Charlie Humphery, Lorena Sueiro Ballesteros, Lorna Hodgson, Kevin Wilkinson, and Ian Collinson — *Journal of Cell Biology*, Vol. 225, No. 9, e202511211 (2026). [doi:10.1083/jcb.202511211](doi:10.1083/jcb.202511211)

1. Live-imaging quantification of mitochondria-containing tunneling nanotubes (mitoTNTs) — TNT length/width and mitochondria number/length within them, acquired on a spinning-disk system with Evident cellSens software. **→ Fig. 1, B and C (i–iv).**
2. Live/fixed imaging and quantification of transferred-mitochondria size/number and mitochondria-derived body (MDB) formation from max-projected images. **→ Fig. 2, D–H; Fig. S2; Fig. S3, C–E; Fig. 4, D–F.**
3. Correlative light and electron microscopy (CLEM) of transferred mitochondria/MDBs using eC-CLEM (Paul-Gilloteaux et al., 2017) within the Icy platform. **→ Fig. 3, A and B.**
4. Ratiometric HyPer7 mitochondrial-ROS imaging (dual-excitation 405 nm/488 nm ratio vs. distance from cell center) — the ratio-calculation procedure itself is not described step-by-step in Methods. **→ Fig. 4, A (i–iii) and B (i and ii).**
5. Time-lapse quantification of transferred-mitochondria fluorescence-intensity decay (degradation kinetics, normalized to initial/6 h intensity). **→ Fig. 5, A and B.**
6. LAMP1 colocalization with transferred mitochondria via Mander's coefficient — no software/algorithm is named anywhere for this specific calculation. **→ Fig. 5, C and D.**

```{note} Ambiguities and gaps flagged during extraction
:class: dropdown
- The Mander's coefficient calculation (Fig. 5 D) is named only in the figure legend; Methods gives no software, plugin, or thresholding procedure for it.
- The ratiometric HyPer7 imaging protocol is described in the figure legend but Methods has no dedicated subsection for the ROI/line-profile method or ratio-image generation.
- Methods names "Cellvis software" for iterative deconvolution — an unusual attribution (Cellvis is typically a labware/dish brand rather than a deconvolution package), reported here verbatim as printed, with no version number.
```

```{admonition} Verbatim quote
"Light microscopy image processing and analysis. Iterative deconvolution was performed on Cellvis software. Images were max-projected and analyzed on Fiji ImageJ (Schneider et al., 2012) using ModularImageAnalysis (Cross et al., 2024). GraphPad Prism software was used for all statistical analyses and graph design."
```

- **Software named**: Evident cellSens; FlowJo; easy cell-CLEM/eC-CLEM (Paul-Gilloteaux et al., 2017); Icy (de Chaumont et al., 2012); "Cellvis" (as printed); Fiji/ImageJ (Schneider et al., 2012); ModularImageAnalysis (MIA; Cross et al., 2024); GraphPad Prism. No version numbers given for any of these.
- **Code repository**: None found. No GitHub/GitLab/Zenodo/accession of any kind appears anywhere in the document.
- **Sample image data**: **No Data Availability statement found at all** (category d). A full search of the document — including Acknowledgments, Author contributions, Disclosures, and the Supplemental material section through its final line — found no data-availability language, repository, or "available upon request" statement anywhere.
- **Based on prior methods**: CLEM registration cites eC-CLEM (Paul-Gilloteaux et al., 2017) and Icy (de Chaumont et al., 2012); Fiji/ImageJ is cited (Schneider et al., 2012); ModularImageAnalysis is cited (Cross et al., 2024). The HyPer7 ratiometric-imaging analysis, the Mander's-coefficient colocalization step, and the deconvolution step are all presented without a methodological citation.

(cenp-c-meiosis)=
## Meiotic CENP-C supports centromere assembly and kinetochore recruitment in spermatogenesis

Rachel S. Keegan, Dina Malkeyeva, Meg B. Weever, and Elaine M. Dunleavy — *Journal of Cell Biology*, Vol. 225, No. 9, e202512053 (2026). [doi:10.1083/jcb.202512053](doi:10.1083/jcb.202512053)

1. Centromeric protein intensity quantification (CID/CENP-A, CENP-C, CAL1, Spc105) — 8-bit single-nuclei images, max-intensity Z-projection, rolling-ball background subtraction (radius 50), ImageJ default-algorithm thresholding, integrated density summed per nucleus, in FIJI/ImageJ. **→ Fig. 1 C; Fig. 2, A–I; Fig. 3, A, B, E, F, and H; Fig. 5, B, D, F, G, and I.**
2. FISH-based chromosome missegregation scoring — fluorescent ssDNA oligo probes (X/Y/2nd/3rd/4th chromosome-specific repeats), manually scored by eye as normal/abnormal against expected per-nucleus focus patterns (criteria given only in Results, not Methods). **→ Fig. 4, A–E; Fig. S3.**
3. Meiotic spindle morphology scoring — GFP-tubulin/CID-immunostained testes; spindles "lacking a defined bipolar structure and without direct contact to centromeres" manually scored as abnormal (criterion stated only in Results). **→ Fig. 3, I and J.**
4. Mature sperm nuclei assessment — DAPI-stained sperm imaged as representative micrographs per genetic line; qualitative comparison only, no quantitative counting method or software described. **→ Fig. 4 F.**

```{note} Ambiguities and gaps flagged during extraction
:class: dropdown
- Both the spindle-abnormality criterion and the FISH missegregation scoring rubric live only in the Results narrative, not in Materials and methods — neither subsection names any scoring software, blinding procedure beyond "strain identification blinded," or sample-size reporting within Methods itself.
- The sperm-nuclei panel (Fig. 4 F) has no scoring criteria, counting method, or software of any kind — a purely qualitative representative-image comparison.
- Fig. S4 (Fly Cell Atlas / SCope-platform single-cell RNA-seq visualization) names the SCope tool only in the supplementary figure legend, with no description anywhere in Methods of the parameters or workflow used to generate its UMAP plots.
```

```{admonition} Verbatim quote
"To quantify protein levels in the samples, fluorescent intensity was measured using FIJI/ImageJ. Single nuclei were isolated among the images (8-bit) and Z-projected with maximal intensity... The background was subtracted (rolling ball radius set to 50.0) from the projected images, and thresholding using the default algorithm was applied to select the entirety of the centromeric signal. Integrated density (mean gray value x area) was summed to generate the total fluorescent intensity per nucleus."

"Spindles lacking a defined bipolar structure and without direct contact to centromeres were scored as abnormal for both meiotic divisions."
```

- **Software named**: FIJI/ImageJ; softWoRx (Applied Precision); GraphPad Prism; NEBioCalculator v.1.17.4 (qPCR only); SCope (named only in a figure legend, not in Methods). Only NEBioCalculator carries a version number.
- **Code repository**: None found. No GitHub/GitLab/Zenodo link appears anywhere in the document.
- **Sample image data**: Not stated for image data specifically (category c). Data Availability statement: "All data supporting the findings of this study are included in the published article and its supplemental material, or are available from the corresponding author upon reasonable request." — a single generic statement covering all data types, with no image-specific mention or repository/accession.
- **Based on prior methods**: FISH probe sequences are cited to Tsai et al. (2011) and Ferree and Barbash (2009). The immunofluorescence intensity-quantification pipeline, the spindle-scoring criterion, and the fertility-assay protocol are all presented without a methodological citation.

(stu1-mps1)=
## Kinetochore clustering is mediated by Mps1 phosphorylation of conserved MELT motifs in Stu1

Darren R. Mallett, Mengqiu Jiang, Gianna M. Minnuto, and Sue Biggins — *Journal of Cell Biology*, Vol. 225, No. 9, e202601143 (2026). [doi:10.1083/jcb.202601143](doi:10.1083/jcb.202601143)

```{note}
This article is formatted as an "HHS Public Access / Author manuscript" (PMC) version — Methods and all figure legends are relocated to the end of the document, after References, and figure legends use the "Figure N:" (colon) format rather than "Fig. N."
```

1. Kinetochore (Mtw1-3xmYPet) foci counting — distinct foci counted manually per cell in X/Y/Z by a blinded observer, plotted/tested (Mann–Whitney U) in RStudio/ggplot2. **→ Figs. 2B, 3B, 4B, 4C, and 6F.**
2. Kinetochore fluorescence-intensity and attachment-status quantification via a **custom, undeposited ImageJ macro**: maximum-intensity projections, manual CFP(Spc110)/mCherry(Mtw1) thresholding for ROI selection, attached-vs.-unattached classification by co-localization of kinetochore puncta with Spc110-mTurquoise2, background subtraction, Mtw1-normalized ratios, bootstrapped 95% CIs. **→ Figs. 1G, 2D, 6B, and 6D.**
3. Serial-dilution growth-assay imaging (spot plates photographed "after sufficient growth") — no quantification method or imaging device/software is named for the image-capture step. **→ Fig. 5G.**
4. AlphaFold2/AlphaFold3 structural modeling and visualization (PyMOL, ChimeraX, APBS electrostatics) — computational structure prediction/rendering, not empirical bioimage analysis. **→ Figs. 1B–C, 7D, 8, and S4.**
5. Mass-spectrometry phosphosite/kinase-motif mapping — Proteome Discoverer 2.5 + Sequest HT/Percolator, results parsed by a Python script adapted from a prior publication (Nelson et al., 2025) and deposited on Zenodo; this is proteomic/text-data parsing, not image analysis. **→ Table S1; Fig. 5C; Figs. S2 and S3; Table S5.**
6. CryoEM and negative-stain EM particle processing (motion correction, CTF correction, blob picking, 2D/3D classification in cryoSPARC; a second Topaz picking pass). **→ Fig. 7 and related panels.**

```{note} Ambiguities and gaps flagged during extraction
:class: dropdown
- The custom ImageJ macro used for the kinetochore intensity/attachment-status analysis (step 2) is never shared, versioned, or deposited, and it is absent from the Data Availability statement even though that statement otherwise names four other data types.
- The serial-dilution assay's Methods paragraph describes the wet-lab protocol fully but names no camera, scanner, or imaging software for the plate photography shown in Fig. 5G.
- No digital quantification/densitometry software is named for any of the paper's immunoblot figures (Figs. 1A, 1D, 3A, 4D, 5A, 5B, 5E, and 5F) — these appear to be presented as representative blots only.
```

```{admonition} Verbatim quote
"For fluorescence intensity measurements, intensity was measured using custom ImageJ macro scripts. Raw images of single cells were converted to maximum-intensity projections and the mean gray value of each channel at each kinetochore focus as well as the background fluorescence was quantified. Strain identification labels were blinded. The user manually thresholded the CFP (Spc110) and mCherry (Mtw1) channels for ROI selection. The macro distinguishes attached versus unattached kinetochores based on the co-localization of the kinetochore puncta with Spc110-mTurquoise2."
```

- **Software named**: DeltaVision Acquire Ultra (acquisition); ImageJ (custom macro, unversioned); RStudio/ggplot2; SnapGene (BLAST + MUSCLE); AlphaFold2/AlphaFold3; PyMOL (Version 3.0); UCSF ChimeraX; APBS; Proteome Discoverer 2.5; Sequest HT; Percolator; Python (adapted script); cryoSPARC; Topaz.
- **Code repository**: A Zenodo DOI (`10.5281/zenodo.18217341`) hosts the phosphosite-parsing Python code for Table S1 — explicitly adapted from a prior publication (Nelson et al., 2025) and not an image-analysis tool. **The paper's own image-analysis code (the custom ImageJ macro) is neither shared nor mentioned anywhere in the Data Availability statement.**
- **Sample image data**: Not stated for image data specifically (category c). Data Availability statement: "All reagents are available from the corresponding author upon request. Raw mass spectrometry data... is available at [MassIVE FTP]. Python code... is available at [Zenodo]. The cryoEM density map of Slk19 is available from EM Databank (EMDB) with accession number EMD-75100." — this statement is detailed but addresses reagents, mass-spec data, code, and the cryoEM map only; it says nothing about the live-cell fluorescence microscopy datasets (DeltaVision) underlying most of the paper's figures.
- **Based on prior methods**: The mass-spec phosphosite-parsing pipeline is explicitly "as previously described (Nelson et al., 2025)"; cryoEM/negative-stain processing cites cryoSPARC (Punjani et al., 2017) and Topaz (Bepler et al., 2019); AlphaFold/ChimeraX/APBS steps carry their respective tool citations. The ImageJ macro-based fluorescence quantification and the manual kinetochore-foci counting are both presented without a methodological citation.

(gcl-pip3)=
## GCL pruning of PIP3 establishes the soma-germline boundary

Mariyah Saiduddin, Juhee Pae, Asier Marcos-Vidal, Martin L. Alani, and Ruth Lehmann — *Journal of Cell Biology*, Vol. 225, No. 9, e202604036 (2026). [doi:10.1083/jcb.202604036](doi:10.1083/jcb.202604036)

1. Primordial germ cell (PGC) counting — Vasa-positive PGCs in fixed embryos counted manually with the ImageJ Cell Counter plugin. **→ Fig. 1, C and D; Fig. 2, B and C; Fig. 3, D and E; Fig. 4, A–D; Fig. 5; Fig. S1; Fig. S2.**
2. PIP3/PIP2/F-actin/myosin-II pole-bud intensity quantification via a custom Python pipeline: Noise2Void denoising of the nuclear channel, Cellpose-SAM 3D segmentation of pole buds, Cellpose cyto3 segmentation of nuclei (both trained human-in-the-loop), 3D erosion/dilation to define nucleus/cytoplasm/membrane compartments, membrane-to-cytoplasm intensity ratios computed per pole bud per timepoint. **→ Fig. 6, C and F; Fig. 7, C and D; Fig. 8, B and E.**
3. Myosin-II circumferential intensity profiling in fixed embryos — custom ImageJ macro (edge-finding filter, manual binary threshold of cleavage furrows, 100 equal-angle segments, mean intensity per segment, normalized in base R). **→ Fig. 8, G–I.**
4. Pole bud height/width measurement using the membrane marker Katushka2-CAAX. **→ Fig. S5, A–D.**

```{note} Ambiguities and gaps flagged during extraction — figure-label discrepancy confirmed
:class: dropdown
The Materials and methods section states that images for "pole bud height and width measurements" are shown in "(Fig. S3)" — but this is a mislabel. Figure S3 is actually an unrelated figure (p60/PI3K-regulatory-subunit distribution via a p60-GFP fosmid line). The actual pole bud height/width diagram and measurements are in **Figure S5** (its legend explicitly shows a "Diagram of pole bud length and width measurements" (panel B), width (panel C), and length (panel D)), and the body-text citation "(Fig. S5, A–D)" confirms this. Beyond the mislabel, no description of *how* height/width were actually measured (manual line tool? software? landmark definition?) is given anywhere in Methods.
```

```{admonition} Verbatim quote
"Fluorescence intensity analysis of PIP3, PIP2, F-actin, and myosin II in time-lapse images of posteriorly mounted live embryos... was performed using custom Python scripts. Prior to segmentation, the nuclear marker channel of the two-channel z-stack fluorescence images was denoised using a Noise2Void (Krull et al., 2019) model... Subsequently, pole buds were segmented in 3D using a Cellpose-SAM model (Pachitariu et al., 2025, Preprint), and nuclei were segmented using a Cellpose cyto3 model (Stringer and Pachitariu, 2025)."

"Vasa-positive PGCs in each embryo were counted manually using the ImageJ Cell Counter plugin (NIH; http://rsb.info.nih.gov/ij/) (Schindelin et al., 2012)."
```

- **Software named**: ImageJ (Cell Counter plugin; general figure/plot use); GraphPad Prism; Cellpose-SAM (Pachitariu et al., 2025, preprint); Cellpose cyto3 (Stringer and Pachitariu, 2025); Noise2Void (Krull et al., 2019); Python (custom scripts); R (base plotting); Nikon Elements. No version numbers given (model names are given in place of classic version numbers for the deep-learning segmentation models).
- **Code repository**: None found. No GitHub/GitLab/Zenodo/OSF/figshare link anywhere in the document for the custom Python or ImageJ-macro code.
- **Sample image data**: On request, though borderline with "not stated" (category b, noted as a close call). Data Availability statement: "The data underlying all figures are available in the published article and supplemental information, and from the corresponding author." — this names "all figures" specifically and offers direct request-based access, going slightly beyond the purely generic "the data" language seen in other papers in this issue, though it stops short of naming "images" or "microscopy data" outright, and no public repository/accession is given.
- **Based on prior methods**: PGC counting cites Schindelin et al. (2012, the Fiji paper); the denoising step cites Krull et al. (2019, Noise2Void); pole-bud/nuclear segmentation cite Pachitariu et al. (2025) and Stringer and Pachitariu (2025); the human-in-the-loop training approach cites Pachitariu and Stringer (2022). The pole bud height/width measurement itself and the myosin-II circumferential-profile macro are both presented without a methodological citation.

(arp23-phosphate)=
## Inorganic phosphate rapidly switches the stability of Arp2/3-induced actin branches

Jiu Xiao, Foad Ghasemi, Adrien Schahl, Miroslav Mladenov, Rebecca Pagès, Matthieu Chavent, Michael Way, Luyan Cao, Guillaume Romet-Lemonne, and Antoine Jégou — *Journal of Cell Biology*, Vol. 225, No. 9, e202605018 (2026). [doi:10.1083/jcb.202605018](doi:10.1083/jcb.202605018)

1. TIRF time-lapse imaging of actin-filament branch formation/dissociation, acquisition controlled by MicroManager. **→ Fig. 1 E; Fig. 4 C; Fig. 5 B**, and the time-lapse panels underlying Figs. 1, 2, 4–7.
2. Identification of branch dissociation/renucleation events from the movies — **the scoring method itself (manual vs. automated) is not described anywhere in Methods**, a genuine gap since all downstream statistics depend on it. Feeds Fig. 1, B, D, and F; Fig. 2, B–F; Fig. 4, B and D; Fig. 5, C and D; Figs. 6 and 7.
3. Branch survival-curve statistics — Kaplan–Meier estimation with censoring via the Python "lifelines" package, 95% CIs via Greenwood's formula; curve fitting (debranching rate, Pi-affinity, kinetic model) via SciPy's `curve_fit`. **→ Fig. 1, B, D, and F; Fig. 2, B–D and F; Fig. 4, B and D; Fig. 5 C; Fig. 6 A; Figs. S1–S3 and S6.**
4. Force-at-junction calculation (F = v_flow × L_branch × η_actin) — an algebraic formula, not a software tool; no image-measurement software is named for how v_flow (local flow velocity) or L_branch (daughter-filament length) were actually extracted from the movies. Underlies force values reported throughout Figs. 1, 2, and 4–7.
5. Molecular dynamics simulation of Pi "backdoor" opening in Arp2/Arp3 (GROMACS 2023.2, CHARMM36m, CHARMM-GUI, LINCS, PME electrostatics; distance-analysis method per Schahl et al., 2025) — computational simulation, not empirical image analysis. **→ Fig. 3, A–C.**

```{note} Ambiguities and gaps flagged during extraction
:class: dropdown
The task brief for this paper referenced "Lbranch" and "vflow" as if they might be named software tools — confirmed on inspection that these are algebraic symbols within the force equation quoted below, not software. The two genuine gaps are: (1) no description anywhere of how branch dissociation/renucleation events were identified from the raw TIRF movies (manual scoring, kymographs, or an automated detector are all unstated), and (2) no image-analysis software (ImageJ/Fiji/MATLAB/custom script) is named anywhere in the paper despite its heavy reliance on fluorescence-microscopy quantification — only downstream statistical packages (lifelines, SciPy) are named.
```

```{admonition} Verbatim quote
"The fraction of surviving branches as a function of time is computed by the Kaplan–Meier method using the "lifelines" package from Python. The error bars represent the 95% confidence interval calculated with the Greenwood's exponential formula."

"The applied pulling force at the branch junction is F = vflow × Lbranch × ηactin, where Lbranch is the length of the daughter filament, vflow the local flow velocity at 250 nm above the glass surface, and ηactin the longitudinal friction coefficient per unit length of the actin filament... determined in a previous publication (Jégou et al., 2013)."
```

- **Software named**: MicroManager/μManager (Edelstein et al., 2014); SciPy (`curve_fit`); lifelines (Python); GROMACS 2023.2; CHARMM-GUI. No ImageJ, Fiji, MATLAB, or any named image-segmentation/tracking tool appears anywhere in the document.
- **Code repository**: None found.
- **Sample image data**: Not stated for image data specifically (category c). Data Availability statement: "The data are available from the corresponding author upon reasonable request." — generic language, no mention of images or movies specifically.
- **Based on prior methods**: The microfluidics assay is based on Jégou et al. (2011), detailed in Wioland et al. (2022); the force-calibration equation and η_actin value are from Jégou et al. (2013); the MD residue-distance method is from Schahl et al. (2025). The core branch-event detection/scoring step that underlies all downstream quantification is uncited and undescribed.

(golgi-nucleus-repair)=
## Spatiotemporal regulation of DNA repair proteins between Golgi and nucleus maintains genome stability

George Galea, Karolina Kuodyte, Muzamil Majid Khan, Peter J. Thul, Beate Neumann, Emma Lundberg, and Rainer Pepperkok — *Journal of Cell Biology*, Vol. 225, No. 9, e202605024 (2026). [doi:10.1083/jcb.202605024](doi:10.1083/jcb.202605024)

1. Antibody/siRNA validation screen — automated widefield imaging, CellProfiler segmentation of nuclei and Golgi, intensity-profile quantification of signal reduction, following the group's own prior protocol (Stadler et al., 2012). **→ Fig. 1 A; Fig. S1; Fig. S2 A; Table S1.**
2. Golgi sub-compartment (cisternal) localization — nocodazole-dispersed mini-stacks, Fiji "plot profile" line-scan intensity vs. cis-(GM130)/trans-(TGN46) markers, Pearson's correlation coefficient, as previously described (Dejgaard et al., 2007). **→ Fig. 2, A–E; Fig. 4, F and G; Fig. S2 C; Table S2.**
3. Golgi-to-nuclear redistribution ratio after genotoxic treatments (DOX, H₂O₂, KBrO₃, CPT, ETO, MMC, IPZ, kinase inhibitors) — CellProfiler + Fiji nuclear/Golgi segmentation and fluorescence-mask intensity-ratio calculation. **→ Fig. 2, F–H; Fig. 3, A–I and K–P; Fig. 4, B–E; Figs. S3–S7.**
4. RAD51C-foci colocalization with γ-H2AX/p-ATM — CellProfiler "structure counting" and intensity-profile modules. **→ Fig. 4, J–M.**
5. Micronuclei scoring from Hoechst-stained nuclei, using the general CellProfiler/Fiji pipeline (no micronuclei-specific segmentation criteria given). **→ Fig. 5, A–C and O.**
6. Comet assay — automated Olympus Scan^R acquisition, tail scoring via the OpenComet Fiji/ImageJ plugin (Gyori et al., 2014), following a prior protocol (Vodenkova et al., 2020). **→ Fig. 5, D and E.**
7. DR-GFP homologous-recombination reporter assay — automated high-content imaging, CellProfiler quantification of % GFP-positive cells. **→ Fig. 5 L.**
8. Colony-formation assay — crystal-violet-stained colonies photographed and quantified for area coverage; **no segmentation/thresholding software is named** for this step. **→ Fig. 5, F–I.**

```{note} Ambiguities and gaps flagged during extraction
:class: dropdown
- The colony-formation assay's Methods text ("digital images of the colonies were acquired using a camera and quantified") names no imaging hardware model or quantification software.
- Western-blot densitometric quantification (Fig. 3 D; Fig. 5, J, K, M, and N; Fig. S6, D and E) is never attached to a named densitometry software, even though the blotting/detection chemistry (Azure 280 imager) is described.
- FACS cell-cycle analysis (Fig. S7 M) is named only in Results and the Fig. S7 legend; there is **no corresponding Methods subsection anywhere in the document** (no staining protocol, cytometer model, or analysis software).
- Micronuclei detection/segmentation criteria (size thresholds, classification rules) are not given beyond the general CellProfiler/Fiji statement.
```

```{admonition} Verbatim quote
"Images were acquired on a fully automated Molecular Devices IXM with a 10×/0.45 NA P-APO objective. The resulting images were analyzed using Cell Profiler software (Carpenter et al., 2006) for quantitative and automated measurements of fluorescence from the antibodies as previously described (Stadler et al., 2012). Briefly, nuclei were segmented in the nuclear channel, the Golgi complex was segmented in the Golgi marker channel, and using the segmented nuclei as seeds, the two structures were associated."

"Finally, after the dishes were dry, digital images of the colonies were acquired using a camera and quantified."
```

- **Software named**: CellProfiler (Carpenter et al., 2006); Fiji (Schindelin et al., 2012); OpenComet plugin (Gyori et al., 2014); GraphPad Prism 9; KM Plotter; GEPIA2 (Tang et al., 2019). No version numbers given for CellProfiler or Fiji.
- **Code repository**: None found.
- **Sample image data**: Not stated for image data specifically (category c). Data Availability statement: "The data are available from the corresponding author upon reasonable request." — generic language covering all data types, no image-specific mention or public repository.
- **Based on prior methods**: The siRNA-validation imaging pipeline follows Stadler et al. (2012) and Erfle et al. (2008); the Golgi-cisternal line-scan/PCC method is explicitly "as previously described (Dejgaard et al., 2007)"; the comet assay follows Vodenkova et al. (2020); the DR-GFP assay design cites Pierce et al. (1999). The colony-formation assay and western-blot densitometry are both presented without a methodological citation, and no Methods subsection exists at all for the FACS cell-cycle analysis.

```{warning} Caveats

**Code availability.** None of the ten articles in this issue provide a public code repository for their own bioimage-analysis pipeline. The only repository links found anywhere in the issue are third-party or adapted tools the authors reused rather than authored: a GitHub SIFT-alignment implementation and a MATLAB File Exchange curvature snippet (both in "Nanoscale junctional membrane curvatures..."), and a Zenodo-hosted phosphosite-parsing Python script (in "Kinetochore clustering...") that is itself proteomic text-data parsing, not image analysis, and is explicitly adapted from a prior publication. Several papers describe substantial custom image-analysis code in detail — a custom ImageJ macro for kinetochore attachment/intensity classification, a custom Python Cellpose/Noise2Void segmentation pipeline, a custom Fiji script for zebrafish vessel shape analysis — none of which is deposited or offered on request.

**Version-number gaps.** Most named software (Fiji/ImageJ, CellProfiler, MetaMorph, Icy, SynActJ, softWoRx, GraphPad Prism in several papers) is cited without a version number. Two papers in this issue show internal version discrepancies between the Methods narrative and a separate reagents/key-resources table for the same tool (Harmony: "v5.2" vs. "4.9"; GraphPad Prism: "v10.5" vs. "10.3.1" — both in "EPHA2/CD44-directed trafficking..."). Deep-learning segmentation models (Cellpose-SAM, Cellpose cyto3, Noise2Void) are identified by model/checkpoint name rather than a classic version string.

**"Based on prior methods" scope.** This report credits a step to prior methods only when the paper cites a reference specifically for that quantification/analysis procedure — not for general reagents, antibodies, or unrelated assays cited elsewhere. Judged this way, the large majority of the true image-analysis and quantification steps across this issue (segmentation/thresholding pipelines, distance and colocalization calculations, foci/spot counting, spindle- and missegregation-scoring criteria) are presented as uncited, in-house methodology, even where the paper cites prior work for its underlying biological assay or sample preparation.

**Figure-mapping and measurement-attribution ambiguities.** A confirmed figure-citation discrepancy was found in "GCL pruning of PIP3...": the Materials and methods section attributes the pole bud height/width measurement images to "Fig. S3," but the actual diagram and measurements are in Figure S5 (confirmed by both the Results-text citation and the Fig. S5 legend itself); Fig. S3 in that paper is an unrelated p60/PI3K-distribution figure. Several other papers name a technique in Results or a figure legend without ever tying it to a specific analysis method in Methods — for example the FISH-probe imaging step in "EPHA2/CD44-directed trafficking...", the AAJ-positivity scoring criterion in "Nanoscale junctional membrane curvatures...", and the SCope/Fly Cell Atlas visualization in "Meiotic CENP-C..." — these are flagged inline rather than guessed at.

**Supplementary-methods-deferral check.** No article in this issue defers image-analysis *methodological detail* to a separate supplementary-methods document that this PDF doesn't include. Every genuine "supplementary" cross-reference found was either an ordinary pointer to a supplementary figure/movie/table, or — in a few cases ("Kinetochore clustering...", "Meiotic CENP-C...") — a deferral of substantive quantitative *data* (confidence-interval tables, coverage maps, PCC value tables) to a supplementary table, which is normal practice and not a methods gap.

**Sample image data availability.** Across the ten articles: **0** publicly deposit raw/original image data with a resolvable accession or DOI (category a); **2** state that image data are available specifically on request ("Piccolino..." — "large imaging datasets... upon reasonable request"; "Nanoscale junctional membrane curvatures..." — "Source images... upon reasonable request") (category b); **7** give only generic "data" language with no image-specific mention (category c) — "EPHA2/CD44-directed trafficking...", "CAST/ELKS–endophilin-A...", "Meiotic CENP-C...", "Kinetochore clustering...", "GCL pruning of PIP3..." (borderline — its statement names "all figures" specifically, going slightly further than the other six, but stops short of naming images/microscopy data outright), "Inorganic phosphate rapidly switches...", and "Spatiotemporal regulation of DNA repair proteins..."; and **1** paper, "Intercellular mitochondrial transfer and trans-mitophagy...", has **no Data Availability statement at all** — the first instance of a completely absent statement across this four-issue survey series (JCS 139/15, JCS 139/16, and JCB 225/07 each had at least a generic statement in every article). No article in this issue deposits raw image data in a public, image-specific repository (e.g., BioImage Archive, IDR, EMPIAR).
```
