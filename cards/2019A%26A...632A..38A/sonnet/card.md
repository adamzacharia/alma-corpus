# A radio census of the massive stellar cluster Westerlund 1

`2019A&A...632A..38A` | Astronomy and Astrophysics 2019 | first author: Andrews, H. | arXiv: 1909.04339 | DOI: 10.1051/0004-6361/201936256

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: star_formation, stellar_physics
- Question: Measure radio fluxes, spectral indices and mass-loss rates of massive stars in Westerlund 1 with ATCA (compared with earlier ALMA 100 GHz data) and characterise the diffuse cluster emission  
  > "We aim to study the radio emission from Westerlund 1, in order to measure radio fluxes from the population of massive stars, and determine mass-loss rates and spectral indices where possible." (abstract)
- Target **Westerlund 1**: coordinates _not stated_; z/distance 5 kpc  
  > "It has a current age estimate of 5$\,$Myr and a distance estimate of 5$\,$kpc." (Introduction); "For this paper, the estimate of 5$\,$kpc is used." (Introduction); distance from adopted estimate; Gaia DR2 suggests ~3 kpc (Aghakhanloo2019) but not used  
  > "It has a current age estimate of 5$\,$Myr and a distance estimate of 5$\,$kpc." (Introduction); "For this paper, the estimate of 5$\,$kpc is used." (Introduction)

## Data provenance

- ALMA projects: 2013.1.00897.S
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Other facility **ATCA**: New 5.5 and 9 GHz continuum observations in four configurations (750C, 1.5A, 1.5B, 6A); the main dataset of the paper  
  > "The data were collected over two spectral windows, with central frequencies 5.5$\,$GHz, and 9$\,$GHz, and a bandwidth of 2$\,$GHz for each band." (2 Observations and data reduction)
- Other facility **ALMA 100 GHz (Fenech et al. 2018)**: Previously published millimetre fluxes and limits, re-tapered to match ATCA uv range for spectral indices and clumping ratios  
  > "The spectral indices of all prior known sources were calculated by comparing source fluxes at three frequencies; 5.5$\,$GHz, 9$\,$GHz and 100$\,$GHz." (3.5 Spectral indices)
- External data: ALMA flux density limits for sources not detected in mm (Table A.2)  
  > "The millimetre flux limits are taken from Table A.2 of , where the detection limit is 3$\sigma$" (Table 3 notes) [from Fenech et al. 2018 (cite: Fenech2018)]
- External data: Previous 8.6 GHz ATCA fluxes (Do10) used for comparison  
  > "in comparison to the previous 8.6$\,$GHz radio observations" (3.4 Comparison to Do10 measurements) [from Dougherty et al. 2010 (cite: Dougher2010)]

## Processing

### Calibration

- pipeline or manual: ATCA data calibrated manually in MIRIAD; extra RFI flagging with SERPent in AIPS on 9 GHz data  
  > "Data reduction and calibration was carried out with the use of MIRIAD$\,$(cite: Miriad)" (2 Observations and data reduction)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: 1934-638 (ATCA)  
  > "1934-638 was observed as a bandpass calibrator for all configurations and was also used for flux amplitude calibration." (2 Observations and data reduction)
- flux scale uncertainty: 0.1% at 5.5 GHz and 0.2% at 9 GHz for ATCA; 5% for ALMA  
  > "Calibrator errors were listed as 0.1$\,$% at 5.5$\,$GHz, and 0.2$\,$% at 9$\,$GHz." (3.2 Confirmation of ATCA detected Sources)
- self calibration: Phase and amplitude self-calibration on concatenated datasets in CASA (GAINCAL, APPLYCAL)  
  > "a run-through of both phase and amplitude self-calibration then additionally carried out on these final datasets" (2 Observations and data reduction)

### Imaging

- task: CASA tclean, multi-scale multi-frequency synthesis  
  > "the deconvolution imaging tool TCLEAN, cleaned in the mode ‘multi-scale multi-frequency synthesis’ with Briggs weighting applied (with the robust parameter set to 0)" (2 Observations and data reduction)
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 0  
  > "with Briggs weighting applied (with the robust parameter set to 0)" (2 Observations and data reduction)
- uv taper: _not stated_
- cell size: 0.3 x 0.3 arcsec  
  > "the cell size was set to 0.3$\times$0.3$\,$arcseconds" (2 Observations and data reduction)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: beam size plus 5, 10, 12, 15, 18, 25, 47 pixels  
  > "The multiple deconvolution scales applied were at the size of the beam, as well as additional scales set at 5, 10, 12, 15, 18, 25, 47 pixels" (2 Observations and data reduction)
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: PBCOR applied for analysis  
  > "PBCOR (primary beam correction) was applied to mitigate the effects of attenuation from the primary beam" (2 Observations and data reduction)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 1.71" x 0.99" (PA 0.790 deg) for FULLCONCAT  
  > "1.71" $\times$ 0.99" (position angle 0.790$^{\circ}$)" (2 Observations and data reduction)
- final rms: 0.015 mJy/beam  
  > "taken to be 0.015$\,$mJy beam$^{-1}$" (3 Analysis)

### Inherited from earlier work

- Millimetre ALMA fluxes, limits, source numbering (FCP18) and ALMA data processing  
  > "The number assigned to these sources is the FCP18 source number, as given in ." (5.2.1 ALMA sources) [from Fenech et al. 2018 (cite: Fenech2018)]
- Mass-loss stellar parameter assumptions (mu, Z, gamma, Te)  
  > "Many of these follow the assumptions made in ." (6.1.1 Mass-loss rates) [from Fenech et al. 2018 (cite: Fenech2018)]
- 5% absolute amplitude error for ALMA  
  > "a 5% error for the absolute amplitude calibration error, following the prescription in ." (3.2 Confirmation of ATCA detected Sources) [from Fenech et al. 2018]

### Not stated but needed to reproduce (our reading)

- Archival ALMA data reduction details (done in the earlier paper)
- Terminal velocities and Teff values adopted per star for the mass-loss rates
- Exact taper parameters for TAPER5/TAPER9/TAPERALMA
- SEAC grid cell number and per-source segmentation parameters
- ATCA project codes and exact data location
- Number of ALMA Band 3 data details (configuration, beam)

## Analysis recipe

1. **Calibrate and image ATCA data**: MIRIAD calibration, SERPent flagging, CASA self-cal and multiscale MFS tclean  
  > "After calibration, data were concatenated in several forms, discussed in detail below" (2 Observations and data reduction)
   - software: MIRIAD, AIPS, SERPent, CASA
   - parameter: robust 0; cell 0.3"  
  > "the cell size was set to 0.3$\times$0.3$\,$arcseconds" (2 Observations and data reduction)
   - fitting: _not stated_
   - validation: _not stated_
2. **Extract source fluxes**: SEAC floodfill source extraction with watershed segmentation (NOISE and GAUSS) for core/total components  
  > "These were set at 5$\sigma$ for the seed threshold and 3$\sigma$ for the flood threshold." (3 Analysis)
   - software: SEAC, AIPS, ParselTongue
   - parameter: seed 5 sigma, flood 3 sigma, local rms from noise map  
  > "The value of $\sigma$ is the rms value of the local spatial region." (3 Analysis)
   - fitting: _not stated_
   - validation: Visual inspection and comparison with Do10 8.6 GHz fluxes  
  > "this required a thorough visual inspection of the SEAC results, for all segmentation options, on each dataset" (3.2 Confirmation of ATCA detected Sources)
3. **Spectral indices from 5.5, 9 and 100 GHz**: Taper ATCA and ALMA data to common uv range, measure core fluxes with matched source sizes  
  > "tapering was applied to datasets of ATCA and ALMA observations, so that only equivalent u-v ranges were considered" (3.5 Spectral indices)
   - software: SEAC
   - fitting: _not stated_
   - validation: _not stated_
4. **Mass-loss rates and clumping ratios**: Wright & Barlow (1975) formula from flux; clumping ratio from ratio of Mdot*fcl^0.5 at radio vs ALMA assuming constant Mdot  
  > "The Wright and Barlow equation was applied to determine radio mass-loss rates" (6.1.1 Mass-loss rates)
   - assumption: Distance 5 kpc; Te = 0.5 Teff for hot stars, 10,000 K for cool stars; mu 1.4/2.0/4/4.7 by type; spherical smooth thermal wind  
  > "The distance, $D$, was assumed to be 5$\,$kpc, as justified in the Introduction." (6.1.1 Mass-loss rates)
   - fitting: _not stated_
   - validation: Comparison with mm and optical literature mass-loss rates  
  > "Our value for WR S, $\dot{M}f_{cl}^{\frac{1}{2}}$ 6.3$\,\pm\,$1.2$\,\times\,$10$^{-6}$ $M_{\odot}$$\,$yr$^{-1}$, is larger than determined by previous modelling of this object" (Mass-loss rates)

## Software

- **MIRIAD** : ATCA calibration  
  > "Data reduction and calibration was carried out with the use of MIRIAD$\,$(cite: Miriad)" (2 Observations and data reduction)
- **CASA** : self-calibration and tclean imaging  
  > "This involved the use of CASA$\,$(cite: Casa), where the functions GAINCAL and APPLYCAL were carried out" (2 Observations and data reduction)
- **SEAC** : source extraction and segmentation  
  > "analysis was carried out on the datasets using SEAC[^3], a source extraction software tool" (3 Analysis)
- **AIPS (JMFIT, HGEOM)** : image alignment and Gaussian size fitting  
  > "Measurements of the spatial extents were made using JMFIT in AIPS to determine a Gaussian fit for the source." (3.3 Spatial extent)
- **SERPent** : RFI flagging of 9 GHz data  
  > "additional flagging of data carried out in astronomical image processing software (AIPS) with the use of scripted e-MERLIN RFI mitigation pipeline" (2 Observations and data reduction)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Stellar radio detections in FULLCONCAT | 30 | not stated | stars | 2 | These radio observations led to 30 radio detections of known stellar sources in Westerlund 1 |
| WR B spectral index | -0.10 | 0.03 | dimensionless | 3 | / WR B / 3.51 $\pm$ 0.12 / 2.96 $\pm$ 0.09 / 2.62 $\pm$ 0.23 / -0.10 $\pm$ 0.03 / |
| W9 spectral index | 0.68 | 0.02 | dimensionless | 3 | with a value of $\alpha$ = 0.68$\,\pm\,$0.02 |
| Mean WR mass-loss rate | 4.61e-5 | not stated | Msun/yr | 4 | with a mean mass-loss rate over the total ensemble calculated to be 4.61 $\times$ 10$^{-5}$ M$_{\odot}$$\,$yr$^{-1}$ |
| Ionised mass of extended emission | 29 | not stated | Msun | 0 | gave a value of 29$\,$M$_{\odot}$, (assuming a general plasma temperature of 10kK) |

## Qualitative findings

- Most WRs have spectral indices consistent with thermal winds; the OB supergiant limits are negative, giving 3 new binary candidates  
  > "These detections have led to evidence for 3 new OB supergiant binary candidates, inferred from derived spectral index limits." (abstract)

## Claim tuples

- H: Do the massive stars in Wd1 show radio emission, and what is its nature? | E: ATCA 5.5/9 GHz imaging, SEAC extraction, radio-mm spectral indices | R: 30 stellar detections; most WRs thermal; WR B negative index | F: Many stars have thermal wind emission, with a few non-thermal binary candidates | **supported**
- H: Is wind clumping decreasing outward in WRs? | E: Compare Mdot*fcl^0.5 from tapered ATCA with ALMA | R: Ratios below 1 for most of 7 WRs; WR D 1.34 | F: Generally supports decreasing clumping with radius, with exceptions | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Diffuse emission may be misattributed to stars; errors are potentially underestimates  
  > "Errors quoted in this paper are therefore potentially underestimates of the true uncertainty on these values" (3.2 Confirmation of ATCA detected Sources)
- Caveat (inferred, ours): ALMA data are not reprocessed here; relies on Fenech 2018 values
- Caveat (inferred, ours): Core/total flux separation depends on tuned segmentation parameters
- Caveat (inferred, ours): Distance 5 kpc vs Gaia 3 kpc affects mass-loss rates (D^1.5)
- Caveat (inferred, ours): Binary inference from index limits relies on non-detections in mm

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Code: SEAC and SERPent are on GitHub  
  > "https://github.com/daniellefenech/SEAC." (footnote)
- Missing: ATCA project code and archive location
- Missing: Per-star terminal velocities and Teff
- Missing: Taper parameters
- Data volume (inferred): ATCA ~92 h of visibilities (tens of GB); ALMA small
- Score (inferred): 3/5, ATCA recipe is fairly detailed with released code, but ALMA part is inherited and several inputs are missing.
- Rediscovery candidate: no, The main data are ATCA, and ALMA plays a minor role with inherited processing.

## Links

- Method: Peck & Fenech 2013 (cite: Peck2013) (SERPent RFI flagging)
- Method: Wright & Barlow 1975 (cite: WrightBarlow1975) (Mass-loss formula)
- Companion: Fenech et al. 2018 (cite: Fenech2018) (ALMA 100 GHz observations of Wd1)
- Companion: Dougherty et al. 2010 (cite: Dougher2010) (Previous ATCA radio observations)

## Checks

```json
{
 "quotes": 50,
 "quotes_ok": 50,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 73,
  "stated": 38,
  "rate": 0.521
 },
 "evidence_ok": true
}
```
