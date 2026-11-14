# A 10<SUP>10</SUP> Solar Mass Flow of Molecular Gas in the A1835 Brightest Cluster Galaxy

`2014ApJ...785...44M` | The Astrophysical Journal 2014 | first author: McNamara, B. R. | arXiv: 1309.0013 | DOI: 10.1088/0004-637X/785/1/44

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: galaxy_clusters_and_sz, nearby_galaxies
- Question: Does radio-mechanical AGN feedback in the Abell 1835 BCG affect its molecular gas, e.g. by driving a molecular outflow?  
  > "Here we examine the effects of feedback on the molecular gas located near the nucleus of the Abell 1835 BCG." (Introduction)
- Target **Abell 1835 BCG**: coordinates 14 01 02.083, +02 52 42.649 (continuum source)  
  > "At the emission line redshift z = 0.252 (Crawford et al. 1999), 1 arcsec = 3.9 kpc." (Introduction); "A central continuum source is detected in both bands at position $14~01~02.083$, $+02~52~42.649$" (3 Observations); z/distance z = 0.252; 1 arcsec = 3.9 kpc  
  > "At the emission line redshift z = 0.252 (Crawford et al. 1999), 1 arcsec = 3.9 kpc." (Introduction); "A central continuum source is detected in both bands at position $14~01~02.083$, $+02~52~42.649$" (3 Observations); distance from emission line redshift from Crawford et al. 1999  
  > "At the emission line redshift z = 0.252 (Crawford et al. 1999), 1 arcsec = 3.9 kpc." (Introduction); "A central continuum source is detected in both bands at position $14~01~02.083$, $+02~52~42.649$" (3 Observations)

## Data provenance

- ALMA projects: 2011.0.00374.S
- bands: Band 3 (92 GHz) and Band 7 (276 GHz)  
  > "We obtained Early Science observations of the BCG with ALMA at 92 GHz (band 3) and 276 GHz (band 7)." (Observations)
- frequencies and spectral setup: 1.875 GHz per spw, two spw per sideband, ~7 GHz total; 0.488 MHz channels, binned to 20 km/s  
  > "A bandwidth of $1.875\GHz$ per spectral window and two spectral windows per sideband provided a total frequency range of $\sim{7}\GHz$." (Observations); "Channels were binned together to improve the S/N ratio, yielding a final resolution of $20\kmps$." (Observations)
- continuum bandwidth: _not stated_
- arrays: Cycle 0 extended array, on average twenty 12 m dishes  
  > "The extended array available for Cycle 0 included on average twenty 12 metre dishes" (Observations)
- configurations: _not stated_
- baselines: up to ~400 m  
  > "Baselines extended to $\sim400\m$." (Observations)
- angular resolution: 0.5 arcsec at CO(3-2), 1.5 arcsec at CO(1-0)  
  > "which provided a spatial resolution of 0.5 arcsec in the CO (3-2) transition and 1.5 arcsec at the CO (1-0) transition." (Observations)
- max recoverable scale: _not stated_
- sensitivity: rms in line-free channels 0.6 mJy (CO 1-0), 1.6 mJy (CO 3-2)  
  > "The rms noise in the line free channels was $0.6~\rm mJy$ at CO(1-0) and $1.6~\rm mJy$ at CO(3-2)." (Observations)
- time on source: 60 min in band 3 and 60 min in band 7  
  > "The exposures, totaling 60 minutes in band 3 and 60 minutes in band 7" (Observations)
- observing dates: 2012 March 27 to 2012 April 24  
  > "were made between 2012 March 27 and 2012, April 24." (Observations)
- pi or archival as stated: _not stated_
- Line: CO J=1-0 (not stated)
- Line: CO J=3-2 (not stated)
- Other facility **HST**: R-band and Far UV images  
  > "R-band and Far UV images taken with the Hubble Space Telescope (O’Dea et al. 2010) are presented in Fig. 2." (4.2 Central Molecular Gas and Star Formation)
- Other facility **Chandra**: X-ray image showing cavities  
  > "A Chandra X-ray image with a similar box superposed is shown in Fig. 2." (4.2 Central Molecular Gas and Star Formation)
- External data: Far-UV luminosity L_FUV=1.85e43 erg/s  
  > "Based on the far UV flux from O’Dea et al. (2010), $L_{\rm FUV}=1.85 \times 10^{43}~\rm erg~s^{-1}$" (5.2 Driving a Molecular Outflow by Radiation Pressure or Supernovae) [from O’Dea et al. (2010)]
- External data: Star formation rate 100-180 Msun/yr  
  > "upward of $100-180~\rm M_\odot ~yr^{-1}$ (M06, Egami et al. 2006, Donahue et al. 2011, )" (4.2 Central Molecular Gas and Star Formation) [from M06, Egami et al. 2006, Donahue et al. 2011]
- External data: Emission-line redshift z=0.252  
  > "At the emission line redshift z = 0.252 (Crawford et al. 1999), 1 arcsec = 3.9 kpc." (Introduction) [from Crawford et al. 1999]

## Processing

### Calibration

- pipeline or manual: CASA following ALMA science support team processing scripts  
  > "following the detailed processing scripts provided by the ALMA science support team." (Observations)
- casa version: CASA 3.3  
  > "The observations were calibrated using the CASA software (version 3.3)" (Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Mars and Titan (flux); 3C 279 bandpass; J1332+0200 phase  
  > "The quasar 3C 279 was observed for bandpass calibration and observations of Mars and Titan provided absolute flux calibration." (Observations)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA CLEAN  
  > "The continuum-subtracted images were reconstructed using the CASA task CLEAN" (Observations)
- deconvolver: _not stated_
- weighting robust: Briggs, robustness 0.5  
  > "assuming Briggs weighting with a robustness parameter of 0.5" (Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: simple polygon mask per channel  
  > "with a simple polygon mask applied to each channel" (Observations)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 1.7x1.3 arcsec PA -84.1 deg (CO 1-0); 0.60x0.48 arcsec PA -80.0 deg (CO 3-2)  
  > "This provided a synthesized beam of $1.7\ensuremath{''}\times1.3\ensuremath{''}$ at a PA of $-84.1^{\circ}$ at CO(1-0)" (Observations)
- final rms: 0.6 mJy (CO 1-0), 1.6 mJy (CO 3-2)  
  > "The rms noise in the line free channels was $0.6~\rm mJy$ at CO(1-0) and $1.6~\rm mJy$ at CO(3-2)." (Observations)

### Inherited from earlier work

- Star formation rate and X-ray cavity power taken from earlier work  
  > "is dwarfed by its mechanical power, $L_{\rm mec} \simeq 10^{45}~\rm erg s^{-1}$(M06)" (Introduction) [from McNamara et al. 2006 (M06)]
- Galactic XCO adopted  
  > "is the average Galactic value (reviewed by Bolatto et al. 2013)" (4.1 Spectra) [from Bolatto et al. 2013]

### Not stated but needed to reproduce (our reading)

- Line-free channels and continuum-subtraction method/order
- Clean threshold, cell and image size
- How the CO(3-2) mass or CO(1-0) wing integration velocity ranges were chosen
- Grid box positions for spectra
- Luminosity distance value used in mass equation
- Flux calibration uncertainty
- Details of the 2D Gaussian central-emission subtraction

## Analysis recipe

1. **Calibrate and image CO cubes and continuum**: CASA calibration per ALMA scripts, CLEAN of continuum-subtracted cubes, continuum from line-free channels  
  > "Images of the continuum emission were also produced with CLEAN by averaging channels free of any line emission." (Observations)
   - software: CASA
   - parameter: Briggs robust 0.5, polygon mask, 20 km/s channels  
  > "assuming Briggs weighting with a robustness parameter of 0.5" (Observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **Fit total spectra and derive molecular gas mass**: Single Gaussian fit to continuum-subtracted spectra; mass from CO(1-0) integral with XCO  
  > "Each spectral profile was fitted with a single gaussian after the continuum was subtracted." (4.1 Spectra)
   - assumption: XCO = 2e20 cm^-2 (K km/s)^-1, Galactic  
  > "$\rm X_{CO} = 2 \times 10^{20}~ \rm cm^{-2} (K~ km ~s^{-1})^{-1}$" (4.1 Spectra)
   - fitting: single Gaussian  
  > "Each spectral profile was fitted with a single gaussian after the continuum was subtracted." (Analysis, Spectra)
   - validation: _not stated_
3. **Map velocity field on grids and isolate high-velocity gas**: Grid of spectra with Gaussian fits per box; 2D Gaussian fitted and subtracted per channel in CO(1-0) to remove central emission; integrate wings  
  > "A two dimensional gaussian profile has been fitted to and subtracted from each channel in order to remove the central emission from the contour map." (4.3 Velocity Field of the Molecular Gas)
   - fitting: Gaussian profile fits  
  > "The mean line of sight velocities measured with gaussian profile fits are indicated in each grid box." (Analysis, Velocity Field of the Molecular Gas)
   - validation: _not stated_
4. **Estimate outflow rate and disk dynamics**: Outflow mass divided by buoyant rise or gas travel time; Toomre Q, pressure and scale height analytic estimates  
  > "We estimate it by dividing the mass of the outflowing molecular gas by either the time for the bubbles to rise by buoyancy" (5.3 A Radio-AGN Driving a Molecular Outflow)
   - assumption: gas to dust ratio 100; R_e=2 kpc encloses half the mass; v_c=400 km/s  
  > "We have also scaled the circular velocity at that radius to $400~\rm km~s^{-1}$." (5.4 Dynamics of the Central Molecular Gas)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 3.3: calibration and CLEAN imaging  
  > "The observations were calibrated using the CASA software (version 3.3)" (Observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Total molecular gas mass | 4.9e10 | ±0.2e10 | Msun | 2 | This expression yields a total molecular gas mass of $4.9 \pm 0.2 \times 10^{10} ~M_{\odot}$. |
| CO(1-0) line integral | 3.6 | ±0.2 | Jy km/s | 2 | The emission integral at CO (1-0) is $3.6 \pm 0.2~ \rm Jy ~km ~s^{-1}$. |
| Central line FWHM | 130 | ±5 | km/s | 2 | $\rm FWHM = 130 \pm 5~ km ~s^{-1}$ (corrected for instrumental broadening) |
| Continuum flux band 3 | 1.26 | ±0.03 | mJy | 1 | fluxes $1.26 \pm 0.03 ~\rm mJy$ in band 3 and $0.7 \pm 0.1 \rm~ mJy$ in band 7 |
| Continuum flux band 7 | 0.7 | ±0.1 | mJy | 1 | fluxes $1.26 \pm 0.03 ~\rm mJy$ in band 3 and $0.7 \pm 0.1 \rm~ mJy$ in band 7 |
| Outflowing wing flux integral total | 0.7 | ±0.2 | Jy km/s | 3 | giving a total flux integral of $0.7 \pm 0.2~
~\rm Jy~km ~s^{-1}$. |
| Outflowing molecular gas mass | 1.0e10 | ±0.3e10 | Msun | 3 | They correspond to a molecular hydrogen mass of $1.0\pm0.3\times 10^{10}~ \rm M_\odot$. |
| Outflow rate | ~200-300 | not stated | Msun/yr | 4 | They imply an outflow rate of $\sim 200-300 ~\rm M_\odot ~yr^{-1}$. |
| Toomre Q | 0.43 | not stated | dimensionless | 4 | \approx0.43 |
| Dynamical pressure | 1.7e-8 | not stated | dyne cm^-2 | 4 | $$\begin{equation}
p_{\rm dyn}={\pi\over2} G\Sigma_g^2\approx1.7\times10^{-8}{\rm dyne}~\rm cm^{-2}. |

## Qualitative findings

- High-velocity gas avoids the nucleus and velocities rise with radius, consistent with a bipolar outflow aligned toward the X-ray cavities  
  > "Taken together, the velocity patterns in both CO (3-2) and CO (1-0) emission are consistent with an accelerating, bipolar outflow of molecular gas." (5.1 Bipolar Outflow or Inflow of Molecular Gas?)

## Claim tuples

- H: Molecular gas in the A1835 BCG is being driven out by radio-AGN bubbles | E: CO(3-2) and CO(1-0) velocity-field mapping in grids | R: ~1e10 Msun at -250 to +480 km/s, 3-10 kpc N-NW and E-SE, velocity rising with radius | F: Consistent with bipolar outflow driven by radio jets or buoyant cavities, although inflow is not excluded | **partially**
- H: The BCG hosts a massive molecular reservoir in a turbulent, nearly face-on disk | E: CO line fits and Toomre analysis | R: 4.9e10 Msun, FWHM 130 km/s, Q≈0.43 | F: Gas may be supported in a rotating turbulent disk, marginally unstable | **partially**
- H: Radiation pressure or supernovae drive the outflow | E: Energy and momentum budget comparison | R: Radiation pressure is too weak by more than 3 orders of magnitude; supernovae power is comparable but coupling is unlikely | F: The radio AGN is the most plausible driver | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Combine band 3 and 7 for sensitivity on large scales plus high resolution on the nucleus  
  > "This combination yielded a sharp image of the molecular gas near the nucleus at CO (3-2), and sensitivity on larger spatial scales at CO (1-0)." (Observations)
- Alternative: Inflow from the cooling flow was considered but disfavored since the highest speed gas avoids the nucleus  
  > "The highest speed gas shown in Fig. 5 avoids the nucleus." (5.1 Bipolar Outflow or Inflow of Molecular Gas?)
- How they decided it was enough: _not stated_
- Limitation (authors): Emission-only data cannot distinguish inflow from outflow  
  > "the ALMA observations alone cannot discriminate with certainty between inflow and outflow." (5.1 Bipolar Outflow or Inflow of Molecular Gas?)
- Limitation (authors): XCO is the prime mass uncertainty  
  > "is the prime uncertainty in our mass estimates." (The CO to H2 Conversion Factor)
- Caveat (inferred, ours): Mass depends on Galactic XCO and the assumption that CO(3-2) and CO(1-0) trace the same dynamics
- Caveat (inferred, ours): Wing integrals are sensitive to continuum subtraction; the redshifted wing is only 2-3 sigma in places
- Caveat (inferred, ours): Outflow rate is poorly defined and depends on assumed timescales
- Caveat (inferred, ours): Single-pointing, low S/N Cycle 0 data limit kinematic modeling

## Reproducibility

- Data public (paper): ALMA Cycle 0 project cited, which is archival  
  > "The paper makes use of the following ALMA data: ADS/JAO.ALMA#2011.0.00374.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Line-free channel ranges
- Missing: Velocity ranges for wing integrals
- Missing: Clean parameters beyond robust
- Missing: Grid box definitions
- Missing: Distance used in the mass formula
- Data volume (inferred): ~10-30 GB raw for two bands in Cycle 0
- Score (inferred): 3/5, Public Cycle 0 data and a simple recipe with a mass formula, but many processing and integration details are missing.
- Rediscovery candidate: yes, Data are public and the key results (CO flux, gas mass, FWHM) are numeric and recoverable with CASA, though the outflow requires care.

## Links

- Method: Bolatto et al. 2013 (XCO value)
- Companion: Russell et al. 2013 (Companion ALMA study of Abell 1664)
- Companion: McNamara et al. 2006 (M06) (Earlier X-ray, star formation and cavity power results)

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
 "numeric_results": 10,
 "numeric_problems": 0,
 "fill": {
  "facts": 70,
  "stated": 43,
  "rate": 0.614
 },
 "evidence_ok": true
}
```
