# ALMA Imaging of the CO (7-6) Line Emission in the Submillimeter Galaxy LESS 073 at z = 4.755

`2020ApJ...892..145Z` | The Astrophysical Journal 2020 | first author: Zhao, Yinghe | arXiv: 2002.04816 | DOI: 10.3847/1538-4357/ab75eb

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies
- Question: What are the CO(7-6) line, [CI] and continuum properties of SMG LESS 073 at z=4.755, and can line-ratio-based f60/f100 estimates be validated against SED fits?  
  > "The SED-fit-based $f_{60}/f_{100}$ is consistent with those estimated from various line ratios as advocated by our earlier work" (abstract)
- Target **LESS 073 (LESS J033229.4-275619)**: coordinates _not stated_; z/distance z = 4.755; D_L = 44,866 Mpc  
  > "LESS 073 (also known as LESS J033229.4$-$275619), which lies at $z=4.755$ in the Extended *Chandra* Deep Field South." (1 Introduction); distance from redshift; cosmology H0=71, OmegaM=0.27, OmegaL=0.73  
  > "LESS 073 (also known as LESS J033229.4$-$275619), which lies at $z=4.755$ in the Extended *Chandra* Deep Field South." (1 Introduction)

## Data provenance

- ALMA projects: 2015.1.00388.S
- bands: Band 4  
  > "using the Band 4 receivers of ALMA in the time division mode (TDM)" (2 Observations and Data Reduction)
- frequencies and spectral setup: 4 SPWs centered at 140.15, 142.15, 128.15, 130.11 GHz, ~2 GHz each; ~33.5 km/s resolution  
  > "were centered at the sky frequencies of 140.15, 142.15, 128.15 and 130.11 GHz, respectively, each with a bandwidth of about 2 GHz." (2 Observations and Data Reduction)
- continuum bandwidth: _not stated_
- arrays: 12-m, 42 and 38 antennas  
  > "42 and 38 12-meter antennas were used respectively" (2 Observations and Data Reduction)
- configurations: _not stated_
- baselines: 15 to 460 m  
  > "with baselines ranging from 15 to 460 meters" (2 Observations and Data Reduction)
- angular resolution: 1.22x0.95 arcsec line; 1.19x0.90 continuum  
  > "$1\ensuremath{''}.22\times0\ensuremath{''}.95$ ($1\ensuremath{''}.19\times0\ensuremath{''}.90$ for the continuum)" (2 Observations and Data Reduction)
- max recoverable scale: _not stated_
- sensitivity: 0.3 mJy/beam per 100 km/s channel; continuum 40 uJy/beam  
  > "For the continuum, the 1$\sigma$ rms noise is about 40 $\mu$Jy beam$^{-1}$." (2 Observations and Data Reduction)
- time on source: 9 minutes total  
  > "The total on-source integration is 9 minutes." (2 Observations and Data Reduction)
- observing dates: March 4 and 26, 2016  
  > "conducted in two equal-duration runs on March 4 and 26, 2016" (2 Observations and Data Reduction)
- pi or archival as stated: _not stated_
- Line: CO 7-6 (806.652 GHz)
- Line: [CI] 3P2-3P1 (370 um) (not stated)
- External data: FIR/submm photometric points for the SED  
  > "the remained photometric points are collected from the literature (De Breuck et al. 2014; Gilli et al. 2014 and see references therein)" (3.2 Continuum Emission) [from De Breuck et al. 2014; Gilli et al. 2014]
- External data: [CII] and [NII] line fluxes for line ratios  
  > "Reference for line (excluding CO (7$-$6)) fluxes: (1) De Breuck et al. (2014); (2) Nagao et al. (2012); (3) this work." (Table 2) [from De Breuck et al. 2014; Nagao et al. 2012]
- External data: CO(2-1) luminosity  
  > "Comparing our $L^\prime _{\rm CO\,(7-6)}$ with $L^\prime _{\rm CO\,(2-1)}$ from Coppin et al. (2010)" (3.1.1 CO (7-6) Emission) [from Coppin et al. 2010]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: CASA 4.5.3  
  > "The data were reduced with CASA 4.5.3 (McMullin et al. 2007)." (2 Observations and Data Reduction)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0334-4008 and J0348-2749 (pointing, phase, bandpass, flux)  
  > "The pointing, phase, bandpass and flux calibrations were based on J0334$-$4008 and J0348$-$2749." (2 Observations and Data Reduction)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 0.0  
  > "cleaned using the Briggs weightings with robust = 0.0" (2 Observations and Data Reduction)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: noise before PB correction; fluxes after  
  > "All noise measurements were performed on the maps before the primary beam correction" (2 Observations and Data Reduction)
- array combination: _not stated_
- smoothing: cubes binned to 100 km/s channels  
  > "we binned spectral cubes into channels with the width of $\delta {\rm v}=100$ km s$^{-1}$" (2 Observations and Data Reduction)
- final beam: 1.22x0.95 arcsec, PA ~87 deg  
  > "and a position angle of $\sim$87$^\circ$" (2 Observations and Data Reduction)
- final rms: moment0 81 mJy/km/s/beam  
  > "its 1$\sigma$ rms noise is 81 mJy km s$^{-1}$ beam$^{-1}$" (2 Observations and Data Reduction)

### Inherited from earlier work

- f60/f100 from line ratios using Lu15 and Lu 2017b, 2018 equations  
  > "We have used the equations in Lu15, Lu et al. (2017b, 2018) to estimate $f_{60}/f_{100}$" (3.3 Line Ratios) [from Lu15; Lu et al. (2017b, 2018)]
- 5% calibration uncertainty added to ALMA photometry  
  > "we have added a calibration uncertainty of 5%, following Bonato et al. (2018)" (3.2 Continuum Emission) [from Bonato et al. (2018)]
- Upper limits handled in SED fit  
  > "we adopt the method proposed in Sawicki (2012) during the fitting process" (3.2 Continuum Emission) [from Sawicki (2012)]

### Not stated but needed to reproduce (our reading)

- Line-free channels and continuum channel selection
- Clean mask, threshold, cell and image size
- Which SED photometric points and values were used
- SED fitting sampler/minimizer details
- Which flux density exactly for the rest-frame 850 um gas mass
- Primary beam and aperture spectrum extraction region details
- Equation parameters for SFR from Lu15 not given

## Analysis recipe

1. **Image continuum and CO(7-6) cube**: Combine calibrated data, clean with Briggs weighting; continuum from SPWs 0-3 excluding line channels; cube from SPW-0 binned to 100 km/s  
  > "The continuum was measured using data in SPWs 0-3 by excluding the line emission channels." (2 Observations and Data Reduction)
   - software: CASA
   - parameter: robust = 0.0  
  > "cleaned using the Briggs weightings with robust = 0.0" (2 Observations and Data Reduction)
   - fitting: _not stated_
   - validation: _not stated_
2. **Measure CO(7-6) flux, width, size**: Average of aperture photometry, 1-d Gaussian spectrum fit, and imfit 2-d fit  
  > "All three fluxes are consistent well with each other, and thus we adopt the averaged $f_{\rm CO\,(7-6)}=0.86\pm0.08$ Jy km s$^{-1}$ as the final result." (3.1.1 CO (7-6) Emission)
   - software: CASA imfit
   - fitting: _not stated_
   - validation: Three methods consistent  
  > "All three fluxes are consistent well with each other" (3.1.1 CO (7-6) Emission)
3. **Fit FIR SED**: Single-temperature modified blackbody, optically thick vs thin  
  > "we adopt a general single-temperature-modified blackbody" (3.2 Continuum Emission)
   - parameter: beta fixed 1.8; nu0 = 1.5 THz (200 um)  
  > "We further fix $\beta=1.8$ (Planck Collaboration et al. 2011) due to our limited data points." (3.2 Continuum Emission)
   - assumption: Filling factor 1 in Stefan-Boltzmann size  
  > "we have assumed that the filling factor of the blackbody (the starburst in this case) is equal to 1" (3.2 Continuum Emission)
   - fitting: _not stated_
   - validation: Optically thick model preferred by size comparison to Hodge 2016  
  > "it seems that the source radius is more consistent with the estimation from the optically thick model" (3.2 Continuum Emission)
4. **Gas mass**: [CI] luminosity times conversion 12.5 Msun/(K km/s pc2); average with CO(2-1) based mass  
  > "Adopting the CO-based [C i]-to-total gas conversion factor of 12.5 $M_\odot$ (K km s$^{-1}$ pc$^2$)$^{-1}$ in Jiao et al. (2017)" (3.1.2 [C I] Emission)
   - assumption: alpha_CO = 0.8  
  > "$\alpha_{\rm CO}=0.8$ $M_\odot$ (K km s$^{-1}$ pc$^2$)$^{-1}$" (3.1.2 [C I] Emission)
   - fitting: _not stated_
   - validation: _not stated_
5. **Line-ratio f60/f100, SFR, depletion time**: Lu15 relations; SFR from CO(7-6), [NII], FIR; depletion time = Mgas/SFR  
  > "The gas depletion time, $\tau_{\rm depletion}=M_{\rm gas}/{\rm SFR}" (3.4.2 The SFR Surface Density)
   - assumption: Salpeter IMF; L_FIR = L_IR/1.9  
  > "we assume a Salpeter (1959) initial mass function" (3.4.1 Estimation of the SFR)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.5.3: Data reduction, cleaning, imfit  
  > "The data were reduced with CASA 4.5.3 (McMullin et al. 2007)." (2 Observations and Data Reduction)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| CO(7-6) integrated flux | 0.86 | 0.08 | Jy km/s | 2 | integrated flux of $0.86\pm0.08$ Jy km s$^{-1}$ |
| CO(7-6) FWHM | 343 | 40 | km/s | 2 | a line width of $343\pm40$ km s$^{-1}$ |
| Continuum flux density | 0.51 | 0.02 | mJy | 2 | the flux density of the continuum is $0.51\pm0.02$ mJy |
| T_dust (optically thick) | 57.6 | 3.5 | K | 3 | $T_{\rm dust}=57.6\pm3.5$ K |
| f60/f100 SED | 0.86 | 0.08 | dimensionless | 3 | $f_{60}/f_{100}=0.86\pm0.08$ |
| L_IR | 5.8e12 | 0.9e12 | Lsun | 3 | $L_{\rm IR}=(5.8\pm0.9)\times10^{12}~L_\odot$ |
| Total molecular gas mass | 3.3e10 | 1.7e10 | Msun | 4 | $(3.3\pm1.7)\times10^{10}~M_\odot$ |
| [CI] flux | 0.23 | 0.08 | Jy km/s | 2 | $f_{\rm [C\,{\scriptsize \textsc{i}}]}=0.23\pm0.08$ Jy km s$^{-1}$ |
| SFR from [NII] | 760 | +590/-330 | Msun/yr | 5 | ${\rm SFR_{[N\,{\scriptsize\textsc{ii}}]}}=760^{+590}_{-330}~M_\odot~{\rm yr}^{-1}$ |
| Average line-ratio f60/f100 | 1.05 | 0.09 | dimensionless | 5 | have an average value of $1.05\pm0.09$ |

## Qualitative findings

- CO(7-6) emission is largely unresolved and continuum totally unresolved at ~1.2x0.9 arcsec  
  > "the CO (7$-$6) emission is largely unresolved" (abstract)

## Claim tuples

- H: Line-ratio f60/f100 method works for high-z sources | E: Compare f60/f100 from line ratios with SED fit | R: Line-ratio mean 1.05±0.09 vs SED 0.86±0.08, within 1-2 sigma | F: Method usable at high z | **supported**
- H: CO(7-6) may be enhanced by non-SF heating | E: Compare L_CO/L_FIR with local (U)LIRGs | R: 10^-4.20 vs 10^-4.61 local | F: Possible shock enhancement of CO | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Optically thin SED model (T=35.8 K) rejected since its radius is above the observed size  
  > "thus we adopt the best-fit results from this model in the following analysis" (3.2 Continuum Emission)
- How they decided it was enough: _not stated_
- Limitation (authors): Low spatial and velocity resolution; [CI] only ~4 sigma  
  > "both our spatial and velocity resolutions are much lower than that in De Breuck et al. (2014)" (3.1.1 CO (7-6) Emission)
- Caveat (inferred, ours): Short 9-min data; [CI] detection marginal
- Caveat (inferred, ours): Large systematics in gas mass from conversion factors
- Caveat (inferred, ours): SED fit with few points and fixed beta
- Caveat (inferred, ours): Averaging three flux methods that are not independent

## Reproducibility

- Data public (paper): ALMA data identified by project code  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2015.1.00388.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Imaging details (mask, cell size, line-free channels)
- Missing: SED photometry table
- Missing: Lu15 equation coefficients
- Data volume (inferred): ~5-20 GB raw (two short Band 4 executions)
- Score (inferred): 3/5, Public data and basic imaging stated, but SED inputs and several imaging details missing.
- Rediscovery candidate: yes, Public data, short dataset, numeric line flux and continuum results reproducible.

## Links

- Method: Lu et al. 2015 (Lu15) (line-ratio f60/f100 and SFR calibrators)
- Method: Sawicki (2012) (SED fit with upper limits)
- Companion: De Breuck et al. 2014 ([CII] data and photometry of LESS 073)

## Checks

```json
{
 "quotes": 57,
 "quotes_ok": 57,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 10,
 "numeric_problems": 0,
 "fill": {
  "facts": 73,
  "stated": 41,
  "rate": 0.562
 },
 "evidence_ok": true
}
```
