---
title: "Journal of Cell Biology, Volume 225, Issue 8 (17 articles)"
subtitle: "Bioimage analysis methods survey"
subject: Methods survey
date: 2026-09-24
---

```{note}
This report was built by downloading each article's PDF, converting it to plain text with `pdftotext -layout`, and extracting the bioimage-analysis workflow for every paper by exact-string search (grep/sed) of the converted text — not by fetching the article live from the publisher. Figure/panel numbers were cross-checked against each figure's own legend (the legend is treated as authoritative when it conflicts with a body-text citation). Every article was also checked for (1) genuine deferral of image-analysis *methodological detail* to a separate supplementary-methods document not included in this PDF, and (2) whether the article's Data Availability statement specifically addresses sample/raw image data, versus generic "data" language, versus no such statement at all. This is the largest issue surveyed so far (17 articles); several papers combine bioimage analysis with non-imaging assays (mass spectrometry, flow cytometry, plate-reader biochemistry) — those non-image steps are noted for completeness but flagged as such rather than counted as bioimage-analysis technique.
```

## At a glance

| Article | DOI | Key imaging software | Version given? | Measurement target | Code repo | Sample image data |
|---|---|---|---|---|---|---|
| [Opposing actomyosin pools in epithelial polarity](#epithelial-polarity-actomyosin) | [doi:10.1083/jcb.202408198](doi:10.1083/jcb.202408198) | Fiji, TrackMate, estimationstats.com | No (full list deferred to Table S9) | 1) ZO-1 particle trajectories; 2) Apical protein intensity (%apical); 3) Particle velocity; 4) Kymographs (gap) | None found | Not stated for images |
| [Asymmetric mitochondrial trafficking](#mitochondrial-trafficking-pnc) | [doi:10.1083/jcb.202409118](doi:10.1083/jcb.202409118) | MitoGraph, Ilastik, CellProfiler, Fiji | No | 1) Network volumetric segmentation; 2) Single-mitochondrion size/distance; 3) Photoconversion kymograph ratio; 4) Manual motion tracking; 5) Fission-event classification; 6) RNA-FISH spots; 7) EdU/nucleoid replication; 8) Network simulation | None found | **On request** (explicit "imaging data") |
| [PARP1 stalls translation, triggers stress granules](#parp1-stress-granules) | [doi:10.1083/jcb.202409149](doi:10.1083/jcb.202409149) | ImageJ (CellCounter), CellProfiler | No | 1) SG+ cell fraction; 2) Automated SG number/area; 3) Immunoblot densitometry; 4) Comet tail moment | None found | **On request** (explicit "raw microscopy images") |
| [Myosin-II nonhelical tailpiece](#myosin-ii-tailpiece) | [doi:10.1083/jcb.202501234](doi:10.1083/jcb.202501234) | MetaMorph, ImageJ (1.53t), Microvolution | Partial | 1) EM filament length/width/bare-zone; 2) VT-iSIM line-scan intensity; 3) Immunogold PREM measurements; 4) FRAP integrated density; 5) Stress-fiber scoring; 6) Manual migration tracking | None found (explicit "no original code") | Not stated for images |
| [Ca2+ transients drive cardiomyocyte proliferation](#calcium-transients-cardiomyocyte) | [doi:10.1083/jcb.202505134](doi:10.1083/jcb.202505134) | Fiji, NIS-Elements (v6.02.01) | Partial | 1) Cytosolic Ca2+ transients; 2) Cell-cycle IF staging; 3) PIV contractility; 4) Spindle-pole Ca2+ heatmap; 5) [Ca2+]i calibration; 6) Nuclear ploidy; 7) Sarcomere shortening | None found | Not stated for images |
| [Fam20 kinase Golgi retention](#fam20-golgi-retention) | [doi:10.1083/jcb.202507107](doi:10.1083/jcb.202507107) | NIS-Elements, ImageJ | No | 1) Fam20A/C localization/colocalization; 2) RUSH trafficking kinetics; 3) Immunoblot intensity; 4) Epithelial content (gap); 5) AlphaFold3 modeling | None found | Not stated for images (MS data publicly deposited, not images) |
| [Fibroblast depletion and epithelial resilience](#fibroblast-depletion-epithelial) | [doi:10.1083/jcb.202507165](doi:10.1083/jcb.202507165) | Imaris, Fiji, CellPose, AnaMorf, VasoMetrics | No | 1) Fibroblast nucleus count; 2) Dermal/membrane coverage; 3) Collagen fiber density/thickness; 4) Nucleus area (CellPose); 5) Basal-cell/PH3+/EdU+ scoring; 6) Delamination distance; 7) BM stiffness (AFM); 8) Capillary diameter | None found (custom MATLAB script undeposited) | **Public deposit** (Zenodo, "original figure files and raw data") |
| [Mitochondria limit CoQ export](#coq-export-mitochondria) | [doi:10.1083/jcb.202507174](doi:10.1083/jcb.202507174) | Incucyte base analysis software | No | 1) Live-cell death (Sytox Green); 2) Cas9-reporter fluorescence (modality unstated); 3) Lipidomic heatmap (non-micrograph) | None found | Not stated for images |
| [Bundled F-actin assembly/disassembly](#bundled-factin-assembly) | [doi:10.1083/jcb.202509039](doi:10.1083/jcb.202509039) | Fiji/ImageJ, JFilament, Gatan DigitalMicrograph | No | 1) Gel densitometry; 2) TIRFM bundle length/intensity/rates; 3) EM bundle width/spacing; 4) Length-width correlation; 5) Bristle F-actin disruption area | None found | Not stated for images |
| [E-/N-cadherin drive hepatic polarity](#cadherin-hepatic-polarity) | [doi:10.1083/jcb.202509170](doi:10.1083/jcb.202509170) | Fiji/ImageJ (2.16.0/1.54g), Microvolution, Huygens STED | Yes | 1) Cadherin/NuMA/RhoA/ROCK2 intensity ratios; 2) BC morphology classification; 3) BC-inheritance tracking; 4) RhoA biosensor dynamics; 5) ZO-1 length; 6) Spindle angle | None found | Not stated for images |
| [Aurora-A S-glutathionylation by Gstp](#aurora-a-glutathionylation) | [doi:10.1083/jcb.202509200](doi:10.1083/jcb.202509200) | Fiji (2.1.16.0/1.54p) | Yes | 1) Immunoblot densitometry; 2) Synapse-puncta colocalization density; 3) TMRM mitochondrial-potential intensity | None found | Not stated for images (bordering on-request) |
| [PS/RhoB connect PI4P and PA metabolism](#pi4p-pa-rhob) | [doi:10.1083/jcb.202509213](doi:10.1083/jcb.202509213) | FIJI | No | 1) PA-biosensor localization (gap); 2) RT-IMPACT PLD localization; 3) IMPACT flow cytometry (not microscopy); 4) Phalloidin area; 5) Immunoblot intensity | Third-party/non-image only (GitHub+Zenodo, sequencing scripts) | Not stated for images (sequencing data publicly deposited) |
| [PCM1 multimerization builds centriolar satellites](#pcm1-centriolar-satellites) | [doi:10.1083/jcb.202509238](doi:10.1083/jcb.202509238) | Imaris, Fiji, ImageJ, Aivia | No | 1) Granule volume/number; 2) Saturation-concentration threshold; 3) Ciliary SMO intensity; 4) FRAP mobile fraction; 5) Client-PCM1 colocalization; 6) U-ExM subdomain mapping; 7) Line-profile client position; 8) In vitro condensate quantification | None found | Not stated for images |
| [Signaling motif controls AQP12 function](#aqp12-signaling-motif) | [doi:10.1083/jcb.202512040](doi:10.1083/jcb.202512040) | ImageJ, ZEN | No | 1) AQP12-family channel localization; 2) Immunogold TEM (qualitative); 3) ZG activation colocalization (Pearson's); 4) Airyscan trafficking/colocalization; 5) Immunoblot densitometry | None found | Not stated for images |
| [VINE couples GAP-mediated Rab5 inactivation](#vine-rab5-inactivation) | [doi:10.1083/jcb.202601107](doi:10.1083/jcb.202601107) | MetaMorph (7.8.13.0), ImageJ, CellProfiler | Yes | 1) Endosomal puncta count; 2) Manual blinded puncta classification; 3) Split-DHFR colony-area screen; 4) AlphaFold2/3 modeling; 5) Western blot intensity | None found | Not stated for images |
| [XPG recruitment/release during NER](#xpg-ner-recruitment) | [doi:10.1083/jcb.202602121](doi:10.1083/jcb.202602121) | FIJI | No | 1) UV-damage (LUD) intensity ratio; 2) FRAP immobile fraction; 3) Real-time UV-C laser accumulation; 4) iFRAP half-life; 5) UV-C colony counting; 6) UDS/EdU intensity | None found | Not stated for images |
| [Procollagen 1 phase-separated condensates](#procollagen-condensates) | [doi:10.1083/jcb.202603129](doi:10.1083/jcb.202603129) | Icy (2.5.4.0), Fiji (1.54p), ImageJ | Yes | 1) Condensate segmentation/count/area; 2) Colocalization (Manders'); 3) FRAP T½; 4) ER/Golgi Col1A1 intensity; 5) Condensate-Sec31 coupling index; 6) Line-scan intensity | None found | Not stated for images |

(epithelial-polarity-actomyosin)=
## Opposing actomyosin pools establish epithelial polarity during naive pluripotency exit

Yu Shi, Nadia I. Manzi, Nicole R. Grater, Nitya Kopparapu, Lauren S. Ohler, Bailey N. de Jesus, and Daniel J. Dickinson — *Journal of Cell Biology*, Vol. 225, No. 8, e202408198 (2026). [doi:10.1083/jcb.202408198](doi:10.1083/jcb.202408198)

1. Single-particle tracking of ZO-1 clusters — TrackMate (Fiji plugin; difference-of-Gaussian detector, LAP tracker per Jaqaman et al., 2008; Ershov et al., 2022), tracks classified apical/basal/moving and normalized to sphere radius across spheroids. **→ Fig. 1, G and H; Fig. S1, B and C; Fig. 5 D; Fig. S5 C; Fig. 6 E; Fig. S6 C.**
2. Apical protein intensity (%apical) — manual circular ROIs in Fiji, %apical = (Int_apical/Int_total) × 100, for ZO-1, PCX, aPKCι, and myosin. **→ Fig. 2 F; Fig. 3, F and G; Fig. 5, B and C; Fig. 6 D; Fig. S2, B, D, and E; Fig. S4 C.**
3. Particle velocity calculation for moving ZO-1 particles, scatter-plotted — no specific software named for the velocity calculation itself. **→ Fig. 5 E; Fig. 6 F.**
4. Kymograph generation showing ZO-1 particle movement — named/shown in the figure legend, but no software, plugin, or algorithm is described anywhere in Methods for how the kymographs were built. **→ Fig. 1 F.**

```{note} Ambiguities and gaps flagged during extraction
:class: dropdown
- Kymograph generation (Fig. 1 F) has no stated software.
- The maximum-intensity projection step used to build nearly every displayed image is never explicitly tied to a tool in Methods (Fiji is named for cropping/rotation/brightness-contrast and for TrackMate input, but not explicitly for the projection step).
- Colocalization claims (e.g., "striking colocalization of aPKCι and ZO-1") are described only qualitatively — no colocalization coefficient or software is named, so these read as visual/qualitative assessments rather than a quantified pipeline.
- Table S9 is referenced twice as holding "the list of software packages and plugins used in this work," meaning additional software may exist beyond what the main-text Methods names.
```

```{admonition} Verbatim quote
"To track ZO-1 particles, the maximum z-projection of the time-lapse movie, focusing on the ZO-1 channel, was processed using the TrackMate FIJI plugin (Ershov et al., 2022)... The Linear Assignment Problem tracker (Jaqaman et al., 2008) was selected as the tracker, and frame-to-frame linking was set with a maximum distance of 1 µm."
```

- **Software named**: FIJI/Fiji (measurement, figure cropping/rotation/brightness-contrast); TrackMate (Ershov et al., 2022); LAP tracker (Jaqaman et al., 2008); Micro-Manager 2.0; estimationstats.com (bootstrap effect-size/estimation plots). No version numbers given in the main text; a full software/plugin list is deferred to Table S9.
- **Code repository**: None found. No custom analysis code is described or linked anywhere.
- **Sample image data**: Not stated for image data specifically (category c). Data Availability statement: "All primary data supporting this manuscript will be openly available in the Texas Data Repository upon manuscript acceptance... at `https://doi.org/10.18738/T8/YTOBXT`." — a resolvable institutional-repository DOI is given, but the statement uses only the generic term "primary data" and never names images or microscopy data specifically.
- **Based on prior methods**: The particle-tracking step cites Jaqaman et al. (2008) and Ershov et al. (2022); the estimation-statistics approach cites Claridge-Chang and Assam (2016) and Ho et al. (2019). The apical-intensity (%apical) formula and the velocity-calculation/scatter-plot step are both presented as the authors' own, uncited method.

(mitochondrial-trafficking-pnc)=
## Asymmetric mitochondrial trafficking balances perinuclear biogenesis to maintain network morphology

Julius Winter, Juan C. Landoni, Keaton B. Holt, Sheda Ben Nejma, Emine Berna Durmus, Tatjana Kleele, Elena F. Koslover, and Suliana Manley — *Journal of Cell Biology*, Vol. 225, No. 8, e202409118 (2026). [doi:10.1083/jcb.202409118](doi:10.1083/jcb.202409118)

1. Mitochondrial network volumetric segmentation/reconstruction — MitoGraph (Viana et al., 2015) on Huygens-deconvolved mito-mScarlet z-stacks, with companion R-scripts aggregating measurements. **→ Fig. 1, F and H; Fig. 2, A and B; Fig. 4 C; Fig. S3 C.**
2. Single-mitochondrion segmentation/tracking of photoconverted material — Ilastik pixel classification followed by CellProfiler's IdentifyPrimaryObjects to measure size/shape/distance to the photoconversion spot. **→ Fig. 1, K and L.**
3. Kymograph generation from photoconversion time-lapses — Fiji (segmented-line ROI, custom macro) plus Python for binning/ratio calculation. **→ Fig. 1, G–I; Fig. 4, E and G; Fig. S1, C–E.**
4. Manual mitochondrial motion tracking (anterograde/retrograde) — Fiji's manual tracking plugin (Fabrice P. Cordelières). **→ Fig. 1, M and N; Fig. 4 B.**
5. Manual mitochondrial fission-event detection/classification (midzone vs. peripheral) — no software named for this step. **→ Fig. 2 C.**
6. Mitochondrial motility/displacement under nocodazole — a pipeline adapted from Han et al. (2023), calculating frame-to-frame segmented overlap. **→ Fig. 1 O.**
7. RNA-FISH spot detection/classification (NDUFA10 mRNA) — bigfish Python library, manual cell-outline drawing in napari, Li thresholding for mitochondria, bigfish's "unet_3_classes_nuc" for nuclei. **→ Fig. 2, H and I.**
8. EdU/mtDNA nucleoid replication assay — CellProfiler segmentation of nuclei and nucleoid foci, distance-to-nucleus and EdU intensity computed automatically. **→ Fig. 2, D–G.**
9. Immunofluorescence quantification of TRAK1/TRAK2 knockdown/overexpression efficiency — CellProfiler, blinded image analysis. **→ Fig. S3 A.**
10. In silico graph-based mitochondrial network simulation (hybrid Brownian dynamics/Monte Carlo, per Holt et al., 2024) — computational, not empirical image analysis. **→ Fig. 3, A–L; Fig. S2, A–I.**

```{note} Ambiguities and gaps flagged during extraction
:class: dropdown
- "Li threshold" (mitochondria segmentation within the bigfish pipeline) and the "unet_3_classes_nuc" nucleus-segmentation algorithm are both named but not further described (no threshold value, no training/architecture detail).
- The "manually trained Ilastik algorithm" used to threshold mito-mEos3.2 images gives no detail on training-image count or classifier settings.
- The custom Fiji macro used for kymograph line-profile extraction is described in one sentence; its code is neither shown nor linked.
```

```{admonition} Verbatim quote
"The deconvolved z-stacks are processed by mitograph (Viana et al., 2015) running via the Windows subsystem for Linux (WSL2)... Once processed, the corresponding R-scripts from the mitograph authors aggregate the data and measurements into summary files, which were used for plotting in Python."
```

- **Software named**: MitoGraph (Viana et al., 2015); R; Python; Huygens Core; CellProfiler (Stirling et al., 2021); Ilastik (Berg et al., 2019); Fiji (with the Cordelières manual-tracking plugin); VisiView 5.0; NIS-Elements; bigfish (Imbert et al., 2021, preprint); napari; Stellaris RNA FISH Probe Designer v4.2. No version numbers given for MitoGraph, CellProfiler, Ilastik, or Fiji.
- **Code repository**: None found. The Zenodo entry (10.5281/zenodo.20008345) hosts only "numerical data underlying the figures," not source code.
- **Sample image data**: **On request** — image data explicitly named (category b). Data Availability statement: "The numerical data underlying the figures are openly available in Zenodo... Large imaging data are available from the corresponding author upon reasonable request." — the numerical data are openly deposited, but the raw imaging data are explicitly gated behind a reasonable-request clause.
- **Based on prior methods**: Micropatterning follows Azioune et al. (2010); volumetric segmentation cites Viana et al. (2015); the motility/displacement pipeline is adapted from Han et al. (2023); RNA-FISH analysis cites the bigfish preprint and napari; the network simulation is detailed in Holt et al. (2024). The fission-event classification and the custom kymograph macro/line-profile processing are presented without a methodological citation.

(parp1-stress-granules)=
## PARP1 hyperactivity stalls translation and triggers stress granule formation following DNA damage

Maria Tereshchenko, Rebecca Earnshaw, Christopher Chin Sang, Minjung Won, Jeanine L. Van Nostrand, Ryan C. Russell, and Hyun O. Lee — *Journal of Cell Biology*, Vol. 225, No. 8, e202409149 (2026). [doi:10.1083/jcb.202409149](doi:10.1083/jcb.202409149)

1. Fraction of cells with stress granules (SG+/SG−) — manual counting with ImageJ's CellCounter plugin, cross-validated by an automated CellProfiler pipeline. **→ Fig. 2, B, D, F, G, and H; Fig. 3, F, H, and I; Fig. 4, G and H; Fig. 5, F and G.**
2. Automated SG number/area per cell — full CellProfiler pipeline described in Methods (IdentifyPrimaryObjects for nuclei/granules, IdentifySecondaryObjects for cytoplasm, MaskObjects, RelateObjects, MeasureObjectSizeShape, ExportToSpreadsheet). **→ likely Fig. S1 F (not explicitly stated).**
3. Immunoblot band-intensity quantification — mean gray value in ImageJ, normalized to loading control. **→ Fig. 1 E; Fig. 4, B–E; Fig. 5, A–D; Fig. 6, B and D.**
4. Alkaline comet assay tail-moment quantification — R&D Systems kit, "quantification was performed using ImageJ." **→ Fig. 1 B.**
5. Live-cell imaging of SG dynamics over time (Okolab chamber, Andor Dragonfly) — acquisition parameters given, but no analysis/quantification method is described anywhere for these datasets. **Not explicitly figure-mapped — flagged as unmapped.**

```{note} Ambiguities and gaps flagged during extraction
:class: dropdown
- Live-cell SG-dynamics imaging (20 h time-lapse) has acquisition parameters but no stated analysis method or figure mapping.
- CellProfiler pipeline threshold/parameter settings (segmentation thresholds, object size ranges) are not specified beyond module names.
- Despite describing a live-cell imaging protocol, no corresponding supplementary movie is referenced in the "Online supplemental material" section — an inconsistency worth flagging.
```

```{admonition} Verbatim quote
"To quantify stress granule number and area per cell, Z-stack images were split into single slices and individual color channels using ImageJ. Nuclear DAPI and GFP stress granule channels were uploaded into CellProfiler. First, DAPI was detected by 'IdentifyPrimaryObjects,'... Next, stress granules were identified using IdentifyPrimaryObjects, and 'RelateObjects' was used to detect which parent nucleus each stress granule belongs to."
```

- **Software named**: ImageJ (CellCounter plugin; also used for comet-assay quantification and band-density measurement); CellProfiler (module names given, no version); GraphPad Prism 11; Andor Fusion software; Zen Blue software; BioRender (for the Fig. 7 schematic only).
- **Code repository**: None found.
- **Sample image data**: **On request** — image data explicitly named (category b). Data Availability statement: "All raw immunoblot images are published with the manuscript. Raw microscopy images are available from the corresponding author upon request." — explicitly names "Raw microscopy images," gated behind a request clause.
- **Based on prior methods**: The ATP-bioluminescence assay cites Hipler et al. (1998); several cell lines are cited to their originating papers (Poser et al., 2008; Van Nostrand et al., 2020; Kim et al., 2011; Kedersha et al., 2016; etc.). The ImageJ CellCounter plugin, the CellProfiler pipeline, and the comet-assay ImageJ quantification are all presented without a citation to a prior methodological source.

(myosin-ii-tailpiece)=
## Role of the nonhelical tailpiece of myosin-II in regulating filament architecture and function

Kangji Wang, Shi Shu, Xiong Liu, and Erfei Bi — *Journal of Cell Biology*, Vol. 225, No. 8, e202501234 (2026). [doi:10.1083/jcb.202501234](doi:10.1083/jcb.202501234)

1. Negative-staining EM of in-vitro-polymerized NM-II filaments — filament length, width, and bare-zone length measured with MetaMorph. **→ Fig. 1, B–F; Fig. 2; Fig. 3, A–D; Fig. 4, A–F; Fig. 5, A–C.**
2. VT-iSIM super-resolution imaging of GFP-tagged NM-IIA — deconvolved with the Microvolution plugin in ImageJ; GFP intensity line-scan via ImageJ's line-scan function. **→ Fig. 7, A and B.**
3. Immunogold PREM of bipolar filaments — filament length, bare-zone length/width measured from >40 filaments per condition; no measurement software explicitly named for this step. **→ Fig. 7 C; Fig. 8, E–G; Fig. 9, D–F.**
4. FRAP of GFP-NM-IIA in stress fibers — manual polygon ROI in ImageJ, integrated density over time. **→ Fig. 7, D–G.**
5. Time-lapse stress-fiber disassembly/aggregation scoring after Y-27632 treatment — percentage of cells scored over time; scoring method/software not explicitly described. **→ Fig. 8, A–C; Fig. 9, A–C.**
6. Immunofluorescence percent-positive/negative cell scoring (pRLC, ppRLC) — imaging software not explicitly named for this quantification step. **→ Fig. 8 D; Fig. S1 B; Figs. S3 and S4.**
7. Correlative light-PREM (CL-PREM) — fluorescence/PREM images aligned/overlaid in Adobe Photoshop, per Shutova et al. (2012) and Yang and Svitkina (2019). **→ Fig. 9, D–F.**
8. Manual cell-migration tracking — ImageJ's manual tracking function on nuclear position. **→ Fig. 10, A and B; Fig. S5.**

```{note} Ambiguities and gaps flagged during extraction
:class: dropdown
- Immunogold PREM filament measurements (Fig. 7 C) have no stated software, unlike the earlier MetaMorph-based negative-staining EM measurements.
- The percentage-of-cells scoring for stress-fiber retention/aggregation and pRLC/ppRLC status (manual visual scoring vs. automated thresholding, blinding, criteria for "aggregate") is not described.
- The line-scan criteria for distinguishing "myosin head" vs. "bare zone" regions (Fig. 7 B) are not detailed beyond naming the ImageJ line-scan tool.
```

```{admonition} Verbatim quote
"Filament lengths and widths were measured with MetaMorph software (MetaMorph, Inc.)."

"A polygon was drawn encircling the bleached area to calculate the integrated density within the area over time."
```

- **Software named**: MetaMorph (and MetaMorph 7.10.4.431 for microscope control); VisiView; NIH ImageJ (1.53t); Microvolution (ImageJ plugin); Microsoft Excel; GraphPad Prism 9.4.1; R (ver. 3.0.1); Adobe Photoshop.
- **Code repository**: None found — the Data Availability statement explicitly states "This paper does not contain any original code."
- **Sample image data**: Not stated for image data specifically (category c). Data Availability statement: "The data supporting the findings of this study are included in the paper and its supplemental information and will be available upon request. This paper does not contain any original code." — generic "data" language, no image-specific mention or repository.
- **Based on prior methods**: Recombinant myosin purification cites Billington et al. (2013) and Liu et al. (2017); PREM processing cites Shutova et al. (2012); CL-PREM cites Yang and Svitkina (2019); live-cell imaging/Western blotting cite Wang et al. (2023). The MetaMorph-based EM filament measurement, the VT-iSIM protocol, the FRAP method, and the migration-tracking assay are all presented without a methodological citation.

(calcium-transients-cardiomyocyte)=
## Sequential changes in calcium transients during M phase regulate cardiomyocyte proliferation

Honghai Liu, Niyatie Ammanamanchi, Jocelyn D. Mich-Basso, Brian K. Panama, Yao Li, Winston Huang, Dena Almeida, Christopher M. Lewarchik, Brendan Lo, Yijen Wu, Michael Gotthardt, Michael I. Kotlikoff, Wolfgang Baehr, Randall Rasmusson, Guy Salama, and Bernhard Kühn — *Journal of Cell Biology*, Vol. 225, No. 8, e202505134 (2026). [doi:10.1083/jcb.202505134](doi:10.1083/jcb.202505134)

1. Cytosolic Ca²⁺ transient (CaT) imaging (Rhod2-AM/Fluo4-AM/GCaMP8) — quantified in Fiji (ROI Manager, Polygon Selection, Multi Measure) to F/F0 traces. **→ Fig. 1 (B, C, E, F, H–L); Fig. 2 (A–E, J–N); Fig. 3 (A, B, F–H); Fig. 6; Fig. 7 (C–E, J–L).**
2. Post hoc immunofluorescence cell-cycle staging (Ki67, H3P, Aurora B, Hoechst) for phase classification. **→ Fig. 1, A and D; Fig. 2, F and G; Fig. S2 A.**
3. Particle Image Velocimetry (PIV) contractility analysis — ImageJ/Fiji PIV plugin (Tseng et al., 2012). **→ Fig. 2, H and I.**
4. Spatial Ca²⁺ heatmap ("Ca²⁺ valley") at spindle poles — Fiji's 3D surface plot function, ratio of spindle-pole to cytoplasm intensity. **→ Fig. 5, A–F.**
5. [Ca²⁺]i calibration (nanomolar) — Rhod2 fluorescence calibrated per Del Nido et al. (1998), Kd = 720 nM (Du et al., 2001). **→ Fig. 2, J–N; Fig. 3, A and B.**
6. Nuclear ploidy quantification — integrated Hoechst intensity in ImageJ/Fiji, normalized to 4N/2N references. **→ Fig. 6, G–K.**
7. Sarcomere shortening fraction — SiR-actin M-line-to-M-line distance, manual measurement with no software explicitly named. **→ likely Fig. S1, A–C (inferred, not explicit).**

```{note} Ambiguities and gaps flagged during extraction
:class: dropdown
- Sarcomere-shortening measurement (Fig. S1, A–C) describes manual distance measurement of "dark regions (M-line positions)" but names no specific software or plugin, unlike other steps that explicitly cite Fiji/ImageJ or NIS-Elements.
- The "3D surface plot function of the Fiji software" used for Ca²⁺ heatmaps is named but its parameters/settings are not detailed.
- Image stitching for large-area acquisition (500–2,000 cells/image) is mentioned only as "provided by the Nikon NIS-Elements software," with no specific module/algorithm named.
```

```{admonition} Verbatim quote
"To extract CaTs data from cardiomyocytes in the calcium fluorescence recordings, the target cells were outlined in Fiji using the Polygon Selections tool, and the selected areas were added to the ROI Manager... The Multi Measure function in ROI Manager was used to measure the mean gray value of each selected cardiomyocyte and the background region across all frames."
```

- **Software named**: Fiji; ImageJ/Fiji (PIV plugin, Tseng et al., 2012); Nikon NIS-Elements (Version 6.02.01), including its "Elements Denoise.ai" module; GraphPad Prism (Ver. 10); Microsoft Excel.
- **Code repository**: None found.
- **Sample image data**: Not stated for image data specifically (category c). Data Availability statement: "This study includes no data deposited in external repositories. All materials are available from the corresponding author upon reasonable request and without undue delay." — generic language covering "materials," no image-specific mention.
- **Based on prior methods**: PIV analysis cites Tseng et al. (2012); the [Ca²⁺]i calibration equation is adapted from Del Nido et al. (1998) with the Kd from Du et al. (2001); the cell-cycle reporter system cites Han et al. (2020) and Sakaue-Sawano et al. (2008); the αMHC-GCaMP8 mouse cites da Silva Lopes et al. (2011). The Fiji-based CaT extraction, spindle-pole heatmap/ratio quantification, nuclear ploidy quantification, and sarcomere-shortening measurement are all presented without an external methods citation.

(fam20-golgi-retention)=
## Receptor-mediated Golgi retention of Fam20 kinases tunes secretome phosphorylation during lactation

Xiaotong Yang, Jueyin He, Xiulan Chen, Xi'e Wang, Chenyun Hu, Xuqian Zhao, Xinxin Chen, Jiaojiao Yu, Ping Liu, Jifeng Wang, Xi Wang, Junjie Hu, Mei Ding, Fuquan Yang, Chih-chen Wang, and Lei Wang — *Journal of Cell Biology*, Vol. 225, No. 8, e202507107 (2026). [doi:10.1083/jcb.202507107](doi:10.1083/jcb.202507107)

1. Confocal fluorescence imaging of Fam20A/Fam20C subcellular localization/colocalization with ERGIC2/ERGIC3/PDI/GM130 — Nikon C2si, NIS-Elements acquisition; n > 200 cells quantified for subcellular distribution, but no segmentation/scoring method is described. **→ Fig. 1, I and J; Fig. 4, J and K; Fig. 5, A and D.**
2. RUSH live-cell imaging of ER-to-Golgi trafficking kinetics (Fam20A/C-SBP-EGFP/mApple), Golgi-region intensity over time. **→ Fig. 2, A–C, E, and F; Fig. 3, C and D.**
3. Immunoblot band-intensity quantification (ImageJ, background-subtracted) for secretion, phosphorylation ratios, and co-IP signal. **→ Fig. 1 F; Fig. 3, B, F, and H; Fig. 4 (E, G, M, O, Q, R, T, U); Fig. 5 (F, H, J).**
4. Epithelial content quantification from H&E-stained mammary tissue — method not described beyond "quantified." **→ Fig. 6 E.**
5. AlphaFold3 structural prediction of the ERGIC2-ERGIC3 heterodimer — computational rendering, not a micrograph. **→ Fig. 4 A.**

```{note} Ambiguities and gaps flagged during extraction
:class: dropdown
- The cell-counting/scoring method for "subcellular distribution" quantification (n > 200 cells, Fig. 1 J, Fig. 4 K) is not described — no criteria, blinding, or software named.
- "Epithelial content" quantification for the H&E images (Fig. 6 E) has no image-analysis tool, thresholding, or ROI method named.
- No colocalization statistic (Pearson's/Manders') or dedicated software is named despite repeated qualitative colocalization claims ("partially overlapping," "complete colocalization").
```

```{admonition} Verbatim quote
"Images were acquired using a 60× oil immersion objective (NA = 1.40)... Image acquisition was performed using NIS-Elements software (Nikon)... Immunoblot band intensities were quantified using ImageJ (NIH) after background subtraction."
```

- **Software named**: NIS-Elements (Nikon); Leica ImageScope; ImageJ (NIH); GraphPad Prism (v.9.11); Proteome Discoverer (v.2.4.1.15); SequestHT; Percolator; PhosphoRS; NAguideR; DAVID; AlphaFold 3; SignalP-6.0; TMHMM.
- **Code repository**: None found.
- **Sample image data**: Not stated for image data specifically (category c). Data Availability statement: "Mass spectrometry proteomics data have been deposited to the ProteomeXchange Consortium... under the dataset identifier PXD059444. Supporting data for the findings of this study can be found in the manuscript and its supplementary files. Source data for the WB results are provided with this paper." — the only resolvable public accession covers MS proteomics data, not microscopy images; the imaging data are addressed only by generic "supporting data" language.
- **Based on prior methods**: Lentiviral transduction cites Cheng et al. (2023); protein purification cites Niu et al. (2016) and Xiao et al. (2013); urea-PAGE for phospho-β-casein cites Kinoshita et al. (2009); several RUSH constructs cite the authors' own prior paper (Chen et al., 2021). The core confocal-imaging/colocalization steps, the subcellular-distribution scoring, and the epithelial-content quantification are all presented without a methodological citation.

(fibroblast-depletion-epithelial)=
## Fibroblast depletion reveals mammalian epithelial resilience across neonatal and adult stages

Isabella M. Gaeta, Shuangshuang Du, Clémentine Villeneuve, David G. Gonzalez, Catherine Matte-Martone, Smirthy Ganesan, Deandra Simpson, Hilldana Tibebu, Jessica L. Moore, Chen Yuan Kam, Sara Gallini, Haoyang Wei, Fabien Bertillot, Dagmar Zeuschner, Lauren E. Gonzalez, Ushnish Rana, Kaelyn D. Sumigray, Sara A. Wickström, and Valentina Greco — *Journal of Cell Biology*, Vol. 225, No. 8, e202507165 (2026). [doi:10.1083/jcb.202507165](doi:10.1083/jcb.202507165)

1. Fibroblast density/nucleus quantification (adult) — Imaris "spot" function (7 µm diameter) on PDGFRα-H2BGFP z-stacks, manual correction. **→ Fig. 1, C and E.**
2. Dermal-signal isolation/flattening — FIJI stitching → Imaris surface creation from SHG signal + distance-transformation masking → custom MATLAB flattening script → re-imported to FIJI for %membrane-coverage quantification. **→ Fig. 1 A; Fig. 2, B and D.**
3. Collagen fiber density (SHG mean fluorescence intensity), thickness, and lacunarity — FIJI thresholding and the AnaMorf FIJI plugin. **→ Fig. 3, A–D.**
4. Fibroblast nucleus area (2D) — CellPose instance segmentation, morphometrics via scikit-image's regionprops. **→ Fig. 2 E.**
5. Epidermal basal-cell/PH3+/EdU+ scoring — FIJI's manual cell counter or Imaris surface-mask + spot function. **→ Fig. 1, D, F, G, I, J, and K; Fig. 2, G–J; Fig. S1, G–J.**
6. Delamination distance quantification (48-h EdU chase) — manual line-measurement tool in FIJI. **→ Fig. 3, H and I.**
7. Basement-membrane stiffness — AFM (JPK NanoWizard 2), Hertz-model fitting in JPK Data Processing Software. **→ Fig. 3, F and G.**
8. Capillary diameter — VasoMetrics FIJI plugin. **→ Fig. S3 G.**

```{note} Ambiguities and gaps flagged during extraction
:class: dropdown
- CellPose is used with no version, model type, or parameters (diameter, thresholds) given.
- Imaris and FIJI/ImageJ are both central to multiple quantifications but carry no version number anywhere.
- The custom MATLAB flattening script is described only functionally; its code is not deposited (a genuine gap, distinct from the raw-data deposit noted below).
- The neonatal fibroblast nucleus-count method (Fig. 2, A and C) is not explicitly restated in Methods — only the "adult" paragraph gives the explicit Imaris spot-function protocol, so the neonatal method is inferred rather than confirmed.
```

```{admonition} Verbatim quote
"Raw live imaging data were imported into FIJI (ImageJ, National Institutes of Health) for stitching (Preibisch et al., 2009). To reduce the dimensionality of 3D imaging stacks, we used Imaris software (Oxford Instruments) to isolate the upper dermal signal and a custom MATLAB script (MathWorks) to flatten it."
```

- **Software named**: FIJI (ImageJ); Imaris; custom MATLAB script; AnaMorf FIJI plugin; CellPose; scikit-image (regionprops/regionprops_table); VasoMetrics FIJI plugin; JPK SPM Control Software v.5; JPK Data Processing Software; GraphPad Prism v9.4; Python (NumPy, SciPy); FACSDiva v8.0.1; FlowJo v.10.9.0. No version numbers given for FIJI, Imaris, CellPose, AnaMorf, or VasoMetrics.
- **Code repository**: None found for the custom MATLAB flattening script or any other analysis code (the Zenodo record below hosts raw figure data, not code).
- **Sample image data**: **Publicly deposited** (category a). Data Availability statement: "Original figure files and corresponding raw data are available on Zenodo at https://zenodo.org/records/20668188." — explicitly names figure/raw image data with a resolvable, specific record URL.
- **Based on prior methods**: FIJI stitching cites Preibisch et al. (2009); the EdU pulse-chase protocol is adopted from Cordero-Espinoza et al. (2021); the FACS dissociation protocol is adapted from Yang et al. (2017). The Imaris workflow, custom MATLAB script, CellPose segmentation, AnaMorf/VasoMetrics plugin use, AFM Hertz-model fitting, and manual delamination scoring are all presented without a methodological citation.

(coq-export-mitochondria)=
## Mitochondria limit coenzyme Q export under cholesterol biosynthetic stress

Marjana Ndoci, Sharanya Bhattacharya, Ishita Agrawal, Yvonne Hinze, Kathrin Lemke, Anna-Lena Schumacher, Esther Uijttewaal, Ulrich Elling, Steffen Lawo, Patrick Giavalisco, Thomas Langer, and Soni Deshwal — *Journal of Cell Biology*, Vol. 225, No. 8, e202507174 (2026). [doi:10.1083/jcb.202507174](doi:10.1083/jcb.202507174)

This is primarily a lipidomics/mass-spectrometry and CRISPR-screen paper; true micrograph-based bioimage analysis is minimal.

1. Live-cell death quantification (Incucyte) — Sytox Green-positive area normalized to phase-contrast area, masks generated by "Incucyte base analysis software." **→ Fig. 2, g–k and m; Fig. 3 q; Fig. S2 b.**
2. Cas9-activity reporter assay (BFP-GFP fluorescence loss) — the imaging modality (flow cytometry vs. microscopy) is not stated anywhere in Methods. **→ Fig. 1, a–c; Fig. S1, a–c** (flagged as unmapped/ambiguous technique).
3. Lipidomic fraction-distribution heatmap — built from mass-spectrometry values, not a micrograph; no software explicitly tied to generating this figure. **→ Fig. 3 l.**

```{note} Ambiguities and gaps flagged during extraction
:class: dropdown
- The BFP-GFP Cas9-reporter assay (Fig. 1, a–c; Fig. S1, a–c) has no corresponding Methods paragraph at all — not even a pointer to supplemental methods — a true methodological omission.
- No image-analysis software (ImageJ/Fiji/CellProfiler) is named anywhere in the document; only the Incucyte's bundled base analysis software.
- Western blot images (ChemiDoc) are presented qualitatively with no densitometry/quantification method described.
```

```{admonition} Verbatim quote
"Cell death was measured using an Incucyte Live-Cell Analysis system (Sartorius) (Deshwal et al., 2023)... To quantify cell death, a mask was generated using the Incucyte base analysis software, analyzing both phase-contrast and green channels. The area occupied by green objects was normalized to the phase area per well."
```

- **Software named**: FastQC v0.11.8; cutadapt v4.5; MAGeCK v0.5.9.5; TraceFinder; Instant Clue v3.0; Incucyte base analysis software; ChemiDoc Imaging System; BioRender.
- **Code repository**: None found.
- **Sample image data**: Not stated for image data specifically (category c). Data Availability statement: "The data underlying Figs. 1, 2, 3, and 4 are available in the published article and its online supplemental material." — generic, no accession/repository, and no explicit mention of the paper's few image-type outputs (Incucyte images, blots, reporter images).
- **Based on prior methods**: The Incucyte cell-death assay, the fractionation method, and the CoQ mass-spectrometry measurement are all cited to the group's own prior paper (Deshwal et al., 2023); the Cas9 reporter cites Tzelepis et al. (2016) but with no accompanying Methods protocol; MAGeCK-based screen analysis cites Li et al. (2014).

(bundled-factin-assembly)=
## Synergistic assembly, disassembly, and protection of complex forms of bundled F-actin

Sudeepa Rajan, Jimok Yoon, Heng Wu, Raju Baskar, Roman Aguirre, Jonathan R. Terman, and Emil Reisler — *Journal of Cell Biology*, Vol. 225, No. 8, e202509039 (2026). [doi:10.1083/jcb.202509039](doi:10.1083/jcb.202509039)

1. Actin sedimentation (pelleting) assays — SDS-PAGE gels quantified by densitometry in ImageJ. **→ Fig. 1, B–D; Fig. 2 A; Fig. 3, A–C; Fig. 7 C.**
2. TIRFM imaging of actin bundle assembly/disassembly — Fiji analysis (rolling-ball background subtraction; bundle length via the JFilament plugin; intensity via line-scan; thinning/severing rates via ROI Manager; colocalization/kymographs via Multi Kymograph). **→ Fig. 2, C and D; Fig. 4 C; Fig. 5 B; Fig. 6 B; Fig. S1 D; Figs. S2–S5.**
3. Negative-stain EM of actin bundles — bundle width/interfilament spacing/filament number measured in Gatan Digital Micrograph and ImageJ; no specific measurement plugin/macro named for this step. **→ Fig. 1 F; Table 1; Fig. 2, E and F; Fig. S2, F and G.**
4. Length-width correlation analysis, combining TIRFM length and EM width. **→ Fig. S2 G.**
5. In vivo confocal imaging of Drosophila bristle F-actin — color-threshold isolation, manual polygon ROI, ImageJ "Measure" function for area/integrated density, used to compute % disrupted bundles and disassembled area. **→ Fig. 8, D–I.**

```{note} Ambiguities and gaps flagged during extraction
:class: dropdown
- The EM bundle-width/interfilament-spacing/filament-count measurement names only "Gatan digital micrograph software... and ImageJ" without a specific measurement plugin or macro — contrast with the TIRFM section, which names JFilament, the line-scan tool, and ROI Manager explicitly.
- Three-color TIRFM colocalization (Fig. S1 D) is described only briefly, without detail on how colocalization (vs. mere co-presence) was quantified or thresholded.
- The JFilament plugin is cited with the same RRID as Fiji itself (RRID:SCR_002285) — likely a citation error in the source article, leaving JFilament without its own distinct machine-readable identifier.
```

```{admonition} Verbatim quote
"All TIRFM data were analyzed using Fiji (ImageJ) software... before each analysis, background subtraction was done using rolling ball radius algorithm (ball radius 50 pixels)... The length of actin filaments was measured manually by using JFilament plugin in Fiji."
```

- **Software named**: ImageJ; Fiji; JFilament plugin; Multi Kymograph (ImageJ plugin); Slidebook 6; SigmaPlot 14; GraphPad Prism (Version 10.5); Gatan Digital Micrograph; Zen 2.3; Zeiss Axiovision; Adobe Photoshop; Microsoft PowerPoint.
- **Code repository**: None found.
- **Sample image data**: Not stated for image data specifically (category c). Data Availability statement: "The data are available in the published article and its online supplemental material and are also available from the corresponding authors upon request." — a single generic statement; it never singles out raw TIRFM movies, EM micrographs, or confocal image files.
- **Based on prior methods**: The TIRFM protocol and its image-analysis pipeline are both explicitly "the same as described by Rajan et al. (2023c)"; light-scattering and bristle-imaging methods likewise cite Rajan et al. (2023c) and Hung et al. (2010); the NADPH-consumption assay cites Grintsevich et al. (2016) and Hung et al. (2011). The EM imaging/analysis procedure itself, the bristle confocal fluorescence quantification, and the length-width correlation analysis are all presented without a citation.

(cadherin-hepatic-polarity)=
## E- and N-cadherin drive hepatic polarity and lumen elongation via opposing effects on RhoA activity

Junya Hayase, Li Yang, Yu-Heng Zhou, Kangji Wang, Cheng-Ran Xu, and Erfei Bi — *Journal of Cell Biology*, Vol. 225, No. 8, e202509170 (2026). [doi:10.1083/jcb.202509170](doi:10.1083/jcb.202509170)

1. Confocal/iSIM/STED fluorescence imaging of cadherins, NuMA, RhoA, ROCK2 — quantitative intensity-ratio image analysis (Fiji/ImageJ) for polar-cortex/AJ ratio, basal-cleavage-furrow/AJ ratio, and apical/cytoplasm ratios. **→ Fig. 3 K; Fig. 4, H and J; Fig. 5, A, C, and K.**
2. Cell-polarity/bile canaliculus (BC) morphology classification (primordial vs. tubular, long:short axis ratio >2.0) — manual classification, method previously established (Wang et al., 2014). **→ Fig. 2, D–I; Fig. 3, C, F, and G; Fig. 4 F; Fig. 5, F and M; Fig. 6, C, D, and F.**
3. Live-cell tracking of symmetric vs. asymmetric BC inheritance (Mzt1-GFP centrosome, radixin-mScarlet apical marker) — described only in the figure legend, with no algorithmic/quantitative detail in Methods. **→ Fig. 4 C.**
4. RhoA-activity biosensor (dT-2×rGBD) dynamics during cytokinesis. **→ Fig. 5, B and C.**
5. ZO-1 length measurement. **→ Fig. 2 J.**
6. Spindle-angle measurement. **→ Fig. S3 H.**

```{note} Ambiguities and gaps flagged during extraction
:class: dropdown
- The method for scoring/tracking symmetric vs. asymmetric BC inheritance from time-lapse movies is described in the figure legend only, with no algorithmic detail (manual visual scoring vs. automated tracking) in the "Image processing and analysis" Methods paragraph.
- The gene ontology (GO) enrichment analysis (Fig. 4 B) names no specific software/database or statistical parameters.
- No statistical/image-analysis software is named for the PCA plot in Fig. 1 A (scRNA-seq reanalysis) beyond the original Yang et al. (2017) dataset citation.
```

```{admonition} Verbatim quote
"All images were processed and analyzed using Fiji/ImageJ (2.16.0/1.54 g). To quantify the intensity ratio of E-cadherin or N-cadherin on the polar cortex to AJ, the mean intensity of the polar membrane signal was divided by the mean intensity on AJ."

"Quantification of cells with BCs was performed as previously described (Wang et al., 2014), with minor modifications."
```

- **Software named**: Fiji/ImageJ (2.16.0/1.54g); Microvolution deconvolution plugin; VisiView; MetaMorph; Huygens STED deconvolution software; Image Studio (LI-COR); MaxQuant 2.4.2.0; R package limma (v3.64.1); RStudio (ver. 2024.12.0+467).
- **Code repository**: None found.
- **Sample image data**: Not stated for image data specifically (category c). Data Availability statement: "The data supporting the findings of this study are included in the paper and its supplemental information and are available from the primary corresponding author... upon reasonable request." — generic language, no image-specific mention; per-figure "Source data" pointers cover only immunoblot images, not the microscopy/live-cell data.
- **Based on prior methods**: BC/polarity classification cites Wang et al. (2014); the ReCLIP assay cites Smith et al. (2011); the BioID proximity-labeling assay cites Cho et al. (2020); the liver-lobe culture cites Yang et al. (2017). The core quantitative intensity-ratio image-analysis methods (polar cortex/AJ, NuMA, RhoA/ROCK2, ZO-1 length, spindle angle) are all presented as original to this study, without a literature citation.

(aurora-a-glutathionylation)=
## Redox-dependent S-glutathionylation of Aurora-A kinase by Gstp promotes postsynaptic maturation

Shuji Wakatsuki, Akiko Yumoto, Takehiro Suzuki, Naoshi Dohmae, and Toshiyuki Araki — *Journal of Cell Biology*, Vol. 225, No. 8, e202509200 (2026). [doi:10.1083/jcb.202509200](doi:10.1083/jcb.202509200)

1. Immunoblot densitometry — quantification of phosphorylated/glutathionylated Aurora-A, Gst isoforms, ERK phosphorylation, synaptic markers, Raf1 phosphorylation, and cell-cycle markers, using Fiji (2.1.16.0/1.54p) on chemiluminescent scans. **→ Figs. 1–10 and Figs. S1, S2, S4, S5, S6 (blot-derived bar graphs throughout).**
2. Quantitative confocal immunofluorescence/synapse-puncta colocalization — synapse density defined as PSD95/synaptophysin (or PSD95/synapsin I) colocalized puncta per unit dendrite length, in randomly chosen 25 µm dendritic segments. **→ Fig. 1 G; Fig. 3, G and H; Fig. 6, A–D and E–H; Fig. 7, C and D; Fig. 8, C and D; Fig. 9, E and F; Fig. 10, E and F; Fig. S4, A and B.**
3. TMRM mitochondrial-membrane-potential imaging — Keyence BZ-X710 acquisition, fluorescence-intensity quantification within neurite ROIs in Fiji. **→ approximately Fig. S5, F–H (soft/approximate mapping — legend text was ambiguous).**

```{note} Ambiguities and gaps flagged during extraction
:class: dropdown
- The precise algorithm/threshold used to define "colocalized"/"double-positive" puncta is never specified — Methods and the Fig. S4 legend describe the ROI-selection and puncta-counting logic conceptually, but not the quantitative colocalization criterion or threshold.
- No specific Fiji/ImageJ plugin, macro, or script is named for puncta counting, colocalization masking, or intensity measurement — only "ImageJ/Fiji" generically.
- Table S3 is stated to hold "a comprehensive list of antibodies, cell lines, reagents, and software used in this study, including catalog numbers and RRIDs," but its contents were not retrievable from the main-text PDF conversion, so additional named software may exist there.
```

```{admonition} Verbatim quote
"To avoid bias, ROIs were selected as 25 μm length segments of dendrites, randomly chosen within a distance of 20–100 μm from the cell body of each neuron. Synapse density was strictly defined as the number of puncta where synaptophysin and PSD95 signals colocalized (merged)."
```

- **Software named**: Fiji (2.1.16.0/1.54p, also printed as "Fuji" in one instance — apparent typo); ImageJ/Fiji (postacquisition processing); Adobe Photoshop; FluoView FV10-ASW 3.1; FusionCapt Advance.
- **Code repository**: None found.
- **Sample image data**: Not stated for image data specifically, bordering on-request (category c). Data Availability statement: "All data supporting the findings of this study are available within the paper and its supplemental materials, including source data files. Additional data are available from the corresponding author upon reasonable request." — generic "data" language; "source data files" refer to the JCB-standard blot/quantification files, not raw confocal image stacks.
- **Based on prior methods**: The general imaging/quantification approach cites the authors' own prior papers (Wakatsuki and Araki, 2021; Wakatsuki et al., 2021a, 2021b); the PEG-PCMal thiol-labeling assay cites Burgoyne et al. (2013); TMRM quantification cites Scaduto and Grotyohann (1999). The synapse-puncta-colocalization quantification method itself carries no independent, uncited citation for the confocal image-analysis pipeline beyond the authors' own prior work.

(pi4p-pa-rhob)=
## Phosphatidylserine and RhoB connect PI4P and PA metabolism to maintain plasma membrane identity

Shiying Huang, Yeun Ju Kim, Xiaofu Cao, Timothy W. Bumpus, Mira Sohn, Matthew Tyler Menold, Ryan K. Dale, Jin Joo Kang, Saori Uematsu, Shagun Gupta, Shu-Bing Qian, Haiyuan Yu, Tamas Balla, and Jeremy M. Baskin — *Journal of Cell Biology*, Vol. 225, No. 8, e202509213 (2026). [doi:10.1083/jcb.202509213](doi:10.1083/jcb.202509213)

1. Live-cell confocal imaging of PA localization (GFP-Nir2-LNS2(816–1181) biosensor) — quantification stated only as "performed on 5 cells per condition," with no metric or software specified. **→ Fig. 1 D; Fig. 2 E.**
2. RT-IMPACT confocal imaging of active-PLD localization via click labeling — a qualitative/localization readout, no quantification pipeline described. **→ Fig. 1 G.**
3. IMPACT labeling quantified by flow cytometry (not microscopy) — BODIPY fluorescence as a PLD-activity readout. **→ Figs. 1–6 (multiple panels).**
4. Phalloidin (F-actin) staining/imaging, quantified by "selecting 10 areas per condition over three frames" — metric and software not specified. **→ Fig. 6, E and F.**
5. Western blot band-intensity quantification, normalized to Ponceau S — no densitometry software named. **→ Fig. 3 B; Fig. 4, A and H; Fig. 5, B, D, and F; Fig. 6 H.**

```{note} Ambiguities and gaps flagged during extraction
:class: dropdown
- FIJI is named as the general image-analysis tool ("Acquired images were analyzed using FIJI") but no macro, plugin, ROI method, or specific measurement is described for any of the confocal datasets.
- Two Data Availability sections exist in the document (one mid-Methods, one at the document end) citing different GEO accession numbers for the sequencing data (GSE308521 vs. GSE303723) — an apparent inconsistency in the source article.
- Ribo-seq data (Table S4) is described in Methods/Results but is not mapped to any figure panel showing image/plot output.
```

```{admonition} Verbatim quote
"Images were acquired via the Zeiss Zen Blue 2.3 software on Zeiss LSM 800 confocal laser scanning microscope... Acquired images were analyzed using FIJI."

"Quantification performed by selecting 10 areas per condition over three frames per biological replicate."
```

- **Software named**: FIJI; Zeiss Zen Blue 2.3; GraphPad Prism; LipidXplorer; cutadapt v5.1; FastQC v0.12.1; MultiQC v1.30; STAR (v2.7.11b / v2.7.10a); featureCounts (Subread v2.1.1); DESeq2 v1.38.0; Bowtie v1.2.3; Magma (custom proteomics tool).
- **Code repository**: A code repository exists but is for the RNA-seq/Ribo-seq bioinformatics pipeline, not bioimage analysis: "Custom Python scripts used to analyze the sequencing data are available at GitHub and Zotero [sic, apparently Zenodo] at `https://github.com/usa0ri/Huang2025` and `https://doi.org/10.5281/zenodo.17144598`." No repository exists for the confocal/FIJI image-analysis steps.
- **Sample image data**: Not stated for image data specifically (category c). Two Data Availability statements both cover only sequencing data (GEO accessions GSE308521 and GSE303723) and the associated analysis code; neither mentions deposition of raw microscopy/confocal image data. Per-figure "Source data" pointers refer to western blot files, not fluorescence micrographs.
- **Based on prior methods**: The PA biosensor construct cites Kim et al. (2015); the IMPACT technique was developed previously by the authors (Bumpus and Baskin, 2017); RT-IMPACT cites Liang et al. (2019). The confocal image acquisition/FIJI analysis, live-cell PA-biosensor quantification, and phalloidin quantification are all presented without a methodological citation for the imaging/quantification approach itself.

(pcm1-centriolar-satellites)=
## Centriolar satellites assemble via a hierarchical pathway driven by PCM1 multimerization

Efe Begar, Ece Seyrek, Selin Yilmaz-Karaoglu, Melis D. Arslanhan, Ezgi Odabasi, and Elif Nur Firat-Karalar — *Journal of Cell Biology*, Vol. 225, No. 8, e202509238 (2026). [doi:10.1083/jcb.202509238](doi:10.1083/jcb.202509238)

1. Granule volume/size quantification — Imaris "Surface Creation" function (intensity thresholding, manual correction). **→ Fig. 1 D.**
2. Threshold/saturation-concentration quantification — 3D voxel reconstruction in Imaris, intensity-per-volume for granule vs. cytoplasmic compartments (per Jiang et al., 2021). **→ Fig. 1, F and G.**
3. Ciliary SMO intensity quantification — ImageJ. **→ Fig. 2 E; Fig. S4 E.**
4. FRAP mobile-fraction/t½ curve fitting (Fiji) — for PCM1-N/PCM1-M and mNG-PCM1-FKBP granules, per equations from Conkar et al. (2019) and Trembecka et al. (2010). **→ Fig. 4 A; Fig. S2 B.**
5. Client-PCM1 colocalization (Pearson Correlation Coefficient) — Imaris Coloc module (Build Coloc Channel), analyzed in GraphPad Prism. **→ Fig. 5, B and C; Fig. 7, C, D, and F.**
6. U-ExM subdomain mapping — Leica Stellaris imaging of expanded gels, "Lightning" deconvolution, expansion factor by manual ruler measurement. **→ Fig. 6, A–C.**
7. Line-profile/plot-profile analysis for client spatial position within granules — ImageJ's Plot Profile function, peak-to-peak distances normalized to PCM1 diameter. **→ Fig. 6, D–F.**
8. In vitro condensate/granule quantification — Aivia software (Leica Microsystems), machine-learning Object Detection module. **→ Fig. 8, C and H.**

```{note} Ambiguities and gaps flagged during extraction
:class: dropdown
- The "Split Touching Objects" function in Imaris (used to separate adjoining granules) is named but not elaborated with parameters or thresholds.
- TIRF microscopy of PCM1-microtubule binding (Fig. 8, E and F) is imaged but no quantification method is given for scoring binding/colocalization.
- The Aivia "machine learning tool" is described only generically, without specifying which built-in classifier or training approach was used.
- A step-by-step Imaris pipeline (cell segmentation rule, spot-creation diameter) is given only in the Fig. S5 A legend, not repeated in the main-text Methods "Image analysis" section.
```

```{admonition} Verbatim quote
"Granule properties, including number, size, and intensity, were quantified from GFP-PCM1 or endogenous PCM1 signals using the Surface Creation function in Imaris software (Bitplane, Oxford Instruments). Surfaces were detected by intensity thresholding, and diameters were estimated using the software's built-in algorithm. Manual corrections were applied as needed to ensure accurate segmentation."
```

- **Software named**: Imaris (Bitplane, Oxford Instruments); Fiji; ImageJ; Aivia (Leica Microsystems); GraphPad Prism 7; Leica Application Suite X (LAS X); LAS X Lightning; Huygens Professional; ZEN Black; LI-COR Odyssey.
- **Code repository**: None found.
- **Sample image data**: Not stated for image data specifically (category c). Data Availability statement: "All data supporting the findings of this study are available in the manuscript, its supplemental material, or from the corresponding author upon reasonable request." — a blanket statement covering all data types, no image-specific accession or repository.
- **Based on prior methods**: The granule-concentration/threshold quantification cites Jiang et al. (2021); the FRAP curve-fitting equations cite Conkar et al. (2019) and Trembecka et al. (2010); U-ExM cites Arslanhan et al. (2023). The Imaris-based granule segmentation, the Aivia-based in vitro granule detection, the ImageJ plot-profile line analysis, and the PCC/Coloc-module colocalization analysis are all described procedurally but without attribution to a specific prior-methods citation.

(aqp12-signaling-motif)=
## A pan-vertebrate signaling motif controls the molecular function of intracellular AQP12

François Chauvigné, Marc Catalán-García, Xavier Daura, Roderick Nigel Finn, and Joan Cerdà — *Journal of Cell Biology*, Vol. 225, No. 8, e202512040 (2026). [doi:10.1083/jcb.202512040](doi:10.1083/jcb.202512040)

1. Immunofluorescence localization of HA-tagged/native AQP12-family channels in oocyte paraffin sections and yolk-platelet membranes — Zeiss Axio Imager Z1/ApoTome. **→ Fig. 1 B; Fig. 2, B and G; Fig. 4, D, G, I, and J; Fig. 5, C, G, and K.**
2. Immunogold TEM of oocyte/yolk-platelet thin sections — qualitative/representative only, no particle-counting or quantification pipeline. **→ Fig. S2 B.**
3. Confocal imaging of zymogen-granule (ZG) activation time course (AMY/GP2 colocalization) — Zeiss LSM 700. **→ Fig. S4 A.**
4. Colocalization quantification (Pearson's correlation coefficient) — ImageJ with the Colocalization Colormap plugin (Jaskolski et al., 2005). **→ Fig. S4, A and B.**
5. Airyscan super-resolution imaging of AQP12/AQP4 trafficking vs. AMY — Zeiss LSM 980-PicoQuant, "Fast Airyscan Sheppard Sum SR-4Y" deconvolution; ZEN 3.5 "Ortho" and "Profile" functions for colocalization visualization/line-scan. **→ Fig. 8, C and D; Fig. 9, B–H and K.**
6. Immunoblot densitometry (Image Studio 5.2, LI-COR), normalized to loading controls. **→ Figs. 1–9 (multiple panels).**

```{note} Ambiguities and gaps flagged during extraction
:class: dropdown
- The Colocalization Colormap/Pearson's coefficient analysis is cited only for the ZG activation time course; threshold settings, ROI definition, or number of images analyzed per timepoint are not given.
- No molecular-graphics/rendering software (e.g., PyMOL, Chimera) is named for the Fig. S5 homology-model "cartoon renders" — SWISS-MODEL/ProMod3 produces only the coordinate model, not the rendering.
- Immunogold TEM (Fig. S2 B) and bright-field H&E histology (Fig. S2 H) both lack any stated image-analysis or quantification method — purely representative/qualitative.
```

```{admonition} Verbatim quote
"To quantify the amount of colocalization between the AMY and GP2 fluorescent stains in both images during the time course, we calculated Pearson's correlation coefficient (or index of correlation) using ImageJ software with the Colocalization Colormap plugin (Jaskolski et al., 2005)."
```

- **Software named**: ImageJ (with Colocalization Colormap plugin); ZEN2 (blue edition); Zen 2010 B SP1; Zen 3.5 lite/ZEN 3.5; Image Studio 5.2 (LI-COR); GraphPad Prism 10; SWISS-MODEL/ProMod3 v3.6.0; MrBayes v3.2.7a; Tracer v1.7.1.
- **Code repository**: None found.
- **Sample image data**: Not stated for image data specifically (category c). Data Availability statement: "Data are available in the article itself and its supplementary materials. The amino acid alignments and phylogenetic trees are available upon request." — only sequence/phylogenetic data are named as on-request; raw microscopy/TEM images are not specifically addressed.
- **Based on prior methods**: Yolk-platelet isolation is a modified method from Bergeron et al. (2011); zymogen-granule isolation follows Chen and Andrews (2008); the Colocalization Colormap plugin cites Jaskolski et al. (2005). The core immunofluorescence, confocal, TEM, and Airyscan imaging protocols are described procedurally without an external methodological citation for the imaging/analysis approach itself.

(vine-rab5-inactivation)=
## The Rab GEF VINE couples phosphatase recruitment to GAP-mediated Rab5 inactivation

Mia S. Frier, Shawn P. Shortill, Michael Davey, and Elizabeth Conibear — *Journal of Cell Biology*, Vol. 225, No. 8, e202601107 (2026). [doi:10.1083/jcb.202601107](doi:10.1083/jcb.202601107)

1. Endosomal puncta/Rab5-fusion localization quantitation — widefield imaging (Leica DMi8), automated quantitation via MetaMorph 7.8.13.0 "journals" (Count Nuclei for live-cell masking, Granularity for puncta detection by size/intensity). **→ Fig. 1, B and F; Fig. 2, B, E, F, H, and J; Fig. 3, E and H; Fig. 4, E and J; Fig. 6 C.**
2. Manual quantitation of blinded fluorescence images — ImageJ's Multi-Point tool, for select complementation panels. **→ Fig. 5 D; Fig. S5 C.**
3. Heatmap generation summarizing pooled puncta-quantitation data — Microsoft Excel 2025, color gradient by average puncta count. **→ Fig. 1 G.**
4. Split-DHFR colony-growth interaction screen — robotic colony arraying, colony area measured with CellProfiler, ratio Z-scores computed in Excel. **→ Fig. 4 B; Table S1.**
5. Structural prediction/modeling (computational, not micrograph-derived) — AlphaFold2/AlphaFold3, conservation mapped with ConSurf, models rendered in PyMOL. **→ Fig. 3, A–C; Fig. 4, F–H; Fig. 5, A and B.**
6. Western blot band/secreted-protein intensity quantitation — ImageJ, chemiluminescence imaged with Vilber Fusion FX. **→ Fig. 1 H; Fig. 6 D; Fig. S3 D.**

```{note} Ambiguities and gaps flagged during extraction
:class: dropdown
- CellProfiler pipeline parameters (modules, thresholding, version) for the colony-area measurement are not described beyond naming the tool.
- The categorical scoring rubric for manual blinded quantitation (Fig. 5 D, Fig. S5 C) is deferred to an in-figure key rather than described in Methods prose.
- PyMOL and ImageJ are both named without version numbers.
```

```{admonition} Verbatim quote
"Automated quantitation was performed on unmodified images using MetaMorph 7.8.13.0 journals (MDS Analytical Technologies). Dead cells were masked, and live cells identified using the Count Nuclei feature, and puncta identified using size and intensity above local background as criteria in the Granularity feature."
```

- **Software named**: MetaMorph 7.8.13.0; ImageJ (Multi-Point tool, blot quantification); Adobe Photoshop CC 2025; Adobe Illustrator CC 2021; Microsoft Excel 2025; GraphPad Prism 10.2.2; ColabFold AlphaFold2; AlphaFold3 server; ConSurf; PyMOL; CellProfiler.
- **Code repository**: None found.
- **Sample image data**: Not stated for image data specifically (category c). Data Availability statement: "All data generated in this study are included in the manuscript and supplemental files." — a single generic sentence with no image-specific mention, accession, or repository.
- **Based on prior methods**: ImageJ-based quantitation cites Schneider et al. (2012); AlphaFold2/ColabFold cites Jumper et al. (2021) and Mirdita et al. (2022); AlphaFold3 cites Abramson et al. (2024); ConSurf cites Ashkenazy et al. (2016); CellProfiler cites Lamprecht et al. (2007); the split-DHFR assay design cites Tarassov et al. (2008). MetaMorph's Count Nuclei/Granularity feature use and the Excel-based heatmap generation are presented without a methodological citation.

(xpg-ner-recruitment)=
## Recruitment and release of XPG during NER is controlled by pre- and post-incision factors and EXO1

Alba Muniesa-Vargas, Cristina Ribeiro-Silva, Carlota Davó-Martínez, Anja Raams, Bart Geverts, Jacinta van de Grint, Maroussia Ganpat, Karen L. Thijssen, Joris Pothof, Adriaan B. Houtsmuller, Arjan F. Theil, Wim Vermeulen, and Hannes Lans — *Journal of Cell Biology*, Vol. 225, No. 8, e202602121 (2026). [doi:10.1083/jcb.202602121](doi:10.1083/jcb.202602121)

1. Protein accumulation at local UV damage (LUD) — average fluorescence intensity at LUD divided by average nuclear intensity, measured in FIJI. **→ Fig. 1, D and E; Fig. 5, A, J, and K.**
2. FRAP (immobile fraction, Fimm) — Leica TCS SP5 nuclear strip bleach. **→ Fig. 1, F and G; Fig. 2, A–E; Fig. 4, C and D.**
3. Real-time UV-C laser accumulation imaging — 266 nm laser coupled to a Leica SP8 confocal, accumulation curves normalized to pre-damage fluorescence. **→ Fig. 2, F–H; Fig. 5, B, C, F, and G.**
4. iFRAP (inverse FRAP) — half-life from one-phase exponential decay fit in GraphPad Prism 9. **→ Fig. 3, A–D; Fig. 4, E and F; Fig. 5, D, E, H, and I.**
5. UV-C colony survival counting — Coomassie-stained colonies counted with the "integrated colony counter GelCount (Oxford Optronix)." **→ Fig. 1 C; Fig. 4 B.**
6. UDS (unscheduled DNA synthesis) assay — EdU/Click-iT staining, fluorescence quantified after background subtraction; the microscope/software used is not restated in this subsection. **→ Fig. 5 L.**

```{note} Ambiguities and gaps flagged during extraction
:class: dropdown
- The UDS assay's imaging/quantification step does not name a microscope or software, unlike the parallel immunofluorescence subsection, which explicitly names the Zeiss LSM700 and FIJI — it is presumed to reuse that pipeline but this is not stated.
- The colony-counting method names only the hardware/software product (GelCount) without describing thresholding or counting criteria.
- Immunoblot bands are visualized on the Odyssey CLx system but not quantified numerically anywhere in the paper (shown only as representative images).
```

```{admonition} Verbatim quote
"Protein accumulation at UV lesions was quantified by dividing the average fluorescence signal intensity at LUD by the average nuclear fluorescence intensity, as measured using FIJI image analysis software."
```

- **Software named**: FIJI; GraphPad Prism version 9 for Windows. No other image-analysis software (no ImageJ, MATLAB, Imaris, or CellProfiler) is named anywhere in the document.
- **Code repository**: None found.
- **Sample image data**: Not stated for image data specifically (category c). Data Availability statement: "The data underlying this article are available in the article and in its online supplementary material. Source data will be shared on reasonable request to the corresponding author." — a blanket statement; the "on request" clause applies to "source data" (uncropped blots) generically, not specifically to raw microscopy images.
- **Based on prior methods**: FRAP cites Ribeiro-Silva et al. (2018); iFRAP cites the authors' own prior paper (Muniesa-Vargas et al., 2024); cell-cycle discrimination by PCNA foci cites Schönenberger et al. (2015). The FIJI-based immunofluorescence intensity-ratio quantification, the colony-counting method, and the UV-C laser real-time accumulation protocol are all presented without a prior-methods citation for the imaging/analysis approach itself.

(procollagen-condensates)=
## Procollagen 1 assembles into phase-separated condensates in the endoplasmic reticulum

Soumya Bhattacharyya, Jose Wojnacki, Nathalie Brouwers, and Vivek Malhotra — *Journal of Cell Biology*, Vol. 225, No. 8, e202603129 (2026). [doi:10.1083/jcb.202603129](doi:10.1083/jcb.202603129)

1. PC1 condensate segmentation, counting, area, and sphericity filtering — Icy v2.5.4.0 (Spot Detector plugin, then Active Contours plugin, run as a single protocol; sphericity ≥85 filter for area histograms). **→ Fig. 1, J and K; Fig. 2 J; Fig. S3 F.**
2. Colocalization quantification (Manders' coefficients) — JACoP plugin in Fiji. **→ Fig. 2 H; Fig. 3 E; Fig. S1 H; Fig. S2 B.**
3. FRAP quantification — recovery profiles in ImageJ, fit in GraphPad Prism to a one-phase-association exponential to derive T½. **→ Fig. 1 O.**
4. ER/Golgi ROI generation and Col1A1 intensity quantitation — manual cell-ROI delineation in Icy; Otsu thresholding on GalNT/Hsp47 channels to define Golgi/ER masks; `bwlabel` (R's EBImage) for labeled ROIs; intensity quantified in R. **→ Fig. 2 B.**
5. PC1 condensate-Sec31 "coupling index" and inter-structure distances — calculated by the SODA plugin (formula given in Methods). **→ Fig. 4, F and G.**
6. Fluorescence line-scan intensity profiles — general Fiji processing stated, but the specific tool/plugin for the line-profile extraction itself is not separately named. **→ Fig. 2 A; Fig. 3 D; Fig. 4 B; Fig. S3 C.**

```{note} Ambiguities and gaps flagged during extraction
:class: dropdown
- The software used to generate the kymograph in Fig. S2 A is not stated (presumably Fiji, per the general processing statement, but not confirmed).
- The coefficient-of-variation analysis in Fig. S1 J has no specified software or method beyond the general Fiji/Icy/R pipeline.
- The SODA plugin's formula is given in full, but no citation/reference for the SODA method or plugin itself is provided anywhere in the References list.
- Western/dot blot quantification names only the imaging instrument (iBright), not a densitometry tool.
```

```{admonition} Verbatim quote
"For characterizing PC1 condensates, PC1 structures were segmented using the Spot Detector (Olivo-Marin, 2002) and Active Contours (Ulman et al., 2017) plugins implemented in Icy, version 2.5.4.0 (de Chaumont et al., 2012)... Both plugins were executed within a single Icy protocol to automate and standardize the analysis workflow."
```

- **Software named**: Fiji 1.54p; ImageJ; JACoP plugin; Icy v2.5.4.0; Spot Detector and Active Contours plugins; SODA plugin; GraphPad Prism; R (ggplot2, dplyr, tidyverse, sf, terra, EBImage, stringr, svglite); IUPred2A; AlphaFold3; BioRender; iBright imaging system.
- **Code repository**: None found.
- **Sample image data**: Not stated for image data specifically (category c). Data Availability statement: "The data underlying all figures are available in the published article and its online supplemental material." — generic, present, but no accession/repository or image-specific mention.
- **Based on prior methods**: Fiji cites Schindelin et al. (2012); JACoP/Manders' cites Bolte and Cordelières (2006); Icy cites de Chaumont et al. (2012); Spot Detector cites Olivo-Marin (2002); Active Contours cites Ulman et al. (2017). The SODA-based coupling-index calculation, the Otsu-thresholding ER/Golgi masking, the FRAP curve-fitting, and the line-scan/kymograph steps are all presented without a citation for the specific method.

```{warning} Caveats

**Code availability.** None of the seventeen articles in this issue provides a public code repository for its own bioimage-analysis pipeline. The one repository link found anywhere in the issue ("Phosphatidylserine and RhoB connect PI4P and PA metabolism...") is for RNA-seq/Ribo-seq bioinformatics scripts (GitHub + Zenodo), not for image analysis. Several papers describe substantial custom code in detail — a custom MATLAB flattening script ("Fibroblast depletion..."), a custom Fiji/Python photoconversion kymograph macro ("Asymmetric mitochondrial trafficking..."), a "Magma" TurboID-proteomics tool ("Phosphatidylserine and RhoB...") — none of which is deposited or offered on request.

**Version-number gaps.** Most named software across this issue (Fiji/ImageJ, Imaris, CellProfiler, Icy, MetaMorph in several papers, ZEN, NIS-Elements) is cited without a version number. Where a version is given at all, it is often only for the statistics package (GraphPad Prism) rather than the imaging tool itself. A handful of papers are more complete: "E-/N-cadherin drive hepatic polarity...", "Redox-dependent S-glutathionylation...", and "Procollagen 1 assembles into phase-separated condensates..." all give explicit Fiji build numbers (e.g., 2.16.0/1.54g), and "The Rab GEF VINE..." and "Role of the nonhelical tailpiece of myosin-II..." give explicit MetaMorph/ImageJ versions.

**"Based on prior methods" scope.** As in earlier issues, this report credits a step to prior methods only when the paper cites a reference specifically for that quantification/analysis procedure — not for general reagents, cell lines, or unrelated assays cited elsewhere. Judged this way, the large majority of the true image-analysis and quantification steps across this issue (intensity-ratio calculations, colocalization pipelines, puncta/foci/granule counting, scoring criteria for cell/organelle classification) are presented as uncited, in-house methodology, even where the paper cites prior work for its underlying biological assay, cell line, or reagent.

**Figure-mapping and measurement-attribution ambiguities.** Several papers name a technique in Results, a figure legend, or a Methods subsection without ever tying it to a specific quantification method or a single figure panel — for example the kymograph generation in "Opposing actomyosin pools..." and "Procollagen 1 assembles into phase-separated condensates...", the Cas9-activity reporter assay's imaging modality (flow cytometry vs. microscopy) in "Mitochondria limit coenzyme Q export...", the sarcomere-shortening measurement software in "Sequential changes in calcium transients...", and the UDS assay's unstated microscope in "Recruitment and release of XPG...". These are flagged inline rather than guessed at, per the extraction rule.

**Supplementary-methods-deferral check.** No article in this issue defers image-analysis *methodological detail* to a separate supplementary-methods document that this PDF doesn't include. Genuine deferrals that were found were all of substantive *data* (validation datasets, parameter-fitting curves, full software/plugin inventories) to a supplementary figure or table — for example Table S9's complete software list in "Opposing actomyosin pools...", the parameter-validation plots in Fig. S2 of "Asymmetric mitochondrial trafficking...", and the step-by-step Imaris pipeline given only in a supplementary figure legend in "Centriolar satellites assemble via a hierarchical pathway...". These are normal practice, not methods gaps of the kind step 3 of the skill is designed to catch.

**Sample image data availability.** Across the seventeen articles in this issue: **1** publicly deposits raw/original image data with a resolvable accession or DOI (category a) — "Fibroblast depletion reveals mammalian epithelial resilience..." (Zenodo, "original figure files and corresponding raw data"); **2** state that image data are available specifically on request (category b) — "Asymmetric mitochondrial trafficking..." ("large imaging data... upon reasonable request") and "PARP1 hyperactivity stalls translation..." ("raw microscopy images are available from the corresponding author upon request"); **14** give only generic "data" language with no image-specific mention (category c), including two papers whose only public accessions cover non-image data specifically (mass-spectrometry proteomics in "Receptor-mediated Golgi retention of Fam20 kinases..."; RNA-seq/Ribo-seq in "Phosphatidylserine and RhoB connect PI4P and PA metabolism..."); and **0** papers in this issue have no Data Availability statement at all — every article states at least a generic data-availability position, unlike JCB 225/9's single instance of a fully absent statement. No article in this issue deposits raw image data in a public, image-specific repository (e.g., BioImage Archive, IDR, EMPIAR) — the one public deposit found (Zenodo, in "Fibroblast depletion...") is a general-purpose repository rather than an imaging-specific one.
```
