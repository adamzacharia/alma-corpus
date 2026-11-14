# Primordial rotating disk composed of at least 15 dense star-forming clumps at cosmic dawn

`2025NatAs...9.1553F` | Nature Astronomy 2025 | first author: Fujimoto, S. | arXiv: 2402.18543 | DOI: 10.1038/s41550-025-02592-w

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies
- Question: How do the internal clumpy substructure and the underlying gas dynamics of a lensed young galaxy at z=6.072 relate, and how does this compare with simulations?  
  > "Our findings have unveiled the connection between the host galaxy’s internal small substructures and the underlying dynamics along with feedback effects for the first time at cosmic dawn" (abstract)
- Target **the Cosmic Grapes (z6_3) in RXCJ0600-2007**: coordinates RA 06:00:09.5647, Dec -20:08:10.993 (J2000)  
  > "R.A. | 06:00:09.5647" (Extended Data Table 3); "two bright emission lines were identified at the same frequency of $\sim$268.7 GHz" (1. Target – A quintuply lensed galaxy the Cosmic Grapes at z=6.072); z/distance z = 6.072  
  > "R.A. | 06:00:09.5647" (Extended Data Table 3); "two bright emission lines were identified at the same frequency of $\sim$268.7 GHz" (1. Target – A quintuply lensed galaxy the Cosmic Grapes at z=6.072); distance from [C II] line redshift (Fujimoto et al. 2021)  
  > "R.A. | 06:00:09.5647" (Extended Data Table 3); "two bright emission lines were identified at the same frequency of $\sim$268.7 GHz" (1. Target – A quintuply lensed galaxy the Cosmic Grapes at z=6.072)

## Data provenance

- ALMA projects: 2021.1.00055.S, 2018.1.00035.L, 2021.1.00247.S, 2021.1.00181.S, 2022.1.00195.S
- bands: Band 6, [C II] 158 um  
  > "Follow-up ALMA Band 6 observations were carried out on the five multiple images in RXCJ0600-2007" (3. ALMA Observations)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: C43-2 and C43-5  
  > "The configurations of C43-2 and C43-5 were used" (3. ALMA Observations)
- baselines: _not stated_
- angular resolution: 0.28x0.25 arcsec beam (deep data); 0.80x0.65 arcsec (z6_4, z6_5)  
  > "The generated cubes achieved full-width-half-maximum (FWHM) sizes of the synthesized beam of" (3. ALMA Observations)
- max recoverable scale: _not stated_
- sensitivity: 0.17 mJy/beam per 20 km/s channel (deep); 0.18 mJy/beam per 60 km/s (z6_4, z6_5); continuum 12 uJy/beam  
  > "with $1\sigma$ line sensitivities in a 20-km s$^{-1}$ (60-km s$^{-1}$) width channel of 0.17 mJy beam$^{-1}$ (0.18 mJy beam$^{-1}$)" (3. ALMA Observations)
- time on source: 49.4 min (C43-2) and 107.8 min (C43-5) for z6_1,2 and Cosmic Grapes; 12.6 min each for z6_4 and z6_5  
  > "with the on-source integration times of 49.4 mins and 107.8 mins, respectively" (3. ALMA Observations); "The C43-2 configuration was used, with the on-source integration time of 12.6 mins for each." (3. ALMA Observations)
- observing dates: January to August 2022  
  > "from January to August 2022 as a part of Cycle 8 program" (3. ALMA Observations)
- pi or archival as stated: _not stated_
- Line: [C II] 158 um (not stated)
- Other facility **JWST NIRCam**: 1-5 um imaging resolving clumps  
  > "The NIRCam images were taken in five bands: F115W, F150W, F277W, F356W, and F444W" (2. NIRCam Observations)
- Other facility **JWST NIRSpec IFU**: H-alpha and [O III] kinematics, line fluxes  
  > "We used the grating/filter setup G395H/F290LP" (3. NIRSpec IFU Observations)
- Other facility **VLT/MUSE, Keck/DEIMOS, Gemini/GMOS**: spectroscopy for lens model  
  > "a new 8.9 hour MUSE observation was obtained" (4. Lens model)
- External data: [C II]-to-gas mass conversion alpha=31 Msun/Lsun  
  > "using a conversion factor of $\alpha_{\rm [CII]}=31\,M_{\odot}/L_{\odot}$ calibrated with star-forming galaxies at $z\sim2$" (10. Toomre Q parameter) [from Zanella et al. 2018 (cite: zanella2018)]
- External data: Dust mass 1.2e6 Msun from FIR SED  
  > "the dust mass is also estimated to be $M_{\rm dust}=1.2^{+1.2}_{-0.7}\times10^{6}\,M_{\odot}$" (10. Toomre Q parameter) [from (cite: valentino2024)]
- External data: Lower-z clump luminosity functions of lensed galaxies  
  > "we also show measurements for similarly lensed galaxies at $z\sim1$–3 using the H$\alpha$ line in the literature" (12. Clump Luminosity Function) [from (cite: livermore2015)]
- External data: Local S values for comparison  
  > "late-type spirals and irregulars, the best local analog of our target, still show the average $S$ value of $S=0.35\pm0.10$ in the rest-frame UV" (11. Clumpiness parameter $S$) [from (cite: mager2018)]
- Simulation/model as data: SERRA (140 galaxies), FIRE-2 (13), TNG50 (12) galaxies at z=6-8 used for S and clump LF comparison  
  > "We select a total of 140 SERRA galaxies at $z=6$–8 for our comparison" (13. Cosmological zoom-in simulations)

## Processing

### Calibration

- pipeline or manual: CASA pipeline script, standard manner  
  > "using the pipeline script in the standard manner" (3. ALMA Observations)
- casa version: CASA 6.4.1.12  
  > "Common Astronomy Software Applications package CASA version 6.4.1.12" (3. ALMA Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: tclean, automask, down to 2 sigma, max 100,000 iterations  
  > "applied the `tclean` routines down to the 2$\sigma$ level with a maximum iteration number of 100,000 in the automask mode" (3. ALMA Observations)
- deconvolver: _not stated_
- weighting robust: Briggs robust 0.5 (arc, Cosmic Grapes); natural for z6_4, z6_5  
  > "we adopt Briggs weighting with a robust parameter of $0.5$" (3. ALMA Observations); "we adopt natural weighting to maximize the sensitivity for a detection experiment" (3. ALMA Observations)
- uv taper: _not stated_
- cell size: 0.05 arcsec  
  > "We imaged the calibrated visibilities with a pixel scale of" (3. ALMA Observations)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: power-law fit to visibilities with line channels masked  
  > "The continuum subtraction was applied to the visibility by performing a power-law fit with the line-detected channels masked." (3. ALMA Observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: channel width 20 km/s (deep), 60 km/s (z6_4, z6_5)  
  > "common spectral channel bin of 20 km s$^{-1}$ for the deep data" (3. ALMA Observations)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Pixel-by-pixel SED fitting method  
  > "We basically follow the pixel-by-pixel method presented in Giménez-Arteaga et al. (2023)" (5. SED analysis) [from (cite: clara2023); details in (cite: clara2024)]
- NIRSpec IFU reduction procedure  
  > "following the procedure developed by the ERS TEMPLATES team" (3. NIRSpec IFU Observations) [from Rigby et al. (cite: rigby2023)]
- Updated lens model construction  
  > "The details of the new MUSE, DEIMOS, and GMOS data and the construction of the updated lens model are presented in separate papers" (4. Lens model) [from (cite: furtak2024)]
- Source-plane reconstruction uses previous GLAFIC model  
  > "we use the previous model constructed with `GLAFIC`(cite: fujimoto2021) for the source-plane reconstruction analysis" (4. Lens model) [from (cite: fujimoto2021)]
- Clumpiness S definition  
  > "is the background pixel values in an area of the sky which is equal to the galaxy’s area(cite: conselice2003)" (11. Clumpiness parameter $S$) [from (cite: conselice2003)]

### Not stated but needed to reproduce (our reading)

- Line-free channels and frequency range used for continuum fit
- Source-plane reconstruction algorithm details and resulting cube pixel scale
- 3DBarolo parameter file settings (ring widths, normalization details, masking thresholds)
- Calibrators and flux-scale uncertainty for ALMA data
- Exact SExtractor/GALFIT convergence setup and PSF used for GALFIT
- How [C II] luminosity per pixel was derived from source-plane cubes
- Details of simulated galaxy selection and noise injection levels

## Analysis recipe

1. **Reduce and image ALMA [C II] cubes**: CASA pipeline calibration, tclean imaging, power-law continuum subtraction  
  > "using the pipeline script in the standard manner" (3. ALMA Observations)
   - software: CASA
   - parameter: robust 0.5, 20 km/s channels, 0.05" pixels  
  > "Briggs weighting with a robust parameter of $0.5$" (3. ALMA Observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **Fit 3D tilted-ring kinematics**: 3DBarolo on source-plane cubes of [C II], Halpha, [O III]; inclination from F150W axis ratio  
  > "we obtain the axis ratio of $q\simeq0.53$ and calculate $i=\arccos(q)\simeq57.9$ deg" (9. Kinematic modeling)
   - software: 3DBarolo
   - parameter: free: V, sigma, PA, inclination; ring width (0.5-1.0) x PSF FWHM; AZIM normalization  
  > "We use $V$, $\sigma$, PA, and inclination as free parameters." (9. Kinematic modeling)
   - assumption: circular rotation  
  > "under the assumption of circular rotation" (9. Kinematic modeling)
   - fitting: 3DBarolo tilted-ring fit  
  > "A 3D tilted-ring model is employed in `3DBarolo`, allowing us to derive rotation curves and gas dynamics in a non-parametric fashion, under the assumption of circular rotation." (9. Kinematic modeling)
   - validation: Monte Carlo mock cubes show Vmax/sigma0 overestimated by 4±2%; PVsplit classification indicates single disk  
  > "the $V_{\rm max}/\sigma_{0}$ value could be overestimated by $4\pm2\%$ for our observation setup" (9. Kinematic modeling)
3. **Derive gas mass and Toomre Q**: [C II] luminosity to Mgas with alpha=31; Q=kappa sigma/(pi G Sigma_gas) radial profile from 3DBarolo plus pixel-by-pixel 2D map  
  > "First, we derived the radial profile of the Toomre $Q$ parameter by employing non-parametric radial profiles of the best-fit $V(R)$ and $\sigma(R)$" (10. Toomre Q parameter)
   - software: 3DBarolo
   - parameter: alpha_[CII]=31 Msun/Lsun  
  > "conversion factor of $\alpha_{\rm [CII]}=31\,M_{\odot}/L_{\odot}$" (10. Toomre Q parameter)
   - assumption: Dark matter negligible in dynamical mass; gas-to-dust ~1e3 for cross-check  
  > "assuming that the dark matter contribution is negligible" (10. Toomre Q parameter)
   - fitting: _not stated_
   - validation: Mgas consistent with Mdyn-Mstar and dust-based estimates; factor-2 uncertainty acknowledged  
  > "This is in excellent agreement with the $M_{\rm gas}$ estimate of $1.1^{+0.4}_{-0.1}\times10^{9}\,M_{\odot}$" (10. Toomre Q parameter)
4. **Identify clumps and measure sizes in NIRCam F150W**: SExtractor detection then simultaneous 16-component GALFIT Sersic fit  
  > "All 16 components are then fitted simultaneously within this adjusted region." (7. Properties of the individual star-forming clumps)
   - software: SExtractor, GALFIT
   - parameter: DETECT_MINAREA=9, DETECT_THRESH=2.0, DEBLEND_NTHRESH=64, DEBLEND_MINCONT=0.0001; Sersic n=1  
  > "except for DETECT_MINAREA = 9, DETECT_THRESH = 2.0, DEBLEND_NTHRESH = 64, and DEBLEND_MINCONT = 0.0001" (7. Properties of the individual star-forming clumps)
   - fitting: GALFIT simultaneous fit with bounded parameters  
  > "All 16 components are then fitted simultaneously within this adjusted region." (7. Properties of the individual star-forming clumps inside the Cosmic Grapes)
   - validation: n=2 for all components gives sizes within ~50%  
  > "the resulting output sizes are consistent with our original results with the $n=1$ assumption within $\sim50\%$" (7. Properties of the individual star-forming clumps)
5. **Quantify clumpiness (S and clump LF) and compare with simulations**: Compute S with sigma=0.2" in r=0.7" circle on F150W; cumulative clump LF vs SFR; same procedure on mock-observed SERRA, FIRE, TNG50 cutouts  
  > "we measure the $S$ parameter and the clump LF in the same manner as the procedures done for the observed map" (13. Cosmological zoom-in simulations)
   - fitting: _not stated_
   - validation: Differential-magnification PSF effects change simulated S and LF by no more than 5%  
  > "alter the $S$ parameter and clump LF measurements for the simulated galaxies no more than $5\%$" (13. Cosmological zoom-in simulations)

## Software

- **CASA** 6.4.1.12: ALMA calibration and imaging  
  > "The ALMA data were reduced using the CASA software version 6.4.1.12" (Code availability.)
- **3DBarolo** : 3D tilted-ring kinematic modeling  
  > "using the 3D-based analysis tool `3DBarolo`" (9. Kinematic modeling)
- **GALFIT** : Sersic fits of clumps  
  > "using the `GALFIT` software" (7. Properties of the individual star-forming clumps)
- **SExtractor** 2.25.0: clump detection  
  > "We use `SExtractor` version 2.25.0" (7. Properties of the individual star-forming clumps)
- **grizli** : NIRCam reduction  
  > "processed with the `grizli` pipeline" (2. NIRCam Observations)
- **BAGPIPES** : pixel-by-pixel SED fitting  
  > "We ran the SED fitting code of BAGPIPES" (5. SED analysis)
- **PyNeb** : electron density and temperature  
  > "using the nebular emission code of `PyNeb`" (6. Global-scale galaxy properties)
- **JWST pipeline** 1.12.5: NIRSpec IFU reduction  
  > "using the STScI pipeline (version 1.12.5)" (3. NIRSpec IFU Observations)
- **NSClean** : NIRSpec noise cleaning  
  > "we also applied the `NSClean` package" (3. NIRSpec IFU Observations)
- **WebbPSF** : PSF matching  
  > "using the PSF models generated with `WebbPSF`" (5. SED analysis)
- **GLAFIC** : source-plane reconstruction  
  > "we use the previous model constructed with `GLAFIC`" (4. Lens model)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Vmax/sigma0 ([C II]) | 3.58 | 0.74 | dimensionless | 2 | 3.58 $\pm$ 0.74 |
| Toomre Q (radially averaged) | 0.2-0.3 | not stated | dimensionless | 3 | Toomre $Q$ parameter in a range of $\simeq$ 0.2–0.3 |
| Gas mass from [C II] | 1.1e9 | +0.4/-0.1 | Msun | 3 | $1.1^{+0.4}_{-0.1}\times10^{9}$ |
| Dynamical mass within 2 re | 1.7e9 | +0.7/-0.8 | Msun | 3 | $M_{\rm dyn}=1.7^{+0.7}_{-0.8}\times10^{9}\,M_{\odot}$ |
| Clumpiness S | 0.81 | 0.02 | dimensionless | 5 | We obtain $S=0.81\pm0.02$ |
| Clump flux fraction in F150W | 69.9 | not stated | percent | 4 | the sum of the fluxes from the 15 clumps accounts for 69.9% of the total flux |
| Inclination | 57.9 | not stated | deg | 2 | $i=\arccos(q)\simeq57.9$ deg |
| Magnification | 32.5 | +0.7/-6.8 | dimensionless | 0 | 32.5$_{-6.8}^{+0.7}$ |

## Qualitative findings

- Symmetric PV diagram indicates a rotation-supported disk, not a merger  
  > "The PV diagram shows a symmetric distribution with the two peaks, providing strong evidence that the *Cosmic Grapes* is a rotation-supported system" (9. Kinematic modeling)
- Dust continuum peaks coincide with bright clumps; clumpy morphology not due to dust obscuration  
  > "We, therefore, conclude that the remarkably clumpy morphology of the *Cosmic Grapes* is not driven by dust reddening." (8. Dust reddening in the Cosmic Grapes)

## Claim tuples

- H: The galaxy contains numerous star-forming clumps that are real | E: SExtractor and GALFIT on NIRCam F150W with lens correction | R: 15 clumps with re~10-60 pc, 70% of F150W flux | F: Highly clumpy young galaxy at z=6 | **supported**
- H: The clumpy galaxy is a dynamically cold rotating disk | E: 3DBarolo on [C II], Halpha, [O III] cubes | R: Vmax/sigma0=3.58±0.74 | F: Rotation-supported disk | **supported**
- H: Clumps form through disk instability | E: Toomre Q from [C II] | R: Q~0.2-0.3 | F: Gravitationally unstable disk | **supported**
- H: Current simulations reproduce the observed clumpiness with a rotating disk | E: Compare S and clump LF with SERRA, FIRE, TNG50 | R: All simulations show lower S and clump LF | F: Simulations underpredict clumpiness | **refuted**

## Reasoning

- Why this data: Deep high-resolution [C II] follow-up to probe internal structure and kinematics  
  > "these follow-up observations aimed to perform deep, high-resolution \[C ii\] line spectroscopy to probe the internal structures and kinematics" (3. ALMA Observations)
- Why this method: _not stated_
- Alternative: Alternative alpha_[CII]~15-18 would lower Mgas by a factor ~2; fiducial 31 retained  
  > "using $\alpha_{\rm [CII]}=31\,M_{\odot}/L_{\odot}$ could result in overestimating $M_{\rm gas}$ by a factor of $\sim$2" (10. Toomre Q parameter)
- How they decided it was enough: _not stated_
- Limitation (authors): Magnification systematic uncertainty up to ~25%  
  > "we conclude that the magnification uncertainty in this study does not exceed $\sim$25%" (4. Lens model)
- Limitation (authors): Clump number may increase with better data; ALMA beam larger than clumps so gas mass only for 7 clumps  
  > "while this number could be increased with further high-resolution observations in the future" (7. Properties of the individual star-forming clumps)
- Caveat (inferred, ours): Clump selection (15 of 20 by visual inspection) is subjective
- Caveat (inferred, ours): Source-plane reconstruction of ALMA cubes at 0.28" beam may blur clumps
- Caveat (inferred, ours): Q depends on uncertain alpha_[CII] and assumed thin/thick disk
- Caveat (inferred, ours): Simulation comparison uses hand-picked selection (e.g., visual rotation checks)

## Reproducibility

- Data public (paper): ALMA 2021.1.00055.S and JWST GO-1567 public; other data on request  
  > "The ALMA data supporting our finding is from #2021.1.00055.S, available at <http://almascience.nao.ac.jp/>." (Data availability.)
- Products in archive: _not stated_
- Code: No custom code released; public tools linked (grizli, CASA, 3DBarolo, TEMPLATES notebook)  
  > "The [C ii], H$\alpha$, and [O iii]$\lambda$5008 data cubes are analyzed with `3DBarolo` available at" (Code availability.)
- Missing: Lens model and source-plane reconstruction (lens model in separate paper)
- Missing: 3DBarolo configuration
- Missing: Line-free channels
- Missing: Pixel-by-pixel SED outputs from companion paper
- Data volume (inferred): ~50-200 GB for ALMA MS plus JWST products
- Score (inferred): 3/5, Public data and many parameters given, but the lens model, source-plane reconstruction and 3DBarolo setup are in other papers or not detailed.
- Rediscovery candidate: no, Key results depend on unreleased lens model and source-plane reconstruction.

## Links

- Method: Giménez-Arteaga et al. 2023/2024 (cite: clara2023; clara2024) (Pixel-by-pixel SED method)
- Method: Rigby et al. 2023 (cite: rigby2023) (NIRSpec IFU reduction)
- Method: Di Teodoro & Fraternali 2015 (cite: diteodoro2015) (3DBarolo)
- Companion: Fujimoto et al. 2021 (cite: fujimoto2021) (Original [C II] discovery and lens model)
- Companion: Furtak et al. 2024 (cite: furtak2024) (Updated lens model)
- Companion: Valentino et al. 2024 (cite: valentino2024) (Dust and FIR SED)
- Related: ALMA Lensing Cluster Survey (ALCS)
- Related: JWST GO 1567
- Related: RELICS

## Checks

```json
{
 "quotes": 90,
 "quotes_ok": 90,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 5,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [
  "2018.1.00035.L",
  "2021.1.00247.S",
  "2021.1.00181.S",
  "2022.1.00195.S"
 ],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 94,
  "stated": 66,
  "rate": 0.702
 },
 "evidence_ok": true
}
```
