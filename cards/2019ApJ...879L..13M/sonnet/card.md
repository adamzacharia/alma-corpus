# ALMA Observations of Molecular Gas in the Host Galaxy of AT2018cow

`2019ApJ...879L..13M` | The Astrophysical Journal Letters 2019 | first author: Morokuma-Matsui, Kana | arXiv: 1906.05446 | DOI: 10.3847/2041-8213/ab2915

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: nearby_galaxies, transients
- Question: What are the molecular gas and star-formation properties of the host galaxy CGCG 137-068 and the local AT2018cow site, and do they favor a massive-star explosion or a TDE progenitor?  
  > "we study the molecular-gas and star-formation properties of CGCG 137-068 and local AT2018cow site using CO($J$=1-0) data taken with the Atacama Large Millimeter/submillimeter Array (ALMA)." (Introduction)
- Target **CGCG 137-068 (host of AT2018cow)**: coordinates 16h16m00.57s +22d16m08.24s (SDSS)  
  > "We adopt a distance to CGCG 137-068 of $60$ Mpc (1$''\sim291$ pc)" (Introduction); "| Redshift                                 | 0.0141                     | SDSS       |" (Table 1); z/distance z = 0.0141; 60 Mpc  
  > "We adopt a distance to CGCG 137-068 of $60$ Mpc (1$''\sim291$ pc)" (Introduction); "| Redshift                                 | 0.0141                     | SDSS       |" (Table 1); distance from Table 1 reference 2 (Perley et al. 2019, per text)  
  > "We adopt a distance to CGCG 137-068 of $60$ Mpc (1$''\sim291$ pc)" (Introduction); "| Redshift                                 | 0.0141                     | SDSS       |" (Table 1)

## Data provenance

- ALMA projects: 2017.A.00045.T
- bands: Band 3 (100.00-115.99 GHz)  
  > "continuum flux of AT2018cow at band 3 ($100.00-115.99$ GHz)" (Data and Analysis)
- frequencies and spectral setup: TDM, 15.625 MHz resolution, 40.64 km/s  
  > "a frequency resolution of $15.625$ MHz, corresponding to a velocity resolution of $40.64$ km s$^{-1}$" (Data and Analysis)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: C43-1  
  > "with an antenna configuration of C43-1 in a target-of-opportunity (ToO) observation" (Data and Analysis)
- baselines: 15 m to 161 m  
  > "Antenna baselines range from 15 m to 161 m" (Data and Analysis)
- angular resolution: 3.66 x 2.71 arcsec (1.1 x 0.8 kpc)  
  > "The achieved synthesized beam is $3''.66\times2''.71$" (Data and Analysis)
- max recoverable scale: 29 arcsec (8.4 kpc)  
  > "a maximum recoverable scale is $29$ arcsec or 8.4 kpc" (Data and Analysis)
- sensitivity: 0.21 mJy/beam at 40.64 km/s  
  > "The achieved rms noise ($\sigma_{\rm rms}$) is 0.21 mJy beam$^{-1}$ after primary beam correction" (Data and Analysis)
- time on source: 19.7 min per execution  
  > "The on-source integration time of each execution was $19.7$ min." (Data and Analysis)
- observing dates: June 30 and July 16, 2018  
  > "were obtained on June 30 and July 16, 2018" (Data and Analysis)
- pi or archival as stated: Archival ToO data, PI Steve Schulze  
  > "project code of 2017.A.00045.T, PI: Steve Schulze" (Data and Analysis)
- Line: 12CO J=1-0 (115.271202 GHz)
- Other facility **SDSS**: Optical images and spectrum (metallicity, BPT)  
  > "the gas-phase metallicity is measured from the SDSS spectrum" (Galactic-scale properties)
- Other facility **GMRT**: HI data from literature  
  > "seen in $\sim6$-arcsec resolution data taken with the Giant Metrewave Radio Telescope (GMRT)" (Introduction)
- External data: Stellar mass and SFR of CGCG 137-068  
  > "Both the stellar mass ($M_{\rm star}$) and star formation rate (SFR) values are taken from (cite: Perley:2019aa)" (Galactic-scale properties) [from (cite: Perley:2019aa)]
- External data: Atomic gas mass  
  > "the atomic gas mass ($M_{\rm atom}$) is from (cite: Roychowdhury:2019aa)" (Galactic-scale properties) [from (cite: Roychowdhury:2019aa)]
- External data: xGASS and xCOLD-GASS reference galaxies  
  > "with those of xGASS (cite: Catinella:2018aa) and xCOLD-GASS galaxies (cite: Saintonge:2017aa) at similar redshifts" (Galactic-scale properties) [from (cite: Catinella:2018aa); (cite: Saintonge:2017aa)]

## Processing

### Calibration

- pipeline or manual: ALMA Science Pipeline  
  > "calibrated with the ALMA Science Pipeline (version of r40896 of Pipeline-CASA51-P2-B) in the CASA 5.1.1 package" (Data and Analysis)
- casa version: CASA 5.1.1 (calibration); CASA 5.4 (imaging)  
  > "generated with the `TCLEAN` task in CASA version 5.4" (Data and Analysis)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: better than 5%  
  > "The flux accuracy of the ALMA 12-m band-3 data is reported to be better than 5 %" (Data and Analysis)
- self calibration: _not stated_

### Imaging

- task: tclean, niter 10000  
  > "and `niter` of 10000" (Data and Analysis)
- deconvolver: _not stated_
- weighting robust: Briggs, robust 0.5  
  > "`Briggs` weighting with a `robust` parameter of 0.5" (Data and Analysis)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: auto-multithresh: sidelobethreshold 2.0, noisethreshold 4.25, minbeamfrac 0.3, lownoisethreshold 1.5, negativethreshold 15.0  
  > "`sidelobethreshold` of 2.0, `noisethreshold` of 4.25, `minbeamfrac` of 0.3, `lownoisethreshold` of 1.5, and `negativethreshold` of 15.0" (Data and Analysis)
- multiscale scales: _not stated_
- continuum subtraction: UVCONTSUB  
  > "Continuum emission is subtracted using the `UVCONTSUB` task" (Data and Analysis)
- line free channels: _not stated_
- primary beam correction: applied  
  > "0.21 mJy beam$^{-1}$ after primary beam correction" (Data and Analysis)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 3.66 x 2.71 arcsec, PA -27.8 deg  
  > "with a P.A. of $-27.8^\circ$" (Data and Analysis)
- final rms: 0.21 mJy/beam at 40.64 km/s  
  > "The achieved rms noise ($\sigma_{\rm rms}$) is 0.21 mJy beam$^{-1}$ after primary beam correction" (Data and Analysis)

### Inherited from earlier work

- Auto-masking parameters follow CASA Guides standard values for 12-m data  
  > "standard values for 12-m array data provided in the CASA Guides for auto-masking" (Data and Analysis) [from CASA Guides Automasking Guide]
- Galactic CO-to-H2 conversion factor  
  > "$X_{\rm CO}=2.0\times 10^{20}$ cm$^{-2}$ (K km s$^{-1}$)$^{-1}$ (cite: Bolatto:2013rr)" (1-kpc-scale properties) [from (cite: Bolatto:2013rr)]

### Not stated but needed to reproduce (our reading)

- Line-free channels used for UVCONTSUB
- Cell size and image size
- Aperture/region and velocity range used to integrate I_CO and total flux
- How the 6 arcsec site-level N(H2) was measured (aperture)
- Method for SFE definitions and SFE(gas)
- Line ratio / CO-to-H2 formula for L'CO to Mmol (helium inclusion)
- Whether the two executions were combined and the calibrators used

## Analysis recipe

1. **Calibrate and image CO(1-0) cube**: Pipeline calibration, uvcontsub, tclean mosaic cube with auto-multithresh  
  > "a $^{12}$CO($J$=1-0) mosaic data cube is generated with the `TCLEAN` task in CASA version 5.4" (Data and Analysis)
   - software: CASA
   - parameter: robust 0.5, niter 10000  
  > "`Briggs` weighting with a `robust` parameter of 0.5" (Data and Analysis)
   - fitting: _not stated_
   - validation: _not stated_
2. **Derive H2 column density and gas surface density at the AT2018cow site**: Convert CO intensity to K via Rayleigh-Jeans and apply Galactic XCO  
  > "using the standard CO-to-H$_2$ conversion factor from the Milky-Way of $X_{\rm CO}=2.0\times 10^{20}$ cm$^{-2}$ (K km s$^{-1}$)$^{-1}$" (1-kpc-scale properties)
   - assumption: Milky Way XCO justified by solar or super-solar metallicity  
  > "since CGCG 137-068 has a solar or super-solar metallicity (see below)" (1-kpc-scale properties)
   - fitting: _not stated_
   - validation: _not stated_
3. **Derive total molecular gas mass and compare with xGASS/xCOLD-GASS**: Integrated CO luminosity to Mmol with Galactic XCO; combine with literature Mstar, SFR, Matom; compare scaling relations  
  > "we compare the integrated galactic properties (SFR, metallicity, $M_{\rm atom}/M_{\rm star}$, $M_{\rm mol}/M_{\rm star}$" (Galactic-scale properties)
   - assumption: Distance 60 Mpc  
  > "We adopt a distance to CGCG 137-068 of $60$ Mpc" (Introduction)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 5.1.1 (pipeline), 5.4 (imaging): Calibration, continuum subtraction, tclean imaging  
  > "Data calibration and imaging were conducted with the standard ALMA data analysis package, the Common Astronomy Software Applications" (Data and Analysis)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Total molecular gas mass | 1.85e8 | 0.04e8 | Msun | 3 | $(1.85\pm0.04)\times10^8$ M$_\odot$ |
| N(H2) at AT2018cow site | 8.6e20 | not stated | cm^-2 | 2 | The H$_2$ column density at the AT2018cow site is estimated to be $8.6\times10^{20}$ cm$^{-2}$ |
| Sigma_mol at site | 14 | not stated | Msun pc^-2 | 2 | of $14$ M$_\odot$ pc$^{-2}$ |
| I_CO | 0.575 | 0.020 | K km/s | 3 | $0.575\pm0.020$ |
| L'CO | 4.34e7 | 0.15e7 | K km/s pc^2 | 3 | $(4.34\pm0.15)\times 10^7$ |
| Mmol/Mstar | 0.13 | not stated | dimensionless | 3 | $M_{\rm mol}/M_{\rm star}$, SFE(mol), and $M_{\rm mol}/M_{\rm atom}$ of CGCG 137-068 are $0.13$ |
| SFE(mol) | 1.2e-9 | not stated | yr^-1 | 3 | $1.2\times10^{-9}$ yr$^{-1}$ |
| Mmol/Matom | 0.29 | not stated | dimensionless | 3 | / M$_{\rm mol}$/M$_{\rm atom}$             / $0.29$                     / this study / |

## Qualitative findings

- AT2018cow lies between a CO peak and a blue young cluster, indicating ongoing star formation  
  > "AT2018cow is located between one of the CO peaks and a blue stellar cluster" (Summary)

## Claim tuples

- H: Is CGCG 137-068 a normal star-forming dwarf in molecular gas properties? | E: Compare Mmol, SFE and gas ratios with xGASS/xCOLD-GASS | R: Normal in SFR, Matom/Mstar, Mmol/Mstar, SFE(mol), Mmol/Matom; high metallicity for its mass | F: Normal SF dwarf galaxy except high metallicity | **supported**
- H: Does the AT2018cow site favor a massive-star progenitor over a TDE? | E: Compare site N(H2), location and host properties with CCSN and TDE samples | R: N(H2)=8.6e20 cm^-2 comparable to Type-I CCSNe; near CO peak and young cluster | F: Massive-star explosion favored, especially SNe Ic-BL without GRB | **supported**

## Reasoning

- Why this data: Archival ToO data covered CO(1-0) though intended for continuum  
  > "Since the original purpose of this observation is to measure the continuum flux of AT2018cow at band 3" (Data and Analysis)
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): FELT host metallicity sample is too small to conclude  
  > "the sample size ($N=2$) is too small to conclude it" (Implications for AT2018cow progenitor)
- Caveat (inferred, ours): Galactic XCO is assumed; uncertain for dwarf galaxies
- Caveat (inferred, ours): Coarse 40 km/s resolution and 1 kpc beam limit site-scale conclusions
- Caveat (inferred, ours): No Halpha data to confirm HII association
- Caveat (inferred, ours): Comparison with CCSN sample selection and aperture mismatch

## Reproducibility

- Data public (paper): Archival ALMA data  
  > "using archival band-3 data from the Atacama Large Millimeter/submillimeter Array (ALMA)" (abstract)
- Products in archive: _not stated_
- Missing: Line-free channels, cell/image size
- Missing: Flux integration aperture and velocity range
- Missing: XCO/mass formula details including helium
- Missing: Literature Mstar, SFR, Matom values
- Data volume (inferred): ~10-20 GB
- Score (inferred): 3/5, Imaging parameters mostly given but aperture and integration choices are missing; short letter.
- Rediscovery candidate: yes, Public archival data, mostly complete imaging recipe, numeric results (Mmol, N(H2)).

## Links

- Companion: (cite: Roychowdhury:2019aa) (GMRT HI of the host)
- Companion: (cite: Perley:2019aa) (Host Mstar and SFR)
- Related: xGASS
- Related: xCOLD-GASS
- Related: SDSS

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
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 65,
  "stated": 42,
  "rate": 0.646
 },
 "evidence_ok": true
}
```
