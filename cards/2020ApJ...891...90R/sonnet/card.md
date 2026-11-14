# Pressure Profiles and Mass Estimates Using High-resolution Sunyaev-Zel'dovich Effect Observations of Zwicky 3146 with MUSTANG-2

`2020ApJ...891...90R` | The Astrophysical Journal 2020 | first author: Romero, Charles E. | arXiv: 1908.09200 | DOI: 10.3847/1538-4357/ab6d70

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: galaxy_clusters_and_sz
- Question: Can MUSTANG-2 90 GHz SZ data constrain the pressure profile and mass (M500, M2500) of the relaxed cluster Zwicky 3146, and how consistent are different mass estimators?  
  > "Here, we investigate the ability to estimate the mass of Zwicky 3146 via the Sunyaev-Zel’dovich (SZ) effect with data taken at 90 GHz by MUSTANG-2" (abstract)
- Target **Zwicky 3146**: coordinates _not stated_; z/distance z=0.291  
  > "The galaxy cluster Zwicky 3146 is a sloshing cool core cluster at $z=0.291$" (abstract); "At $z=0.291$, one arcsecond corresponds to 4.36 kpc." (1 Introduction); distance from _not stated_

## Data provenance

- ALMA projects: _none stated_
- bands: MUSTANG-2 90 GHz on the GBT (not ALMA)  
  > "Observing at 90 GHz on the 100-meter Robert C. Byrd Green Bank Telescope (GBT), MUSTANG-2 achieves a resolution of 10$''$" (3.1 MUSTANG-2 observations)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: 15 uK RMS within central 2' radius (beam-smoothed)  
  > "have a RMS noise of $15~\mu$K (when smoothed to beam resolution) within the central $2\ensuremath{'}$ radius" (3.1 MUSTANG-2 observations)
- time on source: 22.7 hours total; 21.4 hours after flagging  
  > "with a total on-source integration time of 22.7 hours. Excising bad scans, our final maps incorporate 21.4 hours of data" (3.1 MUSTANG-2 observations)
- observing dates: _not stated_
- pi or archival as stated: GBT project AGBT18A_175  
  > "GBT data was taken under the project ID AGBT18A_175." (Acknowledgements)
- Other facility **GBT/MUSTANG-2**: 90 GHz SZ data for all main results  
  > "Observing at 90 GHz on the 100-meter Robert C. Byrd Green Bank Telescope (GBT), MUSTANG-2 achieves a resolution of 10$''$" (3.1 MUSTANG-2 observations)
- Other facility **XMM-Newton**: electron density profile for hydrostatic masses and temperature/entropy  
  > "In this work, we make use of an electron density profile from *XMM* (cite: ghirardini2018)." (4.3.2 via hydrostatic equilibrium)
- Other facility **ALMA**: grid calibrators used for MUSTANG-2 flux calibration  
  > "We additionally use ALMA grid calibrators (cite: fomalont2014; vanKempen2014)" (3.1 MUSTANG-2 observations)
- External data: XMM electron density profile  
  > "we make use of an electron density profile from *XMM* (cite: ghirardini2018)." (4.3.2 via hydrostatic equilibrium) [from (cite: ghirardini2018)]
- External data: FIRST radio source positions/fluxes  
  > "There are six radio sources identified by FIRST (cite: becker1994) which correspond to sources found in the MUSTANG-2 maps." (4.1 Compact source removal) [from (cite: becker1994)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Mars, Uranus, Jupiter, Saturn, Ceres, plus ALMA grid calibrators  
  > "Absolute flux calibrations are preferentially based on the Solar System objects Mars, Uranus, Jupiter, Saturn, and Ceres." (3.1 MUSTANG-2 observations)
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
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Observational techniques and data reduction  
  > "Our observational techniques and data reduction are largely the same as with MUSTANG (cite: romero2015a; romero2017)." (3.1 MUSTANG-2 observations) [from (cite: romero2015a; romero2017)]
- gNFW shape parameters alpha, beta, gamma fixed to A10 values  
  > "we choose to fix $\alpha$, $\beta$, and $\gamma$ to their respective values found in (cite: arnaud2010) (hereafter, A10): 1.05, 5.41, and 0.31" (4.2 Pressure profile fitting) [from (cite: arnaud2010)]

### Not stated but needed to reproduce (our reading)

- Minkasi code/version and availability
- MCMC settings and priors for pressure profile fits
- Y-M relation parameters (tabulated A,B but sources unnamed in text)
- Flux calibration uncertainty derivation
- Point source fit details

## Analysis recipe

1. **Map TODs with Minkasi and fit surface brightness annuli**: Maximum-likelihood fit of concentric annuli to TODs, PCG solver, deconvolved profile with covariance  
  > "we opt to fit a surface brightness profile directly to the MUSTANG-2 timestreams within the Minkasi pipeline." (3.2.2 Surface brightness profiles)
   - software: Minkasi
   - parameter: 30 to 60 PCG steps  
  > "We find sufficient convergence with 30 to 60 steps in the PCG." (3.2.1 Minkasi pipeline)
   - fitting: _not stated_
   - validation: Compared with MIDAS pipeline  
  > "A comparison of the performance between the two approaches is in Appendix [11](#sec:appendix_midas_minkasi)" (3.2 MUSTANG-2 data reduction)
2. **Fit pressure profiles (NP and gNFW) with point sources**: Compton y profile to T_B, matched to Minkasi bins with full covariance; 12 NP bins 5'' to 5'; A10 gNFW  
  > "We define twelve bins with twelve logarithmically spaced radii between 5$''$ and 5$'$." (4.2 Pressure profile fitting)
   - software: emcee
   - parameter: relativistic correction with kT_e = 7 keV; line of sight integration to ±5 R500  
  > "we assume $k_B T_e = 7$ keV" (4.2 Pressure profile fitting)
   - assumption: spherical symmetry  
  > "The choice of adopting spherical symmetry is motivated by (1) the ease of interpretation of results and comparison to the literature" (4.2 Pressure profile fitting)
   - fitting: emcee MCMC with full covariance likelihood  
  > "In both cases, the fitting is done with the MCMC package `emcee` (cite: foreman2013)." (4.2 Pressure profile fitting)
   - validation: Agreement with XMM pressure profile  
  > "The pressure profile recovered is in excellent agreement with the pressure profile derived from *XMM*." (7 Conclusions)
3. **Derive M500 and M2500**: Y-M relations, hydrostatic equilibrium with XMM n_e, virial theorem; self-consistent R500 at each MCMC step  
  > "We investigate mass estimates via three avenues: (1) employing a $Y$-$M$ relation, (2) employing spherical hydrostatic equilibrium (HE) and (3) employing the virial theorem (VT)" (4.3 Mass derivations)
   - software: scipy
   - parameter: mu = 0.61; mu_e = 1.17; f_gas = 0.13  
  > "we take $\mu_e = 1.17$ and $f_{\text{gas}} = 0.13$." (4.3.3 via virial equilibrium)
   - assumption: NFW matter profile for VT; central 100 kpc excluded  
  > "We exclude the points within the central 100 kpc" (4.3.3 via virial equilibrium)
   - fitting: VT: scipy curve fit for rho0 and 1/Rs, 1000 iterations  
  > "$M_{500}$ is calculated self-consistently from the NFW mass curve (as for the hydrostatic mass) over 1000 iterations" (4.3.3 via virial equilibrium)
   - validation: _not stated_

## Software

- **Minkasi** : maximum-likelihood TOD map and profile fitting  
  > "the second method is a maximum likelihood approach (Minkasi)." (3.2 MUSTANG-2 data reduction)
- **MIDAS** : IDL pipeline for comparison  
  > "The first method, called the MUSTANG IDL Data Analysis System (MIDAS)" (3.2 MUSTANG-2 data reduction)
- **emcee** : MCMC fitting  
  > "the fitting is done with the MCMC package `emcee` (cite: foreman2013)." (4.2 Pressure profile fitting)
- **photutils** : Herschel photometry of radio sources  
  > "We obtain photometry of point sources from the level 2 maps with `photutils`" (Appendix Radio Sources)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Fiducial M500 (Y-M) | 8.16 | +0.44/-0.54 stat; +0.46/-0.43 Y-M sys; +0.59/-0.55 cal | 1e14 Msun | 3 | We take our fiducial mass to be $8.16^{+0.44}_{-0.54}$ ($\pm 5.5$% stat) |
| M500 from hydrostatic equilibrium | 8.29 | +1.93/-1.24 stat; +0.74/-0.68 cal | 1e14 Msun | 3 | our estimate from hydrostatic equilibrium, is $8.29^{+1.93}_{-1.24}$ |
| Peak decrement (deconvolved) | 1002 | 70 | uK | 1 | we find a peak decrement of $1002 \pm 70$ $\mu$K |
| Entropy slope NP (100-600 kpc) | 1.34 | 0.06 | dimensionless | 0 | $\alpha_{\text{NP}} = 1.34 \pm 0.06$ |

## Qualitative findings

- Pressure profile constrained to better than 15% out to 240'' (twice radial FOV) and matches XMM  
  > "achieving constraints on the pressure profile to better than 15% out to 240$''$, or twice our radial FOV, is a marked improvement." (6.2 Recovery of pressure profile)

## Claim tuples

- H: Can Minkasi recover pressure profile beyond the FOV? | E: Fit NP and gNFW profiles to TODs | R: Constraints <15% to 240'' | F: Agrees with XMM | **supported**
- H: Are mass estimators consistent with each other and with lensing? | E: Y-M, HE, VT masses compared with literature | R: M500 6.23 to 10.6e14; 2 sigma from lensing | F: Systematic mass uncertainties remain | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Outermost pressure bin likely biased low; unquantified additional systematic  
  > "there is an additional systematic error due the issues discussed in the previous two paragraphs, but which we are currently unable to quantify." (7 Conclusions)
- Caveat (inferred, ours): Hydrostatic bias comes out negative, suggesting problems in data or Y-M relations
- Caveat (inferred, ours): Spherical assumption despite central ellipticity

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Minkasi code and MUSTANG-2 TODs
- Missing: Y-M relation sources
- Missing: MCMC priors
- Data volume (inferred): not applicable to ALMA; GBT TODs of ~22 hours
- Score (inferred): 2/5, Data are GBT MUSTANG-2, not ALMA; ALMA only calibrators.
- Rediscovery candidate: no, No ALMA science data; pipeline code and TODs not described as public.

## Links

- Method: (cite: romero2015a; romero2017) (MUSTANG data reduction approach)
- Related: MUSTANG-2
- Related: FIRST

## Checks

```json
{
 "quotes": 41,
 "quotes_ok": 41,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 0,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [
  "2011.0.00001.CAL"
 ],
 "numeric_results": 4,
 "numeric_problems": 0,
 "fill": {
  "facts": 70,
  "stated": 32,
  "rate": 0.457
 },
 "evidence_ok": true
}
```
