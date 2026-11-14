# The Maser-emitting Structure and Time Variability of the SiS Lines J = 14-13 and 15-14 in IRC+10216

`2018ApJ...860..162F` | The Astrophysical Journal 2018 | first author: Fonfría, J. P. | arXiv: 1805.05218 | DOI: 10.3847/1538-4357/aac5e3

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type multi_facility_alma_minor

## Science

- Fields: evolved_stars, astrochemistry
- Question: What is the spatial structure of the SiS J=14-13 and 15-14 maser emission in IRC+10216, and how does it vary in time with the stellar pulsation?  
  > "We aim to further constrain the structure and excitation conditions of the maser emitting regions as well as its time variability." (Introduction)
- Target **IRC+10216**: coordinates RA(J2000)=09h47m57.435s, Dec=+13°16'43.86"  
  > "The C-rich AGB star IRC+10216, located at $\simeq 120$ pc from Earth (cite: groenewegen_2012)" (Introduction); "The position of the star is $\alpha(\textnormal{J}2000)=09^\textnormal{\scriptsize{h}}47^\textnormal{\scriptsize{m}}57.\!\!^\textnormal{\scriptsize{s}}435$" (Table 1); z/distance ~120 pc (model uses 123 pc)  
  > "The C-rich AGB star IRC+10216, located at $\simeq 120$ pc from Earth (cite: groenewegen_2012)" (Introduction); "The position of the star is $\alpha(\textnormal{J}2000)=09^\textnormal{\scriptsize{h}}47^\textnormal{\scriptsize{m}}57.\!\!^\textnormal{\scriptsize{s}}435$" (Table 1); distance from Groenewegen et al. 2012 (cite: groenewegen_2012)  
  > "The C-rich AGB star IRC+10216, located at $\simeq 120$ pc from Earth (cite: groenewegen_2012)" (Introduction); "The position of the star is $\alpha(\textnormal{J}2000)=09^\textnormal{\scriptsize{h}}47^\textnormal{\scriptsize{m}}57.\!\!^\textnormal{\scriptsize{s}}435$" (Table 1)

## Data provenance

- ALMA projects: 2011.0.00229.S
- bands: _not stated_
- frequencies and spectral setup: ~270-274 GHz, channel width ~0.49 MHz (~0.54 km/s), effective resolution ~1.1 km/s  
  > "The observations covered the spectral range $\simeq 270-274$ GHz with a channel width of $\simeq 0.49$ MHz" (2.2 ALMA Cycle 0 observations)
- continuum bandwidth: _not stated_
- arrays: ALMA Cycle 0, 16 antennas  
  > "The array consisted of 16 antennas with baselines from $\simeq 30$ up to 370 k$\lambda$." (2.2 ALMA Cycle 0 observations)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ~0.55"  
  > "which produced maps with an angular resolution of $\simeq 0.55\ensuremath{''}$." (2.2 ALMA Cycle 0 observations)
- max recoverable scale: _not stated_
- sensitivity: noise RMS ~5 mJy/beam  
  > "The noise RMS is $\simeq 5$ mJy beam$^{-1}$." (2.2 ALMA Cycle 0 observations)
- time on source: _not stated_
- observing dates: 2012 April 8 to 23  
  > "The ALMA observations were taken on 2012 April 8 to 23 during Cycle 0" (2.2 ALMA Cycle 0 observations)
- pi or archival as stated: _not stated_
- Line: SiS J=14-13 (v=0) (254.103213 GHz)
- Line: SiS J=15-14 (v=0) (272.243055 GHz)
- Other facility **CARMA**: B-array SiS J=14-13 observations at ~0.25" and 0.92 km/s resolution (project c0710)  
  > "The antennas were arranged in the B array configuration, with baselines in the range $70-830$ k$\lambda$" (2.1 CARMA observations)
- Other facility **IRAM 30 m**: Single-dish SiS and 29SiS monitoring from 2015 plus 2004 spectra  
  > "This monitoring, motivated by the discovery of the time variability of the thermal line emission by (cite: cernicharo_2014), was carried out from 2015 Jun 7 to present" (2.3 IRAM 30 m telescope observations)
- External data: Fixed envelope model parameters (velocity, temperature, dust profiles, mass-loss rate, etc.)  
  > "(1) (cite: fonfria_2015) (2) (cite: fonfria_2014) (3) (cite: agundez_2012) (4) (cite: ridgway_1988) (5) (cite: fonfria_2008) (6) (cite: debeck_2012)" (Table 2) [from Fonfría et al. 2015, 2014, 2008; Agúndez et al. 2012; Ridgway & Keady 1988; De Beck et al. 2012]
- External data: SiS rest frequencies and spectroscopic constants from MADEX  
  > "the spectroscopic constants of SiS were taken from the MADEX code (cite: cernicharo_2012; velilla_2015)" (3 Modeling) [from (cite: cernicharo_2012; velilla_2015)]
- External data: Dust refractive indices extrapolated from Suh 2000  
  > "estimated by linear extrapolation from the results by (cite: suh_2000) at wavelengths up to 1 mm" (3 Modeling) [from (cite: suh_2000)]
- External data: NIR light curve used as reference for phase lag  
  > "The observations carried out by (cite: shenavrin_2011) and used by (cite: menten_2012) were taken in bands $J$, $H$, $K$, $L$, and $M$" (5.4 Time variability) [from (cite: shenavrin_2011; menten_2012)]

## Processing

### Calibration

- pipeline or manual: Standard CASA calibration for ALMA; Miriad for CARMA  
  > "The calibration and data reduction were performed in the standard way using the CASA software." (2.2 ALMA Cycle 0 observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: ALMA: 3C279 and 3C273 (bandpass and flux)  
  > "Bandpass and absolute flux were calibrated with observations of 3C279 and 3C273." (2.2 ALMA Cycle 0 observations)
- flux scale uncertainty: ALMA ~8%; CARMA ~15%  
  > "The absolute flux calibration uncertainty is about 8%." (2.2 ALMA Cycle 0 observations)
- self calibration: _not stated_

### Imaging

- task: Imaging of CARMA and ALMA data done with GILDAS  
  > "The data imaging of the CARMA and ALMA data sets as well as the single-dish data reduction were achieved using the GILDAS software" (2.3 IRAM 30 m telescope observations)
- deconvolver: _not stated_
- weighting robust: robust = 0.5 (ALMA)  
  > "The data were weighted assuming a robust parameter of 0.5" (2.2 ALMA Cycle 0 observations)
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
- final rms: ~5 mJy/beam (ALMA)  
  > "The noise RMS is $\simeq 5$ mJy beam$^{-1}$." (2.2 ALMA Cycle 0 observations)

### Inherited from earlier work

- ALMA calibration details deferred to earlier paper  
  > "See (cite: cernicharo_2013) for a deeper insight into the calibration process." (2.2 ALMA Cycle 0 observations) [from (cite: cernicharo_2013)]
- Position uncertainty procedure  
  > "Following the procedure used by (cite: fonfria_2014), we derive a statistical position uncertainty of $\simeq 2$ mas." (2.1 CARMA observations) [from (cite: fonfria_2014)]
- Envelope model and comparison of model with data via UVMODEL  
  > "We use the same method followed by (cite: fonfria_2014) to compare the synthetic emission with the observed one." (8 Considerations on the code) [from (cite: fonfria_2014)]

### Not stated but needed to reproduce (our reading)

- Clean/deconvolution settings, cell and image size, and masking for ALMA maps
- Continuum subtraction and line-free channels
- Specific ALMA execution blocks and CASA version
- Full clump/arc parameter list (positions, rotational temperatures) of the best model
- Code of the 3D radiative transfer model is not provided
- Whether the ALMA data were used with archive products

## Analysis recipe

1. **Map SiS emission and decompose into velocity components**: Moment maps, PV diagrams, integrated components A-D with elliptical Gaussian fits  
  > "The fluxes of each component were calculated by integrating the emission above 20% of the peak flux over the Doppler velocity ranges in the second column." (Table 1)
   - software: GILDAS
   - fitting: _not stated_
   - validation: _not stated_
2. **3D radiative transfer modeling of SiS J=14-13 maser structure**: Hand-tuned search for model; rotational temperature modified in maser regions to invert populations; model visibilities replaced via UVMODEL for comparison  
  > "it is possible to replace the observed visibilities contained in the original Miriad packages by those derived from the model with the Miriad task UVMODEL." (8 Considerations on the code)
   - software: Miriad, custom 3D radiative transfer code
   - assumption: Spherically symmetric gas density and SiS abundance; fixed envelope parameters; dust of amorphous carbon  
  > "Thus, we adopt the typical spherically symmetric gas density and SiS abundance with respect to H$_2$ profile." (3 Modeling)
   - fitting: Manual fit; deviation allowed up to ~10% of channel peak (~1.5 Jy/beam)  
  > "the deviation from the synthetic to the observed emission has been adopted to be up to $\simeq 10$% the peak emission in each velocity-channel map" (8 Considerations on the code)
   - validation: Code tested against analytical/numerical results and non-LTE code by Daniel & Cernicharo  
  > "This code was tested comparing the synthetic emission with analytical and numerical results of simple scenarios" (3 Modeling)
3. **Time variability and phase lag of maser versus NIR light curve**: IRAM 30 m monitoring; offset sine fits to relative flux of component A*  
  > "We have fitted the data sets with offset sines finding phase differences of $0.179\pm 0.006$ and $0.164\pm 0.007$" (3.2 Time variability)
   - software: GILDAS
   - fitting: _not stated_
   - validation: Recalibration using constant thermal lines (HNC, SiC2)  
  > "We have used these auxiliary lines to recalibrate the SiS and $^{29}$SiS lines at high frequency." (7 Calibration issues)

## Software

- **CASA** : ALMA calibration  
  > "The calibration and data reduction were performed in the standard way using the CASA software." (2.2 ALMA Cycle 0 observations)
- **Miriad** : CARMA calibration and UVMODEL  
  > "The calibration and data reduction were performed in the standard way using the Miriad package." (2.1 CARMA observations)
- **GILDAS** : Imaging of CARMA/ALMA and single-dish reduction  
  > "The data imaging of the CARMA and ALMA data sets as well as the single-dish data reduction were achieved using the GILDAS software" (2.3 IRAM 30 m telescope observations)
- **MADEX** : SiS frequencies and spectroscopic constants  
  > "the spectroscopic constants of SiS were taken from the MADEX code" (3 Modeling)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Thermal fraction of total SiS 14-13 emission | 25 | not stated | % | 2 | 25% of the total SiS($14-13$) line emission coming from the envelope covered by our CARMA observation has a thermal origin. |
| Maser fraction from extended emission | 60 | not stated | % of maser emission | 2 | The remaining 75% is maser emission: 60% comes from the extended maser emission and 40% from the compact structures. |
| Extended maser shell radius | 13 | not stated | R_star | 2 | a maser emitting shell with a radius of 13$R_\star$ and a thickness of $\simeq 2\ensuremath{R_\star}$ |
| Phase lag relative to NIR, J=14-13 | 0.179 | 0.006 | pulsation phase | 3 | finding phase differences of $0.179\pm 0.006$ and $0.164\pm 0.007$ for the lines $J=14-13$ and $15-14$ |
| Phase lag relative to NIR, J=15-14 | 0.164 | 0.007 | pulsation phase | 3 | finding phase differences of $0.179\pm 0.006$ and $0.164\pm 0.007$ for the lines $J=14-13$ and $15-14$ |
| Moment 0 integrated flux (CARMA 14-13) | 510 | 90 | Jy km/s | 1 | / Moment 0  / $[-14.5,14.5]$ / $510\pm 90$ |

## Qualitative findings

- Extended weak emission cannot be explained thermally and is interpreted as extended maser emission  
  > "The thermal emission cannot explain this extended emission leading us to think that the extended emission is also composed of a significant maser contribution." (6 Summary and conclusions)

## Claim tuples

- H: Is the SiS J=14-13 emission purely thermal? | E: 3D radiative transfer modeling of CARMA data | R: Positive excitation temperatures cannot reproduce observations; clumps, an arc and a shell with negative excitation temperature needed | F: ~75% of emission is maser | **supported**
- H: Does the maser emission follow the stellar pulsation? | E: IRAM 30 m monitoring over a pulsation period | R: Component A* varies periodically with phase lag ~0.2 relative to NIR | F: Some components strongly pulsation-dependent, others mild | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Extended emission as thermal rejected: expected thermal flux ~0.7 Jy/beam, ~75% smaller than observed  
  > "$\simeq 75$% smaller than observed" (5.3.1 Extended Maser Emission)
- How they decided it was enough: _not stated_
- Limitation (authors): No short-spacing or single-dish data; flux lost and sidelobes affect outer emission  
  > "The lack of short baseline visibilities prevented us from properly covering the central region of the $uv$ plane, filtering a significant amount of flux." (5.1 Caveats)
- Caveat (inferred, ours): Model is hand-tuned with no formal fit, uniqueness and uncertainties unquantified
- Caveat (inferred, ours): Sizes and opacities of clumps not meaningful per authors
- Caveat (inferred, ours): Phase lag depends on assumed NIR light curve
- Caveat (inferred, ours): Rotational temperatures in maser regions may be inaccurate

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Radiative transfer code not released
- Missing: Full model clump parameters
- Missing: CARMA data not necessarily public
- Missing: Imaging parameters
- Data volume (inferred): ~10-50 GB for ALMA Cycle 0 data
- Score (inferred): 2/5, Custom unreleased code and hand-tuned model; few imaging details; ALMA role is secondary.
- Rediscovery candidate: no, Main results depend on a custom, hand-tuned model not reproducible from the text.

## Links

- Method: Fonfría et al. 2014 (cite: fonfria_2014) (Model code and CARMA procedure)
- Companion: Pardo et al. 2018 (cite: pardo_2018) (Full IRAM 30 m monitoring dataset)
- Related: CARMA project c0710

## Checks

```json
{
 "quotes": 53,
 "quotes_ok": 53,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 69,
  "stated": 38,
  "rate": 0.551
 },
 "evidence_ok": true
}
```
