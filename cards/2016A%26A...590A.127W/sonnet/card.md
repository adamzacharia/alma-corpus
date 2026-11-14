# Resolving the extended atmosphere and the inner wind of Mira (o Ceti) with long ALMA baselines

`2016A&A...590A.127W` | Astronomy and Astrophysics 2016 | first author: Wong, K. T. | arXiv: 1603.03371 | DOI: 10.1051/0004-6361/201527867

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: evolved_stars
- Question: What are the physical conditions (density, temperature, SiO/H2O abundance, infall/outflow velocities) in Mira's extended atmosphere and inner wind, as probed by long-baseline ALMA continuum and SiO/H2O lines, and how do hydrodynamical models compare?  
  > "We derive the gas density, kinetic temperature, molecular abundance and outflow/infall velocities in Mira's extended atmosphere by modelling the SiO and H$_2$O lines." (abstract)
- Target **Mira A (o Ceti) and Mira B**: coordinates RA 02h19m20.795s, Dec -02d58m43.05s (fitted continuum centre)  
  > "The distance of the Mira AB system was estimated to be $110{\pm}9$ pc (cite: haniff1995)" (1 Introduction); "We have determined the centre of Mira A's continuum emission to be at $(\text{RA}, \text{Dec}) = (02^{\rm h}19^{\rm m}20{s}795" (2 Observations and data processing); z/distance 110 +/- 9 pc  
  > "The distance of the Mira AB system was estimated to be $110{\pm}9$ pc (cite: haniff1995)" (1 Introduction); "We have determined the centre of Mira A's continuum emission to be at $(\text{RA}, \text{Dec}) = (02^{\rm h}19^{\rm m}20{s}795" (2 Observations and data processing); distance from Haniff et al. 1995 (period-luminosity relation)  
  > "The distance of the Mira AB system was estimated to be $110{\pm}9$ pc (cite: haniff1995)" (1 Introduction); "We have determined the centre of Mira A's continuum emission to be at $(\text{RA}, \text{Dec}) = (02^{\rm h}19^{\rm m}20{s}795" (2 Observations and data processing)

## Data provenance

- ALMA projects: 2011.0.00014.SV
- bands: Band 3 and Band 6 observed; Band 6 (229 GHz) lines analysed  
  > "The Mira AB system was observed with ALMA on 2014 October 17 and 25 (ALMA Band 3) and on 2014 October 29 and November 1 (ALMA Band 6)" (2 Observations and data processing)
- frequencies and spectral setup: Band 6: continuum window at 229.6 GHz plus six 117.2 MHz line windows; channel 122.1 kHz (SiO), 61.0 kHz (H2O, H30alpha)  
  > "In Band 6, a continuum window at 229.6 GHz together with six spectral line windows of 117.2 MHz bandwidth around $^{28}$SiO ${\varv} = 0,1,2$ $J=5-4$" (2 Observations and data processing)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: longest 15.24 km; shortest 29.07 m (Band 3), 15.23 m (Band 6)  
  > "The shortest baselines (and the maximum number of antennae) in the observations of Bands 3 and 6 are $29.07\,{\rm m}$ (38) and $15.23\,{\rm m}$ (39), respectively." (2 Observations and data processing)
- angular resolution: ~30 mas at 220 GHz  
  > "With the longest baseline of 15 km, ALMA produces clearly resolved images of the continuum and molecular line emission/absorption at an angular resolution of ${\sim}30\,{\rm mas}$ at 220 GHz." (abstract)
- max recoverable scale: ~14.8" (Band 3 SiO), ~11.3" (Band 6 SiO), 10.5" (H2O)  
  > "The maximum recoverable scales[^3] of the SiO lines in Bands 3 and 6 are therefore ${\sim}14{\ensuremath{''}}8$ and ${\sim}11{\ensuremath{''}}3$, respectively" (2 Observations and data processing)
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: 2014 Oct 17, 25 (Band 3); 2014 Oct 29, Nov 1 (Band 6)  
  > "on 2014 October 29 and November 1 (ALMA Band 6) as part of the 2014 ALMA Long Baseline Campaign Science Verification" (2 Observations and data processing)
- pi or archival as stated: ALMA Science Verification data, calibrated by JAO/ARC staff  
  > "The SV data had been calibrated by staff members of the Joint ALMA Observatory (JAO) and the ALMA Regional Centres (ARCs)" (2 Observations and data processing)
- Line: 28SiO v=0 J=5-4 (217.104919 GHz)
- Line: 28SiO v=2 J=5-4 (214.088575 GHz)
- Line: H2O v2=1 5(5,0)-6(4,3) (232.68670 GHz)
- Line: 29SiO v=0 J=5-4 (214.385752 GHz)
- Other facility **AAVSO**: visual light-curve data used to derive stellar phase (~0.45)  
  > "Based on the visual magnitude data reported by the AAVSO, the stellar phase of Mira A is ${\sim}0.45$ at the time of this observation" (1 Introduction)
- External data: CODEX o54 model atmosphere structures (density, temperature, velocity) provided by developers  
  > "From the CODEX developers we have obtained the atmospheric structure information of the `o54` model series" (Kinematics) [from Ireland et al. 2008, 2011; Scholz et al. 2014 (cite: ireland2008; ireland2011; scholz2014)]
- External data: SiO-He collisional rate coefficients (scaled by 1.38 for H2)  
  > "extrapolated from the scaled (by 1.38) rate coefficients between SiO–He collisions as derived by (cite: dayou2006)" (SiO molecular data) [from Dayou & Balança 2006 (cite: dayou2006)]
- External data: Stellar radius R* = 12.3 mas  
  > "we adopt the value of $R_{\star}$ to be $12.3\,{\rm mas}$ (or $292\,R_{\astrosun}$) as determined by (cite: perrin2004)" (Previous observations) [from Perrin et al. 2004 (cite: perrin2004)]
- Simulation/model as data: CODEX o54 5400 Lsun hydrodynamical models at phases near 0.45 (250420, 261740, 286060, 287880, 289440, 291820) used as RATRAN inputs  
  > "the models at the stellar phases closest to this 2014 ALMA SV dataset (near phase 0.45) are models 250420[^1] (phase 0.38), 261740 (0.40)" (Kinematics)

## Processing

### Calibration

- pipeline or manual: Calibrated by JAO/ARC staff; self-calibration solutions from ALMA Science Portal applied  
  > "We downloaded the self-calibration solutions from the ALMA Science Portal and applied them to the preliminarily calibrated data, and then imaged the continuum and spectral line data." (2 Observations and data processing)
- casa version: CASA 4.2.2  
  > "We use CASA version 4.2.2 for the self-calibration and imaging" (2 Observations and data processing)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: ~20% absolute flux calibration  
  > "The real uncertainty of the flux is dominated by the absolute flux calibration, which is estimated to be of order 20%." (Table 2 notes)
- self calibration: Continuum solutions for continuum; strongest channels of SiO v=1 maser for line data  
  > "from the strongest spectral channels of the $^{28}$SiO ${\varv} = 1$ data, which exhibits strong maser emission, for the spectral line data" (2 Observations and data processing)

### Imaging

- task: CASA clean (Clark); continuum-subtracted and non-subtracted cubes  
  > "The spectral line image data cubes of the SiO and H$_2$O lines in ALMA Band 6 were created by the image deconvolution task, `clean`, in CASA." (2 Observations and data processing)
- deconvolver: _not stated_
- weighting robust: Briggs robust = 0.5  
  > "We weighted the visibilities with a robust (Briggs) parameter of $\mathcal{R}_{\rm Briggs}=0.5$" (2 Observations and data processing)
- uv taper: _not stated_
- cell size: 0.005"  
  > "The cell size and total size of the images are $0{\ensuremath{''}}005 \times 0{\ensuremath{''}}005$ and $15{\ensuremath{''}} \times 15{\ensuremath{''}}$, respectively." (2 Observations and data processing)
- image size: 15" x 15"  
  > "$0{\ensuremath{''}}005 \times 0{\ensuremath{''}}005$ and $15{\ensuremath{''}} \times 15{\ensuremath{''}}$, respectively." (2 Observations and data processing)
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: uvcontsub linear polynomial on line-free channels; but modelling uses non-subtracted cubes  
  > "The continuum was subtracted, with the `uvcontsub` task in CASA, by fitting a linear polynomial to the real and imaginary parts of the visibility data of the line-free (i.e., continuum-only) channels in each spectral window." (2 Observations and data processing)
- line free channels: _not stated_
- primary beam correction: not needed (primary beam ~28" at 220 GHz) except Fig. 1  
  > "At 220 GHz, the primary beam FWHM of the 12-m array is about $28\ensuremath{''}$, which is much larger than the size of the line emission/absorption, and therefore no primary beam correction is needed." (2 Observations and data processing)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: circular 0.032" (SiO), 0.030" (H2O)  
  > "We restored the images with a circular beam of FWHM $0{\ensuremath{''}}032$ for the $^{28}$SiO and $^{29}$SiO lines, and of FWHM $0{\ensuremath{''}}030$ for the H$_2$O $v_2=1$ line." (2 Observations and data processing)
- final rms: CLEAN threshold ~2-3 mJy/beam (~1.5x rms); sigma = 0.80 mJy/beam in SiO v=0 maps  
  > "CLEANed the images down to a threshold of ${\sim}2$–$3\,{\rm mJy}\,{\rm beam}^{-1}$, which is about 1.5 times the rms noise level." (2 Observations and data processing)

### Inherited from earlier work

- Calibration scripts, self-cal solutions and example imaging script from ALMA SV data package  
  > "Detailed calibration scripts, preliminarily calibrated data products (i.e., without self-calibration), and self-calibration solutions for both continuum and spectral line data are available at the ALMA Science Portal" (2 Observations and data processing) [from ALMA Science Portal SV data / ALMA Partnership 2015 (cite: lbc2014)]
- Continuum two-component model (uniform disk + Gaussian) following earlier analyses  
  > "The choices of model components are the similar to those adopted by (cite: mrm2015) and (cite: vro2015)." (Continuum analysis) [from Matthews et al. 2015; Vlemmings et al. 2015]

### Not stated but needed to reproduce (our reading)

- Exact line-free channel ranges used in uvcontsub (only said to differ from CASA Guide script)
- Exact clean parameters (niter, masks, spw/channel regridding) and which self-cal tables
- Full numerical RATRAN input profiles (density, T, velocity, abundance power-law indices) for Model 3
- RATRAN grid, photon count and convergence settings
- Formal fitting/goodness-of-fit method for the models (fit by eye, no stated metric)
- CODEX file contents are private (provided by developers)

## Analysis recipe

1. **Image continuum and fit continuum visibilities**: Fit uniform disk / Gaussian models to Band 6 continuum visibilities for Mira A and B  
  > "We fit the visibilities with the task `uvfit` (Revision 1.10, 2013 August) in Miriad." (Continuum analysis)
   - software: Miriad uvfit, CASA uvmodelfit, UVMULTIFIT
   - fitting: _not stated_
   - validation: Cross-checked uvfit with CASA uvmodelfit and UVMULTIFIT  
  > "We have cross-checked the $uv$-fitting results from the respective tasks in Miriad and CASA with single-component models, and both tasks return similar results." (Continuum analysis)
2. **Image SiO and H2O line cubes and extract spectra**: clean without continuum subtraction; spectra extracted at centre and at radii 32-160 mas along PA 0, 90, 180, 270 deg  
  > "We have extracted the SiO and H$_2$O spectra from the centre of Mira's continuum, and from an array of positions at radii 0$''$032, 0$''$064, 0$''$096, 0$''$128 and 0$''$160" (3.3 Spectra)
   - software: CASA clean
   - fitting: _not stated_
   - validation: Compared continuum-subtracted vs full-data spectra; CASA simulobserve test showed spurious bumps from CLEAN  
  > "we conclude that the "bump" in the continuum-subtracted spectrum is indeed a spurious feature introduced during the imaging (CLEAN) process." (Appendix CASA simulation)
3. **Radiative transfer modelling of SiO and H2O spectra**: 1-D RATRAN Monte Carlo models with power-law density/temperature, SiO two-step abundance, pseudo-continuum core, mixed infall/outflow velocity (Model 3); models convolved with the clean beam and compared by eye  
  > "RATRAN solves the coupled level population and radiative transfer equations with the Monte Carlo method and generates an output image cube for each of the modelled lines." (4 Radiative transfer modelling)
   - software: RATRAN, NumPy, SciPy
   - parameter: R_continuum = 3.60e13 cm, pseudo-continuum T = 2600 K  
  > "$R_{\rm continuum} = 3.60 \times 10^{13}\,{\rm cm}$ (21.8 mas) and $2600\,{\rm K}$, respectively." (4.3 Continuum emission)
   - parameter: SiO abundance drop at r_cond = 1.0e14 cm (~5 R*), outer ~1% of inner; H2O abundance 5.0e-6 (5.0e-5 near photosphere)  
  > "The radius at which SiO abundance drops significantly is assumed to be $r_{\rm cond} = 1.0 \times 10^{14}\,{\rm cm} \approx 5\,R_{\star}$ in our preferred model." (4.4 Modelling results)
   - assumption: Collisional partner purely rotational ground-state H2; spherical symmetry; distance 110 pc; R* = 12.3 mas  
  > "we assume that the gas in Mira's extended atmosphere is composed of purely neutral, molecular hydrogen (H$_2$) in its rotationally ground state, $J=0$." (5.1)
   - fitting: Empirical trial-and-error exploration of profiles; no sampler or likelihood  
  > "We have empirically explored different types of profiles that are plausible in the inner winds and circumstellar envelopes of evolved stars." (4.4 Modelling results)
   - validation: Sensitivity tests on density, abundance, temperature; alternative infall-only Models 1 and 2 rejected  
  > "We present here two models, Models 1 and 2, that fail to reproduce the observed SiO and H2O spectra around Mira in ALMA Band 6." (Infall-only models)
4. **Test CODEX hydrodynamical model structures**: Use CODEX o54 density (scaled by 1e4), temperature and velocity as RATRAN inputs; modify radio-continuum radius to hide strong shocks  
  > "we scale the number density of all CODEX models by a factor of $10^4$ such that the density outside the radio photosphere reaches at least $10^{12}\,{\rm cm}^{-3}$." (Kinematics)
   - software: RATRAN
   - assumption: m_part = 0.7 m_H2 + 0.3 m_He, helium mass fraction 0.3  
  > "$m_{\rm part} = 0.7 m_{{\rm H}_2} + 0.3 m_{{\rm He}} = 4.3372 \times 10^{-24}\,{\rm g}$" (Kinematics)
   - fitting: _not stated_
   - validation: Qualitative comparison of synthesized and observed spectra  
  > "Overall, considering the complexity of Mira’s extended atmosphere and inner wind, we believe that Model 3 can satisfactorily reproduce most of the features in the observed SiO and H$_2$O spectra in ALMA Band 6." (Radiative transfer modelling, Modelling results)

## Software

- **CASA** 4.2.2 (imaging); 4.4.0 for imrebin: self-calibration, uvcontsub, clean imaging, simobserve  
  > "We use CASA version 4.2.2 for the self-calibration and imaging (except for the image binning task as mentioned below)" (2 Observations and data processing)
- **Miriad** uvfit Revision 1.10, 2013 August: continuum visibility fitting  
  > "We fit the visibilities with the task `uvfit` (Revision 1.10, 2013 August) in Miriad." (Continuum analysis)
- **UVMULTIFIT** 2.1.4-r3: cross-check of continuum visibility fits  
  > "Using CASA/`UVMULTIFIT` (version 2.1.4-r3), we also obtained the similar results as reported above." (Continuum analysis)
- **RATRAN** : 1-D radiative transfer modelling of SiO and H2O lines  
  > "We have modelled the H$_2$O and SiO spectra with the radiative transfer code RATRAN" (4 Radiative transfer modelling)
- **matplotlib** 1.4.3: plotting  
  > "with the aid of the `matplotlib` plotting library (version 1.4.3)" (2 Observations and data processing)
- **NumPy/SciPy** 1.9.2 / 0.15.1: extrapolating SiO collisional rate coefficients and building molecular datafile  
  > "We use the Python libraries, NumPy[^14] (version 1.9.2) (cite: numpy) and SciPy[^15] (version 0.15.1)" (SiO molecular data)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Mira A radio photosphere brightness temperature (uniform disk) | 2611 | 51 K (565 K incl. flux calibration) | K | 1 | The brightness temperature of the uniform disk model of Mira A is found to be $2611 \pm 51\,{\rm K}$. |
| Mira A total continuum flux at 229.6 GHz | 149.70 | 0.04 | mJy | 1 | the total flux of Mira A is $149.70 \pm 0.04\,{\rm mJy}$ and that of Mira B is $11.19 \pm 0.04\,{\rm mJy}$ |
| Band 6 spectral index | 1.82 | 0.33 | dimensionless | 1 | we derive an independent spectral index (using the spectral line windows in Band 6 only) of $1.82 \pm 0.33$ |
| Mean 1.3 mm photosphere radius | 22.90 | 0.05 | mas | 1 | $R_{\rm 229\,GHz} = 22.90 \pm 0.05\,{\rm mas}$ ($543\,R_{\astrosun}$) |
| Shock velocity above radio photosphere | <~12 | not stated | km/s | 3 | with the shock velocity of $\Delta V \lesssim 12\,\ensuremath{\,{\rm km}\,{\rm s}^{-1}}$, near the radio photosphere of Mira |
| SiO depletion radius and gas temperature | >=4 R* (preferred 1.0e14 cm ~5 R*), T<~600 K | not stated | R*, K | 3 | gas-phase SiO starts to deplete at a radius of *at least* $4\,R_{\star}$ and a gas temperature of ${\lesssim}600\,{\rm K}$ |
| Gas density just beyond radio photosphere | 1e12-1e13 | not stated | cm^-3 | 3 | The gas density reaches $10^{12}$–$10^{13}\,{\rm cm}^{-3}$ just beyond the radio photosphere. |
| Maximum infall / expansion speeds | ~7.3 infall, ~4.0 expansion | not stated | km/s | 3 | The infall velocity immediately above this expanding layer is about $7.3\,\ensuremath{\,{\rm km}\,{\rm s}^{-1}}$, and the expansion velocity below this layer is about $4.0\,\ensuremath{\,{\rm km}\,{\rm s}^{-1}}$. |

## Qualitative findings

- Clumpy SiO emission within ~0.2" and an arc-like SiO feature to ~3" west  
  > "the SiO vibrational ground state emission extends to a larger projected radial distance than other directions" (3.2 Images)
- No compact hotspot found in continuum, contrary to Vlemmings et al. 2015  
  > "we have not found any sign of a compact (${\sim}4.7\,{\rm mas}$) hotspot ($T_b \sim 10\,000\,{\rm K}$) in Mira A's continuum" (Conclusions)

## Claim tuples

- H: Does Mira's millimetre continuum contain a compact bright hotspot? | E: Visibility fitting of Band 6 continuum with Miriad uvfit and UVMULTIFIT, reproducing Vlemmings et al. approach | R: Additional Gaussian is ~26 mas, not 4.7 mas; Tb(uniform disk)=2611 K | F: No evidence for a compact hotspot | **supported**
- H: What are the atmospheric structure and SiO depletion in Mira's inner wind? | E: RATRAN modelling of SiO and H2O spectra | R: Infall with shock <~12 km/s; SiO depletes beyond ~4 R* at T<~600 K | F: Inner dust shells probably not pure silicate | **partially**
- H: Can CODEX hydrodynamical models reproduce the observed spectra? | E: Use CODEX o54 structures as RATRAN inputs, with density scaled by 1e4 | R: Qualitatively reproduce spectra; after hiding strong shocks fit well | F: CODEX reproduces observations in remarkable detail; non-equilibrium models with extended hot regions not supported | **supported**
- H: Are the bumps in continuum-subtracted spectra real? | E: Weighting, iteration, long-baseline tests and simobserve simulation | R: Simulation reproduces the bump | F: The bump is a CLEAN artefact | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Non-subtracted images used because continuum-subtracted deconvolution produced spurious bumps  
  > "The images (and hence the spectra) deconvolved without continuum subtracted should better represent the real emission and absorption of the SiO and H$_2$O lines." (2 Observations and data processing)
- Alternative: Infall-only Models 1 and 2 rejected because of excess blueshifted emission  
  > "Our modelling shows that pure infall would produce too much emission in the blueshifted velocities of the spectra than is observed" (Preferred model)
- Alternative: Extended shock-heated layer (~4000 K) from non-equilibrium models rejected  
  > "the synthesised spectra exhibit very strong emission features that are absent in the data." (Early hydrodynamic models)
- How they decided it was enough: _not stated_
- Limitation (authors): 1-D model ignores clumps; collisional rate coefficients incomplete (no H, e-, excited H2), so density and abundance uncertain  
  > "the derived H$_2$ gas density from our RATRAN modelling is just a proxy of the densities of all possible collisional partners of SiO" (5.1)
- Limitation (authors): Clumpy structure in images may not all be real  
  > "the simulated ALMA observation suggests that the clumpy structures in the extended atmosphere and inner wind of Mira may not be all real." (Appendix CASA simulation)
- Caveat (inferred, ours): No formal fit or goodness-of-fit; models adjusted by eye, so parameters have no uncertainties
- Caveat (inferred, ours): Single-epoch snapshot; CODEX comparison needed arbitrary 1e4 density scaling and moved continuum radius
- Caveat (inferred, ours): CLEAN artefacts leave imaging reliability uncertain

## Reproducibility

- Data public (paper): SV data and scripts public on ALMA Science Portal  
  > "Detailed calibration scripts, preliminarily calibrated data products (i.e., without self-calibration), and self-calibration solutions for both continuum and spectral line data are available at the ALMA Science Portal" (2 Observations and data processing)
- Products in archive: _not stated_
- Missing: Exact RATRAN model input tables
- Missing: CODEX model files (privately supplied)
- Missing: Line-free channel ranges
- Data volume (inferred): ~50-100 GB for SV Band 6 measurement sets
- Score (inferred): 5/5, Public SV data and detailed imaging settings, but modelling is empirical with unpublished input profiles and no fit statistics.
- Rediscovery candidate: yes, Public data, continuum fits and imaging recipe are numeric and redoable; the radiative transfer part is only partly reproducible.

## Links

- Method: Hogerheijde & van der Tak 2000 (cite: ratran) (RATRAN radiative transfer code)
- Method: Martí-Vidal et al. 2014 (cite: uvmultifit) (UVMULTIFIT tool)
- Companion: Matthews, Reid & Menten 2015 (cite: mrm2015) (independent continuum analysis of same SV data)
- Companion: Vlemmings et al. 2015 (cite: vro2015) (claimed hotspot from same data)
- Companion: ALMA Partnership 2015 (cite: lbc2014) (Long Baseline Campaign SV description)
- Related: 2014 ALMA Long Baseline Campaign Science Verification

## Checks

```json
{
 "quotes": 78,
 "quotes_ok": 78,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 78,
  "stated": 57,
  "rate": 0.731
 },
 "evidence_ok": true
}
```
