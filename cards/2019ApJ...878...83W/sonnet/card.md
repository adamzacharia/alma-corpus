# Evolution of the Gas Mass Fraction of Progenitors to Today’s Massive Galaxies: ALMA Observations in the CANDELS GOODS-S Field

`2019ApJ...878...83W` | The Astrophysical Journal 2019 | first author: Wiklind, Tommy | arXiv: 1903.06962 | DOI: 10.3847/1538-4357/ab1089

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies
- Question: How does the gas mass fraction of likely progenitors of a z=0 galaxy of M*=1.5e11 Msun evolve over z=2-5, using ALMA dust continuum as a gas tracer?  
  > "Gas masses are derived from the 850 µm luminosity. Ancillary data from the CANDELS GOODS-S survey are used to derive the gas mass fractions." (abstract)
- Target **70 CANDELS GOODS-S galaxies (MEAM-selected progenitors, z=2,3,4,5 bins)**: coordinates per-galaxy RA/Dec in Table 1 (CANDELS H-band catalog)  
  > "From this catalog we randomly select 70 galaxies in four redshift bins centered on z=2, 3, 4 and 5" (2.2 The CANDELS GOODS-S sample); "Note—Coordinates are from the CANDELS H-band selected catalog." (Table 1); z/distance z=1.6-5.5 (13 spectroscopic, rest photometric)  
  > "From this catalog we randomly select 70 galaxies in four redshift bins centered on z=2, 3, 4 and 5" (2.2 The CANDELS GOODS-S sample); "Note—Coordinates are from the CANDELS H-band selected catalog." (Table 1); distance from CANDELS catalog (Santini et al. 2015)  
  > "From this catalog we randomly select 70 galaxies in four redshift bins centered on z=2, 3, 4 and 5" (2.2 The CANDELS GOODS-S sample); "Note—Coordinates are from the CANDELS H-band selected catalog." (Table 1)

## Data provenance

- ALMA projects: 2015.1.00870.S
- bands: Band 6 (230 GHz, 1.3 mm) for z=4-5; Band 7 (345 GHz, 870 µm) for z=2-3  
  > "The z=4– 5 observations were done using the Band 6 receivers, 230 GHz (λ 1.3 mm), while the z=2–3 observations were done using the Band 7 receivers, 345 GHz (λ 870 µm)." (3.1 ALMA observations and data reduction)
- frequencies and spectral setup: 7.5 GHz total, four 1.875 GHz spectral windows, 128 dual-pol channels each  
  > "The correlator was configured to process a total bandwidth of 7.5 GHz, consisting of four 1.875 GHz-wide spectral windows." (3.1 ALMA observations and data reduction)
- continuum bandwidth: _not stated_
- arrays: 41-50 12-m antennas  
  > "the z=2 sample, targeting 20 galaxies, was observed December 17-28, 2016, using 50 12-m antennas." (3.1 ALMA observations and data reduction)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: requested ~0.5"x0.5"  
  > "The array configurations used during the observations were selected to give the requested angular resolution of about 0.′′5 × 0.′′5." (3.1 ALMA observations and data reduction)
- max recoverable scale: _not stated_
- sensitivity: required 1σ rms 100 µJy (z=2,3), 50 µJy (z=4), 30 µJy (z=5)  
  > "For the z=4 and z=5 samples, the B6 rms noise requirements were 50 µJy and 30 µJy, respectively" (3.1 ALMA observations and data reduction)
- time on source: _not stated_
- observing dates: Apr 30 2016 (z=4,5); Jun 18-Dec 14 2016 (z=3); Dec 17-28 2016 (z=2)  
  > "The z=3 sample, targeting 20 galaxies, was observed during multiple sessions during the period June 18 - December 14, 2016" (3.1 ALMA observations and data reduction)
- pi or archival as stated: _not stated_
- Other facility **CANDELS GOODS-S (HST, VLT, Spitzer)**: Photometric catalog, redshifts, stellar masses, SED-fit parameters  
  > "The multiwavelength catalog includes 18 bands and combines observations from the ERS/WFC3 and CANDELS/WFC3 data" (3.2 CANDELS data)
- External data: Stellar masses, redshifts, SFR, E(B-V), metallicity from CANDELS SED fits  
  > "The redshifts and stellar mass estimates used in our analysis are from Santini et al. (2015)." (3.2 CANDELS data) [from Santini et al. 2015 (cite: Santini2015)]
- External data: Sizes and Sersic indices  
  > "We also use data on the size and morphology of the galaxies in the CANDELS GOODS-S catalog from van der Wel et al. 2012." (3.2 CANDELS data) [from van der Wel et al. 2012]
- External data: L850/Mgas conversion factor alpha = 6.7±1.7e19 erg/s/Hz/Msun  
  > "derived by Scoville et al. (2014, 2016):" (4.1 Submm data) [from Scoville et al. 2014, 2016]
- External data: CMB correction to observed flux  
  > "see da Cunha et al. (2013) for a discussion and quantification of this correction." (4.1 Submm data) [from da Cunha et al. 2013]
- Simulation/model as data: MEAM progenitor selection (Bolshoi merger tree scatter, Millennium M*(Mh,z) relation)  
  > "We incorporate the statistical scatter in the merger tree from the Bolshoi simulation (Behroozi et al. 2013) and the M ∗ (M h , z) relation derived from the Millennium simulation (Moster et al. 2013)." (2.1 The MEAM selection)

## Processing

### Calibration

- pipeline or manual: standard ALMA pipeline  
  > "The data were calibrated and reduced using the standard ALMA pipeline." (3.1 ALMA observations and data reduction)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Ceres and Pallas  
  > "Ceres and Pallas were primary flux calibrators." (3.1 ALMA observations and data reduction)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA task CLEAN  
  > "We tried different weighting schemes in the CLEAN process to find the best trade-off between sensitivity and angular resolution." (3.1. ALMA observations and data reduction)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "we did the final flux measurements using natural weights." (3.1 ALMA observations and data reduction)
- uv taper: _not stated_
- cell size: 0.1" x 0.1"  
  > "In the CLEAN process we pixelated the image with a pixel size 0.′′1 × 0.′′1." (3.1 ALMA observations and data reduction)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: HPBW 26.5" (B6), 18.0" (B7); images in figures not primary-beam corrected  
  > "is 26.′′5 for the B6 data and 18.′′0 for the B7 data." (3.1 ALMA observations and data reduction)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: z=3 average 0.56"x0.40", PA -86 deg; Table 3 gives beams per bin  
  > "the z=3 galaxies have an average restoring beam of 0.′′56 × 0.′′40, with a position angle of − 86 ◦ ." (3.1 ALMA observations and data reduction)
- final rms: _not stated_

### Inherited from earlier work

- Gas mass from 850 µm luminosity using alpha_850, Td=25 K, beta=1.8  
  > "assuming a dust temperature T d = 25 K and dust emissivity index β = 1.8 to derive L 850 µm (e.g. Scoville et al. 2016)." (4.1 Submm data) [from Scoville et al. 2014, 2016]
- MEAM method  
  > "the multi-epoch abundance matching method developed by Behroozi et al. (2013) and Moster et al. (2013)" (2.1 The MEAM selection) [from Behroozi et al. 2013; Moster et al. 2013]

### Not stated but needed to reproduce (our reading)

- Briggs robust and CLEAN threshold/masking, number of iterations
- Method of stacking (weights, positions) of non-detected galaxies
- Pipeline/CASA version
- Exact procedure and aperture for 2D Gaussian fits and noise measurement
- How the 3σ upper limit flux was converted, rest-frame 850 µm k-correction details
- Which MEAM stellar mass bounds per bin and how random selection was done
- Bandpass/phase calibrator spelled consistently (J023+1636, J03344008 appear garbled)
- Table 3 band/redshift labels inconsistent with text

## Analysis recipe

1. **Select progenitor sample**: MEAM defines M*-z region of progenitors of z=0 log M*=11.2; 70 galaxies randomly chosen from CANDELS GOODS-S H-band catalog in four z bins  
  > "From this catalog we randomly select 70 galaxies in four redshift bins centered on z=2, 3, 4 and 5" (2.2 The CANDELS GOODS-S sample)
   - fitting: _not stated_
   - validation: _not stated_
2. **Image continuum and measure fluxes**: CLEAN natural-weight images; peak flux, or 2D Gaussian integrated flux for slightly extended sources; 5σ detection limit  
  > "In these cases we derived the integrated flux by fitting a two-dimensional Gaussian to the emission." (3.1 ALMA observations and data reduction)
   - software: CASA
   - parameter: detection limit 5σ  
  > "we set a detection limit of 5 σ for a source to be considered securely detected." (3.1 ALMA observations and data reduction)
   - fitting: 2D Gaussian  
  > "In these cases we derived the integrated flux by fitting a two-dimensional Gaussian to the emission." (3.1. ALMA observations and data reduction)
   - validation: _not stated_
3. **Stack non-detections**: stacked ALMA images of non-detected galaxies per bin; 3σ rms upper limits; random 4-galaxy substacks checked  
  > "We construct stacked ALMA images of the non-detected galaxies for each redshift bin." (4.1 Submm data)
   - fitting: _not stated_
   - validation: substacks of four galaxies showed no emission at 2σ  
  > "None showed any emission even at the 2 σ level." (4.1 Submm data)
4. **Derive gas masses and gas fractions**: Mgas = L850/alpha850 with CMB correction; fgas = Mgas/(Mgas+M*)  
  > "The gas mass fraction is defined as f gas = M gas /( M gas + M ∗ )." (4.2 Gas mass fraction)
   - assumption: Td=25 K, beta=1.8, alpha_850 = 6.7e19 erg/s/Hz/Msun, CMB correction for 25 K  
  > "The correction factors used here are listed in Table 1, for an assumed dust temperature of 25 K." (4.1 Submm data)
   - fitting: _not stated_
   - validation: compared with scaling relations of Sargent 2014, Scoville 2017, Tacconi 2018  
  > "We therefore derive the ∆ f gas = ( f gas ) obs − ( f gas ) model for each of the 26 galaxies" (4.2 Gas mass fraction)
5. **Test sensitivity and metallicity effect**: Modified blackbody SED to get minimum detectable SFR; gas-to-dust vs metallicity (Draine 2007; Remy-Ruyer) correction to z>=4 limits  
  > "We vary the dust temperature between 25-35 K, the dust emissivity index β = 1.5 − 1.8 and the critical wavelength λ 0 = 50 − 100 µm." (4.2 Gas mass fraction)
   - assumption: gas-phase Z as low as ~0.2 Zsun at z>=4 via mass-metallicity relation  
  > "the gas-phase metallicity of our z ≳ 4 galaxies can be as low as ∼ 0.2 Z ⊙" (5.3 Metallicity and stellar mass)
   - fitting: _not stated_
   - validation: _not stated_
6. **Fit evolution of fgas with cosmic time**: linear fit of fgas vs cosmic time over z=3 to 0 including literature points  
  > "they can be fitted by a linear relation: f gas = (0.075 ± 0.055) + (0.043 ± 0.007) t Gyr ." (5.1 The gas mass fraction over cosmic time)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : CLEAN imaging  
  > "We tried different weighting schemes in the CLEAN process to find the best trade-off between sensitivity and angular resolution." (3.1. ALMA observations and data reduction)
- **ALMA pipeline** : calibration  
  > "calibrated and reduced using the standard ALMA pipeline" (3.1 ALMA observations and data reduction)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Detection rate z=2 | 75% (15/20) | not stated | percent | 2 | We detect submm emission in 15 out of 20 galaxies in the z=2 sample, 11 out of 20 in the z=3 sample |
| Mean fgas detected z=2 | 0.55 | ±0.12 (abstract/summary; ±0.17 in Sect. 4.2) | dimensionless | 4 | The average gas mass fraction for the detected z = 2 galaxies is f gas = 0.55 ± 0.12 |
| Mean fgas detected z=3 | 0.62 | ±0.15 (summary; ±0.12 in Sect. 4.2) | dimensionless | 4 | f gas = 0.62 ± 0.15 for the z = 3 sample |
| Stacked fgas upper limits z=2,3,4,5 | <0.08, <0.15, <0.38, <0.37 | 3σ | dimensionless | 3 | 4 4.339 20 8.6 < 9.560 < 0.38 |
| Upper limit fgas z>=4 corrected for low metallicity | 0.66 | not stated | dimensionless | 5 | the upper limit to the gas mass fraction of the z=4 and z=5 samples would increase to ∼ 0.66. |
| Rate of fgas decrease with cosmic time | 0.043 | ±0.007 | Gyr^-1 | 6 | decreases at a constant rate of 0.043 ± 0.007 Gyr − 1 over a time interval of ∼ 11.5 Gyr. |
| Mean Δfgas vs Sargent 2014 / Tacconi 2018 | 0.013 / 0.025 | ±0.15 each | dimensionless | 4 | are 0.013 ± 0.15 and 0.025 ± 0.15, respectively |

## Qualitative findings

- Non-detected z=2-3 galaxies tend to be spheroidal, smaller and have lower sSFR; z>=4 galaxies have high stellar-population metallicity (~0.9 Zsun) but no dust detection  
  > "the detected galaxies having a S´ersic index indicating a disk-like morphology, while the undetected galaxies, on average, have a more spheroidal morphology." (4.3. Comparison with CANDELS data)

## Claim tuples

- H: Do gas fractions of MEAM progenitors at z=2-3 match main-sequence scaling relations? | E: ALMA dust continuum gas masses for detected galaxies compared with scaling relations | R: Mean Δfgas ~0.01-0.03 relative to Sargent and Tacconi | F: Detected galaxies agree with expectations; fgas falls linearly with time from z=3 to 0 | **supported**
- H: Are z>=4 low-mass progenitors detectable in dust continuum with expected gas fractions? | E: ALMA observations and stacking of 30 galaxies at z=4-5 | R: 0% detections; stacked fgas<0.38, <0.37 (<0.66 with metallicity correction) | F: Low gas-phase metallicity alone cannot explain the non-detections | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Single-flux-density dust continuum is a faster proxy for gas mass than CO  
  > "A faster, albeit less direct, method to estimate the gas mass in high redshift galaxies is to use a single flux density measurement of optically thin dust emission." (1. Introduction)
- Alternative: Different weighting schemes tried in CLEAN; natural chosen since sources unresolved  
  > "We tried different weighting schemes in the CLEAN process to find the best trade-off between sensitivity and angular resolution." (3.1 ALMA observations and data reduction)
- How they decided it was enough: _not stated_
- Limitation (authors): Conversion factor calibrated on massive, near-solar metallicity galaxies; gas-phase metallicity of sample unknown; dust SED not sampled  
  > "We have no observational input regarding the gasphase metallicities of the galaxies in our sample" (5.3 Metallicity and stellar mass)
- Caveat (inferred, ours): Gas masses depend on a single assumed Td=25 K and a fixed alpha_850
- Caveat (inferred, ours): Stacking details and upper limits not fully specified
- Caveat (inferred, ours): H-band selection biases against dusty z>=4 galaxies
- Caveat (inferred, ours): Small samples; random selection includes quiescent galaxies
- Caveat (inferred, ours): Inconsistent errors for mean fgas between sections

## Reproducibility

- Data public (paper): ALMA project code given; CANDELS public catalogs linked  
  > "We adopt the CANDELS GOODS-S public catalog for the redshift and stellar mass values of CANDELS GOODS-S galaxies used in this paper." (3.2 CANDELS data)
- Products in archive: _not stated_
- Missing: Stacking procedure
- Missing: CLEAN parameters
- Missing: CASA/pipeline version
- Missing: Exact CMB correction implementation and SED k-correction
- Data volume (inferred): ~50-100 GB raw (70 pointings, Cycle 3/4 Band 6/7)
- Score (inferred): 6/5, Public data, Table of per-galaxy fluxes and simple conversion; imaging and stacking details are thin.
- Rediscovery candidate: yes, Public data, simple flux-to-gas-mass recipe with numeric results in tables, though stacking and imaging details are missing.

## Links

- Method: Scoville et al. 2014, 2016 (L850-gas mass conversion)
- Method: da Cunha et al. 2013 (CMB correction)
- Method: Moster et al. 2013; Behroozi et al. 2013 (MEAM selection)
- Companion: Santini et al. 2015 (CANDELS GOODS-S stellar masses)
- Related: CANDELS
- Related: PHIBSS2
- Related: HUDF ALMA surveys

## Checks

```json
{
 "quotes": 58,
 "quotes_ok": 58,
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
  "facts": 77,
  "stated": 44,
  "rate": 0.571
 },
 "evidence_ok": true
}
```
