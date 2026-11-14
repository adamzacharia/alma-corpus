# Tests of star formation metrics in the low-metallicity galaxy NGC 5253 using ALMA observations of H30α line emission

`2017MNRAS.472.1239B` | Monthly Notices of the Royal Astronomical Society 2017 | first author: Bendo, G. J. | arXiv: 1707.06184 | DOI: 10.1093/mnras/stx1837

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, star_formation
- Question: What is the SFR of NGC 5253 from H30alpha recombination line emission, and how reliable are SFRs from other commonly used metrics in this low-metallicity dwarf galaxy?  
  > "to measure the star formation rate (SFR) within the galaxy and to test the reliability of SFRs derived from other commonly-used metrics." (abstract)
- Target **NGC 5253**: coordinates pointings 13:39:55.9 -31:38:26 and 13:39:56.8 -31:38:32 (J2000)  
  > "we use a distance of 3.15$\pm$0.20 Mpc (cite: freedman01)" (Introduction); "two pointings centered on positions 13:39:55.9 -31:38:26 and 13:39:56.8 -31:38:32 in J2000 coordinates" (2.1 Observations and data processing); z/distance 3.15±0.20 Mpc  
  > "we use a distance of 3.15$\pm$0.20 Mpc (cite: freedman01)" (Introduction); "two pointings centered on positions 13:39:55.9 -31:38:26 and 13:39:56.8 -31:38:32 in J2000 coordinates" (2.1 Observations and data processing); distance from Freedman et al. 2001  
  > "we use a distance of 3.15$\pm$0.20 Mpc (cite: freedman01)" (Introduction); "two pointings centered on positions 13:39:55.9 -31:38:26 and 13:39:56.8 -31:38:32 in J2000 coordinates" (2.1 Observations and data processing)

## Data provenance

- ALMA projects: 2013.1.00210.S
- bands: Band 6 (231.6 GHz continuum, H30alpha at 231.90 GHz rest)  
  > "The uncertainty in band 6 flux calibration is specified in the ALMA Proposer’s Guide" (2.1 Observations and data processing)
- frequencies and spectral setup: Three spectral windows, 1.875-1.992 GHz wide each, covering ~229-232.6 GHz (H30alpha) and 243.6-245.6 GHz (CO, CS)  
  > "| Morita | A002/X8440e0/X29c6 |  229.216 - 231.208  |   1.992   |   2040    |" (Table 2 (spectral set-up))
- continuum bandwidth: _not stated_
- arrays: 12 m main array and Morita (7 m) Array  
  > "Observations were performed with both the main (12 m) array and the Morita (7 m) Array with baselines ranging from 8 to 1568 m." (2.1 Observations and data processing)
- configurations: _not stated_
- baselines: 8 to 1568 m  
  > "with baselines ranging from 8 to 1568 m" (2.1 Observations and data processing)
- angular resolution: H30alpha cube beam 0.21x0.19 arcsec; continuum beam 0.28x0.25 arcsec  
  > "The reconstructed beam has a size of 0.21$\times$0.19 arcsec." (2.1 Observations and data processing)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: Morita 30.7 min each; 12 m 8.5, 13.2, 15.8 min  
  > "| 12 m | A002/X966cea/X25de | 11 Dec 2014 | 8.5 | 37 | 13-336 | J1337-1257 | Callisto | J1342-2900 |" (Table 1)
- observing dates: 15 Jun 2014, 10 Dec 2014, 11 Dec 2014, 18 Jul 2015 (two)  
  > "| 12 m | A002/Xa5df2c/X50ce | 18 Jul 2015 | 13.2 | 39 | 14-1512 | J1337-1257 | J1427-4206 | J1342-2900 |" (Table 1)
- pi or archival as stated: _not stated_
- Line: H30alpha recombination line (231.90 GHz)
- Other facility **WISE**: 12 and 22 micron flux densities (AllWISE)  
  > "we made measurements within Wide-field Infrared Survey Explorer (cite: wright10) images from the AllWISE data release." (3.2.1 SFR calculations)
- Other facility **Herschel**: 70-500 micron global flux densities (from Rémy-Ruyer et al. 2013)  
  > "we used the globally-integrated flux densities measured from *Herschel* data by (cite: remyruyer13)" (3.2.1 SFR calculations)
- External data: Herschel 70-500 micron globally-integrated flux densities  
  > "we used the globally-integrated flux densities measured from *Herschel* data by (cite: remyruyer13)" (3.2.1 SFR calculations) [from Rémy-Ruyer et al. 2013 (cite: remyruyer13)]
- External data: Halpha, Paalpha, Pabeta fluxes and extinction corrections for clusters 5 and 11  
  > "(cite: calzetti15) published H$\alpha$, Pa$\alpha$, and Pa$\beta$ fluxes that have been corrected for foreground dust extinction" (3.3.1 SFR calculations) [from Calzetti et al. 2015 (cite: calzetti15)]
- External data: Globally integrated 1.4 GHz flux density 84.7±3.4 mJy  
  > "the globally-integrated measurement of $84.7 \pm 3.4$ mJy from the 1.4 GHz NRAO VLA Sky Survey (cite: condon98)" (3.1 Comparisons to millimetre and radio) [from Condon et al. 1998 (cite: condon98)]
- External data: Electron temperature 11500 K from [OIII] and density 600 cm^-3 from [OII]/[SII]  
  > "we use 11500 K for the electron temperature, which is based on \[OIII\] measurements" (2.3 SFR from the H30alpha data) [from Kobulnicky 1997; López-Sánchez 2007; Guseva 2011; Monreal-Ibero 2012]
- Simulation/model as data: Starburst99 v7.0.1 Geneva 2012/13 tracks used to derive Q-to-SFR conversions and metallicity/rotation correction factors  
  > "The current version (7.0.1) of Starburst99 (cite: leitherer14) provides the Geneva 2012/13 evolutionary tracks" (2.3 SFR from the H30alpha data)

## Processing

### Calibration

- pipeline or manual: Manual calibration of each execution block separately  
  > "The visibility data for each execution block was calibrated separately using the Common Astronomy Software Applications (CASA) version 4.7.0." (2.1 Observations and data processing)
- casa version: CASA 4.7.0  
  > "Common Astronomy Software Applications (CASA) version 4.7.0" (2.1 Observations and data processing)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Ceres, Callisto, Titan, J1427-4206 (Butler-JPL-Horizons 2012 models; getALMAFlux for J1427-4206)  
  > "The Butler-JPL-Horizons 2012 models were used to obtain the flux densities for Callisto and Titan." (2.1 Observations and data processing)
- flux scale uncertainty: 15%  
  > "we used 15% as the final calibration uncertainty" (2.1 Observations and data processing)
- self calibration: _not stated_

### Imaging

- task: clean in CASA  
  > "then created a spectral cube using clean within CASA" (2.1 Observations and data processing)
- deconvolver: _not stated_
- weighting robust: Briggs robust = 0.5 for line cube; natural weighting for continuum image  
  > "We used Briggs weighting with a robust parameter of 0.5" (2.1 Observations and data processing); "we used natural weighting when creating the final image" (2.1 Observations and data processing)
- uv taper: _not stated_
- cell size: 0.05 arcsec  
  > "The pixels have a size of 0.05 arcsec, and the imaged field was 100$\times$100 arcsec." (2.1 Observations and data processing)
- image size: 100x100 arcsec  
  > "the imaged field was 100$\times$100 arcsec" (2.1 Observations and data processing)
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: Linear fit to visibilities in spw containing the line  
  > "fitting the visibility data at approximately 230.7-231.2 GHz and 231.7-232.5 GHz (in the Barycentric frame of reference) with a linear function" (2.1 Observations and data processing)
- line free channels: 230.7-231.2 and 231.7-232.5 GHz (Barycentric)  
  > "230.7-231.2 GHz and 231.7-232.5 GHz (in the Barycentric frame of reference)" (2.1 Observations and data processing)
- primary beam correction: applied after imaging  
  > "After creating the image, we applied a primary beam correction." (2.1 Observations and data processing)
- array combination: 12 m and Morita data concatenated; total power not included  
  > "Hence, we did not include the total power data in our analysis." (2.1 Observations and data processing)
- smoothing: _not stated_
- final beam: 0.21x0.19 arcsec (line); 0.28x0.25 arcsec (continuum)  
  > "The beam size is 0.28$\times$0.25 arcsec." (2.1 Observations and data processing)
- final rms: _not stated_

### Inherited from earlier work

- Q-to-SFR conversion 7.29e-54 for solar metallicity, Kroupa IMF  
  > "(cite: murphy11) derived a scaling term of $7.29\times10^{-54}$ for solar metallicity" (2.3 SFR from the H30alpha data) [from Murphy et al. 2011 (cite: murphy11)]
- Equation for Q from H30alpha flux  
  > "based on equations from (cite: scoville13)" (2.3 SFR from the H30alpha data) [from Scoville & Murchikova 2013 (cite: scoville13)]
- Halpha extinction correction relations using 22 micron and TIR  
  > "which are from (cite: kennicutt09)" (3.3.1 SFR calculations) [from Kennicutt et al. 2009 (cite: kennicutt09)]

### Not stated but needed to reproduce (our reading)

- Line-free channel selection for the continuum image beyond frequency ranges, and clean threshold, niter, and masking
- Flux of J1427-4206 values from getALMAFlux used
- How the 100x100 arcsec mosaic of two pointings was handled in cleaning
- Exact aperture centre and background treatment for curve-of-growth photometry
- Method used to fit line centre, FWHM and integrated flux
- Calibration scripts/CASA task parameters

## Analysis recipe

1. **Calibrate and image H30alpha cube and continuum**: CASA calibration per execution block, uv continuum subtraction, clean with Briggs robust 0.5, primary beam correction; natural-weighted continuum image  
  > "The H30$\alpha$ image was created after subtracting the continuum from the visibility data in the spectral window containing the line." (2.1 Observations and data processing)
   - software: CASA
   - parameter: 10 MHz channels (12.9 km/s), 231.40-231.80 GHz  
  > "The spectral channels in the cube have a width of 10 MHz (equivalent to a velocity width of 12.9 km s$^{-1}$)" (2.1 Observations and data processing)
   - fitting: _not stated_
   - validation: Imaged J1427-4206 and J1337-1257; flux differs <10% from getALMAFlux; astrometry check within 0.05 arcsec  
  > "The measured flux densities differ by $<$10% from the getALMAFlux estimates" (2.1 Observations and data processing)
2. **Measure line and continuum fluxes**: Curve-of-growth aperture photometry; line flux within 0.3 arcsec radius; continuum within 8.5 arcsec radius; Gaussian fit to image  
  > "Most of the H30$\alpha$ flux from the unresolved central source falls within a radius of 0.3 arcsec, so we will use the measurements of the line flux from within that radius as the total flux." (2.2 images)
   - software: CASA
   - fitting: _not stated_
   - validation: Compared continuum with SEST, OVRO, SMA measurements  
  > "We therefore think the ALMA flux density, which is consistent with the SEST measurement, should be fairly reliable." (2.2 images)
3. **Convert H30alpha flux to Q and SFR**: Scoville & Murchikova equation with alpha_B and emissivity interpolated from Storey & Hummer; then Starburst99-based Q-to-SFR conversion for Z=0.0056 with/without rotation  
  > "We interpolated among the $\alpha_B$ and $\epsilon_\nu$ terms published by (cite: storey95) to calculate specific values" (2.3 SFR from the H30alpha data)
   - software: Starburst99
   - parameter: Te = 11500 K, ne = 600 cm^-3, D = 3.15 Mpc  
  > "we use 11500 K for the electron temperature" (2.3 SFR from the H30alpha data)
   - assumption: Nuclear starburst contains most photoionizing stars; Kroupa IMF; continuous star formation >10 Myr; log Q scales linearly with Z; Z≅0.0056  
  > "we assume that the nuclear starburst detected in H30$\alpha$ data contains most of the photoionizing stars in the galaxy" (2.3 SFR from the H30alpha data)
   - fitting: _not stated_
   - validation: Interpolation accurate to within 5% based on 1994 Geneva tracks  
  > "this interpolation should be accurate to within 5%" (2.3 SFR from the H30alpha data)
4. **Compute SFRs from infrared data and total infrared flux**: WISE 12/22 micron aperture photometry; Herschel fluxes colour-corrected; TIR from log-log interpolation integrated 12-500 micron, Monte Carlo uncertainties; conversions of Rieke09, Calzetti10, Kennicutt&Evans12 scaled by 0.90/0.72  
  > "We therefore calculated the total infrared flux by first linearly interpolating between the logarithms of the monochromatic flux densities as a function of the logarithm of the wavelength and then integrating under the curve." (3.2.1 SFR calculations)
   - parameter: 150 arcsec source radius, background annulus 450-500 arcsec  
  > "The backgrounds were measured within annuli with radii of 450 and 500 arcsec" (3.2.1 SFR calculations)
   - assumption: WISE 22 micron conversion same as Spitzer 24 micron  
  > "assumed that the conversions from WISE 22 $\mu$m flux densities to SFR will be the same as for *Spitzer* 24 $\mu$m data" (3.2.1 SFR calculations)
   - fitting: Monte Carlo for TIR uncertainty  
  > "with the uncertainties derived using a monte carlo analysis" (3.2.1 SFR calculations)
   - validation: _not stated_
5. **Compute SFRs from Halpha with extinction corrections and compare**: Halpha fluxes of clusters 5 and 11 from Calzetti15, corrected via Pa lines, 22 micron or TIR; converted with Murphy11 factor 6.43e8; compare all SFRs to H30alpha  
  > "The H$\alpha$ fluxes can be converted to SFR using" (3.3.1 SFR calculations)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.7.0: calibration, continuum subtraction, imaging (clean)  
  > "Common Astronomy Software Applications (CASA) version 4.7.0" (2.1 Observations and data processing)
- **Analysis Utilities (getALMAFlux)** : flux density of J1427-4206 from calibrator catalogue  
  > "The getALMAFlux task within the Analysis Utilities software package was used to calculate the flux density of J1427-4206" (2.1 Observations and data processing)
- **Starburst99** 7.0.1: Q-to-SFR conversions and metallicity/rotation correction factors  
  > "All corrections are derived using version 7.0.1 of the Starburst99 models" (3 Other star formation tracers)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| H30alpha line integral | 0.86 | 0.04 (measurement) ; 0.13 (calibration) | Jy km/s | 2 | The integral of the line is 0.86 Jy km s$^{-1}$ with a measurement uncertainty of 0.04 Jy km s$^{-1}$ |
| H30alpha line velocity (barycentric) | 391 | 2 | km/s | 2 | 391$\pm$2 km s$^{-1}$ and a FWHM of 68$\pm$3 km s$^{-1}$ |
| H30alpha FWHM | 68 | 3 | km/s | 2 | 391$\pm$2 km s$^{-1}$ and a FWHM of 68$\pm$3 km s$^{-1}$ |
| 231.6 GHz continuum flux density (r<8.5 arcsec) | 104 | 16 | mJy | 2 | The 231.6 GHz continuum flux density within a radius of 8.5 arcsec is 104$\pm$16 mJy. |
| Photoionizing photon rate Q | 1.9e52 | 0.3e52 | s^-1 | 3 | we calculated $Q$ to be (1.9$\pm$0.3)$\times$$10^{52}$ s$^{-1}$. |
| SFR (Z=0.0056, with rotation) | 0.087 | 0.013 | Msun/yr | 3 | an SFR of 0.087$\pm$0.013 M$_\odot$ yr$^{-1}$ |
| SFR (Z=0.0056, no rotation) | 0.102 | 0.015 | Msun/yr | 3 | with only the correction for metallicity, we obtain 0.102$\pm$0.015 M$_\odot$ yr$^{-1}$ |
| Total infrared flux (12-500 micron) | 3.2e14 | 0.2e14 | Jy Hz | 4 | This gave a total infrared flux of (3.2$\pm$0.2)$\times$$10^{14}$ Jy Hz |
| SFR from total infrared (Z=0.0056, with rotation) | 0.107 | 0.008 | Msun/yr | 4 | / Total infrared                                             / $0.148 \pm 0.009$   / $0.133 \pm 0.009$   / $0.107 \pm 0.008$     / |
| SFR 1.4 GHz | 0.064 | 0.003 | Msun/yr | 5 | we obtain a SFR of $0.064 \pm 0.003$ M$_\odot$ yr$^{-1}$ |

## Qualitative findings

- H30alpha emission originates mainly from a compact central source (~0.15 arcsec deconvolved) coincident with the 231.6 GHz continuum peak; no second H30alpha source detected  
  > "No significant H30$\alpha$ emission is observed outside of the central peak." (2.2 images)
- Mid-infrared tracers give much higher SFR because dust is unusually hot; recommended against in low-metallicity galaxies  
  > "we strongly recommend not using any star formation tracer based on mid-infrared data for low metallicity galaxies." (Conclusions)

## Claim tuples

- H: Does H30alpha give a reliable SFR for NGC 5253 and how do other metrics compare? | E: Derive Q and SFR from ALMA H30alpha and compare to IR, Halpha and radio SFRs | R: SFR 0.087±0.013 Msun/yr; TIR SFR 0.107±0.008 within ~1.5-2 sigma | F: Total infrared SFR statistically equivalent to H30alpha | **supported**
- H: Mid-infrared SFR metrics are reliable in low-metallicity dwarfs | E: Compare 22 micron and Halpha+22 micron SFRs with H30alpha | R: SFRs ~3x higher | F: Unreliable owing to hot dust | **refuted**
- H: Extinction-corrected Halpha agrees with H30alpha | E: Compare Calzetti15 Pa-corrected Halpha SFR | R: within 25%, lower | F: statistically similar but lower | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Millimetre recombination lines are unaffected by dust extinction and directly trace photoionizing stars  
  > "these millimetre and submillimetre recombination lines are not affected by dust extinction" (Introduction)
- Alternative: Total power data not used; continuum from other spectral windows rejected owing to steep slope, short-baseline problems and broad CO line  
  > "made it difficult to create reliable continuum images using all spectral windows" (2.1 Observations and data processing)
- How they decided it was enough: _not stated_
- Limitation (authors): Lack of H30alpha from fainter sources could bias SFR downward; most continuum emission <5 sigma  
  > "could cause the SFR from the H30$\alpha$ emission to be biased downwards" (2.3)
- Caveat (inferred, ours): Single galaxy, so conclusions on metrics are not general
- Caveat (inferred, ours): Dust vs free-free contribution at 231.6 GHz uncertain; electron temperature assumed
- Caveat (inferred, ours): Aperture mismatch between ALMA nuclear and global IR fluxes
- Caveat (inferred, ours): Interpolation of Starburst99 in Z

## Reproducibility

- Data public (paper): ALMA data cited by project code; public status not explicitly stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2013.1.00210.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Clean parameters (threshold, masks, niter)
- Missing: Exact flux values adopted for calibrators
- Missing: Line fitting details
- Data volume (inferred): ~100-300 GB raw for 5 execution blocks
- Score (inferred): 4/5, Public data, clear calibration/imaging parameters and explicit formulas; some clean details missing.
- Rediscovery candidate: yes, Data public via project code, recipe largely complete, results numeric (line flux, Q, SFR).

## Links

- Method: Scoville & Murchikova 2013 (cite: scoville13) (Q from recombination line flux equation)
- Method: Murphy et al. 2011 (cite: murphy11) (SFR conversions)
- Companion: Miura et al. in preparation (CO(2-1) and other lines from same data)
- Companion: Bendo et al. 2015b, 2016 (cite: bendo15b; bendo16) (Earlier ALMA recombination line SFR studies of NGC 253 and 4945)

## Checks

```json
{
 "quotes": 77,
 "quotes_ok": 77,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 10,
 "numeric_problems": 0,
 "fill": {
  "facts": 80,
  "stated": 57,
  "rate": 0.713
 },
 "evidence_ok": true
}
```
