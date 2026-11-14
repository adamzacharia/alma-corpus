# The Albedos, Sizes, Colors, and Satellites of Dwarf Planets Compared with Newly Measured Dwarf Planet 2013 FY27

`2018AJ....156..270S` | The Astronomical Journal 2018 | first author: Sheppard, Scott S. | arXiv: 1809.02184 | DOI: 10.3847/1538-3881/aae92a

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type multi_facility_alma_minor

## Science

- Fields: solar_system
- Question: What are the size, albedo, color and satellite properties of the dwarf planet 2013 FY27, and how do they compare with other large TNOs?  
  > "Understanding the size and albedo of 2013 FY27 is important in order to put this intrinsically bright object into context of the other dwarf planets beyond Neptune." (Introduction)
- Target **2013 FY27**: coordinates _not stated_; z/distance R = 80.09 au, Delta = 79.74 au (2017 Dec 29)  
  > "The orbit of 2013 FY27, with a semi-major axis near 59 au, eccentricity of 0.39 and inclination of 33 degs, makes it a typical scattered disk object." (Introduction); "FY27 & 2017 Dec 29 & 80.09 & 79.74 & 0.66 & ALMA" (Table 1); distance from Table 1 observing geometry  
  > "The orbit of 2013 FY27, with a semi-major axis near 59 au, eccentricity of 0.39 and inclination of 33 degs, makes it a typical scattered disk object." (Introduction); "FY27 & 2017 Dec 29 & 80.09 & 79.74 & 0.66 & ALMA" (Table 1)

## Data provenance

- ALMA projects: 2017.1.01662.S
- bands: Band 3  
  > "We used Band 3 in the standard continuum setup centered at 97.5 GHz, with a total encompassed bandwidth of 8 GHz." (4 ALMA Observations)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: 8 GHz total, centered at 97.5 GHz  
  > "We used Band 3 in the standard continuum setup centered at 97.5 GHz, with a total encompassed bandwidth of 8 GHz." (4 ALMA Observations)
- arrays: _not stated_
- configurations: 46 antennas, maximum baseline 2500 m  
  > "the array was configured with 46 antennas and a maximal distance between antennas (maximum baseline) of 2500 m." (4 ALMA Observations)
- baselines: _not stated_
- angular resolution: 0.50 x 0.42 arcsec (natural weighting)  
  > "The synthesized beam was $0.50 \times 0.42$ arcseconds in the natural-weighted image." (4 ALMA Observations)
- max recoverable scale: _not stated_
- sensitivity: rms 5.5 microJy  
  > "giving the final image an rms of 5.5 microJy." (4 ALMA Observations)
- time on source: 3.3 hours total, 2.2 hours on source  
  > "The combined observations totaled of 3.3 hours of ALMA time, with 2.2 hours of that integrating on the source." (4 ALMA Observations)
- observing dates: 29 and 30 December 2017 and 04 January 2018  
  > "The Atacama Large Millimeter Array (ALMA) observations were taken on UT 29 and 30 December 2017 and 04 January 2018" (4 ALMA Observations)
- pi or archival as stated: _not stated_
- Other facility **Magellan 6.5 m / IMACS**: Sloan g, r, i photometry, light curve, colors, phase curve, absolute magnitude  
  > "The IMACS camera was used, which has a pixel scale of 0.20 arcsec per pixel and field of view of about 0.16 square deg." (2 Magellan Optical Observations)
- Other facility **Hubble Space Telescope (WFC3/UVIS, GO-15248)**: Discovery of satellite  
  > "An obvious point source was detected about $0.17$ arcseconds at a position angle of 135 degs from the primary" (5 Satellite Discovered)
- External data: Phase integral q = 0.336 pV + 0.479 for TNOs  
  > "As shown in Brown & Butler (2017), $q$ for TNOs can be approximated by $0.336p_V + 0.479$." (Size and Albedo) [from Brown & Butler (2017)]
- External data: Beaming parameter eta=1.175 and emissivity 0.70 for TNOs  
  > "Lellouch et al. (2017) advise using a value of $\eta=1.175$ for TNOs observed with ALMA, so we adopt that value here." (Size and Albedo) [from Lellouch et al. (2017)]
- External data: Sloan to BVRI transformation equations  
  > "using the transformation equations from Smith et al. (2002)" (2 Magellan Optical Observations) [from Smith et al. (2002)]

## Processing

### Calibration

- pipeline or manual: ALMA calibration pipeline in CASA  
  > "visibilities were calibrated using the ALMA calibration pipeline in the Common Astronomy Software Applications package (CASA, McMullin et al. 2007)" (4 ALMA Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J1127-1857  
  > "The absolute flux scale was assessed using the well monitored quasar J1127-1857 as a reference." (4 ALMA Observations)
- flux scale uncertainty: 3 to 4 percent  
  > "the absolute flux calibration is accurate at the 3 to 4 percent level." (4 ALMA Observations)
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "natural weighting was used to maximize sensitivity (at the expense of beam size)" (4 ALMA Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: three observations combined, spectrally averaged and stacked into one visibility set  
  > "The three sets of observations were then combined, spectrally averaged and stacked into one visibility set." (4 ALMA Observations)
- smoothing: _not stated_
- final beam: 0.50 x 0.42 arcsec  
  > "The synthesized beam was $0.50 \times 0.42$ arcseconds in the natural-weighted image." (4 ALMA Observations)
- final rms: 5.5 microJy  
  > "giving the final image an rms of 5.5 microJy." (4 ALMA Observations)

### Inherited from earlier work

- Photometry done similar to earlier work  
  > "All photometry was obtained similar to that described in Sheppard (2007)" (2 Magellan Optical Observations) [from Sheppard (2007)]
- NEATM thermal model  
  > "is to use the Near-Earth Asteroid Thermal Model (NEATM) of Harris (1998)." (Size and Albedo) [from Harris (1998)]

### Not stated but needed to reproduce (our reading)

- tclean parameters (cell size, image size, mask, niter, threshold)
- CASA/pipeline version
- how the source flux (25 microJy) was measured (peak vs fit)
- spectral window setup and any flagging
- calibrators other than J1127-1857 and J1058+0133 details
- solar V magnitude and exact NEATM implementation code

## Analysis recipe

1. **Image ALMA continuum and measure flux**: Calibrate with pipeline, combine three executions, natural-weighted continuum image, measure source flux  
  > "To obtain a continuum image, inverse Fourier transform and deconvolution were applied to the combined visibilities set." (4 ALMA Observations)
   - software: CASA
   - parameter: flux 25 microJy, rms 5.5 microJy, S/N about 4.5  
  > "was 25 microJy bright (Figure [7](#fig:ALMAimage)). This gives the ALMA detection of 2013 FY27 a Signal-to-Noise of about 4.5." (4 ALMA Observations)
   - fitting: _not stated_
   - validation: Compared pipeline flux for phase calibrator J1058+0133 with expected value  
  > "The good match between the retrieved and expected flux for J1058+0133" (4 ALMA Observations)
2. **Optical photometry, colors, phase curve, absolute magnitude**: Aperture photometry on Magellan g, r, i images; linear phase function from March and May r-band; transformation to V  
  > "From the above March and May r-band observations, we find a phase coefficient of $\beta = 0.25\pm 0.03$ mags per deg for 2013 FY27." (2.3 Optical Phase Curve)
   - assumption: Linear phase function  
  > "the linear phase function $\phi (\alpha)$ can be represented as" (2.3 Optical Phase Curve)
   - fitting: _not stated_
   - validation: _not stated_
3. **Solve size and albedo with NEATM**: NEATM fit of thermal flux 25.0+-5.5 microJy at 3.075 mm and V=22.35+-0.03 for D and pV; errors at chi2=1  
  > "We used a flux density from thermal emission of $25.0\pm5.5$ $\mu$Jy at a wavelength of 3.075 mm, and a V-band magnitude of $22.35\pm0.03$ to fit $D$ and $p_V$." (Size and Albedo)
   - parameter: eta = 1.175, emissivity 0.70, beta = 0.25  
  > "Lellouch et al. (2017) advise using a value of $\eta=1.175$ for TNOs observed with ALMA, so we adopt that value here." (Size and Albedo)
   - assumption: Spherical, slow rotator, no nightside emission  
  > "(i) the object is spherical" (Size and Albedo)
   - fitting: Zero degrees of freedom; chi2 contours 1, 2, 3, error bars at chi2=1  
  > "Since there are zero degrees of freedom (using two measurements to fit two parameters), we cannot formerly calculate a reduced-$\chi^2$; instead we use $\chi^2$ itself." (Size and Albedo)
   - validation: _not stated_

## Software

- **CASA** : ALMA calibration pipeline and imaging  
  > "using the ALMA calibration pipeline in the Common Astronomy Software Applications package (CASA, McMullin et al. 2007)" (4 ALMA Observations)
- **NEATM** : Size and albedo from thermal flux  
  > "is to use the Near-Earth Asteroid Thermal Model (NEATM) of Harris (1998)." (Size and Albedo)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| ALMA Band 3 flux density | 25 | 5.5 | microJy | 1 | $25.0\pm5.5$ $\mu$Jy at a wavelength of 3.075 mm |
| Geometric albedo pV | 0.17 | +0.045/-0.030 | dimensionless | 3 | $p_V = 0.17_{-0.030}^{+0.045}$ |
| Effective diameter | 765 | +80/-85 | km | 3 | $D = 765_{-85}^{+80}$ km |
| Primary diameter with satellite | 740 | +85/-90 | km | 3 | making the primary $D = 740_{-90}^{+85}$ km |
| Phase coefficient beta | 0.25 | 0.03 | mag/deg | 2 | $\beta = 0.25\pm 0.03$ mags per deg |
| Absolute magnitude H (mV(1,1,0)) | 3.15 | 0.03 | mag | 2 | we find $m_{V}(1,1,0)=3.15\pm 0.03$ mags |
| g-r color | 0.76 | 0.02 | mag | 2 | $g-r=0.76\pm0.02$ and $r-i=0.31\pm0.03$ |
| Spectral gradient S | 17 | 2 | per 100 nm (percent) | 2 | we find the optical color spectral slope is $S=17\pm 2$ |
| Satellite magnitude difference | 3.0 | 0.2 | mag | 0 | The newly discovered satellite was $3.0\pm0.2$ mags fainter than the primary in the optical. |

## Qualitative findings

- No significant short-term light curve; variations less than 0.06+-0.02 mag  
  > "No clear variability was seen, with variability being less than $0.06\pm 0.02$ over the 3 days" (2.1 r-band Optical Light Curve)

## Claim tuples

- H: What are the size and albedo of 2013 FY27? | E: ALMA Band 3 detection plus Magellan V magnitude, NEATM | R: D = 765 km, pV = 0.17 | F: Size lies in the transition region between largest TNOs and smaller ones | **supported**
- H: Is its color like the largest TNOs? | E: Magellan g, r, i photometry | R: S = 17+-2, moderately red | F: Colors differ from the neutral or ultra-red of the ten largest TNOs; hints at physical change near 800 km | **partially**

## Reasoning

- Why this data: Band 3 gives best continuum sensitivity for a cold object  
  > "For such a cold object, Band 3 provides the best sensitivity in the continuum among all the ALMA bands" (4 ALMA Observations)
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Single thermal wavelength so beaming parameter cannot be determined; assumed parameters add about 5% to D and 10% to albedo uncertainty  
  > "since we have measurements at only one thermal wavelength, we cannot independently determine what the beaming parameter should be." (Size and Albedo)
- Caveat (inferred, ours): Detection is only about 4.5 sigma, so the diameter and albedo are sensitive to flux
- Caveat (inferred, ours): Assumed eta and emissivity from other TNOs dominate systematic error
- Caveat (inferred, ours): Optical magnitude at ALMA epoch extrapolated from May 2016
- Caveat (inferred, ours): Possible satellite contribution to ALMA flux not modeled

## Reproducibility

- Data public (paper): Acknowledges ALMA data ADS/JAO.ALMA#2017.1.01662.S  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2017.1.01662.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Imaging parameters
- Missing: Flux extraction method
- Missing: NEATM code
- Data volume (inferred): about 10-50 GB raw for three Band 3 executions
- Score (inferred): 3/5, Simple recipe with ALMA data public, but imaging and flux extraction details are missing.
- Rediscovery candidate: yes, Public data, a single-flux numeric result, and a simple NEATM model make the main result reproducible.

## Links

- Method: Harris (1998) (NEATM)
- Method: Lellouch et al. (2017) (eta and emissivity for ALMA TNOs)
- Companion: Sheppard and Trujillo (2016) (Survey that discovered 2013 FY27)
- Related: HST GO-15248
- Related: HST Program 15460

## Checks

```json
{
 "quotes": 54,
 "quotes_ok": 54,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 9,
 "numeric_problems": 0,
 "fill": {
  "facts": 67,
  "stated": 39,
  "rate": 0.582
 },
 "evidence_ok": true
}
```
