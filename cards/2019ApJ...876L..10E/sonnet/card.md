# A Radio Source Coincident with the Superluminous Supernova PTF10hgi: Evidence for a Central Engine and an Analog of the Repeating FRB 121102?

`2019ApJ...876L..10E` | The Astrophysical Journal Letters 2019 | first author: Eftekhari, T. | arXiv: 1901.10479 | DOI: 10.3847/2041-8213/ab18a5

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: transients, other
- Question: What is the origin of the radio source detected at the position of the superluminous supernova PTF10hgi, and does it indicate a central engine analogous to the FRB121102 persistent source?  
  > "We investigate various scenarios for the origin of the radio emission: star formation activity, an active galactic nucleus, and a non-relativistic supernova blastwave." (abstract)
- Target **PTF10hgi**: coordinates RA 16h37m47.071s, Dec +06d12m31.88s (J2000) (radio source)  
  > "We identify a point source with a flux density of $F_\nu = 47.3\pm 7.1 \mu$Jy ($6.7\sigma$) at R.A.=${\rm 16^h37^m47^s.071}$, decl.=$+06^\circ12'31''.88$ (J2000)" (2.1 VLA Continuum Observations); "for a luminosity distance of 465 Mpc" (3 Origin of the Radio Emission); z/distance z=0.098; d_L = 465 Mpc  
  > "We identify a point source with a flux density of $F_\nu = 47.3\pm 7.1 \mu$Jy ($6.7\sigma$) at R.A.=${\rm 16^h37^m47^s.071}$, decl.=$+06^\circ12'31''.88$ (J2000)" (2.1 VLA Continuum Observations); "for a luminosity distance of 465 Mpc" (3 Origin of the Radio Emission); distance from redshift from Inserra2013; Perley2016a; DeCia2018, with H0=67.7 cosmology  
  > "We identify a point source with a flux density of $F_\nu = 47.3\pm 7.1 \mu$Jy ($6.7\sigma$) at R.A.=${\rm 16^h37^m47^s.071}$, decl.=$+06^\circ12'31''.88$ (J2000)" (2.1 VLA Continuum Observations); "for a luminosity distance of 465 Mpc" (3 Origin of the Radio Emission)

## Data provenance

- ALMA projects: 2017.1.00280.S
- bands: Band 3 (~100 GHz)  
  > "We obtained millimeter observations with the Atacama Large Millimeter/submillimeter Array (ALMA) in Band 3 ($\sim 100$ GHz) on 2018 January 11" (2.3 ALMA Observations)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: 3 sigma limit F_nu(100 GHz) <~ 44 uJy  
  > "with a $3\sigma$ limit of $F_\nu(100\,{\rm GHz})\lesssim 44 \ \rm \mu$Jy" (2.3 ALMA Observations)
- time on source: 22.2 minutes  
  > "with a total on-source integration time of 22.2 minutes" (2.3 ALMA Observations)
- observing dates: 2018 January 11  
  > "on 2018 January 11 with a total on-source integration time of 22.2 minutes" (2.3 ALMA Observations)
- pi or archival as stated: _not stated_
- Other facility **VLA**: C-band (5 and 7 GHz) continuum detection of the radio source plus phased-array FRB search  
  > "We observed the location of PTF10hgi with the Karl G. Jansky Very Large Array (VLA), in the B configuration, on 2017 December 15 UT." (2.1 VLA Continuum Observations)
- Other facility **HST WFC3/UVIS**: F336W image of host galaxy for astrometry  
  > "The galaxy was imaged in the F336W filter (corresponding to a rest-frame wavelength of $3055$ Å, at the redshift of PTF10hgi) for two orbits" (2.4 Hubble Space Telescope Observations)
- Other facility **Magellan IMACS**: g-band image used for Gaia astrometric tie  
  > "wide-field $g$-band image centered on the host galaxy from the Inamori Magellan Areal Camera and Spectrograph (IMACS) on the Magellan Baade 6.5-m telescope" (2.5 Astrometry)
- External data: Host photometry used for Prospector SED modeling  
  > "we use the magnitudes reported by (cite: Lunnan2014) and (cite: Perley2016a)" (3.1 Star formation Activity) [from Lunnan2014; Perley2016a]
- External data: Swift/XRT upper limit L_X <~ 4e42 erg/s  
  > "a *Swift*/XRT upper limit of $L_X\lesssim 4\times 10^{42}$ erg s$^{-1}$ (cite: Margutti2018)" (3.2 Active Galactic Nucleus) [from Margutti2018]
- External data: PTF10hgi ejecta and engine parameters from light curve fit  
  > "a spin of $P = 4.8$ ms, a magnetic field of $B = 2\times 10^{14}$ G, an ejecta mass of $M_{\rm ej} = 2.2 \ \rm M_{\odot}$" (3.4 Magnetar Nebula) [from Nicholl2017b]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA standard imaging from ALMA data products  
  > "Here we report results using the ALMA data products which utilize standard imaging techniques within CASA." (2.3 ALMA Observations)
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 0.5  
  > "Briggs weighting (cite: Briggs1995) with a robust parameter of 0.5" (2.3 ALMA Observations)
- uv taper: _not stated_
- cell size: 0.03 arcsec  
  > "The field is imaged using 2400 pixels and an image scale of 0.03 arcsec per pixel" (2.3 ALMA Observations)
- image size: 2400 pixels  
  > "The field is imaged using 2400 pixels and an image scale of 0.03 arcsec per pixel" (2.3 ALMA Observations)
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Not stated but needed to reproduce (our reading)

- ALMA array configuration, baselines and resolution
- CASA version and whether pipeline products were used
- ALMA flux, bandpass and phase calibrators
- Spectral setup and continuum bandwidth
- Final synthesized beam and rms
- How the 3 sigma limit was measured

## Analysis recipe

1. **Image ALMA Band 3 and derive upper limit**: MFS Briggs imaging in CASA; non-detection at VLA position gives 3 sigma limit  
  > "We do not detect emission at the position of the VLA source, with a $3\sigma$ limit of $F_\nu(100\,{\rm GHz})\lesssim 44 \ \rm \mu$Jy." (2.3 ALMA Observations)
   - software: CASA
   - parameter: robust 0.5, 2400 pixels at 0.03 arcsec  
  > "The field is imaged using 2400 pixels and an image scale of 0.03 arcsec per pixel, MFS, Briggs weighting" (2.3 ALMA Observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **Constrain radio-to-mm spectral index**: Compare 6 GHz detection with 100 GHz limit  
  > "This indicates a radio to mm spectral index of $\alpha\lesssim 0$." (2.3 ALMA Observations)
   - fitting: _not stated_
   - validation: _not stated_
3. **Use ALMA limit to constrain magnetar nebula models**: Modify FRB121102 nebula model to match 6 GHz luminosity and 100 GHz limit  
  > "we modify the best fit model parameters for FRB121102 to fit the observed luminosity and upper limit at 6 and 100 GHz, respectively." (3.4 Magnetar Nebula)
   - software: CLOUDY
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : VLA and ALMA imaging  
  > "We processed the data in the Common Astronomy Software Application (CASA) software package (cite: McMullin2007) using standard imaging techniques." (2.1 VLA Continuum Observations)
- **pwkit** : fit VLA flux density and position  
  > "We fit for the flux density and source position using the `imtool` program as part of the `pwkit`[^1] package" (2.1 VLA Continuum Observations)
- **Prospector** : host galaxy SED modeling  
  > "we independently model the host SED using the `Prospector` software package (cite: Leja2017)" (3.1 Star formation Activity)
- **Boxfit** v2: off-axis jet afterglow models  
  > "using the two-dimensional relativistic hydrodynamical code `Boxfit v2` (cite: vanEerten2012)" (3.3.2 Off-Axis Jet)
- **CLOUDY** : ejecta ionization structure and free-free transparency  
  > "using the photoionization code `CLOUDY` (cite: Ferland2013)" (3.4 Magnetar Nebula)
- **PRESTO** : RFI masking and single pulse search of phased-array data  
  > "We searched each file for RFI using `PRESTO`’s `rfifind` (cite: Ransom2001)" (2.2 VLA Phased-Array Observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| ALMA 100 GHz flux density limit (3 sigma) | 44 | not stated | uJy | 1 | with a $3\sigma$ limit of $F_\nu(100\,{\rm GHz})\lesssim 44 \ \rm \mu$Jy |
| radio to mm spectral index | <~ 0 | not stated | dimensionless | 2 | This indicates a radio to mm spectral index of $\alpha\lesssim 0$. |
| VLA 6 GHz flux density | 47.3 | 7.1 | uJy | 0 | We identify a point source with a flux density of $F_\nu = 47.3\pm 7.1 \mu$Jy ($6.7\sigma$) |
| radio-inferred SFR | 2.3 | 0.3 | Msun/yr | 0 | We find a radio-inferred SFR of $2.3\pm 0.3$ M$_{\odot}$ yr$^{-1}$. |

## Qualitative findings

- Star formation, AGN and SN blastwave origins are unlikely; a magnetar wind nebula or off-axis jet is consistent with the data.  
  > "We show that the properties of the radio source are consistent with a magnetar wind nebula or an off-axis jet, indicating the presence of a central engine." (abstract)

## Claim tuples

- H: The radio source is powered by a central engine, analogous to the FRB121102 persistent source | E: VLA 6 GHz detection, ALMA 100 GHz limit, and models of star formation, AGN, blastwave, jet and magnetar nebula | R: Conventional origins require unusual parameters; the nebula model fits the luminosity, the ALMA limit and the transparency timescale | F: A magnetar nebula or off-axis jet is plausible, but the origin is not conclusive | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Star formation, AGN, spherical SN ejecta and continuously bursting source considered unlikely  
  > "We show that an origin due to star formation activity, an active galactic nucleus (AGN), an off-axis relativistic jet, or a spherical non-relativistic outflow are all unlikely" (3 Origin of the Radio Emission)
- How they decided it was enough: _not stated_
- Limitation (authors): ALMA 100 GHz limit is too shallow to constrain a star formation origin  
  > "Our ALMA non-detection at 100 GHz does not provide meaningful constraints on a star formation origin" (3.1 Star formation Activity)
- Caveat (inferred, ours): Single-epoch, single-frequency detection at 6.7 sigma
- Caveat (inferred, ours): ALMA limit is shallow and adds little constraint
- Caveat (inferred, ours): Chance coincidence with a background source not quantified

## Reproducibility

- Data public (paper): ALMA project code given in acknowledgments; public status not stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2017.1.00280.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: ALMA calibration and array details
- Missing: CASA version
- Missing: Prospector priors and settings
- Missing: Details of the nebula model grid
- Data volume (inferred): ALMA Band 3 short track, likely a few GB
- Score (inferred): 3/5, ALMA role is a minor upper limit with sparse processing detail, though imaging parameters are given.
- Rediscovery candidate: no, ALMA contributes only a non-detection and its processing is incompletely described; the main results come from VLA and models.

## Links

- Method: Margalit2018a (magnetar nebula free-free transparency prescription)
- Method: Margalit2018b (FRB121102 nebula model scaled to PTF10hgi)
- Companion: Eftekhari et al. in prep. (VLA and ALMA survey of SLSNe and LGRBs)
- Related: VLA/17B-171
- Related: HST GO-15140

## Checks

```json
{
 "quotes": 42,
 "quotes_ok": 42,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 4,
 "numeric_problems": 0,
 "fill": {
  "facts": 68,
  "stated": 32,
  "rate": 0.471
 },
 "evidence_ok": true
}
```
