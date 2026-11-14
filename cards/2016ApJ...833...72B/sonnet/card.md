# ALMA Spectroscopic Survey in the Hubble Ultra Deep Field: The Infrared Excess of UV-Selected z = 2-10 Galaxies as a Function of UV-Continuum Slope and Stellar Mass

`2016ApJ...833...72B` | The Astrophysical Journal 2016 | first author: Bouwens, Rychard J. | arXiv: 1606.05280 | DOI: 10.3847/1538-4357/833/1/72

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies
- Question: How does the infrared excess (IRX = L_IR/L_UV) of UV-selected z=2-10 galaxies depend on UV-continuum slope and stellar mass, measured with deep ASPECS 1.2 mm continuum data?  
  > "The purpose of this paper (paper VI in the ASPECS series) is to focus in particular on the infrared excess ($L_{IR}/L_{UV}$) of $z=2$-10 galaxies over our 1 arcmin$^2$ field" (Introduction)
- Target **Hubble Ultra Deep Field ASPECS 1 arcmin2 region (330 UV-selected z=2-10 galaxies)**: coordinates _not stated_; z/distance z=2-10  
  > "Total                             | 330     |" (Table 2); distance from photometric redshifts and dropout selection; some 3D-HST spectroscopic redshifts  
  > "Total                             | 330     |" (Table 2)

## Data provenance

- ALMA projects: 2013.1.00718.S
- bands: Band 6 (212-272 GHz) full frequency scan  
  > "Those observations were obtained through a full frequency scan in band 6 (212 $-$ 272 GHz) with ALMA in its most compact configuration." (2.1 Band-6 Data Set and Flux Measurements)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: most compact configuration, 7 pointings  
  > "The observations are distributed over 7 pointings and cover an approximate area of $\sim$1 arcmin$^2$ to near uniform depth." (2.1 Band-6 Data Set and Flux Measurements)
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: 12.7 uJy (1 sigma) per primary beam  
  > "The peak sensitivity we measure in these continuum observations is 12.7$\mu$Jy ($1\sigma$) per primary beam." (2.1 Band-6 Data Set and Flux Measurements)
- time on source: 20-hour program  
  > "our recent 20-hour, 1.2-mm ALMA program (2013.1.00718.S" (Introduction)
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Other facility **HST (XDF, ACS, WFC3)**: photometry for LBG selection, UV slopes, stellar masses  
  > "we make use of the XDF reductions (Illingworth et al. 2013), which incorporated all ACS+WFC3/IR data available over the HUDF in 2013." (2.2 LBG samples)
- Other facility **Spitzer/IRAC**: photometry for stellar masses  
  > "4 *Spitzer*/IRAC bands (3.6$\mu$m, 4.5$\mu$m, 5.8$\mu$m, and 8.0$\mu$m)" (2.3 Estimates of the Stellar Mass)
- Other facility **Spitzer/MIPS 24um**: independent IR luminosity check  
  > "we derive independent estimates of IR luminosities for $z=1.5$-3.0 galaxies in our selection using deep 24$\mu$m MIPS observations over GOODS South." (B. Comparison Between MIPS-Inferred and ALMA-Inferred Infrared Luminosities)
- External data: z=4-8 LBG samples  
  > "Our $z=4$-8 samples were drawn from the Bouwens et al. (2015) samples" (2.2 LBG samples) [from Bouwens et al. (2015)]
- External data: Capak and Willott ALMA fluxes, UV luminosities and masses of z=5-7 galaxies  
  > "Combining our own results with those from Capak et al. (2015) and Willott et al. (2015)" (3.5 Synthesis) [from Capak et al. (2015); Willott et al. (2015)]
- External data: Spectroscopic redshifts  
  > "Spectroscopic Redshift from 3D-HST (Momcheva et al. 2015)." (Table 3) [from Momcheva et al. 2015]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA CLEAN, mosaic mode  
  > "inverting the visibilities using the CASA task CLEAN using natural weighting and mosaic mode, for producing the continuum image." (2.1 Band-6 Data Set and Flux Measurements)
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: flux at source position divided by primary beam  
  > "Flux measurements themselves were made using the nominal flux at the position of the source in the continuum map divided by the primary beam." (2.1 Band-6 Data Set and Flux Measurements)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- ASPECS data set, continuum imaging and basic results  
  > "As described in paper II (Aravena et al. 2016a), we collapsed our spectral data cube along the frequency axis in the $uv$-plane" (2.1 Band-6 Data Set and Flux Measurements) [from Aravena et al. 2016a (Paper II); Walter et al. 2016 (Paper I)]

### Not stated but needed to reproduce (our reading)

- CASA version and calibration details
- CLEAN threshold, cell and image size
- Exact line-free channel selection for the continuum
- Catalog of 330 sources including the new photometric-redshift catalog
- FAST grid details beyond those given
- Bootstrap procedure details

## Analysis recipe

1. **Build z=2-10 galaxy sample**: Lyman-break colour criteria plus EAZY photometric redshifts on HST photometry; z=4-8 from Bouwens et al. 2015  
  > "we also applied the EAZY photometric redshift code to the *HST* WFC3/UVIS, ACS, and WFC3/IR photometric catalogs" (2.2 LBG samples)
   - software: SExtractor, EAZY
   - fitting: _not stated_
   - validation: _not stated_
2. **Derive stellar masses and UV slopes**: SED fitting of HST, Ks and IRAC photometry; beta from power-law fit to UV fluxes  
  > "we make use of the publicly-available code FAST (Kriek et al. 2009) to perform this fitting." (2.3 Estimates of the Stellar Mass)
   - software: FAST, MAGPHYS
   - parameter: 0.2 Zsun, tau=100 Gyr, A_V 0-2 mag  
  > "keeping $\tau$ parameter for a $e^{-t/\tau}$ star formation history equal to 100 Gyr" (2.3 Estimates of the Stellar Mass)
   - assumption: Chabrier IMF  
  > "We assume a Chabrier (2003) IMF, a metallicity of 0.2 $Z_{\odot}$" (2.3 Estimates of the Stellar Mass)
   - fitting: _not stated_
   - validation: MAGPHYS masses 0.02 dex lower in median for z<3.8  
  > "with the median and mean stellar mass derived by MAGPHYS being 0.02 dex and 0.04 dex lower, respectively." (2.3 Estimates of the Stellar Mass)
3. **Predict 1.2 mm fluxes from IRX-beta**: M99 and SMC IRX-beta, modified blackbody, CMB correction  
  > "The equivalent flux at an observed wavelength of 1.2$\,$mm is then computed adopting a modified blackbody form with a dust temperature of 35 K" (3.1.1)
   - parameter: Td=35 K, beta_d=1.6  
  > "a dust temperature of 35 K and a dust emissivity power-law spectral index of $\beta_d =
1.6$" (3.1.1)
   - assumption: IR luminosity 8-1000 um  
  > "convert that to an expected IR luminosity for the source (considered to extend from 8$\mu$m to 1000$\mu$m)" (3.1.1)
   - fitting: _not stated_
   - validation: perturbing beta by uncertainties; MIPS 24um comparison  
  > "we perturbed the measured $\beta$’s for individual sources by the estimated uncertainty" (3.1.1)
4. **Measure individual 1.2 mm fluxes**: continuum map value at HST position, after 0.3 arcsec offset correction; compare with negative image  
  > "derived taking the value in our 1.2$\,$mm-continuum image at the nominal optical position of each source in our LBG samples" (3.2)
   - fitting: _not stated_
   - validation: negative-image detections and MIPS 24um  
  > "This can been seen by looking for similar $>2\sigma$ detections in the negative continuum image" (3.2)
5. **Stack continuum by mass, beta and mag**: weighted stack, weights (L_UV/sigma)^2, 3.3x3.3 arcsec aperture, bootstrap uncertainties  
  > "We derive a flux from the stack based on a convolution of the image stack (3.3$''$$\times$3.3$''$ aperture) with the primary beam." (3.3)
   - assumption: no spatial extension  
  > "No spatial extension is assumed in the stacked flux." (3.3)
   - fitting: dA_UV/dbeta constrained by comparing stacks to IRX=10^{0.4(dA/dbeta)(beta+2.23)}-1  
  > "where $IRX=10^{0.4(dA_{UV}/d\beta)(\beta+2.23)}-1$" (3.3.2)
   - validation: perturb beta 10 times  
  > "We repeated this process 10$\times$" (3.3.2)
6. **Derive dust-corrected SFR densities**: apply dust prescription to UV LFs of Bouwens et al. 2015, add IR-bright contribution  
  > "As in previous work, the $UV$ luminosity densities are converted into SFR densities using canonical Madau et al. (1998) and Kennicutt (1998) relationships" (5.2)
   - assumption: Salpeter IMF, 100 Myr constant SFR  
  > "This relationship assumes a Salpeter (1955) IMF and a constant SFR for 100 million years." (5.2)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : CLEAN continuum imaging  
  > "inverting the visibilities using the CASA task CLEAN" (2.1 Band-6 Data Set and Flux Measurements)
- **FAST** : stellar mass SED fitting  
  > "publicly-available code FAST (Kriek et al. 2009)" (2.3 Estimates of the Stellar Mass)
- **MAGPHYS** : cross-check stellar masses  
  > "using the MAGPHYS software (da Cunha et al. 2008)" (2.3 Estimates of the Stellar Mass)
- **SExtractor** : source catalogs and photometry (modified)  
  > "our own modified version of the SExtractor (Bertin & Arnouts 1996) software" (2.2 LBG samples)
- **EAZY** : photometric redshifts  
  > "we also applied the EAZY photometric redshift code" (2.2 LBG samples)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| 1.2 mm continuum rms | 12.7 | not stated | uJy/beam | 0 | deep $1.2\,$mm-continuum observations (12.7$\mu$Jy/beam RMS) |
| Expected 2sigma detections (M99, Td=35K) | 35 | not stated | sources | 3 | 35 and 26 of these galaxies should be detected at $\geq 2\sigma$ and $\geq3\sigma$ significance |
| IRX, M<10^9.75, z=2-3 | 0.11 | +0.32/-0.42 (bootstrap), ±0.34 (formal) | dimensionless | 5 | 0.11$_{-0.42}^{+0.32}$$\pm$0.34 |
| IRX, M<10^9.75, z=4-10 | 0.14 | +0.15/-0.14 (bootstrap), ±0.18 (formal) | dimensionless | 5 | 0.14$_{-0.14}^{+0.15}$$\pm$0.18 |
| IRX, M>10^9.75, z=2-3 | 3.80 | +3.61/-2.40 (bootstrap), ±0.19 (formal) | dimensionless | 5 | 3.80$_{-2.40}^{+3.61}$$\pm$0.19 |
| dA_UV/dbeta, M>10^9.75, z=2-3 | 1.26 | +0.27/-0.36 | dimensionless | 5 | The result we obtain for $dA_{UV}/d\beta$ is 1.26$_{-0.36}^{+0.27}$ |
| Detection fraction for M>10^9.75 (172 sources with rms<17 uJy) | 63 | +14/-17 | percent | 4 | 63$_{-17}^{+14}$% of the galaxies with stellar mass estimates $>10^{9.75}$ $M_{\odot}$ are detected |
| Escape fraction needed for reionization | 8 | ±2 | percent | 6 | galaxies can reionize the universe if the escape fraction $f_{esc}$ is equal to $8\pm2$% |

## Qualitative findings

- Stellar mass is the best predictor of IR luminosity; low-mass galaxies show IRX below the SMC relation.  
  > "These results point to stellar mass as being perhaps the best predictor of IR luminosity in $z\gtrsim2$ galaxy samples." (6 Summary)

## Claim tuples

- H: z>=2 galaxies follow the z~0 M99 IRX-beta relation | E: Compare predicted detections at 1.2 mm with ASPECS detections | R: 35 expected vs 6 tentative detections | F: M99 over-predicts dust emission at z>=2 | **supported**
- H: IRX depends on stellar mass | E: Stack by mass bin | R: only >10^9.75 Msun at z=2-3 detected | F: low-mass galaxies have low IRX, below SMC | **supported**
- H: IRX-mass relation evolves with redshift | E: Combine ASPECS with Capak and Willott under fixed vs evolving Td | R: ~0.5 dex lower IRX at fixed Td; none if Td evolves | F: evolution depends on dust temperature | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Results depend strongly on assumed dust temperature and SED  
  > "our results change by $\sim$0.3-0.5 dex if the dust temperatures we have assumed are too low or too high." (B. Comparison Between MIPS-Inferred and ALMA-Inferred Infrared Luminosities)
- Caveat (inferred, ours): Td=35 K fixed, no direct constraint
- Caveat (inferred, ours): Stacks dominated by few sources; bootstrap errors large
- Caveat (inferred, ours): Photometric redshifts and noisy beta for faint sources
- Caveat (inferred, ours): Single-band ALMA flux

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Source catalog with photometry for all 330 galaxies
- Missing: CASA version and imaging parameters
- Missing: Bouwens et al. 2016 z=9-10 sample (in prep)
- Data volume (inferred): ~tens of GB (ASPECS Band 6 mosaic visibilities)
- Score (inferred): 3/5, Data are archival and stacking is described, but sample catalogs and imaging parameters are incomplete.
- Rediscovery candidate: no, Requires the HST-derived catalogs and masses, which are not fully provided.

## Links

- Method: Aravena et al. 2016a (ASPECS Paper II) (continuum imaging and source detection)
- Companion: Walter et al. 2016 (ASPECS Paper I) (survey description)
- Companion: Decarli et al. 2016a (ASPECS Paper IV) (detected sources' SED and gas)
- Related: ASPECS
- Related: HUDF/XDF

## Checks

```json
{
 "quotes": 53,
 "quotes_ok": 53,
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
  "facts": 81,
  "stated": 40,
  "rate": 0.494
 },
 "evidence_ok": true
}
```
