# Measuring Protoplanetary Disk Gas Surface Density Profiles with ALMA

`2016ApJ...830...32W` | The Astrophysical Journal 2016 | first author: Williams, Jonathan P. | arXiv: 1606.05646 | DOI: 10.3847/0004-637X/830/1/32

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type archival_reuse

## Science

- Fields: protoplanetary_disks
- Question: Can gas surface density profiles of protoplanetary disks be measured from 13CO integrated intensity images, and what resolution and sensitivity are needed for T Tauri disks?  
  > "We extend the modeling approach presented in (cite: 2014ApJ...788...59W) to show that gas surface density profiles can be measured from high fidelity $^{13}$CO integrated intensity images." (abstract)
- Target **HD 163296**: coordinates _not stated_; z/distance 122 pc  
  > "The exceptional disk around the nearby (122 pc) Herbig Ae star HD 163296 is, fortunately, both big and bright." (The HD 163296 disk); distance from _not stated_

## Data provenance

- ALMA projects: 2011.0.00010.SV
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: Public ALMA Science Verification data  
  > "early ALMA observations of $^{13}$CO and other lines are publicly available through its Science Verification program" (The HD 163296 disk)
- Line: 13CO 2-1 (not stated)
- Line: C18O 2-1 (not stated)
- External data: Gas temperature structure T_gas(R,Z) for HD 163296  
  > "we use the gas temperature structure, $T_{\rm gas}(R,Z)$, described in (cite: 2013ApJ...774...16R)" (2.1 Description of the model) [from (cite: 2013ApJ...774...16R)]
- External data: Stellar mass 2.3 Msun and inclination 45 deg  
  > "we set the stellar mass, $2.3\,M_\odot$, and inclination, $i=45^\circ$, based on (cite: 2011ApJ...740...84Q)" (2.1 Description of the model) [from (cite: 2011ApJ...740...84Q)]
- Simulation/model as data: Library of 748 RADMC-3D 13CO 2-1 models for HD 163296; 9900-model T Tauri grid used for simulated observations  
  > "We created an image library by running 748 models over the range of parameters shown in Table [1](#tab:HD163296_grid)." (2.2 Image interpolation); "The resulting image library consists of 9900 models." (3.1 Description)

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
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Modeling methodology (CO isotopologue abundance, molecular layer, temperature parametrization)  
  > "We follow the methodology in Paper I but create a library of resolved images rather than a table of total line luminosities." (2.1 Description of the model) [from Paper I (cite: 2014ApJ...788...59W)]

### Not stated but needed to reproduce (our reading)

- Calibration and imaging procedure for the SV data, and how the zero-moment maps were made (channel range, clipping)
- Beam size and noise of the HD 163296 maps
- Fit region and masking, and how the model was convolved
- MCMC settings (walkers, steps, burn-in)
- Disk position angle and distance handling
- T_gas parameters from Rosenfeld et al. used for the model

## Analysis recipe

1. **Build model image library**: RADMC-3D 13CO 2-1 radiative transfer of azimuthally symmetric Keplerian disks, grid in Mgas, Rc, gamma  
  > "We then calculate the $^{13}$CO 2–1 line emission using the radiative transfer code RADMC-3D." (2.1 Description of the model)
   - software: RADMC-3D
   - parameter: CO freeze-out 20 K; dissociation N_H2 > 1.3e21 cm^-2; 12CO/H2 = 1e-4; 12CO/13CO = 70  
  > "isotopologue ratio, \[$^{12}$CO\]/\[$^{13}$CO\]=70." (2.1 Description of the model)
   - assumption: Hydrostatic equilibrium, Keplerian rotation, azimuthal symmetry  
  > "The gas is assumed to be azimuthally symmetric, in hydrostatic equilibrium and under Keplerian rotation." (2.1 Description of the model)
   - fitting: _not stated_
   - validation: LTE vs NLTE differ by <1 mJy km/s per pixel  
  > "we compared models with LTE and NLTE excitation and found no substantial difference ($<1$ mJy ${\rm km~s^{-1}}$ pixel$^{-1}$)." (2.1 Description of the model)
2. **Fit HD 163296 zero-moment map with MCMC**: Linear interpolation of image library over parameters, MCMC with flat priors  
  > "The MCMC modeling was run with a flat prior for each parameter over the range shown in Table [1](#tab:HD163296_grid) using the `emcee` software package" (2.3 Parameter estimation)
   - software: emcee
   - fitting: emcee, flat priors over grid range; median and 68% intervals  
  > "from which we calculate median and 68% ($\pm 1\sigma$) confidence intervals" (2.3 Parameter estimation)
   - validation: Interpolated images within 3% of full radiative transfer  
  > "we found that interpolated images averaged within 3% of a full radiative transfer calculation." (2.2 Image interpolation)
3. **Test with C18O**: Rerun RADMC-3D with median parameters, vary only CO/C18O abundance by least squares to the zero-moment map  
  > "only varied the \[CO\]/\[C$^{18}$O\] abundance to minimize the least squares difference with the zero-moment map." (2.4 Comparison with the C18O image)
   - software: RADMC-3D
   - fitting: least squares on abundance  
  > "only varied the \[CO\]/\[C$^{18}$O\] abundance to minimize the least squares difference with the zero-moment map." (Comparison with the C$^{18}$O image)
   - validation: Peak residuals about 10% of image maximum  
  > "The fit is very good with peak residuals at about 10% of the image maximum." (2.4 Comparison with the C18O image)
4. **Simulate T Tauri observations and assess recoverability**: Convolve grid images with 0.1-0.4 arcsec beams, add noise 1-30 mJy/beam km/s, KS test against elliptical gaussian fit, then fit with scipy.optimize and compare to inputs  
  > "find the best fit to a given simulated image using the python `scipy.optimize` routine." (3.3 Accuracy of parameter estimation)
   - software: scipy.optimize
   - parameter: 150 pc, 5 au pixels, Mstar 0.5 Msun  
  > "for a distance of 150 pc and a pixel scale of 5 au ($0.03\ensuremath{''}$)." (3.1 Description)
   - fitting: scipy.optimize best fit, no errors estimated  
  > "We do not estimate errors in this case" (3.3 Accuracy of parameter estimation)
   - validation: Histograms of fitted minus input parameters  
  > "plots histograms of the difference between the input and fitted parameters for all disks with mass $M_{\rm gas}=10^{-2}\,M_\odot$" (Accuracy of parameter estimation)

## Software

- **RADMC-3D** : 13CO and C18O 2-1 radiative transfer  
  > "We then calculate the $^{13}$CO 2–1 line emission using the radiative transfer code RADMC-3D." (2.1 Description of the model)
- **emcee** : MCMC parameter estimation  
  > "using the `emcee` software package" (2.3 Parameter estimation)
- **scipy.optimize** : best-fit of simulated images  
  > "using the python `scipy.optimize` routine" (3.3 Accuracy of parameter estimation)
- **Astropy** : Python astronomy tools acknowledged  
  > "We thank the community developers of the Python packages for Astronomy in Astropy" (Acknowledgments)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| HD 163296 gas mass | 0.048 | +0.003/-0.003 | Msun | 2 | $M_{\rm gas}=0.048^{+0.003}_{-0.003}\,M_\odot, |
| Characteristic radius Rc | 213 | +7/-7 | au | 2 | R_c=213^{+7}_{-7}\,{\rm AU}, |
| Gradient gamma | 0.39 | +0.09/-0.08 | dimensionless | 2 | \gamma=0.39^{+0.09}_{-0.08}$. |
| [CO]/[C18O] abundance ratio | 700 | not stated | dimensionless | 3 | The inferred abundance ratio is \[CO\]/\[C$^{18}$O\]=700 |
| Residual standard deviation | 27 | not stated | mJy km/s | 2 | consistent with a gaussian with standard deviation 27 mJy ${\rm km~s^{-1}}$ |

## Qualitative findings

- Fits to 12CO 3-2 by earlier work give higher central densities, steeper profiles and smaller outer radii than the 13CO fit  
  > "Both find higher central densities, steeper profiles, and smaller outer disk radii than our fits to $^{13}$CO." (2.3 Parameter estimation)

## Claim tuples

- H: Gas surface density profile parameters can be fit from a 13CO zero-moment map | E: MCMC fit of image library to HD 163296 ALMA SV data | R: Mgas=0.048 Msun, Rc=213 au, gamma=0.39 with a good fit | F: The method works for a bright disk | **supported**
- H: The same parameters reproduce the C18O image | E: Vary only the CO/C18O ratio | R: Ratio 700, no obvious systematics | F: Abundance is not strongly radius dependent | **supported**
- H: Profiles of T Tauri disks can be measured economically | E: Fit simulated 13CO images across beams and noise levels | R: Rc within about 10 au and gamma within about 0.2 at 0.2-0.3 arcsec | F: Surveys are feasible with ~20 minute integrations | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: MCMC is too slow with direct radiative transfer, so images are interpolated; zero-moment maps suffice because Keplerian rotation separates regions  
  > "we found that it is not necessary to make tomographic comparisons of channel maps to discriminate between models and that velocity integrated (zero-moment) maps suffice." (2.1 Description of the model)
- How they decided it was enough: _not stated_
- Limitation (authors): Small errors reflect the rigid imposed temperature structure; allowing it to vary would increase errors  
  > "The apparently high precision obtained here reflects the rigidity of the temperature structure imposed in our models" (2.3 Parameter estimation)
- Caveat (inferred, ours): Temperature structure, inclination and stellar mass are fixed, so errors are underestimated
- Caveat (inferred, ours): Fit differs from 12CO-based profiles
- Caveat (inferred, ours): CO abundance assumed constant at 1e-4
- Caveat (inferred, ours): Simulated survey uses idealized noise and circular beams, not uv-plane noise

## Reproducibility

- Data public (paper): Public SV data  
  > "early ALMA observations of $^{13}$CO and other lines are publicly available through its Science Verification program" (The HD 163296 disk)
- Products in archive: _not stated_
- Missing: Moment-map construction and noise
- Missing: Temperature structure parameters
- Missing: MCMC configuration
- Missing: Library and code not released
- Data volume (inferred): ~ a few GB (single SV dataset)
- Score (inferred): 3/5, Model and grid are described but the data reduction and fit details are missing and no code is released.
- Rediscovery candidate: no, Data are public, but the moment map construction, temperature model and MCMC setup are not fully specified.

## Links

- Method: (cite: 2014ApJ...788...59W) (Original modeling methodology (Paper I))
- Companion: (cite: 2016arXiv160405719A) (ALMA Lupus gas mass survey)
- Related: ALMA Science Verification HD 163296
- Related: ALMA Lupus survey

## Checks

```json
{
 "quotes": 42,
 "quotes_ok": 42,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 68,
  "stated": 29,
  "rate": 0.426
 },
 "evidence_ok": true
}
```
