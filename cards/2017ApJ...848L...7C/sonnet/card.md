# ALMA Shows that Gas Reservoirs of Star-forming Disks over the Past 3 Billion Years Are Not Predominantly Molecular

`2017ApJ...848L...7C` | The Astrophysical Journal Letters 2017 | first author: Cortese, Luca | arXiv: 1709.07933 | DOI: 10.3847/2041-8213/aa8cc3

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, high_z_galaxies
- Question: Is the cold gas of massive star-forming galaxies at z~0.2 (HIGHz) molecular-dominated, as expected from rapid evolution of H2/HI with redshift, and is their ISM turbulent?  
  > "In order to determine whether Hi becomes so rapidly negligible beyond the very local Universe, we used the Atacama Large Millimeter Array (ALMA) to measure the H$_{2}$ masses of galaxies in the HIGHz sample" (Introduction)
- Target **Five HIGHz galaxies (AGC 191728, 242091, 242147, 249559, 252580)**: coordinates SDSS IDs e.g. J091957.00+013851.6, J140522.72+052814.6, J142735.69+033434.2, J144518.88+025012.3, J151337.28+041921.1  
  > "| 191728 | J091957.00+013851.6 | 0.1763 | 10.89 | 2.91 | 10.15 | $-$0.20 | 1.17 |" (Table 1); "We used ALMA to observe five HIGHz galaxies selected to span the range of sizes, Hi gas fractions and SFRs covered by the entire sample." (2.1 ALMA $^{12}$CO(1-0) observations); z/distance z_SDSS = 0.1754-0.2455  
  > "| 191728 | J091957.00+013851.6 | 0.1763 | 10.89 | 2.91 | 10.15 | $-$0.20 | 1.17 |" (Table 1); "We used ALMA to observe five HIGHz galaxies selected to span the range of sizes, Hi gas fractions and SFRs covered by the entire sample." (2.1 ALMA $^{12}$CO(1-0) observations); distance from SDSS redshift; flat cosmology Omega_M=0.3, Omega_L=0.7, H0=70  
  > "| 191728 | J091957.00+013851.6 | 0.1763 | 10.89 | 2.91 | 10.15 | $-$0.20 | 1.17 |" (Table 1); "We used ALMA to observe five HIGHz galaxies selected to span the range of sizes, Hi gas fractions and SFRs covered by the entire sample." (2.1 ALMA $^{12}$CO(1-0) observations)

## Data provenance

- ALMA projects: 2015.1.00405.S
- bands: _not stated_
- frequencies and spectral setup: four 1875 MHz spectral windows, one on 12CO(1-0) (91.3-96.8 GHz), three for continuum; ~3.0 km/s resolution  
  > "four 1875 MHz wide spectral windows, one centered at the expected frequency of the $^{12}$CO(1-0) emission (ranging between 91.3 and 96.8 GHz)" (2.1 ALMA $^{12}$CO(1-0) observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ~1.7 arcsec  
  > "a synthesized beam of $\sim$1.7 arcsec" (2.1 ALMA $^{12}$CO(1-0) observations)
- max recoverable scale: ~20 arcsec  
  > "The array configuration used is sensitive to extended emission up to $\sim$20$''$." (2.1 ALMA $^{12}$CO(1-0) observations)
- sensitivity: rms ~0.2-0.3 mJy/beam per 20 km/s channel  
  > "a typical rms noise per channel of $\sim$0.2-0.3 mJy beam$^{-1}$" (2.1 ALMA $^{12}$CO(1-0) observations)
- time on source: 150-270 minutes per source  
  > "The total time on source ranged between 150 and 270 minutes depending on the redshift of the source." (2.1 ALMA $^{12}$CO(1-0) observations)
- observing dates: 2016 March 5-19, Cycle 3  
  > "between 2016 March 5 and 19, during the ALMA observing Cycle 3" (2.1 ALMA $^{12}$CO(1-0) observations)
- pi or archival as stated: Program 2015.1.00405 (PI Catinella)  
  > "observed as part of program 2015.1.00405 (P.I. Catinella)" (2.1 ALMA $^{12}$CO(1-0) observations)
- Line: 12CO J=1-0 (not stated)
- Other facility **Arecibo**: HI single-dish spectra and HI masses  
  > "combine Atacama Large Millimeter/submillimeter Array and Arecibo single-dish observations" (abstract)
- Other facility **Keck II ESI**: Halpha long-slit spectroscopy for gas velocity dispersions  
  > "Optical long-slit spectroscopy of the five HIGHz galaxies presented here has been obtained with the Echellette Spectrograph and Imager" (2.2 Keck H$\alpha$ spectroscopy)
- External data: HIGHz sample properties and HI masses  
  > "galaxies in the HIGHz sample (cite: catinella08; highz)" (Introduction) [from Catinella & Cortese 2015 (cite: highz)]
- External data: COLD GASS local comparison sample  
  > "Local star-forming galaxies are from the COLD GASS survey ((cite: gass1; coldgass1), blue points)" (3 Results) [from (cite: gass1; coldgass1)]
- External data: COOL BUDHIES and CHILES samples at z~0.2 and 0.37  
  > "samples at redshifts $z\sim$ 0.2 and $\sim$ 0.37 are from the COOL BUDHIES (magenta triangles) and CHILES (green square) surveys" (3 Results) [from (cite: coolbudhies); (cite: chiles)]
- External data: PHIBSS z~1.5 galaxies  
  > "Black arrows show star-forming galaxies at $z\sim$1.5 from the PHIBSS survey (cite: phibbs2013)." (3 Results) [from (cite: phibbs2013)]
- External data: Main sequence relation  
  > "main sequence of star forming galaxies at each redshift of interest, as estimated by (cite: whitaker2012)" (3 Results) [from (cite: whitaker2012)]

## Processing

### Calibration

- pipeline or manual: standard ALMA pipeline in CASA  
  > "The data were reduced using the standard ALMA pipeline within the Common Astronomy Software Applications (CASA) package" (2.1 ALMA $^{12}$CO(1-0) observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Callisto, Ganymede, Titan, J0854+2006, J1337-1257 or J1550+0527  
  > "Callisto, Ganymede, Titan, J0854+2006, J1337$-$1257 or J1550+0527 being observed as flux density calibrator" (2.1 ALMA $^{12}$CO(1-0) observations)
- flux scale uncertainty: below 10%  
  > "providing an uncertainty below 10%" (2.1 ALMA $^{12}$CO(1-0) observations)
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: mask pixels below 3x rms of smoothed cube; moments from original cube; channels chosen by eye  
  > "pixels with intensity below three times the typical rms of the smoothed cube are masked" (2.1 ALMA $^{12}$CO(1-0) observations)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: cubes corrected for primary beam response  
  > "cleaned flux-calibrated cubes (corrected for variations in the primary beam response)" (2.1 ALMA $^{12}$CO(1-0) observations)
- array combination: _not stated_
- smoothing: 20 km/s channel width; Gaussian smoothing of beam width for masking  
  > "cubes are smoothed using a Gaussian filter of width equal to the synthesized beam" (2.1 ALMA $^{12}$CO(1-0) observations)
- final beam: ~1.7 arcsec  
  > "a synthesized beam of $\sim$1.7 arcsec" (2.1 ALMA $^{12}$CO(1-0) observations)
- final rms: ~0.2-0.3 mJy/beam per channel  
  > "a typical rms noise per channel of $\sim$0.2-0.3 mJy beam$^{-1}$" (2.1 ALMA $^{12}$CO(1-0) observations)

### Inherited from earlier work

- CO luminosity formula  
  > "Integrated $^{12}$CO(1-0) luminosities have been estimated from observed flux densities ($S_{CO}$ in Jy km s$^{-1}$) as in (cite: solomon97)" (2.1 ALMA $^{12}$CO(1-0) observations) [from (cite: solomon97)]

### Not stated but needed to reproduce (our reading)

- tclean parameters (weighting, robust, deconvolver, cell and image size, threshold)
- CASA version and pipeline version
- Continuum subtraction and line-free channels
- How HI masses and spectra were taken or computed from Arecibo
- Exact velocity range of channels used in moment maps
- How SFRs and stellar masses of HIGHz were derived
- Uncertainties on S_CO and masses
- Exact rest frequency used

## Analysis recipe

1. **Make CO cubes and moment maps**: Pipeline-reduced cleaned cubes at 20 km/s; smooth to beam, mask at 3 rms, apply mask to original cube for moments 0-2  
  > "moment maps are obtained from the original cube by including only those pixels that are not masked in the smoothed version." (2.1 ALMA $^{12}$CO(1-0) observations)
   - software: CASA
   - parameter: 3 sigma mask on smoothed cube; channels chosen by visual inspection  
  > "The velocity channels included in each moment map have been chosen via visual inspection of each cube slice." (2.1 ALMA $^{12}$CO(1-0) observations)
   - fitting: _not stated_
   - validation: Alternative methods (2 sigma mask on unsmoothed cube, no mask) agree within 10%  
  > "All of these methods provide flux densities within 10% of the value obtained with our preferred technique described above." (2.1 ALMA $^{12}$CO(1-0) observations)
2. **Derive CO luminosity and H2 mass**: L_CO = 3.25e7 S_CO nu^-2 D_L^2 (1+z)^-3; multiply by alpha_CO  
  > "L_{CO}=3.25 \times 10^{7} S_{CO} \nu^{-2} D_{L}^{2} (1+z)^{-3}" (2.1 ALMA $^{12}$CO(1-0) observations)
   - assumption: Galactic alpha_CO = 3.2 Msun (K km/s pc^2)^-1, no helium; same for all samples  
  > "assuming a Galactic CO-to-H$_{2}$ conversion factor of 3.2 $\,\rm M_{\ensuremath{\odot}}$(K km s$^{-1}$ pc$^{2}$)$^{-1}$" (2.1 ALMA $^{12}$CO(1-0) observations)
   - fitting: _not stated_
   - validation: _not stated_
3. **Compare H2/HI with other samples**: Compute M_H2/M_HI and total gas (x1.3 for helium) fractions; compare with COLD GASS, COOL BUDHIES, CHILES, PHIBSS  
  > "the total (molecular plus atomic, including a factor of 1.3 to account for the contribution of helium) gas-to-stellar mass ratio as a function of stellar mass" (3 Results)
   - assumption: PHIBSS plotted as lower limits M_H2/M_HI >= 2  
  > "we plot PHIBSS galaxies as lower limits assuming $M_{H_{2}}/M_{HI}\geq$2" (3 Results)
   - fitting: _not stated_
   - validation: _not stated_
4. **Measure CO and Halpha velocity dispersions**: CO sigma from moment-2 maps at pixels overlapping Keck slit; Halpha Gaussian fits per 0.15 arcsec pixel, corrected for instrumental and redshift broadening  
  > "fit it with a Gaussian profile, rejecting fits with uncertainties in $\sigma$ greater than 15 km s$^{-1}$" (2.2 Keck H$\alpha$ spectroscopy)
   - software: IRAF
   - fitting: Gaussian profile fit per spatial pixel  
  > "for each spatial pixel (0.15$''$) we extracted a spectrum of the H$\alpha$ line and fit it with a Gaussian profile" (2.2 Keck H$\alpha$ spectroscopy)
   - validation: Other hydrogen and forbidden lines fit as a check  
  > "we also measured other hydrogen and forbidden line profiles as a verification of our H$\alpha$ fits" (2.2 Keck H$\alpha$ spectroscopy)

## Software

- **CASA** : ALMA pipeline data reduction  
  > "The data were reduced using the standard ALMA pipeline within the Common Astronomy Software Applications (CASA) package" (2.1 ALMA $^{12}$CO(1-0) observations)
- **IRAF** : Reduction of Keck ESI spectra  
  > "The spectra were reduced with the standard processing tools in IRAF" (2.2 Keck H$\alpha$ spectroscopy)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| S_CO of AGC191728 | 2.91 | not stated | Jy km/s | 1 | / 191728 / J091957.00+013851.6 / 0.1763 / 10.89 / 2.91 / 10.15 / $-$0.20 / 1.17 / |
| log M_H2/M_HI range of the five HIGHz galaxies | -1.04 to -0.06 | not stated | dimensionless | 3 | / 252580 / J151337.28+041921.1 / 0.1754 / 10.78 / 0.74 / 9.55 / $-$1.04 / 0.79 / |
| log M_H2 range | 9.55-10.35 | not stated | log Msun | 2 | / 242147 / J142735.69+033434.2 / 0.2455 / 11.26 / 2.32 / 10.35 / $-$0.46 / 1.43 / |
| CO velocity dispersion | ~10-20 | not stated | km/s | 4 | The velocity dispersion of the CO component of HIGHz systems is $\sim$10-20 km s$^{-1}$ |
| Halpha velocity dispersion | ~20-40 | not stated | km/s | 4 | the H$\alpha$-emitting gas has dispersions $\sim$20-40 km s$^{-1}$ |

## Qualitative findings

- HIGHz galaxies are HI-dominated despite ~1e10 Msun of H2.  
  > "All HIGHz galaxies observed by ALMA are Hi-dominated, despite harboring $\sim$10$^{10}$$\,\rm M_{\ensuremath{\odot}}$ of H$_{2}$." (3 Results)

## Claim tuples

- H: H2/HI rises rapidly with redshift so gas at z~0.2 is molecular-dominated | E: ALMA CO(1-0) of 5 HIGHz galaxies combined with Arecibo HI | R: All five have log M_H2/M_HI < 0 | F: H2/HI at z~0.2 similar to local main-sequence disks; HI dominates over the past 3 Gyr | **supported**
- H: High total gas fractions drive high ISM turbulence | E: CO moment-2 and Keck Halpha velocity dispersions | R: CO ~10-20 km/s, Halpha ~20-40 km/s | F: High gas fractions do not necessarily imply high turbulence | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Milky Way alpha_CO justified by massive, metal-rich galaxies; conservative since lower alpha would lower H2/HI  
  > "Given that all our galaxies are massive and thus likely metal-rich systems, we can safely assume that a Milky Way conversion factor is a good assumption for our sample." (2.1 ALMA $^{12}$CO(1-0) observations)
- How they decided it was enough: _not stated_
- Limitation (authors): Only 11 galaxies with differing selection, so average evolution cannot be quantified  
  > "Unfortunately, with just 11 galaxies and very different selection criteria, it is impossible to quantify any evolution in the *average* molecular-to-atomic hydrogen ratio." (3 Results)
- Limitation (authors): Velocity dispersions close to instrumental resolution, may be overestimated  
  > "we cannot exclude that our measurements overestimate the real value" (3 Results)
- Caveat (inferred, ours): Only five galaxies, no CO uncertainties given
- Caveat (inferred, ours): Single alpha_CO assumed; no uncertainty propagation
- Caveat (inferred, ours): Beam smearing affects dispersions at 1.7 arcsec
- Caveat (inferred, ours): HI from Arecibo single dish, not resolved

## Reproducibility

- Data public (paper): ALMA project code given; public availability not explicitly stated  
  > "ADS/JAO.ALMA #2015.1.00405.S" (Acknowledgments)
- Products in archive: _not stated_
- Missing: HI masses from Arecibo (from Catinella & Cortese 2015)
- Missing: Detailed imaging parameters
- Missing: Channel ranges for moment maps
- Data volume (inferred): ~tens of GB (5 targets, Band 3, 4 spws)
- Score (inferred): 3/5, Simple recipe and tabulated results, but imaging settings, uncertainties and HI inputs are missing.
- Rediscovery candidate: no, Imaging details and HI data are not given in the paper, and uncertainties are missing.

## Links

- Method: Solomon et al. 1997 (cite: solomon97) (CO luminosity formula)
- Companion: Catinella & Cortese 2015 (cite: highz) (HIGHz sample and HI data)
- Related: HIGHz
- Related: COLD GASS
- Related: COOL BUDHIES
- Related: CHILES
- Related: PHIBSS

## Checks

```json
{
 "quotes": 57,
 "quotes_ok": 57,
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
  "facts": 71,
  "stated": 44,
  "rate": 0.62
 },
 "evidence_ok": true
}
```
