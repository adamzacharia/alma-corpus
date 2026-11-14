# Multiple Rings in the Transitional Disk of GM Aurigae Revealed by VLA and ALMA

`2018ApJ...865...37M` | The Astrophysical Journal 2018 | first author: Macías, Enrique | arXiv: 1808.01920 | DOI: 10.3847/1538-4357/aad811

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks
- Question: What is the radial distribution of large dust grains in the transitional disk of GM Aur at 0.9 mm and 7 mm, and does it contain multiple rings?  
  > "We model our observations using two approaches: an analytical fit to the observed deprojected visibilities, and a physical disk model that fits the SED as well as the VLA and ALMA observations." (abstract)
- Target **GM Aur**: coordinates RA 04h55m10.9885s, Dec 30d21m58.947s (Gaia-based stellar position, ALMA epoch)  
  > "located at $160\pm2$ pc (cite: gai16; gai18) in the Taurus-Auriga cloud" (1 Introduction); "RA = 04h55m10.9885s DEC = 30d21m58.947s for the ALMA observations" (4.1 Surface Brightness Profile Model); z/distance 160±2 pc  
  > "located at $160\pm2$ pc (cite: gai16; gai18) in the Taurus-Auriga cloud" (1 Introduction); "RA = 04h55m10.9885s DEC = 30d21m58.947s for the ALMA observations" (4.1 Surface Brightness Profile Model); distance from Gaia DR2 (gai18)  
  > "located at $160\pm2$ pc (cite: gai16; gai18) in the Taurus-Auriga cloud" (1 Introduction); "RA = 04h55m10.9885s DEC = 30d21m58.947s for the ALMA observations" (4.1 Surface Brightness Profile Model)

## Data provenance

- ALMA projects: 2016.1.00565.S
- bands: ALMA Band 7 (~0.9 mm); VLA Q band (~7 mm)  
  > "The ALMA observations were performed at Band 7 ($\sim0.9$ mm) during Cycle 4 (PI: Kamber Schwarz)." (2.1 ALMA Observations)
- frequencies and spectral setup: Continuum SPW at 317.989 GHz (2 GHz bandwidth); 13CO and C18O (3-2) SPWs with ~122 kHz resolution, ~234.4 MHz each  
  > "One was centered at 317.989 GHz and was dedicated exclusively to detect the continuum dust emission, using the highest bandwidth possible (2 GHz)." (2.1 ALMA Observations)
- continuum bandwidth: _not stated_
- arrays: ALMA 12 m array, 39 antennas  
  > "using 39 antennas of the 12 m array, with baselines ranging from $\sim15$ m to $\sim850$ m" (2.1 ALMA Observations)
- configurations: _not stated_
- baselines: ALMA ~15 m to ~850 m; VLA B config ~150 m to ~10000 m  
  > "with baselines ranging from $\sim15$ m to $\sim850$ m" (2.1 ALMA Observations); "with antenna separations that ranged from $\sim150$ m to $\sim10000$ m" (2.2 VLA Observations)
- angular resolution: ALMA robust 0.5: 0.39x0.28 arcsec; uniform: 0.29x0.20 arcsec; VLA 0.18x0.15 arcsec  
  > "This resulted in a synthesized beam size of $0\rlap.''39\times0\rlap.''28$ (PA$=0^{\circ}$)" (2.1 ALMA Observations)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: ALMA 2016 Nov 11; VLA 2016 June 17 and July 20  
  > "The data were obtained on 2016 November 11" (2.1 ALMA Observations); "The observations were performed on 2016 June 17 and July 20 using the B configuration" (2.2 VLA Observations)
- pi or archival as stated: ALMA Cycle 4, PI Kamber Schwarz  
  > "during Cycle 4 (PI: Kamber Schwarz)" (2.1 ALMA Observations)
- Line: 13CO 3-2 (330.588 GHz)
- Line: C18O 3-2 (329.331 GHz)
- Other facility **VLA**: 7 mm B-configuration continuum data  
  > "We obtained Q band ($\sim7$ mm) data of GM Aur using the VLA" (2.2 VLA Observations)
- Other facility **Gaia**: Distance and stellar position  
  > "The stellar position was obtained from the position and proper motions measured by Gaia" (4.1 Surface Brightness Profile Model)
- External data: Optical to far-IR SED photometry  
  > "Most optical to far-IR data were taken from (cite: esp11) and references therein." (4.2.1 Modeling Procedure) [from (cite: esp11)]
- External data: Herschel photometry and spectra  
  > "we included Herschel photometry and spectra (cite: rib17)" (4.2.1 Modeling Procedure) [from (cite: rib17)]
- External data: (sub)mm and cm photometry 0.62 mm to 5 cm; VLA C-config 7 mm image  
  > "(sub)mm and cm photometry, from 0.62 mm to 5 cm ((cite: mac16), and references therein)" (4.2.1 Modeling Procedure) [from (cite: mac16)]
- External data: Single dish flux 730±70 mJy at 0.80 mm  
  > "previous single dish submm observations measured a flux density of $730\pm70$ mJy at 0.80 mm (cite: wei89)" (3 Results) [from (cite: wei89)]
- External data: Accretion rate 7.8e-9 Msun/yr (average of measured range)  
  > "The mass accretion rate on GM Aur has been measured to be variable, between $1.1\times10^{-8}$ $M_{\odot}$ yr$^{-1}$ and $3.9\times10^{-9}$ $M_{\odot}$ yr$^{-1}$ (cite: ing15)" (4.2.1 Modeling Procedure) [from (cite: ing15)]

## Processing

### Calibration

- pipeline or manual: ALMA pipeline used, no extra flagging; VLA calibration pipeline with additional flagging and rerun  
  > "The pipeline was used to calibrate the data, with no additional flagging required." (2.1 ALMA Observations)
- casa version: CASA 4.7.0 (ALMA calibration); 4.7.2 (VLA); CLEAN with 4.5.3  
  > "version 4.7.0)" (2.1 ALMA Observations); "VLA calibration pipeline within CASA (version 4.7.2)" (2.2 VLA Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: ALMA: J0522-3627 (flux), J0510+1800 (bandpass and gain); VLA: 3C147 flux/bandpass, J0438+3004 gain  
  > "The quasar J0522-3627 was observed as the absolute flux calibrator" (2.1 ALMA Observations); "The quasar 3C147 was used as the flux and bandpass calibrator" (2.2 VLA Observations)
- flux scale uncertainty: ~10% for both ALMA and VLA  
  > "with an expected uncertainty in the flux scale of $\sim10\%$" (2.1 ALMA Observations)
- self calibration: Applied on GM Aur (ALMA); details not given  
  > "Self-calibration was applied on GM Aur, which successfully improved the quality and signal-to-noise ratio of the data." (2.1 ALMA Observations)

### Imaging

- task: CASA CLEAN, version 4.5.3  
  > "We used the task CLEAN of CASA (version 4.5.3) to produce cleaned images from the calibrated visibilities." (2.1 ALMA Observations)
- deconvolver: Multi-frequency synthesis with nterms=2  
  > "the multi-frequency deconvolution algorithm built in CLEAN was used with nterms=2 (cite: con90)" (2.1 ALMA Observations)
- weighting robust: ALMA robust = 0.5 and uniform; VLA natural  
  > "The top-left panel of Fig. [1](#fig:maps) shows the image obtained with a robust parameter of 0.5" (2.1 ALMA Observations); "We applied a natural weighting to maximize the signal-to-noise ratio of the image" (2.2 VLA Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: 2 GHz continuum SPW combined with line-free channels of the two 234 MHz SPWs; channels not specified  
  > "The 2 GHz spectral window was combined with the line-free channels of the two 234 MHz spectral windows to maximize the continuum sensitivity." (2.1 ALMA Observations)
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: ALMA robust 0.39x0.28 arcsec PA 0; uniform 0.29x0.20 arcsec PA 14; VLA 0.18x0.15 arcsec PA -72  
  > "angular resolution of $0\rlap.''18\times0\rlap.''15$ (PA$=-72^{\circ}$)" (2.2 VLA Observations)
- final rms: ALMA 0.10 mJy/beam (robust), 0.35 mJy/beam (uniform); VLA 12 uJy/beam  
  > "an rms of $0.10$mJy beam$^{-1}$, producing a peak SNR of 500" (2.1 ALMA Observations); "an rms of $12~\mu$Jy beam$^{-1}$" (2.2 VLA Observations)

### Inherited from earlier work

- Stellar properties (Teff, spectral type, Av) and optically thin inner dust and photosphere components  
  > "Furthermore, we included optically thin dust inside the disk cavity, following (cite: esp11)." (4.2 Physical Disk Model) [from (cite: esp11)]
- Dust composition: ~38% graphite, ~62% silicates (50% olivine, 50% pyroxene)  
  > "We use a similar dust composition to (cite: esp11)" (4.2.1 Modeling Procedure) [from (cite: esp11)]
- Grain size distribution power law -3.5, min size 0.005 um  
  > "starting at a minimum size of $0.005~\mu$m and with a power of $-3.5$ (cite: mat77)" (4.2 Physical Disk Model) [from (cite: mat77)]
- DIAD code details; epsilon_mid from vertical conservation of dust mass  
  > "We refer to (cite: dal06) and references therein for a more detailed description of the code." (4.2 Physical Disk Model) [from (cite: dal06)]
- Spectral index 3.05 for flux extrapolation  
  > "Assuming a spectral index of 3.05, as measured by (cite: mac16)" (3 Results) [from (cite: mac16)]
- Molecular line analysis deferred  
  > "the molecular emission will be analyzed in Schwarz et al. (in prep.)" (2.1 ALMA Observations) [from Schwarz et al. (in prep.)]

### Not stated but needed to reproduce (our reading)

- Self-calibration solution intervals, number of rounds and reference
- Line-free channel selection for the line SPWs
- CLEAN masks, image size, cell size and number of iterations/threshold
- Prior ranges of the flat priors and MCMC walker count and initial scatter
- Uvrange/binning of visibilities used in the fit
- DIAD code availability and grid ranges/steps; exact chi2 definition
- Dust opacity details for DIAD
- Treatment of free-free contribution at 7 mm in the models

## Analysis recipe

1. **Calibrate and image continuum**: CASA pipeline calibration with self-calibration, then CLEAN with nterms=2 using continuum SPW plus line-free channels  
  > "The pipeline was used to calibrate the data, with no additional flagging required." (2.1 ALMA Observations)
   - software: CASA
   - parameter: robust 0.5 and uniform weighting (ALMA); natural (VLA)  
  > "a robust parameter of 0.5" (2.1 ALMA Observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **Radial profiles and flux densities**: Average emission in concentric ellipses of 0.02 arcsec width using i=52.8, PA=56.5; flux in box above 3 sigma  
  > "The width of the ellipses was set to $0\rlap.''02$, a relatively small fraction of the beam size." (3 Results)
   - fitting: _not stated_
   - validation: Compared with single-dish flux extrapolated with spectral index 3.05  
  > "Assuming a spectral index of 3.05, as measured by (cite: mac16)" (3 Results)
3. **Fit Gaussian-ring surface brightness model to deprojected visibilities**: Hankel transform of sum of Gaussian rings fitted to real part of deprojected visibilities; 3 Gaussians for ALMA, 2 for VLA  
  > "directly fitting an analytical model of the surface brightness profile of the disk to the real part of deprojected visibilities" (4.1 Surface Brightness Profile Model)
   - software: emcee
   - parameter: Free: i, PA, dRA, dDEC, and a_i, sigma_i, x_i per ring  
  > "the free parameters of our model are the inclination, PA, offsets in RA and DEC, and $a_i$, $\sigma_i$, and $x_i$ for each Gaussian ring" (4.1 Surface Brightness Profile Model)
   - assumption: Axisymmetric emission  
  > "If we assume that the emission is axisymmetric" (4.1 Surface Brightness Profile Model)
   - fitting: emcee affine-invariant ensemble MCMC; chains initialized around Levenberg-Marquardt best fit; flat priors for ALMA; Gaussian priors from ALMA posteriors for VLA; 30000 iterations, last 5000 used  
  > "We ran the MCMC for 30000 iterations to assure that the chains had converged. The last 5000 iterations were used to obtain the posteriors" (Markov Chain Monte Carlo runs)
   - validation: Third Gaussian added when two failed to reproduce second visibility minimum at ~600 kλ  
  > "it failed to reproduce the second minimum in the negative visibilities at $\sim600$ k$\lambda$" (4.1 Surface Brightness Profile Model)
4. **Physical DIAD disk model fit to SED, VLA and ALMA**: Grids of DIAD models; best fit chosen by min chi2, visual inspection and iterative refinement; epsilon_mid modulated by factor delta in radial ranges; model visibilities with observed uv coverage, residuals imaged  
  > "we ran a number of grids of models and found the best-fit parameters by a combination of model selection based on minimum $\chi^2$, visual inspection, and successive refinement of the parameters of the grids" (4.2.1 Modeling Procedure)
   - software: DIAD, CASA
   - parameter: Mdot fixed at 7.8e-9 Msun/yr; alpha varied 0.0001-0.01; Rwall 25-40 au; mid amax 1 mm-2.5 cm; eps_atm 0.001-0.8; Rdisk 150-300 au  
  > "we decided to fix $\dot{M}$ to an average value of $7.8\times10^{-9}$ $M_{\odot}$ yr$^{-1}$, and we varied $\alpha$ between 0.0001 and 0.01" (4.2.1 Modeling Procedure)
   - assumption: Dust-to-gas ratio 0.01; distance 160 pc; inclination and PA fixed from step 3  
  > "We assume a fixed “standard" dust-to-gas mass ratio of 0.01." (4.2 Physical Disk Model)
   - fitting: Grid search, not MCMC or Levenberg-Marquardt, due to computational cost  
  > "This prevents us from using common algorithms or statistical methods, such as Levenberg-Marquardt $\chi^2$ minimization or MCMC" (4.2.1 Modeling Procedure)
   - validation: Iterated until SED fit good and VLA/ALMA image residuals below ~3 sigma  
  > "ensuring that the residuals in the VLA and ALMA images were below $\sim3\sigma$" (4.2.1 Modeling Procedure)

## Software

- **CASA** 4.7.0 (ALMA cal), 4.7.2 (VLA cal), 4.5.3 (CLEAN): Calibration, self-calibration and imaging  
  > "Data calibration and editing were performed using the data reduction package CASA" (2.1 ALMA Observations)
- **emcee** : MCMC fit of visibility model  
  > "provided with the `EMCEE` package (cite: for13)" (4.1 Surface Brightness Profile Model)
- **DIAD** : Physical disk model of structure and SED  
  > "We use the D’Alessio Irradiated Accretion Disk (DIAD) code" (4.2 Physical Disk Model)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| ALMA 0.9 mm flux density (robust) | 380 | 40 | mJy | 2 | we measure a flux density of $380\pm40$ mJy |
| ALMA flux density (uniform) | 350 | 40 | mJy | 2 | yields a flux density of $350\pm40$ mJy |
| VLA 7 mm flux density | 1.36 | 0.15 | mJy | 2 | We measure a flux density of $1.36\pm0.15$ mJy |
| Disk inclination | 52.77 | +0.05/-0.04 | deg | 3 | we find an inclination of $52.77^{\circ} ~^{+0.05}_{-0.04}$ |
| Disk position angle | 56.45 | +0.06/-0.05 | deg | 3 | a PA of $56.45^{\circ}~^{+0.06}_{-0.05}$ |
| Inner ring radius x1 at 0.9 mm | 42.5 | ±0.2 | au | 3 | than at 0.9 mm ($x_1=42.5\pm0.2$ au) |
| Inner ring radius x1 at 7 mm | 39 | ±1 | au | 3 | smaller at 7 mm ($x_1=39\pm1$ au) |
| Second ring radius x2 at 0.9 mm | 83.4 | ±0.6 | au | 3 | $x_{2}$ / $0\rlap.''521^{+0\rlap.''004}_{-0\rlap.''004}$ ($83.4^{+0.6}_{-0.6}$ au) |
| Third component x3 at 0.9 mm | 149 | ±1 | au | 3 | $x_{3}$ / $0\rlap.''934^{+0\rlap.''006}_{-0\rlap.''006}$ ($149^{+1}_{-1}$ au) |
| Dust mass in DIAD model | 2.0 | not stated | M_Jup | 4 | The dust mass ($M^{\rm{dust}}_{\rm{disk}}$) in our disk model is $2.0~M_{J}$. |
| Total disk mass (assuming gas-to-dust 100) | 200 | not stated | M_Jup | 4 | this implies a total disk mass of $200~M_{J}$ |
| Best-fit alpha | 0.0012 | not stated | dimensionless | 4 | $\alpha$                                   / 0.0012 |

## Qualitative findings

- Cavity is resolved in both bands; ALMA also shows a fainter extended disk to ~250 au  
  > "The ALMA observations also reveal a fainter disk that extends up to $\sim250$ au." (abstract)

## Claim tuples

- H: Does the GM Aur dust disk contain multiple rings despite smooth deconvolved images? | E: Gaussian-ring fit to deprojected ALMA and VLA visibilities | R: Two rings at ~40 and ~80 au needed, plus an extended component in ALMA | F: The disk has at least two bright rings | **supported**
- H: Are the rings due to large-grain trapping? | E: DIAD model with epsilon_mid enhancements | R: Enhancement factors of 4 and 3 in two rings fit SED and images | F: Large grains are probably trapped in two pressure bumps | **supported**
- H: Is the cavity size different at 0.9 and 7 mm? | E: Compare ring positions in the visibility fits and the model residuals | R: x1 = 39±1 au at 7 mm vs 42.5±0.2 au at 0.9 mm | F: Cavity may be smaller at 7 mm, due to free-free emission or stronger grain concentration; not confirmed | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Visibility fitting avoids CLEAN artifacts and uses the highest spatial frequencies  
  > "Directly analyzing the observed visibilities can provide us with additional information while also avoiding these possible artifacts." (3 Results)
- Alternative: Varying total gas density instead of epsilon_mid rejected since observations trace only large grains  
  > "we choose to only vary $\epsilon_{\rm{mid}}$ since our VLA and ALMA observations only provide information about the large dust grains located in the disk midplane" (4.2.1 Modeling Procedure)
- How they decided it was enough: _not stated_
- Limitation (authors): Mdot and alpha degenerate; other combinations may fit; no MCMC uncertainties on the physical model  
  > "other models with similar disk masses but different values of $\alpha$ and $\dot{M}$ may also result in satisfactory fits" (4.2.1 Modeling Procedure)
- Limitation (authors): VLA data sensitivity limited; asymmetry and cavity difference low significance  
  > "both the C configuration and B configuration images of the 7 mm emission are probably sensitivity limited" (3 Results)
- Caveat (inferred, ours): Gaussian ring parametrization and number of rings is a model choice; no model comparison statistic given
- Caveat (inferred, ours): Physical model has no uncertainties and a hand-tuned grid
- Caveat (inferred, ours): Cavity size difference rests on poorly constrained VLA fit with informative priors from ALMA
- Caveat (inferred, ours): Possible missing extended flux in ALMA

## Reproducibility

- Data public (paper): ALMA project cited; VLA program not identified  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2016.1.00565.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: VLA project code
- Missing: DIAD code and grid details
- Missing: Self-calibration parameters
- Missing: Clean masks and image parameters
- Data volume (inferred): ALMA Band 7 single execution, ~10-30 GB; VLA 8 GHz B config two tracks, ~100+ GB raw
- Score (inferred): 3/5, Data and many settings stated and the visibility fit is reproducible with emcee, but the DIAD model and self-calibration details are unavailable.
- Rediscovery candidate: no, The key physical model needs a non-public DIAD code and the VLA data are not identified, though the ring fit is repeatable.

## Links

- Method: (cite: dal06) (DIAD model description)
- Method: (cite: zha16) (Visibility-based ring fitting approach)
- Companion: (cite: mac16) (Earlier VLA C-configuration observations of GM Aur)
- Companion: Schwarz et al. (in prep.) (Molecular line analysis of the same ALMA data)

## Checks

```json
{
 "quotes": 86,
 "quotes_ok": 86,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 12,
 "numeric_problems": 0,
 "fill": {
  "facts": 80,
  "stated": 58,
  "rate": 0.725
 },
 "evidence_ok": true
}
```
