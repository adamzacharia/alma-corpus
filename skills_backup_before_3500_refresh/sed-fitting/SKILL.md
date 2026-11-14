---
name: alma-sed-fitting
description: "Fit (sub)mm and far-IR photometry that includes ALMA fluxes to get dust temperature, emissivity index beta, L_IR / L_FIR, dust mass and IR-based SFR, with a single or general-opacity modified blackbody, IR templates, or panchromatic energy-balance codes (MAGPHYS, CIGALE). Use when an agent must turn ALMA continuum fluxes (plus Herschel, SCUBA-2, Spitzer, radio) into dust or star-formation quantities, pick fixed T_dust/beta for a single-band source, decide between MBB, templates and MAGPHYS/CIGALE, or check someone else's SED fit. Built from 384 ALMA papers (2012-2026)."
---

# Dust SED fitting (modified blackbody, templates, panchromatic codes)

Fits the thermal dust SED to get T_dust, beta, L_IR (or L_FIR), dust mass and SFR. When the far-IR data are sparse
(for example the 16 quasar-host papers that fix T=47 K and beta=1.6, my count below), the answer is set by
**assumptions** (T_dust, beta, opacity regime, IMF, which wavelength range "L_IR" means) rather than by the data.
The two mistakes that matter most: (1) quoting a T_dust or L_IR that the wavelength coverage cannot constrain as if
it were measured, and (2) mixing conventions (8-1000 um L_IR vs 42.5-122.5 um L_FIR, Chabrier vs Salpeter SFR
constants, optically thin vs general opacity, opacity per dust mass vs per gas+dust mass) when comparing to the
literature.

Counts below are from the evidence pack (`skills/packs/sed-fitting.md`): either its aggregates or my own count of
pack lines, as stated. Several dozen of the 384 tagged papers fit non-dust SEDs (synchrotron afterglows,
X-ray binary jets, YSO model grids, stellar photospheres, CO SLEDs); my own counts use only dust lines.

## When to use

- Turning ALMA continuum fluxes (alone or with Herschel/SCUBA-2/Spitzer) into T_dust, beta, L_IR, SFR_IR or
  M_dust for galaxies at any redshift, quasar hosts, nearby galaxy nuclei, or Galactic clumps.
- Choosing fixed T_dust and beta for a source with one ALMA band.
- Deciding between a modified blackbody (MBB), IR templates, or an energy-balance code (MAGPHYS, CIGALE).
- Removing AGN, synchrotron or free-free contributions before fitting the dust.
- Reviewing a published or colleague's SED fit for convention mismatches and over-claimed precision.

## When not to use

| Situation | Use instead |
|---|---|
| Protoplanetary or debris disk SED with geometry (RADMC-3D, MCFOST, DIAD, DALI are used, e.g. 2019ApJ...878..103R, 2015ApJ...806L..22C, 2020ApJ...893..125U) | `radiative-transfer-modelling` skill |
| Single-band dust mass or gas mass via a Rayleigh-Jeans calibration (2017ApJ...844..123F, 2026ApJ..1001..131C) | `dust-continuum-mass`, `gas-mass-co-conversion` |
| Spectral index between two ALMA bands, beta from alpha (2015ApJ...798..124R) | `spectral-index` |
| Synchrotron / afterglow / jet SEDs (2019ApJ...871...73H, 2023NatAs...7...80U, 2024ApJ...962..116E) | `free-free-synchrotron`, `variability-time-domain` |
| YSO classification with Robitaille-type grids or Tbol/Lbol integration (2015ApJ...808...97Y, 2021A&A...648A..41V) | general YSO SED practice; this skill only covers the dust MBB part |
| Stacked fluxes of undetected populations | `stacking`, then come back here for L_IR |

## Steps

**1. Decide what you are fitting and what the data can support.**
- Goal: pick the output (T_dust, beta, L_IR, SFR, M_dust) and the model complexity the photometry allows.
- Rule seen in the pack: one paper fixes beta=1.8 always, fixes the mid-IR slope alpha=2.5 if there are fewer
  than 4 far-IR points, and also fixes T_dust=35 K if there are fewer than 2 (2017ApJ...840..101C). A photo-z
  survey requires at least 4 detected bands (2014ApJ...788..125S).
- With one continuum point, authors state T_dust is unconstrained (2015ApJ...807..180W) and that L and SFR can be
  uncertain by orders of magnitude (2015ApJ...813...45L); results "depend strongly on assumed dust temperature"
  (2016ApJ...833...72B).
- With two or more points, whether T_dust is identifiable depends on where the points sit relative to the rest-frame
  peak, which parameters are free (T alone with beta fixed, or T and beta together), and the T-beta degeneracy
  (general practice). Count free parameters against points; 2017ApJ...840..101C fixes T only below 2 far-IR points.

**2. Build the photometry table.**
- ALMA flux: total flux from a Gaussian fit (CASA `imfit`, 5 uses in the pack aggregate) or uv-plane fit, not peak
  flux, for resolved sources. Interferometric flux can be lost on extended sources; one paper propagates the
  range of missing flux as the parameter error (2014A&A...567A.125G); another excludes the ALMA point from the
  MBB fit because the ALMA continuum lacks single-dish data and is underestimated (2018MNRAS.475..448T).
  A small beam that resolves out extended dust can also bias the fitted SED shape (general caution).
- Spatial consistency: make every band measure the same emission. Papers use a common solid angle for all bands
  (2017ApJ...840...72L), exclude high-resolution ALMA fluxes from a fit to low-resolution FIR points
  (2021A&A...648A..41V), or admit that differing sizes were not corrected and that fluxes outside the primary beam
  are unreliable (2015ApJ...801...82H). Use matched physical apertures or a justified component model, and list
  every excluded point.
- ALMA continuum hygiene: record the line-free channels and continuum method, and check line contamination of
  the continuum (2024ApJ...962....1S had almost no line-free USB channels). Confirm primary-beam correction and use
  the local noise for off-centre sources. In the pack's "not stated" aggregate, line-free channel variants add up
  to 49 and primary-beam correction variants to 13 (my sum of the listed labels; mentions, not unique papers).
- Herschel/SCUBA-2 at low resolution: deblend with ALMA positions as priors. Examples: iterative subtraction of
  a lens's contribution (2016A&A...596A..75S), splitting Herschel flux in the ALMA flux ratio
  (2018MNRAS.474.4039M), super-deblending with PSF fits and Monte Carlo flux calibration (2024A&A...690A..55S),
  fitting with and without SPIRE to test blending (2018ApJ...859...35G), assigning a fixed 25% of the SCUBA flux
  to the quasar in a blended QSO + companion system (2020MNRAS.493.3744F). This is source allocation, not AGN
  heating removal (that paper assumes the dust is heated by star formation). Prior-based deblending can bias
  against sources faint in the prior band (general caution; no pack card states it).
- Keep three kinds of extra uncertainty apart:
  - Photometric calibration floors on the input fluxes: 7% PACS and 10% other bands (2016ApJ...822...80S), 10%
    flux calibration (2017ApJ...845..154V, 2018PASJ...70L...6K), 10% on all points (2014ApJ...790..160S), an
    extra 15% (2019ApJ...871...85L).
  - Deblending or model uncertainty: 35% on the lens-model flux used during deblending (2016A&A...596A..75S).
  - Systematics on derived outputs: 0.1 dex added in quadrature to MAGPHYS outputs (2020ApJ...901...79A).
- Upper limits: keep >3 sigma points only and treat the rest as 3 sigma limits (2024A&A...690A..55S), or follow
  the code's convention (2020MNRAS.494.3828D sets non-detections as 1.5 +/- 1.0 sigma beyond 10 um).

**3. Remove what is not star-formation-heated dust.**
- Synchrotron and free-free: extrapolate from radio with fixed indices, e.g. alpha_synch=-0.8 and alpha_ff=-0.1
  (2017A&A...597A...5M) or -0.9/-0.1 (2017ApJ...849...90S), or fit grey-body + free-free + synchrotron together
  (2021A&A...656A..46M). In radio galaxies the mm continuum can be synchrotron-contaminated, so SFRs become upper
  limits (2016A&A...591A..73G).
- AGN: subtract a QSO template extrapolated from SDSS+WISE (2017ApJ...844..123F), assume a fixed AGN share
  (20% of L_IR, 2018ApJ...853...24U), or fit an AGN component (CIGALE Fritz/SKIRTOR, 2024ApJ...962....1S,
  2026ApJ..1001..131C). Thresholds used: AGN significant if >=20% of L_IR (2018MNRAS.478.3721S); excluded if
  f_AGN >= 80% (2020A&A...641A.155V); keep the AGN component only if Delta BIC > 2 (2018MNRAS.475.1288S).
- The subtraction itself is uncertain: at least 0.13 dex from the dispersion of QSO templates
  (2017ApJ...844..123F), and extreme obscuration can hide an AGN and bias mid-IR decomposition
  (2018ApJ...859...35G). Propagate that uncertainty, test a buried-AGN alternative, and do not treat a fitted
  f_AGN as complete removal.
- Old stars: heating by old stellar populations (cirrus) also adds IR that is not current star formation.
  2019MNRAS.486..560S neglects it and calls its SFRs conservative upper values. Consider it for quiescent or weakly
  star-forming systems.
- Rest-frame cut: drop points shortward of rest 50 um for a single cold MBB (2016ApJ...822...80S,
  2020ApJ...902...78R). This protects the cold-component fit but does not recover warm-dust luminosity (see
  step 6 and Pitfalls).
- Lensing: correct with the magnification and fit only the far-IR part where it applies (2015MNRAS.451L..40R).
  Differential magnification between bands is a general caution; the cards rarely state how it was handled.

**4. Choose the model.** (per-paper counts are my counts of pack parameter/assumption lines)
- Single-temperature optically thin MBB (general practice):
  S_nu = (1+z) M_d kappa_nu0 (nu_rest/nu0)^beta [B_nu(T_d(z)) - B_nu(T_CMB(z))] / D_L^2, with
  T_CMB(z) = 2.73 (1+z) K (2024A&A...691A.133V uses T_CMB(z=0)=2.73 K) and T_d(z) the dust temperature at z,
  including any CMB heating (see step 6). Here M_d is dust mass only if kappa is per gram of dust.
- General opacity: S_nu proportional to (1 - exp(-(nu/nu_0)^beta)) B_nu(T) with lambda_0 fixed: 100 um
  (2014ApJ...785..149S, 2024A&A...691A.133V), 125 um (2019ApJ...887...74F), 150 um (2017ApJ...844..123F),
  200 um (2014A&A...562A..67G, 2024ApJ...972..111L). Gives warmer T than optically thin: 58.5 K vs about 33 K for
  the same source (2014A&A...562A..67G).
- MBB + mid-IR power law (alpha 1.5-2.5): 2015Natur.522..455C, 2017Sci...355.1285N, 2017ApJ...847...21F;
  fixed alpha=2.0 in 2020A&A...633A.160C and 2024A&A...691A.133V.
- Two-temperature MBB: e.g. T_cold fixed 35 K, beta=1.5, free warm component (2014ApJ...790..160S); warm/cold
  beta 1.5/2.0 (2020ApJ...901...79A).
- Empirical templates scaled to the ALMA flux: CE01 (2012ApJ...761L..32W, 2016ApJ...833..195W), Bethermin
  2017 (2020A&A...643A...2B, 2024A&A...688A..55M), Schreiber 2018 (2021A&A...652A..30S),
  Kirkpatrick 2015 (2018ApJ...853..195W), Magdis 2012 via STARDUST (2024A&A...690A..55S), several libraries
  compared (2019MNRAS.486..560S).
- Panchromatic energy balance: MAGPHYS (high-z version, 2016ApJ...833..112S; 2020ApJ...892...66M) and CIGALE
  (2018ApJ...859...35G, 2026ApJ..1001..131C), when you need M_star and SFR together with dust.

**5. Fit.**
- chi2 grid or Levenberg-Marquardt for MBBs with several points (2014A&A...562A..67G; 2020AJ....159..288M with
  mpfit and lambda_0 fixed at 100 um). Least-squares example from a YSO paper: a simple blackbody (not a
  greybody) fitted with `scipy curve_fit`, errors from the covariance matrix, high-resolution ALMA fluxes
  excluded (2021A&A...648A..41V).
- MCMC (emcee is the most-named sampler) with explicit priors. Settings seen, with what was free:
  - T and beta both free (or beta free): uniform T > 1 K, beta 0.1-20, lambda_0 1-400 um, alpha 0.1-20
    (2019ApJ...871...85L); beta limited to 0-2 to bound T (2021A&A...653A.117B); bounds beta<3,
    T<100 K **observed-frame** (multiply by (1+z) for a rest-frame T prior), lambda_0<2000 um
    (2014A&A...568A..92M); 100 walkers x 500 steps with 100 burn-in, beta=1.8 listed with it
    (2019MNRAS.482.3135B; the pack does not say whether beta was free in that run).
  - beta fixed: 50 walkers x 1e6 steps with 1e4 burn-in, beta=1.8 (2017ApJ...839...58S); T_d hard prior
    10-100 K with beta fixed 1.5 (2016MNRAS.463...10M).
  - Other priors: T 20-70 K (2019A&A...621A..27F).
- Fixed walker and step counts do not prove convergence. Check autocorrelation time or effective sample size,
  inspect chains, and look for posteriors piled against a prior boundary (general practice).
- Error from noise realizations of the photometry: Monte Carlo synthetic photometry (2017ApJ...844..123F).
- CIGALE/MAGPHYS: report the likelihood-weighted PDF mean (2018ApJ...859...35G, 2024ApJ...962....1S).

**6. Derive quantities.**
- L_IR: integrate the best-fit SED over rest-frame 8-1000 um (2016ApJ...833...72B, 2018MNRAS.478.3721S,
  2020A&A...633A.160C). L_FIR: 42.5-122.5 um (2016ApJ...816...37V, 2019ApJ...874L..30V, 2024ApJ...977..198L).
  Conversions reported: L_TIR = 1.41 L_FIR (2020ApJ...904..130V), bolometric factor 1.91 (2018ApJ...867..140L),
  L_TIR(3-1100 um) ~ 1.1 L_IR(8-1000 um) (2018ApJ...853..195W). An MBB alone underestimates L_FIR by about 20%
  (2017ApJ...844L..10S). In 2017ApJ...844..123F, optically thin and Arp 220 comparison models gave L_IR differing
  from the general-opacity MBB by about 0.1 dex (the paper says the result "can be higher than the blackbody
  fits"); treat it as a spread, not a fixed offset.
- If you fit only a cold MBB (rest <50 um dropped), it does not contain the warm-dust emission. For an 8-1000 um
  L_IR add a mid-IR power law or warm component, use a template, or quote the extrapolation uncertainty.
- SFR: always apply the constant to the star-formation-heated luminosity L_IR,SF (AGN and other non-SF heating
  removed), in Lsun, giving Msun/yr. Constants seen: 1.40e-10 L'_IR (Chabrier; 2024ApJ...962....1S, where L'_IR
  excludes the AGN: their L_IR=1.34e13 Lsun with f_AGN=0.59 gives 1.40e-10 x 0.41 x 1.34e13 = 770 Msun/yr, their
  quoted SFR, my arithmetic; also 2025A&A...698A.204H), 1.09e-10 (Chabrier, 2018ApJ...853...24U), 1.0e-10
  (Kennicutt98 with Chabrier, 2017ApJ...844..123F), 1.72e-10 L_IR,SF or 1.73e-10 (Salpeter; 2019A&A...621A..27F,
  2026A&A...705A..39P), 1.8e-10 (Salpeter, 2020ApJ...892..119M). A Kennicutt calibration is named in 12 papers'
  lines (my count). Convert IMFs explicitly (Salpeter/1.5 to Kroupa, 2019A&A...621A..27F; /1.8 for Chabrier,
  2017A&A...604A.117C).
- M_dust: from the MBB normalization with a stated kappa (see table). Check the kappa's mass basis: per gram of
  dust gives M_dust; per gram of gas+dust (e.g. 0.1 cm2/g (nu/1 THz)^beta "includes a gas-to-dust ratio of 100",
  2018MNRAS.475..448T) gives total gas mass directly, so do not multiply by a gas-to-dust ratio again.
- CMB (general practice, da Cunha et al. 2013): heating raises the dust temperature to
  T_d(z)^(4+beta) = T_d0^(4+beta) + T_CMB0^(4+beta) [(1+z)^(4+beta) - 1], and the contrast term subtracts
  B_nu(T_CMB(z)). Papers differ: contrast only (2018MNRAS.481.1631B), heating and contrast (2020MNRAS.493.4294B),
  da Cunha Eq. 12 (2024A&A...691A.133V). If your assumed T_d is already the observed (heated) temperature, apply
  only the contrast term; never apply heating twice. T_d must exceed T_CMB(z): T_CMB is 14.7 K at z=4.43
  (2024A&A...684A..56K) and about 23.4 K at z=7.5 (2017MNRAS.466..138K), so an assumed 25 K at z > 8 is
  unphysical.

**7. Validate** (see Verification checks).

## Parameter defaults and ranges

Counts: my count of distinct bibcodes in the pack's parameter/assumption lines (dust papers only).

| Parameter | Common choice | Range seen | Papers (count) | Examples |
|---|---|---|---|---|
| Fixed (T_d, beta) for quasar hosts (mostly z > 5.7) and some z ~ 2-2.5 quasar systems | 47 K, 1.6 | 41-60 K | 16 pair 47 K with 1.6 (my count; 2024ApJ...977..198L is z ~ 2 Lya nebulae) | 2013ApJ...770...13W, 2017Natur.545..457D, 2020ApJ...904..130V, 2026ApJ..1002L..28Y |
| Fixed T_d for SMGs / DSFGs | 35 K | 25-45 K | 16 use 35 K | 2014ApJ...795....5O, 2017ApJ...840..101C, 2018ApJ...854L...7C, 2025ApJS..278...45F |
| beta (fixed) | 1.5 (26), 1.6 (21), 1.8 (19), 2.0 (18) | 1.2-2.5 (2014ApJ...795L..25R adopts 1.2) | see counts | 2016MNRAS.463...10M (1.5), 2018Sci...362.1034D (1.8), 2016ApJ...822...80S (2.0) |
| beta tested grid | 1.5, 2.0, 2.5 | best 2.0-2.5 | 3 | 2017ApJ...841..130A, 2018MNRAS.477.4380S, 2020MNRAS.493.4294B |
| beta prior / free range | 1.2-2.0 | 0.1-20 (uniform) | several | 2015Natur.522..455C, 2014ApJ...780..115D, 2019ApJ...871...85L |
| T_d from z-dependent relation | Schreiber+18, about 30-65 K | 38-40 K at z~3.5 | 3 | 2020A&A...633A.160C, 2020A&A...642A.155Z, 2018A&A...618A..85S |
| Opacity regime | optically thin | lambda_0 = 100-200 um | 15 mention lambda_0 / thick | 2014A&A...562A..67G, 2019ApJ...887...74F, 2024A&A...691A.133V |
| Mid-IR power-law slope alpha | 2.0 | 1.5-2.5 | 8 | 2017ApJ...847...21F, 2020A&A...633A.160C, 2024A&A...691A.133V |
| kappa normalization (per dust mass) | 0.077 m2/kg at 850 um / 352 GHz | 0.0383-0.15 m2/kg at 850 um | 6 use 0.077 at 850 um / 352 GHz, plus 2015ApJ...811..124S at 870 um (my count) | 2019MNRAS.482.3135B, 2018ApJ...854...97D, 2017ApJ...851...98T (0.0383), 2020MNRAS.493.4294B (0.15) |
| Gas-to-dust (when M_gas is derived) | 100 | about 30-200 | 20 lines use 100 (about a third are disk models) | 2018Sci...362.1034D, 2020A&A...641A.155V (~30 for starbursts), 2014A&A...567A.125G (60), 2016ApJ...833...68A (200) |
| IMF for SFR | Chabrier | Salpeter, Kroupa | 72 / 20 / 8 | 2017ApJ...850...83F, 2019ApJ...876...99S, 2020ApJ...904..130V |
| L_IR range | 8-1000 um rest | 42.5-122.5 um (L_FIR) | 5 / 3 explicit | 2018MNRAS.478.3721S, 2024ApJ...977..198L |
| Photometric calibration floor | 10% | 5-15% | about 7 | 2016ApJ...822...80S, 2019ApJ...871...85L (15%), 2025ApJ...988..135M (5%, stellar SED fit) |
| Fixed z for unknown-z SMGs | 2.5 | 2-3 | 8 use z=2.5 | 2017ApJ...844..123F, 2015ApJ...806L..25S, 2018PASJ...70...65U |

Longer tables (opacity laws, SFR constants, CIGALE/MAGPHYS settings, Galactic-clump choices) are in
`references/parameters.md`.

## Software

Mentions from the pack's "Software named in the matched steps" aggregate (names already lower-cased there).
These are mentions in any matched step, not counts of dust-SED fits: some tools are used for other parts of the
same papers (for example MPFIT for Gaussian line fits in 2024A&A...690A..55S).

| Software | Mentions | Used for | Examples |
|---|---|---|---|
| MAGPHYS | 37 | panchromatic energy balance, M_star + SFR + M_dust | 2016ApJ...833..112S, 2020ApJ...892...66M, 2020ApJ...901...79A |
| CIGALE | 27 | energy balance with AGN (Fritz, SKIRTOR) and radio modules | 2018ApJ...859...35G, 2024ApJ...962....1S, 2026ApJ..1001..131C |
| emcee | 22 | MCMC for template normalization (2018ApJ...853..195W) and MBB parameters; also non-dust uses such as the UV slope in 2020A&A...633A.160C, and disk fits | 2018ApJ...853..195W |
| FAST / FAST++ | 8 + 4 | stellar mass from UV-NIR before the dust fit | 2020A&A...642A.155Z, 2020A&A...633A.160C |
| EAZY, LePhare, hyperz | 9, 5, 4 | photometric redshift to fix z | 2014ApJ...788..125S, 2024A&A...690A..55S |
| CASA imfit | 5 | ALMA total flux for the SED point | aggregate count |
| MR-MOOSE | 2 | Bayesian multi-component SED of blended sources | 2020MNRAS.493.3744F |
| STARDUST | 2 | template-based FIR fit after super-deblending | 2024A&A...690A..55S |
| Prospector, dynesty, Bagpipes | 5, 2, 4 | Bayesian stellar SED | 2024AJ....167..274A |
| scipy curve_fit, MPFIT | 3, 3 | least-squares fits: blackbody for a YSO (curve_fit), LM MBB for a debris disk (mpfit); MPFIT also used for line fits | 2021A&A...648A..41V, 2020AJ....159..288M |
| RADMC-3D, MCFOST, DIAD, DALI | 10 (8 + 2 "radmc3d"), 6, 3, 5 | disk radiative transfer (out of scope here) | 2019ApJ...878..103R |

## Pitfalls

- **Single-band "measurements".** One point cannot constrain T_dust (2015ApJ...807..180W, 2015ApJ...813...45L).
  With two or more, identifiability depends on coverage around the peak and on how many parameters are free
  (see step 1). A fixed-SED L_IR carries about 0.2-0.3 dex systematics (2015MNRAS.453L..83M,
  2016MNRAS.461.2944A, 2020MNRAS.491.4724F) and up to a factor 2-3 for quasar hosts (2020ApJ...904..130V). Quote
  the assumed T and beta next to every number.
- **T-beta degeneracy.** Papers fit beta fixed and free (2019ApJ...879..117K, 2017ApJ...847...21F) or average two
  (T, beta) pairs (2017MNRAS.465.4390B: 47 K/1.6 and 41 K/1.95). Do not compare T_d across papers with different
  beta.
- **Optically thin vs thick.** The same data give 58.5 K or about 33 K (2014A&A...562A..67G). Say which.
- **Missing warm component.** A single cold MBB misses warm dust and underestimates L_FIR by about 20%
  (2017ApJ...844L..10S). Dropping rest <50 um points protects the cold fit (T_d, M_d) but does not restore the
  missing luminosity; for 8-1000 um L_IR add a mid-IR power law, a warm component or a template, or quote the
  extrapolation uncertainty.
- **CMB at high z.** Ignoring CMB heating and contrast biases T and M_d (about a dozen dust papers' lines mention a
  CMB correction, my count; e.g. 2016ApJ...822...80S, 2017ApJ...850...83F, 2020ApJ...897L..14Y). Some papers
  state they skipped it (2015ApJ...807..180W). Papers treat it differently (contrast only, 2018MNRAS.481.1631B;
  heating and contrast, 2020MNRAS.493.4294B), so say which, do not correct heating twice, and keep the assumed
  T_d above T_CMB(z) = 2.73 (1+z) K (step 6).
- **Uncertainty budgets that leave things out.** Fit errors excluding absolute calibration (2021A&A...656A..46M);
  redshift uncertainty propagated through a Delta z = 0.01 grid as 16th-84th percentiles (2017A&A...597A...5M).
  Check whether the T_d uncertainty of a fixed-T result is in the quoted error (general caution).
- **Opacity and mass factors of 2.** kappa choices differ by about 2x (0.077 vs 0.15 m2/kg at 850 um, see table);
  using Dunne et al. 2000 instead of Hildebrand doubles M_d (2019PASJ...71...71H); CIGALE dust masses were divided
  by 2 to match Draine07 opacities (2025A&A...694A..82S). The mass basis matters even more: an opacity per gram of
  gas+dust (2018MNRAS.475..448T) gives gas mass, a factor of about 100 from a dust mass; see
  `references/parameters.md` for the basis of each kappa.
- **AGN, old-star and synchrotron contamination.** Gas masses that ignore the AGN contribution may be biased
  (2026ApJ..1001..131C); AGN template subtraction carries at least 0.13 dex (2017ApJ...844..123F) and a buried
  AGN can be missed (2018ApJ...859...35G); neglecting old-star heating makes SFRs upper values
  (2019MNRAS.486..560S); radio-galaxy mm continuum can be synchrotron (2016A&A...591A..73G).
- **Blending and deblending assumptions** that cannot be verified (2016A&A...596A..75S). With lensing, a single
  magnification for all bands ignores differential magnification (general caution).
- **Mismatched apertures.** Bands that see different emission (different beams, resolved-out flux, sources
  outside the primary beam) give a wrong SED shape (2015ApJ...801...82H, 2018MNRAS.475..448T).
- **Unknown redshift.** Assuming z=2.5 makes those results "less reliable" (2017ApJ...844..123F).
- **Unstated settings.** In the pack's "not stated" list (a top-40 list of label variants, counted as mentions,
  not unique papers), the five flux-calibrator / flux-scale-uncertainty variants add up to 31 (12+9+4+4+2, my
  sum), close to the single label "casa version" (33); line-free channel variants add up to 49. Cards often note that SED
  code priors, grids and initial values are not given (e.g. 2017ApJ...844..123F, 2020MNRAS.493.3744F,
  2026ApJ..1001..131C). State yours.

## Verification checks

What papers did:
- Refit with the parameter free that you fixed and confirm it comes back: T_cold free recovered 35 K
  (2014ApJ...790..160S).
- Compare optically thin vs general-opacity fits and report the spread: 58.5 K vs about 33 K in T
  (2014A&A...562A..67G); about 0.1 dex in L_IR against optically thin and Arp 220 models (2017ApJ...844..123F).
- Cross-check codes: CIGALE vs MAGPHYS (2026ApJ..1001..131C), CIGALE as a sanity check of templates
  (2016A&A...596A..75S), MBB vs MAGPHYS within about 0.5 dex (2020A&A...633A.160C), L_IR vs Draine07 within 10%
  (2020A&A...642A.155Z).
- Drop bands and refit: unchanged without Herschel (2016A&A...596A..75S), with and without SPIRE
  (2018ApJ...859...35G).
- Compare SFR_IR with independent SFRs: radio (2016A&A...596A..75S), SED-decomposition SFR vs FIR SFR
  (2014A&A...562A..67G).
- Report goodness of fit: median reduced chi2 0.52 (2024ApJ...962....1S); reduced chi2 of 1
  (2014ApJ...790..160S).
- Compare dust-based gas mass with CO-based and dynamical mass (2018Sci...362.1034D).

What a careful referee adds:
- A table of every input flux with its error, the error floor, which points are limits, which were excluded and
  why, and the aperture or component model each flux comes from (same emission in every band; step 2).
- For ALMA points: the line-free channels and continuum method, a line-contamination check, and confirmation of
  primary-beam correction with local noise for off-centre sources.
- The full prior list and sampler settings; T-beta posterior contours; a convergence check (autocorrelation
  time or effective sample size, chain inspection) and a check that posteriors are not piled against a prior
  bound (general practice).
- Separately named integrals with rest-frame limits: L_IR(8-1000 um) and L_FIR(42.5-122.5 um), the conversion
  between them stated. Keep a paper's own label only next to its limits (2016MNRAS.463...10M calls an
  8-1000 um integral "LFIR"). SFR with the IMF, the constant, and which luminosity (L_IR,SF) it was applied to.
- For AGN hosts, the AGN-subtraction uncertainty propagated and a buried-AGN alternative tested.
- For single-band sources, the spread in L_IR over a T_d and beta range chosen for the population and redshift,
  instead of one number. Ranges seen in the pack: SMGs 25-45 K around 35 K (table); quasar hosts 41-60 K around
  47 K, beta 1.6-1.95 (2017MNRAS.465.4390B); hot or very luminous systems 50-100 K (2018Sci...362.1034D), a 60-90 K
  prior (2017ApJ...847...21F), 80 K at z = 8.3 (2025ApJ...990...29H); z-dependent 30-65 K (2020A&A...633A.160C).
  Keep T_d above T_CMB(z). These are conditional tests, not full uncertainty bounds.

## Source cards

Full list: `references/sources.md` (all 384 papers). Most informative for this technique:

- 2014A&A...562A..67G: optically thick vs thin MBB, L_IR and SFR, SED decomposition.
- 2017ApJ...844..123F: QSO subtraction, general-opacity MBB, Monte Carlo errors.
- 2016A&A...596A..75S: deblending, Draine & Li, templates, CIGALE sanity check.
- 2017ApJ...840..101C: rule for fixing alpha and T with few points.
- 2016ApJ...822...80S: rest <50 um cut, CMB, calibration floors.
- 2019ApJ...871...85L: full uniform priors for T, beta, lambda_0, alpha.
- 2016MNRAS.463...10M: deblending with T prior and photo-z priors.
- 2020A&A...633A.160C: z-dependent T_dust, MBB scaled to ALMA, CMB, MAGPHYS comparison.
- 2018ApJ...859...35G: CIGALE with AGN torus, with/without SPIRE test.
- 2026ApJ..1001..131C: CIGALE UV-to-radio, AGN, MAGPHYS cross-check.
- 2024ApJ...962....1S: CIGALE for a z=6 quasar, f_AGN, SFR constant.
- 2020MNRAS.493.3744F: MR-MOOSE for blended QSO and companion.
- 2024A&A...690A..55S: super-deblending and STARDUST.
- 2014ApJ...790..160S: two-temperature fit and free-parameter recovery.
- 2017MNRAS.465.4390B: averaging two (T, beta) assumptions.
- 2020ApJ...904..130V: 47 K/1.6 for quasar hosts and its factor 2-3 systematic.
- 2024A&A...691A.133V: general opacity with mid-IR slope and CMB correction.
- 2018MNRAS.475..448T: Galactic MCMC MBB fit (T and beta free).
- 2021A&A...656A..46M: grey-body plus free-free plus synchrotron for a nuclear starburst.
- 2020A&A...641A.155V: AGN thresholds and <U> from L_IR / M_dust.
