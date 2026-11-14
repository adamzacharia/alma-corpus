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

2. **Build the SFR (or Sigma_SFR) map or total.** Method by tracer family (pack lines). Write the input and
   output units next to every calibration you use; where the pack line does not give them, they are marked
   "units not in pack" below and you must take them from the cited paper before applying the coefficient.
   - Dust continuum / IR luminosity with Kennicutt 1998 (19 papers, e.g. 2013ApJ...767..132H,
     2014A&A...562A..67G, 2019ApJ...876..130H, 2019ApJ...881...63N) or Kennicutt and Evans 2012 (3, e.g.
     2020A&A...635A.119C, 2025A&A...698A.204H). Coefficients seen: SFR = 1.72e-10 L_IR (Salpeter,
     2019A&A...621A..27F), SFR = 1.40e-10 L_IR (Chabrier, 2025A&A...698A.204H); units not in pack (the
     usual convention is SFR in Msun/yr with L_IR in Lsun, general practice; verify in the paper).
   - Resolved IR maps from a single ALMA band: papers scale the SED-derived total SFR by each beam's share of
     the continuum flux (2019ApJ...876..130H), which assumes one dust temperature everywhere.
   - H-alpha or Pa-alpha (10 papers): SFR [Msun/yr] = 5.53e-42 L_Halpha (2024ApJ...976...88L; L units not in
     pack), SFR [Msun/yr] = 4.5e-42 L_Halpha [erg/s] (2020ApJS..247...61F), Pa-alpha with Calzetti extinction
     (2021A&A...656A..60A), Balmer-decrement correction (2020ApJ...889....9M, 2019MNRAS.485.1595P). State the
     nebular attenuation prescription and carry its uncertainty: after a stellar-A_V Calzetti correction,
     H-alpha SFRs of z~2 SMGs were still a median factor 3+-1 below IR SFRs (2020A&A...635A.119C), and the
     Spitzer-color H-alpha method of 2020ApJS..247...61F calls its f = 0.44 factor a likely upper limit on
     L_Halpha and its largest uncertainty. Cross-check with an obscured tracer (IR) before treating corrected
     H-alpha as the total SFR.
   - UV plus IR hybrids: Sigma_SFR = 3.2e-3 I24 + 8.1e-2 I_FUV (2012ApJ...760L..25E; map and output units not in
     pack); NUV+12um (2025ApJ...995..151Y); FUV/NUV/12um/24um coefficients K (2018ApJ...861L..18U; units not in
     pack).
   - Free-free and recombination lines: 33 GHz thermal fraction 79% (2015ApJ...813..118M); H30alpha
     (2017MNRAS.472.1239B). 110 GHz continuum mixes free-free with possible synchrotron, about 25%
     (2018ApJ...863..129S).
   - PAH emission (not free-free): log Sigma_SFR = 0.844 log Sigma_L8 - 30.923 from 8 um
     (2019ApJ...887...88E); the intercept depends on the units of Sigma_L8 and Sigma_SFR, which are not in the
     pack, so do not apply it without the paper's unit definitions.
   - Far-IR dust emission (not free-free): linear 160 um to SFR mapping (2019ApJ...876..112R).
   Software: 2012ApJ...760L..25E regridded its Spitzer maps with MOPEX; totals come from CIGALE or MAGPHYS
   (5 and 3 name mentions in the aggregates).

3. **Build the gas map or total.** Goal: Sigma_mol (or Sigma_dense, Sigma_HI+H2) on the same footprint.
   Method: moment-0 with alpha_CO and r_J1 (see the gas-mass skill), times cos i, including or excluding
   helium consistently. X_CO converts CO intensity to H2 column and carries no helium; the 1.36 factor
   belongs in alpha_CO or the Sigma coefficient (X_CO = 2e20 corresponds to alpha_CO = 4.35 including
   helium, 2025ApJ...995..151Y). Apply it exactly once.
   Galactic alpha_CO of 4.3-4.87 dominates (15 papers by my count of unique bibcodes in the pack's
   assumption and parameter lines, e.g. 2020ApJ...903..145L, 2025ApJ...995..151Y, 2019MNRAS.485.1595P;
   2025ApJ...988..162D is not counted because its analysis uses a radially varying alpha_CO and 4.35 only
   for a sensitivity estimate). ULIRG-like 0.8-1.1 in 7 (same count method, repeated lines counted once:
   2014ApJ...790..160S, 2017MNRAS.469.4683C SB case, 2017A&A...604A.117C, 2017ApJ...846..108C,
   2019MNRAS.489..427I, 2020A&A...641A.151S, 2020MNRAS.497.2771M mergers).
   Dense gas: alpha_HCN = 10 (2015ApJ...815..103B, 2018ApJ...858...90G, 2018ApJ...863..129S, 2019AJ....157..131B), alpha_HCO+ about 10 (2015ApJ...813..118M).
   Correct for flux the interferometer missed, or say you did not: 45% missing-flux correction
   (2021A&A...656A..60A); about half the flux recovered (2017ApJ...850...54C).
   **Record provenance of both axes and avoid circular tests.** Some papers derive one axis from an assumed
   star formation law: SFR from the Schmidt-Kennicutt law with an assumed 300 pc disk (2014ApJ...790..160S);
   gas masses that rely on an assumed main-sequence SFE (2019MNRAS.485.2092C); gas surface density taken from
   the global Sigma_SFR for a Toomre estimate (2019ApJ...876..130H). Flag every such point and exclude it from
   any fit or t_dep comparison that tests the same relation.

4. **Match resolution and sampling.** Goal: both maps describe the same gas. Convolve to the coarser beam,
   regrid to about one beam per sample, then measure. Report beam resolution, aperture size (radius or
   diameter, say which) and sampling spacing as three separate numbers.
   - Pixels: 6'' resolution on 3'' pixels (2012ApJ...760L..25E); 2.4'' (43 pc) pixels set by the 8 um map
     (2019ApJ...887...88E).
   - Apertures: beam-sized circles on two grids offset by 0.5 beam FWHM (2024ApJ...976...88L); apertures of
     0.75'' (34 pc) radius (2021A&A...656A..60A); hexagons spaced 1 kpc at 1.5 kpc resolution
     (2021A&A...656A.133Q); 200 pc apertures on a 100 pc grid along a spiral (2025A&A...700A.285W); 1.7 kpc
     resolution (2025ApJ...988..162D).
   - Overlapping samples are not independent. Offset grids (2024ApJ...976...88L), 6'' data on 3'' pixels
     (2012ApJ...760L..25E) and 200 pc apertures every 100 pc (2025A&A...700A.285W) all oversample the beam or
     aperture. Regridding does not create independent points: account for the spatial covariance (or
     resample in spatial blocks, general practice) and do not count overlapping apertures as independent
     constraints when quoting slope errors.
   - Global compact sources: write both enclosed fractions explicitly, Sigma_SFR = f_SFR SFR/A and
     Sigma_gas = f_gas M_gas/A, and measure or justify each. Papers take f_SFR = 1/2 inside the half-light
     radius, (SFR/2)/(pi R_e^2) (2019ApJ...876..130H, 2014A&A...562A..67G), or SFR/(2 pi R^2) with
     R = FWHM/2 (2020A&A...641A.155V); 2017A&A...602L...9M (card, section 3 "Data analysis") halves both,
     SFR/(2 pi R^2) and M_gas/(2 pi R^2). A dust-continuum half-light radius encloses half the
     continuum-traced SFR, not necessarily half the gas: if the gas tracer has a different size, use its own
     size or state the assumption.
   - Validate sizes before trusting a global Sigma: deconvolve from the beam, propagate the size error into
     the area (A scales as R^2), and keep a Sigma lower limit when the source is unresolved. The pack shows why:
     a size from sparse uv coverage that needs higher-resolution confirmation, giving only Sigma_SFR > 26
     (2014A&A...562A..67G); a marginally resolved source with a poorly constrained size (2013ApJ...770...13W);
     sizes biased high at S/N < 10 (2017ApJ...844..123F).
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
   linear fits to binned means (used for R21 trends, 2025ApJ...988..162D); a two-component Gaussian mixture
   chosen by BIC before the ODR fit (2019ApJ...887...88E, the one pack paper that documents this; its software
   line names scikit-learn). From cards: least squares on binned data, plus a slope fixed to 1 for SFE
   (2017A&A...602L...9M, card step 4); double power law with free break, 10,000 bootstraps
   (2019ApJ...882....5W, card step 4). One paper normalises at Sigma_H2 = 100 Msun/pc^2,
   Sigma_SFR = A (Sigma_H2/100)^N (2018ApJ...863..193V).
   Recommendation: fit with errors on both axes and say which axis carries the limits. Kelly 2007 linmix
   censors the dependent variable (general practice); in log Sigma_SFR = N log Sigma_gas + C, CO or gas
   non-detections are limits on the independent variable, so either refit the inverse relation with gas as the
   dependent variable or use a likelihood that handles censoring on x. Censoring is not the same as
   selection: points kept only where CO is significantly detected (2025ApJ...995..151Y, whose slope moved when
   1 sigma points were added) or samples with line-luminosity upper limits (2020A&A...641A.155V) is truncated, and that truncation has to be modelled or the sample restricted
   to where it is complete. Quote OLS or ODR alongside if comparing to older work.
   Document the parent-sample selection before comparing samples: a PACS-detection requirement steered one
   sample to upper main-sequence, warm-dust galaxies (2020A&A...641A.155V); N2 selection biased another toward
   high metallicity and gas fraction (2025ApJ...994....4A). Restrict comparisons to matched selections or
   model the selection.

7. **Derive t_dep, SFE and eps_ff.** t_dep = M_mol/SFR = 1/SFE (2019MNRAS.485.1595P); per pixel
   t_dep = Sigma_mol/Sigma_SFR, summarise with the median (2024ApJ...976...88L, 2025A&A...700A.285W).
   Mind the area units: with Sigma_mol in Msun/pc^2 and Sigma_SFR in Msun/yr/kpc^2,
   t_dep [yr] = 1e6 Sigma_mol/Sigma_SFR, or t_dep [Gyr] = 1e-3 Sigma_mol/Sigma_SFR (unit arithmetic).
   eps_ff = t_ff/t_dep needs a gas scale height or density model (general practice; 2018ApJ...861L..18U
   compares eps_ff from three H prescriptions to estimate the systematic, card step 3). Theory comparisons in the pack use
   Krumholz-McKee turbulence-regulated grids (2018ApJ...863..129S), KDM and SFK models
   (2019MNRAS.487.4305S), Krumholz+18 and feedback-regulated models (2024ApJ...976...88L).

8. **Validate** (see Verification checks) and report the conventions box above.

## Parameter defaults and ranges

| parameter | common choice | range seen | papers (count) | examples |
|---|---|---|---|---|
| IMF | Chabrier | Chabrier, Salpeter, Kroupa | 24 / 13 / 4 (pack lines) | 2018MNRAS.477.4380S, 2019ApJ...884L..33L, 2019Natur.569..519K |
| IR SFR calibration | Kennicutt 1998 | K98, Kennicutt and Evans 2012 | 19 / 3 (pack lines) | 2019ApJ...881...63N, 2020A&A...635A.119C |
| alpha_CO (normal disks) | 4.35-4.36 incl. He | 4.3-4.87 (one paper about 7, 2019AJ....157..131B) | 15 (my count of unique bibcodes, pack lines) | 2020ApJ...903..145L, 2017MNRAS.469.4683C |
| alpha_CO (starburst, nucleus) | 0.8 | 0.8-1.1 | 7 (my count of unique bibcodes, pack lines) | 2017ApJ...846..108C, 2014ApJ...790..160S |
| alpha_HCN | 10 | 10 | 4 (pack lines) | 2018ApJ...858...90G, 2019AJ....157..131B |
| Area for global Sigma_SFR | (SFR/2)/(pi R_e^2) | R from FWHM/2 or HWHM; f_gas often unstated | 4 in pack lines (+1 card) | 2019ApJ...876..130H, 2020A&A...641A.155V |
| Resolution of resolved KS | beam-matched | pixels of 43 pc to 1.7 kpc resolution; apertures 34 pc radius to 1 kpc hexagons | see Step 4 | 2019ApJ...887...88E, 2025ApJ...988..162D, 2021A&A...656A..60A, 2021A&A...656A.133Q |
| CO S/N cut per sample | > 2 | 1 to 3 sigma | 4 (pack lines) | 2017ApJ...851...18L, 2025ApJ...995..151Y |
| Reported SFR uncertainty (paper-specific, not a floor) | none common | 20% (H-alpha), +-0.3 dex L_IR template range, factor 2 (UV) | 3 (pack lines) | 2019Natur.569..519K, 2015MNRAS.453L..83M, 2018ApJ...863..193V |
| Dust T for single-band IR SFR | 40-50 K, beta 1.5-1.6 | 25-120 K | many (see parameters.md) | 2013ApJ...770...13W, 2017A&A...599A.134S |

The SFR uncertainties in the table are what three papers adopted for their own tracer; the pack does not
establish a common minimum. Build a tracer-specific error budget (calibration, attenuation, dust temperature
or template, non-stellar contamination) instead of borrowing one of these numbers.

Results to sanity-check against (not targets): resolved molecular KS slopes 0.63 overall and 0.28 in a CND
(2019ApJ...887...88E), 0.64 to 1.18 (2018ApJ...863..193V), 0.62 to 1.08 with mean 0.81 in dwarfs
(2025ApJ...995..151Y), 0.90 or 1.23 depending on alpha_CO (2024ApJ...976...88L). Depletion times: median
0.8 Gyr in z~0.1 analogues (2024ApJ...976...88L), 1.5 Gyr in Cen A (2019ApJ...887...88E), 3.9 Gyr along a
Seyfert spiral (2025A&A...700A.285W), 0.7 Gyr in protocluster galaxies (2025A&A...698A.204H), 0.4 Gyr in a
LLAGN centre (2020A&A...641A.151S), 12-28 Myr in a hyperluminous quasar (2019ApJ...887...74F). SFE_H2 of
0.9-4.1 per Gyr in dwarfs (2025ApJ...995..151Y). Extreme Sigma_SFR: about 4200 (2013ApJ...767..132H) and
2e3 Msun/yr/kpc^2 (2017ApJ...842L..16L), compared in 2019ApJ...876..130H with its model-dependent
Eddington-limited lower limit of about 650 Msun/yr/kpc^2, which assumes optically thick emission, a gas
fraction of unity, dust-to-gas 1/90 and one global dust temperature. eps_ff = 0.11 in an IRDC (2018ApJ...855L..25K). Longer table in
`references/parameters.md`.

## Software

From the pack aggregates of software named in matched steps (160 papers; counts are small because most
papers do the arithmetic in their own scripts). The counts are name frequencies, not counts of a specific
procedure; the "used for" column is what the excerpted papers show, not a claim about every mention:

| software | count (aggregates) | used for | examples |
|---|---|---|---|
| CIGALE | 5 | SED SFR and M_star feeding the law | 2025A&A...698A.204H, 2024A&A...692A.215C, 2026ApJ..1001..131C |
| CASA | 5 | imaging, moment maps, apertures | 2015ApJ...813..118M, 2019MNRAS.485.1595P, 2024ApJ...976...88L |
| MAGPHYS | 3 | SED SFR, dust temperature | 2020A&A...635A.119C, 2019ApJ...876..130H |
| emcee | 2 | MCMC SED or limit likelihoods | 2019A&A...621A..27F |
| scikit-learn | 2 | GMM before the KS fit in one paper (2019ApJ...887...88E); the only other scikit-learn mention in the excerpts is clustering in an off-topic core paper (2020A&A...635A...2S), so the second count is not a KS use | 2019ApJ...887...88E |
| MOPEX | 2 | Spitzer mosaics and regridding | 2012ApJ...760L..25E, 2019PASJ...71...40T |
| astropy | 2 | named in the aperture-measurement step | 2024ApJ...976...88L |
| reproject | 1 | name in aggregates only; no excerpt shows which paper or step | none in excerpts |
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
  2024ApJ...976...88L) and offsets SFE by up to 0.14 dex (2020ApJ...903..145L). Authors treat alpha_CO as a
  substantial systematic: "an additional systematic uncertainty" (2025ApJ...995..151Y), a factor >= 2
  (2021ApJ...908...54W), about 50% (2018ApJ...860..103S). Carry these paper-specific estimates; the pack
  does not rank alpha_CO above the other systematics.
  A bar may need alpha_CO a few times lower (2020MNRAS.495.3840M).
- **S/N cuts bias the slope.** Including 1 sigma CO points moved a mean slope from 0.87 to 0.73
  (2025ApJ...995..151Y). Cuts on one axis truncate the other; keep limits in a censored fit on the axis that
  actually carries them, and model the selection rather than relying on censoring alone (Step 6). Two of six dwarf slopes rested on two points (2025ApJ...995..151Y).
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
- **Lensing.** Differential magnification may affect line ratios, and t_dep may be underestimated near the
  end of a burst (2016A&A...586L...7B). Gas and SFR tracers need not share a magnification: use
  tracer-specific mu where the lens model constrains them; otherwise propagate a differential-magnification
  uncertainty and label any shared-mu result as such. 2013ApJ...767..132H divided observed properties by a
  single magnification, which is that shared-mu assumption.
- **Limits dominate.** Mostly upper limits preclude a robust t_dep (2021ApJ...908...54W); Sigma_SFR below
  1e-3 Msun/yr/kpc^2 treated as limits (2020MNRAS.495.3840M).
- **Heterogeneous comparison samples** (2024ApJ...976...88L) and small samples (2025ApJ...988..162D,
  2019ApJ...884L..33L) can drive slopes.
- **Selection biases.** PACS-detection selection favours upper main-sequence, warm-dust galaxies
  (2020A&A...641A.155V); N2 selection favours high metallicity and gas fraction (2025ApJ...994....4A).
  Document the parent selection and compare only like with like, or model it (Step 6).
- **Circular axes.** An SFR from an assumed KS law (2014ApJ...790..160S) or a gas mass from an assumed SFE
  (2019MNRAS.485.2092C) cannot test that relation (Step 3).
- **Oversampled grids.** Overlapping apertures and sub-beam pixels shrink formal slope errors unless their
  covariance is handled (Step 4).
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
  2024ApJ...976...88L). Swap the gas estimator: three dust-continuum gas estimates (Scoville16 alpha_nu,
  Hughes17, gas-to-dust ratio) consistent within 0.2 dex (2026ApJ..1001..131C); CO-based masses "generally
  consistent" with dust-based ones, with extra systematic error from the scatter in the r31/r41 excitation
  relations (2024A&A...692A.215C).
- Vary resolution and aperture: trends robust from 100 to 400 pc apertures (2025A&A...700A.285W).
- Drop outliers or subsamples: Kendall tau 0.67 to 0.66 (2020ApJ...903..145L); slopes change < 15% fitting
  only high-z (2020A&A...641A.155V).
- Compare to reference relations: Kennicutt 1998 and Bigiel 2008 (2018ApJ...863..193V,
  2021A&A...656A..60A); the Boquien et al. 2011 relation (2019ApJ...887...88E).
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
- Check the slope after shifting the S/N cut by 1 sigma and after convolving to a coarser beam.
- Check that the area used for Sigma_gas and Sigma_SFR is identical, and whether inclination was applied.
- For dense-gas laws, confirm the HCN line was not cut by the bandpass (2015ApJ...813..118M) and that
  alpha_HCN was stated.

## Source cards

Full list: `references/sources.md` (generated). Most informative for this technique:

- 2024ApJ...976...88L: resolved KS with ODR, constant vs variable alpha_CO, theory comparisons
- 2019ApJ...887...88E: pixel KS at 43 pc, GMM plus ODR, AGN masking, completeness floor
- 2025ApJ...995..151Y: per-galaxy KS in dwarfs, S/N-cut and alpha_CO tests
- 2018ApJ...863..193V: linmix KS fit, factor-2 SFR uncertainty adopted, UV-scaled SFR
- 2020A&A...641A.155V: censored Bayesian regression, Sigma_SFR = SFR/(2 pi R^2)
- 2021A&A...656A..60A: beam apertures, missing-flux correction, Pa-alpha SFR
- 2020ApJ...903..145L: spaxel SFE vs gas fraction, alpha_CO robustness
- 2018ApJ...863..129S: dense-gas law, SFR tracer swap, turbulence model
- 2025A&A...700A.285W: depletion time along a spiral, aperture robustness
- 2012ApJ...760L..25E: FUV+24 um Sigma_SFR, PSF contamination check
- 2019ApJ...876..130H: resolved Sigma_SFR from 870 um, model-dependent Eddington limit
- 2018ApJ...861L..18U: eps_ff in nearby galaxies (method details from its card)
- 2017A&A...602L...9M: KS law of submillimetre galaxies (method details from its card)
- 2019ApJ...882....5W: KS law and scale height in (U)LIRGs (method details from its card)
- 2019MNRAS.487.4305S: resolved SF law tests at z = 4.3
- 2025ApJ...988..162D: R21 effect on KS index and t_dep
- 2021A&A...656A.133Q: environment masks across PHANGS
- 2025A&A...698A.204H: depletion times in protoclusters, alpha_CO rescaling of literature
- 2019A&A...621A..27F: synchrotron removal for radio-galaxy SFRs
