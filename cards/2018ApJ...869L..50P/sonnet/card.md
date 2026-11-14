# The Disk Substructures at High Angular Resolution Project (DSHARP). X. Multiple Rings, a Misaligned Inner Disk, and a Bright Arc in the Disk around the T Tauri star HD 143006

`2018ApJ...869L..50P` | The Astrophysical Journal Letters 2018 | first author: Pérez, Laura M. | arXiv: 1812.04049 | DOI: 10.3847/2041-8213/aaf745

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks
- Question: What substructures (rings, gaps, arc, inner-disk depletion, misalignment) are present in the HD 143006 disk in 1.25 mm continuum and 12CO, and how do they compare with VLT/SPHERE scattered light?  
  > "We compare the observed substructures in the ALMA observations with recent scattered light data from VLT/SPHERE of this object." (abstract)
- Target **HD 143006**: coordinates RA 15h58m36.90s, Dec -22d57m15.603s (J2000, phase center)  
  > "Observations were centered to R.A. (J2000) = 15h 58m 36.90s, Dec (J2000) = $-22$d 57m 15.603s" (Observations); "located in Upper Sco at a distance of $165\pm5$ pc (cite: Gaia2018)" (Introduction); z/distance 165±5 pc  
  > "Observations were centered to R.A. (J2000) = 15h 58m 36.90s, Dec (J2000) = $-22$d 57m 15.603s" (Observations); "located in Upper Sco at a distance of $165\pm5$ pc (cite: Gaia2018)" (Introduction); distance from Gaia (Gaia Collaboration 2018)  
  > "Observations were centered to R.A. (J2000) = 15h 58m 36.90s, Dec (J2000) = $-22$d 57m 15.603s" (Observations); "located in Upper Sco at a distance of $165\pm5$ pc (cite: Gaia2018)" (Introduction)

## Data provenance

- ALMA projects: 2016.1.00484.L, 2015.1.00964.S
- bands: 1.25 mm continuum and 12CO J=2-1  
  > "Dust continuum emission at 1.25 mm and $^{12}$CO emission in the $J=2-1$ transition were observed" (Observations)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: long and short baselines, plus additional short baselines from 2015.1.00964.S  
  > "were combined to increase uv-coverage on the short-spacings" (Observations)
- baselines: _not stated_
- angular resolution: 46x45 mas continuum beam; 66x49 mas CO beam  
  > "for a $46\times 45$ mas beam with position angle (PA) of $52.1\degree$" (Observations)
- max recoverable scale: _not stated_
- sensitivity: continuum rms 14.3 uJy/beam; CO rms 1.04 mJy/beam km/s at 0.32 km/s channels  
  > "The RMS noise in the continuum image is 14.3 $\mu$Jy beam$^{-1}$" (Observations)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: 12CO J=2-1 (not stated)
- Other facility **VLT/SPHERE**: polarized scattered light image used for comparison  
  > "the polarized scattered light coronagraphic image of HD 143006 obtained with VLT/SPHERE" (4.2 Substructures seen in scattered light)
- External data: SPHERE scattered-light image and shadow analysis  
  > "Recent scattered light observations of HD 143006 show multiple brightness asymmetries" (Introduction) [from (cite: benisty2018)]
- External data: Midplane temperature profile and optically thin continuum  
  > "From the midplane temperature profile ($T_{mid}$) assumed in (cite: rings)" (4.1 Substructures in the ALMA images) [from (cite: rings)]

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
- weighting robust: CO: robust = 0.8; continuum uses parameters of Table 4 of DSHARP survey paper  
  > "the CO images were obtained using a robust parameter of 0.8 with a uv-tapering of $20\;$mas" (Observations)
- uv taper: 20 mas (CO)  
  > "with a uv-tapering of $20\;$mas" (Observations)
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 46x45 mas PA 52.1 deg (continuum); 66x49 mas PA 83.6 deg (CO)  
  > "for a beam size of $66\times49$ mas, PA of $83.6\degree$" (Observations)
- final rms: 14.3 uJy/beam (continuum); 1.04 mJy/beam km/s (CO)  
  > "we measure an RMS noise of 1.04 mJy beam$^{-1}$ km s$^{-1}$" (Observations)

### Inherited from earlier work

- Calibration of visibilities  
  > "Details on the calibration of visibilities can be found in (cite: survey)." (Observations) [from (cite: survey) Andrews et al. 2018]
- Continuum imaging parameters  
  > "The continuum images presented here used the same imaging parameters as listed in Table 4 of (cite: survey)" (Observations) [from (cite: survey) Table 4]
- Ring/gap labeling convention  
  > "we follow the convention of (cite: rings) and label the dark/bright annular features" (3.1 Dust Continuum Emission) [from (cite: rings)]

### Not stated but needed to reproduce (our reading)

- Imaging parameters for continuum (in survey paper Table 4)
- Calibration details, CASA version and self-calibration
- Exact continuum model initial conditions and any visibility weighting/averaging
- How moment 1 map was made (clipping, tool)
- Stellar mass origin of 1.8 Msun
- Details of the min2017 scattering surface calculation

## Analysis recipe

1. **Image continuum and CO**: Imaging with DSHARP parameters; CO with robust 0.8 and 20 mas taper  
  > "the CO images were obtained using a robust parameter of 0.8 with a uv-tapering of $20\;$mas" (Observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **Fit Keplerian velocity field to CO moment 1**: Razor-thin Keplerian disk model around 1.8 Msun star, convolved with beam, compared pixel by pixel to moment 1  
  > "using an analytical model of a razor-thin disk in Keplerian motion around a 1.8 M$_{\odot}$ star" (3.3 Modeling CO kinematics)
   - software: emcee
   - parameter: Free: i, PA, vsys, x0, y0; inner/outer radius fixed 0.3 and 250 au  
  > "We fix the inner and outer radius of the disk to 0.3 and 250 au, respectively." (3.3 Modeling CO kinematics)
   - assumption: Stellar mass 1.8 Msun; distance 165 pc  
  > "Keplerian motion around a 1.8 M$_{\odot}$ star" (3.3 Modeling CO kinematics)
   - fitting: emcee, 80 walkers, 4000 steps, last 2000 used; uniform priors i [0,90], PA [0,360], vsys [5,10] km/s, x0,y0 [-0.2,0.2]"; median and 16/84 percentiles  
  > "The parameter space is explored with 80 walkers and for 4000 steps." (3.3 Modeling CO kinematics)
   - validation: Residual map; separate fits masking inside/outside 0.15"  
  > "by masking the velocity field in Figure [3](#fig:mom1) inside and outside of $0.15''$" (3.3 Modeling CO kinematics)
3. **Fit continuum visibilities with ring and arc models**: Three radial Gaussian rings plus a 2D Gaussian arc; B40, B64, arc share geometry, B8 separate; 22 free parameters; model Fourier-transformed and sampled at observed uv  
  > "This results in a total of 22 free parameters that are constrained with over $34$ million visibilities." (3.4 Modeling of continuum emission)
   - software: Galario, emcee
   - assumption: Arc follows steady-state vortex prescription (Lyra & Lin 2013)  
  > "The model adopted for the arc corresponds to the distribution of material in a steady-state vortex (cite: Lyra)." (3.4 Modeling of continuum emission)
   - fitting: emcee, 120 walkers, 25000 steps, posterior from last 15000; median and 16/84 percentiles; priors not stated  
  > "we use the MCMC sampler $emcee$ (cite: emcee) with 120 walkers that we ran for 25000 steps." (3.4 Modeling of continuum emission)
   - validation: Autocorrelation time under 3000 iterations; residual images; largest residual ±9 sigma  
  > "Convergence was checked by measuring the autocorrelation time, which was under 3000 iterations." (3.4 Modeling of continuum emission)
4. **Estimate inner/outer disk misalignment and compare with SPHERE shadows**: Angle between disk normals from fitted i and PA for two near-side configurations; scattering surface height from Min et al. 2017 equations compared with Hp/R  
  > "Using the equations developed in (cite: min2017), we find a $z_{\rm{scat}}/R$ of $\sim$0.03 and $\sim$0.16 at $\sim$18 au" (4.3 A misalignment between inner and outer disk)
   - assumption: Hp smaller than scattering surface by factor ~2-4; Hp/R~0.04 at 18 au from standard temperature profile of Huang et al.  
  > "we estimate that at 18 au $H_p/R\sim0.04$" (4.3 A misalignment between inner and outer disk)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **emcee** : MCMC sampling for CO kinematics and continuum model fits  
  > "We perform our fit using an affine invariant MCMC sampler (cite: emcee)" (3.3 Modeling CO kinematics)
- **Galario** : Fourier transform of model images and sampling at observed uv points  
  > "for this we use the publicly available code Galario (cite: Galario)" (3.4 Modeling of continuum emission)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Continuum rms | 14.3 | not stated | uJy/beam | 1 | The RMS noise in the continuum image is 14.3 $\mu$Jy beam$^{-1}$ |
| Global CO Keplerian fit inclination | 16.2 | ±0.3 | deg | 2 | $16.2\degree\pm0.3\degree$ |
| Inner disk inclination from CO (r<0.15") | 22.84 | ±0.05 | deg | 2 | we find $i = 22.84\degree \pm 0.05\degree$ and PA $= 165.6\degree\pm0.1\degree$ for the inner disk |
| Outer disk inclination from CO | 14.59 | ±0.02 | deg | 2 | an inclination of $14.59\degree\pm0.02\degree$ |
| Systemic velocity | 7.71 | ±0.02 | km/s | 2 | $7.71\pm0.02$ |
| Continuum inner disk (B8) inclination | 24.1 | ±1.0 | deg | 3 | $24.1\pm1.0$ |
| Continuum outer disk inclination | 17.02 | ±0.14 | deg | 3 | $17.02\pm0.14$ |
| Ring radii B8, B40, B64, arc | 7.67, 39.95, 63.6, 74.2 | ±0.04, 0.03, 0.1, 0.1 | au | 3 | $7.67\pm0.04$ |
| Misalignment angle (same near side / opposite near side) | 8 / 41 | not stated | deg | 4 | we find a small misalignment of 8$^\circ$. |

## Qualitative findings

- CO emission is not centrally peaked, indicating gas depletion inside ~15 au  
  > "meaning that there is some depletion of the CO column density inside of $\sim$15 au ($\sim90$ mas)" (4.1 Substructures in the ALMA images)

## Claim tuples

- H: Does the inner disk have a different geometry from the outer disk? | E: Keplerian fits to CO moment 1 and visibility modeling of continuum rings | R: Inner disk i ~24 deg, PA 164 deg vs outer i ~17 deg, PA 176 deg; CO residuals inside 0.15" | F: Inner and outer disk are misaligned (8 or 41 deg) | **supported**
- H: Which misalignment value is correct? | E: Compare scattering surface height from shadow locations with estimated Hp/R | R: Hp/R~0.04 exceeds limit 0.015 for 7 deg but is below 0.08 for 41 deg | F: Large misalignment of ~41 deg favored | **partially**
- H: Could the SE arc be a dust-trapping vortex? | E: Gaussian arc model and comparison with SPHERE | R: Arc ~5 by 21 au, resolved into three peaks; broader scattered-light counterpart | F: Consistent with a vortex, possibly second generation; to be tested at longer wavelengths | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Photoevaporation for the depleted inner disk judged less likely due to moderate accretion and dust-rich inner disk  
  > "A possible origin for the depleted inner disk is photoevaporation, however, the star is accreting at a moderate rate" (4.1 Substructures in the ALMA images)
- How they decided it was enough: _not stated_
- Limitation (authors): Near/far side of inner and outer disks cannot be determined from continuum alone; low CO SNR  
  > "which cannot be determined with the continuum data alone" (4.3 A misalignment between inner and outer disk)
- Limitation (authors): 2D-Gaussian arc model cannot describe multiple peaks  
  > "the 2D-Gaussian prescription cannot properly describe the multiple peaks observed along the arc" (3.4 Modeling of continuum emission)
- Caveat (inferred, ours): Priors for continuum model not given
- Caveat (inferred, ours): Razor-thin Keplerian fit to moment 1 of a low-SNR cube is sensitive to moment map construction
- Caveat (inferred, ours): Quoted tiny CO uncertainties are statistical only
- Caveat (inferred, ours): Misalignment choice depends on assumed temperature profile and the scattering-surface approximations

## Reproducibility

- Data public (paper): Large Program and archival project codes given  
  > "observed with long and short baselines in the ALMA Large Program 2016.1.00484.L" (Observations)
- Products in archive: _not stated_
- Missing: Survey paper imaging parameters and calibration
- Missing: Continuum model priors and initial values
- Missing: Moment map generation details
- Data volume (inferred): Large: DSHARP long baseline plus short baseline continuum and CO; several hundred GB raw
- Score (inferred): 3/5, Data public and fits well specified but calibration/imaging defer to survey paper and priors/moment-map details missing.
- Rediscovery candidate: yes, Public data, numeric model fits with stated sampler setups, though inherited imaging details are needed.

## Links

- Method: (cite: survey) Andrews et al. 2018 (DSHARP calibration and imaging)
- Method: (cite: Galario) Tazzari et al. 2018 (visibility modeling code)
- Method: (cite: min2017) (scattering surface and shadow equations)
- Companion: (cite: rings) Huang et al. 2018 (DSHARP ring and gap characterization and temperature profile)
- Companion: (cite: benisty2018) (SPHERE observations and misalignment modeling of HD 143006)
- Companion: (cite: Shangjia2018) Zhang et al. 2018 (planet mass constraints from gaps)
- Related: DSHARP

## Checks

```json
{
 "quotes": 56,
 "quotes_ok": 56,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 9,
 "numeric_problems": 0,
 "fill": {
  "facts": 71,
  "stated": 37,
  "rate": 0.521
 },
 "evidence_ok": true
}
```
