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

=== SKILL.md (gas-mass-co-conversion) ===
---
name: alma-gas-mass-co-conversion
description: "Turn ALMA CO, [CI], 13CO or dust-continuum measurements into molecular gas masses, surface densities, gas fractions and depletion times, choosing the excitation correction (r_J1), conversion factor (alpha_CO / X_CO, X_CI, CO/H2 abundance) and helium convention the way published ALMA papers do. Use when converting a line flux to L' and M_H2, picking alpha_CO for a galaxy, nucleus, outflow or low-metallicity region, converting mid-J CO to CO(1-0), using [CI] or the Rayleigh-Jeans dust continuum as a gas tracer, stating gas-mass limits for non-detections, or checking someone else's gas mass. Built from 360 ALMA papers (2012-2026)."
---

# Molecular gas masses from CO, [CI] or dust

Converts a line (or continuum) measurement into H2 or total molecular mass:
M_mol = alpha x L'_CO(1-0), with L'_CO(1-0) = L'_CO(J-J-1) / r_J1. Two assumed numbers carry nearly all
of the uncertainty: the conversion factor (alpha_CO, X_CO, X_CI or CO/H2) and, for J>1, the excitation ratio
r_J1. The mistakes that matter most: (1) mixing conventions (alpha_CO with or without helium, alpha_CO for
CO(1-0) applied to CO(2-1), a flux-density ratio used where a brightness-temperature ratio is needed), each a
factor 1.36 to 4 error; (2) using a Galactic alpha_CO where it does not apply (starbursts, nuclei, outflows,
low metallicity), which papers themselves say moves masses by a factor 5 to 10 (2016A&A...594A..81P,
2017A&A...606A..17M, 2019ApJ...879...75H, 2015MNRAS.448.2224C).

> Always report: the line and flux used, r_J1 (and that it is a brightness-temperature ratio), alpha_CO with
> units and whether it includes helium (x1.36), the distance/cosmology, magnification if lensed, and the
> recovered-flux fraction. A gas mass without these is not reproducible.

## When to use

- A detected CO line (any J) in a galaxy, nucleus, cluster BCG, quasar host or GMC and you need L', M_H2,
  Sigma_H2, f_gas or t_dep (e.g. 2018ApJ...865...13T, 2019ApJ...887...74F, 2025ApJ...985..194P).
- Only a mid-J line (CO 3-2 to 7-6) is available at high z and you must correct to CO(1-0)
  (2018Natur.556..469M, 2024A&A...691A.178B, 2020A&A...636A..37D).
- [CI](1-0) or [CI](2-1) as an independent H2 tracer, or to calibrate alpha_CO (2017MNRAS.466.2825B,
  2018ApJ...863..143C, 2021A&A...645A.120F, 2024ApJ...977..198L).
- Rayleigh-Jeans dust continuum as a gas-mass proxy for faint or high-z sources (2014ApJ...783...84S,
  2017A&A...606A..17M, 2026ApJ..1001..131C).
- Non-detections: an n-sigma line-flux limit turned into a gas-mass limit (2019PASJ...71...40T,
  2024ApJ...977..198L, 2020ApJ...897L..19M).
- Measuring alpha_CO itself from dust, dynamics, [CI], 13CO or LVG modelling (2024ApJ...964...18C,
  2015ApJ...812L..23S, 2017ApJ...848..101V, 2026ApJ..1003..231W).

## When not to use

| Situation | Use instead |
|---|---|
| Protoplanetary disk gas mass | Thermochemical or RT disk models (DALI 2, RADMC-3D 5 papers in pack aggregates); CO/H2 = 1e-4 is a lower-limit assumption since CO depletion raises masses (2016ApJ...828...46A); pressure-broadened line wings in 2025ApJ...984L..19Y |
| Protostellar or AGB outflow / shell mass from 12CO | Column-density route with Tex and CO/H2 abundance (2021A&A...648A..41V, 2024ApJ...961..228S, 2018MNRAS.481.4931E); treat as lower limits |
| Optically thick 12CO where 13CO/C18O are detected | LTE isotopologue column density (2017ApJ...848..101V, 2024ApJ...964..166K, 2015ApJ...798...85P) |
| Excitation, density, temperature of the gas | Non-LTE modelling: RADEX (10 papers), MOLPOP-CEP, DESPOTIC, myRadex, or PDR Toolbox / 3d-pdr / Cloudy for [CI] and [CII] |
| Dense-gas mass | HCN with alpha_HCN about 10 (2015ApJ...815..103B, 2018ApJ...858...90G; range 6-40 in 2019ApJS..241...19I) |
| Dust mass itself | the dust-continuum-mass skill; this skill only uses dust as a gas proxy |

## Steps

1. **Measure a clean line flux S dv (Jy km/s).**
   - Primary-beam-corrected cube; spectrum from an aperture enclosing all >=3 sigma emission
     (2018ApJ...865...13T polygon aperture, 2024ApJ...963....1O elliptical aperture).
   - Fit Gaussians (PySpecKit in 2018ApJ...865...13T and 2024ApJ...963....1O; LMFIT with tied redshift and
     width across lines in 2020ApJ...902..109B; up to four tied Gaussians per box in 2018ApJ...863..143C) and
     check against direct channel summation (within 1.4 x FWHM in 2020ApJ...902..109B; 20 and 40 km/s
     binning in 2018ApJ...865...13T).
   - Compare with single-dish flux. Recovered fractions in the pack: 43% (2016ApJ...832..148V), about 20%
     of APEX mass (2017A&A...608A..98S), 40-50% missing (2021A&A...656A..60A, which corrected masses for
     45%), about half (2012A&A...538L...9H, 2017ApJ...843..136E). If you cannot correct, call the mass a
     lower limit (2017ApJ...837...60B).
   - Non-detection: 3 sigma limit = 3 x rms_channel x sqrt(dv_channel x FWHM) (2024ApJ...977..198L) with an
     assumed width taken from another line (2017MNRAS.466.2825B used the sample mean, 410 km/s;
     2019PASJ...71...40T used 5 sigma and 400 km/s).
2. **Compute the line luminosity** (general practice, Solomon and Vanden Bout form, used e.g. by
   2019ApJ...887...74F and 2025ApJ...985..194P):

   ```
   L'_line [K km/s pc^2] = 3.25e7 * S dv [Jy km/s] * nu_obs^-2 [GHz] * D_L^2 [Mpc] * (1+z)^-3
   L'_CO(1-0)            = L'_CO(J-J-1) / r_J1          # r_J1 = brightness-temperature ratio
   M_mol                 = alpha_CO * L'_CO(1-0)        # alpha_CO in Msun (K km/s pc^2)^-1
   ```

   For nearby sources the equivalent L_CO = 2453 S dv D^2 is used (2019BAAA...61..134V), and the
   X_CO form M_mol = 1.05e4 (X_CO/2e20) (1+z)^-1 S dv D_L^2 for CO(1-0) (2014ApJ...784...78R; general
   Bolatto et al. form). Divide by the magnification for lensed sources (2017MNRAS.466.2825B).
3. **Correct to CO(1-0)** with r_J1 (Parameter table). Prefer a measured ratio in the same aperture
   (2018ApJ...863..143C measured r21 per component; 2020ApJ...889....9M per region). Otherwise adopt a
   population ratio and say so (2024A&A...691A.178B used AGN-specific r21=0.68, r31=0.59, r41=0.37 and a
   different set for the control sample).
4. **Choose alpha_CO** (Parameter table): Galactic value for metal-rich disks, ULIRG value for mergers and
   compact starbursts, a metallicity-dependent prescription when Z is known to be low, and an explicit
   range for outflows. Decide helium once: alpha_CO = 4.3-4.4 includes the 1.36 factor (2020MNRAS.495.3840M,
   2020MNRAS.499..193K, 2024MNRAS.527.9343L); X_CO = 2e20 does not, and papers add 1.36 explicitly (2018ApJ...853..149S,
   2021A&A...652A..98G). 2017ApJ...848L...7C deliberately uses 3.2 without helium.
5. **Cross-check with a second tracer if you have one.**
   - [CI](1-0), optically thin LTE (general Papadopoulos and Greve form):
     `M_H2 = 1375.8 D_L^2 (1+z)^-1 (X_CI/1e-5)^-1 (A10/1e-7)^-1 Q10^-1 S_CI dv` with A10 = 7.93e-8 s^-1,
     X_CI = 3e-5 and Tex = 30 K as the usual choices (2017MNRAS.466.2825B, 2018ApJ...863..143C,
     2021A&A...645A.120F). Q10(30 K) is about 0.46 (2024ApJ...977..198L uses 0.457 at 29.1 K).
   - Dust RJ continuum: M_mol = L_nu(850 um rest) / alpha_850, alpha_850 = 6.7e19 erg/s/Hz/Msun calibrated
     at Td = 25 K, beta = 1.8 (2017A&A...606A..17M, 2024ApJ...977..251H, 2019MNRAS.482.3135B); apply a
     temperature correction when Td differs (2026ApJ..1001..131C). This calibration carries a Galactic
     alpha_CO = 6.5 (2017A&A...602L...9M), so compare like with like.
   - 13CO LTE: N(13CO) from Tex (from optically thick 12CO) and tau, then H2/13CO = 1.4e6 to 5e6
     (2024ApJ...964..166K, 2016ApJ...831...32N, 2024ApJ...966...51G); alpha_CO = M_LTE / L'_CO(1-0)
     (2017ApJ...848..101V got 2.26).
6. **Derive the quantities you need.** Sigma_H2 with a cos i deprojection (2025ApJ...995..151Y); in nearby
   disks Sigma_H2 = 4.2 I_CO(1-0) with helium (2019A&A...623A..66B). f_gas = M_gas/(M_gas+M*)
   (2019ApJ...887...74F, 2015ApJ...812L..23S, 2025ApJ...985..194P); t_dep = M_gas/SFR (2014ApJ...783...84S).
   Add H I where needed: H2/HI = 0.3 (2020ApJ...889....9M), HI = 50% of H2 (2014ApJ...783...84S).
7. **Write the error budget.** Statistical flux error plus flux-calibration error in quadrature (10% in
   2016ApJ...828...46A and 2024ApJ...964..166K; 5% in 2025ApJ...988..162D, 2025ApJ...990..221M; 30%
   conservative for ACA Band 8 in 2020ApJ...897L..19M), then the systematic alpha_CO and r_J1 terms stated
   separately (0.3 dex added on M_mol in 2018ApJ...853..195W; 50% in 2019Natur.569..519K and
   2025A&A...698A.296R; +/-0.20 dex in 2021A&A...652A..98G).

## Parameter defaults and ranges

Counts are my own regex count over the pack's "Key parameters" and "Assumptions" lines (345 of the 360
papers appear there), after dropping clearly off-topic hits (for example an X-ray binary jet paper and a
regex false match on "z=4.3"). They are approximate lower bounds: a paper that
states its alpha_CO only in prose outside those lines is not counted. Longer per-population lists are in
`references/parameters.md`.

| Parameter | Common choice | Range seen | Papers (count) | Examples |
|---|---|---|---|---|
| alpha_CO, Galactic (incl. He) | 4.3-4.4 | 4.3, 4.35, 4.36, 4.4 used interchangeably | about 60 | 2017ApJ...835..278S, 2021A&A...656A..60A, 2020MNRAS.495.3840M, 2025ApJ...990..221M |
| X_CO, Galactic (no He) | 2e20 cm^-2 (K km/s)^-1 | 1.8e20 to 4e20 | about 38 at 2e20 | 2014ApJ...784...78R, 2018ApJ...865...13T, 2024ApJ...963....1O; 3e20: 2020MNRAS.496.4061D; 4e20: 2017ApJ...843..136E |
| alpha_CO, ULIRG / merger / starburst | 0.8 | 0.6 to 1.5 | about 39 at 0.8 | 2017ApJ...843...18V, 2018Natur.556..469M, 2019ApJ...887...74F, 2024ApJ...977..198L; 1.0: 2018Natur.553...51M; 1.1: 2015ApJ...812L..23S |
| alpha_CO, z>1 main sequence | 3.6 | 3.6 to 4.6 | 11 at 3.6; 12 at 4.6 | 3.6: 2019ApJ...882..137P, 2020ApJ...902..109B, 2024A&A...691A.178B; 4.6: 2014ApJ...783...84S, 2020MNRAS.497.2771M |
| alpha_CO, Scoville convention | 6.5 (from X_CO = 3e20 with He) | | 8 | 2016ApJ...820...83S, 2017A&A...606A..17M, 2018ApJ...860..111D |
| alpha_CO, low metallicity | scale with Z | 8 to 110 (CO 2-1 at 110) | about 25 mention metallicity | 4.35 Z'^-1.6 (2021A&A...656A.133Q, 2025A&A...698A.296R); 4.35 (Z/Zsun)^-1 (2019Natur.569..519K); 17 at 12+log(O/H)=8.3 (2025A&A...700A.165B); 110 +/- 30 (2017ApJ...835..278S) |
| alpha_CO, outflows | 0.8, with optically thin 0.3-0.34 as lower bound | 0.25 to 3.4 | (see examples) | 2015A&A...580A...1M, 2018ApJ...863..143C (measured 2.1 +/- 1.2), 2019MNRAS.489.1927S, 2017A&A...608A..38O |
| r21 = T_b(2-1)/T_b(1-0) | 0.7-0.8 | 0.6 to 1.0 (super-thermal 1.1-1.4 in outflows) | about 65 state a 2-1/1-0 ratio | 0.7: 2018ApJ...860..172S, 2018ApJ...861L..18U; 0.8: 2021ApJ...908...54W, 2017MNRAS.466.2825B; 1: 2017ApJ...835..278S; 1.4 (outflow): 2018ApJ...863..143C |
| r31 | 0.5-0.8 | 0.27 to 1 | about 39 state an r_J1 for J>=3 | 0.8: 2019ApJ...887...74F, 2024ApJ...963....1O; 0.66: 2016NatAs...1E...3P; 0.42: 2019ApJ...882..136A; 0.27: 2021A&A...656A..60A |
| r41, r43 | 0.4-0.45 (r41) | 0.31 to 0.91 | (see examples) | r41 0.41: 2018Natur.556..469M, 2018PASJ...70L...6K; 0.87 (QSO): 2024ApJ...977..198L; r43 0.91 and 0.46: 2019MNRAS.487.4305S |
| r51 to r76 | SLED of a comparison population | r54 0.28; r51 0.23 (MS) to 0.6 (SB); r76 0.16 (SMG) to 0.48 (QSO) | (see examples) | 2018MNRAS.477.4380S, 2017MNRAS.469.4683C, 2020A&A...636A..37D |
| X_CI = [CI]/H2 | 3e-5 | 1e-5 to 8.4e-5 | 8 at 3e-5 | 2017MNRAS.466.2825B, 2018ApJ...863..143C, 2021A&A...645A.120F; 1.5e-5: 2021ApJ...908..163M; 8.4e-5: 2024ApJ...977..198L |
| Tex for [CI] | 30 K | 15 to 40 K | (see examples) | 2017MNRAS.466.2825B, 2020ApJ...902..109B, 2019ApJ...887..144J; 29.1 K: 2024ApJ...977..198L |
| Q10 | 0.48-0.6 | 0.35 to 0.6 | (see examples) | 0.48: 2021A&A...645A.120F; 0.5: 2018ApJ...866L..12G; 0.6: 2017MNRAS.466.2825B; 0.35: 2019MNRAS.482.3135B |
| alpha_[CI] | 7.3-9.4 | | 2 | 2020ApJ...897L..19M, 2018ApJ...863..143C |
| CO/H2 abundance (Galactic sources, disks) | 1e-4 | 1.6e-5 (LMC) to 7e-4 | about 22 | 2021A&A...648A..41V, 2017ApJ...846L..26W; 2e-4: 2021A&A...646A...1K; 1.6e-5: 2019PASJ...71...44H |
| Helium / mean mass | x1.36 | 1.36 to 1.41 per H2 mass; mu 2.37 to 2.8 per particle | about 29 state it | 1.36: 2018ApJ...853..149S, 2021ApJ...908..163M; 1.41: 2016ApJ...823...68S; mu 2.8: 2024ApJ...961..228S |
| alpha_850 (dust RJ) | 6.7e19 erg/s/Hz/Msun | 0.79e20 to 1.0e20 in the original calibration | 6 | 2017A&A...606A..17M, 2017ApJ...844..123F, 2014ApJ...783...84S |
| Line-detection threshold | 3 sigma | 3 to 5 sigma | (see examples) | 2020ApJ...902..109B, 2024ApJ...977..198L; 5 sigma: 2019PASJ...71...40T |

## Software

From the pack aggregates (software named in matched steps of all 360 papers). The conversion itself is
nearly always custom code; the packages below do flux extraction, excitation modelling or cloud catalogues.

| Tool | Papers | What it is used for |
|---|---|---|
| CASA (+ imfit, immoments) | 25 (+1, +1) | imaging, moment maps, flux extraction |
| RADEX (+ myRadex) | 10 (+1) | non-LTE excitation, Tex, tau, N(CO); e.g. outflow streamer densities (2017ApJ...837...60B), dark-gas X_CO (2020ApJ...889L...4L) |
| emcee | 9 | MCMC for line-ratio, disk and regression fits (2024A&A...691A.178B) |
| RADMC-3D, DALI | 5, 2 | disk models where a gas mass is a model parameter (2018ApJ...854..130W) |
| MAGPHYS | 4 | stellar masses and SFRs for f_gas and t_dep |
| 3DBarolo, KinMS, GALMOD | 4, 2, 1 | dynamical masses used to bound alpha_CO (2018MNRAS.479.5440L) |
| CPROPS / cprops / cpropstoo, astrodendro | 3+1+1, 2 | cloud decomposition before per-cloud luminous masses (2017ApJ...835..278S) |
| PDR Toolbox, 3d-pdr, Cloudy, DESPOTIC | 2, 1, 2 (+1 as CLOUDY), 2 | [CI]/CO/[CII] ratios to density and UV field (2020ApJ...902..109B, 2017MNRAS.466.2825B) |
| LMFIT, PySpecKit | 2, 1 (+1 as pyspeckit) | Gaussian line fits |
| linmix_err | 1 | censored Bayesian regression of alpha_CO trends (2018ApJ...863..143C) |
| MIRIAD, GILDAS | 3, 1 | imaging outside CASA |

## Pitfalls

- **Helium double counting.** 4.35 already includes 1.36; X_CO = 2e20 does not. Check each literature
  value: 2016NatSR...626896A excludes helium, 2017ApJ...848L...7C uses 3.2 without helium,
  2020ApJ...902..109B divides M_mol by 1.36 to get M_H2.
- **alpha_CO per transition.** alpha_CO(2-1) = alpha_CO(1-0)/r21: 4.35, 6.25 and 17.4 for 1-0, 2-1, 3-2 in
  2018ApJ...860..172S; 6.2 for 2-1 in 2018ApJ...868L..38G; 9.3 vs 4.2 measured in 2024ApJ...964...18C.
  Never apply a (1-0) factor to an uncorrected higher-J luminosity.
- **Flux ratio vs brightness ratio.** Several cards quote CO(2-1)/CO(1-0) of about 3 (2018ApJ...865...13T,
  2019ApJ...887..149B, 2020A&A...641A.151S) or 3-2/1-0 of 9 (2017A&A...602A..11P): these are flux-density
  ratios, which equal r_J1 x (nu_J/nu_1)^2 (general). Using them as r_J1 inflates L'_CO(1-0) by 4 or 9.
- **Galactic alpha_CO in starbursts or nuclei.** Factor ~5 (2016A&A...594A..81P), >~8 (2017A&A...606A..17M),
  5.5 (2019ApJ...879...75H), up to 10 (2015MNRAS.448.2224C). Nuclear values of 1/4 Galactic in
  2014A&A...567A.125G and 2019A&A...632A..33A.
- **Mid-J only.** A single mid-J line gives a highly uncertain mass (2016ApJ...827...34O); SLED-shape
  uncertainty is often left out of quoted errors (2017ApJ...845..154V); factor 2 in 2016ApJ...819...82S and
  2017ApJ...846L..14S.
- **Missing short spacings.** Interferometric masses can be well below single-dish (Step 1); conversely
  2014ApJS..214....1U found interferometric masses sometimes above single-dish, so check both ways.
- **CMB at high z.** Not correcting can bias masses low by about 2x (2018ApJ...856...72O); half the intrinsic
  flux missed in 2017MNRAS.466..138K; estimated <~15% and ignored in 2019ApJ...882..138D. State which.
- **Low metallicity and CO-dark gas.** CO misses H2 at low Z; 2016A&A...586A..45S applies a CO-dark
  correction; dark-gas X_CO of 14e20 in 2020ApJ...889L...4L. The metallicity of the ionised gas may not be
  that of the molecular gas (2015ApJ...812L..23S), or is unknown at the ALMA position (2016A&A...586A..45S).
- **[CI] assumptions.** Masses scale as 1/X_CI and depend on Tex through Q10; 2021A&A...645A.120F notes its
  errors exclude X_CI, Q10 and A10; 2020ApJ...897L..19M found [CI] an order of magnitude below the
  CO relation. [CI] can be optically thick (tau about 10 in 2019ApJ...885L..39H).
- **Lensing.** Differential magnification can change line ratios (2016A&A...586L...7B); a single
  magnification is a simplification (2016ApJ...822...80S).
- **Optically thin limits.** Treating 12CO as thin gives lower masses by about an order of magnitude
  (2014ApJ...797...90S); a single thick line underestimates disk mass (2017ApJ...846L..26W).
- **Unstated settings** most often flagged by the cards: CASA version (24), line-free channels and continuum
  subtraction (20, plus 12 + 12 under other wordings), CASA and pipeline version (14), flux calibrator and
  flux-scale uncertainty (14), PB correction (7 + 7). The cards rarely state whether alpha_CO includes
  helium or which aperture the r_J1 was measured in.

## Verification checks

What the papers did:

- **Single-dish flux comparison** (2018ApJ...863..143C consistent; 2021A&A...656A..60A 40-50% missing).
- **Independent tracers agree**: three tracers ([CI], CO(4-3), dust) in 2024ApJ...977..198L; dust vs CO
  median 0.23 dex in 2021A&A...652A..98G; [CI] vs continuum within 2x in 2021A&A...645A.120F; LTE vs X_CO
  masses KS p = 0.52 in 2024ApJ...964..166K; C17O vs X_CO in 2015ApJ...801...63M; dust-based [CI] abundance
  matches CO-based in 2020ApJ...902..109B.
- **Dynamical ceiling**: gas mass plus stars below M_dyn (2015ApJ...812L..23S, 2018MNRAS.479.5440L;
  MH2 < Mdyn prior in 2019MNRAS.486.2366M).
- **Vary the assumptions** and report the spread: excitation corrections (2015ApJ...812L..23S), r43 0.91 and
  0.46 (2019MNRAS.487.4305S), r13 1 and 1.35 (2021A&A...656A..60A), alpha_CO 0.35 to 4.35
  (2025ApJ...992L...7S), D/M 0.1 to 1 (2024ApJ...964...18C).
- **Environment check for alpha_CO**: metallicity from the mass-metallicity relation and BPT
  (2015ApJ...812L..23S); Schmidt-Kennicutt placement (2014ApJ...784...78R).
- **Extraction robustness**: binning and weighting (2024ApJ...963....1O found 0.88-2.5 Jy km/s with natural
  weighting depending on binning, so state your choice); fit vs direct sum (2020ApJ...902..109B).
- **Gas-to-dust sanity**: 944 +/- 77 in 2019ApJ...887...74F and about 30 with alpha_CO = 0.8 vs about 95 at
  solar in 2019ApJ...877L..38R show how alpha_CO choices surface as odd gas-to-dust ratios.

What a careful referee adds:

- Recompute L' and M from the quoted S dv, nu_obs, D_L, z, r_J1 and alpha_CO; check units and helium.
- Confirm r_J1 is a brightness-temperature ratio measured in matched apertures and uv coverage
  (2015ApJ...815..103B and 2016ApJ...821..112K warn that different uv coverage biases line ratios).
- Ask for masses at both Galactic and ULIRG alpha_CO when the environment is ambiguous
  (2014ApJ...787...48X, 2018Sci...362.1034D quote both).
- Check that limits use the same width, r_J1 and alpha_CO as detections.

## Source cards

Full list with titles: `references/sources.md`. Most informative for this technique:

- 2018ApJ...863..143C: [CI] + CO(1-0) alpha_CO for outflow and quiescent gas, per-box decomposition.
- 2017MNRAS.466.2825B: [CI](1-0) H2 masses at z~4, implied alpha_CO = 2.0 +/- 1.0.
- 2024ApJ...964...18C: resolved dust-based alpha_CO in 37 galaxies, Sigma_star dependence.
- 2017ApJ...835..278S: low-metallicity alpha_CO from dust in NGC 6822, CPROPS clumps.
- 2017ApJ...848..101V: 13CO LTE mass and alpha_CO in a BCG.
- 2015ApJ...812L..23S: alpha_CO from dynamical masses at z~1.6.
- 2020ApJ...902..109B: ASPECS CO SLEDs and [CI] abundances.
- 2024ApJ...977..198L: three-tracer gas masses and CGM [CI].
- 2021A&A...645A.120F: [CI] mass with continuum cross-check.
- 2021A&A...652A..98G: dust vs CO masses in Seyfert tori.
- 2014ApJ...783...84S: alpha_850 RJ dust calibration.
- 2024ApJ...964..166K: LTE vs X_CO masses in the Antennae.
- 2018ApJ...860..172S: alpha_CO per transition.
- 2014A&A...567A.125G: dust-matched X_CO in NGC 1068 nucleus.
- 2021A&A...656A..60A: missing-flux correction of nuclear masses.
- 2025ApJ...985..194P: stacked CO(2-1), metallicity-dependent alpha_CO.
- 2024A&A...691A.178B: AGN-specific r_J1 and censored fits.
- 2018ApJ...865...13T: aperture Gaussian fit, X_CO form, binning check.
- 2017ApJ...843...18V: outflow mass with ULIRG alpha_CO.
- 2020ApJ...897L..19M: [CI]-faint galaxy, [CI] limit vs CO mass.
- 2025ApJ...984L..19Y: disk surface density scaling with X_CO.

=== references/parameters.md ===
# Parameter lists for gas-mass conversion (from the gas-mass-co-conversion pack)

Every value below is taken from the pack's "Key parameters", "Assumptions" or excerpt lines, with the paper
that used it. Units: alpha in Msun (K km/s pc^2)^-1, X_CO in cm^-2 (K km/s)^-1.

## alpha_CO / X_CO by environment

| Environment | Values used | Papers |
|---|---|---|
| Milky Way, with helium | 4.3 | 2016ApJ...820L..39N, 2017ApJ...851...18L, 2018ApJ...854...83T, 2019BAAA...61..134V, 2025A&A...701A.113M |
| | 4.35 / 4.36 | 2013ApJ...769L..12L, 2017ApJ...835..278S, 2018ApJ...861L..18U, 2021A&A...656A..60A, 2025ApJ...990..221M, 2026A&A...705A.163H |
| | 4.4 | 2018ApJ...860..103S, 2020MNRAS.494.2131F, 2020MNRAS.495.3840M, 2021ApJ...908...54W |
| | 4.6 | 2014ApJ...783...84S, 2018MNRAS.478.3120A, 2019MNRAS.485.1595P, 2021AN....342.1160P |
| Milky Way, X_CO form | 2e20 | 2014ApJ...784...78R, 2018ApJ...865...13T, 2021A&A...652A..98G, 2024ApJ...963....1O (30% uncertainty), 2025ApJ...992..211N |
| | 1.8e20 to 2.8e20 | 2016ApJ...823...26E, 2016ApJ...831..161K, 2017ApJ...841...43E, 2016NatSR...626896A, 2019ApJ...870...39V |
| | 3e20 to 4.7e20 | 2012A&A...538L...9H, 2020MNRAS.496.4061D, 2017ApJ...843..136E, 2017ApJ...846...73T |
| Scoville convention (X_CO 3e20 with He) | 6.5 | 2016ApJ...820...83S, 2017A&A...606A..17M, 2018ApJ...860..111D, 2019ApJ...880...15K, 2020ApJ...901...79A |
| z>1 main-sequence galaxies | 3.6 | 2016ApJ...833...69D, 2019ApJ...882..137P, 2019ApJ...882..138D, 2020ApJ...902..109B, 2020ApJ...901..141K |
| Early-type / CO(1-0) with r21 0.7 | 3.1 | 2016ApJ...823...51B, 2017ApJ...845..170B, 2021ApJ...908..231M (0.3 dex), 2024ApJ...975..179C |
| ULIRG, merger, SMG, QSO host | 0.8 | 2014ApJ...787...48X, 2017ApJ...843...18V, 2018Natur.556..469M, 2019ApJ...881...63N, 2020MNRAS.493.3744F |
| | 0.86 (0.5 dex error) | 2014ApJ...790..160S |
| | 1.0 to 1.5 | 2018Natur.553...51M, 2018ApJ...861...43P, 2020ApJ...898...61I (1.3, 0.4 dex), 2019ApJS..241...19I (1.5 for CO 2-1) |
| Starburst X_CO | 0.4e20 to 0.8e20 | 2015ApJ...801...63M (0.5e20, factor 2), 2017ApJ...836..130R, 2018ApJ...856...97S, 2024ApJ...964..166K |
| Galaxy centres / nuclei | about 1/4 Galactic | 2014A&A...567A.125G (1/(4 +6 -1)), 2019A&A...632A..33A |
| Outflows | 0.8; thin 0.25 to 0.34 | 2015A&A...580A...1M, 2016ApJ...832..142Z, 2017A&A...608A..38O, 2021A&A...655A..25Z, 2020ApJ...890...29F |
| | measured 2.1 +/- 1.2 ([CI]) | 2018ApJ...863..143C; 2.1 (0.8-3.4) in 2019MNRAS.489.1927S |
| Low metallicity, prescriptions | 4.35 Z'^-1.6 | 2021A&A...656A.133Q, 2025A&A...698A.296R |
| | 4.35 (Z/Zsun)^-1 | 2019Natur.569..519K |
| | f_metal x 4.36 | 2019PASJ...71...40T (f_metal 1.1 at logM 11, 1.4 at 10.5) |
| | Genzel 2015, Accurso 2017, Tacconi 2018, Bolatto 2013 eq. 31 | 2024A&A...692A.215C, 2020ApJ...897L..30M, 2025ApJ...985..194P, 2024ApJ...976...88L |
| Low metallicity, values | 8.4 | 2025A&A...699A.369V |
| | about 10 at 0.5 Zsun | 2017MNRAS.468.3468G |
| | 17 at 12+log(O/H)=8.3 | 2025A&A...700A.165B |
| | about 18 at 0.3 Zsun | 2019ApJ...882....1L |
| | 85 to 110 (CO 2-1, dust-based) | 2017ApJ...835..278S |
| Diffuse / CO-dark gas | X_CO 14e20 | 2020ApJ...889L...4L |
| Per transition | (2-1) 6.2 to 6.7 | 2018ApJ...868L..38G, 2024PASA...41...76Z |
| | (3-2) 17.4 (Galactic, r31 0.25) | 2018ApJ...860..172S |
| | (3-2) 0.3-0.7 (LVG); 0.8 to 1 | 2026ApJ..1003..231W, 2024A&A...682A.182G, 2025ApJ...995..219F |

## Measured alpha_CO in the pack

| Method | Value | Paper |
|---|---|---|
| Dust (resolved, 37 galaxies) | (1-0) 4.2 +1.9/-2.0; (2-1) 9.3 +4.6/-5.4; slope -0.50 with Sigma_star for 2-1 | 2024ApJ...964...18C |
| Dust, dwarf galaxy | 85 to 110 for CO(2-1) | 2017ApJ...835..278S |
| Dust, AGN nucleus | about 1/4 Galactic | 2014A&A...567A.125G |
| [CI](1-0) | 2.0 +/- 1.0 at z~4 | 2017MNRAS.466.2825B |
| [CI](1-0), merger | 2.1 +/- 1.2 (outflow), 3.2 +/- 1.8 (systemic) | 2018ApJ...863..143C |
| Dynamics | 0.6 +/- 0.3 and 1.6 +/- 0.6 at z~1.6 | 2015ApJ...812L..23S |
| 13CO LTE | 2.26 (X_CO 1.04e20) | 2017ApJ...848..101V |
| LVG | (3-2) 0.3-0.7 | 2026ApJ..1003..231W |
| Statistical scatter | 0.165 dex | 2025A&A...700A.165B |

## Excitation ratios (brightness-temperature ratios unless noted)

| Ratio | Values and populations | Papers |
|---|---|---|
| r21 | 0.65 to 0.8 for nearby disks | 0.65: 2021A&A...656A.133Q, 2025ApJ...988..263Z; 0.7: 2018ApJ...857...19F, 2019A&A...623A..66B; 0.77-0.8: 2017ApJ...842L..21N, 2024ApJ...969..122Y, 2020MNRAS.494.2131F |
| | 0.9 to 1 (LIRG, thermalised) | 2019MNRAS.482L..65K, 2016A&A...594A..81P, 2019A&A...621A..83S, 2024ApJ...977...36B |
| | 1.12 to 1.4 (nuclei, outflows) | 2021A&A...656A..60A, 2018ApJ...863..143C |
| | flux-density ratios about 3 to 4 (not r21) | 2018ApJ...853..149S, 2019MNRAS.485..229R, 2019ApJ...887..149B, 2016A&A...595L...7D |
| r31 | 0.5 to 0.8 | 2024ApJ...963....1O, 2019ApJ...887...74F, 2016NatAs...1E...3P, 2018MNRAS.479.2126F, 2025ApJ...995L..63L |
| | 0.27 to 0.42 | 2021A&A...656A..60A, 2019ApJ...882..136A, 2021A&A...646A.127H |
| | 2.0 to 2.9 (AGN tori, stated as brightness ratios) | 2021A&A...652A..98G, 2019A&A...632A..61G |
| r41 | 0.41 (SMG), 0.46, 0.85-0.87 (QSO and companions) | 2018Natur.556..469M, 2024ApJ...977..251H, 2024ApJ...977..198L |
| r43 | 0.6, 0.91 (0.46 tested) | 2017A&A...604A.117C, 2019MNRAS.487.4305S |
| r51, r54 | 0.23 (MS), 0.6 (SB); 0.28 +/- 0.05; 0.39 | 2017MNRAS.469.4683C, 2018MNRAS.477.4380S, 2016ApJ...827...34O |
| r61, r71 | 0.34/0.64 and 0.16/0.48 (SMG/QSO); 0.24 | 2020A&A...636A..37D, 2020NatAs...4..670A |
| AGN vs non-AGN sets | AGN r21 0.68, r31 0.59, r41 0.37; control r21 0.6, r31 0.5 | 2024A&A...691A.178B |

## [CI] parameters

| Parameter | Values | Papers |
|---|---|---|
| X_CI | 3e-5 | 2016A&A...591A..73G, 2017MNRAS.466.2825B, 2018ApJ...866L..12G, 2019MNRAS.482.3135B, 2020A&A...641A.155V |
| | 1.5e-5; 1e-5 (CGM region); 8.4e-5 (QSO) | 2021ApJ...908..163M, 2021A&A...645A.120F, 2024ApJ...977..198L |
| | scaled linearly with metallicity | 2024A&A...685A.138V |
| Tex | 30 K; 29.1 K; 40 K (dust cross-check) | 2017MNRAS.466.2825B, 2024ApJ...977..198L, 2021A&A...645A.120F |
| Q10 | 0.35, 0.457, 0.48, 0.5, 0.6 | 2019MNRAS.482.3135B, 2024ApJ...977..198L, 2021A&A...645A.120F, 2021ApJ...908..163M, 2017MNRAS.466.2825B |
| A10 | 7.93e-8 s^-1 | 2017MNRAS.466.2825B, 2018ApJ...856...72O, 2021A&A...645A.120F |
| [CI](2-1) | Q21 0.57, A21 2.68e-7 s^-1; Q21 0.05-0.4 tested | 2016A&A...591A..73G, 2024A&A...685A.138V |
| Measured [CI]/H2 | 1.9e-5 +/- 0.4e-5 (CO-based), 2.2e-5 +/- 0.3e-5 (dust-based) | 2020ApJ...902..109B |

## CO abundance and isotopologue ratios (Galactic sources, disks)

| Quantity | Values | Papers |
|---|---|---|
| CO/H2 | 1e-4 | 2017A&A...600A..62P, 2018A&A...618A.120L, 2021A&A...648A..41V, 2024ApJ...963...72O |
| | 2e-4; 1e-3 (C-rich ejecta); 1.6e-5 (LMC); 5e-5 to 7e-4 (disks) | 2021A&A...646A...1K, 2018MNRAS.481.4931E, 2019PASJ...71...44H, 2025ApJ...994...98F, 2025ApJ...984L..19Y |
| 12CO/13CO | 50 to 77 | 2017ApJ...848..101V (50), 2016ApJ...828...46A (70), 2015ApJ...798...85P (76) |
| CO/C18O | 550 or 1650; 557; 570 +/- 130 | 2016ApJ...828...46A, 2025ApJ...994...98F, 2020MNRAS.496..394R |
| H2/13CO | 1.4e6 to 5e6 | 2024ApJ...964..166K, 2020ApJ...903...94M, 2024ApJ...966...51G, 2016ApJ...831...32N |
| mu per particle / per H2 | 2.37; 2.76 to 2.8 | 2017ApJ...846L..26W, 2021A&A...648A..41V, 2024ApJ...961..228S |

## Other gas tracers

| Tracer | Conversion | Papers |
|---|---|---|
| HCN | alpha_HCN about 10 (6 to 40; 0.24 to 10 in one AGN) | 2015ApJ...803...60S, 2018ApJ...858...90G, 2019ApJS..241...19I, 2018ApJ...868...95M |
| HCO+ | alpha_HCO+ about 10 | 2015ApJ...813..118M |
| [CII] | alpha_[CII] about 30 Msun/Lsun, 0.3 dex | 2020ApJ...905..147Y |
| Dust RJ | alpha_850 6.7e19 (Td 25 K, beta 1.8); 1.0e20 +/- 0.23e20 (local), 0.79e20 (Planck) | 2017A&A...606A..17M, 2014ApJ...783...84S |
| Dust with gas-to-dust | 100; stellar-mass dependent; 200 | 2021A&A...652A..98G, 2018ApJ...856..118H, 2016ApJ...833...68A |

=== EVIDENCE PACK (gas-mass-co-conversion) ===
# Evidence pack: Molecular gas masses from CO, [CI] or dust (alpha_CO, r_J1) (`gas-mass-co-conversion`)

Scope: CO/[CI] line luminosity to H2 mass, conversion factors, excitation corrections

Built from 360 non-held-out ALMA papers whose methods cards passed mechanical evidence verification (every quote below is verbatim from the paper). Years 2012-2026.
Matcher (regex over analysis steps): `alpha_?co|α_?co|co[- ]to[- ]h2|x_?co|\bl'?co\b|l'_?co|line luminosit|molecular gas mass|h2 mass|\[ci\]|\[c i\]|gas fraction|brightness temperature ratio|r_?21|r_?31|excitation ladder|\bsled\b`
Tagging is by regex, so a few papers may be off-topic: ignore those.

## Aggregates over all papers

### Science fields
- nearby_galaxies: 188
- high_z_galaxies: 143
- agn_and_quasars: 119
- star_formation: 83
- milky_way_ism: 53
- astrochemistry: 33
- galaxy_clusters_and_sz: 25
- protoplanetary_disks: 19
- cosmology: 6
- stellar_physics: 5
- transients: 4
- debris_disks: 3
- evolved_stars: 3
- exoplanets: 2
- other: 1

### Software named in the matched steps
- casa: 25
- radex: 10
- emcee: 9
- radmc-3d: 5
- cprops: 4
- 3dbarolo: 4
- magphys: 4
- cloudy: 3
- miriad: 3
- scipy: 2
- lmfit: 2
- pdrtoolbox: 2
- pyspeckit: 2
- molpop-cep: 2
- kinms: 2
- dali: 2
- despotic: 2
- astrodendro: 2
- photutils: 2
- pdr toolbox: 2
- linmix_err.pro: 1
- 3d-pdr: 1
- papanda: 1
- pdrt: 1
- photodissociation region toolbox: 1
- galmod: 1
- xspec: 1
- starburst99: 1
- diskfit: 1
- monte-carlo bees algorithm: 1
- pystacker: 1
- pystructure: 1
- jam: 1
- mgefit: 1
- pyradex: 1
- radex_emcee: 1
- lee et al. 2014 radiative transfer code: 1
- sofia-2: 1
- michi2: 1
- tirific: 1

### Fitting methods (most common phrasings)
- Simultaneous Gaussian fit; sampler/priors not stated: 1
- Up to four tied Gaussians per box, minimal number of components: 1
- linmix_err.pro (Kelly 2007); priors not stated: 1
- Peak of probability distribution over the grid: 1
- Non-linear least squares, b free or fixed 0.5: 1
- non-linear least squares: 1
- median and 68% interval of bootstrap solutions: 1
- Gaussian profile fit: 1
- single Gaussian per spectrum (two for 12CO in the 13CO-tracing region): 1
- emcee with uniform priors for all parameters: 1
- Uniform priors; 2000 steps x 32 walkers, then re-initialized 6000-step run discarding first 3000; median adopted: 1
- emcee ensemble MCMC, scipy.optimize initial guess, median and 16/84 percentiles: 1
- Maximum likelihood and MCMC; details not stated: 1
- four-component Gaussian, -690 to 900 km/s; sampler/priors not stated: 1
- weighted least squares log10 y = a log10 x + b: 1
- Power-law fits to clumps: 1
- chi2 minimization; errors by re-running with one variable free: 1
- Errorbars from 1000 bootstraps: 1
- Uncertainties from 1000 bootstrap resamplings of galaxies: 1
- non-linear least squares; 1σ from variance of parameter estimates: 1
- chi-square fitting with simultaneous fits and tied parameters: 1
- Gaussian fit; same integral with 20/40 km/s binning and direct summation: 1
- emcee affine-invariant sampler; simple physical priors (vturb>0); linear spacing except log Rc: 1
- chi2 grid: 1
- Grid chi2 plus Bayesian likelihood with flat priors and cutoffs: 1
- Gaussian fits: 1
- Gaussian line fits; CO(7-6) and [CI](2-1) line width fixed to mean of unblended lines: 1
- Bees algorithm with chi2 evaluation; probability-weighted mean and standard deviation of solutions: 1
- Linear regression y = m x + q to binned values; no sampler or priors stated: 1
- MCMC; flat priors; chi2_red=1.23 over 920 dof: 1
- Gaussians; OH doublet amplitudes equal and width fixed to [C II]: 1
- Solved Tex and tau from brightness temperature ratio; errors from noise propagation, 10% flux uncertainty at high S/N: 1
- chi2 minimisation of double Gaussian; 1sigma from 15.865 and 84.135 percentiles: 1
- emcee, uniform priors, 128 CPUs, few days: 1
- least squares: 1
- Gaussian components, 6 fitted: 1
- Levenberg-Marquardt; uncertainties from LM procedure: 1
- emcee ensemble MCMC, flat log priors: 1
- Gaussian fit of r21 distribution: 1
- Cold component fixed at Tkin 50 K, log n 4.2, log N(CO) 18.0 in two-component fit (five free parameters): 1

### Validation checks used
- Blue and red CO(2-1) wings compared for spatial overlap: 1
- Total CO fluxes consistent with single-dish measurements; alpha_CO consistent with Papadopoulos+14: 1
- Box-by-box examination in Appendix; removing uncertain boxes C5, C9 leaves results consistent: 1
- Optically thin alpha_CO ~0.34 gives lower limits: 1
- Discussion of differential lensing: 1
- Compared [CI] and low-J CO linewidths (KS test P=0.88): 1
- Compared with Kaufman et al. 1999 models; tested zeta_CR = 5e-15: 1
- K-S test between masses: statistic 0.148, p=0.524: 1
- Resolution tests by smoothing Antennae and Henize 2-10: intercepts differ by factor ≤2: 1
- 30% systematic flux uncertainty adopted: 1
- Compared with SPIRE/FTS U/LIRG sample: 1
- Compared with Jiao et al. global L'[CI]-L'CO relation: 1
- fluxes consistent with channel-integrated values within 1.4xFWHM: 1
- 3 mm-based luminosities ~10% lower, same conclusions: 1
- compared with RJ dust-based masses: 1
- compared to Valentino2018, 2020a: 1
- Source sizes from 2D Gaussian fit show emission is unresolved: 1
- Checked contamination from companion C1 in Q0050+0051 and from undetected companions: 1
- Radio synchrotron subtracted for Q1416+2649 via power-law from FIRST/VLASS; not possible for Q1228+3128: 1
- Cross-comparison of three mass tracers: 1
- Compared with LVG result of Usero et al. 2004: 1
- Dense tracers (CO 6-5, HCN, HCO+) p-v diagrams confirm outflow; compared with SFR and AGN power: 1
- CO-based SFR consistent with SED SFR: 1
- Opacities checked against C18O non-detection: 1
- Lower bound because of interferometric filtering: 1
- Optical depth cross-checked with 12CO/13CO ratio method (0.36); repeated for full region: 1
- Tested alternative excitation corrections: 1
- Compared with alpha_CO of GN20 and merger values; metallicity check: 1
- Checked metallicity via mass-metallicity relation and BPT diagram: 1
- Compared moment maps and residuals; inclination consistent with NIR estimates: 1
- Dust vs CO masses agree to ~0.23 dex median; Pearson ~0.74 excluding NGC 7213: 1
- Systematic uncertainty ±0.20 dex from conversion factors: 1
- Compared with van der Marel et al. 2013 values: 1
- Gaussian-opacity fit leaves significant wing residuals; factor-2 changes in Sigma_g fail to match wings: 1
- Repeat with only well-matched samples and MS-only targets; KS test: 1
- RADEX with n=3e5 gives factor 2-4 higher columns: 1
- Compared with disk mass 0.014 Msun from HCO+: 1
- Visual match of scaled [C I] spectrum to faint feature: 1
- Compared with indices from Solomon et al. 1987 and Rubio et al. 2015: 1
- Compared with Bjerkeli+2016 and Dunham+2014 for IRAS 15398; Tex factor ~2.5 as uncertainty: 1

### Key parameters and settings (bibcode: value)
- 2018ApJ...863..143C: T_ex = 30 K, X_CI = (3.0±1.5)e-5, alpha_[CI] = 9.43
- 2018ApJ...863..143C: R from RA=16:52:58.900, Dec=02.24.03.950; R=0.5 kpc for C1; sigma_R = 0.3 kpc
- 2017MNRAS.466.2825B: Tex = 30 K; X_CI = 3e-5; A10 = 7.93e-8 s^-1; Q10 = 0.6
- 2017MNRAS.466.2825B: r21/10 = 0.8
- 2017MNRAS.466.2825B: zeta_CR = 1e-15 s^-1; integrate to Av=7; vturb = 1.5 km/s
- 2024ApJ...964..166K: 12CO/13CO=70, H2/12CO=2e4, R21 CO(1-0)/CO(2-1)=0.95
- 2020ApJ...897L..19M: FWHM=96 km/s assumed for [C I]; N_box=3990; N_beam=247
- 2020ApJ...902..109B: lines <3 sigma treated as upper limits
- 2014A&A...567A.125G: R_out~1.5" (100 pc), V_out~100 km/s for CND
- 2017ApJ...848..101V: second 13CO component at -80 km/s below 3 sigma excluded
- 2017ApJ...848..101V: Tex=15 K, filling factor 0.1, 13W32=22.8 K km/s, A_reg=11.2 kpc^2
- 2018ApJ...854..130W: Free: M_disk, r_c, gamma, T0, q, xi, v_sys, inclination, PA
- 2021A&A...652A..98G: T_dust=100 K; kappa_351GHz=0.0865 m^2/kg; gas-to-dust ~100; X_CO=2e20; 3-2/1-0 = 2.9 (tori), 0.7 (FOV), 2.0 (200 pc)
- 2024ApJ...961..228S: Outflow area: intensity > 0.5 K km/s; v_sys = 4 km/s; i_out = i_ring
- 2025ApJ...984L..19Y: 7 free parameters; T100 = 14 K fiducial and 30 K high case; X_CO = 1e-4; mu = 2.37
- 2025ApJ...984L..19Y: a_rep = 0.6 mm from a_max = 1.4 mm; X_CO = 7e-4; alpha = 1e-3, 2e-4, 4e-5
- 2015A&A...581A..85P: TK = Tex = 50-500 K; nH2 1e5-1e7 cm-3
- 2015A&A...581A..85P: V_jet ~165 km/s; HPBW_tr = 0.47''; jet width ~90 AU
- 2015A&A...581A..85P: beam dilution factor ~8; R_disk ~90 AU
- 2019ApJ...885L..39H: H2 density 10^4 cm^-3; velocity width 1 km/s
- 2019BAAA...61..134V: k2 = 190
- 2021A&A...648A..41V: opening angle at 1000 AU projected distance; cloud-velocity channels excluded
- 2015ApJ...798...85P: T=43 K, d=140 pc, mu=1.36
- 2024ApJ...963....1O: CO(3-2)/CO(1-0)=0.8; D_L=1767 Mpc
- 2018MNRAS.474.4988S: area 450 arcsec^2 (0.056 pc^2)
- 2021A&A...646A...1K: Lobe velocity 312 km/s, central 50 km/s
- 2017ApJ...835..278S: maps at 25" ≈ 57 pc resolution, SPIRE 350 um as dust proxy
- 2018MNRAS.479.5440L: exponential vertical profile, h = 0.04'' ~ 300 pc
- 2024ApJ...964...18C: S/N<1 pixels in W_CO and Sigma_mol blanked
- 2024ApJ...964...18C: Sigma_star,T = 100 Msun/pc2; D/M 0.1-1
- 2021A&A...656A..60A: r32=0.66, r21=1.12, r13=1 or 1.35
- 2021A&A...656A..60A: aperture radius 0.75'' = 34 pc
- 2021A&A...645A.120F: CIV doublet ratio fixed to 2:1, common width, red component fixed 2.6 Å from blue
- 2021A&A...645A.120F: X_[CI]=3e-5, Q10=0.48, A10=7.93e-8 s^-1
- 2021A&A...645A.120F: power-law slope -1 over 0.01–12 Ryd; log U from -4 to -1; AV=2
- 2025ApJ...985..194P: r21 = 0.77
- 2015ApJ...801...63M: Abundances reported for Tex 10–75 K
- 2017ApJ...843...18V: R_out = 7 kpc, V_out = 1000 km/s
- 2018A&A...616A..23D: min 20 counts per bin; XRT 0.4–9 keV, NuSTAR 3–30 keV
- 2018ApJ...865...13T: fit range -600 to +600 km/s; CO(2-1)/CO(1-0)=3.2
- 2014ApJ...783...84S: beta = 1.8, Td = 25 K
- 2017ApJ...843..150F: 80 walkers, 1000 steps, first 500 burn-in
- 2020MNRAS.493.3744F: QSO: width 300 km/s, N_CO=1e16 cm-2; companion: 850 km/s, 1e17; Tkin 10-400 K, log nH2 2-7
- 2024ApJ...961..108K: Tex = 17.5 K (minimum mass), X_CO=1.7e-4, mu_H2=2.809
- 2025ApJ...993...90S: 3 sigma_CO threshold
- 2024A&A...684A..56K: 10 zones; Tkin 50-200 K step 25 K; XCO=1e-4
- 2013ApJ...773L..34K: R = 2000 km/s x 25 years
- 2017A&A...600A..62P: Tex = 40 K, tau = 1; Rout = 200 au, Rin = 5 au, T = 30 K at 100 au, q = 0.4, p = 1.5
- 2020MNRAS.496..394R: [CO/13CO]=68±20, [CO/C18O]=570±130; masks 6/4/3 sigma for 12CO/13CO/C18O
- 2015ApJ...811...92C: Stellar mass 1.8 Msun; outer disk i=20 deg, PA=-20 deg; inner disk relative inclination 70 deg, PA=-8 deg; warp between 20 and 23 AU; free-fall at 30 AU
- 2019A&A...632A..33A: r31=0.82, r21~1
- 2019A&A...632A..33A: R_out=0.28'' (~23 pc), v_out=300 km/s, r31=0.82, D_L=17.2 Mpc
- 2017ApJ...842L..15S: 19.5 MHz channels, natural weighting
- 2017ApJ...842L..15S: ~10^7 models sampled; CO/H2 fixed at 8e-5; [C] abundance and GDMR free
- 2025ApJ...988..162D: 5% flux calibration uncertainty included in Gaussian error propagation
- 2020MNRAS.496.4061D: flat priors (log flat for BH mass), ranges in Table 2; 3 million iterations
- 2024ApJ...961..120C: Channels averaged to 15.625 MHz; continuum from line-free channels at 147 and 231 GHz
- 2018Sci...362.1034D: Tdust 50–100 K for W2246, 25–50 K for companions/extended
- 2019A&A...623A..96Y: Tbg = 2.73 K
- 2019MNRAS.485..229R: F21 = 3.2, F10 = 1; rms from line-free range outside -600 to +600 km/s
- 2017ApJ...846L..26W: Free: Mdisk, Rdisk, gamma, T0, q, xi, M*, vsys, inclination, PA, small centering offset
- 2024ApJ...963...72O: Tex = 40 K, mu = 2.8, X_CO=1e-4, d=405.7 pc
- 2015MNRAS.448.2224C: r31 = 0.792
- 2019MNRAS.489.1927S: circular aperture 25"
- 2016ApJ...820...83S: Td=25 K, beta=1.8
- 2024A&A...686A..47M: n_H2 10^1.5-10^7.5 cm^-3; T_kin from T_CMB to 10^3 K; N_CO/dv 10^14.5-10^19.5; dv/dr 0.1-1000 km/s/pc
- 2020ApJ...889....9M: alpha10=4.3; r21=0.79 fixed or measured per region
- 2020ApJ...889..162L: X_CO=1e-4, local linewidth 1 km/s, CMB 19.12 K, 10 zones
- 2019ApJ...871..100H: Free: rho0, p, theta_flared, V_rot,0, V_infall,0, F_C18O; C18O fit at |V-Vlsr|<1.6 km/s, CO at >1.6 km/s
- 2018ApJ...853..195W: beta = 1.8; r_4,1 = 0.4; 0.3 dex added uncertainty on M_mol
- 2018A&A...618A.120L: Tex = 30 K lower limit; mean integral Tmb dV 38.7 K km/s
- 2025A&A...696A.150S: line threshold 5 sigma; assumed line width ~5 km/s
- 2025A&A...700A.285W: robust = 0.5, 30 km/s channels
- 2018ApJ...868L..38G: 120 pc resolution; PAWS CO(1-0) scaled by 0.7 for NGC 5194
- 2017ApJ...846..108C: dark matter fraction 15%; <sin^2 i>=2/3; median sigma 154±5 km/s
- 2020A&A...641A.151S: F_tot/F_25" = 2.0±0.3 at 70 um
- 2020A&A...641A.155V: line width fixed to 50 km/s (scale height 10 pc); [CO/H2]/(dv/dr)=1e-5 km/s/pc; [CI]/H2=3e-5; ortho-to-para 3
- 2018MNRAS.475.5322S: disk radius 90 AU, H~40 AU
- 2018ApJ...860..103S: r21 = 0.8; alpha_CO = 4.4
- 2018ApJ...860..103S: f_H2 = 0.03-0.12 initial; t_dep = 0.7-1.3 Gyr
- 2018ApJ...864L..11X: ring step 0.1'' (0.84 kpc)
- 2020A&A...636A..37D: CO(7-6)/CO(1-0)=0.16 SMG, 0.48 QSO; CO(6-5)/CO(1-0)=0.34 SMG, 0.64 QSO
- 2025A&A...698A.204H: alpha_CO = 4.36
- 2015A&A...580A...1M: X_CO = 0.4e20 (alpha_CO 0.8) to 0.2e20 (alpha_CO 0.34) for outflow; 2e20 (alpha_CO 4.6) for regular gas
- 2019ApJ...882...31A: inclination 68 deg from axial ratio 0.42, intrinsic 0.2
- 2019MNRAS.482.1499M: 5 sigma detection; starburst if sSFR > 4 sSFR(z,M*)
- 2017A&A...602A..11P: Tex = 30 K
- 2024ApJ...966...51G: X(1-0)=2.4, X(2-1)=3 with R21=0.8
- 2024A&A...685A.138V: Q21=0.05-0.4
- 2017A&A...604A...6S: 5 sigma threshold, sigma = 8 mJy/beam
- 2016ApJ...828...46A: line luminosity errors include 10% flux calibration in quadrature
- 2018ApJ...856..118H: L'CO(1-0)/L'CO(2-1)=1.2, alpha_CO(1-0)=4.36 (4.99–7.31 after metallicity correction)
- 2024ApJ...969..122Y: D_L=1179 Mpc, nu_obs=186.822 GHz
- 2021ApJ...908...54W: r21 = 0.8, alpha_CO = 4.4
- 2021ApJ...908...54W: 30% mass return to ISM in constant-t_dep model; none in varying model
- 2026ApJ..1001..131C: Temperature correction B_nu(850,25K)/B_nu(850,T_dust): 0.77 (195616), 1.06 (209435)
- 2013AJ....146...47I: nuclear v_opt = 4800 km/s
- 2018MNRAS.479.3879W: NFW concentration 3.5; CO searched within ~2500 km/s of primary
- 2024A&A...686A..46E: r31 = 0.7; X_CO = 2e20 mol cm-2 (K km/s)-1; between 0.4" and 5"
- 2020ApJ...898...75I: 50 rings, dr = 0.05'' from r = 0.10''; Vsys fixed 4920 km/s; center fixed to AGN; initial i = 45, PA = 128
- 2026A&A...705A..39P: RandomForestRegressor, 200 trees, 80/20 train/test split
- 2019PASJ...71...44H: Tex = 20 K
- 2017ApJ...835L..11T: 2e9 photons, anisotropic scattering, no modified random walk, external radiation field T=10 K
- 2018ApJ...868...95M: V_OF ~1600 km/s, l_OF = 400 pc
- 2025ApJ...995..151Y: cos i correction; helium factor 1.36
- 2020A&A...643A..89P: opening angle 65 deg, PA 22 deg, sector width ~1.1''
- 2018ApJ...856...72O: A10 = 7.93e-8 s^-1, Q10 = 0.6
- 2024ApJ...976...88L: log Upsilon = 0.195 (F336W-F125W) - 1.187, floor -1
- 2024ApJ...976...88L: SFR = 5.53e-42 L_Halpha
- 2017A&A...608A..38O: R = 0.5 kpc, v = 300 km/s
- 2026A&A...705A..33E: ~10% flux calibration error propagated to ~17% (Method 2) and ~14% (Method 3)
- 2020MNRAS.499..193K: Molecular gas: CO(2-1)/CO(1-0)=0.7, alpha_CO=4.4 Msun pc^-2/(K km/s) including helium
- 2020A&A...639A..43A: r21 = 1
- 2023Natur.621..483G: r=2647 pc, h<=600 pc, M_H2=7.5e10 Msun, sigma_v=73 km/s
- 2018ApJ...866..117C: dV deconvolved with 13.5 km/s channel; 10 km/s rotation removed; flux x1.731 for total
- 2021A&A...656A.133Q: R21 = 0.65
- 2021ApJ...908..163M: Delta v = 300 km/s; Q10=0.5; A10=7.93e-8 s^-1; Helium factor 1.36
- 2017ApJ...851...18L: Only spaxels with S/N(CO) > 2 shown in KS relation; Galaxy 3 bulge excluded from correlations due to AGN
- 2019ApJ...873L..19B: alpha_CO = 4.4 Msun/(K km/s pc^2)
- 2024ApJ...975..179C: R21=0.7, alpha_CO=3.1, f_He=0.36
- 2016ApJ...833...69D: Planck15-like cosmology H0=70, Om=0.3, OL=0.7
- 2019A&A...623A..66B: channel 2.5 km/s, 15-1015 km/s
- 2017ApJ...844..123F: L850/Mgas = (6.7±1.7)e19 erg/s/Hz/Msun; Mgas/Mdust = 140
- 2025A&A...701A.113M: 0.8 arcsec slit; 250-500 km/s high-velocity regions; aperture radius ~0.45 arcsec
- 2018ApJ...856...97S: 5-500 K, 1e2-1e7 cm-3, dV=50 km/s, Tbg=2.73 K
- 2020MNRAS.494.2131F: alpha_CO = 4.4, R21 = 0.8
- 2017MNRAS.470L..64P: NH ~1e22 cm-2 for PDRs, ~1e23 for XDR
- 2025A&A...700A.165B: 12+log(O/H)=8.3; alpha_CO,met=17.01; alpha_CO,MW=4.36
- 2018ApJ...857...19F: D=1.93 Mpc; R21=0.7; alpha_CO,MW=4.35; Sigma100_GMC=0.69
- 2024PASA...41...76Z: minimum area larger than 1 beam, no other parameters
- 2020MNRAS.495.3840M: alpha_CO = 4.4 Msun (K km/s pc2)^-1 including helium factor 1.36; inclination 50.2 deg
- 2018ApJ...858...90G: M/L = 352 Msun/pc2 per MJy/sr at 3.6um
- 2018ApJ...859...35G: mass-weighted mean outflow velocity of red and blue wings; no inclination correction
- 2019MNRAS.485.2092C: Metallicities normalised to MW-mass z~0 galaxy (Mstar=5.7e10)
- 2025ApJ...992L...7S: m, b, x0 = 0.816, 0.406, 0.480 (NGC 4424); 0.821, 0.294, 0.360 (NGC 4694)
- 2019Natur.569..519K: A_Halpha = 0.5 mag extinction correction
- 2019MNRAS.486.2366M: 10<T<1000 K, 1e2<n<1e6 cm-3, 1e2<dv<1e6 m/s/pc, 0.1 dex steps
- 2025ApJ...988..263Z: alpha_CO(1-0)=4.35, R21=0.65
- 2019MNRAS.484.4239R: R21 = 2.32
- 2019MNRAS.482.3135B: Q10=0.35, X_CI=3e-5, mu=1.36, A10=7.93e-8 s^-1
- 2016ApJ...823...68S: PA=324 deg, i=58 deg, dR=1.13 arcsec
- 2018A&A...619A..39F: D=2.9 kpc
- 2017MNRAS.468L..87C: line width 50 km/s; solid angle 0.044 arcsec^2
- 2019ApJ...876...91H: alpha_CO = 5.1 Msun (K km/s pc^2)^-1
- 2019A&A...621A..83S: alpha_CO=4.3, D_L=10 Mpc, nuclear aperture r=0.2", v_outflow~180 km/s
- 2017A&A...604A.117C: T=50 K, beta=2.0; alpha_CO=0.8; r43/10=0.6; SFR divided by 1.8 for Chabrier
- 2019ApJ...887...88E: XCO = 2e20 outer disk, 5e20 CND
- 2017A&A...606A..17M: mass-weighted T_dust = 25 K, beta = 1.8
- 2017ApJ...835..174S: inclination 33°, alpha_CO=0.2 alpha_MW
- 2018MNRAS.477.4380S: r54 = 0.28±0.05; alpha_CO = 0.9±0.2
- 2019PASJ...71...85M: Box 120"x160", 114.497-114.73 GHz (1406.8-2013.55 km/s)
- 2016ApJ...833L...6C: kappa_870=0.9 cm2/g, beta=1.7; Tdust 33 K (Clouds C, W), 20 K (Cloud E)
- 2018ApJ...861L..18U: alpha_CO(2-1)=6.2; alpha_CO(1-0)=4.35 for M31 and M51
- 2019A&A...628A..23A: fixed CO line width 642 km/s
- 2018ApJ...861..123F: Linewidths 172 km/s (H02), 350 km/s (S05)
- 2019MNRAS.487.4305S: r43 = 0.91 (also 0.46 tested)
- 2019ApJ...875L...8R: R12 = 1.4; alpha_CO 1.5-3
- 2018MNRAS.478.3120A: RMS 0.139 mJy per 150 km/s channel; line width 200 km/s
- 2017ApJ...841L..25T: Td=32 K, beta=2.2, kappa850=0.4-1.5
- 2019ApJ...882..137P: ASPECS sensitive to H2 ~1e9 Msun at z=0.29 and ~1e10, 2e10, 3e10 Msun at z≈1.43, 2.61, 3.8
- 2019ApJ...884L..33L: CO S/N > 2; Sigma_* > 1e7 Msun kpc^-2; S/N>3 strong lines, >2 weak lines
- 2017ApJ...850...54C: R31=7, XCO=4.7e20
- 2016ApJ...832..142Z: v_w 150 km/s (lower), 180 km/s (upper); alpha_CO 0.34 to 0.8
- 2018ApJ...854L...4R: T_dust varied 20-30 K for uncertainties
- 2018ApJ...860..172S: alpha_CO(1-0)=4.35, (2-1)=6.25, (3-2)=17.4 Msun pc^-2 (K km/s)^-1
- 2019A&A...628A..65A: v_out = 100 km/s, R_out = 35 pc
- 2016A&A...593L...2N: CI and CO luminosities scaled by 0.46 for beam contamination
- 2019ApJ...881..147S: Xco = 2e20 cm^-2 (K km/s)^-1; CO(2-1)/(1-0) ~0.8
- 2019PASJ...71...40T: alphaCO=4.36 f_metal; f_metal=1.1 at logM=11, 1.4 at 10.5; upper limits 5 sigma with 400 km/s
- 2018ApJ...853..149S: CO6-5/2-1 brightness ratio 0.72; CO(2-1)/(1-0) factor 3.1


### Assumptions (bibcode: value)
- 2018ApJ...863..143C: LTE, optically thin [CI], CO and [CI] trace the same gas
- 2018ApJ...863..143C: Outflow alpha_CO of 2.1±1.2 used where [CI] not detected
- 2017MNRAS.466.2825B: Lens models from dust emission apply to [CI] gas
- 2017MNRAS.466.2825B: Solar undepleted elemental abundances; UMIST 2012 subset network
- 2024ApJ...964..166K: 12CO optically thick, 13CO optically thin, same Tx, LTE
- 2024ApJ...964..166K: 10% flux error and factor of 4 X_CO variation define uncertainties
- 2024ApJ...964..166K: Galactic X_CO=2e20 for normal, 0.5e20 for starbursts and centers
- 2020ApJ...897L..19M: [C I] line shape same as CO(4-3)
- 2020ApJ...897L..19M: Milky Way metallicity; plane-parallel PDR
- 2020ApJ...897L..19M: alpha_CO=0.8, alpha_[CI]=7.3 Msun (K km/s pc^2)^-1
- 2020ApJ...902..109B: single common line width for all lines of a source
- 2020ApJ...902..109B: Tdust=25 K, beta=1.8
- 2020ApJ...902..109B: Tex=30 K; alpha_CO=3.6; r21=0.75, r31=0.77 for sources without CO(1-0)
- 2020ApJ...902..109B: single PDR, no optical depth correction
- 2024ApJ...977..198L: Line center and width fixed to CO(4-3) where [C I] is partially covered
- 2024ApJ...977..198L: CGM defined as emission on scales ≳16 kpc
- 2024ApJ...977..198L: T_dust = 47 K, beta = 1.6, optically thin; L_FIR over 42.5-122.5 µm
- 2024ApJ...977..198L: QSOs: alpha_CO=0.8, R41=0.87, X_CI=8.4e-5, Tex=29.1 K (Q10=0.457); companions R41=0.85; dust: DGR 1/50 with 47 K
- 2024ApJ...977..198L: CGM X_CI range (3.0-8.4)e-5; halo mass 10^12.5 Msun; baryon fraction 15.6%
- 2014A&A...567A.125G: X_CO^MW = 2e20 cm^-2 (K km/s)^-1
- 2014A&A...567A.125G: multi-conical uniformly filled outflow; coplanar with disk; X_CO ~1/4 of MW
- 2019ApJ...887...74F: r32/10 = 0.8; alpha_CO = 0.8; flat LCDM H0=70, OmegaM=0.3
- 2019ApJ...887...74F: kappa_1THz=20 cm2/g; lambda_Edd=1; L'CO(5-4)/L'CO(3-2)=0.7
- 2017ApJ...837...60B: X_CO = 1e-4 n(H2), 1.2" streamer depth, kinetic temperature 200 K, background 10 or 100 K
- 2017ApJ...837...60B: Bolatto2013 X-factor N(H2)=2.6e20 T*_A dV
- 2017ApJ...848..101V: optically thick 12CO, same filling factor for 1-0 and 3-2, LTE
- 2017ApJ...848..101V: [12CO]/[13CO]=50, [12CO]/[H2]=1e-4, LTE, 13CO optically thin with finite-opacity correction
- 2015ApJ...812L..23S: Spherical symmetry; dark matter M_DM = 0.25 M_dyn
- 2018ApJ...854..130W: M*=1.7 Msun, d=103 pc, X_CO=1e-4, mu=2.37, inner radius 0.1 AU, Keplerian, vertically isothermal, single plane
- 2021A&A...652A..98G: Galactic X_CO
- 2021A&A...652A..98G: 3-2/1-0 ratios ~2.0 (circumnuclear) and ~2.9 (nuclear); Milky Way X_CO
- 2024ApJ...961..228S: mu = 2.8; X_CO = 2.0e20; protostellar mass 1 Msun for Keplerian; constant mass loss rate
- 2025ApJ...984L..19Y: X_CO = 1e-4 tentatively; CO in gas phase at midplane; vertically constant X_CO
- 2025ApJ...984L..19Y: Disk gravitationally stable (no spirals)
- 2024A&A...691A.178B: Control sample uses r21=0.6, r31=0.5
- 2024A&A...691A.178B: alpha_CO=3.6 (and 0.8 shown)
- 2015A&A...581A..85P: X_CO = 1e-4; CO optically thin (lower limit in B2)
- 2015A&A...581A..85P: compression factor ~3, uncertain by factor ~3
- 2015A&A...581A..85P: C17O/CO=1/1792, X_CO=1e-4, Tex 50-500 K, factor 1.4 for He
- 2019ApJ...885L..39H: 12C/13C = 77; Tex of [13C I] equals that of [C I]
- 2019ApJ...885L..39H: Electron collisions ignored
- 2019BAAA...61..134V: Spherical clouds; distance 63 kpc; alpha_CO = 4.3 Msun (K km/s pc2)^-1 (XCO = 1e20)
- 2021A&A...648A..41V: mu=2.76, X_CO=1e-4, Tbg=2.7 K, outflow perpendicular to disk, optically thin
- 2015ApJ...798...85P: [H2]/[12CO]=1e4, [12CO]/[13CO]=76, LTE
- 2024ApJ...963....1O: X_CO = Milky Way disk value 2e20 cm^-2 (K km/s)^-1, ~30% uncertainty
- 2018MNRAS.474.4988S: gas/dust temperature 140 K; CO/H2 number ratio 1e-4
- 2021A&A...646A...1K: CO/H2 = 2e-4
- 2014ApJ...784...78R: Galactic X_CO = 2e20 cm-2 (K km/s)-1; z=0.128; H0=70, Om=0.3, OL=0.7
- 2014ApJ...790..160S: alpha_CO = 0.86 Msun (K km/s pc^2)^-1, 0.5 dex error; outflow assumes L'(3-2)/L'(1-0)=1
- 2018MNRAS.481.4931E: CO/H2 ~1e-3 (carbon-rich); oxygen-rich case gives 3.9e-2 Msun
- 2017ApJ...835..278S: R21 = 1.0 (0.7-1.0 for CO(1-0))
- 2017ApJ...835..278S: optically thin HI, no opacity correction
- 2017ApJ...835..278S: alpha_CO = 4.35 Msun pc^-2 (K km/s)^-1, R21 = 1 for luminous mass
- 2018MNRAS.479.5440L: parameters constant with radius (single ring)
- 2018MNRAS.479.5440L: [C/H2] abundance of M82; factor of 2 uncertainty
- 2024ApJ...964...18C: constant D/M = 0.55 (mean of 0.4-0.7)
- 2021A&A...656A..60A: Milky Way alpha_CO=4.36
- 2021A&A...656A..60A: alpha_CO=4.36, r31=0.27, 45% missing flux correction, inclination 57 deg, Calzetti extinction
- 2021A&A...645A.120F: Tdust=40 K for the continuum cross-check; X_[CI]=1e-5 for region A
- 2021A&A...645A.120F: Standard ISM abundance ratios scaled to a range of metallicities
- 2025ApJ...985..194P: alpha_CO from stellar mass-metallicity correction (T18), weighted average 4.4-6.9
- 2025ApJ...985..194P: average redshift z=1.6
- 2015ApJ...801...63M: XCO = 0.5e20 cm-2 (K km/s)-1, uncertain at ±2x
- 2017ApJ...843...18V: ULIRG-like alpha_CO = 0.8; luminosity distance 933 Mpc
- 2018A&A...616A..23D: 1.4 Msun neutron star, distance 5.2 kpc for Eddington fractions
- 2018ApJ...865...13T: X_CO = 2e20 (Milky Way), D_L = 374 Mpc
- 2014ApJ...783...84S: alpha_CO = 4.6 Msun (K km/s pc^2)^-1 for SMGs; HI set to 50% of H2 for local sample
- 2017ApJ...843..150F: d=122 pc, PA=312 deg, Mgas=0.09 Msun, XCO=1e-4 for CO, LTE, ring sigma=0.1 R, v_turb proportional to sound speed
- 2020MNRAS.493.3744F: alpha_CO=0.8; lensing corrected; L'(4-3)/L'(1-0)=1 for QSO
- 2020MNRAS.493.3744F: Spherical geometry, H2 only collision partner, CMB background at z=2.84
- 2024ApJ...961..108K: Optically thin, LTE
- 2025ApJ...993...90S: X_CO=1e-4, T_ex=50 K; alternative CO-to-H2 factor 2.0e20
- 2024A&A...684A..56K: CMB at z=4.432, T=14.742 K
- 2013ApJ...773L..34K: LTE, excitation temperature equals kinetic temperature
- 2017A&A...600A..62P: CO/H2 abundance 1e-4
- 2018MNRAS.475..448T: 12CO/H2=2e-4, 16O/18O=300
- 2020MNRAS.496..394R: same Tex for both species
- 2015ApJ...811...92C: X_CO = 1e-4; HCO+ abundance 1e-9; T=70 K inside 30 AU, r^-0.5 beyond
- 2019A&A...632A..33A: Milky Way alpha_CO conversion factor of 2e20 cm-2/(K km/s), thermally excited gas
- 2019A&A...632A..33A: Galactic alpha_CO=4.36 (upper limit) or 1/4 of this for galaxy centres
- 2017ApJ...842L..15S: kappa_d = 0.04 (nu/250 GHz)^beta m2/kg; mu = 1.9; eastern source negligible; same GDMR in both components; 36% He correction
- 2025ApJ...988..162D: Radially varying alpha_CO (Bolatto2013/Sun2022); alpha_CO(1-0)=4.35 for sensitivity estimate
- 2020MNRAS.496.4061D: Galactic CO-to-H2 factor 3e20; CO(2-1)/CO(1-0)~0.6; HI negligible; distance 3.06 Mpc
- 2020ApJ...891...83C: alpha_CO=3.8 Msun (K km/s pc^2)^-1 for all galaxies
- 2024ApJ...961..120C: Dust T=40 K at z=4.3 gives S850 = 1 mJy ↔ 115 Msun/yr
- 2014ApJ...797...90S: X_CO = 1e20 cm-2 (K km/s)-1 (X20=1), 36% He mass contribution; alpha_CO = 2.2 X20 Msun/pc2 per K km/s
- 2018Sci...362.1034D: beta=1.8, kappa(850µm)=0.0484 m2/kg, gas-to-dust 100, alpha_CO,MW=4.6 and ULIRG=0.8
- 2019A&A...623A..96Y: LTE; same Tex for both transitions; 13CO/C18O abundance ratio 5.5-10
- 2019MNRAS.485..229R: X_CO = 2e20 cm-2 (K km/s)-1; D_L = 242.4 Mpc
- 2014ApJ...781L..39T: αCO = 0.8 Msun (K km/s pc2)^-1, thermalized lines; Tdust 40 or 50 K
- 2017ApJ...846L..26W: Flared LTE vertically isothermal Keplerian disk; X_CO=1e-4; mu=2.37; inner radius 0.1 au; distance 140 pc with 20 pc uncertainty added in quadrature
- 2020ApJ...898...61I: H0=70, OmegaM=0.3, OmegaL=0.7
- 2020ApJ...898...61I: R21 = 1; alpha_CO = 1.3 Msun pc^-2 (K km/s)^-1 (~0.4 dex uncertainty) for both samples
- 2024ApJ...963...72O: Column density varies within 20% for Tex 20-50 K
- 2025ApJ...989....1Z: kappa = 2.3 (nu/230 GHz) cm2/g, Tdust = 20 K; ISM xCO=1e-4 for Ophiuchus
- 2024A&A...682A.166F: Flat LCDM, H0=70, Omega_M=0.3
- 2015MNRAS.448.2224C: X_CO = 2e20 cm^-2 (K km/s)^-1, D_L = 21.8 Mpc, z = 0.005688
- 2018A&A...617A..54L: X_CO = 2e20 H2 cm-2 (K km/s)-1; W_CO=0 except J1723
- 2019MNRAS.489.1927S: alpha_CO = 3.1±2.1 Msun (K km/s pc^2)^-1; H0=70
- 2019MNRAS.489.1927S: cone axis at 45 deg to line of sight; alpha_CO^out = 2.1 (range 0.8-3.4)
- 2016ApJ...820...83S: Galactic XCO = 3e20 for all galaxies (alpha_CO=6.5 incl. He)
- 2016ApJ...820...83S: Td=25 K, beta=1.8
- 2024A&A...686A..47M: H2 sole collisional partner, ortho-to-para ratio 3; X_CO/(dv/dr)=1e-5
- 2020ApJ...889....9M: Milky Way CO-to-H2 conversion 2e20 cm^-2 (K km/s)^-1 with helium
- 2020ApJ...889....9M: H2/HI=0.3 for total gas fraction
- 2020ApJ...889..162L: Tkin>19.12 K; N(CO)Phi<3.2e19 cm-2 from dynamical mass; N(CO)/n(H2)<1.1e18 cm
- 2024A&A...692A.215C: alpha_CO depends on metallicity (Genzel 2015)
- 2015ApJ...803...60S: alpha_CO = 0.8; alpha_HCN = 10; uncertainty up to factor of two
- 2019A&A...628A.118B: alpha_CO = 0.8 Msun (K km/s pc^2)^-1; L'CO3-2/L'CO1-0 from systemic emission
- 2019ApJ...871..100H: X_CO=5e-4, X_CO/X_C18O=560, T0=70 K, T ∝ r^-0.4
- 2018ApJ...853..195W: Galactic X_CO = 2e20 cm^-2 (K km/s)^-1
- 2014ApJ...795....5O: M82 CO ladder; Iono+2009 L'CO-LIR relation; Td=35 K, beta=1.5
- 2018A&A...618A.120L: CO abundance 1e-4, mu=1.4, d=140 pc
- 2021AN....342.1160P: Milky Way conversion factor 4.6 Msun/(K km/s pc^2)
- 2021AN....342.1160P: alpha_CO = 0.8 Msun/(K km/s pc^2) for outflow
- 2025ApJ...994...98F: X_CO=5e-5, T_frz=20 K, sigma_crit=0.01 g cm-2, D_CO=1e-3, CO/13CO=69, CO/C18O=557
- 2025A&A...700A.285W: alpha_CO = 1/10 of MW value 4.35 (conservative); 1/2 as optimistic
- 2018ApJ...868L..38G: alpha_CO(2-1) ~ 6.2 Msun pc-2 (K km/s)-1 (Galactic, with CO(2-1)/(1-0)=0.7)
- 2018ApJ...868L..38G: alpha_CO(1-0)=4.35, alpha_HCN~14 for f_dense; f_dense ~ 2.3 HCN/CO
- 2017ApJ...846..108C: Planck cosmology H0=67.77, OmegaM=0.31, OmegaL=0.69
- 2017ApJ...846..108C: Gas and stars share same half-light radius; constant velocity dispersion
- 2017ApJ...846..108C: Chabrier IMF; alpha_CO=0.8; Halpha not extinction corrected
- 2026A&A...705A.163H: alpha_CO = 4.35 Msun (K km/s pc^2)^-1
- 2026A&A...705A.163H: LCDM Om=0.27, OL=0.73, H0=70
- 2020A&A...641A.151S: alpha_CO=1.1 Msun pc^-2 (K km/s)^-1
- 2020A&A...641A.151S: alpha_CO=1.1, solar metallicity, CO(2-1)/CO(1-0)=3
- 2020A&A...641A.155V: [CI] co-spatial with CO; dense and diffuse gas share same metallicity
- 2025ApJ...995..219F: alpha_CO(3-2)~1 Msun/(K km/s pc^2); Tdust=44.7 K (20%); beta=1.8; optically thin; helium factor 1.36
- 2015ApJ...813..118M: alpha_HCO+ ≈ 10, alpha_CO ≈ 4.3 Msun/(K km/s pc^2); mean 33 GHz thermal fraction 79%
- 2019ApJ...883..193N: CO(2-1)/CO(1-0) = 1; alpha_CO = 4.8 (alternative 0.6-0.8); thin disk h=0.1r; v~25 km/s
- 2018MNRAS.475.5322S: beta=1, kappa0=0.035 g cm-2 at 850 um, Tdust=90 K
- 2016MNRAS.458.3134R: X_CO = 2e20 cm^-2 (K km/s)^-1; filament masses assume CO(1-0) and CO(3-2) distributed similarly
- 2015ApJ...811..124S: kappa_870=0.077, delta_GDR=72, solar metallicity, gamma=1, 25% dark matter, CO(2-1) thermalized
- 2017A&A...599A.113M: ISM carbon abundance [C]/[H]=1.35e-4
- 2021ApJ...908..231M: alpha_CO = 3.1 Msun (K km/s pc2)^-1, 0.3 dex uncertainty; L'CO(2-1)/L'CO(1-0)=0.62
- 2025A&A...699A.369V: D=50 kpc; alpha_CO=8.4; R32/10~2; density profile r^-1
- 2018ApJ...860..103S: Milky Way-like alpha_CO ~50% systematic uncertainty; flat LCDM Om=0.307, H0=67.7
- 2018ApJ...864L..11X: constant velocity dispersion across each disk; same rotation curve for all lines; H2O excluded due to low S/N
- 2018ApJ...864L..11X: disk mass and CO 1-0 scale lengths equal that of [CI]; entire support by rotation; no lensing correction
- 2025A&A...701A..48D: r21 = 0.8–1.2; alpha_CO = 0.8–4.3 Msun/(K km/s pc^2)
- 2020ApJ...901..151S: X_CO=2.0e20 (standard) or 0.5e20 cm-2 (K km/s)-1; D=19.6 Mpc
- 2020ApJ...901..151S: X_CO=0.5e20, alpha_CO=1; cylindrical outflow, constant velocity, uniform density
- 2020A&A...636A..37D: alpha_CO=0.8 (and 6.5), M_H2/M_HI=5, beta=2, nu0=1.5 THz, undetected line width 400 km/s
- 2025A&A...698A.204H: same alpha_CO for all sources regardless of MS classification
- 2015A&A...580A...1M: L'CO(2-1)/L'CO(1-0) = 1
- 2017ApJ...843..136E: X = 4e20 cm^-2 (K km/s)^-1, factor of two uncertainty
- 2019ApJ...882...31A: alpha_CO = 4.36 Msun/(K km/s pc^2)
- 2017ApJ...836..130R: XCO=0.4e20 cm^-2 (K km/s)^-1; CO(3-2)/CO(1-0)~0.8
- 2014A&A...568A..92M: Xco thin ~0.449 (T=35.9 K, [CO/H2]=1e-4) lower limit; Xco=5 upper limit
- 2019ApJ...876...72L: 12C/13C = 68±15 and 32S/34S = 24.4±5.0; same Tex and emitting volume
- 2020ApJ...894...28D: CO(1-0)/CO(4-3) = 2.4; alpha_CO from Tacconi18
- 2026ApJ..1003...68Y: X_CO = 6.5e20 cm-2 (K km/s)-1; 2-1/1-0 ratio 0.8; distance 50 kpc
- 2019MNRAS.482.1499M: alpha_CO = 0.8 (merger) or 4.6 (disk); LambdaCDM H0=70
- 2019MNRAS.482.1499M: K-band Sersic traces mass with constant M/L
- 2017A&A...602A..11P: CO 3-2/1-0 flux ratio = 9 (thermalised)
- 2024ApJ...966...51G: Same Tex for 12CO and 13CO from 12CO; N(H2)/N(13CO)=3e6; spherical virialized clumps; distance 50 kpc
- 2021A&A...655A..25Z: alpha_CO = 3.3 Msun (K km/s pc^2)^-1 from stellar mass M*=1.2e11 Msun
- 2021A&A...655A..25Z: alpha_CO = 0.3 (optically thin) and 0.8 (thick) Msun (K km/s pc^2)^-1
- 2020NatAs...4..670A: L_CO(7-6)/L_CO(1-0)=0.24; ULIRG X_CO (Downes1998)
- 2020NatAs...4..670A: LAB6.1 fraction of FIR luminosity follows 1.2 mm continuum
- 2024A&A...685A.138V: X_[CI] ~1.5e-5 scaled linearly to ~25% Zsun
- 2014ApJS..214....1U: alpha_CO = 4.8 (L_FIR<1e11) or 0.8 (U/LIRGs)
- 2019A&A...632A..66O: Conversion 4.6 K km/s pc2 for tails; 0.3 for central disc and broad component (optically thin)
- 2018MNRAS.475.3004S: XCO = 2e20 cm^-2/(K km/s); ratio 3.2; D_L = 16.1 Mpc; z=0.00436
- 2015A&A...584A..99E: r6-5 = 13 (17-36 for wings), X_CO = 0.8, optically thin dust, kappa = 4.0 (nu/1.2 THz)^-2.0 cm2/g, T_dust = 45 K
- 2016ApJ...828...46A: [CO]/[H2]=1e-4; [CO]/[13CO]=70; [CO]/[C18O]=550 or 1650
- 2018ApJ...856..118H: Td = 25 K; stellar-mass-dependent gas-to-dust ratio per Tacconi2018
- 2016A&A...591A..73G: X[CI]=3e-5, Q21=0.57, A21=2.68e-7 s^-1
- 2024ApJ...969..122Y: alphaCO = 4.3 (Galactic), r21 = 0.77
- 2021ApJ...908...54W: stellar velocity dispersion sets gas linewidth; Milky Way alpha_CO
- 2020ApJ...905..147Y: alpha_[CII] ~30 Msun/Lsun with 0.3 dex scatter (M_mol/L_[CII]=15-60)
- 2026ApJ..1001..131C: alpha_nu = 6.7 +/- 1.7e19 erg/s/Hz/Msun; 25 K calibration
- 2018ApJ...854...83T: alpha=4.3 Msun (K km/s pc^2)^-1; thermalized optically thick CO
- 2019ApJ...886...15T: XCO = 7e20 cm-2 (K km/s)-1, 12CO(2-1)/(1-0)=1.0, inclination 30–70 deg
- 2018ApJ...862...64S: Salpeter IMF; BzK and ULIRG CO SLEDs
- 2014A&A...565A..59D: C+ abundance 1.4e-4, n_crit 2.7e3 cm^-3, PDR T ~300 K
- 2017ApJ...844...99L: CO-to-H2 ~1e-4 ISM abundance; distance 188 pc; MvD16 T Tauri models with stellar luminosity 1 Lsun
- 2016NatAs...1E...3P: r31=0.66; H0=70, Om=0.3, OL=0.7
- 2016NatAs...1E...3P: alpha_CO = 3.6 Msun (K km/s pc^2)^-1, solar metallicity
- 2018MNRAS.479.3879W: Non-detected SMGs would follow the L'CO-L_IR trend if at same redshift
- 2018MNRAS.479.3879W: L'CO(3-2)/L'CO(1-0)=0.66, alpha_CO=1 Msun (K km/s pc^2)^-1
- 2024A&A...686A..46E: Galactic X_CO since no merger and not IR luminous; helium included
- 2026A&A...705A..39P: Uniform spherical clouds, 40 shells; GOW chemistry; CR rate from depletion time
- 2012A&A...538L...9H: Xco = 3e20 H2 cm-2 (K km/s)-1; R3-2/1-0 = 0.59; distance 22 Mpc
- 2018A&A...614A..42M: L'CO(2-1)=L'CO(1-0); alpha_CO 0.8 to 4.6
- 2019PASJ...71...44H: distance 50 kpc; 12CO/H2=1.6e-5; 12CO/13CO=50
- 2018ApJ...863..193V: Galactic X_CO = 2e20 cm^-2 (K km/s)^-1
- 2014MNRAS.438.1267S: gas-to-dust ratio 90 ± 25; burst duration 250 Myr
- 2017ApJ...835L..11T: Dust-to-gas fraction 0.014 (Semenov composite aggregate)
- 2018ApJ...868...95M: alpha_HCN = 0.24–10, alpha_CO = 0.8–4.6
- 2018ApJ...868...95M: Inclination 80 deg
- 2017ApJ...845..154V: alpha = 0.8 Msun (K km/s pc^2)^-1; H0=70, OmegaM=0.3
- 2017ApJ...845..154V: Tex = 30 K
- 2017ApJ...845..154V: Majority of [C II] from same region as CO and [C I]
- 2025ApJ...995..151Y: X_CO = 2e20 cm^-2 [K km/s]^-1; alpha_CO = 4.35
- 2025ApJ...995..151Y: Constant mass-to-light ratio 0.35 Msun/Lsun
- 2020A&A...643A..89P: SLED independent of velocity within sector; outflow perpendicular to disk, i=43 deg
- 2020A&A...642A.155Z: Typical dust temperature ~38-40 K at these redshifts (Schreiber18)
- 2024ApJ...972..147C: spherical cloud, CMB heating
- 2015A&A...583A.104S: Milky Way CO-to-H2 conversion
- 2017ApJ...851..126V: alpha_CO = 0.8; r32/r10 ratio 0.97
- 2016ApJ...831...32N: 12CO optically thick; 13CO same Tex as 12CO; LTE; H2/13CO = 5e6
- 2016ApJ...832..148V: X_CO = 2e-20 cm^-2 (K km/s)^-1; D_L = 150 Mpc
- 2018ApJ...867...48I: CO(3–2)/CO(1–0) thermalized; canonical alpha_CO in active environments (0.8 Msun (K km/s pc2)^-1)
- 2018ApJ...867...48I: n_H2 = 1e5 cm^-3, r = 7 pc
- 2018ApJ...856...72O: Undetected [CI] assumed same width as CO(6-5)
- 2018ApJ...856...72O: CMB effect not included; would raise masses ~2x
- 2024ApJ...976...88L: Constant alpha_CO = 4.35 Msun (K km/s pc^2)^-1, or variable alpha_CO from Bolatto+13 eq. 31 iterated until change <0.1%
- 2020ApJ...897L..30M: alpha_CO = 4.3 (MW), Accurso2017 metallicity-dependent, Amorin2016 low values
- 2020ApJ...897L..30M: distance from main sequence 0.15 dex
- 2020ApJ...901...79A: delta_GDR=200; alpha_CO=3.6 for CO; RJ method T_d=25 K, beta=1.8, alpha_CO=6.5
- 2025ApJ...991...53C: alpha_CO = 3 Msun/(K km/s pc^2) x 1.36 for helium
- 2013ApJ...769L..12L: Sigma proportional to I; alpha_CO = 4.35 Msun pc^-2 (K km/s)^-1; N(HI) = 1.823e18 I_HI
- 2019ApJ...879...75H: alpha_CO = 0.8 Msun (K km/s pc^2)^-1; Galactic value would raise mass by 5.5
- 2018ApJ...862....8T: N from X_CO = 2e20 with CO(3-2)/(1-0) ratio of 1
- 2017A&A...608A..38O: optically thin, LTE, alpha_CO = 0.25 at Tex 29 K, spherical outflow
- 2018ApJ...864...38L: beta = 1.8
- 2018ApJ...864...38L: Chabrier IMF; Sigma_SFR = (1/2 SFR)/(1/4 pi d^2)
- 2026A&A...705A..33E: same alpha_CO for clumpy and smooth gas
- 2020MNRAS.499..193K: CO dispersion scaled to ~1 kpc scale height with sigma ∝ L^1/2
- 2020MNRAS.499..193K: sigma_3D^2 = 3 sigma_1D^2
- 2020Natur.581..269N: r21 = 0.81, alpha_CO = 3.0, Texc 25-45 K
- 2024ApJ...977..251H: X_CI=3e-5, r41=0.46, alpha_CO=0.8, Td=25 K, alpha_dust=6.7e19, helium factor 1.36
- 2014ApJ...787...48X: alpha_CO = 4.3 (Galactic) or 0.8 (ULIRG); CO(1-0) emission concentrated in the ALMA disk
- 2019MNRAS.490.5860S: R12 = 1.4; alpha_CO = 1.1 Msun pc^-2/(K km/s)
- 2019MNRAS.490.5860S: near side is west of kinematic major axis
- 2019ApJ...881...63N: Same FWHM as [CII] for all lines
- 2019ApJ...881...63N: alpha_CO=0.8 Msun/(K km/s pc2)
- 2019ApJ...881...63N: Cosmology H0=70, OmegaL=0.7, Om=0.3
- 2025ApJ...992..211N: XCO = 2e20, CO(2-1)/CO(1-0) = 1, D_L = 69.3 Mpc
- 2020A&A...639A..43A: Galactic X_CO = 2e20 cm-2 (K km/s)-1
- 2023Natur.621..483G: Equipartition of turbulent kinetic and magnetic energy
- 2014A&A...567A.119S: galaxy lies on the M-sigma relation
- 2018ApJ...866..117C: T_d = 25 K
- 2018ApJ...866..117C: alpha_CO = 0.8; CO(6-5)/CO(1-0) ~ 2
- 2019ApJ...882..136A: r21=0.76, r31=0.42, r41=0.31 from Daddi et al.
- 2019ApJ...882..136A: alpha_CO = 3.6 Msun (K km/s pc^2)^-1
- 2024MNRAS.527.9343L: R21 = 1; alpha_CO = 4.3 Msun pc-2 (K km/s)-1 including heavy elements; adopted distances
- 2021A&A...656A.133Q: alpha_CO = 4.35 Z'^-1.6; metallicity gradient -0.1 dex per Re
- 2021ApJ...908..163M: X[CI]=1.5e-5, Q10=0.5 (LTE, optically thin)
- 2025A&A...700A.278R: extended component 13% of FIR; 20% of [CII] from ionised gas; geometric factor of two
- 2015ApJ...815..103B: alpha_HCN=10, alpha_CO=4.35, Murphy et al. 2011 TIR-to-SFR
- 2017ApJ...851...18L: alpha_CO = 4.3 Msun (K km/s pc^2)^-1
- 2019ApJ...873L..19B: CO(2-1)/CO(1-0) thermalized, accurate to <30%
- 2019ApJ...873L..19B: Milky Way alpha_CO applied to literature (conservative)
- 2024ApJ...975..179C: alpha_CO calibrated for spiral galaxy disks
- 2020A&A...633A.127F: alpha_CO = 0.8 (alternative 4.3); optically thick
- 2020ApJ...901..141K: alpha_CO=3.6; M0=1e12 Msun/h; h=0.7, Om=0.27
- 2025MNRAS.536.3757A: f_dm = 0.25, r = 10 kpc, SED-fit stellar masses
- 2018ApJ...867..165B: CO(3-2)/CO(1-0) = 6; Xco = 4e20
- 2018ApJ...867..165B: Brightness temperature ratio 0.82; cprops XCO 4.35e20
- 2016ApJ...833...69D: alpha_CO = 3.6 Msun (K km/s pc^2)^-1 for all sources
- 2025ApJ...995L..63L: R31 = 0.5; alpha_CO = 4.36 Msun (K km/s pc^2)^-1
- 2020ApJ...903..145L: alpha_CO = 4.35 Msun (K km/s pc^2)^-1; Salpeter IMF
- 2020ApJ...892..119M: Cosmology Om=0.3, OL=0.7, H0=70
- 2019A&A...623A..66B: I21/I10 = 0.7; alpha = 4.36 Msun/(K km/s pc^2)
- 2019A&A...623A..66B: R21=0.7; X_CO = 2e20 cm^-2/(K km/s) with helium; Sigma_H2 = 4.2 I_1-0
- 2017ApJ...844..123F: Galactic X_CO = 3e20 (alpha_CO = 6.5); alpha_CO=1.4 alternative
- 2017ApJ...844..123F: 50% recycling of stellar mass; 50% gas fraction; gas exhaustion time 200 Myr
- 2025A&A...701A.113M: R21 = 0.7; alpha_CO = 4.3 Msun pc^-2 (K km/s)^-1
- 2020ApJ...890L..10K: I70/I350 as a proxy for dust temperature
- 2020ApJ...902..110D: alpha_CO=3.6 Msun/(K km/s pc2)
- 2018ApJ...856...97S: [CO]/[H2]=1e-4, [HCO+]/[H2]=1e-8, XCO=0.8e20
- 2019ApJ...880...15K: alpha_CO = 6.5 Msun/(K km/s pc^2) incl. factor 1.36 for heavy elements
- 2019ApJ...880...15K: Flat LCDM H0=70, OmegaM=0.3, OmegaL=0.7
- 2025ApJ...990..221M: Galactic alpha_CO = 4.35; D = 88.6 Mpc; uncertainty from 5% flux calibration
- 2021A&A...646A.127H: r31=0.42±0.07 (or 0.27±0.07); alpha_CO=0.8 or 4.36
- 2018ApJ...866L..12G: X_CI=3e-5, Q10=0.5, A10=7.93e-8 s^-1
- 2018ApJ...866L..12G: f_d/t~0.5 from L'CO(4-3)/L'CI
- 2025A&A...700A.165B: alpha_CO scatter 0.165 dex
- 2020ApJ...903...94M: XCO 4e20; CO(2-1)/(1-0)=0.85; [H2]/[13CO]=1.4e6
- 2020ApJ...901L...5K: alpha_CO=4.36; R13≈1.8, R14≈2.4; flat LCDM H0=67.4, Om=0.315
- 2018ApJ...857...19F: Metallicity from radial gradient, CO(2-1)/CO(1-0)=0.7, R_H2/R_CO=1.2, truncated power-law density with beta=1
- 2018ApJ...856L..12N: alpha=1.5, beta=1.5, T_dust=35 K
- 2018ApJ...856L..12N: alpha_CO = 4.3 Msun (K km/s pc^2)^-1, r31 = 0.57
- 2024PASA...41...76Z: alpha_CO(2-1) = 6.7 Msun pc^-2 (K km/s)^-1
- 2018ApJ...858...90G: alpha_CO = 4.3, alpha_HCN = 10 Msun pc-2 (K km/s)-1, include helium
- 2018MNRAS.479.2126F: r31=0.57, alpha_CO=4.3
- 2018MNRAS.479.2126F: lower mass uncertainty includes starburst-like conditions
- 2026ApJ..1003..231W: alpha_CO(3-2) 0.3-0.7 Msun pc^-2 (K km/s)^-1 from one-component LVG, median of probability distribution
- 2020ApJ...892...68N: X_CO = 1e20 cm^-2 (K km/s)^-1 for starburst
- 2018ApJ...859...35G: alpha_CO = 0.8 Msun (K km/s pc^2)^-1, 100% molecular; tidal components 3.6
- 2019MNRAS.485.2092C: Gas dominated by molecular gas at z=2
- 2025ApJ...992L...7S: alpha_CO range 0.35 to 4.35 for uncertainty
- 2020MNRAS.497.2771M: LCDM H0=70, OmegaM=0.3, OmegaL=0.7; Chabrier IMF; alpha_CO 4.6 (B,D) and 0.8 (mergers)
- 2019Natur.569..519K: alpha_CO = 4.35 (Z/Zsun)^-1 Msun/(K km/s pc^2), 50% uncertainty
- 2019MNRAS.486.2366M: x_CO and x_C ~1e-4; MH2 < Mdyn; virial K_vir>=1
- 2025ApJ...988..263Z: Milky Way CO-to-H2 factor for all galaxies
- 2020ApJ...890...29F: alpha_CO=3.2 (0.8 for outflow); CO thermalised; D=23.3 Mpc
- 2019MNRAS.484.4239R: Milky Way XCO = 2e20 cm^-2 (K km/s)^-1
- 2019MNRAS.482.3135B: [CI] optically thin; Scoville calibration assumes Td=25 K, beta=1.8, Galactic X_CO
- 2024ApJ...977...36B: alpha_CO=0.8, L'CO(2-1)/L'CO(1-0)=1
- 2021A&A...656A..45M: Galactic X_CO = 4.3 Msun (K km/s pc^2)^-1
- 2016ApJ...823...68S: X_CO=0.8e20 (low) or 2e20 (Galactic); factor 1.41 for He
- 2018A&A...619A..39F: L'CO(6-5)=0.9 L'CO(2-1); thermalized; alpha_CO=0.8
- 2025ApJ...988...72S: R21 ~0.8; alphaCO = 4.3 Msun (K km/s pc^2)^-1; DL = 100 Mpc
- 2021A&A...648A..32K: alpha_CO = 4.36 (Msun K km/s pc^2)^-1; helium removed; factor 1.3 for total gas
- 2017MNRAS.468L..87C: CO(2-1)/CO(1-0) = 0.8; tau_dep = 2 Gyr, 0.2 Gyr, 20 Myr
- 2019ApJ...876...91H: Cosmology H0=70, OmegaM=0.3, OmegaL=0.7; metallicity-dependent alpha_CO including helium
- 2026ApJ..1004..126K: dust kappa 0.37 m2/kg at 250um, beta=2, T=30 K; Galactic CO-to-H2 2e20
- 2019A&A...621A..83S: thermalized optically thick CO, L'(2-1)/L'(1-0)=1
- 2017A&A...604A.117C: alpha_CO=0.8 Msun (K km/s pc2)^-1
- 2024MNRAS.534..683Z: alpha_CO = 6.7; distance 9.8 Mpc
- 2019ApJ...887...88E: Distance 3.8 Mpc; factor 1.36 for heavy elements
- 2017A&A...606A..17M: Galactic alpha_CO = 6.5 (with helium); alpha_850 = 6.7e19 erg/s/Hz/Msun; gas mostly molecular
- 2025ApJ...992...44D: X_CO = 3e20 cm^-2 (K km/s)^-1 with 30% uncertainty; distance 9 Mpc
- 2019ApJ...879L..13M: Milky Way XCO justified by solar or super-solar metallicity
- 2019ApJ...879L..13M: Distance 60 Mpc
- 2018ApJ...860...87F: Typical Galactic CO abundance ratios and velocity gradients
- 2018ApJ...860...87F: alpha_CO 0.8 for B, 4.3 for A; magnification 2.38; W1 gas bound with isotropic turbulence
- 2025A&A...698A.296R: R21 = 0.65; alpha_CO = 4.35 Z^-1.6; 50% error on alpha_CO/R21
- 2018MNRAS.477.4380S: Clump spherical; sigma_tot ≈ sigma_bgs
- 2024A&A...689A.263D: alpha_CO=1.1 in Shimizu et al.; ~0.3 in hotspot
- 2019PASJ...71...85M: Milky-Way X_CO = 2.0e20 cm^-2 (K km/s)^-1; distance 20.8 Mpc
- 2018MNRAS.476.3956T: alpha_CO=0.8 Msun/(K km/s pc^2)
- 2024A&A...682A.182G: alpha_CO3-2 ≈ 0.8 Msun/(K km/s pc^2)
- 2016ApJ...833L...6C: LMC X_CO = 4.7e20 cm-2 (K km/s)-1; R31=7.4
- 2019ApJ...882....1L: alpha_CO~18 from metallicity (Glover & Mac Low 2011); X_CI=3e-5; Q10=0.6; GDR=540 at 0.3 Zsun
- 2024ApJ...977L...6F: Metallicity-dependent CO-to-H2 conversion factor
- 2018ApJ...861L..18U: CO(2-1)/CO(1-0) = 0.7
- 2019A&A...628A..23A: CO(2-1)/CO(1-0) brightness ratio R21=0.9 for SLED comparison
- 2018ApJ...861..123F: Same HCN-to-dense gas conversion for post-starbursts and other galaxies
- 2019MNRAS.487.4305S: alpha_CO = 0.8±0.1 Msun/(K km/s pc^2)
- 2019ApJ...875L...8R: D_L = 34 Mpc
- 2018MNRAS.478.3120A: Milky-Way like J-transition ratio; alpha_CO = 4.6 Msun (K km/s pc^2)^-1
- 2017A&A...608A..98S: Prolate clouds; alpha_CO=4.3; mu=2.4; f_H2=1; distance 3.8 Mpc
- 2017ApJ...841L..25T: CO J=3-2 thermalized
- 2017ApJ...846L..14S: alpha_CO = 4.0; CO(2-1)/CO(1-0) = 1 (thermalized)
- 2019ApJ...882..137P: alpha_CO = 3.6 Msun/(K km/s pc^2); line width 200 km/s
- 2019ApJ...884L..33L: alpha_CO = 4.3; Salpeter IMF; Rv = 4.5
- 2018ApJ...860..111D: alpha_CO=6.5; Chabrier IMF; flat LCDM H0=70, Om=0.3
- 2019A&A...623A..79C: XCO = 2e20 cm-2 (K km/s)-1, R13 = 2
- 2017MNRAS.465.4390B: alpha_CO=0.8; gas-to-dust ratio 91
- 2019ApJ...870...39V: X_CO≈2.8e20 cm^-2 (K km/s)^-1; distance 40 Mpc; helium factor 1.36
- 2018PASJ...70L...6K: r41=0.41±0.07, alpha_CO=0.8 (starburst/merger)
- 2017ApJ...845..170B: R21 ~0.7; alpha_CO = 3.1; f_He = 0.36; disk thickness h ~0.1 R_d
- 2018A&A...620A.115B: Local 5-4/4-3 ratio applies; differential lensing negligible; Planck2015 cosmology, Chabrier IMF
- 2017ApJ...850...54C: optically thick emission; masses include He
- 2017MNRAS.469.4683C: MS: R51=0.23, alpha_CO=4.87; SB: R51=0.6, alpha_CO=1
- 2017A&A...602L...9M: Galactic alpha_CO = 6.5 Msun (K km/s pc^2)^-1 inherent in Scoville et al. 2016 calibration
- 2016A&A...587A..44P: Intrinsic Brγ/Brδ=1.52, F99 extinction law, Hα/Paα=8.58, Kroupa IMF, i=47 deg
- 2018MNRAS.474.4039M: alpha_CO = 4.2 (incl. helium), r21 = 0.6
- 2018MNRAS.475L..52S: inclination 45 deg, CO(2-1)/CO(1-0) ratio unity, alpha_CO = 0.8 Msun (K km/s pc^2)^-1
- 2017ApJ...849..154S: alpha_CO=1 (4.36 as alternative), R=7 kpc, random-disk inclination, r21/10=0.84
- 2019ApJS..241...19I: alpha_HCN=10 (range 6-40), optically thick thermalized; alpha_CO=1.5 for CO J=2-1 total mass
- 2019ApJ...887..183Z: Planck cosmology H0=68, OmegaLambda=0.69; Chabrier IMF
- 2017ApJ...840....8S: x_CO = 3e-4
- 2016ApJ...822...80S: single line assumed to be CO
- 2018PASJ...70...73H: CO-to-H2 factor 2.0e20 cm-2 (K km/s)-1 with helium factor 1.36
- 2016ApJ...833...68A: Td=25 K, beta=1.8, delta_GDR=200 for MAGPHYS masses
- 2016ApJ...832..142Z: outflow cone perpendicular to disk inclination of 65 deg
- 2018ApJ...861...43P: R21=1; alpha_CO=1
- 2017ApJ...838..146L: Z'=0.5, source area 201 arcsec^2 (29.2 kpc^2)
- 2017MNRAS.468.3468G: metallicity ~0.5 Zsun, alpha_CO~10+-2
- 2017ApJ...851...98T: kappa(850um)=0.383 cm2/g, T_dust=40 K
- 2017ApJ...851...98T: Flat cosmology H0=70, OmegaM=0.3, OmegaL=0.7
- 2018Natur.556..469M: alpha_CO = 0.8, r41 = 0.41, helium factor 1.36, SFR/S870 = 150±50
- 2017ApJ...849...90S: Td = 20 and 100 K; X_CO = 0.8e20; Te = 5000 K; d = 10.8 Mpc
- 2017ApJ...850..180J: circular orbits; Planck16 cosmology
- 2019AJ....157..131B: alpha_HCN ≈ 10, alpha_CO ≈ 7 M_sun (K km/s pc^2)^-1; distance 22 Mpc
- 2016ApJ...833...12R: T_dust = 25 K (20-30 K for uncertainty); gas-to-dust ratio 100
- 2019MNRAS.488.3904L: alpha_CO = 4.4; CO(2-1)/CO(1-0)=0.8
- 2018ApJ...854L...4R: T_dust = 25 K; gas-to-dust 100
- 2018ApJ...860..172S: Galactic alpha_CO; CO(2-1)/(1-0)=0.7, CO(3-2)/(1-0)=0.25; no inclination or filling-factor correction
- 2019ApJ...887..144J: 20% dark matter in dynamical gas mass; T_ex=30 K for [CI]
- 2019A&A...628A..65A: X = 2e20 cm-2 (K km/s)-1, CO(1-0)/CO(2-1) brightness ratio 1
- 2016A&A...593L...2N: CO optically thick
- 2019ApJ...881..147S: Milky Way Xco and line ratio 0.8; comparisons relative within the area
- 2019ApJ...880L..19K: alpha = 0.8 Msun (K km/s pc^2)^-1
- 2016A&A...595A..72M: alpha_CO = 5 Msun/(K km/s pc^2)
- 2019PASJ...71...40T: Field-like CO excitation, no environmental dependence
- 2016NatSR...626896A: X_CO = 2.3e20, D = 17.1 Mpc, helium excluded
- 2019ApJ...877L..38R: GDR ~30 (alpha_CO=0.8); also GDR ~95 for solar metallicity
- 2019ApJ...885L..21M: Mass-weighted dust temperature 100 K
- 2019MNRAS.482L..65K: LIRG-like r21 = 0.9; masses expressed in units of M_sun/alpha_CO
- 2016ApJ...823...26E: XCO = 1.8e20, D = 35 Mpc
- 2019ApJ...871...85L: alpha_CO = 0.8
- 2018ApJ...853..149S: X_CO = 2e20 cm^-2 with factor 1.36 for helium
- 2019ApJ...876..130H: gas fraction of unity, dust-to-gas 1/90, global dust temperature, Kennicutt98 IR SFR calibration with Chabrier IMF
- 2016A&A...594A..81P: ULIRG-like alpha_CO ~0.78 Msun (K km/s pc2)^-1 and r21=0.9
- 2016ApJ...819...82S: CO(5-4)/CO(1-0)=0.23 (factor 2 uncertainty); alpha_CO from Genz12 eq. 7; LCDM H0=70, Om=0.3, OL=0.7
- 2019A&A...632A..61G: X_CO = 2e20 mol cm-2 (K km/s)-1; r21 = 2.2 (CND), 2.5 (torus); r31 = 2.9
- 2019MNRAS.488.5029H: Afterglow spectral slopes alpha=-1/2 to 1/3 (Sari1998)
- 2016ApJ...831..161K: X_CO = 1.8e20 (H2 cm^-2)/(K km/s)
- 2018A&A...613A..34P: gas virialized; inclination 54 deg from axial ratio
- 2019MNRAS.485.1595P: Galactic alpha_CO=4.6 Msun (K km/s pc^2)^-1 for depletion times
- 2018ApJ...867..140L: mu = 10.9; inclination average <v_rot> = pi/2 v_obs
- 2019ApJ...882..138D: alpha_CO=3.6; no CMB correction (<~15%); intermediate excitation from Daddi15
- 2017ApJ...846...73T: Galactic [CO]/[H2]; X_CO = 4.7e20 cm^-2 (K km/s)^-1
- 2018Natur.553...51M: alpha_CO = 1.0 Msun (K km/s pc^2)^-1, thermalized CO emission
- 2016ApJ...823...51B: R21=0.7, alpha_CO=3.1 including 1.36 He factor
- 2017ApJ...842L..21N: r21=0.77, alpha_CO=4.36
- 2017ApJ...848L...7C: Galactic alpha_CO = 3.2 Msun (K km/s pc^2)^-1, no helium; same for all samples
- 2017MNRAS.466..138K: Half of intrinsic flux missed due to CMB; thermally excited CO(3-2); alpha_CO = 4
- 2016A&A...595L...7D: LTE, Tex >> T_CMB, alpha_CO=4.6 for thick gas with F21/F10=4, Galactic CO/H2 abundance for thin gas
- 2018ApJ...867..166S: X_CO = 7e20 cm^-2 (K km/s)^-1
- 2019MNRAS.490.1220K: Only log N(H2)>21 contributes (low-N contributes 3% per Zwaan2006)
- 2018MNRAS.476..122V: Galactic X_CO
- 2016ApJ...827...34O: L'CO(5-4)/L'CO(1-0)=0.39; alpha_CO=0.8
- 2016A&A...590A..73A: N(H2)/I(CO 1-0)=2.5e20 cm^-2; CO 3-2/1-0 brightness temperature ratio 0.5; D=21 Mpc
- 2018MNRAS.477L..60E: alpha_CO=4 scaling; Tex~30 K
- 2019ApJ...887..149B: X_CO = 2e20 cm^-2 (K km/s)^-1; CO(2-1)/CO(1-0) flux density ratio 3.2
- 2019MNRAS.489..427I: Same SED as W; alpha_CO=0.8
- 2017A&A...602A..49H: equal [CII] and CO filling factors; Tex,CO = dust temperature
- 2019A&A...631A.167D: Planck cosmology H0=67.8, Om=0.308
- 2016ApJ...820L..39N: alpha_CO = 4.3 Msun (K km/s pc^2)^-1 (Bolatto et al. 2013); R ≈ 10 kpc
- 2016A&A...586A..45S: Sigma_100=1 for the CO-dark correction; O/H 8.3-8.6 from MUSE
- 2017ApJ...841...43E: X_CO = 1.8e20 H2 cm-2 (K km/s)-1; factor 1.36 for total gas
- 2019ApJ...882....5W: Constant X_CO; no inclination correction; NGC 7469 nucleus excluded
- 2018ApJ...854...90E: X_CO = 2e20 H2/cm2/(K km/s)


### Limitations the authors admit
- 2018ApJ...863..143C: Some extended [CI] emission resolved out; flux 34±15% lower than Herschel
- 2018ApJ...863..143C: Outflow environment unprecedented; [CI]-based assumptions (X_CI, same gas as CO) uncertain
- 2017MNRAS.466.2825B: Cannot rule out AGN; Tex assumed; X_CI assumed; differential lensing possible
- 2024ApJ...964..166K: Comparison depends on assumed X_CO and R21 and on resolution differences; starburst differences are ambiguous
- 2020ApJ...897L..19M: Band 8 ACA stand-alone flux calibration accuracy not explored
- 2020ApJ...902..109B: PDR results only qualitative; small sample; selection effects cannot be fully excluded
- 2024ApJ...977..198L: CGM significance too low for individual targets; mass comparisons depend on uncertain parameters
- 2014A&A...567A.125G: Outflow rate is a lower limit due to limited velocity coverage
- 2014A&A...567A.125G: Resolution does not resolve kinematics of inner r~50 pc
- 2019ApJ...887...74F: Limited depth and resolution prevent distinguishing disk, merger and outflow
- 2019ApJ...887...74F: Dust mass depends strongly on the adopted kappa
- 2017ApJ...837...60B: Missing flux from interferometer filtering; masses are lower bounds
- 2017ApJ...848..101V: Mass traced is only a fraction of total; LTE and abundance assumptions are simplistic
- 2015ApJ...812L..23S: alpha_CO uncertain; metallicity of ionised gas may not represent molecular gas; AGN cannot be excluded
- 2018ApJ...854..130W: Simple model cannot capture inner structures or warp; uncertainties exclude model assumptions
- 2021A&A...652A..98G: Common T_dust adopted for all sources; mass estimates depend on assumed conversion factors
- 2021A&A...652A..98G: Spectral index maps only possible for 3 sources
- 2021A&A...652A..98G: Small-number statistics for orientation and correlations
- 2024ApJ...961..228S: Protostellar mass is uncertain because Keplerian motion cannot be separated from the jet
- 2024ApJ...961..228S: Outflow mass and velocity are likely underestimated; field of view limits outflow length
- 2025ApJ...984L..19Y: CO/H2 ratio uncertain; absolute gas surface density scales as X_CO^-0.5
- 2025ApJ...984L..19Y: Dust opacity model uncertainty affects gas-to-dust ratio; limited spatial resolution
- 2024A&A...691A.178B: Different AGN and galaxy timescales, spatial scales, many upper limits, alpha_CO unknown
- 2015A&A...581A..85P: Resolution too low to fully resolve the disk; edge-on view unfavourable
- 2015A&A...581A..85P: Mass loss rate is a lower limit and uncertain by factor ~3; SO data cannot constrain density and temperature
- 2019ApJ...885L..39H: Southeast positions not definitively detected due to [C I] wing contamination; 12C/13C may exceed 77 so tau is a lower limit
- 2019BAAA...61..134V: Procedure cannot separate clouds that differ only in velocity, only spatially resolved ones
- 2021A&A...648A..41V: Outflow masses are lower limits (no correction for missing flux at cloud velocities or opacity); sample not statistically significant.
- 2015ApJ...798...85P: Gas mass is a crude estimate, dominated by assumed isotopic ratios and temperature
- 2024ApJ...963....1O: X_CO uncertainty may overestimate molecular mass by a factor of a few
- 2024ApJ...963....1O: Chandra data too shallow to resolve cavity
- 2018MNRAS.474.4988S: Mass conversion highly uncertain; deeper observations needed for polar lobes
- 2021A&A...646A...1K: Model is non-unique owing to k–i degeneracy; masses underestimated
- 2014ApJ...784...78R: Cannot tell whether gas lies in front of or behind the BCG
- 2014ApJ...790..160S: Outflow quantities order-of-magnitude; XCO and line ratio uncertain
- 2025A&A...696A.100G: Exact chemical pathways and relative contributions of bottom-up and top-down processes remain unquantified; models omit PAH chemistry
- 2018MNRAS.481.4931E: Velocity resolution is modest and dynamical modelling is deferred.
- 2020ApJ...889L...4L: HI column densities are lower limits for most sightlines (optically thin assumption)
- 2017ApJ...835..278S: Dust maps uncertain (Galactic cirrus, Herschel issues), dominating the error budget
- 2017ApJ...835..278S: Missing flux on large scales
- 2018MNRAS.479.5440L: Velocity map very uncertain due to beam smearing and low S/N; Sigma not robust
- 2024ApJ...964...18C: Data concentrated in narrow metallicity range 8.4-8.6, limiting metallicity analysis
- 2021A&A...656A..60A: Missing flux ~40-50% due to lack of single-dish data.
- 2021A&A...656A..60A: Mass model parameters are degenerate.
- 2021A&A...645A.120F: Low S/N; Lyα and HeII severely affected by night sky lines
- 2021A&A...645A.120F: Mass uncertainty excludes errors on X_[CI], Q10, A10
- 2025ApJ...985..194P: T18 is not calibrated below the SFMS; limited metallicity info; 6 of 10 HM-bMS CO-undetected galaxies have SFRs constrained only by HerMES upper limits
- 2015ApJ...801...63M: Error maps too optimistic; negative bowl from missing short spacings; region 6 fluxes highly uncertain due to absorption
- 2017ApJ...843...18V: Modest angular resolution is a major limitation
- 2018A&A...616A..23D: Observations not strictly simultaneous, spanning many hours across transitions; X-ray spectral model degeneracy
- 2018ApJ...865...13T: X_CO uncertainty may overestimate mass by a factor of a few
- 2018ApJ...865...13T: Projection effects: motions in plane of sky unknown
- 2014ApJ...783...84S: Pathfinder, small samples, only most massive galaxies; results preliminary
- 2017ApJ...843..150F: Parametric temperature/density structure, degeneracies with abundance, dust-to-gas ratio and 18O abundance; turbulence is a disk-averaged intensity-weighted value
- 2020MNRAS.493.3744F: FIR SED poorly sampled so L_IR and SFR are lower limits; kinematics unresolved; SLED has too few points
- 2024ApJ...961..108K: Inclination, Tex, stellar R, M, f_acc are uncertain; mass accretion rate varies by factor 45
- 2025ApJ...993...90S: 12CO affected by foreground absorption; gas mass a lower limit
- 2025ApJ...993...90S: Dust mass depends heavily on opacity and temperature
- 2024A&A...684A..56K: Data not standardized, resolution limited, CO SLED turnover unconstrained
- 2013ApJ...773L..34K: Collision rates unknown; LTE SLEDs for J>3-2 are upper limits; SPIRE limits cannot constrain model
- 2018MNRAS.475..448T: Distance mismatch between GRS 1915+105 and IRAS source; jet power assumes constant power and density
- 2018MNRAS.475..448T: ALMA continuum lacks single-dish data so flux is underestimated
- 2020MNRAS.496..394R: Single excitation temperature is a large source of uncertainty.
- 2020MNRAS.496..394R: Spectral index poorly constrained because bands 6 and 7 are adjacent; fluxes and globule mass are lower bounds.
- 2015ApJ...811...92C: Model is parametric, not dynamically consistent, no systematic parameter search
- 2015ApJ...811...92C: MEM resolution varies with image
- 2019A&A...632A..33A: Missing flux from lack of short spacings; outflow mass uncertain by alpha_CO; outflow rate uncertain by a factor of a few; geometry unconstrained
- 2019A&A...632A..33A: Wings barely resolved
- 2025ApJ...988..162D: Small sample; individual outliers can affect galaxy-to-galaxy trends
- 2025ApJ...988..162D: Metallicity covers only ~0.25 dex and 8 galaxies
- 2020MNRAS.496.4061D: Keplerian rise not resolved; result depends on stellar mass model and Gamma
- 2020MNRAS.496.4061D: Low Gamma should be treated with caution; beam correlations neglected
- 2020ApJ...891...83C: Sizes and axial ratios poorly constrained due to limited resolution and beam elongation
- 2024ApJ...961..120C: Radio resolution cannot identify which of B, C, G hosts the AGN; spectral index from only two points plus limits
- 2024ApJ...961..120C: 5 arcsec ATCA-ASKAP offset unexplained
- 2014ApJ...797...90S: Mass estimates depend on uncertain X_CO; may be an order of magnitude lower if optically thin
- 2018Sci...362.1034D: U1 may be at a different redshift; stellar mass and SFR uncertain by factor of 2
- 2019A&A...623A..96Y: Evolutionary time and Vrel combination not unique
- 2019A&A...623A..96Y: Mosaic fluxes overestimated by 10% due to CASA imaging issue
- 2019MNRAS.485..229R: Mass may differ by up to an order of magnitude due to X-factor and F_ul uncertainty
- 2019MNRAS.485..229R: Filling factor of 1 gives lower limit on tau; velocities are only apparent line-of-sight motions
- 2014ApJ...781L..39T: Redshift remains ambiguous; further CO transitions needed
- 2014ApJ...781L..39T: Simulation not verified at high z for bright CO emitters
- 2017ApJ...846L..26W: Single optically thick CO line likely underestimates gas mass
- 2020ApJ...898...61I: Absolute Sigma_mol depends critically on alpha_CO, and inclination is unknown
- 2020ApJ...898...61I: Modest S/N prevents line profile/outflow analysis
- 2024ApJ...963...72O: Protostellar mass not directly determined; launching radii depend on it
- 2024ApJ...963...72O: Optically thin assumption gives lower limits
- 2025ApJ...989....1Z: Medians are of survivors; survival bias not accounted in medians; absolute ages model-dependent; regions assumed to share initial conditions
- 2024A&A...682A.166F: Simple geometry and single homogeneous cloud; continuum and CO SLED not modeled
- 2015MNRAS.448.2224C: Upper limits depend on X_CO, which may be overestimated by up to an order of magnitude
- 2019ApJ...883..180H: Optical depth problem prevents quantitative column density and C/CO abundance derivation
- 2018A&A...617A..54L: Planck CO maps are masked near some sightlines; weak CO detections may be missed
- 2020MNRAS.499.2534K: Mid-IR resolution blends sources; ages and masses uncertain
- 2019MNRAS.489.1927S: Low spatial resolution prevents constraining geometry of the residual structure
- 2016ApJ...820...83S: Calibration restricted to high stellar mass; low-metallicity systems not probed
- 2024A&A...686A..47M: Only two measurements for r51 and r71; single-component LVG inadequate
- 2020ApJ...889....9M: Resolution cannot exclude that regions comprise unresolved clouds
- 2020ApJ...889....9M: Detailed kinematic characterization left for future work
- 2020ApJ...889..162L: OH+ detection tentative (4 sigma); data insufficient to constrain all eight two-component parameters
- 2024A&A...692A.215C: Scatter in r31 and r41 relations adds systematic errors
- 2015ApJ...803...60S: alpha_CO very uncertain and held constant
- 2015ApJ...803...60S: Missing flux for some lines
- 2019A&A...628A.118B: Gas masses depend strongly on alpha_CO; large uncertainties on tau_dep and tau_SF
- 2019ApJ...871..100H: Offset smaller than beam; calibration issue or proper motion not excluded
- 2018ApJ...853..195W: Optical selection of members may bias the star-forming census; small samples of CO detections.
- 2014ApJ...795....5O: Small number of fields and unknown redshift distribution of faint SMGs give large bias uncertainties; SLE-1 could be systematic noise
- 2018A&A...618A.120L: Launching-radius inferences rely on a steady-state assumption; ACA data would be needed to rule out an envelope
- 2021AN....342.1160P: Band 7 data not optimized for CO(3-2) and only partially covers the field/velocity range
- 2025A&A...696A.150S: findcont conservative in line-rich sources; no manual continuum ranges
- 2025A&A...696A.150S: TM1-only line cubes not produced in first release
- 2025ApJ...994...98F: Surface bias and limited number of lines per annulus prevent discriminating between vertical temperature prescriptions
- 2025A&A...700A.285W: Torque method unvalidated by simulations, configuration likely unstable
- 2025A&A...700A.285W: Mass of young component is poorly constrained from single UV band; closed-box and alpha_CO assumptions
- 2018ApJ...868L..38G: HCN-to-dense-gas conversion and effective critical density remain uncertain
- 2018ApJ...868L..38G: Distances uncertain by 10-30%
- 2017ApJ...846..108C: CO detection is only ~3 sigma peak SNR so 2D CO kinematics and central detail are limited
- 2017ApJ...846..108C: ALESS67.2 nature inconclusive
- 2026A&A...705A.163H: Fixed alpha_CO makes H2 limits uncertain; CO-to-H2 uncertainty may dominate
- 2026A&A...705A.163H: Comparison samples heterogeneous with different selection effects

### Settings cards flag as needed but not stated
- casa version: 24
- continuum subtraction and line-free channels: 20
- casa version and pipeline version: 14
- flux calibrator and flux scale uncertainty: 14
- line-free channels and continuum subtraction method: 12
- line-free channels used for continuum subtraction: 12
- self-calibration solution intervals: 12
- image size and cell size: 10
- flux scale uncertainty: 8
- line-free channels used for continuum: 7
- primary beam correction: 7
- line-free channel ranges for continuum subtraction: 7
- primary beam correction details: 7
- line-free channels for continuum subtraction: 6
- line-free channel ranges: 6
- self-calibration solution intervals and number of iterations: 5
- line-free channel ranges for uvcontsub: 5
- target coordinates: 5
- casa/pipeline version: 5
- cell size and image size: 5
- casa version and whether pipeline or manual calibration: 5
- line-free channels and continuum subtraction: 4
- self-calibration solution intervals and number of rounds: 4
- primary-beam correction details: 4
- flux calibration uncertainty: 3
- source coordinates: 3
- rest frequencies used for the lines: 3
- moment-map clipping thresholds: 3
- clean threshold, mask, cell and image size: 3
- clean threshold, masks, cell and image size: 3
- line-free channels used for uvcontsub: 3
- whether continuum was subtracted and which channels were line-free: 2
- clean threshold and iteration count: 2
- phase center coordinates: 2
- cell and image size: 2
- pipeline version: 2
- primary-beam correction treatment: 2
- casa version and calibration script details: 2
- coordinates of targets: 2
- casa and pipeline versions: 2

## Paper excerpts (40 of 360, chosen for detail and spread over fields/years)

### 2018ApJ...863..143C: ALMA [C I]<SUP>3</SUP> P <SUB>1</SUB>-<SUP>3</SUP> P <SUB>0</SUB> Observations of NGC 6240: A Puzzling Molecular Outflow, and the Role of Outflows in the Globa… (2018; nearby_galaxies, agn_and_quasars, milky_way_ism; observational_alma_primary)
- question: What are the physical properties and energetics of the molecular outflow in NGC 6240, and what is the CO-to-H2 conversion factor in the outflow and quiescent gas, as derived by combining [CI](1-0) with CO(1-0)?
- step 2: Map outflow wings and moment maps
  - method: Image blue (-650,-200) and red (250,800) km/s wings of CO(1-0), CO(2-1), [CI]; moment maps of [CI] within -200<v<250 km/s [3.1: "integrated respectively within $v\in(-650, -200)$ km s$^{-1}$and $v\in(250, 800)$ km s$^{-1}$"]
  - software: CASA
  - validation: Blue and red CO(2-1) wings compared for spatial overlap [3.1: "In Figure [2](#fig:CO21wings_overlap) we directly compare the blue and red line wings using the ALMA CO(2-1) data."]
- step 3: Fit integrated spectra and derive alpha_CO and r21
  - method: Simultaneous two-Gaussian fit to CO(1-0), CO(2-1), [CI] spectra from 12''x6'' aperture with tied v and sigma; M_mol from [CI] LTE optically thin formula; alpha_CO = M_mol/L'CO(1-0) [3.2: "The spectra in Fig. [4](#fig:tot_region_fit) were fitted simultaneously using two Gaussians to account for the narrow core and broad wings"]
  - parameter: T_ex = 30 K, X_CI = (3.0±1.5)e-5, alpha_[CI] = 9.43 [3.2: "We adopt $T_{ex} = 30$ K and $X_{\rm CI} = (3.0\pm1.5) \times10^{-5}$"]
  - assumption: LTE, optically thin [CI], CO and [CI] trace the same gas [4.1.2: "The fundamental underlying assumption is that [CI](1-0) and CO(1-0) trace the same material."]
  - fitting: Simultaneous Gaussian fit; sampler/priors not stated [3.3 Spatially-resolved analysis: the av…: "For each box, the CO(1-0), CO(2-1), and \[CI\](1-0) spectra are fitted simultaneously with a combination of Gaussian functions tied to have the same line centres and widths for all three transitions."]
  - validation: Total CO fluxes consistent with single-dish measurements; alpha_CO consistent with Papadopoulos+14 [2 Observations: "the total CO(1-0) and CO(2-1) line fluxes are consistent with previous single-dish measurements"]
- step 4: Spatially-resolved decomposition into quiescent/outflow
  - method: 13 boxes (nine 2''x2'' and four 3''x3''); up to four Gaussians per box fitted simultaneously; components with -200<v<250 km/s and FWHM<400 km/s are quiescent, others outflow; mean alpha_CO, r21 from components with S/N>=3 [3.3: "we assume that all components with $-200<v[km~s^{-1}]<250$ *and* FWHM$<400$ km s$^{-1}$trace quiescent gas that is not involved in the outflow."]
  - fitting: Up to four tied Gaussians per box, minimal number of components [3.3: "we minimise the number of spectral components required to reproduce the line profiles, up to a maximum of four Gaussians per box"]
  - validation: Box-by-box examination in Appendix; removing uncertain boxes C5, C9 leaves results consistent [Box spectra and outflow identification: "without `C5` and `C9`, we derive $M_{out}=1.1\times10^{10}$ M$_{\odot}$ and $dM_{out}/dt = 2350$ $M_{\odot}~yr^{-1}$"]
- step 5: Compute outflow energetics
  - method: Per box: M_out = L'CO(1-0) x alpha_CO; tau_dyn=R/v_out; Mdot=M_out/tau_dyn; summed over 12 boxes; errors by propagation [3.4: "The mass-loss rate $\dot{M}_{out,i}$, equal to $M_{out,i}/\tau_{dyn,i}$. All uncertainties are derived by error propagation."]
  - parameter: R from RA=16:52:58.900, Dec=02.24.03.950; R=0.5 kpc for C1; sigma_R = 0.3 kpc [3.4: "for box `C1`, we conservatively assume that most of the outflow emission comes from a radius of $1\ensuremath{''}$, hence we set $R=0.5$ kpc"]
  - assumption: Outflow alpha_CO of 2.1±1.2 used where [CI] not detected [3.4: "we adopt the galaxy-averaged outflow $\alpha_{\rm CO}$ of $2.1\pm1.2$"]
  - validation: Optically thin alpha_CO ~0.34 gives lower limits [3.4: "Very stringent lower limits on the outflow energetics can be derived by assuming that its CO(1-0) emission is fully optically thin."]
- step 6: Trends of alpha_CO and r21 with sigma_v and distance
  - method: Bayesian linear regression [3.5: "we conduct a Bayesian linear regression analysis of the relations in Fig. [6](#fig:plots) following (cite: Kelly07)"]
  - software: linmix_err.pro
  - fitting: linmix_err.pro (Kelly 2007); priors not stated [3.5: "We used the IDL routine `linmix_err.pro`"]
- result: mean alpha_CO outflow = 2.1 ± ±1.2 Msun (K km/s pc^2)^-1 [Table 2: "Mean$^\ddag$ outflow comp | $2.1 \pm 1.2$ | $1.4\pm 0.3$"]
- result: mean alpha_CO systemic = 3.2 ± ±1.8 Msun (K km/s pc^2)^-1 [Table 2: "Mean$^\ddag$ systemic comp | $3.2\pm 1.8$ | $1.0\pm 0.2$"]
- result: mean r21 outflow = 1.4 ± ±0.3 dimensionless [Table 2: "Mean$^\ddag$ outflow comp | $2.1 \pm 1.2$ | $1.4\pm 0.3$"]
- result: total molecular mass (boxes) = 2.1e10 ± ±0.5e10 Msun [3.3: "${M}_{mol}^{tot} = (2.1\pm 0.5)\times10^{10}~\rm M_{\odot}$"]
- result: outflow mass = 1.2e10 ± ±0.3e10 Msun [3.4: "$M_{out} = (1.2\pm0.3)\times 10^{10}~M_{\odot}$"]
- result: mass-loss rate = 2500 ± ±1200 Msun/yr [3.4: "$dM_{out}/dt = 2500\pm1200$ $M_{\odot}~yr^{-1}$"]
- result: outflow kinetic power = 0.033 ± ±0.019 L_AGN [3.4: "$1/2\dot{M}_{out}v_{out}^2\equiv \sum_i 1/2\dot{M}_{out,i}v_{out,i}^2 = (0.033\pm0.019)~L_{AGN}$"]
- result: momentum rate = 80 ± ±50 L_AGN/c [3.4: "$v \dot{M}_{out} \equiv \sum_i v_i\dot{M}_{out,i} = (80\pm50)~L_{AGN}/c$"]
- result: depletion time = 8 ± ±4 Myr [3.4: "$\tau_{dep} = 8\pm4$ Myr"]
- result: mass loading eta = 50 ± ±30 dimensionless [Table 3: "$\eta \equiv \dot{M}_{out}$/SFR | $50\pm30$"]
- result: blue-red [CI] wing peak separation = 0.65 ± ±0.02 arcsec [3.1: "The [CI](1-0) red and blue wing peaks are separated by $0.65\ensuremath{''}\pm0.02\ensuremath{''}$."]
- result: total alpha_CO from integrated spectra = 2.1 ± ±1.1 Msun (K km/s pc^2)^-1 [Table 2: "Total$^\dag$ | $2.1\pm 1.1$ | $1.22\pm 0.14$"]
- limitation (authors): Some extended [CI] emission resolved out; flux 34±15% lower than Herschel [2 Observations: "lower by $34\pm15$% than the flux measured by the *Herschel* space observatory"]
- limitation (authors): Outflow environment unprecedented; [CI]-based assumptions (X_CI, same gas as CO) uncertain [4.1.2: "Further investigation is needed, and our work constitutes just a starting point."]
- not stated (card): CO(2-1) clean parameters beyond robust (masks, image size); Image size for [CI] cubes; Gaussian fitting procedure details (optimizer, initial guesses, how number of components chosen, errors); Exact feather parameters (SD scaling, uv overlap); Which CASA version used for which dataset, PdBI cube reduction details; Box positions/centre coordinates for the 13-box grid; Rest frequencies of CO lines;…

### 2017MNRAS.466.2825B: ALMA observations of atomic carbon in z ∼ 4 dusty star-forming galaxies (2017; high_z_galaxies; observational_alma_primary)
- question: What are the molecular gas masses and ISM physical conditions (density, UV field, temperature) of z~4 SPT dusty star-forming galaxies, as traced by [CI](1-0) and PDR modelling?
- step 1: Measure [CI](1-0) line fluxes and upper limit
  - method: Extract spectra at source positions; 3 sigma upper limit for non-detection SPT0345-47 using mean linewidth [2 Sample, Observations and Reduction: "$\Delta V_{\rm CO}$ is the mean linewidth of the detected sample (=410 km/s), and $dv$ is the bin size in km s$^{-1}$ (=50 km/s)."]
- step 2: Compute line luminosities and correct for lensing
  - method: Solomon & Vanden Bout formulae; divide by magnification from lens models [Line luminosities and ratios: "Luminosities in solar units (L$_{\ensuremath{\odot}}$), which represent the true energy output carried by the emission line (used, for example, for calculating cooling contributions) are calculated following (cite: solomon05):"]
  - assumption: Lens models from dust emission apply to [CI] gas [3.2: "we make the assumption that these lens models also apply to the cold molecular gas traced by ."]
  - validation: Discussion of differential lensing [Correction for magnification due to gra…: "Overall, it is likely that differential lensing does not significantly affect the ability of to trace molecular gas."]
- step 3: Derive atomic carbon and H2 masses
  - method: Weiss et al. 2005 carbon mass formula; Papadopoulos & Greve 2004 H2 mass formula [3.5: "(cite: papadopoulos04b) give an expression for calculating the total H$_2$ mass from the luminosity of the ($1-0$) line"]
  - parameter: Tex = 30 K; X_CI = 3e-5; A10 = 7.93e-8 s^-1; Q10 = 0.6 [3.5: "we adopt a literature-standard /H$_2$ abundance ratio of $3 \times 10^{-5}$, and the Einstein $A$ coefficient $A_{10} = 7.93 \times 10^{-8} s^{-1}$."]
  - validation: Compared [CI] and low-J CO linewidths (KS test P=0.88) [3.5: "A Kolmogorov-Smirnov test comparing the CO and linewidths returns $P=0.88$"]
- step 4: Derive alpha_CO implied by [CI] gas masses
  - method: Ratio of M(H2)[CI] to L'CO(1-0), with CO(1-0) from CO(2-1) or higher-J via SLED [3.5.1: "The units of $L'_{\rm CO}$ result in the ratio M(H$_2)^{\rm CI}$/$L'_{\rm CO(1-0)}$ being equal to the value of $\alpha_{\rm CO}$ required to force agreement."]
  - parameter: r21/10 = 0.8 [3.5.1: "We assume a CO$(2-1)$/CO$(1-0)$ brightness temperature ratio of r$_{21/10} = 0.8$"]
- step 5: PDR modelling of density, UV field, temperature
  - method: Grid of 3d-pdr 1D models; probability distributions from ratios [CII]/[CI], CO(4-3)/CO(2-1), [CI]/CO(4-3) [4.2: "we find probability density distributions for the mean density and the mean UV field strength for each galaxy, based on our grid of one-dimensional PDR models."]
  - software: 3d-pdr
  - parameter: zeta_CR = 1e-15 s^-1; integrate to Av=7; vturb = 1.5 km/s [4.1: "The cosmic-ray ionisation rate is taken to be $\zeta_{\rm CR}=10^{-15}\,{\rm s}^{-1}$"]
  - assumption: Solar undepleted elemental abundances; UMIST 2012 subset network [4.1: "We use a subset of the UMIST 2012 network (cite: McEl13) of 33 species (including e$^{-}$ and 330 reactions)"]
  - fitting: Peak of probability distribution over the grid [Comparing to other PDR models: "take $\log n$ and $\log G$ to be the peak of the probability distribution function defined by these line ratio constraints."]
  - validation: Compared with Kaufman et al. 1999 models; tested zeta_CR = 5e-15 [4.3: "Re-calculating our values of $n,G$ with CR fluxes $\zeta_{\rm CR}=5 \times 10^{-15}\,{\rm s}^{-1}$ ($500 \times \zeta_{\rm CR, MW}$), we find that the derived values of $n,G$ typically increase by $\sim 0.5$ dex"]
- result: Mean H2 mass from [CI] (X_CI=3e-5) = 6.6e10 ± 2.1e10 Msun [3.5: "we measure a mean (corrected for gravitational magnification) M(H$_2)^{\rm CI} = (6.6 \pm 2.1) \times 10^{10}$ M$_{\ensuremath{\odot}}$"]
- result: Mean [CI] mass = 1.2e7 ± 0.3e7 Msun [3.4: "$(1.2 \pm 0.3) \times 10^7$ M$_{\ensuremath{\odot}}$"]
- result: Mean H2 mass from CO (alpha=0.8) = 2.8e10 ± 1.7e10 Msun [3.5.1: "$<$M(H$_2)^{\rm CO, \alpha=0.8} > = (2.8 \pm 1.7) \times 10^{10}$ M$_{\ensuremath{\odot}}$"]
- result: Mean implied alpha_CO = 2.0 ± 1.0 Msun (K km/s pc^2)^-1 [3.5.1: "we find a mean CO-to-H$_2$ conversion factor of $\alpha_{\rm CO} = 2.0 \pm 1.0$"]
- result: Mean L[CI]/LFIR = 7.7e-6 ± 2.4e-6 dimensionless [3.4: "$(7.7 \pm 2.4) \times 10^{-6}$"]
- result: Mean log n (3d-pdr) = 5.2 ± 0.6 log cm^-3 [4.2: "$< \log n > = 5.2 \pm 0.6$ cm$^{-3}$, and $< \log G > = 2.9 \pm 1.5$"]
- result: Mean log G = 2.9 ± 1.5 log Habing [4.2: "$< \log G > = 2.9 \pm 1.5$"]
- result: Mean gas temperature = 25 ± not stated K [4.2.1: "We find a mean gas temperature for our sources of 25 K."]
- result: Mean log n with Kaufman99 models = 4.4 ± 0.4 log cm^-3 [4.3: "$< \log n > = 4.4 \pm 0.4$ cm$^{3}$"]
- limitation (authors): Cannot rule out AGN; Tex assumed; X_CI assumed; differential lensing possible [2 Sample, Observations and Reduction: "Due to a lack of X-ray data for our sample we cannot rule out a possible AGN component in any of our 13 DSFGs."]
- not stated (card): CASA version, calibration and imaging steps for the [CI] cubes (deferred to Weiss et al. 2013); Line flux extraction method (aperture, line fitting) and FWHM fitting; Synthesized beam and weighting; Continuum subtraction; Method for deriving PDR probability distributions and uncertainties from line ratios; Treatment of CO(5-4) to CO(4-3) conversion details

### 2024ApJ...964..166K: Physical Properties of Molecular Clouds in the Overlap Region of the Merging Antennae Galaxies (2024; nearby_galaxies, star_formation; observational_alma_primary)
- question: What are the physical properties of GMCs in the Antennae overlap region, which can form super star clusters, and how do they compare with GMCs in other galaxy environments?
- step 5: Derive masses (LTE and X_CO)
  - method: LTE from 12CO/13CO(2-1) with Tx, tau, N(13CO), H2/13CO=1.4e6; and M_lum=1.36 m_H2 X_CO L_CO with X_CO=0.5e20 [4.2.2: "The luminosity is then converted into mass using the standard $\mathrm{X_{CO}=0.5\times10^{20}\;cm^{-2}(K\:km\:s^{-1})^{-1}}$ for starburst galaxies"]
  - parameter: 12CO/13CO=70, H2/12CO=2e4, R21 CO(1-0)/CO(2-1)=0.95 [4.2.1: "We used abundance ratios of $\mathrm{H_{2}/^{13}CO=1.4\times 10^{6}}$ by combining $\mathrm{^{12}CO/^{13}CO}=70$ and $\mathrm{H_{2}/^{12}CO=2\times 10^{4}}$"]
  - assumption: 12CO optically thick, 13CO optically thin, same Tx, LTE [4.2.1: "which we assumed to be optically thick and optically thin respectively"]
  - validation: K-S test between masses: statistic 0.148, p=0.524 [4.2.2: "The K-S statistic and p-value between the two mass distributions are 0.148 and 0.524 respectively"]
- step 7: Find pre-SSC candidate clumps
  - method: GESD outlier test on properties (upper bound 20 outliers, 0.05 level); clumps outlying in ≥2 of density, pressure, virial parameter; thresholds M>1e6, R<25 pc, Pe/k>1e7 within uncertainties [5.1: "we used the `papanda` implementation of the Generalized Extreme Studentized Deviate (GESD) test (cite: 1983Rosner) to detect outliers in each of the calculated physical properties with an upper bound of 20 outliers."]
  - software: papanda
  - assumption: 10% flux error and factor of 4 X_CO variation define uncertainties [5.1: "assuming 10% errors in observed flux and that $\mathrm{X_{CO}}$ tends to vary by a factor of 4 in starburst galaxies"]
- step 9: Compare with other galaxies
  - method: Standardize catalogs (deconvolved R, σv, X_CO 2 or 0.5), fit size-linewidth σv=aR^b, Heyer relation, KDEs (0.25 dex), K-S tests (scipy ks_2samp) [6: "we re-calculated any physical properties that did not match our definitions described in Section 4"]
  - software: SciPy
  - assumption: Galactic X_CO=2e20 for normal, 0.5e20 for starbursts and centers [6: "standard Galactic and starburst values of $\mathrm{X_{CO}=2\times10^{20}\;cm^{-2}(K\:km\:s^{-1})^{-1}}$ and $\mathrm{X_{CO}=0.5\times10^{20}\;cm^{-2}(K\:km\:s^{-1})^{-1}}$ respectively"]
  - fitting: Non-linear least squares, b free or fixed 0.5 [Appendix Spatial and Spectral Resolution: "the slope is held constant at 0.5 and the intercept is fit using a non-linear least squares method"]
  - validation: Resolution tests by smoothing Antennae and Henize 2-10: intercepts differ by factor ≤2 [Appendix Spatial and Spectral Resolution: "the fitted intercepts are only a factor of 2 difference"]
- result: Possible SSC-forming clumps = 17 (6 outliers + 11) ± not stated count [5.1: "In addition to these 6 outlier clumps, there are eleven other clumps that are within uncertainties of having the necessary conditions to form SSCs."]
- result: Mean X_CO mass per clump = 1.14e6 ± σ=1.58e6 Msun [Table 3: "| $\mathrm{M_{lum}}$ ($\mathrm{10^{5}\:M_{\odot}}$) | 0.63 | 77 | 11.4 | 15.8 |"]
- result: Size-linewidth fit, Antennae clumps = a=2.98, b=0.55 ± ±0.15, ±0.01 km/s pc^-0.5 (a) [Table 6: "| Antennae Clumps | S | 2.98$\pm$0.15 | 0.55$\pm$0.01 | 3.52$\pm$0.05 | |"]
- result: K-S between X_CO and LTE masses = statistic 0.148, p 0.524 ± not stated dimensionless [4.2.2: "The K-S statistic and p-value between the two mass distributions are 0.148 and 0.524 respectively"]
- limitation (authors): Comparison depends on assumed X_CO and R21 and on resolution differences; starburst differences are ambiguous [6.2: "any conclusions based on this category are heavily dependent on the assumption that these properties are not significantly affected by the resolution of the observations"]
- not stated (card): Phase center/coordinates of the overlap field and exact observation dates, arrays and configurations; Spectral window setup and rest frequencies; Imaging parameters (tclean weighting, robust, cell size, image size, deconvolver) used for the cubes; Electron temperature Te used for the ionizing flux; Details of how the ellipse HWHM fit and the circularity-based radius error were done; Whether conti…

### 2020ApJ...897L..19M: Discovery of a [C I]-faint, CO-bright Galaxy: ALMA Observations of the Merging Galaxy NGC 6052 (2020; nearby_galaxies, milky_way_ism; observational_alma_primary)
- question: Why is [C I](1-0) undetected relative to CO(4-3) in the merging galaxy NGC 6052, and can [C I] trace its molecular gas mass?
- step 2: Measure CO(4-3) flux and [C I] upper limit
  - method: Integrate primary-beam-corrected spectrum over FoV; 3 sigma upper limit for [C I] using box/beam scaling [3 Morita Array Observation: "We obtain a $3\sigma$ upper limit for the [C I] (1–0) velocity integrated intensity using"]
  - software: CASA
  - parameter: FWHM=96 km/s assumed for [C I]; N_box=3990; N_beam=247 [3 Morita Array Observation: "$N_{\rm box} = 3990$ (the number of pixel where CO (4–3) is detected inside the three sigma contour of Figure [2](#fig:mom0)(b))"]
  - assumption: [C I] line shape same as CO(4-3) [3 Morita Array Observation: "assuming the same value with CO (4–3) line shape"]
  - validation: 30% systematic flux uncertainty adopted [3 Morita Array Observation: "we adopt 30 % as a conservative systematic uncertainly error"]
- step 4: PDR modeling of density
  - method: Compare L[CI]/L_CO(4-3) and L[CI]/L_TIR upper limits to PDRT tracks of constant n_H and U_uv [4.1 Photodissociation Regions: "The red solid and blue dashed lines indicate the tracks for constant $n_{\rm H}$ and $U_{\rm uv}$, respectively."]
  - software: PDRT
  - assumption: Milky Way metallicity; plane-parallel PDR [2 NGC 6052: "we assume the Milky Way metallicity for PDR modeling"]
  - validation: Compared with SPIRE/FTS U/LIRG sample [Discussion, Photodissociation Regions: "together with the data for nearby U/LIRGs observed by SPIRE/FTS (cite: Kame_2016), and the upper limits we obtain for NGC 6052."]
- step 5: Molecular gas mass comparison
  - method: M_H2 = alpha*L' for CO(1-0) and [C I] upper limit [4.2 Molecular gas mass: "where $M_{\rm H2}^{\rm line} = \alpha_{\rm line} L'_{\rm line}$"]
  - assumption: alpha_CO=0.8, alpha_[CI]=7.3 Msun (K km/s pc^2)^-1 [4.2 Molecular gas mass: "assuming a CO (1–0) to H$_2$ conversion factor $\alpha_{\rm CO}$=0.8"]
  - validation: Compared with Jiao et al. global L'[CI]-L'CO relation [4.2 Molecular gas mass: "located an order of magnitude below the global relation obtained in previous surveys"]
- result: CO(4-3) integrated flux = 414 ± 124 Jy km/s [3 Morita Array Observation: "$S_{\rm CO(4-3)}\Delta v = 414\pm124$ Jy km s$^{-1}$"]
- result: [C I](1-0) 3sigma upper limit = <28 ± not stated Jy km/s [Morita Array Observation: "We obtain a $3\sigma$ upper limit for the \[C I\] (1–0) velocity integrated intensity using"]
- result: M_H2 from CO(1-0) = 8e8 ± not stated Msun [4.2 Molecular gas mass: "$M_{\rm H2}^{\rm CO} = 8 \times 10^{8}~M_{\odot}$"]
- result: M_H2 upper limit from [C I] = <1e8 ± not stated Msun [4.2 Molecular gas mass: "$M_{\rm H2}^{\rm [CI]} < 10^{8}~[M_{\odot}$]"]
- result: U_uv from ([OI]+[CII])/TIR = 4-5 ± not stated G0 [4.1 Photodissociation Regions: "The ratio suggests $U_{\rm uv}=4-5$."]
- limitation (authors): Band 8 ACA stand-alone flux calibration accuracy not explored [3 Morita Array Observation: "the actual performance of the flux calibration has not been explored for the ACA stand-alone mode in Band 8"]
- not stated (card): CLEAN threshold and iteration count; Phase center coordinates; Continuum subtraction and line-free channels for ACA data; Number of execution blocks, calibrators and integration times; Which PDRT model parameters (metallicity grid, version) and how L ratios were mapped to tracks; How CO(4-3) FWHM of 96 km/s was measured; Derivation of the 88% missing-flux figure

### 2020ApJ...902..109B: The ALMA Spectroscopic Survey in the Hubble Ultra Deep Field: CO Excitation and Atomic Carbon in Star-forming Galaxies at z = 1-3 (2020; high_z_galaxies, astrochemistry; large_program_or_survey)
- question: What are the CO excitation, atomic carbon abundance and ISM conditions in a cold gas mass-selected sample of 22 star-forming galaxies at z=0.46-3.60 from ASPECS, and what do they imply for the cosmic molecular gas density?
- step 1: Extract spectra and fit lines
  - method: Single-pixel spectra from cubes convolved to 2.2"; simultaneous Gaussian fits of all CO and [CI] lines with tied redshift and width [3.1 Spectral line analysis: "All the lines in the continuum-free spectrum are modeled by Gaussian line shapes, whose central frequencies are tied together by a single redshift."]
  - software: LMFIT
  - parameter: lines <3 sigma treated as upper limits [4.1 Observed emission lines from CO and…: "we will treat tentative lines with an integrated line flux smaller than $3\sigma$ in the VLA and ALMA data as upper limits."]
  - assumption: single common line width for all lines of a source [3.1 Spectral line analysis: "We therefore model all the lines with a single line width."]
  - fitting: non-linear least squares [3.1 Spectral line analysis: "using the non-linear least square fitting code LMFIT"]
  - validation: fluxes consistent with channel-integrated values within 1.4xFWHM [4.1 Observed emission lines from CO and…: "we also compute the line fluxes by integrating the channels within $1.4\times$ the FWHM and confirm these are consistent"]
- step 4: Compare dust luminosity vs CO luminosity
  - method: Estimate rest-frame 850 um luminosity from 1.2 mm and 3 mm continuum and compare to L'CO(1-0) with Scoville2016 relation [5.4 Dust continuum versus low-J CO: "We estimate the rest frame $L_{\nu}(850\,\ensuremath{\mu}m)$ for our sources from the 1.2 mm continuum emission"]
  - assumption: Tdust=25 K, beta=1.8 [Table 4: "assuming $\ensuremath{T_{\mathrm{dust}}}=25$ K and $\beta=1.8$."]
  - validation: 3 mm-based luminosities ~10% lower, same conclusions [5.4 Dust continuum versus low-J CO: "are on average $\approx 10\%$ lower than those from the 1.2 mm, but overall we come to the same conclusions."]
- step 5: Derive [CI] masses and abundances
  - method: Optically thin [CI] mass from line luminosity; abundance [CI]/[H2]=M[CI]/(6 M_H2), M_H2=Mmol/1.36 [6.1 Atomic carbon abundances: "where $\ensuremath{M_{\mathrm{H}_{2}}}= \ensuremath{M_{\mathrm{mol}}}/ 1.36$, not including He."]
  - assumption: Tex=30 K; alpha_CO=3.6; r21=0.75, r31=0.77 for sources without CO(1-0) [6.1 Atomic carbon abundances: "we assume a typical value of $\ensuremath{T_{\mathrm{ex}}}= 30$ K"]
  - validation: compared with RJ dust-based masses [6.1 Atomic carbon abundances: "we come to similar conclusions if we use the dust continuum based molecular gas masses instead"]
- step 6: PDR modelling
  - method: PDRTOOLBOX line ratios ([CI], CO<=4-3, LIR) used to solve for density and G_UV, bootstrapping flux ratios 1000 times [6.2 PDR modeling: "we bootstrap the observed flux ratios within their error a 1000 times and solve for the ISM density and UV radiation field for each instance."]
  - software: PDRTOOLBOX
  - assumption: single PDR, no optical depth correction [6.2 PDR modeling: "assumes that the ISM of a galaxy can be described by a single PDR with a fixed input abundane"]
  - fitting: median and 68% interval of bootstrap solutions [6.2 PDR modeling: "As the final density and radiation field we take the median of these values."]
  - validation: compared to Valentino2018, 2020a [6.2 PDR modeling: "the galaxies occupy the same parameter space as the main-sequence galaxies"]
- result: Average [CI]/[H2] abundance (CO-based) = 1.9e-5 ± 0.4e-5 dimensionless [6.1 Atomic carbon abundances: "$(\ensuremath{\ensuremath{\mathrm{[C\, \textsc{i}]}}/[\ensuremath{\mathrm{H}_{2}}]})_{\rm CO} = \ensuremath{(1.9 \pm 0.4) \times 10^{-5}}$"]
- result: Average [CI]/[H2] abundance (dust-based) = 2.2e-5 ± 0.3e-5 dimensionless [6.1 Atomic carbon abundances: "$(\ensuremath{\ensuremath{\mathrm{[C\, \textsc{i}]}}/[\ensuremath{\mathrm{H}_{2}}]})_{\rm RJ} = \ensuremath{(2.2 \pm 0.3) \times 10^{-5}}$"]
- result: PDR density = >=1e4 ± not stated cm^-3 [6.2 PDR modeling: "the PDR models predict fairly high densities, $\ge 10^{4}$ cm$^{-3}$, for all sources"]
- limitation (authors): PDR results only qualitative; small sample; selection effects cannot be fully excluded [6.2 PDR modeling: "Our results should therefore be treated as qualitative measures of the ISM density and UV radiation field."]
- not stated (card): CASA version and exact calibration/imaging parameters (deferred to companion papers); Source positions used for single-pixel extraction; Median-filter width for continuum fitting; LVG code/priors detail and Bee algorithm settings beyond parameter ranges; Stacking implementation details (velocity bin handling, error propagation); How 3 sigma upper limits and VLA spectra were combined with ALMA in …

### 2024ApJ...977..198L: The SUPERCOLD-CGM Survey. II. [C I](1─0) Emission and the Physical Conditions of Cold Gas in Enormous Lyα Nebulae at z ∼ 2 (2024; high_z_galaxies, agn_and_quasars, milky_way_ism; observational_alma_primary)
- question: What are the physical conditions and molecular gas content of QSOs, companions and the cold CGM in ELANe at z~2, from [C I](1-0), CO(4-3) and dust continuum?
- step 2: Measure [C I] fluxes and widths
  - method: Extract spectra at peak pixel, fit Gaussian; 3 sigma upper limits = 3×RMS×sqrt(δν×FWHM) [3 Results: "We derive the 3$\sigma$ [C I]$(1-0)$ flux upper limits for the companion galaxies where the [C I]$(1-0)$ line is undetected using $\rm 3\times RMS_{channel} \times \sqrt{\rm \delta \nu \times FWHM}$."]
  - assumption: Line center and width fixed to CO(4-3) where [C I] is partially covered [3 Results: "We adopt a Gaussian profile with the line center and width fixed to the values derived from the CO(4$-$3) line"]
  - fitting: Gaussian profile fit [Results: "we use a Gaussian profile to fit the spectrum for each of the QSOs and companions where a full \[C I\]$(1-0)$ spectrum is obtained."]
  - validation: Source sizes from 2D Gaussian fit show emission is unresolved [Appendix: "we consider the [C I]$(1-0)$ emission from the cold ISM of the QSOs to be spatially unresolved"]
- step 3: Estimate CGM [C I] flux
  - method: CGM flux = tapered 7+12 m flux minus 12 m flux; uncertainty is quadrature sum [3.2: "The uncertainty of the [C I]$(1-0)$ flux for the CGM is calculated through $\sqrt{\sigma_{12m}^{2} + \sigma_{7m+12m}^{2}}$"]
  - assumption: CGM defined as emission on scales ≳16 kpc [3.2: "we adopt the definition ‘CGM’ for all the [C I]$(1-0)$ emission on scales $\gtrsim$ 16 kpc"]
  - validation: Checked contamination from companion C1 in Q0050+0051 and from undetected companions [Extended [C I](1-0) emission: "To check if there is any contamination from the companion galaxy C1 in the tapered data to the CGM, we use the fact that the QSO is more luminous in \[C I\]$(1-0)$ than companion C1"]
- step 4: Derive luminosities, FIR luminosity, SFR and dust mass
  - method: Line luminosities from Carilli & Walter formulae; MBB SED normalised to continuum; SFR = 2.1e-10 L_FIR [3.3: "SFR = 2.1 \times 10^{-10}\ L_{\rm FIR(SF)}\ [\rm M_{\ensuremath{\odot}}\ yr^{-1} ]"]
  - assumption: T_dust = 47 K, beta = 1.6, optically thin; L_FIR over 42.5-122.5 µm [3.3: "We adopt a dust temperature of 47 K and emissivity index of 1.6"]
  - validation: Radio synchrotron subtracted for Q1416+2649 via power-law from FIRST/VLASS; not possible for Q1228+3128 [Individual QSOs: "We follow a similar procedure as for Q1228+3128 to subtract the radio synchrotron contribution from the observed ALMA continuum emission."]
- step 5: Constrain gas density and radiation field
  - method: Compare L[CI]/L_CO(4-3) and L[CI]/L_FIR ratios with PDR Toolbox models [4.2: "comparing the observed ratios with those predicted in the photo-dissociation region (PDR) model PhotoDissociation Region Toolbox"]
  - software: PhotoDissociation Region Toolbox
- step 6: Derive molecular gas masses and CGM mass/baryon fraction
  - method: CO(4-3), [C I] and dust based masses; compare to infer alpha_CO [4.3.4: "This suggests that the QSOs and companions are likely starbursts, and both have a low conversion factor"]
  - assumption: QSOs: alpha_CO=0.8, R41=0.87, X_CI=8.4e-5, Tex=29.1 K (Q10=0.457); companions R41=0.85; dust: DGR 1/50 with 47 K [Table 2: "For the QSOs, we adopt $\alpha_{\rm CO}$ = 0.8 $\rm M_{\ensuremath{\odot}}$${[\rm K\ km/s\ pc^2]}^{-1}$, $R_{\rm 41}$ = 0.87"]
  - assumption: CGM X_CI range (3.0-8.4)e-5; halo mass 10^12.5 Msun; baryon fraction 15.6% [4.3.5: "adopting a typical halo mass for QSOs of $10^{12.5}$ $\rm M_{\ensuremath{\odot}}$"]
  - validation: Cross-comparison of three mass tracers [Molecular gas mass: "We here use the \[C I\]$(1-0)$ and CO(4$-$3) lines, as well as the dust continuum emission, as three independent tracers for the molecular gas mass"]
- result: CGM [C I](1-0) flux in Q0050+0051 = 0.22 (2.7σ) ± not stated Jy km/s [3.2: "we detect a [C I]$(1-0)$ flux (luminosity) of 0.22 $\rm Jy\ km\ s^{-1}$ ((2.5 $\pm$ 0.9) $\times 10^{7}$ $\rm L_{\ensuremath{\odot}}$) at an SNR of 2.7"]
- result: CGM molecular mass Q0050+0051 = (1.0-2.8)e10 ± not stated Msun [4.3.5: "This leads to a molecular gas mass of ($1.0 - 2.8$)$\times 10^{10}$ $\rm M_{\ensuremath{\odot}}$ based on the [C I]$(1-0)$ line."]
- result: CGM mass 3σ limits other QSOs = <(0.2-1.4)e10 ± not stated Msun [4.3.5: "the resulting range in limits for the molecular gas mass in the CGM is $<$($0.2 - 1.4$)$\times 10^{10}$ $\rm M_{\ensuremath{\odot}}$"]
- result: Baryon fraction in molecular CGM = <0.4-3 ± not stated % [4.3.5: "represents $<$0.4-3$\%$ of the baryons"]
- result: Gas density of QSOs = 10^4.4-10^4.8 ± not stated cm^-3 [4.2: "we estimate a gas density in the range of $10^{4.4}-10^{4.8}\,{\rm cm^{ -3}}$ and radiation field of $10^{3.3}-10^{3.7}$"]
- result: [C I] flux Q0050+0051 QSO (12 m) = 0.89 ± 0.04 Jy km/s [Table 1: "0.89$\pm$0.04 | 382 | 1.11$\pm$0.07"]
- result: r[CI]/CO Q0050+0051 QSO = 0.36 ± 0.03 dimensionless [3.1 Individual QSOs: "The $r_{[\rm C\ I]/CO}$ values in the QSO and C1 are 0.36 $\pm$ 0.03 and 0.75 $\pm$ 0.18"]
- result: [CI]/FIR ratio Q1416+2649 = 1.1e-6 ± not stated dimensionless [4.2: "extremely low $L_{\rm [C\ I](1-0)}$/$L_{\rm FIR(SF)}$ ratio of $1.1 \times 10^{-6}$"]
- limitation (authors): CGM significance too low for individual targets; mass comparisons depend on uncertain parameters [4.3.4: "any comparison between the various tracers will be hampered by large uncertainties"]
- not stated (card): Number of clean iterations, threshold and masks in tclean; Cell and image size; Line-free channel ranges per target; Gaussian-fit procedure and peak-pixel selection details; Exact PDR model grid and fitting method for n and G0; Comparison sample compilation for Figures 6-7; Observing dates, times on source and configurations (only in Paper I)

### 2014A&A...567A.125G: Molecular line emission in NGC 1068 imaged with ALMA. I. An AGN-driven outflow in the dense molecular gas (2014; nearby_galaxies, agn_and_quasars, astrochemistry; observational_alma_primary)
- question: How are the dense molecular gas distribution, kinematics and line ratios in NGC 1068 related to AGN fueling and feedback, and does the AGN drive a molecular outflow?
- step 4: Derive X_CO
  - method: Match CO(1-0) flux (~100 Jy km/s in 10" aperture, PdBI recovers ~80%) to the dust-derived gas mass; scale for 3-2 and 6-5 via line ratios [5.4 The CO-to-H2 conversion factor: "is $\sim1/(4^{+6}_{-1})\times X_{\rm CO}^{\rm MW}$"]
  - assumption: X_CO^MW = 2e20 cm^-2 (K km/s)^-1 [5.4 The CO-to-H2 conversion factor: "$X_{\rm CO}^{\rm MW}=2\times10^{20}$cm$^{-2}$(K km s$^{-1}$)$^{-1}$"]
  - validation: Compared with LVG result of Usero et al. 2004 [5.4 The CO-to-H2 conversion factor: "A similar conclusion, pointing to an $X_{\rm CO}\sim$ a factor of 4–8 lower than $X_{\rm CO}^{\rm MW}$"]
- step 6: Estimate outflow mass, rate and energetics
  - method: Integrate CO(3-2) outside residual velocity range [-50,+50] km/s; dM/dt = 3 V_out M_mol/R_out tan(alpha); coplanar outflow tan(alpha)=1/tan(i); also L_kin and momentum flux [6.1.2 Mass outflow rate: "The mass ($M_{\rm mol}$) has been calculated from the CO(3–2) data cube, after subtraction of the projected rotation curve"]
  - parameter: R_out~1.5" (100 pc), V_out~100 km/s for CND [6.1.2 Mass outflow rate: "The average projected radial extent of the outflow in the CND is $R_{\rm out}\sim1.5\ensuremath{''}$ (100 pc)"]
  - assumption: multi-conical uniformly filled outflow; coplanar with disk; X_CO ~1/4 of MW [6.1.2 Mass outflow rate: "If we assume that the outflow is coplanar with the main disk, $\tan(\alpha)=1/\tan(i)$"]
  - validation: Dense tracers (CO 6-5, HCN, HCO+) p-v diagrams confirm outflow; compared with SFR and AGN power [6.2 The molecular outflow in dense gas …: "An inspection of this figure shows that the outflow signatures identified in CO(3–2) out to radii $r \sim 400$ pc are echoed in CO(6–5), HCN(4–3), and HCO$^+$(4–3)"]
- result: CND mass load rate of molecular outflow (coplanar) = 63 ± +21/-37 Msun/yr [6.1.2 Mass outflow rate: "then $\mathrm{d}M/\mathrm{d}t\sim63^{+21}_{-37}$ M$_{\ensuremath{\odot}}$ yr$^{-1}$"]
- result: Molecular outflow mass in CND = 1.8e7 ± +0.6/-1.1 e7 Msun [6.1.2 Mass outflow rate: "$M_{\rm mol} \sim 1.8^{+0.6}_{-1.1} \times 10^7$ M$_{\ensuremath{\odot}}$ for the CND"]
- result: Bow-shock arc outflow rate = 6 ± +2/-3.6 Msun/yr [6.1.2 Mass outflow rate: "gives $\mathrm{d}M/\mathrm{d}t \sim 6^{+2}_{-3.6}$ M$_{\ensuremath{\odot}}$ yr$^{-1}$"]
- result: Kinetic luminosity of CND outflow = 5e41 ± +1.7/-3 e41 erg/s [6.3 The powering source: "$L_{\rm kin}\sim 5^{+1.7}_{-3}\times10^{41}$ erg s$^{-1}$"]
- result: XCO relative to MW = 1/(4 +6/-1) ± +6/-1 in denominator dimensionless [5.4 The CO-to-H2 conversion factor: "is $\sim1/(4^{+6}_{-1})\times X_{\rm CO}^{\rm MW}$"]
- limitation (authors): Outflow rate is a lower limit due to limited velocity coverage [6.2 The molecular outflow in dense gas …: "should be taken as a lower limit"]
- limitation (authors): Resolution does not resolve kinematics of inner r~50 pc [8 Summary and conclusions: "we cannot spatially resolve the kinematics of the dense molecular gas in the inner $r\sim50$ pc"]
- not stated (card): Which GILDAS tasks, cleaning algorithm, mask, cell and image size were used; CASA version and calibration script details; flagging; Line-free channels used for continuum; Self-calibration solution interval and iterations; Kinemetry mask/clipping and handling of outliers beyond the listed ellipses; Details of velocity-field (moment 1) construction beyond 5 sigma clipping; BayesClumpy priors for pa…

### 2019ApJ...887...74F: ALMA Reveals a Gas-rich, Maximum Starburst in the Hyperluminous, Dust-obscured Quasar W0533-3401 at z ∼ 2.9 (2019; agn_and_quasars, high_z_galaxies; observational_alma_primary)
- question: What are the molecular gas, dust, stellar and SMBH properties of the hyperluminous obscured quasar W0533-3401, and is it a gas-rich maximum starburst in a transition phase toward an unobscured quasar?
- step 2: Derive CO luminosity and molecular gas mass
  - method: L'CO from Solomon & Vanden Bout Eq. 3; convert to CO(1-0) with r32/10=0.8; apply alpha_CO [4.1 CO(3-2) line emission: "We also adopt the CO-to-H$_2$ conversion factor, $\alpha_{\rm CO}=0.8~M_\odot$(K km s$^{-1}$ pc$^2$)$^{-1}$"]
  - assumption: r32/10 = 0.8; alpha_CO = 0.8; flat LCDM H0=70, OmegaM=0.3 [4.1 CO(3-2) line emission: "we adopt the excitation ratio between the CO$(3-2)$ and CO$(1-0)$ line of $r_{32/10} = 0.8$"]
- step 5: Dust mass, gas-to-dust ratio, SFR, depletion time, BH properties
  - method: Optically thin M_dust equation; f_gas, SFR from SED and from CO(5-4)-FIR relation; t_depl = M_gas/SFR; M_BH from L_AGN with Eddington ratio 1; Mdot_BH from L_AGN with eta/(1-eta)=0.1 [4.4 Rapid growth of both the stellar co…: "adopting $\frac{\eta}{1-\eta}=0.1$"]
  - assumption: kappa_1THz=20 cm2/g; lambda_Edd=1; L'CO(5-4)/L'CO(3-2)=0.7 [4.3 Stellar mass and star formation rate: "by taking $L'_{\rm CO(5-4)}/L'_{\rm CO(3-2)}=0.7$"]
  - validation: CO-based SFR consistent with SED SFR [4.3 Stellar mass and star formation rate: "which is generally consistent with the best-fit SED result"]
- result: L'CO(3-2) = 8.4e10 ± 0.5e10 K km/s pc^2 [4.1 CO(3-2) line emission: "$L'_{\rm CO(3-2)}=(8.4\pm0.5)\times10^{10}$ K km s$^{-1}$ pc$^2$"]
- result: Molecular gas mass = 8.4e10 ± 0.5e10 Msun [4.1 CO(3-2) line emission: "we obtain a molecular gas mass of $M_{\rm H_2}=(8.4\pm0.5)\times10^{10}\,M_\odot$"]
- result: Dust mass = 8.9e7 ± 1.6e7 Msun [Table 4: "| $M_{\rm dust}$ | (8.9 $\pm$ 1.6) $\times 10^{7}$ | $M_\odot$ | \(11\) |"]
- result: Gas-to-dust ratio = 944 ± 77 dimensionless [4.2 Dust properties: "$\delta_{\rm GDR} = 944\pm77$"]
- result: Gas fraction = 0.71 ± not stated dimensionless [4.3 Stellar mass and star formation rate: "$f_{\rm gas}=M_{\rm H_2}/(M_{\rm H_2}+M_\star)=0.71$"]
- result: Gas depletion time = 12-28 ± not stated Myr [4.3 Stellar mass and star formation rate: "We infer $t_{\rm depl}\sim 12-28$ Myr"]
- result: BH mass growth rate = 49 ± not stated Msun/yr [4.4 Rapid growth of both the stellar co…: "We infer ${\dot{M}}_{\rm BH}$ = 49 $M_\odot$ yr$^{-1}$"]
- result: M_BH/M_star (lambda_Edd=1) = 0.063 ± not stated dimensionless [4.4 Rapid growth of both the stellar co…: "($M_{\rm BH}/M_\star=0.063$)"]
- limitation (authors): Limited depth and resolution prevent distinguishing disk, merger and outflow [4.1 CO(3-2) line emission: "due to limited depth and resolution, we cannot make a solid conclusion"]
- limitation (authors): Dust mass depends strongly on the adopted kappa [4.2 Dust properties: "the largest uncertainty can arise from the adopted $\kappa_{\nu_{\rm rest}}$ value"]
- not stated (card): tclean parameters: cell size, image size, deconvolver, threshold, masking, niter; line-free channels and continuum subtraction method; CASA version and pipeline version; moment-map thresholds and aperture used for line flux and spectrum extraction; 3DBarolo settings beyond rings and width (free parameters, normalization, fit mask); bayesed sampler and likelihood details (forthcoming version not p…

### 2017ApJ...837...60B: The ALMA View of the OMC1 Explosion in Orion (2017; star_formation; observational_alma_primary)
- question: What is the structure and kinematics of the OMC1 explosive outflow in 12CO J=2-1 and how does it relate to the ejection of BN, Source I and Source n?
- step 4: Streamer density and excitation
  - method: RADEX non-LTE modelling of CO 2-1 brightness [Column densities and masses: "the radiative transfer and excitation code RADEX (cite: vanderTak2007) indicates that the CO excitation temperature in the J=2$-$1 line ranges from 25 K to 88 K"]
  - software: RADEX
  - assumption: X_CO = 1e-4 n(H2), 1.2" streamer depth, kinetic temperature 200 K, background 10 or 100 K [Column densities and masses: "Assuming cylindrical geometry, a characteristic width or depth of 1.2$''$ (500 AU), and a $^{12}$CO abundance $X_{CO} = 10^{-4} n(H_2)$"]
  - validation: Opacities checked against C18O non-detection [Column densities and masses: "These optical depths are consistent with the non-detection of C$^{18}$O at a brightness temperature above 0.2 K"]
- step 5: Mass of fast CO gas
  - method: X-factor conversion of CO flux to H2 mass, summed over 86" circle [Column densities and masses: "Integration of the CO data cube over an 86" diameter circle and summing the flux over the radial velocity ranges $-$100 to 0 km s$^{-1}$ and +20 to 120 km s$^{-1}$ implies a mass of 1.0 M$_{\odot}$"]
  - assumption: Bolatto2013 X-factor N(H2)=2.6e20 T*_A dV [Column densities and masses: "which gives $N(H_2) \approx ~2.6 \times 10^{20} ~T^*_A \Delta V$"]
  - validation: Lower bound because of interferometric filtering [Column densities and masses: "extended emission is filtered out and thus our mass estimates are lower bounds"]
- result: Mass of fast CO streamers = ~1 ± lower bound Msun [Column densities and masses: "The total mass of the streamers traced by CO having a radial velocity that differs from the ambient cloud by more than 20 km s$^{-1}$ is $M_{fast} \sim$1 M$_{\odot}$."]
- result: CO density required (kinetic T 100 K) = 1e6 to 1e7 ± not stated cm^-3 [Column densities and masses: "the acceptable volume density ranges from $\sim 10^6$ to $\sim 10^7$ cm$^{-3}$ for a background radiation temperature of 10 K"]
- limitation (authors): Missing flux from interferometer filtering; masses are lower bounds [Column densities and masses: "The spatial-filtering of the interferometer severely limits our ability to estimate masses within the inner $\pm$10 km s$^{-1}$"]
- not stated (card): CASA version; Cell size, image size, clean threshold, masks; Whether total-power data were combined; Line-free channels and continuum subtraction; Observing dates, configurations, calibrators; Method for fitting streamer lines and determining intersection points

### 2017ApJ...848..101V: A <SUP>13</SUP>CO Detection in a Brightest Cluster Galaxy (2017; galaxy_clusters_and_sz, milky_way_ism, nearby_galaxies; observational_alma_primary)
- question: Can 13CO(3-2) emission in a BCG give an LTE molecular gas mass and a CO-to-H2 conversion factor to test the Galactic value?
- step 2: Extract and fit spectra
  - method: Integrated spectrum from 6.8''x5'' box and from 13CO-tracing region, converted to brightness temperature, fitted with Gaussians; luminosities L'_CO computed [Spectra: "A spatially integrated spectrum was extracted for each spectral line from a $6.8''\times 5''$ ($13.6\times 10\rm\; kpc$) box encompassing all of the significant line emission."]
  - parameter: second 13CO component at -80 km/s below 3 sigma excluded [Spectra: "the significance of the second component is below $3\sigma$, so has not been included in these fits"]
  - fitting: single Gaussian per spectrum (two for 12CO in the 13CO-tracing region) [Spectra: "The spectra are all best fit by a single Gaussian velocity component."]
- step 4: Line ratios and excitation temperature
  - method: r31 and R32 from peak temperatures; Tex and filling factor from Rayleigh-Jeans equation assuming optically thick 12CO and LTE [CO (3-2)/(1-0): "The ratio of CO (3-2)/(1-0) brightness temperatures for the $^{13}$CO-bright component, $0.71\pm0.14$, implies an excitation temperature of $T_{\rm ex}\approx 15\rm\; K$."]
  - assumption: optically thick 12CO, same filling factor for 1-0 and 3-2, LTE [CO (3-2)/(1-0): "We also assume that the CO(1-0) and CO(3-2) emission originate from the same regions in the molecular clouds, so the area filling factors are the same."]
- step 5: LTE 13CO column density, mass and alpha_CO
  - method: 13CO column from optical depth and Tex; N(H2) via abundances; mass = 1.36 m_H2 N A_source; alpha_CO = M/L'_10 with L'_10 = L'_32/r31 [CO-to-H$_2$ Conversion Factor: "The total molecular gas mass is then computed from $M_{\rm mol} = 1.36 m_{\rm H_2} N_{\rm H_2} A_{\rm source}$"]
  - parameter: Tex=15 K, filling factor 0.1, 13W32=22.8 K km/s, A_reg=11.2 kpc^2 [CO-to-H$_2$ Conversion Factor: "For $T_{\rm ex}=15\rm\; K$, $\Phi_A=0.1$, and $^{13}W_{32}=22.8\hbox{$\rm\; K\rm\; km\rm\; s^{-1}\,$}$"]
  - assumption: [12CO]/[13CO]=50, [12CO]/[H2]=1e-4, LTE, 13CO optically thin with finite-opacity correction [CO-to-H$_2$ Conversion Factor: "Assuming the abundance ratios $[^{12}{\rm CO}]/[^{13}{\rm CO}] = 50$ and $[^{12}{\rm CO}]/[{\rm H}_2] = 10^{-4}$"]
  - validation: Optical depth cross-checked with 12CO/13CO ratio method (0.36); repeated for full region [CO-to-H$_2$ Conversion Factor: "This method yields an optical depth of $0.36$"]
- result: 13CO-traced molecular gas mass (LTE) = 2.1e9 ± not stated Msun [CO-to-H$_2$ Conversion Factor: "This gives a total molecular gas mass of $2.1\ensuremath{\times 10^{9}}\hbox{$\rm\thinspace M_{\odot}$}$."]
- result: alpha_CO (13CO-bright component) = 2.26 ± not stated Msun (K km/s pc^2)^-1 [CO-to-H$_2$ Conversion Factor: "giving a CO-to-H$_2$ conversion factor of $\alpha_{\rm CO} = 2.26\hbox{$\rm\thinspace M_{\odot}$}(\hbox{$\rm\; K\rm\; km\rm\; s^{-1}\rm\; pc^{2}\,$})^{-1}$"]
- result: X_CO = 1.04e20 ± not stated cm^-2 (K km/s)^-1 [Discussion: "$X_{\rm CO}=1.04\ensuremath{\times 10^{20}}\hbox{$\rm\; cm^{-2}\,$}(\hbox{$\rm\; K\rm\; km\rm\; s^{-1}\,$})^{-1}$"]
- result: Total CO(1-0) flux = 8.06 ± 0.08 Jy km/s [Table 1: "$8.06\pm0.08$"]
- result: r31 (13CO-bright component) = 0.71 ± 0.15 dimensionless [CO (3-2)/(1-0): "The resulting $r_{31}$ line ratio is $0.71\pm0.15$ for the $^{13}$CO-bright velocity component"]
- result: R32 (13CO-bright, 13CO-tracing region) = 3.32 ± 0.66 dimensionless [Table 1: "$3.32\pm0.66$"]
- result: 13CO column density = 1.74e17 ± not stated cm^-2 [CO-to-H$_2$ Conversion Factor: "the total $^{13}$CO column density is $1.74\ensuremath{\times 10^{17}}\hbox{$\rm\; cm^{-2}\,$}$"]
- result: Total molecular gas mass with Galactic factor or alpha scaling = 1.1e10 ± not stated Msun [CO-to-H$_2$ Conversion Factor: "the total CO(1-0) luminosity gives a total molecular gas mass of $1.1\ensuremath{\times 10^{10}}\hbox{$\rm\thinspace M_{\odot}$}$"]
- limitation (authors): Mass traced is only a fraction of total; LTE and abundance assumptions are simplistic [CO-to-H$_2$ Conversion Factor: "As a result, this LTE analysis is only sensitive to a fraction of the total molecular gas mass."]
- not stated (card): Number of tclean/clean iterations, threshold and masks; Line-free channels used for uvcontsub and continuum fit order; Flux calibrator and flux scale uncertainty; Pipeline version; Image size and cell size; Exact extraction polygon for the region tracing 13CO; Details of the Monte Carlo and Gaussian fitting method (fitter, errors); Whether the 2011/2012 archival projects were used and how

### 2015ApJ...812L..23S: A Higher Efficiency of Converting Gas to Stars Pushes Galaxies at z ∼ 1.6 Well Above the Star-forming Main Sequence (2015; high_z_galaxies; observational_alma_primary)
- question: Do high-redshift (z~1.6) starbursts, selected as outliers above the star-forming main sequence, convert gas to stars with higher efficiency than main-sequence galaxies?
- step 2: Compare L'CO/L_TIR with the main sequence
  - method: Convert to CO(1-0), plot L'CO vs L_TIR and normalised ratios against the Sargent2014 compilation [CO-to-IR ratio: "All line luminosities are converted to CO (1-0) using values of 0.85 and 0.7, respectively for CO (2-1) and CO (3-2)"]
  - validation: Tested alternative excitation corrections [CO-to-IR ratio: "Different excitation corrections than those applied here would not impact our results"]
- step 3: Gas masses and alpha_CO from dynamical mass
  - method: M_dyn = 5 sigma^2 r_1/2 / G; subtract half the stellar mass and dark matter to get gas mass, for the two resolved sources [Gas masses, $\alpha_{\rm CO}$, and SFE: "$$\begin{equation} M_{\rm dyn}(r<r_{\rm 1/2}) \simeq \frac{5 \sigma^2 r_{\rm 1/2}}{G} \label{eq1} \end{equation}$$"]
  - assumption: Spherical symmetry; dark matter M_DM = 0.25 M_dyn [Gas masses, $\alpha_{\rm CO}$, and SFE: "a dark matter component ($M_{\rm DM}=0.25\times$ $M_{dyn}$; (cite: Daddi2010a))"]
  - validation: Compared with alpha_CO of GN20 and merger values; metallicity check [Gas masses, $\alpha_{\rm CO}$, and SFE: "both not far from those found for the high-redshift submillimeter galaxies in the proto-cluster GN20 (cite: Tan2014) and consistent with lower conversion factors for galaxies in mergers (cite: Narayanan2011)"]
- step 4: Gas masses for unresolved sources
  - method: Apply the average alpha_CO = 1.1 to the CO luminosities [Gas masses, $\alpha_{\rm CO}$, and SFE: "using the average ($\alpha_{\rm CO}=1.1$ M$_{\odot}$ / K km s$^{-1}$ pc$^{-2}$) value of the two estimates"]
  - validation: Checked metallicity via mass-metallicity relation and BPT diagram [Gas masses, $\alpha_{\rm CO}$, and SFE: "In Figure [4](#fig:emlines)$a$, we show the mass-metallicity relation at $z\sim1.6$ (cite: Zahid2014) based on \[NII\]$\lambda6585$/H$\alpha$, with our sample shown in red."]
- result: Median L'CO/<L'CO>_MS = 0.60 ± 0.04 dimensionless [CO-to-IR ratio: "We measure a median value of $L^\prime_{\rm CO}/<L^\prime_{\rm CO}>_{\rm MS}=0.60\pm0.04$ for our sample."]
- result: Gas mass PACS-819 = 2.0e10 ± 1.2e10 Msun [Gas masses, $\alpha_{\rm CO}$, and SFE: "$2.0\pm1.2 \; (6.2\pm2.2)\times10^{10}$ M$_{\odot}$"]
- result: Gas mass PACS-830 = 6.2e10 ± 2.2e10 Msun [Gas masses, $\alpha_{\rm CO}$, and SFE: "$2.0\pm1.2 \; (6.2\pm2.2)\times10^{10}$ M$_{\odot}$"]
- result: alpha_CO PACS-819 = 0.6 ± 0.3 Msun/(K km/s pc^2) [Gas masses, $\alpha_{\rm CO}$, and SFE: "we estimate $\alpha_{\rm CO}=0.6\pm0.3$ for PACS-819 and $1.6\pm0.6$ for PACS-830"]
- result: alpha_CO PACS-830 = 1.6 ± 0.6 Msun/(K km/s pc^2) [Gas masses, $\alpha_{\rm CO}$, and SFE: "we estimate $\alpha_{\rm CO}=0.6\pm0.3$ for PACS-819 and $1.6\pm0.6$ for PACS-830"]
- result: Gas fractions = 28-52% ± not stated percent [Gas masses, $\alpha_{\rm CO}$, and SFE: "gas fractions $f_{\rm gas}=M_{\rm gas} / (M_{\rm gas} + M_{*}$) between 28 and 52%"]
- limitation (authors): alpha_CO uncertain; metallicity of ionised gas may not represent molecular gas; AGN cannot be excluded [Gas masses, $\alpha_{\rm CO}$, and SFE: "we cannot rule out the presence of a low-to-moderate luminosity AGN"]
- not stated (card): CASA version and calibration procedure/pipeline; Bandpass and phase calibrator names; Imaging parameters (weighting, cell size, deconvolution); uvfit settings and line integration window; How L_TIR, SFR and M* were computed in detail

### 2018ApJ...854..130W: The Orbit of the Companion to HD 100453A: Binary-driven Spiral Arms in a Protoplanetary Disk (2018; protoplanetary_disks, stellar_physics; multi_facility_alma_minor)
- question: What is the orbit of the companion HD 100453B, and is it consistent with driving the spiral arms and truncating the disk of HD 100453A?
- step 2: Fit disk kinematics to ALMA CO visibilities
  - method: RADMC-3D synthetic 12CO 2-1 channel maps Fourier transformed and fit to visibilities with MCMC [3.2 CO 2–1 Modelling: "Those synthetic channel maps are Fourier Transformed and fit directly to the visibilities using the MCMC fitting package `emcee`"]
  - software: RADMC-3D, emcee
  - parameter: Free: M_disk, r_c, gamma, T0, q, xi, v_sys, inclination, PA [3.2 CO 2–1 Modelling: "the density, temperature, and velocity structure of the system are described by the following parameters: $M_{\rm disk}$, $r_{\rm c}$, $\gamma$, $T_0$, $q$, $\xi$, and $v_{sys}$."]
  - assumption: M*=1.7 Msun, d=103 pc, X_CO=1e-4, mu=2.37, inner radius 0.1 AU, Keplerian, vertically isothermal, single plane [3.2 CO 2–1 Modelling: "Here we fix the stellar mass to a value of $M_* = 1.7$ $M_{\odot}$ and the distance to a value of $d = 103$ pc"]
  - fitting: emcee with uniform priors for all parameters [3.2 CO 2–1 Modelling: "with uniform priors for all parameters"]
  - validation: Compared moment maps and residuals; inclination consistent with NIR estimates [4.3.2 ALMA Disk Kinematic Modelling: "is consistent with the independent measurements from the NIR images (Figure 5)"]
- result: Disk inclination from CO = 27.6 ± 0.2 deg [Table 3: "$i_{Disk}$ ($^{\circ}$) | 27.6 | 0.2"]
- result: Disk position angle = 55.0 ± 0.5 deg [Table 3: "$PA$ ($^{\circ}$) | 55.0 | 0.5"]
- result: Systemic velocity = 5.25 ± 0.01 km/s [Table 3: "$v_{sys}$ (km/s) | 5.25 | 0.01"]
- result: Disk gas mass (model) = 7.0e-6 ± 1.0e-6 Msun [Table 3: "$M_{Disk}$ (M$_{\odot}$) | 7.0$\times 10^{-6}$ | 1.0$\times 10^{-6}$"]
- limitation (authors): Simple model cannot capture inner structures or warp; uncertainties exclude model assumptions [4.3.2 ALMA Disk Kinematic Modelling: "our simple model cannot capture all of the disk features that result in the observed CO emission profile."]
- not stated (card): CASA version and pipeline version; CLEAN threshold, mask, image size and cell size; Whether continuum was subtracted and which channels were line-free; Priors ranges for MCMC parameters and walker/step numbers; Fixed parameters of the CO model such as outer radius, flaring, and CO depletion; Initial disk mass and parameters of hydrodynamic simulation beyond h/r and alpha

### 2021A&A...652A..98G: The Galaxy Activity, Torus, and Outflow Survey (GATOS). I. ALMA images of dusty molecular tori in Seyfert galaxies (2021; agn_and_quasars, nearby_galaxies; large_program_or_survey)
- question: What are the sizes, orientations, masses and gas properties of dusty molecular tori in nearby Seyferts, and does AGN feedback leave an imprint on the radial distribution of molecular gas?
- step 4: Derive molecular gas masses from dust and CO
  - method: Modified blackbody dust mass with gas-to-dust 100; CO mass via Bolatto et al. Eq. 3 with 1.36 He factor; compared dust-based and CO-based masses [4.4: "The CO-based molecular gas masses derived from Equation (3) of (cite: Bol13), after including the mass of Helium"]
  - parameter: T_dust=100 K; kappa_351GHz=0.0865 m^2/kg; gas-to-dust ~100; X_CO=2e20; 3-2/1-0 = 2.9 (tori), 0.7 (FOV), 2.0 (200 pc) [4.4: "We assumed a dust temperature $T_{\rm dust} \sim T_{\rm gas}=100$ K and a dust emissivity $\kappa_{{\rm 351~GHz}}=0.0865$ m$^2$ kg$^{-1}$ (cite: Kla01)"]
  - assumption: Galactic X_CO [4.4: "we assumed a galactic CO–to–H$_2$ conversion factor ($X_{\rm CO}=2\times10^{20}$mol cm$^{-2}$ (K km s$^{-1}$)$^{-1}$)"]
  - validation: Dust vs CO masses agree to ~0.23 dex median; Pearson ~0.74 excluding NGC 7213 [4.4: "their median values differ only by $\sim0.23$ dex"]
- step 9: Gas concentration indices vs AGN luminosity
  - method: Compute Sigma_H2 at r<=50 pc, torus scale, and r<=200 pc; indices as log ratios; Spearman, Kendall, Pearson tests vs L_2-10keV and Eddington ratio [8.1: "We normalized the nuclear surface densities $\Sigma_{\rm H_2}^{\rm 50pc}$ and $\Sigma_{\rm H_2}^{\rm torus}$ to the H$_{\rm 2}$ surface densities measured on ’circumnuclear’ scales"]
  - assumption: 3-2/1-0 ratios ~2.0 (circumnuclear) and ~2.9 (nuclear); Milky Way X_CO [8.1: "we assumed slightly different 3–2/1–0 brightness temperature ratios of $\sim2.0$ and $\sim2.9$, respectively"]
  - validation: Systematic uncertainty ±0.20 dex from conversion factors [8.1: "Under these extreme hypotheses the total uncertainty amounts to $\pm$0.20 dex"]
- result: Molecular gas mass of extended components, median = ~6e5 ± range ~5e4-1e7 Msun [4.4: "a median value of $\sim6\times10^{5}$M$_{\ensuremath{\odot}}$"]
- result: Median difference log M_gas(dust) vs M_gas(CO) = 0.23 ± not stated dex [4.4: "their median values differ only by $\sim0.23$ dex"]
- result: Pearson correlation M_dust vs M_CO (excluding NGC 7213) = ~0.74 ± p~6e-3 dimensionless [4.4: "show Pearson correlation parameters $\sim+0.74$ and two-sided $p$ values $\sim6\times10^{-3}$"]
- result: Spearman rho, index-II vs log L(2-10keV) = -0.79 ± p=1e-4 dimensionless [Table 7: "$\rho_{\rm Sp}$=**–0.79** , $p$=${\bf 10^{-4}}$"]
- result: Gas concentration index-I variation across sample = ~1 ± not stated dex [8.1: "the gas concentration measured by index-I changes by $\sim1$ dex across the sample"]
- result: Gas concentration index-II variation across sample = ~2 ± not stated dex [8.1: "The corresponding decrease is of $\sim$2 dex for index-II."]
- limitation (authors): Common T_dust adopted for all sources; mass estimates depend on assumed conversion factors [4.4: "In the absence of estimates for each galaxy, we were constrained to adopt a common $T_{\rm dust}$ for all sources"]
- limitation (authors): Spectral index maps only possible for 3 sources [4.3: "meaningful spectral index maps cannot be obtained for the rest of the GATOS galaxies"]
- limitation (authors): Small-number statistics for orientation and correlations [4.5: "Within the limits imposed by the sparse statistics"]
- not stated (card): Exact line-free channels / velocity masks per target; CASA version and pipeline details, calibrators; Cell size, image size, deconvolution and cleaning thresholds in GILDAS; How CO/dust masses were integrated (apertures, noise masks); Details of the 1D-Gaussian strip fits (initial guesses); Subtraction of point source in spectral index maps and beam matching details; XSPEC fit priors/start values…

### 2024ApJ...961..228S: Ring Gap Structure around Class I Protostar WL 17 (2024; star_formation, protoplanetary_disks; archival_reuse)
- question: Does the Class I protostar WL 17 have a ring-hole or a ring-gap structure, is an outflow associated with it, and what do these imply for ring formation timescale and planet formation?
- step 4: Outflow velocity, timescale, mass, mass-loss rate
  - method: PV diagrams give v_max; t_dyn = r_out/v_max tan(i); M_out = mu m_H A N_ave with N = X_CO W_CO; Mdot = M_out/t_dyn [3.3 Outflow Physical Quantities: "Next, we estimate the outflow mass $M_{\rm out}$ as $M_{\rm out} = \mu m_{\rm H} AN_{\rm ave}$"]
  - parameter: Outflow area: intensity > 0.5 K km/s; v_sys = 4 km/s; i_out = i_ring [3.3 Outflow Physical Quantities: "the areas surrounded by white lines indicate outflow areas with intensities exceeding 0.5 K km s$^{-1}$"]
  - assumption: mu = 2.8; X_CO = 2.0e20; protostellar mass 1 Msun for Keplerian; constant mass loss rate [3.3 Outflow Physical Quantities: "We used a protostellar mass of $1{M}_\odot$ for calculating the physical quantities for the WL 17 system below."]
  - validation: Compared with van der Marel et al. 2013 values [3.3 Outflow Physical Quantities: "The outflow mass derived in this study is comparable to that in (cite: van_der_Marel_2013)."]
- result: Outflow total mass = 8.7e-4 ± not stated Msun [3.3 Outflow Physical Quantities: "The total mass of the blue-shifted and red-shifted outflows is $M_{\rm out,total}=$8.7$\times$10$^{-4}\, M_{\odot}$"]
- result: Outflow max velocities (blue, red) = 2.0 and 3.5 ± not stated km/s [3.3 Outflow Physical Quantities: "$v_{\rm blue,max}=$2.0$\,{\rm km\,s^{-1}}$ and $v_{\rm red,max}=$3.5$\,{\rm km\,s^{-1}}$"]
- result: Mean outflow dynamical timescale = 3.0e3 ± not stated yr [3.3 Outflow Physical Quantities: "is $t_{\rm dyn}=$ 3.0 $\times 10^3$ yr"]
- result: Total outflow mass ejection rate = 3.6e-7 ± not stated Msun/yr [3.3 Outflow Physical Quantities: "we estimated the total mass loss rate (sum of the red and blue shifted outflows) of 3.6$\times$10$^{-7}$ $M_{\odot}$ yr$^{-1}$"]
- limitation (authors): Protostellar mass is uncertain because Keplerian motion cannot be separated from the jet [4.5 Uncertainty in Timescale Estimation: "Thus, in this study, the protostellar mass is uncertain and cannot be determined accurately."]
- limitation (authors): Outflow mass and velocity are likely underestimated; field of view limits outflow length [4.5 Uncertainty in Timescale Estimation: "Thus, we will likely underestimate both the mass and velocity of the outflow."]
- not stated (card): Spectral window/channel ranges used for continuum vs line, and line-free channels for imcontsub; Image size (pixels) and deconvolution settings (deconvolver, threshold, mask, niter); Calibrators and flux scale; whether the pipeline or manual scripts were used; Rest frequencies and the velocity range used to define the blue/red outflow moment maps; Exact outflow area definition, 0.5 K km/s contour…

### 2025ApJ...984L..19Y: exoALMA. XIV. Gas Surface Densities in the RX J1604.3−2130 A Disk from Pressure-broadened CO Line Wings (2025; protoplanetary_disks; observational_alma_primary)
- question: What is the radial gas surface density and midplane pressure profile of the J1604 transition disk, derived from pressure-broadened CO J=3-2 line wings, and what does it imply for dust trapping, turbulence and planet formation?
- step 4: Fit radial gas surface density with pressure-broadened line model
  - method: Radiative transfer with Voigt opacity, layered vertical temperature, hydrostatic H2, continuum absorption; fit each radius [3.2 Modeling the spectra: "The convolved synthetic spectrum at each radius $r$ is then compared with the azimuthally stacked spectrum at the same radius."]
  - software: emcee
  - parameter: 7 free parameters; T100 = 14 K fiducial and 30 K high case; X_CO = 1e-4; mu = 2.37 [3.2 Modeling the spectra: "In our model fitting procedure, we fix $T_{\rm 100} = 14$ K as a fiducial case."]
  - assumption: X_CO = 1e-4 tentatively; CO in gas phase at midplane; vertically constant X_CO [3.2 Modeling the spectra: "We tentatively assume $X_{\rm CO}=10^{-4}$ for fitting and discuss possible uncertainties in the following sections."]
  - fitting: Uniform priors; 2000 steps x 32 walkers, then re-initialized 6000-step run discarding first 3000; median adopted [3.2 Modeling the spectra: "We re-run MCMC sampling for 6000 steps and check that the chains are well converged."]
  - validation: Gaussian-opacity fit leaves significant wing residuals; factor-2 changes in Sigma_g fail to match wings [3.2 Modeling the spectra: "We confirm that the spectra cannot be well-fitted without pressure-broadening."]
- step 5: Constrain X_CO and peak gas surface density via Toomre Q and literature range
  - method: Require Q>1 at gas peak and combine with 1e-6<X_CO<1e-3 [4.1 Gas surface density profile: "If we assume $Q > 1$ at the peak of the gas surface density, we can obtain $X_{\rm CO} > 7 \times 10^{-4}$."]
  - assumption: Disk gravitationally stable (no spirals) [4.1 Gas surface density profile: "there is no significant asymmetric structure such as a spiral arm in the J1604 disk, suggesting the disk is gravitationally stable"]
- step 6: Estimate turbulence alpha and fragmentation velocity
  - method: Steady-state advection-diffusion dust profile compared with observed dust ring width for three alpha; v_frag from St_max and alpha [4.2 Turbulence and dust fragmentation: "When $\alpha_{\rm turb}$ is set to $2\times10^{-4}$, the observed width of the dust ring is well reproduced."]
  - parameter: a_rep = 0.6 mm from a_max = 1.4 mm; X_CO = 7e-4; alpha = 1e-3, 2e-4, 4e-5 [4.2 Turbulence and dust fragmentation: "We adopt $a_{\rm rep} = 0.6\ {\rm mm}$ by converting $a_{\rm max} = 1.4\ {\rm mm}$"]
- result: Peak gas surface density (fiducial T, X_CO=1e-4) = ~80 (X_CO/1e-4)^-0.5 ± not stated g cm^-2 [4.1 Gas surface density profile: "The maximum value at $r\sim87$ au is $\sim80 (X_{\rm CO}/10^{-4})^{-0.5}\ {\rm g\ cm^{-2}}$"]
- result: Peak gas surface density (conclusion) = 18-44 ± not stated g cm^-2 [4.1 Gas surface density profile: "we conclude the peak gas surface density of $18-44\ {\rm g\ cm^{-2}}$ with $1.6 \times 10^{-4} < X_{\rm CO} < 10^{-3}$"]
- result: Gas mass within 50<r<110 au = 0.05-0.1 ± not stated Msun [4.1 Gas surface density profile: "gas mass within $50<r<110$ au of $0.05-0.1\ {\rm M_\odot}$"]
- result: Gas-to-dust ratio at ring peak = 70-400 ± not stated dimensionless [4.1 Gas surface density profile: "we estimate the gas-to-dust surface density ratio at the dust surface density peak to be $70-400$"]
- result: Midplane pressure peak (fiducial) = ~21 (X_CO/1e-4)^-0.5 at r~80 au ± not stated microPa [4.1 Gas surface density profile: "The $P_{\rm mid}$ profile peaks at $r\sim80$ au with $\sim21(X_{\rm CO}/10^{-4})^{-0.5}\ {\rm \mu Pa}$"]
- result: Turbulence alpha_turb = ~2e-4 ± not stated dimensionless [4.2 Turbulence and dust fragmentation: "When $\alpha_{\rm turb}$ is set to $2\times10^{-4}$, the observed width of the dust ring is well reproduced."]
- result: Fragmentation velocity = ~1 ± not stated m s^-1 [4.2 Turbulence and dust fragmentation: "$v_{\rm frag}$ is estimated to be $\sim 1\ {\rm m\ s^{-1}}$ at the dust ring"]
- result: Planet mass from gap depth = 0.1-2 ± not stated Mjup [4.1 Gas surface density profile: "we can estimate the mass of the planet of $0.1-2\ M_{\rm jup}$ for a range of turbulence parameter $\alpha = 10^{-4}-10^{-2}$"]
- limitation (authors): CO/H2 ratio uncertain; absolute gas surface density scales as X_CO^-0.5 [6 Summary: "We note that the CO/H$_2$ ratio remains uncertain in this study."]
- limitation (authors): Dust opacity model uncertainty affects gas-to-dust ratio; limited spatial resolution [4.4 Caveats: "there might be a large uncertainty in the dust opacity model."]
- not stated (card): Exact exoALMA CO cube parameters (robust, taper, continuum subtraction) are only by reference to Loomis et al.; Likelihood and noise definition for the CO spectral fit (per-channel noise estimate, fit velocity range) not specified; Which radii/annuli spacing used for fits and how radial profiles are averaged/errors defined; Band 7 continuum image details and absolute flux handling; Details of Too…

### 2024A&A...691A.178B: KASHz+SUPER: Evidence of cold molecular gas depletion in AGN hosts at cosmic noon (2024; agn_and_quasars, high_z_galaxies; archival_reuse)
- question: Do X-ray-selected AGN hosts at cosmic noon (z=1-2.6) have lower cold molecular gas content (CO luminosity, gas fraction) than matched non-active galaxies?
- step 3: Convert to CO(1-0) luminosity
  - method: L'CO equation of Carilli & Walter with AGN line ratios r21=0.68, r31=0.59, r41=0.37 [4.2: "assuming the line ratios measured for a sample of IR-selected AGN up to $z\simeq4$"]
  - assumption: Control sample uses r21=0.6, r31=0.5 [3: "retrieve the CO(1-0) using $r_{21}=0.6$ and $r_{31}=0.5$"]
- step 6: Bayesian bisector fits and gas fraction distributions
  - method: OLS bisector in Bayesian framework, Gaussian likelihood with error-function upper limits, uniform priors, intrinsic scatter free; hierarchical Gaussian for fgas [5.1: "Upper limits were included in the likelihood function as error functions (cite: lamperti2019)"]
  - software: emcee, scipy
  - fitting: emcee ensemble MCMC, scipy.optimize initial guess, median and 16/84 percentiles [5.1: "We then sample the yielded likelihood function through the `emcee` library"]
  - validation: Repeat with only well-matched samples and MS-only targets; KS test [5.3: "This result holds in both parameter spaces also when excluding non-active galaxies and AGN hosts without a proper match in the other sample"]
- step 7: Compare to simulations
  - method: Filter TNG/EAGLE/Simba at z=2: 10<logM*<11.7, logSFR 0.7-2.8, logLbol>44.3, lambda_Edd>1% for AGN, <0.1% for non-active; fH2=alphaCO fgas [6: "We use $\log{L_{\rm bol}}>44.3$ erg s$^{-1}$to span the same bolometric luminosity range as our observations"]
  - assumption: alpha_CO=3.6 (and 0.8 shown) [6: "we present the comparison between observed data and simulations assuming $\alpha_{\rm CO}=3.6"]
- result: AGN LCO-LFIR slope m = 1.16 ± +0.15/-0.12 dimensionless [Table bisector fits: "$1.16_{-0.12}^{+0.15}$"]
- result: Non-active LCO-LFIR slope m = 0.99 ± +0.07/-0.06 dimensionless [Table bisector fits: "$0.99 ^{+0.07}_{-0.06}$"]
- result: Mean log(L'CO/M*) AGN = -1.09 ± +0.21/-0.19 dex [Table bisector fits: "$-1.09^{+0.21}_{-0.19}$"]
- result: Mean log(L'CO/M*) non-active = -0.62 ± +0.07/-0.06 dex [Table bisector fits: "$-0.62^{+0.07}_{-0.06}$"]
- result: KS p-value of fgas distributions = <1e-7 ± not stated dimensionless [5.2: "significantly different according to the KS test (p-value \< $10^{-7}$)"]
- limitation (authors): Different AGN and galaxy timescales, spatial scales, many upper limits, alpha_CO unknown [7: "First, we are comparing two phenomena that occur on very different timescales"]
- not stated (card): Channel ranges used for line-free continuum identification per source; Exact spectrum extraction apertures per source; MCMC settings (walkers, steps, convergence) for emcee; Prior ranges for the uniform priors; Control-sample CO fluxes from PHIBSS were private communication; Simulation catalog selections and H2 post-processing details

### 2015A&A...581A..85P: The jet and the disk of the HH 212 low-mass protostar imaged by ALMA: SO and SO<SUB>2</SUB> emission (2015; star_formation, astrochemistry; observational_alma_primary)
- question: What are the physical and dynamical properties of the molecular jet and the disk of HH 212, as traced by SO and SO2, and what are the SO and SO2 abundances?
- step 3: Constrain SO excitation and jet column density/abundance
  - method: RADEX grids compared to SO line ratio and intensities; then LTE optically thin N_SO and N_CO; X_SO = X_CO N_SO/N_CO [4.2 SO and SO2 abundance in the jet: "Then, the abundance of SO is derived as $X_{\rm SO} = X_{\rm CO} \times N_{\rm SO} / N_{\rm CO}$"]
  - software: RADEX
  - parameter: TK = Tex = 50-500 K; nH2 1e5-1e7 cm-3 [4.2 SO and SO2 abundance in the jet: "kinetic temperatures ($T_{\rm K} = 50 -500$ K) and H$_2$ densities ($n_{H_2}$ from $10^{5}$ to $10^{7}$ cm$^{-3}$)"]
  - assumption: X_CO = 1e-4; CO optically thin (lower limit in B2) [4.2 SO and SO2 abundance in the jet: "the abundance of CO with respect to H$_2$ is assumed to be $X_{\rm CO} = N_{\rm CO} / N_{\rm H_2} = 10^{-4}$"]
  - validation: RADEX with n=3e5 gives factor 2-4 higher columns [4.2 SO and SO2 abundance in the jet: "are from a factor 2 (for $T_{\rm K} = 500$ K) to a factor 4 (for $T_{\rm K} = 50$ K) larger than in the LTE-optically thin case"]
- step 4: Jet density and mass loss rate
  - method: NH2 from NCO; cylinder geometry for nH2; Mdot = 1/3 m_H2 (N_CO/X_CO) HPBW_tr V_jet [4.3 Jet physical and dynamical properti…: "$\dot{M}_{\rm jet} = 1/3 \times m_{\rm H_2} \times (N_{\rm CO} / X_{\rm CO}) \times HPBW_{\rm tr} \times V_{\rm jet}$"]
  - parameter: V_jet ~165 km/s; HPBW_tr = 0.47''; jet width ~90 AU [4.3 Jet physical and dynamical properti…: "($V_{\rm jet} \sim 165$ km s$^{-1}$) and $HPBW_{\rm tr}$ is the beam size across the jet width ($HPBW_{\rm tr} = 0.47\ensuremath{''}$)"]
  - assumption: compression factor ~3, uncertain by factor ~3 [4.3 Jet physical and dynamical properti…: "therefore the $\dot{M}_{\rm jet}$ values are affected by a factor $\sim 3$ uncertainty"]
- step 5: Disk mass and SO abundance
  - method: RADEX for SO 10-10 and ratio; LTE optically thin SO and C17O columns over |V-Vsys|=1.9-3.5 km/s; disk mass from C17O over beam area, blue+red lobes [4.4 Disk properties: mass and SO abunda…: "$M_{\rm disk} \sim \left( 1.4 \times m_{\rm H_2} \times (N_{\rm C^{17}O} / X_{\rm C^{17}O}) \times A_{\rm beam} \right)_{\rm blue + red}$"]
  - software: RADEX
  - parameter: beam dilution factor ~8; R_disk ~90 AU [4.4 Disk properties: mass and SO abunda…: "strongly diluted in the $0.65\ensuremath{''} \times 0.47\ensuremath{''}$ beam (dilution factor $\sim 8$)"]
  - assumption: C17O/CO=1/1792, X_CO=1e-4, Tex 50-500 K, factor 1.4 for He [Table 2: "We assume optically thin emission at LTE with $T_{\rm ex} = 50-500$ K."]
  - validation: Compared with disk mass 0.014 Msun from HCO+ [4.4 Disk properties: mass and SO abunda…: "This value is close to the disk mass of $0.014$ M$_{\odot}$ estimated by (cite: lee14) from HCO$^{+}$ $4-3$."]
- result: Jet mass loss rate = >=0.2-2e-6 ± factor ~3 Msun/yr [4.3 Jet physical and dynamical properti…: "$\dot{M}_{\rm jet} \ge 0.2 - 2 \times 10^{-6}$ M$_{\odot}$ yr$^{-1}$"]
- result: Jet ejection efficiency Mdot_jet/Mdot_inf = >=0.03-0.3 ± not stated dimensionless [4.3 Jet physical and dynamical properti…: "$\dot{M}_{\rm jet}/\dot{M}_{\rm inf} \ge 0.03-0.3$"]
- result: SO abundance in jet = ~1e-7 to 2e-6 ± temperature range 50-500 K dimensionless [4.2 SO and SO2 abundance in the jet: "($X_{\rm SO} \sim 10^{-7}-2 \times 10^{-6}$)"]
- result: SO2/SO ratio in jet = ~0.5-4 ± not stated dimensionless [4.2 SO and SO2 abundance in the jet: "we find SO$_2$/SO$\sim 0.5-4$ in HH 212"]
- result: Disk mass = >=0.002-0.013 ± not stated Msun [4.4 Disk properties: mass and SO abunda…: "The disk mass turns out to be $\sim 0.002 - 0.013$ M$_{\odot}$."]
- result: SO abundance in disk = ~1e-8 to 1e-7 ± not stated dimensionless [4.4 Disk properties: mass and SO abunda…: "$X_{\rm SO} = X_{\rm C^{17}O} \times N_{\rm SO} / N_{\rm C^{17}O} \sim 10^{-8} - 10^{-7}$"]
- result: Fraction of sulfur in SO and SO2 in jet = 1% to 40% ± not stated percent [4.2 SO and SO2 abundance in the jet: "from 1% up to 40% of the elemental S is in the form of SO and SO$_2$ in the HH 212 jet"]
- limitation (authors): Resolution too low to fully resolve the disk; edge-on view unfavourable [4.4 Disk properties: "The angular resolution ($\sim 0.5\ensuremath{''}$) is too low to fully resolve the disk"]
- limitation (authors): Mass loss rate is a lower limit and uncertain by factor ~3; SO data cannot constrain density and temperature [4.2 SO and SO2 abundance in the jet: "the avalaible SO observations do not allow constraining the density and temperature of the emitting gas"]
- not stated (card): ALMA project code and archive MOUS/data location; CASA version and calibration script details; Imaging parameters (weighting, robust, cell, image size, deconvolver, masks); Continuum subtraction and line-free channels; Primary beam correction; Exact beam-dilution factor derivation and RADEX input grids/collision data files; Knot extraction aperture/position coordinates; Absolute flux scale uncert…

### 2019ApJ...885L..39H: First Detection of Submillimeter-wave [<SUP>13</SUP>C I] <SUP>3</SUP> P <SUB>1</SUB>-<SUP>3</SUP> P <SUB>0</SUB> Emission in a Gaseous Debris Disk of 49 Ceti w… (2019; debris_disks, astrochemistry; archival_reuse)
- question: Can the [13C I] 3P1-3P0 F=3/2-1/2 hyperfine line be detected in the 49 Ceti gas disk, and what does the [C I]/[13C I] ratio imply for [C I] optical depth?
- step 1: Image the [C I] cube
  - method: Reduced with CASA 5.5.0, Briggs weighting +0.5 [Dataset: "Data reduction was performed by using version 5.5.0 of the Common Astronomy Software Applications (CASA) package (cite: mcm07)."]
  - software: CASA
- step 2: Extract spectra at six positions and identify [13C I]
  - method: Spectra averaged over 0.5 arcsec circles; compare with [C I] spectrum scaled by 1/12 and shifted by -2.2 km/s [Detection of [13C I] 3P1-3P0 line emiss…: "The overlaid spectra with pink color show the [C I] spectra whose intensity is scaled by 1/12 and whose velocity is blue-shifted by 2.2 km s$~^{-1}$"]
  - software: CASA
  - validation: Visual match of scaled [C I] spectrum to faint feature [Detection of [13C I] 3P1-3P0 line emiss…: "The overlaid spectra well correspond to the faint features."]
- step 3: Derive optical depth
  - method: Use intensity ratio and hyperfine relative intensities [[C I] and [13C I] intensity ratio: "The peak optical depth ($\tau$) of the [C I] emission is roughly estimated to be 10$\pm$3 by considering the relative intensities of the hyperfine components."]
  - assumption: 12C/13C = 77; Tex of [13C I] equals that of [C I] [[C I] and [13C I] intensity ratio: "Here, we assumed the excitation temperature of [$^{13}$C I] is identical to that of [C I]."]
- step 4: Derive N(C) and TK with non-LTE
  - method: RADEX optimized to reproduce [C I] intensity and optical depth [[C I] and [13C I] intensity ratio: "We optimized these two parameters to reproduce the [C I] intensity and its optical depth (10$\pm$3) derived above."]
  - software: RADEX
  - parameter: H2 density 10^4 cm^-3; velocity width 1 km/s [[C I] and [13C I] intensity ratio: "Here, the velocity width is assumed to be 1 km s$^{-1}$."]
  - assumption: Electron collisions ignored [[C I] and [13C I] intensity ratio: "we ignored it for [C I] in this calculation"]
- result: [C I]/[13C I] intensity ratio = 12 ± ±3 dimensionless [abstract: "The [C I]/[13C I] line intensity ratio is found to be 12$\pm$3"]
- result: [C I] peak optical depth = 10 ± ±3 dimensionless [[C I] and [13C I] intensity ratio: "estimated to be 10$\pm$3"]
- result: Kinetic temperature = 18 ± ±7 K [[C I] and [13C I] intensity ratio: "$T{\rm_{K}}$ = 18$\pm$7 K"]
- result: N(C) = 1.5e18 ± ±1.0e18 cm^-2 [[C I] and [13C I] intensity ratio: "$N$(C) = (1.5$\pm$1.0) $\times$ 10$^{18}$ cm$^{-2}$"]
- limitation (authors): Southeast positions not definitively detected due to [C I] wing contamination; 12C/13C may exceed 77 so tau is a lower limit [Detection of [13C I] 3P1-3P0 line emiss…: "we cannot detect the [$^{13}$C I] line definitively, because of the heavy contamination of the wing component"]
- not stated (card): Calibration and imaging details (cell size, image size, deconvolver, masking, continuum subtraction, line-free channels); Exact positions of the six spectral extraction circles; Array configuration, spectral setup and on-source time; How the 12±3 ratio and its uncertainty were computed; RADEX line width/collision data and optimization method

### 2019BAAA...61..134V: Molecular Clouds resolved with ALMA ^{12}CO J=1-0 and J=2-1 observations towards the Magellanic Bridge (2019; milky_way_ism, nearby_galaxies; observational_alma_primary)
- question: Can ALMA resolve individual molecular clouds in Magellanic Bridge regions B and C, and do their properties follow the trends of other metal-poor Local Group clouds?
- step 3: Derive physical properties
  - method: Req from projected area; Mvir; LCO = 2453 S dV D_L^2; Mmol with alpha_CO [3.2 Physical properties: "We have derived the radii, luminosities and virial and H 2 masses for each of the clouds based on the J = 1 − 0 line cube."]
  - parameter: k2 = 190 [3.2 Physical properties: "we used a value of k 2 = 190 for a density distribution of ρ ( r ) ∝ r −1"]
  - assumption: Spherical clouds; distance 63 kpc; alpha_CO = 4.3 Msun (K km/s pc2)^-1 (XCO = 1e20) [3.2 Physical properties: "galactic H 2 mass to CO luminosity factor α CO = 4.3 M ⊙ (K km s −1 pc 2 )"]
- step 5: Fit scaling relations
  - method: Power-law fit to all dwarf-galaxy clouds for size-linewidth and Mvir-LCO [3.2 Physical properties: "Using Maximum Likelihood and Markov Chain Monte Carlo (MCMC), we fit the best line that correlates them all."]
  - fitting: Maximum likelihood and MCMC; details not stated [3.2 Physical properties: "Using Maximum Likelihood and Markov Chain Monte Carlo (MCMC), we fit the best line that correlates them all."]
  - validation: Compared with indices from Solomon et al. 1987 and Rubio et al. 2015 [3.2 Physical properties: "similar to the indexes (0.5 and 0.52) found by Solomon et al. (1987) and Rubio et al. (2015) respectively"]
- result: Req range B = 1.9-4.5 ± not stated pc [Table 2: "B 0.3 - 0.8 1.9 - 4.5 349 - 2578 3.7 - 106.0 16 - 456 0.82 - 1.36"]
- result: Req range C = 0.5-2.5 ± not stated pc [Table 2: "C 0.3 - 0.7 0.5 - 2.5 91 - 984 3.9 - 137.7 17 - 592 0.86 - 1.96"]
- result: Larson law index = 0.41 ± not stated dimensionless [3.2 Physical properties: "A power law fit gave us an exponential index of 0.41 for Larson’s law"]
- result: Mvir vs LCO index = 0.66 ± not stated dimensionless [3.2 Physical properties: "and of 0.66 for virial mass vs. luminosity, lower than the index for galactic plane clouds."]
- limitation (authors): Procedure cannot separate clouds that differ only in velocity, only spatially resolved ones [2. Data: "not recognize clouds that have a different structure in the velocity axis, but only separates clouds if they can be spatially resolved."]
- not stated (card): CASA version and calibration/imaging details (tclean parameters, weighting, robust); How 12m and ACA data were reduced or combined; whether pipeline products used; Continuum subtraction and line-free channels; Cloud-by-cloud measured values (only ranges given); Priors, likelihood and sampler setup for the MCMC fit; How FWHM to velocity dispersion conversion was done; Mask/cutoff for the peak temp…

### 2021A&A...648A..41V: Outflows, envelopes, and disks as evolutionary indicators in Lupus young stellar objects (2021; star_formation, astrochemistry; observational_alma_primary)
- question: Whether commonly used evolutionary tracers (Tbol, Lbol/Lsubmm, Mdisk/Menv, chemistry, outflow properties) are mutually consistent for 7 Lupus prestellar and protostellar sources, and what the outflows are like.
- step 6: Measure outflow morphology, dynamical times, mass, momentum, energy
  - method: Moment maps of 12CO(2-1) red/blue lobes (3 sigma); sizes deprojected by inclination; column density with Tex=25 and 100 K; mass from N/X_CO [4.3.2 Mass, Momentum and Energy: "we estimate the density for two different values of T$_{ex}$: 25 K and 100 K."]
  - software: CASA
  - parameter: opening angle at 1000 AU projected distance; cloud-velocity channels excluded [4.3.1 First Glimpse: "The outflow opening angles are derived from the width of the outflow at a projected distance of 1000 AU from the originating source."]
  - assumption: mu=2.76, X_CO=1e-4, Tbg=2.7 K, outflow perpendicular to disk, optically thin [4.3.2 Mass, Momentum and Energy: "a CO abundance of X$_{CO}$ = 10$^{-4}$ (cite: Lacyetal1994)."]
  - validation: Compared with Bjerkeli+2016 and Dunham+2014 for IRAS 15398; Tex factor ~2.5 as uncertainty [4.3.2 Mass, Momentum and Energy: "this factor is a fair representation of the uncertainty in the mass measurements"]
- result: Outflow total size IRAS 15398-3359 = 4350 ± ±95 AU [Table (outflow params): "| Total | | | | 4350$\pm$95"]
- result: Outflow dynamical time IRAS 15398-3359 = ~300 ± ±20 yr [4.3.1 First Glimpse: "is of about 300$\pm$20 yr, revealing that it would be the shortest of the outflow sources in our sample"]
- result: Outflow size IRAS 16059-3857 = 39250 ± ±320 AU [4.3.1 First Glimpse: "is 39250$\pm$320 AU, with the red lobe being almost two times larger than the blue one"]
- result: Outflow dynamical time IRAS 16059-3857 = 5500 ± ±460 yr [4.3.1 First Glimpse: "We also estimate its average dynamical time to be 5500$\pm$460 yr."]
- result: Outflow total size J160115-41523 = 40550 ± ±1214 AU [4.3.1 First Glimpse: "the total size is 40550$\pm$1214 AU"]
- result: Total outflow mass IRAS 16059-3857 (25K/100K) = 10.9/26.4 x1e-4 ± not stated Msun [Table (outflow params): "| Total | | | | 39200$\pm$300 | | 10.9/26.4"]
- limitation (authors): Outflow masses are lower limits (no correction for missing flux at cloud velocities or opacity); sample not statistically significant. [4.3.2 Mass, Momentum and Energy: "these values should be treated as lower limits, since we do not correct for the missing flux at cloud velocities, nor the opacity of the emission."]
- not stated (card): Line-free channels used for continuum subtraction; Cell size, image size, deconvolver, masks and clean thresholds in tclean; Which pipeline version was used; Exact velocity ranges/regions used for each outflow lobe flux integration beyond the cloud-velocity cuts; Details of the modified blackbody/SED fit initial values and which points were included; Flux and uncertainty of the beta fit for sourc…

### 2015ApJ...798...85P: CO Gas Inside the Protoplanetary Disk Cavity in HD 142527: Disk Structure from ALMA (2015; protoplanetary_disks; observational_alma_primary)
- question: How much gas survives inside the dust-depleted cavity of the HD 142527 disk, and what are the gas cavity size, wall shape and inclination?
- step 4: Gas mass in cavity from optically thin 13CO and C18O
  - method: LTE column density from summed peak emission in high-velocity channels, converted to H2 mass [3.5: "We measured the integrated line intensity of $^{13}{\rm CO}$ by summing the peak emission from the selected high velocity channels"]
  - parameter: T=43 K, d=140 pc, mu=1.36 [3.5: "For the gas temperature we used $T=43$ K, as calculated from $^{12}{\rm CO}$ in the previous section."]
  - assumption: [H2]/[12CO]=1e4, [12CO]/[13CO]=76, LTE [3.5: "Assuming a fiducial CO interstellar abundance of $[{\rm H}_2]/[\mbox{$^{12}{\rm CO}$}]=10^4$ and $[\mbox{$^{12}{\rm CO}$}]/[\mbox{$^{13}{\rm CO}$}]=76$"]
  - validation: Cross-check with archival C18O J=3-2 [3.5: "consistent with the $J=2-1$ estimate (5-$\sigma$ error bars)"]
- result: Gas mass in cavity from 13CO = 1.7e-3 ± 0.6e-3 Msun [3.5: "$M_{\rm gas} = (1.7 \pm 0.6)\times 10^{-3}$ M$_\odot$"]
- limitation (authors): Gas mass is a crude estimate, dominated by assumed isotopic ratios and temperature [3.5: "The main sources of uncertainty are the assumed isotopic line ratios and the gas temperature."]
- not stated (card): Briggs robust value, cell size, image size, CLEAN masks and threshold; Line-free channels used for continuum subtraction; Whether data were self-calibrated; CASA version; LIME settings (number of grid points, photons, collision data) and model grid ranges; How the high-velocity channel peaks were selected and summed for 13CO; Solid angle Omega adopted for the cavity; Model grids for M_star and in…

### 2024ApJ...963....1O: "Beads-on-a-string" Star Formation Tied to One of the Most Powerful Active Galactic Nucleus Outbursts Observed in a Cool-core Galaxy Cluster (2024; galaxy_clusters_and_sz, star_formation, agn_and_quasars; multi_facility_alma_minor)
- question: How do the cooling ICM, an AGN outburst, the warm ionized gas, cold molecular gas and the 'beads on a string' star formation relate in the merging cool-core cluster SDSS 1531?
- step 3: Derive molecular gas mass
  - method: Fit four-component Gaussian to aperture spectrum, convert integral to H2 mass with CO-to-H2 factor [3.4.3 Mass Distribution: "we fit a four-component Gaussian line to the CO (3-2) spectrum extracted from an elliptical aperture containing all $\geq 3\sigma$ emission"]
  - software: pyspeckit
  - parameter: CO(3-2)/CO(1-0)=0.8; D_L=1767 Mpc [3.4.3 Mass Distribution: "$D_L$ is its luminosity distance (1767 Mpc in our adopted cosmology)"]
  - assumption: X_CO = Milky Way disk value 2e20 cm^-2 (K km/s)^-1, ~30% uncertainty [3.4.3 Mass Distribution: "$X_{\mathrm{CO}} = X_{\mathrm{CO,~MW}} = 2 \times 10^{20}$ cm $\left(\mathrm{K~km~s}^{-1}\right)^{-1}$"]
  - fitting: four-component Gaussian, -690 to 900 km/s; sampler/priors not stated [3.4.3 Mass Distribution: "The fit, from -690 km s$^{-1}$ to 900 km s$^{-1}$, yielded an emission integral of $\sim 1.7 \pm 0.3$ Jy km s$^{-1}$."]
  - validation: Compared integrals across binnings and weightings (0.88-2.5 Jy km/s natural) [3.4.3 Mass Distribution: "With natural weighting, we obtain integrals ranging from $0.88 - 2.5$ Jy km s$^{-1}$ depending on the different binning selected"]
- result: CO(3-2) integrated flux = 1.7 ± 0.3 Jy km/s [3.4.3 Mass Distribution: "yielded an emission integral of $\sim 1.7 \pm 0.3$ Jy km s$^{-1}$"]
- result: Molecular H2 gas mass = 3.7e10 ± 0.7e10 Msun [3.4.3 Mass Distribution: "these results give a $H_2$ gas mass of $(3.7 \pm 0.7) \times 10^{10}\text{ M}_\odot$"]
- limitation (authors): X_CO uncertainty may overestimate molecular mass by a factor of a few [3.4.3 Mass Distribution: "we may overestimate the total molecular mass by a factor of a few"]
- limitation (authors): Chandra data too shallow to resolve cavity [3.1.1: "the current X-ray data is too shallow to resolve"]
- not stated (card): Briggs robust value tested; Line-free channels and order used for continuum subtraction; clean threshold, mask, niter, cell and image size; Which of the Compact/Extended execution blocks were combined in the final cube; Aperture definition and four-Gaussian fit initial guesses for spectrum; Rest frequency/velocity frame used for channel binning; Whether archive pipeline products were used or the …

### 2018MNRAS.474.4988S: A disrupted molecular torus around Eta Carinae as seen in <SUP>12</SUP>CO with ALMA (2018; evolved_stars, stellar_physics; observational_alma_primary)
- question: What is the structure, kinematics and mass of the cool molecular equatorial torus around Eta Carinae seen in 12CO 2-1, and how does it relate to the IR torus, H2 emission and the binary orbit?
- step 3: Estimate gas mass
  - method: X_CO conversion (2e20 and 0.4e20) and LTE optically thin CO mass with CO/H2 of 1e-4 or AGCar-based ratio [4 Mass estimate from CO data: "An LTE optically thin analysis leads to a total CO mass of roughly 5.9$\times$10$^{-4}$ $M_{\odot}$."]
  - parameter: area 450 arcsec^2 (0.056 pc^2) [4 Mass estimate from CO data: "Averaged over a projected area on the sky of 450 arcsec$^2$ (0.056 pc$^2$ at the 2.3 kpc distance"]
  - assumption: gas/dust temperature 140 K; CO/H2 number ratio 1e-4 [4 Mass estimate from CO data: "we expect the gas and dust temperature (140 K) to be similar"]
  - validation: Range of conversions compared; uncertainty dominated by CO-to-H2 conversion [4 Mass estimate from CO data: "Clearly the dominant uncertainty here is in the appropriate conversion of CO to H$_2$"]
- result: Average integrated surface brightness = 26 ± ±0.4 K km/s [4 Mass estimate from CO data: "26 ($\pm$0.4) K km s$^{-1}$"]
- result: LTE optically thin CO mass = 5.9e-4 ± not stated Msun [4 Mass estimate from CO data: "total CO mass of roughly 5.9$\times$10$^{-4}$ $M_{\odot}$"]
- result: Total molecular gas mass (rough) = ~1 (range 0.2-5) ± order of magnitude Msun [4 Mass estimate from CO data: "we infer $\sim$1 $M_{\odot}$ as a very rough order-of-magnitude estimate"]
- limitation (authors): Mass conversion highly uncertain; deeper observations needed for polar lobes [4 Mass estimate from CO data: "In any case, the correct X-factor to use is highly uncertain."]
- not stated (card): Line-free channels and continuum fit order; Excitation temperature, CO column density details and CNO abundance in the LTE optically thin mass calculation; How the 450 arcsec^2 area and moment-map clipping thresholds were defined; Moment map velocity ranges and PV extraction width; Number of antennas and array configuration, time on source, calibrators

### 2021A&A...646A...1K: Molecular remnant of Nova 1670 (CK Vulpeculae). II. A three-dimensional view of the gas distribution and velocity field (2021; evolved_stars, stellar_physics, astrochemistry; observational_alma_primary)
- question: What is the 3D spatio-kinematic structure, distance, age and outflow momentum/energy of the molecular and atomic remnant of Nova 1670 (CK Vul)?
- step 3: Mass, momentum, kinetic energy
  - method: CO column density times area, converted to H2 mass with CO abundance; momentum and Ekin from model deprojected velocities at 2.6, 3.5, 5.7 kpc [4 Mass, momentum, and kinetic energy in…: "By multiplying these column densities by the respective sizes of the regions, we estimated the number of CO molecules"]
  - parameter: Lobe velocity 312 km/s, central 50 km/s [4 Mass, momentum, and kinetic energy in…: "we calculated a flux-weighted average CO velocity in the lobes (at $r>$2$''$) of CO of 312 km s$^{-1}$."]
  - assumption: CO/H2 = 2e-4 [4 Mass, momentum, and kinetic energy in…: "using a CO abundance of 2$\times$10$^{-4}$ relative to H$_2$"]
  - validation: Compared with PPN ranges of Bujarrabal et al. 2001 [4 Mass, momentum, and kinetic energy in…: "Values at the considered distances are within the ranges of $M\varv$ and $E_{\rm kin}$ found by (cite: Bujarrabal2001) for PPNe"]
- result: Total H2 mass at 3.5 kpc (analysed regions) = 0.59 ± not stated Msun [Table 2: "| All | | | 0.32 | 0.59 | 1.56"]
- result: Total momentum at 3.5 kpc = 1.8e40 ± not stated g cm/s [Table 2: "| 9.9e39 | 1.8e40 | 4.8e40"]
- result: Total kinetic energy at 3.5 kpc = 2.3e47 ± not stated erg [Table 2: "| 1.3e47 | 2.3e47 | 6.2e47"]
- limitation (authors): Model is non-unique owing to k–i degeneracy; masses underestimated [3.1 Step 1: General shape: "Thus, our model does not generally offer a unique representation of the available data."]
- not stated (card): Exact ALMA reduction, calibration, imaging parameters (all in Paper I); SHAPE model files and parameter values (bump definitions) not given; Procedure for flux weighting of the 312 km/s velocity; How the 52% flux recovery was computed in detail; Uncertainty derivation for the distance

### 2014ApJ...784...78R: Massive Molecular Gas Flows in the A1664 Brightest Cluster Galaxy (2014; galaxy_clusters_and_sz, nearby_galaxies; observational_alma_primary)
- question: What are the mass, kinematics and origin (inflow, outflow or merger) of the molecular gas in the Abell 1664 BCG?
- step 4: Derive molecular gas masses
  - method: M_mol = 1.05e4 X_CO /(1+z) S_CO dv D_L^2 from CO(1-0) intensities [4.1: "we calculated the molecular gas mass"]
  - assumption: Galactic X_CO = 2e20 cm-2 (K km/s)-1; z=0.128; H0=70, Om=0.3, OL=0.7 [4.1: "Under the assumption of the Galactic value $\rm X_{CO}=2\times 10^{20}"]
  - validation: Schmidt-Kennicutt placement and subsolar metallicity argue Galactic X_CO reasonable [4.1: "Therefore, we argue that the Galactic $\rm X_{CO}$ value is likely to be reasonable."]
- result: Total molecular gas mass = 1.1e10 ± 0.1e10 Msun [4.1: "The total CO mass in the BCG is then $(1.1\pm0.1)\times 10^{10}"]
- result: HVS mass = 5.0e9 ± 0.7e9 Msun [Table 1: "$1.5\pm0.2$ | $8.2\pm0.8$ | $170\pm20$ | $-568\pm8$ | $5.0\pm0.7$"]
- result: Systemic component mass = 5.7e9 ± 1.0e9 Msun [4.1: "$M_{\rm disk} = (5.7\pm1.0)\times 10^9"]
- limitation (authors): Cannot tell whether gas lies in front of or behind the BCG [4.4: "we cannot distinguish between an inflow of gas located behind the BCG and an outflow of gas located in front of the BCG."]
- not stated (card): Line-free channels and continuum subtraction method/order; Image size, cell size, clean threshold and iterations; Channel binning used for spectra; Spectral extraction details and baseline fitting; Flux calibration uncertainty; Pixel/region definitions for clumps A, B and HVS sub-regions; PV slice widths; Luminosity distance value used

### 2014ApJ...790..160S: ALMA Observations of a Candidate Molecular Outflow in an Obscured Quasar (2014; agn_and_quasars, nearby_galaxies; observational_alma_primary)
- question: What are the morphology, kinematics and mass of molecular gas in the obscured quasar SDSS J1356+1026, and is there a molecular outflow related to the known ionized outflow?
- step 3: Derive molecular gas masses and SFR from CO
  - method: Mass from CO(1-0) luminosity with ULIRG XCO; SFR via Schmidt-Kennicutt law assuming 300 pc disk [3.3 Molecular Gas Mass and Star Formati…: "Using the Schmidt-Kennicutt law (cite: KennicuttJr:1998id), we find the star formation rate at the N nucleus to be SFR=1.2 $M_{\odot}$ yr$^{-1}$"]
  - assumption: alpha_CO = 0.86 Msun (K km/s pc^2)^-1, 0.5 dex error; outflow assumes L'(3-2)/L'(1-0)=1 [3.3 Molecular Gas Mass and Star Formati…: "This corresponds to $\alpha_{\rm{CO}}$= 0.86 $M_{\odot}$ (K kms pc$^{2}$)$^{-1}$"]
- result: Total molecular gas mass = 9e8 ± +19/-6 e8 Msun [Table 2: "| Sum | $9^{+19}_{-6}\times 10^8$ |"]
- result: N nucleus molecular mass = 3e8 ± +6/-2 e8 Msun [4.1 The N nucleus: "the molecular gas mass is estimated to be $3^{+6}_{-2} \times10^8$ $M_{\odot}$"]
- result: W arm molecular mass = 5e8 ± +11/-3 e8 Msun [4.2 The W arm: "the W arm contains $5^{+11}_{-3} \times10^8$ $M_{\odot}$ of molecular gas"]
- result: Outflow molecular mass = 7e7 ± +15/-5 e7 Msun [4.1 The N nucleus: "$M_{\mathrm{mol}} =7^{+15}_{-5}\times10^7$ $M_{\odot}$"]
- limitation (authors): Outflow quantities order-of-magnitude; XCO and line ratio uncertain [5.2.1 Properties of the Molecular Outfl…: "First, the $X_{\rm{CO}}$ factor in the context of an outflow is uncertain."]
- not stated (card): Exact clean parameters (cell size, image size, niter, masks, spectral-line channel ranges for CO 3-2); Line-free channel ranges for CO(3-2) 300 GHz continuum check; Aperture sizes/centres for flux extraction; Kinematic fitting details of 2D Gaussian per channel; Herschel photometry values (Petric et al. in prep.); Exact formulae for outflow energetics and Kennicutt SFR conversion; HST astrometric…

### 2025A&A...696A.100G: PDRs4All: XII. Far-ultraviolet-driven formation of simple hydrocarbon radicals and their relation with polycyclic aromatic hydrocarbons (2025; milky_way_ism, astrochemistry, star_formation; observational_alma_primary)
- question: How are simple hydrocarbon radicals (C2H, C, CH_n) formed in the FUV-irradiated Orion Bar PDR, and are they linked to PAH aliphatic content traced by the 3.4/3.3 um AIB ratio?
- step 7: Correlate C2H with H2, AIB, [CI] intensities
  - method: Smooth images to 0.8 arcsec, clip at 3 sigma, weighted least-squares log-log fits, Pearson/Spearman coefficients [Line intensity correlations: "after clipping intensities below a 3$\sigma$ detection threshold"]
  - fitting: weighted least squares log10 y = a log10 x + b [Table 3 notes: "Regressions fitted to the molecular PDR data (bluish areas in Fig. [18](#fig:PDR_correlations)) in a weighted least-square fit, log$_{10}$ $y$ = $a$ log$_{10}$ $x$ + $b$."]
- limitation (authors): Exact chemical pathways and relative contributions of bottom-up and top-down processes remain unquantified; models omit PAH chemistry [abstract: "the exact chemical pathways and their relative contributions remain to be quantified"]
- not stated (card): CASA version and pipeline version; flux, bandpass and phase calibrators and flux scale uncertainty; CLEAN threshold, masks, weighting, cell and image size; continuum subtraction and line-free channels; exact crosscut positions and widths; Monte Carlo radiative transfer model details and code availability; Meudon PDR grid inputs beyond Table 1

### 2018MNRAS.481.4931E: ALMA reveals the aftermath of a white dwarf-brown dwarf merger in CK Vulpeculae (2018; stellar_physics, evolved_stars, astrochemistry; observational_alma_primary)
- question: What are the dust and molecular gas structures in the inner region of CK Vul, and what do they imply about the origin of the 1670 event?
- step 4: Estimate gas mass and gas-to-dust ratio
  - method: Recompute H2 mass from literature CO column density [3.1.2: "Assuming the CO column density in (cite: kaminski-n), and a CO/H$_2$ ratio of $\sim10^{-3}$ (appropriate for carbon–rich AGB winds), we recalculated a H$_2$ mass of $\sim9.8\times10^{-3}$ M$_\odot$."]
  - assumption: CO/H2 ~1e-3 (carbon-rich); oxygen-rich case gives 3.9e-2 Msun [3.1.2: "If the nebula is considered oxygen–rich, this will give a value $\sim3.9\times10^{-2}$ M$_\odot$."]
- result: Gas-to-dust ratio = ~50 to 200 ± not stated dimensionless [3.1.2: "the gas–to–dust ratio is $\sim50$ to 200"]
- limitation (authors): Velocity resolution is modest and dynamical modelling is deferred. [Observations: "We defer modelling of the dynamics of these emission lines to a future, more detailed, paper"]
- not stated (card): Image size, cell size, masking, deconvolver, cleaning threshold; Spectral cube channel width and rest-frame/velocity settings; Whether tclean used the combined data and any primary beam correction; CASA and pipeline versions; Flux scale uncertainty; Integration ranges and moment/PV extraction details; CO column density value used for H2 mass

### 2020ApJ...889L...4L: Revealing the CO X-factor in Dark Molecular Gas through Sensitive ALMA Absorption Observations (2020; milky_way_ism, astrochemistry; observational_alma_primary)
- question: What are the properties of CO and HCO+ in diffuse, cold dark molecular gas, and what is the CO X-factor there, as probed by absorption toward continuum sources?
- step 5: Compute CO X-factor
  - method: Reconstruct W_CO from tau and Tex; X_CO = N_H2/W_CO [6 The CO X-factor: "We have reconstructed the CO integrated intensity from the $\tau$ and $\mathrm{T_{ex}}$ obtained from our RADEX modeling."]
  - validation: Compared with Taurus results and simulations [6 The CO X-factor: "Our results are in agreement with observations in regions without $\mathrm{^{12}CO}$ and $\mathrm{^{13}CO}$ emission detections in Taurus (cite: Pineda2010)."]
- result: CO X-factor = 14e20 ± 3e20 cm^-2 (K km/s)^-1 [6 The CO X-factor: "The average X-factor we obtain in our sightlines is (14 $\pm$ 3) $\times$ 10$^{20}$ cm$^{-2}$ (K $\mathrm{km\, s^{-1}\, }$)$^{-1}$"]
- limitation (authors): HI column densities are lower limits for most sightlines (optically thin assumption) [5 HCO+ as a molecular gas tracer: "for the majority of sightlines represents a lower limit under the optically thin assumption."]
- not stated (card): Robust value, cell size, image size, masking for imaging; Spectral extraction method and continuum-free channels; Number of Gaussian components and fitting priors/initial guesses; RADEX grid ranges and collision-rate files; How W_CO was reconstructed from tau and Tex (integration limits); Which sources enter the X-factor average; Beam size, rms in K, CASA/pipeline version; Source coordinates and …

### 2017ApJ...835..278S: Physical Properties of Molecular Clouds at 2 pc Resolution in the Low-metallicity Dwarf Galaxy NGC 6822 and the Milky Way (2017; nearby_galaxies, star_formation, milky_way_ism; observational_alma_primary)
- question: How do the structure of CO-bright clumps and the CO-to-H2 conversion in the low-metallicity dwarf galaxy NGC 6822 compare with Milky Way clouds, and what does this imply for molecular gas depletion times?
- step 2: Estimate global CO luminosity
  - method: Aperture correction using Halpha and 24um fractions of fields, plus flux recovery correction [4.1 Total CO Luminosity: "Our “aperture correction” is the ratio of total star formation tracer luminosity of the galaxy to the luminosity inside our fields."]
  - assumption: R21 = 1.0 (0.7-1.0 for CO(1-0)) [3.5 CO Excitation: "therefore, we adopt $R_{21} = 1.0$ throughout the paper"]
  - validation: Compared to Gratier et al. IRAM estimate [4.1 Total CO Luminosity: "This value agrees within the uncertainty with a similarly derived estimate by (cite: Gratier10a)"]
- step 3: Derive complex gas masses and alpha_CO from dust
  - method: GDR from outer 50 pc ring, background subtraction, dust-traced gas minus HI gives H2; alpha_CO = H2/L_CO [4.2 Atomic-Molecular Complexes: "we estimate the GDR by comparing $\Sigma_\mathrm{atom}$ and $\Sigma_\mathrm{dust}$ in regions where atomic gas makes up most of the gas."]
  - parameter: maps at 25" ≈ 57 pc resolution, SPIRE 350 um as dust proxy [3.2 Atomic Gas and Dust: "The H$\,$I and dust maps are evaluated at a common resolution of $25\ensuremath{''} \approx 57$ pc"]
  - assumption: optically thin HI, no opacity correction [3.6 H I Opacity Correction: "we adopt the standard assumption of optically thin H$\,$I emission and work without opacity correction"]
  - validation: Compared with three dust models agreeing within factor of a few [3.2 Atomic Gas and Dust: "results derived from more complex dust modeling (i.e., modified blackbody, (cite: Galliano11), or (cite: DraineLi07) model) agree within a factor of a few"]
- step 5: Identify CO clumps and measure properties
  - method: CPROPS: size, line width, luminosity; mean over methods, with corrections for sensitivity and resolution; virial mass Mvir = 1040 R sigma^2 [3.4 Cloud Property Measurements: "The values reported here are the mean across all of these characterization methods."] [4.5 CO Clump Properties: "$M_\mathrm{vir}~[\mbox{$\rm M_{\odot}$}] = 1040 R \sigma^2~[\mathrm{pc}\,\mathrm{km}^2\,\mathrm{s}^{-2}]$"]
  - software: CPROPS
  - assumption: alpha_CO = 4.35 Msun pc^-2 (K km/s)^-1, R21 = 1 for luminous mass [4.5 CO Clump Properties: "using a fiducial Galactic CO-to-H$_2$ conversion factor $\alpha_\mathrm{CO} = 4.35$ M$_{\odot}$ pc$^{-2}$ (K km s$^{-1}$)$^{-1}$ and $R_{21} = 1$"]
  - fitting: Power-law fits to clumps [4.5 CO Clump Properties: "Black lines show power law fits to the NGC 6822 clumps"]
  - validation: Compared to WLM and outer Milky Way clumps; scatter between methods as uncertainty [3.4 Cloud Property Measurements: "We adopt the scatter in results from different measurement approaches as our best estimate of the uncertainty"]
- result: Number of CO clumps = ~150 ± not stated clumps [4.5 CO Clump Properties: "We identify and measure the properties of ${\sim} 150$ of these roughly pc-scale “clumps,”"]
- result: Global CO(2-1) luminosity of NGC 6822 = 6-10 x 10^4 ± not stated K km/s pc^2 [4.1 Total CO Luminosity: "a best-estimate global CO(2-1) luminosity of NGC 6822 of $\sim 6{-}10 \times 10^4$ K km s$^{-1}$ pc$^2$"]
- result: Joint alpha_CO (2-1) = 110 ± ±30 Msun pc^-2 (K km/s)^-1 [4.2 Atomic-Molecular Complexes: "$\delta_\mathrm{GDR} = 320 \pm 80$ and $\alpha_\mathrm{CO} = 110 \pm 30$"]
- result: alpha_CO Fields 2 & 4 = 85 ± ±25 Msun pc^-2 (K km/s)^-1 [4.2 Atomic-Molecular Complexes: "we determine $\alpha_\mathrm{CO} = 85 \pm 25$ M$_{\odot}$ pc$^{-2}$ (K km s$^{-1}$)$^{-1}$"]
- result: Mean gas-to-dust ratio = 380 ± ±70 dimensionless [4.2 Atomic-Molecular Complexes: "we find $\delta_\mathrm{GDR} = 380 \pm 70$"]
- result: Molecular depletion time of complexes = ~360 ± not stated Myr [5.5 Star-forming Gas Content: "present day star formation will consume the molecular gas content of the complexes in ${\sim} 360$ Myr"]
- result: Mean clump radius / velocity dispersion = R≈2.3 pc, sigma_v≈1.1 km/s ± not stated pc; km/s [5.1 The CO-bright Clumps: "These CO-bright clumps have an average size of $R \approx 2.3$ pc, velocity dispersion of $\sigma_\mathrm{v} \approx 1.1$ km s$^{-1}$"]
- limitation (authors): Dust maps uncertain (Galactic cirrus, Herschel issues), dominating the error budget [3.2 Atomic Gas and Dust: "This uncertainty dominates the error budget in our analysis of dust-inferred gas masses."]
- limitation (authors): Missing flux on large scales [2 ALMA Survey: "emission extending over scales larger than the maximum recoverable scale of about $0.6 \lambda / L_\mathrm{min} \approx 11\ensuremath{''} \approx 25$ pc is missing in our data sets"]
- not stated (card): Exact clean parameters (threshold, niter, mask, mosaic gridding); Line-free channels / continuum subtraction for CO cube; CASA version and pipeline version; CPROPS settings (S/N cuts, parameters, extrapolation); Details of convolution of Milky Way data and HI/dust regridding; Herschel background/cirrus handling for 350 um map and conversion to dust mass; Public availability of the HI map (not rel…

### 2018MNRAS.479.5440L: Neutral versus ionized gas kinematics at z ≃ 2.6: the AGN-host starburst galaxy PKS 0529-549 (2018; high_z_galaxies, agn_and_quasars; observational_alma_primary)
- question: Do neutral ([C I]) and ionized ([O III]) gas trace the same kinematics in PKS 0529-549 at z~2.6, and is the [C I] disc dynamically relaxed and baryon-dominated?
- step 1: Image continuum and [C I] cube
  - method: CASA clean, natural weighting, 50 km/s channels, image-plane continuum subtraction [2.1 ALMA data: "The [C I] cube was imaged using a channel width of 50 $\mathrm{km}\,\mathrm{s}^{-1}$"]
  - software: CASA
  - validation: Tried uv-plane subtraction, found over-subtraction [2.1 ALMA data: "sanity checks revealed that the continuum was over-subtracted in this way"]
- step 3: 3D disc model of [C I]
  - method: GALMOD trial-and-error for initial estimates and geometry, then 3DBarolo chi2 fit of Vrot and sigma in a single ring [3.2 Disc modelling: "We use $V_{\rm rot}$ and $\sigma_{\rm V}$ as free parameters, but keep the others fixed to the values estimated with GALMOD."]
  - software: GALMOD, 3DBarolo
  - parameter: exponential vertical profile, h = 0.04'' ~ 300 pc [3.2 Disc modelling: "we assume an exponential vertical profile with fixed $h = 0.04'' \simeq 300$ pc"]
  - assumption: parameters constant with radius (single ring) [3.2 Disc modelling: "we assume that the disc parameters are constant with radius ($R$)"]
  - fitting: chi2 minimization; errors by re-running with one variable free [3.2 Disc modelling: "To estimate errors on each variable, we re-run $^{\rm 3D}$BAROLO leaving such variable free"]
  - validation: Compare model with PV diagrams, channel maps, moment map residuals [3.2 Disc modelling: "we build model cubes and compare them with the observed one using Position-Velocity (PV) diagrams and channel maps"]
- step 4: Mass budget and dynamical mass
  - method: M_R = eps R Vrot^2/G with eps=1; baryonic mass from stellar (literature) + molecular (from [C I] flux) + WIM [3.3 Mass budget: "For simplicity, we adopt $\varepsilon = 1$ (spherical geometry)."]
  - assumption: [C/H2] abundance of M82; factor of 2 uncertainty [3.3 Mass budget: "This [C I]$-$to$-$H$_2$ conversion assumes the [C/H$_2$] abundance of the local starburst galaxy M82"]
  - validation: Compare Mdyn with Mbar at 4 and 8 kpc [Mass budget: "If we extrapolate the measured rotation velocity out to 8 kpc, we get $M_{\rm 8\,kpc} = (1.8\pm0.6) \times 10^{11}$ M$_{\odot}$ which is closer to $M_{\rm bar}$."]
- result: Vrot = 310 ± 50 km/s [Table 1: "$V_{\rm rot}$ ($\mathrm{km}\,\mathrm{s}^{-1}$) | $310\pm50$"]
- result: sigma_V = <~30 ± upper limit km/s [Table 1: "$\sigma_{\rm V}$ ($\mathrm{km}\,\mathrm{s}^{-1}$) | $\lesssim$30"]
- result: inclination = 50 ± 4 deg [Table 1: "$i$ ($^{\circ}$) | $50\pm4$"]
- result: M_4kpc = 0.9e11 ± 0.3e11 Msun [3.3 Mass budget: "thus $M_{\rm 4\, kpc} = (0.9 \pm 0.3) \times10^{11}$ M$_{\odot}$"]
- result: M_bar = 3.4e11 ± 2.0e11 Msun [3.3 Mass budget: "the total baryonic mass of PKS 0529-549 is $M_{\rm bar} = (3.4\pm2.0) \times 10^{11}$ $M_{\odot}$"]
- result: M_mol = 4e10 ± factor of 2 Msun [3.3 Mass budget: "we estimate $M_{\rm mol}\simeq 4 \times 10^{10}$ M$_{\odot}$"]
- limitation (authors): Velocity map very uncertain due to beam smearing and low S/N; Sigma not robust [2.1 ALMA data: "We stress that the velocity map is very uncertain due to beam smearing effects and the low S/N ratio."]
- not stated (card): Line-free channel ranges for continuum subtraction; Exact channel mask regions; 3DBarolo settings (initial estimates, ring geometry, normalization, fit options); GALMOD fixed centre, PA, Vsys values and iteration details; CASA version and clean parameters (cell, image size, threshold); Mol mass conversion details (Man et al. in prep.)

### 2024ApJ...964...18C: Resolved Measurements of the CO-to-H<SUB>2</SUB> Conversion Factor in 37 Nearby Galaxies (2024; nearby_galaxies, milky_way_ism; multi_facility_alma_minor)
- question: How does the CO-to-H2 conversion factor (alpha_CO) vary at 2 kpc resolution across 37 nearby galaxies, and how does it scale with local and galaxy-integrated quantities, especially stellar mass surface density?
- step 2: Derive alpha_CO per pixel
  - method: alpha_CO = (Sigma_dust/(Z x D/M) - Sigma_atom)/W_CO, with errors propagated [2 Calculating alpha_CO: "$$\begin{equation} \label{eq:aco_final} \ensuremath{\alpha_{\rm CO}}= \ensuremath{\Sigma_\mathrm{mol}}~W_\mathrm{CO}^{-1}"]
  - parameter: S/N<1 pixels in W_CO and Sigma_mol blanked [3.3 S/N Mask and Completeness: "we blank pixels with $\mathrm{S/N} < 1$ in $W_\mathrm{CO}$ and $\Sigma_\mathrm{mol}$."]
  - assumption: constant D/M = 0.55 (mean of 0.4-0.7) [2 Calculating alpha_CO: "we will take a constant $\mathrm{D/M}=0.55$ (mean of 0.4–0.7) as the fiducial case for deriving $\alpha_{\rm CO}$."]
  - validation: Compared with Sandstrom et al. 2013 and COMING [6.3 Comparing to previous alpha_CO surv…: "The $\alpha_{\rm CO}$ measured in the three works are in general consistent with each other within uncertainties."]
- step 3: Regress alpha_CO on local and galaxy-averaged quantities
  - method: Spearman-type correlation and linear regression log alpha_CO = m x + b in completeness >50% zone [4.1 Correlations with Local Conditions: "we perform linear regression with the functional form: $$\begin{equation} \log\ensuremath{\alpha_{\rm CO}}=mx+b,"]
  - fitting: Errorbars from 1000 bootstraps [4.1 Correlations with Local Conditions: "We first bootstrap the measurements by 1000 times with uncertainties"]
- step 4: Fit alpha_CO vs Sigma_star power law
  - method: Fit log(alpha/alpha_gal,T) = a log(Sigma_star/100) + b above 100 Msun/pc2; vary D/M and threshold [5 Power-law dependence: "We use a power law to characterize this scaling relation"]
  - parameter: Sigma_star,T = 100 Msun/pc2; D/M 0.1-1 [5.1 Dependence of the power-law index: "i.e. $0.1 \leq \text{D/M} \leq 1$."]
  - fitting: Uncertainties from 1000 bootstrap resamplings of galaxies [5 Power-law dependence: "The uncertainties of $a$ and $b$ are estimated from 1000 rounds of bootstrap resampling."]
  - validation: Robustness to D/M, threshold and toy D/M-variation model [8 Internal variation of D/M: "The constant D/M case and the toy model case should sandwich the actual indices."]
- result: Mean alpha_CO(2-1) = 9.3 ± +4.6/-5.4 Msun pc-2 (K km/s)-1 [abstract: "$9.3^{+4.6}_{-5.4}$ and $4.2^{+1.9}_{-2.0}~M_\odot~pc^{-2}~(K~km~s^{-1})^{-1}$"]
- result: Mean alpha_CO(1-0) = 4.2 ± +1.9/-2.0 Msun pc-2 (K km/s)-1 [abstract: "$9.3^{+4.6}_{-5.4}$ and $4.2^{+1.9}_{-2.0}~M_\odot~pc^{-2}~(K~km~s^{-1})^{-1}$"]
- result: W_CO-weighted mean alpha_CO(2-1) = 5.69 ± not stated Msun pc-2 (K km/s)-1 [4 Results: "The $W_{\rm CO}$-weighted mean for $\ensuremath{\alpha_{\textup{CO}\,\ensuremath{(2{\ensuremath{-}}1)}}}$ and $\ensuremath{\alpha_{\textup{CO}\,\ensuremath{(1{\ensuremath{-}}0)}}}$ are 5.69 and 3.33, respectively."]
- result: Power-law index a, CO(2-1), fiducial = -0.50 ± +0.07/-0.06 dimensionless [5 Power-law dependence: "the fitting yields $a=-0.50^{+0.07}_{-0.06}$ and $b=0.03^{+0.01}_{-0.01}$ with $\ensuremath{\Delta_\mathrm{rms}}=0.15~\mathrm{dex}$ for CO $(2{\ensuremath{-}}1)$"]
- result: Power-law index a, CO(1-0), fiducial = -0.22 ± +/-0.06 dimensionless [5 Power-law dependence: "$a=-0.22^{+0.06}_{-0.06}$ and $b=0.003^{+0.01}_{-0.01}$ with $\ensuremath{\Delta_\mathrm{rms}}=0.13~\mathrm{dex}$ for CO $(1{\ensuremath{-}}0)$"]
- limitation (authors): Data concentrated in narrow metallicity range 8.4-8.6, limiting metallicity analysis [4.1 Correlations with Local Conditions: "$>80\%$ of our data is concentrated in a small dynamic range of $8.4 \leq \ensuremath{12+\log({\rm O/H})}\leq 8.6$."]
- not stated (card): Exact PHANGS-ALMA CO(2-1) product version, moment-map masking and noise maps; Dust SED fit outputs (J. Chastenet et al. in prep.) and uncertainty maps; Binning details for plots and regression method for linear fits; HI processing for EveryTHINGS and PHANGS-VLA (in preparation)

### 2021A&A...656A..60A: Black hole feeding and star formation in NGC 1808 (2021; nearby_galaxies, agn_and_quasars; observational_alma_primary)
- question: How is the AGN of NGC 1808 fed, and how do star formation and feedback behave in the central few hundred pc, based on the kinematics of the molecular gas?
- step 2: Estimate missing flux and H2 mass
  - method: Compare ALMA flux with SEST-derived expected CO(3-2) flux; compute L'CO and M(H2) [3.3 CO luminosity and H2 mass: "we should expect some missing flux by a factor up to $\sim$40-50%"]
  - parameter: r32=0.66, r21=1.12, r13=1 or 1.35 [3.3 CO luminosity and H2 mass: "(r$_{\rm 13}$=1). If instead we use r$_{\rm 13}$=1.35"]
  - assumption: Milky Way alpha_CO=4.36 [3.3 CO luminosity and H2 mass: "$\alpha_{\rm CO}$=4.36 M$_{\rm \odot}(\rm K\,km\,s^{-1}\,pc^2)^{-1}$ (cite: bol13)"]
  - validation: Compared to single-dish masses [3.3 CO luminosity and H2 mass: "Our rather smaller value derived with the ALMA high resolution observations is due to lack of single-dish observations"]
- step 5: Resolved Kennicutt-Schmidt relation
  - method: Compute SFR from Pa-alpha and molecular gas surface density from CO(3-2) in apertures [4.2 Resolved Kennicutt-Schmidt relation: "we compute the surface densities of star formation rate (SFR) and molecular gas to build a resolved Kennicutt-Schmidt (KS) diagram"]
  - parameter: aperture radius 0.75'' = 34 pc [4.2 Resolved Kennicutt-Schmidt relation: "where the radius of 0.75$''$ = 34 pc"]
  - assumption: alpha_CO=4.36, r31=0.27, 45% missing flux correction, inclination 57 deg, Calzetti extinction [4.2 Resolved Kennicutt-Schmidt relation: "The molecular masses were corrected from the 45% missing flux, as discussed in Section [3.3](#miss)"]
  - validation: Comparison with Bigiel2008 and Casasola2015 [4.2 Resolved Kennicutt-Schmidt relation: "All our points lie in the KS relation"]
- result: CO(3-2) flux in 18'' FoV = 2594 ± not stated Jy km/s [3.3 CO luminosity and H2 mass: "the integrated emission in our ALMA FoV of 18$''$ is 2594 Jy km/s"]
- result: missing flux fraction = ~40-50% ± not stated percent [3.3 CO luminosity and H2 mass: "we should expect some missing flux by a factor up to $\sim$40-50%"]
- result: L'CO = 6.1e7 ± not stated K km/s pc^2 [3.3 CO luminosity and H2 mass: "${L_{\rm CO}}^\prime=$6.1$\times10^7$ K km/spc$^2$"]
- result: M(H2) in FoV (r13=1) = 2.7e8 ± not stated Msun [3.3 CO luminosity and H2 mass: "molecular mass of 2.7$\times$10$^8$M$_\odot$ in our FoV"]
- result: M(H2) in FoV (r13=1.35) = 3.6e8 ± not stated Msun [3.3 CO luminosity and H2 mass: "we obtain a molecular mass of 3.6$\times$10$^8$M$_\odot$"]
- limitation (authors): Missing flux ~40-50% due to lack of single-dish data. [3.3 CO luminosity and H2 mass: "Our rather smaller value derived with the ALMA high resolution observations is due to lack of single-dish observations to detect weak extended emission"]
- limitation (authors): Mass model parameters are degenerate. [4.4 Lindblad resonances: "Given the freedom and the degeneracy to distribute all mass components"]
- not stated (card): Line-free channels used for continuum; Robust/taper and cell/image size in GILDAS; Clean masks and stopping thresholds; Rest frequencies and velocity frame for the cubes; Tilted-ring fit initialization, ring widths beyond 0.3'' and 3DBarolo parameters; Aperture positions/fluxes for KS regions and Pa-alpha extinction values; Mass model parameter fitting details; Treatment of missing-flux correctio…

### 2021A&A...645A.120F: ALMA and MUSE observations reveal a quiescent multi-phase circumgalactic medium around the z ≃ 3.6 radio galaxy 4C 19.71 (2021; high_z_galaxies, agn_and_quasars; observational_alma_primary)
- question: What are the kinematics, ionization and molecular gas content of the multi-phase circumgalactic medium around the z≃3.6 radio galaxy 4C 19.71, probed with ALMA [CI](1-0) and MUSE rest-frame UV lines?
- step 3: Detect and fit lines
  - method: Blind search of binned cube for [CI] and 13CO; Gaussian fits to [CI] and double-Gaussian to CIV; Lyα and HeII constrained using C IV/[CI] redshift and widths [3.1 Molecular and atomic emission lines: "We used the non-linear least square method to fit a Gaussian function to the spectrum using the RMS=0.3 mJy as one sigma uncertainty in the flux."]
  - parameter: CIV doublet ratio fixed to 2:1, common width, red component fixed 2.6 Å from blue [3.2 Ionized gas: "we fixed the C iv $\lambda$1548/C iv $\lambda$1550 doublet ratio to the theoretical ratio of 2:1"]
  - fitting: non-linear least squares; 1σ from variance of parameter estimates [3.1 Molecular and atomic emission lines: "The reported errors are the square root of the variance, one sigma, of the parameter estimate for the Gaussian fits."]
  - validation: Lyα flux estimated by two independent methods (integration of unaffected channels and Gaussian fit) [3.2 Ionized gas: "To estimate the Ly$\alpha$ $\lambda$1215.7 Å integrated line flux, we used two independent methods."]
- step 4: Derive molecular gas mass, SFE and depletion time
  - method: [CI]-based H2 mass equation; cross-check with Scoville2016 continuum method [4.3 Molecular gas mass: "we compared it with the molecular gas mass estimated from the observed continuum flux density in ALMA band 3 (cite: Scoville2016)"]
  - parameter: X_[CI]=3e-5, Q10=0.48, A10=7.93e-8 s^-1 [4.3 Molecular gas mass: "we assumed the median value of $Q_{10}$=0.48"]
  - assumption: Tdust=40 K for the continuum cross-check; X_[CI]=1e-5 for region A [4.3 Molecular gas mass: "assuming $T_{\rm dust}$=40 K"]
  - validation: Continuum-based mass 6e10 Msun within a factor of two of [CI] mass [4.3 Molecular gas mass: "we find a molecular gas mass of $M_{\rm mol}= 6 \times 10^{10}$ M$_{\odot}$"]
- step 5: Photoionization/PDR modeling of CGM cloud
  - method: Cloudy 17.01 grids of isochoric and isobaric models compared with [CI]/CIV and CIV/HeII ratios [4.4.1 photoionization: "The density, for the isochoric models, varied from log n$_H$ (cm$^{-3}$)=0 to 3 in steps of 1 dex"]
  - software: Cloudy
  - parameter: power-law slope -1 over 0.01–12 Ryd; log U from -4 to -1; AV=2 [4.4.1 photoionization: "a simple hard power-law with a slope of $-$1 over the energy range of 0.01 to 12 Ryd"]
  - assumption: Standard ISM abundance ratios scaled to a range of metallicities [4.4.1 photoionization: "Grids of models were made assuming the standard ISM abundance ratios scaled to a range of metallicities."]
  - validation: tested slopes -1.5 and -2.0 show modest differences [4.4.1 photoionization: "The resulting line ratios show only modest differences compared to our fiducial model"]
- result: Systemic redshift = 3.5895 ± not stated dimensionless [3.1 Molecular and atomic emission lines: "$z_{\rm sys}$=3.5895"]
- result: [CI](1-0) FWHM, core = 87 ± 23 km/s [3.1 Molecular and atomic emission lines: "FWHM of 87$\pm$23 km s$^{-1}$"]
- result: [CI](1-0) FWHM, region A = 108 ± 54 km/s [3.1 Molecular and atomic emission lines: "it has an FWHM of 108$\pm$54 km s$^{-1}$"]
- result: CIV FWHM region A = 179 ± 27 km/s [3.2 Ionized gas: "an FWHM of 179$\pm$27 km s$^{-1}$"]
- result: M_H2 core = 3.06e10 ± 1.11e10 Msun [4.3 Molecular gas mass: "M$_{\rm H_2}^{\rm Core}$=(3.06$\pm$1.11)$\times$10$^{10}$ M$_{\odot}$"]
- result: M_H2 region A = 1.42e10 ± 0.95e10 Msun [4.4.4 Gas masses: "M$_{\rm H_2}^{\rm north}$=(1.42$\pm$0.95)$\times$10$^{10}$ M$_{\odot}$"]
- result: Star formation efficiency = 2.74 ± +5.57/-0.99 Gyr^-1 [4.3 Molecular gas mass: "SFE$\equiv$SFR/M$_{\rm H_2}$=2.74$^{+5.57}_{-0.99}$ Gyr$^{-1}$"]
- result: Gas depletion time = 0.36 ± +1.08/-0.18 Gyr [4.3 Molecular gas mass: "t_{\rm depl}\equiv$SFE$^{-1}$=0.36$^{+1.08}_{-0.18}$ Gyr"]
- result: Gas fraction = 0.19 ± 0.07 dimensionless [4.1 A normal star-forming galaxy?: "$f_{\rm gas}$=0.19$\pm 0.07$"]
- result: [CI]/CIV flux ratio, region A = 0.017 ± 0.011 dimensionless [4.4.1 photoionization: "flux ratios of \[C i\]/C iv=0.017$\pm$0.011"]
- limitation (authors): Low S/N; Lyα and HeII severely affected by night sky lines [5 Conclusions: "We are limited to low signal-to-noise and the source is at an unfortunate redshift"]
- limitation (authors): Mass uncertainty excludes errors on X_[CI], Q10, A10 [4.3 Molecular gas mass: "without additional errors arising from from uncertainties in $X_{\rm [C\textsc{i}]}$, $Q_{10}$, or $A_{10}$"]
- not stated (card): Exact CASA version and the tclean parameters (cell, image size, mask, niter, threshold); Line-free channel ranges used for the continuum fit; Aperture/region definitions (pixel boundaries) for regions A, B, C; Flux calibrator and flux scale uncertainty; Details of Cloudy inputs (ionizing luminosity normalisation, abundances, dust); Method for computing inclination from dynamical mass in detail

### 2025ApJ...985..194P: Traversing the Star-forming Main Sequence with Molecular Gas Stacks of z ∼ 1.6 Cluster Galaxies (2025; high_z_galaxies, galaxy_clusters_and_sz; observational_alma_primary)
- question: Do z~1.6 cluster galaxies, including those at low mass and well below the star-forming main sequence, have molecular gas fractions that differ from coeval field galaxies, as measured with stacked CO(2-1)?
- step 7: Compute gas masses
  - method: L'CO from Solomon & Vanden Bout; M_gas = alpha_CO L'CO / r21 [Gas Masses: "The line luminosity can be converted into a gas mass through:"]
  - parameter: r21 = 0.77 [Gas Masses: "we adopt an excitation factor correction, $r_{21}$, of 0.77"]
  - assumption: alpha_CO from stellar mass-metallicity correction (T18), weighted average 4.4-6.9 [Gas Masses: "We find the weighted average $\alpha_{CO}$ for our stacks of spectra to be between 4.4 and 6.9"]
  - validation: alpha_CO variation checked in discussion [Discussion, Variance of alpha_CO: "Nevertheless, we consider what values of $\alpha_{\textrm{CO}}$ would be required for our measured CO luminosities to be in line with the T18 field scaling relation."]
- step 9: Forward model field gas fractions
  - method: Redraw stellar masses and DeltaMS within errors 10,000 times, resample, feed to T18 at z=1.6, add 0.1 dex scatter, compare to measurements [Forward Modeling: "We Gaussian scatter the quantity log($\mu$) for each realization of “field galaxy groupings” assuming the inherent 0.1 dex scatter on the T18 relation"]
  - assumption: average redshift z=1.6 [Forward Modeling: "Using the average redshift of the groupings ($z=1.6$)"]
- result: Gas mass LM grouping = 1.3 ± 0.4 1e10 Msun [Gas Masses: "we detect average gas masses of 1.3$\pm$0.4 $\times$10$^{10}$ M$_{\odot}$, 5.6$\pm$0.6 $\times$10$^{10}$ M$_{\odot}$, and 3.1$\pm$0.4 $\times$10$^{10}$ M$_{\odot}$"]
- result: Gas mass HM-aMS = 5.6 ± 0.6 1e10 Msun [Gas Masses: "5.6$\pm$0.6 $\times$10$^{10}$ M$_{\odot}$"]
- result: Gas mass HM-bMS = 3.1 ± 0.4 1e10 Msun [Gas Masses: "3.1$\pm$0.4 $\times$10$^{10}$ M$_{\odot}$ for the LM, HM-aMS, and HM-bMS groupings"]
- result: Gas fractions LM, HM-aMS, HM-bMS = 75%, 65%, 32% ± 11%, 8%, 6% percent [Gas Masses: "gas fractions ($f_{gas} = M_{gas}/(M_{gas}+M_{*})$) of 75$\pm$11%, 65$\pm$8%, and 32$\pm$6% respectively"]
- limitation (authors): T18 is not calibrated below the SFMS; limited metallicity info; 6 of 10 HM-bMS CO-undetected galaxies have SFRs constrained only by HerMES upper limits [Comparison of CO-detected to CO-undetec…: "the T18 field scaling relation is primarily calibrated for galaxies on or above the SFMS at this redshift"]
- not stated (card): Stellar mass-metallicity relation and alpha_CO prescription details used (T18 form); CIGALE module parameters (tau, age grids, etc.); Line-free channel ranges for continuum subtraction; Per-galaxy stellar masses, SFRs, DeltaMS, redshifts; Cube image sizes and clean mask definitions; Spectral extraction aperture sizes per galaxy and exact aperture formula; Numeric flux scale uncertainty; Metallici…

### 2015ApJ...801...63M: ALMA Multi-line Imaging of the Nearby Starburst NGC 253 (2015; nearby_galaxies, astrochemistry; observational_alma_primary)
- question: What are the spatially resolved molecular line properties, chemistry, opacities and dense gas conditions across the central starburst of NGC 253 in the 3 mm band?
- step 3: Derive excitation temperature, column densities and abundances
  - method: Optically thin LTE column densities; Tex from SO(32-21)/SO(22-11) ratio; N(H2) from CO(1-0) with XCO [3.4 Excitation and Abundances: "Molecular column densities $N_{mol}$ are determined assuming optically thin LTE emission"]
  - parameter: Abundances reported for Tex 10–75 K [3.4 Excitation and Abundances: "abundances are reported for T$_{ex}$ ranging from 10 K (first number in each entry) to 75 K (second number)"]
  - assumption: XCO = 0.5e20 cm-2 (K km/s)-1, uncertain at ±2x [3.4 Excitation and Abundances: "We adopt a CO-to-H$_{2}$ conversion factor of X$_{CO} = 0.5\times 10^{20}$ cm$^{-2}$ (K km s$^{-1}$)$^{-1}$."]
  - validation: C17O/H2 compared with expected value from [CO/C17O]=1000 and [CO/H2]=1e-4 [4.1 CO Isotopologues: "The level of agreement between the two methods of constraining N(H$_{2}$) is reasonable, being less than the uncertainties in each method."]
- result: SO-derived Tex inner disk = 74 ± not stated K [3.4 Excitation and Abundances: "we estimate the inner disk to have an excitation temperature of 74 K in SO"]
- limitation (authors): Error maps too optimistic; negative bowl from missing short spacings; region 6 fluxes highly uncertain due to absorption [2 Observations and Data Reduction: "Because of this the fluxes toward this location should be considered highly uncertain."]
- not stated (card): CASA version and calibrators; Imaging weighting/robust, cell and image size, deconvolver, clean thresholds; Line-free channels for continuum; Exact beam-matching common resolution per line and mask details; LVG code availability and grid ranges; Exact line widths/velocity ranges used for integrated intensities

### 2017ApJ...843...18V: Quasar Feedback in the Ultraluminous Infrared Galaxy F11119+3257: Connecting the Accretion Disk Wind with the Large-scale Molecular Outflow (2017; agn_and_quasars, nearby_galaxies; observational_alma_primary)
- question: Does the CO(1-0) emission of the ULIRG F11119+3257 show broad wings confirming the molecular outflow, and what are its energetics compared with the OH-based estimates?
- step 5: Derive outflow mass and energetics
  - method: Mass from integrated flux with alpha_CO; Mdot = M V/R, Pdot = Mdot V, Edot = 1/2 Mdot V^2 [4.1 Energetics of the CO Outflow: "$$\dot{M}_{\rm out,CO} & = & \frac{M_{\rm out,CO}~V_{\rm out,CO}}{R_{\rm out,CO}}\\"]
  - parameter: R_out = 7 kpc, V_out = 1000 km/s [4.1 Energetics of the CO Outflow: "we adopt a conservatively low value for the radius, $R_{\rm out,CO}$ = 7 kpc, and $V_{\rm out,CO}$ = 1000 km s$^{-1}$"]
  - assumption: ULIRG-like alpha_CO = 0.8; luminosity distance 933 Mpc [4.3 Comparisons with Published Models: "ULIRG-like CO$-$to$-$H$_2$ conversion factor of $\alpha_{\rm CO}$ = 0.8 $M_\odot$ (K km s$^{-1}$ pc$^2$)$^{-1}$"]
  - validation: Compared with OH-based local and time-averaged values (Table 4) [4.2 Comparisons with the Herschel OH Ou…: "Table 4 compares the mass, momentum, and kinetic energy outflow rates derived from the new ALMA CO(1$-$0) data cube"]
- result: Outflowing molecular mass (ULIRG-like alpha_CO) = (0.6-1.4)e9 ± not stated Msun [4.1 Energetics of the CO Outflow: "This results in an outflowing molecular gas mass of $\sim$ (0.6 $-$ 1.4) $\times$ 10$^9$ $M_\odot$"]
- result: Mass outflow rate = 80-200 ± not stated Msun/yr [4.1 Energetics of the CO Outflow: "$\dot{M}_{\rm out,CO}$ = (80 $-$ 200) $M_\odot$ yr$^{-1}$"]
- result: Momentum flux = (6-13)e35 dyne = 1.5-3.0 L_AGN/c ± not stated dyne [4.1 Energetics of the CO Outflow: "$\dot{P}_{\rm out,CO}$ = (6 $-$ 13) $\times$ 10$^{35}$ dyne = (1.5 $-$ 3.0) $L_{\rm AGN}/c$"]
- result: Mechanical power = (3-6)e43 erg/s = 0.15-0.40% L_AGN ± not stated erg/s [4.1 Energetics of the CO Outflow: "(3 $-$ 6) $\times$ 10$^{43}$ ergs s$^{-1}$ = (0.15 $-$ 0.40)% $L_{\rm AGN}$"]
- result: Efficiency f_CO = 0.02-0.03 ± not stated dimensionless [4.3 Comparisons with Published Models: "we derive $f_{\rm CO}$ = 0.02 – 0.03"]
- limitation (authors): Modest angular resolution is a major limitation [5 Conclusions: "The modest angular resolution of the ALMA data set is a major limitation of our analysis."]
- not stated (card): Line-free channels used for the continuum fit; Number of clean iterations, threshold, cell and image size; Exact velocity range used for the two-Gaussian fits and the bootstrap setup; Flux calibrator and CASA/pipeline version; Source coordinates and phase center; How the rotation model velocity-gradient fit was parametrized in detail; How R_out and V_out nominal values map to the quoted mass rang…

### 2018A&A...616A..23D: The evolving jet spectrum of the neutron star X-ray binary Aql X-1 in transitional states during its 2016 outburst (2018; star_formation, transients; observational_alma_primary)
- question: How does the optically thick-to-thin jet spectral break of the neutron star LMXB Aql X-1 evolve across state transitions in its 2016 outburst, and does it move to lower frequencies in softer states as in BH XRBs?
- step 3: Classify accretion state from X-ray spectra
  - method: Fit Swift/XRT (and NuSTAR) spectra with tbabs*nthcomp(+diskbb, rfxconv), constrained by comparison with Suzaku spectra of previous outbursts [2.4 Swift and NuSTAR: "we used a basic model consisting of thermal Comptonisation absorbed from neutral material (`tbabs*nthcomp` in XSPEC) and, where necessary, we added a disc blackbody"]
  - software: XSPEC
  - parameter: min 20 counts per bin; XRT 0.4–9 keV, NuSTAR 3–30 keV [2.4 Swift and NuSTAR: "used the 0.4–9 keV energy range for analysis"]
  - assumption: 1.4 Msun neutron star, distance 5.2 kpc for Eddington fractions [3.1 Accretion state: "the Eddington fraction during obs 2a/2b is $\sim$60–65% for a 1.4 M$_{\odot}$ neutron star"]
  - fitting: chi-square fitting with simultaneous fits and tied parameters [Observations and data analysis, Swift a…: "we can attempt to constrain the two-component models by fitting all the spectra simultaneously and linking the column density of the absorbing material, expected to be constant."]
  - validation: comparison with Suzaku P0/P9, HIDs [2.4 Swift and NuSTAR: "Our obs 1 perfectly matches the P0 interval"]
- result: Eddington fraction obs 2a/2b = ~60–65% ± not stated percent [3.1 Accretion state: "the Eddington fraction during obs 2a/2b is $\sim$60–65% for a 1.4 M$_{\odot}$ neutron star"]
- limitation (authors): Observations not strictly simultaneous, spanning many hours across transitions; X-ray spectral model degeneracy [3.1 Accretion state: "Besides the spectral degeneracy, a caveat to the classification above is that the multi-wavelength observations span several hours."]
- not stated (card): Cell size, image size, deconvolver, masking and clean threshold; Which spectral windows/channels were combined for continuum images; Exact flagging steps and antenna lists in re-calibration; Whether flux calibrator models/absolute flux scale uncertainty were applied; Fit weighting and points used for spectral slopes; Parameter values imposed for obs 2a and 3 X-ray fits

### 2018ApJ...865...13T: A Galaxy-scale Fountain of Cold Molecular Gas Pumped by a Black Hole (2018; galaxy_clusters_and_sz, nearby_galaxies, agn_and_quasars; observational_alma_primary)
- question: Are the warm ionized and cold molecular gas in the Abell 2597 BCG cospatial and comoving, and does their kinematics reflect inflow, jet-driven outflow and bubble uplift (a galaxy-scale fountain) as predicted by chaotic cold accretion/preci…
- step 3: Derive molecular gas mass
  - method: Fit single Gaussian to spectrum from polygon aperture of >=3 sigma emission (10 km/s channels), convert to M_H2 with Bolatto relation [3.3 Total mass: "We fit a single Gaussian to the CO(2-1) spectrum extracted from a polygonal aperture encompassing all $\ge3\sigma$ emission"]
  - software: PySpecKit
  - parameter: fit range -600 to +600 km/s; CO(2-1)/CO(1-0)=3.2 [3.3 Total mass: "while ours is fit between $-600$ and $+600$ km s"]
  - assumption: X_CO = 2e20 (Milky Way), D_L = 374 Mpc [3.3 Total mass: "we adopt the average value for the disk of the Milky Way of $X_{\mathrm{CO}} = X_{\mathrm{CO,~MW}} = 2 \times 10^{20}$"]
  - fitting: Gaussian fit; same integral with 20/40 km/s binning and direct summation [3.3 Total mass: "Within errors, we obtain the same integral for cubes binned to 20 or 40 km s"]
  - validation: Consistency across binning and analytic integral [3.3 Total mass and mass distribution of…: "Within errors, we obtain the same integral for cubes binned to 20 or 40 km s, and an identical flux with an analytic integral of the line"]
- result: Integrated CO(2-1) flux = 7.8 ± 0.3 Jy km/s [3.3 Total mass: "$S_{\mathrm{CO}}\Delta v = 7.8\pm0.3$ Jy km s"]
- result: CO(2-1) total FWHM = 252 ± 16 km/s [3.3 Total mass: "line FWHM of $252 \pm 16$ km s"]
- result: Total H2 mass = 3.2e9 ± 0.1e9 Msun [3.3 Total mass: "$M_{\mathrm{H}_2} = \left(3.2 \pm 0.1\right) \times 10^9$"]
- limitation (authors): X_CO uncertainty may overestimate mass by a factor of a few [3.3: "we may be overestimating the total mass by a factor of a few"]
- limitation (authors): Projection effects: motions in plane of sky unknown [3.4: "unless most gas motions are contained in the plane of the sky"]
- not stated (card): CLEAN cell size, image size, niter/threshold, and masking; Line-free channels used for UVCONTSUB and fit order; Self-calibration solution intervals and number of iterations; Spectral resampling/regridding details for velocity frame; Exact smoothing kernel widths in the masked-moment code beyond FWHM=beam; Polygon aperture definitions for spectra; Flux scale uncertainty; Pipeline vs manual calibra…

### 2014ApJ...783...84S: The Evolution of Interstellar Medium Mass Probed by Dust Emission: ALMA Observations at z = 0.3-2 (2014; high_z_galaxies; observational_alma_primary)
- question: Can the Rayleigh-Jeans dust continuum measured with ALMA Band 7 be used to trace ISM mass, and how does ISM mass evolve from z=2 to 0.4 in stellar-mass-selected galaxies?
- step 1: Calibrate empirical alpha850 (L_nu/M_ISM)
  - method: Ratio of 850um specific luminosity to ISM mass for local galaxies, Planck Galactic data, and SMGs with CO(1-0) [2.2: "Based on the data shown in Fig. 1, we find a constant of proportionality between the 850µm specific luminosity and the ISM mass"]
  - parameter: beta = 1.8, Td = 25 K [2.4: "In the following, we assume T d = 25 K to characterize the bulk of the ISM mass."]
  - assumption: alpha_CO = 4.6 Msun (K km/s pc^2)^-1 for SMGs; HI set to 50% of H2 for local sample [2.5: "a standard α CO = M ISM /L CO = 4.6 M ⊙ (K km sec [−][1] pc [2] ) [−][1]"]
  - validation: Three independent calibrations agree within ~20% [2.3: "The value of the constant of proportionality between the 850µm flux and the ISM mass in the Galaxy found by the Planck Mission is therefore within 20% of that found earlier"]
- step 4: Derive gas fractions and depletion times
  - method: M_ISM/(M*+M_ISM) and tau_SF = M_ISM/<SFR> [5. STACKED SAMPLES: "The depletion timescales for the ISM via star formation are given by τ SF = M ISM / < SFR >"]
  - validation: Compared with Tacconi et al. 2013 CO gas fractions [5. STACKED SAMPLES: "Tacconi et al. (2013) surveyed 52 galaxies at z = 1 - 3 in CO(3-2) and found mean gas mass fractions of 0.33 and 0.47"]
- result: alpha850 local galaxies = 1.0 ± ±0.23 1e20 erg s^-1 Hz^-1 Msun^-1 [2.2: "= 1.0 ± 0.23 × 10 [20] ergs sec [−][1] Hz [−][1] M ⊙−1 . (7)"]
- result: alpha850 from Planck = 0.79 ± not stated 1e20 erg s^-1 Hz^-1 Msun^-1 [2.3: "= 0.79 × 10 [20] ergs/sec/Hz/M ⊙ (9)"]
- result: alpha850 SMGs = 1.01 ± ±0.52 1e20 erg s^-1 Hz^-1 Msun^-1 [Figure 4: "The average value of the luminosity-tomass ratio = 1.01 ± 0.52 × 10 [20]"]
- result: Gas mass fractions (low-z, mid-z, high-z, IR bright) = 2, 12, 14, 53 % ± ±0.5, 3, 3, 5 % [5. STACKED SAMPLES: "∼ 2 ± 0.5, 12 ± 3, 14 ± 3 and 53 ± 5 % for the low-z, mid-z, high-z and IR bright samples, respectively."]
- result: Depletion time range = 0.2-1.2 ± not stated Gyr [5. STACKED SAMPLES: "This depletion timescale is similar for the subsamples (0.2 - 1.2 Gyr)."]
- limitation (authors): Pathfinder, small samples, only most massive galaxies; results preliminary [6. SUMMARY: "Thus the evolutionary trends mentioned above are very preliminary and much larger samples are warranted."]
- not stated (card): CASA version and calibrator/flux scale details; Image size, cell size, and flux-scale uncertainty; How apertures were centered (positions from COSMOS) and pixel treatment; Exact stacking procedure (alignment, weights) and how uncertainties on stacked masses were computed; Primary beam correction not stated

## All papers in this technique

- 2012A&A...538L...9H (2012): ALMA CO and VLT/SINFONI H<SUB>2</SUB> observations of the Antennae overlap region: mass and energy dissipation
- 2013AJ....146...47I (2013): High-density Molecular Gas Properties of the Starburst Galaxy NGC 1614 Revealed with ALMA
- 2013ApJ...769L..12L (2013): Clumping and the Interpretation of kpc-scale Maps of the Interstellar Medium: Smooth H I and Clumpy, Variable H<SUB>2</SUB> Surface Density
- 2013ApJ...773L..34K (2013): Carbon Monoxide in the Cold Debris of Supernova 1987A
- 2014A&A...565A..59D (2014): ALMA resolves turbulent, rotating [CII] emission in a young starburst galaxy at z = 4.8
- 2014A&A...567A.119S (2014): ALMA-backed NIR high resolution integral field spectroscopy of the NUGA galaxy NGC 1433
- 2014A&A...567A.125G (2014): Molecular line emission in NGC 1068 imaged with ALMA. I. An AGN-driven outflow in the dense molecular gas
- 2014A&A...568A..92M (2014): Herschel-ATLAS and ALMA. HATLAS J142935.3-002836, a lensed major merger at redshift 1.027
- 2014ApJ...781L..39T (2014): Serendipitous ALMA Detection of a Distant CO-emitting X-Ray Bright Galaxy
- 2014ApJ...783...84S (2014): The Evolution of Interstellar Medium Mass Probed by Dust Emission: ALMA Observations at z = 0.3-2
- 2014ApJ...784...78R (2014): Massive Molecular Gas Flows in the A1664 Brightest Cluster Galaxy
- 2014ApJ...787...48X (2014): ALMA Observations of Warm Molecular Gas and Cold Dust in NGC 34
- 2014ApJ...790..160S (2014): ALMA Observations of a Candidate Molecular Outflow in an Obscured Quasar
- 2014ApJ...795....5O (2014): Faint Submillimeter Galaxies Revealed by Multifield Deep ALMA Observations: Number Counts, Spatial Clustering, and a Dark Submillimeter Lin…
- 2014ApJ...797...90S (2014): An Infrared-luminous Merger with Two Bipolar Molecular Outflows: ALMA and SMA Observations of NGC 3256
- 2014ApJS..214....1U (2014): Cold Molecular Gas in Merger Remnants. I. Formation of Molecular Gas Disks
- 2014MNRAS.438.1267S (2014): An ALMA survey of sub-millimetre Galaxies in the Extended Chandra Deep Field South: the far-infrared properties of SMGs
- 2015A&A...580A...1M (2015): The fast molecular outflow in the Seyfert galaxy IC 5063 as seen by ALMA
- 2015A&A...581A..85P (2015): The jet and the disk of the HH 212 low-mass protostar imaged by ALMA: SO and SO<SUB>2</SUB> emission
- 2015A&A...583A.104S (2015): The nuclear gas disk of NGC 1566 dissected by SINFONI and ALMA
- 2015A&A...584A..99E (2015): The Dragonfly Galaxy. II. ALMA unveils a triple merger and gas exchange in a hyper-luminous radio galaxy at z = 2
- 2015ApJ...798...85P (2015): CO Gas Inside the Protoplanetary Disk Cavity in HD 142527: Disk Structure from ALMA
- 2015ApJ...801...63M (2015): ALMA Multi-line Imaging of the Nearby Starburst NGC 253
- 2015ApJ...803...60S (2015): ALMA Multi-line Observations of the IR-bright Merger VV 114
- 2015ApJ...811...92C (2015): Accretion Kinematics through the Warped Transition Disk in HD142527 from Resolved CO(6-5) Observations
- 2015ApJ...811..124S (2015): Sub-kiloparsec Imaging of Cool Molecular Gas in Two Strongly Lensed Dusty, Star-forming Galaxies
- 2015ApJ...812L..23S (2015): A Higher Efficiency of Converting Gas to Stars Pushes Galaxies at z ∼ 1.6 Well Above the Star-forming Main Sequence
- 2015ApJ...813..118M (2015): Microwave Continuum Emission and Dense Gas Tracers in NGC 3627: Combining Jansky VLA and ALMA Observations
- 2015ApJ...815..103B (2015): Dense Gas Fraction and Star-formation Efficiency Variations in the Antennae Galaxies
- 2015MNRAS.448.2224C (2015): Constraining globular cluster formation through studies of young massive clusters - V. ALMA observations of clusters in the Antennae
- 2016A&A...586A..45S (2016): Star formation efficiency along the radio jet in Centaurus A
- 2016A&A...586L...7B (2016): An ALMA view of the interstellar medium of the z = 4.77 lensed starburst SPT-S J213242-5802.9
- 2016A&A...587A..44P (2016): Sub-kpc star formation law in the local luminous infrared galaxy IC 4687 as seen by ALMA
- 2016A&A...590A..73A (2016): A precessing molecular jet signaling an obscured, growing supermassive black hole in NGC 1377?
- 2016A&A...591A..73G (2016): ALMA finds dew drops in the dusty spider's web
- 2016A&A...593L...2N (2016): Planck's Dusty GEMS. II. Extended [CII] emission and absorption in the Garnet at z = 3.4 seen with ALMA
- 2016A&A...594A..81P (2016): High-velocity extended molecular outflow in the star-formation dominated luminous infrared galaxy ESO 320-G030
- 2016A&A...595A..72M (2016): GRB 980425 host: [C II], [O I], and CO lines reveal recent enhancement of star formation due to atomic gas inflow
- 2016A&A...595L...7D (2016): ALMA reveals optically thin, highly excited CO gas in the jet-driven winds of the galaxy IC 5063
- 2016ApJ...819...82S (2016): Properties of the Interstellar Medium in Star-Forming Galaxies at z ~ 1.4 Revealed with ALMA
- 2016ApJ...820...83S (2016): ISM Masses and the Star formation Law at Z = 1 to 6: ALMA Observations of Dust Continuum in 145 Galaxies in the COSMOS Survey Field
- 2016ApJ...820L..39N (2016): First Connection between Cold Gas in Emission and Absorption: CO Emission from a Galaxy-Quasar Pair
- 2016ApJ...821..112K (2016): SMA Observations of the Extended <SUP>12</SUP>CO(J = 6-5) Emission in the Starburst Galaxy NGC 253
- 2016ApJ...822...80S (2016): The Redshift Distribution of Dusty Star-forming Galaxies from the SPT Survey
- 2016ApJ...823...26E (2016): High Star Formation Rates in Turbulent Atomic-dominated Gas in the Interacting Galaxies IC 2163 and NGC 2207
- 2016ApJ...823...51B (2016): Toward Precision Black Hole Masses with ALMA: NGC 1332 as a Case Study in Molecular Disk Dynamics
- 2016ApJ...823...68S (2016): Gas Dynamics and Outflow in the Barred Starburst Galaxy NGC 1808 Revealed with ALMA
- 2016ApJ...827...34O (2016): Witnessing the Birth of the Red Sequence: ALMA High-resolution Imaging of [C II] and Dust in Two Interacting Ultra-red Starbursts at z = 4.…
- 2016ApJ...828...46A (2016): ALMA Survey of Lupus Protoplanetary Disks. I. Dust and Gas Masses
- 2016ApJ...831...32N (2016): A Study of the Relation between Star Formation and Molecular Clumps on Subparsec Scales in 30 Doradus
- 2016ApJ...831..161K (2016): Ocular Shock Front in the Colliding Galaxy IC 2163
- 2016ApJ...832..142Z (2016): The Molecular Wind in the Nearest Seyfert Galaxy Circinus Revealed by ALMA
- 2016ApJ...832..148V (2016): Molecular Gas Along a Bright Hα Filament in 2A 0335+096 Revealed by ALMA
- 2016ApJ...833...12R (2016): VLA and ALMA Imaging of Intense Galaxy-wide Star Formation in z ∼ 2 Galaxies
- 2016ApJ...833...68A (2016): The ALMA Spectroscopic Survey in the Hubble Ultra Deep Field: Continuum Number Counts, Resolved 1.2 mm Extragalactic Background, and Proper…
- 2016ApJ...833...69D (2016): ALMA Spectroscopic Survey in the Hubble Ultra Deep Field: CO Luminosity Functions and the Evolution of the Cosmic Density of Molecular Gas
- 2016ApJ...833..112S (2016): Gas Fraction and Depletion Time of Massive Star-forming Galaxies at z ~ 3.2: No Change in Global Star Formation Process out to z &gt; 3
- 2016ApJ...833L...6C (2016): ALMA Reveals Potential Localized Dust Enrichment from Massive Star Clusters in II Zw 40
- 2016MNRAS.458.3134R (2016): ALMA observations of cold molecular gas filaments trailing rising radio bubbles in PKS 0745-191
- 2016NatAs...1E...3P (2016): Large molecular gas reservoirs in ancestors of Milky Way-mass galaxies nine billion years ago
- 2016NatSR...626896A (2016): Kennicutt-Schmidt Law in the Central Region of NGC 4321 as Seen by ALMA
- 2017A&A...599A.113M (2017): Lupus disks with faint CO isotopologues: low gas/dust or high carbon depletion?
- 2017A&A...600A..62P (2017): The hybrid disks: a search and study to better understand evolution of disks
- 2017A&A...602A..11P (2017): ALMA reveals starburst-like interstellar medium conditions in a compact star-forming galaxy at z 2 using [CI] and CO
- 2017A&A...602A..49H (2017): VALES. II. The physical conditions of interstellar gas in normal star-forming galaxies up to z = 0.2 revealed by ALMA
- 2017A&A...602L...9M (2017): On the Kennicutt-Schmidt scaling law of submillimetre galaxies
- 2017A&A...604A...6S (2017): The physical and chemical structure of Sagittarius B2. II. Continuum millimeter emission of Sgr B2(M) and Sgr B2(N) with ALMA
- 2017A&A...604A.117C (2017): Planck's dusty GEMS. IV. Star formation and feedback in a maximum starburst at z = 3 seen at 60-pc resolution
- 2017A&A...606A..17M (2017): An ALMA survey of submillimetre galaxies in the COSMOS field: Physical properties derived from energy balance spectral energy distribution …
- 2017A&A...608A..38O (2017): Properties of the molecular gas in the fast outflow in the Seyfert galaxy IC 5063
- 2017A&A...608A..98S (2017): Inefficient jet-induced star formation in Centaurus A. High resolution ALMA observations of the northern filaments
- 2017ApJ...835..174S (2017): Spatially resolved CO SLED of the Luminous Merger Remnant NGC 1614 with ALMA
- 2017ApJ...835..278S (2017): Physical Properties of Molecular Clouds at 2 pc Resolution in the Low-metallicity Dwarf Galaxy NGC 6822 and the Milky Way
- 2017ApJ...835L..11T (2017): Grand-design Spiral Arms in a Young Forming Circumstellar Disk
- 2017ApJ...836..123L (2017): CO-DARK Star Formation and Black Hole Activity in 3C 368 at Z = 1.131: Coeval Growth of Stellar and Supermassive Black Hole Masses
- 2017ApJ...836..130R (2017): Alma Observations of Massive Molecular Gas Filaments Encasing Radio Bubbles in the Phoenix Cluster
- 2017ApJ...837...60B (2017): The ALMA View of the OMC1 Explosion in Orion
- 2017ApJ...838..146L (2017): ALMA Observations of the Interaction of a Radio Jet with Molecular Gas in Minkowski's Object
- 2017ApJ...840....8S (2017): Luminous Infrared Galaxies with the Submillimeter Array. V. Molecular Gas in Intermediate to Late-stage Mergers
- 2017ApJ...841...43E (2017): ALMA CO Clouds and Young Star Complexes in the Interacting Galaxies IC 2163 and NGC 2207
- 2017ApJ...841L..25T (2017): Rotating Starburst Cores in Massive Galaxies at z = 2.5
- 2017ApJ...842L..15S (2017): ISM Properties of a Massive Dusty Star-forming Galaxy Discovered at z ∼ 7
- 2017ApJ...842L..21N (2017): ALMA Observations of Gas-rich Galaxies in z ∼ 1.6 Galaxy Clusters: Evidence for Higher Gas Fractions in High-density Environments
- 2017ApJ...843...18V (2017): Quasar Feedback in the Ultraluminous Infrared Galaxy F11119+3257: Connecting the Accretion Disk Wind with the Large-scale Molecular Outflow
- 2017ApJ...843..136E (2017): Disentangling the Circumnuclear Environs of Centaurus A. III. An Inner Molecular Ring, Nuclear Shocks, and the CO to Warm H<SUB>2</SUB> Int…
- 2017ApJ...843..150F (2017): A Three-dimensional View of Turbulence: Constraints on Turbulent Motions in the HD 163296 Protoplanetary Disk Using DCO<SUP>+</SUP>
- 2017ApJ...844...99L (2017): An ALMA Survey of CO Isotopologue Emission from Protoplanetary Disks in Chamaeleon I
- 2017ApJ...844..123F (2017): The Circumgalactic Medium of Submillimeter Galaxies. II. Unobscured QSOs within Dusty Starbursts and QSO Sightlines with Impact Parameters …
- 2017ApJ...845..154V (2017): Molecular Gas in Three z ∼ 7 Quasar Host Galaxies
- 2017ApJ...845..170B (2017): ALMA Observations of Circumnuclear Disks in Early-type Galaxies: <SUP>12</SUP>CO(2-1) and Continuum Properties
- 2017ApJ...846...73T (2017): ALMA Detects CO(3-2) within a Super Star Cluster in NGC 5253
- 2017ApJ...846..108C (2017): A Spatially Resolved Study of Cold Dust, Molecular Gas, H II Regions, and Stars in the z = 2.12 Submillimeter Galaxy ALESS67.1
- 2017ApJ...846L..14S (2017): Massive Quenched Galaxies at z ∼ 0.7 Retain Large Molecular Gas Reservoirs
- 2017ApJ...846L..26W (2017): An ALMA Dynamical Mass Estimate of the Proposed Planetary-mass Companion FW Tau C
- 2017ApJ...848..101V (2017): A <SUP>13</SUP>CO Detection in a Brightest Cluster Galaxy
- 2017ApJ...848L...7C (2017): ALMA Shows that Gas Reservoirs of Star-forming Disks over the Past 3 Billion Years Are Not Predominantly Molecular
- 2017ApJ...849...90S (2017): Evolution of Molecular Clouds in the Superwind Galaxy NGC 1808 Probed by ALMA Observations
- 2017ApJ...849..154S (2017): ALMA Pinpoints a Strong Overdensity of U/LIRGs in the Massive Cluster XCS J2215 at z = 1.46
- 2017ApJ...850...54C (2017): ALMA CO(3-2) Observations of Star-forming Filaments in a Gas-poor Dwarf Spheroidal Galaxy
- 2017ApJ...850..180J (2017): Dynamical Characterization of Galaxies at z ∼ 4-6 via Tilted Ring Fitting to ALMA [C II] Observations
- 2017ApJ...851...18L (2017): SDSS-IV MaNGA-resolved Star Formation and Molecular Gas Properties of Green Valley Galaxies: A First Look with ALMA and MaNGA
- 2017ApJ...851...98T (2017): No Sign of Strong Molecular Gas Outflow in an Infrared-bright Dust-obscured Galaxy with Strong Ionized-gas Outflow
- 2017ApJ...851..126V (2017): Galactic-scale Feedback Observed in the 3C 298 Quasar Host Galaxy
- 2017MNRAS.465.4390B (2017): The discovery of gas-rich, dusty starbursts in luminous reddened quasars at z ∼ 2.5 with ALMA
- 2017MNRAS.466..138K (2017): A merger in the dusty, z = 7.5 galaxy A1689-zD1?
- 2017MNRAS.466.2825B (2017): ALMA observations of atomic carbon in z ∼ 4 dusty star-forming galaxies
- 2017MNRAS.468.3468G (2017): Molecular gas on large circumgalactic scales at z = 3.47
- 2017MNRAS.468L..87C (2017): New ALMA constraints on the star-forming interstellar medium at low metallicity: a 50 pc view of the blue compact dwarf galaxy SBS 0335-052
- 2017MNRAS.469.4683C (2017): ALMA constraints on star-forming gas in a prototypical z = 1.5 clumpy galaxy: the dearth of CO(5-4) emission from UV-bright clumps
- 2017MNRAS.470L..64P (2017): CO excitation in the Seyfert galaxy NGC 7130
- 2018A&A...613A..34P (2018): ALMA view of RX J1131-1231: Sub-kpc CO (2-1) mapping of a molecular disk in a lensed star-forming quasar host galaxy
- 2018A&A...614A..42M (2018): ALMA observations of AGN fuelling. The case of PKS B1718-649
- 2018A&A...616A..23D (2018): The evolving jet spectrum of the neutron star X-ray binary Aql X-1 in transitional states during its 2016 outburst
- 2018A&A...617A..54L (2018): Molecular gas and dark neutral medium in the outskirts of Chamaeleon
- 2018A&A...618A.120L (2018): The HH30 edge-on T Tauri star. A rotating and precessing monopolar outflow scrutinized by ALMA
- 2018A&A...619A..39F (2018): The dense molecular gas in the z ∼ 6 QSO SDSS J231038.88+185519.7 resolved by ALMA
- 2018A&A...620A.115B (2018): Dense-gas tracers and carbon isotopes in five 2.5 &lt; z &lt; 4 lensed dusty star-forming galaxies from the SPT SMG sample
- 2018ApJ...853..149S (2018): Revisiting the Extended Schmidt Law: The Important Role of Existing Stars in Regulating Star Formation
- 2018ApJ...853..195W (2018): Herschel and ALMA Observations of Massive SZE-selected Clusters
- 2018ApJ...854...83T (2018): Optical, Near-IR, and Sub-mm IFU Observations of the Nearby Dual Active Galactic Nuclei MRK 463
- 2018ApJ...854...90E (2018): Molecular Gas Properties in M83 from CO PDFs
- 2018ApJ...854..130W (2018): The Orbit of the Companion to HD 100453A: Binary-driven Spiral Arms in a Protoplanetary Disk
- 2018ApJ...854L...4R (2018): Cospatial Star Formation and Supermassive Black Hole Growth in z ∼ 3 Galaxies: Evidence for In Situ Co-evolution
- 2018ApJ...856...72O (2018): An Extreme Protocluster of Luminous Dusty Starbursts in the Early Universe
- 2018ApJ...856...97S (2018): Dense Molecular Gas in the Starburst Nucleus of NGC 1808
- 2018ApJ...856..118H (2018): Molecular Gas Reservoirs in Cluster Galaxies at z = 1.46
- 2018ApJ...856L..12N (2018): Molecular Emission from a Galaxy Associated with a z ∼ 2.2 Damped Lyα Absorber
- 2018ApJ...857...19F (2018): The ALMA View of GMCs in NGC 300: Physical Properties and Scaling Relations at 10 pc Resolution
- 2018ApJ...858...90G (2018): Dense Gas, Dynamical Equilibrium Pressure, and Star Formation in Nearby Star-forming Galaxies
- 2018ApJ...859...35G (2018): The Dual Role of Starbursts and Active Galactic Nuclei in Driving Extreme Molecular Outflows
- 2018ApJ...860...87F (2018): The Discovery of a New Massive Molecular Gas Component Associated with the Submillimeter Galaxy SMM J02399-0136
- 2018ApJ...860..103S (2018): Molecular Gas Contents and Scaling Relations for Massive, Passive Galaxies at Intermediate Redshifts from the LEGA-C Survey
- 2018ApJ...860..111D (2018): Similar Scaling Relations for the Gas Content of Galaxies Across Environments to z ∼ 3.5
- 2018ApJ...860..172S (2018): Cloud-scale Molecular Gas Properties in 15 Nearby Galaxies
- 2018ApJ...861...43P (2018): Hidden in Plain Sight: A Massive, Dusty Starburst in a Galaxy Protocluster at z = 5.7 in the COSMOS Field
- 2018ApJ...861..123F (2018): Why Post-starburst Galaxies Are Now Quiescent
- 2018ApJ...861L..18U (2018): Star Formation Efficiency per Free-fall Time in nearby Galaxies
- 2018ApJ...862....8T (2018): Warm CO Gas Generated by Possible Turbulent Shocks in a Low-mass Star-forming Dense Core in Taurus
- 2018ApJ...862...64S (2018): Deciphering the Activity and Quiescence of High-redshift Cluster Environments: ALMA Observations of Cl J1449+0856 at z = 2
- 2018ApJ...863..143C (2018): ALMA [C I]<SUP>3</SUP> P <SUB>1</SUB>-<SUP>3</SUP> P <SUB>0</SUB> Observations of NGC 6240: A Puzzling Molecular Outflow, and the Role of O…
- 2018ApJ...863..193V (2018): Molecular Gas Filaments and Star-forming Knots Beneath an X-Ray Cavity in RXC J1504-0248
- 2018ApJ...864...38L (2018): CO (7-6), [C I] 370 μm, and [N II] 205 μm Line Emission of the QSO BRI 1335-0417 at Redshift 4.407
- 2018ApJ...864L..11X (2018): Flat Rotation Curves Found in Merging Dusty Starbursts at z = 2.3 through Tilted-ring Modeling
- 2018ApJ...865...13T (2018): A Galaxy-scale Fountain of Cold Molecular Gas Pumped by a Black Hole
- 2018ApJ...866..117C (2018): ALMA Observation of NGC 5135: The Circumnuclear CO (6-5) and Dust Continuum Emission at 45 pc Resolution
- 2018ApJ...866L..12G (2018): A Magnified View of Circumnuclear Star Formation and Feedback around an Active Galactic Nucleus at z = 2.6
- 2018ApJ...867...48I (2018): Circumnuclear Multiphase Gas in the Circinus Galaxy. II. The Molecular and Atomic Obscuring Structures Revealed with ALMA
- 2018ApJ...867..140L (2018): Resolving Star Formation on Subkiloparsec Scales in the High-redshift Galaxy SDP.11 Using Gravitational Lensing
- 2018ApJ...867..165B (2018): Dense Molecular Filaments Feeding a Starburst: ALMA Maps of CO(3-2) in Henize 2-10
- 2018ApJ...867..166S (2018): Internal Structures of Molecular Clouds in the LMC Revealed by ALMA
- 2018ApJ...868...95M (2018): ALMA Observations of HCN and HCO<SUP>+</SUP> Outflows in the Merging Galaxy NGC 3256
- 2018ApJ...868L..38G (2018): Do Spectroscopic Dense Gas Fractions Track Molecular Cloud Surface Densities?
- 2018MNRAS.474.3640M (2018): CO excitation in the Seyfert galaxy NGC 34: stars, shock or AGN driven?
- 2018MNRAS.474.4039M (2018): ALMA + VLT observations of a damped Lyman-α absorbing galaxy: massive, wide CO emission, gas-rich but with very low SFR
- 2018MNRAS.474.4988S (2018): A disrupted molecular torus around Eta Carinae as seen in <SUP>12</SUP>CO with ALMA
- 2018MNRAS.475..448T (2018): Mapping jet-ISM interactions in X-ray binaries with ALMA: a GRS 1915+105 case study
- 2018MNRAS.475.3004S (2018): ALMA observation of the disruption of molecular gas in M87
- 2018MNRAS.475.5322S (2018): Deuterated formaldehyde in the low-mass protostar HH212
- 2018MNRAS.475L..52S (2018): Imaging the molecular outflows of the prototypical ULIRG NGC 6240 with ALMA
- 2018MNRAS.476..122V (2018): An ALMA view of star formation efficiency suppression in early-type galaxies after gas-rich minor mergers
- 2018MNRAS.476.3956T (2018): ALMA view of a massive spheroid progenitor: a compact rotating core of molecular gas in an AGN host at z = 2.226
- 2018MNRAS.477.4380S (2018): Testing star formation laws in a starburst galaxy at redshift 3 resolved with ALMA
- 2018MNRAS.477L..60E (2018): Giant galaxy growing from recycled gas: ALMA maps the circumgalactic molecular medium of the Spiderweb in [C I]
- 2018MNRAS.478.3120A (2018): Characterizing the circum-galactic medium of damped Lyman-α absorbing galaxies
- 2018MNRAS.479.2126F (2018): ALMA observations of a metal-rich damped Ly α absorber at z = 2.5832: evidence for strong galactic winds in a galaxy group
- 2018MNRAS.479.3879W (2018): An ALMA survey of CO in submillimetre galaxies: companions, triggering, and the environment in blended sources
- 2018MNRAS.479.5440L (2018): Neutral versus ionized gas kinematics at z ≃ 2.6: the AGN-host starburst galaxy PKS 0529-549
- 2018MNRAS.481.4931E (2018): ALMA reveals the aftermath of a white dwarf-brown dwarf merger in CK Vulpeculae
- 2018Natur.553...51M (2018): Galaxy growth in a massive halo in the first billion years of cosmic history
- 2018Natur.556..469M (2018): A massive core for a cluster of galaxies at a redshift of 4.3
- 2018PASJ...70...73H (2018): ALMA <SUP>12</SUP>CO (J = 1-0) imaging of the nearby galaxy M 83: Variations in the efficiency of star formation in giant molecular clouds
- 2018PASJ...70L...1M (2018): ALMA [C I] observations toward the central region of Seyfert galaxy NGC 613
- 2018PASJ...70L...6K (2018): A high dust emissivity index β for a CO-faint galaxy in a filamentary Lyα nebula at z = 3.1
- 2018Sci...362.1034D (2018): The multiple merger assembly of a hyperluminous obscured quasar at redshift 4.6
- 2019A&A...621A..83S (2019): Outflows in the inner kiloparsec of NGC 1566 as revealed by molecular (ALMA) and ionized gas (Gemini-GMOS/IFU) kinematics
- 2019A&A...623A..66B (2019): ALMA CO(2-1) observations in the XUV disk of M83
- 2019A&A...623A..79C (2019): ALMA observations of molecular tori around massive black holes
- 2019A&A...623A..96Y (2019): Signs of outflow feedback from a nearby young stellar object on the protostellar envelope around HL Tauri
- 2019A&A...628A..23A (2019): Imaging the molecular interstellar medium in a gravitationally lensed star-forming galaxy at z = 5.7
- 2019A&A...628A..65A (2019): Nuclear molecular outflow in the Seyfert galaxy NGC 3227
- 2019A&A...628A.118B (2019): The gentle monster PDS 456. Kiloparsec-scale molecular outflow and its implications for QSO feedback
- 2019A&A...631A.167D (2019): A dense, solar metallicity ISM in the z = 4.2 dusty star-forming galaxy SPT 0418-47
- 2019A&A...632A..33A (2019): ALMA captures feeding and feedback from the active galactic nucleus in NGC 613
- 2019A&A...632A..61G (2019): ALMA images the many faces of the <ASTROBJ>NGC 1068</ASTROBJ> torus and its surroundings
- 2019A&A...632A..66O (2019): ALMA observations of PKS 1549-79: a case of feeding and feedback in a young radio quasar
- 2019AJ....157..131B (2019): Kiloparsec-Scale Variations in the Star Formation Efficiency of Dense Gas: The Antennae Galaxies (NGC 4038/39)
- 2019ApJ...870...39V (2019): ALMA Observations of the Molecular Gas in the Elliptical Galaxy NGC 3557
- 2019ApJ...871...85L (2019): The ISM Properties and Gas Kinematics of a Redshift 3 Massive Dusty Star-forming Galaxy
- 2019ApJ...871..100H (2019): ALMA Observations of the Protostellar Disk around the VeLLO IRAS 16253-2429
- 2019ApJ...873L..19B (2019): Extremely Low Molecular Gas Content in a Compact, Quiescent Galaxy at z = 1.522
- 2019ApJ...874...53B (2019): Environmental Effect on the Interstellar Medium in Galaxies across the Cosmic Web at z = 0.73
- 2019ApJ...874L..30V (2019): 400 pc Imaging of a Massive Quasar Host Galaxy at a Redshift of 6.6
- 2019ApJ...875L...8R (2019): An Accreting Supermassive Black Hole Irradiating Molecular Gas in NGC 2110
- 2019ApJ...876...72L (2019): Sulfur Chemistry in Protoplanetary Disks: CS and H<SUB>2</SUB>CS
- 2019ApJ...876...91H (2019): Molecular Gas Properties in the Host Galaxy of GRB 080207
- 2019ApJ...876..130H (2019): ALMA Reveals Potential Evidence for Spiral Arms, Bars, and Rings in High-redshift Submillimeter Galaxies
- 2019ApJ...877L..38R (2019): Active Galactic Nuclei in Dusty Starbursts at z = 2: Feedback Still to Kick in
- 2019ApJ...879...75H (2019): Jet-driven Galaxy-scale Gas Outflows in the Hyperluminous Quasar 3C 273
- 2019ApJ...879L..13M (2019): ALMA Observations of Molecular Gas in the Host Galaxy of AT2018cow
- 2019ApJ...880...15K (2019): The Molecular Gas Reservoirs of z ∼ 2 Galaxies: A Comparison of CO(1-0) and Dust-based Molecular Gas Masses
- 2019ApJ...880L..19K (2019): A Luminous Molecular Gas Pair beyond Redshift 7
- 2019ApJ...881...63N (2019): An ALMA Multiline Survey of the Interstellar Medium of the Redshift 7.5 Quasar Host Galaxy J1342+0928
- 2019ApJ...881..147S (2019): Positive and Negative Feedback of AGN Outflows in NGC 5728
- 2019ApJ...882....1L (2019): CO and Fine-structure Lines Reveal Low Metallicity in a Stellar-mass-rich Galaxy at z ∼ 1?
- 2019ApJ...882....5W (2019): The Kennicutt-Schmidt Law and Gas Scale Height in Luminous and Ultraluminous Infrared Galaxies
- 2019ApJ...882...31A (2019): A Superluminous Supernova in High Surface Density Molecular Gas within the Bar of a Metal-rich Galaxy
- 2019ApJ...882..136A (2019): The ALMA Spectroscopic Survey in the Hubble Ultra Deep Field: Evolution of the Molecular Gas in CO-selected Galaxies
- 2019ApJ...882..137P (2019): The ALMA Spectroscopic Survey in the HUDF: the Molecular Gas Content of Galaxies and Tensions with IllustrisTNG and the Santa Cruz SAM
- 2019ApJ...882..138D (2019): The ALMA Spectroscopic Survey in the HUDF: CO Luminosity Functions and the Molecular Gas Content of Galaxies through Cosmic History
- 2019ApJ...883..180H (2019): First Subarcsecond Submillimeter-wave [C I] Image of 49 Ceti with ALMA
- 2019ApJ...883..193N (2019): The ALMA Discovery of the Rotating Disk and Fast Outflow of Cold Molecular Gas in NGC 1275
- 2019ApJ...884L..33L (2019): The ALMaQUEST Survey: The Molecular Gas Main Sequence and the Origin of the Star-forming Main Sequence
- 2019ApJ...885L..21M (2019): How to Fuel an AGN: Mapping Circumnuclear Gas in NGC 6240 with ALMA
- 2019ApJ...885L..39H (2019): First Detection of Submillimeter-wave [<SUP>13</SUP>C I] <SUP>3</SUP> P <SUB>1</SUB>-<SUP>3</SUP> P <SUB>0</SUB> Emission in a Gaseous Debr…
- 2019ApJ...886...15T (2019): An ALMA View of Molecular Filaments in the Large Magellanic Cloud. II. An Early Stage of High-mass Star Formation Embedded at Colliding Clo…
- 2019ApJ...887...74F (2019): ALMA Reveals a Gas-rich, Maximum Starburst in the Hyperluminous, Dust-obscured Quasar W0533-3401 at z ∼ 2.9
- 2019ApJ...887...88E (2019): Star Formation Efficiencies at Giant Molecular Cloud Scales in the Molecular Disk of the Elliptical Galaxy NGC 5128 (Centaurus A)
- 2019ApJ...887..144J (2019): Discovery of Four Apparently Cold Dusty Galaxies at z = 3.62-5.85 in the COSMOS Field: Direct Evidence of Cosmic Microwave Background Impac…
- 2019ApJ...887..149B (2019): Origins of Molecular Clouds in Early-type Galaxies
- 2019ApJ...887..183Z (2019): On the Gas Content, Star Formation Efficiency, and Environmental Quenching of Massive Galaxies in Protoclusters at z ≈ 2.0-2.5
- 2019ApJS..241...19I (2019): ALMA Spatially Resolved Dense Molecular Gas Survey of Nearby Ultraluminous Infrared Galaxies
- 2019BAAA...61..134V (2019): Molecular Clouds resolved with ALMA ^{12}CO J=1-0 and J=2-1 observations towards the Magellanic Bridge
- 2019MNRAS.482.1499M (2019): VALES V: a kinematic analysis of the molecular gas content in H-ATLAS galaxies at z ∼ 0.03-0.35 using ALMA
- 2019MNRAS.482.3135B (2019): The relationship between dust and [C I] at z = 1 and beyond
- 2019MNRAS.482L..65K (2019): ALMACAL V: absorption-selected galaxies with evidence for excited ISMs
- 2019MNRAS.484.4239R (2019): The AGN fuelling/feedback cycle in nearby radio galaxies I. ALMA observations and early results
- 2019MNRAS.485..229R (2019): Deep and narrow CO absorption revealing molecular clouds in the Hydra-A brightest cluster galaxy
- 2019MNRAS.485.1595P (2019): Multiphase circumgalactic medium probed with MUSE and ALMA
- 2019MNRAS.485.2092C (2019): Suppressed CO emission and high G/D ratios in z = 2 galaxies with sub-solar gas-phase metallicity
- 2019MNRAS.486.2366M (2019): The molecular gas properties in the gravitationally lensed merger HATLAS J142935.3-002836
- 2019MNRAS.487.4305S (2019): Testing star formation laws on spatially resolved regions in a z ≈ 4.3 starburst galaxy
- 2019MNRAS.488.3904L (2019): Survival of molecular gas in a stellar feedback-driven outflow witnessed with the MUSE TIMER project and ALMA
- 2019MNRAS.488.5029H (2019): Star-formation rates of two GRB host galaxies at z ∼ 2 and a [C II] deficit observed with ALMA
- 2019MNRAS.489..427I (2019): Hyperluminous starburst gives up its secrets
- 2019MNRAS.489.1927S (2019): Testing the blast-wave AGN feedback scenario in MCG-03-58-007
- 2019MNRAS.490.1220K (2019): ALMACAL - VI. Molecular gas mass density across cosmic time via a blind search for intervening molecular absorbers
- 2019MNRAS.490.5860S (2019): The multiphase gas structure and kinematics in the circumnuclear region of NGC 5728
- 2019Natur.569..519K (2019): Fast and inefficient star formation due to short-lived molecular clouds and rapid feedback
- 2019PASJ...71...40T (2019): Environmental impacts on molecular gas in protocluster galaxies at z ∼ 2
- 2019PASJ...71...44H (2019): Formation of high-mass stars in an isolated environment in the Large Magellanic Cloud
- 2019PASJ...71...85M (2019): Complex distribution and velocity field of molecular gas in NGC 1316 as revealed by the Morita Array of ALMA
- 2020A&A...633A.127F (2020): A CO molecular gas wind 340 pc away from the Seyfert 2 nucleus in ESO 420-G13 probes an elusive radio jet
- 2020A&A...636A..37D (2020): Dust and gas content of high-redshift galaxies hosting obscured AGN in the Chandra Deep Field-South
- 2020A&A...639A..43A (2020): Cold molecular gas and PAH emission in the nuclear and circumnuclear regions of Seyfert galaxies
- 2020A&A...641A.151S (2020): Molecular gas in the central region of NGC 7213
- 2020A&A...641A.155V (2020): CO emission in distant galaxies on and above the main sequence
- 2020A&A...642A.155Z (2020): GOODS-ALMA: Optically dark ALMA galaxies shed light on a cluster in formation at z = 3.5
- 2020A&A...643A..89P (2020): Excitation and acceleration of molecular outflows in LIRGs: The extended ESO 320-G030 outflow on 200-pc scales
- 2020ApJ...889....9M (2020): GASP. XXII. The Molecular Gas Content of the JW100 Jellyfish Galaxy at z ∼ 0.05: Does Ram Pressure Promote Molecular Gas Formation?
- 2020ApJ...889..162L (2020): Probing the Full CO Spectral Line Energy Distribution (SLED) in the Nuclear Region of a Quasar-starburst System at z = 6.003
- 2020ApJ...889L...4L (2020): Revealing the CO X-factor in Dark Molecular Gas through Sensitive ALMA Absorption Observations
- 2020ApJ...890...29F (2020): Multiphase Gas Flows in the Nearby Seyfert Galaxy ESO428-G014. Paper I
- 2020ApJ...890L..10K (2020): Systematic Variations of CO J = 2-1/1-0 Ratio and Their Implications in The Nearby Barred Spiral Galaxy M83
- 2020ApJ...891...83C (2020): ALMA Reveals the Molecular Gas Properties of Five Star-forming Galaxies across the Main Sequence at 3
- 2020ApJ...892...68N (2020): The MBHBM<SUB>⋆</SUB> Project. I. Measurement of the Central Black Hole Mass in Spiral Galaxy NGC 3504 Using Molecular Gas Kinematics
- 2020ApJ...892..119M (2020): Measuring the Heating and Cooling of the Interstellar Medium at High Redshift: PAH and [C II] Observations of the Same Star-forming Galaxie…
- 2020ApJ...894...28D (2020): From Nuclear to Circumgalactic: Zooming in on AGN-driven Outflows at z ∼ 2.2 with SINFONI
- 2020ApJ...897L..19M (2020): Discovery of a [C I]-faint, CO-bright Galaxy: ALMA Observations of the Merging Galaxy NGC 6052
- 2020ApJ...897L..30M (2020): The High Molecular Gas Content, and the Efficient Conversion of Neutral into Molecular Gas, in Jellyfish Galaxies
- 2020ApJ...898...61I (2020): Circumnuclear Molecular Gas in Low-redshift Quasars and Matched Star-forming Galaxies
- 2020ApJ...898...75I (2020): ALMA Observations of Multiple CO and C Lines toward the Active Galactic Nucleus of NGC 7469: An X-Ray-dominated Region Caught in the Act
- 2020ApJ...901...79A (2020): The ALMA Spectroscopic Survey in the Hubble Ultra Deep Field: The Nature of the Faintest Dusty Star-forming Galaxies
- 2020ApJ...901..141K (2020): An Intensity Mapping Detection of Aggregate CO Line Emission at 3 mm
- 2020ApJ...901..151S (2020): Molecular Gas Outflow in the Starburst Galaxy NGC 1482
- 2020ApJ...901L...5K (2020): High Molecular Gas Masses in Absorption-selected Galaxies at z ≍ 2
- 2020ApJ...902..109B (2020): The ALMA Spectroscopic Survey in the Hubble Ultra Deep Field: CO Excitation and Atomic Carbon in Star-forming Galaxies at z = 1-3
- 2020ApJ...902..110D (2020): The ALMA Spectroscopic Survey in the Hubble Ultra Deep Field: Multiband Constraints on Line-luminosity Functions and the Cosmic Density of …
- 2020ApJ...903...94M (2020): ALMA Observations of Giant Molecular Clouds in M33. II. Triggered High-mass Star Formation by Multiple Gas Colliding Events at the NGC 604 …
- 2020ApJ...903..145L (2020): ALMaQUEST. IV. The ALMA-MaNGA QUEnching and STar Formation (ALMaQUEST) Survey
- 2020ApJ...905..147Y (2020): The ALPINE-ALMA [C II] Survey: [C II] 158 μm Emission Line Luminosity Functions at z ∼ 4-6
- 2020MNRAS.493.3744F (2020): SMM J04135+10277: a distant QSO-starburst system caught by ALMA
- 2020MNRAS.494.2131F (2020): Fast cloud-cloud collisions in a strongly barred galaxy: suppression of massive star formation
- 2020MNRAS.495.3840M (2020): A large amount of diffuse molecular gases in the bar of the strongly barred galaxy NGC 1300: cause of the low star formation efficiency
- 2020MNRAS.496..394R (2020): Illuminating a tadpole's metamorphosis II: observing the ongoing transformation with ALMA
- 2020MNRAS.496.4061D (2020): Revealing the intermediate-mass black hole at the heart of the dwarf galaxy NGC 404 with sub-parsec resolution ALMA observations
- 2020MNRAS.497.2771M (2020): VALES VI: ISM enrichment in star-forming galaxies up to z ∼ 0.2 using <SUP>12</SUP>CO(1-0), <SUP>13</SUP>CO(1-0), and C<SUP>18</SUP>O(1-0) …
- 2020MNRAS.499..193K (2020): Measuring the mixing scale of the ISM within nearby spiral galaxies
- 2020MNRAS.499.2534K (2020): Resolved star formation in the metal-poor star-forming region Magellanic Bridge C
- 2020NatAs...4..670A (2020): Infalling gas in a Lyman-α blob
- 2020Natur.581..269N (2020): A cold, massive, rotating disk galaxy 1.5 billion years after the Big Bang
- 2021A&A...645A.120F (2021): ALMA and MUSE observations reveal a quiescent multi-phase circumgalactic medium around the z ≃ 3.6 radio galaxy 4C 19.71
- 2021A&A...646A...1K (2021): Molecular remnant of Nova 1670 (CK Vulpeculae). II. A three-dimensional view of the gas distribution and velocity field
- 2021A&A...646A.127H (2021): Multiwavelength dissection of a massive heavily dust-obscured galaxy and its blue companion at z∼2
- 2021A&A...648A..32K (2021): A MeerKAT view of pre-processing in the Fornax A group
- 2021A&A...648A..41V (2021): Outflows, envelopes, and disks as evolutionary indicators in Lupus young stellar objects
- 2021A&A...652A..98G (2021): The Galaxy Activity, Torus, and Outflow Survey (GATOS). I. ALMA images of dusty molecular tori in Seyfert galaxies
- 2021A&A...654A.165V (2021): The effect of active galactic nuclei on the cold interstellar medium in distant star-forming galaxies
- 2021A&A...655A..25Z (2021): The IBISCO survey. I. Multiphase discs and winds in the Seyfert galaxy Markarian 509
- 2021A&A...656A..45M (2021): AGN feeding and feedback in Fornax A. Kinematical analysis of the multi-phase ISM
- 2021A&A...656A..60A (2021): Black hole feeding and star formation in NGC 1808
- 2021A&A...656A.133Q (2021): Stellar structures, molecular gas, and star formation across the PHANGS sample of nearby galaxies
- 2021AN....342.1160P (2021): CO kinematics unveil outflows plausibly driven by a young jet in the gigahertz peaked radio core of NGC 6328
- 2021ApJ...908...54W (2021): ALMA Measures Rapidly Depleted Molecular Gas Reservoirs in Massive Quiescent Galaxies at z ∼ 1.5
- 2021ApJ...908..163M (2021): Extremely Low Molecular Gas Content in the Vicinity of a Red Nugget Galaxy at z = 1.91
- 2021ApJ...908..231M (2021): Compact Molecular Gas Distribution in Quasar Host Galaxies
- 2023Natur.621..483G (2023): Polarized thermal emission from dust in a galaxy at redshift 2.6
- 2024A&A...682A.166F (2024): A benchmark for extreme conditions of the multiphase interstellar medium in the most luminous hot dust-obscured galaxy at z = 4.6
- 2024A&A...682A.182G (2024): JWST detection of extremely excited outflowing CO and H<SUB>2</SUB>O in VV 114 E SW: A possible rapidly accreting IMBH
- 2024A&A...684A..56K (2024): Probing the interstellar medium of the quasar BRI 0952‒0115. An analysis of [C II], [C II], CO, OH, and H<SUB>2</SUB>O
- 2024A&A...685A..80Z (2024): Unveiling [C II] clumps in a lensed star-forming galaxy at z ∼ 3.4
- 2024A&A...685A.138V (2024): The cold interstellar medium of a normal sub-L<SUP>⋆</SUP> galaxy at the end of reionization
- 2024A&A...686A..46E (2024): AGN feedback in the Local Universe: Multiphase outflow of the Seyfert galaxy NGC 5506
- 2024A&A...686A..47M (2024): A possible relation between global CO excitation and massive molecular outflows in local ULIRGs
- 2024A&A...689A.263D (2024): GATOS: missing molecular gas in the outflow of NGC 5728 revealed by JWST
- 2024A&A...691A.178B (2024): KASHz+SUPER: Evidence of cold molecular gas depletion in AGN hosts at cosmic noon
- 2024A&A...692A.215C (2024): Molecular gas budget of strongly magnified low-mass star-forming galaxies at cosmic noon
- 2024ApJ...961..108K (2024): The CO Outflow Components Ejected by a Recent Accretion Event in B335
- 2024ApJ...961..120C (2024): Brightest Cluster Galaxy Formation in the z = 4.3 Protocluster SPT 2349-56: Discovery of a Radio-loud Active Galactic Nucleus
- 2024ApJ...961..228S (2024): Ring Gap Structure around Class I Protostar WL 17
- 2024ApJ...963....1O (2024): "Beads-on-a-string" Star Formation Tied to One of the Most Powerful Active Galactic Nucleus Outbursts Observed in a Cool-core Galaxy Cluster
- 2024ApJ...963...72O (2024): Revealing Multiple Nested Molecular Outflows with Rotating Signatures in HH270mms1-A with ALMA
- 2024ApJ...964...18C (2024): Resolved Measurements of the CO-to-H<SUB>2</SUB> Conversion Factor in 37 Nearby Galaxies
- 2024ApJ...964..166K (2024): Physical Properties of Molecular Clouds in the Overlap Region of the Merging Antennae Galaxies
- 2024ApJ...966...51G (2024): The Size─Linewidth Relation and Signatures of Feedback from Quiescent to Active Star Forming Regions in the LMC
- 2024ApJ...969..122Y (2024): ALMA Reveals Spatially Resolved Properties of Molecular Gas in the Host Galaxy of FRB 20191001A at z = 0.2340
- 2024ApJ...972..147C (2024): Comparisons between Resolved Star Formation Rate and Gas Tracers in the Strongly Lensed Galaxy SDSS J0901+1814 at Cosmic Noon
- 2024ApJ...975..179C (2024): Modeling ALMA Observations of the Warped Molecular Gas Disk in the Red Nugget Relic Galaxy NGC 384
- 2024ApJ...976...88L (2024): Disk Turbulence and Star Formation Regulation in High-z Main-sequence Analog Galaxies
- 2024ApJ...977...36B (2024): GOALS-JWST: The Warm Molecular Outflows of the Merging Starburst Galaxy NGC 3256
- 2024ApJ...977..198L (2024): The SUPERCOLD-CGM Survey. II. [C I](1─0) Emission and the Physical Conditions of Cold Gas in Enormous Lyα Nebulae at z ∼ 2
- 2024ApJ...977..251H (2024): Molecular Gas Mass Measurements of an Active, Starburst Galaxy at z ≍ 2.6 Using ALMA Observations of the [C I], CO, and Dust Emission
- 2024ApJ...977L...6F (2024): The Impact of Shear on Disk Galaxy Star Formation Rates
- 2024MNRAS.527.9343L (2024): WISDOM project - XVIII. Molecular gas distributions and kinematics of three megamaser galaxies
- 2024MNRAS.534..683Z (2024): Molecular clouds as hubs in spiral galaxies: gas inflow and evolutionary sequence
- 2024PASA...41...76Z (2024): Hierarchical hub-filament structures and gas inflows on galaxy-cloud scales
- 2025A&A...696A.100G (2025): PDRs4All: XII. Far-ultraviolet-driven formation of simple hydrocarbon radicals and their relation with polycyclic aromatic hydrocarbons
- 2025A&A...696A.150S (2025): ALMAGAL: II. The ALMA evolutionary study of high-mass protocluster formation in the Galaxy: ALMA data processing and pipeline
- 2025A&A...698A.204H (2025): An ALMA spectroscopic survey of the Planck high-redshift object PLCK G073.4−57.5 confirms two protoclusters
- 2025A&A...698A.296R (2025): The impact of spiral arms on the star formation life cycle
- 2025A&A...699A.369V (2025): Dense clumps survive in the vicinity of R136 in 30 Doradus
- 2025A&A...700A.165B (2025): GAMA 526784: The progenitor of a globular cluster-rich ultra-diffuse galaxy?: II. Molecular gas, neutral gas, and environment
- 2025A&A...700A.278R (2025): CO(1─0) imaging reveals 10-kiloparsec molecular gas reservoirs around star-forming galaxies at high redshift
- 2025A&A...700A.285W (2025): Gravitational torques from lopsided young stellar component sustain high black hole accretion rates in NGC 4593
- 2025A&A...701A..48D (2025): NGC 6860, Mrk 915, and MCG -01-24-012: I. Spatial anticorrelation between cold molecular and ionized gas distributions in Seyfert galaxies
- 2025A&A...701A.113M (2025): MIRACLE: I. Unveiling the multi-phase, multi-scale physical properties of the active galaxy NGC 424 with MIRI, MUSE, and ALMA
- 2025ApJ...984L..19Y (2025): exoALMA. XIV. Gas Surface Densities in the RX J1604.3−2130 A Disk from Pressure-broadened CO Line Wings
- 2025ApJ...985..194P (2025): Traversing the Star-forming Main Sequence with Molecular Gas Stacks of z ∼ 1.6 Cluster Galaxies
- 2025ApJ...988...72S (2025): ALMA-JELLY. I. High Resolution CO(2─1) Observations of Ongoing Ram Pressure Stripping in NGC 4858 Reveal Asymmetrical Gas Tail Formation an…
- 2025ApJ...988..162D (2025): Constraining Resolved Extragalactic R<SUB>21</SUB> Variation with Well-calibrated ALMA Observations
- 2025ApJ...988..263Z (2025): Diffuse X-Ray-emitting Gas in the Central Region of Star-forming Galaxies
- 2025ApJ...989....1Z (2025): The ALMA Survey of Gas Evolution of PROtoplanetary Disks (AGE-PRO). I. Program Overview and Summary of First Results
- 2025ApJ...990..221M (2025): Spatially and Dynamically Extended Molecular Gas in Stephan's Quintet Revealed by ALMA CO(1─0) Total Power Mapping
- 2025ApJ...991...53C (2025): HerS-3: An Exceptional Einstein Cross Reveals a Massive Dark Matter Halo
- 2025ApJ...992...44D (2025): Revisiting the Gas Dynamics of Henize 2─10: Possible Drivers of the Starburst
- 2025ApJ...992..211N (2025): Revisiting the Supermassive Black Hole Mass of NGC 7052 Using High Spatial Resolution Molecular Gas Observed with ALMA
- 2025ApJ...992L...7S (2025): Characterization of Two Cool Galaxy Outflow Candidates Using Mid-infrared Emission from Polycyclic Aromatic Hydrocarbons
- 2025ApJ...993...90S (2025): ALMA High-resolution Observation for the Transitional Disk Around IRAS 04125+2902
- 2025ApJ...994...98F (2025): Measuring the Two-dimensional Thermal Structures of Protoplanetary Disks
- 2025ApJ...995..151Y (2025): Molecular Gas and Star Formation in Dwarf Galaxies Observed by the Atacama Large Millimeter/submillimeter Array
- 2025ApJ...995..219F (2025): PASSAGES: The Discovery of a Strongly Lensed Protocluster Core Candidate at Cosmic Noon
- 2025ApJ...995L..63L (2025): ALMA Reveals Diverse Dust-to-gas Mass Ratios and Quenching Modes in Old Quiescent Galaxies
- 2025MNRAS.536.3757A (2025): The kinematics of massive high-redshift dusty star-forming galaxies
- 2026A&A...705A..33E (2026): The Galaxy Activity, Torus, and Outflow Survey (GATOS): X. Molecular gas clumpiness under the influence of AGN
- 2026A&A...705A..39P (2026): High-z [OI] emission lines: COLDSIM simulations and ALMA observations
- 2026A&A...705A.163H (2026): CHILES: X. Molecular and atomic gas at intermediate redshift
- 2026ApJ..1001..131C (2026): MAGAZ3NE: Far-IR and Radio Insights into the Nature and Properties of Ultramassive Galaxies at z ≳ 3
- 2026ApJ..1003...52D (2026): Molecular Gas Excitation in z ∼ 0.7 Gas-rich Poststarburst Galaxies from SQuIGG<inline-formula> <mml:math><mml:mover><mml:mrow><mml:mi>L</m…
- 2026ApJ..1003...68Y (2026): A Multiscale Molecular and Atomic Gas View on the H II Region N113 in the Large Magellanic Cloud: Evidence for High-mass Star Formation Tri…
- 2026ApJ..1003..231W (2026): Multiscale Gas Structure and Dynamics in an Extragalactic Central Molecular Zone
- 2026ApJ..1004..126K (2026): An Active Galactic Nucleus in the Antennae Galaxies?
