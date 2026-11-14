# The ALMA early science view of FUor/EXor objects - V. Continuum disc masses and sizes

`2018MNRAS.474.4347C` | Monthly Notices of the Royal Astronomical Society 2018 | first author: Cieza, Lucas A. | arXiv: 1711.08693 | DOI: 10.1093/mnras/stx3059

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks, star_formation
- Question: How do the continuum disc masses and sizes of FUor and EXor outbursting objects differ, and what does this imply for outburst mechanisms and evolutionary stage?  
  > "here we focus on the continuum data and the differences and similarities between the FUor and EXor populations." (abstract)
- Target **V883 Ori, HBC 494, V2775 Ori, V1647 Ori, NY Ori, V1143 Ori, V1118 Ori, ASASSN-13db**: coordinates _not stated_; z/distance 414±7 pc  
  > "Adopting the distance of 414$\pm$7 pc from Menten et al. (2007) to the Orion Nebula Cluster" (4.1 Dust masses); distance from Menten et al. (2007), Orion Nebula Cluster  
  > "Adopting the distance of 414$\pm$7 pc from Menten et al. (2007) to the Orion Nebula Cluster" (4.1 Dust masses)

## Data provenance

- ALMA projects: 2013.1.00710.S
- bands: Band 6 (230 GHz, 1.3 mm)  
  > "Here we present results from a small ALMA 230 GHz (band-6) survey of eight outbursting sources" (1 Introduction)
- frequencies and spectral setup: Three 58.6 GHz SPWs at 230.5380, 220.3987, 219.5603 GHz (12CO, 13CO, C18O 2-1); two 1.875 GHz continuum SPWs at 232.6 and 218.0 GHz  
  > "Two additional spectral windows with 1.875 GHz bandwidths were centered at 232.6 and 218.0 GHz and were selected for continuum observations." (2.2 Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: 34 antennas, baselines 14.6-348.5 m (Dec 2014, Apr 2015); 35 antennas, 42-1574 m (Aug 2015)  
  > "The third observations were on August 30th, 2015 with an array of 35 antennas and longer baselines of 42-1574m." (2.2 Observations)
- baselines: _not stated_
- angular resolution: 0.25" combined  
  > "The data set combining the two array configurations reached a resolution of 0.25$''$ while maintaining a maximum recoverable scale of 11$''$." (2.2 Observations)
- max recoverable scale: 11"  
  > "The data set combining the two array configurations reached a resolution of 0.25$''$ while maintaining a maximum recoverable scale of 11$''$." (2.2 Observations)
- sensitivity: continuum rms 0.07 mJy/beam  
  > "For the continuum, we obtained a rms of 0.07 mJy beam$^{-1}$ and a synthesized beam of 0.25$''$ $\times$ 0.17$''$ with P.A. = $-$85 deg." (2.3 Data reduction)
- time on source: 122 s per science target  
  > "The total integration time was 122 s per science target." (2.2 Observations)
- observing dates: 2014-12-12, 2015-04-05, 2015-08-30  
  > "Two of three observations took place on December 12$^{th}$, 2014 and April 5$^{th}$, 2015." (2.2 Observations)
- pi or archival as stated: _not stated_
- Line: 12CO J=2-1 (not stated)
- Line: 13CO J=2-1 (not stated)
- Line: C18O J=2-1 (not stated)
- External data: Object type, spectral type, Lbol, companions for sources  
  > "The data for the four top rows (Object Type, Spectral Type, and L$_{Bol}$, and Companions) are taken from the review by Audard et al. (2014)" (Table 1) [from Audard et al. (2014) (cite: Audard2014)]
- External data: T Tauri disc Rc, Md, gamma values for comparison  
  > "The 16 T Tauri stars studied by Andrews et al. (2010) have $\gamma$ values ranging from 0.4 to 1.1 with a mean of 0.87$\pm$0.17." (4.2.2 Comparison) [from Andrews et al. (2010)]

## Processing

### Calibration

- pipeline or manual: Standard calibration by the ALMA observatory  
  > "All data were calibrated using the Common Astronomy Software Applications package (CASA v4.4; McMullin et al. 2007) by the ALMA observatory." (2.3 Data reduction)
- casa version: CASA v4.4  
  > "The visibility data were also edited, calibrated, and imaged using CASA v4.4." (2.3 Data reduction)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Ganymede  
  > "Ganymede was used as flux calibrator" (2.2 Observations)
- flux scale uncertainty: 7% for band 6  
  > "estimated at the 7$\%$ level for band-6 observations (ALMA Technical Handbook for Cycle 3)." (3.1 Continuum)
- self calibration: _not stated_

### Imaging

- task: CLEAN in CASA 4.4; three nights concatenated  
  > "The observations from all three nights were concatenated and processed together to increase the signal to noise and *uv*-coverage." (2.3 Data reduction)
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 0  
  > "using a robust parameter equal to zero, a briggs weighting was performed" (2.3 Data reduction)
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
- final beam: 0.25" x 0.17", PA -85 deg (continuum)  
  > "a synthesized beam of 0.25$''$ $\times$ 0.17$''$ with P.A. = $-$85 deg." (2.3 Data reduction)
- final rms: 0.07 mJy/beam continuum; 12.5, 16.0, 13.9 mJy/beam for 12CO, 13CO, C18O  
  > "the rms is 12.5 mJy beam$^{-1}$ for $^{12}$CO, 16.0 mJy beam$^{-1}$ for $^{13}$CO and 13.9 mJy beam$^{-1}$ for C$^{18}$O" (2.3 Data reduction)

### Inherited from earlier work

- Disc parameterization (power-law with exponential taper)  
  > "we adopt the parameterization presented by Andrews et al. 2009." (4.2 Radiative transfer modeling) [from Andrews et al. 2009]
- Model visibilities computed via FFT of model images (code not described)  
  > "The model visibilities are obtained by taking the Fast Fourier Transform of model images and interpolating to the same *uv* points as the observations (Marino et al. in prep)." (4.2 Radiative transfer modeling) [from Marino et al. in prep]
- Dust opacity law for dust masses  
  > "dust opacity ($\kappa_{\nu}$ = 10($\nu/$1000 GHz)cm$^2$g$^{-1}$; Beckwith et al. 1990)" (4.1 Dust masses) [from Beckwith et al. 1990]

### Not stated but needed to reproduce (our reading)

- Image size, cell size, clean threshold and masks
- Continuum SPW flagging of line channels and any continuum subtraction
- Self-calibration status
- Stellar luminosity/Rstar treatment details and radial grid of RADMC-3D models
- Weights and uv binning used in the MCMC
- Reference position/phase center and distance used per source in RT model
- Exact imfit regions

## Analysis recipe

1. **Image the continuum**: Concatenate three executions and CLEAN with Briggs weighting  
  > "We used the CLEAN algorithm to image the data, and using a robust parameter equal to zero, a briggs weighting was performed" (2.3 Data reduction)
   - software: CASA
   - parameter: robust = 0  
  > "using a robust parameter equal to zero, a briggs weighting was performed" (2.3 Data reduction)
   - fitting: _not stated_
   - validation: _not stated_
2. **Measure fluxes, sizes, inclinations**: 2D Gaussian fits with IMFIT; inclination from minor/major axis ratio  
  > "We use the IMFIT routine within CASA to fit two dimensional Gaussians to the continuum data and derive both continuum fluxes and disc sizes" (3.1 Continuum)
   - software: CASA
   - fitting: _not stated_
   - validation: Compared fluxes with Liu et al. 2016 SMA and Cieza et al. 2016 ALMA  
  > "Our fluxes for NY Ori and V1118 Ori agree well with those presented by Liu et al. (2016)" (3.1 Continuum)
3. **Derive dust and disc masses from flux**: Optically thin formula M=F d^2/(kappa B(T)); gas-to-dust 100  
  > "M_{dust}  [M_{\oplus}] =  5.0 \times F_{1.3}  (mJy)" (4.1 Dust masses)
   - assumption: d = 414 pc, Tdust = 20 K, kappa = 10(nu/1000 GHz) cm2/g, gas-to-dust 100  
  > "we also calculate the disc masses adopting a standard gas-to-dust mass ratio of 100" (4.1 Dust masses)
   - fitting: _not stated_
   - validation: _not stated_
4. **Radiative transfer + MCMC visibility fit of five resolved discs**: RADMC-3D models with Andrews et al. 2009 surface density; emcee fit to visibilities; each disc fit separately  
  > "We construct radiative transfer models using the RADMC-3D code (Dullemond et al. 2012), to derive the physical properties of the spatially resolved discs." (4.2 Radiative transfer modeling)
   - software: RADMC-3D, emcee
   - parameter: Priors uniform: Mdisc 0.001-1 Msun, gamma 0-2, Rc 10-100 au, hc 1-10 au, psi 0-2, Rstar 1-8 Rsun, i 10-80 deg  
  > "our priors for the free parameters come from assuming uniform distributions in the following intervals." (4.2 Radiative transfer modeling)
   - parameter: ~100 walkers, 1000 iterations  
  > "after running 1000 iterations ($\sim10$ times the autocorrelation time) with approximately 100 walkers" (4.2 Radiative transfer modeling)
   - assumption: 10,000 K blackbody central source with L=Lbol; amax 3 mm, n(a)∝a^-3.5; kappa_abs(1.3mm)=2.2 cm2/g; viscous heating ignored  
  > "we model the central heating source as a 10,000 K blackbody (an A0-type star to be precise) with a luminosity equal to the bolometric luminosity of the system" (4.2 Radiative transfer modeling)
   - fitting: Likelihood ∝ exp(-chi2/2) with f_sigma weight scaling; Goodman-Weare ensemble sampler; uniform priors  
  > "The likelihood function is proportional to $\exp[-\chi^2/2]$" (4.2 Radiative transfer modeling)
   - validation: Compared to Gaussian-fit and flux-based masses and sizes; residual map for HBC 494  
  > "We note that the disc masses derived from the radiative transfer modeling agree with the values calculated from Equation 2 (see Table 1)" (4.2.1 Radiative transfer results)
5. **Compare with T Tauri discs**: Place Rc, Mdisc, gamma on Md-Rc plane with Andrews et al. 2010 sample  
  > "Figure [6](#fig:mdvsrc) places our sample of outbursting sources in the M$_d$ vs. R$_c$ plane together with the objects studied by Andrews et al. (2010)." (4.2.2 Comparison)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.4: Calibration, CLEAN imaging, IMFIT  
  > "The visibility data were also edited, calibrated, and imaged using CASA v4.4." (2.3 Data reduction)
- **RADMC-3D** : Radiative transfer disc models  
  > "We construct radiative transfer models using the RADMC-3D code (Dullemond et al. 2012)" (4.2 Radiative transfer modeling)
- **emcee** : MCMC sampling of model parameters  
  > "We used the publicly available python module *emcee* to sample the parameter space" (4.2 Radiative transfer modeling)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| 1.3 mm flux V883 Ori | 353 | ±35 | mJy | 2 | / F$_{1.3mm}$ \[mJy\] / 353$\pm$35 / 113$\pm$11 / 106$\pm$10 / 78$\pm$8 / 32$\pm$3 / 2.3$\pm$0.2 / 1.3$\pm$0.1 / 0.3$\pm$0.07 / |
| Mdisc V883 Ori (RT fit) | 600 | +50/-60 | MJup | 4 | / V883 Ori / 31$^{+6}_{-6}$ / 600$^{+50}_{-60}$ / 1.48$^{+0.04}_{-0.06}$ / |
| Rc V2775 Ori | 42 | +2/-2 | au | 4 | / V2775 Ori / 42$^{+2}_{-2}$ / 80$^{+10}_{-10}$ / 1.44$^{+0.06}_{-0.06}$ / |
| gamma HBC 494 | 1.94 | +0.04/-0.30 | dimensionless | 4 | / HBC 494 / 21$^{+7}_{-12}$ / 100$^{+70}_{-80}$ / 1.94$^{+0.04}_{-0.30}$ / |
| Dust mass of ASASSN-13db | 1.5 | not stated | Mearth | 3 | / M$_{DUST}$ \[M$_{\oplus}$\] / 1800 / 570 / 530 / 390 / 160 / 12 / 6.5 / 1.5 / |

## Qualitative findings

- EXor sources lack the prominent outflows seen in FUors  
  > "We also report that the EXor sources lack the prominent outflows seen in the FUor population." (abstract)
- V1118 Ori resolved into two millimetre sources; HBC 494 disc asymmetric  
  > "The disc around HBC 494 is asymmetric, hinting at a structure in the outer disc or the presence of a second disc." (abstract)

## Claim tuples

- H: FUor and EXor discs differ in mass | E: 1.3 mm continuum fluxes converted to masses | R: FUor ~80-600 MJup vs EXor ~0.5-40 MJup | F: FUor and EXor may represent different evolutionary stages | **supported**
- H: FUor discs are structurally different from T Tauri discs | E: RT/MCMC fits compared to Andrews et al. 2010 | R: Small Rc for mass and larger gamma | F: FUor discs are massive, compact, centrally concentrated | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Dust opacity, temperature and distance uncertainties; small sample  
  > "we note that significant uncertainties exists in the dust opacities, temperatures and distances" (4.1 Dust masses)
- Caveat (inferred, ours): Small sample; classification-dependent conclusions
- Caveat (inferred, ours): Fixed T=20 K and opacity for very luminous FUors
- Caveat (inferred, ours): Resolution of 80 au limits Rc and structure constraints
- Caveat (inferred, ours): Model-dependent masses differ by up to 50% from flux-based

## Reproducibility

- Data public (paper): ALMA program cited; public status not explicitly stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA #2013.0.00710.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Imaging parameters beyond robust=0
- Missing: RT model grid and visibility-fitting code (Marino in prep)
- Data volume (inferred): ~50-150 GB raw for three executions
- Score (inferred): 3/5, Data identified and main steps given, but imaging details and fitting code are missing.
- Rediscovery candidate: no, Visibility MCMC code not available and imaging details missing, though flux-based results are reproducible.

## Links

- Method: Andrews et al. 2009 (Disc surface density parameterization)
- Companion: Zurlo et al. 2017; Ruiz-Rodriguez et al. 2017a,b; Principe et al. 2017 (Outflows in V2775 Ori, HBC 494, V883 Ori, V1647 Ori)
- Companion: Cieza et al. 2016 (Long-baseline ALMA study of V883 Ori)

## Checks

```json
{
 "quotes": 56,
 "quotes_ok": 56,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [
  "2013.0.00710.S"
 ],
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 74,
  "stated": 44,
  "rate": 0.595
 },
 "evidence_ok": true
}
```
