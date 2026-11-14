# Modelling high-resolution ALMA observations of strongly lensed highly star-forming galaxies detected by Herschel

`2018MNRAS.476.4383D` | Monthly Notices of the Royal Astronomical Society 2018 | first author: Dye, S. | arXiv: 1705.05413 | DOI: 10.1093/mnras/sty513

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies
- Question: What are the lens mass properties and intrinsic (de-magnified) properties of six Herschel-selected lensed submm galaxies, and do image-plane and visibility-plane lens modelling agree?  
  > "In this paper, we have opted to use both uv-plane and image-plane modelling, so that comparison between both methods can be made." (Introduction)
- Target **H-ATLAS J142413.9+022303**: coordinates J142413.9+022303 (from name)  
  > "| H-ATLAS J142413.9+022303 |   0.595$^a$   | 4.243$^b$ |" (Table 1); z/distance z_l=0.595, z_s=4.243  
  > "| H-ATLAS J142413.9+022303 |   0.595$^a$   | 4.243$^b$ |" (Table 1); distance from Bussmann et al. 2012 (lens); Cox et al. 2011 (source)  
  > "| H-ATLAS J142413.9+022303 |   0.595$^a$   | 4.243$^b$ |" (Table 1)
- Target **H-ATLAS J142935.3-002836**: coordinates J142935.3-002836 (from name)  
  > "| H-ATLAS J142935.3-002836 |   0.218$^c$   | 1.026$^d$ |" (Table 1); z/distance z_l=0.218, z_s=1.026  
  > "| H-ATLAS J142935.3-002836 |   0.218$^c$   | 1.026$^d$ |" (Table 1); distance from Messias et al. 2014 (lens); Negrello et al. 2017 (source)  
  > "| H-ATLAS J142935.3-002836 |   0.218$^c$   | 1.026$^d$ |" (Table 1)
- Target **HELMS J004714.2+032454**: coordinates J004714.2+032454 (from name)  
  > "| HELMS J004714.2+032454   |   0.478$^e$   | 1.190$^e$ |" (Table 1); z/distance z_l=0.478, z_s=1.190  
  > "| HELMS J004714.2+032454   |   0.478$^e$   | 1.190$^e$ |" (Table 1); distance from Nayyeri et al. 2016  
  > "| HELMS J004714.2+032454   |   0.478$^e$   | 1.190$^e$ |" (Table 1)
- Target **HELMS J001626.0+042613**: coordinates J001626.0+042613 (from name)  
  > "| HELMS J001626.0+042613   | 0.215$^{f,g}$ | 2.509$^e$ |" (Table 1); z/distance z_l=0.215, z_s=2.509  
  > "| HELMS J001626.0+042613   | 0.215$^{f,g}$ | 2.509$^e$ |" (Table 1); distance from Amvrosiadis et al. 2017 / Marchetti et al. in prep. (lens); Nayyeri et al. 2016 (source)  
  > "| HELMS J001626.0+042613   | 0.215$^{f,g}$ | 2.509$^e$ |" (Table 1)
- Target **HELMS J004723.6+015751**: coordinates J004723.6+015751 (from name)  
  > "| HELMS J004723.6+015751   | 0.365$^{f,g}$ | 1.441$^e$ |" (Table 1); z/distance z_l=0.365, z_s=1.441  
  > "| HELMS J004723.6+015751   | 0.365$^{f,g}$ | 1.441$^e$ |" (Table 1); distance from Amvrosiadis et al. 2017 / Marchetti et al. in prep. (lens); Nayyeri et al. 2016 (source)  
  > "| HELMS J004723.6+015751   | 0.365$^{f,g}$ | 1.441$^e$ |" (Table 1)
- Target **HELMS J001615.7+032435**: coordinates J001615.7+032435 (from name)  
  > "| HELMS J001615.7+032435   |   0.663$^e$   | 2.765$^e$ |" (Table 1); z/distance z_l=0.663, z_s=2.765  
  > "| HELMS J001615.7+032435   |   0.663$^e$   | 2.765$^e$ |" (Table 1); distance from Nayyeri et al. 2016  
  > "| HELMS J001615.7+032435   |   0.663$^e$   | 2.765$^e$ |" (Table 1)

## Data provenance

- ALMA projects: 2013.1.00358.S
- bands: Band 7 continuum  
  > "comprising Band 7 continuum observations in four spectral windows, each of width 1875 MHz centred on the frequencies 336.5, 338.5, 348.5 and 350.5 GHz." (2 Data)
- frequencies and spectral setup: four 1875 MHz spectral windows at 336.5, 338.5, 348.5, 350.5 GHz; 128 channels each, 15.6 MHz resolution  
  > "In each spectral window, there are 128 frequency channels giving a resolution of 15.6 MHz." (2 Data)
- continuum bandwidth: _not stated_
- arrays: forty two 12 m antennas  
  > "Forty two 12 m antennas were used with an on-source integration time of approximately 125 s." (2 Data)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.12 arcsec  
  > "This results in an angular resolution of 0.12 arcsec" (2 Data)
- max recoverable scale: _not stated_
- sensitivity: ~230 uJy/beam (H-ATLAS), ~130 uJy/beam (HELMS) after combining all spectral windows  
  > "an RMS of approximately 230 $\mu$Jy/beam and 130 $\mu$Jy/beam for the H-ATLAS and HELMS sources respectively after combining all four spectral windows" (2 Data)
- time on source: approximately 125 s  
  > "Forty two 12 m antennas were used with an on-source integration time of approximately 125 s." (2 Data)
- observing dates: _not stated_
- pi or archival as stated: PI: Eales; calibrated visibilities from ALMA science archive  
  > "we have used the calibrated visibilities as provided in the ALMA science archive." (2 Data)
- Other facility **Herschel SPIRE/PACS**: 100-500 um photometry for SED fitting  
  > "For the H-ATLAS sources, SPIRE and PACS photometry was taken from the H-ATLAS first data release (cite: valiante16)." (2 Data)
- Other facility **SMA**: 880 um photometry where available  
  > "Where available, we have also used $880\,\mu$m photometry obtained with the Submillimeter Array (SMA) as detailed in (cite: bussmann13)" (2 Data)
- Other facility **SCUBA-2**: 850 um fluxes  
  > "$850\,\mu$m Submillimeter Common User Bolometer Array 2 fluxes as given in Bakx et al. (2017, in prep.)" (2 Data)
- Other facility **IRAS**: 60 um flux for J142935.3-002836  
  > "we have taken the 60$\,\mu$m flux density as given in the IRAS faint source catalogue (cite: moshir92)." (2 Data)
- External data: HELMS SPIRE fluxes  
  > "For the HELMS sources, SPIRE fluxes were taken from (cite: nayyeri16)" (2 Data) [from (cite: nayyeri16)]
- External data: H-ATLAS SPIRE and PACS photometry  
  > "For the H-ATLAS sources, SPIRE and PACS photometry was taken from the H-ATLAS first data release (cite: valiante16)." (2 Data) [from (cite: valiante16)]
- External data: ALMA Band 6 (1280 um) photometry  
  > "ALMA Band 6 data (1280 $\mu$m) from (cite: messias14)" (2 Data) [from (cite: messias14)]
- External data: Lens and source redshifts  
  > "$^e$(cite: nayyeri16). $^f$(cite: amvrosiadis17). $^g$Marchetti et al. (in prep.)." (Table 1) [from bussmann12, cox11, messias14, negrello17, nayyeri16, amvrosiadis17]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: CASA 4.3.1  
  > "Both calibration and cleaning were carried out using version 4.3.1 of the `Common Astronomy Software Applications` package" (2 Data)
- pipeline version: _not stated_
- archive products used as is: calibrated visibilities from ALMA science archive used  
  > "we have used the calibrated visibilities as provided in the ALMA science archive." (2 Data)
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: none; sources too faint, external calibrator phase calibration applied  
  > "the sources are too faint to provide such self-calibration hence we have instead opted to apply the phase calibration provided by external calibrators" (3.1 Adapting the SLI method)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: Briggs, robustness -0.2  
  > "constructed using Briggs weighting with a robustness parameter of -0.2 and were primary beam corrected." (2 Data)
- uv taper: _not stated_
- cell size: 0.02 arcsec (H-ATLAS), 0.03 arcsec (HELMS)  
  > "The image pixel scale used for the H-ATLAS and HELMS sources was 0.02 and 0.03 arcsec respectively." (2 Data)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: applied  
  > "constructed using Briggs weighting with a robustness parameter of -0.2 and were primary beam corrected." (2 Data)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Image-plane Voronoi SLI implementation, regularisation scheme  
  > "The image plane version adopts an implementation similar to that described by (cite: nightingale15) which uses a randomised Voronoi tessellation in the source plane" (3 Methodology) [from (cite: nightingale15)]
- Visibility uncertainty estimation method  
  > "We used a similar method as (cite: hezaveh16) for determining the $1\sigma$ uncertainties, $\sigma_j$, on the visibilities." (3.1 Adapting the SLI method) [from (cite: hezaveh16)]
- Regularisation weight optimisation  
  > "the regularisation weight was optimised following the procedure outlined in (cite: dye08)." (3.1 Adapting the SLI method) [from (cite: dye08)]
- Dust mass method  
  > "which we computed using the method outlined in (cite: dunne11)." (4.1 Intrinsic source properties) [from (cite: dunne11)]

### Not stated but needed to reproduce (our reading)

- MCMC sampler, priors, chain settings and convergence criteria
- Number of Voronoi source pixels and k-means settings
- Visibility averaging/uv-grouping used for sigma_j
- Which spectral windows/channels were averaged and CLEAN parameters (mask, threshold, iterations)
- Range of fixed slopes alpha scanned
- Source code of lens modelling not released
- SED fitting code and priors; far-IR luminosity and gas mass conversion details

## Analysis recipe

1. **Image-plane lens modelling**: Semi-linear inversion with Voronoi source pixels, Bayesian evidence maximised by MCMC, on cleaned image  
  > "we have used k-means clustering for the source pixels and Markov Chain Monte Carlo (MCMC) optimisation" (3 Methodology)
   - software: MCMC (unnamed code)
   - parameter: power-law slopes fixed per run; number of source pixels fixed  
  > "We performed multiple MCMC runs for a range of power-law density profile slopes which were kept fixed in each case to help simplify parameter space." (3.1 Adapting the SLI method)
   - assumption: Elliptical power-law density profile plus external shear only when evidence improved  
  > "We only incorporated external shear in the lens model when the Bayesian evidence was improved by its inclusion." (3.2 Lens model)
   - fitting: Maximise Bayesian evidence of Suyu et al. 2006  
  > "we used Markov Chain Monte Carlo (MCMC) optimisation to maximise the Bayesian evidence derived by (cite: suyu06)." (3.1 Adapting the SLI method)
   - validation: Compared with visibility-plane results; beam sidelobe test  
  > "We therefore conclude that beam sidelobes in the current data play a negligible role." (4 Results)
2. **Visibility-plane lens modelling**: Model visibilities for each source pixel via MIRIAD uvmodel; chi-squared on complex visibilities  
  > "This is achieved by incorporating the ` MIRIAD` software package library (cite: sault95) into our reconstruction code, but using a much streamlined version of the ` uvmodel` procedure." (3.1 Adapting the SLI method)
   - software: MIRIAD
   - assumption: no covariance between visibilities  
  > "it is assumed that there is no covariance between visibilities" (3.1 Adapting the SLI method)
   - fitting: _not stated_
   - validation: Compared to image-plane parameters; mild differences only for HELMS J001615.7+032435  
  > "On the whole, there is good agreement between the parameters obtained using the two methods" (4 Results)
3. **Compute magnifications**: Average magnification over 100 source plane pixelisations using best-fit image-plane model  
  > "computed the average source magnification factor of 100 different source plane pixelisations." (4 Results)
   - fitting: _not stated_
   - validation: _not stated_
4. **SED fitting and intrinsic properties**: De-magnify photometry; fit single-temperature optically thick and dual-temperature optically thin SEDs; dust mass via Dunne et al. method; SFR from L_FIR  
  > "we then fitted the rest-frame photometry with both a single temperature optically thick spectral energy distribution (SED) and a dual temperature optically thin SED." (4.1 Intrinsic source properties)
   - parameter: emissivity index fixed to 2.0; L_FIR integrated 3-1100 um  
  > "In all cases, the emissivity index was fixed to 2.0 (cite: smith13)." (4.1 Intrinsic source properties)
   - assumption: kappa_850=0.077 m^2/kg; Kroupa IMF with Kennicutt & Evans SFR conversion  
  > "extrapolating the 850 $\mu$m value of $\kappa_{850}=0.077$ m$^2$kg$^{-1}$ (cite: james02)" (4.1 Intrinsic source properties)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.3.1: calibration and cleaning  
  > "Both calibration and cleaning were carried out using version 4.3.1 of the `Common Astronomy Software Applications` package" (2 Data)
- **MIRIAD** : uvmodel to compute model visibilities  
  > "This is achieved by incorporating the ` MIRIAD` software package library (cite: sault95) into our reconstruction code" (3.1 Adapting the SLI method)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Power-law slope alpha, H-ATLAS J142413.9 (image plane) | 2.03 | 0.04 | dimensionless | 1 | / H-ATLAS J142413.9 / $0.59\pm0.01$ / $(0.18\pm 0.01,0.68\pm0.01)$ / $84\pm2$ / $1.07\pm0.02$ / $2.03\pm0.04$ / |
| Einstein radius HELMS J004723.6 (image plane) | 2.16 | 0.10 | arcsec | 1 | $2.16\pm0.10$ |
| Total magnification H-ATLAS J142935.3 (image plane) | 23.6 | 1.3 | dimensionless | 3 | / H-ATLAS J142935.3 / $23.6\pm1.3$ / $22.3\pm1.3$ / |
| SFR H-ATLAS J142413.9 | 2200 | 500 | Msun/yr | 4 | $2200 \pm 500$ |
| SFE increase relative to SMG/ULIRG relation | factor of 5 (40 relative to z<0.5 H-ATLAS galaxies) | not stated | dimensionless | 4 | the increase in SFE is a factor of 5 relative to that implied by the SMG/ULIRG relationship of Rowlands et al. and a factor of 40 relative to $z<0.5$ H-ATLAS galaxies. |

## Qualitative findings

- Lenses all have near-isothermal density profiles; reconstructed sources mostly disturbed  
  > "all six having mass density profiles that are close to isothermal." (abstract)

## Claim tuples

- H: Do image-plane and visibility-plane modelling give consistent lens models? | E: Modelled both cleaned images and visibilities for six lenses | R: Parameters agree except mildly for HELMS J001615.7+032435 | F: Image-plane modelling is adequate and an order of magnitude faster | **supported**
- H: Are the lensed sources highly star-forming relative to dust mass? | E: Demagnified photometry, SED fits, SFR/dust mass vs Rowlands et al. | R: Five of six exceed mean SFR/dust mass ratio | F: High SFR-to-dust ratios, implying higher SFE or dense gas fraction | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Both approaches compared since image-plane can bias when uv coverage is sparse  
  > "This can in principle cause biases in the lens modelling, especially when coverage of the uv-plane is sparse." (Introduction)
- Alternative: External SIE for HELMS J001615.7 less favoured by Bayesian evidence  
  > "However, the model is less favoured by the Bayesian evidence" (Object notes)
- How they decided it was enough: _not stated_
- Limitation (authors): Low S/N and undetected counter-image in HELMS J001615.7+032435 raise modelling uncertainty  
  > "results in an undetected counter-image which increases the modelling uncertainty for this system." (Object notes)
- Caveat (inferred, ours): No sampler/prior details; uncertainties on lens parameters may be underestimated
- Caveat (inferred, ours): Dust mass and SFR uncertainties are from SED fits with fixed emissivity
- Caveat (inferred, ours): Uniform noise map used for image plane ignores pixel correlation

## Reproducibility

- Data public (paper): ALMA dataset 2013.1.00358.S from ALMA science archive  
  > "we have used the calibrated visibilities as provided in the ALMA science archive." (2 Data)
- Products in archive: _not stated_
- Missing: Lens modelling code not released
- Missing: MCMC and SED fitting settings
- Missing: Some photometry from in-prep papers
- Data volume (inferred): ~tens of GB
- Score (inferred): 3/5, Public archival data and clear model description, but custom unreleased code and missing sampler settings.
- Rediscovery candidate: no, Requires custom uv-plane lens modelling code not released and unspecified MCMC settings.

## Links

- Method: (cite: warren03) (semi-linear inversion lens modelling)
- Method: (cite: suyu06) (Bayesian evidence framework)
- Method: (cite: nightingale15) (Voronoi source plane implementation)
- Method: (cite: hezaveh16) (visibility-plane SLI applied to ALMA)
- Companion: (cite: dye15) (image-plane modelling of SDP.81)
- Companion: (cite: nayyeri16) (HELMS lens sample)
- Related: H-ATLAS
- Related: HerMES Large Mode Survey

## Checks

```json
{
 "quotes": 72,
 "quotes_ok": 72,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 92,
  "stated": 63,
  "rate": 0.685
 },
 "evidence_ok": true
}
```
