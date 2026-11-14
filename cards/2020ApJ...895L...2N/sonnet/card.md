# Substructure Formation in a Protostellar Disk of L1527 IRS

`2020ApJ...895L...2N` | The Astrophysical Journal Letters 2020 | first author: Nakatani, Riouhei | arXiv: 2004.14122 | DOI: 10.3847/2041-8213/ab8eaa

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, protoplanetary_disks
- Question: Does substructure form in the dust distribution of the young Class 0/I disk of L1527 IRS?  
  > "However, it has not yet been known if substructures can also form in even younger systems." (Introduction)
- Target **L1527 IRS (IRAS04368+2557)**: coordinates RA 04h39m53.870s, Dec +26d03m09.6s (J2000, ALMA phase center)  
  > "The pointing and phase referencing centers were on R.A.$=$04$^{\mbox{\scriptsize h}}$39$^{\mbox{\scriptsize m}}$53$^{\mbox{\scriptsize s}}$.870 (J2000)" (2.1 ALMA Observations); "the relatively short distance of $137{\,\rm pc}$ (cite: Torres2007)" (Introduction); z/distance 137 pc  
  > "The pointing and phase referencing centers were on R.A.$=$04$^{\mbox{\scriptsize h}}$39$^{\mbox{\scriptsize m}}$53$^{\mbox{\scriptsize s}}$.870 (J2000)" (2.1 ALMA Observations); "the relatively short distance of $137{\,\rm pc}$ (cite: Torres2007)" (Introduction); distance from Torres et al. 2007  
  > "The pointing and phase referencing centers were on R.A.$=$04$^{\mbox{\scriptsize h}}$39$^{\mbox{\scriptsize m}}$53$^{\mbox{\scriptsize s}}$.870 (J2000)" (2.1 ALMA Observations); "the relatively short distance of $137{\,\rm pc}$ (cite: Torres2007)" (Introduction)

## Data provenance

- ALMA projects: 2013.1.00858.S, 2016.A.00011.S, 2016.1.01203.S, 2017.1.00509.S
- bands: ALMA Bands 7, 4, 3; JVLA Q, K, C bands  
  > "multiwavelength observations with ALMA (Band 7, Band 4, Band 3) and JVLA (Q band, K band)." (Introduction)
- frequencies and spectral setup: Band 4: five spws at 146.965, 150.494, 150.432, 138.175, 138.346 GHz  
  > "which provided five spectral windows at \[146.965, 150.494, 150.432, 138.175, 138.346\] GHz central frequencies" (Observation Summaries)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: ALMA C34-7(6), C40-5, C40-8 (Band 7); C40-4, C40-7 (Band 4); C43-8 (Band 3); JVLA A and B  
  > "| 13       | ALMA-Band 7 | 20170729       | C40-5         | 338–352        | 17–1100" (Table 1)
- baselines: _not stated_
- angular resolution: Band 7 beam 0.072"x0.067"; Q band 0.087"x0.068"  
  > "| Band 7 | #12–13 | 0.5 | 0.072$''$$\times$0.067$''$; -11$^{\circ}$ | 0.15 | 370 | 1.9 |" (Table 3)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: ALMA 2015-2017; JVLA 2011-2013  
  > "The observations have been carried out from 2015 to 2017." (2.1 ALMA Observations); "They were carried out from 2011 to 2013" (2.2 JVLA Observations)
- pi or archival as stated: JVLA data archival (PI Melis); ALMA PIs Sakai and Oya  
  > "We have retrieved the archival National Radio Astronomical Observatory (NRAO) Karl G. Jansky Very Lary Array (JVLA) observations towards L1527 IRS." (2.2 JVLA Observations)
- Other facility **JVLA**: Q, K, C band continuum (archival)  
  > "They were carried out from 2011 to 2013, which were interleaved with Q band, K band, and C band observations in each epoch." (2.2 JVLA Observations)
- External data: Disk temperature model used for tau and mass  
  > "Using the temperature model of (cite: Tobin2013)," (3.1 Optical Thickness) [from Tobin2013]
- External data: Dust opacity model (kappa_7mm ≈ 0.02 cm2/g for amax≲100 um)  
  > "We adopt the opacity model of (cite: Birnstiel2018) in our discussions." (4.1 Optical Thickness) [from Birnstiel2018]
- Simulation/model as data: Thin smooth disk model with Sigma0 (R/1au)^-1, Sigma0=1e3-1e4 g/cm2, i=5 deg, observed with simobserve for 1-2 h  
  > "The surface density profile is given by a simple power-law as $\Sigma_0 (R/1{\,\rm au})^{-1}$." (3.1 Observed Images)

## Processing

### Calibration

- pipeline or manual: Epoch 1 pipeline; Epoch 2 manual; JVLA manual  
  > "We manually calibrated the observations of Epoch 2 using the 5.4.0 release of CASA." (Observation Summaries); "We manually calibrated the data following the standard calibration procedure" (2.2 JVLA Observations)
- casa version: ALMA Epoch 1 CASA 4.7.0, Epoch 2 5.4.0; JVLA 4.7.2  
  > "(release 4.7.0) and with Pipeline-Cycle4-R2-B" (Observation Summaries)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: JVLA 3C147 (Perley-Butler 2010/2013); ALMA J0510+1800 for Epoch 2 Band 4  
  > "by referencing the absolute flux from quasar 3C147" (Observation Summaries)
- flux scale uncertainty: _not stated_
- self calibration: Band 4 Epoch 2: three iterations of gain phase self-cal; JVLA not self-calibrated  
  > "we performed three iterations of gain phase self-calibration using the spectral window which has the broadest frequency width" (Observation Summaries)

### Imaging

- task: CASA TCLEAN MFS, nterm=1 (JVLA)  
  > "We performed the multi-frequency synthesis (MFS) imaging using the CASA task TCLEAN, by setting the parameter *nterm*$=$1." (Observation Summaries)
- deconvolver: _not stated_
- weighting robust: Briggs robust -2 (Q, K, Band 4), 0 (Q A-config), 0.5 (Band 3, 7)  
  > "| Band 3 | #7–9 | 0.5 | 0.155$''$$\times$0.068$''$; -2$^{\circ}$ | 0.020 | 23 | 5.4 |" (Table 3)
- uv taper: Q-band data beyond 1000 klambda flagged  
  > "Note that the data at $uv$ distances greater than 1000 $k\lambda$ was flagged for Q-band." (2.2 JVLA Observations)
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: Images smoothed to minimum common beam before spectral index and free-free subtraction  
  > "we smooth the two images by the minimum beam that covers the beams of the original two data" (3.1 Observed Images)
- final beam: _not stated_
- final rms: Q band 0.11 mJy/beam; Band 7 0.15 mJy/beam  
  > "| Q band | #2–6 | -2 | 0.087$''$$\times$0.068$''$; 76$^{\circ}$ | 0.11 | 3.7 | 0.96 |" (Table 3)

### Inherited from earlier work

- Disk temperature profile  
  > "based on observed temperature profile for L1527 IRS (cite: Tobin2013)" (3.1 Observed Images) [from Tobin2013]
- Free-free spectral index -0.1  
  > "is typical for optically-thin free-free emission (cite: Anglada2018)." (3.1 Observed Images) [from Anglada2018]

### Not stated but needed to reproduce (our reading)

- tclean parameters for ALMA bands (deconvolver, cell, image size, masks, threshold)
- Self-calibration details for ALMA Bands 3 and 7
- Details of proper-motion shift (FIXPLANET target coordinates)
- Spw/continuum channel selection for ALMA
- Procedure for 2D-Gaussian fitting (software, initial guesses)
- Beam-integration details of mass and Toomre Q calculation

## Analysis recipe

1. **Calibrate and image ALMA and JVLA continuum**: Standard CASA calibration; proper motion corrected with FIXPLANET; tclean imaging  
  > "we used the CASA task FIXPLANET to shift the target source to the expected coordinates on 01, Aug. 2017." (2.1 ALMA Observations)
   - software: CASA, tclean, fixplanet
   - fitting: _not stated_
   - validation: Q-band flux 3.7 mJy compared with 3.5 mJy at 43 GHz from Li2017  
  > "We recovered a $\sim$3.7 mJy total flux density at the mean frequency of $\sim$45 GHz" (Observation Summaries)
2. **Verify clumps are real**: Compare multi-epoch/config images, S/N, triple 2D-Gaussian fits, simobserve of smooth disk  
  > "we find that all of the Q-band data can be well fit by triple 2D-Gaussians" (3.1 Observed Images)
   - software: CASA simobserve
   - parameter: Sigma0 1e3–1e4 g/cm2, i=5 and 10 deg  
  > "The inclination is set to $i = 5\deg$." (3.1 Observed Images)
   - fitting: Triple 2D Gaussians  
  > "we find that all of the Q-band data can be well fit by triple 2D-Gaussians" (Results)
   - validation: Smooth disk cannot reproduce both A and B config results  
  > "A smooth disk model would not be capable of reproducing all of the observed features simultaneously." (3.1 Observed Images)
3. **Spectral index maps and free-free subtraction**: alpha from ln I ratio between smoothed images (3 sigma); subtract K-band scaled with index -0.1 from Q band  
  > "we smooth the Q and K band images with the minimum beam that covers both of the K- and Q-band beams to subtract the free-free contamination" (3.1 Observed Images)
   - assumption: free-free spectral index -0.1  
  > "where the adopted spectral index, $-0.1$, is typical for optically-thin free-free emission" (Results)
   - fitting: _not stated_
   - validation: consistent with measured alpha 7mm-1.3cm ~0  
  > "and is consistent with the aforementioned measurements of $\alpha _ {7\, {\rm mm}\text{--}1.3\,{\rm cm}}$." (Results)
4. **Optical depth and clump masses**: tau=-ln(1-Tb/Tmodel); mass from Eq. with kappa7mm=0.02 cm2/g integrated over beam area  
  > "Adopting $\kappa_{7\, {\rm mm}} = 0.02 \,{\rm cm}^2 {\rm \,g}^{-1}$, we estimate the lower limits of the clump mass" (4.2 Clump Masses)
   - assumption: amax ≲100 um; dust-to-gas 1%; Tobin2013 temperature, truncated within 5 au  
  > "we assume $a_{\rm max} \lesssim 100 \,{\rm \upmu m}$ in the following discussions." (Discussions: Optical Thickness)
   - fitting: _not stated_
   - validation: Acknowledged large opacity uncertainty (Woitke2016 order of magnitude higher)  
  > "The opacity model of (cite: Woitke2016) predicts about an order of magnitude larger absorption opacity than the adopted one in this study." (Discussions: Clump Masses)

## Software

- **CASA** 4.7.0, 4.7.2, 5.4.0: Calibration, imaging, simobserve, fixplanet  
  > "We use Common Astronomy Software Applications (cite: McMullin2007) package for the calibration and analysis." (2.1 ALMA Observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Clump-N dust mass lower limit | 0.40 | not stated | M_J | 4 | we estimate the lower limits of the clump mass to be $0.40 { \rm \, M_{\rm J}}$ for clump-N and $0.48 { \rm \, M_{\rm J}}$ for clump-S. |
| Clump-S dust mass lower limit | 0.48 | not stated | M_J | 4 | $0.40 { \rm \, M_{\rm J}}$ for clump-N and $0.48 { \rm \, M_{\rm J}}$ for clump-S. |
| Total dust mass lower limit | 2.7 | not stated | M_J | 4 | The lower limit of the total dust mass (with $3\sigma$ or higher detection) is $2.7 { \rm \, M_{\rm J}}$. |
| Disk mass | 0.26 | not stated | Msun | 4 | total disk mass of $M_{\rm disk} \sim 0.26{\, \rm M_\odot}$ for dust-to-gas mass ratios of 1% |
| Clump N/S distance from clump C | ~15 | not stated | au | 3 | Both of the clump-N and -S are located at a distance of $\sim 15{\,\rm au}$ from clump-C. |
| Clump brightness temperature | ≃60 | not stated | K | 3 | The brightness temperatures are similar ($\simeq 60 {\,\rm K}$) for all the clumps. |
| alpha_3mm-7mm at 30 au north | 2.49 | +0.60/-0.51 | dimensionless | 3 | The values of $\alpha_\text{3mm-7mm}$ are $\sim 2.49_{\,-0.51} ^{\,+0.60}$ and $2.77_{\,-0.54} ^{\,+0.67}$ at $d = 30{\,\rm au}$ |

## Qualitative findings

- Three clumps are present in Q-band after free-free subtraction; N and S are likely optically thick  
  > "The northern and southern clumps are located at a distance of $\sim 15{\,\rm au}$ from the central clump and are likely optically thick at $7\, {\rm mm}$ wavelength." (abstract)

## Claim tuples

- H: Substructure exists in the infant disk of L1527 IRS | E: Q-band multi-epoch imaging, Gaussian fits, simulated smooth disk | R: Three clumps detected consistently in independent epochs and configurations | F: Clumpy structure is physical and indicates substructure | **supported**
- H: Clumps are not free-free artifacts | E: Subtract scaled K-band image | R: Clumps remain | F: Dust origin | **supported**
- H: Clumps form a symmetric ring or spiral | E: Compare positions, masses, 7 mm historical data | R: N and S symmetric but N fainter | F: Ring/spiral plausible but individual clumps not ruled out | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Smooth disk with noise producing clumps rejected  
  > "It appears that a smooth disk requires a series of coincidences to be observed as clumpy structure found in our Q-band data." (3.1 Observed Images)
- How they decided it was enough: _not stated_
- Limitation (authors): Masses highly uncertain due to cm dust opacity  
  > "our estimated mass suffers from huge uncertainties mainly originating from poor understanding of dust opacity at cm-wavelengths." (4.2 Clump Masses)
- Caveat (inferred, ours): Clump-N detection marginal
- Caveat (inferred, ours): Low-S/N Q-band data with flagged long baselines
- Caveat (inferred, ours): Free-free subtraction assumes fixed index -0.1
- Caveat (inferred, ours): Mass depends on assumed opacity and temperature model

## Reproducibility

- Data public (paper): Archival JVLA and ALMA data cited with project codes  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2013.1.00858.S" (Acknowledgments)
- Products in archive: _not stated_
- Missing: ALMA tclean parameters
- Missing: Gaussian-fit procedure details
- Missing: Temperature model implementation
- Data volume (inferred): ~100-300 GB across ALMA and JVLA
- Score (inferred): 3/5, Public data and clear JVLA imaging parameters, but many ALMA imaging and fit details missing.
- Rediscovery candidate: no, Key detection is from JVLA, with incomplete ALMA recipe.

## Links

- Method: Birnstiel2018 (dust opacity model)
- Method: Tobin2013 (temperature model)
- Companion: Sakai2019 (previous Band 7 / Band 6 spectral index and warped disk)
- Related: DSHARP

## Checks

```json
{
 "quotes": 62,
 "quotes_ok": 62,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 4,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 68,
  "stated": 42,
  "rate": 0.618
 },
 "evidence_ok": true
}
```
