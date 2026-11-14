---
name: alma-isotopic-ratios
description: "Measure isotope ratios (12C/13C, 16O/18O, 18O/17O, 14N/15N, 32S/34S, Si, Cl, Ar) and deuterium fractionation (D/H in DCO+, DCN, N2D+, CH2DOH, HDO and similar) from ALMA isotopologue lines, and use isotopologue pairs to measure or correct line optical depth. Use when a task asks for an isotope or deuteration ratio, a 15N or D enrichment, an opacity from a 12CO/13CO-type ratio, the main-species column from a rare isotopologue, or which elemental ratio to assume. Built from 99 ALMA papers (2013-2026)."
---

# Isotope and deuterium fractionation ratios

Measures the abundance ratio of two isotopologues (for example HCN/HC15N, CH2DOH/CH3OH, 13CO/C18O) and
reads it as an elemental isotope ratio, a fractionation signature, or an optical depth. Two mistakes matter
most. First, dividing intensities of a main line that is optically thick: the HCN/DCN ratio in Class II disks
went from about 10 (thin) to 54-75 once an HCN opacity of 5.8 was applied (2020ApJ...898...97B). Second,
assuming the pair is co-spatial, equally excited and equally filtered by the interferometer when it is not:
the ALMA data of NGC 1068 recovered only about 30% of the single-dish 12CN flux (2019A&A...629A...6T) but about
53% of the 13CN flux (same paper, card).

## When to use

- An isotope ratio is the science result: CO isotopologues in a starburst (2019A&A...624A.125M,
  2021A&A...656A..46M), CN/13CN in starbursts (2019A&A...629A...6T), CN/C15N and HCN/HC15N in disks
  (2017A&A...603L...6H, 2019A&A...632L..12H, 2020ApJ...898...97B), C2H vs CO carbon reservoirs
  (2024ApJ...965..147B), AGB and post-AGB envelopes (2013A&A...556L...1V, 2018A&A...615A..28D,
  2018A&A...617A..23B), Titan's atmosphere (2016ApJ...821L...8S, 2018ApJ...859L..15C, 2020ApJ...890...95I),
  molecular absorbers at z = 0.89 (2014A&A...566L...6M, 2015A&A...582L...4M, 2019A&A...629A.128W).
- Deuterium fractionation: COMs in hot cores and corinos (2016A&A...587A..91B, 2019A&A...632A..19T,
  2018A&A...620A.170J), water (2019A&A...631A..25J), DCO+/DCN/N2D+ in disks and cores (2017A&A...606A.125S,
  2015ApJ...810..112O, 2020ApJ...895..119T), HCN/DCN across evolutionary stages (2020ApJ...898...97B).
- Optical depth of a main line from its isotopologue ratio: HCO+/H13CO+ (2014ApJ...795...28B), CO/13CO/C18O
  pixel maps (2020MNRAS.496..394R), HCN/H13CN and HCO+/H13CO+ in galaxies (2015ApJ...801...63M,
  2017MNRAS.466...49J, 2021A&A...649A.125W), [CI]/[13CI] and 12CO/13CO in debris disks (2019ApJ...885L..39H,
  2019ApJ...883..180H).
- Main-species column or gas mass from a thin rare isotopologue scaled by an assumed elemental ratio:
  13CH3OH (2019ApJ...877L..25M, 2020MNRAS.498L..87B), H13CN (2024A&A...686A.201N), C18O and 13C17O
  (2025A&A...699A.382M, 2019ApJ...882L..31B, 2020MNRAS.493L.108B).

## When not to use

- The column density of each isotopologue is the hard part: derive N with the **rotational-diagram-lte**
  skill (rotation diagrams, XCLASS/MADCUBA/CASSIS/Weeds LTE fits) or, when excitation may be sub-thermal,
  the **non-lte-excitation** skill (RADEX, LVG). This skill starts from those columns or from matched
  intensities and covers what is specific to ratios.
- Gas mass from CO with alpha_CO: **gas-mass-co-conversion**. Disk-wide forward models where the isotope
  ratio is a fixed input (DALI, RAC2D, LIME, RADMC-3D as in 2017ApJ...836..201D, 2021ApJ...908....8C,
  2013ApJ...774...16R): **radiative-transfer-modelling**.
- Predicting fractionation with a reaction network (DALI isotope network in 2024ApJ...965..147B; UCLCHEM,
  ALCHEMIC in the pack software list): **chemical-modelling**.
- Absorption spectra toward a continuum source need covering factor and opacity profiles first:
  **absorption-lines**. Line assignment for rare isotopologues: **line-identification**.
- Off-topic matches in this pack (regex hits): 2025ApJ...985..225L is a JWST extinction paper. Three
  Orion KL deuteration papers are Herschel/HIFI papers by title; read each for its own method:
  2013ApJ...770..142N (H2O/HDO; it also discusses ALMA data lacking zero spacings, and HDO collision rates
  that stop at 450 K), 2013ApJ...777...85N (NH2D modelled with NH3 collision rates as a proxy) and
  2014ApJ...787..112C (LTE, no radiative pumping, constant source size).

## Steps

1. **Pick the isotopologue pair and the route.**
   - Goal: a pair whose ratio can be read without a large opacity correction.
   - Method, as papers do it:
     - Fitted columns of rare isotopologues: 13CO, C18O and C17O columns from synthetic LTE spectra
       (MADCUBA, Tex fixed at 15 K), assuming all isotopologues share distribution and velocity profile
       (2019A&A...624A.125M). The same authors say 13CO is moderately optically thick, so assess the
       opacity of every line in the pair before reading the column ratio as an isotope ratio. Note the
       algebra (general practice): N(13CO)/N(C18O) ~ (16O/18O)/(12C/13C), so this pair mixes a carbon and
       an oxygen ratio and needs one of them assumed or measured separately.
     - Same rare substitution in both species: 13CO/13C18O measures 16O/18O directly, with no carbon
       multiplier, provided 13CO is thin; it gave 520 +/- 60 in NGC 253 against 100 +/- 20 from HCO+
       (2021A&A...656A..46M).
     - Double isotope with an assumed multiplier: H13CN/HC15N times an assumed 12C/13C gives HCN/HC15N;
       12C/13C = 68 in 2020ApJ...898...97B (step 7) and 68(15) in 2017A&A...603L...6H (the pack states its
       assumption HCN/H13CN = elemental 12C/13C; the value 68(15) is in the card). The assumed ratio's
       error propagates directly into the result.
     - Isotope-independent opacity from hyperfine structure: CN, whose 12CN hyperfine ratio gives tau
       (2019A&A...629A...6T; the authors say CN is the only molecule meeting all their selection
       conditions, card).
     - Isotope-assumed opacity: [CI]/[13CI] with hyperfine relative intensities gives tau only after
       assuming 12C/13C = 77 and equal Tex; if the true ratio is above 77 the tau is a lower limit
       (2019ApJ...885L..39H). This is not self-calibration.
     - Deuteration against a rare main-species isotopologue: [CH2DOH]/[CH3OH] with CH3OH from 13CH3OH or
       CH3 18OH; literature comparisons kept only when built the same way (2019A&A...632A..19T).
   - Software: none specific; spectroscopy from CDMS/JPL (2018A&A...615A..28D, 2019A&A...624A.125M).
2. **Make the pair comparable in the data.**
   - Goal: same beam, same uv coverage, same mask, same velocity range.
   - Method: observe both lines in one setup where possible ("cross-calibration uncertainties were mitigated
     by the simultaneous observation", 2017A&A...603L...6H card). Convolve maps to a common beam before
     ratioing (2020MNRAS.496..394R). One literature example of a common mask: pixels above 3 sigma in both the
     major and minor isotopologue (2020ApJ...898...97B, with CASA imsmooth). A mask or S/N cut that selects
     on the weak line can bias the ratio (the card for 2019A&A...629A...6T flags this for its S/N cut), so
     recommended: recompute the ratio at two or three clip levels and report how it moves. Quantify
     missing flux per line against single dish (2019A&A...629A...6T) and see **array-combination** if it
     differs.
   - Software: CASA (5 papers, plus 1 naming CASA 4.4.0 and 1 imsmooth), GILDAS/MAPPING (2 entries).
3. **Measure the intensities.**
   - Goal: integrated intensities, or column densities, with errors.
   - Method: ratio of velocity-integrated intensities only where the weak line has S/N >~ 5 (2019A&A...629A...6T
     card); per-pixel, per-channel brightness-temperature ratios with masks of 6/4/3 sigma for
     12CO/13CO/C18O (2020MNRAS.496..394R); one profile shape fitted to both lines with a free scale factor
     (2017A&A...597A..99W, CLASS); uv-plane Gaussian fit to the bright isotopologue, then the same geometry
     imposed on the weak one so only the flux is free (2017A&A...603L...6H card, GILDAS UV_FIT); a joint
     absorption fit with the isotope ratio as a free parameter (2019A&A...629A.128W).
   - Nondetections: report a bound with its confidence level and the right direction. A missing rare
     isotopologue gives a lower limit on main/rare (2014A&A...566L...6M: NE H2(37)Cl+ not detected, only
     a lower limit on the ratio); a missing deuterated species gives an upper limit on the deuteration
     (2016A&A...587A..91B: CH3OD < 0.07%). State the sigma level used for the bound (recommended; the pack
     does not give one).
   - Pitfall to handle here: blends. 13CN may be blended with CH3OH (2019A&A...629A...6T); C18O may carry up
     to 30% HNCO contamination (2017ApJ...840L..11S).
4. **Get or correct the optical depth.**
   - Goal: tau of the main line, so its column is not underestimated.
   - Method (general radiative transfer, stated with its assumptions): work in brightness temperature per
     channel, after convolving both cubes to one beam. For each line T_B = f [J_nu(Tex) - J_nu(Tbg)]
     (1 - exp(-tau_nu)), with J_nu(T) = (h nu/k)/(exp(h nu/kT) - 1) and f the filling factor. The ratio is
     T_main/T_rare = (f_main/f_rare) x [J_main(Tex) - J_main(Tbg)]/[J_rare(Tex) - J_rare(Tbg)] x
     (1 - exp(-tau_main))/(1 - exp(-tau_rare)). The J ratio is 1 only if the two frequencies are close and
     Tex is shared; compute it otherwise. Setting tau_main = X tau_rare per channel further assumes equal
     Tex, the same line profile and the same transition, so that the column ratio X carries over to the
     opacity ratio (small differences in frequency, A and partition function ignored). Solve channel by
     channel, as 2020MNRAS.496..394R did (per-pixel, per-channel ratios at equal Tex). A ratio of
     velocity-integrated intensities does not obey this relation exactly; use it only as an approximation
     or fit the integrated profiles with a radiative-transfer model.
   - Literature shortcuts: 2014ApJ...795...28B applied tau_12 ~ X ln[R/(R - 1)] to area-integrated
     HCO+/H13CO+ intensities, assuming X = 24, equal Tex and brightness equal to Tex for HCO+, and got
     tau ~ 2.5 (1.5-2.5 for X = 17-40). For a thick main line and thin rare line the ratio tends to
     R ~ X/tau_main (general practice). For CN, I(3/2-1/2)/I(1/2-1/2) = (1 - exp(-tau1))/(1 - exp(-tau2))
     with tau1 = 2 tau2, assuming LTE (2019A&A...629A...6T).
   - What papers found: tau(12CO 2-1) = 43 +/- 7 in 49 Ceti (2019ApJ...883..180H); [CI] peak tau 10 +/- 3
     (2019ApJ...885L..39H); HCN and HCO+ tau 5-8 and CO tau ~ 2.5 in NGC 253 (2015ApJ...801...63M); 12CN
     tau 0.7-1.1 in three starbursts (2019A&A...629A...6T card).
5. **Convert to a column-density ratio.**
   - Goal: N_main/N_rare, not an intensity ratio.
   - Method: compute each N under shared assumptions (same Tex, same source size) with the
     **rotational-diagram-lte** or **non-lte-excitation** skill. For single-line pairs, use isotopologue
     lines with the same quantum numbers and correct the intensity ratio for Einstein A, frequency, partition
     function and lower-level energy (2018A&A...615A..28D). That paper states the method holds only for
     optically thin LTE emission with no difference in radiative pumping between the isotopologues, and it
     excluded masers. If the lines do not match in quantum numbers, or pumping may differ (bright IR
     field, maser candidates), go to excitation or radiative-transfer modelling instead. Check that Tex is really shared: RADEX gave equal Tex to
     better than 3% for CN and C15N below 20-25 K (2017A&A...603L...6H card).
   - Deuterated species: apply statistical corrections. 2016A&A...587A..91B assumed a 2:1 split between
     out-of-plane and in-plane conformers; PILS reported CH2DOH/CH3OH = 0.071 raw and 0.024 after correcting
     for the number of equivalent H atoms (2018A&A...620A.170J card). The CH3OD partition function is
     uncertain enough to change its column a lot (2019A&A...632A..19T).
   - Software: MADCUBA (2 papers, plus SLIM and MADCUBAIJ entries), CASSIS (2), Weeds (2), XCLASS/myXCLASS
     with MAGIX (1 each), RADEX (4 plus 1), LVG codes (2).
6. **Interpret the ratio.**
   - Goal: decide whether it is elemental, fractionated, or an excitation or opacity artefact.
   - Method: compare with the local ISM value at the source's galactocentric radius (see the parameter table), with single-dish values (2019A&A...629A...6T, 2021A&A...656A..46M compiled all
     literature NGC 253 ratios), and with chemical models (two deuteration models, T14 and A12 in
     2016A&A...587A..91B; DALI isotope network in 2024ApJ...965..147B). Consider isotope-selective
     photodissociation (2019ApJ...875...62Y, 2019ApJ...882L..31B) and chemical fractionation
     (2024ApJ...965..147B found C2H 12C/13C differs from CO in TW Hya).
7. **Propagate errors.**
   - Propagate calibration as a covariance, not as all-or-nothing. A common multiplicative error cancels
     in the ratio only where it has been shown to be common; keep a differential term otherwise, even for
     lines in one execution. ALCHEMI fits exclude absolute flux calibration error and report line flux
     scaling anomalies in some tunings (2021A&A...656A..46M); 2019A&A...629A...6T put ~10% on its ratios,
     mainly from a ~5% absolute flux calibration error (card).
   - Report the statistical error and say what is left out: Titan's ratios carry unquantified systematics
     from temperature profile and line broadening (2016ApJ...821L...8S); 2019A&A...624A..82B took ~40% (sqrt 2 x 30%) for a ratio.

## Parameter defaults and ranges

Counts are my tallies of distinct bibcodes, made by reading every value in the pack's "Key parameters",
"Assumptions" and "Limitations" lines and the excerpt method lines, one count per bibcode per value (not all
99 papers; 2025ApJ...985..225L excluded as off-topic). The per-bibcode lists are in
`references/parameters.md`. Longer tables of adopted and measured ratios are in


| Parameter | Common choice | Range seen | Papers (count) | Examples |
|---|---|---|---|---|
| Assumed 12C/13C, local disks/clouds | 69-70 | 60-77 | 16 at 69-70; 7 at 76-77; 4 at 68; 8 at 60-63 | 2016ApJ...823L..18H, 2019A&A...632A..19T, 2017ApJ...836..201D, 2020ApJ...898...97B |
| Assumed 12C/13C, Galactic centre / inner Galaxy / other Galactic values below 60 | 20-24 (GC) | 20-62 | 5 | 2014ApJ...795...28B, 2017A&A...605L...6T, 2014A&A...569A..11S, 2019A&A...624A..82B, 2025A&A...695A.149K (50, high-mass YSOs) |
| Assumed 12C/13C, galaxies / LMC | 40-50 | 25-100 | 9 | 2020ApJ...898...75I, 2017ApJ...850...54C, 2016ApJ...825...44I, 2020ApJ...891..164S, 2015ApJ...801...63M (80) |
| Assumed 16O/18O, Galactic | 557-560 | 250-570 | 9 at 557-560; 3 at 570; 4 at 500; 1 at 550; 1 at 450; 1 at 300; 1 at 250 | 2016ApJ...823L..18H, 2019A&A...631A..25J, 2019ApJ...883...98Z, 2015ApJ...798...85P, 2015ApJ...810..112O |
| Assumed 18O/17O | 3.6 | 3.6-3.65 | 3 | 2013ApJ...770..142N, 2020MNRAS.493L.108B, 2018ApJ...868...80C |
| Shared Tex for the pair | same Tex for both lines | fixed 15 K (2019A&A...624A.125M) to Tex = peak Tb of thick CO (2026A&A...705A.198M) | 9 | 2020MNRAS.496..394R, 2014ApJ...795...28B, 2019ApJ...876...72L |
| Beam filling / covering factor | 1, or equal for both lines | 0.3-1 | 7 state a value or equality; 3 more flag it as a limitation | value 1: 2016ApJ...820...19T, 2019A&A...629A.128W, 2020A&A...637A...7M, 2025A&A...695A.149K; equal: 2017MNRAS.466...49J, 2018ApJ...856...97S; 0.3-1: 2014A&A...566L...6M; limitation only: 2025ApJS..276...49J, 2019ApJ...876...72L, 2017A&A...606A.109M |
| Detection cut for the weak isotopologue | 3 sigma (masks), 5 sigma (ratio maps) | 3-5 sigma | 3 | 2020ApJ...898...97B, 2020MNRAS.496..394R, 2019A&A...629A...6T (5 sigma, card) |
| Tex for deuterated columns | two bracketing values, or Tex/Tkin = 0.5 | 8-80 K | 2 | 2017A&A...606A.125S, 2020ApJ...895..119T |

Galactocentric scaling is done in the pack: 12C/13C = 62, 16O/18O = 450, 14N/15N = 422 at 7.02 kpc
(2019A&A...624A..82B); 12C/13C = 50 at 6.5 kpc (2014A&A...569A..11S). Recommendation: take the reference
ratio from the source's galactocentric radius, not a single "ISM" number, and show how the result moves
over the 60-77 range when the source is local.

Two oxygen values in the pack are left out of the ranges above on purpose. 2015ApJ...799..204C is written
"18O/16O=540±30" in the pack, which cannot be right as written (a ratio of 540 must be 16O/18O); treat it
as unresolved until the paper is checked. 2020A&A...637A...7M lists 16O/18O = 69 +/- 11, a value for the
z = 0.89 absorber toward PKS 1830-211, not a Galactic reference.

## Software

From the pack aggregates (matched steps only; most cards do not name software for this step):

| Use | Software (pack count) |
|---|---|
| LTE column densities of each isotopologue | MADCUBA 2 (+SLIM 1, MADCUBAIJ 1), CASSIS 2, Weeds 2, XCLASS 1, myXCLASS 1, MAGIX 1 |
| Non-LTE columns / excitation check | RADEX 4 (+1 "van der Tak 2007"), LVG codes 2, RATRAN 2, LIME 5 |
| Disk forward models with fixed isotope ratios | RADMC-3D 3, DALI 2, RAC2D 2, vis_sample 1, Whitney MCRT 1 |
| Planetary atmospheres retrievals | NEMESIS 2 |
| Imaging, smoothing, masks | CASA 5 (+CASA 4.4.0 1, imsmooth 1), MIRIAD 1, GILDAS 1, GILDAS/MAPPING 1, CLASS 1 |
| Statistics on ratios | scipy 1 (Spearman), LTSFIT 1, MATLAB 1 |
| Chemistry with fractionation | DALI isotope network (2024ApJ...965..147B), UCLCHEM 1, ALCHEMIC 1 |

## Pitfalls

- **Thick main line.** Ratios of a thick main line to a rare one underestimate the isotope ratio. 2017A&A...597A..99W
  had to assume 12CO optically thin to equate 12CO/13CO with 12C/13C; R Scl intensity ratios ignore optical
  depth (2013A&A...556L...1V); the HCN/DCN case moved by a factor 5-7 with an opacity correction
  (2020ApJ...898...97B). Prefer a double-isotope or hyperfine route.
- **The "thin" rare line may not be thin.** C18O optical depth was called "a major uncertainty"
  (2020ApJ...898...97B); 13CO was moderately thick in NGC 253 (2019A&A...624A.125M); HC3N is thick at Titan's
  poles (2019Icar..319..417T); a H2CO isotopologue ratio of ~4 implied thick emission (2025A&A...693A.101T).
- **Assumed elemental ratio propagates.** The 12C/13C in HC3N could be as low as 43, not the assumed bulk value
  (2018ApJ...859L..15C); 12C/13C uncertain by a factor ~2 (2017MNRAS.466...49J); if 12C/13C exceeds 77 the
  derived tau is a lower limit (2019ApJ...885L..39H); a gas mass shifts by factor 2 down to 5 up from the
  isotope ratio alone (2013ApJ...776...77K).
- **Not co-spatial.** D fractions are lower limits when species are not co-located (2017A&A...606A.125S); CN
  and C15N co-spatiality is "hard to assess" (2017A&A...603L...6H); disk models predicted cospatial
  isotopologues that the data did not show (validation line in the pack aggregates).
- **Different missing flux.** Each isotopologue is filtered differently (2019A&A...629A...6T card); extended
  emission resolved out biases abundances (2014A&A...569A..11S, 2018A&A...615A..28D); near systemic velocity
  emission was attenuated and R13/18 became a lower limit (2019ApJ...875...62Y).
- **Excitation and filling.** A single Tex is "a large source of uncertainty" (2020MNRAS.496..394R); beam
  filling may differ between tracers (2018ApJ...856...97S); a fixed filling factor makes columns lower limits by
  ~2-3 (2025ApJS..276...49J); covering factor 0.3-1 is poorly known in absorption (2014A&A...566L...6M).
- **Fractionation and selective photodissociation are often ignored.** 2019A&A...624A.125M says it cannot
  constrain fractionation; 2021ApJ...908....8C did not include CO fractionation; 2024ApJ...965..147B shows
  C2H and CO can carry different 12C/13C.
- **Spectroscopy.** CH3OD partition function (2019A&A...632A..19T) and CH2DOH spectroscopy uncertain by
  ~factor 3 (2024AJ....167...66Y); collision rates borrowed from NH3 for NH2D (2013ApJ...777...85N) and from
  N2H+/HCN for N2D+/DCN (2017A&A...606A.125S card).
- **Dust blocks or suppresses the lines.** Optically thick dust hides molecules near the disk midplane
  (2017ApJ...843...27L), and continuum oversubtraction or blocking may reduce line flux (2025A&A...693A.101T).
  Before reading a line deficit or a ratio, check the dust optical depth at both line frequencies and whether
  continuum subtraction could have removed line emission; a pair at different frequencies sees different
  dust opacity.
- **Time variability.** Non-simultaneous XD and XH observations of a variable absorber add error
  (2020A&A...637A...7M).
- **Settings the cards flag as not stated.** Line-free channels and continuum subtraction (about 40 flags
  across differently worded variants), CASA version (11 + 2), self-calibration intervals (5 + 2 + 2), flux
  scale uncertainty (3 + 2). For a weak isotopologue the continuum level matters: STATCONT was "not optimal"
  near the noise (2021A&A...656A..46M); N2D+ continuum subtraction was less accurate on an atmospheric
  feature (2017A&A...606A.125S). See **continuum-subtraction**.

## Verification checks

What papers did:
- Vary Tex and show the ratio barely moves: 10 and 20 K changed columns by ~5% and ~10% but ratios were
  nearly unchanged (2019A&A...624A.125M).
- Two transitions of the same isotopologue give consistent abundances (C18O 3-2 and 2-1 in 2016ApJ...821L...8S);
  the best fit reproduces lines not used in the fit (2020ApJ...890...95I).
- Two independent ratio estimators agree: integrated opacity vs Gaussian fit, 3.46 vs 3.50
  (2015A&A...582L...4M); ortho and para lines fitted separately (2019A&A...629A.128W).
- Thinness of the rare line from its own hyperfine ratios (13CN ratios 1.03-1.25, consistent with thin LTE,
  2019A&A...629A...6T card); the four weakest CN hyperfine lines, scaled by intensity, have matching
  profiles, so they are thin (2017A&A...603L...6H card).
- Geometry perturbation: random changes to the imposed uv geometry moved the ratio by ~0.1 sigma
  (2017A&A...603L...6H card).
- Compare with single dish and literature (2019A&A...629A...6T, 2021A&A...656A..46M), with an earlier result on the
  same source (HH 212 deuteration vs 2.4 +/- 0.4%, 2019A&A...632A..19T), with opacity-corrected and uncorrected
  versions both shown (2020ApJ...898...97B).
- Temperature-profile perturbation of 5 K changed retrieved abundances by < 20% (2019Icar..319..417T).

What a careful referee adds:
- Missing-flux fraction for each isotopologue separately, not one number for the pair.
- The calibration covariance of the two lines: cancellation claimed only for a multiplicative error shown to
  be common, with a differential calibration term kept even when both lines share an execution.
- The ratio recomputed at two or three clip or mask thresholds, and bounds (with confidence level) for
  nondetections.
- Dust optical depth at both line frequencies and a check that continuum subtraction did not remove line flux.
- The elemental reference ratio, its galactocentric radius and its uncertainty, with the result recomputed at
  both ends.
- For D/H: the statistical correction applied and the partition function source.
- A blend check for each weak line against an LTE model of the full band.

## Source cards

All 99 papers with titles are in `references/sources.md`. Most informative for this technique:

- 2019A&A...624A.125M (resolved C, O ratios with thin CO isotopologues, Tex test)
- 2021A&A...656A..46M (ALCHEMI: ratios for C, O, N, S, Si; source-size test)
- 2019A&A...629A...6T (CN/13CN with hyperfine opacity and missing-flux check)
- 2017A&A...603L...6H (CN/C15N via uv fit with fixed geometry, RADEX Tex check)
- 2020ApJ...898...97B (HCN/HC15N, HCN/DCN, opacity-corrected vs uncorrected)
- 2019A&A...632A..19T (CH2DOH/CH3OH from 13CH3OH, chi2 grid)
- 2016A&A...587A..91B (deuterated COMs, Weeds, statistical conformer split)
- 2018A&A...620A.170J (PILS D and 13C in O-bearing COMs, statistical correction)
- 2017A&A...606A.125S (DCO+, DCN, N2D+ ring models in a disk)
- 2024ApJ...965..147B (C2H vs CO 12C/13C, DALI fractionation models)
- 2014ApJ...795...28B (tau from HCO+/H13CO+)
- 2020MNRAS.496..394R (per-pixel tau maps from CO isotopologues)
- 2018A&A...615A..28D (intensity-ratio corrections, Si, S, Cl in AGB stars)
- 2016ApJ...821L...8S (Titan C and O ratios with NEMESIS)
- 2019A&A...629A.128W (35Cl/37Cl free in a joint absorption fit)
- 2015A&A...582L...4M (36Ar/38Ar in absorption, two estimators)
- 2013A&A...556L...1V (12CO/13CO maps around an AGB star)
- 2019ApJ...885L..39H (tau of [CI] from [13CI])
- 2019A&A...624A..82B (galactocentric reference ratios)
- 2015ApJ...801...63M (LVG modelling of isotopologue ratios in a starburst)
