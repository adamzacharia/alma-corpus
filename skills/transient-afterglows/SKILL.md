---
name: alma-transient-afterglows
description: "Measure and model mm/radio afterglows of GRBs, TDEs, FBOTs, supernovae and gravitational-wave counterparts with ALMA: light curves and SEDs, synchrotron breaks (self-absorption, injection nu_m, cooling nu_c) and segment slopes, closure relations, forward versus reverse shock, energy injection, jet breaks and off-axis or structured jets, energetics and circumburst density (ISM versus wind), equipartition analysis of non-relativistic outflows, and mm polarization. Use when fitting or reproducing an afterglow model, choosing afterglowpy/boxfit/ScaleFit/redback, planning ToO follow-up, or checking someone else's afterglow parameters. Built from 35 ALMA papers (2012-2026), 30 of them on transients."
---

# Radio/mm transient afterglows

ALMA gives the mm point of a broadband synchrotron SED, often the only band near the peak frequency, mostly free of
interstellar scintillation. Papers turn light curves and SEDs into spectral breaks, an electron index p, a density
profile, energetics and jet geometry. Two mistakes matter most: (1) mixing conventions (sign of alpha and beta,
which break is the SED peak, how energy injection or density is parametrised, which code lacks self-absorption) so
that a "reproduced" parameter is not the same quantity; (2) forcing one forward-shock model onto data that need a
reverse shock, energy injection or a second component, where the radio SEDs are often what breaks the model
(2024ApJ...974..279D, 2022MNRAS.512.2337D, 2017MNRAS.464.4624S).

Scope of the evidence: the pack has 35 papers; 5 are regex hits off topic (lensed SMG, YSO burst, HH 211, two
z > 12 galaxies). Of the 30 on topic, 19 model afterglow or outflow emission, 3 only measure afterglow fluxes or
limits, 7 study GRB or FRB host galaxies, and 1 is a phased-ALMA pulse search (my reading of the pack). The pack is
thin: most numbers below rest on one or two papers. Lines marked "(card)" come from a single methods card, not the
pack excerpts. Cross-reference `variability-time-domain` (is a flux change real), `free-free-synchrotron` (thermal
versus non-thermal continuum), `polarization-magnetic-fields` and `sed-fitting` (host SFRs).

## Agent checklist

1. Fix conventions before any fit: write `F_nu ∝ t^alpha nu^beta` (or the paper's sign) and keep it. Papers use
   both: "decays with index 1.65" and p = 4alpha/3 + 1 (2022MNRAS.512.2337D) versus alpha = -1.62 after the break
   (2023NatAs...7...80U).
2. Get fluxes, not projects: ALMA afterglow papers measure point sources with CASA `imfit` on archive pipeline
   images (2024ApJ...974..279D, 2024NatAs...8..774B, 2025ApJ...993L...6N card). Fetch those products only.
3. Add a flux-scale systematic in quadrature: default 5% in Band 3 and 10% in Band 7 (2022MNRAS.512.2337D card;
   5% also in 2024ApJ...974...18C card and 2024NatAs...8..774B card). Most cards say it was not stated (8 entries).
4. Decide the medium with closure relations plus one independent test (peak-flux argument in
   2024ApJ...974..279D; temporal and spectral indices agreeing in 2019ApJ...870...59S). If neither ISM nor wind
   passes both, do not fit a physical model yet: add a component.
5. Pick the established code: afterglowpy (3 papers) or boxfit (4) for jets, ScaleFit for boxfit-based fits, redback
   for model libraries and comparison, Chevalier/Matsumoto-Piran equipartition for non-relativistic outflows. Do not
   write your own closed-form fitter for a published comparison. Know each code's gaps (afterglowpy: no
   self-absorption, no reverse shock, no wind, 2025ApJ...985..124L).
5b. Non-relativistic outflows (TDEs, SNe, FBOTs; general practice plus Step 6 below): fit each epoch's SED for
   the self-absorption peak (nu_p, F_p) with a smoothed broken power law, then convert with equipartition to
   R, B, E, n and velocity; the time series of R and n gives the outflow speed and density profile. Before
   fitting: interpolate non-simultaneous bands to a common epoch, inflate cm-wave errors for interstellar
   scintillation (negligible at mm), subtract host emission at low frequency, and state the geometry factors
   and epsilon_e, epsilon_B. R depends only weakly on departures from equipartition, E strongly; say which
   results depend on that assumption.
6. When the data are silent, fix microphysics at epsilon_e = 0.1, epsilon_B = 0.01, xi_N = 1, theta_obs = 0
   (2021ApJ...912...21E, 2026MNRAS.550g1193B, 2017ApJ...850L..21K) and say every inferred energy and density is
   conditional on them (2026MNRAS.550g1193B).
7. Sample, do not grid-guess: emcee with 64 walkers, 75,000 steps, 30,000 burn-in, tripled if not converged
   (2025ApJ...985..124L), broad uniform or log-uniform priors (2018ApJ...862...94L).
8. Minimum validation: overplot posterior draws on every band (250 draws in 2026MNRAS.550g1193B), check the radio
   SEDs separately (2024ApJ...974..279D), and compare models by evidence (log Bayes factor 42.5 in
   2026MNRAS.550g1193B), not by eye.
9. Write down: t0 and frame, data excluded and why, fixed parameters, priors, sampler settings, code version,
   regime ordering (nu_a, nu_m, nu_c), and which results are limits.

## When to use

- Broadband GRB afterglow modelling with ALMA epochs: 2017PASJ...69...20H, 2018ApJ...862...94L,
  2022MNRAS.512.2337D, 2024ApJ...974..279D, 2017MNRAS.464.4624S, 2019Natur.575..459M, 2026MNRAS.550g1193B.
- Orphan or off-axis afterglows and GW counterparts: 2025ApJ...985..124L, 2017ApJ...848L..21A, 2017ApJ...850L..21K.
- TDE, FBOT and supernova outflows from SED peaks: 2026ApJ...998..111C, 2024ApJ...974...18C, 2025ApJ...992L..18S,
  2025ApJ...993L...6N, 2019ApJ...870...59S. Late-time limits on jets and engines: 2021ApJ...912...21E.
- mm polarization of afterglows: 2019ApJ...884L..58U, 2019ApJ...878L..26L, 2023NatAs...7...80U.
- Separating afterglow from host or supernova light: 2024NatAs...8..774B, 2025ApJ...992L..18S, 2019MNRAS.488.5029H.

## When not to use

| Situation | Use instead |
|---|---|
| Host-galaxy SFR, dust or gas of a transient host (2012ApJ...761L..32W, 2020MNRAS.496.4405H, 2021ApJ...915...46C, 2024ApJ...969..122Y, 2020ApJ...899..165A) | `sed-fitting`, `dust-continuum-mass`, `gas-mass-co-conversion`; but check for afterglow leakage into the host flux (2020MNRAS.496.4405H ran fits with and without radio points) |
| Millisecond pulses, FRBs, magnetars | Phased-array single-pulse search with PRESTO (2025A&A...701A.191V, 2021ApJ...912...21E) |
| Is the flux change real at all? | `variability-time-domain` first |
| Thermal free-free versus synchrotron in a steady source | `free-free-synchrotron`, `spectral-index` |
| Afterglow as a backlight for absorption lines | `absorption-lines` (2018A&A...620A.119D) |

## Steps

1. **Assemble the data and time axis.** Goal: one table of time since trigger, frequency, flux, error, upper-limit
   flag and source. Fix z and d_L (2024ApJ...974..279D fixes z = 1.160, d_L = 2.52e28 cm) and the cosmology.
   Convert X-ray fluxes to a flux density at one energy (5 keV with beta = -1 in 2025ApJ...985..124L). Correct
   optical for Galactic extinction and fit host extinction (SMC curve in 2024ApJ...974..279D, 2017MNRAS.464.4624S).
   GCN points without errors need an assumed error that cannot dominate the fit (2026MNRAS.550g1193B).
2. **Measure ALMA fluxes.** CASA `imfit` point source on pipeline images (2024ApJ...974..279D, 2024NatAs...8..774B);
   elliptical Gaussian fixed to the beam (2024ApJ...974...18C card); `imstat` for rms (2025ApJ...992L..18S card).
   Image each spectral window for an in-band index (2018A&A...620A.119D: beta = +0.39 +/- 0.13 in Band 3;
   2019ApJ...878L..26L: about -0.4 between 91.5 and 103.5 GHz). Use natural weighting for faint points
   (2012ApJ...761L..32W). State peak or integrated flux; cards flag this as unstated (2022MNRAS.512.2337D).
3. **Clean the data set.** Subtract host or nucleus emission (power-law host SED, under 10% of the flux in
   2025ApJ...992L..18S; host-subtracted UVOT in 2022MNRAS.512.2337D). Treat cm points as scintillating: three
   orphan afterglows scintillate below about 10 GHz (2025ApJ...985..124L card), while the 97.5 GHz modulation index
   was <~2.5% (2024ApJ...974..279D card). Exclude what the model cannot describe and list it
   (2024ApJ...974..279D excludes uvw2, X-rays before 0.01 d, radio after the rebrightening; 2017MNRAS.464.4624S
   drops UVOT UV and u). Handle limits in the likelihood, not by dropping them (penalty against a zero-flux point,
   2025ApJ...985..124L).
4. **Describe empirically.** Power-law and smoothly broken power-law fits to each light curve and SED
   (2017PASJ...69...20H, 2022MNRAS.512.2337D, 2023NatAs...7...80U: break at 3.77 +/- 0.35 d, alpha 0.26 then -1.62).
   Build SEDs at chosen epochs (1200 s, 6800 s, 21600 s, 1 d in 2022MNRAS.512.2337D), interpolating light curves
   with power laws to a common time (2024ApJ...974..279D card). Do not average a whole band across epochs where the
   beam changes (2019ApJ...870...59S).
5. **Apply closure relations.** Goal: regime, medium and p. Check slow cooling (nu_m < nu_c, 2024ApJ...974..279D,
   2019ApJ...884L..58U). Examples: p = 2.50 +/- 0.16 from alpha = 1.1 in ISM (2022MNRAS.512.2337D); p = 2.373 from
   t^-1.53 in wind, then spectral slopes -0.687 and -1.187 around nu_c (2019ApJ...870...59S). Decision rule: accept a
   medium only if the predicted optical or mm slope and the peak flux both agree (2024ApJ...974..279D ruled out ISM
   because the predicted peak was over ten times the mm constraint).
6. **Identify components.** An early mm peak with a steep decay and SEDs a forward shock cannot fit points to a
   reverse shock (2022MNRAS.512.2337D: FS p = 2.50, RS p = 2.80; 2019ApJ...878L..26L: RS break at 24 +/- 4 GHz).
   Test self-consistency by scaling FS parameters by the ejecta Lorentz factor (peak flux matched to 5% in
   2018ApJ...862...94L). A late mm rebrightening: test energy injection and a shell-collision RS against all bands
   (2024ApJ...974..279D: neither captures every band, RS not unique). Refreshed two-component jets: compare by
   Bayes factor (2026MNRAS.550g1193B).
7. **Fit a physical model.** Use the code that has the physics you need (Software table). Fit in stages: optical,
   then optical + X-ray, then all bands, and repeat with and without inverse-Compton cooling and with finite and
   infinite Gamma_0 (2025ApJ...985..124L). Free versus fixed t0 changed Gamma_0 from 204 to 81
   (2025ApJ...985..124L): report which.
8. **Jet geometry and energetics.** A jet break gives theta_j and beaming-corrected energy (13.44 +/- 0.35 deg and
   1.27e50 erg in 2018ApJ...862...94L; 8.8 deg from boxfit in 2017PASJ...69...20H). No break: assume spherical
   (2024ApJ...974..279D) and quote theta_j as a lower limit by inverting the Chevalier and Li relation
   (2024ApJ...974..279D card). Off-axis: grid or fit theta_obs with boxfit (41 deg in 2017ApJ...850L..21K;
   20-40 deg in 2017ApJ...848L..21A). Structured jets: state core angle, profile indices and whether lateral spreading
   is included (2026ApJ...998..111C: a ≈ b ≈ 12, q ≈ 12, no spreading, ad-hoc epsilon_e ∝ t^4).
9. **Non-relativistic outflows (TDE, FBOT, SN).** Fit each SED for peak flux and frequency (GS02-based weighted model
   with both nu_a < nu_m and nu_m < nu_a in 2026ApJ...998..111C card; nu_m < nu_a < nu_c with the peak at nu_a in
   2024ApJ...974...18C card). Convert to R, B, E, n with equipartition (Chevalier 1998 with epsilon_e = epsilon_B =
   0.1 and f = 0.5 in 2025ApJ...992L..18S card; Barniol Duran 2013 in 2024ApJ...974...18C card; off-axis version of
   Matsumoto and Piran in 2026ApJ...998..111C, 2025ApJ...993L...6N). Fit R(t) for the launch date
   (2024ApJ...974...18C: 46 d from all data, about 210 d from late epochs) and n(r) for the CSM (rho ∝ r^-3.10 in
   2025ApJ...993L...6N).
10. **Polarization, if measured.** See Pitfalls; report P with debiasing and a systematic floor.

## Parameter defaults and ranges

| Parameter | Common choice | Range seen | Papers (count) | Notes |
|---|---|---|---|---|
| p (fixed) | 2.2-2.6 | 2.2, 2.43, 2.5, 2.6 | 4 | 2017ApJ...848L..21A, 2017ApJ...850L..21K, 2021ApJ...912...21E, 2019Natur.575..459M |
| p (fitted) | 2.1-2.5 | 1.64-2.80 | 6 | 2.079 (2018ApJ...862...94L), 2.28 (2024ApJ...974..279D), 1.81 (2017MNRAS.464.4624S), 1.64 (2026MNRAS.550g1193B) |
| p prior | [2, 3] | [1.4, 3.1], [2, 4] | 3 | 2025ApJ...985..124L, 2026MNRAS.550g1193B, 2024ApJ...974...18C card |
| epsilon_e (fixed) | 0.1 | 0.07-0.1 | 6 | 2021ApJ...912...21E, 2017ApJ...850L..21K, 2026ApJ...998..111C, 2017ApJ...848L..21A, 2026MNRAS.550g1193B, 2019Natur.575..459M (0.07) |
| epsilon_B (fixed) | 0.01 | 8e-5 to 0.01 | 4 | 0.01 (2021ApJ...912...21E, 2026MNRAS.550g1193B), 1e-3 (2026ApJ...998..111C), 8e-5 (2019Natur.575..459M); fitted 0.24 in 2024ApJ...974..279D |
| epsilon_B grid | | 1e-5 to 1e-2 | 1 | 2017ApJ...850L..21K |
| xi_N | 1 | fixed | 3 | 2024ApJ...974..279D, 2017ApJ...850L..21K, 2026MNRAS.550g1193B |
| theta_obs | 0 when on-axis | 0-45 deg grid; 30-90 deg | 4 | 2017PASJ...69...20H, 2024ApJ...974..279D, 2017ApJ...850L..21K, 2021ApJ...912...21E |
| theta_c prior | | 0.02-0.78 rad | 1 | 2025ApJ...985..124L; theta_obs/theta_j <= 3/2 in 2026MNRAS.550g1193B |
| log Gamma_0 prior | | [0, 3] | 1 | 2025ApJ...985..124L |
| n0 (ISM) | fitted | 1e-4 to 1e-1 grid; log n0 in [-5, 2] | 3 | 2017ApJ...850L..21K, 2026MNRAS.550g1193B; fitted 3.2e-4 in 2018ApJ...862...94L |
| A_* (wind) | fitted | 4.7e-3 | 1 | 2024ApJ...974..279D |
| E_K,iso | fitted | 1e47-1e53 grid; log in [44, 54] | 2 | 2017ApJ...850L..21K, 2026MNRAS.550g1193B |
| Equipartition | epsilon_e = epsilon_B = 0.1, f = 0.5 | p = 3 | 2 | 2025ApJ...992L..18S card, 2025ApJ...993L...6N card |
| MCMC | emcee, 64-128 walkers | 75k-225k steps | 3 | 2025ApJ...985..124L, 2018ApJ...862...94L (128 chains, 3% init dispersion) |
| Error floor | 10% | | 1 | 2018ApJ...862...94L |
| Flux-scale systematic | 5% Band 3, 10% Band 7 | 2-10% | 4 | 2022MNRAS.512.2337D, 2024ApJ...974...18C, 2024NatAs...8..774B, 2019ApJ...878L..26L (cards) |

The paper should report every fixed value, the prior ranges, whether p < 2 was allowed (it was in
2026MNRAS.550g1193B and 2017MNRAS.464.4624S; general practice: p < 2 needs an upper electron cutoff), and posteriors
with asymmetric errors.

## Software

| Job | Package (pack count) | Setting that matters |
|---|---|---|
| Jet afterglow fits | afterglowpy (3): 2022MNRAS.512.2337D, 2025ApJ...985..124L, 2026MNRAS.550g1193B | Jet type (top hat, Gaussian, power law); ICC on or off; Gamma_0 finite; no SSA, RS or wind |
| 2D hydro jet templates, off-axis grids | boxfit (3) + Boxfit v2 (1): 2017PASJ...69...20H, 2017ApJ...850L..21K, 2017ApJ...848L..21A, 2021ApJ...912...21E | Run with a homogeneous medium (2017PASJ...69...20H); azimuthal resolution 20/30 versus 70 changes flux by up to 20% (2017ApJ...850L..21K) |
| boxfit-based MCMC | ScaleFit (1): 2024ApJ...974..279D | Spherical when no jet break; data exclusions |
| Model library + inference | redback (1) with nessai (1): 2026MNRAS.550g1193B | Two-component refreshed model, Bayes factor |
| Samplers | emcee (3), PyMultiNest/MultiNest (3), nessai (1) | Walkers, burn-in, convergence |
| Optical engine models | MOSFiT (1): 2021ApJ...912...21E | Gives E_K for jet breakout limits |
| ALMA photometry | CASA (6), imfit | Point source, beam fixed |
| Other radio | MIRIAD (1, ATCA): 2021A&A...650A.117N | |
| X-ray | HEASoft, XSPEC (1 each): 2022MNRAS.512.2337D | |

Several fits use codes that are not public (2023NatAs...7...80U and 2019Natur.575..459M, cards). Reproduce those
with afterglowpy or boxfit, and expect and report differences.

## Pitfalls

### Model conventions

- **Sign conventions.** F ∝ nu^-beta with beta = -1/3 below the peak (2022MNRAS.512.2337D, 2021A&A...650A.117N)
  versus F ∝ nu^beta with beta = -1 for X-rays (2025ApJ...985..124L). Afterglow slopes "alpha = -1/2 to 1/3"
  (2019MNRAS.488.5029H) are spectral, not temporal.
- **Spectral segments (general practice).** Slow cooling with nu_a < nu_m < nu_c: nu^2, nu^(1/3), nu^-(p-1)/2,
  nu^-p/2. With nu_m < nu_a the low end is nu^2 then nu^(5/2). The SED peak is nu_m for a relativistic jet and
  often nu_a for a non-relativistic outflow; 2026ApJ...998..111C fits both with weights, and the regime ordering
  changes every derived quantity.
- **Normalisation (general practice; the cards rarely state it).** Granot and Sari 2002 and the older sharp-break
  formulae differ in the coefficients of nu_m, nu_c and F_max and in break smoothness; the GS02 smoothing
  parameters used in 2026ApJ...998..111C (card) are s1 = 1.06, s2 = 1.76 + 0.05p, s4 = 3.63p - 1.60. Injection
  nu_m depends on whether epsilon_e or epsilon_e(p-2)/(p-1) is the parameter; cooling nu_c depends on whether
  Compton Y is included (the ICC switch in 2025ApJ...985..124L). Match the paper's choice before comparing numbers.
- **Jet break form.** GS02 flux times [1 + (t/t_j)]^(-3/4) (2019ApJ...884L..58U) is an approximation, not a
  hydrodynamic jet; lateral spreading may be absent (2026ApJ...998..111C).
- **Energy injection.** E ∝ t^(1-q) with q = -1.88 (2024ApJ...974..279D), index m = 0.35 (2018ApJ...862...94L) and
  E_iso ∝ t^0.25 (2023NatAs...7...80U) are different parametrisations; convert before comparing.
- **Density.** n0 (s = 0) versus n = n0 R^-s with s = 2 (2019Natur.575..459M), wind A_* (2024ApJ...974..279D),
  and mass-loss rate at an assumed v_w = 1000 km/s (2025ApJ...993L...6N). Off-axis TDE density uses
  n_ext = n_e/(4 Gamma^2) (2024ApJ...974...18C).
- **Degeneracies.** Unlocated nu_a leaves parameters degenerate (2018ApJ...862...94L, 2019ApJ...878L..26L);
  xi_N < 1 makes energies lower limits (2022MNRAS.512.2337D); equipartition energies are lower limits
  (2025ApJ...993L...6N); sparse early data leave theta_obs and Gamma_0 degenerate (2025ApJ...985..124L).

### Observing and data

- Flux-scale uncertainty is the most common unstated setting (8 card entries, pack aggregates); high-frequency
  epochs can suffer decorrelation in bad weather (2017ApJ...848L..21A) and Band 9 may never be observed
  (2021A&A...650A.117N).
- ToO timing: the polarized reverse shock was caught by starting 2.2 h after the burst (2019ApJ...878L..26L card);
  TDE and FBOT epochs came from DDT programs (2025ApJ...992L..18S card, 2025ApJ...993L...6N card).
- Astrometry: ALMA astrometry bugs left an unexplained offset in 2017PASJ...69...20H; check against field sources
  (2021A&A...650A.117N used two quasars).
- Unexplained single points happen: the ALMA flux at 227 d in 2025ApJ...992L..18S could not be accounted for.
  Say so rather than drop it silently.
- Free-free absorption makes equipartition parameters unphysical (2025ApJ...993L...6N); SLSNe can stay optically
  thick to free-free at 100 GHz (2021ApJ...912...21E). For a late off-axis jet that peaks at GHz, a 100 GHz upper
  limit constrains little (2021ApJ...912...21E). That is specific to non-detections of late jets: a detected mm
  point above the self-absorption peak is usually the main lever on the optically thin slope (p) and on a cooling
  break (general practice), so never drop or down-weight ALMA detections in an SED fit.

### Polarization

- ALMA Band 3 afterglow polarization is sub-percent: 0.27 +/- 0.04% at 5.2 d (2019ApJ...884L..58U card),
  0.87 +/- 0.13% falling to 0.60 +/- 0.19% with the angle rotating by about 54 deg (2019ApJ...878L..26L card),
  <0.6% at 3 sigma against optical 1.3% (2023NatAs...7...80U card). Compare with D-terms of about 1% and the
  calibrator stability (<0.02%) these papers checked (cards).
- Debias P from Monte Carlo realisations of Q and U (1e5 in 2019ApJ...878L..26L card) and measure at the Stokes I
  position and beam. Non-simultaneous optical and radio polarimetry limits conclusions (2019ApJ...884L..58U).
- The pack has no ALMA paper that models off-axis or structured-jet polarization; interpretations are RS field
  order, Faraday depolarization by cool electrons, or plasma-scale fields (the last refuted in 2023NatAs...7...80U,
  card). Treat off-axis polarization predictions as outside this evidence.

## Verification checks

- Posterior draws over every band (2026MNRAS.550g1193B), radio SEDs checked separately (2024ApJ...974..279D).
- Model also explains X-ray and optical (2023NatAs...7...80U); predicted X-ray does not exceed the data
  (2019ApJ...884L..58U); SSC prediction checked against X-rays (2017PASJ...69...20H).
- Temporal and spectral slopes give the same p independently (2019ApJ...870...59S).
- Evidence-based model comparison (2026MNRAS.550g1193B, 2017MNRAS.464.4624S), and honesty when no model is
  statistically good (36 fits, none good, in 2017MNRAS.464.4624S).
- Code resolution or setting tests (boxfit azimuthal resolution in 2017ApJ...850L..21K; ICC and Gamma_0 variants
  in 2025ApJ...985..124L); launch date compared with the first detection (2024ApJ...974...18C).
- A referee adds: parameters recovered from a simulated light curve with your sampling and errors; the fit redone
  with the cm points inflated for scintillation; every limit marked as a limit.

## Source cards

Full list in `references/sources.md`. Most informative: 2024ApJ...974..279D, 2025ApJ...985..124L,
2026MNRAS.550g1193B, 2022MNRAS.512.2337D, 2018ApJ...862...94L, 2019ApJ...878L..26L, 2019ApJ...884L..58U,
2023NatAs...7...80U, 2026ApJ...998..111C, 2024ApJ...974...18C, 2025ApJ...993L...6N, 2025ApJ...992L..18S,
2017ApJ...850L..21K, 2017ApJ...848L..21A, 2021ApJ...912...21E, 2017MNRAS.464.4624S, 2019Natur.575..459M,
2019ApJ...870...59S, 2017PASJ...69...20H, 2024NatAs...8..774B.
