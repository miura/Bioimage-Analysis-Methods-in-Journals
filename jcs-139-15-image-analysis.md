---
title: "Journal of Cell Science, Volume 139, Issue 15 (5 articles)"
subtitle: "Bioimage analysis methods survey"
subject: Methods survey
date: 2026-09-24
---

# JCS Vol. 139, Issue 15 — Bioimage Analysis Methods

```{note}
Built by reading the actual article PDFs (`pdftotext -layout` + exact-string search), not the publisher's web pages — this mirrors the approach used for the Issue 16 report, since journals.biologists.com bot-gates and truncates web fetches before reaching the Materials and Methods text. All quotes below are verbatim from the PDFs. Figure/panel numbers were confirmed by cross-reading each Methods description against the matching Results narrative and figure legend text in the same PDF — where the legend and body text disagree on a panel letter, the figure legend is treated as authoritative. Each article's Data and resource availability statement was also checked for whether it makes raw/original sample image data itself available, as distinct from code availability — see the "Sample image data" table column, the per-article bullet of that name, and the Caveats section for the outcome.
```

All 5 research articles in this issue use image analysis in some form, ranging from a single ImageJ densitometry step to a five-tool computer-vision pipeline (segmentation, tracking, PIV, and a machine-learning classifier) built around a live-cell ERK biosensor.

## At a glance

| Article | DOI | Key imaging software | Version given? | Measurement target | Code repo | Sample image data |
|---|---|---|---|---|---|---|
| [Endothelial biomechanics & Cx43](#endo-cx43) | [doi:10.1242/jcs.264023](doi:10.1242/jcs.264023) | Custom MATLAB (PIV/TFM/MSM), ImageJ | No | 1) Tractions & intercellular stress (TFM/MSM); 2) Cell area and orientation; 3) Mean dye transfer length (GJIC assay) | None | Not stated for images (generic "data...found within the article and its supplementary information"; only the cell-area/orientation code is offered "upon request") |
| [LATS2–PHF6 nuclear speckles](#lats2-phf6) | [doi:10.1242/jcs.264138](doi:10.1242/jcs.264138) | FV10-ASW, ImageJ | No | 1) Colocalization scoring (line-scan + % colocalized foci); 2) Western blot band intensity (PHF6-pS183) | None | Not stated for images (mass-spec proteomics data are deposited to ProteomeXchange, but imaging data fall under the generic "found within the article and its supplementary information" clause) |
| [mGluR/AMPAR trafficking by dopamine](#mglur-dopamine) | [doi:10.1242/jcs.264725](doi:10.1242/jcs.264725) | ImageJ | No | 1) Receptor internalization index; 2) Surface receptor fraction/recycling index; 3) Synaptic AMPAR–bassoon colocalization | None | Not stated for images (generic "data...found within the article and its supplementary information") |
| [LGI1–ADAM22–PSD93 at the AIS](#lgi1-adam22) | [doi:10.1242/jcs.264880](doi:10.1242/jcs.264880) | ImageJ (v1.54p), PyMOL (structure only) | ImageJ: 1.54p | 1) AIS fluorescence-intensity linescan (protein clustering); 2) AIS length; 3) AlphaFold structural visualization (non-micrograph) | None | Not stated for images (generic "data...found within the article and its supplementary information") |
| [PIK3CA / ERK wave collective migration](#pik3ca-erk) | [doi:10.1242/jcs.264916](doi:10.1242/jcs.264916) | Trackmate+Cellpose3, PIVLab (MATLAB), AVeMap, ilastik, CellProfiler, Time Course Inspector, DiPer, Origin, Python | Cellpose3 named, others mostly unversioned | 1) Cell tracking & directional persistence; 2) PIV & order parameter; 3) ERK activity (C/N ratio) time course; 4) ERK–speed cross-correlation; 5) Leader-cell counting; 6) Actomyosin polarity (polar plots) | 1 GitHub repo | Not stated for images ("raw data and scripts are available upon request" — mentions "raw data" generically, not images specifically) |

---

(endo-cx43)=
## Endothelial cell biomechanical adaptation to altered connexin 43 expression under fluid shear stress

Islam, Subramanianbalachandar, Steward Jr — *J. Cell Sci.* 139, jcs264023 (2026). [doi:10.1242/jcs.264023](doi:10.1242/jcs.264023)

Three separate image-analysis pipelines, all built on custom code rather than off-the-shelf plugins:

1. **Traction force microscopy (TFM) and monolayer stress microscopy (MSM)**: substrate-gel bead displacements tracked with a particle-image-velocimetry routine **custom-written in MATLAB**; cell-substrate tractions computed via Fourier-transform TFM; intercellular stresses derived from the traction field using a 2D force-balance stress tensor (MSM). **→ Fig. 1A,B** (traction color plots & traction-vs-time, chalcone) and **Fig. 2A,B** (traction, RA) for tractions; **Fig. 1C,D** and **Fig. 2C,D** (RMS/normal/shear stress color plots and vs. time) for intercellular stress; strain-energy calculations reported in **Fig. S1C,D** (chalcone) and **Fig. S2C,D** (RA).
2. **Cell area and orientation**: a **custom-written MATLAB algorithm** (image-processing toolbox) binarizes phase-contrast images, segments individual cells, and extracts per-cell area (pixel count converted to µm²) and orientation. **→ Fig. 3B,C,E,F** (chalcone, orientation/area under static and FSS) and **Fig. 4B,C,E,F** (RA, same measurements); cell-velocity data from the same tracking are reported only in **Fig. S1A,B** (chalcone) / **Fig. S2A,B** (RA) — no main-figure velocity panel.
3. **Mean dye transfer length (GJIC assay)**: dye-transfer images imported into `ImageJ`; length measured by manually drawing perpendicular lines from the scrape edge to the furthest point of visible dye transfer. **→ Fig. 5C,D** (chalcone) and **Fig. 6C,D** (RA).

```{admonition} Verbatim quote
:class: tip
"Cell-induced substrate gel deformations were calculated using a particle image velocimetry routine custom-written in MATLAB, and cell-substrate tractions were calculated using Fourier transform traction force microscopy... Cell area and orientation were measured using a custom-written algorithm in MATLAB. This algorithm utilizes the image-processing toolbox... Images of dye transfer were imported into ImageJ and mean dye transfer length was calculated by manually drawing horizontal lines perpendicular to the scrape area."
```

- **Software named**: custom MATLAB (PIV / Fourier-transform TFM / MSM; separate custom MATLAB cell-segmentation algorithm), `ImageJ` (dye-transfer length only).
- **Code repository**: none provided — the MATLAB routines are described as "custom-written" with no link, and cite the group's own prior papers as the algorithm source.
- **Sample image data**: Not stated for images specifically. The Data and resource availability statement reads: "All relevant data and details of resources can be found within the article and its supplementary information" — generic, with no repository named and no explicit mention of raw images (only the cell-area/orientation code is separately offered "upon request").
- **Based on prior methods**: TFM/MSM procedure — Butler et al., 2002; Tambe et al., 2011, 2013; Trepat et al., 2009; Islam & Steward, 2019a,b (the authors' own prior JoVE/Exp. Mech. papers, which is where the actual MATLAB algorithm was first described in detail). GJIC scrape-loading dye-transfer assay — Dydowiczova et al., 2020; Noguchi et al., 1999; Watanabe et al., 1999.

---

(lats2-phf6)=
## Ribosomal RNA transcription is regulated by sequestration of LATS2 and PHF6 to the nuclear speckles following DNA damage

Suzuki, Mukai, Kato, Sakashita, Endo, Nojima, Yabuta — *J. Cell Sci.* 139, jcs264138 (2026). [doi:10.1242/jcs.264138](doi:10.1242/jcs.264138)

A single Methods sentence ("image analysis was performed using FV10-ASW and ImageJ") underlies a repeated line-scan/scatter-plot colocalization workflow applied across six figures:

1. **Colocalization scoring**: for each pair of channels, a line scan is drawn across a nuclear-speckle focus (position marked in the representative image), the two channels' intensity profiles are plotted, a scatter plot of pixel-pair intensities is generated, and the percentage of cells with "high/high" colocalized foci is counted (100 cells/sample, 3 independent experiments). **→ Fig. 1B–D** (LATS2-pS835 vs SC35), **Fig. 3B–D** (PHF6-pS183 vs SC35), **Fig. 4B,C** (LATS2-pS835 vs total PHF6) and **Fig. 4E,F** (PHF6-pS183 vs total PHF6), **Fig. 5D** (PHF6 vs NPM, nucleolar colocalization) and **Fig. 6B,C** (FUrd incorporation vs DNA, nucleolar transcription assay).
2. **Western-blot band-intensity quantification**: `ImageJ` densitometry, normalized to α-tubulin and to the untreated parental control. **→ Fig. 2E** (PHF6-pS183 level from the in vitro/in vivo kinase-assay blot shown in **Fig. 2D**).

```{admonition} Verbatim quote
:class: tip
"The image analysis was performed using the FV10-ASW (Olympus) and ImageJ (NIH) software."
```

- **Software named**: `FV10-ASW` (Olympus, acquisition-side image handling), `ImageJ` (NIH).
- **Code repository**: none.
- **Sample image data**: Not stated for images specifically. The statement reads: "The mass spectrometry proteomics data have been deposited to the ProteomeXchange consortium... All other relevant data and details of resources can be found within the article and its supplementary information" — the public deposit is proteomics data, not imaging data, which falls under the generic clause.
- **Based on prior methods**: no citation is attached to the line-scan/colocalization scoring approach itself — it reads as this lab's own procedure, consistent with their earlier paper (Suzuki et al., 2013) which is cited for the antibodies and unrelated assays, not for this specific image-quantification method.

---

(mglur-dopamine)=
## Metabotropic glutamate receptor internalization and synaptic AMPA receptor endocytosis by dopamine

Aruna, Kulkarni, Bhattacharyya — *J. Cell Sci.* 139, jcs264725 (2026). [doi:10.1242/jcs.264725](doi:10.1242/jcs.264725)

A section explicitly titled *"Image acquisition and analysis"* describes a masked-thresholding internalization-index pipeline, reused across most main figures:

1. **Internalization index**: raw confocal images maximally projected → thresholded with identical values across all images in a comparison (to avoid bias) → binary mask separates real fluorescence from background → thresholded areas of surface vs. internalized receptor signal measured → internalization index = internal fluorescence / (surface + internal fluorescence), normalized to control, all in `ImageJ`. **→ Fig. 1B** (mGluR1 internalization), **Fig. 2B** (mGluR5 internalization), **Fig. 3B** (dose/time course), **Fig. 4B,H** (clathrin/dynamin dependence — pharmacological and knockdown), **Fig. 8B,D,F** (DHPG/dopamine dose and receptor-blocker experiments).
2. **Surface-receptor fraction**: thresholded surface-fluorescence area divided by cell area (itself defined via a low-threshold background mask), normalized to control-cell average. **→ Fig. 6B** and **Fig. 7B,D,F** (recycling assays, PP2A/PP2B dependence).
3. **Synaptic AMPAR colocalization**: surface GluA1 puncta thresholded at a single z-section and scored against presynaptic bassoon puncta; reported as % of bassoon-defined synapses with detectable surface GluA1. **→ Fig. 8H**.
4. Representative-image cosmetic adjustments only (no quantification) in `Adobe Photoshop`.

```{admonition} Verbatim quote
:class: tip
"All analyses were done in a masked manner using raw images, and quantification was done using ImageJ software (National Institutes of Health, USA) (Schneider et al., 2012)... Internalization index for each cell was then calculated by dividing the value contributed by the internal fluorescence with the value contributed by the total fluorescence (surface+internal)."
```

- **Software named**: `ImageJ` (NIH), `Adobe Photoshop` (cosmetic only).
- **Code repository**: none.
- **Sample image data**: Not stated for images specifically. The Data and resource availability statement reads only: "All relevant data and details of resources can be found within the article and its supplementary information" — generic, with no repository accession and no explicit mention of raw images.
- **Based on prior methods**: the masked-thresholding/internalization-index procedure itself is explicitly attributed to the authors' own prior papers — Gulia et al., 2017; Mahato et al., 2015; Ojha et al., 2022; Pandey et al., 2014, 2020; Sharma et al., 2018; Trivedi & Bhattacharyya, 2012 — plus the general ImageJ citation, Schneider et al., 2012.

---

(lgi1-adam22)=
## The LGI1–ADAM22 complex organizes PSD93 clustering at the axon initial segment

Zhang, Tan, Teng, Hu, Li, Liu, Shi — *J. Cell Sci.* 139, jcs264880 (2026). [doi:10.1242/jcs.264880](doi:10.1242/jcs.264880)

A section explicitly titled *"AIS staining image analysis"*, with a version number and a direct methodological citation — unusual thoroughness for this issue:

1. **AIS fluorescence-intensity linescan**: images opened in `ImageJ` (version 1.54p), channels split; using the segmented-line tool (line width 5) a line is drawn along the entire AnkyrinG-positive AIS, saved to the ROI Manager, then overlaid on the PSD93 or ADAM22 channel and measured (mean gray value) with the `Measure` tool; final calculations in `GraphPad Prism` (version 10.6.1). **→ Fig. 1F,H** (PSD93 intensity along the AIS in CA3 and cortical neurons, *Lgi1* KO), **Fig. 3B,D** (ADAM22 intensity, *Lgi1* KO), **Fig. 4G** (LGI1 intensity, *Adam22* cKO), **Fig. 5B,D** (PSD93 intensity, *Adam22* cKO, CA3/cortex) and **Fig. 5F** (AIS length in cultured *Adam22* cKO neurons).
2. **Structural visualization** (not micrograph image analysis): an AlphaFold 3-predicted ADAM22–PSD93 PDZ interaction model rendered in `PyMOL` (version 1.8.6.2). **→ Fig. 6D** — flagged separately since this is molecular-structure visualization, not fluorescence-image quantification.

```{admonition} Verbatim quote
:class: tip
"Statistical analysis of fluorescence intensity was conducted according to methods reported in previous studies (Di Re et al., 2019). Images were opened in ImageJ (version 1.54p) and channels were split. Using the segmented line tool, with a line width of 5, lines were drawn along the entire AnkyrinG-positive AIS... The AnkyrinG ROIs were overlaid onto the PSD93 or ADAM22 channels and mean gray values were obtained using the 'Measure' tool."
```

- **Software named**: `ImageJ` (v1.54p), `GraphPad Prism` (v10.6.1), `PyMOL` (v1.8.6.2, structural figure only).
- **Code repository**: none.
- **Sample image data**: Not stated for images specifically. The Data and resource availability statement reads only: "All relevant data and details of resources can be found within the article and its supplementary information" — generic, with no repository accession and no explicit mention of raw images.
- **Based on prior methods**: the AIS-intensity linescan approach is explicitly cited to Di Re et al., 2019.

---

(pik3ca-erk)=
## Oncogenic PIK3CA enhances collective migration of mammary epithelial cells through ERK wave propagation

Dayoub, Fokin, Leonov, Gautreau, Alexandrova — *J. Cell Sci.* 139, jcs264916 (2026). [doi:10.1242/jcs.264916](doi:10.1242/jcs.264916)

By far the most computationally elaborate paper in this issue — a live-cell imaging pipeline combining classical PIV, deep-learning segmentation, a pixel-classification ML tool, and custom Python signal analysis:

1. **Cell tracking & directional persistence**: nuclei (H2B–miRFP703) tracked with the `ImageJ` plugin **Trackmate** (Ershov et al., 2022) using the **Cellpose3** deep-learning segmentation algorithm (Stringer & Pachitariu, 2025) for nucleus detection; trajectories and directional persistence (autocorrelation of angular deviation, fit to an exponential-decay-with-plateau model) computed with the **DiPer** software (Gorelik & Gautreau, 2014). **→ Fig. 1F** (directional persistence) and **Fig. 1G** (trajectories); the Methods text also references a supplementary version of this analysis at **Fig. S2**.
2. **Particle image velocimetry (PIV) & order parameter**: wound-healing movies processed with the open-source **PIVLab** (MATLAB; Thielicke & Sonntag, 2021; Thielicke & Stamhuis, 2014, FFT window-deformation algorithm) to obtain displacement-vector fields; the local order parameter (cosine of the angle between each velocity vector and the wound-border normal) computed with **AVeMap** (Deforet et al., 2012) and visualized as a colored kymograph. **→ Fig. 1D** (order-parameter heat maps) and **Fig. 1E** (PIV displacement-vector overlay); **Fig. S2** again referenced for the underlying order-parameter kymograph.
3. **ERK activity (C/N ratio) pipeline**: raw H2B–miRFP703 images processed with **ilastik** (manually trained pixel classifier, ≥100 cells/line) for nucleus prediction, then **CellProfiler** for nucleus/cytoplasm segmentation and calculation of the cytoplasmic/nuclear (C/N) ratio of the ERK-KTR biosensor; heatmaps and per-FOV/total ERK-activity time courses generated with the **Time Course Inspector** Shiny app (Dobrzynski et al., 2020). **→ Fig. 3A–D** (ERK-wave kymographs, fluctuation traces, total activity, wave frequency/speed/distance) and **Fig. 4A,B** (ERK-vs-speed kymographs and traces); the full pipeline is diagrammed in **Fig. S3**.
4. **Cross-correlation analysis**: custom **Python** scripts (NumPy, pandas, matplotlib) compute the temporal cross-correlation between the ERK-activity signal and the cell-speed signal across time lags. **→ Fig. 4C**.
5. **Leader-cell counting**: front-row cells counted with the `ImageJ` **'Cell Counter'** plugin.
6. **Actomyosin polarity (polar plots)**: eight radial lines drawn from each cell's nuclear center to the cell periphery; F-actin and pMLC2 intensities measured at each line/cell-contour intersection; profiles compiled and rendered as polar plots in **Origin** (OriginLab). **→ Fig. 6B**.
7. **Y27632-treated ERK-wave/pMLC2 dataset**: same ilastik/CellProfiler/Time-Course-Inspector pipeline as (3), applied to ROCK-inhibited cells. **→ Fig. 5C–F**.

```{admonition} Verbatim quote
:class: tip
"Cells were tracked using with the ImageJ plugin, Trackmate (Ershov et al., 2022) with the segmentation algorithm Cellpose3 (Stringer and Pachitariu, 2025)... Cells defined by their nuclei were then analyzed for recognition of nuclei and cytoplasm using the CellProfiler software (https://cellprofiler.org/), allowing calculation of cytoplasmic/nuclear (C/N) ratio of ERK-KTR. Heatmaps of ERK activity dynamics... were obtained using the Time Course Inspector (https://github.com/dmattek/shiny-timecourse-inspector; Dobrzynski et al., 2020)."
```

```{note}
:class: dropdown
Leader-cell counting (item 5 above) is named in Methods with a specific ImageJ plugin, but the text never ties this count to one numbered main-figure panel — flagged here rather than guessed, per the same policy applied to ambiguous cases in the Issue 16 report.
```

- **Software named**: `ImageJ`/`Trackmate`, `Cellpose3`, `DiPer`, `PIVLab` (MATLAB), `AVeMap`, `ilastik`, `CellProfiler`, `Time Course Inspector`, `Origin`, custom `Python` (NumPy/pandas/matplotlib), `GraphPad Prism` (v8.00, statistics only).
- **Code repository**: `Time Course Inspector` — <https://github.com/dmattek/shiny-timecourse-inspector>. The custom Python cross-correlation scripts are explicitly described as "available upon request" rather than posted to a repository.
- **Sample image data**: Not stated for images specifically. The Data and resource availability statement reads: "Raw data and scripts are available upon request. All relevant data and details of resources can be found within the article and its supplementary information." This is the closest wording to an image-data commitment found in this issue — "raw data" could plausibly include the raw movies/micrographs — but it does not name images explicitly, so it is classified here as generic rather than an explicit image-data statement.
- **Based on prior methods**:
  - Trackmate — Ershov et al., 2022.
  - Cellpose3 segmentation — Stringer & Pachitariu, 2025.
  - DiPer trajectory/persistence software — Gorelik & Gautreau, 2014; the exponential-decay persistence fit — Wang et al., 2023.
  - PIVLab — Thielicke & Sonntag, 2021; Thielicke & Stamhuis, 2014.
  - AVeMap order-parameter analysis — Deforet et al., 2012.
  - Time Course Inspector — Dobrzynski et al., 2020.
  - ERK-KTR biosensor construct — Gagliardi et al., 2021 (also Goedhart et al., 2012; Regot et al., 2014, cited in Discussion).

---

## Caveats

```{warning}
- Checked for explicit pointers to a **supplementary Materials and Methods** document (e.g. "as described in the supplementary information", "detailed in supplementary methods"): none of the 5 articles in this issue defer any *image-analysis* step to a separate supplementary methods document. Every "supplementary information" mention found is the standard JCS data-availability boilerplate ("data...can be found within the article and its supplementary information"), not a pointer to additional methodological text. If a future issue's papers do defer method detail this way, that will be flagged inline in the relevant workflow step rather than silently missed.
- Only one article in this issue (PIK3CA/ERK wave, jcs264916) links an actual code repository, and only for one component of its pipeline (Time Course Inspector); its own custom Python cross-correlation scripts are stated as "available upon request," not posted anywhere. No other article in the issue provides any code link.
- Several software mentions have no version number (custom MATLAB routines in the endothelial-biomechanics paper, FV10-ASW/ImageJ in the LATS2–PHF6 paper, ImageJ in the mGluR/dopamine paper, most of the tools in the PIK3CA/ERK-wave pipeline besides Cellpose3 and ImageJ v1.54p/GraphPad v10.6.1 in the AIS paper).
- "Based on prior methods" here means a citation was attached to that *specific* analysis step in the text — several papers in this issue (LATS2–PHF6, most notably) cite prior work only for antibodies or unrelated assays, and the image-quantification procedure itself is uncited, which is noted explicitly rather than treated as "based on" those citations.
- Two figure references in the PIK3CA/ERK-wave paper's Methods text (directional persistence/trajectories, and the order parameter) point to a supplementary figure (Fig. S2) even though the main-text Fig. 1F,G,D,E legends describe what reads as the same measurements — both the main and supplementary figure numbers are given above rather than picking one.
- The AIS paper's PyMOL/AlphaFold panel (Fig. 6D) is listed for completeness but is structural-model visualization, not image analysis of a micrograph — don't conflate it with the fluorescence-linescan figures in the same paper.
- Leader-cell counting in the PIK3CA/ERK-wave paper is named with its specific ImageJ plugin in Methods but not tied to a numbered figure panel in the body text — flagged rather than guessed.
- **Sample image data availability**: each article's Data and resource availability statement was checked for whether it makes raw/original *image* data available, as distinct from code availability. All 5 articles in this issue fall into the same category — none explicitly commits to sharing raw or original images. Two articles (LATS2–PHF6, jcs264138, and Beadex-adjacent RNA-seq deposits elsewhere in this survey) publicly deposit non-image data (mass-spectrometry proteomics, in this case) alongside the generic "found within the article and its supplementary information" clause for everything else; the PIK3CA/ERK-wave paper (jcs264916) comes closest with "raw data and scripts are available upon request," but this does not name images specifically. No article in this issue publicly deposits raw/original images, and none was found to have no Data and resource availability statement at all.
```
