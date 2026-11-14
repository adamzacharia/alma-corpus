# VALES. VII. Molecular and ionized gas properties in the pressure balanced interstellar medium of starburst galaxies at z ∼ 0.15

`2020A&A...643A..78M` | Astronomy and Astrophysics 2020 | first author: Molina, Juan | arXiv: 2009.08446 | DOI: 10.1051/0004-6361/202039008

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies
- Question: How do the morpho-kinematics of ionized (Paα) and molecular (CO 1-0) gas in three dusty starbursts at z~0.12-0.18 relate to ISM pressure balance, alpha_CO and star formation activity?  
  > "We aim to study the morpho-kinematic properties of the ionized and molecular gas in three dusty starburst galaxies at z = 0.12 − 0.17" (abstract)
- Target **HATLASJ090750.0+010141**: coordinates 09:07:50.07 +01:01:41.47  
  > "RA (J2000) 09:07:50.07 11:46:25.01 12:14:46.47" (Table 2); "z spec 0.12834 0.16553 0.17981" (Table 2); z/distance z_spec = 0.12834  
  > "RA (J2000) 09:07:50.07 11:46:25.01 12:14:46.47" (Table 2); "z spec 0.12834 0.16553 0.17981" (Table 2); distance from _not stated_
- Target **HATLASJ114625.4-014511**: coordinates 11:46:25.01 -01:45:12.81  
  > "RA (J2000) 09:07:50.07 11:46:25.01 12:14:46.47" (Table 2); "z spec 0.12834 0.16553 0.17981" (Table 2); z/distance z_spec = 0.16553  
  > "RA (J2000) 09:07:50.07 11:46:25.01 12:14:46.47" (Table 2); "z spec 0.12834 0.16553 0.17981" (Table 2); distance from _not stated_
- Target **HATLASJ121446.0-011155**: coordinates 12:14:46.47 -01:11:55.55  
  > "RA (J2000) 09:07:50.07 11:46:25.01 12:14:46.47" (Table 2); "z spec 0.12834 0.16553 0.17981" (Table 2); z/distance z_spec = 0.17981  
  > "RA (J2000) 09:07:50.07 11:46:25.01 12:14:46.47" (Table 2); "z spec 0.12834 0.16553 0.17981" (Table 2); distance from _not stated_

## Data provenance

- ALMA projects: 2015.1.01012.S
- bands: Band 3  
  > "Observations were taken on Band-3 with the extended 12 m array" (2.2 ALMA observations)
- frequencies and spectral setup: One FDM window of 1.875 GHz at 3906.250 kHz native resolution on redshifted CO(1-0) (97-103 GHz); three TDM windows for continuum  
  > "using a spectral window in Frequency Division Mode to cover 1.875 GHz of bandwidth at a native 3906.250 kHz resolution" (2.2 ALMA observations)
- continuum bandwidth: 6 GHz  
  > "The continuum emission image, obtained over 6 GHz bandwidth reaches noise levels of 13µJy beam" (2.2 ALMA observations)
- arrays: 12 m array, 36-38 antennas  
  > "using 36 to 38 antennas with a maximum baseline of 1.5 km" (2.2 ALMA observations)
- configurations: _not stated_
- baselines: maximum baseline 1.5 km  
  > "using 36 to 38 antennas with a maximum baseline of 1.5 km" (2.2 ALMA observations)
- angular resolution: 0.45-0.52 arcsec beam major axis  
  > "in a range between 0′′.45–0′′.52" (2.2 ALMA observations)
- max recoverable scale: _not stated_
- sensitivity: rms ~400-500 µJy/beam at ~12 km/s channels; continuum 13 µJy/beam  
  > "Final images reach r.m.s. noises of ∼ 400–500µJy beam−1 at ≈ 12 km s−1 channel width." (2.2 ALMA observations)
- time on source: 35 min per target  
  > "36 35 0′′.52" (Table 1)
- observing dates: 9, 11, 13 Aug 2016  
  > "9 Aug. 2016 J1229+0203" (Table 1)
- pi or archival as stated: PI E. Ibar, project 2015.1.01012.S  
  > "taken from project 2015.1.01012.S; P.I.: E. Ibar" (2.2 ALMA observations)
- Line: CO J=1-0 (115.271 GHz)
- Line: Paα (SINFONI) Paschen alpha (1.8751 µm)
- Other facility **VLT/SINFONI**: Seeing-limited Paα IFU data (project 099.B-0479(A))  
  > "Project 099.B-0479(A); P.I. J.Molina" (2.3 SINFONI observations)
- Other facility **GAMA DR3 / WISE**: K-band Sérsic models, Hα/Hβ/[NII]/[OIII] fluxes, WISE colours  
  > "taken from the GAMA DR3 (Baldry et al. 2018)" (Table A.1)
- External data: Stellar masses from magphys SED fitting  
  > "The stellar masses for the three galaxies were estimated in Villanueva et al. (2017)" (2.4 Stellar Mass and IR-based SFR estimates) [from Villanueva et al. 2017]
- External data: CO(1-0) flux densities and luminosities from earlier ALMA data  
  > "The total galaxy CO(1-0) velocity-integrated flux densities ( S CO(1−0) ∆ v ) are taken from Villanueva et al. (2017)." (2.5 CO(1-0) Luminosities) [from Villanueva et al. 2017]
- External data: L_IR values for IR-based SFR  
  > "luminosity ( L IR ) estimates taken from Ibar et al. (2015)" (2.4 Stellar Mass and IR-based SFR estimates) [from Ibar et al. 2015]
- External data: K-band Sérsic parameters  
  > "Sérsic best-fit model parameters taken from the GAMA-DR3 for our sample (Kelvin et al. 2012)" (Table 3) [from Kelvin et al. 2012]

## Processing

### Calibration

- pipeline or manual: Provided ALMA pipeline to calibrated uv products; days concatenated before imaging  
  > "using the provided ALMA pipeline up to calibrated uv products" (2.2 ALMA observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J1229+0203 (two targets), J0854+2006 (third)  
  > "J1229+0203 J1229+0203 J1150−0023 0.80 36 35" (Table 1)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: tclean  
  > "After exploring different imaging approaches using task tclean" (2.2 ALMA observations)
- deconvolver: _not stated_
- weighting robust: Briggs, robust=0.4  
  > "we decided to use a Briggs weighting (robust=0.4)" (2.2 ALMA observations)
- uv taper: _not stated_
- cell size: 0.1 arcsec  
  > "The pixel size is set to 0′′.1." (2.2 ALMA observations)
- image size: _not stated_
- masking: Interactive cleaning to 2-3σ in channels with source emission  
  > "the signal was interactively cleaned down to 2–3-σ in spectral channels with confident source emission" (2.2 ALMA observations)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: Slight convolution within tclean to circular beam  
  > "we apply a slight convolution (within tclean) to obtain a circular beam" (2.2 ALMA observations)
- final beam: _not stated_
- final rms: 400-500 µJy/beam at ~12 km/s  
  > "Final images reach r.m.s. noises of ∼ 400–500µJy beam−1" (2.2 ALMA observations)

### Inherited from earlier work

- Moment maps built following Swinbank et al. (2012)  
  > "We construct the two-dimensional moment maps by following Swinbank et al. (2012)." (3.2 Galaxy Dynamics) [from Swinbank et al. (2012)]
- Beam-smearing velocity dispersion correction  
  > "we apply the correction suggested by Stott et al. (2016)" (3.2.2 Kinematic Parameters) [from Stott et al. (2016)]
- Stellar mass truncation by K-band Sérsic profile  
  > "the stellar masses are truncated using the K -band Sérsic model profile following Molina et al. (2019a)" (3.3 The CO-to-H2 conversion factor from dynamics) [from Molina et al. (2019a)]
- Channel width choice  
  > "The channel width is set to minimize spectral resolution effects (Molina et al. 2019b)." (2.2 ALMA observations) [from Molina et al. 2019b]
- Pressure balance model  
  > "We choose Wilson et al. (2019)’s ISM pressure balance model" (4.1 What sets the molecular gas velocity dispersions?) [from Wilson et al. (2019)]

### Not stated but needed to reproduce (our reading)

- Spectral window frequencies/line-free channels and continuum subtraction method
- Self-calibration use
- Primary-beam correction and imaging cube size
- emcee priors, walkers, steps and likelihood details for kinematic and alpha_CO fits
- Adopted scale height/Sérsic inputs and Σ_SFR pixel selection thresholds
- CASA version
- Data-reduction details for SINFONI line fitting masks

## Analysis recipe

1. **Image ALMA CO(1-0) cubes**: Pipeline-calibrated data concatenated and imaged with tclean, Briggs weighting  
  > "Data taken in different days were concatenated together after running the pipeline and before imaging." (2.2 ALMA observations)
   - software: CASA, tclean
   - parameter: robust=0.4, pixel 0.1 arcsec, ~12 km/s channels  
  > "Briggs weighting (robust=0.4)" (2.2 ALMA observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **Build moment maps by Gaussian line fitting**: Per-pixel Gaussian fit on spectra averaged over a resolution element, adaptive binning up to two more times if S/N<5; MC errors  
  > "We apply an S/N = 5 threshold to determine whether we have detected an emission line or not." (3.2 Galaxy Dynamics)
   - software: lmfit
   - fitting: Gaussian least squares with lmfit; Monte Carlo resampling for uncertainties  
  > "We use the lmfit Python package (Newville et al. 2014) to fit a Gaussian profile to the emission lines." (3.2 Galaxy Dynamics)
   - validation: _not stated_
3. **Fit 2D kinematic disc models**: Arctan rotation curve, 7 free parameters, convolved with beam/PSF, fit with emcee; inclination constrained from K-band Sérsic b/a  
  > "For each observation, the kinematic model considers seven free parameters ( V 0, V asym, R t, PA, [ x / y ], and inclination angle)." (3.2.1 Kinematic Modelling)
   - software: emcee
   - parameter: b/a 1σ relative error 10%; q0 = 0.14  
  > "We use q 0 = 0.14 mean" (3.2.1 Kinematic Modelling)
   - assumption: oblate spheroid geometry for inclination  
  > "considering an oblate spheroid geometry (Holmberg 1958)" (3.2.1 Kinematic Modelling)
   - fitting: emcee MCMC; priors not stated  
  > "we use a Markov Chain Monte Carlo (MCMC) technique (Calistro Rivera et al. 2018; Molina et al. 2019b) implemented in emcee (Foreman-Mackey et al. 2013)." (3.3. The CO-to-H2 conversion factor from dynamics)
   - validation: Residual maps and reduced chi-square  
  > "The model best-fit parameters and χ 2 ν values are given in Table 4" (3.2.1 Kinematic Modelling)
4. **Extract rotation curves and dispersions**: Simulated slit along major axis; tilted rings for R1/2; Vrot at 2R1/2; sigma corrected for beam smearing and taken as median beyond 3 beams  
  > "we define the global velocity dispersion for each gas phase (σ v,CO, σ v,Paα ) as the median value taken from the pixels located beyond three times the synthesized beam or PSF FWHM" (3.2.2 Kinematic Parameters)
   - fitting: _not stated_
   - validation: _not stated_
5. **Derive alpha_CO from dynamical mass**: Fit alpha_CO and f_DM(R) with Mdyn = Vcirc^2 R/G (thin and thick disc; Sérsic and exponential mass profiles) against Mstar + alpha_CO L'CO  
  > "Thus, we employ a total of four different dynamical models per galaxy." (3.3 The CO-to-H2 conversion factor from dynamics)
   - software: emcee
   - parameter: Rotation velocity beam-smearing correction ≲10%; only radii beyond 3 beams  
  > "we also apply a correction factor (≲ 10 %) to the rotation velocity values" (3.3 The CO-to-H2 conversion factor from dynamics)
   - assumption: Mdyn = stars + H2 + dark matter; constant alpha_CO across disc; HI negligible in inner region  
  > "we also assume a constant α CO value across each galactic disc" (3.3 The CO-to-H2 conversion factor from dynamics)
   - fitting: MCMC in emcee with likelihood on L'CO, Mdyn, Mstar  
  > "by considering the likelihood of the estimated L CO ′, M dyn and M ⋆ values" (3.3 The CO-to-H2 conversion factor from dynamics)
   - validation: Comparison of four dynamical models; no-dark-matter limit gives ≲14% higher alpha_CO  
  > "the median α CO values increase by ≲14 %" (4.4 Limitations of our dynamical mass approach)
6. **Test vertical pressure balance and scale height**: Compare pixel σ_CO vs Σ_H2 and Σ_Tot with Wilson et al. 2019 model; derive h_H2  
  > "By using Eq. 8 we estimate roughly h H 2 for both starbursts." (4.1 What sets the molecular gas velocity dispersions?)
   - parameter: ψ ~0.3, γ ~0.05  
  > "it contributes a small correction for both galaxies (γ ∼ 0.05)" (4.1 What sets the molecular gas velocity dispersions?)
   - assumption: Σ⋆ from K-band image scaled to magphys M⋆ (constant M/L)  
  > "scaling the SINFONI K -band continuum image surface brightness distribution" (4.1 What sets the molecular gas velocity dispersions?)
   - fitting: _not stated_
   - validation: _not stated_
7. **Σ_SFR–Σ_H2 and Σ_SFR–P_grav relations**: Register Paα and CO maps, compute pixel Σ_SFR and Σ_H2, fit log-log power law to combined samples with emcee  
  > "By performing a linear fit in the log-log parameter space (log 10 (Σ SFR ) = N × log 10 ( P grav / P 0 )) using emcee" (4.3 Pressure regulated star-formation activity)
   - software: IDL hastrom, emcee
   - parameter: 0.2 dex uncertainties for PHANGS data  
  > "we have adopted conservative 0.2 dex uncertainties for the PHANGS data estimates" (4.3 Pressure regulated star-formation activity)
   - assumption: SFR_Paα = 4.0e-41 L_Paα; intrinsic Hα/Paα 0.116  
  > "SFR Paα ( M ⊙ yr −1 ) = 4.0 × 10 −41 × L Paα (erg s −1 )" (3.1 Average ISM properties)
   - fitting: emcee linear fit in log-log; priors not stated  
  > "using emcee (ForemanMackey et al. 2013), we find a best-fit slope" (4.3. Pressure regulated star-formation activity)
   - validation: Residual rms compared with Sun et al. 2020 fit  
  > "We measure r.m.s. ≈ 0.34 and ≈ 0.36 dex from our and Sun et al. (2020) best-fits" (4.3 Pressure regulated star-formation activity)

## Software

- **CASA** : ALMA pipeline calibration, imaging and gaussfit  
  > "Data reduction was carried out using the Common Astronomy Software Applications (CASA)" (2.2 ALMA observations)
- **tclean** : Imaging CO cubes  
  > "using task tclean" (2.2 ALMA observations)
- **emcee** : Kinematic modelling, alpha_CO MCMC and Σ_SFR–P_grav fit  
  > "we use the emcee Python package (ForemanMackey et al. 2013) to find the best-fit model" (3.2.1 Kinematic Modelling)
- **lmfit** : Gaussian line fits  
  > "We use the lmfit Python package (Newville et al. 2014)" (3.2 Galaxy Dynamics)
- **ESOREX/esoreflex** : SINFONI reduction  
  > "To reduce the data, first, we use the SINFONI esoreflex and esorex pipelines." (2.3.2. 'OOOO' Jittering)
- **SkyCor** : Sky line subtraction for OOOO data  
  > "sky emission lines are subtracted using SkyCor (Noll et al. 2014)" (2.3.2 ‘OOOO’ Jittering)
- **Molecfit** : Telluric correction  
  > "Molecfit (Kausch et al. 2015) is implemented to remove telluric absorption bandpass lines" (2.3.2 ‘OOOO’ Jittering)
- **magphys** : Stellar masses from SED fitting (previous work)  
  > "Bayesian SED fitting code magphys (Da Cunha et al. 2008)" (2.4 Stellar Mass and IR-based SFR estimates)
- **VOSA** : Standard star SED for flux calibration  
  > "Visual Observatory SED Analyser (VOSA, Bayo et al. 2008)" (2.3.3 Flux calibration)
- **IDL hastrom** : Registering images to common pixel grid  
  > "We use the hastrom task written in the Interactive Data Language (IDL)" (4.2 The star-formation activity traced at ∼ kpc-scales)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| alpha_CO HATLAS114625 | 0.7 | +0.5/-0.3 | Msun (K km/s pc^2)^-1 | 5 | 0.7 − [+] 0 [0] . [.] 3 [5] 1.2 [+] − [1] 0 [.] . [0] 6 |
| alpha_CO HATLAS121446 | 1.2 | +1.0/-0.6 | Msun (K km/s pc^2)^-1 | 5 | 0.7 − [+] 0 [0] . [.] 3 [5] 1.2 [+] − [1] 0 [.] . [0] 6 |
| alpha_CO upper limits (3σ) | 2.7 and 5.1 | not stated | Msun (K km/s pc^2)^-1 | 5 | α CO,uplim = 2.7 and 5.1 M ⊙ (K km s −1 pc 2 ) −1 for HATLAS114625 and HATLAS121446 |
| Sigma_SFR–P_grav slope N | 0.78 | 0.01 | dimensionless | 7 | we find a best-fit slope N = 0.78 ± 0.01 |
| log10(P0/kB) | 5.38 | 0.04 | cm^-3 K | 7 | log 10 ( P 0 / k B [cm −3 K]) = 5.38 ± 0.04 |
| CO velocity dispersion sigma_v,CO (114625, 121446) | 26 and 34 | ±10, ±11 | km/s | 4 | σ v,CO (km s −1 ) 35 ± 12 26 ± 10 34 ± 11 |
| Vrot,CO/sigma_v,CO | 8 and 7 | ±3, ±2 | dimensionless | 4 | of 8 ± 3 and 7 ± 2 for HATLAS114625 and HATLAS121446, respectively |
| Molecular gas mass | 6.0 and 10.3 (x10^9) | +4.3/-2.6; +8.7/-5.3 (as extracted) | Msun | 5 | M H 2 (× 10 9 M ⊙ ) 6.0 [+] − [4] 2 [.] . [3] 6 10.3 − [+] 5 [8] . [.] 3 [7] |
| Molecular gas scale height h_H2 | 200 and 160 | +250/-130; +570/-80 | pc | 6 | we obtain h H 2 ∼ 200 [+] − [250] 130 and 160 [+] − [570] 80 [pc] [median] [values] |
| Depletion time range | ~0.1–1 | not stated | Gyr | 7 | The two galaxies presented in this work exhibit τ dep values in the range of ∼0.1–1 Gyr |
| Warm H2 rotational temperature (HATLAS090750) | 1600 | ±400 | K | 0 | linear fit with T rot ≈ 1600±400 K |

## Qualitative findings

- HATLAS090750 has irregular morpho-kinematics consistent with a merger; the other two are disc-like.  
  > "One starburst galaxy shows irregular morphology which may indicate a major merger, while the other two systems show disc-like morpho-kinematics." (abstract)
- The disc starbursts have molecular gas fractions ~0.1, not gas-rich as initially expected.  
  > "we obtain molecular gas fractions of the order of ∼ 0.1 for both starbursts" (5 Conclusions)

## Claim tuples

- H: Is the molecular gas velocity dispersion set by vertical pressure balance? | E: Compare pixel σ_CO vs Σ_H2/Σ_Tot with Wilson et al. 2019 model | R: Data follow σ ∝ Σ^0.5 with scatter ~0.22 dex; h_H2~160-200 pc | F: Dispersion consistent with set by self-gravity pressure balance | **supported**
- H: Are the starbursts gas-rich and have ULIRG-like alpha_CO? | E: Dynamical mass MCMC for alpha_CO | R: alpha_CO 0.7 and 1.2; f_H2 ~0.1 | F: Low alpha_CO, not gas-rich | **supported**
- H: Does Σ_SFR correlate with P_grav? | E: Log-log emcee fit with PHANGS, ULIRG, DYNAMO data | R: N=0.78±0.01 | F: Star formation consistent with pressure-regulated | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Dynamical mass used to constrain alpha_CO; Wilson et al. model chosen because no stellar velocity dispersion is available  
  > "We choose Wilson et al. (2019)’s ISM pressure balance model because we lack of stellar velocity dispersion measurement for our sources." (4.1 What sets the molecular gas velocity dispersions?)
- How they decided it was enough: _not stated_
- Limitation (authors): alpha_CO–f_DM degeneracy and constant alpha_CO assumption limit dynamical interpretation  
  > "The dynamical interpretation is mainly limited by the degeneracy between α CO and f DM values" (4.4 Limitations of our dynamical mass approach)
- Limitation (authors): No reliable Paα flux calibration for HATLAS090750  
  > "we were unable to obtain a reliable flux calibration for its SINFONI observation" (3.1 Average ISM properties)
- Caveat (inferred, ours): Only two galaxies enter the pressure analysis; the P_grav fit is dominated by literature samples
- Caveat (inferred, ours): Constant M/L for Σ⋆ and Eq. 6 upper-limit pressure may bias results
- Caveat (inferred, ours): Fit uncertainties underestimated (authors admit)

## Reproducibility

- Data public (paper): ALMA project code given; public status not explicitly stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2015.1.01012.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Priors and MCMC settings
- Missing: Line-free channels and CASA version
- Missing: Literature comparison data tables (Wilson, Sun, Fisher) must be obtained
- Missing: SINFONI data reduction details
- Data volume (inferred): ~10-50 GB (three Band 3 12 m datasets plus SINFONI cubes)
- Score (inferred): 3/5, ALMA project is identified and imaging parameters are largely given, but MCMC settings, priors and several inputs are missing.
- Rediscovery candidate: no, Key results rely on SINFONI data, literature samples and under-specified MCMC modelling.

## Links

- Method: Swinbank et al. (2012) (Moment map construction)
- Method: Wilson et al. (2019) (Pressure balance model)
- Method: Stott et al. (2016) (Beam smearing correction)
- Companion: Villanueva et al. (2017) (VALES survey and earlier CO(1-0) data)
- Companion: Molina et al. (2019b) (Previous VALES kinematic analysis)
- Related: VALES
- Related: H-ATLAS
- Related: GAMA
- Related: PHANGS
- Related: DYNAMO
- Related: THINGS

## Checks

```json
{
 "quotes": 99,
 "quotes_ok": 99,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 11,
 "numeric_problems": 0,
 "fill": {
  "facts": 104,
  "stated": 75,
  "rate": 0.721
 },
 "evidence_ok": true
}
```
