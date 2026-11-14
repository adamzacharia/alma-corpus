# A dominant population of optically invisible massive galaxies in the early Universe

`2019Natur.572..211W` | Nature 2019 | first author: Wang, T. | arXiv: 1908.02372 | DOI: 10.1038/s41586-019-1452-4

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies
- Question: What is the true abundance and star-formation-rate density of massive galaxies at z>3 that are invisible in the UV/NIR (H-dropouts), and are they a bulk population?  
  > "This raises the questions of the true abundance of massive galaxies and the star-formation-rate density in the early universe." (abstract)
- Target **63 H-dropouts (IRAC [4.5]<24, no HST H-band counterpart) in CANDELS GOODS-S, UDS, COSMOS**: coordinates Listed per source in Extended Data Table 2  
  > "This left us 63 sources with 2 of them serendipitously detected in previous band-7 continuum observations with ALMA." (Methods 1.1); z/distance photometric z_median = 4 (ALMA-detected); two Lyα spec-z: 3.097 and 5.113  
  > "This left us 63 sources with 2 of them serendipitously detected in previous band-7 continuum observations with ALMA." (Methods 1.1); distance from EAzY photometric redshifts; VLT/X-SHOOTER Lyα  
  > "This left us 63 sources with 2 of them serendipitously detected in previous band-7 continuum observations with ALMA." (Methods 1.1)

## Data provenance

- ALMA projects: 2015.1.01495.S, 2013.1.01292.S
- bands: Band 7 (870 µm) continuum  
  > "Our ALMA band-7 con tinuum observations of H-dropouts are performed during January and July 2016." (Methods 1.3)
- frequencies and spectral setup: central frequency 343.5 GHz  
  > "a spectral setup placed around a central frequency of 343.5 GHz" (Methods 1.3)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: COSMOS 0.6x1"; other two fields 0.2-0.3", tapered to 0.6"  
  > "only the CANDLES-COSMOS field was observed as requested, yielding a synthesis beam of 0.6 × 1 [′′] . The other two fields were observed at 0.2-0.3 [′′] resolution." (Methods 1.3)
- max recoverable scale: _not stated_
- sensitivity: detection limit 0.6 mJy (4σ)  
  > "are detected down to an integrated flux of 0.6 mJy (4σ" (abstract)
- time on source: ~1.8 min per object, ~2 h total  
  > "The integration time is roughly 1.8 mins per object with a total observing time of ∼2 h." (Methods 1.3)
- observing dates: January and July 2016  
  > "Our ALMA band-7 con tinuum observations of H-dropouts are performed during January and July 2016." (Methods 1.3)
- pi or archival as stated: _not stated_
- Other facility **HST/CANDELS**: F160W H-band selection and photometry  
  > "We have crossmatched the F160W-selected catalog from the three CANDELS fields" (Methods 1.1)
- Other facility **Spitzer/IRAC SEDS**: 4.5 µm selected parent catalog  
  > "IRAC 3.6 and 4.5 µm selected catalog [31] from the SEDS survey" (Methods 1.1)
- Other facility **VLT/X-SHOOTER**: Lyα spectroscopic redshifts for two sources  
  > "We thus followed up these objects with VLT/X-SHOOTER to confirm the presence of an emission line." (Methods 1.5)
- Other facility **JCMT/SCUBA-2**: 450 and 850 µm fluxes in COSMOS  
  > "is covered by deep SCUBA-2 450 µm and 870 µm observations from the STUDIES survey" (Methods 1.4)
- Other facility **VLA 3 GHz**: radio fluxes in COSMOS  
  > "The VLA 3 GHz observation in COSMOS [60] reaches a" (Methods 1.4)
- External data: ZFOURGE catalogs used for LBG comparison sample  
  > "we have selected LBGs using the ZFOURGE catalogs in the same three CANDELS fields [22]" (Methods 1.6) [from Straatman et al. 2016 (cite: 22)]
- External data: UV luminosity functions for massive LBG SFRD  
  > "we utilized the latest determination of the UV luminosity function at z ∼ 4 − 6 [25]" (Methods 1.6) [from Ono et al. 2018 (cite: 25)]
- External data: Previous ALMA program detecting two H-dropouts serendipitously  
  > "including two galaxies that were serendipitously detected in a previous ALMA program [54]" (Methods 1.3) [from Schreiber et al. 2016 (cite: 54)]
- Simulation/model as data: Semi-analytical model mock catalog (Henriques et al. 2015) and Illustris mock fields compared with observed H-dropout densities  
  > "the SFR density from H-dropouts ([4.5] < 24 and H − [4.5] > 2.5) in semi-analytical models [19]" (Figure 3 caption)

## Processing

### Calibration

- pipeline or manual: CASA pipeline  
  > "We reduced the data using the CASA pipeline (version 4.3.1)." (Methods 1.3)
- casa version: CASA 4.3.1  
  > "We reduced the data using the CASA pipeline (version 4.3.1)." (Methods 1.3)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: uvmodelfit in the (u,v) plane for total flux  
  > "We measured the total flux of all our targets directly in the ( u, v ) plane using the uvmodelfit procedure from the CASA pipeline." (Methods 1.3)
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: tapered to 0.6" for the two high-resolution fields  
  > "we tapered the baselines for these two fields to an angular resolution of 0.6 [′′] ." (Methods 1.3)
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- LBG selection criteria  
  > "We select our z = 4 − 6 LBG galaxy sample using the selection criterion in [64] ." (Methods 1.6) [from Bouwens et al. 2015 (cite: 64)]
- Photometry procedure follows earlier deep surveys  
  > "The photometry was obtained with a procedure very similar to that previously used in deep surveys [22,46]" (Methods 1.2) [from (cite: 22, 46)]
- Dust-corrected SFR for UV-selected LBGs  
  > "We then derive the dust-corrected SFR for these brightest UV-selected galaxies following the approach in ref. [17] ." (Methods 1.6) [from Bouwens et al. 2012 (cite: 17)]

### Not stated but needed to reproduce (our reading)

- Image size, cell size, weighting/robust and cleaning parameters for ALMA continuum
- uvmodelfit starting parameters and S/N definition
- Flux calibrators and ALMA flux scale uncertainty
- Details of the stacking and uv-taper implementation
- Cosmological volume and effective-volume computation for space density
- Priors for EAzY/FAST beyond what is described

## Analysis recipe

1. **Select H-dropouts**: Crossmatch SEDS IRAC [4.5]<24 sources with F160W catalog, require no H-band counterpart within 2" radius, visual inspection  
  > "identified those without H-band counterparts within a 2” radius (corresponding roughly to the PSF size of IRAC 3.6 and 4.5 µm)" (Methods 1.1)
   - fitting: _not stated_
   - validation: Compared with blind ALMA survey in GOODS-S (completeness ~57% vs estimated 53%)  
  > "this implies a completeness of our searching approach of ∼ 57%, consistent with our estimated value." (Methods 1.1)
2. **Measure ALMA 870 µm fluxes**: Tapered baselines to 0.6"; fit circular Gaussian in uv plane with uvmodelfit; detection at S/N>4  
  > "The sources were modeled with a circular Gaussian profile of variable total flux, centroid, width, axis ratio and position angle." (Methods 1.3)
   - software: CASA
   - fitting: uvmodelfit Gaussian  
  > "using the uvmodelfit procedure from the CASA pipeline. The sources were modeled with a circular Gaussian profile of variable total flux, centroid, width, axis ratio and position angle." (Methods 1.3 ALMA observation and data reduction)
   - validation: ALMA/SCUBA-2 870 µm median flux ratio 1.05  
  > "yields excellent agreement with a median value of S ALMA / S SCUBA−2 = 1.05." (Methods 1.4)
3. **Photometric redshifts and stellar masses**: EAzY redshifts with full templates, then FAST with delayed-exponential SFH, Calzetti attenuation, solar metallicity, with L_IR constraint from ALMA; 200 Monte Carlo realizations for errors  
  > "photometric redshifts were computed with EAzY [65] using the full set of template SEDs" (Methods 2.2)
   - software: EAzY, FAST
   - parameter: A_V up to 6 mag  
  > "allowing A V up to 6 magnitudes" (Methods 2.2)
   - assumption: Chabrier IMF; T_dust = 36.7 K with 5 K scatter  
  > "the dust temperature was drawn from a Gaussian distribution centered on 36.7 K and with a width of 5 K" (Methods 2.2)
   - fitting: chi2 minimization with extra L_IR term  
  > "The observed infrared luminosity was then compared to the modeled value, which we computed as the difference of bolometric luminosity before after applying dust attenuation." (Methods 2.2 Photometric redshift and stellar mass determination)
   - validation: Spec-z vs photo-z scatter ~0.1  
  > "σ ∆ z /(1+ z spec ) ∼ 0.1." (main text)
4. **Stacked IR SED and L_IR/SFR**: Median stacking of 24 µm to ALMA 870 µm images of 39 detected sources; fit with empirical IR SED library  
  > "The stacked IR SED is derived by median stacking of the Spitzer/24µm, Herschel/100µm, 160µm, 250µm, 350µm, 500µm, and ALMA 870µm images" (Extended Data Fig. 3)
   - assumption: Intrinsic IR SED of each ALMA-detected H-dropout equals stacked SED  
  > "assuming their intrinsic far-infrared SED resembles that of the stacked one." (Figure 2 caption)
   - fitting: _not stated_
   - validation: _not stated_
5. **SFR density and mass function with incompleteness correction**: Sum SFRs over volume with correction factor 2-2.4 from HST chance superposition and IRAC incompleteness; compare with LBGs from ZFOURGE  
  > "a factor of 2 to 2.4 has been applied to the number density" (Methods 1.1)
   - fitting: _not stated_
   - validation: _not stated_
6. **Clustering and halo mass**: Angular cross-correlation with H-detected 3.5<z<5.5 galaxies (Landy-Szalay), power-law fit with β fixed to 0.8 and integral constraint, Limber to r0, then bias and halo mass  
  > "β is the power-law index fixed to 0.8 and IC is the integral constraint." (Methods 2.3)
   - fitting: power law fit to CCF at >10" scales  
  > "We then fit the derived CCF with a power-law model:" (Methods 2.3 Clustering measurements)
   - validation: _not stated_

## Software

- **CASA** 4.3.1: pipeline reduction and uvmodelfit  
  > "We reduced the data using the CASA pipeline (version 4.3.1)." (Methods 1.3)
- **EAzY** : photometric redshifts  
  > "photometric redshifts were computed with EAzY [65]" (Methods 2.2)
- **FAST** : stellar masses  
  > "we then ran FAST [66] to estimate the stellar masses" (Methods 2.2)
- **FASTPHOT** : prior-based PSF-fitting SCUBA-2 flux extraction  
  > "with the prior-based PSF-fitting code FASTPHOT [59]" (Methods 1.4)
- **CIGALE** : full SED fits to stacked SEDs  
  > "best-fit SED templates obtained with the SED-fitting tool Cigale [75]" (Extended Data Fig. 5)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| ALMA detections among H-dropouts | 39 of 63 | not stated | sources | 2 | submillimeter (wavelength 870 µ m) detections of 39 massive star-forming galaxies |
| Median 870 µm flux | 1.6 | not stated | mJy | 2 | with a median of S 870 µ m =1.6 mJy |
| Stacked L_IR | 2.2e12 | 0.3e12 | L_sun | 4 | L IR = 2.2 ± 0.3 × 10 [12] L ⊙ |
| Mean dust temperature | 36.7 | 2.1 | K | 4 | T dust = 36.7 ± 2.1 K |
| Stacked flux of ALMA-undetected | 0.24 | 0.04 | mJy | 2 | 0.24 ± 0.04 mJy |
| SFR density of ALMA-detected H-dropouts, average over z=4-6 | 1.6e-3 | not stated | M_sun/yr/Mpc^3 | 5 | approximately 1.6×10 [−][3] M ⊙ yr [−][1] Mpc [−][3] when averaged over the three bins |
| Galaxy bias | 8.4 | 1.5 | dimensionless | 6 | b = 8.4 ± 1.5 |
| Halo mass at z=4 | 10^(13±0.3) | 0.3 dex | h^-1 M_sun | 6 | M h ∼ 10 [13][±][0][.][3] h [−][1] M ⊙ at z = 4 |
| Number density | ~2e-5 | not stated | Mpc^-3 | 5 | Their number density, n ∼ 2 × 10 [−][5] |

## Qualitative findings

- At M*≳10^10.5 Msun H-dropouts outnumber LBGs, and including red H-detected galaxies they make >80% of the most massive galaxies at z>4.  
  > "they make up more than than 80% of the most massive galaxies at z - 4." (main text)

## Claim tuples

- H: H-dropouts are massive dusty star-forming galaxies at z>3 | E: ALMA 870 µm detections, photo-z, SCUBA-2/VLA colors, X-SHOOTER | R: 62% detected, median z=4, two Lyα spec-z confirmed | F: Most H-dropouts are massive, dusty z>3 galaxies with SFR ~200 Msun/yr | **supported**
- H: H-dropouts dominate the SFR density among massive galaxies at z>3 | E: Compare SFRD and mass function to massive LBGs | R: One to two orders higher than massive LBGs; ~10% of total LBG SFRD | F: Majority of the most massive galaxies are missed by LBG selection | **supported**
- H: H-dropouts reside in massive halos | E: Cross-correlation with H-detected galaxies | R: b=8.4±1.5, Mh~10^13 h^-1 Msun | F: Likely progenitors of massive ellipticals in groups and clusters | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Cross-correlation with a larger population used because the H-dropout sample is small.  
  > "Since the number of H-dropouts is small, we calculate two-point angular cross-correlation function (CCF) with a much larger population" (Methods 2.3)
- How they decided it was enough: _not stated_
- Limitation (authors): Redshifts of individual galaxies carry large uncertainty.  
  > "whereas the estimated redshifts for individual galaxies exhibit a large uncertainty" (main text)
- Caveat (inferred, ours): Mostly photometric redshifts; only two spec-z
- Caveat (inferred, ours): Stacked SED assumed for all individual SFRs
- Caveat (inferred, ours): Large completeness correction (factor 2-2.4)
- Caveat (inferred, ours): Clustering based on few sources with fixed power-law slope

## Reproducibility

- Data public (paper): ALMA data in archive; HST and Spitzer public  
  > "Source data for the ALMA 870 µ m imaging are available through the ALMA archive." (Data availability)
- Products in archive: _not stated_
- Code: SED modeling and stacking codes on github.com/cschreib  
  > "The codes used to model the optical-to-infrared SEDs, and to stack the optical and infrared images are accessible through github" (Code availability)
- Missing: ALMA imaging parameters
- Missing: Measured photometric catalog (on request)
- Missing: Volume/completeness details for SFRD
- Data volume (inferred): ~50-150 GB raw for two ALMA projects plus public multiwavelength imaging
- Score (inferred): 3/5, Public ALMA and multiwavelength data, but a Nature-letter-style recipe omits many parameters; catalogs partly on request.
- Rediscovery candidate: no, Requires extensive multiwavelength photometry and SED pipeline beyond ALMA; recipe incomplete.

## Links

- Method: Schreiber et al. 2018 (cite: 13) (Empirical IR SED library used for stacked SED fits)
- Companion: Franco et al. 2018 (cite: 32) (Blind GOODS-ALMA survey used to check completeness)
- Companion: Yamaguchi et al. 2019 (cite: 33) (ASAGAO near-IR-dark sources comparison)
- Related: CANDELS
- Related: SEDS
- Related: ZFOURGE
- Related: 3D-HST
- Related: STUDIES

## Checks

```json
{
 "quotes": 66,
 "quotes_ok": 66,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 9,
 "numeric_problems": 0,
 "fill": {
  "facts": 84,
  "stated": 51,
  "rate": 0.607
 },
 "evidence_ok": true
}
```
