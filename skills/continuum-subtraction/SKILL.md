---
name: alma-continuum-subtraction
description: "Separate spectral-line emission from continuum in ALMA data: pick line-free channels, fit and subtract the continuum in the uv plane (uvcontsub) or image plane (imcontsub, STATCONT), and build the matching continuum image from the same channels. Use when making line cubes, moment maps, line fluxes or continuum images from ALMA spectral data, when a field is line-rich (hot cores, starbursts, spectral scans), when lines sit in absorption against bright continuum, or when a referee asks how the continuum was removed. Built from 1551 ALMA papers (2012-2026)."
---

# Continuum subtraction and line-free channel selection

Continuum subtraction fits a low-order model of the continuum across channels that carry no line emission and
removes it, leaving a line-only cube; the same line-free channels give the continuum image. Two mistakes matter
most: (1) a wrong line-free channel set (line wings, blends or absorption inside the "continuum" channels) biases
both the line flux and the continuum flux, and (2) the channel set and fit settings are often not reported, so the
result cannot be reproduced. In the pack's "not stated" list, 15 labels about line-free channels occur 323 times
(sum of the labels shown; labels overlap, so this is not a unique-card count). Across the whole corpus,
`imaging.continuum_subtraction` is unstated in 64% of 3498 cards (`stats/README.md`, corpus-wide, including papers
with no line imaging).

Counts marked "my count" are regex counts over the 220 papers whose processing fields the pack prints (a sample of
the 1551); the method is in `references/parameters.md`. "(card)" marks a claim checked against a verbatim quote in
that paper's methods card because the pack lists the paper only in its bibliography.

## When to use

- Any ALMA line cube, moment map or line flux where the source has detectable continuum (dust, free-free,
  synchrotron, a quasar core, a planet or comet body).
- Building a continuum image from the same spectral windows that carry lines (exclude line channels, then MFS or
  mtmfs image the rest) (2018MNRAS.475..448T, 2020MNRAS.496..598C, 2020MNRAS.499.2493A; 2024ApJ...972..111L, card).
- Line-rich sources where few channels are line-free: hot cores, complex organics, starburst nuclei, spectral
  scans. Two statistical routes exist and they are different operations:
  - STATCONT selects the continuum channels, then subtraction is done in the uv plane: 2018ApJ...866...87B
    (threshold adjusted by hand), 2021A&A...647A..87L (corrected sigma clipping on preliminary cubes, then
    uvcontsub), followed by 2019ApJ...882..118X.
  - STATCONT estimates the continuum per pixel and subtracts it in the image plane: 2021A&A...656A..46M,
    2023A&A...677A..15M; 2017A&A...604A...6S and 2024A&A...687A.163B (card). 2020A&A...636A..67A chose STATCONT
    "as there were very few line free channels"; 2021A&A...653A.129C used it on a Band 3 spectrum too line-rich
    for line-free selection.
- High-redshift line searches where the line sits in one spw and the other spws give the continuum
  (2013ApJ...770...13W, 2013A&A...559A..29C; 2019ApJ...873...50D and 2020A&A...636A..37D, card).

## When not to use

- **Absorption against a bright continuum: keep a continuum-bearing product for the absorption analysis.**
  Subtracted products are still fine for other uses: 2025ApJ...989...83B ran uvcontsub for its main emission and
  absorption results, and separately computed tau = -ln(T_nu / T_cont) on continuum spectra, fitting each feature
  with a Gaussian plus a linear continuum. Fully unsubtracted routes: 2018A&A...615A.141B fitted absorption on
  non-subtracted data with XCLASS and a continuum background layer (T_B = 132 K); 2021MNRAS.504.2687N processed its
  line data without subtraction. 2015ApJ...814...22E subtracted in the image plane because uv-plane subtraction
  "can cause artifacts in the presence of absorption features". A beam filling factor of 1 gives only a lower
  limit on tau (2019MNRAS.485..229R).
- **Temperatures from optically thick lines.** 2020ApJ...905...89Y took the disk atmosphere temperature from the
  13CO peak brightness temperature without subtraction (subtracting first lowers the peak where the line is
  optically thick over bright dust; general reasoning). 2016ApJ...820L..25Y subtracted continuum from HCO+ but not
  from CO.
- **Too few line-free channels.** 2014ApJ...790..160S did not subtract continuum from its CO(3-2) cube for that
  reason. 2020ApJ...905...85S assumed a constant continuum and fitted the continuum flux density as a free parameter
  together with the absorption depth, offset and width, using the other sideband or an SED when line-free
  bandwidth was short (card for the joint fit). A Gaussian-plus-constant fit can also follow a subtraction rather
  than replace it: 2026ApJ..1002L..28Y ran a linear uvcontsub, then fitted the [C II] spectrum as "a Gaussian
  profile plus a constant" (card); 2013ApJ...770...13W used the fitted constant only as a consistency check.
- **Continuum fluxes contaminated by a strong line in broadband data.** Correct the continuum flux instead:
  2015Natur.522..455C subtracted the [C II] contribution from its measured continuum fluxes (card).

## Steps

Keep two products apart: the calibrated, unflagged visibilities (input for line work) and a continuum-only copy
(input for continuum imaging). Do not image continuum from continuum-subtracted data (general practice).
2025ApJ...989...30Z is a clean example: a pseudo-continuum copy flagged +-15 km/s around six lines, self-calibration
on it, the tables applied to the full data, then uvcontsub (fitorder=1) excluding the same channels.

1. **Calibrate; self-calibrate only if it helps.** Papers self-calibrated on line-free continuum and applied the
   tables to the line data before subtracting (2018ApJ...852..122H, 2018A&A...615A..28D, 2025ApJS..280...33Y,
   2026A&A...709A..93D, 2025ApJ...989...30Z; 2021A&A...648A..19W, card). Others applied the solutions after the
   subtraction (2020ApJ...898...10T, 2017ApJ...850L..30Y, card). It is conditional: 2024ApJ...961..228S could not
   improve at S/N < 100 (card) and 2021ApJ...910...53V found its source too faint. Software: CASA gaincal/applycal.
2. **Check flux scales and frames before combining.** 2021A&A...648A..19W compared the flux calibration of each
   execution (card); 2018ApJ...852..122H found self-calibrated continuum fluxes within 5% within each band and
   used fixvis/fixplanets for proper motion. For a moving target, 2025NatAs...9.1476C used `phaseshift` to move the
   fitted continuum peak to the phase centre before uvcontsub (card).
3. **Find the line-free channels.** Goal: no emission, absorption or atmospheric features. Methods in the pack:
   - inspect amplitude vs channel or visibility plots (2018ApJ...856..143I, 2018MNRAS.475..448T;
     2020MNRAS.497.3504T, card), or pick by eye from cubes or spectra (2014Sci...345.1584B, 2020MNRAS.496..598C,
     2024ApJ...977...37N; 2024AJ....167...66Y from dirty cubes, card);
   - exclude a velocity window around each known line, or a multiple of the line FWHM (`references/parameters.md`);
   - start automatic, then iterate: pipeline findcont ranges, then exclude channels with emission above 3 sigma
     (2026A&A...709A..93D); a CDMS model spectrum shifted to the field V_lsr and widened to 50 km/s, then manual
     re-identification after skewed baselines appeared (2025ApJS..280...33Y); findContinuum works on dirty cubes and
     takes the 19% most line-free channels as baseline (2023PASP..135g4501H);
   - iterate by hand: 2019Natur.570...83M re-imaged, marked weak lines and required a residual slope < 30 mJy per
     window; 2019A&A...627A.114K iterated pure-continuum ranges (card);
   - statistical selection for line-rich fields (2018ApJ...866...87B, 2021A&A...647A..87L); 2015A&A...576A.129B
     split each spw into 1000-channel sub-windows and kept the best pair of line-free channels in each;
   - drop atmospheric lines and band edges (examples in `references/parameters.md`).
4. **Make the continuum image from unsubtracted data.** Select only line-free channels (or flag line channels in a
   copy), average, image with MFS or mtmfs. The effective bandwidth shrinks: about 7.5 GHz (2018PASJ...70...36I),
   4 GHz from two spws (2023A&A...673A..46B), about 5% of the band (2020ApJ...905...25G). 2021A&A...648A..19W
   averaged the remaining channels to 125 MHz (card).
5. **Fit and subtract the continuum from the line data**, writing a new output. Most often reported: CASA
   uvcontsub, order 0 or 1, over line-free channels of the same spw (86 of the 220 printed papers name uvcontsub,
   my count). Alternatives:
   - fit other spws and apply the model to the line spw: linear extrapolation of a uv model from three SPWs
     (2013A&A...559A..29C); also 2019A&A...624L...7V, 2019ApJ...873...50D, 2020A&A...636A..37D, and a CLEAN-component
     model from three off-line bands (2013ApJ...763..120C) (all card);
   - subtract a continuum start model during deconvolution: ALMA-IMF used `.tt0`/`.tt1` products at the start of
     tclean (2023A&A...678A.194C);
   - mstransform with `fitorder=1` (2020PASJ...72...36T; per observing day in 2017ApJ...850L...5T);
   - image-plane imcontsub: zeroth order inside a 20 x 20 arcsec mask (2025A&A...701A.120P); on the smoothed
     7m+12m cube before feathering (2025A&A...702A.133K); chosen over uvcontsub for a phase-centre offset
     (2025PASJ...77..139I); to mitigate the JvM effect (2024AJ....167...66Y, card); because uv-plane subtraction
     "appeared to be over-subtracted" (2024ApJ...977..251H, card); also 2024ApJ...961..228S, 2025A&A...698A.204H (card);
   - per-pixel STATCONT (2021A&A...656A..46M, who found uv subtraction "inefficient" for 188 cubes, card); per-pixel
     2-sigma clipped channel averages (2021ApJ...907..122M); a median along frequency before a SoFiA search
     (2025A&A...702A.183H) or over the full spw (2020ApJ...905...25G);
   - GILDAS: UV-BASELINE with a degree-zero polynomial (2021A&A...652A..98G), uv-subtract (2020ApJ...890...29F);
     first-order baselines on extracted spectra with CLASS (2019A&A...628A..27B) (all card);
   - AIPS UVLSF (2015ApJ...808...97Y); visibility-domain average of far-off-line channels (2017Icar..286..289L);
     MIRIAD image-plane polynomials (2015ApJ...814...22E);
   - remove a source model before deconvolution when an adequate model exists: 2019AJ....157..251T subtracted a
     limb-darkened Neptune model. Validate the model first (see Pitfalls).
   After per-spw subtraction, check overlapping windows agree: 2019Natur.570...83M aligned spws with a*nu + b.
6. **Combine data sets: per data set or after combining.** Per data set: 2014A&A...572L...9R, 2024ApJ...972..147C
   (12 m and 7 m separately), 2017A&A...601A...4A and 2017A&A...607L...5Q before merging with IRAM 30m,
   2020ApJ...892L..18I per cycle (all card). Combined first: 2014A&A...570L..14R combined 12 m and ACA,
   self-calibrated, then subtracted (card); 2019PASJ...71..105T ran uvcontsub on combined ten-day data (card);
   2026ApJ..1005...94N (concat with visweightscale) and 2025A&A...703A..15M (concat, then statwt). Combine first when
   flux scales, frames and setups match (step 2); otherwise subtract per data set.
7. **Image the line cube and run the checks below.** Measure noise in line-free channels of the subtracted cube
   (2025ApJ...989...30Z imaged > 200 km/s so enough line-free channels exist; 2024ApJ...966...59S used 1000 random
   regions, card).

### CASA notes (general practice, not from the pack)

- Older `uvcontsub`: `uvcontsub(vis='x.ms', fitspw='0:20~110;400~480', fitorder=1, want_cont=False)`, which writes
  `x.ms.contsub`; `fitorder=0` for a constant. Newer CASA 6 releases replaced it with a task taking `outputvis`,
  `fitspec`, `fitorder` and `fitmethod`, keeping the old one as `uvcontsub_old`. Run `help(uvcontsub)` in the
  installed version before writing calls.
- Use keywords for imcontsub: `imcontsub(imagename='cube.im', linefile='cube.line', contfile='cube.cont',
  fitorder=0, chans='0~20;100~120')`; check the signature with `help(imcontsub)`. Run it on cubes with a common
  beam and spectral frame.
- The ALMA pipeline also subtracts continuum for its delivered cubes (2025A&A...702A.276P, 2024A&A...689A.145S;
  2018A&A...617A..54L, card). Treat its ranges as a first guess for line-rich sources (2026A&A...709A..93D).

## Parameter defaults and ranges

Reported choices for each paper's own sources, not transferable defaults. Size masks from the measured line extent
and pick the order from bandwidth, continuum curvature and the checks below. Full examples, total vs half-width
conventions, STATCONT settings and bandwidth examples: `references/parameters.md`.

| parameter | most often reported | range seen | papers (count) | examples |
|---|---|---|---|---|
| Domain | uv plane | uv, image plane, per-pixel statistical | 134 uv, 24 image, 9 both of 220 printed (my count) | uv: 2016ApJ...829....6W; image: 2025A&A...701A.120P; by data set: 2014ApJ...797...90S, 2023MNRAS.521.1045R |
| Fit order | 1 | 0 to 2 in uv; 3 and 6 image plane (Venus) | 46 first, 20 zeroth, 4 both, 1 second (my count) | 1: 2025ApJS..280...33Y; 0: 2023A&A...673A..46B; 3, 6: 2022MNRAS.514.2994G |
| Excluded window, disks/stars | no single value | examples only | examples | +-15 (2025ApJ...989...30Z), +-35 (2021MNRAS.506.1978L); +-20 is a self-cal mask only (2021AJ....162...99F) |
| Excluded window, galaxies | no single value | examples only | examples | \|v - v_sys\| < 500 with < 1000 and 100-2200 tested (2025ApJ...989...83B); fit \|v\| > 1500 (2019A&A...630A..59B) |
| Exclusion by line width | total 2.5 x FWHM (half-width 1.25) | 8 x FWHM as a check | 1 explicit total width | 2020ApJ...904..131N |
| STATCONT clipping | sigma clipping | alpha 2; default | examples | alpha 2: 2017A&A...604A...6S (card); default: 2021A&A...656A..46M |

## Software

From the pack aggregate "Software named in the matched steps" (labels overlap, e.g. casa and tclean in one step,
so do not add them as unique papers):

| label | count (pack aggregate) | used for |
|---|---|---|
| casa | 820 | calibration, uvcontsub / imcontsub, imaging |
| tclean | 201 | continuum (mfs/mtmfs) and cube imaging |
| uvcontsub | 128 | uv-plane polynomial fit |
| gildas | 40 | UV-BASELINE / uv-subtract, CLASS baselines |
| statcont | 32 | statistical continuum (2018A&A...609A.101S is the method paper) |
| miriad | 17 | image-plane polynomials (2015ApJ...814...22E) |
| mstransform | 13 | regridding; `fitorder` subtraction (2020PASJ...72...36T) |
| aips | 11 | UVLSF (2015ApJ...808...97Y) |
| alma pipeline | 11 | delivered cubes; findcont ranges (2026A&A...709A..93D) |
| imcontsub | 9 | image-plane fit |
| uvmultifit | 9 | continuum models fitted to visibilities |
| xclass | 4 | non-subtracted spectra with a continuum layer (2018A&A...615A.141B) |

"casa version" is the most common not-stated item (103, pack aggregate); "casa version and pipeline version" (19)
and "pipeline version" (8) also appear.

## Pitfalls

- **Line emission inside the continuum channels.** Causes over-subtraction (negative bowls at line positions) and a
  biased continuum (general reasoning). An automatic first selection left skewed baselines in some ALMA-QUARKS
  fields until channels were re-picked by hand (2025ApJS..280...33Y).
- **Statistical methods in hot cores.** STATCONT's c-SCM assumes a flat continuum and can fail with < 10% line-free
  channels (2018A&A...609A.101S). ALMA-IMF's start model was overestimated at bright hot cores with line forests,
  leaving negative residuals, and STATCONT can be imperfect towards hot cores or outflows (2023A&A...678A.194C).
  Per-pixel STATCONT left the continuum "slightly overestimated" where noise is higher and was "not optimal" for
  lines near the noise level (2021A&A...656A..46M, card).
- **Absorption plus uv-plane subtraction.** 2015ApJ...814...22E moved to the image plane for this reason;
  2020MNRAS.498.4109J rejected UVCONTSUB after visual inspection and adopted first-order IMCONTSUB on one sideband;
  2014ApJ...792L..25V subtracted a residual artifact averaged from line-free channels, which raised its CS flux by
  38% (card).
- **Image-plane fitting needs consistent beams and flux scales.** 2021A&A...656A..46M worked at a common 1.6 arcsec
  resolution (card); 2025A&A...702A.133K smoothed to a common beam before imcontsub; 2024AJ....167...66Y used
  image-plane subtraction to recover the flux scale under the JvM effect (card). Check residual/restored scaling
  before comparing image- and uv-plane results.
- **Source-model subtraction needs a good model.** A uniform disk model misses Jupiter's zone/belt structure and
  changes line-to-continuum ratios by up to 30% (2023NatAs...7.1048C). 2022MNRAS.514.2994G assumed line and
  continuum are similarly distributed under spatial filtering (about 22% of the continuum survives). Validate the
  spatial continuum model and apply matched filtering before interpreting line/continuum ratios.
- **High fit order.** Extrapolating a linear or higher fit across a broad line or from one side is poorly
  constrained (general practice); prefer order 0 unless the slope is measured on both sides. High orders remove
  broad wings: the Venus PH3 polynomial baselines suppressed pressure-broadened wings, so cloud-level abundance
  profiles could not be derived (2022MNRAS.514.2994G).
- **Few line-free channels.** Papers used the other sideband or an SED (2020ApJ...905...85S), extrapolated a broad
  spw to narrow ones (2019A&A...624L...7V, card), or switched to STATCONT (2020A&A...636A..67A).
- **Uncertainties.** Formal line errors ignore subtraction systematics (2019ApJ...882..118X says its uncertainties
  "might be underestimated"). Reported terms are paper-specific: a 10% subtraction error in quadrature
  (2013ApJ...773L..34K, card); about 11% continuum-level uncertainty (2023A&A...677A..15M; 2021A&A...653A.129C added
  it to the fit errors). Better: take the spread over alternative masks and fit orders (2019Natur.570...83M, <= 7%)
  or propagate the fit uncertainty, state which quantity it applies to, and keep it apart from flux calibration.
- **Channel covariance.** A fitted baseline correlates errors across channels, and adjacent ALMA channels are not
  independent anyway: 2021MNRAS.506.1978L applied an effective bandwidth factor of 2.667 to its integrated-flux
  limit, and 2025ApJ...989...83B built Hanning smoothing into its absorption fits. Check the spectral response of
  your own setup when fitting widths or integrating flux errors; do not reuse one paper's factor.
- **Bandpass residuals for weak absorption.** 2025ApJ...989...83B states that bandpass calibration effects on its
  optical depths are not quantified. Assess bandpass residuals and report any unquantified term separately from
  continuum-fit and flux-scale errors.
- **Missing flux is separate.** Interferometric filtering is a different error (2018A&A...615A.141B,
  2020ApJ...890...29F, card, report resolved-out emission; 2023A&A...678A.194C links negative bowls and absorption features
  to missing short spacings); check short-spacing coverage before blaming subtraction for negative bowls.
- **Reporting.** 323 not-stated label occurrences about line-free channels (pack aggregate, labels overlap); 30 of
  the 87 printed `line_free_channels` fields say the ranges were not given (my count). Good examples list channels
  per spw (2018MNRAS.481.4931E: SPW0 25-118; SPW1 50-75, 90-118; SPW2 all; SPW3 9-35, 95-119; 2024A&A...682A..54T,
  card) or frequency ranges (2018A&A...612A..29B), with the frame (2017MNRAS.472.1239B, barycentric;
  2023A&A...673A..46B, sky frequency).

## Verification checks

Checks papers ran:

- Image with and without subtraction and compare (2018ApJ...852..122H, 2024ApJ...966L..13D; 2018A&A...609A..47P
  "did not find any significant difference", 2024ApJ...972..111L substructure persists, 2020ApJ...889L..24P made
  both cubes, card).
- Vary fit order, channel ranges or exclusion width (2012ApJ...757..129R, wings persist; 2019Natur.570...83M,
  <= 7%; 2020ApJ...904..131N, 8 x FWHM did not bias the continuum; 2025ApJ...989...83B, alternative cases gave faint,
  likely spurious features near CO; 2019A&A...628A.118B, first order "did not significantly change our results",
  card).
- Try another continuum estimate: the alternate sideband gave "no appreciable differences" (2020ApJ...905...85S,
  card); a Gaussian-plus-constant fit agreed with the 120 uJy continuum from line-free basebands
  (2013ApJ...770...13W); two continuum estimates for stacked spectra (2020ApJ...904..131N); LTE modelling on
  STATCONT-subtracted spectra gave consistent N and T_ex (2026A&A...709A..93D).
- Residual flatness: slope < 30 mJy per spw with overlapping spws aligned (2019Natur.570...83M); coherence of
  continuum maps from adjacent sub-windows (2015A&A...576A.129B).
- Flux-scale consistency between executions or settings (2018ApJ...856..143I, within about 20%;
  2021A&A...648A..19W, card).
- Noise and flux errors from line-free channels: spread of integrals over equally wide line-free ranges
  (2025ApJ...989...30Z) or over 500 random Keplerian masks (2025ApJ...985...84L); cube noise against expected
  thermal noise (2026A&A...709A..93D).
- Compare total line flux with single-dish data where available (2014ApJ...797...90S, 76-97% recovered).

What a careful referee adds:

- A reproducibility record: CASA and pipeline versions, data set and spw mapping, channel indexing, spectral frame
  and rest frequency, exact line-free ranges per spw, fit order and task (or STATCONT settings). Cards often flag
  rest frequency and frame as missing (2016ApJ...829....6W).
- Negative bowls in moment-0 maps at line positions; line residue in the continuum image at line peaks.
- For line-rich sources, a continuum image from a strict, small channel set for comparison.
- For absorption, the continuum level used for tau must come from a continuum-bearing product, with the covering
  factor and a bandpass-residual assessment stated.

## Source cards

The full list of papers is in `references/sources.md`. The most informative for this technique:

- 2019Natur.570...83M: iterative uv subtraction per spw, residual-slope criterion, a*nu + b alignment, <= 7% test
- 2018A&A...609A.101S: STATCONT method paper; flat-continuum assumption, fails below about 10% line-free channels
- 2018ApJ...866...87B: STATCONT channel selection for uv subtraction, threshold adjusted by hand
- 2021A&A...656A..46M: per-pixel STATCONT at a common resolution; noisy-region overestimate
- 2023A&A...678A.194C: ALMA-IMF continuum start model in tclean; failure modes at hot cores
- 2026A&A...709A..93D: findcont start, 3 sigma iteration, first-order uvcontsub, STATCONT cross-check
- 2025ApJS..280...33Y: model-spectrum line masking, skewed-baseline check, manual re-selection
- 2020ApJ...904..131N: total exclusion 2.5 x FWHM, tested against 8 x FWHM; two continuum estimates
- 2025ApJ...989...83B: three exclusion cases; absorption opacity, Hanning smoothing, bandpass caveat
- 2015ApJ...814...22E: image-plane subtraction to avoid uv artifacts with absorption; order by line richness
- 2018A&A...615A.141B: STATCONT channel counts by position; absorption modelled on non-subtracted data
- 2025ApJ...989...30Z: separate pseudo-continuum copy, self-cal, then uvcontsub on the same mask
- 2019A&A...628A.118B: zeroth-order uv fit with |v| > 1000 km/s
- 2020MNRAS.498.4109J: uvcontsub and imcontsub compared; first-order imcontsub on one sideband adopted
- 2025PASJ...77..139I: imcontsub chosen because of a phase-centre offset
- 2022MNRAS.514.2994G: high-order image-plane baselines suppress broad wings; matched filtering assumption
- 2023NatAs...7.1048C: uniform-disk continuum model alters line-to-continuum ratios by up to 30%
- 2021MNRAS.506.1978L: first-order uvcontsub outside +-35 km/s; channel covariance factor
- 2013A&A...559A..29C: uv continuum model from other SPWs, linearly extrapolated
- 2018MNRAS.481.4931E: explicit per-spw channel lists
- 2014ApJ...790..160S: skipped subtraction where too few line-free channels
- 2013ApJ...770...13W: continuum from line-free spws checked against a Gaussian-plus-constant fit
- 2012ApJ...757..129R: polynomial order and channel ranges varied
