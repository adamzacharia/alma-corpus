# The ALMA Lupus protoplanetary disk survey: evidence for compact gas disks and molecular rings from CN

`2019A&A...623A.150V` | Astronomy and Astrophysics 2019 | first author: van Terwisga, S. E. | arXiv: 1811.03071 | DOI: 10.1051/0004-6361/201834257

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type large_program_or_survey

## Science

- Fields: protoplanetary_disks, astrochemistry
- Question: What is the CN N=3-2 emission morphology and flux distribution of Lupus Class II disks, and what do they imply for gas disk sizes and UV irradiation, compared with DALI models?  
  > "We seek to characterize the CN emission from 94 Class II disks in the Lupus star forming region, compare it to observations in other regions, and interpret our observations with a grid of models." (abstract)
- Target **Lupus Class II disks (94 of 95)**: coordinates _not stated_; z/distance ~160 pc (typical)  
  > "$\sim 24$ AU radius at $160$ pc (the typical distance for these objects, based on *Gaia* DR2 (cite: gaiadr2; bailerjones18))" (Introduction); distance from Gaia DR2  
  > "$\sim 24$ AU radius at $160$ pc (the typical distance for these objects, based on *Gaia* DR2 (cite: gaiadr2; bailerjones18))" (Introduction)
- Target **Sz 71**: coordinates _not stated_; z/distance 155.89 pc  
  > "| Sz 71 | M1.5 | 155.89 | 0.33 | 0.42 | -9.03 |" (Table 1); distance from Gaia DR2  
  > "| Sz 71 | M1.5 | 155.89 | 0.33 | 0.42 | -9.03 |" (Table 1)
- Target **Sz 98**: coordinates _not stated_; z/distance 156.22 pc  
  > "| Sz 98 | K7 | 156.22 | 1.53 | 0.74 | -7.59 |" (Table 1); distance from Gaia DR2  
  > "| Sz 98 | K7 | 156.22 | 1.53 | 0.74 | -7.59 |" (Table 1)

## Data provenance

- ALMA projects: 2013.1.00220.S, 2015.1.00222.S, 2016.1.01239.S
- bands: Band 7 (CN, 13CO 3-2, 335 GHz continuum) and Band 6 (12CO 2-1, 225 GHz continuum)  
  > "The analysis in this article mainly focuses on the Band 7 results, and only uses the Band 6 $^{12}$CO $J=2-1$ data." (Observations and data reduction)
- frequencies and spectral setup: CN spectral resolution 0.24 MHz (binned to 0.5 km/s); 13CO 3-2 0.12 MHz  
  > "CN was observed at a lower spectral resolution of 0.24 MHz compared to $^{13}$CO $J=3-2$, for which a 0.12 MHz resolution was used." (Observations and data reduction)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: Band 7 continuum 0.3''x0.3''; CN cubes 0.37''x0.31'' (completion survey 0.22''x0.20'')  
  > "The resulting typical beam shape is $0.37'' \times 0.31''$; for the Lupus completion survey it is $0.22'' \times 0.20''$." (Observations and data reduction)
- max recoverable scale: _not stated_
- sensitivity: continuum 0.25 and 0.41 mJy/beam; typical CN channel rms 10 mJy/beam; median line flux noise 48 mJy km/s  
  > "The median noise level on the disk- and velocity integrated line fluxes is 48 mJy km s$^{-1}$." (Observations and data reduction)
- time on source: Band 7: 1 min (M-type) or 30 s (earlier types); Completion Survey 4.5 min in Band 7  
  > "In Band 7, all M-type stars were observed for 1 minute on source, while earlier-type stars were observed for 30 s" (Observations and data reduction)
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: CN N=3-2, J=7/2-5/2 (F=7/2-5/2, 9/2-7/2) (340.247770 GHz)
- Line: 13CO J=3-2 (not stated)
- Line: 12CO J=2-1 (not stated)
- Other facility **IRAM 30m (literature surveys)**: CN fluxes for Taurus-Auriga and rho Oph for comparison  
  > "who targeted 42 and 30 stars respectively with the IRAM 30-m single-dish telescope" (CN in Lupus versus Taurus-Auriga and rho Ophiuchi)
- Other facility **X-shooter**: stellar properties and accretion rates  
  > "intermediate-resolution *XSHOOTER* spectra of most sources in the sample have also been taken" (Introduction)
- External data: CN N=2-1 fluxes of Taurus-Auriga and rho Oph disks  
  > "we compare the Lupus CN observations to the results presented for CN in (cite: guilloteau13) and (cite: reboussin15)" (CN in Lupus versus Taurus-Auriga and rho Ophiuchi) [from (cite: guilloteau13); (cite: reboussin15)]
- External data: Stellar properties and accretion rates  
  > "optical spectroscopy (cite: alcala17) and comparing the stellar temperature and luminosity with evolutionary models by (cite: siess00)" (Observations and data reduction) [from (cite: alcala17); (cite: siess00)]
- External data: CN fluxes for IM Lup (N=2-1, SMA)  
  > "CN $N=2-1$ has been observed and detected towards IM Lup by (cite: oeberg11)." (Integrated CN flux survey results) [from (cite: oeberg11)]
- Simulation/model as data: DALI model grid (Rc 15-60 AU, Mdisk 2e-6 to 9e-2 Msun, UV excess) following Cazzoletti et al. 2018  
  > "samples disks with critical radii $R_c$ in the gas disk between 15 – 60 AU, and between $2\times10^{-6} - 9\times10^{-2} \,M_{\odot}$ in total disk mass." (CN models in the context of the Lupus population)

## Processing

### Calibration

- pipeline or manual: NRAO pipeline calibration  
  > "Pipeline calibration of the data was performed by the NRAO." (Observations and data reduction)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Titan (flux); J1427-4206 (bandpass); J1604-4228 and J1610-3958 (gain)  
  > "Flux, phase, bandpass and gain were calibrated using observations of Titan, J1427-4206, and J1604-4228 and J1610-3958 respectively." (Observations and data reduction)
- flux scale uncertainty: _not stated_
- self calibration: Phase and gain self-calibration for all objects, solution interval one minute  
  > "Phase- and gain self-calibration were performed for all objects at the largest solution interval of one minute (for the highest sensitivity)." (Observations and data reduction)

### Imaging

- task: CASA clean  
  > "Both continuum and line imaging were performed using the *clean* task in `CASA`." (Observations and data reduction)
- deconvolver: _not stated_
- weighting robust: Continuum: Briggs robust +0.5; CN cubes: natural weighting  
  > "imaged using Briggs weighting with a robust parameter of $+0.5$ after averaging over all continuum channels" (Observations and data reduction); "imaged using natural weighting to maximize $S/N$" (Observations and data reduction)
- uv taper: 0.5'' circular beam taper for 13CO in Sz 98  
  > "For $^{13}$CO in Sz 98, we additionally used $u,v$-plane tapering to create an $0.5''$ circular beam" (Observations and data reduction)
- cell size: _not stated_
- image size: _not stated_
- masking: Image-plane Keplerian masking for moment-zero maps of Sz 98 and Sz 71; line-width uncertainty 0.5 km/s (CN), 0.3 km/s (CO)  
  > "image-plane Keplerian masking was used to create their moment-zero maps (cite: loomis18; salinas17)" (Observations and data reduction)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: CN channels binned to 0.5 km/s  
  > "The CN channels were binned for an effective velocity resolution of 0.5 km s$^{-1}$" (Observations and data reduction)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Integrated flux measurement: circular aperture, curve of growth; non-detections beam-sized aperture, 10 km/s width  
  > "Integrated fluxes for these objects were determined in the same way as those in (cite: ansdell16; ansdell18)" (Integrated CN flux survey results) [from (cite: ansdell16; ansdell18)]
- Disk mass from 890 um flux, optically thin dust, gas-to-dust 100  
  > "leading to the same approximation used in (cite: ansdell16):" (CN models in the context of the Lupus population) [from (cite: ansdell16)]
- DALI initial abundances as in default Cazzoletti models  
  > "the initial overall abundances are the same as those used in the default models of (cite: cazzoletti18)" (CN models in the context of the Lupus population) [from (cite: cazzoletti18)]
- UV luminosity from accretion rate with 10000 K blackbody  
  > "Following (cite: kama16b), the UV is produced from the accretion rate, the stellar mass, and a 10000 K blackbody spectrum for the accreting material." (CN models in the context of the Lupus population) [from (cite: kama16b)]

### Not stated but needed to reproduce (our reading)

- Line-free channels / continuum subtraction method for CN cubes
- Detection criterion (S/N threshold) for the 36 detections
- CASA version used for imaging and self-calibration (only imfit 4.3.1 given)
- Image size and cell size
- Exact aperture sizes and per-source fluxes in the full table
- DALI input files, full chemistry settings and grid spacing
- MCMC priors, walkers and chain length for the uv fits
- Mapping of stellar mass and inclination into the Keplerian mask in detail

## Analysis recipe

1. **Measure integrated CN and 13CO fluxes**: Circular aperture photometry with curve-of-growth after integrating over channels with emission; beam-sized aperture and 10 km/s width for non-detections  
  > "circular aperture photometry was performed on the source position after integrating over all channels with significant emission" (Integrated CN flux survey results)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Test correlations with 13CO and continuum**: Modified Kendall rank test with upper limits  
  > "a modified Kendall-rank test taking into account upper limits was used (cite: isobe86)" (3.1)
   - fitting: _not stated_
   - validation: _not stated_
3. **Compare Lupus with Taurus and rho Oph**: Logrank test on CN flux distributions; literature N=2-1 J=5/2-3/2 fluxes scaled to N=3-2 with ratio 1.6  
  > "a single scaling factor was used here to obtain estimated CN $N=3-2,~J=7/2-5/2$ fluxes from these surveys, assuming an intermediate value of 1.6" (3.2)
   - assumption: ratio range 1.1-2.1 from Cazzoletti grid  
  > "this ratio is found to vary between 1.1 and 2.1" (3.2)
   - fitting: _not stated_
   - validation: _not stated_
4. **Compare fluxes to DALI grid for gas disk radii and UV**: Overplot DALI grid of CN 3-2 and 2-1 fluxes vs. disk mass (from 890 um flux) at several Rc and UV luminosities  
  > "the model grid is overplotted to both the Lupus data and the previous large samples" (3.3.1)
   - software: DALI
   - parameter: Mdisk = 100 F d^2/(kappa B(Tdust)), kappa=10 cm2/g at 1000 GHz, beta=1, Tdust=20 K  
  > "The $T_{\rm{dust}}$ used here is 20 K." (3.3)
   - assumption: gas-to-dust ratio 100, optically thin dust  
  > "we will assume that the gas-to-dust ratio of these disks is $100$ throughout, and that the dust is optically thin" (3.3)
   - fitting: _not stated_
   - validation: _not stated_
5. **Resolved CN rings in Sz 71 and Sz 98**: Keplerian-masked moment-zero maps, azimuthally averaged deprojected radial profiles  
  > "these profiles have been made by azimuthally averaging over the (deprojected) moment-zero maps" (4.1)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
6. **Search for continuum substructure in uv-plane**: Fit deprojected visibilities binned at 15 klambda with Gaussian core (Model 1) vs Gaussian core plus cosine-modulated Gaussian (Model 2)  
  > "subsequently the data were binned to $15$ k$\lambda$ bins in u,v-space" (uv-plane analysis)
   - software: PyMC, CASA
   - parameter: baselines up to 800 klambda (Sz 71) and 500 klambda (Sz 98)  
  > "Baselines up to 800 k$\lambda$ are used for our fit to Sz 71, and up to 500 k$\lambda$ for Sz 98" (uv-plane analysis)
   - fitting: MCMC with PyMC; priors and likelihood not stated  
  > "were obtained from MCMC-fits to the observations with the *PyMC* Python module." (uv-plane analysis)
   - validation: BIC comparison of Model 1 and 2  
  > "the two-component Gaussian model fits the continuum significantly better than the single-component one, when comparing the Bayesian Information Criterion" (uv-plane analysis)
7. **SED fitting to set disk structure**: RADMC3D grid for flaring, scale height, mass, inner radius, then DALI with small and settled large grains  
  > "we used the `RADMC3D`-code to globally constrain the flaring angle of the disk $\psi$, its scale height $h_r$, the disk mass $M_d$" (SED fitting procedure)
   - software: RADMC-3D, DALI
   - parameter: gamma=1, Rout ~200 AU, f in [0.85,0.99], chi in [0.2,1.0]  
  > "We explore only $f = [0.85, 0.99]$ and $\chi = [0.2, 1.0]$." (SED fitting procedure)
   - assumption: gas surface density = 100 x dust  
  > "The gas surface density is $100 \times$ the dust surface density and is not decoupled." (4.2.1)
   - assumption: R_V=3.1, A_V=0.5 (Sz 71), 1.0 (Sz 98)  
  > "We corrected the data for extinction using $R_V = 3.1$, and $A_V = 0.5$ mag and $1.0$ mag for Sz 71 and Sz 98 respectively" (SED fitting procedure)
   - fitting: _not stated_
   - validation: _not stated_
8. **Model CN rings with DALI**: Thermo-chemical DALI models with varied UV excess, ray-traced and convolved with 0.3'' Gaussian beam, compared to radial profiles and fluxes  
  > "After ray-tracing each model, the images were convolved with an $0.3''$ circular Gaussian beam" (4.2.1)
   - software: DALI
   - parameter: Sz 71: logL(912-1100A)=-5.2 (M1), -4.1 (M2); Sz 98: -3.4  
  > "| Sz 71 | M1     | -5.2                                     | 0.8                |" (Table 2)
   - assumption: UV excess varied up to factor 10 from accretion-based estimate  
  > "we have allowed for variations in the UV excess at these wavelengths of up to a factor 10" (4.2.1)
   - fitting: No formal fit; goal not a perfect fit  
  > "Our goal is not to provide a perfect fit to the data" (4.2)
   - validation: Compare model and observed radial profiles and integrated fluxes  
  > "the most remarkable feature of the CN emission, its concentration in a ring, is indeed reproduced in the model radial profiles, and occurs at radii within 20 AU of those seen in the data" (Model results)

## Software

- **CASA** 4.3.1 (imfit); others not stated: clean imaging, imfit for PA and inclination  
  > "using the *imfit* task in `CASA`, version `4.3.1`" (Observations and data reduction)
- **DALI** : physico-chemical modeling and ray-tracing of CN  
  > "Models constructed with the physico-chemical code `DALI` are used to study the integrated fluxes" (abstract)
- **RADMC-3D** : first-phase SED modeling  
  > "we used the `RADMC3D`-code" (SED fitting procedure)
- **PyMC** : MCMC fits of uv-plane continuum models  
  > "MCMC-fits to the observations with the *PyMC* Python module" (uv-plane analysis)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| CN detection rate | 36 of 94 (38%) | not stated | dimensionless | 1 | 36 of 94 sources are detected, for a total detection rate of $38\%$ across the sample. |
| Logrank p, Lupus vs Taurus CN distribution | 0.064 | not stated | dimensionless | 3 | ($p = 0.064$) |
| CN ring peak radius Sz 71 / Sz 98 | 40 / 60 | not stated | AU | 5 | The peak emission is found at 40 and 60 AU for Sz 71 and Sz 98 respectively |
| CN flux Sz 98 | 3.49 | 0.13 | Jy km/s | 1 | $3.49 \pm 0.13$ |
| CN flux Sz 71 | 2.35 | 0.95 | Jy km/s | 1 | $2.35 \pm 0.95$ |
| Unresolved continuum ring radius Sz 98 | 117 | not stated | AU | 6 | located at 117 AU |
| Delta BIC Sz 71 / Sz 98 | 1296.9 / 1382.7 | not stated | dimensionless | 6 | $\Delta_{\rm{BIC}} = 1296.9$ for Sz 71, and for Sz98, $\Delta_{\rm{BIC}} = 1382.7$ |
| DALI model CN flux Sz 71 M2 / Sz 98 M1 | 3.9 / 3.7 | not stated | Jy km/s | 8 | / Sz 98 / **M1** / -3.4                                     / 3.7                / |

## Qualitative findings

- CN flux is not correlated with 13CO or 890 um continuum flux, nor with estimated UV flux  
  > "neither the $890\,\mu$m continuum nor the $^{13}$CO $J=3-2$ line flux are correlated with the CN flux ($p > 0.05$)" (3.1)
- Models without substructure reproduce CN rings; no link to CO snowline  
  > "This implies that CN rings are purely chemical in nature" (Conclusions)

## Claim tuples

- H: Do Lupus disks have different CN fluxes than Taurus or rho Oph? | E: Logrank test of CN flux distributions using scaled single-dish fluxes | R: p=0.064 vs Taurus; rho Oph always significantly fainter | F: No significant Lupus-Taurus difference; rho Oph may be fainter | **partially**
- H: Do faint CN fluxes require compact gas disks? | E: Compare Lupus fluxes to DALI grid of Rc and UV | R: Faint sources need Rc <= 15 AU | F: A population of compact gas disks exists in Lupus | **supported**
- H: Are CN rings caused by continuum substructure or the CO snowline? | E: Compare CN profiles with uv-plane continuum fits and DALI models without substructure | R: Smooth models reproduce rings; no consistent link with continuum features or snowline | F: CN rings are chemical and trace UV irradiation | **supported**

## Reasoning

- Why this data: Complete, unbiased, uniformly observed Lupus sample, about 3x more sensitive than single-dish surveys  
  > "The sensitivity of this dataset is a factor of $\sim 3$ better than previous large single-dish CN surveys." (Introduction)
- Why this method: _not stated_
- Alternative: Optically thick continuum blanketing of CN excluded from low brightness temperatures (6.0 K, 4.4 K)  
  > "we can exclude this possibility" (4.1.1)
- How they decided it was enough: _not stated_
- Limitation (authors): Model absolute fluxes uncertain by a factor of a few; UV excess and accretion-to-UV conversion uncertain by up to an order of magnitude  
  > "lead to an uncertainty of a factor of a few in flux (cite: woitke18)" (4.2)
- Caveat (inferred, ours): Small DALI grid with fixed disk structure; Rc-UV degeneracy
- Caveat (inferred, ours): Ratio 1.6 for scaling N=2-1 to N=3-2 is uncertain and drives the Taurus comparison
- Caveat (inferred, ours): Only two resolved disks; ring result at low S/N
- Caveat (inferred, ours): Hyperfine blending affects the ring profiles

## Reproducibility

- Data public (paper): ALMA data cited with project IDs  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2013.1.00220.S and ADS/JAO.ALMA#2015.1.00222.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: DALI model input files
- Missing: Full CASA imaging parameters
- Missing: Table of fluxes not fully legible in text
- Data volume (inferred): ~100-300 GB raw for 93 short scheduling blocks over three projects
- Score (inferred): 3/5, Public data and clear survey approach but DALI setup and many imaging parameters unstated.
- Rediscovery candidate: no, Key results rely on DALI modeling with unreleased setup and incomplete imaging details.

## Links

- Method: (cite: ansdell16); (cite: ansdell18) (Survey observations and flux measurements)
- Method: (cite: cazzoletti18) (DALI CN model grid)
- Method: (cite: loomis18) (Keplerian masking)
- Companion: (cite: svt18) (V1094 Sco ring structure)
- Companion: (cite: tazzari17) (Smooth disk model fits of Sz 71 and Sz 98)
- Related: ALMA Lupus disk survey
- Related: Lupus Completion Survey

## Checks

```json
{
 "quotes": 81,
 "quotes_ok": 81,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 3,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 100,
  "stated": 61,
  "rate": 0.61
 },
 "evidence_ok": true
}
```
