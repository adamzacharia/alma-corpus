# A Galaxy-scale Fountain of Cold Molecular Gas Pumped by a Black Hole

`2018ApJ...865...13T` | The Astrophysical Journal 2018 | first author: Tremblay, G. R. | arXiv: 1808.00473 | DOI: 10.3847/1538-4357/aad6dd

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: galaxy_clusters_and_sz, nearby_galaxies, agn_and_quasars
- Question: Are the warm ionized and cold molecular gas in the Abell 2597 BCG cospatial and comoving, and does their kinematics reflect inflow, jet-driven outflow and bubble uplift (a galaxy-scale fountain) as predicted by chaotic cold accretion/precipitation models?  
  > "the threshold criterion predicts that the kinematics of the hot, warm, and cold phases of the ISM should retain memory of their shared journey along what is ultimately the same thermodynamic pathway" (Introduction)
- Target **Abell 2597 BCG (PKS 2322-123)**: coordinates RA 23h25m19.7s, Dec -12d07m27s (J2000)  
  > "Abell 2597 is a cool core cluster of galaxies at redshift $z=0.0821$" (Introduction); "1$''$ corresponds to 1.549 kpc at the redshift of the A2597 BCG ($z=0.0821$), where the associated luminosity and angular size distances are 374.0 and 319.4 Mpc, respectively" (Introduction); z/distance z=0.0821; D_L=374.0 Mpc; D_A=319.4 Mpc  
  > "Abell 2597 is a cool core cluster of galaxies at redshift $z=0.0821$" (Introduction); "1$''$ corresponds to 1.549 kpc at the redshift of the A2597 BCG ($z=0.0821$), where the associated luminosity and angular size distances are 374.0 and 319.4 Mpc, respectively" (Introduction); distance from redshift with H0=70, OmegaM=0.27, OmegaLambda=0.73  
  > "Abell 2597 is a cool core cluster of galaxies at redshift $z=0.0821$" (Introduction); "1$''$ corresponds to 1.549 kpc at the redshift of the A2597 BCG ($z=0.0821$), where the associated luminosity and angular size distances are 374.0 and 319.4 Mpc, respectively" (Introduction)

## Data provenance

- ALMA projects: 2012.1.00988.S
- bands: Band 6 / 213 GHz  
  > "CO(2-1) & ALMA & Band 6 / 213 GHz & 3 hrs & 2012.1.00988.S" (Table 1)
- frequencies and spectral setup: CO(2-1) baseband at 213.04685 GHz; three other basebands at 215.0, 227.7, 229.7 GHz; FDM, 0.488 MHz channels, 1875 MHz per baseband  
  > "The other three basebands sampled the local rest-frame $\sim230$ GHz continuum at 215.0, 227.7, and 229.7 GHz" (2.1 ALMA CO(2-1) Observations); "delivering a native spectral (velocity) resolution of 0.488 MHz ($\sim1.3$ km s) across an 1875 MHz bandwidth per baseband" (2.1 ALMA CO(2-1) Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 17-1284 m, 29 12 m antennas  
  > "Baselines between the array’s 29 operational 12 m antenna spanned $17-1284$ m" (2.1 ALMA CO(2-1) Observations)
- angular resolution: 0.715" x 0.533" beam at PA 74 deg (natural); tapered 0.944" x 0.764"  
  > "with a $0.715\ensuremath{''}\times0.533\ensuremath{''}$ synthesized beam at P.A. = $74^\circ$" (2.1 ALMA CO(2-1) Observations)
- max recoverable scale: no extended emission resolved out versus IRAM 30m  
  > "we find no evidence that any extended emission has been “resolved out” by the interferometer." (2.1 ALMA CO(2-1) Observations)
- sensitivity: 0.16 mJy/beam per 40 km/s channel  
  > "The final data cube reaches an RMS sensitivity and angular resolution of $0.16$ mJy beam$^{-1}$ per 40 km s channel" (2.1 ALMA CO(2-1) Observations)
- time on source: three hours across three scheduling blocks  
  > "ALMA observed the Abell 2597 BCG for three hours across three scheduling blocks" (2.1 ALMA CO(2-1) Observations)
- observing dates: 17-19 November 2013  
  > "executed between 17-19 November 2013" (2.1 ALMA CO(2-1) Observations)
- pi or archival as stated: _not stated_
- Line: 12CO J=2-1 (230.538001 GHz)
- Other facility **VLT/MUSE**: Optical IFU cube for warm ionized gas kinematics (Halpha etc.), ESO programme 094.A-0859(A)  
  > "Obtained as part of ESO programme 094.A-0859(A) (PI: Hamer)" (2.2 MUSE Optical Integral Field Spectroscopy)
- Other facility **Chandra ACIS-S**: Deep 626 ks X-ray image of cavities  
  > "spanning 626.37 ksec in total integration time across fourteen separate ACIS-S observations" (2.5 Deep Chandra X-ray data)
- Other facility **HST ACS/SBC**: FUV continuum map compared to CO  
  > "We have smoothed the *HST*/ACS SBC FUV continuum map from (cite: oonk11) with a Gaussian" (3.2 Morphology of the cold molecular nebula)
- External data: CO(2-1)/CO(1-0) flux density ratio of 3.2  
  > "Assuming a CO(2-1) to CO(1-0) flux density ratio of 3.2 (cite: braine92)" (3.3 Total mass) [from (cite: braine92)]
- External data: Milky Way X_CO = 2e20 cm^-2 (K km/s)^-1  
  > "we adopt the average value for the disk of the Milky Way of $X_{\mathrm{CO}} = X_{\mathrm{CO,~MW}} = 2 \times 10^{20}$" (3.3 Total mass) [from (cite: bolatto13b)]
- External data: X-ray cavity gas densities/sizes, 4pV energy ~4e58 erg, cavity age ~2e8 yr  
  > "the cavity system has an estimated $4pV$ mechanical energy of $\sim4\times10^{58}$ ergs (cite: tremblay12b)" (4.2 The Fountain’s “Plume”) [from (cite: tremblay12b)]
- External data: Systemic velocity cz = 24,613 +/- 29 km/s  
  > "$z=0.0821 \pm 0.0001$ ($cz = 24,613 \pm 29$ km s)" (2.4 Adoption of a systemic velocity) [from (cite: tremblay16)]

## Processing

### Calibration

- pipeline or manual: Raw visibilities imported, flagged and reduced into calibrated measurement sets with CASA  
  > "Raw visibilities were imported, flagged, and reduced into calibrated measurement sets using `CASA` version 4.2" (2.1 ALMA CO(2-1) Observations)
- casa version: CASA 4.2  
  > "using `CASA` version 4.2" (2.1 ALMA CO(2-1) Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Neptune; phase calibrators J2258-2758 and J2331-1556  
  > "Observations of A2597 were bracketed by slews to Neptune as well as the quasars J2258-2758 and J2331-1556" (2.1 ALMA CO(2-1) Observations)
- flux scale uncertainty: _not stated_
- self calibration: iterative phase-only self-cal on galaxy continuum; 14% RMS improvement  
  > "we iteratively performed phase-only self-calibration using the galaxy’s own continuum, yielding a $14\%$ improvement in RMS noise." (2.1 ALMA CO(2-1) Observations)

### Imaging

- task: CLEAN  
  > "using the `CLEAN` algorithm with `natural` weighting" (2.1 ALMA CO(2-1) Observations)
- deconvolver: _not stated_
- weighting robust: natural; Briggs robust -2 to 2 tried, results similar  
  > "including `Briggs` with a `robust` parameter that ranged from -2.0 (roughly `uniform`) to 2.0 (close to `natural`)" (Footnote 3)
- uv taper: Gaussian taper for some images, beam 0.944x0.764 arcsec PA 86  
  > "some ALMA images presented in this paper use Gaussian-weighted $uv$ tapering of the outer baselines" (2.1 ALMA CO(2-1) Observations)
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: UVCONTSUB uv-plane fit  
  > "We used the `UVCONTSUB` task to fit and subtract the continuum from the CO(2-1) spectral window in the $uv$ plane." (2.1 ALMA CO(2-1) Observations)
- line free channels: _not stated_
- primary beam correction: pbcor = True  
  > "corrected for response of the primary beam (`pbcor = True`)" (2.1 ALMA CO(2-1) Observations)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.715" x 0.533" at PA 74 deg  
  > "$0.715\ensuremath{''}\times0.533\ensuremath{''}$ synthesized beam at P.A. = $74^\circ$" (2.1 ALMA CO(2-1) Observations)
- final rms: 0.16 mJy/beam per 40 km/s  
  > "RMS sensitivity and angular resolution of $0.16$ mJy beam$^{-1}$ per 40 km s channel" (2.1 ALMA CO(2-1) Observations)

### Inherited from earlier work

- Masked-moment technique for velocity and dispersion maps  
  > "made from the ALMA data using the “masked moment” technique described by (cite: dame11) and implemented by Timothy Davis" (2.1 ALMA CO(2-1) Observations) [from (cite: dame11)]
- Systemic velocity adopted from earlier paper  
  > "As discussed in the Methods section of (cite: tremblay16), this velocity is consistent with Ca II H+K and G-band absorption features" (2.4 Adoption of a systemic velocity) [from (cite: tremblay16)]
- Absorption-feature analysis of infalling clouds  
  > "we found three deep, narrow continuum absorption features ([4](#fig:nature)), which we discuss in (cite: tremblay16)" (3.1 “Shadows” cast by inflowing cold clouds) [from (cite: tremblay16)]
- H2 mass relation  
  > "following the relation reviewed by (cite: bolatto13b)" (3.3 Total mass) [from (cite: bolatto13b)]

### Not stated but needed to reproduce (our reading)

- CLEAN cell size, image size, niter/threshold, and masking
- Line-free channels used for UVCONTSUB and fit order
- Self-calibration solution intervals and number of iterations
- Spectral resampling/regridding details for velocity frame
- Exact smoothing kernel widths in the masked-moment code beyond FWHM=beam
- Polygon aperture definitions for spectra
- Flux scale uncertainty
- Pipeline vs manual calibration scripts

## Analysis recipe

1. **Calibrate and image CO(2-1) and continuum**: CASA calibration, phase-only self-cal, UVCONTSUB, natural-weighted CLEAN; optional uv taper; continuum from three line-free basebands  
  > "We then deconvolved and imaged the continuum-free CO(2-1) measurement set using the `CLEAN` algorithm with `natural` weighting" (2.1 ALMA CO(2-1) Observations)
   - software: CASA
   - parameter: natural weighting; 40 km/s channels (binned to 5, 10, 40 km/s as needed)  
  > "binned the data (in the $uv$ plane) to 5, 10, or 40 km s channels" (2.1 ALMA CO(2-1) Observations)
   - fitting: _not stated_
   - validation: Compared total flux with IRAM 30m; no resolved-out emission  
  > "In comparing the total recovered ALMA CO(2-1) flux with an older single-dish IRAM 30m observation" (2.1 ALMA CO(2-1) Observations)
2. **Make moment maps and two-Gaussian maps**: Masked moments: smooth cube spatially (beam FWHM) and spectrally, mask at 1.5 sigma, compute moments on unsmoothed cube; two-Gaussian fits along lines of sight  
  > "enabling creation of a three dimensional mask that selects all pixels above a 1.5$\sigma$ flux threshold." (2.1 ALMA CO(2-1) Observations)
   - software: makeplots (T. Davis), Python
   - parameter: 1.5 sigma mask threshold  
  > "selects all pixels above a 1.5$\sigma$ flux threshold" (2.1 ALMA CO(2-1) Observations)
   - fitting: Multi-Gaussian chi^2 minimization, adding Gaussians as needed  
  > "These fits iteratively fit (and, if necessary, add) Gaussians to the extracted spectra using a simple $\chi^2$ minimization technique." (3.4.2 Cold gas motions induced by the radio jet)
   - validation: _not stated_
3. **Derive molecular gas mass**: Fit single Gaussian to spectrum from polygon aperture of >=3 sigma emission (10 km/s channels), convert to M_H2 with Bolatto relation  
  > "We fit a single Gaussian to the CO(2-1) spectrum extracted from a polygonal aperture encompassing all $\ge3\sigma$ emission" (3.3 Total mass)
   - software: PySpecKit
   - parameter: fit range -600 to +600 km/s; CO(2-1)/CO(1-0)=3.2  
  > "while ours is fit between $-600$ and $+600$ km s" (3.3 Total mass)
   - assumption: X_CO = 2e20 (Milky Way), D_L = 374 Mpc  
  > "we adopt the average value for the disk of the Milky Way of $X_{\mathrm{CO}} = X_{\mathrm{CO,~MW}} = 2 \times 10^{20}$" (3.3 Total mass)
   - fitting: Gaussian fit; same integral with 20/40 km/s binning and direct summation  
  > "Within errors, we obtain the same integral for cubes binned to 20 or 40 km s" (3.3 Total mass)
   - validation: Consistency across binning and analytic integral  
  > "Within errors, we obtain the same integral for cubes binned to 20 or 40 km s, and an identical flux with an analytic integral of the line" (3.3 Total mass and mass distribution of the molecular gas)
4. **Compare MUSE Halpha and ALMA CO**: MUSE reduced with pipeline, PYPARADISE line fits; WCS shifts to align; reproject ALMA onto MUSE grid; compare velocity and dispersion  
  > "We then resampled the ALMA data onto the MUSE maps’ pixel grids in Python using `reproject`" (2.3 ALMA and MUSE Line Ratio Maps)
   - software: MUSE pipeline, PyParadise, reproject, PyRAF
   - assumption: CO and Halpha photocentroids and NW blob aligned  
  > "assuming that the CO(2-1) and H$\alpha$ photocentroids in the galaxy center as well as a bright, clearly detected ($\gae10\sigma$) “blob” of emission to the northwest in both datasets should be aligned" (2.3 ALMA and MUSE Line Ratio Maps)
   - fitting: _not stated_
   - validation: Beam matched MUSE PSF so no smoothing; alignment uncertainty smaller than PSF  
  > "we are confident that the alignment is “correct”, at least to an uncertainty that is smaller than the PSF of either observation." (2.3 ALMA and MUSE Line Ratio Maps)
5. **Energetics and uplift budget**: Compare cold gas mass and kinetic energy with displaced hot gas mass and 4pV cavity energy; freefall velocity estimates  
  > "the total kinetic energy in the cold molecular nebula (e.g., $\frac{1}{2} M_\mathrm{mol} v^2$) is about an order of magnitude lower" (4.2 The Fountain’s “Plume”)
   - assumption: spherical cavity geometry; M~1e12 Msun, scale radius ~20 kpc  
  > "assuming spherical cavity geometry" (4.2 The Fountain’s “Plume”)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.2: calibration, uvcontsub, CLEAN imaging  
  > "using `CASA` version 4.2" (2.1 ALMA CO(2-1) Observations)
- **PYPARADISE** : stellar and nebular fitting of MUSE cube  
  > "decoupling and modeling the stellar and nebular components of the galaxy with PYPARADISE" (2.2 MUSE Optical Integral Field Spectroscopy)
- **MUSE pipeline** 1.6.4: MUSE data reduction  
  > "using version 1.6.4 of the standard MUSE pipeline" (2.2 MUSE Optical Integral Field Spectroscopy)
- **CIAO** 4.9: Chandra reduction  
  > "using CIAO version 4.9" (2.5 Deep Chandra X-ray data)
- **reproject** : resampling ALMA onto MUSE grid  
  > "using `reproject`, an `Astropy` affiliated package" (2.3 ALMA and MUSE Line Ratio Maps)
- **PySpecKit** : spectral fitting (listed in software)  
  > "`PySpecKit` (cite: pyspeckit)" (Software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| 230 GHz continuum point source flux at 221.3 GHz | 13.6 | 0.2 | mJy | 1 | The peak (and therefore total) flux measured from the continuum point source is $13.6 \pm 0.2$ mJy at 221.3 GHz |
| Radio-through-mm spectral index | 0.95 | 0.03 | dimensionless | 1 | a spectral index of $\alpha=0.95 \pm 0.03$ if $S \propto \nu^{-\alpha}$ |
| Integrated CO(2-1) flux | 7.8 | 0.3 | Jy km/s | 3 | $S_{\mathrm{CO}}\Delta v = 7.8\pm0.3$ Jy km s |
| CO(2-1) total FWHM | 252 | 16 | km/s | 3 | line FWHM of $252 \pm 16$ km s |
| Total H2 mass | 3.2e9 | 0.1e9 | Msun | 3 | $M_{\mathrm{H}_2}  = \left(3.2 \pm 0.1\right) \times 10^9$ |
| FWHM of broad southern-jet component | 342 | 8 | km/s | 2 | FWHM of $342\pm8$ km s($\sigma=145\pm3$ km s) |
| Gas mass in southern-jet region | 6.4e8 | 0.4e8 | Msun | 2 | molecular gas mass of $\left(6.4\pm 0.4\right) \times 10^8$ |
| Halpha deblended FWHM | 565 | 25 | km/s | 4 | the deblended H$\alpha$ FWHM is $565 \pm 25$ km s |
| Kinetic energy of molecular nebula | ~2e57 | not stated | erg | 5 | roughly $\sim2\times10^{57}$ ergs |

## Qualitative findings

- Halpha and CO(2-1) are cospatial and velocity centroids agree within ~45 km/s, but Halpha is 2-3x broader  
  > "The velocity difference map is largely smooth and below $\pm45$ km s" (3.6 MUSE and ALMA Comparison)
- Cold gas velocities are below circular speed and escape speed; filaments not in freefall  
  > "*Almost* everywhere, projected line of sight velocities are below the circular speed at any given radius, and well below the galaxy’s escape velocity." (3.4 Velocity structure)

## Claim tuples

- H: Warm ionized and cold molecular gas trace the same clouds | E: Compare MUSE Halpha and ALMA CO(2-1) maps and spectra | R: Cospatial, velocity centroids match within ~45 km/s; Halpha widths 2-3x larger | F: Cold gas is cospatial and comoving with warm gas | **supported**
- H: Cold gas jet/cavity coupling | E: Channel maps, multi-Gaussian fits near radio lobes, deep Chandra | R: Blueshifted sheet hugs lobes; broadest FWHM 342 km/s at jet deflection | F: Cold gas dynamically coupled to mechanical feedback | **partially**
- H: Cavities can uplift the cold gas | E: Compare gas mass and energy with cavity displaced mass and 4pV | R: 3.2e9 Msun vs >=7e9 Msun; 2e57 vs 4e58 erg | F: Uplift energetically feasible | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Natural weighting to improve sensitivity to filamentary outskirts  
  > "improving sensitivity to the filamentary outskirts of the nebula" (2.1 ALMA CO(2-1) Observations)
- Alternative: Free-fall of filaments rejected based on velocity structure  
  > "The southern filament’s velocity structure is inconsistent with gravitational free-fall" (3.4.1)
- How they decided it was enough: _not stated_
- Limitation (authors): X_CO uncertainty may overestimate mass by a factor of a few  
  > "we may be overestimating the total mass by a factor of a few" (3.3)
- Limitation (authors): Projection effects: motions in plane of sky unknown  
  > "unless most gas motions are contained in the plane of the sky" (3.4)
- Caveat (inferred, ours): Fountain interpretation is qualitative; no kinematic modeling distinguishing inflow/outflow/uplift in 3D
- Caveat (inferred, ours): Halpha-CO width mismatch explanation is speculative
- Caveat (inferred, ours): Mass uses Milky Way X_CO and an assumed 3.2 line ratio
- Caveat (inferred, ours): Uplift energetics ignore coupling efficiency

## Reproducibility

- Data public (paper): Code, ALMA/MUSE data products released in Zenodo repository; ALMA data from Cycle 1 program  
  > "along with all MUSE and ALMA data products, is included in this paper’s software repository" (2.3)
- Products in archive: _not stated_
- Code: Python codes/notebooks at Zenodo doi 10.5281/zenodo.1233825 and GitHub  
  > "All Python Codes / Jupyter Notebooks we have created to enable this analysis are publicly available in an online repository" (2 Observations & Data Reduction)
- Missing: CLEAN parameters (cell, size, niter, threshold, mask)
- Missing: Self-cal intervals
- Missing: Aperture polygon definitions
- Missing: Line-free channel selection
- Data volume (inferred): ~20-50 GB raw ALMA data (3 execution blocks, 4 basebands FDM)
- Score (inferred): 3/5, ALMA project code, code and data products released, and key numbers given, but imaging parameters and apertures omitted; interpretive paper.
- Rediscovery candidate: no, Main conclusions are qualitative/interpretive with several unstated imaging settings, although the mass and flux numbers are reproducible.

## Links

- Method: (cite: dame11) (masked moment technique)
- Method: (cite: bolatto13b) (CO-to-H2 mass relation)
- Companion: (cite: tremblay16) (Earlier Nature paper on the same ALMA data reporting absorbing infalling clouds)
- Related: Close AGN Reference Survey (CARS)
- Related: Chandra Cycle 18 Large Program 18800649

## Checks

```json
{
 "quotes": 83,
 "quotes_ok": 83,
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
  "facts": 87,
  "stated": 64,
  "rate": 0.736
 },
 "evidence_ok": true
}
```
