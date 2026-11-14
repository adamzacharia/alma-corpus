# ALMA Observations of Nearby Luminous Infrared Galaxies with Various AGN Energetic Contributions Using Dense Gas Tracers

`2014AJ....148....9I` | The Astronomical Journal 2014 | first author: Imanishi, Masatoshi | arXiv: 1404.6597 | DOI: 10.1088/0004-6256/148/1/9

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, astrochemistry, agn_and_quasars
- Question: Do AGN-important (U)LIRGs show different HCN/HCO+/HNC J=4-3 flux ratios than starburst-dominated galaxies?  
  > "Our primary interest is to determine whether AGN-important galaxies display noticeably different molecular line flux ratios from starburst-dominated galaxies." (Targets)
- Target **IRAS 08572+3915 NW**: coordinates (09 00 25.39, +39 03 54.2) continuum peak  
  > "IRAS 08572$+$3915 | 0.058 | 1.1" (Table 1); z/distance z = 0.058  
  > "IRAS 08572$+$3915 | 0.058 | 1.1" (Table 1); distance from Table 1 redshift; literature  
  > "IRAS 08572$+$3915 | 0.058 | 1.1" (Table 1)
- Target **IRAS 12127-1412 NE**: coordinates (12 15 19.13, -14 29 41.7) continuum peak  
  > "IRAS 12127$-$1412 | 0.133 | 2.3" (Table 1); z/distance z = 0.133  
  > "IRAS 12127$-$1412 | 0.133 | 2.3" (Table 1); distance from _not stated_
- Target **IRAS 00183-7111**: coordinates (00 20 34.70, -70 55 26.4) continuum peak  
  > "IRAS 00183$-$7111 ($z =$ 0.327)" (Targets); z/distance z = 0.327  
  > "IRAS 00183$-$7111 ($z =$ 0.327)" (Targets); distance from _not stated_
- Target **IRAS 22491-1808**: coordinates (22 51 49.35, -17 52 24.2) continuum peak  
  > "Our molecular line data of dense gas tracers indicate $z =$ 0.0776" (Results); z/distance z = 0.076 adopted (Kim & Sanders 1998); lines give 0.0776  
  > "Our molecular line data of dense gas tracers indicate $z =$ 0.0776" (Results); distance from Kim & Sanders 1998  
  > "Our molecular line data of dense gas tracers indicate $z =$ 0.0776" (Results)
- Target **NGC 1614**: coordinates _not stated_; z/distance z = 0.016  
  > "NGC 1614 (IRAS 04315$-$0840) | 0.016 | 0.32" (Table 1); distance from _not stated_
- Target **IRAS 20551-4250**: coordinates _not stated_; z/distance z = 0.043  
  > "IRAS 20551$-$4250 | 0.043 | 0.84" (Table 1); distance from _not stated_

## Data provenance

- ALMA projects: 2011.0.00020.S
- bands: Band 7 for all except IRAS 00183-7111 (Band 6)  
  > "Band 7 was used for all sources except IRAS 00183$-$7111 ($z=$ 0.327), for which band 6 was used due to its high redshift." (3 Observations and Data Analysis)
- frequencies and spectral setup: 1.875 GHz wide mode; 4 spectral windows for HCN/HCO+, 2 for HNC  
  > "We adopted the widest 1.875 GHz band width mode." (3 Observations and Data Analysis); "For HCN and HCO$^{+}$ J=4–3 observations, four spectral windows were used. For HNC J=4–3 observations, two spectral windows were used." (Table 3)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 15–402 m depending on execution  
  > "2012 December 14        | 24      | 15–402   | 22" (Table 2)
- angular resolution: about 0.6 to 2.5 arcsec beams  
  > "IRAS 00183$-$7111 | a (261) | 2.2 (26$\sigma$) | (00 20 34.70, $-$70 55 26.4) | 0.084 | 2.5 $\times$ 1.2 (177$^{\circ}$)" (Table 4)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: 17–65 min per execution  
  > "Col.(6): Net on source exposure time in min." (Table 2)
- observing dates: _not stated_
- pi or archival as stated: PI = M. Imanishi, Cycle 0  
  > "within the program 2011.0.00020.S (PI = M. Imanishi)" (3 Observations and Data Analysis)
- Line: HCN J=4-3 (354.505 GHz)
- Line: HCO+ J=4-3 (356.734 GHz)
- Line: HNC J=4-3 (362.630 GHz)
- Other facility **Nobeyama Millimeter Array**: pre-ALMA HCN J=1-0 data of (U)LIRGs  
  > "observed with the pre-ALMA interferometric facility, Nobeyama Millimeter Array" (Table 7)
- External data: IRAS fluxes and optical classes in Table 1  
  > "taken from (cite: kim98), (cite: san03), or IRAS faint source catalog" (Table 1) [from Kim & Sanders 1998; Sanders et al. 2003]
- External data: NGC 1614 and IRAS 20551-4250 ALMA results  
  > "Our ALMA Cycle 0 observational results of NGC 1614 and IRAS 20551$-$4250 have been published in (cite: ima13a) and (cite: ima13b), respectively." (4 Results) [from Imanishi & Nakanishi 2013a,b]
- External data: HCN J=1-0 data of (U)LIRGs  
  > "HCN J=1–0 emission peak in [mJy], based on Gaussian fit (cite: ima04; ima06b; in06; ima07b; ima09b)" (Table 7) [from Imanishi et al. 2004, 2006b, 2007b, 2009b; Imanishi & Nakanishi 2006]

## Processing

### Calibration

- pipeline or manual: Started from calibrated data provided by JAO, except IRAS 22491-1808 HNC re-calibrated after phase center fix  
  > "We started data analysis from calibrated data provided by the Joint ALMA Observatory, using CASA" (3 Observations and Data Analysis)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: delivered calibrated data used except IRAS 22491-1808 HNC  
  > "We corrected for the phase center by using the CASA task ’fixvis’ and re-calibrated the IRAS 22491$-$1808 HNC data." (3 Observations and Data Analysis)
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: clean  
  > "performed the task “clean” for continuum-subtracted molecular line data, as well as for the continuum data themselves" (3 Observations and Data Analysis)
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: 0.3 or 0.1 arcsec/pixel depending on beam  
  > "we employed 0$\ensuremath{''}$3 pixel$^{-1}$ or 0$\ensuremath{''}$1 pixel$^{-1}$, depending on the beam size of the obtained data" (3 Observations and Data Analysis)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: continuum estimated from line-free channels, subtracted from spectra  
  > "We then subtracted the estimated continuum emission from the spectra, and performed the task “clean” for continuum-subtracted molecular line data" (3 Observations and Data Analysis)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: binned 40 channels (17–18 km/s Band 7; 22–23 km/s Band 6)  
  > "we binned 40 channels (17–18 km s$^{-1}$ in band 7 and 22–23 km s$^{-1}$ in band 6)" (3 Observations and Data Analysis)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Observation and analysis details of NGC 1614 and IRAS 20551-4250  
  > "Observation details of NGC 1614 and IRAS 20551$-$4250 are presented in (cite: ima13a; ima13b), and are not repeated here." (3 Observations and Data Analysis) [from (cite: ima13a; ima13b)]
- Line luminosity equations  
  > "where we adopted equations (1) and (3) from (cite: sol05)" (4 Results) [from (cite: sol05)]

### Not stated but needed to reproduce (our reading)

- CASA version
- clean parameters (weighting, robust, threshold, mask, deconvolver)
- line-free channel ranges
- continuum-subtraction fit order
- flux calibration accuracy
- moment-map clipping thresholds and velocity ranges
- reference calibrator flux values

## Analysis recipe

1. **Continuum imaging**: Line-free channels used to estimate continuum; cleaned continuum-a and -b maps; peak flux and rms measured  
  > "We then selected channels that were free from strong emission lines to estimate the continuum flux level." (3 Observations and Data Analysis)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Line cubes and moment maps**: Continuum-subtracted cubes cleaned; moment 0/1/2 maps made  
  > "integrated intensity (moment 0) maps and spectra at the continuum peak" (4 Results)
   - software: CASA
   - parameter: 40-channel binning; 0.3 or 0.1 arcsec pixels  
  > "To create spectra, we binned 40 channels" (3 Observations and Data Analysis)
   - fitting: _not stated_
   - validation: Continuum well subtracted in spectra  
  > "the continuum level was found to be well-subtracted" (4 Results)
3. **Measure line fluxes**: Gaussian fits to spectra at continuum peak within beam  
  > "the lines were fitted with a Gaussian profile" (4 Results)
   - fitting: Gaussian profile; FWHM fixed for weak lines  
  > "CS J=7–6 | $<$0.34 ($<$3$\sigma$) | 0.11 | 36 | 0.6 $\times$ 0.5 (40$^{\circ}$) | 39869$\pm$73 | 1.1$\pm$0.5 | 240 (fix)" (Table 5)
   - validation: _not stated_
4. **Derive luminosities and flux ratios**: Line luminosities from Gaussian fluxes; HCN/HCO+ and HCN/HNC ratios compared  
  > "The molecular line luminosities are derived from the fluxes based on Gaussian fits" (4 Results)
   - assumption: H0 = 71 km/s/Mpc, OmegaM = 0.27, OmegaL = 0.73  
  > "we adopt H$_{0}$ $=$ 71 km s$^{-1}$ Mpc$^{-1}$, $\Omega_{\rm M}$ = 0.27, and $\Omega_{\rm \Lambda}$ = 0.73" (1 Introduction)
   - fitting: _not stated_
   - validation: _not stated_
5. **Compare observed HCN J=4-3 peak with thermal expectation**: HCN J=1-0 peak predicted from IR flux, scaled by 16 for thermal excitation  
  > "HCN is thermalized at up to J=4–3, where the peak flux is 16 times higher at J=4–3 than at J=1–0" (Table 8)
   - assumption: thermal excitation to J=4-3  
  > "HCN is thermalized at up to J=4–3" (Table 8)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : calibration, fixvis, clean, imaging  
  > "using CASA, except the IRAS 22491$-$1808 HNC data" (3 Observations and Data Analysis)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| HCN J=4-3 flux, IRAS 08572+3915 | 3.2 | 0.3 | Jy km/s | 3 | HCN J=4–3 / 2.8 (18$\sigma$) / 0.15 / 23 / 1.8 $\times$ 1.1 ($-$113$^{\circ}$) / 17501$\pm$10 / 9.7$\pm$0.6 / 330$\pm$21 / 3.2$\pm$0.3 |
| HCO+ J=4-3 flux, IRAS 08572+3915 | 4.2 | 0.3 | Jy km/s | 3 | HCO$^{+}$ J=4–3 / 3.5 (29$\sigma$) / 0.12 / 19 / 2.5 $\times$ 1.1 ($-$111$^{\circ}$) / 17489$\pm$7 / 14$\pm$0.8 / 290$\pm$17 / 4.2$\pm$0.3 |
| HCN J=4-3 flux, IRAS 12127-1412 | 1.2 | 0.2 | Jy km/s | 3 | HCN J=4–3 / 1.1 (8.7$\sigma$) / 0.12 / 40 / 0.6 $\times$ 0.5 (59$^{\circ}$) / 39924$\pm$32 / 2.2$\pm$0.2 / 570$\pm$78 / 1.2$\pm$0.2 |
| HCO+ J=4-3 flux, IRAS 12127-1412 | 0.77 | 0.19 | Jy km/s | 3 | HCO$^{+}$ J=4–3 / 0.56 (5.2$\sigma$) / 0.11 / 30 / 0.6 $\times$ 0.5 (59$^{\circ}$) / 39985$\pm$42 / 1.5$\pm$0.2 / 570$\pm$110 / 0.77$\pm$0.19 |
| HCN J=4-3 flux, IRAS 22491-1808 | 7.6 | 0.5 | Jy km/s | 3 | HCN J=4–3 / 7.1 (38$\sigma$) / 0.19 / 34 / 0.6 $\times$ 0.6 (29$^{\circ}$) / 23297$\pm$9 / 18$\pm$1 / 420$\pm$21 / 7.6$\pm$0.5 |
| HCO+ J=4-3 flux, IRAS 22491-1808 | 5.4 | 0.4 | Jy km/s | 3 | HCO$^{+}$ J=4–3 / 4.7 (31$\sigma$) / 0.15 / 42 / 0.6 $\times$ 0.5 ($-$6$^\circ$) / 23296$\pm$16 / 9.4$\pm$0.5 / 570$\pm$35 / 5.4$\pm$0.4 |
| HCN J=4-3 flux, IRAS 00183-7111 | 0.78 | 0.42 | Jy km/s | 3 | HCN J=4–3 / 0.70 (3.9$\sigma$) / 0.18 / 41 / 2.4 $\times$ 1.2 (177$^{\circ}$) / 98576$\pm$100 / 1.6$\pm$0.6 / 620$\pm$230 / 0.78$\pm$0.42 |
| Molecular-line redshift of IRAS 22491-1808 | 0.0776 | not stated | dimensionless | 3 | Our molecular line data of dense gas tracers indicate $z =$ 0.0776, $\sim$500 km s$^{-1}$ redshifted. |

## Qualitative findings

- HCN/HCO+ J=4-3 flux ratios higher in buried AGN ULIRGs than in starburst NGC 1614; HCN/HNC ratios not clearly different  
  > "there is no clear difference in the HCN-to-HNC J=4–3 flux ratios among observed sources" (abstract)
- Observed HCN J=4-3 peak much lower than thermal expectation, indicating sub-thermal excitation  
  > "indicating that HCN is sub-thermally excited at J=4–3 even in our active ULIRG sample" (6.3 Implications)

## Claim tuples

- H: AGN-dominated ULIRGs show higher HCN/HCO+ J=4-3 ratios than starbursts | E: ALMA Band 6/7 observations of four ULIRGs, compared with NGC 1614 and IRAS 20551-4250 | R: Buried-AGN ULIRGs show higher HCN/HCO+ than NGC 1614 | F: Enhanced HCN/HCO+ J=4-3 may diagnose buried AGNs | **supported**
- H: HCN/HNC J=4-3 ratio distinguishes AGN from starburst | E: Compared HCN/HNC ratios | R: No clear difference | F: HCN/HNC not diagnostic here | **refuted**
- H: Starburst-type ULIRG IRAS 22491-1808 differs from AGN ULIRGs | E: Measured line ratios and widths | R: High HCN/HCO+ ratio with very large line widths | F: May be turbulence-induced heating | **partially**
- H: HCN J=4-3 is thermally excited | E: Compared observed peaks with J=1-0-based expectation | R: Observed peaks much smaller | F: HCN sub-thermally excited at J=4-3 | **supported**

## Reasoning

- Why this data: J=4-3 applicable to higher-z sources with ALMA than J=3-2 or J=1-0  
  > "Given that the J=4–3 line energy diagnostic is applicable to higher redshift sources than that of J=3–2 using ALMA, we selected J=4–3 line as our initial choice" (1 Introduction)
- Why this method: _not stated_
- Alternative: Band 6 J=3-2 lines considered but J=4-3 chosen  
  > "with the caution that the J=3–2 line could be better for detection if the excitation is significantly sub-thermal" (1 Introduction)
- How they decided it was enough: _not stated_
- Limitation (authors): Marginal 3.6 sigma HNC detection in IRAS 00183-7111 needs confirmation  
  > "the marginal (3.6$\sigma$) detection of the HNC emission in IRAS 00183$-$7111 requires further confirmation" (4 Results)
- Limitation (authors): Unconstrained clump physical properties cause largest uncertainty  
  > "the unconstrained physical properties of each molecular gas clump could cause the largest uncertainty" (6.2 Interpretation)
- Caveat (inferred, ours): Tiny sample of six galaxies, one starburst-LIRG comparison
- Caveat (inferred, ours): No flux-scale uncertainty included
- Caveat (inferred, ours): Several lines only 3-5 sigma with fixed FWHM
- Caveat (inferred, ours): Mechanisms not discriminated
- Caveat (inferred, ours): Gaussian fit at a single position, different beams among lines

## Reproducibility

- Data public (paper): Program 2011.0.00020.S cited  
  > "This paper made use of the following ALMA data: ADS/JAO.ALMA#2011.0.00020.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: CLEAN parameters
- Missing: CASA version
- Missing: line-free channel ranges
- Missing: moment map velocity ranges
- Missing: calibrator flux values
- Data volume (inferred): tens of GB
- Score (inferred): 3/5, Data are archival and tables are numeric, but imaging parameters are not given.
- Rediscovery candidate: no, Imaging recipe and parameters too sparse for a faithful redo.

## Links

- Method: Solomon & Vanden Bout 2005 (cite: sol05) (line luminosity equations)
- Companion: Imanishi & Nakanishi 2013a (cite: ima13a) (NGC 1614 ALMA results)
- Companion: Imanishi & Nakanishi 2013b (cite: ima13b) (IRAS 20551-4250 ALMA results)
- Related: IRAS 1Jy sample

## Checks

```json
{
 "quotes": 67,
 "quotes_ok": 67,
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
  "facts": 88,
  "stated": 49,
  "rate": 0.557
 },
 "evidence_ok": true
}
```
