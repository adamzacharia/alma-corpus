# A D/H ratio consistent with Earth's water in Halley-type comet 12P from ALMA HDO mapping

`2025NatAs...9.1476C` | Nature Astronomy 2025 | first author: Cordiner, M. A. | arXiv: 2508.05925 | DOI: 10.1038/s41550-025-02614-7

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: solar_system
- Question: What is the D/H ratio in water of Halley-type comet 12P/Pons-Brooks, and is it consistent with Earth's ocean water and the origin of H2O in the coma?  
  > "imply a coma D/H ratio (for water) of $(1.71\pm0.44)\times10^{-4}$" (abstract)
- Target **12P/Pons-Brooks**: coordinates _not stated_; z/distance perihelion r_H=0.78 au on 2024 April 21; phase angle ~30 deg  
  > "12P/Pons-Brooks is a Halley-type comet on a highly elliptical 71-year orbit, last reaching perihelion at $r_H=0.78$ au on 2024 April 21." (main text); distance from _not stated_

## Data provenance

- ALMA projects: 2023.1.01143.L
- bands: Band 6 (HDO, CH3OH ~242 GHz) and Band 5 (H2O 183 GHz, CH3OH 193 GHz)  
  > "CH$_3$OH ($J_K=5_K$–$4_K$ band) near 242 GHz in Band 6, with a spectral resolution of 488 kHz." (Methods, ALMA Observations)
- frequencies and spectral setup: Band 6: 488 kHz resolution; Band 5: 122 kHz resolution  
  > "were observed simultaneously in Band 5, at 122 kHz resolution." (Methods, ALMA Observations)
- continuum bandwidth: ~4 GHz aggregate  
  > "An aggregate continuum bandwidth of $\sim4$ GHz was also observed simultaneously with the spectral lines in each setup." (Methods, ALMA Observations)
- arrays: _not stated_
- configurations: C-2 to C-3, baselines 15–500 m, 41–46 antennas  
  > "spanning baselines 15–500 m (corresponding to ALMA configurations C-2 to C-3)" (Methods, ALMA Observations)
- baselines: _not stated_
- angular resolution: Band 6 beam 1.10''x1.03''; Band 5 beam 1.36''x0.95''  
  > "has a restoring beam FWHM of $1.10''\times1.03''$" (Methods, ALMA Observations)
- max recoverable scale: _not stated_
- sensitivity: sigma_c = 0.68 mJy at 242 GHz; 37 mJy at 183 GHz; 2.8 mJy at 193 GHz (per channel)  
  > "$\sigma_c=37$ mJy at 183 GHz (H$_2$O) and $\sigma_c=2.8$ mJy at 193 GHz (CH$_3$OH)" (Methods, ALMA Observations)
- time on source: _not stated_
- observing dates: 10 sessions (6 dates), 2024 April 18 to May 4  
  > "spread over 10 observing sessions (6 dates) between UT 2024 April 18 and 2024 May 4" (Methods, ALMA Observations)
- pi or archival as stated: ALMA Large Program 2023.1.01143.L (PI M. Cordiner)  
  > "program 2023.1.01143.L (PI: M. Cordiner)" (Methods, ALMA Observations)
- Line: HDO 2(1,1)-2(1,2) (241.561 GHz)
- Line: p-H2O 3(1,3)-2(2,0) (183.310 GHz)
- Line: CH3OH J_K=5_K-4_K band (~242 GHz) and 4_K-3_K band (193 GHz) (near 242 GHz; 193 GHz)
- Other facility **NASA IRTF/iSHELL**: CH3OH/H2O production rate ratios, rotational temperatures, and H2O OPR  
  > "The critical role of IR observations in this study is to demonstrate that the CH$_3$OH/H$_2$O relative abundances in the coma did not vary significantly over time" (Methods, IRTF Observations)
- Other facility **SOHO/SWAN**: Water production rates showing variability (private communication)  
  > "the comet’s water production rate observed by SOHO/SWAN was variable over this period (M. Combi, private communication 2024)" (main text)
- External data: Spectroscopic parameters for H2O, HDO, CH3OH from LAMDA  
  > "Spectroscopic parameters for H$_2$O, HDO and CH$_3$OH were taken from the Leiden Atomic and Molecular Database LAMDA database (cite: van20)." (Methods, Radiative Transfer Modeling) [from (cite: van20)]
- External data: Updated p-H2O–H2O collisional excitation rates  
  > "Updated p-H$_2$O–H$_2$O collisional excitation rates were included from (cite: man24)" (Methods, Radiative Transfer Modeling) [from (cite: man24)]
- External data: Radiative pumping rates from Planetary Spectrum Generator  
  > "Radiative pumping rates were obtained from the Planetary Spectrum Generator (cite: vil18)" (Methods, Radiative Transfer Modeling) [from (cite: vil18)]
- External data: Photodissociation rates for the active Sun  
  > "Molecular photodissociation rates for the active Sun were obtained from (cite: hue15)." (Methods, Radiative Transfer Modeling) [from (cite: hue15)]
- External data: Literature D/H values of other comets used in comparison (Fig 3), incl. revised values  
  > "including the revised values for comets 1P/Halley (cite: bro12), C/1996 B2 (cite: lis19) and 67P/Churyumov-Gerasimenko (cite: mandt24)" (main text) [from (cite: nom23) and references therein]

## Processing

### Calibration

- pipeline or manual: JAO automated pipeline calibration scripts  
  > "Data were flagged and calibrated in CASA version 6.5 (Ref. (cite: casa22)) using automated pipeline calibration scripts supplied by the Joint ALMA Observatory (JAO)." (Methods, ALMA Observations)
- casa version: CASA 6.5  
  > "Data were flagged and calibrated in CASA version 6.5" (Methods, ALMA Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0423-0120 (amplitude and bandpass); phase: J0407+0742, J0401+0413, J0424+0036, J0309+1029  
  > "Calibration of the amplitudes and bandpasses was performed using observations of the nearby quasar J0423-0120" (Methods, ALMA Observations)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: tclean (Högbom)  
  > "Imaging and deconvolution was performed using the `tclean` (Högbom) algorithm" (Methods, ALMA Observations)
- deconvolver: Högbom  
  > "Imaging and deconvolution was performed using the `tclean` (Högbom) algorithm" (Methods, ALMA Observations)
- weighting robust: natural weighting  
  > "with natural weighting, a flux threshold of twice the RMS noise per channel" (Methods, ALMA Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: 10''-diameter circular mask about phase center; threshold 2 sigma_c  
  > "a flux threshold of twice the RMS noise per channel ($\sigma_c$) in each image, and a $10''$-diameter circular mask about the phase center" (Methods, ALMA Observations)
- multiscale scales: _not stated_
- continuum subtraction: uvcontsub, 2nd-order polynomial, line channels excluded  
  > "The thermal continuum was then subtracted from the visibilities using the `uvcontsub` task, with a 2nd-order polynomial fit, excluding channels containing spectral line emission." (Methods, ALMA Observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: 9 Band 6 sessions time-averaged and concatenated into one measurement set  
  > "The 9 sets of Band 6 observations were then time-averaged and concatenated together to form a single measurement set." (Methods, ALMA Observations)
- smoothing: Spectral axis averaged across pairs of adjacent channels after cvel2 to rest frame of comet  
  > "then averaged across pairs of adjacent channels to reduce the frequency correlation introduced as a result of Hanning smoothing by the ALMA correlator" (Methods, ALMA Observations)
- final beam: Band 6 1.10''x1.03''; Band 5 1.36''x0.95''  
  > "In Band 5, the beam FWHM is $1.36''\times0.95''$" (Methods, ALMA Observations)
- final rms: _not stated_

### Inherited from earlier work

- Fourier-domain visibility modeling approach with SUBLIME  
  > "Following the methods of Cordiner et al. (cite: cor23), the calibrated, continuum-subtracted ALMA data were modeled directly" (main text) [from (cite: cor23)]
- Coma temperature retrieval with smoothed segmented linear T(r)  
  > "For the coma temperature retrievals, we followed the methodology of (cite: cor23), incorporating a smoothed, segmented, linear $T(r)$ profile." (Methods, Radiative Transfer Modeling) [from (cite: cor23)]
- IRTF observing and data reduction procedures  
  > "The observing and data reduction followed the procedures outlined in (cite: dis17) and references therein." (Methods, IRTF Observations) [from (cite: dis17)]
- OPR retrieval methodology  
  > "using the most detailed methodology described by (cite: bon13)" (Methods, IRTF Observations) [from (cite: bon13)]

### Not stated but needed to reproduce (our reading)

- Exact SUBLIME version and configuration/input files, grid parameters
- Initial guesses and bounds for lmfit parameters
- Line-free channels used for uvcontsub
- Specific ephemeris offsets per session (in Supplementary Table 1, not provided)
- Details of the T(r) segment nodes and the log-linear velocity law implementation
- Flux-scale uncertainty and any self-calibration choices
- Pipeline version

## Analysis recipe

1. **Calibrate and prepare visibilities**: Pipeline calibration, phaseshift to correct comet offset, uvcontsub, cvel2 to comet rest frame, channel averaging, concatenation of Band 6 sessions  
  > "this offset was corrected in each measurement set, by fitting a point-source to the continuum visibility data and using the CASA `phaseshift` task to move the fitted flux peak to the phase center." (Methods, ALMA Observations)
   - software: CASA
   - parameter: 2nd-order polynomial continuum fit  
  > "with a 2nd-order polynomial fit, excluding channels containing spectral line emission" (Methods, ALMA Observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **Image and make moment maps**: tclean natural weighting; moment 0 from contiguous channels above 2 sigma with peak >3 sigma  
  > "Significant line emission (identified as contiguous channels above the $2\sigma$ level, as part of a feature with a peak strength $>3\sigma$) was spectrally integrated" (Methods, ALMA Observations)
   - software: CASA, Splatalogue
   - fitting: _not stated_
   - validation: _not stated_
3. **Fit CH3OH for coma temperature, velocity and Q(H2O) proxy**: SUBLIME 3D non-LTE model fitted to visibilities with two-region (hemispherically asymmetric) coma, segmented T(r), accelerated velocity law  
  > "we first performed independent fits to the two CH$_3$OH datasets (April 18–25 and May 4), using models with variable $Q_1$, $Q_2$, $T_1(r)$, $T_2(r)$, $v_1$, $v_2$, $\phi$ and $\theta_{jet}$." (Methods, Radiative Transfer Modeling)
   - software: SUBLIME, lmfit
   - parameter: 4 T(r) segments for Apr 18–25; 3 for May 4  
  > "we found that four segments were required in the $T(r)$ profile to obtain a good fit to the observations, whereas on May 4, only 3 segments were required" (Methods, Radiative Transfer Modeling)
   - assumption: Steady-state coma; electron density scaling x_ne=0.2; collisional cross-section with H2O 5e-14 cm^-2; T1=T2  
  > "with an electron density scaling factor of $x_{ne}=0.2$" (Methods, Radiative Transfer Modeling)
   - fitting: chi^2 minimization with lmfit, Levenberg-Marquardt, across all baselines and spectral channels  
  > "the $\chi^2$ statistic was minimized across all baselines and spectral channels with the `lmfit` Python code (cite: new16), using the Levenberg-Marquardt nonlinear least-squares algorithm" (Methods, Radiative Transfer Modeling)
   - validation: Reduced chi-square near 1; abundance within 5% across velocity-law choices  
  > "all three models had best-fitting abundances within 5% of each other" (Methods, Radiative Transfer Modeling)
4. **Retrieve H2O production rate on May 4**: Iterate H2O and CH3OH retrievals until T(r) and Q(H2O) converge; fit p-H2O with theta_jet=90, phi=phi_STO, psi=PSAng fixed; v1, v2, Q1, Q2 free; OPR=3  
  > "we iteratively improved $T(r)$ and $Q({\rm H_2O})$ by running successive retrievals on CH$_3$OH and H$_2$O, feeding the results of one retrieval into the other, until the respective model parameters converged." (Methods, Radiative Transfer Modeling)
   - software: SUBLIME, lmfit
   - parameter: p-H2O/H2O fixed at 0.25  
  > "The p-H$_2$O/H$_2$O mixing ratio was fixed at 0.25 (see Methods)." (Table 1)
   - assumption: OPR = 3 (statistical equilibrium)  
  > "so this value was used to convert the ALMA p-H$_2$O production rate to a total $Q({\rm H_2O})$" (main text)
   - fitting: _not stated_
   - validation: Optical depth tau<0.3 for 183 GHz line  
  > "observed H$_2$O 183 GHz line was relatively optically thin ($\tau<0.3$)" (Methods, Radiative Transfer Modeling)
5. **Derive Q(H2O) for April 18–25 and HDO/H2O**: Vary Q(H2O) in CH3OH fits until abundance matched May 4 value (2.328%), giving 9.23e29 s^-1; then fit HDO visibilities with x(HDO), v1, v2, Q1/Q2 free  
  > "The required $Q({\rm H_2O})$ value of $9.23\times10^{29}$ s$^{-1}$ was then used to derive the HDO/H$_2$O mixing ratio ($x({\rm HDO})$) by fitting the HDO visibility data" (Methods, Radiative Transfer Modeling)
   - software: SUBLIME, lmfit
   - assumption: CH3OH/H2O constant over ALMA period, 20% added uncertainty  
  > "an additional uncertainty of 20% was assumed" (Methods, Radiative Transfer Modeling)
   - fitting: _not stated_
   - validation: Consistent with IRTF average Q(H2O) of (1.1±0.2)e30 s^-1  
  > "further validated by its consistency with the average IRTF value of $(1.1\pm0.2)\times10^{30}$ s$^{-1}$ observed April 18 and 22" (Methods, Radiative Transfer Modeling)
6. **Test parent vs daughter production scale length**: Haser daughter model; re-optimize for L_p in 0–2000 km; 99% limit at delta chi^2 = 6.63  
  > "crossed a threshold of $\chi^2-\chi_m^2=6.63$" (Methods, Radiative Transfer Modeling)
   - software: SUBLIME
   - fitting: cubic spline interpolation of chi^2(L_p)  
  > "using cubic spline interpolation between the points" (Methods, Radiative Transfer Modeling)
   - validation: _not stated_
7. **Error budget and D/H conversion**: Combine uncertainties in quadrature (26% total); convert HDO/H2O to D/H via H-atom statistics (factor 1/2)  
  > "to produce a total ($1\sigma$) error estimate of 26%" (Methods, Radiative Transfer Modeling)
   - fitting: _not stated_
   - validation: _not stated_
8. **Compare with other comets**: K-S tests between HTC, JFC, OCC D/H samples; mean D/H in comets  
  > "The distribution of D/H values in HTCs can be compared with that of JFCs and Oort cloud comets (OCCs) using the Kolmogorov-Smirnov (K-S) test" (main text)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 6.5: Calibration, phaseshift, uvcontsub, cvel2, tclean  
  > "Data were flagged and calibrated in CASA version 6.5" (Methods, ALMA Observations)
- **SUBLIME** : 3D non-LTE radiative transfer modelling of visibilities  
  > "modeled in the Fourier domain using the SUBLIME 3D radiative transfer software (cite: cor22)" (Methods, Radiative Transfer Modeling)
- **lmfit** : Levenberg-Marquardt chi^2 minimization  
  > "with the `lmfit` Python code (cite: new16)" (Methods, Radiative Transfer Modeling)
- **Planetary Spectrum Generator** : Radiative pumping rates; IRTF atmospheric transmittance and fluorescence models  
  > "Radiative pumping rates were obtained from the Planetary Spectrum Generator (cite: vil18)" (Methods, Radiative Transfer Modeling)
- **Splatalogue** : Line identification  
  > "Spectral lines were identified using frequency and intensity data from the Splatalogue (cite: rem16)." (Methods, ALMA Observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Coma D/H in water | 1.71e-4 | ±0.44e-4 | dimensionless | 7 | imply a coma D/H ratio (for water) of $(1.71\pm0.44)\times10^{-4}$ |
| HDO/H2O mixing ratio, April 18–25 | 3.41e-4 | ±0.89e-4 | dimensionless | 5 | This leads to a final HDO/H$_2$O value of $(3.41\pm0.89)\times10^{-4}$. |
| Q(H2O) on May 4 | 4.71e29 | ±0.09e29 | s^-1 | 4 | $Q({\rm H_2O})=(4.71\pm0.09)\times10^{29}$ s$^{-1}$ |
| Q(H2O) for April 18–25 (derived) | 9.23e29 | 20% systematic added | s^-1 | 5 | The required $Q({\rm H_2O})$ value of $9.23\times10^{29}$ s$^{-1}$ |
| L_p upper limit H2O (99%) | 135 | not stated | km | 6 | the 99% confidence upper limits on their respective $L_p$ values are 135 km and 610 km |
| L_p upper limit HDO (99%) | 610 | not stated | km | 6 | the 99% confidence upper limits on their respective $L_p$ values are 135 km and 610 km |
| Mean cometary D/H | 2.9e-4 | std dev 1.4e-4 | dimensionless | 8 | the average D/H in cometary water is now $2.9\times10^{-4}$ (with a standard deviation of $1.4\times10^{-4}$) |
| K-S p value HTC vs OCC | 99.7% | not stated | percent | 8 | is 99.7%. The $p$ value for HTCs compared with JFCs is 77% |
| Total HDO/H2O error budget | 26% | not stated | percent | 7 | to produce a total ($1\sigma$) error estimate of 26% |

## Qualitative findings

- H2O and HDO maps consistent with nucleus (parent) sublimation.  
  > "The ALMA H$_2$O and HDO visibility data are found to be most consistent with nucleus sublimation ($L_p=0$)." (main text)
- No significant reason to distinguish comet families by D/H alone.  
  > "we find no significant reason to distinguish them based solely on D/H ratios" (main text)

## Claim tuples

- H: Is the D/H in water of HTC 12P consistent with Earth's oceans? | E: Fit SUBLIME model to ALMA HDO and H2O visibilities, with CH3OH as proxy for Q(H2O) | R: D/H = (1.71±0.44)e-4 vs VSMOW 1.56e-4 | F: Consistent with terrestrial ocean water, at the lower end of comet values | **supported**
- H: Do H2O and HDO come directly from the nucleus? | E: Chi^2 analysis of production scale length | R: L_p=0 preferred; upper limits 135 km (H2O), 610 km (HDO) | F: Consistent with nucleus outgassing | **supported**
- H: Do comet dynamical families differ in D/H? | E: K-S tests | R: p = 99.7% (HTC vs OCC), 77% (HTC vs JFC) | F: Differences cannot be established with current statistics | **partially**

## Reasoning

- Why this data: 12P is among the brightest and most active periodic comets, an excellent target for remote spectroscopy  
  > "12P is among the brightest and most active known periodic comets, and thus presented an excellent opportunity for remote (ground-based) spectroscopy during its 2024 apparition." (main text)
- Why this method: Fourier-domain fitting avoids imaging artifacts from gridding and deconvolution  
  > "The Fourier domain is used since it is native to the ALMA data, and therefore intrinsically avoids the imaging artifacts" (Methods, Radiative Transfer Modeling)
- Alternative: Distributed (icy grain) H2O source tested; no improvement in fit for parent-only model  
  > "the quality of the fits (as monitored using the $\chi^2$ statistic) did not significantly improve through addition of distributed (coma) sources" (main text)
- How they decided it was enough: _not stated_
- Limitation (authors): HDO and H2O observed ~2 weeks apart; Q(H2O) inferred via CH3OH proxy  
  > "Since H$_2$O and HDO were observed approximately 2 weeks apart" (main text)
- Limitation (authors): Low S/N of HDO leaves L_p unconstrained for 50% distributed case  
  > "the HDO $L_p$ value is unconstrained as a result of the lower signal-to-noise" (main text)
- Caveat (inferred, ours): Q(H2O) for HDO dates rests on assumed constant CH3OH/H2O ratio from 3 IRTF nights and a May 4 ratio
- Caveat (inferred, ours): Constant-velocity, simplified coma geometry for H2O/HDO
- Caveat (inferred, ours): OPR assumed 3 and p-H2O fraction 0.25
- Caveat (inferred, ours): Error budget partly assumed (20% systematic)

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: SUBLIME configuration and version
- Missing: Line-free channel ranges
- Missing: Supplementary Tables (geometry, line lists)
- Missing: IRTF reduced data
- Data volume (inferred): ~100s of GB raw across 10 sessions (Large Program)
- Score (inferred): 3/5, Project code and general recipe are given, but SUBLIME setup, supplementary tables and many model details are missing.
- Rediscovery candidate: no, Requires SUBLIME modeling and IRTF-derived inputs not fully specified.

## Links

- Method: (cite: cor22) (SUBLIME 3D model)
- Method: (cite: cor23) (Fourier-domain fitting and temperature methodology)
- Related: ALMA Large Program 2023.1.01143.L

## Checks

```json
{
 "quotes": 80,
 "quotes_ok": 80,
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
  "facts": 94,
  "stated": 63,
  "rate": 0.67
 },
 "evidence_ok": true
}
```
