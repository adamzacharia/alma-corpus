# ALMA Observations of Elias 2-24: A Protoplanetary Disk with Multiple Gaps in the Ophiuchus Molecular Cloud

`2017ApJ...851L..23C` | The Astrophysical Journal Letters 2017 | first author: Cieza, Lucas A. | arXiv: 1711.06905 | DOI: 10.3847/2041-8213/aa9b7b

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks
- Question: Does the Elias 2-24 disk show gaps in 1.3 mm continuum, and do the gap temperatures and widths point to snow-lines or forming planets?  
  > "place the disk structure in the context of mechanisms capable of forming narrow gaps such as condensation fronts and dynamical clearing by actively forming planets." (abstract)
- Target **Elias 2-24**: coordinates _not stated_; z/distance ~125 pc  
  > "nearby Ophiuchus Molecular Cloud (distance $\sim$125 pc; Loinard et al. 2008)" (Introduction); distance from Loinard et al. 2008  
  > "nearby Ophiuchus Molecular Cloud (distance $\sim$125 pc; Loinard et al. 2008)" (Introduction)

## Data provenance

- ALMA projects: 2016.1.00545.S
- bands: Band 6 (230 GHz/1.3 mm)  
  > "Elias 2-24 was observed by ALMA in band-6 (230 GHz/1.3 mm)" (1.3 mm observations)
- frequencies and spectral setup: Two continuum spws of 1.875 GHz at 232.6 and 218.0 GHz; three line spws for 12CO, 13CO, C18O (2-1)  
  > "two spectral windows with 1.875 GHz bandwidths for continuum observations centered at 232.6 and 218.0 GHz." (1.3 mm observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 16.7 to 2647.3 m, 42-45 12-m antennas  
  > "42-45 of the 12-m ALMA antennas were used with baselines ranging from 16.7 to 2647.3 m." (1.3 mm observations)
- angular resolution: 0.20'' x 0.25'' (clean, uniform weighting)  
  > "The cleaning resulted in a synthesized beam of 0.20$''$ $\times$ 0.25$''$ and a continuum rms of 0.26 mJy beam$^{-1}$." (Data analysis)
- max recoverable scale: _not stated_
- sensitivity: 0.26 mJy/beam, 0.19 mJy/beam after self-cal  
  > "Applying one iteration of phase-only self-calibration reduced the noise level to 0.19 mJy beam$^{-1}$ for this object," (Data analysis)
- time on source: 45 s  
  > "The total integration time on Elias 2-24 was 45 s." (1.3 mm observations)
- observing dates: July 13 and 14, 2017, three execution blocks  
  > "on July 13$^{th}$ and 14$^{th}$ 2017, in three different execution blocks." (1.3 mm observations)
- pi or archival as stated: _not stated_
- Line: 12CO 2-1 (230.5380 GHz)
- Line: 13CO 2-1 (220.3987 GHz)
- Line: C18O 2-1 (219.5603 GHz)
- External data: Stellar parameters, dust properties, parameterization, gas-to-dust ratio of 100 for the RT model  
  > "We adopt the same parameterization, stellar parameters, dust properties, and gas to dust mass ratio (i.e., 100) used by Andrews et al. (2010)." (Radiative transfer modeling) [from Andrews et al. (2010)]
- External data: Stellar mass of 1.0 Msun for planet mass estimates  
  > "a stellar mass of 1.0 M$_{\odot}$ (Andrews et al. 2016)" (Discussion) [from Andrews et al. (2016)]

## Processing

### Calibration

- pipeline or manual: Calibrated by the ALMA observatory with CASA  
  > "All the ODISEA data were calibrated using the Common Astronomy Software Applications package (CASA v4.2.1; McMullin et al. 2007) by the ALMA observatory" (Data analysis)
- casa version: CASA v4.2.1  
  > "(CASA v4.2.1; McMullin et al. 2007)" (Data analysis)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J1517-2422 and J1733-1304  
  > "J1517-2422 and J1733-1304 served as flux calibrators" (1.3 mm observations)
- flux scale uncertainty: _not stated_
- self calibration: One iteration of phase-only self-calibration  
  > "Applying one iteration of phase-only self-calibration reduced the noise level to 0.19 mJy beam$^{-1}$ for this object," (Data analysis)

### Imaging

- task: CASA clean, standard algorithm; all 3 EBs concatenated  
  > "We also used CASA to image all ODISEA data using the standard `clean` algorithm," (Data analysis)
- deconvolver: _not stated_
- weighting robust: uniform weighting  
  > "with uniform weightings." (Data analysis)
- uv taper: _not stated_
- cell size: 0.02'' pixel for uvmem images  
  > "These `uvmem` images have a pixel size of 0.02$''$" (Data analysis)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.20'' x 0.25''  
  > "The cleaning resulted in a synthesized beam of 0.20$''$ $\times$ 0.25$''$" (Data analysis)
- final rms: 0.26 mJy/beam (0.19 after self-cal)  
  > "a continuum rms of 0.26 mJy beam$^{-1}$." (Data analysis)

### Inherited from earlier work

- Bayesian MCMC procedure described in a companion paper  
  > "which is described in more detail in Pérez et al. (in prep)" (Radiative transfer modeling) [from Pérez et al. (in prep)]
- uvmem technical details  
  > "see Cárcamo et al. 2017 for technical details regarding `uvmen`" (Data analysis) [from Cárcamo et al. 2017]
- Model parameterization, stellar and dust properties, gas-to-dust ratio  
  > "We adopt the same parameterization, stellar parameters, dust properties, and gas to dust mass ratio (i.e., 100) used by Andrews et al. (2010)." (Radiative transfer modeling) [from Andrews et al. (2010)]

### Not stated but needed to reproduce (our reading)

- Dust opacity law and stellar luminosity/Teff used in RADMC-3D
- Priors and parameter bounds for the MCMC
- Number of photons and grid setup for RADMC-3D
- Clean mask, threshold, cell and image size
- Self-calibration solution interval and reference antenna
- Which fluxes were used to set flux scale
- uvmem weights and regularization details beyond the quoted values
- Stellar mass assumption for the planet mass hill-radius calculation as inclination of gaps vs stellar properties
- Definition of the missing mass integration limits

## Analysis recipe

1. **Calibrate and image continuum**: ALMA calibration in CASA; concatenate 3 EBs; clean with uniform weights; one round of phase-only self-calibration  
  > "The observations from all 3 execution blocks were concatenated and processed together to increase the signal to noise and uv-coverage." (Data analysis)
   - software: CASA
   - fitting: _not stated_
   - validation: Noise after self-cal consistent with expected thermal noise  
  > "consistent with the expected thermal noise." (Data analysis)
2. **Super-resolution image synthesis**: uvmem model image fit to visibilities with entropy regularization, and a pure chi^2 model with positivity  
  > "We used the `uvmem` package (Casassus et al. 2006, 2015) to fit a model image to the data in a least $\chi^2$ sense." (Data analysis)
   - software: uvmem
   - parameter: lambda = 0.1, G = 30, eta = 1.0  
  > "$\lambda= 0.1$, $G=30$, and $\eta = 1.0$." (Data analysis)
   - fitting: Least chi^2 with entropy regularization L = chi^2 - lambda S  
  > "using a measure of entropy regularization and the following objective function: $L = \chi^2 - \lambda S$" (Data analysis)
   - validation: 100 Monte Carlo noise injections into visibilities; third gap survives  
  > "specifically 100 different injections of gaussian random noise in the visibilities" (Data analysis)
3. **Disk geometry and radial profile**: Elliptical Gaussian fit to model image gives PA and inclination; deprojected azimuthal averaging in ellipses  
  > "An elliptical Gaussian fit to the model image indicates a position angle of 43.4 deg (East of North) and an inclination of 23.6 deg." (Data analysis)
   - fitting: _not stated_
   - validation: _not stated_
4. **Radiative transfer model of disk**: RADMC-3D with 5-parameter disk (Mdisk, gamma, Rc, h100, psi), MCMC fit  
  > "the structure of the disk can be fully described by 5 free parameters: $R_{C}$, $\Sigma_c$, $\gamma$, $h_{100}$, and $\psi$." (Radiative transfer modeling)
   - software: RADMC-3D, emcee
   - parameter: 100 walkers, 500 steps  
  > "we used 100 walkers for 500 steps" (Radiative transfer modeling)
   - assumption: Gas-to-dust ratio 100, Andrews et al. 2010 parameterization  
  > "gas to dust mass ratio (i.e., 100) used by Andrews et al. (2010)" (Radiative transfer modeling)
   - fitting: Affine invariant MCMC (emcee), chains initialized around Andrews et al. 2010 values  
  > "The chains were initialized in a uniform distribution around the parameters reported in Andrews et al. (2010)" (Radiative transfer modeling)
   - validation: Parameters agree within 1-2 sigma with Andrews et al. 2010  
  > "Our model parameters agree well (within 1–2-$\sigma$) with those derived by Andrews et al. (2010) using lower resolution data." (Radiative transfer modeling)
5. **Gap temperatures, widths and missing mass**: Midplane temperature from model at gap locations; Gaussian fits to gaps with IRAF splot; integrate model surface density over gap width  
  > "We can also estimate the mass of the “missing material" at each gap by integrating the surface density profile of the best-fit model over the width of the gap." (Radiative transfer modeling)
   - software: IRAF
   - assumption: Gaps are fully evacuated  
  > "We estimate the widths of the gaps by assuming that they are fully evacuated" (Radiative transfer modeling)
   - fitting: Gaussian fits with splot  
  > "Gaussian fits to the gaps using the `splot` routine within the IRAF package noao.onedspec" (Radiative transfer modeling)
   - validation: Equivalent widths consistent with integrating area and the deprojected radial average  
  > "produce consistent equivalent widths." (Radiative transfer modeling)
6. **Planet mass estimates**: Gap width = 4-8 Hill radii; r_Hill = a (m_p/3M*)^(1/3)  
  > "planets can open gaps that are 4 to 8 times the Hill radius" (Discussion)
   - assumption: Stellar mass 1.0 Msun  
  > "a stellar mass of 1.0 M$_{\odot}$ (Andrews et al. 2016)" (Discussion)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.2.1: Calibration and clean imaging  
  > "(CASA v4.2.1; McMullin et al. 2007)" (Data analysis)
- **uvmem** : Super-resolution non-parametric image synthesis  
  > "We used the `uvmem` package (Casassus et al. 2006, 2015)" (Data analysis)
- **RADMC-3D** : Radiative transfer modeling  
  > "using the code RADMC-3D (Dullemond et al. 2012)" (Radiative transfer modeling)
- **emcee** : MCMC sampling  
  > "the publicly available python module *emcee*" (Radiative transfer modeling)
- **IRAF** : Gaussian fits to gaps with splot  
  > "using the `splot` routine within the IRAF package noao.onedspec" (Radiative transfer modeling)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Integrated continuum flux | 345 | 35 mJy (absolute flux calibration) | mJy | 1 | The integrated continuum flux is 345 mJy $\pm$ 35 mJy |
| Position angle | 43.4 | not stated | deg | 3 | a position angle of 43.4 deg (East of North) and an inclination of 23.6 deg. |
| Inclination | 23.6 | not stated | deg | 3 | a position angle of 43.4 deg (East of North) and an inclination of 23.6 deg. |
| Gap locations | 20, 52, 87 | ±3, ±2, ±3 | au | 5 | the gaps are located at 20$\pm$3 au, 52$\pm$2 au, 87$\pm$3 au |
| Gap widths | 6, 28, 11 | ±2, ±3, ±4 | au | 5 | have widths of 6$\pm$2 au, 28$\pm$3 au, and 11$\pm$4 au. |
| Midplane temperature at gaps | 23, 15, 12 (at 20, 52, 87 au) | not stated | K | 5 | $\sim$23 K at 20 au, $\sim$15 K at 52 au, and $\sim$12 K at 87 au |
| Missing mass at gaps | ~4, 20, 10 (at 20, 52, 87 au) | not stated | MJup | 5 | we derive “missing masses" of $\sim$4 $M_{\mathrm{Jup}}$, 20 $M_{\mathrm{Jup}}$, and 10 $M_{\mathrm{Jup}}$ for the gaps at 20, 52 and 87 au |
| Planet masses | 0.2–1.5, 1.0–8.0, 0.02–0.15 (inner, middle, outer) | range from 4-8 Hill radii | MJup | 6 | we derive planets masses in the range of 0.2–1.5 $M_{\mathrm{Jup}}$, 1.0–8.0 $M_{\mathrm{Jup}}$, and 0.02–0.15 $M_{\mathrm{Jup}}$ |

## Qualitative findings

- Third gap at 0.18'' identified in the uvmem image; it survives noise realizations  
  > "This third gap survives the different realization of noise injected to the visibilities and it is seen as a change in slope in the deprojected radial average." (Data analysis)

## Claim tuples

- H: Elias 2-24 has multiple concentric gaps | E: 1.3 mm imaging with clean and uvmem | R: Gaps at ~20, 52, 87 au | F: Disk has three partially resolved gaps | **supported**
- H: Gaps are located at snow-lines | E: RT model midplane temperature at gap locations | R: 23, 15, 12 K | F: Temperatures close to CO and N2 condensation fronts | **partially**
- H: Forming planets can carve the gaps | E: Hill radius argument and missing mass from surface density | R: Planet masses 0.02-8 MJup versus missing mass 4-20 MJup | F: Enough mass to form such planets | **partially**

## Reasoning

- Why this data: Disk size, brightness and orientation allow substructure search at modest resolution  
  > "The size, brightness, and orientation of its disk, allow us to search for substructure in Elias  2-24 using what now can be considered modest resolution." (Introduction)
- Why this method: _not stated_
- Alternative: Water, ammonia and clathrate snow-lines lie at <20 au and are unresolved  
  > "all these temperatures correspond to stellocentric distances $<$ 20 au, which are not resolved by our observations." (Discussion)
- How they decided it was enough: _not stated_
- Limitation (authors): Gaps only partially resolved, degeneracy between width and depth  
  > "Since the gaps are only partially resolved, there is a degeneracy between the width and the depth of the gaps." (Radiative transfer modeling)
- Limitation (authors): Other explanations (MHD, instabilities) remain possible  
  > "However, other potential explanations still exist, including magneto-hydrodynamic effects and disk instabilities." (Summary and Conclusions)
- Caveat (inferred, ours): Smooth disk model fitted without gaps while temperatures taken at gap locations
- Caveat (inferred, ours): Snow-line match relies on a broad temperature range and a single midplane model
- Caveat (inferred, ours): Planet masses depend on the assumed 4-8 Hill radii and the gap widths from partially resolved data
- Caveat (inferred, ours): Very short 45 s integration; uvmem super-resolution may bias gap depths

## Reproducibility

- Data public (paper): Data cited by ALMA project code in the acknowledgments  
  > "This paper uses the following ALMA data: ADS/JAO.ALMA #2016.1.00545.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: MCMC priors and RT setup details deferred to Pérez et al. (in prep)
- Missing: Clean parameters and mask
- Missing: Dust opacity and stellar luminosity inputs
- Data volume (inferred): ~10-30 GB for three execution blocks
- Score (inferred): 3/5, Public data and clear outline, but RT modeling and imaging details are underspecified or deferred to in-prep papers.
- Rediscovery candidate: no, Key RT and imaging details are missing, though results are numeric.

## Links

- Method: Casassus et al. 2006, 2015 (uvmem package)
- Method: Cárcamo et al. 2017 (uvmem technical details)
- Method: Pérez et al. (in prep) (Bayesian MCMC modeling approach)
- Companion: Cieza et al. in prep. (ODISEA survey)
- Related: ODISEA (Ophiuchus DIsk Survey Employing ALMA)

## Checks

```json
{
 "quotes": 69,
 "quotes_ok": 69,
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
  "facts": 80,
  "stated": 53,
  "rate": 0.662
 },
 "evidence_ok": true
}
```
