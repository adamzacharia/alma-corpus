# A Radio-to-mm Census of Star-forming Galaxies in Protocluster 4C23.56 at Z = 2.5: Gas Mass and Its Fraction Revealed with ALMA

`2017ApJ...842...55L` | The Astrophysical Journal 2017 | first author: Lee, Minju M. | arXiv: 1705.10330 | DOI: 10.3847/1538-4357/aa74c2

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies, galaxy_clusters_and_sz
- Question: What are the molecular gas masses and gas fractions of main-sequence Halpha-emitting galaxies in protocluster 4C23.56 at z=2.49, and how do they compare with field galaxies?  
  > "The gas mass ($M_{\rm gas}$) and gas fraction ($f_{\rm gas}$) are comparable to those of field galaxies" (abstract)
- Target **Protocluster 4C23.56 (HAEs)**: coordinates _not stated_; z/distance z = 2.49  
  > "Radio galaxy (HAE1) at z = 2.483 $\pm$ 0.003 is associated to this protocluster" (2.2 Protocluster 4C23.56); distance from narrow-band Halpha selection; CO redshifts  
  > "Radio galaxy (HAE1) at z = 2.483 $\pm$ 0.003 is associated to this protocluster" (2.2 Protocluster 4C23.56)

## Data provenance

- ALMA projects: 2012.1.00242.S
- bands: Band 3 (CO 3-2) and Band 6 (1.1 mm)  
  > "The Band 3 CO (3–2) observations have been performed to cover 22 HAEs, and the Band 6 1.1 mm observations have been performed to cover 19 HAEs" (2.1 Halpha emitters)
- frequencies and spectral setup: Band 6: four 1.875 GHz TDM windows at 256.0, 258.0, 272.0, 273.8 GHz; Band 3: FDM window at 99.3 GHz, TDM at 101.1, 111.3, 113.2 GHz  
  > "The central frequencies of the four spectral windows are 256.0, 258.0, 272.0, and 273.8 GHz." (3.1); "One of the spectral windows, centered at 99.3 GHz, is taken in frequency division mode (FDM)" (3.1)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: Band 6: 17-462 m; Band 3: 43-1574 m  
  > "The baseline lengths were between 17 and 462 m." (3.1); "The minimum baseline was 43 m, and the maximum baseline was 1574 m for Band 3." (3.1)
- angular resolution: Band 3 0.91x0.66 arcsec; Band 6 0.78x0.68 arcsec  
  > "The synthesized beam sizes are 0$^{\prime\prime}$.91$\times$0$^{\prime\prime}$.66 (PA = $23.5^{\circ})$ for Band 3" (3.1)
- max recoverable scale: _not stated_
- sensitivity: Band 6 ~0.08 mJy/beam; Band 3 ~0.17 mJy at 100 km/s  
  > "The noise level (1$\sigma$) reached $\sim0.08~$mJy beam$^{-1}$ per field" (3.1); "The typical noise (1$\sigma$) level reached $\sim 0.17$ mJy when the spectral resolution is re-binned to 100 km s$^{-1}$." (3.1)
- time on source: Band 6 ~30 min (8 pointings); Band 3 4 hours (4 pointings)  
  > "The Band 3 CO(3-2) observations were executed for a total of 4 hours of on-source time with 4-pointing" (3.1)
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: CO 3-2 (345.79599 GHz)
- Other facility **Subaru/MOIRCS**: NB2288 Halpha emitter sample, J and Ks photometry for stellar masses and SFRs  
  > "The stellar masses ($M_{\star}$) and SFRs of the HAEs are derived from the broad-band emissions in $J$ and $Ks$ bands" (4.1)
- Other facility **Spitzer MIPS 24 um**: archival 24 um images for visual comparison  
  > "We present the MIPS image only to show the visual characteristics" (4.2)
- Other facility **ASTE AzTEC**: 1.1 mm SMG detections  
  > "SMGs observed at 1.1 mm with the Atacama Submillimeter Experiment" (2.2)
- External data: PHIBBS-I comparison sample (Mstar, SFR from Table 2)  
  > "the values of $M_{\star}$ and SFR are simply adopted from Table 2 in (cite: Tacconi2013)" (5.1) [from (cite: Tacconi2013)]
- External data: ALESS SMG 870 um fluxes and SED parameters  
  > "primary beam corrected flux, column 8 in Table 3" (5.2) [from (cite: Hodge2013); (cite: da Cunha2015)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: CASA 4.2.2 for calibration, 4.6.0 for imaging  
  > "used 4.2.2 version for calibration and imaged with 4.6.0 version" (3.1)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Band 6 Neptune; Band 3 Titan  
  > "The flux calibrator was Titan for Band 3." (3.1)
- flux scale uncertainty: ~15-18%, not included in flux errors  
  > "The absolute flux uncertainties for both bands were estimated as$\sim15-18$%" (3.1)
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "We applied the CLEAN algorithm to the calibrated visibilities with natural weighting" (3.1)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: flux measured after primary beam correction  
  > "We measured the flux after primary beam correction." (3.2.2)
- array combination: _not stated_
- smoothing: imsmooth Gaussian kernel 0.8x0.8 arcsec (Band 6), 0.6x0.6 arcsec (Band 3), channel by channel  
  > "We adopted a smoothing Gaussian kernel size of $0^{\prime\prime}.8\times0^{\prime\prime}.8$ for Band 6 and $0^{\prime\prime}.6\times0^{\prime\prime}.6$ for Band 3." (3.2.2)
- final beam: smoothed 1.1x0.9 arcsec (Band 3), 1.1x1.0 arcsec (Band 6)  
  > "$1^{\prime\prime}.1\times0^{\prime\prime}.9$ for Band 3 and $1^{\prime\prime}.1\times1^{\prime\prime}.0$ for Band 6" (3.2.2)
- final rms: _not stated_

### Inherited from earlier work

- CO gas mass recipe, metallicity-dependent alpha_CO  
  > "We derived the gas mass from CO (3–2) emission by following the prescription presented in (cite: Genzel2015)." (5.1) [from (cite: Genzel2015)]
- dust-based gas mass method with Td=25 K  
  > "We derive gas mass from dust continuum detection using a method presented in (cite: Scoville2016)." (5.2) [from (cite: Scoville2016)]
- CO integration range chosen to maximize S/N  
  > "following the description in (cite: Seko2016)" (3.2.2) [from (cite: Seko2016)]
- Mstar, SFR and extinction correction from companion paper  
  > "the full description of the data reduction and analysis for these observations will be presented in I. Tanaka et al. (in preparation)" (4.1) [from I. Tanaka et al. (in preparation)]

### Not stated but needed to reproduce (our reading)

- Array configurations and observing dates
- Pipeline vs manual calibration
- Cell size, image size, clean threshold and masks
- Continuum line-free channels and continuum subtraction
- Exact velocity integration ranges per source
- Stellar masses and SFRs depend on unpublished Tanaka et al. analysis
- Projected-density kernel details and survey volume computation

## Analysis recipe

1. **calibrate and image**: CLEAN with natural weighting on calibrated visibilities  
  > "We applied the CLEAN algorithm to the calibrated visibilities with natural weighting" (3.1)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **detect sources and measure fluxes**: Smooth images with imsmooth, take peak flux (1.1 mm) or peak velocity-integrated flux (CO moment 0); detection criteria within 1 arcsec of HAEs  
  > "We adopted a peak flux at 1.1 mm or a peak velocity-integrated flux in the CO (3–2) moment 0 map to compute gas mass" (3.2.2)
   - software: CASA
   - parameter: 1.1 mm detection >4 sigma; CO needs 2 of 3 criteria (peak >4 sigma, two channels >3.5 sigma, integrated S/N >5)  
  > "A CO (3–2) line was regarded as detected if at least two among three criteria (a-c) are satisfied" (3.2.1)
   - fitting: _not stated_
   - validation: compared with imfit Gaussian, clipped aperture photometry and specfit; growth curves for kernel choice  
  > "We also checked whether the peak flux is consistent with other flux measurements, i.e., Gaussian fitting (using CASA commend `imfit`)" (Flux versus S/N)
3. **CO-based gas mass**: M_gas = alpha_CO x L'_CO with alpha_MW=4.36 times metallicity factor A(Z), R13=1.9  
  > "We use a standard luminosity (brightness temperature) line ratio between different rotational transitions of CO, i.e., CO (1–0)-to-CO(3-2) ratio $R_{13} = 1.9$" (5.1)
   - parameter: alpha_CO,1 in range [4.4, 5.9]  
  > "The adopted metallicity-dependent conversion factor is in the range of $\alpha_{\rm CO, 1}=[4.4, 5.9]$." (5.1)
   - assumption: metallicity from empirical mass-metallicity relation (Genzel2015 eq 12a, Wuyts2014)  
  > "we adopted the galaxy’s metallicity derived from an empirical mass-metallicity relation" (5.1)
   - fitting: _not stated_
   - validation: compared to dust-based masses  
  > "The gas masses derived from different estimators of CO (3–2) and 1.1 mm are roughly consistent with each other" (5.3 Combined results of SFR vs $M_{\rm gas}$)
4. **dust-based gas mass**: Scoville RJ-tail luminosity-to-mass relation  
  > "Therefore, we assume a dust temperature of 25 K to weigh the global gas amount" (5.2)
   - assumption: Td = 25 K  
  > "we assume a dust temperature of 25 K" (5.2)
   - fitting: _not stated_
   - validation: _not stated_
5. **gas fraction, comparison and gas density**: f_gas = Mgas/(Mgas+Mstar); compare with PHIBBS-I and ALESS main-sequence galaxies; protocluster gas density from CO detections over survey volume  
  > "The survey area is 14 comoving Mpc$^2$, and we adopted a $\sim$20% sensitivity region (a radius of 37$^{\prime\prime}$) with our 4-pointing observations." (6.3)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.2.2 (calibration), 4.6.0 (imaging): calibration, CLEAN imaging, imsmooth, immath, imfit, specfit  
  > "Common Astronomy Software Applications package (CASA, used 4.2.2 version for calibration and imaged with 4.6.0 version)" (3.1)
- **FAST** : SED fitting for stellar mass calibration  
  > "calibrated from empirical fitting between (cite: Bruzual2003) (BC03) and the spectral energy distribution (SED) fitting with the FAST code" (4.1 MOIRCS/Subaru NIR data : Mstar and SFR)
- **MOPEX** : Spitzer MIPS image processing  
  > "We used MOPEX software package for image processing." (4.2)
- **Astropy** : listed in software  
  > "CASA (cite: casa2007) , Astropy (cite: astropy2013)" (Software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| CO(3-2) detections | 7 of 22 HAEs | not stated | sources | 2 | seven CO detections out of 22 targeted H$\alpha$ emitters (HAEs) |
| 1.1 mm detections | 4 of 19 | not stated | sources | 2 | four out of 19 in 1.1 mm dust continuum |
| mean f_gas from CO(3-2) | 0.53 | 0.07 | dimensionless | 5 | $\langle f_{\rm gas}\rangle = 0.53 \pm 0.07$ from CO (3–2) |
| mean f_gas from 1.1 mm | 0.50 | 0.06 | dimensionless | 5 | 0.50 $\pm$ 0.06 for 1.1 mm measurement |
| protocluster cosmic gas density (CO-detected range) | ~5e9 | not stated | Msun Mpc^-3 | 5 | the cosmic gas density is estimated as $\rho_{\rm gas, 4C23.56}\sim 5 \times 10^{9} \,M_{\odot}\, {\rm Mpc}^{-3}$ |
| Mgas from dust | (0.5-1.4)e11 | not stated | Msun | 4 | in the range of $(0.5-1.4)\times 10^{11}$ M$_{\odot}$ for four objects |
| Mstar-SFE Pearson correlation excluding AGN | 0.89 | p=0.02 | dimensionless | 5 | Pearson’s correlation coefficient (in log scale) = 0.89 with a p-value of 0.02 |

## Qualitative findings

- CO- and dust-based gas masses are consistent for simultaneous detections, though dust-based values are systematically smaller  
  > "The gas mass derived from 1.1 mm is systematically smaller for all four cases" (5.3)

## Claim tuples

- H: Protocluster main-sequence galaxies have gas fractions similar to field galaxies | E: CO(3-2) and 1.1 mm gas masses compared with PHIBBS-I and ALESS main-sequence samples | R: <f_gas>=0.53±0.07 (CO) vs 0.49±0.05 for PHIBBS-I MS | F: gas fractions comparable to field | **supported**
- H: Protoclusters have higher cosmic gas density than general fields | E: Gas density from CO detections over survey volume vs HUDF limit | R: ~5e9 Msun/Mpc^3, ~22x above field limit (6x with wider range) | F: protocluster gas density higher by an order of magnitude | **supported**
- H: Environment affects SFE and stellar mass | E: Compare detections with surface galaxy density | R: five of seven CO detections in highest-density region; positive Mstar-SFE correlation | F: possible environmental role, needs confirmation | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Smoothing images gave better S/N than uv tapering and avoids divergent Gaussian fits for disturbed galaxies  
  > "We found that image-based smoothing delivers a better S/N than tapering the uv visibilities." (3.2.2)
- Alternative: U/LIRG-like alpha_CO=0.8 disfavoured since it makes CO and dust masses inconsistent  
  > "The U/LIRG-like conversion factor yields larger inconsistencies between different estimators" (6.3)
- How they decided it was enough: _not stated_
- Limitation (authors): Small number of detections; sample bias cannot be rejected  
  > "We cannot reject this argument with the current data set." (6.4.2)
- Caveat (inferred, ours): Mstar and SFR rely on unpublished data and a single extinction recipe
- Caveat (inferred, ours): Universal smoothing kernel and peak-flux measurement may bias fluxes
- Caveat (inferred, ours): Gas density is a lower limit and uses small volume with cosmic-variance uncertainty
- Caveat (inferred, ours): alpha_CO assumed with no independent test

## Reproducibility

- Data public (paper): ALMA data acknowledged as project 2012.1.00242.S; public status not stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2012.1.00242.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Mstar and SFR tables depend on in-preparation paper
- Missing: Detailed imaging parameters and velocity ranges
- Data volume (inferred): ~50-150 GB raw for two bands
- Score (inferred): 3/5, Public project and clear gas mass formulae, but imaging details and Mstar/SFR inputs are partly unstated.
- Rediscovery candidate: yes, Public data, formulae stated, results numeric; Mstar/SFR taken from Table 1.

## Links

- Method: (cite: Genzel2015) (CO gas mass prescription)
- Method: (cite: Scoville2016) (dust gas mass method)
- Method: (cite: Seko2016) (CO integration range)
- Companion: I. Tanaka et al., in preparation (HAE Mstar/SFR derivation)
- Companion: M. Lee et al., in preparation (kinematics and SED fitting)
- Related: MAHALO-Subaru
- Related: PHIBBS-I
- Related: ALESS

## Checks

```json
{
 "quotes": 61,
 "quotes_ok": 61,
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
  "facts": 78,
  "stated": 45,
  "rate": 0.577
 },
 "evidence_ok": true
}
```
