---
title: "Journal of Cell Science, Volume 139, Issue 16 (8 articles)"
subtitle: "Bioimage analysis methods survey"
subject: Methods survey
date: 2026-09-24
---

# JCS Vol. 139, Issue 16 — Bioimage Analysis Methods

```{note}
Built by reading the actual article PDFs (`pdftotext` + exact-string search), not the publisher's web pages — several of these articles are paywalled or bot-gated on `journals.biologists.com`, so a web fetch alone would have missed or mangled the Materials and Methods text. All quotes below are verbatim from the PDFs. Figure/panel numbers were confirmed by cross-reading each Methods description against the matching Results narrative and figure legend text in the same PDF — where the legend and body text disagree on a panel letter, the figure legend is treated as authoritative. Each article's Data and resource availability statement was also checked for whether it makes raw/original sample image data itself available, as distinct from code availability — see the "Sample image data" table column, the per-article bullet of that name, and the Caveats section for the outcome.
```

All 8 research articles in this issue use some form of image analysis, and — confirming the premise of this exercise — every image-analysis step below does indeed terminate in a specific figure panel: a micrograph, a quantification plot/box-plot, or a table. Software names are reproduced exactly as printed in each paper (including inconsistent capitalization, e.g. `ImageJ-win64`).

## At a glance

| Article | DOI | Key imaging software | Version given? | Measurement target | Code repo | Sample image data |
|---|---|---|---|---|---|---|
| [Beadex modulates haematopoiesis...](#beadex) | [doi:10.1242/jcs.264524](doi:10.1242/jcs.264524) | `ImageJ-win64`, `Imaris Viewer` | Imaris: 10.2.0 | 1) Cell area; 2) Phagocytic index; 3) Lamellipodium area; 4) F-actin/phalloidin intensity; 5) Western blot band intensity (Profilin) | None | Not stated for images (RNA-sequencing data are publicly deposited in NCBI SRA, but imaging data fall under the generic "found within the article and its supplementary information" clause) |
| [Chromokinesin KLP-19...](#klp-19) | [doi:10.1242/jcs.264066](doi:10.1242/jcs.264066) | ImageJ, Fiji, MATLAB, IMOD, Amira, Python, Utrack | MATLAB: 2012 release | 1) EB-2/EBP-2 comet dynamics; 2) FRAP recovery; 3) Electron-tomography MT segmentation & inter-MT distance; 4) Spindle length & segregation-rate tracking; 5) Single-molecule motor velocity/run length; 6) SHG-based MT polarity/intensity | 3 GitHub repos | On request only — explicit: "the light and electron microscopy data can be provided by S.R. pending scientific review and a completed material transfer agreement" |
| [NIFK Ser247 phosphorylation](#nifk) | [doi:10.1242/jcs.264641](doi:10.1242/jcs.264641) | Fiji/ImageJ | No | 1) Mitotic index (pH3+ cell counting); 2) Lagging-chromosome/bridge scoring | None | Not stated for images (generic "data...found within the article and its supplementary information") |
| [Avl9 DENN domain protein](#avl9) | [doi:10.1242/jcs.264716](doi:10.1242/jcs.264716) | ImageJ/Fiji, Adobe Photoshop | Fiji: 2.16/1.54p | 1) Plasma-membrane fraction (GFP-Snc1 surface/total ratio); 2) CPY mis-sorting (secreted CPY integrated density) | None | Not stated for images (generic "data...found within the article and its supplementary information") |
| [Golgi-bypass secretion (proTGFα)](#golgi-bypass) | [doi:10.1242/jcs.264719](doi:10.1242/jcs.264719) | Fiji | No | 1) Organelle-marker colocalization (proTGFα/GRASP65 with ER/ERGIC/ERES markers); 2) Western blot band intensity | None | Not stated for images (generic "data...found within the article and its supplementary information") |
| [TRAPPC11/12/13–Tca17 subcomplex](#trappc11) | [doi:10.1242/jcs.264822](doi:10.1242/jcs.264822) | Metamorph Premier, Huygens Professional | No | 1) Colocalization of TRAPP subunits with PAS marker Atg8; 2) Western blot densitometry (TRAPPC11-HA3 turnover) | None | Not stated for images (generic "data...found within the article and its supplementary information"; no proteomics accession is given despite mass-spec methods) |
| [SNED1 fibrillar assembly](#sned1-fibrillar) | [doi:10.1242/jcs.264884](doi:10.1242/jcs.264884) | Fiji ImageJ, Zeiss ZEN | No | 1) ECM layer thickness; 2) 3D reconstruction/volume rendering; 3) Colocalization (Manders' coefficient); 4) Area-fraction density | None | Not stated for images ("research materials are available upon request," not images specifically; otherwise generic boilerplate) |
| [SNED1 LDV motif](#sned1-ldv) | [doi:10.1242/jcs.264885](doi:10.1242/jcs.264885) | Fiji ImageJ, OrientationJ, Zeiss ZEN | No | 1) ECM thickness; 2) Colocalization (MOC); 3) Fiber alignment; 4) Area-fraction density; 5) Cell adhesion/spreading morphometry | None | Not stated for images ("research materials are available upon request," not images specifically; otherwise generic boilerplate) |

---

(beadex)=
## Beadex modulates haematopoiesis and innate immune defence against microbial infection in *Drosophila melanogaster*

Jain, Salian, Shah, Nongthomba — *J. Cell Sci.* 139, jcs264524 (2026). [doi:10.1242/jcs.264524](doi:10.1242/jcs.264524)

**Workflow** — section literally titled *"Image analysis and quantification"*:

1. Confocal acquisition: phagocytosis assay on a **Leica SP8**; lymph gland immunostaining on a **Leica Falcon** confocal.
2. *Cell area*: maximum-intensity z-stack projection → cell boundary traced with the freehand selection tool → area measured in `ImageJ`. **→ Fig. 2E** (lymph gland primary lobe area, w1118 vs Bx7 mutant) and **Fig. S2A** (haemocyte cell-area control check, confirming no confound in the lamellipodium measurements below).
3. *Phagocytic index*: ingested bacteria counted **manually** while viewing the cell in 3D rendering in `Imaris Viewer`. **→ Fig. 5C** (Bx7 mutant vs control) and **Fig. 5I** (He-GAL4>UAS-BxRNAi knockdown vs both genetic controls); profilin-rescue variants of the same measurement appear in **Fig. S3A–C,F,H**.
4. *Lamellipodium area*: maximum-intensity z-stack projection → lamellipodium region traced with the freehand tool (phalloidin-defined outer boundary) → non-lamellipodium area subtracted to get net lamellipodium area, in `ImageJ`. **→ Fig. 5J** (knockdown vs genetic controls).
5. *F-actin intensity*: mean grey value of phalloidin signal measured in 3–4 equal-size rectangular ROIs within the lamellipodium (`ImageJ`), background-corrected against an equivalent region outside the cell. **→ Fig. 5E**.
6. *Western blot quantification*: band mean grey value measured in `ImageJ`, normalized to total protein (Ponceau S staining). **→ Fig. 6D** (Profilin protein level quantification; raw blot shown in **Fig. 6C**).

```{admonition} Verbatim quote
:class: tip
"Analysis was performed using **ImageJ-win64** and **Imaris Viewer (10.2.0)**. Cell area was calculated by creating a z-stack projection (maximum intensity), selecting the cell boundaries with the freehand selection tool, and measuring the area in ImageJ. The phagocytosis index was calculated by manually counting the ingested bacteria and viewing the cell in 3D in Imaris."
```

```{note}
:class: dropdown
Two panels in Fig. 5 are quantified but **not** tied to ImageJ/Imaris in the text: **Fig. 5B** (percentage of engulfing cells) and **Fig. 5D** (filopodia number per cell) are described only as "quantifications" without a named tool for the counting step itself — likely manual scoring from the same confocal z-stacks used for the ImageJ measurements above.
```

- **Software named**: `ImageJ-win64`, `Imaris Viewer` (v10.2.0), `GraphPad Prism 10.0` (statistics).
- **Code repository**: none provided.
- **Sample image data**: Not stated for images specifically. The RNA-sequencing data are publicly deposited in the NCBI Sequence Read Archive (BioProject PRJNA1338986), but imaging data fall under the paper's generic "found within the article and its supplementary information" clause, with no repository named for micrographs.
- **Based on prior methods**: the plasmatocyte-counting protocol (not the image-analysis steps themselves) follows Bosch et al., 2019 and the haemocyte-extraction procedure follows Petraki et al., 2015. No prior paper is cited specifically for the ImageJ/Imaris quantification approach — it reads as this lab's own procedure.

---

(klp-19)=
## Chromokinesin KLP-19 regulates microtubule overlap and dynamics during anaphase in *C. elegans*

Zimyanin, Magaj, Manzi, Yu, Gibney, Chen, Basaran, Horton, Siller, Pani, Needleman, Dickinson, Redemann — *J. Cell Sci.* 139, jcs264066 (2026). [doi:10.1242/jcs.264066](doi:10.1242/jcs.264066)

The most methodologically diverse paper in the issue — five distinct imaging/analysis pipelines, each traceable to its own figure:

1. **EB-2::GFP comet imaging**: spinning-disc confocal, images processed in `ImageJ`; acquisition controlled with **Slidebook 6.0** (3i). **→ Fig. 5D** (bar plot, normalized EBP-2::GFP intensity) and **Fig. 5E** (EBP-2 comet quantification at the midzone boundary line).
2. **FRAP**: Yokogawa CSU-W1 SoRa spinning disk with **Nikon NIS-Elements** for acquisition; FRAP curves calculated by combining `FIJI` (StackReg plugin, for drift correction) and `MATLAB` (Statistics Toolbox, 2012 release). **→ Fig. 5B**. (β-tubulin::GFP midzone intensity measurement that motivates the FRAP experiment is **Fig. 5A**.)
3. **Electron tomography**: tomograms computed in `IMOD`; microtubule segmentation, tracing, and 3D interaction/distance analysis performed in `Amira` via an extension to its filament editor (the "SpindleAnalysis Toolbox"). **→ Fig. 6A,B** (3D tomographic reconstructions, color-coded by inter-MT distance), **Fig. 6C** (MT interaction-distance distribution plot) and **Fig. 6D** (bar plot of average MT parameters — number/length/interactions); **Fig. 6E,F** are schematic diagrams built from the same tomography data, not direct image-analysis outputs.
4. **Mitotracker time-lapse**: custom `Python` pipeline (`nd2reader`, `OpenCV`, `SciPy`) for channel splitting, embryo-outline masking (median projection + watershed segmentation), gaussian blur and adaptive thresholding; kymographs built via image rotation and intensity projection. **→ Fig. 3A–E** (metaphase spindle length, pole-to-pole and chromosome-segregation rates), with corresponding double-depletion data in **Fig. S4, S5**.
5. **Single-molecule / TIRF assays**: kymographs and particle tracking in `FIJI`; single-particle tracking via **Utrack**; sc-SiMPull data quantified with a dedicated **SiMPull Analysis MATLAB package**. **→ Fig. 4B(ii–iv)** (KLP-19 motility on immobilized MTs), **Fig. 4C** (velocity violin plot), **Fig. 4D** (run-length violin plot), **Fig. 4E,F** (SPD-1 particle behavior), with photobleaching/oligomerization/stoichiometry data in **Fig. S9C, S10A,B,D–G**.
6. **SHG / two-photon imaging**: analyzed with `MATLAB` and `ImageJ`. **→ Fig. 1** (representative SHG image of the anaphase spindle) and **Fig. 2A,B** (MT polarity/SPD-1::GFP intensity along the spindle axis, from SHG data); the derived FWHM and linescan quantifications from the same image set appear in **Fig. 2E–G**.

- **Code repositories**:
  - Own tracking code: <https://github.com/uvarc/mitosisanalyzer>
  - SiMPull analysis package (adapted, not original to this paper): <https://github.com/dickinson-lab/SiMPull-Analysis-Software>
  - Dependency: <https://github.com/Open-Science-Tools/nd2reader>
- **Sample image data**: On request only — the one article in this issue whose Data and resource availability statement explicitly names imaging data: "The light and electron microscopy data can be provided by S.R. pending scientific review and a completed material transfer agreement. Requests for the data should be submitted to the corresponding authors." This is not a public deposit and carries extra conditions (review, MTA) beyond a plain request.
- **Based on prior methods**:
  - Amira segmentation/filament tracing — Redemann et al., 2014; Weber et al., 2012.
  - SiMPull MATLAB package — Dickinson et al., 2017; Sarıkaya & Dickinson, 2021.
  - Utrack particle tracking — Roudot et al., 2023.
  - EB-2 comet counting approach — Srayko et al., 2005.
  - Microfluidic device fabrication — Chang & Dickinson, 2022; Dickinson et al., 2017; Jaqaman et al., 2008.
  - Fiji itself — Schindelin et al., 2012.

---

(nifk)=
## Stress- and mitosis-dependent phosphorylation of NIFK on Ser247

Schleich, Teleman — *J. Cell Sci.* 139, jcs264641 (2026). [doi:10.1242/jcs.264641](doi:10.1242/jcs.264641)

The lightest imaging component in the issue:

1. Phospho-histone-H3-stained cells imaged (≥10 images per condition).
2. Mitotic index: cell counting performed in `Fiji/ImageJ`, ratio of pH3-positive cells calculated. **→ Fig. 3B** (percentage pH3-positive cells per field of view across the mitotic time course).
3. Lagging-chromosome/chromosomal-bridge scoring: confocal imaging (Leica SP6/SP8, 63× objective) scored **manually by eye** — no software named for this step. **→ Fig. S4E** (percentage of anaphase/telophase cells with lagging chromosomes or bridges, NIFK[S247A] vs control).

- **Software named**: `Fiji/ImageJ` (cell counting only, Fig. 3B).
- **Code repository**: none.
- **Sample image data**: Not stated for images specifically. The Data and resource availability statement reads only: "All relevant data and details of resources can be found within the article and its supplementary information" — generic, with no repository accession and no explicit mention of raw images.
- **Based on prior methods**: none cited for the imaging/scoring steps themselves.

---

(avl9)=
## The yeast DENN domain protein Avl9 contributes to recycling and sorting of endosomal cargos

Rioux, Manj, Prosser — *J. Cell Sci.* 139, jcs264716 (2026). [doi:10.1242/jcs.264716](doi:10.1242/jcs.264716)

1. Widefield fluorescence microscopy (Leica DMi8, Hamamatsu Flash 4.0 v3 camera, **LAS X v3.7.6.25997** acquisition software).
2. Images imported into `ImageJ/Fiji 2.16/1.54p` (exact version given), 16-bit → 8-bit TIFF conversion, cropped in `Adobe Photoshop`.
3. PM-fraction quantification: freehand ROI around the outer and inner perimeter of the plasma membrane → total vs. cytosolic integrated density in `ImageJ`. **→ Fig. 5B** (GFP-Snc1 surface-to-total ratio, WT vs avl9Δ), **Fig. 5D** (GFP-Snc1EN− surface-to-total ratio), **Fig. 6B** (rcy1Δ/avl9Δ epistasis), **Fig. 6D** (snx4Δ/avl9Δ epistasis) and **Fig. 6F** (vps35Δ/avl9Δ epistasis) — all "SuperPlot" presentations of the same ImageJ surface-fraction measurement applied to different genetic backgrounds.
4. CPY mis-sorting assay: chemiluminescence images imported into `ImageJ`, background-subtracted, circular ROI integrated density per spot. **→ Fig. 4B** (quantification of secreted CPY integrated density).
5. Statistics in `GraphPad Prism 9`.

- **Software named**: `ImageJ`, `Fiji` (v2.16/1.54p), `Adobe Photoshop`, `GraphPad Prism 9`.
- **Code repository**: none.
- **Sample image data**: Not stated for images specifically. The Data and resource availability statement reads only: "All relevant data and details of resources can be found within the article and its supplementary information" — generic, with no repository accession and no explicit mention of raw images.
- **Based on prior methods**: colocalization-metric rationale cites Adler & Parmryd, 2010 (though this particular paper doesn't run colocalization itself — that citation appears in the reference list); the monensin endpoint growth assay is adapted from Hung et al., 2018.

---

(golgi-bypass)=
## A Golgi-bypass secretion mechanism for proTGFα involving TMED9 and GRASP65

Steigleder, Döring, Tauber, Nüchel, Lemberg — *J. Cell Sci.* 139, jcs264719 (2026). [doi:10.1242/jcs.264719](doi:10.1242/jcs.264719)

1. Confocal imaging on a **Leica SP5**.
2. "Image processing and co-localization analysis were performed using `Fiji`." **→ Fig. S3A** (proTGFα/GRASP65/calnexin co-localization), **Fig. S3B,C** (proTGFα/GRASP65 co-localization with ERGIC53 and Sec16 markers). The paper's main-figure micrographs (e.g. Fig. 2D,E schematic/localization panels) are qualitative and not run through a Fiji colocalization measurement — only the supplementary marker-overlap panels are.
3. Western blot signal intensities also quantified in `Fiji`. **→ used throughout the immunoblot quantification panels in Figs 1, 3, 4 and 5** (e.g. Fig. 1 TMED9 overexpression blots, Fig. 3E co-immunoprecipitation, Fig. 4B TMED9–GRASP65 association, Fig. 5A ATG5/ATG7 knockout blots) — the Methods text names Fiji once for all blot densitometry and does not tie individual blot panels to it by number.
4. General statistics in `GraphPad` (v10.2.0); blot densitometry bookkeeping in `Microsoft Excel`.

- **Software named**: `Fiji`, `GraphPad` (v10.2.0), `Microsoft Excel`.
- **Code repository**: none.
- **Sample image data**: Not stated for images specifically. The Data and resource availability statement reads only: "All relevant data and details of resources can be found within the article and its supplementary information" — generic, with no repository accession and no explicit mention of raw images.
- **Based on prior methods**: Fiji — Schindelin et al., 2012 (cited twice, once for imaging and once for the western-blot quantification).

---

(trappc11)=
## A subcomplex comprising TRAPPC11, TRAPPC12, TRAPPC13 and the fungal TRAPPC2L homolog, Tca17, directs TRAPPIII to autophagy

Pinar, de los Ríos, Rodríguez-Pires, Espeso, Peñalva — *J. Cell Sci.* 139, jcs264822 (2026). [doi:10.1242/jcs.264822](doi:10.1242/jcs.264822)

1. Fluorescence microscopy on a Leica DMI6000B (63×/1.4 NA objective, Hamamatsu ORCA-ER CCD, objective heater), hardware driven by **Metamorph Premier**.
2. Z-stacks (0.5 µm z-step) streamed to minimize acquisition lag between planes, then deconvolved in **Huygens Professional**.
3. Maximum-intensity projections of red/green channels merged using Metamorph's "color align" plugin; figures annotated in **Corel Draw**. **→ Fig. 2D** (TRAPPC11/Trs85 colocalization at PASs, % colocalized punctae in wild-type vs trs33Δ), **Fig. 2E–H** (TRAPPC11 recruitment across tca17Δ, trappc12Δ and other mutant backgrounds), **Fig. 3A** (Trs85 colocalization at PASs) and **Fig. 3B–D** (quantification of colocalized punctae across genotypes). The paper explicitly states: *"For the colocalization data in Figs 2D and 3A, we ensured results were reproducible across experiments."*
4. Colocalization reproducibility cross-checked across 8 independently generated gene-replaced clones.
5. Western blot chemiluminescence quantified in **Image Lab 5.2.1** (Bio-Rad), plotted with **SigmaPlot**. **→ Fig. S5** (TRAPPC11–HA3 signal over a nitrogen-starvation time course).

- **Software named**: `Metamorph Premier`, `Huygens Professional`, `Corel Draw`, `Image Lab 5.2.1`, `SigmaPlot`.
- **Code repository**: none.
- **Sample image data**: Not stated for images specifically. The Data and resource availability statement reads only: "All relevant data and details of resources can be found within the article and its supplementary information" — generic, with no repository accession and no explicit mention of raw images or the mass-spectrometry data described in Methods.
- **Based on prior methods**: no specific citation is attached to the imaging/deconvolution/colocalization procedure itself — described as this lab's standard pipeline.

---

(sned1-fibrillar)=
## SNED1 fibrillar assembly in the extracellular matrix requires fibronectin and collagen I

Leverton, Pally, Jones, Therol, Ricard-Blum, Naba — *J. Cell Sci.* 139, jcs264884 (2026). [doi:10.1242/jcs.264884](doi:10.1242/jcs.264884)

Section titled *"Image analysis"*, imaged on a **Zeiss Confocal LSM 880**:

1. **ECM thickness analysis**: first/last in-focus z-slices identified, thickness = (slice count) × (slice thickness, 0.33–0.35 µm). **→ Fig. 1F** (SNED1 layer thickness across timepoints).
2. **3D reconstruction**: z-stack volume visualized in `Fiji ImageJ`'s **Volume Viewer** plugin (z-aspect 10.0, Max Projection mode, tricubic smooth interpolation). **→ produces the xy/xz orthogonal-projection micrographs used throughout Fig. 1D and Fig. 2A,C** (the Methods text does not tie Volume Viewer to one specific panel by number, but the orthogonal-projection image type it describes is exactly what appears in these panels).
3. **Colocalization analysis**: `Zeiss ZEN`, computing the Manders' overlap coefficient (MOC) between channels, thresholds set from negative controls, values tracked in `Microsoft Excel`. **→ Fig. 2B** (MOC between SNED1 and fibronectin, by z-slice/timepoint).
4. **Area-fraction density**: `Fiji ImageJ`, manual brightness/contrast, Analyze → Set Measurements. **→ Fig. 1D** (SNED1 signal area fraction over time), **Fig. 2E,F** (fibronectin/collagen-I signal area fraction, fibronectin-knockdown experiment appears as **Fig. 3B,D**) and **Fig. 4C** (collagen-I/SNED1/fibronectin area fraction, ±ascorbic acid).
5. Statistics/plots in `GraphPad Prism`.

- **Software named**: `Fiji ImageJ` (+ Volume Viewer plugin), `Zeiss ZEN`, `Microsoft Excel`, `GraphPad Prism`.
- **Code repository**: none.
- **Sample image data**: Not stated for images specifically. The Data and resource availability statement reads: "All relevant data and details of resources can be found within the article and its supplementary information. Research materials are available upon request from the corresponding author" — "research materials" reads as reagents/constructs rather than raw images, and no repository or explicit image-data commitment is given.
- **Based on prior methods**:
  - Decellularized cell-derived ECM protocol — Harris et al., 2018.
  - Manders' overlap coefficient — Dunn et al., 2011.
  - Fibronectin-matrix quantification convention — Pankov & Yamada, 2004.

---

(sned1-ldv)=
## SNED1 modulates ECM architecture and cell proliferation via its LDV integrin-binding motif

Pally, Leverton, Jones, Naba — *J. Cell Sci.* 139, jcs264885 (2026). [doi:10.1242/jcs.264885](doi:10.1242/jcs.264885)

Companion paper to the one above, same lab, same core pipeline (Zeiss Axio Imager Z2 epifluorescence or Zeiss Confocal LSM 800/880), section also titled *"Image analysis"*, plus one addition:

1. **ECM thickness**, **colocalization** (`Zeiss ZEN`, MOC) and **area-fraction density** (`Fiji ImageJ`) — same procedures as in the fibrillar-assembly companion paper above. **→ Fig. 2C,D** (Manders' overlap coefficient, SNED1WT/RGE/LAV variants), **Fig. 2E** (overall ECM thickness) and **Fig. 2F** (SNED1-specific thickness); **Fig. 2I** and the parallel fibronectin panel (**Fig. 2J**) carry the area-fraction density measurements.
2. **Fiber-alignment analysis** (new in this paper): the **OrientationJ** Fiji plugin quantifies F-actin and ECM-fiber alignment on 8-bit maximum-intensity projections. **→ Fig. 2G** (SNED1 fiber alignment histogram), **Fig. 2H** (fibronectin fiber alignment histogram), **Fig. 3E,F** (F-actin alignment in cells seeded on the two ECM types) and **Fig. 3H** (quantification of cell-alignment in the cross-seeding experiment).
3. Cell counting for adhesion/spreading assays: `ImageJ`. **→ Fig. 3A** (adhesion), **Fig. 3B** (spreading) and **Fig. 3C,D** (quantification of cell area and aspect ratio from those images).

- **Software named**: `Fiji ImageJ` (+ Volume Viewer, `OrientationJ` plugins), `Zeiss ZEN`, `Microsoft Excel`, `GraphPad Prism`.
- **Code repository**: none.
- **Sample image data**: Not stated for images specifically. The Data and resource availability statement reads: "All relevant data and details of resources can be found within the article and its supplementary information. Research materials are available upon request to the corresponding author" — the same "research materials" wording as the companion paper above, not an explicit image-data commitment, and no repository is named.
- **Based on prior methods**:
  - OrientationJ fiber/fluorescence alignment method — Püspöki et al., 2016; Rezakhaniha et al., 2012.
  - Cross-references its own companion paper for the Manders'-coefficient line-graph approach — Leverton et al., 2026 (i.e. the fibrillar-assembly paper above); Fig. 2C,D,E,F in this paper explicitly note that the SNED1WT condition reproduces data from that companion manuscript.

---

## Caveats

```{warning}
- Checked for explicit pointers to a **supplementary Materials and Methods** document (e.g. "as described in the supplementary information", "detailed in supplementary methods"): none of the 8 articles in this issue defer any *image-analysis* step to a separate supplementary methods document. Every "supplementary information" mention found is the standard JCS data-availability boilerplate ("data...can be found within the article and its supplementary information") or a pointer to a specific supplementary figure/movie (Fig. S…, Movie S…), not to additional methodological text. If a future issue's papers do defer method detail this way, that will be flagged inline in the relevant workflow step rather than silently missed.
- No article in this issue links a code repository for its *image-analysis* scripts specifically (KLP-19's GitHub links are for particle-tracking/SiMPull code, which is analysis-adjacent but not "image analysis" in the segmentation/quantification sense for every figure).
- Several software mentions have no version number (Fiji/ImageJ in 5 of 8 papers, Zeiss ZEN, Metamorph, Huygens, Imaris core app aside from the Viewer build).
- "Based on prior methods" here means a citation was attached to that *specific* analysis step in the text — not just general lab-protocol citations elsewhere in the paper.
- Figure numbers were assigned by matching each Methods description to the Results narrative and figure legend wording in the same PDF. Where a paper's Methods text names a technique (e.g. Golgi-bypass's Fiji colocalization, SNED1-fibrillar's Volume Viewer) without citing a specific panel, that is noted explicitly rather than guessed — those cases are flagged inline above instead of given a single confident figure number.
- A few panels (Beadex Fig. 5B,D) are described as "quantifications" without a named software tool for the counting step itself, even though neighboring panels in the same figure explicitly cite ImageJ/Imaris — these are flagged rather than assumed to use the same tool.
- **Sample image data availability**: each article's Data and resource availability statement was checked for whether it makes raw/original *image* data available, as distinct from code availability. Of the 8 articles, 1 (Chromokinesin KLP-19, jcs264066) explicitly commits to sharing light and electron microscopy data — but only on request, pending scientific review and a completed material transfer agreement, not as a public deposit. The remaining 7 articles give only generic language ("found within the article and its supplementary information," sometimes alongside a public deposit of non-image data such as RNA-seq reads, or a "research materials available upon request" clause that reads as reagents/constructs rather than images) with no explicit statement about raw or original micrographs. No article in this issue publicly deposits raw/original images, and none was found to have no Data and resource availability statement at all.
```
