# Atacama Compact Array observations of the pulsar-wind nebula of SNR 0540-69.3

`2020MNRAS.496.1834L` | Monthly Notices of the Royal Astronomical Society 2020 | first author: Lundqvist, P. | arXiv: 2006.05222 | DOI: 10.1093/mnras/staa1675

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, milky_way_ism
- Question: What is the synchrotron spectrum of the PWN of SNR 0540-69.3 from radio through mm to UV/IR, how does it join at higher frequencies, and is there room for dust in the PWN?  
  > "To better constrain the continuum emission from PWN0540, we have obtained data from the Atacama Compact Array (ACA) in Bands 4 and 6" (Introduction); "There is room for $2.5\times10^{-3} ~{\rm M}_\odot$ of dust with temperature $\sim 55$ K" (abstract)
- Target **SNR 0540-69.3 / PWN0540 (PSR B0540-69.3)**: coordinates _not stated_; z/distance 50 kpc (LMC)  
  > "corresponding to $\sim 4.9-8.5$ pc at the 50 kpc distance of LMC" (Introduction); distance from LMC distance, (cite: man93b; GW00)  
  > "corresponding to $\sim 4.9-8.5$ pc at the 50 kpc distance of LMC" (Introduction)

## Data provenance

- ALMA projects: 2017.1.01391.S
- bands: ACA Band 4 (145 GHz) and Band 6 (223.5 GHz)  
  > "using ACA in Band 4 (145 GHz) and Band 6 (223.5 GHz)" (2.2 ACA observations)
- frequencies and spectral setup: four 128-channel spws per band, 1.875 GHz usable each, centred 138,140,150,152 GHz (Band 4) and 214.5,216.5,230.5,232.5 GHz (Band 6)  
  > "The four spws were centred at 138, 140, 150 and 152 GHz for Band 4 and 214.5, 216.5, 230.5 and 232.5 GHz for Band 6." (2.2 ACA observations)
- continuum bandwidth: 7.5 GHz total usable  
  > "The spectral setup covered a total usable bandwidth of 7.5 GHz" (2.2 ACA observations)
- arrays: ACA, 10-11 7-m antennas  
  > "the array consisted of 10–11 7-m antennas" (2.2 ACA observations)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: Band 4: 10.79x8.33 arcsec; Band 6: 7.52x5.18 arcsec  
  > "$10\hbox{$.\!\!^{\prime\prime}$}79\times8\hbox{$.\!\!^{\prime\prime}$}33~(84\hbox{$.\!\!^\circ$}09)$" (Table 2)
- max recoverable scale: _not stated_
- sensitivity: rms 0.291 mJy (Band 4), 0.348 mJy (Band 6)  
  > "| 4 | 145 | $30.97\pm1.58$ | 0.291 |" (Table 2)
- time on source: 438.5 s (Band 4), 665.3 s (Band 6)  
  > "The total on-source integration times were 438.5 seconds and 665.3 seconds, in Bands 4 and 6, respectively." (2.2 ACA observations)
- observing dates: 2018 March 19 (Band 4), 2018 March 25 (Band 6)  
  > "The data were obtained on 2018 March 19 and 2018 March 25 for Bands 4 and 6, respectively" (2.2 ACA observations)
- pi or archival as stated: PI P. Lundqvist, own proposal  
  > "ALMA Program 2017.1.01391.S, PI: P. Lundqvist" (Footnote 2)
- Other facility **ATCA 3 cm**: 8.64 GHz high-resolution radio image (Program C014, 1995)  
  > "These data were obtained 1995 Oct. 23–24 UT under ATCA Program C014." (2.1 ATCA obsevations)
- Other facility **AKARI**: 2.5-28.7 micron catalogue photometry  
  > "Processed data were retrieved from the AKARI-LMC Point Source Catalogue" (2.3 AKARI observations)
- Other facility **Spitzer, HST, VLT/NACO (literature)**: published IR/optical/UV flux densities  
  > "References: (1) (cite: bra14), (2) This paper, (3) (cite: Williams08), (4) (cite: Mignani12), (5) (cite: serf04)." (Table 4)
- External data: Radio integrated flux densities of PWN (1.5-8.6 GHz)  
  > "References: (1) (cite: bra14), (2) This paper, (3) (cite: Williams08), (4) (cite: Mignani12), (5) (cite: serf04)." (Table 4) [from (cite: bra14)]
- External data: Spitzer MIPS/IRAC flux densities and line fluxes  
  > "we included the Spitzer IRAC IR data from (cite: Williams08)" (3.2 Fluxes in the ACA and AKARI bands) [from (cite: Williams08)]
- External data: VLT/NACO and HST optical/UV flux densities  
  > "the VLT/NACO data of (cite: Mignani12)" (4 Discussion) [from (cite: Mignani12); (cite: serf04)]
- External data: Dust mass absorption coefficients  
  > "interpolated $\kappa_{\lambda}$ and $\beta$ in temperature using the results reported by (cite: men98)" (4 Discussion) [from (cite: men98)]

## Processing

### Calibration

- pipeline or manual: ALMA Pipeline-calibrated uv-data used; own imaging  
  > "We used the calibrated uv-data delivered by ALMA, which was calibrated using the ALMA Pipeline" (2.2 ACA observations)
- casa version: CASA 5.4.0  
  > "using CASA version 5.4.0" (2.2 ACA observations)
- pipeline version: _not stated_
- archive products used as is: No; delivered images under-cleaned, re-imaged  
  > "the delivered image products were under-cleaned" (2.2 ACA observations)
- flux calibrator: _not stated_
- flux scale uncertainty: 5% Band 4, 10% Band 6  
  > "which is estimated to be 5% for Band 4 and 10% for Band 6" (3.2 Fluxes in the ACA and AKARI bands)
- self calibration: Band 4: several phase-only rounds 300 s down to 30 s, then amplitude 30 s; Band 6: one phase and one amplitude round, 300 s  
  > "For the Band 6 data, we performed one round each of phase-only and amplitude self-calibration, with a time interval of 300 seconds." (2.2 ACA observations)

### Imaging

- task: CASA tclean, continuum over full 7.5 GHz  
  > "using the CASA task TCLEAN with Briggs weighting and a Robust = 0.5 weighting of the visibilities" (2.2 ACA observations)
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 0.5  
  > "using the CASA task TCLEAN with Briggs weighting and a Robust = 0.5 weighting of the visibilities" (2.2 ACA observations)
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
- final beam: Band 4 10.79x8.33 arcsec; Band 6 7.52x5.18 arcsec  
  > "$7\hbox{$.\!\!^{\prime\prime}$}52\times5\hbox{$.\!\!^{\prime\prime}$}18~(-83\hbox{$.\!\!^\circ$}60)$" (Table 2)
- final rms: 0.291 mJy/beam (Band 4); 0.348 mJy/beam (Band 6)  
  > "For Band 6 the corresponding numbers are 19.33 mJy beam$^{-1}$ and 0.348 mJy beam$^{-1}$, respectively." (3.2 Fluxes in the ACA and AKARI bands)

### Inherited from earlier work

- Monte Carlo power-law index and uncertainty method  
  > "were estimated using the same method as in (cite: serf04)" (4 Discussion) [from (cite: serf04)]
- 3-cm ATCA data first presented and reduced earlier; PWN 3-cm integrated flux taken from earlier work  
  > "We have used the 3-cm data first presented in (cite: dick02) and subsequently in (cite: bra14)." (2.1 ATCA obsevations) [from (cite: dick02); (cite: bra14)]
- X-ray and optical images and alignment  
  > "The X-ray and optical images are from our previous study in (cite: nlun11)." (3.1 Morphology revealed by ACA and ATCA) [from (cite: nlun11)]

### Not stated but needed to reproduce (our reading)

- CLEAN threshold, niter, masks, image size and cell size for the ACA tclean imaging
- Exact self-calibration solint sequence for Band 4 intermediate rounds and reference antenna
- Per-pixel definition of PWN area and shell masks used in the smearing experiment
- Power-law fit method details (fit weights) beyond Monte Carlo description
- Pulsar coordinates and ATCA/ACA alignment offsets
- Interpolated kappa and beta values for forsterite dust
- Whether flux in Table 4 for ACA is from peak times correction or integrated aperture

## Analysis recipe

1. **Image ACA continuum**: Re-imaged pipeline-calibrated data with deeper cleaning and self-calibration  
  > "we performed our own imaging to improve signal-to-noise and image quality" (2.2 ACA observations)
   - software: CASA, tclean
   - parameter: Briggs robust = 0.5, 7.5 GHz bandwidth  
  > "Briggs weighting and a Robust = 0.5 weighting of the visibilities" (2.2 ACA observations)
   - fitting: _not stated_
   - validation: Self-calibration raised Band 4 S/N by ~2 over deeper cleaning alone  
  > "Self-calibration produced a factor of about two improvement in the S/N for the Band 4 data compared to deeper cleaning alone" (2.2 ACA observations)
2. **Correct peak flux to integrated PWN flux**: Compared observed image to normalized point-source (beam) model; for Band 4 subtracted smeared 3-cm shell image (constants A, B) before computing correction  
  > "We then normalized the peak flux density of this image to the observed image for each band." (3.2 Fluxes in the ACA and AKARI bands)
   - parameter: correction factors ~1.50 (Band 6), 1.05 (Band 4 after shell removal); A/B = 3.8±0.2  
  > "In our analysis we arrive at $A/B = 3.8\pm0.2$" (3.2 Fluxes in the ACA and AKARI bands)
   - assumption: Intrinsic structures at 3 cm and mm are similar  
  > "The residuals are found to be consistent with noise, which means that the intrinsic structures are similar at 3 cm" (3.2 Fluxes in the ACA and AKARI bands)
   - fitting: A and B tuned to give zero net flux at PWN and SNR positions  
  > "The difference was tuned through the constants $A$ and $B$ to achieve zero net flux density at the positions of the PWN and SNR, respectively." (3.2 Fluxes in the ACA and AKARI bands)
   - validation: 3-cm image smeared with Band 6 beam and subtracted gives residuals consistent with noise  
  > "The residuals are found to be consistent with noise" (3.2 Fluxes in the ACA and AKARI bands)
3. **Fit synchrotron power laws**: Power-law fits to radio/mm and IR/UV flux densities, excluding line-contaminated HST filters  
  > "we have discarded HST filters which encapsulate strong nebular lines from our analysis" (4 Discussion)
   - parameter: 10 000 simulated data sets, 500 seeds averaged, 68% bounds  
  > "We did this 500 times with different seed values for the randomizer" (4 Discussion)
   - assumption: Gaussian flux uncertainties; frequencies uniform within bins  
  > "the flux uncertainty is assumed to have a Gaussian distribution, and the frequency distribution to be evenly distributed within the frequency bins" (4 Discussion)
   - fitting: Monte Carlo power-law fits, median taken as index  
  > "assigned the median value to be the preferred $\alpha_{\nu,{\rm radio/mm}}$" (4 Discussion)
   - validation: _not stated_
4. **Derive break, B field and dust mass**: Intersect power laws for break; equate synchrotron lifetime to age for B; optically thin forsterite dust emission model  
  > "The dust emission was calculated assuming optically thin forsterite dust." (4 Discussion)
   - parameter: remnant age 1100 yr; D = 50 kpc; T_dust = 55 K  
  > "assumed to be 1 100 years (cite: rey85)" (4 Discussion)
   - assumption: Small silicate (forsterite) grains, kappa from Mennella et al.  
  > "We have assumed small-sized dust particles" (4 Discussion)
   - fitting: _not stated_
   - validation: Compared with Williams et al. 2008 dust model  
  > "Our dust mass estimate is consistent with the $\sim 3\times10^{-3} ~{\rm M}_\odot$ of silicate dust" (4 Discussion)

## Software

- **CASA** 5.4.0: reduction and imaging of ACA data (tclean, self-cal)  
  > "using CASA version 5.4.0" (2.2 ACA observations)
- **MIRIAD** 1.0: reduction, CLEAN and RESTOR of ATCA 3-cm data  
  > "The data were reduced using MIRIAD version 1.0" (2.1 ATCA obsevations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| radio/mm spectral index 1.449-233.5 GHz | 0.17 | 0.02 | dimensionless | 3 | the spectral index $\alpha_{\nu} = 0.17\pm{0.02}$ |
| UV/IR spectral index | 0.87 | +0.08/-0.10 | dimensionless | 3 | we arrive at $\alpha_{\nu} = 0.87^{+0.08}_{-0.10}$ |
| SNR shell spectral index 8.6-145 GHz | 0.64 | 0.05 | dimensionless | 3 | we derive $\alpha_{\nu} = 0.64\pm{0.05}$ for the range $8.6-145$ GHz |
| Band 4 peak flux density | 30.97 | 1.58 | mJy/beam | 1 | / 4 / 145 / $30.97\pm1.58$ / 0.291 / |
| Band 6 peak flux density | 19.33 | 1.96 | mJy/beam | 1 | / 6 / 223.5 / $19.33\pm1.96$ / 0.348 / |
| magnetic field from break | 3.9e-4 | +1.1/-0.7 e-4 | G | 4 | $B = (3.9^{+1.1}_{-0.7}) \times10^{-4}$ G |
| dust mass | 2.5e-3 | not stated | Msun | 4 | There is room for $2.5\times10^{-3} ~{\rm M}_\odot$ of dust with temperature $\sim 55$ K |

## Qualitative findings

- PWN is partially resolved in ACA Band 6 and the SNR shell is detected in Band 4; strong emission 1.5 arcsec SW of pulsar persists at mm  
  > "The ACA data clearly reveal the supernova remnant shell $\sim 20-35 \ensuremath{''}$ west of the pulsar" (abstract)

## Claim tuples

- H: Does the flat radio spectrum continue into the mm? | E: Fit power law to radio plus ACA integrated fluxes | R: alpha = 0.17±0.02 over 1.449-233.5 GHz | F: Flat synchrotron spectrum continues to mm, with possible break near 9e10 Hz | **supported**
- H: Is there room for dust in PWN0540? | E: Compare dual-break synchrotron fit with 24 micron excess | R: 2.5e-3 Msun of ~55 K dust fits | F: Dust allowed if dual breaks, but line contamination is a more likely cause of excess | **partially**
- H: Does the SNR shell have a steeper spectrum than the PWN? | E: Subtract smeared 3-cm shell and PWN templates from Band 4 | R: alpha_SNR - alpha_PWN = 0.47±0.03; alpha_SNR 0.64±0.05 | F: Shell steeper than PWN, consistent with radio | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: 3-cm data used as template because PWN is only partially resolved and emission is uneven  
  > "The reason for this modelling is the uneven spatial distribution of emission seen in the PWN at many wavelengths." (Introduction)
- Alternative: HST filters containing strong nebular lines were discarded from continuum fits  
  > "we have discarded HST filters which encapsulate strong nebular lines from our analysis" (4 Discussion)
- How they decided it was enough: _not stated_
- Limitation (authors): Band 6 cannot reliably trace the shell; deeper image needed  
  > "but a deeper image is needed to draw firm conclusions" (3.1 Morphology revealed by ACA and ATCA)
- Caveat (inferred, ours): Integrated mm fluxes depend on a 3-cm template assumption and point-source correction
- Caveat (inferred, ours): Dust mass degenerate with synchrotron break choice and line contamination
- Caveat (inferred, ours): Spectral fits mix archival data from different epochs (1995-2018) for a variable nebula

## Reproducibility

- Data public (paper): ALMA program cited; ATCA program C014 and AKARI catalogue referenced  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2017.1.01391.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: tclean parameters (threshold, niter, masks, image size, cell)
- Missing: exact shell/PWN masks and A,B tuning procedure
- Missing: literature flux tables must be gathered from cited papers
- Data volume (inferred): ~ few GB (two ACA Band 4/6 datasets) plus small ATCA data
- Score (inferred): 3/5, Public ACA data and clear flux pipeline, but many imaging and template-modelling details unstated and heavy reliance on literature fluxes.
- Rediscovery candidate: no, Imaging details and mask choices are incomplete and results depend on literature data and manual tuning.

## Links

- Method: (cite: serf04) (Monte Carlo power-law fitting method)
- Companion: (cite: bra14) (Radio flux densities and spectral indices of PWN and shell)
- Companion: (cite: Williams08) (Spitzer data and dust model)
- Companion: (cite: Mignani12) (UV/optical/NIR photometry)
- Related: AKARI LMC survey

## Checks

```json
{
 "quotes": 68,
 "quotes_ok": 68,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 77,
  "stated": 54,
  "rate": 0.701
 },
 "evidence_ok": true
}
```
