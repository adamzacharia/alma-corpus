# Water around IRAS 15398-3359 observed with ALMA

`2016A&A...595A..39B` | Astronomy and Astrophysics 2016 | first author: Bjerkeli, P. | arXiv: 1608.06158 | DOI: 10.1051/0004-6361/201628795

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, astrochemistry
- Question: Map the distribution and kinematics of gaseous water (HDO, H2^18O) towards IRAS 15398-3359 to test whether a recent accretion burst released water over an extended region.  
  > "We aim to map the distribution and kinematics of gaseous water towards the low-mass embedded protostar IRAS 15398–3359." (abstract)
- Target **IRAS 15398-3359**: coordinates phase centre RA(J2000) 15h43m02.24s, Dec -34d09m06.7s  
  > "is a Class 0 (cite: Andre:1990fk; Andre:1993fk) protostar located in the Lupus I cloud at a distance of 155 pc (cite: Lombardi:2008lr)." (1 Introduction); "The phase centre was at $\alpha_{2000}$ = 15$^{\rm h}$43$^{\rm m}$02$\stackrel{^{\rm
s}}{_{\bf\cdot}}$24" (2 Observations); z/distance 155 pc  
  > "is a Class 0 (cite: Andre:1990fk; Andre:1993fk) protostar located in the Lupus I cloud at a distance of 155 pc (cite: Lombardi:2008lr)." (1 Introduction); "The phase centre was at $\alpha_{2000}$ = 15$^{\rm h}$43$^{\rm m}$02$\stackrel{^{\rm
s}}{_{\bf\cdot}}$24" (2 Observations); distance from Lombardi et al. 2008  
  > "is a Class 0 (cite: Andre:1990fk; Andre:1993fk) protostar located in the Lupus I cloud at a distance of 155 pc (cite: Lombardi:2008lr)." (1 Introduction); "The phase centre was at $\alpha_{2000}$ = 15$^{\rm h}$43$^{\rm m}$02$\stackrel{^{\rm
s}}{_{\bf\cdot}}$24" (2 Observations)

## Data provenance

- ALMA projects: 2013.1.00244.S, 2011.0.00628.S
- bands: two setups at 390 and 460 GHz  
  > "in two setups at 390 and 460 GHz." (abstract)
- frequencies and spectral setup: Line SPWs 234 MHz wide, 0.122 MHz channels; continuum SPWs 2000 MHz, 15.625 MHz channels  
  > "The bandwidth for the line spectral windows is 234 MHz, and for the continuum spectral windows it is 2000 MHz." (2 Observations)
- continuum bandwidth: _not stated_
- arrays: 12 m array, 36 antennas  
  > "Thirty-six antennas in the 12 m array were used during the observations" (2 Observations)
- configurations: _not stated_
- baselines: 20 m to 520 m  
  > "providing baselines in the range 20 m ($\approx$25–30 k$\lambda$) to 520 m ($\approx$700–800 k$\lambda$)" (2 Observations)
- angular resolution: continuum ~0.3", lines ~0.5" (uv taper for lines)  
  > "The output continuum image cubes have an angular resolution $\sim$0.3$^{\prime \prime}$ , while the line image cubes have a resolution of $\sim$0.5$^{\prime \prime}$." (2 Observations)
- max recoverable scale: 4-5 arcsec  
  > "The largest recoverable scales in the observations presented here range from 4 – 5$^{\prime \prime}$." (3.2 Continuum and other lines)
- sensitivity: _not stated_
- time on source: total observing time 3.6 hours  
  > "the total observing time was 3.6 hours" (2 Observations)
- observing dates: 2015 May 20 and 21  
  > "observed using ALMA on 2015 May 20 and 21" (2 Observations)
- pi or archival as stated: Cycle 2 program, PI Jes Jørgensen  
  > "Cycle 2 program 2013.1.00244.S (PI: Jes Jørgensen)" (2 Observations)
- Line: HDO 1_01-0_00 (464.925 GHz)
- Line: H2^18O 4_14-3_21 (390.608 GHz)
- Line: N2H+ 5-4 (465.825 GHz)
- Line: CS 8-7 (not stated)
- Line: C33S 8-7 (391.851 GHz)
- Other facility **ALMA Cycle 0 (2011.0.00628.S)**: H13CO+ (3-2) hole map used for comparison  
  > "these observations revealed a hole in the H$^{13}$CO$^+$ (3–2) emission (cite: Jorgensen:2013lr)" (1 Introduction)
- Other facility **SMA**: CO (2-1) outflow map from earlier paper  
  > "the CO map obtained with the SMA, which reveals dynamical events in the outflow on timescales of a few hundred years (cite: Bjerkeli:2016lr)" (1 Introduction)
- External data: Infalling envelope density profile, power law p=-1.4, n=2e9 cm-3 at 6.1 AU  
  > "the infalling envelope density profile was taken from the best-fit model presented in (cite: Mottram:2013qy)" (4.2.1) [from (cite: Mottram:2013qy)]
- External data: X(HDO)=2e-7 relative to H2  
  > "$X$(HDO) = 2$\,\times\,10^{-7}$ (cite: Persson:2014oz)" (4.1) [from (cite: Persson:2014oz)]
- External data: X(H2^18O)=1e-7 relative to H2  
  > "$X$(H$_2^{18}$O) = 1$\,\times\,10^{-7}$ (cite: Wilson:1994qy)" (4.1) [from (cite: Wilson:1994qy)]
- External data: Bolometric luminosity 1.8 Lsun  
  > "The bolometric luminosity is meassured at 1.8 $L_{\odot}$ (cite: Jorgensen:2013lr)" (1 Introduction) [from (cite: Jorgensen:2013lr)]
- External data: Outflow inclination 20 deg  
  > "which has been estimated to be 20$^{\circ}$ (cite: Oya:2014kx)" (4.2.3) [from (cite: Oya:2014kx)]

## Processing

### Calibration

- pipeline or manual: standard CASA procedure  
  > "The data reduction was carried out in CASA (cite: McMullin:2007nr) and followed the standard procedure." (2 Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Titan (phase J1517-2422, bandpass J1256-0547)  
  > "bandpass calibration on the quasar J1256-0547, and flux calibration on Titan." (2 Observations)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: uv taper used when CLEANing lines  
  > "The difference arises because a uv taper was used when CLEANing the lines." (2 Observations)
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: ~0.5" lines, ~0.3" continuum  
  > "the line image cubes have a resolution of $\sim$0.5$^{\prime \prime}$" (2 Observations)
- final rms: _not stated_

### Inherited from earlier work

- Outflow-cavity model geometry (wind-driven shell)  
  > "The details of this model can be found in (cite: Bjerkeli:2016lr)." (4.2.3) [from (cite: Bjerkeli:2016lr)]
- Burst timescale of 100-1000 years  
  > "recent accretion burst occurring 100 – 1000 years ago" (1 Introduction) [from (cite: Jorgensen:2013lr)]

### Not stated but needed to reproduce (our reading)

- tclean parameters (weighting, robust, taper size, cell, image size, masks, threshold)
- CASA version
- line-free channels and continuum subtraction method
- stellar/disk parameters, dust opacities and outflow cone geometry for RADMC-3D
- RADEX collider and linewidth settings
- how integrated flux and 5 sigma significance were computed
- MATLAB analysis scripts

## Analysis recipe

1. **Reduce and image data**: CASA standard reduction; line cubes cleaned with uv taper  
  > "The data reduction was carried out in CASA (cite: McMullin:2007nr) and followed the standard procedure." (2 Observations)
   - software: CASA
   - fitting: _not stated_
   - validation: Flagging DA42 has no significant effect on maps  
  > "This has no significant effect on the reduced image cubes" (2 Observations)
2. **Map line emission and continuum**: Maps and spectra analysed in MATLAB; continuum peak from Gaussian fit; HDO spectrum averaged within 1"  
  > "The subsequent analysis of the maps was made in MATLAB." (2 Observations)
   - software: MATLAB
   - fitting: Gaussian fit to continuum peak  
  > "(from a Gaussian fit)" (3.2 Continuum and other lines)
   - validation: _not stated_
3. **Test shock excitation**: RADEX excitation to find pressure needed for 3-sigma H2^18O given HDO strength  
  > "Using `RADEX`  and assuming relative abundances with respect to H$_2$" (4.1)
   - software: RADEX
   - assumption: X(HDO)=2e-7, X(H2^18O)=1e-7  
  > "$X$(HDO) = 2$\,\times\,10^{-7}$ (cite: Persson:2014oz)" (4.1)
   - fitting: _not stated_
   - validation: _not stated_
4. **Model 100 K radius for burst scenarios**: RADMC-3D dust temperature for envelope and envelope plus low-density outflow, luminosity raised by 1 and 2 orders  
  > "we constructed a model of the IRAS 15398–3359 system using RADMC-3D" (4.2.1)
   - software: RADMC-3D
   - parameter: fifty million photon packets; model radius 1000 AU; 1000 grid points each in radial and azimuthal  
  > "fifty million photon packets were propagated through the model" (4.2.1)
   - assumption: dust-to-gas mass ratio 100; no scattering  
  > "The dust-to-gas mass ratio was taken to be 100." (4.2.1)
   - fitting: _not stated_
   - validation: Anisotropic scattering changes distances by <10%; inclination <6%  
  > "Using anisotropic scattering will not change the distances reported here by more than 10%." (4.2.1)

## Software

- **CASA** : data reduction and imaging  
  > "The data reduction was carried out in CASA" (2 Observations)
- **MATLAB** : analysis of maps  
  > "The subsequent analysis of the maps was made in MATLAB." (2 Observations)
- **RADEX** : excitation/pressure constraint  
  > "Using `RADEX`  and assuming relative abundances" (4.1)
- **RADMC-3D** : dust temperature models  
  > "we constructed a model of the IRAS 15398–3359 system using RADMC-3D" (4.2.1)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Continuum peak flux at 465 GHz | 36 | 1 | mJy/beam | 2 | peak flux of 36$\pm$1 mJy beam$^{-1}$ at 465 GHz |
| Continuum peak flux at 403 GHz | 23 | 1 | mJy/beam | 2 | 23$\pm$1 mJy beam$^{-1}$ at 403 GHz |
| HDO line FWHM | ~1 | not stated | km/s | 2 | The line width is narrow with a FWHM $\simeq$1 $\mathrm{km \, s^{-1}}$. |
| Pressure nT needed for H2^18O detection | 1e11 | not stated | cm-3 K | 3 | needs to be as high as $10^{11}$ cm$^{-3}$ K to excite |
| 100 K radius, envelope only, 100x luminosity | <=150 | not stated | AU | 4 | Not even for the case when the luminosity is increased by two orders of magnitude is the 100 K radius farther away than 150 AU |
| Outflow-driven timescale to red knot | ~2300 | not stated | yr | 0 | a timescale of $\sim$2300 years for the gas to reach the location of the red-shifted knot |

## Qualitative findings

- HDO detected near the protostar and extended into outflow; H2^18O not detected (tentative in outflow)  
  > "H$_2^{18}$O is tentatively detected towards the red-shifted outflow lobe, but otherwise it is absent from the mapped region" (abstract)

## Claim tuples

- H: Water in the H13CO+ hole is from a recent accretion burst | E: HDO and H2^18O mapping with ALMA | R: HDO detected at 5 sigma in region of H13CO+ hole, H2^18O undetected | F: Consistent with burst scenario | **supported**
- H: HDO arises from shocks | E: RADEX pressure limit and line width | R: Narrow ~1 km/s line, no H2^18O | F: Shocks not easily reconciled | **partially**
- H: Burst heating can reach ~500 AU | E: RADMC-3D with low-density outflow | R: 100 K radius to ~500 AU for 10-100x luminosity and n<1e5 | F: Extended hour-glass release in a recent burst | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Spherical envelope sublimation and outflow transport of water rejected  
  > "It is clear that an envelope profile cannot explain the large extent of the HDO emission." (4.2.1)
- How they decided it was enough: _not stated_
- Limitation (authors): No short-spacing data; lowest contours unreliable  
  > "should therefore be considered as unreliable because we lack short spacing data" (3.2)
- Caveat (inferred, ours): HDO only 5 sigma; H2^18O features at 3 sigma
- Caveat (inferred, ours): Outflow density and luminosity not constrained by data
- Caveat (inferred, ours): Model not fitted to data

## Reproducibility

- Data public (paper): ALMA program data cited in acknowledgements  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2013.1.00244.S and #2011.0.00628.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: imaging parameters
- Missing: RADMC-3D input geometry details
- Data volume (inferred): ~50-100 GB
- Score (inferred): 3/5, Data identified but imaging and modelling details sparse.
- Rediscovery candidate: no, Imaging and model recipes incomplete.

## Links

- Method: (cite: Bjerkeli:2016lr) (outflow model geometry)
- Companion: (cite: Jorgensen:2013lr) (Cycle 0 H13CO+ hole discovery)

## Checks

```json
{
 "quotes": 64,
 "quotes_ok": 64,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 74,
  "stated": 44,
  "rate": 0.595
 },
 "evidence_ok": true
}
```
