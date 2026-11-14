# ALMA Observations of the Physical and Chemical Conditions in Centaurus A

`2017ApJ...851...76M` | The Astrophysical Journal 2017 | first author: McCoy, Mark | arXiv: 1712.00360 | DOI: 10.3847/1538-4357/aa99d6

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, agn_and_quasars, astrochemistry
- Question: What are the physical and chemical conditions of the molecular arms and circumnuclear disk in NGC 5128 (Cen A), how do they relate to the absorption complexes against the AGN, and does the AGN influence the gas?  
  > "By observing multiple chemical probes, we determine the physical and chemical conditions of the nuclear interstellar medium of NGC 5128." (abstract)
- Target **Centaurus A (NGC 5128)**: coordinates RA 13h25m27.616s, Dec -43d01m08.813s (J2000)  
  > "the nearest radio galaxy at a distance of 3.8 Mpc" (abstract); "The AGN is detected as an unresolved millimeter continuum source at a position of RA(J2000): 13$^{h}$25$^{m}$27.616$^{s}$ DEC (J2000): -43$^{\circ}$01$'$08.813$''$." (3.1 Millimeter Continuum); z/distance 3.8 Mpc  
  > "the nearest radio galaxy at a distance of 3.8 Mpc" (abstract); "The AGN is detected as an unresolved millimeter continuum source at a position of RA(J2000): 13$^{h}$25$^{m}$27.616$^{s}$ DEC (J2000): -43$^{\circ}$01$'$08.813$''$." (3.1 Millimeter Continuum); distance from Harris et al. 2010 (cite: Har2010)  
  > "the nearest radio galaxy at a distance of 3.8 Mpc" (abstract); "The AGN is detected as an unresolved millimeter continuum source at a position of RA(J2000): 13$^{h}$25$^{m}$27.616$^{s}$ DEC (J2000): -43$^{\circ}$01$'$08.813$''$." (3.1 Millimeter Continuum)

## Data provenance

- ALMA projects: 2011.0.00010.S, 2011.0.00008.SV
- bands: Band 6 (1 mm) and Band 3 (3 mm); 20 spectral windows  
  > "We observed 20 spectral windows, four in the 1 mm band (ALMA Band 6) and sixteen in the 3 mm band (ALMA Band 3)." (2.1 Observational Setup)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: Each spectral window 937.5 MHz (Band 6), 234.4 MHz (Band 3), 3840 channels  
  > "with a bandwidth of 234.4 MHz (approximately 730 km s$^{-1}$)" (2.1 Observational Setup)
- arrays: 17 antennas (Band 6); 17 then 16 antennas (Band 3)  
  > "The 3 mm observations were performed with 17 antennas for the first two observing runs and 16 antennas for the final two observations" (2.1 Observational Setup)
- configurations: _not stated_
- baselines: Band 6: 18-125 m; Band 3: 36-400 m  
  > "with baselines of 18 m to 125 m." (2.1 Observational Setup); "with baselines of 36 m to 400m." (2.1 Observational Setup)
- angular resolution: Beams ~1.3-2.2" (Table 1); emission cubes convolved to 2.25"  
  > "The emission cubes were all then convolved to a common beam of 2.25$"$ $\times$ 2.25$"$" (2.2 Calibration and Imaging)
- max recoverable scale: 10" (Band 6), 20" (Band 3)  
  > "The maximum recoverable scale is 10$"$ and the primary beam is 27$"$." (2.1 Observational Setup); "The maximum recoverable scale was 20$"$ and the primary beam was 62$"$." (2.1 Observational Setup)
- sensitivity: _not stated_
- time on source: ~33 min (Band 6), ~66 min (Band 3)  
  > "The total on-source integration time is $\sim$ 33 minutes" (2.1 Observational Setup); "The total on-source integration time is $\sim$ 66 minutes" (2.1 Observational Setup)
- observing dates: 2012 Jan 24 (Band 6); 2012 Apr 7 to May 9 (Band 3)  
  > "on 2012 Jan 24" (2.1 Observational Setup); "spanning the time between 2012 Apr 7 and 2012 May 9" (2.1 Observational Setup)
- pi or archival as stated: Cycle 0 project PI Ott; plus science verification 12CO(2-1) data  
  > "(PI:Ott)" (2.1 Observational Setup)
- Line: 13CO J=2-1 (220.398684 GHz)
- Line: C18O J=2-1 (219.560358 GHz)
- Line: HCN J=1-0 (88.631847 GHz)
- Line: HCO+ J=1-0 (89.188526 GHz)
- Line: 13CO J=1-0 (110.201354 GHz)
- Other facility **ALMA Science Verification (2011.0.00008.SV)**: 12CO(2-1) data for comparison  
  > "Additional ALMA data obtained during science verification (2011.0.00008.SV) were used to provide the $^{12}$CO($2-1$) 1.3 mm transition for comparison." (2.2 Calibration and Imaging)
- External data: Single-dish line ratios and conversion factor X = 4.0e20 for the CND  
  > "(cite: Isr2014) use LVG and PDR models to determine the conversion factor for the CND in NGC 5128 to be $X = 4.0 \times 10^{20}$ cm$^{-2}$ (K km s$^{-1}$)$^{-1}$." (4.3.2 Conversion Factor Analysis) [from (cite: Isr2014)]
- External data: Inclinations 71 deg (outer CND) and 37 deg (inner CND)  
  > "we use the reported value of 37$^{\circ}$ for the inclination angle from (cite: Qui2010)" (4.3.1 Dynamical Masses) [from (cite: Esp2009; Qui2010)]
- External data: SMBH mass 5.5e7 Msun  
  > "the mass of the SMBH ($5.5\times 10^{7} M_{\odot}$, (cite: Cap2009))" (4.3.1 Dynamical Masses) [from (cite: Cap2009)]

## Processing

### Calibration

- pipeline or manual: Initial calibration by ALMA team in CASA; self-calibration by authors  
  > "Initial calibration and editing of the data were performed by the ALMA team using the CASA (Common Astronomy Software Applications) data reduction package" (2.2 Calibration and Imaging)
- casa version: CASA 4.1  
  > "self calibration and imaging were performed by us with CASA version 4.1" (2.2 Calibration and Imaging)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Titan (flux); PKS B1424-418 gain; 3C279 bandpass for Band 3, Titan bandpass for Band 6  
  > "Titan is the flux and bandpass calibrator and complex gain (phase/gain) calibration was done by observing PKS B1424$-$418" (2.1 Observational Setup)
- flux scale uncertainty: 5% Band 3, 10% Band 6  
  > "An overall flux accuracy of 5% was assumed for the Band 3 observations and a flux accuracy of 10% was assumed for the Band 6 observations" (2.2 Calibration and Imaging)
- self calibration: Phase-only then one amplitude+phase iteration on the continuum core, avoiding line channels  
  > "As the first step, we self-calibrated the phases only, then we did an iteration of simultaneous amplitude and phase self-calibration." (2.2 Calibration and Imaging)

### Imaging

- task: CASA CLEAN  
  > "Imaging was performed using the CASA task CLEAN with natural weighting" (2.2 Calibration and Imaging)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "Imaging was performed using the CASA task CLEAN with natural weighting" (2.2 Calibration and Imaging)
- uv taper: _not stated_
- cell size: 0.2 arcsec per pixel  
  > "an image size of 320 $\times$ 320 pixels at 0.2 arcseconds per pixel" (2.2 Calibration and Imaging)
- image size: 320 x 320 pixels (64")  
  > "an image size of 320 $\times$ 320 pixels at 0.2 arcseconds per pixel" (2.2 Calibration and Imaging)
- masking: Mask from cube smoothed to 4.5" keeping >~3 sigma; central ~5"x5" masked for absorption in moment maps; absorption cubes not cleaned  
  > "only including emission in the original image cube where the smoothed cube contained emission stronger than $\sim$ 3 times the RMS." (2.2 Calibration and Imaging)
- multiscale scales: _not stated_
- continuum subtraction: UVCONTSUB2, 1st order polynomial on line- and absorption-free channels  
  > "We then used the CASA task UVCONTSUB2 to fit a 1st order polynomial continuum model to channels that were free of both line emission and absorption." (2.2 Calibration and Imaging)
- line free channels: _not stated_
- primary beam correction: Moment 0 maps are primary beam corrected  
  > "Figure [2](#Fig:mom0) shows the primary beam corrected integrated intensity (moment 0) maps" (3.2 Molecular Gas Structure)
- array combination: _not stated_
- smoothing: Emission cubes averaged over 10 channels; convolved to 2.25"; 12CO(2-1) and comparison cubes to 3.0"  
  > "Broader spectral resolution (averaged over 10 channels) image cubes were created and cleaned to map the emission." (2.2 Calibration and Imaging)
- final beam: 2.25" x 2.25" (3.0" for 12CO(2-1) comparison)  
  > "the $^{12}$CO($2-1$) was convolved to a 3.0$"$ $\times$ 3.0$"$ beam" (2.2 Calibration and Imaging)
- final rms: Continuum rms 1.3 mJy/beam (3 mm), 2.1 mJy/beam (1 mm)  
  > "We achieved rms values for the 3 mm and 1 mm images of 1.3 mJy beam$^{-1}$ and 2.1 mJy beam$^{-1}$ respectively." (3.1 Millimeter Continuum)

### Inherited from earlier work

- Rest frequencies from NIST recommended list  
  > "The rest frequencies of the targeted molecular transitions from (cite: Lov2004)." (Table 1) [from (cite: Lov2004)]
- Assume 12CO/13CO abundance ~40 as in NGC 253 and IC 342  
  > "we assume that the \[$^{12}$CO/$^{13}$CO\] abundance ratio is near 40, the values found toward the centers of NGC 253 ((cite: Hen2014)) and IC 342 ((cite: Mei2001))" (4.2.1 CO Isotopic Ratios) [from (cite: Hen2014; Mei2001)]

### Not stated but needed to reproduce (our reading)

- CLEAN threshold, number of iterations, and cleaning masks
- Self-calibration solution intervals and reference antenna
- Exact line-free channel ranges for UVCONTSUB2
- Aperture sizes for continuum flux measurements
- Details of how the 12CO(2-1) SV data were processed and beam handled
- Procedure and uncertainties for the Gaussian fits to the spectra
- How the isotopologue opacity solution was found (no fitting algorithm)
- Whether flux scale was bootstrapped from Titan model version

## Analysis recipe

1. **Self-calibrate and continuum-subtract**: Phase then amp+phase self-cal on nuclear continuum with GAINCAL/APPLYCAL; UVCONTSUB2 first order  
  > "We performed a self calibration on the bright radio continuum core of Cen A using the CASA task GAINCAL to generate the calibration tables and APPLYCAL to apply the corrections to the data." (2.2 Calibration and Imaging)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Image cubes and continuum**: CLEAN natural weighting; emission cubes cleaned and convolved to common beam; absorption cubes dirty  
  > "The artifacts are not present in the dirty cube that we used for the analysis of the absorption spectra." (2.2 Calibration and Imaging)
   - software: CASA
   - fitting: _not stated_
   - validation: Cubes inspected for CLEAN artifacts  
  > "The emission cubes were then inspected for artifacts created by CLEAN." (2.2 Calibration and Imaging)
3. **Make moment maps, PV diagrams and extract spectra**: Moment 0/1/2 with masking; PV slices averaged over 11 pixels; spectra in 2.25" apertures at eight regions  
  > "Spectra were taken using a 2.25” apertures corresponding to the circles in Figure [4](#Fig:Schematic)." (3.4.1 Emission Spectra)
   - fitting: Gaussian components fit to spectra (22 velocity components)  
  > "We identify 22 velocity components throughout all of the observed molecular transitions and spatial locations." (3.4.1 Emission Spectra)
   - validation: _not stated_
4. **Isotopologue ratio and excitation analysis**: Adjust abundance ratio and opacity until consistent with observed 12CO/13CO/C18O ratios; 13CO(2-1)/(1-0) for Tex  
  > "we adjust the abundance ratio and opacity for the isotopologue ratios until a consistent solution is found with the observed intensity ratios." (4.2.1 CO Isotopic Ratios)
   - assumption: [12CO/13CO] near 40 as starting value; high-temperature limit, equal filling factors and linewidths  
  > "assuming similar area filling factors, $^{i}f_{a}$, and the same T$_{x}$" (4.2.1 CO Isotopic Ratios)
   - fitting: Manual iteration, no sampler  
  > "we adjust the abundance ratio and opacity for the isotopologue ratios until a consistent solution is found with the observed intensity ratios." (Gas Chemistry / CO Isotopic Ratios)
   - validation: Comparison with single-dish ratios of Israel et al. 2014  
  > "The emission ratios are consistent with the single dish data from (cite: Isr2014)." (4.2.1 CO Isotopic Ratios)
5. **Dynamical and gas masses**: M_enc = v^2 R/(G sin^2 i) from HCO+ velocities; H2 mass from 12CO(2-1) with X factors and 13CO  
  > "using the equation $M_{enc} = \frac{v^2 R}{G \sin^{2}i}$" (4.3.1 Dynamical Masses)
   - assumption: 12CO(2-1)/(1-0) = 0.8; X = 2.0e20 (also 0.4e20, 4.0e20); [12CO/H2]=8.5e-5; Tex=20 K  
  > "assuming a ratio of $^{12}$CO($2-1$) to $^{12}$CO($1-0$) of 0.8 ((cite: Ler2009))" (4.3.2 Conversion Factor Analysis)
   - fitting: _not stated_
   - validation: _not stated_
6. **Absorption opacity ratios compared with emission ratios**: Convert absorption spectra to tau, assuming covering factor unity, and compare ratios to emission  
  > "assuming a continuum source covering factor of unity" (3.4.2 Absorption Spectra)
   - assumption: tau = -ln[1-(-F_spec/F_cont)]; optically thin and similar excitation for ratio comparison  
  > "assuming the transitions are optically thin, then the $\tau$ absorption ratio and the T emission ratios may be compared robustly" (4.4 Comparing Absorption and Emission)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.1: Self-calibration, continuum subtraction (UVCONTSUB2), imaging (CLEAN), GAINCAL/APPLYCAL  
  > "self calibration and imaging were performed by us with CASA version 4.1" (2.2 Calibration and Imaging)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Core continuum flux Band 3 | 8.1 | 0.4 | Jy | 2 | core flux of $8.1 \pm 0.4$ Jy in band 3 and $6.7 \pm 0.7$ Jy in band 6 |
| Core continuum flux Band 6 | 6.7 | 0.7 | Jy | 2 | core flux of $8.1 \pm 0.4$ Jy in band 3 and $6.7 \pm 0.7$ Jy in band 6 |
| Core spectral index between bands | -0.2 | 0.1 | dimensionless | 2 | The spectral index between the two bands is $-0.2 \pm 0.1$ for the bright radio core continuum |
| CND size | ~410 pc x 215 pc | not stated | pc | 3 | The CND is measured to be $\sim$ 410 pc (22$"$) $\times$ 215 pc (10.7$"$) |
| Systemic velocity (LSRK) | ~550 | not stated | km/s | 3 | the systemic velocity in the LSRK (Local Standard of Rest, kinematic definition) velocity frame for Cen A is approximately 550 km s$^{-1}$ |
| Enclosed dynamical mass, outer CND | 1.4e9 | 0.2e9 | Msun | 5 | enclosed dynamical mass of about $1.4 \pm 0.2 \times 10^{9} M_{\odot}$ |
| Enclosed dynamical mass, inner CND | 3.6e8 | factor of 2 | Msun | 5 | enclosed dynamical mass of $3.6 \times 10^{8} M_{\odot}$ (uncertain by a factor of 2) |
| H2 mass of CND region (X=2.0e20) | 1.2e8 | not stated | Msun | 5 | an H$_{2}$ mass of $1.2\times 10^{8} M_{\odot}$ is calculated for the CND region |
| Gas mass of CND from 13CO limit | ~2e6 | not stated | Msun | 5 | a total gas mass of $\sim 2\times 10^{6} M_{\odot}$ for the CND is calculated |
| HCN(1-0)/HCO+(1-0) ratio | ~0.6 | not stated | dimensionless | 3 | an HCN(1-0)/HCO$^{+}$(1-0) ratio near 0.6 everywhere they are both detected |
| HCN(1-0)/HNC(1-0) in CND | 1.5-3.5 | not stated | dimensionless | 3 | ratios toward the CND of Cen A are between 1.5 – 3.5 |
| 13CO(2-1)/13CO(1-0) emission ratio | 1.1-1.5 | not stated | dimensionless | 4 | We observe an emission line ratio $^{13}$CO($2-1$)/$^{13}$CO($1-0$) of 1.1 – 1.5. |

## Qualitative findings

- Molecular arms are strong in CO isotopologues; the CND is dominated by dense gas tracers and weak in 13CO and C18O  
  > "It is dominated by dense gas tracers while the molecular arms are dominated by $^{12}$CO and its rare isotopologues." (abstract)
- No emission connecting the arms and CND is detected, though large-scale structure may be resolved out  
  > "We do not detect emission connecting the narrow linewidth emission components of the molecular arms, and the broad linewidth emission from the molecular CND." (4.1 Are the Molecular Arms and the CND Connecting?)

## Claim tuples

- H: Are the CND and molecular arms chemically and kinematically distinct? | E: Maps, PV diagrams, spectra and line ratios of 9 transitions | R: Arms bright in CO isotopologues, CND in dense gas tracers; 13CO(1-0)/HCN(1-0) <0.2 in CND vs >=3 in arms | F: They are distinct and no connection is seen | **supported**
- H: Do the LV and HV absorption complexes originate in the CND? | E: Compare absorption opacity ratios with emission ratios | R: Absorption ratios match CND rather than arms | F: Both complexes likely originate in the CND; HV may be infalling | **partially**
- H: Does the AGN influence the CND chemistry? | E: Dense gas line ratios compared with PDR/XDR models | R: Elevated CN, weak rare CO isotopologues; PDR weakly favored over XDR | F: AGN may radiatively influence the CND but star formation or shocks are not excluded | **partially**

## Reasoning

- Why this data: Cen A's proximity gives resolution down to 40 pc and a multi-line survey probes nuclear gas conditions  
  > "Our observations resolve physical sizes down to 40 pc." (abstract)
- Why this method: _not stated_
- Alternative: Isotope-selective photodissociation vs low-metallicity accreted gas as explanation for faint rare CO isotopologues; latter cannot be ruled out  
  > "With the current data presented here, we do not see strong evidence for this possibility, but cannot rule it out." (4.2.3 The Influence of the AGN on Gas Chemistry)
- How they decided it was enough: _not stated_
- Limitation (authors): Missing short spacings may resolve out extended structure; up to ~25% extended emission not recovered  
  > "This suggests that there is $\lesssim 25$% extended emission that is not recovered by our interferometric ALMA observations." (4.4 Comparing Absorption and Emission)
- Limitation (authors): 3 mm and 1 mm continuum not simultaneous; ~30% variability of Cen A  
  > "the 3 mm and 1 mm continuum were not observed simultaneously." (3.1 Millimeter Continuum)
- Limitation (authors): CLEAN artifacts in absorption cubes not understood  
  > "The clean artifacts are not fully understood" (2.2 Calibration and Imaging)
- Caveat (inferred, ours): Isotopologue analysis is a manual by-eye solution without uncertainties
- Caveat (inferred, ours): Mass estimates depend on literature inclinations that differ between sources
- Caveat (inferred, ours): Only a few absorption components analyzed; hyperfine blending
- Caveat (inferred, ours): PDR vs XDR conclusion is qualitative with no modeling

## Reproducibility

- Data public (paper): Cycle 0 project and SV data cited by project code, standard ALMA archive data  
  > "This manuscript makes use of the following ALMA data: ADS/JAO.ALMA #2011.0.00008.SV and 2011.0.00010.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: CLEAN parameters and masks
- Missing: line-free channel ranges
- Missing: self-cal solints
- Missing: aperture definitions
- Missing: isotopologue solution procedure details
- Data volume (inferred): ~50-100 GB raw (Cycle 0, 20 spectral windows, 3840 channels)
- Score (inferred): 3/5, Data public and main steps described, but imaging and fitting details are sparse and the analysis is partly manual.
- Rediscovery candidate: no, Key numerical results depend on unstated imaging and manual line decomposition choices and heterogeneous assumptions.

## Links

- Method: (cite: CASAref) (CASA software reference)
- Companion: (cite: Esp2017) (Companion ALMA Cycle 3 study of Cen A CND at higher resolution)
- Companion: (cite: Isr2014) (Single-dish comparison data and conversion factor)
- Related: ALMA Cycle 0 early science
- Related: ALMA science verification

## Checks

```json
{
 "quotes": 86,
 "quotes_ok": 86,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 12,
 "numeric_problems": 0,
 "fill": {
  "facts": 77,
  "stated": 56,
  "rate": 0.727
 },
 "evidence_ok": true
}
```
