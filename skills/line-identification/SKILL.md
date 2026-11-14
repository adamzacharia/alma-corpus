---
name: alma-line-identification
description: "Assign molecular, atomic and recombination transitions to lines in ALMA spectra: spectral scans and unbiased surveys, crowded hot-core and hot-corino spectra, COM detections, vibrationally excited states, hyperfine groups, disk line surveys by matched filtering, and evolved-star wind surveys. Covers catalogue lookup (CDMS, JPL, Splatalogue), detection thresholds, blend rules, LTE synthetic-spectrum checks (XCLASS, Weeds, CASSIS, MADCUBA, MADEX) and claiming a new detection. Use when a task asks which species a line belongs to, for a line inventory of a source, whether a molecule is detected, or which transitions are clean enough to fit. Built from 65 ALMA papers in the evidence pack (2013-2026), about 52 of them on-topic."
---

# Spectral line identification and line surveys

Turns a list of emission or absorption peaks into secure assignments (species, transition, vibrational
state) and decides which transitions are clean enough to measure. The two mistakes that matter most:
calling a molecule detected from lines that are blended or that sit at the wrong velocity, and never
checking that the same LTE model does not predict strong lines you do not see. Expect a residue of
unidentified lines (about 20% in 2025ApJS..276...49J; 66 unidentified lines reported in the AGB survey 2018A&A...615A..28D).

Counts below come from the evidence pack. 65 papers were tagged by regex; about 13 are off-topic for
molecular line assignment (astrometry, stellar masses, extragalactic redshift work), so "on-topic" counts
use the 31 on-topic paper excerpts in the pack unless an aggregate is named.

## When to use

- Spectral scans and unbiased surveys of hot cores and hot corinos where every channel may hold a line:
  PILS (2018A&A...616A..90C, 2017A&A...597A..53L, 2020A&A...635A..48M), ReMoCA (2019A&A...628A..10B),
  GUAPOS (2020A&A...644A..84M), ATOMS (2025A&A...694A.166C), Orion KL (2015ApJ...803...97S,
  2017A&A...604L...2F, 2019ApJ...885...82L), Sgr B2 (2014Sci...345.1584B, 2024ApJ...962...48J).
- Claiming a first or new detection of a molecule: iso-propyl cyanide (2014Sci...345.1584B), urea
  (2019A&A...628A..10B), methyl isocyanate (2017MNRAS.469.2230M), cyanamide (2024ESC.....8..665M),
  methylenimine (2024IJAsB..23...14M), vibrationally excited acetic acid (2019ApJ...882..118X).
- Inventories of hot corinos and protostellar disks: B335 (2016ApJ...830L..37I), V883 Ori
  (2019NatAs...3..314L, 2025ApJS..276...49J, 2024AJ....167...66Y), MWC 480 and LkCa 15
  (2020ApJ...893..101L, 2024ApJ...974...83Y), DG Tau (2019A&A...623L...6P).
- Evolved-star wind surveys and searches for metal oxides: R Dor and IK Tau (2018A&A...615A..28D), AlO
  (2017A&A...598A..53D), FeO (2018ApJ...855..113D), vibrationally excited HNC in IRC+10216
  (2013ApJ...778L..25C).
- Separating a weak target line from contaminants such as recombination lines or narrow foreground
  absorption (2019A&A...622A..26G) or a blended pair (HNC/CN in 2018ApJ...866L..12G).

## When not to use

- **Extragalactic redshifts and blind searches for line emitters** (one or two CO, [CII] or [CI] lines,
  which line is it, what z): use **redshift-line-search**. The pack holds several of these
  (2013ApJ...767...88W, 2014ApJ...781L..39T, 2016ApJ...833...69D, 2025A&A...698A.204H), but their logic is
  redshift ladders and photo-z priors, not catalogue matching at a known velocity.
- **Rotation temperature and column density** once lines are assigned (rotation diagrams, LTE column
  fitting, upper limits): use **rotational-diagram-lte**. This skill stops at a clean, assigned line list
  plus the LTE model used to check it.
- Kinetic temperature and density from line ratios, sub-thermal or maser excitation: **non-lte-excitation**.
- Absorption against a background continuum (column per velocity component): **absorption-lines**.
- Isotopologue or deuteration ratios: **isotopic-ratios** (after this skill).
- Choosing line-free channels: **continuum-subtraction**. It drives what you can identify, but it has its
  own skill.

## Steps

1. **Fix the reference velocity and build the spectrum.**
   - Goal: a continuum-subtracted spectrum (in K, if you will model it) at the position where lines are
     brightest, with the source velocity known.
   - Method: extract from a circular aperture around the continuum or line peak. Radii stated explicitly:
     0.5" (2020ApJ...896...35J) and nested 80/320/800 mas (IK Tau) or 75/300/1000 mas (R Dor)
     (2018A&A...615A..28D). Other papers give the circle size without saying radius or diameter: a 0.6"
     circular aperture (2019NatAs...3..314L), a 3.1" circle (2024ESC.....8..665M), a 23.75" circle for
     ACA data (2024IJAsB..23...14M). State which one you use. Shift to the source velocity before
     stacking or fitting (2019NatAs...3..314L).
     Adopt v_sys from the literature or a strong simple line: 8.34 km/s for B335 (2016ApJ...830L..37I),
     6.96 km/s for IRAS 4A1 (2019ApJ...872..196S), 97 km/s for G31.41+0.31 (2024ESC.....8..665M), 68.50
     km/s for G10.47+0.03 (2024IJAsB..23...14M).
   - Weak disk lines: two filtering approaches appear, and they give different products.
     - Detection only: a Keplerian matched filter applied to visibilities (VISIBLE, about 2-3x S/N gain
       in 2020ApJ...893..101L) yields a normalized filter impulse response spectrum. Use its significance
       to decide whether a line is there; it is not a brightness spectrum, so never fit an LTE model to it
       or read line intensity from it. Extract a calibrated spectrum or image separately for that.
     - Spectrum for modelling: first-principal-component (PC1) filtering of the cube produced the
       disk-averaged spectra that were then modelled with XCLASS (2025ApJS..276...49J).
   - Continuum: STATCONT was used in the large surveys (2025ApJS..276...49J, 2020A&A...644A..84M); a
     2nd-order polynomial baseline on the extracted spectrum in 2024IJAsB..23...14M.
   - Software: CASA (imaging), STATCONT, spectral-cube, VISIBLE.

2. **List candidate peaks with an explicit detection rule.**
   - Goal: a reproducible peak list, not a by-eye one.
   - Method: rules seen in the pack: continuous emission above 3x the local off-source channel rms
     (2018A&A...615A..28D); above 3 sigma and near the systemic velocity (2025A&A...694A.166C); above 3 rms
     (2020A&A...644A..84M); above 5 sigma (2020ApJ...896...35J); contiguous channels above 2 sigma with a
     peak above 3 sigma (2025NatAs...9.1476C); above 4 sigma in matched-filter response
     (2020ApJ...893..101L); also 3 sigma in 2025ApJS..276...49J and 2019ApJ...872..196S, 5 sigma in
     2024ESC.....8..665M, 2 sigma in 2019ApJ...871..170M. State the rms definition, which the cards often
     leave out.

3. **Match candidates against line catalogues.**
   - Goal: every plausible assignment for each peak, not just the first hit.
   - Method: query CDMS and JPL at the rest frequency for v_sys, with Splatalogue to see all species near a
     frequency at once (2016ApJ...830L..37I, 2019A&A...622A..26G, 2015ApJ...803...97S). Include
     recombination lines (H66 epsilon in 2019A&A...622A..26G; an H-alpha check in 2019A&A...628A..10B) and
     vibrationally excited states (HC3N in up to seven states in 2025A&A...694A.166C; acetic acid
     vt = 1, 2 in 2019ApJ...882..118X; methyl formate vt = 0, 1, 2 in 2015ApJ...803...97S). For evolved
     stars, also compare with an existing survey atlas (the SMA VY CMa atlas in 2018A&A...615A..28D).
   - Velocity agreement: keep three things apart. (a) The centroid uncertainty of each line: the one
     explicit budget in the pack compares fitted line centres with JPL frequencies using a 1.5 km/s
     v_LSR uncertainty and a Gaussian sigma floored at the channel width (2019A&A...623L...1K, from the
     key-parameters aggregate). (b) The line width, which is a property of the gas, not a tolerance.
     (c) The acceptance window for calling a match. No paper in the pack gives a numeric window: ATOMS
     only says "near" the systemic velocity (2025A&A...694A.166C), and the ASSAY card flags the
     line-matching tolerance as not stated (2025ApJS..276...49J). Set and report your own window from
     the channel width, the v_sys uncertainty and the catalogue frequency uncertainty (general practice).
   - Hyperfine structure: keep the components together. Use catalogue entries that include hyperfine
     splitting (14N hyperfine in 2020MNRAS.492.1180R) or sum Gaussians per component scaled by catalogue
     line strengths with one shared width (2017A&A...598A..53D). That scaling assumes optically thin LTE,
     and the AlO authors themselves say this assumption is likely invalid (2017A&A...598A..53D): check
     opacity (relative component strengths) before fixing component ratios, and treat fixed ratios as an
     assumption. Say so when the hyperfine lines are unresolved (2024IJAsB..23...14M).
   - Transition cuts seen before matching: Aij >= 1e-4 s^-1 and Eup up to about 400 K
     (2017A&A...604L...2F); Aij >= 1e-5 s^-1 (2019ApJ...872..196S); Aul >= 1e-8 s^-1 and Eu <= 1000 K
     (2024AJ....167...66Y). These depend on source temperature and sensitivity; there is no single default.
   - Software: CDMS, JPL, Splatalogue (counts under Software); astroquery can script the lookup (named once
     in the pack aggregates).

4. **Model the whole band in LTE and compare.**
   - Goal: a synthetic spectrum that reproduces the detected lines of each species and predicts no strong
     line where the data show nothing.
   - Three scopes appear in the pack; say which one you ran.
     - Full-band model of all identified species, against which each new species is judged: Weeds over the
       whole 3 mm window (2014Sci...345.1584B) and Weeds synthetic spectra of all identified molecules
       (2019A&A...628A..10B); a preliminary identification of the whole spectrum before XCLASS fits
       (2020A&A...644A..84M); XCLASS screening of about 1500 species (2025ApJS..276...49J, below).
     - Targeted LTE fits of one species or family: XCLASS for HC3N vibrational states
       (2025A&A...694A.166C); CASSIS grids for nitriles (2018A&A...616A..90C); CASSIS LTE models with a
       CH3OH reference in the AFGL 4176 line census (2020ApJ...896...35J); CASSIS for NH2CN
       (2024ESC.....8..665M) and CH2NH (2024IJAsB..23...14M); MADCUBA-AUTOFIT for PN, PO and SO
       (2020MNRAS.492.1180R).
     - Catalogue identification with a code, no model reported: MADEX (2013ApJ...778L..25C).
   - Free parameters where stated: column density, temperature, source size, velocity offset and line
     width (2014Sci...345.1584B, 2025A&A...694A.166C).
   - Automated screening for big surveys: XCLASS model spectra for about 1500 species at 35 column steps
     from 5e12 to 5e18 cm^-2, scoring each species by f = matched / modelled lines, keeping species at
     100%, then visual inspection (2025ApJS..276...49J). The card flags the isolated-line criteria and the
     line-matching tolerance behind f as not stated, so this cannot be reproduced from the paper's text
     alone: define both yourself and report them.
   - Non-detections constrain the model: the CH3OH grid in 2019A&A...631A..64B had to reproduce the
     detected lines and produce no emission for two undetected ones.
   - Snyder-style criteria for weak species (2019ApJ...882..118X): simulate thermalized spectra with the
     continuum as background (Tbg 11.5 to 43.1 K across Bands 4 to 7) and keep only features that pass
     the P and D factor tests (six vt = 1 and three vt = 2 clean features). Neither the pack nor the card
     defines the P and D factors or their thresholds (the card cites a separate method paper); read that
     paper before applying the test.
   - Software: Weeds/CLASS (GILDAS), XCLASS with MAGIX, CASSIS (LTE-RADEX, MCMC), MADCUBA (SLIM, AUTOFIT),
     MADEX.

5. **Classify blends and pick the clean transitions.**
   - Goal: label every assigned line as clean, blended or not detected before any quantity is fitted.
   - Blending (a separate question from opacity): classify as blended (B), not blended (NB) or not
     detected (ND); NB if the contaminant is weaker than about 10% of the target line
     (2015ApJ...803...97S). Keep only transitions not severely blended with other species
     (2014Sci...345.1584B). GUAPOS used three rules to accept a transition (2020A&A...644A..84M); the pack
     shows only two of them (intensity above 3 rms, a blending criterion), without the blending
     threshold, so read the paper before copying the rule set. Fit a simple profile (soft parabola) only
     to expose blends, not for parameters (2018A&A...615A..28D); finish with manual inspection of blends.
   - Opacity (flag separately): a clean, unblended line can still be optically thick. Fits used only
     optically thin lines, tau < 0.2 (2018A&A...616A..90C, which excluded blended and optically thick
     lines as two separate cuts), or checked tau_0 << 1 afterwards (2020A&A...644A..84M).
   - Overlapping lines: a joint fit is one option. 2018ApJ...866L..12G fit HNC(5-4) and CN(4-3) with free
     amplitudes, a constant continuum, one shared Gaussian width and redshift (assumed common to both
     species) and CN in optically thin LTE at 300 K, and warned that the split depends strongly on the
     adopted redshift. Tie width and velocity only when there is evidence both lines come from the same
     gas component; otherwise compare fits with and without the tie and carry the spread into the
     line fluxes.

6. **Decide detection status and report.**
   - Goal: a defensible "detected / tentative / not detected" per species.
   - Detection evidence quoted for new species: six non-blended lines above 5 sigma for NH2CN
     (2024ESC.....8..665M); nine clearly detected urea lines (2019A&A...628A..10B).
   - Not detection minima, do not reuse them as such: at least three lines per vibrational state were
     required to fit, not to detect (2025A&A...694A.166C); 25, 12 and 14 lines were the transitions
     selected for fitting the three C2H4O2 isomers (2020A&A...644A..84M).
   - Tentative status, with each paper's own reason: FeO rests on a single transition, and the authors
     say a second transition would strengthen the identification (2018ApJ...855..113D; the quote is in
     the card); the CO/OH results are tentative because of the simple methods used, with non-LTE
     modelling needed (2019A&A...623L...1K); acetone in B335 is called tentative, and the pack does not
     give the reason (2016ApJ...830L..37I). State your reason whenever you write "tentative".
   - Report the line list (rest frequency, Eup, Aij, catalogue entry, flag), the unidentified lines, the
     LTE model parameters and the catalogue versions.
   - Report the uncertainty method with the model: how errors were set (varying N and Tex until the fit
     degrades in 2018A&A...616A..90C; calibration error plus fit error in 2019NatAs...3..314L; Monte Carlo
     on synthetic data for Gaussian fit errors in 2020ApJ...896...35J), known degeneracies (Tex-N for
     acetic acid gives about a factor 2 in N in 2020A&A...644A..84M), and how results move with fixed
     assumptions (N changes by 2.1 to 2.5x over Tex 5 to 50 K in 2020MNRAS.492.1180R). Then hand the clean
     lines to **rotational-diagram-lte**.

## Parameter defaults and ranges

| Parameter | Common choice | Range seen | Papers (count) | Examples |
|---|---|---|---|---|
| Detection threshold | 3 sigma (6 of 10) | 2 to 5 sigma; 4 sigma in matched-filter response | 10 | 2018A&A...615A..28D, 2025A&A...694A.166C, 2020A&A...644A..84M, 2025ApJS..276...49J, 2019ApJ...872..196S, 2025NatAs...9.1476C (3 sigma peak, 2 sigma channels); 2020ApJ...893..101L (4); 2020ApJ...896...35J, 2024ESC.....8..665M (5); 2019ApJ...871..170M (2) |
| Velocity criterion for a match | "near" v_sys; no paper states a numeric window | not stated; matching tolerance flagged as unstated in 2025ApJS..276...49J | 1 | 2025A&A...694A.166C |
| Line-centre uncertainty when comparing with catalogue frequencies | v_LSR uncertainty plus fitted sigma | 1.5 km/s v_LSR uncertainty; sigma floored at channel width | 1 | 2019A&A...623L...1K |
| Blend rule | contaminant < ~10% of target counts as not blended | "not severely blended" (no number) | 2 | 2015ApJ...803...97S, 2014Sci...345.1584B |
| Opacity cut or check for fitted lines | only optically thin lines | tau < 0.2 cut; tau_0 << 1, tau ~ 0.7, max tau <= 0.15 checks | 4 | 2018A&A...616A..90C (cut); 2020A&A...644A..84M, 2019A&A...631A..64B, 2026ApJ..1000L..32A (checks) |
| Lines used in these analyses | see column 3; detection evidence and fit requirements differ | detection evidence: 6 non-blended lines > 5 sigma, 9 clearly detected lines; fit requirement: >= 3 lines per vibrational state; lines selected for fitting: 25, 12, 14 per isomer | 4 | 2024ESC.....8..665M, 2019A&A...628A..10B (detection); 2025A&A...694A.166C (fit); 2020A&A...644A..84M (selection) |
| Einstein A cut | >= 1e-5 to 1e-4 s^-1 | 1e-8 to 1e-4 s^-1 | 3 | 2017A&A...604L...2F, 2019ApJ...872..196S, 2024AJ....167...66Y |
| Upper-level energy cut | Eu < 250 to 400 K | up to 1000 K | 3 | 2020A&A...644A..84M, 2017A&A...604L...2F, 2024AJ....167...66Y |
| Tex fixed or explored, hot cores and corinos | 100 to 160 K fixed | 90 to 300 K grid | 4 | 2016ApJ...830L..37I (100 K), 2019A&A...628A..10B and 2020ApJ...896...35J (160 K), 2018A&A...616A..90C (grid) |
| Tex fitted, hot cores and corinos (results, not settings) | none | 110 to 140 K (nitriles); 210.5 +/- 32.8 K; 220 +/- 20 K; 250 K (+/- 25 or 35 K); HC3N* 160 to 335 K | 5 | 2018A&A...616A..90C, 2024IJAsB..23...14M, 2019A&A...631A..64B, 2024ESC.....8..665M, 2025A&A...694A.166C |
| Tex, V883 Ori disk | 120 K fixed | fitted 91.5 +/- 3.5 K (13CH3OH), 103.3 +/- 34.9 K (CH3OCHO) | 2 | 2019NatAs...3..314L, 2025ApJS..276...49J |
| Tex assumed, other disks | a range, not one value | 20 to 100 K; 25, 50, 75 K; 30 to 300 K | 3 | 2020A&A...644A.119P, 2019A&A...623A.124C, 2019A&A...623L...6P |
| Line width (FWHM) | fixed, e.g. from a filtered or clean line (2025ApJS..276...49J) | fixed or explored 0.8 to 5 km/s; fitted 4.5 to 5.2 km/s; visual grid 0.5 to 25 km/s | 8 | 2018A&A...616A..90C (0.8-1.2, 1.8-2.4), 2017MNRAS.469.2230M (1.1), 2019NatAs...3..314L (2), 2025ApJS..276...49J (3), 2019A&A...628A..10B (5.0), 2020ApJ...896...35J (5), 2017A&A...598A..53D (grid; fit 4.5, 5.0), 2024ESC.....8..665M (fit 5.2) |
| Source size | 0.5" (3 of 8) | 0.15" to 2"; filling factor 0.384 | 8 | 2018A&A...616A..90C, 2017MNRAS.469.2230M, 2020ApJ...896...35J (0.5"); 2019NatAs...3..314L (0.6"); 2019A&A...631A..64B (0.15"); 2024ESC.....8..665M (1.3"); 2019A&A...628A..10B (2"); 2025ApJS..276...49J (0.384) |
| Background temperature | 2.73 K, Tc = 0 | continuum as background; 11.5 to 43.1 K | 4 | 2024ESC.....8..665M, 2018ApJ...863..129S, 2018A&A...616A..90C, 2019ApJ...882..118X |
| Column grid for screening | 5e12 to 5e18 cm^-2, 35 steps | 1e13 to 1e17 cm^-2 grid | 2 | 2025ApJS..276...49J, 2018A&A...616A..90C |

How counted: my own count of on-topic papers in the pack (excerpts plus the key-parameter and assumption
aggregates) that state a numeric value or explicit rule for the row; free parameters with no stated value
are not counted (source size is free in 2014Sci...345.1584B and 2025A&A...694A.166C). The Examples column
is the full per-row list, so every count can be checked. Fixed settings, explored grids and fitted results
are kept in separate rows or labelled. Extragalactic line-search papers are excluded (for example S/N > 5 in
2016ApJ...833...69D). See `references/parameters.md` for per-paper values.

## Software

Counts from the pack aggregates (all 65 papers, regex-tagged steps) and, in brackets, from my own count of
the 31 on-topic paper excerpts (named anywhere in the excerpt):

| Software | Used for | Aggregate count | On-topic excerpts |
|---|---|---|---|
| CDMS | rest frequencies, Aij, Eu, partition functions | 13 (+2 other phrasings) | [20] |
| JPL catalog | same, plus species CDMS lacks | 5 (+4 other phrasings) | [11] |
| Splatalogue | combined lookup and blend checks | 7 | [6] |
| CASSIS | LTE grids, MCMC, and LTE fits with its LTE-RADEX module (an LTE fit, not a non-LTE check, in 2024ESC.....8..665M) | 7 | [5] |
| XCLASS (+MAGIX) | automated species screening (2025ApJS..276...49J) and targeted LTE fits | 5 | [4] |
| Weeds (GILDAS CLASS) | full-band LTE synthetic spectra | 5 (CLASS 2, GILDAS 1, CLASS90 1) | [2] |
| MADCUBA (SLIM, AUTOFIT) | LTE synthetic spectra, Levenberg-Marquardt fits | 2 + 2 (MADCUBA-IJ) | [1] |
| MADEX | line identification in an evolved-star wind; no model details given (2013ApJ...778L..25C) | 1 | [1] |
| STATCONT | continuum level in line-rich spectra | 1 | [2] |
| CASA | imaging, spectra extraction | 6 | not counted |
| VISIBLE | uv-plane matched filtering in disks | 1 | [1] |
| RADEX | non-LTE check of identifications (2018A&A...615A..28D) | 1 | [1] |

Also named once each: ALMA Data-Mining Toolkit, CubeLineMoment, gaussfit_catalog, pyspeckit and
spectral-cube for line lists and masked moments in NGC 253 (2019ApJ...871..170M); astropy SLSQP Gaussian
fits (2020ApJ...896...35J).

## Pitfalls

- **Blends hide in crowded spectra.** Authors admit that unidentified blends may explain under-reproduced
  lines (2020A&A...644A..84M), that many lines were blended and one temperature could not be set
  (2015ApJ...803...97S), and that HC3N had only three lines, two blended (2018A&A...616A..90C).
- **Unidentified lines remain.** About 20% in V883 Ori (2025ApJS..276...49J); report them, do not force
  assignments.
- **Continuum subtraction shapes the line list.** Line-free channels and the subtraction method are the
  settings cards most often flag as unstated (several phrasings, 1 to 4 papers each in the pack
  aggregates). The ReMoCA line-continuum split was "preliminary" with baseline artifacts
  (2019A&A...628A..10B); uncertainties may be underestimated because continuum-subtraction systematics
  were not included (2019ApJ...882..118X); N2D+ sat on the edge of an atmospheric feature
  (2017A&A...606A.125S).
- **Optically thick lines and dust.** Low-Eu lines may be thick, so Trot is an upper limit and N a lower
  limit (2019ApJ...872..196S); CH3OH lines likely thick in V883 Ori (2019NatAs...3..314L); optically thick
  dust hides midplane molecules (2017ApJ...843...27L).
- **Fixed source size and line width bias the model.** A fixed filling factor makes columns lower limits
  by about 2-3x (2025ApJS..276...49J); a maximum source size makes them lower limits
  (2019ApJ...880..130M); a line only two channels wide underestimates the column (2019ApJ...885...82L);
  higher-energy lines are likely more compact than the size set by low-energy lines (2016A&A...595L...4L).
- **Spectroscopy itself is uncertain.** CH2DOH spectroscopy uncertain by about a factor of 3
  (2024AJ....167...66Y); the urea line list came from a lab paper then in preparation
  (2019A&A...628A..10B card); in the deuterated acetaldehyde work neither the data processing nor the LTE model was
  optimized to reproduce line intensities (2019A&A...624A..70C). Record catalogue entry and version; the cards rarely state partition functions or
  entry tags.
- **Single-line species need an assumed Tex.** With one transition, Tex cannot be derived
  (2020MNRAS.492.1180R, 2020A&A...644A.119P); report how N moves over the Tex range.
- **Spatial resolution limits.** Unresolved emission prevents placing the species
  (2016ApJ...830L..37I, 2013ApJ...778L..25C, 2024ESC.....8..665M); extended emission may be filtered out
  (2018A&A...615A..28D, 2019ApJ...880..130M).
- **Masers are not thermal lines.** Exclude them from LTE line sets (2018A&A...615A..28D).
- **Velocity structure.** Lines from disk, outflow and envelope peak at different velocities
  (blue-dominant, disk and outflow line groups in 2020ApJ...896...35J); a single v_sys can misassign
  lines in multi-component sources.

## Verification checks

What papers did:
- Visual inspection of every automatically selected species (2025ApJS..276...49J) and manual inspection of
  blends (2018A&A...615A..28D).
- Check candidate lines are not blended using CDMS/JPL and Splatalogue (2024IJAsB..23...14M,
  2024ESC.....8..665M).
- Check the model does not predict emission for undetected lines (2019A&A...631A..64B); one paper in the
  pack aggregates checked the synthetic spectrum for missing detectable transitions.
- Rule out contamination by recombination lines (2019A&A...628A..10B, 2019A&A...622A..26G).
- Compare with an independent line list for the same source (2020ApJ...896...35J against a 2019 list) or
  analyse a reference source with the same lines (same analysis on Orion data, pack aggregates).
- Cross-check the LTE fit with a rotation diagram (consistent within errors in 2025A&A...694A.166C; a
  factor 7.6 difference explained by continuum opacity in 2019NatAs...3..314L).
- Check optical depth of the lines used: tau ~ 0.7 (2019A&A...631A..64B), tau_0 << 1
  (2020A&A...644A..84M), max tau <= 0.15 (2026ApJ..1000L..32A).
- Check identifications against non-LTE spectra (RADEX in 2018A&A...615A..28D).
- Justify LTE with density: ~1e8 cm^-3 (2024ESC.....8..665M), 7e7 cm^-3 (2024IJAsB..23...14M),
  n_H2 >> n_crit (2019ApJ...882..118X).

What a careful referee adds:
- Every claimed detection lists the clean transitions with S/N and velocity offset from v_sys, plus the
  strongest predicted lines that should have been seen.
- One LTE model reproduces all clean lines of a species and its other vibrational states (ATOMS assumed
  the same abundance for all HC3N states, 2025A&A...694A.166C). Say which parameters are tied and why:
  2024AJ....167...66Y assumed a common emitting size, Tex and line width. Isotopologues keep their own
  column density, or a column tied by a stated isotope ratio (CH3OH = 13CH3OH x 60 in
  2019NatAs...3..314L); never force equal columns across isotopologues.
- The uncertainty method is stated next to the model: calibration error, fit error, known parameter
  degeneracies and the sensitivity to every fixed assumption (Tex, size, width), as in Step 6.
- Detection holds when the continuum level or line-free channels change.
- Catalogue entries and versions are cited, so the assignment can be re-run.

## Source cards

Full list with titles: `references/sources.md`. Most informative for this technique:

- 2025ApJS..276...49J: automated XCLASS screening of about 1500 species, PC1 filtering, about 20% U lines.
- 2018A&A...615A..28D: AGB band 7 survey; 3x rms rule, catalogue plus atlas match, soft-parabola blend check.
- 2015ApJ...803...97S: B/NB/ND classification with the 10% rule; torsionally excited methyl formate.
- 2020A&A...644A..84M: three selection rules (two visible in the pack), Eu < 250 K, lines selected per isomer, Tex-N degeneracy.
- 2019A&A...628A..10B: Weeds full-band model, urea detection, H-alpha check.
- 2014Sci...345.1584B: full 3 mm LTE model of all molecules; only weakly blended transitions shown.
- 2025A&A...694A.166C: HC3N vibrational states, 3 sigma, three lines per state, RTD cross-check.
- 2019ApJ...882..118X: Snyder criteria, P and D factors (thresholds not in the pack), band-dependent Tbg.
- 2018A&A...616A..90C: CASSIS grid, tau < 0.2 lines, error by varying N and Tex.
- 2020ApJ...896...35J: 203 lines from 25 molecules; 5 sigma; literature line-list comparison.
- 2024ESC.....8..665M: six non-blended lines above 5 sigma for a new molecule.
- 2024IJAsB..23...14M: ACA spectrum, polynomial baseline, CASSIS MCMC.
- 2020ApJ...893..101L: matched filtering of disk visibilities, 4 sigma.
- 2019A&A...631A..64B: model must not produce emission in undetected lines.
- 2016ApJ...830L..37I: 31 lines assigned with CDMS and JPL at fixed v_sys.
- 2017A&A...598A..53D: hyperfine Gaussian sums with shared FWHM grid.
- 2020MNRAS.492.1180R: MADCUBA-AUTOFIT with hyperfine entries, fixed Tex for single lines.
- 2019A&A...622A..26G: removing recombination and foreground lines with Splatalogue, CDMS, JPL.
- 2018ApJ...866L..12G: joint deblending of HNC and CN under assumed shared kinematics; split depends on redshift.
- 2017A&A...604L...2F, 2019ApJ...872..196S, 2024AJ....167...66Y: Aij and Eu transition cuts.
