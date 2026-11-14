# ALMA Observations of Supernova Remnant N49 in the LMC. I. Discovery of CO Clumps Associated with X-Ray and Radio Continuum Shells

`2018ApJ...863...55Y` | The Astrophysical Journal 2018 | first author: Yamane, Y. | arXiv: 1806.10390 | DOI: 10.3847/1538-4357/aacfff

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, milky_way_ism
- Question: How do molecular and atomic gas, radio continuum and X-rays relate in the LMC supernova remnant N49, and what does this say about shock-cloud interaction, synchrotron enhancement and recombining plasma?  
  > "we investigate the physical relations among the molecular/atomic clouds, radio continuum, and X-rays to understand the origins of the synchrotron radio emission and the recombining plasma." (Introduction)
- Target **N49 (LHA 120-N49)**: coordinates RA 5h26m01s, Dec -66d05m06s (J2000)  
  > "its distance has been determined to be 50 $\pm$ 1.3 kpc[^1] (cite: 2013Natur.495...76P)" (Introduction); z/distance 50 kpc (LMC)  
  > "its distance has been determined to be 50 $\pm$ 1.3 kpc[^1] (cite: 2013Natur.495...76P)" (Introduction); distance from (cite: 2013Natur.495...76P)  
  > "its distance has been determined to be 50 $\pm$ 1.3 kpc[^1] (cite: 2013Natur.495...76P)" (Introduction)

## Data provenance

- ALMA projects: _none stated_
- bands: Band 3 (86–116 GHz)  
  > "We carried out ALMA Cycle 3, Band 3 (86–116 GHz) observations (P.I., Jacco Th. van Loon)" (2.1.3 ALMA)
- frequencies and spectral setup: CO(1-0) window 234.4 MHz (141.1 kHz x 3840 channels); continuum window 1875 MHz  
  > "with a bandwidth of 234.4 MHz (141.1 kHz $\times$ 3840 channels)" (2.1.3 ALMA)
- continuum bandwidth: _not stated_
- arrays: ALMA 12-m array, 49 antennas  
  > "using 49 antennas of the ALMA 12-m array" (2.1.3 ALMA)
- configurations: _not stated_
- baselines: 13.0 to 282.7 m (5.0 to 108.6 kλ)  
  > "The baselines ranged from 13.0 to 282.7 m, corresponding to $u$–$v$ distances from 5.0 to 108.6 k$\lambda$." (2.1.3 ALMA)
- angular resolution: 3.2'' x 2.2'', PA 66.1 deg  
  > "The synthesized beam size was $\sim$$3.2\ensuremath{''}$ $\times$ $2.2\ensuremath{''}$" (2.1.3 ALMA)
- max recoverable scale: _not stated_
- sensitivity: rms ~8 mJy/beam (~0.07 K) at 0.4 km/s  
  > "the rms noise was $\sim$8 mJy beam$^{-1}$ ($\sim$0.07 K), with a velocity resolution of 0.4 km s$^{-1}$." (2.1.3 ALMA)
- time on source: _not stated_
- observing dates: January 12 and 18, 2016  
  > "The observations were carried out on January 12 and 18, 2016, through three spectral windows." (2.1.3 ALMA)
- pi or archival as stated: PI Jacco Th. van Loon  
  > "(P.I., Jacco Th. van Loon)" (2.1.3 ALMA)
- Line: 12CO J=1-0 (not stated)
- Other facility **Mopra**: 12CO(1-0) maps, beam ~45''  
  > "the final beam size of the datasets was $\sim$45$\ensuremath{''}$" (2.1.1 Mopra)
- Other facility **ASTE**: 12CO(3-2) maps  
  > "The $^{12}$CO($J$ = 3–2) observations were performed by using ASTE" (2.1.2 ASTE)
- Other facility **ATCA and Parkes**: HI 21 cm cube and 1.4 GHz continuum  
  > "they were obtained with ATCA and the Parkes radio telescope (C2908, PI: Kosuke Fujii)" (2.2 Hi and radio continuum)
- Other facility **Chandra**: archival ACIS-S X-ray images (108 ks)  
  > "The total exposure time was 108 ks." (2.3 X-rays)
- External data: HI data cube from unpublished work  
  > "The Hi 21 cm data are from K. Fujii et al. (2018, in preparation)" (2.2 Hi and radio continuum) [from K. Fujii et al. (2018, in preparation)]
- External data: Archival Magellanic Mopra Assessment CO data combined with Mopra data  
  > "we combined our data with the archived datasets from the Magellanic Mopra Assessment (cite: 2011ApJS..197...16W; 2017ApJ...850..139W)" (2.1.1 Mopra) [from (cite: 2011ApJS..197...16W; 2017ApJ...850..139W)]
- External data: Radio spectral index of N49 ~ -0.59 ± 0.03  
  > "the spectral index was measured to be $\sim$$-$0.59 $\pm$ 0.03 (cite: 2017ApJS..230....2B)" (3.3.1) [from (cite: 2017ApJS..230....2B)]
- External data: Suzaku N_H ~3.51e21 cm^-2 and recombining plasma results  
  > "$N_{\rm H}$ is $\sim$3.51 $\times$ 10$^{21}$ cm$^{-2}$ estimated by the integrated spectrum of N49 with $Suzaku$ (cite: 2015ApJ...808...77U)" (4.1) [from (cite: 2015ApJ...808...77U)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0519-4546 (flux); J0516-6207 phase; J0635-7516 gain  
  > "phase calibration on J0516–6207, and flux calibration on J0519–4546" (2.1.3 ALMA)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA, multi-scale CLEAN  
  > "We also applied the multi-scale CLEAN algorithm (cite: 2008ISTSP...2..793C) implemented in CASA." (2.1.3 ALMA)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "We applied the natural weighting to recover the weak extended emission." (2.1.3 ALMA)
- uv taper: _not stated_
- cell size: 0.5'' x 0.5'' pixel (from mass calculation)  
  > "square pixel (0$\ensuremath{''}$5 $\times$ 0$\ensuremath{''}$5)" (3.4)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 3.2'' x 2.2'', PA 66.1 deg  
  > "with a position angle of 66.1 degrees" (2.1.3 ALMA)
- final rms: ~8 mJy/beam (~0.07 K)  
  > "the rms noise was $\sim$8 mJy beam$^{-1}$ ($\sim$0.07 K)" (2.1.3 ALMA)

### Inherited from earlier work

- N(H2)=7.0e20 W(CO) conversion  
  > "We also used the following relationship between the molecular hydrogen column density $N$(H$_2$) and the $^{12}$CO($J$ = 1–0) integrated intensity $W$(CO) from (cite: 2008ApJS..178...56F):" (3.4) [from (cite: 2008ApJS..178...56F)]
- Mopra intensity calibration scale using Orion-KL  
  > "to be consistent with corrected peak CO brightness temperature of $T_\mathrm{XB} \sim 100$ K (cite: 2005PASA...22...62L)" (2.1.1 Mopra) [from (cite: 2005PASA...22...62L)]
- X-ray optical depth formula  
  > "According to (cite: 1994hea2.book.....L), the X-ray optical depth $\tau_{\rm x}$ is given by" (4.1) [from (cite: 1994hea2.book.....L)]

### Not stated but needed to reproduce (our reading)

- CASA version and whether archive pipeline products were used
- Multi-scale CLEAN scales, threshold, mask, niter
- Continuum subtraction and line-free channels
- Image size, final cube channel width details
- Primary beam correction
- How the missing-flux comparison handled ALMA/Mopra alignment
- Table of clump properties (positions) not in text
- Self-calibration status of ALMA data
- ALMA project code printed in paper

## Analysis recipe

1. **Image ALMA CO(1-0) cube**: CASA imaging with natural weighting and multi-scale CLEAN  
  > "We applied the natural weighting to recover the weak extended emission." (2.1.3 ALMA)
   - software: CASA
   - fitting: _not stated_
   - validation: ALMA flux ~3% smaller than Mopra when smoothed to 45'' over 282.9–288.7 km/s, so missing flux negligible  
  > "the ALMA data is $\sim3\%$ smaller than the single-dish data and thus the missing flux is considered to be negligible." (2.1.3 ALMA)
2. **Identify CO clumps**: Peaks above 5σ (0.48 K km/s) in 1.2 km/s channel maps from 281.4–288.6 km/s; merge peaks within 3.2'' with single-peaked spectra  
  > "a position of peak intensity above 0.48 K km s$^{-1}$ \[equal to the 5$\sigma$ level of the ALMA $^{12}$CO($J$ = 1–0) data\] is defined as an individual CO peak." (3.4)
   - fitting: _not stated_
   - validation: _not stated_
3. **Derive clump properties**: Single Gaussian fit to peak spectra; size from half-maximum contour area; virial and CO masses  
  > "derived from a single Gaussian fitting for CO spectra obtained at the peak positions of the CO clumps." (3.4)
   - parameter: M_vir = 210 R (ΔV)^2 Msun; mu = 2.38  
  > "We adopt $\mu$ = 2.38 to take into account the $\sim$36 % abundance by mass of helium relative to atomic hydrogen." (3.4)
   - assumption: N(H2) = 7.0e20 W(CO) cm^-2; distance 50 kpc  
  > "N({\rm H}_2) = 7.0 \times 10^{20} W({\rm CO}) ({\rm cm}^{-2})." (3.4)
   - fitting: _not stated_
   - validation: _not stated_
4. **Compare CO with X-ray and radio continuum**: Azimuthal and radial profiles; Pearson correlation; X-ray optical depth estimate  
  > "The linear Pearson correlation coefficients are $\sim$0.95 for the CO and soft X-rays" (3.2)
   - software: CIAO
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : ALMA imaging with multi-scale CLEAN  
  > "we used the Common Astronomy Software Applications package (cite: 2007ASPC..376..127M)" (2.1.3 ALMA)
- **Miriad** : ATCA data reduction  
  > "For all our ATCA data reduction, we used Miriad software (cite: 1995ASPC...77..433S)." (2.2 Hi and radio continuum)
- **CIAO** v4.9 (CALDB v4.7.6): Chandra reduction with chandra_repro and merge_obs  
  > "We reduced these observations using the CIAO v4.9 software package (cite: 2006SPIE.6270E..1VF) with CALDB v4.7.6." (2.3 X-rays)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Number of CO clumps | 21 | not stated | clumps | 2 | we identified 21 CO clumps and confirmed that all clumps have single-peaked spectra. |
| Total virial mass of clumps | 5.3e3 | not stated | Msun | 3 | The total virial mass of the CO clumps is $\sim$5.3 $\times$ $10^3$ $M_{\ensuremath{\odot}}$ |
| Total CO-derived mass | 1.9e3 | not stated | Msun | 3 | whereas the total CO-derived mass is $\sim$1.9 $\times$ $10^3$ $M_{\ensuremath{\odot}}$ |
| Clump FWHM line width range | 0.7–2.0 | not stated | km/s | 3 | the FWHM line width is 0.7–2.0 km s$^{-1}$ |
| Clump sizes | 0.9–2.0 | not stated | pc | 3 | The sizes of the CO clumps are 0.9–2.0 pc. |
| Pearson correlation CO vs soft X-rays | 0.95 | not stated | dimensionless | 4 | The linear Pearson correlation coefficients are $\sim$0.95 for the CO and soft X-rays |
| CO 3-2/1-0 ratio along SE rim | ~0.6 | not stated | dimensionless | 0 | We find the region with high-intensity ratios $\sim 0.6$ along the southeastern rim of N49 |
| Separation hard X-ray peak to CO clump L | ~0.6 | not stated | pc | 4 | the separation between the hard X-ray peak and CO clump L is $\sim$0.6 pc |

## Qualitative findings

- Blue-velocity (280–291 km/s) CO and HI clouds are associated with the SNR; middle and red HI clouds are in front.  
  > "We conclude that the blue-velocity CO/Hi clouds are likely to be associated with N49." (Summary)

## Claim tuples

- H: CO clumps interact with the SNR shock | E: Compare ALMA CO clumps with Chandra X-rays and ATCA radio continuum | R: Clumps J, K, L rim-brightened in hard X-rays and radio continuum on 0.7–2 pc scales | F: Dynamical interaction between clumps and shock | **supported**
- H: Clumps are in virial equilibrium | E: Compare virial and CO-derived masses | R: Virial mass ~3 times CO mass | F: Clumps may not be virialized, possibly perturbed by the shock | **partially**
- H: Recombining plasma forms via thermal conduction with cold clumps | E: Spatial comparison of hard X-rays with CO clumps | R: Hard X-rays enhanced around clumps J, K, L | F: Possible scenario, needs confirmation | **partially**

## Reasoning

- Why this data: LMC chosen to avoid line-of-sight contamination and distance uncertainty  
  > "We have therefore focused on the SNRs in the Large Magellanic Cloud (LMC) to avoid these problems." (Introduction)
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): No line broadening detected due to low sensitivity and low-excitation line data  
  > "we cannot find clear evidence for the suggested line broadening in our ALMA CO datasets because of low sensitivity and low excitation line data." (4.2)
- Caveat (inferred, ours): Single CO conversion factor assumed for LMC
- Caveat (inferred, ours): Clump-X-ray association is visual, no significance test
- Caveat (inferred, ours): Thermal-conduction scenario is speculative
- Caveat (inferred, ours): Virial mass depends on clump boundary definition

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: ALMA project code not printed in paper
- Missing: CASA version and CLEAN parameters
- Missing: HI data unpublished
- Missing: Clump table values not in text
- Data volume (inferred): ~10-50 GB for ALMA Band 3 12-m data, plus Chandra archive
- Score (inferred): 3/5, Clear clump identification and mass recipe, but CLEAN settings and several datasets are unspecified.
- Rediscovery candidate: no, Project code not printed and imaging parameters missing; HI data unpublished.

## Links

- Companion: K. Fujii et al. (2018, in preparation) (Source of the HI data)
- Related: Magellanic Mopra Assessment

## Checks

```json
{
 "quotes": 55,
 "quotes_ok": 55,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 0,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2015.1.01195.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 73,
  "stated": 42,
  "rate": 0.575
 },
 "evidence_ok": true
}
```
