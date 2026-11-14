# The First Detection of Molecular Activity in the Largest Known Oort Cloud Comet: ALMA Imaging of C/2014 UN271 (Bernardinelli─Bernstein) at 16.6 au from the Sun

`2025ApJ...986L..22R` | The Astrophysical Journal Letters 2025 | first author: Roth, Nathan X. | arXiv: 2505.04767 | DOI: 10.3847/2041-8213/add526

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: solar_system
- Question: What are the molecular activity drivers, CO outgassing kinematics and continuum (nucleus/dust) properties of the distant active Oort cloud comet C/2014 UN271 at 16.6 au?  
  > "revealing the nature of the activity drivers and outgassing kinematics of the largest Oort cloud comet discovered to date" (abstract)
- Target **C/2014 UN271 (Bernardinelli-Bernstein)**: coordinates not stated (tracked with JPL Horizons ephemerides)  
  > "We report ALMA observations taken near *r*~H~ = 16.6 au and geocentric distance $\Delta$ = 16.9 au." (Introduction); z/distance rH = 16.6 au, Delta = 16.9 au  
  > "We report ALMA observations taken near *r*~H~ = 16.6 au and geocentric distance $\Delta$ = 16.9 au." (Introduction); distance from JPL Horizons ephemerides  
  > "We report ALMA observations taken near *r*~H~ = 16.6 au and geocentric distance $\Delta$ = 16.9 au." (Introduction)

## Data provenance

- ALMA projects: 2023.1.00703.S
- bands: Band 6, 216-234 GHz, four non-contiguous spectral windows (58 MHz to 2 GHz wide)  
  > "using the ALMA 12 m array with the Band 6 receiver, covering frequencies between 216 and 234 GHz in four non-contiguous spectral windows ranging from 58 MHz to 2 GHz wide" (2 Observations and Data Reduction)
- frequencies and spectral setup: 244 kHz resolution for H2CO window, 31 kHz for CO window; 0.04-0.33 km/s velocity resolution  
  > "the frequency resolution was 244 kHz for the H$_2$CO spectral line window and 31 kHz for the CO spectral window" (2 Observations and Data Reduction)
- continuum bandwidth: _not stated_
- arrays: ALMA 12 m array, most compact configuration  
  > "We leveraged the highest spectral resolution and the most compact ALMA array configuration" (Introduction)
- configurations: _not stated_
- baselines: 15-312 m (Mar 8), 15-314/284 m (Mar 17)  
  > "15–312" (Table 2)
- angular resolution: 1.48''-2.55'' synthesized beam  
  > "The spatial scale (range in semi-minor and semi-major axes of the synthesized beam) was 1.48$''$ – 2.55$''$" (2 Observations and Data Reduction)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: 49 min per execution, 3 executions per date  
  > "*T*~int~ is the total on-source integration time." (Table 2)
- observing dates: UT 2024 March 8 and 17  
  > "We conducted pre-perihelion observations toward UN271 on UT 2024 March 8 and 17" (2 Observations and Data Reduction)
- pi or archival as stated: _not stated_
- Line: CO J=2-1 (not stated (230 GHz))
- Line: H2CO 3(0,3)-2(0,2) (not stated)
- Other facility **Las Cumbres Observatory (1-m, 2-m FTS MuSCAT4)**: g' and r' optical photometry Feb 3-Mar 24 2024 for lightcurve/outburst context  
  > "Optical observations of the comet were taken between 2024 February 03 and March 24 with the Las Cumbres Observatory network of telescopes" (2 Observations and Data Reduction)
- External data: Nucleus diameter 137±17 km, albedo 5.3%, beaming factor 1.175, emissivities, spectral index 1.93  
  > "providing a nucleus diameter 137 $\pm$ 17 km and a geometric albedo $p_V$ = (5.3 $\pm$ 1.2)%." (5 Analysis of Continuum Emission) [from (cite: Lellouch2022)]
- External data: Photodissociation rates  
  > "Photodissociation rates were adopted from (cite: Hrodmarsson2023)." (4.1) [from (cite: Hrodmarsson2023)]
- External data: Dust opacities at 1.2 mm (size index -3, max size 1 mm, 50% porosity)  
  > "We adopted dust opacities calculated by (cite: Boissier2012) at $\lambda$ = 1.2 mm for a size index of -3, a maximum size of 1 mm, and a dust porosity of 50%." (Continuum Modeling) [from (cite: Boissier2012)]
- External data: Hale-Bopp Q(CO)=3e27 s-1 at 14 au  
  > "$Q$(CO) = $3\times10^{27}$ s$^{-1}$ for Hale-Bopp at *r*~H~ = 14 au post-perihleion (cite: Biver2002)" (Active CO Fraction) [from (cite: Biver2002)]

## Processing

### Calibration

- pipeline or manual: ALMA pipeline calibration plus post-pipeline flux corrections  
  > "We examined the quasar fluxes and applied post-pipeline corrections to the flux calibration as detailed in Appendix [7](#sec:fluxcal)." (2 Observations and Data Reduction)
- casa version: CASA 6.6.1  
  > "Common Astronomy Software Applications (CASA) package version 6.6.1" (2 Observations and Data Reduction)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0334-4008 and J0538-4405 (Mar 8), J0519-4546 (Mar 17); J0538-4405 flux reset from 2.15 to 2.38 Jy via fifth-order polynomial fits (factor ~1.05)  
  > "Our procedure provides a flux of 2.38 Jy, which better fits the trend." (Flux Calibration)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: Högbom  
  > "We deconvolved the point-spread function with the Högbom algorithm, using natural visibility weighting" (2 Observations and Data Reduction)
- weighting robust: natural weighting  
  > "using natural visibility weighting" (2 Observations and Data Reduction)
- uv taper: 2'' Gaussian taper for March 17 CO image  
  > "We applied a 2$\ensuremath{''}$ Gaussian taper in the $uv$-plane to the March 17 CO image" (3.1)
- cell size: _not stated_
- image size: _not stated_
- masking: 10'' diameter mask on peak continuum position; threshold 2x rms  
  > "a 10$\ensuremath{''}$ diameter mask centered on the peak continuum position, and a flux threshold of twice the rms noise" (2 Observations and Data Reduction)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: Gaussian primary beam response  
  > "corrected for the (Gaussian) response of the ALMA primary beam" (2 Observations and Data Reduction)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Autocorrelation spectra recovered, extracted and calibrated  
  > "We recovered, extracted, and calibrated the autocorrelation spectra as in (cite: Cordiner2023)." (2.1) [from (cite: Cordiner2023)]
- Fourier-domain modeling of interferometric spectra  
  > "We chose to perform modeling of the interferometric spectra in the Fourier domain following (cite: Cordiner2023)" (CO Fourier Domain Modeling) [from (cite: Cordiner2023)]
- Continuum visibility fitting and NEATM nucleus modeling  
  > "following the methods of (cite: Lellouch2022), including the use of the Near Earth Asteroid Thermal Model" (Continuum Modeling) [from (cite: Lellouch2022)]
- Two-region coma model  
  > "We followed methods applied to CO-rich comets C/2016 R2 (PanSTARRS) and 29P/Schwassmann-Wachmann 1 (cite: Cordiner2022; Roth2023)" (4.1) [from (cite: Cordiner2022; Roth2023)]

### Not stated but needed to reproduce (our reading)

- Line-free channels and continuum subtraction method
- Image pixel/cell size and image size
- Exact spectral window frequencies and CO rest frequency
- Initial guesses and bounds for lmfit fits
- Choice of aperture/extraction for interferometric spectra fitted
- Pipeline version
- Calibrator catalog data used for polynomial fit details
- Phase center coordinates

## Analysis recipe

1. **Calibrate and image CO and continuum**: Standard CASA flagging/calibration, post-pipeline flux correction, Högbom clean with natural weighting, primary beam correction  
  > "The data were flagged, calibrated, and imaged using standard routines in Common Astronomy Software Applications (CASA) package version 6.6.1" (2 Observations and Data Reduction)
   - software: CASA
   - parameter: 10'' mask, threshold 2x rms  
  > "a 10$\ensuremath{''}$ diameter mask centered on the peak continuum position, and a flux threshold of twice the rms noise" (2 Observations and Data Reduction)
   - fitting: _not stated_
   - validation: Flux scale checked against ALMA calibrator catalog  
  > "We compared the 233 GHz flux predicted by the ALMA Flux Estimation algorithm for each quasar on the date of observations against the nearby measured values." (Flux Calibration)
2. **Extract autocorrelation spectra**: Recover flagged autocorrelations and convert to Jy using beam sizes and aperture efficiencies  
  > "The spectra were converted to a flux scale (Jy) using the beam sizes and aperture efficiencies in the ALMA Technical Handbook" (2.1)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
3. **Fit CO line with 3D radiative transfer and derive production rates and scale lengths**: SUBLIMED non-LTE model, two regions (jet and ambient), Haser distribution, vis_sample Fourier transform, least-squares fit to visibilities  
  > "We then performed least-squares fits of our radiative transfer models against the measured interferometric visibilities." (Fourier Domain Modeling)
   - software: SUBLIMED, vis_sample, lmfit
   - parameter: Lp=0 assumed for geometry; free Q1,Q2,v1,v2,gamma,phi,psi  
  > "allowing the molecular production rate, expansion speed, and jet geometry ($Q_1, Q_2, v_1, v_2, \gamma, \phi, \psi$) to vary as free parameters" (Fourier Domain Modeling)
   - assumption: Gas kinetic temperature 4 K  
  > "We assumed a gas kinetic temperature $T_{\mathrm{kin}}$ = 4 K" (Fourier Domain Modeling)
   - assumption: H2CO-CO collision cross-section 5e-14 cm-2 (thermalization approximation)  
  > "using an average collisional cross-section with CO of $5\times10^{-14}$ cm$^{-2}$" (4.1)
   - fitting: Levenberg-Marquardt least squares; uncertainties from covariance diagonal; Lp from delta chi2 curve (1 and 2.6 sigma at 1 and 6.63)  
  > "We obtained the 1$\sigma$ and 2.6$\sigma$ uncertainties from the values for $\Delta\chi^2$ = 1 (68% confidence) and 6.63 (99% confidence) thresholds." (Fourier Domain Modeling)
   - validation: Checked for background CO sources with Planck maps and SIMBAD  
  > "confirmed there were no known background sources within 100$\ensuremath{''}$" (4.1)
4. **H2CO upper limit**: Extract spectrum at nucleus, 3 sigma integrated intensity limit, assume direct release  
  > "We assumed direct nucleus release of H$_2$CO." (4.1.2)
   - software: SUBLIMED
   - fitting: _not stated_
   - validation: _not stated_
5. **Continuum visibility fits: nucleus size and dust coma mass**: lmfit fits to 233 GHz visibilities with point source, point+1/rho coma, and fixed max coma; NEATM diameters; coma dust mass from flux with opacities  
  > "We used the `lmfit` package to perform least squares fits to the 233 GHz continuum visibilities" (Continuum Modeling)
   - software: lmfit
   - parameter: Tss=95±9 K (NEATM) or 60 K (CO)  
  > "The resulting $T_{ss}$ is 95 $\pm$ 9 K on both dates." (Continuum Modeling)
   - assumption: Opacities 0.17-0.467 m2/kg; dust at equilibrium temperature  
  > "the derived opacities are in the range $1.70-4.67\times10^{-1}$ m$^2$ kg$^{-1}$" (Coma Dust Mass)
   - fitting: Least squares, chi2 comparison  
  > "Based on $\chi^2$ analysis, our March 8 data are best fit by a 101–129 km nucleus" (5)
   - validation: Compared with Lellouch et al. nucleus size  
  > "Overall, our values are in formal agreement with (cite: Lellouch2022) within 2$\sigma$." (5)
6. **Active CO fraction**: Cowan & A'Hearn sublimation with ice-sublimation code; A=Q/Z; f=A/surface area  
  > "The active area is calculated by dividing $Q$(CO) by $Z$, and the nucleus active fractional area is found by dividing the active area by the nucleus surface area." (Active CO Fraction)
   - software: Small-Bodies-Node/ice-sublimation
   - assumption: Visual albedo 0.05, IR emissivity 0.95  
  > "for a visual abledo of 0.05 and an infrared emissivity of 0.95" (Active CO Fraction)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 6.6.1: calibration and imaging  
  > "Common Astronomy Software Applications (CASA) package version 6.6.1" (2 Observations and Data Reduction)
- **SUBLIMED** : 3D non-LTE radiative transfer of coma  
  > "We modeled molecular line emission using the SUBLIMED three-dimensional radiative transfer code for cometary atmospheres" (4.1)
- **vis_sample** : Fourier transform of model cubes at observed uv coverage  
  > "We used the `vis_sample` program (cite: Loomis2018) to take the Fourier transform of our radiative transfer model cubes" (Fourier Domain Modeling)
- **lmfit** : Levenberg-Marquardt fits of line and continuum models  
  > "We used the `lmfit` application of the Levenberg-Marquardt minimization technique" (Fourier Domain Modeling)
- **BANZAI** : LCO image processing  
  > "All data were processed with the BANZAI pipeline" (2 Observations and Data Reduction)
- **Small-Bodies-Node/ice-sublimation** commit e20745b: CO sublimation rate per unit area  
  > "We used the Small-Bodies-Node/ice-sublimation code (cite: VanSelous2021) to calculate the average CO sublimation rate per surface unit" (Active CO Fraction)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Q(CO) March 8 (Lp<2500 km model) | 3.44 | 0.55 | 1e27 s-1 | 3 | 3.44 $\pm$ 0.55 |
| Q(CO) March 17 | 5.33 | 0.88 | 1e27 s-1 | 3 | 5.33 $\pm$ 0.88 |
| v1 sunward jet speed March 8 | 0.386 | 0.006 | km/s | 3 | 0.386 $\pm$ 0.006 |
| Jet half-opening angle March 8 | 27 | 5 | deg | 3 | 27 $\pm$ 5 |
| Lp 1 sigma upper limit March 8 | <2500 | not stated | km | 3 | our 1$\sigma$ upper limit on $L_p$ ($<$2,500 km for March 8) |
| Q(H2CO)/Q(CO) 3 sigma March 8 | <3.4 | not stated | % | 4 | $Q$(H$_2$CO)/$Q$(CO) $<$ 3.4% and $<$3.8% on March 8 and 17 |
| Nucleus diameter range | 101-151 | not stated | km | 5 | with nominal diameters ranging from 101 km – 151 km |
| Dust coma mass March 8 | 0.44-1.2 | 0.08-0.2 | 1e11 kg | 5 | $(0.44\pm0.08$)–$(1.2\pm0.2)$ |
| CO active fraction UN271 | 0.07 | not stated | % | 6 | 137 / 41 / 0.07 |
| Brightening Feb 24-29 | -0.44 | 0.06 | mag | 0 | the comet brightened by $-0.44\pm0.06$ mag |
| Surface temperature from CO speed | 60 | 2 (Mar 8), 3 (Mar 17) | K | 3 | give $T$ = $(60\pm2)$ K and $(60\pm3)$ K on March 8 and 17 |

## Qualitative findings

- CO outgassing showed multiple jets that evolved between epochs; continuum compact and unresolved  
  > "CO outgassing displayed multiple active jets which evolved from one epoch to the next." (abstract)

## Claim tuples

- H: Is CO in UN271 released directly from the nucleus or produced via coma chemistry? | E: Fit Lp from Fourier-domain radiative transfer modeling | R: Lp<2,500 km (Mar 8), no known parent with required photodissociation rate | F: Direct nucleus CO sublimation is a key activity driver | **supported**
- H: Is H2CO present? | E: Spectra at nucleus position | R: Q(H2CO)/Q(CO)<3.4% and <3.8% | F: H2CO not significant | **supported**
- H: Continuum comes from the large nucleus and possibly a dust coma | E: Visibility fits with NEATM | R: Nucleus 101-151 km; March 8 coma 0.4-1.2e11 kg | F: Results support a large nucleus, tentative coma on March 8 | **partially**
- H: Did UN271 outburst near the ALMA epochs? | E: LCO lightcurve | R: 0.44 mag brightening Feb 24-29 | F: Outburst in late February, returned to quiescence in March | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Fourier-domain modeling avoids imaging artifacts from incomplete uv sampling  
  > "to avoid the introduction of imaging artifacts owing to the incomplete $uv$ sampling inherent to interferometric observations" (CO Fourier Domain Modeling)
- Alternative: Modeling autocorrelation and interferometric spectra simultaneously was not done because they probe different coma scales  
  > "we elected to treat only the interferometric spectra for these reasons." (4.1)
- How they decided it was enough: _not stated_
- Limitation (authors): Two-component model is a simplification of the dual-jet geometry; March 17 S/N lower  
  > "Our two-component radiative transfer model is a simplification of this geometry" (4.1.1)
- Caveat (inferred, ours): Flux scale adjusted by ~5% for one calibrator, directly affects continuum nucleus size
- Caveat (inferred, ours): Dust masses depend strongly on assumed opacities and maximum size
- Caveat (inferred, ours): Single-epoch pair with low S/N on March 17
- Caveat (inferred, ours): Nucleus size inferred from tied assumptions from Lellouch et al.

## Reproducibility

- Data public (paper): ALMA project 2023.1.00703.S cited  
  > "ADS/JAO.ALMA #2023.1.00703.S and #2011.0.00001.CAL" (Acknowledgments)
- Products in archive: _not stated_
- Missing: Cell/image sizes, line-free channels
- Missing: Initial guesses for fits
- Missing: SUBLIMED version/setup details
- Missing: Calibrator catalog data used in flux correction
- Data volume (inferred): ~50-150 GB raw for six 12 m executions
- Score (inferred): 3/5, Data and software named with many modeling parameters, but imaging details and fit setups are incomplete.
- Rediscovery candidate: no, Requires SUBLIMED radiative transfer and unstated imaging details.

## Links

- Method: (cite: Cordiner2023) (Autocorrelation extraction and Fourier-domain modeling)
- Method: (cite: Cordiner2022) (SUBLIMED code)
- Method: (cite: Lellouch2022) (Continuum/NEATM methods and nucleus parameters)
- Companion: (cite: Lellouch2022) (Previous ALMA continuum observations of UN271)
- Companion: (cite: Kelley2022) (UN271 outbursts)
- Related: Las Cumbres Observatory network

## Checks

```json
{
 "quotes": 76,
 "quotes_ok": 76,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [
  "2011.0.00001.CAL"
 ],
 "numeric_results": 11,
 "numeric_problems": 0,
 "fill": {
  "facts": 86,
  "stated": 57,
  "rate": 0.663
 },
 "evidence_ok": true
}
```
