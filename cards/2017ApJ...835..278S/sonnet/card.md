# Physical Properties of Molecular Clouds at 2 pc Resolution in the Low-metallicity Dwarf Galaxy NGC 6822 and the Milky Way

`2017ApJ...835..278S` | The Astrophysical Journal 2017 | first author: Schruba, Andreas | arXiv: 1701.02748 | DOI: 10.3847/1538-4357/835/2/278

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, star_formation, milky_way_ism
- Question: How do the structure of CO-bright clumps and the CO-to-H2 conversion in the low-metallicity dwarf galaxy NGC 6822 compare with Milky Way clouds, and what does this imply for molecular gas depletion times?  
  > "With the goal of a statistical measurement of the structure of CO in low metallicity clouds over a wide area, we used ALMA to map CO(2-1) emission across five star-forming complexes" (1 Introduction)
- Target **NGC 6822**: coordinates RA 19h 44m 57.74s, Dec -14d 48m 12.4s  
  > "Distance | $474 \pm 13$ kpc | (cite: Rich14)" (Table 1); "R. A. $^{a}$ | 19h 44m 57.74s | NED" (Table 1); z/distance 474 ± 13 kpc  
  > "Distance | $474 \pm 13$ kpc | (cite: Rich14)" (Table 1); "R. A. $^{a}$ | 19h 44m 57.74s | NED" (Table 1); distance from Rich14  
  > "Distance | $474 \pm 13$ kpc | (cite: Rich14)" (Table 1); "R. A. $^{a}$ | 19h 44m 57.74s | NED" (Table 1)

## Data provenance

- ALMA projects: 2013.1.00351.S
- bands: Band 6 (1.3 mm), Cycle 1  
  > "We observed five fields in NGC 6822 with ALMA in Cycle 1 using the 1.3-mm Band 6 receivers" (2 ALMA Survey)
- frequencies and spectral setup: CO(2-1) window: 0.938 GHz bandwidth, 244 kHz channels, centered 230.612 GHz; three continuum windows of 2 GHz at 229.196, 215.063, 213.188 GHz  
  > "This window has bandwidth $0.938$ GHz with channel width $244$ kHz ($\approx 0.32$ km s$^{-1}$) and is centered at 230.612 GHz." (2 ALMA Survey); "centered at 229.196 GHz, 215.063 GHz, and 213.188 GHz" (2 ALMA Survey)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 15-438 m  
  > "The ALMA observations include baselines of $15{-}438$ m length." (2 ALMA Survey)
- angular resolution: average beam FWHM 0.9" ≈ 2.0 pc  
  > "The average synthesized beam size has FWHM $0.9\ensuremath{''} \approx 2.0$ pc" (2 ALMA Survey)
- max recoverable scale: ≈ 11" ≈ 25 pc  
  > "maximum recoverable scale of about $0.6 \lambda / L_\mathrm{min} \approx 11\ensuremath{''} \approx 25$ pc" (2 ALMA Survey)
- sensitivity: rms ~0.5 K; 1σ ~0.9 K km/s over 5 km/s  
  > "the achieved rms brightness sensitivity is ${\sim} 0.5$ K." (2 ALMA Survey)
- time on source: _not stated_
- observing dates: 2014-03-23 to 2014-03-25  
  > "Field 1 | uid://A002/X7d44e7/X1d11 | 2014-03-23 10:06:34" (Table 3)
- pi or archival as stated: PI A. Schruba  
  > "(project code: 2013.1.00351.S; PI. A. Schruba)" (2 ALMA Survey)
- Line: CO J=2-1 (230.538 GHz)
- Other facility **IRAM 30-m**: CO(2-1) map used to estimate flux recovery  
  > "We can estimate the amount of missing flux from existing IRAM 30-m CO(2-1) mapping at $15^{\prime\prime} \approx 36$ pc resolution (cite: Gratier10a)" (2 ALMA Survey)
- Other facility **VLA LITTLE THINGS**: HI maps  
  > "The H$\,$I data are from the Very Large Array (VLA) taken as part of the LITTLE THINGS survey (cite: Hunter12)." (3.2 Atomic Gas and Dust)
- Other facility **Herschel**: dust maps (SPIRE 350 um used as dust proxy)  
  > "we reverted using SPIRE’s $350~\ensuremath{\mu}m$ band as dust proxy" (3.2 Atomic Gas and Dust)
- Other facility **Spitzer**: 8 and 24 um maps  
  > "both from the *Spitzer* Infrared Nearby Galaxy Survey (cite: Kennicutt03a)" (3.1 Tracers of Recent Star Formation)
- External data: Halpha map  
  > "the H$\alpha$ map (cite: deBlok06a) traces the distribution of recent star formation" (3.1 Tracers of Recent Star Formation) [from (cite: deBlok06a)]
- External data: WLM CO clump measurements  
  > "we include their measurements for WLM as listed in their Table 1." (3.3 Matched Resolution Comparison Data) [from (cite: Rubio15)]
- External data: Outer Galaxy clump data (FCRAO)  
  > "These data, as reprocessed by (cite: Brunt03), have a resolution of $100\ensuremath{''} \times 0.98$ km s$^{-1}$." (3.3 Matched Resolution Comparison Data) [from (cite: Heyer01; Brunt03)]

## Processing

### Calibration

- pipeline or manual: analyst-calibrated data sets (QA2) processed in CASA  
  > "using the “analyst-calibrated” data sets created with help of the QA2 script-generator tool" (2 ALMA Survey)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Titan (Butler-JPL Horizons-2012) for Fields 2,3,4; same scale imposed on Fields 1,5 via quasars  
  > "Titan was observed during three observing sessions (Fields 2, 3, 4) to set the absolute flux scale with an estimated uncertainty of $5\%$" (2 ALMA Survey)
- flux scale uncertainty: 5%  
  > "to set the absolute flux scale with an estimated uncertainty of $5\%$" (2 ALMA Survey)
- self calibration: _not stated_

### Imaging

- task: CASA clean, standard parameters; mfs for continuum  
  > "The calibrated visibilities were imaged and deconvolved with the `clean` task using standard parameters." (2 ALMA Survey)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "imaged the data using natural weighting" (2 ALMA Survey)
- uv taper: _not stated_
- cell size: 0.15" pixel; channel width 0.635 km/s  
  > "We chose an angular pixel scale of $0.15\ensuremath{''}$ and a channel width of $0.635$ km s$^{-1}$" (2 ALMA Survey)
- image size: _not stated_
- masking: peaks >5σ in two adjacent channels grown to neighbors >1.5σ  
  > "searching for emission peaks above $5\sigma$ in two adjacent channels which we then grow to include all neighboring pixels above $1.5\sigma$" (2 ALMA Survey)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: single fixed elliptical Gaussian per mosaic; 0.83-1.03" mean beam  
  > "We restored the deconvolved image using a single fixed elliptical Gaussian for each mosaic, so that each image has a single beam." (2 ALMA Survey)
- final rms: 12.4-18.7 mJy per channel (0.27-0.63 K)  
  > "Rms Noise | milly Jy | 18.7 | 14.1 | 14.9 | 12.4 | 13.1" (Table 2)

### Inherited from earlier work

- Cloud property measurement algorithm details  
  > "For details on `CPROPS`, we refer to (cite: Rosolowsky06), (cite: Leroy15a), and A. Schruba et al. (in preparation)." (3.4 Cloud Property Measurements) [from (cite: Rosolowsky06; Leroy15a)]
- Clump dynamical-state analysis  
  > "Following an analysis presented by (cite: Rubio15) for WLM, we evaluate the dynamical state of the clumps in three ways" (5.1 The CO-bright Clumps) [from (cite: Rubio15)]
- Joint alpha_CO and GDR solution  
  > "If we carry out a joint solution for $\alpha_\mathrm{CO}$ and GDR across the galaxy (cite: Sandstrom13; Leroy11)" (4.2 Atomic-Molecular Complexes) [from (cite: Sandstrom13; Leroy11)]
- Depletion-time bias model  
  > "we use their Eq. 16" (5.5 Star-forming Gas Content) [from (cite: Kruijssen14a)]

### Not stated but needed to reproduce (our reading)

- Exact clean parameters (threshold, niter, mask, mosaic gridding)
- Line-free channels / continuum subtraction for CO cube
- CASA version and pipeline version
- CPROPS settings (S/N cuts, parameters, extrapolation)
- Details of convolution of Milky Way data and HI/dust regridding
- Herschel background/cirrus handling for 350 um map and conversion to dust mass
- Public availability of the HI map (not released)

## Analysis recipe

1. **Image CO(2-1) and continuum cubes**: CASA clean, natural weighting, single restoring beam  
  > "The calibrated visibilities were imaged and deconvolved with the `clean` task using standard parameters." (2 ALMA Survey)
   - software: CASA
   - parameter: 0.15" pixels, 0.635 km/s channels  
  > "We chose an angular pixel scale of $0.15\ensuremath{''}$ and a channel width of $0.635$ km s$^{-1}$" (2 ALMA Survey)
   - fitting: _not stated_
   - validation: Flux recovery 73±20% vs IRAM 30-m in Field 2  
  > "For this field, the ALMA observations recover $(73 \pm 20)\%$ of the single-dish flux." (2 ALMA Survey)
2. **Estimate global CO luminosity**: Aperture correction using Halpha and 24um fractions of fields, plus flux recovery correction  
  > "Our “aperture correction” is the ratio of total star formation tracer luminosity of the galaxy to the luminosity inside our fields." (4.1 Total CO Luminosity)
   - assumption: R21 = 1.0 (0.7-1.0 for CO(1-0))  
  > "therefore, we adopt $R_{21} = 1.0$ throughout the paper" (3.5 CO Excitation)
   - fitting: _not stated_
   - validation: Compared to Gratier et al. IRAM estimate  
  > "This value agrees within the uncertainty with a similarly derived estimate by (cite: Gratier10a)" (4.1 Total CO Luminosity)
3. **Derive complex gas masses and alpha_CO from dust**: GDR from outer 50 pc ring, background subtraction, dust-traced gas minus HI gives H2; alpha_CO = H2/L_CO  
  > "we estimate the GDR by comparing $\Sigma_\mathrm{atom}$ and $\Sigma_\mathrm{dust}$ in regions where atomic gas makes up most of the gas." (4.2 Atomic-Molecular Complexes)
   - parameter: maps at 25" ≈ 57 pc resolution, SPIRE 350 um as dust proxy  
  > "The H$\,$I and dust maps are evaluated at a common resolution of $25\ensuremath{''} \approx 57$ pc" (3.2 Atomic Gas and Dust)
   - assumption: optically thin HI, no opacity correction  
  > "we adopt the standard assumption of optically thin H$\,$I emission and work without opacity correction" (3.6 H I Opacity Correction)
   - fitting: _not stated_
   - validation: Compared with three dust models agreeing within factor of a few  
  > "results derived from more complex dust modeling (i.e., modified blackbody, (cite: Galliano11), or (cite: DraineLi07) model) agree within a factor of a few" (3.2 Atomic Gas and Dust)
4. **Correlate CO with 8um, 24um, Halpha**: 80% CO flux threshold contours, area fractions, Spearman rank correlation  
  > "we determine the maximum intensity contour for each tracer that encompasses $80\%$ of the total CO emission" (4.3 Coincidence of CO)
   - fitting: _not stated_
   - validation: _not stated_
5. **Identify CO clumps and measure properties**: CPROPS: size, line width, luminosity; mean over methods, with corrections for sensitivity and resolution; virial mass Mvir = 1040 R sigma^2  
  > "The values reported here are the mean across all of these characterization methods." (3.4 Cloud Property Measurements); "$M_\mathrm{vir}~[\mbox{$\rm M_{\odot}$}] = 1040 R \sigma^2~[\mathrm{pc}\,\mathrm{km}^2\,\mathrm{s}^{-2}]$" (4.5 CO Clump Properties)
   - software: CPROPS
   - assumption: alpha_CO = 4.35 Msun pc^-2 (K km/s)^-1, R21 = 1 for luminous mass  
  > "using a fiducial Galactic CO-to-H$_2$ conversion factor $\alpha_\mathrm{CO} = 4.35$ M$_{\odot}$ pc$^{-2}$ (K km s$^{-1}$)$^{-1}$ and $R_{21} = 1$" (4.5 CO Clump Properties)
   - fitting: Power-law fits to clumps  
  > "Black lines show power law fits to the NGC 6822 clumps" (4.5 CO Clump Properties)
   - validation: Compared to WLM and outer Milky Way clumps; scatter between methods as uncertainty  
  > "We adopt the scatter in results from different measurement approaches as our best estimate of the uncertainty" (3.4 Cloud Property Measurements)
6. **Bias-corrected molecular depletion time**: Kruijssen & Longmore 2014 model fit constrained at 100 pc and 1.6 kpc apertures  
  > "The model is constrained at small aperture size ($l_\mathrm{ap} \approx 100$ pc) by the average $M_\mathrm{mol}$ and $\mathit{SFR}$ for the star-forming complexes" (5.5 Star-forming Gas Content)
   - parameter: t_gas=35 Myr, t_over=5 Myr, t_star=10 Myr, lambda=400 pc, beta=1  
  > "separation of SF regions $\lambda = 400$ pc (estimated from H$\alpha$ map); fraction of gas decrease during SF process $\beta = 1$" (5.5 Star-forming Gas Content)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : calibration/imaging  
  > "The data were processed in the Common Astronomy Software Applications package (cite: Petry12)" (2 ALMA Survey)
- **CPROPS** updated version (cpropstoo): identify clumps and measure size, line width, luminosity  
  > "we use an updated version of the `CPROPS` algorithm" (3.4 Cloud Property Measurements)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Number of CO clumps | ~150 | not stated | clumps | 5 | We identify and measure the properties of ${\sim} 150$ of these roughly pc-scale “clumps,” |
| Global CO(2-1) luminosity of NGC 6822 | 6-10 x 10^4 | not stated | K km/s pc^2 | 2 | a best-estimate global CO(2-1) luminosity of NGC 6822 of $\sim 6{-}10 \times 10^4$ K km s$^{-1}$ pc$^2$ |
| Joint alpha_CO (2-1) | 110 | ±30 | Msun pc^-2 (K km/s)^-1 | 3 | $\delta_\mathrm{GDR} = 320 \pm 80$ and $\alpha_\mathrm{CO} = 110 \pm 30$ |
| alpha_CO Fields 2 & 4 | 85 | ±25 | Msun pc^-2 (K km/s)^-1 | 3 | we determine $\alpha_\mathrm{CO} = 85 \pm 25$ M$_{\odot}$ pc$^{-2}$ (K km s$^{-1}$)$^{-1}$ |
| Mean gas-to-dust ratio | 380 | ±70 | dimensionless | 3 | we find $\delta_\mathrm{GDR} = 380 \pm 70$ |
| Flux recovery in Field 2 | 73 | ±20 | % | 1 | the ALMA observations recover $(73 \pm 20)\%$ of the single-dish flux |
| Molecular depletion time of complexes | ~360 | not stated | Myr | 3 | present day star formation will consume the molecular gas content of the complexes in ${\sim} 360$ Myr |
| Global molecular depletion time (bias-corrected) | ~2 | not stated | Gyr | 6 | $t_\mathrm{dep,\, gal} \approx 2$ Gyr |
| Mean clump radius / velocity dispersion | R≈2.3 pc, sigma_v≈1.1 km/s | not stated | pc; km/s | 5 | These CO-bright clumps have an average size of $R \approx 2.3$ pc, velocity dispersion of $\sigma_\mathrm{v} \approx 1.1$ km s$^{-1}$ |

## Qualitative findings

- CO correlates with 8 um better than 24 um and anti-correlates with Halpha at pc scales  
  > "CO emission correlates with $8\,\ensuremath{\mu}m$ emission better than with $24\,\ensuremath{\mu}m$ emission and anti-correlates with H$\alpha$" (abstract)

## Claim tuples

- H: Are CO-bright clumps in a low-metallicity dwarf similar to Milky Way clumps? | E: CPROPS clump measurements at 2 pc compared to WLM and outer Galaxy | R: Sizes ~2-3 pc, line widths ~1 km/s; differences ≲2 in virial mass/surface brightness | F: Clump properties largely unaffected by 1/5 solar metallicity | **supported**
- H: Does alpha_CO depend on spatial scale at low metallicity? | E: Dust-based alpha_CO for complexes vs virial for clumps | R: alpha_CO ~20-25x Galactic for complexes, near Galactic in clumps | F: Strong dependence on scale and evolutionary state | **supported**
- H: Is the molecular depletion time short in dwarf galaxies? | E: Kruijssen & Longmore bias model applied to targeted complexes | R: Complexes 360 Myr; global ~2 Gyr | F: Global depletion time may be as long as in massive disks | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Dust used since CO traces only dense gas at low metallicity  
  > "We use dust, combined with a gas-to-dust ratio, $\delta_\mathrm{GDR}$, to trace the total gas reservoir" (4.2 Atomic-Molecular Complexes)
- Alternative: Recent starburst explanation for short depletion time rejected  
  > "There is no evidence that NGC 6822 has recently undergone a galaxy-wide starburst." (5.5 Star-forming Gas Content)
- How they decided it was enough: _not stated_
- Limitation (authors): Dust maps uncertain (Galactic cirrus, Herschel issues), dominating the error budget  
  > "This uncertainty dominates the error budget in our analysis of dust-inferred gas masses." (3.2 Atomic Gas and Dust)
- Limitation (authors): Missing flux on large scales  
  > "emission extending over scales larger than the maximum recoverable scale of about $0.6 \lambda / L_\mathrm{min} \approx 11\ensuremath{''} \approx 25$ pc is missing in our data sets" (2 ALMA Survey)
- Caveat (inferred, ours): Dust-based alpha_CO rests on a poorly constrained 350 um proxy and the assumption that the outer ring is atomic
- Caveat (inferred, ours): Depletion-time bias model parameters are rough estimates
- Caveat (inferred, ours): No ACA/total-power combination; flux recovery estimated from one field

## Reproducibility

- Data public (paper): ALMA project code given; HI map not publicly released  
  > "Due to calibration complications, these were not released with the rest of the survey" (3.2 Atomic Gas and Dust)
- Products in archive: _not stated_
- Code: CPROPS available at github cpropstoo  
  > "https://github.com/akleroy/cpropstoo/" (footnote 5)
- Missing: CASA/clean parameters
- Missing: CPROPS configuration
- Missing: Herschel dust maps and HI map provided privately
- Missing: Clump catalog is in online machine-readable table only
- Data volume (inferred): ~tens to 100 GB raw for 5 mosaics of 52 pointings
- Score (inferred): 3/5, ALMA data public but imaging and CPROPS settings are vague, and dust/HI inputs are private.
- Rediscovery candidate: no, Key dust-based results rely on privately provided maps and underspecified processing.

## Links

- Method: Rosolowsky & Leroy 2006 (cite: Rosolowsky06) (CPROPS algorithm)
- Method: Kruijssen & Longmore 2014 (cite: Kruijssen14a) (depletion time bias model)
- Companion: Rubio et al. 2015 (cite: Rubio15) (WLM CO clumps comparison)
- Related: LITTLE THINGS
- Related: Herschel Dwarf Galaxy Survey
- Related: SINGS/Spitzer

## Checks

```json
{
 "quotes": 78,
 "quotes_ok": 78,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [
  "2013.1.00351.S"
 ],
 "obscore_codes_not_in_card": [
  "2012.1.00336.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 9,
 "numeric_problems": 0,
 "fill": {
  "facts": 85,
  "stated": 58,
  "rate": 0.682
 },
 "evidence_ok": true
}
```
