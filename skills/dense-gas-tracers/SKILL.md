---
name: alma-dense-gas-tracers
description: "Measure and interpret HCN, HCO+, HNC, CS and N2H+ emission in galaxies and the Milky Way ISM with ALMA: matched-beam line-ratio maps and radial profiles, dense-gas fractions (HCN/CO) and conversion factors (alpha_HCN, alpha_HCO+), dense-gas star formation efficiency (SFR/HCN), AGN versus starburst diagnostics from HCN/HCO+ and HCN/HNC (with their competing explanations: excitation, abundance, opacity, IR pumping), multi-J excitation checks, vibrationally excited HCN, and the artefact checks a ratio needs. Use when forming or checking a dense-gas line ratio, turning HCN or HCO+ into a dense gas mass, testing whether an elevated HCN/HCO+ means an AGN, or building a dense-gas star formation relation. Built from 180 ALMA papers (2013-2026)."
---

# Dense gas tracers: HCN, HCO+, HNC, CS and N2H+ ratios

These lines trace gas denser than the bulk CO-emitting gas. Papers use them three ways: as a dense-gas fraction
(HCN/CO) and dense-gas star formation efficiency (SFR/HCN), as excitation and chemistry probes (multi-J and
cross-species ratios), and as AGN versus starburst diagnostics (HCN/HCO+, HCN/HNC, HCN/CS). The two mistakes that
matter most: (1) dividing two maps that differ in beam, uv coverage, mask or flux scale, so the ratio holds the
artefact rather than the gas (2017ApJ...843..136E, 2022A&A...667A.131B, 2024A&A...691A.121N); (2) reading an
elevated HCN/HCO+ as "AGN" when abundance, opacity, excitation, mechanical heating and IR pumping can all raise
it (2014A&A...570A..28V, 2018ApJ...856..143I, 2020ApJ...902...99I, 2025ApJ...985..259J).

## Agent checklist

1. **Check the pairing first.** Same-J HCN and HCO+ taken simultaneously share calibration and astrometry
   (2026ApJ..1004...39I). Lines from different tunings or bands carry their own flux-scale error: 5% (Band 5)
   and 10% (Bands 6, 7), doubled for Cycle 0, in 2023ApJ...950...75I; 10% for Band 6 in 2025ApJ...985..259J.
   Add these in quadrature to every cross-band ratio.
2. **Match beam, grid and spatial filtering before dividing.** Convolve to the coarsest beam and resample onto a
   beam-spaced grid so each pixel is an independent sightline (hexagonal grid in 2024A&A...691A.121N). If one
   line has 7m/TP data and the other does not, treat the ratio as unreliable on scales above the shorter
   maximum recoverable scale.
3. **Default mask when the paper is silent:** a CO-based velocity mask, 4 sigma seed grown into channels above
   2 sigma, applied to both lines (2024A&A...691A.121N, 2025A&A...693L..13N); a pixel counts as detected at
   S/N >= 3 (2024A&A...691A.121N, 2023MNRAS.521.3348N). For per-pixel ratio maps require > 3 sigma in both
   lines (2026ApJ..1004...39I).
4. **Do not average detections.** S/N clipping biases detected-pixel means toward high HCN/CO and low SFR/HCN
   (2024A&A...691A.121N). Stack in bins of an independent quantity (CO intensity, radius, pressure) and fit
   with a method that takes upper limits (LinMix, 5 papers in pack aggregates).
5. **Conversion factor default:** match the comparison sample. Nearby-disc HCN/CO work uses alpha_HCN = 14-15
   with alpha_CO = 4.35 (2018ApJ...868L..38G, 2024A&A...691A.121N, 2023MNRAS.521.3348N, 2025A&A...693L..13N);
   most other work (starbursts, AGN hosts, mergers, high z) uses 10 Msun (K km/s pc^2)^-1 (11 papers, my count
   of pack lines, e.g. 2017ApJ...850..170O, 2019ApJS..241...19I). Quote a factor-of-a-few uncertainty on f_dense
   (2024A&A...691A.121N).
6. **AGN decision rule.** HCN/HCO+ > 1 alone is not evidence for an AGN. Claim AGN-driven chemistry only after
   isotopologue ratios rule out opacity, multi-J fits rule out an excitation difference, and HCN-vib limits
   address IR pumping (Step 8). Reading the isotopologue test (general practice; always compare a species with
   its own isotopologue, HCN/H13CN and HCO+/H13CO+, against 12C/13C, never H13CN/H13CO+): if HCN/H13CN is close to the
   adopted 12C/13C (50-100), HCN is optically thin and opacity cannot explain the ratio; if it is far below
   12C/13C, HCN is optically thick and the main-line ratio understates the column ratio, so correct with
   H13CN/H13CO+. Then compare the abundance ratio with XDR, PDR, cosmic-ray and shock chemistry models before
   naming a driver, and bring in independent tracers (SiO for shocks, X-ray luminosity) where they exist. If these tests are not possible with the data, write "consistent with" and list
   the explanations still allowed.
7. **Excitation fits need enough ratios.** If the independent ratios are fewer than the free parameters
   (2018ApJ...856..143I, 2023ApJ...950...75I), fix N_HCO+ = 1e16 cm^-2 and [HCN]/[HCO+] = 3 and show the
   result under the alternatives (1e15, ratio 1) (2023ApJ...950...75I, 2023ApJ...954..148I).
8. **Upper limits:** 3 sigma over the line width of a detected line from the same region (2013PASJ...65..100I,
   2017ApJ...850..170O, 2021A&A...649A.105F, 2025ApJ...985..259J). Carry ratios built from limits as limits
   (2023A&A...679A.119R).
9. **Write down:** beam and pixel grid, mask recipe, velocity window, ratio unit (K km/s or Jy km/s), J levels,
   alpha_CO, R21 and alpha_HCN, flux-scale uncertainty, arrays combined, continuum channel ranges, and for each
   ratio the check that backs its interpretation.

## When to use

- HCN/CO dense-gas fractions and SFR/HCN efficiencies across discs, bars, centres and pressure
  (2018ApJ...868L..38G, 2024A&A...691A.121N, 2023MNRAS.521.3348N, 2025A&A...693L..13N, 2023ApJ...945...42B).
- HCN/HCO+ and related ratios in AGN and (U)LIRG nuclei (2013PASJ...65..100I, 2016AJ....152..218I,
  2018ApJ...856..143I, 2022A&A...667A.131B, 2024A&A...686A..48N, 2026ApJ..1004...39I).
- Multi-J excitation of dense gas (2013PASJ...65..100I, 2023ApJ...950...75I, 2024ApJ...977...38B).
- Obscured nuclei and HCN-vib searches (2015A&A...584A..42A, 2021A&A...649A.105F, 2025ApJ...985..259J).
- Dense gas in low-metallicity and high-z systems (2014ApJ...793...37A, 2020ApJ...902..140N,
  2017ApJ...850..170O, 2018A&A...620A.115B, 2023A&A...679A.119R).
- Dense gas in outflows and streamers (2018ApJ...868...95M, 2024A&A...687A..43B, 2024A&A...689A.163L).

## When not to use

| Situation | Use instead |
|---|---|
| Making the moment maps themselves (masks, windows, clipping) | `alma-moment-maps` |
| Full non-LTE grid or Bayesian excitation fit as the main result | `alma-non-lte-excitation` (this skill covers only the ratio-specific settings) |
| Total molecular gas from CO, alpha_CO and R21 choices | `alma-gas-mass-co-conversion` |
| Kennicutt-Schmidt relations with total gas | `alma-star-formation-laws` |
| HCO+, HCN or HNC seen in absorption against a continuum source (diffuse Milky Way gas, quasar sightlines) | `alma-absorption-lines`: N(HCO+) = 1.10e12 cm^-2 x integral tau dv with X(HCO+) = 3e-9 (2018A&A...610A..49L, 2025A&A...699A..17L) |
| 12C/13C or 14N/15N from H13CN, H13CO+, N15NH+ | `alma-isotopic-ratios` |
| Cosmic-ray ionisation or time-dependent chemistry from HCN/HNC | `alma-chemical-modelling` (emulator plus UltraNest in 2024ApJ...977...38B) |
| N2H+ filament or core kinematics in Milky Way clouds | `alma-envelope-kinematics-pv`, with hyperfine fits (PySpecKit, 9 papers in pack aggregates; CLASS hfs in 2021MNRAS.503.4320F) |

## Steps

1. **Inventory the lines and how they were taken.**
   - List species, J, band, array configurations and whether HCN/HCO+ share a tuning (same-J pairs were
     "taken simultaneously" in 2026ApJ..1004...39I). Cross-band ratios inherit the per-band flux-scale error
     (checklist item 1).
   - Check for blends before trusting a flux. HNC(5-4) blends with CN(4-3) at high z: fit both together with a
     common width and velocity offset and test recovery on simulations (2018A&A...620A.115B; also
     2021A&A...645A..45C). General practice: in broad nuclear lines, vibrationally excited HCN (v2=1f) lies
     about 400 km/s from HCO+ at J=3-2 and 4-3, so check HCO+ for HCN-vib contamination; 2020ApJ...902...99I
     notes a weak HCO+-VIB candidate "may be HOC+".
2. **Image and subtract continuum, with care near bright nuclei.**
   - CASA (34 papers) with tclean (7); MIRIAD (4) and GILDAS (4) in older or Milky Way work (pack aggregates).
     Weighting varies: robust 0.5 (2026ApJ..1004...39I, 2024ApJ...963..115L), robust 1.0 for HCN, HCO+, CS
     (2024ApJ...967..133S), uniform (2022A&A...667A.131B).
   - Line-free channel ranges are the most commonly unstated setting (34 card entries over 11 phrasings, my
     count of pack aggregates); record them. Broad lines (200-800 km/s FWHM in 2023ApJ...950...75I) need wide
     cubes: 2026ApJ..1004...39I imaged +/-1500 km/s around each line.
   - Toward a strong continuum, HCN and HCO+ can appear in absorption: 2020ApJ...902...99I used the absorption
     at the continuum peak to measure an outflow and, from H13CN/H13CO+ absorption, the abundance ratio;
     2025ApJ...995..211I took a ~350 K background from the continuum brightness. Do not read a dip at the
     nucleus as a ratio change without checking the continuum-subtracted and unsubtracted spectra.
   - Faint lines: dirty images with uv tapers to tame sidelobes from mixed configurations
     (2023A&A...679A.119R).
3. **Match beam, uv coverage and grid.**
   - Convolve all lines (and SFR maps) to one beam and reproject onto a beam-spaced grid (2024A&A...691A.121N;
     common beams in 2013PASJ...65..100I and 2022MNRAS.510.4485R).
   - Match spatial filtering, not only the beam: 2017ApJ...843..136E built ratio maps at matched uv range and
     resolution after finding ~50% of CO(3-2) flux missing. 2024A&A...691A.121N combined 12m, 7m and TP for
     HCN. 2018ApJ...868L..38G checked ALMA HCN/CO against single-dish EMPIRE and found agreement within
     0.06 dex.
   - When data at different resolutions must be combined, 2022A&A...667A.131B grouped data by resolution and
     scaled intensities with I_source = ((theta_s^2 + theta_b^2) / theta_b^2) I_beam, taking the coarsest
     beam as the source size. Treat this as an assumption to state, not a correction to trust.
4. **Mask, integrate, estimate noise.**
   - Mask on the brighter independent line (CO) and apply it to the faint tracer (2024A&A...691A.121N,
     2018ApJ...868L..38G); seed-and-grow recipes: 4 to 2 sigma (2024A&A...691A.121N, 2025A&A...693L..13N),
     S/N > 4 to 2 (2024A&A...689A.122B), >= 4 in >= 3 channels to >= 2 (2023MNRAS.521.3348N). These build
     masks; they are not detection criteria.
   - Uncertainty (independent channels; if Hanning-smoothed or channels narrower than the resolution, integrate
     line-free windows of the same width instead): rms of emission-free channels times sqrt(N_channels) times channel width
     (2024A&A...691A.121N). For aperture spectra, Gaussian fits with flux over twice the FWHM
     (2025ApJ...985..259J); single and double Gaussian fluxes agreed within ~10% (2023ApJ...950...75I).
5. **Form ratios, profiles and stacks.**
   - State units. A ratio in Jy km/s differs from one in K km/s by (nu1/nu2)^2 (general practice): negligible
     for same-J HCN/HCO+, large across J. 2017ApJ...843..136E quotes CO(6-5)/CO(3-2) as 0.2-1.4 in Tmb and
     0.9-5.9 in flux units.
   - Ratio maps: mask where either line is below 3 sigma (2026ApJ..1004...39I, 2022A&A...667A.131B). Masking
     only on HCN (2025ApJ...985..259J) selects HCN-bright pixels; note the bias.
   - Profiles and trends: stack spectra at the CO velocity (2025A&A...693L..13N) in 10-20 bins per galaxy
     (2025A&A...693L..13N, 2023MNRAS.521.3348N). Stacking agreed with mask-and-average within ~10%
     (2018ApJ...868L..38G). Fit with LinMix (upper limits), MARS via R `earth` for breaks
     (2024A&A...691A.121N), or bisector fits (2018ApJ...868L..38G). See `alma-stacking`.
   - Compare at matched physical resolution only: the HCN/CO slope against cloud-scale CO intensity was 0.81 at
     650 pc and 0.41 at 2770 pc (2018ApJ...868L..38G), and 260 pc scatter was twice the kpc-scale scatter
     (0.28 versus 0.14 dex, 2024A&A...691A.121N).
6. **Dense-gas fraction, mass and efficiency.**
   - f_dense = (alpha_HCN / alpha_CO) x HCN/CO; with alpha_HCN = 14 and alpha_CO = 4.35, f_dense ~ 2.3 HCN/CO
     for CO(1-0) (2018ApJ...868L..38G), ~2.1 W_HCN/W_CO(2-1) with R21 = 0.65 (2024A&A...691A.121N). Keep
     alpha_HCN constant unless you have a reason (2024A&A...691A.121N); alpha_HCN/alpha_CO = 3.2 fixed when
     alpha_CO varies (2023ApJ...945...42B, 2024A&A...692A.146B).
   - HCO+ masses: alpha_HCO+ = 10 (2015ApJ...813..118M, 2023ApJ...942...25F, 2024ApJ...963..115L) or 2-5 for
     thermalised optically thick nuclei (2020ApJ...902...99I, 2022ApJ...926..159I). Near an AGN where HCN is
     overabundant, 2020ApJ...902...99I adopted the HCO+ mass (HCN gave 4-5 times more).
   - Only high-J data: papers assume thermalised optically thick emission, L'(1-0) = L'(3-2)
     (2018ApJ...853L..25I, 2020ApJ...902...99I), or a measured or literature ratio: HCN(3-2)/(1-0) = 0.5
     (2025ApJ...985..259J), 0.3 (2024A&A...689A.163L), HCN(4-3)/(1-0) = 0.6 +/- 0.2 (2015ApJ...811...39I),
     r_5,1 = 0.25 (2026MNRAS.549ag931B). General practice: assuming thermalisation gives the smallest L'(1-0),
     so the mass is a lower bound if the gas is subthermal.
   - Low-metallicity clumps: LTE masses from HCO+ with Tex = 30 K and X(HCO+) = 1e-9 (2014ApJ...793...37A,
     2020ApJ...902..140N); report the Tex sensitivity (+39% at 20 K, -28% at 40 K in 2020ApJ...902..140N) and
     the alpha_CO alternative (f_dense 0.025 versus 0.013).
   - SFR/HCN: Balmer-corrected Halpha checked against 33 GHz (within 20%) and 21 um (2024A&A...691A.121N);
     IR-based SFR with C_IR = 1.48e-10 Msun/yr/Lsun (2025A&A...693L..13N). See `alma-star-formation-laws`.
7. **Check excitation with multi-J ratios.**
   - RADEX dominates (33 papers, plus pyradex 5, SpectralRadex 3; pack aggregates). Typical settings: uniform
     sphere or LVG, H2-only collisions, T_bg = 2.73 K at z = 0 (2023ApJ...950...75I, 2013PASJ...65..100I), CMB
     at the source redshift for high z (7.004 K in 2017ApJ...850..170O). Line width set from the data:
     250 km/s (2013PASJ...65..100I), 400 or 1000 km/s (2018ApJ...856..143I), 500 km/s (2023ApJ...954..148I).
   - Fit flux-scale factors as bounded nuisance parameters (0.95-1.05 for Band 5, 0.9-1.1 for Bands 6-7;
     emcee with 100 walkers, 100 tau steps, 5 tau burn-in in 2023ApJ...950...75I).
   - If low-J and high-J ratios cannot be fitted together, the gas is multi-component: 2013PASJ...65..100I
     found chi2 = 7.774 for the joint fit and used only high-J ratios. Say which component the result describes.
   - Collision rates matter at the factor-2 level in intensity but barely moved medians (2024ApJ...977...38B);
     HCO+ electron collisions were included in 2024A&A...686A..48N. Use `alma-non-lte-excitation` for the fit.
8. **Diagnose AGN versus starburst.** Work through the explanations in order and record which survive.

   | Explanation | Test papers used | Example |
   |---|---|---|
   | Opacity: HCN thick, HCO+ thinner (or the reverse) | Main-to-13C ratios against 12C/13C = 50-100 to correct the intrinsic ratio | 2018ApJ...856..143I; HCN/H13CN = 8 in IRAS 22491-1808 |
   | Excitation: different n, T in AGN gas | Multi-J RADEX fits with the abundance ratio free or fixed | 2023ApJ...950...75I, 2013PASJ...65..100I |
   | Abundance: HCN enhanced by X-rays, heating, shocks | H13CN/H13CO+ (> 3 in the NGC 1068 torus, 2020ApJ...902...99I); non-LTE [HCN]/[HCO+] = 5-20 (2013PASJ...65..100I); column ratio 10 across the CND (2014A&A...570A..28V) | |
   | Mechanical heating, outflows | Ratio peaks off-nucleus or in line wings; PPV geometry of the top-10% ratio pixels | 2025ApJ...985..259J, 2024A&A...686A..48N, 2026ApJ..1004...39I |
   | IR pumping via v2=1 | HCN-vib detection or limits; CON criterion Sigma_HCN-vib >= 1 Lsun/pc^2 on ~100 pc scales, or L_HCN-vib/L_IR > 1e-8 | 2025ApJ...985..259J, 2021A&A...649A.105F; 2014A&A...570A..28V lists the omission as a limitation |
   | Metallicity (low N/C/O lowers HCN) | PDR grids across Z | HCO+/HCN(4-3) >= 2.2 read as Z = 0.5 Zsun (2023A&A...679A.119R); HCN/HCO+ = 0.2 in 30 Dor (2014ApJ...793...37A) |

   - Measured spread to anchor expectations (same J): starburst NGC 1614 0.18 at 4-3 (2018ApJ...856..143I) and
     0.56 / 0.38 / 0.31 at 2-1 / 3-2 / 4-3 (2023ApJ...950...75I); IRAS 15250+3609 3.0 at 4-3
     (2018ApJ...856..143I); NGC 1097 2.0 at 4-3 (2013PASJ...65..100I); Cen A 0.37 at 4-3
     (2017ApJ...843..136E).
   - Resolution changes the answer. In NGC 1068 at ~40 pc, HCN(1-0)/HCO+(1-0) is 1.01 at the AGN but 3.64 at
     CND-S, and 0.62 in a starburst-ring region (2022A&A...667A.131B), whose authors say the HCN(4-3)/HCO+(4-3)
     and HCN(4-3)/CS(2-1) diagnostics need confirmation in other galaxies.
   - HCN/HNC: high values were explained only by PDR models in 2017ApJ...850..170O; X_HCN/X_HNC > 4 flagged
     regions where the cosmic-ray chemistry model fails (UV or shocks) in 2024ApJ...977...38B.
9. **Report** every ratio with its unit, beam, aperture or mask, statistical error, and the systematic budget
   (flux scale per band, missing flux, conversion factor), plus the test from Step 8 that supports its reading.

## Parameter defaults and ranges

| Parameter | Common choice | Range seen | Papers (count) | Examples |
|---|---|---|---|---|
| alpha_HCN, Msun (K km/s pc^2)^-1 | 10 (starbursts, AGN hosts, mergers, high z); 14-15 (nearby-disc HCN/CO) | 3.1-27; 6-40 quoted range | 11 at 10, 4 at 14-15 (my count) | 2019ApJS..241...19I (10, 6-40), 2025A&A...693L..13N (15), 2015ApJ...806L..34F (~27), 2024A&A...684L..11G (~3.1) |
| alpha_HCO+ | 10 | 2-5 in thermalised nuclei | 3 at 10, 2 at 2-5 | 2015ApJ...813..118M, 2022ApJ...926..159I |
| alpha_CO (with HCN/CO) | 4.35 | 0.8-20 | 6 at 4.35, 2 at 4.3 (my count) | 2015ApJ...803...60S (0.8), 2024A&A...689A.122B (4.2-20) |
| R21 | 0.65 | 0.54 median map; Sigma_SFR scaling | 3 | 2024A&A...691A.121N, 2023MNRAS.521.3348N (0.64), 2025A&A...693L..13N |
| Mask | CO-based, 4 sigma seed to 2 sigma | 4-5 seed, 2-3 grow | 5 | 2024A&A...691A.121N, 2023ApJ...945...42B (5 to 3) |
| Detection / ratio threshold | S/N >= 3 | 2.5-3 | 6 (my count) | 2024ApJ...963..115L (2.5), 2026ApJ..1004...39I |
| Channel width (galaxies) | 5-20 km/s | 5-105 km/s | 6 (my count) | 2024A&A...691A.121N (5), 2024ApJ...967..133S (10), 2026ApJ..1004...39I (20), 2022MNRAS.510.4485R (105 for HCO+/CO) |
| RADEX n_H2 grid, cm^-3 | 1e2-1e7 | 1e1-1e9 | 9 (my count) | 2013PASJ...65..100I, 2023ApJ...950...75I (1e3-1e8), 2024A&A...686A..48N |
| RADEX T_kin grid, K | lower edge 5-10, upper 130-1000 | 5-1000 | 8 (my count) | 2013PASJ...65..100I, 2023ApJ...950...75I, 2018ApJ...856...97S |
| Fiducial N_HCO+, [HCN]/[HCO+] | 1e16 cm^-2, 3 | 1e14-1e17; 0.1-10 | 3 | 2023ApJ...950...75I, 2023ApJ...954..148I, 2018ApJ...856..143I |
| Abundances for masses | X(HCO+) 1e-9 to 1e-8; X(HCN) 1e-8 to 2e-8 | X(HCO+) 1e-9-1e-8 | 6 | 2013PASJ...65..100I (5e-9), 2018ApJ...856..143I (1e-8), 2017ApJ...850..170O (2e-8) |
| 12C/13C for opacity | 50-100 (ULIRGs) | 18-100 | 5 (my count) | 2018ApJ...856..143I, 2016ApJ...825...44I, 2014A&A...570A..28V (18, 24), 2021A&A...649A.125W |
| Flux-scale error per band | 5% B3-5, 10% B6-7 | doubled for Cycle 0; 50% on high-z ratios | 4 | 2023ApJ...950...75I, 2025ApJ...985..259J, 2023A&A...679A.119R |
| Upper limits | 3 sigma, detected-line width | 1-3 sigma | 7 (my count) | 2021A&A...649A.105F, 2024ApJ...969..102N (1 sigma) |

## Software

| Job | Package (pack aggregate count) | Setting that matters |
|---|---|---|
| Calibration, imaging, continuum | CASA (34), tclean (7), imcontsub (2), feather (3), PHANGS-ALMA pipeline (2) | line-free channels; arrays combined (2024A&A...691A.121N used the pipeline) |
| Cube handling, moments, spectra | spectral-cube (6, plus 2 as spectralcube), astropy (5), specutils (2025ApJ...985..259J), CubeLineMoment (2024ApJ...977...38B) | common beam and grid before ratios |
| Line fitting, hyperfine | PySpecKit (9), GILDAS (4), CLASS (3), GILDAS/CLASS (2), lmfit (4) | fix hyperfine separations; one T_ex for all components (2021MNRAS.503.4320F) |
| Excitation | RADEX (33), pyradex (5), SpectralRadex (3), LAMDA data (3), Myradex (2017ApJ...850..170O), DESPOTIC (2) | collision partner, T_bg, line width, column per width |
| Samplers | emcee (2), UltraNest (3), corner (2) | autocorrelation length; flux-scale nuisance terms |
| Regression with limits | LinMix (5), R `earth` MARS (2) | fit binned stacks, check against per-pixel fits |
| Chemistry | UCLCHEM (2), KIDA (2), TensorFlow emulators (2) | see `alma-chemical-modelling` |
| Lensed sources | Lenstool (2021A&A...645A..45C) | line-specific magnification |

Reach for these instead of writing a new fitter or LVG solver.

## Pitfalls

- **Mismatched filtering.** Missing flux is common: factor ~2 (2013AJ....146...47I), ~50% of CO(3-2)
  (2017ApJ...843..136E), masses as lower limits without short spacings (2019ApJ...883..193N). Combining ALMA with
  IRAM 30m added ~37% uncertainty in 2023ApJ...942...25F. A ratio with HCN from the 12m alone and CO from
  12m+7m+TP is biased low wherever the dense gas sits in extended structure.
- **Beam larger than adopted.** 2023ApJ...950...75I had native beams larger than its adopted beam for some
  transitions and had to assume the emission came from the adopted area.
- **S/N selection.** Clipped means favour bright HCN (2024A&A...691A.121N); compounding errors in ratios of
  faint lines limit what can be said (2026MNRAS.549ag931B).
- **Optical depth saturation.** At high N_HCO+ and [HCN]/[HCO+], HCN saturates and the fitted abundance ratio
  becomes a lower limit (2023ApJ...950...75I).
- **Single-zone models of mixed gas.** RADEX assumes all lines sample the same gas (2014A&A...570A..28V);
  density and temperature from J <= 3 lines are degenerate (2023ApJ...942...25F); large regions mix diffuse
  and dense gas (2024ApJ...977...38B); fits were poorly constrained in T and n in 2022A&A...667A.131B.
- **Lensing.** Differential magnification is a main uncertainty (2017ApJ...850..170O); HNC(5-4) had
  mu = 16.3 against 22.0 for CO(4-3) in 2021A&A...645A..45C.
- **Conversion factors.** HCN-to-dense-gas conversion and the density HCN traces remain uncertain
  (2018ApJ...868L..38G); an alpha_HCN from bound clumps overestimates mass in unbound outflow gas (factor ~5
  reduction considered in 2024A&A...689A.163L).
- **Obscured nuclei.** Very high columns make lines opaque and self-absorbed (2015A&A...584A..42A,
  2016A&A...590A..25M), so ground-state ratios there say little about chemistry.
- **Unstated settings.** Cards flag CASA version (28 entries over 5 phrasings), flux-scale uncertainty (10
  entries over 3 phrasings) and 7m/12m combination (2) as not stated (my counts of pack aggregates). When
  reproducing, assume the archive pipeline defaults, flag them, and check them against reported noise.
- **Overreach.** In CosmicCoder agent runs, conclusions were more confident than the evidence. Here this means
  calling a ratio an AGN signature from one transition at one resolution. If the Step 8 tests cannot be run,
  record the question as open instead of iterating on speculation.

## Verification checks

- Ratio reproduces from independent extraction: stacking versus mask-and-average within ~10%
  (2018ApJ...868L..38G); single versus double Gaussian within ~10% (2023ApJ...950...75I).
- Interferometer against single dish: 0.06 dex agreement in 2018ApJ...868L..38G.
- Trends survive dropping the centre (positive slopes remained in 2024A&A...691A.121N) and per-pixel LinMix
  fits agree with binned fits within 1 sigma (2024A&A...691A.121N).
- SFR tracer cross-check (33 GHz within 20%, 2024A&A...691A.121N).
- Excitation: LM and MCMC agree (2023ApJ...950...75I); results stable when N_HCO+ and [HCN]/[HCO+] change;
  CO-only and CO+HCN fits give consistent T_kin and column (2017ApJ...850..170O); outflow masses from two J
  levels agree within ~30% (2018ApJ...856..143I).
- AGN claims: several independent lines point the same way (ratio, extent, mass ratio, HCN-vib, isotopologues
  in 2020ApJ...902...99I); HCN-vib searched off-peak too and resolution effects modelled (2025ApJ...985..259J).
- Detection rates on small samples get binomial intervals (beta quantiles, 0 +17/-0% in 2025ApJ...985..259J).
- A referee will also ask: are the units consistent, is each ratio on matched beams and uv ranges, are
  calibration and conversion-factor systematics in the error bar, and is the AGN reading tested against the
  other explanations rather than assumed.

## Source cards

Full list in `references/sources.md` (180 papers). Most informative here:

- Dense-gas fraction and efficiency: 2018ApJ...868L..38G, 2024A&A...691A.121N, 2023MNRAS.521.3348N,
  2025A&A...693L..13N, 2023ApJ...945...42B, 2024A&A...692A.146B, 2015ApJ...815..103B, 2023ApJ...942...25F,
  2024ApJ...963..115L
- AGN versus starburst ratios and excitation: 2013PASJ...65..100I, 2014A&A...570A..28V, 2018ApJ...856..143I,
  2020ApJ...902...99I, 2022A&A...667A.131B, 2023ApJ...950...75I, 2024A&A...686A..48N, 2026ApJ..1004...39I
- Obscured nuclei and HCN-vib: 2015A&A...584A..42A, 2021A&A...649A.105F, 2025ApJ...985..259J
- Low metallicity and high z: 2014ApJ...793...37A, 2020ApJ...902..140N, 2017ApJ...850..170O,
  2018A&A...620A.115B, 2023A&A...679A.119R
- HCN/HNC chemistry: 2024ApJ...977...38B
