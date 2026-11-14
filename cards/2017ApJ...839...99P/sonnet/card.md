# A Multi-wavelength Analysis of Dust and Gas in the SR 24S Transition Disk

`2017ApJ...839...99P` | The Astrophysical Journal 2017 | first author: Pinilla, P. | arXiv: 1703.09227 | DOI: 10.3847/1538-4357/aa6973

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks
- Question: How do the dust (0.45 and 1.3 mm) and gas (13CO, C18O) distributions in the SR 24S transition disk compare with dust-trapping models, and is the northern companion SR 24N detected?  
  > "We perform a multi-wavelength investigation by combining new data with previous ALMA data at 0.45 mm." (abstract)
- Target **SR 24S (and SR 24N)**: coordinates RA 16:26:58.5, Dec -24:45:37.2 (J2000, adopted phase center)  
  > "In this paper, we adopt a value of 137 pc." (Introduction); "$\alpha_{2000}$=16:26:58.5, $\delta_{2000}$=-24:45:37.2 were used to correct the phase center" (Observations); z/distance 137 pc  
  > "In this paper, we adopt a value of 137 pc." (Introduction); "$\alpha_{2000}$=16:26:58.5, $\delta_{2000}$=-24:45:37.2 were used to correct the phase center" (Observations); distance from adopted within the 120-145 pc range for L1688 (Mamajek 2008; Loinard 2008)  
  > "In this paper, we adopt a value of 137 pc." (Introduction); "$\alpha_{2000}$=16:26:58.5, $\delta_{2000}$=-24:45:37.2 were used to correct the phase center" (Observations)

## Data provenance

- ALMA projects: 2013.1.00091.S, 2011.0.00724.S
- bands: Band 6 (1.3 mm) new; 0.45 mm Cycle 0 archival  
  > "SR 24 was observed with ALMA in Band 6 during Cycle 2 on September 26th, 2015 (#2013.1.00091.S)." (Observations)
- frequencies and spectral setup: 4 spws of 1875 MHz; C18O at 219.56035 GHz, 13CO at 220.39868 GHz, ~1.35 km/s channels; continuum centered at 235 GHz  
  > "The source was observed in four spectral windows, each with a bandwidth of 1875.0 MHz." (Observations); "The other spectral windows were configured to obtain the continuum emission centered at 235 GHz ($\sim$1.3 mm)." (Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: longest baseline 2269.9 m; 34 antennas  
  > "For these observations 34 antennas were used and the longest baseline was 2269.9 m." (Observations)
- angular resolution: 0.18" x 0.12" (1.3 mm continuum, Briggs); 0.37" x 0.19" (0.45 mm)  
  > "| 2 | 0.18$\times$0.12 | 1.30 | 15.4 | 220 | 0.06 |" (Table 1)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: 49.31 min total, 22.67 min on source  
  > "The total observation time was 49.31 min, with a total time on source of 22.67 min." (Observations)
- observing dates: 2015 September 26  
  > "SR 24 was observed with ALMA in Band 6 during Cycle 2 on September 26th, 2015 (#2013.1.00091.S)." (Observations)
- pi or archival as stated: _not stated_
- Line: 13CO J=2-1 (220.39868 GHz)
- Line: C18O J=2-1 (219.56035 GHz)
- External data: 0.45 mm Cycle 0 continuum data of SR 24S (project 2011.0.00724.S)  
  > "The details of the calibration process for the Cycle 0 data are presented in (cite: perez_L2014)." (Results) [from (cite: marel2015); calibration (cite: perez_L2014)]
- External data: Mid-plane temperatures from dust radiative transfer models of SR 24S  
  > "For the physical temperature, we assume the mid-plane values from dust radiative transfer models for SR 24S in (cite: marel2015)." (4.2 Optical thickness) [from (cite: marel2015)]
- External data: Dust opacity at 1.3 mm of ~3 cm2/g  
  > "a dust opacity at 1.3 mm of $\sim3\,$cm$^{2}$g$^{-1}$ (cite: andrews2011)" (Results) [from (cite: andrews2011)]

## Processing

### Calibration

- pipeline or manual: CASA calibration; details not given  
  > "The data were calibrated using the Common Astronomy Software Package (CASA), version 4.4." (Observations)
- casa version: CASA 4.4  
  > "The data were calibrated using the Common Astronomy Software Package (CASA), version 4.4." (Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Pallas (flux); QSO J1517-2422 (bandpass); J1617-2537 and J1627-2426 (phase)  
  > "The asteroid Pallas was observed for the flux calibration." (Observations)
- flux scale uncertainty: 10% calibration uncertainty  
  > "the error includes a calibration uncertainty of 10%" (Results)
- self calibration: _not stated_

### Imaging

- task: clean  
  > "Continuum and line imaging were performed using the `clean` algorithm." (Observations)
- deconvolver: _not stated_
- weighting robust: Briggs robust = 0.5 for continuum; natural for lines  
  > "We used natural weighting and Briggs weighting (robust = 0.5) to find the best compromise between resolution and sensitivity." (Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: uvcontsub  
  > "The continuum was subtracted from line-containing channels using `uvcontsub`." (Observations)
- line free channels: _not stated_
- primary beam correction: applied to the 1.3 mm image  
  > "after the cleaning process (and after primary beam correction)" (Continuum emission)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.18" x 0.12" (continuum); 0.21" x 0.16" (lines, natural)  
  > "the final beam size in this case is 0.21”$\times$0.16”." (Observations)
- final rms: 63 uJy/beam continuum; ~1.4 mJy/beam per 1.35 km/s channel for lines  
  > "we achieved a rms of 63 $\mu$Jy beam$^{-1}$ with a beam size of 0.18” $\times$ 0.12”." (Observations); "for a final rms of around 1.4 mJy beam$^{-1}$ per 1.35 km s$^{-1}$ channel for both lines" (Observations)

### Inherited from earlier work

- Calibration of Cycle 0 0.45 mm data  
  > "The details of the calibration process for the Cycle 0 data are presented in (cite: perez_L2014)." (Results) [from (cite: perez_L2014)]
- Temperature structure for optical depth taken from earlier radiative transfer modeling  
  > "we assume the mid-plane values from dust radiative transfer models for SR 24S in (cite: marel2015)." (4.2 Optical thickness) [from (cite: marel2015)]

### Not stated but needed to reproduce (our reading)

- Line-free channels used for uvcontsub
- Image size and cell size for clean (pixel sizes only given in the fit section), masks, thresholds, iterations
- CASA version/calibration details of Cycle 0 data
- Temperature profile values taken from van der Marel et al. 2015
- Starting values/initialization of emcee walkers; uv binning of visibilities
- Which channels formed the moment-0 maps beyond velocity range

## Analysis recipe

1. **Find disk center, PA and inclination and recenter**: uvmodelfit with Gaussian/disk model on short baselines or all uv; center checked by minimizing scatter of imaginary visibilities; fixvis to recenter  
  > "a simple Gaussian or disk model was used to fit the data (using `uvmodelfit` in CASA)" (Observations)
   - software: CASA uvmodelfit, fixvis
   - parameter: short baselines <~200 kλ or full uv  
  > "either using only short baselines ($\lesssim200\,$k$\lambda$) or all the uv coverage" (Observations)
   - fitting: _not stated_
   - validation: Two independent center determinations agree  
  > "Both methods give very similar centers" (Observations)
2. **Image continuum and CO lines; derive fluxes, moment maps**: clean with Briggs/natural weighting, uvcontsub, moment-0 maps from -1.35 to 10.8 km/s  
  > "zero moment map for $^{13}$CO and C$^{18}$O obtained from -1.35 km s$^{-1}$ to 10.8 km s$^{-1}$" (Gas emission)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
3. **Dust masses and integrated spectral index**: Optically thin mass formula; alpha_mm from total fluxes at 0.45 and 1.3 mm; SR 24N upper limit from 3 sigma_N in 1" circle  
  > "Assuming optically thin emission, the dust mass can be estimated as (cite: hildebrand1983)" (Continuum emission)
   - assumption: d = 137 pc, kappa(1.3 mm) ~3 cm2/g, T = 20 K  
  > "Assuming a distance of 137 pc, a dust opacity at 1.3 mm of $\sim3\,$cm$^{2}$g$^{-1}$ (cite: andrews2011) and a temperature of 20 K" (Continuum emission)
   - fitting: _not stated_
   - validation: _not stated_
4. **Visibility-domain fitting of ring morphology**: Fit real part of visibilities with three axisymmetric ring models (Gaussian, asymmetric Gaussian, Gaussian+power law), separately at each wavelength; PA and i from 1.3 mm fixed for 0.45 mm  
  > "we obtained the PA and the $i$ using the 1.3 mm data (since it has better signal-to-noise) for each model, and keep the best-fit values of these two parameters to fit the 0.45 mm data." (4.1 Disk morphology)
   - software: emcee
   - parameter: radial grid 1-500 au in 0.1 au steps; 4000 steps, 1000 walkers, burn-in ~1000 steps  
  > "for a total of 4000 steps with 1000 walkers." (4.1 Disk morphology)
   - fitting: emcee MCMC, Gaussian likelihood on real visibilities, uniform priors (e.g. Rpeak 1-100 au, Rwidth 1-50 au, i and PA 10-80 deg, x0,y0 +-0.2")  
  > "We adopted a set of uniform prior probability distributions for the free parameters explored by the Markov chain in the three models" (4.1 Disk morphology)
   - validation: Synthetic images and residuals made with identical uv coordinates; test with fixed uvmodelfit parameters; two-ring test  
  > "We image the models and residuals (data-model) using identical $(u,v)$ coordinates as the actual ALMA observations." (4.1 Disk morphology)
5. **Spectral index profile and optical depth**: Spectral index from best-fit intensity profiles; tau from brightness temperature of de-projected azimuthally averaged image without Rayleigh-Jeans  
  > "optical depth $\tau$ obtained from the brightness temperature, which is calculated from the azimuthally averaged flux of the de-projected image" (4.2 Optical thickness)
   - assumption: Mid-plane temperature from van der Marel et al. 2015 models  
  > "we assume the mid-plane values from dust radiative transfer models for SR 24S in (cite: marel2015)." (4.2 Optical thickness)
   - fitting: _not stated_
   - validation: Error propagation from rms and azimuthal standard deviation  
  > "The error bars are obtained from error propagation taking into account the rms of the observations and the standard deviation from the azimuthally averaged flux values." (4.2 Optical thickness)

## Software

- **CASA** 4.4: calibration, uvmodelfit, fixvis, clean, uvcontsub  
  > "The data were calibrated using the Common Astronomy Software Package (CASA), version 4.4." (Observations)
- **emcee** : MCMC fitting of visibility models  
  > "For the fits, we used *emcee* (cite: foreman2013)" (4.1 Disk morphology)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| 1.3 mm total flux | 220 | not stated | mJy | 2 | / 2 / 0.18$\times$0.12 / 1.30 / 15.4 / 220 / 0.06 / |
| 0.45 mm total flux | 1885 | not stated | mJy | 2 | / 0 / 0.37$\times$0.19 / 0.45 / 278 / 1885 / 1.9 / |
| Integrated spectral index alpha_mm | 2.02 | 0.13 | dimensionless | 3 | $\alpha_{\rm{mm}} = \ln(F_{\rm{1.3\,mm}}/F_{\rm{0.45\,mm}}) /\ln (\rm{0.45\,mm}/\rm{1.3\,mm}) = 2.02\pm{0.13}$ |
| SR 24S dust mass | 3.0e-4 | not stated | Msun | 3 | $M_{\mathrm{dust, SR\,24S}}\sim3.0\times10^{-4}M_\odot$ |
| SR 24N dust mass upper limit | <=0.12 | not stated | Earth masses | 3 | $\lesssim 0.12\,M_{\bigoplus}$ |
| Dust mass ratio SR 24S/SR 24N | >~840 | not stated | dimensionless | 3 | $M_{\mathrm{dust, SR\,24S}}/M_{\mathrm{dust, SR\,24N}}\gtrsim840$ |
| uvmodelfit PA and inclination (1.3 mm) | PA 27.8 deg, i 49.8 deg | 1.3 deg, 2.4 deg | deg | 1 | $27.8^{\circ}\pm{1.3}^{\circ}$ and $49.8^{\circ}\pm{2.4}^{\circ}$ respectively |
| Ring peak radius, symmetric Gaussian, 1.3 mm | 42.15 | +2.29/-2.67 | au | 4 | / $1.30$ mm / $42.15^{+2.29}_{-2.67}$ / $21.41^{+2.69}_{-2.04}$ / |
| Ring peak radius, symmetric Gaussian, 0.45 mm | 20.66 | +3.25/-3.17 | au | 4 | / $0.45$ mm / $20.66^{+3.25}_{-3.17}$ / $36.62^{+2.36}_{-2.49}$ / |
| Region with alpha_mm<2 | 32 to 81 au | 3 and 4 au | au | 5 | specifically from $32\pm3$ au to $81\pm4$ au |
| Cavity depletion at 1.3 mm vs 0.45 mm | ~85% vs ~24% | not stated | percent of peak | 2 | the flux is reduced by around 85% |

## Qualitative findings

- 13CO and C18O peak at the center of the mm cavity; neither dust nor gas detected in SR 24N  
  > "we find that the $^{13}$CO and C$^{18}$O (J=2-1) emission peaks at the center of the continuum cavity." (abstract)

## Claim tuples

- H: Does the ring narrow at longer wavelength as predicted by dust trapping? | E: Visibility MCMC ring fits at 0.45 and 1.3 mm | R: Ring peak ~20 au further out and ~10 au narrower at 1.3 mm | F: Consistent with pressure-bump trapping, though peak shift may be optical depth | **supported**
- H: Is gas present inside the mm cavity? | E: 13CO and C18O moment maps and radial cuts | R: Emission peaks at cavity center | F: Gas not strongly depleted or cavity unresolved; low-mass planets or dead zone | **supported**
- H: Is SR 24N detected in dust or gas? | E: Flux/rms at SR 24N location | R: ~3 sigma flux, no CO detection; dust mass <=0.12 Mearth | F: SR 24N poor in mm-grains and cold gas | **supported**
- H: Is the ring emission optically thin? | E: Brightness-temperature optical depth with literature temperatures | R: tau>1 near the ring at both wavelengths | F: alpha_mm cannot be read as grain growth in the ring | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Visibility modeling avoids deconvolution limits and can identify unresolved structures  
  > "visibility modeling has some advantages over imaging analysis, since it can identify unresolved structures" (Observations)
- Alternative: Internal photoevaporation ruled out as cavity origin  
  > "this scenario can be ruled out as a potential origin for the mm-cavity in SR 24S" (Discussion)
- How they decided it was enough: _not stated_
- Limitation (authors): Gas masses not estimated due to foreground absorption  
  > "because of the foreground absorption in some of the channels, we do not estimate gas masses from the current observations" (Gas emission)
- Limitation (authors): Only real visibilities fit, so significance of asymmetry residuals unclear  
  > "in the framework of our models, it is difficult to conclude how significant is the amount of residuals" (4.1 Disk morphology)
- Caveat (inferred, ours): Optical thickness and assumed 20 K temperature make dust mass a rough lower estimate
- Caveat (inferred, ours): Foreground cloud absorption contaminates CO lines; central peak may be affected
- Caveat (inferred, ours): Fitting only real part with fixed PA/i for 0.45 mm; MCMC convergence settings loosely described
- Caveat (inferred, ours): Different resolutions at the two wavelengths complicate the comparison of cavity depth

## Reproducibility

- Data public (paper): Archive data cited by project code; public status not explicitly stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2013.1.00091.S and #2011.0.00724.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Line-free channel ranges, clean masks and image/cell sizes for imaging
- Missing: Cycle 0 calibration details
- Missing: Temperature profile from van der Marel et al. 2015
- Data volume (inferred): ~20-60 GB for the two datasets
- Score (inferred): 3/5, Data identified and fit models/priors well specified, but imaging and Cycle 0 details are missing.
- Rediscovery candidate: yes, ALMA data are archival projects, fitting recipe and priors are given, and main results are numeric (ring parameters, fluxes, alpha_mm).

## Links

- Method: (cite: perez_L2014) (Calibration of the Cycle 0 data and visibility modeling approach)
- Method: (cite: foreman2013) (emcee sampler)
- Companion: (cite: marel2015) (Original 0.45 mm Cycle 0 observations and radiative transfer model of SR 24S)

## Checks

```json
{
 "quotes": 71,
 "quotes_ok": 71,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
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
