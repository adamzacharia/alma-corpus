# A Cavity of Large Grains in the Disk around the Group II Herbig Ae/Be Star HD 142666

`2018ApJ...860....7R` | The Astrophysical Journal 2018 | first author: Rubinstein, A. E. | arXiv: 1804.07343 | DOI: 10.3847/1538-4357/aabfba

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: protoplanetary_disks
- Question: Does the disk of the Group II Herbig Ae star HD 142666 contain a cavity or gap in large dust grains, as constrained by SED plus ALMA 1.3 mm modeling?  
  > "We analyzed the disk around the Group II source, HD 142666, using irradiated accretion disk modeling of the broad-band spectral energy distribution along with the 1.3 millimeter spatial brightness distribution" (abstract)
- Target **HD 142666 (V1026 Sco)**: coordinates _not stated_; z/distance d=150.1 pc  
  > "located in the Upper Sco OB-2 association (Sandell et al. 2011; d=150.1 pc; Gaia Collaboration et al. 2016a)" (1. Introduction); distance from Gaia Collaboration et al. 2016a  
  > "located in the Upper Sco OB-2 association (Sandell et al. 2011; d=150.1 pc; Gaia Collaboration et al. 2016a)" (1. Introduction)

## Data provenance

- ALMA projects: 2013.1.00498.S
- bands: Band 6 (1.3 mm)  
  > "HD 142666 was observed on July 21, 2015 at Band 6 using an array of 44 antennas." (2.2 ALMA Observations)
- frequencies and spectral setup: Two continuum SPWs centered at 216.974 and 232.349 GHz, each 1.875 GHz wide  
  > "Two spectral windows (SPW) centered at 216.974 and 232.349 GHz were used to detect the continuum, each with a bandwidth of 1.875 GHz." (2.2 ALMA Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.200 x 0.165 arcsec beam (uniform weighting)  
  > "resulting in a synthesized beam of 0.”200 _×_ 0.”165" (2.2 ALMA Observations)
- max recoverable scale: _not stated_
- sensitivity: rms 0.22 mJy/beam  
  > "an rms sensitivity of 0.22 mJy beam _[−]_ [1]" (2.2 ALMA Observations)
- time on source: 59.04 minutes  
  > "The total on-source time was 59.04 minutes." (2.2 ALMA Observations)
- observing dates: July 21, 2015  
  > "HD 142666 was observed on July 21, 2015 at Band 6" (2.2 ALMA Observations)
- pi or archival as stated: Archival, Cycle 2, PI L. Pérez  
  > "We used Cycle 2 ALMA archival observations (PI: L. P´erez)" (2.2 ALMA Observations)
- Other facility **Spitzer IRS, 2MASS, AKARI, IRAS, Tycho-2, WISE, Herschel and literature photometry**: Archival SED photometry and IRS spectrum  
  > "we gathered the IRS spectrum (Keller et al. 2008) and visible to mm photometry from 2MASS, AKARI, IRAS, Tycho-2, WISE" (2.1 Stellar Properties and the SED)
- External data: IRS spectrum  
  > "we gathered the IRS spectrum (Keller et al. 2008)" (2.1 Stellar Properties and the SED) [from Keller et al. 2008]
- External data: Teff of 7580 K and intrinsic (B-V)0  
  > "a T eff of 7580 K following Kenyon & Hartmann (1995)." (Table 1) [from Kenyon & Hartmann (1995)]
- External data: Spectral type A8  
  > "We adopt a spectral type of A8 spectral type from Mora et al. (2001)" (Table 1) [from Mora et al. 2001]
- External data: Mass accretion rate range 1e-8 to 2e-7 Msun/yr  
  > "has been measured to be between 1 x 10 _[−]_ [8] and 2 x" (2.1 Stellar Properties and the SED) [from Salyk et al. 2013; Mendigutía et al. 2011; Donehew & Brittain 2011; Garcia Lopez et al. 2006]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: QSOs J1517-2422 and J1627-2426 (flux); Titan (bandpass)  
  > "The observations were flux calibrated with the QSOs J1517-2422 and J1627-2426 and bandpass calibrated with Titan." (2.2 ALMA Observations)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA CLEAN, interactive  
  > "We used the CLEAN task in CASA interac tively to obtain deconvolved images from the observed visibilities." (2.2 ALMA Observations)
- deconvolver: _not stated_
- weighting robust: uniform weighting  
  > "We chose a uniform weighting" (2.2 ALMA Observations)
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
- final beam: 0.200 x 0.165 arcsec  
  > "a synthesized beam of 0.”200 _×_ 0.”165" (2.2 ALMA Observations)
- final rms: 0.22 mJy/beam  
  > "an rms sensitivity of 0.22 mJy beam _[−]_ [1]" (2.2 ALMA Observations)

### Inherited from earlier work

- Parametric surface brightness profile fit to visibilities  
  > "we fit the visibilities using a parametric model of the surface brightness profile of the disk as in Zhang et al. (2016)." (2.2 ALMA Observations) [from Zhang et al. (2016)]
- Disk model with irradiated accretion, settling and wall  
  > "using the physically self-consistent disk model by D’Alessio et al. (2006)." (3.1 Modeling Procedure) [from D’Alessio et al. (2006)]
- Wall emission calculation  
  > "The wall emission was calculated following D’Alessio et al. (2005)." (3.1 Modeling Procedure) [from D’Alessio et al. (2005)]

### Not stated but needed to reproduce (our reading)

- Which CASA version and calibration (pipeline vs manual) were used
- CLEAN mask, threshold, cell and image size
- Parametric visibility model functional form and fitting method details
- Dust opacity law and composition used in disk model
- Stellar parameters other than Table 1 and fixed model parameters (e.g. dust-to-gas details, grain composition)
- Exact fitting weights between SED chi2 and visibility comparison
- Photometry values used in the SED
- Whether the disk center and deprojection parameters were fixed
- Flux calibration scale uncertainty

## Analysis recipe

1. **Build and deredden SED, derive stellar properties**: Dereddened with Mathis (1990) law; luminosity from dereddened V; mass from Siess tracks  
  > "This luminosity, together with the effective temperature, was compared with evolutionary tracks (Siess et al. 2000) to obtain a stellar mass." (2.1 Stellar Properties and the SED)
   - assumption: R_V = 3.1, giving A_V = 0.992  
  > "Assuming R _V_ = 3.1, we obtained A _V_ = 0.992." (2.1 Stellar Properties and the SED)
   - fitting: _not stated_
   - validation: _not stated_
2. **Image and characterize continuum emission**: CLEAN image; 1x1 arcsec box flux; Gaussian fit for center, PA, FWHM, inclination; deprojection of visibilities minimizing scatter  
  > "The values that resulted in the minimum scatter in the real and imaginary parts of the visibilities were consistent with the results found by the Gaussian fit." (2.2 ALMA Observations)
   - software: CASA
   - fitting: Gaussian image fit; parametric brightness profile fit to visibilities  
  > "we fit the visibilities using a parametric model of the surface brightness profile of the disk as in Zhang et al. (2016)." (2.2 ALMA Observations)
   - validation: Gaussian fit consistent with flux in box  
  > "we estimated a flux density of 113 _±_ 6 mJy, consistent with the results of a Gaussian fit to the image." (2.2 ALMA Observations)
3. **Fit SED and ALMA data with physical disk model grid**: Grid of D'Alessio irradiated accretion disk models with cavity in large grains; best SED fit by chi2; model images Fourier transformed, sampled at ALMA uv, cleaned and compared with visibilities and radial profile  
  > "From the grid of parameters tested, the models that best fit the SED were obtained by minimizing the _χ_ [2] ." (3.1 Modeling Procedure)
   - software: CASA
   - parameter: Grid ranges in Table 2, e.g. R_cav 8-20 au, delta_cav 1-0.001, i 40-70 deg  
  > "R cav (au) 8 – 20 15.6" (Table 2)
   - assumption: Grain size distribution n(a) ∝ a^-3.5, a_min = 0.005 um; alpha fixed at 0.01; dust-to-gas 0.01  
  > "two populations of grains with size distributions _n_ ( _a_ ) _∝_ _a_ _[−]_ [3] _[.]_ [5] between a minimum size, _a_ _min_ = 0 _._ 005 _µ_ m" (3.1 Modeling Procedure)
   - fitting: Grid search with chi2 minimization for SED; visibility/profile comparison by eye  
  > "The simulated visibilities and images were compared with the observed visibilities and the averaged radial profile of the disk, respectively." (3.1 Modeling Procedure)
   - validation: Full disk models without cavity compared and failed to reproduce visibilities  
  > "Full disk models always failed to reproduce the visibilities and the inner parts of the radial profile (Figures 2 and 3)." (3.2 Disk Properties)

## Software

- **CASA** : Calibration and CLEAN imaging  
  > "The data were calibrated using the reduction package Common Astronomy Software Applications (CASA: McMullin et al. 2007)." (2.2 ALMA Observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Continuum flux density at 1.38 mm | 113 | 6 | mJy | 2 | we estimated a flux density of 113 _±_ 6 mJy |
| Cavity radius in large grains (best fit) | 15.6 | not stated | au | 3 | R cav (au) 8 – 20 15.6 |
| Parametric model intensity drop radius | <9.5 | not stated | au | 2 | The resulting intensity profile shows a drop in intensity at R _<_ 9.5 au. |
| Dust mass of disk | 5.3e-4 | not stated | Msun | 3 | found a mass of 5.3 _×_ 10 _[−]_ [4] M _⊙_ . |
| Settling parameter epsilon | 0.001 | not stated | dimensionless | 3 | We also found a high degree of settling in the disk ( _ϵ_ = 0.001) |
| Inner wall radius | 1.3 | not stated | au | 3 | inner edge of the disk (R wall ) of 1.3 au |
| Outer disk radius R_d | 65 | not stated | au | 3 | R d (au) 30 – 100 65 |

## Qualitative findings

- Small grains fill the cavity; the cavity exists only in large grains.  
  > "Our detailed modeling of HD 142666 also indicates that no corresponding cavities exist in the small grains." (4. Discussion)

## Claim tuples

- H: Does the Group II disk HD 142666 have a cavity in large grains? | E: Joint SED and ALMA visibility/image modeling with and without a large-grain cavity | R: Full disk models fail; best fit has cavity out to 15.6 au | F: Group II disks can have cavities of large grains | **supported**
- H: Is HD 142666 highly settled, consistent with Group II? | E: Disk model fit | R: epsilon = 0.001 | F: High degree of settling consistent with Group II | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Self-shadowing cannot explain the cavity since mm emission probes the midplane  
  > "this cannot explain the cavity revealed by the ALMA observations since the radio emission probes dust in the midplane" (4. Discussion)
- How they decided it was enough: _not stated_
- Limitation (authors): Resolution insufficient to fully resolve the inner disk  
  > "the ALMA observations did not have enough angular resolution to fully resolve the inner parts of the disk" (abstract)
- Caveat (inferred, ours): Cavity inferred from a null in visibilities at beam-limited resolution; grid is coarse with no parameter uncertainties
- Caveat (inferred, ours): Fit quality for visibilities judged qualitatively, no chi2 for ALMA
- Caveat (inferred, ours): Many parameters degenerate; the alpha value is fixed
- Caveat (inferred, ours): Only one SPW shown

## Reproducibility

- Data public (paper): Archival ALMA data used  
  > "We used Cycle 2 ALMA archival observations (PI: L. P´erez)" (2.2 ALMA Observations)
- Products in archive: _not stated_
- Missing: Photometry table
- Missing: D'Alessio disk model code
- Missing: Imaging parameters like mask and cell size
- Missing: Visibility fit details
- Data volume (inferred): ~5-10 GB raw single-execution Band 6 continuum
- Score (inferred): 4/5, Public data and a clear outline, but the disk model code and many imaging and fitting details are missing and no uncertainties are given.
- Rediscovery candidate: no, The model code is not public and the fitting recipe is incomplete.

## Links

- Method: D’Alessio et al. (2006) (Disk structure model used)
- Method: Zhang et al. (2016) (Parametric visibility modeling approach)

## Checks

```json
{
 "quotes": 49,
 "quotes_ok": 49,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 67,
  "stated": 38,
  "rate": 0.567
 },
 "evidence_ok": true
}
```
