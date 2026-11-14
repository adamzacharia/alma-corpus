---
name: alma-rotational-diagram-lte
description: "Derive rotational/excitation temperatures and LTE column densities from ALMA molecular lines: rotation (population) diagrams with opacity correction, full-spectrum LTE fitting in XCLASS, MADCUBA (SLIM/AUTOFIT), CASSIS or Weeds/MCWeeds, single-line LTE columns at an assumed Tex, and the abundance, isotopologue and deuteration ratios built on them. Use when a task asks for Trot or Tex, N_tot, a COM inventory, an LTE upper limit, or an LTE gas mass from line fluxes or spectra. Built from 375 ALMA papers (2012-2026)."
---

# Rotational diagrams and LTE column densities

Measures a single excitation (rotational) temperature and a total column density per species, assuming
level populations follow a Boltzmann distribution. The two mistakes that matter most: treating optically
thick or continuum-affected lines as thin (biases Trot and underestimates N), and quoting a column from one
line at an assumed Tex without showing how N moves over a plausible Tex range. Beam filling (source size) is
the third silent assumption: many papers set it to 1 (24 by my count, see the parameter table), which gives a
beam-averaged column, not the intrinsic source column. With a fixed filling factor, 2025ApJS..276...49J
states its columns are lower limits by a factor of about 2 to 3.

## When to use

- Several transitions of one species spanning a range of upper-level energies: fit a rotation (population)
  diagram or an LTE synthetic spectrum for Trot and N (2020ApJ...890..142P, 2014Sci...345.1584B,
  2018A&A...620A..75K).
- Line-rich hot cores, hot corinos and warm disks where every species must be modelled at once to handle
  blends: full-spectrum LTE modelling with Weeds (2016A&A...587A..91B, 2019A&A...628A..10B), XCLASS
  (2020A&A...636A..67A, 2025ApJS..276...49J), MADCUBA (2024A&A...682A..74F, 2021A&A...656A..46M) or CASSIS
  (2020A&A...644A..59K).
- One line only, and a column, mass or upper limit is still needed at an assumed Tex (2020MNRAS.492.1180R,
  2015ApJ...798..124R, 2018A&A...619A..28L).
- Isotopologue, deuteration and molecule-to-molecule ratios, which need N for each species under shared
  assumptions (2016A&A...587A..91B, 2019A&A...628A..10B, 2020A&A...636A..67A).
- Tex from a ratio of two lines of the same species under LTE (CO R32 gave Tex = 29 K in 2017A&A...608A..38O;
  a [CI] ratio gave Tex = 44 +/- 16 K in 2024ApJ...977..251H), or from the peak brightness of an optically
  thick line (2026A&A...705A.198M, 2021A&A...648A..19W).
- Gas dense enough that LTE is defensible. Papers justify it with densities well above the critical density,
  for example n > 1e6 cm^-3 (2018ApJ...864..170G), n ~ 1e8 cm^-3 (2020A&A...644A..84M), n_H2 >~ 1e10 cm^-3
  (2018A&A...620A.170J), n_H2 >> n_crit ~ 1e5 cm^-3 (2019ApJ...882..118X).

## When not to use

- You need kinetic temperature and density, or there is evidence the levels are not thermalized (density
  plausibly below the critical density of the lines used, radiative pumping or fluorescence, a non-LTE
  check that disagrees): use the **non-lte-excitation** skill (RADEX, LVG grids, LIME, RADMC-3D non-LTE).
  The pack shows why: in HH 212, RADEX columns were a factor 2 to 4 above the LTE optically thin ones
  (2015A&A...581A..85P); the LTE assumption was "found not to hold" in 2016ApJ...833...41Z; ALCHEMI
  residuals revealed non-LTE deviations (2021A&A...656A..46M). The collider species alone does not decide
  it: debris-disk work scans electron density "from the radiation-dominated regime to LTE"
  (2016MNRAS.460.2933M) and runs both LTE and non-LTE fits with fluorescence (2020MNRAS.497.2811K), and a
  comet study pairs a CH3OH rotational diagram with non-LTE LIME modelling of H2O and electron collisions
  and pumping (2019ApJ...870L..26C). Where electron density or radiation field is unknown, bracket the
  result with a non-LTE scan instead of assuming LTE.
- Resolved disk temperature and abundance structure fitted to visibilities (parametric disk plus RADMC-3D or
  LIME plus emcee, as in step 3 of 2018ApJ...864..170G): use **radiative-transfer-modelling** or
  **uv-plane-fitting**.
- Molecular gas mass from CO with an alpha_CO or X_CO factor: use **gas-mass-co-conversion**. Isotope ratio
  science: **isotopic-ratios**. Assigning lines in the first place: **line-identification**.
- Thermal free-free "LTE" (solar, HII regions) is a different calculation (2020ApJ...888L..28S,
  2017A&A...605A..78A): use **free-free-synchrotron**.
- Masers: excluded from LTE analyses (2018A&A...615A..28D).

## Steps

1. **Prepare the spectrum.**
   - Goal: a continuum-subtracted spectrum in brightness temperature, from a region where one set of
     physical conditions is plausible.
   - Method: extract from a beam-sized aperture (1.6" in 2024A&A...689A..64B), the line peak pixel
     (2020A&A...636A..67A), a 3" circle (2020MNRAS.492.1180R) or a disk mask (6" in 2018ApJ...864..170G).
     Convert Jy/beam to K with the beam of that cube; a flux integrated over an aperture larger than the
     beam is in Jy, not Jy/beam, and needs the aperture solid angle instead.
   - Common spatial response (required before combining lines): papers assume all lines come from the same
     environment (2020ApJ...890..142P) or share one spatial distribution so a beam-coupling factor can be
     applied (2025A&A...696A.100G), and warn when comparing different physical scales
     (2024A&A...689A..64B). Match beams and apertures across lines (smooth to the coarsest), check that the
     recoverable scale of each setup covers the emission (resolved-out flux lowers fluxes:
     2018A&A...615A..28D, 2019A&A...624A.125M), or model the differences explicitly.
   - Continuum: if it is bright, keep its level so it can act as the background term
     (2018A&A...616A..90C; Tbg = 21 K from dust in 2018A&A...619A..28L). A continuum brightness
     temperature is not the same as a physical blackbody background temperature; state which one enters the
     radiative-transfer equation.
   - Dust attenuation: 2025ApJS..276...49J divided line intensities by exp(-tau_dust) after fitting N_H2
     and a filling factor eta to the continuum, under its stated assumption that dust and gas are well
     coupled and the gas is in LTE. That correction is geometry dependent (foreground dust, mixed dust and
     gas, temperature differences); apply it only with a stated line-dust transfer model that justifies it.
   - Software: CASA, GILDAS CLASS, MADCUBA, STATCONT for continuum (see **continuum-subtraction**).
2. **Identify lines and choose the ones to fit.**
   - Goal: a list of transitions that are detected, unblended and have trusted spectroscopy.
   - Method: build an LTE model of all species across the band, then keep transitions not severely blended
     (2014Sci...345.1584B). Automated screening: XCLASS model spectra for about 1500 species at 35 column
     steps, kept only if every predicted line matched, then visual inspection (2025ApJS..276...49J).
     Detection rules seen: 3 sigma integrated intensity and reject lines more than 15% contaminated
     (2024A&A...689A..64B); a species counts only if all unblended transitions predicted above 5 sigma are
     seen (2021A&A...656A..46M). Line cuts seen: Aij >= 1e-3 s^-1 and Eup <= 500 K (2019A&A...624A..70C),
     Eup <= 300 K and A >= 1e-6 s^-1 (2025A&A...693A.101T), Eu < 250 K for the main fit
     (2020A&A...644A..84M).
   - Software: CDMS and JPL catalogues (counts under Software), XCLASS, Weeds, MADCUBA SLIM.
3. **Rotation (population) diagram.**
   - Goal: Trot and N from the slope and intercept.
   - Method (general practice): for each line, N_u = 8 pi k nu^2 W / (h c^3 A_ul) in cgs, with W the
     integrated intensity in K cm/s (Rayleigh-Jeans, thin, beam-filling, background negligible). In
     practical units: N_u [cm^-2] = 1.94e3 nu[GHz]^2 W[K km/s] / A_ul[s^-1]. Do not plug K km/s straight
     into the cgs form; that loses a factor 1e5. Then fit ln(N_u/g_u) = ln(N_tot/Q(Trot)) - E_u/(k Trot).
     Correct for opacity with C_tau = tau/(1 - exp(-tau)) and, for a circular Gaussian source in a circular
     Gaussian beam, for beam dilution with (theta_s^2 + theta_b^2)/theta_s^2 when a source size is adopted.
   - Spin and symmetry states: decide first whether the column you report is one state (ortho, para, A, E)
     or the total. Use a partition function and g_u from the same catalogue entry and convention (some
     entries include the spin weight, some treat each state as a separate species), and convert to a total
     column once, with a stated ratio: 2018ApJ...864..170G assumed o/p = 3 to get the total H2CO abundance;
     2024ApJ...969..143I fitted para-H2CO only, so no ratio was needed. Never apply the spin correction both
     in Q and again afterwards.
   - What papers do: iterate the opacity correction from a C_tau = 1 start until tau and Tex change by at
     most 0.001% (2020ApJ...890..142P); correct the population diagram for optical depth with the
     opacities delivered by the Weeds LTE model and subtract the modelled emission of contaminating species
     (2016A&A...587A..91B); 2014Sci...345.1584B built its diagrams from lines not too severely blended,
     after removing the contaminating-molecule model, and assumed thin lines, which it verified a
     posteriori. Add the absolute flux uncertainty in quadrature (10% in 2020ApJ...890..142P, 15% in
     2024A&A...689A..64B). 2019ApJ...872..200H (card) quotes "a conservative error of 20% for the
     ln(E_u/g_u) values"; that wording is anomalous (the ordinate is ln(N_u/g_u), and a percentage of a
     logarithm depends on units), so do not copy it. Instead propagate the intensity error to the ordinate,
     sigma_ln = sigma_W / W, add the calibration term as sigma_cal / W (fractional), and treat the
     calibration error as correlated among lines from the same setup or tuning (it shifts N, not Trot,
     when all lines share it). Fit one to three temperature components when the diagram curves
     (2024A&A...689A..64B; 22 and 59 K for C2H in 2025A&A...696A.100G). Require at least three lines
     (2020ApJ...890..142P, 2020ApJ...890...76N, 2025A&A...694A.166C).
   - Software: Python/NumPy/SciPy (2020ApJ...890..142P), Weeds output, or any linear fitter.
4. **Full-spectrum LTE fit.**
   - Goal: N, Tex, source size, FWHM and velocity per species, fitting blends jointly.
   - Method: one synthetic LTE spectrum per species, summed (Weeds with five model parameters: N,
     temperature, source size, velocity offset and linewidth, in 2014Sci...345.1584B and
     2016A&A...587A..91B; in the latter "the other four parameters were optimized by eye", so not all five
     were free; MADCUBA AUTOFIT with V, FWHM, Tex, N free and size fixed in 2024A&A...682A..74F). Fix FWHM from unblended
     lines, fit Tex only when at least 2 lines span a range of Eup, otherwise fix it (100 K, or 300 K for
     some species, in 2024A&A...686A..59N). Exclude lines the model says are thick: tau < 0.7
     (2025ApJS..276...49J), tau < 0.5 (2019A&A...622A.206M), tau < 0.2 (2018A&A...616A..90C), tau < 0.1
     (2020A&A...635A..48M). Penalise over-prediction (weight 3 when the model exceeds the data in
     2020A&A...635A..48M).
   - Optimisers seen: by eye (2016A&A...587A..91B, 2019A&A...628A..10B); Levenberg-Marquardt in
     MADCUBA-AUTOFIT (2020MNRAS.492.1180R); MADCUBA least squares with only statistical errors
     (2021A&A...656A..46M); genetic algorithm for the best fit plus MCMC errors in XCLASS/MAGIX
     (2025ApJS..276...49J); genetic, Levenberg-Marquardt and errorestim-ins in MAGIX (2019ApJ...885...82L,
     algorithms in the pack, XCLASS/MAGIX from the card); XCLASS errorestim_ins MCMC (2020A&A...636A..67A);
     MCWeeds with priors and Powell minimisation (2019A&A...623A..68T); emcee with uniform Tex and N priors
     (2024A&A...689A..65R; emcee named in the card) and emcee with 300 walkers and 1500 steps
     (2024A&A...687A.220I; emcee named in the card); regular chi2 grids (2019A&A...624A..82B,
     2020A&A...644A..59K).
5. **Handle optically thick species.**
   - Goal: avoid the saturated main isotopologue.
   - Method: fit a rare isotopologue and scale: CH3OH from 13CH3OH times 60 (2019NatAs...3..314L); main
     species from 13C isotopologues with 12C/13C (2016A&A...587A..91B). Check opacity with isotopologue
     intensity ratios (28SiO/29SiO ~ 8 and ~ 20 in 2024A&A...682A..74F; a 12CO/13CO line ratio of 2.0
     gave tau_12CO ~ 56 and tau_13CO ~ 0.7 in 2015ApJ...798...85P, assuming the same Tex for both lines,
     CMB neglected and an abundance ratio of 76).
   - Tex from a thick line: 2026A&A...705A.198M set the CO Tex equal to the measured peak brightness
     temperature. That is an approximation that holds only when the line is very thick, fills the beam,
     the background is negligible and h nu << k Tex. In general (general practice), invert
     T_B = eta [J_nu(Tex) - J_nu(T_bg)] (1 - exp(-tau)), with J_nu(T) = (h nu/k) / (exp(h nu/(k T)) - 1)
     and eta the filling factor; for cold gas at ALMA frequencies the Rayleigh-Jeans shortcut T_B ~ Tex
     underestimates Tex, and eta < 1 makes T_B a lower limit on Tex.
6. **One line only.**
   - Goal: a column or limit with an honest Tex range.
   - Method: take Tex from co-spatial species fitted with more lines (PN fitted over the 26-75 K range of
     other tracers in 2024A&A...682A..74F; minor species tied to CH3OH in 2019A&A...624A..82B or to SO2 in
     2019ApJ...885...82L), or from the dust temperature (2016ApJ...830L..37I). Report the spread: N changed by
     factors 2.5 (PN) and 2.1 (PO) over 5-50 K (2020MNRAS.492.1180R), by 40% for Tex +/- 20 K
     (2016ApJ...825...79S), by less than 20% over 20-50 K (2024ApJ...963...72O).
7. **Abundances, ratios, limits.**
   - Method: divide by N(H2) from dust (Tdust 100 K, kappa 1.0 cm2/g, gas-to-dust 100 in
     2020A&A...636A..67A) or from a CO isotopologue, or quote ratios to CH3OH or formamide
     (2021A&A...656A..46M, 2019A&A...628A..10B). For the CO route, 2021A&A...656A..46M took
     16O/18O = 100 (its measured HCO+ value, 100 +/- 20) and CO/H2 ~ 8e-5, so
     N(H2) = 100 N(C18O) / 8e-5, with a factor 2 uncertainty. Note the pack's method line for that step
     prints the ratio as "18O/16O = 100"; that is inverted (it must be 16O/18O, as the paper's Oxygen result
     states).
   - Upper limits: papers quote 3 sigma on the integrated intensity at a stated Tex (100 K in
     2018A&A...619A..28L), but the limit is only reproducible with the width used. State the assumed
     linewidth (FWHM 1.9 km/s for the CO limit in 2015ApJ...798..124R; Delta v = 300 km/s for [CI] in
     2021ApJ...908..163M), the channel width, the rms per channel and how channel correlation was treated.
     General practice for a box integration over N_ch channels of width dv: sigma_W = rms dv sqrt(N_ch),
     inflated for correlated channels (for example Hanning smoothing); for absorption,
     2018A&A...620A.119D used integral tau dV ~ 3 sigma_tau sqrt(Delta V delta v). Show the arithmetic.
   - Mass from a column (general practice, with the papers' formulas): M = mu m_H2 N(H2) A, with
     N(H2) = N(tracer) / X(tracer) and A the physical area (A = Omega d^2). 2015A&A...581A..85P used
     M_disk ~ 1.4 m_H2 (N_C17O / X_C17O) A_beam summed over the blue and red lobes; 2017ApJ...848..101V used
     M_mol = 1.36 m_H2 N_H2 A_source with filling factor 0.1, 12CO/13CO = 50 and 12CO/H2 = 1e-4. The 1.36
     to 1.4 factor adds helium; say which you use and do not apply it twice (2021ApJ...908..163M quotes a
     helium factor of 1.36 separately from its [CI] H2 mass). Keep the filling convention consistent: a
     beam-averaged column goes with the beam or aperture area, a source-intrinsic column with the source
     area.
8. **Absorption against continuum (separate branch).**
   - The emission formula for N_u does not apply. Normalize by the continuum, I/I_c, and fit opacity, not
     brightness: 2019A&A...623A..68T fitted Weeds spectra with Gaussian opacity components (N, FWHM, v0 per
     component) through MCWeeds; 2019ApJ...883..193N derived tau = 0.0057 from 40 mJy absorption against a
     7 Jy continuum under LTE, a covering factor of 1 and Tex 100 K, and checked the feature on
     continuum-unsubtracted images. State the covering factor, the Tex (or the CMB lower bound used in
     2018A&A...620A.119D, 10.1 K at its redshift) and whether the line's own source function is neglected
     against the continuum; then N_tot follows from the integrated opacity.
9. **Maps of Trot and N (optional).**
   - Method: fit pixel by pixel, only where enough lines are detected: at least three lines per pixel and
     display only relative errors below 60% (2025A&A...693A..76C); pixels above 5 sigma
     (2018ApJ...856..147O).

## Parameter defaults and ranges

Counts are my count of distinct pack bibcodes whose parameter or assumption lines state the setting, not of
all 375 papers. The longer table, with typical fitted temperatures by environment, is in
`references/parameters.md`.

| Parameter | Common choice | Range seen | Papers (count) | Examples |
|---|---|---|---|---|
| Minimum lines for a free Trot | 3 | 2 (with Eup spread) to 3 | 5 | 2020ApJ...890..142P, 2025A&A...694A.166C, 2024A&A...686A..59N |
| Detection threshold | 3 sigma | 3 to 5 sigma | 9 | integrated intensity 3 sigma: 2024A&A...689A..64B; line or component peak 3 to 3.5 sigma: 2024ApJ...962...48J, 2019ApJ...875...24C; 3 sigma, type not stated: 2020ApJ...890...76N, 2025A&A...694A.166C; model-predicted lines: 3 sigma match 2019ApJ...872..196S, 5 sigma 2021A&A...656A..46M; absorption dips 4 sigma: 2019A&A...623A..68T; map pixels 5 sigma: 2018ApJ...856..147O |
| Opacity cut for fitted lines | tau < 0.2 to 0.7 | 0.1 to 0.7 | 5 | 2020A&A...635A..48M, 2018A&A...616A..90C, 2025ApJS..276...49J |
| Flux calibration error added | 10% | 10 to 20% | 5 | 2020ApJ...890..142P, 2024A&A...689A..64B, 2017ApJ...843..150F |
| Beam filling, assumed | 1 (source fills beam) | 0.1 to 1 | 24 at unity | unity: 2024A&A...689A..64B, 2024A&A...686A..59N, 2020A&A...644A..59K; 0.5: 2020A&A...635A..48M; 0.1: 2017ApJ...848..101V |
| Beam filling, fitted | eta from data | 0.384; restricted < 1 | 2 | 2025ApJS..276...49J (fitted to the continuum, then fixed for lines), 2024ApJ...969..143I |
| Fixed source size (hot cores, corinos) | 0.5" (9 papers) | 0.15" to 3" (5" to 10" in galaxies) | about 30 | 2018A&A...616A..90C, 2019A&A...628A..10B, 2019A&A...631A..64B, 2021A&A...656A..46M |
| Fixed Tex, hot core / corino | 100 to 150 K | 100 to 300 K | 9 | 2024A&A...686A..59N, 2018A&A...620L...6T, 2019A&A...623A..93C |
| Fixed Tex, cold gas / galaxies | 15 to 25 K | 5 to 50 K | 8 | 2021A&A...656A..46M, 2020MNRAS.492.1180R, 2020MNRAS.493L.108B |
| Free Tex bounds, hot cores | 25 to 90 K up to 300 to 400 K | 10 to 500 K | 6 | 2020A&A...636A..67A, 2019A&A...624A..82B, 2018A&A...619A..28L, 2018A&A...616A..90C, 2015ApJ...813L..19J, 2019A&A...623L...6P |
| Free Tex priors, disks (emcee) | open from 0 K | (0, 50) K to (0, 100) K | 1 | 2024A&A...689A..65R |
| Background temperature | 2.73 K CMB | CMB to 132 K continuum | 6 | 2019A&A...623A..96Y, 2018A&A...616A..90C, 2018A&A...615A.141B |
| Ortho/para or A/E | 3 (o/p), 1 (A/E) | o/p 1 to 3 | 8 | 2024A&A...689A..65R, 2024ApJ...968L..19F, 2026A&A...707A.120H |
| 12C/13C (or 12CO/13CO) adopted | 50 to 70 | 50 to 100 | 23 | 50: 2017MNRAS.466...49J; 60: 2019NatAs...3..314L; 62: 2016ApJ...832..158Z; 69 to 70: 2019A&A...632A..19T; 76: 2015ApJ...798...85P; 100: 2017A&A...608A..38O |

Assumption tallies (my count of distinct bibcodes in the pack's Assumptions list, where 354 papers have at
least one line): 201 state LTE, 93 state optically thin emission.

How the recounted rows were made (my count over the current pack's Key-parameter and Assumptions lines):
- Beam filling at unity: a bibcode counts if a line says filling factor 1 or unity, emission or source
  fills the beam, beam dilution unity, or negligible beam dilution. 19 from the Assumptions list
  (2024A&A...682A..74F, 2020ApJ...890..142P, 2019A&A...623A..68T, 2024A&A...689A..64B,
  2016ApJ...832..158Z, 2025A&A...693A.101T, 2025A&A...696A..31G, 2018A&A...615A.141B, 2020MNRAS.497.5454I,
  2024A&A...686A..59N, 2020ApJ...889...43Z, 2019ApJ...876...72L, 2024A&A...692A..97M, 2019ApJ...882..118X,
  2019ApJ...871..112X, 2020A&A...641A.104A, 2018ApJ...856..147O, 2025A&A...695A.149K, 2016ApJ...823...91S)
  plus 5 more only in Key parameters (2020A&A...644A..59K, 2020ApJ...898...54T, 2020A&A...644A..84M,
  2019ApJ...871..170M, 2017A&A...605L...6T) = 24. Not counted: "about 1" (2025A&A...699A.369V), equal
  but unspecified factors between lines, and source size equal to the synthesised beam
  (2019A&A...624A..82B), which is not unity filling for a Gaussian source.
- 12C/13C: distinct bibcodes adopting a numerical 12C/13C or 12CO/13CO abundance ratio: 6 at 50, 5 at 60,
  1 at 62, 1 at 65, 8 at 68 to 70, 1 at 76, 1 at 100 = 23. Excluded: 12CO/13CO = 8 in the planetary
  nebula NGC 6302 (2017A&A...597A..27S), an environment-dependent ~50 to ~100 (2016ApJ...825...44I), and
  an unquoted ISM value (2026A&A...705A.198M). Measured ratios, such as 22 +/- 2 in NGC 253
  (2021A&A...656A..46M), are results, not scaling inputs.
- Detection threshold: distinct bibcodes whose Key-parameter line states a sigma cut for detecting or
  fitting lines, split by what the cut applies to in the table row.

## Software

Counts are from the pack aggregate "Software named in the matched steps" (one paper can name several).

| Tool | Used for | Count | Examples |
|---|---|---|---|
| CASSIS | LTE and RADEX-coupled chi2 fits of line sets | 27 | 2020A&A...644A..59K |
| MADCUBA (+ MADCUBAIJ) | SLIM line ID, AUTOFIT LTE fits (Levenberg-Marquardt in 2020MNRAS.492.1180R) | 23 (+3) | 2024A&A...682A..74F, 2020MNRAS.492.1180R, 2021A&A...656A..46M |
| Weeds (+ MCWeeds) | LTE synthetic spectra in GILDAS CLASS; MCWeeds adds priors and samplers | 21 (+4) | 2016A&A...587A..91B, 2019A&A...628A..10B, 2019A&A...623A..68T |
| XCLASS (+ MAGIX) | LTE full-band modelling; MAGIX genetic, Levenberg-Marquardt, errorestim_ins | 18 (+6) | 2020A&A...636A..67A, 2025ApJS..276...49J, 2019ApJ...885...82L |
| CDMS / JPL | spectroscopic catalogues (frequencies, Aij, Eu, gu, Q) | 10 / 4 | 2025ApJS..276...49J, 2019A&A...631A..64B |
| emcee | posterior sampling of N and Tex (and of disk models) | 26 | 2024A&A...689A..65R, 2024A&A...687A.220I (both from the cards) |
| SciPy, lmfit, mpfit | rotation-diagram and custom fits | 3, 3, 2 | 2020ApJ...890..142P |
| CASA | imaging and spectrum extraction | 23 | 2020A&A...636A..67A |
| RADEX, LIME, RADMC-3D | non-LTE or full radiative transfer run alongside LTE | 48, 22, 17 (+3) | see non-lte-excitation |

RADEX is the single most named tool in these steps because many papers run an LTE fit and a RADEX
non-LTE check side by side (2015A&A...581A..85P, 2020MNRAS.492.1180R, 2019A&A...623A..68T). Other papers
use a different LVG code for the same cross-check (grelvg after rotation diagrams in 2024A&A...689A..64B). Version numbers of the LTE
codes are rarely stated in the cards (XCLASS version is flagged as not stated in 2020A&A...636A..67A).

## Pitfalls

- **Opacity.** A uniform single-component LTE model cannot fit very thick lines, and formal Trot errors from
  the diagram are not the true errors (2016A&A...587A..91B). Mildly thick lines underestimate N by a factor
  of a few (2020A&A...644A.119P). CH3OH and CH3CN can be thick in hot cores (2019NatAs...3..314L,
  2020ApJ...898...54T).
- **Background continuum.** The population diagram assumes the continuum is negligible next to Tex; at
  high resolution toward Sgr B2(N1S) that failed and urea's Trot = 350 +/- 190 K had to be viewed with
  caution (2019A&A...628A..10B). Thick dust makes N_H2 a lower limit (2018A&A...615A.141B); continuum
  over-subtraction removes line flux (2025A&A...693A.101T); STATCONT is not optimal for faint lines
  (2021A&A...656A..46M).
- **Beam filling.** A fixed filling factor makes N a lower limit by about 2 to 3 (2025ApJS..276...49J);
  unresolved emission with beam dilution ignored underestimates N (2025A&A...693A.101T,
  2025A&A...696A..31G).
- **Tex-N degeneracy.** About a factor 2 on N for a poorly constrained species (2020A&A...644A..84M); with
  one transition Tex is unconstrained (2024A&A...682A..74F, 2020A&A...644A.119P) and upper limits depend on
  the assumed Tex (2024A&A...686A..59N).
- **Uncertainties too small.** Fit errors usually exclude calibration (2021A&A...656A..46M,
  2020ApJ...892...99C) and systematics from fixed parameters (2026A&A...707A.120H); errors were judged
  underestimated in 2020A&A...644A..59K.
- **Blends and unidentified lines.** About 20% of lines stayed unidentified in V883 Ori
  (2025ApJS..276...49J); unidentified blends can bias fits (2020A&A...644A..84M).
- **Partition function and spectroscopy.** Include vibrational and conformer contributions: factors 1.64 to
  2.36 at 150 K for propyl cyanide (2014Sci...345.1584B), a factor 2.1 for torsional states of CH3OCHO
  (2019ApJ...880..130M); CH2DOH spectroscopy was uncertain by about a factor 3 (2024AJ....167...66Y).
- **Several gas components.** One temperature is not appropriate for mixed gas (2017A&A...608A..38O); fit
  two or three components when the diagram bends (2024A&A...689A..64B).
- **Spatial filtering.** Extended emission resolved out by the interferometer lowers fluxes
  (2018A&A...615A..28D, 2019A&A...624A.125M).
- **Settings papers leave out.** The cards most often flag CASA version (29), continuum subtraction and
  line-free channels (23, 19 and 15 under different phrasings) and flux scale uncertainty (13) as not
  stated. For this technique the cards also flag the rotation-diagram weighting (2020ApJ...890..142P), the
  XCLASS source sizes and MCMC settings (2020A&A...636A..67A), the MAGIX settings (2025ApJS..276...49J) and
  the by-eye tolerances (2016A&A...587A..91B). State all of them.

## Verification checks

What the papers did:
- Compare the rotation diagram with the full-spectrum fit: 0.28 dex scatter and 0.03 dex offset in
  2025ApJS..276...49J; diagrams used to confirm by-eye Weeds temperatures in 2016A&A...587A..91B.
- Check optical thinness a posteriori (2014Sci...345.1584B) or with isotopologue ratios
  (2024A&A...682A..74F).
- Inspect residuals over the whole band: no bright predicted line may be missing or exceeded
  (2021A&A...656A..46M); search residual peaks above 5 then 4 sigma for missed components
  (2019A&A...623A..68T).
- Scan Tex and report the change in N (2020MNRAS.492.1180R).
- Check blends with a comparison line of the suspected contaminant (ethanol at 217803.69 MHz in
  2020A&A...636A..67A; H alpha recombination lines in 2019A&A...628A..10B).
- Show that the Eup range is similar across sources being compared and that densities exceed critical
  densities (2020ApJ...890..142P).
- Cross-check with non-LTE (2015A&A...581A..85P) or with earlier temperatures for the same source
  (2018ApJ...864..170G, 2026A&A...707A.120H).
- Test the source-size assumption (CO isotopologues refitted for a 10" size in 2021A&A...656A..46M).

What a careful referee adds (recommendation, not pack evidence): show the diagram with every point,
including excluded lines and why; make sure Eup spans at least about Trot; quote N with flux-scale and
fixed-parameter systematics folded in; state the Q(T) source, background temperature and source size.

## Source cards

All 375 papers are listed in `references/sources.md`. Most informative for this technique:

- 2016A&A...587A..91B: Weeds full-spectrum LTE plus opacity-corrected population diagrams, Sgr B2(N2)
- 2019A&A...628A..10B: urea; population diagram compromised by the continuum background
- 2014Sci...345.1584B: population diagrams after subtracting contaminants; vibrational Q corrections
- 2020ApJ...890..142P: iterative opacity-corrected rotation diagrams for H2CO in 15 disks
- 2018ApJ...864..170G: H2CO rotation diagram in HD 163296 with LTE justification
- 2025ApJS..276...49J: XCLASS + MAGIX, tau < 0.7 iteration, comparison with rotation diagrams
- 2020A&A...636A..67A: XCLASS with Tex bounds and errorestim_ins MCMC errors
- 2024A&A...682A..74F: MADCUBA AUTOFIT, single-line Tex range, isotopologue opacity check
- 2020MNRAS.492.1180R: MADCUBA with fixed Tex, Tex sensitivity, RADEX cross-check
- 2021A&A...656A..46M: ALCHEMI MADCUBA survey fit, detection criterion, source size test
- 2024A&A...689A..64B: multi-component rotation diagrams with 15% calibration error
- 2024A&A...686A..59N: rules for when Tex is fitted or fixed
- 2019A&A...623A..68T: MCWeeds priors and automated component search in absorption
- 2020A&A...644A..59K: CASSIS chi2 grids, LTE then non-LTE
- 2018A&A...620A..75K: TiO2 rotational diagram at 580 K around Mira
- 2025A&A...693A..76C: pixel-by-pixel LTE maps with line-count and error cuts
- 2019NatAs...3..314L: optically thick CH3OH replaced by 13CH3OH x 60
- 2018A&A...616A..90C: continuum as background, tau < 0.2 line selection
- 2020A&A...635A..48M: tau < 0.1 selection and asymmetric weighting
- 2025A&A...696A.100G: two-temperature C2H population diagram with beam-coupling correction
- 2017A&A...608A..38O: Tex from a CO line ratio, single-component limits
