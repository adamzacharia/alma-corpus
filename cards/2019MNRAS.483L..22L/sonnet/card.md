# Direct detection of quasar feedback via the Sunyaev-Zeldovich effect

`2019MNRAS.483L..22L` | Monthly Notices of the Royal Astronomical Society 2019 | first author: Lacy, Mark | arXiv: 1811.05023 | DOI: 10.1093/mnrasl/sly215 | **HELD OUT (benchmark)**

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: agn_and_quasars, galaxy_clusters_and_sz
- Question: Can the thermal/kinetic Sunyaev-Zeldovich effect from a quasar wind bubble around HE 0515-4414 be directly detected with ALMA, and what does it imply for wind energetics?  
  > "In this paper, we describe our attempt to use ALMA to" (Introduction); "Estimates of the energy in the wind allow us to constrain the wind luminosity to the lower end of theoretical predictions" (abstract)
- Target **HE 0515-4414**: coordinates 05:17:07.614 -44:10:55.64  
  > "HE 0515-4414 ($z=1.71$; Reimers et al. 1998)" (Introduction); "QSO | 05:17:07.614 | -44:10:55.64 | 66.2" (Table 1); z/distance z=1.71  
  > "HE 0515-4414 ($z=1.71$; Reimers et al. 1998)" (Introduction); "QSO | 05:17:07.614 | -44:10:55.64 | 66.2" (Table 1); distance from Reimers et al. 1998  
  > "HE 0515-4414 ($z=1.71$; Reimers et al. 1998)" (Introduction); "QSO | 05:17:07.614 | -44:10:55.64 | 66.2" (Table 1)

## Data provenance

- ALMA projects: 2016.1.00309.S
- bands: Band 4 (~130 GHz)  
  > "which lies in ALMA band-4." (2.1 ALMA)
- frequencies and spectral setup: four 2 GHz basebands centered at 133, 135, 145, 147 GHz; single pointing  
  > "using four 2 GHz basebands centered at 133, 135, 145, and 147 GHz." (2.1 ALMA)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: one SB in a large configuration (~0.7'') executed once; one SB in a compact configuration (~2.7'') executed 14 times  
  > "one executed 14 times in a compact configuration" (2.1 ALMA)
- baselines: _not stated_
- angular resolution: natural 3.2''x2.3'' PA 106; tapered 6.7''x6.4'' PA 110  
  > "$\theta_{\rm FWHM} =$ 6.7$''$$\times$6.4$''$ at PA $= 110^{\circ}$" (2.1 ALMA)
- max recoverable scale: _not stated_
- sensitivity: natural weighting RMS 3.5 uJy/beam; tapered RMS 6.6 uJy/beam  
  > "with an RMS of $\sigma =$ 3.5 $\mu$Jy beam$^{-1}$" (2.1 ALMA)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Other facility **Spitzer**: 3.6 and 4.5 um imaging (DDT PID 13221)  
  > "*Spitzer* observations were obtained in a DDT program (PID 13221)." (2.2 Optical and Infrared)
- Other facility **Gemini (GMOS, FLAMINGOS-2)**: Z, J, Ks imaging (GS-2017B-FT-12)  
  > "Gemini fast turnaround observations were obtained in program GS-2017B-FT-12 using the GMOS and FLAMINGOS-2 instruments." (2.2 Optical and Infrared)
- Other facility **HST WFC3**: F140W/F160W images and G141 grism spectra (program 14594)  
  > "These consist of broad-band images in the F140W and F160W filters, and grism spectra using the G141 dispersive element." (2.2 Optical and Infrared)
- External data: Wind bubble expansion model (self-similar, equations 6 & 7)  
  > "We base our treatment of the expansion of the wind bubble on the model in RS11" (3.2.1 Thermal SZE Model) [from Rowe & Silk 2011 (RS11)]
- External data: Black hole mass formulation  
  > "using the formulation of Bennert et al. (2015)." (2.2 Optical and Infrared) [from Bennert et al. 2015]
- External data: Poor cluster at z=0.28 mass 6e12 Msun  
  > "Bielby et al. (2017) find a poor cluster at $z=0.28$ in the field" (3.1 The quasar host galaxy and its environment) [from Bielby et al. 2017]

## Processing

### Calibration

- pipeline or manual: ALMA pipeline  
  > "Calibration of the data was performed with the ALMA pipeline." (footnote 1)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: ~5% amplitude calibration accuracy  
  > "resulting in an amplitude calibration accuracy of $\approx 5$%" (2.1 ALMA)
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: natural weighting, then taper  
  > "No clear signal was readily apparent in the naturally-weighted map" (2.1 ALMA)
- uv taper: taper matched to signal size giving 6.7''x6.4'' beam; also 20'' taper tried  
  > "so tapering was applied to improve the surface brightness sensitivity of the image." (2.1 ALMA)
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: 12% correction at decrement position  
  > "After a 12% correction for the response of the primary beam" (2.1 ALMA)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Not stated but needed to reproduce (our reading)

- CASA/pipeline version
- Taper values (uv-taper parameters) and imaging task/cell/size
- Method of point-source model fitting in the uv-plane and tool used
- Exact configurations and dates
- How the 3.5 sigma significance was assessed (noise estimation region, trials factor)
- How bubble radii were deconvolved from beam

## Analysis recipe

1. **Subtract point sources**: Subtract point-source models for QSO, A1, A3, A5 in the uv-plane  
  > "the subtraction of point source models in the $uv$-plane" (2.1 ALMA)
   - assumption: all sources unresolved in compact configuration data  
  > "all sources were unresolved in the smaller configuration data" (2.1 ALMA)
   - fitting: _not stated_
   - validation: _not stated_
2. **Image with taper and find SZE decrement**: Taper to match signal size; measure peak decrement and correct for primary beam  
  > "recovers an apparent dip of flux density of $-23.1\,\mu$Jy, significant at the 3.5$\sigma$ level" (2.1 ALMA)
   - fitting: _not stated_
   - validation: Corroborated by extended emission-line gas at same position angle  
  > "The SZE detection is corroborated by the presence of extended emission line gas at the same position angle as the wind." (abstract)
3. **Thermal SZE model and bubble energy**: Derive Compton y, pressure, enthalpy; conical RS11 wind model solved for L_W and t from R and y_max  
  > "we can estimate both $L_W$ and $t$, and the total energy of the event, $E_W = L_W t$." (Interpretation of the SZE Signal / Thermal SZE Model)
   - parameter: cone half angle 30 deg, axis 45 deg to line of sight  
  > "We estimate the half angle of the cone in our system to be $\theta = 30^{\circ}$" (3.2.1 Thermal SZE Model)
   - assumption: negligible cooling, equipartition T=T_e, n≈1.92 n_e, strong shock  
  > "The first is that cooling of the hot phase gas is negligible." (3.2.1 Thermal SZE Model)
   - fitting: _not stated_
   - validation: Energy estimates agree among three methods  
  > "the fair agreement in the total energy estimate between the three different methods" (3.2.2 Thermal Plus Kinetic SZE Model)
4. **Thermal plus kinetic SZE model**: Add kSZE term to y_max relation to explain one-sided decrement; recompute L_W, t, shock  
  > "Adding this kSZE term to the right side of Equation" (3.2.2 Thermal Plus Kinetic SZE Model)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **ALMA pipeline** : calibration  
  > "Calibration of the data was performed with the ALMA pipeline." (footnote 1)
- **IRAF (GMOS and Gemini packages)** : Gemini data reduction  
  > "We used the standard GMOS data reduction package in IRAF" (2.2 Optical and Infrared)
- **astrodrizzle** : combine HST broad-band images  
  > "The broad-band images were combined using astrodrizzle" (2.2 Optical and Infrared)
- **aXe** : extract HST grism spectra  
  > "the aXe software (Kümmel et al. 2009) was used to extract the grism spectra." (2.2 Optical and Infrared)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| SZE peak decrement (tapered, before PB correction) | -23.1 | 3.5 sigma | uJy/beam | 2 | recovers an apparent dip of flux density of $-23.1\,\mu$Jy |
| Peak decrement after PB correction | -25.9 | not stated | uJy | 2 | this peak value of the decrement becomes $-25.9 \, \mu$Jy |
| Compton y | 2.08e-5 | not stated | dimensionless | 3 | $y=\tau k_{\rm B} T_{\rm e}/(m_{\rm e}c^2) \approx 2.08  \times 10^{-5}$ |
| Wind kinetic power (tSZE+kSZE) | 0.429e11 | not stated | Lsun | 4 | tSZE plus kSZE / 0.429 / 12.87 / 0.67 / 510 / 0.36 / 1.50 |
| Wind age (tSZE only) | 8.13e7 | not stated | yr | 3 | tSZE only / 1.70 / 8.13 / 1.68 / 807 / 0.91 / 0.95 |
| Cooling time | ~0.6 | not stated | Gyr | 4 | This corresponds to a cooling time of $\sim$0.6 Gyr |
| Black hole mass | 4.3e10 | not stated | Msun | 0 | $M_{\bullet}\approx 4.3\times 10^{10}\,M_{\odot}$ |

## Qualitative findings

- SZE decrement only SW of quasar; extended [OIII] gas C1 at similar PA with velocity gradient  
  > "we find \[Oiii\] emission and faint continuum in the C1 component" (3.1 The quasar host galaxy and its environment)

## Claim tuples

- H: A quasar-wind bubble can be detected via SZE with ALMA | E: Band 4 compact-configuration observations after point-source subtraction and tapering | R: -25.9 uJy decrement at 3.5 sigma SW of quasar | F: First tentative detection of SZE from a quasar wind bubble | **partially**
- H: Wind power relative to bolometric luminosity | E: Conical RS11 model with tSZE and kSZE | R: wind luminosity ~0.003% of Lbol; ~0.01% by energy | F: Wind at low end of theoretical predictions | **supported**

## Reasoning

- Why this data: Band 4 matches SZE decrement peak near 130 GHz; compact configs match 1-10'' scales  
  > "The peak intensity of the thermal SZE decrement is seen at $\approx 130$ GHz" (2.1 ALMA)
- Why this method: _not stated_
- Alternative: Contamination from intragroup/cluster medium argued against; starburst origin cannot be ruled out  
  > "we cannot currently rule out a starburst origin." (3.2.2 Thermal Plus Kinetic SZE Model)
- How they decided it was enough: _not stated_
- Limitation (authors): Single object; only 3.5 sigma; model assumes cone geometry  
  > "We emphasize though that this is only a single object" (3.3 Discussion)
- Caveat (inferred, ours): 3.5 sigma significance without look-elsewhere or noise-realization tests
- Caveat (inferred, ours): Residual diffuse emission from A5 or imperfect subtraction could mimic decrement
- Caveat (inferred, ours): Model degeneracies and many geometric assumptions (cone angle, inclination)

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: CASA version and imaging parameters
- Missing: taper specifics
- Missing: uv-model fitting details
- Data volume (inferred): ~10-50 GB
- Score (inferred): 3/5, Data are identified but imaging parameters are largely unstated; modelling is analytic and reproducible.
- Rediscovery candidate: no, Imaging recipe is incomplete and detection is marginal.

## Links

- Method: Rowe & Silk 2011 (wind bubble SZE model)

## Checks

```json
{
 "quotes": 52,
 "quotes_ok": 52,
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
  "facts": 71,
  "stated": 37,
  "rate": 0.521
 },
 "evidence_ok": true
}
```
