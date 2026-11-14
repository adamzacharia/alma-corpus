# Observation of narrow polar jets in the nascent wind of oxygen-rich AGB star EP Aqr

`2019MNRAS.487..622T` | Monthly Notices of the Royal Astronomical Society 2019 | first author: Tuan-Anh, P. | arXiv: 1905.02715 | DOI: 10.1093/mnras/stz1281

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: evolved_stars
- Question: What is the morpho-kinematics of the nascent wind of the oxygen-rich AGB star EP Aqr at short distances (<2.5 arcsec) from the star, as probed by SiO, SO2 and CO emission?  
  > "In the present article, we extend the analysis to short distances from the star using new ALMA observations of SiO(5-4) and SO$_2$($16_{6,10}-17_{5,13}$) emissions" (Introduction)
- Target **EP Aqr**: coordinates _not stated_; z/distance 114±8 pc  
  > "at a distance of 114$\pm$8 pc from the Sun (cite: vanLeeuwen2007; Gaia2018)" (Introduction); distance from van Leeuwen 2007; Gaia 2018  
  > "at a distance of 114$\pm$8 pc from the Sun (cite: vanLeeuwen2007; Gaia2018)" (Introduction)

## Data provenance

- ALMA projects: 2016.1.00026.S, 2016.1.00057.S
- bands: Band 6 (12CO, 13CO, SiO; SO2 band not stated)  
  > "Together with observations of the CO line in ALMA Band 6, observations of $^{13}$CO(2-1) and SiO(5-4) line emissions were obtained." (Observations and data reduction)
- frequencies and spectral setup: 13CO: 1920 channels ~30.5 kHz; SiO: 960 channels ~61 kHz; SO2: 960 channels ~488 kHz  
  > "include 1920 channels $\sim$ 30.5 kHz wide for $^{13}$CO(2-1) and 960 channels $\sim$ 61 kHz wide for SiO(5-4)." (Observations and data reduction); "The spectral setup included 960 channels $\sim$ 488 kHz wide and approximately centred on the line." (Observations and data reduction)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: C40-2 and C40-5 (CO, 13CO, SiO); two configurations for SO2  
  > "Both lines were observed in two different configurations, C40-2 and C40-5." (Observations and data reduction)
- baselines: 15 m to 1400 m (CO, 13CO, SiO); 15 m to 3144 m (SO2)  
  > "Maximum baseline (m) | 1400 | 1400 | 1400 | 3144" (Table 1)
- angular resolution: Beam 0.33x0.30 (12CO), 0.27x0.25 (13CO), 0.29x0.25 (SiO), 0.18x0.17 arcsec2 (SO2)  
  > "Beam FWHM (arcsec$^2$) | 0.33$\times$0.30 | 0.27$\times$0.25 | 0.29$\times$0.25 | 0.18$\times$0.17" (Table 1)
- max recoverable scale: _not stated_
- sensitivity: Noise 6, 3.8, 3.9, 1.0 mJy/beam/channel (12CO, 13CO, SiO, SO2)  
  > "Noise (mJy beam$^{-1}$channel$^{-1}$) | 6 | 3.8 | 3.9 | 1.0" (Table 1)
- time on source: 52, 50, 50, 160 min (12CO, 13CO, SiO, SO2)  
  > "Time on source (min) | 52 | 50 | 50 | 160" (Table 1)
- observing dates: 2016 Oct 30 to 2017 Apr 5 (00026); 2016 Oct 8 to Dec 17 (00057)  
  > "between 2016 October 30 and 2017 April 5" (Observations and data reduction)
- pi or archival as stated: _not stated_
- Line: 12CO J=2-1 (230.538 GHz)
- Line: 13CO J=2-1 (220.399 GHz)
- Line: SiO J=5-4 (217.105 GHz)
- Line: SO2 16(6,10)-17(5,13) (234.422 GHz)
- External data: Temperature law T~109 exp(-r/3.1) K and T~106/r K from CO(1-0)/(2-1) comparison  
  > "they proposed two different forms for the radial dependence: $T\sim109 \exp(-r/3.1)$ and $T\sim106/r$ (with $T$ in Kelvin and $r$ in arcsec)" (SO2 emission) [from Hoai2019 (cite: Hoai2019)]
- External data: Einstein coefficients used for temperature/emissivity factors  
  > "$^*$ From (cite: Schoier2005)" (Table 2) [from (cite: Schoier2005)]

## Processing

### Calibration

- pipeline or manual: CASA standard scripts  
  > "The data have been calibrated using CASA[^2] standard scripts." (Observations and data reduction)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: GILDAS for 12CO and 13CO; CASA for SiO and SO2  
  > "Mapping was done with either GILDAS[^3] ($^{12}$CO(2-1), $^{13}$CO(2-1)) or CASA (SiO(5-4), SO$_2$($16_{6,10}-17_{5,13}$))." (Observations and data reduction)
- deconvolver: _not stated_
- weighting robust: Natural weighting for 12CO and 13CO after merging C40-2 and C40-5  
  > "Natural weighting was used for both $^{12}$CO and $^{13}$CO lines after having merged C40-2 and C40-5 observations" (Observations and data reduction)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: Merging in uv plane; more weight to 13CO C40-5 before merging  
  > "before merging more weight was given to the $^{13}$CO C40-5 observations to account for their weaker signal in comparison with C40-2 observations." (Observations and data reduction)
- smoothing: Spectral resolution 0.2 km/s for 13CO and SiO; 0.7 km/s for SO2  
  > "Data were then smoothed to obtain a spectral resolution of 0.2 km s$^{-1}$ for both $^{13}$CO(2-1) and SiO(5-4) observations, and 0.7 km s$^{-1}$ for SO$_2$." (Observations and data reduction)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- 12CO(2-1) observations and data reduction not repeated  
  > "Details of the $^{12}$CO(2-1) observations, here referred to simply as CO, and of the associated data reduction were presented in (cite: Hoai2019) and are not repeated here." (Observations and data reduction) [from (cite: Hoai2019)]
- Coordinate system with y axis 20 deg west of north  
  > "As was done in (cite: Hoai2019) we use an orthonormal system of coordinates having the $y$ axis in the plane of the sky pointing 20$^\circ$ west of north" (Observations and data reduction) [from (cite: Hoai2019)]

### Not stated but needed to reproduce (our reading)

- CASA version and exact standard scripts
- Flux, bandpass and phase calibrators
- CASA tclean parameters (cell, image size, robust, masks) for SiO and SO2
- Continuum subtraction and line-free channels
- Number of execution blocks and which are combined for SO2
- Imaging details of 12CO from Hoai2019
- Exact procedure for rms-based line width and sine-wave fits
- Details of the 12CO/13CO ratio derivation (temperature, absorption treatment)

## Analysis recipe

1. **Calibrate and image data cubes**: CASA standard script calibration, conversion to LSR, spectral smoothing, uv merging, mapping with GILDAS or CASA  
  > "After having obtained calibrated visibilities, we converted them to the Local Standard of Rest (LSR) kinematics spectral frame." (Observations and data reduction)
   - software: CASA, GILDAS
   - parameter: Star LSR velocity -33.6 km/s as origin  
  > "using as origin of the Doppler velocity scale the star LSR velocity of $-$33.6 km s$^{-1}$" (Observations and data reduction)
   - fitting: _not stated_
   - validation: _not stated_
2. **Quantify octant asymmetry**: Integrate flux in octants (blue/red, N/S, E/W) and fit a two-parameter toy model (u,v)  
  > "A toy model parameterization in terms of two parameters $u$ and $v$, respectively measuring the blue/red and east/west asymmetries, gives a good fit to the CO and SiO data but not to the SO$_2$ data." (CO, SiO and SO2 emissions: comparing the main features)
   - fitting: _not stated_
   - validation: rms deviation between model and observed octant values  
  > "The values of $u$ and $v$ are listed in the table together with the rms deviation between model and observed values." (CO, SiO and SO2 emissions: comparing the main features)
3. **Measure SO2 rotation**: Sine wave fits of mean Doppler velocity vs position angle in radial intervals  
  > "Sine wave fits give respective amplitudes of 0.70 and 0.99 km s$^{-1}$ and phase shifts that nearly cancel." (SO2 emission)
   - assumption: Inclination of axis to line of sight ~10 deg  
  > "We retain from this a mean rotation velocity of approximately $0.81/\sin10^\circ \sim 4$ to 5 km s$^{-1}$ ." (SO2 emission)
   - fitting: Sine wave <Vz>=Vz0+Vz1 cos(psi+psi0)  
  > "The results of sine wave fits of the form $\langle V_z\rangle=V_{z0}+V_{z1}\cos(\psi+\psi_0)$ are listed in Table [\[tab6\]](#tab6)." (Rotation)
   - validation: Compared with CO broad component from Hoai2019  
  > "The values obtained here are very similar and are clearly dominated by expansion, leaving essentially no room for rotation." (Rotation)
4. **Characterise SiO jets and wind via P-V maps**: Project cube onto (sin alpha*, Vz) with 3-sigma cut, assuming r*=3.5 arcsec; jet position distributions above 0.02 Jy/beam  
  > "This is shown in Figure [8](#fig10), using a 3-$\sigma$ noise cut on $f$ and assuming that $r^*$ is the same in all directions (and taken equal to 3.5 arcsec)" (General remarks)
   - parameter: Jet selection R<2.5 arcsec, |Vz|>12 km/s, f>0.02 Jy/beam  
  > "A clean signal is seen above $f\sim0.02$ Jy beam$^{-1}$." (A closer look at the polar jets)
   - assumption: Same radial range r* in all directions  
  > "However, the above arguments assume that the radial range $r^*$ of SiO emission is the same in all directions." (General remarks)
   - fitting: _not stated_
   - validation: _not stated_
5. **Derive 12CO/13CO abundance ratio**: Compare 12CO and 13CO brightness accounting for temperature, absorption and Einstein coefficients  
  > "Accounting for temperature, for an average absorption of 20$\pm$20% of $^{12}$CO emission and for the values of the Einstein coefficients listed in Table [\[tab2\]](#tab2), we measure a relative abundance ratio $^{12}$CO/$^{13}$CO of 9$\pm$2." (13CO(2-1) emission)
   - assumption: 13CO optically thin; absorption 20±20%  
  > "$^{13}$CO emission being essentially optically thin" (13CO(2-1) emission)
   - fitting: _not stated_
   - validation: Consistent with Cami et al. 2000 ratio ~10  
  > "they find a $^{12}$CO/$^{13}$CO ratio of the order of 10, however with a large uncertainty." (13CO(2-1) emission)

## Software

- **CASA** : Calibration with standard scripts; mapping of SiO and SO2  
  > "The data have been calibrated using CASA[^2] standard scripts." (Observations and data reduction)
- **GILDAS** : Mapping of 12CO(2-1) and 13CO(2-1)  
  > "Mapping was done with either GILDAS[^3] ($^{12}$CO(2-1), $^{13}$CO(2-1))" (Observations and data reduction)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| 12CO/13CO abundance ratio | 9 | ±2 | dimensionless | 5 | 7) The $^{12}$C/$^{13}$C abundance ratio is measured as 9$\pm$2. |
| SO2 line width FWHM | ~7.5 | not stated | km/s | 3 | broad SO$_2$ line profile ($\sim$ 7.5 km s$^{-1}$ FWHM) |
| SO2 rotation velocity | ~4 to 5 | not stated | km/s | 3 | We retain from this a mean rotation velocity of approximately $0.81/\sin10^\circ \sim 4$ to 5 km s$^{-1}$ . |
| Sine-wave amplitude of SO2 Vz, whole R range | 0.81 | not stated | km/s | 3 | The amplitude obtained for the whole $R$ range is 0.81 km s$^{-1}$. |
| Polar jet velocity | ~20 | not stated | km/s | 4 | two narrow polar jets with velocity reaching $\sim$ 20 km s$^{-1}$ |
| Jet opening angle | ~±10 | not stated | deg | 4 | meaning an opening angle of $\sim \pm10^\circ$ |
| Jet y offset blue-red | -0.104 | 0.19 | arcsec | 4 | $\Delta x=-0.022\pm0.19$ arcsec and $\Delta y=-0.104\pm0.19$ arcsec |
| SiO toy-model asymmetry u | -0.34 | not stated | dimensionless | 2 | $u$  / $-$0.06     / $-$0.34     / 0.15 |
| SiO toy-model asymmetry v | 0.21 | not stated | dimensionless | 2 | $v$  / 0.05        / 0.21        / 0.14 |
| SiO terminal velocity law | V~2+9 sin^2 alpha | not stated | km/s | 4 | A sensible description of the terminal velocity is given by the form $V\sim2+9\sin^2\alpha$ km s$^{-1}$ |

## Qualitative findings

- Axis of rotation near the star, jet axis and large-scale axisymmetry axis coincide  
  > "A same axis serves as axis of rotation close to the star, as jet axis and as axi-symmetry axis at large distances." (abstract)
- Strong depletion of SiO and CO emission in the blue-western quadrant  
  > "A sharp depletion of SiO and CO emissions, starting near the star, rapidly broadens to cover the whole blue-western quadrant" (abstract)

## Claim tuples

- H: Does the nascent wind of EP Aqr contain collimated polar jets? | E: P-V maps of SiO and CO data cubes, jet position distributions | R: Two polar structures reach ~20 km/s, launched within ~25 au | F: Narrow polar jets exist in the nascent wind | **supported**
- H: Is there rotation close to the star? | E: Sine wave fits to SO2 mean velocity vs position angle | R: Amplitude 0.81 km/s, rotation ~4-5 km/s; none detected in SiO and CO | F: Rotation dominates within ~30 au and gives way to expansion by 50 au | **partially**
- H: Is the SiO/CO emission asymmetric? | E: Octant fluxes, depletion cube decomposition | R: Strong blue-west depletion in SiO, weaker in CO | F: A depletion of the blue-western quadrant is present in both lines | **supported**
- H: What is the 12CO/13CO ratio? | E: Compare 12CO and 13CO(2-1) with temperature and absorption corrections | R: 9±2 | F: Ratio consistent with Cami et al. (~10) | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Spherical shell ejected by pulsation rejected as explanation of jets  
  > "Not only is the spherical shell interpretation irreconcilable with SO$_2$ observations" (A closer look at the polar jets)
- Alternative: Jets launched by a distant companion (from the spiral) excluded  
  > "the jets are launched within $\pm$25 au from the star, excluding a possible relation to a distant companion" (A closer look at the polar jets)
- How they decided it was enough: _not stated_
- Limitation (authors): Under-determination of radio observations makes interpretation partly subjective  
  > "one must keep in mind the ambiguity and arbitrariness inherent to the under-determination of radio observations." (Discussion and conclusion)
- Limitation (authors): SO2 beam, line width and sensitivity prevent detailed features  
  > "The beam size, the line width and the sensitivity of the SO$_2$ observations prevent revealing more detailed features with sufficient confidence." (Discussion and conclusion)
- Caveat (inferred, ours): Line width measured as rms deviation per pixel, a crude proxy for FWHM
- Caveat (inferred, ours): No uncertainties on most fitted values (u, v, sine amplitudes)
- Caveat (inferred, ours): 12CO/13CO ratio depends on poorly constrained absorption (20±20%) and LTE
- Caveat (inferred, ours): Assumption r*=3.5 arcsec same in all directions for SiO
- Caveat (inferred, ours): Interpretation largely qualitative, no modelling

## Reproducibility

- Data public (paper): Project codes listed in acknowledgements  
  > "This paper makes use of the following ALMA data: 2016.1.00026.S and 2016.1.00057.S." (ACKNOWLEDGEMENTS)
- Products in archive: _not stated_
- Missing: Calibration and tclean parameters
- Missing: Calibrator and CASA version details
- Missing: Custom analysis code (octant fluxes, depletion cubes) not released
- Missing: Line-width and sine-fit procedure details
- Data volume (inferred): ~100-300 GB (several mosaic execution blocks over two projects)
- Score (inferred): 3/5, Public data and simple analyses with numeric results, but reduction/imaging parameters mostly unstated and much is qualitative.
- Rediscovery candidate: no, Imaging recipe incomplete and main results largely qualitative/morphological.

## Links

- Companion: Hoai et al. 2019 (cite: Hoai2019) (Earlier ALMA CO analysis of EP Aqr, source of CO data, temperature law and coordinate system)
- Companion: Homan et al. 2018 (cite: Homan2018) (Independent ALMA observations of EP Aqr compared throughout)

## Checks

```json
{
 "quotes": 65,
 "quotes_ok": 65,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 10,
 "numeric_problems": 0,
 "fill": {
  "facts": 75,
  "stated": 43,
  "rate": 0.573
 },
 "evidence_ok": true
}
```
