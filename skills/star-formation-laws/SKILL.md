---
name: alma-star-formation-laws
description: "Relate ALMA gas measurements to star formation the way published ALMA papers do: build Sigma_SFR and Sigma_gas (molecular, dense or total) on matched apertures or pixels, fit Kennicutt-Schmidt slopes, and compute depletion times, SFE, dense-gas SFE and efficiency per free-fall time. Use when placing galaxies, regions, clumps or lensed sources on the KS plane, quoting t_dep = M_gas/SFR, comparing to Kennicutt 1998 or Bigiel 2008, fitting a resolved star formation law, splitting SFR offsets into SFE and gas-fraction terms, or checking someone else's depletion time or KS slope. Built from 414 ALMA papers (2012-2026)."
---

# Star formation laws and depletion times

Measures how fast gas turns into stars: Sigma_SFR versus Sigma_gas (the Kennicutt-Schmidt, KS, relation),
its slope N, and the ratios t_dep = M_gas/SFR = 1/SFE and eps_ff = t_ff/t_dep. Every quantity is a ratio of
two calibrated maps or totals, so the mistakes that matter most are convention mismatches, not noise:
(1) SFR and gas built with different IMFs, alpha_CO, helium or area conventions (each a factor of 1.36 to about 5;
one z = 4.3 galaxy's t_dep runs from 23 to 140 Myr across five gas estimators, 2025A&A...694A.218B), and
(2) a slope that reflects the S/N cut, the fitting method, the region or the alpha_CO prescription rather than the
physics (constant vs variable alpha_CO moved one resolved slope from 0.90 to 1.23, 2024ApJ...976...88L;
component slopes in one merger span 0.15 to 0.98, 2025ApJ...979..217S).

> Always report: SFR tracer and calibration coefficient (with IMF), alpha_CO (and r_J1) with helium convention,
> the area definition (pi R_e^2 with half the SFR, aperture, pixel, beam), resolution in pc, inclination
> treatment, S/N cuts and how limits enter, and the regression method. A KS slope or t_dep without these cannot be
> compared to anything.

Gas masses themselves (L' to M_H2, choosing alpha_CO, r_J1, [CI], dust-based gas) are covered by the sibling
skill `alma-gas-mass-co-conversion` (`../gas-mass-co-conversion/SKILL.md`). Use it for the gas side and do not
re-derive alpha_CO here. Coefficients, sampling setups and published results are tabulated in
`references/parameters.md`.

Counts are from the rebuilt evidence pack (414 papers): software from its aggregates, everything else my count of
unique bibcodes in its aggregate parameter and assumption lines unless stated. The regex also caught papers that
mention an "SFE" only in passing (protoplanetary disks, simulated clumps, a Titan occultation, e.g.
2015ApJ...809...93D, 2025ApJ...995...98D, 2025A&A...701A.219N, 2025PSJ.....6..286M); those are excluded.

## When to use

- Integrated t_dep and SFE for detected galaxies, cluster members, quasar hosts, protocluster or group galaxies
  (2025A&A...698A.204H, 2019PASJ...71...40T, 2021MNRAS.500.3667S, 2025A&A...694A.218B).
- Resolved KS on pixels, beam apertures, hexagons, rings or spaxels in nearby galaxies and mergers
  (2019ApJ...887...88E, 2024ApJ...976...88L, 2025ApJ...979..217S, 2022A&A...663A..61P, 2020MNRAS.496.2155Z).
- Spaxel-level split of SFR offsets into SFE and gas-fraction terms with matched control spaxels
  (2020MNRAS.492.6027E, 2020MNRAS.493L..39E, 2024ApJ...964..120P).
- Global KS placement of compact high-z sources from sizes plus totals (2017A&A...602L...9M, 2020A&A...641A.155V,
  2022A&A...665A...3J); resolved laws in lensed sources after a lens model (2018ApJ...867..140L,
  2020MNRAS.494.5542R).
- Dense-gas laws with HCN or HCO+ (2018ApJ...863..129S, 2015ApJ...813..118M, 2025A&A...693L..13N); eps_ff and
  theory comparisons (2018ApJ...861L..18U, 2023ApJ...945...42B, 2019MNRAS.487.4305S).
- Environmental tests: arms, bars, ram-pressure tails, cluster position, AGN hosts (2021A&A...656A.133Q,
  2020MNRAS.496.2155Z, 2020MNRAS.495.3840M, 2017MNRAS.468.4205K).

## When not to use

- Converting CO, [CI] or dust to gas mass: use `alma-gas-mass-co-conversion`.
- Deriving L_IR or SFR from a full far-IR SED (CIGALE, MAGPHYS, greybody fits): use an SED-fitting skill and
  bring the SFR here. This skill only covers how the SFR enters the law.
- Cloud-scale SFE defined as M_star/(M_star+M_gas) for single clumps, YSO clusters or simulated clumps stopped at a
  set SFE (2019PASJ...71...44H, 2015MNRAS.449..715W, 2018A&A...615A..94F). That is a mass ratio, not a rate; do not
  put it on the KS plane.
- GMC catalogues and virial parameters: use a GMC-decomposition skill. Toomre Q: use a stability skill.

## Steps

1. **Fix conventions before touching data.** One IMF, one alpha_CO convention, one cosmology for both axes.
   Chabrier is the most common IMF (68 papers), then Salpeter (31), Kroupa (18); a paper converting between two
   is counted under both. Salpeter-to-Chabrier SFR factors run from /1.6 (2024ApJ...976...70L) to /1.8
   (2017A&A...604A.117C), with /1.7 most common (2020MNRAS.496..875R, 2021NatAs...5..319P, -0.23 dex in
   2021A&A...654A..90L); Salpeter to Kroupa /1.5 (2019A&A...621A..27F). Pick one factor and state it. Rescale
   literature gas masses to your alpha_CO or X_CO before comparing (2025A&A...698A.204H; 2020MNRAS.496.2155Z;
   2021A&A...655A..42S to a metallicity-dependent alpha_CO).

2. **Build the SFR (or Sigma_SFR) map or total.** Write input and output units next to every calibration;
   `references/parameters.md` marks coefficients whose units are not in the pack, and those units must come from
   the cited paper before you apply the coefficient. Tracer families:
   - IR luminosity or dust continuum. Kennicutt 1998 is named in 32 papers' aggregate lines (count includes its
     H-alpha calibration), Kennicutt and Evans 2012 in 15. Coefficients with units in the pack run from
     SFR [Msun/yr] = 1.7e-10 L_IR/Lsun (2021ApJ...915...46C) to 1.0e-10 L_IR/Lsun with Chabrier
     (2015ApJ...815L...8U); Chabrier values alone span 0.95e-10 (2019A&A...625A..96K) to 1.49e-10
     (2022MNRAS.510.4976A), so quote the coefficient, not only the IMF. Resolved single-band maps scale the SED
     total by each beam's continuum share (2019ApJ...876..130H, 2018Natur.560..613T), assuming one T_dust.
   - H-alpha, Pa-alpha: SFR [Msun/yr] = 4.5e-42 L_Halpha [erg/s] (2020ApJS..247...61F), 5.53e-42
     (2024ApJ...976...88L); Pa-alpha with Calzetti extinction (2021A&A...656A..60A). State the nebular attenuation
     prescription and carry its uncertainty: after a stellar-A_V Calzetti correction, H-alpha SFRs of z~2 SMGs were
     still a median factor 3+-1 below IR SFRs (2020A&A...635A.119C), and the f = 0.44 factor of
     2020ApJS..247...61F gives a likely upper limit on L_Halpha and is its largest uncertainty. Cross-check with an
     obscured tracer before treating corrected H-alpha as the total SFR. In IFU maps keep star-forming spaxels (BPT
     plus EW(Halpha) > 6 A, 2024ApJ...964..120P); retired-spaxel SFRs are upper limits (2024ApJ...963..115L).
   - Hybrids: FUV + 24 um (2012ApJ...760L..25E; units not in pack); H-alpha + WISE 22 um, matching MUSE maps to
     about 0.1 dex (2025ApJ...985...14L); FUV/NUV/12/24 um coefficients K (2018ApJ...861L..18U; units not in pack).
   - Free-free and recombination lines: 3 GHz via Murphy 2012, validated by 3-33 GHz spectral indices and
     q_IR = 2.56 (2025ApJ...979..217S); 93 GHz with a 30% SFR uncertainty (2023ApJ...945...42B); 33 GHz thermal
     fraction 79% (2015ApJ...813..118M); H40alpha (2022MNRAS.510.4998Z). 110 GHz mixes free-free with possible
     synchrotron, about 25% (2018ApJ...863..129S).
   - Mid-IR and PAH (not free-free): Sigma_SFR [Msun/yr/kpc^2] = 3.8e-3 I_21um [MJy/sr] (2025MNRAS.544.4014Z);
     log Sigma_SFR = 0.844 log Sigma_L8 - 30.923 (2019ApJ...887...88E; the intercept depends on units not in the
     pack, so do not apply it without the paper's definitions).
   - Far-IR dust emission (not free-free): linear 160 um to SFR mapping (2019ApJ...876..112R).
   - Quasar and AGN hosts: separate the point source from extended emission and compare continuum and line SFRs
     (Band 5 continuum vs CO(5-4): 953 vs 975 Msun/yr in one quasar, 104 vs 232 in another,
     2026MNRAS.546ag167S), or subtract a fitted AGN fraction (25-60% of L_IR assigned to star formation,
     2024A&A...684A..33K).

3. **Build the gas map or total.** Sigma_mol (or Sigma_dense, Sigma_HI+H2) on the same footprint: moment-0 with
   alpha_CO and r_J1 (see the gas-mass skill), times cos i, helium handled consistently. X_CO converts CO
   intensity to H2 column and carries no helium; the 1.36 factor belongs in alpha_CO or the Sigma coefficient
   (X_CO = 2e20 corresponds to alpha_CO = 4.35 including helium, 2025ApJ...995..151Y). Apply it exactly once.
   - Galactic 4.0-4.87 (or X_CO = 2-2.3e20) in 26 papers (e.g. 2020ApJ...903..145L, 2020MNRAS.493L..39E,
     2026A&A...707A.144S); 2025ApJ...988..162D is not counted because its analysis uses a radially varying
     alpha_CO and 4.35 only for a sensitivity estimate. ULIRG-like 0.6-1.3 in 25 for their own analysis (e.g.
     1.1 for a LIRG merger, 2025ApJ...979..217S; 1.0, 2020MNRAS.494.5542R; 0.6, 2013A&A...559A..29C), plus 2 as
     an alternative or for comparison data only (2024MNRAS.533.2966Q, 2016PASJ...68...20S). 3.6-3.8, often as the
     alternative to 0.8, in 5 (2021MNRAS.507.3998P, 2025A&A...694A.218B). Papers assigning values by galaxy type
     are counted in each class they use (2017MNRAS.469.4683C, 2020MNRAS.497.2771M).
   - Variable alpha_CO in 16 papers: Bolatto 2013 eq. 31 iterated (2024ApJ...976...88L, 2021ApJ...909...12G);
     Z^-1.5 and Sigma_star^-0.25 terms with an R21 that scales with Sigma_SFR (2025ApJ...985...14L,
     2025A&A...693L..13N); Accurso 2017 (2021MNRAS.500.3802H); Genzel 2015 (2024A&A...692A.215C).
   - Dense gas: alpha_HCN = 10 in 5 papers (e.g. 2015ApJ...815..103B, 2018ApJ...863..129S), 14
     (2023MNRAS.521.3348N), 15 (2025A&A...693L..13N); alpha_HCO+ about 10 (2015ApJ...813..118M). Atomic gas:
     Sigma_atom [Msun/pc^2] = 2.0e-2 I_HI [K km/s] cos i, helium included (2024A&A...687A.293Q).
   - Missing flux: correct for it or say you did not: 45% correction (2021A&A...656A..60A); about half recovered
     (2017ApJ...850...54C); gas masses as lower limits (2015ApJ...799...11X); only compact CO counted, assuming
     diffuse CO forms no massive stars (2020MNRAS.493.2872C).
   **Record provenance of both axes and avoid circular tests.** SFR from the Schmidt-Kennicutt law with an assumed
   300 pc disk (2014ApJ...790..160S); gas masses that rely on an assumed main-sequence SFE (2019MNRAS.485.2092C);
   gas surface density taken from the global Sigma_SFR for a Toomre estimate (2019ApJ...876..130H); Sigma_SFR
   turned into Sigma_H2 with the Leroy 2013 relation for controls (2021MNRAS.500.3802H). Flag such points and
   exclude them from any fit or t_dep comparison that tests the same relation. A weaker coupling: an R21 that
   scales with Sigma_SFR puts a Sigma_SFR term into the gas axis, so also report the slope with a fixed R21.

4. **Match resolution and sampling.** Convolve to the coarser beam (Aniano kernels, 2025PASJ...77..616I), regrid
   to about one beam per sample, then measure. Report beam resolution, aperture size (radius or diameter, say
   which) and sampling spacing as three separate numbers. Setups in the pack range from 43 pc pixels
   (2019ApJ...887...88E) and 34 pc-radius apertures (2021A&A...656A..60A) through 150 pc pixels retested up to
   1 kpc (2022A&A...663A..61P) and 500 pc hexagons (2025ApJ...979..217S) to 1 kpc hexagons at 1.5 kpc resolution
   (2021A&A...656A.133Q) and 1.7 kpc resolution (2025ApJ...988..162D); full list in parameters.md.
   - Overlapping samples are not independent. Offset grids (2024ApJ...976...88L), 6'' data on 3'' pixels
     (2012ApJ...760L..25E), 200 pc apertures every 100 pc (2025A&A...700A.285W), every possible grid origin
     (2020MNRAS.496.2155Z) and 25 grid offsets (2021MNRAS.500.3802H) all oversample. Regridding does not create
     independent points: account for the spatial covariance, as 2024MNRAS.535.2538Z does for pixels smaller than
     the beam (or resample in spatial blocks, general practice), and do not count overlapping apertures as
     independent constraints when quoting slope errors.
   - Global compact sources: write both enclosed fractions, Sigma_SFR = f_SFR SFR/A and Sigma_gas = f_gas M_gas/A,
     and measure or justify each. Papers take f_SFR = 1/2 inside the half-light radius, (SFR/2)/(pi R_e^2)
     (2019ApJ...876..130H, 2014A&A...562A..67G, 2022MNRAS.510.4976A), or SFR/(2 pi R^2) with R = FWHM/2
     (2020A&A...641A.155V, 2022A&A...665A...3J); 2017A&A...602L...9M (card, section 3 "Data analysis") and
     2017MNRAS.470.3775V (two-sided disk, 2 pi R_FWHM^2) halve both SFR and M_gas. A dust-continuum half-light
     radius encloses half the continuum-traced SFR, not necessarily half the gas: use the gas tracer's own size or
     state the assumption (2017MNRAS.470.3775V takes unresolved CO radii as optical Petrosian radius / 1.6).
   - Validate sizes before trusting a global Sigma: deconvolve from the beam, propagate the size error into the area
     (A scales as R^2), and keep a Sigma lower limit when unresolved. The pack shows why: a sparse-uv size giving
     only Sigma_SFR > 26 (2014A&A...562A..67G); a poorly constrained marginal size (2013ApJ...770...13W); sizes
     biased high at S/N < 10 (2017ApJ...844..123F); plotted errors without the size term (2025A&A...701A..85K).
   - Inclination: cos i (2025ApJ...995..151Y, 2022A&A...663A..61P); 1/cos i from the fitted ellipticity
     (2021MNRAS.500.3802H); fixed 70 deg (2019ApJ...887...88E); 45+-15 deg when the axis ratio is unconstrained
     (2021MNRAS.500.3667S); none (2019ApJ...882....5W).

5. **Apply detection cuts and keep limits.** CO S/N > 2 per spaxel (2017ApJ...851...18L, 2019ApJ...884L..33L);
   S/N > 3 in H-alpha and CO (2022MNRAS.514.5035L); > 3 sigma in one tracer and > 1 sigma in the other
   (2024MNRAS.535.1533B); 2 sigma gas cut (2024ApJ...972..147C); only Sigma_* bins with > 60% detected pixels
   (2022A&A...663A..61P). State the completeness floor, e.g. Sigma_mol about 4 Msun/pc^2 at 3 sigma over 10 km/s
   (2019ApJ...887...88E). Remove AGN-dominated pixels before fitting (19 removed, 2019ApJ...887...88E; inside
   0.5 R_e in LINER/AGN hosts, 2024ApJ...962...88V); a D4000-based Sigma_SFR for AGN and retired spaxels trades
   accuracy for completeness (2024ApJ...964..120P). Dropping all non-detections (2026A&A...707A.144S) truncates
   the sample (Step 6).

6. **Fit the relation.** log Sigma_SFR = N log Sigma_gas + C. Methods seen (aggregates plus pack lines): Kelly
   2007 Bayesian regression via linmix / LINMIX_ERR with errors on both axes and censored points
   (2018ApJ...863..193V, 2020A&A...641A.155V, 2025ApJ...979..217S); scipy ODR (2024ApJ...976...88L,
   2019ApJ...887...88E); ASURV survival analysis (2025ApJ...979..217S); a hierarchical Bayesian fit with NUTS,
   centred variables, one normalisation and a shared intrinsic scatter across environments (2022A&A...663A..61P);
   OLS per galaxy (2025ApJ...995..151Y); linear fits to binned means (R21 trends, 2025ApJ...988..162D); Gaussian
   mixtures with scikit-learn chosen by BIC (2019ApJ...887...88E) or AIC and BIC (2025ApJ...979..217S). From
   cards: least squares on binned data plus a slope fixed to 1 for SFE (2017A&A...602L...9M, card step 4); double
   power law with free break, 10,000 bootstraps (2019ApJ...882....5W, card step 4). One paper normalises at
   Sigma_H2 = 100 Msun/pc^2 (2018ApJ...863..193V). 2025ApJ...979..217S is the model for reporting: linmix with
   and without upper limits, checked with ODR and ASURV, and N per morphological component.
   Recommendation: fit with errors on both axes and say which axis carries the limits. Kelly 2007 linmix censors
   the dependent variable (general practice); in log Sigma_SFR = N log Sigma_gas + C, CO or gas non-detections
   are limits on the independent variable, so either refit the inverse relation with gas as the dependent
   variable or use a likelihood that handles censoring on x. Never fit limits as detections: the AGN relations
   of 2017MNRAS.468.4205K did so and are only upper limits. Censoring is not the same as selection: points kept
   only where CO is significantly detected (2025ApJ...995..151Y, whose slope moved when 1 sigma points were
   added) or samples with line-luminosity upper limits (2020A&A...641A.155V) are truncated, and that truncation
   has to be modelled or the sample restricted to where it is complete. Quote OLS or ODR alongside if comparing
   to older work.
   Document the parent-sample selection before comparing samples: PACS detection steered one sample to upper
   main-sequence, warm-dust galaxies (2020A&A...641A.155V); N2 selection biased another toward high metallicity
   and gas fraction (2025ApJ...994....4A); requiring FIR and H-alpha detections put an AGN sample on or above the
   main sequence (2020MNRAS.492.3194S). Restrict comparisons to matched selections or model the selection.

7. **Derive t_dep, SFE and eps_ff.** t_dep = M_mol/SFR = 1/SFE (2019MNRAS.485.1595P); per pixel
   t_dep = Sigma_mol/Sigma_SFR, summarised with the median (2024ApJ...976...88L, 2020MNRAS.496.2155Z).
   Mind the area units: with Sigma_mol in Msun/pc^2 and Sigma_SFR in Msun/yr/kpc^2,
   t_dep [yr] = 1e6 Sigma_mol/Sigma_SFR, or t_dep [Gyr] = 1e-3 Sigma_mol/Sigma_SFR (unit arithmetic).
   To ask whether SFR offsets come from SFE or gas fraction, ALMaQUEST computes Delta SFE and Delta f_H2 against
   control spaxels matched within 0.1 dex in Sigma_H2 (or Sigma_*), M_*, O/H and 0.1 R/R_e (2020MNRAS.492.6027E,
   2020MNRAS.493L..39E) and classes radial bins by Delta f_gas - Delta SFE with a +-0.15 band, about twice the
   typical error (2024ApJ...964..120P).
   eps_ff = t_ff/t_dep needs a gas scale height or density model (general practice): 2018ApJ...861L..18U compares
   three H prescriptions to estimate the systematic (card step 3); 2023ApJ...945...42B fixes a 100 pc half depth
   and notes that observed eps_ff depends on the theoretical definition; 2025ApJ...979..217S assumes H = 100 pc and
   filling factor 1 and gets medians of 25% and 42%, far above the 0.015 used in models (2019MNRAS.487.4305S,
   2024MNRAS.52710201E). Theory comparisons use Krumholz-McKee grids (2018ApJ...863..129S), KDM and SFK models
   (2019MNRAS.487.4305S), Krumholz+18 and feedback-regulated models (2024ApJ...976...88L).

8. **Validate** (see Verification checks) and report the conventions box above.

## Parameter defaults and ranges

| parameter | common choice | range seen | papers (count) | examples |
|---|---|---|---|---|
| IMF | Chabrier | Chabrier, Salpeter, Kroupa | 68 / 31 / 18 (unique bibcodes) | 2018MNRAS.477.4380S, 2024ApJ...964..120P, 2025ApJ...979..217S |
| Salpeter to Chabrier SFR factor | /1.7 | /1.6 to /1.8 | 7 | 2020MNRAS.496..875R, 2017A&A...604A.117C |
| IR SFR calibration | Kennicutt 1998 | K98, Kennicutt and Evans 2012 | 32 / 15 (regex over aggregates) | 2019ApJ...881...63N, 2026ApJ..1003..206S |
| alpha_CO (normal disks) | 4.35-4.36 incl. He | 4.0-4.87 (one paper about 7, 2019AJ....157..131B) | 26 (unique bibcodes) | 2020ApJ...903..145L, 2026A&A...707A.144S |
| alpha_CO (starburst, merger, SMG) | 0.8 | 0.6-1.3 | 25 (+2 alternative only) | 2025ApJ...979..217S, 2014ApJ...790..160S |
| alpha_CO (variable) | Z- and Sigma_*-dependent | Bolatto eq. 31, Accurso, Genzel | 16 (unique bibcodes) | 2025ApJ...985...14L, 2021ApJ...909...12G |
| alpha_HCN | 10 | 10-15 | 7 | 2018ApJ...858...90G, 2025A&A...693L..13N |
| Area for global Sigma | (SFR/2)/(pi R_e^2) | R from FWHM/2 or HWHM; 2 pi R^2 two-sided; f_gas often unstated | 8 in pack lines (+1 card) | 2022MNRAS.510.4976A, 2022A&A...665A...3J |
| Resolution of resolved KS | beam-matched | pixels of 43 pc to 1 kpc; 500 pc hexagons; apertures 34 pc radius to 1 kpc hexagons at 1.7 kpc resolution | see Step 4 | 2019ApJ...887...88E, 2022A&A...663A..61P, 2025ApJ...988..162D |
| S/N cut per sample | > 2 to > 3 | 1 to 5 sigma | 9 (pack lines) | 2017ApJ...851...18L, 2024MNRAS.535.1533B |
| Reported SFR uncertainty (paper-specific, not a floor) | none common | 20% to 0.5 dex | 11 (pack lines) | 2019Natur.569..519K, 2020MNRAS.498.1560J, 2020MNRAS.496..875R |
| Dust T for single-band IR SFR | 40-50 K, beta 1.5-1.8 | 25-120 K | many (see parameters.md) | 2026MNRAS.546ag167S, 2017A&A...599A.134S |

The SFR uncertainties are what papers adopted for their own tracer (20% H-alpha, 2019Natur.569..519K; 30% at
93 GHz, 2023ApJ...945...42B; 0.42 dex systematic, 2020MNRAS.498.1560J; 0.5 dex for template choice,
2020MNRAS.496..875R; factor 2 UV, 2018ApJ...863..193V); the pack does not establish a common minimum. Build a
tracer-specific error budget (calibration, attenuation, dust temperature or template, non-stellar contamination,
IMF) instead of borrowing one of these numbers.

Published results to sanity-check against (not targets) are in `references/parameters.md`. In brief: resolved
molecular slopes run from sub-linear (0.52 in a merger, 2025ApJ...979..217S; 0.63, 2019ApJ...887...88E) to 1.23
(2024ApJ...976...88L); a global slope of 1.26 for dusty z < 0.35 galaxies (2017MNRAS.470.3775V); t_dep from
1-20 Myr in a lensed z = 3 DSFG (2020MNRAS.494.5542R) to 3-4 Gyr between spiral arms (2020MNRAS.496.2155Z).

## Software

From the pack aggregates of software named in matched steps (414 papers; counts are small because most papers do
the arithmetic in their own scripts). Counts are name frequencies, not counts of a specific procedure; "used
for" is what the excerpted papers show, not a claim about every mention:

| software | count (aggregates) | used for | examples |
|---|---|---|---|
| CIGALE | 11 | SED SFR and M_star feeding the law | 2025A&A...698A.204H, 2024A&A...692A.215C |
| CASA (+ tclean, gaussfit) | 9 (+1, +1) | imaging, moment maps, apertures, CO sizes | 2024ApJ...976...88L, 2017MNRAS.470.3775V |
| MAGPHYS | 9 | SED SFR, dust temperature | 2020A&A...635A.119C, 2019ApJ...876..130H |
| emcee | 8 | MCMC SED or limit likelihoods | 2021MNRAS.500.3667S, 2019A&A...621A..27F |
| Pipe3D | 7 | MaNGA spaxel Sigma_SFR, Sigma_* | 2024ApJ...964..120P, 2020MNRAS.492.6027E |
| scikit-learn | 5 | GMM before the KS fit; MLPRegressor ranking of SFR drivers (2020MNRAS.493L..39E) | 2019ApJ...887...88E, 2025ApJ...979..217S |
| scipy | 5 | ODR; leastsq line fits | 2024ApJ...976...88L, 2025ApJ...979..217S |
| linmix / LINMIX_ERR | 4 | Kelly 2007 regression with limits | 2018ApJ...863..193V, 2020A&A...641A.155V |
| ASURV, R survdiff | 2, 1 | survival analysis with limits | 2025ApJ...979..217S, 2017MNRAS.468.4205K |
| astropy | 3 | apertures, error propagation | 2024ApJ...976...88L, 2025A&A...694A.218B |
| MOPEX | 2 | Spitzer mosaics and regridding | 2012ApJ...760L..25E, 2019PASJ...71...40T |

## Pitfalls

- **Area convention factor 2.** (SFR/2)/(pi R_e^2) and SFR/(pi R^2) differ by 2; also R as FWHM/2 vs HWHM vs
  diameter (one paper writes (1/2 SFR)/(1/4 pi d^2), 2018ApJ...864...38L). Gas and SFR must use the same area:
  t_dep from totals does not care, but KS positions and Sigma-based t_dep do.
- **IMF and calibration drift.** Literature SFRs mix Salpeter and Chabrier; conversion factors differ by paper
  (1.6 to 1.8, Step 1), and coefficients differ by up to 1.5x within one IMF (Step 2). Convert before plotting.
- **alpha_CO drives the slope.** Constant vs variable alpha_CO changes resolved slopes (0.90 vs 1.23,
  2024ApJ...976...88L) and offsets SFE by up to 0.14 dex (2020ApJ...903..145L); a fixed alpha_CO probably
  overestimates gas in starbursting centres and overstates the gas-fraction role (2020MNRAS.492.6027E). Several
  authors call alpha_CO the largest uncertainty in their gas masses (2017MNRAS.468.4205K, 2017MNRAS.470.3775V,
  2015ApJ...799...11X); others give "an additional systematic uncertainty" (2025ApJ...995..151Y), a factor >= 2
  (2021ApJ...908...54W), about 50% (2018ApJ...860..103S). Carry these paper-specific estimates; the pack does not
  rank alpha_CO against the SFR systematics for the law as a whole. A bar may need alpha_CO a few times lower
  (2020MNRAS.495.3840M).
- **S/N cuts bias the slope.** Including 1 sigma CO points moved a mean slope from 0.87 to 0.73
  (2025ApJ...995..151Y). Cuts on one axis truncate the other; keep limits in a censored fit on the axis that
  actually carries them, and model the selection rather than relying on censoring alone (Step 6). Two of six
  dwarf slopes rested on two points (2025ApJ...995..151Y).
- **Region mixing.** Slopes in one merger range from 0.15 (an arm) to 0.98 (a nucleus) while the system gives
  0.52 (2025ApJ...979..217S); one pooled N over arms, nuclei and tails may describe none of them.
- **Single dust temperature.** Single-band ALMA SFRs assume one T_dust; SFRs uncertain by orders of magnitude
  without the FIR peak (2015ApJ...813...45L); template choice spans nearly a decade (2019MNRAS.486..560S);
  uncertainties often exclude it (2013ApJ...770...13W). Resolved maps inherit it (2019ApJ...876..130H,
  2024ApJ...976...70L).
- **Non-stellar emission.** Synchrotron can contaminate 110 GHz SFRs by about 25% (2018ApJ...863..129S);
  radio-galaxy SFRs fell sevenfold after removing synchrotron (2019A&A...621A..27F); a fixed non-thermal index
  gives about 20% SFR variation in 3 GHz maps (2025ApJ...979..217S); the quasar share of the FIR may be an upper
  limit (2026MNRAS.546ag167S); AGN photoionisation makes SFR(Halpha) an upper limit (2020MNRAS.492.3194S); AGN
  light biases gas and SFR (2026ApJ..1001..131C, 2021A&A...656A.133Q); free-free cannot always be excluded
  (2020A&A...641A.151S); 24 um SFRs overestimate at high z (2021ApJ...909L..29D).
- **Missing flux, resolved-out gas and coverage gaps** lower Sigma_gas and shorten t_dep (2021A&A...656A..60A,
  2017ApJ...850...54C, 2020A&A...641A.151S); a MUSE mosaic gap overestimated t_dep locally (2020MNRAS.496.2155Z).
- **Registration and PSFs.** 24 um Airy rings add about 0.1 dex (2012ApJ...760L..25E); manually aligned HST
  images can hide offsets (2018ApJ...863..193V); ALMA-HST astrometry 0.1-0.2'' (2019ApJ...881..124M).
- **Scale dependence.** Arm/inter-arm contrasts may depend on resolution (2021A&A...656A.133Q); large beams
  blend regions (2025ApJ...990..221M); beam smearing inflates sigma_v up to 20% (2019ApJ...882....5W), and rotation
  and GMC blending broaden 500 pc linewidths (2025ApJ...979..217S), which feeds eps_ff.
- **Lensing.** Differential magnification may affect line ratios, and t_dep may be underestimated near the end of
  a burst (2016A&A...586L...7B). Gas and SFR tracers need not share a magnification: use tracer-specific mu where
  the lens model constrains them; otherwise propagate a differential-magnification uncertainty and label any
  shared-mu result as such. Shared-mu assumptions in the pack: one magnification for all observed properties
  (2013ApJ...767..132H), uniform magnification from 160 um to 1.3 mm (2020MNRAS.494.5542R), differential lensing
  "assumed not too severe" (2021A&A...655A..42S), a 6 GHz magnification used for 1 mm (2024ApJ...961....2K).
- **Limits dominate.** Mostly upper limits preclude a robust t_dep (2021ApJ...908...54W); relations fitted with
  limits as detections are only limits (2017MNRAS.468.4205K); Sigma_SFR below 1e-3 Msun/yr/kpc^2 treated as
  limits (2020MNRAS.495.3840M).
- **Heterogeneous or mismatched comparisons.** Heterogeneous (2024ApJ...976...88L, 2021MNRAS.500.3667S) and small
  samples (2025ApJ...988..162D, 2020MNRAS.492.6027E) can drive slopes; one Bigiel 2008 comparison differed in CO
  transition, conversion factor, SFR tracer, sample and resolution at once (2020MNRAS.496.2155Z).
- **Selection biases.** PACS-detection selection favours upper main-sequence, warm-dust galaxies
  (2020A&A...641A.155V); N2 selection favours high metallicity and gas fraction (2025ApJ...994....4A); bright or
  IR-selected samples favour massive star-forming galaxies (2020MNRAS.496.2155Z) or intense starbursts
  (2024ApJ...964...95S). Document the parent selection and compare like with like, or model it (Step 6).
- **Circular axes.** An SFR from an assumed KS law (2014ApJ...790..160S) or a gas mass from an assumed SFE
  (2019MNRAS.485.2092C) cannot test that relation (Step 3).
- **Oversampled grids.** Overlapping apertures and sub-beam pixels shrink formal slope errors unless their
  covariance is handled (Step 4).
- **What cards flag as not stated** (aggregates, summed over phrasings): line-free channels and continuum
  subtraction (45), CASA and pipeline version (29), flux calibrator or flux-scale uncertainty (24),
  self-calibration (13), primary-beam correction (8). Specific to this technique: the SFR formula
  (2015ApJ...813..118M), the Sigma_SFR recipe (2018ApJ...863..129S), and the regression method and treatment of
  limits (2025ApJ...988..162D, 2017MNRAS.470.3775V, 2017MNRAS.468.4205K) are often missing. State them.

## Verification checks

What papers did (pack):
- Swap the SFR tracer: 8.4 GHz vs IR (2018ApJ...863..129S); radio vs SED (2018ApJ...868...75S); 3-33 GHz spectral
  indices and q_IR on a radio SFR (2025ApJ...979..217S); Band 5 continuum vs CO(5-4) (2026MNRAS.546ag167S);
  H-alpha vs SED SFRs, consistent above about 13 Msun/yr (2020ApJS..247...61F); other SED codes within about
  0.1 dex (2017MNRAS.469.4683C); alternative templates (2015MNRAS.453L..83M).
- Swap alpha_CO: metallicity-dependent or radially varying (2020ApJ...903..145L, 2025ApJ...995..151Y,
  2024ApJ...976...88L); a factor-two lower value in starburst centres left the SFE conclusion intact
  (2020MNRAS.492.6027E). Swap the gas estimator: three dust-continuum gas estimates (Scoville16 alpha_nu,
  Hughes17, gas-to-dust ratio) consistent within 0.2 dex (2026ApJ..1001..131C); CO-based masses "generally
  consistent" with dust-based ones, with extra systematic error from the scatter in the r31/r41 excitation
  relations (2024A&A...692A.215C); five estimators giving t_dep of 23-140 Myr for one galaxy, [CI] chosen as least
  reliant on conversions (2025A&A...694A.218B).
- Swap the fitter: linmix with and without limits, ODR and ASURV on the same points (2025ApJ...979..217S).
- Vary resolution, grid and aperture: robust from 100 to 400 pc apertures (2025A&A...700A.285W); pixels of 150 pc
  to 1 kpc (2022A&A...663A..61P); every grid origin, with integrated t_dep matching the densest part of the
  resolved relation (2020MNRAS.496.2155Z).
- Drop outliers or subsamples: Kendall tau 0.67 to 0.66 (2020ApJ...903..145L); slopes change < 15% fitting only
  high-z (2020A&A...641A.155V); conclusions unchanged without fully quenched spaxels (2024ApJ...964..120P);
  adding O/H to the control matching moves Delta Sigma_SFR by about 0.01 dex (2020MNRAS.492.6027E).
- Compare to reference relations: Kennicutt 1998 and Bigiel 2008 (2018ApJ...863..193V, 2021A&A...656A..60A);
  local starbursts (2015ApJ...799...11X); the Boquien et al. 2011 relation (2019ApJ...887...88E).
- Line choice: KS index 0.80 vs 0.78 from CO(1-0) vs CO(2-1) with fixed R21 (2025ApJ...988..162D).

What a careful referee adds:
- Recompute t_dep from the quoted M_gas and SFR, and check both share IMF, helium and magnification.
- Re-fit with errors on both axes and limits included on the correct axis; report how N moves vs OLS.
- Check that neither axis was derived from an assumed KS law or SFE, and that slope errors account for
  overlapping apertures or sub-beam pixels.
- For global Sigma, confirm the size is beam-deconvolved with S/N high enough to trust it, the area error is
  propagated, and f_SFR and f_gas are both stated.
- For lensed sources, check whether gas and SFR tracers share a magnification or the shared-mu assumption is
  labelled.
- Check that every calibration coefficient comes with its input and output units.
- Check the slope after shifting the S/N cut by 1 sigma, after convolving to a coarser beam, and per morphological
  component before one N is quoted.
- Check that the area used for Sigma_gas and Sigma_SFR is identical, and whether inclination was applied.
- For dense-gas laws, confirm the HCN line was not cut by the bandpass (2015ApJ...813..118M) and that alpha_HCN
  was stated. For eps_ff, check the scale height or density model and the eps_ff definition.

## Source cards

Full list: `references/sources.md` (generated). Most informative for this technique:

- 2024ApJ...976...88L: resolved KS with ODR, constant vs variable alpha_CO, theory comparisons
- 2025ApJ...979..217S: 500 pc KS in a merger, linmix/ODR/ASURV cross-check, GMM, per-component slopes, eps_ff
- 2019ApJ...887...88E: pixel KS at 43 pc, GMM plus ODR, AGN masking, completeness floor
- 2022A&A...663A..61P: hierarchical Bayesian KS across environments, pixel-scale tests, detection-fraction cut
- 2025ApJ...995..151Y: per-galaxy KS in dwarfs, S/N-cut and alpha_CO tests
- 2020MNRAS.492.6027E: Delta SFE vs Delta f_H2 with control spaxels, alpha_CO robustness
- 2024ApJ...964..120P: radial SFE vs gas-fraction drivers, D4000 Sigma_SFR for non-SF spaxels
- 2020MNRAS.496.2155Z: beam binning over all grid origins, t_dep in cluster galaxies, convention mismatches
- 2018ApJ...863..193V: linmix KS fit, factor-2 SFR uncertainty adopted, UV-scaled SFR
- 2020A&A...641A.155V: censored Bayesian regression, Sigma_SFR = SFR/(2 pi R^2), selection bias
- 2017MNRAS.470.3775V: global KS with two-sided disk areas, CO size fallback
- 2021A&A...656A..60A: beam apertures, missing-flux correction, Pa-alpha SFR
- 2020ApJ...903..145L: spaxel SFE vs gas fraction, alpha_CO robustness
- 2018ApJ...863..129S: dense-gas law, SFR tracer swap, turbulence model
- 2025A&A...694A.218B: t_dep across five gas estimators at z = 4.3
- 2026MNRAS.546ag167S: quasar-host SFR from decomposed continuum vs CO(5-4)
- 2025A&A...700A.285W: depletion time along a spiral, aperture robustness
- 2012ApJ...760L..25E: FUV+24 um Sigma_SFR, PSF contamination check
- 2019ApJ...876..130H: resolved Sigma_SFR from 870 um, model-dependent Eddington limit
- 2018ApJ...861L..18U: eps_ff in nearby galaxies (method details from its card)
- 2017A&A...602L...9M: KS law of submillimetre galaxies (method details from its card)
- 2019ApJ...882....5W: KS law and scale height in (U)LIRGs (method details from its card)
- 2019MNRAS.487.4305S: resolved SF law tests at z = 4.3
- 2025ApJ...988..162D: R21 effect on KS index and t_dep
