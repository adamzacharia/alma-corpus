# ALMA Investigation of Vibrationally Excited HCN/HCO<SUP>+</SUP>/HNC Emission Lines in the AGN-Hosting Ultraluminous Infrared Galaxy IRAS 20551-4250

`2016ApJ...825...44I` | The Astrophysical Journal 2016 | first author: Imanishi, Masatoshi | arXiv: 1605.00644 | DOI: 10.3847/0004-637X/825/1/44

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, astrochemistry, agn_and_quasars
- Question: Do HCN, HCO+ and HNC show vibrationally excited (v2=1f) J=3-2 emission in the AGN-hosting ULIRG IRAS 20551-4250, and does infrared radiative pumping and abundance explain the enhanced HCN-to-HCO+ ratio?  
  > "We found that all of the observational results were reproduced, if the HCN abundance was significantly higher than that of HCO$^{+}$ and HNC." (abstract)
- Target **IRAS 20551-4250**: coordinates continuum peak (20 58 26.80, -42 39 00.3) J2000  
  > "in which case the luminosity distance is 188 Mpc and 1 arcsec corresponds to 0.84 kpc at the distance of IRAS 20551$-$4250" (1 Introduction); z/distance z=0.043; luminosity distance 188 Mpc  
  > "in which case the luminosity distance is 188 Mpc and 1 arcsec corresponds to 0.84 kpc at the distance of IRAS 20551$-$4250" (1 Introduction); distance from redshift with H0=71, Omega_M=0.27, Omega_Lambda=0.73 (Komatsu et al. 2009)  
  > "in which case the luminosity distance is 188 Mpc and 1 arcsec corresponds to 0.84 kpc at the distance of IRAS 20551$-$4250" (1 Introduction)

## Data provenance

- ALMA projects: 2013.1.00033.S
- bands: Band 6 (211–275 GHz)  
  > "Our ALMA Cycle 2 observations in band 6 (211–275 GHz) were undertaken within the program 2013.1.00033.S" (2 Observations and Data Analysis)
- frequencies and spectral setup: 1.875 GHz band mode, 3840 channels; 3 USB windows for HCN/HCO+ and 4 windows (2 USB, 2 LSB) for HNC  
  > "We adopted the widest 1.875 GHz band mode and 3840 total channel number for our observations." (2 Observations and Data Analysis); "We employed four spectral windows, of which two in USB were used to cover HNC J=3–2 and HNC v$_{2}$=1f J=3–2 lines." (2 Observations and Data Analysis)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 15–650 m, 35 antennas  
  > "| HCN/HCO$^{+}$ J=3–2 | 2014 May 17 | 35      | 15–650   | 14          |" (Table 1)
- angular resolution: ~0.5 arcsec (~420 pc)  
  > "The achieved spatial resolution is $\sim$0$\ensuremath{''}$5 ($\sim$420 pc)" (3 Results)
- max recoverable scale: ~10 arcsec  
  > "The maximum recoverable scale in our data is $\sim$10”." (2 Observations and Data Analysis)
- sensitivity: _not stated_
- time on source: 14 min (HCN/HCO+), 36 min (HNC)  
  > "| HNC J=3–2           | 2014 May 17 | 35      | 15–650   | 36          |" (Table 1)
- observing dates: 2014 May 17  
  > "| HCN/HCO$^{+}$ J=3–2 | 2014 May 17 | 35      | 15–650   | 14          |" (Table 1)
- pi or archival as stated: Own program, PI M. Imanishi  
  > "within the program 2013.1.00033.S (PI = M. Imanishi)" (2 Observations and Data Analysis)
- Line: HCN J=3-2 v=0 and v2=1f (265.89 / 267.20 GHz)
- Line: HCO+ J=3-2 v=0 and v2=1f (267.56 / 268.69 GHz)
- Line: HNC J=3-2 v=0 and v2=1f (271.98 / 273.87 GHz)
- Other facility **Spitzer IRS**: 5–35 micron spectrum used to estimate infrared pumping flux  
  > "is estimated from the 5–35 $\mu$m spectrum of IRAS 20551$-$4250 taken by Spitzer IRS (Fig. 7)" (4.3.1)
- External data: HCN/HCO+/HNC J=4-3 fluxes from ALMA Cycle 0  
  > "HCN J=4–3 fluxes at v$_{2}$=1f and v=0 are from (cite: ima13b)." (Table 5) [from (cite: ima13b)]
- External data: Molecular parameters (E_u, A_ul) from CDMS  
  > "Values in Cols. (3) and (4) are from the Cologne Database of Molecular Spectroscopy (CDMS) (cite: mul05) via Splatalogue" (Table 5) [from (cite: mul05)]
- External data: Vibrational A coefficients A(v2=1-0): HCN 1.7, HCO+ 3.0, HNC 5.2 s^-1  
  > "$\sim$1.7 s$^{-1}$ (HCN) (cite: deg86; aal07a), $\sim$3.0 s$^{-1}$ (HCO$^{+}$) (cite: mau95), and $\sim$5.2 s$^{-1}$ (HNC) (cite: aal07a)" (4.3.1) [from (cite: deg86; aal07a; mau95)]

## Processing

### Calibration

- pipeline or manual: Calibrated data provided by the Joint ALMA Observatory used  
  > "We first checked the visibility plots in calibrated data provided by the Joint ALMA Observatory" (2 Observations and Data Analysis)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J2056-4714, flux from ALMA monitoring  
  > "The flux density of J2056$-$4714 is estimated from ALMA monitoring observations." (Table 1)
- flux scale uncertainty: <10% in band 6  
  > "the absolute calibration uncertainty is estimated to be $<$10% in band 6" (2 Observations and Data Analysis)
- self calibration: _not stated_

### Imaging

- task: CASA clean  
  > "After subtracting these estimated continuum levels, we performed the task “clean” for detected emission line data." (2 Observations and Data Analysis)
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: 0.1 arcsec per pixel  
  > "adopted a pixel scale of 0$\ensuremath{''}$1 pixel$^{-1}$ in this clean procedure" (2 Observations and Data Analysis)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: Continuum estimated from line-free channels and subtracted  
  > "We selected channels that were not clearly affected by detected emission line features, and estimated the continuum flux levels" (2 Observations and Data Analysis)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: 40-channel spectral binning (~20 km/s)  
  > "We employed 40 channel spectral binning ($\sim$20 km s$^{-1}$)" (2 Observations and Data Analysis)
- final beam: ~0.5 x 0.46 arcsec  
  > "0.50$\times$0.46 (74$^{\circ}$)" (Table 2)
- final rms: _not stated_

### Inherited from earlier work

- Equation for thermal free-free emission estimate  
  > "is estimated to be $\sim$1.6 mJy, using equation (1) of (cite: nak05)" (3 Results) [from (cite: nak05)]
- Power-law intrinsic continua and PAH equivalent width definition  
  > "Following (cite: ima07b), we adopt power-law-shaped intrinsic continua, using data unaffected by the silicate dust absorption features and strong PAH emission features." (4.3.1) [from (cite: ima07b)]

### Not stated but needed to reproduce (our reading)

- clean weighting/robust, deconvolver, threshold and masks
- specific line-free channels and continuum fit order
- CASA version
- channel ranges for moment 0 maps
- Gaussian fitting procedure details
- Spitzer IRS spectrum data reduction and power-law fit wavelength ranges

## Analysis recipe

1. **Image continuum and lines**: CASA clean after continuum subtraction; moment 0/1/2 maps; imfit for sizes  
  > "Using the CASA task “imfit”, we estimate the deconvolved, intrinsic emission size" (3 Results)
   - software: CASA
   - parameter: 40-channel binning, 0.1 arcsec pixels  
  > "We employed 40 channel spectral binning ($\sim$20 km s$^{-1}$)" (2 Observations and Data Analysis)
   - fitting: _not stated_
   - validation: Independent continuum maps a and b consistent; line peaks agree with continuum peak within 1 pixel  
  > "These independently taken continuum data show consistent results, in terms of peak position, peak flux, and morphology." (3 Results)
2. **Measure line fluxes**: Gaussian fits to spectra at continuum peak; upper limit from moment 0 for HCO+ v2=1f  
  > "We fit detected molecular emission lines in the spectra with Gaussian profiles." (3 Results)
   - software: CASA
   - fitting: Gaussian profiles  
  > "We fit detected molecular emission lines in the spectra with Gaussian profiles." (3 Results)
   - validation: _not stated_
3. **Predict infrared pumping and derive abundance ratios**: Compare observed v2=1f J=3 column density ratios with predicted pumping using B coefficients, Spitzer IR continuum at 12/14/21.5 micron  
  > "The discrepancy between observation (Eqn. (3)) and prediction (Eqn. (13)) can be reconciled if the column density at v=0 (N$_{v=0}$) for HCN is higher than HCO$^{+}$ and HNC" (4.3.1)
   - assumption: Same emitting region and optically thin v2=1f; foreground screen dust; AGN-dominated mid-IR continuum  
  > "a simple foreground screen dust model is applicable" (4.3.1)
   - fitting: _not stated_
   - validation: Optical depth ratios from abundance and from isotopologue flux are consistent  
  > "The two independently derived optical depth ratios in Equations (16) and (19) show consistent results to each other." (4.3.2)
4. **Estimate line opacity and excitation temperatures**: HCN/H13CN ratio with 12C/13C 50–100; clumpy flux attenuation tau/(1-exp(-tau)); T_ex from v2=1f/v=0; pumping condition test  
  > "Assuming optically thin emission for H$^{13}$CN J=3–2, HCN J=3–2 emission is estimated to be optically thick, and its flux can be attenuated by a factor of 3–6." (4.3.2)
   - assumption: 12C/13C ~50 in starbursts, ~100 in ULIRGs  
  > "In ULIRGs, the $^{12}$C/$^{13}$C abundance ratios are as high as $\sim$100 (cite: hen14)." (4.3.2)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : Calibrated data analysis, clean, imfit  
  > "We used CASA (cite: pet12) for our data analysis." (2 Observations and Data Analysis)
- **Splatalogue** : Molecular line parameters from CDMS  
  > "Molecular parameters are derived from the Cologne Database of Molecular Spectroscopy (CDMS) (cite: mul05) via Splatalogue" (1 Introduction)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| HCN v2=1f J=3-2 flux | 0.25 | 0.07 | Jy km/s | 2 | / HCN J=3–2, v$_{2}$=1f        / 267.20           / 0.22 (7.6$\sigma$) |
| HNC v2=1f J=3-2 flux | 0.20 | 0.07 | Jy km/s | 2 | / HNC J=3–2, v$_{2}$=1f / 273.87 / 692.0 / 8.5 / 0.20$\pm$0.07 / |
| HCO+ v2=1f J=3-2 flux upper limit | <0.088 | 3 sigma | Jy km/s | 2 | / HCO$^{+}$ J=3–2, v$_{2}$=1f / 268.69 / 1217.4 / 13.1 / $<$0.088 / |
| Continuum flux at ~255 GHz | 3.6–3.8 | not stated | mJy/beam | 1 | / a: 244.8–246.6, 247.1–249.0, 259.8–263.5 / 3.8 (59$\sigma$) |
| Abundance ratio HCN:HCO+:HNC | 1:<0.4:<0.08 | not stated | dimensionless | 3 | HCN:HCO^{+}:HNC (abundance) & = & 1:<0.4:<0.08. |
| HCN v=0 J=3-2 flux attenuation | 6 | not stated | dimensionless | 4 | we adopt the flux attenuation of HCN J=3–2 emission to be 6 |
| J=4-3 to J=3-2 flux ratio | HCN 1.6, HCO+ 1.7, HNC 1.8 | 0.2 | dimensionless | 2 | are 1.6$\pm$0.2 for HCN, 1.7$\pm$0.2 for HCO$^{+}$, and 1.8$\pm$0.2 for HNC |
| tau(9.7um) silicate | 2.7 | not stated | dimensionless | 3 | is estimated to be $\tau_{9.7}$ $\sim$ 2.7 |

## Qualitative findings

- HCN and HNC v2=1f J=3-2 detected, HCO+ v2=1f not; IR radiative pumping affects v=0 rotational excitation for HCN and HNC.  
  > "We detected HCN v$_{2}$=1f J=3–2 and HNC v$_{2}$=1f J=3–2 emission lines" (5 Summary)

## Claim tuples

- H: Is IR pumping alone responsible for the HCN/HCO+/HNC v2=1f pattern, or is HCN abundance enhanced? | E: Compared observed v2=1f ratios with predicted pumping from the Spitzer spectrum | R: Observed 1:<0.20:0.69 vs predicted 1:0.5:9 needs HCN abundance higher by >2.5 and ~13 | F: HCN abundance is significantly higher than HCO+ and HNC | **supported**
- H: Does IR pumping affect v=0 rotational excitation? | E: Compared T_ex-vib with threshold and IR absorption requirement | R: T_ex-vib >185 K for HCN vs ~160 K threshold; HNC 250 vs 80 K | F: IR pumping affects v=0 excitation for HCN and HNC | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Rotational transitions within v=0 and v2=1 not treated; same-region assumption is simplistic  
  > "Second, we assumed that HCN, HCO$^{+}$, and HNC emission both at v=0 and v$_{2}$=1 come from the same region ($\S$4.3.1). This is clearly too simplistic." (4.4 Possible caveats)
- Caveat (inferred, ours): HNC v2=1f may be blended with HC3N v7=1f
- Caveat (inferred, ours): Spitzer IRS resolution too low to confirm IR absorption
- Caveat (inferred, ours): Opacity estimates rely on assumed 12C/13C

## Reproducibility

- Data public (paper): ALMA program 2013.1.00033.S acknowledged  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2013.1.00033.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: clean parameters
- Missing: CASA version
- Missing: Spitzer spectrum processing and power-law fit ranges
- Data volume (inferred): ~10-30 GB
- Score (inferred): 3/5, Data identified and results numeric, but imaging parameters and IR continuum fitting are sparsely specified.
- Rediscovery candidate: yes, Public ALMA data; line fluxes in tables are checkable via simple imaging and Gaussian fits.

## Links

- Method: (cite: ima07b) (IR spectral continuum and PAH equivalent width method)
- Method: (cite: sak10) (IR pumping condition)
- Companion: (cite: ima13b) (ALMA Cycle 0 J=4-3 data of same source)

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
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 68,
  "stated": 41,
  "rate": 0.603
 },
 "evidence_ok": true
}
```
