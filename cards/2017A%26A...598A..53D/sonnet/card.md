# Search for aluminium monoxide in the winds of oxygen-rich AGB stars

`2017A&A...598A..53D` | Astronomy and Astrophysics 2017 | first author: De Beck, E. | arXiv: 1611.05409 | DOI: 10.1051/0004-6361/201628928

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: evolved_stars, astrochemistry
- Question: Is gas-phase AlO detectable at long wavelengths in the winds of oxygen-rich AGB stars, and where in the wind does it trace?  
  > "The detection at long wavelengths of emission in rotational transitions of AlO towards asymptotic giant branch stars can help constrain the presence and location of AlO gas in the outflows" (abstract)
- Target **R Aqr**: coordinates _not stated_; z/distance 214 pc  
  > "R Aqr is a Mira pulsator at a distance $d=214$ pc" (4.1 Overview of the sample); distance from _not stated_
- Target **o Cet**: coordinates _not stated_; z/distance 92 pc  
  > "o Cet is nearby ($d=92$ pc)" (4.1 Overview of the sample); distance from _not stated_
- Target **IK Tau**: coordinates _not stated_; z/distance ~265 pc  
  > "IK Tau is a relatively nearby ($d\approx265$ pc) Mira pulsator" (4.1 Overview of the sample); distance from _not stated_

## Data provenance

- ALMA projects: 2012.1.00524.S
- bands: CO J=3-2 setup covering AlO N=9-8 at ~344.4 GHz  
  > "The spectral setup of the observations covers the AlO ($N=9-8$) transition at $\sim$344.4 GHz." (ALMA)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: o Cet 0.64"x0.42"; R Aqr 0.38"x0.32"  
  > "The observations of o Cet have a synthesised beam size of $0.64\ensuremath{''}\times0.42\ensuremath{''}$, those of R Aqr$0.38\ensuremath{''}\times0.32\ensuremath{''}$." (ALMA)
- max recoverable scale: _not stated_
- sensitivity: integrated-intensity map rms 0.15 Jy/beam (o Cet), 0.075 Jy/beam (R Aqr)  
  > "have rms noise levels of 0.15 Jy beam$^{-1}$ (o Cet) and 0.075 Jy beam$^{-1}$ (R Aqr)." (ALMA)
- time on source: _not stated_
- observing dates: o Cet 25 Feb + 3 May 2014; R Aqr 21 May 2015  
  > "| R Aqr | $9-8$ | 344451.8 | 82.8 | 3.4 | 0.075$^{d}$ | 0.014$^{d}$ | 0.134$^{d}$ | $0.38\times0.32$ | ALMA | 21 May 2015 |" (Table 1)
- pi or archival as stated: _not stated_
- Line: AlO N=9-8 (344451.8 MHz)
- Other facility **APEX**: AlO N=5-4 to 9-8 spectra of R Dor, N=6-5 of WX Psc  
  > "The $N=5-4,\dots,9-8$ transitions were observed towards R Dor" (APEX)
- Other facility **IRAM 30m**: N=3-2, 4-3 of IK Tau and WX Psc  
  > "towards two oxygen-rich stars, IK Tau and WX Psc, with the IRAM 30 m telescope" (IRAM 30 m)
- Other facility **Herschel/HIFI**: N=20-19 and 29-28 spectra of seven stars  
  > "The $N=20-19$ and $N=29-28$ transitions of AlO at 764.603 GHz and 1106.980 GHz, respectively, were observed towards several evolved stars" (Herschel/HIFI)
- Other facility **SMA**: IK Tau N=8-7, 9-8 from a spectral survey  
  > "Within the framework of a spectral survey of IK Tau in the range $279-355$ GHz" (SMA)
- External data: AlO hyperfine line strengths and frequencies from JPL database  
  > "which is specified in the entries for AlO in the JPL database for molecular spectroscopy" (Aluminium monoxide: AlO) [from (cite: pickett1998_jpl)]
- External data: Stellar distances and mass-loss rates  
  > "at distances $d=380$ pc and $d=176$ pc, respectively (cite: maercker2016_water)" (4.1 Overview of the sample) [from (cite: maercker2016_water)]

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

- ALMA calibration and reduction procedures  
  > "Some first results on o Cet and a description of the data calibration and reduction procedures have been presented by (cite: ramstedt2014_mira)." (ALMA) [from (cite: ramstedt2014_mira)]
- SMA observing, calibration and reduction  
  > "we refer to (cite: debeck2013_po_pn) and (cite: kaminski2013_vycma_sma)." (SMA) [from (cite: debeck2013_po_pn); (cite: kaminski2013_vycma_sma)]
- Synthetic hyperfine-profile method  
  > "Following the example of (cite: kaminski2013_vycma_sma; kaminski2016_omicet), we can construct synthetic profiles" (4.2 Velocity of the AlO gas) [from (cite: kaminski2013_vycma_sma; kaminski2016_omicet)]

### Not stated but needed to reproduce (our reading)

- ALMA calibration details, CASA version, imaging parameters (weighting, cell, masks)
- Integration window for the integrated-intensity maps
- Frequency/velocity resolution and continuum subtraction channels
- Rotational-diagram fitting details

## Analysis recipe

1. **Fit hyperfine synthetic line profiles**: Sum of Gaussians per HFS component scaled by JPL line strengths; FWHM chosen by visual inspection  
  > "From a visual inspection of the synthetic profiles produced for $FWHM$ in the range $0.5-25.0$ km s$^{-1}$(in steps of 0.5 km s$^{-1}$)" (4.2 Velocity of the AlO gas)
   - parameter: FWHM grid 0.5-25 km/s in 0.5 km/s steps  
  > "in the range $0.5-25.0$ km s$^{-1}$(in steps of 0.5 km s$^{-1}$)" (4.2 Velocity of the AlO gas)
   - assumption: Optically thin, LTE; same FWHM for all HFS components  
  > "The same intrinsic line width, characterised by the full-width at half-maximum ($FWHM$) of the Gaussian, is assumed for all hyperfine components" (4.2 Velocity of the AlO gas)
   - fitting: _not stated_
   - validation: _not stated_
2. **Rotational diagram for IK Tau**: Rotational-diagram analysis of integrated intensities of ground-based data  
  > "we perform a rotational-diagram analysis of the integrated intensities." (4.4 AlO around IK Tau)
   - parameter: Emitting region 75 mas diameter (~20 AU radius); outflow velocity 5 km/s; Mdot 1e-5 Msun/yr  
  > "an emitting region of 75 mas (in diameter; $\sim$20 AU in radius)" (4.4 AlO around IK Tau)
   - assumption: Optically thin LTE emission  
  > "Assuming optically thin emission that is excited under local thermal equilibrium (LTE) conditions" (4.4 AlO around IK Tau)
   - fitting: _not stated_
   - validation: Authors caution non-LTE may invalidate results  
  > "we should hence interpret our results with particular care." (4.4 AlO around IK Tau)

## Software

- **GILDAS/CLASS** : Reduction of IRAM and APEX data  
  > "Data reduction was carried out using the GILDAS/CLASS[^3] package." (IRAM 30 m)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| AlO FWHM, o Cet | 4.5 | 1.0 | km/s | 1 | we suggest best-fit values for $FWHM$ of $4.5\pm1.0$ km s$^{-1}$ and $5.0\pm1.0$ km s$^{-1}$ for o Cet and R Aqr, respectively. |
| AlO FWHM, R Aqr | 5.0 | 1.0 | km/s | 1 | we suggest best-fit values for $FWHM$ of $4.5\pm1.0$ km s$^{-1}$ and $5.0\pm1.0$ km s$^{-1}$ for o Cet and R Aqr, respectively. |
| IK Tau AlO column density | 3.6e16 | 3.2e16 | cm^-2 | 2 | we derive a column density $N_{\mathrm{col}}=3.6\pm3.2\times10^{16}$ cm$^{-2}$. |
| IK Tau rotational temperature | 16.6 | 4.8 | K | 2 | We derive a rotational temperature $T_{\mathrm{rot}}=16.6\pm4.8$ K. |
| IK Tau AlO/H2 | 9.5e-8 | 8.4e-8 | dimensionless | 2 | AlO/H$_2$ $\approx 9.5\pm8.4\times 10^{-8}$ |
| AlO N=9-8 S/N in integrated intensity, R Aqr | ~18 | not stated | dimensionless | 0 | The emission reaches a signal-to-noise ratio $S/N\approx18$ in integrated intensity |

## Qualitative findings

- AlO N=9-8 emission is unresolved and traces the inner wind (few tens of AU) where gas is not yet accelerated to terminal velocity  
  > "the AlO ($N=9-8$) emission likely traces the inner parts of the wind, out to only a few tens of AU" (abstract)

## Claim tuples

- H: AlO gas is present at long wavelengths in O-rich AGB winds | E: Mined archival APEX, IRAM, HIFI, SMA, ALMA spectra of eight stars | R: Definite detections for o Cet and R Aqr; tentative for IK Tau, W Hya, R Dor; non-detections for WX Psc, R Cas, TX Cam | F: AlO is present in the gas phase in AGB outflows | **supported**
- H: AlO emission is confined to the inner wind | E: Synthetic HFS profile fits of ALMA spectra | R: FWHM ~5 km/s, emitting radius limited to ~20-35 AU | F: AlO traces the inner wind before acceleration | **supported**
- H: Detection rate correlates with wind properties | E: Compare detections across mass-loss rates | R: Detections and non-detections at both low and high densities | F: No firm correlation can be concluded | **partially**

## Reasoning

- Why this data: Data originally for other species were mined for AlO  
  > "These projects were not targeted at detecting AlO emission in particular" (3 Observations)
- Why this method: _not stated_
- Alternative: Stacking R Dor spectra rejected because HFS components do not align  
  > "the hyperfine structure components of the different AlO transitions do not align in frequency space, making stacking to confirm low-level detections less reliable." (4.1 Overview of the sample)
- How they decided it was enough: _not stated_
- Limitation (authors): Inhomogeneous data not aimed at AlO; low sensitivity; LTE optically thin assumption likely invalid  
  > "the observations are not homogeneous across the sample of eight stars" (3 Observations)
- Caveat (inferred, ours): FWHM chosen by visual inspection without a formal fit
- Caveat (inferred, ours): Rotational-diagram result based on few low-S/N points and doubtful LTE
- Caveat (inferred, ours): ALMA reduction details are deferred to another paper

## Reproducibility

- Data public (paper): ALMA project acknowledged; HIFI from Herschel Science Archive; public status of others not stated  
  > "We retrieved the most recent level-2 products of the observations present in the Herschel Science Archive" (Herschel/HIFI)
- Products in archive: _not stated_
- Missing: ALMA calibration/imaging parameters
- Missing: Integration velocity ranges
- Missing: Access to non-ALMA proprietary data
- Data volume (inferred): ~10-50 GB for ALMA raw data of two sources
- Score (inferred): 2/5, ALMA role minor; processing deferred to other papers; visual fitting.
- Rediscovery candidate: no, Recipe incomplete and multi-facility, not all public.

## Links

- Method: (cite: ramstedt2014_mira) (ALMA calibration and reduction of o Cet data)
- Method: (cite: kaminski2013_vycma_sma) (Synthetic HFS profile method and SMA reduction)
- Companion: (cite: kaminski2016_omicet) (Detailed AlO study of o Cet)
- Related: HIFISTARS

## Checks

```json
{
 "quotes": 42,
 "quotes_ok": 42,
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
  "facts": 72,
  "stated": 30,
  "rate": 0.417
 },
 "evidence_ok": true
}
```
