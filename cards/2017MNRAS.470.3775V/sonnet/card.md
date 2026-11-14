# VALES I: the molecular gas content in star-forming dusty H-ATLAS galaxies up to z = 0.35

`2017MNRAS.470.3775V` | Monthly Notices of the Royal Astronomical Society 2017 | first author: Villanueva, V. | arXiv: 1705.09826 | DOI: 10.1093/mnras/stx1338

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type large_program_or_survey

## Science

- Fields: nearby_galaxies, high_z_galaxies
- Question: What is the molecular gas content, size, star-formation law and star-formation efficiency of dusty H-ATLAS star-forming galaxies at z<0.35, measured via ALMA CO(1-0)?  
  > "We use ALMA Band3 CO(1–0) observations to study the molecular gas content in a sample of 67 dusty normal star-forming galaxies selected from the Herschel Astrophysical Terahertz Large Area Survey (H-ATLAS)." (abstract)
- Target **67 H-ATLAS galaxies (equatorial GAMA fields), e.g. HATLASJ083601.5+002617**: coordinates Table 2 lists RA/Dec per source (equatorial GAMA fields)  
  > "The galaxies presented in this paper have been selected from the equatorial fields of the H-ATLAS survey" (2.1 H-ATLAS sample); "The optical counterparts to the Herschel-detected galaxies all have high-quality spectra from the Galaxy and Mass Assembly survey" (2.1 H-ATLAS sample); z/distance z = 0.02-0.35 (z_spec in Table 2)  
  > "The galaxies presented in this paper have been selected from the equatorial fields of the H-ATLAS survey" (2.1 H-ATLAS sample); "The optical counterparts to the Herschel-detected galaxies all have high-quality spectra from the Galaxy and Mass Assembly survey" (2.1 H-ATLAS sample); distance from GAMA optical spectroscopic redshifts; luminosity distances for H0=70, OmegaM=0.3, OmegaL=0.7  
  > "The galaxies presented in this paper have been selected from the equatorial fields of the H-ATLAS survey" (2.1 H-ATLAS sample); "The optical counterparts to the Herschel-detected galaxies all have high-quality spectra from the Galaxy and Mass Assembly survey" (2.1 H-ATLAS sample)

## Data provenance

- ALMA projects: 2012.1.01080.S, 2013.1.00530.S
- bands: Band 3 (Cycles 1 and 2)  
  > "ALMA Cycle-1 observations were taken in Band-3 between December 2013 and March 2014" (2.2 Observational strategy)
- frequencies and spectral setup: SPWs fixed manually with zero source redshift, optimised central frequency over ~7.5 GHz to maximise sources with CO(1-0) in range  
  > "We optimised the central frequency position of the SPWs (over ∼7.5 GHz) to maximise the number of sources with the CO(1–0) line redshifted into the ranges covered" (2.2 Observational strategy)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ~3''-4'' (most compact configuration)  
  > "resulting in image cubes with typical synthesised beams of 3” - 4”" (2.3 Data reduction)
- max recoverable scale: _not stated_
- sensitivity: Cycle-1 design 1.5 mJy/beam at 50 km/s; Cycle-2 design 2 mJy/beam at 30 km/s; achieved average rms 1.6 mJy/beam at 50 km/s  
  > "down to a root mean square (rms) of 1.5 mJy beam−1 at 50 km s−1 channel width" (2.2 Observational strategy); "We get an average rms level of 1.6 mJy beam−1 (at 50 km s−1) for both Cycle-1 and Cycle-2." (2.4.1 CO emission)
- time on source: ~3 to 9 minutes per source (Cycle-1)  
  > "spending approximately 3 to 9 minutes on-source in each source" (2.2 Observational strategy)
- observing dates: Dec 2013-Mar 2014 (Cycle 1), Jan 2015 (Cycle 2)  
  > "Cycle-2 observations were taken in Band-3 on January 2015" (2.2 Observational strategy)
- pi or archival as stated: P.I. E. Ibar  
  > "P.I. E. Ibar)." (2.1 H-ATLAS sample)
- Line: 12CO J=1-0 (115.271 GHz)
- Other facility **Herschel (H-ATLAS PACS/SPIRE), IRAS, WISE**: Far-IR photometry for IR luminosity/SFR and sample selection  
  > "constructed with photometry from IRAS, Wide-field Infrared Survey Explorer (WISE), and Herschel PACS and SPIRE instruments" (2.4.2 IR emission)
- Other facility **GAMA (+GALEX, SDSS, VISTA, WISE)**: _not stated_
- External data: Cycle-2 [CII] PACS spectroscopy and IR luminosities/stellar masses for comparison  
  > "in Cycle-2 we targeted 27 galaxies that have previous Herschel PACS [C ii] spectroscopy as shown by Ibar et al. (2015)" (2.1 H-ATLAS sample) [from Ibar et al. 2015]
- External data: HI mass estimator from photometry (Eqn 5)  
  > "we estimate these using Eqn. 4 from Zhang et al. 2009" (3.3 The Schmidt-Kennicutt relation) [from Zhang et al. 2009]
- External data: Literature CO samples (SMGs, BzK, local spirals, ULIRGs, etc.) combined in fits  
  > "Our sample is compared to other studies taken from the literature" (Figure 5 caption) [from Daddi et al. 2010a; Solomon et al. 1997; Leroy et al. 2008; Ivison et al. 2011; Saintonge et al. 2011; others]
- External data: MAGPHYS SED fits of GAMA (stellar masses)  
  > "in our present study we use the derived stellar masses and their uncertainties" (2.4.3 SED fitting) [from Driver et al. 2016; da Cunha et al. 2008]
- Simulation/model as data: Lagos et al. (2011) semi-analytic models of molecular gas fraction vs redshift (halo masses 1e11, 1e12) compared with data  
  > "semi-analytic prescriptions for galaxy formation and evolution of the molecular ISM computed by Lagos et al. (2011)" (3.5 Evolution of the molecular gas fraction)

## Processing

### Calibration

- pipeline or manual: Own structured pipeline in CASA based on the standard pipeline; phase calibrator re-scaled to average flux density and bootstrapped to targets when multiple observations  
  > "Based on the standard pipeline for data processing, we designed our own structured pipeline for calibration, concatenation and imaging." (2.3 Data reduction); "we re-calibrate the phase calibrator to an average flux density (usually variations are seen at ≲15%) and bootstrap this scaling to the targets" (2.3 Data reduction)
- casa version: CASA 4.4.0  
  > "(casa version 4.4.0)" (2.3 Data reduction)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Callisto, Mars, Ceres/Titan, Ganymede (per Table 1)  
  > "Ceres, Titan" (Table 1)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA clean  
  > "imaging was performed using the task clean at different spectral resolutions (from 20 to 100 km s−1 in steps of 10 km s−1)" (2.3 Data reduction)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "The final cubes were created using natural weighting" (2.3 Data reduction)
- uv taper: _not stated_
- cell size: _not stated_
- image size: 256x256 pixels, ~5 pixels per beam FWHM  
  > "choosing an image size of 256 × 256 pixels with roughly 5 pixels (semi-major axis) per synthesised beam full width half maximum" (2.3 Data reduction)
- masking: manual cleaning of CO line emission down to 3.0 sigma  
  > "manually cleaning the CO line emission down to a threshold of 3.0σ" (2.3 Data reduction)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: applied in final clean  
  > "this time applying a primary beam correction" (2.3 Data reduction)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: typical 3''-4''  
  > "typical synthesised beams of 3” - 4”" (2.3 Data reduction)
- final rms: 1.6 mJy/beam at 50 km/s  
  > "We get an average rms level of 1.6 mJy beam−1 (at 50 km s−1)" (2.4.1 CO emission)

### Inherited from earlier work

- IR SED fitting (modified blackbody with power-law high-frequency end) for L_IR  
  > "to obtain the total IR luminosity (Ibar et al. 2013, 2015)" (2.4.2 IR emission) [from Ibar et al. 2013, 2015]
- SFR calibration from L_IR  
  > "SFR(M⊙ yr−1) = 10−10 × L IR assuming a Chabrier (2003) Initial Mass Function (IMF)" (2.4.2 IR emission) [from Kennicutt 1998]
- CO luminosity formula  
  > "We compute the CO luminosity following Solomon & Vanden Bout (2005)" (3.2 Correlations between L IR and L′CO) [from Solomon & Vanden Bout 2005]
- Petrosian radius definition  
  > "using Eqn. (1) from Shimasaku et al. (2001)" (3.1 Morphological description) [from Shimasaku et al. 2001]

### Not stated but needed to reproduce (our reading)

- Which CASA task/parameters for flagging and the exact spectral window layout per execution block
- Clean mask definitions and sigma used for 3-sigma threshold (rms estimation region)
- Line-free channel definitions and whether continuum subtraction was done
- Details of the Monte-Carlo and linear regression method (fitter, weights, treatment of limits)
- Exact ALMA flux scale uncertainty
- How the Gaussian fits were bounded for spectra binning choice
- Detailed MAGPHYS settings and photometry used

## Analysis recipe

1. **Image cubes at optimal velocity resolution**: Clean cubes at 20-100 km/s, pick resolution maximising number of >5 sigma point-like detections; 100 km/s if undetected; then re-clean with primary beam correction  
  > "We sought the resolution that provided the highest number of non-cleaned point-like detections >5.0σ within the data-cube" (2.3 Data reduction)
   - software: CASA
   - parameter: natural weighting, 256x256 pixels, 3 sigma clean threshold  
  > "The final cubes were created using natural weighting" (2.3 Data reduction)
   - fitting: _not stated_
   - validation: _not stated_
2. **Fit line and measure integrated CO flux**: Single Gaussian fit to spectrum for centre/FWHM; collapse cube over ±1 FWHM; fit 2D Gaussian with gaussfit (irregular aperture for 7 sources); non-detections collapsed ±250 km/s  
  > "The velocity integrated CO flux densities ( S CO ∆v in units of Jy km s −1 ) were obtained by collapsing the data cubes between ± 1 × fwhm centred on the line" (2.4.1 CO emission)
   - software: CASA gaussfit
   - fitting: single Gaussian line profile; 2D Gaussian image-plane fit  
  > "The 2D intensity map is then fitted with a 2D-Gaussian for all detected sources using the task gaussfit within casa." (2.4.1 CO emission)
   - validation: Double-Gaussian test in 16 spectra: fluxes decrease ~5% on average, ~30% scatter; kept single Gaussian  
  > "we obtain that fluxes decrease by a ∼5% (on average), although with a large scatter (∼30%)." (2.4.1 CO emission)
3. **Derive IR luminosity, SFR, stellar mass**: Modified blackbody SED fit integrated 8-1000 um with Monte-Carlo errors (100 iterations); SFR = 1e-10 L_IR; stellar mass from MAGPHYS  
  > "randomly varying the broadband photometry within the observational uncertainties in a Monte-Carlo simulation (100 times)" (2.4.2 IR emission)
   - software: MAGPHYS
   - assumption: Chabrier IMF; 1.72 factor Salpeter to Chabrier  
  > "we assume a 1.72 factor to convert from a Salpeter to a Chabrier IMF" (2.4.2 IR emission)
   - fitting: modified blackbody + mid-IR power law; MAGPHYS Bayesian SED fit  
  > "using a modified black body that is forced to follow a power law at the high-frequency end of the spectrum." (2.4.2 IR emission)
   - validation: Compared with Ibar et al. 2015: scatter 0.15-0.2 dex; SFR offset factor 2  
  > "Both of these parameters demonstrate satisfactory agreement with a mean scatter of between 0.15 and 0.2 dex" (2.4.3 SED fitting)
4. **CO luminosity and molecular gas mass**: L'CO from Eqn 2; M_H2 = alpha_CO L'CO with morphology-dependent alpha_CO  
  > "We adopt αCO = 4.6 (K km s−1 pc2)−1 for the B– and D–dominated galaxies" (3.2 Correlations between L IR and L′CO)
   - assumption: alpha_CO = 4.6 for B/D galaxies, 0.8 for mergers/interacting  
  > "while αCO = 0.8 (K km s−1 pc2)−1 for mergers/interacting galaxies" (3.2 Correlations between L IR and L′CO)
   - fitting: _not stated_
   - validation: Discussed alpha_CO uncertainty (factor of six; metallicity-based variation factor of four)  
  > "assuming a different αCO can change M H2 by over a factor of six" (3.2 Correlations between L IR and L′CO)
5. **Size comparison and Schmidt-Kennicutt relation**: Deconvolved CO sizes via gaussfit; Petrosian radii ratio; surface densities over two-sided disk area 2 pi R_FWHM^2; HI estimated via Zhang+09; linear regressions  
  > "dividing the measured values by the area of a two-sided disk (2π R FWHM 2 )" (3.3 The Schmidt-Kennicutt relation)
   - software: CASA gaussfit
   - assumption: For CO-unresolved galaxies, CO radius = optical Petrosian radius / 1.6  
  > "we used the Petrosian optical radius divided by the mean R P,Opt /R P,CO = 1.6 ratio found for our galaxies" (3.3 The Schmidt-Kennicutt relation)
   - fitting: linear regression in log space; KS test for size ratio populations  
  > "We compute a linear regression (in log scale) to the" (3.2 Correlations between L IR and L ′ CO)
   - validation: _not stated_
6. **Star formation efficiency and gas fraction**: SFE = SFR/M_H2, empirical arctan parametrisation vs L_IR (Eqn 7); f_H2 = M_H2/(M_H2+M*) with M_H2/M* = tau x sSFR  
  > "We define the star formation efficiency as SFE = SFR/M H2" (3.4 Star formation efficiency)
   - fitting: Empirical function fitted to all z<0.4 samples, scatter 0.5 dex  
  > "This function has a scatter of σ = 0.5 dex." (3.4 Star formation efficiency)
   - validation: Compared with Bauermeister+13 and Lagos+11 models  
  > "the two black curves show semi-analytic prescriptions for galaxy formation and evolution of the molecular ISM computed by Lagos et al. (2011)," (3.5 Evolution of the molecular gas fraction)

## Software

- **CASA** 4.4.0: calibration, concatenation, imaging (clean), gaussfit  
  > "(casa version 4.4.0)" (2.3 Data reduction)
- **MAGPHYS** : Bayesian SED fitting for stellar masses  
  > "modelled with the Bayesian SED fitting code, MAGPHYS (da Cunha et al. 2008)" (2.4.3 SED fitting)
- **ALMA Observing Tool** : Scheduling block design with manually fixed SPWs  
  > "We modified the ‘by-default’ approach provided by the ALMA Observing Tool (OT)" (2.2 Observational strategy)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Spectrally detected galaxies (>5 sigma) | 49 of 67 | not stated | galaxies | 2 | We identify 49 galaxies (out of 67) with a >5σ peak line detection |
| Average rms | 1.6 | not stated | mJy/beam at 50 km/s | 1 | We get an average rms level of 1.6 mJy beam−1 (at 50 km s−1) |
| CO luminosity median | 0.3e10 | 0.1e10 | K km/s pc2 | 4 | with a median of (0.3 ± 0.1) × 1010 K km s−1 pc2 |
| L_IR vs L'CO slope (B/D detected) | 0.95 | 0.04 | dimensionless | 5 | log[L IR / L⊙] = (0.95 ± 0.04) × log L CO′ /[K km s−1 pc2] + (2.0 ± 0.4). |
| Optical-to-CO Petrosian radius ratio (21 resolved) | 1.6 | 0.5 (scatter) | dimensionless | 5 | the mean and scatter of the R P,Opt /R P,CO distribution are 1.6 ± 0.5 |
| Global Schmidt-Kennicutt slope (combined samples) | 1.26 | 0.02 | dimensionless | 5 | log[Σ SFR / (M⊙ yr−1 kpc−2)] = (1.26 ± 0.02) × log[Σ M H2 / (M⊙ pc−2)] − (3.6 ± 0.2). |
| Median SFE of transition-zone sources | 8.5 | 0.1 | Gyr^-1 | 6 | with a median of 8.5 ± 0.1 Gyr−1 |
| log M_H2 range B/D galaxies | 8.9-10.9 (median 10.31) | 0.1 | log Msun | 4 | median of log(M H2 / M⊙) = 10.31 ± 0.1 |

## Qualitative findings

- Molecular gas is more compact than the stellar component  
  > "the molecular gas is on average ∼0.6 times more compact than the stellar component" (abstract)
- Gas fraction increases rapidly with redshift within z<0.35, possibly affected by Herschel selection  
  > "This rapid evolution might be affected by the selection criteria" (4 Conclusions)

## Claim tuples

- H: Is molecular gas distributed more compactly than stars in these galaxies? | E: Compared Petrosian radii in r-band and CO for 21 resolved galaxies | R: R_P,Opt/R_P,CO = 1.6 ± 0.5 | F: CO is more concentrated than stars | **supported**
- H: Do galaxies fill an intermediate efficiency regime between disks and starbursts? | E: SFE vs L_IR with literature samples | R: Many sources with SFE 4.3-11.7 Gyr^-1 in transition zone | F: Continuous transition of SFE with L_IR rather than bimodality | **partially**
- H: Does gas content evolve rapidly with redshift at z<0.35? | E: Gas fraction vs redshift compared to models | R: f_H2 increases with redshift, faster than semi-analytic predictions | F: Rapid evolution, possibly selection effect | **partially**

## Reasoning

- Why this data: Single-pointing Band-3 CO(1-0) for dusty Herschel-selected galaxies at 0.02<z<0.35 avoids mosaics and high-J conversions  
  > "the redshift range puts galaxies far enough so galaxies can be imaged with a single ALMA pointing in Band-3" (2.1 H-ATLAS sample)
- Why this method: _not stated_
- Alternative: Double-Gaussian line fits rejected in favour of single Gaussian for collapsing cubes  
  > "We decide to stick to the single Gaussian fit to estimate the fwhm to collapse the cubes." (2.4.1 CO emission)
- How they decided it was enough: _not stated_
- Limitation (authors): alpha_CO is the major uncertainty in gas masses  
  > "The major uncertainty in our molecular gas mass estimates originates from the assumption of the αCO conversion factor." (3.2 Correlations between L IR and L′CO)
- Caveat (inferred, ours): alpha_CO assigned by visual morphology can create artificial bimodality
- Caveat (inferred, ours): HI masses from a photometric estimator with 0.31 dex scatter
- Caveat (inferred, ours): Unresolved CO sizes assumed from optical radius / 1.6
- Caveat (inferred, ours): Fits combine samples at different epochs with different alpha_CO
- Caveat (inferred, ours): Redshift evolution of gas fraction confounded by Herschel selection

## Reproducibility

- Data public (paper): ALMA programs identified by code and acknowledged as ADS/JAO.ALMA data  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA 2012.1.01080.S & ADS/JAO.ALMA 2013.1.00530.S." (ACKNOWLEDGEMENTS)
- Products in archive: _not stated_
- Missing: Custom pipeline scripts not released
- Missing: Clean mask and rms details
- Missing: Regression method details
- Data volume (inferred): ~50-150 GB raw for 67 short Band-3 observations over two programs
- Score (inferred): 3/5, Public data and a fair description of methods and Table 2 values, but custom pipeline and several imaging/fit details are missing.
- Rediscovery candidate: yes, Archival data, simple per-source recipe (cube, Gaussian fit, flux, L'CO), numeric results in Table 2.

## Links

- Method: Ibar et al. 2015 (IR SED fitting and Cycle-2 sample [CII] data)
- Method: da Cunha et al. 2008 (MAGPHYS SED fitting)
- Companion: Molina et al. in prep. (Kinematic analysis of VALES spectra)
- Companion: Hughes et al. 2016 (Physical conditions of ISM in VALES galaxies)
- Related: H-ATLAS
- Related: GAMA

## Checks

```json
{
 "quotes": 78,
 "quotes_ok": 78,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 83,
  "stated": 58,
  "rate": 0.699
 },
 "evidence_ok": true
}
```
