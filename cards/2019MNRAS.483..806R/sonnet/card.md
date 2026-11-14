# First ALMA maps of HCO, an important precursor of complex organic molecules, towards IRAS 16293-2422

`2019MNRAS.483..806R` | Monthly Notices of the Royal Astronomical Society 2019 | first author: Rivilla, V. M. | arXiv: 1811.01650 | DOI: 10.1093/mnras/sty3078

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: astrochemistry, star_formation
- Question: Where and how is the formyl radical HCO formed in IRAS 16293-2422 (envelope gas-phase vs hot corino grain surface), and what is its role as precursor of H2CO, CH3OH and glycolaldehyde?  
  > "We also present different chemical models to understand the formation of HCO itself, and its role in the formation of more complex species such as glycolaldehyde." (1 Introduction)
- Target **IRAS 16293-2422 (sources A and B)**: coordinates RA=16h 32m 22.62s, DEC=-24d 28m 32.46s (phase center)  
  > "IRAS 16293$-$2422 (hereafter IRAS16293) is a low-mass protostellar system located at a distance of 141$^{+31}_{-21}$ pc ((cite: dzib2018))." (1 Introduction); "The phase center was RA=16h 32m 22.62s, DEC=-24$^{\circ}$ 28$^{\prime}$ 32.46$^{\prime\prime}$." (2 Observations); z/distance 141 +31/-21 pc  
  > "IRAS 16293$-$2422 (hereafter IRAS16293) is a low-mass protostellar system located at a distance of 141$^{+31}_{-21}$ pc ((cite: dzib2018))." (1 Introduction); "The phase center was RA=16h 32m 22.62s, DEC=-24$^{\circ}$ 28$^{\prime}$ 32.46$^{\prime\prime}$." (2 Observations); distance from Dzib et al. 2018  
  > "IRAS 16293$-$2422 (hereafter IRAS16293) is a low-mass protostellar system located at a distance of 141$^{+31}_{-21}$ pc ((cite: dzib2018))." (1 Introduction); "The phase center was RA=16h 32m 22.62s, DEC=-24$^{\circ}$ 28$^{\prime}$ 32.46$^{\prime\prime}$." (2 Observations)

## Data provenance

- ALMA projects: 2015.1.01193.S
- bands: Band 3 (3 mm)  
  > "The observations were performed in Band 3 (3 mm) with the array in a configuration with baselines ranging from 15 m to 783 m." (2 Observations)
- frequencies and spectral setup: Four spws: 86.58-87.05, 88.50-88.97, 99.00-99.23, 101.10-101.57 GHz; 0.72-0.84 km/s resolution  
  > "| 0 | 86.58-87.05 | 1.45$\times$1.04 | 0.84 | 2.0 |" (Table 1); "| 3 | 101.10-101.57 | 1.25$\times$0.90 | 0.72 | 2.3 |" (Table 1)
- continuum bandwidth: _not stated_
- arrays: 40 antennas  
  > "using 40 antennas of the Atacama Large Millimeter/Submillimeter Array (ALMA)" (2 Observations)
- configurations: _not stated_
- baselines: 15 m to 783 m  
  > "with the array in a configuration with baselines ranging from 15 m to 783 m" (2 Observations)
- angular resolution: synthesized beams ~1.25-1.45 x 0.90-1.04 arcsec per spw; continuum 1.09x0.78 arcsec  
  > "has a synthesized beam of 1.09$\ensuremath{''}\times$0.78$\ensuremath{''}$" (3.1 Continuum)
- max recoverable scale: ~12 arcsec  
  > "We note that these ALMA observations had a maximum recoverable scale of $\sim$12$\ensuremath{''}$." (3.2.2 Comparison with single-dish data)
- sensitivity: rms 1.4-2.3 mJy per channel  
  > "| 2 | 99.00-99.23 | 1.28$\times$0.92 | 0.74 | 1.4 |" (Table 1)
- time on source: about 70 min  
  > "The on-source observing time was about 70 min." (2 Observations)
- observing dates: 11 June 2016, Cycle 3  
  > "in Cycle 3 in June 11 2016" (2 Observations)
- pi or archival as stated: Own program, PI Rivilla  
  > "as part of the project 2015.1.01193.S (PI Rivilla)" (2 Observations)
- Line: HCO 1_0,1-0_0,0 J=3/2-1/2 F=2-1 (quadruplet) (86.67076 GHz)
- Line: H2CO 6_1,5-6_1,6 (101.33299 GHz)
- Line: CH3OH 7_2,6-6_3,3 etc. (86.61560 GHz)
- Line: CH2OHCHO 14_5,9-14_4,10 etc. (101.52785 GHz)
- Other facility **IRAM 30m (TIMASSS survey)**: Public single-pointing single-dish spectra used to detect extended HCO  
  > "publicly available single-dish IRAM 30m data from the TIMASSS survey consisting on a single-pointing towards IRAS16293" (2 Observations)
- External data: Dust absorption coefficient 0.009 cm2/g at 1 mm (thin ices, n=1e6 cm-3)  
  > "extrapolating from the value at 1 mm of 0.009 cm$^2$ g$^{-1}$ (thin ices in a H$_2$ density of 10$^6$ cm$^{-3}$; see (cite: ossenkopf94))" (3.1 Continuum) [from (cite: ossenkopf94)]
- External data: Cold envelope N(H2)=2e23 cm-2 and 10 K temperature  
  > "which is $N_{\rm H_2}$=2$\times$10$^{23}$ cm$^{-2}$" (3.2.3 Derivation of physical parameters) [from (cite: van-dischoeck1995)]
- External data: Spectroscopic catalogs JPL and CDMS  
  > "we used molecular entries from JPL[^4] ((cite: pickett1998)) and CDMS[^5]" (3.2.1 Identification) [from (cite: pickett1998); (cite: muller2001; muller2005; endres2016)]
- External data: Desorption energies HCO 1600 K and CH2OHCHO 6684 K  
  > "has much higher desorption energy than HCO (6684 K vs. 1600 K; (cite: garrod08))" (4.2) [from (cite: garrod08)]
- Simulation/model as data: 0-D two-stage chemical model (free-fall collapse over 1e6 yr, then warm-up 10-200 K over 2e5 yr) based on Vasyunin et al. 2013b/2017, models I-III  
  > "we used an updated chemical model based on (cite: vasyunin2013b). This schematic 0-dimensional model mimics the evolution of a parcel of gas and dust" (4 Comparison with the chemical model)

## Processing

### Calibration

- pipeline or manual: Standard ALMA calibration scripts of CASA  
  > "The data were calibrated and imaged using standard ALMA calibration scripts of the Common Astronomy Software Applications package (CASA)" (2 Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Titan (phase: J1625-2527; bandpass: J1517-2422)  
  > "Flux calibration was obtained through observations of Titan." (2 Observations)
- flux scale uncertainty: 5%  
  > "The flux density calibration uncertainty is of 5$\%$" (2 Observations)
- self calibration: _not stated_

### Imaging

- task: CASA imaging of datacubes including continuum  
  > "We imaged with CASA the datacubes including the continuum" (2 Observations)
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: uv-plane subtraction using line-free channels chosen from fitted continuum level  
  > "we used this continuum level as a reference for selecting the line-free channels, which were used to substract the continuum in the uv-plane" (3.1 Continuum)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 1.09x0.78 arcsec continuum at ~94 GHz  
  > "has a synthesized beam of 1.09$\ensuremath{''}\times$0.78$\ensuremath{''}$" (3.1 Continuum)
- final rms: _not stated_

### Inherited from earlier work

- 5% flux calibration uncertainty adopted from Band 7 and Band 3/6 calibrator analyses  
  > "consistent with that of the ALMA band 7 observations of the same source carried out by (cite: jorgensen2016)" (2 Observations) [from (cite: jorgensen2016); (cite: bonato2018)]
- Cold envelope temperature of 10 K  
  > "we assumed the temperature of 10 K of the surrounding circumbinary envelope of IRAS16293 ((cite: van-dischoeck1995) and (cite: quenard2018a))" (3.2.3 Derivation of physical parameters) [from (cite: van-dischoeck1995); (cite: quenard2018a)]
- Chemical model based on earlier code  
  > "The chemical network used in this study is based on an updated version of the one presented in (cite: vasyunin2017)." (4) [from (cite: vasyunin2013b); (cite: vasyunin2017)]

### Not stated but needed to reproduce (our reading)

- CASA version and tclean/imaging parameters (weighting, robust, cell, image size, deconvolver, masks)
- Which channels were line-free for continuum subtraction
- Whether archive calibration products or manual scripts were used
- Chemical network updates and rate coefficients (details deferred to Vasyunin et al. in prep.)
- Details of the TIMASSS data reduction and matching to ALMA integration area
- MADCUBA version
- Exact positions or apertures used to extract spectra

## Analysis recipe

1. **Fit continuum level and derive N(H2)**: Modified blackbody fit by visual inspection varying beta and tau_d0 over four spws; T_c fixed to CH3OH Tex; N(H2) from tau_d0  
  > "We tried multiple combinations of both parameters (some examples are shown in Figures [11](#fig-continuoA) and [12](#fig-continuoB)) and chose by visual inspection the solutions" (7 Fit of the continuum level)
   - software: MADCUBA
   - parameter: nu0=94 GHz; Tc=178 K (A), 181 K (B)  
  > "assumed that $T_{\rm c}$ is equal to the excitation temperature derived from CH$_3$OH, 178 K and 181 K for sources A and B respectively" (7 Fit of the continuum level)
   - assumption: gas-to-dust 100; mu=2.8; kappa0 extrapolated from 0.009 cm2/g at 1 mm  
  > "In the calculation we assumed a gas-to-dust mass ratio of 100" (3.1 Continuum)
   - fitting: Visual inspection; errors from 5% calibration plus spectral rms  
  > "We assumed a flux density calibration error of $\pm$5$\%$" (7 Fit of the continuum level)
   - validation: Comparison with previous N(H2) estimates  
  > "These hydrogen column densities are in good agreement with previous estimates" (3.1 Continuum)
2. **Measure source sizes and identify lines**: 2D Gaussian fits for sizes; SLIM line identification with JPL/CDMS; Gaussian line fits  
  > "The identification of the lines was performed using the SLIM (Spectral Line Identification and Modeling) tool of MADCUBA" (3.2.1 Identification)
   - software: MADCUBA-SLIM
   - parameter: Molecular emission size assumed equal to continuum: 0.88 arcsec (A), 0.44 arcsec (B)  
  > "This gives 0.88$\ensuremath{''}$ for source A and 0.44$\ensuremath{''}$ for source B." (3.2.1 Identification)
   - assumption: Line emission unresolved, same size as continuum  
  > "we will assume hereafter that the molecular emission/absorption share the same size of the continuum" (3.2.1 Identification)
   - fitting: _not stated_
   - validation: _not stated_
3. **Derive column densities, Tex and abundances via LTE**: MADCUBA-AUTOFIT LTE fits of emission and absorption components with Levenberg-Marquardt; abundances relative to N(H2)  
  > "it provides the best non-linear least-squared fit using the Levenberg-Marquardt algorithm." (3.2.3 Derivation of physical parameters)
   - software: MADCUBA-AUTOFIT
   - parameter: Free: N, Tex, v, FWHM; HCO Tex assumed 50-180 K; absorption 10 K; H2CO Tex 100 K  
  > "we then assumed a range of temperatures typical of hot corinos, 50$-$180 K" (3.2.3 Derivation of physical parameters)
   - assumption: LTE  
  > "we assumed Local Thermodynamic Equilibrium (LTE) conditions" (3.2.3 Derivation of physical parameters)
   - fitting: Errors from covariance matrix diagonal (inverse Hessian) and final chi2  
  > "The errors of the parameters left free are derived from the diagonal elements of covariance matrix, the inverse of the Hessian Matrix, and the final $\chi^2$ of the fit." (3.2.3 Derivation of physical parameters)
   - validation: Simulated HCO spectra with random noise and channel resampling show weaker lines dilute below 2-3 sigma  
  > "the other transitions can be spectrally diluted and fall below 2$-$3$\sigma$ levels" (3.2.3 Derivation of physical parameters)
4. **Compare ALMA with IRAM 30m spectra**: Integrate ALMA over 28 arcsec IRAM beam and compare; fit extended HCO with LTE at 10 K  
  > "ALMA integrated in an area matching the IRAM 30m beam ($\sim$28$^{\prime\prime}$)" (3.2.2 Comparison with single-dish data)
   - software: MADCUBA-AUTOFIT
   - assumption: Emission fills the telescope beam; Tex 10 K  
  > "We assumed that the emission fills the telescope beam" (3.2.3 Derivation of physical parameters)
   - fitting: LTE AUTOFIT  
  > "The MADCUBA-AUTOFIT tool compares the observed spectra with the LTE synthetic spectra of the different species calculated following the previous expressions, taking into account all transitions, and it provides the best non-linear least-squared fit using the Levenberg-Marquardt algorithm." (Derivation of physical parameters)
   - validation: _not stated_
5. **Compare abundances with chemical models**: 0-D gas-grain model with collapse and warm-up; models I-III for HCO formation; CH2OHCHO via HCO+CH2OH; abundance uncertainty factor of 3  
  > "we have considered an uncertainty range multiplying and dividing by a factor of 3" (4)
   - parameter: Collapse 1e6 yr, n 3e3 to 1e8 cm-3; warm-up 10-200 K over 2e5 yr  
  > "It is assumed that during this stage a parcel of gas and dust warms up from 10 K to 200 K during 2$\times$10$^{5}$ years" (4)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : Calibration and imaging  
  > "The data were calibrated and imaged using standard ALMA calibration scripts of the Common Astronomy Software Applications package (CASA)" (2 Observations)
- **MADCUBA (SLIM, AUTOFIT)** : Line identification, LTE fits, analysis  
  > "The analysis of the data was done with" (2 Observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Dust beta, source A | 0.9 | ±0.4 | dimensionless | 1 | $\beta$=0.9$\pm$0.4 and $\tau_{d0}$=0.09$\substack{+0.01 \\ -0.01}$ for source A |
| Dust beta, source B | 0.0 | ±0.5 | dimensionless | 1 | $\beta$=0.0$\pm$0.5 and $\tau_{d0}$=2.1$\substack{+0.6 \\ -0.4}$ for source B |
| N(H2) source A | 4.4e24 | not stated | cm-2 | 1 | We obtained N(H2)=4.4$\times$10$^{24}$ cm$^{-2}$ and N(H2)=5.0$\times$10$^{25}$ cm$^{-2}$ for A and B, respectively. |
| N(H2) source B | 5.0e25 | not stated | cm-2 | 1 | We obtained N(H2)=4.4$\times$10$^{24}$ cm$^{-2}$ and N(H2)=5.0$\times$10$^{25}$ cm$^{-2}$ for A and B, respectively. |
| HCO abundance source A | (0.06-0.36)e-8 | not stated | relative to H2 | 3 | For source A, the HCO abundance is (0.06$-$0.36)$\times$10$^{-8}$, for the range of excitation temperature considered. |
| HCO abundance source B | (0.01-0.06)e-8 | not stated | relative to H2 | 3 | For source B, the HCO abundance is (0.01$-$0.06)$\times$10$^{-8}$ |
| CH3OH Tex source B | 181 | ±9 | K | 3 | / CH$_3$OH / 181$\pm$9 / 2.4$\pm$0.1 / 1.5$\pm$0.1 / 282$\pm$10 |
| CH2OHCHO Tex source B | 157 | ±14 | K | 3 | We obtained a temperature of 157$\pm$14 K for source B |
| Extended envelope HCO abundance | (1.5-2.9)e-11 | not stated | relative to H2 | 4 | which translates into an abundance of (1.5$-$2.9)$\times$10$^{-11}$ |

## Qualitative findings

- HCO emission is compact and coincident with the continuum in both hot corinos, with redshifted absorption from infalling foreground envelope  
  > "The observations revealed compact HCO emission arising from the two protostars." (abstract)

## Claim tuples

- H: Is HCO in hot corinos formed by gas-phase or grain-surface chemistry? | E: Compare LTE-derived HCO abundances with chemical models I-III | R: Only model II with CO hydrogenation reaches ~1e-10 peak, higher by over an order of magnitude than models I and III | F: Hot corino HCO forms by CO hydrogenation on grains followed by thermal desorption | **supported**
- H: Is extended HCO in the envelope formed by gas-phase chemistry? | E: Fit IRAM 30m HCO and compare with model I | R: Abundance ~1e-11 matches model I | F: Gas-phase routes suffice for the cold envelope | **supported**
- H: Is HCO+CH2OH the main route to glycolaldehyde? | E: Compare modelled and observed abundances | R: Model reproduces observed CH2OHCHO at ~140 K | F: HCO+CH2OH favored; other routes not excluded | **partially**

## Reasoning

- Why this data: No high-resolution HCO observations existed previously  
  > "up to now, no high angular resolution observations of HCO are available" (1 Introduction)
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): CH3OH and H2CO column densities are lower limits because lines are optically thick  
  > "the lines are not optically thin, and our estimates of the CH$_3$OH column densities should be considered as strict lower limits" (3.2.3)
- Limitation (authors): HCO Tex could not be determined since all four lines share Eup of 4 K  
  > "We were not able to derive the excitation temperature of HCO because the 4 detected lines of HCO share the same $E_{\rm up}$, 4 K." (3.2.3)
- Caveat (inferred, ours): Continuum fit by eye with no formal fitting
- Caveat (inferred, ours): Unresolved sources with assumed sizes make abundances size dependent
- Caveat (inferred, ours): Chemical model compared by eye with a single 0-D track
- Caveat (inferred, ours): Weak HCO lines only marginally detected

## Reproducibility

- Data public (paper): ALMA data from project 2015.1.01193.S; IRAM data publicly available from TIMASSS  
  > "publicly available single-dish IRAM 30m data from the TIMASSS survey" (2 Observations)
- Products in archive: _not stated_
- Missing: Imaging parameters
- Missing: Chemical network details
- Missing: MADCUBA version
- Data volume (inferred): ~10-20 GB
- Score (inferred): 3/5, Data identified and LTE method clear, but imaging parameters are absent and the chemical model is not released.
- Rediscovery candidate: yes, Data are public and the LTE fits give numeric abundances, though imaging details are missing.

## Links

- Method: (cite: rivilla2016) (MADCUBA description)
- Companion: (cite: jorgensen2016) (ALMA PILS survey of the same source)
- Related: TIMASSS
- Related: PILS

## Checks

```json
{
 "quotes": 76,
 "quotes_ok": 76,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 9,
 "numeric_problems": 0,
 "fill": {
  "facts": 80,
  "stated": 54,
  "rate": 0.675
 },
 "evidence_ok": true
}
```
