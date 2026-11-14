# ALMA observations of 99 GHz free-free and H40α line emission from star formation in the centre of NGC 253

`2015MNRAS.450L..80B` | Monthly Notices of the Royal Astronomical Society 2015 | first author: Bendo, G. J. | arXiv: 1504.02142 | DOI: 10.1093/mnrasl/slv053

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: nearby_galaxies, star_formation
- Question: Use ALMA 99 GHz free-free continuum and H40alpha emission to derive electron temperature, photoionizing photon rate, SFR and dust attenuation in the centre of NGC 253  
  > "we present ALMA observations of free-free continuum emission and H40$\alpha$ emission at 99.02 GHz from the centre of NGC 253 that we use to derive star formation rates (SFRs) as well as the electron temperature ($T_e$) of the gas." (Introduction)
- Target **NGC 253**: coordinates _not stated_; z/distance 3.44±0.26 Mpc  
  > "assuming a distance of $3.44\pm0.26$ Mpc (based on the average of distances measured by (cite: dalcanton09))" (2 Data); distance from average of distances measured by Dalcanton et al. 2009  
  > "assuming a distance of $3.44\pm0.26$ Mpc (based on the average of distances measured by (cite: dalcanton09))" (2 Data)

## Data provenance

- ALMA projects: 2011.0.00172.S, 2011.0.00061.S
- bands: _not stated_
- frequencies and spectral setup: Spectral window centred at 98.54 GHz sky frequency, 3840 channels of 488 kHz (1.5 km/s), both polarisations  
  > "was centered at a sky frequency of 98.54 GHz, contained 3840 channels each with a width of 488 kHz (1.5 km s$^{-1}$), and included both polarisations" (2 Data)
- continuum bandwidth: _not stated_
- arrays: Cycle 0, 14-20 antennas operational  
  > "Only 14-20 antennas were operational." (2 Data)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 1.9x1.6 arcsec (~30 pc)  
  > "The full-width at half maximum (FWHM) of the reconstructed beam is $1.9\times1.6$ arcsec" (2 Data)
- max recoverable scale: cannot recover >20 arcsec structures  
  > "we lack the *uv* coverage to recover $>$20 arcsec structures" (2 Data)
- sensitivity: Noise per 3.9 MHz channel: 5.2 mJy (total), 0.9-1.3 mJy (regions)  
  > "| Total   | 5.2         |" (Table 1)
- time on source: 29 min per location, three locations  
  > "the total integration time per location was 29 min" (2 Data)
- observing dates: 07 May, 01 July, 02 July 2012 (three EBs)  
  > "three execution blocks (EBs) performed on 07 May, 01 July, and 02 July 2012" (2 Data)
- pi or archival as stated: _not stated_
- Line: H40alpha recombination line (~99.02 GHz)
- External data: Near-infrared Pabeta and Brgamma line fluxes and attenuation values A_J=2.00±0.36, A_K=0.87±0.16  
  > "values of $A_J=2.00 \pm 0.36$ and $A_K=0.87\pm0.16$ for an attenuation sheet as reported by (cite: engelbracht98)" (4 Analysis) [from (cite: engelbracht98)]
- External data: Emissivity and effective recombination coefficient alpha_B tables (case B, ne=1e3)  
  > "interpolated between the $\epsilon_\nu$ values from (cite: storey95) for case B recombination" (4 Analysis) [from (cite: storey95)]
- External data: Radio-to-mm SED data used to refit free-free fraction  
  > "(cite: rodriguezrico06) found a much smaller contribution of free-free emission to the central 30 arcsec" (4 Analysis) [from (cite: rodriguezrico06)]
- Simulation/model as data: Starburst99 v7.0.1 models for Q to SFR conversion  
  > "We used version 7.0.1 of the Starburst99 models (cite: leitherer99) to determine how to convert" (4 Analysis)

## Processing

### Calibration

- pipeline or manual: Reprocessed in CASA with flagging and phase/amplitude calibration; amplitudes rescaled to match J0137-245 average across EBs  
  > "we rescaled the amplitudes of the visibility data so that the signal measured for J0137-245 in the individual execution blocks matched the weighted average of these values" (2 Data)
- casa version: 4.2.2  
  > "We reprocessed the data using the Common Astronomy Software Applications version 4.2.2" (2 Data)
- pipeline version: _not stated_
- archive products used as is: No; reprocessed  
  > "more up-to-date than the one used to create the data in the ALMA archive" (2 Data)
- flux calibrator: Uranus (Butler-JPL-Horizons 2012)  
  > "Uranus was the flux calibrator, J2333-237 was the bandpass calibrator, and J0137-245 was the phase calibrator." (2 Data)
- flux scale uncertainty: 5%  
  > "The flux calibration uncertainty reported in the ALMA Technical Handbook is 5%" (2 Data)
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "using a clean algorithm with natural weightings in an interactive mode" (2 Data)
- uv taper: _not stated_
- cell size: 0.1 arcsec  
  > "covering a 32$\times$32 arcsec region (with 0.1 arcsec pixels)" (2 Data)
- image size: 32x32 arcsec  
  > "covering a 32$\times$32 arcsec region (with 0.1 arcsec pixels)" (2 Data)
- masking: interactive clean  
  > "using a clean algorithm with natural weightings in an interactive mode" (2 Data)
- multiscale scales: _not stated_
- continuum subtraction: Two cubes with and without continuum; continuum measured by fitting and removing line emission  
  > "the continuum at 99.02 GHz was measured in the other image cube by fitting and removing the line emission" (2 Data)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: 8 visibility channels per image channel = 3.9 MHz (~11.8 km/s); cubes 98.80-99.09 GHz  
  > "each channel in each cube covers 8 channels in the visibility data, which corresponds to 3.9 MHz ($\sim$11.8 km s$^{-1}$)" (2 Data)
- final beam: 1.9x1.6 arcsec  
  > "The full-width at half maximum (FWHM) of the reconstructed beam is $1.9\times1.6$ arcsec" (2 Data)
- final rms: _not stated_

### Inherited from earlier work

- Data originally acquired and published  
  > "The data were originally acquired as part of program 2011.0.00172.S and published by (cite: bolatto13)." (2 Data) [from (cite: bolatto13)]
- Equations for line/continuum ratio and SFR adapted from Scoville & Murchikova  
  > "which are adapted from (cite: scoville13)" (4 Analysis) [from (cite: scoville13)]

### Not stated but needed to reproduce (our reading)

- CLEAN threshold, iteration count and mask definitions
- Line-free channels used for continuum fitting and order of baseline fit
- Flagging details
- Exact SED data points and fit used to derive 70% free-free fraction
- Emissivity and alpha_B interpolation values
- Region definitions for E, C, W
- Engelbracht line fluxes used for attenuation
- Source coordinates

## Analysis recipe

1. **Reprocess and image data**: Recalibrate in CASA, rescale EB amplitudes to J0137-245, concatenate, clean to cubes with and without continuum  
  > "We produced two versions of the image cube (with and without continuum) using a clean algorithm with natural weightings in an interactive mode." (2 Data)
   - software: CASA
   - parameter: natural weighting, 0.1 arcsec pixels, 3.9 MHz channels  
  > "(with 0.1 arcsec pixels)" (2 Data)
   - fitting: _not stated_
   - validation: Calibrator cubes show <1% channel variation and no spectral features at H40alpha  
  > "Cleaned image cubes of the bandpass and phase calibrators show $<$1% variations in the flux density from channel to channel" (2 Data)
2. **Measure line and continuum properties**: Measure H40alpha flux, mean velocity, FWHM in continuum-subtracted cube; continuum by fitting and removing line; integrate over central 20x10 arcsec and E, C, W regions  
  > "H40$\alpha$ fluxes, mean velocities (relative to the Solar System Barycentre, and velocity FWHM were measured in the continuum-subtracted image cube" (2 Data)
   - fitting: _not stated_
   - validation: _not stated_
3. **Determine free-free fraction**: Refit SED of Rodriguez-Rico et al. allowing synchrotron slope to vary  
  > "we find that $70\pm10$% of the 99.02 GHz emission is from free-free emission" (4 Analysis)
   - assumption: Continuum multiplied by 0.70±0.10  
  > "multiplying the measured continuum by $0.70\pm0.10$" (Table 1)
   - fitting: _not stated_
   - validation: Sensitivity tests with no correction (Te 5800-7100 K) and 50% (Te 2500-3000 K)  
  > "the measured $T_e$ would increase to values of 5800-7100 K" (4 Analysis)
4. **Derive electron temperature**: Solve line-to-continuum ratio equation for Te using interpolated Storey & Hummer emissivities  
  > "to calculate $T_e$ for each of the regions in our analysis" (4 Analysis)
   - assumption: Case B, ne = 1e3 cm^-3  
  > "for case B recombination and $n_e$=$10^3$ cm$^{-3}$" (4 Analysis)
   - fitting: _not stated_
   - validation: Compared with previous NGC 253 and Milky Way values  
  > "slightly lower than the previously-reported values from (cite: puxley97) and (cite: rodriguezrico06)" (4 Analysis)
5. **Derive Q and SFR**: Starburst99 conversion; SFR from line and continuum equations adapted from Scoville & Murchikova  
  > "SFR = 1 M$_\odot$ yr$^{-1}$ corresponds to $Q$ = $1.85\times10^{53}$ s$^{-1}$ after $\sim$5 Myr of continuous star formation" (4 Analysis)
   - software: Starburst99
   - parameter: Z=0.040, Kroupa IMF 0.1-100 Msun, average of zero and 40% break-up rotation Geneva tracks  
  > "for $Z$=0.040 metallicity (the highest metallicity for which tracks are available) and a (cite: kroupa02) initial mass function for a mass range of 0.1-100 M$_\odot$" (4 Analysis)
   - assumption: Continuous star formation >5 Myr; D = 3.44 Mpc  
  > "imply that the star formation is continuous and has been ongoing for $>$5 Myr" (4 Analysis)
   - fitting: _not stated_
   - validation: Compared with literature mm/radio Q and SFR  
  > "we can compare our total SFR (and $Q$" (4 Analysis)
6. **Derive dust attenuation**: Compare Engelbracht et al. Pabeta and Brgamma fluxes to 0.7x total H40alpha flux assuming attenuating sheet  
  > "we compare the Pa$\beta$ and Br$\gamma$ fluxes from the (cite: engelbracht98) spectroscopy data (which were the lines detected at the highest signal-to-noise levels) to 0.7$\times$ our total H40$\alpha$ flux" (4 Analysis)
   - assumption: ne=1e3 cm^-3, Te=6200±400 K, sheet geometry  
  > "Assuming that $n_e=10^3$ cm$^{-3}$ and using $T_e=6200\pm400$ K" (4 Analysis)
   - fitting: _not stated_
   - validation: ne range 1e2-1e5 changes results by ~0.2 dex  
  > "the effects are on the order of 0.2 dex for a range of $10^2$-$10^5$ cm$^{-3}$" (4 Analysis)

## Software

- **CASA** 4.2.2: Reprocessing and imaging  
  > "We reprocessed the data using the Common Astronomy Software Applications version 4.2.2" (2 Data)
- **Starburst99** 7.0.1: Q to SFR conversion  
  > "We used version 7.0.1 of the Starburst99 models (cite: leitherer99)" (4 Analysis)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Electron temperature range | 3700-4500 | ±300-400 | K | 4 | We calculate electron temperatures of 3700-4500 K |
| Q | 3.2e53 | 0.2e53 | s^-1 | 5 | $(3.2\pm0.2)\times10^{53}$ s$^{-1}$ |
| SFR (central 20x10 arcsec) | 1.73 | 0.12 | Msun/yr | 5 | $1.73\pm0.12$ M$_\odot$ yr$^{-1}$ |
| Total H40alpha flux | 6.91 | 0.80 | Jy km/s | 2 | $6.91 \pm 0.80$ |
| Total 99.02 GHz free-free flux density | 146.5 | 17.2 | mJy | 2 | $146.5 \pm 17.2$ |
| A_Pabeta | 5.0 | 0.2 | mag | 6 | $A_{Pa\beta}=5.0\pm0.2$ and $A_{Br\gamma}=4.2\pm0.2$ |
| A_Brgamma | 4.2 | 0.2 | mag | 6 | $A_{Pa\beta}=5.0\pm0.2$ and $A_{Br\gamma}=4.2\pm0.2$ |
| Central H40alpha FWHM | 191 | 4 | km/s | 2 | with a FWHM of $191\pm4$ km s$^{-1}$ |

## Qualitative findings

- Central H40alpha emission appears to rotate orthogonally to the galaxy plane; no AGN indicated by line width  
  > "appears to be rotating orthogonally to the plane of the galaxy" (2 Data)

## Claim tuples

- H: Can ALMA H40alpha and 99 GHz continuum constrain Te in NGC 253's centre? | E: Line-to-continuum ratio with 70% free-free fraction | R: Te = 3700-4500 K | F: Consistent with previous measurements and Milky Way values | **supported**
- H: Better-constrained Q and SFR from mm data | E: Starburst99 conversion of line and continuum | R: Q=(3.2±0.2)e53 s^-1; SFR=1.73±0.12 Msun/yr | F: Within the broad range of previous measurements but better constrained | **supported**
- H: NIR line attenuation was underestimated | E: Compare H40alpha with Pabeta and Brgamma | R: A higher than Engelbracht values | F: Attenuation too low by ~3 dex in sheet scenario | **partially**

## Reasoning

- Why this data: Explore early ALMA capability to detect free-free and recombination lines  
  > "It is therefore of interest to use early ALMA observations to explore the telescope’s capabilities to detect these star formation tracers." (Introduction)
- Why this method: _not stated_
- Alternative: Program 2011.0.00061.S not used because of different spectral settings  
  > "Because the spectral settings were different from program 2011.0.00172.S, we did not use the data in our analysis" (2 Data)
- How they decided it was enough: _not stated_
- Limitation (authors): Unidentified systematic amplitude calibration effects could affect flux densities  
  > "although unidentified systematic amplitude calibration effects could affect the flux densities" (2 Data)
- Limitation (authors): Attenuation analysis uses simple sheet model  
  > "it is beyond the scope of this paper to explore a more complex treatment of the attenuating medium" (4 Analysis)
- Caveat (inferred, ours): Free-free fraction of 70% rests on a refit SED with free synchrotron slope and strongly drives Te
- Caveat (inferred, ours): The ~3 dex attenuation claim relies on a sheet model and mismatched apertures and resolutions
- Caveat (inferred, ours): Cycle 0 data with few antennas and missing short spacings

## Reproducibility

- Data public (paper): Archive data acknowledged, program 2011.0.00172.S  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2011.0.001720.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: CLEAN parameters
- Missing: SED data for free-free fraction
- Missing: Region apertures
- Missing: Interpolation values for emissivity
- Data volume (inferred): ~50-100 GB raw for three EBs
- Score (inferred): 3/5, Public data and a clear analytic recipe, but imaging and SED-fit details are missing.
- Rediscovery candidate: yes, Public data, numeric results from explicit equations, though some inputs are not given.

## Links

- Method: (cite: scoville13) (Source of line/continuum and SFR equations)
- Method: (cite: storey95) (Emissivities and recombination coefficients)
- Companion: (cite: bolatto13) (Original publication of the data)
- Companion: (cite: leroy15) (Other analysis of the same data)
- Companion: (cite: meier15) (Other analysis of the same data)
- Related: 2011.0.00061.S

## Checks

```json
{
 "quotes": 68,
 "quotes_ok": 68,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [
  "2011.0.00061.S"
 ],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [
  "2011.0.001720.S"
 ],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 79,
  "stated": 53,
  "rate": 0.671
 },
 "evidence_ok": true
}
```
