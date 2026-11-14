# DCO<SUP>+</SUP>, DCN, and N<SUB>2</SUB>D<SUP>+</SUP> reveal three different deuteration regimes in the disk around the Herbig Ae star HD 163296

`2017A&A...606A.125S` | Astronomy and Astrophysics 2017 | first author: Salinas, V. N. | arXiv: 1707.06475 | DOI: 10.1051/0004-6361/201731223

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks, astrochemistry
- Question: Constrain the radial extent of DCO+, DCN and N2D+ in the HD 163296 disk and spatially characterize the high and low temperature deuteration pathways  
  > "We aim to constrain the radial extent of main deuterated species; we are particularly interested in spatially characterizing the high and low temperature pathways for enhancing deuteration of these species." (abstract)
- Target **HD 163296**: coordinates RA 17h56m51.21s, Dec -21d57m22.0s (J2000)  
  > "HD163296 ($\rm\alpha_{2000}$ = ${\rm    17^h56^m51{s}21}$, $\delta_{2000}$ = $-21^\circ57'22{\ensuremath{''}}0$)" (2 Observations); "Its proximity (122 pc) makes it an excellent laboratory to study the spatial location of the different deuteration regimes in protoplanetary disks" (Introduction); z/distance 122 pc  
  > "HD163296 ($\rm\alpha_{2000}$ = ${\rm    17^h56^m51{s}21}$, $\delta_{2000}$ = $-21^\circ57'22{\ensuremath{''}}0$)" (2 Observations); "Its proximity (122 pc) makes it an excellent laboratory to study the spatial location of the different deuteration regimes in protoplanetary disks" (Introduction); distance from Perryman1997 (Hipparcos), cited with Qi2011, Mathews2013  
  > "HD163296 ($\rm\alpha_{2000}$ = ${\rm    17^h56^m51{s}21}$, $\delta_{2000}$ = $-21^\circ57'22{\ensuremath{''}}0$)" (2 Observations); "Its proximity (122 pc) makes it an excellent laboratory to study the spatial location of the different deuteration regimes in protoplanetary disks" (Introduction)

## Data provenance

- ALMA projects: 2013.1.01268.S
- bands: Band 6  
  > "using the Atacama Large (sub-)Millimeter Array (ALMA) in Band 6 as a part of Cycle 2" (2 Observations)
- frequencies and spectral setup: 7 spectral windows; three on DCO+, N2D+, DCN at 61 kHz resolution; 2 GHz continuum centered at 232.989 GHz  
  > "all of them at a resolution of 61 kHz. A final SPW contains wideband (2 GHz) continuum centered at 232.989 GHz." (2 Observations)
- continuum bandwidth: _not stated_
- arrays: thirty-three 12 m antennas  
  > "The total integration time on source was 4 hours and 43 min with thirty-three 12 m antennas." (2 Observations)
- configurations: _not stated_
- baselines: uv-distance 20–630 kλ  
  > "Baselines in the antenna array configuration correspond to a range in $uv$-distance of 20–630 k$\lambda$" (2 Observations)
- angular resolution: 0.53x0.42" (DCO+, DCN), 0.50x0.39" (N2D+) with natural weighting  
  > "| N$_2$D$^+$ J= 3–2 | 231.321 | 61.6$\pm$ 7.5 | 0$\ensuremath{''}$50$\times$0$\ensuremath{''}$39 | 3.37 |" (Table 1 (lines))
- max recoverable scale: _not stated_
- sensitivity: channel rms 3.25 (DCO+), 3.11 (DCN), 3.37 (N2D+) mJy/beam  
  > "| DCN J=3–2 | 217.238 | 104.4$\pm$ 5.6 | 0$\ensuremath{''}$53$\times$0$\ensuremath{''}$42 | 3.11 |" (Table 1 (lines))
- time on source: 4 h 43 min  
  > "The total integration time on source was 4 hours and 43 min with thirty-three 12 m antennas." (2 Observations)
- observing dates: 27-29 July 2014 (Cycle 2)  
  > "as a part of Cycle 2 on the 27th, 28th and 29th of July 2014" (2 Observations)
- pi or archival as stated: _not stated_
- Line: DCO+ J=3-2 (216.112 GHz)
- Line: DCN J=3-2 (217.238 GHz)
- Line: N2D+ J=3-2 (231.321 GHz)
- External data: Physical disk model (density, scale heights, stellar parameters)  
  > "We adopt the physical model used by (cite: Mathews2013)." (4.3 Physical model) [from (cite: Mathews2013)]
- External data: H13CO+ 3-2 (620) and H13CN 3-2 (170 mJy/beam km/s) integrated fluxes  
  > "H$^{13}$CO$^+$ $J$=3–2 (620 mJy beam$^{-1}$ km s$^{-1}$), H$^{13}$CN $J$=3–2 (170 mJy beam$^{-1}$ km s$^{-1}$) (cite: Huang2017)" (3.2 Column densities) [from (cite: Huang2017)]
- External data: N2H+ 3-2 integrated flux 520 mJy/beam km/s  
  > "N$_2$H$^+$ $J$=3–2 (520 mJy beam$^{-1}$ km s$^{-1}$) (cite: Qi2015)" (3.2 Column densities) [from (cite: Qi2015)]
- External data: 12C/13C ratio of 69  
  > "assuming a $^{12}$C/$^{13}$C ratio of 69 (cite: Wilson1999)" (3.2 Column densities) [from (cite: Wilson1999)]
- External data: Collisional rate coefficients (LAMBDA; N2H+/HCO+, HCN)  
  > "We use the rate coefficients from the Leiden Atomic and Molecular Database (cite: LAMBDA_database2005)" (4.4 Line excitation) [from (cite: LAMBDA_database2005)]
- External data: Stellar mass 2.3 Msun for Keplerian mask  
  > "using a stellar mass value of 2.3 M$_\odot$ (cite: vandenAncker1997)" (Appendix Keplerian Masking) [from (cite: vandenAncker1997)]

## Processing

### Calibration

- pipeline or manual: standard CASA reduction with ALMA calibration scripts  
  > "The data were calibrated following the standard CASA reduction as provided in the calibration scripts by ALMA." (2 Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J1733-1304 (1.329 Jy LSB, 1.255 Jy USB)  
  > "The quasar J1733-1304 was used as gain, bandpass and total flux calibrator with 1.329 Jy on the lower sideband and 1.255 Jy in the upper sideband." (2 Observations)
- flux scale uncertainty: _not stated_
- self calibration: applied as implemented by Carney et al. 2017  
  > "Self calibration was applied to the data as implemented by (cite: Carney2017)." (2 Observations)

### Imaging

- task: CLEAN task in CASA  
  > "imaged by the CLEAN task in CASA" (2 Observations)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "Line parameters of CLEAN images using natural weighting." (Table 1 (lines))
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: Keplerian mask for integrated intensity maps  
  > "This mask is constructed by calculating the projected Keplerian velocities of the disk and matching them with the expected Doppler shifted emission in the data’s spectral cube" (2 Observations)
- multiscale scales: _not stated_
- continuum subtraction: linear fit to line-free channels in the uv plane  
  > "were continuum subtracted in the visibility plane using a linear fit to the line-free channels" (2 Observations)
- line free channels: N2D+: channels 350–750 (one side of spectrum)  
  > "We fit the continuum only using the least noisy line-free channels from one side of the spectra (channels 350–750)" (2 Observations)
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Self-calibration procedure  
  > "Self calibration was applied to the data as implemented by (cite: Carney2017)." (2 Observations) [from (cite: Carney2017)]
- Physical disk model  
  > "We adopt the physical model used by (cite: Mathews2013)." (4.3 Physical model) [from (cite: Mathews2013)]
- Optically thin column density formula  
  > "consider the analytical formula from (cite: Remijan2003) for optically thin emission" (3.2 Column densities) [from (cite: Remijan2003)]

### Not stated but needed to reproduce (our reading)

- CASA version
- tclean/CLEAN parameters: cell size, image size, threshold, masks, channel width of cubes
- Line-free channels for DCO+ and DCN continuum subtraction
- Exact self-calibration solution intervals
- Stellar parameters/ RADMC inputs (only referenced to Mathews2013)
- Fitting algorithm and parameter grid for chi2 minimisation
- Inclination and position angle used for Keplerian mask and annuli

## Analysis recipe

1. **Keplerian-masked integrated intensity maps**: Mask pixels in each channel whose projected Keplerian velocity matches the channel Doppler shift, convolved with beam, then integrate  
  > "we first calculate the projected radial velocity on each pixel using a stellar mass value of 2.3 M$_\odot$" (Appendix Keplerian Masking)
   - software: CASA
   - parameter: stellar mass 2.3 Msun  
  > "using a stellar mass value of 2.3 M$_\odot$ (cite: vandenAncker1997)" (Appendix Keplerian Masking)
   - fitting: _not stated_
   - validation: S/N gain of ~2 compared to Yen2016 stacking factor ~4  
  > "In contrast our method achieves an increase in S/N of a factor of $\sim$ 2" (Appendix Keplerian Masking)
2. **Radial profiles**: Average over concentric ellipsoidal annuli, error from standard deviation  
  > "This profile is constructed taking the average value of concentric ellipsoid annuli and their error is taken from the standard deviation." (3.1 Detections)
   - fitting: _not stated_
   - validation: _not stated_
3. **Disk-averaged column densities and deuterium fractionation**: Optically thin formula of Remijan 2003 with CDMS parameters; Df from H13CO+, H13CN, N2H+ literature fluxes  
  > "The partition function (Q$_{rot}$), upper energy level (E$_u$ K), line strength (S$_{ij}$) and dipole moment ($\mu$ Debye) were taken from the CDMS database." (3.2 Column densities)
   - parameter: Tex 10 and 25 K for N2D+; 25 and 80 K for DCN and DCO+  
  > "10 and 25 K for N$_2$D$^+$ and 25 and 80 K for DCN and DCO$^+$" (3.2 Column densities)
   - assumption: 12C/13C = 69; optically thin emission; Df are lower limits  
  > "These D$_{\rm f}$ values are only lower limits as the species might not be spatially co-located." (3.2 Column densities)
   - fitting: _not stated_
   - validation: _not stated_
4. **Excitation temperature profile**: Non-LTE LIME models with constant abundance (Tex=25 K disk average), averaging Tex of points z<10h(R)  
  > "To construct the radial excitation temperature profile we take the average excitation temperature of the points below $z<10\times h(R)$" (4.4 Line excitation)
   - software: LIME, RADMC
   - parameter: 50000 grid points, 12 iterations  
  > "We manually set the number of iterations to 12 and confirm convergence by comparing consecutive iterations." (4.4 Line excitation)
   - assumption: Tgas = Tdust; N2H+ and HCN rate coefficients used for N2D+ and DCN  
  > "assuming T$_{\rm gas}=$T$_{\rm dust}$" (4.3 Physical model)
   - fitting: _not stated_
   - validation: convergence checked by comparing consecutive iterations  
  > "We manually set the number of iterations to 12 and confirm convergence by comparing consecutive iterations." (4.4 Line excitation)
5. **Fit parametric abundance ring models**: Compute emission profile from column density and Tex via Remijan equation, make 2D image, convolve with beam, minimise chi2 against integrated intensity maps  
  > "We minimize ${ \chi^2=(F_{\rm obs}(x,y)-F_{\rm model}(x,y))^2/\sigma(x,y)^2}$ values" (4.6 Best-fit parameters)
   - parameter: DCO+: 7 parameters (Rin, R1, R2, three abundances); DCN, N2D+: Rin, Rout, X  
  > "Our model uses a set of seven parameters describing three regions" (4.4 abundance models)
   - assumption: vertically averaged abundances, no vertical distribution  
  > "We do not consider a vertical distribution of the DCO$^+$ and DCN molecules." (4.6 Best-fit parameters)
   - fitting: chi2 minimum of the explored parameter space; formal errors at 90% confidence  
  > "The formal errors are calculated at 90% confidence levels." (Table 3)
   - validation: Compared different DCO+ ring/gap configurations; degeneracy acknowledged  
  > "In the case of DCO$^+$ the location of the different radial zones are degenerate." (4.6 Best-fit parameters)

## Software

- **CASA** : Calibration, continuum subtraction, CLEAN imaging  
  > "imaged by the CLEAN task in CASA" (2 Observations)
- **LIME** : Non-LTE excitation temperature profile  
  > "We used LIME (cite: Brinch2010), a 3D radiative transfer code in non-LTE" (4.4 Line excitation)
- **RADMC** : Gas temperature profile of physical model  
  > "The gas temperature profile was computed by the 2D radiative transfer code RADMC (cite: Dullemond2004b)" (4.3 Physical model)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| DCO+ integrated intensity | 1270.45 | 5.8 | mJy km/s | 1 | / DCO$^+$ J=3–2 / 216.112 / 1270.45$\pm$ 5.8 / |
| DCN integrated intensity | 104.4 | 5.6 | mJy km/s | 1 | / DCN J=3–2 / 217.238 / 104.4$\pm$ 5.6 / |
| N2D+ integrated intensity | 61.6 | 7.5 | mJy km/s | 1 | / N$_2$D$^+$ J= 3–2 / 231.321 / 61.6$\pm$ 7.5 / |
| DCO+/HCO+ (25 K) | 0.05 | 0.01 | dimensionless | 3 | /   25 K   /    0.05$\pm$0.01    /  0.02$\pm$0.01  /     0.45$\pm$0.21     / |
| N2D+/N2H+ (10 K) | 0.34 | 0.15 | dimensionless | 3 | /   10 K   /         \-          /       \-        /     0.34$\pm$0.15     / |
| DCO+ column density (25 K) | 1.68e12 | 0.01e12 | cm^-2 | 3 | / 25 K / 1.68$\pm 0.01\times 10^{12}$ / |
| DCO+ ring radii Rin, R1, R2, Rout | 50, 118, 245, 316 | +5/-3, +4/-5, +3/-13, +3/-10 | AU | 5 | $R_{\rm in}$=50$^{+5}_{-3}$ AU, $R_1$=118$^{+4}_{-5}$ AU , $R_2$=245$^{+3}_{-13}$ AU and $R_{\rm out}$=316$^{+3}_{-10}$ AU |
| DCN ring Rin, Rout | 51, 201 | +/-6, +15/-24 | AU | 5 | / $R_{\rm in}$ / 51$^{+6}_{-6}$ AU / 139$^{+5}_{-4}$ AU / 50$^{+5}_{-3}$ AU / |
| N2D+ ring Rin, Rout | 139, 287 | +5/-4, +15/-21 | AU | 5 | / $R_{\rm out}$ / 201$^{+15}_{-24}$ AU / 287$^{+15}_{-21}$ AU / 316$^{+3}_{-10}$ AU / |
| DCN abundance Xhigh | 7.5e-13 | +/-0.9e-13 | relative to H2 | 5 | constant abundance $X_{\rm high}$=7.5$^{+0.9}_{-0.9}\times$10$^{-13}$ |

## Qualitative findings

- DCO+ and DCN inner depression is attributed to optically thick dust within ~50 AU  
  > "We conclude that our $R_{\rm  in}$ parameter is tracing this optically thick dust region." (5.1 The inner depression)
- DCO+ alone cannot trace the CO snowline  
  > "Without previous knowledge, DCO$^+$ alone cannot trace the location of the CO snowline." (5.2)

## Claim tuples

- H: DCN, N2D+ and DCO+ trace distinct deuteration regimes | E: Radial ring abundance models fit to Keplerian-masked integrated intensity maps | R: DCO+ needs three rings (50-118-245-316 AU); DCN ring 51-201 AU; N2D+ ring 139-287 AU | F: First two DCO+ rings correlate with high and low temperature pathways | **supported**
- H: Df values consistent with previous estimates | E: Optically thin column densities and ratios with literature H13CO+, H13CN, N2H+ | R: DCO+/HCO+ 0.05, DCN/HCN 0.02, N2D+/N2H+ 0.34-0.45 | F: Agree with earlier values; N2D+ a good tracer of the cold outer disk | **supported**
- H: Inner depression arises from optically thick dust | E: Compared continuum brightness temperature with Isella2016 | R: Peak continuum 25 K here vs 55 K at higher resolution | F: Depression due to optically thick dust, not chemistry | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: DCO+ models with gaps between rings fit equally well; resolution cannot distinguish them  
  > "The modest spatial resolution of our data cannot distinguish between these models." (4.6 Best-fit parameters)
- How they decided it was enough: _not stated_
- Limitation (authors): N2D+ is weak, on edge of atmospheric feature, continuum subtraction less accurate  
  > "The N$_2$D$^+$ ($J$=3–2) emission is sitting on the edge of a strong atmospheric feature at high $T_{\rm sys}$." (2 Observations)
- Limitation (authors): Isothermal vertical temperature assumption and no vertical abundance distribution  
  > "A drawback of this approach is that assuming an isothermal vertical structure of the temperature profile might not properly describe the vertical region over which the molecules extend." (4.4 Line excitation)
- Caveat (inferred, ours): No MCMC; chi2 minimum with 90% errors, method of error estimation unclear
- Caveat (inferred, ours): Radial profiles of weak lines (4-5 sigma) drive model structure
- Caveat (inferred, ours): Df uses literature fluxes from different beams and observations

## Reproducibility

- Data public (paper): Project code given; ALMA data acknowledged  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA# 2013.1.01268.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: CASA version and clean parameters
- Missing: chi2 fitting algorithm and grid
- Missing: Inclination/PA used
- Missing: Self-calibration details (in Carney2017)
- Data volume (inferred): ~50-100 GB raw
- Score (inferred): 3/5, Data public and approach clear, but imaging and fitting details missing.
- Rediscovery candidate: no, Imaging and fitting recipe is incomplete.

## Links

- Method: (cite: Carney2017) (Self-calibration implementation)
- Method: (cite: Mathews2013) (Physical model of HD 163296)
- Method: (cite: Remijan2003) (Column density formula)
- Companion: (cite: Yen2016) (Earlier ALMA DCO+, DCN, N2D+ observations of HD 163296)
- Companion: (cite: Carney2017) (H2CO from same dataset)

## Checks

```json
{
 "quotes": 75,
 "quotes_ok": 75,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 10,
 "numeric_problems": 0,
 "fill": {
  "facts": 82,
  "stated": 54,
  "rate": 0.659
 },
 "evidence_ok": true
}
```
