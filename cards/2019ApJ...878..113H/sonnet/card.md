# Modeling the Spatial Distribution and Origin of CO Gas in Debris Disks

`2019ApJ...878..113H` | The Astrophysical Journal 2019 | first author: Hales, A. S. | arXiv: 1905.03844 | DOI: 10.3847/1538-4357/ab211e

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: debris_disks, astrochemistry
- Question: Where is the CO gas located in three CO-rich debris disks, and is it primordial or of secondary (cometary) origin?  
  > "The detection of gas in debris disks raises the question of whether this gas is a remnant from the primordial protoplanetary phase, or released by the collision of secondary bodies." (abstract)
- Target **HD 131835**: coordinates _not stated_; z/distance 133.7 pc  
  > "Distance (pc)$^{c}$              |   133.7   |   137.5   |   111.8" (Table 2); "HD 131835 (HIP 73145) is a well-studied, $\sim$16 My old A4V star located in the Upper Centaurus Lupus (UCL) moving group" (CO Rich Debris Disks in Sco-Cen); distance from Gaia DR2  
  > "Distance (pc)$^{c}$              |   133.7   |   137.5   |   111.8" (Table 2); "HD 131835 (HIP 73145) is a well-studied, $\sim$16 My old A4V star located in the Upper Centaurus Lupus (UCL) moving group" (CO Rich Debris Disks in Sco-Cen)
- Target **HD 138813**: coordinates _not stated_; z/distance 137.5 pc  
  > "HD 138813 (HIP 76310) is an A0V star member of the 11 Myr old Upper Scorpius association" (CO Rich Debris Disks in Sco-Cen); distance from Gaia DR2  
  > "HD 138813 (HIP 76310) is an A0V star member of the 11 Myr old Upper Scorpius association" (CO Rich Debris Disks in Sco-Cen)
- Target **HD 156623**: coordinates _not stated_; z/distance 111.8 pc  
  > "HD 156623 (HIP 84881) is also an A-type star member of the Upper Scorpius association" (CO Rich Debris Disks in Sco-Cen); distance from Gaia DR2  
  > "HD 156623 (HIP 84881) is also an A-type star member of the Upper Scorpius association" (CO Rich Debris Disks in Sco-Cen)

## Data provenance

- ALMA projects: 2012.1.00688.S
- bands: _not stated_
- frequencies and spectral setup: 12CO(2-1), velocity resolution 0.32 km/s  
  > "The velocity resolution of the cubes is 0.32 km s$^{-1}$" (CO Rich Debris Disks in Sco-Cen)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: beams 1.42x1.21, 1.02x0.71, 1.32x0.87 arcsec  
  > "| HD 131835 | $1.42\times 1.21$ | 28 | 10.1 | 16 | 798 $\pm$ 35 | 22.5 |" (Table 1)
- max recoverable scale: _not stated_
- sensitivity: line rms 10.1, 7.3, 5.9 mJy/beam per 0.32 km/s channel  
  > "| HD 138813 | $1.02\times 0.71$ | 81 | 7.3 | 14 | 1406 $\pm$ 78 | 18.0 |" (Table 1)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: 12CO J=2-1 (not stated)
- Other facility **Gaia DR2**: distances  
  > "Distances are obtained from the second data release (DR2) of Gaia" (Table 2)
- External data: ALMA CO(2-1) observational results, images and continuum/SED dust parameters  
  > "Summary of ALMA $^{12}$CO(2-1) observational results from (cite: Lieman2016)." (Table 1) [from (cite: Lieman2016)]
- External data: Stellar luminosities scaled from Hipparcos to Gaia distance  
  > "Luminosities are derived using the values in (cite: kral2017) scaled by the difference in distance between Hipparcos and Gaia DR2." (Table 2) [from (cite: kral2017)]
- External data: Stellar masses  
  > "Stellar mass for HD 131835 is taken from (cite: moor2015), and from (cite: hernandez2005) for HD 138813." (Table 2) [from (cite: moor2015); (cite: hernandez2005)]

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
- final beam: see Table 1 beams  
  > "| HD 156623 | $1.32\times 0.87$ | 87 | 5.9 | 11 | 1183 $\pm$ 37 | 32.3 |" (Table 1)
- final rms: _not stated_

### Inherited from earlier work

- Observations, CLEAN imaging and continuum analysis from earlier survey paper  
  > "A description of the selection criteria, the full source list, main observational results and analysis of the continuum data were presented in (cite: Lieman2016)." (Introduction) [from (cite: Lieman2016)]
- Dust mass, grain size and radial extent from SED modeling  
  > "The dust mass, grain size and radial extent are from the SED modeling of (cite: Lieman2016)." (Modeling gas of primordial origin) [from (cite: Lieman2016)]
- Thermochemical model details  
  > "We briefly summarize the main aspects of the models here and refer the reader to the original papers for more details." (Thermochemical model details) [from (cite: Gorti2004); (cite: Gorti2011)]

### Not stated but needed to reproduce (our reading)

- CASA version, calibration and imaging parameters (robust, weighting, masks) used for the data (inherited from Lieman-Sifry 2016)
- Stellar luminosity temperature/disk model details for synthetic LIME setup (grid, photons)
- Prior ranges and walker initialization for emcee
- Thermochemical code availability and exact dust grain parameters
- Observing dates, configurations and integration times

## Analysis recipe

1. **Derive gas disk geometry and radial emissivity**: Lucy-Richardson deconvolution with Keplerian velocity kernel, embedded in emcee MCMC over geometry parameters  
  > "for which the best-fit surface brightness distribution is found by Lucy-Richardson deconvolution as described in [3.1](#lucy)." (Disk modeling and parameter-space search)
   - software: emcee
   - parameter: 1000 walkers, burn-in 100-400 steps, 800-1000 further iterations; sampled area 2 arcsec radius; grid every 1/3 beam; Delta R 0.1 arcsec  
  > "After the burn-in phase, 800 to 1000 more iterations are allowed in order to further sample the posterior probability around the global maximum." (Disk modeling and parameter-space search); "We adopt a grid that samples every $1/3$ of the beam to prevent over-sampling and avoid excessive computational time." (Lucy-Richardson Deconvolution)
   - assumption: T_gas = T_dust in stellar equilibrium, flat Keplerian disk, no turbulence  
  > "The local disk temperature $T(r)$ is computed assuming that $T_{gas}(r)=T_{dust}(r)$" (Lucy-Richardson Deconvolution)
   - fitting: free: PA, inclination, v_r, offsets; stop when reduced chi2<1 or change <1%  
  > "until the reduced $\chi^2$ reaches a value less than unity or when the fractional change in the reduced $\chi^2$ is less than 1$\%$" (Lucy-Richardson Deconvolution)
   - validation: residual maps show no residuals above 5 sigma; compared with literature and imfit/uvmodelfit continuum inclinations  
  > "with no residuals above 5-$\sigma$ level (15% of the peak flux)" (Modeling results)
2. **Simple CO mass limits**: Optically thin LTE mass, LTE critical-density mass and photodissociation shielding estimates  
  > "A simple CO mass estimate can be made by assuming that the emission is in LTE and optically thin." (Estimate of optically thin LTE mass limit)
   - assumption: disk thickness 10 au, radius ~200 au  
  > "Assuming a constant disk thickness of 10 au" (Estimate of mass required for LTE)
   - fitting: _not stated_
   - validation: _not stated_
3. **Thermochemical modelling of primordial and secondary gas and compare to ALMA**: Thermochemical disk models with double power-law surface density, LIME non-LTE line cubes, simobserve and CASA imaging, fit by varying mass and slopes  
  > "The model images were processed through the CASA task simobserve to create synthetic visibilities" (Modeling gas of primordial origin)
   - software: LIME, CASA
   - parameter: primordial mass grid 0.1-35 Earth masses in 5 steps, then 0.1 steps; p1,p2 varied manually in -5 to +5, fine step 0.05  
  > "The surface density exponents p$_1$ and p$_2$ were varied manually between -5 and +5 using different step sizes, and then fine-tuned using steps of 0.05." (Modeling gas of primordial origin)
   - assumption: secondary: CO:H2O 1:10 released, gas T = dust T, run to ~2 Myr; primordial: ISM abundances, CR rate 1e-16 s-1, X-ray 1e27 erg/s, 1% dust outside belt  
  > "we assume that at the start of the simulation CO and H$_2$O are released in a 1:10 ratio" (Modeling gas of secondary origin)
   - fitting: manual grid fit to integrated spectra and channel maps  
  > "We initially fit the integrated flux by varying the total disk mass in the range 0.1 - 35M$_{\oplus}$ in steps of 5M$_{\oplus}$, to narrow down the mass range." (Modeling gas of primordial origin)
   - validation: compared integrated spectra and channel maps with data  
  > "The integrated spectra for the best fit models are compared to the $^{12}$CO(2–1) data in Figure [7](#intspec-pa)." (Modeling gas of primordial origin)
4. **Estimate CO production rate**: Production rate ~ (M(t=0) - M(t_f))/t_f from time-dependent chemical models  
  > "the production rate $\sim (M(t=0) - M(t_f))/t_f$" (Modeling gas of secondary origin)
   - fitting: _not stated_
   - validation: compared with beta Pic and Kral et al. 2018  
  > "Our rates are also in reasonable agreement with (cite: kral2018)" (Discussion)

## Software

- **CASA** 5.1.0: simobserve, imaging of model cubes; imfit and uvmodelfit for continuum inclination  
  > "The synthetic data cubes are then processed through CASA[^1] version 5.1.0" (Modeling gas of primordial origin)
- **emcee** : MCMC parameter search  
  > "The parameter search is performed using the Python package *emcee*" (Disk modeling and parameter-space search)
- **LIME** : non-LTE synthetic CO cubes  
  > "generate synthetic CO line emission data cubes using LIME" (Modeling gas of primordial origin)
- **Astropy** : listed in Software section  
  > "Astropy (cite: 2013A&A...558A..33A)" (Software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| HD 131835 inclination | 68.6 | 1.6 | deg | 1 | / HD 131835 / 68.6 $\pm$1.6 / 57.7 $\pm$6.2 / 7.26 $\pm$0.06 / 0.03$\pm$0.06 / -0.02$\pm$0.06 / |
| HD 138813 inclination | 29.0 | 0.3 | deg | 1 | / HD 138813 / 29.0 $\pm$0.3 / 49.6 $\pm$0.8 / 7.75 $\pm$0.01 / -0.08$\pm$0.01 / 0.03$\pm$0.01 / |
| HD 156623 inclination | 31.8 | 0.5 | deg | 1 | / HD 156623 / 31.8 $\pm$0.5 / 94.1 $\pm$2.8 / 4.20 $\pm$0.03 / 0.05$\pm$0.02 / 0.01$\pm$0.02 / |
| CO masses, primordial models (HD 131835, HD 138813, HD 156623) | 5.0e-3, 4.2e-3, 3.8e-3 | not stated | Earth masses | 3 | total CO masses of $5.0\times 10^{-3}$,$4.2\times 10^{-3}$ and $3.8\times 10^{-3}$ M$_{\oplus}$ |
| CO masses, cometary models | 4.6e-3, 3.1e-3, 2.45e-3 | not stated | Earth masses | 3 | The best fit cometary gas masses are $4.6 \times 10^{-3},
 3.1\times 10^{-3}$ and $2.45\times 10^{-3}$ M$_{\oplus}$ |
| CO replenishment rate | 8e-7 | not stated | Earth masses per yr | 4 | $8\times 10^{-7}$ M$_{\oplus}$ yr$^{-1}$ |

## Qualitative findings

- CO emission in HD 131835 and HD 138813 is ring-like; HD 156623 is centrally peaked  
  > "The CO surface brightness from HD 156623 is found to be centrally peaked." (Modeling results)

## Claim tuples

- H: Is the CO gas primordial or secondary? | E: Thermochemical models of both scenarios fit to CO(2-1), plus gas-drag argument | R: Both reproduce emission; primordial needs tens of Earth masses of H2 | F: Secondary origin favored | **supported**
- H: Do CO production rates resemble beta Pic? | E: Time-dependent chemistry for cometary model | R: ~8e-7 Earth masses/yr vs 2.3e-7 for beta Pic | F: Rates only slightly higher than beta Pic | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Primordial/hybrid origin rejected since gas drag retains small dust, making disk optically thick  
  > "These disks would then no longer be classified as debris disks." (Discussion)
- How they decided it was enough: _not stated_
- Limitation (authors): Single CO transition cannot break mass-temperature degeneracy  
  > "this degeneracy cannot be broken with only one CO transition observed." (Modeling gas of primordial origin)
- Caveat (inferred, ours): Resolution of 1-1.5 arcsec is coarse for sub-beam deconvolution
- Caveat (inferred, ours): T_gas=T_dust assumption and manual model fitting without uncertainties
- Caveat (inferred, ours): Gas and dust only partially co-located

## Reproducibility

- Data public (paper): ALMA data acknowledged by project code  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2012.1.00688.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Thermochemical code not released
- Missing: Calibration/imaging details only in Lieman-Sifry 2016
- Missing: Lucy-Richardson code not stated as released
- Data volume (inferred): ~10-50 GB raw
- Score (inferred): 3/5, Public data and clear deconvolution recipe, but thermochemical modelling is manual and depends on unreleased code and inherited processing.
- Rediscovery candidate: no, Main results rely on custom thermochemical models and manual fits.

## Links

- Method: (cite: scoville1983) (Lucy-Richardson deconvolution with kinematic prior)
- Method: (cite: Gorti2011) (thermochemical model)
- Companion: (cite: Lieman2016) (original ALMA survey and data reduction)
- Companion: (cite: kral2018) (complementary CI modeling and secondary gas origin)
- Related: ALMA Sco-Cen debris disk survey (Lieman-Sifry et al. 2016)

## Checks

```json
{
 "quotes": 54,
 "quotes_ok": 54,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 80,
  "stated": 40,
  "rate": 0.5
 },
 "evidence_ok": true
}
```
