# ALMA Observations of the IRDC Clump G34.43+00.24 MM3: Hot Core and Molecular Outflows

`2013ApJ...775L..31S` | The Astrophysical Journal Letters 2013 | first author: Sakai, Takeshi | arXiv: 1309.2804 | DOI: 10.1088/2041-8205/775/1/L31

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, astrochemistry
- Question: What is the star formation activity (hot core, outflows) inside the IRDC clump G34.43+00.24 MM3, and how early is its evolutionary stage?  
  > "However, details of star formation activity within MM3 are still incomplete as previous single-dish observations lacked sufficient angular resolution." (Introduction)
- Target **G34.43+00.24 MM3**: coordinates RA 18h53m20.4s, Dec +1d28m23.0s (J2000, phase center)  
  > "The distance to this IRDC was determined to be 1.56$^{+0.12}_{-0.11}$ kpc by VLBI maser parallax observations (Kurayama et al. 2011)." (Introduction); "The phase center was (R.A.(J2000), Dec.(J2000)) = (18$^{\rm h}$53$^{\rm m}$20.4$^{\rm s}$, 1$^{\circ}$28$^{\prime}$23.0$^{\prime\prime}$)." (2.1 ALMA); z/distance 1.56 kpc  
  > "The distance to this IRDC was determined to be 1.56$^{+0.12}_{-0.11}$ kpc by VLBI maser parallax observations (Kurayama et al. 2011)." (Introduction); "The phase center was (R.A.(J2000), Dec.(J2000)) = (18$^{\rm h}$53$^{\rm m}$20.4$^{\rm s}$, 1$^{\circ}$28$^{\prime}$23.0$^{\prime\prime}$)." (2.1 ALMA); distance from VLBI maser parallax (Kurayama et al. 2011)  
  > "The distance to this IRDC was determined to be 1.56$^{+0.12}_{-0.11}$ kpc by VLBI maser parallax observations (Kurayama et al. 2011)." (Introduction); "The phase center was (R.A.(J2000), Dec.(J2000)) = (18$^{\rm h}$53$^{\rm m}$20.4$^{\rm s}$, 1$^{\circ}$28$^{\prime}$23.0$^{\prime\prime}$)." (2.1 ALMA)

## Data provenance

- ALMA projects: 2011.0.00656.S
- bands: Band 6 (1.3 mm)  
  > "We observed G34.43+00.24 MM3 with ALMA Band 6 on 2012 August 11, 15, and 26." (2.1 ALMA)
- frequencies and spectral setup: 234 MHz mode, 61 kHz channels, averaged by 8 to 488 kHz (0.64 km/s at 230 GHz)  
  > "Since we averaged 8 channels for all the data in order to reduce the noise, the channel width shown in this Letter is 488 kHz, corresponding to the velocity width of 0.64 km s$^{-1}$ at 230 GHz." (2.1 ALMA)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: extended configuration, 23-26 antennas  
  > "The observations were carried out with the extended configuration using 23-26 antennas, whose baseline coverage is from 20.6 m to 399.6 m." (2.1 ALMA)
- baselines: 20.6 m to 399.6 m  
  > "whose baseline coverage is from 20.6 m to 399.6 m" (2.1 ALMA)
- angular resolution: synthesized beams ~0.8x0.6 arcsec (continuum 0.82x0.61)  
  > "1.3 mm Continuum  | $\dots$                                   | $\dots$   | $\dots$   | 0.82$\times$0.61" (Table 1)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: 2012 August 11, 15, and 26  
  > "We observed G34.43+00.24 MM3 with ALMA Band 6 on 2012 August 11, 15, and 26." (2.1 ALMA)
- pi or archival as stated: _not stated_
- Line: CS J=5-4 (244.93556 GHz)
- Line: 13CS J=5-4 (231.22069 GHz)
- Line: SiO J=6-5 (260.51802 GHz)
- Line: CH3OH 5_0-4_0 A+ (241.79143 GHz)
- Line: CH3OH 10_2-9_3 A- (231.28110 GHz)
- Line: CH3CH2CN 27_0,27-26_1,26 (231.31230 GHz)
- Line: HCOOCH3 21_3,19-20_3,18 E (247.04415 GHz)
- Other facility **Keck II NIRC2**: K_p-band (2.124 um) adaptive-optics imaging, 0.15 arcsec resolution  
  > "We observed in the $K_p$ (2.124 $\mu$m) filter using NIRC2 on Keck II with laser-guide star adaptive optics." (2.2 Keck)
- External data: Distance 1.56 kpc  
  > "The distance to this IRDC was determined to be 1.56$^{+0.12}_{-0.11}$ kpc by VLBI maser parallax observations (Kurayama et al. 2011)." (Introduction) [from Kurayama et al. 2011 (cite: kur11)]
- External data: Dust temperature of 29 K from SED fit  
  > "Rathborne et al. (2010) reported the dust temperature of this clump to be 29 K by fitting the SED at the infrared and radio wavelengths." (4.2 Properties of the Hot Core) [from Rathborne et al. 2010 (cite: rat10)]
- External data: 1.2 mm flux 1.02 Jy over 24 arcsec diameter  
  > "Rathborne et al. (2006) reported the 1.2 mm continuum emission integrated over a diameter of 24$^{\prime\prime}$ to be 1.02 Jy." (3 Results) [from Rathborne et al. 2006 (cite: rat06)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Neptune and J1751+096 (bandpass J1924-292)  
  > "The flux calibrations were done by observing Neptune and J1751+096." (2.1 ALMA)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA; line images by CLEANing dirty images  
  > "The line images were obtained by CLEANing the dirty images after subtracting the continuum directly from the visibilities." (2.1 ALMA)
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: continuum subtracted directly from visibilities; continuum from line-free channels of four basebands, 228-245 GHz  
  > "The 1.3 mm (236.930 GHz) continuum image was made by averaging the line-free channels of the four 234 MHz basebands between 228-245 GHz." (2.1 ALMA)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.82x0.61 arcsec, P.A. 110.4 deg (continuum)  
  > "0.82$\times$0.61 | 0.0062$\times$0.0046 | 110.4" (Table 1)
- final rms: _not stated_

### Inherited from earlier work

- Continuum mass derived using the same method as Rathborne et al. (2006)  
  > "We derive the mass of the continuum source by using the same method as reported in Rathborne et al. (2006)." (4.2 Properties of the Hot Core) [from Rathborne et al. (2006) (cite: rat06)]
- Keck data analysis details deferred  
  > "Further details and analysis of these observations will be presented in Foster et al. (in preparation)." (2.2 Keck) [from Foster et al. (in preparation)]

### Not stated but needed to reproduce (our reading)

- CASA version
- weighting/robust, cell and image size, clean threshold and masks
- line-free channel list
- flux density scale uncertainty and Neptune/J1751+096 flux values
- dust opacity and gas-to-dust ratio used for mass
- rms noise of images
- CH3OH rotation diagram fitting details and line intensities used
- how outflow velocity Vmax and extent were measured from PV diagrams

## Analysis recipe

1. **Image continuum and lines**: Continuum from line-free channels; continuum subtracted in visibilities; CLEAN line cubes  
  > "The line images were obtained by CLEANing the dirty images after subtracting the continuum directly from the visibilities." (2.1 ALMA)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Derive outflow parameters from PV diagrams**: R=Robs/sin i, V=Vmax/cos i, tdyn=R/V from SiO PV diagram  
  > "$R_{\rm outflow}$ = $R_{\rm obs}$/$\sin i$, $V_{\rm outflow}$ = $V_{\rm max}$/$\cos i$, and $t_{\rm dyn}$ = $R_{\rm outflow}$/$V_{\rm outflow}$" (4.1 Properties of the Outflow)
   - assumption: inclination 45 degrees  
  > "By assuming the inclination angle of 45 degree for simplicity" (4.1 Properties of the Outflow)
   - fitting: _not stated_
   - validation: CS data give almost the same results  
  > "Note that we obtain almost same results from the CS data." (4.1 Properties of the Outflow)
3. **CH3OH rotation temperature of hot core**: Two high-excitation CH3OH lines intensity ratio  
  > "we calculated the rotation temperature of CH$_3$OH to be 134$\pm$10 K under assumptions of local thermodynamic equilibrium condition and optically thin emission." (4.2 Properties of the Hot Core)
   - assumption: LTE, optically thin  
  > "under assumptions of local thermodynamic equilibrium condition and optically thin emission" (4.2 Properties of the Hot Core)
   - fitting: _not stated_
   - validation: _not stated_
4. **Continuum mass of Peak A**: Dust continuum mass as in Rathborne et al. 2006 for T=29-134 K  
  > "In this temperature range, the mass is derived to be 0.2-1.1 $M_\odot$." (4.2 Properties of the Hot Core)
   - assumption: temperature range 29-134 K; distance 1.56 kpc  
  > "The temperature is expected to be in the range between the two estimates of the temperature (29–134 K)." (4.2 Properties of the Hot Core)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : data reduction and imaging  
  > "The data were reduced by the CASA software package." (2.1 ALMA)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Peak A continuum peak intensity | 14 | not stated | mJy/beam | 1 | The peak intensity of this source is 14 mJy beam$^{-1}$, and its integrated flux density is 38 mJy. |
| Peak A integrated flux density | 38 | not stated | mJy | 1 | its integrated flux density is 38 mJy |
| CH3OH rotation temperature | 134 | 10 | K | 3 | we calculated the rotation temperature of CH$_3$OH to be 134$\pm$10 K |
| Hot core deconvolved size | 0.5" x 0.2" (800 x 300 AU) | not stated | arcsec / AU | 1 | Its deconvolved size is 0.5$^{\prime\prime}$ $\times$ 0.2$^{\prime\prime}$ with P.A. = -56.9$^\circ$, corresponding to 800 AU $\times$ 300 AU. |
| Outflow dynamical timescale | ~740 | not stated | yr | 2 | the outflow size, outflow velocity, and dynamical timescale are evaluated to be $\sim$4400 AU, $\sim$28 km s$^{-1}$, and $\sim$740 yr |
| Outflow velocity | ~28 | not stated | km/s | 2 | $\sim$28 km s$^{-1}$ |
| Continuum source mass | 0.2-1.1 | not stated | Msun | 4 | In this temperature range, the mass is derived to be 0.2-1.1 $M_\odot$. |

## Qualitative findings

- A young, collimated outflow in SiO, CS, CH3OH is driven by a protostar in a hot core at Peak A; extended SiO/CS/CH3OH emission may trace past low-mass star formation.  
  > "We have found a young outflow toward the center of this clump in the SiO, CS, and CH$_3$OH lines." (abstract)

## Claim tuples

- H: Peak A harbors a hot core | E: Detect high-excitation CH3OH and complex organics and derive Trot | R: CH3OH Trot 134±10 K; CH3CH2CN and HCOOCH3 detected | F: Peak A contains a hot core with low mass | **supported**
- H: MM3 hosts a very young outflow | E: PV diagrams of SiO, CS, CH3OH | R: tdyn ~740 yr, ~20 km/s widths | F: Outflow is very young and collimated | **supported**
- H: Low-mass stars already formed earlier in the clump | E: Extended SiO/CS/CH3OH and K-band H2 emission | R: Extended outflow-like emission unassociated with Peak A | F: Past low-mass star formation occurred | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Large hot core size could be higher accretion rate or a multiple system of hot corinos  
  > "Alternatively, this source may be a multiple star system harboring a few hot corinos." (4.2 Properties of the Hot Core)
- How they decided it was enough: _not stated_
- Limitation (authors): Most continuum flux resolved out; mass subject to missing flux  
  > "Thus, most of the flux is resolved out in the ALMA observation." (3 Results)
- Caveat (inferred, ours): Inclination of 45 deg is arbitrary, giving timescale uncertainty
- Caveat (inferred, ours): Rotation temperature from only two lines with optically thin LTE assumption
- Caveat (inferred, ours): Mass range depends on unstated dust parameters
- Caveat (inferred, ours): Missing flux affects sizes and masses

## Reproducibility

- Data public (paper): ALMA project cited in acknowledgments (Cycle 0 data)  
  > "This Letter makes use of the following ALMA data: ADS/JAO.ALMA#2011.0.00656.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Imaging parameters
- Missing: CASA version
- Missing: Dust mass assumptions
- Missing: Rotation diagram details
- Data volume (inferred): ~10-50 GB (Cycle 0, three EBs)
- Score (inferred): 4/5, Short Letter with few processing details, but simple analysis and public data.
- Rediscovery candidate: no, Imaging and analysis details are insufficient for exact redo.

## Links

- Method: Rathborne et al. 2006 (cite: rat06) (Method for continuum mass)
- Companion: Foster et al. (in preparation) (Keck K-band analysis)
- Companion: Sakai et al. (in preparation) (Deuterium fractionation in the clump)

## Checks

```json
{
 "quotes": 55,
 "quotes_ok": 55,
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
  "facts": 68,
  "stated": 33,
  "rate": 0.485
 },
 "evidence_ok": true
}
```
