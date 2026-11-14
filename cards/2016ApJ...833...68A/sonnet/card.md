# The ALMA Spectroscopic Survey in the Hubble Ultra Deep Field: Continuum Number Counts, Resolved 1.2 mm Extragalactic Background, and Properties of the Faintest Dusty Star-forming Galaxies

`2016ApJ...833...68A` | The Astrophysical Journal 2016 | first author: Aravena, M. | arXiv: 1607.06769 | DOI: 10.3847/1538-4357/833/1/68

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type large_program_or_survey

## Science

- Fields: high_z_galaxies, cosmology
- Question: What are the 1.2-mm continuum number counts, the resolved fraction of the extragalactic background, and the properties of the faint dusty star-forming galaxies detected in the ASPECS Hubble UDF field?  
  > "For the first time, we are able to characterize the population of galaxies that dominate the EBL at 1.2 mm." (abstract)
- Target **Hubble Ultra Deep Field (ASPECS ~1 arcmin^2 region)**: coordinates _not stated_; z/distance detected sources at z=1-3 (median z=1.7±0.4)  
  > "Our ALMA observations cover a $\sim1$ arcmin$^2$ region within the deepest 4.7 arcmin$^2$ of the *Hubble* UDF: the eXtremely Deep Field (XDF)." (2.2 Multi-wavelength data); distance from spectroscopic and photometric redshifts from Skelton et al. 2014  
  > "Our ALMA observations cover a $\sim1$ arcmin$^2$ region within the deepest 4.7 arcmin$^2$ of the *Hubble* UDF: the eXtremely Deep Field (XDF)." (2.2 Multi-wavelength data)

## Data provenance

- ALMA projects: 2013.1.00146.S, 2013.1.00718.S
- bands: Band 3 and Band 6 (3 mm and 1.2 mm)  
  > "ALMA band 3 and band 6 observations were obtained during Cycle-2" (2.1 ALMA observations and data reduction)
- frequencies and spectral setup: Band 3: 5 tunings, 84.2-114.9 GHz, single pointing; Band 6: 8 tunings, 212.0-272.0 GHz, 7-point mosaic  
  > "We scanned band 6 using eight frequency tunings, covering $212.0-272.0$ GHz." (2.1 ALMA observations and data reduction)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: C34-2 (band 3) and C34-1 (band 6)  
  > "Observations in bands 3 and 6 were taken with ALMA’s compact array configurations, C34-2 and C34-1, respectively." (2.1 ALMA observations and data reduction)
- baselines: _not stated_
- angular resolution: 3.6''x2.1'' (band 3), 1.7''x0.9'' (band 6)  
  > "resulting in synthesized beam sizes of $3.6''\times2.1''$ and $1.7''\times0.9''$ from the low to high frequency ends of bands 3 and 6, respectively." (2.1 ALMA observations and data reduction)
- max recoverable scale: _not stated_
- sensitivity: rms 12.7 uJy (1.2 mm) and 3.8 uJy (3 mm) at map centres  
  > "We reach an rms sensitivity of $12.7\mu$Jy and $3.8\mu$Jy in the centres of the 1.2-mm and 3-mm maps, respectively." (2.1 ALMA observations and data reduction)
- time on source: _not stated_
- observing dates: Band 3: 2014 Jul 1 - 2015 Jan 5; Band 6: 2014 Dec 12 - 2015 Apr 21  
  > "Observations in band-3 were conducted between July 01, 2014 to January 05, 2015, and observations in band 6 were conducted between December 12, 2014 to April 21, 2015" (2.1 ALMA observations and data reduction)
- pi or archival as stated: _not stated_
- Other facility **HST (ACS, WFC3/IR; HUDF09, HUDF12, CANDELS)**: optical/near-IR photometry and counterparts  
  > "Available data includes *HST* Advanced Camera for Surveys (ACS) and Wide Field Camera 3 IR data from the HUDF09, HUDF12 and Cosmic Assembly Near-infrared Deep Extragalactic Legacy Survey (CANDELS) programs" (2.2 Multi-wavelength data)
- Other facility **Spitzer IRAC/MIPS, Herschel PACS/SPIRE**: IR coverage; Herschel not used in SED fits due to blending  
  > "We do not include *Herschel* photometry in the fits since its angular resolution is very poor" (4.2 Identification and SED fitting)
- External data: Photometric and spectroscopic redshift catalog and 26-band photometry of the field  
  > "including the photometric and spectroscopic redshift information available from (cite: skelton14)" (2.2 Multi-wavelength data) [from (cite: skelton14)]
- External data: Main-sequence fit as function of redshift  
  > "compare with the main-sequence fit derived by Whitaker et al. (2014)" (4.4 Starburst versus Main sequence) [from (cite: whitaker14)]
- External data: Planck CIB intensity (Table 10) used to derive EBL at 242 GHz of 14.2±0.6 Jy/deg2  
  > "By interpolating the *Planck* measurements (see their Table 10) over the frequency range of our observations (212-272 GHz), we find an EBL at $\sim242$ GHz of $14.2\pm0.6$ Jy deg$^{-2}$." (7.1 Integrated intensity and fraction of the EBL) [from (cite: planck14)]
- External data: Bright-end number counts from Karim et al. Table 1 and Oteo et al. counts  
  > "we use the results from from (cite: karim13) and (cite: oteo15)." (7.1 Integrated intensity and fraction of the EBL) [from (cite: karim13); (cite: oteo15)]
- External data: Literature number counts for comparison, flux scaling from Fujimoto et al.  
  > "We scale the flux densities of the different studies as $S_{\rm 1.2mm}=0.4~S_{\rm 870}$, $S_{\rm 1.2mm}=0.8~S_{\rm 1.1mm}$ and $S_{\rm 1.2mm}=1.3~S_{\rm 1.3mm}$ (cite: fujimoto16)." (5 Number counts) [from (cite: fujimoto16)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: tight boxes on continuum sources detected at >5 sigma in dirty maps; clean to 2.5 sigma  
  > "we produced ‘clean’ maps masking with tight boxes all the continuum sources previously detected in the ‘dirty’ maps with significances above $5\sigma$, and cleaning down to a $2.5\sigma$ threshold." (2.1 ALMA observations and data reduction)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: source extraction done prior to PB correction; extraction out to PB=0.3  
  > "Source detection was performed using SExtractor (cite: bertin96) in the ALMA 1.2-mm and 3-mm maps prior to PB correction." (3.1 Source detection and flux measurements)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 1.7''x0.9'' at 1.2 mm  
  > "With an ALMA beam size at 1.2-mm of $1.7''\times0.9''$" (2.1 ALMA observations and data reduction)
- final rms: 12.7 uJy (1.2 mm centre), 3.8 uJy (3 mm centre)  
  > "We reach an rms sensitivity of $12.7\mu$Jy and $3.8\mu$Jy in the centres of the 1.2-mm and 3-mm maps, respectively." (2.1 ALMA observations and data reduction)

### Inherited from earlier work

- Survey setup and data reduction steps  
  > "The ASPECS survey setup and data reduction steps are described in detail in Paper I (Walter et al. 2016)." (2.1 ALMA observations and data reduction) [from Paper I (cite: walter16)]
- Flux scaling between wavelengths for number counts  
  > "$S_{\rm 1.2mm}=0.4~S_{\rm 870}$, $S_{\rm 1.2mm}=0.8~S_{\rm 1.1mm}$ and $S_{\rm 1.2mm}=1.3~S_{\rm 1.3mm}$ (cite: fujimoto16)" (5 Number counts) [from (cite: fujimoto16)]
- ISM mass from RJ dust continuum  
  > "Following (cite: scoville14), we compute the ISM mass in units of $10^{10} M_\ensuremath{\odot}$ as:" (6.1 Gas masses from dust, and caveats) [from (cite: scoville14)]
- Gas-to-dust ratio vs metallicity  
  > "This metallicity value would translate into $\delta_{\rm GDR}\sim200$ (cite: remyruyer14)." (6.1 Gas masses from dust, and caveats) [from (cite: remyruyer14)]

### Not stated but needed to reproduce (our reading)

- CASA version and calibration/imaging details (robust, uv taper, cell size, image size, continuum channel selection), deferred to Paper I
- Exact SExtractor configuration beyond minimum area and threshold
- Whether the 1.2 mm map used is the collapsed cube of all channels with line masking
- Weighting scheme for the Gaussian peak fitting and error estimates
- MAGPHYS priors and parameter grids
- Exact bins and cumulative-sum procedure for number counts, and effective area as function of PB
- Details of the stacking catalogs and selection of main-sequence cut
- Number of Monte Carlo realizations for error propagation of the counts

## Analysis recipe

1. **Detect sources and measure fluxes**: SExtractor detection on non-PB-corrected maps; 2D Gaussian fit, peak flux used for unresolved sources  
  > "We compute fluxes based on 2-dimensional Gaussian fit centered at the location of the SExtractor detection." (3.1 Source detection and flux measurements)
   - software: SExtractor
   - parameter: minimum area 5 pixels (1.5''); extraction down to 2.5 sigma local; main sample >3.5 sigma  
  > "We use a minimum area of 5 pixels ($1.5''$) for detection, extracting sources down to 2.5$\sigma$, where $\sigma$ is evaluated locally for each source." (3.1 Source detection and flux measurements)
   - fitting: _not stated_
   - validation: fitted values agree with pixel values at source positions  
  > "These fitted values are in agreement with the actual pixel values at the position of the sources." (3.1 Source detection and flux measurements)
2. **Compute fidelity and completeness**: Fidelity from detections in inverted negative map; completeness from Monte Carlo injection of artificial point sources; both parametrised with erf functions  
  > "We ingest 10 artificial point-like sources with randomly generated flux levels (between $10-300 \mu$Jy) in the ALMA map." (3.2 Fidelity and completeness)
   - parameter: 100 artificial sources total (10x10), matched within 1''; fidelity A=log10(42), B=1/4; completeness A'=log10(35), B'=0.45  
  > "We repeat this process 10 times, for a total of 100 artificial sources." (3.2 Fidelity and completeness)
   - fitting: _not stated_
   - validation: input and recovered flux densities agree within uncertainties  
  > "the input and recovered flux densities agree well within individual source uncertainties." (3.2 Fidelity and completeness)
3. **Derive cumulative number counts**: N(S_i) = (1/A) sum P_j/C_j, summed cumulatively; Poisson plus flux errors  
  > "Since we are limited by the modest number of detections, we compute the cumulative number counts rather than computing differential counts" (5 Number counts)
   - parameter: extended to 3 sigma, where fidelity and completeness are both 50%  
  > "we extend our number count measurements down to significances of $3\sigma$." (5 Number counts)
   - fitting: _not stated_
   - validation: compared with literature counts  
  > "Our ALMA UDF observations appear to be in general agreement with these earlier measurements" (5 Number counts)
4. **Identify counterparts and fit SEDs**: Optical counterparts within 1'' radius; HST positions shifted by 0.3'' to match ALMA; MAGPHYS SED fit with 26 filters at fixed best redshift  
  > "We fit the spectral energy distribution (SED) of the continuum–detected galaxies using the high-redshift extension of `MAGPHYS` (cite: dacunha08; dacunha15)." (4.2 Identification and SED fitting)
   - software: MAGPHYS
   - parameter: 26 filters, U band to IRAC 8 um, plus ALMA 1.2 mm; no Herschel  
  > "We use the available 26 broad and medium band filters in the optical and infrared regimes, from the $U$ band to *Spitzer* IRAC 8$\mu$m." (4.2 Identification and SED fitting)
   - fitting: redshift fixed at best available value  
  > "For each individual galaxy, we perform SED fits to the photometry fixed at the best available redshift." (4.2 Identification and SED fitting)
   - validation: comparison to main sequence of Whitaker et al. 2014  
  > "We thus conclude that our faint ALMA 1.2-mm continuum sources are main-sequence galaxies at $z\sim1-3$." (4.4 Starburst versus Main sequence)
5. **Stack undetected galaxies**: 9''x9'' cutouts from clean mosaic at catalog positions, PB-weighted average; noise from annulus of 4-12 pixels  
  > "All these sub-images are then combined together, to construct a weighted average using the PB sensitivity map as the weight." (5 Stacking analysis)
   - parameter: M*>1e9 Msun, z<4, F850LP and F160W <27.5 AB, within/above main sequence with 0.5 dex scatter, >3.5'' from five brightest detections  
  > "All samples have been selected to have $M_*>10^9\ M_\ensuremath{\odot}$ and $z<4$" (5.1 Nature of undetected galaxies)
   - fitting: _not stated_
   - validation: 3 sigma upper limits for non-detections  
  > "we do not find significant emission and thus place $3\sigma$ limits on the 1.2-mm flux densities" (5.1 Nature of undetected galaxies)
6. **Estimate dust emissivity index beta**: beta from 1.2 mm/3 mm flux ratio in the RJ, optically thin limit  
  > "Note that at the observed frequencies it is valid to assume the optically thin and RJ approximations." (5.2 Stacking in the 3-mm continuum)
   - assumption: single-component modified blackbody, optically thin, Rayleigh-Jeans  
  > "We use a single-component modified black body dust model in the optically thin regime" (5.2 Stacking in the 3-mm continuum)
   - fitting: _not stated_
   - validation: _not stated_
7. **Derive ISM masses, depletion times and gas fractions**: Scoville et al. 2014 RJ dust calibration; compared with MAGPHYS dust mass times gas-to-dust ratio  
  > "From this dust mass estimate, and under the assumption of a fixed gas-to-dust ratio $(\delta_{\rm GDR})$ and that the ISM is mostly molecular, one can obtain a measurement of the gas mass as $M_{\rm gas}=\delta_{\rm GDR} M_{\rm d}$." (6.1 Gas masses from dust, and caveats)
   - software: MAGPHYS
   - assumption: Td=25 K, beta=1.8, delta_GDR=200 for MAGPHYS masses  
  > "This method to compute ISM masses assumes a dust emissivity index $\beta=1.8$, which we use throughout for consistency with other studies." (6.1 Gas masses from dust, and caveats)
   - fitting: _not stated_
   - validation: compared with CO-based masses of Paper IV; dust-based lower by factor ~3-4  
  > "under-predict the gas masses by a factor of $\sim3-4$ compared to the CO based estimates." (6.1 Gas masses from dust, and caveats)
8. **Compute EBL contribution**: Integrate fidelity/completeness-corrected counts, add bright end from Karim+13 and Oteo+15 and stacking contributions of m2+m3; compare with Planck EBL at 242 GHz  
  > "we directly integrate the number counts, corrected for fidelity and completeness, down to the faintest flux bin ($S_{\rm 1.2mm}\sim37\mu$Jy)." (7.1 Integrated intensity and fraction of the EBL)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **SExtractor** : source detection in 1.2 mm and 3 mm maps  
  > "Source detection was performed using SExtractor (cite: bertin96)" (3.1 Source detection and flux measurements)
- **MAGPHYS** high-redshift extension: SED fitting for stellar mass, SFR, dust mass, L_IR  
  > "`MAGPHYS` delivers estimates for the stellar masses, star formation rate (SFR), dust mass and IR luminosity." (4.2 Identification and SED fitting)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Number of sources >3.5 sigma at 1.2 mm | 9 | not stated | sources | 1 | Nine sources are detected in the 1.2-mm map at a significance above 3.5$\sigma$. |
| Median redshift of detected sources | 1.7 | 0.4 | dimensionless | 4 | We find that our faint ALMA millimeter-selected galaxies, however, have a median redshift $z=1.7\pm0.4$. |
| Median stellar mass | 4.0e10 | not stated | Msun | 4 | Our sources show a median stellar mass of $4.0\times10^{10}\ M_\odot$ and a median SFR of $40\ M_\ensuremath{\odot}$ yr$^{-1}$ |
| Median SFR | 40 | not stated | Msun/yr | 4 | Our sources show a median stellar mass of $4.0\times10^{10}\ M_\odot$ and a median SFR of $40\ M_\ensuremath{\odot}$ yr$^{-1}$ |
| Integrated intensity from number counts | 7.8 | 0.4 | Jy/deg2 | 8 | We obtain an integrated intensity of $7.8\pm0.4$ Jy deg$^{-2}$. |
| Fraction of Planck EBL from individual detections | 55% | 4% | percent | 8 | This makes up $55\pm4\%$ of the EBL measured by *Planck* at 242 GHz |
| Total EBL fraction with bright end and stacking | 80% | 7% | percent | 8 | which makes up $80\pm7\%$ ($\sim77--84\%$) of the EBL at 242 GHz measured by *Planck*. |
| Beta for ASPECS C1 | 1.3 | 0.2 | dimensionless | 6 | we find $\beta=1.3\pm0.2$. |
| Stacked 1.2 mm flux of z=1-2 sample (z2) | 12 | 4 | uJy | 5 | / z2 / $z=1-2$ / $1.22\pm0.20$ / $0.52\pm0.63$ / $9.45\pm0.43$ / 11 / $12\pm4$ / |
| EBL extra contribution from stacking | 2.8 | 0.5 | Jy/deg2 | 8 | We find an extra contribution of $2.8\pm0.5$ Jy deg$^{-2}$ or $\sim20\pm4\%$ of the EBL at 242 GHz. |

## Qualitative findings

- All 1.2 mm sources above 3.5 sigma with counterparts lie at z=1-3 and are consistent with the main sequence.  
  > "We thus conclude that our faint ALMA 1.2-mm continuum sources are main-sequence galaxies at $z\sim1-3$." (4.4 Starburst versus Main sequence)
- Dust-based gas fractions are lower than for main-sequence galaxies at similar redshifts, while depletion times agree.  
  > "they have gas fractions that are much lower than the those found for same comparison samples." (6.2 Gas depletion timescales and fractions)

## Claim tuples

- H: Do faint 1.2 mm-selected galaxies lie at lower redshift than bright SMGs? | E: Counterpart identification and redshift compilation for >3.5 sigma sources | R: median z=1.7±0.4, no source at z>3 | F: Faint mm-selected galaxies are at lower redshift than bright DSFGs | **supported**
- H: Are the faint DSFGs starbursts or main sequence? | E: SED fitting and SFR-M* comparison with Whitaker+14 | R: all within scatter of main sequence | F: Main-sequence galaxies | **supported**
- H: What fraction of the 1.2 mm EBL is resolved? | E: Integrate counts, add bright end and stacking | R: 55±4% from detections; 80±7% total | F: Most of the EBL is resolved by faint main-sequence galaxies at z~1.7 | **supported**
- H: Are the dust-based gas masses consistent with CO-based estimates? | E: Scoville and MAGPHYS gas masses compared with Paper IV | R: dust-based lower by factor ~3-4 (~2 in abstract) | F: Dust-based masses likely underestimated, giving low gas fractions | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: 3.5 sigma cut chosen because fidelity is ~50-60% there  
  > "This significance level cut corresponds to roughly $50-60\%$ fidelity of the sample" (3.1 Source detection and flux measurements)
- Alternative: Herschel photometry excluded from SED fits due to blending.  
  > "The *Herschel* photometry is thus heavily blended." (4.2 Identification and SED fitting)
- How they decided it was enough: _not stated_
- Limitation (authors): Small area makes counts and EBL fraction subject to cosmic variance.  
  > "measurements covering $\sim$1 arcmin$^{-2}$ or less of the sky, aiming to resolve the sources contributing to this background will be most likely highly affected by cosmic variance." (7.3 The effect of cosmic variance)
- Limitation (authors): Flux may be missed for resolved sources given small beam; beta result affected.  
  > "we could be missing flux that could contribute to a larger $\beta$ value." (5.2 Stacking in the 3-mm continuum)
- Caveat (inferred, ours): Only 9 detections, so medians and counts have large Poisson uncertainty
- Caveat (inferred, ours): Gas masses depend on assumed Td, beta, gas-to-dust ratio
- Caveat (inferred, ours): Stacking affected by possible confusion at these depths
- Caveat (inferred, ours): Counterpart-less sources may be spurious or high-z
- Caveat (inferred, ours): EBL fraction depends on bright-end counts from other studies

## Reproducibility

- Data public (paper): ALMA data cited by project code; public status not stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2013.1.00146.S and ADS/JAO.ALMA#2013.1.00718.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Calibration and imaging parameters deferred to Paper I
- Missing: Reduced maps and PB map not given
- Missing: MAGPHYS setup details
- Missing: SExtractor configuration
- Data volume (inferred): Tens of GB raw for the two projects
- Score (inferred): 3/5, Data are identified and the analysis is described, but calibration and imaging settings are deferred to Paper I and several catalog steps are only roughly specified.
- Rediscovery candidate: no, Imaging details are in Paper I and the stacking and counts rely on external catalogs, so the recipe is not complete from this paper alone.

## Links

- Method: (cite: walter16) (Survey setup, data reduction)
- Method: (cite: scoville14) (ISM mass from dust continuum)
- Method: (cite: dacunha15) (MAGPHYS high-z extension)
- Companion: (cite: decarli16a) (Paper III, CO luminosity function)
- Companion: (cite: decarli16b) (Paper IV, CO-brightest objects and gas masses)
- Companion: (cite: aravena16b) (Paper V, line search)
- Related: ASPECS
- Related: HUDF/XDF
- Related: CANDELS

## Checks

```json
{
 "quotes": 72,
 "quotes_ok": 72,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 10,
 "numeric_problems": 0,
 "fill": {
  "facts": 92,
  "stated": 55,
  "rate": 0.598
 },
 "evidence_ok": true
}
```
