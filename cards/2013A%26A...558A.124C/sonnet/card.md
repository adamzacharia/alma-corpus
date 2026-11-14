# ALMA observations of feeding and feedback in nearby Seyfert galaxies: an AGN-driven outflow in NGC 1433

`2013A&A...558A.124C` | Astronomy and Astrophysics 2013 | first author: Combes, F. | arXiv: 1309.7486 | DOI: 10.1051/0004-6361/201322288

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, agn_and_quasars
- Question: Does the molecular gas within the central ~100 pc of the Seyfert 2 galaxy NGC 1433 show AGN feeding and/or an AGN-driven outflow, as seen in CO(3-2) at 24 pc resolution?  
  > "The nearby distance (9.9 Mpc) and low inclination of 33$^\circ$ make NGC 1433 an ideal target to test and refine the scenario of AGN feeding and feedback" (Introduction)
- Target **NGC 1433**: coordinates RA 03h42m01.55s, Dec -47d13m19.5s (J2000, phase centre); new centre 03h42m01.49s, -47d13m20.2s  
  > "| Distance | 9.9 Mpc (1$''$ = 48 pc) | \(4\) |" (Table 1); "| $V_{\rm hel}$ | 1075 km s$^{-1}$ | \(1\) |" (Table 1); z/distance 9.9 Mpc; V_hel = 1075 km/s  
  > "| Distance | 9.9 Mpc (1$''$ = 48 pc) | \(4\) |" (Table 1); "| $V_{\rm hel}$ | 1075 km s$^{-1}$ | \(1\) |" (Table 1); distance from HyperLeda  
  > "| Distance | 9.9 Mpc (1$''$ = 48 pc) | \(4\) |" (Table 1); "| $V_{\rm hel}$ | 1075 km s$^{-1}$ | \(1\) |" (Table 1)

## Data provenance

- ALMA projects: 2011.0.00208.S
- bands: Band 7  
  > "The galaxy NGC 1433 was observed simultaneously in CO(3-2), HCO$^+$(4-3), HCN(4-3), and continuum, with Band 7." (Observations)
- frequencies and spectral setup: Sky frequencies 344.56, 355.46, 353.24, 343.27 GHz (CO(3-2), HCO+(4-3), HCN(4-3), continuum); 1.875 GHz per baseband; 0.488 MHz (~0.42 km/s) resolution  
  > "The sky frequencies were 344.56 GHz, 355.46 GHz, 353.24 GHz, and 343.27 GHz, respectively." (Observations); "dual polarization mode with 1.875 GHz total bandwidth per baseband, and a velocity resolution of 0.488 MHz $\sim$0.42 km/s" (Observations)
- continuum bandwidth: _not stated_
- arrays: ALMA Cycle 0, 19 antennae  
  > "The observations were carried out with the Atacama Large Millimeter/submillimeter Array (ALMA) telescope in Cycle 0, with 19 antennae, during June and July 2012." (Observations)
- configurations: Cycle 0 extended configuration  
  > "The Cycle 0 extended configuration provides in Band 7 a beam of 0.56$''$$\times$0.42$''$, with a PA of 85$^\circ$." (Observations)
- baselines: _not stated_
- angular resolution: 0.56" x 0.42", PA 85 deg (~24 pc)  
  > "The Cycle 0 extended configuration provides in Band 7 a beam of 0.56$''$$\times$0.42$''$, with a PA of 85$^\circ$." (Observations)
- max recoverable scale: extended emission filtered out above ~3" per channel map  
  > "Because of missing short spacings, extended emission was filtered out at scales larger than $\sim$3$''$  in each channel map." (Observations)
- sensitivity: rms 0.09 mJy/beam continuum; ~3 mJy/beam in line channel maps (~170 mK)  
  > "The total integration time provided an rms of 0.09 mJy/beam in the continuum, and $\sim$3 mJy/beam in the line channel maps" (Observations)
- time on source: 27 minutes per block, three blocks, total duration two hours  
  > "For each period, NGC 1433 was observed for 27 minutes; the median system temperatures were T$_{sys}$ = 140, 230, and 160 K." (Observations)
- observing dates: June and July 2012  
  > "with 19 antennae, during June and July 2012" (Observations)
- pi or archival as stated: _not stated_
- Line: CO 3-2 (not stated)
- Line: HCO+ 4-3 (not stated)
- Line: HCN 4-3 (not stated)
- Other facility **HST (Hubble Legacy Archive)**: B, V, I images compared to CO morphology  
  > "We superposed the CO map onto the HST maps in the B, V, and I filters." (Results)
- External data: Ionized gas (H-alpha) rotation curve and mass model, used for velocity residuals  
  > "Figure [\[fig:vrot\]](#fig:vrot) displays the residuals obtained, relative to the adopted H$\alpha$ rotation curve" (CO kinematics) [from Buta etal. 2001]
- External data: CO(1-0) SEST spectrum and central flux for comparison  
  > "Towards the central position, Bajaja etal. (1995) found a CO(1-0) spectrum peaking at T$_A^*$= 48mK, with FWHM=168 km/s" (CO luminosity) [from Bajaja etal. 1995]
- External data: Central 21 cm flux 3.4 mJy  
  > "The central emission is 3.4 mJy, quite similar to what is obtained at the ends of the bar from the HII regions." (Slope of radio-continuum emission) [from Ryder etal. 1996]
- External data: Galaxy inclination and PA  
  > "| Inclination | 33.0$^\circ$ | \(3\) |" (Table 1) [from Buta etal. 2001]

## Processing

### Calibration

- pipeline or manual: calibrated with CASA; pipeline vs manual not stated  
  > "The data were calibrated, imaged, and cleaned with the CASA software (v3.3; McMullin etal. 2007)" (Observations)
- casa version: CASA v3.3  
  > "The data were calibrated, imaged, and cleaned with the CASA software (v3.3; McMullin etal. 2007)" (Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0334-401  
  > "The flux calibration was done with the nearby quasar J0334-401, which is regularly monitored at ALMA" (Observations)
- flux scale uncertainty: 10%  
  > "and resulted in 10% accuracy." (Observations)
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: 0.1" per pixel  
  > "The final cube is 360x360 pixels with 0.1$''$ per pixel in the plane of the sky" (Observations)
- image size: 360x360 pixels, 60 channels of 4.24 km/s  
  > "The final cube is 360x360 pixels with 0.1$''$ per pixel in the plane of the sky, and has 60 channels of 4.24 km/s width." (Observations)
- masking: mask at 50 mJy emission level, then 30 mJy level  
  > "cleaned using first a mask at the 50 mJy emission level, and then the 30 mJy level." (Observations)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: applied to compute fluxes, not applied for plots  
  > "The final maps were corrected for primary beam attenuation to compute fluxes, but were kept uncorrected for the plots." (Observations)
- array combination: _not stated_
- smoothing: spectra smoothed to 4.88 MHz (4.24 km/s)  
  > "The spectra were then smoothed to 4.88 MHz (4.24 km/s) to build channel maps." (Observations)
- final beam: 0.56" x 0.42", PA 85 deg  
  > "a beam of 0.56$''$$\times$0.42$''$, with a PA of 85$^\circ$" (Observations)
- final rms: ~3 mJy/beam per channel; 0.09 mJy/beam continuum  
  > "an rms of 0.09 mJy/beam in the continuum, and $\sim$3 mJy/beam in the line channel maps" (Observations)

### Inherited from earlier work

- Adopted H-alpha rotation curve and mass model used as the regular velocity field  
  > "In a previous paper (Buta etal. 2001), a detailed mass model of NGC 1433 was performed from NIR photometry and H$\alpha$ spectroscopy." (CO kinematics) [from Buta etal. 2001]
- Dust absorption cross section (Draine & Lee) as in Dumke et al. for N(H2) from continuum  
  > "assuming the same Draine & Lee (1984) dust absorption cross section as described in Dumke etal. (1997) for a solar metallicity" (Dust continuum emission) [from Draine & Lee (1984); Dumke etal. (1997)]
- Jet power from radio luminosity formula  
  > "we can estimate the jet power from the formula proposed by Birzan etal. (2008, their Eq. 16)" (Discussion and summary) [from Birzan etal. 2008]

### Not stated but needed to reproduce (our reading)

- Clean threshold, weighting/robust and deconvolver used in tclean/clean
- Calibration details (bandpass/phase calibrators, pipeline vs manual script)
- Line-free channels and continuum subtraction method
- Which spectral window gave the continuum and how it was imaged
- Exact velocity-residual and outflow-region definitions and how H-alpha curve was deprojected
- Fourier decomposition details (bins, deprojection parameters)
- Conversion from IRAS fluxes to 24 K dust temperature

## Analysis recipe

1. **Calibrate and image CO(3-2) cube and continuum**: Calibration, imaging, cleaning in CASA; analysis in GILDAS  
  > "the analysis was then finalized with the GILDAS software (Guilloteau & Lucas 2000)" (Observations)
   - software: CASA, GILDAS
   - parameter: 360x360 pixels of 0.1", 60 channels of 4.24 km/s, masks at 50 then 30 mJy  
  > "The final cube is 360x360 pixels with 0.1$''$ per pixel in the plane of the sky, and has 60 channels of 4.24 km/s width." (Observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **Measure line fluxes and decompose the spectrum**: Clipped cube (<2 sigma = 6 mJy/beam set to zero); Gaussian decomposition of total spectrum into three components; fluxes after primary beam correction  
  > "To measure fluxes we used a clipped cube where all pixel values $<$2$\sigma$ (6 mJy/beam) were set to zero." (Molecular gas distribution and morphology); "A Gaussian decomposition in three components has been performed on the spectrum" (CO kinematics)
   - software: GILDAS
   - fitting: Gaussian fits; sampler/priors not stated  
  > "Total = Gaussian fit, assuming only one component, C1/C1/C3 represent three velocity-component decomposition" (Observations (Table: CO(3-2) line fluxes))
   - validation: _not stated_
3. **Derive H2 masses and column densities**: Standard CO-to-H2 factor with assumed CO(3-2)/CO(1-0) ratio; optically thin lower bound; dust continuum column density  
  > "Assuming a CO(3-2)/CO(1-0) flux ratio of $\sim$5" (CO luminosity)
   - assumption: X = 2.3e20 cm-2/(K km/s), CO(3-2)/CO(1-0) flux ratio ~5, CO abundance 6e-5, D = 9.9 Mpc, dust T = 24 K with beta=2  
  > "with the standard CO-to-H$_2$ conversion factor of 2.3 10$^{20}$cm$^{-2}$/(Kkm/s)" (CO luminosity); "the average temperature of the dust in NGC 1433 can be estimated as 24 K, assuming that the dust opacity has a dependence in frequency of $\nu^\beta$, with $\beta=2$" (Dust continuum emission)
   - fitting: _not stated_
   - validation: Comparison with SEST CO(1-0) flux  
  > "By comparison, Bajaja etal. (1995) find in their central 43$''$ beam a mass of 1.8 10$^8$ M$_\odot$" (CO luminosity)
4. **Identify the outflow from kinematics**: Velocity field, PV diagrams along major and minor axes, residuals relative to H-alpha rotation curve, summed CO flux in two 0.7"x1.2" regions  
  > "we have summed the CO flux within two regions of sizes 0.7$''$$\times$1.2$''$, centred on the red and blue outflow regions" (CO kinematics)
   - software: GILDAS
   - assumption: Outflow angle alpha to line of sight unknown; tan(alpha) ~ 1; velocity 100-200 km/s  
  > "Conservatively, the outflow velocity probably lies between 100 km/s and 200 km/s." (CO kinematics)
   - fitting: _not stated_
   - validation: Compared with H-alpha kinematics; inflow and black hole rotation alternatives argued against  
  > "for gas rotating in circular motion within the sphere of influence of the black hole, the velocity maxima should appear on the major axis and disappear on the minor axis" (Discussion and summary)
5. **Estimate outflow rate, energetics and drivers**: dM/dt ~ (Mv/d) tan(alpha); L_kin = 0.5 dM/dt v^2; compare with SFR (Kennicutt), AGN radiation momentum and jet power  
  > "the flow rate is of the order of dM/dt $\sim$ (Mv/d) tan$\alpha$= 7 tan$\alpha$ M$_\odot$/yr" (Discussion and summary)
   - assumption: M=3.6e6 Msun, d=1" ~ 50 pc, v=100 km/s  
  > "each high-velocity component has a projected radial extent from the centre of d=1$''$ $\sim$ 50  pc, and moves at a projected velocity of v=100 km/s" (Discussion and summary)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** v3.3: Calibration, imaging and cleaning  
  > "The data were calibrated, imaged, and cleaned with the CASA software (v3.3; McMullin etal. 2007)" (Observations)
- **GILDAS** : Final analysis  
  > "the analysis was then finalized with the GILDAS software (Guilloteau & Lucas 2000)" (Observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Total CO(3-2) flux | 234 | 1 | Jy km/s | 2 | / Total        /  234$\pm$ 1   / 1073.1$\pm$0.3 /   85.3$\pm$ 0.7   /   2.58    / |
| Total CO(3-2) FWHM | 85.3 | 0.7 | km/s | 2 | / Total        /  234$\pm$ 1   / 1073.1$\pm$0.3 /   85.3$\pm$ 0.7   /   2.58    / |
| Red outflow component CO flux | 10.1 | 0.1 | Jy km/s | 2 | / Red$^{(2)}$  / 10.1$\pm$ 0.1 / 1138.2$\pm$0.3 /   56.$\pm$ 0.7   /   0.17    / |
| Blue outflow component CO flux | 6.0 | 0.1 | Jy km/s | 2 | / Blue$^{(2)}$ / 6.0$\pm$ 0.1  / 1018.7$\pm$0.6 /   61.$\pm$ 1     /   0.09    / |
| Continuum peak (0.87 mm) | 0.5 | ~3 sigma detection | mJy | 1 | The peak emission is just detected at 3$\sigma$, about 0.5 mJy. |
| Molecular mass within primary beam | 5.2e7 | not stated | Msun | 3 | corresponds to a molecular mass M(H$_2$) = 5.2 10$^7$ M$_\odot$ |
| Outflow molecular mass (blue, red) | 1.3e6, 2.3e6 | not stated | Msun | 3 | we derive molecular masses of 1.3 10$^6$ and 2.3 10$^6$ M$\odot$ for the blue and red velocity components |
| Outflow mass rate | 7 tan(alpha) | factor of a few | Msun/yr | 5 | the flow rate is of the order of dM/dt $\sim$ (Mv/d) tan$\alpha$= 7 tan$\alpha$ M$_\odot$/yr |
| Jet power | 2e42 | not stated | erg/s | 5 | P$_{jet}$ = 2 10$^{42}$ erg/s |
| Dust-derived N(H2) at continuum peak | 4.5e22 | not stated | cm-2 | 3 | we find a molecular gas column density of N(H$_2$) = 4.5 10$^{22}$ cm$^{-2}$ |

## Qualitative findings

- CO shows a multi-arm flocculent nuclear spiral inside the nuclear ring, flowing to a ~200 pc pseudo-ring and on to the centre; HCO+ and HCN undetected  
  > "The dense gas tracers HCO$^+$ and HCN remain undetected, confirming the absence of very dense gas" (Discussion and summary)

## Claim tuples

- H: Is there a molecular outflow in the nucleus of NGC 1433? | E: CO(3-2) kinematics: PV diagrams and residuals relative to the H-alpha rotation curve | R: Red and blue components deviating by ~100 km/s projected at ~100 pc from the centre, ~7% of nuclear emission (3.6e6 Msun) | F: Tentative outflow, to be confirmed with higher resolution | **partially**
- H: Is the outflow driven by star formation or the AGN? | E: Compare outflow rate and power to SFR, AGN luminosity and jet power | R: Outflow rate ~40 times SFR; jet power ~2 orders above outflow kinetic luminosity | F: AGN (probably radio jet) helps drive the outflow | **partially**
- H: Does gas feed the AGN? | E: Morphology and kinematics of CO inside the nuclear ring | R: Gas flows inward via spiral to ~200 pc ring coinciding with the inner ILR and continues to the centre | F: Gas is presently fuelling the AGN | **supported**

## Reasoning

- Why this data: CO(3-2) traces high-density gas in circumnuclear regions at high resolution  
  > "CO line emission is therefore our best probe, and in particular CO(3-2), which traces the high density gas" (Introduction)
- Why this method: _not stated_
- Alternative: Inflow, streaming motions in the bar, and a massive BH rotation (M_BH 5.6e8 Msun) rejected as explanations of the high-velocity gas  
  > "we consider inflow to be unlikely" (CO kinematics)
- How they decided it was enough: _not stated_
- Limitation (authors): Missing short spacings filter extended emission above ~3"  
  > "Because of missing short spacings, extended emission was filtered out at scales larger than $\sim$3$''$  in each channel map." (Observations)
- Limitation (authors): Outflow estimate uncertain because the angle alpha is unknown  
  > "Although this estimate is uncertain by a factor of a few, given the unknown $\alpha$" (Discussion and summary)
- Caveat (inferred, ours): Outflow detection rests on a few ~100 km/s channels at moderate S/N, with no independent kinematic model
- Caveat (inferred, ours): Mass uses standard X factor, which is uncertain
- Caveat (inferred, ours): Continuum detected at only 3 sigma, so the recentring and dust torus interpretation are weak
- Caveat (inferred, ours): Single pointing smaller than the galaxy, so flux is incomplete

## Reproducibility

- Data public (paper): Cycle 0 data, project 2011.0.00208.S, cited in acknowledgements  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2011.0.00208.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Calibration scripts and cleaning parameters
- Missing: Outflow region and residual-map definition details
- Missing: Exact data of velocity-residual computation
- Data volume (inferred): ~5-20 GB raw
- Score (inferred): 3/5, Public Cycle 0 data and simple measurements, but imaging and kinematic residual details are sparse.
- Rediscovery candidate: no, Key results involve interpretive, loosely specified steps (outflow region selection, residuals), not a complete numeric recipe.

## Links

- Method: McMullin etal. 2007 (CASA)
- Method: Guilloteau & Lucas 2000 (GILDAS)
- Companion: Buta etal. 2001 (mass model and H-alpha rotation curve of NGC 1433)
- Companion: Boone etal. 2011 (CO(3-2) in nearby AGN, NUGA)
- Related: NUGA

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
 "numeric_results": 10,
 "numeric_problems": 0,
 "fill": {
  "facts": 76,
  "stated": 52,
  "rate": 0.684
 },
 "evidence_ok": true
}
```
