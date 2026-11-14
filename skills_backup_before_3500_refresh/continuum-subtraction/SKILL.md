---
name: alma-continuum-subtraction
description: "Separate spectral-line emission from continuum in ALMA data: pick line-free channels, fit and subtract the continuum in the uv plane (uvcontsub) or image plane (imcontsub, STATCONT), and build the matching continuum image from the same channels. Use when making line cubes, moment maps, line fluxes or continuum images from ALMA spectral data, when a field is line-rich (hot cores, starbursts, spectral scans), when lines sit in absorption against bright continuum, or when a referee asks how the continuum was removed. Built from 656 ALMA papers (2012-2026)."
---

# Continuum subtraction and line-free channel selection

Continuum subtraction fits a low-order model of the continuum across channels that carry no line emission and
removes it, leaving a line-only cube; the same line-free channels give the continuum image. Two mistakes matter
most: (1) a wrong line-free channel set (line wings, blends or absorption inside the "continuum" channels) biases
both the line flux and the continuum flux, and (2) the channel set and fit settings are often not reported, so the
result cannot be reproduced. In the pack's "not stated" list, labels about line-free channels occur 208 times (sum
of the 15 variant labels shown; a card can carry more than one variant, so this is not a unique-card count). Across
the whole corpus, the continuum-subtraction setting is unstated in 65% of 1591 cards (`stats/README.md`; that
denominator includes papers with no line imaging).

**How the counts were made.** "Pack aggregate" means a number printed in the pack's aggregate sections. "My count"
means a regex count over the pack's `processing.imaging.*` parameter lines, which cover 426 of the 440 papers the
current parameter list shows (years 2012-2026; the list is truncated after about 700 lines, so roughly 216 of the
656 papers are not in it, and every "my count" is a lower bound). A paper is counted once per category; papers that
used two methods are counted in both. Patterns: uv plane = `uvcontsub`, "uv plane/domain/space", "visibilit",
GILDAS uv tasks, UVLSF; image plane = `imcontsub`, "image plane/domain/space", STATCONT, "per pixel"; first order =
`fitorder=1`, "first-order/degree", "linear fit/model/baseline"; zeroth order = `fitorder=0`, "zeroth/zero-order",
"constant fit/level/baseline", "flat continuum". Edge cases were checked by hand (for example 2018ApJ...866...87B
moved to uv, 2024ApJ...977..251H moved to image plane, 2021A&A...655A..25Z not counted as zeroth because it only
checked that order).

## When to use

- Any ALMA line cube, moment map or line flux where the source has detectable continuum (dust, free-free,
  synchrotron, a quasar core, a planet or comet body).
- Building a continuum image from the same spectral windows that carry lines (exclude line channels, then MFS or
  mtmfs image the rest) (2024ApJ...972..111L, 2018MNRAS.475..448T, 2021A&A...648A..19W).
- Line-rich sources where few channels are line-free: hot cores, complex organics, starburst nuclei, spectral
  scans. Two statistical routes are used here and they are different operations:
  - STATCONT selects the continuum channels, then the subtraction is done in the uv plane: 2018ApJ...866...87B
    (c-SCM plus an aggregate deviation spectrum, threshold adjusted by hand), followed by 2019ApJ...882..118X.
  - STATCONT estimates the continuum per pixel and subtracts it in the image plane: 2021A&A...656A..46M,
    2017A&A...604A...6S, 2017A&A...602A..59C, 2019A&A...622A.206M, 2024A&A...687A.163B; 2020A&A...636A..67A chose
    STATCONT "as there were very few line free channels".
- Line searches at high redshift where the line falls in one spw and the other spws give the continuum
  (2013ApJ...770...13W, 2019ApJ...873...50D, 2020A&A...636A..37D).

## When not to use

- **Absorption against a bright continuum.** Keep the continuum for the absorption analysis. 2018A&A...615A.141B
  fitted absorption on non-continuum-subtracted data with XCLASS and a continuum background layer
  (T_B = 132 K); 2015ApJ...814...22E subtracted in the image plane because uv-plane subtraction "can cause
  artifacts in the presence of absorption features". Optical depth needs the continuum level, so measure and keep
  it, and note the beam-filling assumption: 2019MNRAS.485..229R states that a filling factor of 1 gives only a lower
  limit on tau. Subtraction does not recover line emission hidden by optically thick line plus continuum:
  2016ApJ...820L..25Y subtracted continuum from HCO+ but not from CO, and assumed CO plus continuum optically thick.
- **Too few line-free channels to define the continuum.** 2014ApJ...790..160S did not subtract continuum from its
  CO(3-2) cube for that reason. 2020ApJ...905...85S fitted the continuum flux density as a free parameter together
  with the absorption Gaussians, using the other sideband or an SED when line-free bandwidth was short. A
  Gaussian-plus-constant fit is also used, but in the pack it follows a subtraction rather than replacing it:
  2026ApJ..1002L..28Y ran a linear uvcontsub first, then fitted Gaussian plus constant (a residual-baseline term);
  2013ApJ...770...13W subtracted a continuum image and used the fitted constant only as a consistency check against
  the continuum from three line-free spws.
- **A bright compact source dominates the field.** Remove a model of it first: 2019AJ....157..251T subtracted a
  limb-darkened Neptune model from the data before deconvolution. The pack does not show a fixed follow-up sequence
  after such a model subtraction.
- **Continuum fluxes contaminated by a strong line in broadband data.** Correct the continuum flux for the line
  contribution instead: 2015Natur.522..455C subtracted the [C II] contribution from its measured continuum fluxes.

## Steps

Keep two products apart throughout: the calibrated, unflagged visibilities (input for line work) and a
continuum-only copy (input for continuum imaging). Do not flag line channels in the data you will later image as
a line cube, and do not image continuum from continuum-subtracted data (general practice).

1. **Calibrate; self-calibrate only if it helps.** Many papers self-calibrated on line-free continuum and applied
   the tables to the line data before subtracting (2018ApJ...852..122H, 2018A&A...615A..28D, 2021A&A...648A..19W,
   2017ApJ...840...60B, 2019ApJ...871...48P, 2016ApJ...818..156C, 2017A&A...601A...5H). Others transferred the
   self-cal solutions after the subtraction (2020ApJ...898...10T, 2017ApJ...850L..30Y). Self-calibration is
   conditional: 2024ApJ...961..228S attempted it and got no improvement at S/N < 100. Adopt self-cal only if the
   continuum S/N supports it and the image improves. Software: CASA gaincal/applycal.
2. **Check flux scales and frames before combining.** 2021A&A...648A..19W compared the flux calibration of each
   execution; 2021A&A...656A..46M reports line-flux scaling anomalies in some tunings. Doppler-correct moving or
   multi-epoch data: for a comet, phaseshift, uvcontsub, then cvel2 to the comet rest frame (2025NatAs...9.1476C);
   uvcontsub3 after cvel Doppler tracking (2016ApJ...817..168H); fixvis/fixplanets for proper motion
   (2018ApJ...852..122H).
3. **Find the line-free channels.** Goal: a channel set with no emission, absorption, or atmospheric features.
   Methods in the pack:
   - inspect amplitude vs channel (plotms) and excise line peaks (2018AJ....155...47A, 2018MNRAS.475..448T,
     2020MNRAS.497.3504T), or pick by eye from cubes or spectra (2014Sci...345.1584B, 2024AJ....167...66Y,
     2021A&A...655A..72S, 2013ApJ...774L...7M);
   - exclude a velocity window around each known line (table below);
   - iterate: 2019Natur.570...83M subtracted, re-imaged, marked weak lines, and required a residual slope < 30 mJy
     across each window, with channels chosen within 1 arcsec of Sgr A*; 2019A&A...627A.114K iterated the
     pure-continuum ranges; 2017PASJ...69...18T picked them from an initial naturally weighted image;
   - statistical selection for line-rich fields (2018ApJ...866...87B, see "When to use");
   - drop atmospheric lines and bad edges: 2019MNRAS.488.5029H excluded atmospheric lines; 2019A&A...630A..59B
     excluded channels with atmospheric transmission < 0.5; 2017A&A...603A..92V kept far from the 183 GHz water
     line; 2016A&A...586A..69P excluded end channels.
4. **Make the continuum image from the unsubtracted calibrated data.** Split or select only the line-free channels
   (or flag line channels in a separate copy), average, and image with MFS or mtmfs. The effective bandwidth is
   smaller than the full band: about half (2015ApJ...801...82H), 5.61 GHz (2020ApJ...897L..33J), about 7.5 GHz
   (2018PASJ...70...36I), 52 MHz (2021A&A...655A..72S). 2021A&A...648A..19W and 2024A&A...689A..85G averaged the
   remaining channels to 125 MHz.
5. **Fit and subtract the continuum from the line data**, writing a new output and keeping the original. Most
   often reported: CASA uvcontsub, 0th or 1st order, over line-free channels of the same spw (122 papers name
   uvcontsub, my count; spread 2013-2026). Alternatives:
   - fit the continuum spws and apply the model to the line spw (2019ApJ...873...50D, 2019A&A...624L...7V,
     2020A&A...636A..37D; 2013ApJ...763..120C with a CLEAN-component model from three off-line bands);
   - image-plane imcontsub (2024ApJ...961..228S, 2019ApJ...871..170M, 2025A&A...698A.204H); 2024AJ....167...66Y used
     it to mitigate the JvM effect and 2024ApJ...977..251H because uvcontsub over-subtracted;
   - per-pixel STATCONT (2021A&A...656A..46M, 2017A&A...604A...6S), after convolving all cubes to a common beam
     (2021A&A...656A..46M);
   - GILDAS: UV-BASELINE degree zero (2021A&A...652A..98G), uv-subtract (2020ApJ...890...29F); CLASS baselines on
     extracted spectra (2019A&A...628A..27B, 2019A&A...632A..19T);
   - AIPS UVLSF (2015ApJ...808...97Y); AIPS visibility-domain average of far-off-line channels
     (2017Icar..286..289L); MIRIAD image-plane polynomials (2015ApJ...814...22E).
   After per-spw subtraction, check that overlapping windows agree: 2019Natur.570...83M additionally aligned spws
   by subtracting a line a*nu + b.
6. **Combine data sets: per data set or after combining.** Per data set: 2014A&A...572L...9R; 2024ApJ...972..147C
   (12 m and 7 m separately); 2017A&A...601A...4A and 2017A&A...607L...5Q before merging with IRAM 30m;
   2020ApJ...892L..18I per cycle, then inverse-variance weighting. Combined first: 2014A&A...570L..14R combined 12 m
   and ACA, self-calibrated, then subtracted; 2019PASJ...71..105T ran uvcontsub on combined ten-day data. Combining
   first is reasonable when flux scales, frames and spectral setups match (step 2); subtract per data set when they
   differ.
7. **Image the line cube and run the checks below.** Measure noise in line-free channels of the subtracted cube
   (2024ApJ...966...59S used 1000 random regions in line-free channels; 2024MNRAS.527.9343L cleaned to 1.5x the
   line-free rms).

### CASA notes (general practice, not from the pack)

- Older `uvcontsub` call, one order chosen explicitly:
  `uvcontsub(vis='x.ms', fitspw='0:20~110;400~480', fitorder=1, want_cont=False)`, which writes `x.ms.contsub`.
  Use `fitorder=0` for a constant. Newer CASA 6 releases replaced this task with one taking `outputvis`,
  `fitspec`, `fitorder` and `fitmethod`, keeping the old one as `uvcontsub_old`. The pack does not establish the
  release where this changed: run `help(uvcontsub)` in the installed version before writing calls.
- `imcontsub(imagename, linefile, contfile, fitorder, chans)` fits each pixel's spectrum; run it on cubes with a
  common beam and spectral frame.
- The ALMA pipeline also subtracts continuum for its delivered cubes (2018A&A...617A..54L, 2019MNRAS.489..349R).
  Treat pipeline channel ranges as a starting point and re-check them for line-rich sources.

## Parameter defaults and ranges

These are choices papers reported for their own sources, not transferable defaults. Size masks from the measured
line extent, and choose fit order from bandwidth, continuum curvature and the validation in "Verification checks".

| parameter | most often reported | range seen | papers (count) | examples |
|---|---|---|---|---|
| Domain | uv plane (visibilities) | uv, image plane, per-pixel statistical | about 223 uv, 32 image plane, 1 both (my count) | uv: 2016ApJ...829....6W, 2019MNRAS.484.4239R; image: 2024ApJ...961..228S, 2025A&A...698A.204H |
| Fit order | 1 (linear) | 0 to 2; Savitzky-Golay order 3 | 55 first order, 30 zeroth, 2 both, 1 second order (my count) | 1: 2017ApJ...842...94T, 2024ApJ...972..111L, 2026ApJ..1003...64Y; 0: 2019A&A...628A.118B, 2018ApJ...863..143C, 2025A&A...699A.256P; 2: 2025NatAs...9.1476C; S-G: 2019ApJ...870L..26C |
| Order when line-rich | 0 | 0 to 1 | 2 (my count) | zeroth for the line-rich H13CN cube, first for others (2015ApJ...814...22E); mostly zeroth with only 10 line-free channels per window (2019ApJ...871..170M) |
| Excluded half-width, protoplanetary and debris disks | +-25 km/s around each line | +-15 to +-50 km/s | 7 (my count) | +-25: 2021A&A...648A..19W, 2024ApJ...966...59S, 2024A&A...689A.104D; +-15: 2025A&A...698A.183D, 2024A&A...689A..65R (from systemic); +-20: 2024A&A...689A..85G; +-50: 2020ApJ...898..146M |
| Excluded half-width, galaxies | +-300 to +-750 km/s | see examples | 3 | +-300 about the CO(2-1) sky frequency (2020ApJ...890...29F); +-750 about the expected line frequency (2019A&A...632L...7J); full mask widths of about 300-600 km/s, not half-widths (2021A&A...652A..98G) |
| Fit channels, galaxies | \|v\| > 700 to 1500 km/s | 500 to 2500 km/s | 9 (my count) | \|v\| > 1000 from the CO(3-2) peak (2019A&A...628A.118B); > 1500 from the [C II] centroid (2019A&A...630A..59B); > 600 from systemic (2019ApJ...884L..28I); > 700 (2026A&A...705A..39P); > 750 (2024ApJ...970....9B); > 1000 (2025ApJ...990L..31B); fitting intervals -2500 to -500 and +500 to +2500 (2019MNRAS.489.1927S) |
| Exclusion relative to line width | 1.25 to 2 x FWHM, or 3 sigma_v | n/a | 3 | 2 x FWHM (2019ApJ...887..107F); 1.25 x FWHM from the peak (2020ApJ...904..130V); 3 sigma_v of a Gaussian fit (2020A&A...643A...2B) |
| Undetected line in the subtraction | assume 300 km/s width at the known redshift | n/a | 1 | 2020A&A...637A..84P (400 km/s is used for upper limits, a separate step, in 2020A&A...641A.155V) |
| STATCONT clipping | sigma clipping, alpha = 2 | alpha 2 to 3; default | 4 state a setting (my count) | alpha = 2: 2017A&A...604A...6S, 2017A&A...602A..59C; alpha = 3 with -0.5 sigma correction: 2018ApJ...866...87B; default: 2021A&A...656A..46M |
| Line-free fraction, line-rich field | 10-20% of the bandwidth | n/a | 1 | 2018ApJ...866...87B |
| Line-free channels by position, line-rich core | n/a | 144 channels (280 MHz) at line-poor to 10 (17 MHz) at line-rich positions | 1 | 2018A&A...615A.141B |
| Continuum shape assumed | flat within the fitted range | see examples | few | < 1% change across spw0/spw1 (2019A&A...628A.118B); < 1% within each spw for spectral index 2 (2024A&A...689A.317G); flat despite a 1-2% change over the sideband (2019A&A...632L...7J); power law nu^3.7 (2020A&A...641A.155V) |

## Software

From the pack aggregate "Software named in the matched steps" (labels and counts as printed; labels overlap, for
example a step can name both casa and tclean, so do not add them as unique papers):

| label | count (pack aggregate) | used for |
|---|---|---|
| casa | 367 | calibration, uvcontsub / imcontsub, imaging |
| tclean | 25 | continuum (mfs/mtmfs) and cube imaging after subtraction |
| gildas | 18 | uv-plane UV-BASELINE / uv-subtract (2021A&A...652A..98G, 2020ApJ...890...29F) |
| gildas mapping | 2 | imaging after GILDAS subtraction |
| statcont | 15 | statistical continuum, per pixel or for channel selection |
| miriad | 12 | image-plane polynomial subtraction (2015ApJ...814...22E) |
| uvcontsub | 11 | uv-plane polynomial fit (122 papers name it in parameter lines, my count) |
| aips | 6 | UVLSF (2015ApJ...808...97Y); visibility-domain averaging (2017Icar..286..289L) |
| xclass | 2 | fitting non-subtracted spectra with a continuum layer (2018A&A...615A.141B) |
| uvmultifit | 2 | fitting models to line-free channels in the uv plane (2014A&A...563A.136M) |
| mstransform | 2 | regridding around subtraction (2018ApJ...852..122H) |
| casa 5.4.1 | 2 | named version (2021A&A...648A..19W) |

"casa version" is the most common not-stated item (75, pack aggregate); "pipeline version" (7) and "casa version
and pipeline version" (13) also appear.

## Pitfalls

- **Line emission inside the continuum channels.** Leads to over-subtraction (negative bowls at line positions)
  and a biased continuum (general reasoning). In NGC 253, lines made up 5.3% to 36.6% of the total flux per
  50 GHz bin (2021A&A...656A..46M), so a line-rich "continuum" image can be badly contaminated. Channels chosen
  because they "appeared line free" (2013ApJ...774L...7M) carry this risk when the field is line-rich.
- **Absorption plus uv-plane subtraction.** Default visibility-domain subtraction left negative residuals near CS
  in 2014ApJ...792L..25V (they subtracted an average artifact from line-free channels); 2015ApJ...814...22E moved to
  the image plane for this reason; 2024ApJ...977..251H moved to imcontsub because uvcontsub over-subtracted.
- **Image-plane fitting needs consistent beams and flux scales.** 2021A&A...656A..46M convolved cubes to a common
  beam before per-pixel subtraction; 2024AJ....167...66Y chose imcontsub to mitigate the JvM effect, so check the
  residual/restored flux scaling before comparing image-plane and uv-plane results.
- **STATCONT near the noise.** Per-pixel STATCONT overestimated the continuum in noisy regions and was "not
  optimal" for lines near the noise level (2021A&A...656A..46M).
- **High fit order with one-sided channels.** A linear or higher fit extrapolated across a broad line, or from one
  side of the spectrum, is poorly constrained (general practice); prefer order 0 unless the continuum slope is
  measured on both sides.
- **Few line-free channels.** Papers used the other sideband or an SED (2020ApJ...905...85S), extrapolated the
  broad spw to narrow spws (2019A&A...624L...7V), or switched to STATCONT (2020A&A...636A..67A).
- **Uncertainties.** Formal line errors ignore continuum-subtraction systematics (2019ApJ...882..118X says its
  uncertainties "might be underestimated" for this reason). 2013ApJ...773L..34K added a 10% subtraction error in
  quadrature, but that value is specific to its data. Better: estimate the term from the spread over alternative
  masks and fit orders (as 2019Natur.570...83M did, <= 7%) or propagate the fit uncertainty, state which quantity
  it applies to (line flux, peak, ratio), remember a fitted baseline correlates errors across channels, and keep
  it separate from the flux-calibration uncertainty.
- **Missing flux is separate.** Interferometric filtering is a different error that subtraction does not fix
  (2018A&A...615A.141B, 2014A&A...570L..14R, 2020ApJ...890...29F report resolved-out emission); do not attribute
  negative bowls to subtraction without checking short-spacing coverage.
- **Reporting.** Channel ranges and fit settings are routinely missing (pack "not stated" label occurrences:
  line-free channels for continuum subtraction 33, line-free channels used for continuum subtraction 28,
  line-free channels used for uvcontsub 16, line-free channels for uvcontsub 13, line-free channels and uvcontsub
  fit order 7; labels can overlap within a card). 29 of the 81 `line_free_channels` parameter entries say the
  ranges were not given (my count). Good examples list the channels per spw (2018MNRAS.481.4931E: SPW0 25-118;
  SPW1 50-75, 90-118; SPW2 all; SPW3 9-35, 95-119; 2016MNRAS.463..252B; 2024A&A...682A..54T) or frequency ranges
  with the frame (2017MNRAS.472.1239B, barycentric; 2018ApJ...863..143C; 2024ApJ...977..251H).

## Verification checks

Checks papers ran:

- Image with and without subtraction and compare (2018A&A...609A..47P, no significant difference;
  2024ApJ...972..111L, the redshifted [C II] substructure persists without uvcontsub; 2020ApJ...889L..24P and
  2018ApJ...868..113T made both cubes).
- Vary the fit order and channel ranges (2012ApJ...757..129R; 2019A&A...628A.118B, first order did not
  significantly change results; 2021A&A...655A..25Z checked zeroth order; 2019Natur.570...83M, different line-free
  sets changed spectra by <= 7%; 2020ApJ...905...85S tried other continuum subtraction methods, result insensitive).
- Try another continuum estimate: alternate sideband (2020ApJ...905...85S, "no appreciable differences"); the
  constant from a Gaussian-plus-constant fit agreed with the 120 uJy continuum from line-free basebands
  (2013ApJ...770...13W).
- Residual flatness and alignment: residual slope < 30 mJy across each spw, with overlapping spws aligned
  (2019Natur.570...83M); line-free channels checked for residuals (2024A&A...689A.317G).
- Flux-scale consistency between executions before combining (2021A&A...648A..19W).
- Noise calibration from line-free channels: errors scaled so Var(S/sigma) = 1 in line-free channels
  (2019MNRAS.485.2092C).
- Compare total line flux against single-dish data where available (2014ApJ...797...90S, 76-97% recovered;
  2024MNRAS.527.9343L against JCMT).

What a careful referee adds:

- Ask for a reproducibility record: CASA and pipeline versions, the input data set and spw mapping, channel
  indexing convention, spectral frame and rest frequency, the exact line-free ranges per spw, fit order and
  fitting task (or STATCONT settings). Rest frequency and frame are among the items cards flag as missing
  (2021A&A...648A..19W, 2024ApJ...972..111L, 2016ApJ...829....6W).
- Look for negative bowls in moment-0 maps at line positions and for line residue in the continuum image at line
  peaks.
- For line-rich sources, compare the continuum image against one made from a strict, small channel set.
- For absorption studies, confirm the continuum level used for optical depth came from data that were not
  continuum-subtracted, and state the covering factor assumed.

## Source cards

The full list of papers is in `references/sources.md`. The most informative for this technique:

- 2019Natur.570...83M: iterative uv subtraction per spw, residual-slope criterion, a*nu + b spw alignment, <= 7% test
- 2018ApJ...866...87B: STATCONT c-SCM plus aggregate deviation spectrum to select channels for uv subtraction
- 2021A&A...656A..46M: per-pixel STATCONT after common-beam convolution; line contribution 5.3-36.6% of flux
- 2015ApJ...814...22E: image-plane subtraction to avoid uv artifacts with absorption; order by line richness
- 2018A&A...615A.141B: STATCONT channel counts by position; absorption modelled on non-subtracted data
- 2020A&A...636A..67A: STATCONT when few channels are line-free
- 2019A&A...628A.118B: zeroth-order uv fit with |v| > 1000 km/s; first order tested
- 2024ApJ...972..111L: uvcontsub fitorder 1; checked the cube without subtraction
- 2024ApJ...977..251H: imcontsub chosen because uvcontsub over-subtracted
- 2025NatAs...9.1476C: comet workflow with phaseshift, 2nd-order uvcontsub, cvel2
- 2021A&A...648A..19W: +-25 km/s flagging, 125 MHz averaging, self-cal before subtraction, execution flux check
- 2018MNRAS.481.4931E: explicit per-spw channel lists
- 2014ApJ...790..160S: skipped subtraction where too few line-free channels
- 2020ApJ...905...85S: continuum as a free fit parameter; alternate-sideband test
- 2013ApJ...770...13W: continuum from line-free spws checked against a Gaussian-plus-constant fit
- 2014ApJ...792L..25V: negative residuals from default visibility subtraction near CS
- 2012ApJ...757..129R: polynomial order and channel ranges varied
- 2021A&A...652A..98G: GILDAS UV-BASELINE degree zero with 300-600 km/s mask widths
- 2019ApJ...873...50D: continuum fit on continuum spws applied to the line spw
- 2024ApJ...961..228S: imcontsub; self-calibration attempted without improvement
- 2019AJ....157..251T: planet model subtracted before deconvolution
