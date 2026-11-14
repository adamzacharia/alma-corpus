# CO Gas Inside the Protoplanetary Disk Cavity in HD 142527: Disk Structure from ALMA

`2015ApJ...798...85P` | The Astrophysical Journal 2015 | first author: Perez, S. | arXiv: 1410.8168 | DOI: 10.1088/0004-637X/798/2/85

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks
- Question: How much gas survives inside the dust-depleted cavity of the HD 142527 disk, and what are the gas cavity size, wall shape and inclination?  
  > "Estimates of the survival of gas inside disk cavities are needed to discriminate between clearing scenarios." (abstract)
- Target **HD 142527**: coordinates _not stated_; z/distance 140 pc  
  > "HD 142527 is most likely embedded inside the Lu22 condensation of the Lupus dark cloud, at a distance of 140 pc away" (Introduction); distance from Vilas-Boas et al. 2000 (Lu22 condensation of Lupus)  
  > "HD 142527 is most likely embedded inside the Lu22 condensation of the Lupus dark cloud, at a distance of 140 pc away" (Introduction)

## Data provenance

- ALMA projects: 2011.0.00465.S
- bands: Band 6 (~230 GHz)  
  > "we analyse ALMA Band-6 ($\sim$230 GHz) CO line emission and dust continuum observations of HD 142527." (Introduction)
- frequencies and spectral setup: FDM, 125 MHz bandwidth in four spectral windows, 0.2 km/s channels; 12CO, 13CO, C18O J=2-1 at 230.538, 220.399, 219.560 GHz  
  > "The ALMA correlator was configured in the Frequency Division Mode (FDM) to provide 125 MHz bandwidth in four different spectral windows at 0.2 km s$^{-1}$ resolution per channel." (2 ALMA data and processing)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: up to 402 m  
  > "The dataset provides baselines up to 402 meters" (2 ALMA data and processing)
- angular resolution: 0.85" x 0.64", PA -66.5 deg (lines)  
  > "resulted in a synthetic beam size of 0.85$\ensuremath{''}\times$0.64$\ensuremath{''}$ at PA$=-66.5$ degrees" (2 ALMA data and processing)
- max recoverable scale: _not stated_
- sensitivity: 11 mJy per 0.2 km/s channel  
  > "an RMS noise level of 11 mJy per 0.2 km s$^{-1}$ channel was reached" (2 ALMA data and processing)
- time on source: 82 minutes total (both sessions)  
  > "The total time spent on-source was 82 minutes." (2 ALMA data and processing)
- observing dates: 2012 April 12 and June 15; only June used  
  > "The HD 142527 band 6 observations were acquired on 2012 April 12, and June 15, using sixteen and twenty 12m antennas respectively." (2 ALMA data and processing)
- pi or archival as stated: _not stated_
- Line: 12CO J=2-1 (230.538 GHz)
- Line: 13CO J=2-1 (220.399 GHz)
- Line: C18O J=2-1 (219.560 GHz)
- Other facility **ALMA Band 7 (Cycle 0, Casassus et al. 2013)**: 345 GHz continuum data  
  > "we also make use of the 345 GHz continuum data described in (cite: Cas2013)." (2 ALMA data and processing)
- External data: 12CO/13CO ratio 76.27±1.94 in ISM  
  > "we adopt the $^{12}{\rm CO}$ to $^{13}{\rm CO}$ ratio of $76.27\pm1.94$ as measured in the ISM by (cite: Sta2008)." (3.3 Optical Thickness) [from (cite: Sta2008)]
- External data: 12CO/C18O ratio 500  
  > "The $^{12}{\rm CO}$ to ${\rm C}^{18}{\rm O}$ ratio is assumed to be the canonical value of $500$ for the ISM (cite: Wil1994)." (3.3 Optical Thickness) [from (cite: Wil1994)]
- External data: Archival ALMA C18O J=3-2 integrated intensity/noise from Fukagawa et al. 2013  
  > "The noise level on each of these channel map is 0.12 mJy beam$^{-1}$ (cite: Fuk2013)." (3.5) [from (cite: Fuk2013)]
- External data: Observed SED photometry and A_V=0.6  
  > "We obtained observed continuum fluxes from (cite: Ver2011) (see references there in)." (Spectral energy distribution) [from (cite: Ver2011)]

## Processing

### Calibration

- pipeline or manual: CASA, standard fashion (WVR, Tsys, bandpass, phase, amplitude)  
  > "which included offline Water Vapor Radiometer (WVR) calibration, system temperature correction, as well as bandpass, phase and amplitude calibrations." (2 ALMA data and processing)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Titan  
  > "In both sessions Titan was observed as flux calibrator" (2 ALMA data and processing)
- flux scale uncertainty: ~10%  
  > "we estimate the absolute flux calibration to be accurate within $\sim$10 $\%$." (2 ALMA data and processing)
- self calibration: _not stated_

### Imaging

- task: CLEAN in CASA  
  > "Imaging of the CO lines was performed using the CLEAN task in CASA" (2 ALMA data and processing)
- deconvolver: _not stated_
- weighting robust: Briggs weighting (robust not stated)  
  > "Maps were reconstructed with CLEAN using Briggs weighting." (3.1.2 Channel maps)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: in visibility domain before imaging  
  > "Continuum subtraction in the visibility domain was performed prior to imaging of the CO lines." (2 ALMA data and processing)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.85x0.64 arcsec lines; 0.94x0.72 continuum  
  > "Cont. | 225.393 | 0.94$\times$0.72" (Table 1)
- final rms: _not stated_

### Inherited from earlier work

- Band 7 345 GHz continuum data  
  > "we also make use of the 345 GHz continuum data described in (cite: Cas2013)." (2 ALMA data and processing) [from (cite: Cas2013)]
- Isotopic line-ratio optical depth method  
  > "We can estimate the optical depths ($\tau_\nu$) of each isotopologue from their observed isotopic line ratio (cite: Lyo2011)." (3.3 Optical Thickness) [from (cite: Lyo2011)]
- Surface density profile parameterization  
  > "The global surface density profile is a power law in radius with an exponential tapering at large radii, as described in (cite: Lyn1974) (cite: And2011)." (4.1) [from (cite: Lyn1974; And2011)]

### Not stated but needed to reproduce (our reading)

- Briggs robust value, cell size, image size, CLEAN masks and threshold
- Line-free channels used for continuum subtraction
- Whether data were self-calibrated
- CASA version
- LIME settings (number of grid points, photons, collision data) and model grid ranges
- How the high-velocity channel peaks were selected and summed for 13CO
- Solid angle Omega adopted for the cavity
- Model grids for M_star and inclination; how model visibilities were produced
- Exact 3C279/J1604-446 flux handling details

## Analysis recipe

1. **Calibrate and image CO cubes**: Standard CASA calibration; continuum subtraction in uv; CLEAN with Briggs weighting; 0.2 km/s channels; June data only  
  > "in this work we only used the June observations which have higher signal-to-noise and better $uv$-coverage than the April data." (2 ALMA data and processing)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Moment maps and spectra**: Gaussian fit to each spaxel spectrum, median-filtered 0.1"x0.1"; systemic velocity from symmetric line wings  
  > "derived by fitting a gaussian profile to the spectral axis in each spatial pixel of the CLEANed data cubes." (3.1.1 Moment maps)
   - fitting: _not stated_
   - validation: _not stated_
3. **Optical depth from isotopologue ratios**: Isothermal slab line ratio in high-velocity channels (<1.8 and >5.4 km/s)  
  > "In this velocity range, the isotopic line ratio $R$ has a value of 2.0$\pm$0.2, which yields optical depths of" (3.3 Optical Thickness)
   - assumption: Same excitation temperature, CMB neglected, 12CO/13CO=76, 12CO/C18O=500  
  > "We also assume that the two selected lines share the same excitation temperature" (3.3 Optical Thickness)
   - fitting: _not stated_
   - validation: _not stated_
4. **Gas mass in cavity from optically thin 13CO and C18O**: LTE column density from summed peak emission in high-velocity channels, converted to H2 mass  
  > "We measured the integrated line intensity of $^{13}{\rm CO}$ by summing the peak emission from the selected high velocity channels" (3.5)
   - parameter: T=43 K, d=140 pc, mu=1.36  
  > "For the gas temperature we used $T=43$ K, as calculated from $^{12}{\rm CO}$ in the previous section." (3.5)
   - assumption: [H2]/[12CO]=1e4, [12CO]/[13CO]=76, LTE  
  > "Assuming a fiducial CO interstellar abundance of $[{\rm H}_2]/[\mbox{$^{12}{\rm CO}$}]=10^4$ and $[\mbox{$^{12}{\rm CO}$}]/[\mbox{$^{13}{\rm CO}$}]=76$" (3.5)
   - fitting: _not stated_
   - validation: Cross-check with archival C18O J=3-2  
  > "consistent with the $J=2-1$ estimate (5-$\sigma$ error bars)" (3.5)
5. **Forward model gas disk with LIME**: Parametric axisymmetric disk, LIME non-LTE radiative transfer, model visibilities sampled at observed uv, chi2 comparison; scan of M_star and inclination, then cavity radius  
  > "Our models were compared to the data in the visibility plane based on $\chi^2$ statistics." (4.2 Modeling Results)
   - software: LIME, CASA
   - parameter: h=0.1 r, gamma=1, R_c=200 au, T=50 K (r/50au)^-0.3, b=50 m/s, inner truncation 0.3 au  
  > "The velocity dispersion of the random motions of the gas (Doppler b-parameter) was fixed to 50 m s$^{-1}$." (4.1)
   - assumption: Keplerian rotation, ISM CO abundance, vertically isothermal, axisymmetric  
  > "For simplicity, we assumed that the gas in the disk follows circular Keplerian rotation" (4.1)
   - fitting: Reduced chi2 grid in M_star and inclination; cavity radius by visual inspection  
  > "The error was obtained from visual inspection of the plotted models against the $^{13}{\rm CO}$ data." (4.2 Modeling Results)
   - validation: Visual comparison of best model with 13CO and C18O maps; SED consistency check with MCFOST  
  > "Finally, the best fit models were contrasted with the data by visual inspection." (4.2 Modeling Results)

## Software

- **CASA** : Calibration and CLEAN imaging  
  > "All the line data were calibrated using the *Common Astronomy Software Applications* package" (2 ALMA data and processing)
- **LIME** : Non-LTE radiative transfer for model channel maps  
  > "three-dimensional non-local thermodynamic equilibrium (non-LTE) molecular excitation and radiative transfer code LIME (cite: Bri2010)" (4.2 Modeling Results)
- **MCFOST** : SED of the disk model  
  > "Synthetic fluxes were calculated using the Monte Carlo radiative transfer code MCFOST (cite: Pin2006)." (Spectral energy distribution)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Inclination | 28 | 0.5 | deg | 5 | $i$ / deg / 28 / 0.5 |
| Gas cavity radius | 90 | 5 | au | 5 | The best fit for the cavity radius in the gas is 90$\pm5$ au. |
| Gas depletion factor delta_gap | 0.02 | 0.01 | dimensionless | 5 | We estimate an uncertainty of 0.01 based on the optical thickness of the lines. |
| Gas mass in cavity from 13CO | 1.7e-3 | 0.6e-3 | Msun | 4 | $M_{\rm gas} = (1.7 \pm 0.6)\times 10^{-3}$ M$_\odot$ |
| Isotopic line ratio R | 2.0 | 0.2 | dimensionless | 3 | the isotopic line ratio $R$ has a value of 2.0$\pm$0.2 |
| Optical depth 12CO | ~56 | not stated | dimensionless | 3 | $\tau_{\scriptstyle \rm {12}CO} \sim 56$ and $\tau_{\scriptstyle \rm {13}CO} \sim 0.7$ |
| Systemic velocity | 3.6 | 0.1 | km/s | 2 | We measure the systemic velocity at $3.6\pm0.1$ ${\rm km\,s}^{-1}$ |
| 12CO gas temperature at 80 au | 43 | not stated | K | 0 | implies a gas temperature of 43 K for the $^{12}{\rm CO}$ gas surface, measured at a radius of 80 au. |
| Total disk mass from model | 0.1 | not stated | Msun | 5 | yields a total (dust plus gas) mass of the disk of 0.1 M$_{\odot}$ |

## Qualitative findings

- CO gas cavity is smaller than the dust cavity and the gas wall is diffuse while the dust wall is sharper  
  > "The gap wall appears diffuse and tapered-off in the gas distribution, while in dust continuum is manifestly sharper." (Summary)

## Claim tuples

- H: Gas survives inside the dust cavity | E: CO isotopologue J=2-1 imaging, high-velocity channels | R: Emission from all three isotopologues inside cavity; ~1.5-2 MJup | F: Substantial gas remains, disfavoring photoevaporation as the main clearing | **supported**
- H: Gas cavity size differs from dust cavity | E: 13CO modeling and radial cuts | R: Gas cavity radius 90±5 au vs ~140 au dust | F: Gas cavity smaller with smoother wall | **supported**
- H: Disk inclination from gas kinematics | E: chi2 in uv-plane with M_star fixed at 2.2 | R: i=28±0.5 deg | F: Higher than the previous ~20 deg | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Gas mass is a crude estimate, dominated by assumed isotopic ratios and temperature  
  > "The main sources of uncertainty are the assumed isotopic line ratios and the gas temperature." (3.5)
- Caveat (inferred, ours): Inclination/M_star degeneracy: Δchi2 values are tiny and the 0.5 deg error looks underestimated
- Caveat (inferred, ours): Cavity radius error from visual inspection only
- Caveat (inferred, ours): Axisymmetric model ignores known non-axisymmetry and non-Keplerian gas
- Caveat (inferred, ours): 12CO foreground absorption from intervening cloud
- Caveat (inferred, ours): Single-temperature LTE mass with canonical isotope ratios

## Reproducibility

- Data public (paper): ALMA Cycle 0 project 2011.0.00465.S acknowledged  
  > "This paper makes use of the following ALMA data: ADS/ JAO.ALMA#2011.0.00465.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Imaging parameters (robust, masks, cell size)
- Missing: LIME configuration and model grid
- Missing: Band 7 continuum data reference reduction
- Data volume (inferred): ~10-30 GB
- Score (inferred): 3/5, Data public and clear methods, but imaging and modeling settings are missing and fits are partly visual.
- Rediscovery candidate: no, Modeling setup incomplete and inclination/cavity estimates rely on LIME grid and visual inspection.

## Links

- Method: (cite: Lyo2011) (Isotopologue line ratio optical depth)
- Method: (cite: Bri2010) (LIME code)
- Companion: (cite: Cas2013) (Band 7 ALMA observations of HD 142527)
- Companion: (cite: Fuk2013) (ALMA CO J=3-2 data)

## Checks

```json
{
 "quotes": 61,
 "quotes_ok": 61,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 9,
 "numeric_problems": 0,
 "fill": {
  "facts": 76,
  "stated": 44,
  "rate": 0.579
 },
 "evidence_ok": true
}
```
