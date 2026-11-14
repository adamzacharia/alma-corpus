# ALMA <SUP>12</SUP>CO (J = 1-0) imaging of the nearby galaxy M 83: Variations in the efficiency of star formation in giant molecular clouds

`2018PASJ...70...73H` | Publications of the Astronomical Society of Japan 2018 | first author: Hirota, Akihiko | arXiv: 1808.01702 | DOI: 10.1093/pasj/psy071

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, star_formation
- Question: Do GMCs in M83 form stars with a uniform star formation efficiency per free-fall time, or does SFE_ff vary across galactic environments?  
  > "To see whether GMCs form stars with uniform star formation efficiency (SFE) per free-fall time ($\mathrm{SFE}_{\mathrm{ff}}$), GMCs are identified from the data cube" (abstract)
- Target **M83**: coordinates _not stated_; z/distance 4.5 Mpc  
  > "it is one of the nearest (4.5 Mpc, (cite: Thim2003M83Distance)) spiral galaxies that is seen face-on" (Introduction); distance from Thim et al. 2003  
  > "it is one of the nearest (4.5 Mpc, (cite: Thim2003M83Distance)) spiral galaxies that is seen face-on" (Introduction)

## Data provenance

- ALMA projects: 2011.0.00772.S
- bands: _not stated_
- frequencies and spectral setup: ~1 GHz bandwidth around ~114.92 GHz, 0.244 MHz channels, Hanning applied online (0.488 MHz, ~1.27 km/s effective)  
  > "configured to cover $\sim$1 GHz bandwidth around a center frequency of $\sim$114.92 GHz with a channel spacing of 0.244 MHz." (2.1 ALMA observations)
- continuum bandwidth: _not stated_
- arrays: about 16 12-m antennas  
  > "Observations were made with about 16 antennas that have 12m diameter each." (2.1 ALMA observations)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: combined CLEAN beam 44.3 pc x 25.1 pc  
  > "(44.3 pc $\times$ 25.1 pc)" (2.3 Combined imaging)
- max recoverable scale: _not stated_
- sensitivity: ALMA-only median rms ~7.4 mJy/beam at 2.54 km/s; combined ~8.0 mJy/beam  
  > "the median value of the rms was $\sim$7.4 mJy per beam with a velocity resolution of $\sim2.54$ $\mathrm{km\ s}^{-1}$." (2.1 ALMA observations); "The median value of the rms noise within the mapped area was $\sim$8.0 mJy per beam." (2.3 Combined imaging)
- time on source: 45 pointings, ~6 s per pointing integration  
  > "45 pointings were observed sequentially with an integration time of $\sim$6 s per pointing" (2.1 ALMA observations)
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: 12CO J=1-0 (not stated)
- Other facility **Nobeyama 45-m**: OTF 12CO(1-0) zero-spacing data for flux recovery  
  > "the ALMA data were combined with zero-spacing data obtained using the NRO 45-m telescope." (2.2 45-m Telescope observations and data combination)
- Other facility **SINGG**: Halpha image for HII region catalog  
  > "retrieved from the data archive of the Survey for Ionization in Neutral-Gas Galaxies" (2.4 Ancillary data sets)
- Other facility **HST/WFC3 ERS (GO-11360)**: Pa-beta image for internal extinction  
  > "An image of $\mathrm{Pa}\beta$ was produced from the narrow- and the broad-band filter images retrieved from the data archive of the HST/WFC3 ERS program (GO-11360)." (2.4 Ancillary data sets)
- Other facility **THINGS (VLA)**: HI map  
  > "a map of the atomic hydrogen ($\mathrm{H}\emissiontype{I}$) retrieved from the archive of The HI Nearby Galaxy Survey" (3.3 Comparison with the distribution of atomic hydrogen)
- External data: HII region catalog (HIIphot on SINGG Halpha)  
  > "A catalog of $\mathrm{H}\emissiontype{II}$ regions was taken from (cite: Hirota2014)" (2.4 Ancillary data sets) [from (cite: Hirota2014)]
- External data: Foreground extinction A_Halpha=0.18 mag and [NII] fraction 0.11  
  > "Correction for foreground extinction was made by adopting $A_{\mathrm{H}\alpha}$ = 0.18 mag, which is given by (cite: Meurer2006SINGG)." (2.4 Ancillary data sets) [from (cite: Meurer2006SINGG)]
- External data: SFR calibration SFR=5.3e-42 L(Halpha)  
  > "we use the SFR calibration provided by (cite: Calzetti2007)" (5.1.2 Derivation of SFR) [from (cite: Calzetti2007)]
- Simulation/model as data: Feldmann & Gnedin toy model of GMC mass evolution with feedback, tau_ff=6.7 Myr, SFE_ff,i=0.01, t_avg=4 Myr  
  > "We adopt $\tau_{\mathrm{ff}}=6.7$ Myr and $\mathrm{SFE}_{\mathrm{ff,i}}=0.01$ as representative values for the GMCs in M83." (6.1.3 Rapid mass consumption)

## Processing

### Calibration

- pipeline or manual: standard ALMA calibration scripts bundled with data, CASA  
  > "These calibrations are made by applying calibration scripts bundled with the data set." (2.1 ALMA observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J1337-129 and Titan; 3C279 passband; J1316-336 gain  
  > "The absolute flux scale was calibrated using J1337-129 and Titan, and 3C279 was used for the passband calibration." (2.1 ALMA observations)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: natural weighting (ALMA-only sanity check)  
  > "the calibrated visibility data were Fourier-transformed with natural weighting, and the CLEAN method was applied" (2.1 ALMA observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: ALMA + 45-m pseudo-visibilities, joint FT and CLEAN in MIRIAD, relative weight tuned  
  > "The calibrated ALMA visibility data and pseudo-visibility data generated from the 45-m observations were Fourier-transformed and deconvolved with the CLEAN method together." (2.3 Combined imaging)
- smoothing: cube smoothed to circular ~46 pc beam for cloud identification  
  > "the original data cube is smoothed spatially by convolving with a Gaussian beam to obtain an axisymmetric beam profile of ($\sim46$ pc)." (4.1 Cloud identification)
- final beam: 44.3 pc x 25.1 pc  
  > "(44.3 pc $\times$ 25.1 pc)" (2.3 Combined imaging)
- final rms: ~8.0 mJy/beam median at 2.54 km/s  
  > "The median value of the rms noise within the mapped area was $\sim$8.0 mJy per beam." (2.3 Combined imaging)

### Inherited from earlier work

- Data combination procedure  
  > "combined by the procedure introduced in (cite: Kurono2009)" (2.3 Combined imaging) [from (cite: Kurono2009)]
- 45-m cube to pseudo-visibility conversion  
  > "using the same methodology as (cite: Hirota2014)" (2.3 Combined imaging) [from (cite: Hirota2014)]
- Moment extrapolation and size correction  
  > "by following the procedure proposed by (cite: Rosolowsky2006CPROPS)" (4.2 Derivation of basic cloud parameters) [from (cite: Rosolowsky2006CPROPS)]

### Not stated but needed to reproduce (our reading)

- Exact 45-m to ALMA relative weighting factor
- CASA version and any pipeline details
- CLEAN threshold, masks, cell and image size
- Line-free channels used for rms
- Exact astrodendro min_delta/min_value in absolute units and pixel size
- Bootstrap details for cloud parameter uncertainties
- Center position, inclination and PA of M83 (blank in text)

## Analysis recipe

1. **Combine ALMA and 45-m data and image**: Pseudo-visibilities from 45-m cube combined with ALMA visibilities, joint CLEAN in MIRIAD  
  > "The 45-m data cube was converted into pseudo visibility data sets using the same methodology as (cite: Hirota2014)" (2.3 Combined imaging)
   - software: CASA, MIRIAD, NOSTAR
   - fitting: _not stated_
   - validation: Combined image recovers 45-m total flux; ALMA alone recovers ~23%  
  > "Thus, only approximately 23% of the CO flux was detected with the interferometric image synthesis." (2.2 45-m Telescope observations and data combination)
2. **Identify GMCs**: astrodendro leaves on cube smoothed to 46 pc; peak SNR>3, 3 sigma above merge level, min pixels 3 x Abeam/Apixel; 3 dispersed leaves flagged, 179 remain  
  > "each *leaf* has a peak SNR over 3, and the peak SNR of each *leaf* is higher by at least 3 from the merging level to neighboring *leaves*." (4.1 Cloud identification)
   - software: astrodendro
   - fitting: _not stated_
   - validation: Tested threshold of 2 x beam area (6% more leaves, some smaller than beam)  
  > "the number of identified *leaves* increased by approximately 6%" (4.1 Cloud identification)
3. **Derive cloud properties**: Moments extrapolated to 0 K, deconvolved by resolution; R=3.4/sqrt(pi) sqrt(sx sy); M=4.4 L_CO; virial mass with n=1; tau_ff from rho with factor 1.26  
  > "Uncertainties for the size parameters and CO luminosity are determined by performing bootstrap error estimates." (4.2 Derivation of basic cloud parameters)
   - assumption: CO-to-H2 factor 2.0e20 cm-2 (K km/s)-1 with helium factor 1.36  
  > "applying the CO-to-H$_{2}$ conversion factor of 2.0 $\times$ 10$^{20}$ cm$^{-2}$ (K km s$^{-1}$)$^{-1}$" (4.2.1 Adopted definition of physical quantities)
   - fitting: _not stated_
   - validation: Extrapolation factors compared with Gaussian expectation  
  > "most of the data points for the identified GMCs agree with the expected line for a Gaussian profile." (4.2 Derivation of basic cloud parameters)
4. **Fit GMC mass spectra**: Truncated power law fit to cumulative mass function for 1e6-3e7 Msun; 100 bootstrap draws; KS test  
  > "A bootstrap method with 100 draws was used to estimate the confidence interval of the fitted parameters" (4.7 Mass spectrum of GMCs)
   - fitting: Truncated power law of Williams & McKee; median and MAD of bootstrap  
  > "The most likely value and the confidence interval for each parameter were obtained by taking the median and the median absolute deviation (MAD) of 100 bootstrap realizations for each parameter." (4.7 Mass spectrum of GMCs)
   - validation: Two-sided KS test  
  > "the two-sided Kolmogorov–Smirnov (KS) test was performed to evaluate the goodness of fit" (4.7 Mass spectrum of GMCs)
5. **Derive SFR per HII region and GMC**: Halpha corrected for foreground, [NII], and internal extinction from Pa-beta; SFR from Calzetti calibration; HII regions cross-matched if center lies within GMC ellipse; SFR split by mass among multiple GMCs; upper limit 3.5e-4 Msun/yr for unmatched  
  > "If the central position of an $\mathrm{H}\emissiontype{II}$ region is within the boundary of a GMC, then the $\mathrm{H}\emissiontype{II}$ region is judged to be associated with the GMC." (5.2 Cross-matching)
   - software: HIIphot
   - assumption: Cardelli extinction curve, intrinsic Halpha/Pabeta=17.1, median A_Halpha=1.9 mag outside Pabeta FOV  
  > "The extinction curve of (cite: Cardelli1989) and the intrinsic ratio of $I_{\mathrm{H}\alpha} / I_{\mathrm{Pa}\beta}$ = 17.1" (5.1.1 Derivation of Halpha luminosity)
   - fitting: _not stated_
   - validation: Association radius varied by +/-20%  
  > "By changing the association radius by $\pm$20% as was done in the previous subsection" (5.5 SFE_ff for individual GMCs)
6. **Compute SFE_ff and test with cloud evolution model and feedback forces**: SFE_ff = SFR tau_ff / M; compare with Feldmann & Gnedin toy model (+/-0.4 dex); compare (F_rad+F_gas)/F_grav  
  > "we employ a toy model introduced by (cite: Feldmann2011)" (6.1.1 Cloud mass evolution model)
   - assumption: GMC lifetime 15 Myr, alpha_fb=7.3 /Myr, T_HII=1e4 K, Case B  
  > "we here adopt the smallest value of 15 Myr: $\alpha_{\mathrm{fb}}$ is derived as 7.3 Myr$^{-1}$." (6.1.1 Cloud mass evolution model)
   - fitting: _not stated_
   - validation: Considered IMF sampling and stellar age effects  
  > "We consider three mechanisms here: (1) stochastic sampling of the stellar IMF, (2) uncertainty of stellar ages that affects the SFR calibration factor, and (3) mass consumption of GMCs due to stellar feedback." (6.1 Is there intrinsic environmental variation of the SFE?)

## Software

- **CASA** : ALMA calibration  
  > "processed with the standard ALMA calibration procedures using the CASA software package" (2.1 ALMA observations)
- **MIRIAD** : data reduction, combination and imaging  
  > "converted to the MIRIAD (cite: SaultTeubenWright1995MIRIAD) data format for the subsequent reduction process." (2.1 ALMA observations)
- **NOSTAR** : 45-m OTF data processing  
  > "The OTF data were processed with the NOSTAR software package" (2.2 45-m Telescope observations and data combination)
- **astrodendro** : GMC identification  
  > "We used the *astrodendro*[^1] software package to identify clouds from the data cube." (4.1 Cloud identification)
- **HIIphot** : HII region identification  
  > "using the HIIphot software (cite: Thilker2000)" (2.4 Ancillary data sets)
- **Starburst99** : Halpha per stellar mass and bolometric/Halpha ratio  
  > "we here perform a simple calculation using Starburst99" (6.1.2 Uncertainty of stellar ages)
- **APLpy** : plotting  
  > "This research made use of APLpy, an open-source plotting package for Python" (Acknowledgments)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Number of GMCs | 179 | not stated | dimensionless | 2 | After manually flagging three *leaves* with too dispersed appearance, 179 *leaves* remained. |
| Median GMC mass | 1.6e6 | not stated | Msun | 3 | the median value of the cloud mass is found to be 1.6 $\times$ 10$^6$ ${M}_{\odot}$ |
| ALMA-only CO flux fraction | ~23% | not stated | percent | 1 | only approximately 23% of the CO flux was detected with the interferometric image synthesis. |
| Median virial parameter | ~1.4 | not stated | dimensionless | 3 | has a median value of $\sim$1.4 for all samples. |
| Mass spectrum slope (all) | -1.6 | 0.1 | dimensionless | 4 | has a slope of $\sim$-1.6 $\pm$ 0.1 |
| Mass-weighted mean SFE_ff | ~9.3e-3 | not stated | dimensionless | 6 | for all GMC samples is $\sim$9.3 $\times$ 10$^{-3}$ |
| Median SFE_ff | 3.0e-3 | not stated | dimensionless | 6 | is 3.0 $\times$ 10$^{-3}$ |
| Radially averaged SFE_ff | 5.8e-3 | +1.8/-1.4 e-3 | dimensionless | 6 | 5.8$^{+1.8}_{-1.4}$ $\times$ 10$^{-3}$ |
| GMCs with (Frad+Fgas)/Fgrav>1 | 37 of 179, lifetime ~20 Myr | not stated | count | 6 | 37 out of 179 are found to have |

## Qualitative findings

- Eastern arm CO splits into primary (leading, many HII regions) and secondary (trailing, few) ridges  
  > "the one on the leading side has numerous H regions associated with it, whereas the other one on the trailing side has only a few." (abstract)

## Claim tuples

- H: Mean SFE_ff of GMCs agrees with turbulence-regulated models | E: Cross-match 179 GMCs with HII regions | R: mass-weighted mean ~9.4e-3 | F: agrees with ~0.01 | **supported**
- H: SFE_ff is universal across the mapped region | E: Compare SFE_ff by environment and with evolution toy model | R: primary arm ridge ~2.7e-2, >5x inter-arm | F: SFE_ff not universal; increases with GMC evolution | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: IMF sampling, stellar age uncertainty and rapid mass loss considered as artifacts, rejected  
  > "we conclude that the observed variation in $\mathrm{SFE}_{\mathrm{ff}}$ is not just an artifact caused by the rapid mass consumption of GMCs due to the stellar feedback." (6.1.3)
- How they decided it was enough: _not stated_
- Limitation (authors): SFR may be underestimated by about a factor of 2; central region feedback uncertain  
  > "the SFR derived here could be underestimated by approximated a factor of 2." (5.1.2)
- Caveat (inferred, ours): Halpha SFR timescale comparable to cloud lifetime
- Caveat (inferred, ours): Fixed CO-to-H2 factor across environments incl. center
- Caveat (inferred, ours): Resolution-limited cloud decomposition
- Caveat (inferred, ours): HII association by simple geometric overlap

## Reproducibility

- Data public (paper): ALMA program 2011.0.00772.S cited; 45-m data not stated public  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2011.0.00772.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: 45-m data access
- Missing: Exact combination weights
- Missing: Hirota2014 HII catalog values
- Data volume (inferred): ~tens of GB (45-pointing Band 3 mosaic plus 45-m cube)
- Score (inferred): 3/5, ALMA data are public and the recipe is mostly described, but combination weights, 45-m data and HII catalog come from other sources.
- Rediscovery candidate: no, Depends on non-public 45-m data and external catalogs and several unspecified parameters.

## Links

- Method: (cite: Kurono2009) (ALMA+single-dish combination)
- Method: (cite: Rosolowsky2006CPROPS) (moment extrapolation)
- Method: (cite: Feldmann2011) (cloud evolution toy model)
- Companion: (cite: Hirota2014) (HII catalog and 45-m data methodology)
- Related: SINGG
- Related: THINGS
- Related: HST/WFC3 ERS

## Checks

```json
{
 "quotes": 68,
 "quotes_ok": 68,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 9,
 "numeric_problems": 0,
 "fill": {
  "facts": 85,
  "stated": 53,
  "rate": 0.624
 },
 "evidence_ok": true
}
```
