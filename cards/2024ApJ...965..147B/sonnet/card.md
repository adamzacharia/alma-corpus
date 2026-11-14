# The Carbon Isotopic Ratio and Planet Formation

`2024ApJ...965..147B` | The Astrophysical Journal 2024 | first author: Bergin, Edwin A. | arXiv: 2403.09739 | DOI: 10.3847/1538-4357/ad3443

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: protoplanetary_disks, astrochemistry
- Question: What is the 12C/13C ratio in C2H in the TW Hya disk, does it differ from that in CO, and can thermochemical models with isotopic fractionation produce two separate carbon isotopic reservoirs?  
  > "We confirm that the TW Hya gaseous disk exhibits two separate carbon isotopic reservoirs as noted previously (cite: Yoshida22)." (abstract)
- Target **TW Hya**: coordinates _not stated_; z/distance d = 60.1 pc  
  > "assuming $i = 6.8\ensuremath{^\circ}$, ${\rm PA} = 151\ensuremath{^\circ}$, $M_{\rm star} = 0.6~M_{\rm sun}$ and $d = 60.1~{\rm pc}$" (2.1 C$_2$H); distance from _not stated_

## Data provenance

- ALMA projects: 2013.1.00198.S, 2015.1.00308.S
- bands: _not stated_
- frequencies and spectral setup: Three line windows at 336.571, 351.060, 349.346 GHz, 467 MHz each; continuum window at 338.769 GHz, 2 GHz  
  > "The correlators were set to have three-line windows centered on 336.571, 351.060, and 349.346 GHz, and each window had a bandwidth of 467 MHz." (2.2 $^{13}$CCH)
- continuum bandwidth: 2 GHz at 338.769 GHz  
  > "A fourth spectral window was dedicated to continuum observations, centering on 338.769 GHz with a band width of 2 GHz." (2.2 $^{13}$CCH)
- arrays: _not stated_
- configurations: _not stated_
- baselines: 15 to 704 m, 42 antennas  
  > "The array included 42 antennas, with baselines lengths spanning from 15 to 704 m." (2.2 $^{13}$CCH)
- angular resolution: 13CCH 0.32" x 0.30" PA 4.4 deg; C2H 0.50" x 0.41" PA 59.0 deg  
  > "The resulting images have a beam of $0.50\ensuremath{''} \times 0.41\ensuremath{''}$ with a position angle of $59.0\ensuremath{^\circ}$." (2.1 C$_2$H)
- max recoverable scale: _not stated_
- sensitivity: 3.6 mJy/beam per 210 m/s channel (13CCH)  
  > "The final $^{13}$CCH image has a noise level of $3.6~{\rm mJy \, beam^{-1}}$ per $210~{\rm m\,s^{-1}}$ channel" (2.2 $^{13}$CCH)
- time on source: 49 minutes  
  > "The total on-source time was 49 minutes." (2.2 $^{13}$CCH)
- observing dates: 13CCH: November 23, 2016  
  > "The $^{13}$CCH line observations of TW Hya were carried out by ALMA on November 23, 2016 (2015.1.00308.S)." (2.2 $^{13}$CCH)
- pi or archival as stated: _not stated_
- Line: C2H N=4-3, J=9/2-7/2, F=5-4 (not stated)
- Line: 13CCH N=4-3, J=9/2-7/2, F1=5-4 (F2=11/2-9/2 and 9/2-7/2) (not stated)
- External data: C2H ALMA data and imaging (2013.1.00198.S)  
  > "We refer the reader to the original article for details on the data reduction and imaging." (2.1 C$_2$H) [from Bergin et al. 2016 (cite: Bergin16)]
- External data: CO 12C/13C ratio 21±5 at 70-110 au  
  > "| 70 – 110 | / | 21$^{+5}_{-5}$ | (cite: Yoshida22) |" (Table 1) [from (cite: Yoshida22)]
- External data: Other TW Hya 12C/13C ratios (Zhang17, Hily-Blant19, Yoshida24)  
  > "| $<$ 60 | / | 86$^{+4}_{-4}$ | (cite: Hily-Blant19) |" (Table 1) [from (cite: Zhang17; Hily-Blant19; Yoshida24)]
- Simulation/model as data: DALI thermochemical models of TW Hya, late-stage (zeta=1e-19 s-1) and early-stage (zeta=5e-17 s-1), run for 1 Myr, with the Miotello14 isotope network  
  > "we use the Dust And LInes thermochemical model (DALI) code (cite: Bruderer12; Bruderer13)." (3 Model)

## Processing

### Calibration

- pipeline or manual: Raw data calibrated by NRAO staff; then phase-only self-calibration  
  > "The raw visibility data were calibrated by NRAO staff members in CASA version 4.7.0, and we further applied phase-only self-calibration" (2.2 $^{13}$CCH)
- casa version: CASA 4.7.0  
  > "calibrated by NRAO staff members in CASA version 4.7.0" (2.2 $^{13}$CCH)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J1107+4449 (flux); J1037-2934 gain; J1058+0133 bandpass as ordered  
  > "The Nearby Quasars J1037-2934, J1058+0133, J1107+4449 were used for gain, bandpass, and flux calibration, respectively." (2.2 $^{13}$CCH)
- flux scale uncertainty: _not stated_
- self calibration: Phase-only, using the continuum spw and line-free channels of the line spws  
  > "phase-only self-calibration on the data using the continuum spectral window and line-free channels in all three-line spectral windows" (2.2 $^{13}$CCH)

### Imaging

- task: CLEAN  
  > "Fourier inverted to generate images by using the CLEAN task with a Briggs weight of 0.5." (2.2 $^{13}$CCH)
- deconvolver: _not stated_
- weighting robust: Briggs 0.5  
  > "CLEAN task with a Briggs weight of 0.5" (2.2 $^{13}$CCH)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: Keplerian mask for C2H integrated map  
  > "made using a Keplerian mask assuming $i = 6.8\ensuremath{^\circ}$" (2.1 C$_2$H)
- multiscale scales: _not stated_
- continuum subtraction: C2H: linear continuum model, uvcontsub  
  > "modeling the continuum contribution as a linear component around the line emission and using the `uvcontsub` task to remove this in the image plane" (2.1 C$_2$H)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.32" x 0.30", PA 4.4 deg  
  > "a beam size of $0.32\ensuremath{''} \times 0.30\ensuremath{''}$ with a position angle of $4.4\ensuremath{^\circ}$" (2.2 $^{13}$CCH)
- final rms: 3.6 mJy/beam per 210 m/s channel  
  > "noise level of $3.6~{\rm mJy \, beam^{-1}}$ per $210~{\rm m\,s^{-1}}$ channel" (2.2 $^{13}$CCH)

### Inherited from earlier work

- C2H data reduction and imaging  
  > "We refer the reader to the original article for details on the data reduction and imaging." (2.1 C$_2$H) [from (cite: Bergin16)]
- Disk-averaged spectrum extraction method  
  > "`GoFish` (cite: GoFish) which implements the method presented in (cite: Yen16)" (2.2 $^{13}$CCH) [from (cite: GoFish); (cite: Yen16)]
- JvM correction scripts  
  > "Using the scripts released as part of the MAPS Large Program (cite: Oberg21) to apply a correction" (2.1 C$_2$H) [from (cite: CZekala_ea_2021); (cite: Oberg21)]
- DALI TW Hya model  
  > "We use the extant TW Hya model published by (cite: Trapman17) and (cite: Bosman19_twhya)." (3 Model) [from (cite: Trapman17); (cite: Bosman19_twhya)]
- Flux uncertainty method  
  > "where the uncertainties have been calculated following (cite: Teague19)" (2.1 C$_2$H) [from (cite: Teague19)]

### Not stated but needed to reproduce (our reading)

- Image size, cell size, deconvolver, threshold and masking for CLEAN of 13CCH
- Line-free channels used for self-calibration and solint
- Rest frequencies and hyperfine line parameters
- Velocity integration limits for line fluxes
- Flux calibrator flux values
- Full DALI chemical network files and grid setup

## Analysis recipe

1. **Integrated C2H flux**: Keplerian-masked moment-0 map; integrated over disk and annulus 0.52-1.68 arcsec; uncertainties following Teague19  
  > "Integrating over the whole disk yields a total integrated flux of $6.17 \pm 1.16~{\rm Jy~km\,s^{-1}}$" (2.1 C$_2$H)
   - software: CASA
   - parameter: i=6.8 deg, PA=151 deg, Mstar=0.6 Msun, d=60.1 pc  
  > "$i = 6.8\ensuremath{^\circ}$, ${\rm PA} = 151\ensuremath{^\circ}$, $M_{\rm star} = 0.6~M_{\rm sun}$ and $d = 60.1~{\rm pc}$" (2.1 C$_2$H)
   - fitting: _not stated_
   - validation: JvM correction gives 5% and 2% differences in flux and peak  
  > "Calculating the integrated flux density and peak intensity with the JvM-corrected data found discrepancies of 5% and 2%, respectively." (2.1 C$_2$H)
2. **Extract 13CCH stacked spectrum**: Shift spectra by Keplerian velocity, stack in annuli 0.52-1.68 arcsec weighted by area, integrate  
  > "the spectrum in each pixel was shifted to the systemic velocity by applying a shift of $\delta v(r,\,\phi) = -v_{\rm kep}(r) \, \cos \phi \, \sin i$" (2.2 $^{13}$CCH)
   - software: GoFish
   - parameter: Annulus width 1/4 beam FWHM (~80 mas); weights proportional to r^2; centre offset (-52, -155) mas  
  > "As each annulus has a fixed width of 1/4 of the beam FWHM (${\sim}~80~{\rm mas}$), the weights are simply proportional to $r^2$." (2.2 $^{13}$CCH)
   - assumption: 13CCH radial profile follows C2H  
  > "Assuming that the radial emission profile of $^{13}$CCH follows that of C$_2$H" (2.2 $^{13}$CCH)
   - fitting: Gaussian fits to line peaks  
  > "From Gaussian fits to the line, the peak intensity values for the bright annulus region" (2.2 $^{13}$CCH)
   - validation: JvM correction 1% flux difference; radii varied to maximise S/N  
  > "The integrated flux density was not found to substantially vary compared to the native data, finding only a 1% difference." (2.2 $^{13}$CCH)
3. **Derive C2H/13CCH ratio**: Ratio of integrated flux (and peak) densities, assuming optically thin, correcting 11% A-coefficient difference  
  > "the integrated flux density ratio is essentially equivalent to the overall column density ratio correcting for an 11% difference in the A-coefficents" (3.1)
   - assumption: C2H optically thin  
  > "the C$_2$H emission in TW Hya is optically thin" (3.1)
   - fitting: _not stated_
   - validation: Peak-flux ratio 78±15 consistent with integrated ratio  
  > "we find a C$_2$H / $^{13}$CCH ratio of $78 \pm 15$, consistent with the integrated flux approach" (3.1)
4. **Model carbon isotope fractionation**: DALI late-stage and early-stage disk models with isotope network, vertical cuts at 63 au  
  > "we use the Dust And LInes thermochemical model (DALI) code (cite: Bruderer12; Bruderer13)" (4)
   - software: DALI
   - parameter: zeta 1e-19 (late) vs 5e-17 s-1 (early); small-grain fraction 1% vs 10%; run 1 Myr; initial 12C/13C 77  
  > "We also include the presence of cosmic rays ($\zeta_{\rm H_2} = 5 \times 10^{-17}$ s$^{-1}$)." (4.2)
   - assumption: C/O ~2 late-stage, half of gas carbon in CH4; early stage ISM CO 2.7e-4  
  > "we assume C/O $\sim$2 based on the analysis from C$_2$H" (4.1)
   - fitting: No fitting of emission levels  
  > "In our efforts we will not fit the overall emission levels" (4)
   - validation: Compared model ratios with observed CO and C2H ratios  
  > "The gaseous CO isotopic ratio estimated from column density ratios at 63 au is 79 which is well above the observed value of 21." (Model and Results (Late-Stage Model))

## Software

- **CASA** 4.7.0: Calibration and imaging  
  > "calibrated by NRAO staff members in CASA version 4.7.0" (2.2 $^{13}$CCH)
- **GoFish** : Disk-averaged spectrum extraction  
  > "we use the Python package `GoFish` (cite: GoFish)" (2.2 $^{13}$CCH)
- **DALI** : Thermochemical modelling  
  > "Dust And LInes thermochemical model (DALI) code" (4)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| 13CCH integrated flux, bright annulus | 56.9 | 14.1 | mJy km/s | 2 | yields an integrated flux of $56.9 \pm 14.1~{\rm mJy~km\,s^{-1}}$ |
| C2H integrated flux, annulus | 4.20 | 0.68 | Jy km/s | 1 | we find $4.20 \pm 0.68~{\rm Jy~km\,s^{-1}}$ |
| C2H/13CCH flux ratio, bright annulus | 74 | 22 | dimensionless | 3 | we find a C$_2$H / $^{13}$CCH ratio of $74 \pm 22$ in the bright annulus |
| N(CCH)/N(13CCH) | 65 | 20 | dimensionless | 3 | N(CCH)/N($^{13}$CCH) = 65$\pm$20 |
| Model CO 12C/13C at 63 au, late stage | 79 | not stated | dimensionless | 4 | The gaseous CO isotopic ratio estimated from column density ratios at 63 au is 79 |
| Model C2H ratio, late stage | 78 | not stated | dimensionless | 4 | The gaseous C$_2$H isotopic ratio estimated from column density ratios is 78 |
| Early-stage model CO 12C/13C | ~50 | not stated | dimensionless | 4 | $^{13}$CO gas becomes modestly enriched with $^{12}$C/$^{13}$C $\sim$ 50 |

## Qualitative findings

- Two carbon isotopic reservoirs exist in TW Hya: CO 13C-enriched and C2H not  
  > "We confirm that the TW Hya gaseous disk exhibits two separate carbon isotopic reservoirs" (abstract)

## Claim tuples

- H: C2H traces excess carbon with an isotopic ratio different from CO | E: Detect 13CCH and compare C2H/13CCH with CO ratio | R: 65±20 vs 21±5 | F: Two isotopic reservoirs confirmed | **supported**
- H: A present-day low-ionization disk model can create two reservoirs | E: DALI late-stage model | R: CO ratio 79 vs observed 21 | F: Cannot reproduce | **refuted**
- H: An early-stage disk with interstellar cosmic rays can create two reservoirs | E: DALI early-stage model | R: 13C-rich CO (~50), 12C-rich methane ice | F: Produces dichotomy but weaker than observed | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Late-stage model without excess CH4 gave no significant fractionation and C2H reduced by 3 orders of magnitude  
  > "This model did not produce significant carbon isotopic fractionation of CO or C$_2$H." (4.1)
- How they decided it was enough: _not stated_
- Limitation (authors): Models do not fully match observations; CO enrichment only 50 vs 20  
  > "Our models also do not fully match observations." (5.2)
- Caveat (inferred, ours): 13CCH detection only ~4 sigma
- Caveat (inferred, ours): Optically thin assumption for C2H only argued indirectly
- Caveat (inferred, ours): Models not fit to data; single radius; no cosmic ray alternatives explored

## Reproducibility

- Data public (paper): Project codes acknowledged; archival data  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2013.1.00198.S," (Acknowledgments)
- Products in archive: _not stated_
- Missing: Imaging parameters beyond robust
- Missing: Full DALI model inputs
- Data volume (inferred): ~50-100 GB
- Score (inferred): 3/5, Data public and extraction method clear, but imaging details and DALI setup rely on prior papers.
- Rediscovery candidate: yes, Public data, stacking recipe described, numeric flux and ratio results.

## Links

- Method: (cite: GoFish) (Spectrum extraction code)
- Method: (cite: CZekala_ea_2021) (JvM correction)
- Companion: (cite: Bergin16) (Original C2H data)
- Companion: (cite: Yoshida22) (CO isotope ratio)
- Related: MAPS

## Checks

```json
{
 "quotes": 67,
 "quotes_ok": 67,
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
  "facts": 76,
  "stated": 51,
  "rate": 0.671
 },
 "evidence_ok": true
}
```
