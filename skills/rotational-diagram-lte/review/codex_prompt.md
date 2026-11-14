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

=== SKILL.md (rotational-diagram-lte) ===
---
name: alma-rotational-diagram-lte
description: "Derive rotational/excitation temperatures and LTE column densities from ALMA molecular lines: rotation (population) diagrams with opacity correction, full-spectrum LTE fitting in XCLASS, MADCUBA (SLIM/AUTOFIT), CASSIS or Weeds/MCWeeds, single-line LTE columns at an assumed Tex, and the abundance, isotopologue and deuteration ratios built on them. Use when a task asks for Trot or Tex, N_tot, a COM inventory, an LTE upper limit, or an LTE gas mass from line fluxes or spectra. Built from 375 ALMA papers (2012-2026)."
---

# Rotational diagrams and LTE column densities

Measures a single excitation (rotational) temperature and a total column density per species, assuming
level populations follow a Boltzmann distribution. The two mistakes that matter most: treating optically
thick or continuum-affected lines as thin (biases Trot and underestimates N), and quoting a column from one
line at an assumed Tex without showing how N moves over a plausible Tex range. Beam filling (source size) is
the third silent assumption; most papers set it to 1 and admit that makes N a lower limit.

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

- You need kinetic temperature and density, the gas is sub-thermally excited, or the colliders are electrons
  (debris disks, comae): use the **non-lte-excitation** skill (RADEX, LVG grids, LIME, RADMC-3D non-LTE).
  The pack shows why: in HH 212, RADEX columns were a factor 2 to 4 above the LTE optically thin ones
  (2015A&A...581A..85P); the LTE assumption was "found not to hold" in 2016ApJ...833...41Z; ALCHEMI
  residuals revealed non-LTE deviations (2021A&A...656A..46M); debris-disk CO masses used non-LTE with
  electron collisions (2016MNRAS.460.2933M, 2020MNRAS.497.2811K).
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
     Convert Jy/beam to K. If the continuum is bright, keep its level so it can act as the background
     temperature (2018A&A...616A..90C; Tbg = 21 K from dust in 2018A&A...619A..28L). Where dust is optically
     thick, correct line intensities for dust attenuation, as 2025ApJS..276...49J did by dividing by
     exp(-tau_dust) after fitting N_H2 and a filling factor eta to the continuum.
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
   - Method (general practice): for each line, N_u = 8 pi k nu^2 W / (h c^3 A_ul) with W the integrated
     intensity in K km/s (Rayleigh-Jeans, thin, beam-filling), then fit
     ln(N_u/g_u) = ln(N_tot/Q(Trot)) - E_u/(k Trot). Correct for opacity with C_tau = tau/(1 - exp(-tau))
     and for beam dilution with (theta_s^2 + theta_b^2)/theta_s^2 when a source size is adopted.
   - What papers do: iterate the opacity correction from a C_tau = 1 start until tau and Tex change by at
     most 0.001% (2020ApJ...890..142P); take the opacities from the LTE model and also subtract the modelled
     emission of contaminating species before fitting (2016A&A...587A..91B, 2014Sci...345.1584B); add the
     absolute flux uncertainty in quadrature (10% in 2020ApJ...890..142P, 15% in 2024A&A...689A..64B, 20% on
     ln(Eu/gu) in 2019ApJ...872..200H); fit one to three temperature components when the diagram curves
     (2024A&A...689A..64B; 22 and 59 K for C2H in 2025A&A...696A.100G). Require at least three lines
     (2020ApJ...890..142P, 2020ApJ...890...76N, 2025A&A...694A.166C).
   - Software: Python/NumPy/SciPy (2020ApJ...890..142P), Weeds output, or any linear fitter.
4. **Full-spectrum LTE fit.**
   - Goal: N, Tex, source size, FWHM and velocity per species, fitting blends jointly.
   - Method: one synthetic LTE spectrum per species, summed (Weeds, 5 parameters in 2014Sci...345.1584B;
     MADCUBA AUTOFIT with V, FWHM, Tex, N free and size fixed in 2024A&A...682A..74F). Fix FWHM from unblended
     lines, fit Tex only when at least 2 lines span a range of Eup, otherwise fix it (100 K, or 300 K for
     some species, in 2024A&A...686A..59N). Exclude lines the model says are thick: tau < 0.7
     (2025ApJS..276...49J), tau < 0.5 (2019A&A...622A.206M), tau < 0.2 (2018A&A...616A..90C), tau < 0.1
     (2020A&A...635A..48M). Penalise over-prediction (weight 3 when the model exceeds the data in
     2020A&A...635A..48M).
   - Optimisers seen: by eye (2016A&A...587A..91B, 2019A&A...628A..10B), Levenberg-Marquardt in MADCUBA
     (2020MNRAS.492.1180R, 2021A&A...656A..46M), genetic algorithm plus MCMC errors through MAGIX
     (2025ApJS..276...49J, 2019ApJ...885...82L), XCLASS errorestim_ins MCMC (2020A&A...636A..67A), MCWeeds
     with priors and Powell minimisation (2019A&A...623A..68T), emcee (2024A&A...689A..65R,
     2024A&A...687A.220I), regular chi2 grids (2019A&A...624A..82B, 2020A&A...644A..59K).
5. **Handle optically thick species.**
   - Goal: avoid the saturated main isotopologue.
   - Method: fit a rare isotopologue and scale: CH3OH from 13CH3OH times 60 (2019NatAs...3..314L); main
     species from 13C isotopologues with 12C/13C (2016A&A...587A..91B). Check opacity with isotopologue
     intensity ratios (28SiO/29SiO ~ 8 and ~ 20 in 2024A&A...682A..74F; a 12CO/13CO ratio of 2.0 gave
     tau_12CO ~ 56 in 2015ApJ...798...85P). For thick CO, Tex is set to the peak brightness
     temperature (2026A&A...705A.198M).
6. **One line only.**
   - Goal: a column or limit with an honest Tex range.
   - Method: take Tex from co-spatial species fitted with more lines (PN fitted over the 26-75 K range of
     other tracers in 2024A&A...682A..74F; minor species tied to CH3OH in 2019A&A...624A..82B or to SO2 in
     2019ApJ...885...82L), or from the dust temperature (2016ApJ...830L..37I). Report the spread: N changed by
     factors 2.5 (PN) and 2.1 (PO) over 5-50 K (2020MNRAS.492.1180R), by 40% for Tex +/- 20 K
     (2016ApJ...825...79S), by less than 20% over 20-50 K (2024ApJ...963...72O).
7. **Abundances, ratios, limits.**
   - Method: divide by N(H2) from dust (Tdust 100 K, kappa 1.0 cm2/g, gas-to-dust 100 in
     2020A&A...636A..67A) or from a CO isotopologue (with a factor 2 uncertainty in 2021A&A...656A..46M), or
     quote ratios to CH3OH or formamide (2021A&A...656A..46M, 2019A&A...628A..10B). Upper limits: 3 sigma
     integrated intensity at a stated Tex (100 K in 2018A&A...619A..28L).
8. **Maps of Trot and N (optional).**
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
| Detection threshold | 3 sigma | 3 to 5 sigma | 5 | 2024A&A...689A..64B, 2024ApJ...962...48J, 2021A&A...656A..46M |
| Opacity cut for fitted lines | tau < 0.2 to 0.7 | 0.1 to 0.7 | 5 | 2020A&A...635A..48M, 2018A&A...616A..90C, 2025ApJS..276...49J |
| Flux calibration error added | 10% | 10 to 20% | 5 | 2020ApJ...890..142P, 2024A&A...689A..64B, 2017ApJ...843..150F |
| Beam filling | 1 (source fills beam) | eta 0.384 fitted to 1 | 16 | 2024A&A...689A..64B, 2024A&A...686A..59N, 2025ApJS..276...49J |
| Fixed source size (hot cores, corinos) | 0.5" (9 papers) | 0.15" to 3" (5" to 10" in galaxies) | about 30 | 2018A&A...616A..90C, 2019A&A...628A..10B, 2019A&A...631A..64B, 2021A&A...656A..46M |
| Fixed Tex, hot core / corino | 100 to 150 K | 100 to 300 K | 9 | 2024A&A...686A..59N, 2018A&A...620L...6T, 2019A&A...623A..93C |
| Fixed Tex, cold gas / galaxies | 15 to 25 K | 5 to 50 K | 8 | 2021A&A...656A..46M, 2020MNRAS.492.1180R, 2020MNRAS.493L.108B |
| Free Tex bounds | 50 to 300 K | 10 to 500 K | 6 | 2020A&A...636A..67A, 2019A&A...624A..82B, 2018A&A...619A..28L |
| Background temperature | 2.73 K CMB | CMB to 132 K continuum | 6 | 2019A&A...623A..96Y, 2018A&A...616A..90C, 2018A&A...615A.141B |
| Ortho/para or A/E | 3 (o/p), 1 (A/E) | o/p 1 to 3 | 8 | 2024A&A...689A..65R, 2024ApJ...968L..19F, 2026A&A...707A.120H |
| 12C/13C for scaling | 60 to 70 | 50 to 70 | 7 | 2019NatAs...3..314L, 2019A&A...632A..19T, 2017MNRAS.466...49J |

Assumption tallies (my count of distinct bibcodes in the pack's Assumptions list, where 354 papers have at
least one line): 201 state LTE, 93 state optically thin emission, 16 state a beam filling factor of 1 or
emission filling the beam.

## Software

Counts are from the pack aggregate "Software named in the matched steps" (one paper can name several).

| Tool | Used for | Count | Examples |
|---|---|---|---|
| CASSIS | LTE and RADEX-coupled chi2 fits of line sets | 27 | 2020A&A...644A..59K |
| MADCUBA (+ MADCUBAIJ) | SLIM line ID, AUTOFIT LTE fits (Levenberg-Marquardt) | 23 (+3) | 2024A&A...682A..74F, 2020MNRAS.492.1180R, 2021A&A...656A..46M |
| Weeds (+ MCWeeds) | LTE synthetic spectra in GILDAS CLASS; MCWeeds adds priors and samplers | 21 (+4) | 2016A&A...587A..91B, 2019A&A...628A..10B, 2019A&A...623A..68T |
| XCLASS (+ MAGIX) | LTE full-band modelling; MAGIX genetic, Levenberg-Marquardt, errorestim_ins | 18 (+6) | 2020A&A...636A..67A, 2025ApJS..276...49J, 2019ApJ...885...82L |
| CDMS / JPL | spectroscopic catalogues (frequencies, Aij, Eu, gu, Q) | 10 / 4 | 2025ApJS..276...49J, 2019A&A...631A..64B |
| emcee | posterior sampling of N and Tex | 26 | 2024A&A...689A..65R, 2024A&A...687A.220I |
| SciPy, lmfit, mpfit | rotation-diagram and custom fits | 3, 3, 2 | 2020ApJ...890..142P |
| CASA | imaging and spectrum extraction | 23 | 2020A&A...636A..67A |
| RADEX, LIME, RADMC-3D | non-LTE or full radiative transfer run alongside LTE | 48, 22, 17 (+3) | see non-lte-excitation |

RADEX is the single most named tool in these steps because many papers run an LTE fit and a non-LTE check
side by side (2015A&A...581A..85P, 2020MNRAS.492.1180R, 2024A&A...689A..64B). Version numbers of the LTE
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

=== references/parameters.md ===
# LTE and rotation-diagram parameters (from the `rotational-diagram-lte` pack)

Every value is copied from the pack's key-parameter, assumption, limitation or excerpt lines. Papers in the
pack that are off-topic for LTE line excitation (solar free-free, pure disk kinematics, dust-only work) are
left out. Non-LTE grids (RADEX, LVG) belong to the non-lte-excitation skill and appear here only as
cross-checks.

## 1. Full-spectrum LTE fits: fixed and free parameters

| Paper | Code | Free | Fixed / bounds |
|---|---|---|---|
| 2016A&A...587A..91B | Weeds | size, N, T, v offset, FWHM (by eye) | deuterated species share main-isotopologue parameters |
| 2019A&A...628A..10B | Weeds | by eye | size 2" for all species; urea Trot 160 K, FWHM 5.0 km/s |
| 2014Sci...345.1584B | Weeds | 5 parameters per species | size 1.0", Trot 153 K, linewidth 5 km/s |
| 2020A&A...636A..67A | XCLASS | Tex, N, FWHM, vLSR | Tex 50-300 K (HNCO, NH2CHO), 70-400 K (H2CO); vLSR within +/-0.5 km/s |
| 2025ApJS..276...49J | XCLASS + MAGIX | N only | v_width 3 km/s, Trot 120 K, eta 0.384; lines with tau < 0.7 and width < 4 km/s |
| 2019ApJ...885...82L | XCLASS / MAGIX | per species | genetic, Levenberg-Marquardt, errorestim-ins; other species' Trot tied to SO2 |
| 2024A&A...682A..74F | MADCUBA AUTOFIT | V, FWHM, Tex, N | emission fills beam; 34SO Tex fixed at 58 K in one region |
| 2020MNRAS.492.1180R | MADCUBA AUTOFIT | N, v, FWHM | Tex 5 K (PN, PO), 34 K (SO) |
| 2021A&A...656A..46M | MADCUBA | N, Tex when constrained | size 5" (10" for 12CO), vLSR 230 km/s, FWHM 150 km/s, Tex 15 K when unconstrained |
| 2024A&A...686A..59N | LTE fit | N, Tex only with >= 2 lines spanning Eup | FWHM ~1.8 +/- 0.5 km/s from unblended lines; Tex 100 K (300 K for t-HCOOH, NH2CHO); Vlsr 2.7 km/s |
| 2018A&A...616A..90C | LTE grid | Tex 90-300 K, N 1e13-1e17 cm-2 | FWHM 1.8-2.4 (A), 0.8-1.2 (B) km/s; size 0.5"; tau < 0.2 |
| 2018A&A...619A..28L | LTE | N, Tex | CH2NH N 1e14-5e15, Tex 25-300 K; NO, N2O N 1e15-1e17, Tex 25-400 K; FWHM 1 km/s; Tbg 21 K |
| 2019A&A...624A..82B | LTE grid | Tex, N | Tex 10-500 K in 10 K steps; N in 20 log steps; channels within +/-2 FWHM; size = synthesised beam |
| 2020A&A...635A..48M | LTE | Trot, N | filling factor 0.5; FWHM 2.2-2.4 km/s; tau < 0.1; weight 3 where model exceeds data |
| 2017A&A...597A..53L | LTE | N | FWHM 1.0 km/s, size 0.5", tau <= 0.1, common Tex 125 K |
| 2015ApJ...813L..19J | LTE | Tex, vLSR, FWHM, N | initial Tex 50-350 K, FWHM 0.5-10 km/s, N 1e14-1e17 cm-2, size 0.53" |
| 2020ApJ...898...54T | LTE | FWHM 1-10 km/s | size 0.3" (Core A), 0.5" (B, C); filling factor 1 |
| 2019A&A...623A..68T | MCWeeds (absorption) | N, FWHM, v0 per component | dips > 4 sigma; velocity prior uniform +/-3 km/s; FWHM max 30 km/s; log N normal width 2 |
| 2024A&A...689A..65R | emcee | Tex, Nt | uniform Tex 0-50 K, Nt 1e11-1e14 cm-2 (disk-averaged); Tex 0-100 K, Nt 1e11-1e16 (radial) |
| 2024A&A...687A.220I | emcee | joint fit | beam and source size 0.5", FWHM 1 km/s, vLSR 2.7 km/s; 300 walkers, 1500 steps |
| 2016A&A...595L...4L | MCMC | | 100000 iterations, burn-in 20000, thinning 50; size 0.2" |
| 2019A&A...622A.206M | LTE | Ncol, Tex, VLSR, FWHM | transitions with tau < 0.5 |

## 2. Rotation (population) diagrams

| Paper | Species / source | Settings | Result quoted |
|---|---|---|---|
| 2020ApJ...890..142P | H2CO, 15 disks | iterative C_tau, converge at 0.001% (5000 iterations max); 10% flux error in quadrature; >= 3 lines | Tex 11 +/- 0.39 K (DM Tau) to 37 +/- 3.6 K (J1604-2130) |
| 2018ApJ...864..170G | o-H2CO, HD 163296 | 3 ortho lines; flux error from 500 signal-free apertures | 24 +/- 14 K |
| 2016A&A...587A..91B | COMs, Sgr B2(N2) | opacity from Weeds, contamination removed | CH2DCN 136 (14) K; C2H5CN 137.3 (1.6) K |
| 2019A&A...628A..10B | urea, formamide, Sgr B2(N1S) | opacity and contamination corrected | urea 350 +/- 190 K (unreliable); formamide 159 +/- 5 K |
| 2014Sci...345.1584B | i-, n-PrCN, Sgr B2(N2) | contaminants subtracted, thin verified | n-PrCN 153 +/- 12 K; i-PrCN 154 +/- 99 K |
| 2018A&A...620A..75K | TiO2, Mira | unblended lines | 580 +/- 65 K, N 2.7e16 cm-2 |
| 2019ApJ...870L..26C | CH3OH, comet ISON | 3 lines | 139 +/- 29 K |
| 2024A&A...689A..64B | OCS, SO2, NGC 253 | 1-3 components, reduced chi2, 15% calibration error, no beam correction | OCS 10-65 K and 124-312 K; SO2 55-79 K and 115-298 K |
| 2025A&A...696A.100G | C2H, Orion Bar | beam coupling from IRAM 30m and ALMA maps | 22 +/- 2 K and 59 +/- 7 K |
| 2019ApJ...872..200H | | 20% error on ln(Eu/gu); 80% confidence intervals | |
| 2025A&A...693A..76C | CH3CN K ladder, per pixel | K = 2,3,4,5,7,8 and v8=1; >= 3 lines per pixel; show relative errors < 60% | |
| 2020ApJ...890...76N | K ladders | cores with >= 3 K lines above 3 sigma; Q(T) from Araya 2005 | |
| 2017ApJ...834....6S | | Trot 7.4 K adopted where 2_K-1_K not detected; A and E same N | |
| 2019ApJ...872..196S | | Trot 200 K where no diagram fit; Aij >= 1e-5 | |

## 3. Tex assumed for single lines and limits

| Paper | Tex | Sensitivity reported |
|---|---|---|
| 2020MNRAS.492.1180R | 5 K (PN, PO), 34 K (SO) | N changes by 2.5 (PN), 2.1 (PO) over 5-50 K |
| 2024A&A...682A..74F | PN over the 26-75 K (region 1) and 12-30 K (region 2) range of other tracers | |
| 2016ApJ...825...79S | | +/- 20 K changes N by 40% |
| 2024ApJ...963...72O | 40 K | N within 20% for 20-50 K |
| 2020MNRAS.496..394R | 20 K | higher or variable Tex changes results by < ~2 |
| 2020MNRAS.493L.108B | 25 K at 90-110 au | 20-80 K gives N within errors |
| 2015ApJ...798..124R | 50 K (CO mass limit) | |
| 2018A&A...619A..28L | 100 K for quoted 3 sigma limits | |
| 2016ApJ...830L..37I | 100 K, close to the 111 K dust temperature | |
| 2021A&A...656A..46M | 15 K when unconstrained; 300 K for vibrational display | |
| 2019A&A...624A.125M | 15 K | |
| 2017ApJ...848..101V | 15 K from CO(3-2)/(1-0) | |
| 2018A&A...620A.119D | lower limit = CMB at z (10.1 K), 20 and 30 K tried | |
| 2015A&A...582L...4M | Tex = CMB at z = 0.89 (5.14 K) | |

## 4. Optical depth handling

| Paper | Approach |
|---|---|
| 2016A&A...587A..91B | Goldsmith-Langer correction with Weeds opacities |
| 2020ApJ...890..142P | iterative C_tau from a thin start |
| 2019NatAs...3..314L | CH3OH = 13CH3OH x 60 |
| 2024A&A...682A..74F | 28SiO/29SiO ~ 8 and ~ 20, 32SO/34SO ratios vs MADCUBA tau |
| 2015ApJ...798...85P | 13CO/12CO line ratio R = 2.0 +/- 0.2 gives tau_12CO ~ 56, tau_13CO ~ 0.7; 12CO/13CO = 76 |
| 2026A&A...705A.198M | Tex = peak Tb of 12CO; tau_12CO = 77 from ISM 12C/13C |
| 2020ApJ...898...97B | tau_blend(C2H) = 1.1 +/- 0.2, tau(HCN) = 5.8 +/- 1.8 |
| 2015ApJ...803...97S | thin after excluding thick lines; tau ~ 2 at S mu^2 ~ 35 at 150 K |
| 2018A&A...615L..10M | optical depth ratio 77 with same Tex |

## 5. Partition function and spectroscopy

| Paper | Item |
|---|---|
| 2014Sci...345.1584B | vibrational Q factors at 150 K: 1.64 (i-PrCN), 2.09 (g-n-PrCN), 2.36 (a-n-PrCN) |
| 2019ApJ...880..130M | CH3OCHO corrected by a factor 2.1 for torsional states |
| 2016A&A...587A..92M | Q corrections for conformers and vibrational states |
| 2016A&A...587A..91B | statistical 2:1 split for out-of-plane / in-plane conformers |
| 2019A&A...632A..19T | two CH3OD partition functions; CH3OD Trot fixed to CH2DOH |
| 2020MNRAS.497.5454I | Qrot = 1.23 Trot^1.5 |
| 2024AJ....167...66Y | Aul >= 1e-8 s-1, Eu <= 1000 K; CH2DOH spectroscopy uncertain by ~3 |
| 2019A&A...624A..70C | Aij >= 1e-3 s-1, Eup <= 500 K |
| 2025A&A...693A.101T | Eup <= 300 K, A >= 1e-6 s-1, < 1000 GHz |

## 6. Spin and isotopic ratios adopted

| Paper | Ratio |
|---|---|
| 2024A&A...689A..65R | o/p 3:1 |
| 2019ApJ...876...72L | H2CS o/p 3 |
| 2024ApJ...968L..19F | o/p 1 |
| 2021A&A...645A.145G | H2CO o/p 1.8-2.8; H2CS 3.0; CH3OH A/E = 1 |
| 2026A&A...707A.120H | E/A = 1 (CH3OH, CH3CHO); OPR 3 (H2CO, CH2CO) |
| 2024ApJ...969..143I | para-H2CO only, no OPR needed |
| 2019NatAs...3..314L, 2015ApJ...813L..19J, 2020MNRAS.498L..87B | 12C/13C = 60 |
| 2019A&A...632A..19T, 2024A&A...686A.201N | 12C/13C = 70 |
| 2017MNRAS.466...49J, 2014A&A...569A..11S | 12C/13C = 50 |
| 2021A&A...656A..46M | measured 12C/13C = 22 +/- 2 in NGC 253 |

## 7. LTE justification by density

| Paper | Density quoted |
|---|---|
| 2018ApJ...864..170G | > 1e6 cm-3, emission thermalized |
| 2017ApJ...839...43O | > 1e6 cm-3 |
| 2018A&A...614A.123P | n_crit ~ 1e6 cm-3 vs 4e7-5e8 cm-3 |
| 2018MNRAS.478.2505I | n_crit ~ 1e7 cm-3 |
| 2020A&A...635A.189F | n(H2) > 1e7 cm-3 |
| 2025A&A...693A..76C | > 1e7 cm-3 |
| 2024IJAsB..23...14M | 7e7 cm-3 |
| 2020A&A...644A..84M, 2024ESC.....8..665M | ~ 1e8 cm-3 |
| 2019ApJ...871..112X | > 1e9 cm-3 |
| 2018A&A...620A.170J | >~ 1e10 cm-3 |
| 2016ApJ...833...41Z | LTE assumed and found not to hold |

## 8. Abundance normalisation

| Paper | N(H2) route |
|---|---|
| 2020A&A...636A..67A | dust continuum, Tdust 100 K, kappa 1.0 cm2/g, gas-to-dust 100 |
| 2025ApJS..276...49J | continuum fit, N_H2 = 1.24e25 cm-2 (2%), kappa 2.2 cm2/g at 230 GHz, beta 1 |
| 2021A&A...656A..46M | C18O with 18O/16O = 100 and CO/H2 ~ 8e-5, factor 2 uncertainty |
| 2018A&A...615A.141B | dust temperature = CH3OCHO Tex; N_H2 a lower limit for thick dust |
| 2024IJAsB..23...14M | N(H2) = 1.30e23 cm-2 |
| 2015A&A...581A..85P | X_SO = X_CO N_SO / N_CO with X_CO = 1e-4 |

=== EVIDENCE PACK (rotational-diagram-lte) ===
# Evidence pack: Rotational diagrams and LTE column densities (`rotational-diagram-lte`)

Scope: LTE column densities, excitation temperatures, optical depth corrections

Built from 375 non-held-out ALMA papers whose methods cards passed mechanical evidence verification (every quote below is verbatim from the paper). Years 2012-2026.
Matcher (regex over analysis steps): `rotation(?:al)? diagram|population diagram|\blte\b|xclass|madcuba|cassis|weeds|excitation temperature|boltzmann (?:plot|diagram)|lte (?:column|model|fit|analysis|assumption)`
Tagging is by regex, so a few papers may be off-topic: ignore those.

## Aggregates over all papers

### Science fields
- astrochemistry: 211
- star_formation: 199
- protoplanetary_disks: 95
- nearby_galaxies: 57
- milky_way_ism: 45
- debris_disks: 26
- agn_and_quasars: 25
- evolved_stars: 24
- stellar_physics: 12
- solar_system: 7
- exoplanets: 7
- high_z_galaxies: 6
- sun: 5
- galaxy_clusters_and_sz: 4
- transients: 1

### Software named in the matched steps
- radex: 48
- cassis: 27
- emcee: 26
- madcuba: 23
- casa: 23
- lime: 22
- weeds: 21
- xclass: 18
- radmc-3d: 17
- cdms: 10
- vis_sample: 8
- magix: 6
- madex: 6
- mcfost: 6
- miriad: 5
- jpl: 4
- mcweeds: 4
- class: 4
- scipy: 3
- spectralradex: 3
- lmfit: 3
- shape: 3
- radmc3d: 3
- gildas: 3
- casa simobserve: 3
- madcubaij: 3
- python: 2
- gildas class: 2
- gofish: 2
- torus: 2
- pythonradex: 2
- mpfit: 2
- ali code: 2
- hitran: 2
- shapemol: 2
- radmc3dpy: 2
- ratran: 2
- gildas/class: 2
- bettermoments: 2
- radmc: 2

### Fitting methods (most common phrasings)
- Linear fit; formal errors viewed with caution: 1
- Manual by-eye: 1
- emcee MCMC; likelihood from weighted real and imaginary visibility differences: 1
- LTE AUTOFIT; some Tex fixed (34SO region 1 at 58 K): 1
- LTE: 1
- Visual optimization, no sampler: 1
- linear fit: 1
- Graphical comparison of tracks of line ratios in Tkin-n plane; no formal fit: 1
- XCLASS errorestim_ins MCMC for errors: 1
- Power-law fits with R^2: 1
- Genetic algorithm for best fit; MCMC for uncertainties: 1
- Initial by-eye search then grids minimizing chi2; 54 DF; reduced chi2 ~4.0: 1
- MCMC, likelihood ∝ exp(-chi2/2) accounting for independent beams and channel correlation: 1
- Linear fit of ln(Nu/gu) vs Eu; includes 10% flux uncertainty: 1
- Powell local minimisation, MCWeeds priors: uniform velocity, truncated normal FWHM, normal log N width 2: 1
- Reduced chi2 grid in M_star and inclination; cavity radius by visual inspection: 1
- Gaussian hyperfine components fit with MCMC: 1
- emcee affine-invariant MCMC, walkers = 4x free parameters, 2000 burn-in + 3000 steps, 16/50/84 percentiles, chi2 likeli…: 1
- Same MCMC strategy as CH3CN: 1
- MADCUBA least-squares fit; only statistical uncertainties reported: 1
- Levenberg-Marquardt least squares; errors from covariance matrix: 1
- reduced chi-square minimisation: 1
- best chi-square over grid; uncertainty ranges from chi-square: 1
- linear fit to population diagram: 1
- free: R0, DeltaR, Sigma0, T0, v*, i, PA, offsets: 1
- Rotational diagram fit: 1
- Simultaneous fit of all detected CH3OH transitions for Tkin: 1
- chi2 grid; 95% confidence region chi2<7.81 (3 dof): 1
- chi2 minimization: 1
- chi2 minimum on regular grid: 1
- Levenberg-Marquardt least squares; uncertainties from covariance diagonal; Lp from delta chi2 curve (1 and 2.6 sigma at…: 1
- Least squares on logarithmic form; residual RMS ~60 K: 1
- Gaussian fit to stacked spectrum for centroid/width: 1
- two-component rotational diagram: 1
- Best fit found by manual variation of parameters: 1
- Levenberg-Marquardt: 1
- Weighted parabola fit, weights inverse square of uncertainties: 1
- Power-law fit to mass spectra m(v) ∝ v^-gamma: 1
- emcee; uniform priors Tex 10-150 K, log N 9-14, tau<1: 1
- emcee; uniform priors T 10-150 K, log n 4-10, log N 9-14, log M -5 to 0 (also linear M 0-1): 1

### Validation checks used
- Population diagram used to verify manually derived temperature: 1
- Detected if frequency, peak intensity and width are reproduced and line not contaminated: 1
- Compared with astrochemical models T14, A12 and Orion KL: 1
- Compared with 24 K from Carney et al. 2017: 1
- Channel maps of data, model and residuals; third-component test: 1
- Compared with SiO J=5-4 high resolution maps: 1
- Hyperfine-included fit gives consistent FWHM: 1
- Nine clearly detected lines; checked Halpha contamination: 1
- considered unreliable for urea: 1
- Compared flux integral with earlier papers' 10.0 and 12.3 Jy km/s: 1
- Varied 12CO/13CO between 50 and 200 and HCO+ abundance; similar results: 1
- Blending checked with ethanol comparison line at 217803.69 MHz: 1
- Compared with Lopez-Sepulcre et al. 2015 relation: 1
- RADEX with n=3e5 gives factor 2-4 higher columns: 1
- Compared with disk mass 0.014 Msun from HCO+: 1
- Visual inspection of selected species: 1
- Rotation diagram comparison: scatter 0.28 dex, offset 0.03 dex: 1
- Compared to 13CO J=3-2 line with 12C/13C=10±3: 1
- Compared with Kaminski et al. 2016, 2017: 1
- Model spectrum compared with half-disc spectra: 1
- Energy ranges similar across disks; critical densities below disk densities supporting LTE: 1
- residual peaks above 5 sigma then 4 sigma searched for missing components: 1
- Cross-check with archival C18O J=3-2: 1
- Visual comparison of best model with 13CO and C18O maps; SED consistency check with MCFOST: 1
- Compared with Habart2005 density model and 13CO conversion factors: 1
- Compared with earlier CH3CN temperatures: 1
- Compared with WHISPER-based column densities at PDR and core: 1
- Residuals inspected against full-spectrum model; non-LTE deviations identified; extra criteria for new detections: 1
- Compared with literature ratios in Table 8: 1
- Consistent with Rico-Villas 2020 ~3%: 1
- Compared with GC GMCs and hot cores: 1
- Tex sensitivity: column densities vary by factor 2.5 (PN), 2.1 (PO) over 5-50 K: 1
- Compared with LTE ratios: 1
- Uniform-sphere geometry gave similar results (not shown): 1
- Only transitions not severely blended with other species are used: 1
- Optical thinness verified a posteriori: 1
- HD 121191 compared to Moor et al. 2017: 1
- Collision rates varied by factor 2 changed line intensities by a few percent; alternative Tkin=100 K model run: 1
- Compared observed and reintegrated flux densities in 8 R and 8 angle bins: 1
- Compared with Men'shchikov et al. 2002 dust temperature and CO density: 1

### Key parameters and settings (bibcode: value)
- 2018ApJ...864..170G: Flux error: std of 500 simulated flux measurements at random signal-free positions
- 2018ApJ...864..170G: Fixed R1=1 au, R2=80 au, Rout=600 au, (z/r)_u=0.5; (z/r)_l=0.15, 0.20, 0.25
- 2019A&A...628A..10B: source size 2''; Trot 160 K; Delta V 5.0 km/s
- 2017A&A...608A..38O: R = 0.5 kpc, v = 300 km/s
- 2017A&A...608A..38O: Tkin 10-200 K (log steps 0.043); nH2 1e2-1e7 cm-3 (log steps 0.167); N(12CO) 5e15-1e20 cm-2 (log step 0.5); line width 100 km/s; Tbg 2.73 K
- 2020A&A...636A..67A: Tex 50-300 K for HNCO and NH2CHO, 70-400 K for H2CO; FWHM and vLSR constrained by Gaussian fits, vLSR free within ±0.5 km/s
- 2015A&A...581A..85P: TK = Tex = 50-500 K; nH2 1e5-1e7 cm-3
- 2015A&A...581A..85P: beam dilution factor ~8; R_disk ~90 AU
- 2025ApJS..276...49J: SG2 and SG3 spectra scaled up by 5% and 2%
- 2025ApJS..276...49J: v_width = 3 km/s, T_rot = 120 K, eta = 0.384, N free
- 2025ApJS..276...49J: tau criterion 0.7; exclude line width >4 km/s
- 2018A&A...620A..75K: R338=2.15 au, T*=2100 K, Rout=8.6 au
- 2016MNRAS.460.2933M: ne0 between 1e-2 and 1e7 cm-3; Tk half to twice dust temperature (50 K)
- 2020ApJ...890..142P: convergence when tau and Tex change at most 0.001% (5000 iterations max for LkCa 15)
- 2019A&A...623A..68T: detect dips >4 sigma; four velocity ranges; velocity prior uniform ±3 km/s; FWHM max 30 km/s
- 2019A&A...623A..68T: Tkin 10–130 K, nH2 10–1e7 cm-3; Mopra Tmb = 1.7 × TA*
- 2015ApJ...798...85P: T=43 K, d=140 pc, mu=1.36
- 2015ApJ...798...85P: h=0.1 r, gamma=1, R_c=200 au, T=50 K (r/50au)^-0.3, b=50 m/s, inner truncation 0.3 au
- 2026A&A...707A.120H: Tex(C17O)=15 K; l_depth=0.1 pc
- 2026A&A...707A.120H: E/A = 1; Tbg=2.73 K; dv=0.6 km/s; K=2 used as upper limit for dx>=30 arcsec
- 2026A&A...707A.120H: E/A=1 for CH3OH, CH3CHO; OPR=3 for H2CO, CH2CO
- 2021A&A...656A..46M: Source size 5'' (10'' for 12C16O); fixed v_LSR=230 km/s, FWHM=150 km/s, Tex=15 K when unconstrained
- 2021A&A...656A..46M: Detection criterion: all unblended transitions above 5 sigma in model detected and fit converged
- 2021A&A...656A..46M: CO isotopologues recalculated for 10'' source size
- 2021A&A...656A..46M: line width 150 km/s; LTE Tex=300 K for display
- 2020MNRAS.492.1180R: Velocity ranges [-6.5,-4.5], [-4.5,-2.0], [-2.0,0] km/s
- 2020MNRAS.492.1180R: Tex fixed: 5 K for PN/PO, 34 K for SO; free N, v, FWHM
- 2020MNRAS.492.1180R: Tkin = 20 K, background 2.73 K
- 2024A&A...689A..64B: 3 sigma detection threshold; lines >15% contaminated rejected
- 2024A&A...689A..64B: Spectra from circular region of one beam (1.6") at coordinates in Table 1
- 2024A&A...689A..64B: N 5e12-1e18 cm-2; n 1e3-1e8 cm-3; T limited to collisional-rate range; source size 0.1"-150"
- 2014Sci...345.1584B: Vibrational partition function factors at 150 K: 1.64 (i-PrCN), 2.09 (g-n-PrCN), 2.36 (a-n-PrCN)
- 2020MNRAS.497.2811K: 100 walkers, ~10,000 steps; 2.667 channels per resolution element
- 2019ApJ...870L..26C: 5,000 cells Delaunay grid; expansion velocity 1.1 km/s; Tkin 145 K
- 2015ApJ...803...60S: Case 1: Tkin 5-300 K step 5, n 10^2-10^5; case 2: Tkin 5-400 K, n 10^3-10^7
- 2015RAA....15.2213A: uncertainties: absolute 0.16 (3-2) and 2.2 (6-5) Jy arcsec^-2 plus 20% relative; ten iterations
- 2017ApJ...848..101V: Tex=15 K, filling factor 0.1, 13W32=22.8 K km/s, A_reg=11.2 kpc^2
- 2020A&A...644A..59K: beam filling factor 1.0 for almost all models
- 2020ApJ...900..131L: T_ex = T_kin = 228 K
- 2025ApJ...986L..22R: Lp=0 assumed for geometry; free Q1,Q2,v1,v2,gamma,phi,psi
- 2017A&A...605A..78A: ALMA data used up to theta~70 deg
- 2015ApJ...798..124R: Tex = 50 K, FWHM 1.9 km/s, inclination ~20 deg
- 2025A&A...696A.100G: T_k = 600 K upper limit; sigma_turb = 1 km/s
- 2024A&A...689A.317G: Power-law density and temperature; constant velocity
- 2024ApJ...962....1S: Tex=50 K, Q≈19, [OH]/[H2]=5e-7, f=0.3, r_out=2 kpc, v_out=669 km/s
- 2018A&A...620A.119D: delta v = 13 km/s; integral limit 3.9 km/s
- 2021ApJ...908..163M: Delta v = 300 km/s; Q10=0.5; A10=7.93e-8 s^-1; Helium factor 1.36
- 2016ApJ...832..158Z: X12,13=62, X13,18=8.7
- 2016ApJ...832..158Z: Tex = 15 K and 50 K; inclination 40 deg for momentum/energy
- 2018ApJ...864..133T: 256 walkers, 200 burn-in, 100 sampling steps; 10% flux systematic
- 2018ApJ...864..133T: 13 free params per radius; 256 walkers, 1500 burn-in, 250 sampling steps
- 2025A&A...699A.382M: v_exp = largest velocity offset 1.68±0.14 km/s, inclination-corrected to 2.2±0.4 km/s
- 2018ApJ...853L..19S: Z_LMC = 0.4 Zsun, scaling factor 2.5
- 2017A&A...602A..42K: Central source 5 pc, water layer 1.5 pc from outer radius
- 2020ApJ...898...54T: source size 0.3" Core A, 0.5" Cores B and C; filling factor 1; FWHM free between 1 and 10 km/s
- 2014ApJ...787..112C: Source sizes 10'' hot core/compact ridge, 30'' plateau, 180'' extended ridge
- 2025A&A...693A.101T: line width 0.2 km/s; pixels within 1.5" radius
- 2025A&A...693A.101T: T_kin 10-200 K step 10; log n 5-12 step 0.1; N=1e12 cm-2; E_up<=300 K, A>=1e-6; <1000 GHz
- 2018A&A...615A..28D: Apertures 80/320/800 mas (IK Tau), 75/300/1000 mas (R Dor)
- 2017ApJ...839...86H: free: M*, Mdisk, Rc, Rin,gas, gamma, T100, i, h0
- 2020ApJ...898...97B: tau_blend(C2H)=1.1±0.2; tau(HCN)=5.8±1.8
- 2019MNRAS.485.2457H: T_kin 60 K, line width 4.4 km/s, sphere radius 2.35 pc, abundance 1e-9, density 1e4 cm^-3
- 2013ApJ...774...16R: Mgas=0.09 Msun, gamma=0.8, rc=150 AU, Tfrz=19 K, sigma_s=9e20 cm^-2, Tm=19K (r/155AU)^-0.3
- 2013ApJ...774...16R: xi=0.01 km/s, i=224 deg, PA=312 deg
- 2024IJAsB..23...14M: V_LSR = 68.50 km/s
- 2020ApJ...898...75I: Tkin 50,100,200,300,500 K; nH2 1e3,1e4,1e5 cm-3; [C0]/[CO] 1,3,10; N_CO/dV 3e16,1e17,3e17
- 2020A&A...644A..84M: Eu < 250 K for the main fit; 25 MF, 12 GA, 14 AA lines
- 2020A&A...644A..84M: beam filling factor 1; single temperature component
- 2025A&A...696A..31G: Priors: TK 50–500 K, nH2 10^2–10^7 cm-3, N 10^13–10^17 cm-2; 20 walkers, 4500 steps after burn-in
- 2015A&A...582L...1T: source size 3", vLSR +7.5 km/s, dv 2.0 km/s, TK 100±20 K
- 2020ApJ...892...99C: Free: i, M*, v*, r0, sigma_r, M_C0, T100, dx, dz; PA fixed 48.5 deg
- 2020ApJ...892...99C: 200 walkers, 1500 steps, first 200 discarded
- 2017Icar..286..289L: Surface pressure 12 μbar nominal (10, 14 tested); CO uniformly mixed; correlation length = scale height; convergence when fit rms constant within 1%
- 2015ApJ...801...63M: Abundances reported for Tex 10–75 K
- 2013A&A...557L..11B: Outflow temperature constant at 200 K
- 2019MNRAS.485..229R: Spectra from larger circle matching CO(1-0) beam; single Gaussian fit per line
- 2020A&A...633A..13D: A_s=1.8e8 cm-3, B=1e7 cm-3, spiral velocity 8+5r/R1, bipolar outflow 60 km/s, opening angle ~40 deg, n=2
- 2020A&A...633A..13D: domain radius 2700 AU, 100000 grid points, levels up to J=41
- 2020ApJ...898...61I: n_H2 = 1e5 cm^-3; N_CO/dV = 2.5e16 cm^-2 (km/s)^-1; background 2.73 K
- 2021A&A...656A..68E: Ten equidistant frequencies per receiver band, averaged
- 2025NatAs...9.1476C: 4 T(r) segments for Apr 18–25; 3 for May 4
- 2015MNRAS.447.3936M: T_k 10 to 150 K
- 2018A&A...615A.141B: line width and source size fixed (source larger than beam); dust continuum temperature = azimuthally averaged brightness temperature
- 2018A&A...615A.141B: background T_B=132 K; line width and velocity offset fixed; source fills beam
- 2019NatAs...3..314L: FWHM fixed at 2 km/s, Tex = 120 K, emission size 0.6"
- 2019NatAs...3..314L: X_mol = 4e-9 above 80 K; FWHM 2 km/s
- 2025A&A...693A..76C: only values with relative errors <60% displayed
- 2025A&A...693A..76C: lines K=2,3,4,5,7,8 and v8=1 K,l=2,1; at least three lines detected per pixel
- 2018A&A...619A..28L: CH2NH: N=1e14-5e15 cm-2, Tex=25-300 K; NO and N2O: N=1e15-1e17, Tex=25-400 K; Vpeak 2.5-2.9 km/s; FWHM=1 km/s
- 2018A&A...619A..28L: Tex=100 K for quoted limits; 3 sigma 23 mJy km/s (CH3NH2), 27/21/27 (NH2OH)
- 2019A&A...624A.125M: Tex = 15 K; source size 3''
- 2020MNRAS.497.5454I: Low-resolution cubes; regions MM1+MM3+MM4, MM2, MM5+MM6
- 2015ApJ...813L..19J: Td=190 K, gas-to-dust 154, kappa(1.21 mm)=0.24 cm2/g
- 2015ApJ...813L..19J: Initial ranges Tex=50-350 K, vLSR=-57 to -47 km/s, FWHM=0.5-10 km/s, N=1e14-1e17 cm-2; source size 0.53''
- 2024AJ....167...66Y: Aul >= 1e-8 s-1, Eu <= 1000 K
- 2024AJ....167...66Y: 24 free parameters; 100 walkers, 15000 steps, 12000 burn-in
- 2017A&A...598A..53D: FWHM grid 0.5-25 km/s in 0.5 km/s steps
- 2017A&A...598A..53D: Emitting region 75 mas diameter (~20 AU radius); outflow velocity 5 km/s; Mdot 1e-5 Msun/yr
- 2016ApJ...829....6W: T = 33 K; A32 = 2.497e-6 Hz; Be = 57.635; distance 116 pc
- 2020A&A...644A.119P: Tex = TK = 20-100 K
- 2017ApJ...842...94T: N(He+)/N(H+)=0.09; a=0.822-0.942
- 2013A&A...555A..73K: ambient density 1.9e3 cm^-3; N=1e15 cm^-2; T>900 K; adopted 960 K
- 2024A&A...686A..59N: FWHM fitted on unblended lines then fixed (~1.8±0.5 km/s); Tex fitted only if >=2 lines with range of Eup, else fixed to 100 K (300 K for t-HCOOH, NH2CHO)
- 2024A&A...686A..59N: Vlsr = 2.7 km/s
- 2020A&A...643A..89P: Tkin 3–400 K, nH2 1e2–1e5 cm-3, NCO/Δv 1e15–1e20, 40 log steps each
- 2020MNRAS.498L..87B: N 3e16–4e19 cm-2, nH2 3e6–2e8 cm-3, Tkin 80–180 K
- 2024A&A...689A.263D: pixel grid 0.13'', apertures minimum width 0.8''
- 2015ApJ...803...97S: Blended lines also removed
- 2020ApJ...898..146M: kinetic temperatures 10-250 K, full range of electron densities
- 2019AJ....157..251T: Dry adiabat, T=71.5 K at 1 bar, trace gases 30x protosolar (NH3 1x), intermediate H2
- 2015MNRAS.453.4324M: wind 8 to 11 km/s, turbulent 2 km/s
- 2021A&A...655A..80D: Distance 395 pc, Mdot 3e-6 Msun/yr, v_inf 16.5 km/s
- 2016ApJ...830L..37I: Tex = 100 K
- 2016ApJ...830L..37I: kappa(1.2 mm)=0.0068 cm2/g; mean molecular weight 2.33
- 2017AJ....153..233F: T_ex = 17 K
- 2017AJ....153..233F: Fixed: Rc 600 au, T_mid,150 17.5 K, z_q,150 70 au, gamma 1, v_turb 1% sound speed, d 414 pc
- 2024ApJ...966..117X: microturbulence 1 km/s; 12CO/H = 1e-4; 13CO and C18O ratios 62 and 500
- 2024ApJ...966..117X: mu=1.4, Tbg=2.7 K, 1 sigma threshold for synthetic ALMA
- 2019A&A...624A..82B: Tex 10–500 K in 10 K steps; N sampled by 20 log steps; channels within ±2×FWHM
- 2018ApJ...856...97S: 5-500 K, 1e2-1e7 cm-3, dV=50 km/s, Tbg=2.73 K
- 2020A&A...635A..48M: FWHM 2.2-2.4 km/s, vlsr 0.8 km/s for A
- 2020A&A...635A..48M: Weight 3 when model exceeds data
- 2020A&A...635A..48M: Optically thin lines only (tau<0.1); unblended criteria
- 2014ApJ...786..114L: 7 free parameters: T0, n0, vr0, vphi0, m, q, x(HCO+)
- 2014ApJ...786..114L: Disk outer radius 0.3 arcsec (120 AU), half thickness 0.1 arcsec, inner radius 0.01 arcsec; envelope outer radius 5 arcsec
- 2026A&A...705A.193L: ortho-to-para ratio 3; emitting area = beam for radially resolved
- 2026A&A...705A.193L: 17 au emitting region, disk mass 0.2 Msun, rc 30 au
- 2018ApJ...855..113D: Tx lower limit 80 K, upper 2000 K; unresolved source of 150 mas
- 2018ApJ...855..113D: R Dor: Re=2.5 R*, Rmax=6 R*, vturb=3 km/s; IK Tau: constant f, Rmax=40 R*, vturb=1 km/s
- 2019AJ....157..117M: stellar model scaled to 60 au; ISRF of Draine 1978
- 2021A&A...645A.145G: ortho-to-para H2CO 1.8-2.8; H2CS 3.0; CH3OH A/E = 1
- 2017ApJ...837...93Y: kinetic temperature 300 K; FWHM 40 km/s; L = 0.2 pc
- 2012ApJ...757..129R: PA fixed 151 deg; M*=0.8 Msun; inclination free; T10,q free per line
- 2024ESC.....8..665M: source size 1.3″; Tbg = 2.73 K; Tc = 0; systemic velocity 97 km/s
- 2020A&A...641A.160M: size 2", T=200 K, N=1.1e17 cm-2, dV=5.0 km/s, Voff=0, Vsys=62 km/s
- 2024ApJ...966...51G: X(1-0)=2.4, X(2-1)=3 with R21=0.8
- 2017MNRAS.469.3347M: n_coll=1e6 cm-3 adopted for SiO (1e5 and 1e4 excluded)
- 2017A&A...605A..21C: R_in = 50 AU for H2CO; Tc 12–36 K in 2 K steps; Rc 210–410 AU (H2CO), 70–350 AU (C18O) in 20 AU steps; X1/X2 0.001–10 (0.1–1000 for C18O)
- 2017A&A...605A..21C: Reference abundances 1e-12 (H2CO), 1e-7 (C18O)
- 2018A&A...616A..90C: Tex 90-300 K; N 1e13-1e17 cm-2; FWHM 1.8-2.4 (A), 0.8-1.2 (B) km/s
- 2018A&A...616A..90C: Only optically thin lines (tau<0.2) used
- 2020ApJ...895..119T: Tex = 8 K for other molecules; 12C/13C = 60
- 2020ApJ...895..119T: Tkin = 16 K, Tex = 15 K
- 2015ApJ...812...27A: fixed i=65 deg, Rin=0.1 AU, Rout=200 AU; 7 free parameters
- 2024ApJ...974...83Y: 50 walkers, 10000 steps, 2000 burn-in
- 2018A&A...617A..23B: Free parameters f0 and Re per molecule; radial points 0.05" to 0.75" in 0.1" steps
- 2018ApJ...861...72C: b = 0.57 km/s; sphere volume equals torus with 35 au x 10 au
- 2023MNRAS.526L..41P: 10^6 particles, 11 grain sizes 1 um-1 mm, M*=1.5 Msun, disc 0.01 Msun, H/R=0.1 at 50 au
- 2015ApJ...799..204C: turbulent velocity 40 m/s; inclination ~7 deg
- 2024A&A...687A.220I: Beam and source size fixed to 0.5"; FWHM 1 km/s; vLSR 2.7 km/s; 300 walkers; 1500 steps for joint fit
- 2024ApJ...964..166K: 12CO/13CO=70, H2/12CO=2e4, R21 CO(1-0)/CO(2-1)=0.95
- 2018ApJ...869...59W: 0.0001 < Md < 0.35 Msun, 200 K < T1au < 650 K; gamma=1 (disk), 0.5 (envelope); rc=100 au; Mstar 1.4 Msun
- 2018A&A...609A..47P: Freezeout at T<21 K with factor epsilon=8e-5
- 2025ApJ...992...55T: dv=0.1 km/s (2 channels), Tb=0.3 K limit for L1544
- 2017A&A...597A..53L: FWHM 1.0 km/s, source size 0.5'', tau <= 0.1
- 2017MNRAS.466...49J: 12C/13C = 50
- 2021A&A...655A..72S: source size varied about beam size at steps of 5 mas; 13C ratio 30
- 2014ApJ...796....1T: T(r)=max[23 K (rA/300AU)^-0.2, 19 K (rB/300AU)^-0.2]; kappa0.9mm=0.053; C18O abundance 1.7e-7
- 2026ApJ..1003...64Y: 100 walkers, 15,000 steps, 2,000 burn-in
- 2017A&A...597A..27S: 12CO/13CO abundance ratio 8; 12CO abundance 1e-4, 13CO 1.25e-5
- 2019AJ....158..162F: Tkin 10-250 K; stellar mass 1 Msun
- 2023PASJ...75.1105K: distance 140 pc, inclination 45 deg, PA 135 deg, disk mass 0.1 Msun, gas-to-dust 100
- 2019PASJ...71..105T: N(He+)/N(H+)=0.09
- 2012ApJ...749..162O: alpha = -1, 0, 2; cutoff 100 AU
- 2024ApJ...968L..19F: Delta v = 0.3 km/s; Tex = 6 K (or 9 K)
- 2019ApJ...880..130M: Source size <= (0.29±0.15)"x(0.12±0.10)" from 2D Gaussian fit of 10(-3)-11(-2) moment 0 map
- 2017A&A...603L...6H: 44 mJy/K flux-to-temperature conversion
- 2017A&A...603L...6H: CN column density 1e12-1e15 cm-2; C15N lower by 300 or 441
- 2024A&A...686A.201N: aperture 2" x ~0.1" at 60 au SE; v_z=2.5 km/s; two Gaussian components
- 2017MNRAS.469.2230M: Linewidth 1.1 km/s; source size 0.5"
- 2018ApJ...863..143C: T_ex = 30 K, X_CI = (3.0±1.5)e-5, alpha_[CI] = 9.43
- 2020ApJ...897L..33J: M*=15 Msun, rmin=13 au, Te=5850 K, inclination -25 deg, v0=10 km/s
- 2014ApJ...796..131O: SO ring 70-120 AU, 32 K, SO abundance 9e-7 (5000x outside); disk 54 AU, 0.3 Msun; j=6.1e-4 km/s pc
- 2024NatAs...8..587F: 128 walkers, 2000 steps after 1000 burn-in
- 2018A&A...614A..58B: Inclination 70 deg to plane of sky axis, PA -15 deg, X(13CO)=1.5e-5, X(12CO)=1.5e-4
- 2017MNRAS.465.2595M: Tk 20-300 K at 20 AU; 10-150 K outer belt; 100-2000 K inner
- 2015ApJ...813...99F: Fixed: d=122 pc, M*=2.3 Msun, PA=312 deg, Mgas=0.09 Msun, CO/H2=1e-4 (unless varied)
- 2024A&A...687A.233M: linewidth 1 km/s, source size 0.5 arcsec, vLSR 2.7 km/s, Tex 125 and 300 K
- 2019ApJ...885...82L: Algorithms: genetic, Levenberg-Marquardt, errorestim-ins
- 2019A&A...632L..12H: threshold 40 mJy/beam; r>0.3''
- 2017A&A...601A..49B: size 0.9", Trot 180 K, N = 1.0e17 cm-2, FWHM 5.0 km/s
- 2019PASJ...71...68K: Line widths fixed at average 3 sigma width: 330, 120, 140 km/s for Nucleus, CNR-E, CNR-SE
- 2024A&A...689A..85G: Fit 13.4-18 and 18-25.6 micron; noise 2 and 4 mJy; ~1e5 steps
- 2019MNRAS.490.1570B: Non-detections: 3 sigma level as intensity upper limit
- 2020MNRAS.493L.108B: Tex = 25 K at 90–110 au; 20–80 K gives column densities within errors
- 2019ApJ...872..196S: vsys = 6.96 km/s; match at 3 sigma for Aij >= 1e-5
- 2019ApJ...872..196S: Trot assumed 200 K where no diagram fit
- 2019A&A...623L...6P: Tex = 30-300 K; ring 0.33-0.75 arcsec (40-90 au)
- 2019A&A...623L...6P: N_H2CO up to 1e15 cm-2, line width ~6 km/s
- 2024ApJ...969..143I: filling factor restricted to <1
- 2019A&A...629A..72O: Tfit 152 +/- 4 K, adopted 140 K; size 1.2 arcsec; N = 4e17 cm-2
- 2018ApJ...868...95M: Tkin 5–6300 K, nH2 1e1–1e7 cm-3, NCO 1e12–1e22 cm-2, FF 1e-5–1, abundance ratios 1e-7–1e-3
- 2020ApJ...898...10T: X(C18O)=5.1e-7; T(r)=max[62 K (r_N/100au)^-0.5, 48 K (r_S/100au)^-0.5]; snapshot at 58.7 orbital periods
- 2013ApJ...770..142N: Hot Core 2'' clump: Tkin=200 K, n(H2)=1e8 cm-3, enhanced continuum
- 2026ApJ..1000L..32A: 256 walkers, 5000 steps after 1000 burn-in
- 2017A&A...605A..28D: 128^3 grid cells, 150 channels over +-100 km/s, 17 lowest rotational transitions
- 2016A&A...591A.108O: T = 20 K, width 15 km/s, v_LSR 3.68 km/s
- 2018ApJ...857...35S: RADEX: density 1e7 cm-3, column density 1e17 cm-2, velocity width 5 km/s
- 2024ApJ...962...48J: LTE trial T=150-300 K, Ntot=0.1-1.0e17 cm-2; line peak >=3 sigma_SC
- 2019A&A...632A..19T: source sizes 0.36'' (IRAS2A), 0.20'' (IRAS4A), 0.19'' (HH212)
- 2017ApJ...834....6S: Trot = 7.4 K adopted for regions without 2_K-1_K detection
- 2020MNRAS.496..394R: Tex = 20 K; median in 1.2"x0.9" ellipse, PA 60 deg
- 2015ApJ...811L...4Z: Tex = 10 K; D = 150 pc; radial velocity 5 km/s; size 1''; angle 30 deg
- 2024A&A...689A..65R: Priors uniform Tex in (0,50) K, Nt in (1e11,1e14) cm-2 (disk-averaged); Tex (0,100) K, Nt (1e11,1e16) radial
- 2018MNRAS.474.4988S: area 450 arcsec^2 (0.056 pc^2)
- 2018ApJ...853..147M: gas kinetic temperature 52 K to 210 K; stellar field at 85 AU
- 2017ApJ...843..150F: 80 walkers, 1000 steps, first 500 burn-in
- 2024ApJ...961..108K: Tex = 17.5 K (minimum mass), X_CO=1.7e-4, mu_H2=2.809
- 2016ApJ...825...79S: source size from continuum, else 10"
- 2015ApJ...815..106H: Tex = 50, 100, 150 K
- 2017A&A...597L...5B: V(2e15 cm)=2.5 km/s; inclination ~45 deg (±15); X(13CO)~2e-5; X(12CO)~1e-4
- 2019ApJ...872...92F: Tex = 20 K; also 1071 K and 237 K
- 2018ApJ...863...19A: velocity range 15<|V-Vsys|<50 km/s, Vsys=7.9 km/s; 1 beam cut width
- 2019ApJ...876...72L: CS fluxes integrated to 150 au (MWC 480) and 200 au (LkCa 15)
- 2017A&A...604L...2F: Source size 3'' for each component
- 2017ApJ...840L..11S: 12CO J=1-0 Gaussian FWHM = 375 km/s
- 2020ApJ...890...76N: Cores with at least three K lines above 3 sigma
- 2015ApJ...803...70S: Tex 20-80 K at DNC peak, 20-130 K at HN13C peak
- 2018A&A...612L..11S: mass-loss 2.5e-7 Msun/yr, v_exp 2.5 km/s, 12CO/H2=5e-4, 13CO/H2=5e-5
- 2019ApJ...877L..32M: robust = 0.5
- 2016A&A...595L...4L: 100000 iterations, burn-in 20000, thinning 50; source size fixed 0.2"
- 2019A&A...623A.124C: Tex = 25, 50, 75 K
- 2025ApJ...992L..15L: Tex = 15 K; mean molecular weight 2.72 m_H2; X(C18O)=2e-7; distance 5.1 kpc
- 2019ApJ...882..118X: Tbg 11.5, 27.4, 33.9, 43.1 K for Band 4, Band 6, Band 7 1.1 mm, 0.87 mm
- 2019ApJ...871..170M: Tex=Tkin=Trot=150 K, filling factor 1
- 2020A&A...634L..12D: Tex = 50 K; 12CO/13CO = 65
- 2013ApJ...773L..34K: R = 2000 km/s x 25 years
- 2025ApJ...984L..15P: 12CO abundance 1e-4 relative to H in warm layer; depleted below 20 K by a variable factor
- 2019ApJ...885L..39H: H2 density 10^4 cm^-3; velocity width 1 km/s
- 2017ApJ...849...56A: Free: Mdisk, Rout, p, Sdamp, H1, h; fixed: i=85 deg, Rin=0.1 AU, T1=403.5 K, q=0.5, kappa=0.031, g/d=100; outer radius 1000 AU
- 2018ApJ...862L...2F: CR ionization 1.3e-17 s^-1; 1% chemical desorption; grain radius 7 micron; UV photodesorption yield 1e-5
- 2019A&A...631A..25J: Tex = 124 K
- 2017ApJ...840....8S: tau within [0,100]
- 2020AJ....159...62C: Tex=50 K, X(H2/CO)~1e4, mean molecular weight 2.8, inclination 20 deg
- 2015ApJ...805..186L: mean CO intensity ~1.2 Jy/beam km/s between NK1 and NK5
- 2026A&A...705A..97K: Uniform priors; minimum T 140 K; maximum radius 10 au; N upper limit 1e20 cm-2
- 2019ApJ...875...24C: components rejected if peak <3.5 sigma; separation >2 channels (0.4 km/s)
- 2018ApJ...859..111H: 100 models per generation, 50 generations; Rc fixed 75 au, Rout 150 au
- 2024ApJ...963...72O: Tex = 40 K, mu = 2.8, X_CO=1e-4, d=405.7 pc
- 2019ApJ...871..112X: dV = 6.5 km/s, Vlsr = 64 km/s, Tex = 190 K
- 2018ApJ...863..129S: T_bg = 2.73 K
- 2020ApJ...896...35J: CH3OH LTE reference: N_H2=4e25 cm-2, vLSR=-52, FWHM 5 km/s, T=160 K, size 0.5'', abundance 1e-8
- 2013ApJ...777...85N: NH2D: Tkin 200 K, n(H2) 1e8 cm-3 for correction factor
- 2025ApJ...993...90S: 3 sigma_CO threshold
- 2019A&A...632A.101T: CO Tex = 75 K; SiO 9-47 K, H2CO 8-46 K, HCN 12-41 K from RADEX
- 2019A&A...632A.101T: RADEX grid: nH2 = 1e4-1e6 cm-3; Tkin = 75-700 K; dv = 10 km/s
- 2019A&A...625A.118K: alpha=1e-3; gas mass 0.003 Msun; 12CO/H2 = 1e-4; microturbulence 30 m/s
- 2025ApJ...987..197H: Tex = 50 K; Qrot=686.7, gu=21, Aul=2.567e-5, El=24.01 K
- 2017A&A...608A..22A: dV=150 km/s
- 2024MNRAS.534.2904C: 0.15'' beam, 250 m/s channels, noise 2.5 mJy, i=30 deg, PA=0, 100 pc
- 2016MNRAS.463L..74K: initial expansion velocity 2 km/s; stellar temperature 3000 K
- 2019A&A...631A..64B: source size 0.15''
- 2019ApJ...882..160Q: R1 and R2 grid interval of 5 au; vertical boundaries Σ21 = 3.2 and 100; i and PA fixed from continuum
- 2025A&A...694A.166C: Detection requires 3 sigma and velocity near systemic; need at least three lines per state to fit
- 2016A&A...587A..92M: Linewidth 5.4 km/s; Trot 150-180 K
- 2016ApJ...833...41Z: Fits including (1,1)-(5,5), and omitting (1,1) and (4,4); (9,9) omitted
- 2018ApJ...856..147O: Fitting for pixels above 5 sigma; Tex from peak intensity + 2.7 K CMB
- 2016ApJ...818..156C: p fixed to 1; 12-dimensional posterior
- 2019A&A...627A...1Q: Tex = 300 and 125 K
- 2017ApJ...834..178Y: q fixed -0.4; envelope within 80 deg of polar axis zero density
- 2016ApJ...823L..18H: Sigma_c=5e-5 g/cm2, gamma=1, r_c=100 AU, B=3, r_ring=150 AU, sigma_ring=20 AU
- 2016ApJ...823L..18H: turbulent broadening xi = 0.01 km/s
- 2016A&A...595A..87M: T = 150 K, linewidth 5 km/s, velocity 73.5 km/s, source size 1.0''
- 2016MNRAS.459.3629I: Ne=Np=1e9 cm^-3, Te=1e4 K, L=4.5e-7 pc, f_a~0.1, r_in~0.13 pc
- 2017ApJ...843...27L: Integrated intensities measured in lower disk atmosphere with 2 sigma cutoff
- 2017ApJ...839...43O: (z/r)up=0.3, rout=100 AU fixed; vary inner radius, lower boundary, power law
- 2026ApJ..1003...68Y: min_value 2.5 K (5 sigma), min_pix 50, min_delta 2.5 K
- 2019MNRAS.486.4114R: inclination varied; best CC fit 60-70 deg
- 2017ApJ...851..132C: data averaged to 25 channels of 0.4 km/s; fixed d = 388 pc
- 2019A&A...624A..70C: Aij ≥ 0.001 s-1, Eup ≤ 500 K; source size 3″, Tex 100 K, linewidth 0.8 km/s, N = 5e14 (CH2DCOH), 3.5e14 cm-2 (CH3COD)
- 2018MNRAS.475.5322S: Trot = 20, 40, 90, 160, 300 K
- 2018MNRAS.475.5322S: source size 0.2" for beam dilution
- 2019A&A...629A..75B: kappa_HCO+ = 0.2; cavity gas eta = 0.2; kappa_H13CO+ = 2 (<200 au), 6 (>200 au)
- 2019A&A...623A..93C: Tex = 300 K, source size 0.5", FWHM 1 km/s
- 2018MNRAS.478.2505I: Grid resolution 23.3 au
- 2016ApJ...823L..10W: layers z/r<=0.1, 0.1-0.2, 0.2-0.3
- 2016A&A...590A..93M: Source size 1.2'', Trot 150 K, linewidth 5.0 km/s, velocity offset -0.8 km/s, Vlsr 74 km/s
- 2018A&A...620L...6T: Trot fixed 150 K; extra components at 250 K and 50 K when needed
- 2018ApJ...856..117F: Free: T_atm0, T_mid0, q_atm, R_c, inclination, δv_turb; fixed: stellar mass, distance, CO abundance, PA, systemic velocity, offset
- 2017A&A...605L...6T: beam filling factor 1; same Tex for all transitions of a molecule
- 2018A&A...620A.170J: source size 0.5'', FWHM 1.0 km/s, vLSR 2.5-2.7 km/s fixed
- 2017ApJ...846L..26W: Free: Mdisk, Rdisk, gamma, T0, q, xi, M*, vsys, inclination, PA, small centering offset
- 2018ApJ...852..122H: Fiducial: N_CO=3e19 cm-2, R1=15 AU, R2=70 AU, A=3, f=0.025, Tmid10=40 K, Tatm10=125 K, q=0.47, Tfrz=27 K, Rin=0.05, Rout=215 AU
- 2019A&A...622A.206M: free: Ncol, Tex, VLSR, FWHM
- 2019MNRAS.485..739M: CO/H2 ~1e-4; CO/C18O ~550; minimum at 20 K
- 2019A&A...623A..96Y: Tbg = 2.73 K
- 2017NatAs...1E.130Z: D/H = 1.5e-5
- 2018A&A...617A.120M: IRAS 16293: N=3e12 cm-2, width 1.0 km/s; VLA 1623: N=2e12 cm-2, width 0.7 km/s
- 2017A&A...606A.125S: 50000 grid points, 12 iterations
- 2017ApJ...837..174O: kappa = 0.008 cm2/g at 1.2 mm, beta = 1.8; mean particle mass 3.83e-24 g
- 2019NatAs...3.1109P: 13CO abundance 7e-7; turbulent velocity 50 m/s; star R=2.25 Rsun, Kurucz 10,000 K
- 2019ApJ...883...98Z: zeta_CR = 1.36e-18 (standard) and 1.36e-17 s^-1 (high); gamma ±0.2 tests
- 2019ApJ...871..100H: Free: rho0, p, theta_flared, V_rot,0, V_infall,0, F_C18O; C18O fit at |V-Vlsr|<1.6 km/s, CO at >1.6 km/s
- 2019ApJ...871....5T: r_pk=95 au, sigma_r=10 au, Sigma_d,0=1.84e-2 g cm^-2, h_d=9.8 au, a_max=1 mm, gas Sigma ~ r^-1 for 8-320 au, h_g=13.2 au (r/95 au)^1.25, gas-to-dust 100
- 2016MNRAS.461..385B: C18O abundance 1.4e-7 to 1.7e-6; N_CO photodissociation 1e18,1e19,1e20 cm-2; vturb 0.01-0.1 cs
- 2018A&A...612A..72J: Freeze-out factor 0.01 below 30 K; abundances lowered by factor 5 for matching C18O
- 2019ApJ...882L..31B: Tex = 50 K
- 2018A&A...614A.123P: Cubic grid 1 pc side, max density difference between cells 10%, min cell 100 au, ~10^7 cells
- 2019ApJ...872..200H: 20% error on ln(Eu/gu); 80% confidence intervals
- 2017A&A...599A.101V: d=54 pc, i=6 deg, PA=155 deg
- 2018ApJ...863L..35M: Tex=135 K, dV=3.2 km/s, N=1.3e17 cm-2
- 2019ApJ...875...62Y: Tex lower limit 45 K
- 2016MNRAS.460..627K: Velocity integration limits 9-20 km/s red, -4 to 6 km/s blue
- 2019ApJ...877L..25M: Tkin=100 K, linewidth 5 km/s
- 2019NatAs...3..517Z: Te = 8000 K, N(He+)/N(H+)=0.08
- 2019PASJ...71...44H: Tex = 20 K


### Assumptions (bibcode: value)
- 2016A&A...587A..91B: LTE, uniform physical structure, Gaussian source; deuterated species share parameters of main isotopologue
- 2016A&A...587A..91B: 12C/13C used to derive main species N from 13C isotopologues; statistical 2:1 distribution for out-of-plane/in-plane conformers
- 2018ApJ...864..170G: Emission thermalized (LTE) given densities >1e6 cm-3
- 2018ApJ...864..170G: LTE; uniform o/p of 3 for total abundance
- 2024A&A...682A..74F: Emission fills the beam (theta_S fixed)
- 2019A&A...628A..10B: LTE, source size 2'' for all species
- 2019A&A...628A..10B: Background continuum negligible (found invalid at this resolution)
- 2017A&A...608A..38O: optically thin, LTE, alpha_CO = 0.25 at Tex 29 K, spherical outflow
- 2017A&A...608A..38O: 12CO/13CO = 100; HCO+/12CO = 1.3e-4
- 2020A&A...636A..67A: LTE; H2CO modeled with source size ~0.15'' below beam
- 2020A&A...636A..67A: N(H2) from continuum with Tdust=100 K, kappa=1.0 cm2/g, gas-to-dust 100
- 2015A&A...581A..85P: X_CO = 1e-4; CO optically thin (lower limit in B2)
- 2015A&A...581A..85P: C17O/CO=1/1792, X_CO=1e-4, Tex 50-500 K, factor 1.4 for He
- 2025ApJS..276...49J: Dust and gas coupled, gas in LTE; kappa=2.2 cm2/g at 230 GHz, beta=1
- 2025ApJS..276...49J: LTE
- 2025ApJS..276...49J: T_rot fixed 120 K, eta fixed 0.384
- 2018A&A...620A..75K: CO abundance 4e-4 relative to H2; LTE; spherical symmetry; distance 102 pc
- 2018A&A...620A..75K: LTE; solar composition with fully molecular hydrogen (Asplund et al. 2009)
- 2016MNRAS.460.2933M: h=0.07 and orientation fixed to dust fit; Keplerian rotation; systemic velocity 0.1 km/s; electrons as collision partner
- 2020ApJ...890..142P: LTE, all lines from same environment, emission fills beam; mu=2.37, t0~0.01
- 2019A&A...623A..68T: LTE, beam filling factor 1
- 2019A&A...623A..68T: HCO+ abundance 3e-9 (diffuse), 2e-8 for N>9.4e13, log-interpolated between
- 2015ApJ...798...85P: Same excitation temperature, CMB neglected, 12CO/13CO=76, 12CO/C18O=500
- 2015ApJ...798...85P: [H2]/[12CO]=1e4, [12CO]/[13CO]=76, LTE
- 2015ApJ...798...85P: Keplerian rotation, ISM CO abundance, vertically isothermal, axisymmetric
- 2026A&A...707A.120H: LTE for C17O 1-0; N(13CO)/N(C18O)~8 for consistency check
- 2021A&A...656A..46M: LTE, single Gaussian component, column density linear in source solid angle
- 2021A&A...656A..46M: L_IR = 2.1e10 Lsun
- 2021A&A...656A..46M: Factor of 2 uncertainty in H2
- 2020MNRAS.492.1180R: LTE, single transition so Tex cannot be derived
- 2020MNRAS.492.1180R: He collision rates scaled to H2 (x1.385 PN, x1.4 PO)
- 2024A&A...689A..64B: LTE, optically thin lines, beam filling factor 1
- 2024A&A...689A..64B: Semi-infinite slab geometry, CBR 2.7 K, H2 OPR=3, line widths from measured averages, 15% calibration error
- 2014Sci...345.1584B: LTE
- 2014Sci...345.1584B: Optically thin transitions
- 2020MNRAS.497.2811K: LTE, mu=14, axisymmetric
- 2020MNRAS.497.2811K: collision rates from Dickinson & Richards 1975, Allison & Dalgarno 1971
- 2019ApJ...870L..26C: H13CN photodissociation and pumping rates same as HCN
- 2015ApJ...803...60S: [13CO]/[H2]=1.4e-6, [CO]/[13CO]=70, [CO]/[H2]=1e-4, [HCO+]/[H2]=1e-9; uniform sphere
- 2015ApJ...803...60S: 13CO and CO from same cloud; 12CO(1-0) optically thick
- 2015RAA....15.2213A: Rotational symmetry, negligible absorption, LTE
- 2015RAA....15.2213A: LTE, optically thin
- 2017ApJ...848..101V: optically thick 12CO, same filling factor for 1-0 and 3-2, LTE
- 2017ApJ...848..101V: [12CO]/[13CO]=50, [12CO]/[H2]=1e-4, LTE, 13CO optically thin with finite-opacity correction
- 2020A&A...644A..59K: H2 main collisional partner; ortho/para 3; CMB 2.73 K only external radiation; isothermal homogeneous gas
- 2020ApJ...900..131L: Solar abundances (Asplund09); LTE
- 2020ApJ...888L..28S: negligible background, T<10,000 K, thermal LTE electron-proton free-free emission
- 2025ApJ...986L..22R: Gas kinetic temperature 4 K
- 2025ApJ...986L..22R: H2CO-CO collision cross-section 5e-14 cm-2 (thermalization approximation)
- 2017A&A...605A..78A: LTE thermal free-free and H- absorption proportional to f^-2
- 2026A&A...705A.198M: LTE with Tex equal to peak brightness temperature; tau12CO=77 from ISM 12C/13C
- 2019ApJ...883..193N: HCN-H2 abundance 1e-9
- 2015ApJ...798..124R: LTE
- 2025A&A...696A.100G: all C2H rotational lines share the same spatial distribution; optically thin
- 2025A&A...696A.100G: dust modified blackbody, T=50 K, opacity 0.03(160/lambda)^1.6
- 2024A&A...689A.317G: LTE; optically thin Gaussian dust; SiO abundance 6.6e-6; distance 265 pc
- 2024ApJ...962....1S: OH abundance 5e-7 chosen as compromise and to match the empirical relation
- 2020ApJ...894...76W: Non-LTE ionization-excitation and radiative transfer; hydrostatic equilibrium Avrett & Loeser solar starting model
- 2018A&A...620A.119D: Tx lower limit = CMB temperature 10.1 K (also 20 and 30 K tried)
- 2024ApJ...977..251H: X_CI=3e-5, r41=0.46, alpha_CO=0.8, Td=25 K, alpha_dust=6.7e19, helium factor 1.36
- 2018ApJ...866L..12G: LTE, optically thin, 300 K
- 2021ApJ...908..163M: X[CI]=1.5e-5, Q10=0.5 (LTE, optically thin)
- 2020ApJ...890..167T: Tex = 36 K, optically thin, [HCN]/[H2]=4.8e-8
- 2016ApJ...832..158Z: Same Tex and beam filling factor for all isotopologues, C18O optically thin, LTE
- 2016ApJ...832..158Z: CO abundance 1e-4 relative to H2; 2.34e-24 g per H2; beam filling factor 1
- 2018ApJ...864..133T: LTE; thermal broadening only for tau
- 2018ApJ...864..133T: Thermal H2 ortho-para ratio; slab geometry; no beam-smear correction
- 2025A&A...699A.382M: chi(CO)~1e-4, mu_g=2.3, 16O/18O=560, inclination 40±10 deg, d=163 pc
- 2025A&A...699A.382M: chi(HCO+)~1e-8, 12C/13C~69
- 2018ApJ...853L..19S: LTE
- 2018ApJ...853L..19S: LTE, optically thin
- 2018ApJ...853L..19S: All species co-spatial with methanol
- 2017A&A...602A..42K: LTE
- 2017A&A...602A..42K: ortho-to-para ratio 3:1; main collider ortho H2; 22 GHz intensity uncertainty 50%
- 2020ApJ...898...54T: optically thin
- 2020ApJ...898...54T: LTE, optically thin
- 2014ApJ...787..112C: kappa_1.3mm=0.42 cm2/g, beta=2, dust-to-gas 0.01, NH2=2.5e24 cm-2 for dust opacity
- 2025A&A...693A.101T: Optically thin, LTE, beam-filling emitting area
- 2025A&A...693A.101T: Densities from DALI model
- 2018A&A...615A..28D: vLSR 33 km/s (IK Tau), 7 km/s (R Dor)
- 2018A&A...615A..28D: Optically thin, LTE, no radiative pumping differences; masers excluded
- 2017ApJ...839...86H: T∝R^-0.5, vertically isothermal, turbulent linewidth 10 m/s, PA fixed at -71.4 deg
- 2020ApJ...898...97B: Emitting area = mask size; Trot unknown
- 2019MNRAS.485.2457H: spherical symmetry; uniform abundance, density and temperature
- 2013ApJ...774...16R: 80% of gas is H2; constant CO:H2 abundance; CO depleted by 1e8 below freezeout; ISM isotopologue ratios
- 2024IJAsB..23...14M: LTE valid given gas density 7e7 cm^-3
- 2024IJAsB..23...14M: Optically thin, LTE; N(H2)=1.30e23 cm^-2 for abundance
- 2020ApJ...898...75I: CO/13CO isotopic ratio = 40
- 2020ApJ...898...75I: [CO]/[H2] = 1e-4; Tbg = 2.73 K; [CO]/[13CO] = 40
- 2020A&A...644A..84M: LTE, justified by n ~ 1e8 cm-3
- 2025A&A...696A..31G: LTE; beam dilution not corrected
- 2025A&A...696A..31G: OPR 0.25, beam dilution factor unity, same emitting region for all transitions, line width averaged over transitions
- 2015A&A...582L...1T: LTE
- 2020ApJ...892...99C: T(r)=T100 sqrt(100 au/r); mu=14; line broadening 1 km/s; Gaussian line profile
- 2017Icar..286..289L: LTE; molecular mass 27.94; surface radius 1190 km; Fresnel surface with dielectric constant 3.5
- 2015ApJ...801...63M: XCO = 0.5e20 cm-2 (K km/s)-1, uncertain at ±2x
- 2013A&A...557L..11B: LTE excitation valid for low-J high-opacity transitions
- 2019MNRAS.485..229R: CO/H2 = 3.2e-4 (Milky Way gas-phase carbon, all in CO); optically thin LTE
- 2020A&A...633A..13D: H2 ortho-to-para 3, CO/H2 6.5e-4, equatorial plane reflection symmetry
- 2021A&A...656A..68E: LTE in radiation formation
- 2025NatAs...9.1476C: Steady-state coma; electron density scaling x_ne=0.2; collisional cross-section with H2O 5e-14 cm^-2; T1=T2
- 2017ApJ...850...35L: Thermal free-free emission in LTE
- 2018A&A...614A..42M: Tex ~16 K, LTE, homogeneous absorber, A_C=1.6e-4
- 2015MNRAS.447.3936M: Dust, colliders and CO co-located, axisymmetric; uniform T_k; colliders H2 (primordial) or e- and H2O (secondary)
- 2018A&A...615A.141B: Spherical symmetry; LTE; dust temperature = CH3OCHO Tex for N_H2
- 2018A&A...615A.141B: LTE; extended foreground filling beam
- 2019NatAs...3..314L: LTE; CH3OH column = 13CH3OH x 60
- 2025A&A...693A..76C: optically thin, LTE
- 2025A&A...693A..76C: LTE, density >1e7 cm-3
- 2018A&A...619A..28L: LTE, source size 0.5", Tbg=21 K due to dust
- 2019A&A...624A.125M: All isotopologues share distribution and velocity profile; column density ratios equal atomic isotopic ratios
- 2020MNRAS.497.5454I: Optically thin, LTE, beam-filling factor 1, Qrot = 1.23 Trot^1.5
- 2015ApJ...813L..19J: Dust temperature 190 K from LTE modeling average
- 2015ApJ...813L..19J: 12C/13C = 60; CH3CN abundance 1e-8
- 2024AJ....167...66Y: common emitting size, Tex and line width under LTE
- 2024AJ....167...66Y: LTE, common Tex and line width, Lorentzian broadening gamma
- 2017A&A...598A..53D: Optically thin, LTE; same FWHM for all HFS components
- 2017A&A...598A..53D: Optically thin LTE emission
- 2016ApJ...829....6W: Optically thin, LTE; H2/CO = 1e4 for total gas
- 2020A&A...644A.119P: LTE, optically thin, o/p ratio of H2CO from Guzman+18
- 2017ApJ...842...94T: Optically thin line and continuum
- 2013A&A...555A..73K: Spherical symmetry; emitting size = N/n
- 2013A&A...555A..73K: Wind age 400 yr from mean velocity -18.6 km/s and extent ~13''
- 2024A&A...686A..59N: LTE, beam dilution of unity (source fills ~1'' beam)
- 2020A&A...643A..89P: Z_CO = 1e-4; LTE H2 ortho-to-para ratio; Yang2010 collision rates
- 2020MNRAS.498L..87B: Spherical geometry, A/E=1, 12C/13C=60, FWHM 3.5 km/s, collisional excitation only
- 2020MNRAS.498L..87B: Trot = 100 K from methanol LVG for methyl formate and ethanol
- 2024A&A...689A.263D: LTE; no PSF correction
- 2024A&A...689A.263D: Fritz et al. 2011 extinction curve
- 2015ApJ...803...97S: LTE, optically thin after exclusion; tau~2 at Smu2~35 assuming 150 K
- 2020ApJ...898..146M: Optically thin, electron collisions dominate, little H2, CO co-located with dust at 118 au
- 2019AJ....157..251T: Neptune's disk-average matches the nominal model; clouds ignored; LTE
- 2015PASJ...67....8N: Optically thin lines, LTE with single Tex
- 2016MNRAS.458.3134R: optically thick, thermalized CO gives excitation temperature
- 2021A&A...655A..80D: AlCl modelled dust-free with 700 K blackbody IR field; AlF with silicate dust; H2 ortho-to-para 3; SiS-H2 rates as stand-in for AlCl
- 2021AN....342.1160P: alpha_CO = 0.8 Msun/(K km/s pc^2) for outflow
- 2020ApJ...891L...8M: Free-free hydrogen absorption main opacity source
- 2016ApJ...830L..37I: Tex 100 K as typical of IRAS 16293-2422 COMs and close to 111 K dust temperature
- 2016ApJ...830L..37I: Dust temperature equals LTE temperature (100 K)
- 2017AJ....153..233F: HCO+ abundance 1e-9
- 2017AJ....153..233F: Mgas = Mdisk; 80% H2 by weight, mean molecular mass 2.37; constant abundance with freeze-out/photodissociation cuts
- 2024ApJ...966..117X: constant CO abundance, H2 dominant collision partner
- 2024ApJ...966..117X: optically thin, LTE
- 2019A&A...624A..82B: LTE, optically thin lines, source size equal to synthesised beam
- 2019A&A...624A..82B: CH2NH and NH2CHO Tex fixed to CH3OH values
- 2018ApJ...856...97S: [HCO+]/[H13CO+] = 50 or 25; same beam filling
- 2018ApJ...856...97S: [CO]/[H2]=1e-4, [HCO+]/[H2]=1e-8, XCO=0.8e20
- 2020A&A...635A..48M: LTE, single Trot, filling factor 0.5, isotopologue Trot fixed to main species, continuum correction with Td 30.1 K (A), 21.2 K (B)
- 2014ApJ...786..114L: Dust and gas same temperature; LTE; kappa from Beckwith1990 with beta=1; thermal line width only; free-fall infall and constant specific angular momentum in th…
- 2026A&A...705A.193L: LTE
- 2018ApJ...855..113D: Optically thin emission, LTE, all H in H2
- 2019AJ....157..117M: constant surface brightness belt between 20 and 100 au, face-on
- 2021A&A...645A.145G: Optically thin emission and LTE
- 2017ApJ...837...93Y: CS abundance relative to H x_CS = 5e-7
- 2012ApJ...757..129R: vertically isothermal, mu=2.37, Keplerian, vr=vz=0
- 2024ESC.....8..665M: LTE valid since gas density ~1e8 cm^-3
- 2020ApJ...903...94M: XCO 4e20; CO(2-1)/(1-0)=0.85; [H2]/[13CO]=1.4e6
- 2020A&A...641A.160M: LTE
- 2024ApJ...966...51G: Same Tex for 12CO and 13CO from 12CO; N(H2)/N(13CO)=3e6; spherical virialized clumps; distance 50 kpc
- 2012ApJ...757L...4J: isothermal medium, LTE
- 2020AJ....159..288M: κν=2.3 cm2/g, grain temperature ~15 K at 140 au
- 2018ApJ...859L..15C: LTE for Boltzmann comparison of v=0 and v7=1
- 2015A&A...582L...4M: Excitation temperature equals CMB temperature at z=0.89, 5.14 K; optically thin lines
- 2017MNRAS.469.3347M: distance 50 kpc; H2 collisional partner
- 2017A&A...605A..21C: i = 44 deg, PA = 133 deg, d = 122 pc; OPR = 3 at T>=200 K and exponentially lower below; H2 collision partner; dust continuum optically thin
- 2017A&A...605A..21C: LTE; Trot equals kinetic temperature; co-spatial emitting regions
- 2024ApJ...967...15K: LTE
- 2024ApJ...967...15K: Spherical homogeneous HII region, LTE, He+/H+=0.096
- 2018A&A...616A..90C: LTE, source size 0.5 arcsec, Gaussian profiles, continuum as background temperature
- 2019A&A...629A...6T: 13CN optically thin; LTE
- 2019A&A...629A...6T: LTE, optically thin 13CN
- 2020ApJ...895..119T: Tkin equal to dust temperature 16 K; Tex/Tkin = 50%
- 2015ApJ...812...27A: LTE, X(C18O)=3.0e-7, zero turbulence, mean molecular weight 2.37 mH, position/PA from continuum, Vsys 6.4
- 2024ApJ...974...83Y: Common Tex for all species, optically thin, Gaussian line shape, Tcmb=2.73 K
- 2018A&A...617A..23B: Distance 395 pc, Mdot 3e-6 Msun/yr, L 7500 Lsun, expansion velocity 16.5 km/s, spherical symmetry
- 2018ApJ...861...72C: Carbon ionisation provides the electrons; uniform sphere geometry
- 2023MNRAS.526L..41P: distance 140 pc, gas-to-dust 100, astrosilicate grains, Tgas=Tdust, CO LTE, turbulent velocity zero
- 2019ApJ...872..121U: X(H13CO+)=6e-11, X(C34S)=4.87e-10, distance 8.5 kpc, mu=2.35e-57 Msun, no external pressure or magnetic field
- 2015ApJ...799..204C: 12C/13C=70±10, 18O/16O=540±30
- 2024A&A...687A.220I: LTE excitation
- 2020MNRAS.496..364R: optically thin and LTE
- 2020ApJ...891..164S: Optically thin, LTE; SO from SO(3_3-2_3) with Trot=50 K
- 2024ApJ...964..166K: 12CO optically thick, 13CO optically thin, same Tx, LTE
- 2018ApJ...869...59W: LTE, no spatial gas-dust segregation, thermal coupling; 13CO/C18O abundances 3.5e-6 and 4.8e-7
- 2018ApJ...869...59W: Envelope T=15 K, C18O abundance 4.8e-7, LTE optically thin
- 2018A&A...609A..47P: T_ex = T_kin (LTE)
- 2018A&A...609A..47P: Gas temperature equals dust temperature; CO in LTE
- 2025ApJ...992...55T: LTE; Tex 7 K (L1544, MC 35-mm), 9 K (MC 27)
- 2025ApJ...992...55T: static physical structure at each radius, 2e5 yr
- 2017A&A...597A..53L: LTE, Gaussian line profiles, common Tex = 125 K for all species
- 2017MNRAS.466...49J: LTE, equal Tex, optically thick 12C, thin 13C, equal beam filling
- 2017MNRAS.466...49J: Critical densities at Tex=20 K, optically thin
- 2021A&A...655A..72S: LTE, Gaussian emitting region, single temperature/density component
- 2014ApJ...796....1T: LTE, Tex = Tk
- 2026ApJ..1003...64Y: H2S ortho-to-para ratio 3; LTE; SO2 radius same as SO; M*=2.0 Msun; i=46.7 deg
- 2017A&A...597A..27S: Constant temperature per structure; density falls as 1/r except for constant density in the inner ring and inner main-ring rim; radial Hubble-like velocity
- 2019AJ....158..162F: Gas co-located with belt, Keplerian, optically thin
- 2023PASJ...75.1105K: 12CO abundance 9.83e-5 relative to H2, 13CO 1.49e-6, C18O 2.26e-7
- 2019PASJ...71..105T: optically thin line and continuum; spherical geometry with L ~1.14e16 cm
- 2012ApJ...749..162O: Hyperfine levels in LTE; DCN vertical layer same as HCN
- 2024ApJ...968L..19F: LTE, ortho-to-para ratio of unity
- 2019ApJ...880..130M: LTE, optically thin lines; column densities are lower limits; CH3OCHO corrected by factor 2.1 for torsional states
- 2017A&A...603L...6H: Equal excitation temperature for all hf lines within each group
- 2017A&A...603L...6H: Single excitation temperature for CN and C15N
- 2024A&A...686A.201N: Tex=100 K, 12C/13C=70, X_HCN=1e-7, optically thin
- 2017MNRAS.469.2230M: LTE
- 2017MNRAS.469.2230M: 16O/18O=500; 12C/13C=68
- 2018ApJ...863..143C: LTE, optically thin [CI], CO and [CI] trace the same gas
- 2020ApJ...897L..33J: Ne follows r^-2 law
- 2014ApJ...796..131O: edge-on, inclination 90 deg
- 2024NatAs...8..587F: Optically thin, LTE, 10% flux systematics
- 2018A&A...614A..58B: LTE level populations, constant abundances, axial symmetry, D = 1100 pc
- 2017MNRAS.465.2595M: nC/nC+=1, nCO/nC=1/100 as in beta Pic; vertical aspect ratio 0.1
- 2021A&A...648A..19W: 12CO optically thick and LTE so TB traces kinetic temperature
- 2018PASJ...70...85T: CS/C34S = 22.35, equal filling factors and Tex, mu=2.8, X(CS)=1e-8, A21=2.2e-5 s-1
- 2015ApJ...813...99F: CO frozen out below 19 K and photodissociated above column threshold (abundance reduced by 8 orders of magnitude); LTE; mu=2.37
- 2024A&A...687A.233M: Tex between 125 K and 300 K
- 2019ApJ...885...82L: LTE; other species' Trot fixed to that of SO2; same centroid velocity for isotopologues
- 2019A&A...632L..12H: Optically thin lines, equal excitation temperature, flux ratio = column density ratio within 1%
- 2019A&A...632L..12H: Uniform physical conditions
- 2024A&A...691A.180F: LTE, optically thin
- 2017A&A...601A..49B: LTE valid given high densities of hot cores
- 2019PASJ...71...68K: Spherical homogeneous geometry; Tbg = 2.73 K; [CO]/[H2]=6e-5, [HCO+]/[H2]=8e-9
- 2020ApJ...889...43Z: Same excitation temperature for all transitions; beam filling factor unity
- 2020ApJ...889...43Z: Inclination ~80 deg for SMA1
- 2014A&A...569A..11S: 12C/13C = 50
- 2024A&A...689A..85G: distance 140±10 pc; Gaussian line FWHM 4.7 km/s
- 2019MNRAS.490.1570B: Gas temperature equals dust temperature, T_dust = 13100 D^-1/2 K
- 2019MNRAS.490.1570B: Peanut distance approximated by projected distance, giving upper limit T ~500 K
- 2018ApJ...869...75M: LTE, optically thin, T=30 K, CO/H2=1e-4
- 2020MNRAS.493L.108B: LTE, optically thin
- 2017ApJ...850L..30Y: T ~100-300 K; isotropic outflow orientation; 8 kpc distance
- 2014ApJ...785L..12C: [H2]/[CO] = 10^4; mu~2.3; Keplerian rotation
- 2019ApJ...872..196S: LTE, single Trot
- 2019A&A...623L...6P: LTE, optically thin, CH3OH co-spatial with H2CO
- 2024ApJ...969..143I: Para-H2CO only, so no ortho-to-para ratio needed
- 2019A&A...629A..72O: LTE
- 2018ApJ...868...95M: Tbg 2.73 K, FWHM 150 km/s, [CO/H2]=1e-4
- 2020ApJ...898...10T: LTE
- 2013ApJ...770..142N: ortho:para H2O = 3; 16O/18O=250; 18O/17O=3.6; 10% calibration uncertainty
- 2026ApJ..1000L..32A: OPR = 3
- 2017A&A...605A..28D: distance 150 pc; 12CO/H2 = 6.5e-4
- 2016A&A...591A.108O: LTE, optically thin
- 2023PASJ...75..424O: beta = 1, kappa 2.25 cm2/g at 225 GHz; 13CO/H2 = 1/67e-4; CO/H2 = 1e-4
- 2018A&A...617A..54L: Excitation temperature equals CMB; N(HCO+)/N(H2)=3e-9
- 2018ApJ...857...35S: LTE
- 2018ApJ...857...35S: LTE, optically thin
- 2018ApJ...859..131L: LTE excitation; solid angle of beam-convolved Keplerian mask
- 2018ApJ...859..131L: Distance 59.5 pc, PA 155 deg, inclination 8 deg, M*=0.8 Msun
- 2024ApJ...962...48J: LTE, optically thin, Tex=Trot
- 2019A&A...632A..19T: CH3OD Trot fixed to that of CH2DOH; two CH3OD partition functions; 12C/13C = 70
- 2017ApJ...834....6S: LTE, optically thin, same beam-averaged column density for A and E types
- 2020MNRAS.496..394R: single Tex=20 K; higher or variable Tex changes results by factor <~2
- 2015ApJ...811L...4Z: H2/CO abundance ~1e4; mean molecular weight 2.8; optically thin, LTE
- 2024A&A...689A..65R: LTE, optically thin, ortho-to-para ratio 3:1
- 2018MNRAS.474.4988S: gas/dust temperature 140 K; CO/H2 number ratio 1e-4
- 2018ApJ...853..147M: All species co-located with CO; LTE excitation
- 2021AJ....161...38O: LTE
- 2018MNRAS.475..448T: 12CO/H2=2e-4, 16O/18O=300
- 2016ApJ...827...72S: Optically thin, LTE
- 2016ApJ...827...72S: Same region as SO2; Trot = 100 K
- 2017ApJ...843..150F: LTE; 20% amplitude calibration uncertainty
- 2017ApJ...843..150F: d=122 pc, PA=312 deg, Mgas=0.09 Msun, XCO=1e-4 for CO, LTE, ring sigma=0.1 R, v_turb proportional to sound speed
- 2024ApJ...961..108K: Optically thin, LTE
- 2016ApJ...825...79S: Tex uncertainty +-20 K changes N by 40%
- 2018ApJ...867L...6B: Te 6000 K, LTE optically thin H30α
- 2020A&A...635A.189F: linewidth about 3 km/s
- 2020A&A...635A.189F: LTE justified by n(H2)>10^7 cm^-3
- 2015ApJ...815..106H: X(C18O)=1e-7; uniform relative abundances over position-velocity space
- 2024ApJ...969..165D: LTE and optically thin; Tex 20-50 K
- 2024ApJ...969..165D: tau=0
- 2017A&A...597L...5B: LTE level populations; distance 1 kpc
- 2019ApJ...872...92F: LTE; NLTE would likely raise the limit
- 2021A&A...651L...6B: Emitting area 1.2e-11 sr (5σ extent of 0.9 mm dust); LTE; 32S/34S = 22
- 2018ApJ...863...19A: LTE, Tex=30 K, optically thin, X(12CO)=2.7e-4, same intrinsic momentum in all four flows
- 2018ApJ...863...19A: LTE, gas T = dust T = 20 K, kappa(850um)=0.035, beta=1, gas-to-dust 100, mean molecular weight 2.37
- 2019ApJ...876...72L: LTE (Tex = Tkin) and optically thin lines; beam filling factor of unity
- 2019ApJ...876...72L: H2CS ortho-to-para ratio of 3
- 2024A&A...692A..97M: LTE, optically thin, beam filling factor 1
- 2017A&A...604L...2F: LTE, same Trot and source size for all species, optically thin
- 2017ApJ...840L..11S: LTE, 13CO and C18O optically thin, total star-forming molecular mass 10^9 Msun, Z=0.02
- 2020ApJ...890...76N: LTE, optically thin; Q(T) from Araya2005
- 2015ApJ...803...70S: Same Tex for DNC and HN13C; HN12C/HN13C = 60-80
- 2025ApJ...994...98F: X_CO=5e-5, T_frz=20 K, sigma_crit=0.01 g cm-2, D_CO=1e-3, CO/13CO=69, CO/C18O=557
- 2025ApJ...994...98F: Optically thick LTE gas so T_gas = T_b
- 2018A&A...612L..11S: Spherical uniformly expanding envelope, ISRF only external UV
- 2019ApJ...877L..32M: CO mass upper limit assumes LTE
- 2016A&A...595L...4L: LTE
- 2019A&A...623A.124C: Optically thin, LTE, disk mass ~0.09 Msun all H2, d=122 pc
- 2025ApJ...992L..15L: LTE, optically thin C18O
- 2019ApJ...882..118X: Negligible beam dilution; thermalized transitions since n_H2 >> n_crit (~1e5 cm-3)
- 2019ApJ...871..170M: Optically thin emission
- 2020A&A...634L..12D: Steady flow; LTE
- 2013ApJ...773L..34K: LTE, excitation temperature equals kinetic temperature
- 2025ApJ...984L..15P: Astrosilicate grains, dn ∝ a^-3.5 da, 0.03-1000 micron, gas-to-dust 100; zero turbulent velocity; 1 Myr isochrones
- 2019A&A...623L...1K: optically thin, single-temperature LTE gas
- 2019ApJ...885L..39H: Electron collisions ignored
- 2017ApJ...849...56A: LTE, vertically isothermal, same density power-law index for disk and envelope
- 2018ApJ...862L...2F: Excitation temperature 10-40 K
- 2018ApJ...862L...2F: LTE, gas-to-dust ratio 100, star mass 0.7 Msun
- 2024ApJ...970...28O: gas and dust well mixed, T_gas = T_dust; LTE
- 2019A&A...631A..25J: 16O/18O = 560
- 2017ApJ...840....8S: Spherical geometry for column length (half of source size for Arp 55)
- 2020AJ....159...62C: tau0=0.2 from C18O/12CO ratio ~5
- 2015ApJ...805..186L: Tex~50 K, CO abundance 8.5e-5, jet diameter ~0.2 arcsec
- 2026A&A...705A..97K: linewidth 4.71 km/s; distance from Gaia DR3 parallax inverse
- 2019A&A...627A.114K: Single excitation temperature for all species, LTE
- 2019MNRAS.484.1257M: HCN in LTE at 40 K; CO/H2 ratio 1e-4
- 2019ApJ...875...24C: single excitation temperature equal to dust temperature; single beam filling factor
- 2018ApJ...859..111H: LTE with Tgas=Tdust; CO/H2 = 1e-4; freeze-out below 20 K with depletion factor 1000
- 2024ApJ...963...72O: Column density varies within 20% for Tex 20-50 K
- 2019ApJ...871..112X: LTE, single Tex, dense LMH region (n>1e9 cm^-3), negligible beam dilution
- 2018ApJ...863..129S: optically thin, LTE, single component
- 2013ApJ...777...85N: 12C/13C = 60; H2CO ortho:para 3:1
- 2025ApJ...993...90S: X_CO=1e-4, T_ex=50 K; alternative CO-to-H2 factor 2.0e20
- 2017A&A...607L...5Q: LTE (Tex=TK); spherical emission; no IR pumping
- 2017MNRAS.469.3518M: ionization fraction 0.5, C/CO=100
- 2019A&A...632A.101T: Optically thin emission; HCN abundances lower limits
- 2019A&A...625A.118K: Vertically isothermal disk, LTE CO
- 2025ApJ...987..197H: Constant Tex = 50 K for outflowing gas
- 2019A&A...628A..27B: LTE valid at high densities
- 2017A&A...608A..22A: CO abundance 1e-5 to 1e-4
- 2017A&A...608A..22A: gas-to-dust ratio 100
- 2020ApJ...890..129K: Tgas 70 K, inclination 50 deg
- 2014ApJ...789L...4T: Tex = 10 K; X(H13CO+) = 1.0e-9
- 2024MNRAS.534.2904C: T_dust=T_gas, LTE, 12CO/H2=1e-4, grain size dist s^-3.5
- 2016MNRAS.463L..74K: Outflow emission neglected in fits
- 2017ApJ...839L..14H: Optically thin, LTE
- 2019A&A...631A..64B: LTE, optically thin; CDMS spectroscopy
- 2019ApJ...882..160Q: Hyperfine levels in LTE; HCO+ collisional rates used for N2H+
- 2025A&A...694A.166C: LTE
- 2016A&A...587A..92M: Partition function corrections for conformers and vibrational states
- 2016ApJ...833...41Z: LTE (found not to hold)
- 2020A&A...641A.104A: LTE, optically thin lines, beam filling factor of unity
- 2014ApJ...791..123W: LTE and optically thin lines
- 2018ApJ...856..147O: LTE, optically thin CH3OH; filling factor unity
- 2016ApJ...818..156C: Vertically isothermal, radial power-law temperature, hydrostatic equilibrium, Keplerian rotation, LTE
- 2025A&A...695A.236L: Isothermal LTE
- 2019A&A...627A...1Q: LTE, optically thin emission
- 2017PASJ...69...18T: [H2]/[13CO]=5.0e5, Tex=8.5 K, beta=1
- 2023ApJ...956L..35Z: Tex 30 K, H2/CO 1e4, 120 km/s range
- 2013ApJ...774L...7M: Tex=100 K, mu=2.72 mH, [H13CO+/H2]=3.3e-11
- 2017ApJ...834..178Y: Free-fall infall, constant angular momentum, LTE
- 2016ApJ...823L..18H: LTE; Keplerian velocities; ISM isotopologue ratios 69 and 557; T_atm,10=150 K, q_atm=0.5; C18O traces CO column
- 2024BAAA...65..173M: Optically thin lines, LTE
- 2016A&A...595A..87M: LTE
- 2016MNRAS.459.3629I: LTE, uniform density and temperature clouds, stimulated emission by non-thermal background neglected
- 2020ApJ...904..158L: LTE; 28SiO v=1 optically thick; same Tex for 28SiO and 29SiO
- 2013ApJ...775L..31S: LTE, optically thin
- 2017ApJ...843...27L: Optically thin; same Tex (165 K) for methanol and CH3SH
- 2017ApJ...839...43O: LTE justified by densities above 1e6 cm-3
- 2026ApJ..1003...68Y: LTE; [H2]/[13CO] = 3.2e6
- 2018A&A...619A.140V: T = 300 K, line width 1 km/s
- 2018ApJ...867...48I: Tex=30 K, tau<~1
- 2023ApJ...956L..16T: LTE, T = 25 K, [H2]/[C18O] = 5.9e6, ring thickness ~1,000 au (or 100 au)
- 2014ApJ...793...37A: Tex = 30 K, X_HCO+ ~ 1e-9
- 2019MNRAS.486.4114R: Dust-to-gas ratio fixed at 0.01 in simulations
- 2017ApJ...851..132C: vertically isothermal; abundance ratios H2/gas=0.8, H/H2=2, 12CO/H=7.5e-5, 12CO/13CO=69, 12CO/C18O=557; LTE
- 2025A&A...699A.369V: [H2/13CO]=1.8e6; beam filling factor ~1; TBG=2.73 K
- 2018ApJ...867..165B: PDR emission, optically thick gas
- 2018MNRAS.475.5322S: Optically thin, LTE
- 2019A&A...629A..75B: HCO+/H13CO+ = 12C/13C = 69; CO/H = 1.4e-4 above 20 K; gas-to-dust 100; LTE
- 2025A&A...695A.149K: 12C/13C = 50; beam filling factor of unity; 13CN optically thin
- 2016A&A...595L...7D: LTE, Tex >> T_CMB, alpha_CO=4.6 for thick gas with F21/F10=4, Galactic CO/H2 abundance for thin gas
- 2018MNRAS.478.2505I: Gas-to-dust mass ratio 100; dust opacity kappa=0.5 (nu/220 GHz)^1.7 cm2/g; LTE
- 2018MNRAS.478.2505I: LTE justified by n_crit ~1e7 cm-3
- 2016ApJ...823L..10W: LTE; Kama et al. disk structure
- 2025ApJ...985..225L: CO only in emission; H2-derived extinction used to de-redden
- 2016A&A...590A..93M: Same source size and temperature as more abundant isotopologues
- 2016ApJ...825...44I: 12C/13C ~50 in starbursts, ~100 in ULIRGs
- 2020ApJ...899L..10F: Inclination 30 and 70 deg; Tex = 20 K; [12CO/H2] = 1e-4; LTE
- 2018A&A...620L...6T: LTE; source size 3"; uniform line width and velocity
- 2018ApJ...856..117F: Mdisk=0.05 Msun, CO/H2=1e-6, M*=0.7 Msun, d=54 pc, CO freeze-out at 19 K
- 2017A&A...602A..49H: equal [CII] and CO filling factors; Tex,CO = dust temperature
- 2018A&A...620A.170J: LTE justified by n_H2 ≳ 1e10 cm^-3
- 2017ApJ...846L..26W: Flared LTE vertically isothermal Keplerian disk; X_CO=1e-4; mu=2.37; inner radius 0.1 au; distance 140 pc with 20 pc uncertainty added in quadrature
- 2025NatAs...9.1833L: Gas temperature approximates dust temperature
- 2018PASJ...70L...1M: Tex = Trot 18 K (CND), 12 K (ring)
- 2019ApJ...886....6T: Optically thin, lines from same physical structure; mean molecular weight 2.8
- 2018ApJ...852..122H: LTE; thin Keplerian disk; inclination 5 deg, PA 152 deg; mu=2.37; CO freezeout step function p=1e-6 below Tfrz
- 2026ApJ..1001L...1T: Ring density between compact condensations and cold envelope; CO freeze-out below ~20 K
- 2019A&A...622A.206M: LTE; transitions with optical depth < 0.5
- 2019MNRAS.485..739M: ISM C18O abundance, no isotope-selective photodissociation or freeze-out
- 2019A&A...623A..96Y: LTE; same Tex for both transitions; 13CO/C18O abundance ratio 5.5-10
- 2017NatAs...1E.130Z: HD and 13C18O abundance constant in warm region (T>20 K)
- 2018A&A...617A.120M: ortho/para ratio of 3 for c-C3H2; molecular data from LAMDA
- 2017A&A...606A.125S: Tgas = Tdust; N2H+ and HCN rate coefficients used for N2D+ and DCN
- 2017ApJ...837..174O: Dust temperature 100 K (70-130 K), gas temp equals dust temp
- 2019NatAs...3.1109P: Dust mix 60% silicate, 15% amorphous carbon, hollow spheres (max void 0.8), dn/da ~ a^-3.5, dust-to-gas 1/100
- 2017A&A...603A..10B: LTE, isothermal homogeneous
- 2019ApJ...883...98Z: Initial CO abundance 1.4e-4 relative to H; CO/C18O=570, CO/13CO=69; no isotopologue fractionation
- 2017A&A...606L...7B: LTE and optically thin lines
- 2018A&A...614A.106C: Optically thin, LTE, gas mass primarily H2
- 2019ApJ...871..100H: X_CO=5e-4, X_CO/X_C18O=560, T0=70 K, T ∝ r^-0.4
- 2019ApJ...871....5T: Gas-to-dust mass ratio 100; CO abundance 1e-4; HCO+ 1e-9; turbulence 120 m/s; LTE
- 2017ApJ...847..108W: optically thin, LTE
- 2017ApJ...847..108W: kappa=0.0182 cm2/g, gas-to-dust ratio 100, dust T 100 and 300 K
- 2016MNRAS.461..385B: LTE; [C18O]/[CO]=[18O]/[16O]; CO/H2~1e-4; gas and dust thermally coupled
- 2018A&A...612A..72J: Gas and dust temperatures coupled; Keplerian rotation (PP-disk), Terebey et al. velocities (toroid), free-fall elsewhere; LIME model radius 2000 AU
- 2018A&A...614A.123P: LTE valid as critical density ~1e6 cm-3 versus 4e7-5e8 cm-3
- 2019ApJ...876L..13S: Optically thin emission, LTE
- 2019ApJ...872..200H: optically thin emission
- 2018ApJ...863L..35M: Single Tex because high density (n_H>1e6 cm-3)
- 2018A&A...615L..10M: same excitation temperature; optical depth ratio 77
- 2019ApJ...875...62Y: common Tex among isotopologues; 12CO(2-1) heavily optically thick; LTE
- 2016ApJ...823...91S: LTE, emission fills beam
- 2016MNRAS.460..627K: Optically thin CO, T=50 K, CO abundance 1e-4, distance 140 pc
- 2019ApJ...887..209A: T=20 K for Groups 1 and 3, 10 K for Group 2; SMM4A excluded
- 2019ApJ...886...14F: 13CO/H2 = 3.1e-7 (12CO/H2 = 1.6e-5, 12CO/13CO = 50)
- 2017MNRAS.467L.120M: LTE, optically thin
- 2019PASJ...71...44H: distance 50 kpc; 12CO/H2=1.6e-5; 12CO/13CO=50
- 2016A&A...587A.145B: Tex = 100 K, CO/H2 = 1e-4, inclination 20 deg
- 2017ApJ...837...60B: X_CO = 1e-4 n(H2), 1.2" streamer depth, kinetic temperature 200 K, background 10 or 100 K
- 2016ApJ...831...32N: 12CO optically thick; 13CO same Tex as 12CO; LTE; H2/13CO = 5e6
- 2018A&A...615A..83V: LTE, Tex 10-50 K
- 2018ApJ...866..141K: inclination i = 45 deg; tau ~10 for wing
- 2016ApJ...824...88O: Tex 100 K (envelope), 130 K (CB), 100 K (disk); CH3OH optically thin
- 2019ApJ...886...15T: LTE
- 2018ApJ...856...14L: SO Tex 200-300 K in jet, ~100 K in shell
- 2017ApJ...849...68S: LTE ortho/para ratio of 1
- 2017ApJ...835..108S: 13CO/H2 = 3.2e-7
- 2016ApJ...821...94K: LTE
- 2019ApJ...886L...4Z: N(He+)/N(H+)=0.08, Te=1e4 K
- 2017ApJ...850L...2A: Tgas = Tdust = 20-50 K
- 2018ApJ...868...80C: kappa = 0.005 cm2/g, Tdust = 27 K, N2H+ Tex = 15 K, 18O/17O = 3.65


### Limitations the authors admit
- 2016A&A...587A..91B: Uniform single-component LTE model cannot fit very optically thick lines; formal temperature errors unreliable
- 2018ApJ...864..170G: o/p is a disk-averaged value; vertical distributions cannot be distinguished by SMA data
- 2024A&A...682A..74F: Single PN transition so Tex unconstrained; blending of SiS, PO, 29SiO lines in region 1; PO only tentative
- 2019A&A...628A..10B: Line-continuum splitting is preliminary with unexplained baseline artifacts
- 2017A&A...608A..38O: Separation of outflowing and regular gas is uncertain, so masses are likely lower limits
- 2017A&A...608A..38O: Single-component model not appropriate for mixed gas; Tkin-n degeneracy
- 2020A&A...636A..67A: H2CO opacity may cause the differences in distribution and kinematics
- 2015A&A...581A..85P: Resolution too low to fully resolve the disk; edge-on view unfavourable
- 2015A&A...581A..85P: Mass loss rate is a lower limit and uncertain by factor ~3; SO data cannot constrain density and temperature
- 2025ApJS..276...49J: Fixed beam-filling factor makes column densities likely lower limits (factor ~2-3)
- 2025ApJS..276...49J: ~20% of lines unidentified
- 2018A&A...620A..75K: Spherical model gives reduced chi2 ~4.0; a non-spherical model is needed
- 2018A&A...620A..75K: Beam-shift effect in ZIMPOL data not corrected; Clump γ polarization likely overestimated
- 2016MNRAS.460.2933M: Dust mass depends strongly on assumed composition and amax; h not fully constrained
- 2020ApJ...890..142P: Non-uniform initial calibration across the sample
- 2020ApJ...890..142P: Model-based snowline estimates are very uncertain
- 2019A&A...623A..68T: Field of view limited by background continuum and finite resolution; ACA combination would help
- 2019A&A...623A..68T: PDF width likely underestimated due to limited field of view
- 2015ApJ...798...85P: Gas mass is a crude estimate, dominated by assumed isotopic ratios and temperature
- 2026A&A...707A.120H: Did not recover high temperatures (>100 K) at the cloud edge; limited angular resolution and sensitivity
- 2026A&A...707A.120H: Uncertainties exclude systematics from fixed parameters
- 2021A&A...656A..46M: Calibration uncertainty not included in fit uncertainties; line flux scaling anomalies in some tunings
- 2021A&A...656A..46M: STATCONT continuum subtraction not optimal for lines near noise level
- 2020MNRAS.492.1180R: Resolution too low to resolve cavity wall layers; speculative conclusions
- 2024A&A...689A..64B: CS results poorly constrained, source size fixed at 1.6"
- 2024A&A...689A..64B: Comparing GMC-scale NGC 253 with parsec scale Galactic regions
- 2014Sci...345.1584B: Preliminary LTE model not fully optimized for ALMA; abundance uncertainties exclude free-free contamination and dust property uncertainties
- 2020MNRAS.497.2811K: Dust masses have large systematic uncertainties from arbitrary composition; HD 129590 gas unconstrained by MCMC
- 2019ApJ...870L..26C: Ad-hoc use of phase calibrator scans for sky subtraction leaves standing waves and sky lines and high noise
- 2015ApJ...803...60S: alpha_CO very uncertain and held constant
- 2015ApJ...803...60S: Missing flux for some lines
- 2015RAA....15.2213A: Imperfect deconvolution/calibration and crude symmetry and optically thin assumptions
- 2017ApJ...848..101V: Mass traced is only a fraction of total; LTE and abundance assumptions are simplistic
- 2020A&A...644A..59K: Errors underestimated; isothermal assumption fails in center; SO2 fits unsatisfactory
- 2020A&A...644A..59K: Beam filling factors set to 1; no collisions with e- and H
- 2020ApJ...900..131L: SFR from [O I] unreliable; relations have large uncertainties and are extrapolated; dust opacity and XDR contribution may bias metallicity and [N II] results
- 2020ApJ...888L..28S: Width comparable to beam, so the actual width may be narrower
- 2020ApJ...888L..28S: Only relative brightness temperatures because single-dish data not combined
- 2025ApJ...986L..22R: Two-component model is a simplification of the dual-jet geometry; March 17 S/N lower
- 2017A&A...605A..78A: 100 GHz results 30-55'' from the limb may be affected by the 60'' beam
- 2026A&A...705A.198M: Optically thick masses are lower limits; inner radii are upper limits; degeneracy thick/thin needs radiative transfer
- 2019ApJ...883..193N: Missing flux from lack of short baselines, so masses are lower limits
- 2019ApJ...883..193N: Residual is not a true chi2 because neighbouring pixels are correlated; modelling assumptions simple
- 2015ApJ...798..124R: Data cannot distinguish between gap and double power-law forms; dust opacity degenerate with surface density
- 2025A&A...696A.100G: Exact chemical pathways and relative contributions of bottom-up and top-down processes remain unquantified; models omit PAH chemistry
- 2024A&A...689A.317G: In-falling component size is not conclusive
- 2024ApJ...962....1S: Mass outflow rate uncertainty dominated by poorly constrained OH abundance
- 2024ApJ...962....1S: Almost no line-free channels in USB; simple fitting assumptions
- 2020ApJ...894...76W: gamma Vir models lack constraints at other wavelengths; temperature minimum cannot be analyzed
- 2020ApJ...894...76W: Variability at longer timescales cannot be ruled out for gamma Lep
- 2024ApJ...977..251H: Systematic uncertainties in X_CI, alpha_CO, r41, dust parameters
- 2018ApJ...866L..12G: Deblending of HNC/CN depends strongly on redshift; outflow rate cannot be estimated; limited tracers
- 2021ApJ...908..163M: Q10 cannot be constrained without other line ratios; the tentative line is not confirmed in Data1.
- 2020ApJ...890..167T: A single source of ~1e4 Msun cannot explain T2 and T3 kinematics; diffuse mass distribution possible
- 2016ApJ...832..158Z: Specific angular momentum is only an upper limit; envelope model is over-simplified; CO depletion neglected
- 2018ApJ...864..133T: Beam smear not corrected, affecting inner 90-100 au
- 2018ApJ...864..133T: Neighbouring annuli are correlated within a beam
- 2025A&A...699A.382M: Field of view truncates the outflow; velocity resolution comparable to gradients; expansion velocity poorly constrained
- 2018ApJ...853L..19S: Dust emissivity uncertain; coagulation on small scales could lower N(H2) and raise abundances
- 2017A&A...602A..42K: 22 GHz line uncertain due to NH3 contamination; same dilution factor assumed for all lines
- 2020ApJ...898...54T: Low velocity resolution (3 km/s) hindered line identification and Gaussian fitting; CH3CN optical thickness cannot be ruled out
- 2014ApJ...787..112C: LTE, no radiative pumping, constant source size assumed; some species optically thick
- 2025A&A...693A.101T: Radial extent unresolved; beam dilution underestimates column densities
- 2025A&A...693A.101T: Continuum oversubtraction/blocking may reduce line flux
- 2018A&A...615A..28D: Dust masses and dust-to-gas ratios uncertain by about a factor of 5
- 2018A&A...615A..28D: Extended emission may be resolved out
- 2017ApJ...839...86H: Grid search does not characterize uncertainties on CO parameters
- 2020ApJ...898...97B: C18O optical depth is a major uncertainty; rare isotopologue needed
- 2020ApJ...898...97B: Small sample: two Class 0 and three Class I sources
- 2020ApJ...898...97B: Resolution too low to identify Keplerian disks
- 2019MNRAS.485.2457H: Coarse spectral resolution (3.4 km/s) may overestimate dispersions and Mach number; Mach number is an upper bound
- 2019MNRAS.485.2457H: Cloud line-of-sight extent unknown; PPV not equivalent to physical space
- 2013ApJ...774...16R: Models are degenerate, not unique or optimal; systematic residuals at large radii
- 2013ApJ...774...16R: Band 7 sky frequency in SV measurement set incorrect
- 2024IJAsB..23...14M: Hyperfine lines unresolved and source not spatially resolved
- 2020ApJ...898...75I: Dominance of H2 in the CND is assumed; HI/HII may contribute
- 2020ApJ...898...75I: RADEX assumes single homogeneous medium though real structure is complex; single transition limits Tex
- 2020A&A...644A..84M: Tex-Ntot degeneracy for AA gives a factor ~2 uncertainty on Ntot
- 2020A&A...644A..84M: Some MF transitions under-reproduced; unidentified blends possible
- 2025A&A...696A..31G: Gas temperatures poorly constrained by HCNH+; large-scale emission filtered; beam dilution neglected
- 2015A&A...582L...1T: Detection of tEME is tentative; many lines blended
- 2020ApJ...892...99C: Temperature poorly constrained by the data
- 2020ApJ...892...99C: Calibration uncertainty not included in MCMC fit
- 2017Icar..286..289L: Lower mesosphere and stratopause temperatures are more uncertain, and the HCN vertical distribution is not unique given moderate optical thickness
- 2017Icar..286..289L: Spatial resolution insufficient to resolve surface
- 2015ApJ...801...63M: Error maps too optimistic; negative bowl from missing short spacings; region 6 fluxes highly uncertain due to absorption
- 2013A&A...557L..11B: Model is preliminary, LTE only, symmetric, and applied to 12CO 3-2 only
- 2019MNRAS.485..229R: Mass may differ by up to an order of magnitude due to X-factor and F_ul uncertainty
- 2019MNRAS.485..229R: Filling factor of 1 gives lower limit on tau; velocities are only apparent line-of-sight motions
- 2020A&A...633A..13D: Model not formally fit; chosen by eye
- 2020A&A...633A..13D: Mass-loss rate is a lower limit as optical depth is about unity
- 2020ApJ...898...61I: Absolute Sigma_mol depends critically on alpha_CO, and inclination is unknown
- 2020ApJ...898...61I: Modest S/N prevents line profile/outflow analysis
- 2021A&A...656A..68E: Best-case scenario without noise, atmosphere, imaging artifacts; static slightly eccentric beam; correction factors not for one-to-one correction
- 2025NatAs...9.1476C: HDO and H2O observed ~2 weeks apart; Q(H2O) inferred via CH3OH proxy
- 2025NatAs...9.1476C: Low S/N of HDO leaves L_p unconstrained for 50% distributed case
- 2017ApJ...850...35L: Side lobes may affect 1.3 mm umbral brightness, which should be treated as an upper limit
- 2026A&A...705A.204J: Dynamical model omits collisions, gas evolution, dust feedback and assumes Gaussian gas profile
- 2018A&A...614A..42M: Only CO(2-1) available; cannot constrain temperature, pressure, heating
- 2015MNRAS.447.3936M: Detailed chemical modelling beyond scope; T_k assumed uniform; vibrational/electronic states neglected
- 2018A&A...615A.141B: Dust optically thick so N_H2 and mass are lower limits
- 2018A&A...615A.141B: Interferometer filters out extended emission
- 2019NatAs...3..314L: XCLASS fit is imperfect; CH3OH lines likely optically thick, requiring 2-D modelling postponed
- 2025A&A...693A..76C: Disk model is a toy proof of concept; H2CO method unreliable near the star
- 2018A&A...619A..28L: Comparison with single-dish Sgr B2/Orion data may reflect beam dilution rather than chemistry
- 2019A&A...624A.125M: Fractionation not constrained; source size and Tex assumed; 13CO moderately optically thick; missing short spacings
- 2020MNRAS.497.5454I: Radio components may be knots of a single jet so member count may be lower
- 2015ApJ...813L..19J: Gaussian fit underestimates the actual disk size
- 2024AJ....167...66Y: Emission only marginally resolved; midplane assumption; CH2DOH spectroscopy uncertain by ~factor 3
- 2017A&A...598A..53D: Inhomogeneous data not aimed at AlO; low sensitivity; LTE optically thin assumption likely invalid
- 2016ApJ...829....6W: CO mass assumes optically thin LTE and could be larger by a factor of a few or more
- 2016ApJ...829....6W: Debris mass depends strongly on assumed size distribution, density, albedo
- 2020A&A...644A.119P: Column densities may be underestimated by a factor of a few if lines are mildly optically thick
- 2020A&A...644A.119P: Unsharp-masked ring morphology is uncertain due to the technique's arbitrariness
- 2020A&A...644A.119P: Excitation temperature must be assumed since only one line per species
- 2017ApJ...842...94T: Orbital parameters of the Bar cannot be derived accurately from the PV diagram
- 2013A&A...555A..73K: Band 7 data heavily spatially filtered, redshifted wind not detected, wind age may be underestimated
- 2024A&A...686A..59N: Single/limited lines for some species; coarse spectral resolution; low angular resolution; upper limits depend on assumed Tex and lines covered
- 2020A&A...643A..89P: Inner outflow fluxes uncertain due to broad nuclear profile; CO(4–3) excess unexplained
- 2020MNRAS.498L..87B: Emission unresolved; cannot distinguish envelope from disk; S hot corino needs higher resolution

### Settings cards flag as needed but not stated
- casa version: 29
- continuum subtraction and line-free channels: 23
- line-free channels and continuum subtraction method: 19
- self-calibration solution intervals and number of iterations: 15
- line-free channels used for continuum subtraction: 15
- line-free channels for continuum subtraction: 15
- image size and cell size: 14
- self-calibration solution intervals: 14
- flux scale uncertainty: 13
- line-free channels used for continuum: 9
- primary beam correction details: 9
- continuum subtraction method and line-free channels: 9
- flux calibrator and flux scale uncertainty: 8
- line-free channel ranges for continuum: 8
- casa version and pipeline version: 7
- flux calibration uncertainty: 7
- line-free channels and continuum subtraction: 6
- source coordinates: 5
- line-free channels for uvcontsub: 5
- line-free channel ranges: 5
- line-free channel ranges for continuum subtraction: 5
- line-free channels and continuum subtraction details: 4
- primary-beam correction details: 4
- pipeline version: 4
- line-free channel ranges for uvcontsub: 4
- self-calibration solution intervals and reference antenna: 4
- clean threshold, masks, cell and image size: 4
- casa version and whether the pipeline or manual calibration was used: 4
- line-free channels and uvcontsub fit order: 4
- self-calibration solution intervals and number of rounds: 4
- primary beam correction: 3
- line-free channels used for uvcontsub: 3
- flux, bandpass and phase calibrators and flux scale uncertainty: 3
- self-calibration status: 3
- cell size and image size: 3
- casa version and calibration/pipeline details: 3
- continuum-subtraction and line-free channels: 3
- line-free channels for continuum: 3
- whether pipeline or manual calibration was used: 3
- casa version and calibration procedure: 3

## Paper excerpts (40 of 375, chosen for detail and spread over fields/years)

### 2016A&A...587A..91B: Exploring molecular complexity with ALMA (EMoCA): Deuterated complex organic molecules in Sagittarius B2(N2) (2016; star_formation, astrochemistry, milky_way_ism; observational_alma_primary)
- question: Which deuterated complex organic molecules are detectable toward the hot core Sgr B2(N2), what are their deuteration levels, and how do they compare with astrochemical models and Orion KL?
- step 2: Population diagrams for rotational temperature
  - method: Linear fit to optical-depth- and contamination-corrected population diagrams of well-detected lines [3 Radiative transfer modeling: "Each population diagram was also corrected for optical depth following the method described in (cite: Goldsmith99), using the opacities delivered by Weeds."]
  - software: Weeds
  - fitting: Linear fit; formal errors viewed with caution [3 Radiative transfer modeling: "we believe that the formal errors on the rotational temperature derived from the fit to the population diagrams do not necessarily represent the true errors"]
  - validation: Population diagram used to verify manually derived temperature [3 Radiative transfer modeling: "The population diagrams were used to verify that the rotational temperature derived in the course of the (manual) modeling with Weeds made sense."]
- step 3: LTE modeling of full spectrum
  - method: Per-species synthetic LTE spectra with size, N, T, velocity offset and FWHM; four parameters optimized by eye; summed linearly into full model [3 Radiative transfer modeling: "The other four parameters were optimized by eye."]
  - software: Weeds
  - assumption: LTE, uniform physical structure, Gaussian source; deuterated species share parameters of main isotopologue [3 Radiative transfer modeling: "The physical structure of the source assumed for the modeling is uniform."]
  - fitting: Manual by-eye [3 Radiative transfer modeling of the li…: "The other four parameters were optimized by eye."]
  - validation: Detected if frequency, peak intensity and width are reproduced and line not contaminated [3 Radiative transfer modeling: "We emphasize that our definition of a “detected” line is very conservative"]
- step 4: Deuteration levels and upper limits
  - method: Column density of deuterated species from the main-species LTE model parameters; ratio XD/XH [5 Results: "This model is then used to obtain constraints on the column density of the deuterated species."]
  - software: Weeds
  - assumption: 12C/13C used to derive main species N from 13C isotopologues; statistical 2:1 distribution for out-of-plane/in-plane conformers [4 Spectroscopic predictions: "we assumed a statistical distribution (2:1) to compute and report individual column densities"]
  - validation: Compared with astrochemical models T14, A12 and Orion KL [abstract: "The results are compared to predictions of two astrochemical models that treat the deuteration process."]
- result: CH2DCN deuteration level = 0.4 ± not stated % [6.1.1: "we derive a deuterium fractionation of $0.4\%$ for this molecule"]
- result: CH2DOH deuteration = 0.12 ± not stated % [6.1.3: "The deuterium fractionation we derive for this isotopologue is 0.12%"]
- result: CH3OD deuteration upper limit = <0.07 ± not stated % [7 Conclusions: "CH$_3$OD ($<0.07\%$)"]
- result: DC3N deuteration = 0.09 ± not stated % [6.1.4: "We obtain a deuterium fractionation of 0.09%"]
- result: [CH2DOH]/[CH3OD] = >1.8 ± not stated dimensionless [6.3: "leads to \[CH$_2$DOH\]/\[CH$_3$OD\] $> 1.8$"]
- result: CH2DCN rotational temperature (population diagram) = 136 ± 14 K [Table 1: "| CH$_2$DCN | $\varv=0$ | 136 (14) |"]
- result: C2H5CN rotational temperature (population diagram) = 137.3 ± 1.6 K [Table 1: "| C$_2$H$_5$CN | $\varv=0$ | 137.3 (1.6) |"]
- limitation (authors): Uniform single-component LTE model cannot fit very optically thick lines; formal temperature errors unreliable [5.2: "Here again, a more complex model with a non-uniform physical structure would be necessary to fit all transitions in a consistent way."]
- not stated (card): Exact line-free channel ranges per spectral window; Self-calibration solution intervals and the line used; Clean thresholds, masks, image size; Integration frequency boundaries for each line; Full list of identified transitions (stated as not available); Tolerances for by-eye LTE parameter optimization; Velocity of source systemic velocity assumed

### 2018ApJ...864..170G: H<SUB>2</SUB>CO Ortho-to-para Ratio in the Protoplanetary Disk HD 163296 (2018; protoplanetary_disks, astrochemistry; observational_alma_primary)
- question: What is the disk-averaged H2CO ortho-to-para ratio in the HD 163296 disk, and what does it say about H2CO formation (gas-phase vs grain surface)?
- step 2: Measure disk-integrated fluxes and rotational temperature
  - method: Circular 6 arcsec mask fluxes; rotational diagram of three ortho lines [3.2: "Using the three ortho lines we constructed a rotational diagram"]
  - parameter: Flux error: std of 500 simulated flux measurements at random signal-free positions [3.2: "The uncertainty in the flux was estimated by taking the standard deviation of 500 simulated flux measurements from regions free of signal"]
  - assumption: Emission thermalized (LTE) given densities >1e6 cm-3 [3.2: "we expect the bulk of the emission to be thermalized"]
  - validation: Compared with 24 K from Carney et al. 2017 [3.2: "This temperature is consistent with the temperature of 24 K derived by (cite: carney2017)"]
- step 3: Fit H2CO abundance structure to ALMA visibilities
  - method: Two-component parametric abundance (X1, X2, alpha free), RADMC-3D LTE models, vis-sample, MCMC, for three (z/r)_l [4.1: "We use a Bayesian approach to find the best fit of the model to the ALMA visibilities."]
  - software: RADMC-3D, vis-sample, emcee
  - parameter: Fixed R1=1 au, R2=80 au, Rout=600 au, (z/r)_u=0.5; (z/r)_l=0.15, 0.20, 0.25 [Table 3: "$R_1$ | 1 au"]
  - assumption: LTE; uniform o/p of 3 for total abundance [4.1: "are computed assuming a uniform o/p ratio of 3"]
  - fitting: emcee MCMC; likelihood from weighted real and imaginary visibility differences [4.1: "We then compute the weighted difference between model and observations, for the real and imaginary parts of the complex visibility, which gives the likelihood of the model."]
  - validation: Channel maps of data, model and residuals; third-component test [4.1: "Fig. [5] shows channel maps of the $\mathrm{H_2CO}$ line observed with ALMA (top row), together with the best fit model (middle row), and the residuals (bottom row)."]
- result: Rotational temperature from three ortho lines = 24 ± ±14 K [3.2: "We obtain a rotational temperature of $24\pm14$ K."]
- result: ALMA 290 GHz p-H2CO flux = 1.22 ± 0.05 Jy km/s [Table 2: "$1.22\pm 0.05$"]
- limitation (authors): o/p is a disk-averaged value; vertical distributions cannot be distinguished by SMA data [4.2: "However, we cannot rule out any of the vertical distribution choices based on the SMA data."]
- not stated (card): Line-free channels and continuum subtraction details; Self-calibration solution intervals and reference; Cleaning threshold, image size and cell size; MCMC priors, walkers and steps; Source coordinates; Gas-to-dust ratio, collisional rates and line broadening used in RADMC-3D; SMA calibration flux values and MIR steps; Dust/gas structure parameters from Qi et al. 2011 in detail

### 2024A&A...682A..74F: The GUAPOS project: G31.41+0.31 Unbiased ALMA sPectral Observational Survey. IV. Phosphorus-bearing molecules and their relation to shock tracers (2024; star_formation, astrochemistry; observational_alma_primary)
- question: Are P-bearing molecules (PN, PO) in the hot molecular core G31.41+0.31 associated with shock tracers (SiO, SO, SO2, SiS), and what does this say about P chemistry?
- step 1: Integrated intensity maps
  - method: Integrate PN, SiO and other lines over 85.7-105.8 km/s; compare morphology and pixel-by-pixel ratios [3.1.1 PN, PO and SiO: "map of PN $J=2-1$ (panel (a)) integrated in the velocity range with emission above $3\sigma$ rms, namely 85.7–105.8 km s$^{-1}$"]
  - software: madcuba
  - validation: Compared with SiO J=5-4 high resolution maps [3.1.1 PN, PO and SiO: "In panel (d) of Fig. [1](#fig:PN-integ) we show the maps of the high-velocity wings of the SiO $J=5-4$ line published in (cite: Beltran18)."]
- step 2: Extract spectra at regions 1, 2 and hot core
  - method: Spectra in brightness temperature from the two PN peaks and the 20 sigma 3 mm continuum contour [3.1.1 PN, PO and SiO: "We chose the 3 mm continuum contour at 20$\sigma$ rms to disentangle the emission of the hot core from that of the ultracompact Hii region"]
  - software: madcuba
- step 3: LTE fits for column densities and Tex
  - method: SLIM AUTOFIT of multiple transitions for SO, 34SO, SO2, SiS, SiO; free V, FWHM, Tex, Ntot, fixed filling beam [3.3.1 SO, 34SO, SO2, SiS, and SiO: "Through its AUTOFIT function, SLIM produces the synthetic spectrum that best matches the data assuming LTE."]
  - software: madcuba
  - assumption: Emission fills the beam (theta_S fixed) [3.3.1 SO, 34SO, SO2, SiS, and SiO: "we can safely assume that the emission fills the telescope beam"]
  - fitting: LTE AUTOFIT; some Tex fixed (34SO region 1 at 58 K) [3.3.1 SO, 34SO, SO2, SiS, and SiO: "For $^{34}$SO, in region "1" the fit converged leaving $V$, $FWHM$, and $N_{\rm tot}$ free, but we had to fix $T_{\rm ex}$. The best-fit $T_{\rm ex}$ obtained by visual inspection is 58 K."]
- step 4: PN and PO column densities
  - method: Fit PN at Tex range from other tracers (26-75 K region 1, 12-30 K region 2); PO fitted with PN Tex, FWHM, V; upper limit in region 1 [3.3.2 PN and PO: "we derive the best-fit in a range of $T_{\rm ex}$ based on the minimum and maximum values obtained from the other tracers."]
  - software: madcuba
  - fitting: LTE [3.2.2 Tentative detection of PO: "We used madcuba to fit simultaneously the four transitions. The fitting method, which assumes local thermodynamic equilibrium (LTE) conditions"]
  - validation: Hyperfine-included fit gives consistent FWHM [3.3.2 PN and PO: "derived in all cases FWHMs slightly smaller but consistent within the errors with the values obtained neglecting it."]
- step 5: Opacity check
  - method: Compare madcuba tau with isotopologue intensity ratios (28SiO/29SiO, 32SO/34SO) [3.3.3 Opacity of SiO and SO lines: "the intensity ratio between the $^{28}$SiO and the $^{29}$SiO lines is $^{28}$SiO/$^{29}$SiO$\sim 8$ in region "1" and $^{28}$SiO/$^{29}$SiO$\sim 20$ in region "2"."]
  - software: madcuba
- result: PN Ntot region 1 (Tex=26 K) = 1.3e13 ± 0.1e13 cm^-2 [Table (fit-total): "| | PN | 9.7(0.9) | 94.8(0.4) | $1.3(0.1)\times 10^{13}$ | 26 | 0.01 |"]
- result: PN Ntot region 2 (Tex=12 K) = 1.5e13 ± 0.1e13 cm^-2 [Table 2: "| PN | 11.7(1.2) | 94.2(0.5) | $1.5(0.1)\times 10^{13}$ | 12 | 0.01 |"]
- result: SiO Ntot region 1 = 3.6e14 ± 0.1e14 cm^-2 [Table 2: "| SiO | 12.6(0.4) | 95.1(0.2) | $3.6(0.1)\times 10^{14}$ | 26.4(0.2) | 0.9 |"]
- result: SiO Ntot region 2 = 1.8e14 ± 0.2e14 cm^-2 [Table 2: "| SiO | 11.5(0.6) | 93.0(0.3) | $1.8(0.2)\times 10^{14}$ | 11.6(0.6) | 0.7 |"]
- result: PO/PN region 2 = ~0.6-0.9 ± not stated dimensionless [3.3.2 / 4.3: "the PO/PN ratio in region "2", where PO is tentatively detected, is $\sim 0.6-0.9$"]
- result: PO integrated-line S/N region 2 = ~6 ± not stated dimensionless [3.2.2 Tentative detection of PO: "we obtain a signal-to-noise ratio of $\sim 6$."]
- limitation (authors): Single PN transition so Tex unconstrained; blending of SiS, PO, 29SiO lines in region 1; PO only tentative [3.3.2 PN and PO: "For PN, we cannot derive $T_{\rm ex}$ from the data since we have only one transition."]
- not stated (card): Imaging parameters (weighting, robust, cell, image size, clean threshold); Continuum subtraction and line-free channels; Array configurations, baselines, time on source, observing dates; How the extraction regions 1 and 2 were defined (aperture size/shape); Role of project 2013.1.00489.S; Details of the Fig.1 moment-map procedure

### 2019A&A...628A..10B: Re-exploring Molecular Complexity with ALMA (ReMoCA): interstellar detection of urea (2019; astrochemistry, star_formation; observational_alma_primary)
- question: Is urea detected toward the hot cores of Sgr B2(N) in the ReMoCA ALMA survey, and how does its abundance compare with related COMs and chemical models?
- step 4: Model full spectrum and fit urea LTE emission
  - method: Weeds LTE synthetic spectra of all identified molecules, parameters optimized by visual inspection; urea at 160 K, size 2'', N=2.7e16 [4.4 Detection of urea: "The synthetic spectrum matches the ReMoCA spectrum relatively well, as evaluated by visual inspection"]
  - software: Weeds, CDMS-format predictions
  - parameter: source size 2''; Trot 160 K; Delta V 5.0 km/s [Table 3: "NH$_2$C(O)NH$_2$, $\varv=0$$^\star$ | d | 7 | 2.0 | 160 | 2.7 (16) | 1.86 | 5.0 | 0.0 | 1"]
  - assumption: LTE, source size 2'' for all species [4.3 Position selection: "We assumed a source size of 2$\ensuremath{''}$ for all species, which is more extended than the beam."]
  - fitting: Visual optimization, no sampler [4.4 Detection of urea: "the quality of this match is carefully evaluated by visual inspection of the spectra themselves which we use to optimize the model parameters."]
  - validation: Nine clearly detected lines; checked Halpha contamination [6.1 Astronomical detection: "We can thus safely conclude that at the high angular resolution of the ReMoCA survey and toward the specific position Sgr B2(N1S), the ReMoCA spectrum is not significantly contaminated by H$\alpha$ emission."]
- step 5: Population diagrams
  - method: Population diagrams corrected for opacity and contamination [4.4 Detection of urea: "yields a rotational temperature of $350 \pm 190$ K"]
  - assumption: Background continuum negligible (found invalid at this resolution) [4.4 Detection of urea: "requires the background continuum temperature to be negligible compared to the excitation temperature of the transitions."]
  - fitting: linear fit [4.4 Detection of urea: "This dependence on the background level affects the observed datapoints as well and cannot be accounted for by a simple linear fit to the population diagram."]
  - validation: considered unreliable for urea [4.4 Detection of urea: "this population diagram should be viewed with caution."]
- step 6: Derive N2 upper limit and compare N1S/N2
  - method: Used N2 model at 180 K, 0.9''; abundances relative to formamide [4.4 Detection of urea: "No sign of urea was found"]
  - software: Weeds
- result: Urea column density toward N1S = 2.7e16 ± not stated cm^-2 [Table 3: "NH$_2$C(O)NH$_2$, $\varv=0$$^\star$ | d | 7 | 2.0 | 160 | 2.7 (16)"]
- result: Urea rotational temperature from population diagram = 350 ± 190 K [4.4 Detection of urea: "yields a rotational temperature of $350 \pm 190$ K"]
- result: Urea column density upper limit toward N2 = <2.3e15 ± not stated cm^-2 [Table 4: "NH$_2$C(O)NH$_2$, $\varv=0$ | n | 0 | 0.9 | 180 | $<$ 2.3 (15)"]
- result: N-methylformamide column density toward N1S = 2.6e17 ± not stated cm^-2 [Table 3: "CH$_3$NHCHO, $\varv=0$$^\star$ | d | 38 | 2.0 | 160 | 2.6 (17)"]
- result: Formamide column density toward N1S = 2.9e18 ± not stated cm^-2 [Table 3: "NH$_2$CHO, $\varv=0$$^\star$ | d | 20 | 2.0 | 160 | 2.9 (18)"]
- result: Urea/formamide abundance ratio N1S = 0.0093 ± not stated dimensionless [4.7 Comparison of Sgr B2(N1S) and Sgr B…: "1 / 0.086 / 0.090 / 0.14 / 0.0093 for Sgr B2(N1S)"]
- result: Formamide rotational temperature = 159 ± 5 K [4.6 Other related molecules: "well-constrained rotational temperature of $159 \pm 5$ K"]
- result: 16O/18O ratio from formamide = 140 ± not stated dimensionless [4.6 Other related molecules: "The $^{16}$O/$^{18}$O ratio of 140"]
- result: 14N/15N ratio from formamide = 314 ± not stated dimensionless [4.6 Other related molecules: "The $^{14}$N/$^{15}$N ratio of 314"]
- limitation (authors): Line-continuum splitting is preliminary with unexplained baseline artifacts [2.2 Data reduction: "the splitting of the line and continuum emission performed so far is still preliminary and we plan to improve it in the future."]
- not stated (card): Pipeline/QA details and flux calibrator names and flux scale uncertainty; Which line was used for self-calibration in each setup; Exact channel masks for continuum determination; Clean thresholds, masks and iteration counts; Full list of molecules/parameters in the full Weeds model; Uncertainties on LTE column densities; Urea spectroscopic line list (Medvedev et al. in prep.); Details of the MAGI…

### 2017A&A...608A..38O: Properties of the molecular gas in the fast outflow in the Seyfert galaxy IC 5063 (2017; nearby_galaxies, agn_and_quasars; observational_alma_primary)
- question: What are the excitation, optical depth, mass, density, temperature and pressure of the molecular gas in the jet-driven fast outflow of IC 5063, from multiple CO and HCO+ transitions?
- step 3: Excitation temperature and outflow mass
  - method: LTE optically thin Tex from R32; sum flux of pixels with R32 > 1.0; convert with alpha_CO; Mdot = 3vM/R [5.2 Mass estimates: "adding the flux from all 3-D pixels in the CO(2-1) cube, and similarly in the CO(3-2) cube, for which $R_{32}$ $> 1.0$"]
  - parameter: R = 0.5 kpc, v = 300 km/s [5.2 Mass estimates: "Using $R \sim 0.5$ kpc and $v = 300$$\,$km$\,$s$^{-1}$"]
  - assumption: optically thin, LTE, alpha_CO = 0.25 at Tex 29 K, spherical outflow [5.2 Mass estimates: "This assumes that the outflow has a spherical geometry."]
  - validation: Compared flux integral with earlier papers' 10.0 and 12.3 Jy km/s [5.2 Mass estimates: "compares well with the values of 10.0 Jy $\,$km$\,$s$^{-1}$ and 12.3 Jy $\,$km$\,$s$^{-1}$"]
- step 4: Non-LTE RADEX modelling of Tkin, density, pressure
  - method: Single-slab RADEX grids in Tkin and nH2 compared to line ratios for four regions, for a range of CO column densities [5.3 Kinetic temperature, density and pr…: "we modelled the data using a single slab (1-D) model with constant kinetic temperature and density"]
  - software: RADEX
  - parameter: Tkin 10-200 K (log steps 0.043); nH2 1e2-1e7 cm-3 (log steps 0.167); N(12CO) 5e15-1e20 cm-2 (log step 0.5); line width 100 km/s; Tbg 2.73 K [5.3 Kinetic temperature, density and pr…: "We set the background temperature to 2.73 K and the line width to 100 $\,$km$\,$s$^{-1}$."]
  - assumption: 12CO/13CO = 100; HCO+/12CO = 1.3e-4 [5.3 Kinetic temperature, density and pr…: "For the ratio $^{12}$CO/$^{13}$CO we have assumed 100."]
  - fitting: Graphical comparison of tracks of line ratios in Tkin-n plane; no formal fit [5.3 Kinetic temperature, density and pr…: "The quality of models can be assessed by to what extent the different lines in the panels of Fig. [12](#fig:f_radex) intersect in a common region."]
  - validation: Varied 12CO/13CO between 50 and 200 and HCO+ abundance; similar results [5.3 Kinetic temperature, density and pr…: "varying this ratio between 50 and 200 gives similar results, within the errors."]
- result: Excitation temperature from mean R32 (LTE, thin) = 29 ± not stated K [5.1 Excitation temperatures: "indicates an excitation temperature of $T_{\rm ex}$ = 29 K"]
- result: Highest pixel R32 and corresponding Tex = R32 ~1.65; Tex = 54 K ± not stated K [5.1 Excitation temperatures: "Such values correspond to $T_{\rm ex}$ = 54 K assuming optically thin emission and LTE."]
- result: Outflow flux integrals (R32>1.0) = CO(2-1) 9.5; CO(3-2) 25.3 ± not stated Jy km/s [5.2 Mass estimates: "The flux integrals we find are 9.5 Jy $\,$km$\,$s$^{-1}$ for the CO(2-1) line and 25.3 Jy $\,$km$\,$s$^{-1}$ for the CO(3-2) line."]
- result: Molecular outflow mass = 1.3e6 (CO 2-1), 1.1e6 (CO 3-2) ± likely lower limit, factor of a few larger Msun [5.2 Mass estimates: "$1.3 \cdot 10^6$ $M_\odot$ based on the CO(2-1) flux integral and $1.1 \cdot 10^6$ $M_\odot$ from the CO(3-2) data"]
- result: Mass outflow rate = ~12 ± or somewhat higher Msun/yr [5.2 Mass estimates: "gives a gas mass outflow rate of the about $\sim$12 $M_\odot$ yr$^{-1}$ or somewhat higher"]
- result: Pressure in jet-affected regions = 10^6 - 10^7.5 ± not stated K cm^-3 [5.3 Kinetic temperature, density and pr…: "The resulting pressures are in the range $10^6$–$10^{7.5}$ K cm$^{-3}$."]
- limitation (authors): Separation of outflowing and regular gas is uncertain, so masses are likely lower limits [5.2 Mass estimates: "the main uncertainty in the mass estimate comes from the uncertainties in the separation of regular and anomalous gas"]
- limitation (authors): Single-component model not appropriate for mixed gas; Tkin-n degeneracy [5.3 Kinetic temperature, density and pr…: "there is a degeneracy between them in the models"]
- not stated (card): Self-calibration solution intervals and number of iterations; Number of CLEAN iterations and cleaning thresholds; Taper parameters for the low-resolution HCO+ and 13CO cubes; Exact definition of regions FO, O, L, D (polygons in position-velocity space) and how line ratios and errors were extracted; Rest frequencies used and continuum subtraction/line-free channels; Method of chi-square or matchin…

### 2020A&A...636A..67A: Exploring the formation pathways of formamide. Near young O-type stars (2020; star_formation, astrochemistry; archival_reuse)
- question: Is formamide (NH2CHO) chemically related to HNCO and/or H2CO, as tested by comparing moment maps and LTE-modelled abundances in three high-mass star-forming regions?
- step 1: Extract spectra and model with LTE
  - method: Extract spectra at NH2CHO peak pixels from continuum-subtracted images; fit NH2CHO, HNCO, H2CO and potential blenders (C2H5OH, CH3CN v8=1, CH3(18)OH) simultaneously in XCLASS [2.3 Line identification: "performing simultaneous fits of the species NH$_2$CHO, HNCO, H$_2$CO, and species that were potentially blended with NH$_2$CHO"]
  - software: CASA, XCLASS
  - parameter: Tex 50-300 K for HNCO and NH2CHO, 70-400 K for H2CO; FWHM and vLSR constrained by Gaussian fits, vLSR free within ±0.5 km/s [2.3 Line identification: "The $T_\mathrm{ex}$ free parameter was allowed to vary between 50 and 300 K for HNCO and NH$_2$CHO and between 70 and 400 K for H$_2$CO."]
  - assumption: LTE; H2CO modeled with source size ~0.15'' below beam [2.3 Line identification: "The temperature of H$_2$CO was modeled using higher temperatures and a source size smaller than the beam size ($\sim0.15''$)"]
  - assumption: N(H2) from continuum with Tdust=100 K, kappa=1.0 cm2/g, gas-to-dust 100 [Table 2 notes: "assuming a T$_{dust}$ of 100 K, a dust opacity of 1.0 cm$^2$ g$^{-1}$ (cite: Ossenkopf1994), and a gas-to-dust ratio of 100"]
  - fitting: XCLASS errorestim_ins MCMC for errors [3.4: "The errors shown were determined using the *errorestim$\_$ins* algorithm using the Markov chain Monte Carlo (MCMC) method built into the XCLASS software."]
  - validation: Blending checked with ethanol comparison line at 217803.69 MHz [2.3 Line identification: "the peak integrated emission of NH$_2$CHO (1) is $\sim$8 times stronger than that of C$_2$H$_5$OH"]
- step 4: Correlate abundances
  - method: Divide modeled Ncol by core N(H2); fit power laws between species pairs [3.4: "Modeled $N_\mathrm{col}$ values were divided by the H$_2$ column densities listed in Table [2](#spectrapoints) to obtain abundances for comparison"]
  - software: XCLASS
  - fitting: Power-law fits with R^2 [3.4: "The fit for NH$_2$CHO vs. HNCO is \[*X*(NH$_2$CHO)=0.06 *X*(HNCO)$^{0.95}$\] (R$^2$=0.93)."]
  - validation: Compared with Lopez-Sepulcre et al. 2015 relation [5.2 XCLASS analysis: "the relationship between the abundances of HNCO and NH$_2$CHO in this work is almost exactly the same as that reported in (cite: Ana2015)"]
- result: X(NH2CHO) vs X(HNCO) power-law fit = X(NH2CHO)=0.06 X(HNCO)^0.95 ± 0.06±0.03; exponent ±0.05 dimensionless [5.2 XCLASS analysis: "*X*(NH$_2$CHO)=0.06($\pm$0.03) *X*(HNCO)$^{0.95 (\pm0.05)}$"]
- result: X(NH2CHO) vs X(H2CO) fit = X(NH2CHO)=0.618 X(H2CO)^1.103, R^2=0.943 ± not stated dimensionless [3.4: "The fit for NH$_2$CHO vs. H$_2$CO is \[*X*(NH$_2$CHO)=0.618 *X*(H$_2$CO)$^{1.103}$\]"]
- result: X(HNCO) vs X(H2CO) fit = X(HNCO)=4.796 X(H2CO)^1.111, R^2=0.936 ± not stated dimensionless [3.4: "*X*(HNCO)=4.796 *X*(H$_2$CO)$^{1.111}$\] (R$^2$=0.936)"]
- result: Tex range of NH2CHO = 50-150 ± not stated K [3.4: "The $T_\mathrm{ex}$ range for NH$_2$CHO is 50-150 K"]
- limitation (authors): H2CO opacity may cause the differences in distribution and kinematics [5.1: "It is possible that the greater differences in spatial distribution, velocity, and dispersion between H$_2$CO and NH$_2$CHO compared to HNCO arise from optical depth issues."]
- not stated (card): Imaging parameters (robust, cell, image size, deconvolver, CLEAN threshold); CASA version; Moment map clipping thresholds and velocity ranges; XCLASS version, source sizes and MCMC settings; Beam-matching or smoothing before differencing moment maps; Line-free channels used for STATCONT

### 2015A&A...581A..85P: The jet and the disk of the HH 212 low-mass protostar imaged by ALMA: SO and SO<SUB>2</SUB> emission (2015; star_formation, astrochemistry; observational_alma_primary)
- question: What are the physical and dynamical properties of the molecular jet and the disk of HH 212, as traced by SO and SO2, and what are the SO and SO2 abundances?
- step 3: Constrain SO excitation and jet column density/abundance
  - method: RADEX grids compared to SO line ratio and intensities; then LTE optically thin N_SO and N_CO; X_SO = X_CO N_SO/N_CO [4.2 SO and SO2 abundance in the jet: "Then, the abundance of SO is derived as $X_{\rm SO} = X_{\rm CO} \times N_{\rm SO} / N_{\rm CO}$"]
  - software: RADEX
  - parameter: TK = Tex = 50-500 K; nH2 1e5-1e7 cm-3 [4.2 SO and SO2 abundance in the jet: "kinetic temperatures ($T_{\rm K} = 50 -500$ K) and H$_2$ densities ($n_{H_2}$ from $10^{5}$ to $10^{7}$ cm$^{-3}$)"]
  - assumption: X_CO = 1e-4; CO optically thin (lower limit in B2) [4.2 SO and SO2 abundance in the jet: "the abundance of CO with respect to H$_2$ is assumed to be $X_{\rm CO} = N_{\rm CO} / N_{\rm H_2} = 10^{-4}$"]
  - validation: RADEX with n=3e5 gives factor 2-4 higher columns [4.2 SO and SO2 abundance in the jet: "are from a factor 2 (for $T_{\rm K} = 500$ K) to a factor 4 (for $T_{\rm K} = 50$ K) larger than in the LTE-optically thin case"]
- step 5: Disk mass and SO abundance
  - method: RADEX for SO 10-10 and ratio; LTE optically thin SO and C17O columns over |V-Vsys|=1.9-3.5 km/s; disk mass from C17O over beam area, blue+red lobes [4.4 Disk properties: mass and SO abunda…: "$M_{\rm disk} \sim \left( 1.4 \times m_{\rm H_2} \times (N_{\rm C^{17}O} / X_{\rm C^{17}O}) \times A_{\rm beam} \right)_{\rm blue + red}$"]
  - software: RADEX
  - parameter: beam dilution factor ~8; R_disk ~90 AU [4.4 Disk properties: mass and SO abunda…: "strongly diluted in the $0.65\ensuremath{''} \times 0.47\ensuremath{''}$ beam (dilution factor $\sim 8$)"]
  - assumption: C17O/CO=1/1792, X_CO=1e-4, Tex 50-500 K, factor 1.4 for He [Table 2: "We assume optically thin emission at LTE with $T_{\rm ex} = 50-500$ K."]
  - validation: Compared with disk mass 0.014 Msun from HCO+ [4.4 Disk properties: mass and SO abunda…: "This value is close to the disk mass of $0.014$ M$_{\odot}$ estimated by (cite: lee14) from HCO$^{+}$ $4-3$."]
- result: SO abundance in jet = ~1e-7 to 2e-6 ± temperature range 50-500 K dimensionless [4.2 SO and SO2 abundance in the jet: "($X_{\rm SO} \sim 10^{-7}-2 \times 10^{-6}$)"]
- result: SO2/SO ratio in jet = ~0.5-4 ± not stated dimensionless [4.2 SO and SO2 abundance in the jet: "we find SO$_2$/SO$\sim 0.5-4$ in HH 212"]
- result: Disk mass = >=0.002-0.013 ± not stated Msun [4.4 Disk properties: mass and SO abunda…: "The disk mass turns out to be $\sim 0.002 - 0.013$ M$_{\odot}$."]
- result: SO abundance in disk = ~1e-8 to 1e-7 ± not stated dimensionless [4.4 Disk properties: mass and SO abunda…: "$X_{\rm SO} = X_{\rm C^{17}O} \times N_{\rm SO} / N_{\rm C^{17}O} \sim 10^{-8} - 10^{-7}$"]
- result: Fraction of sulfur in SO and SO2 in jet = 1% to 40% ± not stated percent [4.2 SO and SO2 abundance in the jet: "from 1% up to 40% of the elemental S is in the form of SO and SO$_2$ in the HH 212 jet"]
- limitation (authors): Resolution too low to fully resolve the disk; edge-on view unfavourable [4.4 Disk properties: "The angular resolution ($\sim 0.5\ensuremath{''}$) is too low to fully resolve the disk"]
- limitation (authors): Mass loss rate is a lower limit and uncertain by factor ~3; SO data cannot constrain density and temperature [4.2 SO and SO2 abundance in the jet: "the avalaible SO observations do not allow constraining the density and temperature of the emitting gas"]
- not stated (card): ALMA project code and archive MOUS/data location; CASA version and calibration script details; Imaging parameters (weighting, robust, cell, image size, deconvolver, masks); Continuum subtraction and line-free channels; Primary beam correction; Exact beam-dilution factor derivation and RADEX input grids/collision data files; Knot extraction aperture/position coordinates; Absolute flux scale uncert…

### 2025ApJS..276...49J: ALMA Spectral Survey of an Eruptive Young Star, V883 Ori (ASSAY). II. Freshly Sublimated Complex Organic Molecules in the Keplerian Disk (2025; protoplanetary_disks, astrochemistry, star_formation; observational_alma_primary)
- question: What is the COM inventory and composition of the freshly sublimated ices in the Keplerian disk of the eruptive star V883 Ori, and how does it compare with hot corinos, hot cores and comet 67P?
- step 2: Correct dust attenuation
  - method: Fit continuum vs spectral window weighted by PC1 moment 0 to get N_H2 and eta; divide line intensity by exp(-tau_dust) [3.1 Dust attenuation of line intensities: "To get $N_{\rm H_{2}}$ and $\eta$, we fitted the continuum intensities as a function of spectral windows, weighted by the moment 0 map of the PC1"]
  - parameter: SG2 and SG3 spectra scaled up by 5% and 2% [3.1 Dust attenuation of line intensities: "we scaled up the SG2 and SG3 spectra by 5% and 2%, respectively."]
  - assumption: Dust and gas coupled, gas in LTE; kappa=2.2 cm2/g at 230 GHz, beta=1 [3.1 Dust attenuation of line intensities: "We assume that dust and gas are well coupled and that the gas is in LTE."]
- step 3: Identify molecular lines
  - method: XCLASS model spectra for ~1500 species at 35 column density steps; f_N,X = matched/modeled lines; keep species reaching 100%, then visual inspection [3.2 Molecular line identification: "for every possible species (about 1,500), we constructed model spectra with 35 column density steps (from 5$\times$10$^{12}$ cm$^{-2}$ to 5$\times$10$^{18}$ cm$^{-2}$)."]
  - software: XCLASS, CDMS, JPL
  - parameter: v_width = 3 km/s, T_rot = 120 K, eta = 0.384, N free [3.2 Molecular line identification: "We fixed $v_{\rm width}$ at 3 km s$^{-1}$, which is obtained from the PC1-filtered spectrum."]
  - assumption: LTE [3.2 Molecular line identification: "Assuming local thermodynamic equilibrium (LTE), `XCLASS` can model the spectra of each molecular species"]
  - validation: Visual inspection of selected species [3.2 Molecular line identification: "Finally, we performed a visual inspection to confirm the detection of those molecules selected by this procedure."]
- step 4: Derive column densities by iterative LTE fitting
  - method: Fit N only with MAGIX, iteratively keeping isolated lines with tau<0.7 and width<4 km/s until convergence [4.1: "The optical depth criterion is set to $\tau_{\rm \nu,line}=0.7$, meaning that only lines with their modeled $\tau_{\rm \nu,line}$ lower than 0.7 are considered in the fitting process."]
  - software: XCLASS, MAGIX
  - parameter: tau criterion 0.7; exclude line width >4 km/s [4.1: "we removed observed lines with large line width ($>$ 4 km s$^{-1}$), which may be due to blending with unidentified lines."]
  - assumption: T_rot fixed 120 K, eta fixed 0.384 [4.1: "the column density ($N$) was the only free parameter in the analysis, while the other parameters were fixed to the aforementioned values."]
  - fitting: Genetic algorithm for best fit; MCMC for uncertainties [4.1: "The genetic algorithm was used to derive the best-fit values of the parameters, and the Markov chain Monte Carlo (MCMC) method was used to calculate the uncertainties."]
  - validation: Rotation diagram comparison: scatter 0.28 dex, offset 0.03 dex [4.1: "the difference in column densities obtained from the two methods has a scatter of 0.28 dex with only a slight offset of 0.03 dex."]
- result: Number of COM species detected = 23 ± not stated species [5.1: "a total of 23 complex organic molecular species have been found in V883 Ori, based on about 3,700 lines above 3$\sigma$."]
- result: Beam-filling factor eta = 0.384 ± not stated dimensionless [3.1 Dust attenuation of line intensities: "Finally, the fitted $\eta$ is 0.384, and the fitted $N_{\rm H_{2}}$ is $1.24\times10^{25}$ cm$^{-2}$ with uncertainty of 2$\%$."]
- result: N_H2 = 1.24e25 ± 2% cm^-2 [3.1 Dust attenuation of line intensities: "Finally, the fitted $\eta$ is 0.384, and the fitted $N_{\rm H_{2}}$ is $1.24\times10^{25}$ cm$^{-2}$ with uncertainty of 2$\%$."]
- result: CH3OH column density = 2.35e18 ± +0.65/-0.14 e18 cm^-2 [Table 1: "$2.35_{-0.14}^{+0.65}\times10^{18}$"]
- result: CH3OCHO column density = 1.05e18 ± +0.04/-0.17 e18 cm^-2 [Table 1: "$1.05_{-0.17}^{+0.04}\times10^{18}$"]
- limitation (authors): Fixed beam-filling factor makes column densities likely lower limits (factor ~2-3) [11: "the accurate beam-filling factors of less abundant molecules can increase the column densities by a factor of $\sim2-3$, so the current values can be considered lower limits."]
- limitation (authors): ~20% of lines unidentified [5.1: "Most observed lines have been identified, but $\sim$20$\%$ of the lines remain unidentified."]
- not stated (card): Imaging parameters (robust, cell, tclean settings, beam of final cubes) are deferred to Paper I; CASA/pipeline version and calibrators not stated; Which strong isolated lines were used to build the PC1; XCLASS version and MAGIX genetic algorithm/MCMC settings; Exact criteria for isolated lines and line-matching tolerance in f_N,X; Spectral extraction aperture details beyond ~0.3''

### 2018A&A...620A..75K: High-resolution observations of gas and dust around Mira using ALMA and SPHERE/ZIMPOL (2018; evolved_stars, astrochemistry; observational_alma_primary)
- question: Constrain the distribution of gas and the composition and properties of dust grains forming in the inner circumstellar environment of Mira (o Cet)
- step 4: Model CO v=1 J=3-2 line (gas density, temperature, velocity)
  - method: LTE radiative transfer in a spherical shell with power-law profiles; model images convolved with beam; spectra from 20, 50, 100 mas apertures; grid of ~2e4 models [4.3.1: "We calculated close to 2 × 10 [4] models spanning the ranges given in Table 2."]
  - parameter: R338=2.15 au, T*=2100 K, Rout=8.6 au [4.3.1: "The stellar radius and temperature were set to _R_ [338GHz] ⋆ = 2.15 au and _T_ ⋆ = 2100 K"]
  - assumption: CO abundance 4e-4 relative to H2; LTE; spherical symmetry; distance 102 pc [4.3.1: "We assume a CO abundance of 4 × 10 [−][4] relative to H 2 ."]
  - fitting: Initial by-eye search then grids minimizing chi2; 54 DF; reduced chi2 ~4.0 [4.3.1: "Our best fit reached a reduced-χ [2] = χ [2] /DF ∼ 4.0."]
  - validation: Compared to 13CO J=3-2 line with 12C/13C=10±3 [4.3.2: "We calculated models considering the best-fit models, within the uncertainties given in Table 2, and assuming a [12] C-to- [13] C ratio of 10 ± 3"]
- step 5: Derive TiO2 and AlO column densities and depletion
  - method: Rotational diagram of unblended TiO2 lines; LTE AlO column with TiO2 excitation temperature; divide by H2 column from CO model; compare to solar abundances [4.3.3: "From the rotational diagram shown in Fig. 7, we derive an excitation temperature of 580 ± 65 K and a column density of (2.7 ± 0.7) × 10 [16] cm [−][2] ."]
  - assumption: LTE; solar composition with fully molecular hydrogen (Asplund et al. 2009) [4.3.3: "for a gas with solar composition (Asplund et al. 2009) and in which hydrogen is fully molecular"]
  - validation: Compared with Kaminski et al. 2016, 2017 [4.3.3: "The column density we find is comparable to that reported by Kami´nski et al. (2016)"]
- result: Gas mass between R338 and 4R338 = 3.8e-4 ± ±1.3e-4 Msun [4.3.1: "We find a mass in the vibrationally-excited CO region of (3.8 ± 1.3) × 10 [−][4] _M_ ⊙ ."]
- result: Preferred mass including 13CO = ~2.5e-4 ± not stated Msun [4.3.2: "we conclude that the mass in the vibrationally-excited CO region is ∼ 2.5 × 10 [−][4] _M_ ⊙ ."]
- result: vLSR = 47.7 ± ±0.1 km/s [4.3.1: "We find υ LSR = 47.7 ± 0.1 km/s."]
- result: TiO2 excitation temperature = 580 ± ±65 K [4.3.3: "we derive an excitation temperature of 580 ± 65 K"]
- result: TiO2 column density = 2.7e16 ± ±0.7e16 cm-2 [4.3.3: "a column density of (2.7 ± 0.7) × 10 [16] cm [−][2]"]
- result: AlO column density = 7e15 ± ±2e15 cm-2 [4.3.3: "an AlO column density of (7±2)×10 [15] cm [−][2] is needed"]
- result: Fraction of Ti in TiO2 = ~4.5 ± not stated % [4.3.3: "the TiO 2 molecules account for ∼ 4.5% of the expected titanium and the AlO molecules account for < 0.1% of the expected aluminium."]
- limitation (authors): Spherical model gives reduced chi2 ~4.0; a non-spherical model is needed [4.3.1: "This shows that a more complex model (non-spherically symmetric) is required"]
- limitation (authors): Beam-shift effect in ZIMPOL data not corrected; Clump γ polarization likely overestimated [Beam-shift effect: "we do not attempt to improve the reduction."]
- not stated (card): Spatial image size and cell size, clean threshold, masks and deconvolver; Line-free channels used for continuum and self-calibration solution intervals; Model code for CO v=1 not released/named; power-law radiative transfer details unspecified; Sampling/grid steps for the model grid; Continuum subtraction method for lines; Aperture/integration velocity ranges for TiO2 fluxes; SZ package version a…

### 2016MNRAS.460.2933M: Exocometary gas in the HD 181327 debris ring (2016; debris_disks; observational_alma_primary)
- question: Where are the mm dust and CO gas located in the HD 181327 debris ring, and what is the origin and mass of the CO?
- step 4: Fit non-LTE CO model for gas mass
  - method: RADMC-3D non-LTE models in image space against natural-weighted dirty map; MCMC on MCO, r0, Δr over grid of Tk and electron density [3.2 12CO (2-1): "The free parameters in the MCMC are the CO gas mass (M$_\mathrm{CO}$), ring radius ($r_0$) and FWHM of the ring ($\Delta r$)."]
  - software: RADMC-3D
  - parameter: ne0 between 1e-2 and 1e7 cm-3; Tk half to twice dust temperature (50 K) [3.2 12CO (2-1): "We vary n$_{\mathrm{e}^{-}}^{0}$between 10$^{-2}$-$10^{7}$ cm$^{-3}$ to cover from the radiation-dominated regime to LTE."]
  - assumption: h=0.07 and orientation fixed to dust fit; Keplerian rotation; systemic velocity 0.1 km/s; electrons as collision partner [3.2 12CO (2-1): "with a fixed vertical aspect ratio $h$ of 0.07 and fixed disc orientation"]
  - fitting: MCMC, likelihood ∝ exp(-chi2/2) accounting for independent beams and channel correlation [3.2 12CO (2-1): "taking into account the number of independent beams in the image and the correlation between adjacent channels in ALMA data"]
  - validation: Model spectrum compared with half-disc spectra [3.2 12CO (2-1): "The model spectrum matches roughly the observed CO line profile."]
- result: CO mass (ne0=100 cm-3, Tgas=Tdust) = 1.8e-6 ± 0.6e-6 Mearth [3.2 12CO (2-1): "We find M$_\mathrm{CO}=1.8\pm0.6 \times10^{-6}$ M$_{\oplus}$"]
- result: CO ring radius = 81 ± +10/-9 AU [3.2 12CO (2-1): "$r_0=81^{+10}_{-9}$ AU"]
- limitation (authors): Dust mass depends strongly on assumed composition and amax; h not fully constrained [3.1 Dust continuum: "On the other hand the scale height is not fully constrained."]
- not stated (card): Briggs robust value; Line-free channels for continuum fit; uvmem regularization/hyperparameters and pixel size; uvmem and uvsim code availability; Priors' bounds for MCMC and number of walkers/steps; Pipeline CASA version; Mask/exact kernel for CO spectrum smoothing

### 2020ApJ...890..142P: An ALMA Survey of H<SUB>2</SUB>CO in Protoplanetary Disks (2020; protoplanetary_disks, astrochemistry; archival_reuse)
- question: What are the H2CO emission morphologies, excitation temperatures and column densities across 15 protoplanetary disks, and what do they imply about H2CO formation (gas-phase vs CO-ice hydrogenation)?
- step 3: Disk-averaged and azimuthally-averaged rotational diagrams
  - method: Opacity-corrected rotational diagram linear fit with iterative opacity correction for four disks with >=3 lines [4.3 Rotational Diagram Analysis: "we initially solve for the opacity-uncorrected $\overline{T_{ex}}$ and $\overline{N_{tot}}$ using a linear fit assuming $C_{\tau_{ul}}=1$, and then we correct the rotational diagram for the opacity using an iterative approach"]
  - software: Python, NumPy, SciPy
  - parameter: convergence when tau and Tex change at most 0.001% (5000 iterations max for LkCa 15) [4.3 Rotational Diagram Analysis: "at most 0.001% (or, in the case of the uncertain spike in excitation temperature for LkCa 15, until 5000 iterations have passed)"]
  - assumption: LTE, all lines from same environment, emission fills beam; mu=2.37, t0~0.01 [4.3 Rotational Diagram Analysis: "This method assumes that the lines are in local thermodynamic equilibrium (LTE), that all lines originate from the same disk environment, and that the emission fills the beam."]
  - fitting: Linear fit of ln(Nu/gu) vs Eu; includes 10% flux uncertainty [Table 4 notes: "Errors and fits include 10% absolute flux uncertainties, added in quadrature to the velocity-integrated flux uncertainties."]
  - validation: Energy ranges similar across disks; critical densities below disk densities supporting LTE [4.3 Rotational Diagram Analysis: "Notably the energy ranges covered by the H$_2$CO lines for each disk are similar, implying that these results are not due to excitation effects from using different H$_2$CO lines."]
- result: Disk-averaged Tex, DM Tau = 11 ± 0.39 K [Table 4: "| DM Tau | $11 \pm 0.39$ | $2.4 \pm 0.34$ |"]
- result: Disk-averaged Tex, J1604-2130 = 37 ± 3.6 K [Table 4: "| J1604-2130 | $37 \pm 3.6$ | $21 \pm 3.2$ |"]
- result: Disk-averaged Tex, LkCa 15 = 29 ± 8.8 K [Table 4: "| LkCa 15 | $29 \pm 8.8$ | $3.1 \pm 1.4$ |"]
- result: Disk-averaged Tex, MWC 480 = 21 ± 2.2 K [Table 4: "| MWC 480 | $21 \pm 2.2$ | $1.9 \pm 0.47$ |"]
- result: Disk-averaged Ntot, J1604-2130 = 21e12 ± 3.2e12 cm^-2 [Table 4: "| J1604-2130 | $37 \pm 3.6$ | $21 \pm 3.2$ |"]
- result: Disk-averaged Ntot, MWC 480 = 1.9e12 ± 0.47e12 cm^-2 [Table 4: "| MWC 480 | $21 \pm 2.2$ | $1.9 \pm 0.47$ |"]
- limitation (authors): Non-uniform initial calibration across the sample [2.3 Data Reduction: "we note that this initial calibration was non-uniform across the sample."]
- limitation (authors): Model-based snowline estimates are very uncertain [5.2 H2CO and the CO Snowline: "Note that these model-based estimates are very uncertain"]
- not stated (card): Line-free channels and spectral windows used for continuum subtraction and self-calibration; Exact self-calibration solint per dataset; Clean thresholds, image size, cell size, and number of iterations; Hand-drawn clean masks not provided; Data-reduction details of Loomis et al. (subm.) for 2015.1.00657.S; Rotational diagram fit weighting and uncertainty procedure details; Beam used to convolve K…

### 2019A&A...623A..68T: Small-scale physical and chemical structure of diffuse and translucent molecular clouds along the line of sight to Sgr B2 (2019; milky_way_ism, astrochemistry; archival_reuse)
- question: What is the spatial and kinematic structure, physical nature and chemistry of diffuse and translucent molecular clouds seen in absorption along the line of sight to Sgr B2(N)?
- step 2: decompose c-C3H2 absorption into velocity components
  - method: Automatic fitting of Weeds synthetic spectra with Gaussian opacity components per pixel using MCWeeds and Powell minimisation; fitted N_tot, FWHM, v0 [3.3 Modelling: "we use the fitting routine MCWeeds (Giannetti et al. 2017), which combines the python package PyMC2 (Patil et al. 2010) and Weeds (Maret et al. 2011)."] [3.4 Minimisation method: "We use a modified version of this method ( fmin_powell from scipy 3 ) with MCWeeds."]
  - software: Weeds, MCWeeds, PyMC2, scipy, GILDAS CLASS
  - parameter: detect dips >4 sigma; four velocity ranges; velocity prior uniform ±3 km/s; FWHM max 30 km/s [Appendix B: "Search in the continuum-subtracted spectrum for absorption dips with a peak signal-to-noise ratio higher than 4"]
  - assumption: LTE, beam filling factor 1 [5.4 Cloud sizes: "This means that our assumption of a beam filling factor of 1 to fit the spectra is reasonable."]
  - fitting: Powell local minimisation, MCWeeds priors: uniform velocity, truncated normal FWHM, normal log N width 2 [Appendix B: "the probability distribution for the velocity is uniform over the chosen interval"]
  - validation: residual peaks above 5 sigma then 4 sigma searched for missing components [Appendix B: "The programme looks for peaks above a threshold of 5σ in the residuals."]
- step 6: determine cloud nature (H2, Av, density)
  - method: Fit HCO+/H13CO+ absorption towards K4 with Weeds; N(H2) from HCO+ abundance 3e-9; Av=N(H2)/9.4e20; test against Mopra emission with RADEX non-LTE grids [4.7 Nature of the detected line-of-sigh…: "We perform non-LTE radiative transfer calculations with RADEX (van der Tak et al. 2007) to estimate the densities and kinetic temperatures"]
  - software: Weeds, RADEX
  - parameter: Tkin 10–130 K, nH2 10–1e7 cm-3; Mopra Tmb = 1.7 × TA* [4.7 Nature of the detected line-of-sigh…: "10–130 K for the kinetic temperature and 10–10 [7] cm [−][3] for the H 2 density"]
  - assumption: HCO+ abundance 3e-9 (diffuse), 2e-8 for N>9.4e13, log-interpolated between [Table 11: "2 × 10 [−][8] for N(HCO [+] ) > 9.4 × 10 [13] cm [−][2], and an interpolated value (in log-log space) in between."]
- result: Velocity components detected in c-C3H2 across 322 positions = 2838 ± not stated components [4.2 Identification of velocity componen…: "In total, 2838 velocity components are detected towards the 322 selected positions."]
- result: Median FWHM Category I = 5.4 ± not stated km/s [4.2 Identification of velocity componen…: "Category I has a median linewidth of 5.4 km s [−][1] ."]
- result: Median FWHM Category II = 7.5 ± not stated km/s [4.2 Identification of velocity componen…: "have a somewhat larger median linewidth of 7.5 km s [−][1] ."]
- result: H2 column densities from HCO+ = 3.3e20 to 9.0e22 ± not stated cm-2 [4.7 Nature of the detected line-of-sigh…: "We obtain H 2 column densities ranging from 3.3 × 10 [20] to 9.0 × 10 [22] cm [−][2]"]
- limitation (authors): Field of view limited by background continuum and finite resolution; ACA combination would help [6. Conclusions: "the limited size of the continuum background emission, which results from the spatial filtering of the interferometer, and the finite angular resolution."]
- limitation (authors): PDF width likely underestimated due to limited field of view [5.5 Turbulence: "Hence, the width of their PDFs is likely underestimated."]
- not stated (card): Calibrated/imaged EMoCA cubes and continuum map (from Belloche et al. 2016) are required; imaging parameters not given here; Initial guesses and exact tolerance settings of the automatic MCWeeds fit for reproducing the 2838 components; Exact ellipses excluded around hot cores N1 and N2; Baseline fitting (polynomial order, line-free windows) in CLASS; Primary-beam correction details; Exact noise-c…

### 2015ApJ...798...85P: CO Gas Inside the Protoplanetary Disk Cavity in HD 142527: Disk Structure from ALMA (2015; protoplanetary_disks; observational_alma_primary)
- question: How much gas survives inside the dust-depleted cavity of the HD 142527 disk, and what are the gas cavity size, wall shape and inclination?
- step 3: Optical depth from isotopologue ratios
  - method: Isothermal slab line ratio in high-velocity channels (<1.8 and >5.4 km/s) [3.3 Optical Thickness: "In this velocity range, the isotopic line ratio $R$ has a value of 2.0$\pm$0.2, which yields optical depths of"]
  - assumption: Same excitation temperature, CMB neglected, 12CO/13CO=76, 12CO/C18O=500 [3.3 Optical Thickness: "We also assume that the two selected lines share the same excitation temperature"]
- step 4: Gas mass in cavity from optically thin 13CO and C18O
  - method: LTE column density from summed peak emission in high-velocity channels, converted to H2 mass [3.5: "We measured the integrated line intensity of $^{13}{\rm CO}$ by summing the peak emission from the selected high velocity channels"]
  - parameter: T=43 K, d=140 pc, mu=1.36 [3.5: "For the gas temperature we used $T=43$ K, as calculated from $^{12}{\rm CO}$ in the previous section."]
  - assumption: [H2]/[12CO]=1e4, [12CO]/[13CO]=76, LTE [3.5: "Assuming a fiducial CO interstellar abundance of $[{\rm H}_2]/[\mbox{$^{12}{\rm CO}$}]=10^4$ and $[\mbox{$^{12}{\rm CO}$}]/[\mbox{$^{13}{\rm CO}$}]=76$"]
  - validation: Cross-check with archival C18O J=3-2 [3.5: "consistent with the $J=2-1$ estimate (5-$\sigma$ error bars)"]
- step 5: Forward model gas disk with LIME
  - method: Parametric axisymmetric disk, LIME non-LTE radiative transfer, model visibilities sampled at observed uv, chi2 comparison; scan of M_star and inclination, then cavity radius [4.2 Modeling Results: "Our models were compared to the data in the visibility plane based on $\chi^2$ statistics."]
  - software: LIME, CASA
  - parameter: h=0.1 r, gamma=1, R_c=200 au, T=50 K (r/50au)^-0.3, b=50 m/s, inner truncation 0.3 au [4.1: "The velocity dispersion of the random motions of the gas (Doppler b-parameter) was fixed to 50 m s$^{-1}$."]
  - assumption: Keplerian rotation, ISM CO abundance, vertically isothermal, axisymmetric [4.1: "For simplicity, we assumed that the gas in the disk follows circular Keplerian rotation"]
  - fitting: Reduced chi2 grid in M_star and inclination; cavity radius by visual inspection [4.2 Modeling Results: "The error was obtained from visual inspection of the plotted models against the $^{13}{\rm CO}$ data."]
  - validation: Visual comparison of best model with 13CO and C18O maps; SED consistency check with MCFOST [4.2 Modeling Results: "Finally, the best fit models were contrasted with the data by visual inspection."]
- result: Inclination = 28 ± 0.5 deg [Table 2: "$i$ | deg | 28 | 0.5"]
- result: Gas cavity radius = 90 ± 5 au [4.2 Modeling Results: "The best fit for the cavity radius in the gas is 90$\pm5$ au."]
- result: Gas depletion factor delta_gap = 0.02 ± 0.01 dimensionless [4.2 Modeling Results: "We estimate an uncertainty of 0.01 based on the optical thickness of the lines."]
- result: Gas mass in cavity from 13CO = 1.7e-3 ± 0.6e-3 Msun [3.5: "$M_{\rm gas} = (1.7 \pm 0.6)\times 10^{-3}$ M$_\odot$"]
- result: Isotopic line ratio R = 2.0 ± 0.2 dimensionless [3.3: "the isotopic line ratio $R$ has a value of 2.0$\pm$0.2"]
- result: Optical depth 12CO = ~56 ± not stated dimensionless [3.3: "$\tau_{\scriptstyle \rm {12}CO} \sim 56$ and $\tau_{\scriptstyle \rm {13}CO} \sim 0.7$"]
- result: Total disk mass from model = 0.1 ± not stated Msun [4.2: "yields a total (dust plus gas) mass of the disk of 0.1 M$_{\odot}$"]
- limitation (authors): Gas mass is a crude estimate, dominated by assumed isotopic ratios and temperature [3.5: "The main sources of uncertainty are the assumed isotopic line ratios and the gas temperature."]
- not stated (card): Briggs robust value, cell size, image size, CLEAN masks and threshold; Line-free channels used for continuum subtraction; Whether data were self-calibrated; CASA version; LIME settings (number of grid points, photons, collision data) and model grid ranges; How the high-velocity channel peaks were selected and summed for 13CO; Solid angle Omega adopted for the cavity; Model grids for M_star and in…

### 2026A&A...707A.120H: Spatial distribution of organics in the Horsehead nebula: Signposts of chemistry driven by atomic carbon (2026; astrochemistry, star_formation, milky_way_ism; observational_alma_primary)
- question: How are simple and complex organic molecules spatially distributed across the UV-illuminated edge of the Horsehead nebula, and what do their column density profiles say about formation pathways (e.g. atomic C chemistry)?
- step 3: Calibrate C17O-to-H2 factor and derive nH2 profiles
  - method: Fit C17O hyperfine lines in LTE with Tex=15 K at PDR and core; X = N(H2)/N(C17O); nH2 = X N(C17O)/l_depth with interpolated X [3.2.2: "Assuming a typical cloud depth along the line of sight of $\ell_{\mathrm{depth}} \simeq 0.1$ pc"]
  - software: SpectralRadex
  - parameter: Tex(C17O)=15 K; l_depth=0.1 pc [3.2.1: "with the excitation temperature fixed at $T_{\mathrm{ex}}=15$ K, we repeated the fitting procedure but now for the ALMA 7m+30m data"]
  - assumption: LTE for C17O 1-0; N(13CO)/N(C18O)~8 for consistency check [3.2.1: "Assuming $N(^{13}\mathrm{CO})/N(\mathrm{C^{18}O}) \sim 8$"]
  - fitting: Gaussian hyperfine components fit with MCMC [3.2.1: "Each hyperfine component was modeled as an independent Gaussian with fixed velocity separations"]
  - validation: Compared with Habart2005 density model and 13CO conversion factors [3.2.2: "along with the profile modeled by (cite: Habart2005) convolved with a $15^{\prime\prime}$ full width at half maximum (FWHM) Gaussian"]
- step 4: Derive Tkin from CH3CN K-ladder
  - method: Non-LTE RADEX fit of CH3CN J=6-5 K=0,1,2 with nH2 fixed from C17O; free Tkin and N [3.2.3: "the modeled CH$_3$CN intensities only depend on $T_{\mathrm{kin}}$ and $N(\mathrm{CH_3CN})$ as free parameters"]
  - software: SpectralRadex, RADEX, emcee
  - parameter: E/A = 1; Tbg=2.73 K; dv=0.6 km/s; K=2 used as upper limit for dx>=30 arcsec [3.2.3: "we assumed a ratio of $\mathrm{E/A} = 1$ between the two noninteracting torsional substates"]
  - fitting: emcee affine-invariant MCMC, walkers = 4x free parameters, 2000 burn-in + 3000 steps, 16/50/84 percentiles, chi2 likelihood, points every ~7.5 arcsec [3.2: "The number of walkers was set to four times the number of free model parameters, with 2000 burn-in steps and an additional 3000 steps used to sample the posterior distributions."]
  - validation: Compared with earlier CH3CN temperatures [3.2.3: "which is in good agreement with previous estimates using CH$_3$CN (cite: Gratier2013)"]
- step 6: Column density profiles of other organics
  - method: Non-LTE RADEX for H2CO, CH3OH, HNCO, HC3N; rotational-diagram (optically thin, fixed Tex) for CH2CO and CH3CHO; only N free [3.2.5: "the only free parameter to fit is $N$"]
  - software: SpectralRadex, emcee
  - parameter: E/A=1 for CH3OH, CH3CHO; OPR=3 for H2CO, CH2CO [3.2.5: "we assumed $\mathrm{E/A} = 1$ for CH$_3$OH and CH$_3$CHO and an ortho-to-para ratio of $\mathrm{OPR} = 3$ for H$_2$CO and CH$_2$CO"]
  - fitting: Same MCMC strategy as CH3CN [3.2.5: "The fitting strategy was essentially the same as for CH$_3$CN"]
  - validation: Compared with WHISPER-based column densities at PDR and core [3.2.5: "We checked the consistency of our results by comparing them with previous efforts."]
- result: N(C18O)/N(C17O) = 3.6 ± 0.5 dimensionless [3.2.1: "we derive an average isotopologue ratio of $N(\mathrm{C^{18}O})/N(\mathrm{C^{17}O}) = 3.6 \pm 0.5$"]
- result: X_C17O at PDR = 4.0e6 ± 0.2e6 dimensionless [3.2.1: "$X_{\mathrm{C^{17}O}} = (4.0\pm0.2) \times10^{6}$ for the PDR"]
- result: X_C17O at dense core = 5.9e6 ± 0.3e6 dimensionless [3.2.1: "$X_{\mathrm{C^{17}O}} = (5.9\pm0.3) \times10^{6}$ for the dense core"]
- result: N(C17O) at PDR = 4.7e15 ± 0.2e15 cm^-2 [Appendix 7.2: "$N(\mathrm{C^{17}O}) = (4.7 \pm 0.2)\times10^{15}$ cm$^{-2}$ for the PDR"]
- result: N(C17O) at dense core = 5.2e15 ± 0.2e15 cm^-2 [Appendix 7.2: "$N(\mathrm{C^{17}O}) = (5.2 \pm 0.2)\times10^{15}$ cm$^{-2}$ for the dense core"]
- result: Tkin PDR (CH3CN) = 58 ± +13/-10 K [3.2.3: "$T_{\mathrm{kin}} = 58^{+13}_{-10}$ K for the PDR position"]
- result: Tkin dense core (CH3CN) = 28 ± +11/-10 K [3.2.3: "$T_{\mathrm{kin}} = 28^{+11}_{-10}$ K for the dense core position"]
- result: X_13CO = ~1.7e5 ± not stated dimensionless [3.2.1: "we determined a $^{13}\mathrm{CO}$-to-H$_2$ conversion factor of $X_{\mathrm{^{13}CO}}\sim1.7\times10^{5}$"]
- result: CH2CO abundance wrt N_H at PDR = 4.7 ± +0.3/-0.3 not stated (table units) [Table 5: "| CH$_2$CO | $4.7^{+0.3}_{-0.3}$ | $1.4^{+0.1}_{-0.1}$ | $0.9$ |"]
- result: CH3CN abundance wrt N_H at PDR = 1.3 ± +0.1/-0.1 not stated (table units) [Table 5: "| CH$_3$CN | $1.3^{+0.1}_{-0.1}$ | $0.2^{+0.1}_{-0.1}$ | $0.2$ |"]
- limitation (authors): Did not recover high temperatures (>100 K) at the cloud edge; limited angular resolution and sensitivity [3.2.3: "This discrepancy likely stems from the limited angular resolution and sensitivity of the observations"]
- limitation (authors): Uncertainties exclude systematics from fixed parameters [3.2.5: "without including systematic uncertainties on the fixed parameters"]
- not stated (card): CLEAN parameters in GILDAS/MAPPING (weighting, mask, threshold, niter); Line-free channels and velocity ranges for moment maps; Likelihood form and priors/bounds for the MCMC fits; Which values of nH2 and Tkin were fixed for each molecule; Calibration scripts and flagging beyond antenna CM06; Exact conversion of 30m to pseudo-visibility weighting; Details of the 1-sigma noise and systematic fixed…

### 2021A&A...656A..46M: ALCHEMI, an ALMA Comprehensive High-resolution Extragalactic Molecular Inventory. Survey presentation and first results from the ACA array (2021; nearby_galaxies, astrochemistry; large_program_or_survey)
- question: What is the molecular richness of the central molecular zone of NGC 253, probed by an unbiased ALMA spectral scan, and what do ACA 15'' spectra reveal about its chemistry, vibrational emission, organics and isotopic ratios?
- step 5: Extract 15'' spectrum and fit LTE model per species
  - method: Extract spectrum from the pixel at average of peak positions of 16 bright moment 0 maps; fit single-Gaussian LTE synthetic spectra per molecule with all transitions at once [4.2.1 Selected sample position: "The spectra analyzed in this article were extracted from the pixel at position $\alpha_{J2000}=00^h47^m33.10^s$, $\delta_{J2000}=-25^\circ17'18.1''$"]
  - software: MADCUBA
  - parameter: Source size 5'' (10'' for 12C16O); fixed v_LSR=230 km/s, FWHM=150 km/s, Tex=15 K when unconstrained [4.2.2 Line identification and LTE model…: "parameters were fixed to $v_{LSR}=230$ $\rm km\,s^{-1}$ and $\Delta~v_{1/2}=150$ $\rm km\,s^{-1}$"] [4.2.2 Line identification and LTE model…: "the excitation temperature was set to $T_{ex}$=15 K"]
  - parameter: Detection criterion: all unblended transitions above 5 sigma in model detected and fit converged [4.2.2 Line identification and LTE model…: "A species has been considered detected if all the detectable transitions above $5~\sigma$ (according to the LTE model), which are not blended with brighter transitions, are detected in our data."]
  - assumption: LTE, single Gaussian component, column density linear in source solid angle [4.2.2 Line identification and LTE model…: "the modeling described here will consider a single Gaussian emission profile"]
  - fitting: MADCUBA least-squares fit; only statistical uncertainties reported [4.2.2 Line identification and LTE model…: "reported uncertainties do not include calibration uncertainties but statistical uncertainty on the fit to the spectra."]
  - validation: Residuals inspected against full-spectrum model; non-LTE deviations identified; extra criteria for new detections [9.1 Fitting details of newly detected s…: "any bright emission line predicted by the LTE model should be consistent with the observed spectra and no big outliers should be present."]
- step 6: Derive isotopic ratios and opacity effects
  - method: Column density ratios of isotopologue pairs; effect of source size tested on HCO+; CN hyperfine multi-component LTE models [5.4 Isotopic ratios: "Table [6](#tab.isotopicratios) shows the isotopic ratios derived from the column densities fitted to all detected isotopologue pairs"]
  - software: MADCUBA
  - parameter: CO isotopologues recalculated for 10'' source size [5.4 Isotopic ratios: "the emission of $^{13}$CO and C$^{18}$O fits were recalculated for an equivalent source size of $10''$."]
  - validation: Compared with literature ratios in Table 8 [5.4 Isotopic ratios: "Table [8](#tab.isotopicratiosliterature) compiles all isotopic ratios reported in the literature towards NGC 253."]
- step 7: Vibrational emission and proto-SSC fraction
  - method: Gaussian fits to v2=1f transitions, L_vib/L_IR compared with Sgr B2(N) value [5.2.2 Vibrational emission as tracer: "Assuming that vibrational emission is mostly contributed by Sgr B2(N)-like hot cores, this comparison results in a $\sim3\%$ level"]
  - parameter: line width 150 km/s; LTE Tex=300 K for display [Table notes: "considers a line width of 150 $\rm km\,s^{-1}$, similar to that fitted to most rotational transitions."]
  - assumption: L_IR = 2.1e10 Lsun [1.2 NGC 253: "$L_{\rm IR}=2.1\times10^{10}\,L_\odot$"]
  - validation: Consistent with Rico-Villas 2020 ~3% [5.2.2 Vibrational emission as tracer: "this estimate is consistent with the contribution from proto-SSCs of $\sim 3\%$ derived by (cite: Rico-Villas2020)"]
- step 8: Organic abundances relative to methanol
  - method: C2H5OH and HCOOH relative to CH3OH; H2 from C18O with 18O/16O=100 and CO/H2~8e-5 [5.3 Organic Molecules: "assuming $\rm ^{18}O/^{16}O=100$ (as derived in Sect. [5.4.2](#sec.isotopologuesOxygen)) and CO/H$_2\sim 8\times10^{-5}$ (cite: Frerking1982), which yields $N_{\rm H_2}=3.1\times10^{23}~\rm cm^{-2}$"]
  - software: MADCUBA
  - assumption: Factor of 2 uncertainty in H2 [5.3 Organic Molecules: "We included a conservative factor of 2 uncertainty in the H$_2$ determination"]
  - validation: Compared with GC GMCs and hot cores [5.3 Organic Molecules: "The comparison in Fig. [12](#fig.complexmolecules) shows that the averaged abundances towards NGC 253 are on the high end of GMC measurements"]
- result: Number of species detected (firm or tentative) = 78 ± not stated species [4.2.2 Line identification and LTE model…: "only 78 species are considered firmly or tentatively detected, accounting for 1790 transitions"]
- result: 12C/13C from bright high dipole moment species (weighted) = 22 ± 2 dimensionless [5.4.1 Carbon: "is $22\pm2$."]
- result: 16O/18O from HCO+ = 100 ± 20 dimensionless [5.4.2 Oxygen: "Our $\rm ^{16}O/^{18}O$ ratio of $100\pm20$ measured with HCO$^+$"]
- result: 16O/18O from 13CO/13C18O = 520 ± 60 dimensionless [Table 6: "| $520\pm60$ | $^{13}$CO/ $^{13}$C$^{18}$O |"]
- result: 14N/15N weighted average = 170 ± 20 dimensionless [5.4.3 Nitrogen: "are consistent with a weighted average of $170\pm20$"]
- result: 32S/34S (CS) = 9.7 ± 0.5 dimensionless [5.4.4 Sulfur: "ratios measured with both CS and SO ($9.7\pm0.5$ and $14\pm4$, respectively)"]
- result: 28Si/29Si = 9 ± 2 dimensionless [5.4.5 Silicon: "the ratio $\rm ^{28}Si/^{29}Si$=$9\pm2$"]
- result: L_vib/L_IR from HCN 3-2 v2=1f = 1.4e-9 ± not stated dimensionless [Table vibLuminosities: "| HCN $3-2$ | 267.199 | $53\pm11$ | 8.5 | $6.08\pm0.07$ | $120\pm20$ | 28.9 | 1.4 |"]
- result: Proto-SSC contribution to IR luminosity = ~3 ± not stated % [5.2.2 Vibrational emission as tracer: "this comparison results in a $\sim3\%$ level as a proxy to the contribution from proto-SSCs to the global infrared luminosity in NGC 253."]
- result: C2H5OH/CH3OH abundance = 1.1e-1 ± 0.4e-1 dimensionless [5.3 Organic Molecules: "abundances of $\rm C_2H_5OH$ ($1.1\pm0.4\times10^{-1}$) and HCOOH ($2.8\pm1.0\times10^{-2}$) relative to CH$_3$OH"]
- result: N_H2 toward the sample position = 3.1e23 ± factor of 2 cm^-2 [5.3 Organic Molecules: "which yields $N_{\rm H_2}=3.1\times10^{23}~\rm cm^{-2}$"]
- limitation (authors): Calibration uncertainty not included in fit uncertainties; line flux scaling anomalies in some tunings [3.1 Flux calibration accuracy: "only the statistical uncertainty in the fits due the noise in the spectra are considered and not the absolute flux calibration uncertainty mentioned above"]
- limitation (authors): STATCONT continuum subtraction not optimal for lines near noise level [3.3 Continuum subtraction: "continuum subtraction is seen not to be optimal for spectral lines close to the noise level."]
- not stated (card): Explicit line-free channels or STATCONT settings per spectral window; Exact MADCUBA fit settings (algorithm options, mask choices per molecule); CASA version used for processing; tclean threshold values per spectral window; Distance to NGC 253 adopted; Observing dates and per-execution details; Pixel/spectral window data selection for line subsets used in each species fit

### 2020MNRAS.492.1180R: ALMA and ROSINA detections of phosphorus-bearing molecules: the interstellar thread between star-forming regions and comets (2020; astrochemistry, star_formation; observational_alma_primary)
- question: How are P-bearing molecules (PN, PO) formed in star-forming regions, and is the comet 67P/C-G P reservoir inherited from such environments?
- step 1: Map SO, PN, PO emission and identify P-spots
  - method: Integrated maps in velocity ranges; seven P-spots identified visually in PN map [3.1.2: "peaking towards several visually-identified spots (P-spots, hereafter) located along the cavities of the bipolar outflow"]
  - software: CASA, MADCUBA
  - parameter: Velocity ranges [-6.5,-4.5], [-4.5,-2.0], [-2.0,0] km/s [3.1.2: "three different velocity ranges (\[-6.5,-4.5\], \[-4.5,-2.0\] and \[-2.0, 0\] km s$^{-1}$)"]
- step 2: Extract spectra
  - method: Spectra from circular regions at P-spot, MM, HV positions [3.1.2: "The spectra extracted in a circular region of 3$^{\prime\prime}$ diameter centered on the positions of the P-spots"]
  - software: MADCUBA
- step 3: LTE fit of column densities, velocities, linewidths
  - method: MADCUBA-AUTOFIT synthetic LTE spectra with CDMS entries incl. 14N hyperfine [3.1.3 LTE analysis: "we have used the MADCUBA-AUTOFIT tool that compares the observed spectra with the LTE synthetic spectra of the different species"]
  - software: MADCUBA, SLIM, AUTOFIT
  - parameter: Tex fixed: 5 K for PN/PO, 34 K for SO; free N, v, FWHM [3.1.3 LTE analysis: "Then, fixing $T_{\rm ex}$, we run MADCUBA-AUTOFIT leaving $N$, $\varv$, and $FWHM$ as free parameters."]
  - assumption: LTE, single transition so Tex cannot be derived [3.1.3 LTE analysis: "Since our data contain only a single rotational transition of the three species (PN, PO and SO), the excitation temperature cannot be derived, and hence we assumed fixed values."]
  - fitting: Levenberg-Marquardt least squares; errors from covariance matrix [3.1.3 LTE analysis: "This tool provides the best non-linear least-squared fit using the Levenberg-Marquardt algorithm."]
  - validation: Tex sensitivity: column densities vary by factor 2.5 (PN), 2.1 (PO) over 5-50 K [3.1.3 LTE analysis: "the column densities of PN and PO can vary by a factor of 2.5 and 2.1, respectively, assuming different values of $T_{\rm ex}$ in the range of 5$-$50 K"]
- step 4: Non-LTE test of PO/PN ratio
  - method: RADEX with n(H2)=1e4,1e5,1e6 cm-3 deriving column densities matching line fluxes [3.1.4 Non-LTE analysis: "we have run RADEX assuming three different values: $n$(H$_2$) = 1$\times$10$^{4}$, 1$\times$10$^{5}$ and 1$\times$10$^{6}$ cm$^{-3}$."]
  - software: RADEX
  - parameter: Tkin = 20 K, background 2.73 K [3.1.4 Non-LTE analysis: "The calculations assume a kinetic temperature of $T_{\rm kin}$ = 20 K and a background temperature of 2.73 K."]
  - assumption: He collision rates scaled to H2 (x1.385 PN, x1.4 PO) [3.1.4 Non-LTE analysis: "For PO, the recent collision data with He (described in Appendix [7](#appendix-PO-collision-rates)) were scaled by 1.4 to mimic H$_2$."]
  - validation: Compared with LTE ratios [Discussion, Hints from molecular abunda…: "In all cases, the PO/PN ratio clearly increases with increasing distance from the central protostar, supporting the role of photochemistry to explain the observed relative abundances of PN and PO."]
- result: PO/PN ratio at P2 = 0.6 ± 0.2 dimensionless [Table 3: "| P2 | 0.6$\pm$0.2 | 170$\pm$11 | 309$\pm$107 |"]
- result: PO/PN ratio at P3 = 1.4 ± 0.3 dimensionless [Table 3: "| P3 | 1.4$\pm$0.3 | 151$\pm$14 | 112$\pm$17 |"]
- result: PO/PN ratio at P5 = 2.6 ± 0.6 dimensionless [Table 3: "| P5 | 2.6$\pm$0.6 | 72$\pm$9 | 27$\pm$5 |"]
- result: N(PN) at P4 (LTE) = 5.5 ± 0.2 1e12 cm-2 [Table 4: "| P4 | 5.5$\pm$0.2 | -5.14$\pm$0.03 | 1.50$\pm$0.05 | 0.24$\pm$0.01 |"]
- result: PN-PO velocity differences in P3-P6 = 0.4, 0.46, 0.24, 0.5 ± 0.1, 0.07, 0.09, 0.1 km/s [3.1.3 LTE analysis: "the differences are 0.4$\pm$0.1, 0.46$\pm$0.07, 0.24$\pm$0.09 and 0.5$\pm$0.1 km s$^{-1}$, respectively"]
- result: Max non-LTE PO/PN (P5) = 7.6 (n=1e6) ± not stated dimensionless [Table 5: "| P5 | 17.0 | 2.5 | 2.1 | | 82 | 16 | 16 | | 4.8 | 6.4 | 7.6 |"]
- limitation (authors): Resolution too low to resolve cavity wall layers; speculative conclusions [4.1.3: "the current data only allows to draw some speculative conclusions, and higher angular resolution observations are needed"]
- not stated (card): Imaging parameters (weighting/robust, cell, image size, deconvolver, masking); CASA version and pipeline version; Continuum subtraction and line-free channels; Flux calibration accuracy and self-calibration; Details of P-spot selection and spectra extraction beyond 3" circle; ROSINA spectra reduction details and ion counts; Per-spot Tex handling for second velocity components

### 2024A&A...689A..64B: An ALCHEMI inspection of sulphur-bearing species towards the central molecular zone of NGC 253 (2024; nearby_galaxies, astrochemistry; archival_reuse)
- question: Which type of gas regions are probed by sulphur-bearing species in the NGC 253 CMZ, and which process(es) dominate the release of sulphur into the gas phase?
- step 1: Extract spectra and line parameters
  - method: Velocity-integrated maps and beam-sized (1.6") spectra from ALCHEMI cubes; direct integration for non-blended lines, Gaussian fits for FWHM and Vlsr, two-Gaussian fits for blended lines; flux converted to brightness temperature [5.1 Gaussian Fit and Spectra: "In the case of non-blended lines, we measured the direct integration of the channel intensities."] [5.1 Gaussian Fit and Spectra: "we performed a multi-Gaussian fit (with two Gaussian components)"]
  - software: GILDAS MAPPING, GILDAS CLASS, WEEDS
  - parameter: 3 sigma detection threshold; lines >15% contaminated rejected [3 Observations, Data Processing and Lin…: "the threshold for line detection was set to 3$\sigma$ for the integrated intensity."]
  - parameter: Spectra from circular region of one beam (1.6") at coordinates in Table 1 [5.1 Gaussian Fit and Spectra: "We extracted each spectrum from a circular region of a beam size (1.6$"$) centred at the coordinates given in Tab. [1](#tab:regions)."]
- step 2: Rotation diagram LTE analysis
  - method: Rotation diagrams without beam correction, one to three rotation temperature components, chi-square minimisation including 15% calibration error and rms [5.2 Derivation of physical parameters: "we performed rotation diagrams (RDs) without beam correction."] [5.2.1 LTE analysis: OCS, CCS, and SO2: "The best-fit was calculated by minimizing the reduced chi-square, $\chi^2_r$."]
  - assumption: LTE, optically thin lines, beam filling factor 1 [5.2.1 LTE analysis: OCS, CCS, and SO2: "The beam filling factor was set to 1 as (1) we do not know the size of emission of the species"]
  - fitting: reduced chi-square minimisation [5.2.1 LTE analysis: OCS, CCS, and SO2: "The best-fit was calculated by minimizing the reduced chi-square, $\chi^2_r$."]
- step 3: Non-LTE LVG modelling
  - method: Grid (>=10,000 models) over column density, gas density and gas temperature, with source size free when >=4 lines; fit each rotation-temperature component separately; slab geometry [5.2.2 Methodology of the LVG analysis: "For each region and species, we ran a large grid of models ($\geq 10,000$) varying the column density of the species, the gas density and the gas temperature."]
  - software: grelvg
  - parameter: N 5e12-1e18 cm-2; n 1e3-1e8 cm-3; T limited to collisional-rate range; source size 0.1"-150" [5.2.2 Methodology of the LVG analysis: "In *grelvg* the sizes can vary between 0.1$\ensuremath{''}$ and 150$\ensuremath{''}$."]
  - assumption: Semi-infinite slab geometry, CBR 2.7 K, H2 OPR=3, line widths from measured averages, 15% calibration error [5.2.2 Methodology of the LVG analysis: "we assumed the geometry to be a semi-infinite slab"] [5.2.2 Methodology of the LVG analysis: "The ortho-to-para ratio (OPR) for H$_2$ is assumed to be set to the statistical value of 3."]
  - fitting: best chi-square over grid; uncertainty ranges from chi-square [5.2.2 Methodology of the LVG analysis: "For each region and species, we ran a large grid of models ($\geq 10,000$) varying the column density of the species, the gas density and the gas temperature."]
  - validation: Uniform-sphere geometry gave similar results (not shown) [5.2.2 Methodology of the LVG analysis: "We nonetheless performed some modelling using the geometry of a uniform sphere which led to similar results (not shown)."]
- result: OCS first-component Trot range = 10 to 65 ± not stated K [5.2.1 LTE analysis: OCS, CCS, and SO2: "ranges from $T_{\text{rot}}=10$ K in GMC10 to $T_{\text{rot}}=65$ K in SSC5"]
- result: OCS second-component Trot range = 124-312 ± not stated K [5.2.1 LTE analysis: OCS, CCS, and SO2: "The range of the second temperature component is $T_{\text{rot}}=124-312$ K."]
- result: SO2 Trot components = 55-79 and 115-298 ± not stated K [5.2.1 LTE analysis: OCS, CCS, and SO2: "The first and second components have $T_{\text{rot}}= (55-79)$ K and $(115-298)$ K, respectively."]
- result: H2S gas temperature (inner CMZ and GMC10) = 30-159 ± not stated K [5.2.3 Results of the LVG analysis: "$T_{\text{gas}}=30-159$ K and $n_{\text{gas}}\geq 10^7$cm$^{-3}$"]
- result: H2S emission size = 0.17-0.5 ± not stated arcsec [5.2.3 Results of the LVG analysis: "values ranging between 0.17 and 0.5$\ensuremath{''}$ ($\sim 3-8$ pc)"]
- result: CS low-Eu component gas temperature = 5-14 ± not stated K [5.2.3 Results of the LVG analysis: "values between $T_{\text{gas}}=5-14$ K, and between $T_{\text{gas}}=15-110$ K for the first and second components"]
- result: OCS low-Eu LVG column density = 2e15-5e17 ± not stated cm^-2 [5.2.3 Results of the LVG analysis: "The total column densities derived range between $2\times10^{15}$ and $5\times10^{17}$ cm$^{-2}$."]
- result: Best H2S OPR = 1 ± not stated dimensionless [12.2 H2S + H2-34S: "We found that the best OPR reproducing the observations in all the regions is 1."]
- limitation (authors): CS results poorly constrained, source size fixed at 1.6" [5.2.3 Results of the LVG analysis: "Overall, due to the low number of transitions available for each of the component, the results for CS are among the less constrained and should be taken with caution."]
- limitation (authors): Comparing GMC-scale NGC 253 with parsec scale Galactic regions [6.2 Comparison with Galactic environmen…: "We would like to raise a word of caution as we are comparing GMC-size scales in NGC 253 with parsec and sub-parsec scales in the various Galactic environments."]
- not stated (card): Private-communication line identifications used for contamination checks; Exact line-free channel ranges for rms and baseline fitting; grelvg grid sampling steps and chi-square definition/minimisation details; How blended-line multi-Gaussian fits were initialised; Exact velocity windows for direct integration of each line; Exact ALCHEMI data release/version of the cubes; Rotation-diagram fitting …

### 2014Sci...345.1584B: Detection of a branched alkyl molecule in the interstellar medium: iso-propyl cyanide (2014; astrochemistry, star_formation; observational_alma_primary)
- question: Can a branched alkyl molecule (iso-propyl cyanide) be detected in the ISM, and how does its abundance compare with its straight-chain isomer and with chemical model predictions?
- step 2: Identify lines via LTE modeling
  - method: LTE model of all molecules with 5 parameters (column density, temperature, source size, velocity offset, linewidth) per spectral window [Line identification and spectral modeli…: "with five parameters: column density, temperature, source size, velocity offset, and linewidth."]
  - software: Weeds, CLASS
  - assumption: LTE [Line identification and spectral modeli…: "The emission of each molecule across the full 3 mm atmospheric window is modeled assuming local thermodynamic equilibrium"]
  - validation: Only transitions not severely blended with other species are used [Line identification and spectral modeli…: "Only the transitions that are not severely blended with transitions of other species are shown in these figures."]
- step 4: Derive rotation temperature
  - method: Population diagram linear fit after subtracting contaminating-molecule model [Line identification and spectral modeli…: "Finally, we constructed population diagrams(cite: Goldsmith99) for *i*-PrCN and *n*-PrCN using the transitions that are not too severely blended with emission from other identified species."]
  - assumption: Optically thin transitions [Line identification and spectral modeli…: "provided the transitions are optically thin (which is verified to be true a posteriori)"]
  - fitting: linear fit to population diagram [Materials and Methods, Line identificat…: "a linear fit to these data points can give a rough estimate of the rotation temperature characterizing the emission of the molecules, provided the transitions are optically thin"]
  - validation: Optical thinness verified a posteriori [Line identification and spectral modeli…: "provided the transitions are optically thin (which is verified to be true a posteriori)"]
- step 5: Derive column densities and abundance ratio
  - method: LTE model with size 1.0'', Trot 153 K, linewidth 5 km/s, with correction for vibrationally excited states [main text: "With the size and temperature derived above and a linewidth measurement of 5 km s$^{-1}$, we obtain a good fit to all transitions"]
  - software: Weeds
  - parameter: Vibrational partition function factors at 150 K: 1.64 (i-PrCN), 2.09 (g-n-PrCN), 2.36 (a-n-PrCN) [Laboratory spectroscopy: "increase the partition function values at 150 K by factors of 1.64, 2.09, and 2.36 for *i*-PrCN, *g-n*-PrCN, and *a-n*-PrCN, respectively."]
- result: Rotation temperature (n-PrCN) = 153 ± 12 (SEM) K [Line identification and spectral modeli…: "We derive $T_{\rm ex} = 154 \pm 99$ K for *i*-PrCN and $153 \pm 12$ K (SEM) for *n*-PrCN."]
- result: i-PrCN column density = 7.2e16 ± 1.4e16 (SEM) cm^-2 [main text: "we derive column densities of $7.2 \pm 1.4 \times 10^{16}$ cm$^{-2}$ and $1.8 \pm 0.4 \times 10^{17}$ cm$^{-2}$ (SEM), respectively"]
- result: n-PrCN column density = 1.8e17 ± 0.4e17 (SEM) cm^-2 [main text: "we derive column densities of $7.2 \pm 1.4 \times 10^{16}$ cm$^{-2}$ and $1.8 \pm 0.4 \times 10^{17}$ cm$^{-2}$ (SEM), respectively"]
- result: [i-PrCN]/[n-PrCN] = 0.40 ± 0.06 (SEM) dimensionless [main text: "which yields an abundance ratio \[*i*-PrCN\]/\[*n*-PrCN\] of $0.40 \pm 0.06$ (SEM)"]
- limitation (authors): Preliminary LTE model not fully optimized for ALMA; abundance uncertainties exclude free-free contamination and dust property uncertainties [Line identification and spectral modeli…: "This model has not been fully optimized for ALMA yet but it is already sufficiently reliable to allow for detecting new molecules in the ALMA spectra."]
- not stated (card): Exact line-free channel ranges used for continuum subtraction; CLEAN parameters (weighting/robust, cell size, image size, masks, threshold); Which spectral line and reference antenna/solint used for self-calibration; Full list and frequencies of i-PrCN and n-PrCN transitions used in population diagrams; Weeds LTE parameters for all other molecules in the preliminary model; Details of free-free co…

### 2020MNRAS.497.2811K: Survey of planetesimal belts with ALMA: gas detected around the Sun-like star HD 129590 (2020; debris_disks, astrochemistry; observational_alma_primary)
- question: Do debris discs around later-type stars host secondary CO/CN gas, and what are the dust and gas properties of 10 planetesimal-belt systems?
- step 5: Fit gas disc with LTE radiative transfer MCMC
  - method: Gaussian ring gas model, RADMC-3D CO cubes vs dirty cubes, per channel [3.2.2: "We then produce dirty cubes (i.e. without cleaning the images) around the CO line and use RADMC-3D to produce CO model cubes"]
  - software: RADMC-3D, emcee
  - parameter: 100 walkers, ~10,000 steps; 2.667 channels per resolution element [3.2.2: "we run the simulations with 100 walkers and for $\sim$10,000 steps"]
  - assumption: LTE, mu=14, axisymmetric [3.2.2: "we first assume that CO is in local thermal equilibrium (LTE)"]
  - fitting: free: R0, DeltaR, Sigma0, T0, v*, i, PA, offsets [3.2.2: "The free parameters of this gas model are thus $R_0$, $\Delta R$, $\Sigma_0$, $T_0$, $v_\star$"]
  - validation: HD 121191 compared to Moor et al. 2017 [3.2.2: "We compare our results on the CO detection in HD 121191 to (cite: 2017ApJ...849..123M)."]
- step 6: Non-LTE CO and CN masses
  - method: Optically thin non-LTE with fluorescence, scan over electron density and Tk 10-250 K, take min/max [3.2.2 Fit with an MCMC radiative transf…: "To account for our lack of knowledge of the temperature and electron density in each system, we assume wide ranges for both and then give a mass range estimate computed as being the minimum and maximum values reached on these plots"]
  - software: LAMDA database
  - assumption: collision rates from Dickinson & Richards 1975, Allison & Dalgarno 1971 [3.2.2: "The CO/electron collision rates where taken from (cite: 1975JPhB....8.2846D)"]
- result: HD 129590 CO mass (non-LTE) = 2.1e-5 - 1.3e-4 ± range M_earth [3.2.2: "we find that (the optically thin) mass range is $2.1\times10^{-5}$ - $1.3\times10^{-4}$ M$_\oplus$"]
- result: HD 121191 gas ring radius = 22 ± +2/-3 au [3.2.2: "$R_0 = 22^{+2}_{-3}$ au"]
- result: HD 121191 CO mass LTE = 2.3e-3 ± +2.3/-0.9 e-3 M_earth [3.2.2: "$2.3^{+2.3}_{-0.9} \times 10^{-3}$ M$_\oplus$"]
- limitation (authors): Dust masses have large systematic uncertainties from arbitrary composition; HD 129590 gas unconstrained by MCMC [3.1.2: "it should be understood that it has large systematic uncertainties"]
- not stated (card): Line-free channels for continuum and uvcontsub; CASA version and pipeline version; Image size, cell size, clean threshold; Flux, bandpass and phase calibrators; MCMC priors ranges and burn-in length; Velocity binning of cubes and masks used for fluxes; Stellar models for non-LTE fluorescence and electron density grid

### 2019ApJ...870L..26C: ALMA Autocorrelation Spectroscopy of Comets: The HCN/H<SUP>13</SUP>CN Ratio in C/2012 S1 (ISON) (2019; solar_system, astrochemistry; observational_alma_primary)
- question: Can ALMA main-array autocorrelation spectra recover extended coma emission from comet ISON, and what is the H12CN/H13CN ratio (13C fractionation in cometary HCN)?
- step 2: Measure line intensities and rotational temperature
  - method: Integrate lines; rotational diagram of three CH3OH lines [Results: "Using a rotational diagram analysis (cite: boc94), the best-fitting rotational temperature was found to be $T_{rot}=139\pm29$ K"]
  - fitting: Rotational diagram fit [Results: "Using a rotational diagram analysis (cite: boc94), the best-fitting rotational temperature was found to be $T_{rot}=139\pm29$ K"]
- step 3: Non-LTE radiative transfer modeling for production rates
  - method: Modified LIME, statistical equilibrium plus Monte Carlo, Haser spherical coma, collisions with H2O and electrons, fluorescent pumping; fit CH3OH for Tkin then derive Q [Radiative transfer modeling: "Our model employs a modified version of the Line Modeling Engine (cite: bri10)"]
  - software: LIME
  - parameter: 5,000 cells Delaunay grid; expansion velocity 1.1 km/s; Tkin 145 K [Radiative transfer modeling: "The model coma is divided into 5,000 cells on an unstructured Delaunay grid with logarithmic radial sampling."]
  - assumption: H13CN photodissociation and pumping rates same as HCN [Radiative transfer modeling: "the photodissociation and pumping rates for H$^{13}$CN were assumed to be the same as for HCN"]
  - fitting: Simultaneous fit of all detected CH3OH transitions for Tkin [Radiative transfer modeling: "The coma kinetic temperature was derived by simultaneously fitting all the detected CH$_3$OH transitions, resulting in $T_{kin}= 145$ K."]
  - validation: Collision rates varied by factor 2 changed line intensities by a few percent; alternative Tkin=100 K model run [Radiative transfer modeling: "varying them by a factor of 2 and found that the predicted line intensities changed by only a few percent"]
- result: H12CN/H13CN ratio = 88 ± ±18 dimensionless [Discussion: "reveal an H$^{12}$CN/H$^{13}$CN ratio of $88 \pm 18$"]
- result: CH3OH rotational temperature = 139 ± ±29 K [Results: "$T_{rot}=139\pm29$ K"]
- result: Q(HCN) = 3.0e26 ± ±0.1e26 s-1 [Table 1: "$(3.0 \pm 0.1) \times 10^{26}$"]
- result: Q(H13CN) = 3.4e24 ± ±0.7e24 s-1 [Table 1: "$(3.4 \pm 0.7)\times 10^{24}$"]
- result: Ratio with Tkin=100 K = 82 ± ±17 dimensionless [Discussion: "The corresponding H$^{12}$CN/H$^{13}$CN ratio is $82\pm17$"]
- limitation (authors): Ad-hoc use of phase calibrator scans for sky subtraction leaves standing waves and sky lines and high noise [Discussion: "Our ad-hoc use of phase calibration scans to subtract the sky and telescope background signal is far from ideal"]
- not stated (card): Which scans/antennas were averaged and any flagging or weighting; Line-free channel ranges for baseline fitting; Velocity range for line integration; Opacity tau0 values used; Model details such as abundance profile and photodissociation scale lengths; Observation details of the interferometric cross-correlation comparison

### 2015ApJ...803...60S: ALMA Multi-line Observations of the IR-bright Merger VV 114 (2015; nearby_galaxies, astrochemistry; observational_alma_primary)
- question: Distribution and kinematics of diffuse and dense molecular gas in the merger VV 114, and spatial variation of excitation conditions across the two merging disks
- step 4: Non-LTE radiative transfer modeling
  - method: RADEX grid in Tkin, nH2, N(H2) (case 1) or [HCN]/[HCO+] (case 2); chi2 minimization [5.2 Radiative Transfer Analysis using R…: "varied the parameters until the residuals between the observed line fluxes and the modeled line fluxes are minimized in a $\chi^2$ sense"]
  - software: RADEX
  - parameter: Case 1: Tkin 5-300 K step 5, n 10^2-10^5; case 2: Tkin 5-400 K, n 10^3-10^7 [5.2 Radiative Transfer Analysis using R…: "$T_{\rm{kin}}$ = 5 – 400 K using steps of d$T_{\rm{kin}}$ = 5 K, $n_{\rm{H_2}}$ = $10^3$ – $10^7~\rm{cm^{-3}}$"]
  - assumption: [13CO]/[H2]=1.4e-6, [CO]/[13CO]=70, [CO]/[H2]=1e-4, [HCO+]/[H2]=1e-9; uniform sphere [5.2 Radiative Transfer Analysis using R…: "we fixed \[$^{13}$CO\]/\[H$_2$\] = 1.4 $\times$ 10$^{-6}$ (cite: dav13) and \[CO\]/\[$^{13}\rm{CO}$\] = 70"]
  - fitting: chi2 grid; 95% confidence region chi2<7.81 (3 dof) [5.2 Radiative Transfer Analysis using R…: "We list the results that are within the 95 % confidence level with 3-degree of freedom ($\chi^2 < 7.81$)"]
- step 5: LTE filling factor, Tex, column density, abundances
  - method: Tex from CO(1-0) with Phi=Tb/Tkin; optical depth and column density equations [5.3 Filling factor and Column Density u…: "Using $T_{\rm{kin}}$ estimated from the RADEX calculation (§[5.2](#chi)), we estimate the beam filling factor $\Phi_{\rm{A}}$"]
  - assumption: 13CO and CO from same cloud; 12CO(1-0) optically thick [5.3 Filling factor and Column Density u…: "Assuming that the $^{13}$CO and CO arise from the same molecular cloud, and that the $^{12}$CO (1–0) is optically thick"]
- result: Tkin at R21a (eastern nucleus), best fit = 50 (range 25-90) ± not stated K [5.2.1 Case 1: "constrained to within 25 – 90 K (the best fit is 50 K)"]
- result: nH2 at E0 (AGN) = 10^5.0-10^5.4 ± not stated cm^-3 [5.2.2 Case 2: "$n_{\rm{H_2}}$ = 10$^{5.0}$ – 10$^{5.4}$ cm$^{-3}$"]
- limitation (authors): alpha_CO very uncertain and held constant [5.1: "such a study is beyond the scope of this present paper"]
- limitation (authors): Missing flux for some lines [3.2 12CO (3-2): "there are significant negative sidelobes at the north and south of the image which is likely the cause of missing flux"]
- not stated (card): Briggs robust value for each cube; Line-free channels used for continuum; CASA version and clean parameters (threshold, masks, iterations); How multi-configuration data were combined; Exact box positions and Gaussian fit details; RADEX script details (line widths, chi2 error budget); Pa-alpha extinction correction and SFR calibration choices; Whether pipeline products were re-calibrated

### 2015RAA....15.2213A: <SUP>12</SUP>CO emission from the Red Rectangle (2015; evolved_stars; archival_reuse)
- question: What are the morphology, temperature, density and kinematics of the CO gas envelope of the Red Rectangle, from archival ALMA CO(3-2) and CO(6-5) data?
- step 2: Reconstruct effective density
  - method: Iteratively solve F(y,z)=∫ρ(ξ,z)dx assuming rotational symmetry, 35 ξ bins x 50 z bins of 0.1'' [GAS EFFECTIVE DENSITY: "The integral equation is solved by iteration, using as input the fluxes, integrated over Doppler velocities, measured in each of the 1526 pixels that have been retained."]
  - parameter: uncertainties: absolute 0.16 (3-2) and 2.2 (6-5) Jy arcsec^-2 plus 20% relative; ten iterations [GAS EFFECTIVE DENSITY: "Ten iterations are amply sufficient to achieve convergence."]
  - assumption: Rotational symmetry, negligible absorption, LTE [MAIN FEATURES: "The assumption of rotational invariance about the star axis implies in addition that absorption is negligible."]
  - fitting: chi2 minimization [GAS EFFECTIVE DENSITY: "The iterative process is stopped when the value of $\chi^2$ used to measure the quality of the agreement"]
  - validation: Compared observed and reintegrated flux densities in 8 R and 8 angle bins [GAS EFFECTIVE DENSITY: "we compare in Figure 5 the observed flux densities with those obtained by integration of the effective densities along the line of sight"]
- step 3: Derive temperature from CO ratio
  - method: k_BT=(E6-E3)/ln(C/R_T) with (E6-E3)/kB=82.5 K, C=15.6 [TEMPERATURE AND DENSITY DISTRIBUTIONS: "In the present case, $(E_6-E_3)/k_B$=82.5 K and $C$=15.6."]
  - assumption: LTE, optically thin [TEMPERATURE AND DENSITY DISTRIBUTIONS: "In a regime of thermal equilibrium, and in the absence of significant absorption"]
  - validation: Compared with Men'shchikov et al. 2002 dust temperature and CO density [TEMPERATURE AND DENSITY DISTRIBUTIONS: "It is in good agreement with a model (Men’shchikov et al. 2002)"]
- result: Average temperature = 63 ± not stated K [MAIN FEATURES: "their ratio, 4.3, corresponds to an average temperature of 63 K"]
- limitation (authors): Imperfect deconvolution/calibration and crude symmetry and optically thin assumptions [DATA: "most of the flux fluctuations observed here arise from imperfect deconvolution and/or calibration"]
- not stated (card): Calibration and imaging software/CASA version and parameters of the archive-delivered cubes; Exact regridding/rotation interpolation method; Initial guesses and optimizer for chi2 minimization; Rest frequencies used; Observing dates and times on source

### 2017ApJ...848..101V: A <SUP>13</SUP>CO Detection in a Brightest Cluster Galaxy (2017; galaxy_clusters_and_sz, milky_way_ism, nearby_galaxies; observational_alma_primary)
- question: Can 13CO(3-2) emission in a BCG give an LTE molecular gas mass and a CO-to-H2 conversion factor to test the Galactic value?
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
- result: r31 (13CO-bright component) = 0.71 ± 0.15 dimensionless [CO (3-2)/(1-0): "The resulting $r_{31}$ line ratio is $0.71\pm0.15$ for the $^{13}$CO-bright velocity component"]
- result: R32 (13CO-bright, 13CO-tracing region) = 3.32 ± 0.66 dimensionless [Table 1: "$3.32\pm0.66$"]
- result: 13CO column density = 1.74e17 ± not stated cm^-2 [CO-to-H$_2$ Conversion Factor: "the total $^{13}$CO column density is $1.74\ensuremath{\times 10^{17}}\hbox{$\rm\; cm^{-2}\,$}$"]
- result: Total molecular gas mass with Galactic factor or alpha scaling = 1.1e10 ± not stated Msun [CO-to-H$_2$ Conversion Factor: "the total CO(1-0) luminosity gives a total molecular gas mass of $1.1\ensuremath{\times 10^{10}}\hbox{$\rm\thinspace M_{\odot}$}$"]
- limitation (authors): Mass traced is only a fraction of total; LTE and abundance assumptions are simplistic [CO-to-H$_2$ Conversion Factor: "As a result, this LTE analysis is only sensitive to a fraction of the total molecular gas mass."]
- not stated (card): Number of tclean/clean iterations, threshold and masks; Line-free channels used for uvcontsub and continuum fit order; Flux calibrator and flux scale uncertainty; Pipeline version; Image size and cell size; Exact extraction polygon for the region tracing 13CO; Details of the Monte Carlo and Gaussian fitting method (fitter, errors); Whether the 2011/2012 archival projects were used and how

### 2020A&A...644A..59K: Molecular remnant of Nova 1670 (CK Vulpeculae). I. Properties and enigmatic origin of the gas (2020; evolved_stars, astrochemistry, stellar_physics; observational_alma_primary)
- question: What are the molecular composition, morphology, excitation, and origin of the molecular gas in the remnant of Nova 1670 (CK Vul), a candidate stellar merger?
- step 3: Extract regional spectra and fit excitation (LTE then non-LTE)
  - method: Averaged spectra in 5 regions at 1'' beam; chi2 grid of Tex/Tkin and N with LTE then RADEX; Gaussian velocity components [5.1 The modeling procedure: "We used CASSIS and its $\chi^2$ minimization procedures plugged into RADEX"]
  - software: CASSIS, RADEX, CASA
  - parameter: beam filling factor 1.0 for almost all models [5.1 The modeling procedure: "The beam filling factor was set to 1.0 for almost all models."]
  - assumption: H2 main collisional partner; ortho/para 3; CMB 2.73 K only external radiation; isothermal homogeneous gas [5.1 The modeling procedure: "We assume that throughout the entire molecular nebula H$_2$ is the main collisional partner for all molecules."]
  - fitting: chi2 minimum on regular grid [5.1 The modeling procedure: "Physical parameters were identified within a regular grid of models through finding the $\chi^2$ minimum."]
  - validation: Compared with KMT17 results; model-vs-observed spectra for SO2 and CH3OH [5.4 Lobes: "The “integrated” column densities reported in KMT17 cannot be directly compared, but they are in reasonable quantitative agreement with our results."]
- result: Median temperature, central region = 17.1 ± not stated K [5.3 Temperatures: "The median temperature for species we modeled with the highest confidence is 17.1 K."]
- result: Median temperature, SW and NE lobes = 13.9 ± not stated K [5.4 Lobes SW and NE: "The median temperature in the SW and NE lobes is about 13.9 K"]
- result: H2 density from CH3OH in lobes = (1-20)e4 ± not stated cm^-3 [5.4 Excitation in the lobes: "Our models yield $n$(H$_2$) of $(1-20)\times10^4$ cm$^{-3}$."]
- limitation (authors): Errors underestimated; isothermal assumption fails in center; SO2 fits unsatisfactory [5.3 Excitation central region: "The errors are highly underestimated as they do not account for systematic errors"]
- limitation (authors): Beam filling factors set to 1; no collisions with e- and H [5.1 The modeling procedure: "collisions with electrons (and with atomic hydrogen) are not considered in our analysis"]
- not stated (card): Line-free channels and continuum-subtraction fit order; Self-calibration solution intervals and which datasets were self-calibrated; Cell size, image size, masks and clean thresholds; Exact transitions and velocity windows used for each molecule and region; Region polygons coordinates for the five regions; CASSIS grid ranges and steps for chi2 minimization; Per-line Gaussian fit parameters; Exact…

### 2020ApJ...900..131L: Ionized and Atomic Interstellar Medium in the z = 6.003 Quasar SDSS J2310+1855 (2020; agn_and_quasars, high_z_galaxies; observational_alma_primary)
- question: What are the physical conditions of the ionized and atomic ISM in the z=6.003 quasar J2310+1855, and is there an imprint of AGN heating, as probed by [N II] 122um and [O I] 146um together with [C II] and [O III]?
- step 3: Derive ionized and neutral gas masses and SFR
  - method: Minimum ionized mass from [N II] and [O III] LTE formula; C+ and O mass from [C II] and [O I]; SFR via Farrah et al. relations [4.1 Properties of J2310+1855: "The minimum ionized gas mass traced by singly ionized nitrogen is:"]
  - parameter: T_ex = T_kin = 228 K [4.1 Properties of J2310+1855: "adopting a gas temperature of $T_{\rm kin} = 228 \ \rm K$"]
  - assumption: Solar abundances (Asplund09); LTE [4.1 Properties of J2310+1855: "Assuming LTE where $T_{\rm kin} \approx T_{\rm ex}$"]
  - validation: Compared with CO(2-1) molecular gas mass and dust-continuum SFR [4.1 Properties of J2310+1855: "The SFRs traced by both the dust continuum and the \[C II\]$_{\rm 158 \mu m}$, \[N II\]$_{\rm 122 \mu m}$ and \[O III\]$_{\rm 88 \mu m}$ FIR FS lines are consistent"]
- result: Minimum ionized gas mass from [N II] = 6.2e8 ± not stated Msun [4.1 Properties of J2310+1855: "we derive a minimum ionized gas mass of $M^{min}_{ionized}= 6.2 \times 10^{8}$"]
- result: Minimum neutral gas mass from [C II] = 7.8e10 ± not stated Msun [4.1 Properties of J2310+1855: "we constrain the minimum atomic gas mass of $M^{min}_{neutral}= 7.8 \times 10^{10} \rm \ M_{\ensuremath{\odot}}$"]
- result: Minimum neutral gas mass from [O I] = 1.7e10 ± not stated Msun [4.1 Properties of J2310+1855: "which leads to $M^{min}_{neutral}= 1.7 \times 10^{10} \rm \ M_{\ensuremath{\odot}}$"]
- result: SFRs from [C II], [O I], [N II], [O III] = 1524, 11917, 2208, 1058 ± 1.8 to 2.6 dex statistical Msun/yr [4.1 Properties of J2310+1855: "are 1524, 11917, 2208, and 1058 $\rm M_{\ensuremath{\odot}}\ yr^{-1}$, respectively."]
- limitation (authors): SFR from [O I] unreliable; relations have large uncertainties and are extrapolated; dust opacity and XDR contribution may bias metallicity and [N II] results [4.1 Properties of J2310+1855: "The error bars of the parameters in the above relations are large, which result in large uncertainties in the SFR estimation."]
- not stated (card): CLEAN parameters: niter, threshold, masks, cell and image size; Line-free channels used for UVCONTSUB; Exact aperture centering and Gaussian fit details (priors, errors); Flux calibrator model and flux scale uncertainty; Method for deriving Sigma_FIR for high-z objects (sizes, L_FIR used); Cloudy model parameters used to infer density and C II fraction; Whether continuum from the three line-free …

### 2020ApJ...888L..28S: Estimating the Temperature and Density of a Spicule from 100 GHz Data Obtained with ALMA (2020; sun; observational_alma_primary)
- question: What are the temperature and density of a spicule seen at 100 GHz with ALMA, and how does it relate to spicules seen in IRIS Mg II and AIA 304 A?
- step 3: Optical depth vs temperature, observed and modeled
  - method: Observed tau = -ln(1-Tb/T); model free-free optical depth for assumed T and density with 0.5'' line-of-sight depth; intersection gives T and n [3 The spicules observed with ALMA, IRIS…: "The black line estimates from the observations and the colored line of the model cross when we assume the kinetic temperature of the plasma and the number density of ionized hydrogens"]
  - assumption: negligible background, T<10,000 K, thermal LTE electron-proton free-free emission [3 The spicules observed with ALMA, IRIS…: "2) the temperature range of the 100GHz spicule is lower than 10,000K, 3) the emission from the spicule is the thermal free-free emission"]
  - validation: Consistency with 193 A absorption and Rutten (2017) temperature range [3 The spicules observed with ALMA, IRIS…: "The temperature range is consistent with the temperature derived above, and thus, justifies our estimation."]
- result: Kinetic temperature = ~6800 ± not stated K [abstract: "the kinetic temperature of the plasma and the number density of ionized hydrogens in the 100GHz spicule are $\sim$6800 K"]
- result: Ionized hydrogen number density = 2.2e10 ± not stated cm^-3 [abstract: "$\rm 2.2\times10^{10} \ cm^{-3}$"]
- limitation (authors): Width comparable to beam, so the actual width may be narrower [3 The spicules observed with ALMA, IRIS…: "the actual width can be narrower than the value because the width is comparable to the size of the synthesized beam."]
- limitation (authors): Only relative brightness temperatures because single-dish data not combined [2 Observations: "in this study, we only deal with relative brightness temperatures."]
- not stated (card): Briggs robust value, cell size, image size, clean iterations; Pre-event reference time for background subtraction; Details of the free-free opacity formula and constants used; Number of antennas and array configuration; Which sources were used as calibrators

### 2025ApJ...986L..22R: The First Detection of Molecular Activity in the Largest Known Oort Cloud Comet: ALMA Imaging of C/2014 UN271 (Bernardinelli─Bernstein) at 16.6 au from the Sun (2025; solar_system; observational_alma_primary)
- question: What are the molecular activity drivers, CO outgassing kinematics and continuum (nucleus/dust) properties of the distant active Oort cloud comet C/2014 UN271 at 16.6 au?
- step 3: Fit CO line with 3D radiative transfer and derive production rates and scale lengths
  - method: SUBLIMED non-LTE model, two regions (jet and ambient), Haser distribution, vis_sample Fourier transform, least-squares fit to visibilities [Fourier Domain Modeling: "We then performed least-squares fits of our radiative transfer models against the measured interferometric visibilities."]
  - software: SUBLIMED, vis_sample, lmfit
  - parameter: Lp=0 assumed for geometry; free Q1,Q2,v1,v2,gamma,phi,psi [Fourier Domain Modeling: "allowing the molecular production rate, expansion speed, and jet geometry ($Q_1, Q_2, v_1, v_2, \gamma, \phi, \psi$) to vary as free parameters"]
  - assumption: Gas kinetic temperature 4 K [Fourier Domain Modeling: "We assumed a gas kinetic temperature $T_{\mathrm{kin}}$ = 4 K"]
  - assumption: H2CO-CO collision cross-section 5e-14 cm-2 (thermalization approximation) [4.1: "using an average collisional cross-section with CO of $5\times10^{-14}$ cm$^{-2}$"]
  - fitting: Levenberg-Marquardt least squares; uncertainties from covariance diagonal; Lp from delta chi2 curve (1 and 2.6 sigma at 1 and 6.63) [Fourier Domain Modeling: "We obtained the 1$\sigma$ and 2.6$\sigma$ uncertainties from the values for $\Delta\chi^2$ = 1 (68% confidence) and 6.63 (99% confidence) thresholds."]
  - validation: Checked for background CO sources with Planck maps and SIMBAD [4.1: "confirmed there were no known background sources within 100$\ensuremath{''}$"]
- result: Q(CO) March 8 (Lp<2500 km model) = 3.44 ± 0.55 1e27 s-1 [Table 1: "3.44 $\pm$ 0.55"]
- result: Q(CO) March 17 = 5.33 ± 0.88 1e27 s-1 [Table 1: "5.33 $\pm$ 0.88"]
- result: v1 sunward jet speed March 8 = 0.386 ± 0.006 km/s [Table 1: "0.386 $\pm$ 0.006"]
- result: Jet half-opening angle March 8 = 27 ± 5 deg [Table 1: "27 $\pm$ 5"]
- result: Lp 1 sigma upper limit March 8 = <2500 ± not stated km [4.1: "our 1$\sigma$ upper limit on $L_p$ ($<$2,500 km for March 8)"]
- result: Surface temperature from CO speed = 60 ± 2 (Mar 8), 3 (Mar 17) K [4.1.1: "give $T$ = $(60\pm2)$ K and $(60\pm3)$ K on March 8 and 17"]
- limitation (authors): Two-component model is a simplification of the dual-jet geometry; March 17 S/N lower [4.1.1: "Our two-component radiative transfer model is a simplification of this geometry"]
- not stated (card): Line-free channels and continuum subtraction method; Image pixel/cell size and image size; Exact spectral window frequencies and CO rest frequency; Initial guesses and bounds for lmfit fits; Choice of aperture/extraction for interferometric spectra fitted; Pipeline version; Calibrator catalog data used for polynomial fit details; Phase center coordinates

### 2017A&A...605A..78A: Center-to-limb observations of the Sun with ALMA . Implications for solar atmospheric models (2017; sun; archival_reuse)
- question: To derive information on the temperature structure of the solar chromosphere and compare it with existing models.
- step 4: Invert CLV to Te(tau)
  - method: Assumed Te = a1 + a2 ln tau; Tb(mu)=a1+a2(ln mu - gamma); least-squares fit; data reduced to common reference frequency using f^-2 absorption [Inversion of the center-to-limb curve: "The coefficients $a_1$ and $a_2$ can be determined by least square fit of the observations."]
  - parameter: ALMA data used up to theta~70 deg [Inversion of the center-to-limb curve: "we used ALMA measurements up to $\theta\simeq70$$^\circ$"]
  - assumption: LTE thermal free-free and H- absorption proportional to f^-2 [Inversion of the center-to-limb curve: "both the free-free and the H$^-$ absorption coefficients are proportional to $f^{-2}$"]
  - fitting: Least squares on logarithmic form; residual RMS ~60 K [Inversion of the center-to-limb curve: "The fit was very good, with an RMS of residuals of $\sim60$ K"]
  - validation: Adding a quadratic term did not change results; power series unstable; compared with Eddington-Barbier and models [Inversion of the center-to-limb curve: "the addition of a quadratic term in ([\[logform\]](#logform)) did not change appreciably either the data fit or the inversion results"]
- result: Global inversion slope a2 = -608 ± not stated K [Inversion of the center-to-limb curve: "The global inversion gave a slope of $a_2=-608$ K."]
- result: Slopes per band (100, 239, 343 GHz) = -608, -519, -818 ± not stated K [Inversion of the center-to-limb curve: "with slopes of $-608$, $-519$ and $-818$ K at 100, 239 and 343 GHz respectively"]
- limitation (authors): 100 GHz results 30-55'' from the limb may be affected by the 60'' beam [Summary and conclusions: "which may have been affected by the 60$''$ antenna beam"]
- not stated (card): Calibration and image reconstruction details of the Science Verification full-disk images (CASA version, procedure); Absolute flux scale/uncertainty; Pixel size and how limb irregularities and the ellipticity were corrected; Voigt fit parameters for diffuse-light correction; Exact mask thresholds; Details of the Fig 4 CLV binning and elliptical radius fitting; Handling of 230 vs 239 GHz naming an…

### 2026A&A...705A.198M: The ALMA survey to Resolve exoKuiper belt Substructures (ARKS): IV. CO gas imaging and overview (2026; debris_disks, astrochemistry; large_program_or_survey)
- question: What is the spectro-spatial distribution, optical depth and mass of CO gas in ARKS debris discs, and is CO detectable in the 13 discs without previous detections?
- step 5: Line fluxes and CO masses
  - method: Integrate stacked spectrum over V*±5 sigma (Gaussian fit); box integration for edge-on; optically thin LTE mass and tau=77 scaling [3.4 Flux and mass: "We set the limits of integration to $V_{*} \pm 5~\sigma$."]
  - software: GoFish
  - assumption: LTE with Tex equal to peak brightness temperature; tau12CO=77 from ISM 12C/13C [3.4 Flux and mass: "we calculate this assuming local thermodynamic equilibrium (LTE) and a CO excitation temperature equal to the peak-brightness temperature measured"]
  - fitting: Gaussian fit to stacked spectrum for centroid/width [3.3 stacking: "we fitted a Gaussian to the spectro-spatially stacked spectra"]
  - validation: Stellar velocity of HD 121617 compared with independent measurement, consistent within 3 sigma [3.3 stacking: "We found the two measured velocities to be consistent within $3~\sigma$ of each other."]
- result: 12CO J=3-2 integrated flux HD 9672 = 8.9 ± 0.9 Jy km/s [Table: "| HD 9672 | $3$ | 8.9 $\pm$ 0.9 | 3.0 $\pm$ 0.3"]
- result: 12CO integrated flux HD 32297 = 3.7 ± 0.4 Jy km/s [Table: "| HD 32297 | $68$ | 3.7 $\pm$ 0.4"]
- result: 12CO integrated flux HD 121617 = 3.6 ± 0.4 Jy km/s [Table: "| HD 121617 | $28$ | 3.6 $\pm$ 0.4"]
- result: 12CO integrated flux HD 131488 = 2.7 ± 0.3 Jy km/s [Table: "| HD 131488 | $6$ | 2.7 $\pm$ 0.3"]
- result: 12CO integrated flux HD 131835 = 1.9 ± 0.2 Jy km/s [Table: "| HD 131835 | $21$ | 1.9 $\pm$ 0.2"]
- result: Optically thin 12CO mass range = ~1-6e-4 ± not stated Earth masses [3.4 Flux and mass: "These values (Table [\[tab:linefluxesofgas\]](#tab:linefluxesofgas)) are of order $\sim1-6\times10^{-4}$ M$_{\oplus}$."]
- limitation (authors): Optically thick masses are lower limits; inner radii are upper limits; degeneracy thick/thin needs radiative transfer [4.2: "To break this degeneracy, radiative transfer modelling needs to be carried out"]
- not stated (card): Line-free channels / continuum subtraction approach for the line cubes; Exact nbeams and C value for each system; Clean mask thresholds and RMS estimation region; Which Measurement Sets / execution blocks per target; Gofish annulus/aperture radii used for each spectrum; Excitation temperatures per disc used in mass calculation

### 2019ApJ...883..193N: The ALMA Discovery of the Rotating Disk and Fast Outflow of Cold Molecular Gas in NGC 1275 (2019; agn_and_quasars, nearby_galaxies, galaxy_clusters_and_sz; observational_alma_primary)
- question: What are the morphology and kinematics of the cold molecular gas in the inner kpc to ~30 pc of NGC 1275, how is the AGN fed, what do the blue-shifted absorption features imply, and what is the SMBH mass from gas dynamics?
- step 5: Absorption optical depth and column density
  - method: tau from 40 mJy absorption against 7 Jy continuum; LTE, covering factor 1, Tex 100 K, HCN/H2 = 1e-9 [3.2 The HCN(3-2) and HCO+(3-2) Lines: "Under the assumption of the local thermodynamic equilibrium and a covering factor of 1, we obtain the H$_{2}$ column density of $2.3\times10^{22}$ cm$^{-2}$."]
  - assumption: HCN-H2 abundance 1e-9 [3.2 The HCN(3-2) and HCO+(3-2) Lines: "Here we assume a HCN-H$_{2}$ abundance ratio of $10^{-9}$ (cite: Smith2014)."]
  - validation: spectra on continuum-unsubtracted images and archival data [3.2 The HCN(3-2) and HCO+(3-2) Lines: "To check that these features are not an artifact caused by the process of continuum subtraction, we also show the spectrum measured on the continuum unsubtracted images"]
- result: H2 column density of absorber = 2.3e22 ± not stated cm^-2 [3.2 The HCN(3-2) and HCO+(3-2) Lines: "we obtain the H$_{2}$ column density of $2.3\times10^{22}$ cm$^{-2}$"]
- result: Absorption optical depth = 0.0057 ± not stated dimensionless [3.2 The HCN(3-2) and HCO+(3-2) Lines: "yielding the optical depth of 0.0057"]
- limitation (authors): Missing flux from lack of short baselines, so masses are lower limits [4.1 Filaments: "Note that the estimated mass should be a lower limit since the total emissions cannot be recovered because of the lack of short interferometric baselines."]
- limitation (authors): Residual is not a true chi2 because neighbouring pixels are correlated; modelling assumptions simple [5 Black Hole Mass: "This residual is useful to judge the fitting results but is not equivalent to the $\chi^{2}$, as the neighboring pixels in the observed cube are correlated."]
- not stated (card): Image sizes, cell sizes, cleaning thresholds and masks for tclean; Line-free channel ranges for uvcontsub; Self-calibration solution parameters and reference model; Exact reduction of archival 2013.1.01102.S data; mpfit settings and grid spacing for the SMBH search; MGE fit parameters and Gaussian components; Target coordinates

### 2015ApJ...798..124R: ALMA Observations of the Debris Disk around the Young Solar Analog HD 107146 (2015; debris_disks; observational_alma_primary)
- question: What is the radial distribution of mm-sized dust in the HD 107146 debris disk, and is there a gap or dip in the dust surface density?
- step 6: CO upper limit and planet mass from gap width
  - method: LTE CO column/mass upper limit from non-detection; chaotic/crossing zone relation for planet mass using gap width [7 The non-detection of CO: "we derived a $3\sigma$ upper limit for the mass of gaseous CO of $M_{\rm{CO}} < 1.9 \times 10^{-6}~M_{\oplus}$"]
  - parameter: Tex = 50 K, FWHM 1.9 km/s, inclination ~20 deg [7 The non-detection of CO: "uniform excitation temperature of 50 K throughout the disk"]
  - assumption: LTE [7 The non-detection of CO: "after assuming LTE"]
- result: CO mass 3σ upper limit (Tex=50 K) = 1.9e-6 ± not stated Earth masses [7 The non-detection of CO: "$M_{\rm{CO}} < 1.9 \times 10^{-6}~M_{\oplus}$"]
- result: Planet mass from gap, crossing zone (coefficient 2.1) = 6.1 ± +2.1/-3.1 Earth masses [9.1 A gap in the disk?: "We obtain $6.1^{+2.1}_{-3.1}~M_{\oplus}$ and $4.1^{+1.4}_{-2.1}~M_{\oplus}$"]
- limitation (authors): Data cannot distinguish between gap and double power-law forms; dust opacity degenerate with surface density [5.3 Double power-law: "The ALMA data presented in this paper do not allow us to distinguish between these possible different functional forms"]
- not stated (card): Number of emcee walkers and iterations (only 'several hundreds') and burn-in; Priors and bounds on model parameters; Clean threshold, mask, cell and image size of the CLEAN images; Whether CASA clean or other tools were used for the visibility extraction and weight rescaling in detail; Which spectral windows/channels were used for continuum (line-free channels excluded CO); Exact dust opacity tab…

### 2025A&A...696A.100G: PDRs4All: XII. Far-ultraviolet-driven formation of simple hydrocarbon radicals and their relation with polycyclic aromatic hydrocarbons (2025; milky_way_ism, astrochemistry, star_formation; observational_alma_primary)
- question: How are simple hydrocarbon radicals (C2H, C, CH_n) formed in the FUV-irradiated Orion Bar PDR, and are they linked to PAH aliphatic content traced by the 3.4/3.3 um AIB ratio?
- step 4: Beam-dilution correct single-dish C2H lines and build population diagram
  - method: Beam coupling factors from smoothed IRAM 30m and ALMA C2H 4-3 maps; rotational diagram fit with two temperatures [Beam dilution appendix: "The final beam coupling correction factor is $f_{\rm b}$ = $f_{\rm b}$(single-dish) $\cdot$$f_{\rm b}$(ALMA)."]
  - assumption: all C2H rotational lines share the same spatial distribution; optically thin [Beam dilution appendix: "we assume that the emission from all C$_2$H rotational lines have the same spatial distribution."]
  - fitting: two-component rotational diagram [C$_2$H rotational temperatures and $N$(…: "The resulting diagram (Fig. [21](#fig:DRs_corr_c2h)) can be fitted with two rotational temperature components, 22 $\pm$ 2 K and 59 $\pm$ 7 K"]
- step 5: Derive C2H and C column densities and abundances
  - method: Nonlocal non-LTE Monte Carlo radiative transfer grid in n_H and T_k; f(H2)=2/3; dust continuum excitation; new C-H2 rates to 3000 K [4.4: "we updated our nonlocal and non-LTE radiative transfer Monte Carlo model (cite: Goico22) to treat the rotational excitation of C$_2$H"]
  - parameter: T_k = 600 K upper limit; sigma_turb = 1 km/s [4.4: "Taking $T_{\rm k}$ = 600 K as an upper limit"]
  - assumption: dust modified blackbody, T=50 K, opacity 0.03(160/lambda)^1.6 [Nonlocal and non-LTE appendix: "with a color temperature of 50 K and a wavelength-dependent (in $\upmu$m) dust continuum opacity that varies as 0.03(160/$\lambda$)$^{1.6}$"]
  - validation: T_rot(C2H 4-3)=20-24 K agrees with population diagram [Nonlocal and non-LTE appendix: "in agreement with the rotational temperature inferred from a population diagram"]
- result: N(C2H) in DF3/DF4 = <=1e15 ± not stated cm^-2 [4.4: "$N$(C$_2$H) $\lesssim$ 10$^{15}$ cm$^{-2}$ and $n_{\rm H}$ of a few 10$^{5}$ cm$^{-3}$"]
- result: Peak [C2H] in DF3 = (2-4)e-7 ± not stated relative to H [4.4: "\[C$_2$H\] $\simeq$ (2–4)$\times$10$^{-7}$ in DF3"]
- result: N(C) at [CI] peak behind DF3 = 2e18 ± not stated cm^-2 [4.5: "We obtain $N$(C) $\simeq$ 2$\times$10$^{18}$ cm$^{-2}$"]
- result: Rotational temperatures of C2H at SDLS = 22 and 59 ± ±2 and ±7 K [C2H rotational temperatures appendix: "22 $\pm$ 2 K and 59 $\pm$ 7 K"]
- result: N(C2H) at SDLS = 7.3e14 ± ±1.3e14 cm^-2 [C2H rotational temperatures appendix: "$N$(C$_2$H) = (7.3 $\pm$1.3) $\times$ 10$^{14}$ cm$^{-2}$"]
- limitation (authors): Exact chemical pathways and relative contributions of bottom-up and top-down processes remain unquantified; models omit PAH chemistry [abstract: "the exact chemical pathways and their relative contributions remain to be quantified"]
- not stated (card): CASA version and pipeline version; flux, bandpass and phase calibrators and flux scale uncertainty; CLEAN threshold, masks, weighting, cell and image size; continuum subtraction and line-free channels; exact crosscut positions and widths; Monte Carlo radiative transfer model details and code availability; Meudon PDR grid inputs beyond Table 1

### 2024A&A...689A.317G: Continuum and molecular emission from the inner regions of the symbiotic system R Aquarii (2024; evolved_stars, astrochemistry, stellar_physics; observational_alma_primary)
- question: What do ALMA continuum, H30alpha and molecular line maps reveal about the inner regions of the symbiotic system R Aqr, and how are weak molecules distributed there?
- step 4: Model compact molecular emission (SiO v=0 J=16-15 example)
  - method: LTE ray-tracing model of expanding oblate shell plus in-falling spherical shell with dust and photosphere continuum, continuum subtracted, convolved with beam [5 Modeling: "Our model nebula consists of an oblate ellipsoidal shell in radial expansion for the emission and an in-falling spherical shell for the absorption"]
  - parameter: Power-law density and temperature; constant velocity [5 Modeling: "we assumed a constant radial velocity to simplify our calculations."]
  - assumption: LTE; optically thin Gaussian dust; SiO abundance 6.6e-6; distance 265 pc [5 Modeling: "We assumed local thermodynamic equilibrium (LTE) to obtain the coefficients of absorption and emission in each point of the circumstellar shells."]
  - fitting: Best fit found by manual variation of parameters [5 Modeling: "We found the best-fit model by manually varying the parameters to adjust the synthetic maps to the observations."]
  - validation: Qualitative comparison with channel maps of other lines; size uncertainty <20% (expanding), ~50% (in-falling) [5 Modeling: "We estimated that the uncertainty in the determination of the sizes of the expanding shell and in-falling component is smaller than 20% and $\sim$50%, respectively."]
- result: Expanding shell outer radius (equatorial) and expansion velocity = 1.6e14 cm; 9.0 km/s ± <20% cm; km/s [Table 4: "R$_{o.equ}$ (cm) | 1.6$\times$10$^{14}$ | 6$\times$10$^{13}$"]
- result: In-falling component velocity = -17 ± not stated km/s [5 Modeling: "we accurately derived velocities of 9 and $-$17 km s$^{-1}$ for the expanding and in-falling components, respectively."]
- result: Position angle of expanding shell projection = 105 ± not stated deg [5 Modeling: "the projection of the expanding shell is inclined at a PA of 105°"]
- limitation (authors): In-falling component size is not conclusive [5 Modeling: "Therefore, the obtained result concerning the size of the in-falling component is not conclusive."]
- not stated (card): Robust parameter values; Line-free channel ranges per spectral window; Self-calibration solution intervals and reference components; Cell and image sizes; CASA and GILDAS versions; Model code and fitting figure of merit; dust Gaussian parameters; Band 7 flux date inconsistency (November 2018 vs 2017)

### 2024ApJ...962....1S: Molecular Outflow in the Reionization-epoch Quasar J2054-0005 Revealed by OH 119 μm Observations (2024; agn_and_quasars, high_z_galaxies; observational_alma_primary)
- question: Does the z=6.04 quasar J2054-0005 host a molecular outflow traced by OH 119 μm, and how strong is it relative to star formation?
- step 4: Derive outflow mass and rate
  - method: Optical depth, LTE OH column density from equivalent width, N_H2 via abundance, thin shell M=mu mH N_H Omega r^2, Mdot=M v/r; empirical relation as check [4.2.1 Optically-thin outflow model: "Assuming that the outflow is expanding at velocity $v_\mathrm{out}$ as a thin spherical shell, the mass outflow rate averaged over the outflow lifetime can be expressed as"]
  - parameter: Tex=50 K, Q≈19, [OH]/[H2]=5e-7, f=0.3, r_out=2 kpc, v_out=669 km/s [Table 3: "using the covering factor $f=0.3$, outflow radius $r_\mathrm{out}=2~\mathrm{kpc}$, excitation temperature $T_\mathrm{ex}=50~\mathrm{K}$"]
  - assumption: OH abundance 5e-7 chosen as compromise and to match the empirical relation [4.1 Outflow mass: "Choosing this value is also motivated by the fact that it yields an outflow mass and mass outflow rate comparable to those obtained using an empirical relation"]
  - validation: Cross-check with empirical relation [4.2.2 Empirical relation: "are in agreement with those obtained under LTE and moderate OH abundance"]
- result: Outflow mass (LTE) = 4.9e9 ± not stated Msun [Table 3: "Mass $M_\mathrm{out}$ \[$M_\odot$\] | $4.9\times10^9$ | $4.5\times10^9$"]
- result: Mass outflow rate (LTE) = 1700 ± not stated Msun/yr [Table 3: "Mass outflow rate $\dot{M}_\mathrm{out}$ \[$M_\odot~\mathrm{yr^{-1}}$\] | $1700$ | $1500$"]
- result: OH column density = 7.5e15 ± not stated cm^-2 [Table 3: "Column density $N_\mathrm{OH}~[\mathrm{cm^{-2}}]$ | $7.5\times10^{15}$"]
- result: Mass loading factor = 2.2 ± not stated dimensionless [Table 3: "Mass loading factor $\eta$ | $2.2$ | $1.9$"]
- limitation (authors): Mass outflow rate uncertainty dominated by poorly constrained OH abundance [4.2.1: "Clearly, the uncertainty of the mass outflow rate is dominated by the poorly constrained OH abundance."]
- limitation (authors): Almost no line-free channels in USB; simple fitting assumptions [3.3: "Given the fact that there are almost no line-free channels in the USB spectrum and that fitting was done under simple assumptions"]
- not stated (card): Line-free channels/velocity ranges and fitting initial guesses for curve_fit; Exact tclean parameters (cell, image size, niter, automask thresholds); Which spectral extraction mask (>3σ continuum) exact definition; CASA and pipeline versions; CIGALE module parameter grids and version; Fitting data for Mdot-LIR relations (values for comparison sources, regression method); Self-calibration status

### 2020ApJ...894...76W: The MESAS Project: ALMA Observations of the F-type Stars γ Lep, γ Vir A, and γ Vir B (2020; stellar_physics, debris_disks; observational_alma_primary)
- question: What are the submm/mm fluxes and chromospheric structure of debris-poor F-type stars, and is there short-term variability or bias for debris disk studies?
- step 4: Fit semi-empirical chromosphere models
  - method: KINICH-PAKAL iteratively modifies temperature/density profiles, ionization and opacity of a solar base model to fit ALMA and Herschel data [3.3 Stellar atmosphere models: "This code iteratively modifies the radial temperature and hydrogen density profiles, the ionization balance, and the opacity of a base model using the Levenberg-Marquardt algorithm"]
  - software: KINICH-PAKAL
  - assumption: Non-LTE ionization-excitation and radiative transfer; hydrostatic equilibrium Avrett & Loeser solar starting model [3.3 Stellar atmosphere models: "we do not assume that ionization-excitation and radiative transfer are in local thermal equilibrium"]
  - fitting: Levenberg-Marquardt [3.3 Stellar atmosphere models: "using the Levenberg-Marquardt algorithm to adjust the synthetic spectrum"]
  - validation: Synthetic spectrum compared with observed [3.3 Stellar atmosphere models: "leading the synthethic spectrum to be in agreement with the observed one shown in Fig. [3](#tb_plot)"]
- result: gamma Lep temperature minimum = 4800 K at 750 km (Teff/TRmin = 0.76) ± not stated K [4.1 Semi-empirical chromospheric model: "we see a temperature minimum of T$_{R, min}$ = 4800 K (T$_{eff}$/T$_{R, min}$ = 0.76) at a height of 750 km above the photosphere"]
- limitation (authors): gamma Vir models lack constraints at other wavelengths; temperature minimum cannot be analyzed [4.1 Semi-empirical chromospheric model: "Therefore, it is not possible to perform an analysis of the temperature minimum in these two stars."]
- limitation (authors): Variability at longer timescales cannot be ruled out for gamma Lep [4.2 Potential millimeter wavelength var…: "we cannot rule out the possibility of variability at time periods longer than the length of the EBs."]
- not stated (card): CLEAN mask, niter, cell and image size; Whether pipeline products were used or manually re-imaged; spectral line flagging; uvmodelfit starting parameters; KINICH-PAKAL settings, convergence criteria and weighting of data points; Source of stellar parameters (footnotes a-e); How per-scan time series were binned and uncertainties assigned; Gamma Vir EB combination procedure

### 2018A&A...620A.119D: X-shooter and ALMA spectroscopy of GRB 161023A. A study of metals and molecules in the line of sight towards a luminous GRB (2018; transients, astrochemistry, high_z_galaxies; multi_facility_alma_minor)
- question: Use the GRB 161023A afterglow as a background source to study the host environment, molecular content (via ALMA mm spectroscopy) and intervening systems along the line of sight.
- step 2: Derive CO and HCO+ column density upper limits from ALMA non-detections
  - method: LTE absorption column density formula with integral of tau = 3 sigma_tau sqrt(DeltaV deltaV) [3.3.5 ALMA limits: "$$\begin{equation} \int\tau_{\nu}dV\simeq3\sigma_{\tau}\sqrt{\Delta V \delta V}, \end{equation}$$"]
  - parameter: delta v = 13 km/s; integral limit 3.9 km/s [3.3.5 ALMA limits: "Assuming a $\delta v=13$ km s$^{-1}$"]
  - assumption: Tx lower limit = CMB temperature 10.1 K (also 20 and 30 K tried) [3.3.5 ALMA limits: "$T_x=2.725(1+z)=10.1$ K"]
  - validation: Compared with X-shooter H2 and CO limits [abstract: "which are consistent with those that we obtain from the optical spectra"]
- result: log N(CO) upper limit from ALMA (Tx=10.1 K) = <15.7 ± not stated log cm^-2 [abstract: "$log(N_{CO}/cm^{-2})<15.7$ and $log(N_{HCO+}/cm^{-2})<13.2$"]
- result: log N(HCO+) upper limit from ALMA = <13.2 ± not stated log cm^-2 [abstract: "$log(N_{CO}/cm^{-2})<15.7$ and $log(N_{HCO+}/cm^{-2})<13.2$"]
- not stated (card): tclean parameters (cell, image size, masking, deconvolver) not given; Spectral rms and line width used to derive the 3.9 km/s optical-depth limit; How continuum was normalised for optical depth; Flux scale uncertainty; Line-free channels and continuum handling; Velocity width Delta V assumed for CO/HCO+ lines

### 2024ApJ...977..251H: Molecular Gas Mass Measurements of an Active, Starburst Galaxy at z ≍ 2.6 Using ALMA Observations of the [C I], CO, and Dust Emission (2024; high_z_galaxies, agn_and_quasars; observational_alma_primary)
- question: What are the molecular gas mass and ISM excitation conditions of a z=2.57 radio-loud starburst galaxy, as inferred from [CI], CO and dust emission?
- step 5: Derive molecular gas mass three ways
  - method: [CI] with LTE Tex, CO(4-3) with r41 and alpha_CO, Band 6 dust with Scoville2016 [3.3 Inference of molecular gas masses: "we are able to derive the molecular gas mass via three different independent approaches"]
  - assumption: X_CI=3e-5, r41=0.46, alpha_CO=0.8, Td=25 K, alpha_dust=6.7e19, helium factor 1.36 [3.3.3 The dust emission approach: "assuming a mass-weighted dust temperature of $\Td=25$ K"]
  - validation: Checked Q10=0.44±0.02 against Papadopoulos2022 value 0.48 [3.3.1 The Atomic Carbon approach: "Our value, $Q_{10}=0.44\,\pm\,0.02$, is 8 percent lower than (cite: Papadopoulos2022)’s suggested value."]
- result: Excitation temperature from [CI] = 44 ± 16 K [3.3.1 The Atomic Carbon approach: "$R\,=\,0.84\,\pm\,0.20$ and $\Tex=44\,\pm\,16$ K"]
- result: M_mol from [CI] = 3.1e11 ± 0.6e11 Msun [3.3.1 The Atomic Carbon approach: "$(3.1\pm0.6)\times10^{11}\text{M\ensuremath{_\odot}}$"]
- result: M_mol from CO(4-3) = 7.3e10 ± 0.9e10 Msun [3.3.2 The CO approach: "$(7.3\ \pm\ 0.9)\times10^{10}$M$_\odot$"]
- result: M_mol from Band 6 dust = 2.2e11 ± 0.2e11 Msun [3.3.3 The dust emission approach: "(2.2 $\pm$ 0.2)$\times10^{11}$M$_\odot$"]
- result: CO(7-6)/CO(4-3) ratio r74 = 0.34 ± 0.06 dimensionless [3.4 Line ratios: "$r_{74}=0.34\pm0.06$"]
- limitation (authors): Systematic uncertainties in X_CI, alpha_CO, r41, dust parameters [3.3.4 Uncertainties: "The molecular gas mass inferred using three different tracers are all subject to systematic uncertainties."]
- not stated (card): Spatial extent and orientation of the elliptical extraction aperture; Exact velocity ranges / channels used in spectral fits and moment maps; Line-free channels used for imcontsub; tclean cell size, image size, masks, threshold, niter; Rest frequencies adopted; Dust SED/Gamma_RJ value for Td=25 K; Initial guesses for Gaussian/imfit regions

### 2018ApJ...866L..12G: A Magnified View of Circumnuclear Star Formation and Feedback around an Active Galactic Nucleus at z = 2.6 (2018; high_z_galaxies, agn_and_quasars; observational_alma_primary)
- question: What are the resolved molecular gas properties on sub-kpc scales around the AGN in the lensed galaxy 9io9 at z=2.6, and does the AGN affect star formation in the circumnuclear ring?
- step 7: Deblend HNC/CN feature
  - method: Fit HNC(5-4)+CN(4-3) with shared Gaussian width and redshift, free amplitudes and constant continuum; CN LTE optically thin with CDMS intensities at 300 K [4.2 A possible dense molecular outflow: "We fit the spectrum allowing the HNC$(J=5\rightarrow 4)$ and CN$(N=4\rightarrow 3)$ amplitudes, $\sigma_{\rm dense}$ and redshift (assuming the same for both species) to vary as free parameters."]
  - assumption: LTE, optically thin, 300 K [4.2 A possible dense molecular outflow: "we assume local thermodynamic equilibrium and optically thin emission"]
  - validation: Noted deblending depends strongly on redshift (fixing z=2.5534 raises HNC) [4.2 A possible dense molecular outflow: "we caution the reader that the deblending is highly dependent on redshift."]
- result: Dense gas line width sigma = 289 ± 48 km/s [4.2 A possible dense molecular outflow: "$\sigma_{\rm dense}=(289\pm48)$ km s$^{-1}$"]
- limitation (authors): Deblending of HNC/CN depends strongly on redshift; outflow rate cannot be estimated; limited tracers [4.2 A possible dense molecular outflow: "deeper observations will be required to properly model the complex"]
- not stated (card): Line-free channels used for continuum subtraction; Cell size and image size; Mask definition for clean; Lens model priors, number of pixels, and Voronoi settings; galpak3d starting values and priors, and the code modification; Details of how HNC/CN fit was done (fitter, priors); Flux calibrator and flux scale uncertainty; Whether CASA pipeline version was recorded; Continuum flux measurement

### 2021ApJ...908..163M: Extremely Low Molecular Gas Content in the Vicinity of a Red Nugget Galaxy at z = 1.91 (2021; high_z_galaxies; observational_alma_primary)
- question: Is there molecular gas (via [C I]) in or around the compact quiescent galaxy GDS24569 that could drive further size evolution or explain its quenching?
- step 4: H2 mass upper limit
  - method: Papadopoulos et al. 2004 [CI] to M_H2 equation with 3 sigma limit [3.3 Upper limits in molecular gas mass: "By substituting these numbers in the equation above, we obtain a conservative $3\sigma$ upper limit on molecular hydrogen mass of $\sim7.1\times 10^{9}\,M_\odot$"]
  - parameter: Delta v = 300 km/s; Q10=0.5; A10=7.93e-8 s^-1; Helium factor 1.36 [3.3 Upper limits in molecular gas mass: "We set $\Delta v=300$ km / s based on stellar velocity dispersion measurements in massive compact quiescent galaxies"]
  - assumption: X[CI]=1.5e-5, Q10=0.5 (LTE, optically thin) [3.3 Upper limits in molecular gas mass: "We adopt the excitation factor $Q_{10}=0.5$ as a fiducial value, assuming local thermodynamic equilibrium"]
- result: 3 sigma upper limit on M_H2 = 7.1e9 ± not stated Msun [3.3 Upper limits in molecular gas mass: "$3\sigma$ upper limit on molecular hydrogen mass of $\sim7.1\times 10^{9}\,M_\odot$"]
- result: 3 sigma upper limit on [CI] integrated flux = 42 ± not stated mJy km/s/beam [3.3 Upper limits in molecular gas mass: "$S_{[\textrm{C}~\textsc{i}]}\Delta v\sim42$ mJy km / s / beam as a $3\sigma$ upper limit"]
- result: gas mass fraction upper limit = <5% ± not stated percent [3.3 Upper limits in molecular gas mass: "characterizing a significantly low gas mass fraction"]
- limitation (authors): Q10 cannot be constrained without other line ratios; the tentative line is not confirmed in Data1. [3.3 Upper limits in molecular gas mass: "none of these values can be constrained without line ratios to other excitation levels"]
- not stated (card): CASA version and calibration (pipeline vs manual); tclean deconvolver, weighting/robust, masking, cleaning threshold, image size; continuum subtraction and line-free channels; how the two datasets were combined; primary beam correction details; SED fitting priors, sampler settings, and star-formation-history parametrization; exact conversion of rms to 3-sigma flux limit

### 2020ApJ...890..167T: The Fifth Candidate for an Intermediate-mass Black Hole in the Galactic Center (2020; milky_way_ism; observational_alma_primary)
- question: What is the internal structure and kinematics of the high-velocity compact cloud HCN–0.085–0.094, and does it harbor an intermediate-mass black hole?
- step 4: Test protostellar outflow alternative
  - method: LTE gas mass from HCN, kinetic energy, compared with Spitzer 24 micron luminosity [Origin of T1: "The molecular gas mass of T1 was estimated to be approximately 2 $M_\odot$ according to the HCN intensity under the assumption of the local thermodynamic equilibrium (LTE)"]
  - assumption: Tex = 36 K, optically thin, [HCN]/[H2]=4.8e-8 [Origin of T1: "with an excitation temperature of 36 K in the optically thin limit (cite: takekawa17b) and a fractional abundance of $\rm [HCN]/[H_2] = 4.8\times10^{-8}$"]
- result: T1 LTE gas mass = ~2 ± not stated Msun [Origin of T1: "The molecular gas mass of T1 was estimated to be approximately 2 $M_\odot$"]
- limitation (authors): A single source of ~1e4 Msun cannot explain T2 and T3 kinematics; diffuse mass distribution possible [Indications: "However, there could be diffuse mass distribution around the point-like mass."]
- not stated (card): Channel ranges used for continuum estimation in uvcontsub; tclean cell size, image size, niter, threshold, masking; Number and positions of loci beyond the figure, and fit uncertainties' definition; Feathering parameters; Exact moment-map clipping thresholds; Fitting code for orbit and chi-square grid

## All papers in this technique

- 2012ApJ...749..162O (2012): Evidence for Multiple Pathways to Deuterium Enhancements in Protoplanetary Disks
- 2012ApJ...757..129R (2012): Kinematics of the CO Gas in the Inner Regions of the TW Hya Disk
- 2012ApJ...757L...4J (2012): Detection of the Simplest Sugar, Glycolaldehyde, in a Solar-type Protostar with ALMA
- 2013A&A...555A..73K (2013): ALMA detection of the rotating molecular disk wind from the young star HD 163296
- 2013A&A...557L..11B (2013): ALMA observations of the Red Rectangle, a preliminary analysis
- 2013ApJ...770..142N (2013): The Abundance of H<SUB>2</SUB>O and HDO in Orion Kl from Herschel/HIFI
- 2013ApJ...773L..34K (2013): Carbon Monoxide in the Cold Debris of Supernova 1987A
- 2013ApJ...774...16R (2013): A Spatially Resolved Vertical Temperature Gradient in the HD 163296 Disk
- 2013ApJ...774L...7M (2013): ALMA Observations of the Massive Molecular Outflow G331.512-0.103
- 2013ApJ...775L..31S (2013): ALMA Observations of the IRDC Clump G34.43+00.24 MM3: Hot Core and Molecular Outflows
- 2013ApJ...777...85N (2013): Deuterated Molecules in Orion KL from Herschel/HIFI
- 2013Natur.493..644B (2013): An old disk still capable of forming a planetary system
- 2014A&A...569A..11S (2014): A necklace of dense cores in the high-mass star forming region G35.20-0.74 N: ALMA observations
- 2014ApJ...785L..12C (2014): Spiral Arms in the Disk of HD 142527 from CO Emission Lines with ALMA
- 2014ApJ...786..114L (2014): ALMA Results of the Pseudodisk, Rotating Disk, and Jet in the Continuum and HCO<SUP>+</SUP> in the Protostellar System HH 212
- 2014ApJ...787..112C (2014): Herschel Observations of Extraordinary Sources: Analysis of the HIFI 1.2 THz Wide Spectral Survey toward Orion KL. I. Methods
- 2014ApJ...789L...4T (2014): ALMA Observations of a High-density Core in Taurus: Dynamical Gas Interaction at the Possible Site of a Multiple Star Formation
- 2014ApJ...791..123W (2014): A Study of Dynamical Processes in the Orion KL Region Using ALMA—Probing Molecular Outflow and Inflow
- 2014ApJ...793...37A (2014): From Gas to Stars in Energetic Environments: Dense Gas Clumps in the 30 Doradus Region within the Large Magellanic Cloud
- 2014ApJ...796....1T (2014): Angular Momentum Exchange by Gravitational Torques and Infall in the Circumbinary Disk of the Protostellar System L1551 NE
- 2014ApJ...796..131O (2014): Formation of a Keplerian Disk in the Infalling Envelope around L1527 IRS: Transformation from Infalling Motions to Kepler Motions
- 2014Sci...345.1584B (2014): Detection of a branched alkyl molecule in the interstellar medium: iso-propyl cyanide
- 2015A&A...581A..85P (2015): The jet and the disk of the HH 212 low-mass protostar imaged by ALMA: SO and SO<SUB>2</SUB> emission
- 2015A&A...582L...1T (2015): Searching for trans ethyl methyl ether in Orion KL⋆
- 2015A&A...582L...4M (2015): Detection of extragalactic argonium, ArH<SUP>+</SUP>, toward PKS 1830-211
- 2015ApJ...798...85P (2015): CO Gas Inside the Protoplanetary Disk Cavity in HD 142527: Disk Structure from ALMA
- 2015ApJ...798..124R (2015): ALMA Observations of the Debris Disk around the Young Solar Analog HD 107146
- 2015ApJ...799..204C (2015): Constraining the X-Ray and Cosmic-Ray Ionization Chemistry of the TW Hya Protoplanetary Disk: Evidence for a Sub-interstellar Cosmic-Ray Ra…
- 2015ApJ...801...63M (2015): ALMA Multi-line Imaging of the Nearby Starburst NGC 253
- 2015ApJ...803...60S (2015): ALMA Multi-line Observations of the IR-bright Merger VV 114
- 2015ApJ...803...70S (2015): ALMA Observations of the IRDC Clump G34.43+00.24 MM3: DNC/HNC Ratio
- 2015ApJ...803...97S (2015): An ALMA Imaging Study of Methyl Formate (HCOOCH<SUB>3</SUB>) in Torsionally Excited States toward Orion KL
- 2015ApJ...805..186L (2015): Jet Motion, Internal Working Surfaces, and Nested Shells in the Protostellar System HH 212
- 2015ApJ...811L...4Z (2015): Origin and Kinematics of the Eruptive Flow from XZ Tau Revealed by ALMA
- 2015ApJ...812...27A (2015): ALMA Observations of the Transition from Infall Motion to Keplerian Rotation around the Late-phase Protostar TMC-1A
- 2015ApJ...813...99F (2015): Weak Turbulence in the HD 163296 Protoplanetary Disk Revealed by ALMA CO Observations
- 2015ApJ...813L..19J (2015): A Keplerian-like Disk around the Forming O-type Star AFGL 4176
- 2015ApJ...815..106H (2015): Sgr B2(N): A Bipolar Outflow and Rotating Hot Core Revealed by ALMA
- 2015MNRAS.447.3936M (2015): CO mass upper limits in the Fomalhaut ring - the importance of NLTE excitation in debris discs and future prospects with ALMA
- 2015MNRAS.453.4324M (2015): ALMA reveals sunburn: CO dissociation around AGB stars in the globular cluster 47 Tucanae
- 2015PASJ...67....8N (2015): A multi-transition study of molecules toward NGC 1068 based on high-resolution imaging observations with ALMA
- 2015RAA....15.2213A (2015): <SUP>12</SUP>CO emission from the Red Rectangle
- 2016A&A...587A..91B (2016): Exploring molecular complexity with ALMA (EMoCA): Deuterated complex organic molecules in Sagittarius B2(N2)
- 2016A&A...587A..92M (2016): Exploring molecular complexity with ALMA (EMoCA): Alkanethiols and alkanols in Sagittarius B2(N2)
- 2016A&A...587A.145B (2016): A young bipolar outflow from IRAS 15398-3359
- 2016A&A...590A..93M (2016): Spectroscopic study and astronomical detection of doubly <SUP>13</SUP>C-substituted ethyl cyanide
- 2016A&A...591A.108O (2016): Azimuthal asymmetries in the debris disk around HD 61005. A massive collision of planetesimals?
- 2016A&A...593L..14F (2016): Magnetically regulated fragmentation of a massive, dense, and turbulent clump
- 2016A&A...595A..87M (2016): Laboratory spectroscopic study and astronomical detection of vibrationally excited n-propyl cyanide
- 2016A&A...595L...4L (2016): Hot methanol from the inner region of the HH 212 protostellar system
- 2016A&A...595L...7D (2016): ALMA reveals optically thin, highly excited CO gas in the jet-driven winds of the galaxy IC 5063
- 2016ApJ...818..156C (2016): A Disk-based Dynamical Constraint on the Mass of the Young Binary DQ Tau
- 2016ApJ...821...94K (2016): The Deuterium Fraction in Massive Starless Cores and Dynamical Implications
- 2016ApJ...823...91S (2016): The Radial Distribution of H<SUB>2</SUB> and CO in TW Hya as Revealed by Resolved ALMA Observations of CO Isotopologues
- 2016ApJ...823L..10W (2016): First Detection of Gas-phase Methanol in a Protoplanetary Disk
- 2016ApJ...823L..18H (2016): Evidence for a CO Desorption Front in the Outer AS 209 Disk
- 2016ApJ...824...88O (2016): Infalling-Rotating Motion and Associated Chemical Change in the Envelope of IRAS 16293-2422 Source A Studied with ALMA
- 2016ApJ...825...44I (2016): ALMA Investigation of Vibrationally Excited HCN/HCO<SUP>+</SUP>/HNC Emission Lines in the AGN-Hosting Ultraluminous Infrared Galaxy IRAS 20…
- 2016ApJ...825...79S (2016): Survey Observations of a Possible Glycine Precursor, Methanimine (CH2NH)
- 2016ApJ...826...26T (2016): Revealing a Detailed Mass Distribution of a High-density Core MC27/L1521F in Taurus with ALMA
- 2016ApJ...827...72S (2016): The Detection of a Hot Molecular Core in the Large Magellanic Cloud with ALMA
- 2016ApJ...829....6W (2016): ALMA Observations of HD 141569’s Circumstellar Disk
- 2016ApJ...830L..37I (2016): Discovery of a Hot Corino in the Bok Globule B335
- 2016ApJ...831...32N (2016): A Study of the Relation between Star Formation and Molecular Clumps on Subparsec Scales in 30 Doradus
- 2016ApJ...832..158Z (2016): ALMA Cycle 1 Observations of the HH46/47 Molecular Outflow: Structure, Entrainment, and Core Impact
- 2016ApJ...833...41Z (2016): High-resolution Observations of Molecular Lines in Arp 220: Kinematics, Morphology, and Limits on the Applicability of the Ammonia Thermome…
- 2016MNRAS.458.3134R (2016): ALMA observations of cold molecular gas filaments trailing rising radio bubbles in PKS 0745-191
- 2016MNRAS.459.3629I (2016): ALMA observations of the submillimetre hydrogen recombination line from the type 2 active nucleus of NGC 1068
- 2016MNRAS.460..627K (2016): The winds from HL Tau
- 2016MNRAS.460.2933M (2016): Exocometary gas in the HD 181327 debris ring
- 2016MNRAS.461..385B (2016): Determining the mid-plane conditions of circumstellar discs using gas and dust modelling: a study of HD 163296
- 2016MNRAS.463L..74K (2016): ALMA observations of the vibrationally excited rotational CO transition v = 1, J = 3 - 2 towards five AGB stars
- 2016PASJ...68..103F (2016): A massive dense gas cloud close to the nucleus of the Seyfert galaxy NGC 1068
- 2017A&A...597A..27S (2017): ALMA high spatial resolution observations of the dense molecular region of NGC 6302
- 2017A&A...597A..53L (2017): The ALMA-PILS survey: First detections of ethylene oxide, acetone and propanal toward the low-mass protostar IRAS 16293-2422
- 2017A&A...597L...5B (2017): A second post-AGB nebula that contains gas in rotation and in expansion: ALMA maps of IW Carinae
- 2017A&A...598A..53D (2017): Search for aluminium monoxide in the winds of oxygen-rich AGB stars
- 2017A&A...599A.101V (2017): Robustness of N<SUB>2</SUB>H<SUP>+</SUP> as tracer of the CO snowline
- 2017A&A...601A..49B (2017): Rotational spectroscopy, tentative interstellar detection, and chemical modeling of N-methylformamide
- 2017A&A...602A..42K (2017): Subarcsecond imaging of the water emission in Arp 220
- 2017A&A...602A..49H (2017): VALES. II. The physical conditions of interstellar gas in normal star-forming galaxies up to z = 0.2 revealed by ALMA
- 2017A&A...603A..10B (2017): Fragmentation and disk formation in high-mass star formation: The ALMA view of G351.77-0.54 at 0.06'' resolution
- 2017A&A...603L...6H (2017): Direct evidence of multiple reservoirs of volatile nitrogen in a protosolar nebula analogue
- 2017A&A...604L...2F (2017): The complexity of Orion: an ALMA view. II. gGg'-ethylene glycol and acetic acid
- 2017A&A...605A..21C (2017): Increased H<SUB>2</SUB>CO production in the outer disk around HD 163296
- 2017A&A...605A..28D (2017): The extended molecular envelope of the asymptotic giant branch star π<SUP>1</SUP> Gruis as seen by ALMA. I. Large-scale kinematic structure…
- 2017A&A...605A..78A (2017): Center-to-limb observations of the Sun with ALMA . Implications for solar atmospheric models
- 2017A&A...605L...6T (2017): Complex organic molecules in diffuse clouds along the line of sight to Sagittarius B2
- 2017A&A...606A.125S (2017): DCO<SUP>+</SUP>, DCN, and N<SUB>2</SUB>D<SUP>+</SUP> reveal three different deuteration regimes in the disk around the Herbig Ae star HD 16…
- 2017A&A...606L...7B (2017): Deuterated methanol on a solar system scale around the HH212 protostar
- 2017A&A...607L...5Q (2017): Clues to NaCN formation
- 2017A&A...608A..22A (2017): Luminous, pc-scale CO 6-5 emission in the obscured nucleus of NGC 1377
- 2017A&A...608A..38O (2017): Properties of the molecular gas in the fast outflow in the Seyfert galaxy IC 5063
- 2017AJ....153..233F (2017): ALMA Observations of Asymmetric Molecular Gas Emission from a Protoplanetary Disk in the Orion Nebula
- 2017ApJ...834....6S (2017): Merger-induced Shocks in the Nearby LIRG VV 114 through Methanol Observations with ALMA
- 2017ApJ...834..178Y (2017): Signs of Early-stage Disk Growth Revealed with ALMA
- 2017ApJ...835..108S (2017): Kinematic Structure of Molecular Gas around High-mass YSO, Papillon Nebula, in N159 East in the Large Magellanic Cloud: A New Perspective w…
- 2017ApJ...835..228T (2017): A Surface Density Perturbation in the TW Hydrae Disk at 95 au Traced by Molecular Emission
- 2017ApJ...837...60B (2017): The ALMA View of the OMC1 Explosion in Orion
- 2017ApJ...837...93Y (2017): Tidal Distortion of the Envelope of an AGB Star IRS 3 near Sgr A*
- 2017ApJ...837..174O (2017): L483: Warm Carbon-chain Chemistry Source Harboring Hot Corino Activity
- 2017ApJ...839...43O (2017): H<SUB>2</SUB>CO Distribution and Formation in the TW HYA Disk
- 2017ApJ...839...86H (2017): Radial Surface Density Profiles of Gas and Dust in the Debris Disk around 49 Ceti
- 2017ApJ...839L..14H (2017): Detection of Submillimeter-wave [C I] Emission in Gaseous Debris Disks of 49 Ceti and β Pictoris
- 2017ApJ...840....8S (2017): Luminous Infrared Galaxies with the Submillimeter Array. V. Molecular Gas in Intermediate to Late-stage Mergers
- 2017ApJ...840L..11S (2017): Extreme CO Isotopic Abundances in the ULIRG IRAS 13120-5453: An Extremely Young Starburst or Top-heavy Initial Mass Function
- 2017ApJ...842...94T (2017): ALMA View of the Galactic Center Minispiral: Ionized Gas Flows around Sagittarius A<SUP>∗</SUP>
- 2017ApJ...843...27L (2017): Formation and Atmosphere of Complex Organic Molecules of the HH 212 Protostellar Disk
- 2017ApJ...843..150F (2017): A Three-dimensional View of Turbulence: Constraints on Turbulent Motions in the HD 163296 Protoplanetary Disk Using DCO<SUP>+</SUP>
- 2017ApJ...846L..26W (2017): An ALMA Dynamical Mass Estimate of the Proposed Planetary-mass Companion FW Tau C
- 2017ApJ...847..108W (2017): Discovery of Striking Difference of Molecular-emission-line Richness in the Potential Proto-binary System NGC 2264 CMM3
- 2017ApJ...848..101V (2017): A <SUP>13</SUP>CO Detection in a Brightest Cluster Galaxy
- 2017ApJ...849...56A (2017): ALMA Observations of the Protostar L1527 IRS: Probing Details of the Disk and the Envelope Structures
- 2017ApJ...849...68S (2017): Very Large Array Ammonia Observations of the HH 111/HH 121 Protostellar System: A Detection of a New Source with a Peculiar Chemistry
- 2017ApJ...850...35L (2017): Solar ALMA Observations: Constraining the Chromosphere above Sunspots
- 2017ApJ...850L...2A (2017): ALMA Observations of SMM11 Reveal an Extremely Young Protostar in Serpens Main Cluster
- 2017ApJ...850L..30Y (2017): ALMA Detection of Bipolar Outflows: Evidence for Low-mass Star Formation within 1 pc of Sgr A*
- 2017ApJ...851..132C (2017): The Architecture of the GW Ori Young Triple-star System and Its Disk: Dynamical Masses, Mutual Inclinations, and Recurrent Eclipses
- 2017ApJS..233...11B (2017): Rotational and High-resolution Infrared Spectrum of HC<SUB>3</SUB>N: Global Ro-vibrational Analysis and Improved Line Catalog for Astrophys…
- 2017Icar..286..289L (2017): Detection of CO and HCN in Pluto's atmosphere with ALMA
- 2017MNRAS.465.2595M (2017): ALMA observations of the η Corvi debris disc: inward scattering of CO-rich exocomets by a chain of 3-30 M<SUB>⊕</SUB> planets?
- 2017MNRAS.466...49J (2017): Optical depth estimates and effective critical densities of dense gas tracers in the inner parts of nearby galaxy discs
- 2017MNRAS.467L.120M (2017): The ALMA view of W33A: a spiral filament feeding the candidate disc in MM1-Main
- 2017MNRAS.469.2230M (2017): Detection of methyl isocyanate (CH<SUB>3</SUB>NCO) in a solar-type protostar
- 2017MNRAS.469.3347M (2017): ALMA spectral survey of Supernova 1987A - molecular inventory, chemistry, dynamics and explosive nucleosynthesis
- 2017MNRAS.469.3518M (2017): ALMA observations of the multiplanet system 61 Vir: what lies outside super-Earth systems?
- 2017NatAs...1E.130Z (2017): Mass inventory of the giant-planet formation zone in a solar nebula analogue
- 2017PASJ...69...18T (2017): A statistical study of giant molecular clouds traced by <SUP>13</SUP>CO, C<SUP>18</SUP>O, CS, and CH<SUB>3</SUB>OH in the disk of NGC 1068 …
- 2018A&A...609A..47P (2018): Direct mapping of the temperature and velocity gradients in discs. Imaging the vertical CO snow line around IM Lupi
- 2018A&A...612A..72J (2018): The ALMA-PILS survey: 3D modeling of the envelope, disks and dust filament of IRAS 16293-2422
- 2018A&A...612L..11S (2018): Detection of CI line emission towards the oxygen-rich AGB star omi Ceti
- 2018A&A...614A..42M (2018): ALMA observations of AGN fuelling. The case of PKS B1718-649
- 2018A&A...614A..58B (2018): High-resolution observations of IRAS 08544-4431. Detection of a disk orbiting a post-AGB star and of a slow disk wind
- 2018A&A...614A.106C (2018): Probing midplane CO abundance and gas temperature with DCO<SUP>+</SUP> in the protoplanetary disk around HD 169142
- 2018A&A...614A.123P (2018): The physical and chemical structure of Sagittarius B2. III. Radiative transfer simulations of the hot core Sgr B2(M) for methyl cyanide
- 2018A&A...615A..28D (2018): ALMA spectral line and imaging survey of a low and a high mass-loss rate AGB star between 335 and 362 GHz
- 2018A&A...615A..83V (2018): Unveiling the physical conditions of the youngest disks. A warm embedded disk in L1527
- 2018A&A...615A.141B (2018): Accelerating infall and rotational spin-up in the hot molecular core G31.41+0.31
- 2018A&A...615L..10M (2018): Unlocking the secrets of the midplane gas and dust distribution in the young hybrid disc HD 141569
- 2018A&A...616A..90C (2018): The ALMA-PILS survey: complex nitriles towards IRAS 16293-2422
- 2018A&A...617A..23B (2018): Molecular line study of the S-type AGB star W Aquilae. ALMA observations of CS, SiS, SiO and HCN
- 2018A&A...617A..54L (2018): Molecular gas and dark neutral medium in the outskirts of Chamaeleon
- 2018A&A...617A.120M (2018): Tracing the cold and warm physico-chemical structure of deeply embedded protostars: IRAS 16293-2422 vs. VLA 1623-2417
- 2018A&A...619A..28L (2018): The ALMA-PILS survey: Stringent limits on small amines and nitrogen-oxides towards IRAS 16293-2422B
- 2018A&A...619A.140V (2018): Millimeter-wave spectroscopy and modeling of 1,2-butanediol . Laboratory spectrum in the 59.6-103.6 GHz region and comparison with the ALMA…
- 2018A&A...620A..75K (2018): High-resolution observations of gas and dust around Mira using ALMA and SPHERE/ZIMPOL
- 2018A&A...620A.119D (2018): X-shooter and ALMA spectroscopy of GRB 161023A. A study of metals and molecules in the line of sight towards a luminous GRB
- 2018A&A...620A.170J (2018): The ALMA-PILS survey: isotopic composition of oxygen-containing complex organic molecules toward IRAS 16293-2422B
- 2018A&A...620L...6T (2018): Chemical segregation of complex organic O-bearing species in Orion KL
- 2018ApJ...852..122H (2018): CO and Dust Properties in the TW Hya Disk from High-resolution ALMA Observations
- 2018ApJ...853..147M (2018): Molecular Reconnaissance of the β Pictoris Gas Disk with the SMA: A Low HCN/(CO+CO<SUB>2</SUB>) Outgassing Ratio and Predictions for Future…
- 2018ApJ...853L..19S (2018): The Detection of Hot Cores and Complex Organic Molecules in the Large Magellanic Cloud
- 2018ApJ...855..113D (2018): Constraints on Metal Oxide and Metal Hydroxide Abundances in the Winds of AGB Stars: Potential Detection of FeO in R Dor
- 2018ApJ...856...14L (2018): A 100 au Wide Bipolar Rotating Shell Emanating from the HH 212 Protostellar Disk: A Disk Wind?
- 2018ApJ...856...97S (2018): Dense Molecular Gas in the Starburst Nucleus of NGC 1808
- 2018ApJ...856..117F (2018): Turbulence in the TW Hya Disk
- 2018ApJ...856..147O (2018): Gravitationally Unstable Condensations Revealed by ALMA in the TUKH122 Prestellar Core in the Orion A Cloud
- 2018ApJ...857...35S (2018): ALMA Observations of the IRDC Clump G34.43+00.24 MM3: Complex Organic and Deuterated Molecules
- 2018ApJ...859..111H (2018): The Circumstellar Disk and Asymmetric Outflow of the EX Lup Outburst System
- 2018ApJ...859..131L (2018): The Distribution and Excitation of CH<SUB>3</SUB>CN in a Solar Nebula Analog
- 2018ApJ...859L..15C (2018): Interferometric Imaging of Titan’s HC<SUB>3</SUB>N, H<SUP>13</SUP>CCCN, and HCCC<SUP>15</SUP>N
- 2018ApJ...861...72C (2018): ALMA Resolves C I Emission from the β Pictoris Debris Disk
- 2018ApJ...862....8T (2018): Warm CO Gas Generated by Possible Turbulent Shocks in a Low-mass Star-forming Dense Core in Taurus
- 2018ApJ...862L...2F (2018): First Detection of the Simplest Organic Acid in a Protoplanetary Disk
- 2018ApJ...863...19A (2018): The Distinct Evolutionary Nature of Two Class 0 Protostars in Serpens Main SMM4
- 2018ApJ...863..129S (2018): Spatially Resolved Dense Molecular Gas Excitation in the Nearby LIRG VV 114
- 2018ApJ...863..143C (2018): ALMA [C I]<SUP>3</SUP> P <SUB>1</SUB>-<SUP>3</SUP> P <SUB>0</SUB> Observations of NGC 6240: A Puzzling Molecular Outflow, and the Role of O…
- 2018ApJ...863L..35M (2018): First Results of an ALMA Band 10 Spectral Line Survey of NGC 6334I: Detections of Glycolaldehyde (HC(O)CH<SUB>2</SUB>OH) and a New Compact …
- 2018ApJ...864..133T (2018): Temperature, Mass, and Turbulence: A Spatially Resolved Multiband Non-LTE Analysis of CS in TW Hya
- 2018ApJ...864..170G (2018): H<SUB>2</SUB>CO Ortho-to-para Ratio in the Protoplanetary Disk HD 163296
- 2018ApJ...866..141K (2018): Extremely Dense Cores Associated with Chandra Sources in Ophiuchus A: Forming Brown Dwarfs Unveiled?
- 2018ApJ...866L..12G (2018): A Magnified View of Circumnuclear Star Formation and Feedback around an Active Galactic Nucleus at z = 2.6
- 2018ApJ...867...48I (2018): Circumnuclear Multiphase Gas in the Circinus Galaxy. II. The Molecular and Atomic Obscuring Structures Revealed with ALMA
- 2018ApJ...867..165B (2018): Dense Molecular Filaments Feeding a Starburst: ALMA Maps of CO(3-2) in Henize 2-10
- 2018ApJ...867L...6B (2018): Evidence for the First Extragalactic Hydrogen Recombination Line Maser in NGC 253
- 2018ApJ...868...80C (2018): The Physical and Chemical Properties of the ρ Ophiuchi A Dense Core
- 2018ApJ...868...95M (2018): ALMA Observations of HCN and HCO<SUP>+</SUP> Outflows in the Merging Galaxy NGC 3256
- 2018ApJ...869...59W (2018): Physical and Chemical Conditions of the Protostellar Envelope and the Protoplanetary Disk in HL Tau
- 2018ApJ...869...75M (2018): ALMA Detection of Extended Millimeter Halos in the HD 32297 and HD 61005 Debris Disks
- 2018MNRAS.474.4988S (2018): A disrupted molecular torus around Eta Carinae as seen in <SUP>12</SUP>CO with ALMA
- 2018MNRAS.475..448T (2018): Mapping jet-ISM interactions in X-ray binaries with ALMA: a GRS 1915+105 case study
- 2018MNRAS.475.5322S (2018): Deuterated formaldehyde in the low-mass protostar HH212
- 2018MNRAS.478.2505I (2018): Radiative transfer modelling of W33A MM1: 3D structure and dynamics of a complex massive star-forming region
- 2018PASJ...70...85T (2018): ALMA view of the circumnuclear disk of the Galactic Center: tidally disrupted molecular clouds falling to the Galactic Center
- 2018PASJ...70L...1M (2018): ALMA [C I] observations toward the central region of Seyfert galaxy NGC 613
- 2019A&A...622A.206M (2019): A 10-M<SUB>☉</SUB> YSO with a Keplerian disk and a nonthermal radio jet
- 2019A&A...623A..68T (2019): Small-scale physical and chemical structure of diffuse and translucent molecular clouds along the line of sight to Sgr B2
- 2019A&A...623A..93C (2019): Laboratory spectroscopic study of the <SUP>15</SUP>N isotopomers of cyanamide, H<SUB>2</SUB>NCN, and a search for them toward IRAS 16293-24…
- 2019A&A...623A..96Y (2019): Signs of outflow feedback from a nearby young stellar object on the protostellar envelope around HL Tauri
- 2019A&A...623A.124C (2019): Upper limits on CH<SUB>3</SUB>OH in the HD 163296 protoplanetary disk. Evidence for a low gas-phase CH<SUB>3</SUB>OH-to-H<SUB>2</SUB>CO rat…
- 2019A&A...623L...1K (2019): Detection of highly excited OH towards AGB stars. A new probe of shocked gas in the extended atmospheres
- 2019A&A...623L...6P (2019): Organic molecules in the protoplanetary disk of DG Tauri revealed by ALMA
- 2019A&A...624A..70C (2019): Astrophysical detections and databases for the mono deuterated species of acetaldehyde CH<SUB>2</SUB>DCOH and CH<SUB>3</SUB>COD
- 2019A&A...624A..82B (2019): Methylamine and other simple N-bearing species in the hot cores NGC 6334I MM1-3
- 2019A&A...624A.125M (2019): Spatially resolved carbon and oxygen isotopic ratios in NGC 253 using optically thin tracers
- 2019A&A...625A.118K (2019): Highly structured disk around the planet host PDS 70 revealed by high-angular resolution observations with ALMA
- 2019A&A...627A...1Q (2019): Formation of interstellar propanal and 1-propanol ice: a pathway involving solid-state CO hydrogenation
- 2019A&A...627A.114K (2019): Massive dust clumps in the envelope of the red supergiant VY Canis Majoris
- 2019A&A...628A..10B (2019): Re-exploring Molecular Complexity with ALMA (ReMoCA): interstellar detection of urea
- 2019A&A...628A..27B (2019): The complex chemistry of hot cores in Sgr B2(N): influence of cosmic-ray ionization and thermal history
- 2019A&A...629A...6T (2019): ALMA view of the <SUP>12</SUP>C/<SUP>13</SUP>C isotopic ratio in starburst galaxies
- 2019A&A...629A..72O (2019): Laboratory rotational spectroscopy of isotopic acetone, CH<SUB>3</SUB><SUP>13</SUP>C(O)CH<SUB>3</SUB> and <SUP>13</SUP>CH<SUB>3</SUB>C(O)CH…
- 2019A&A...629A..75B (2019): First detections of H<SUP>13</SUP>CO<SUP>+</SUP> and HC<SUP>15</SUP>N in the disk around HD 97048. Evidence for a cold gas reservoir in the…
- 2019A&A...631A..25J (2019): ALMA observations of water deuteration: a physical diagnostic of the formation of protostars
- 2019A&A...631A..64B (2019): Kinematics around the B335 protostar down to au scales
- 2019A&A...632A..19T (2019): Interferometric observations of warm deuterated methanol in the inner regions of low-mass protostars
- 2019A&A...632A.101T (2019): Chemical and kinematic structure of extremely high-velocity molecular jets in the Serpens Main star-forming region
- 2019A&A...632L..12H (2019): Multiple nitrogen reservoirs in a protoplanetary disk at the epoch of comet and giant planet formation
- 2019AJ....157..117M (2019): On the Ubiquity and Stellar Luminosity Dependence of Exocometary CO Gas: Detection around M Dwarf TWA 7
- 2019AJ....157..251T (2019): Neptune's Latitudinal Variations as Viewed with ALMA
- 2019AJ....158..162F (2019): From Scattered-light to Millimeter Emission: A Comprehensive View of the Gigayear-old System of HD 202628 and its Eccentric Debris Ring
- 2019ApJ...870L..26C (2019): ALMA Autocorrelation Spectroscopy of Comets: The HCN/H<SUP>13</SUP>CN Ratio in C/2012 S1 (ISON)
- 2019ApJ...871....5T (2019): The Flared Gas Structure of the Transitional Disk around Sz 91
- 2019ApJ...871..100H (2019): ALMA Observations of the Protostellar Disk around the VeLLO IRAS 16253-2429
- 2019ApJ...871..112X (2019): ALMA Observations of the Spatial Distribution of Three C<SUB>2</SUB>H<SUB>4</SUB>O<SUB>2</SUB> Isomers toward Sgr B2(N)
- 2019ApJ...871..170M (2019): Fire in the Heart: A Characterization of the High Kinetic Temperatures and Heating Sources in the Nucleus of NGC 253
- 2019ApJ...872...92F (2019): The Planet Formation Potential around a 45 Myr Old Accreting M Dwarf
- 2019ApJ...872..121U (2019): Molecular Cloud Cores in the Galactic Center 50 km s<SUP>-1</SUP> Molecular Cloud
- 2019ApJ...872..196S (2019): Implications of a Hot Atmosphere/Corino from ALMA Observations toward NGC 1333 IRAS 4A1
- 2019ApJ...872..200H (2019): ALMA Observations of the Massive Molecular Outflow G331.512-0.103. II. Physical Properties, Kinematics, and Geometry Modeling
- 2019ApJ...875...24C (2019): Filamentary Accretion Flows in the Infrared Dark Cloud G14.225-0.506 Revealed by ALMA
- 2019ApJ...875...62Y (2019): ALMA Observations of Layered Structures due to CO Selective Dissociation in the ρ Ophiuchi A Plane-parallel PDR
- 2019ApJ...876...72L (2019): Sulfur Chemistry in Protoplanetary Disks: CS and H<SUB>2</SUB>CS
- 2019ApJ...876L..13S (2019): Line Ratios Reveal N<SUB>2</SUB>H<SUP>+</SUP> Emission Originates above the Midplane in TW Hydrae
- 2019ApJ...877L..25M (2019): The First Bird’s-eye View of a Gravitationally Unstable Accretion Disk in High-mass Star Formation
- 2019ApJ...877L..32M (2019): Multiple Rings of Millimeter Dust Emission in the HD 15115 Debris Disk
- 2019ApJ...880..130M (2019): A New, Rotating Hot Corino in Serpens
- 2019ApJ...882..118X (2019): ALMA Detection of Vibrationally Excited (v <SUB>t</SUB> = 1, 2) Acetic Acid toward NGC 6334I
- 2019ApJ...882..160Q (2019): Probing CO and N<SUB>2</SUB> Snow Surfaces in Protoplanetary Disks with N<SUB>2</SUB>H<SUP>+</SUP> Emission
- 2019ApJ...882L..31B (2019): The First Detection of <SUP>13</SUP>C<SUP>17</SUP>O in a Protoplanetary Disk: A Robust Tracer of Disk Gas Mass
- 2019ApJ...883...98Z (2019): Systematic Variations of CO Gas Abundance with Radius in Gas-rich Protoplanetary Disks
- 2019ApJ...883..193N (2019): The ALMA Discovery of the Rotating Disk and Fast Outflow of Cold Molecular Gas in NGC 1275
- 2019ApJ...885...82L (2019): Sulfur-bearing Molecules in Orion KL
- 2019ApJ...885L..39H (2019): First Detection of Submillimeter-wave [<SUP>13</SUP>C I] <SUP>3</SUP> P <SUB>1</SUB>-<SUP>3</SUP> P <SUB>0</SUB> Emission in a Gaseous Debr…
- 2019ApJ...886....6T (2019): The VLA/ALMA Nascent Disk and Multiplicity (VANDAM) Survey of Orion Protostars. I. Identifying and Characterizing the Protostellar Content …
- 2019ApJ...886...14F (2019): An ALMA View of Molecular Filaments in the Large Magellanic Cloud. I. The Formation of High-mass Stars and Pillars in the N159E-Papillon Ne…
- 2019ApJ...886...15T (2019): An ALMA View of Molecular Filaments in the Large Magellanic Cloud. II. An Early Stage of High-mass Star Formation Embedded at Colliding Clo…
- 2019ApJ...886L...4Z (2019): Discovery of a Photoionized Bipolar Outflow toward the Massive Protostar G45.47+0.05
- 2019ApJ...887..209A (2019): Protostellar Evolution in Serpens Main: Possible Origin of Disk-size Diversity
- 2019ESC.....3.2088S (2019): Complex Organic Molecules in Star-Forming Regions of the Magellanic Clouds
- 2019MNRAS.484.1257M (2019): A gap in HD 92945's broad planetesimal disc revealed by ALMA
- 2019MNRAS.485..229R (2019): Deep and narrow CO absorption revealing molecular clouds in the Hydra-A brightest cluster galaxy
- 2019MNRAS.485..739M (2019): Asymmetric mid-plane gas in ALMA images of HD 100546
- 2019MNRAS.485.2457H (2019): `The Brick' is not a brick: a comprehensive study of the structure and dynamics of the central molecular zone cloud G0.253+0.016
- 2019MNRAS.486.4114R (2019): ALMA reveals a pseudo-disc in a proto-brown dwarf
- 2019MNRAS.490.1570B (2019): The peculiar chemistry of the inner ejecta of Eta Carina
- 2019NatAs...3..314L (2019): The ice composition in the disk around V883 Ori revealed by its stellar outburst
- 2019NatAs...3..517Z (2019): Dynamics of a massive binary at birth
- 2019NatAs...3.1109P (2019): Kinematic detection of a planet carving a gap in a protoplanetary disk
- 2019PASJ...71...44H (2019): Formation of high-mass stars in an isolated environment in the Large Magellanic Cloud
- 2019PASJ...71...68K (2019): A Chandra and ALMA study of X-ray-irradiated gas in the central ∼100 pc of the Circinus galaxy
- 2019PASJ...71..105T (2019): Rotating ionized gas ring around the Galactic center IRS13E3
- 2020A&A...633A..13D (2020): The extended molecular envelope of the asymptotic giant branch star π<SUP>1</SUP> Gruis as seen by ALMA. II. The spiral-outflow observed at…
- 2020A&A...634L..12D (2020): ALMA reveals a large structured disk and nested rotating outflows in DG Tauri B
- 2020A&A...635A..48M (2020): The ALMA-PILS survey: inventory of complex organic molecules towards IRAS 16293-2422 A
- 2020A&A...635A.189F (2020): Seeds of Life in Space (SOLIS). VII. Discovery of a cold dense methanol blob toward the L1521F VeLLO system
- 2020A&A...636A..67A (2020): Exploring the formation pathways of formamide. Near young O-type stars
- 2020A&A...641A.104A (2020): Studying star-forming processes at core and clump scales: the case of the young stellar object G29.862-0.0044
- 2020A&A...641A.160M (2020): Far-infrared laboratory spectroscopy of aminoacetonitrile and first interstellar detection of its vibrationally excited transitions
- 2020A&A...643A..89P (2020): Excitation and acceleration of molecular outflows in LIRGs: The extended ESO 320-G030 outflow on 200-pc scales
- 2020A&A...644A..59K (2020): Molecular remnant of Nova 1670 (CK Vulpeculae). I. Properties and enigmatic origin of the gas
- 2020A&A...644A..84M (2020): The GUAPOS project: G31.41+0.31 Unbiased ALMA sPectral Observational Survey. I. Isomers of C<SUB>2</SUB>H<SUB>4</SUB>O<SUB>2</SUB>
- 2020A&A...644A.119P (2020): ALMA chemical survey of disk-outflow sources in Taurus (ALMA-DOT). III. The interplay between gas and dust in the protoplanetary disk of DG…
- 2020AJ....159...62C (2020): ALMA Observations of the Extraordinary Carina Pillars: HH 901/902
- 2020AJ....159..288M (2020): The Big Sibling of AU Mic: A Cold Dust-rich Debris Disk around CP-72 2713 in the β Pic Moving Group
- 2020ApJ...888L..28S (2020): Estimating the Temperature and Density of a Spicule from 100 GHz Data Obtained with ALMA
- 2020ApJ...889...43Z (2020): Dense Cores, Filaments, and Outflows in the S255IR Region of High-mass Star Formation
- 2020ApJ...890...76N (2020): ALMA Observations of Two Massive and Dense MALT90 Clumps
- 2020ApJ...890..129K (2020): Detection of Irregular, Submillimeter Opaque Structures in the Orion Molecular Clouds: Protostars within 10,000 yr of Formation?
- 2020ApJ...890..142P (2020): An ALMA Survey of H<SUB>2</SUB>CO in Protoplanetary Disks
- 2020ApJ...890..167T (2020): The Fifth Candidate for an Intermediate-mass Black Hole in the Galactic Center
- 2020ApJ...891..164S (2020): Chemistry and Physics of a Low-metallicity Hot Core in the Large Magellanic Cloud
- 2020ApJ...891L...8M (2020): The Formation Height of Millimeter-wavelength Emission in the Solar Chromosphere
- 2020ApJ...892...99C (2020): The Surprisingly Low Carbon Mass in the Debris Disk around HD 32297
- 2020ApJ...894...76W (2020): The MESAS Project: ALMA Observations of the F-type Stars γ Lep, γ Vir A, and γ Vir B
- 2020ApJ...895..119T (2020): ALMA ACA and Nobeyama Observations of Two Orion Cores in Deuterated Molecular Lines
- 2020ApJ...896...35J (2020): A Detailed View of the Circumstellar Environment and Disk of the Forming O-star AFGL 4176
- 2020ApJ...897L..33J (2020): The Ionized Warped Disk and Disk Wind of the Massive Protostar Monoceros R2-IRS2 Seen with ALMA
- 2020ApJ...898...10T (2020): Circumbinary Disks of the Protostellar Binary Systems in the L1551 Region
- 2020ApJ...898...54T (2020): Chemical Composition in the IRAS 16562-3959 High-mass Star-forming Region
- 2020ApJ...898...61I (2020): Circumnuclear Molecular Gas in Low-redshift Quasars and Matched Star-forming Galaxies
- 2020ApJ...898...75I (2020): ALMA Observations of Multiple CO and C Lines toward the Active Galactic Nucleus of NGC 7469: An X-Ray-dominated Region Caught in the Act
- 2020ApJ...898...97B (2020): An Evolutionary Study of Volatile Chemistry in Protoplanetary Disks
- 2020ApJ...898..146M (2020): Dust Populations in the Iconic Vega Planetary System Resolved by ALMA
- 2020ApJ...899L..10F (2020): A Low-velocity Bipolar Outflow from a Deeply Embedded Object in Taurus Revealed by the Atacama Compact Array
- 2020ApJ...900..131L (2020): Ionized and Atomic Interstellar Medium in the z = 6.003 Quasar SDSS J2310+1855
- 2020ApJ...903...94M (2020): ALMA Observations of Giant Molecular Clouds in M33. II. Triggered High-mass Star Formation by Multiple Gas Colliding Events at the NGC 604 …
- 2020ApJ...904..158L (2020): ALMA Observations and Modeling of the Rotating Outflow in Orion Source I
- 2020MNRAS.492.1180R (2020): ALMA and ROSINA detections of phosphorus-bearing molecules: the interstellar thread between star-forming regions and comets
- 2020MNRAS.493L.108B (2020): <SUP>13</SUP>C<SUP>17</SUP>O suggests gravitational instability in the HL Tau disc
- 2020MNRAS.496..364R (2020): A molecular absorption line survey towards the AGN of Hydra-A
- 2020MNRAS.496..394R (2020): Illuminating a tadpole's metamorphosis II: observing the ongoing transformation with ALMA
- 2020MNRAS.497.2811K (2020): Survey of planetesimal belts with ALMA: gas detected around the Sun-like star HD 129590
- 2020MNRAS.497.5454I (2020): Multiwavelength investigation of extended green object G19.88-0.53: revealing a protocluster
- 2020MNRAS.498L..87B (2020): FAUST I. The hot corino at the heart of the prototypical Class I protostar L1551 IRS5
- 2021A&A...645A.145G (2021): ALMA chemical survey of disk-outflow sources in Taurus (ALMA-DOT). V. Sample, overview, and demography of disk molecular emission
- 2021A&A...648A..19W (2021): A highly non-Keplerian protoplanetary disc. Spiral structure in the gas disc of CQ Tau
- 2021A&A...651L...6B (2021): A major asymmetric ice trap in a planet-forming disk. II. Prominent SO and SO<SUB>2</SUB> pointing to C/O &lt; 1
- 2021A&A...655A..72S (2021): Physical conditions in the warped accretion disk of a massive star. 349 GHz ALMA observations of G023.01‒00.41
- 2021A&A...655A..80D (2021): ATOMIUM: halide molecules around the S-type AGB star W Aquilae
- 2021A&A...656A..46M (2021): ALCHEMI, an ALMA Comprehensive High-resolution Extragalactic Molecular Inventory. Survey presentation and first results from the ACA array
- 2021A&A...656A..68E (2021): The Sun at millimeter wavelengths. III. Impact of the spatial resolution on solar ALMA observations
- 2021AJ....161...38O (2021): The TW Hya Rosetta Stone Project. I. Radial and Vertical Distributions of DCN and DCO<SUP>+</SUP>
- 2021AN....342.1160P (2021): CO kinematics unveil outflows plausibly driven by a young jet in the gigahertz peaked radio core of NGC 6328
- 2021ApJ...908..108F (2021): Physical and Chemical Structure of the Disk and Envelope of the Class 0/I Protostar L1527
- 2021ApJ...908..163M (2021): Extremely Low Molecular Gas Content in the Vicinity of a Red Nugget Galaxy at z = 1.91
- 2023ApJ...956L..16T (2023): An ALMA-resolved View of 7000 au Protostellar Gas Ring around the Class I Source CrA-IRS 2 as a Possible Sign of Magnetic Flux Advection
- 2023ApJ...956L..35Z (2023): One, Two, Three ... An Explosive Outflow in IRAS 12326-6245 Revealed by ALMA
- 2023MNRAS.526.4402B (2023): Fragmentation and dynamics of dense gas structures in the proximity of massive young stellar object W42-MME
- 2023MNRAS.526L..41P (2023): Kinematic and thermal signatures of the directly imaged protoplanet candidate around Elias 2-24
- 2023PASJ...75..424O (2023): ALMA Band 6 high-resolution observations of the transitional disk around SY Chamaeleontis
- 2023PASJ...75.1105K (2023): Kinematic signatures of a low-mass planet with a moderately inclined orbit in a protoplanetary disk
- 2024A&A...682A..74F (2024): The GUAPOS project: G31.41+0.31 Unbiased ALMA sPectral Observational Survey. IV. Phosphorus-bearing molecules and their relation to shock t…
- 2024A&A...686A..59N (2024): A deep search for large complex organic species toward IRAS16293-2422 B at 3 mm with ALMA
- 2024A&A...686A.201N (2024): ALMA view of the L1448-mm protostellar system on disk scales: CH<SUB>3</SUB>OH and H<SUP>13</SUP>CN as new disk wind tracers
- 2024A&A...687A..36T (2024): JWST Observations of Young protoStars (JOYS). Linked accretion and ejection in a Class I protobinary system
- 2024A&A...687A.220I (2024): Rotational spectroscopy of CH<SUB>3</SUB>OD with a reanalysis of CH<SUB>3</SUB>OD toward IRAS 16293-2422
- 2024A&A...687A.233M (2024): Unveiling the gas phase H<SUB>2</SUB>NCO radical: Laboratory rotational spectroscopy and interstellar searches in the direction of IRAS 162…
- 2024A&A...689A..64B (2024): An ALCHEMI inspection of sulphur-bearing species towards the central molecular zone of NGC 253
- 2024A&A...689A..65R (2024): ALMA high-resolution observations unveil planet formation shaping molecular emission in the PDS 70 disk
- 2024A&A...689A..85G (2024): MINDS: A multi-instrument investigation into the molecule-rich JWST-MIRI spectrum of the DF Tau binary system
- 2024A&A...689A.263D (2024): GATOS: missing molecular gas in the outflow of NGC 5728 revealed by JWST
- 2024A&A...689A.317G (2024): Continuum and molecular emission from the inner regions of the symbiotic system R Aquarii
- 2024A&A...691A.180F (2024): CHEMOUT: CHEMical complexity in star-forming regions of the OUTer Galaxy: IV. ALMA observations of organic species at a galactocentric radi…
- 2024A&A...692A..97M (2024): Sulfur-bearing molecules in a sample of early star-forming cores
- 2024AJ....167...66Y (2024): Chemistry of Complex Organic Molecules in the V883 Ori Disk Revealed by ALMA Band 3 Observations
- 2024ApJ...961..108K (2024): The CO Outflow Components Ejected by a Recent Accretion Event in B335
- 2024ApJ...962....1S (2024): Molecular Outflow in the Reionization-epoch Quasar J2054-0005 Revealed by OH 119 μm Observations
- 2024ApJ...962...48J (2024): Thermal Properties of the Hot Core Population in Sagittarius B2 Deep South.
- 2024ApJ...963...72O (2024): Revealing Multiple Nested Molecular Outflows with Rotating Signatures in HH270mms1-A with ALMA
- 2024ApJ...964..166K (2024): Physical Properties of Molecular Clouds in the Overlap Region of the Merging Antennae Galaxies
- 2024ApJ...966...51G (2024): The Size─Linewidth Relation and Signatures of Feedback from Quiescent to Active Star Forming Regions in the LMC
- 2024ApJ...966..117X (2024): Disk Wind Feedback from High-mass Protostars. III. Synthetic CO Line Emission
- 2024ApJ...967...15K (2024): Infall Motions in the Hot Core Associated with the Hypercompact H II Region G345.0061+01.794 B
- 2024ApJ...968L..19F (2024): Deep Search for Phosphine in a Prestellar Core
- 2024ApJ...969..143I (2024): A Radial Decrease in Kinetic Temperature Measured with H<SUB>2</SUB>CO in 30 Doradus
- 2024ApJ...969..165D (2024): Chemistry in Externally FUV-irradiated Disks in the Outskirts of the Orion Nebula Cluster
- 2024ApJ...970...28O (2024): CH<SUB>3</SUB>OH and Its Deuterated Species in the Disk/Envelope System of the Low-mass Protostellar Source B335
- 2024ApJ...974...83Y (2024): Detection of Dimethyl Ether in the Central Region of the MWC 480 Protoplanetary Disk
- 2024ApJ...977..251H (2024): Molecular Gas Mass Measurements of an Active, Starburst Galaxy at z ≍ 2.6 Using ALMA Observations of the [C I], CO, and Dust Emission
- 2024BAAA...65..173M (2024): Understanding the chemistry of the young stellar object G29.862-0.0044
- 2024ESC.....8..665M (2024): Detection and Chemical Modeling of Complex Prebiotic Molecule Cyanamide in the Hot Molecular Core G31.41 + 0.31
- 2024IJAsB..23...14M (2024): Detection and prebiotic chemistry of possible glycine precursor molecule methylenimine towards the hot molecular core G10.47+0.03
- 2024MNRAS.529.3601R (2024): Observations of spiral and streamer on a candidate proto-brown dwarf
- 2024MNRAS.534.2904C (2024): Observational signatures of circumbinary discs - II. Kinematic signatures in velocity residuals
- 2024NatAs...8..587F (2024): Resolved ALMA observations of water in the inner astronomical units of the HL Tau disk
- 2025A&A...693A..76C (2025): Dissecting the disk and the jet of a massive (proto)star: An ALMA view of IRAS 20126+4104
- 2025A&A...693A.101T (2025): Characterising the molecular line emission in the asymmetric Oph-IRS 48 dust trap: Temperatures, timescales, and sub-thermal excitation
- 2025A&A...694A.166C (2025): The ALMA-ATOMS survey: Vibrationally excited HC<SUB>3</SUB>N lines in hot cores
- 2025A&A...695A.149K (2025): Physical conditions around high-mass young star-forming objects via simultaneous observations of excited OH and methanol masers
- 2025A&A...695A.236L (2025): Erosion of a dense molecular core by a strong outflow from a massive protostar
- 2025A&A...696A..31G (2025): Shock-induced HCNH<SUP>+</SUP> abundance enhancement in the heart of the starburst galaxy NGC 253 unveiled by ALCHEMI
- 2025A&A...696A.100G (2025): PDRs4All: XII. Far-ultraviolet-driven formation of simple hydrocarbon radicals and their relation with polycyclic aromatic hydrocarbons
- 2025A&A...699A.369V (2025): Dense clumps survive in the vicinity of R136 in 30 Doradus
- 2025A&A...699A.382M (2025): FAUST: XXV. A potential new molecular outflow in [BHB2007] 11
- 2025ApJ...984L..15P (2025): exoALMA. X. Channel Maps Reveal Complex <SUP>12</SUP>CO Abundance Distributions and a Variety of Kinematic Structures with Evidence for Emb…
- 2025ApJ...985..225L (2025): Unveiling Two Deeply Embedded Young Protostars in the S68N Class 0 Protostellar Core with JWST/NIRSpec
- 2025ApJ...986L..22R (2025): The First Detection of Molecular Activity in the Largest Known Oort Cloud Comet: ALMA Imaging of C/2014 UN271 (Bernardinelli─Bernstein) at …
- 2025ApJ...987..197H (2025): The ALMA-ATOMS Survey: Exploring Protostellar Outflows in HC<SUB>3</SUB>N
- 2025ApJ...992...55T (2025): Extended and Compact Ortho-H<SUB>2</SUB>D<SUP>+</SUP> Structures Close to the Moment of Star Formation: Evidence from ALMA-ACA Observations…
- 2025ApJ...992L..15L (2025): A Dense Molecular Ringlike Structure in Gaseous CO Depletion Region G34.74−0.12
- 2025ApJ...993...90S (2025): ALMA High-resolution Observation for the Transitional Disk Around IRAS 04125+2902
- 2025ApJ...994...98F (2025): Measuring the Two-dimensional Thermal Structures of Protoplanetary Disks
- 2025ApJS..276...49J (2025): ALMA Spectral Survey of an Eruptive Young Star, V883 Ori (ASSAY). II. Freshly Sublimated Complex Organic Molecules in the Keplerian Disk
- 2025NatAs...9.1476C (2025): A D/H ratio consistent with Earth's water in Halley-type comet 12P from ALMA HDO mapping
- 2025NatAs...9.1833L (2025): Detection of a septuple stellar system in formation via disk fragmentation
- 2026A&A...705A..97K (2026): MINDS: Young binary systems with JWST/MIRI: Variable water-rich primaries and extended emission
- 2026A&A...705A.193L (2026): Zooming into the water snow line: High-resolution water observations of the HL Tau disk
- 2026A&A...705A.198M (2026): The ALMA survey to Resolve exoKuiper belt Substructures (ARKS): IV. CO gas imaging and overview
- 2026A&A...705A.204J (2026): The ALMA survey to Resolve exoKuiper belt Substructures (ARKS): X. Interpreting the peculiar dust rings around HD 131835
- 2026A&A...707A.120H (2026): Spatial distribution of organics in the Horsehead nebula: Signposts of chemistry driven by atomic carbon
- 2026ApJ..1000L..32A (2026): exoALMA. XXIV. Formaldehyde Emission in Protoplanetary Disks of exoALMA Compared with Their Properties and Dynamical State
- 2026ApJ..1001L...1T (2026): ALMA Band 9 CO(6─5) Reveals a Warm Ring Structure Associated with the Embedded Protostar in the Cold Dense Core MC 27/L1521F
- 2026ApJ..1003...64Y (2026): Compact Hydrogen Sulfide Emission Indicates Sulfur-bearing Ice Sublimation in the Inner Disk of HD 163296
- 2026ApJ..1003...68Y (2026): A Multiscale Molecular and Atomic Gas View on the H II Region N113 in the Large Magellanic Cloud: Evidence for High-mass Star Formation Tri…
