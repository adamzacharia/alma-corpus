# An Intensely Star-forming Galaxy at z ~ 7 with Low Dust and Metal Content Revealed by Deep ALMA and HST Observations

`2013ApJ...778..102O` | The Astrophysical Journal 2013 | first author: Ouchi, Masami | arXiv: 1306.3572 | DOI: 10.1088/0004-637X/778/2/102

Card schema 1.0 | model gemini-3.8-flash | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies
- Question: To measure dust continuum emission and the [C II] 158 um line in the luminous z=6.595 galaxy Himiko to constrain its dust content, obscured star formation, and ISM metallicity.  
  > "We seek to use the cold dust continuum and [C II] measures from ALMA to understand its dust content and gas phase metallicity." (Introduction); "To understand whether obscured star-formation is an important issue as well as the metallicity of Himiko, a key source at high redshift, we carried out deep ALMA Band 6 observations" (2.1 ALMA)
- Target **Himiko**: coordinates _not stated_; z/distance z = 6.595  
  > "‘Himiko’, at a redshift z=6.595." (abstract); "Total x(pix)=2815.4, y(pix)=2790.4" (Table 2); "Ouchi et al. (2009a) reported the discovery of the star-forming galaxy at z=6.595, ’Himiko’" (1 Introduction); distance from Ouchi et al. (2009a)  
  > "‘Himiko’, at a redshift z=6.595." (abstract); "Total x(pix)=2815.4, y(pix)=2790.4" (Table 2); "Ouchi et al. (2009a) reported the discovery of the star-forming galaxy at z=6.595, ’Himiko’" (1 Introduction)

## Data provenance

- ALMA projects: 2011.0.00115.S
- bands: Band 6  
  > "we carried out deep ALMA Band 6 observations in 2012 July 15, 18, 28, and 31" (2.1 ALMA)
- frequencies and spectral setup: 4 spectral windows: central frequencies 250.24 and 252.11 GHz in LSB, and 265.90 and 267.78 GHz in USB, each with bandwidth 1875 MHz; [CII] targeted at 250.24 GHz  
  > "set the central frequency of the 4 spectral windows are 250.24 and 252.11 GHz in LSB, and 265.90 and 267.78 GHz in USB with a bandwidth of 1875 MHz." (2.1 ALMA)
- continuum bandwidth: total bandwidth 19.417 GHz (sum of 4 spectral windows; 7.5 GHz sampled)  
  > "over the the total bandwidth of 19.417 GHz whose 7.5 GHz is sampled." (2.1 ALMA); "The continuum sensitivity is given in the total bandwidth for the continuum measurement is 19.417 GHz or 86.894 um that is a sum of 4 spectral windows (see text)." (Table 1)
- arrays: 16 12m-antenna array  
  > "with 16 12m-antenna array under the the extended configuration of 36-400m baseline." (2.1 ALMA)
- configurations: _not stated_
- baselines: 36-400m  
  > "under the the extended configuration of 36-400m baseline." (2.1 ALMA)
- angular resolution: 0''.82 x 0''.58  
  > "The FWHM beam size of the final image is 0''.82 x 0''.58 with a position angle of 79 deg .5." (2.1 ALMA)
- max recoverable scale: _not stated_
- sensitivity: sigma_cont = 17.4 uJy beam^-1; sigma_line = 83.3 uJy beam^-1 (200 km s^-1 channel)  
  > "The 1sigma noise of continuum image is sigma_cont=17.4 uJy beam^-1 over the the total bandwidth of 19.417 GHz whose 7.5 GHz is sampled. The 1sigma noise of line image is sigma_line=83.3 uJy beam^-1 at 250.239 GHz over a channel width of 200 km s^-1." (2.1 ALMA)
- time on source: 3.17 hours  
  > "The total on-source integration time was 3.17 hours." (2.1 ALMA)
- observing dates: 2012 July 15, 18, 28, and 31  
  > "carried out deep ALMA Band 6 observations in 2012 July 15, 18, 28, and 31" (2.1 ALMA)
- pi or archival as stated: _not stated_
- Line: C II [C II] 158 um (^2P_3/2 -> ^2P_1/2) (1900.54 GHz)
- Other facility **HST (WFC3-IR)**: Deep broad-band (J125, H160) and medium-band (F098M) imaging of Himiko  
  > "We carried out deep HST/WFC3-IR broad-band (J125 and H160) and medium-band (F098M) observations for Himiko." (2.2 HST)
- Other facility **Spitzer (IRAC)**: SEDS imaging at 3.6 um and 4.5 um and SpUDS photometry at 5.8 um, 8.0 um, and 24 um  
  > "we use the very deep Spitzer/IRAC SEDS data reaching 26 mag at the 3sigma level (Ashby et al. 2013) to investigate the counterpart of the overall Himiko system at 3.6um and 4.5um bands." (2.3 Spitzer)
- Other facility **Subaru**: Optical/narrowband NB921 imaging discovering the extended Ly-alpha nebula  
  > "This source was identified from an extensive 1 deg^2 optical survey for z=6.6 galaxies in the UKIDSS/UDS field conducted with the Subaru telescope." (1 Introduction)
- Other facility **UKIDSS**: J, H, K DR8 photometric data from the UKIDSS/UDS survey  
  > "Our near-IR SED is taken using total magnitudes from the HST images (§2.2), the Spitzer/IRAC SEDS images (§2.3) and JHK DR8 data from the UKIDSS/UDS survey." (3.3 Improved Physical Properties from the Near-Infrared SED)
- External data: Optical B, V, R, i', z', NB921 magnitudes and Spitzer/SpUDS 5.8, 8.0, 24 um photometry  
  > "Measurements obtained in Ouchi et al. (2009a)." (Table 3) [from (cite: ouchi2009a)]
- External data: UKIDSS/UDS DR8 J, H, K aperture photometry  
  > "Total magnitudes from UKIDSS/UDS DR8 data that are estimated with a 2'' diameter aperture photometry and the aperture correction in the same manner as Ono et al. (2010b)." (Table 3) [from (cite: ono2010b)]

## Processing

### Calibration

- pipeline or manual: manual  
  > "Our data were reduced with Common Astronomy Software Applications (CASA) package." (2.1 ALMA)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Neptune and Callisto  
  > "The absolute flux scale was established by observations of Neptune and Callisto." (2.1 ALMA)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0''.82 x 0''.58, PA 79.5 deg  
  > "The FWHM beam size of the final image is 0''.82 x 0''.58 with a position angle of 79 deg .5." (2.1 ALMA)
- final rms: 17.4 uJy beam^-1 (continuum); 83.3 uJy beam^-1 (line, 200 km s^-1 channel)  
  > "The 1sigma noise of continuum image is sigma_cont=17.4 uJy beam^-1 over the the total bandwidth of 19.417 GHz whose 7.5 GHz is sampled. The 1sigma noise of line image is sigma_line=83.3 uJy beam^-1 at 250.239 GHz over a channel width of 200 km s^-1." (2.1 ALMA)

### Inherited from earlier work

- SED fitting procedure with Bruzual & Charlot models and nebular emission prescription  
  > "undertake chi^2 fitting of a range of stellar synthesis models in the same manner as Ono et al. (2010b) using the stellar synthesis models of Bruzual & Charlot (2003) with dust attenuation formulate given by Calzetti et al. (2000)." (3.3 Improved Physical Properties from the Near-Infrared SED) [from (cite: ono2010b)]
- Aperture correction for Spitzer/IRAC 3-arcsec photometry  
  > "We obtain total magnitudes of Spitzer/IRAC images from a 3''-diameter aperture and use an aperture correction given in Yan et al. (2005)." (2.3 Spitzer) [from (cite: yan2005)]

### Not stated but needed to reproduce (our reading)

- tclean/clean deconvolver, robust/weighting parameter, and cell size used in CASA imaging
- Channels or exact frequency ranges flagged/excluded for continuum averaging
- Self-calibration details if any were attempted

## Analysis recipe

1. **Process and image ALMA continuum and spectral line data**: Calibrated data reduced in CASA; continuum imaged across line-free ranges in LSB and USB (249.30-253.05 GHz and 264.96-268.71 GHz); spectral cube rebinned to 166 MHz (200 km s^-1) channels.  
  > "We rebin our data to a resolution of 166 MHz (200 km s^-1)... We averaged fluxes over the two spectral windows of LSB (249.30-253.05 GHz or 1.203-1.185mm) and USB (264.96-268.71 GHz or 1.131-1.116mm) in the range of frequency free from the [C II] line." (2.1 ALMA)
   - software: CASA
   - parameter: Rebinned resolution: 166 MHz (200 km s^-1); continuum effective frequency: 259.01 GHz  
  > "We rebin our data to a resolution of 166 MHz (200 km s^-1)... Figure 1 presents the resulting ALMA continuum data at 259.01 GHz in frequency (or 1.167mm in wavelength) with a 1sigma sensitivity of 17.4uJy beam^-1." (2.1 ALMA)
   - assumption: _not stated_
   - fitting: _not stated_
   - validation: Compared apparent 2-sigma peak at target position with surrounding negative noise peaks at 2-3 sigma level to establish non-detection.  
  > "There is a ~ 2sigma flux peak in the beam size on the position of Himiko. However, there are a series of negative pixels nearby that correspond to the 2-3 sigma level per beam. We conclude therefore that Himiko remains undetected" (2.1 ALMA)
2. **Derive FIR continuum luminosity upper limit**: Derived 3-sigma upper limit on L_FIR by integrating an optically thin graybody modified blackbody model from 8 to 1000 um.  
  > "Assuming an optically thin graybody of modified blackbody radiation with a dust emissivity power-law spectral index of beta_d=1.5 and a dust temperature of T_d=40K (Eales et al. 1989; Klaas et al. 1997), we obtain a 3sigma upper limit of L_FIR < 8.0 x 10^10 L_odot integrated over 8-1000um." (3.1 Far Infrared SED)
   - parameter: beta_d = 1.5, T_d = 40 K (also explored T_d = 20-60 K, beta_d = 0-2)  
  > "Assuming an optically thin graybody of modified blackbody radiation with a dust emissivity power-law spectral index of beta_d=1.5 and a dust temperature of T_d=40K" (3.1 Far Infrared SED)
   - assumption: Optically thin dust emission; local thermal equilibrium between ISM and CMB at z=6.595 imposes T_d >= 21 K.  
  > "Assuming local thermal equilibrium between ISM of Himiko and CMB at z=6.595 (da Cunha et al. 2013), this yields a lower limit of T_d=21 K." (3.1 Far Infrared SED)
   - fitting: _not stated_
   - validation: Checked sensitivity to alternative T_d (25 K, 60 K) and beta_d (0, 2) values.  
  > "For T_d=25K and T_d=60K, the 3sigma upper limit luminosities in 8-1000um are <2.7 x 10^10 and <3.0 x 10^11 L_odot, respectively. Similarly, for beta_d=0 and beta_d=2, the 3sigma upper limit luminosities in 8-1000um are <3.5 x 10^10 and <1.2 x 10^11 L_odot" (3.1 Far Infrared SED)
3. **Constrain [C II] line luminosity and compare with local SFR scaling relations**: Searched velocity channels within +-600 km s^-1 around z_Lya=6.595; derived 3-sigma line flux and luminosity upper limit and compared to De Looze et al. (2011) relation.  
  > "The corresponding 3sigma upper limit for [C II] is 250.0 uJy in a channel width of 200 km s^-1. The associated luminosity limit is <5.4 x 10^7 L_odot." (2.1 ALMA); "Himiko clearly departs significantly from the scaling relation; the deficit amounts to a factor ~ x30." (3.2 ISM metallicity from [C II] Emission)
   - parameter: Channel width 200 km s^-1; search velocity window +-600 km s^-1  
  > "We searched for a signal of [C II] over 600 km s^-1 around the frequency corresponding to z_Lya=6.595." (2.1 ALMA)
   - assumption: Line width of 200 km s^-1 for 3-sigma flux limit determination  
  > "The line sensitivity is defined with a channel width of 200 km s^-1." (Table 1)
   - fitting: _not stated_
   - validation: Verified non-detection across velocity range and identified that ~3 sigma peaks slightly offset from optical center are noise peaks.  
  > "there are noise peaks barely reaching at the 3sigma level in 0 km s^-1 and -200 km s^-1 that are slightly north and south of the Himiko’s optical center position, respectively. However, neither of these sources is a reliable counterpart of Himiko." (2.1 ALMA)
4. **SED fitting with stellar synthesis models to determine physical properties**: chi^2 fitting of Bruzual & Charlot (2003) models with Calzetti dust attenuation, Salpeter IMF, constant and exponentially decaying SFH, with and without nebular emission.  
  > "undertake chi^2 fitting of a range of stellar synthesis models in the same manner as Ono et al. (2010b) using the stellar synthesis models of Bruzual & Charlot (2003) with dust attenuation formulate given by Calzetti et al. (2000)." (3.3 Improved Physical Properties from the Near-Infrared SED)
   - parameter: IMF: Salpeter (0.1-100 M_sun); metallicity: Z=0.02-1.0 Z_sun; E(B-V)=0-1; age=1-810 Myr  
  > "We adopt Salpeter initial mass function (IMF; Salpeter 1955) with lower and upper mass cutoffs of 0.1 and 100 M_odot, respectively. Applying models of constant and exponentially-decaying star-formation histories with metallicities ranging from Z=0.02-1.0Z_odot, we search for the best-fit model in a parameter space of E(B-V)=0-1 and age=1-810 Myr" (3.3 Improved Physical Properties from the Near-Infrared SED)
   - assumption: Salpeter IMF; Calzetti dust attenuation law; f_esc = 0 for ionizing photons in stellar+nebular model.  
  > "In the stellar+nebular models, we assume that all ionizing photons lead to nebular emission lines corresponding to an escape fraction f_esc=0." (3.3 Improved Physical Properties from the Near-Infrared SED)
   - fitting: Grid chi^2 minimization over E(B-V), age, and metallicity.  
  > "we search for the best-fit model in a parameter space of E(B-V)=0-1 and age=1-810 Myr" (3.3 Improved Physical Properties from the Near-Infrared SED); "The uncertainty of color excess is smaller than our model-parameter grid of Delta E(B-V)=0.01." (Table 4)
   - validation: Compared reduced chi^2 between pure stellar (chi^2/dof = 3.13) and stellar+nebular (chi^2/dof = 1.55) models.  
  > "Adding nebular emission to the stellar SED models given above, the best fit has a more satisfactory reduced chi^2, 1.6" (3.3 Improved Physical Properties from the Near-Infrared SED)

## Software

- **CASA** : ALMA data reduction and imaging  
  > "Our data were reduced with Common Astronomy Software Applications (CASA) package." (2.1 ALMA)
- **MULTIDRIZZLE** : HST/WFC3 image reduction and drizzling  
  > "The various WFC3 images were reduced with WFC3 and MULTIDRIZZLE packages on PyRAF." (2.2 HST)
- **PyRAF** : Running HST data reduction packages  
  > "The various WFC3 images were reduced with WFC3 and MULTIDRIZZLE packages on PyRAF." (2.2 HST)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| ALMA 1.2mm continuum 1-sigma rms sensitivity | 17.4 | not stated | uJy beam^-1 | 1 | 259.007 GHz: sigma_cont = 17.4 uJy beam^-1 |
| ALMA 1.2mm continuum 3-sigma upper limit | 52.1 | not stated | uJy | 1 | f_cont < 52.1 uJy |
| ALMA [C II] line 1-sigma rms sensitivity | 83.3 | not stated | uJy beam^-1 | 1 | 250.239 GHz: sigma_line = 83.3 uJy beam^-1 |
| ALMA [C II] line flux 3-sigma upper limit | 250.0 | not stated | uJy | 1 | f_line < 250.0 uJy |
| FIR continuum luminosity (8-1000 um) 3-sigma upper limit | 8.0 | not stated | 10^10 L_odot | 2 | L_FIR < 8.0 x 10^10 L_odot |
| [C II] line luminosity 3-sigma upper limit | 5.4 | not stated | 10^7 L_odot | 3 | L_[CII] < 5.4 x 10^7 L_odot |
| Stellar mass (stellar+nebular model) | 1.5e10 | +0.2e10/-0.2e10 | M_odot | 4 | stellar+nebular: M_* = 1.5^+0.2_-0.2 x 10^10 M_odot |
| Star formation rate (stellar+nebular model) | 100 | 2 | M_odot yr^-1 | 4 | stellar+nebular: SFR = 100 +- 2 M_odot yr^-1 |
| Dust extinction E(B-V)_* | 0.15 | not stated | mag | 4 | E(B-V)_* = 0.15 |
| Stellar age (stellar+nebular model) | 182 | +22/-20 | Myr | 4 | stellar+nebular: Age = 182^+22_-20 Myr |
| Specific star formation rate sSFR (stellar+nebular model) | 6.7e-9 | 0.9e-9 | yr^-1 | 4 | sSFR = 6.7 +- 0.9 x 10^-9 yr^-1 |
| UV-continuum slope beta for Clump A | -2.84 | 0.32 | dimensionless | 0 | A(clump): beta = -2.84 +- 0.32 |
| UV-continuum slope beta for Total Himiko | -2.00 | 0.57 | dimensionless | 0 | Total: beta = -2.00 +- 0.57 |

## Qualitative findings

- Himiko is undetected in 1.2 mm dust continuum (<52 uJy) and [C II] 158 um emission (<250 uJy), indicating dust-poor and metal-poor interstellar gas.  
  > "Both aspects of our ALMA observations suggest Himiko is an unique object with a very low dust content and perhaps nearly primordial interstellar gas." (abstract)
- Himiko falls below the local [C II]-SFR relation by a factor of >30, implying gas-phase metallicity <= 0.03 Z_sun.  
  > "our observations indicate Himiko lies off the local L_[CII] - star formation rate scaling relation by a factor of more than 30." (abstract); "De Looze (2012) has argued that offsets from the [C II]-SFR relation can be explained in terms of metal abundance and this would imply a gas-phase metallicity of <~ 0.03Z_odot." (4.1 The Low Dust and Metal Content of Himiko)
- HST imaging reveals Himiko consists of three distinct L* clumps undergoing a triple major merger.  
  > "Himiko is undergoing a triple major merger event whose extensive ionized nebula of Lyman alpha emitting gas, discovered in our earlier work with Subaru, is powered by star formation and the dense circum-galactic gas." (abstract)

## Claim tuples

- H: Himiko contains cold dust emission and significant obscured star formation traceable by ALMA 1.2 mm continuum. | E: Conducted deep ALMA Band 6 continuum imaging targeting 1.2 mm (259 GHz) with 17.4 uJy beam^-1 rms sensitivity. | R: No dust continuum detected, placing a 3-sigma upper limit of <52.1 uJy (L_FIR < 8.0 x 10^10 L_sun). | F: Himiko has very low dust content, with SFR(FIR) < 14 M_sun yr^-1, ruling out substantial obscured star formation. | **refuted**
- H: The [C II] 158 um line traces star formation in Himiko following the local [C II]-SFR scaling relation. | E: Targeted redshifted [C II] at 250.24 GHz with ALMA Band 6 down to 83.3 uJy beam^-1 per 200 km s^-1 channel. | R: No line detected; 3-sigma upper limit L_[CII] < 5.4 x 10^7 L_sun. | F: Himiko departs from the local [C II]-SFR relation by a factor of >30, indicating very low metallicity (<=0.03 Z_sun) and/or high PDR density. | **refuted**
- H: Himiko's extensive Ly-alpha halo and extreme star formation are caused by gravitational lensing or an active galactic nucleus. | E: Examined high-resolution HST/WFC3 imaging, deep Spitzer/IRAC imaging, X-ray limits, and existing Keck spectroscopy. | R: HST resolves three distinct L* clumps with asymmetric properties; no foreground lens, no X-ray detection, and no high-ionization emission lines. | F: Gravitational lensing and AGN excitation are ruled out; Himiko is an unlensed triple major merger powered by starburst photoionization. | **refuted**

## Reasoning

- Why this data: ALMA Band 6 reaches an order of magnitude deeper than previous IRAM observations, capable of detecting dust continuum and [C II] 158 um to test for obscured star formation and metallicity.  
  > "Our ALMA observations probe an order of magnitude deeper than previous IRAM observations, yet fail to detect a 1.2mm dust continuum" (abstract)
- Why this method: Combining ALMA with HST WFC3 and Spitzer SEDS allows simultaneous morphological deconstruction into subcomponents and multi-wavelength SED modeling.  
  > "The present paper is concerned with the analysis of uniquely deep ALMA and HST observations of this remarkable source." (1 Introduction)
- Alternative: Considered and rejected gravitational lensing, central AGN heating, single virialized galaxy with HII clumps, and strong shock-driven outflows as explanations for Himiko.  
  > "we conclude that Himiko is not a gravitational lensed system... we conclude the Lya halo is unlikely to be heated by an active galactic nucleus... we consider that Himiko is unlikely to be a single virialized system" (4.2 Nature of Himiko)
- How they decided it was enough: _not stated_
- Limitation (authors): Far-infrared luminosity and dust mass upper limits depend strongly on assumed dust temperature T_d and emissivity index beta_d.  
  > "Note that these upper limits depend upon the assumed dust temperature and beta_d. For T_d=25K and T_d=60K, the 3sigma upper limit luminosities in 8-1000um are <2.7 x 10^10 and <3.0 x 10^11 L_odot, respectively." (3.1 Far Infrared SED)
- Limitation (authors): HST F098M detects only marginal extended Ly-alpha emission due to the shallower surface brightness limit of HST compared to Subaru.  
  > "The F098M image in Figure 4 detects only marginal extended Lya emission, because of the shallower surface brightness limit of the 2.4m HST compared to the 8m Subaru telescope." (2.2 HST)
- Caveat (inferred, ours): The severe deficit in [C II] emission relative to SFR could alternatively be caused by [C II] deficit at high FIR surface brightness or collisional de-excitation in high-density PDRs rather than solely low metallicity.
- Caveat (inferred, ours): Derivation of SFR from UV/optical SED fitting is sensitive to assumptions about SFH and nebular line contributions.

## Reproducibility

- Data public (paper): ALMA data are identified by project code 2011.0.00115.S and HST data by program #12265.  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2011.0.00115.S... These observations are associated with program #12265." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Exact CASA imaging clean parameters (weighting scheme, robust parameter, multiscale settings if any, pixel cell size)
- Missing: Exact list of channel ranges used for continuum subtraction/averaging
- Data volume (inferred): 10 - 50 GB
- Score (inferred): 75/5, The paper provides clear project codes, observing details, sensitivities, upper limits, and SED modeling assumptions. However, imaging parameters (weighting/robust, pixel cell size) in CASA and details of the SED fitting software scripts are not completely documented.
- Rediscovery candidate: yes, Public ALMA Early Science data (2011.0.00115.S) with clear null detection result (<52.1 uJy continuum, <250 uJy line) that is straightforward to re-image and verify.

## Links

- Method: (cite: ono2010b) (Describes the SED fitting methodology with stellar synthesis and nebular emission models)
- Method: (cite: bruzual2003) (Stellar population synthesis models used for SED fitting)
- Method: (cite: calzetti2000) (Dust attenuation law adopted for SED modeling)
- Companion: (cite: ouchi2009a) (Discovery paper of Himiko containing earlier optical, Subaru, Keck, and IRAM observations)
- Related: UKIDSS/UDS
- Related: SEDS
- Related: SpUDS

## Checks

```json
{
 "quotes": 80,
 "quotes_ok": 34,
 "quote_pass_rate": 0.425,
 "quotes_too_long": 8,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 13,
 "numeric_problems": 0,
 "fill": {
  "facts": 80,
  "stated": 52,
  "rate": 0.65
 },
 "evidence_ok": false
}
```
