# Continuum subtraction: parameter examples

Choices papers reported for their own sources, not transferable defaults. Every row lists explicit examples; no row
claims a corpus-wide range. "(card)" means the claim is not in the pack's printed method entries and was checked
against a verbatim quote in that paper's methods card.

## How the counts were made

My count, regex over the `processing.imaging.continuum_subtraction` and `processing.imaging.line_free_channels`
values printed in the pack's "Key parameters and settings" section. The pack prints 702 of about 2750 parameter
lines, so the counts cover only the 220 papers (of 1551) whose processing fields are printed (211 subtraction
fields, 87 line-free fields). They are a sample, not a census. A paper counts once per category and can fall in
two. Patterns (case-insensitive):

| category | pattern | papers |
|---|---|---|
| uv plane | `uvcontsub`, "uv plane/domain/space/data", "(u,v)", "visibilit", UV-BASELINE, uv-subtract, UVLSF | 134 |
| names `uvcontsub` | `uvcontsub` | 86 |
| image plane | `imcontsub`, "image plane/domain/space", STATCONT, "per pixel" | 24 |
| both uv and image | intersection of the two rows above | 9 |
| names STATCONT / `imcontsub` | literal names | 7 / 5 |
| first order | `fitorder=1`, "first/1st order", "order 1", "linear" | 46 |
| zeroth order | `fitorder=0`, "zeroth/zero order", "order 0", "constant", "flat continuum" | 20 |
| both first and zeroth | intersection | 4 |
| second order | `fitorder=2`, "second/2nd order" | 1 |
| line-free field says ranges not given | "not stated/given/specified/listed/reported" in the 87 line-free fields | 30 |

Regex counts are approximate: "Not performed in uv-plane" still matches uv (2020MNRAS.499.3909Y), and a paper that
compared both domains counts in both (2019ApJ...886...51C, 2020MNRAS.498.4109J).

## Fit order

| order | examples |
|---|---|
| 0 (constant) | 2023A&A...673A..46B, 2025PASJ...77..733T, 2025A&A...702A.133K (imcontsub); 2019A&A...628A.118B (first order tested, no significant change, card); 2020A&A...643A...2B, 2021A&A...655A..72S, 2024A&A...682A..54T, 2025A&A...698A.204H (per pixel) (card) |
| 1 (linear) | 2017ApJ...842...94T, 2025ApJS..280...33Y, 2025A&A...703A..15M, 2021MNRAS.506.1978L, 2025ApJ...989...83B, 2020ApJ...904..131N; 2019PASJ...71..105T, 2020ApJ...904..130V (card) |
| 2 | 2025PSJ.....6..286M; 2025NatAs...9.1476C (comet, card) |
| 3 and 6, image plane | 2022MNRAS.514.2994G (3rd order wideband SO2, 6th order narrowband PH3, Venus) |
| polynomial order 3 in a 51-channel window | 2019ApJ...870L..26C (card) |
| per target | first order for HCO+, HCN, CS and zeroth for the line-rich H13CN cube (2015ApJ...814...22E); first for one quasar, zeroth for the others (2024A&A...689A.220T); zero- or first-order fits (2021ApJ...909...98Y) |

## Excluded velocity windows: disks, envelopes, stars

Half-widths unless marked. Each is one paper's choice for its own line widths.

| value | example and what it applies to |
|---|---|
| +-15 km/s around each line | 2025ApJ...989...30Z (pseudo-continuum flag, same mask for uvcontsub); 2025A&A...698A.183D |
| +-20 km/s | 2021AJ....162...99F: flagged for the self-calibration continuum only; uvcontsub channels not stated. 2024A&A...689A..85G: flagged to form the pseudo-continuum (card) |
| +-25 km/s | 2021A&A...648A..19W (flagged, rest averaged to 125 MHz, card); 2024A&A...692A.155K |
| +-30 km/s | 2025A&A...703A..15M: a search interval about the stellar velocity; only channels with detected emission inside it were excluded |
| +-35 km/s | 2021MNRAS.506.1978L (uvcontsub fit outside f_CO +- 35 km/s) |
| +-50 km/s | 2020ApJ...898..146M (card) |

## Excluded or fitted velocity ranges: galaxies

| kind | example |
|---|---|
| excluded half-width | +-300 about the CO(2-1) sky frequency (2020ApJ...890...29F, card); +-400 to +-450 from [C II] (2024A&A...690A.197M); +-750 (2019A&A...632L...7J); +-800 of z_CO (2023MNRAS.518..691J); +-750 initial, then +-250 around HD(1-0) for imcontsub (2020MNRAS.498.4109J) |
| excluded, tested alternatives | \|v - v_sys\| < 500 (main), < 1000, and 100 to 2200 km/s for CO(1-0) (2025ApJ...989...83B) |
| full mask width (not half-width) | about 300 to 600 km/s per target (2021A&A...652A..98G, card) |
| fitted channels | \|v\| > 500 (2021A&A...645A..33B); > 560 (2021A&A...654L...8C); > 1000 from the CO(3-2) peak (2019A&A...628A.118B); > 1500 from the [C II] centroid (2019A&A...630A..59B); -2650 to -690 and 820 to 2280 (2023A&A...673A..46B); -2500 to -500 and +500 to +2500 (2019MNRAS.489.1927S, card) |

## Exclusion relative to line width

Total width and half-width are different conventions; only the conventions papers state are given.

| example | total width | half-width (from line centre) |
|---|---|---|
| 2020ApJ...904..131N | 2.5 x FWHM (about 900 km/s on average); 8 x FWHM tested | 1.25 x FWHM (derived) |
| 2020ApJ...904..130V | not stated | at least 1.25 x FWHM from the line peak (card) |
| 2019ApJ...887..107F | not stated | fit channels at v > \|2 x FWHM\| (card) |

## Undetected lines and upper limits

- 2020A&A...641A.155V: continuum from an S/N-weighted average of line-free channels over about 7.5 GHz with an
  assumed nu^3.7 power law; upper limits use an arbitrary Delta v = 400 km/s, a separate step (card).

## Edge and atmospheric channels

- Five channels at each end of each window (2025A&A...699A.187G); end channels of each spw (2016A&A...586A..69P, card).
- Atmospheric transmission < 0.5 excluded (2019A&A...630A..59B); channels far from the 183 GHz water line
  (2017A&A...603A..92V, card).

## STATCONT settings

| setting | examples |
|---|---|
| sigma clipping alpha = 2, per pixel | 2017A&A...604A...6S (card) |
| corrected sigma clipping for channel selection, then uvcontsub | 2018ApJ...866...87B (threshold adjusted by hand), 2021A&A...647A..87L |
| default clipping parameter, per pixel | 2021A&A...656A..46M |
| c-SMC on 32 x 1 GHz windows of a spectrum | 2021A&A...653A.129C |

## Line-free bandwidth: examples, not a range

| measured fraction or bandwidth | example |
|---|---|
| 10-20% of the bandwidth | 2018ApJ...866...87B |
| at least 20% in most spws, 10% in two | 2021A&A...647A..87L |
| about one quarter of each spw used for the fit | 2019A&A...630A..59B |
| about 5% of the total bandwidth | 2020ApJ...905...25G |
| 144 channels (280 MHz) at line-poor to 10 (17 MHz) at line-rich positions | 2018A&A...615A.141B |
| about 7.5 GHz | 2018PASJ...70...36I |
| 4 GHz from two line-free spws | 2023A&A...673A..46B |

Failure threshold (a method limit, not a measured fraction): STATCONT c-SCM can fail below about 10% line-free
channels in complex spectra (2018A&A...609A.101S, tested on 750 synthetic spectra).

## Continuum shape assumed across the fitted range

- < 1% change across spw0/spw1 (2019A&A...628A.118B); < 1% within each spw for spectral index 2
  (2024A&A...689A.317G, card); flat despite a 1-2% change over the sideband (2019A&A...632L...7J); flat within the
  band of interest (2020ApJ...904..131N); constant across a narrow band (2020ApJ...905...85S); power law nu^3.7
  (2020A&A...641A.155V, card).
