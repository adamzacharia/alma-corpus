---
name: alma-spectral-index
description: "Measure millimetre/submillimetre spectral indices (alpha) between or within ALMA bands, convert them to a dust opacity (emissivity) index beta, and judge grain-growth claims against optical depth, scattering, free-free and calibration systematics. Use when asked for an alpha map, radial alpha profile, disk-integrated or source-integrated alpha, beta of disks, envelopes, cores or debris rings, or whether low alpha means mm-sized grains. Built from 233 ALMA papers (2012-2026)."
---

# Spectral index and dust emissivity index (alpha, beta)

Measures how flux scales with frequency, S_nu ∝ nu^alpha, between two or more ALMA (and often VLA or ATCA) bands,
and turns alpha into the dust opacity index beta (kappa ∝ nu^beta) to argue about grain growth. The two mistakes
that matter most: (1) treating low alpha as grain growth when the emission may be optically thick
(2018A&A...619A.161C: a spectral-index decrease may be optical thickness rather than grain growth), and (2) quoting
only the statistical error when the per-band flux-calibration error dominates (10% per band gives 0.42 on alpha in
2018A&A...616A..88V; about 0.4 in 2018ApJ...852..122H).

How this skill was built: every paper-specific claim below is taken from the `spectral-index` evidence pack.
Counts are either pack aggregates (said so) or my own count of the pack's per-paper lines (said so). A paper that
appears only in the pack's paper list is not used as evidence for any method detail. Many of the 233 tagged papers
use "alpha" or "beta" for something else (Fermi photon index, disk viscosity, Nuker profile, `frank`
hyperparameter, disk flaring index); those are ignored. Convention used here: S_nu ∝ nu^alpha (frequency). Some
papers use other conventions (S_nu ∝ nu^-alpha in 2017MNRAS.469L.123O); normalise before comparing.

## When to use

- Two or more continuum bands of the same source, and the question is alpha, beta, a_max or "grain growth".
- Radial alpha profiles of protoplanetary disks (2020ApJ...891...48H: 1.1 and 2.1 mm in 1 au annuli;
  2020ApJ...898...36L, a dual-wavelength ring study).
- Envelope dust opacity indices of protostars from two bands (2025A&A...700A.188C used 95 and 233 GHz).
- Debris-disk mm index and grain size-distribution slope q (2015ApJ...798..124R, 2017MNRAS.466.4201W,
  2019AJ....158..162F).
- Using alpha as one diagnostic, among others, of whether compact emission is dust, free-free or synchrotron in
  clusters, galaxy nuclei and stellar sources (2018ApJ...853..171G, 2021A&A...652A..98G, 2017ApJ...841..130A).
  Alpha alone does not classify a source; see step 8.
- Deciding which beta to adopt when only one band exists (adopted-beta counts in `references/parameters.md`).

## When not to use

| Situation | Use instead |
|---|---|
| Single band, you only need a dust mass | `dust-continuum-mass` skill (it covers kappa, T, gas-to-dust) |
| Many bands from far-IR to mm with T_dust free (galaxies, high z) | `sed-fitting` skill |
| You need to split dust from free-free/synchrotron at cm wavelengths | `free-free-synchrotron` skill first, then come back |
| You want ring/gap positions and widths, not alpha | `disk-substructure-profiles` or `uv-plane-fitting` |
| Full 2D/3D modelling of T, tau, scattering | `radiative-transfer-modelling` |
| Bands observed at different epochs on a variable source (stars, AGN, outbursts) | treat as `variability-time-domain` first; 2019ApJ...875...55W could not exclude short-lived mm flares, and 2020ApJ...894...76W could not rule out longer-timescale variability |

## Steps

1. **Pick the bands for lever arm, not convenience.**
   - Goal: keep the calibration term small. The error on alpha scales as 1/ln(nu1/nu2) (general practice).
   - Papers: adjacent B6 and B7 were called "not optimal" (2020MNRAS.496..394R, alpha 2.2 ± 0.5). Wider pairs in
     the pack (my count, 7 papers): 95/233 GHz (2025A&A...700A.188C), 1.1/2.1 mm (2020ApJ...891...48H),
     1.3/0.45 mm (2024A&A...689A.317G), 33/94.5 GHz (2015ApJ...813..118M), 9 to 349.5 GHz
     (2017ApJ...841..130A), 350 to 6600 um (2017MNRAS.466.4201W), 3 to 340 GHz (2024RMxAA..60..355R).
   - In-band alpha (one band, two sidebands or MFS) has a short lever arm: 218.0/232.6 GHz (2016Natur.535..258C;
     the pack writes its formula with the frequency ratio inverted, so check the sign convention), within Band 3
     (2015A&A...577L...4V, 1.71 ± 0.05).

2. **Calibrate, self-calibrate where justified, and build the continuum.**
   - Record the flux calibrator and adopted per-band uncertainty. Pack aggregates: "flux calibrator and flux
     scale uncertainty" or "flux scale uncertainty" is flagged as not stated in 10 cards (my sum of 3 phrasings),
     CASA version in 18 (plus 15 more in combined CASA/pipeline phrasings).
   - Line-free channels only. Check whether a flat continuum per spw is good enough: the fractional change across
     a window is about alpha × (Delta nu / nu) (general practice). 2024A&A...689A.317G found <1% for its own
     windows assuming alpha 2; compute it for yours and fit a sloped continuum if it is not small.
   - Self-calibrate only when the source S/N supports it and the model is reliable (general practice); check that
     flux and structure are preserved before and after. The pack gives no self-cal settings specific to alpha
     work (solution intervals are flagged as not stated in 13 cards, pack aggregate).

3. **Image both bands on a matched footing.**
   - Same uv range: 40-610 klambda in 2017MNRAS.467L.120M (the only explicit range in the pack). Choose the range
     from your own baselines: shortest common to longest common.
   - Same beam: CASA `imsmooth` to the coarser beam (2020ApJ...891...48H); convolve to a common 0.13-0.16"
     (2021A&A...652A..98G); convolve 94.5 GHz to the 33 GHz beam (2015ApJ...813..118M).
   - Same pixel grid: convolve and regrid before dividing (2015ApJ...813..118M).
   - CASA `tclean` with `deconvolver='mtmfs'`, `nterms=2` gives an in-band alpha image: 2018ApJ...852..122H
     (nterms=2, robust=0), 2018ApJ...853..171G (alpha from mtmfs maps; nterms not given in the pack).
   - Primary-beam correct before measuring fluxes, and set a PB cutoff: 2017MNRAS.466.4201W judged N/S
     asymmetries and vertical structure unreliable near the primary-beam edge. Treat the noise as spatially
     varying after correction (general practice).

4. **Measure alpha in the form the question needs.**
   - Integrated: aperture flux (0.3" radius in four bands, 2020MNRAS.496..394R), `imfit` Gaussian
     (2024Ap&SS.369...18M), or `uvmodelfit` (2020ApJ...894...76W). Then alpha = ln(S1/S2)/ln(nu1/nu2).
   - Pixel map: divide matched images where both bands pass an S/N cut (see table); 2017ApJ...841..130A also built
     the error map pixel by pixel.
   - Radial profile: deproject with fixed i and PA, average in annuli (1 au bins, i = 53.21 deg,
     PA = 57.17 deg in 2020ApJ...891...48H), then alpha = log(I1/I0)/log(nu1/nu0) per annulus.
   - Joint visibility fit with alpha as a free parameter: uniform prior 0-4, Metropolis-Hastings MCMC over three
     frequencies (2018ApJ...859..103W).
   - Many bands: weighted power-law fit (2017ApJ...841..130A, 2020MNRAS.496..394R); Bayesian MCMC with flat prior
     (2017MNRAS.466.4201W); SciPy `curve_fit` least squares (2019ApJ...875...55W, a brightness-temperature index
     in wavelength).

5. **Put the systematic error in.**
   - Adopted per-band calibration errors: 10% (my count, 5 papers: 2020ApJ...891...48H, 2018ApJ...869..158F,
     2018A&A...616A..88V, 2024A&A...689A.104D, 2020ApJ...892...99C), 15% (2020MNRAS.496..394R). 2025A&A...700A.188C
     quotes 0.1 on alpha from flux calibration.
   - Two-band error with fractional calibration errors f1, f2 and correlation rho (general practice):
     sigma_alpha^2 = (f1^2 + f2^2 - 2 rho f1 f2) / ln^2(nu1/nu2). Quadrature (rho = 0) is what the papers above
     assume; data sharing a calibrator or session can be correlated. The scale error is coherent across all pixels
     and annuli of one dataset, so in Monte Carlo draw one scale factor per dataset, not per pixel.
   - Report statistical and absolute errors separately (2018A&A...616A..88V gives 0.42 absolute from 10% per band).
   - Source selection by alpha significance is a per-paper choice: 2018ApJ...853..171G kept sources with
     |alpha| > 5 sigma(alpha) or sigma(alpha) < 0.1 and said completeness could not be quantified. That cut
     rejects real indices near zero, so pick a criterion for your own question and model its selection effect.

6. **Remove non-dust emission.**
   - Model free-free from cm data first: 2019ApJ...883...71C (HL Tau, ALMA + VLA) modelled the jet as 175 uJy at
     32.5 GHz, index 0.7, size 22 mas.
   - Extrapolate a long-wavelength free-free map to the dust band and subtract: 2016ApJ...833L...6C extrapolated
     **3 mm** emission to 870 um with index -0.118. This requires the dust contribution at 3 mm to be negligible
     (they computed S_3mm^dust < 0.1 mJy for beta = 1.7).
   - Fixed component indices seen: free-free -0.1 (2019MNRAS.483.1624B, 2017ApJ...849...90S, 2020ApJ...895L...2N),
     synchrotron -0.7 to -0.9 (2018ApJ...867...48I, 2017ApJ...849...90S, 2015ApJ...813..118M), dust 3.8
     (2017ApJ...849...90S). Test the non-thermal index (2015ApJ...813..118M tried -0.6 as well as -0.85).

7. **Convert alpha to beta, with the assumptions stated.**
   - Optically thin and Rayleigh-Jeans: beta = alpha - 2 (2015ApJ...798..124R, 2020ApJ...894...76W).
   - Outside RJ, optically thin, single temperature (general practice, exact for two bands):
     beta = alpha - ln[B_nu1(T)/B_nu2(T)] / ln(nu1/nu2). The form Delta alpha = x e^x/(e^x - 1) - 1 with
     x = h nu / k T is only a local (differential) approximation at one frequency. 2019A&A...626A..36D quote
     corrections Delta alpha = 0.06 at 100 K and 0.20 at 35 K (the pack does not say which formula or frequency).
   - Temperatures used: midplane 30 K and 18 K at two rings (2020ApJ...891...48H); 45 ± 5 K for a debris ring
     (2017MNRAS.466.4201W); midplane irradiated T, about 15 K at 50 au (2020ApJ...898...36L).
   - Optical depth: tau_nominal = -ln(1 - I_nu/B_nu(T)) (2020ApJ...891...48H). Before using it: convert Jy/beam
     to specific intensity in the same units as B_nu (divide by the beam solid angle), require 0 < I_nu/B_nu < 1,
     and remember it assumes an isothermal, beam-filling, absorption-only slab (general practice). Report it as
     nominal tau, or as a limit when those assumptions fail. 2020ApJ...891...48H took beta from the tau ratio only
     in optically thin parts (peak tau_nominal 0.94 and 0.70 at two rings, 1.1 mm).
   - Include scattering when tau is not small: 2020ApJ...891...48H used an analytic absorption plus scattering
     slab with DSHARP opacities (`dsharp_opac`), p = 3.5 (also 2.5, 1.5), a_min = 0.1 um, and found similar
     results with Birnstiel 2018 and Zhu 2019 formulae.
   - Count your free parameters. 2024ApJ...971..129C: two bands constrain four parameters only with priors.
     State the priors, rerun with different priors, and report the allowed region of (a_max, p, T) rather than a
     single a_max; 2020ApJ...891...48H aimed to show consistent parameter space, not precise grain sizes.

8. **Interpret.**
   - Alpha is a diagnostic, not a classifier. Values near or below 2 can come from optically thick dust,
     scattering, cold dust outside RJ (where B_nu is shallower than nu^2), free-free or synchrotron, or a mix of
     components (general practice). Use temperature, optical depth, morphology and cm data before naming the
     mechanism. 2021A&A...652A..98G compared alpha with dust vs free-free/synchrotron expectations;
     2018ApJ...853..171G cross-matched to HII, maser, X-ray and Spitzer catalogues before classifying.
   - ISM-like beta: 2018ApJ...852..122H assumed an ISM beta upper limit of 1.7; 2024A&A...691A.180F called 1.7
     typical for ice-coated grains in dense cores. 2025A&A...700A.188C (per its title) report envelope opacity
     indices that bridge ISM and disk values. As general practice, beta well below 1 is read as mm-size grains,
     but only after tau and scattering are ruled out (2018A&A...619A.161C caveat).
   - Debris disks: q = (alpha_mm - alpha_pl)/beta_s + 3 with beta_s = 1.8 ± 0.2 (2017MNRAS.466.4201W,
     2019AJ....158..162F); q from the Draine (2006) relation after beta = alpha - 2 (2015ApJ...798..124R).
     Normalise alpha_mm to the frequency convention first (see the Fomalhaut note in `references/parameters.md`).

## Parameter defaults and ranges

| parameter | common choice | range seen | papers (count) | examples |
|---|---|---|---|---|
| Band pair | widest pair available | adjacent B6/B7 to 9-349.5 GHz | my count: 7 wide-pair, 2 adjacent B6/B7, 2 in-band | 2025A&A...700A.188C, 2020ApJ...891...48H, 2020MNRAS.496..394R |
| Flux-cal error per band | 10% | 10% to 15% | my count: 10% in 5; 15% in 1 | 2018A&A...616A..88V, 2024A&A...689A.104D, 2020ApJ...892...99C, 2020MNRAS.496..394R |
| Resulting absolute error on alpha | about 0.4 (10% per band) | 0.1-0.42 | 3 | 2018A&A...616A..88V, 2018ApJ...852..122H, 2025A&A...700A.188C |
| Matched uv range | shortest common to longest common baseline | 40-610 klambda (one case) | 1 | 2017MNRAS.467L.120M |
| Common beam | coarser of the two | 0.13-0.16" in one survey | 3 | 2020ApJ...891...48H, 2021A&A...652A..98G, 2015ApJ...813..118M |
| Pixel S/N cut for alpha maps | 3 sigma in both bands | 2.5 to 20 | my count: 4 | 2018A&A...616A..88V (2.5), 2017ApJ...841..130A (3), 2015ApJ...813..118M (3), 2018A&A...619A.161C (20) |
| In-band alpha imaging | `mtmfs`, `nterms=2` | - | 2 (nterms stated in 1) | 2018ApJ...852..122H, 2018ApJ...853..171G |
| Briggs robust for alpha images | rarely stated | 0 in the one alpha paper that states it | 1 | 2018ApJ...852..122H |
| T for non-RJ correction | measured or modelled | 35-100 K | 1 | 2019A&A...626A..36D |
| Size distribution slope p | 3.5 | 1.5-3.5 tested | 1 (alpha paper) | 2020ApJ...891...48H |
| Minimum grain size | 0.1 um | - | 1 (alpha paper) | 2020ApJ...891...48H |
| beta_s (debris) | 1.8 ± 0.2 | - | 2 | 2017MNRAS.466.4201W, 2019AJ....158..162F |
| Adopted beta if not measured | 1.0 (disks, protostars); 1.8-2.0 (galaxies, clumps) | 0.4-2.0 | my count: 82 single-value adoptions, see references | 2016ApJ...828...46A, 2020ApJ...892...66M, 2020A&A...635A...2S |
| Free-free index | -0.1 | -0.118 to -0.1 | 4 | 2019MNRAS.483.1624B, 2016ApJ...833L...6C |
| Synchrotron index | -0.8 (4 papers) | -0.7 to -0.9 | 7 | 2020A&A...642A.155Z, 2024ApJ...961..120C, 2015ApJ...813..118M, 2018ApJ...867...48I |

Per-paper beta adoption, measured alpha values and the full list of thresholds are in `references/parameters.md`.

## Software

Counts are the pack's software aggregate (mentions in matched steps, not unique papers). Mapping used: CASA row =
`casa` 33 + `casa imfit` 2 + `casa uvmodelfit` 1; mcfost row = `mcfost` 2 + `mcfost-python` 1; SciPy row = `scipy` 1
+ `scipy curve_fit` 1. Left out as off-topic for alpha work: `make3fglxml` 1 (Fermi), `xclass` 1 and `magix` 1
(line fitting), `tiny tim` 1, `mge` 1, `fargo` 2 and `la-compass` 1 (hydro), `fsps` 1, `prospector` 1, `parrot` 1,
`hyper` 1, `moreli` 1, `planetalp` 1, `mcmc (unnamed)` 1. The bibcodes in the last column are only those the
pack ties to the tool; other uses are aggregate mentions without a named paper.

| Tool | Pack count | Used for (bibcode where the pack ties the tool to the step) |
|---|---|---|
| CASA (incl. imfit, uvmodelfit) | 36 (33 + 2 + 1) | `imsmooth` beam matching (2020ApJ...891...48H), mtmfs alpha maps (2018ApJ...853..171G), convolve/regrid (2015ApJ...813..118M), `imfit` (2024Ap&SS.369...18M), `uvmodelfit` (2020ApJ...894...76W) |
| emcee | 9 | visibility disk models with beta fixed at 0.4, separate from the alpha measurement (2015ApJ...798..124R); the other pack emcee steps are not tied to an alpha measurement |
| GILDAS | 4 | uv-plane continuum subtraction and CLEAN (2024A&A...689A.317G) |
| MIRIAD | 3 | point-source `IMFIT` for in-band cm indices (2020PASJ...72...62A) |
| RADMC-3D, mcfost, DIAD | 3, 3, 2 | disk forward models; the pack ties RADMC-3D to SED and CPD-mass models (2024ApJ...966...59S, 2019MNRAS.488.1005P), not to an alpha step |
| Frankenstein (`frank`) | 3 | 1D visibility profiles; the `alpha`/`wsmooth` values in 2024A&A...689A.104D and 2024ApJ...971..129C look like frank hyperparameters, not spectral indices (my reading; the pack does not name the tool for them) |
| galario, dynesty | 2, 2 | visibility forward modelling and nested sampling (2019A&A...628A.100D, an SZ model, not dust alpha) |
| SciPy (incl. curve_fit) | 2 | least-squares power-law fits (2019ApJ...875...55W) |
| dsharp_opac | 1 | DSHARP opacities for grain-size constraints (2020ApJ...891...48H) |
| STATCONT | 1 | continuum level from line-rich spectra (2020A&A...644A..84M) |
| dust_emissivity | 1 | MCMC modified-blackbody T and beta (2024A&A...684A..56K) |
| uvplot, uvmem, protomidpy | 1 each | visibility plotting, imaging and profile tools (not tied to an alpha step) |
| lifelines | 2 | survival statistics with censored values (not tied to a paper in the pack) |
| CIGALE, cmcirsed, MAGPHYS, EAZY | 3, 1, 2, 2 | galaxy SED fits (2025A&A...698A.204H, 2020ApJ...892...66M); see `sed-fitting` |

## Pitfalls

- **Calibration, not noise, sets the error.** Absolute alpha uncertain by about 0.4 (2018ApJ...852..122H,
  2018A&A...616A..88V); absolute flux scale uncertain, affecting the spectral index (2015ApJ...812..126C). Some
  papers leave calibration out of the fit uncertainty (2021A&A...656A..46M, 2020ApJ...892...99C). Relative alpha
  changes across one disk are more robust than the absolute level, since the scale offset is common (general
  practice).
- **Short lever arm.** Adjacent B6/B7 gave alpha 2.2 ± 0.5 (2020MNRAS.496..394R); 231/266 GHz gave
  1.18 ± 0.65 (2017NatAs...1..709O).
- **Optical depth mimics grain growth.** A spectral-index decrease may be optical thickness rather than grain growth
  (2018A&A...619A.161C); dust masses are lower limits if emission is optically thick (2024ApJ...966...59S,
  2025ApJ...993..120H).
- **Scattering** is part of the emergent intensity at high optical depth; 2020ApJ...891...48H included it with an
  analytic slab.
- **Temperature, tau and beta are degenerate.** Temperature, flux calibration and degeneracies prevented precise
  grain sizes (2020ApJ...891...48H); temperature poorly constrained (2020ApJ...892...99C); 2015ApJ...810L...7V
  tested 24 and 200 K against a uniform 60 K. Two bands need priors for four parameters (2024ApJ...971..129C).
- **Different spatial filtering per band.** Recoverable scale depends on each dataset: 2016ApJ...833L...6C
  noted structures above about 12" undersampled in Band 7; ALMA-only recovered about 18% of the flux
  (2014ApJ...795L..25R); ALMA flux was low without ACA data (2024RMxAA..60..355R); about 70% recovery vs APEX
  (2020MNRAS.496..394R). Match uv ranges, compare with single-dish flux, or combine with ACA/TP.
- **Primary-beam edge.** Structure near the PB edge is unreliable (2017MNRAS.466.4201W).
- **Non-simultaneous bands on variable sources.** Short mm flares cannot be excluded (2019ApJ...875...55W);
  longer-timescale variability not ruled out (2020ApJ...894...76W); 2026ApJ..1004..126K had to assume the index
  does not change with time.
- **Limits and small samples.** Treat non-detections in one band as censored (survival statistics, general
  practice). Index maps were possible for only 3 of the GATOS sources (2021A&A...652A..98G); 2024ApJ...961..120C
  had an index from two points plus limits.
- **Map artefacts and resolution.** 17 GHz left out of index maps for artefacts (2017ApJ...841..130A); limited
  resolution smears structure and spectral index errors may be underestimated (2017A&A...602L..10O); resolution
  washes out alpha variations (2020ApJ...898...36L); flux systematics from differing beams (2017ApJ...841..130A).
- **Model choice.** The fitted function changes ring results and uncertainties may be underestimated
  (2020ApJ...898...36L); equal weighting of frequencies in a joint fit may not reflect each dataset
  (2018ApJ...859..103W).
- **Settings the cards rarely state** (pack aggregates, my sums over phrasings): CASA version 18 (+15 combined
  with pipeline), self-cal solution intervals 13 (+9 with iterations), line-free channels about 41, image and
  cell size 12, flux calibrator and uncertainty 10, primary-beam correction 7, CLEAN threshold/mask/niter 8,
  uvmodelfit starting parameters 3, continuum bandwidth 2. Write down every one of these you used, separating
  what you chose from defaults you inherited.

## Verification checks

What papers did:
- Compare a disk-averaged index with the literature (2020ApJ...891...48H: 2.7 ± 0.2 vs 2.94 ± 0.44).
- Swap the analytic grain-size formula and the temperature structure (2020ApJ...891...48H: Birnstiel 2018,
  Zhu 2019, McClure temperatures).
- Change priors (Jeffreys vs uniform, negligible change) and check a uniform-disk fit against `uvmodelfit`
  (2018ApJ...859..103W).
- Vary the non-thermal index (2015ApJ...813..118M: -0.6 vs -0.85).
- Compare in-band and cross-band indices (2020PASJ...72...62A: -0.50 in-band vs -0.37 ATCA+ALMA); split a band
  in halves (2024RMxAA..60..355R: 1.3 ± 0.9 within 2-4 GHz vs 0.69 ± 0.03 from 3 to 340 GHz).
- Test alternative beta and T (2020ApJ...892...66M: T 15-35 K, beta 1.5-2.0; 2024A&A...691A.180F: beta from
  3 mm/2 mm fluxes lowers N(H2) by about 3; 2014ApJ...795L..25R: beta 1.0-2.0 scanned).
- Check flux recovery against single-dish data (2020MNRAS.496..394R, about 70%).
- Compare q with independent estimates and the collisional value 3.51 (2017MNRAS.466.4201W).
- Rely on wide frequency coverage for robustness (2017ApJ...841..130A, 9 to 349.5 GHz).

What a careful referee adds:
- Absolute and relative alpha errors given separately, per-band flux-cal values named, correlation stated.
- Bands at matched uv range, beam, pixel grid and astrometric registration; epochs close enough for the source.
- Peak brightness temperature compared with a physical temperature to test optical thickness (general practice).
- Free-free estimated or bounded from cm data before calling alpha "dust".
- Any beta < 1 claim shown to survive tau and scattering corrections, with T and priors stated and varied.

## Source cards

Full list: `references/sources.md` (generated). Most informative for this technique:

- 2020ApJ...891...48H: B4/B6 radial alpha, imsmooth, 10% per band, nominal tau, DSHARP opacities, scattering
- 2018A&A...616A..88V: S/N < 2.5 mask, 10% per band gives 0.42 on alpha
- 2018ApJ...852..122H: mtmfs nterms=2, robust 0, ±0.4 absolute, ISM beta limit 1.7
- 2018A&A...619A.161C: S/N > 20 both bands; optical depth vs grain growth caveat
- 2018ApJ...859..103W: joint MCMC visibility fit with alpha free, prior 0-4, prior test
- 2018ApJ...853..171G: mtmfs alpha for compact sources, 5 sigma selection, incomplete catalogue
- 2015ApJ...813..118M: convolve and regrid, 3 sigma pixels, fixed and tested non-thermal index
- 2017ApJ...841..130A: weighted power law 9-349.5 GHz, pixel error map, artefact band dropped
- 2015ApJ...798..124R: debris alpha 2.42, beta = alpha - 2, q via Draine 2006
- 2017MNRAS.466.4201W: debris alpha_mm and q with beta_s; PB-edge caveat; sign convention issue
- 2019A&A...626A..36D: non-RJ correction values
- 2020MNRAS.496..394R: adjacent bands give poor alpha; 15% calibration; flux recovery
- 2016ApJ...833L...6C: 3 mm free-free extrapolated to 870 um
- 2017MNRAS.467L.120M: matched uv range, free-free point sources
- 2024ApJ...971..129C: two bands vs four parameters
- 2021A&A...652A..98G: alpha maps of AGN tori at a common resolution
- 2025A&A...700A.188C: envelope opacity index, 95/233 GHz, 0.1 calibration term
- 2019ApJ...883...71C: HL Tau ALMA+VLA, free-free jet model
