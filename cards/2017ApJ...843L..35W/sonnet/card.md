# ALMA Observations of the Gravitational Lens SDP.9

`2017ApJ...843L..35W` | The Astrophysical Journal Letters 2017 | first author: Wong, Kenneth C. | arXiv: 1707.00702 | DOI: 10.3847/2041-8213/aa7d4a

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies
- Question: What are the ALMA Band 6 continuum and CO(6-5) morphology of the lensed SMG SDP.9, what is the lens mass model, and can the central image be detected to constrain the SMBH mass?  
  > "We search for the central image of the lens, which can be used constrain the inner mass distribution of the lens galaxy including the central supermassive black hole" (abstract)
- Target **SDP.9 (H-ATLAS J090740.0-004200)**: coordinates _not stated_; z/distance z_L=0.6129, z_S=1.5747  
  > "SDP.9 consists of a massive early-type galaxy at $z_{\mathrm{L}} = 0.6129$ (cite: bussmann+2013) lensing a background submillimeter galaxy at $z_{\mathrm{S}} = 1.5747$" (1 Introduction); distance from z_L from Bussmann+2013; z_S measured from ALMA CO(6-5)  
  > "SDP.9 consists of a massive early-type galaxy at $z_{\mathrm{L}} = 0.6129$ (cite: bussmann+2013) lensing a background submillimeter galaxy at $z_{\mathrm{S}} = 1.5747$" (1 Introduction)

## Data provenance

- ALMA projects: 2015.1.00415.S
- bands: Band 6 continuum plus CO(6-5)  
  > "The Band 6 continuum was observed, as well as the CO $J$=6–5 line" (2.1 ALMA Data)
- frequencies and spectral setup: 4 SPWs of 1.875 GHz, 31.2 MHz resolution (TDM), centered 251.5, 254.0, 266.2, 268.3 GHz; last tuned to CO(6-5)  
  > "The spectral windows are centered at 251.5, 254.0, 266.2, and 268.3 GHz. The last one is tuned for the CO(6–5) at the source redshift." (2.1 ALMA Data)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: C36-7  
  > "baselines ranged from 84.7 m to 16.2 km with the C36-7 configuration." (2.1 ALMA Data)
- baselines: 84.7 m to 16.2 km, 49 12 m antennas  
  > "49 12 m antennas were used, and baselines ranged from 84.7 m to 16.2 km with the C36-7 configuration." (2.1 ALMA Data)
- angular resolution: CO 35x23 mas; continuum 36x24 mas natural, 28x19 mas robust 0.5  
  > "The resulting synthesized beam FWHM are $36 \times 24$ mas (PA=$50^{\circ}$) and $28 \times 19$ mas (PA=$58^{\circ}$), respectively" (2.1 ALMA Data)
- max recoverable scale: _not stated_
- sensitivity: CO 0.13 mJy/beam per 10 km/s channel; continuum 0.012 mJy/beam  
  > "with a root mean square (rms) noise level of 0.13 mJy beam$^{-1}$ per 10 km s$^{-1}$ channel" (2.1 ALMA Data)
- time on source: 4526 s  
  > "The total on-source time was 4526 s" (2.1 ALMA Data)
- observing dates: 2015 November  
  > "The observations were carried out in 2015 November." (2.1 ALMA Data)
- pi or archival as stated: PI: K. Wong, Cycle 3  
  > "(Program 2015.1.00415.S; PI: K. Wong)" (2.1 ALMA Data)
- Line: CO J=6-5 (691.47 GHz)
- Other facility **HST WFC3**: Archival F160W imaging (3718 s) used for lens light and mass modeling  
  > "The observations consist of 3718 s of exposure time in the F160W filter." (2.2 HST Data)
- Other facility **SDSS**: Absolute astrometry for HST alignment  
  > "We use the positions of nine stars in the *HST* field of view and match them to SDSS" (3 Lens Model)
- External data: MAMBO 1200 um flux 7.6±1.4 mJy  
  > "($F_{1200} = 7.6 \pm 1.4$ mJy) (cite: negrello+2014)" (2.1 ALMA Data) [from (cite: negrello+2014)]
- External data: Stellar mass used for SMBH prior  
  > "using the stellar mass measurement from (cite: negrello+2014)" (3 Lens Model) [from (cite: negrello+2014)]
- External data: Lens redshift 0.6129  
  > "massive early-type galaxy at $z_{\mathrm{L}} = 0.6129$ (cite: bussmann+2013)" (1 Introduction) [from (cite: bussmann+2013)]

## Processing

### Calibration

- pipeline or manual: standard manner (details not given)  
  > "The calibration is done in a standard manner" (2.1 ALMA Data)
- casa version: CASA 4.5.0 (imaging)  
  > "Common Astronomy Software Applications (cite: mcmullin+2007) version 4.5.0" (2.1 ALMA Data)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: ~10%  
  > "the uncertainty of the flux calibration is $\sim$10 %" (2.1 ALMA Data)
- self calibration: _not stated_

### Imaging

- task: CASA clean  
  > "In executing the CASA task `clean`, we apply the natural weighting for the CO line" (2.1 ALMA Data)
- deconvolver: _not stated_
- weighting robust: CO natural; continuum natural and Briggs robust=0.5  
  > "For the continuum, we use both the natural and Briggs weighting (robust=0.5)." (2.1 ALMA Data)
- uv taper: none  
  > "We do not taper either image." (2.1 ALMA Data)
- cell size: _not stated_
- image size: _not stated_
- masking: deconvolved down to 1.5 sigma  
  > "We use the `clean` task to deconvolve the synthesized beam down to 1.5$\sigma$." (2.1 ALMA Data)
- multiscale scales: _not stated_
- continuum subtraction: uvcontsub  
  > "We use the CASA task `uvcontsub` to subtract the line emission from the continuum." (2.1 ALMA Data)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: CO 35x23 mas PA 49 deg  
  > "is $35 \times 23$ mas with a position angle (PA) of $49^{\circ}$" (2.1 ALMA Data)
- final rms: 0.13 mJy/beam per 10 km/s (CO); 0.012 mJy/beam (continuum)  
  > "with rms noise levels of 0.012 mJy beam$^{-1}$ for both" (2.1 ALMA Data)

### Inherited from earlier work

- SMBH inference approach follows Wong+2015  
  > "in a manner similar to (cite: wong+2015)" (4.2 SMBH Mass Inference) [from (cite: wong+2015)]
- Lens modeling with Glee  
  > "Glee, a lens modeling software developed by A. Halkola and S. H. Suyu (cite: suyuhalkola2010; suyu+2012)" (3 Lens Model) [from (cite: suyuhalkola2010; suyu+2012)]

### Not stated but needed to reproduce (our reading)

- Line-free channels and channel range for uvcontsub
- Image size and cell size
- Clean mask and iteration/threshold details
- Calibration pipeline vs manual and CASA calibration version
- Locations of the conjugate points
- Sampler and prior details for Glee fits
- Which calibrator was bandpass
- Velocity range used for integrated CO map

## Analysis recipe

1. **Image continuum and CO**: CASA clean with natural weighting for CO; natural and Briggs for continuum; uvcontsub  
  > "We use the CASA task `uvcontsub` to subtract the line emission from the continuum." (2.1 ALMA Data)
   - software: CASA
   - parameter: robust=0.5, no taper, clean to 1.5 sigma  
  > "We do not taper either image." (2.1 ALMA Data)
   - fitting: _not stated_
   - validation: Continuum flux consistent with MAMBO, so missing flux negligible  
  > "suggesting that the missing flux is negligible" (2.1 ALMA Data)
2. **Measure fluxes and source redshift**: Peak and total flux per arc; redshift from CO flux integrated across both arcs in each velocity bin  
  > "Taking the CO line flux integrated across both arcs in each velocity bin, we measure a more accurate source redshift" (2.1 ALMA Data)
   - fitting: _not stated_
   - validation: Compared with previous Z-Spec redshift  
  > "in comparison with the previous measurement of $z_{\mathrm{S}} = 1.577 \pm 0.008$" (2.1 ALMA Data)
3. **Fit lens light in HST**: Two cored power-law profiles plus point source with linked centroids; then fix light and fit arcs for mass model  
  > "The best fit comes from a combination two cored power-law profiles and a point source with their centroids linked" (3 Lens Model)
   - software: Glee
   - parameter: core radius uniform prior max 0.065 arcsec; SMBH mass lognormal prior 7.1-9.9 in log10 M  
  > "The core radius is given a uniform prior with a maximum extent of 0.065$''$" (3 Lens Model)
   - assumption: Cored elliptical power-law mass with central point mass and external shear; Chabrier IMF  
  > "We assume a cored elliptical power-law mass distribution with a central point mass (representing the SMBH) and external shear." (3 Lens Model)
   - fitting: Priors on structural parameters from HST fit used for ALMA fit  
  > "we first fit to the extended arcs in the *HST* data and use the constraints on the structural parameters as priors" (3 Lens Model)
   - validation: Comparison with Dye+2014 model; also modeled with glafic with similar results  
  > "We have also modeled the ALMA constraints with glafic (cite: oguri2010) and obtained similar results." (3 Lens Model)
4. **Fit lens model to ALMA conjugate points**: Four conjugate-point pairs per arc; uncertainties 0.02 arcsec radial, 0.05 arcsec tangential; centroid free with 0.12 arcsec Gaussian  
  > "We assume a 0.02$''$ uncertainty on the positions of these points in the radial direction and 0.05$''$ uncertainty in the tangential direction." (3 Lens Model)
   - software: Glee, glafic
   - fitting: _not stated_
   - validation: Reduced chi2 <1  
  > "The reduced $\chi^{2}$ of the model fit when comparing the modeled image positions to the constraints is $< 1$" (3 Lens Model)
5. **Predict central image flux and SMBH constraint**: Map conjugate points to source plane, weight by sqrt(mu)/sigma, lens a Gaussian mock source (sigma=0.0168 arcsec), Gaussian non-detection likelihood on CO map  
  > "The mapped positions are weighted by $\sqrt{\mu_{i}}/\sigma_{i}$" (4.2 SMBH Mass Inference)
   - software: Glee
   - assumption: Results same if source twice as large  
  > "although our results are the same even if we assume a source twice as large" (4.2 SMBH Mass Inference)
   - fitting: Importance sampling  
  > "we use importance sampling to attempt to constrain the SMBH mass" (3 Lens Model)
   - validation: _not stated_

## Software

- **CASA** 4.5.0: imaging, uvcontsub  
  > "version 4.5.0" (2.1 ALMA Data)
- **Glee** : lens modeling  
  > "We model the lens system using ALMA constraints and the *HST* images with Glee" (3 Lens Model)
- **glafic** : cross-check lens modeling  
  > "We have also modeled the ALMA constraints with glafic (cite: oguri2010)" (3 Lens Model)
- **Drizzlepac** : HST reduction  
  > "The data are reduced using Drizzlepac (cite: gonzaga+2012)" (2.2 HST Data)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Source redshift | 1.5747 | 0.0002 (95%) | dimensionless | 2 | $z_{\mathrm{S}} = 1.5747\pm 0.0002$ (95% confidence interval) |
| Einstein radius | 0.66 | ±0.01 | arcsec | 4 | $0.66_{-0.01}^{+0.01}$ |
| Mass profile slope | 2.13 | +0.10/-0.09 | dimensionless | 4 | $2.13_{-0.09}^{+0.10}$ |
| Axis ratio b/a | 0.68 | +0.05/-0.04 | dimensionless | 4 | $0.68_{-0.04}^{+0.05}$ |
| External shear | 0.04 | ±0.01 | dimensionless | 4 | $0.04_{-0.01}^{+0.01}$ |
| CO total flux | 9.1 | 0.32 | Jy km/s | 2 | $9.1 \pm 0.32$ |
| Continuum total flux (natural) | 10.0 | 0.23 | mJy | 2 | $10.0 \pm 0.23$ |
| Central image 3 sigma limit | 0.0471 | not stated | Jy km/s | 5 | down to a 3$\sigma$ rms level of 0.0471 Jy km s$^{-1}$ |

## Qualitative findings

- ALMA morphology differs from HST, indicating spatial offset between stars and gas/dust in the source  
  > "This difference suggests a spatial offset between the stellar component and the gas and dust component of the source galaxy" (4.1 Lens Model Results)

## Claim tuples

- H: Source redshift can be improved with ALMA CO | E: Integrate CO flux over both arcs per velocity bin | R: z_S=1.5747±0.0002 | F: More accurate than Z-Spec value | **supported**
- H: Lens mass follows power law with shear | E: Glee fit to HST and ALMA conjugate points | R: theta_E=0.66, gamma'=2.13 | F: Slightly steeper than isothermal | **supported**
- H: Central image can constrain SMBH mass | E: Search integrated CO map and predict flux | R: No detection; predicted flux too low | F: No meaningful SMBH constraint | **refuted**

## Reasoning

- Why this data: _not stated_
- Why this method: Natural weighting for CO to maximize sensitivity to a point-like central image  
  > "we aim to maximize the sensitivity to a central image (which is expected to be a point source)" (2.1 ALMA Data)
- Alternative: Two Sersic profiles plus point source gave comparable light fit  
  > "we also try fitting a sum of two Sérsic profiles and a point source, which provides a comparable fit" (3 Lens Model)
- How they decided it was enough: _not stated_
- Limitation (authors): ~50% of data flagged due to antenna problems  
  > "We note that $\sim$50 % of the data are flagged" (2.1 ALMA Data)
- Limitation (authors): Conjugate points cause degeneracies; position uncertainties overestimated  
  > "The use of conjugate points leads to degeneracies in the lens model" (3 Lens Model)
- Caveat (inferred, ours): Lens model uses only conjugate points, not visibilities or surface brightness
- Caveat (inferred, ours): 50% flagging may affect flux and sensitivity
- Caveat (inferred, ours): HST-ALMA astrometric offset of ~0.12 arcsec limits joint modeling
- Caveat (inferred, ours): Posterior sampling method not described

## Reproducibility

- Data public (paper): Program code given; HST archival  
  > "ADS/JAO.ALMA#2015.1.00415.S" (Acknowledgments)
- Products in archive: _not stated_
- Missing: Conjugate point coordinates
- Missing: Glee configuration and sampler details
- Missing: Imaging image/cell sizes and line-free channels
- Data volume (inferred): ~100-300 GB raw (long-baseline Band 6, 4 SPWs)
- Score (inferred): 3/5, Public data and basic imaging parameters given, but lens modeling details and several imaging settings are missing.
- Rediscovery candidate: no, Lens model recipe incomplete (conjugate points and sampling unspecified), though fluxes and redshift could be redone.

## Links

- Method: (cite: suyuhalkola2010; suyu+2012) (Glee lens modeling software)
- Method: (cite: wong+2015) (SMBH inference from central image non-detection)
- Companion: (cite: dye+2014) (Previous lens model of SDP.9)
- Companion: (cite: negrello+2014) (HST data and stellar mass)
- Related: H-ATLAS
- Related: SDP.81

## Checks

```json
{
 "quotes": 68,
 "quotes_ok": 68,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 77,
  "stated": 54,
  "rate": 0.701
 },
 "evidence_ok": true
}
```
