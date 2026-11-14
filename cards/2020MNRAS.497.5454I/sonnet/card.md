# Multiwavelength investigation of extended green object G19.88-0.53: revealing a protocluster

`2020MNRAS.497.5454I` | Monthly Notices of the Royal Astronomical Society 2020 | first author: Issac, Namitha | arXiv: 2007.15186 | DOI: 10.1093/mnras/staa2301

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type multi_facility_alma_minor

## Science

- Fields: star_formation, milky_way_ism
- Question: What is the nature of star formation in the EGO G19.88-0.53: a single MYSO or a protocluster, and what are the jet, core and outflow properties  
  > "G19.88-0.53 unveils as harbouring a protocluster rather than a single massive young stellar object." (abstract)
- Target **G19.88-0.53 (IRAS 18264-1152)**: coordinates _not stated_; z/distance 3.31 kpc  
  > "it is placed at the near distance of 3.31 kpc" (1 INTRODUCTION); distance from Roman-Duval et al. 2009; Ge et al. 2014 (kinematic, near distance)  
  > "it is placed at the near distance of 3.31 kpc" (1 INTRODUCTION)

## Data provenance

- ALMA projects: 2017.1.00377.S
- bands: Band 3 (2.7 mm) and Band 7 (870 um)  
  > "ALMA) archival data at 2.7 mm (Band 3) and 870 $\mu m$ (Band 7) are used" (2.5 Atacama Large Millimeter Array archival data)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: 12-m array (high and medium resolution) and 7-m ACA (low resolution)  
  > "The high- and medium-resolution ALMA observations were obtained with the 12-m array in the FDM Spectral Mode and the low-resolution observations used the 7-m array in the ACA Spectral Mode." (2.5 Atacama Large Millimeter Array archival data)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: Band 3: 16.9x8.0, 2.6x2.2, 0.46x0.28 arcsec; Band 7: 5.2x2.6, 0.67x0.47 arcsec  
  > "Three data sets with resolutions 16.9 arcsec$\times$8.0 arcsec, 2.6 arcsec$\times$2.2 arcsec, and 0.46 arcsec$\times$0.28 arcsec" (2.5 Atacama Large Millimeter Array archival data)
- max recoverable scale: _not stated_
- sensitivity: Band 3 rms 4.2, 3.6, 17 mJy (high, medium, low); Band 7 rms 3.5 and 17 mJy (high, low)  
  > "In Band 3, rms of 4.2, 3.6 and 17 mJy are achieved for high, medium and low resolution observations, respectively." (2.5 Atacama Large Millimeter Array archival data)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: Archival, PI S. Leurini  
  > "Observations were made during 2017-2018 (PI: S. Leurini #2017.1.00377.S)." (2.5 Atacama Large Millimeter Array archival data)
- Line: 13CO 1-0 (110.2013543 GHz)
- Line: C18O 1-0 (109.7821734 GHz)
- Line: C17O 3-2 (337.7061123 GHz)
- Line: CH3OH J=7-6 A- and E-type (337.1-340.1 GHz range)
- Other facility **uGMRT**: Band 4 and Band 5 radio continuum; ionized jet detection  
  > "Observations for G19.88-0.53 were carried out in Band 4 ($550 - 850$ MHz) and Band 5 ($1000 - 1450$ MHz)." (2.1 Radio continuum observation)
- Other facility **UKIRT-UIST**: NIR HK spectroscopy, H2 lines  
  > "using the HK grism set-up" (2.2 Near-infrared spectroscopic observation)
- Other facility **Herschel Hi-GAL**: 70-500 um images for SED  
  > "The $\rm 70-500\,\mu m$ images retrieved were observed as a part of the Herschel infrared Galactic plane Survey" (2.3 Far-infrared data from Hi-GAL survey)
- Other facility **APEX+Planck**: 870 um maps for clump  
  > "APEX+Planck database provides 870 $\mu m$ images." (2.4 APEX+Planck data)
- External data: VLA radio maps at 3.6 cm, 1.3 cm used for R1 spectral index  
  > "this uGMRT sub-band and VLA maps from (cite: 2006AJ....131..939Z) to derive the spectral index of R1" (4.1 Ionized jet) [from Zapata et al. 2006 (cite: 2006AJ....131..939Z)]
- External data: Continuum-subtracted H2 line image  
  > "we display the continuum-subtracted H$_2$ line image from (cite: 2010MNRAS.404..661V)" (3.2 Near-infrared line emission) [from Varricatt et al. 2010]
- External data: LSR velocity of 43.6 km/s  
  > "the data cube is corrected for the LSR velocity of $\rm 43.6\,km\,s^{-1}$" (3.4.1 CH3OH line emission) [from Qiu et al. 2007; Beuther et al. 2002a]

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

- task: Moment maps with CASA IMMOMENTS; 2D Gaussian fits with CASA viewer  
  > "using the CASA task, `IMMOMENTS`" (4.3.2 Outflow activity)
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
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- uGMRT data reduction, NIR reduction, SED modelling formalism and outflow velocity limits follow earlier paper  
  > "Data reduction is carried out along the lines discussed in (cite: 2019MNRAS.485.1775I)." (2.1 Radio continuum observation) [from Issac et al. 2019 (cite: 2019MNRAS.485.1775I)]
- Core mass formalism  
  > "This is done following the formalism described in (cite: 2018ApJ...853..160C)." (4.2.2 Nature of mm cores) [from Cheng et al. 2018 (cite: 2018ApJ...853..160C)]
- Optical depth expression and Qrot  
  > "we derived the optical depth of the $\rm CH_3OH$ lines adopting the following expression from (cite: 2012MNRAS.422.1098R)" (4.2.1 CH3OH rotational temperature) [from Ren et al. 2012]

### Not stated but needed to reproduce (our reading)

- ALMA calibration pipeline/CASA version and whether archive products were used
- Continuum imaging parameters (robust, cell, size, deconvolver)
- Line-free channels and continuum subtraction method
- How spectra extraction regions were defined
- Fitting uncertainties for continuum core flux
- Distance used in core mass equation presumably 3.31 kpc
- Which ALMA execution blocks/ spectral windows

## Analysis recipe

1. **Identify mm cores and measure properties**: 2D Gaussian fits to 2.7 mm high-resolution continuum cores  
  > "The deconvolved sizes of the cores are estimated by fitting 2D Gaussians to each component using the 2D fitting tool of CASA viewer." (3.3.2 Millimeter cores)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Fit molecular line spectra**: Gaussian profile fits of CO isotopologue and CH3OH lines; lines identified with CDMS/JPL via Weeds  
  > "Line parameters for the three transitions of CO determined by fitting Gaussian profiles using CLASS90 are listed" (3.4.2 Emission in isotopologues of CO)
   - software: CLASS90, Weeds
   - fitting: single or double Gaussians  
  > "Single Gaussians are used to fit these spectra." (Emission in isotopologues of CO)
   - validation: _not stated_
3. **Methanol rotational temperature and column density**: Rotation diagram with linear least-squares fit  
  > "Linear least-square fits to the data points gives the estimate of the rotational temperature" (4.2.1 CH3OH rotational temperature)
   - parameter: Low-resolution cubes; regions MM1+MM3+MM4, MM2, MM5+MM6  
  > "we extract the spectrum covering three regions (1) MM1, MM3, and MM4, (2) MM2, and (3) MM5 and MM6." (4.2.1 CH3OH rotational temperature)
   - assumption: Optically thin, LTE, beam-filling factor 1, Qrot = 1.23 Trot^1.5  
  > "$\eta_{\rm bf}$ is the beam-filling factor, taken to be 1 since the emission region is larger than the beam size" (4.2.1 CH3OH rotational temperature)
   - fitting: Linear least squares  
  > "Linear least-square fits to the data points gives the estimate of the rotational temperature" (CH_3OH rotational temperature)
   - validation: Optical depth check, tau up to ~0.1  
  > "Only two transitions for the combined cores of MM1, MM3, and MM4 show values $\sim 0.1$." (4.2.1 CH3OH rotational temperature)
4. **Core masses**: Optically thin dust mass with Trot as temperature, kappa=0.1(nu/1000GHz)^beta  
  > "we use the estimated $T_{\rm rot}$ values in the above expression to derive masses." (4.2.2 Nature of mm cores)
   - assumption: beta = 2.0  
  > "with $\beta$, the dust emissivity spectral index, fixed at 2.0" (4.2.2 Nature of mm cores)
   - fitting: _not stated_
   - validation: Kauffmann et al. 2010 mass-size criterion  
  > "$m(r) > 870{\rm M_\odot}(r/\rm pc)^{1.33}$" (4.2.2 Nature of mm cores)
5. **Infall and outflow analysis**: Infall velocity from inverse P-Cygni C17O; moment-0 maps of blue/red wings  
  > "The infall velocity is estimated as $V_{\rm inf}$ = $|V_{\rm LSR} - V_{\rm R}|$" (4.3.1 Infall signature in MM6)
   - software: CASA
   - parameter: Blue 36.1-42.1, red 45.1-51.1 km/s for C18O low-res  
  > "the emission is integrated over the velocity range of 36.1 to 42.1 $\rm km\,s^{-1}$" (4.3.2 Outflow activity)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : 2D Gaussian fitting of cores and moment maps  
  > "using the 2D fitting tool of CASA viewer" (3.3.2 Millimeter cores)
- **CLASS90/GILDAS** : Molecular line analysis and Gaussian fits  
  > "Analysis of molecular line data is carried out using CLASS90" (2.5 Atacama Large Millimeter Array archival data)
- **Weeds** : Line identification with CDMS/JPL  
  > "The CDMS and JPL databases are interactively loaded on the spectra employing the Weeds extension of CLASS90." (3.4.1 CH3OH line emission)
- **AIPS** : uGMRT calibration  
  > "using the Astronomical Image Processing System (AIPS)" (2.1 Radio continuum observation)
- **Clumpfind** : Clump identification in 870 um map  
  > "two-dimensional Clumpfind procedure" (3.3.1 Dust clump)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Rotational temperature MM2 | 115.9 | 23.5 | K | 3 | / MM2 / 10.1 / 115.9$\pm$23.5 / 3.9$\pm$0.5 / 0.7 / 29.6 / 1.0 / |
| Core masses range | 10-30 | not stated | Msun | 4 | The mass estimates range between $10 - 30\,{\rm M_\odot}$ |
| Infall velocity MM6 | 2.9 | not stated | km/s | 5 | $\rm 2.9\,km\,s^{-1}$ and $16.1\times10^{-3}\,M_\odot\,\rm yr^{-1}$ |
| Mass infall rate MM6 | 16.1e-3 | not stated | Msun/yr | 5 | $16.1\times10^{-3}\,M_\odot\,\rm yr^{-1}$ |
| Spectral index of R1 | 0.58 | 0.19 | dimensionless | 0 | yields a spectral index value of $0.58\pm0.19$ |
| Clump mass | 1911 | not stated | Msun | 0 | The mass of the clump is estimated to be 1911 $M_\odot$. |

## Qualitative findings

- Six mm cores and nine radio components reveal an eleven-member protocluster; MM2/R1 drives an ionized jet and collimated outflow  
  > "At higher resolution an additional collimated, bipolar outflow in the south-east and north-west direction is detected likely powered by MM2." (5 SUMMARY)

## Claim tuples

- H: G19.88-0.53 hosts a protocluster | E: Cross-identification of radio and ALMA mm sources | R: Six mm cores plus radio components, eleven members | F: Protocluster with sources in different evolutionary phases | **supported**
- H: MM6 shows infall | E: C17O(3-2) inverse P-Cygni profile | R: Vinf 2.9 km/s, infall rate 16.1e-3 Msun/yr | F: Infall signature | **supported**
- H: mm cores are hot cores | E: CH3OH rotation diagrams | R: Trot 47-116 K | F: Consistent with hot cores especially MM1-MM4 | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Radio components may be knots of a single jet so member count may be lower  
  > "then the number of distinct members of the detected protocluster would be less than eleven" (4.2 A protocluster revealed)
- Caveat (inferred, ours): Mass uses Trot as dust temperature; methanol may trace shocks
- Caveat (inferred, ours): Single-Gaussian/low-resolution beams blend cores
- Caveat (inferred, ours): No ALMA calibration or imaging details
- Caveat (inferred, ours): Infall from single inverse P-Cygni profile, could be outflow/artifact

## Reproducibility

- Data public (paper): Archival ALMA data  
  > "Atacama Large Millimeter Array (ALMA) archival data at 2.7 mm (Band 3) and 870 $\mu m$ (Band 7)" (2.5 Atacama Large Millimeter Array archival data)
- Products in archive: _not stated_
- Missing: Imaging parameters and CASA version
- Missing: Regions used for spectra
- Missing: Core mass distance explicit
- Data volume (inferred): ~50-200 GB for ALMA Band 3 and 7 12m+ACA
- Score (inferred): 4/5, Public data and formulae given, but ALMA processing and imaging details missing.
- Rediscovery candidate: no, Processing and extraction details are insufficient.

## Links

- Method: Issac et al. 2019 (cite: 2019MNRAS.485.1775I) (Data reduction, SED and outflow methods)
- Method: Cheng et al. 2018 (cite: 2018ApJ...853..160C) (core mass formalism)
- Companion: Qiu et al. 2007 (cite: 2007ApJ...654..361Q) (previous PdBI/SiO outflow observations)
- Related: ATLASGAL
- Related: Hi-GAL
- Related: GLIMPSE
- Related: UWISH2

## Checks

```json
{
 "quotes": 55,
 "quotes_ok": 55,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 79,
  "stated": 40,
  "rate": 0.506
 },
 "evidence_ok": true
}
```
