# Radio Continuum Observations of the Galactic Center: Photoevaporative Proplyd-like Objects Near Sgr A*

`2015ApJ...801L..26Y` | The Astrophysical Journal Letters 2015 | first author: Yusef-Zadeh, F. | arXiv: 1502.03109 | DOI: 10.1088/2041-8205/801/2/L26

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: milky_way_ism, star_formation
- Question: Are there photoevaporative proplyd-like objects (low-mass star formation) near Sgr A*, as seen in 34 GHz VLA continuum plus a supporting ALMA SiO spectrum?  
  > "We interpret these sources as a candidate population of photoevaporative protoplanetary disks (proplyds) that are associated with newly formed low mass stars" (abstract)
- Target **Sgr A* region (E arm, RC1/RC2)**: coordinates SiO source 12 at 17h45m41.36s, -29°0'24.57''  
  > "Our 34 GHz observations reveal partially resolved sources with typical sizes of a few hundred AU at the 8 kpc distance to the Galactic center." (Introduction); z/distance 8 kpc  
  > "Our 34 GHz observations reveal partially resolved sources with typical sizes of a few hundred AU at the 8 kpc distance to the Galactic center." (Introduction); distance from assumed distance to the Galactic center (no citation given)  
  > "Our 34 GHz observations reveal partially resolved sources with typical sizes of a few hundred AU at the 8 kpc distance to the Galactic center." (Introduction)

## Data provenance

- ALMA projects: 2011.0.00005.SV
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: SiO 5-4 (not stated)
- Other facility **VLA**: 34.5 GHz A-configuration continuum imaging, 7.8 uJy rms, ~88x46 mas  
  > "Radio continuum observations were carried out with the Karl G. Jansky Very Large Array (VLA)[^1] in its A-configuration at 34.5 GHz on March 9, 2014 (14A-232)." (Observations and Data Reduction)
- Other facility **VLT/NACO**: 3.8 micron L'-band images for near-IR counterpart limits  
  > "L$'$-band (3.8 $\mu$m) data were taken with the Nasmyth Adaptive Optics System (NACO) at the Very Large Telescope (VLT; program 089.B-0503(B))" (Observations and Data Reduction)
- External data: Lyman continuum ionizing photon rate of massive stars, 2.5e50 s^-1  
  > "The EUV Lyman continuum ionization radiation from massive stars is estimated to be $\Phi\approx 2.5\times10^{50}$ s$^{-1}$ (Genzel, Hollenbach & Townes 1994)" (Results) [from Genzel, Hollenbach & Townes 1994]

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

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Details of the ALMA SiO observations and reduction  
  > "Details of these observations are given in Yusef-Zadeh et al. (2013)." (Observations and Data Reduction) [from Yusef-Zadeh et al. 2013]
- NACO image reduction by speckle holography  
  > "The images were reduced with the speckle holography method, as described in detail in Schödel et al. (2010, 2013)." (Observations and Data Reduction) [from Schödel et al. (2010, 2013)]

### Not stated but needed to reproduce (our reading)

- ALMA band, spectral setup, beam and rms for the SiO data
- ALMA calibration and imaging steps
- VLA calibration software, imaging parameters and weighting
- Source-finding and Gaussian fitting procedure for the 44 sources
- Velocity range and channel width used for the SiO spectrum
- SiO luminosity calculation

## Analysis recipe

1. **Fit Gaussians to 34 GHz sources**: Gaussian fits give positions, sizes, peak and integrated fluxes (Table 1)  
  > "The Parameters of Gaussian Fitted 34 GHz Sources" (Table 1)
   - fitting: _not stated_
   - validation: _not stated_
2. **Estimate ionized mass, density and mass-loss rate**: Spherical source of 500 AU radius, filling factor 1; expansion at the sound speed gives the mass-loss rate  
  > "Assuming a spherical source with solid angle corresponding to a radius of 500 AU and electron density filling the sphere with volume filling factor of 1" (Results)
   - assumption: c_s ≈ 10 km/s for T = 8000 K  
  > "Assuming that the ionized gas expands at the sound speed ($c_s\approx 10$ km s$^{-1}$ for $T=8\,000$ K)" (Results)
   - fitting: _not stated_
   - validation: _not stated_
3. **Fit SiO (5-4) spectrum of new source 12**: Gaussian fit to the ALMA spectrum  
  > "A Gaussian fit to this spectrum gives peak flux density 13.69$\pm$1.81 mJy beam$^{-1}$" (Results)
   - fitting: _not stated_
   - validation: _not stated_

## Software


## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Number of 34 GHz compact sources | 44 | not stated | sources | 1 | We report 44 partially resolved compact sources clustered in two regions in the E arm of ionized gas that orbits Sgr A\*. |
| VLA 34 GHz rms sensitivity | 7.8 | not stated | uJy | 0 | the 1$\sigma$ rms sensitivity is 7.8 $\mu$Jy |
| SiO source 12 peak flux density | 13.69 | 1.81 | mJy/beam | 3 | A Gaussian fit to this spectrum gives peak flux density 13.69$\pm$1.81 mJy beam$^{-1}$ |
| Mass-loss rate of proplyd candidates | 1e-7 to 1e-6 | not stated | Msun/yr | 2 | $M_i/(r/c_s)\approx 10^{-7} - 10^{-6}\, 
\msol\, \rm yr^{-1}$ |
| Electron density | 1.2e5 | not stated | cm^-3 | 2 | $1.2\times10^{5}$ cm$^{-3}$ |

## Qualitative findings

- SiO (5-4) sources 4, 5 and 12 coincide with the proplyd candidate concentration; their linewidths are similar to low-mass protostellar outflows  
  > "We note that the SiO (5-4) sources 4, 5 and 12 coincide with the concentration of proplyds candidates." (Results)

## Claim tuples

- H: The compact 34 GHz sources are photoevaporating disks around low-mass stars near Sgr A* | E: 34 GHz VLA imaging, NACO 3.8 um limits, SiO from ALMA | R: 44 bow-shock sources facing Sgr A*, no near-IR counterparts, SiO sources coincident | F: They are a proplyd candidate population, implying in-situ low-mass star formation | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: An isolated molecular globule as the mass reservoir is deemed improbable, since a dense, massive globule would collapse  
  > "As such a dense and massive globule would collapse and form a YSO, it is therefore much more plausible that the reservoir of neutral material is instead a circumstellar disk" (Results)
- How they decided it was enough: _not stated_
- Limitation (authors): Near-IR stellar counterparts cannot be identified with certainty, owing to the lack of proper motion data and confusion  
  > "We can not find near-IR stellar counterparts to radio sources listed in Table 1 with certainty because of the lack of stellar proper motion data and confusing sources in this region." (Results)
- Caveat (inferred, ours): Bow-shock morphology could also come from other sources, e.g. a nuclear wind
- Caveat (inferred, ours): No spectral index or disk mass measurements
- Caveat (inferred, ours): Interpretation as proplyds is based on analogy

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: ALMA observing and processing details, which are only given in Yusef-Zadeh et al. 2013
- Missing: VLA calibration and imaging parameters
- Data volume (inferred): ~50-200 GB (VLA 8 GHz A-config plus ALMA SV)
- Score (inferred): 2/5, The ALMA part is minimal and its details are inherited; the VLA reduction is only sketched.
- Rediscovery candidate: no, The recipe is incomplete and ALMA is a minor component.

## Links

- Method: Yusef-Zadeh et al. 2013 (ALMA SiO observation details)
- Method: Schödel et al. (2010, 2013) (NACO speckle holography reduction)
- Companion: Yusef-Zadeh et al. 2014 (44 GHz sources, massive YSOs)
- Related: VLA 14A-232
- Related: VLT 089.B-0503(B)

## Checks

```json
{
 "quotes": 25,
 "quotes_ok": 25,
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
  "facts": 61,
  "stated": 16,
  "rate": 0.262
 },
 "evidence_ok": true
}
```
