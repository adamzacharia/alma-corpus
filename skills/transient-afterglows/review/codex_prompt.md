# Review task: an ALMA agent skill against its evidence pack

You are reviewing a skill file (SKILL.md, plus an optional parameters table) that another model wrote from the
EVIDENCE PACK below. The pack is built from methods cards of published ALMA papers; every quote in it was
mechanically verified against the paper text. The skill will be given to research agents that analyse ALMA data,
so wrong defaults or misattributed practice cause real errors. You have no file access: everything you need is in
this message.

Check, in this order:

1. **Attribution.** Every number, range, default, software attribution and "papers do X" claim that cites
   bibcodes: does the pack support it for those bibcodes? Flag claims the pack contradicts, claims cited to a paper
   whose pack entry says something else, and counts that do not match the pack aggregates.
2. **Unsupported practice.** Statements presented as literature practice with no support in the pack. (General
   background marked as general practice is fine if it is correct.)
3. **Scientific correctness.** Wrong formulas, wrong units, wrong CASA task/parameter names or semantics, unsafe
   advice, or a recommendation that contradicts the evidence.
4. **Omissions.** Important pitfalls, assumptions or validation checks that are clearly present in the pack (for
   example in "Limitations the authors admit" or "Settings cards flag as needed but not stated") but missing from
   the skill.
5. **Usability.** Anything an agent would misread or could not act on.
6. **Contamination and team lessons.** If a WRITER CONTEXT section is present: flag any mention of, or hint at,
   the held-out evaluation targets it names (objects, papers, or their numbers). Team lessons may appear only as
   labelled team experience in general form; flag any that is presented as literature practice or carries
   numbers not in the context.

Some skills are *workflow* skills (paper reproduction, claim verification, archival reuse, software map). Their
packs aggregate card fields such as inherited conventions, missing-for-reproduction items, validation checks and
software used. Lines marked "(card)" in the pack are the card author's inference; the skill should say so when it
leans on one. Review them with the same rules.

Output format (Markdown, nothing else):

```
# Codex review: <slug>
VERDICT: CLEAN | FIX
## Findings
- SR-01 | high|medium|low | <attribution|unsupported|science|omission|usability> | <the claim, quoted briefly> | <problem, citing the pack line or bibcode> | <concrete fix>
- SR-02 | ...
## Notes
<at most 5 lines: overall quality, anything the writer should know>
```

Use `VERDICT: CLEAN` only when there are no high or medium findings. Be specific and terse; do not restate the
skill. Do not invent pack content: when you say the pack contradicts a claim, cite the pack line.

=== SKILL.md (transient-afterglows) ===
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

=== WRITER CONTEXT (readers, team lessons, contamination rule; not a literature source) ===
# Who reads these skills, and what went wrong in their runs (CosmicCoder meeting notes, Oct-Nov 2026)

Distilled from the CosmicCoder agent meeting notes (all pages) for skill writers. This file is for YOU, the writer.
Do not quote it as a literature source. Lessons below may appear in a skill only as clearly labelled team experience
("in CosmicCoder agent runs ...") and only in general form.

## The readers

The skills are read by research agents working on ALMA data: single Claude Code agents, research frameworks
(Denario, AutoResearch) and teams of agents (questioner, worker, reviewer/validator, editor) that post findings to a
shared forum and are graded against published papers or by astronomers. Tasks come in two shapes:

- **Bottom-up / reproduction**: given an ALMA dataset (and maybe a literature summary), find what the paper found.
- **Top-down / novel**: given a research question, pick the method and the data, then answer it.

Evaluation decomposes a paper into (hypothesis, experiment, result, finding) tuples and asks: are the individual
experiments correct, are the final conclusions correct, are the findings significant, are they novel. Experts want
each experiment traceable to code.

## Lessons from the runs (write skills that prevent these)

1. **Agents reimplemented a naive version of a standard package** (a cube kinematics fitter) and got a worse
   measurement than the paper. Agents need to know which established tool does the job and reach for it.
2. **One dataset is rarely enough.** Good projects needed several datasets to clear up inconsistencies and to check
   earlier literature claims, plus tables and numbers from other papers. One framework gave up when a table from
   another paper was needed.
3. **Downloading whole projects is a trap.** An agent tried to fetch about 4 TB of raw data by project code; the
   analysis needed only specific products, which astroquery could fetch. Older-cycle data that needed
   reprocessing could not be processed in that environment (CASA/tclean was not installable on one HPC system).
   Archive image products were often usable as delivered.
4. **Unstated and inherited conventions break reproductions.** A paper in a series reused corrections (for
   example flux and number recovery from artificial source insertion) and design choices from its earlier
   papers without restating them. Reproduced images were noisier than the paper's and nobody could tell what
   extra preprocessing the authors had done.
5. **"Done" must mean executed and checked.** A framework's judge approved tasks when code had been written but
   not run. Stricter gates (the file ran, outputs exist and look sane) fixed it.
6. **Context flooding.** Agents printed huge raw tables into their context, costing millions of input tokens.
   Summarise; write tables to files.
7. **Overconfident conclusions.** One system's conclusions were "more confident than its evidence supports".
   Single agents stopped after minutes having characterised the obvious bright component and missed the faint
   compact signal that was the real finding.
8. **No stopping criterion.** Open-ended runs became a money pit, agents going back and forth verifying claims
   they could only speculate about given the data. Agents need a rule for when the evidence is enough and when a
   question cannot be settled with the data in hand (and should be written down as open).
9. **Verifiers and editors help.** Adding a verifier/editor that asked "what is the most important question?"
   raised scores; teams with worker and validate roles beat strict pipelines; adaptive iterative loops beat
   heavy fixed pipelines. Staged work (each stage with tests and an answer key, stop or retry by stage) worked for
   model reproductions; open items needing expert confirmation were recorded rather than forced.
10. **Novelty is easy to fake.** Ideation agents treated unpublished data as proof of a novel question without
    checking whether the same question had been answered with other datasets, and repackaged an observing
    proposal into analysis tasks instead of distinct hypotheses.
11. **Results need tolerances.** Reproductions reported agreement to stated precision (for example within 0.3% or
    "within reading precision" of a figure) and explained each remaining mismatch (smoothing of a published
    figure, a possible table typo) instead of declaring success or failure overall.

## Contamination rule (critical)

The team's evaluation tasks are held out of the corpus. Never name, describe or hint at their targets or results
in a skill: no L1521F / L1521F-IRS, no "CMF across Galactic environments" protocluster series, no z~6 quasar-host
[CII] kinematics sample results, no SZ quasar-feedback detection in HE 0515-4414, no specific numbers from those
papers. Write general practice from the pack. If a lesson above came from one of those tasks, state it only in
general form (as it is phrased above).

=== EVIDENCE PACK (transient-afterglows) ===
# Evidence pack: Radio/mm transients: GRB, TDE and supernova afterglow modelling (`transient-afterglows`)

Scope: synchrotron afterglow modelling of explosive transients: spectral breaks, forward/reverse shocks, jet geometry, energetics and density from mm light curves

Built from 35 non-held-out ALMA papers whose methods cards passed mechanical evidence verification (every quote below is verbatim from the paper). Years 2012-2026.
Matcher (regex over analysis steps): `afterglow|gamma[- ]ray burst|\bgrbs?\b|forward shock|reverse shock|boxfit|afterglowpy|tidal disruption|\btdes?\b|fbot|blast ?wave|kilonova|\bfrbs?\b|supernova (?:light|radio)`
Tagging is by regex, so a few papers may be off-topic: ignore those.

## Aggregates over all papers

### Science fields
- transients: 28
- high_z_galaxies: 11
- star_formation: 8
- nearby_galaxies: 4
- other: 2
- stellar_physics: 1
- astrochemistry: 1

### Software named in the matched steps
- casa: 6
- boxfit: 3
- emcee: 3
- afterglowpy: 3
- pymultinest: 2
- scalefit: 1
- bateconvert: 1
- battblocks: 1
- heasoft: 1
- batmaskwtevt: 1
- uvotsource: 1
- headas: 1
- xspec: 1
- mercurius: 1
- drp: 1
- presto (rfifind, single_pulse_search.py): 1
- boxfit v2: 1
- mosfit: 1
- prospector: 1
- aton: 1
- bagpipes: 1
- swift burst analyser: 1
- nessai: 1
- redback: 1
- miriad: 1
- multinest: 1
- alma science pipeline software: 1
- tclean: 1

### Fitting methods (most common phrasings)
- chi-square fits, no sampler stated: 1
- emcee MCMC; priors and likelihood not stated: 1
- Power-law and Band function fits in XSPEC for BAT/XRT spectra; Bayesian blocks for BAT duration: 1
- Smoothly broken power-law fits to light curves and SEDs: 1
- Nested sampling (MERCURIUS/PyMultiNest) with gamma prior on T_dust and Gaussian prior on beta: 1
- Point-source model and extended 2-D Gaussian: 1
- Polynomial FIR SED approximation; low-order polynomial residuals assess calibration uncertainty.: 1
- Parameters chosen by hand to roughly match the observation, no formal fit: 1
- emcee MCMC with uniform priors: 1
- emcee EnsembleSampler, uniform priors, simple Gaussian likelihood per data point; radio upper limits for AT 2020blt pen…: 1
- Markov chain Monte Carlo fits to multicolor optical light curves using MOSFiT for magnetar/ejecta parameters.: 1
- best-matching templates identified; method not stated: 1
- Nested sampling with nessai using priors and conditions in Table 7: 1
- MultiNest Bayesian inference; models CM, WM, TS compared via evidence and reduced chi2: 1

### Validation checks used
- chi2/nu reported: 1
- Compared SSC analytic prediction with X-ray data: 1
- Compared with TOUGH sample SFR: 1
- Predicted optical spectral index compared with measured beta_O = -0.63+-0.08; ISM ruled out via peak flux argument: 1
- Highest-likelihood model compared with optical, X-ray and radio SEDs; radio SEDs found incompatible with the model: 1
- Models compared by eye with higher frequency radio bands; neither captures the other radio bands: 1
- Chi-squared per degree of freedom reported for spectral fits: 1
- Comparison with standard FS predictions in afterglowpy showing underestimation of early X-ray/optical and high-frequenc…: 1
- Posteriors shown; TUNER fit compared with MERCURIUS: 1
- Pixel brightness histogram fitted with Gaussian (sigma=0.096 mJy/beam); spurious-peak probability between 5e-4 and 5e-3: 1
- Compared SEDs with optical/NIR photometry and with optical SFRs: 1
- 70 and 160 μm ratios agree within errors, supporting the 154 μm correction.: 1
- Model PV diagrams roughly consistent with observed PV structures: 1
- Temporal decay and spectral indices independently agree with the fireball expectations: 1
- Peak flux matches within 5%: 1
- model compared with observations and with earlier modelling of the same events: 1
- Tested multiple SN yield tables (Bianchi & Schneider 2007; Zhukovska et al. 2008), AGB yield tables (Ferrarotti & Gail …: 1
- Continuum flux consistent with H14: 1
- Azimuthal resolution 20/30 compared with 70: flux within 20%: 1
- Bayesian model comparison via log Bayes factor and information score from nessai, plus 250 posterior draws overplotted …: 1
- Astrometry checked against two known quasars B2258-391 and NVSS J230132-385927: 1
- Consistent with SED-modelling A_V = 0.25 +/- 0.10 from Carniani24b: 1
- Grid of 36 fits with different data cuts; none statistically good: 1
- Compared predicted $\nu_m$ across viewing angles $\theta_{\rm obs}=70-90\,\rm deg$ against observed SEDs: 1
- Launch dates compared against the first detection at delta t = 40 days: 1
- Model also explains X-ray and optical: 1
- Model curves compared by eye with data (Fig. 3, Extended Data Figs 6, 7): 1
- Computed X-ray light curve does not overwhelm the observed one: 1
- Correction is below 10% of the flux measurements: 1

### Key parameters and settings (bibcode: value)
- 2017PASJ...69...20H: on-axis case, theta_obs=0
- 2024ApJ...974..279D: z fixed to 1.160 and d_L = 2.52e28 cm
- 2024ApJ...974..279D: Excluded: uvw2 data, radio data after 8.2 days, X-ray t<0.01 d, first ATCA epoch, radio <16.7 GHz at 6.6 d
- 2024ApJ...974..279D: Other forward shock parameters kept fixed; lower frequency radio bands excluded
- 2022MNRAS.512.2337D: UVOT extraction radius = 3'' aperture corrected to 5''; MASTER aperture size = 3.9''
- 2022MNRAS.512.2337D: SED epochs: 1200 s, 6800 s, 21600 s, 1 d; FS spectral indices fixed to beta_low = -1/3 and beta_up = 0.75 (p ~ 2.50)
- 2026A&A...706A.174A: Rest-frame wavelengths 10 to 10^3 micron fitted
- 2026A&A...706A.174A: T_dust gamma prior (shape a=1.5); beta_dust Gaussian prior centred 1.8, sigma 0.25
- 2012ApJ...761L..32W: natural weighting
- 2012ApJ...761L..32W: 3-sigma upper limit 0.33 mJy for GRB 021004
- 2024A&A...688A...8W: HAWC+ calibration comparison source exceeds PACS by 15 ± 7%; taken into account in the analysis
- 2024A&A...688A...8W: Relative HAWC+ flux-calibration error 10%
- 2025A&A...701A.191V: Fluence limits: F_Band3 = 1330 mJy ms (37 antennas, 0.1 s width), F_Band1 = 1200 mJy ms (37 antennas, 0.1 s width), F_Band1 = 900 mJy ms (49 antennas, 0.1 s wi…
- 2025A&A...701A.191V: Integration times = 1, 1.5, and 2.5 hours; S/N = 6; pulsar period = 1 s; duty cycle = 10%
- 2021ApJ...909...11J: R_j = 0.2 arcsec; z_bo = 0.5 arcsec; c_s = 8 km/s; beta = 4; v_s = 14 km/s; bow shock thickness 0.3 arcsec
- 2019ApJ...870...59S: Radio decay t^-1.53 gives p=2.373; indices -0.687 below and -1.187 above the break
- 2020MNRAS.496.4405H: Filter effective wavelengths from the SVO Filter Profile Service
- 2018ApJ...862...94L: 128 chains, 10^4 posterior samples, 10% uncertainty floor
- 2025ApJ...985..124L: most runs: 64 walkers, 75,000 iterations, 30,000 burn-in; if not converged: 64 walkers, 225,000 iterations, 125,000 burn-in
- 2025ApJ...985..124L: broad uniform priors (Table of priors, e.g. log10 Gamma_0 in [0,3], theta_c in [0.02,0.78] rad, p in [2,3])
- 2025ApJ...985..124L: afterglowpy runs repeated with and without ICC and with Gamma_0 infinite and finite
- 2025ApJ...985..124L: X-ray fluxes converted to a 5 keV flux density with spectral index beta = -1
- 2021ApJ...912...21E: DM up to 5000 pc cm^-3 with step size 5; 256 us time resolution; 2 MHz channels; 7sigma threshold
- 2021ApJ...912...21E: theta_j = 10 deg; theta_obs = 30, 60, 90 deg; epsilon_e = 0.1; epsilon_B = 0.01; p = 2.5; f_j = 0.5
- 2026ApJ..1000..159M: Star formation start redshift z = 20 (GHZ2) and z = 30 (GS-z14-0)
- 2026ApJ..1000..159M: Yield metallicity range = 10^-4 to 0.1 Z_sun
- 2026ApJ..1000..159M: Larson IMF with α = 1.35 and M_ch = 0.35 M_sun (and M_ch = 10 M_sun for top-heavy test), mass range 0.1-100 M_sun
- 2017ApJ...850L..21K: theta_jet 5-45 deg, E_AG,iso 1e47-1e53 erg, eps_B 1e-5-1e-2, n 1e-4-1e-1, theta_obs 0-45 deg
- 2026MNRAS.550g1193B: For twocomponent_refreshed: fixed theta_obs = 0, log epsilon_e = -1, log epsilon_B = -2, xi_N = 1
- 2021A&A...650A.117N: Briggs robust = 0.0 to 2.0; uv taper FWHM = 5 arcsec
- 2025ApJ...987L...2H: [C II] limit L < 6e7 Lsun; metallicity Z/Zsun = 0.17
- 2025ApJ...987L...2H: Intrinsic beta_UV = -3; A_V = 0.3 mag
- 2017MNRAS.464.4624S: Flat (uniform/log-uniform) priors on all parameters except Galactic reddening (Gaussian, mu=0.56, sigma=0.04)
- 2017MNRAS.464.4624S: UVOT UV filters and u band excluded in best fits
- 2026ApJ...998..111C: Top-hat jet: $f_A=f_V=(\Gamma\theta_j)^2$, $\theta_j=0.1$, $\epsilon_e=0.1$, $\epsilon_B=10^{-3}$, $\eta=1$; Structured jet: $k=0$, $q\approx 12$, $a\approx b\…
- 2021ApJ...915...46C: Briggs weighting with robust = 0.5
- 2021ApJ...915...46C: CO(1-0) velocity integration width = 180 km s^-1
- 2017ApJ...848L..21A: p=2.2 adopted; epsilon_e=0.1
- 2019Natur.575..459M: s = 0, eps_e = 0.07, eps_B = 8e-5, p = 2.6, n0 = 0.5, Ek = 8e53 erg


### Assumptions (bibcode: value)
- 2017PASJ...69...20H: homogeneous circumburst medium (ISM)
- 2017PASJ...69...20H: ALMAJ2300-0522 at same redshift as GRB
- 2024ApJ...974..279D: Slow cooling regime with nu_m < nu_c
- 2024ApJ...974..279D: theta_obs = 0 and xi_N = 1
- 2024ApJ...974..279D: Spherical jet (theta = pi/2)
- 2024ApJ...974..279D: Milky Way extinction (Fitzpatrick 1999, R_V=3.1, A_V=0.3271) and SMC host extinction curve (Pei 1992) with free A_V,host
- 2024ApJ...974..279D: LCDM cosmology Omega_m=0.315, H0=67.4
- 2024ApJ...974..279D: For the shell collision, collision time = start of rise (8.2 d), deceleration time = peak (18.1 d)
- 2022MNRAS.512.2337D: Galactic N_H = 5.6 x 10^20 cm^-2; afterglow and supernova negligible after 58 days in UVOT
- 2022MNRAS.512.2337D: Constant density external medium; standard fireball closure relations for FS
- 2026A&A...706A.174A: kappa = 8.94 cm2/g at 158 micron, appropriate for SN-ejected dust after reverse shock destruction
- 2019MNRAS.488.5029H: Afterglow spectral slopes alpha=-1/2 to 1/3 (Sari1998)
- 2012ApJ...761L..32W: Dust temperature from CE01 luminosity-dependent templates; cosmology H0=71, OmegaM=0.27, OmegaL=0.73
- 2024A&A...688A...8W: YSO FIR dust-continuum SED is continuous and featureless.
- 2025A&A...701A.191V: Phasing efficiency eta_p ~ 0.6; Band 3 T_sys = 74 K, G = 1.08 K/Jy; Band 1 T_sys = 45 K, G = 1.12 K/Jy
- 2025A&A...701A.191V: Missing pulsar spectral indices drawn from normal distribution with mean = -1.6 and std = 0.54
- 2019ApJ...870...59S: Generic fireball formalism with wind scaling; ISM scaling rejected
- 2020MNRAS.496.4405H: Radio emission may be contaminated by a long-lived radio afterglow
- 2018ApJ...862...94L: ISM environment; uniform priors, log-uniform for scale parameters
- 2018ApJ...862...94L: pressure behind RS equals that at FS; same p; constant microphysical parameters
- 2025ApJ...985..124L: homogeneous circumburst medium, single-shell approximation
- 2025ApJ...985..124L: Galactic extinction with R_V = 3.1; redshift z = 1.0272 for AT 2023lcr
- 2021ApJ...912...21E: Phasing efficiency factor of 0.9, nominal pulse width W = 10 ms, and beaming fraction f_b = 0.5
- 2021ApJ...912...21E: Constant density CSM; gamma_j = 1/(5 theta_j)
- 2026ApJ..1000..159M: Exponentially rising SFH parameterization and Larson IMF
- 2017ApJ...850L..21K: epsilon_e=0.1, xi_N=1, p=2.43, z=0.009854
- 2026MNRAS.550g1193B: Constant-density circumburst medium (n_0), z = 1.216, flat LambdaCDM cosmology (H_0 = 70 km s^-1 Mpc^-1, Omega_m = 0.3, Omega_Lambda = 0.7)
- 2021A&A...650A.117N: Isotropic emission, spectral slope beta = -1/3 or 0.7 for radio AG and beta = 0.7 for kilonova flare
- 2025ApJ...987L...2H: SMC-like reddening curve; intrinsic slope beta_UV = -3 (A_V is an upper limit)
- 2017MNRAS.464.4624S: SMC-like host extinction curve
- 2026ApJ...998..111C: Thin-shell geometry, locally spherical dynamics without lateral spreading, constant density external medium ($k=0$), and ad-hoc $\epsilon_e\propto t^4$ at earl…
- 2017ApJ...848L..21A: epsilon_e=0.1, eta_gamma=0.1
- 2024ApJ...974...18C: Constant outflow velocity for the linear-radius launch-date estimate
- 2023NatAs...7...80U: Uniform density medium, energy injection E_iso propto t^0.25
- 2019Natur.575..459M: Power-law density profile s=0 or s=2; power-law electron distribution
- 2025ApJ...993L...6N: Effective mass-loss rate computed for an arbitrary wind velocity of 1000 km/s
- 2019ApJ...884L..58U: ISM environment, slow cooling
- 2019ApJ...878L..26L: Omega_m=0.31, Omega_Lambda=0.69, H0=68 km/s/Mpc


### Limitations the authors admit
- 2017PASJ...69...20H: ALMA astrometry bugs reported; large offset not explained
- 2024ApJ...974..279D: Higher-frequency ATCA data at epoch three were dropped, losing temporal information
- 2024ApJ...974..279D: Possible unaccounted systematic uncertainties in ATCA calibration prevent excluding energy injection
- 2024ApJ...974..279D: Reverse shock model is not unique; two break frequencies unconstrained
- 2022MNRAS.512.2337D: MASTER has only two orthogonal polarizing filters at a single site and measures only Stokes Q, so an unfavorable polarization angle orientation could still hide a polarized afterglow.
- 2022MNRAS.512.2337D: Standard closure relations for a reverse shock in a constant density medium do not provide an acceptable fit to the SED evolution.
- 2022MNRAS.512.2337D: The estimated isotropic kinetic energy is only a lower limit because the fraction of accelerated electrons xi may be < 1 and Compton losses from the VHE component may suppress X-ray flux.
- 2026A&A...706A.174A: Stellar mass and other SED-derived properties highly uncertain because of Lupus-I extinction
- 2026A&A...706A.174A: Lens redshift not confirmed; MUSE and FORS2 data too poor
- 2026A&A...706A.174A: Dust mass strongly depends on the assumed kappa and optical depth
- 2026A&A...706A.174A: Unresolved data and fixed GDMR and [CO]/[H2] prevent tight gas-mass constraints
- 2026A&A...706A.174A: A minor AGN contribution cannot be ruled out
- 2019MNRAS.488.5029H: Dust property uncertainties for 070521 host underestimated because only one FIR photometric point
- 2019MNRAS.488.5029H: [CII] detection only S/N~4; possible ALMA observational bias
- 2012ApJ...761L..32W: GRB 080607 detection is marginal (3.3 sigma) with possible non-Gaussian noise; single-band photometry requires template dust temperature
- 2024A&A...688A...8W: ALMA resolution cannot resolve a possible disk; continuum sensitivity cannot constrain larger-scale dust.
- 2024A&A...688A...8W: Saturated (NEO)WISE burst photometry is unsuitable for quantitative conclusions.
- 2024A&A...688A...8W: Only three dust configurations and one burst shape were explored.
- 2024A&A...688A...8W: Main models simplify geometry, dust properties and burst-induced changes.
- 2024A&A...688A...8W: Larger grains could lengthen the afterglow and make FIR-based burst energies overestimates.
- 2024A&A...688A...8W: TORUS time-dependent modeling excludes line emission and chemical networks.
- 2025A&A...701A.191V: Every 18.192 s there is a drop-off in the time series caused by the phasing cycle of the array, and 30 minutes of data were unusable.
- 2025A&A...701A.191V: Pulses with small polarisation fractions or arriving outside the main integrated pulse profile phase window would not be detected by the selection criteria.
- 2025A&A...701A.191V: The sample size is limited to eight pulses over a limited energy range.
- 2025A&A...701A.191V: Phased ALMA surveys are unlikely to be sensitive to millisecond pulsars (MSPs).
- 2021ApJ...909...11J: Possible missing flux: MRS ~0.75 arcsec versus knot size ~1 arcsec; impact on the knot peak deviations unknown
- 2021ApJ...909...11J: Sub-knots are not spatially resolved, so shock structure analysis is limited to the knots
- 2019ApJ...870...59S: Combining whole-band data is less robust owing to beam changes and interpolation
- 2020MNRAS.496.4405H: Best templates are not unique; other configurations have similar reduced chi2
- 2020MNRAS.496.4405H: IMF test is simple and may mask IMF differences
- 2020MNRAS.496.4405H: Three hosts are only marginally detected (S/N ~5, ~4, ~3.5)
- 2020MNRAS.496.4405H: Reduced chi2 of 1 is not expected to be reached because errors are not perfectly estimated
- 2020MNRAS.496.4405H: GRB050915A has several host candidates; the closest one to the host position was chosen
- 2024ApJ...969..122Y: Sample size too small for statistical conclusions; FRB-site limit not constraining.
- 2020ApJ...899..165A: Clump sizes unreliable, not reported, because they are smaller than the beam
- 2020ApJ...899..165A: Cloud-scale depletion times are not consistently measurable owing to gas-star offsets
- 2018ApJ...862...94L: nu_a not constrained, causing parameter degeneracies; epsilon_e~0.9 problematic
- 2025ApJ...985..124L: afterglowpy lacks reverse-shock physics, which may affect radio observations
- 2025ApJ...985..124L: afterglowpy has no synchrotron self-absorption, so low-frequency radio data are overpredicted
- 2025ApJ...985..124L: afterglowpy supports only a homogeneous medium, with no stellar wind
- 2025ApJ...985..124L: Sparse early-time data leave viewing-angle and Lorentz-factor degeneracies unresolved
- 2021ApJ...912...21E: Short phased-VLA observation duration (~40 min per source) is prohibitively small for detecting intermittent FRBs.
- 2021ApJ...912...21E: ALMA 100 GHz observations are less constraining for obscured star formation rates and late-time off-axis jet afterglows because synchrotron emission peaks at lower (GHz) frequencies on these timescal…
- 2021ApJ...912...21E: CLOUDY models start at t > 1 yr in the source frame, so 100 GHz free-free transparency timescales shorter than 1 yr (1+z) rely on extrapolations.
- 2021ApJ...912...21E: Seven ALMA-observed SLSNe (LSQ14bdq, SN2015bn, SN2016ard, SN2017jan, SN2018ibb, SN2018hti, SN2018lfe) are expected to still be optically thick to free-free absorption at 100 GHz at the time of observ…
- 2026ApJ..1000..159M: It remains unclear whether an AGN contributes to the UV emission of GHZ2, requiring further observations to accurately constrain its stellar mass and potential AGN activity.
- 2026ApJ..1000..159M: Band-8 observations of GHZ2 are much shallower than Band-6 and less constraining on M_dust.
- 2026ApJ..1000..159M: If gas mass is not constrained via M_dyn - M_* and instead allowed to vary across f_gas = 0.1-0.9, it is impossible to disentangle dust models or place meaningful constraints on SFE without direct [C…
- 2026ApJ..1000..159M: Using M_dyn - M_* as a proxy for M_gas has an uncertain molecular-to-total gas fraction.
- 2017MNRAS.465L..89P: The association with the z=1.96 galaxy is not definitive
- 2017ApJ...850L..21K: Degeneracy due to few detections and large Epeak uncertainty
- 2026MNRAS.550g1193B: Public prompt-emission constraints are limited (Fermi/GBM was in the SAA, and nominal short-GRB classification relies on SVOM discovery notices).
- 2026MNRAS.550g1193B: The 10 GHz VLA measurement from GCN 41455 had no reported uncertainty, requiring an assumed uncertainty for modelling.
- 2026MNRAS.550g1193B: Host-frame afterglow extinction A_V^host is weakly constrained by only three photometric points (1 dof) and is sensitive to host-subtraction and cross-calibration systematics.
- 2026MNRAS.550g1193B: In the refreshed two-component jet model, microphysical parameters (epsilon_e, epsilon_B, xi_N) and viewing angle (theta_obs = 0) are fixed, so inferred energetics and density are conditional on thes…
- 2026MNRAS.550g1193B: Host galaxy association is ambiguous because LS DR10 imaging depth does not rule out a fainter near-coincident host, and Prospector SED results suffer from age-dust-metallicity degeneracies due to li…
- 2021A&A...650A.117N: Scheduled ALMA Band 9 observations could not be performed due to weather constraints.
- 2021A&A...650A.117N: The faint ATCA 5.5 GHz extended emission near the GRB site is at the ~5 sigma level, so there is no guarantee that it is real and it is too faint to split in time or frequency.
- 2021A&A...650A.117N: Small angular sizes (< 0.2''), faintness, and strong host foreground emission prevent MUSE from clarifying the nature of individual clumps C-G and K-M.
- 2021A&A...650A.117N: Low S/N in the outskirts of the galaxy prevents measuring E(B-V)_host, EW(Halpha), or a secure SFR at the GRB explosion site.
- 2021A&A...650A.117N: Apparent lower metallicity in region B and high velocity dispersions (~60 km s^-1) in the outskirts could be affected by low-number statistics or low S/N.
- 2025ApJ...987L...2H: H I mass from N_HI depends heavily on the assumed geometry
- 2025ApJ...987L...2H: A_V is only an upper bound on the dust in the line of sight
- 2017MNRAS.464.4624S: Poor temporal sampling limits constraints
- 2026ApJ...998..111C: Cannot currently distinguish between the delayed spherical outflow and prompt highly off-axis jet scenarios until the light curve peak is observed or VLBI imaging is obtained
- 2026ApJ...998..111C: Lateral spreading of the jet is not included in the structured jet forward model
- 2026ApJ...998..111C: The structured jet forward model requires an ad-hoc temporal evolution of epsilon_e proportional to t^4 at early times
- 2021ApJ...915...46C: The CO-to-H2 conversion factor is difficult to estimate and not well established in the low-metallicity regime.
- 2021ApJ...915...46C: A comparable galaxy sample in the same stellar mass range did not exist for comparing M_gas.
- 2021ApJ...915...46C: The upper limit on the molecular gas mass fraction (mu_gas) could not constrain the redshift trend effectively.
- 2017ApJ...848L..21A: Bad weather may cause flux decorrelation at high frequency in the Sep 5 epoch
- 2024ApJ...974...18C: Chandra spectra have too few counts to constrain the spectral shape
- 2024ApJ...974...18C: Inferred Gamma depends on the assumed jet launch date
- 2023NatAs...7...80U: PA difference between radio and optical only ~90% significant
- 2025ApJ...993L...6N: Equipartition-based energy is a lower limit
- 2025ApJ...993L...6N: Parameters at dt_rest ~ 17.5 d are not physical because the SED is free-free absorbed
- 2025ApJ...993L...6N: Cooling estimates depend strongly on assumed CSM density profile and shock velocity
- 2025ApJ...993L...6N: Small LFBOT sample
- 2019ApJ...884L..58U: Non-simultaneous multi-wavelength polarimetry limits conclusions
- 2025ApJ...992L..18S: Second flare is not modelled beyond equipartition
- 2025ApJ...992L..18S: ALMA flux at Delta t = 227 days is too high relative to low-GHz data and cannot be accounted for
- 2025ApJ...992L..18S: ATA fluxes are contaminated by background due to the large beam
- 2025ApJ...992L..18S: Model degeneracies between relativistic and non-relativistic outflows remain
- 2019ApJ...878L..26L: Systematic uncertainties from RS dynamics approximations and stochastic random walk; forward-shock parameters degenerate since nu_a not located
- 2024NatAs...8..774B: The afterglow/SN decomposition is uncertain and affects the Ni mass

### Settings cards flag as needed but not stated
- casa version: 2
- flux scale uncertainty: 2
- flux calibrator and flux scale uncertainty: 2
- casa version and pipeline version: 2
- image size, cell size, masking and clean threshold: 1
- flux calibrator flux scale and its uncertainty: 1
- which frequency/spectral windows were used for continuum imaging: 1
- how the template sed was selected and normalized to 345 ghz: 1
- boxfit fitting settings (priors, optimization, fixed parameters): 1
- light-curve fitting method and extinction treatment details: 1
- whether primary beam correction was applied: 1
- alma flux calibrator, calibration pipeline/casa version and imaging parameters (the images are arch…: 1
- region or fit settings used with casa imfit for the alma point-source flux (box, initial guess, fix…: 1
- per-epoch alma flux values: the main flux table is only partly printed, the full table is machine-r…: 1
- priors, likelihood, walker number and burn-in for the emcee/scalefit mcmc: 1
- initial guesses and fitting method for the pl+bpl light curve fit (software, fit range): 1
- which data points entered the scalefit fit besides those listed as excluded, and how upper limits w…: 1
- alma flux scale uncertainty adopted: 1
- exact times (days post-trigger) and durations of each alma epoch: 1
- exact region coordinates and sizes used in the casa viewer for alma gaussian fitting and rms noise …: 1
- whether peak or integrated flux density from the gaussian fits in casa viewer was reported as the a…: 1
- exact cosmological parameters (h0, omega_m, omega_lambda) from planck 2018 used for luminosity calc…: 1
- fitting algorithm/software and uncertainty estimation method used for the smoothly broken power-law…: 1
- imaging parameters for aca tclean (cell size, image size, deconvolver, threshold, niter) and the cl…: 1
- line-free channel ranges used for continuum estimation in the aca cubes: 1
- exact velocity range used to integrate each aca line and how line fluxes and uncertainties were com…: 1
- flux calibrator and flux-scale uncertainty for the aca and archival data: 1
- primary-beam correction details for the off-axis archival b6/b7 data and how photometry (table of p…: 1
- pyautolens configuration: priors on sersic and mass parameters (except lens centre), number of live…: 1
- mercurius priors on the dust opacity transition wavelength and on mass, and the l_ir/sfr conversion…: 1
- tuner code and set-up (not released in the paper): number of steps, convergence criteria, density p…: 1
- gain factor, flagging choices and spectral baseline handling for lmt/rsr and apex data beyond those…: 1
- rest frequencies and line-width/integration windows adopted for the weak lines ([ci], hcn, h2o+): 1
- clean threshold, mask, cell and image size, niter: 1
- magphys priors/library details and exact photometry treatment for 070521 (flux ladder, redshift fix…: 1
- continuum subtraction method for the line cube: 1
- flux calibration uncertainty and any alma flux scale error added: 1
- observed 080207 band 9 on-source time inconsistent (8 vs 5 min): 1
- how l[cii] was derived from flux and how sigma_fir comparison samples were homogenised: 1
- target coordinates: 1

## Paper excerpts (35 of 35, chosen for detail and spread over fields/years)

### 2017PASJ...69...20H: ALMA and RATIR observations of GRB 131030A (2017; transients, high_z_galaxies; multi_facility_alma_minor)
- question: Constrain the late-time 345 GHz afterglow/host emission of GRB131030A, model the forward shock with RATIR and Swift data, and assess the host galaxy and the nearby submm source
- step 2: Fit afterglow light curves and SEDs
  - method: Single and broken power-law fits to light curves; power-law fits to SEDs [2.3 Afterglow Lightcurve: "To describe the light curves, we employed a single power-law function by dividing light curve data into earlier"]
  - fitting: chi-square fits, no sampler stated [Afterglow Lightcurve: "We successfully fitted the single power-law function to the earlier light curves."]
  - validation: chi2/nu reported [2.4 Afterglow Spectrum: "$\beta=-0.57\pm0.09$ ($\chi^{2}/\nu=1.9$ with $\nu=8$)"]
- step 3: Forward shock modeling
  - method: boxfit 2D relativistic hydrodynamic jet model fit to six OIR bands and ALMA limit, ISM only [3.1 Forward Shock Radiation and X-Ray E…: "we performed forward shock synchrotron radiation modeling with the optical light curves and ALMA upper limit by using the boxfit code (cite: boxfit)."]
  - software: boxfit
  - parameter: on-axis case, theta_obs=0 [3.1 Forward Shock Radiation and X-Ray E…: "We determined the optimal modeling parameters with the on-axis case (observing angle, $\theta_{obs}=0$)"]
  - assumption: homogeneous circumburst medium (ISM) [3.1 Forward Shock Radiation and X-Ray E…: "Because the code involved a two-dimensional relativistic hydrodynamical jet simulation with a homogeneous circumburst medium"]
  - validation: Compared SSC analytic prediction with X-ray data [3.1 Forward Shock Radiation and X-Ray E…: "On the basis of the analytic solution described by (cite: fan08), we calculated the expected flux density of synchrotron self-inverse-Compton radiation"]
- step 4: Host IR luminosity and SFR limits
  - method: Redshift Chary & Elbaz template SED to z=1.293 and scale to ALMA 3-sigma limit; convert L_IR to SFR [4.2 Host Galaxy and ALMAJ2300-0522: "We constrained the 3-$\sigma$ upper limits of IR luminosity as $L_{IR} <1.11\times10^{11} L\solar$."]
  - assumption: ALMAJ2300-0522 at same redshift as GRB [4.2 Host Galaxy and ALMAJ2300-0522: "By assuming the same redshift with GRB131030A, we also obtained $L_{IR}=8.65\times10^{11} L\solar$"]
  - validation: Compared with TOUGH sample SFR [4.2 Host Galaxy and ALMAJ2300-0522: "The upper limit of SFR was consistent with those of the TOUGH samples"]
- result: Host L_IR 3-sigma upper limit = <1.11e11 ± not stated Lsun [abstract: "$L_{IR}<1.11\times10^{11} L\solar$"]
- result: Host SFR 3-sigma upper limit = <18.7 ± not stated Msun/yr [abstract: "SFR$<18.7$ ($M\solar$ yr$^{-1}$)"]
- result: ALMAJ2300-0522 L_IR if at z=1.293 = 8.65e11 ± not stated Lsun [4.2 Host Galaxy and ALMAJ2300-0522: "we also obtained $L_{IR}=8.65\times10^{11} L\solar$ and the corresponding SFR of 147 $M\solar$ yr$^{-1}$"]
- result: Jet break time (r-band) = 2.51e5 ± 0.48e5 s [Table 1: "$(2.51\pm0.48)\times10^{5}$"]
- result: Boxfit jet opening angle = 8.8 ± not stated deg [3.1 Forward Shock Radiation and X-Ray E…: "$\theta_{jet}=8^{\circ}.8$, $E=1.05\times10^{52}$ erg"]
- limitation (authors): ALMA astrometry bugs reported; large offset not explained [2.1 ALMA Submillimeter Follow-up Observ…: "Although several astrometry-related bugs (e.g. phase calibrator coordinate inconsistency) were reported from the ALMA ARC after data delivery"]
- not stated (card): Image size, cell size, masking and clean threshold; Flux calibrator flux scale and its uncertainty; Which frequency/spectral windows were used for continuum imaging; How the template SED was selected and normalized to 345 GHz; Boxfit fitting settings (priors, optimization, fixed parameters); Light-curve fitting method and extinction treatment details; Whether primary beam correction was applied

### 2024ApJ...974..279D: A Millimeter Rebrightening in GRB 210702A (2024; transients; observational_alma_primary)
- question: Why does the ALMA 97.5 GHz afterglow light curve of GRB 210702A rebrighten, and can a standard forward shock model explain the multi-wavelength data?
- step 4: test forward shock regimes with closure relations
  - method: Compare observed temporal and spectral indices with predicted closure relations for ISM and wind media to derive p and select the medium [3.3 Stellar wind medium: "For the stellar wind case we derive $p=2.24\pm0.01$ from our observed light curve evolution"]
  - assumption: Slow cooling regime with nu_m < nu_c [3.3 Stellar wind medium: "During slow-cooling ($\nu_m<\nu_c$) there are two spectral regimes to consider"]
  - validation: Predicted optical spectral index compared with measured beta_O = -0.63+-0.08; ISM ruled out via peak flux argument [3.3 Stellar wind medium: "which is more than an order of magnitude larger than our constraint on the peak flux from our millimeter data at 1.17 days and therefore clearly rules out an ISM medium"]
- step 6: fit forward shock model to multi-wavelength data
  - method: MCMC exploration of ScaleFit parameter space with data excluded where the model is not expected to apply [4 Afterglow modelling with ScaleFit: "We conduct a Markov Chain Monte Carlo (MCMC) exploration of our `ScaleFit` parameter space using the `emcee` Python package"]
  - software: ScaleFit, emcee
  - parameter: z fixed to 1.160 and d_L = 2.52e28 cm [4 Afterglow modelling with ScaleFit: "We fix the burst redshift to $z=1.160$ and the luminosity distance to the value computed using our adopted cosmology, $d_L=2.52\times10^{28}$ cm."]
  - parameter: Excluded: uvw2 data, radio data after 8.2 days, X-ray t<0.01 d, first ATCA epoch, radio <16.7 GHz at 6.6 d [4 Afterglow modelling with ScaleFit: "We therefore exclude these data from our modelling, along with the radio observations following the start of the 97.5 GHz rebrightening at 8.2 days."]
  - assumption: theta_obs = 0 and xi_N = 1 [4 Afterglow modelling with ScaleFit: "We assume that the observer is looking directly down the axis of the jet ($\theta_\mathrm{obs}=0$) and that the fraction of shock-accelerated electrons is unity"]
  - assumption: Spherical jet (theta = pi/2) [4 Afterglow modelling with ScaleFit: "We assume a spherical jet ($\theta=\pi/2$) since our observations show no clear evidence for a jet break."]
  - assumption: Milky Way extinction (Fitzpatrick 1999, R_V=3.1, A_V=0.3271) and SMC host extinction curve (Pei 1992) with free A_V,host [4 Afterglow modelling with ScaleFit: "we adopt the Small Magellanic Cloud (SMC) extinction curve from (cite: Pei1992) to account for possible host galaxy extinction, which is a free parameter in our modelling"]
  - assumption: LCDM cosmology Omega_m=0.315, H0=67.4 [1 Introduction: "We adopt a $\Lambda$CDM cosmology with $\Omega_m=0.315$ and $H_0=67.4$ km s$^{-1}$ Mpc$^{-1}$ (cite: Planck2020)."]
  - fitting: emcee MCMC; priors and likelihood not stated [4 Afterglow modelling with ScaleFit: "following the implementation described in detail in (cite: deWet2023b)"]
  - validation: Highest-likelihood model compared with optical, X-ray and radio SEDs; radio SEDs found incompatible with the model [4 Afterglow modelling with ScaleFit: "As we expected, the optically thick spectra observed in the Epoch 1 and 3 radio SEDs are incompatible with our highest-likelihood model"]
- step 8: test explanations for the rebrightening
  - method: Test energy injection (closure relation for q, kinetic energy rising as t^(1-q) between 8.2 and 18.1 days) and a reverse shock from a shell collision against higher frequency radio data; rule out other scenarios by argument [5.5 Energy injection: "we introduce a period of energy injection in which the kinetic energy of the blast wave increases as $t^{1-q}$ between 8.2 and 18.1 days"]
  - parameter: Other forward shock parameters kept fixed; lower frequency radio bands excluded [5.5 Energy injection: "We keep all other forward shock parameters the same."]
  - assumption: For the shell collision, collision time = start of rise (8.2 d), deceleration time = peak (18.1 d) [5.6 Reverse shock: "We choose to associate the collision time with the beginning of the rise in the 97.5 GHz light curve at 8.2 days, and the deceleration time with the peak in the light curve at 18.1 days."]
  - validation: Models compared by eye with higher frequency radio bands; neither captures the other radio bands [5.5 Energy injection: "The model can adequately capture the 97.5 GHz rebrightening, but does not fully capture the behaviour in the higher frequency bands"]
- result: Electron index p from wind-medium closure relations = 2.24 ± 0.01 dimensionless [3.3 Stellar wind medium: "For the stellar wind case we derive $p=2.24\pm0.01$ from our observed light curve evolution"]
- result: ScaleFit MCMC electron index p = 2.28 ± +0.01/-0.01 dimensionless [Table 2: "$2.28^{+0.01}_{-0.01}$"]
- result: Isotropic kinetic energy E_K,iso = 30.7 ± +4.5/-3.1 1e53 erg [Table 2: "$30.7^{+4.5}_{-3.1}$"]
- result: Wind density parameter A_star = 4.7e-3 ± +1.6/-2.1 (e-3) dimensionless [Table 2: "$4.7^{+1.6}_{-2.1}\times10^{-3}$"]
- result: epsilon_e = 8.7e-3 ± +1.3/-2.1 (e-3) dimensionless [Table 2: "$8.7^{+1.3}_{-2.1}\times10^{-3}$"]
- result: epsilon_B = 2.4e-1 ± +3.7/-1.0 (e-1) dimensionless [Table 2: "$2.4^{+3.7}_{-1.0}\times10^{-1}$"]
- result: Host extinction A_V,host = 0.011 ± +0.010/-0.007 mag [Table 2: "$0.011^{+0.010}_{-0.007}$"]
- result: Energy injection index q = -1.88 ± not stated dimensionless [5.5 Energy injection: "we calculate a value of $q=-1.88$"]
- result: Blast wave energy increase during the rebrightening = about 10 ± not stated dimensionless [5.5 Energy injection: "We find that the blast wave energy increases by a factor of $\approx10$ over the course of the rebrightening."]
- limitation (authors): Higher-frequency ATCA data at epoch three were dropped, losing temporal information [3.4 Radio evolution: "leads to a loss of possibly valuable temporal information"]
- limitation (authors): Possible unaccounted systematic uncertainties in ATCA calibration prevent excluding energy injection [5.5 Energy injection: "possible unaccounted-for systematic uncertainties from the calibration of our ATCA data prevents us from completely excluding this scenario"]
- limitation (authors): Reverse shock model is not unique; two break frequencies unconstrained [5.6 Reverse shock: "this is not a unique model since two of the break frequencies"]
- not stated (card): ALMA flux calibrator, calibration pipeline/CASA version and imaging parameters (the images are archive products, but their CASA pipeline version and weighting are not given); Region or fit settings used with CASA imfit for the ALMA point-source flux (box, initial guess, fixed beam); Per-epoch ALMA flux values: the main flux table is only partly printed, the full table is machine-readable only; Pr…

### 2022MNRAS.512.2337D: The early afterglow of GRB 190829A (2022; transients; archival_reuse)
- question: Characterize the early stages of the multi-wavelength afterglow evolution of GRB 190829A and determine its emission mechanism, physics of the ejecta, and properties of the external medium.
- step 3: Reduce Swift BAT, XRT, and UVOT data and MASTER optical polarimetry
  - method: Process BAT light curves and spectra with HEASOFT and XSPEC, retrieve and convert XRT light curves, perform host-subtracted aperture photometry on UVOT images with HEADAS/UVOTSOURCE, and perform aperture photometry and Stokes Q calculation… [Swift/BAT: "BAT data were processed using HEASOFT package (v6.25)."] [Swift/UVOT: "The analysis pipeline used software HEADAS 6.24 and UVOT calibration 20170922."]
  - software: HEASOFT, BATECONVERT, BATMASKWTEVT, BATTBLOCKS, XSPEC, HEADAS, UVOTSOURCE
  - parameter: UVOT extraction radius = 3'' aperture corrected to 5''; MASTER aperture size = 3.9'' [Swift/UVOT: "The source counts were extracted using a region of 3$''$ radius. In order to be consistent with the UVOT calibration, these count rates were then corrected to 5$''$ using the curve of growth contained in the calibration files."] [MASTER polarization measurements: "After astrometric binding of each image, we performed standard aperture photometry using an aperture size of 3.9$\ensuremath{''}$."]
  - assumption: Galactic N_H = 5.6 x 10^20 cm^-2; afterglow and supernova negligible after 58 days in UVOT [Swift/XRT: "in addition to the Galactic value $N_H=5.6\times 10^{20}$ cm$^{-2}$ (cite: Willingale2013)."] [Swift/UVOT: "At these late times we can assume that the emission from the afterglow and supernova is negligible compared to the host after this time (both components have AB magnitude $>$23 at this stage)."]
  - fitting: Power-law and Band function fits in XSPEC for BAT/XRT spectra; Bayesian blocks for BAT duration [Swift/BAT: "We used BATTBLOCKS to run the Bayesian Block algorithm over the 64 ms, background-subtracted, 15–350 keV light curve"] [Swift/BAT: "Spectral analysis was carried out using XSPECV12.10.1 (cite: Arnaud1996)"]
  - validation: Chi-squared per degree of freedom reported for spectral fits [Swift/BAT: "Its spectrum, integrated from $T_0$-52 s to $T_0$-47 s, is well fit by a simple power law with a photon index of $1.89 \pm 0.22$ ($\chi^{2}/\mathrm{d.o.f.} = 1.04$)"]
- step 4: Model multi-wavelength light curves and broadband SEDs with Forward Shock and Reverse Shock components
  - method: Fit X-ray, UVOIR, and radio light curves with power laws and smoothly broken power laws; model broadband SEDs at 4 epochs (1200 s, 6800 s, 21600 s, 1 d) using two smoothly broken power-law components (FS and RS); test standard FS model usi… [A forward shock plus reverse shock scen…: "we derive that the emission rises with a slope of $-3.2 \pm 0.5$, reaches its peak at around 1400 s and then decays with index $1.65 \pm 0.18$."] [Spectral Energy Distribution (SED): "To better disentangle the different emission components we studied the afterglow SED at four different epochs: 1200 s (slightly before the peak), 6800 s (during the steep decay), 21600 s (around the time of the H.E.S.S. detection), and 1 d after the BAT trigger. Each component was described with a smoothly broken powe…"]
  - software: afterglowpy
  - parameter: SED epochs: 1200 s, 6800 s, 21600 s, 1 d; FS spectral indices fixed to beta_low = -1/3 and beta_up = 0.75 (p ~ 2.50) [Spectral Energy Distribution (SED): "To better disentangle the different emission components we studied the afterglow SED at four different epochs: 1200 s (slightly before the peak), 6800 s (during the steep decay), 21600 s (around the time of the H.E.S.S. detection), and 1 d after the BAT trigger."] [Spectral Energy Distribution (SED): "Assuming an electron spectral energy index $p$ $\sim$ 2.50, as derived from the radio light curves, we set $\beta^{FS}_{low}$=-1/3 and $\beta^{FS}_{up}$=0.75 for the FS spectral index below and above the peak energy, respectively."]
  - assumption: Constant density external medium; standard fireball closure relations for FS [Spectral Energy Distribution (SED): "The first spectral component tracks the evolution of a forward shock (FS) expanding in a constant density medium, as observed at the low frequency radio data."]
  - fitting: Smoothly broken power-law fits to light curves and SEDs [Spectral Energy Distribution (SED): "Each component was described with a smoothly broken power-law (SBPL), and its evolution was determined according to the standard fireball model."]
  - validation: Comparison with standard FS predictions in afterglowpy showing underestimation of early X-ray/optical and high-frequency radio emission [Standard Forward Shock model: "While the late X-rays and low-frequency radio data can be reasonably well described by this FS model, the early time X-rays/optical data and the high-frequency radio emission are significantly underestimated by the model."]
- result: 343 GHz temporal decay index = 1.65 ± not stated dimensionless [A forward shock plus reverse shock scen…: "At the highest frequency probed by ALMA (343 GHz), the afterglow rapidly decays as $t^{-1.65}$."]
- result: 100 GHz light curve break time = 3.6 ± 0.1 days [A forward shock plus reverse shock scen…: "The break times are 3.6$\pm$0.1 days and 10.1$\pm$2.9 days for 100 GHz and 17 GHz, respectively."]
- result: 17 GHz light curve break time = 10.1 ± 2.9 days [A forward shock plus reverse shock scen…: "The break times are 3.6$\pm$0.1 days and 10.1$\pm$2.9 days for 100 GHz and 17 GHz, respectively."]
- result: 5.5 GHz light curve peak time = 4.1 ± 0.4 days [A forward shock plus reverse shock scen…: "The radio flux at 5.5 GHz increases with a slope of -0.46 $\pm$ 0.09 reaching its peak at 4.1 $\pm$ 0.4 days, and then decays with slope of 1.13 $\pm$ 0.12 (Figure 1)."]
- result: 5.5 GHz post-peak decay slope = 1.13 ± 0.12 dimensionless [A forward shock plus reverse shock scen…: "The radio flux at 5.5 GHz increases with a slope of -0.46 $\pm$ 0.09 reaching its peak at 4.1 $\pm$ 0.4 days, and then decays with slope of 1.13 $\pm$ 0.12 (Figure 1)."]
- result: Forward shock electron spectral index p = 2.50 ± 0.16 dimensionless [A forward shock plus reverse shock scen…: "Using the standard closure relations for GRB afterglows, the post peak temporal slope, $\alpha \approx$1.1, is related to the spectral index of the accelerated electrons as $p$ = 4$\alpha$/3 +1 = 2.50 $\pm$0.16."]
- result: Reverse shock electron spectral index p = 2.80 ± 0.04 dimensionless [Spectral Energy Distribution (SED): "The second spectral component tracks the reverse shock (RS) modeled with spectral slopes of $\beta^{RS}_{low}$ $\approx$ -1.0 $\pm$0.2 and $\beta^{RS}_{up}$ $\approx$ 0.90$\pm$0.02, leading to $p$=2.80$\pm$0.04."]
- result: Optical polarization Stokes parameter Q upper limit (3 sigma) = <= 6 ± not stated % [Polarization: "In this interval, the time-averaged 3 $\sigma$ upper limit is $Q$ $\lesssim$6%, where $Q=\left(F_{0}-F_{90}\right)/\left(F_0 + F_{90}\right)$ is the Stokes parameter"]
- result: Intrinsic reddening E(B-V) = 0.90 ± 0.05 mag [Spectral Energy Distribution (SED): "They are obtained for an intrinsic reddening of $E(B-V)$=$0.90 \pm 0.05$ and an intrinsic hydrogen column desnity of $N_H=1.13 \pm 0.06 \times 10^{22}$ cm$^{-2}$"]
- result: Intrinsic hydrogen column density N_H (from SED fit) = 1.13e22 ± 0.06e22 cm^-2 [Spectral Energy Distribution (SED): "They are obtained for an intrinsic reddening of $E(B-V)$=$0.90 \pm 0.05$ and an intrinsic hydrogen column desnity of $N_H=1.13 \pm 0.06 \times 10^{22}$ cm$^{-2}$"]
- result: Prompt duration T90 = 57 ± 3 s [Swift/BAT: "We used BATTBLOCKS to run the Bayesian Block algorithm over the 64 ms, background-subtracted, 15–350 keV light curve finding a $T_{90} = 57 \pm 3$ s and $T_{50} = 5 \pm 1$ s ."]
- result: Rest-frame minimum variability timescale Delta t_min / (1+z) = 1.5 ± 0.5 s [Prompt emission: "From this analysis, we found $\Delta~t_{min}/(1+z)=1.5 \pm 0.5$"]
- limitation (authors): MASTER has only two orthogonal polarizing filters at a single site and measures only Stokes Q, so an unfavorable polarization angle orientation could still hide a polarized afterglow. [Polarization: "However, each telescope of the MASTER network has two filter with orthogonal polarization angles and can only constrain the component of the polarization vector along the line of sight."]
- limitation (authors): Standard closure relations for a reverse shock in a constant density medium do not provide an acceptable fit to the SED evolution. [Spectral Energy Distribution (SED): "By imposing the standard closure relations for a RS expanding in a constant density medium, no acceptable fit could be found."]
- limitation (authors): The estimated isotropic kinetic energy is only a lower limit because the fraction of accelerated electrons xi may be < 1 and Compton losses from the VHE component may suppress X-ray flux. [Burst Energetics and Environment: "Our estimated total energy is an order of magnitude lower than the value derived by (cite: Salafia2021), however we caution that our value can only place a lower limit to the burst energetics."]
- not stated (card): Exact region coordinates and sizes used in the CASA viewer for ALMA Gaussian fitting and RMS noise extraction; Whether peak or integrated flux density from the Gaussian fits in CASA viewer was reported as the ALMA flux density; Exact cosmological parameters (H0, Omega_m, Omega_Lambda) from Planck 2018 used for luminosity calculations; Fitting algorithm/software and uncertainty estimation method u…

### 2026A&A...706A.174A: Hiding behind a curtain of dust: Gas and dust properties of an ultra-luminous strongly-lensed z = 3.75 galaxy behind the Milky Way disc (2026; high_z_galaxies; observational_alma_primary)
- question: Confirm the spectroscopic redshift of the strongly lensed submm galaxy J154506 behind the Milky Way (Lupus-I cloud) and make an initial characterisation of its dust and molecular gas properties
- step 4: Fit the FIR dust SED with a modified blackbody
  - method: Bayesian greybody fit with MERCURIUS (PyMultiNest nested sampling), optically thin and self-consistent opacity scenarios, magnification-corrected [6.1 Dust emission and FIR-derived prope…: "We first fitted J154506 using the Bayesian FIR SED PYMULTINEST fitting code MERCURIUS (cite: Witstok2022), which employs a nested sampling algorithm (cite: Buchner2014) to fit a greybody spectrum to FIR photometry."]
  - software: MERCURIUS, PyMultiNest
  - parameter: Rest-frame wavelengths 10 to 10^3 micron fitted [6.1 Dust emission and FIR-derived prope…: "For fitting, we considered rest-frame FIR wavelengths from 10 to"]
  - parameter: T_dust gamma prior (shape a=1.5); beta_dust Gaussian prior centred 1.8, sigma 0.25 [6.1 Dust emission and FIR-derived prope…: "Specifically, we used a default gamma distribution with a shape parameter (a=1.5)"] [6.1 Dust emission and FIR-derived prope…: "we imposed a Gaussian prior centred at 1.8 with a standard deviation of 0.25."]
  - assumption: kappa = 8.94 cm2/g at 158 micron, appropriate for SN-ejected dust after reverse shock destruction [6.1 Dust emission and FIR-derived prope…: "This value of $\kappa$ is appropriate for dust grains ejected by supernovae (SNe) after reverse shock destruction (cite: Hirashita2014)."]
  - fitting: Nested sampling (MERCURIUS/PyMultiNest) with gamma prior on T_dust and Gaussian prior on beta [6.1 Dust emission and FIR-derived prope…: "we imposed a Gaussian prior centred at 1.8 with a standard deviation of 0.25."]
  - validation: Posteriors shown; TUNER fit compared with MERCURIUS [6.2 Radiative transfer model results: "The well-constrained TUNER model fits the observed data comparably to the best-fit MERCURIUS model"]
- result: Dust temperature, optically thin and self-consistent MERCURIUS fits = 30 and 48 ± 2 and 1 K [6.1 Dust emission and FIR-derived prope…: "we obtain an emissivity indices of $\beta_{\rm dust}$ $=2.0 \pm0.1$ and $2.1 \pm0.1$, and dust temperatures of $30\pm2$ and $48\pm1$ K"]
- result: Dust emissivity index beta, optically thin and self-consistent MERCURIUS fits = 2.0 and 2.1 ± 0.1 and 0.1 dimensionless [6.1 Dust emission and FIR-derived prope…: "we obtain an emissivity indices of $\beta_{\rm dust}$ $=2.0 \pm0.1$ and $2.1 \pm0.1$"]
- result: Intrinsic IR luminosity (MERCURIUS) = 6-7e12 ± not stated Lsun [6.1 Dust emission and FIR-derived prope…: "The derived intrinsic IR luminosity is L$_{\rm{IR}}=6-7\times 10^{12}~\rm{L}_{\odot}$"]
- result: IR-based SFR (MERCURIUS) = 860 to 910 ± 80 and 90 Msun/yr [6.1 Dust emission and FIR-derived prope…: "the IR-based SFR ranges from $860\pm80$ to $910\pm90~\rm{M}_{\odot}yr^{-1}$"]
- result: Dust mass, optically thin and variable optical depth models (magnification corrected) = 3.4e9 and 1.7e9 ± 1.6e9 and 0.3e9 Msun [6.1 Dust emission and FIR-derived prope…: "we derive dust masses of $3.4\pm1.6\times10^{9}~\rm{M}_{\odot}$ and $1.7\pm0.3\times10^{9}~\rm{M}_{\odot}$ for the optically-thin and variable dust optical depth models, respectively"]
- limitation (authors): Stellar mass and other SED-derived properties highly uncertain because of Lupus-I extinction [4 Spectroscopic redshift confirmation: "makes SED-derived properties, such as the stellar mass, highly uncertain."]
- limitation (authors): Lens redshift not confirmed; MUSE and FORS2 data too poor [3.5 MUSE and FORS2 observations: "The low quality of this dataset precluded spectroscopic confirmation of the lens and prevented further detailed analysis."]
- limitation (authors): Dust mass strongly depends on the assumed kappa and optical depth [6.1 Dust emission and FIR-derived prope…: "Dust mass estimates are highly dependent on the assumed"]
- not stated (card): Imaging parameters for ACA tclean (cell size, image size, deconvolver, threshold, niter) and the clean mask for continuum; Line-free channel ranges used for continuum estimation in the ACA cubes; Exact velocity range used to integrate each ACA line and how line fluxes and uncertainties were computed; Flux calibrator and flux-scale uncertainty for the ACA and archival data; Primary-beam correction…

### 2019MNRAS.488.5029H: Star-formation rates of two GRB host galaxies at z ∼ 2 and a [C II] deficit observed with ALMA (2019; high_z_galaxies; observational_alma_primary)
- question: What are the dust-obscured SFRs of two GRB host galaxies at z~2 once rest-frame FIR is measured, and is their [C II]/FIR ratio unusual?
- step 5: Compare with main sequence and [CII] deficit samples
  - method: Place hosts on SFR-M* main sequence (Whitaker2014) and in L[CII]/LFIR vs LFIR, Sigma_FIR, LCO/LFIR planes; check afterglow contamination by extrapolating radio flux [5.2 Main sequence: "the SFRs of the GRB 070521 and 080207 host galaxies derived from our analysis place them on the main sequence within observational uncertainties."]
  - assumption: Afterglow spectral slopes alpha=-1/2 to 1/3 (Sari1998) [5.1.1 GRB 070521 host: "assuming that the radio flux originates from the afterglow with typical spectral slopes, $\alpha$=$-$1/2 to 1/3, (cite: Sari1998)"]
- result: L[CII]/LFIR 080207 = 7.5e-4 ± not stated dimensionless [abstract: "The luminosity ratio of \[C ii\] 158$\mu$m to FIR is 7.5$\times 10^{-4}$"]
- limitation (authors): Dust property uncertainties for 070521 host underestimated because only one FIR photometric point [4 SED Modelling and results: "uncertainties of dust properties of the GRB 070521 host, i.e., dust mass and dust temperature errors, are probably underestimated by MAGPHYS."]
- limitation (authors): [CII] detection only S/N~4; possible ALMA observational bias [5.3.4 Observational bias: "the \[C ii\] deficit of the GRB 080207 host might be the observational bias toward the lower $L_{\rm [CII]}$/$L_{\rm FIR}$ ratio caused by the deep ALMA observation."]
- not stated (card): CLEAN threshold, mask, cell and image size, niter; MAGPHYS priors/library details and exact photometry treatment for 070521 (flux ladder, redshift fixing); Continuum subtraction method for the line cube; Flux calibration uncertainty and any ALMA flux scale error added; Observed 080207 band 9 on-source time inconsistent (8 vs 5 min); How L[CII] was derived from flux and how Sigma_FIR comparison sa…

### 2012ApJ...761L..32W: ALMA Submillimeter Continuum Imaging of the Host Galaxies of GRB 021004 and GRB 080607 (2012; high_z_galaxies, transients; observational_alma_primary)
- question: Do the GRB 021004 and GRB 080607 host galaxies at z>2 have significant dust-obscured star formation, and is the large afterglow extinction of the dark burst GRB 080607 representative of its host?
- step 1: Make continuum images
  - method: Inspect JAO calibration, Fourier transform visibilities with natural weighting; dirty image for GRB 021004, CLEAN for GRB 080607 [Observation and Data Reduction: "We further inspected the JAO calibration in CASA, and Fourier-transformed the complex visibility to make our own images."]
  - software: CASA
  - parameter: natural weighting [Observation and Data Reduction: "(i.e., “natural weighting”)"]
- step 2: Measure 345 GHz flux
  - method: Point-source flux at host location; for GRB 080607 point-source and 2-D Gaussian fits [GRB 080607: "We measure a flux of 0.31 mJy by fitting the emission with a point-source model."]
  - software: CASA
  - fitting: Point-source model and extended 2-D Gaussian [GRB 080607: "We therefore also fit the emission with an extended 2-D Gaussian, and obtain a slightly higher integrated flux of 0.32 mJy."]
  - validation: Pixel brightness histogram fitted with Gaussian (sigma=0.096 mJy/beam); spurious-peak probability between 5e-4 and 5e-3 [GRB 080607: "Thus the probability of finding a $>3.3\sigma$ spike at the location of our target is between $5\times10^{-4}$ (assuming a Gaussian noise) and $5\times10^{-3}$"]
- step 3: Derive L_IR and SFR
  - method: Redshift CE01 templates and select those consistent with the observed 345 GHz flux or upper limit; convert L_IR to SFR [GRB 021004: "We thus redshift the CE01 SEDs to $z=2.330$ and look for those with observed 345 GHz fluxes below our upper limit."]
  - parameter: 3-sigma upper limit 0.33 mJy for GRB 021004 [GRB 021004: "adopting the 3-$\sigma$ upper limit of 0.33 mJy"]
  - assumption: Dust temperature from CE01 luminosity-dependent templates; cosmology H0=71, OmegaM=0.27, OmegaL=0.73 [Introduction: "We adopt cosmological parameters of $H_0=71$ km s$^{-1}$ Mpc$^{-1}$, $\Omega_M=0.27$, and $\Omega_\Lambda=0.73$"]
  - validation: Compared SEDs with optical/NIR photometry and with optical SFRs [GRB 080607: "the bottom panel of Figure [2](#fig2) further shows that the SED is well represented by known dusty templates of local galaxies across the full spectral range."]
- result: S345 GRB 080607 host = 0.31 ± 0.09 mJy [abstract: "$S_{345} = 0.31\pm 0.09$ mJy"]
- result: S345 GRB 021004 host = 0.17 ± 0.11 mJy [GRB 021004: "The 345 GHz point-source flux measured at the location of the host galaxy is $0.17\pm0.11$ mJy."]
- result: L_IR GRB 080607 host = 2.4e11 to 4.5e11 ± range Lsun [abstract: "$L_{\rm IR}=(2.4$–$4.5)\times10^{11}~L_\ensuremath{\odot}$"]
- result: L_IR upper limit GRB 021004 host (3 sigma) = <3.1e11 ± not stated Lsun [abstract: "3-$\sigma$ upper limit of $L_{\rm IR}<3.1\times10^{11}~L_\ensuremath{\odot}$"]
- result: SFR GRB 080607 host = 41–77 ± range Msun/yr [GRB 080607: "The inferred SFR is between 41 and 77 $M_\ensuremath{\odot}$ yr$^{-1}$."]
- result: SFR upper limit GRB 021004 host = <53 ± 3 sigma Msun/yr [GRB 021004: "the 3-$\sigma$ upper limit of the SFR of the host galaxy is 53 $M_\ensuremath{\odot}$ yr$^{-1}$"]
- result: Detection significance GRB 080607 = 3.3 ± not stated sigma [GRB 080607: "we adopt the more conservative measurement of 0.31 mJy with a statistical significance of 3.3 $\sigma$."]
- limitation (authors): GRB 080607 detection is marginal (3.3 sigma) with possible non-Gaussian noise; single-band photometry requires template dust temperature [GRB 080607: "However, there are hints of a non-Gaussian noise."]
- not stated (card): CASA version; Imaging parameters: cell size, image size, CLEAN threshold/mask, iterations; Method and region used for point-source and Gaussian fits; How L_IR was integrated from templates (8-1000 micron) and template matching tolerance; Flux scale uncertainty; Whether the four spectral windows were all combined

### 2024A&A...688A...8W: The accretion burst of the massive young stellar object G323.46‒0.08 (2024; star_formation; multi_facility_alma_minor)
- question: Verify the accretion-burst origin of the G323 maser flare and constrain the burst energy and accreted mass.
- step 4: Measure the FIR afterglow
  - method: Match PACS catalog fluxes with aperture growth curves; interpolate HAWC+ fluxes to PACS wavelengths and average growth-curve ratios. [FIR imaging: "Radii that reproduce HPPSC fluxes were derived by varying the aperture size on the PACS images."] [HAWC+ FIR photometry: "the HAWC+ 62 and 154 $\mu$m fluxes were interpolated to the PACS wavelengths using a polynomial approximation of the post-burst FIR SED established from all HAWC+ bands."]
  - software: DRP
  - parameter: HAWC+ calibration comparison source exceeds PACS by 15 ± 7%; taken into account in the analysis [HAWC+ FIR photometry: "PSF photometry of this object revealed that its HAWC+ flux exceeds the PACS flux by (15$\pm$7)%. Consequently, this was taken into account in the analysis."]
  - parameter: Relative HAWC+ flux-calibration error 10% [HAWC+ FIR photometry: "This yields a relative error of 10%."]
  - assumption: YSO FIR dust-continuum SED is continuous and featureless. [HAWC+ FIR photometry: "since the dust-continuum SED of the YSOs is continuous and featureless in the FIR (cf. (cite: Stecklum:2021))."]
  - fitting: Polynomial FIR SED approximation; low-order polynomial residuals assess calibration uncertainty. [HAWC+ FIR photometry: "The uncertainty of the flux calibration can be assessed from the residuals of a low-order polynomial fit to the observed fluxes"]
  - validation: 70 and 160 μm ratios agree within errors, supporting the 154 μm correction. [HAWC+ FIR photometry: "The ratio values agree within their errors, which a posteriori confirms the 154 $\mu$m flux correction."]
- result: 70 μm HAWC+/PACS flux ratio = 1.142 ± ±0.046 dimensionless [HAWC+ FIR photometry: "They amount to $1.142\pm0.046$ and $1.085\pm0.061$."]
- result: 160 μm HAWC+/PACS flux ratio = 1.085 ± ±0.061 dimensionless [HAWC+ FIR photometry: "They amount to $1.142\pm0.046$ and $1.085\pm0.061$."]
- result: 70 μm post-burst excess = 14.2 ± ±4.6 % [Burst energy estimate for the mean model: "They are elevated by $(14.2\pm4.6)\%$ at $70{\,} \rm \mu$m and $(8.5\pm6.1)\%$ at $160{\,}\rm\mu$m"]
- result: 160 μm post-burst excess = 8.5 ± ±6.1 % [Burst energy estimate for the mean model: "They are elevated by $(14.2\pm4.6)\%$ at $70{\,} \rm \mu$m and $(8.5\pm6.1)\%$ at $160{\,}\rm\mu$m"]
- limitation (authors): ALMA resolution cannot resolve a possible disk; continuum sensitivity cannot constrain larger-scale dust. [The ALMA view of G323: "The coarse resolution of the ALMA 12-m array is not sufficient to resolve a possible disk."]
- limitation (authors): Saturated (NEO)WISE burst photometry is unsuitable for quantitative conclusions. [IR light curves and color change: "Since the (NEO)WISE fluxes in both bands exceed the limit for which a meaningful bias correction can be applied, the burst light curves are not suitable for drawing quantitative conclusions."]
- limitation (authors): Only three dust configurations and one burst shape were explored. [Reliability of the derived burst energy: "We use only three settings, which are meant to provide limits."]
- not stated (card): Exact archive identifiers and project code for the reanalyzed 3 mm data set.; ALMA spectral-window frequencies, channel widths, channel selections and the SiO transition.; CASA and ALMA pipeline versions, calibration tables, calibrators and flux-scale uncertainty.; Whether ALMAGAL images were used unchanged or reimaged; imaging task, weighting, robust value, taper, masks, cell size and image size…

### 2025A&A...701A.191V: Observing radio transients with Phased ALMA: Pulses from the Galactic Centre magnetar (2025; stellar_physics, transients; archival_reuse)
- question: Can Phased ALMA at Band 3 detect and characterize single pulses and the cumulative energy distribution of the Galactic Centre magnetar PSR J1745-2900, and what are the prospects for observing radio transients (pulsars and FRBs) with Phased…
- step 5: Predict event rates and detectability for PSR J1745-2900, FRBs, and ATNF pulsars at Phased ALMA Band 1 and Band 3
  - method: Scaled observed Band 3 event rate and L-band FRB rates to Band 1 using fluence completeness thresholds and power-law index gamma; extrapolated 2301 ATNF pulsar fluxes (Dec < 47 deg) to 42 GHz using spectral indices and compared against rad… [PAM Band 1 predictions: "Based on our detections, we report a Poissonian rate of $\rm{R_{Band\hspace{1mm}3}}$ = 4 per hour (events/hr) for PSR J1745-2900 at ALMA Band 3."] [Pulsars: "To this end, we selected all the known pulsars from the ATNF catalogue (cite: catalogue) having flux density reported at 1.4 GHz or 2 GHz. We limited the sources detectable by ALMA based on a declination below 47° (cite: almahand)."]
  - parameter: Fluence limits: F_Band3 = 1330 mJy ms (37 antennas, 0.1 s width), F_Band1 = 1200 mJy ms (37 antennas, 0.1 s width), F_Band1 = 900 mJy ms (49 antennas, 0.1 s width), F_Band1 = 90 mJy ms (49 antennas, 1 ms FRB width) [PAM Band 1 predictions: "The fluence completeness limit using 37 antennas of 12m at Band 3 is $\rm{F_{Band\hspace{1mm}3}}$ = 1330 mJy ms and at Band 1 $\rm{F_{Band\hspace{1mm}1}}$ = 1200 mJy ms, considering a pulse width of 0.1 s."] [PAM Band 1 predictions: "However, if we instead consider a total of 49 antennas for the phasing, then the expected rate rises to $\rm{R_{Band\hspace{1mm}1}} = 10 \pm 3$ events/hr, as the fluence threshold drops to $\rm{F_{Band\hspace{1mm}1}}$ = 900 mJy ms."]
  - parameter: Integration times = 1, 1.5, and 2.5 hours; S/N = 6; pulsar period = 1 s; duty cycle = 10% [Pulsars: "We assumed a pulse width equal to 10$\%$ of the period and considered on-source integration times of 1, 1.5, and 2.5 hours."] [Pulsars: "For a pulsar spin period of 1 s with a duty cycle of 10%, we estimate that the Band 3 system is sensitive to 0.060 mJy."]
  - assumption: Phasing efficiency eta_p ~ 0.6; Band 3 T_sys = 74 K, G = 1.08 K/Jy; Band 1 T_sys = 45 K, G = 1.12 K/Jy [Pulsars: "We derived the minimum sensitivity for Band 3 using the radiometer equation for pulsars and considering telescope parameters such as $T_{sys}$ = 74 K, $G$ = 1.08 K/Jy (cite: almahand) for Band 3, a phasing efficiency of $\eta_{p} \sim 0.6$ (cite: matthews2017), a minimum detected S/N of 6 and 1 hour of on-source integ…"] [Pulsars: "Assuming that the Band 1 system behaves similarly ($T_{sys}$ = 45 K, $G$ = 1.12 K/Jy in (cite: almahand)), then we expect a minimum detectable flux of 0.035 mJy, using the same 37-antenna set-up."]
  - assumption: Missing pulsar spectral indices drawn from normal distribution with mean = -1.6 and std = 0.54 [Pulsars: "For the sources that do not have a reported spectral index, we draw a spectral index from a normal distribution, considering a mean of -1.6 and standard deviation equal to 0.54 (cite: index)."]
- result: Observed Band 3 Poissonian event rate for PSR J1745-2900 = 4 ± not stated events/hr [PAM Band 1 predictions: "Based on our detections, we report a Poissonian rate of $\rm{R_{Band\hspace{1mm}3}}$ = 4 per hour (events/hr) for PSR J1745-2900 at ALMA Band 3."]
- result: Predicted Band 1 event rate for PSR J1745-2900 (37 12m antennas) = 5 ± 2 events/hr [PAM Band 1 predictions: "We obtain a rate of $\rm{R_{Band\hspace{1mm}1}} = 5 \pm 2$ events/hr."]
- result: Predicted Band 1 event rate for PSR J1745-2900 (49 12m antennas) = 10 ± 3 events/hr [PAM Band 1 predictions: "However, if we instead consider a total of 49 antennas for the phasing, then the expected rate rises to $\rm{R_{Band\hspace{1mm}1}} = 10 \pm 3$ events/hr, as the fluence threshold drops to $\rm{F_{Band\hspace{1mm}1}}$ = 900 mJy ms."]
- result: Predicted Band 1 event rate for FRB 20121102A at peak activity (49 12m antennas) = 1 to 32 ± not stated events/hr [Conclusions: "For the periodic FRB 20121102A, at peak activity, we obtained a rate between 1 and 32 events/hr with PAM Band 1 using 49 12m antennas."]
- result: Number of known pulsars detectable with PAM Band 1 in 1 hr integration = 166 ± not stated dimensionless [Pulsars: "This would lead to the detection of 166 pulsars (7.2$\%$ of those visible to ALMA), 188 (8.2$\%$), and 209 (9.1$\%$), respectively."]
- result: Number of known pulsars detectable with PAM Band 1 in 1.5 hr integration = 188 ± not stated dimensionless [Pulsars: "This would lead to the detection of 166 pulsars (7.2$\%$ of those visible to ALMA), 188 (8.2$\%$), and 209 (9.1$\%$), respectively."]
- result: Number of known pulsars detectable with PAM Band 1 in 2.5 hr integration = 209 ± not stated dimensionless [Pulsars: "This would lead to the detection of 166 pulsars (7.2$\%$ of those visible to ALMA), 188 (8.2$\%$), and 209 (9.1$\%$), respectively."]
- result: Number of repeating FRBs currently visible to ALMA = 19 ± not stated dimensionless [FRBs: "As shown in Fig. 4, currently ALMA could potentially detect 19 repeating FRBs."]
- limitation (authors): Every 18.192 s there is a drop-off in the time series caused by the phasing cycle of the array, and 30 minutes of data were unusable. [Observations: "We used a total of $\sim$2 hr observing time, excluding 30 minutes of unusable data (see Table 2)."]
- limitation (authors): Pulses with small polarisation fractions or arriving outside the main integrated pulse profile phase window would not be detected by the selection criteria. [Methods and data processing: "It is worth noting that pulses with small polarisation fractions would have not been detected by our pipelines."]
- limitation (authors): The sample size is limited to eight pulses over a limited energy range. [Discussion: "Alternatively, a power-law relation for the cumulative energy distribution would be the result of the limited energy range of our pulses."]
- not stated (card): How the 18.192 s periodic drop-off artefact from the ALMA phasing cycle was masked, excised, or mitigated during the single-pulse search; Quantitative thresholds for linear and circular polarisation fractions used to accept or reject single-pulse candidates during visual inspection; Exact boxcar widths or matched-filtering parameters used in the PRESTO single-pulse search; Specific details of the…

### 2021ApJ...909...11J: 25 au Angular Resolution Observations of HH 211 with ALMA: Jet Properties and Shock Structures in SiO, CO, and SO (2021; star_formation; observational_alma_primary)
- question: Jet properties (proper motion, wiggle, knot and sub-knot structure) and shock structures of the HH 211 protostellar jet in CO, SiO and SO at ~25 AU resolution
- step 6: Model PV structure of backward/forward shocks and sideways ejection in knot BK3
  - method: Simple kinematic model of a jet beam (unshocked beam, backward shock, internal working surface, forward shock, sideways ejection) plus a jet-driven bow shock, producing model PV diagrams along and perpendicular to the jet axis [4.2.1 Illustrative Model For Shock Stru…: "this model has two components, a jet beam and a bow shock structure."]
  - parameter: R_j = 0.2 arcsec; z_bo = 0.5 arcsec; c_s = 8 km/s; beta = 4; v_s = 14 km/s; bow shock thickness 0.3 arcsec [Appendix I: Shock Model for knot BK3: "where z$_{bo}=$$0^{\prime\prime}_{^\textrm{.}}5$ is z position of the bow shock tip"] [Appendix I: Shock Model for knot BK3: "is the shock velocity to roughly match the observation."]
  - fitting: Parameters chosen by hand to roughly match the observation, no formal fit [Appendix I: Shock Model for knot BK3: "is the shock velocity to roughly match the observation."]
  - validation: Model PV diagrams roughly consistent with observed PV structures [4.2.1 Illustrative Model For Shock Stru…: "These features are also similar to those seen in the observation."]
- limitation (authors): Possible missing flux: MRS ~0.75 arcsec versus knot size ~1 arcsec; impact on the knot peak deviations unknown [4.1 Wiggle Structure and Protobinary?: "but we are not sure how and to what extent the missing flux impacts our results."]
- limitation (authors): Sub-knots are not spatially resolved, so shock structure analysis is limited to the knots [4.2 Backward and Forward Shocks and Sid…: "Since sub-knots are not spatially resolved, here we focus on the knots."]
- not stated (card): CASA version and whether the standard pipeline or manual scripts were used for calibration; Self-calibration solution interval, number of iterations and reference antenna; Primary-beam correction, CLEAN threshold, mask, niter, cell size and image size; Continuum subtraction method and line-free channels; How the 2015 and 2016 data were weighted and aligned when concatenated, and the flux scale co…

### 2019ApJ...870...59S: ALMA, ATCA, and Spitzer Observations of the Luminous Extragalactic Supernova SN 1978K (2019; star_formation, nearby_galaxies, other; observational_alma_primary)
- question: What is the radio-millimeter spectrum of SN 1978K, and what do ALMA, ATCA and Spitzer data imply for the synchrotron emission and for warm and cold dust?
- step 4: Model radio-millimeter spectrum
  - method: Compare modified Montes+1997 parameterized model with a broken power law GRB fireball cooling-break model with wind scaling [3: "Figure [5](#figure:atcaalma) combines the radio and millimeter observations of SN 1978K, and shows model fits from two possible interpretations for the radio-millimeter spectrum."]
  - parameter: Radio decay t^-1.53 gives p=2.373; indices -0.687 below and -1.187 above the break [3.2: "The fireball model then requires that the spectral indices be $\nu^{(1-p)/2} = \nu^{-0.687}$ below $\nu_{\rm c}$ and $\nu^{-p/2} = \nu^{-1.187}$ above it."]
  - assumption: Generic fireball formalism with wind scaling; ISM scaling rejected [3.2: "However, we can still adopt the generic fireball formalism here."]
  - validation: Temporal decay and spectral indices independently agree with the fireball expectations [3.2: "The fact that both the radio temporal decay and the spectral indices independently agree with the fireball expectations make this a promising interpretation."]
- result: Electron spectral index p (wind fireball) = 2.373 ± not stated dimensionless [3.2: "this implies $p=2.373$"]
- result: Change in spectral index at break = ~0.5 ± not stated dimensionless [3.2: "the change in the spectral index appears to be $\sim 0.5$"]
- limitation (authors): Combining whole-band data is less robust owing to beam changes and interpolation [2.1: "it might be considered a little less robust to combine all the data for the whole band"]
- not stated (card): Image size, cell size, masks, clean threshold for ALMA; Method of flux extraction (point-source fit vs peak) and flux uncertainty/absolute calibration error for ALMA; Which channels were flagged as bad; Fitting method, priors and uncertainties for the broken power law and Montes model; How power-law decay indices and their errors were fit; Exact Montes model parameter names (lost in table convers…

### 2020MNRAS.496.4405H: Far-infrared star formation rates of six GRB host galaxies with ALMA (2020; high_z_galaxies, star_formation, transients; observational_alma_primary)
- question: Do rest-frame FIR ALMA continuum data change the SED-derived SFRs, stellar masses and AGN/radio requirements of six IR-bright z~2 GRB host galaxies compared with earlier work without FIR data
- step 2: Assemble multi-wavelength SED photometry
  - method: Combine literature UV-to-radio photometry with the new Band 7 point; 3 sigma upper limits are not used in the fit; radio points are dropped in the no-radio configuration [3 Data: "We collected UV-to-radio photometric data of six GRB host galaxies reported in previous studies."] [Table 2: "upper limit, which is not taken into account in the SED fitting analysis."]
  - parameter: Filter effective wavelengths from the SVO Filter Profile Service [Table 2: "Effective wavelength retrieved from"]
  - assumption: Radio emission may be contaminated by a long-lived radio afterglow [6 Discussion: "The options to include and exclude radio data are due to a possible contamination from a long-lived radio afterglow in the radio flux of the host galaxy (cite: Perley2013b)."]
- limitation (authors): Best templates are not unique; other configurations have similar reduced chi2 [4 SED Modelling and results: "in some cases there exist other templates with similar reduced $\chi^2$ values."]
- limitation (authors): IMF test is simple and may mask IMF differences [6 Discussion: "We caution readers that our testing scheme is very simple, and therefore, the IMF differences could be masked by the simplifications of the model."]
- limitation (authors): Three hosts are only marginally detected (S/N ~5, ~4, ~3.5) [3 Data: "However, the host galaxies of GRB070306, GRB071021 and GRB050915A are marginally detected with S/Ns of $\sim5,\sim4$ and $\sim3.5$, respectively."]
- not stated (card): How the ASC reduction was done (pipeline vs manual, CASA version, flux calibrator) and which imaging parameters (weighting, robust, cell, size, CLEAN depth) produced the continuum images that imfit was run on; Which spectral windows/channels formed the continuum image and whether lines were excluded; the 0.04 and 0.02 uJy sensitivities look like typos and no image rms is given; imfit setup: fit r…

### 2024ApJ...969..122Y: ALMA Reveals Spatially Resolved Properties of Molecular Gas in the Host Galaxy of FRB 20191001A at z = 0.2340 (2024; nearby_galaxies, transients; observational_alma_primary)
- question: What are the spatially resolved molecular gas properties and kinematics of the FRB 20191001A host galaxy and its companion, and the gas and continuum limits at the FRB site?
- step 5: FRB-site limits
  - method: 3 sigma upper limit on N(H2) with Galactic conversion factor and 100 km/s linewidth; 3 sigma 1.3 mm continuum limit [3.3 FRB 20191001A site: "That is obtained by assuming the Galactic conversion factor, and the CO linewidth at the site, $\SI{100}{km.s^{-1}}$"]
- result: N(H2) at FRB site (3 sigma) = <2.1e21 ± not stated cm^-2 [3.3 FRB 20191001A site: "is $< \SI{2.1e+21}{cm^{-2}}$"]
- limitation (authors): Sample size too small for statistical conclusions; FRB-site limit not constraining. [3.1 HG 20191001A: "The sample size is insufficient to show that this difference is statistically significant"]
- not stated (card): Line-free channels used for continuum; Cleaning iteration limits and primary beam correction details; Flux calibrator and flux scale uncertainty; Aperture/region used for spectrum extraction and moment-0 integration; 3DBarolo parameter file details (initial guesses, mask, thresholds); How FRB-site column density and upper limits were computed in detail; SFR/stellar mass uncertainty propagation fo…

### 2020ApJ...899..165A: Local Starburst Conditions and Formation of GRB 980425/SN 1998bw within a Collisional Ring (2020; nearby_galaxies, star_formation, transients; observational_alma_primary)
- question: What are the molecular gas properties and depletion times on cloud scales near GRB 980425 in ESO 184-G82, and was the progenitor formed in situ or ejected from a starburst cluster?
- step 7: Upper limit on depletion time at GRB position
  - method: 3 sigma per channel over >=2 channels in ~150 pc region at GRB position [4 Discussion: "The upper limit is based on the CO(2-1) emission having a significance of 3$\sigma$ in each channel, and spread over at least two channels"]
- result: Upper limit tau_dep at GRB position = 0.37-1.25 ± not stated Gyr [4 Discussion: "we estimate an upper limit of $0.37-1.25$ Gyr for the molecular gas depletion time at the GRB position"]
- limitation (authors): Clump sizes unreliable, not reported, because they are smaller than the beam [3 Measurements and Results: "The size measurements are therefore not reliable and hence we do not report these measurements."]
- limitation (authors): Cloud-scale depletion times are not consistently measurable owing to gas-star offsets [3 Measurements and Results: "it is not possible to *consistently* measure the efficiency of star formation, or the depletion time, on cloud scales"]
- not stated (card): CASA version and pipeline version; Imaging task parameters (cell, image size, deconvolver, niter, threshold); Line-free channels / continuum subtraction method; Flux calibrator and flux scale uncertainty; Halpha map extraction regions for gas complexes; Exact MUSE reduction and Halpha flux measurement details; Distance used for physical scales

### 2018ApJ...862...94L: First ALMA Light Curve Constrains Refreshed Reverse Shocks and Jet Magnetization in GRB 161219B (2018; transients; multi_facility_alma_minor)
- question: What do multi-wavelength (radio to X-ray) observations, including the first ALMA light curve, reveal about the forward and reverse shocks, energetics, circumburst density and jet magnetization of GRB 161219B?
- step 2: Model forward shock with SN and host in all bands
  - method: Synchrotron FS model with jet break, SN 1998bw template, SMC extinction, MCMC [4 Multi-wavelength modeling: "we carry out a Markov Chain Monte Carlo (MCMC) analysis using the Python-based code EMCEE"]
  - software: emcee
  - parameter: 128 chains, 10^4 posterior samples, 10% uncertainty floor [4 Multi-wavelength modeling: "We initialized 128 Markov chains with parameters clustered around their best fit values (with a 3% dispersion)."]
  - assumption: ISM environment; uniform priors, log-uniform for scale parameters [4 Multi-wavelength modeling: "Priors for all scale parameters ($\epsilon_{\rm e}$, $\epsilon_{\rm B}$, $n_{0}$, $E_{\rm K,iso}$, $t_{\rm jet}$, and $\Upsilon_{\rm SN}$) are uniform in logarithmic space"]
  - fitting: emcee MCMC with uniform priors [4 Multi-wavelength modeling: "We assume uninformative, uniform priors on all free parameters."]
- step 3: Model reverse shock from energy injection and compare to FS
  - method: Analytic RS scaling relations anchored to cm and ALMA bands; compare with FS scaled by Lorentz factor [6.3 self-consistency: "We present a comparison between the observed RS parameters and the values expected by scaling the FS parameters by $\Gamma_{\rm E}$"]
  - assumption: pressure behind RS equals that at FS; same p; constant microphysical parameters [6.1: "make the simplifying assumption that the pressure behind the RS is equal to that at the FS"]
  - validation: Peak flux matches within 5% [6.3: "We find the peak flux density to match within 5%(!), suggesting that the RS is not magnetized relative to the FS."]
- result: circumburst density n0 = 3.2e-4 ± +1.4/-1.2 e-4 cm^-3 [Table: "$(3.2^{+1.4}_{-1.2})\times10^{-4}$"]
- result: jet break time = 33.0 ± +1.5/-1.4 d [Table: "$33.0^{+1.5}_{-1.4}$"]
- result: jet opening angle = 13.44 ± 0.35 deg [Table: "$13.44\pm0.35$"]
- result: beaming-corrected kinetic energy = 1.27e50 ± +0.36/-0.25 e50 erg [Table: "$(1.27^{+0.36}_{-0.25})\times10^{50}$"]
- result: electron index p = 2.079 ± +0.009/-0.006 dimensionless [Table: "$2.079^{+0.009}_{-0.006}$"]
- result: injection index m = 0.35 ± 0.09 dimensionless [5 Energy injection: "$m=(4\alpha_{\rm X}+3p-3)/(p+3) = 0.35\pm0.09$"]
- limitation (authors): nu_a not constrained, causing parameter degeneracies; epsilon_e~0.9 problematic [4.1 Afterglow: "We note that $\ensuremath{\nu_{\rm a}}$ is not constrained by the data, resulting in some degeneracies between the physical parameters"]
- not stated (card): ALMA imaging parameters (tclean weighting, cell, masking) and how flux densities were measured; CASA version and pipeline version; ALMA flux calibrator flux scale uncertainty; Full multi-frequency data tables (only samples printed); Exact MCMC burn-in length and convergence criteria (deferred to earlier papers)

### 2025ApJ...985..124L: The Nature of Optical Afterglows without Gamma-Ray Bursts: Identification of AT2023lcr and Multiwavelength Modeling (2025; transients; multi_facility_alma_minor)
- question: Why were optical afterglows without detected GRBs (AT 2023lcr, AT 2020blt, AT 2021any, AT 2021lfa) not seen with a GRB: off-axis jet, low initial Lorentz factor, or on-axis classical GRB missed by satellites?
- step 5: MCMC afterglow modelling of the radio, optical and X-ray data
  - method: afterglowpy jet models (top hat, Gaussian, power law) fit with the emcee EnsembleSampler to radio, optical and X-ray data, for several data subsets and afterglowpy settings [4.1 Settings: "We use `afterglowpy` (version 0.7.3; (cite: Ryan_2020)) and MCMC methods in `emcee` (version 3.1.4; (cite: Foreman_Mackey_2013)) to fit the radio, optical, and X-ray observations of AT 2023lcr"] [4.1 Settings: "We fit each model only to optical observations, then only to optical and X-ray observations, then to all radio, optical, and X-ray observations"]
  - software: afterglowpy, emcee
  - parameter: most runs: 64 walkers, 75,000 iterations, 30,000 burn-in; if not converged: 64 walkers, 225,000 iterations, 125,000 burn-in [4.1 Settings: "We perform most runs using 64 walkers and 75,000 iterations, discarding 30,000 iterations as the burn-in."] [4.1 Settings: "If samples do not appear converged with these settings, we run using 64 walkers and 225,000 iterations, discarding 125,000 as the burn-in."]
  - parameter: broad uniform priors (Table of priors, e.g. log10 Gamma_0 in [0,3], theta_c in [0.02,0.78] rad, p in [2,3]) [4.1 Settings: "To minimize bias, our priors are broad and uniform"]
  - parameter: afterglowpy runs repeated with and without ICC and with Gamma_0 infinite and finite [4.2 afterglowpy Limitations: "To work around this, we run MCMC multiple times, with each combination: with and without ICC; and with $\Gamma_0 = \infty$ and $\Gamma_0 \neq \infty$."]
  - parameter: X-ray fluxes converted to a 5 keV flux density with spectral index beta = -1 [4.1 Settings: "For all afterglows, we converted X-ray fluxes to a 5 keV flux density assuming a spectral index of $\beta = -1$, where $f_\nu \propto \nu^\beta$."]
  - assumption: homogeneous circumburst medium, single-shell approximation [4.2 afterglowpy Limitations: "to model a blast wave propagating through a homogeneous circumburst medium (cite: Ryan_2020)"]
  - assumption: Galactic extinction with R_V = 3.1; redshift z = 1.0272 for AT 2023lcr [4.1 Settings: "Optical observations were corrected for Galactic extinction with $E(B-V)=A_V/R_V$, assuming $R_V = 3.1$ (cite: Schlegel_1998)."] [2.2 Optical Spectroscopy: "we adopt $z=1.0272$ as the redshift of AT 2023lcr"]
  - fitting: emcee EnsembleSampler, uniform priors, simple Gaussian likelihood per data point; radio upper limits for AT 2020blt penalized against a zero-flux point [4.1 Settings: "We use a simple Gaussian likelihood for each data point."] [4.1 Settings: "For AT2020blt, we penalize samples that do not satisfy radio upper limits by finding the log likelihood between the sample-generated radio data point and a zero flux point."]
  - validation: model compared with observations and with earlier modelling of the same events [5.2 AT2023lcr: "The model is able to reproduce key features of all observations"]
- result: AT 2023lcr jet half-opening angle theta_c (on-axis top hat, finite Gamma_0) = 0.02 rad (1.15 deg) ± not stated rad [5.2 AT2023lcr: "with a highly collimated jet ($\theta_\text{c} \approx 0.02$ rad, or equivalently, $1.15^\circ$)"]
- result: AT 2023lcr beaming-corrected blast-wave energy E_K = 2.2e50 ± not stated erg [5.2 AT2023lcr: "we obtain a beaming-corrected value of the blast wave energy $E_{K} \approx 2.2 \times 10^{50}$ erg"]
- result: AT 2023lcr posterior initial Lorentz factor Gamma_0 = 166 ± not stated dimensionless [5.2 AT2023lcr: "our posterior $\Gamma_0 \approx 166$"]
- result: AT 2020blt opening angle and beaming-corrected E_K = theta_c ~ 5 deg; E_K ~ 4e50 erg ± not stated deg; erg [5.3 AT2020blt: "we obtain $\theta_\text{c} \sim 5^\circ$ and a beaming-corrected $E_\text{K} \sim 4 \times 10^{50}$ erg"]
- result: AT 2021any Gamma_0, free t_0 model = 204 ± +371/-115 dimensionless [5.4 AT2021any: "The free $t_0$ model finds $\Gamma_0 \approx 204_{-115}^{+371}$, while the fixed $t_0$ model finds $\Gamma_0 \approx 81_{-15}^{+17}$"]
- result: AT 2021any Gamma_0, fixed t_0 model = 81 ± +17/-15 dimensionless [5.4 AT2021any: "The free $t_0$ model finds $\Gamma_0 \approx 204_{-115}^{+371}$, while the fixed $t_0$ model finds $\Gamma_0 \approx 81_{-15}^{+17}$"]
- result: AT 2021lfa on-axis Gamma_0 (top hat; Gaussian) = 11; 6 ± not stated dimensionless [5.5 AT2021lfa: "$\Gamma_0 \approx 11$ for the top hat model and $\Gamma_0 \approx 6$ for the Gaussian model"]
- result: AT 2021lfa off-axis Gamma_0 (Gaussian; power law) = 110; 155 ± not stated dimensionless [5.5.2 Off-axis Interpretation: "the Gaussian jet with $\Gamma_0 \approx 110$ and power law jet with $\Gamma_0 \approx 155$"]
- result: AT 2021lfa off-axis Gaussian theta_c and theta_v = theta_c ~ 1.7 deg; theta_v ~ 3.4 deg ± not stated deg [5.5.2 Off-axis Interpretation: "we obtain $\theta_\text{c} \approx 1.7^\circ$ and $\theta_\text{v} \approx 3.4^\circ$ for the Gaussian solution"]
- limitation (authors): afterglowpy lacks reverse-shock physics, which may affect radio observations [4.2 afterglowpy Limitations: "In addition to the above, `afterglowpy` does not support reverse shock physics, which might particularly affect radio observations."]
- limitation (authors): afterglowpy has no synchrotron self-absorption, so low-frequency radio data are overpredicted [4.2 afterglowpy Limitations: "Also, `afterglowpy` lacks support for synchrotron self-absorption."]
- limitation (authors): afterglowpy supports only a homogeneous medium, with no stellar wind [4.2 afterglowpy Limitations: "Finally, `afterglowpy` implements a homogeneous circumburst medium, with no support for a stellar wind medium."]
- not stated (card): ALMA CASA and pipeline version, and whether pipeline products were used unchanged; ALMA flux, bandpass and phase calibrators, array configuration, baselines, and on-source time for each epoch; ALMA spectral window setup: the four frequencies (90.5, 92.4, 102.5, 105.5 GHz) appear only in the data table, not in the text; continuum bandwidth is not given; How the ALMA peak flux density and its error…

### 2021ApJ...912...21E: Late-time Radio and Millimeter Observations of Superluminous Supernovae and Long Gamma-Ray Bursts: Implications for Central Engines, Fast Radio Bursts, and Obs… (2021; transients, star_formation; observational_alma_primary)
- question: Search for late-time non-thermal synchrotron radio and millimeter emission from superluminous supernovae (SLSNe) and long gamma-ray bursts (LGRBs) to constrain central engines (magnetar wind nebulae, off-axis relativistic jets), non-relati…
- step 2: Search Phased-VLA observations for fast radio bursts (FRBs)
  - method: Perform RFI excision with rfifind, incoherently dedisperse filterbank time series across 1000 trial DMs, remove red noise, and search scans with matched-filtering single_pulse_search.py. [Phased VLA Observations: "We performed a standard RFI search using the `rfifind` routine in `PRESTO` (cite: Ransom2001) with two second integration times."] [Phased VLA Observations: "For each source, we incoherently dedispersed the data at $1000$ trial DMs ranging up to $\rm DM = 5000 \ \rm pc \ cm^{-3}$ with a step size of $5$"]
  - software: PRESTO (rfifind, single_pulse_search.py)
  - parameter: DM up to 5000 pc cm^-3 with step size 5; 256 us time resolution; 2 MHz channels; 7sigma threshold [Phased VLA Observations: "The phased-array data were recorded with 256 $\mu$s time resolution and 2 MHz channels with 2 GHz total bandwidth."] [Phased VLA Observations: "For each source, we incoherently dedispersed the data at $1000$ trial DMs ranging up to $\rm DM = 5000 \ \rm pc \ cm^{-3}$ with a step size of $5$"]
  - assumption: Phasing efficiency factor of 0.9, nominal pulse width W = 10 ms, and beaming fraction f_b = 0.5 [Phased VLA Observations: "Assuming a phasing efficiency factor of $0.9$ and a nominal $10$ ms pulse width, we find a minimum detectable flux density of $S_{\rm min}\approx 16$ mJy ($7\sigma$) for our observations."] [Phased VLA Observations: "where we assume a beaming fraction $f_b = 0.5$."]
- step 5: Constrain off-axis relativistic jets and minimum jet breakout energies
  - method: Generate a grid of 6 and 100 GHz off-axis jet afterglow light curves using Boxfit v2 to determine ruled-out (E_iso, n) space, and compute minimum jet breakout energy E_min from optical light curve kinetic energies E_K derived with MOSFiT. [Off-axis Relativistic Jets: "To constrain the presence of off-axis jets, we produce a grid of afterglow models for a range of jet energies and CSM densities using the two-dimensional relativistic hydrodynamical code `Boxfit v2` (cite: vanEerten2012)."] [Off-axis Relativistic Jets: "For each SLSN in our sample, we therefore estimate the minimal energy for jet breakout to determine whether our non-detections can constrain the theoretical predictions."]
  - software: Boxfit v2, MOSFiT
  - parameter: theta_j = 10 deg; theta_obs = 30, 60, 90 deg; epsilon_e = 0.1; epsilon_B = 0.01; p = 2.5; f_j = 0.5 [Off-axis Relativistic Jets: "We model the light curves assuming a jet opening angle of $\theta_j = 10^\circ$ and viewing angles of $\theta_{\rm obs} = 30^\circ$, $60^\circ$, and $90^\circ$."] [Off-axis Relativistic Jets: "We further assume a constant density CSM and jet microphysical parameters of $\epsilon_e = 0.1$, $\epsilon_B = 0.01$, and $p=2.5$"]
  - assumption: Constant density CSM; gamma_j = 1/(5 theta_j) [Off-axis Relativistic Jets: "where $E_K$ is the initial kinetic energy of the SN, $\gamma_j = 1/5 \theta_j$ as per (cite: Mizuta2013), and $f_j$ is the fraction of energy contributing to a collimated jet (cite: Margalit2018a)."]
  - fitting: Markov chain Monte Carlo fits to multicolor optical light curves using MOSFiT for magnetar/ejecta parameters. [Magnetar Wind Nebulae: "The parameters are derived via Markov chain Monte Carlo fits to the multicolor light curves using `MOSFiT`, an analytic Python-based modular code designed to model a variety of transients."]
- result: Minimum detectable FRB flux density (7sigma, 10 ms) = 16 ± not stated mJy [Abstract: "no FRBs are detected to a limit of $16$ mJy ($7\sigma$; 10 ms duration) in about 40 min on source per event."]
- result: Maximum FRB burst energy upper limits = <= 2e37 - 4e38 ± not stated erg [Phased VLA Observations: "For the range of redshifts probed by our initial VLA sample of SLSNe ($z \sim 0.101 - 0.376$), we find $E_{\rm b,max} \lesssim 2 \times 10^{37} - 4 \times 10^{38}$ erg."]
- result: Minimum isotropic jet breakout energy range for SLSNe = 7e52 - 6e54 ± not stated erg [Off-axis Relativistic Jets: "Finally, we note that the range of jet breakout energies ($E_{\rm min,iso} \approx 7 \times 10^{52} - 6 \times 10^{54}$ erg) for the SLSNe in our sample suggests that we do not expect a population of off-axis jets with energies comparable to the lowest energy LGRBs"]
- limitation (authors): Short phased-VLA observation duration (~40 min per source) is prohibitively small for detecting intermittent FRBs. [Phased VLA Observations: "Thus, while we are sensitive to the low energy range of FRBs (from FRB 121102), given the intermittent nature of FRB 121102, the short duration of our observations ($\approx 40$ min per source) is prohibitively small."]
- limitation (authors): ALMA 100 GHz observations are less constraining for obscured star formation rates and late-time off-axis jet afterglows because synchrotron emission peaks at lower (GHz) frequencies on these timescales. [Obscured Star Formation: "For the remaining SLSNe in our sample, the radio-inferred SFR limits exceed the optically-inferred rates by factors of $\approx 2-5.2\times 10^3$ (Table [\[tab:master\]](#tab:master)), where the high end is driven primarily by the ALMA 100 GHz observations, which are less constraining in this context."]
- limitation (authors): CLOUDY models start at t > 1 yr in the source frame, so 100 GHz free-free transparency timescales shorter than 1 yr (1+z) rely on extrapolations. [Magnetar Wind Nebulae: "Finally, we report upper limits on $t_{\rm ff, 100GHz}$ for eight sources where $t_{\rm ff, 100GHz} > 1 \rm{yr}$ $(1+z)$, as the `CLOUDY` models start from $t > 1$ yr in the source frame and these results are thus based on extrapolations."]
- not stated (card): Exact CASA version used for VLA processing and ALMA archival pipeline products; Exact ALMA array configurations and baseline ranges for the 2017 and 2019 campaigns; Exact pixel interpolation/regridding method used when median-combining ALMA images of different pixel scales (0.04-0.2 arcsec) and beam sizes for stacking; Exact fraction of magnetar spin-down power assumed to be deposited into ionizi…

### 2026ApJ..1000..159M: Low Dust Mass and High Star Formation Efficiency at z &gt; 12 from Deep ALMA Observations (2026; high_z_galaxies; observational_alma_primary)
- question: What are the dust mass build-up, dust production and growth mechanisms, and star formation efficiency of UV-bright galaxies at z > 12 (GHZ2 and GS-z14-0)?
- step 4: Model dust production history from star formation histories and stellar yields
  - method: Parameterize non-parametric SFHs (from Bagpipes and Prospector) with an exponential profile SFR(t) ∝ exp(t/τ) and integrate SN and AGB dust yields following Valiante et al. (2009) across stellar masses 0.1-100 M_sun to compare predicted du… [4.1. Dust production and evolution at c…: "The SFHs are parameterized with an exponential profile (SFR( _t_ ) _∝_ exp( _t/τ_ )), with star formation starting at _z_ = 20 for GHZ2 and _z_ = 30 for GS-z14-0."] [4.1. Dust production and evolution at c…: "Our predictions are based on a recipe presented in Valiante et al. (2009, see also, Schneider & Maiolino (2024) for recent review) with the SN dust yield from Bianchi & Schneider (2007) and Zhukovska et al. (2008), and the AGB dust yield from Ferrarotti & Gail (2006) and the ATON code (Dell’Agli et al. 2019)."]
  - software: Bagpipes, Prospector, ATON
  - parameter: Star formation start redshift z = 20 (GHZ2) and z = 30 (GS-z14-0) [4.1. Dust production and evolution at c…: "with star formation starting at _z_ = 20 for GHZ2 and _z_ = 30 for GS-z14-0."]
  - parameter: Yield metallicity range = 10^-4 to 0.1 Z_sun [4.1. Dust production and evolution at c…: "Given the metalpoor nature of the galaxies at _z_ _>_ 12, we use the dust yield model with the metallicity of 10 _[−]_ [4] –0 _._ 1 _Z_ _⊙_ ."]
  - parameter: Larson IMF with α = 1.35 and M_ch = 0.35 M_sun (and M_ch = 10 M_sun for top-heavy test), mass range 0.1-100 M_sun [4.1. Dust production and evolution at c…: "We integrate the dust yield from stars ranging 0 _._ 1–100 _M_ _⊙_ under a Larson (Larson 1998) IMF with _α_ = 1 _._ 35 and _M_ ch = 0 _._ 35, which is similar to a Salpeter IMF (Salpeter 1955)."] [4.1. Dust production and evolution at c…: "Specifically, ≲ 4% dust survival rate is required in GS-z14-0 under _M_ ch = 10 instead of _M_ ch = 0 _._ 35 in the Larson IMF (comparable to the top-heavy IMF)"]
  - assumption: Exponentially rising SFH parameterization and Larson IMF [4.1. Dust production and evolution at c…: "The SFHs are parameterized with an exponential profile (SFR( _t_ ) _∝_ exp( _t/τ_ )), with star formation starting at _z_ = 20 for GHZ2 and _z_ = 30 for GS-z14-0."] [4.1. Dust production and evolution at c…: "We integrate the dust yield from stars ranging 0 _._ 1–100 _M_ _⊙_ under a Larson (Larson 1998) IMF with _α_ = 1 _._ 35 and _M_ ch = 0 _._ 35"]
  - validation: Tested multiple SN yield tables (Bianchi & Schneider 2007; Zhukovska et al. 2008), AGB yield tables (Ferrarotti & Gail 2006; ATON), and varied IMF characteristic mass (M_ch = 0.35 vs 10). [4.1. Dust production and evolution at c…: "with the SN dust yield from Bianchi & Schneider (2007) and Zhukovska et al. (2008), and the AGB dust yield from Ferrarotti & Gail (2006) and the ATON code (Dell’Agli et al. 2019)."] [4.1. Dust production and evolution at c…: "Specifically, ≲ 4% dust survival rate is required in GS-z14-0 under _M_ ch = 10 instead of _M_ ch = 0 _._ 35 in the Larson IMF"]
- result: SN reverse shock dust destruction efficiency required for GS-z14-0 = > 80 ± not stated % [4.1. Dust production and evolution at c…: "For GS-z14-0, a high _>_ 80% destruction efficiency by SN reverse shocks is necessary to reproduce the observed dust-to-stellar mass ratios, while destruction is not necessarily significant for GHZ2 (see Figure 4)."]
- limitation (authors): It remains unclear whether an AGN contributes to the UV emission of GHZ2, requiring further observations to accurately constrain its stellar mass and potential AGN activity. [2.1. GHZ2: "Note that despite the rich dataset it is still unclear whether an active galactic nucleus (AGN) contributes to the UV emission of GHZ2 (see also, Calabro et al. 2024)."]
- limitation (authors): Band-8 observations of GHZ2 are much shallower than Band-6 and less constraining on M_dust. [3.1. ALMA data: "For GHZ2, the Band-8 observations have an r.m.s depth of 54 _._ 6 _µ_ Jy beam _[−]_ [1] with a beamsize of 0 _[′′]_ _._ 71 _×_ 0 _[′′]_ _._ 63, which is much shallower than Band-6 depth and less constraining on _M_ dust even when taking _T_ dust variation into account."]
- limitation (authors): If gas mass is not constrained via M_dyn - M_* and instead allowed to vary across f_gas = 0.1-0.9, it is impossible to disentangle dust models or place meaningful constraints on SFE without direct [C II] or CO observations. [4.1. Dust production and evolution at c…: "Nevertheless, it is impossible to disentangle any models with this broad _f_ gas range of 0.1–0.9. Further ALMA observations targetting [C ii] or CO lines will be a key to directly constrain _f_ gas and confirm the gas mass from the dynamical masses."]
- not stated (card): Exact frequency ranges of the spectral windows and exact central frequencies used for the continuum maps; Cell size and image dimensions used when generating the dirty continuum maps; Exact aperture or region definition over which the continuum r.m.s. noise was measured; Exact exponential decay/rise timescale parameter tau used to smooth the non-parametric star formation histories in Figure 4

### 2017MNRAS.465L..89P: A revised host galaxy association for GRB 020819B: a high-redshift dusty starburst, not a low-redshift gas-poor spiral (2017; high_z_galaxies, transients; multi_facility_alma_minor)
- question: Is the purported z=0.41 spiral really the host of GRB 020819B, or is the radio afterglow in an unrelated background galaxy?
- step 1: Blind line search and continuum check in archival ALMA data
  - method: Reanalysis of H14 ALMA observations in CASA, blind search of the entire spectrum at the afterglow site, continuum detection verified [ALMA Reanalysis: "performing a blind search of the entire spectrum at the afterglow site for line features. None were found"]
  - software: CASA
  - validation: Continuum flux consistent with H14 [ALMA Reanalysis: "we verify the continuum detection at a flux level consistent with value originally reported by H14"]
- limitation (authors): The association with the z=1.96 galaxy is not definitive [Discussion: "This association is not definitive, although we argue that it is likely."]
- not stated (card): Calibration procedure and whether archive products or a re-run script were used; Line search method, channel width and detection threshold for the blind search; Imaging parameters (weighting, cell, mask); Continuum measurement method

### 2017ApJ...850L..21K: ALMA and GMRT Constraints on the Off-axis Gamma-Ray Burst 170817A from the Binary Neutron Star Merger GW170817 (2017; transients, other; multi_facility_alma_minor)
- question: Can ALMA and GMRT non-detections plus public X-ray/radio data constrain the afterglow of GRB 170817A/GW170817 and the jet geometry (off-axis)?
- step 3: Compare with GRB samples
  - method: Compare luminosity limits to sub-mm/radio GRB samples and Swift X-ray light curves; compute Eiso distribution median/dispersion [3.1: "computed with (PY)MULTINEST"]
  - software: PyMultiNest, Swift Burst Analyser
- step 4: Broadband off-axis afterglow modeling
  - method: BOXFIT 9-parameter templates in homogeneous ISM across 1.4 GHz-X-ray [3.2: "We fix the fractions of $\epsilon_e$ and $\xi_N$ at 0.1 and 1, respectively, and $p$ to 2.43 and the redshift to 0.009854."]
  - software: BOXFIT
  - parameter: theta_jet 5-45 deg, E_AG,iso 1e47-1e53 erg, eps_B 1e-5-1e-2, n 1e-4-1e-1, theta_obs 0-45 deg [3.2: "E$_{\rm AG,\,iso} = 10^{47}$–$10^{53}$ erg, $\epsilon_B = 10^{-5}$–$10^{-2}$"]
  - assumption: epsilon_e=0.1, xi_N=1, p=2.43, z=0.009854 [3.2: "and $p$ to 2.43 and the redshift to 0.009854"]
  - fitting: best-matching templates identified; method not stated [Results and discussion, Modeling the br…: "The best-matching templates (colored curves in Fig. [3](#fig:lc)) strongly argue for a GRB seen off-axis"]
  - validation: Azimuthal resolution 20/30 compared with 70: flux within 20% [3.2: "able to recover the absolute flux scale at maximum to within 20%"]
- result: Model 1 theta_obs = 41 ± not stated deg [3.2: "The jet axis and the line of sight are misaligned by $41^\circ$."]
- result: Optical afterglow contamination of kilonova = <1 ± not stated % [3.2: "The contamination by the afterglow in the optical is negligible ($<1\%$)"]
- limitation (authors): Degeneracy due to few detections and large Epeak uncertainty [4 Summary: "Limiting this parameter study is the degeneracy in the afterglow parameters"]
- not stated (card): tclean weighting/robust, deconvolver, threshold; ALMA flux scale uncertainty and QA details; GMRT AIPS calibration and imaging parameters; Fit likelihood/optimizer for matching BOXFIT templates to data; how best models were chosen; epsilon_B, n and other parameter grid sampling and goodness-of-fit; Epeak/Egamma parameter-study grid sampling; Fixed values for the unlisted eighth frequency (21 GHz …

### 2026MNRAS.550g1193B: GOTO identification and broad-band modelling of the counterpart to the SVOM GRB 250818B (2026; transients; multi_facility_alma_minor)
- question: What are the physical parameters of the broadband afterglow, circumburst environment, and host-galaxy association of the SVOM-triggered GRB 250818B?
- step 5: Model broadband afterglow and compare jet/energy-injection models
  - method: Fit broadband X-ray, optical/NIR, and radio detections and upper limits with a baseline top-hat jet model (afterglowpy) and a refreshed-shock two-component jet model (twocomponent_redback_refreshed in redback). [`afterglowpy` Baseline Modelling: "A rapid afterglow modelling tool is provided by `afterglowpy` (cite: ryan2020), and in combination with `redback` (cite: sarin2024) this enables end-to-end modelling and inference."] [`redback` energy-injection test and mod…: "We use a refreshed shock, two-component model (cite: lamb2017; lamb2018; lamb2020) from `redback`, the `twocomponent_redback_refreshed` from their model library"]
  - software: afterglowpy, redback, nessai
  - parameter: For twocomponent_refreshed: fixed theta_obs = 0, log epsilon_e = -1, log epsilon_B = -2, xi_N = 1 [`afterglowpy` Baseline Modelling: "| $\theta_{\rm obs}$ (rad) | | $0, \pi/2$ | $\theta_{\rm obs}/\theta_j \leq 3/2$ | $0.07^{+0.03}_{-0.02}$ | | 0 | fixed | 0 |"] [`afterglowpy` Baseline Modelling: "| $\log \varepsilon_e$ | | $-5, 0$ | $\varepsilon_e + \varepsilon_B \leq 0.9$ | $-0.26^{+0.13}_{-0.19}$ | | $-1$ | fixed | $-1$ |"]
  - assumption: Constant-density circumburst medium (n_0), z = 1.216, flat LambdaCDM cosmology (H_0 = 70 km s^-1 Mpc^-1, Omega_m = 0.3, Omega_Lambda = 0.7) [Abstract: "Synchrotron forward-shock modelling favours a constant-density medium and strongly prefers refreshed (energy-injection) emission"] [Introduction: "Throughout this paper, we assume a flat $\Lambda$CDM cosmology with $H_{0} = 70~\mathrm{km~s^{-1}~Mpc^{-1}}$, $\Omega_{\rm m} = 0.3$ and $\Omega_{\Lambda} = 0.7$"]
  - fitting: Nested sampling with nessai using priors and conditions in Table 7 [`afterglowpy` Baseline Modelling: "We sample the posterior with the nested sampler `nessai` (cite: williams2023), adopting the priors listed in Table [\[tab:pri_post\]](#tab:pri_post)."]
  - validation: Bayesian model comparison via log Bayes factor and information score from nessai, plus 250 posterior draws overplotted on multiband light curves [`redback` energy-injection test and mod…: "The sampler, `nessai`, provides a log Evidence and an information score (cite: williams2021); despite the increased number of parameters for the `twocomponent_redback_refreshed` model, this is the preferred model."]
- result: Isotropic kinetic energy log E_iso (twocomponent_refreshed) = 52.60 ± +0.12/-0.13 erg (log10) [`afterglowpy` Baseline Modelling: "| $\log E_{\rm iso}$ (erg) | | $44, 54$ | \- | $52.48^{+0.23}_{-0.22}$ | | $44, 54$ | \- | $52.60^{+0.12}_{-0.13}$ |"]
- result: Circumburst density log n_0 (twocomponent_refreshed) = 0.56 ± +0.07/-0.07 cm^-3 (log10) [`afterglowpy` Baseline Modelling: "| $\log n_0$ (cm$^{-3}$) | | $-5,2$ | \- | $-0.21^{+0.93}_{-0.67}$ | | $-5,2$ | \- | $0.56^{+0.07}_{-0.07}$ |"]
- result: Core opening angle theta_c (twocomponent_refreshed) = 0.07 ± +0.01/-0.01 rad [`afterglowpy` Baseline Modelling: "| $\theta_c$ (rad) | | \- | \- | \- | | $0, 0.1$ | $\theta_c < \theta_j$ | $0.07^{+0.01}_{-0.01}$ |"]
- result: Jet opening angle theta_j (twocomponent_refreshed) = 0.10 ± +0.01/-0.02 rad [`afterglowpy` Baseline Modelling: "| $\theta_j$ (rad) | | $0, 0.3$ | \- | $0.07^{+0.03}_{-0.02}$ | | $0.02, 0.12$ | $\theta_j > \theta_c$ | $0.10^{+0.01}_{-0.02}$ |"]
- result: Electron energy distribution index p (twocomponent_refreshed) = 1.64 ± +0.05/-0.05 dimensionless [`afterglowpy` Baseline Modelling: "| $p$ | | $2, 3$ | \- | $2.05^{+0.03}_{-0.02}$ | | $1.4, 3.1$ | \- | $1.64^{+0.05}_{-0.05}$ |"]
- result: Log Bayes factor (twocomponent_refreshed vs afterglowpy top-hat) = 42.537 ± not stated dimensionless [`afterglowpy` Baseline Modelling: "| | | 25.82 | | $-42.537$ | | 21.98 | | $42.537$ |"]
- limitation (authors): Public prompt-emission constraints are limited (Fermi/GBM was in the SAA, and nominal short-GRB classification relies on SVOM discovery notices). [Observations: "We inspected the publicly available *Fermi*/GBM time-tagged event (TTE) data around $T_{0}$ and found that the spacecraft appears to have been traversing the South Atlantic Anomaly at that time; accordingly, no on-board or ground trigger was reported."]
- limitation (authors): The 10 GHz VLA measurement from GCN 41455 had no reported uncertainty, requiring an assumed uncertainty for modelling. [Radio and millimeter/submillimeter: "In addition, we include the 10 GHz flux density reported in GCN 41455 (cite: Ricci2025gcn41455). As no uncertainty was provided, the point is shown as indicative in Fig. 2; for modelling, we assign an assumed uncertainty to prevent the fit from being dominated by this measurement."]
- limitation (authors): Host-frame afterglow extinction A_V^host is weakly constrained by only three photometric points (1 dof) and is sensitive to host-subtraction and cross-calibration systematics. [Optical SED and line-of-sight extinction: "Given that the fit is constrained by only three photometric points (one degree of freedom) and is sensitive to host-subtraction and cross-calibration systematics, these numerical values should be regarded as indicative rather than definitive."]
- not stated (card): Assumed uncertainty value assigned to the GCN 41455 10 GHz VLA data point during afterglow modelling; Exact likelihood function and treatment of upper limits in redback / afterglowpy nested sampling fits; Hyperparameter values (kappa_c) for the short and long GRB Gamma offset priors in the Bayesian host association analysis; Schechter luminosity function parameters (M*, alpha, M_max) used to comp…

### 2021A&A...650A.117N: The host galaxy of the short GRB 050709 (2021; transients, nearby_galaxies, star_formation; multi_facility_alma_minor)
- question: Characterize the physical properties (star formation rate, metallicity, gas kinematics, excitation mechanisms, merger history) of the host galaxy of short GRB 050709 and constrain late-time radio emission.
- step 3: Reduce ATCA radio continuum data and measure fluxes/upper limits
  - method: Reduce ATCA 5.5 and 9.0 GHz visibilities in MIRIAD, image with robust weighting (0.0 to 2.0) and tapering, check astrometry against cataloged quasars, and derive upper limits on point-source afterglow/kilonova emission and extended emissio… [3.2. ATCA radio-continuum observations: "Data reduction was performed in a standard manner using the Multichannel Image Reconstruction, Image Analysis and Display (MIRIAD) software package for ATCA radio interferometry (for details, see Sault et al. 1995) 5"] [3.2. ATCA radio-continuum observations: "The Briggs “robust” parameter (Briggs 1995) was varied between 0.0 and 2.0 (natural weighting for maximum sensitivity)."]
  - software: MIRIAD
  - parameter: Briggs robust = 0.0 to 2.0; uv taper FWHM = 5 arcsec [3.2. ATCA radio-continuum observations: "The Briggs “robust” parameter (Briggs 1995) was varied between 0.0 and 2.0 (natural weighting for maximum sensitivity)."] [3.2. ATCA radio-continuum observations: "Adding some tapering (full width half maximum = 5 arcsec) increases the noise level to 8 µJy and the extended emission level to 40 µJy;"]
  - assumption: Isotropic emission, spectral slope beta = -1/3 or 0.7 for radio AG and beta = 0.7 for kilonova flare [5.3. Constraints on GRB late-time emiss…: "Here, for the radio AG we considered its spectral slope ( F ν ∼ ν − β ) to be either β = −1/3 or 0.7, and for a kilonova radio flare we set β = 0.7."]
  - validation: Astrometry checked against two known quasars B2258-391 and NVSS J230132-385927 [3.2. ATCA radio-continuum observations: "We double-checked the astrometry of the resulting radio images by comparing the position of two known radio sources in the field with their published coordinates."]
- result: ATCA 5.5 GHz point-source flux density at GRB position (3 sigma upper limit) = < 15 ± not stated µJy [3.2. ATCA radio-continuum observations: "At standard resolution (robust parameter = 0), there is no evidence for a source at the GRB position at either frequency ( F ν (5.5 GHz) < 15 µJy, F ν (9.0 GHz) < 15 µJy; 3σ)."]
- result: ATCA 9.0 GHz point-source flux density at GRB position (3 sigma upper limit) = < 15 ± not stated µJy [3.2. ATCA radio-continuum observations: "At standard resolution (robust parameter = 0), there is no evidence for a source at the GRB position at either frequency ( F ν (5.5 GHz) < 15 µJy, F ν (9.0 GHz) < 15 µJy; 3σ)."]
- result: ATCA 5.5 GHz tapered extended emission flux near GRB position = 40 ± 8 µJy [3.2. ATCA radio-continuum observations: "Adding some tapering (full width half maximum = 5 arcsec) increases the noise level to 8 µJy and the extended emission level to 40 µJy;"]
- result: Late-time 5.5 GHz radio specific luminosity upper limit (beta = 0.7) = < 1.8e28 ± not stated erg s^-1 Hz^-1 [Table 2: "5.5 GHz 1.5 1.8 0.8 0.9"]
- limitation (authors): Scheduled ALMA Band 9 observations could not be performed due to weather constraints. [3.3. ALMA millimeter observations: "Unfortunately, due to weather constraints observations in band 9 could not be performed despite being scheduled."]
- limitation (authors): The faint ATCA 5.5 GHz extended emission near the GRB site is at the ~5 sigma level, so there is no guarantee that it is real and it is too faint to split in time or frequency. [3.2. ATCA radio-continuum observations: "We conclude that there may be some extended emission at the GRB explosion site at the 5σ level. This is too faint to perform a more detailed analysis (e.g., splitting in time or frequency). It does not look like a spurious source, but at the S/N level at which we detect it there is no guarantee that it is real."]
- limitation (authors): Small angular sizes (< 0.2''), faintness, and strong host foreground emission prevent MUSE from clarifying the nature of individual clumps C-G and K-M. [4.1. The nature of objects C-G and K-M: "While the HST image seems to provide compelling evidence that these are star-forming regions, young luminous stellar clusters, or background (foreground) galaxies, their individual nature cannot be clarified with certainty using the MUSE data cube."]
- not stated (card): CASA tclean cell size, image size, and deconvolver settings for ALMA imaging; Relative data weights applied when combining the C40-6 and C40-3 ALMA execution blocks; Exact emission line profile fitting procedure/code used to extract line fluxes, velocities, and velocity dispersions from the gas-phase MUSE cube

### 2025ApJ...987L...2H: Dissecting the Massive Pristine, Neutral Gas Reservoir of a Remarkably Bright Galaxy at z = 14.179 (2025; high_z_galaxies; multi_facility_alma_minor)
- question: Reanalyse the JWST/NIRSpec prism spectrum of GS-z14 to measure its H I column density from the damped Lyman-alpha profile and combine it with published ALMA [O III]-88um, [C II]-158um and dust-continuum constraints to determine the gas con…
- step 5: Upper bound on H I mass from the [C II] non-detection
  - method: Apply the metallicity-dependent [C II]-to-H I conversion calibrated on gamma-ray burst sightlines to the [C II] luminosity limit [Analysis and results: "we derive an upper bound of $M_{\rm HI} < 10^{9.9}\,M_\odot$ ($3\sigma$)"]
  - parameter: [C II] limit L < 6e7 Lsun; metallicity Z/Zsun = 0.17 [Observations: "resulted in a non-detection at a limit $<6\times 10^{7}\,L_\odot$ (cite: Schouws25)"]
- step 8: Line-of-sight dust-to-gas ratio A_V/N_HI
  - method: Derive A_V from the observed rest-UV slope assuming an intrinsic beta_UV = -3 and an SMC-like reddening curve, divide by N_HI from the DLA fit, and compare with GRB sightlines and MW/SMC/LMC averages [Analysis and results: "Assuming a steep, intrinsic power-law with $\beta_{\rm UV} = -3$ requires $A_V = 0.3$ mag for a SMC-like reddening curve (cite: Gordon03)"]
  - parameter: Intrinsic beta_UV = -3; A_V = 0.3 mag [Analysis and results: "This quantity is effectively the maximum allowed amount of dust in the line-of-sight that will extinguish the light"]
  - assumption: SMC-like reddening curve; intrinsic slope beta_UV = -3 (A_V is an upper limit) [Analysis and results: "for a SMC-like reddening curve (cite: Gordon03) to match the observed rest-frame UV spectral slope"]
  - validation: Consistent with SED-modelling A_V = 0.25 +/- 0.10 from Carniani24b [Analysis and results: "This upper bound is also consistent with the visual attenuation $A_V = 0.25\pm 0.10$"]
- result: H I mass upper bound from [C II] non-detection = < 10^9.9 ± 3 sigma Msun [Analysis and results: "we derive an upper bound of $M_{\rm HI} < 10^{9.9}\,M_\odot$ ($3\sigma$)"]
- result: Upper limit visual extinction A_V = 0.3 ± not stated mag [Analysis and results: "requires $A_V = 0.3$ mag for a SMC-like reddening curve (cite: Gordon03)"]
- result: Dust-to-gas ratio A_V/N_HI = 1.3e-23 ± 0.6e-23 mag cm^2 [Analysis and results: "This yields a dust-to-gas ratio of $A_V/N_{\rm HI} = (1.3\pm 0.6)\times 10^{-23}$ mag cm$^{2}$."]
- result: Gas-phase metallicity range from dust-to-gas relation = -1.95 < [M/H] < -1.15 ± not stated dex [Analysis and results: "indicate a gas-phase metallicity of $-1.95 < {\rm [M/H]} < -1.15$"]
- limitation (authors): H I mass from N_HI depends heavily on the assumed geometry [Analysis and results: "However, this estimate of $M_{\rm HI}$ from the DLA $N_{\rm HI}$ is heavily dependent on the assumed geometry of the system."]
- limitation (authors): A_V is only an upper bound on the dust in the line of sight [Analysis and results: "This quantity is effectively the maximum allowed amount of dust in the line-of-sight that will extinguish the light"]
- not stated (card): Priors and bounds for log N_HI, x_HI and beta_UV in the dynesty fit, and the nested-sampling settings (live points, stopping criterion); Wavelength range of the prism spectrum used in the fit and how the 'full spectrum' chi^2 and BIC were counted (degrees of freedom, error treatment); Which version of the NIRSpec reduction and which spectral extraction were used (spectrum is on Zenodo but pipelin…

### 2017MNRAS.464.4624S: GRB 110715A: the peculiar multiwavelength evolution of the first afterglow detected by ALMA (2017; transients; multi_facility_alma_minor)
- question: What are the physical parameters of the jet and environment of GRB 110715A, constrained by broadband afterglow modelling of 17-band follow-up including the first ALMA GRB afterglow observation?
- step 1: Fit broadband afterglow with numerical forward-shock model
  - method: Numerical top-hat jet forward-shock model with energy injection or wind termination shock, fitted with Bayesian inference to X-ray, UV/optical/NIR, submm and radio data [Model and fitting description: "The best fit model parameters are found using Bayesian inference using the MultiNest tool (cite: 2009MNRAS.398.1601F)."]
  - software: MultiNest
  - parameter: Flat (uniform/log-uniform) priors on all parameters except Galactic reddening (Gaussian, mu=0.56, sigma=0.04) [Table 5: "(c) $\mu$ = 0.56, $\sigma$ = 0.04"]
  - parameter: UVOT UV filters and u band excluded in best fits [Model and fitting description: "We excluded the upper limits from the UV filters of UVOT as well as observations using its $u$-band filter"]
  - assumption: SMC-like host extinction curve [Model and fitting description: "we also determine the host dust extinction in the fit, which we assume follows an SMC-like extinction curve"]
  - fitting: MultiNest Bayesian inference; models CM, WM, TS compared via evidence and reduced chi2 [Model and fitting description: "We chose three different types of models that we expect have this behaviour"]
  - validation: Grid of 36 fits with different data cuts; none statistically good [The best fit: "However, none of them is either a statistically good fit or can fully explain the temporary flux increase at $\sim$0.3 days."]
- result: TS model electron index p = 1.8148 ± 0.0041 dimensionless [Table of best fit parameters: "$1.8148 \pm 0.0041$"]
- limitation (authors): Poor temporal sampling limits constraints [Conclusions: "This shows the need for better broadband sampling and more complex models"]
- not stated (card): ALMA calibration, CASA version, flux calibrator and imaging details; How the 4.9 mJy ALMA flux was measured (inherited from De Ugarte Postigo 2012); Full photometric table is only online; MultiNest settings (live points, tolerance); Likelihood form and systematic error treatment

### 2026ApJ...998..111C: Continued Rapid Radio Brightening of the Tidal Disruption Event AT2018hyz (2026; transients; multi_facility_alma_minor)
- question: What is the physical origin and geometry of the continued, rapidly rising late-time radio and millimeter emission from the tidal disruption event AT2018hyz?
- step 5: Model off-axis relativistic jet scenarios (generalized equipartition and structured jet forward modeling)
  - method: Apply generalized off-axis equipartition analysis of Matsumoto & Piran (2023) using $\nu_m$ constraint, and forward model afterglow emission from a steep angular structured jet [Off-Axis Relativistic Jet: "Below we consider two off-axis jet model approaches, using the analytic formalism of (cite: Matsumoto2023), which is an extension of the equipartition analysis in the spherical case from §4.2, and the numerical approach of (cite: Gill-Granot-18)"]
  - parameter: Top-hat jet: $f_A=f_V=(\Gamma\theta_j)^2$, $\theta_j=0.1$, $\epsilon_e=0.1$, $\epsilon_B=10^{-3}$, $\eta=1$; Structured jet: $k=0$, $q\approx 12$, $a\approx b\approx 12$ [Generalized Equipartition Analysis: "We assume a narrow jet geometry with $f_{A}=f_{V}=(\Gamma\theta_{j})^2$ and $\theta_{j}=0.1\,(\approx5.7^{\circ})$ (see Appendix B in (cite: Matsumoto2023)), and take into account the deviation from equipartition with $\epsilon_{e}=0.1$ and $\epsilon_{B}=10^{-3}$."] [Off-Axis Jet with Steep Angular Structu…: "The key finding is that the model requires a large off-axis viewing angle, with $q\approx 12$, in good agreement with the simple top-hat calculation in §5.2.1. This, coupled with the steep gradient in the angular structure, with $a\approx b\approx 12$"]
  - assumption: Thin-shell geometry, locally spherical dynamics without lateral spreading, constant density external medium ($k=0$), and ad-hoc $\epsilon_e\propto t^4$ at early times for the structured jet [Off-Axis Jet with Steep Angular Structu…: "Lateral spreading of the flow, which becomes important as the initially relativistic jet is sufficiently decelerated (cite: Rhoads-99; Sari+99; Granot-Piran-12), is not included in the model"] [Off-Axis Jet with Steep Angular Structu…: "Our model includes an ad-hoc temporal evolution of $\epsilon_e\propto t^4$ in the first few hundred days of evolution"]
  - validation: Compared predicted $\nu_m$ across viewing angles $\theta_{\rm obs}=70-90\,\rm deg$ against observed SEDs [Generalized Equipartition Analysis: "We find that only viewing angles of $\theta_{\rm obs} \gtrsim 80^{\circ}$ have predicted values of $\nu_m$ in agreement with the observed value"]
- result: Off-axis jet viewing angle (theta_obs) = 80-90 ± not stated deg [Generalized Equipartition Analysis: "We therefore conclude that if AT2018hyz harbors an off-axis jet, then its viewing angle is $\approx 80-90^{\circ}$."]
- limitation (authors): Cannot currently distinguish between the delayed spherical outflow and prompt highly off-axis jet scenarios until the light curve peak is observed or VLBI imaging is obtained [Introduction: "the true origin of the outflow will not be clear until we see the end of the rise in the radio light curve."]
- limitation (authors): Lateral spreading of the jet is not included in the structured jet forward model [Off-Axis Jet with Steep Angular Structu…: "Lateral spreading of the flow, which becomes important as the initially relativistic jet is sufficiently decelerated (cite: Rhoads-99; Sari+99; Granot-Piran-12), is not included in the model (cite: Kumar-Granot-03; vanEerten-MacFadyen-12; Duffell-Laskar-18)."]
- limitation (authors): The structured jet forward model requires an ad-hoc temporal evolution of epsilon_e proportional to t^4 at early times [Off-Axis Jet with Steep Angular Structu…: "Our model includes an ad-hoc temporal evolution of $\epsilon_e\propto t^4$ in the first few hundred days of evolution"]
- not stated (card): How ALMA flux densities were extracted (e.g., whether pwkit imtool fitsrc, CASA imfit, or peak pixel was used on ALMA images); Exact forward-modeling parameters for the structured jet (e.g., exact values of core energy, core Lorentz factor, core opening angle, and external density normalization A); Cosmological parameters assumed to convert redshift z=0.0457 to luminosity distance

### 2021ApJ...915...46C: ALMA Host Galaxy Observation of the Off-axis Gamma-Ray Burst XRF 020903 (2021; transients, high_z_galaxies; observational_alma_primary)
- question: Whether the submillimeter/millimeter radio properties (dust continuum, CO emission, molecular gas mass, and gas depletion timescale) of the off-axis GRB XRF 020903 host galaxy resemble those of classical GRB host galaxies, supporting an id…
- step 1: Calibrate and image ALMA continuum and CO(1-0) observations
  - method: Run ALMA Science Pipeline calibration, merge execution blocks where needed (GRB 050709), and image continuum and a 180 km s^-1 CO(1-0) velocity-integrated map using TCLEAN with Briggs weighting [XRF 020903: "Data calibration was performed using the ALMA Science Pipeline Software of CASA version 4.7.0-1. Maps were processed using the TCLEAN algorithm with the Briggs weighting (with a robust parameter of 0.5)."] [XRF 020903: "Furthermore, a CO ($J=1-0$) velocity-integrated map with a velocity width of 180 km $^{-1}$ was created using the TCLEAN algorithm."]
  - software: CASA, ALMA Science Pipeline Software, TCLEAN
  - parameter: Briggs weighting with robust = 0.5 [XRF 020903: "Maps were processed using the TCLEAN algorithm with the Briggs weighting (with a robust parameter of 0.5)."]
  - parameter: CO(1-0) velocity integration width = 180 km s^-1 [XRF 020903: "Furthermore, a CO ($J=1-0$) velocity-integrated map with a velocity width of 180 km $^{-1}$ was created using the TCLEAN algorithm."]
- limitation (authors): The CO-to-H2 conversion factor is difficult to estimate and not well established in the low-metallicity regime. [Molecular Gas Mass: "In the low-metallicity range, the conversion factor estimation becomes difficult, because the estimation methods have not yet been established."]
- limitation (authors): A comparable galaxy sample in the same stellar mass range did not exist for comparing M_gas. [Molecular Gas Mass: "A comparable sample in the same stellar mass range did not exist."]
- limitation (authors): The upper limit on the molecular gas mass fraction (mu_gas) could not constrain the redshift trend effectively. [Molecular Gas Mass-SFR, Gas Fraction, a…: "Although the upper limit of $\mu_{\rm gas}$ could not constrain the trend effectively, the limit of $t_{\rm depl}$ was consistent with the results of most of GRB samples (e.g., GRB 980703, GRB 021211, GRB 031203, GRB 050826, GRB 060814, GRB 070306, GRB 071021, GRB 081109A, GRB 110918A), and one of SLSN, PTF10tpz."]
- not stated (card): ALMA project codes for the archival GRB host galaxy continuum observations re-evaluated in Table 1 (GRB 050401, GRB 050915A, GRB 070802, GRB 081221, GRB 111123A, GRB 120624B, GRB 130606A); Exact cell size, image size, and cleaning thresholds/masking used in TCLEAN for XRF 020903 and GRB 050709; Continuum subtraction procedure (if any) before creating the CO(1-0) velocity-integrated map; Reason fo…

### 2017ApJ...848L..21A: The Electromagnetic Counterpart of the Binary Neutron Star Merger LIGO/Virgo GW170817. VI. Radio Constraints on a Relativistic Jet and Predictions for Late-tim… (2017; transients, high_z_galaxies; multi_facility_alma_minor)
- question: Do radio/mm observations of GW170817 constrain a relativistic SGRB jet (on- or off-axis) and what late-time radio emission is expected from the kilonova ejecta?
- step 2: Compare radio limits/detections with on-axis afterglow models
  - method: Standard afterglow synchrotron model in constant density medium [Afterglow constraints: "we utilize the standard afterglow synchrotron model in a constant density medium (cite: gs02)"]
  - assumption: epsilon_e=0.1, eta_gamma=0.1 [On-axis Afterglow Models: "(assuming an efficiency of $\eta_\gamma=0.1$)"]
- step 3: Constrain off-axis jet parameters
  - method: BOXFIT grid over E_K, n, theta_j, theta_obs, epsilon_B; compare with radio and X-ray [Off-axis Afterglow Models: "for a wide range of kinetic energies, densities, jet opening angles, observer orientations, and $\epsilon_B$"]
  - software: BOXFIT
  - parameter: p=2.2 adopted; epsilon_e=0.1 [Off-axis Afterglow Models: "All simulations discussed for the remainder of this paper assume $p=2.2$"]
- step 4: Predict kilonova ejecta radio emission
  - method: Blue and red ejecta components with fiducial n=1e-3 cm^-3 and range from jet modeling [Predictions: "for a fiducial density of $n=1\times10^{-3}$ cm$^{-3}$ (solid lines)"]
- result: Observer viewing angle (jet+X-ray) = 20-40 ± not stated deg [Off-axis Afterglow Models: "tightens the viewing angle constraint to $20^{\circ}\lesssim\theta_{\rm obs}\lesssim40^{\circ}$"]
- result: Circumbinary density = 1e-4 to 1e-2 ± not stated cm^-3 [Off-axis Afterglow Models: "low densities $n\sim 10^{-4}-10^{-2}$ cm$^{-3}$"]
- limitation (authors): Bad weather may cause flux decorrelation at high frequency in the Sep 5 epoch [Observations: "these data may suffer from flux decorrelation"]
- not stated (card): ALMA phase and gain calibrators, CASA version, and custom pipeline details; Imaging parameters (weighting, robust, cell/image size, deconvolver); Parameter grid ranges and fitting/comparison criteria for BOXFIT; Kilonova radio emission model and equations used for Figure 4; ALMA flux scale uncertainty

### 2024ApJ...974...18C: The Peculiar Radio Evolution of the Tidal Disruption Event ASASSN-19bt (2024; transients; multi_facility_alma_minor)
- question: Radio evolution of the TDE ASASSN-19bt, tested against an off-axis relativistic jet or a spherical non-relativistic outflow
- step 8: Fit evolution laws, estimate launch dates and circumnuclear density profiles
  - method: Linear fit of radius versus time extrapolated to R = 0 for the launch date; power-law fits to R, E, B, n and Gamma versus time; compare with other TDEs [5.3 Multiple Outflows?: "then we can apply a linear fit to the radius evolution and extrapolate to $R = 0$."] [5.2 Circumnuclear Density: "In the relativistic model, we estimate the density of the unshocked ambient medium at radius $R$ as $n_\text{ext} = n_e/4\Gamma^2$"]
  - assumption: Constant outflow velocity for the linear-radius launch-date estimate [5.3 Multiple Outflows?: "if the outflow is assumed to be moving at a constant velocity"]
  - validation: Launch dates compared against the first detection at delta t = 40 days [5.3 Multiple Outflows?: "which is inconsistent with our initial radio detection at $\delta t = 40$ days."]
- result: Launch date from linear fit to all radius data = 46 ± not stated days (delta t) [5.3 Multiple Outflows?: "applying a linear fit to all of the data implies a launch date of $\delta t \approx46$ days"]
- result: Launch date from linear fit to later epochs = approximately 210 ± not stated days (delta t) [5.3 Multiple Outflows?: "would imply a launch date of $\delta t \approx 210$ days"]
- result: Density profile slope, off-axis jet model = n(r) proportional to r^-4.3 early, r^-2.6 late ± not stated dimensionless [5.2 Circumnuclear Density: "the constructed density profile decays as $n(r)\propto r^{-4.3}$ at early times and as $n(r)\propto r^{-2.6}$ at late times"]
- limitation (authors): Chandra spectra have too few counts to constrain the spectral shape [2.3 X-rays: Chandra X-ray Observatory: "Due to the low-number statistics, we cannot statistically constrain the spectral shape and both thermal and non-thermal models are statistically acceptable."]
- limitation (authors): Inferred Gamma depends on the assumed jet launch date [4.2 Relativistic Jet from an Arbitrary …: "We note that $\Gamma$ is dependent on the inferred launch date of the jet"]
- not stated (card): ALMA imaging recipe: clean task, weighting/robust, cell size, image size, masking, uv range, spectral windows and bandwidth used for the continuum; ALMA beam sizes, image rms and integration time per execution block, and how the upper limit on 2019 June 20 was defined (sigma level); Whether the pipeline products were used as delivered or manually re-flagged, and the flux density assumed for J0519…

### 2023NatAs...7...80U: Simultaneous radio and optical polarimetry of GRB 191221B afterglow (2023; transients; observational_alma_primary)
- question: Is the radio (97.5 GHz) polarization of the GRB 191221B afterglow depolarized relative to the optical, and what does this say about magnetic field configuration and cool electrons / jet energy?
- step 3: Model afterglow light curves and SED
  - method: Numerical forward-shock synchrotron model with Blandford-McKee solution, equal arrival time surface, fixed theta_j; adjust parameters to fit radio-optical-X-ray data [Methods: "We performed numerical calculations of flux from the shock with a fixed $\theta_j$ which evolves as the Blandford-McKee (BM) self-similar solution"]
  - assumption: Uniform density medium, energy injection E_iso propto t^0.25 [Methods: "the ambient density is uniform and the energy continues to be injected to the shock by long activity of the central engine"]
  - validation: Model also explains X-ray and optical [Introduction: "The model also explains the X-ray and optical afterglows"]
- result: 97.5 GHz light curve break time = 3.77 ± 0.35 days [Introduction: "a break-time at $3.77\pm 0.35$ days"]
- result: Pre-break index alpha = 0.26 ± 0.02 dimensionless [Introduction: "$\alpha = 0.26\pm 0.02$ (before the break)"]
- result: Post-break index alpha = -1.62 ± 0.13 dimensionless [Introduction: "$\alpha = -1.62\pm 0.13$ (after the break)"]
- limitation (authors): PA difference between radio and optical only ~90% significant [Methods: "the PA between radio and optical is different at $\sim$90% confidence level."]
- not stated (card): tclean parameters: weighting/robust, cell size, image size, masks; Self-calibration solution intervals; Beam sizes and image rms values; Fitting method/priors for the afterglow model and light curve broken power law; Numerical afterglow polarization code is not public; ALMA configurations and on-source times; Source coordinates

### 2019Natur.575..459M: Observation of inverse Compton emission from a long γ-ray burst (2019; transients; multi_facility_alma_minor)
- question: What is the broadband emission of GRB 190114C from radio to TeV, and is the TeV emission a distinct inverse Compton (SSC) component of the afterglow?
- step 2: Model broadband SED and light curves as synchrotron plus SSC forward shock
  - method: Numerical code solving electron distribution evolution with synchrotron, SSC, adiabatic losses, gamma-gamma absorption, pairs, self-absorption [Methods, Afterglow model: "we use a numerical code that solves the evolution of the electron distributions and derives the radiative"]
  - parameter: s = 0, eps_e = 0.07, eps_B = 8e-5, p = 2.6, n0 = 0.5, Ek = 8e53 erg [Methods, Afterglow model: "we have used s = 0, ϵ e = 0.07, ϵ B = 8 × 10 −5, p = 2.6, n 0 = 0.5, and E k = 8 × 10 53 erg."]
  - assumption: Power-law density profile s=0 or s=2; power-law electron distribution [Methods, Afterglow model: "We consider two types of power law radial profiles n(R) = n0 R −s for the external environment: s = 0 (homogeneous medium) and s = 2"]
  - validation: Model curves compared by eye with data (Fig. 3, Extended Data Figs 6, 7) [Methods, Afterglow model: "The results of the modeling are overlaid to the data in Fig. 3, and Extended Data Figs. 6 and 7."]
- result: Synchrotron energy, 68-110 s = 1.5e52 ± not stated erg [Main text: "∼ 1.5 × 10 52 erg and ∼ 6.0 × 10 51 erg respectively in the time interval 68-110 s"]
- result: SSC energy, 68-110 s = 6.0e51 ± not stated erg [Main text: "∼ 1.5 × 10 52 erg and ∼ 6.0 × 10 51 erg respectively in the time interval 68-110 s"]
- result: Bulk Lorentz factor at 100 s = ~140-160 ± not stated dimensionless [Main text: "the bulk Lorentz factor is ∼ 140-160 at 100 s"]
- not stated (card): ALMA flux values and uncertainties are not tabulated; photometry method (aperture, fitting) and calibrators not given; ALMA flux scale uncertainty not given; imaging parameters not given; numerical afterglow code not public

### 2025ApJ...993L...6N: The Most Luminous Known Fast Blue Optical Transient AT 2024wpp: Unprecedented Evolution and Properties in the X-Rays and Radio (2025; transients; multi_facility_alma_minor)
- question: What are the X-ray and radio (including early millimeter) properties and evolution of the most luminous FBOT AT 2024wpp, what shock and circumstellar environment do they imply, and what progenitor do they favor?
- step 8: derive time evolution of the shock and the CSM density profile
  - method: Power-law fits to F_pk, nu_pk and R versus time over three phases, then CSM density versus radius compared with other LFBOTs [6 The origin and evolution of the radio…: "The corresponding evolution of the peak frequency is"] [6.3 Radio emitting outflow propagating …: "The CSM density profile derived from later"]
  - assumption: Effective mass-loss rate computed for an arbitrary wind velocity of 1000 km/s [8.1 A universal CSM density profile in …: "for an arbitrary wind velocity of"]
- result: SED peak flux evolution F_pk proportional to t^a, 17-32 d (rest frame) = 4.04 ± 0.42 dimensionless [6 The origin and evolution of the radio…: "The peak flux density increases as"]
- result: Peak frequency evolution nu_pk proportional to t^a, 32-73 d = -2.99 ± 0.10 dimensionless [6 The origin and evolution of the radio…: "The corresponding evolution of the peak frequency is"]
- result: Shock radius evolution R proportional to t^a = 3.12 ± 0.12 dimensionless [6 The origin and evolution of the radio…: "The physical parameters inferred from single epoch spectral analysis imply a rapidly growing radio emitting region"]
- result: CSM density profile index, rho proportional to r^-s, 46-118 d = 3.10 ± 0.16 dimensionless [6.3 Radio emitting outflow propagating …: "The CSM density profile derived from later"]
- result: Effective mass-loss rate of the CSM (v_w = 1000 km/s) = up to 1e-3 ± not stated Msun/yr [8.1 A universal CSM density profile in …: "mass-loss rates up to"]
- limitation (authors): Equipartition-based energy is a lower limit [6.2 Off-axis models: "is a lower limit due to the equipartition assumption"]
- limitation (authors): Parameters at dt_rest ~ 17.5 d are not physical because the SED is free-free absorbed [Table: Shock parameters of AT 2024wpp: "are not physical as the SED is free-free absorbed due to the surrounding medium up to radius"]
- limitation (authors): Cooling estimates depend strongly on assumed CSM density profile and shock velocity [6.1 Energy losses of synchrotron emitti…: "We caution that the above estimates based on cooling timescales depends strongly on the CSM density profile and shock velocities"]
- not stated (card): CASA version and the exact task/procedure used to measure ALMA flux densities (aperture or point-source fit, region, whether peak or integrated); Which archive pipeline products (MOUS/member OUS, continuum image, pipeline version) were used for each epoch; ALMA image rms, synthesized beams and spectral windows/bandwidth used for the 97.5 and 203 GHz images; Whether the quoted ALMA uncertainties i…

### 2019ApJ...884L..58U: First Detection of Radio Linear Polarization in a Gamma-Ray Burst Afterglow (2019; transients; observational_alma_primary)
- question: Is the millimeter-band linear polarization of the GRB 171205A afterglow detectable, and does its low degree imply Faraday depolarization by non-accelerated electrons?
- step 3: Model afterglow SED and light curve
  - method: Granot & Sari 2002 forward shock with jet-break factor [1+(t/t_j)]^-3/4 [Afterglow modeling: "we adopt the flux formula of (cite: 22) multiplied by the geometrical flux reduction factor $[1+(t/t_{j})]^{-3/4}$"]
  - assumption: ISM environment, slow cooling [Afterglow modeling: "Alternatively, we find that the ISM environment case can well fit it."]
  - validation: Computed X-ray light curve does not overwhelm the observed one [Afterglow modeling: "For these values we calculated X-ray light curve, which does not overwhelm the observed one."]
- limitation (authors): Non-simultaneous multi-wavelength polarimetry limits conclusions [Faraday depolarization effect: "Although the (semi-) simulataneous measurments in multiple wavelengths are required"]
- not stated (card): Weighting/robust, cell and image size; Mask used in CLEAN; Polarization calibration details and leakage handling; Target coordinates and ALMA array configuration; Fitting method for afterglow model and error treatment of P.A.; Time on source

### 2025ApJ...992L..18S: The First Radio-bright Off-nuclear Tidal Disruption Event AT 2024tvd Reveals the Fastest-evolving Double-peaked Radio Emission (2025; transients; multi_facility_alma_minor)
- question: How does the radio emission of the off-nuclear TDE AT 2024tvd evolve, and are its two radio flares explained by prompt or delayed, relativistic or non-relativistic outflow(s)?
- step 7: model host nucleus emission and subtract it from compact-configuration VLA data
  - method: Fit a power law to VLA A-configuration flux densities of the host nucleus (X band at 88 days, S, C and Ku bands at 160 days) and subtract it from C- and D-configuration TDE fluxes [Emission from the host galaxy nucleus: "We construct an SED of the host galaxy nucleus by taking flux measurements at two different epochs from VLA observations taken in A-configuration"]
  - validation: Correction is below 10% of the flux measurements [Emission from the host galaxy nucleus: "However, we note that this is a minor correction of less than $10\%$ of the flux measurements for these observations."]
- result: Host nucleus SED normalisation and index = A = 64 uJy at 5 GHz, beta = 0.53 ± A: 4 uJy; beta: 0.12 uJy; dimensionless [Emission from the host galaxy nucleus: "with $A = 64 \pm 4\, \rm \mu Jy$, and $\beta = 0.53 \pm 0.12$"]
- result: Host nucleus star formation rate from 1.4 GHz luminosity = 0.51 ± 0.06 Msun/yr [Emission from the host galaxy nucleus: "we infer an SFR of $0.51 \pm 0.06 \, \rm M_{\rm \odot} \, yr^{-1}$"]
- limitation (authors): Second flare is not modelled beyond equipartition [Multi-epoch time-dependent modeling of …: "We leave the modeling of the second radio flare beyond equipartition for future work."]
- limitation (authors): ALMA flux at Delta t = 227 days is too high relative to low-GHz data and cannot be accounted for [The nature of the second radio flare: "We note that the high-GHz emission observed with ALMA at $\Delta t = 227$ days is too high compared to the emission in low-GHz, and we cannot account for it in our equipartition analysis."]
- limitation (authors): ATA fluxes are contaminated by background due to the large beam [Allen Telescope Array: "The flux density measured by the ATA is contaminated by the background due to the large beam of the ATA."]
- not stated (card): Individual ALMA execution dates, array configurations and baselines for all four epochs (only Delta t of two epochs is given in the text); ALMA spectral setup details: continuum bandwidth, channelisation, integration time and sensitivity per epoch; ALMA project code to epoch mapping (which epochs belong to 2024.A.00024.T vs 2024.A.00034.T); Archive product identifiers and CASA/pipeline version of…

### 2019ApJ...878L..26L: ALMA Detection of a Linearly Polarized Reverse Shock in GRB 190114C (2019; transients; observational_alma_primary)
- question: Is the mm-band afterglow of GRB 190114C linearly polarized, and what does its polarization and temporal evolution imply about the reverse shock and jet magnetic field structure?
- step 4: Broadband SED and forward/reverse shock decomposition
  - method: Optical/X-ray spectral and temporal indices compared with synchrotron closure relations; radio/mm SED fit with broken power law; RS propagated back to match optical [4.2 Radio and millimeter: RS: "can be fit with a broken power law model, transitioning from $\beta=2$ (fixed) to $\beta=0.3\pm0.2$ at $\nu_{\rm break}=24\pm4$ GHz."]
  - assumption: Omega_m=0.31, Omega_Lambda=0.69, H0=68 km/s/Mpc [1 Introduction: "We assume $\Omega_m=0.31$, $\Omega_{\lambda}=0.69$, and $H_0=68$ km s$^{-1}$ Mpc$^{-1}$."]
- result: Radio SED break frequency = 24 ± ±4 GHz [4.2 Radio and millimeter: RS: "$\nu_{\rm break}=24\pm4$ GHz"]
- result: Mean intra-band Stokes I spectral index = ≈-0.4 ± not stated dimensionless [4.2 Radio and millimeter: RS: "the mean Stokes $I$ intra-band spectral index between the two ALMA base-bands at 91.5 GHz and 103.5 GHz is $\approx-0.4$"]
- limitation (authors): Systematic uncertainties from RS dynamics approximations and stochastic random walk; forward-shock parameters degenerate since nu_a not located [5 Discussion: "larger systematic uncertainties arise from the approximations used in the RS dynamics as well as the stochastic nature of the 2D random walk."]
- not stated (card): tclean parameters (weighting, robust, cell, image size, masking) for the Stokes images; CASA version; Whether archive pipeline products or manual calibration were used as the base; Time-binning of scans for the Stokes I light curve; Forward-shock model fitting method and priors; how parameters were chosen; Flagging details; Polarization calibrator solution settings (solints)

### 2024NatAs...8..774B: JWST detection of a supernova associated with GRB 221009A without an r-process signature (2024; transients, star_formation; multi_facility_alma_minor)
- question: Is there a supernova associated with GRB 221009A, does it show r-process enrichment, and what is the host galaxy environment (JWST NIRSpec/NIRCam; ALMA used to constrain the afterglow)?
- step 1: ALMA afterglow photometry
  - method: Point-source flux fit with imfit on pipeline-processed images at two epochs [5.4 ALMA Observations: "We performed photometry using `imfit` in the Common Astronomy Software Applications (CASA; (cite: CASA2022))"]
  - software: CASA
- result: ALMA 97.5 GHz flux density, epoch 1 (143.65 d) = 163 ± 22 uJy [5.4 ALMA Observations: "find a best-fit flux density in the two epochs of $(163\pm22)\,\mu$Jy and $(104\pm23)\,\mu$Jy"]
- result: ALMA 97.5 GHz flux density, epoch 2 (183.78 d) = 104 ± 23 uJy [5.4 ALMA Observations: "find a best-fit flux density in the two epochs of $(163\pm22)\,\mu$Jy and $(104\pm23)\,\mu$Jy"]
- limitation (authors): The afterglow/SN decomposition is uncertain and affects the Ni mass [2.2: "Of course, assuming a different afterglow contribution in our spectrum will affect the estimated mass."]
- not stated (card): ALMA CASA version and pipeline version; ALMA flux calibrator and imaging parameters (weighting, cell, size); imfit region and fitting details; ALMA array configuration, integration time, and beam

### 2018A&A...620A.119D: X-shooter and ALMA spectroscopy of GRB 161023A. A study of metals and molecules in the line of sight towards a luminous GRB (2018; transients, astrochemistry, high_z_galaxies; multi_facility_alma_minor)
- question: Use the GRB 161023A afterglow as a background source to study the host environment, molecular content (via ALMA mm spectroscopy) and intervening systems along the line of sight.
- step 1: Calibrate and image ALMA data, measure afterglow fluxes
  - method: Archive calibration script in CASA 4.7; images per spectral window; fluxes in Table 1 [2.4 ALMA observations: "subsequently images were produced by using the combined emission in each spectral window"]
  - software: CASA
- result: Band 3 spectral slope = +0.39 ± 0.13 dimensionless [3.1: "$\beta_{Band3} = +0.39\pm0.13$"]
- not stated (card): tclean parameters (cell, image size, masking, deconvolver) not given; Spectral rms and line width used to derive the 3.9 km/s optical-depth limit; How continuum was normalised for optical depth; Flux scale uncertainty; Line-free channels and continuum handling; Velocity width Delta V assumed for CO/HCO+ lines

## All papers in this technique

- 2012ApJ...761L..32W (2012): ALMA Submillimeter Continuum Imaging of the Host Galaxies of GRB 021004 and GRB 080607
- 2017ApJ...848L..21A (2017): The Electromagnetic Counterpart of the Binary Neutron Star Merger LIGO/Virgo GW170817. VI. Radio Constraints on a Relativistic Jet and Pred…
- 2017ApJ...850L..21K (2017): ALMA and GMRT Constraints on the Off-axis Gamma-Ray Burst 170817A from the Binary Neutron Star Merger GW170817
- 2017MNRAS.464.4624S (2017): GRB 110715A: the peculiar multiwavelength evolution of the first afterglow detected by ALMA
- 2017MNRAS.465L..89P (2017): A revised host galaxy association for GRB 020819B: a high-redshift dusty starburst, not a low-redshift gas-poor spiral
- 2017PASJ...69...20H (2017): ALMA and RATIR observations of GRB 131030A
- 2018A&A...620A.119D (2018): X-shooter and ALMA spectroscopy of GRB 161023A. A study of metals and molecules in the line of sight towards a luminous GRB
- 2018ApJ...862...94L (2018): First ALMA Light Curve Constrains Refreshed Reverse Shocks and Jet Magnetization in GRB 161219B
- 2019ApJ...870...59S (2019): ALMA, ATCA, and Spitzer Observations of the Luminous Extragalactic Supernova SN 1978K
- 2019ApJ...878L..26L (2019): ALMA Detection of a Linearly Polarized Reverse Shock in GRB 190114C
- 2019ApJ...884L..58U (2019): First Detection of Radio Linear Polarization in a Gamma-Ray Burst Afterglow
- 2019MNRAS.488.5029H (2019): Star-formation rates of two GRB host galaxies at z ∼ 2 and a [C II] deficit observed with ALMA
- 2019Natur.575..459M (2019): Observation of inverse Compton emission from a long γ-ray burst
- 2020ApJ...899..165A (2020): Local Starburst Conditions and Formation of GRB 980425/SN 1998bw within a Collisional Ring
- 2020MNRAS.496.4405H (2020): Far-infrared star formation rates of six GRB host galaxies with ALMA
- 2021A&A...650A.117N (2021): The host galaxy of the short GRB 050709
- 2021ApJ...909...11J (2021): 25 au Angular Resolution Observations of HH 211 with ALMA: Jet Properties and Shock Structures in SiO, CO, and SO
- 2021ApJ...912...21E (2021): Late-time Radio and Millimeter Observations of Superluminous Supernovae and Long Gamma-Ray Bursts: Implications for Central Engines, Fast R…
- 2021ApJ...915...46C (2021): ALMA Host Galaxy Observation of the Off-axis Gamma-Ray Burst XRF 020903
- 2022MNRAS.512.2337D (2022): The early afterglow of GRB 190829A
- 2023NatAs...7...80U (2023): Simultaneous radio and optical polarimetry of GRB 191221B afterglow
- 2024A&A...688A...8W (2024): The accretion burst of the massive young stellar object G323.46‒0.08
- 2024ApJ...969..122Y (2024): ALMA Reveals Spatially Resolved Properties of Molecular Gas in the Host Galaxy of FRB 20191001A at z = 0.2340
- 2024ApJ...974...18C (2024): The Peculiar Radio Evolution of the Tidal Disruption Event ASASSN-19bt
- 2024ApJ...974..279D (2024): A Millimeter Rebrightening in GRB 210702A
- 2024NatAs...8..774B (2024): JWST detection of a supernova associated with GRB 221009A without an r-process signature
- 2025A&A...701A.191V (2025): Observing radio transients with Phased ALMA: Pulses from the Galactic Centre magnetar
- 2025ApJ...985..124L (2025): The Nature of Optical Afterglows without Gamma-Ray Bursts: Identification of AT2023lcr and Multiwavelength Modeling
- 2025ApJ...987L...2H (2025): Dissecting the Massive Pristine, Neutral Gas Reservoir of a Remarkably Bright Galaxy at z = 14.179
- 2025ApJ...992L..18S (2025): The First Radio-bright Off-nuclear Tidal Disruption Event AT 2024tvd Reveals the Fastest-evolving Double-peaked Radio Emission
- 2025ApJ...993L...6N (2025): The Most Luminous Known Fast Blue Optical Transient AT 2024wpp: Unprecedented Evolution and Properties in the X-Rays and Radio
- 2026A&A...706A.174A (2026): Hiding behind a curtain of dust: Gas and dust properties of an ultra-luminous strongly-lensed z = 3.75 galaxy behind the Milky Way disc
- 2026ApJ...998..111C (2026): Continued Rapid Radio Brightening of the Tidal Disruption Event AT2018hyz
- 2026ApJ..1000..159M (2026): Low Dust Mass and High Star Formation Efficiency at z &gt; 12 from Deep ALMA Observations
- 2026MNRAS.550g1193B (2026): GOTO identification and broad-band modelling of the counterpart to the SVOM GRB 250818B
