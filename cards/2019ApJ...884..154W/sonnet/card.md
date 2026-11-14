# Discovery of a Dark, Massive, ALMA-only Galaxy at z ∼ 5-6 in a Tiny 3 mm Survey

`2019ApJ...884..154W` | The Astrophysical Journal 2019 | first author: Williams, Christina C. | arXiv: 1905.11996 | DOI: 10.3847/1538-4357/ab44aa

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies
- Question: What are the nature, redshift and contribution to cosmic star formation of two serendipitous 3 mm continuum sources found in deep ALMA Band 3 data in COSMOS, including one optical/NIR-dark source?  
  > "Here we report the serendipitous discovery of 2 previously unknown sources in deep ALMA 3-mm observations in the COSMOS field, and assess the implications for dust obscured star formation at $z>3$." (Introduction)
- Target **3MM-1**: coordinates 10:02:36.82 +02:08:40.60  
  > "Coordinates | 10:02:36.82 +02:08:40.60" (Table 1); z/distance z = 5.5 +1.2/-1.1 (photometric, SED fit)  
  > "Coordinates | 10:02:36.82 +02:08:40.60" (Table 1); distance from BAGPIPES SED fitting  
  > "Coordinates | 10:02:36.82 +02:08:40.60" (Table 1)
- Target **3MM-2**: coordinates 10:02:36.30 +2:08:49.55  
  > "Coordinates | 10:02:36.82 +02:08:40.60 | 10:02:36.30 +2:08:49.55" (Table 1); z/distance z_CO = 3.329 (probable CO(4-3))  
  > "we determine the line is likely CO($4-3$) at $z=3.329$, in agreement with the best-fit photometric redshift" (Results, 3MM-2); distance from single CO line at 106.5 GHz plus SED photometric redshift  
  > "Considering the CO emission line detection (consistent with redshifts 2.25, 3.33, and 4.41), we determine the line is likely CO($4-3$) at $z=3.329$, in agreement with the best-fit photometric redshift." (Results, 3MM-2)

## Data provenance

- ALMA projects: 2018.1.01739.S, 2015.1.00853.S, 2015.1.00861.S
- bands: Band 3  
  > "ALMA Band 3 observations were carried out in two observing blocks on 2018 December 23 and 24" (2.1 ALMA millimeter interferometry)
- frequencies and spectral setup: One 1.875 GHz SPW at 94.92 GHz (7.8 MHz channels); three 1.875 GHz continuum SPWs at 96.8, 106.9, 108.8 GHz (15.6 MHz channels)  
  > "Three additional 1.875 GHz bandwidth spectral windows were placed at sky frequencies 96.8, 106.9, and 108.8 GHz for continuum observations, each with 15.6 MHz channelization." (2.1 ALMA millimeter interferometry)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: maximum baselines of 500 m, 43 antennas  
  > "A total of 43 antennas were active reaching maximum baselines of 500m" (2.1 ALMA millimeter interferometry)
- angular resolution: ~2 arcsec (2.2" x 1.7", natural weighting)  
  > "synthesized beam major axis = 2.2”, minor axis = 1.7” under natural weighting" (2.1 ALMA millimeter interferometry)
- max recoverable scale: _not stated_
- sensitivity: 5.7 uJy/beam continuum at 101.9 GHz; 55-65 uJy/beam per 100 km/s channel  
  > "The imaged data reach a continuum sensitivity of 5.7$\mu$Jy/beam at 101.9 GHz" (2.1 ALMA millimeter interferometry)
- time on source: 97 min  
  > "The total time on-source was 97 min." (2.1 ALMA millimeter interferometry)
- observing dates: 2018 December 23 and 24  
  > "ALMA Band 3 observations were carried out in two observing blocks on 2018 December 23 and 24" (2.1 ALMA millimeter interferometry)
- pi or archival as stated: Own program (PI Williams) plus 2015.1.00853.S (PI Bezanson); 2015.1.00861.S downloaded  
  > "We downloaded and imaged these data following the same procedure as for our own data." (2.2 ALMA source detection)
- Line: CO 4-3 (probable, serendipitous line in 3MM-2) (not stated)
- Other facility **Subaru Suprime-Cam/HSC, UltraVISTA, Spitzer/IRAC and MIPS**: Optical, NIR and mid-IR photometry for deblended SED  
  > "Ultradeep NIR coverage is provided by the 4th data release of the UltraVISTA survey" (2.3.1 Optical, near-infrared, and Spitzer/IRAC)
- Other facility **Herschel PACS/SPIRE, SCUBA-2 (S2COSMOS)**: FIR/submm photometry with ALMA priors; 850um S=3.5+-1.1 mJy for 3MM-1  
  > "The flux measured with SCUBA is $S_{850}$=3.5$\pm$1.1 mJy ($SNR=3.1$)." (3.1 3MM-1)
- Other facility **VLA 3 GHz and 1.4 GHz**: Radio photometry at ALMA positions  
  > "Photometry on the 3GHz map using the ALMA position as prior reveals 9.98$\pm$2.39 $\mu$Jy/beam (4$\sigma$) point source for $3MM$-1" (2.3.3 Radio VLA 3Ghz and 1.4 Ghz)
- External data: 3 mm number counts used for expected source density and chance-alignment simulation  
  > "we use their best-fit powerlaw to the cumulative number counts" (4.2 Number counts) [from Zavala2018_3mm]
- External data: S2COSMOS 850um map (private communication)  
  > "We therefore use the state-of-the-art S2COSMOS observations (Simpson priv. comm.)" (2.3.2 Far-infrared to submillimeter) [from Simpson et al. in prep]
- External data: Empirical AGN-dominated mid-IR template  
  > "we investigate any possible contamination using the empirical AGN-dominated template published by (cite: Kirkpatrick2015)." (3.1 3MM-1) [from (cite: Kirkpatrick2015)]

## Processing

### Calibration

- pipeline or manual: Standard ALMA Cycle 6 pipeline  
  > "The data were reduced using the standard ALMA Cycle 6 pipeline, and no problems with the pipeline calibration were found." (2.1 ALMA millimeter interferometry)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "We imaged the data using natural weighting, creating a 101 GHz continuum image of the field from all four spectral windows." (2.1 ALMA millimeter interferometry)
- uv taper: _not stated_
- cell size: 0.2" pixels  
  > "We imaged the data using 0.2” pixels and created a 500$\times$500 pixel image" (2.1 ALMA millimeter interferometry)
- image size: 500x500 pixels (100" on a side)  
  > "We imaged the data using 0.2” pixels and created a 500$\times$500 pixel image, yielding images 100” on a side." (2.1 ALMA millimeter interferometry)
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: detection in uncorrected maps; fluxes corrected for primary beam response  
  > "The 3 mm flux densities of these sources, corrected for the primary beam response, are 155 $\pm$ 20 $\mu$Jy and 75 $\pm$ 10" (2.2 ALMA source detection)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 2.2" x 1.7"  
  > "synthesized beam major axis = 2.2”, minor axis = 1.7” under natural weighting" (2.1 ALMA millimeter interferometry)
- final rms: 5.7 uJy/beam at 101.9 GHz  
  > "The imaged data reach a continuum sensitivity of 5.7$\mu$Jy/beam at 101.9 GHz" (2.1 ALMA millimeter interferometry)

### Inherited from earlier work

- Details of 2015.1.00861.S data  
  > "These data are described in more detail in (cite: Silverman2018), and have non-overlapping frequency coverage with our own data." (2.2 ALMA source detection) [from (cite: Silverman2018)]
- Results on the other four targets in the program  
  > "results on these targets are presented elsewhere ((cite: Bezanson2019))" (2.1 ALMA millimeter interferometry) [from (cite: Bezanson2019)]
- Dynamical mass procedure  
  > "Following the procedure used by (cite: Wang2013), we compute $V_{circ} = 0.75  FWHM(CO)/sin(i)$" (3.2 3MM-2) [from (cite: Wang2013)]

### Not stated but needed to reproduce (our reading)

- tclean/imaging software and CASA version
- Details of 3MM-2 and 3MM-1 flux extraction method (e.g. point-source fit vs peak)
- Line-free channels and continuum subtraction approach for line search
- Full BAGPIPES priors for SFH (tau, age), metallicity and redshift prior details
- Detailed MOPHONGO settings and the photometric tables' flux conversions
- Gas mass dust temperature, emissivity and gas-to-dust assumptions for Scoville calibration
- Simpson S2COSMOS map not public

## Analysis recipe

1. **image and blind source detection**: Natural-weighted continuum map from four SPWs, blind search in uncorrected map; sidebands imaged separately for spectral index; line search with 100-400 km/s channels  
  > "Two blind 3 mm continuum sources were apparent in this map, located 24.6” and 38.2” from the phase center" (2.2 ALMA source detection)
   - parameter: peak SNR ~8 each; primary beam response 0.57 and 0.29  
  > "Each source is detected at a peak signal-to-noise ratio of $\sim8$" (2.2 ALMA source detection)
   - fitting: Gaussian fit to CO line (width 630+-70 km/s)  
  > "A Gaussian fit indicates in a width of $630\pm 70$ km/s." (2.2 ALMA source detection)
   - validation: Probability of noise fluctuation <1e-9; spectral indices consistent with thermal dust  
  > "We find spectral indices for both continuum sources in excellent agreement with the expectation for thermal dust emission." (2.2 ALMA source detection)
2. **deblended multi-wavelength photometry with ALMA priors**: MOPHONGO deblending in optical/NIR/IRAC; Gaussian fits at fixed prior locations in Herschel and SCUBA-2; VLA photometry at ALMA position  
  > "We measured flux densities for $3MM$-1 in the optical and UltraVISTA bands in $1.2\ensuremath{''}$-diameter apertures after subtracting the neighbors using MOPHONGO" (2.3.1 Optical, near-infrared, and Spitzer/IRAC)
   - software: MOPHONGO
   - parameter: HSC z prior for 3MM-1, F814W prior for 3MM-2; 1.8" apertures for IRAC  
  > "we adopted the HSC $z$-band image as prior for $3MM$-1" (2.3.1 Optical, near-infrared, and Spitzer/IRAC)
   - fitting: _not stated_
   - validation: Herschel SPIRE fluxes compared with published, 30% scatter added in quadrature  
  > "Comparison of the measured SPIRE fluxes with those published showed a scatter of 30%" (2.3.2 Far-infrared to submillimeter)
3. **SED fitting for redshift, mass, SFR**: BAGPIPES with BC03, nebular emission, Charlot & Fall dust with free exponent, Draine & Li dust emission, energy balance, delayed-exponential SFH, uniform priors; Calzetti comparison  
  > "We select the flexible dust absorption model of (cite: Charlot2000), with the exponent of the effective absorption $\propto\lambda^{-n}$ as a free parameter" (2.4 Spectral Energy Distribution Modeling)
   - software: BAGPIPES, CLOUDY, PROSPECTOR
   - parameter: metallicities 0.2-2.5 Zsun; fitting in linear fluxes with no upper limits enforced  
  > "All fitting is performed in linear fluxes and uncertainties and no upper limits are enforced on measurements with low SNR." (2.4 Spectral Energy Distribution Modeling)
   - assumption: Kroupa IMF; LCDM H0=70, OmegaM=0.3  
  > "We assume a $\Lambda$CDM cosmology with H$_0$=70 km s$^{-1}$ Mpc$^{-1}$, $\Omega_M$ = 0.3, $\Omega_\Lambda$ = 0.7" (Introduction)
   - fitting: Bayesian posteriors with uniform diffuse priors (sampler not named)  
  > "For each parameter, uniform, diffuse priors are assumed" (2.4 Spectral Energy Distribution Modeling)
   - validation: Tested Calzetti law, mid-IR to submm only fit, da Cunha and Arp 220 SEDs, AGN template subtraction, PROSPECTOR non-parametric SFH  
  > "We also experimented with fitting only the mid-infrared to sub-millimeter SED, finding the same results." (3.1 3MM-1)
4. **gas and dynamical masses**: Scoville 2016 submm-flux-to-gas-mass for 3MM-1; CO(4-3) with Bothwell excitation and Wang 2013 dynamical mass for 3MM-2  
  > "we find that $3MM$-1 likely has M$_{\rm{gas}}\sim0.5-1.5 \times 10^{11}$ M$_{\odot}$" (3.1 3MM-1)
   - parameter: Re = 3 (+1.8/-0.9) kpc from van der Wel 2014  
  > "Adopting the mean size $R_e=3^{+1.8}_{-0.9}$ kpc expected for massive 10$^{11}$M$_\odot$ star forming galaxies at $z=3$" (3.2 3MM-2)
   - assumption: inclination 45 deg for disk geometry  
  > "Assuming a disk geometry with an inclination angle of $i=45^{\circ}$ would imply M$_{dyn}\sim3\times10^{11}$M$_\odot$." (3.2 3MM-2)
   - fitting: _not stated_
   - validation: _not stated_
5. **source density and CSFRD contribution**: Effective survey area 8 arcmin2; selection volume z=4.1 to 5.7 from halo mass function; Poisson uncertainty  
  > "Using this selection volume we determine a space density of $2.9^{+6.5}_{-2.4}\times10^{-5}$ Mpc$^{-3}$." (4.5 Contribution to CSFRD)
   - software: HMF
   - parameter: Behroozi2013 halo mass function, 30% baryon conversion, Mhalo ~1e12  
  > "assuming the halo mass function of (cite: Behroozi2013) and a high $30\%$ baryon conversion into stars" (4.5 Contribution to CSFRD)
   - fitting: _not stated_
   - validation: Cosmic variance ~30% not included; no completeness correction  
  > "Cosmic variance is only on the order of $\sim$30% based on the calculator by (cite: Trenti2008)" (4.5 Contribution to CSFRD)

## Software

- **BAGPIPES** : Bayesian SED fitting  
  > "We use the Bayesian Analysis of Galaxies for Physical Inference and Parameter EStimation (BAGPIPES) code (cite: Carnall2018)" (2.4 Spectral Energy Distribution Modeling)
- **MOPHONGO** : Deblended optical/NIR/IRAC photometry  
  > "after subtracting the neighbors using MOPHONGO" (2.3.1 Optical, near-infrared, and Spitzer/IRAC)
- **CLOUDY** : Nebular emission in SED models  
  > "using the CLOUDY photoionization code (cite: Ferland2017)" (2.4 Spectral Energy Distribution Modeling)
- **PROSPECTOR** : Non-parametric SFH cross-check  
  > "We explore the dependence on SFH by also fitting the SED with PROSPECTOR (cite: Leja2017)" (3.2 3MM-2)
- **HMF** : Halo mass function calculator for selection volume  
  > "Using the halo mass function calculator HMF published by (cite: Murray2013)" (4.5 Contribution to CSFRD)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| 3MM-1 3mm flux density (PB corrected) | 155 | 20 | uJy | 1 | are 155 $\pm$ 20 $\mu$Jy and 75 $\pm$ 10 |
| 3MM-2 3mm flux density | 75 | 10 | uJy | 1 | are 155 $\pm$ 20 $\mu$Jy and 75 $\pm$ 10 |
| 3MM-2 CO line integrated flux | 0.66 | 0.1 | Jy km/s | 1 | with an integrated flux density of 0.66 $\pm$ 0.1 Jy km s$^{-1}$ |
| Equivalent survey area | 8.0 | not stated | arcmin^2 | 1 | we derive a total survey area of 8.0 arcmin$^{2}$ to 155$\mu$Jy ($5\sigma$ limit) |
| 3MM-1 photometric redshift | 5.5 | +1.2/-1.1 | dimensionless | 3 | very high redshift $z\sim5.5^{+1.2}_{-1.1}$ |
| 3MM-1 log stellar mass | 10.8 | 0.4 | log Msun | 3 | massive $10^{10.8\pm0.4}$M$_\odot$ |
| 3MM-1 SFR | 309 | +241/-149 | Msun/yr | 3 | $SFR=309^{+241}_{-149}$M$_\odot$/yr |
| 3MM-2 photometric redshift | 3.3 | 0.2 | dimensionless | 3 | finding a well-constrained photometric redshift of $z=3.3\pm0.2$ |
| 3MM-2 stellar mass ratio CF00 vs Calzetti | 8 | +7.1/-3.9 | dimensionless | 3 | a factor $8^{+7.1}_{-3.9}$ lower stellar mass ($10^{10.2}$ M$_\odot$) |
| 3MM-1 source density | 2.9 | +6.5/-2.4 | 1e-5 Mpc^-3 | 5 | we determine a space density of $2.9^{+6.5}_{-2.4}\times10^{-5}$ Mpc$^{-3}$ |
| CSFRD contribution of 3MM-1 | 0.9 | +2.0/-0.7 | 1e-2 Msun/yr/Mpc^3 | 5 | $0.9^{+2.0}_{-0.7}\times10^{-2}$ M$_{\odot}$ yr$^{-1}$ Mpc$^{-3}$ |
| 3MM-2 dynamical mass Mdyn sin^2 i | 1.5 | +1.0/-0.5 | 1e11 Msun | 4 | M$_{dyn}sin^2(i) = 1.5^{+1.0}_{-0.5}\times10^{11}$M$_\odot$ |

## Qualitative findings

- 3MM-1 is an ALMA-only galaxy invisible in all prior optical-to-radio catalogs, with faint ~3 sigma IRAC, SCUBA-2 and VLA detections.  
  > "The other source is missing from all previous optical/near-infrared/sub-mm/radio catalogs (“ALMA-only”)" (abstract)
- 3MM-1 shows a 3 GHz radio excess possibly indicating an AGN, but AGN contribution does not significantly affect SED results.  
  > "We conclude that any AGN contribution does not significantly impact our SED-fitting results." (3.1 3MM-1)

## Claim tuples

- H: Is 3MM-1 a real, high-redshift massive dusty galaxy absent from existing catalogs? | E: Deblended ALMA-prior photometry and BAGPIPES SED fit | R: z=5.5+1.2/-1.1, logM*=10.8, SFR~309, SNR~3 in IRAC, SCUBA-2 and VLA | F: 3MM-1 is a real massive dusty z~5-6 galaxy | **supported**
- H: Does the attenuation law affect derived stellar mass and SFR? | E: Fit 3MM-2 with flexible CF00 vs Calzetti | R: Calzetti gives factor ~8 lower mass and ~2.2 lower SFR; flat n=0.4 | F: Grey attenuation law favored; caution needed relating progenitors and descendants | **supported**
- H: Do such sources contribute substantially to the CSFRD? | E: Space density from single source and 8 arcmin2 area with halo-mass-function volume | R: rho_SFR 0.9e-2 Msun/yr/Mpc^3 with large Poisson uncertainty | F: Possibly comparable to all UV-selected galaxies, but uncertain | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Deblended photometry with ALMA position priors needed because of neighbors and faint sources  
  > "We therefore proceeded to perform deblended photometry on both ALMA positions using the following data sets." (2.3 Multi-wavelength photometry)
- Alternative: Two sources at same redshift considered and disfavored  
  > "Overall, there is no conclusive evidence that the two sources are at the same redshift." (3.3 Redshifts)
- How they decided it was enough: _not stated_
- Limitation (authors): Single object; Poisson uncertainty large; stellar mass uncertainties likely underestimated due to parametric SFH  
  > "It is likely that the uncertainties on the stellar mass and other stellar population parameters are underestimated" (4.1 Implications from full optical-to-mm spectrum SED fitting)
- Caveat (inferred, ours): Redshift of 3MM-1 is photometric only with no spectroscopic confirmation
- Caveat (inferred, ours): CSFRD from one source and assumed selection volume
- Caveat (inferred, ours): Radio excess and possible AGN not independently checked
- Caveat (inferred, ours): 3MM-1 SCUBA-2 and VLA detections are only ~3-4 sigma

## Reproducibility

- Data public (paper): Programs cited with ALMA project codes; 2015.1.00861.S 'downloaded'  
  > "We downloaded and imaged these data following the same procedure as for our own data." (2.2 ALMA source detection)
- Products in archive: _not stated_
- Missing: Exact imaging commands and CASA version
- Missing: S2COSMOS map not public
- Missing: Full SED fit configuration beyond Table priors
- Missing: Gas mass conversion details
- Data volume (inferred): Tens of GB of ALMA data for several projects plus public COSMOS ancillary imaging
- Score (inferred): 3/5, ALMA data public and recipe mostly described, but imaging tooling, SED priors detail and private S2COSMOS data are limiting.
- Rediscovery candidate: no, Key results rely on a multi-wavelength deblended SED analysis and private SCUBA-2 data, so not straightforward to redo from ALMA data alone.

## Links

- Method: (cite: Carnall2018) (BAGPIPES SED fitting code)
- Method: (cite: Labbe2013; Labbe2015) (MOPHONGO deblending)
- Companion: (cite: Bezanson2019) (Results on the other targets of the same ALMA program)
- Companion: (cite: Silverman2018) (Describes 2015.1.00861.S data)
- Related: ASPECS
- Related: Zavala 2018 archival 3 mm survey
- Related: ASAGAO
- Related: S2COSMOS
- Related: COSMOS

## Checks

```json
{
 "quotes": 80,
 "quotes_ok": 80,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 3,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 12,
 "numeric_problems": 0,
 "fill": {
  "facts": 86,
  "stated": 60,
  "rate": 0.698
 },
 "evidence_ok": true
}
```
