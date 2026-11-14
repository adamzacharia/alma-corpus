# Concurrent Starbursts in Molecular Gas Disks within a Pair of Colliding Galaxies at z = 1.52

`2018ApJ...868...75S` | The Astrophysical Journal 2018 | first author: Silverman, J. D. | arXiv: 1810.01595 | DOI: 10.3847/1538-4357/aae64b

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies
- Question: What are the molecular gas, dynamics, alpha_CO, gas-to-dust ratio and star formation conditions of the two interacting galaxies in the z=1.52 starburst PACS-787?  
  > "we assess the physical characteristics of each galaxy through a determination of α CO (and the gasto-dust ratio) based on a dynamical mass estimate of PACS-787." (1. INTRODUCTION)
- Target **PACS-787**: coordinates East 10:02:27.995 +02:10:04.56; West 10:02:27.927 +02:10:04.61 (Table 2)  
  > "PACS787; z spec = 1.5234;" (1. INTRODUCTION); "the projected separation of the two galaxies is 1.02” that corresponds to 8.65 kpc at z = 1.5249." (4.1 Molecular line emission (CO 5-4)); z/distance z_spec = 1.5234 (East 1.5256, West 1.5240 from CO)  
  > "PACS787; z spec = 1.5234;" (1. INTRODUCTION); "the projected separation of the two galaxies is 1.02” that corresponds to 8.65 kpc at z = 1.5249." (4.1 Molecular line emission (CO 5-4)); distance from Subaru/FMOS Halpha and [NII] spectroscopy; CO centroid redshifts  
  > "PACS787; z spec = 1.5234;" (1. INTRODUCTION); "the projected separation of the two galaxies is 1.02” that corresponds to 8.65 kpc at z = 1.5249." (4.1 Molecular line emission (CO 5-4))

## Data provenance

- ALMA projects: 2015.1.00861.S, 2016.1.01426.S, 2012.1.00952.S
- bands: Band 3 (CO 2-1) and Band 6 (CO 5-4, 1.28 mm continuum)  
  > "to detect CO(2 - 1) at 91.31 GHz (Band 3)" (3. ALMA OBSERVATIONS AND DATA ANALYSIS)
- frequencies and spectral setup: Four spectral windows in Band 6 (226.01, 228.43, 241.01, 244.01 GHz); CO(5-4) in the 228.43 GHz window  
  > "226.01, **228.43** [a] 2.0, 1.86 15.62, 3.91 19.73" (Table 1)
- continuum bandwidth: _not stated_
- arrays: 12m, 43 antennas (high res); 42 antennas (compact)  
  > "PACS-787 was observed on November 7, 2016 with 43 12m antennas" (3.1 High resolution)
- configurations: _not stated_
- baselines: 18.6 m to 1.11 km (high-res); max 278.9 m (compact)  
  > "The antenna baselines spanned a range of 18.6 m to 1.11 km" (3.1 High resolution)
- angular resolution: 0.38" x 0.34" (high res Band 6)  
  > "beam size of 0.38 ′′ × 0.34 ′′" (3.1 High resolution)
- max recoverable scale: 2.98"  
  > "a maximum recoverable scale of 2.98 ′′" (3.1 High resolution)
- sensitivity: _not stated_
- time on source: 19.73 min (high res), 10.2 min (compact)  
  > "The onsource integration time was 19.73 minutes." (3.1 High resolution)
- observing dates: 2016 Mar 04 (Band 3), 2016 Nov 07, 2017 Mar 18 (Band 6)  
  > "PACS-787 was reobserved on March 18, 2017 with 42 antennas in a compact configuration" (3.1 High resolution)
- pi or archival as stated: Own program (PI J. Silverman)  
  > "Proposal #2016.1.01426.S; PI J. Silverman" (3.1 High resolution)
- Line: CO 5-4 (576.27 GHz)
- Line: CO 2-1 (not stated)
- Other facility **HST ACS/WFC3**: F814W and F140W imaging showing tidal features and stellar bridge  
  > "WFC3/F140W (single-orbit; 40 minute exposure on-source)" (2. PACS-787: AN EXTREME OUTLIER FROM THE SF MS)
- Other facility **Herschel/Spitzer/Subaru HSC/UltraVISTA photometry**: SED photometry for stellar mass, dust mass and SFR  
  > "continuum emission from PACS-787 is detected by Spitzer/MIPS (24 µ m), Herschel/PACS (100 and 160 µ m)" (2.2 Star formation rate (SFR))
- Other facility **VLA 3 GHz**: radio continuum for SFR check  
  > "we measure the SFR from the radio flux at 3 GHz (Smolˇci´c et al. 2017)" (6.2)
- External data: Hydrodynamic merger simulations used to calibrate dynamical mass  
  > "We use available simulations of gas-rich galaxy mergers (Fensch et al. 2017)" (5.2) [from Fensch et al. 2017]
- External data: CO(2-1)/CO(1-0) luminosity ratio 0.85  
  > "L ′ CO 2 − 1 /L ′ CO 1 − 0 = 0.85; Daddi et al. 2015" (5.5) [from Daddi et al. 2015]
- Simulation/model as data: Fensch et al. 2017 mergers: 15 snapshots with SFR enhancement >3x, 10 random projections each, CO(5-4) mock emission  
  > "we select 15 snapshots where the merger has triggered a substantial SFR enhancement ( > 3 × ) and generate 10 random projections for each snapshot." (5.2)

## Processing

### Calibration

- pipeline or manual: standard pipeline in CASA  
  > "to carry out the processing of the ALMA raw data though the standard pipeline" (3.2)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J1058+0133 (bandpass, flux, pointing); J0948+0022 (phase)  
  > "J1058+0133 (bandpass, flux, pointing), and J0948+0022 (phase)" (3.1 High resolution)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA clean; immoments to collapse cube  
  > "we then generate images using the task ‘clean’ with a natural weighting scheme of the antenna pattern." (3.2)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "a natural weighting scheme of the antenna pattern" (3.2)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: Continuum images use full spectral range without channels with CO emission  
  > "Continuum images make use of the full spectral range without channels having CO emission." (3.2)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: Compact and extended visibilities merged only for diffuse CO analysis  
  > "We merged the visibilities from the compact and extended ALMA configurations (Band 6), only for this exercise" (7. DIFFUSE CO EMISSION)
- smoothing: _not stated_
- final beam: 0.38"x0.34" high-res  
  > "beam size of 0.38 ′′ × 0.34 ′′" (3.1 High resolution)
- final rms: _not stated_

### Inherited from earlier work

- Stellar mass method as in COSMOS catalog  
  > "sure the stellar mass as done in Laigle et al. (2016)." (2.1. Stellar mass (M stellar)) [from Laigle et al. (2016)]
- Dust SED fitting approach  
  > "Following Magdis et al. (2012a), we simultaneously fit the broadband SED using a model with five components" (2.2) [from Magdis et al. (2012a)]
- CO(2-1) luminosity of PACS-787 taken from earlier paper  
  > "from our estimate of the CO(2 - 1) luminosity, as reported in Silverman et al. (2018)" (5.5) [from Silverman et al. 2018]

### Not stated but needed to reproduce (our reading)

- clean parameters (cell size, image size, mask, threshold, niter)
- CASA version
- line-free channels used for continuum
- how rms and velocity ranges chosen
- Band 3 and 2012.1.00952.S data usage
- flux calibrator flux density values
- uvmodelfit/GILDAS settings
- priors for the realizations of Mdyn beyond Gaussian errors
- how Mdyn was combined with fc distribution

## Analysis recipe

1. **Measure stellar mass**: GALFIT photometry of components, SED fitting with BC03 and constant SFH  
  > "we use GALFIT (Peng et al. 2010) to measure fluxes in seven optical bands" (2.1)
   - software: GALFIT, Hyperzmass
   - assumption: Chabrier IMF, constant SFH  
  > "implementing a constant star formation history (SFH)" (2.1)
   - fitting: chi2 minimisation, 68% interval  
  > "accounted for in the 68% confidence interval based on the χ [2] statistic" (2.1)
   - validation: Summed SEDs give mid-IR fluxes within 10% of Spitzer/IRAC  
  > "within 10% of the measured Spitzer /IRAC fluxes" (2.1)
2. **Dust mass, LIR and SFR**: Draine & Li dust model fit to MIR-FIR SED, SFR from Kennicutt & Evans  
  > "the total FIR luminosity is log L = 12.83 ± 0.04 (units of L ⊙ )" (2.2)
   - parameter: alpha fixed at 2; Umax = 10^6  
  > "An index α, fixed at a value of 2" (2.2)
   - assumption: no energy balance required  
  > "We do not require energy balance between the FIR and absorbed UV emission" (2.2)
   - fitting: chi2 minimisation; Monte Carlo for Mdust error  
  > "Monte Carlo simulations are used to assess the error on M dust" (2.2)
   - validation: Agrees with radio SFR  
  > "This rate is in good agreement with that derived from the radio emission (3 and 5 GHz)" (2.2)
3. **Measure CO and continuum properties of each galaxy**: imfit elliptical Gaussian on moment-0 images; double Gaussian line fit for FWHM; offsets of red/blue maps  
  > "fitting the spatial distribution of the emission using the CASA tool ‘imfit’ with an elliptical Gaussian model" (4.1)
   - software: CASA, GILDAS
   - fitting: double Gaussian with single fixed width per galaxy  
  > "a double Gaussian model of a single fixed velocity width for each component" (4.2)
   - validation: Confirmed with GILDAS and uvmodelfit  
  > "Measurements are confirmed using a separate analysis package, GILDAS, and the task ‘uvmodelfit’." (3.2)
4. **Calibrate dynamical mass correction with simulations**: Mock CO(5-4) from Fensch simulations; compare Eq.2 Mdyn with true mass; use mean ratio and 0.2 dex dispersion as fc  
  > "We find that our dynamical mass estimates are low by a factor of 2.0 (Figure 10)." (5.2)
   - parameter: inclination limited to 20-70 deg  
  > "inclined by less than 20 ◦ or more than 70 ◦" (5.2)
   - fitting: _not stated_
   - validation: _not stated_
5. **Dynamical mass, gas mass, alpha_CO, G/D**: Thin-disk Mdyn (Neri 2001) with fc and inclination from axis ratio; 10k realizations; Mgas = 2[Mdyn - Mdm] - Mstellar; alpha_CO=Mgas/L'CO(1-0)  
  > "We calculate the dynamical mass within a half-light radius, as given in Equation 2, by generating 10k realizations that incorporate all sources of uncertainty" (5.3. Likelihood distribution of the dynamical mass)
   - assumption: Mdm = 0.2 x Mdyn with dispersion 0.05  
  > "We assume that the dark matter mass ( M dm ) is equal to 0.2 × M dyn with a dispersion of 0.05" (5.4)
   - fitting: Monte Carlo, Gaussian errors  
  > "while assuming Gaussian distributions for each parameter with errors" (5.3. Likelihood distribution of the dynamical mass)
   - validation: 14% unphysical trials noted  
  > "a non-negligible fraction (14%) of cases that are unphysical" (5.4)
6. **Per-galaxy gas, SFR, depletion time**: Split total gas by CO(5-4) ratio and SFR by 1.28mm continuum ratio; tau=Mgas/SFR  
  > "under the assumption that the ratio (1.10 ± 0.08) of the continuum emission at λ rest = 505.5 µ m, detected by ALMA, reflects the ratio in SFR." (6.2)
   - assumption: same excitation and same dust SED for both galaxies  
  > "This assumes that the excitation states of the two galaxies are the same." (6.1)
   - fitting: _not stated_
   - validation: Radio 3 GHz SFR and CO(5-4)-SFR checks  
  > "As an independent check, we measure the SFR from the radio flux at 3 GHz" (6.2)
7. **Diffuse emission**: Multi-component elliptical Gaussian visibility fits on merged data  
  > "A multi-component fit was performed on the CO(5 - 4) visibility data with an elliptical Gaussian at the position of each of the two galaxies." (7. DIFFUSE CO EMISSION)
   - software: CASA
   - fitting: 2- and 3-component Gaussian fits  
  > "With evidence for an extended component, we re-fit the data allowing for a third Gaussian component and inspected the residuals after subtracting the two galaxies." (7. DIFFUSE CO EMISSION)
   - validation: Also seen in continuum-only visibilities  
  > "further supported by the existence of an extended component with the continuum-only visibilities (Figure 15)" (7. DIFFUSE CO EMISSION)

## Software

- **CASA** : pipeline, clean, immoments, imfit  
  > "We use Common Astronomy Software Applications (CASA) to carry out the processing of the ALMA raw data" (3.2)
- **GILDAS** : confirm measurements  
  > "Measurements are confirmed using a separate analysis package, GILDAS" (3.2)
- **GALFIT** : component photometry  
  > "we use GALFIT (Peng et al. 2010)" (2.1)
- **Hyperzmass** : stellar mass SED fit  
  > "The code Hyperzmass (i.e., a modified version of Hyperz" (2.1)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| SFR total | 991 | +96/-87 | Msun/yr | 2 | total SFR = 991 −+96 87 M ⊙ yr −1 |
| Dust mass log | 9.2 | 0.06 | log Msun | 2 | log M dust = 9.2 ± 0.06 M ⊙ |
| Median dynamical mass (sum) | 1.1e11 | +0.6/-0.4 | Msun | 5 | we indicate the median dynamical mass ( _M_ _dyn_ ( _r_ _<_ _r_ 1 _/_ 2 ) = 1 _._ 1 [+0] _−_ 0 _[.]_ _._ [6] 4 _[×]_ [ 10] [11] [M] _[⊙]_ [)] |
| Total gas mass | 7.5e10 | +10/-7.3 e10 | Msun | 5 | M gas = 7.5 [+10] −7.1.3 × 10 10 M ⊙ |
| alpha_CO median | 1.3 | 84% of trials <3.1 | Msun (K km/s pc2)^-1 | 5 | we find the median α CO to be 1.3 M ⊙ (K km s − 1 pc 2 ) − 1 |
| gas-to-dust ratio | 35 | 84% of trials <83 | dimensionless | 5 | the likely value of the gas-to-dust (G/D) ratio to be 35 based on the median of 10k trials |
| Mgas East/West | 4.4e10 / 3.2e10 | 0.6e10 / 0.4e10 | Msun | 6 | 4.4 ± 0.6 × 10 10 M ⊙ (East) and 3.2 ± 0.4 × 10 10 |
| Depletion time East/West | 85 / 67 | 14 / 10 | Myr | 6 | time scale of 85 ± 14 (67 ± 10) Myrs |
| Projected separation | 8.65 | not stated | kpc | 3 | the projected separation of the two galaxies is 1.02” that corresponds to 8.65 kpc |
| Diffuse fraction of flux | ≈20 | not stated | % | 7 | appears to contain ≈ 20% of the total flux of the system |

## Qualitative findings

- Two compact interacting, likely counter-rotating molecular disks plus diffuse CO/continuum bridge co-spatial with stellar emission  
  > "the interaction of likely counter-rotating molecular disks that may accelerate the loss of angular momentum." (abstract)

## Claim tuples

- H: Is PACS-787 a pre-coalescence merger with two disks? | E: 0.3" ALMA CO(5-4) and continuum imaging plus HST | R: Two galaxies separated by 8.65 kpc, r1/2 ~1 kpc, velocity offset ~400 km/s | F: Early-stage major merger with starburst in both galaxies | **supported**
- H: Is alpha_CO and G/D lower than typically assumed? | E: Simulation-calibrated dynamical mass to gas mass | R: alpha_CO median 1.3; G/D 35 | F: lower than typical values, though with large uncertainty | **partially**
- H: Is there diffuse tidal gas? | E: Multi-component visibility fits of merged data | R: 10 sigma diffuse component with ~20% of flux | F: Tidal bridge detected | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Dynamical mass gives gas mass independent of CO luminosity  
  > "to assess the molecular gas content, independent of the CO luminosity or mm continuum." (5. MOLECULAR GAS MASS THROUGH A DYNAMICAL ASSESSMENT)
- How they decided it was enough: _not stated_
- Limitation (authors): Thin-disk approximation may underestimate Mdyn; many trials unphysical so no lower limit on alpha_CO  
  > "we cannot place a reliable lower limit on the value of α CO" (5.5)
- Caveat (inferred, ours): Gas mass from difference of comparable quantities with huge uncertainty
- Caveat (inferred, ours): fc calibrated on simulations that may not match PACS-787
- Caveat (inferred, ours): Possible weak AGN affects metallicity and SED
- Caveat (inferred, ours): Single object

## Reproducibility

- Data public (paper): ALMA project codes listed; public status not explicit  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2012.1.00952.S" (Acknowledgments)
- Products in archive: _not stated_
- Missing: Fensch simulation outputs and Bournaud CO post-processing tool
- Missing: clean parameters
- Missing: exact Monte Carlo setup
- Missing: priv. comm. HST astrometry
- Data volume (inferred): ~50-100 GB raw for three projects
- Score (inferred): 3/5, Public ALMA data and clear equations, but imaging parameters and simulation calibration are unspecified.
- Rediscovery candidate: no, Simulation calibration and unstated imaging settings prevent a complete recipe.

## Links

- Method: Fensch et al. 2017 (merger simulations for fc)
- Method: Bournaud et al. 2015 (CO post-processing tool)
- Companion: Silverman et al. 2018 (CO(2-1) sample paper)
- Related: COSMOS
- Related: FMOS-COSMOS

## Checks

```json
{
 "quotes": 83,
 "quotes_ok": 83,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 3,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 10,
 "numeric_problems": 0,
 "fill": {
  "facts": 85,
  "stated": 61,
  "rate": 0.718
 },
 "evidence_ok": true
}
```
