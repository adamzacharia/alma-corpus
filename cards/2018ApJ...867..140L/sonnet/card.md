# Resolving Star Formation on Subkiloparsec Scales in the High-redshift Galaxy SDP.11 Using Gravitational Lensing

`2018ApJ...867..140L` | The Astrophysical Journal 2018 | first author: Lamarche, C. | arXiv: 1809.09630 | DOI: 10.3847/1538-4357/aae394

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies, milky_way_ism
- Question: What are the ISM, star formation and stellar population properties of the lensed galaxy SDP.11, and how does differential lensing affect its [C ii] line profile and [C ii]/FIR variation on sub-kpc scales?  
  > "we study the ISM and star forming conditions within H-ATLAS J091043.1-000321 (hereafter SDP.11), a strongly-lensed, Ultra Luminous Infrared Galaxy- (ULIRG-) like source, at z = 1.7830" (Introduction)
- Target **SDP.11 (H-ATLAS J091043.1-000321)**: coordinates _not stated_; z/distance z = 1.7830; D_L = 13.65 Gpc  
  > "strongly-lensed star-forming galaxy H-ATLAS J091043.1-000321 (SDP.11), at z = 1.7830" (abstract); "1" = 8.54 kpc, D$_A$ = 1.76 Gpc, and D$_L$ = 13.65 Gpc." (Introduction); distance from [C ii] ALMA line fit (this paper), flat LCDM H0=71  
  > "strongly-lensed star-forming galaxy H-ATLAS J091043.1-000321 (SDP.11), at z = 1.7830" (abstract); "1" = 8.54 kpc, D$_A$ = 1.76 Gpc, and D$_L$ = 13.65 Gpc." (Introduction)

## Data provenance

- ALMA projects: 2015.1.01362.S
- bands: Band 9 (683 GHz)  
  > "Observing at 683 GHz in this array configuration" (2.1 ALMA)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: ~6.5 GHz  
  > "for a total continuum bandwidth of $\sim$ 6.5 GHz" (2.1 ALMA)
- arrays: _not stated_
- configurations: C40-4, 42 antennas  
  > "with the array in the C40-4 configuration, using 42 antennas" (2.1 ALMA)
- baselines: 15 to 920 m  
  > "with baselines ranging from 15 to 920 m" (2.1 ALMA)
- angular resolution: 0.20 x 0.16 arcsec (line)  
  > "achieving a synthesized beam of size 0$\ensuremath{''}$20 x 0$\ensuremath{''}$16" (2.1 ALMA)
- max recoverable scale: ~1.3 arcsec  
  > "the interferometer is sensitive to a maximum recoverable scale of $\sim$ 1$\ensuremath{''}$3" (2.1 ALMA)
- sensitivity: ~4.5 mJy/beam per 50 km/s channel; continuum 0.72 mJy/beam  
  > "The RMS sensitivity is $\sim$ 4.5 mJy beam$^{-1}$ in each 50 km s$^{-1}$ channel." (2.1 ALMA)
- time on source: 12.6 minutes  
  > "The total on-source integration time for these observations was 12.6 minutes." (2.1 ALMA)
- observing dates: November 16, 2016  
  > "The observations were conducted on November 16, 2016" (2.1 ALMA)
- pi or archival as stated: _not stated_
- Line: [C II] 2P3/2-2P1/2 (158 um (157.7 um))
- Other facility **Herschel/PACS**: [O III] 52, [N III] 57, [O I] 63 um etc. line fluxes  
  > "fine-structure lines were all observed in SDP.11 using the Photodetector Array Camera and Spectrometer (PACS)" (2.2 Herschel/PACS)
- Other facility **Herschel/SPIRE**: [O III] 88, [N II] 122, [C II] 158 um fluxes  
  > "were all observed in SDP.11 using the Spectral and Photometric Imaging Receiver (SPIRE)" (2.3 Herschel/SPIRE)
- Other facility **VLA**: 6, 15, 33 GHz radio continuum (ZINGRS and archival) plus FIRST 1.43 GHz  
  > "Here we use the 6 and 15 GHz radio fluxes from the ZINGRS radio survey (Project IDs: 16B-331 and 16A-375, respectively)" (3.3.3 Gas Phase Metallicity)
- External data: FIR luminosity, dust temperature 41 K, beta 1.5, average magnification 10.9  
  > "modeling the FIR SED of SDP.11 with a modified blackbody function, assuming a constant dust temperature of 41 K across the source, and a dust emissivity index ($\beta$) of 1.5 (cite: Bussmann2013)" (3.4.1 [C ii]/FIR Ratio) [from (cite: Bussmann2013)]
- External data: CO(4-3) measurements for molecular gas mass  
  > "using the measurements from (cite: Oteo2017)" (3.4.3 Molecular Gas) [from (cite: Oteo2017)]
- External data: SPIRE 500 um photometry 232 +/- 8 mJy  
  > "SPIRE photometry measures 232 $\pm$ 8 mJy at 500 $\mu$m (cite: Bussmann2013)" (3.1 Line and Continuum Fluxes) [from (cite: Bussmann2013)]
- External data: Stellar mass ~1.9e11 Msun  
  > "the reported value of the stellar mass within SDP.11, $\sim$ 1.9 $\times$ 10$^{11}$ $M_{\odot}$ (cite: Negrello2014)" (3.5 Lens Modeling) [from (cite: Negrello2014)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: CASA 4.7.2  
  > "The data were reduced, imaged, and cleaned using the Common Astronomy Software Application (CASA)[^3], version 4.7.2." (2.1 ALMA)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: natural weighting, 50 km/s channels  
  > "The \[C ii\] data were imaged using 50 km s$^{-1}$ spectral channels, and natural weighting" (2.1 ALMA)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: applied to moment-0 maps; 3 sigma masks from flat-noise maps  
  > "Creating a moment-zero, primary-beam corrected, map by collapsing the spectral cube along the velocity axis" (3.1 Line and Continuum Fluxes)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.20 x 0.16 arcsec (line); 0.20 x 0.15 arcsec (continuum)  
  > "yields a beam size of 0$\ensuremath{''}$20 x 0$\ensuremath{''}$15 and an RMS sensitivity of 0.72 mJy beam$^{-1}$" (2.1 ALMA)
- final rms: _not stated_

### Inherited from earlier work

- Lens modeling code and procedure  
  > "For a more complete description of the code, see (cite: Bussmann2015)." (3.5 Lens Modeling) [from (cite: Bussmann2015)]
- PDR mass formula  
  > "we can estimate the PDR mass following (cite: Hailey-Dunsheath2010)" (3.4.2 PDR Mass) [from (cite: Hailey-Dunsheath2010)]
- Minimum ionized gas mass formula  
  > "Following (cite: Ferkinhoff2010), we can estimate the minimum ionized gas mass" (3.2.2 Ionized Gas Mass) [from (cite: Ferkinhoff2010)]
- Radio thermal/nonthermal decomposition, nu0 = 1 GHz  
  > "Adopting a $\nu_{0,r}$ value of 1 GHz, as in (cite: Klein2018)" (3.3.3 Gas Phase Metallicity) [from (cite: Klein2018)]

### Not stated but needed to reproduce (our reading)

- Line-free channels and continuum subtraction method
- CLEAN threshold, mask, cell and image size
- Whether archive or manual calibration was used; flux calibrator model and Band 9 flux uncertainty
- uvmcmcfit priors, chain settings and uv-data averaging
- Line fit details for the dual Gaussian
- FIR-luminosity-per-pixel conversion details and SFR-surface-density fit method
- Pointing/phase center used and PDR Toolbox inputs

## Analysis recipe

1. **Image [C ii] cube and continuum**: CASA imaging with natural weighting, 50 km/s channels; continuum from all line-free channels  
  > "A continuum image was created by combining all non-line spectral channels present in the measurement set" (2.1 ALMA)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Measure integrated line and continuum fluxes**: Sum pixels >3 sigma in flat-noise maps applied to primary-beam-corrected moment-0 map; dual Gaussian fit to the spectrum  
  > "We fit the source-integrated spectrum with a dual Gaussian line profile, one for each velocity component." (3.1 Line and Continuum Fluxes)
   - software: CASA
   - fitting: dual Gaussian  
  > "We fit the source-integrated spectrum with a dual Gaussian line profile, one for each velocity component." (Results and Discussion, Line and Continuum Fluxes)
   - validation: Compared with ZEUS-2, SPIRE and SEPIA fluxes  
  > "While the \[C ii\] 158 $\ensuremath{\mu}m$ flux which we measure with ALMA is consistent with our previous line flux measurement from APEX/ZEUS-2" (3.1 Line and Continuum Fluxes)
3. **Compute [C II]/FIR map and Sigma_SFR relation**: Modified blackbody scaling of 158 um continuum to L_FIR per pixel; power-law fit of ratio vs Sigma_SFR on beam-independent pixels  
  > "we sample pixels from the map such that no selected pixel is within one beam width of any other selected pixel" (3.4.1 [C ii]/FIR Ratio)
   - assumption: T_dust = 41 K, beta = 1.5, bolometric factor 1.91, Kennicutt 1998 SFR  
  > "assuming a constant dust temperature of 41 K across the source, and a dust emissivity index ($\beta$) of 1.5" (3.4.1 [C ii]/FIR Ratio)
   - fitting: power law  
  > "Fitting a power-law to the plot of L$_{[C\,\textrm{\sc ii}]}$/L$_{FIR}$ vs. $\Sigma_{SFR}$, we find a power-law index of -0.7" (Results and Discussion, PDRs, [C ii]/FIR Ratio)
   - validation: _not stated_
4. **Lens modeling of red and blue [C ii] components**: uvmcmcfit in uv-plane; SIE lens, elliptical Gaussian source; red fit first, blue fit with lens fixed  
  > "This code models the foreground lensing galaxy using a single isothermal ellipsoid (SIE) profile" (3.5 Lens Modeling)
   - software: uvmcmcfit
   - parameter: moment-0 maps collapsed over 300 km/s centered at +/-155 km/s  
  > "Each moment-zero map is collapsed over 300 km s$^{-1}$ in the velocity dimension." (3.5 Lens Modeling)
   - assumption: Lens within 0.2 arcsec of HST optical centroid; no external shear  
  > "requiring that the foreground lensing galaxy be located within $\pm$ 0$\ensuremath{''}$2 of the centroid of the known optical source" (Results and Discussion, Lens Modeling)
   - fitting: MCMC  
  > "It then uses Markov Chain Monte Carlo (MCMC) to sample the parameter space" (3.5 Lens Modeling)
   - validation: Compared with earlier lens models  
  > "finding that the position of the lens is co-spatial with a known optical source, in agreement with previous lens modeling" (Conclusions)
5. **Derive masses and depletion time**: PDR mass formula, L'CO(4-3) with alpha_CO, dynamical mass for rotating disk  
  > "assuming an SMG CO excitation of r$_{43/10}$ = 0.41 (cite: Bothwell2013), and taking a ULIRG value of $\alpha_{CO}$ = 0.8" (3.4.3 Molecular Gas)
   - software: PDR Toolbox
   - assumption: mu = 10.9; inclination average <v_rot> = pi/2 v_obs  
  > "estimated from the observed velocity by correcting for the average inclination angle, $\langle$v$_{rot}$$\rangle$ $\sim$ $\frac{\pi}{2}$ v$_{obs}$" (Results and Discussion, Lens Modeling)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.7.2: ALMA reduction, imaging and cleaning  
  > "The data were reduced, imaged, and cleaned using the Common Astronomy Software Application (CASA)[^3], version 4.7.2." (2.1 ALMA)
- **uvmcmcfit** : uv-plane gravitational lens modeling  
  > "we perform gravitational lens modeling on the ALMA \[C ii\] 158 $\ensuremath{\mu}m$ line observations of SDP.11 using the code uvmcmcfit" (3.5 Lens Modeling)
- **HIPE** 15.0.1: Herschel PACS and SPIRE processing and SPIRE line fitting  
  > "The raw data were processed using the Herschel Interactive Pipeline Environment (HIPE) (cite: Ott2010) version 15.0.1." (2.2 Herschel/PACS)
- **PDR Toolbox** : PDR G0, density and temperature  
  > "utilizing the PDR Toolbox (cite: Pound2008; Kaufman2006)" (3.4.2 PDR Mass)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| [C ii] integrated flux | 260 | 9 | Jy km/s | 2 | we calculate a source-integrated \[C ii\] 158 $\ensuremath{\mu}m$ flux of 260 $\pm$ 9 Jy km s$^{-1}$ |
| 158 um rest-frame continuum flux density | 189 | 4 | mJy | 2 | we obtain a source-integrated specific flux of 189 $\pm$ 4 mJy at 158 $\mu$m rest-frame |
| [C ii] redshift | 1.7830 | 0.0002 | dimensionless | 2 | We suggest a refined redshift for the source of 1.7830 $\pm$ 0.0002 |
| Magnification red component | 11.5 | 0.2 | dimensionless | 4 | varying from $\mu$ = 11.5 $\pm$ 0.2 for the red component of the line to $\mu$ = 6.2 $\pm$ 0.1 for the blue component |
| Magnification blue component | 6.2 | 0.1 | dimensionless | 4 | varying from $\mu$ = 11.5 $\pm$ 0.2 for the red component of the line to $\mu$ = 6.2 $\pm$ 0.1 for the blue component |
| Power-law index of [C II]/FIR vs Sigma_SFR | -0.7 | not stated | dimensionless | 3 | we find a power-law index of -0.7 |
| PDR gas mass | 3.7e9 | not stated | Msun | 5 | We calculate a PDR gas mass of $\sim$ 3.7 $\times$ 10$^{9}$ $M_{\odot}$ |
| Dynamical mass | 2.4e10 | not stated | Msun | 5 | We obtain a dynamical mass of $\sim$ 2.4 $\times$ 10$^{10}$ $M_{\odot}$. |
| Molecular gas depletion time | ~16 | not stated | Myr | 5 | this molecular gas reservoir will be depleted within $\sim$ 16 Myrs |

## Qualitative findings

- [C ii] resolves into two spatially offset Einstein rings in red and blue velocity components, separated by ~310 km/s  
  > "The line has two clearly defined velocity components, separated by $\sim$ 310 km s$^{-1}$" (3.1 Line and Continuum Fluxes)

## Claim tuples

- H: Is SDP.11 a compact merger-driven starburst like local ULIRGs? | E: Mapped [C ii]/FIR and did lens modeling of red/blue components | R: [C ii]/FIR as low as ~0.02% at continuum peak, but symmetric profile after differential lensing correction | F: Starburst may be spread over a ~3.5 kpc rotating disk rather than a major merger, though a merger cannot be excluded | **partially**
- H: Does differential lensing affect the observed line profile? | E: uvmcmcfit fits to red and blue components | R: mu = 11.5 vs 6.2 | F: Correction yields a more symmetric line | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Lens model lacks external shear and mass-profile variation; ALMA may resolve out flux  
  > "At present, UVMCMCFIT has neither the ability to include external shear, nor the ability to vary the mass-density profile" (3.5 Lens Modeling)
- Caveat (inferred, ours): Single short Band 9 observation with max recoverable scale below the ring size; resolved-out flux affects fluxes and ratios
- Caveat (inferred, ours): Ratio maps limited to ~40% of the [C II] region with continuum detection
- Caveat (inferred, ours): Uncertainties on ratios and masses depend on assumed T_dust, beta, alpha_CO

## Reproducibility

- Data public (paper): ALMA project cited in acknowledgments; Herschel OBSIDs given  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA$\#$2015.1.01362.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Imaging parameters (cell, size, cleaning threshold)
- Missing: uvmcmcfit configuration and priors
- Missing: Per-pixel L_FIR computation details
- Data volume (inferred): ~5-20 GB
- Score (inferred): 5/5, Single public dataset and mostly clear measurements, but imaging and lens-fit settings are sparse.
- Rediscovery candidate: no, Imaging and lens fitting settings are incomplete and results depend on Herschel and literature inputs.

## Links

- Method: (cite: Bussmann2015) (uvmcmcfit lens modeling code)
- Method: (cite: Hailey-Dunsheath2010) (PDR mass formula)
- Companion: (cite: Bussmann2013) (earlier lens model and FIR properties of SDP.11)
- Companion: (cite: Zhang2018) (SPIRE spectra first presented)
- Related: H-ATLAS
- Related: ZINGRS

## Checks

```json
{
 "quotes": 64,
 "quotes_ok": 64,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 9,
 "numeric_problems": 0,
 "fill": {
  "facts": 79,
  "stated": 48,
  "rate": 0.608
 },
 "evidence_ok": true
}
```
