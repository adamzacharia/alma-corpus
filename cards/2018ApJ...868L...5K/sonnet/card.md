# A Spatially Resolved au-scale Inner Disk around DM Tau

`2018ApJ...868L...5K` | The Astrophysical Journal Letters 2018 | first author: Kudo, Tomoyuki | arXiv: 1810.13148 | DOI: 10.3847/2041-8213/aaeb1c

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks
- Question: Does the DM Tau transitional disk have a dust-free inner cavity of a few au, as inferred from SED modeling, and what is the fine radial and azimuthal structure of its dust and CO emission?  
  > "Previous submillimeter observations were, however, unable to detect the cavity; instead, a dust ring $\sim$20 au in radius was seen." (abstract)
- Target **DM Tau**: coordinates 04:33:48.749 +18:10:09.64 (ICRS, outer ring center from ellipse fit)  
  > "distance: 145 pc; (cite: gaia18)" (Introduction); "| 04:33:48.749 \[0.001\] | +18:10:09.64 \[0.01\] |" (Table 1); z/distance 145 pc  
  > "distance: 145 pc; (cite: gaia18)" (Introduction); "| 04:33:48.749 \[0.001\] | +18:10:09.64 \[0.01\] |" (Table 1); distance from Gaia Collaboration 2018  
  > "distance: 145 pc; (cite: gaia18)" (Introduction); "| 04:33:48.749 \[0.001\] | +18:10:09.64 \[0.01\] |" (Table 1)

## Data provenance

- ALMA projects: 2017.1.01460.S, 2013.1.00198.S, 2013.1.00498.S
- bands: Band 6 (1.3 mm)  
  > "DM Tau was observed with ALMA in band 6 in the C43–9 configuration on October 27, 2017" (Observations)
- frequencies and spectral setup: Five SPWs: 13CO 220.39868 GHz, C18O 219.56035 GHz, 12CO 230.53800 GHz (117 MHz each), two continuum windows of 2.0 GHz  
  > "and the last two windows for continuum observations with bandwidth 2.0 GHz" (Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: C43-9  
  > "in the C43–9 configuration on October 27, 2017, UT" (Observations)
- baselines: 135.1 m to 14.9 km, 47 antennas  
  > "utilizing 47 antennas with the baseline length extending from 135.1 m to 14.9 km" (Observations)
- angular resolution: 43x31 mas  
  > "The excellent angular resolution achieved in the new ALMA observations, 43$\times$31 mas" (abstract)
- max recoverable scale: _not stated_
- sensitivity: 11 uJy/beam continuum RMS (Briggs 2.0)  
  > "providing RMS noise levels of 11 $\mu$Jy beam$^{-1}$" (Observations)
- time on source: 66.1 min  
  > "The total on-source integration time was 66.1 min." (Observations)
- observing dates: October 27, 2017  
  > "in the C43–9 configuration on October 27, 2017, UT" (Observations)
- pi or archival as stated: _not stated_
- Line: 12CO J=2-1 (230.53800 GHz)
- Line: 13CO J=2-1 (220.39868 GHz)
- Line: C18O J=2-1 (219.56035 GHz)
- External data: Archival short-baseline ALMA dataset combined to recover missing flux  
  > "We combined our data with another ALMA dataset (cite: pini18) to recover the missing flux" (Observations) [from Pinilla et al. 2018 (cite: pini18)]
- External data: 3.4 cm flux density used to estimate free-free contamination  
  > "determined by extrapolating the flux density measured at 3.4 cm (cite: zapa17) to 1.3 mm" (Results) [from (cite: zapa17)]
- External data: Single-dish total flux ~110 mJy  
  > "($\sim$70 mJy out of a total of $\sim$110 mJy; (cite: beck90))" (Observations) [from (cite: beck90)]

## Processing

### Calibration

- pipeline or manual: CASA following ALMA-provided calibration scripts  
  > "following the calibration scripts provided by ALMA" (Observations)
- casa version: CASA 5.1.1  
  > "package (cite: mcmu07) version 5.1.1" (Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: 10% assumed absolute flux calibration uncertainty  
  > "assuming a 10 % uncertainty in absolute flux calibration" (Observations)
- self calibration: Not performed; >50% of long-baseline data flagged in tests; 13% attenuation estimated from check source  
  > "Therefore, we decided not performing self-calibration." (Observations); "This corresponds to a 13% attenuation" (Observations)

### Imaging

- task: CASA CLEAN with multi-scale multi-frequency deconvolution  
  > "CASA with the `CLEAN` task using a multi-scale multi-frequency deconvolution algorithm (cite: rau11)" (Observations)
- deconvolver: _not stated_
- weighting robust: Briggs 2.0  
  > "synthesized with a Briggs weighting of 2.0 to maximize the signal-to-noise (S/N) ratio" (Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: uvcontsub in visibility space  
  > "by subtracting the continuum in the visibility space with `uvcontsub` in the CASA tools" (Observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: Long baseline combined with archival short-baseline data; phase centers aligned with fixvis  
  > "were shifted by `fixvis` in the CASA tools" (Observations)
- smoothing: 12CO cube smoothed with 75 mas circular Gaussian (imsmooth), 0.5 km/s channels  
  > "spatially smoothed with a circular Gaussian kernel of 75 mas by `imsmooth` in CASA for presentation purposes" (Observations)
- final beam: _not stated_
- final rms: 11 uJy/beam (continuum)  
  > "providing RMS noise levels of 11 $\mu$Jy beam$^{-1}$" (Observations)

### Inherited from earlier work

- Deprojection of continuum in visibility domain  
  > "we deprojected the dust continuum image in the visibility domain following (cite: zhan16)" (Results) [from (cite: zhan16)]
- Disk model: power law with exponential taper  
  > "simple power-law radial profile with an exponential taper at the outside (cite: lynd74; hart98)" (Model fitting) [from (cite: lynd74; hart98)]

### Not stated but needed to reproduce (our reading)

- Image size, cell size, and multiscale scales for CLEAN
- Clean masks and thresholds
- Line-free channels for uvcontsub
- Archival short-baseline data details (project code, calibration) and relative weighting
- Visibility binning/uncertainty treatment and likelihood for MCMC
- Ellipse fitting procedure details
- Moment map clipping thresholds

## Analysis recipe

1. **Combine long and short baseline data and image continuum**: Align phase centers via ellipse isophote fitting and fixvis, check amplitude consistency below 200 klambda, CLEAN with Briggs 2.0  
  > "We compared the amplitudes as a function of $uv$-distance at less than 200 k$\lambda$ between our long baseline data and archival short baseline data, and confirmed their consistency." (Observations)
   - software: CASA
   - fitting: _not stated_
   - validation: Total flux 116.75 mJy consistent with single dish  
  > "consistent with previous single dish observations assuming a 10 % uncertainty in absolute flux calibration" (Observations)
2. **Derive geometry and radial profile**: Ellipse fit to outer ring; deprojection in visibility domain; azimuthal averaging  
  > "The inclination and the position angle of the disk were derived by fitting an ellipse to the outer ring." (Results)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
3. **Inner disk dust mass**: Optically thin flux-to-mass conversion  
  > "a temperature of 100 K, and a gas-to-dust mass ratio of 100, the total mass of the inner disk is measured as 0.04 $M_{\rm Jup}$" (Results)
   - assumption: d=145 pc, kappa=2.3 cm2/g at 230 GHz, T=100 K, gas-to-dust 100  
  > "a dust opacity per gas mass $\kappa_{\nu}=$2.3 cm$^2$ g$^{-1}$ at 230 GHz (cite: beckwith+91)" (Results)
   - fitting: _not stated_
   - validation: Free-free contamination <8% estimated  
  > "The contamination from possible free-free emission is less than 8% (3$\sigma$ level)" (Results)
4. **Visibility-domain model fit of dust profile**: Two-component analytic disk model with gaps, images converted to visibilities with vis_sample, MCMC fit, residual imaging  
  > "we utilize the public python code vis_sample" (Model fitting)
   - software: vis_sample, emcee, CASA
   - parameter: 11 free parameters, flat priors, 100 walkers, 500 burn-in + 500 steps  
  > "The burn-in phase (from initial conditions to reasonable sampling) employs 500 steps, and we run another 500 steps for convergence, totaling 1000 steps with 100 walkers." (Model fitting)
   - assumption: Inclination and P.A. fixed to ellipse-fit values  
  > "The disk inclination ($i$) and position angle (P.A.) are fixed as in Table 1." (Model fitting)
   - fitting: emcee MCMC with flat priors  
  > "Our calculations used flat priors with the parameter ranges summarized in Table [2](#tab:table2)." (Model fitting)
   - validation: Reduced chi2 2.4; residual map shows 7 sigma west structure  
  > "The residual map shows a structure at $\sim$7 $\sigma$ level to the west in the outer dust ring, indicating a real azimuthal asymmetry." (Model fitting)
5. **12CO moment maps and rotation center check**: Moment 0 and 1 maps; compare to Keplerian loci for 0.53 Msun in PV diagram  
  > "we plot loci of the peak emission of a Keplerian disk around a 0.53 $M_{\odot}$ star (DM Tau’s mass) in the position–velocity diagram" (Results)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 5.1.1: Calibration, CLEAN imaging, fixvis, uvcontsub, imsmooth  
  > "CASA v5.1.1; (cite: mcmu07), vis_sample (https://github.com/AstroChem/vis_sample), emcee (cite: foreman-mackey+2013)" (Software)
- **vis_sample** : Sampling model images at observed uv coverage  
  > "we utilize the public python code vis_sample" (Model fitting)
- **emcee** : MCMC fitting of the disk model  
  > "we used the Markov Chain Monte Carlo (MCMC) method in the emcee package" (Model fitting)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Outer ring radius | 0.176 | 0.001 | arcsec | 2 | 0.176$\pm$0.001: 25.5$\pm$0.2 |
| Disk inclination | 35.2 | 0.7 | deg | 2 | 35.2$\pm$0.7 |
| Disk position angle | 157.8 | 1.0 | deg | 2 | 157.8$\pm$1.0 |
| Inner ring flux inside 0.06 arcsec | 1.33 | 0.03 | mJy | 2 | The total flux density of the inner ring inside 0.$''$06 is 1.33 $\pm$ 0.03 mJy. |
| Inner disk dust mass | 0.04 | not stated | M_Jup | 3 | the total mass of the inner disk is measured as 0.04 $M_{\rm Jup}$ |
| Outer ring azimuthal brightness contrast | 1.28 | 0.04 | dimensionless | 2 | is 1.28 $\pm$ 0.04 |
| Total continuum flux density | 116.75 | 0.14 | mJy | 1 | The total flux density after combining long and short baseline data is 116.75 $\pm$ 0.14 mJy |
| Cavity radius R_cav | 3.16 | +0.22/-0.23 | au | 4 | 3.16$^{+0.22}_{-0.23}$ |
| Gap depletion delta_2 | ~0.356 | not stated | dimensionless | 4 | The depletion factor $\delta_{2}$ at $r_{\rm gap_{2}}$ is measured as $\sim$0.356 |
| Reduced chi2 | 2.4 | not stated | dimensionless | 4 | is 2.4 |
| 12CO integrated intensity inside 0.18 arcsec | 185 | 7 | Jy km/s | 5 | The total integrated intensity is 185 $\pm$ 7 Jy km s$^{-1}$ inside 0.$''$18. |

## Qualitative findings

- Inner dust ring is symmetric in continuum but 12CO is asymmetric, peaking at north blob  
  > "This inner ring is symmetric in continuum emission, but asymmetric in $^{12}$CO emission." (abstract)

## Claim tuples

- H: DM Tau has a dust cavity of a few au | E: Long-baseline ALMA 1.3 mm imaging and visibility model fit | R: Inner ring at ~4 au and cavity R_cav=3.16 au | F: Confirms SED-inferred cavity | **supported**
- H: The outer ring is azimuthally asymmetric | E: Visibility model fit and residual map | R: Contrast 1.28±0.04 and 7 sigma residual | F: Real but low-contrast asymmetry | **supported**
- H: The gap is depleted relative to the outer ring | E: Radial profile and model | R: Factor ~40 depletion, gap not dust free | F: Consistent with planet-induced gaps | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Photoevaporation disfavored by normal accretion rate; secular gravitational instability and sintering inconsistent with gap properties  
  > "The measured close-to-normal accretion rate of DM Tau disfavors photoevaporation" (Discussions)
- How they decided it was enough: _not stated_
- Limitation (authors): Inner ring north-south asymmetry needs more data to confirm  
  > "More data are needed to confirm the apparent asymmetry." (Results)
- Caveat (inferred, ours): Reduced chi2 of 2.4 shows the model is imperfect
- Caveat (inferred, ours): MCMC run is short (1000 steps) with no convergence diagnostics
- Caveat (inferred, ours): No self-calibration; 13% decoherence loss
- Caveat (inferred, ours): Single-epoch single-array long-baseline data

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Code: vis_sample is public; no custom code released  
  > "vis_sample is publicly available at https://github.com/AstroChem/vis_sample" (Software)
- Missing: Imaging parameters (cell, size, masks, scales)
- Missing: Short-baseline dataset identification
- Missing: MCMC likelihood and uncertainty weighting
- Data volume (inferred): ~100-300 GB
- Score (inferred): 3/5, Data identified and tools public, but imaging and fit details are sparse.
- Rediscovery candidate: no, Imaging and likelihood details are incomplete and combining datasets is involved.

## Links

- Method: (cite: zhan16) (Visibility-domain deprojection)
- Method: (cite: rau11) (Multi-scale multi-frequency deconvolution)
- Companion: (cite: pini18) (Source of short-baseline ALMA data)

## Checks

```json
{
 "quotes": 71,
 "quotes_ok": 71,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 3,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [
  "2013.1.00198.S"
 ],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 11,
 "numeric_problems": 0,
 "fill": {
  "facts": 73,
  "stated": 46,
  "rate": 0.63
 },
 "evidence_ok": true
}
```
