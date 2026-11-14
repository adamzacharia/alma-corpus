# Measurement of the Black Hole Mass in NGC 1332 from ALMA Observations at 0.044 arcsecond Resolution

`2016ApJ...822L..28B` | The Astrophysical Journal Letters 2016 | first author: Barth, Aaron J. | arXiv: 1605.01346 | DOI: 10.3847/2041-8205/822/2/L28

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, agn_and_quasars
- Question: What is the mass of the central black hole in NGC 1332, measured from CO(2-1) gas kinematics that resolve the BH's gravitational radius of influence?  
  > "fit the beam-smeared model line profiles directly to the ALMA data cube." (abstract)
- Target **NGC 1332**: coordinates _not stated_; z/distance 22.3 Mpc (1'' = 108.6 pc)  
  > "We adopt a distance of 22.3 Mpc to NGC 1332 for consistency with Paper I and with (cite: rusli2011); at this distance, 1$''$ corresponds to 108.6 pc." (1 Introduction); distance from adopted for consistency with Paper I and Rusli et al. 2011  
  > "We adopt a distance of 22.3 Mpc to NGC 1332 for consistency with Paper I and with (cite: rusli2011); at this distance, 1$''$ corresponds to 108.6 pc." (1 Introduction)

## Data provenance

- ALMA projects: 2015.1.00896.S
- bands: Band 6  
  > "NGC 1332 was observed in ALMA Band 6 as part of project 2015.1.00896.S." (2 Observations)
- frequencies and spectral setup: band centered at 229.354 GHz; 75 channels of 15.4 MHz (20.1 km/s)  
  > "The observations were obtained in a frequency band centered at 229.354 GHz, corresponding to the redshifted $^{12}$CO(2–1) line in NGC 1332." (2 Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: beam 0.052'' x 0.037'', PA 64 deg; geometric mean 0.044''  
  > "The synthesized beam has major and minor axis FWHM sizes of 0.052$''$ and 0.037$''$ with major axis position angle (PA) 64$^\circ$" (2 Observations)
- max recoverable scale: _not stated_
- sensitivity: rms 0.142 mJy/beam per channel at 0.04'' binned pixels  
  > "the rms noise level is 0.142 mJy beam $^{-1}$ per channel" (2 Observations)
- time on source: 101 min on source  
  > "for a total on-source integration time of 101 min" (2 Observations)
- observing dates: 2015 September 16 and 23  
  > "Three separate observations on 2015 September 16 and 23 were carried out" (2 Observations)
- pi or archival as stated: _not stated_
- Line: 12CO J=2-1 (not stated)
- External data: Deprojected stellar luminosity profile (K-band VLT AO plus R-band)  
  > "we use the deprojected stellar luminosity profile from (cite: rusli2011), based on a combination of $K$-band VLT adaptive-optics data at small radii" (3 Dynamical Modeling) [from Rusli et al. 2011 (cite: rusli2011)]
- External data: R-band mass-to-light ratio 7.35 from best-fitting stellar-dynamical model (private communication)  
  > "Their best-fitting stellar-dynamical model implies an $R$-band mass-to-light ratio of $\Upsilon_R=7.35$ (J. Thomas, private communication)." (3 Dynamical Modeling) [from Rusli et al. 2011 (cite: rusli2011)]

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

- task: CASA; cube with 0.01'' pixels, 6.4'' x 6.4'' FOV, 75 channels  
  > "to produce an emission-line data cube with $0.01\ensuremath{''}$ pixels, a field of view of $6.4\ensuremath{''}\times6.4\ensuremath{''}$, and 75 frequency channels" (2 Observations)
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
- smoothing: spatial block averaging 4x4 pixels to 0.04'' pixels  
  > "we first binned the data cube spatially by block averaging in $4\times4$ pixel blocks, producing 0.04$''$ pixels" (2 Observations)
- final beam: 0.052'' x 0.037'' at PA 64 deg  
  > "major and minor axis FWHM sizes of 0.052$''$ and 0.037$''$" (2 Observations)
- final rms: 0.142 mJy/beam per channel (0.04'' pixels)  
  > "the rms noise level is 0.142 mJy beam $^{-1}$ per channel" (2 Observations)

### Inherited from earlier work

- Dynamical modeling methods follow Paper I (thin-disk model, chi2 at ~1 pixel per beam, stellar mass profile)  
  > "Our dynamical modeling follows the methods described in Paper I." (3 Dynamical Modeling) [from Paper I (cite: barth2016)]
- Stellar mass M*(r) profile plot and neglect of dark matter/gas masses  
  > "(cite: rusli2011) give full details of the $L_\star(r)$ measurement, and Paper I presents a plot of $M_\star(r)$." (3 Dynamical Modeling) [from Rusli et al. 2011; Paper I]

### Not stated but needed to reproduce (our reading)

- CASA version and calibration/imaging details (weighting, robust, cleaning, continuum subtraction)
- Array configurations, baselines and calibrators
- Spectral window and channel selection used for chi2 (56 of 75 channels)
- How CO surface brightness map was made
- Coordinates of the dynamical center and the target
- IDL fitting code not released; amoeba convergence settings
- Stellar luminosity profile table not provided

## Analysis recipe

1. **Make and bin the CO(2-1) cube**: Process in CASA to cube with 0.01'' pixels, then block-average 4x4 to 0.04'' pixels  
  > "we first binned the data cube spatially by block averaging in $4\times4$ pixel blocks, producing 0.04$''$ pixels" (2 Observations)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Kinematic maps**: Gaussian line-profile fits to binned cube for intensity, v_LOS, sigma_LOS  
  > "We created kinematic maps by fitting Gaussian line profiles to the data." (2 Observations)
   - fitting: _not stated_
   - validation: _not stated_
3. **Thin-disk dynamical model fit to cube**: Model circular-rotation disk in potential of BH plus stars, Gaussian profiles with turbulent dispersion, scaled to CO surface brightness, convolved with beam, rebinned to 0.04'', chi2 compared to data cube  
  > "The goodness of fit (quantified by $\chi^2$) is computed by direct comparison of the model cube with the binned ALMA data." (3 Dynamical Modeling)
   - software: IDL amoeba
   - parameter: Free parameters: M_BH, Upsilon, sigma_turb, i, Gamma, v_sys, (x0,y0), f0  
  > "Free parameters include $M_\mathrm{BH}$, $\Upsilon$, $\sigma_\mathrm{turb}$, $i$, $\Gamma$, $\ensuremath{v_\mathrm{sys}}$, the dynamical center position $(x_0,y_0)$, and an overall normalization factor $f_0$" (3 Dynamical Modeling)
   - assumption: Uniform sigma_turb; dark matter and molecular gas mass neglected; distance 22.3 Mpc  
  > "We neglect the contributions of dark matter and of molecular gas, both of which are $\lesssim10^8$ ${M}_{\odot}$ within $r=250$ pc" (3 Dynamical Modeling)
   - fitting: chi2 minimization with amoeba downhill simplex; confidence from delta chi2  
  > "We optimize the model fits using the `amoeba` downhill simplex method in IDL." (3 Dynamical Modeling)
   - validation: reduced chi2 checks; fits to varying r_fit  
  > "The expected range on $\chi^2_{\nu}$ for 2515 degrees of freedom is $1.00\pm0.03$, so this result suggests that there is still a mild degree of systematic model-data mismatch within $\ensuremath{r_\mathrm{fit}}=50$ pc." (Modeling Results, Fits to smaller regions)
4. **Fit smaller central regions to limit stellar-profile systematics**: Fit within elliptical regions of semimajor axis r_fit; for r_fit=50 pc fix x0, y0, v_sys at best-fit values and grid in M_BH with five other parameters free  
  > "we take the values of these three parameters and hold them fixed, calculating a grid of models with $\ensuremath{r_\mathrm{fit}}=50$ pc for a range of values of $M_\mathrm{BH}$ with the remaining five parameters free." (4.2 Fits to smaller regions)
   - software: IDL amoeba
   - parameter: r_fit = 50 pc, 45 spatial pixels, 2515 dof  
  > "These constrained fits for $\ensuremath{r_\mathrm{fit}}=50$ pc (containing 45 spatial pixels) have 2515 degrees of freedom" (4.2 Fits to smaller regions)
   - fitting: 68.3% and 99% confidence from chi2 vs M_BH  
  > "The 68.3% and 99% confidence ranges on $M_\mathrm{BH}$ are $(6.64_{-0.63}^{+0.65})\times10^8$ and $(6.64_{-1.66}^{+1.69})\times10^8$ ${M}_{\odot}$, respectively." (Modeling Results, Fits to smaller regions)
   - validation: Smooth chi2 curve required; compared with Rusli stellar-dynamical and Humphrey X-ray masses  
  > "Our goal is to fit models over the smallest possible spatial region that permits successful fits with well-defined confidence limits on $M_\mathrm{BH}$ (manifested by a smooth and regular curve of $\chi^2$ vs. $M_\mathrm{BH}$)." (Modeling Results, Fits to smaller regions)

## Software

- **CASA** : Producing the emission-line data cube  
  > "We processed the data using the Common Astronomy Software Applications (cite: mcmullin2007) package" (2 Observations)
- **IDL amoeba** : Downhill simplex optimization of model fits  
  > "We optimize the model fits using the `amoeba` downhill simplex method in IDL." (3 Dynamical Modeling)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| M_BH (r_fit=50 pc, 68.3%) | 6.64e8 | +0.65/-0.63 e8 | Msun | 4 | we find $\ensuremath{M_\mathrm{BH}}=(6.64_{-0.63}^{+0.65})\times10^8$ ${M}_{\odot}$ |
| M_BH (full disk fit) | 6.86e8 | ±0.14e8 (68.3%) | Msun | 3 | The 68.3% confidence region (corresponding to $\Delta\ensuremath{\chi^2}=1$) is $(6.86\pm0.14)\times10^8$ ${M}_{\odot}$. |
| Reduced chi2, r_fit=50 pc | 1.09 | not stated | dimensionless | 4 | the best-fitting model has $\ensuremath{\chi^2}=2739.8$ and $\ensuremath{\chi^2_{\nu}}=1.09$ |
| sigma_turb (r_fit=50 pc) | 32.1 | not stated | km/s | 4 | $\ensuremath{\sigma_\mathrm{turb}}=32.1$ km s$^{-1}$ |
| Gravitational radius of influence | 25 pc (0.23'') | not stated | pc | 4 | This model implies $\ensuremath{r_\mathrm{g}}= 25$ pc or 0.23$''$ |

## Qualitative findings

- Disk shows regular rotation with central high-velocity emission to ~500 km/s; no high central sigma_turb required.  
  > "This demonstrates that the Cycle 3 data do not require or prefer a high central $\sigma_\mathrm{turb}$." (4.3 Turbulent velocity dispersion)

## Claim tuples

- H: Can ALMA CO kinematics resolving r_g give a robust M_BH for NGC 1332? | E: Beam-smeared thin-disk model fits to the cube within r_fit=50 pc | R: M_BH=6.64e8 Msun, zero mass rejected at >99.99% | F: ALMA can measure BH masses by resolving r_g | **supported**
- H: Is the stellar-dynamical M_BH of 1.45e9 consistent with CO kinematics? | E: Delta chi2 of constrained fits at that mass | R: Delta chi2=101 at 1.45e9 | F: Highly inconsistent; factor-two disagreement | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Smaller-region fits reduce sensitivity to stellar mass profile shape and warp  
  > "This makes the model-fitting results less susceptible to errors due to the shape of the stellar mass profile" (4.2 Fits to smaller regions)
- How they decided it was enough: _not stated_
- Limitation (authors): Mild systematic model-data mismatch; distance uncertainty not in error budget; S/N limiting; minor-axis kinematics unresolved by factor of two  
  > "The error budget does not incorporate uncertainty in the distance to NGC 1332" (4.2 Fits to smaller regions)
- Caveat (inferred, ours): Uniform sigma_turb and flat-disk assumptions with a known warp
- Caveat (inferred, ours): Choice of r_fit=50 pc and fixing x0,y0,v_sys is somewhat ad hoc
- Caveat (inferred, ours): Stellar M/L and profile taken from literature without uncertainty

## Reproducibility

- Data public (paper): ALMA program 2015.1.00896.S cited; public status not stated  
  > "This paper makes use of data from ALMA program 2015.1.00896.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Custom IDL model code
- Missing: Stellar luminosity profile table
- Missing: CASA reduction parameters
- Missing: CO surface brightness model details
- Data volume (inferred): ~50-100 GB raw for 3 execution blocks
- Score (inferred): 3/5, Data public in archive, approach clear but model code and imaging details missing and inherited from Paper I.
- Rediscovery candidate: no, Custom model and external stellar profile/M-L needed; imaging details unstated.

## Links

- Method: Barth et al. 2016 (Paper I) (cite: barth2016) (Modeling methods followed)
- Companion: Rusli et al. 2011 (Stellar-dynamical M_BH and stellar profile)

## Checks

```json
{
 "quotes": 44,
 "quotes_ok": 44,
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
  "facts": 66,
  "stated": 34,
  "rate": 0.515
 },
 "evidence_ok": true
}
```
