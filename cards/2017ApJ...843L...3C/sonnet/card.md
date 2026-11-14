# Variable H<SUP>13</SUP>CO<SUP>+</SUP> Emission in the IM Lup Disk: X-Ray Driven Time-dependent Chemistry?

`2017ApJ...843L...3C` | The Astrophysical Journal Letters 2017 | first author: Cleeves, L. Ilsedore | arXiv: 1706.00833 | DOI: 10.3847/2041-8213/aa76e2

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks, astrochemistry
- Question: Does H13CO+ J=3-2 emission in the IM Lup disk vary in time relative to the continuum, and can X-ray flare driven chemistry explain it?  
  > "To explore one possible explanation for this newly discovered variability, we carry out simple models of time evolving X-ray irradiation of circumstellar disk material" (Introduction)
- Target **IM Lup**: coordinates _not stated_; z/distance 161 pc  
  > "assuming a distance of $d=161$ pc (cite: gaia)" (Swift XRT and UVOT Observations); distance from Gaia  
  > "assuming a distance of $d=161$ pc (cite: gaia)" (Swift XRT and UVOT Observations)

## Data provenance

- ALMA projects: 2013.1.00226.S
- bands: _not stated_
- frequencies and spectral setup: Channel width 244.141 kHz (0.28 km/s) after averaging; original 2014 data 61.035 kHz (0.07 km/s)  
  > "We channel-averaged the 17 July 2014 observations (61.035 kHz / 0.07 km s$^{-1}$) to match the spectral resolution of the latter two datasets, 244.141 kHz or 0.28 km s$^{-1}$" (2.1 ALMA Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: Min/max baselines 20.1-650.3 m, 15.1-348.5 m, 21.4-558.2 m for the three epochs  
  > "| 07/17/2014 | 20.1 m | 650.3 m |" (Table 1)
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: 21, 17 and 34 minutes for the 17 July 2014, 29 January 2015 and 13 May 2015 observations  
  > "The time spent on source was 21, 17, and 34 minutes for the 17 July 2014, 29 January 2015, and 13 May 2015 observations, respectively." (2.1 ALMA Observations)
- observing dates: 17 July 2014, 29 January 2015, 13 May 2015  
  > "The 2013.00694 observations were taken on 29 January 2015 (40 antennas) and 13 May 2015 (36 antennas)." (2.1 ALMA Observations)
- pi or archival as stated: Two programs: PI Öberg (2013.1.00226) and PI Cleeves (2013.00694)  
  > "project codes ADS/JAO.ALMA#2013.1.00226 (PI: Öberg) and ADS/JAO.ALMA#2013.00694 (PI: Cleeves)" (2.1 ALMA Observations)
- Line: H13CO+ J=3-2 (not stated)
- Other facility **Swift XRT and UVOT**: X-ray spectra/luminosities and UVM2 FUV fluxes of IM Lup over multiple epochs  
  > "The observations accumulated a total of 32.9 ks of XRT data in Photon Counting mode and 11.4 ks of UVOT in the UVM2 filter." (2.2 Swift XRT and UVOT Observations)
- External data: IM Lup disk physical model (density, temperature, UV, columns) used as chemical model input  
  > "The input physical parameters are drawn from the IM Lup model presented in (cite: cleeves2016b)." (3 X-ray Flare Chemical Models) [from (cite: cleeves2016b)]
- External data: Three plasma temperature components (0.3, 0.6, 2.1 keV) for IM Lup X-ray spectrum  
  > "three plasma components identified in (cite: gunther2010) at 0.3, 0.6 and 2.1 keV" (2.2 Swift XRT and UVOT Observations) [from (cite: gunther2010)]
- External data: HCO+ dissociative recombination rate coefficient  
  > "$\alpha = 2.8\times10^{-7} (T_{\rm gas} / 300~{\rm K})^{-0.69}$ cm$^{3}$ s$^{-1}$ (cite: amano1990)" (4 Model Results) [from (cite: amano1990)]
- Simulation/model as data: Time-dependent chemical models (5956 reactions, 644 species) at six disk locations with X-ray flares  
  > "The reaction network includes 5956 reactions and 644 species" (3 X-ray Flare Chemical Models)

## Processing

### Calibration

- pipeline or manual: Latter two observations processed by ALMA/NAASC staff; self-calibration applied  
  > "The latter two observations were processed by the ALMA/NAASC staff" (2.1 ALMA Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Titan set amplitude scale; J1517-2422 bandpass; J1610-3958 phase  
  > "the quasar J1517-2422 was used to calibrate the bandpass, J1610-3958 was used to calibrate the phases, and Titan set the amplitude scale" (2.1 ALMA Observations)
- flux scale uncertainty: _not stated_
- self calibration: 2013.00694 data self-calibrated with three rounds of phase calibration on disk continuum; 2013.1.00226 as in Öberg et al. 2015  
  > "the 2013.00694 data were both self-calibrated with three rounds of phase calibration on the disk continuum emission" (2.1 ALMA Observations)

### Imaging

- task: CASA clean; cvel for channel averaging  
  > "with the CASA task `cvel`. To correct for the beam differences, we imaged the data with `clean`" (2.1 ALMA Observations)
- deconvolver: _not stated_
- weighting robust: Natural weighting with UV taper  
  > "using a UV taper and natural weighting to produce a circular $1.4\ensuremath{''}$ beam" (2.1 ALMA Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: Same mask used in clean traces gas motion, used for spectra extraction  
  > "Disk-integrated spectra were extracted from the image cube with the same mask used in `clean`, which traces the gas motion." (2.1 ALMA Observations)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: circular 1.4 arcsec  
  > "to produce a circular $1.4\ensuremath{''}$ beam" (2.1 ALMA Observations)
- final rms: _not stated_

### Inherited from earlier work

- Analysis and self-calibration of the 2013.1.00226 data  
  > "the analysis was previously reported by (cite: oberg2015im), and will not be repeated here" (2.1 ALMA Observations) [from (cite: oberg2015im)]
- Simple grain surface chemistry  
  > "with simple grain surface chemistry as described in (cite: cleeves2014par)" (3 X-ray Flare Chemical Models) [from (cite: cleeves2014par)]

### Not stated but needed to reproduce (our reading)

- tclean/clean parameters (cell size, image size, taper value, clean threshold, mask definition)
- line-free channels and continuum subtraction details
- CASA version
- Rest frequency and velocity range for integration
- Elliptical annulus geometry for continuum flux
- Details of the HC18O+ data
- Swift observation IDs and exact epochs

## Analysis recipe

1. **Homogenize and image the three epochs**: Channel-average 2014 data with cvel and image all with clean using UV taper and natural weighting to a 1.4'' circular beam  
  > "we imaged the data with `clean` using a UV taper and natural weighting to produce a circular $1.4\ensuremath{''}$ beam" (2.1 ALMA Observations)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Measure disk-integrated line and continuum fluxes**: Sum spectra within the clean mask; continuum in elliptical annulus; RMS from line-free frequencies/off-source  
  > "The RMS uncertainty on the integrated flux was estimated with the same mask applied to line-free frequencies." (2.1 ALMA Observations)
   - software: CASA
   - fitting: _not stated_
   - validation: Checked scans and calibrator phase/amplitude; vis_sample test of UV coverage effect  
  > "We sampled the model with the same spatial frequencies of the ALMA observations using `vis_sample`" (2.1 ALMA Observations)
3. **Fit Swift X-ray spectra and derive LX**: Fit three fixed-temperature plasma components with free normalizations and absorption; integrate 1-10 keV  
  > "we fixed the temperatures of these three components and allow their normalizations and absorption column densities to vary" (2.2 Swift XRT and UVOT Observations)
   - software: HEASoft
   - assumption: d=161 pc; absorption not removed  
  > "We do not remove the absorption component in calculating the X-ray luminosity" (2.2 Swift XRT and UVOT Observations)
   - fitting: _not stated_
   - validation: _not stated_
4. **Time-dependent X-ray flare chemical models**: Evolve chemistry 0.5 Myr to steady state, then apply exponential-rise/decay flares and compute chemistry at 30 min intervals over two months at six disk points  
  > "We then “switch on” X-ray flares and compute the chemistry at 30 minute intervals over a two-month period." (3 X-ray Flare Chemical Models)
   - software: Fogel et al. 2011 chemical code, Bethell & Bergin Monte Carlo X-ray radiative transfer
   - parameter: Flares: 35x (tr=3h, td=5h), 80x (1h, 3h), 10x (10h, 30h)  
  > "a $35\times$ change in X-ray luminosity with $t_r=3$ hours and $t_d=5$ hours" (3 X-ray Flare Chemical Models)
   - assumption: No change in X-ray spectral shape during flares  
  > "we do not consider changes in the X-ray spectral shape (i.e., hardening)" (3 X-ray Flare Chemical Models)
   - fitting: _not stated_
   - validation: Steady state confirmed by no HCO+ change from 0.5 to 1 Myr  
  > "We confirm the model has reached steady state by examining no further chemical evolution in HCO$^+$ from 0.5 to 1 Myr." (3 X-ray Flare Chemical Models)
5. **Estimate electron density from HCO+ decay**: t_half = ln2/(alpha n_e) using recombination rate  
  > "such that the time for post-flare HCO$^+$ abundance to halve is" (4 Model Results)
   - assumption: T_gas = 100 K  
  > "assuming $T_{\rm gas} = 100$ K, $n_e$ is estimated to be $\sim2.7$ cm$^{-3}$" (4 Model Results)
   - fitting: _not stated_
   - validation: Compared to detailed chemical model value 3.3 cm^-3  
  > "where the value from the detailed chemical model is 3.3 cm$^{-3}$" (4 Model Results)

## Software

- **CASA** : cvel and clean imaging  
  > "with the CASA task `cvel`" (2.1 ALMA Observations)
- **vis_sample** : Sampling a model with observed UV coverage to test spatial filtering  
  > "We sampled the model with the same spatial frequencies of the ALMA observations using `vis_sample`" (2.1 ALMA Observations)
- **HEASoft** : Swift X-ray spectral fitting and uvotsource photometry  
  > "The photometric UVOT measurements were extracted using HEASoft with the `uvotsource` routine" (2.2 Swift XRT and UVOT Observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| H13CO+ J=3-2 disk-integrated flux, 17 Jul 2014 | 0.466 | 0.032 | Jy km/s | 2 | $0.466\pm0.032$ Jy km s$^{-1}$ |
| H13CO+ J=3-2 disk-integrated flux, 29 Jan 2015 | 0.590 | 0.020 | Jy km/s | 2 | $0.590\pm 0.020$ Jy km s$^{-1}$ |
| H13CO+ J=3-2 disk-integrated flux, 13 May 2015 | 1.254 | 0.019 | Jy km/s | 2 | $1.254 \pm 0.019$ Jy km s$^{-1}$ |
| 1.15 mm continuum flux, 13 May 2015 | 0.307 | 0.001 | Jy | 2 | $0.307 \pm 0.001$ Jy |
| Line-to-continuum ratio increase between last two epochs | 2.1 (28 sigma) | not stated | dimensionless | 2 | Between the latter two epochs the line-to-continuum ratio increased by a factor of 2.1, or $28\sigma$. |
| Swift X-ray luminosity range | (9.2±1.8)e29 to (4.5±0.9)e30 | 20% | erg/s | 3 | varied between $L_{\rm X} = (9.2\pm1.8)\times10^{29}$ erg s$^{-1}$ up to $L_{\rm X} = (4.5\pm0.9)\times10^{30}$ erg s$^{-1}$ |
| Electron density estimate at r=50 AU, z/r=0.5 | ~2.7 (detailed model 3.3) | factor of a few | cm^-3 | 5 | $n_e$ is estimated to be $\sim2.7$ cm$^{-3}$ from these equations |

## Qualitative findings

- Continuum constant while H13CO+ doubled, attributed to abundance change since line is optically thin  
  > "we find the H$^{13}$CO$^+$ line is consistent with being optically thin and hence attribute changes in flux to changes in the abundance" (2.3 Observed Features)

## Claim tuples

- H: H13CO+ emission varies in time independent of the continuum | E: Three-epoch ALMA observations with matched beam and UV-coverage tests | R: Line flux rose from 0.466 to 1.254 Jy km/s while continuum stayed ~0.3 Jy | F: Significant short-term chemical variability detected | **supported**
- H: X-ray flares can drive the HCO+ enhancement | E: Time-dependent chemical models with 10x-80x flares | R: HCO+ increases and persists days to a month | F: Strong or long-duration flares can potentially explain the brightening | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): No X-ray data during the ALMA event; spectral hardening not modeled  
  > "We do not have constraints on the shape of IM Lup’s X-ray spectrum during the ALMA event" (3 X-ray Flare Chemical Models)
- Caveat (inferred, ours): No simultaneous X-ray coverage, so the flare link is circumstantial
- Caveat (inferred, ours): Systematic UV-coverage flux differences comparable to the signal in some comparisons
- Caveat (inferred, ours): Only an explanation by model; other causes are not excluded

## Reproducibility

- Data public (paper): Archive-linked ALMA projects; Swift public data acknowledged  
  > "we acknowledge the use of public data from the Swift data archive" (Acknowledgments)
- Products in archive: _not stated_
- Missing: Imaging parameters and masks
- Missing: Chemical code configuration and exact model inputs
- Data volume (inferred): ~10-50 GB across three epochs
- Score (inferred): 3/5, Data identified and main fluxes tabulated, but imaging/model details are incomplete.
- Rediscovery candidate: yes, ALMA data are archival, and line and continuum fluxes are numeric, though imaging details are underspecified.

## Links

- Method: (cite: fogel2011) (Chemical code)
- Method: (cite: bethell2011u) (X-ray radiative transfer)
- Companion: (cite: oberg2015im) (Analysis of the 2014 ALMA data)
- Companion: (cite: cleeves2016b) (IM Lup disk model)

## Checks

```json
{
 "quotes": 52,
 "quotes_ok": 52,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2013.1.00694.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 74,
  "stated": 40,
  "rate": 0.541
 },
 "evidence_ok": true
}
```
