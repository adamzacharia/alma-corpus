# Gas Inside the 97 AU Cavity around the Transition Disk Sz 91

`2015ApJ...805...21C` | The Astrophysical Journal 2015 | first author: Canovas, H. | arXiv: 1503.04821 | DOI: 10.1088/0004-637X/805/1/21

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks
- Question: What are the geometry, dust cavity size and gas content inside the cavity of the transition disk Sz 91, and what do they imply for the cavity-making mechanism?  
  > "We here use ALMA cycle 0 band-6 and band-3 observations to describe the disk in more detail." (Introduction)
- Target **Sz 91**: coordinates _not stated_; z/distance 200 pc  
  > "The transition disk Sz 91, at 200 pc (cite: merin2008)" (Introduction); distance from Merin et al. 2008  
  > "The transition disk Sz 91, at 200 pc (cite: merin2008)" (Introduction)

## Data provenance

- ALMA projects: _none stated_
- bands: Band 6 (231 GHz) and Band 3 (110 GHz)  
  > "Sz 91 was observed with ALMA band-6 (231 GHz) and band-3 (110 GHz) during Cycle-0" (2.1 Interferometry)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: Band 6 total 2x1.875 GHz; band 3 total 7.5 GHz  
  > "The total bandwidth of the band-3 observations was 7.5 GHz ($4\times1.875$ GHz)." (2.1 Interferometry)
- arrays: _not stated_
- configurations: _not stated_
- baselines: 21-402 m in band 6; 21-452 m in band 3  
  > "ranging from 21 to 402 m (16 to 309 k$\lambda$) in band-6, and from 21 to 452 m (7 to 167 k$\lambda$) in band-3." (2.1 Interferometry)
- angular resolution: band 6 beam 0.86" x 0.60", PA 88.9 deg; band 3 beam 2.08" x 1.51"  
  > "the beam is $0.86\ensuremath{''} \times 0.60\ensuremath{''}$ with a position angle (PA) of $88.9\ensuremath{^\circ}$ in band-6" (2.1 Interferometry)
- max recoverable scale: _not stated_
- sensitivity: continuum rms 0.1 mJy/beam in both bands; 12CO channel median rms 6.2 mJy/beam  
  > "In the continuum, we reach a rms of 0.1 mJy/beam in band-6 and 0.1 mJy/beam in band-3." (2.1 Interferometry)
- time on source: 3.77 min per band-6 epoch; 0.4 min band 3  
  > "226 seconds (3.77 minutes) in band-6 and 24 seconds (0.4 minutes) in band-3" (2.1 Interferometry)
- observing dates: 18/06/2012, 02/07/2012, 03/07/2012, 04/07/2012 (band 6); 01/08/2012 (band 3)  
  > "109.99 | 01/08/2012 | Neptune" (Table 1)
- pi or archival as stated: _not stated_
- Line: 12CO 2-1 (230.538 GHz)
- Line: 13CO 1-0 (110.20135 GHz)
- Line: C18O 1-0 (109.78218 GHz)
- Other facility **Herschel PACS/SPIRE, WISE**: Far-IR and mid-IR photometry for SED  
  > "We add two WISE flux at 12 and 22 $\mu$m, two Herschel/PACS fluxes at 100 and $160\ensuremath{\mu}m$" (2.2 Photometry)
- Other facility **VLT/X-shooter**: Public spectra for stellar systemic velocity  
  > "we used public VLT/X-shooter spectra (ID: 089.C-0143) to derive the systemic radial velocity of Sz 91" (3 Continuum and 12CO images)
- External data: SED photometry (optical to 850 um) of Sz 91  
  > "to the photometry presented by (cite: romero2012)" (2.2 Photometry) [from Romero et al. 2012 (cite: romero2012)]
- External data: Herschel fluxes  
  > "For the Herschel fluxes we adopt the most recent values presented by (cite: bustamante2015)." (2.2 Photometry) [from (cite: bustamante2015)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Titan/Neptune (band 6 epochs), Neptune (band 3)  
  > "18/06/2012 | Titan" (Table 1)
- flux scale uncertainty: ~15% (lower limit)  
  > "We used the dispersion of the band-6 flux calibrations to estimate a flux uncertainty of $\approx15\%$." (2.1 Interferometry)
- self calibration: _not stated_

### Imaging

- task: CASA CLEAN, natural weighting; four band-6 datasets concatenated  
  > "The visibilities were Fourier transformed and deconvolved, using natural weighting, with the CLEAN algorithm" (2.1 Interferometry)
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
- final beam: _not stated_
- final rms: 0.1 mJy/beam continuum  
  > "In the continuum, we reach a rms of 0.1 mJy/beam in band-6" (2.1 Interferometry)

### Inherited from earlier work

- Stellar and SED photometry base  
  > "to the photometry presented by (cite: romero2012)" (2.2 Photometry) [from (cite: romero2012)]
- Surface density index p_s=1 fixed for Regions 1,2  
  > "we fix the power-law indexes of their surface density distribution to the standard value of $p_s = 1$ following (cite: andrews2007)" (5.3 Fitting procedure) [from (cite: andrews2007)]

### Not stated but needed to reproduce (our reading)

- CASA version
- clean threshold, mask, cell and image size
- uv-fit model settings and how three fits were combined
- genetic algorithm mutation/crossover settings and chi2 weights
- gas model velocity-resolution and CO line-profile comparison details
- MCFOST version and grid settings

## Analysis recipe

1. **Image continuum and 12CO**: Concatenate band-6 datasets; natural-weighted CLEAN; moment maps  
  > "For the band-6 data, we combined the four datasets to increase the $uv$ coverage before cleaning." (2.1 Interferometry)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Measure fluxes and disk geometry from visibilities**: uv-plane fits (Gaussian in band 6, point source in band 3); ring, disk, Gaussian fits with uvfit for i, PA, center  
  > "In band-6 Sz 91 is resolved (see next section), so we fit a Gaussian profile; in band-3 Sz 91 is not resolved, so we use a point-source profile." (2.2 Photometry)
   - software: CASA uvfit
   - fitting: _not stated_
   - validation: Compared to Tsukagoshi et al. 2014 values  
  > "These results are in agreement with those derived by T2014" (4.3 Disk orientation)
3. **Radial binning of deprojected visibilities**: 30 equal-count radial bins; null at ~150 klambda indicates cavity  
  > "We split the continuum and $^{12}\mathrm{CO}$ visibilities into 30 radial bins, ensuring that all bins contain the same amount of visibilities." (4.5 Inner disk)
   - fitting: _not stated_
   - validation: _not stated_
4. **Dust radiative transfer model fit to SED + continuum visibilities**: Three-region axisymmetric MCFOST model; genetic algorithm minimizing chi2_SED + chi2_uv  
  > "We use a population of 50 "parent" models and let them evolve through 50 generations, resulting in a total of 2500 models." (5.3 Fitting procedure)
   - software: MCFOST, CASA simalma
   - parameter: p_s=1, psi=1.15, gamma=0.3, a_min=0.05 um in Regions 2,3  
  > "We find that our data is equally well fitted with values ranging from $\gamma = [-0.2, 0.8]$ and use $\gamma = 0.3$." (5.3 Fitting procedure)
   - assumption: Compact astrosilicates, Mie theory, power-law size distribution  
  > "For the composition we assumed compact astro-silicates (cite: mathis1989) with a power-law size distribution (cite: draine2006)." (5.2 Dust composition and distribution)
   - fitting: Genetic algorithm, combined reduced chi2  
  > "The quality of a fit is measured with the combined reduced $\chi^2$ given by the sum of reduced $\chi^2$ from SED and the continuum visibilities" (5.3 Fitting procedure)
   - validation: Synthetic simalma image; residual rms 0.1 mJy/beam; one-at-a-time local chi2 grids  
  > "The residual image has an rms of 0.1 mJy/beam similar to the rms of the observations." (5.4 Modeling results)
5. **Gas 12CO model**: Manual exploration on dust model; vary v_turb and gas mass in cavity; compare line profile  
  > "we manually explore different models by varying the turbulence velocity ($v_\mathrm{turb}$) within a range of \[10,300\] m/s" (5.6 Gaseous Disk)
   - software: MCFOST
   - assumption: gas-to-dust 100, CO freeze-out at 20 K, H2/12CO = 1e4, LTE, Keplerian  
  > "We fix the gas to dust ratio in the outer region (Region 3) to the standard value of 100, and we ensure that the $^{12}\mathrm{CO}$ freezes-out at 20 K" (5.6 Gaseous Disk)
   - fitting: _not stated_
   - validation: Model profile deficit at high velocities  
  > "compared to the observations the model shows a lack of emission at higher velocities, and an excess at lower velocities" (6.2 Model limitations)

## Software

- **CASA** : Calibration, imaging, uvfit, simalma  
  > "The observations were processed using the Common Astronomy Software Application (CASA) package" (2.1 Interferometry)
- **MCFOST** : Radiative transfer disk modeling  
  > "using the radiative transfer code MCFOST (cite: pinte2006; pinte2009)" (5 Radiative transfer model)
- **Analysis Utilities** : buildConfigurationFile for simulated array  
  > "We created an antenna configuration file that mimics our observations using the buildConfigurationFile/Analysis Utilities" (5.4 Modeling results)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Inclination | 49.5 | 3.5 | deg | 2 | $i=49.5\ensuremath{^\circ}\pm3.5\ensuremath{^\circ}$ |
| Position angle | 18.2 | 3.5 | deg | 2 | $\mathrm{PA}=18.2\ensuremath{^\circ}\pm3.5\ensuremath{^\circ}$ |
| Dust cavity radius | 97 | not stated | au | 4 | $R_{cav}$ / $97$ au |
| Band 3 flux | 0.7 | 0.1 | mJy | 2 | 2700.00 / 0.7 / 0.1 / This work |
| 1.3 mm flux (uv fit) | 12.7 | 1.9 | mJy | 2 | 1300.00 / 12.7 / 1.9 / This work |
| alpha_0.8-1.3mm | 2.34 | 0.40 | dimensionless | 2 | $\alpha_\mathrm{0.8-1.3mm} = 2.34\pm0.40$ |
| alpha_1.3-2.7mm | 4.07 | 0.29 | dimensionless | 2 | $\alpha_\mathrm{1.3-2.7mm} = 4.07\pm0.29$ |
| 12CO integrated flux (visibility fit) | 3.0 | 0.4 | Jy km/s | 2 | A Gaussian fit to the visibilities yields a larger value of $\mathrm{F_{^{12}CO}}=3.0\pm0.4$ Jy km/s. |
| Innermost radius of 12CO gas probed | 28 | not stated | au | 3 | our observations probe the $^{12}\mathrm{CO}$ gas down to $\sim28$ au from the central star |
| Dust mass Region 3 | 14.3 | not stated | Earth masses | 4 | $M_\mathrm{dust_3}$ / $14.3$ $M_\mathrm{\ensuremath{\oplus}}$ |
| Turbulent velocity | 120 | not stated | m/s | 5 | with $v_\mathrm{turb} = 120$ m/s |

## Qualitative findings

- Gas detected at larger radii (400 au) than dust (220 au).  
  > "We detect gas at larger radii (400 au) than the dust (220 au)." (Conclusions)

## Claim tuples

- H: Does Sz 91 have a very large mm-dust cavity? | E: uv-plane fits and MCFOST modeling of band 6 continuum and SED | R: Cavity radius ~97 au; null in visibilities at ~150 klambda | F: Largest cavity around a T Tauri star | **supported**
- H: Is there gas inside the dust cavity? | E: 12CO(2-1) channel maps and velocity analysis | R: Emission down to 0.5 km/s at S/N~6, probing gas to ~28 au | F: Gas present well inside the cavity | **supported**
- H: Is a three-zone dust structure required? | E: Genetic search with two- vs three-region models | R: Two-region model could not match data | F: Three-zone model required, though Region 1/2 details are degenerate | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Photoevaporation and grain growth alone excluded; a low-mass stellar companion cannot be excluded.  
  > "However, we cannot yet exclude that a low mass stellar companion is carving the cavity in the disk around Sz 91." (6.3 Cavity-making mechanism)
- How they decided it was enough: _not stated_
- Limitation (authors): Local one-parameter exploration does not give proper statistical errors; parameters correlated; gas model poorly matches line profile.  
  > "the exercise we performed does not allow to derive proper statistical errors of the fitted parameters" (6.2 Model limitations)
- Caveat (inferred, ours): 12CO strongly contaminated by cloud absorption
- Caveat (inferred, ours): Moderate resolution (~0.6 arcsec) limits cavity constraints
- Caveat (inferred, ours): Distance 200 pc uncertain
- Caveat (inferred, ours): Alpha_mm tension dismissed as underestimated errors

## Reproducibility

- Data public (paper): Cycle 0 program 2011.0.00733 and public X-shooter spectra  
  > "we used public VLT/X-shooter spectra (ID: 089.C-0143)" (3 Continuum and 12CO images)
- Products in archive: _not stated_
- Missing: CASA version and clean parameters
- Missing: MCFOST input files and GA settings
- Missing: gas model details
- Data volume (inferred): ~10-30 GB raw
- Score (inferred): 5/5, Public Cycle 0 data and clear model table, but imaging and fitting settings are sparse.
- Rediscovery candidate: yes, Public data; geometry, fluxes and alpha_mm are reproducible numeric results.

## Links

- Method: Pinte et al. 2006, 2009 (MCFOST) (Radiative transfer code)
- Companion: Tsukagoshi et al. 2014 (SMA and Subaru observations of Sz 91)
- Companion: Romero et al. 2012 (Earlier SED and stellar properties of Sz 91)

## Checks

```json
{
 "quotes": 57,
 "quotes_ok": 57,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 0,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2011.0.00733.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 11,
 "numeric_problems": 0,
 "fill": {
  "facts": 73,
  "stated": 39,
  "rate": 0.534
 },
 "evidence_ok": true
}
```
