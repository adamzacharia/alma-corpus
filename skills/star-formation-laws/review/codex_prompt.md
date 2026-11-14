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

=== SKILL.md (star-formation-laws) ===
---
name: alma-star-formation-laws
description: "Relate ALMA gas measurements to star formation the way published ALMA papers do: build Sigma_SFR and Sigma_gas (molecular, dense or total) on matched apertures or pixels, fit Kennicutt-Schmidt slopes, and compute depletion times, SFE, dense-gas SFE and efficiency per free-fall time. Use when placing galaxies, regions, clumps or lensed sources on the KS plane, quoting t_dep = M_gas/SFR, comparing to Kennicutt 1998 or Bigiel 2008, fitting a resolved star formation law, or checking someone else's depletion time or KS slope. Built from 160 ALMA papers (2012-2026)."
---

# Star formation laws and depletion times

Measures how fast gas turns into stars: Sigma_SFR versus Sigma_gas (the Kennicutt-Schmidt, KS, relation),
its slope N, and the ratios t_dep = M_gas/SFR = 1/SFE and eps_ff = t_ff/t_dep. Every quantity is a ratio of
two calibrated maps or totals, so the mistakes that matter most are convention mismatches, not noise:
(1) SFR and gas built with different IMFs, alpha_CO, helium or area conventions (each a factor of 1.36 to about 5),
and (2) a slope that reflects the S/N cut, the fitting method or the alpha_CO prescription rather than the
physics (a constant vs variable alpha_CO moved one resolved slope from 0.90 to 1.23, 2024ApJ...976...88L).

> Always report: SFR tracer and calibration (with IMF), alpha_CO (and r_J1) with helium convention, the area
> definition (pi R_e^2 with half the SFR, aperture, pixel, beam), resolution in pc, inclination treatment, S/N
> cuts, and the regression method. A KS slope or t_dep without these cannot be compared to anything.

Gas masses themselves (L' to M_H2, choosing alpha_CO, r_J1, [CI], dust-based gas) are covered by the sibling
skill `alma-gas-mass-co-conversion` (`../gas-mass-co-conversion/SKILL.md`). Use it for the gas side and do not
re-derive alpha_CO here.

Counts below are from the evidence pack (my count of pack lines unless stated as aggregates). The regex that
built the pack also caught papers that only mention an "SFE" in passing (protoplanetary-disk hydro, core mass
functions, number counts, YMC toy models, e.g. 2015ApJ...809...93D, 2020A&A...635A...2S, 2015A&A...584A..78C);
those are excluded from counts.

## When to use

- Integrated t_dep and SFE for detected galaxies, cluster members, quasar hosts, protocluster galaxies
  (2025A&A...698A.204H, 2019PASJ...71...40T, 2019ApJ...887...74F, 2021ApJ...908...54W).
- Resolved KS relation on pixels, beam apertures, rings or spaxels in nearby galaxies (2019ApJ...887...88E,
  2024ApJ...976...88L, 2025ApJ...995..151Y, 2020ApJ...903..145L, 2021A&A...656A..60A).
- Global KS placement of compact high-z sources from sizes plus SFR and gas totals (2017A&A...602L...9M,
  2020A&A...641A.155V, 2014A&A...562A..67G).
- Resolved laws in lensed sources, after a lens model (2018ApJ...867..140L, 2024ApJ...972..147C).
- Dense-gas star formation laws with HCN or HCO+ (2018ApJ...863..129S, 2015ApJ...813..118M,
  2015ApJ...815..103B, 2019AJ....157..131B).
- Efficiency per free-fall time or theory comparisons (2018ApJ...861L..18U, 2018ApJ...855L..25K,
  2019MNRAS.487.4305S, 2024ApJ...976...88L).
- Environmental tests: spiral arms, bars, ram pressure, minor mergers (2021A&A...656A.133Q,
  2025A&A...698A.296R, 2020MNRAS.495.3840M, 2018MNRAS.476..122V).

## When not to use

- Converting CO, [CI] or dust to gas mass: use `alma-gas-mass-co-conversion`.
- Deriving L_IR or SFR from a full far-IR SED (CIGALE, MAGPHYS, greybody fits): use an SED-fitting skill and
  bring the SFR here. This skill only covers how the SFR enters the law.
- Cloud-scale SFE defined as M_star/(M_star+M_gas) for single clumps or YSO clusters (2019PASJ...71...44H,
  2015MNRAS.449..715W). That is a mass ratio, not a rate; do not put it on the KS plane.
- GMC catalogues and virial parameters: use a GMC-decomposition skill. Toomre Q: use a stability skill.

## Steps

1. **Fix conventions before touching data.** Goal: one IMF, one alpha_CO convention, one cosmology for both
   axes. Chabrier is the most common IMF (24 papers), then Salpeter (13), Kroupa (4). Papers convert
   literature SFRs: Salpeter to Chabrier by /1.8 (2017A&A...604A.117C) or /1.6 (2024ApJ...976...70L),
   Salpeter to Kroupa by /1.5 (2019A&A...621A..27F); stellar masses by /1.7 (2018A&A...616A.110E). Pick one
   factor and state it. When comparing to literature samples, rescale their gas masses to your alpha_CO, as
   2025A&A...698A.204H did (to 4.36).

2. **Build the SFR (or Sigma_SFR) map or total.** Method by tracer family (pack lines):
   - Dust continuum / IR luminosity with Kennicutt 1998 (19 papers, e.g. 2013ApJ...767..132H,
     2014A&A...562A..67G, 2019ApJ...876..130H, 2019ApJ...881...63N) or Kennicutt and Evans 2012 (3, e.g.
     2020A&A...635A.119C, 2025A&A...698A.204H). Coefficients seen: 1.72e-10 L_IR (Salpeter,
     2019A&A...621A..27F), 1.40e-10 L_IR (Chabrier, 2025A&A...698A.204H).
   - Resolved IR maps from a single ALMA band: papers scale the SED-derived total SFR by each beam's share of
     the continuum flux (2019ApJ...876..130H), which assumes one dust temperature everywhere.
   - H-alpha or Pa-alpha (10 papers): 5.53e-42 L_Halpha (2024ApJ...976...88L), 4.5e-42 L_Halpha
     (2020ApJS..247...61F), Pa-alpha with Calzetti extinction (2021A&A...656A..60A), Balmer-decrement
     correction (2020ApJ...889....9M, 2019MNRAS.485.1595P).
   - UV plus IR hybrids: Sigma_SFR = 3.2e-3 I24 + 8.1e-2 I_FUV (2012ApJ...760L..25E); NUV+12um
     (2025ApJ...995..151Y); FUV/NUV/12um/24um coefficients (2018ApJ...861L..18U).
   - Free-free and recombination lines: 33 GHz thermal fraction 79% (2015ApJ...813..118M), H30alpha
     (2017MNRAS.472.1239B), 110 GHz (2018ApJ...863..129S), 8 um PAH (2019ApJ...887...88E), 160 um
     (2019ApJ...876..112R).
   Software: maps are regridded with MOPEX (2012ApJ...760L..25E) or astropy/reproject; totals come from
   CIGALE (5 papers in aggregates) or MAGPHYS (3).

3. **Build the gas map or total.** Goal: Sigma_mol (or Sigma_dense, Sigma_HI+H2) on the same footprint.
   Method: moment-0 with alpha_CO and r_J1 (see the gas-mass skill), times cos i, including or excluding
   helium consistently. Galactic alpha_CO near 4.3-4.6 dominates (about 16 papers, e.g. 2020ApJ...903..145L,
   2025ApJ...995..151Y, 2019MNRAS.485.1595P); ULIRG-like 0.8-1.1 in at least 8 (2014ApJ...790..160S,
   2017A&A...604A.117C, 2020A&A...641A.151S). Dense gas: alpha_HCN = 10 (2015ApJ...815..103B,
   2018ApJ...858...90G, 2018ApJ...863..129S, 2019AJ....157..131B), alpha_HCO+ about 10 (2015ApJ...813..118M).
   Correct for flux the interferometer missed, or say you did not: 45% missing-flux correction
   (2021A&A...656A..60A); about half the flux recovered (2017ApJ...850...54C).

4. **Match resolution and sampling.** Goal: both maps describe the same gas. Convolve to the coarser beam,
   regrid to about one beam per sample, then measure.
   - Pixels: 6'' maps on 3'' pixels (2012ApJ...760L..25E); 2.4'' (43 pc) pixels set by the 8 um map
     (2019ApJ...887...88E).
   - Apertures: beam-sized circles on two grids offset by 0.5 beam FWHM (2024ApJ...976...88L); 0.75''
     (34 pc) radius (2021A&A...656A..60A); 1 kpc hexagons at 1.5 kpc resolution (2021A&A...656A.133Q);
     200 pc apertures along a spiral (2025A&A...700A.285W).
   - Global compact sources: Sigma = (SFR/2)/(pi R_e^2), i.e. half the SFR inside the half-light radius
     (2019ApJ...876..130H, 2014A&A...562A..67G, 2020A&A...641A.155V, 2017A&A...602L...9M per its card).
   - Inclination: cos i correction (2025ApJ...995..151Y); fixed 70 deg (2019ApJ...887...88E); 57 deg
     (2021A&A...656A..60A); some apply none (2019ApJ...882....5W).

5. **Apply detection cuts and keep limits.** CO S/N > 2 per spaxel (2017ApJ...851...18L,
   2019ApJ...884L..33L); 3 sigma SFR threshold (2012ApJ...760L..25E); 2 sigma gas cut (2024ApJ...972..147C);
   state the completeness floor, e.g. Sigma_mol about 4 Msun/pc^2 at 3 sigma over 10 km/s
   (2019ApJ...887...88E). Remove AGN-dominated pixels before fitting (19 AGN points removed,
   2019ApJ...887...88E; an AGN bulge excluded, 2017ApJ...851...18L).

6. **Fit the relation.** log Sigma_SFR = N log Sigma_gas + C. Methods seen (aggregates plus pack lines):
   Bayesian regression with errors in both axes and censored points, Kelly 2007 via linmix / LINMIX_ERR
   (2018ApJ...863..193V, 2020A&A...641A.155V); orthogonal distance regression, scipy ODR
   (2024ApJ...976...88L, 2019ApJ...887...88E); ordinary least squares per galaxy (2025ApJ...995..151Y);
   linear fits to binned means (used for R21 trends, 2025ApJ...988..162D); Gaussian-mixture decomposition chosen by BIC with
   scikit-learn before the fit (2019ApJ...887...88E). One paper normalises at Sigma_H2 = 100 Msun/pc^2,
   Sigma_SFR = A (Sigma_H2/100)^N (2018ApJ...863..193V). Recommendation: use a method that handles errors on
   both axes and upper limits (linmix), and quote OLS or ODR alongside if comparing to older work.

7. **Derive t_dep, SFE and eps_ff.** t_dep = M_mol/SFR = 1/SFE (2019MNRAS.485.1595P); per pixel
   t_dep = Sigma_mol/Sigma_SFR, summarise with the median (2024ApJ...976...88L, 2025A&A...700A.285W).
   eps_ff = t_ff/t_dep needs a gas scale height or density model (general practice; 2018ApJ...861L..18U
   compares three scale-height prescriptions per its card). Theory comparisons in the pack use
   Krumholz-McKee turbulence-regulated grids (2018ApJ...863..129S), KDM and SFK models
   (2019MNRAS.487.4305S), Krumholz+18 and feedback-regulated models (2024ApJ...976...88L).

8. **Validate** (see Verification checks) and report the conventions box above.

## Parameter defaults and ranges

| parameter | common choice | range seen | papers (count) | examples |
|---|---|---|---|---|
| IMF | Chabrier | Chabrier, Salpeter, Kroupa | 24 / 13 / 4 (pack lines) | 2018MNRAS.477.4380S, 2019ApJ...884L..33L, 2019Natur.569..519K |
| IR SFR calibration | Kennicutt 1998 | K98, Kennicutt and Evans 2012 | 19 / 3 (pack lines) | 2019ApJ...881...63N, 2020A&A...635A.119C |
| alpha_CO (normal disks) | 4.35-4.36 incl. He | 4.3-4.87 | about 16 (pack lines) | 2020ApJ...903..145L, 2017MNRAS.469.4683C |
| alpha_CO (starburst, nucleus) | 0.8 | 0.8-1.1 | at least 8 (pack lines) | 2017ApJ...846..108C, 2014ApJ...790..160S |
| alpha_HCN | 10 | 10 | 4 (pack lines) | 2018ApJ...858...90G, 2019AJ....157..131B |
| Area for global Sigma | (SFR/2)/(pi R_e^2) | R from FWHM/2 or HWHM | 4 in pack lines (+1 card) | 2019ApJ...876..130H, 2020A&A...641A.155V |
| Resolution of resolved KS | beam-matched | 34 pc to 1.5 kpc | see Step 4 | 2021A&A...656A..60A, 2021A&A...656A.133Q |
| CO S/N cut per sample | > 2 | 1 to 3 sigma | 4 (pack lines) | 2017ApJ...851...18L, 2025ApJ...995..151Y |
| SFR uncertainty floor | factor 2 | 20% to factor 2 | 3 (pack lines) | 2018ApJ...863..193V, 2019Natur.569..519K, 2015MNRAS.453L..83M |
| Dust T for single-band IR SFR | 40-50 K, beta 1.5-1.6 | 25-120 K | many (see parameters.md) | 2013ApJ...770...13W, 2017A&A...599A.134S |

Results to sanity-check against (not targets): resolved molecular KS slopes 0.63 overall and 0.28 in a CND
(2019ApJ...887...88E), 0.64 to 1.18 (2018ApJ...863..193V), 0.62 to 1.08 with mean 0.81 in dwarfs
(2025ApJ...995..151Y), 0.90 or 1.23 depending on alpha_CO (2024ApJ...976...88L). Depletion times: median
0.8 Gyr in z~0.1 analogues (2024ApJ...976...88L), 1.5 Gyr in Cen A (2019ApJ...887...88E), 3.9 Gyr along a
Seyfert spiral (2025A&A...700A.285W), 0.7 Gyr in protocluster galaxies (2025A&A...698A.204H), 0.4 Gyr in a
LLAGN centre (2020A&A...641A.151S), 12-28 Myr in a hyperluminous quasar (2019ApJ...887...74F). SFE_H2 of
0.9-4.1 per Gyr in dwarfs (2025ApJ...995..151Y). Extreme Sigma_SFR: about 4200 (2013ApJ...767..132H) and
2e3 Msun/yr/kpc^2 (2017ApJ...842L..16L) against an Eddington-limited lower limit of about 650
(2019ApJ...876..130H). eps_ff = 0.11 in an IRDC (2018ApJ...855L..25K). Longer table in
`references/parameters.md`.

## Software

From the pack aggregates of software named in matched steps (160 papers; counts are small because most
papers do the arithmetic in their own scripts):

| software | count (aggregates) | used for | examples |
|---|---|---|---|
| CIGALE | 5 | SED SFR and M_star feeding the law | 2025A&A...698A.204H, 2024A&A...692A.215C, 2026ApJ..1001..131C |
| CASA | 5 | imaging, moment maps, apertures | 2015ApJ...813..118M, 2019MNRAS.485.1595P, 2024ApJ...976...88L |
| MAGPHYS | 3 | SED SFR, dust temperature | 2020A&A...635A.119C, 2019ApJ...876..130H |
| emcee | 2 | MCMC SED or limit likelihoods | 2019A&A...621A..27F |
| scikit-learn | 2 | GMM split of KS points | 2019ApJ...887...88E |
| MOPEX | 2 | Spitzer mosaics and regridding | 2012ApJ...760L..25E, 2019PASJ...71...40T |
| astropy / reproject | 2 / 1 | aperture photometry, regridding | 2024ApJ...976...88L |
| linmix / LINMIX_ERR | 1 / 1 | Kelly 2007 regression with limits | 2018ApJ...863..193V, 2020A&A...641A.155V |
| scipy ODR | 1 | orthogonal regression | 2024ApJ...976...88L |
| Pipe3D, MPDAF | 1 each | IFU H-alpha maps | 2019MNRAS.485.1595P (MPDAF) |

## Pitfalls

- **Area convention factor 2.** (SFR/2)/(pi R_e^2) and SFR/(pi R^2) differ by 2; also R as FWHM/2 vs HWHM vs
  diameter (one paper writes (1/2 SFR)/(1/4 pi d^2), 2018ApJ...864...38L). Gas and SFR must use the same
  area: t_dep from totals does not care, but KS positions and Sigma-based t_dep do.
- **IMF and calibration drift.** Literature SFRs mix Salpeter and Chabrier; conversion factors differ by
  paper (1.5 to 1.8, see Step 1). Convert before plotting.
- **alpha_CO drives the slope.** Constant vs variable alpha_CO changes resolved slopes (0.90 vs 1.23,
  2024ApJ...976...88L) and offsets SFE by up to 0.14 dex (2020ApJ...903..145L). Authors call alpha_CO the
  dominant systematic (2025ApJ...995..151Y, 2021ApJ...908...54W factor >= 2, 2018ApJ...860..103S about 50%).
  A bar may need alpha_CO a few times lower (2020MNRAS.495.3840M).
- **S/N cuts bias the slope.** Including 1 sigma CO points moved a mean slope from 0.87 to 0.73
  (2025ApJ...995..151Y). Cuts on one axis truncate the other; use censored regression rather than dropping
  limits. Two of six dwarf slopes rested on two points (2025ApJ...995..151Y).
- **Single dust temperature.** Single-band ALMA SFRs assume one T_dust; uncertain by 2-3 dex without the FIR
  peak (2015ApJ...813...45L); template choice spans nearly a decade (2019MNRAS.486..560S); uncertainties
  often exclude it (2013ApJ...770...13W). Resolved maps inherit it (2019ApJ...876..130H, 2024ApJ...976...70L).
- **Non-stellar continuum.** Synchrotron can contaminate 110 GHz SFRs by about 25% (2018ApJ...863..129S);
  radio-galaxy SFRs fell sevenfold after removing synchrotron (2019A&A...621A..27F); AGN light biases gas and
  SFR (2026ApJ..1001..131C, 2021A&A...656A.133Q); free-free cannot always be excluded (2020A&A...641A.151S).
- **Missing flux and resolved-out gas** lower Sigma_gas and shorten t_dep (2021A&A...656A..60A,
  2017ApJ...850...54C, 2020A&A...641A.151S).
- **Registration and PSFs.** 24 um Airy rings add about 0.1 dex (2012ApJ...760L..25E); manually aligned HST
  images can hide offsets (2018ApJ...863..193V); ALMA-HST astrometry 0.1-0.2'' (2019ApJ...881..124M).
- **Scale dependence.** Arm/inter-arm contrasts may depend on resolution (2021A&A...656A.133Q); large beams
  blend regions (2025ApJ...990..221M); beam smearing inflates sigma_v up to 20% (2019ApJ...882....5W).
- **Lensing.** Differential magnification can bias ratios; t_dep may be underestimated near the end of a
  burst (2016A&A...586L...7B). Divide all extensive quantities by the same mu (2013ApJ...767..132H).
- **Limits dominate.** Mostly upper limits preclude a robust t_dep (2021ApJ...908...54W); Sigma_SFR below
  1e-3 Msun/yr/kpc^2 treated as limits (2020MNRAS.495.3840M).
- **Heterogeneous comparison samples** (2024ApJ...976...88L) and small samples (2025ApJ...988..162D,
  2019ApJ...884L..33L) can drive slopes.
- **What cards flag as not stated** (aggregates): CASA version (8), flux-scale uncertainty (7+4), line-free
  channels and continuum subtraction (5+5+3), primary-beam correction (3+2). Specific to this technique:
  the SFR formula (2015ApJ...813..118M), the Sigma_SFR recipe (2018ApJ...863..129S), and the regression
  method (2025ApJ...988..162D) are often missing. State them.

## Verification checks

What papers did (pack):
- Swap the SFR tracer: 8.4 GHz vs IR (2018ApJ...863..129S); H-alpha vs SED SFRs, consistent above about 13
  Msun/yr (2020ApJS..247...61F); two independent L_IR estimates (2018ApJ...862...64S); other SED codes
  within about 0.1 dex (2017MNRAS.469.4683C); alternative templates (2015MNRAS.453L..83M).
- Swap alpha_CO: metallicity-dependent or radially varying (2020ApJ...903..145L, 2025ApJ...995..151Y,
  2024ApJ...976...88L); dust-based vs CO-based gas within 0.2 dex (2026ApJ..1001..131C, 2024A&A...692A.215C).
- Vary resolution and aperture: trends robust from 100 to 400 pc apertures (2025A&A...700A.285W).
- Drop outliers or subsamples: Kendall tau 0.67 to 0.66 (2020ApJ...903..145L); slopes change < 15% fitting
  only high-z (2020A&A...641A.155V).
- Compare to reference relations: Kennicutt 1998 and Bigiel 2008 (2018ApJ...863..193V,
  2021A&A...656A..60A); the Boquien et al. 2011 relation (2019ApJ...887...88E).
- Line choice: KS index 0.80 vs 0.78 from CO(1-0) vs CO(2-1) with fixed R21 (2025ApJ...988..162D).

What a careful referee adds:
- Recompute t_dep from the quoted M_gas and SFR, and check both share IMF, helium and magnification.
- Re-fit with errors on both axes and limits included; report how N moves vs OLS.
- Check the slope after shifting the S/N cut by 1 sigma and after convolving to a coarser beam.
- Check that the area used for Sigma_gas and Sigma_SFR is identical, and whether inclination was applied.
- For dense-gas laws, confirm the HCN line was not cut by the bandpass (2015ApJ...813..118M) and that
  alpha_HCN was stated.

## Source cards

Full list: `references/sources.md` (generated). Most informative for this technique:

- 2024ApJ...976...88L: resolved KS with ODR, constant vs variable alpha_CO, theory comparisons
- 2019ApJ...887...88E: pixel KS at 43 pc, GMM plus ODR, AGN masking, completeness floor
- 2025ApJ...995..151Y: per-galaxy KS in dwarfs, S/N-cut and alpha_CO tests
- 2018ApJ...863..193V: linmix KS fit, factor-2 SFR floor, UV-scaled SFR
- 2020A&A...641A.155V: censored Bayesian regression, Sigma_SFR = SFR/(2 pi R^2)
- 2021A&A...656A..60A: beam apertures, missing-flux correction, Pa-alpha SFR
- 2020ApJ...903..145L: spaxel SFE vs gas fraction, alpha_CO robustness
- 2018ApJ...863..129S: dense-gas law, SFR tracer swap, turbulence model
- 2025A&A...700A.285W: depletion time along a spiral, aperture robustness
- 2012ApJ...760L..25E: FUV+24 um Sigma_SFR, PSF contamination check
- 2019ApJ...876..130H: resolved Sigma_SFR from 870 um, Eddington limit
- 2018ApJ...861L..18U: eps_ff in nearby galaxies
- 2017A&A...602L...9M: KS law of submillimetre galaxies
- 2019ApJ...882....5W: KS law and scale height in (U)LIRGs
- 2019MNRAS.487.4305S: resolved SF law tests at z = 4.3
- 2025ApJ...988..162D: R21 effect on KS index and t_dep
- 2021A&A...656A.133Q: environment masks across PHANGS
- 2025A&A...698A.204H: depletion times in protoclusters, alpha_CO rescaling of literature
- 2019A&A...621A..27F: synchrotron removal for radio-galaxy SFRs

=== references/parameters.md ===
# Star formation laws: longer parameter table

All values are from the evidence pack (`skills/packs/star-formation-laws.md`); a few marked "card" come from
the paper's methods card. They are what papers adopted, not recommendations. Gas-side conversion factors
(alpha_CO, r_J1, X_CI, gas-to-dust) are treated in `../gas-mass-co-conversion/` and listed here only where
they set a star formation law result.

## SFR calibrations

| tracer | calibration as quoted | IMF | paper |
|---|---|---|---|
| L_IR (8-1000 um) | SFR = 1.72e-10 L_IR, then /1.5 to Kroupa | Salpeter -> Kroupa | 2019A&A...621A..27F |
| L_IR | SFR = 1.40e-10 L_IR | Chabrier | 2025A&A...698A.204H |
| L_IR | Kennicutt 1998, rescaled to Chabrier | Chabrier | 2019ApJ...876..130H, 2019ApJ...881...63N, 2025ApJ...994....4A |
| L_IR | Kennicutt 1998 | Salpeter | 2017A&A...599A.134S, 2018ApJ...856...72O, 2019ApJ...876...99S |
| L_IR | Kennicutt and Evans 2012 | not stated in pack line | 2017A&A...605A..42C, 2020A&A...635A.119C |
| TIR | Murphy et al. 2011 TIR-to-SFR | not stated in pack line | 2015ApJ...815..103B |
| H-alpha | SFR = 5.53e-42 L_Halpha (Hao+11) | not stated in pack line | 2024ApJ...976...88L |
| H-alpha | SFR = 4.5e-42 L_Halpha (Kennicutt 1998) | not stated in pack line | 2020ApJS..247...61F |
| H-alpha | Murphy et al. 2011, 20% uncertainty | Kroupa | 2019Natur.569..519K |
| Pa-alpha | with Calzetti extinction | not stated | 2021A&A...656A..60A |
| FUV + 24 um | Sigma_SFR = 3.2e-3 I24 + 8.1e-2 I_FUV; A_FUV = 8.24 E(B-V) | not stated | 2012ApJ...760L..25E |
| FUV / NUV / 12 um / 24 um | K = 1.04e-1, 1.04e-1, 3.77e-3, 2.97e-3 | not stated | 2018ApJ...861L..18U |
| UV (HST) | Salim07, SFR uncertainty factor 2; region SFR = share of UV counts x global SFR | Chabrier | 2018ApJ...863..193V |
| 8 um PAH | log Sigma_SFR = 0.844 log Sigma_L8 - 30.923 | not stated | 2019ApJ...887...88E |
| 33 GHz free-free | mean thermal fraction 79% | not stated | 2015ApJ...813..118M |
| 110 GHz | possible 25% synchrotron contamination | not stated | 2018ApJ...863..129S |
| 160 um | linear mapping, no AGN contribution | universal IMF | 2019ApJ...876..112R |
| WISE 22 um | same conversion as Spitzer 24 um | not stated | 2017MNRAS.472.1239B |
| [CII] | 0.5 dex scatter on SFR_CII | not stated | 2019ApJ...882...10N |

IMF conversions used: Salpeter to Chabrier SFR /1.8 (2017A&A...604A.117C), /1.6 (2024ApJ...976...70L);
Salpeter to Kroupa /1.5 (2019A&A...621A..27F); stellar mass Chabrier = Salpeter/1.7 (2018A&A...616A.110E).

## Dust temperature and emissivity for single-band IR SFRs

| T_dust, beta | paper |
|---|---|
| 47 K, 1.6 | 2013ApJ...770...13W |
| 47 K | 2018ApJ...854...97D, 2019ApJ...881...63N |
| 40 K (all galaxies) | 2017A&A...599A.134S |
| 41 K, 1.5, bolometric factor 1.91 | 2018ApJ...867..140L |
| average of (47 K, 1.6) and (41 K, 1.95) | 2017MNRAS.465.4390B |
| 45 K, 1.5 | 2019ApJ...881..124M |
| 35 K, 1.5 | 2017ApJ...851..145M |
| 30 K, 1.5 | 2018MNRAS.478.1170C |
| 30-50 K, 1.2-2.0 | 2019ApJ...882...10N |
| 25-45 K | 2017A&A...605A..42C |
| 25 K (20-30 K for errors) | 2016ApJ...833...12R |
| 50 K, 2.0 | 2017A&A...604A.117C |
| 50 K, 2.5 (to set upper limits) | 2019A&A...621A..27F |
| 30, 50, 90, 120 K, 1.5 (2 at 50 K) | 2015ApJ...813...45L |
| free T, beta = 1.8 | 2025A&A...698A.204H |

## Gas side, as it enters the law

| quantity | value | paper |
|---|---|---|
| alpha_CO (Galactic, incl. He) | 4.35 | 2020ApJ...903..145L, 2025ApJ...995..151Y, 2025ApJ...988..162D |
| alpha_CO | 4.36, r31 = 0.27, inclination 57 deg, 45% missing flux | 2021A&A...656A..60A |
| alpha_CO | 4.36 x f_metal (1.1 at log M* = 11, 1.4 at 10.5) | 2019PASJ...71...40T |
| alpha_CO | 4.4 incl. He, R21 = 0.7 | 2020MNRAS.499..193K |
| alpha_CO | 4.6 | 2019MNRAS.485.1595P |
| alpha_CO | 4.6 disks, 0.8 mergers | 2020MNRAS.497.2771M |
| alpha_CO | variable, Bolatto+13 eq. 31, iterated to < 0.1% change | 2024ApJ...976...88L |
| alpha_CO | metallicity-dependent, Genzel 2015 | 2024A&A...692A.215C |
| alpha_CO | 0.8 | 2017A&A...604A.117C, 2017ApJ...846..108C, 2019MNRAS.489..427I |
| alpha_CO | 0.86, 0.5 dex error | 2014ApJ...790..160S |
| alpha_CO | 1.1, CO(2-1)/CO(1-0) = 3 | 2020A&A...641A.151S |
| alpha_CO MS vs SB | 4.87 with R51 = 0.23 vs 1 with R51 = 0.6 | 2017MNRAS.469.4683C |
| X_CO | 2e20 with He, Sigma_H2 = 4.2 I_1-0, R21 = 0.7 | 2019A&A...623A..66B |
| alpha_HCN | 10 | 2015ApJ...815..103B, 2018ApJ...858...90G, 2018ApJ...863..129S, 2019AJ....157..131B |
| alpha_HCO+ | about 10 | 2015ApJ...813..118M |
| gas from dust | log delta_GDR = 10.54 - 0.99 (12+log O/H); starbursts delta_GDR about 30 | 2020A&A...641A.155V |
| gas from 850 um | alpha_nu = 6.7e19 erg/s/Hz/Msun at 25 K, T correction 0.77-1.06 | 2026ApJ..1001..131C |

## Sampling, cuts and fits

| setting | value | paper |
|---|---|---|
| pixel grid | 6'' resolution, 3'' pixels; SFR 3 sigma = 0.018 Msun/yr | 2012ApJ...760L..25E |
| pixel grid | 2.4'' = 43 pc; Sigma_mol complete to about 4 Msun/pc^2 | 2019ApJ...887...88E |
| aperture grid | beam-sized, second grid offset by 0.5 FWHM | 2024ApJ...976...88L |
| aperture | 0.75'' = 34 pc radius | 2021A&A...656A..60A |
| hexagons | 1 kpc spacing, 1.5 kpc resolution | 2021A&A...656A.133Q |
| spiral apertures | 200 pc wide on a 100 pc grid; robust 100-400 pc | 2025A&A...700A.285W |
| aperture photometry | 3'' apertures (11 regions) | 2018ApJ...863..129S |
| spaxel cut | CO S/N > 2; Sigma_* > 1e7 Msun/kpc^2 | 2019ApJ...884L..33L |
| spaxel cut | CO S/N > 2; AGN bulge excluded | 2017ApJ...851...18L |
| resampling | 10,000 resamplings; 2 sigma gas cut | 2024ApJ...972..147C |
| regression | Kelly 2007 linmix, log space | 2018ApJ...863..193V |
| regression | LINMIX_ERR with censored points; L_IR >= 10^8.5 Lsun | 2020A&A...641A.155V |
| regression | ODR | 2024ApJ...976...88L, 2019ApJ...887...88E |
| regression | least squares per galaxy | 2025ApJ...995..151Y |
| regression | least squares on binned data, also slope fixed to 1 for SFE (card) | 2017A&A...602L...9M |
| regression | double power law with free break, 10,000 bootstraps (card) | 2019ApJ...882....5W |
| correlation | Kendall tau | 2020ApJ...903..145L |

## Efficiency per free-fall time and life-cycle parameters

| quantity | value | paper |
|---|---|---|
| eps_ff (IRDC, turbulent core model) | 0.11; eps_core = 0.5 | 2018ApJ...855L..25K |
| eps_ff in models | KDM 0.015; SFK 0.0045, b = 0.4 | 2019MNRAS.487.4305S |
| dense-gas model | n_dense = 2.8e5 cm^-3, eps_SF = 0.28% | 2018ApJ...863..129S |
| feedback model | P*/m* = 3000 km/s | 2024ApJ...976...88L |
| life-cycle fit | t_gas = 35 Myr, t_over = 5 Myr, t_star = 10 Myr, lambda = 400 pc | 2017ApJ...835..278S |
| (U)LIRG disk model | alpha+beta about 0.3, Sigma_gas/Sigma_total about 0.5 | 2019ApJ...882....5W |
| star formation timescale | 5 Myr | 2017ApJ...850...54C |

=== EVIDENCE PACK (star-formation-laws) ===
# Evidence pack: Star formation laws and depletion times (`star-formation-laws`)

Scope: relating gas surface density to SFR, depletion times

Built from 160 non-held-out ALMA papers whose methods cards passed mechanical evidence verification (every quote below is verbatim from the paper). Years 2012-2026.
Matcher (regex over analysis steps): `kennicutt|schmidt|depletion time|star formation efficiency|\bsfe\b|t_?dep|resolved star formation law|sigma_?sfr|σ_?sfr`
Tagging is by regex, so a few papers may be off-topic: ignore those.

## Aggregates over all papers

### Science fields
- high_z_galaxies: 103
- nearby_galaxies: 59
- star_formation: 39
- agn_and_quasars: 35
- milky_way_ism: 20
- galaxy_clusters_and_sz: 10
- cosmology: 4
- astrochemistry: 2
- protoplanetary_disks: 1
- other: 1

### Software named in the matched steps
- cigale: 5
- casa: 5
- magphys: 3
- astropy: 2
- mopex: 2
- scikit-learn: 2
- emcee: 2
- cmcirsed: 1
- hyperz: 1
- ramses: 1
- radmc-3d: 1
- linmix: 1
- networkx: 1
- fargo: 1
- mpdaf: 1
- sextractor: 1
- linmix_err: 1
- scipy odr: 1
- cprops: 1
- pdr toolbox: 1
- starburst99: 1
- mosfire drp: 1
- reproject: 1
- despotic: 1
- halotools: 1
- pipe3d: 1
- bagpipes: 1
- galfit: 1
- arepo: 1
- sc sam: 1
- casa imfit: 1
- sed3fit: 1
- eso sinfoni pipeline: 1
- iraf: 1

### Fitting methods (most common phrasings)
- chi2 best fit; parameters are likelihood-weighted means and standard deviations: 1
- chi2 minimisation; A_V values from fits within Delta chi2<1: 1
- Least squares, no priors: 1
- Bayesian linear regression (Kelly 2007) via linmix: 1
- Gaussian line fits: 1
- relations fitted to compiled r31, r41 data; r51 from Narayanan 2014: 1
- Kelly (2007) Bayesian approach: 1
- ODR; priors not applicable: 1
- Gaussian mixture model (2 components, full covariance chosen by BIC) after removing 19 AGN points; orthogonal distance …: 1
- Linear regression y = m x + q to binned values; no sampler or priors stated: 1
- Modified blackbody fit; Monte Carlo simulations of synthetic photometry for statistical error: 1
- chi2 minimisation over A, n, sigma: 1
- bisector power-law fit: 1
- Monte Carlo for TIR uncertainty: 1
- power law: 1
- emcee MCMC; upper-limit likelihood following Shangguan 2018: 1
- Median of Monte Carlo distribution as value; mean of 16th/84th percentile offsets as 1 sigma: 1
- SED chi2 fit; reduced chi2 1.3: 1
- chi2_red=1.1: 1
- Linear fit between literature median and stacked limit: 1
- Monte Carlo error propagation: 1
- power-law fit gives slope -0.53±0.12: 1
- Greybody fit to Herschel+ALMA for ULASJ1234: Td=31+-4 K, beta=2.5+-0.3 (not adopted): 1
- Template fitting chi2: 1
- chi2 over template/amplitude grid, flat priors: 1
- template fitting; details not stated: 1
- emcee MCMC for DL07 models: 1
- MCMC: 1
- Least squares, errors derived from Sigma_SFR uncertainties: 1
- template library fits (Chary & Elbaz, Draine, Rieke): 1

### Validation checks used
- SFR range cross-checked with modified blackbody + Kennicutt98 relation (cited): 1
- Toomre upper limits marginally consistent with Jeans lower limits: 1
- Tested alternate SFR tracer (8.4 GHz) and conversion factors: 1
- Density threshold model rejected via correlation coefficient -0.55: 1
- Compared with Kneissl+19 SFRs and CIGALE with cmcirsed dust model: 1
- Reproduced Simpson et al. 2014 hyperz results: 1
- Repeated with metallicity-dependent alpha_CO (Sun+20; Narayanan+12) and alternative SFR spaxel selections: 1
- Excluded lowest-SFE point; tau changes 0.67 to 0.66: 1
- Repeated with varying alpha_CO; offsets <0.14 dex: 1
- Agreement with Coppin09 and Gilli11: 1
- Tested with 1 sigma CO points and radially varying alpha_CO: 1
- Only qualitative; authors note need for higher statistics: 1
- Qualitative morphology comparison: 1
- Trend persists if HCN used for dense gas mass: 1
- CO-based SFR consistent with SED SFR: 1
- Compared with KS and Bigiel08 relations: 1
- free-Td fits for two Herschel sources set 90 K and 120 K: 1
- Trends robust to resolution 100–300 pc and aperture 100–400 pc: 1
- Gaussian-cluster test of Lambda_MSR vs concentration: 1
- Agrees with D08 for Δt_SF = 0.6 Myr: 1
- Other SED codes and templates give results within ~0.1 dex: 1
- Range of R51 and alpha_CO explored: 1
- Agrees with earlier G2 and G6 metallicities: 1
- Compared to dust-based masses: 1
- Robustness checks excluding SMGs, outliers, high-z only; alternate metallicity assumptions: 1
- Comparison with Bigiel2008 and Casasola2015: 1
- LABOCA 870 um flux agrees with modeled ALMA flux within ~10%: 1
- compared with Orion Nebula Cluster eps_ff: 1
- Estimated 24 micron PSF Airy ring contamination (~0.1 dex) and excluded pixels within 11'' of bright peaks: 1
- Consistency of the two LIR estimates; A4 and A5 inconsistent hence interlopers: 1
- Compared fit with Boquien et al. 2011 calibration: 1
- Alternative methods consistent within 0.2 dex: 1
- Halpha SFRs compared to SED SFRs; Halpha vs [C II] compared with De Looze relations: 1
- L'_CO compared with L_IR-L'_CO relation; consistent within uncertainties: 1
- Compared single, broken and two-component power laws via reduced chi2: 1
- Conclusions unchanged with Chary01 or Arp220 SEDs; ALMA and Herschel SFRs consistent for four sources detected by both: 1
- Residual SPIRE excess reduced in SED B: 1
- Compared with optically thin models and Arp 220 SED; L_IR differs by ~0.1 dex: 1
- Alternative TIR-based SFR tracers compared in appendix: 1
- Smoothing test: slopes flatten by at most ~10%: 1

### Key parameters and settings (bibcode: value)
- 2025A&A...698A.204H: beta = 1.8, dust temperature free
- 2020A&A...635A.119C: A_V 0-5 in steps of 0.01; Calzetti law; BC03 templates
- 2025ApJ...995..151Y: cos i correction; helium factor 1.36
- 2015ApJ...813...45L: beta=1.5; 50K model beta=2
- 2025A&A...700A.285W: a=0.04, b=-0.93, theta in [0,3pi]
- 2020ApJS..251...14H: SFE 0.1-0.75
- 2015MNRAS.449..715W: k_nu = 0.04 cm2 g-1 (nu/505 GHz)^1.75
- 2015ApJ...809...93D: 1 mm particles; initial dust-to-gas 0.9%; T = 221 (r/AU)^-1/2 K; 1 Msun star
- 2020A&A...641A.155V: includes sources with L_IR>=10^8.5 Lsun and Flag=0.5 upper limits; excludes AGN-dominated galaxies and QSOs
- 2021A&A...656A..60A: aperture radius 0.75'' = 34 pc
- 2024ApJ...976...88L: log Upsilon = 0.195 (F336W-F125W) - 1.187, floor -1
- 2024ApJ...976...88L: SFR = 5.53e-42 L_Halpha
- 2012ApJ...760L..25E: Sigma_SFR = 3.2e-3 I24 + 8.1e-2 IFUV; 3 sigma SFR threshold 0.018 Msun/yr; A_FUV = 8.24 E(B-V)
- 2019PASJ...71...40T: 7 arcsec aperture, aperture correction 2.57
- 2019PASJ...71...40T: alphaCO=4.36 f_metal; f_metal=1.1 at logM=11, 1.4 at 10.5; upper limits 5 sigma with 400 km/s
- 2019ApJ...887...88E: Sigma_mol completeness ~4 Msun/pc2 (3 sigma, 10 km/s)
- 2026ApJ..1001..131C: Temperature correction B_nu(850,25K)/B_nu(850,T_dust): 0.77 (195616), 1.06 (209435)
- 2020ApJS..247...61F: SFR = 4.5e-42 L(Halpha) [erg/s]
- 2020A&A...641A.151S: F_tot/F_25" = 2.0±0.3 at 70 um
- 2013ApJ...770...13W: Td=47 K, beta=1.6
- 2017ApJ...844..123F: Redshift fixed (QSO z for composites, 2.5 otherwise)
- 2018ApJ...858...90G: M/L = 352 Msun/pc2 per MJy/sr at 3.6um
- 2024ApJ...972..147C: 10,000 resamplings; 2 sigma gas cut
- 2021A&A...645A.120F: X_[CI]=3e-5, Q10=0.48, A10=7.93e-8 s^-1
- 2021A&A...656A.133Q: 1 kpc hexagon spacing, 1.5 kpc resolution
- 2017MNRAS.472.1239B: 150 arcsec source radius, background annulus 450-500 arcsec
- 2020MNRAS.495.3840M: alpha_CO = 4.4 Msun (K km/s pc2)^-1 including helium factor 1.36; inclination 50.2 deg
- 2017MNRAS.468L..87C: line width 50 km/s; solid angle 0.044 arcsec^2
- 2021A&A...652A..30S: Schreiber18 templates with Td=25 K and Td=40-50 K; R_SB=1
- 2020MNRAS.499..193K: Molecular gas: CO(2-1)/CO(1-0)=0.7, alpha_CO=4.4 Msun pc^-2/(K km/s) including helium
- 2019ApJ...876...99S: beta fixed at 1.6
- 2017ApJ...850...54C: 5 Myr star formation timescale
- 2025ApJ...994....4A: Common FWHM for three lines; wavelength offset limited to +/-5 A; doublet ratios fixed to 3
- 2020A&A...642A.155Z: radio spectral index alpha = -0.8
- 2017A&A...599A.134S: IR8=8; bootstrap uncertainties
- 2018ApJ...860..103S: f_H2 = 0.03-0.12 initial; t_dep = 0.7-1.3 Gyr
- 2026A&A...705A..39P: RandomForestRegressor, 200 trees, 80/20 train/test split
- 2020ApJ...901...79A: z bins 0.4-1.0, 1.0-2.0, 2.0-3.0
- 2021ApJ...908...54W: 30% mass return to ISM in constant-t_dep model; none in varying model
- 2016PASJ...68..103F: Td 50-70 K, beta=1.7, kappa0=0.005 cm/g at 231 GHz
- 2019MNRAS.485.2092C: Metallicities normalised to MW-mass z~0 galaxy (Mstar=5.7e10)
- 2019MNRAS.487.4305S: KDM eps_ff=0.015; SFK eps_ff=0.0045, b=0.4, beta_mag to infinity
- 2019ApJ...884L..33L: CO S/N > 2; Sigma_* > 1e7 Msun kpc^-2; S/N>3 strong lines, >2 weak lines
- 2019MNRAS.486..560S: Reference template M10; also P08, E11 MS/SB, CE01, DH02, S18 (R_SB=1, 4)
- 2017MNRAS.465.4390B: average of (T=47K, beta=1.6) and (T=41K, beta=1.95)
- 2018MNRAS.475.1288S: DeltaBIC>2 for AGN component; 10^5 bootstrap draws
- 2018ApJ...861....7F: dt = depletion time (~640 and 210 Myr) or ~1.0 Gyr
- 2018ApJ...861L..18U: K=1.04e-1 (FUV), 1.04e-1 (NUV), 3.77e-3 (12um), 2.97e-3 (24um)
- 2017ApJ...836L...2B: disk diameter ~0.6''; b/a = 0.6
- 2017A&A...604A.117C: T=50 K, beta=2.0; alpha_CO=0.8; r43/10=0.6; SFR divided by 1.8 for Chabrier
- 2019ApJ...881...63N: kappa=2.64 m2/kg at 125 um; T_dust=47 K
- 2017ApJ...835..278S: t_gas=35 Myr, t_over=5 Myr, t_star=10 Myr, lambda=400 pc, beta=1
- 2017ApJ...842L..21N: 105 templates × 10^4 amplitudes (0–100)
- 2017ApJ...851...18L: Only spaxels with S/N(CO) > 2 shown in KS relation; Galaxy 3 bulge excluded from correlations due to AGN
- 2017ApJ...844L..10S: beta = 1.8
- 2019ApJ...882..137P: TNG100 f_H=0.76; T_SF=1000 K; Sigma_SFR,MW=0.004 Msun/yr/kpc^2
- 2017ApJ...851..145M: T_d = 35 K, beta_IR = 1.5
- 2017ApJ...834..135T: w=0.6, eta~1, Mgas/SFR uncertainty ±0.24 dex
- 2019ApJ...882..136A: starburst log(delta_MS)>0.4; passive <-0.4


### Assumptions (bibcode: value)
- 2019ApJ...876..130H: gas fraction of unity, dust-to-gas 1/90, global dust temperature, Kennicutt98 IR SFR calibration with Chabrier IMF
- 2019ApJ...876..130H: gas disk dominates over stellar component; radius = HWHM of ALMA emission along major axis
- 2018ApJ...863..129S: alpha_HCN(1-0)=10; constant T_dust = 25 K for Sigma_H2
- 2018ApJ...863..129S: n_dense=2.8e5 cm^-3, eps_SF=0.28%
- 2025A&A...698A.204H: Chabrier IMF; SFR_IR = 1.40e-10 L_IR
- 2020A&A...635A.119C: Solar metallicity; four SFHs (B, E, Sb, C)
- 2020ApJ...903..145L: alpha_CO = 4.35 Msun (K km/s pc^2)^-1; Salpeter IMF
- 2014A&A...562A..67G: Cosmology H0=67, Om=0.32, OL=0.68; 1 arcsec=6.6 kpc
- 2025ApJ...995..151Y: X_CO = 2e20 cm^-2 [K km/s]^-1; alpha_CO = 4.35
- 2025ApJ...995..151Y: Constant mass-to-light ratio 0.35 Msun/Lsun
- 2018A&A...615A..94F: Distance 3.6 kpc; spherical clump with density contrast 10; stopped at SFE 15%
- 2015ApJ...813..118M: alpha_HCO+ ≈ 10, alpha_CO ≈ 4.3 Msun/(K km/s pc^2); mean 33 GHz thermal fraction 79%
- 2019ApJ...887...74F: kappa_1THz=20 cm2/g; lambda_Edd=1; L'CO(5-4)/L'CO(3-2)=0.7
- 2018ApJ...863..193V: SFR uncertainty factor of two; Salim07 UV calibration (Chabrier IMF)
- 2015ApJ...813...45L: z=2 for sources without redshift
- 2020A&A...635A...2S: Star formation efficiency 30%, so 20 Msun core forms B-type star
- 2020ApJS..251...14H: each leaf collapses on a freefall time
- 2015MNRAS.449..715W: gas-to-dust ratio 100
- 2015MNRAS.448.2224C: current mass ~4x the mass at 10 Gyr; 1:1 1G:2G
- 2015ApJ...809...93D: Schmidt number Sc=1; Epstein drag; no dust feedback
- 2017MNRAS.469.4683C: delta_GDR ~ 120 from 12+log(O/H)=8.53; Kennicutt 1998 L_IR-SFR, Chabrier IMF
- 2017MNRAS.469.4683C: MS: R51=0.23, alpha_CO=4.87; SB: R51=0.6, alpha_CO=1
- 2019MNRAS.485.1595P: Galactic alpha_CO=4.6 Msun (K km/s pc^2)^-1 for depletion times
- 2024A&A...692A.215C: Chabrier IMF; flat LCDM Om=0.3, OL=0.7
- 2024A&A...692A.215C: alpha_CO depends on metallicity (Genzel 2015)
- 2020A&A...641A.155V: Gas mass from M_dust with metallicity-dependent gas-to-dust ratio log(delta_GDR)=10.54-0.99x(12+log(O/H)); starbursts supersolar (delta_GDR~30); Sigma_SFR=SFR/…
- 2021A&A...656A..60A: alpha_CO=4.36, r31=0.27, 45% missing flux correction, inclination 57 deg, Calzetti extinction
- 2013ApJ...767..132H: Standard starburst SFR conversion (Kennicutt 1998)
- 2024ApJ...976...88L: Constant alpha_CO = 4.35 Msun (K km/s pc^2)^-1, or variable alpha_CO from Bolatto+13 eq. 31 iterated until change <0.1%
- 2024ApJ...976...88L: Krumholz+18 fiducial parameters; P*/m* = 3000 km/s for Faucher-Giguere model
- 2018ApJ...855L..25K: eps_core = 0.5; steady SFR; Salpeter CMF 1-240 Msun; mm continuum is complete protostellar core census
- 2019A&A...621A..27F: SFR = 1.72e-10 L_IR_SF, Salpeter IMF then /1.5 to Kroupa
- 2018ApJ...862...64S: Salpeter IMF; BzK and ULIRG CO SLEDs
- 2014ApJ...790..160S: alpha_CO = 0.86 Msun (K km/s pc^2)^-1, 0.5 dex error; outflow assumes L'(3-2)/L'(1-0)=1
- 2024A&A...682A..54T: Chabrier IMF
- 2019PASJ...71...40T: [NII] correction from mass-metallicity relation; A_Halpha systematic 0.32 mag
- 2019PASJ...71...40T: Field-like CO excitation, no environmental dependence
- 2019ApJ...887...88E: Fixed inclination 70 deg
- 2026ApJ..1001..131C: alpha_nu = 6.7 +/- 1.7e19 erg/s/Hz/Msun; 25 K calibration
- 2026ApJ..1001..131C: Photon index 1.4 for X-ray; radio spectral index -0.8
- 2020ApJS..247...61F: f-factor 0.44 (likely upper limit on LHalpha); Calzetti and SMC reddening
- 2020A&A...641A.151S: alpha_CO=1.1, solar metallicity, CO(2-1)/CO(1-0)=3
- 2025ApJ...988..162D: Radially varying alpha_CO (Bolatto2013/Sun2022); alpha_CO(1-0)=4.35 for sensitivity estimate
- 2019PASJ...71...44H: Weidner13 mmax-Mecl relation
- 2015MNRAS.453L..83M: L_IR accurate to ±0.3 dex from SED template range, included in analysis; Chabrier IMF
- 2017ApJ...844..123F: Constant dust temperature, local thermal equilibrium
- 2018ApJ...858...90G: alpha_CO = 4.3, alpha_HCN = 10 Msun pc-2 (K km/s)-1, include helium
- 2024ApJ...972..147C: SFR maps scaled to TIR total SFR (Kroupa IMF); gas maps scaled by CO line ratios
- 2021A&A...645A.120F: Tdust=40 K for the continuum cross-check; X_[CI]=1e-5 for region A
- 2015A&A...584A..78C: 1.3 mm flux corresponds to redshift-independent IR luminosity for 0.5<z<15; SFR from Kennicutt & Evans 2012
- 2024ApJ...977L...6F: Metallicity-dependent CO-to-H2 conversion factor
- 2016MNRAS.457.4536W: 30% global SFE upper limit for clouds
- 2015ApJ...815..103B: alpha_HCN=10, alpha_CO=4.35, Murphy et al. 2011 TIR-to-SFR
- 2019ApJ...881..124M: Td=45 K, β=1.5, κ850=0.077 m^2/kg
- 2017MNRAS.472.1239B: WISE 22 micron conversion same as Spitzer 24 micron
- 2024A&A...685A..80Z: constant SFR
- 2020NatAs...4..670A: L_CO(7-6)/L_CO(1-0)=0.24; ULIRG X_CO (Downes1998)
- 2020NatAs...4..670A: LAB6.1 fraction of FIR luminosity follows 1.2 mm continuum
- 2015MNRAS.452...54M: Local S-K relation; solar metallicity foreground
- 2018ApJ...867..140L: T_dust = 41 K, beta = 1.5, bolometric factor 1.91, Kennicutt 1998 SFR
- 2018ApJ...867..140L: mu = 10.9; inclination average <v_rot> = pi/2 v_obs
- 2017MNRAS.468L..87C: CO(2-1)/CO(1-0) = 0.8; tau_dep = 2 Gyr, 0.2 Gyr, 20 Myr
- 2024ApJ...976...70L: SFRs divided by 1.6 to convert Salpeter to Chabrier IMF
- 2021A&A...652A..30S: Salpeter IMF; H0=70, Om=0.3, OL=0.7
- 2020MNRAS.499..193K: CO dispersion scaled to ~1 kpc scale height with sigma ∝ L^1/2
- 2014A&A...568A..92M: Xco thin ~0.449 (T=35.9 K, [CO/H2]=1e-4) lower limit; Xco=5 upper limit
- 2019ApJ...876...99S: kappa_125um = 18.75 cm2/g; Salpeter IMF with Kennicutt 1998 SFR
- 2017ApJ...850...54C: Kroupa IMF
- 2025ApJ...994....4A: E(B-V)_stellar/E(B-V)_nebular = 0.83; Kennicutt (1998) SFR relation modified for Chabrier IMF
- 2020ApJ...889....9M: Chabrier IMF; Balmer decrement dust correction
- 2014ApJ...792...34O: Dwarf-galaxy T_dust=27.6 K, beta=1.5; Salpeter IMF; cosmology (0.3,0.7,0.7)
- 2017A&A...599A.134S: Single T_dust=40 K for all galaxies; Kennicutt 1998 SFR conversion; Salpeter IMF
- 2026A&A...705A..39P: Uniform spherical clouds, 40 shells; GOW chemistry; CR rate from depletion time
- 2016A&A...586L...7B: Chabrier IMF; magnification 5.7
- 2016PASJ...68..103F: Lbol ≈ LFIR
- 2025A&A...695A...6P: Case B Halpha/Hbeta=2.86
- 2020A&A...643A...6C: Case B recombination, Chabrier IMF, one-fifth solar metallicity
- 2020MNRAS.497.2771M: LCDM H0=70, OmegaM=0.3, OmegaL=0.7; Chabrier IMF; alpha_CO 4.6 (B,D) and 0.8 (mergers)
- 2015ApJ...810..133I: H0=70, OmegaM=0.3, OmegaL=0.7
- 2019MNRAS.485.2092C: Gas dominated by molecular gas at z=2
- 2019ApJ...882....5W: Constant X_CO; no inclination correction; NGC 7469 nucleus excluded
- 2019ApJ...882....5W: alpha+beta~0.3, Sigma_gas/Sigma_total~0.5, g_galaxy/g~0.05-0.2
- 2020MNRAS.494.3828D: half of gas available to form stars
- 2015ApJ...810...91H: kappa_d(125 um)=2.64±0.29 m^2/kg, beta=1.5, T_dust=30-40 K
- 2019MNRAS.487.4305S: Zero magnetic field in SFK
- 2019ApJ...884L..33L: alpha_CO = 4.3; Salpeter IMF; Rv = 4.5
- 2019MNRAS.486..560S: Old stellar heating neglected, so SFRs are conservative upper values
- 2019MNRAS.486..560S: Lambda-CDM H0=70, Om=0.3, OL=0.7; Salpeter IMF
- 2017ApJ...849...90S: Td = 20 and 100 K; X_CO = 0.8e20; Te = 5000 K; d = 10.8 Mpc
- 2019ApJ...876..112R: linear mapping 160-um to SFR; no AGN contribution; universal IMF
- 2019AJ....157..131B: alpha_HCN ≈ 10, alpha_CO ≈ 7 M_sun (K km/s pc^2)^-1; distance 22 Mpc
- 2017MNRAS.465.4390B: kappa0=0.045 m2/kg at 250 GHz
- 2018ApJ...861....7F: constant SFR, no radial motions of stars
- 2017ApJ...836L...2B: Axisymmetric thin disk; dark matter negligible
- 2019ApJ...870...39V: Gas in an inclined disk with inclination from 3DBAROLO
- 2017A&A...604A.117C: alpha_CO=0.8 Msun (K km/s pc2)^-1
- 2019Natur.569..519K: H-alpha SFR calibration of Murphy et al. 2011, Kroupa IMF, 20% uncertainty
- 2019ApJ...881...63N: Optically thin dust; Kennicutt98 SFR relation with Chabrier IMF
- 2017ApJ...842L..21N: Chabrier IMF
- 2018ApJ...856...72O: Salpeter IMF, Kennicutt 1998 calibration, ALESS SED for all components
- 2017ApJ...834....6S: Free-free emission dominates 110 GHz
- 2018ApJ...854L...4R: Maximal AGN scenario: all 5.8-8.0 um emission from AGN
- 2018A&A...616A.110E: local GDR-metallicity relation holds at all redshifts; M_Chabrier=M_Salpeter/1.7
- 2017ApJ...838..146L: normal IMF
- 2018MNRAS.478.1170C: Td=30 K, beta=1.5; total SFR ~ SFR_UV unless continuum detected
- 2018MNRAS.476..122V: Galactic X_CO
- 2016ApJ...827L..32B: delta_GDR ~100 from MZR, Z=8.57
- 2019A&A...623A..66B: R21=0.7; X_CO = 2e20 cm^-2/(K km/s) with helium; Sigma_H2 = 4.2 I_1-0
- 2017ApJ...844L..10S: mBB underestimates L_FIR by ~20%; corrected; SFR from Kennicutt98
- 2016A&A...586A..45S: clump radius ~20 pc
- 2019ApJ...882..137P: Dust abundance D_MW = Z/Zsun
- 2018PASJ...70L...6K: kappa_850 = 3.2 cm2/g
- 2018ApJ...859...12G: remaining FIR fraction originates from the annulus
- 2017ApJ...835...98U: z=3.0 for ADF22.2 and ADF22.5 lacking zspec
- 2017ApJ...849..154S: sources at cluster redshift; Chabrier IMF
- 2017ApJ...851..145M: CMB contribution removed; [CII] line contamination negligible
- 2018ApJ...854...97D: T_dust=47 K
- 2018ApJ...864...38L: Chabrier IMF; Sigma_SFR = (1/2 SFR)/(1/4 pi d^2)
- 2019ApJ...887..183Z: Planck cosmology H0=68, OmegaLambda=0.69; Chabrier IMF
- 2016ApJ...833...68A: Td=25 K, beta=1.8, delta_GDR=200 for MAGPHYS masses
- 2017A&A...606A..17M: optically thick starburst, solar metallicity; cirrus heating ignored
- 2017ApJ...842L..16L: Sigma_SFR = 2e3 Msun/yr/kpc^2; Chabrier IMF
- 2016ApJ...833...12R: T_dust = 25 K (20-30 K for uncertainty); gas-to-dust ratio 100
- 2017ApJ...834..135T: current SFR maintained; outflow rate comparable to SFR (eta~1)
- 2019ApJ...887..144J: 20% dark matter in dynamical gas mass; T_ex=30 K for [CI]
- 2019ApJ...877L..38R: SFR from total IR luminosity with Kennicutt (1998) conversion; Chabrier IMF
- 2016ApJ...828...56W: Salpeter IMF
- 2017ApJ...846..108C: Chabrier IMF; alpha_CO=0.8; Halpha not extinction corrected
- 2019ApJ...882...10N: Td = 30-50 K, beta = 1.2-2.0; 0.5 dex scatter on SFR_CII
- 2016MNRAS.457L.122H: H0=70, OmegaM=0.30, OmegaL=0.70
- 2017A&A...605A..42C: Td 25-45 K; Kennicutt & Evans FIR-SFR
- 2018MNRAS.477.4380S: Chabrier IMF; H0=72, Om=0.27
- 2016ApJ...833..195W: z=2; Chary & Elbaz 2001 SED; Kennicutt 1998 SFR conversion
- 2019MNRAS.489..427I: Same SED as W; alpha_CO=0.8


### Limitations the authors admit
- 2019ApJ...876..130H: Single dust temperature assumed across sources, affecting Sigma_SFR maps
- 2019ApJ...876..130H: Interpretations require kinematic confirmation; small sample
- 2018ApJ...863..129S: Possible synchrotron contamination of 110 GHz SFR (~25%); absolute values uncertain due to conversion factors
- 2025A&A...698A.204H: Gas mass has large systematic uncertainties from alpha_CO, which are ignored; CI excitation not constrained
- 2025A&A...698A.204H: Simulation comparison is only qualitative
- 2020A&A...635A.119C: Small sample (six) with archival heterogeneous IFU data, hard to assess selection bias
- 2020ApJ...903..145L: Small HI sample limits conclusions
- 2014A&A...562A..67G: Size measurement needs confirmation at higher resolution; sparse uv sampling
- 2025ApJ...995..151Y: Constant Galactic alpha_CO adds systematic uncertainty; no resolved metallicity
- 2025ApJ...995..151Y: Two galaxies have slopes from only two CO data points
- 2018A&A...615A..94F: Fragment numbers are lower limits due to large missing flux and pointing offsets
- 2018A&A...615A..94F: Mass estimates are likely upper limits for warm fragments; simulations use single spherical clumps
- 2015ApJ...813..118M: Only three regions; nuclear HCN cut off by bandpass; single-component fit poor for Enuc. 2
- 2019ApJ...887...74F: Limited depth and resolution prevent distinguishing disk, merger and outflow
- 2019ApJ...887...74F: Dust mass depends strongly on the adopted kappa
- 2018ApJ...863..193V: The cavity is poorly defined and may not be real
- 2018ApJ...863..193V: HST images manually aligned, so small-scale offsets between gas and UV may be missed
- 2015ApJ...813...45L: Dust temperature unconstrained for most sources; L_BB and SFR uncertain by orders of magnitude
- 2025A&A...700A.285W: Torque method unvalidated by simulations, configuration likely unstable
- 2025A&A...700A.285W: Mass of young component is poorly constrained from single UV band; closed-box and alpha_CO assumptions
- 2020A&A...635A...2S: Temperatures assumed rather than measured; unresolved multiplicity biases CMF
- 2020A&A...635A...2S: Low number statistics limit Q-parameter conclusions
- 2020ApJS..251...14H: Completeness assumes point sources and does not capture extended emission; masses uncertain by factor ~2
- 2015MNRAS.449..715W: Mass estimates uncertain due to cloud boundary definition and a factor ~2 systematics; gas temperature measured only for G0.253
- 2015MNRAS.448.2224C: Upper limits depend on X_CO, which may be overestimated by up to an order of magnitude
- 2017MNRAS.469.4683C: Clump SFRs vary by up to ~1 dex between methods and clump R51/alpha_CO are poorly constrained
- 2019MNRAS.485.1595P: CO-to-H2 conversion factor is uncertain, so masses are expressed as functions of alpha_CO
- 2019MNRAS.485.1595P: Analysis of G0 hampered by the bright quasar; GalPak3D did not converge for several galaxies
- 2024A&A...692A.215C: Scatter in r31 and r41 relations adds systematic errors
- 2020A&A...641A.155V: LVG parameters highly degenerate; best-fit values reflect relative trends only
- 2020A&A...641A.155V: Sample biased to upper main sequence and warm dust by PACS detection requirement
- 2021A&A...656A..60A: Missing flux ~40-50% due to lack of single-dish data.
- 2021A&A...656A..60A: Mass model parameters are degenerate.
- 2013ApJ...767..132H: Only compact-configuration data used; SPT0529-54 posterior bimodal
- 2024ApJ...976...88L: Literature comparison sample is heterogeneous and of differing data quality
- 2018ApJ...855L..25K: Dust temperature assumption is the largest uncertainty (up to factor ~2); MIREX has zero-point offsets, saturation and MIR-source contamination.
- 2012ApJ...760L..25E: Clumps mostly unresolved; higher resolution needed; short spacings needed
- 2012ApJ...760L..25E: Inclination of the arm is uncertain
- 2019A&A...621A..27F: Upper limits dominate many SFRs; no intermediate-frequency data to determine synchrotron steepening
- 2018ApJ...862...64S: Small field and low-number statistics; field comparison selection not equivalent
- 2014ApJ...790..160S: Outflow quantities order-of-magnitude; XCO and line ratio uncertain
- 2024A&A...682A..54T: Resolution cannot distinguish merging from rotation, or single from multiple companions
- 2019PASJ...71...40T: Larger sample needed; CO excitation assumed; low-mass detections biased
- 2019ApJ...887...88E: Large scatter, projection effects and warped disk uncertainty in the KS fits; XCO uncertainty in CND
- 2026ApJ..1001..131C: A3COSMOS gas masses do not include AGN contribution; AGN may bias gas mass of 195616
- 2020ApJS..247...61F: Spitzer blending can overestimate stellar masses; about one-third have contaminated Spitzer photometry
- 2020ApJS..247...61F: f-factor is the largest uncertainty in the Halpha measurement
- 2020A&A...641A.151S: ALMA configuration resolves out diffuse gas; MRS 6.2 arcsec
- 2020A&A...641A.151S: Cannot exclude free-free contribution to continuum
- 2013ApJ...770...13W: Source only marginally resolved; intrinsic size poorly constrained and inclination unknown
- 2013ApJ...770...13W: L_FIR uncertainties exclude dust temperature uncertainty
- 2025ApJ...988..162D: Small sample; individual outliers can affect galaxy-to-galaxy trends
- 2025ApJ...988..162D: Metallicity covers only ~0.25 dex and 8 galaxies
- 2019PASJ...71...44H: SFE is an upper limit; CO-dark gas possible
- 2015MNRAS.453L..83M: Log-normal is not a literal description of the true AGN distribution
- 2018A&A...617A..82B: Inclinations and sizes of marginally resolved sources are uncertain, affecting dynamical masses
- 2017ApJ...844..123F: Redshifts of non-QSO SMGs unknown (assumed 2.5), making their results less reliable
- 2017ApJ...844..123F: Size measurements at SNR<10 are biased high
- 2017ApJ...844..123F: Duty cycle is an upper limit since no BH accretion assumed in SMGs without QSOs
- 2018ApJ...858...90G: Sample not representative; simple alpha_CO and alpha_HCN; limited to inner few kpc
- 2024ApJ...972..147C: LVG parameters highly degenerate; large uncertainty in non-thermal index; unknown CI excitation
- 2021A&A...645A.120F: Low S/N; Lyα and HeII severely affected by night sky lines
- 2021A&A...645A.120F: Mass uncertainty excludes errors on X_[CI], Q10, A10
- 2021A&A...656A.133Q: Spiral masks are broad; contrasts may be resolution-dependent; centre results sensitive to alpha_CO and AGN contamination
- 2015A&A...584A..78C: CIB uncertainties prevent a precise resolved fraction; no source redshifts or SEDs
- 2024ApJ...977L...6F: Systematic biases affect barred and non-barred samples differently
- 2016MNRAS.457.4536W: Masses are upper limits due to the isothermal assumption; small sample and limited resolution
- 2015ApJ...815..103B: Different uv coverage between CARMA and ALMA makes CO line ratios uncertain; CARMA may resolve out flux
- 2019ApJ...881..124M: MASOSA red colour needs deeper observations; HST cannot distinguish one vs two components
- 2019ApJ...881..124M: ALMA-HST astrometry uncertain at 0.1-0.2''
- 2017MNRAS.472.1239B: Lack of H30alpha from fainter sources could bias SFR downward; most continuum emission <5 sigma
- 2024A&A...685A..80Z: Clump C is tentative and needs confirmation; dynamical modelling is beyond scope
- 2020NatAs...4..670A: Uniform shell model over-simplified; results rough estimate
- 2020MNRAS.495.3840M: alpha_CO may be a factor of a few lower in the bar, so Sigma_mol could be overestimated
- 2020MNRAS.495.3840M: SFR below 1e-3 Msun/yr/kpc2 should be considered upper limits
- 2015MNRAS.452...54M: Dust temperature unconstrained from single upper limit; dynamical mass extremely uncertain; B1/B2 marginal; lensing speculative
- 2025ApJ...990..221M: Large beam may blend gas from different regions, causing apparent connections; alpha_CO uncertain so mass may be an upper limit
- 2018ApJ...867..140L: Lens model lacks external shear and mass-profile variation; ALMA may resolve out flux
- 2017MNRAS.468L..87C: Cold dust mass is only an estimate; alternative dust properties would change it
- 2024ApJ...976...70L: Dust luminosity relies on single ALMA band; temperature variations could affect result
- 2021A&A...652A..30S: ALMA data not deep enough to confirm or reject 39% of observed candidates; SFR depends on IR template
- 2020MNRAS.499..193K: MUSE spectral resolution is larger than measured Halpha dispersions, so these are uncertain
- 2014A&A...568A..92M: Knot C in rest-frame optical poorly fitted by the lens model
- 2026ApJ..1003...52D: Small sample with limited dynamic range in excitation
- 2019ApJ...876...99S: Lack of NIR/MIR data prevents distinguishing dust models
- 2017ApJ...850...54C: Missing short spacings; about half of expected flux recovered
- 2025ApJ...994....4A: Small sample, N2 selection bias toward high metallicity and high gas fraction
- 2025ApJ...994....4A: Metallicity calibration differs from that of the FMR
- 2020A&A...642A.155Z: Single lines cannot give definitive redshifts
- 2020ApJ...889....9M: Resolution cannot exclude that regions comprise unresolved clouds
- 2020ApJ...889....9M: Detailed kinematic characterization left for future work
- 2014ApJ...792...34O: Single object; may not be representative of LAE population
- 2024ApJ...964...18C: Data concentrated in narrow metallicity range 8.4-8.6, limiting metallicity analysis
- 2017A&A...599A.134S: Sample likely biased against heavily obscured H-dropout galaxies
- 2018ApJ...860..103S: Small sample of 8; alpha_CO systematic uncertainty ~50%; SFR from 24um may be overestimated up to ~2x
- 2026A&A...705A..39P: Simulation volume cannot sample SFR>~100 Msun/yr systems typical of observed high-z sources
- 2020ApJ...901...79A: MAGPHYS stellar masses may be systematically underestimated; small source numbers may drive redshift trend
- 2021ApJ...908...54W: Mostly upper limits on M_H2 and SFR preclude robust depletion time measurement
- 2021ApJ...908...54W: alpha_CO uncertainty of factor >=2
- 2014ApJ...783...84S: Pathfinder, small samples, only most massive galaxies; results preliminary
- 2025A&A...698A.296R: Upper limits for lambda and t_fb in many arms; alpha_CO and R21 may differ between environments; diffuse ionised gas leakage may bias inter-arm SFE
- 2016A&A...586L...7B: Depletion time may be underestimated if source is at end of starburst; differential magnification may affect line ratios
- 2016PASJ...68..103F: Beam does not resolve the cloud; higher resolution and sensitivity needed
- 2025A&A...695A...6P: Origin of the broad components remains uncertain
- 2020A&A...643A...6C: S/N of spectra insufficient to analyse ISM line morphologies; only centroids
- 2020MNRAS.497.2771M: Optical depth not accounted; 12CO/13CO luminosity ratios are lower limits to abundance ratios; degeneracy between starburst age and top-heavy IMF
- 2015ApJ...810..133I: Large Sigma_SFR uncertainties for ~0.1" sources; only 13 sources; redshifts mostly lower limits
- 2019MNRAS.485.2092C: Gas masses rely on assumed MS SFE; effect of MS offset cannot be dissected with five galaxies
- 2019ApJ...882....5W: sigma_v overestimated by up to 20% from beam smearing and up to 12% from channelization
- 2026A&A...705A..81K: Low per-channel S/N prevents full delensed cubes; source plane resolution insufficient to resolve clumps; results preliminary.
- 2020MNRAS.494.3828D: magphys underestimates stellar mass by 0.46 dex vs EAGLE; fixed gas-to-dust ratio
- 2015ApJ...810...91H: Fields centered on z~1.4 galaxies could be biased regions
- 2019MNRAS.487.4305S: Large systematic uncertainties; magnetic field strength unknown; need larger sample
- 2019ApJ...884L..33L: Small number of galaxies may explain steeper rSFMS slope; Sigma_* range only 1.5 dex
- 2025ApJ...988..135M: Visual merger classifications are subjective and may miss minor mergers.
- 2025ApJ...988..135M: Stellar masses depend on the assumed attenuation curve (~0.4 dex).
- 2020MNRAS.491.4724F: IR SED shape/dust temperature could change slope; low-mass stacks only upper limits
- 2019MNRAS.486..560S: Archival ALMA data not deep enough to confirm most candidates individually; FIR template choice spans nearly a decade in SFR
- 2017ApJ...849...90S: X_CO analysis beyond scope; masses uncertain by factor of few
- 2019ApJ...876..112R: Only two galaxies; extended [CII] likely resolved out

### Settings cards flag as needed but not stated
- casa version: 8
- flux calibrator and flux scale uncertainty: 7
- line-free channels and continuum subtraction method: 5
- continuum subtraction and line-free channels: 5
- self-calibration solution intervals: 4
- flux scale uncertainty: 4
- image size and cell size: 3
- casa version and pipeline version: 3
- line-free channels for continuum subtraction: 3
- line-free channels used for uvcontsub: 3
- primary beam correction details: 3
- line-free channel ranges used for continuum: 2
- flux calibrators and flux-scale uncertainty: 2
- line-free channels used for continuum: 2
- flux calibrator and flux-scale uncertainty: 2
- clean threshold, masking, image size and cell size: 2
- line-free channels used for continuum subtraction: 2
- coordinates of targets: 2
- primary-beam correction details: 2
- line-free channels and continuum subtraction: 2
- rest frequencies used for the lines: 2
- clean threshold, mask, cell and image size: 2
- cell size, image size, clean threshold and masks: 2
- cprops parameters: 2
- casa/pipeline version: 2
- line-free channel ranges for uvcontsub: 2
- clean threshold, masks and iterations: 2
- self-calibration and flux scale details: 2
- continuum-subtraction method and line-free channels: 2
- line-free channels and continuum subtraction method for cubes: 2
- casa version and calibration approach: 2
- uvmodelfit starting parameters: 2
- primary beam correction: 2
- cell and image size: 2
- multi-scale clean scale values: 1
- clean threshold/niter and mask definitions per source: 1
- weighting and taper details for 0.07" and 0.05" maps: 1
- the sfr values for each source needed for sigma_sfr maps (da cunha et al. in prep): 1
- dust-to-gas ratio source (referred to as 'same as above' but not given): 1
- toomre/jeans calculation details (gas surface density conversion, kappa): 1

## Paper excerpts (40 of 160, chosen for detail and spread over fields/years)

### 2019ApJ...876..130H: ALMA Reveals Potential Evidence for Spiral Arms, Bars, and Rings in High-redshift Submillimeter Galaxies (2019; high_z_galaxies; observational_alma_primary)
- question: Does sub-kpc-resolution 870 um continuum imaging of ALESS SMGs reveal substructure (clumps, bars, rings, spiral arms), and what does it imply for star formation rate density relative to the Eddington limit?
- step 4: Build Sigma_SFR maps
  - method: Scale SED-derived total SFR by per-beam fraction of total 870 um flux; galaxy-average = 0.5xSFR/(pi Re^2) [3.3 Star formation rate surface density…: "galaxy-averaged values calculated using the half-light radii as 0.5$\times$SFR/($\pi$R$_{e}^{2}$)"]
  - validation: SFR range cross-checked with modified blackbody + Kennicutt98 relation (cited) [3.3 Star formation rate surface density…: "instead using simple modified blackbody fits with, e.g., the (cite: Kennicutt1998) IR SFR relation (re-scaled to the (cite: Chabrier2003) IMF) returns the same results"]
- step 5: Compare to Eddington limit
  - method: Estimate optical depth from peak intensity and MAGPHYS dust T; adopt optically thick Eddington flux of Andrews & Thompson, convert to SFR density, compare with Sigma_SFR and local U/LIRGs [4.1 The intensity of the star formation: "we derive a lower limit on the Eddington-limited $\Sigma_{\mathrm{SFR}}$ of $\sim$650 M$_{\odot}$ yr$^{-1}$ kpc$^{-2}$"]
  - assumption: gas fraction of unity, dust-to-gas 1/90, global dust temperature, Kennicutt98 IR SFR calibration with Chabrier IMF [4.1 The intensity of the star formation: "Assuming the same dust-to-gas ratio as above (1/90) and adopting a gas fraction of unity as the most extreme scenario"]
- step 6: Velocity dispersion constraints (Jeans, Toomre)
  - method: Jeans length equal to largest clump size gives lower limit; Toomre Q<1 with flat-rotation-curve epicyclic frequency gives upper limit; gas surface density from global Sigma_SFR [4.3 Evidence for interaction, bars, rin…: "we derive upper limits for the one-dimensional velocity dispersion of the potentially barred sources of $\sigma_{\rm r} \lesssim$ 70–160 km s$^{-1}$"]
  - assumption: gas disk dominates over stellar component; radius = HWHM of ALMA emission along major axis [4.3 Evidence for interaction, bars, rin…: "Here we assume that the gas disk dominates over the stellar component."]
  - validation: Toomre upper limits marginally consistent with Jeans lower limits [4.3 Evidence for interaction, bars, rin…: "these Toomre-based upper limits are consistent, albeit marginally, with the lower limits derived from equating the sizes of the largest ‘clumps’ observed to the Jeans length"]
- result: Eddington-limited Sigma_SFR lower limit = ~650 ± not stated Msun/yr/kpc^2 [4.1 The intensity of the star formation: "lower limit on the Eddington-limited $\Sigma_{\mathrm{SFR}}$ of $\sim$650 M$_{\odot}$ yr$^{-1}$ kpc$^{-2}$"]
- result: Peak Sigma_SFR at 0.07" for ALESS 9.1 = 547 ± +102/-93 Msun/yr/kpc^2 [Table 4: "| ALESS 9.1 | 102$^{+27}_{-32}$ | 547$^{+102}_{-93}$ | 575$^{+116}_{-108}$ |"]
- result: Toomre velocity dispersion upper limits = <70–160 ± not stated km/s [Table 5: "| ALESS 76.1 | $>$100 | $<$160 |"]
- limitation (authors): Single dust temperature assumed across sources, affecting Sigma_SFR maps [4.1 The intensity of the star formation: "One important caveat in the above analysis is the previously stated assumption of a single dust temperature across the sources."]
- limitation (authors): Interpretations require kinematic confirmation; small sample [Summary: "a larger sample size is important for moving beyond the handful of submillimeter-brightest sources studied here"]
- not stated (card): multi-scale clean scale values; clean threshold/niter and mask definitions per source; image size and cell size; weighting and taper details for 0.07" and 0.05" maps; the SFR values for each source needed for Sigma_SFR maps (da Cunha et al. in prep); dust-to-gas ratio source (referred to as 'same as above' but not given); Toomre/Jeans calculation details (gas surface density conversion, kappa); g…

### 2018ApJ...863..129S: Spatially Resolved Dense Molecular Gas Excitation in the Nearby LIRG VV 114 (2018; nearby_galaxies, star_formation, astrochemistry; observational_alma_primary)
- question: How does dense molecular gas excitation, star formation efficiency and chemistry vary across the AGN, starburst and shocked Overlap regions of the merging LIRG VV 114?
- step 3: Measure aperture fluxes and Sigma_dense, SFE, f_dense
  - method: Fluxes in eleven 3'' apertures; M_dense = alpha_HCN L'_HCN(1-0) [5.2: "$\Sigma_{\rm dense}$ is calculated by dividing the dense gas mass ($M_{\rm dense}$) by the aperture area."]
  - assumption: alpha_HCN(1-0)=10; constant T_dust = 25 K for Sigma_H2 [5.3: "assuming a constant $T_{\rm dust}$ of 25 K"]
  - validation: Tested alternate SFR tracer (8.4 GHz) and conversion factors [5.3: "since the general trend does not change regardless of the employed SFR tracer or adopted conversion factor"]
- step 4: Fit Sigma_SFR vs flux slopes and compare turbulence-regulated model
  - method: Log-log slope fits excluding Region 1; Krumholz & McKee turbulence-regulated model grid in Mach number and mean density over SFE_H2 vs f_dense [5.1: "We estimate the slope by fitting all the data points except Region 1"]
  - assumption: n_dense=2.8e5 cm^-3, eps_SF=0.28% [5.3: "we assume $n_{\rm dense}$ = 2.8 $\times$ 10$^5$ cm$^{-3}$ and $\epsilon_{\rm SF}$ = 0.28%"]
  - validation: Density threshold model rejected via correlation coefficient -0.55 [5.3: "VV 114 data do not show such a positive linear correlation (the correlation coefficient is -0.55)"]
- result: HNC(1–0)/HCN(1–0) at E0 = 0.85 ± 0.23 dimensionless [4.3: "The HNC (1–0)/HCN (1–0) line ratio at E0 is 0.85 $\pm$ 0.23"]
- result: HCN(4–3)/CS(7–6) at E0 = 4.9 ± 1.3 dimensionless [4.3: "The HCN (4–3)/CS (7–6) ratio is 4.9 $\pm$ 1.3 at the AGN position of VV 114 (E0)."]
- result: Slope Sigma_SFR vs HCN(1–0) flux = 2.03 ± 0.18 dimensionless [5.1: "are 2.03 $\pm$ 0.18, 0.83 $\pm$ 0.07, 0.65 $\pm$ 0.04, 1.69 $\pm$ 0.67, 1.30 $\pm$ 0.16, and 0.84 $\pm$ 0.14"]
- result: Slope vs HCN(4–3) flux = 0.65 ± 0.04 dimensionless [5.1: "2.03 $\pm$ 0.18, 0.83 $\pm$ 0.07, 0.65 $\pm$ 0.04"]
- result: M_dense Region 6 = 1.8e8 ± 0.2e8 Msun [5.2: "$M_{\rm dense}$ = (1.8 $\pm$ 0.2) $\times$ 10$^8$ $M_{\odot}$ (Region 6)"]
- result: Mach number Overlap vs eastern nucleus = ~5 vs ~2 ± not stated dimensionless [5.3: "(${\mathcal M}$ $\sim$ 5 and $\bar{n}$ $\sim$ 10$^{4.0}$ cm$^{-3}$) relative to the eastern nucleus (${\mathcal M}$ $\sim$ 2"]
- result: Dynamical mass E0 = 9.3e7 ± not stated Msun [3.2: "$M_{\rm dyn}$ of 9.3 $\times$ 10$^7$ $M_{\odot}$ assuming the inclination of 90$^\circ$"]
- limitation (authors): Possible synchrotron contamination of 110 GHz SFR (~25%); absolute values uncertain due to conversion factors [5.3: "The absolute values are uncertain because of the assumed conversion factors to derive the surface densities and the assigned SFR tracer."]
- not stated (card): Line-free channel ranges for continuum subtraction per spw; Which dataset uses natural vs briggs beyond Table 1, and image/cell sizes; Clean thresholds, masks, deconvolver; Flux-integration method for apertures and uncertainty treatment; Fitting method for slopes and rotation diagrams (regression, error weighting); Mach number/density grid ranges for turbulence model; Details of Sigma_SFR and Sig…

### 2025A&A...698A.204H: An ALMA spectroscopic survey of the Planck high-redshift object PLCK G073.4−57.5 confirms two protoclusters (2025; high_z_galaxies, star_formation; observational_alma_primary)
- question: What is the redshift distribution of the galaxies in the Planck-selected field G073, are the two suspected structures (z~1.5 and z~2) real protoclusters, and what are their gas and star-formation properties?
- step 5: Derive stellar mass and SFR
  - method: CIGALE SED fitting (delayed SFH with burst, BC03, Draine14 dust, Calzetti attenuation, solar metallicity); SFR_IR from cmcirsed modified blackbody with Kennicutt&Evans relation [4.1 Stellar masses and star-formation r…: "we assumed a delayed star-formation history with an optional burst, a (cite: chabrier03) IMF, the stellar population models of (cite: bruzual03), the dust models from (cite: draine14), the (cite: calzetti00) attenuation law, and solar metallicity"]
  - software: CIGALE, cmcirsed
  - parameter: beta = 1.8, dust temperature free [4.1 Stellar masses and star-formation r…: "assuming the CO-derived redshift and a dust emissivity-index $\beta$ equal to 1.8 (cite: cortese14; pokhrel16), leaving the dust temperatures as free parameters."]
  - assumption: Chabrier IMF; SFR_IR = 1.40e-10 L_IR [4.1 Stellar masses and star-formation r…: "${\rm SFR_{\rm IR}}\,=\,1.40\times 10^{-10}\times L_{\rm IR}$"]
  - fitting: chi2 best fit; parameters are likelihood-weighted means and standard deviations [4.1 Stellar masses and star-formation r…: "The best-fit is assessed through $\chi^2$, and the best-fit parameters and associated uncertainties are estimated as the likelihood-weighted means and standard deviations."]
  - validation: Compared with Kneissl+19 SFRs and CIGALE with cmcirsed dust model [4.1 Stellar masses and star-formation r…: "However, the differences were within the uncertainties."]
- step 7: Compare gas properties to field and cluster samples and to TNG300
  - method: Compute depletion time and gas-to-stellar ratio, MS offsets (Popesso+23), scaling relations of Liu+19 and Sargent+14, update Gouin+22 simulation comparison with spectroscopic redshifts [5.2 Depletion timescales: "We corrected all the gas mass estimates from this literature cluster sample to have the same $\alpha_{\rm CO}$ conversion factor of 4.36 (when possible)"]
- result: Median depletion time, G073 = 0.7 ± ±0.6 Gyr [5.2 Depletion timescales: "The median depletion times for the G073 sources and for the cluster members are ($0.7\,{\pm}\,0.6$) Gyr and ($0.8\,{\pm}\,1.2$) Gyr, respectively"]
- result: Median gas-to-stellar mass ratio, G073 = 3.5 ± +3.1/-1.6 dimensionless [5.3 Gas-to-stellar mass ratio: "the G073 sample has a median gas-to-stellar mass ratio of $\mu_{\rm gas}\,{=}\,3.5^{+3.1}_{-1.6}$"]
- result: Median gas-to-stellar mass ratio, literature cluster sample = 1.6 ± +2.3/-0.9 dimensionless [5.3 Gas-to-stellar mass ratio: "our comparison sample has a median gas-to-stellar mass ratio of $\mu_{\rm gas}\,{=}\,1.6^{+2.3}_{-0.9}$"]
- result: Average dust temperature = 27 ± ±3 K [4.1 Stellar masses and star-formation r…: "The resulting average dust temperature of the sample was found to be (27$\pm$3) K."]
- result: Halo mass of z=1.5 structure = ≈1e13 ± not stated Msun [6.1 The large-scale structure probed by…: "a total dark matter halo mass of ${\approx}\,1\,{\times}\,10^{13}\,$M$_{\odot}$"]
- result: Halo mass of z=2 structure = ≈4e13 ± not stated Msun [6.1 The large-scale structure probed by…: "a total dark matter halo mass of ${\approx}\,4\,{\times}\,10^{13}\,$M$_{\odot}$"]
- limitation (authors): Gas mass has large systematic uncertainties from alpha_CO, which are ignored; CI excitation not constrained [4.2 Molecular gas masses: "there are large systematic uncertainties involved in estimating the gas mass, which we ignore here for simplicity."]
- limitation (authors): Simulation comparison is only qualitative [6.1 The large-scale structure probed by…: "this comparison only qualitatively illustrates broad agreement."]
- not stated (card): Exact CASA version and pipeline version; Line-free channel ranges used for continuum subtraction per source; LineSeeker S/N threshold settings beyond the negative-peak cutoff and kernel details; Whether Cycle 2 Band 6 data were reprocessed or Kneissl+19 products used; CIGALE module parameter grids and cmcirsed fit details; Exact selection of the comparison literature sample and the corrections ap…

### 2020A&A...635A.119C: Extended Hα over compact far-infrared continuum in dusty submillimeter galaxies. Insights into dust distributions and star-formation rates at z ∼ 2 (2020; high_z_galaxies; multi_facility_alma_minor)
- question: Do the FIR (870 um) continuum and H-alpha have different sizes in z~2 SMGs, and what does this imply for dust attenuation, SFR estimates and SED modeling?
- step 5: Compare H-alpha SFRs with IR SFRs
  - method: hyperz UV-to-NIR fit for A_V; FIR template fitting for L_IR (8-1000 um); Kennicutt & Evans calibrations; attenuation relations from Calzetti and Kashino [4.2.1: "we estimate the star-formation rates based on H$\alpha$ and infrared luminosities by adopting the calibration provided by (cite: Kennicutt:2012aa)"]
  - software: hyperz, magphys
  - parameter: A_V 0-5 in steps of 0.01; Calzetti law; BC03 templates [4.2.1: "We follow the (cite: Calzetti:2000aa) law to allow total attenuation ($A_V$) between 0 to 5 in steps of 0.01."]
  - assumption: Solar metallicity; four SFHs (B, E, Sb, C) [4.2.1: "assuming solar metallicities, with different SFHs"]
  - fitting: chi2 minimisation; A_V values from fits within Delta chi2<1 [4.2.1: "take all the $A_V$ values from fits that have $\Delta\chi^2<1$ from the lowest $\chi^2$"]
  - validation: Reproduced Simpson et al. 2014 hyperz results [4.2.1: "We confirm that we are able to reproduce their results."]
- result: IR SFR / uncorrected H-alpha SFR = 21 ± 15 dimensionless [4.2.1: "on average a factor of $21\pm15$ in median (with bootstrap error) lower than infrared-based SFRs"]
- result: IR SFR / stellar-A_V-corrected H-alpha SFR = 4 ± 2 dimensionless [4.2.1: "but now by a factor of $4\pm2$"]
- result: Remaining discrepancy with Calzetti correction = 3 ± 1 dimensionless [4.2.1: "missing at least a median factor of $3\pm1$"]
- limitation (authors): Small sample (six) with archival heterogeneous IFU data, hard to assess selection bias [2.1: "it is difficult to assess the potential selection biases"]
- not stated (card): Exact CASA versions for the re-reduced older ALMA datasets; Which ALMA execution blocks/MS were used per source; uv-taper values and clean parameters (robust, niter, cell, image size); uvmodelfit starting values; Curve-of-growth plateau radius criteria and aperture steps; Photometry tables for UV-to-NIR SEDs; Details of the Monte Carlo error runs

### 2020ApJ...903..145L: ALMaQUEST. IV. The ALMA-MaNGA QUEnching and STar Formation (ALMaQUEST) Survey (2020; nearby_galaxies; large_program_or_survey)
- question: How does sSFR depend on molecular gas fraction versus star formation efficiency, globally and at kpc scales, in MaNGA galaxies spanning starburst, main-sequence and green valley
- step 2: Derive H2 mass and global quantities
  - method: Sum CO flux, SFR and M* within 1.5 Re (star-forming [SII] BPT spaxels for SFR) and MaNGA bundle; compute sSFR, SFE, fH2 [2.5 Global Measurements: "These integrated quantities are estimated in two ways: 1) By summing up the measured values over the area enclosed by 1.5 $R_{e}$ and 2) by summing over the areas within the MaNGA bundles."]
  - assumption: alpha_CO = 4.35 Msun (K km/s pc^2)^-1; Salpeter IMF [2.5 Global Measurements: "adopting a constant conversion factor ($\alpha_{\mathrm{CO}}$) of 4.35 $\rm M_{\odot}$(K km s$^{-1}$ pc$^{2}$)$^{-1}$ (cite: bol13)"]
  - validation: Repeated with metallicity-dependent alpha_CO (Sun+20; Narayanan+12) and alternative SFR spaxel selections [3.1: "the varying $\alpha_{\mathrm{CO}}$ does not affect any trends in the global results presented in this section."]
- step 3: Correlation of sSFR with SFE, fH2, HI ratios
  - method: Kendall tau correlation analysis [3.1: "The Kendall correlation analysis for the ALMaQUEST sample shows that the correlation between sSFR and SFE ($\tau$ = 0.67) is slightly stronger"]
  - validation: Excluded lowest-SFE point; tau changes 0.67 to 0.66 [3.1: "We find that the $\tau$ value only slightly decreases from 0.67 to 0.66 in this case"]
- step 4: Spaxel-level distributions
  - method: Histograms of sSFR, fH2, SFE on star-forming spaxels per galaxy [3.3: "we plot the histograms of sSFR, $f_{\rm H_{2}}$ and SFE computed on a spaxel-by-spaxel basis for the star-forming spaxels of 46 ALMaQUEST galaxies"]
  - validation: Repeated with varying alpha_CO; offsets <0.14 dex [3.3: "While there is a systematic offset ($<$ 0.14 dex) in the resulted SFE and $f_{\rm H_{2}}$"]
- result: Kendall tau sSFR vs SFE = 0.67 ± not stated dimensionless [3.1: "the correlation between sSFR and SFE ($\tau$ = 0.67)"]
- result: Kendall tau sSFR vs fH2 = 0.54 ± not stated dimensionless [3.1: "that between sSFR and $f_{\rm H_{2}}$ ($\tau$ = 0.54)"]
- result: Kendall tau, all spaxels case = 0.56 ± not stated dimensionless [Appendix: "A moderate correlation ($\tau$ = 0.56) with high significance"]
- result: Kendall tau, [NII] BPT: sSFR-SFE / sSFR-fH2 = 0.78 / 0.49 ± not stated dimensionless [Appendix: "a stronger correlation strength ($\tau$ = 0.78) is found in the sSFR vs. SFE relation, with respect to the sSFR vs. $f_{\rm H_{2}}$ relation ($\tau$ = 0.49)"]
- result: Max difference in global H2 mass with varying alpha_CO = 0.27 dex (mean ~0.05 and ~0.14 dex for methods 1 and 2) ± not stated dex [3.1: "can be as large as 0.27 dex with an average value of $\sim 0.05$ and $\sim 0.14$ dex in method 1 and method 2, respectively"]
- limitation (authors): Small HI sample limits conclusions [3.2: "our results should be taken with caution given that the current ALMaQUEST $\rm H\textsc{i}$ sample size is still limited."]
- not stated (card): Line-free channels and continuum spectral windows used for continuum subtraction; Velocity ranges chosen by hand for moment-0 maps per galaxy; tclean/CLEAN image size, masking, and deconvolver; Exact conversion of CO flux to L'CO and treatment of line brightness (R21 not needed but redshift/distance used); Per-galaxy CASA version assignment beyond three listed; Spaxel S/N cuts for CO in resolved …

### 2014A&A...562A..67G: ALMA reveals a warm and compact starburst around a heavily obscured supermassive black hole at z = 4.75 (2014; high_z_galaxies, agn_and_quasars; observational_alma_primary)
- question: How compact, warm and dusty is the starburst around the Compton-thick QSO XID403 at z=4.75, and can it explain the X-ray obscuration and outflows?
- step 4: Derive L_IR, SFR and SFR surface density
  - method: Integrate best-fit greybody; Kennicutt98 SFR; Sigma_SFR=(SFR/2)/(pi r_half^2) [4 Star formation rate: "By integrating the best-fit modified greybody spectrum we obtained a far-IR (42.5-122.5$\mu$m) luminosity"]
  - assumption: Cosmology H0=67, Om=0.32, OL=0.68; 1 arcsec=6.6 kpc [1 Introduction: "A concordance $\Lambda$CDM cosmology with $H_0=67$ km s$^{-1}$ Mpc$^{-1}$, $\Omega_m=0.32$, $\Omega_{\Lambda}=0.68$"]
  - validation: Agreement with Coppin09 and Gilli11 [Star formation rate and compactness: "These values are in excellent agreement with those previously derived by (cite: coppin09) and (cite: gilli11) and have significantly smaller uncertainties."]
- result: SFR = 1020 ± 150 Msun/yr [Table 2: "| SFR | $1020\pm150$ | $M_{\odot}$yr$^{-1}$ | this work |"]
- result: L_IR (8-1000um) = 5.9e12 ± 0.9e12 Lsun [Table 2: "| $L_{IR}$ | $5.9\pm 0.9$ | $10^{12} L_{\odot}$ | this work |"]
- result: Sigma_SFR lower limit = >26 ± not stated Msun/yr/kpc2 [Table 2: "| $\Sigma_{SFR}$ | $>26$ | $M_{\odot}$yr$^{-1}$kpc$^{-2}$ | this work |"]
- limitation (authors): Size measurement needs confirmation at higher resolution; sparse uv sampling [2 ALMA observations: "this measurement needs to be confirmed by data at even higher resolution"]
- not stated (card): CLEAN parameters (weighting, robust, cell, size, masking); Flagging details and phase-calibrator solutions; Exact fit setup for uvmodelfit (starting values); Parameters of the SED decomposition fit beyond qualitative description; Photometry in the CANDELS fit and SPIRE 250um flux (Daddi et al. in prep)

### 2025ApJ...995..151Y: Molecular Gas and Star Formation in Dwarf Galaxies Observed by the Atacama Large Millimeter/submillimeter Array (2025; nearby_galaxies; archival_reuse)
- question: Do dwarf galaxies follow the molecular star formation law of massive spirals, and is their star formation regulated by gravitational stability (Toomre Q)?
- step 3: Derive surface density maps
  - method: Sigma_H2 from I_CO; Sigma_SFR from NUV+12um; Sigma_star from 3.4/3.6um [3.1 Radial Distributions: "The H$_2$ surface mass density was derived from the intensity of CO ($I_{\rm CO}$) using the standard Galactic CO-to-H$_2$ conversion factor"]
  - parameter: cos i correction; helium factor 1.36 [3.1 Radial Distributions: "where the factor of 1.36 accounts for the helium correction."]
  - assumption: X_CO = 2e20 cm^-2 [K km/s]^-1; alpha_CO = 4.35 [3.1 Radial Distributions: "The adopted conversion factor $X_{\rm CO}$ corresponds to $\alpha_{\rm CO} = 4.35\ M_\odot\ \rm pc^{-2}\ [K \,\mbox{km~s$^{-1}$}]^{-1}$, including the helium correction."]
  - assumption: Constant mass-to-light ratio 0.35 Msun/Lsun [3.1 Radial Distributions: "assuming a constant mass-to-light ratio of $\Upsilon_\star^{3.4}= 0.35\ \mbox{$M_\odot$}L_{\odot}^{-1}$"]
- step 5: Fit molecular SFL and SFE
  - method: Least-squares power-law fit of Sigma_SFR vs Sigma_H2 per galaxy; SFE = Sigma_SFR/Sigma_H2 [3.2 Molecular SFL: "we performed least-squares fits for each galaxy"]
  - fitting: Least squares, no priors [3.2 Molecular SFL: "we performed least-squares fits for each galaxy"]
  - validation: Tested with 1 sigma CO points and radially varying alpha_CO [3.2 Molecular SFL: "we included additional data points down to the $1\sigma$ level of the CO intensity"]
- result: Mean molecular SFL slope, all six = 0.81 ± 0.18 dimensionless [3.2 Molecular SFL: "The resulting power-law indices range from 0.62 to 1.08, with a mean slope of N = 0.81$\pm$0.18."]
- result: Mean slope, four galaxies with 3+ points = 0.87 ± 0.05 dimensionless [3.2 Molecular SFL: "yields a mean slope of N = 0.87$\pm$0.05"]
- result: Mean slope including 1 sigma points = 0.73 ± 0.05 dimensionless [3.2 Molecular SFL: "yielding an average index of N$=0.73\pm 0.05$"]
- result: SFE_H2 range = 0.9 to 4.1 ± not stated Gyr^-1 [3.2 Molecular SFL: "the SFE$_{\rm H_2}$ values range from 0.9 Gyr$^{-1}$ to 4.1 Gyr$^{-1}$"]
- limitation (authors): Constant Galactic alpha_CO adds systematic uncertainty; no resolved metallicity [3.2 Molecular SFL: "We note that the adopted $\alpha_{\rm CO}$ introduces an additional systematic uncertainty."]
- limitation (authors): Two galaxies have slopes from only two CO data points [3.2 Molecular SFL: "the slope estimates rely on only two central data points where CO is significantly detected"]
- not stated (card): Spectral setup and observing details (dates, configurations, time on source); Imaging cell size, image size, channel width, clean threshold, masks; Line-free channels and whether continuum was subtracted; Moment map generation method; Radial profile center and exact annulus handling, and how fits were done (weighting); Rotation curve values used for kappa; How the 7.5'' convolution kernel was set…

### 2018A&A...615A..94F: Fragmentation properties of massive protocluster gas clumps: an ALMA study (2018; star_formation; observational_alma_primary)
- question: What regulates fragmentation (magnetic field vs turbulence) in massive, young protocluster clumps, as probed by the fragment population in 278 GHz continuum and compared with MHD simulations?
- step 4: Correlate fragment and clump properties
  - method: Compare number, masses, separations with clump T, mass, sigma_nth, Mach number, SFE [5.1: "We have searched for possible relations between the properties of the fragment population in Table [\[tab_averages\]](#tab_averages), and the physical parameters of the parent clumps"]
  - validation: Only qualitative; authors note need for higher statistics [5.1: "all the conclusions drawn in this Section should be corroborated by a higher statistics"]
- step 5: Compare with MHD simulations
  - method: RAMSES runs with mu=2 and 200 (130), converted via RADMC-3D to dust continuum, CASA-simulated, same fragment criteria [5.3: "we have calculated the properties of the fragments using the same criteria adopted for the real images"]
  - software: RAMSES, RADMC-3D, CASA
  - assumption: Distance 3.6 kpc; spherical clump with density contrast 10; stopped at SFE 15% [5.2: "we have decided to analyse the simulations stopped at a SFE of $15\%$"]
  - validation: Qualitative morphology comparison [5.2: "our main aim is to compare the overall morphology of the real and synthetic images"]
- limitation (authors): Fragment numbers are lower limits due to large missing flux and pointing offsets [Conclusions: "The number of fragments is likely a lower limit given the huge amount of missing flux in most of the sources."]
- limitation (authors): Mass estimates are likely upper limits for warm fragments; simulations use single spherical clumps [4.1: "In these cases, our mass estimates are likely upper limits."]
- not stated (card): CASA version and whether the pipeline or manual calibration was used; Weighting/robust, cell and image size, deconvolver and masks; Line-free channels and spectral setup; Dust opacity law value and frequency scaling (only referenced to Fontani 2016); Noise rms per map; Self-calibration usage; Exact GILDAS MAPPING procedure for fragment flux integration

### 2015ApJ...813..118M: Microwave Continuum Emission and Dense Gas Tracers in NGC 3627: Combining Jansky VLA and ALMA Observations (2015; nearby_galaxies, star_formation; observational_alma_primary)
- question: How do free-free continuum (33 and 94.5 GHz) and dense gas tracers (HCN, HCO+ J=1-0) compare on ~90 pc scales in three regions of NGC 3627, and how do dense gas fraction and star formation efficiency relate?
- step 4: Dense gas fraction and SFE
  - method: Convolve to CO beam, take peak in 15 arcsec aperture; dense gas mass from HCO+ / total from CO; SFR from 33 GHz thermal luminosity [3.3 Dense Gas Fractions: "The dense molecular gas fraction is taken to be the mass ratio of dense molecular gas traced by the $J=1\rightarrow0$ transition of HCO$^{+}$ to the total molecular gas"]
  - software: CASA
  - assumption: alpha_HCO+ ≈ 10, alpha_CO ≈ 4.3 Msun/(K km/s pc^2); mean 33 GHz thermal fraction 79% [3.3 Dense Gas Fractions: "$\alpha_{\rm CO} \approx 4.3$ M${_\odot}\,{\rm (K\,km\,s^{-1}\,pc^{2})}^{-1}$"]
  - validation: Trend persists if HCN used for dense gas mass [3.3 Dense Gas Fractions: "the trend observed in the top panel of Figure [5](#fig:dgas) would persist even if we instead used the HCN-derived dense gas mass"]
- limitation (authors): Only three regions; nuclear HCN cut off by bandpass; single-component fit poor for Enuc. 2 [2.5 Line Imaging and Photometry: "the detection of HCN towards the nucleus is cut off by the bandpass at a radial velocity of $v_\mathrm{LSRK} \approx 800\mathrm{\,km\,s^{-1}}$"]
- not stated (card): Line-free channels for uvcontsub; ALMA array configuration, baselines, and time on source; CASA version; Image size and cell size; Clean masks and thresholds; Velocity ranges for moment 0 integration; SFR calibration formula and how L33 converts to SFR; Monte Carlo details for velocity dispersion errors; Unit conversion from Jy/beam to K km/s for HCO+, HCN, CO

### 2019ApJ...887...74F: ALMA Reveals a Gas-rich, Maximum Starburst in the Hyperluminous, Dust-obscured Quasar W0533-3401 at z ∼ 2.9 (2019; agn_and_quasars, high_z_galaxies; observational_alma_primary)
- question: What are the molecular gas, dust, stellar and SMBH properties of the hyperluminous obscured quasar W0533-3401, and is it a gas-rich maximum starburst in a transition phase toward an unobscured quasar?
- step 5: Dust mass, gas-to-dust ratio, SFR, depletion time, BH properties
  - method: Optically thin M_dust equation; f_gas, SFR from SED and from CO(5-4)-FIR relation; t_depl = M_gas/SFR; M_BH from L_AGN with Eddington ratio 1; Mdot_BH from L_AGN with eta/(1-eta)=0.1 [4.4 Rapid growth of both the stellar co…: "adopting $\frac{\eta}{1-\eta}=0.1$"]
  - assumption: kappa_1THz=20 cm2/g; lambda_Edd=1; L'CO(5-4)/L'CO(3-2)=0.7 [4.3 Stellar mass and star formation rate: "by taking $L'_{\rm CO(5-4)}/L'_{\rm CO(3-2)}=0.7$"]
  - validation: CO-based SFR consistent with SED SFR [4.3 Stellar mass and star formation rate: "which is generally consistent with the best-fit SED result"]
- result: Dust mass = 8.9e7 ± 1.6e7 Msun [Table 4: "| $M_{\rm dust}$ | (8.9 $\pm$ 1.6) $\times 10^{7}$ | $M_\odot$ | \(11\) |"]
- result: Gas-to-dust ratio = 944 ± 77 dimensionless [4.2 Dust properties: "$\delta_{\rm GDR} = 944\pm77$"]
- result: Gas fraction = 0.71 ± not stated dimensionless [4.3 Stellar mass and star formation rate: "$f_{\rm gas}=M_{\rm H_2}/(M_{\rm H_2}+M_\star)=0.71$"]
- result: Gas depletion time = 12-28 ± not stated Myr [4.3 Stellar mass and star formation rate: "We infer $t_{\rm depl}\sim 12-28$ Myr"]
- result: BH mass growth rate = 49 ± not stated Msun/yr [4.4 Rapid growth of both the stellar co…: "We infer ${\dot{M}}_{\rm BH}$ = 49 $M_\odot$ yr$^{-1}$"]
- result: M_BH/M_star (lambda_Edd=1) = 0.063 ± not stated dimensionless [4.4 Rapid growth of both the stellar co…: "($M_{\rm BH}/M_\star=0.063$)"]
- limitation (authors): Limited depth and resolution prevent distinguishing disk, merger and outflow [4.1 CO(3-2) line emission: "due to limited depth and resolution, we cannot make a solid conclusion"]
- limitation (authors): Dust mass depends strongly on the adopted kappa [4.2 Dust properties: "the largest uncertainty can arise from the adopted $\kappa_{\nu_{\rm rest}}$ value"]
- not stated (card): tclean parameters: cell size, image size, deconvolver, threshold, masking, niter; line-free channels and continuum subtraction method; CASA version and pipeline version; moment-map thresholds and aperture used for line flux and spectrum extraction; 3DBarolo settings beyond rings and width (free parameters, normalization, fit mask); bayesed sampler and likelihood details (forthcoming version not p…

### 2018ApJ...863..193V: Molecular Gas Filaments and Star-forming Knots Beneath an X-Ray Cavity in RXC J1504-0248 (2018; galaxy_clusters_and_sz, nearby_galaxies, star_formation; observational_alma_primary)
- question: What are the mass, morphology, kinematics, origin and star formation of the molecular gas in the RXCJ1504 BCG, and how does it relate to an X-ray cavity?
- step 7: Compute local SFRs from HST FUV and fit star formation law
  - method: FUV count rates in regions scaled to global SFR; fit Sigma_SFR = A (Sigma_H2/100)^N in log space [4.3 Star Formation Along the Filament: "Thus the SFR within each region is the ratio of its UV count rate to the total UV count rate multiplied by the global SFR."]
  - software: linmix
  - assumption: SFR uncertainty factor of two; Salim07 UV calibration (Chabrier IMF) [4.3 Star Formation Along the Filament: "Throughout this work we take the SFR uncertainty to be a factor of two"]
  - fitting: Bayesian linear regression (Kelly 2007) via linmix [4.3 Star Formation Along the Filament: "The fits were conducted in log space using the linmix package in Python, which employs the Bayesian approach to linear regression described in (cite: Kelly07)."]
  - validation: Compared with KS and Bigiel08 relations [4.3 Star Formation Along the Filament: "The linear scaling measured between $\Sigma_{\rm SFR}$ and $\Sigma_{{\rm H}_2}$ in spiral galaxies (cite: Bigiel08) has also been plotted in Fig."]
- result: Star formation law fit, all gas: A and N = A=0.58, N=0.64 ± A ±0.11, N ±0.18 dimensionless [4.3 Star Formation Along the Filament: "Fitting this SF law to the entire gas distribution yields $A=0.58\pm0.11$ and $N=0.64\pm0.18$."]
- result: Star formation law fit, central gas: A and N = A=0.23, N=1.18 ± A ±0.13, N ±0.37 dimensionless [4.3 Star Formation Along the Filament: "gives $A=0.23\pm0.13$ and $N=1.18\pm0.37$"]
- result: Gas consumption time = 1.4e8 ± not stated yr [4.3 Star Formation Along the Filament: "will be consumed in $1.4\ensuremath{\times 10^{8}}\rm\; yr$."]
- limitation (authors): The cavity is poorly defined and may not be real [4.1 Gas Origin: "The feature identified as a potential cavity is poorly defined, so it is not clear if it is a real cavity."]
- limitation (authors): HST images manually aligned, so small-scale offsets between gas and UV may be missed [3.5 Spatial Correlation with UV Emission: "Spatial offsets between the molecular gas and young stars could be present, but would be missed due to this manual alignment."]
- not stated (card): Line-free channels and continuum-subtraction order for uvcontsub; Clean masks, threshold, niter, cell and image size; Self-calibration solution intervals; Exact HST data sets and pipeline products, and manual shifts beyond those quoted; Regions (polygon and extraction boxes) definitions for spectra and SFR; Flux calibrator and flux scale uncertainty; Extraction details of the Chandra surface brig…

### 2015ApJ...813...45L: Radio Jet Feedback and Star Formation in Heavily Obscured, Hyperluminous Quasars at Redshifts ∼ 0.5-3. I. ALMA Observations (2015; agn_and_quasars, high_z_galaxies; observational_alma_primary)
- question: How much cool dust emission / star formation accompanies highly obscured, radio-powerful WISE-selected quasars at z~0.5-3, as measured with ALMA 870 um snapshot photometry?
- step 3: Fit SEDs (AGN torus + modified blackbody + stellar) and derive SFRs
  - method: parametric AGN MIR component plus greybody at fixed T=30,50,90,120 K, beta=1.5 (2 for 50 K); SFR from Kennicutt conversion [5.2.2 Three-Component SED Fits: "We have made four fits to each source, each with a different temperature for the BB component."]
  - parameter: beta=1.5; 50K model beta=2 [5.2.2 Three-Component SED Fits: "For $\beta$ we have selected a value of 1.5"]
  - assumption: z=2 for sources without redshift [5.2.2 Three-Component SED Fits: "For the four sources without measured redshift we assume $z = 2$."]
  - validation: free-Td fits for two Herschel sources set 90 K and 120 K [5.2.2 Three-Component SED Fits: "we have adopted the two dust temperature values which have fitted W1500-0649 and W2059-3541 successfully: 90 K (rounding up from 89 K) and 120 K"]
- result: SFR range from BB fits (detected) = 13.5-25700 ± not stated Msun/yr [5.2.2 Three-Component SED Fits: "the corresponding SFR range is 13.5–25700 $M_{\odot}$ ${\rm yr}^{-1}$"]
- limitation (authors): Dust temperature unconstrained for most sources; L_BB and SFR uncertain by orders of magnitude [5.2 Spectral Energy Distribution Fits: "is uncertain by 2-3 dex without measurements at the FIR peak of the dust SED."]
- not stated (card): CASA version and calibration/imaging procedure (pipeline vs manual, weighting, cleaning); Region used for imfit and how upper limits were set (3 sigma assumed?); Rest-frame Gamma_RJ/Gamma_0 values and temperature-scaled constant for 30 K and 90 K ISM masses; Fitting code and parameter priors for the AGN+BB+stellar fits; photometry weighting; Redshift-tied details of k-correction templates

### 2025A&A...700A.285W: Gravitational torques from lopsided young stellar component sustain high black hole accretion rates in NGC 4593 (2025; agn_and_quasars, nearby_galaxies; observational_alma_primary)
- question: What secular mechanism drives high SMBH accretion rates in NGC 4593, from kpc-scale gas down to the SMBH sphere of influence?
- step 4: Depletion time along spiral
  - method: Parametrize spiral with polynomial, extract Sigma_mol and Sigma_SFR in 200 pc apertures on 100 pc grid, compute t_dep [3.4 Star formation along the single-arm…: "Along this spiral path, we extract $\Sigma_{\rm mol}$ and $\Sigma_{\rm SFR}$ in 200 pc-wide apertures"]
  - parameter: a=0.04, b=-0.93, theta in [0,3pi] [3.4 Star formation along the single-arm…: "$a=0.04$, $b=-0.93$ are best-fitting parameters over the range $\theta = [0,3\pi]$"]
  - validation: Trends robust to resolution 100–300 pc and aperture 100–400 pc [3.4 Star formation along the single-arm…: "across aperture widths ranging from 100 to 400 pc"]
- result: Median molecular gas depletion time along spiral = 3.9 ± 0.6 Gyr [3.4 Star formation along the single-arm…: "$\langle t^{\rm mol}_{\rm dep} \rangle = 3.9 \pm 0.6\,$ Gyr"]
- limitation (authors): Torque method unvalidated by simulations, configuration likely unstable [3.7.2 Torques from the young stellar co…: "First, the configuration is likely unstable over time."]
- limitation (authors): Mass of young component is poorly constrained from single UV band; closed-box and alpha_CO assumptions [3.6.2 Mass of the young stellar compone…: "Thus, we were limited to a flux measurement in the F330W filter."]
- not stated (card): CASA tclean parameters (cell, image size, mask, niter, threshold), line-free channels, and rest frequency; ALMA calibration/pipeline version and flux calibrator details for both programs; Whether CASA was used for the joint imaging of the combined cube; KinMS_fitter prior ranges, number of walkers and burn-in; skySampler settings; Aperture and masks used to measure total CO flux and M_mol; Spiral…

### 2020A&A...635A...2S: Physical properties of the star-forming clusters in NGC 6334. A study of the continuum dust emission with ALMA (2020; star_formation, milky_way_ism; observational_alma_primary)
- question: What are the core mass function, spatial distribution of cores and mass segregation in the star-forming clusters of NGC 6334, and how do they relate to cluster evolutionary stage and fragmentation physics?
- step 6: Mass segregation
  - method: Three approaches: MST of low/high mass (20 Msun), radial mass distribution, and mass segregation ratio with 500 random clusters [5.2 Mass segregation: "We used 500 randomly generated uniform clusters for a good determination of $\langle l_\mathrm{random}\rangle$."]
  - software: NetworkX
  - assumption: Star formation efficiency 30%, so 20 Msun core forms B-type star [5.2 Mass segregation: "Assuming a star formation efficiency of 30%, a compact source with a mass of $\sim$20 $M_\odot$ ends up with forming a B-type star"]
  - validation: Gaussian-cluster test of Lambda_MSR vs concentration [10 Correlation between the mass segrega…: "For each value of $\sigma$, we generate 50 Gaussian clusters containing 70 cores each."]
- result: Lambda_MSR NGC 6334-I = 3.60 ± not stated dimensionless [Table of cluster properties: "| NGC 6334-I | 14 | 3 | 23 | 4.0$\times$10$^{5}$ | 1.0 | 20 | $-$0.71 | 3.60 |"]
- limitation (authors): Temperatures assumed rather than measured; unresolved multiplicity biases CMF [5.1 Core mass function: "the measured slope can be biased due to the uncertainty in temperature determination and the unresolved multiplicity in the massive cores."]
- limitation (authors): Low number statistics limit Q-parameter conclusions [4.2 Spatial structure of the clusters i…: "the total number of sources in that cluster (10) limits the conclusions that can be derived from this analysis."]
- not stated (card): Line-free channel ranges used for continuum; tclean multiscale scales, image size, masking and threshold; Self-calibration solution intervals; SExtractor parameters beyond thresholds (filter, mesh size); Hyperparameters of the seven scikit-learn clustering algorithms; How the SExtractor flux was corrected for ACA/combined images and which image (super-resolution vs combined) was used for the cata…

### 2020ApJS..251...14H: CMZoom. II. Catalog of Compact Submillimeter Dust Continuum Sources in the Milky Way's Central Molecular Zone (2020; milky_way_ism, star_formation; multi_facility_alma_minor)
- question: Which compact sources (<10'', ~0.4 pc) exist in the 1.3 mm SMA CMZoom continuum maps of the Central Molecular Zone, what are their properties and completeness, and what do they imply for CMZ star formation potential?
- step 5: Maximum SFR potential and missed massive-star precursors
  - method: Sum eps*m/tff over leaves; IMF sampling (Kroupa) weighted by 1-P(m) for missing massive precursors [5.3 High-Mass Star Precursor Completene…: "We then average the number of massive ($\geq 8$ M$_\odot$) stars for 1000 iterations of each leaf mass bin."]
  - parameter: SFE 0.1-0.75 [5.3 High-Mass Star Precursor Completene…: "a star formation efficiencies ranging between 0.1-0.75"]
  - assumption: each leaf collapses on a freefall time [5.2 Maximum Star Formation Potential of…: "assuming each compact source in our catalog collapses on a freefall time and forms stars with an assumed star formation efficiency"]
- result: Maximum SFR potential CMZ = 0.08 - 2.20 ± not stated Msun/yr [5.2 Maximum Star Formation Potential of…: "the maximum star formation potential of the CMZ is between 0.08 - 2.20M$_\odot$ yr$^{-1}$"]
- result: Maximum SFR potential excluding Sgr B2 = 0.04 - 0.47 ± not stated Msun/yr [5.2 Maximum Star Formation Potential of…: "or, excluding Sgr B2, between 0.04 - 0.47M$_\odot$ yr$^{-1}$"]
- result: Missed massive-star precursors = <~1% ± not stated percent [5.3 High-Mass Star Precursor Completene…: "which we find to be $\lessapprox1$% (if we assume a star formation efficiency of 0.75)"]
- limitation (authors): Completeness assumes point sources and does not capture extended emission; masses uncertain by factor ~2 [3.2 Source Recovery and Simulated Obser…: "These mass completeness estimates account only for the observational biases in observing point-source-like emission"]
- not stated (card): Exact dendrogram parameter values in the appendix-referenced setup (min_value, min_npix, min_delta numeric values beyond 3 MJy/sr scaling); Access/processing of CMZoom SMA maps from Dataverse versus Paper I imaging details; Simulated observation antenna configuration, integration time and weather settings; Herschel temperature map not yet published (in prep.); Exact point-source flux values and m…

### 2015MNRAS.449..715W: Tracing the conversion of gas into stars in Young Massive Cluster Progenitors (2015; milky_way_ism, star_formation; multi_facility_alma_minor)
- question: Are four extreme quiescent Galactic centre clouds gravitationally bound YMC progenitors, and is their gas distribution compact enough to form an Arches-like cluster?
- step 4: Mass surface density profiles and comparison with Sgr B2 and Arches
  - method: Enclosed mass in circular apertures; BGPS fluxes converted to mass with Kauffmann et al. relation at 20 K; stellar mass from UCHII OB stars with Kroupa IMF correction; SFE factor 1/3 [Discussion: "The dust temperature is assumed to be 20 K"]
  - parameter: k_nu = 0.04 cm2 g-1 (nu/505 GHz)^1.75 [Discussion: "k_{\nu} = 0.04 \rm ~ cm^{2} ~ g^{-1} \left(\frac{\nu}{505 ~ GHz}\right)^{1.75}"]
  - assumption: gas-to-dust ratio 100 [Discussion: "Note that this contains the explicit assumption that the gas-to-dust ratio is 100."]
- result: Total stellar mass in Sgr B2 from 25 UCHII sources = ~3.5e3 ± not stated Msun [Discussion: "Taking all 25 sources in (cite: Gaume), we estimate a total stellar mass of $\sim$ 3.5 x 10$^{3}$ M$_{\odot}$."]
- limitation (authors): Mass estimates uncertain due to cloud boundary definition and a factor ~2 systematics; gas temperature measured only for G0.253 [Dust Mass: "We note that these mass estimates are necessarily uncertain due to the ambiguity involved in defining a distinct cloud area"]
- not stated (card): Coefficient k in the virial mass formula; ALMA calibration, imaging and feathering details (deferred to Rathborne et al. 2014b); Hanning smoothing and CASA fit procedure details for spectra; How cloud boundaries were drawn on the column-density maps; Aperture centres and radial bins for profiles

### 2015MNRAS.448.2224C: Constraining globular cluster formation through studies of young massive clusters - V. ALMA observations of clusters in the Antennae (2015; star_formation, nearby_galaxies; archival_reuse)
- question: Do young massive clusters in the Antennae (50-200 Myr) contain the large molecular gas reservoirs required by AGB-type multiple-population GC formation scenarios?
- step 4: Toy model of expected gas mass in AGB scenario
  - method: Compute 2G mass from 1:1 ratio and SFE=1/3, divide gas over 50 Myr window with SF timescale [Toy model: "if we adopt a standard star-formation efficiency for this cluster of SFE=$1/3$ (e.g. (cite: Lada:2003p2573)), this means that M$_{gas}^{\text{2G}}=7.5\times10^5$ M$_{\odot}$"]
  - assumption: current mass ~4x the mass at 10 Gyr; 1:1 1G:2G [Toy model: "assume that the current mass of the cluster is $\sim4$ times more massive than it will be in $\sim10$ Gyr"]
  - validation: Agrees with D08 for Δt_SF = 0.6 Myr [Summary of the toy model and comparison…: "a good agreement is achieved between D08 model and our “toy model", if one adopts a relatively short $\Delta t^{\text{2G}}_{SF}$ of 0.6 Myr."]
- limitation (authors): Upper limits depend on X_CO, which may be overestimated by up to an order of magnitude [Conclusions: "We note, however, that the adopted $X_\text{CO}$ may be overestimated by up to an order of magnitude"]
- not stated (card): Calibration, CASA version and imaging parameters (all deferred to Whitmore et al. 2014); How the spectrum rms was measured (channel range, line-free channels); Configuration, time on source, sensitivity; Details of binning to 10/20 km/s

### 2015ApJ...809...93D: Observational Signatures of Planets in Protoplanetary Disks I. Gaps Opened by Single and Multiple Young Planets in Disks (2015; protoplanetary_disks; theory_or_simulation_compared_to_alma)
- question: Are gaps opened by one or several planets in protoplanetary disks broadly consistent with observed gaps/cavities in transitional disks at NIR and mm wavelengths?
- step 1: 2D two-fluid hydro simulations
  - method: FARGO with dust fluid, planets on fixed circular orbits, no accretion, alpha=0.001, 256x256 cells, 1-500 AU [2.1 Hydrodynamical Gas+Dust Simulations: "The simulations have 256 grid cells in both radial (1-500 AU) and azimuthal ($2\pi$) directions."]
  - software: FARGO
  - parameter: 1 mm particles; initial dust-to-gas 0.9%; T = 221 (r/AU)^-1/2 K; 1 Msun star [2.1 Hydrodynamical Gas+Dust Simulations: "We further assume a radial temperature distribution $T = 221 (r/{\rm AU})^{-1/2}$ K"]
  - assumption: Schmidt number Sc=1; Epstein drag; no dust feedback [2.1 Hydrodynamical Gas+Dust Simulations: "No feedback from the dust on the gas is considered since gas-to-dust mass ratio is always much larger than 1 in our simulations."]
- result: Big-grain gap density contrast, models with Mp>=1MJ = >~1e9 ± lower limit (hard floor) dimensionless [Table 2: "$\gtrsim10^9$"]
- not stated (card): Whitney MCRT code version and input parameter files; Hydro floor value for big-grain surface density; Stellar luminosity; Inclined-image azimuthal averaging details

### 2017MNRAS.469.4683C: ALMA constraints on star-forming gas in a prototypical z = 1.5 clumpy galaxy: the dearth of CO(5-4) emission from UV-bright clumps (2017; high_z_galaxies; observational_alma_primary)
- question: Do UV-bright star-forming clumps in a z=1.5 main-sequence galaxy show CO(5-4) emission, and what does the resolved CO(5-4) distribution imply for gas content and star formation efficiency?
- step 5: Fit IR SED and derive L_IR, SFR, dust and gas mass
  - method: Draine & Li fit to IR+radio photometry including ALMA 1300 um; gas from dust mass via metallicity-dependent gas-to-dust ratio [2.2 Integrated stellar mass and star fo…: "fitting the IR (3.6$\mu$m to 350$\mu$m) and radio photometry of UDF6462 with the (cite: Draine_Li_2007) models"]
  - assumption: delta_GDR ~ 120 from 12+log(O/H)=8.53; Kennicutt 1998 L_IR-SFR, Chabrier IMF [5.3.1 Gas mass from sub-mm continuum: "We find a ratio $\delta_{\rm GDR}$ $\simeq$ 120 for UDF6462."]
  - validation: Other SED codes and templates give results within ~0.1 dex [2.2 Integrated stellar mass and star fo…: "Very similar results (within $\sim$ 0.1 dex) are obtained when fitting the SED using other commonly used codes"]
- step 7: Convert CO(5-4) to molecular gas mass and compute SFE and gas fractions
  - method: L'CO(5-4) converted with R51 and alpha_CO; average of MS and SB assumptions for nucleus; simulation-motivated R51=0.6 and alpha_CO=2.9 for clumps [5.3.2 Molecular gas mass from CO(5-4) e…: "The average of these two estimates yield a molecular gas mass equal to $M_{\rm mol, nuc}$ = $(1.9\pm1.6)\times 10^{10}\mbox{$M_{\odot}$}$"]
  - assumption: MS: R51=0.23, alpha_CO=4.87; SB: R51=0.6, alpha_CO=1 [5.3.2 Molecular gas mass from CO(5-4) e…: "For the SB case, we instead used $\alpha_{\rm CO}$ = 1 and an excitation correction equal to $R_{51}$ = 0.6"]
  - validation: Range of R51 and alpha_CO explored [5.3.2 Molecular gas mass from CO(5-4) e…: "we carry out the calculation of $M_{\rm mol}$ for a range of plausible values for $R_{51}$ and $\alpha_{\rm CO}$"]
- result: Galaxy L_IR = 33e10 ± 9e10 Lsun [2.2 Integrated stellar mass and star fo…: "$L_{\rm IR}$= (33$\pm$9)$\times10^{10}\mbox{$L_{\odot}$}$"]
- result: Galaxy gas mass from SED = 2.0e10 ± +4.4/-1.4 e10 Msun [5.3.1 Gas mass from sub-mm continuum: "$M_{\rm gas, gal}$ = $2.0^{+4.4}_{-1.4}\times 10^{10}\mbox{$M_{\odot}$}$"]
- result: Galaxy depletion time = 0.51 ± not stated Gyr [5.3.1 Gas mass from sub-mm continuum: "a depletion time-scale $\tau_{\rm depl, gal}$ = 0.51 Gyr"]
- result: Nuclear molecular gas mass from CO = 1.9e10 ± 1.6e10 Msun [5.3.2 Molecular gas mass from CO(5-4) e…: "$M_{\rm mol, nuc}$ = $(1.9\pm1.6)\times 10^{10}\mbox{$M_{\odot}$}$"]
- result: Average clump gas mass from stack = 2e8 ± range 1-6e8 Msun [5.3.2 Molecular gas mass from CO(5-4) e…: "average clump gas mass of $M_{\rm mol, cl}$ $\simeq$ $2\times 10^{8}\mbox{$M_{\odot}$}$"]
- result: Average clump gas fraction from stack = ~30% (20-60%) ± not stated dimensionless [5.3.2 Molecular gas mass from CO(5-4) e…: "gas fraction of $f_{\rm gas, cl}$ $\simeq$ 30% (20-60%)"]
- limitation (authors): Clump SFRs vary by up to ~1 dex between methods and clump R51/alpha_CO are poorly constrained [6.1 Scaling relations for giant clumps: "the SFR estimates for individual clumps can vary by up to $\sim$1 dex"]
- not stated (card): Per-execution calibrators and CASA/pipeline version; Channel/velocity range used for continuum and line-free channels; Number of pixels, cell size and clean parameters for GILDAS maps; Exact UV_FIT initial guesses and fixed parameters per clump; Details of simobserve configuration and noise model; Wang et al. in preparation 500 um photometry; Flux calibrators and ALMA flux scale uncertainty

### 2019MNRAS.485.1595P: Multiphase circumgalactic medium probed with MUSE and ALMA (2019; nearby_galaxies, milky_way_ism; observational_alma_primary)
- question: What galaxies (stellar and molecular gas) are associated with the strong HI absorber at z=0.313 toward Q1130-1449, and is the absorption linked to a single galaxy or a group/CGM structure?
- step 3: Derive CO luminosity, molecular mass and depletion time
  - method: Integrate CO spectra; L_CO from Solomon formula; Mmol as function of alpha_CO; tau_depl = M_H2/SFR with alpha_CO=4.6 [3.2 Physical Properties of the Galaxy G…: "We calculated the molecular depletion times for the three objects detected with ALMA following: $\tau_{\rm depl}$=M$_{H2}$/SFR=1/SFE"]
  - software: CASA
  - assumption: Galactic alpha_CO=4.6 Msun (K km/s pc^2)^-1 for depletion times [3.2 Physical Properties of the Galaxy G…: "we assumed a Galactic CO-H$_2$ conversion factor of $\alpha_{\rm CO}$=4.6 M$_{\odot}$ (K km/s pc$^2$)$^{-1}$"]
- step 4: MUSE line fluxes, SFR and metallicity
  - method: Gaussian fits to nebular lines, Balmer-decrement dust correction, Kennicutt98 SFR, strong-line metallicities [3.2 Physical Properties of the Galaxy G…: "We measured the emission fluxes from a Gaussian fit to the nebular lines."]
  - software: MPDAF, Sextractor
  - fitting: Gaussian line fits [Physical Properties of the Galaxy Group: "We measured the emission fluxes from a Gaussian fit to the nebular lines."]
  - validation: Agrees with earlier G2 and G6 metallicities [3.2 Physical Properties of the Galaxy G…: "Our estimates agreed within the errors with earlier measurements of G2 and G6 metallicities by (cite: kacprzak10b)."]
- result: CO(1-0) integrated flux G2 = 0.63 ± ±0.01 Jy km/s [Table 3: "| G2 | 11 30 07.66 | $-$14 49 23.41 | 9.7 | 44.8 | 0.63$\pm$0.01 | 250$\pm$50 |"]
- result: CO(1-0) integrated flux G4 = 0.42 ± ±0.03 Jy km/s [Table 3: "| G4 | 11 30 07.62 | $-$14 49 11.44 | 18.0 | 83.2 | 0.42$\pm$0.03 | 535$\pm$50 |"]
- result: CO(1-0) integrated flux G6 = 0.20 ± ±0.01 Jy km/s [Table 3: "| G6 | 11 30 08.53 | $-$14 49 28.54 | 21.5 | 99.4 | 0.20$\pm$0.01 | 205$\pm$50 |"]
- result: Molecular mass range = 1.00 to 3.16 x alpha_CO x 1e9 ± ±0.05 to ±0.07 Msun [3.2 Physical Properties of the Galaxy G…: "$M_{\rm mol}$ = (1.00$\pm$0.05) to (3.16$\pm$0.07) $\times$ ($\alpha_{\rm CO}$/1 K km/s pc$^2$) $\times$ 10$^9$ M$_{\odot}$"]
- result: Depletion time G2 = 13 ± ±5 Gyr [Table 3: "3.16$\pm$0.07 | 13$\pm$5"]
- limitation (authors): CO-to-H2 conversion factor is uncertain, so masses are expressed as functions of alpha_CO [3.2 Physical Properties of the Galaxy G…: "Estimates of the corresponding H$_2$ molecular masses however rely on the rather uncertain CO-H$_2$ conversion factor"]
- limitation (authors): Analysis of G0 hampered by the bright quasar; GalPak3D did not converge for several galaxies [3.3 Morphological and Kinematical Prope…: "The analysis of galaxy G0 is hampered by the proximity to the bright quasar (2.3 arcsec)."]
- not stated (card): Self-calibration solution intervals and imaging parameters for the continuum model; Line-free channels for uvcontsub and the fit order; Cleaning threshold, masks and niter in tclean; Duchamp parameters other than the 5-sigma threshold; GalPak3D priors, model choice and initial conditions; Simulation parameters and post-processing details (in a separate paper); ALMA flux scale uncertainty

### 2024A&A...692A.215C: Molecular gas budget of strongly magnified low-mass star-forming galaxies at cosmic noon (2024; high_z_galaxies; observational_alma_primary)
- question: What is the molecular gas content (CO and dust based) of strongly magnified low-mass star-forming galaxies at cosmic noon, and do they show a molecular gas deficit relative to scaling relations?
- step 4: SED fitting for stellar mass, SFR, Sigma_SFR
  - method: CIGALE with delayed SFH, BC03, nebular emission, Charlot & Fall attenuation, Dale 2014 dust; HST+JWST+ACA photometry [3.3: "we adopted a delayed SF history and used the (cite: bruzualStellarPopulationSynthesis2003) simple stellar population model."]
  - software: CIGALE
  - assumption: Chabrier IMF; flat LCDM Om=0.3, OL=0.7 [1 Introduction: "Additionally, we adopted the initial mass function (IMF) derived by (cite: chabrierGalacticStellarSubstellar2003)."]
- step 7: Molecular gas mass from CO
  - method: M_mol = alpha_CO L'CO(1-0) with Genzel 2015 model (a); r_J1 from Sigma_SFR relations fitted to compiled data [3.6.1: "we selected the first model (a) proposed in (cite: genzelCombinedCODust2015)."]
  - assumption: alpha_CO depends on metallicity (Genzel 2015) [Molecular gas mass using CO emissions: "As we are working with subsolar metallicities, we decided to employ an $\alpha_{\rm{CO}}$ model that accounts for the photo-dissociation of molecular gas in these types of galaxies"]
  - fitting: relations fitted to compiled r31, r41 data; r51 from Narayanan 2014 [3.6.1: "We fitted a model to the observational data sets for J= 3,4 and derived relations between both ${r}_{\rm{31}}$ and ${r}_{\rm{41}}$ and $\Sigma_{\rm{SFR}}$"]
  - validation: Compared to dust-based masses [3.6.3: "This CO-based approach is also generally consistent with the dust mass method at 870$\mu$m/1.25mm (bands 6 and 7)."]
- result: J0033 Mmol from CO = 10 ± 3 1e9 Msun [Table 6: "| J0033 | 4.42$\pm$0.08 | \- | 0.60$\pm$0.5 | \- | 10$\pm$3 | 23$^{+7} _{-6}$ |"]
- limitation (authors): Scatter in r31 and r41 relations adds systematic errors [3.6.1: "both derived relations present significant scatter, which incorporates systematic errors into our molecular gas estimations."]
- not stated (card): Cell size and image size for cubes and MFS images; Line-free channels / continuum selection for MFS in bands 3-4; Exact apertures and regions for flux extraction; CIGALE module parameter grids (only on Zenodo); Velocity ranges collapsed for moment maps for each arc; Functional form and fit parameters of r31 and r41 vs Sigma_SFR; Which CASA version applies to which project; Flux calibrators and fl…

### 2020A&A...641A.155V: CO emission in distant galaxies on and above the main sequence (2020; high_z_galaxies, star_formation; large_program_or_survey)
- question: How do CO line emission and excitation (CO SLEDs) of IR-selected galaxies on and above the main sequence at z~1.1-1.7 depend on L_IR, SFE, <U>, Sigma_SFR and distance from the main sequence?
- step 4: Fit scaling relations
  - method: Bayesian linear regression in log space with errors on both variables and censored data (LINMIX_ERR) [4.1 How does the CO emission correlate …: "applying a Bayesian regression analysis (LINMIX ERR.PRO, (cite: kelly_2007))"]
  - software: LINMIX_ERR
  - parameter: includes sources with L_IR>=10^8.5 Lsun and Flag=0.5 upper limits; excludes AGN-dominated galaxies and QSOs [4.1 How does the CO emission correlate …: "The modeling includes our and literature sources with $L_{\rm IR}\geq10^{8.5}$ $L_{\odot}$, reliable upper limits on the line luminosities ($Flag=0.5$)"]
  - assumption: Gas mass from M_dust with metallicity-dependent gas-to-dust ratio log(delta_GDR)=10.54-0.99x(12+log(O/H)); starbursts supersolar (delta_GDR~30); Sigma_SFR=SFR/(2 pi R^2), R=FWHM/2 [4.3.1 The star formation efficiency and…: "we then assumed that starburst galaxies have supersolar metallicities ($\delta_{\rm GDR}\sim30$"]
  - fitting: Kelly (2007) Bayesian approach [Table 5 notes: "adopting the Bayesian approach described in (cite: kelly_2007)"]
  - validation: Robustness checks excluding SMGs, outliers, high-z only; alternate metallicity assumptions [4.1 How does the CO emission correlate …: "fitting only the high-redshift samples changes the slopes of the two relations by $<15$% at $<3\sigma$ significance"]
- result: Slope of L_IR vs L'_CO(5-4) = 0.92 ± 0.01 dimensionless [Table 5: "| $L_{\rm IR}$, $L'_{\rm CO(5-4)}$ | $0.92\pm0.01$ | $-1.55\pm0.08$ | $0.17\pm0.01$ | $0.99$ |"]
- result: Slope of L_IR vs L'_CO(7-6) = 0.94 ± 0.01 dimensionless [Table 5: "| $L_{\rm IR}$, $L'_{\rm CO(7-6)}$ | $0.94\pm0.01$ | $-2.34\pm0.09$ | $0.16\pm0.01$ | $0.99$ |"]
- result: Slope of <U> vs R_52 = 0.36 ± 0.05 dimensionless [Table 5: "| $\langle U \rangle$, $R_{52}$ | $0.36\pm0.05$ | $-0.95\pm0.07$ | $0.15\pm0.02$ | $0.75$ |"]
- result: Slope of Sigma_SFR vs R_52 = 0.16 ± 0.02 dimensionless [Table 5: "| $\Sigma_{\rm SFR}$, $R_{52}$ | $0.16\pm0.02$ | $-0.60\pm0.03$ | $0.14\pm0.02$ | $0.82$ |"]
- limitation (authors): LVG parameters highly degenerate; best-fit values reflect relative trends only [4.4.4 Large velocity gradient modeling: "due to the high degeneracy among the LVG parameters, even with a handful of CO lines one could not obtain results simultaneously constraining $n_{\rm H_2}$, $T_{\rm kin}$, and $N(\mathrm{H_2})$"]
- limitation (authors): Sample biased to upper main sequence and warm dust by PACS detection requirement [2.1 The primary CO (5-4) sample: "We note that the initial requirement of a PACS detection steered the sample towards upper main-sequence objects and warm dust temperatures $T_{\rm dust}\gtrsim 30$ K."]
- not stated (card): CASA version and pipeline version; Weighting, robust and cleaning parameters (cubes are fit in uv plane, so mainly channel widths); Exact GILDAS scripts for the uv-plane fitting (customized, not released); Channel width / velocity resolution of the extracted spectra; Line-free channel selections per source; Metallicity assignment details for individual galaxies; Details of the Kelly LINMIX censor…

### 2021A&A...656A..60A: Black hole feeding and star formation in NGC 1808 (2021; nearby_galaxies, agn_and_quasars; observational_alma_primary)
- question: How is the AGN of NGC 1808 fed, and how do star formation and feedback behave in the central few hundred pc, based on the kinematics of the molecular gas?
- step 5: Resolved Kennicutt-Schmidt relation
  - method: Compute SFR from Pa-alpha and molecular gas surface density from CO(3-2) in apertures [4.2 Resolved Kennicutt-Schmidt relation: "we compute the surface densities of star formation rate (SFR) and molecular gas to build a resolved Kennicutt-Schmidt (KS) diagram"]
  - parameter: aperture radius 0.75'' = 34 pc [4.2 Resolved Kennicutt-Schmidt relation: "where the radius of 0.75$''$ = 34 pc"]
  - assumption: alpha_CO=4.36, r31=0.27, 45% missing flux correction, inclination 57 deg, Calzetti extinction [4.2 Resolved Kennicutt-Schmidt relation: "The molecular masses were corrected from the 45% missing flux, as discussed in Section [3.3](#miss)"]
  - validation: Comparison with Bigiel2008 and Casasola2015 [4.2 Resolved Kennicutt-Schmidt relation: "All our points lie in the KS relation"]
- limitation (authors): Missing flux ~40-50% due to lack of single-dish data. [3.3 CO luminosity and H2 mass: "Our rather smaller value derived with the ALMA high resolution observations is due to lack of single-dish observations to detect weak extended emission"]
- limitation (authors): Mass model parameters are degenerate. [4.4 Lindblad resonances: "Given the freedom and the degeneracy to distribute all mass components"]
- not stated (card): Line-free channels used for continuum; Robust/taper and cell/image size in GILDAS; Clean masks and stopping thresholds; Rest frequencies and velocity frame for the cubes; Tilted-ring fit initialization, ring widths beyond 0.3'' and 3DBarolo parameters; Aperture positions/fluxes for KS regions and Pa-alpha extinction values; Mass model parameter fitting details; Treatment of missing-flux correctio…

### 2013ApJ...767..132H: ALMA Observations of SPT-discovered, Strongly Lensed, Dusty, Star-forming Galaxies (2013; high_z_galaxies; observational_alma_primary)
- question: Are four SPT-discovered dusty sources gravitationally lensed, and what are their magnifications and intrinsic properties from visibility-plane lens modeling?
- step 3: Derive intrinsic properties
  - method: Divide observed fluxes by magnification; greybody SED for L_FIR; SFR from Kennicutt conversion [4 Discussion: "The lens models permit the calculation of some intrinsic properties of the lensed galaxies by simply dividing observed properties by the magnification."]
  - assumption: Standard starburst SFR conversion (Kennicutt 1998) [4 Discussion: "assuming a standard conversion for starbursting galaxies (cite: kennicutt98)"]
  - validation: LABOCA 870 um flux agrees with modeled ALMA flux within ~10% [2.3 Other Supporting Data: "agree with the total flux density in the modeled ALMA data (described below) to within calibration uncertainties, typically 10%"]
- result: SPT0346-52 intrinsic L_FIR = 37.3 ± 2.8 1e12 Lsun [Table 1: "37.3$\pm$2.8"]
- result: SPT0346-52 SFR surface density = 4200 ± not stated Msun/yr/kpc^2 [4 Discussion: "implying a star-formation rate of 4200 M$_{\odot}$ yr$^{-1}$ kpc$^{-2}$"]
- limitation (authors): Only compact-configuration data used; SPT0529-54 posterior bimodal [4 Discussion: "The extended array data on this source can possibly break this degeneracy."]
- not stated (card): CASA version and calibration scripts; Imaging parameters (weighting, cleaning, cell size); MCMC chain length, priors, tempering schedule T; Greybody fit parameters (T_dust, beta) and FIR luminosity integration range; Lens priors and source-model starting values; Phase calibrator names; Code for lens modeling not released

### 2024ApJ...976...88L: Disk Turbulence and Star Formation Regulation in High-z Main-sequence Analog Galaxies (2024; nearby_galaxies, high_z_galaxies; archival_reuse)
- question: What sets the molecular gas velocity dispersion (turbulence) and star formation regulation on kpc scales in z~0.1 analogues of z~1-2 main-sequence galaxies, and do star formation theories reproduce the sigma_mol-Sigma_SFR/Sigma_mol relatio…
- step 2: Measure Sigma_*, Sigma_SFR and Sigma_mol in beam-sized apertures
  - method: Two offset grids of beam-sized circular apertures; stellar mass from F125W with color-based M/L; SFR from Halpha (Hao+11); Sigma_mol = alpha_CO R_J,J-1 I_CO [3 Methods: "we define a “grid” of circular, beam-sized apertures centered on the galaxy, and a second that is offset from the center by $0.5 \times$ the beam FWHM"]
  - software: CASA, astropy
  - parameter: log Upsilon = 0.195 (F336W-F125W) - 1.187, floor -1 [3.1 Stellar Mass Surface Density: "and we impose a floor of $\mathrm{log} \, \Upsilon_{*,\mathrm{F125W}} = -1$."]
  - parameter: SFR = 5.53e-42 L_Halpha [3.3 Star Formation Rate Surface Density: "SFR\;[M_{\odot}\,yr^{-1}]} = 5.53 \times 10^{-42} \times L_{\mathrm{H}\alpha}"]
  - assumption: Constant alpha_CO = 4.35 Msun (K km/s pc^2)^-1, or variable alpha_CO from Bolatto+13 eq. 31 iterated until change <0.1% [3.2 Molecular Gas Surface Density: "repeating this process until $\alpha_{\mathrm{CO}}$ changes by less than 0.1%."]
- step 4: Fit scaling relations and compare to theory
  - method: ODR power-law fits of Sigma_mol-Sigma_*, KS, sigma_mol-Sigma_mol, -Sigma_SFR, -t_dep, with PHANGS; compare to Krumholz+18, TIGRESS, SILCC, Brucy+20 curves [4.3 Resolved Molecular KS Relation at H…: "with a power law of the form $\mathrm{log}$ $\Sigma_{\mathrm{SFR}}$ $= N\, \times\, \mathrm{log}$ $\Sigma_{\mathrm{mol}}$ $+\,C$ using ODR."]
  - software: scipy ODR
  - assumption: Krumholz+18 fiducial parameters; P*/m* = 3000 km/s for Faucher-Giguere model [4.4 Resolved Correlations: "If we assume $P_{*}/m_{*} = 3,000$ km s$^{-1}$"]
  - fitting: ODR; priors not applicable [Results, Resolved Molecular KS Relation…: "with a power law of the form $\mathrm{log}$ $\Sigma_{\mathrm{SFR}}$ $= N\, \times\, \mathrm{log}$ $\Sigma_{\mathrm{mol}}$ $+\,C$ using ODR."]
- result: Resolved Sigma_mol-Sigma_* slope = 0.78 ± 0.03 dimensionless [4.2 Sigma_mol-Sigma_* Relation: "\log \Sigma_{\mathrm{mol}} = (0.78\pm0.03) \times \log \Sigma_{*} + (0.05\pm0.07)."]
- result: KS slope, constant alpha_CO, DYNAMO only = 0.90 ± 0.04 dimensionless [4.3 Resolved Molecular KS Relation at H…: "(0.90 \pm 0.04) \, \times \, \mathrm{log} \; \Sigma_{\mathrm{mol}} - (2.70 \pm 0.08)"]
- result: KS slope, variable alpha_CO, DYNAMO = 1.23 ± 0.03 dimensionless [4.3 Resolved Molecular KS Relation at H…: "(1.23 \pm 0.03) \, \times \, \mathrm{log} \; \Sigma_{\mathrm{mol}} - (3.08 \pm 0.06)"]
- result: Median depletion time, constant alpha_CO = 0.8 ± not stated Gyr [4.3 Resolved Molecular KS Relation at H…: "more than half of the DYNAMO line-of-sight measurements (297/490) have $t_{\mathrm{dep}}$ $<1$ Gyr."]
- result: sigma_mol-Sigma_mol slope (DYNAMO+PHANGS) = 0.48 ± 0.02 dimensionless [4.4 Resolved Correlations: "\mathrm{log}\;\sigma_{\mathrm{mol}} = (0.48 \pm 0.02) \, \times \, \mathrm{log\;}\Sigma_{\mathrm{mol}} + (0.47 \pm 0.03)"]
- result: sigma_mol-Sigma_SFR slope (DYNAMO+PHANGS) = 0.27 ± 0.02 dimensionless [5.1.2 Feedback-Regulated Star Formation: "$N = 0.27 \pm 0.02$"]
- result: sigma_mol-t_dep slope = -0.80 ± 0.07 dimensionless [4.4 Resolved Correlations: "\mathrm{log}\;\sigma_{\mathrm{mol}} = (-0.80 \pm 0.07) \, \times \, \mathrm{log\;}t_{\mathrm{dep}} + (1.00 \pm 0.03)."]
- result: Fraction of measurements in powered-breakout region = ~38 ± not stated percent [5.3 Feedback-Driven Outflows: "We find that ${\sim} 38$% of our measurements lie within the region where powered breakouts"]
- limitation (authors): Literature comparison sample is heterogeneous and of differing data quality [4.1 Galaxy Averaged Relationship: "We offer the strong caveat that the sample is not homogeneously selected and there is a difference in data quality"]
- not stated (card): Line-free channels, continuum subtraction and moment-map/integrated intensity masking details; Image size, cell size, channel width, cleaning threshold, final rms of cubes; Aperture radius definition and exact beam-sized aperture grid placement; S/N cuts for spectral fits and initial guesses for curve_fit; Metallicity values used for variable alpha_CO; Extinction values per aperture; Whether ALMA…

### 2018ApJ...855L..25K: Core Emergence in a Massive Infrared Dark Cloud: A Comparison between Mid-IR Extinction and 1.3 mm Emission (2018; star_formation, milky_way_ism; observational_alma_primary)
- question: How does the presence of 1.3 mm continuum emitting dense structures (cores) depend on the local mass surface density from MIR extinction in IRDC G28.37+0.07, and what dense gas fraction and star formation efficiency per free-fall time foll…
- step 5: Estimate star formation efficiency per free-fall time
  - method: Turbulent Core Model: t_*f/t_ff = 0.42 for Mc=5 Msun, M_cl=1e4 Msun; eps_ff from f_dg and eps_core [4.2 Star Formation Rates: "Under these two conditions, $t_{*f}/\bar{t}_{\rm ff,cl}\rightarrow0.42$."]
  - assumption: eps_core = 0.5; steady SFR; Salpeter CMF 1-240 Msun; mm continuum is complete protostellar core census [4.2 Star Formation Rates: "Assuming the SFR is steady and the CMF is evenly populated"]
  - validation: compared with Orion Nebula Cluster eps_ff [4.2 Star Formation Rates: "about a factor of two larger than the value estimate inside the half-mass radius of the Orion Nebula Cluster"]
- result: star formation efficiency per free-fall time = 0.11 ± +0.06/-0.041 (0.17 and 0.069 quoted) dimensionless [4.2 Star Formation Rates: "$\epsilon_{\rm ff}=0.11^{0.17}_{0.069}$"]
- limitation (authors): Dust temperature assumption is the largest uncertainty (up to factor ~2); MIREX has zero-point offsets, saturation and MIR-source contamination. [3.3 Dense Gas Fraction: "Systematic variations arising from the choice of dust temperature are up to a factor of almost two and are the most significant source of uncertainty"]
- not stated (card): Clean threshold, number of iterations and masks; Exact uv-taper parameters; Calibration pipeline/CASA version; Which pixels were flagged as MIR-bright sources (visual list); Rebinning and regridding procedure to MIREX grid; Mosaic phase centers/coordinates

### 2012ApJ...760L..25E: Giant Molecular Clouds and Star Formation in the Tidal Molecular Arm of NGC 4039 (2012; nearby_galaxies, star_formation, milky_way_ism; archival_reuse)
- question: What are the properties of the newly found tidal molecular arm south of NGC 4039, and how do its clumps and star formation efficiency compare with other arms and tidal features?
- step 4: Derive SFR surface density and SFE
  - method: Combine FUV (extinction-corrected) and 24 micron maps at 6'' resolution, regrid to 3'' pixels, compare with gas surface density pixel by pixel [Star Formation Law and Stellar Clusters: "We also convolved the molecular gas surface densities to 6$''$ and converted the molecular gas and SFR surface density maps to a pixel size of 3$''$ ."]
  - software: MOPEX
  - parameter: Sigma_SFR = 3.2e-3 I24 + 8.1e-2 IFUV; 3 sigma SFR threshold 0.018 Msun/yr; A_FUV = 8.24 E(B-V) [Star Formation Law and Stellar Clusters: "For the SFR map, a 3$\sigma$ threshold was used, or 0.018 $M_\odot$ yr$^{-1}$."]
  - validation: Estimated 24 micron PSF Airy ring contamination (~0.1 dex) and excluded pixels within 11'' of bright peaks [Star Formation Law and Stellar Clusters: "so the PSF contamination in this case is about 25%, or about 0.1 dex on the SF law plot."]
- result: Arm SFE = -8.2 ± 0.3 log(yr^-1) [Star Formation Law and Stellar Clusters: "log(SFE \[yr$^{-1}$\]) = –8.2 $\pm$ 0.3"]
- result: NGC 4039 region SFE = -8.8 ± 0.3 log(yr^-1) [Star Formation Law and Stellar Clusters: "log(SFE \[yr$^{-1}$\]) = –8.8 $\pm$ 0.3"]
- limitation (authors): Clumps mostly unresolved; higher resolution needed; short spacings needed [Distribution and kinematics of the mole…: "Higher resolution observations to resolve these complexes are necessary to set stronger constraints."]
- limitation (authors): Inclination of the arm is uncertain [Distribution and kinematics of the mole…: "Although the inclination of this structure is rather uncertain"]
- not stated (card): tclean/clean parameters (weighting, robust, deconvolver, threshold, niter); Exact CASA version and calibration scripts used; Mosaic imaging details and primary beam correction; Continuum subtraction and line-free channels; How clumps were identified and their apertures/fluxes measured; Pixel-to-pixel SF law regridding details and region definitions; Exact conversion of FUV/24 micron maps to MJy/s…

### 2019A&A...621A..27F: Massive galaxies on the road to quenching: ALMA observations of powerful high redshift radio galaxies (2019; agn_and_quasars, high_z_galaxies; observational_alma_primary)
- question: What are the star-formation rates of powerful high-z radio galaxy hosts once synchrotron contamination and spatially resolved components are separated using ALMA data, and how do they compare with the main sequence and SMBH growth?
- step 3: Integrate IR luminosities and uncertainties; derive SFR
  - method: Integrate models over rest-frame 8-1000 um for each MCMC sample; percentiles give uncertainties; upper limits by scaling modified BB (beta=2.5, T=50 K) to ALMA; SFR from Kennicutt1998 divided by 1.5 for Kroupa [4.1 SF and AGN IR luminosities: "This is done by scaling a modified BB (with fixed $\beta = 2.5$ and T=$50$ K) to the ALMA data point."]
  - assumption: SFR = 1.72e-10 L_IR_SF, Salpeter IMF then /1.5 to Kroupa [5.1: "${\rm SFR} = 1.72 \times 10^{-10} \times {\rm L}_{\rm SF}^{\rm IR},$"]
- result: median SFR of sample = 110 ± not stated Msun/yr [5.1: "with a median[^3] value of 110 M$_{\odot}$ yr$^{-1}$"]
- result: SFR reduction factor vs Drouart2014 = ~7 ± not stated dimensionless [5.1: "Our star-formation rates are seven times lower than previously estimated by (cite: Drouart2014) for the same sources."]
- result: ratio L_IR_SF to Drouart2014 (detections only) = ~0.5 ± not stated dimensionless [4.4: "our estimates of L$^\mathrm{IR}_\mathrm{SF}$ are only $\sim$50% of those estimated in (cite: Drouart2014)"]
- limitation (authors): Upper limits dominate many SFRs; no intermediate-frequency data to determine synchrotron steepening [MRC 1017-220: "without a data point at an intermediate frequency between the radio and ALMA data, it is not possible to make a final conclusion"]
- not stated (card): Number of walkers, steps and burn-in for emcee; Exact line-free/flagged channels per source; CASA version used for imaging; Image size and clean threshold/masks; Flux calibrator and flux-scale uncertainty; How ALMA band 3/4 photometry was extracted per source in detail (regions, apertures); Prior treatment of normalisations in MR-MOOSE

### 2018ApJ...862...64S: Deciphering the Activity and Quiescence of High-redshift Cluster Environments: ALMA Observations of Cl J1449+0856 at z = 2 (2018; galaxy_clusters_and_sz, high_z_galaxies; observational_alma_primary)
- question: How much obscured star formation and how much quiescence is there in the core of the z=2 cluster ClJ1449, and what do ALMA 870um continuum and CO(4-3) say about member galaxies and the forming BCG?
- step 2: Derive IR luminosities and SFRs
  - method: LIR from 870um flux via MS/SB SEDs and from CO(4-3) via CO SLED and CO(5-4)-LIR relation; SFR via Kennicutt 1998 [4.1 Dusty star formation: "The IR luminosity estimate L$_{IR,870\mu m}$ was derived from the measured 870$\mu$m flux using the average MS and starburst (SB) SEDs"]
  - assumption: Salpeter IMF; BzK and ULIRG CO SLEDs [1 Introduction: "Stellar masses and star formation rates are quoted for a (cite: salpeter1955) IMF."]
  - validation: Consistency of the two LIR estimates; A4 and A5 inconsistent hence interlopers [4.1 Dusty star formation: "the consistency of L$_{IR,870\mu m}$ and L$_{IR,CO43}$, besides ensuring cluster membership of the 870$\mu$m detections, also confirms the reliability of the SFR estimates."]
- result: Total SFR of cluster members = ~700 ± ±100 Msun/yr [4.1 Dusty star formation: "corresponding to a total SFR of $\sim700\pm100$ M$_{\odot}$/yr"]
- result: Total LIR = 4.3e12 ± ±0.5e12 Lsun [4.1 Dusty star formation: "total L$_{IR}\sim4.3\pm0.5\times10^{12}$L$_{\odot}$"]
- result: SFR/Mhalo lower limit = 1300 ± ±400 Msun/yr/1e14 Msun [4.1 Dusty star formation: "of $\sim$1300$\pm$400 M$_{\odot}$ yr$^{-1}$ / 10$^{14}$ M$_{\odot}$"]
- result: SFR volume density = 1.0e4 ± ±0.1e4 Msun/yr/Mpc^3 [4.1 Dusty star formation: "SFR volume density $\sim1.0\pm0.1\times10^{4}$ M$_{\odot}$ yr$^{-1}$Mpc$^{-3}$"]
- limitation (authors): Small field and low-number statistics; field comparison selection not equivalent [4.1.1 Color distribution: "the very small number statistics of the *ALMA*-detected sample in the cluster"]
- not stated (card): Reduction/calibration and imaging details (CASA version, weighting, cleaning) are only in C18; Positions and catalogue of known cluster members; Per-source flux values for A1-A6 and members; Flux-boosting correction recipe for CO(4-3); CO(5-4)/CO(4-3) ratio values and CO(5-4)-LIR relation coefficients adopted; Conversion from 870um flux to LIR with Bethermin SEDs (template details)

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

### 2024A&A...682A..54T: HYPERION. Interacting companion and outflow in the most luminous z &gt; 6 quasar (2024; agn_and_quasars, high_z_galaxies; observational_alma_primary)
- question: Does deep, lower-resolution ALMA band 3 and 6 data of the z>6 quasar J0100+2802 reveal an interacting companion and a [CII] outflow, and what are their properties?
- step 4: Derive companion TIR and SFR
  - method: Integrate best-fit models 8-1000 um; Kennicutt 1998 with Chabrier IMF [3.3: "obtaining $L_{\rm TIR}$ in the range $[0.3-3.4]\times 10^{12}\ \rm L_{\odot}$."]
  - assumption: Chabrier IMF [3.3: "adopting a Chabrier initial mass function (cite: chabrier2003)"]
- result: Companion SFR range = 35-344 ± not stated Msun/yr [3.3: "This implies an SFR in the range $[35-344]\ \rm M_{\odot}\ yr^{-1}$"]
- limitation (authors): Resolution cannot distinguish merging from rotation, or single from multiple companions [4 Discussion: "However, the resolution of our observation did not allow us to distinguish between merging and rotation processes."]
- not stated (card): Cell size, image size, clean mask and iteration/threshold values; Which MFS/line channels were combined exactly for continuum and moment maps; X_C+, gas temperature and density used in the HI mass equation; Outflow radius derivation details and L_out computation; Priors/initial values of the two-Gaussian MCMC; Exact PSF subtraction procedure and apertures; Archive pipeline version and calibrators…

### 2019PASJ...71...40T: Environmental impacts on molecular gas in protocluster galaxies at z ∼ 2 (2019; high_z_galaxies; observational_alma_primary)
- question: Do molecular gas fractions and depletion timescales of protocluster galaxies at z~2-2.5 differ from field-galaxy scaling relations, and does this depend on stellar mass?
- step 2: Estimate SFRs
  - method: MIPS 24um to LIR with Wuyts templates then Kennicutt; Halpha with dust correction for non-detections [2.2 Stellar mass and star formation rate: "we use (cite: 2008ApJ...682..985W) templates to avoid the overestimate of SFRs."]
  - software: MOPEX
  - parameter: 7 arcsec aperture, aperture correction 2.57 [2.2 Stellar mass and star formation rate: "We use an aperture correction of 2.57 to derive total fluxes"]
  - assumption: [NII] correction from mass-metallicity relation; A_Halpha systematic 0.32 mag [2.2 Stellar mass and star formation rate: "with the systematic uncertainty of 0.32 mag"]
- step 4: Derive gas masses, fractions and depletion times
  - method: Convert L'(3-2) to L'(1-0) and apply metallicity-dependent alphaCO; compare with Tacconi scaling relations [4 Molecular gas properties: "we assume the same CO excitation with $L'_{(1-0)}/L'_{(3-2)}$=1.8"]
  - parameter: alphaCO=4.36 f_metal; f_metal=1.1 at logM=11, 1.4 at 10.5; upper limits 5 sigma with 400 km/s [4 Molecular gas properties: "The correction factor is $f_\mathrm{metal}=1.1$ at $\log(M_\mathrm{star}/M$$)=11$ and $f_\mathrm{metal}=1.4$ at $\log(M_\mathrm{star}/M$$)=10.5$."]
  - assumption: Field-like CO excitation, no environmental dependence [4 Molecular gas properties: "which is a typical value in field galaxies"]
- result: f_gas of massive CO-detected galaxies = 0.37-0.53 ± not stated dimensionless [4 Molecular gas properties: "moderately gas-rich with $f_\mathrm{gas}=0.37-0.53$"]
- limitation (authors): Larger sample needed; CO excitation assumed; low-mass detections biased [5 Discussion: "although we need a larger sample to verify the scaling relation in high-density environments"]
- not stated (card): CASA version and calibration details (calibrators, flagging); Synthesized beam sizes (blank in text); Clean threshold, masking, image size and cell size; Exact SFR conversion details and Wuyts template application; Coefficients of the scaling relations evaluated per galaxy; Individual galaxy coordinates and catalogs

### 2019ApJ...887...88E: Star Formation Efficiencies at Giant Molecular Cloud Scales in the Molecular Disk of the Elliptical Galaxy NGC 5128 (Centaurus A) (2019; nearby_galaxies, agn_and_quasars, milky_way_ism; observational_alma_primary)
- question: What is the resolved Kennicutt-Schmidt star formation law and star formation efficiency at GMC scales (~40 pc) in the molecular disk of the elliptical galaxy Cen A?
- step 5: Build resolved KS law and SFE maps at 43 pc
  - method: Regrid CO and 8 um PAH to 2.4" pixels; SFR surface density via log Sigma_SFR = 0.844 log Sigma_L8 - 30.923; inclination correction 70 deg; fit orthogonal distance regression [5 Spatially Resolved KS Law: "The pixel size in our analysis is 2.4$''$ (or 43 pc, i.e. that of the 8 $\mu$m map)."]
  - software: scikit-learn
  - parameter: Sigma_mol completeness ~4 Msun/pc2 (3 sigma, 10 km/s) [5 Spatially Resolved KS Law: "complete down to surface densities of $\Sigma_{\rm mol} \simeq 4\,M_\odot\,{\rm pc}^{-2}$"]
  - assumption: Fixed inclination 70 deg [5 Spatially Resolved KS Law: "Our surface density maps have been corrected by a fixed inclination of 70$^\circ$."]
  - fitting: Gaussian mixture model (2 components, full covariance chosen by BIC) after removing 19 AGN points; orthogonal distance regression [5.1 KS Law: "A Bayesian Information Criterion (BIC) selects the best model, which is the one obtained with the full covariance matrix"]
  - validation: Compared fit with Boquien et al. 2011 calibration [5 Spatially Resolved KS Law: "The two fits have a very similar slope but the (cite: 2011AJ....142..111B) intercept is slightly higher than the one we find."]
- result: Global SFE = 0.6 (depletion time 1.5 Gyr) ± not stated Gyr^-1 [5.2 SFE: "so the SFE is 0.6 Gyr$^{-1}$ (or depletion time $\tau =$ 1.5 Gyr)"]
- result: KS slope (orthogonal regression), all data = 0.63 (intercept -2.4) ± not stated dimensionless [5.1 KS Law: "The slope of the orthogonal distance regression fit to the data points characterizing the SF law is $N$ = 0.63 (intercept is –2.4)."]
- result: KS slope in CND = 0.28 (intercept -1.6) ± not stated dimensionless [5.1 KS Law: "for the CND $N$ = 0.28, and intercept –1.6"]
- result: Mean SFE CND / outer disk = 0.32 / 1.29 ± stddev 0.24 / 0.93 Gyr^-1 [Table 2: "| CND | 1.65 | 0.32 | 0.26 | 0.24 |"]
- limitation (authors): Large scatter, projection effects and warped disk uncertainty in the KS fits; XCO uncertainty in CND [5.1 KS Law: "We note however that the scatter is large"]
- not stated (card): Imaging parameters (weighting, robust, tclean deconvolver, mosaic gridder, cleaning threshold) are not given; Final synthesized beam and rms noise of the combined cube; Line-free channels used for continuum subtraction; How TP data were combined with interferometer data (feather vs joint deconvolution); Spitzer map convolution/regridding details and the AGN-contaminated pixel mask; GMM initialisa…

### 2026ApJ..1001..131C: MAGAZ3NE: Far-IR and Radio Insights into the Nature and Properties of Ultramassive Galaxies at z ≳ 3 (2026; high_z_galaxies, agn_and_quasars; archival_reuse)
- question: Do FIR-to-radio data change the inferred nature (quiescent vs dusty star-forming), gas content and AGN activity of two spectroscopically confirmed MAGAZ3NE ultramassive galaxies at z>~3?
- step 3: Molecular gas mass and depletion time
  - method: RF 850um luminosity from CIGALE SED with temperature correction, converted with Scoville16 alpha_nu; compared with Hughes17 and gas-to-dust ratio methods; t_dep = M_mol/SFR [4.3.1 Molecular Gas Mass: "we estimated the RF 850$\mu$m luminosity ($L_{\nu_{850,\mu{\rm m}}}$) directly from the `CIGALE` fit."]
  - software: CIGALE
  - parameter: Temperature correction B_nu(850,25K)/B_nu(850,T_dust): 0.77 (195616), 1.06 (209435) [4.3.1 Molecular Gas Mass: "This correction factor is 0.77 for 195616 and 1.06 for 209435."]
  - assumption: alpha_nu = 6.7 +/- 1.7e19 erg/s/Hz/Msun; 25 K calibration [4.3.1 Molecular Gas Mass: "6.7 \pm 1.7 \times 10^{19} \, \text{erg} \, \text{s}^{-1} \, \text{Hz}^{-1} \, M_\odot^{-1}"]
  - validation: Alternative methods consistent within 0.2 dex [4.3.1 Molecular Gas Mass: "showing consistency within 0.2 dex."]
- step 4: Predict stellar mass growth and diagnose AGN
  - method: Constant SFR over 0.5 t_dep; AGN from SED fraction, X-ray, radio loudness, emission lines [4.4 Predicted Stellar Mass Evolution: "we assume a constant SFR over one half of the depletion timescale (0.5$\times t_{\rm dep}$)."]
  - software: CIGALE
  - assumption: Photon index 1.4 for X-ray; radio spectral index -0.8 [5.1.2 X-ray and Radio AGNs: "assuming a photon index of $\Gamma = 1.4$ (cite: Marsan2022)"]
- result: log M_mol 195616 / 209435 = 10.43 / 11.75 ± ±0.11 / +0.10/-0.13 log Msun [Table 5: "$10.43^{+0.11}_{-0.11}$"]
- result: Depletion time 195616 / 209435 = 0.43 / 1.44 ± ±0.13 / ±0.48 Gyr [Table 5: "$0.43 \pm 0.13$"]
- result: Predicted log M_star,final 209435 = 11.72 (+0.34 dex over 0.72 Gyr) ± +0.09/-0.12 log Msun [4.4 Predicted Stellar Mass Evolution: "reaching a stellar mass of $\log (M_{\star}/M_{\odot})$ = 11.72 over the course of the next 0.72 Gyr."]
- result: 195616 rest-frame 2-10 keV luminosity = 2.17e44 ± ±0.23e44 erg/s [5.1.2: "$L_{\rm 2-10 keV, rest} = 2.17 \pm 0.23 \times 10^{44}$ erg s$^{-1}$"]
- limitation (authors): A3COSMOS gas masses do not include AGN contribution; AGN may bias gas mass of 195616 [4.3.1: "the (cite: Liu2019b) approach does not include any possible AGN contribution, which may lead to overestimates of both SFR and molecular gas mass."]
- not stated (card): CIGALE parameter values beyond Table 6 (defaults of v2022.1 assumed, but the nebular U grid differs between text and table); How ALMA flux density and uncertainties were extracted/used in the SED fit beyond the A3COSMOS catalog; CIGALE upper-limit treatment and any systematic error floor; Exact stellar mass and SFR for A3COSMOS comparison galaxies (source and fitting); Coordinates of targets

### 2020ApJS..247...61F: The ALPINE-ALMA [C II] Survey: Multiwavelength Ancillary Data and Basic Physical Measurements (2020; high_z_galaxies; large_program_or_survey)
- question: What are the ancillary multi-wavelength data and basic physical properties (stellar mass, SFR, UV luminosity, UV slope, Halpha, velocity offsets) of the ALPINE galaxies, and is the sample representative of 4<z<6 galaxies?
- step 8: Derive Halpha luminosity/EW and SFR from Spitzer colors
  - method: [3.6]-[4.5] color constrains Halpha for 4<z<5 using BC03 basis models A-F; f=0.44; [N II]/Halpha=0.15; SFR via Kennicutt98 [4.4 Measurement of Halpha emission: "we assume an [N II] to H$\alpha$ ratio of $0.15$, as expected for galaxies at $\log({\rm M}/{\rm {M}_{\odot}})= 10$ (cite: FAISST18)"]
  - parameter: SFR = 4.5e-42 L(Halpha) [erg/s] [4.4 Measurement of Halpha emission: "${\rm SFR\,(M_{\odot}\,yr^{-1})} = 4.5 \times 10^{-42}\, L_{\rm{H\alpha}}\,{\rm (erg\,s^{-1})},$"]
  - assumption: f-factor 0.44 (likely upper limit on LHalpha); Calzetti and SMC reddening [4.4 Measurement of Halpha emission: "For now, the assumed $f=0.44$ provides likely an *upper* limit on the H$\alpha$ luminosities."]
  - validation: Halpha SFRs compared to SED SFRs; Halpha vs [C II] compared with De Looze relations [4.4 Measurement of Halpha emission: "The H$\alpha$-derived SFRs trace well the SED-derived SFRs above $\sim 13\,{M}_{\odot}\,{\rm yr^{-1}}$."]
- limitation (authors): Spitzer blending can overestimate stellar masses; about one-third have contaminated Spitzer photometry [4.1.1 Fitting Method: "In total, one-third of the galaxies have contaminated Spitzer photometry to some degree."]
- limitation (authors): f-factor is the largest uncertainty in the Halpha measurement [4.4 Measurement of Halpha emission: "The $f$-factor is the largest uncertainty in this measurement method"]
- not stated (card): The ALMA data reduction and [C II] line fitting are entirely deferred to Bethermin et al. 2020; no calibration or imaging settings given here; The final catalogs are hosted at an author web page; the exact catalog contents are needed to reproduce numbers; Mophongo/SExtractor/LePhare configuration beyond listed parameters (e.g. LePhare redshift handling is fixed to spectroscopic z but not explicit…

### 2020A&A...641A.151S: Molecular gas in the central region of NGC 7213 (2020; nearby_galaxies, agn_and_quasars; archival_reuse)
- question: What are the AGN power, molecular gas kinematics, gas mass and depletion time in the central region of the LLAGN NGC 7213, and what is the AGN impact on the host ISM and star formation?
- step 5: Gas mass and depletion time
  - method: APEX CO(2-1) -> CO(1-0) with ratio 3, L' via Carilli & Walter, M_gas=alpha_CO L'; SFR scaled by Herschel 70um aperture ratio; t_depl=M_gas/SFR [4.4 The molecular gas mass: "We therefore assumed $f_{\rm CO(2-1)}$/$f_{\rm CO(1-0)}=3$"]
  - parameter: F_tot/F_25" = 2.0±0.3 at 70 um [4.4 The molecular gas mass: "F$_{tot}$/F$_{25^{\prime\prime}}$=2.0$\pm$0.3"]
  - assumption: alpha_CO=1.1, solar metallicity, CO(2-1)/CO(1-0)=3 [4.4 The molecular gas mass: "we assume it to be solar-like"]
  - validation: L'_CO compared with L_IR-L'_CO relation; consistent within uncertainties [4.4 The molecular gas mass: "the two values are consistent within the uncertainties"]
- result: L'_CO(1-0) APEX = 1.8e8 ± 0.3e8 K km/s pc^2 [4.4 The molecular gas mass: "L$^{\prime}_{\rm CO(1-0), APEX}=(1.8\pm0.3)\times10^8$K km s$^{-1}$ pc$^2$"]
- result: Molecular gas mass = 2.0e8 ± 0.3e8 Msun [4.4 The molecular gas mass: "M$_{\rm gas}=(2.0\pm0.3)\times10^8$ M$_{\odot}$"]
- result: Depletion time = 0.4 ± 0.1 Gyr [4.4 The molecular gas mass: "t$_{\rm depl}$=0.4$\pm$0.1 Gyr"]
- limitation (authors): ALMA configuration resolves out diffuse gas; MRS 6.2 arcsec [3.2.2 The CO(2-1) emission line: "that has most likely been resolved out because of the extended antenna configuration"]
- limitation (authors): Cannot exclude free-free contribution to continuum [4.1 The point-like continuum: "With the current data, we are not able to exclude the contribution from other mechanisms"]
- not stated (card): Clean threshold, niter, masks, cell and image size; Line-free channels and continuum-subtraction order; Primary-beam correction details; Moment-map clipping thresholds; 3DBarolo parameter file details (e.g. normalisation, fitting mode, VDISP initial); How APEX baseline/windows and double-Gaussian fit were set; Outflow velocity/size/flux extraction details for Regions A and C; Exact NED coordinate…

### 2013ApJ...770...13W: Redshift 6.4 Host Galaxies of 10<SUP>8</SUP> Solar Mass Black Holes: Low Star Formation Rate and Dynamical Mass (2013; high_z_galaxies, agn_and_quasars; observational_alma_primary)
- question: What are the star formation rates, [C II] properties and dynamical masses of the host galaxies of two z=6.4 quasars with ~1e8 Msun black holes?
- step 2: Derive L_FIR and SFR
  - method: Convert continuum flux to L_FIR (42.5-122.5 micron) with a greybody, then SFR via Kennicutt relation [3.1 Far-infrared luminosity: "This continuum flux-density was converted to a far-infrared luminosity assuming a typical SED for high-redshift star-forming galaxies."]
  - parameter: Td=47 K, beta=1.6 [3.1 Far-infrared luminosity: "we adopt a greybody spectrum with dust temperature, $T_{\rm d} =47$ K and emissivity index, $\beta=1.6$."]
- result: J0210-0456 L_FIR = 2.60e11 ± 0.76e11 Lsun [Table 1: "$L_{\rm FIR}$ | $(2.60 \pm 0.76) \times 10^{11} \, {\rm L}_\odot$"]
- result: J2329-0301 L_FIR (3 sigma) = <1.9e11 ± not stated Lsun [3.1 Far-infrared luminosity: "J2329-0301 is undetected with $L_{\rm FIR} <1.9 \times 10^{11} \, {\rm L}_\odot$ ($3\,\sigma$ limit)."]
- result: J0210-0456 SFR = 48 ± 14 Msun/yr [Table 1: "SFR | $48 \pm 14\, {\rm M}_\odot\,{\rm yr}^{-1}$"]
- result: J2329-0301 SFR limit = <40 ± not stated Msun/yr [Table 1: "SFR | $48 \pm 14\, {\rm M}_\odot\,{\rm yr}^{-1}$ | $<40\, {\rm M}_\odot\,{\rm yr}^{-1}$"]
- limitation (authors): Source only marginally resolved; intrinsic size poorly constrained and inclination unknown [3.3 [C ii] dynamics and spatial extent: "The intrinsic source size is not well constrained as it is only marginally resolved"]
- limitation (authors): L_FIR uncertainties exclude dust temperature uncertainty [3.1 Far-infrared luminosity: "uncertainties on $L_{\rm FIR}$ (and inferred SFR) only include the flux measurement uncertainties, not that of the dust temperature."]
- not stated (card): Imaging weighting/robust, deconvolution and cleaning parameters; CASA version and calibration script/flux model for Uranus; Exact channel ranges for line, wings, and continuum spectral windows; Method and aperture for the 3.4 sigma continuum flux measurement and spectral extraction; How [C II] flux integration and line luminosity conversion were done; Fit details for the Gaussian plus constant sp…

### 2025ApJ...988..162D: Constraining Resolved Extragalactic R<SUB>21</SUB> Variation with Well-calibrated ALMA Observations (2025; nearby_galaxies; observational_alma_primary)
- question: How does the CO(2-1)/CO(1-0) line ratio R21 vary between and within nearby galaxies at 1.7 kpc resolution, using well calibrated ALMA data, and how does it depend on SFR surface density, radius, specific SFR and metallicity?
- step 5: Bin R21 and fit scaling relations
  - method: Bin by r_gal, Σ_SFR, sSFR, metallicity; linear (radius, metallicity) or power-law (SFR, sSFR) regression to binned values; Kendall tau [4.1.2: "we fit a regression line to the equally weighted binned means. For the regression line, we either assume a linear relation (galactocentric radius) or a power-law"]
  - fitting: Linear regression y = m x + q to binned values; no sampler or priors stated [Table 3: "We fit a linear regression of the form $y = mx+q$."]
  - validation: Compared single, broken and two-component power laws via reduced chi2 [Appendix: Comparing different R21 Fitti…: "the simple power law prescription is used."]
- step 6: Assess impact of R21 on KS relation and depletion time
  - method: Compare KS index and depletion time from CO(1-0) vs CO(2-1) with fixed R21 [5.1: "we fit the relation to the same points when using the CO(2-1) measurements and a fixed $R_{21}$."]
  - assumption: Radially varying alpha_CO (Bolatto2013/Sun2022); alpha_CO(1-0)=4.35 for sensitivity estimate [5.1: "we use a radially varying CO-to-H$_2$ conversion factor based on the prescription from (cite: Bolatto2013)"]
- result: Galaxy-to-galaxy scatter (ALMA) vs single-dish = 0.05 dex vs 0.11 dex ± not stated dex [4.1.1: "we find a scatter of 0.05 dex for our ALMA-based observations vs. 0.11 dex for the single-dish sample"]
- result: Slope of log R21 vs log Σ_SFR (binned medians) = 0.12 ± +0.03/-0.04 dimensionless [4.1.2: "a slope of $m{=}0.12^{+0.03}_{-0.04}$ or $m{=}0.10^{+0.02}_{-0.02}$"]
- result: Slope of log R21 vs log sSFR (binned) = 0.14 ± ±0.03 dimensionless [4.1.2: "yields a slope of $m{=}0.14^{+0.03}_{-0.03}$"]
- result: Radial slope of R21 (median) = -0.017 ± +0.006/-0.01 per kpc [Table 3: "$-0.017^{+0.006}_{-0.01}$"]
- result: Metallicity slope = -1.1 ± +0.8/-0.6 dimensionless [4.1.2: "yields a negative slope of $m=-1.1^{+0.8}_{-0.6}$"]
- result: KS index change CO(1-0) to CO(2-1), all sightlines = 0.80 to 0.78 ± not stated dimensionless [5.1: "the KS index only changes by $-2\%$, from $N_{10}{=}0.80$ to $N_{21}{=}0.78$"]
- result: R21 vs stellar mass relation = log R21 = -0.07 log M* + 0.57 ± ±0.02 (slope), ±0.09 (intercept) dimensionless [5.2: "-0.07{\pm}0.02 \log_{10}\left(\frac{M_*^{\rm gal}}{M_\odot}\right) + 0.57{\pm}0.09"]
- limitation (authors): Small sample; individual outliers can affect galaxy-to-galaxy trends [4.1.1: "Given the small number of galaxies within our sample, we caution, however, that individual outliers can affect the observed trends."]
- limitation (authors): Metallicity covers only ~0.25 dex and 8 galaxies [4.1.2: "we only cover a small dynamical range of metallicities (${\sim}$0.25 dex)"]
- not stated (card): Exact bin edges and bin widths for r_gal, SFR surface density, sSFR and metallicity; Regression method for binned fits and how the uncertainties on m and q were derived; Details of the fit to all sightlines (slope 0.11) and treatment of uncertainties; Spectral setup, channel width and line-free channels for the CO(1-0) cubes; Robust weighting, cell size and image size used by the PHANGS pipeline;…

### 2019PASJ...71...44H: Formation of high-mass stars in an isolated environment in the Large Magellanic Cloud (2019; star_formation, nearby_galaxies; observational_alma_primary)
- question: What are the distribution and basic physical properties of the natal gas around high-mass YSOs in isolated environments in the LMC?
- step 4: Star formation efficiency
  - method: SFE = Mecl/(Mecl+Mcloud), with Mecl from the mmax-Mecl relation [Star Formation Efficiency: "SFE = \frac{M_{\mathrm{ecl}}}{M_{\mathrm{ecl}} + M_{\mathrm{cloud}}}"]
  - assumption: Weidner13 mmax-Mecl relation [Star Formation Efficiency: "the masses of the star cluster associated with the isolated high-mass YSOs range from 110 to 310$\;$$M_{\odot}$"]
- result: Star formation efficiency range = 4 to 43 ± not stated % [Star Formation Efficiency: "they range from 4 to 43%"]
- limitation (authors): SFE is an upper limit; CO-dark gas possible [Star Formation Efficiency: "We note that this SFE is an upper limit because a part of the natal clouds may have been already dissipated away"]
- not stated (card): CASA version and calibration/imaging pipeline; tclean weighting, robust, cell and image size; line-free channels and continuum subtraction; exact beam sizes per target (in table not reproduced); LVG code and grid parameters; target coordinates; noise threshold values (sigma) used for the clump masks

### 2015MNRAS.453L..83M: ALMA and Herschel reveal that X-ray-selected AGN and main-sequence galaxies have different star formation rate distributions (2015; nearby_galaxies, agn_and_quasars, high_z_galaxies; observational_alma_primary)
- question: Do X-ray selected AGN hosts have the same SFR distribution relative to the main sequence as normal star-forming galaxies?
- step 3: convert fluxes to L_IR and SFR
  - method: MS-galaxy average IR SEDs (Bethermin15, Draine07 templates), then Kennicutt98 relation; R_MS=SFR/SFR_MS [3 ALMA observations and data analysis: "converted to 8-1000 ${\rm \mu m}$ infrared luminosities (hereafter, $L_{\rm IR}$) using our adopted redshifts (see §2)"]
  - assumption: L_IR accurate to ±0.3 dex from SED template range, included in analysis; Chabrier IMF [3 ALMA observations and data analysis: "we estimate that the corresponding $L_{\rm IR}$ are accurate to within $\pm0.3$ dex, which we factor into our analyses"]
  - validation: Conclusions unchanged with Chary01 or Arp220 SEDs; ALMA and Herschel SFRs consistent for four sources detected by both [3 ALMA observations and data analysis: "our conclusions do not change if we instead use either the (cite: Chary01) SEDs or a starburst SED (i.e., Arp220)"]
- result: Fraction of combined AGN with R_MS<0.5 = 34 to 55 per cent (54-88 of 159) ± range from upper limits per cent [4.1 Star-forming properties of X-ray AG…: "We find that 54 to 88 (range due to upper limits) of the 159 AGNs (i.e., $\approx$34 to $\approx$55 per cent) in our combined"]
- limitation (authors): Log-normal is not a literal description of the true AGN distribution [4.2 Parameterising an X-ray AGN SFR dis…: "is not to be taken as a literal description of the true AGN $R_{\rm MS}$ distribution"]
- not stated (card): CASA version and calibration/imaging procedure (pipeline vs manual, weighting, cell, beam); Archive reduced products or how visibilities were calibrated for GILDAS uv_fit; Source positions/priors used in uv_fit and which sources were point vs Gaussian; Prior forms and widths, chain length and convergence criteria for the hierarchical MCMC; How upper limits and L_IR uncertainties enter the likelih…

## All papers in this technique

- 2012ApJ...760L..25E (2012): Giant Molecular Clouds and Star Formation in the Tidal Molecular Arm of NGC 4039
- 2013ApJ...767..132H (2013): ALMA Observations of SPT-discovered, Strongly Lensed, Dusty, Star-forming Galaxies
- 2013ApJ...770...13W (2013): Redshift 6.4 Host Galaxies of 10<SUP>8</SUP> Solar Mass Black Holes: Low Star Formation Rate and Dynamical Mass
- 2014A&A...562A..67G (2014): ALMA reveals a warm and compact starburst around a heavily obscured supermassive black hole at z = 4.75
- 2014A&A...568A..92M (2014): Herschel-ATLAS and ALMA. HATLAS J142935.3-002836, a lensed major merger at redshift 1.027
- 2014ApJ...783...84S (2014): The Evolution of Interstellar Medium Mass Probed by Dust Emission: ALMA Observations at z = 0.3-2
- 2014ApJ...790..160S (2014): ALMA Observations of a Candidate Molecular Outflow in an Obscured Quasar
- 2014ApJ...792...34O (2014): ALMA Observation of 158 μm [C II] Line and Dust Continuum of a z = 7 Normally Star-forming Galaxy in the Epoch of Reionization
- 2015A&A...584A..78C (2015): ALMA constraints on the faint millimetre source number counts and their contribution to the cosmic infrared background
- 2015ApJ...809...93D (2015): Observational Signatures of Planets in Protoplanetary Disks I. Gaps Opened by Single and Multiple Young Planets in Disks
- 2015ApJ...810...91H (2015): Optical-Infrared Properties of Faint 1.3 mm Sources Detected with ALMA
- 2015ApJ...810..133I (2015): Compact Starbursts in z ∼ 3-6 Submillimeter Galaxies Revealed by ALMA
- 2015ApJ...813...45L (2015): Radio Jet Feedback and Star Formation in Heavily Obscured, Hyperluminous Quasars at Redshifts ∼ 0.5-3. I. ALMA Observations
- 2015ApJ...813..118M (2015): Microwave Continuum Emission and Dense Gas Tracers in NGC 3627: Combining Jansky VLA and ALMA Observations
- 2015ApJ...815..103B (2015): Dense Gas Fraction and Star-formation Efficiency Variations in the Antennae Galaxies
- 2015MNRAS.448.2224C (2015): Constraining globular cluster formation through studies of young massive clusters - V. ALMA observations of clusters in the Antennae
- 2015MNRAS.449..715W (2015): Tracing the conversion of gas into stars in Young Massive Cluster Progenitors
- 2015MNRAS.452...54M (2015): The assembly of `normal' galaxies at z ∼ 7 probed by ALMA
- 2015MNRAS.453L..83M (2015): ALMA and Herschel reveal that X-ray-selected AGN and main-sequence galaxies have different star formation rate distributions
- 2016A&A...586A..45S (2016): Star formation efficiency along the radio jet in Centaurus A
- 2016A&A...586L...7B (2016): An ALMA view of the interstellar medium of the z = 4.77 lensed starburst SPT-S J213242-5802.9
- 2016ApJ...819...82S (2016): Properties of the Interstellar Medium in Star-Forming Galaxies at z ~ 1.4 Revealed with ALMA
- 2016ApJ...823...26E (2016): High Star Formation Rates in Turbulent Atomic-dominated Gas in the Interacting Galaxies IC 2163 and NGC 2207
- 2016ApJ...827L..32B (2016): Sub-kiloparsec ALMA Imaging of Compact Star-forming Galaxies at z ~ 2.5: Revealing the Formation of Dense Galactic Cores in the Progenitors…
- 2016ApJ...828...56W (2016): Discovery of a Galaxy Cluster with a Violently Starbursting Core at z = 2.506
- 2016ApJ...833...12R (2016): VLA and ALMA Imaging of Intense Galaxy-wide Star Formation in z ∼ 2 Galaxies
- 2016ApJ...833...68A (2016): The ALMA Spectroscopic Survey in the Hubble Ultra Deep Field: Continuum Number Counts, Resolved 1.2 mm Extragalactic Background, and Proper…
- 2016ApJ...833..112S (2016): Gas Fraction and Depletion Time of Massive Star-forming Galaxies at z ~ 3.2: No Change in Global Star Formation Process out to z &gt; 3
- 2016ApJ...833..195W (2016): The SXDF-ALMA 2-arcmin<SUP>2</SUP> Deep Survey: Stacking Rest-frame Near-infrared Selected Objects
- 2016MNRAS.457.4536W (2016): Comparing young massive clusters and their progenitor clouds in the Milky Way
- 2016MNRAS.457L.122H (2016): ALMA resolves extended star formation in high-z AGN host galaxies
- 2016PASJ...68..103F (2016): A massive dense gas cloud close to the nucleus of the Seyfert galaxy NGC 1068
- 2017A&A...599A.134S (2017): The ALMA Redshift 4 Survey (AR4S). I. The massive end of the z = 4 main sequence of galaxies
- 2017A&A...602A..11P (2017): ALMA reveals starburst-like interstellar medium conditions in a compact star-forming galaxy at z 2 using [CI] and CO
- 2017A&A...602L...9M (2017): On the Kennicutt-Schmidt scaling law of submillimetre galaxies
- 2017A&A...604A.117C (2017): Planck's dusty GEMS. IV. Star formation and feedback in a maximum starburst at z = 3 seen at 60-pc resolution
- 2017A&A...605A..42C (2017): Extended ionised and clumpy gas in a normal galaxy at z = 7.1 revealed by ALMA
- 2017A&A...606A..17M (2017): An ALMA survey of submillimetre galaxies in the COSMOS field: Physical properties derived from energy balance spectral energy distribution …
- 2017ApJ...834....6S (2017): Merger-induced Shocks in the Nearby LIRG VV 114 through Methanol Observations with ALMA
- 2017ApJ...834..135T (2017): Bulge-forming Galaxies with an Extended Rotating Disk at z ~ 2
- 2017ApJ...835...98U (2017): ALMA Deep Field in SSA22: Source Catalog and Number Counts
- 2017ApJ...835..174S (2017): Spatially resolved CO SLED of the Luminous Merger Remnant NGC 1614 with ALMA
- 2017ApJ...835..278S (2017): Physical Properties of Molecular Clouds at 2 pc Resolution in the Low-metallicity Dwarf Galaxy NGC 6822 and the Milky Way
- 2017ApJ...836L...2B (2017): ALMA [C II] 158 μm Detection of a Redshift 7 Lensed Galaxy behind RXJ1347.1-1145
- 2017ApJ...838..146L (2017): ALMA Observations of the Interaction of a Radio Jet with Molecular Gas in Minkowski's Object
- 2017ApJ...842L..16L (2017): ALMA [N II] 205 μm Imaging Spectroscopy of the Interacting Galaxy System BRI 1202-0725 at Redshift 4.7
- 2017ApJ...842L..21N (2017): ALMA Observations of Gas-rich Galaxies in z ∼ 1.6 Galaxy Clusters: Evidence for Higher Gas Fractions in High-density Environments
- 2017ApJ...844..123F (2017): The Circumgalactic Medium of Submillimeter Galaxies. II. Unobscured QSOs within Dusty Starbursts and QSO Sightlines with Impact Parameters …
- 2017ApJ...844L..10S (2017): An Imperfectly Passive Nature: Bright Submillimeter Emission from Dust-obscured Star Formation in the z = 3.717 “Passive” System, ZF 20115
- 2017ApJ...846..108C (2017): A Spatially Resolved Study of Cold Dust, Molecular Gas, H II Regions, and Stars in the z = 2.12 Submillimeter Galaxy ALESS67.1
- 2017ApJ...849...90S (2017): Evolution of Molecular Clouds in the Superwind Galaxy NGC 1808 Probed by ALMA Observations
- 2017ApJ...849..154S (2017): ALMA Pinpoints a Strong Overdensity of U/LIRGs in the Massive Cluster XCS J2215 at z = 1.46
- 2017ApJ...850...54C (2017): ALMA CO(3-2) Observations of Star-forming Filaments in a Gas-poor Dwarf Spheroidal Galaxy
- 2017ApJ...851...18L (2017): SDSS-IV MaNGA-resolved Star Formation and Molecular Gas Properties of Green Valley Galaxies: A First Look with ALMA and MaNGA
- 2017ApJ...851..145M (2017): ALMA Reveals Metals yet No Dust within Multiple Components in CR7
- 2017MNRAS.465.4390B (2017): The discovery of gas-rich, dusty starbursts in luminous reddened quasars at z ∼ 2.5 with ALMA
- 2017MNRAS.468L..87C (2017): New ALMA constraints on the star-forming interstellar medium at low metallicity: a 50 pc view of the blue compact dwarf galaxy SBS 0335-052
- 2017MNRAS.469.4683C (2017): ALMA constraints on star-forming gas in a prototypical z = 1.5 clumpy galaxy: the dearth of CO(5-4) emission from UV-bright clumps
- 2017MNRAS.472.1239B (2017): Tests of star formation metrics in the low-metallicity galaxy NGC 5253 using ALMA observations of H30α line emission
- 2018A&A...615A..94F (2018): Fragmentation properties of massive protocluster gas clumps: an ALMA study
- 2018A&A...616A.110E (2018): Starbursts in and out of the star-formation main sequence
- 2018A&A...617A..82B (2018): The WISSH quasars project. V. ALMA reveals the assembly of a giant galaxy around a z = 4.4 hyper-luminous QSO
- 2018ApJ...853..149S (2018): Revisiting the Extended Schmidt Law: The Important Role of Existing Stars in Regulating Star Formation
- 2018ApJ...854...97D (2018): An ALMA [C II] Survey of 27 Quasars at z &gt; 5.94
- 2018ApJ...854L...4R (2018): Cospatial Star Formation and Supermassive Black Hole Growth in z ∼ 3 Galaxies: Evidence for In Situ Co-evolution
- 2018ApJ...855L..25K (2018): Core Emergence in a Massive Infrared Dark Cloud: A Comparison between Mid-IR Extinction and 1.3 mm Emission
- 2018ApJ...856...72O (2018): An Extreme Protocluster of Luminous Dusty Starbursts in the Early Universe
- 2018ApJ...856..118H (2018): Molecular Gas Reservoirs in Cluster Galaxies at z = 1.46
- 2018ApJ...856L..12N (2018): Molecular Emission from a Galaxy Associated with a z ∼ 2.2 Damped Lyα Absorber
- 2018ApJ...858...90G (2018): Dense Gas, Dynamical Equilibrium Pressure, and Star Formation in Nearby Star-forming Galaxies
- 2018ApJ...859...12G (2018): The Dust and [C II] Morphologies of Redshift ∼4.5 Sub-millimeter Galaxies at ∼200 pc Resolution: The Absence of Large Clumps in the Interst…
- 2018ApJ...860..103S (2018): Molecular Gas Contents and Scaling Relations for Massive, Passive Galaxies at Intermediate Redshifts from the LEGA-C Survey
- 2018ApJ...861....7F (2018): ALMA 26 Arcmin<SUP>2</SUP> Survey of GOODS-S at One Millimeter (ASAGAO): Average Morphology of High-z Dusty Star-forming Galaxies in an Exp…
- 2018ApJ...861L..18U (2018): Star Formation Efficiency per Free-fall Time in nearby Galaxies
- 2018ApJ...862...64S (2018): Deciphering the Activity and Quiescence of High-redshift Cluster Environments: ALMA Observations of Cl J1449+0856 at z = 2
- 2018ApJ...863..129S (2018): Spatially Resolved Dense Molecular Gas Excitation in the Nearby LIRG VV 114
- 2018ApJ...863..193V (2018): Molecular Gas Filaments and Star-forming Knots Beneath an X-Ray Cavity in RXC J1504-0248
- 2018ApJ...864...38L (2018): CO (7-6), [C I] 370 μm, and [N II] 205 μm Line Emission of the QSO BRI 1335-0417 at Redshift 4.407
- 2018ApJ...867..140L (2018): Resolving Star Formation on Subkiloparsec Scales in the High-redshift Galaxy SDP.11 Using Gravitational Lensing
- 2018MNRAS.474.4039M (2018): ALMA + VLT observations of a damped Lyman-α absorbing galaxy: massive, wide CO emission, gas-rich but with very low SFR
- 2018MNRAS.475.1288S (2018): Identifying the subtle signatures of feedback from distant AGN using ALMA observations and the EAGLE hydrodynamical simulations
- 2018MNRAS.476..122V (2018): An ALMA view of star formation efficiency suppression in early-type galaxies after gas-rich minor mergers
- 2018MNRAS.477.4380S (2018): Testing star formation laws in a starburst galaxy at redshift 3 resolved with ALMA
- 2018MNRAS.478.1170C (2018): Kiloparsec-scale gaseous clumps and star formation at z = 5-7
- 2018MNRAS.481.1631B (2018): Obscured star formation in bright z ≃ 7 Lyman-break galaxies
- 2018PASJ...70L...6K (2018): A high dust emissivity index β for a CO-faint galaxy in a filamentary Lyα nebula at z = 3.1
- 2019A&A...621A..27F (2019): Massive galaxies on the road to quenching: ALMA observations of powerful high redshift radio galaxies
- 2019A&A...623A..66B (2019): ALMA CO(2-1) observations in the XUV disk of M83
- 2019AJ....157..131B (2019): Kiloparsec-Scale Variations in the Star Formation Efficiency of Dense Gas: The Antennae Galaxies (NGC 4038/39)
- 2019ApJ...870...39V (2019): ALMA Observations of the Molecular Gas in the Elliptical Galaxy NGC 3557
- 2019ApJ...874...53B (2019): Environmental Effect on the Interstellar Medium in Galaxies across the Cosmic Web at z = 0.73
- 2019ApJ...876...99S (2019): Star Formation and ISM Properties in the Host Galaxies of Three Far-infrared Luminous Quasars at z ∼ 6
- 2019ApJ...876..112R (2019): Strong Far-ultraviolet Fields Drive the [C II]/Far-infrared Deficit in z ∼ 3 Dusty, Star-forming Galaxies
- 2019ApJ...876..130H (2019): ALMA Reveals Potential Evidence for Spiral Arms, Bars, and Rings in High-redshift Submillimeter Galaxies
- 2019ApJ...877L..38R (2019): Active Galactic Nuclei in Dusty Starbursts at z = 2: Feedback Still to Kick in
- 2019ApJ...881...63N (2019): An ALMA Multiline Survey of the Interstellar Medium of the Redshift 7.5 Quasar Host Galaxy J1342+0928
- 2019ApJ...881..124M (2019): Resolved UV and [C II] Structures of Luminous Galaxies within the Epoch of Reionization
- 2019ApJ...881..147S (2019): Positive and Negative Feedback of AGN Outflows in NGC 5728
- 2019ApJ...882....5W (2019): The Kennicutt-Schmidt Law and Gas Scale Height in Luminous and Ultraluminous Infrared Galaxies
- 2019ApJ...882...10N (2019): Resolved [C II] Emission from z &gt; 6 Quasar Host-Companion Galaxy Pairs
- 2019ApJ...882..136A (2019): The ALMA Spectroscopic Survey in the Hubble Ultra Deep Field: Evolution of the Molecular Gas in CO-selected Galaxies
- 2019ApJ...882..137P (2019): The ALMA Spectroscopic Survey in the HUDF: the Molecular Gas Content of Galaxies and Tensions with IllustrisTNG and the Santa Cruz SAM
- 2019ApJ...884L..33L (2019): The ALMaQUEST Survey: The Molecular Gas Main Sequence and the Origin of the Star-forming Main Sequence
- 2019ApJ...885L..21M (2019): How to Fuel an AGN: Mapping Circumnuclear Gas in NGC 6240 with ALMA
- 2019ApJ...887...74F (2019): ALMA Reveals a Gas-rich, Maximum Starburst in the Hyperluminous, Dust-obscured Quasar W0533-3401 at z ∼ 2.9
- 2019ApJ...887...88E (2019): Star Formation Efficiencies at Giant Molecular Cloud Scales in the Molecular Disk of the Elliptical Galaxy NGC 5128 (Centaurus A)
- 2019ApJ...887..144J (2019): Discovery of Four Apparently Cold Dusty Galaxies at z = 3.62-5.85 in the COSMOS Field: Direct Evidence of Cosmic Microwave Background Impac…
- 2019ApJ...887..183Z (2019): On the Gas Content, Star Formation Efficiency, and Environmental Quenching of Massive Galaxies in Protoclusters at z ≈ 2.0-2.5
- 2019MNRAS.485.1595P (2019): Multiphase circumgalactic medium probed with MUSE and ALMA
- 2019MNRAS.485.2092C (2019): Suppressed CO emission and high G/D ratios in z = 2 galaxies with sub-solar gas-phase metallicity
- 2019MNRAS.486..560S (2019): Passive galaxies in the early Universe: ALMA confirmation of z ∼ 3-5 candidates in the CANDELS GOODS-South field
- 2019MNRAS.487.4305S (2019): Testing star formation laws on spatially resolved regions in a z ≈ 4.3 starburst galaxy
- 2019MNRAS.489..427I (2019): Hyperluminous starburst gives up its secrets
- 2019Natur.569..519K (2019): Fast and inefficient star formation due to short-lived molecular clouds and rapid feedback
- 2019PASJ...71...40T (2019): Environmental impacts on molecular gas in protocluster galaxies at z ∼ 2
- 2019PASJ...71...44H (2019): Formation of high-mass stars in an isolated environment in the Large Magellanic Cloud
- 2020A&A...635A...2S (2020): Physical properties of the star-forming clusters in NGC 6334. A study of the continuum dust emission with ALMA
- 2020A&A...635A.119C (2020): Extended Hα over compact far-infrared continuum in dusty submillimeter galaxies. Insights into dust distributions and star-formation rates …
- 2020A&A...641A.151S (2020): Molecular gas in the central region of NGC 7213
- 2020A&A...641A.155V (2020): CO emission in distant galaxies on and above the main sequence
- 2020A&A...642A.155Z (2020): GOODS-ALMA: Optically dark ALMA galaxies shed light on a cluster in formation at z = 3.5
- 2020A&A...643A...6C (2020): The ALPINE-ALMA [CII] survey. Small Lyα-[CII] velocity offsets in main-sequence galaxies at 4.4 &lt; z &lt; 6
- 2020ApJ...889....9M (2020): GASP. XXII. The Molecular Gas Content of the JW100 Jellyfish Galaxy at z ∼ 0.05: Does Ram Pressure Promote Molecular Gas Formation?
- 2020ApJ...897L..30M (2020): The High Molecular Gas Content, and the Efficient Conversion of Neutral into Molecular Gas, in Jellyfish Galaxies
- 2020ApJ...901...79A (2020): The ALMA Spectroscopic Survey in the Hubble Ultra Deep Field: The Nature of the Faintest Dusty Star-forming Galaxies
- 2020ApJ...903..145L (2020): ALMaQUEST. IV. The ALMA-MaNGA QUEnching and STar Formation (ALMaQUEST) Survey
- 2020ApJS..247...61F (2020): The ALPINE-ALMA [C II] Survey: Multiwavelength Ancillary Data and Basic Physical Measurements
- 2020ApJS..251...14H (2020): CMZoom. II. Catalog of Compact Submillimeter Dust Continuum Sources in the Milky Way's Central Molecular Zone
- 2020MNRAS.491.4724F (2020): A3COSMOS: the dust attenuation of star-forming galaxies at z = 2.5-4.0 from the COSMOS-ALMA archive
- 2020MNRAS.494.3828D (2020): An ALMA survey of the SCUBA-2 CLS UDS field: physical properties of 707 sub-millimetre galaxies
- 2020MNRAS.495.3840M (2020): A large amount of diffuse molecular gases in the bar of the strongly barred galaxy NGC 1300: cause of the low star formation efficiency
- 2020MNRAS.497.2771M (2020): VALES VI: ISM enrichment in star-forming galaxies up to z ∼ 0.2 using <SUP>12</SUP>CO(1-0), <SUP>13</SUP>CO(1-0), and C<SUP>18</SUP>O(1-0) …
- 2020MNRAS.499..193K (2020): Measuring the mixing scale of the ISM within nearby spiral galaxies
- 2020NatAs...4..670A (2020): Infalling gas in a Lyman-α blob
- 2021A&A...645A.120F (2021): ALMA and MUSE observations reveal a quiescent multi-phase circumgalactic medium around the z ≃ 3.6 radio galaxy 4C 19.71
- 2021A&A...652A..30S (2021): The emergence of passive galaxies in the early Universe
- 2021A&A...656A..60A (2021): Black hole feeding and star formation in NGC 1808
- 2021A&A...656A.133Q (2021): Stellar structures, molecular gas, and star formation across the PHANGS sample of nearby galaxies
- 2021ApJ...908...54W (2021): ALMA Measures Rapidly Depleted Molecular Gas Reservoirs in Massive Quiescent Galaxies at z ∼ 1.5
- 2024A&A...682A..54T (2024): HYPERION. Interacting companion and outflow in the most luminous z &gt; 6 quasar
- 2024A&A...685A..80Z (2024): Unveiling [C II] clumps in a lensed star-forming galaxy at z ∼ 3.4
- 2024A&A...692A.215C (2024): Molecular gas budget of strongly magnified low-mass star-forming galaxies at cosmic noon
- 2024ApJ...964...18C (2024): Resolved Measurements of the CO-to-H<SUB>2</SUB> Conversion Factor in 37 Nearby Galaxies
- 2024ApJ...972..147C (2024): Comparisons between Resolved Star Formation Rate and Gas Tracers in the Strongly Lensed Galaxy SDSS J0901+1814 at Cosmic Noon
- 2024ApJ...976...70L (2024): The ALMA-CRISTAL Survey: Spatially Resolved Star Formation Activity and Dust Content in 4 &lt; z &lt; 6 Star-forming Galaxies
- 2024ApJ...976...88L (2024): Disk Turbulence and Star Formation Regulation in High-z Main-sequence Analog Galaxies
- 2024ApJ...977L...6F (2024): The Impact of Shear on Disk Galaxy Star Formation Rates
- 2025A&A...695A...6P (2025): GA-NIFS: Multiphase analysis of a star-forming galaxy at z ∼ 5.5
- 2025A&A...698A.204H (2025): An ALMA spectroscopic survey of the Planck high-redshift object PLCK G073.4−57.5 confirms two protoclusters
- 2025A&A...698A.296R (2025): The impact of spiral arms on the star formation life cycle
- 2025A&A...700A.285W (2025): Gravitational torques from lopsided young stellar component sustain high black hole accretion rates in NGC 4593
- 2025ApJ...988..135M (2025): The Physical Properties and Morphologies of Faint Dusty Star-forming Galaxies Identified with JWST
- 2025ApJ...988..162D (2025): Constraining Resolved Extragalactic R<SUB>21</SUB> Variation with Well-calibrated ALMA Observations
- 2025ApJ...990..221M (2025): Spatially and Dynamically Extended Molecular Gas in Stephan's Quintet Revealed by ALMA CO(1─0) Total Power Mapping
- 2025ApJ...994....4A (2025): Enhanced Gas-phase Metallicities and Suppressed Outflows for Galaxies in a Rich Cluster Core at Cosmic Noon
- 2025ApJ...995..151Y (2025): Molecular Gas and Star Formation in Dwarf Galaxies Observed by the Atacama Large Millimeter/submillimeter Array
- 2026A&A...705A..39P (2026): High-z [OI] emission lines: COLDSIM simulations and ALMA observations
- 2026A&A...705A..81K (2026): Resolving the molecular gas emission of the z ∼ 2.5─2.8 starburst galaxies SPT 0125-47 and SPT 2134-50
- 2026ApJ..1001..131C (2026): MAGAZ3NE: Far-IR and Radio Insights into the Nature and Properties of Ultramassive Galaxies at z ≳ 3
- 2026ApJ..1003...52D (2026): Molecular Gas Excitation in z ∼ 0.7 Gas-rich Poststarburst Galaxies from SQuIGG<inline-formula> <mml:math><mml:mover><mml:mrow><mml:mi>L</m…
