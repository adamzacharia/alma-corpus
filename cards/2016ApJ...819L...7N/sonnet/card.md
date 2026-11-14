# ALMA Observations of a Gap and a Ring in the Protoplanetary Disk around TW Hya

`2016ApJ...819L...7N` | The Astrophysical Journal Letters 2016 | first author: Nomura, Hideko | arXiv: 1512.05440 | DOI: 10.3847/2041-8205/819/1/L7

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks, astrochemistry
- Question: Does the TW Hya disk show a gap and ring in 336 GHz dust continuum, how do they relate to the CO snow line, and how depleted is CO in the disk?  
  > "which show the presence of a gap and a ring associated with the CO snow line." (Introduction)
- Target **TW Hya**: coordinates _not stated_; z/distance 54±6 pc  
  > "TW Hya’s proximity (54$\pm$6 pc) makes it an ideal source to study" (Introduction); "assuming an inclination angle of $7^{\circ}$ and a position angle of $-30^{\circ}$" (Dust Continuum Emission); distance from Andrews12 (cited with the distance statement)  
  > "TW Hya’s proximity (54$\pm$6 pc) makes it an ideal source to study" (Introduction); "assuming an inclination angle of $7^{\circ}$ and a position angle of $-30^{\circ}$" (Dust Continuum Emission)

## Data provenance

- ALMA projects: 2013.1.01397.S, 2011.0.00340.S
- bands: Band 7  
  > "TW Hya was observed with ALMA in Band 7 on 20-21 May, 2015 with 40 antennas in Cycle 2" (Observations and Data Reduction)
- frequencies and spectral setup: SPW centers 329.295, 330.552, 340.211, 342.846 GHz; 30.52 kHz channels, 117.188 MHz bandwidth (SPW2: 15.26 kHz, 58.594 MHz)  
  > "The channel spacing was $\delta \nu=$30.52kHz and the bandwidth was 117.188MHz except for SPW 2" (Observations and Data Reduction)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: uv-coverage 22-580 kλ  
  > "with a uv-coverage of 22-580 k$\lambda$ (PI: D. Ishimoto)" (Observations and Data Reduction)
- angular resolution: 0.37x0.31 arcsec (~20 AU) full; 0.32x0.26 arcsec (~15 AU) for >200 kλ  
  > "0.”37$\times$0.”31 ($\sim 20$AU, $P.A.=55.7^{\circ}$) and 0.23mJy beam$^{-1}$" (Dust Continuum Emission)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: 20-21 May 2015  
  > "TW Hya was observed with ALMA in Band 7 on 20-21 May, 2015" (Observations and Data Reduction)
- pi or archival as stated: PI D. Ishimoto (2013.1.01397.S); N2H+ from ALMA archive  
  > "Also, the ALMA archived data of N$_2$H$^+$ $J=4-3$ line at 372.672GHz were reanalysed in a similar way" (Observations and Data Reduction)
- Line: C18O J=3-2 (not stated)
- Line: 13CO J=3-2 (not stated)
- Line: N2H+ J=4-3 (372.672 GHz)
- External data: Dust temperature profile Td=22K(R/10AU)^-0.3 from model fit  
  > "We adopt $T_{d}=22K(R/{\rm 10AU})^{-0.3}$, where $R$ is the disk radius, by fitting the model result in (cite: Andrews12)" (Dust Surface Density and Gap Parameters) [from (cite: Andrews12)]
- External data: Inclination 7 deg and PA -30 deg  
  > "assuming an inclination angle of $7^{\circ}$ and a position angle of $-30^{\circ}$" (Dust Continuum Emission) [from (cite: Qi08)]
- External data: Isotopologue ratios CO:13CO=67:1, 13CO:C18O=7:1 and CO/H2 = 6e-5  
  > "the abundance ratios of CO $: ^{13}$CO$=$67 $:$ 1 and $^{13}$CO $:$ C$^{18}$O$=$7 $:$ 1 (cite: Qi11)" (CO Column Density) [from (cite: Qi11)]

## Processing

### Calibration

- pipeline or manual: Calibration of bandpass, gain amplitude and phase, flux scaling, flagging; continuum self-calibration, solutions applied to lines  
  > "The obtained solution table of the self-calibration for the continuum emission was applied to the visibilities of the lines." (Observations and Data Reduction)
- casa version: CASA 4.3.1 and 4.4.0  
  > "CASA, version 4.3.1 and 4.4.0." (Observations and Data Reduction)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: Continuum self-cal improved rms from 2.6 to 0.23 mJy  
  > "The self-calibration significantly improved the sensitivity of the continuum image by one order of magnitude from 2.6 to 0.23mJy." (Observations and Data Reduction)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: Briggs robust = 0 (full); uniform weighting for >200 kλ data  
  > "imaged using the CLEAN algorithm with Briggs weighting with a robust parameter of 0" (Observations and Data Reduction); "imaged using the CLEAN algorithm with uniform weighting." (Observations and Data Reduction)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: Continuum from averaging line-free channels in all SPWs  
  > "the continuum visibilities were extracted by averaging the line-free channels in all SPWs" (Observations and Data Reduction)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: Line profiles smoothed to 0.45x0.45 arcsec beam  
  > "All data are smoothed to a beam size of 0.”45$\times$0.”45." (Figure 4 caption)
- final beam: 0.37x0.31 arcsec continuum; 0.41x0.33 arcsec lines  
  > "0."41$\times$0."33 ($P.A.=53.4^{\circ}$), 12.0mJy beam$^{-1}$ ($^{13}$CO)" (CO Isotopologue Line Emission)
- final rms: 0.23 mJy/beam continuum (0.49 for >200 kλ)  
  > "were 0.”32$\times$0.”26 ($\sim 15$AU, $P.A.=54.5^{\circ}$) and 0.49mJy beam$^{-1}$." (Results, Dust Continuum Emission)

### Inherited from earlier work

- N2H+ archival data reanalysed consistent with earlier published result  
  > "The re-analysed data is consistent with that in (cite: Qi13)." (Observations and Data Reduction) [from (cite: Qi13)]

### Not stated but needed to reproduce (our reading)

- Line-free channel ranges
- CLEAN threshold, masks, cell and image size
- Self-calibration solution intervals and number of iterations
- Flux calibrator and flux scale uncertainty
- Gas-phase temperature profile data and radial bin widths
- Exact deprojection centre

## Analysis recipe

1. **Calibrate and image continuum**: CASA calibration, self-calibration, CLEAN imaging full data and >200 kλ data  
  > "the continuum visibility data with deprojected baselines longer than 200k$\lambda$ was extracted in order to enhance small scale structure around the gap." (Observations and Data Reduction)
   - software: CASA
   - fitting: _not stated_
   - validation: Compared with Andrews12, Hogerheijde15, Zhang16  
  > "Our result is consistent with the recent ALMA observations with higher spatial resolution and sensitivity (cite: Zhang16)." (Dust Continuum Emission)
2. **Derive dust surface density**: Invert I=B(Td)[1-exp(-tau)] on deprojected profile  
  > "$$\begin{equation} I_{d, \nu}=B_{\nu}(T_d)[1-\exp(-\tau_{d, \nu})], \label{eq_dust} \end{equation}$$" (Dust Surface Density and Gap Parameters)
   - assumption: kappa=3.4 cm^2/g; Td=22K(R/10AU)^-0.3, vertically uniform  
  > "the dust opacity, $\kappa_{\nu}$, is set as $\kappa_{\nu}=3.4$ cm$^2$ g$^{-1}$." (Dust Surface Density and Gap Parameters)
   - fitting: _not stated_
   - validation: Consistent with SMA-derived surface density and spectral-index colour temperature  
  > "the derived dust surface density distribution is consistent with that derived from" (Dust Surface Density and Gap Parameters)
3. **Gap width and depth**: Power-law plus Gaussian fit to high-frequency profile, add Gaussian deficit to full-data profile to recover missing flux  
  > "(iii) obtain the intensity at the gap as $I_{\rm gap}=I^{\rm full}-\Delta I_{\rm gap}$, where $I^{\rm full}$ is the intensity of the full data." (Dust Surface Density and Gap Parameters)
   - parameter: Gap edges 9-13 AU inner, 39-43 AU outer  
  > "we adopted the edges of the gap at $R=9-13$AU (inner edge) and $39-43$ AU (outer edge)" (Dust Surface Density and Gap Parameters)
   - fitting: Gaussian fit to gap; no sampler stated  
  > "(ii) fit the gap region in the high frequency data using a single Gaussian profile of" (Results, Dust Surface Density and Gap Parameters)
   - validation: _not stated_
4. **CO column density and gas-to-dust ratio**: Three-zone radiative transfer for C18O+continuum, Tg from 13CO peak Tb, derive N_CO and compare with dust  
  > "we adopt the brightness temperature at the peak of the $^{13}$CO line (Fig. 5) as the gas temperature, $T_g$." (CO Column Density)
   - assumption: CO/H2 = 6e-5; isotopologue ratios from Qi11; uniform vertical Tg  
  > "assuming an abundance ratio of CO to H$_2$ of $6\times 10^{-5}$ (cite: Qi11)" (CO Gas-to-Dust Surface Density Ratio)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.3.1 and 4.4.0: Calibration and CLEAN imaging  
  > "The visibility data were reduced and calibrated using" (Observations and Data Reduction)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Gap radius | 25 | not stated | AU | 3 | The gap and ring are located at around 25 and 41 AU from the central star |
| Ring radius | 41 | not stated | AU | 3 | The gap and ring are located at around 25 and 41 AU from the central star |
| Gap Gaussian FWHM | 13.9 | 1.0 | AU | 3 | whose FWHM is $13.9\pm 1.0$AU and depth is $7.7\pm 0.5$mJy |
| Gap depth (Sigma0-Sigma)/Sigma0 | ~0.23 | not stated | dimensionless | 3 | the depth is $(\Sigma_0-\Sigma)/\Sigma_0\sim 0.23$ |
| Total continuum flux density | 1.41 | not stated | Jy | 1 | The total and peak flux density were 1.41Jy and 0.15Jy beam$^{-1}$ |
| CO column density | ~1e18 | not stated | cm^-2 | 4 | $N_{\rm CO}\sim 10^{18}$cm$^{-2}$ |
| H2 gas-to-dust surface density ratio | ~0.1-1 | not stated | dimensionless | 4 | The resulting H$_2$ gas-to-dust surface density ratio ($\sim 0.1-1$) |

## Qualitative findings

- CO is depleted throughout the disk down to ~10 AU, likely freeze-out and surface reactions  
  > "show a decrement in CO line emission throughout the disk, down to $\sim$ 10AU" (abstract)

## Claim tuples

- H: Does TW Hya have a gap and ring in dust continuum? | E: Imaging of Band 7 continuum, with >200 kλ subset | R: Gap at ~25 AU and ring at ~41 AU | F: Gaps/rings exist in old disks, near the CO snow line | **supported**
- H: Is CO depleted in the disk? | E: 13CO and C18O column densities vs dust | R: H2 gas-to-dust ratio ~0.1-1 | F: Strong CO depletion down to ~10 AU | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Gap origin: planet below super-Neptune mass or CO ice sintering  
  > "or could be the result of the destruction of large dust aggregates due to the sintering of CO ice." (abstract)
- How they decided it was enough: _not stated_
- Limitation (authors): Gap width and depth limited by resolution and artefacts from 200 kλ cut  
  > "We note that our estimate of the gap width is limited by the angular resolution of the high spatial frequency data." (Dust Surface Density and Gap Parameters)
- Caveat (inferred, ours): Gap parameters depend on ad hoc 200 kλ cut and flux completion
- Caveat (inferred, ours): Assumed single Td and Tg profiles and opacity drive derived densities
- Caveat (inferred, ours): CO column likely underestimated

## Reproducibility

- Data public (paper): Archive codes given  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2013.1.01397.S and ADS/JAO.ALMA#2011.0.00340.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Self-cal parameters
- Missing: CLEAN masks and thresholds
- Missing: Line-free channels
- Data volume (inferred): ~50-100 GB
- Score (inferred): 3/5, Public data and clear equations, but imaging and self-cal details are missing.
- Rediscovery candidate: yes, Public data, numeric gap parameters, mostly specified recipe.

## Links

- Companion: (cite: Zhang16) (Higher resolution ALMA TW Hya continuum)
- Companion: (cite: Okuzumi15) (CO ice sintering model)
- Related: HL Tau long baseline campaign

## Checks

```json
{
 "quotes": 54,
 "quotes_ok": 54,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 66,
  "stated": 36,
  "rate": 0.545
 },
 "evidence_ok": true
}
```
