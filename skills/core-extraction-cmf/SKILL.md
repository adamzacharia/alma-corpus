---
name: alma-core-extraction-cmf
description: "Find compact cores in ALMA continuum (or dense-gas line) maps with astrodendro, clumpfind, getsources or gaussclumps, measure their fluxes and sizes, and build a completeness-corrected core mass function (CMF) with a defensible power-law fit. Use when extracting a core catalog from a protocluster, IRDC, hub-filament or CMZ map, when fitting or comparing a CMF slope with the IMF, when estimating core completeness, or when checking someone else's core catalog or CMF. Built from 67 ALMA papers (2014-2026)."
---

# Core extraction and core mass functions

Turns a continuum image into a catalog of compact cores (position, flux, size, mass) and, when the sample is
large enough, a core mass function. Two things decide whether the result means anything: (1) the
extraction settings and algorithm, which change the number of cores and the CMF slope by a lot (the same
G286 map gives 76 dendrogram cores and a true slope of 1.24 +/- 0.17, but 0.64 +/- 0.13 with clumpfind:
2018ApJ...853..160C), and (2) the completeness and temperature treatment: the dendrogram slope moved from
1.11 (raw) to 1.24 after flux and number corrections in 2018ApJ...853..160C, random 20-100 K temperatures
spread the NGC 6334 slope over -0.7 to -1.46 (2020A&A...635A...2S), and two papers say their own
beam-sized or point-source injections overestimate completeness (2019MNRAS.483.1624B, 2020ApJS..251...14H).

> Always report: algorithm and version, every threshold in units of the local rms, the image the finder
> ran on (PB-corrected or not, 12m-only or combined), the mass formula inputs, the flux calibration
> uncertainty and how it was propagated into masses, the CASA/pipeline version and the imaging settings
> (weighting, clean threshold, masks), the completeness limit and how it was measured, the CMF convention
> (dN/dM, dN/dlogM or cumulative N(>M)), fit range and fit method. The cards most often flag flux
> calibrator / flux-scale uncertainty (6, 3 and 3 cards under three phrasings), line-free channels (5 + 3)
> and CASA version (3) as not stated (pack aggregate "Settings cards flag as needed but not stated").

Related skills: mass from flux (opacity, temperature, gas-to-dust) is in `alma-dust-continuum-mass`;
decomposing CO cubes into GMCs and virial analysis of clouds is in `alma-gmc-decomposition-virial`;
blind source detection and number counts in extragalactic fields are in `alma-source-extraction-counts`.
This skill only repeats what is specific to cores.

## When to use

- A continuum (1.3 mm, 3 mm, 0.87 mm) map of a clump, IRDC, protocluster or CMZ cloud and you need a core
  catalog (2016ApJ...833..209O, 2020ApJ...894L..14L, 2025ApJ...994..233Y, 2020ApJS..251...14H).
- Fitting a CMF and comparing it with the Salpeter IMF (2016ApJ...833..209O, 2018ApJ...853..160C,
  2020ApJ...890...76N, 2020A&A...635A...2S, 2020ApJ...894L..14L).
- Dense-gas cores in a line cube (H13CO+, C34S) when the continuum is confused or absent
  (2019ApJ...872..121U, 2023MNRAS.526.4402B). Masses then need the line branch of step 4.
- Fragmentation statistics: core counts per clump, separations, core-to-clump mass fractions
  (2020ApJ...890...76N, 2017A&A...600A.141K, 2026A&A...705A.100E).
- Checking a published or tool-produced core catalog or CMF slope.

## When not to use

| Situation | Use instead |
|---|---|
| CO cube of a nearby galaxy or LMC cloud, structures of tens of pc | `alma-gmc-decomposition-virial` (CPROPS, astrodendro on CO: 2018ApJ...857...19F, 2024ApJ...964..166K, 2024ApJ...966...51G) |
| Blind line or continuum source search in a deep field, number counts, purity from inverted maps | `alma-source-extraction-counts` (this pack's clumpfind hits in 2017PASJ...69...45H, 2018Natur.556..469M, 2021ApJ...908..163M are that use) |
| Converting one core's flux to a mass | `alma-dust-continuum-mass` |
| Clumps in a lensed or high-z galaxy | Source-plane or galaxy kinematics work. Structures are far larger than cores, and lensed data need the clumps reassembled into lens images: 2017A&A...604A.117C runs 3D clumpfind on a CO(4-3) cube and then groups the clumps into image systems; 2015ApJ...806L..17S selects 5 sigma regions and uses clumpfind as a cross-check |
| Peak finding for cloud-lifecycle (tuning-fork) statistics | HEISENBERG workflow, which uses clumpfind only to place apertures (2019Natur.569..519K, 2025A&A...698A.296R) |
| Only a handful of cores | Report masses individually; authors say such samples are too small for a CMF or a trend (2017MNRAS.464L..31H, 2025ApJ...994..233Y) |
| Emission optically thick (hot cores, very bright compact sources) | Treat masses as lower limits and do not build a CMF (2025ApJ...994..233Y, 2019A&A...621A.122B) |

## Steps

1. **Prepare the image the finder will run on.**
   - Goal: flat, well-characterised noise and known spatial filtering.
   - Run the finder on the non-primary-beam-corrected image (flat noise) and measure fluxes on the
     PB-corrected image; drop sources below 30% PB response (2020ApJ...894L..14L). 2019ApJ...871..185L also
     ran its dendrogram on the uncorrected image and quoted peaks from the PB-corrected one (card; no PB cut
     stated). If you run on a PB-corrected mosaic, use a local rms map, not one global value
     (2020ApJS..251...14H prunes leaves against the local RMS).
   - Measure rms in an emission-free region of the final map (2017A&A...600A.141K) or with random beam
     apertures (2021ApJ...908..163M, line cube).
   - Know what the array filters out. 12m-only maps lose most extended flux: ALMA+ACA recovers 8.4 of ~29
     Msun in TUKH122 (2.5 Msun for 12m only; 2018ApJ...856..147O); ~20% recovered in 2018A&A...616L..10F and
     2017A&A...608A..98S. Combining with single-dish (Herschel 250 um feather) changed core masses by ~10%
     except one core by ~60% (2018ApJ...856..147O). Cores are compact, so their fluxes are less affected
     than the clump, but the background under them is not.
   - Record the flux calibration uncertainty now; it enters every mass (see the report box above).
2. **Extract cores.** Pick one algorithm as fiducial and run a second as a check (step 6).
   - astrodendro (leaves = cores): `min_value` and `min_delta` in units of rms; `min_npix` is a pixel
     count (a voxel count in a cube), so convert from beam area yourself. General practice: beam area in
     pixels = 1.1331 * bmaj * bmin / cdelt^2 (FWHMs and pixel size in the same angular unit); for a cube,
     multiply by the number of channels you require. Example: 2024ApJ...969..143I states 1 beam area = 14
     square pixels; 2020ApJ...896..110L uses 40 px, "approximately the synthesized beam area" (card).
     Typical: 3 sigma, 1 sigma, about 1 beam (table below). 2018ApJ...856..147O's "min pixels 3 x
     theta_beam" is dimensionally ambiguous; treat it as unresolved, not as "3 beams".
   - clumpfind (Williams et al. 1994; IDL, Starlink CUPID): lowest contour and step, 2-3 sigma and
     2 sigma in the on-topic core papers, then keep peaks above 5 sigma (2016ApJ...833..209O,
     2020ApJ...890...76N, 2019MNRAS.483.1624B, 2019ApJ...872..121U).
   - getsources (+ getimages for background) is the multi-scale choice: 2018A&A...616L..10F ran getimages
     with default parameters and a 2" maximum structure size, then getsources with default parameters
     (versions 2.171128 and 1.140127: card); 2018A&A...618L...5N used getsources v1.140127 (card) but its
     configuration is not given; 2019ApJ...884...48C seeds a CASA `imfit` 2D Gaussian with the getsources
     position and size and keeps converged fits only.
   - gaussclumps (Starlink CUPID) after a median-filter background subtraction, threshold 3 rms, filter
     width 10" (2017A&A...600A.141K). SExtractor appears in 2020A&A...635A...2S.
   - Line cubes: 3D clumpfind at 2 sigma levels and steps, rejecting candidates with fewer than 3 pixels
     at >= 3 sigma or fewer than 2 channels (2019ApJ...872..121U).
   - Visual vetting is common and should be recorded: by three coauthors with a dendrogram confirmation
     (2025ApJ...994..233Y), visual inspection of clumpfind regions (2019MNRAS.483.1624B); 2019ApJ...871..185L
     admits its catalog edits are subjective.
3. **Measure flux, size and position.**
   - Flux: integrate within the leaf/clump on the PB-corrected map (2020ApJ...894L..14L), or fit a 2D
     Gaussian (`imfit`) seeded by the finder (2019ApJ...884...48C; 2020ApJ...896..110L, card). Integration
     is unit-aware (general practice): for a Jy/beam map, S = sum(I_pix) * (pixel area / beam area) with
     beam area = 1.1331 bmaj bmin; for a surface-brightness map (e.g. the MJy/sr CMZoom map of
     2020ApJS..251...14H), S = sum(I_pix) * pixel solid angle in sr (x 1e6 for MJy to Jy). A plain sum of
     Jy/beam pixels is not a flux.
   - Size: geometric mean of the semi-axes (2020ApJ...890...76N) or R = 1.91 sqrt(sigma_maj sigma_min)
     from second moments (2024ApJ...966...51G, a CO clump paper; the 1.91 factor is the usual
     moment-to-radius conversion). Deconvolve only cores clearly larger than the beam: 2020ApJ...894...87C
     drops cores with area < 1.5 beam areas (34 of 76) from the deconvolved analysis; 2024ApJ...966...51G
     removes clumps with minor axis < sqrt(2) beam.
4. **Convert to mass.** Branch on what selected the core.
   - **Dust continuum** (the usual case). Optically thin modified blackbody; details and opacity choices in
     `alma-dust-continuum-mass`. Values used by core papers in this pack:
     kappa_230GHz = 0.01 cm2/g including gas-to-dust 100, mu = 2.33 (2019ApJ...884...48C), and the same
     0.01 cm2/g (gas+dust) in 2018A&A...618L...5N (card); kappa = 5.95e-3 cm2/g at 1.3 mm with dust-to-gas
     1:141 (2018ApJ...855L..25K, card); kappa ~0.867 cm2/g (dust) at ~226 GHz with beta 1.75, gas-to-dust
     100, mu_H2 = 2.8 (2020ApJS..251...14H); 0.899 cm2/g (dust) at 1.3 mm with gas-to-dust 150, mu = 2.8
     (2024A&A...690A.185W, card); k_100GHz = 0.21 cm2/g with Rgd = 100 (2020ApJ...890...76N); 0.0755
     cm2/g at 3 mm, beta = 2 (2018ApJ...856..147O).
   - **Line-selected cores** (H13CO+, C34S cubes). A dust formula does not apply. Either measure dust masses
     on a matched continuum map, or document the whole line chain: excitation temperature per core,
     optical depth, abundance and the column-to-mass integral. 2019ApJ...872..121U warns the abundance alone
     is uncertain by up to a factor of 2, and its card flags that the per-core Tex assignment from the LVG
     grid is not stated. 2023MNRAS.526.4402B derives dust-core masses separately on its 865 um map at 54 K.
   - Temperature. A single 20 K for catalog masses: 2018ApJ...853..160C, 2020ApJ...894...87C and
     2018ApJ...855L..25K (card) (3 papers, my count). 2020ApJS..251...14H uses 20 K only to convert its
     completeness simulations to mass; its catalog masses use Herschel dust temperatures. Other choices:
     the parent-clump temperature (2020ApJ...890...76N, which uses rotational temperatures where
     available), the temperature of the hosting Herschel core (2018A&A...616L..10F, card), SED-fit clump
     temperatures of 23-28 K (2019ApJ...884...48C), PPMAP temperatures (2018A&A...618L...5N, card), a
     temperature set by clump L/M stage (2024A&A...690A.185W: 20 K for L/M < 1, 35 K for 1-10, card;
     2026A&A...705A.100E, card), and fixed 12 K or 54 K (2018ApJ...856..147O, 2023MNRAS.526.4402B).
   - Mass limit: convert the detection threshold flux (3 sigma) at the clump temperature
     (2020ApJ...890...76N gives 0.7-1.4 Msun limits that way). This is a sensitivity limit, not a
     completeness limit (step 5).
5. **Measure completeness.** Inject synthetic sources into the real map, rerun the same finder with the
   same parameters, and record the recovered fraction per flux or mass bin.
   - 2D Gaussians injected and recovered by the same dendrogram (2025ApJ...994..233Y: 0.25 / 0.20 mJy
     completeness limits at 3 mm); artificial cores placed at random positions and recovered by astrodendro
     (2020ApJ...894L..14L, 20 km/s cloud: 90% completeness ~2 Msun for the 30% PB selection, ~5 Msun for
     sources above 5 sigma); 600 beam-sized Gaussians per mass bin, logistic fit to the completeness curve,
     N_corr = N / f (2019MNRAS.483.1624B); point sources passed through CASA `simobserve` and `tclean`
     before extraction (2020ApJS..251...14H: 95% completeness at 80 Msun robust, ~50 Msun
     high-completeness, Td = 20 K); 10 beam-shaped artificial cores per run, 30 repeats
     (2018ApJ...853..160C, card). A catalog-level 90% flux completeness of 0.95 mJy (0.13 / 0.37 Msun at
     3.5 / 6 kpc) is quoted by 2026A&A...705A.100E (card).
   - Apply both a number correction and a flux correction (recovered flux vs injected) when building a
     "true" CMF (2018ApJ...853..160C reports raw 1.11 +/- 0.20 and corrected 1.24 +/- 0.17).
   - Inject sources with a realistic size range, not only beam-sized or point sources: both
     2019MNRAS.483.1624B and 2020ApJS..251...14H say their point/beam-sized tests overestimate completeness
     for extended cores.
6. **Test robustness of the catalog.**
   - Vary the finder parameters: min_value 3 sigma and min_delta 2 sigma left conclusions unchanged
     (2020ApJ...894L..14L); dropping F_min from 4 to 3 sigma raised the count from 76 to 125 cores
     (2018ApJ...853..160C). For clumpfind, cited tests show the power-law index unchanged for thresholds of
     2-4 sigma and steps of 2-3.5 sigma in Orion A (quoted by 2016ApJ...833..209O).
   - Run a second algorithm: fluxes and sizes similar between astrodendro and clumpfind
     (2020ApJ...890...76N, 2024MNRAS.527.5895D), but CMF slopes can differ by 0.6 (2018ApJ...853..160C).
   - Check resolution: 12m-only vs combined image (2018ApJ...853..160C); uv-tapers from 100 to 200 klambda
     before a dendrogram, 150 klambda adopted (2021ApJ...907L..15S, card); compare predicted fragment counts
     with higher-resolution data (2020A&A...635A...2S: 9 predicted vs 7 resolved fragments for one source).
   - Keep two catalogs if needed: a robust one (leaf peak > 6 sigma local rms) and a high-completeness one
     (> 4 sigma), each with its own completeness (2020ApJS..251...14H: 285 vs 816 leaves).
7. **Build and fit the CMF.**
   - Fit only above the completeness limit (2020A&A...635A...2S fits dN/dlnM above 2 Msun).
   - Preferred: unbinned maximum likelihood. MLE on the eCDF with a 90% confidence interval
     (2020ApJ...890...76N: -1.33 +/- 0.15, interval -1.58 to -1.08, labelled dN/dM proportional to M^alpha; taken as
     labelled that is a logarithmic exponent of -0.33, and the authors call the CMF top-heavy, card);
     MLE of Clauset et al. (2009) with the lower bound chosen by minimising the KS distance, via `plfit`
     (2020ApJ...894L..14L: alpha 1.00-1.07 in dN/dlogM, lower bound ~5 Msun).
   - Other fits seen: chi2 in log space with 5 bins per dex, Poisson errors, empty bins as upper limits
     (2018ApJ...853..160C); cumulative N(>M) = k M^-alpha + c over 2.4-14 Msun with Poisson counting
     uncertainties sigma_N = sqrt(N) (2016ApJ...833..209O); single power law with chi2/dof, binning not
     stated (2019ApJ...872..121U). If you refit such data, pass sqrt(N) as the per-point uncertainty
     (e.g. `scipy.optimize.curve_fit(..., sigma=np.sqrt(N))`, which weights by 1/N), not as a weight; and
     note that cumulative points are correlated, so the chi2 errors are optimistic (general practice).
   - State the convention and convert explicitly. General practice: Salpeter is dN/dM ~ M^-2.35, i.e.
     dN/dlogM ~ M^-1.35 and N(>M) ~ M^-1.35; a dN/dM exponent x becomes x + 1 in dN/dlogM. Papers compare
     against 1.35 (2016ApJ...833..209O, 2020A&A...635A...2S) and against Orion A 2.3 +/- 0.1 in the dN/dM
     form (2019ApJ...872..121U).
8. **Propagate the temperature and multiplicity bias into the slope.**
   - Random temperatures 20-100 K over 100000 trials moved the NGC 6334 slope across -0.7 to -1.46
     (2020A&A...635A...2S); a flux-dependent T_dust moved CMZ slopes to 1.40 +/- 0.10 with a fixed 1 Msun
     lower bound (2020ApJ...894L..14L).
   - Unresolved multiplicity flattens the high-mass end; 2020A&A...635A...2S models it with a Jeans
     fragmentation recipe (epsilon0 = 0.4, p = 1.3 reproduce a -1.35 slope).
9. **Optional: virial state and core-to-clump fractions.**
   - alpha_vir = 5 sigma^2 R / (G M) with sigma the 1D velocity dispersion (2020ApJ...890...76N,
     2020ApJ...894...87C). 2020ApJ...894...87C uses the thermal-corrected dispersion, a density index
     k_rho = 1.5 giving a = 5/4, and treats alpha > alpha_cr = 2a as unbound; its absolute uncertainty is
     about a factor of 2.5 (T = 15 / 30 K changes alpha by 0.6 / 1.9), so it cannot say whether cores are
     super- or subvirial. Report the same budget.
   - Uniform-sphere virial mass (2016ApJ...833..209O, general form): M_vir / Msun = 210 (R / pc)
     (Delta_v_FWHM / km s^-1)^2. Use the FWHM here; putting a dispersion in changes M_vir by 8 ln 2 = 5.55.
     2016ApJ...833..209O neglects magnetic fields, which can raise the virial mass; say so if you do too.
   - See `alma-gmc-decomposition-virial` for line-width and geometry choices. Report core-to-clump mass
     fractions with the flux-recovery caveat (2020ApJ...890...76N: 0.06 prestellar, 0.23 protostellar).

## Parameter defaults and ranges

Counts are my own count of the pack's "Key parameters" and excerpt lines, on-topic core and dense-gas papers
only (CO cloud, galaxy and blind-search papers excluded); entries taken from single cards are marked
"(card)" in `references/parameters.md`, which also lists the papers behind every count.

| Parameter | Common choice | Range seen | Papers (count) | Examples |
|---|---|---|---|---|
| astrodendro `min_value` | 3 sigma | 2-5 sigma, or absolute flux | 3 sigma: 7; 4 sigma: 3; 5 sigma: 2; 2 sigma: 2; absolute mJy/beam only: 1 | 2020ApJ...890...76N, 2020ApJ...896..110L, 2017MNRAS.464L..31H, 2020ApJ...894L..14L, 2024A&A...690A.185W, 2020ApJ...896...35J |
| astrodendro `min_delta` | 1 sigma | 1-5 sigma, or absolute flux | 1 sigma: 8; 1.5 sigma: 1; 2 sigma: 1; 3 sigma: 1; 5 sigma: 2; global noise: 1; absolute only: 1 | 2018ApJ...853..160C, 2018ApJ...856..147O, 2025ApJ...994..233Y, 2021ApJ...907L..15S, 2025ApJ...990...80K, 2024A&A...690A.185W |
| astrodendro `min_npix`, beam-area settings | 1 beam area | 0.5-2 beams | 1 beam: 3; ~0.5 beam: 2; 2 beams: 1; ambiguous "3 x theta_beam": 1 | 2020ApJ...894L..14L, 2020ApJS..251...14H, 2024MNRAS.527.5895D, 2018ApJ...856..147O |
| astrodendro `min_npix`, fixed pixel counts | n/a (depends on pixel size) | 5-74 px | 6 papers: 5, 15, 25, 40, 60, 74 px | 2025ApJ...994..233Y, 2020ApJ...896..110L, 2017MNRAS.464L..31H, 2023MNRAS.526.4402B |
| Leaf pruning by local rms | peak > 4-6 sigma, mean > 2 sigma | 4-6 sigma | 1 | 2020ApJS..251...14H |
| clumpfind lowest level / step (core papers) | 2-3 sigma / 2 sigma | 2-3 sigma / 2-3 sigma | 2 sigma/2 sigma: 2; 3 sigma/2 sigma: 2; step 3 sigma, level not stated: 1; absolute levels: 1 | 2016ApJ...833..209O, 2019ApJ...872..121U, 2020ApJ...890...76N, 2019MNRAS.483.1624B, 2018ApJ...853..160C |
| clumpfind peak cut | 5 sigma | 5 sigma | 1 | 2016ApJ...833..209O |
| Minimum core size | >= 1 beam | 0.5 beam to sqrt(2) beam minor axis | several | 2018ApJ...853..160C, 2020ApJ...894...87C |
| PB cut | 30% response | 30% | 1 | 2020ApJ...894L..14L |
| Dust temperature | 20 K uniform | 12-54 K fixed, or clump / host-core / PPMAP / L-M scheme | 20 K for catalog masses: 3 | 2018ApJ...853..160C, 2020ApJ...894...87C, 2018ApJ...856..147O (12 K), 2023MNRAS.526.4402B (54 K) |
| Opacity at 1.3 mm | 0.01 cm2/g (gas) | 5.95e-3 to 0.01 (gas); 0.867-0.899 (dust) | see step 4 | 2019ApJ...884...48C, 2018ApJ...855L..25K, 2020ApJS..251...14H, 2024A&A...690A.185W |
| Completeness by injection | same finder, synthetic Gaussians | point to beam-sized; 600 per bin | 5 (one from a card) | 2019MNRAS.483.1624B, 2020ApJ...894L..14L, 2025ApJ...994..233Y, 2020ApJS..251...14H, 2018ApJ...853..160C |
| CMF fit | MLE above completeness | MLE, binned chi2, cumulative LSQ | MLE: 2; binned chi2: 1; cumulative LSQ: 1; power law, method not stated: 2 | 2020ApJ...890...76N, 2020ApJ...894L..14L, 2018ApJ...853..160C, 2016ApJ...833..209O, 2020A&A...635A...2S, 2019ApJ...872..121U |
| Reported slope, logarithmic forms (dN/dlogM, dN/dlnM, N(>M)) | ~1.0-1.25 | 0.64-1.6 | 4 | 2018ApJ...853..160C, 2020ApJ...894L..14L, 2020A&A...635A...2S, 2016ApJ...833..209O (cumulative) |
| Reported slope, dN/dM form (native; dN/dlogM exponent in brackets) | n/a | 1.15-1.48 (0.15-0.48); 1.33 (0.33) | 2 | 2019ApJ...872..121U, 2020ApJ...890...76N |

## Software

Pack aggregates (software named in matched steps, all 67 papers, including off-topic ones): astrodendro 29,
clumpfind 25 (plus Starlink/CUPID variants 2), casa 6, getsources 4, cprops 3, fellwalker 2, heisenberg 2,
casa imfit 2, getimages 2, scimes 1, plfit 1, gaussclumps 1.

Many of the clumpfind hits are not core extraction: blind line searches (2018PASJ...70...36I,
2017PASJ...69...45H, 2018Natur.556..469M, 2021ApJ...908..163M), clumps in galaxies or lensed sources
(2015ApJ...806L..17S, 2017A&A...604A.117C, 2016ApJ...820..118Z, 2018ApJ...866..117C), GMCs in NGC 1068
(2017PASJ...69...18T), SN 1987A ejecta (2017ApJ...842L..24A), and HEISENBERG peak placement
(2019Natur.569..519K, 2025A&A...698A.296R). Counting only on-topic core papers in the pack lines (my count):
astrodendro about 15, clumpfind about 8, getsources 3, gaussclumps 1, SExtractor 1.

| Tool | Used for | Notes |
|---|---|---|
| astrodendro | Hierarchical segmentation; leaves = cores | Most-used finder among on-topic core papers here (about 15, my count), e.g. 2020ApJ...894L..14L, 2024A&A...690A.185W, 2025ApJ...994..233Y |
| clumpfind (IDL, Starlink CUPID) | Contour-based partition of all emission | Assigns all emission above the lowest level to clumps (general behaviour); found 83 cores vs 76 for the dendrogram and a much flatter slope in 2018ApJ...853..160C |
| getsources / getimages | Multi-scale extraction with background removal | Default parameters in 2018A&A...616L..10F; used in 2018A&A...618L...5N (card, settings not given); seed for imfit in 2019ApJ...884...48C |
| gaussclumps (CUPID) | Gaussian decomposition with background filter | Misses low-contrast cores larger than the filter (2017A&A...600A.141K) |
| CASA `imfit` | 2D Gaussian flux and size per core | Seeded by a finder (2019ApJ...884...48C; 2020ApJ...896..110L, card) |
| CASA `simobserve` + `tclean` | Completeness simulations | 2020ApJS..251...14H |
| plfit | Clauset MLE power-law with KS lower bound | 2020ApJ...894L..14L |
| SCIMES, CPROPS | Cloud-scale clustering of dendrogram structures | GMC work: see `alma-gmc-decomposition-virial` |

## Pitfalls

- **Algorithm choice changes the CMF.** Dendrogram vs clumpfind slopes of 1.24 vs 0.64 on the same data
  (2018ApJ...853..160C). Never compare a slope with another paper's without matching algorithm and
  convention.
- **Mixed slope conventions.** dN/dM exponents (2019ApJ...872..121U, 2020ApJ...890...76N) are one larger
  in magnitude than dN/dlogM or cumulative ones for the same distribution; convert before pooling or
  comparing with 1.35, and never "correct" a published value because it resembles Salpeter.
- **Threshold changes the sample.** 4 sigma to 3 sigma gave 76 to 125 cores (2018ApJ...853..160C);
  robust vs high-completeness pruning gave 285 vs 816 leaves (2020ApJS..251...14H).
- **Temperature and opacity dominate the mass error.** Temperature: 2018ApJ...853..160C assumes uniform 20 K
  and quotes factor ~2 mass uncertainty; 2018ApJ...855L..25K calls the temperature choice the largest
  uncertainty (up to factor ~2); 2020ApJ...894L..14L and 2019ApJ...884...48C say T_dust at core scales is
  unknown. Opacity: 2020ApJS..251...14H attributes its factor ~2 systematic to the dust opacity. A
  temperature that varies with mass changes the slope (step 8); temperatures assigned from clump L/M can
  build in trends with L/M (a caveat the 2026A&A...705A.100E and 2024A&A...690A.185W cards raise).
- **Line-selected masses carry abundance and excitation errors** (factor up to 2 from abundance in
  2019ApJ...872..121U); do not push them through a dust formula.
- **Completeness tests that are too easy.** Point or beam-sized injections overestimate completeness for
  extended cores (2019MNRAS.483.1624B, 2020ApJS..251...14H). Background filtering misses low-contrast cores
  (2017A&A...600A.141K).
- **Sensitivity limit is not completeness limit.** 2020ApJ...890...76N reports only 3 sigma mass
  sensitivity limits (0.7-1.4 Msun), with no measured completeness. Completeness depends on the selection:
  for the 20 km/s cloud 2020ApJ...894L..14L finds 90% completeness ~2 Msun with the 30% PB selection but
  ~5 Msun for sources above 5 sigma. Measure it for your own selection and fit above it.
- **Missing flux and unresolved cores.** Interferometer maps resolve out the clump (2016ApJ...833..209O,
  2018ApJ...856..147O); several cores have radii close to the beam, so sizes and densities are upper and
  lower limits (2018ApJ...856..147O, 2020ApJ...894...87C).
- **Multiplicity and resolution.** Unresolved multiplicity biases the CMF (2020A&A...635A...2S); cores may
  fragment at higher resolution (2018ApJ...853..160C).
- **Contamination of continuum flux.** Free-free at 1.2 mm not removed in 2020ApJ...896...35J; protostellar
  mass is not in the core mass (2025ApJ...990...80K); prestellar vs protostellar status often unknown
  (2020ApJ...894L..14L).
- **Small samples.** Too few cores for a robust CMF (2017MNRAS.464L..31H); trends on N = 4 (2025ApJ...994..233Y).
- **Settings the cards flag as not stated:** flux calibrator and flux-scale uncertainty, CASA and pipeline
  version, primary-beam correction details, line-free channels and clean thresholds (pack aggregate, the
  most frequent entries); CMF fitting method, binning and range (2016ApJ...833..209O, 2019ApJ...872..121U,
  2018ApJ...853..160C); clumpfind implementation and parameters beyond the thresholds
  (2016ApJ...833..209O, 2020ApJ...890...76N, 2016PASJ...68L...7T); astrodendro call details
  (2020ApJ...894L..14L); getsources parameters (2019ApJ...884...48C); size deconvolution procedure
  (2016ApJ...833..209O). Record all of these yourself.
- **CASA < 5.0 7m mosaic flux scaling** overestimated Band 6 fluxes by ~8% and Band 3 by ~2%
  (2019MNRAS.483.1624B); check the CASA version of archival products.

## Verification checks

What papers did:
- Second algorithm on the same map, comparing fluxes and sizes (2020ApJ...890...76N, 2024MNRAS.527.5895D).
- Parameter sweeps of the finder (2020ApJ...894L..14L, 2018ApJ...853..160C, 2020ApJS..251...14H appendix
  study of delta and kernel; 2017A&A...600A.141K filter widths 7.5-15").
- Injection-recovery completeness with the identical finder settings (2025ApJ...994..233Y,
  2020ApJ...894L..14L, 2019MNRAS.483.1624B, 2020ApJS..251...14H).
- Temperature Monte Carlo on the slope (2020A&A...635A...2S) and alternative temperature prescriptions
  (2020ApJ...894L..14L; Hi-GAL dust temperatures changed results by ~5-10% in 2024A&A...690A.185W, card).
- Excluding the most massive core and refitting over a different range (2018ApJ...853..160C).
- Single-dish combination to test missing flux (2018ApJ...856..147O).
- Uncertainty propagation on cores: bootstrap 100 iterations with a 5% floor (2024ApJ...966...51G);
  mass ~40% and column density ~35% (2020ApJ...890...76N).

What a careful referee adds:
- Report the slope in the dN/dlogM convention with its fit range and lower bound, and the MLE result even if
  a binned fit is shown; give the native convention too.
- Show the completeness curve itself and the injected size distribution.
- Propagate the flux calibration uncertainty into masses and say which CASA/pipeline version made the map.
- Overlay the catalog on the map so spurious leaves along filaments and at mosaic edges are visible.
- Run the finder on the sign-inverted map to estimate false positives (done in line-search papers such as
  2017A&A...604A.117C; rarely for continuum cores).
- Check that the slope survives a different temperature scheme and the second algorithm before comparing it
  with the IMF.

## Source cards

Full list: `references/sources.md`. Most informative for this technique:

- 2018ApJ...853..160C: dendrogram vs clumpfind, flux and number completeness, binned fit with upper limits
- 2020ApJ...894L..14L: astrodendro on non-PB-corrected maps, plfit MLE with KS lower bound, injection completeness
- 2020ApJ...890...76N: astrodendro and clumpfind side by side, eCDF MLE with confidence interval
- 2020A&A...635A...2S: temperature Monte Carlo and multiplicity bias on the slope
- 2020ApJS..251...14H: pruned dendrogram, simobserve completeness, robust vs complete catalogs
- 2019MNRAS.483.1624B: CUPID clumpfind, logistic completeness correction
- 2016ApJ...833..209O: clumpfind 2 sigma, cumulative CMF fit
- 2025ApJ...994..233Y: visual + dendrogram vetting, Gaussian injection completeness
- 2019ApJ...884...48C: getsources seeding imfit
- 2018A&A...618L...5N: getsources and PPMAP temperatures
- 2018A&A...616L..10F: getimages + getsources defaults
- 2017A&A...600A.141K: gaussclumps with background filter
- 2019ApJ...872..121U: 3D clumpfind cores in line cubes, CMF vs Orion A
- 2018ApJ...856..147O: dendrogram on ALMA+ACA, Herschel feather test
- 2024A&A...690A.185W: L/M-based temperatures, ALMAGAL cores
- 2026A&A...705A.100E: core populations vs clump properties
- 2020ApJ...894...87C: deconvolution cut and virial uncertainty budget
- 2021ApJ...907L..15S: dendrogram on uv-tapered images
- 2017MNRAS.464L..31H: small-sample caution
