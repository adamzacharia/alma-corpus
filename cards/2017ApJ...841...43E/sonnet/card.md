# ALMA CO Clouds and Young Star Complexes in the Interacting Galaxies IC 2163 and NGC 2207

`2017ApJ...841...43E` | The Astrophysical Journal 2017 | first author: Elmegreen, Debra Meloy | arXiv: 1704.03086 | DOI: 10.3847/1538-4357/aa6ba5

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, star_formation
- Question: What are the mass distributions of CO clouds in IC 2163 and NGC 2207, and how do clouds relate to young star complexes seen with HST?  
  > "used to determine the properties of molecular clouds and their association with star-forming regions observed with the Hubble Space Telescope." (abstract)
- Target **IC 2163 and NGC 2207**: coordinates _not stated_; z/distance 35 Mpc  
  > "IC 2163 and NGC 2207 are at a distance of 35 Mpc (NASA/IPAC Extragalactic Database, NED)." (2.1 Data); distance from NED  
  > "IC 2163 and NGC 2207 are at a distance of 35 Mpc (NASA/IPAC Extragalactic Database, NED)." (2.1 Data)

## Data provenance

- ALMA projects: 2012.1.00357.S
- bands: _not stated_
- frequencies and spectral setup: 12CO(1-0), 2.6 mm, channel width 10 km/s, rms 3.7 mJy/beam per channel  
  > "a channel width of $10$ km s$^{-1}$, and an rms noise per channel of $3.7$ mJy beam$^{-1}$" (2.1 Data)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: 34 pointings  
  > "were made in 34 pointings" (2.1 Data)
- baselines: _not stated_
- angular resolution: 2.00" x 1.52" (HPBW)  
  > "with a point spread function of $2.00^{\prime\prime} \times 1.52^{\prime\prime}$ (HPBW)" (2.1 Data)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: 12CO J=1-0 (not stated)
- Other facility **HST WFPC2**: F336W, F439W, F555W, F814W images for star complexes  
  > "taken with filters F336W (U), F439W (B), F555W (V), and F814W (I)" (2.1 Data)
- Other facility **Spitzer IRAC/MIPS**: 8 and 24 micron data  
  > "Spitzer IRAC observations at 8$\mu m$ and MIPS observations at 24$\mu m$" (2.1 Data)
- Other facility **VLA**: 6 cm radio continuum  
  > "Radio continuum observations at 6 cm observed with the Karl G. Jansky Very Large Array (VLA)" (2.1 Data)
- External data: Total H2 masses, SF aperture definitions, SFRs, HI masses from Paper I  
  > "For IC 2163, the H$_2$ mass is $2.1\times10^9\; M_\odot$ and for NGC 2207, it is $2.3\times10^9\;M_\odot$." (2.2 Identification of CO Clouds) [from (cite: elmegreen16)]
- External data: X_CO = 1.8e20 conversion factor  
  > "$X_{\rm CO}= 1.8 \pm 0.3 \times10^{20}$ $H_2$ cm$^{-2}$ (K km s$^{-1}$)$^{-1}$ from (cite: dame01)" (2.3 CO Masses) [from (cite: dame01)]

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
- masking: smooth-plus-velocity continuity blanking mask applied to unsmoothed cube  
  > "creating a blanking mask via the technique of smooth-plus-velocity continuity (cf. Papers I and II) and applying it to the original unsmoothed cube" (2.2 Identification of CO Clouds)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: CO convolved to 2.5" for comparison with radio image  
  > "with the CO image convolved to the 2.5” resolution of the radio image" (3.2 NGC 2207 Nuclear Region)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- ALMA data reduction  
  > "Further data reduction techniques are given in Papers I and II." (2.1 Data) [from Papers I and II (cite: elmegreen16; cite: kaufman16)]
- Blanking mask technique  
  > "smooth-plus-velocity continuity (cf. Papers I and II)" (2.2 Identification of CO Clouds) [from Papers I and II]
- Population synthesis fitting method  
  > "performed using the methods described in (cite: elm12)" (2.5 Star-forming Complexes and CO Clouds) [from (cite: elm12)]

### Not stated but needed to reproduce (our reading)

- Details of ALMA calibration and imaging (CASA version, weighting, cleaning, flux calibrator)
- Mask smoothing parameters and velocity continuity thresholds
- Exact bin edges/fit ranges for mass function slopes
- Cloud rectangle photometry boundaries
- Cloud catalog not given

## Analysis recipe

1. **identify CO clouds**: Visual identification in DS9 on masked CO surface density image; cuts on pixel intensity, channel count and resolution; SExtractor as comparison  
  > "we identified 327 discrete CO clouds by eye in the resulting surface density image in DS9" (2.2 Identification of CO Clouds)
   - software: DS9, SExtractor
   - parameter: 2 or more pixels above I(CO)=200 Jy/beam m/s; at least 2 channels above 2 sigma  
  > "clouds that contained 2 or more pixels (2 px = 1.0” = 170 pc at the assumed distance of 35 Mpc) above a CO intensity $I(CO)= 200$ Jy beam$^{-1}$ m s$^{-1}$" (2.2 Identification of CO Clouds)
   - fitting: _not stated_
   - validation: SExtractor run gave 178 clouds, same slope in overlapping mass range  
  > "the mass function for clouds identified by SExtractor has the same slope in the$\log_{10}(M/M_\odot)$ range of 6.6 to 7.6" (2.3 CO Masses)
2. **measure cloud H2 masses**: Variable-rectangle photometry with IRAF imstat, converted with X_CO  
  > "Photometry on the visually-identified CO clouds was done with the Image Reduction and Analysis Facility (IRAF) task *imstat*" (2.3 CO Masses)
   - software: IRAF
   - assumption: X_CO = 1.8e20 H2 cm-2 (K km/s)-1; factor 1.36 for total gas  
  > "should be multiplied by 1.36 to get the total gas mass, including helium and heavy elements" (2.3 CO Masses)
   - fitting: _not stated_
   - validation: _not stated_
3. **cloud mass functions**: Histograms in 0.2 dex bins with linear fits in log-log  
  > "binned in $\log_{10}(M/M_\odot)$ intervals of 0.2" (2.3 CO Masses)
   - fitting: linear fit  
  > "The linear fitting functions for each sample are shown in the matching color." (2.3 CO Masses)
   - validation: _not stated_
4. **star complex ages and masses from HST**: SExtractor on F439W, photometry in other filters, population synthesis fits  
  > "we ran SExtractor on the F439W images for each galaxy to identify the most prominent star-forming regions" (2.5 Star-forming Complexes and CO Clouds)
   - software: SExtractor, IRAF imexamine
   - parameter: 10 contiguous pixels above 10 sigma  
  > "restricted to 10 contiguous pixels greater than the $10\sigma$ threshold" (2.5 Star-forming Complexes and CO Clouds)
   - assumption: Bruzual & Charlot models, solar abundance, exponentially decaying SFH with 10 Myr decay time  
  > "The star formation history for each region was assumed to be a decaying exponential with a decay time of 10 Myr." (2.5 Star-forming Complexes and CO Clouds)
   - fitting: _not stated_
   - validation: _not stated_
5. **cross-correlate complexes with clouds**: Compare complex masses within 300 and 500 pc of clouds and within 2400 pc SF apertures  
  > "cross-correlated to search for star-forming regions within 300 pc and 500 pc of the CO clouds" (2.6 Correlations)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **SExtractor** : source extraction in CO and HST images  
  > "we also ran the CO intensity image through the source extraction program SExtractor" (2.2 Identification of CO Clouds)
- **IRAF** : imstat photometry and imexamine  
  > "Photometry on the visually-identified CO clouds was done with the Image Reduction and Analysis Facility (IRAF) task *imstat*" (2.3 CO Masses)
- **DS9** : visual cloud identification  
  > "we identified 327 discrete CO clouds by eye in the resulting surface density image in DS9" (2.2 Identification of CO Clouds)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Number of CO clouds | 249 | not stated | clouds | 1 | The final number of clouds was then 249 |
| Eyelid cloud mass function slope | -0.7 | 0.1 | dimensionless | 3 | The eyelid cloud mass function has a slope of $-0.7\pm 0.1$ |
| Non-eyelid cloud mass function slope | -1.3 | 0.1 | dimensionless | 3 | the rest of the clouds have a slope of $-1.3\pm 0.1$ |
| NGC 2207 main arms slope | -1.6 | 0.1 | dimensionless | 3 | the slope is $-1.6\pm 0.1$ |
| Sum of cloud H2 mass, IC 2163 | 7.4e8 | not stated | Msun | 2 | The sum of the cloud $H_2$ masses is $7.4\times10^8\;M_\odot$ for IC 2163 and $9.1\times10^8\;M_\odot$ for NGC 2207. |
| Star complex mass slope | -0.7 | 0.1 | dimensionless | 4 | The slopes are the same, $-0.7\pm 0.1$ |
| Complex-to-cloud mass ratio, <30 Myr, within 300 pc | 4.4% | not stated | percent | 5 | then the ratio of the summed complex mass to the cloud mass is 4.4% (4.9% for IC 2163 complexes) |
| Feature i central complex to CO mass ratio | 3.5% | not stated | percent | 5 | The ratio of the central star complex mass to the CO mass in the C-shaped contour structure of Figure [11](#feati) is 3.5%. |

## Qualitative findings

- Eyelid complexes older than 2e8 yr are deficient, consistent with destruction by the interaction  
  > "This suggests that processes that formed the eyelids destroyed the complexes there." (Conclusions)

## Claim tuples

- H: Do CO cloud mass functions differ between the IC 2163 eyelids and other regions? | E: Visually identified 249 clouds and fit log-log mass functions | R: Slope -0.7 in eyelids, -1.3 elsewhere, -1.6 in NGC 2207 main arms | F: Eyelid clouds resemble inner Milky Way; others are steeper like outer MW/M33 | **supported**
- H: Are eyelid star complexes younger than elsewhere? | E: Compared age distributions from SED fits | R: 1 of 77 eyelid complexes older than 2e8 yr vs 34 of 656 elsewhere | F: Older complexes destroyed in the eyelids, a 4 sigma result | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: SExtractor cloud identification rejected because it merged eyelid clouds into one  
  > "In what follows we use the visual identifications of clouds." (2.2 Identification of CO Clouds)
- How they decided it was enough: _not stated_
- Limitation (authors): Mass ratios are not true efficiencies as the association of complex with cloud is unknown  
  > "we do not know which complex formed in which cloud" (2.6 Correlations)
- Caveat (inferred, ours): Visual cloud identification at 340 pc resolution is subjective; clouds are really associations
- Caveat (inferred, ours): Single X_CO applied across starburst and disk regions
- Caveat (inferred, ours): Mass function slopes from binned log-log fits without stated fit ranges
- Caveat (inferred, ours): Age cut-off significance estimated with simple Poisson errors

## Reproducibility

- Data public (paper): ALMA project code given in acknowledgments  
  > "This paper used the following ALMA data: ADS/JAO.ALMA#2012.1.00357.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Calibrated CO cube and masks from Papers I and II
- Missing: Cloud and complex catalogs
- Missing: HST photometry details
- Data volume (inferred): tens of GB for 34-pointing mosaic
- Score (inferred): 3/5, Public ALMA data but processing is deferred to earlier papers and cloud identification is visual.
- Rediscovery candidate: no, Visual cloud selection and inherited reduction prevent a complete recipe.

## Links

- Method: (cite: elmegreen16) (Paper I: data reduction, masking, molecular masses)
- Method: (cite: kaufman16) (Paper II: data reduction and kinematics)

## Checks

```json
{
 "quotes": 47,
 "quotes_ok": 47,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 76,
  "stated": 34,
  "rate": 0.447
 },
 "evidence_ok": true
}
```
