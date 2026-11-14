# A Dust-trapping Ring in the Planet-hosting Disk of Elias 2-24

`2024ApJ...971..129C` | The Astrophysical Journal 2024 | first author: Carvalho, Adolfo S. | arXiv: 2406.12819 | DOI: 10.3847/1538-4357/ad5a07

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks
- Question: Is the bright ring at 78 au in the planet-hosting disk Elias 24 a dust trap, and what are the dust properties, turbulence and gas-to-dust ratio there?  
  > "We present evidence of dust trapping in the bright ring of the planet-hosting disk Elias 2-24" (abstract)
- Target **Elias 2-24 (Elias 24)**: coordinates RA = 16h 26m 24.08s, Dec = -24d 16m 13.9s (J2000)  
  > "located at J2000 RA = 16h 26m 24.08s, Dec = -24d 16m 13.9s, and a distance of $139 \pm 1$ pc (cite: gaia_DR3_2023A&A)" (Introduction); z/distance 139 ± 1 pc  
  > "located at J2000 RA = 16h 26m 24.08s, Dec = -24d 16m 13.9s, and a distance of $139 \pm 1$ pc (cite: gaia_DR3_2023A&A)" (Introduction); distance from Gaia DR3  
  > "located at J2000 RA = 16h 26m 24.08s, Dec = -24d 16m 13.9s, and a distance of $139 \pm 1$ pc (cite: gaia_DR3_2023A&A)" (Introduction)

## Data provenance

- ALMA projects: 2017.1.01330.S, 2018.1.01198.S, 2013.1.00498.S
- bands: Band 3 (3 mm, new) and Band 6 (1.3 mm, DSHARP)  
  > "The data were taken using ALMA Band 3 ($\lambda \approx 3$ mm) in 4 spectral windows (SPWs) centered at 90.5, 92.5, 102.5, and 104.5 GHz." (2 Data and Calibration)
- frequencies and spectral setup: 4 SPWs at 90.5, 92.5, 102.5, 104.5 GHz, 1.875 GHz bandwidth, 128 channels each  
  > "All SPWs had a 1.875 GHz bandwidth sampled at 128 channels each." (2 Data and Calibration)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: 3 compact executions (C43-6, 15m-2,500m) and 4 extended (C43-10, 244m-16,200m)  
  > "3 executions in compact antenna configurations (C43-6, 15m$-$2,500m baselines) and 4 executions in extended antenna configurations (C43-10, 244m$-$16,200m)" (2 Data and Calibration)
- baselines: uv-range 5-5,400 kλ (3 mm); 11.5-11,500 kλ (1.3 mm)  
  > "The resulting range of $uv$-distances in the 3 mm data are 5-5,400 k$\lambda$." (2 Data and Calibration)
- angular resolution: 3 mm CLEAN 0.060"x0.058"; 1.3 mm CLEAN 0.036"x0.034"; frank 29 mas (3 mm), 15 mas (1.3 mm)  
  > "The final 3 mm CLEAN image reached a resolution of $0.060'' \times 0.058''$ (8.2 au $\times$ 7.9 au)" (2 Data and Calibration)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: November 30, 2017 and June 12-29, 2019 (3 mm)  
  > "conducted on November 30, 2017, and June 12-29, 2019" (2 Data and Calibration)
- pi or archival as stated: _not stated_
- Other facility **VLT/NaCo**: L' imaging discovery of companion (prior work)  
  > "using VLT/NaCo $L^\prime$ diffraction-limited imaging (cite: Jorquera_Elias24_CPD_2021AJ)" (Introduction)
- External data: 1.3 mm calibrated DSHARP visibilities  
  > "we employ their publicly available calibrated visibilities" (2 Data and Calibration) [from Andrews_DSHARP_I_2018ApJ]
- External data: Stellar luminosity L*=6 Lsun and its 0.2 dex uncertainty  
  > "We use $L_* = 6 \ L_\odot$ (cite: Natta_El24Mass_2006)" (4.1) [from Natta_El24Mass_2006]
- External data: Stellar mass 0.78 Msun  
  > "$M_*=0.78$ $M_\odot$ is the stellar mass (cite: Andrews_DSHARP_I_2018ApJ)" (4.1) [from Andrews_DSHARP_I_2018ApJ]
- External data: Disk inclination and PA priors (29.0 deg, 45.7 deg) and 1.3 mm phase center  
  > "we construct Gaussian priors using the the inclination and position angle values and $1\sigma$ uncertainties from (cite: Huang_DSHARPII_2018ApJ)" (8 frank fitting) [from Huang_DSHARPII_2018ApJ]
- External data: DSHARP dust opacities, grain density 1.675 g/cm3  
  > "$\rho_m=1.675$ g cm$^{-3}$ is the average grain density (cite: birnstiel-DSHARP-scattering_2018ApJL)" (4.3) [from birnstiel-DSHARP-scattering_2018ApJL]

## Processing

### Calibration

- pipeline or manual: Standard ALMA Pipeline Calibration; 90.5 GHz SPW of compact data omitted  
  > "The standard ALMA Pipeline Calibration was applied" (2 Data and Calibration)
- casa version: CASA 5.4.0 and 5.6.1  
  > "Self-calibration was done with CASA versions 5.4.0 and 5.6.1 using the parallelized $\mathtt{mpicasa}$." (2 Data and Calibration)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: execution offsets <3%, no correction; 10% overall flux uncertainty  
  > "offsets in flux amplitude between each execution were within uncertainties ($< 3 \%$) and required no correction" (2 Data and Calibration)
- self calibration: Short baselines: phase-only (scan-length, 90s, 45s, 24s) then one amp+phase; combined: phase-only (300s, scan-length) then amp+phase infinite  
  > "phase-only self-calibration, where we combined the SPWs and step down the solution intervals (scan-length, 90s, 45s, and 24s)" (2 Data and Calibration)

### Imaging

- task: CASA tclean, multiscale multifrequency synthesis  
  > "We imaged the data with CASA $\mathtt{tclean}$, using the multiscale, multifrequency synthesis mode" (2 Data and Calibration)
- deconvolver: _not stated_
- weighting robust: robust = 0.8 (also 0.0 for profiles)  
  > "a Briggs weighting parameter of $\mathtt{robust}=0.8$" (2 Data and Calibration)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: cleaning threshold 1 sigma, RMS from annulus 1.7-3.0 arcsec  
  > "spanning 1.7 arcsec to 3.0 arcsec" (2 Data and Calibration)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 3 mm 0.060"x0.058"; 1.3 mm 0.036"x0.034"  
  > "which has a resolution of $0.036'' \times 0.034''$ (5.0 au $\times$ 4.7 au)" (2 Data and Calibration)
- final rms: _not stated_

### Inherited from earlier work

- Self-calibration method  
  > "We follow the method described in (cite: Andrews_DSHARP_I_2018ApJ) and (cite: Oberg_MAPS_2021ApJS)" (2 Data and Calibration) [from Andrews_DSHARP_I_2018ApJ; Oberg_MAPS_2021ApJS]
- 1.3 mm CLEAN parameters  
  > "For the 1.3 mm data we use the same CLEAN parameters as in (cite: Andrews_DSHARP_I_2018ApJ)" (2 Data and Calibration) [from Andrews_DSHARP_I_2018ApJ]
- frank alpha and w_smooth fiducial values  
  > "we set a conservative $\alpha=1.3$ and $w_{\mathrm{smooth}}=10^{-1}$, following (cite: Andrews_CPD_2021ApJ)" (8 frank fitting) [from Andrews_CPD_2021ApJ]
- Radiative transfer model with scattering  
  > "we perform radiative transfer modeling following the model in (cite: Sierra_MAPS_2021ApJS)" (4.2) [from Sierra_MAPS_2021ApJS]
- Dust trapping efficiency formalism  
  > "following the procedure in (cite: Dullemond_DSHARP_2018ApJ)" (4.1) [from Dullemond_DSHARP_2018ApJ]
- Gas-to-dust constraint via optical depth and Stokes number  
  > "as is done in (cite: Stammler_DustGasRatio_2019ApJ)" (4.4) [from Stammler_DustGasRatio_2019ApJ]

### Not stated but needed to reproduce (our reading)

- tclean multiscale scales, image size, cell size, mask details
- Which 3 mm SPWs/channels for continuum and any line-free selection
- Model grids, sampling of the marginal probability (grid resolution, number of points) in the radiative transfer fit
- Exact 1.3 mm CLEAN parameters (in DSHARP paper)
- Exact self-calibration reference antenna, SNR thresholds
- Fitting of Gaussian to ring: fitting method and weighting

## Analysis recipe

1. **Calibrate and self-calibrate 3 mm data, image**: Pipeline calibration, align executions to common phase center, self-calibrate short then combined baselines, tclean imaging  
  > "We then align the different executions to a common phase-center, determined by fitting a 2D Gaussian to the emission peak of one of the long-baseline observations." (2 Data and Calibration)
   - software: CASA, tclean, gaincal, virtualconcat
   - parameter: robust=0.8, 1 sigma threshold  
  > "a Briggs weighting parameter of $\mathtt{robust}=0.8$" (2 Data and Calibration)
   - fitting: _not stated_
   - validation: JvM correction factor 0.98 (3 mm), 0.78 (1.3 mm)  
  > "The correction factor for the 3 mm data is 0.98, so we do not apply any correction." (2 Data and Calibration)
2. **Derive deconvolved radial profiles**: Fit 1-D radial brightness profile to deprojected visibilities with Gaussian process; point-source at phase center subtracted; 5000 fits for uncertainties  
  > "The code assumes an axi-symmetric emission distribution and fits a 1-D radial brightness profile to the real, deprojected visibilities using a Gaussian process." (3 Radial Profiles)
   - software: frankenstein
   - parameter: Rmax=2.1", N=300, p0=1e-15 Jy^2, alpha=1.3, wsmooth=0.1  
  > "we set a conservative $\alpha=1.3$ and $w_{\mathrm{smooth}}=10^{-1}$" (8 frank fitting)
   - assumption: Axisymmetric emission; i=29 deg, PA=45.7 deg  
  > "$N(29.0, 0.4)$" (Table 2)
   - fitting: Hyperparameter and geometry priors (Table 2) sampled in 5000 fits; 16-84th percentile as 1 sigma  
  > "we compute 5000 different $\mathtt{frank}$ fits for the 1.3 mm and 3 mm data, randomly sampling hyperparameters and disk geometries." (8 frank fitting)
   - validation: Compared with CLEAN image and CLEAN model radial profiles; residual imaging  
  > "The CLEAN-beam-convolved $\mathtt{frank}$ profile matches the CLEAN image profile well." (12 Tests)
3. **Spectral index profile**: Convolve 1.3 mm profile by 25 mas to 29 mas and compute alpha = log(I230/I100)/log(2.3)  
  > "We then compute the spectral index profile as $\alpha = \log(\frac{I_\mathrm{230 \ GHz}}{I_\mathrm{100 \ GHz}}) / \log(\frac{230}{100})$." (3 Radial Profiles)
   - fitting: _not stated_
   - validation: _not stated_
4. **Ring width and dust-trapping efficiency**: Fit single Gaussian to ring B77, deconvolve width, compare w_d with pressure scale height; compute psi and alpha/St following Dullemond et al.  
  > "To compute $w_d$, we fit a single Gaussian to B77 (within $78 \pm 5$ au), using the $\mathtt{frank}$ profile at 1.3 and 3 mm." (4.1)
   - software: frankenstein
   - parameter: w_max = 17.1 au, w_min = h_p = 5.15 au  
  > "The maximum pressure bump width, $w_\mathrm{max}$, is measured as the separation of the ring to the nearest minimum, so $w_\mathrm{max}=17.1$ au." (4.1)
   - assumption: Passive flared disk Td, phi=0.02, L*=6 Lsun, scaled by 0.5, mu=2.33, Sc=1, Gaussian rings  
  > "We use $L_* = 6 \ L_\odot$ (cite: Natta_El24Mass_2006) and assume $\varphi = 0.02$, as adopted in (cite: Dullemond_DSHARP_2018ApJ)." (4.1)
   - fitting: _not stated_
   - validation: 1.3 mm w_d consistent with Jennings et al. 2022  
  > "our measurement of $w_d$ at 1.3 mm is identical (within uncertainty) to that reported by (cite: Jennings_frankDSHARP_2022MNRAS)" (4.1)
5. **Radiative transfer fit of Sigma_d, a_max, T_d**: Scattering-included marginal probability analysis at each radius with DSHARP opacities using two bands  
  > "we perform radiative transfer modeling following the model in (cite: Sierra_MAPS_2021ApJS), where we include the effect of dust scattering opacity and use the DSHARP dust opacity law" (4.2)
   - parameter: p=2.5 fixed (3.5 tested); Gaussian prior on Td with 11% width; a_max(r<50 au)>0.072 cm; IMF-like Sigma_d prior exponent -2.3  
  > "we fix the power law index of the grain size distribution to $p=2.5$ and impose a prior on the dust temperature profile" (4.2)
   - assumption: DSHARP opacity law  
  > "use the DSHARP dust opacity law" (4.2)
   - fitting: Marginal probability distributions; chi2-based probabilities with priors  
  > "and then add it to the $\chi^2$ probabilities" (10 Priors)
   - validation: p=3.5 and Ricci opacities tested with similar Sigma_d, Td  
  > "We have also tested using the (cite: Ricci_TaurusOpacities_GrainGrowth_2010A&A) opacities and find similar results for our $\Sigma_d$ and $T_d$ profiles" (Footnote 3)
6. **Toomre Q, Stokes number and gas-to-dust ratio**: Sample 1e6 draws of Sigma_d and T; compute Q and St assuming Sigma_g=100 Sigma_d; derive Sigma_g/Sigma_d in ring from tau, St and alpha/St with Q>2 stability  
  > "we combine the probability distributions of $\Sigma_d$ and $T(r)$ by taking $10^6$ random samples from both at each radius value." (4.3)
   - parameter: rho_m=1.675 g/cm3, Q>2 for stability  
  > "We constrain the lowest allowable Stokes number by requiring that the disk be gavitationally stable ($Q > 2$)." (4.4)
   - assumption: Sigma_g/Sigma_d=100 for Q profile  
  > "$\Sigma_g(r) = 100 \ \Sigma_d(r)$ is the local gas surface density" (4.3)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 5.4.0 and 5.6.1: Self-calibration and imaging  
  > "Self-calibration was done with CASA versions 5.4.0 and 5.6.1" (2 Data and Calibration)
- **tclean** : Imaging  
  > "We imaged the data with CASA $\mathtt{tclean}$" (2 Data and Calibration)
- **frankenstein** : Visibility-fit radial profiles  
  > "we use the visibility fitting package $\mathtt{frankenstein}$ (cite: jennings_frank_2020MNRAS)" (3 Radial Profiles)
- **emcee** : MCMC fit of 3 mm disk geometry  
  > "we fit the disk geometry using MCMC (cite: FM_emcee_2013PASP)" (8 frank fitting)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Total dust mass | 13.8 | +0.7/-0.5 | 1e-4 Msun | 5 | $M_\mathrm{dust} = 13.8^{+0.7}_{-0.5} \times 10^{-4} \ M_\odot$ |
| Ring dust width w_d (1.3 mm) | 3.53 | 0.09 | au | 4 | ($2.49 \pm 0.02 \ \mathrm{au}$ versus $3.53 \pm 0.09 \ \mathrm{au}$) |
| Ring dust width w_d (3 mm) | 2.49 | 0.02 | au | 4 | ($2.49 \pm 0.02 \ \mathrm{au}$ versus $3.53 \pm 0.09 \ \mathrm{au}$) |
| alpha_turb range | 8e-4 to 0.03 | not stated | dimensionless | 4 | $8 \times 10^{-4} < \alpha_\mathrm{turb} < 0.03$ |
| Max Sigma_g/Sigma_d in ring | 27 | not stated | dimensionless | 6 | we estimate a maximum gas-to-dust ratio of 27 |
| a_max at 78 au | 0.63 | not stated | cm | 5 | $a_\mathrm{max}(r = 78)$ au $= 0.63$ cm |
| Sigma_d at 78 au | 0.38 | not stated | g cm-2 | 5 | $\Sigma_d(r = 78)$ au$= 0.38$ g cm$^{-2}$ |
| Ring temperature / scale height | Td=11 K, h_p=5.15 au | not stated | K, au | 4 | $T_d(78 \ \mathrm{au}) = 11$ K and a pressure scale-height of $h_p(78 \ \mathrm{au}) = 5.15$ au |
| Gap minimum flux contrast | 0.003 | not stated | dimensionless | 2 | the emission is a factor of $0.003$ times the peak flux in the disk |
| Sigma_d(58 au)/Sigma_d(42 au) | 1/250 | not stated | dimensionless | 5 | $\Sigma_d(58 \ \mathrm{au}) = \Sigma_d(42 \ \mathrm{au})/250$ |

## Qualitative findings

- Ring B77 is a dust trap with larger grains more trapped; gap shallow with shoulder emission consistent with 0.3-1 MJup planet simulations.  
  > "We find clear evidence of efficient dust trapping in B77, the bright ring in the Elias 24 system." (6 Conclusions)

## Claim tuples

- H: Is the B77 ring a dust trap? | E: Compare deconvolved ring widths at 1.3 and 3 mm with pressure scale height; multiband fits | R: w_d < h_p in both bands, narrower at 3 mm; Sigma_d and a_max peak at ring | F: Ring is an efficient dust trap | **supported**
- H: What is the gas-to-dust ratio in the ring? | E: Toomre Q stability with optical depth and Stokes number relation | R: Max Sigma_g/Sigma_d = 27 in ring | F: Gas-to-dust ratio much lower than 100 | **supported**
- H: Is the gap cleared at the planet orbit and what does it say about the planet? | E: Radial profiles at both bands compared with simulations | R: Gap minimum 0.003 of peak flux; shoulder emission | F: Consistent with 0.3-1 MJup, alpha~1e-3 planet-carved gap | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: frank visibility fitting avoids beam convolution and CLEAN PSF mismatch  
  > "To recover radial intensity profiles of higher spatial resolution than those extracted from $\mathtt{CLEAN}$ images via azimuthal averaging (i.e. to avoid beam convolution)" (3 Radial Profiles)
- Alternative: Ricci opacities and p=3.5 tested; similar Sigma_d and Td  
  > "find similar results for our $\Sigma_d$ and $T_d$ profiles" (Footnote 3)
- How they decided it was enough: _not stated_
- Limitation (authors): Only two bands constrain four parameters; priors needed; porosity unconstrained  
  > "we only have 2 bands with which to constrain the 4 model parameters" (4.2)
- Caveat (inferred, ours): a_max prior (>0.072 cm) and Sigma_d IMF prior drive inner-disk results
- Caveat (inferred, ours): Td scaled by 0.5 ad hoc and passive model assumed
- Caveat (inferred, ours): Gas-to-dust bound relies on Q>2 criterion with no observed spirals
- Caveat (inferred, ours): Scale-height formalism assumes Gaussian rings and Sc=1
- Caveat (inferred, ours): Results depend on opacity law (a_max 10x lower with Ricci)

## Reproducibility

- Data public (paper): DSHARP 1.3 mm calibrated visibilities public; 3 mm from ALMA archive programs  
  > "we employ their publicly available calibrated visibilities" (2 Data and Calibration)
- Products in archive: _not stated_
- Missing: Radiative transfer fitting code (Sierra et al. 2021) details and grids
- Missing: tclean image parameters
- Missing: Exact scales/masks
- Data volume (inferred): ~100-300 GB raw for 7 Band 3 executions plus DSHARP visibilities
- Score (inferred): 3/5, Public data and detailed frank settings, but the multiband fit code and several imaging parameters are not given.
- Rediscovery candidate: yes, Data public, frank setup and formulas largely given, numeric results (ring widths, dust mass, gas-to-dust).

## Links

- Method: jennings_frank_2020MNRAS (frankenstein visibility fitting)
- Method: Dullemond_DSHARP_2018ApJ (trapping efficiency formalism)
- Method: Sierra_MAPS_2021ApJS (multiband radiative transfer model)
- Method: Andrews_DSHARP_I_2018ApJ (self-cal and 1.3 mm data)
- Companion: Jorquera_Elias24_CPD_2021AJ (planetary-mass companion detection)
- Companion: pinte_Elias24_CO_2023MNRAS (CO kinematic counterpart)
- Companion: Jennings_frankDSHARP_2022MNRAS (frank analysis of DSHARP data)
- Related: DSHARP
- Related: MAPS

## Checks

```json
{
 "quotes": 77,
 "quotes_ok": 77,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 3,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 10,
 "numeric_problems": 0,
 "fill": {
  "facts": 89,
  "stated": 60,
  "rate": 0.674
 },
 "evidence_ok": true
}
```
