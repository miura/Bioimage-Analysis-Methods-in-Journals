---
title: Journal of Cell Biology, Volume 225, Issue 7 (12 articles)
subtitle: Bioimage analysis methods survey
subject: Methods survey
date: 2026-09-24
---

:::{note}
**Methodology.** All 12 article PDFs in this folder were converted to plain text with `pdftotext -layout` (poppler-utils) and searched with `grep`/`sed` for image-analysis Methods subsections, exact software name strings and version numbers, code-repository URLs, and citations tying a specific analysis step to a prior published method. Figure/panel numbers were cross-checked against figure-legend text (legend wording is treated as authoritative when it conflicts with a body-text parenthetical citation). Several articles in this issue are "HHS Public Access" or "Europe PMC Funders Group" author-manuscript reformattings, in which the Materials and Methods section and/or figure legends are relocated to the end of the document (after the References list) and legends are headed "Figure N." rather than "Fig. N."; this was checked for and accounted for per article, and is noted below where it applies. Given the number and length of papers in this issue, extraction was parallelized: twelve independent passes (one per article) applied the identical grep/legend-cross-checking procedure used for the two prior JCS issue reports, and their findings were merged into this single document. Every article was also explicitly checked for genuine deferral of image-analysis methodological detail to a separate supplementary Materials and Methods document not included in the main-text PDF (as opposed to routine pointers to a supplementary figure, movie, or table, or generic data-availability boilerplate), and, separately, for whether its Data Availability statement makes raw/original sample image data itself available (as distinct from code availability) — see the "Sample image data" table column, the per-article bullet of that name, and the Caveats section for both outcomes.
:::

## At a glance

| Article | DOI | Key imaging software | Version given? | Measurement target | Code repo | Sample image data |
|---|---|---|---|---|---|---|
| [Yeh et al. — Bitesize/F-actin, *Drosophila* embryo](#jcb-202306071) | [doi:10.1083/jcb.202306071](doi:10.1083/jcb.202306071) | Custom MATLAB (Frangi-filter segmentation), FIJI, GraphPad Prism | Partial (MATLAB R2019b; FIJI 2.0.0-rc-68/1.52e for TIRF only) | 1) Actin cap area; 2) Nuclear density/fallout; 3) Actin cap growth kinetics; 4) Furrow apical/basal actin ratio; 5) pMoesin nuclear enrichment; 6) F-actin bundle thickness (TIRF FWHM); 7) BtszB–F-actin binding affinity (Kd, Hill coefficient) | None | No Data Availability statement found in this PDF |
| [Guerrero-Fonseca et al. — Neutrophil proteases/cortactin](#jcb-202410019) | [doi:10.1083/jcb.202410019](doi:10.1083/jcb.202410019) | Imaris, ImageJ, FlowJo, GraphPad Prism, PROSPER | No | 1) Cortactin MFI (junctional/cytoplasmic); 2) Endothelial CatG internalization; 3) Transmigrated neutrophil counts; 4) Intracellular CatG dot counts; 5) Rolling velocity/adhesion/flux (IVM); 6) Western blot band intensity; 7) Flow-cytometric MFI; 8) In-silico protease cleavage-site prediction | None | Not stated for images (generic "data available in article and supplemental material") |
| [Covill-Cooke et al. — Mmm1 lipid transport](#jcb-202411196) | [doi:10.1083/jcb.202411196](doi:10.1083/jcb.202411196) | Volocity, Fiji, SoftWoRx, GraphPad Prism, AlphaFold3, ChimeraX, Damietta | No | 1) Vps13-GFP/Mdm34-mCherry colocalization frequency; 2) Mitochondrial morphology; 3) Cardiolipin/phospholipid levels (TLC autoradiography); 4) Tethered-construct protein levels (immunoblot); 5) Predicted Mmm1–Mdm10 3D structure (non-micrograph) | None | Not stated for images (generic "data available in article and supplemental material") |
| [Petrova/Bernier-Latmani et al. — Eosinophils and villus SMC](#jcb-202505012) | [doi:10.1083/jcb.202505012](doi:10.1083/jcb.202505012) | Imaris, Fiji (+TrakEM2), Photoshop, Affinity Photo 2, GraphPad Prism | Partial (bioinformatics packages versioned; imaging tools not) | 1) GFP+ SMC count/distribution per villus; 2) Eosinophil position and density; 3) Cell–cell contact counts (volume EM); 4) SMC area per villus; 5) Transition/"star" cell counts; 6) RNA-seq differential expression/GSEA; 7) TGFβ-pathway villus SMC quantification | None | Not stated for images (only RNA-seq data are publicly deposited in GEO; imaging data are "available from the corresponding authors upon reasonable request," not deposited) |
| [Yang et al. — Optogenetic astrocyte Ca2+](#jcb-202506032) | [doi:10.1083/jcb.202506032](doi:10.1083/jcb.202506032) | AQuA, ImageJ (Reslice, ROI Manager, TrackMate, Kymograph Builder), GraphPad Prism 10 | Partial (Prism 10 only) | 1) Ca2+ event amplitude/duration/frequency; 2) Organelle spatial distribution; 3) Organelle mean velocity; 4) FRAP kymographs; 5) Process length/elongation; 6) IP3R immunoblot band intensity | None | Not stated for images ("original data are available from the corresponding authors upon request" — generic, not image-specific) |
| [Appalabhotla et al. — Optogenetic PLC-γ1](#jcb-202507177) | [doi:10.1083/jcb.202507177](doi:10.1083/jcb.202507177) | MATLAB, Python, Li-Cor Odyssey | No | 1) HaloTag membrane-recruitment kinetics; 2) Protrusion/retraction pixel maps; 3) Cell-edge velocity maps; 4) Calcium (R-GECO) response; 5) DAG-biosensor enrichment; 6) PLC-γ1 phosphorylation (immunoblot); 7) Phospholipase activity (scintillation counting) | None | Not stated for images ("data underlying the figures...unconditionally available upon request" — generic, not image-specific) |
| [Curtis et al. — Cell wall integrity at yeast mating contact](#jcb-202508068) | [doi:10.1083/jcb.202508068](doi:10.1083/jcb.202508068) | MetaMorph/NIS-Elements (GA3), ImageJ, Fiji + HyperStackReg, MATLAB (ROI_TOI_QUANT_V9), R/ggplot | Partial (MetaMorph 7.8; HyperStackReg DOI truncated in source) | 1) Mating efficiency/outcome classification; 2) Cortical protein clustering parameter; 3) Cortical fluorescence linescans; 4) Kymographs (Bem1/Pkc1 dynamics); 5) Mean per-cell GFP intensity | None (only a truncated third-party Zenodo DOI for the HyperStackReg plugin) | Not stated for images ("data generated in this study are available from the corresponding author upon reasonable request" — generic, not image-specific) |
| [Bacher et al. — *Rickettsia* actin-based motility](#jcb-202508117) | [doi:10.1083/jcb.202508117](doi:10.1083/jcb.202508117) | ImageJ2/Fiji, NIS Elements, MetaMorph, Zen Black, Huygens Professional, Imaris, Geneious, InterPro, AlphaFold3, RAW/BilboMD/FoXS/MultiFoXS | Yes (Fiji v2.9.0/1.53t; Imaris 10.2; Huygens v24.10; Prism 10.3.1/11; Geneious 2025.0.3/2026.0.1) | 1) Actin polymerization kinetics; 2) Nucleation rate; 3) G-actin binding affinity; 4) Barbed-end elongation rate (TIRF); 5) Sequence/motif analysis; 6) Predicted structure; 7) SEC-SAXS ensemble modeling; 8) Bacteria/actin-tail counts; 9) Surface Sca2 coverage (3D morphometry); 10) Actin-tail intensity line-scans; 11) Bacterial motility speed/efficiency | None | Not stated for images ("Data...underlying Figures 2, 3, 5, 6, 7, 8, 9, and S5 are included in Supplementary Dataset S1" — a numeric source-data file, not stated to contain raw/original micrographs) |
| [Chouhan et al. — Arl8b/Rab11a/LAMP1 sorting](#jcb-202509040) | [doi:10.1083/jcb.202509040](doi:10.1083/jcb.202509040) | ImageJ (JaCoP, RGB profile), Fiji, custom Python/OpenCV/TrackPy, FlowJo/FACSDiva, GraphPad Prism 8.0 | Partial (Prism 8.0; FlowJo 10.0.1; FACSDiva 8.0.1) | 1) Colocalization coefficients (Manders'/Pearson's); 2) Intensity line-scan profiles; 3) p62 punctum counts; 4) Perinuclear index; 5) Corrected total cell fluorescence; 6) Lysosome number/area; 7) Ripley's K spatial clustering; 8) Diffusion exponent; 9) Flow-cytometric surface MFI; 10) Immuno-EM vesicle diameter; 11) Western blot densitometry | None for own code (third-party OpenCV/TrackPy citation links only) | Not stated for images ("all relevant data...are included in the manuscript and supplementary material" — generic, not image-specific) |
| [Das et al. — NASP and H3 nuclear import](#jcb-202511182) | [doi:10.1083/jcb.202511182](doi:10.1083/jcb.202511182) | ZEN 3.3, Ilastik, FIJI, Bio-Rad Image Lab | No | 1) H3.2/H3.3 nuclear import rate; 2) Simulated import curve; 3) Nuclear export decay; 4) Mitotic chromatin intensity; 5) NASP vs. H3.2 relative import; 6) Cell-cycle duration; 7) Photobleaching control; 8) Western blot densitometry; 9) Aggregate-isolation assay quantification | None | On request only — explicit: "All raw and processed images are available upon reasonable request" (not a public deposit) |
| [Sakers et al. — Neuroligin-2/Nedd4l astrocyte morphogenesis](#jcb-202512111) | [doi:10.1083/jcb.202512111](doi:10.1083/jcb.202512111) | FIJI + Sholl Analysis plugin, Imaris, SynBot, R/clusterProfiler, ImageJ, Proteome Discoverer, Mascot | Yes (FIJI v1.53c; Sholl v4.0.1; Imaris v9.9; ImageJ v1.54f; clusterProfiler v4.6.2; Proteome Discoverer 2.3; Mascot v2.5) | 1) Dendritic/process branching complexity (Sholl); 2) 3D territory volume/3D Sholl; 3) Synapse colocalization/density; 4) CRISPR editing efficiency (immunoblot); 5) Co-IP band quantification; 6) Ubiquitination-assay quantification; 7) Protein degradation kinetics; 8) iBioID immunoblot densitometry; 9) GO-term enrichment; 10) Mass-spectrometry interactome statistics | 4 GitHub repos (Eroglu-Lab) | Yes — public: "all original images can be accessed via Duke Digital Repository" (doi:10.7924/r4r500) |
| [Williams et al. — Chromosome segregation synchrony, *S. pombe*](#jcb-202602088) | [doi:10.1083/jcb.202602088](doi:10.1083/jcb.202602088) | softWoRx, MATLAB, TrackMate/ImageJ, R, Python/SciPy | No (imaging-tool versions unstated; RRIDs given) | 1) Sister-chromatid separation timing (Δt synchrony); 2) Kymograph visualization; 3) Centromere-distance tracking kinetics; 4) Securin-GFP degradation kinetics; 5) Stochastic model fit to separation-timing data (non-imaging) | 2 Zenodo DOIs (one is data, one is non-imaging stochastic-model code) | Not stated for images ("data underlying Δt distributions" is openly in Zenodo, but this is derived numeric measurement data, not stated to include the raw microscopy movies themselves) |

(jcb-202306071)=
## Yeh et al. — Bitesize bundles F-actin and influences actin remodeling in syncytial *Drosophila* embryo development

Anna R. Yeh, Gregory J. Hoeprich, Anthony McDougal, Bruce L. Goode, Adam C. Martin — *J. Cell Biol.* 225(7) (2026). [doi:10.1083/jcb.202306071](doi:10.1083/jcb.202306071)

:::{note} Reformatting note
This is an HHS Public Access author-manuscript version: Materials and Methods appears inline, but figure legends are relocated to the end of the document (after References) and headed "Figure N." rather than "Fig. N."
:::

1. **Actin cap segmentation and area quantification.** A custom MATLAB (R2019b) pipeline — intensity scaling, `FrangiFilter2D` ridge enhancement, Gaussian blur (`imgaussfilt()`), seed detection (`imregionalmin()`), median filter, `watershed()` segmentation — with manual correction in FIJI, measures actin-cap area during nuclear cycle 12. **→ Figure 2, A–B''** (cap visualization and area/histogram quantification).
2. **Nuclear counting and fallout frequency.** The same MATLAB segmentation pipeline applied to Sqh::GFP maximum-intensity projections, combined with FIJI area/count measurements, gives nuclear density and fallout frequency. **→ Figure 3F** (nuclear fallout/density); reused for **Figure 5D** (relative nuclear density in mutants).
3. **Actin cap growth kinetics.** Manual FIJI segmentation across timepoints (area, aspect ratio) with MATLAB-fitted growth-rate slopes.
   :::{note} Figure mapping ambiguity
   The text cites this result to "(Figure S2D–E)" — a supplementary figure not included in this PDF. No main-text figure panel could be found for this specific growth-rate measurement.
   :::
4. **Furrow actin intensity (apical/basal ratio).** FIJI intensity measurement of the most apical/basal 2 μm of cellularization furrows, normalized (I−Imin)/(Imax−Imin).
   :::{note} Figure mapping ambiguity
   Only a related qualitative comparison is tied to "Figure S4A, B" (supplementary, not in this PDF); no main-text panel citation could be found for this specific ratio measurement.
   :::
5. **pMoesin nuclear-enrichment quantification.** FIJI "Plot Profile" intensity traces across 3–4 nuclei per embryo, averaged to give fold nuclear enrichment. **→ Figure 4E** (Btsz RNAi vs. control) and **Figure 5F** (btsz exon 4 and btszK13-4 mutants vs. control).
6. **Confocal image acquisition.** Zeiss LSM 710 point-scanning confocal, Zen (Zeiss ZEN) software, 40×/1.2 or 63×/1.4 objectives — underlies all fixed/live confocal panels in **Figures 2–5**.
7. **General image processing.** FIJI/MATLAB linear brightness/contrast adjustment for all figures; Gaussian blur (0.5) for **Figures 2, 3, 4B, S4A**; Gaussian blur + rolling-ball background subtraction (radius 50 px) for **Figure 5D**.
8. **BtszB–F-actin co-sedimentation quantification.** Coomassie-gel densitometry on a ChemiDoc Imaging System (BioRad), fit to a Hill equation and compared in GraphPad Prism (Mann-Whitney U). **→ Figure 6, B–E** (Kd, Hill coefficient, low-speed pelleting fraction).
9. **TIRF actin-bundling (filament thickness).** FIJI v2.0.0-rc-68/1.52e, rolling-ball background subtraction (5 px), perpendicular line-scan fit to a 2D Gaussian for FWHM. Acquired on a Nikon-Ti2000 TIRF system (Nikon "Elements" software). **→ Figure 6, F–G** (representative images and FWHM/thickness quantification).
10. **General statistics.** GraphPad Prism and MATLAB, primarily Mann-Whitney U tests (Student's t-test noted for Figure 6E) — applied across **Figures 2–6** quantification panels.

:::{admonition} Verbatim quotes
:class: note, dropdown
"Figure images were processed in FIJI or MATLAB R2019b. For actin cap area and nuclear fallout quantifications, images were run through a segmentation analysis (detailed below) in MATLAB."

"Ridge-like structures in the image were enhanced with FrangiFilter2D using the default parameters (Dirk-Jan Kroon (2022). Hessian based Frangi Vesselness filter... MATLAB Central File Exchange); based on (Frangi et al., 1998)."

"Images were analyzed in FIJI version 2.0.0-rc-68/1.52e (National Institutes of Health, Bethesda, MD). Background subtraction was conducted using the rolling ball background subtraction algorithm (ball radius, 5 pixels)."
:::

- **Software:** FIJI (v2.0.0-rc-68/1.52e for TIRF; unversioned elsewhere), MATLAB R2019b, Zen (Zeiss ZEN), Nikon Elements, GraphPad Prism, ChemiDoc Imaging System, FrangiFilter2D (MATLAB File Exchange).
- **Code repository:** None. The only link found is to a third-party MATLAB File Exchange filter function, not the authors' own segmentation code; the code's author (Jonathan Jackson) is thanked in Acknowledgments but no repository is provided.
- **Sample image data:** No Data Availability statement was found anywhere in this manuscript — not even the generic "available upon request" boilerplate seen in other articles in this issue.
- **Based on prior methods:** Frangi et al., 1998 (Frangi vesselness ridge-enhancement filter — the one image-analysis step tied to a prior citation).

(jcb-202410019)=
## Guerrero-Fonseca et al. — Neutrophil serine proteases degrade endothelial cortactin and promote extravasation

Idaira M. Guerrero-Fonseca, Karina B. Hernández-Almaraz, Iliana I. León-Vega, Régis Joulia, Armando Montoya-García, Hilda Vargas-Robles, Theresia E.B. Stradal, Klemens Rottner, Reyna Oregon, Eduardo Vadillo, Jennifer L. Johnson, William B. Kiosses, Sergio D. Catz, Sussan Nourshargh, Michael Schnoor — *J. Cell Biol.* 225(7), e202410019 (2026). [doi:10.1083/jcb.202410019](doi:10.1083/jcb.202410019)

1. **Cortactin MFI at endothelial junctions.** 3D-reconstructed confocal z-stacks of postcapillary venules (PCVs), analyzed in Imaris via isosurface masking of PECAM-1(CD31)-positive junctional vs. cytoplasmic areas. **→ Fig. 1, C and E**; also **Fig. 2D**, **Fig. 5B**, **Fig. S1B**.
2. **Endothelial CatG internalization.** Imaris isosurface masking of MRP-14 signal (to exclude neutrophil CatG) followed by masking within CD31-positive areas. **→ Fig. 4, E–G**; **Video 1**.
3. **Cortactin degradation / transmigrated neutrophil counts (AAT-augmentation experiment).** Imaris analysis of confocal z-stacks. **→ Fig. 5, B and C**.
4. **HUVEC CatG dot counts and cortactin MFI (super-resolution, NEI20 exocytosis-inhibition).** Imaris isosurface masking. **→ Fig. 4, C and D**; representative images **Fig. 4, A–B**.
5. **Neutrophil rolling velocity, adhesion, and flux (intravital microscopy).** Acquired on an Axioscope A1 (Zeiss) epifluorescence/transillumination intravital rig.
   :::{note} Methods gap
   No analysis/tracking software is named anywhere in the text for computing flux, rolling velocity, or adhesion counts from these recordings — this step's software is not stated. **→ Fig. 5, D–F**.
   :::
6. **Video/flow-chamber adherent-leukocyte analysis.** "Recorded videos were analyzed using ImageJ software" — the specific panel this applies to is not cross-referenced explicitly in the legend text.
7. **Western blot densitometry** (cortactin, VE-cadherin, CatG, vinculin, GAPDH, γ-tubulin, ArpC5A, Arpin). ImageJ pixel-intensity quantification. **→ Fig. 3, C, D, G, H**; **Fig. S2A**.
8. **Flow cytometry** (cortactin MFI, CatG MFI, neutrophil-depletion efficiency). FACS Canto II acquisition, FlowJo Treestar V10 analysis. **→ Fig. 2, E–G**; **Fig. 3, A, B, E, F, I, J**; **Fig. S1, G–H**; **Fig. S2, B–F**.
9. **In-silico protease cleavage-site prediction** (non-micrograph). PROSPER (Protease Specificity Prediction Server) applied to the cortactin sequence. **→ Fig. S3A**.
10. **General statistics.** GraphPad Prism (two-tailed Student's t test; one-way ANOVA with Bonferroni's multiple comparisons) — applied broadly across Figs. 1–5 and supplementary figures.

:::{admonition} Verbatim quotes
:class: note, dropdown
"Analysis of confocal images was performed using Imaris software (Bitplane, RRID:SCR_007370)."

"Image stacks of longitudinal half vessels were reconstructed in 3D and analyzed using Imaris software (Joulia et al., 2022). The MFI values of cortactin and CatG in venular ECs were measured based on the isosurface masking of PECAM1-positive areas representing junctions and cytoplasmic non-junctional regions."

"Recorded videos were analyzed using ImageJ software (NIH, Bethesda, MA, USA, RRID:SCR_003070)."
:::

- **Software:** Imaris (Bitplane), ImageJ (NIH), FlowJo Treestar V10, GraphPad Prism, Leica LIGHTNING deconvolution software, PROSPER. No version numbers given for any of these.
- **Code repository:** None found. Data Availability statement points only to the article and its supplemental material, with no code link.
- **Sample image data:** Not stated for images specifically. The Data Availability statement reads only: "All data are available in the published article and its online supplemental material" — a generic sentence with no mention of raw/original micrographs and no repository accession.
- **Based on prior methods:** Joulia et al., 2022 (3D reconstruction/Imaris workflow); Hoesel et al., 2005 (neutrophil depletion protocol); Schnoor et al., 2011 (intravital microscopy setup).

(jcb-202411196)=
## Covill-Cooke et al. — Mitochondrially tethered Mmm1 can function as a sole lipid transporter at ER–mitochondria contacts

Christian Covill-Cooke, Takashi Hirashima, Shin Kawano, Joe Ganellin, Andrew Moody, Sabine N.S. van Schie, Arun T. John Peter, Chika Horie Saito, Toshiya Endo, Benoît Kornmann — *J. Cell Biol.* 225(7), e202411196 (2026). [doi:10.1083/jcb.202411196](doi:10.1083/jcb.202411196)

1. **Colocalization frequency (Vps13-GFP with Mdm34-mCherry).** Thresholded puncta area vs. thresholded mitochondrial mass compared statistically by chi-squared test in GraphPad Prism. **→ Fig. 2, B and C.**
2. **Live-cell fluorescence acquisition.** UltraView IX81 Olympus spinning-disc confocal, Volocity acquisition software, 100× oil objective. Underlies **Fig. 2 (B, E)**; presumed (not explicitly re-stated) for **Fig. S1 (B–E)** and **Fig. S2**.
3. **Mitochondrial morphology / rescue-experiment imaging.** DeltaVision Elite (Cytiva) acquisition, SoftWoRx deconvolution, Fiji processing/analysis. **→ Fig. 4B**.
4. **Vps13-GFP/MDC-like foci in stationary phase.** DeltaVision MPX (Applied Precision), SoftWoRx deconvolution with manufacturer parameters. **→ Fig. S1D**.
5. **Predicted 3D structure of the Mmm1–Mdm10 heterodimer** (non-micrograph). AlphaFold 3 prediction, ChimeraX visualization. **→ Fig. 3B**; predicted-aligned-error plot **Fig. S3D**.
6. **Structure-based mutant design** (non-micrograph). Damietta-based design of a lipid-transport-deficient Mmm1 SMP-domain mutant. **→ Fig. 5C**.
7. **Cardiolipin/phospholipid quantification (TLC).** ³²P-labeled lipids detected by autoradiography (phosphor imaging plate + Typhoon FLA-7000 imaging analyzer).
   :::{note} Methods gap
   No densitometry/quantification software (e.g., ImageQuant) is named for converting the phosphor-imager scan into the reported band percentages. **→ Fig. 4, C and D.**
   :::
8. **Immunoblot protein levels of tethered constructs.** Odyssey DLx (LI-COR) scanner detection; no band-quantification software named. **→ Fig. 5D**; also underlies **Fig. S5, A–C**.

:::{admonition} Verbatim quotes
:class: note, dropdown
"Images were obtained using an UltraView IX81 Olympus spinning disc confocal microscope equipped with a 100× oil immersion objective lens (NA = 1.4). Image acquisition, using Volocity software, was carried out at room temperature."

"Deconvolution was performed using SoftWoRx software (Cytiva), and the acquired images were processed and analyzed with Fiji software."

"The percentage of cells showing colocalization (observed) was then compared with this expected value using a chi-squared test calculated in GraphPad Prism."
:::

- **Software:** Volocity, Fiji, SoftWoRx (Cytiva), GraphPad Prism, AlphaFold 3, ChimeraX, Damietta. No version numbers given for any imaging-analysis tool.
- **Code repository:** None found. Data Availability statement points only to the article and its supplemental material.
- **Sample image data:** Not stated for images specifically. The Data Availability statement reads only: "All data are available in the published article and its online supplemental material" — the same generic wording seen elsewhere in this issue, with no repository accession or explicit mention of raw images.
- **Based on prior methods:** Abramson et al., 2024 (AlphaFold 3); Pettersen et al., 2021 (ChimeraX); Grin et al., 2024 and Maksymenko et al., 2023 (Damietta mutation-design method); Hanson and Lester, 1980, Folch et al., 1957, and Vaden et al., 2005 (lipid extraction/TLC protocol, wet-lab not image analysis).

(jcb-202505012)=
## Petrova, Bernier-Latmani et al. — Eosinophils promote a second wave of postnatal smooth muscle differentiation in intestinal villi

Tatiana V. Petrova, Kelly de Korodi, Thea Berg, Tania Wyss, Yahya Mohammadzadeh, Lida Safazada, Kathleen Shah, Nicola L. Harris, Jeremiah Bernier-Latmani — *J. Cell Biol.* 225(7) (2026). [doi:10.1083/jcb.202505012](doi:10.1083/jcb.202505012)

:::{note} Reformatting note
This is a Europe PMC Funders Group author-manuscript version: Methods, figures/legends and References are relocated to the end of the document, and legends are headed "Figure N." rather than "Fig. N."
:::

1. **GFP+ SMC counts and villus-position distribution (lineage tracing).** Zeiss LSM 880 confocal, ZEN acquisition; Imaris/Fiji/Photoshop/Affinity Photo 2 for analysis. **→ Figure 1, F–G.**
2. **Eosinophil distance-from-base, density, and height.** Same confocal/analysis toolset as above. **→ Figure 2, B–D.**
3. **Cell–cell contact quantification from 3D volume EM.** Block-face SEM images collected and aligned in FIJI; segmentation and video generation via the TrakEM2 Fiji plugin. **→ Figure 2, E–F**; **Video 1**.
4. **Villus SMC area per villus area.** Confocal + Imaris/Fiji/Photoshop/Affinity Photo 2. **→ Figure 3D.**
5. **"Transition" and "star" cell counts per villus.** Same toolset. **→ Figure 3, I–J.**
6. **RNA-seq differential expression / GSEA (intestinal fibroblasts).** bcl2fastq v2.2 demultiplexing, kallisto v0.44.0 pseudo-alignment, R v4.2.2, tximport v1.26.1, SVA v3.46.0, DESeq2, clusterProfiler v4.6.2 GSEA, msigdbr v7.5.1, limma v3.50.3 (for re-analysis of two external GEO datasets). **→ Figure 4, B–F.**
7. **Transition-cell counts, CNN1+ SMC height, eosinophil density (TGFβ-blocking antibody experiment).** Confocal + Imaris/Fiji/Photoshop/Affinity Photo 2. **→ Figure 5, C–E.**
8. **CNN1+ SMC height, transition-cell/αSMA+ counts, villus area (Tgfbr2 conditional-knockout experiment).** Same toolset. **→ Figure 5, H–K.**
9. **%Area αSMA+ in ex-vivo fibroblast/eosinophil co-culture.** Same toolset. **→ Figure 5N.**
10. **General statistics.** GraphPad Prism 10/11 (two-tailed unpaired Student's t test; one-way ANOVA with Tukey's post hoc) — applied across Figures 1, 3, and 5.

:::{note} Methods gap — dropdown
:class: dropdown
Figure 4A's CD22+ eosinophil visualization ("masking CD22 by SIGLECF") is not attributed to any named software or step-by-step procedure beyond the general Imaris/Fiji/Photoshop/Affinity Photo 2 toolset. Villus-area measurements used as the denominator in several panels (e.g., Fig. 3D, Fig. 5K) are also never described as manual ROI tracing vs. automated segmentation.
:::

:::{admonition} Verbatim quotes
:class: note, dropdown
"Confocal images were obtained using a Zeiss LSM 880 microscope and ZEN acquisition software (Zeiss)... Images were analyzed using Imaris (Bitplane), Fiji (Schindelin et al., 2012), Photoshop (Adobe) and Affinity Photo 2 software."

"Series nearly aligned images were collected and aligned in the FIJI imaging software (www.fiji.sc). Segmentation of different cells and structures and video generation were carried out with FIJI software running the TrakEM2 plugin."
:::

- **Software:** Zeiss ZEN, Imaris (Bitplane), Fiji + TrakEM2, Photoshop (Adobe), Affinity Photo 2, GraphPad Prism 10/11, plus a versioned RNA-seq bioinformatics stack (bcl2fastq, kallisto, R, tximport, SVA, DESeq2, clusterProfiler, msigdbr, limma).
- **Code repository:** None found. Only GEO accession numbers (data, not code) are given.
- **Sample image data:** Not stated for images specifically. The RNA-seq datasets underlying Fig. 4 are publicly deposited in GEO (GSE33807, GSE236132, GSE289872), but the Data Availability statement is explicit that "all other data are available from the corresponding authors upon reasonable request" — imaging data falls under that generic on-request clause, not a public repository, and no raw-image repository is named anywhere in the text.
- **Based on prior methods:** Bernier-Latmani and Petrova, 2016 (whole-mount staining protocol); Schindelin et al., 2012 (Fiji); Bray et al., 2016 (kallisto); Love et al., 2014 (DESeq2); Subramanian et al., 2005 (GSEA); Ritchie et al., 2015 (limma); Spencer et al., 2014 (eosinophil morphological identification for EM).

(jcb-202506032)=
## Yang et al. — Light-based modulation of astrocytic calcium for regulation of organelle dynamics and morphogenesis

Lan Yang, Mikael Björklund, Cong Yi, Shue Chen, Zhi Hong — *J. Cell Biol.* 225(7), e202506032 (2026). [doi:10.1083/jcb.202506032](doi:10.1083/jcb.202506032)

1. **Ca2+ event detection/quantification** (amplitude dF/F, duration, frequency, spatial hotspots). Time-lapse stacks converted to 8-bit grayscale TIFF in ImageJ, then analyzed with the AQuA toolbox (GluSnFR preset). **→ Fig. 1, C–E, G, H**; **Fig. 2, A, B, H, I, K, L**; **Fig. S1B**.
2. **Organelle spatial distribution (movement distance/trajectory).** ImageJ Reslice tool + ROI Manager on process termini.
   :::{note} Figure mapping ambiguity
   No explicit figure citation is given in the Methods text; this step plausibly underlies the perinuclear/distal organelle-accumulation data in **Fig. 6, A–B**, but that link is inferred, not stated.
   :::
3. **Organelle mean velocity.** TrackMate (ImageJ plugin), parameters tuned per particle. **→ Fig. 4, B‴–I‴** (dynein/dynactin recruitment); **Fig. 5, B‴–I‴** (kinesin-1 recruitment); **Fig. S2, A–D**; **Fig. S5, A–D**.
4. **FRAP kymographs.** ImageJ Kymograph Builder tool. **→ Fig. 6, C–D** (LAMP1-mCherry and Rab5a bleaching).
5. **Process length/elongation.**
   :::{note} Methods gap
   No software or measurement procedure is described anywhere in the text for this morphometric step, though the figure legend reports quantitative process-length values at three timepoints. **→ Fig. 6, E–G.**
   :::
6. **Immunoblot band quantification (IP3R1/2/3 levels).** ImageJ gray-value measurement. **→ Fig. 2, E–F.**
7. **Illumination calibration** (not a downstream image-analysis output). Thorlabs S175C power-meter sensor + PM100USB, calibrated per filter channel — underlies the Local/Global illumination protocols used throughout Figs. 1–6.
8. **General statistics.** GraphPad Prism 10 — applied broadly across Figs. 1–6.

:::{admonition} Verbatim quotes
:class: note, dropdown
"Ca2+ imaging data were analyzed using the AQuA toolbox, following instructions by Wang et al. (2019). Specifically, time-lapse image stacks (500 frames per movie) were first converted into 8-bit grayscale TIFF format using ImageJ and then imported into AQuA."

"Mean organelle velocity (μm/s) was quantified using the TrackMate plugin in ImageJ, with key parameters (Diameter, Max. Distance, Max. Gap) adjusted according to the observed particles and their motility."
:::

- **Software:** ImageJ (Reslice, ROI Manager, Kymograph Builder, densitometry), TrackMate, AQuA ("AQuA nEvt" module), GraphPad Prism 10. No version numbers given except Prism 10.
- **Code repository:** None. Data Availability statement states only that data are "available from the corresponding authors upon request."
- **Sample image data:** Not stated for images specifically. The Data Availability statement reads: "Original data are available from the corresponding authors upon request" — a generic "data" statement, not an explicit reference to raw or original images, and no repository is named.
- **Based on prior methods:** Wang et al., 2019 (AQuA Ca2+-event-detection method, explicitly followed).

(jcb-202507177)=
## Appalabhotla et al. — Optogenetic control of PLC-γ1 activity directs cell motility

Ravikanth Appalabhotla, Priscila F. Siesser, Harrison Truscott, Nicole Hajicek, John Sondek, James E. Bear, Jason M. Haugh — *J. Cell Biol.* 225(7) (2026). [doi:10.1083/jcb.202507177](doi:10.1083/jcb.202507177)

:::{note} Reformatting note
HHS Public Access author-manuscript version; Supplementary Material section is a routine "refer to PMC" pointer, not a methods deferral.
:::

1. **HaloTag-JF646 membrane-recruitment kinetics** (fold-change, dissociation rate fit to exponential-plateau function). MATLAB/Python, manual thresholding for segmentation. **→ Fig. 1, E–G.**
2. **Protrusion/retraction pixel maps and front/rear area change.** MATLAB/Python custom pipeline. **→ Fig. 3, B–C**; also **Fig. 4B, D–E**; **Fig. 5C, E–G**; **Fig. 6C, E–G**; **Fig. 7C, E–G**; **Fig. 9B, D–F**.
3. **Cell-edge velocity maps.** MATLAB/Python, "constructed as previously described" (Welf et al., 2012; Johnson et al., 2015). **→ Fig. 5D**; **Fig. 6D**; **Fig. 7D**; **Fig. 9C**.
4. **Calcium (R-GECO) response quantification.**
   :::{note} Figure mapping ambiguity
   No figure legend in this text explicitly presents an R-GECO quantification panel, despite a dedicated Methods description of the analysis — no figure mapping could be found.
   :::
5. **DAG biosensor enrichment.** MATLAB/Python, normalized to pre-photoactivation baseline. **→ Fig. 2E.**
6. **PLC-γ1 phosphorylation (pTyr783) immunoblot densitometry.** Li-Cor Odyssey acquisition.
   :::{note} Methods gap
   No densitometry/quantification software (e.g., Image Studio) is named for converting the Odyssey scan into the reported band ratios. **→ Fig. 2B**; **Fig. 8C.**
   :::
7. **Phospholipase activity ([3H]inositol phosphate accumulation).** Beckman Coulter LS 6500 liquid scintillation counter — not itself image analysis. **→ Fig. 2C**; **Fig. 8D.**
8. **General statistics.** MATLAB built-in functions (t-tests, ANOVA with Tukey-Kramer post-hoc) — applied across Figs. 4E, 5G, 6G, 7G.

:::{admonition} Verbatim quotes
:class: note, dropdown
"Image analysis was performed using a combination of MATLAB (Mathworks; RRID:SCR_001622) and Python (RRID:SCR_008394). Fluorescent images were background subtracted and segmented via manual thresholding."

"Spatiotemporal maps of edge velocity were constructed as previously described (Welf et al., 2012; Johnson et al., 2015). Protruded/retracted pixels between consecutive frames were binned according to the aforementioned spatial reference and the sum of the pixel counts in each angular bin were converted to a velocity."
:::

- **Software:** MATLAB (RRID:SCR_001622), Python (RRID:SCR_008394), Li-Cor Odyssey System. No version numbers given.
- **Code repository:** None found. Data Availability statement offers data "upon request," no code link.
- **Sample image data:** Not stated for images specifically. The statement reads: "Data underlying the figures and supplemental material is unconditionally available upon request addressed to the corresponding authors" — generic wording, not an explicit reference to raw or original images, and no repository is named.
- **Based on prior methods:** Welf et al., 2012 and Johnson et al., 2015 (edge-velocity map construction); Waldo et al., 2010 (phospholipase-activity assay quantification).

(jcb-202508068)=
## Curtis et al. — Regulation of the cell wall integrity pathway at the contact site between mating partners in yeast

Erin R. Curtis, Aarshi Jain, Daniel J. Lew — *J. Cell Biol.* 225(7) (2026). [doi:10.1083/jcb.202508068](doi:10.1083/jcb.202508068)

:::{note} Reformatting note
HHS Public Access author-manuscript version; figures/legends relocated to the end of the document, headed "Figure N."
:::

1. **Mating-efficiency/outcome scoring** (fusion, dissipation, G1 arrest, budding, lysis). Manual visual scoring from time-lapse movies. **→ Figure 1B**; **Figure 3, E–F**; **Figure 5, B/D**; **Figure 6, C–D**; **Figure 8C.**
2. **Image denoising and drift correction** (preprocessing). ImageJ Hybrid 3D Median Filter Plugin (or NIS-Elements GA3 median filter for the alternate microscope) plus the HyperStackReg Fiji plugin. Applies broadly to all time-lapse figures.
   :::{note} Truncated code citation
   The HyperStackReg plugin's own DOI is printed twice in this manuscript, identically truncated as "[DOI.10.5281]" — the suffix after "10.5281" is missing/cut off in the source PDF itself, so the full Zenodo DOI is not recoverable from this document.
   :::
3. **Protein clustering parameter** (Bem1, Wsc1, Rom2, Pkc1 cortical clustering). A MATLAB-based GUI, "ROI_TOI_QUANT_V9" (developed by Denis Tsygankov). **→ Figure 1, D and F**; **Figure 2, B–C**; **Figure 4, C, E, F**; **Figure 6, A–B**; **Figure 7D.**
4. **Cortical fluorescence linescans.** Fiji Freehand Line Tool (3–5 px wide), exported to R/ggplot. **→ Figure 1, E, G–H**; **Figure 2, D–F**; **Figure 4, A–B, D**; **Figure 6, E–F**; **Figure 7C**; **Figure 8, A–B.**
5. **Kymographs** (Bem1/Pkc1 dynamics). Fiji Multi Plot function on linescans, visualized in R/ggplot. **→ Figure 1, G–H**; **Figure 2D**; **Figure 4, A–B, D**; **Figure 6, E–F**; **Figure 7C**; **Figure 8B.**
6. **Mean per-cell GFP fluorescence intensity.**
   :::{note} Methods gap
   No image-analysis software or segmentation method is described anywhere in the text for how per-cell GFP intensity was extracted from images (only the downstream Student's t-test is named). **→ Figure 3B.**
   :::
7. **General statistics.** R Stats package (Kolmogorov-Smirnov, chi-squared, Shapiro-Wilk tests) — applied across Figures 1B, 2C, 3(B, E, F), 5(B, D), 6(C, D), 8C.

:::{admonition} Verbatim quotes
:class: note, dropdown
"Images were denoised using the ImageJ Hybrid 3D Median Filter Plugin (2007) with drift correction completed using HyperStackReg plugin in Fiji, written by Ved Sharma [DOI.10.5281]. All images shown and analyzed are maximum intensity projections."

"Clustering parameter was measured using a MATLAB based GUI called ROI_TOI_QUANT_V9, developed by Denis Tsygankov (Lai et al., 2018)."
:::

- **Software:** MetaMorph 7.8, NIS-Elements/GA3 (Nikon), ImageJ Hybrid 3D Median Filter Plugin, Fiji + HyperStackReg, MATLAB (ROI_TOI_QUANT_V9), R (ggplot, ks.test, chisq.test).
- **Code repository:** None for the authors' own analysis code. Only a truncated third-party Zenodo DOI stub is given for the HyperStackReg plugin.
- **Sample image data:** Not stated for images specifically. The Data Availability statement reads: "The data generated in this study are available from the corresponding author upon reasonable request" — generic, with no repository and no explicit mention of raw images.
- **Based on prior methods:** Lai et al., 2018 (ROI_TOI_QUANT_V9 clustering-parameter method).

(jcb-202508117)=
## Bacher et al. — Divergent *Rickettsia* species exhibit distinct mechanisms of actin-based motility

Meghan C. Bacher, Julie E. Choe, Jiawen Jiang, Joanna M. Idrovo, Joshua T. Del Mundo, Michal Hammel, Matthew D. Welch — *J. Cell Biol.* 225(7) (2026). [doi:10.1083/jcb.202508117](doi:10.1083/jcb.202508117)

:::{note} Reformatting note
HHS Public Access author-manuscript version.
:::

1. **Pyrene actin-polymerization kinetics.** Tecan Infinite F200 Pro + Magellan v7.1; baseline-corrected/graphed in Prism 10.3.1. **→ Fig. 2A**; **Fig. S4, A–C**; **Fig. 3C.**
2. **Maximum-slope (nucleation-rate) calculation.** Prism 10.3.1 first-derivative smoothing; normalized in Excel. **→ Fig. 3B.**
3. **Fluorescence anisotropy binding assay** (Kd for G-actin). Tecan + Magellan v7.1; Hill-equation fit in Prism 11. **→ Fig. S5A.**
4. **TIRF barbed-end elongation rate.** NIS Elements acquisition (Nikon Ti Eclipse/iLas2 TIRF); manual barbed-end tracing in ImageJ2/Fiji v2.9.0/1.53t; graphed in Prism 10.3.1. **→ Fig. 2B.**
5. **Sequence alignment/domain-motif analysis** (non-micrograph). Geneious 2025.0.3/2026.0.1 (MUSCLE); InterPro. **→ Fig. 1A**; **Fig. 1B**; **Fig. S1.**
6. **Protein structure prediction** (non-micrograph). AlphaFold3 server. **→ Fig. 1B**; **Fig. S2A**; **Fig. 4B** (PAE matrices).
7. **SEC-SAXS data reduction/ensemble modeling** (non-micrograph). RAW (Guinier Rg), BilboMD (AlphaFold3-PAE-restrained rigid-body ensembles), FoXS/MultiFoXS (curve fitting/2-state selection). **→ Fig. 4, A, C, D.**
8. **Fixed-cell confocal quantification** (bacteria counts, actin-tail frequency, RickA/Sca2/6 puncta). MetaMorph 7.8.2.0 acquisition (Nikon Ti Eclipse/Yokogawa CSU-X1); ImageJ2/Fiji v2.9.0/1.53t max-intensity projection; manual counts plotted in Prism 10.3.1. **→ Fig. 5, A–B**; **Fig. 6, A–C**; **Fig. 7, A–B.**
9. **Lattice-SIM imaging + deconvolution** (Sca2 ortholog surface localization). Zeiss Elyra 7 LSIM, Zen Black acquisition/SIM processing, Huygens Professional v24.10 (CMLE, 0.01% confidence) deconvolution. **→ Fig. 8A**; **Fig. 8E.**
10. **3D surface morphometry** (Sca2 ortholog surface area, sphericity, overlapped volume). Imaris 10.2. **→ Fig. 8, B–D.**
11. **Actin-tail intensity line-scan analysis.** ImageJ2/Fiji, max-intensity projection, manual 1.25 μm perpendicular line 0.5 μm from bacterial pole; plotted in Prism 10.3.1. **→ Fig. 8, E–F.**
12. **Live-cell motility tracking** (bacterial speed). ImageJ2/Fiji "Manual Tracking" plugin, 1 min at 5 s intervals; plotted in Prism 10.3.1. **→ Fig. 9, A and C.**
13. **Motility efficiency (ΔD/d).** X/Y coordinates from tracking; distance formula in Excel; plotted in Prism 10.3.1. **→ Fig. 9B.**
14. **General statistics.** Prism 10.3.1/11 (two-way/one-way ANOVA with Tukey's, Welch's t-test, Kruskal-Wallis) — applied across Figs. 2B, 3B, 5, 6B–C, 7B, 8B–D, 9A–B.

:::{note} Methods gaps — dropdown
:class: dropdown
No software is named for rendering the overlaid motility-trace plot in Fig. 9C (only the underlying ImageJ2/Fiji tracking is described). No software is named for producing the domain-architecture cartoons in Fig. 1, A–B. No specific tool is named for annotating the PAE-matrix confidence boxes in Fig. 4B beyond "AlphaFold3 server."
:::

:::{admonition} Verbatim quotes
:class: note, dropdown
"Elongation rate was determined over the course of 300 s by manually tracing the barbed ends (fast growing end with visually stable attachment point) of each filament 60 frames apart in ImageJ2/Fiji (v2.9.0/1.53t, RRID:SCR_002285) and graphed in Prism 10.3.1."

"To quantify and compare Sca2 ortholog localization and coverage of the R. parkeri versus R. bellii surface, deconvolved images stacks were analyzed using Imaris 10.2 (Oxford Instruments, RRID:SCR_007370). Separate surfaces were created for bacteria and Sca2 ortholog to generate area..., sphericity..., and overlapped volume... values used for quantifying Sca2 ortholog coverage of Rickettsia."
:::

- **Software:** Magellan v7.1, GraphPad Prism 10.3.1/11, Microsoft Excel, ImageJ2/Fiji v2.9.0/1.53t (RRID:SCR_002285), ImageJ "Manual Tracking" plugin, NIS Elements, MetaMorph 7.8.2.0, Zen Black, Huygens Professional v24.10, Imaris 10.2, Geneious 2025.0.3/2026.0.1, InterPro, AlphaFold3 server, RAW/FoXS/MultiFoXS/BilboMD.
- **Code repository:** None found. Data Availability statement points only to a Supplementary Dataset S1 (data, not code).
- **Sample image data:** Not stated for images specifically. The statement reads: "Data are underlying Figures 2, 3, 5, 6, 7, 8, 9, and S5 are included in Supplementary Dataset S1" — this appears to be a numeric source-data file (the quantifications behind those panels), and nothing in the text states that raw or original micrographs themselves are included or deposited.
- **Based on prior methods:** Blum et al., 2024 (InterPro); Abramson et al., 2024 (AlphaFold3); Hopkins et al., 2017 (RAW); Pelikan et al., 2009 (BilboMD); Schneidman-Duhovny et al., 2013 and 2016 (FoXS/MultiFoXS); Rambo and Tainer, 2013; Svergun, 1992; Schindelin et al., 2012 (ImageJ2/Fiji, general software citation).

(jcb-202509040)=
## Chouhan et al. — Arl8b inactivates the Rab11a recycling pathway to promote LAMP1 sorting and lysosome biogenesis

Priya Chouhan, Yogita Phogat, Kshitiz Walia, Saikat Debnath, Sandeep Choubey, Medha Gupta, Amit Tuli, Mahak Sharma — *J. Cell Biol.* 225(7), e202509040 (2026). [doi:10.1083/jcb.202509040](doi:10.1083/jcb.202509040)

1. **Colocalization (Manders' M1/M2).** JaCoP plugin in ImageJ, manual thresholding after channel splitting — used for a large number of marker-pair combinations. **→ Fig. 1G**; **Fig. 2, B, D, E**; **Fig. 3B**; **Fig. 4, B, D, F**; **Fig. 6, C, E, F**; **Fig. 7, B, D**; **Fig. 8, F, I**; **Fig. S1, J, L, N, P**; **Fig. S2, C, E, G**; **Fig. S3, C, F, H, K**; **Fig. S5A.**
2. **Colocalization (Pearson's PCC)** for direct-binder pairs. Same JaCoP/ImageJ pipeline. **→ Fig. 1J**; **Fig. 6B.**
3. **Intensity line-scan profiles.** ImageJ "RGB plot profile" — used across many colocalization figures (Figs. 1–4, 6, 7, S1–S3) without a single itemized panel list in Methods.
4. **p62 punctum counts.** Fiji manual threshold + Analyze Particles. **→ Fig. 9E.**
5. **Perinuclear index (lysosome distribution).** Fiji freehand ROI + "Clear Outside," 5 μm ROI expansion. **→ Fig. 8B.**
6. **Corrected total cell fluorescence (CTCF).** ImageJ "Measure." **→ Fig. 8D** (cathepsin D); **Fig. 9C** (EGFR); **Fig. 3E** (surface-recycled LAMP1 ratio).
7. **Mean lysosome number per cell.** Custom Python pipeline. **→ Fig. S5G.**
8. **Lysosomal area (peripheral vs. perinuclear).** Custom Python + OpenCV contour detection; Delaunay-triangulation/alpha-shape boundary (α = 0.02). **→ Fig. S5H.**
9. **Ripley's K spatial-clustering analysis.** OpenCV centroid extraction + custom K(r) code. **→ Fig. S5I.**
10. **Diffusion-exponent analysis.** Custom pipeline with the TrackPy particle-tracking library (search range 9 px, memory 5 frames, min. track length 20 frames). **→ Fig. S5J.**
11. **Flow cytometry** (surface LAMP1/LAMP2/EGFR MFI). BD FACSAria Fusion, FACSDiva v8.0.1, FlowJo v10.0.1. Applies broadly (e.g., **Fig. 1, A–D**; **Fig. S1**; **Fig. S3**; **Fig. S5, C–D**; **Fig. 9A**).
12. **Immuno-EM vesicle diameter.** Fiji Line tool. **→ Fig. S5F.**
13. **Western blot densitometry.** ImageJ. **→ Fig. 8G** (cathepsin D); **Fig. S5B** (TBC1D9B).
14. **General statistics.** GraphPad Prism 8.0 — applied across essentially all quantitative panels.

:::{note} Methods gaps — dropdown
:class: dropdown
AlphaFold3 structural modeling (Fig. 5A, F; Fig. S4C) and Chimera visualization have no dedicated Methods subsection — mentioned only in Results/legend text. ConSurf conservation scoring (Fig. S4E) and AlphaMissense pathogenicity scoring (Table S1) are likewise cited only in Results text with no Methods description of parameters or version used.
:::

:::{admonition} Verbatim quotes
:class: note, dropdown
"For colocalization analysis, images were processed using Just Another Colocalization (JaCoP) Plugin in ImageJ."

"To characterize lysosomal diffusion within different spatial regions of HeLa cells, we developed a custom image analysis pipeline that segments cellular regions, extracts lysosome coordinates, and tracks their motion using the open-source TrackPy library (https://zenodo.org/records/60550) (Crocker and Grier, 1996)."
:::

- **Software:** ImageJ (JaCoP, RGB Plot Profile, Measure/Analyze, densitometry), Fiji (Analyze Particles, ROI tools, Line tool), Adobe Photoshop CS 2024, Zeiss ZEN 2012/Zen Black, Olympus CellSens, Python/OpenCV/TrackPy (custom pipeline), BD FACSDiva v8.0.1, FlowJo v10.0.1, GraphPad Prism 8.0.
- **Code repository:** No repository for the authors' own custom Python code. Two third-party library citation links are given in Methods: OpenCV (`https://github.com/opencv/opencv/wiki/CiteOpenCV`) and TrackPy (`https://zenodo.org/records/60550`).
- **Sample image data:** Not stated for images specifically. The Data Availability statement reads: "All relevant data supporting the findings of the study are included in the manuscript and supplementary material" — generic, with no repository accession and no explicit mention of raw or original images.
- **Based on prior methods:** Ito, 2015 (Delaunay triangulation); Edelsbrunner et al., 2003 (alpha-shape algorithm); Crocker and Grier, 1996 (TrackPy particle-linking algorithm); Dixon, 2002 and Ripley, 1977 (Ripley's K statistical method).

(jcb-202511182)=
## Das et al. — NASP functions in the cytoplasm to prevent histone H3 aggregation during early embryogenesis

Mohit Das, Eli Coronado-Chavez, Anusha D. Bhatt, Reyhaneh Tirgar, Amanda A. Amodeo, Jared T. Nordman — *J. Cell Biol.* 225(7), e202511182 (2026). [doi:10.1083/jcb.202511182](doi:10.1083/jcb.202511182)

1. **H3.2/H3.3 nuclear import rate.** Zeiss LSM 980 + Airyscan-2 live imaging, ZEN 3.3 (blue edition) acquisition/reconstruction; nuclear/cytoplasmic segmentation via Ilastik pixel + object classification; import-rate slope by linear regression. **→ Fig. 1, A–C** (H3.2) and **Fig. 1, D–F** (H3.3); normalized versions **Fig. S1, A–F.**
2. **Simulated H3.2 import at 50% concentration** (Michaelis-Menten model; software not named). **→ Fig. 1C**; **Fig. S1, C, G, H.**
3. **Nuclear export (photoconversion decay).** Zeiss LSM 980/Airyscan-2, ZEN Blue interactive bleaching mode, 405 nm photoconversion. **→ Fig. 2, B–C**; unnormalized **Fig. S1, J–K.**
4. **Mitotic chromatin intensity.** Sum-projection in FIJI; Ilastik segmentation of chromatin/cytoplasm; pseudo-colored heat maps via FIJI's Thermal LUT. **→ Fig. 2, D–E** (H3.2) and **Fig. 2, F–G** (H3.3).
5. **NASP-Dendra2 vs. H3.2-Dendra2 relative import kinetics.** Same live-imaging/Ilastik/FIJI pipeline. **→ Fig. 3, A–D**; non-chromatin-subtracted version **Fig. S2C.**
6. **Cell-cycle duration** (metaphase-to-metaphase timing).
   :::{note} Methods gap
   The operational definition is stated, but no software/tool is named for identifying metaphase timepoints in the time-lapse series. **→ Fig. S1I.**
   :::
7. **Photobleaching control.**
   :::{note} Methods gap
   Described narratively only ("continuously imaged area... compared with the outside area and the unimaged embryo") — no software, ROI tool, or quantitative metric is named, and no figure depicts this comparison.
   :::
8. **Western blot densitometry** (H3, H2B, NASP levels). Bio-Rad ChemiDoc MP imaging, Bio-Rad Image Lab software. **→ Fig. 4, B and D**; **Fig. 5, E and G**; **Fig. S4, B and D.**
9. **Aggregate-isolation assay quantification** (SDS-PAGE/western, protein-aggregate fraction ratios). Differential/ultracentrifugation isolation, Bio-Rad Image Lab densitometry. **→ Fig. 5, B–G**; **Fig. S4, A–E**; **Fig. S5, A–B.**
10. **General statistics** (two-way/one-way ANOVA, paired t-test, linear regression). No statistics software package (e.g., GraphPad Prism) is named anywhere in the text — a consistent minor gap across the whole paper.

:::{admonition} Verbatim quotes
:class: note, dropdown
"The z-stack for the time point of metaphase chromatin for each nuclear cycle was sum projected in FIJI. The chromatin and cytoplasm of these images were then segmented using the pixel classification + object classification features on Ilastik. A CSV file was exported containing the total intensity."

"To determine potential photobleaching during image acquisition, two embryos of the same age were imaged from the interphase nucleus and metaphase chromatin for NC10... These comparisons showed minimal photobleaching, and therefore, no numerical photobleaching corrections were applied to our data."
:::

- **Software:** ZEN 3.3 (blue edition), ZEN Blue, FIJI, Ilastik, Bio-Rad Image Lab. No version numbers given for any of these.
- **Code repository:** None found. Data Availability statement offers raw/processed images "upon reasonable request," no code link.
- **Sample image data:** On request only — this is the one article in the issue whose Data Availability statement explicitly names images: "All raw and processed images are available upon reasonable request." This is not a public deposit, but it is a more specific commitment about image data than the generic "data available on request" wording used elsewhere in this issue.
- **Based on prior methods:** Shindo and Amodeo, 2019 (import-rate slope method); Shindo and Amodeo, 2021 (Michaelis-Menten import-simulation model); Chen et al., 2024 (aggregate-isolation protocol, adapted).

(jcb-202512111)=
## Sakers et al. — Neuroligin-2 is ubiquitinated by Nedd4l to control developmental astrocyte morphogenesis

Kristina Sakers, Juan J. Ramirez, Nimrod Elazar, Leykashree Nagendren, Erik Soderblom, Cagla Eroglu — *J. Cell Biol.* 225(7) (2026). [doi:10.1083/jcb.202512111](doi:10.1083/jcb.202512111)

:::{note} Reformatting note
HHS Public Access author-manuscript version: Methods and figure legends ("Figure N.") are relocated to the end of the document, after References.
:::

1. **In-vitro dendritic/process branching complexity (Sholl analysis).** FIJI v1.53c + Sholl Analysis plugin v4.0.1; results analyzed via a custom in-house R (v4.0.0+) pipeline. **→ Fig. 1, D and F**; **Fig. 2, C, F, J**; **Fig. 5B**; **Fig. 8B**; comparison panel **Fig. S1, C–D.**
2. **In-vivo 3D morphology reconstruction and territory volume.** Imaris v9.9 filament tracer (3D reconstruction), Convex Hull function (territory volume), two custom extensions for 3D Sholl; statistics via a custom R script. **→ Fig. 5, D–F**; **Fig. 8, C–F.**
3. **Synapse colocalization/density** (excitatory Bassoon/PSD95; inhibitory Bassoon/Gephyrin). SynBot run within FIJI, manual thresholding; a custom FIJI macro crops the binarized output and applies an astrocyte ROI. **→ Fig. S5, C–D** (no main-text figure panel was found for this step).
4. **CRISPR editing-efficiency quantification** (GFP-reporter band intensity). ImageJ densitometry, normalized to GAPDH. **→ Fig. S1F.**
5. **Co-IP band quantification** (Nedd4l–Neuroligin binding). ImageJ densitometry, normalized to IP bait band; paired Student's t-test. **→ Fig. 6, C, E, G, I.**
6. **Ubiquitination-assay quantification.** Densitometry (consistent with the ImageJ workflow used elsewhere), paired Student's t-test. **→ Fig. 7, A–B.**
7. **Cycloheximide-chase degradation kinetics.**
   :::{note} Methods gap
   The two-way ANOVA statistics are named, but the specific software used to quantify band intensity from these SDS-PAGE blots is not explicitly stated for this subsection (unlike the Immunoprecipitation/Western-blotting subsections, which name ImageJ explicitly). **→ Fig. 7, C–F.**
   :::
8. **iBioID immunoblot densitometry** (streptavidin/biotinylation signal). ImageJ v1.54f.
   :::{note} Figure mapping ambiguity
   Fig. 3E is described only as a qualitative representative blot in the legend; no explicit quantification panel tied to this densitometry could be found.
   :::
9. **GO-term enrichment analysis** (iBioID interactome, non-micrograph). R package clusterProfiler v4.6.2, `simplify` function. **→ Fig. 4, C–D**; full data in Dataset S2.
10. **Mass-spectrometry interactome statistics** (non-micrograph). Proteome Discoverer 2.3 (Minora Feature Detector), Mascot Distiller/Server v2.5. **→ Fig. 3F**; **Fig. 4, A, B, E.**

:::{admonition} Verbatim quotes
:class: note, dropdown
"Sholl Analysis was performed in FIJI (NIH, v1.53c) using the Sholl Analysis plug-in (v4.0.1)... Resulting values were then analyzed in R (v4.0.0 and above) using an in-home pipeline which can be found here: https://github.com/Eroglu-Lab/In-Vitro-Sholl."

"We used SynBot (Savage et al., 2024) (https://github.com/Eroglu-Lab/Syn_Bot) in FIJI to quantify the colocalization of Bassoon... and Psd95... or Bassoon and Gephyrin... synapses for the entire image using manual thresholding. Using a custom macro in FIJI (https://github.com/Eroglu-Lab/Sakers-et-al-2025), we then cropped the binarized synaptic output images to draw an ROI around the labeled astrocyte and quantify the number of synaptic puncta within and outside the ROI."

"Imaris v9.9 (Bitplane) was used to reconstruct images using the filament tracer in 3D. We used two custom extensions to quantify filament complexity (3D Sholl analysis) every 5μm from the cell nucleus... A linear mixed model followed by Dunnett's post-hoc test was used to analyze the 3D Sholl data using a custom R script found at: https://github.com/Eroglu-Lab/In-vivo-Sholl-Analysis. The whole astrocyte territory volume was calculated using the Convex Hull function in Imaris on the cell surface."
:::

- **Software:** FIJI v1.53c + Sholl Analysis plugin v4.0.1, ImageJ v1.54f, Imaris v9.9, SynBot, R (v4.0.0+, clusterProfiler v4.6.2, ggplot2), Proteome Discoverer 2.3, Mascot Distiller/Server v2.5, CRISPOR.
- **Sample image data:** Yes — the only article in this issue that publicly deposits raw/original images: the Data availability statement states "all original images can be accessed via Duke Digital Repository: `https://doi.org/10.7924/r4r500`" (also expressible as [doi:10.7924/r4r500](doi:10.7924/r4r500)), in addition to mass-spectrometry proteomics data deposited to ProteomeXchange/PRIDE (dataset PXD049185).
- **Code repository:** Four GitHub repositories, all under the Eroglu-Lab organization — `In-Vitro-Sholl` (Sholl-analysis R pipeline), `Syn_Bot` (synapse-quantification tool), `Sakers-et-al-2025` (custom FIJI macro for this paper), and `In-vivo-Sholl-Analysis` (3D Sholl/territory-volume R script). This is a notable contrast with the rest of this issue's articles, nearly all of which provide no code repository at all.
- **Based on prior methods:** Wilson et al., 2017 (Sholl statistical approach); Savage et al., 2024 (SynBot); Baldwin et al., 2021 and Stogsdill et al., 2017 (PALE technique / territory-volume finding); Concordet and Haeussler, 2018 (CRISPOR); Wu et al., 2021 (clusterProfiler).

(jcb-202602088)=
## Williams et al. — Chromosome segregation synchrony in *S. pombe* is noise limited and arises without positive feedback

Wendi Williams, Kien Phan, Jing Chen, Stefan Legewie, Julia Kamenz, Silke Hauf — *J. Cell Biol.* 225(7), e202602088 (2026). [doi:10.1083/jcb.202602088](doi:10.1083/jcb.202602088)

1. **Manual scoring of sister-chromatid separation timing.** Visual inspection of time-lapse recordings, confirmed against tracked trajectories. **→ Fig. 1, C–D**; underlies the Δt distributions in **Fig. 1, E, F, H**; **Fig. 2, A, C, E**; **Fig. 3A**; **Fig. 4, C–D**; and corresponding **Fig. S1–S4** panels.
2. **Kymograph assembly.** Custom MATLAB script (RRID:SCR_001622), contrast-enhanced. **→ Fig. 1D**; **Fig. 3, B and F**; **Fig. S1, F, I**; **Fig. S2, B–D**; **Fig. S4, D, K.**
3. **Centromere-distance tracking kinetics.** TrackMate (in ImageJ, RRID:SCR_003070) with manual corrections. **→ Fig. 1D validation**; **Fig. S1E**; distance-vs-time plots in **Fig. 2, B, D, F**; **Fig. S2, E–F**; **Fig. S4B.**
4. **Post-processing/statistical display of tracked trajectories** (population mean/SD, smoothed splines). Custom MATLAB and R scripts (generalized additive models with cubic regression splines). **→ Fig. 2, B, D, F**; **Fig. S2, E–F**; **Fig. S3, E–F**; **Fig. S4B.**
5. **Securin-GFP degradation kinetics.** ROI defined by TetR-tdTomato nuclear signal, background-subtracted; local slope via 7-point-smoothed-spline derivative.
   :::{note} Methods gap
   The specific software used for this ROI/intensity extraction and derivative calculation is not itemized beyond the generic "custom MATLAB and R scripts" statement used elsewhere in Methods. **→ Fig. 3E**; **Fig. S1, A–D**; **Fig. S4, E, H, J.**
   :::
6. **Deconvolution** (preprocessing). softWoRx software, applied "when necessary" — no figure mapping given.
7. **General statistics** (Gaussian fits, Kolmogorov-Smirnov, one-sample t-test). R's `dnorm`. Applied across Figs. 1E–F, 1H, 2A, 2C, 2E, 3A, 3C–D, 4C–D and corresponding supplementary figures; results tabulated in Table S1.
8. **Stochastic model of separase release/cohesin cleavage** (non-imaging, fitted to the image-derived Δt data). Python (SciPy `differential_evolution`, L-BFGS-B refinement), modified Gillespie algorithm, Earth Mover's Distance goodness-of-fit, fivefold cross-validation. **→ Fig. 4B**; **Fig. S4G**; **Fig. 5, A–F**; **Table S3–S4.**

:::{note} AI-assisted code disclosure
:class: note
The paper discloses: "Stochastic modeling, optimization, and analysis scripts were developed using Google Gemini 3.1 Pro (Antigravity IDE)." This applies to the non-imaging stochastic-model code (item 8), not to the primary image-analysis pipeline (kymographs/TrackMate/GFP-intensity quantification).
:::

:::{admonition} Verbatim quotes
:class: note, dropdown
"Images were deconvolved using softWoRx software when necessary to improve signal clarity. The time point of sister chromatid separation was scored manually and was defined as the last time point at which sister chromatids moved coordinately or convergently before moving consistently toward opposing spindle poles."

"Kymographs were assembled using a custom MATLAB (RRID:SCR_001622) script, and the contrast was enhanced for easier visualization of the separation events. Trackmate (Ershov et al., 2022; Tinevez et al., 2017) with manual corrections was used in ImageJ (RRID:SCR_003070) for tracking the kinetics of sister chromatid separation, and custom MATLAB (RRID:SCR_001622) and R (RRID:SCR_001905) scripts were used to further process and display the data."
:::

- **Software:** softWoRx, MATLAB (RRID:SCR_001622), TrackMate (in ImageJ, RRID:SCR_003070), R (RRID:SCR_001905), Python/SciPy (`differential_evolution`), Google Gemini 3.1 Pro (AI-assisted code generation, non-imaging code only). No version numbers given for the imaging-analysis tools (only RRIDs).
- **Sample image data:** Not stated for images specifically. The statement reads: "The data underlying Δt distributions in Figs. 1, 2, 3, 4, and 5 are openly available in Zenodo... at `https://doi.org/10.5281/zenodo.19462276`" — this is derived timing/measurement data, and nothing in the text states that the underlying raw microscopy movies/kymograph source images are themselves included in that deposit.
- **Code repository:** Two Zenodo DOIs — `10.5281/zenodo.19462276` (the Δt/data underlying Figs. 1–5) and `10.5281/zenodo.19434950`, explicitly described as "the code for the stochastic model" — i.e., the non-imaging Gillespie-simulation/parameter-fitting code, not the image-analysis (kymograph/TrackMate/MATLAB/R) scripts, for which no repository is given.
- **Based on prior methods:** Ershov et al., 2022 and Tinevez et al., 2017 (TrackMate); Gillespie, 1976/1977 (stochastic simulation algorithm); Storn and Price, 1997 (differential evolution); Byrd et al., 1995 (L-BFGS-B); Bazán et al., 2019 (Earth Mover's Distance as goodness-of-fit).

:::{warning} Caveats
**Supplementary-methods-deferral check.** Every one of the 12 articles in this issue was explicitly checked for genuine deferral of image-analysis methodological detail to a separate supplementary Materials and Methods document not included in the main-text PDF (as distinct from routine pointers to a supplementary figure, movie, or table, or generic data-availability boilerplate). **None of the 12 articles defer any image-analysis step's methodological detail this way** — every image-analysis procedure found is fully described within each article's own main-text Methods section. (One article, Yeh et al., 202306071, does point a specific *result panel* — not the method description itself — to a supplementary figure not included in this PDF, Figure S2D–E and S4A–B; this is a figure-location gap, not a methods-deferral, and is flagged inline in that section.)

**Code-repository landscape — a departure from prior issues.** Unlike both previously surveyed JCS issues, where no article provided a code repository, this JCB issue includes several: Sakers et al. (202512111) link four GitHub repositories under the Eroglu-Lab organization covering Sholl analysis (2D and 3D), SynBot synapse quantification, and a paper-specific FIJI macro; Williams et al. (202602088) provide two Zenodo DOIs, though only one of them (`zenodo.19434950`) is code, and that code is for the non-imaging stochastic model rather than the image-analysis pipeline itself — no repository is given for their kymograph/TrackMate/MATLAB/R image-analysis scripts; Chouhan et al. (202509040) and Bacher et al. (202508117, via ImageJ2/Fiji's own citation) provide citation links to third-party open-source libraries they used (OpenCV, TrackPy) rather than their own analysis code; and Curtis et al. (202508068) cite a truncated, unresolvable Zenodo DOI stub ("[DOI.10.5281]", cut off in the source PDF itself) for a third-party Fiji plugin (HyperStackReg), not their own code. The remaining seven articles provide no code repository of any kind.

**Version-number gaps.** Several articles give thorough version numbers for imaging software (notably Bacher et al. 202508117 and Sakers et al. 202512111), but many others name key tools — Imaris, ImageJ, Fiji, GraphPad Prism, MATLAB, R — without any version number at all (e.g., Guerrero-Fonseca et al. 202410019; Covill-Cooke et al. 202411196; Das et al. 202511182; most of Chouhan et al. 202509040 and Williams et al. 202602088, which give RRIDs but not versions).

**"Based on prior methods" scope.** A citation is only listed as a prior-methods basis for a given step when the text ties that specific image-analysis procedure to a prior paper — general reagent, antibody, strain-construction, or biological-rationale citations elsewhere in an article are not counted as image-analysis method citations, even when they appear in the same paragraph.

**Figure-mapping and measurement-attribution ambiguities.** Several steps could not be tied to a specific main-text figure panel despite being described in Methods — these are flagged inline with a "Figure mapping ambiguity" note in each affected article's section (e.g., the R-GECO quantification in Appalabhotla et al. 202507177; two organelle-quantification steps in Yang et al. 202506032 and Yeh et al. 202306071 whose only figure citation points to a supplementary figure not included in this PDF).

**Sample image data availability.** Each article was also checked for whether it makes its underlying raw/original image data available, as a distinct question from code availability. Across the 12 articles: **1 article (Sakers et al., 202512111)** explicitly and publicly deposits raw/original images, at the Duke Digital Repository (doi:10.7924/r4r500); **1 article (Das et al., 202511182)** explicitly states that raw and processed images exist and are available, but only "upon reasonable request," not as a public deposit; **9 articles** (Guerrero-Fonseca 202410019; Covill-Cooke 202411196; Petrova 202505012; Yang 202506032; Appalabhotla 202507177; Curtis 202508068; Bacher 202508117; Chouhan 202509040; Williams 202602088) give only generic data-availability language ("available in the article and its supplemental material," "available upon request," or a numeric/derived-data deposit) that never specifically names raw or original images, so no claim about image-data availability can be made for them beyond that generic wording; and **1 article (Yeh et al., 202306071)** contains no Data Availability statement at all in this PDF. This check is independent of, and should not be conflated with, the code-repository landscape described above — an article can (and in this issue's case, mostly does) provide neither, provide one without the other, or in Sakers et al.'s case, provide both.

**Distinct "Methods gaps" (not supplementary deferrals).** Multiple articles have at least one image-analysis step that is used to produce a reported figure but has no described method or software named anywhere in the available text — these are genuine gaps in methodological reporting, not deferrals to another document, and are flagged inline with a "Methods gap" note: the spindle/centrosome-geometry and colocalization-description steps in Yeh et al. (202306071); the IVM flux/velocity/adhesion tracking step in Guerrero-Fonseca et al. (202410019); the thresholding-software and lipid/immunoblot-densitometry steps in Covill-Cooke et al. (202411196); the process-length measurement in Yang et al. (202506032); the immunoblot-densitometry software in Appalabhotla et al. (202507177); the per-cell GFP-intensity measurement in Curtis et al. (202508068); the AlphaFold3/Chimera/ConSurf/AlphaMissense steps lacking Methods description in Chouhan et al. (202509040); the cell-cycle-duration and photobleaching-control steps in Das et al. (202511182); the cycloheximide-chase densitometry software in Sakers et al. (202512111); and the securin-GFP-kinetics software attribution in Williams et al. (202602088).
:::
