---
name: alma-rotational-diagram-lte
description: "Derive rotational/excitation temperatures and LTE column densities from ALMA molecular lines: rotation (population) diagrams with opacity correction, full-spectrum LTE fitting (least squares or MCMC) in CASSIS, XCLASS, MADCUBA (SLIM/AUTOFIT) or Weeds/MCWeeds, single-line LTE columns at an assumed Tex, and the abundance, isotopologue and deuteration ratios built on them. Use when a task asks for Trot or Tex, N_tot, a COM inventory, an LTE upper limit, or an LTE gas mass from line fluxes or spectra. Built from 930 ALMA papers (2012-2026)."
---

# Rotational diagrams and LTE column densities

Measures a single excitation (rotational) temperature and a total column density per species, assuming
level populations follow a Boltzmann distribution. The two mistakes that matter most: treating optically
thick or continuum-affected lines as thin (biases Trot and underestimates N), and quoting a column from one
line at an assumed Tex without showing how N moves over a plausible Tex range. Beam filling (source size) is
the third silent assumption: many papers set it to 1 (27 by my count, rule and ledger in
`references/parameters.md` section 10), which gives a beam-averaged column, not the intrinsic source column.
With a fixed filling factor, 2025ApJS..276...49J (card) says its columns are lower limits by a factor of
about 2 to 3, and source size and column are degenerate when the emission is unresolved
(2025A&A...696A..18C, 2025ApJ...991...59B).

## When to use

- Several transitions of one species spanning a range of upper-level energies: fit a rotation (population)
  diagram or an LTE synthetic spectrum for Trot and N (2020ApJ...890..142P, 2014Sci...345.1584B,
  2018A&A...620A..75K).
- Line-rich hot cores, hot corinos and warm disks where every species must be modelled at once to handle
  blends: Weeds (2016A&A...587A..91B, 2019A&A...628A..10B), XCLASS (2020A&A...636A..67A,
  2025ApJS..276...49J), MADCUBA (2024A&A...682A..74F, 2021A&A...656A..46M) or CASSIS (2020A&A...644A..59K;
  CASSIS MCMC in 2025A&A...696A..18C).
- Radial or per-pixel Trot and N maps (2025A&A...698A.115R, 2023MNRAS.525.6146W, 2025A&A...693A..76C).
- One line only, and a column, mass or upper limit is still needed at an assumed Tex (2020MNRAS.492.1180R,
  2015ApJ...798..124R, 2018A&A...619A..28L).
- Isotopologue, deuteration and molecule ratios, which need N per species under shared assumptions
  (2016A&A...587A..91B, 2019A&A...628A..10B).
- Tex from a two-line ratio (CO R32 gave 29 K in 2017A&A...608A..38O) or from the peak of an optically
  thick line (2026A&A...705A.198M, 2021A&A...648A..19W).
- Gas dense enough that LTE is defensible: n > 1e6 cm^-3 (2018ApJ...864..170G), n ~ 1e8 cm^-3
  (2020A&A...644A..84M), n_H2 >~ 1e10 cm^-3 (2018A&A...620A.170J), n_H2 >> n_crit ~ 1e5 cm^-3
  (2019ApJ...882..118X). Compute n_crit = A_ul / C_ul per line at the adopted temperature and compare with
  the mean H2 density, as 2022A&A...657A.136E did.

## When not to use

- You need kinetic temperature and density, or there is evidence the levels are not thermalized (density
  plausibly below n_crit, radiative pumping, a non-LTE check that disagrees): use **non-lte-excitation**.
  In HH 212, RADEX columns were a factor 2 to 4 above the LTE thin ones (2015A&A...581A..85P); LTE was
  "found not to hold" in 2016ApJ...833...41Z; ALCHEMI residuals revealed non-LTE deviations
  (2021A&A...656A..46M); in NGC 253, opacity- and size-corrected diagrams still bent, with Trot below the
  LVG minimum gas temperature (2025A&A...698A.261B). 2025ApJ...991...59B starts with one LTE component and
  adds a second component or a non-LTE fit only when the LTE fit is unsatisfactory.
- The collider species alone does not decide it: debris-disk work scans electron density "from the
  radiation-dominated regime to LTE" (2016MNRAS.460.2933M) and runs LTE and non-LTE fits with fluorescence
  (2020MNRAS.497.2811K); a comet study pairs a CH3OH diagram with non-LTE LIME modelling
  (2019ApJ...870L..26C). Where electron density or radiation field is unknown, bracket with a non-LTE scan.
- Disk structure fitted to visibilities: **radiative-transfer-modelling**, **uv-plane-fitting**. alpha_CO
  masses: **gas-mass-co-conversion**. Isotope ratios: **isotopic-ratios**. Line assignment:
  **line-identification**. Free-free "LTE" (2020ApJ...888L..28S): **free-free-synchrotron**. Masers are
  excluded from LTE analyses (2018A&A...615A..28D).

## Steps

1. **Prepare the spectrum.** Goal: continuum-subtracted spectrum in brightness temperature from a region
   where one set of conditions is plausible.
   - Extract from a beam-sized aperture (1.6" in 2024A&A...689A..64B), the line peak pixel
     (2020A&A...636A..67A), a 3" circle (2020MNRAS.492.1180R) or a disk mask (6" in 2018ApJ...864..170G).
     Convert Jy/beam to K with that cube's beam (T = 1.222e3 I / (nu^2 theta_maj theta_min), I in mJy/beam,
     nu in GHz, axes in arcsec, 2025A&A...697A.190L); an aperture-integrated flux is Jy, not Jy/beam.
   - Common spatial response (required before combining lines): papers assume all lines share one
     environment (2020ApJ...890..142P) or one spatial distribution for a beam-coupling factor
     (2025A&A...696A.100G), and warn about comparing physical scales (2024A&A...689A..64B). Match beams and
     apertures (equal-beam cubes in 2025A&A...698A.115R) and check each setup's recoverable scale (CS J=7-6
     dropped for its small MRS in 2025ApJ...985...84L; about 80% of single-dish flux filtered, argued equal
     for both isotopologues, in 2022A&A...657A.136E), or model the differences.
   - Bright continuum is the background term (2018A&A...616A..90C; Tbg = 21 K in 2018A&A...619A..28L;
     Tbg = max(continuum Tb, 2.73 K) in 2021ApJS..257....6G and 2024ApJ...967...68H). A continuum brightness
     temperature is not a physical blackbody temperature; state which enters the transfer equation.
   - Dust attenuation: 2025ApJS..276...49J divided line intensities by exp(-tau_dust) after fitting N_H2 and
     eta to the continuum, assuming coupled dust and gas in LTE; apply only with a stated line-dust geometry.
     Software: CASA, GILDAS CLASS, MADCUBA, STATCONT (see **continuum-subtraction**).
2. **Identify lines and choose the ones to fit.** Goal: detected, unblended transitions with trusted
   spectroscopy.
   - Build an LTE model of all species across the band, then keep transitions not severely blended
     (2014Sci...345.1584B). Automated screening: XCLASS model spectra for about 1500 species at 35 column
     steps, keeping species whose predicted lines all match, then visual inspection (2025ApJS..276...49J,
     card).
   - Detection rules differ by paper: a species counts only if all unblended transitions predicted above
     5 sigma are detected (2021A&A...656A..46M); if enough unblended lines exceed 5 sigma and the model
     predicts no strong undetected line (2025A&A...693A.160M); 3 sigma integrated intensity with lines
     more than 15% contaminated rejected (2024A&A...689A..64B). Aij and Eup cuts: `references/parameters.md`
     section 5. Software: CDMS, JPL, Splatalogue, XCLASS, Weeds, MADCUBA SLIM.
3. **Rotation (population) diagram.** Goal: Trot and N from slope and intercept.
   - General practice: N_u = 8 pi k nu^2 W / (h c^3 A_ul) in cgs with W in K cm/s (Rayleigh-Jeans, thin,
     beam-filling, negligible background). Practical units: N_u [cm^-2] = 1.94e3 nu[GHz]^2 W[K km/s] /
     A_ul[s^-1]; plugging K km/s into the cgs form loses 1e5. Fit ln(N_u/g_u) = ln(N_tot/Q(Trot)) -
     E_u/(k Trot). Correct for opacity with C_tau = tau/(1 - exp(-tau)) and, for a circular Gaussian source
     in a circular Gaussian beam, for dilution with (theta_s^2 + theta_b^2)/theta_s^2.
   - Spin and symmetry states: decide whether the column is one state (ortho, para, A, E) or the total; take
     Q and g_u from the same catalogue convention; convert to a total once with a stated ratio (o/p = 3 for
     total H2CO in 2018ApJ...864..170G; para-H2CO only, no ratio, in 2024ApJ...969..143I).
   - What papers do: iterate C_tau from a thin start until tau and Tex change by at most 0.001%
     (2020ApJ...890..142P); correct with the opacities delivered by Weeds and subtract contaminating species
     (2016A&A...587A..91B, card); 2014Sci...345.1584B used lines not too severely blended, removed the
     contaminant model and verified thinness a posteriori. Add the flux-scale error in quadrature (10% in
     2020ApJ...890..142P, 15% in 2024A&A...689A..64B). 2019ApJ...872..200H (card) quotes "a conservative
     error of 20% for the ln(E_u/g_u) values"; that wording is anomalous, do not copy it. Propagate
     sigma_ln = sigma_W / W, and treat calibration error as correlated among lines of one setup (it shifts
     N, not Trot, when shared).
   - Fit one to three components when the diagram curves (2024A&A...689A..64B; 22 and 59 K for C2H in
     2025A&A...696A.100G); 2025A&A...698A.261B justified a second component by FWHM and velocity trends
     with Eu and gave the two components filling factors 0.5 and about 0.01. Require at least three lines
     (2020ApJ...890..142P, 2025A&A...694A.166C, 2024A&A...684A...4U) spanning a real Eu range: four HCO
     lines at Eup = 4 K gave no Tex (2019MNRAS.483..806R).
   - Resolved disks: per annulus, 2025A&A...698A.115R took tau from the peak brightness and Tex, applied
     C_tau, and sampled Tex and N with emcee (uniform Tex 10-100 K, N 1e10-1e16 cm^-2, 10% calibration).
     The shortcut tau = -ln(1 - Tb/Tex) is Rayleigh-Jeans with eta = 1 and no background; in general use
     tau = -ln(1 - Tb / (eta [J(Tex) - J(Tbg)])) (step 5), which matters at low Tex (2024ApJ...969..102N).
4. **Full-spectrum LTE fit.** Goal: N, Tex, source size, FWHM and velocity per species, blends fitted
   jointly.
   - Model: one synthetic LTE spectrum per species. Weeds takes five inputs (N, temperature, size, velocity
     offset, linewidth) per species (2014Sci...345.1584B, 2024A&A...681A.104B); in 2016A&A...587A..91B
     (card) the size was measured and "the other four parameters were optimized by eye", so not all were
     free. MADCUBA AUTOFIT fitted V, FWHM, Tex and N with size fixed (2024A&A...682A..74F).
   - Summing species spectra is exact only where species do not overlap in opacity along the sightline (thin
     lines, or species in separate gas). Where opaque lines of different species overlap, combine opacities
     and source functions: 2025A&A...693A.160M handled line overlap "with an average source function per
     frequency and distance".
   - Fix FWHM from unblended lines; fit Tex only when at least 2 lines span a range of Eup, otherwise fix it
     (2024A&A...686A..59N). Opacity limits on fitted lines are paper-specific choices (tau < 0.1 to about 3,
     table below), not a rule of the method. Penalise over-prediction (weight 3 in 2020A&A...635A..48M).
   - Shared parameters for weak species: fit CH3OH (or all species), then fix Tex, FWHM and vLSR to the
     CH3OH values or species medians and fit only N (2025A&A...696A..18C, 2023MNRAS.525.6146W);
     2025A&A...696A..18C kept CH3OH-constrained fits where median-constrained ones failed and left thick
     CH3OH out of the medians.
   - Optimisers (by eye, Levenberg-Marquardt, MAGIX genetic plus MCMC, MCWeeds, emcee, CASSIS MCMC, chi2
     grids) and their settings per paper: `references/parameters.md` section 1.
5. **Handle optically thick species.** Goal: N that is not set by saturated lines.
   - Fit a rare isotopologue and scale: CH3OH from 13CH3OH x 60 (2019NatAs...3..314L); main species from 13C
     isotopologues with 12C/13C (2016A&A...587A..91B). Check opacity with isotopologue intensity ratios
     (28SiO/29SiO in 2024A&A...682A..74F; a 12CO/13CO line ratio of 2.0 gave tau_12CO ~ 56 in
     2015ApJ...798...85P, assuming one Tex, CMB neglected and abundance ratio 76).
   - Or fit with the least opaque lines: high-excitation CH3OH (2025A&A...696A..18C), A < 1e-4 s^-1 and/or
     Eu > 300 K (2025ApJ...986L...9B), thin LTE only for Eu > 200 K (2022ApJ...937...10L). If no thin
     tracer exists, report N as a lower limit (2019MNRAS.483..806R).
   - Thick lines are not unusable: they constrain Tex and the filling factor while leaving N weakly
     constrained unless thinner isotopologues are fitted jointly. 2020ApJ...905..122H least-squares fitted
     Trot, N(12CO) and filling factor to 12CO, 13CO and C18O with 12CO(2-1) opacities of 38 to 76, and
     found Trot and filling factor correlated at 0.99.
   - Tex from a thick line: 2026A&A...705A.198M set Tex to the peak brightness temperature. That holds only
     for very thick, beam-filling lines with negligible background and h nu << k Tex. In general invert
     T_B = eta [J(Tex) - J(Tbg)] (1 - exp(-tau)), J(T) = (h nu/k) / (exp(h nu/(k T)) - 1); for cold gas the
     Rayleigh-Jeans shortcut underestimates Tex, and eta < 1 makes T_B a lower limit on Tex.
   - Hyperfine multiplets: the integrated intensity, line strength, A coefficient and g_u must refer to the
     same thing (one component or the whole multiplet). 2022A&A...657A.136E summed all components, scaled
     the strongest component by 9/5 for faint 15N isotopologues, and used the isolated faintest N2H+
     component (3/27 weight) as the thin one. State any scaling to the full multiplet.
6. **One line only.** Goal: a column or limit with an honest Tex range.
   - Take Tex from co-spatial species with more lines (PN over the 26-75 K range of other tracers in
     2024A&A...682A..74F; species tied to CH3OH in 2019A&A...624A..82B, or to SO2 in 2019ApJ...885...82L) or
     from the dust temperature (2016ApJ...830L..37I). Report the spread: factors 2.5 (PN) and 2.1 (PO) over
     5-50 K (2020MNRAS.492.1180R); more examples in `references/parameters.md` section 3. Bracketing with
     two fixed values is common (35 and 45 K in 2022A&A...657A.136E).
7. **Abundances, ratios, limits, mass.**
   - Divide by N(H2) from dust (Tdust 100 K, kappa 1.0 cm2/g, gas-to-dust 100 in 2020A&A...636A..67A) or a
     CO isotopologue, or quote ratios to CH3OH (2021A&A...656A..46M, 2019A&A...628A..10B). For C18O,
     2021A&A...656A..46M took 16O/18O = 100 and CO/H2 ~ 8e-5: N(H2) = 100 N(C18O) / 8e-5, factor 2
     uncertain (the pack's method line prints "18O/16O = 100", inverted).
   - Upper limits: 3 sigma on the integrated intensity at a stated Tex (100 K in 2018A&A...619A..28L), with
     the assumed linewidth (1.9 km/s in 2015ApJ...798..124R; 300 km/s for [CI] in 2021ApJ...908..163M),
     channel width, rms and channel correlation stated. For model-based limits, 2025ApJ...991...59B fixed
     Trot, width and velocity to the CH3OH values and varied only N; 2024A&A...681A.104B instead fixed the
     other parameters to medians from other molecules. General practice: sigma_W = rms dv sqrt(N_ch),
     inflated for correlated channels; for absorption, 2018A&A...620A.119D used integral tau dV ~
     3 sigma_tau sqrt(Delta V delta v).
   - Mass (general practice with the papers' formulas): M = mu m_H2 N(tracer)/X(tracer) A, A = Omega d^2.
     2015A&A...581A..85P used M ~ 1.4 m_H2 (N_C17O / X_C17O) A_beam; 2017ApJ...848..101V used 1.36 m_H2
     N_H2 A_source with filling factor 0.1. Apply the helium factor once, and pair a beam-averaged column
     with the beam area, a source column with the source area.
8. **Absorption against continuum (separate branch).** The emission formula does not apply.
   - Normalize by the continuum and fit opacity: Gaussian opacity components in MCWeeds
     (2019A&A...623A..68T); tau = 0.0057 from 40 mJy against 7 Jy with covering factor 1 and Tex 100 K,
     checked on continuum-unsubtracted images (2019ApJ...883..193N). State covering factor, Tex (or the CMB
     bound, 10.1 K in 2018A&A...620A.119D) and whether the line source function is neglected; N then
     follows from the integrated opacity. With f_c = 1, columns are lower limits (2018ApJ...864...73W).
   - Tex from two absorption lines: 2024ApJ...969..102N solved the tau(2-1)/tau(1-0) ratio without
     Rayleigh-Jeans; 2026ApJ..1000..141K fitted the Boltzmann opacity relation per velocity bin with tau < 1
     and used RADEX to exclude collisionally excited HCO+.
   - Check continuum coverage per transition and epoch before forming opacity ratios: different continuum
     sizes at different frequencies made ratios very uncertain in 2025A&A...700A..22O; 2026ApJ..1000..141K
     flags its two bands as nine months apart with no simultaneous monitoring, and a component whose
     covering factor could not be constrained. Normalize each line by its own continuum.
9. **Maps (optional).** Fit per pixel only with at least three lines and relative errors below 60%
   (2025A&A...693A..76C), or CH3CN K=3 above 3 sigma (2020ApJ...904..181L).

## Parameter defaults and ranges

Counts are my count of distinct bibcodes in the current pack's Key-parameter and Assumptions lists (capped
at 700 lines each, covering 301 and 362 of the 930 papers), so every count is a lower bound. "Earlier"
examples are pack papers outside the capped lists. Count rules and bibcode ledgers:
`references/parameters.md` section 10.

| Parameter | Common choice | Range seen | Papers (count) | Examples |
|---|---|---|---|---|
| Minimum lines for a free Trot | 3 | 2 (with Eup spread) to 6 (H2O) | 4 | 2024A&A...684A...4U, 2022MNRAS.512.4419P, 2023A&A...674A.125B; earlier 2020ApJ...890..142P |
| Detection threshold | 3 sigma (10 of 17) | 3 to 5 sigma | 17 | 2024A&A...689A..64B, 2025A&A...698A.261B, 2026A&A...711A.118A, 2021A&A...656A..46M, 2019A&A...623A..68T |
| Opacity limit on fitted lines | tau < 0.2 to 1 | 0.1 to about 3 | 4 | 0.2 2018A&A...616A..90C; 0.7 2025ApJS..276...49J; 1 2026ApJ..1000..141K; 2-3 2024A&A...681A.104B; earlier 0.1 2020A&A...635A..48M |
| Flux calibration error added | 10% (9 of 11) | 10 to 15% | 11 | 10%: 2025ApJ...985...84L, 2022A&A...664A.171V, 2023A&A...678A.160E; 15%: 2024A&A...689A..64B, 2025A&A...698A.261B |
| Error floor on N or Tex | 20% | 20 to 30% | 4 | 2024A&A...689A.248S, 2026ApJ..1004L...6D, 2026A&A...709A..93D; 30% 2024A&A...681A.104B |
| Beam filling, assumed | 1 | about 0.01 to 1 | 27 at unity (+3 ignore dilution) | unity: 2024A&A...689A..64B, 2021A&A...653A.129C; 0.5 2018A&A...618A..11T; 0.34 2025ApJ...994..158G; 0.1 2017ApJ...848..101V; 0.06 2015A&A...581A..48G |
| Beam filling, fitted | from data | 0.02 to 1 | 3 | 2025ApJS..276...49J (0.384, then fixed), 2020ApJ...904..181L, 2020ApJ...905..122H; earlier 2024ApJ...969..143I |
| Source size, hot cores | 0.5" (7) or continuum size (4) | 0.08" to 3" | 48 state a size | 2023MNRAS.525.6146W, 2018A&A...618A..11T, 2021ApJ...907..108G, 2025A&A...696A..18C |
| Fixed Tex, hot core / corino | 100 to 150 K | 80 to 300 K | 17 | 2024A&A...689A.248S, 2025ApJS..276...49J, 2019NatAs...3..314L, 2016A&A...590L...6C |
| Fixed Tex, cold gas / galaxies | 15 K (7 of 20) | 4.4 to 50 K | 20 | 2021A&A...656A..46M, 2017ApJ...848..101V, 2025ApJ...985..166K, 2022A&A...659A.158H |
| Free Tex bounds, hot cores / corinos | lower 10 to 50 K, upper 300 K | 10 to 550 K | 16 | 10-300 2025A&A...696A..18C; 80-300 2023MNRAS.525.6146W; 50-550 2020A&A...639A..87V; 10-500 2019A&A...624A..82B |
| Free Tex priors, disks | 10 to 100 K | 3 to 300 K | 2 | 10-100 2025A&A...698A.115R; 3-300 (CS), 10-35 (C34S) 2025ApJ...985...84L; earlier 2024A&A...689A..65R |
| Background temperature | 2.73 K CMB | CMB at z (3.69 to 19.2 K) to 132 K continuum | about 50 | 2018A&A...615A.141B, 2021ApJS..257....6G, 2024A&A...689A..67G |
| Ortho/para or A/E | o/p 3, A/E 1 | o/p 0.25 to 3 | 18 | 2018ApJ...864..170G, 2025ApJ...985...84L, 2024A&A...688L..22P, 2026A&A...707A.120H |
| 12C/13C (or 12CO/13CO) adopted | 68 to 70 (12 of 30) | 5 to 100 | 30 | 60 2015ApJ...813L..19J; 76 2015ApJ...798...85P; 100 2017A&A...608A..38O; 20 2025A&A...693A.160M; 8 2017A&A...597A..27S; 5 2022NatAs...6..275K |

Low isotope ratios are special cases: galactocentric-distance values (2021A&A...653A.129C), Sgr B2 = 20
(2025A&A...693A.160M), an adopted 12CO/13CO abundance of 8 (2017A&A...597A..27S), 5 only for 13CO lower
limits (2022NatAs...6..275K). Of the 362 papers in the Assumptions list, 227 state LTE and 115 thin emission.

## Software

Counts are from the pack aggregate "Software named in the matched steps" (one paper can name several).

| Tool | Used for | Count | Examples |
|---|---|---|---|
| CASSIS | LTE and RADEX-coupled fits; chi2 grids or MCMC | 136 | 2020A&A...644A..59K, 2025A&A...696A..18C, 2022A&A...657A.136E |
| MADCUBA (+ SLIM, AUTOFIT) | SLIM line ID, AUTOFIT LTE fits | 52 (+14, +8) | 2024A&A...682A..74F, 2020MNRAS.492.1180R, 2021A&A...656A..46M |
| Weeds (+ CLASS/Weeds, MCWeeds) | LTE synthetic spectra in GILDAS CLASS; MCWeeds adds priors and samplers | 55 (+10, +6) | 2016A&A...587A..91B, 2024A&A...681A.104B, 2019A&A...623A..68T |
| XCLASS (+ MAGIX) | LTE full-band modelling and optimisation | 52 (+17) | 2020A&A...636A..67A, 2025ApJS..276...49J, 2019ApJ...885...82L |
| CDMS / JPL (+ JPL catalog) / Splatalogue | frequencies, Aij, Eu, gu, Q | 48 / 14 (+6) / 11 | 2025A&A...696A..18C |
| emcee | posterior sampling of N and Tex (and of disk models) | 67 | 2023MNRAS.525.6146W, 2025A&A...698A.115R |
| SciPy, lmfit, pyspeckit | rotation-diagram, Gaussian and custom fits | 9, 7, 9 | 2020ApJ...890..142P, 2026ApJ..1000..141K |
| CASA | imaging and spectrum extraction | 58 | 2020A&A...636A..67A |
| RADEX (+ SpectralRadex), LIME, RADMC-3D | non-LTE or full radiative transfer | 134 (+12), 48, 30 | see non-lte-excitation |

The aggregates count papers that name each tool, not joint use, so the near-equal CASSIS and RADEX totals
say nothing about how often both appear in one paper. Some papers do run an LTE fit and a RADEX check on
the same data (2015A&A...581A..85P, 2020MNRAS.492.1180R, 2026ApJ..1000..141K); 2024A&A...689A..64B used
the LVG code grelvg after its diagrams. LTE code versions are rarely stated (XCLASS version flagged as not
stated in 2020A&A...636A..67A).

## Pitfalls

- **Opacity.** Thick lines bias thin-assumption columns low (mildly thick lines underestimate N by a factor
  of a few, 2020A&A...644A.119P). In 2016A&A...587A..91B (card) a uniform single-component model could not
  fit the very thick lines, and formal diagram errors on Trot were not the true errors. That is a limit of
  that model, not of LTE: 2020ApJ...905..122H reproduced CO peak intensities with 12CO opacities up to 76
  by fitting the opacity explicitly. CH3OH and CH3CN can be thick in hot cores (2019NatAs...3..314L,
  2020ApJ...898...54T).
- **Background continuum.** The diagram assumes the continuum is negligible next to Tex; toward Sgr B2(N1S)
  that failed and urea's Trot = 350 +/- 190 K was unreliable (2019A&A...628A..10B). Raising the baseline by
  1 rms raised N by factors 1.2 to 1.8 (2025A&A...696A..18C); a 2.73 K background may be wrong next to an
  AGN (2020MNRAS.496.5308S).
- **Beam filling.** A fixed filling factor makes N a lower limit by about 2 to 3 (2025ApJS..276...49J,
  card); ignoring dilution of unresolved emission underestimates N (2025A&A...693A.101T,
  2025A&A...696A..31G); size and N are degenerate (2025A&A...696A..18C); Trot and filling factor
  correlated at 0.99 (2020ApJ...905..122H). Column comparisons depend on beam, distance and dilution
  (2023MNRAS.525.6146W).
- **Tex-N degeneracy.** About a factor 2 on N for a poorly constrained species (2020A&A...644A..84M); one
  transition leaves Tex unconstrained (2024A&A...682A..74F).
- **What Trot means.** Limited Eu coverage gave unrealistically low Trot of 10 to 20 K (2024A&A...684A...4U);
  a bent diagram means Trot is not the gas temperature (2025A&A...698A.261B); treat thin-line Trot as a
  lower limit to Tkin (2014A&A...570A..28V, 2013PASJ...65..100I). At low Tex the Rayleigh-Jeans form fails
  (2024ApJ...969..102N).
- **Uncertainties too small.** Fit errors usually exclude calibration (2021A&A...656A..46M) and
  fixed-parameter systematics (2026A&A...707A.120H, 2025A&A...696A..18C).
- **Blends.** About 20% of lines stayed unidentified in V883 Ori (2025ApJS..276...49J, card).
- **Partition function.** Include vibrational and conformer terms: factors 1.64 to 2.36 at 150 K for propyl
  cyanide (2014Sci...345.1584B), 2.1 for CH3OCHO torsional states (2019ApJ...880..130M); CH2DOH
  spectroscopy uncertain by about 3 (2024AJ....167...66Y). One temperature does not fit mixed gas
  (2017A&A...608A..38O).
- **Settings papers leave out.** Cards most often flag CASA version (42), continuum subtraction and
  line-free channels (26 each under three phrasings), flux scale uncertainty (19) and flux calibration
  uncertainty (15) as not stated (pack aggregate); also rotation-diagram weighting (2020ApJ...890..142P)
  and XCLASS sizes and MCMC settings (2020A&A...636A..67A). State all of them.

## Verification checks

What the papers did:
- Compare the diagram with the full-spectrum fit: 0.28 dex scatter and 0.03 dex offset in
  2025ApJS..276...49J (card).
- Check thinness a posteriori (2014Sci...345.1584B) or with isotopologue ratios (2024A&A...682A..74F).
- Inspect residuals over the band: no bright predicted line missing or exceeded (2021A&A...656A..46M);
  search residual peaks above 5 then 4 sigma (2019A&A...623A..68T).
- Scan Tex and report the change in N (2020MNRAS.492.1180R). Sampler checks: another seed and a chain
  longer than 3000 steps (2023MNRAS.525.6146W); a shorter burn-in did not change the fit (2025A&A...696A..18C).
- Perturb inputs: baseline +1 rms, other pixels (2025A&A...696A..18C); 12CO/13CO from 50 to 200
  (2017A&A...608A..38O); 0.4 against 0.8 km/s channels (2025A&A...698A.115R).
- Derive N from each transition separately; disagreement means an assumption failed (2020MNRAS.496.5308S,
  2014A&A...570A..28V).
- Fit with two methods and compare with single-dish values (2022A&A...657A.136E); cross-check with non-LTE
  (2015A&A...581A..85P, 2026ApJ..1000..141K); test the source size (2021A&A...656A..46M, 2023MNRAS.525.6146W).

What a careful referee adds (recommendation, not pack evidence): show every diagram point including
excluded lines; make Eup span at least about Trot; fold flux-scale and fixed-parameter systematics into N;
state the Q(T) source, background temperature, source size and spin-state convention.

## Source cards

All 930 papers are listed in `references/sources.md`. Most informative for this technique:

- 2016A&A...587A..91B: Weeds full-spectrum LTE plus opacity-corrected diagrams, Sgr B2(N2)
- 2019A&A...628A..10B: urea; diagram compromised by the continuum background
- 2014Sci...345.1584B: diagrams after subtracting contaminants; vibrational Q corrections
- 2020ApJ...890..142P: iterative opacity-corrected H2CO diagrams in 15 disks
- 2018ApJ...864..170G: H2CO diagram in HD 163296 with LTE justification and o/p convention
- 2025ApJS..276...49J: XCLASS + MAGIX, tau < 0.7, comparison with rotation diagrams
- 2020MNRAS.492.1180R: MADCUBA with fixed Tex, Tex sensitivity, RADEX cross-check
- 2021A&A...656A..46M: ALCHEMI survey fit, detection criterion, source size test
- 2025A&A...693A.160M: Sgr B2 hot cores, line overlap with an average source function
- 2019A&A...623A..68T: MCWeeds priors and automated component search in absorption
- 2022A&A...657A.136E: hyperfine bookkeeping, CASSIS MCMC against CLASS HFS
- 2020ApJ...905..122H: LTE fit of thick CO with opacity and filling factor
- 2025A&A...696A..18C: CASSIS MCMC, median- and CH3OH-constrained refits, baseline and pixel tests
- 2025A&A...698A.261B: two-component diagrams, bent diagrams as non-LTE evidence
- 2024ApJ...969..102N, 2026ApJ..1000..141K: Tex from absorption-line opacity ratios
- 2025ApJ...991...59B: LTE first, non-LTE only if needed; model-based upper limits
