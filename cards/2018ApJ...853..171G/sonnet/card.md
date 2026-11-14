# Distributed Star Formation throughout the Galactic Center Cloud Sgr B2

`2018ApJ...853..171G` | The Astrophysical Journal 2018 | first author: Ginsburg, Adam | arXiv: 1801.04941 | DOI: 10.3847/1538-4357/aaa6d4

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, milky_way_ism
- Question: Is there extended, distributed star formation across the Sgr B2 cloud beyond the N, M, S protoclusters, and how do star formation thresholds and surface density relations compare with local clouds?  
  > "Their spatial distribution spread over a $\sim12\times3$ pc region demonstrates that Sgr B2 is experiencing an extended star formation event" (abstract)
- Target **Sgr B2 cloud (N, M, S, DS)**: coordinates _not stated_; z/distance 8.4 kpc  
  > "We adopt a distance to Sgr B2 $D_{\mathrm{Sgr B2}}=\ensuremath{8.4\textrm{~kpc}}$" (1 Introduction); distance from adopted, close to IAU Galactic Center distance of 8.5 kpc, accounting for ~100 pc offset from Reid2009a  
  > "We adopt a distance to Sgr B2 $D_{\mathrm{Sgr B2}}=\ensuremath{8.4\textrm{~kpc}}$" (1 Introduction)

## Data provenance

- ALMA projects: 2013.1.00269.S
- bands: Band 3 (3 mm)  
  > "Observations were taken in ALMA Band 3 with the 12m Total Power array, the ALMA ACA 7m array, and in two configurations with the ALMA 12m array" (2.1 ALMA data)
- frequencies and spectral setup: 4 spectral windows, 30720 channels, single polarization, 244 kHz (~0.8 km/s) channels; centers 89.48, 91.28, 101.37, 103.23 GHz, 1.875 GHz each (7.5 GHz total)  
  > "The basebands were centered at 89.48, 91.28, 101.37, and 103.23 GHz with bandwidth 1.875 GHz (total 7.5 GHz)." (2.1 ALMA data)
- continuum bandwidth: _not stated_
- arrays: 12m (two configurations), ACA 7m, Total Power  
  > "in two configurations with the ALMA 12m array" (2.1 ALMA data)
- configurations: _not stated_
- baselines: 12m: 15-349 m, 15-328 m, 43-1574 m; 7m: 9-49 m  
  > "| 01-Jul-2015 | 12m   | 3517                 | 43-1574               | 43             |" (Table 1 (observations))
- angular resolution: 0.54"x0.46" (robust 0.5); 0.37"x0.32" (robust -1); 2.35"x1.99" (tapered)  
  > "imaged with Briggs robust parameter 0.5, achieving a beam size $0.54\arcsec\times0.46\arcsec$" (2.1 ALMA data)
- max recoverable scale: _not stated_
- sensitivity: average RMS 0.09 mJy/beam (0.05 K) in signal-free region; 0.3 mJy/beam near Sgr B2 M; cubes ~9 mJy/beam per 0.8 km/s channel  
  > "average RMS noise $0.09$ mJy/beam, 0.05 K" (2.1 ALMA data)
- time on source: _not stated_
- observing dates: Jul 2014 - Jul 2015  
  > "| 06-Dec-2014 | 12m   | 6849                 | 15-349                | 34             |" (Table 1 (observations))
- pi or archival as stated: _not stated_
- Line: HC3N J=10-9 (not stated)
- Other facility **Herschel Hi-GAL**: 70-350 um data for SED-fit column density maps  
  > "We use Herschel Hi-Gal data (cite: Molinari2010a) to perform SED fits to each pixel (cite: Battersby2011a)." (2.2 Other data)
- Other facility **CSO SHARC / JCMT SCUBA**: 350 and 450 um images combined with Herschel for higher-resolution column maps  
  > "we combine the Herschel data with SHARC 350 $\mu \textrm{m}$ and SCUBA 450 $\mu \textrm{m}$ images." (2.2 Other data)
- Other facility **VLA**: cm-wavelength HII region catalogs and 20 cm/1.3 cm images for cross-matching  
  > "if there is a corresponding 0.7 or 1.3 cm source from one of the previous VLA surveys" (3.2 H II regions)
- External data: Column density maps from Herschel SED fits (fit uncertainty 25%)  
  > "The estimated fit uncertainty in the column density is $25\%$, with an upper limit on the systematic uncertainty of a factor of two (Battersby et al, in prep)." (2.2 Other data) [from Battersby et al, in prep; (cite: Battersby2011a)]
- External data: Methanol maser catalog (MMB)  
  > "The (cite: Caswell2010a) Methanol Multibeam (MMB) Survey identified 11 sources in our observed field of view" (3.2 6.67 GHz CH3OH masers) [from (cite: Caswell2010a)]
- External data: Water maser catalog  
  > "We matched our catalog with the (cite: McGrath2004a) water maser catalog, finding that 23 of our sources have a water maser within 1." (3.2 H2O masers) [from (cite: McGrath2004a)]
- External data: Chandra X-ray point source catalog  
  > "3 of the sources have X-ray counterparts in the (cite: Muno2009a) Chandra point source catalog within 1." (3.2 X-ray sources) [from (cite: Muno2009a)]
- External data: Gutermuth et al. star-gas surface density relations (eq. 5, 7)  
  > "We use their equation 7:" (4.4.1) [from (cite: Gutermuth2011a)]
- External data: Sgr B2 age t=0.74 Myr from last pericenter passage  
  > "We use the dynamical model of (cite: Kruijssen2015a) to get an age of the Sgr B2 cloud $t=0.74$ Myr, the time since pericenter passage." (4.1) [from (cite: Kruijssen2015a)]
- Simulation/model as data: Robitaille2017a and Zhang2015f protostellar models used to constrain luminosity needed for S3mm>0.5 mJy  
  > "The Robitaille models that produce $S_{3 \mathrm{mm}} > 0.5$ mJy within an $r<2500\mathrm{~AU}$ aperture uniformly have ${L>10^4~\ensuremath{L_{\odot}}}$." (3.3.5)

## Processing

### Calibration

- pipeline or manual: ALMA QA2 calibrated measurement sets used  
  > "The ALMA QA2 calibrated measurement sets were combined to make a single high-resolution, high-dynamic range data set." (2.1 ALMA data)
- casa version: CASA 4.7.2-REL r39762  
  > "using CASA (version 4.7.2-REL r39762) `tclean`" (2.1 ALMA data)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: 3 iterations phase-only, then 2 iterations amplitude+phase (continuum only; none for cubes)  
  > "We therefore ran 3 iterations of phase-only self-calibration and two iterations of amplitude + phase self-calibration" (2.1 ALMA data)

### Imaging

- task: CASA tclean, 7m+12m jointly, all four basebands  
  > "We imaged the continuum jointly across all four basebands (without excluding any spectral line regions) using CASA (version 4.7.2-REL r39762) `tclean`" (2.1 ALMA data)
- deconvolver: multi-scale multi-frequency synthesis, 2 Taylor terms (mtmfs, nterms=2)  
  > "parameters `deconvolver=‘mtmfs’` and `nterms=2`" (3.1)
- weighting robust: Briggs robust 0.5 (main); -1; taper with robust 2  
  > "The final image used for most of the analysis in this paper was imaged with Briggs robust parameter 0.5" (2.1 ALMA data)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: clean to 0.1 mJy/beam over pixels with S>2.5 mJy/beam from previous tclean iteration  
  > "we cleaned to a threshold of 0.1 mJy/beam over all pixels with $S_\nu > 2.5$ mJy / beam as determined from a previous iteration of `tclean`." (2.1 ALMA data)
- multiscale scales: _not stated_
- continuum subtraction: median-subtracted cubes (median along each spectrum treated as continuum)  
  > "We use median-subtracted cubes (i.e., spectral cubes with the median along each spectrum treated as continuum and subtracted) for our analysis of the lines" (2.1 ALMA data)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: 7m+12m (and TP) combined into single dataset  
  > "The ALMA QA2 calibrated measurement sets were combined to make a single high-resolution, high-dynamic range data set." (2.1 ALMA data)
- smoothing: _not stated_
- final beam: 0.54"x0.46"  
  > "achieving a beam size $0.54\arcsec\times0.46\arcsec$" (2.1 ALMA data)
- final rms: 0.09 mJy/beam average (0.3 mJy/beam within one primary beam of Sgr B2 M)  
  > "average RMS noise $0.09$ mJy/beam, 0.05 K" (2.1 ALMA data)

### Inherited from earlier work

- Median-estimated continuum error <5% except at Sgr B2 N  
  > "the only location in which an error $>5\%$ on the median-estimated continuum is expected is the Sgr B2 North core" (2.1 ALMA data) [from (cite: Sanchez-Monge2017b; Sanchez-Monge2017a)]
- Gas/stellar surface density methodology (11th nearest neighbor, gridded)  
  > "We adopt the same approach used in (cite: Gutermuth2009a) and (cite: Gutermuth2011a) to compare gas and stellar mass surface densities." (4.4.1) [from (cite: Gutermuth2009a; Gutermuth2011a)]
- Feathering technique for single-dish combination  
  > "we used a ‘feathering’ technique (cite: Stanimirovic2002a; Cotton2017a) to combine the images in the Fourier domain." (2.2 Other data) [from (cite: Stanimirovic2002a; Cotton2017a)]

### Not stated but needed to reproduce (our reading)

- tclean image size, cell size, multiscale scales and primary-beam mask details
- self-calibration solution intervals and per-iteration imaging parameters (only in script)
- exact by-eye source selection and per-source peak/photometry procedure
- Herschel SED-fitting details (Battersby et al. in prep) and dust opacity for column density maps
- uvcombine/feather weighting parameters
- cluster radius definitions for source association

## Analysis recipe

1. **Image continuum with self-calibration**: Joint 7m+12m tclean imaging of all basebands, self-cal, mtmfs  
  > "We therefore ran 3 iterations of phase-only self-calibration and two iterations of amplitude + phase self-calibration" (2.1 ALMA data)
   - software: CASA
   - parameter: robust 0.5, -1, and tapered robust 2 images  
  > "Using the same visibility data, we also produce an image with robust parameter -1" (2.1 ALMA data)
   - fitting: _not stated_
   - validation: calibrator J1752-2956 spectral index -0.62±0.14 consistent with synchrotron  
  > "we imaged one of our calibrators, J1752-2956, and obtained a spectral index $\alpha=-0.62\pm0.14$" (3.1)
2. **Identify compact continuum sources and measure photometry/spectral index**: By-eye selection of peaks >5x lowest RMS across images, excluding r>1" sources; local noise via MAD in 0.5-1.5" annulus; alpha from mtmfs maps  
  > "Outside of the dense clusters, every peak that is higher than five times the lowest measured RMS noise value was visually inspected." (3.1)
   - software: CASA
   - parameter: alpha kept if |alpha|>5 sigma(alpha) or sigma(alpha)<0.1  
  > "We include in the analysis only those sources with $|\alpha| > 5
\sigma(\alpha)$ or $\sigma(\alpha) < 0.1$" (3.1)
   - fitting: _not stated_
   - validation: high/low-confidence classes; completeness not quantified  
  > "we cannot readily quantify our completeness" (3.1)
3. **Cross-match and classify sources**: Positional matching within 0.5-1" to VLA HII, MMB, H2O maser, Chandra, Spitzer catalogs; test alternative nature hypotheses (prestellar cores, EGGs, HII regions, YSOs)  
  > "We cross-matched our source catalog with catalogs of NH$_3$ sources, H II regions, X-ray sources, Spitzer sources, and methanol and water masers." (3.2)
   - assumption: beta=1.75, kappa(3.1mm)=0.0018 cm2/g per gram gas (Ossenkopf1994a), gas-to-dust 100, d=8.4 kpc  
  > "assuming a dust opacity index $\beta=1.75$ (spectral index $\alpha=3.75$ if measured on the Rayleigh-Jeans tail of the spectral energy distribution)" (3.3.1)
   - fitting: _not stated_
   - validation: comparison with Robitaille/Zhang models, HOPS Orion sources, and MUSTANG Orion data  
  > "We compare our detected sample to that of the Herschel Orion Protostar Survey (cite: Furlan2016a)" (3.3.5)
4. **Infer stellar mass and SFR**: Assign 12 Msun to cores and 45 Msun to HII regions (Kroupa IMF), extrapolate with mass fractions 0.09 and 0.14, divide by age 0.74 Myr  
  > "we assume each source not associated with an H II region contains or will form a star with mass equal to the average over the range 8-20 $M_{\odot}$ assuming a (cite: Kroupa2001a) initial mass function" (4.1)
   - assumption: age t=0.74 Myr from Kruijssen2015a  
  > "We divide the inferred stellar mass by this age" (4.1)
   - fitting: _not stated_
   - validation: compared with Schmiedeke2016a mass estimates  
  > "We compare our mass estimates to those of (cite: Schmiedeke2016a)" (4.1)
5. **Column density maps and thresholds**: Herschel SED fits at 25", combined with SHARC/SCUBA via feathering; column densities at source positions; compare with Lada+2010 and Krumholz+2008 thresholds  
  > "we created several column density maps using different assumptions about the dust temperature." (2.2 Other data)
   - software: uvcombine
   - parameter: constant T=20 and 50 K maps plus SED-temperature maps; SCUBA scaled by 3x  
  > "We had to scale the SCUBA data up by a factor $\approx3$" (2.2 Other data)
   - assumption: foreground column 5e21-5e22 cm-2  
  > "This material may have column densities as low as 5$\times 10^{21}$ $\textrm{cm}^{-2}$ or as high as 5$\times 10^{22}$ $\textrm{cm}^{-2}$" (2.2 Other data)
   - fitting: _not stated_
   - validation: feathering experiments with SCUBA scaling 0.5x-10x  
  > "we show the images and resulting histograms when we combine the Herschel data with the SCUBA data scaled by a range of factors from $0.5\times$ to $10\times$" (Appendix Single Dish Combination)
6. **Star-gas surface density relation**: 11th-nearest-neighbor and gridded stellar surface density vs gas surface density; compare with Gutermuth+2011 alpha=1 and 2 relations  
  > "We computed both the star-centric mass surface density using the 11th nearest neighbor density and a gridded surface density." (4.4.1)
   - parameter: 21.8 Msun per source, each = 23% of stellar mass (95 Msun per source); c=0.3  
  > "each 3 mm source is treated as a “cluster” containing 95 $M_{\odot}$ of stellar mass" (4.4.1)
   - fitting: curves compared by eye (k=0.1 Myr^-1 for alpha=1; k=1e-4 for alpha=2)  
  > "with $k=10^{-4}$ pc$^{2}$ $M_{\odot}$$^{-1}$ Myr$^{-1}$ and $\alpha=2$, at times $t=0.01$, 0.1, and 0.74 Myr" (4.4.2)
   - validation: critical evaluation of nine possible explanations for discrepancy  
  > "We evaluate several possibilities here:" (4.4.3)

## Software

- **CASA** 4.7.2-REL r39762: tclean imaging, self-calibration, spectral index maps  
  > "using CASA (version 4.7.2-REL r39762) `tclean`" (2.1 ALMA data)
- **spectral-cube** : cube analysis  
  > "The tools used include `spectral-cube`, `radio-beam`, and `uvcombine`" (Software)
- **radio-beam** : beam handling  
  > "The tools used include `spectral-cube`, `radio-beam`, and `uvcombine`" (Software)
- **uvcombine** : combining single-dish and Herschel data  
  > "The tools used include `spectral-cube`, `radio-beam`, and `uvcombine`" (Software)
- **astropy** : general analysis  
  > "`astropy` (cite: Astropy-Collaboration2013a), `astroquery`" (Software)
- **astroquery** : catalog queries (e.g., SIMBAD)  
  > "`astropy` (cite: Astropy-Collaboration2013a), `astroquery`" (Software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Number of compact 3 mm sources | 271 | not stated | sources | 2 | We detected 271 compact continuum sources |
| Sources with HII region counterparts | 31 | not stated | sources | 3 | 31 of our sources are classified as H II regions |
| Sources with significant spectral index | 62 (33 with alpha>2) | not stated | sources | 2 | We measured spectral indices for 62 sources, of which 33 have $\alpha>2$. |
| Calibrator J1752-2956 spectral index | -0.62 | 0.14 | dimensionless | 1 | obtained a spectral index $\alpha=-0.62\pm0.14$ |
| Total inferred stellar mass | 26000 (max 46000) | not stated | Msun | 4 | / Total / 240 / 57 / 5500 / 26000 / 19000 / 33000 / 1993 / 33400 / 0.035 / |
| Total SFR (max) | 0.062 | not stated | Msun/yr | 4 | Our estimated total inferred SFR of the Sgr B2 cloud is 0.062$M_{\odot}$$\textrm{yr}^{-1}$ |
| Dynamic range in combined image | 18000 | not stated | dimensionless | 1 | is 18000 (average RMS noise $0.09$ mJy/beam, 0.05 K) |

## Qualitative findings

- Most sources are YSOs with massive envelopes (M*>~8 Msun) rather than prestellar cores, externally ionized globules, or HII regions  
  > "Most of the newly-detected sources are YSOs with gas envelopes which, based on their luminosities, must contain objects with stellar masses $M_*\gtrsim8$ $M_{\odot}$." (abstract)
- Column density threshold N(H2)>~1e23 is necessary but not sufficient for high-mass star formation  
  > "indicating that this threshold is a necessary but not sufficient criterion for high-mass star formation" (Conclusions)

## Claim tuples

- H: Is star formation in Sgr B2 extended beyond the N, M, S protoclusters? | E: 3 mm ALMA mosaic, source catalog and classification | R: 271 compact sources over ~12x3 pc, >half of new generation not in clusters | F: Sgr B2 is undergoing an extended star formation burst | **supported**
- H: Does Sgr B2 follow the local-cloud column density threshold for star formation? | E: Compare source background column densities and YSO counts with Lada+2010 | R: All sources above ~1e23 cm-2 but much gas without YSOs; YSO count 3-6x below extrapolation | F: Higher threshold required in Sgr B2 | **supported**
- H: Do local-cloud Sigma*-Sigma_gas relations extrapolate to Sgr B2? | E: Compare with Gutermuth+2011 relations | R: alpha=2 relation inconsistent; linear alpha=1 consistent; local extrapolation exceeds data by >=50x | F: A volume-density threshold, higher in CMZ, may be needed | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Automated source finding not viable due to extended HII regions, sidelobe artifacts, and resolved-out emission, so sources selected by eye  
  > "An automated selection is not viable across the majority of the observed field for several reasons:" (3.1)
- Alternative: Prestellar cores, externally ionized globules, interloper OB HII regions, and recently formed OB HII regions rejected as explaining whole sample  
  > "After determining that the other possibilities cannot explain the whole sample, we test and validate the hypothesis that most or all of the sources contain YSOs" (3.3.5)
- How they decided it was enough: _not stated_
- Limitation (authors): Catalog potentially incomplete; completeness cannot be quantified  
  > "Our selection criteria result in a reliable but potentially incomplete catalog" (3.1)
- Limitation (authors): Column density maps not very accurate; SFR strongly dependent on assumed timescale  
  > "our estimate of the star formation rate remains strongly dependent on the assumed star formation timescale" (4.1.1)
- Caveat (inferred, ours): Subjective by-eye source selection limits reproducibility and completeness
- Caveat (inferred, ours): YSO classification relies on indirect arguments and unconstrained high-mass dust models
- Caveat (inferred, ours): Mass/SFR depend on assumed IMF and age; mixed-resolution column maps with a 3x SCUBA rescaling

## Reproducibility

- Data public (paper): Images and cubes distributed with the paper; scripts and catalog on GitHub  
  > "All three images are distributed with the paper (<https://doi.org/10.11570/17.0007>)." (2.1 ALMA data)
- Products in archive: _not stated_
- Code: GitHub repository SgrB2_ALMA_3mm_Mosaic, hash e26ce0f  
  > "The software used to make this version of the paper is available from github at <https://github.com/keflavich/SgrB2_ALMA_3mm_Mosaic/> with hash e26ce0f (2017-12-28)." (Software)
- Missing: Battersby et al. column density maps (in prep)
- Missing: self-calibration script parameters (in external repo)
- Missing: by-eye selection decisions
- Data volume (inferred): ~1 TB (four ~225 GB cubes; raw 7m/12m/TP data larger)
- Score (inferred): 6/5, Code, images and catalog are released and ALMA data are in the archive, but selection is by eye and column maps depend on unpublished work.
- Rediscovery candidate: no, Source selection is subjective and column density products are unpublished, though numbers are largely derivable.

## Links

- Method: (cite: Rau2011a) (multi-scale multi-frequency synthesis)
- Method: (cite: Gutermuth2011a) (star-gas surface density methodology)
- Companion: (cite: Schmiedeke2016a) (Sgr B2 clusters and HII region mass estimates)
- Related: Hi-GAL
- Related: Methanol Multibeam Survey
- Related: Herschel Orion Protostar Survey

## Checks

```json
{
 "quotes": 81,
 "quotes_ok": 81,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 93,
  "stated": 68,
  "rate": 0.731
 },
 "evidence_ok": true
}
```
