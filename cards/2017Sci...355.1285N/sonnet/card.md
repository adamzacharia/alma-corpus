# [C II] 158-μm emission from the host galaxies of damped Lyman-alpha systems

`2017Sci...355.1285N` | Science 2017 | first author: Neeleman, Marcel | arXiv: 1703.07797 | DOI: 10.1126/science.aal1737

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies
- Question: Can the host galaxies of two high-metallicity z~4 damped Lyman-alpha absorbers be detected in [C II] 158 um and dust continuum, and how do they compare with emission-selected galaxies?  
  > "We report here on a search for the galaxies associated with two DLAs at $z \sim 4$ using the Atacama Large Millimeter/Sub-millimeter Array (ALMA)." (main text)
- Target **SDSS J081740.52+135134.5 (DLA host ALMA J081740.86+135138.2)**: coordinates 08:17:40.53 +13:51:34.6 (quasar field centre)  
  > "| $z_{\rm abs}$ |  | $4.2584 \pm 0.0001$ | $3.7975 \pm 0.0001$ |" (Table S3); "| Right Ascension | (J2000) | 08:17:40.53 | 12:01:10.31 |" (Table S1); z/distance z_abs = 4.2584; z_[CII] = 4.2601  
  > "| $z_{\rm abs}$ |  | $4.2584 \pm 0.0001$ | $3.7975 \pm 0.0001$ |" (Table S3); "| Right Ascension | (J2000) | 08:17:40.53 | 12:01:10.31 |" (Table S1); distance from DLA redshift from Keck/HIRES absorption spectra; [C II] redshift from ALMA  
  > "| $z_{\rm abs}$ |  | $4.2584 \pm 0.0001$ | $3.7975 \pm 0.0001$ |" (Table S3); "| Right Ascension | (J2000) | 08:17:40.53 | 12:01:10.31 |" (Table S1)
- Target **SDSS J120110.31+211758.5 (DLA host ALMA J120110.26+211756.2)**: coordinates 12:01:10.31 +21:17:58.5 (quasar field centre)  
  > "| $z_{\rm abs}$ |  | $4.2584 \pm 0.0001$ | $3.7975 \pm 0.0001$ |" (Table S3); "| Right Ascension | (J2000) | 08:17:40.53 | 12:01:10.31 |" (Table S1); z/distance z_abs = 3.7975; z_[CII] = 3.7978  
  > "| $z_{\rm abs}$ |  | $4.2584 \pm 0.0001$ | $3.7975 \pm 0.0001$ |" (Table S3); "| Right Ascension | (J2000) | 08:17:40.53 | 12:01:10.31 |" (Table S1); distance from DLA redshift from Keck/HIRES absorption spectra; [C II] redshift from ALMA  
  > "| $z_{\rm abs}$ |  | $4.2584 \pm 0.0001$ | $3.7975 \pm 0.0001$ |" (Table S3); "| Right Ascension | (J2000) | 08:17:40.53 | 12:01:10.31 |" (Table S1)

## Data provenance

- ALMA projects: 2015.1.01564.S
- bands: _not stated_
- frequencies and spectral setup: One 1.875 GHz band centred on redshifted [C II]; three 2 GHz bands for continuum; 128 channels of 15.625 MHz per band; central frequencies ~349-408 GHz  
  > "One of the ALMA 1.875 GHz bands was centered on the expected redshifted frequency of the [C II] 158$\upmu$m line" (Observations, Data Reduction and Analysis); "The remaining three 2 GHz bands were set to measure the continuum emission in the quasar fields." (Observations, Data Reduction and Analysis)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: Maximum baseline 263 m; 39 and 44 antennas  
  > "| Maximum Baseline | \(m\) | 263 | 263 |" (Table S1)
- angular resolution: Synthesized beams 1"x0.9" and 1.1"x0.9" (natural weighting)  
  > "yielding synthesized beams of $1''\times0.9''$ (SDSS J081740.52+135134.5) and $1.1''\times0.9''$ (SDSS J120110.31+211758.5)" (Observations, Data Reduction and Analysis)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: 46 min and 76 min (2782 s and 4596 s)  
  > "Total on-source integration times on the two quasar fields were 46 minutes and 76 minutes, respectively." (Observations, Data Reduction and Analysis)
- observing dates: 2015 December 29 to 2016 January 1  
  > "over a span of four days from 2015 December 29 to 2016 January 1" (Observations, Data Reduction and Analysis)
- pi or archival as stated: _not stated_
- Line: C II 2P3/2-2P1/2 fine structure (rest wavelength 157.74 um)
- Other facility **Keck-I HIRES**: Optical absorption spectra of the DLAs (redshift, N(HI), metallicity)  
  > "The optical spectra shown in Fig. 2 were obtained with the High Resolution (HIRES) Spectrograph on the Keck-I telescope" (Observations, Data Reduction and Analysis)
- Other facility **SDSS**: Quasar positions, redshifts and photometry  
  > "The position of the quasar, its redshift ($z_{\rm QSO}$), and photometry ($r$ and $i$ filters) are from the Sloan Digital Sky Survey (SDSS)" (Table S4 caption)
- External data: DLA redshift, N(HI) and metallicity from optical absorption spectra and Keck reductions  
  > "are derived from the optical absorption spectra (*6*)" (Table S3 caption) [from Rafelski et al. 2012 (ref 6)]
- External data: Comparison samples of z>1 galaxies and local [CII]-SFR relation  
  > "Also plotted is the correlation for galaxies in the local Universe (blue line), along with the associated scatter (blue dashed lines) (cite: DeLooze2014)." (Figure 4 caption) [from (cite: DeLooze2014); (cite: Carilli2013)]

## Processing

### Calibration

- pipeline or manual: Standard ALMA staff reduction, then re-examined in CASA and AIPS for extra flagging  
  > "The data were calibrated as part of the standard reduction procedure by the ALMA support staff (*34*)." (Observations, Data Reduction and Analysis)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: Self-calibrated on quasar continuum for SDSS J120110.31+211758.5 only; ~25% rms improvement  
  > "we self-calibrated the data set on the quasar continuum emission, resulting in an improvement of $\approx 25$% in the root mean square noise of the final image" (Observations, Data Reduction and Analysis)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "imaged, using natural weighting, yielding synthesized beams" (Observations, Data Reduction and Analysis)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: continuum subtracted from line band before cube imaging  
  > "imaged, after subtracting any continuum flux, using natural weighting to create a spectral data cube" (Observations, Data Reduction and Analysis)
- line free channels: _not stated_
- primary beam correction: applied to final cubes and continuum images  
  > "After applying the primary beam correction, the final spectral cubes and continuum images were analyzed" (Observations, Data Reduction and Analysis)
- array combination: _not stated_
- smoothing: Cubes averaged by four channels to 62.5 MHz (52 and 47 km/s)  
  > "The spectral cubes were then averaged by four channels to a resolution of 62.5 MHz" (Observations, Data Reduction and Analysis)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Optical spectra reduction and DLA properties  
  > "The data were reduced using standard reduction procedures (*6*)." (Observations, Data Reduction and Analysis) [from ref 6 (Rafelski et al. 2012)]
- SFR calibration from 158/160 um continuum luminosity  
  > "we use the standard calibration obtained from nearby star-forming galaxies (*41*)" (Physical Parameters of the DLA Host Galaxies) [from ref 41 (Calzetti et al. 2010)]
- Dynamical mass formula and v_circ=0.75 FWHM  
  > "$v_{\rm circ} = 0.75 \times {\rm FWHM_{[CII]}}$ (*43*)" (Physical Parameters of the DLA Host Galaxies) [from ref 43 (Wang et al. 2013)]
- Modified blackbody parameter ranges  
  > "consistent with other high redshift studies (*24*)" (Physical Parameters of the DLA Host Galaxies) [from ref 24 (Carilli & Walter 2013)]

### Not stated but needed to reproduce (our reading)

- CASA and AIPS versions
- Which channels were flagged and flagging criteria
- Line-free channels for continuum subtraction
- Cell and image size, clean thresholds
- Self-calibration solution intervals
- Details of the exponential disk fitting code (ref 44) and fit parameters
- Exact modified blackbody grid and how TIR was marginalised
- Flux calibrator and flux scale uncertainty

## Analysis recipe

1. **Image continuum and [C II] cube**: Natural-weighted imaging of three continuum bands; line band continuum-subtracted and imaged to cube, averaged by four channels  
  > "The visibility sets from the three bands set up for continuum measurements were imaged, using natural weighting" (Observations, Data Reduction and Analysis)
   - software: CASA, AIPS
   - fitting: _not stated_
   - validation: _not stated_
2. **Measure continuum and line fluxes, sizes**: Integrate flux over emission extent; noise from annulus; derive FWHM, z and integrated flux; CASA fitter for sizes  
  > "The continuum flux density of each DLA target was determined by integrating the observed flux density over the full extent of the continuum emission feature in the continuum image." (Observational Properties)
   - software: CASA
   - fitting: CASA fitter for sizes  
  > "We used the fitter function in CASA to determine the physical sizes" (Observational Properties)
   - validation: _not stated_
3. **Derive kinematic axis and p-v diagrams**: Straight line fit to positions of maximum flux in each velocity bin gives position angle  
  > "The direction of the axis was determined by fitting a straight line to the positions of maximum flux density in each velocity bin." (Observational Properties)
   - fitting: Bootstrapping for uncertainties  
  > "Uncertainties were determined through bootstrapping." (Observational Properties)
   - validation: _not stated_
4. **Estimate SFR and TIR luminosity**: SFR from 158 um continuum luminosity; TIR from modified blackbody models fit to single flux point  
  > "we apply a range of modified black body models, and fit these models to the measured 158 $\upmu$m continuum flux density" (Physical Parameters of the DLA Host Galaxies)
   - parameter: alpha 1.5-2.5, beta 1.2-2.0, dust T 25-45 K  
  > "the dust temperature in the range $25 - 45$ K" (Physical Parameters of the DLA Host Galaxies)
   - fitting: _not stated_
   - validation: Systematic TIR uncertainty factor 2.5  
  > "This results in a systematic uncertainty on the TIR by a factor of 2.5." (Physical Parameters of the DLA Host Galaxies)
5. **Estimate dynamical mass**: M_dyn = 1.16e5 v_circ^2 D; v_circ from exponential disk model fitted to cube with inclination fixed at 90 deg, giving lower limit  
  > "we have fixed the inclination to 90 degrees (i.e., an edge-on disk)" (Physical Parameters of the DLA Host Galaxies)
   - assumption: Edge-on disk, inclination 90 deg  
  > "since the velocity resolution of the data is insufficient to accurately estimate the inclination" (Physical Parameters of the DLA Host Galaxies)
   - fitting: Exponential disk model fit to spectral cube  
  > "The circular velocity is estimated by fitting an exponential disk model to the full spectral cube (*44*)." (Physical Parameters of the DLA Host Galaxies)
   - validation: Consistent with v_circ = 0.75 x FWHM  
  > "This lower limit is consistent with the circular velocity estimate obtained using $v_{\rm circ} = 0.75 \times {\rm FWHM_{[CII]}}$ (*43*)." (Physical Parameters of the DLA Host Galaxies)

## Software

- **CASA** : Flagging, imaging analysis, fitter for source sizes  
  > "re-examined using both the Common Astronomy Software Application (CASA) package (*35*)" (Observations, Data Reduction and Analysis)
- **AIPS** : Additional flagging of sub-standard channels  
  > "Astronomical Image Processing System (AIPS) package (*36*) to perform additional flagging of sub-standard channels" (Observations, Data Reduction and Analysis)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| z_[CII] ALMA J081740.86+135138.2 | 4.2601 | 0.0001 | dimensionless | 2 | $4.2601 \pm 0.0001$ |
| z_[CII] ALMA J120110.26+211756.2 | 3.7978 | 0.0001 | dimensionless | 2 | $3.7978 \pm 0.0001$ |
| Continuum flux density (J0817 host) | 1.19 | 0.11 | mJy | 2 | $1.19 \pm 0.11$ |
| Continuum flux density (J1201 host) | 0.31 | 0.11 | mJy | 2 | $0.31 \pm 0.11$ |
| Integrated [C II] flux (J0817 host) | 5.4 | 0.6 | Jy km/s | 2 | $5.4 \pm 0.6$ |
| Integrated [C II] flux (J1201 host) | 1.9 | 0.3 | Jy km/s | 2 | $1.9 \pm 0.3$ |
| SFR (J0817 host) | 110 | 10 | Msun/yr | 4 | SFR of $110 \pm 10$ M$_\odot~{\rm yr}^{-1}$ for ALMA J081740.86+135138.2 |
| SFR (J1201 host) | 24 | 8 | Msun/yr | 4 | $24 \pm 8$ M$_\odot~{\rm yr}^{-1}$ for ALMA J120110.26+211756.2 |
| log L_TIR (J0817 host) | 12.0 | 0.1 (stat) 0.4 (sys) | log Lsun | 4 | $12.0 \pm 0.1 \pm 0.4$ |
| log L_[CII] (J0817 host) | 9.48 | 0.05 | log Lsun | 2 | $9.48 \pm 0.05$ |
| log M_dyn (J0817 host) | >10.8 | not stated | log Msun | 5 | $>10.8$ |
| Impact parameters (proper) | 42 kpc and 18 kpc | not stated | kpc | 0 | The observed impact parameters correspond to physical (proper) distances of 42 kpc and 18 kpc |

## Qualitative findings

- [C II] and dust continuum emission detected from both DLA host galaxies, within 100 km/s of the absorption redshift  
  > "are within 100 km s$^{-1}$ of each other" (main text)

## Claim tuples

- H: Galaxies associated with high-metallicity z~4 DLAs can be detected in [C II] and dust continuum | E: ALMA Band 7 observations of two quasar fields | R: >6 sigma [C II] features at 6.2" and 2.5" offsets, with continuum | F: The emission arises from DLA host galaxies | **supported**
- H: DLA hosts resemble emission-selected galaxies | E: Compare L_[CII] vs SFR and L_[CII]/L_TIR vs L_TIR with literature samples | R: They lie in the same parameter space as high-z emission-selected galaxies | F: High-metallicity DLA hosts are similar to massive star-forming galaxies such as massive LBGs | **supported**
- H: Absorbing gas lies within an extended enriched H I reservoir | E: Compare impact parameters with [C II] extent and absorption kinematics | R: Impact parameters 18-42 kpc vs [C II] extent ~5 kpc | F: Absorbers likely probe inner halo gas of the host | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Satellite-galaxy origin of absorption disfavoured, as no [C II] is seen at the absorber position  
  > "The first explanation is disfavored, because the satellite galaxies would need to be metal-enriched" (main text)
- How they decided it was enough: _not stated_
- Limitation (authors): Inclination not constrained, so M_dyn is a lower limit; SFR systematic factor ~2.5; TIR systematic factor 2.5  
  > "systematic errors due to the conversion are expected to result in an additional uncertainty by a factor of $\sim 2.5$ in SFR" (Physical Parameters of the DLA Host Galaxies)
- Caveat (inferred, ours): TIR from a single continuum point with assumed SED
- Caveat (inferred, ours): Only two targets, selected for high metallicity
- Caveat (inferred, ours): Marginal spatial resolution limits kinematic modelling
- Caveat (inferred, ours): Third quasar in the program excluded

## Reproducibility

- Data public (paper): Data available through the ALMA archive and Keck Observatory Archive  
  > "The data reported in this paper are available though the ALMA archive" (Acknowledgments)
- Products in archive: _not stated_
- Missing: Software versions and imaging parameters
- Missing: Disk model code details
- Missing: Exact SED model grid
- Data volume (inferred): ~10-50 GB raw for two Band 7 fields
- Score (inferred): 5/5, Public data and a simple recipe, but CASA settings and disk-fit details are missing.
- Rediscovery candidate: yes, Public data, simple flux/line measurements with numeric results in Table S2.

## Links

- Method: (cite: Calzetti2010) (SFR calibration)
- Method: (cite: Wang2013) (Dynamical mass estimator)
- Companion: (cite: Rafelski2012) (DLA metallicity sample and HIRES data)
- Companion: (cite: Neeleman2016) (Related ALMA work on DLA hosts)
- Related: SDSS
- Related: Keck HIRES DLA sample

## Checks

```json
{
 "quotes": 69,
 "quotes_ok": 69,
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
  "facts": 76,
  "stated": 44,
  "rate": 0.579
 },
 "evidence_ok": true
}
```
