# Array combination: parameters, counts and tools

Companion to `../SKILL.md`. Source: `skills/packs/array-combination.md` (714 papers). "(card)" means the pack
lists the paper only by title or in a cut line and the value was checked verbatim in its methods card.

## How the counts were made

All counts use the pack's "Key parameters and settings" section. 413 papers have a
`processing.imaging.array_combination` line there (one each).

- **12m+7m lines (~137).** Regex over the 413 lines: a 12-m term (`12 m`, `12-m`, `12m`, `TM`, main array) and a
  7-m term (`7 m`, `7m`, `ACA`) on the same line. Includes a few lines that say an array was left out.
- **ALMA TP lines (79).** Regex `\bTP\b|total power` gives 84 lines; I removed 5 that do not combine TP
  (2023PASP..135g4501H pipeline does not support it; 2023A&A...678A.194C and 2022A&A...662A...8M did not combine
  TP; 2024ApJ...972..147C excluded TP; 2024ApJ...966..171M used TP only for velocity dispersion). Of the 79, 55
  mention feathering; 3 of those first used the single dish as a clean model (2018MNRAS.475..448T,
  2017A&A...605A..28D, 2024A&A...688A..30B). The other 24: TP2VIS 4 (2021A&A...653A..53A, 2023ApJ...949..108K,
  2026A&A...707A.252K, 2018ApJ...867..166S); pseudo-visibilities or SD2VIS 4 (2017A&A...601L...9G,
  2018A&A...618A..35G, 2025A&A...696A.100G, 2017A&A...605A.126R); TP cube as `tclean` model 1
  (2021A&A...645A..97Q); "Fourier space" 1 (2019Natur.569..519K); MIRIAD `immerge` 1 (2026ApJ..1001...33L); not
  stated 13 (2018ApJ...853..171G, 2021A&A...647A..10G, 2026A&A...709A.216U, 2024MNRAS.527.1444A,
  2020A&A...633A..13D, 2024ApJ...968L..11G, 2023A&A...671A..69G, 2020A&A...634A..56D, 2024A&A...691A.121N,
  2025PASJ...77L..55S, 2019ApJ...875...24C, 2024MNRAS.535..729P, 2023MNRAS.521.3348N).
- **Non-ALMA single dish (29; 18 feather).** Regex for IRAM, APEX, Mopra, SEST, JCMT, SCUBA, Herschel, BGPS,
  MALT90, Nobeyama/NRO, GBT, Bolocam, Planck or "30 m" on the 413 lines; then "feather" on those.
- **Weighting, deconvolver, masking, taper, multiscale, `statwt`.** Unique papers that have an
  `array_combination` line and whose other key-parameter lines mention the setting. Product (line vs continuum)
  is taken only from the text of the weighting line itself: "line" if it names km/s channels, a velocity
  resolution, CO or lines; "continuum" if it names continuum or mfs; otherwise "unspecified". Papers whose
  weighting appears only in an excerpt (for example natural + Hogbom in 2024MNRAS.527.4420M) are not counted.

## Weighting by product (my count, 56 papers)

Line cubes (20 papers):
- robust 0.5 (15): 2020ApJ...890..167T, 2021ApJ...908..231M, 2024PASJ...76..960S, 2018ApJ...863..143C,
  2017A&A...605A.116K, 2024ApJ...971..176H, 2019ApJ...885L..20H, 2018ApJ...864..120M, 2023MNRAS.522.4078C,
  2018ApJ...867..111Z, 2016ApJ...832..142Z, 2020ApJ...888...56I, 2018ApJ...860L..14K, 2021A&A...648A..41V
  (continuum and 12CO), 2022MNRAS.514..578W
- natural (4): 2018A&A...617A..23B, 2021A&A...645A..97Q, 2020ApJ...889....9M, 2020ApJ...901..151S
- robust 1 (1): 2020ApJ...894...72S
- robust 2 (1, faint lines): 2021A&A...648A..41V

Continuum (7 papers; 4 also appear under lines):
- robust 0.5 (5): 2025A&A...701A.219N, 2020ApJ...889....9M, 2020ApJ...901..151S, 2021A&A...648A..41V,
  2022MNRAS.514..578W
- natural (1): 2026A&A...706A.248T
- robust 0 (1): 2022A&A...662A...8M

Product not stated on the weighting line (33 papers):
- robust 0.5 (22): 2019ApJ...875...96N, 2021A&A...653A..53A, 2025ApJ...994..158G, 2013Natur.499..450B,
  2019ApJ...872..121U, 2019ApJ...874...89C, 2017ApJ...843...45K, 2021A&A...646A..25Z, 2025PASJ...77..616I,
  2018ApJ...853..111J, 2018ApJ...862....8T, 2019PASJ...71...85M, 2019ApJ...887..143S, 2018A&A...610A..77H,
  2023PASJ...75..646K, 2026ApJ..1004..207M, 2017PASJ...69...83M, 2021ApJ...910...11O, 2021ApJ...907L..15S,
  2026A&A...706A.328L, 2020A&A...635A...2S, 2020ApJ...894...87C
- natural (5): 2024ApJ...968..131T, 2023ApJ...953..164M, 2018MNRAS.475..448T, 2019A&A...623A..96Y,
  2018ApJ...867..166S
- robust 2 (2): 2022MNRAS.514.5035L, 2019ApJ...883..145J
- robust 1 (1): 2026ApJ..1001..184M
- robust -0.2 (1): 2023ApJ...949..108K
- different per array (2): 2020ApJ...896...36T (robust 0.5 for 12 m, natural for 7 m); 2025ApJ...990..150A
  (robust 1 for 12 m, robust 2 for the 12m+ACA mosaic)

## Full parameter table

| Parameter | Common choice | Range seen | Papers (count) | Examples |
|---|---|---|---|---|
| ACA/12-m weight multiplier | not stated by most | 0.116 (vs 1), 0.25, 0.3, 0.41, x2.4 | 1 each | 2024A&A...688A..30B, 2017A&A...605A.126R, 2014A&A...570L..14R, 2025ApJ...990..150A, 2021A&A...650A.202R |
| Resulting ACA/12-m ratio | not stated by most | 0.18; ACA:TM1:TM2 ~1:5:6 | 2 | 2020A&A...633A..13D, 2018A&A...616A..34H |
| Per-configuration multiplier | unscaled | 0.2; 0.6 and 0.2 via `visweightscale`; 1/10 | 4 | 2023MNRAS.522.4078C, 2020A&A...642A..93H, 2026ApJ..1005...94N, 2016ApJ...829L..10I |
| Per-configuration ratio | unscaled | 1:4 high-res product, 1:1 total-flux product | 1 | 2022A&A...664A..63X |
| `statwt` after merging | 11 papers (my count) | `oldstatwt` for old data | 11 | 2016ApJS..222....1F, 2017A&A...600A.141K, 2017ApJ...850...83F, 2019ApJ...871...37H, 2020A&A...641A..97V, 2021Sci...371..713L, 2022MNRAS.513.5790C, 2023A&A...679A.119R, 2023ApJ...945...69R, 2025A&A...695A.163B, 2025A&A...703A..15M |
| TP2VIS weights | TP weight from TP map rms | 7m x5, TP x20 (MIRIAD) | 2 | 2018ApJ...867..166S, 2023ApJ...949..108K |
| Feather `sdfactor` | 1.0 or "default" | rarely stated (feather parameters flagged not stated in 3 cards) | 2 explicit | 2018ApJ...867..111Z, 2024A&A...688A..30B |
| MACF model units | Jy/pixel | n/a | 1 | 2023PASP..135c4501P |
| Single-dish flux scale | rarely stated | TP x0.979 (solar); a 14% interferometric excess over the full-disk map corrected | 2 | 2020A&A...635A..71W, 2018A&A...619L...6N |
| K-to-Jy factor | rarely stated | APEX Tmb x39 to Jy/beam; Mopra 16.2 Jy/K; IRAM 6.15 Jy/K; TP 41 Jy/K (Ta*, Band 3, card); "~41.5 K/Jy" (direction unclear) | 4 | 2013ApJ...774...73I, 2017ApJ...835..265W, 2019ApJ...887...88E, 2021MNRAS.500.5500B |
| Pseudo-visibility uv range | 0 up to the next array's dish | 0-5 m, 0-7 m (after deconvolving the IRAM map), 0-12 m | 2 | 2025A&A...696A.100G, 2026A&A...707A.120H |
| Overlap-scale flux agreement | within calibration error | 10% (card), 15% Band 8 (card) | 2 | 2020ApJ...889....9M, 2018ApJ...863..143C |
| uv taper | not stated by most | 0.6" to 3" | 7 (my count) | 2020ApJ...894...87C, 2022MNRAS.514.5035L, 2016ApJ...832...37G, 2018ApJ...863..143C, 2019ApJ...874...89C, 2018ApJ...858...90G, 2018ApJ...862....8T |
| Multiscale | 0 plus 2-4 larger scales | [0,1,5,10,15] px at 0.2"; 0,2",5",10"; [0,7,21] px; point to 10" | 16 (my count) | 2018MNRAS.475..448T, 2019A&A...623A..96Y, 2025A&A...701A.219N, 2024MNRAS.530..597B |
| Hogbom | for compact or continuum | n/a | 7 (my count) | 2019ApJ...887..143S, 2021A&A...645A..97Q, 2021A&A...653A..53A, 2021ApJ...907L..15S, 2021ApJS..257...43L, 2025ApJ...994..158G, 2026A&A...706A.248T |
| Masking | auto-multithresh | "automask", algorithm not named; pbmask 10% | auto-multithresh 5 (my count) | 2019PASJ...71...85M, 2024ApJ...968..131T, 2025A&A...701A.219N, 2025ApJ...994..158G, 2026ApJ..1004..207M; 2021ApJ...907L..15S; 2023A&A...678A.194C |
| Clean depth | single-paper recipes | multiscale to ~4 sigma then single-scale to ~1 sigma; 2x rms; ~2.5x rms; 5 sigma; ~1 sigma | 1 each | 2025ApJ...988..162D, 2025ApJ...990..150A, 2018ApJ...853..111J, 2023A&A...678A.194C, 2023ApJ...953..164M |

The multiscale count includes 2016ApJ...829L..10I, 2018ApJ...861...14C, 2019ApJ...874...89C,
2020ApJ...888...56I, 2021A&A...653A..53A, 2021ApJS..257...43L, 2023A&A...678A.194C, 2024ApJ...968..131T,
2025A&A...702A.133K, 2025ApJ...988..162D, 2026A&A...706A.248T and 2026ApJ..1004..207M besides the examples.

## Alignment tools (Step 3)

- Positional offsets between short- and long-baseline data fixed (2020ApJ...889L..24P; 20 and 40 mas offsets in
  2019AJ....158...15P); proper motion corrected (2019A&A...625A.118K; 2016ApJ...820L..40A).
- `fixvis` (2018ApJ...868L...5K); `fixvis` + `fixplanets` to Gaia positions (2021MNRAS.506.1978L); `phaseshift`
  (2024A&A...687A.311A); VisAlign (2022MNRAS.513.5790C; 2025A&A...702A..18D); `fixplanets` + `cvel` for a moving
  target (2016ApJ...821L...8S); old frame relabelled to ICRS (2023ApJ...954..197I).
- Common LSRK frame before combining (2016A&A...587A..44P; 2021A&A...645A..49G); `mstransform` regrid to
  0.25 km/s (2018ApJ...852..122H). In `concat`, default `freqtol`/`dirtol` keep fields and spws separate
  (2025A&A...699A..80H); papers set freqtol 10 MHz (2020A&A...641A..97V) or 30 MHz (2026A&A...712A.227E).

## More software (pack aggregate mentions)

| Software | Mentions | Used for | Examples |
|---|---|---|---|
| `imcontsub`; `mstransform` | 3; 2 | image-plane continuum subtraction; regridding | 2018ApJ...852..122H |
| `simobserve`; DC_script | 3; 2 | simulated combinations; method comparison | 2023PASP..135c4501P |
| SoAP | 2 | solar imaging with TP feathering | 2020A&A...635A..71W |
| uvcombine | 2 | feathering: Herschel with SCUBA (no ALMA in that step); BGPS with ALMA | 2018ApJ...853..171G, 2024ApJ...962...48J |
| sdintimaging; J-comb; FSSC | below the aggregate cut-off | joint deconvolution; uv-domain combination; feather-like | 2023PASP..135c4501P, 2026A&A...708A.251X |
| uvmultifit; galario; dynesty | 3; 3; 3 | fitting visibilities (separate from imaging) | 2018A&A...617A..23B, 2019A&A...628A.100D |
