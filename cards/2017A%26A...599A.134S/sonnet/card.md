# The ALMA Redshift 4 Survey (AR4S). I. The massive end of the z = 4 main sequence of galaxies

`2017A&A...599A.134S` | Astronomy and Astrophysics 2017 | first author: Schreiber, C. | arXiv: 1606.06252 | DOI: 10.1051/0004-6361/201629155

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies
- Question: Where do massive z~4 galaxies lie on the SFR-M* plane, and what are the normalization and scatter of the main sequence at z=4?  
  > "to provide the first robust constraints on the normalization and scatter of the MS at $z=4$" (1 Introduction)
- Target **96 massive z~4 galaxies in CANDELS GOODS-south, UDS and COSMOS**: coordinates _not stated_; z/distance 3.5<z_phot<4.7, <z>=3.99  
  > "our sample is selected purely on stellar mass ($M_\ast> 5\times10^{10}\,{\rm M}_\odot$) and photometric redshift ($3.5 < z < 4.7$) to ensure the highest completeness, resulting in $110$ galaxies" (2.1 Observed sample); distance from photometric redshifts from Schreiber et al. 2015  
  > "our sample is selected purely on stellar mass ($M_\ast> 5\times10^{10}\,{\rm M}_\odot$) and photometric redshift ($3.5 < z < 4.7$) to ensure the highest completeness, resulting in $110$ galaxies" (2.1 Observed sample)

## Data provenance

- ALMA projects: 2013.1.01292.S
- bands: Band 7, 888.1 um (337.8 GHz)  
  > "($888.1\,\mu{\rm m}$, $337.8\,{\rm GHz}$)" (4.1 Data)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.3-0.7 arcsec (minor axis FWHM)  
  > "ranging from $0.3$ to $0.7\,\ensuremath{''}$ (FWHM of the minor axis of the beam)" (4.1 Data)
- max recoverable scale: _not stated_
- sensitivity: RMS 0.15-0.22 mJy in 0.7 arcsec tapered images  
  > "find an RMS of $0.15$ to $0.22\,{\rm mJy}$" (4.1 Data)
- time on source: 1.3 min per galaxy, 6 hours total  
  > "integrating $1.3$ minutes on each galaxy for a total observing time of $6$ hours" (4.1 Data)
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Other facility **HST CANDELS**: H-band catalogs and photometry for sample selection  
  > "We drew our sample from the CANDELS *HST*$H$-band catalogs" (2.1 Observed sample)
- Other facility **Herschel and Spitzer**: stacked FIR/MIR SED to measure dust temperature  
  > "we can stack them together on the *Spitzer* and *Herschel* images to recover their average SED" (5.1 Dust temperature and star-formation rates)
- External data: Photometric redshifts and stellar masses for parent sample  
  > "Photometric redshifts and stellar masses for all galaxies in this parent sample were derived in (cite: schreiber2015)." (2.1 Observed sample) [from (cite: schreiber2015)]
- External data: Dust SED library  
  > "we use the dust SEDs introduced in (cite: schreiber2016-b)" (5.1 Dust temperature and star-formation rates) [from (cite: schreiber2016-b)]
- Simulation/model as data: Mock catalog of 100000 galaxies for forward modelling the sSFR distribution  
  > "we generated a mock catalog of $100\,000$ galaxies" (5.3 Modeling the sSFR distribution)

## Processing

### Calibration

- pipeline or manual: CASA pipeline  
  > "We reduced the data into calibrated visibilities using the CASA pipeline (version 4.3.1)" (4.1 Data)
- casa version: 4.3.1  
  > "CASA pipeline (version 4.3.1)" (4.1 Data)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: longest baselines tapered to 0.7 arcsec  
  > "we tapered the longest baselines to reach an homogeneous angular resolution of $0.7\,\ensuremath{''}$" (4.1 Data)
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: applied a posteriori to fluxes and uncertainties  
  > "the fluxes and uncertainties are corrected for primary beam attenuation a posteriori" (4.2 Flux measurements)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Stacking, flux boosting correction and photometry/redshift/mass analysis  
  > "As in (cite: schreiber2015), we median stack the images" (5.1 Dust temperature and star-formation rates) [from (cite: schreiber2015)]
- Full reduction and flux catalog deferred  
  > "More details on the reduction and flux measurements will be provided together with the complete catalog in a forthcoming paper (Leiton et al. in prep.)." (4.2 Flux measurements) [from Leiton et al. in prep.]

### Not stated but needed to reproduce (our reading)

- Imaging parameters (weighting, robust, cell, deconvolver, masks)
- Calibrators and flux scale uncertainty
- Per-field array configurations and dates
- Median sizes used for fixed-size fits
- Individual flux catalog (deferred to Leiton et al.)
- Grid ranges for sigma_MS and sSFR_MS

## Analysis recipe

1. **Measure 890um fluxes in uv plane**: Elliptical Gaussian fit in uv plane; fallback with position frozen to HST counterpart and size fixed to median of high S/N sources  
  > "we discarded the fit and used a simpler model where the position is frozen to that of the HST counterpart" (4.2 Flux measurements)
   - software: CASA uvmodelfit
   - fitting: _not stated_
   - validation: Fake sources at random positions give mean 0.02±0.02 mJy; agree with ALESS for ID 23751  
  > "find a mean flux of $0.02\pm0.02\,{\rm mJy}$, indicating that our fluxes are not biased" (4.2 Flux measurements)
2. **Derive average dust temperature from stacked SED**: Median stack Spitzer, Herschel images, fit PSF; fit Schreiber2016 SED library with L_IR and T_dust free  
  > "we keep this last parameter fixed at ${\rm IR8}=8$" (5.1 Dust temperature and star-formation rates)
   - parameter: IR8=8; bootstrap uncertainties  
  > "Uncertainties are determined by bootstrapping the sample." (5.1 Dust temperature and star-formation rates)
   - assumption: Single T_dust=40 K for all galaxies; Kennicutt 1998 SFR conversion; Salpeter IMF  
  > "we choose here to assume a single dust temperature of $T_{\rm dust}=40\,{\rm K}$ for all galaxies" (5.1 Dust temperature and star-formation rates)
   - fitting: SED chi2 fit; reduced chi2 1.3  
  > "with a reduced $\chi^2$ of $1.3$ for both samples" (5.1 Dust temperature and star-formation rates)
   - validation: Refit excluding SPIRE bands changes T_dust by only 0.6 K  
  > "find higher $T_{\rm dust}$ values by only $0.6\,{\rm K}$" (5.1 Dust temperature and star-formation rates)
3. **Forward-model the sSFR distribution**: Mock catalogs with log-normal MS plus contaminant fraction, noise and measurement errors; chi2 grid in sigma_MS and sSFR_MS  
  > "A linear combination of these two histograms is then fit to our observed data" (5.3 Modeling the sSFR distribution)
   - software: phy++
   - parameter: Dz/(1+z)=6.5%, dlogM=0.14 dex; T_dust 40 K with 3 K scatter; sSFR ~(1+z)^1.5  
  > "with an average of $40\,{\rm K}$ and a Gaussian scatter of $3\,{\rm K}$" (5.3 Modeling the sSFR distribution)
   - fitting: Grid chi2 minimisation over sigma_MS and sSFR_MS; f_c from relative histogram weights  
  > "the relative weight of each histogram allows us to derive $f_{\rm c}$" (5.3 Modeling the sSFR distribution)
   - validation: Varied redshift/mass errors; scatter changes 0.02-0.05 dex; compared to Herschel stacking and simulations  
  > "our measured scatter would have been smaller by $0.02\,{\rm dex}$" (5.3 Modeling the sSFR distribution)

## Software

- **CASA** 4.3.1: pipeline calibration, cleaned images, uvmodelfit  
  > "using the CASA pipeline (version 4.3.1)" (4.1 Data)
- **phy++** : most of the analysis  
  > "Most of the analysis for this paper was done using `phy++`" (Acknowledgements)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Detections at >3 sigma | 30 of 96 | not stated | galaxies | 1 | we detect $46$, $30$ and $17$ galaxies at $>$$2$, $3$ and $5\sigma$ significance |
| Mean flux of sample | 1.00 | 0.04 | mJy | 1 | The mean flux of the sample is $1.00 \pm 0.04\,{\rm mJy}$ including non-detections. |
| T_dust full sample | 40 | 2 | K | 2 | $T_{\rm dust}=40\pm2$ and $43\pm1\,{\rm K}$ for the full sample and for the ALMA detections |
| sigma_MS | 0.28 | +0.14/-0.12 | dex | 3 | $\sigma_{\rm MS} = 0.28^{+0.14}_{-0.12}\,{\rm dex}$ |
| log10 sSFR_MS | 0.45 | +0.11/-0.18 | 1/Gyr (log) | 3 | $\log_{10}({\rm sSFR}_{\rm MS}\,[1/{\rm Gyr}]) = 0.45^{+0.11}_{-0.18}$ |
| Contaminant fraction | 25 | 0 to 40% within 1 sigma | % | 3 | the fit required a contaminant fraction of $f_{\rm c} = 25\%$ |
| Median SFR below/above 1e11 Msun | 138 and 406 | 22 and 25 | Msun/yr | 3 | $138\pm22$ and $406\pm25\,{\rm M}_\odot/{\rm yr}$ |

## Qualitative findings

- UVJ classification is unreliable for quiescent galaxies at z~4 in UDS and COSMOS  
  > "We conclude that the $UVJ$ classification in CANDELS UDS and COSMOS is indeed unreliable at these redshifts" (5.5 Contaminants: quiescent galaxies or redshift interlopers?)

## Claim tuples

- H: The main sequence is in place at z=4 with scatter similar to low z | E: Forward model sSFR distribution of ALMA-observed mass-selected galaxies | R: sigma_MS=0.28 dex, log sSFR_MS=0.45 | F: MS already in place at z=4 among massive galaxies, consistent with Illustris | **supported**
- H: Average dust temperature of the sample | E: Fit stacked Spitzer/Herschel/ALMA SED | R: T_dust=40±2 K | F: Average T_dust of 40 K, consistent with recent z~4 studies | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Low detection rate makes direct conclusions difficult, so forward modeling used without stacking  
  > "we use a forward modeling approach where we model the observed distribution of ${\rm sSFR}= {\rm SFR}/M_\ast$" (5.2 The z=4 main sequence)
- How they decided it was enough: _not stated_
- Limitation (authors): Sample likely biased against heavily obscured H-dropout galaxies  
  > "our parent sample is very likely biased against the most heavily obscured galaxies at these redshifts" (2.1 Observed sample)
- Caveat (inferred, ours): Single assumed T_dust=40 K drives SFRs
- Caveat (inferred, ours): Contaminant fraction degenerate between quiescent and interlopers
- Caveat (inferred, ours): Photometric redshifts only
- Caveat (inferred, ours): Only 3-parameter model

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Code: phy++ library is open source; analysis scripts not stated  
  > "a free and open source C++ library for fast and robust numerical astrophysics" (Acknowledgements)
- Missing: Flux catalog (Leiton et al. in prep.)
- Missing: Imaging details
- Missing: Stellar masses and photometric redshifts from Schreiber 2015 catalogs
- Data volume (inferred): Small: ~6 h Band 7 snapshots, likely tens of GB
- Score (inferred): 3/5, Data and main steps are described, but reduction details and catalog are deferred and inputs are external.
- Rediscovery candidate: no, Key recipe parts (catalog, masses, redshifts, SED library) are not in the paper.

## Links

- Method: (cite: schreiber2015) (stacking, photometry and mass methods)
- Method: (cite: schreiber2016-b) (dust SED library)
- Companion: Leiton et al. in prep. (full catalog and reduction)
- Related: CANDELS
- Related: ALESS

## Checks

```json
{
 "quotes": 46,
 "quotes_ok": 46,
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
  "stated": 35,
  "rate": 0.522
 },
 "evidence_ok": true
}
```
