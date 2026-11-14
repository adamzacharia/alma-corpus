# The Northern arc of ∊ Eridani's Debris Ring as seen by ALMA

`2017MNRAS.469.3200B` | Monthly Notices of the Royal Astronomical Society 2017 | first author: Booth, Mark | arXiv: 1705.01560 | DOI: 10.1093/mnras/stx1072

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: debris_disks, exoplanets
- Question: What are the geometry, width and structure of the epsilon Eri debris ring at 1.3 mm, what do they imply for planets, and is there emission at the star, interior dust or CO gas?  
  > "We use a forward modelling technique to determine the geometric properties of the disc. We compare these results with prior observations and discuss the implications for planets in the system" (Introduction)
- Target **epsilon Eridani**: coordinates pointing 03:32:54.8535 -09:27:11.438 (J2000), 18'' north of the star  
  > "$\alpha=03:32:54.8535$; $\delta=-09.27.11.438$ (J2000), 18$''$ to the North of the star" (Observations); "At a distance of 3.2 pc, the K2V star $\epsilon$ Eridani is the closest extrasolar system known to host a debris disc" (Introduction); z/distance 3.2 pc  
  > "$\alpha=03:32:54.8535$; $\delta=-09.27.11.438$ (J2000), 18$''$ to the North of the star" (Observations); "At a distance of 3.2 pc, the K2V star $\epsilon$ Eridani is the closest extrasolar system known to host a debris disc" (Introduction); distance from _not stated_

## Data provenance

- ALMA projects: 2013.1.00645.S
- bands: Band 6 (1.34 mm)  
  > "The data were taken in band 6 (1.34 mm) on the 17th and 18th January 2015" (Observations)
- frequencies and spectral setup: One SPW at CO(2-1) 230.538 GHz with 3840 x 0.5 MHz channels; three SPWs at 232, 219, 217 GHz with 128 x 16 MHz channels  
  > "one spectral window, centred at the CO(2-1) line at 230.538 GHz, had 3840 channels of width 0.5 MHz (0.6 kms$^{-1}$) and the other three spectral windows, centred at 232, 219 and 217 GHz" (Observations)
- continuum bandwidth: 7.875 GHz  
  > "we can, therefore, use the full bandwidth of all four channels adding up to 7.875 GHz" (Observations)
- arrays: _not stated_
- configurations: compact configuration  
  > "The observations were taken whilst the array was in a compact configuration with baselines between 15 and 350 m." (Observations)
- baselines: 15-350 m  
  > "baselines between 15 and 350 m" (Observations)
- angular resolution: 1.6'' x 1.1'', PA 92 deg (natural weighting)  
  > "The resulting synthesised beam has a size 1.6$''$$\times$1.1$''$ with a position angle of 92$^\circ$ E of N." (Observations)
- max recoverable scale: ~18'' (shortest baseline 15 m)  
  > "has a shortest baseline of 15 m meaning that we are not sensitive to emission on scales larger than 18$''$" (Disc flux density)
- sensitivity: continuum RMS 14 uJy/beam; line RMS 0.98 mJy/beam per 1.27 km/s channel  
  > "We find this to be $\sigma=14$ $\mu$Jy beam$^{-1}$." (Observations); "No spectral lines were detected down to an RMS sensitivity per beam of 0.98 mJy beam$^{-1}$ in a 1.27 km s$^{-1}$ wide channel." (Observations)
- time on source: 4.4 hours  
  > "The total time on target was 4.4 hours." (Observations)
- observing dates: 17-18 January 2015  
  > "The data were taken in band 6 (1.34 mm) on the 17th and 18th January 2015" (Observations)
- pi or archival as stated: Project 2013.1.00645.S, PI A. Jordán (an author)  
  > "as part of the project 2013.1.00645.S (PI: A. Jordán)" (Observations)
- Line: CO J=2-1 (230.538 GHz)
- External data: Stellar photosphere flux 530±11 uJy at 1.3 mm (Kurucz model)  
  > "The flux density of the stellar photosphere at 1.3 mm is expected to be $530\pm11\mu$Jy based on a Kurucz atmosphere model (cite: macgregor15)" (Stellar flux) [from (cite: macgregor15)]
- External data: Schechter galaxy-count parameters at 1.3 mm: phi*=1800±400 deg^-2, S*=1.7±0.2 mJy, alpha=-2.08±0.11  
  > "They find values of these constants of $\phi_\star=1800\pm400$ deg$^{-2}$, $S_\star=1.7\pm0.2$ mJy and $\alpha=-2.08\pm0.11$." (Azimuthal variations) [from (cite: carniani15)]
- External data: alpha Cen B excesses of 40% (870 um) and 220% (3 mm), used to interpolate chromospheric contribution  
  > "find that $\alpha$ Cen B has excesses above the photosphere of 40% and 220% at 870 $\mu$m and 3 mm respectively" (Stellar flux) [from (cite: liseau15)]
- External data: Planet mass limits from direct imaging  
  > "(cite: janson15) provide the most constraining limits on planets in the system, which are shown by the grey region in figure" (Orientation / radial profile) [from (cite: janson15)]
- External data: Stellar radial velocity 16.43±0.09 km/s  
  > "$\epsilon$ Eri itself has a radial velocity of 16.43$\pm$0.09 km s$^{-1}$ (cite: nidever02)" (CO mass limit) [from (cite: nidever02)]

## Processing

### Calibration

- pipeline or manual: Standard observatory calibration  
  > "The data were reduced using the standard observatory calibration in `CASA` version 4.3.1 (cite: mcmullin07)" (Observations)
- casa version: CASA 4.3.1  
  > "standard observatory calibration in `CASA` version 4.3.1" (Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: 5% calibration uncertainty  
  > "Including a 5% calibration uncertainty (cite: alma16)." (Observations footnote)
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: natural weighting, multi-frequency synthesis (dirty image)  
  > "created using natural weighting and multi-frequency synthesis" (Observations)
- uv taper: 2.5'' taper for the displayed CLEAN image  
  > "We also show a CLEAN image[^3] with a 2.5$''$ taper" (Observations)
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: Gaussian primary beam model; pixels with beam power >20% used in fits  
  > "We, therefore, only include pixels where the primary beam power is $>$20% of the peak in the primary beam." (Modelling)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Modelling procedure based on earlier work  
  > "The modelling procedure used here is based on that of (cite: booth16)." (Modelling) [from (cite: booth16)]
- Gaussian ring model (run C) as in earlier work  
  > "As in (cite: macgregor15), we also consider a Gaussian function (run C)" (Single component) [from (cite: macgregor15)]
- CO mass upper-limit method (low and high density)  
  > "we follow the method of (cite: matra15), considering both the case of low and high gas density" (CO mass limit) [from (cite: matra15)]
- Chromospheric contribution interpolation approach  
  > "Following (cite: chavez16), we interpolate between these, assuming that the excess follows a power law" (Stellar flux) [from (cite: chavez16)]

### Not stated but needed to reproduce (our reading)

- Dirty image cell size, image size and mask details
- Exact calibrators used and flux-scale reference
- How the six execution blocks were combined/weighted and any flagging
- Pixel-per-beam value used for S_ncr
- Convergence/burn-in criteria for emcee beyond walker and step numbers
- Details of the Gaussian primary beam model and dirty beam generation
- Whether self-calibration was applied

## Analysis recipe

1. **Image continuum and measure noise and stellar peak**: Dirty image with natural weighting and MFS over all four SPWs; RMS from a region 90'' off; Gaussian fit to stellar peak  
  > "we measure the RMS, $\sigma$, in a region 90$''$ offset from the primary beam to avoid any influence from the emission" (Observations)
   - software: CASA
   - fitting: _not stated_
   - validation: CLEAN image with 2.5'' taper used to check the northern peak is not due to sensitivity  
  > "This also shows that the peak at the northern ansa is not simply due to the higher sensitivity near to the phase centre." (Observations)
2. **Forward-model the ring in the image plane (single component, runs A, B, C)**: Model disc with line-of-sight integrator, plus central point source, times primary beam, convolved with dirty beam, compared to dirty image; chi2 with noise correlation ratio  
  > "The resulting sky image is then multiplied by the primary beam, convolved with the dirty beam and compared with the dirty image to produce a likelihood" (Modelling)
   - software: emcee
   - parameter: 120 walkers, 2000 timesteps; uniform priors; pixels with primary beam >20%  
  > "The MCMC is run with 120 walkers and 2000 timesteps for each model tested." (Modelling)
   - assumption: Black-body grains with T ∝ R^-0.5; ring centre coincident with star  
  > "The disc grains are assumed to act like black bodies i.e., they have a temperature that is $\propto R^{-0.5}$." (Modelling); "we assume that it is coincident with the location of the star" (Modelling)
   - fitting: MCMC with emcee; ln L = -chi2/2; priors in Table  
  > "a Markov Chain Monte Carlo (MCMC) routine is run making use of `emcee` (cite: foreman13)" (Modelling)
   - validation: Reduced chi2 comparison among runs; radial profiles of restored images; visibility-plane refit in appendix  
  > "here we re-run run A but this time fitting to the visibilities." (Appendix)
3. **Test for interior dust components (runs D, E, F)**: Add second component to run A best fit with same orientation; priors from LMT models (D: narrow ring ~20 AU; E: wide R^-3.5); run F for ring just interior to main belt  
  > "we assume that the main belt is described as in the best fit for run A and that the interior dust has the same inclination and position angle as the main belt." (Multiple components)
   - software: emcee
   - assumption: Extrapolate 1.1 mm flux to 1.3 mm with lambda^-3 slope  
  > "Extrapolating this flux density to 1.3 mm using a spectral slope of $\lambda^{-3}$" (Multiple components)
   - fitting: same MCMC  
  > "To test these we assume that the main belt is described as in the best fit for run A and that the interior dust has the same inclination and position angle as the main belt." (Multiple components)
   - validation: chi2_red compared (1.086 for run F)  
  > "it offers just a very slight improvement on the single component models with a $\chi^2_{red}=1.086$" (Multiple components)
4. **CO gas upper limit**: Integrate three channels (14.5-18.3 km/s), primary-beam correct, sum over ring pixels within 50% beam, scale to full ring; convert to mass with Matra et al. method for CMB-dominated and LTE cases  
  > "we consider the channels between 14.5 and 18.3 km s$^{-1}$ as potentially including the CO emission and spectrally integrate over these (three) channels." (CO mass limit)
   - assumption: CO co-located with dust in 63-76 AU ring (second-generation gas); LTE minimum mass at 16.6 K  
  > "we assume the CO to be co-located with the dust of the best-fit model for run A, i.e. in a uniform ring between 63 and 76 AU." (CO mass limit)
   - fitting: _not stated_
   - validation: Compared with Kral et al. 2017 predicted ~1e-9 Earth masses  
  > "(cite: kral17) show that $\epsilon$ Eri should have roughly 10$^{-9}$ M$_\oplus$ of CO." (CO mass limit)
5. **Planet constraints from ring edges**: Wisdom chaotic-zone relation for planet mass vs semi-major axis, with corrections for planetesimal eccentricity, planet eccentricity and collisions; resonance interpretation of edges (3:2 and 2:1)  
  > "If the belt we see around $\epsilon$ Eri is also bounded by the 3:2 and 2:1 resonances of an unseen planet, then the inner and outer edges should correspond to the same planet semi-major axis." (Radial profile)
   - parameter: C = 1.3; age 600 Myr for collisional case; planetesimal e<0.1  
  > "Given the width of the ring, the planetesimals must have an eccentricity less than 0.1" (Radial profile)
   - assumption: Inner edge set by outermost planet  
  > "Assuming the inner edge is defined solely by the outermost planet in the system (cite: deller05)" (Radial profile)
   - fitting: _not stated_
   - validation: Compared to Janson et al. imaging limits  
  > "(cite: janson15) provide the most constraining limits on planets in the system, which are shown by the grey region in figure [6](#fplloc)." (Radial profile)
6. **Assess residual clumps and background galaxy probability**: Residuals from run F; Schechter function galaxy counts from Carniani et al. to estimate chance of background galaxy  
  > "Galaxy number counts can be parametrised using a (cite: schechter76) function." (Azimuthal variations)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.3.1: Standard calibration of the data  
  > "standard observatory calibration in `CASA` version 4.3.1" (Observations)
- **emcee** : MCMC fitting of disc models  
  > "a Markov Chain Monte Carlo (MCMC) routine is run making use of `emcee`" (Modelling)
- **Astropy** : Acknowledged community Python package  
  > "This research made use of Astropy, a community-developed core Python package for Astronomy" (Acknowledgements)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Run A inner radius | 62.6 | +0.9/-1.5 | AU | 2 | 62.6$^{+0.9}_{-1.5}$ |
| Run A outer radius | 75.9 | +1.0/-0.9 | AU | 2 | 75.9$^{+1.0}_{-0.9}$ |
| Run C Gaussian ring centre R_mid | 69.4 | +0.5/-0.4 | AU | 2 | 69.4$^{+0.5}_{-0.4}$ |
| Run C FWHM | 11.3 | +1.4/-1.2 | AU | 2 | 11.3$^{+1.4}_{-1.2}$ |
| Inclination (run A) | 34 | ±2 | deg | 2 | Our models result in an inclination of around 34$\pm2$$^\circ$ and position angle of $-4\pm3$$^\circ$ East of North. |
| Position angle | -4 | ±3 | deg E of N | 2 | position angle of $-4\pm3$$^\circ$ East of North |
| Total disc flux density (run A) | 8.3 | ±0.6 | mJy | 2 | 8.3$^{+0.6}_{-0.6}$ |
| Flux density at star | 820 | ±68 | uJy | 1 | $F_{cen}=820\pm68\,\mu$Jy |
| Excess over photosphere | 290 | ±55 | uJy | 1 | there is an excess over the photosphere of $290\pm55\mu$Jy |
| Fractional ring width ΔR/R | 0.17 | not stated | dimensionless | 2 | we find a fractional belt width of $\Delta R/R=0.17$ |
| CO(2-1) flux in ring | 0.13 | ±0.11 | Jy km/s | 4 | giving a final result of 0.13$\pm$0.11 Jy km s$^{-1}$ |
| CO(2-1) 3σ upper limit | 0.33 | not stated | Jy km/s | 4 | 3$\sigma$ upper limit on the CO (2-1) line flux density within the main belt of 0.33 Jy km s$^{-1}$ |
| CO mass 3σ upper limit (CMB-dominated) | 9.6e-7 | not stated | Earth masses | 4 | 3$\sigma$ CO mass upper limit of 9.6$\times10^{-7}$ M$_\oplus$ |
| CO mass 3σ upper limit (LTE) | 2.6e-8 | not stated | Earth masses | 4 | 3$\sigma$ CO mass upper limit of 2.6$\times10^{-8}$ M$_\oplus$ |
| Implied planet semi-major axis (resonances) | 47.8 | ±1.2 (inner), ±1.0 (outer) | AU | 5 | the inner edge would be at the 3:2 resonance of a planet at 47.8$\pm$1.2 AU and the outer edge would be at the 2:1 resonance of a planet at 47.8$\pm$1.0 AU |
| Run F inner component | R_in 51 (+3/-4), R_out 59 (±5) AU, flux 0.7±0.4 mJy | as listed | AU, mJy | 3 | $R_{in, int} = 51^{+3}_{-4}$ AU, $R_{out, int} = 59^{+5}_{-5}$ AU and $F_{\nu, int} = 0.7^{+0.4}_{-0.4}$ mJy |
| Narrow interior ring flux limit (run D) | >0.8 mJy ruled out at 99.7% | not stated | mJy | 3 | models with a total flux density of this component $>$0.8 mJy are ruled out at the 99.7% level |

## Qualitative findings

- Ring is narrow (11-13 AU), comparable fractional width to the Kuiper belt; edges steep  
  > "The observed disc emission is found to be narrow with a width of just 11-13 AU." (abstract)
- Emission at the star is unresolved and consistent with chromospheric emission  
  > "attribute this excess to stellar chromospheric emission" (abstract)
- No CO detected  
  > "We have, therefore, not detected any CO gas in the disc" (CO mass limit)

## Claim tuples

- H: Is the epsilon Eri ring narrow? | E: Image-plane MCMC fits of sharp-edged and Gaussian ring models | R: Width 11-13 AU, ΔR/R=0.17 | F: One of the narrowest known debris discs, similar to the Kuiper belt | **supported**
- H: Are the ring edges set by resonances with a planet? | E: Compared edges to 3:2 and 2:1 resonances | R: Both match a planet at ~47.8 AU | F: A planet at ~48 AU is possible, mass 0.4-1.2 MJ, though possibly coincidence | **partially**
- H: Is there dust interior to the main ring or clumps in the ring? | E: Multi-component fits and residual analysis | R: Narrow 20 AU belt limited to <0.8 mJy; tentative 2σ emission just interior; residuals likely contain a background galaxy | F: Tentative evidence only; follow-up needed | **partially**
- H: Is the central emission above the photosphere due to the chromosphere? | E: Compared measured flux to photosphere plus alpha Cen B-based chromospheric estimate | R: Excess 290±55 uJy; expected total ~900 uJy | F: Entire excess consistent with chromosphere | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Image-plane forward modelling since the disc is much larger than the primary beam and only part is observed  
  > "The proximity of this star to the Earth results in the disc having an angular diameter far larger than the primary beam of ALMA" (Observations)
- Alternative: Visibility-plane fit of run A gave consistent results (flux 0.6% higher)  
  > "In particular, the total disc flux density is only 0.6% higher." (Appendix)
- How they decided it was enough: _not stated_
- Limitation (authors): Only part of ring observed; flux density may be underestimated, and lack of short baselines limits sensitivity to extended emission  
  > "we have only observed part of the ring and assumed there to be no large variations around the ring." (Disc flux density)
- Limitation (authors): Models cannot be distinguished from the image alone  
  > "from the images alone it is not possible to distinguish between these models" (Single component)
- Caveat (inferred, ours): Ring flux depends on assumption of azimuthal symmetry from a partial arc
- Caveat (inferred, ours): Gaussian primary beam model and dirty-image fitting may bias results
- Caveat (inferred, ours): Clump significance low (≤5σ) with high background galaxy probability
- Caveat (inferred, ours): Black-body temperature profile degenerate with optical depth

## Reproducibility

- Data public (paper): Data cited as ALMA project 2013.1.00645.S (archive data, acknowledged)  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2013.1.00645.S." (Acknowledgements)
- Products in archive: _not stated_
- Code: _not stated_
- Missing: Modelling code (Booth et al. 2016 based) not released
- Missing: Imaging parameters (cell, size) not given
- Missing: Calibrators and exact EB processing not given
- Data volume (inferred): ~50-100 GB raw for six execution blocks
- Score (inferred): 3/5, Public data and clear model/priors/MCMC setup, but custom unreleased code and missing imaging details.
- Rediscovery candidate: no, Requires custom image-plane forward-model code not released; imaging details incomplete.

## Links

- Method: (cite: booth16) (Modelling procedure basis)
- Method: (cite: matra15) (CO mass limit method)
- Method: (cite: wyatt99) (Line-of-sight integrator for sky image)
- Companion: (cite: chavez16) (LMT 1.1 mm observations of epsilon Eri)
- Companion: (cite: macgregor15) (SMA 1.3 mm observations of epsilon Eri)

## Checks

```json
{
 "quotes": 87,
 "quotes_ok": 87,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 17,
 "numeric_problems": 0,
 "fill": {
  "facts": 86,
  "stated": 59,
  "rate": 0.686
 },
 "evidence_ok": true
}
```
