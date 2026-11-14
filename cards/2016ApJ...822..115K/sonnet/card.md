# Detection of HF Toward PKS 1830-211, Search for Interstellar H<SUB>2</SUB>F<SUP>+</SUP>, and Laboratory Study of H<SUB>2</SUB>F<SUP>+</SUP> and H<SUB>2</SUB>Cl<SUP>+</SUP> Dissociative Recombination

`2016ApJ...822..115K` | The Astrophysical Journal 2016 | first author: Kawaguchi, K. | arXiv: - | DOI: 10.3847/0004-637X/822/2/115

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: astrochemistry, milky_way_ism, high_z_galaxies
- Question: Can HF and H2F+ be detected in the z=0.89 absorber toward PKS 1830-211 and in Galactic sources, and does the dissociative recombination rate of H2F+ explain its low abundance?  
  > "we report the detection of HF in the z = 0.89 molecular absorber toward PKS 1830−211 and searches for H 2 F [+] toward PKS 1830−211 and other Galactic sources." (1. INTRODUCTION)
- Target **PKS 1830-211 (z=0.89 absorber, SW and NE images)**: coordinates _not stated_; z/distance z_abs = 0.88582  
  > "We adopt a redshift of z abs = 0.88582, heliocentric frame, giving v = 0 km s [−][1] for the absorption toward the SW image of PKS 1830−211." (2.1. ALMA Observations); distance from adopted in this paper  
  > "We adopt a redshift of z abs = 0.88582, heliocentric frame, giving v = 0 km s [−][1] for the absorption toward the SW image of PKS 1830−211." (2.1. ALMA Observations)
- Target **NGC 6334 I**: coordinates RA 17h20m53.32s, Dec -35d46m58.5s (J2000)  
  > "NGC 6334 I (high-mass star° ′ ° ′ forming region, _a_ 2000 : 17 20 53 32, _b_ 2000 : −35 46 58 5)" (2.2. Herschel Observations); z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2013.1.01099.S
- bands: Band 8 (403.5 GHz, H2F+) and Band 9 (653.5 GHz, HF)  
  > "redshifted to 403.5 GHz, i.e., in ALMA band 8) and HF J = 1–0 transition (rest frequency of 1232.4762 GHz, redshifted to 653.5 GHz, i.e., in ALMA band 9)" (2.1. ALMA Observations)
- frequencies and spectral setup: four 1.875 GHz spws, 960 channels of 1.938 MHz; band 8 centered ~401.5, 403.5, 413.8, 415.5 GHz; band 9 ~648.0, 649.9, 651.7, 653.6 GHz  
  > "four different spectral windows of 1.875 GHz, each counting 960 channels separated by 1.938 MHz" (2.1. ALMA Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.39"x0.29" (PA -84°) band 8; 0.21"x0.19" (PA 64°) band 9  
  > "we obtained synthesized beams of 0 39 × 0 29 (position angle PA = −84°) in band 8 and 0 21 × 0 19 (PA = 64°) in band 9." (2.1. ALMA Observations)
- max recoverable scale: _not stated_
- sensitivity: rms 0.5% (1σ, of continuum) in 4.2 km/s channels, band 8  
  > "the rms noise level (1σ) is estimated to be 0.5% with 4.2 km s [−][1] channels." (4.1. ALMA Observations of the z = 0.89 Absorber)
- time on source: _not stated_
- observing dates: 2015 May 14 (band 8) and May 19 (band 9), Cycle 2  
  > "on 2015 May 14 and May 19, respectively" (2.1. ALMA Observations)
- pi or archival as stated: _not stated_
- Line: H2F+ 1_10–1_01 (760.929 GHz)
- Line: HF J=1–0 (1232.4762 GHz)
- Line: ortho-H2Cl+ 2_12–1_01 (781.6 GHz)
- Other facility **Herschel/HIFI**: H2F+ searches toward W31C, NGC 6334 I, GC IRS 21, 2Mass J1747  
  > "We used the dual-beam switch mode and the wideband spectrometer of the Herschel/HIFI spectrograph" (2.2. Herschel Observations)
- External data: H2 column densities ~2e22 (SW) and ~1e21 cm-2 (NE)  
  > "assuming an H 2 column density of ∼2 × 10 [22] cm [−][2] in SW and ∼1 × 10 [21] cm [−][2] in NE (Muller et al. 2014b)" (4.1. ALMA Observations) [from Muller et al. 2014b]
- External data: H2Cl+ column density in NGC 6334 I 1.7e13 cm-2  
  > "the abundance of H 2 Cl [+] has been reported to be 1.7 × 10 [13] cm [−][2] (Lis et al. 2010)" (4.2. Herschel Observations) [from Lis et al. 2010]

## Processing

### Calibration

- pipeline or manual: CASA, standard procedure; self-calibration with two-point-source model  
  > "The data calibration was done within the CASA [7] package, following a standard procedure." (2.1. ALMA Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: gain solutions from self-calibration of PKS 1830-211 visibilities using two point sources  
  > "The complex gain solutions were determined by self-calibration of the visibilities of PKS 1830−211, using a simple model of two point sources" (2.1. ALMA Observations)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 0.5  
  > "Using a Clean deconvolution (with Briggs weighting and robust parameter set to 0.5)" (2.1. ALMA Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: Hanning smoothing; HF spectra smoothed to 2.8 km/s, H2F+ to 4.2 km/s  
  > "Data were smoothed to a velocity resolution of 2.8 km s [−][1]." (Figure 1 caption)
- final beam: _not stated_
- final rms: _not stated_

### Not stated but needed to reproduce (our reading)

- CASA version
- flux calibrator and flux scale
- phase calibrator
- image size and cell size
- time on source and array configuration
- continuum level/flux of each image
- how absorption spectra were normalized and line velocity ranges for integration
- Herschel reduction details and observation IDs

## Analysis recipe

1. **extract spectra of both lensed images**: fit two point sources to visibilities with UVMULTIFIT  
  > "The spectra were extracted toward both images using the CASA-python task UVMULTIFIT (Martí-Vidal et al. 2014) to fit a model of two point sources to the visibilities." (2.1. ALMA Observations)
   - software: CASA, UVMULTIFIT
   - fitting: _not stated_
   - validation: SW spectrum divided by NE to remove bandpass residuals (Fig 1)  
  > "The normalized spectrum toward the SW image has been divided by that toward the NE image in order to remove small bandpass residuals." (Figure 1 caption)
2. **derive HF and H2F+ column densities**: optical depth tau = -ln(T_MB/T_back) and column density formula (Eq. 4) assuming all molecules in lowest level  
  > "Assuming that all HF molecules are in the ground state of J = 0, the column density is obtained by using the following formula:" (4.1. ALMA Observations)
   - parameter: SW linewidth 20 km/s, tau lower limit 4; NE tau 0.21  
  > "the lower limit of τ is estimated to be 4 from a simulation of the shape of the absorption line. On the other hand, the τ value of NE is obtained to be 0.21." (4.1. ALMA Observations)
   - assumption: Lowest ortho level only, ortho-to-para ratio 3, T_CMB 5.14 K at z=0.89  
  > "We assume that all ortho state molecules are present in the lowest 1 01 state." (4.1. ALMA Observations)
   - fitting: _not stated_
   - validation: _not stated_
3. **measure recombination rate constants in the laboratory**: time-resolved IR OPO laser absorption of pulsed discharge; fit decay with exponential (pseudo-first-order); electron density from Langmuir probe  
  > "the decay was found to be fitted to an exponential function as shown in Figure 4(c). This indicates that the reaction proceeds in the pseudo-firstorder scheme." (4.3. Laboratory Time-resolved Infrared Laser Spectroscopy)
   - parameter: _not stated_
   - assumption: Same electron density assumed for H2Cl+ as for H2F+  
  > "we assumed the same density for the production of H 2 Cl [+]." (4.3. Laboratory Time-resolved Infrared Laser Spectroscopy)
   - fitting: least-squares fits of decay curves  
  > "By least-squares fittings of the observed decay curves, we determined the k e [e [−] ] values" (4.3. Laboratory Time-resolved Infrared Laser Spectroscopy)
   - validation: H2F+ rate agrees with earlier flowing afterglow measurement  
  > "The present value for H 2 F + is in agreement with that obtained by the flowing afterglow experiment" (4.3. Laboratory Time-resolved Infrared Laser Spectroscopy)

## Software

- **CASA** : calibration and imaging of ALMA data  
  > "The data calibration was done within the CASA [7] package, following a standard procedure." (2.1. ALMA Observations)
- **UVMULTIFIT** : two-point-source fit to visibilities to extract spectra  
  > "The spectra were extracted toward both images using the CASA-python task UVMULTIFIT" (2.1. ALMA Observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| N(HF) SW | >3.4e14 | lower limit | cm-2 | 2 | column densities >3.4 × 10 [14] cm [−][2] and 0.18 × 10 [14] cm [−][2], respectively |
| N(HF) NE | 0.18e14 | not stated | cm-2 | 2 | column densities >3.4 × 10 [14] cm [−][2] and 0.18 × 10 [14] cm [−][2], respectively |
| N(H2F+) upper limit (3σ), total, SW | 8.8e11 | upper limit | cm-2 | 2 | upper limit (3σ) of 8.8 × 10 [11] cm [−][2] |
| N(H2F+) upper limit toward NGC 6334 I | 2.5e11 | upper limit | cm-2 | 0 | The upper limit on the column density was derived to be 2.5 × 10 [11] cm [−][2] in NGC 6334 I |

## Qualitative findings

- HF abundance in the absorber is close to Galactic diffuse clouds; H2F+ undetected while ortho-H2Cl+ is detected  
  > "The currently obtained abundance in the z = 0.89 absorber is thus close to the values of low-density Galactic clouds." (4.1. ALMA Observations)

## Claim tuples

- H: Is HF detectable in the z=0.89 absorber and is it a tracer of H2? | E: ALMA band 9 HF 1-0 absorption toward both images | R: HF detected in SW (saturated) and NE | F: HF/H2 similar to Galactic diffuse clouds | **supported**
- H: Is H2F+ present in these sources? | E: ALMA band 8 and Herschel HIFI searches | R: No detection; upper limits 1/386 of HF and 1/16 of H2Cl+ | F: H2F+ much less abundant than H2Cl+ | **supported**
- H: Does faster recombination explain low H2F+? | E: Laboratory rate constants | R: rates differ by only ~2 | F: Formation mechanism is the main factor | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Absorption profile time variability limits comparison of spectra from different epochs  
  > "somewhat limit the direct comparison of spectra taken at different epochs." (4.1. ALMA Observations)
- Caveat (inferred, ours): Saturated SW HF gives only lower limit
- Caveat (inferred, ours): Ortho-to-para ratio of 3 assumed for H2F+
- Caveat (inferred, ours): Lab rate measured at 209 K from a high rotational level, extrapolated to 50 K with unverified temperature dependence

## Reproducibility

- Data public (paper): ALMA project code given  
  > "This paper makes use of the following ALMA data: ADS/ JAO.ALMA#2013.1.01099.S." (6. SUMMARY)
- Products in archive: _not stated_
- Missing: CASA version and calibrator details
- Missing: imaging parameters
- Missing: spectral normalization recipe
- Data volume (inferred): tens of GB
- Score (inferred): 3/5, Public ALMA data and clear column-density method, but calibration and imaging details are sparse.
- Rediscovery candidate: no, Calibration and extraction details insufficient, and half the paper is laboratory work.

## Links

- Method: Martí-Vidal et al. 2014 (UVMULTIFIT)
- Companion: Muller et al. 2014a (H2Cl+ detection toward PKS 1830-211)

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
 "numeric_results": 4,
 "numeric_problems": 0,
 "fill": {
  "facts": 66,
  "stated": 30,
  "rate": 0.455
 },
 "evidence_ok": true
}
```
