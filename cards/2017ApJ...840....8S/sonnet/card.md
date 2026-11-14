# Luminous Infrared Galaxies with the Submillimeter Array. V. Molecular Gas in Intermediate to Late-stage Mergers

`2017ApJ...840....8S` | The Astrophysical Journal 2017 | first author: Sliwa, Kazimierz | arXiv: 1703.07121 | DOI: 10.3847/1538-4357/aa689b

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type multi_facility_alma_minor

## Science

- Fields: nearby_galaxies, astrochemistry
- Question: What are the molecular gas physical conditions, 12CO/13CO abundance ratio and CO-to-H2 conversion factor in the LIRGs Arp 55 and NGC 2623, and how do they depend on merger stage?  
  > "We perform a Bayesian likelihood non-local thermodynamic equilibrium analysis to constrain the molecular gas physical conditions such as temperature, column and volume densities and the \[$^{12}$CO\]/\[$^{13}$CO\] abundance ratio." (abstract)
- Target **NGC 2623 (Arp 243)**: coordinates 08h38m24.1s +25d45m16.53s (CO 3-2 peak, Line Ratios table)  
  > "is an advanced merger LIRG ($L_{\rm{FIR}}$ = 3.0 $\times$ 10$^{11}$ $L_{\odot}$; (cite: Sanders2003)) at a distance of 83 Mpc (1$''$ = 402 pc)." (2.1 The Targets); z/distance 83 Mpc  
  > "is an advanced merger LIRG ($L_{\rm{FIR}}$ = 3.0 $\times$ 10$^{11}$ $L_{\odot}$; (cite: Sanders2003)) at a distance of 83 Mpc (1$''$ = 402 pc)." (2.1 The Targets); distance from _not stated_
- Target **Arp 55**: coordinates NE 09h15m55.5s +44d19m57.9s; SW 09h15m54.7s +44d19m51.5s  
  > "The system consists of two nuclei separated by $\sim$ 11$^{\prime\prime}$ (9.3 kpc at $D_{\rm{L}}$ = 175 Mpc; 1$^{\prime\prime}$ = 850 pc)." (2.1 The Targets); z/distance D_L = 175 Mpc  
  > "The system consists of two nuclei separated by $\sim$ 11$^{\prime\prime}$ (9.3 kpc at $D_{\rm{L}}$ = 175 Mpc; 1$^{\prime\prime}$ = 850 pc)." (2.1 The Targets); distance from _not stated_

## Data provenance

- ALMA projects: 2015.1.00804.S
- bands: Band 3 (13CO 1-0) and Band 6 (13CO 2-1)  
  > "The receiver Bands 3 and 6 were tuned to $^{13}$CO $J$=1$-$0 and $J$ = 2-1, respectively." (2.2 ALMA)
- frequencies and spectral setup: four spectral windows, 1.875 GHz bandwidth, 960 channels each  
  > "Each observation consisted of four spectral windows with a bandwidth of 1.875 GHz and 960 channels each." (2.2 ALMA)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: Band 6 baselines above 200 m flagged  
  > "we flag all baselines above 200 m after applying the water vapour radiometer and system temperature corrections" (2.2 ALMA)
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: Cycle 2, PI K. Sliwa  
  > "ALMA observations towards NGC 2623 were conducted during Cycle 2 (Project ID= 2015.1.00804.S; PI: K.Sliwa)." (2.2 ALMA)
- Line: 13CO J=1-0 (not stated)
- Line: 13CO J=2-1 (not stated)
- Other facility **CARMA**: 12CO and 13CO J=1-0 maps and 2.8 mm continuum  
  > "Arp 55 was observed in $^{12}$CO and $^{13}$CO $J$=1$-$0 using CARMA in the B, C, and D array configurations" (2.3 CARMA)
- Other facility **SMA**: 12CO J=2-1, 3-2 and 13CO 2-1 data  
  > "We use the SMA calibrated $uv$ datasets of $^{12}$CO $J$=2$-$1 and $J$ = 3–2 from Paper I." (2.4 Submillimeter Array (SMA))
- Other facility **JCMT**: 12CO 2-1 map of Arp 55 to check flux recovery  
  > "For Arp 55, we used the JCMT to map a 56$''$ $\times$ 56$''$ area in $^{12}$CO $J$=2$-$1 using the RxA3 receiver" (2.5 JCMT)
- External data: JCMT 12CO 3-2 flux of Arp 55, 775 ± 130 Jy km/s  
  > "measured the $^{12}$CO $J$=3$-$2 flux in Arp 55 in a JCMT spectrum to be 775 $\pm$ 130 Jy km s$^{-1}$" (2.5 JCMT) [from Papadopoulos2012a]
- External data: Comparison LIRG temperature/density results (Arp 220, Arp 299, VV 114, NGC 1614, NGC 6240, NGC 4038/9, M51)  
  > "We plot the most probable $T_{\rm{kin}}$ versus $n_{\rm{H_{2}}}$ of Arp 220 (cite: Rangwala2011), Arp 299 (cite: Sliwa2012), VV 114 (cite: Sliwa2013)" (5.3 Merger Stage) [from Rangwala2011; Sliwa2012; Sliwa2013; Sliwa2014; Tunnard2015b; Schirm2014]

## Processing

### Calibration

- pipeline or manual: Band 3 with ALMA pipeline; Band 6 manual  
  > "The Band 6 observations were manually calibrated using `CASA` v4.7.0." (2.2 ALMA)
- casa version: CASA v4.7.0 (Band 6 calibration and imaging)  
  > "The Band 6 observations were manually calibrated using `CASA` v4.7.0." (2.2 ALMA)
- pipeline version: CASA ALMA pipeline v4.5.3 (Band 3)  
  > "The Band 3 data were calibrated using the `CASA` (cite: McMullin2007) ALMA pipeline (v4.5.3)" (2.2 ALMA)
- archive products used as is: _not stated_
- flux calibrator: J0854+2006 (both bands)  
  > "The observations used J0854+2006 as the flux and bandpass calibrators and J0837+2454 as the gain calibrator." (2.2 ALMA)
- flux scale uncertainty: 10% Band 3, 20% Band 6  
  > "We estimate a flux calibration uncertainty of 10$\%$ and 20$\%$ for Bands 3 and 6, respectively." (2.2 ALMA)
- self calibration: _not stated_

### Imaging

- task: CASA v4.7.0  
  > "We image the datasets using `CASA` v4.7.0" (2.2 ALMA)
- deconvolver: _not stated_
- weighting robust: Briggs robust 0.5  
  > "using a Briggs robust weighting of 0.5" (2.2 ALMA)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: CLEAN boxes around emission  
  > "CLEAN boxes were placed around the emission to aid the CLEAN process converge." (2.2 ALMA)
- multiscale scales: _not stated_
- continuum subtraction: uv-domain using line-free channels  
  > "Each dataset was continuum subtracted in the $uv$ domain using line-free channels." (2.2 ALMA)
- line free channels: _not stated_
- primary beam correction: applied to integrated intensity maps, 2 sigma cutoff  
  > "Each integrated intensity map was primary beam corrected." (2.2 ALMA)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 13CO 1-0 2.4x1.9 arcsec; 13CO 2-1 3.4x1.4 arcsec; 2.5 arcsec compromise for analysis  
  > "| $^{13}$CO $J$=2$-$1  | ALMA | 14.3 | 1.1 | 40 | 3.4 $\times$ 1.4 |" (Table 1)
- final rms: 13CO 1-0 0.43 mJy/beam; 2-1 1.1 mJy/beam  
  > "| $^{13}$CO $J$=1$-$0  | ALMA | 28.6 | 0.43 | 30 | 2.4 $\times$ 1.9 |" (Table 1)

### Inherited from earlier work

- SMA calibration and 12CO 2-1/3-2 uv datasets  
  > "We use the SMA calibrated $uv$ datasets of $^{12}$CO $J$=2$-$1 and $J$ = 3–2 from Paper I. For calibration details, see Paper I." (2.4 SMA) [from Paper I, Wilson2008]
- Nested-sampling RADEX likelihood code and details  
  > "We use the code published in (cite: Kamenetzky2014) that implements a nested sampling algorithm" (4.1 Radiative Transfer Modeling) [from Kamenetzky2014]
- Dynamical mass formula  
  > "$M_{\rm{dyn}}$ = 99$\Delta$V$^{2}$D(pc) (cite: Wilson1990)" (Table 3) [from Wilson1990]

### Not stated but needed to reproduce (our reading)

- Line-free channel ranges for continuum subtraction
- Clean thresholds and image sizes/cell sizes for ALMA cubes
- Priors ranges and sampler settings for pyradexnest (beyond the three listed priors)
- Exact RADEX collisional data and line width treatment
- Which ALMA execution blocks/MOUS were used
- Method for deriving deconvolved source sizes

## Analysis recipe

1. **Calibrate and image ALMA 13CO cubes and moment maps**: Pipeline (Band 3) / manual (Band 6) calibration, uv continuum subtraction, CLEAN with boxes, integrated intensity with 2 sigma cutoff, primary-beam correction  
  > "Integrated intensity maps were created including line emission channels and using a 2$\sigma$ cutoff." (2.2 ALMA)
   - software: CASA
   - parameter: robust 0.5; 30 and 40 km/s channels; Band 6 baselines >200 m flagged  
  > "creating datacubes of 30 and 40 km s$^{-1}$ channel width for $^{13}$CO $J$=1$-$0 and $J$=2-1, respectively" (2.2 ALMA)
   - fitting: _not stated_
   - validation: _not stated_
2. **Match resolutions and measure line fluxes at nuclear peaks**: Gaussian taper during imaging to common resolution; 13CO 2-1 flux scaled using average 13CO(2-1/1-0) line ratio (1.6 Arp 55; 0.85 NGC 2623)  
  > "we estimate the flux of $^{13}$CO $J$=2$-$1 at the resolution of $^{12}$CO $J$=1$-$0 using an average $^{13}$CO (2-1/1-0) line ratio of 1.6 (K units" (4.2.1 Arp 55)
   - software: CASA
   - parameter: Arp 55 imaged with baselines >30.5 klambda; NGC 2623 at 2.5 arcsec  
  > "we image all Arp 55 maps with baselines above 30.5 k$\lambda$, the shortest baseline in the $^{12}$CO $J$=3$-$2 observations" (2.5 JCMT)
   - assumption: 30% uncertainty on 13CO flux scaled  
  > "We also implement a 30$\%$ uncertainty for $^{13}$CO which covers the observed range" (4.2.1 Arp 55)
   - fitting: _not stated_
   - validation: JCMT flux compared to SMA to check flux recovery  
  > "The JCMT $^{12}$CO $J$=2$-$1 flux measured for Arp 55 is consistent with the total flux measured in the SMA map" (2.5 JCMT)
3. **Non-LTE modelling of Tkin, nH2, N(CO), 12CO/13CO, filling factor**: RADEX with Bayesian nested sampling, with priors from dynamical mass, column length and tau in [0,100]  
  > "we implement three priors" (4.1 Radiative Transfer Modeling)
   - software: RADEX, pyradexnest
   - parameter: tau within [0,100]  
  > "The final prior limit the optical depth, $\tau$, within the range of \[0,100\]." (4.1 Radiative Transfer Modeling)
   - assumption: Spherical geometry for column length (half of source size for Arp 55)  
  > "We estimate the column length from the deconvolved source diameter, assuming a spherical geometry." (4.1 Radiative Transfer Modeling)
   - fitting: nested sampling; flux scaled by area filling factor <=1  
  > "the flux is permitted to scale uniformly down by an area filling factor $\Phi_{\rm{A}}$($\leq$ 1)" (4.1 Radiative Transfer Modeling)
   - validation: _not stated_
4. **Derive alpha_CO**: From RADEX 12CO column density vs peak 12CO 1-0 luminosity, assuming x_CO = 3e-4; dynamical-mass upper limit alpha_CO,dyn = Mdyn/L_CO  
  > "By comparing the $^{12}$CO column density (Table [4](#tab:results)) with the peak $^{12}$CO $J$=1$-$0 luminosity we measure $\alpha_{\rm{CO}}$" (5.2 CO-to-H2 Conversion Factor)
   - assumption: x_CO = 3e-4  
  > "we adopt the value of 3 $\times$ 10$^{-4}$, a value found in warm star forming clouds (cite: Lacy1994)" (5.2 CO-to-H2 Conversion Factor)
   - fitting: _not stated_
   - validation: dynamical mass upper limit  
  > "$\alpha_{\rm{CO, dyn}}$ is strictly an upper limit to the true $\alpha_{\rm{CO}}$ value" (5.2 CO-to-H2 Conversion Factor)

## Software

- **CASA** 4.7.0 (pipeline 4.5.3): calibration, imaging  
  > "The Band 6 observations were manually calibrated using `CASA` v4.7.0." (2.2 ALMA)
- **RADEX** : non-LTE radiative transfer  
  > "We use the code published in (cite: Kamenetzky2014)" (4.1 Radiative Transfer Modeling)
- **Starlink** : JCMT data cube reduction  
  > "A data cube spanning -585 to 585 km s$^{-1}$ was created using the `Starlink` software" (2.5 JCMT)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| NGC 2623 best-fit Tkin | 107 | 1sigma range 31-530 | K | 3 | / NGC 2623 / Median / 125 / 2.8 / 4.8 / -1.0 / 18.9 / 250 / 8.7 / 0.5 / |
| NGC 2623 best-fit log nH2 | 2.7 | 1sigma range 2.2-3.3 | log cm^-3 | 3 | less dense ($\sim$ 10$^{2.7}$ cm$^{-3}$) |
| NGC 2623 [12CO]/[13CO] best fit | 267 | 1sigma 85-720 | dimensionless | 3 | / NGC 2623 / Median / 125 / 2.8 / 4.8 / -1.0 / 18.9 / 250 / 8.7 / 0.5 / |
| Arp 55NE alpha_CO | 0.1 | range 0.1-0.2 | Msun (K km/s pc^2)^-1 | 4 | we measure $\alpha_{\rm{CO}}$ for Arp 55NE, Arp 55SW and NGC 2623 to be 0.1, 0.08 and 0.7 |
| NGC 2623 alpha_CO | 0.7 | not stated | Msun (K km/s pc^2)^-1 | 4 | 0.1, 0.08 and 0.7 (3 $\times$ 10$^{-4}$/$x_{\rm{CO}}$) |
| 2.8 mm continuum flux NGC 2623 | 18 | 4 | mJy | 0 | We measure the 2.8 mm continuum flux of NGC 2623 and Arp 55 to be 18 $\pm$ 4 mJy and 1.9 $\pm$ 0.4 mJy |
| NGC 2623 13CO 1-0 flux | 3.1 | ±0.3 (meas.), ±0.3 (cal.) | Jy km/s | 1 | 3.1 ($\pm$ 0.3) \[$\pm$ 0.3\] |

## Qualitative findings

- Advanced mergers have warmer, less dense gas and lower pressure than early/intermediate mergers  
  > "advanced mergers have a warmer and less dense molecular gas component than the early/intermediate mergers." (5.3)

## Claim tuples

- H: Gas conditions differ with merger stage | E: Non-LTE RADEX analysis of Arp 55 vs NGC 2623 and literature LIRGs | R: Arp 55 cold and dense; NGC 2623 ~110 K and less dense | F: Advanced mergers warmer and less dense | **supported**
- H: 12CO/13CO is enhanced in LIRGs | E: RADEX abundance ratio fits | R: NGC 2623 ~250; Arp 55 ~15-30 | F: NGC 2623 follows the LIRG trend, Arp 55 does not | **supported**
- H: alpha_CO transitions from Galactic to LIRG value early in a merger | E: alpha_CO from RADEX column densities | R: ~0.1 for Arp 55, ~0.7 for NGC 2623 | F: Transition occurs at an even earlier stage | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): alpha_CO largest uncertainty from x_CO assumption  
  > "The largest uncertainty in these values arises from the assumption of the $^{12}$CO abundance relative to H$_{2}$" (5.2)
- Caveat (inferred, ours): Only two galaxies and single positions modelled; merger-stage trend relies on heterogeneous literature fits
- Caveat (inferred, ours): Few lines constrain many RADEX parameters; degeneracies large
- Caveat (inferred, ours): Fractionation could bias 12CO/13CO
- Caveat (inferred, ours): Mixed resolutions and missing flux in CO 3-2

## Reproducibility

- Data public (paper): ALMA project listed; public status not stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA$\#$2015.0.0804.S ." (Acknowledgments)
- Products in archive: _not stated_
- Code: pyradexnest at github (third-party code)  
  > "https://github.com/jrka/pyradexnest" (footnote)
- Missing: CARMA and SMA raw data processing details
- Missing: line-free channels
- Missing: clean parameters
- Missing: sampler settings
- Data volume (inferred): ~50-100 GB for the two ALMA bands (raw); CARMA/SMA additional
- Score (inferred): 3/5, ALMA data identified and imaging basics given, but modelling priors and many imaging parameters are missing, with multi-facility inputs.
- Rediscovery candidate: no, Key results depend on SMA/CARMA data and unspecified modelling settings, so the recipe is incomplete.

## Links

- Method: Kamenetzky2014 (Bayesian RADEX nested sampling code)
- Companion: Wilson2008 (Paper I) (SMA data and calibration)
- Related: SMA LIRG survey

## Checks

```json
{
 "quotes": 63,
 "quotes_ok": 63,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [
  "2015.0.0804.S"
 ],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 78,
  "stated": 49,
  "rate": 0.628
 },
 "evidence_ok": true
}
```
