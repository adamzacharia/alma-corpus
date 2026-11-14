---
name: alma-spectral-index
description: "Measure millimetre/submillimetre spectral indices (alpha) between or within ALMA bands, convert them to a dust opacity (emissivity) index beta, and judge grain-growth claims against optical depth, scattering, free-free, AME and calibration systematics. Use when asked for an alpha map, radial alpha profile, disk-integrated or source-integrated alpha, beta of disks, envelopes, cores or debris rings, or whether low alpha means mm-sized grains. Built from 640 ALMA papers (2012-2026)."
---

# Spectral index and dust emissivity index (alpha, beta)

Measures how flux scales with frequency, S_nu ∝ nu^alpha, between two or more ALMA (and often VLA or ATCA) bands,
and turns alpha into the dust opacity index beta (kappa ∝ nu^beta) to argue about grain growth. The two mistakes
that matter most: (1) treating low alpha as grain growth when the emission may be optically thick or scattering
(2023MNRAS.518.6092L: the DS Tau inner disk is optically thick even at 2.9 mm, so alpha cannot constrain grain size
there; 2021ApJ...909..212K: a central alpha below 2 may come from optically thick scattering), and (2) quoting only
the statistical error when the per-band flux-calibration error dominates (10% per band gives 0.42 on alpha in
2018A&A...616A..88V and about 0.4 in 2025A&A...694L..15H).

How this skill was built: every paper-specific claim comes from the rebuilt `spectral-index` evidence pack (640
papers). Counts are pack aggregates or my own count of the pack's per-paper lines, and each says which and how. A
paper the pack only lists by title is used only where its methods card states the value verbatim, marked "(card)".
Many tagged papers use "alpha" or "beta" for something else (photon index, disk viscosity, Nuker profile, `frank`
hyperparameter, flaring index, wind exponent, UV slope, alpha_CO, rate coefficients); those are ignored. Convention:
S_nu ∝ nu^alpha. Some papers use S_nu ∝ nu^-alpha (2017MNRAS.469L.123O, 2021Galax...9..115D); normalise first.

## When to use

- Two or more continuum bands of the same source, and the question is alpha, beta, a_max or "grain growth".
- Radial alpha profiles of protoplanetary disks: alpha_mm(R) = log[I1(R)/I2(R)]/log(nu1/nu2) from B3/B6 images at a
  common beam (2023MNRAS.518.6092L, DS Tau, alpha about 2.1 inside to about 3 outside).
- Envelope and streamer opacity indices of protostars: 95 and 233 GHz (2025A&A...700A.188C), 230 and 100 GHz with a
  T(r) law (2024A&A...682A..61C), multiband radial and angular sectors (2023A&A...676A...4C), outflow cavity walls
  at 100.6 and 225.4 GHz (2025A&A...698L..16S).
- Debris-disk mm index and grain size-distribution slope q (2017MNRAS.466.4201W, 2019AJ....158..162F,
  2026A&A...705A.196H).
- Using alpha as one diagnostic, among others, of whether compact emission is dust, free-free, synchrotron or AME in
  clusters, cores, jets and stellar sources (2018ApJ...853..171G, 2024A&A...686A.122A, 2017ApJ...841..130A,
  2025A&A...694L..15H). Alpha alone does not classify a source; see step 8.
- Deciding which beta to adopt when only one band exists (196-paper census in `references/parameters.md`).

## When not to use

| Situation | Use instead |
|---|---|
| Single band, you only need a dust mass | `dust-continuum-mass` skill (it covers kappa, T, gas-to-dust) |
| Many bands from far-IR to mm with T_dust free (galaxies, high z) | `sed-fitting` skill |
| You need to split dust from free-free/synchrotron/AME at cm wavelengths | `free-free-synchrotron` skill first, then come back |
| You want ring/gap positions and widths, not alpha | `disk-substructure-profiles` or `uv-plane-fitting` |
| Full 2D/3D modelling of T, tau, scattering | `radiative-transfer-modelling` |
| Bands observed at different epochs on a variable source (stars, AGN, outbursts) | treat as `variability-time-domain` first; 2019ApJ...875...55W could not exclude short-lived mm flares, 2015ApJ...815...64W called its broadband inference uncertain because bands were not contemporaneous, and 2026A&A...712A.244H had bands spread over a week |

## Steps

1. **Pick the bands for lever arm, not convenience.**
   - Goal: keep the calibration term small. The error on alpha scales as 1/ln(nu1/nu2) (general practice).
   - Wide-pair examples: 95/233 GHz (2025A&A...700A.188C), 110.2/217.0 GHz (2023ApJ...948..110Y), 1.3/2.9 mm
     (2023MNRAS.518.6092L), 0.87 to 6.8 mm in four bands (2024A&A...683A.141R), 9 to 349.5 GHz (2017ApJ...841..130A).
   - Adjacent or in-band pairs have a short lever arm: B6/B7 (2025MNRAS.538.2358S), 218/233 GHz (2021ApJ...923..121Y),
     94.05/106.05 GHz (2024A&A...689L...5M, alpha constrained only within about 30 au); sidebands at 91.5/103.5 GHz
     gave alpha about -5 ± 4 (2015ApJ...815...64W).

2. **Calibrate, self-calibrate where justified, and build the continuum.**
   - Record the flux calibrator, adopted per-band uncertainty and CASA version (often missing; see Pitfalls).
   - Line-free channels only. Check whether a flat continuum per spw is good enough: the fractional change across
     a window is about alpha × (Delta nu / nu) (general practice). 2024A&A...689A.317G found <1% for its own
     windows assuming alpha 2; compute it for yours and fit a sloped continuum if it is not small.
   - Self-calibrate only when the source S/N supports it and the model is reliable (general practice); check that
     flux and structure are preserved. Self-cal can move the phase centre: 2026A&A...712A.244H checked band-to-band
     alignment on the non-self-calibrated QA2 images.

3. **Image both bands on a matched footing.**
   - Same uv range (3 papers, my count): 20-1500 klambda, then smoothed to 2" (2018ApJ...859...86T); 40-610 klambda
     (2017MNRAS.467L.120M); 50-1000 klambda with a taper so beam areas agree within a few percent
     (2025ApJ...985..148L). Choose the range from your own baselines: shortest common to longest common.
     Image-plane comparison without uv matching was justified in 2023MNRAS.518.6092L because uv sampling was similar
     and the maximum recoverable scales (about 1.8" and 2.6") were far larger than the 0.5" disk.
   - Same beam (9 pack papers + 3 cards, my count; list in `references/parameters.md` section 3): Band 6 convolved
     to the Band 3 beam (2024ApJ...961....4B), common [0.13", 0.09"] (2023MNRAS.518.6092L), per-spw `imsmooth`
     (2026A&A...712A.244H). Never restore a band finer than its data support: a forced 0.3" beam super-resolved a
     5 GHz map (2021ApJ...918...76C).
   - Same pixel grid and registration: regrid before dividing (general practice); 2023ApJ...945...40C warns that
     misalignment between frequencies and steep brightness gradients cause spectral-index artefacts.
   - MTMFS spectral-index imaging, CASA `tclean` with `deconvolver='mtmfs'`, `nterms=2`. Within one band: 3 mm maps
     of compact sources (2018ApJ...853..171G, nterms not given). Across bands: a combined B6+B7 image at robust 0.0
     (2015ApJ...808L...3A) and all 12 m data combined as a cross-check (2025A&A...702A.276P, central-pixel alpha
     0.57 ± 0.23 vs 0.56 ± 0.11 from per-band fits). In-band maps can be too noisy to use (2024ApJ...961....4B).
     Robust for alpha imaging is rarely stated: 0 (2018ApJ...852..122H, 2015ApJ...808L...3A); 0.5, 0 and -0.5 tested
     (2025A&A...698A.165A).
   - Primary-beam correct before measuring fluxes, and set a PB cutoff: 2017MNRAS.466.4201W judged N/S asymmetries
     and vertical structure unreliable near the primary-beam edge; `frank` profiles ignore the primary beam
     (2026A&A...705A.196H). Treat the noise as spatially varying after correction (general practice).

4. **Measure alpha in the form the question needs.** Keep integrated fluxes (Jy) and peak intensities (Jy/beam)
   apart; a peak-intensity index is only comparable between bands at the same beam (general practice).
   - Integrated-flux index: curve-of-growth total flux, with the compact inner-disk flux checked against CASA
     `imfit` (2025MNRAS.538.2358S). Then alpha = ln(S1/S2)/ln(nu1/nu2).
   - Peak-intensity index: 2024ApJ...961....4B measured both integrated contour flux and brightest-pixel intensity,
     and used the brightest-pixel values at the 3 mm positions, with Band 6 convolved to the Band 3 beam and limits
     for single-band detections. Do not mix a Jy/beam peak in one band with a total flux in the other.
   - Pixel map: divide matched images where both bands pass an S/N cut (see table); 2017ApJ...841..130A also built
     the error map pixel by pixel.
   - Radial profile: deproject with fixed i and PA, average on ellipses, take alpha per annulus (1 au bins,
     i = 53.21 deg, PA = 57.17 deg in 2020ApJ...891...48H; i = 67.58 deg, PA = 159.62 deg in 2023MNRAS.518.6092L).
     `frank` profiles at matched resolution are an alternative (2025MNRAS.538.2358S, 2024ApJ...974..306S).
   - Joint visibility fit with alpha free: uniform prior 0-4, Metropolis-Hastings MCMC over three frequencies
     (2018ApJ...859..103W); uniform prior -5 to 5 with 5000 Monte Carlo draws of a Gaussian(1, 0.1) ALMA
     calibration factor (2025ApJ...979..142N).
   - Many bands or spws: weighted power-law fit (2017ApJ...841..130A); SciPy `curve_fit` (2025A&A...702A.276P); a
     log-space linear fit over 12 spws with a log-parabola checked by BIC (2026A&A...712A.244H).
   - Faint diffuse emission: uv-plane regression against a template image (2026A&A...707A.255C). Its simulations
     recovered an input alpha 0 with a pure chi-square template but gave -0.26 ± 0.09 with entropy regularisation,
     so test any regularised imager on simulated data before trusting its alpha.

5. **Put the systematic error in.**
   - Adopted per-band calibration errors: see the table below (ledger in `references/parameters.md` section 4);
     10% in every band is most common (17 papers, e.g. 2020ApJ...891...48H); 5% at B3-B6 and 10% at B7 in
     2023A&A...676A...4C; 5-20% by band in 2020ApJ...905...89Y, which does not tie values to instruments in the pack.
   - Resulting alpha errors: 0.42 (2018A&A...616A..88V), about 0.4 (2025A&A...694L..15H), 0.1 at 95/233 GHz
     (2025A&A...700A.188C), 0.083 from 5% at B3 and 10% at B7 (2024ApJ...974L..25D).
   - Two-band error with fractional calibration errors f1, f2 and correlation rho (general practice):
     sigma_alpha^2 = (f1^2 + f2^2 - 2 rho f1 f2) / ln^2(nu1/nu2). Quadrature (rho = 0) is what the papers above
     assume; data sharing a calibrator or session can be correlated. The scale error is coherent across all pixels
     and annuli of one dataset, so in Monte Carlo draw one scale factor per dataset, not per pixel
     (2025ApJ...979..142N). 2024MNRAS.527.9668H notes the scale errors shift profiles but not their relative shape.
   - Report statistical and absolute errors separately. Some papers leave calibration out of the main fit and test
     it afterwards (2023MNRAS.518.6092L reran with about 10% per band); 2024A&A...682A..61C put 5% systematic on top
     of a statistical beta error.
   - Source selection by alpha significance is a per-paper choice: 2018ApJ...853..171G kept sources with
     |alpha| > 5 sigma(alpha) or sigma(alpha) < 0.1 and said completeness could not be quantified. That cut rejects
     real indices near zero, so pick a criterion for your own question and model its selection effect.

6. **Remove non-dust emission.**
   - Model free-free from cm data first: 2019ApJ...883...71C (HL Tau, ALMA + VLA) modelled the jet as 175 uJy at
     32.5 GHz, index 0.7, size 22 mas.
   - Extrapolate a long-wavelength free-free map to the dust band and subtract: 2016ApJ...833L...6C extrapolated
     **3 mm** emission to 870 um with index -0.118. This requires the dust contribution at 3 mm to be negligible
     (they computed S_3mm^dust < 0.1 mJy for beta = 1.7).
   - The reverse: extrapolate the dust band down and subtract. 2024ApJ...974..243N scaled 261 GHz to 100 GHz with
     index 4 (3.8 changed the cold-dust flux by about 4%); 2025MNRAS.538.2358S extrapolated the B6-B7 dust index
     (2.4 ± 0.3) to Band 3 and attributed the inner-disk excess (about 36.8 uJy) to free-free.
   - With cm or Band 1 data, check for anomalous or excess microwave emission (AME/EME), not only free-free and
     synchrotron. In NGC 4725 B free-free gave only 25% of the 30 GHz emission, with AME dominating
     (2020ApJ...905L..23M); the rho Oph W filament has a Band 1 EME index of -0.78 ± 0.05 (2026A&A...707A.255C). A
     negative index there need not mean synchrotron. 2015ApJ...813..118M assumed AME negligible; say so if you do.
   - Debris disks: fit, subtract or bound the stellar photosphere in each band before deriving the belt index, and
     propagate its uncertainty. 2026A&A...705A.196H subtracted stellar flux from the real visibilities as a constant
     offset, with target-specific exceptions (none for HD 109573, the SED flux for HD 32297).
   - Fixed component indices (my count; ledger in `references/parameters.md` section 5): free-free -0.1 (11 papers);
     ionised jets 0.6 (2017ApJ...840...32T), 0.4 thick or -0.1 thin (2025A&A...702A..18D); synchrotron fiducial
     -0.68 to -0.9 in 20 papers, separate from explored ranges reaching -0.6 (2021A&A...654A..24B) and -1.5
     (2021MNRAS.503.1174K); dust 3.75-4. Vary the fixed index you adopt and report the change.

7. **Convert alpha to beta, with the assumptions stated.**
   - Optically thin and Rayleigh-Jeans: beta = alpha - 2 (2020ApJ...894...76W, 2026A&A...709A.173M,
     2025A&A...698A.165A). 2025A&A...699A.373F used alpha = 2 if thick and beta + 2 if thin, neglecting
     self-scattering.
   - Outside RJ, optically thin, single temperature, and negligible background (general practice, exact for two
     bands): beta = alpha - ln[B_nu1(T)/B_nu2(T)] / ln(nu1/nu2). If the background is not negligible (cold dust, high
     z), replace B_nu(T) by B_nu(T) - B_nu(T_bg) and use rest-frame frequencies in both bands; 2020ApJ...905...89Y
     subtracted the 2.73 K CMB and 2023MNRAS.523.4654T fitted CMB-corrected greybodies at z = 4.4. The form
     Delta alpha = x e^x/(e^x - 1) - 1 with x = h nu / k T is only a local (differential) approximation.
     2019A&A...626A..36D quote Delta alpha = 0.06 at 100 K and 0.20 at 35 K (the pack does not say which formula or
     frequency). 2026MNRAS.552g1700S used the full Planck function.
   - Temperatures used (10 papers, my count; list in `references/parameters.md` section 3): midplane 30 K and 18 K
     at two rings (2020ApJ...891...48H); T(r) = 38 K (L/Lsun)^0.2 (r/100 au)^-0.4, 21 to 8 K over 600-4000 au
     (2024A&A...682A..61C); 20, 14.7 and about 30 K tried (2021A&A...649A.122P). If T is taken as exact,
     Delta beta = Delta alpha (2023A&A...676A...4C, 2024A&A...682A..61C); say so, because it hides the T error.
   - Optical depth (general practice): tau_nominal = -ln(1 - I_nu/B_nu(T)), with the same background condition as
     above (else use I_nu/[B_nu(T) - B_nu(T_bg)]). Convert Jy/beam to specific intensity in the same units as B_nu,
     require 0 < I_nu/B_nu < 1, and remember it assumes an isothermal, beam-filling, absorption-only slab. Report it
     as nominal tau, or as a limit when those assumptions fail. Where the disk is optically thick, T_d can be set to
     the brightness temperature (2021ApJ...923..121Y).
   - Include scattering when tau is not small: 2020MNRAS.496..169L used an isothermal plane-parallel slab with
     scattering; 2020ApJ...905...89Y fitted T_d, tau_100GHz and beta per position but left scattering out and said
     the values depend on the adopted absorption coefficient. DSHARP opacities with p = 3.5 appear in 4 alpha papers
     (my count: 2020ApJ...891...48H, which also tested p = 2.5 and 1.5 with a_min = 0.1 um; 2023ApJ...948..110Y,
     which gridded a_max 10 um-1 cm and Sigma_d 0.001-10 g/cm2; 2023MNRAS.518.6092L; 2024A&A...682A..61C).
     2021ApJ...923..121Y compared DSHARP with a 2.3 (nu/230 GHz)^0.4 cm2/g law.
   - Count your free parameters. Two bands cannot fix T, tau (or Sigma_d), a_max and p together without priors
     (general practice). State the priors, rerun with different priors and opacity models, and report the allowed
     region of (a_max, p, T) rather than a single a_max. Evidence: 2023MNRAS.518.6092L reran everything with a
     second opacity model and found the gap-ring grain-size jump depends on it; 2025MNRAS.538.2358S notes its
     model a_max scales linearly with the assumed gas surface density; 2013ApJ...777...92S broke the beta-T
     degeneracy only by requiring consistency with the compact source size (beta about 0.6, T about 45 K).

8. **Interpret.**
   - Alpha is a diagnostic, not a classifier. Values near or below 2 can come from optically thick dust,
     scattering, cold dust outside RJ, free-free, synchrotron, AME, or a mix (general practice;
     2021ApJ...909..212K for scattering). Use temperature, optical depth, morphology and cm data before naming the
     mechanism. 2018ApJ...853..171G cross-matched to HII, maser, X-ray and Spitzer catalogues before classifying;
     2024ApJ...961....4B modelled an optically thick sphere inside thin dust to predict alpha. Paper-specific cuts
     exist (2024A&A...686A.122A: below 0.5 free-free dominated, 0.5-2 contaminated, above 2 dust dominated;
     2015ApJ...815...64W: thermal if alpha >= 1.5); treat them as that paper's scheme, not a rule.
   - ISM-like beta: 2018ApJ...852..122H assumed an ISM beta upper limit of 1.7, and 2021MNRAS.501.4317P used
     beta_ISM = 1.7. 2025A&A...700A.188C (per its title) report envelope opacity indices that bridge ISM and disk
     values. Measured low value: beta = 0.2 ± 0.1 from four bands in AB Aur (2024A&A...683A.141R, optically thin,
     T = 39 K assumed). As general practice, beta well below 1 is read as mm-size grains, but only after tau and
     scattering are ruled out.
   - Debris disks: q = (alpha_mm - alpha_pl)/beta_s + 3 with beta_s = 1.8 ± 0.2 (2017MNRAS.466.4201W,
     2019AJ....158..162F); 2026A&A...705A.196H fitted beta from B6 and B7 with beta_s = 1.8 and got beta = 0.3 ± 0.2,
     q = 3.17 ± 0.11 for HD 107146. Normalise alpha_mm to the frequency convention first (Fomalhaut note in
     `references/parameters.md`).

## Parameter defaults and ranges

| parameter | common choice | range seen | papers (count) | examples |
|---|---|---|---|---|
| Band pair | widest pair available | in-band 94/106 GHz to 9-349.5 GHz | examples only (step 1) | 2025A&A...700A.188C, 2023MNRAS.518.6092L, 2024A&A...689L...5M |
| Flux-cal error per band | 10% | 5% to 20% (instrument split for 20% not given) | my count: 10% in 17; 5/10% by band in 5; 5% in 3; 15% in 1; 5-20% in 1 | 2018A&A...616A..88V, 2023A&A...676A...4C, 2020ApJ...905...89Y |
| Resulting absolute error on alpha | about 0.4 (10% per band, nearby bands) | 0.083-0.42 | my count: 4 | 2018A&A...616A..88V, 2025A&A...694L..15H, 2025A&A...700A.188C, 2024ApJ...974L..25D |
| Matched uv range | shortest common to longest common baseline | 20-1500, 40-610, 50-1000 klambda | my count: 3 | 2018ApJ...859...86T, 2017MNRAS.467L.120M, 2025ApJ...985..148L |
| Common beam | coarser of the bands | 35 mas to 2.7" | my count: 9 pack + 3 card | 2024ApJ...961....4B, 2023MNRAS.518.6092L, 2024MNRAS.527.1444A |
| S/N cut for alpha maps or fits | 3 sigma in each band | 2 to 20 | my count: 12 (3 sigma in 6) | 2025A&A...703A..82S (2), 2018A&A...616A..88V (2.5), 2025A&A...698L..16S (3), 2023ApJ...948..110Y (4), 2018A&A...619A.161C (20) |
| MTMFS spectral-index imaging | `mtmfs`, `nterms=2` | within-band and combined-band | my count: 4 used, 1 too noisy | 2018ApJ...853..171G, 2015ApJ...808L...3A, 2025A&A...702A.276P, 2024ApJ...961....4B |
| Briggs robust for alpha imaging | rarely stated | 0; 0.5/0/-0.5 tested | my count: 3 | 2018ApJ...852..122H, 2015ApJ...808L...3A, 2025A&A...698A.165A |
| T for non-RJ correction or tau | measured or modelled T(r) | 8-100 K | my count: 10 (step 7) | 2019A&A...626A..36D, 2024A&A...682A..61C, 2021ApJ...923..121Y |
| Size distribution slope p | 3.5 | 1.5-3.5 tested | my count: 5 alpha papers | 2020ApJ...891...48H, 2023ApJ...948..110Y, 2023MNRAS.518.6092L, 2024A&A...682A..61C, 2024ApJ...974..102S (2.5 or 3.5) |
| beta_s (debris) | 1.8 ± 0.2 | - | 3 | 2017MNRAS.466.4201W, 2019AJ....158..162F, 2026A&A...705A.196H |
| Adopted beta if not measured | 1.8 (41), 1.5 (36), 2.0 (35), 1.0 (26, disks and protostars), 1.6 (25) | 0-2.0 | my count: 196 single-value adoptions | 2025A&A...693A..49S, 2020ApJ...892...66M, 2026A&A...713A.167D |
| Free-free index | -0.1 | -0.118 to -0.1 (jets 0.4-0.7) | my count: 11 at -0.1 | 2019MNRAS.483.1624B, 2016ApJ...833L...6C, 2019ApJ...883...71C |
| Synchrotron index (fiducial) | -0.7 (7), -0.8 (6) | fiducial -0.68 to -0.9; explored -0.6 to -1.5 | my count: 20 fiducial | 2018ApJ...867...48I, 2020A&A...642A.155Z, 2021MNRAS.503.1174K |

Counts in the beta row use bins (1.8-1.85, 1.46-1.55); the ledger, the parsing method, multi-value papers and priors
are in `references/parameters.md` sections 1 and 3-5, with measured alpha values in section 2.

## Software

Pack software aggregate (mentions in matched steps, not unique papers); merge map and the full census are in
`references/parameters.md` section 6.

| Tool | Pack count | Used for (bibcode where the pack ties the tool to the step) |
|---|---|---|
| CASA (tclean, imfit, imsmooth) | 120 | mtmfs alpha maps (2018ApJ...853..171G), per-spw `imsmooth` (2026A&A...712A.244H), `imfit` inner-disk check (2025MNRAS.538.2358S) |
| emcee | 27 | two-greybody SED fits with free beta (2023MNRAS.523.4654T); radio-mm SED with AME (2020ApJ...905L..23M) |
| SciPy (curve_fit, optimize) | 17 | power-law fits (2025A&A...702A.276P, 2019ApJ...875...55W) |
| RADMC-3D, DustPy | 11, 4 | a_max(R) fit to alpha_mm(R) (2023MNRAS.518.6092L); dust evolution vs observed alpha (2025MNRAS.538.2358S) |
| Frankenstein (`frank`) | 9 | 1D visibility profiles (2025MNRAS.538.2358S, 2026A&A...705A.196H); its `alpha` is a hyperparameter |
| uvmultifit, eht-imaging | 3, 2 | per-spw point-source fluxes (2026A&A...712A.244H); RML alpha map (2023ApJ...945...40C) |

## Pitfalls

- **Calibration, not noise, sets the error.** Absolute alpha uncertain by about 0.4 (2018A&A...616A..88V,
  2025A&A...694L..15H); the 10% systematic dominated a disk-averaged index (2025ApJ...988..106H). Relative alpha
  changes across one disk are more robust than the absolute level, since the scale offset is common (general
  practice; 2024MNRAS.527.9668H).
- **Optical depth mimics grain growth.** The DS Tau inner disk is optically thick even at 2.9 mm, so its grain size
  was fixed rather than fitted (2023MNRAS.518.6092L); optically thin masses are lower limits (2018AJ....156..239Z,
  2018ApJ...863...94L), and an inner region may be off by up to about 5 because it is thick (2024A&A...682A..61C).
- **Scattering** lowers alpha in thick regions (2021ApJ...909..212K); papers that leave it out say so
  (2020ApJ...905...89Y, 2025A&A...699A.373F).
- **Temperature, tau and beta are degenerate.** 2015ApJ...810L...7V tested 24 and 200 K against a uniform 60 K;
  2023MNRAS.523.4654T varied absolute flux scales by 10% in opposite directions and beta from 1 to 2.5;
  2015ApJ...800...70S could not derive T from its data and quoted masses uncertain by a factor of 2.
- **Different spatial filtering per band.** 2016ApJ...833L...6C noted structures above about 12" undersampled in
  Band 7; ALMA-only recovered about 18% (2014ApJ...795L..25R), 15% (2015ApJ...800...70S) and 30% of the flux
  (2026A&A...707A.255C, indices reliable only on primary-beam scales without ACA). Match uv ranges or add ACA/TP.
- **Non-simultaneous bands on variable sources.** Short mm flares cannot be excluded (2019ApJ...875...55W); a core
  index changed from -0.79 (reduced chi^2 2.76) to -0.905 (123.0) with the choice of Band 7 epoch
  (2026A&A...712A.244H); 2026ApJ..1004..126K had to assume the index does not change with time.
- **Limits and small samples.** Treat non-detections in one band as censored (survival statistics, general
  practice); 2024ApJ...961....4B gave upper and lower limits for single-band sources. 2024ApJ...961..120C fixed
  alpha = -0.8 for sources with one frequency.
- **Map artefacts, resolution, model choice.** 17 GHz left out of index maps for artefacts, and flux systematics
  from differing beams (2017ApJ...841..130A); sub-beam grain-size fluctuations need confirmation
  (2023MNRAS.518.6092L); the innermost 1-2 beams of a `frank` profile are less certain (2025MNRAS.538.2358S) and
  `frank` uncertainties are likely underestimated (2026A&A...705A.196H); an RML alpha map has no robust uncertainty
  (2023ApJ...945...40C); equal weighting of frequencies may not suit each dataset (2018ApJ...859..103W).
- **Settings the cards rarely state** (pack aggregate, my sums; split in `references/parameters.md` section 7):
  line-free channels 66, CASA version 28 plus 33 more CASA-related flags (27 also ask for pipeline details), flux
  calibrator and uncertainty 23, self-cal solution intervals 17 (+20), image and cell size 13, PB correction 12,
  CLEAN threshold/mask/niter 9, uvmodelfit starting parameters 3, continuum bandwidth 3. Record every one you used.

## Verification checks

What papers did:
- Cross-check two alpha methods: mtmfs nterms=2 vs per-band power law (2025A&A...702A.276P: 0.57 ± 0.23 vs
  0.56 ± 0.11); peak flux vs `imfit` (2025MNRAS.538.2358S); 1 mm vs 3 mm brightest-pixel positions
  (2024ApJ...961....4B, much smaller than the errors).
- Change priors, Jeffreys vs uniform (2018ApJ...859..103W); rerun with another opacity model and about 10%
  calibration per band (2023MNRAS.518.6092L).
- Vary the fixed non-dust index (2024ApJ...974..243N: 4 vs 3.8, about 4%; 2015ApJ...813..118M: -0.6 vs -0.85, card).
- BIC test of curvature and band alignment on non-self-calibrated images (2026A&A...712A.244H); simulate the uv
  coverage on a template with known alpha (2026A&A...707A.255C).
- Compare q with the collisional value 3.51 (2017MNRAS.466.4201W) and other debris indices (2026A&A...705A.196H).

What a careful referee adds:
- Absolute and relative alpha errors given separately, per-band flux-cal values named, correlation stated.
- Bands at matched uv range, beam, pixel grid and astrometric registration; epochs close enough for the source.
- Integrated and peak indices kept apart, with units and resolution stated.
- Peak brightness temperature compared with a physical temperature to test optical thickness (general practice).
- Free-free, AME and (for debris) stellar flux estimated or bounded before calling alpha "dust".
- Any beta < 1 claim shown to survive tau and scattering corrections, with T, background and priors stated and
  varied.

## Source cards

Full list: `references/sources.md` (generated). Most informative for this technique:

- 2023MNRAS.518.6092L: B3/B6 radial alpha at a common beam, RADMC-3D a_max(R) fit, thick inner disk, opacity rerun
- 2025MNRAS.538.2358S: B3/B6/B7 frank profiles at 35 mas, inner-disk free-free from extrapolated dust index
- 2018A&A...616A..88V: S/N < 2.5 mask, 10% per band gives 0.42 on alpha
- 2024ApJ...974L..25D: 5% B3 and 10% B7 give 0.083 on alpha
- 2025A&A...702A.276P: mtmfs alpha cross-checked against per-band power law
- 2015ApJ...808L...3A: combined B6+B7 nterms=2 spectral-index map, robust 0.0
- 2026A&A...712A.244H: per-spw index fit with chi^2 cut and BIC, imsmooth, QA2 alignment, epoch effect
- 2018ApJ...859..103W: joint MCMC visibility fit with alpha free, prior 0-4, prior test
- 2018ApJ...853..171G: mtmfs alpha for compact sources, 5 sigma selection, incomplete catalogue
- 2024ApJ...961....4B: integrated vs brightest-pixel fluxes, beam matching, limits, in-band maps too noisy
- 2024A&A...682A..61C: streamer beta, exact-T assumption, thick inner region
- 2026A&A...705A.196H: debris beta and q from B6/B7, stellar flux subtraction
- 2017MNRAS.466.4201W: debris alpha_mm and q with beta_s; PB-edge caveat; sign convention issue
- 2020ApJ...905...89Y: per-position T_d, tau, beta with CMB subtracted, 5-20% calibration
- 2016ApJ...833L...6C: 3 mm free-free extrapolated to 870 um
- 2020ApJ...905L..23M: free-free only 25% at 30 GHz, AME dominant
- 2026A&A...707A.255C: Band 1 EME index from uv regression, regularisation bias, flux loss
