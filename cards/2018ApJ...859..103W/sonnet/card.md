# Extended Millimeter Emission in the HD 141569 Circumstellar Disk Detected with ALMA

`2018ApJ...859..103W` | The Astrophysical Journal 2018 | first author: White, Jacob Aaron | arXiv: 1804.09724 | DOI: 10.3847/1538-4357/aac088

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: protoplanetary_disks, debris_disks
- Question: Is there extended millimeter emission exterior to the inner disk of HD 141569, and how do the grain size distributions of the inner and outer disks compare?  
  > "These data detect extended millimeter emission that is exterior to the inner disk." (abstract)
- Target **HD 141569**: coordinates _not stated_; z/distance 111 pc  
  > "corresponding to $\sim 112$ au at the system distance of 111 pc." (Observational Data); distance from _not stated_

## Data provenance

- ALMA projects: 2012.1.00698.S, 2015.1.01600.S, 2013.1.00883.S
- bands: 345, 230 and 100 GHz  
  > "We present archival ALMA observations of the HD 141569 circumstellar disk at 345, 230, and 100 GHz." (abstract)
- frequencies and spectral setup: 230 GHz: four SPWs (468.75 MHz at 219.565 GHz; 117.18 MHz at 220.40 GHz; two 2000 MHz at 231.02 and 233.02 GHz)  
  > "two SPWs had 2000 MHz bandpasses centered at rest frequencies of 231.02 and 233.02 GHz." (Observational Data)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 230 GHz: 1.03 x 0.99 arcsec, PA 70.8 deg  
  > "The size of the resulting synthesized beam is $1.03 \times 0.99$ arcsec$^{2}$ at a position angle of 70.8$^{\circ}$" (Observational Data)
- max recoverable scale: _not stated_
- sensitivity: 230 GHz: 130 uJy/beam  
  > "The 230 GHz observations achieve a sensitivity of $130~\mu \rm Jy~beam^{-1}$." (Observational Data)
- time on source: 230 GHz: 20.5 min total, about 2.25 min on source  
  > "The total integration time was 20.5 minutes, with about 2.25 minutes on source." (Observational Data)
- observing dates: 230 GHz: 2016 May 16  
  > "The ALMA 230 GHz observations were taken on 2016 May 16$^{\rm th}$." (Observational Data)
- pi or archival as stated: _not stated_
- Other facility **HST**: PSF-subtracted scattered light image from Konishi et al. 2016  
  > "a PSF subtracted HST scattered light image from (cite: konishi)" (Observational Data)
- External data: 345 GHz ALMA data previously published  
  > "The 345 and 100 GHz data were published previously by (cite: white16) and (cite: white17), respectively." (Observational Data) [from (cite: white16)]
- External data: HST scattered light image  
  > "a PSF subtracted HST scattered light image from (cite: konishi)" (Observational Data) [from (cite: konishi)]

## Processing

### Calibration

- pipeline or manual: 230 GHz reduced with CASA pipeline  
  > "The data were reduced using the Common Astronomy Software Applications (CASA 4.5.3) pipeline (cite: casa)" (Observational Data)
- casa version: CASA 4.5.3  
  > "The data were reduced using the Common Astronomy Software Applications (CASA 4.5.3) pipeline (cite: casa)" (Observational Data)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Titan (230 GHz)  
  > "and flux calibration with Titan." (Observational Data)
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
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Disk geometry projection of visibilities  
  > "we calculate the visibilities and project them to the disk geometry (cite: white16)." (Visibility Fitting) [from (cite: white16)]
- MCMC framework  
  > "using the framework laid out in (cite: white_fom)." (Visibility Fitting) [from (cite: white_fom)]
- Mass estimate method for grain size distribution  
  > "we adopt the methods laid out in (cite: white16; white17)" (Discussion) [from (cite: white16; white17)]

### Not stated but needed to reproduce (our reading)

- Disk inclination and position angle values used for the models and the radial profiles
- Phase center and stellar position
- Imaging parameters for the continuum images (weighting, cell, size)
- Details of the 345 and 100 GHz calibration
- MCMC settings (chain length, walkers, burn-in, step size)
- Dust temperature used for alpha_pl
- Which channels or SPWs were used as continuum
- Visibility weighting and any flux scale corrections

## Analysis recipe

1. **Bin visibilities**: Annular averaging of visibilities for each frequency  
  > "The visibility data for each frequency is annularly averaged in 10-k$\lambda$ bins" (Visibility Fitting)
   - parameter: 10 klambda bins; uncertainty is the standard deviation per bin  
  > "The uncertainties represent the standard deviation of each bin." (Visibility Fitting)
   - fitting: _not stated_
   - validation: _not stated_
2. **Fit single-component disk model**: MCMC fit of a surface brightness ∝ r^-1 disk with inner and outer edges to all three data sets at once  
  > "The single-component model used here adopts a surface brightness profile $\propto r^{-1}$ and assumes the disk has an inner and outer edge." (Single-Component Model)
   - parameter: Free: 345 GHz flux, spectral index, disk center, width; uniform priors flux 0.01-50 mJy, disk 0.1-300 au, index 0-4  
  > "A uniform prior distribution is chosen for the flux to range from .01 to 50 mJy, the disk from 0.1 to 300 au, and the spectral index from 0 to 4." (Single-Component Model)
   - assumption: Flux follows a single power law in frequency  
  > "(and assuming the flux is well defined by a single power law in frequency)" (Single-Component Model)
   - fitting: Metropolis-Hastings MCMC; chi2 averaged with equal weight over the three frequencies  
  > "The three are averaged together with equal weighting to get a representative $\chi^{2}$." (Visibility Fitting)
   - validation: Jeffreys priors gave negligible differences; uniform-disk fit consistent with uvmodelfit  
  > "we ran MCMC modeling for the single component using Jeffreys priors, which resulted in negligible differences." (Single-Component Model)
3. **Fit two-component disk model**: MCMC fit of inner and outer disks, each with own center, width and spectral index; non-overlapping  
  > "The inner disk prior range is from 0.1 to 100 and the outer disk prior range is from 50 to 500 au, and models are not accepted if the two disks overlap." (Two-Component Model)
   - fitting: Same MCMC; most probable values and 95% credible regions  
  > "A summary of the most probable model parameters, 95% Credible Region, and reduced $\chi^{2}$ at each frequency are given in Table [\[obs\]](#obs)." (Two-Component Model)
   - validation: Compared reduced chi2 of the models  
  > "the two-component model is preferred (1.74 versus 1.08 averaged reduced $\chi^{2}$)" (Discussion)
4. **Azimuthally averaged radial profiles**: Sum flux in elliptical apertures from images, normalize and compare with HST  
  > "These curves were generated by summing up the total flux in elliptical apertures with the inclination and position angle previously constrained in the disk (cite: white16)." (Discussion)
   - fitting: _not stated_
   - validation: Check for a slight peak consistent with visibility-modeled outer disk  
  > "the slight peak in flux is broadly consistent with the 95 - 300 au outer disk location detected in the visibility data." (Discussion)
5. **Derive grain size distribution slope q**: q = (alpha_mm - alpha_pl)/beta_s + 3  
  > "q = \frac{\alpha_{mm} - \alpha_{pl}}{\beta_{s}} + 3," (Discussion)
   - assumption: beta_s = 1.8±0.2  
  > "where $\beta_{s} = 1.8\pm0.2$ is a power law index for the dust opacity (cite: draine)" (Discussion)
   - fitting: _not stated_
   - validation: _not stated_
6. **Estimate dust mass**: Optically thin single grain size mass, and a full size distribution mass for 10 um to 3 mm grains  
  > "assume the disk is populated only by grains that have been observed (i.e. $\sim~10~\mu$m to $\sim~3$ mm)." (Discussion)
   - assumption: rho = 1 g/cm3, T*=10500 K, L*=24.2 Lsun, d=111 pc, albedo~0, grain radius = wavelength  
  > "The adopted stellar parameters are $T_{*} = 10500$ K, $L_{*} = 24.2~\rm L_{\odot}$, and $d=111$ pc." (Discussion)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.5.3: Pipeline reduction of the 230 GHz data; uvmodelfit in earlier work  
  > "The data were reduced using the Common Astronomy Software Applications (CASA 4.5.3) pipeline (cite: casa)" (Observational Data)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Inner disk extent (two-component) | 16 to 45 au | not stated | au | 3 | The inner disk ranges from approximately 16 to 45 au |
| Outer disk extent | 95 to 300 au | not stated | au | 3 | the outer disk ranges from 95 to 300 au |
| Inner disk spectral index | 1.81 | ±0.15 | dimensionless | 3 | The best fit spectral indicies of $1.81\pm0.15$ and $2.28^{+0.43}_{-0.29}$ |
| Outer disk spectral index | 2.28 | +0.43/-0.29 | dimensionless | 3 | The best fit spectral indicies of $1.81\pm0.15$ and $2.28^{+0.43}_{-0.29}$ |
| Inner disk q | 2.95 | ±0.10 | dimensionless | 5 | corresponds to a grain size distribution of $q =2.95\pm0.10$ |
| Outer disk q | 3.21 | +0.30/-0.16 | dimensionless | 5 | $q=3.21^{+0.30}_{-0.16}$ |
| Average reduced chi2 single vs two-component | 1.72 vs 1.08 | not stated | dimensionless | 3 | Average $\chi^{2}_{red}$       / 1.72                               / 1.08 |
| Mass in 10 um-3 mm solids, inner and outer disk | 0.041 and 0.18 | not stated | Earth masses | 6 | roughly 0.041 $\rm M_{\oplus}$ of small solids in the inner disk and 0.18 $\rm M_{\oplus}$ of small solids in the outer disk |
| Outer disk 345 GHz flux (two-component) | 11 | 95% range 8.4-13 | mJy | 3 | For the outer disk, the best fit 345 GHz flux is 11 mJy |

## Qualitative findings

- The outer disk's grain size distribution is steeper than the inner disk's; the radial profiles give only tentative support.  
  > "HD 141569’s outer disk has a steeper grain size distribution than the inner disk." (Summary)

## Claim tuples

- H: Millimeter emission exists exterior to the inner disk of HD 141569 | E: Simultaneous MCMC visibility fits of one- and two-component models to 345, 230 and 100 GHz data | R: Two-component model has average reduced chi2 of 1.08 vs 1.72; outer disk at 95-300 au | F: Extended mm emission is detected in the outer disk | **supported**
- H: The outer disk has a more evolved grain size distribution | E: Convert spectral indices to q | R: q = 2.95 inner, 3.21 outer | F: Outer disk has a steeper q, so is more evolved | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Equal weighting of frequencies may not reflect each data set's beam and sensitivity; image plane detection not convincing  
  > "an equal weighting of each frequency may not directly reflect the contribution from each set of visibilities." (Visibility Fitting)
- Caveat (inferred, ours): Outer disk detection rests on a modest chi2 improvement, and the 230 GHz data are noisy
- Caveat (inferred, ours): Spectral index uncertainties are large and overlap between protoplanetary and debris values
- Caveat (inferred, ours): Dust temperature for alpha_pl is not given

## Reproducibility

- Data public (paper): Archival ALMA data retrieved from the archive  
  > "The 230 GHz ALMA data were retrieved from the ALMA archive." (Observational Data)
- Products in archive: _not stated_
- Missing: MCMC code details and settings
- Missing: Disk geometry values
- Missing: Imaging and uv-averaging details
- Data volume (inferred): ~10-50 GB for three small datasets
- Score (inferred): 3/5, Public data and a clear model, but MCMC settings, geometry and the temperature assumption are missing, and the method is inherited from earlier papers.
- Rediscovery candidate: yes, Public data and numeric results, but the recipe has gaps.

## Links

- Method: (cite: white_fom) (MCMC visibility modeling framework)
- Method: (cite: white16) (Visibility projection and mass method)
- Companion: (cite: white16) (345 GHz data)
- Companion: (cite: white17) (100 GHz data)

## Checks

```json
{
 "quotes": 52,
 "quotes_ok": 52,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 3,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 9,
 "numeric_problems": 0,
 "fill": {
  "facts": 75,
  "stated": 37,
  "rate": 0.493
 },
 "evidence_ok": true
}
```
