# Radiative Transfer Modeling of a Shadowed Protoplanetary Disk Assisted by a Neural Network

`2025ApJ...991..176W` | The Astrophysical Journal 2025 | first author: Williams, Jonathan P. | arXiv: 2509.01937 | DOI: 10.3847/1538-4357/adfa15

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: protoplanetary_disks
- Question: What causes the large shadow over the southern half of the V1098 Sco disk in SPHERE scattered light, and what is the geometry of the inner disk (misalignment of inner vs outer disk)?  
  > "We model the ALMA continuum and line data to determine the outer disk geometry and the central stellar mass." (abstract)
- Target **V1098 Sco (2MASS J16140792-1938292)**: coordinates _not stated_; z/distance 160 pc  
  > "V1098 Sco is of spectral type K1 and lies at a distance of 160 pc (cite: 2020yCat.1350....0G) in the Upper Sco region" (1 Introduction); distance from Gaia (cite: 2020yCat.1350....0G)  
  > "V1098 Sco is of spectral type K1 and lies at a distance of 160 pc (cite: 2020yCat.1350....0G) in the Upper Sco region" (1 Introduction)

## Data provenance

- ALMA projects: 2018.1.00564.S
- bands: Band 7 (340 GHz) continuum and CO 3-2  
  > "The final data products are Band 7 (340 GHz) continuum and CO 3–2 spectral line." (2.2 ALMA mm observations)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: continuum 0.41x0.32 arcsec PA -76 deg; line 0.38x0.31 arcsec PA -75 deg  
  > "The beam and rms noise levels are $0\hbox{$.\!\!^{''}$}41 \times 0\hbox{$.\!\!^{''}$}32$ at a position angle of $-76^\circ$" (2.2 ALMA mm observations)
- max recoverable scale: _not stated_
- sensitivity: 0.13 mJy/beam continuum; 5 mJy/beam per 0.5 km/s channel line  
  > "0.13 mJy beam$^{-1}$ for the continuum and" (2.2 ALMA mm observations)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: Archival data, downloaded from archive; cited to Carpenter et al. 2025  
  > "We downloaded ALMA observations of V1098 Sco from the archive (cite: 2025ApJ...978..117C)" (2.2 ALMA mm observations)
- Line: CO 3-2 (not stated)
- Other facility **VLT/SPHERE (IRDIS, DPI mode, H band)**: 1.6 micron polarized scattered-light image of the disk (DESTINYS program 1104.C-0415(D)), reduced with IRDAP  
  > "The data was reduced using the public IRDAP (IRDIS Data reduction for Accurate Polarimetry) pipeline" (2.1 SPHERE near-infrared observations)
- External data: Distance of 160 pc  
  > "lies at a distance of 160 pc (cite: 2020yCat.1350....0G)" (1 Introduction) [from (cite: 2020yCat.1350....0G)]
- External data: Dust composition/opacities: amorphous olivine 50% Mg 50% Fe  
  > "opacities calculated for a composition of amorphous olivine with 50% Mg and 50% Fe (cite: 1994A&A...292..641J; 1995A&A...300..503D)" (4 Radiative Transfer Modeling) [from (cite: 1994A&A...292..641J; 1995A&A...300..503D)]
- Simulation/model as data: Grid of 34,560 RADMC-3D scattered light models (10^6 photon packets) and 1024 Sobol-sampled training models (5x10^6 photons) plus 128 validation models, used to train a neural network  
  > "The grid range and step size are shown in Table [2](#tab:model_grid) and amount to 34,560 models in total." (4.2 Geometry of the Tilted Inner disk)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.41x0.32 arcsec (continuum), 0.38x0.31 arcsec (CO)  
  > "$0\hbox{$.\!\!^{''}$}38 \times 0\hbox{$.\!\!^{''}$}31$ at $-75^\circ$" (2.2 ALMA mm observations)
- final rms: 0.13 mJy/beam continuum; 5 mJy/beam per 0.5 km/s channel  
  > "5 mJy beam$^{-1}$ per 0.5 ${\rm km~s^{-1}}$ channel for the line." (2.2 ALMA mm observations)

### Inherited from earlier work

- ALMA calibration and imaging follow the eDisk reduction procedures  
  > "reduced it using the same procedures[^2] as for the eDisk project (cite: 2023ApJ...951....8O)" (2.2 ALMA mm observations) [from (cite: 2023ApJ...951....8O)]
- SPHERE observing mode and instrumental polarization model  
  > "IRDAP accounts for instrumental polarization by means of a detailed instrument model described in (cite: 2020A&A...633A..64V)." (2.1 SPHERE near-infrared observations) [from (cite: 2020A&A...633A..64V)]
- Sobol sequence sampling for NN training  
  > "we sampled the parameter space over the same range in Table [2](#tab:model_grid) using a Sobol sequence as in (cite: 2023A&A...672A..30K)." (4.3 Neural network) [from (cite: 2023A&A...672A..30K)]
- Two grain populations (0.1 and 300 micron)  
  > "We model the dust as consisting of two size populations (cite: 2012A&A...539A.148B) with $0.1\,\mu$m and $300\,\mu$m grains" (4 Radiative Transfer Modeling) [from (cite: 2012A&A...539A.148B)]

### Not stated but needed to reproduce (our reading)

- ALMA CASA version and calibration details (deferred to eDisk scripts)
- Observing dates, array configurations, baselines, spectral setup, and time on source
- Weighting/robust, cell and image size, and continuum subtraction for ALMA imaging
- Neural network layer widths, learning rate, optimizer, epochs details and train/test setup
- Threshold/contour definitions for the northern disk and southern arc masks
- galario fit priors, sampler, and number of free parameters beyond those listed
- Whether visibility fit used all baselines and any weights
- Stellar luminosity/temperature used in RADMC-3D, and inner-disk warp code (provided privately by Dullemond)
- Dust mass fraction assumptions for the inner disk

## Analysis recipe

1. **Fit continuum ring in visibility plane**: Gaussian ring radial profile fit to real and imaginary visibilities  
  > "Using the `galario` package (cite: galario), we then fit the real and imaginary parts of the complex visibilities to constrain the ring parameters and disk inclination and position angle." (3.1 Continuum)
   - software: galario
   - assumption: Azimuthally symmetric Gaussian ring  
  > "We model the radial intensity profile as an azimuthally symmetric Gaussian ring centered at radius $R_{\rm ring}$" (3.1 Continuum)
   - fitting: _not stated_
   - validation: Fit compared with data (Figure 2)  
  > "The fit to the data is shown in Figure [2](#fig:galario)" (3.1 Continuum)
2. **Measure stellar mass from CO kinematics**: Keplerian fit to 2-D velocity field with inclination fixed to 40.1 deg  
  > "We use the `eddy` package (cite: eddy) to fit a Keplerian profile to the 2-D velocity field. We fix the inclination equal to $40.1^\circ$" (3.2 Kinematics)
   - software: eddy
   - assumption: Distance 160 pc; true uncertainties ~10% due to systematics  
  > "the true uncertainties are closer to $\sim 10$%, due to systematics and additional effects not modeled here" (3.2 Kinematics)
   - fitting: _not stated_
   - validation: Mass consistent with K1 spectral type and age  
  > "The derived stellar mass is consistent with the K1 spectral type and 5 Myr median age of Upper Sco." (3.2 Kinematics)
3. **Radiative transfer fit of ALMA continuum for large grains**: Grid of RADMC-3D models varying Sigma1, alpha, Rin, Rout; minimize sum of squared intensity residuals; inclination fixed 40 deg, PA -5 deg  
  > "The quality of each model was assessed by calculating the sum of the squared intensity residuals" (4.1 Large Grains in the Outer Disk)
   - software: radmc3d
   - assumption: 10% small grains, 90% large by mass  
  > "We set the mass fraction to be 10% small grains, 90% large" (4.1 Large Grains in the Outer Disk)
   - fitting: Grid search, not a statistically rigorous fit  
  > "we do not perform a statistically rigorous fit" (4.1 Large Grains in the Outer Disk)
   - validation: Visual comparison of data and model  
  > "A comparison of the data and model are shown in Figure [5]" (4.1 Large Grains in the Outer Disk)
4. **Grid of SPHERE scattered-light models of tilted inner disk**: RADMC-3D models with 5 free parameters Rtilt, itilt, PAtilt, H1, beta; compared to data via triangle auto-threshold binary masks  
  > "we settled on the triangle method, where the threshold is automatically determined from the normalized histogram of pixel values" (4.2 Geometry of the Tilted Inner disk)
   - software: radmc3d, scikit-image
   - parameter: Rin(small)=0.5 au, Rout(small)=96 au  
  > "we fix it to 0.5 au. The outer radius, $R_{\rm out}^{\rm small}$, simply scales the extent of the emission and we set it to 96 au" (4.2 Geometry of the Tilted Inner disk)
   - fitting: Likelihood from sum of squared difference of binary maps  
  > "maximizing the likelihood defined by the sum of the squared difference map" (4.2 Geometry of the Tilted Inner disk)
   - validation: _not stated_
5. **Train neural network emulator of RT images**: Fully connected network 5 inputs -> 1600 outputs (40x40), two hidden layers, leaky ReLU, MSE loss, 2000 epochs, trained on 1024 Sobol-sampled models  
  > "The input is a vector composed of the five model parameters" (4.3 Neural network)
   - software: PyTorch
   - fitting: MSE loss  
  > "calculates the mean squared error between the network predictions and training targets" (4.3 Neural network)
   - validation: 128 independent RT models compared with NN images  
  > "we carried out a validation test by comparing an independent set of 128 radiative transfer models with neural network images" (4.3 Neural network)
6. **MCMC fit of inner disk geometry**: emcee with 20 walkers, uniform priors over grid ranges, 10,000 steps after 2,000 burn-in  
  > "uniformly sampling across the parameter extents of our model grid in Table [2](#tab:model_grid), with 20 walkers." (4.4 MCMC model fitting)
   - software: emcee
   - fitting: emcee, uniform priors, threshold-map likelihood with NN images  
  > "we show results for 10,000 steps after discarding the first 2,000 from the burn-in phase" (4.4 MCMC model fitting)
   - validation: Maximum likelihood model compared with SPHERE image  
  > "Figure [13](#fig:bestfit) shows the maximum likelihood model in comparison with the SPHERE image." (4.4 MCMC model fitting)
7. **Compute misalignment and companion constraint**: Misalignment angle formula from Min et al. 2017; companion constraint from Nixon et al. 2013 formula  
  > "From (cite: 2017A&A...604L..10M), we calculate the misalignment angle between the outer disk and tilted inner disk" (5 Discussion)
   - assumption: Inner and outer disk rotate in same direction; wave-like warp regime alpha<H/R  
  > "Under the reasonable assumption that the inner and outer disk rotate in the same direction" (5 Discussion)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **galario** : Visibility-plane fit of continuum ring  
  > "Using the `galario` package (cite: galario)" (3.1 Continuum)
- **eddy** : Keplerian rotation map fit  
  > "We use the `eddy` package (cite: eddy)" (3.2 Kinematics)
- **radmc3d** : Dust thermal emission and scattering models  
  > "using the versatile `radmc3d` code (cite: radmc3d)" (4 Radiative Transfer Modeling)
- **emcee** : MCMC fitting  
  > "We use the `emcee` package (cite: emcee)" (4.4 MCMC model fitting)
- **PyTorch** : Neural network  
  > "`PyTorch` (used here)" (4.3 Neural network)
- **scikit-image** : Triangle thresholding  
  > "Various thresholding algorithms are implemented in the python image processing package `scikit-image`" (4.2 Geometry of the Tilted Inner disk)
- **IRDAP** : SPHERE data reduction  
  > "The data was reduced using the public IRDAP (IRDIS Data reduction for Accurate Polarimetry) pipeline" (2.1 SPHERE near-infrared observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Ring radius | 63.0 | 0.1 | au | 1 | / $R_{\rm ring}$ / 63.0  / 0.1   / au   / |
| Ring FWHM | 29.0 | 0.4 | au | 1 | / FWHM           / 29.0  / 0.4   / au   / |
| Outer disk inclination | 40.1 | 0.25 | deg | 1 | / incl           / 40.1  / 0.25  / deg  / |
| Outer disk PA (continuum) | -2.0 | 0.4 | deg | 1 | / PA             / -2.0  / 0.4   / deg  / |
| Stellar mass | 0.99 | ~10% (true) | Msun | 2 | find a best fit stellar mass of $0.99\,M_\odot$ |
| Dust mass | 42 | not stated | Earth masses | 3 | The total dust mass is $42\,M_\oplus$. |
| Rtilt | 23.4 | 0.2 | au | 6 | / $R_{\rm tilt}$        / 23.4  / 0.2   / au   / |
| itilt | 13.1 | 0.4 | deg | 6 | / $i_{\rm tilt}$        / 13.1  / 0.4   / deg  / |
| PAtilt | 102.9 | 0.3 | deg | 6 | / ${\rm PA}_{\rm tilt}$ / 102.9 / 0.3   / deg  / |
| Misalignment angle | 38 | not stated | deg | 7 | the misalignment angle between the outer disk and tilted inner disk to be |
| Companion constraint RHS | 1.4 | not stated | au | 7 | the right hand side equates to 1.4 au |

## Qualitative findings

- Mm-sized dust is in a ring with cavity ~40 au, while CO emission fills the cavity  
  > "we detect CO emission within the millimeter continuum cavity" (3.2 Kinematics)

## Claim tuples

- H: A misaligned inner disk causes the southern shadow | E: RADMC-3D grid plus NN-assisted MCMC fit to SPHERE image | R: Best fit Rtilt 23.4 au, itilt 13.1 deg, PAtilt 102.9 deg | F: Inner and outer disk are misaligned by 38 deg | **supported**
- H: A neural network can emulate RT images to enable Bayesian fitting | E: Trained on 1024 models, validated on 128 | R: Network reproduces model morphologies with occasional hot pixels | F: Simulation-based inference is feasible for RT modeling | **supported**
- H: A companion may drive the misalignment | E: Apply Nixon et al. 2013 break radius formula | R: Constraint on companion mass and orbital radius | F: Low-mass close companion allowed; no clear binary signatures | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Intensity-based likelihood is hard for SPHERE image (substructure, phase function, faint arc), so binary-threshold morphology matching was used  
  > "Instead, we focus on matching the scattered light morphology to compare the models to the observations." (4.2 Geometry of the Tilted Inner disk)
- Alternative: Arc from front side outer radii rejected since it does not extend around the disk  
  > "We rule out a scenario where this comes from the outer radii of the front side of the disk" (4.2 Geometry of the Tilted Inner disk)
- How they decided it was enough: _not stated_
- Limitation (authors): Error dominated by model validity rather than statistics; ALMA resolution too poor to examine inner kinematics  
  > "The precision with which each parameter is determined belies the error in matching the observations" (4.4 MCMC model fitting)
- Caveat (inferred, ours): Uncertainties are purely statistical and strongly underestimate systematic error
- Caveat (inferred, ours): Fixed dust properties and no substructure/phase function modeling
- Caveat (inferred, ours): Degenerate PA solution (180 deg) and assumption of co-rotation
- Caveat (inferred, ours): ALMA RT fit not statistically rigorous

## Reproducibility

- Data public (paper): ALMA data downloaded from archive  
  > "We downloaded ALMA observations of V1098 Sco from the archive" (2.2 ALMA mm observations)
- Products in archive: _not stated_
- Missing: SPHERE data access (ESO archive) not explicitly stated
- Missing: NN architecture details and code
- Missing: Inner-disk warp code from Dullemond
- Missing: Thresholding mask contours
- Data volume (inferred): ~10-50 GB ALMA archive data for one Band 7 project; SPHERE small
- Score (inferred): 3/5, Public data and named tools, but key NN and RT setup details and code are not given.
- Rediscovery candidate: no, Main results depend on SPHERE data and custom RT/NN pipeline not fully specified; only ALMA ring/mass parts are easily redone.

## Links

- Method: (cite: 2023ApJ...951....8O) (eDisk reduction procedures used for ALMA data)
- Method: (cite: 2023A&A...672A..30K) (Sobol sampling and NN approach)
- Companion: (cite: 2025ApJ...978..117C) (Source of the archival ALMA observations)
- Related: eDisk
- Related: DESTINYS

## Checks

```json
{
 "quotes": 67,
 "quotes_ok": 67,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 11,
 "numeric_problems": 0,
 "fill": {
  "facts": 87,
  "stated": 50,
  "rate": 0.575
 },
 "evidence_ok": true
}
```
