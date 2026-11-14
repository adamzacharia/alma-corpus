---
name: alma-analysis-software-map
description: "Router from an ALMA analysis job (imaging, self-calibration, array combination, continuum subtraction, moment maps, disk or galaxy cube kinematics, uv-plane fitting, radial profiles, source and line finding, dendrograms and cores, GMC decomposition, line identification, LTE and non-LTE modelling, radiative transfer, chemistry, SED fitting, lensing, stacking, MCMC and nested sampling, censored regression, astrometric alignment) to the established package ALMA papers use for it, with paper counts, the setting that matters, when to prefer an alternative, and the technique skill to read next. Use before writing any fitter, source finder, sampler or radiative-transfer code, when choosing a tool for a reproduction, or when checking which software a paper's result depends on. Built from 3422 ALMA papers (2012-2026)."
---

# Analysis software map (job to established package)

ALMA papers almost never write their own fitter, finder or radiative-transfer code: they use a small set of
community packages, and CASA alone is named in 2638 of the 3422 papers here (pack aggregate "Packages by number
of papers"). Reimplementing a standard fitter is the wrong default. In CosmicCoder agent runs a naive home-made
cube kinematics fitter gave a worse measurement than the paper's established package. The second mistake that
matters: picking a package by name without the setting and input files that decide its answer.

> **Count convention.** "P" = distinct papers naming the package in their software inventory (pack aggregate
> "Packages by number of papers", all 3422 members). "S" = mentions in one technique's matched analysis steps
> (pack aggregate "Software named in each technique's matched steps"; a paper can add more than one). Spellings
> are counted separately (3dbarolo 65 P and 3d-barolo 18 P); I add them only where I say so. Both undercount
> tools used without being named. The full per-package table is `references/packages.md`.

## Agent checklist

1. Before writing a fitter, finder, sampler or model code, look the job up in the router below and use the
   established package. Write your own code only for glue (unit conversions, plotting, a closed-form formula).
2. Reproducing a paper: use the software and version the paper names, even if it is old. If it names none,
   use the most-named package for that job in the router, and write down that you assumed it.
3. Imaging default: CASA `tclean` (380 P; 537 S in imaging-choices) with Briggs robust 0.5, the median robust
   in every major field (stats README, 3498 cards). Masking: `auto-multithresh` (12 P) is the common automatic
   choice. Record its thresholds even when you use the defaults (2024AJ....168..151J, 2024ApJ...966...32E).
4. Sampler default: emcee (410 P, the most-named fitting package). Switch to nested sampling (dynesty 34 P;
   MultiNest 22 P + PyMultiNest 9 P) when you need a Bayesian evidence for model selection (2013MNRAS.430.2454L,
   2019A&A...628A.100D).
5. Main fork: fit the model in the domain where the data live. For visibilities use uvmultifit (81 P), galario
   (76 P) or vis_sample (30 P), not an image fit. For rotating gas in a cube use 3DBarolo (65 + 18 P) or KinMS
   (31 P), not a fit to the moment-1 map. For disk velocity maps use eddy (30 P) on bettermoments (58 P) maps.
6. Validate before you report. Run the package on synthetic data with known input. Papers use `simobserve`
   (23 P), for example Gaussian-source recovery in 2016ApJ...833..238H and model measurement sets in
   2020ApJ...904...77G. Then check residuals in the fitting domain and cross-check the headline number with a
   second package (2018ApJ...859...32P, 2020ApJ...898...33C, 2022MNRAS.516.4066L).
7. Write down the package, version, key settings, input data files (molecular data, opacities, templates) and
   the script path. Cards show pipeline versions unstated in 96% of papers and the CASA version in 61% (stats
   README). Recording them already beats most of the literature.
8. Check availability first, and mark every install note "check before use". CASA and the heavy suites
   (GILDAS, MIRIAD, AIPS, GALFIT, MAGPHYS, CIGALE) may not install in your environment (`tools_gap.md`). In
   CosmicCoder agent runs CASA/`tclean` could not be installed on one HPC system. If the right tool is
   missing, say so, use the archive products as delivered or the listed Python alternative, and flag the
   difference.
9. Write large outputs (tables, chains, catalogues) to files and summarise them. Do not print them into the
   context.

## When to use

- You are about to write code for a standard job: imaging, continuum subtraction, moment maps, rotation-curve
  or Keplerian fits, uv-plane fits, radial profiles, source or line finding, clump decomposition, line
  identification, excitation or radiative-transfer modelling, SED fitting, lens modelling, stacking, sampling.
- You are reproducing a paper and need to know which tool its numbers came from and what it implies. One
  example: a dendrogram catalogue depends on `min_value` and `min_delta` (3 sigma, 1 sigma and min_npix 60 in
  2017MNRAS.464L..31H).
- You need a second, independent package to check a result (see Verification checks).
- A reviewer asks "why this tool?" and you need the corpus practice behind the choice.

## When not to use

| Situation | Do instead |
|---|---|
| You need the method itself (which estimator, what thresholds, which priors) | Read the technique skill named in the router's last column; this skill only picks the tool |
| You are deciding whether to recalibrate, which archive products to fetch, or how to merge projects | `alma-archival-data-reuse` |
| You are reproducing a specific paper | `alma-paper-reproduction` first; use this map only to fill gaps the paper leaves |
| You are deciding whether a result is real or how strongly to word it | `alma-claim-verification` |
| The job is a closed-form formula (Toomre Q, a virial parameter, a unit conversion) | Write a small named function and keep every constant as an input; no package needed (general practice) |
| The data are from another facility (Chandra, XMM, JWST, MUSE, Herschel, HST) | Use that facility's own pipeline (CIAO 60 P, XSPEC 62 P, JWST pipeline 34 + 28 + 9 P across spellings, MUSE pipeline 15 + 10 P, HIPE 54 P); see `references/packages.md` |

## Steps

1. **Name the job and the data domain.** Goal: one router row. Decide whether the measurement lives in
   visibilities, a cube, an image, a spectrum or a catalogue, because the router splits on that. Closes when you
   can state "job X on data Y gives quantity Z with uncertainty".
2. **Find what the target or nearest papers used.** Read the methods, software section and acknowledgements.
   Many packages appear only as acknowledgements with no role (numpy "listed in software section",
   2017ApJ...848L..21A; astropy "acknowledged research tool", 2014ApJ...788L..34P), so tie each tool to a step.
   Papers in a series inherit outputs from earlier software runs: photometric redshifts "by Simpson et al. 2013"
   (2014MNRAS.442..577T), core extraction done "in Paper III" (2023A&A...674A..76P), a line search from an earlier
   paper (2019ApJ...882..140B). Trace those to the paper that ran the tool. Closes with a list of
   job, tool, version and source.
3. **Pick the package** from the router, applying its "prefer the alternative when" column. Closes with one
   primary tool and one cross-check tool.
4. **Confirm availability, version and interface.** Check before use: task parameters change between CASA
   releases, so run the task's own help rather than trusting remembered signatures (general practice). Versions
   in use vary widely (CASA 4.7.2 in 68 P, 5.4.0 in 54, 5.1.1 in 53, 4.7.0 in 52). Note when a paper ran a
   modified build: an in-house modified `simobserve` (2016A&A...593A..61M), "adapted" bettermoments, "modified"
   CuTEx (versions in the pack aggregate). A stock install will not reproduce those exactly. Closes when a
   trivial call runs.
5. **Smoke-test on known input.** Inject a model with known parameters (simobserve 23 P; injection-null-tests S:
   casa 24, sextractor 9, imfit 6, simobserve 5) and recover it within its errors. Closes when recovery is
   within the quoted uncertainty, or you know the bias.
6. **Run on the data, then inspect residuals** in the domain you fitted: residual visibilities, residual cube,
   residual image. Closes when residuals look like noise or the leftover structure is explained.
7. **Cross-check the headline number** with an independent package or domain (examples under Verification
   checks). Closes when the two agree within errors or the difference is explained.
8. **Record provenance**: package, version, settings, input files, the command or script path, run date.
   Closes when someone else could rerun it.

## Software router (job to package)

Read across: the job, the packages papers use (counts), what they used them for and the setting that matters,
when to prefer the alternative, and the technique skill with the detailed settings.

| Job | Packages (counts) | Used for / setting that matters | Prefer the alternative when | Go deeper |
|---|---|---|---|---|
| Calibration, restoring delivered data | CASA 2638 P; ALMA pipeline 83 P (+ calibration pipeline 12, science pipeline 9); scriptForPI | Pipeline calibration (2015A&A...582L...4M); scriptForPI then imaging (2019ApJS..244...40L, 2025A&A...695A.163B) | Use delivered products when they serve the science; recalibrate only when the paper did | alma-archival-data-reuse |
| Self-calibration | CASA `gaincal` 17 P, `applycal` 9 P (S: casa 597, tclean 128, gaincal 28, applycal 17) | Phase-only solutions (2019ApJ...879L..25I); continuum solutions applied to the full spectral data (2020ApJ...905...25G); combined-polarization "T" solutions (2016A&A...593A..61M) | Solution intervals and amplitude rounds: see the technique skill | alma-self-calibration |
| Imaging and deconvolution | `tclean` 380 P (S 537 + casa tclean 60); `auto-multithresh` 12 P | Multiscale deconvolution for extended emission (2017ApJ...842L..24A); mtmfs for wide-band continuum (2026MNRAS.552g1573L); Hogbom for a continuum image (2024MNRAS.533.1143M); robust 0.5 median (stats README) | MEM: uvmem 10 P (2015ApJ...811...92C), which also tested JvM-restoration effects (2022MNRAS.513.5790C); VLBI/EHT RML: eht-imaging 13 P; GILDAS, MIRIAD, AIPS, difmap for their own arrays | alma-imaging-choices |
| Array combination (12m, 7m, TP) | `concat` 19 P, `statwt` 14 P, `feather` 14 P (S 22 + casa feather 6), PHANGS-ALMA pipeline 15 P, tp2vis (S 3) | Recompute weights with statwt before combining (2017ApJ...835..174S, 2021A&A...649A.122P); uv-plane `concat` of 12m and 7m (2021ApJ...910..148M); `feather` with total power (2016ApJ...832..142Z, 2023ApJ...958...53S) | Full staging and short-spacing pipeline for nearby-galaxy CO: PHANGS-ALMA (2021ApJS..257...43L) | alma-array-combination |
| Continuum subtraction | `uvcontsub` 94 P (S 132), `imcontsub` 11 P, `mstransform` 11 P, statcont 37 P (S 33), findContinuum | First-order fit in the uv plane (2020ApJ...904..131N); `fitorder=1` in mstransform (2017ApJ...850L...5T, 2020PASJ...72...36T); line-free channel finding (2026MNRAS.552g1573L) | Line-rich hot cores and line forests: statcont (2017A&A...604A...6S, 2018A&A...609A.101S); image plane on small subcubes (2021ApJ...909..181L) | alma-continuum-subtraction |
| Beam matching, PB correction, regridding | `imsmooth` 15 P, `impbcor` 12 P, reproject 16 P | Common beam before ratios or modelling (2019PASJ...71..124S, 2021A&A...648A..33M, 2020ApJ...905..122H); resample ALMA onto another grid (2018ApJ...865...13T) | - | alma-moment-maps |
| Cube handling and PV cuts in Python | spectral-cube 41 P, astropy 559 P, pvextractor 16 P (S 13 in envelope PV), CARTA 55 P (viewer) | Cube analysis (2018ApJ...860..119G); PV diagrams (2016ApJ...828..100F) | PV rotation-curve fitting: SLAM (S 4), impv (S 5) | alma-envelope-kinematics-pv |
| Moment maps and velocity fields | `immoments` 34 P (S 38 + 30), bettermoments 58 P (S 66), keplerian_mask 21 P, SoFiA 18 P | bettermoments quadratic or parabola-fit line centres (2018ApJ...868..113T, 2019Natur.574..378T); Keplerian masks for lines at < 2 km/s resolution (2023A&A...678A.146B); SoFiA masks for moments (2019PASJ...71...85M) | Several components per sightline: per-pixel Gaussian fits with pyspeckit 44 P (2018ApJ...854...83T) | alma-moment-maps |
| Protoplanetary disk kinematics | eddy 30 P (S 39), GoFish 55 P (S 32), DISCMINER 15 P, disksurf 12 P, pdspy 11 P, VISIBLE 15 P | eddy Keplerian fit to the v0 map (2019ApJ...884L..56T); GoFish Keplerian-shifted stacking and radial profiles (2020ApJ...899..157T, 2021AJ....162...99F); emission surfaces with disksurf (2024ApJ...964..190L) | Channel-map forward model with residuals: DISCMINER (2023A&A...674A.113I); weak-line detection: VISIBLE matched filter (2018ApJ...859..131L) | alma-keplerian-disk-kinematics |
| Galaxy cube kinematics (rotation, dispersion, mass) | 3DBarolo 65 + 18 P (S 90 + 22 + 5), KinMS 31 P (S 56 + kinms_mcmc 13 + kinms_fitter 9), GalPak3D 19 P, kinemetry 23 P | 3DBarolo tilted rings on the cube (2018A&A...612A..29B, 2016ApJ...823...68S); KinMS forward models with beam smearing (2015ApJ...806...39O, 2017MNRAS.468.4675D) | Few beams across a source, few parameters: KinMS or GalPak3D with a sampler (recommendation in alma-galaxy-3d-kinematics; 2017ApJ...835..213P; source-plane cube, 2018ApJ...866L..12G); 2D harmonic decomposition: kinemetry (2014A&A...567A.125G) | alma-galaxy-3d-kinematics |
| SMBH mass from gas | KinMS (S 20), SkySampler 10 P (S 10), MgeFit 9 P, JAMPy (S 6) | CLEAN components as the gas distribution (2019MNRAS.485.4359S); MGE of the stellar light for the potential (2022MNRAS.509.2920N) | Stellar kinematics from optical IFU: pPXF 45 P (2017A&A...600A..80K) | alma-smbh-gas-dynamics |
| Simple uv-plane fits (point, Gaussian, disk) | CASA `uvmodelfit` 30 P (S 56 + 38), GILDAS `uv_fit`, uvmultifit 81 P (S 86) | uvmodelfit for one component (uniform disk, 2016ApJ...829....6W); uvmultifit for several components or per-channel spectra (2013A&A...558A.123M, 2014A&A...566A.112M) | Model images or many parameters: next row | alma-uv-plane-fitting |
| uv-plane forward models of images | galario 76 P (S 86), vis_sample 30 P (S 37), plus emcee | FT a model image and sample it at the observed (u,v) (2018A&A...619A.161C, 2016ApJ...828..113M, 2017A&A...605A..21C) | Subtract fitted models from the visibilities: `uvsub` 10 P (2021A&A...654A..90L) | alma-uv-plane-fitting |
| Disk radial profiles, rings, gaps | frank 16 P + frankenstein 9 P, galario (S 47), GoFish (S 45) | Non-parametric 1D visibility fits beyond the beam (2024A&A...682A..55M, 2020MNRAS.498.1319M) | Parametric ring models in emcee; papers compare both (2021A&A...649A.122P) | alma-disk-substructure-profiles |
| Image-plane sizes, fluxes, photometry | CASA `imfit` 96 P, GALFIT 121 P, photutils 76 P | Gaussian flux, position and size (2017ApJ...844..123F); prior-based iterative fits in crowded maps (2019ApJS..244...40L); elliptical-annulus profiles (2019AJ....158...47M) | Clumpy sources: aperture photometry, not a single Gaussian | alma-source-extraction-counts |
| Blind continuum source finding | SExtractor 113 + 12 P (S 101), PyBDSF 12 P (S 14), BLOBCAT 9 P, Aegean 9 P | Run on the S/N map; blind extraction plus Gaussian fits (2019ApJS..244...40L); source extraction (2015ApJ...815L...8U) | Any finder: run it unchanged on the inverted map and on injected sources | alma-source-extraction-counts |
| Blind line search in cubes | LineSeeker 11 P, findclumps (interferopy 10 P; S 9 to 12), SoFiA 18 P | Fidelity and completeness with LineSeeker (2019ApJ...882..139G); findclumps (2023Natur.617..261K); SoFiA-2 with injection recovery and inverted-cube fidelity (2025A&A...695A.163B) | Spectral-line source finding with masks: SoFiA (2018ApJ...853..195W) | alma-redshift-line-search |
| Cores, clumps, filaments | astrodendro 84 P (S 99), getsf 23 P (S 27), getsources 9 P, clumpfind 44 P (S 46), CuTEx 9 P, FilFinder 15 P | Dendrogram leaves as cores (2016ApJ...831...32N, 2017ApJ...842...92G); `min_value`/`min_delta` in rms units (2017MNRAS.464L..31H) | Multi-scale background and filament separation: getsf (2022A&A...662A...8M, completeness images in 2023A&A...674A..75N); compact-source photometry: CuTEx (2025A&A...696A.151C) | alma-core-extraction-cmf |
| GMC decomposition and virial analysis | CPROPS 37 P (S 41), cpropstoo (S 8), pycprops (S 5), astrodendro (S 12), SCIMES (S 3) | Cloud properties on the cube (2015ApJ...806...35J, 2014ApJ...793...37A) | Hierarchical structure, not discrete clouds: astrodendro | alma-gmc-decomposition-virial |
| Line identification | CDMS 57 P (S 65), Splatalogue 43 P (S 31), JPL (S 15 + 13), CASSIS 87 P, MADEX 18 P | Line ID and LTE synthetic spectra in CASSIS (2016A&A...590L...6C); check lines against CDMS and JPL (2017A&A...597A..53L); Splatalogue queries through astroquery (2018ApJ...860..119G) | New-molecule spectroscopy: SPFIT/SPCAT 9/11 P (2023MNRAS.523.2887M) | alma-line-identification |
| LTE synthetic spectra, column densities | CASSIS (S 136), XCLASS 38 P + MAGIX 15 P, Weeds 34 P, MADCUBA 21 P (with SLIM) | LTE spectral modelling with automated MAGIX fits (2014ApJ...787..112C; 2016A&A...587A..91B Weeds; 2018ApJ...853L..19S MADCUBA) | Sub-thermal excitation: next row | alma-rotational-diagram-lte |
| Non-LTE excitation | RADEX 212 P (S 231), SpectralRadex 11 P (S 17), pyradex (S 8), LAMDA 15 + 10 P, RATRAN 18 P, LIME 67 P | RADEX grids; Python interface with emcee or UltraNest (2022A&A...667A.131B, 2024A&A...686A..31B); LAMDA collision files (2014ApJ...785..149S) | Spatial structure or optically thick lines: RATRAN (2012ApJ...749..162O) or LIME (2013ApJ...774...16R) | alma-non-lte-excitation |
| Line fitting (Gaussian, hyperfine) | lmfit 53 P, MPFIT 40 P, pyspeckit 44 P, SciPy curve_fit 11 + 10 + 9 P, GILDAS CLASS | Gaussian spectral fits (2016ApJ...832..148V); lmfit as pyspeckit's engine (2018ApJ...861...14C); N2H+ hyperfine in GILDAS (2013A&A...555A.112P) | - | alma-dense-gas-tracers |
| Dust and line radiative transfer | RADMC-3D 168 + 13 P (S 220 + 16), MCFOST 52 P (S 78), LIME (S 83), DALI 44 P (S 80), Hyperion 10, TORUS 11, MCMax 10, DUSTY 13 P | Model images then sampled in uv (2016ApJ...832..110C, vis_sample); disk thermo-chemistry with DALI (2014A&A...562A..26B); continuum plus CO with MCFOST (2013A&A...557A.133D) | Spherical dust shells of evolved stars: DUSTY (2016A&A...596A..50G) | alma-radiative-transfer-modelling |
| Dust opacities | optool 18 P (S 14), dsharp_opac 9 P | DSHARP or DIANA opacities fed to RADMC-3D (2024A&A...681A..82G, 2023A&A...675A.131T); kappa and beta (2019ApJ...881..159M) | - | alma-dust-continuum-mass |
| Astrochemical models | NAUTILUS 17 P, MAGICKAL 14 P, UCLCHEM 11 P, Meudon PDR 11 P, PDR Toolbox 13 P, Cloudy 66 P | Gas-grain models (2016ApJ...825...79S, 2014Sci...345.1584B); UCLCHEM coupled to RADEX (2020MNRAS.496.5308S); PDR grids for G0 and density (2016A&A...595A..72M) | Ionised gas and [CII]/[NII]: Cloudy (2012A&A...542L..34N) | alma-chemical-modelling |
| SED fitting | CIGALE 101 P, MAGPHYS 98 P, Bagpipes 34 P, Prospector 30 P; photo-z EAZY 60, LePhare 31, FAST 25 + 9, hyperz 19 | UV-to-mm/radio SED fits at fixed redshift (2019ApJS..244...40L, MAGPHYS); modified blackbody in emcee (2014A&A...568A..92M) or curve_fit (2018A&A...615L..14M) | Non-parametric star-formation histories: Prospector (2019ApJ...884..154W cross-check) | alma-sed-fitting |
| Strong lensing | lenstool 25 P (S 28), PyAutoLens 13 P (S 20), glafic 16 P (S 18), visilens 15 P (S 16), uvmcmcfit (S 7) | Galaxy-scale lenses fitted on visibilities (2016ApJ...826..112S, 2022MNRAS.512.2426M, 2015ApJ...812...43B) | Cluster lenses and magnification maps: lenstool or glafic (2016A&A...593L...2N, 2016ApJS..222....1F) | alma-lens-modelling |
| Stacking | stacker 11 P, linestacker (S 10), GoFish (S 25 in stacking) | uv-plane stacking of faint sources (2015ApJ...810..133I); shifting phase centres (2019ApJ...887..107F) | Disks: Keplerian-shifted stacking with GoFish | alma-stacking |
| MCMC and nested sampling | emcee 410 P, dynesty 34 P, MultiNest 22 + 9 P, UltraNest (S 4), corner 19 + 9 P | emcee for posteriors; evidence for model choice with MultiNest (2013MNRAS.430.2454L) or dynesty (2019A&A...628A.100D); UltraNest orbit fit (2025A&A...699A..22M) | Plain least squares when the posterior is near Gaussian and you need speed: lmfit, MPFIT | technique skill of the model |
| Regression with upper limits | linmix 50 + 9 P, lifelines 26 P, ASURV 11 P | Bayesian regression with censored points (2017ApJ...844...99L); Kaplan-Meier (2017ApJ...851...83C, 2014ApJ...784...62A) | - | alma-star-formation-laws |
| Astrometric and position alignment | `fixvis` 10 P, `fixplanets` 8 P, scikit-image 21 P, reproject, astroquery 14 P | Phase-shift visibilities with Gaia positions and proper motions (2021A&A...648A..33M); align multi-epoch data (2018ApJ...869L..41A); cross-correlation image registration (2018ApJ...869L..14M) | Common phase centre in metadata across execution blocks: fixplanets (2023A&A...676A...4C) | alma-variability-time-domain |
| Hydro and N-body comparisons | PHANTOM 31 P (S 32), FARGO3D 12 P, PLUTO 10, RAMSES 10, REBOUND 13, DustPy 9 | SPH with PHANTOM (2018ApJ...860L..13P) or grid hydro with FARGO3D (2018ApJ...860L..12T), then radiative transfer (S in hydro-simulation-comparison: mcfost 17, radmc-3d 13, fargo2radmc3d 3) | - | alma-hydro-simulation-comparison |
| Polarization, planets, time domain | CASA (S 157 polarization), POLARIS (S 8); NEMESIS 13 P (S 29); CASA uvmodelfit light curves | Line-by-line retrievals for planetary atmospheres (2014ApJ...795L..30C) | - | alma-polarization-magnetic-fields, alma-solar-system-atmospheres |

The router covers the main jobs. `references/packages.md` lists all 220 packages named in 8 or more papers,
with fields, versions and uses.

## Parameter defaults and ranges

Defaults to use when the paper or data are silent. Each one needs a sentence in your write-up saying you assumed it.

| Decision | Default | Range or alternative seen | Evidence |
|---|---|---|---|
| Briggs robust | 0.5 | -2 to 2 in most fields | stats README (median 0.5 in all major fields) |
| tclean masking | auto-multithresh, record its values | stated settings `noisethreshold` 5, `sidelobethreshold` 1.25 | 2024ApJ...966...32E, 2024AJ....168..151J, 2024RAA....24f5011X |
| Continuum fit order | 1 (linear) in the uv plane | 0 (constant) on small image subcubes | 2020ApJ...904..131N, 2017ApJ...850L...5T, 2021A&A...653A..77P; 2021ApJ...909..181L |
| Visibility weights | `statwt` after concatenation or self-calibration | - | 2017ApJ...835..174S, 2021A&A...648A..33M, 2022MNRAS.513.5790C |
| Self-cal solution intervals | phase-only, starting long (`inf`) and shortening | inf then int in two rounds | 2024A&A...686A.274V, 2019ApJ...879L..25I |
| Keplerian mask | use for disk lines at fine velocity resolution | lines < 2 km/s resolution | 2023A&A...678A.146B, 2021A&A...648A..19W |
| astrodendro thresholds | `min_value` 3 sigma, `min_delta` 1 sigma | `min_npix` 60 in one case; vary them and check conclusions | 2017MNRAS.464L..31H |
| emcee walkers and steps | set per model, then check convergence | 48 walkers x 3500 steps (500 burn-in); 200 x 5000 + 5000; walkers = 8 x parameters | 2020ApJ...891...48H, 2021A&A...648A..19W, 2024A&A...688A.149D |
| Sampler choice | emcee | nested sampling when the evidence is needed | 410 vs 34 + 22 + 9 P; 2013MNRAS.430.2454L |
| Second package for the headline number | one independent tool or domain | galario cross-check fit; independent lens check; second lens code; second SED code; 3DBarolo vs KinMS | 2018ApJ...859...32P, 2020ApJ...898...33C, 2017ApJ...843L..35W, 2019ApJ...884..154W, 2022MNRAS.516.4066L |

The cards rarely state MCMC convergence diagnostics or a finder's full parameter set, so treat chain lengths and
thresholds above as examples, not defaults to copy. The technique skills hold the full ranges.

## Pitfalls

- **Reimplementing a standard tool.** A home-made fitter skips what the package handles: beam smearing in cube
  kinematics (KinMS models it explicitly, 2015ApJ...806...39O), visibility sampling (galario, vis_sample), and
  line opacity in LTE synthetic spectra (Weeds, 2016A&A...587A..91B). In CosmicCoder agent runs this cost accuracy against the published value.
- **Fitting in the wrong domain.** A Gaussian on a CLEAN image is not a uv fit; a tilted-ring fit to a moment-1
  map is not a cube fit. Papers that fit visibilities name uvmultifit, galario or vis_sample (router counts).
- **Name in the paper does not mean used.** Clumpfind is named only as an algorithm that would struggle
  (2012A&A...538L...9H). `fixplanets` is discussed and not used (2021A&A...648A..33M). Gravlens is named for
  earlier work and replaced (2015ApJ...812...43B). Tie every tool to a step before you copy it.
- **Spellings split the counts.** 3dbarolo / 3d-barolo, radmc-3d / radmc3d, sextractor / source extractor,
  frank / frankenstein, linmix / linmix_err and five GILDAS spellings are separate rows. Add them before you
  rank tools. Generic names collide: "clean" (the algorithm), "class" (GILDAS CLASS), "fast" (the SED code),
  "shape" (SHAPE modelling), "visible" (the VISIBLE filter).
- **Modified or adapted builds.** Some results come from in-house versions (simobserve in 2016A&A...593A..61M;
  "adapted" bettermoments and "modified" CuTEx in the version lists). A stock install may not reproduce them.
  Flag it and do not force agreement.
- **Inherited software outputs.** Series papers reuse catalogues, masks and corrections made by earlier runs
  (2014MNRAS.442..577T, 2023A&A...674A..76P, 2019ApJ...882..140B). In CosmicCoder agent runs, unstated inherited
  corrections broke a reproduction. Find the paper that ran the tool and its settings.
- **The input files decide the answer as much as the code.** RADEX results depend on the LAMDA file
  (2014ApJ...785..149S). RT models depend on the opacity table (optool or dsharp_opac, 2024A&A...681A..82G).
  LTE fits depend on the catalogue entry (CDMS predictions in 2023MNRAS.523.2887M). Record the file and its version.
- **Defaults hide choices.** "Default parameters" for auto-multithresh (2024ApJ...966...32E) is only
  reproducible with the CASA version. Pipeline versions are unstated in 96% of cards (stats README).
- **Cross-facility tools are not ALMA tools.** XSPEC, CIAO, HIPE, the JWST and MUSE pipelines appear because
  papers are multi-wavelength. Do not route ALMA jobs through them.
- **Heavy installs and environment limits.** If CASA or a legacy suite will not install, do not quietly swap
  in an untested reimplementation. Use the delivered archive products or the Python alternative the router
  names, and state the difference.

## Verification checks

Before reporting a number that came out of a package:

- The code ran and wrote its outputs, and they look sane (no NaN maps, chains not stuck, catalogue sizes
  plausible). In CosmicCoder agent runs a judge passed tasks whose code was written but never run.
- **Recovery test**: a synthetic input through the same tool and settings comes back within errors (simobserve
  23 P; 2016ApJ...833..238H, 2020ApJ...904...77G). For finders, also check completeness and fidelity from
  injected sources and the inverted map (2025A&A...695A.163B, 2019ApJ...882..139G, 2023A&A...674A..75N).
- **Residuals** in the fitting domain show no structure above the noise, or the leftover structure is named.
- **Independent cross-check** of the headline quantity: a second package (2018ApJ...859...32P galario
  cross-check; 2020ApJ...898...33C PyAutoLens check; 2017ApJ...843L..35W glafic check; 2022MNRAS.516.4066L
  3DBarolo vs KinMS) or a second domain (uv fit vs image fit; parametric vs frank profile, 2021A&A...649A.122P).
- **Sampler health**: chains converged by the package's own diagnostic, priors stated, and posteriors not
  piled against a prior edge (general practice).
- **Provenance**: package, version, settings, input data files and script path are in the write-up.

What an evaluator will look for: the quantity with its uncertainty, the package and settings that produced it,
the recovery or cross-check that backs it, and code traceable to each experiment.

## Source cards

Full member list: `references/sources.md`. Per-package table: `references/packages.md`. Most informative for
software choice:

- 2019ApJS..244...40L (archive mining: astroquery, CASA, PyBDSF, GALFIT, GILDAS uv_fit, MAGPHYS in one chain)
- 2022MNRAS.513.5790C (uvmem vs tclean, statwt, multi-epoch visibility alignment)
- 2025A&A...695A.163B (SoFiA-2 line finding with injection and inverted-cube fidelity)
- 2026MNRAS.552g1573L (pipeline, findContinuum, mtmfs, astrodendro and Hyper for 1.3 mm continuum sources)
- 2017ApJ...842...92G (astrodendro, spectral-cube, pvextractor, pyspeckit stack)
- 2016ApJ...828..113M (vis_sample as an open uvmodel implementation)
- 2018A&A...619A.161C (galario sampling at observed uv points)
- 2024A&A...682A..55M (frank super-resolution profiles)
- 2018ApJ...868..113T (bettermoments plus eddy rotation curves)
- 2023A&A...674A.113I (DISCMINER channel-map modelling)
- 2015ApJ...806...39O (KinMS PV modelling with beam smearing)
- 2018A&A...612A..29B (3DBarolo cube fits)
- 2022MNRAS.516.4066L (3DBarolo vs KinMS cross-check)
- 2017MNRAS.464L..31H (dendrogram thresholds stated)
- 2022A&A...662A...8M (getsf cores and filaments)
- 2014ApJ...787..112C (XCLASS with MAGIX, MADEX LVG)
- 2024A&A...686A..31B (SpectralRadex with UltraNest)
- 2014A&A...562A..26B (DALI thermo-chemical disk model)
- 2024A&A...681A..82G (optool opacities into RADMC-3D)
- 2015ApJ...812...43B (uvmcmcfit visibility lens modelling replacing Gravlens)
- 2022MNRAS.512.2426M (PyAutoLens in the uv plane)
- 2013MNRAS.430.2454L (MultiNest evidence for model selection)
- 2017ApJ...844...99L (linmix regression with upper limits)
- 2021A&A...648A..33M (fixvis with Gaia positions, imsmooth, statwt, dsharp_opac)
- 2016ApJ...833..238H (simobserve recovery test)
- 2016A&A...593A..61M (modified simobserve, T-type gaincal)
