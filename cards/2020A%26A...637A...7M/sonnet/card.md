# Detection of deuterated molecules, but not of lithium hydride, in the z = 0.89 absorber toward PKS 1830-211

`2020A&A...637A...7M` | Astronomy and Astrophysics 2020 | first author: Muller, S. | arXiv: 2003.13436 | DOI: 10.1051/0004-6361/202037628

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: astrochemistry, high_z_galaxies
- Question: Are deuterated molecules (ND, NH2D, HDO) and lithium hydride detectable in the z=0.89 absorber toward PKS 1830-211, and what are their abundance ratios?  
  > "we report the first detection of three deuterated species, ND, NH$_2$D, and HDO, and an upper limit to $^7$LiH, in the z=0.89 absorber against the quasar PKS 1830$-$211." (Introduction)
- Target **PKS 1830-211 (z=0.89 absorber, SW image)**: coordinates _not stated_; z/distance z=0.88582  
  > "All velocities in this paper are referred to the heliocentric frame, taking a redshift of z=0.88582 (cite: wik96)." (2 Observations); distance from Wiklind & Combes 1996 (cite: wik96)  
  > "All velocities in this paper are referred to the heliocentric frame, taking a redshift of z=0.88582 (cite: wik96)." (2 Observations)
- Target **B 0218+357 (archival, LiH)**: coordinates _not stated_; z/distance z=0.68  
  > "ALMA archival observations of the same $^7$LiH (1–0) line toward B 0218+357, taken in October 2018 (project code 2018.1.00187.S)" (3.3 Non-detection of 7LiH); distance from _not stated_

## Data provenance

- ALMA projects: 2018.1.00692.S, 2018.1.00051.S, 2018.1.00187.S
- bands: Band 6 (2019 Apr 11) and Band 7 (2019 Jul 28)  
  > "| 2019 Apr 11 | B6 | 43 | 1.0 | 66 | 4.7 | 0.6 | NH$_2$D, HDO, p-NH$_2$, ($^7$LiH) |" (Table 1)
- frequencies and spectral setup: four spectral windows, each 1.875 GHz wide; velocity resolution 1–5 km/s after Hanning smoothing  
  > "The correlator was configured to cover four spectral windows, each 1.875 GHz wide, with a resulting velocity resolution of 1–5 km s$^{-1}$ (after Hanning smoothing), depending on the project." (2 Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.6 arcsec (Apr, B6); 0.03 arcsec (Jul, B7)  
  > "| 2019 Jul 28 | B7 | 42 | 0.6 | 19 | 1.1 | 0.03 | ND, o-H$^2_{18}$O |" (Table 1)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: 66 min (Apr 11), 19 min (Jul 28)  
  > "| 2019 Jul 28 | B7 | 42 | 0.6 | 19 | 1.1 | 0.03 | ND, o-H$^2_{18}$O |" (Table 1)
- observing dates: 2019 April 11 and 2019 July 28  
  > "observed with the Atacama Large Millimeter/submillimeter Array (ALMA) on 2019 April 11 and 2019 July 28" (2 Observations)
- pi or archival as stated: _not stated_
- Line: HDO 1_0,1–0_0,0 (464.924520 GHz)
- Line: o-NH2D 1_1,0–0_0,0, F=2–1 (470.271911 GHz)
- Line: ND N=1–0, J=2–1 (522.077372 GHz)
- Line: ND N=1–0, J=1–1 (546.127619 GHz)
- Line: o-H2(18)O 1_1,0–1_0,1 (547.676440 GHz)
- Line: 7LiH J=1–0 (443.952930 GHz)
- Line: p-NH2 1_1,0–1_0,1 (469.440621 and 470.409052 GHz)
- External data: 16O/18O = 69 ± 11 from HCO+ isotopologues  
  > "we adopt the ratio $^{16}$O/$^{18}$O $= 69 \pm 11$ derived from observations of HCO$^+$ isotopologues by (cite: mul06; mul11)" (3.1.2 HDO) [from (cite: mul06; mul11)]
- External data: N(H2) = 2e22 cm-2 along SW line of sight  
  > "Taking the column density of H$_2$ estimated along the SW line of sight [^6], $2 \times 10^{22}$ cm$^{-2}$ (cite: mul14)" (3.3 Non-detection of 7LiH) [from (cite: mul14)]
- External data: 2012 p-NH2 and o-NH3 spectra; 2014 o-H2O/H2(18)O spectra for comparison  
  > "two others were observed together with ortho-NH$_3$ back in 2012 (cite: mul14)" (3.1.1 NH2) [from (cite: mul14; mul16b)]
- External data: NH/NH2/NH3 abundance ratios in diffuse gas (3–2:1:1) and dark clouds (3:1:19)  
  > "NH:NH$_2$:NH$_3$= 3–2:1:1 observed in the Galactic diffuse gas (cite: per10; per12)" (3.1.1 NH2) [from (cite: per10; per12; legal14)]
- External data: Spectroscopy parameters from CDMS and JPL  
  > "Spectroscopy parameters are taken from the Cologne Database for Molecular Spectroscopy (cite: CDMS01; CDMS05; CDMS16)" (Table 2 notes) [from (cite: CDMS01; CDMS05; CDMS16; pic98)]
- External data: Collisional rates for NH2D and HDO  
  > "The rates are taken from (cite: dan14) for NH$_2$D and from (cite: fau12) for HDO." (3.1) [from (cite: dan14; fau12)]
- External data: H2 column density 8e21 cm-2 toward B0218+357  
  > "we estimate an H$_2$ column density of $8 \times 10^{21}$ cm$^{-2}$ (cite: wal16)" (3.3 Non-detection of 7LiH) [from (cite: wal16)]

## Processing

### Calibration

- pipeline or manual: CASA, standard procedure; self-calibration on continuum  
  > "The data calibration was carried out within the Common Astronomy Software Applications package (CASA[^2]), following a standard procedure." (2 Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: one iteration of phase-only solutions per 6 sec integration on PKS 1830-211 continuum  
  > "the visibilities were further self-calibrated on the continuum of PKS 1830$-$211, by one iteration of phase-only solutions per 6 sec integration." (2 Observations)

### Imaging

- task: No imaging; spectra extracted by fitting two point sources to visibilities with UVMULTIFIT  
  > "The final spectra were extracted using the CASA Python task UVMULTIFIT ((cite: mar14)) by fitting a model of two point sources to the interferometric visibilities." (2 Observations)
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

- Opacity-to-column conversion assuming excitation locked to CMB (Tex=TCMB=5.14 K)  
  > "Since all species have large electric dipole moments, $> 1$ D, we expect that their excitation is locked to the temperature of the CMB (see (cite: mul13))." (3.1) [from (cite: mul13)]
- LiH archival data reduced similarly as Section 2  
  > "reduced with a similar process as described in Section [2](#sec:obs)" (3.3 Non-detection of 7LiH) [from Section 2 of this paper]
- Full polarization observations of Apr 11  
  > "The observations on 2019 April 11 were done in full polarization mode (Marti-Vidal et al., in prep.)" (2 Observations) [from Marti-Vidal et al., in prep.]

### Not stated but needed to reproduce (our reading)

- Line-free channels and continuum normalization procedure
- Gaussian fitting code and fitting/error method
- Exact CASA version and bandpass/flux calibrator flux scale
- Velocity-resolution/Hanning details per project
- Details of the time-variation correction applied to final ratios
- Phase center/coordinates of target
- Exact RADEX input parameters beyond range

## Analysis recipe

1. **Extract normalized spectra**: Fit two point sources to visibilities with UVMULTIFIT; normalize Stokes I spectra to continuum and average the two executions  
  > "The spectra, extracted from Stokes I data, were then normalized to the continuum level and averaged." (2 Observations)
   - software: CASA, UVMULTIFIT
   - fitting: _not stated_
   - validation: NE image spectra used as monitor to discard Galactic, atmospheric lines or bandpass ripples  
  > "the spectra extracted from the NE image serve as a monitor to control the quality of the spectral bandpass" (2 Observations)
2. **Convert opacity to column density**: N = alpha * integral tau dv with alpha computed for Tex=TCMB; RADEX check of collisional effects  
  > "we ran the radiative transfer code RADEX (cite: vdtak07) for NH$_2$D and HDO" (3.1)
   - software: RADEX
   - parameter: TCMB=5.14 K at z=0.89  
  > "the $\alpha$ factors can be calculated with $\hbox{$T_\mathrm{CMB}$}=5.14$ K at z=0.89" (3.1)
   - assumption: covering factor fc=1; only H2 collision partner; OPR=3  
  > "We further assume that the absorbing gas completely and uniformly covers the background continuum emission from the quasar, that is, a covering factor $\hbox{$f_c$}=1$." (3.1)
   - fitting: _not stated_
   - validation: alpha constant within 10% for n up to 1e4 cm-3 and Tkin 10–100 K  
  > "the corresponding $\alpha$ conversion factors remain constant within 10% for volume density up to $10^4$ cm$^{-3}$ and kinetic temperature in the range 10–100 K." (3.1)
3. **Fit Gaussian velocity components**: One or two Gaussian components per spectrum; joint tight 2-Gaussian fit of p-NH2, NH2D, HDO; ND forced with p-NH2 components  
  > "2Gt: all species fitted simultaneously with the same tight 2-Gaussian velocity profile" (Table 3 notes)
   - fitting: _not stated_
   - validation: _not stated_
4. **Derive deuterium fractionation ratios**: Ratios of integrated opacities with pivot species (NH2 for NH/NH3, H2-18O for H2O), OPR and time-variation corrections  
  > "| ND/NH | ND/p-NH$_2$ | NH/NH$_2$=1–5 $^{\circ}$ | OPR(NH$_2$)=3 | $\times 2$ | (0.7–7)$\times 10^{-3}$ |" (Table 4)
   - assumption: NH2/NH3=1, NH/NH2=3, 16O/18O=69±11, factor 2 variation Apr–Jul 2019  
  > "Further assuming NH$_2$/NH$_3$=1, as we have discussed above, we end up with the ratio NH$_2$D/NH$_3$ $\sim 3 \times 10^{-3}$." (3.1.1 NH2)
   - fitting: _not stated_
   - validation: _not stated_
5. **7LiH upper limit**: 3 sigma_tau sqrt(dv*Dv) with Dv=20 km/s, times alpha; divide by N(H2)  
  > "An upper limit on the integrated opacity of $^7$LiH can be calculated as $3\sigma_{\tau} \sqrt{\delta v \Delta v}$" (3.3 Non-detection of 7LiH)
   - parameter: sigma_tau=1e-3 per 4.7 km/s channel; line width 20 km/s; alpha=2.5e11  
  > "$\sigma_{\tau} = 1 \times 10^{-3}$ is the root-mean-square (rms) noise level normalized to the continuum level per velocity channel $\delta v = 4.7$ km s$^{-1}$" (3.3 Non-detection of 7LiH)
   - assumption: N(H2)=2e22 cm-2  
  > "$2 \times 10^{22}$ cm$^{-2}$ (cite: mul14)" (3.3 Non-detection of 7LiH)
   - fitting: _not stated_
   - validation: Archival B0218+357 LiH spectrum checked for comparison  
  > "show no line absorption feature down to a rms noise level of 1% of the continuum level, with 1.1 km s$^{-1}$ velocity resolution" (3.3 Non-detection of 7LiH)

## Software

- **CASA** : calibration  
  > "The data calibration was carried out within the Common Astronomy Software Applications package (CASA[^2])" (2 Observations)
- **UVMULTIFIT** : spectra extraction by visibility fitting of two point sources  
  > "The final spectra were extracted using the CASA Python task UVMULTIFIT ((cite: mar14))" (2 Observations)
- **RADEX** : check of collisional excitation effects on alpha for NH2D and HDO  
  > "we ran the radiative transfer code RADEX (cite: vdtak07) for NH$_2$D and HDO" (3.1)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| NH2D/NH2 (v~-4 km/s) | 2.7e-3 | 0.3e-3 | dimensionless | 4 | NH$_2$D/NH$_2$ = $(2.7 \pm 0.3)\times 10^{-3}$ for the $v\sim-4$ km s$^{-1}$ velocity component |
| ND/NH2D (v~-4 km/s) | 2.7 | 0.2 | dimensionless | 4 | we derive ND/NH$_2$D = $2.7 \pm 0.2$ |
| ND/NH (v~-4 km/s) | 2.44e-3 | 0.07e-3 (fit only) | dimensionless | 4 | we further derive ND/NH $= (2.44 \pm 0.07) \times 10^{-3}$ |
| ND/NH (v=+5 km/s) | 1.3e-4 | 0.8e-4 | dimensionless | 4 | we obtain a ratio ND/NH = $(1.3 \pm 0.8) \times 10^{-4}$ |
| NH2D/NH3 (v~-4 km/s) | ~3e-3 | not stated | dimensionless | 4 | NH$_2$D/NH$_3$ $\sim 3 \times 10^{-3}$ |
| HDO/H2O (v=-4 km/s) | ~1e-3 | not stated | dimensionless | 4 | we end up with a ratio HDO/H$_2$O $\sim 1 \times 10^{-3}$ |
| HDO/H2O (v~+5 km/s) | ~6e-4 | not stated | dimensionless | 4 | we estimate a ratio HDO/H$_2$O $\sim 6 \times 10^{-4}$ |
| N(7LiH) upper limit (3σ) | 7e9 | not stated | cm-2 | 5 | we then obtain an upper limit of $7 \times 10^9$ cm$^{-2}$ for the column density of $^7$LiH |
| 7LiH/H2 upper limit (PKS 1830-211) | <4e-13 | 3σ | dimensionless | 5 | we derive a stringent upper limit $^7$LiH/H$_2$ $< 4 \times 10^{-13}$ (3$\sigma$) |
| 7LiH/H2 upper limit (B0218+357) | <5e-11 | 3σ | dimensionless | 5 | corresponding to an abundance ratio $^7$LiH/H$_2$ $< 5 \times 10^{-11}$ |
| NH2/NH3 (2012) | ~1 | not stated | dimensionless | 4 | yield a total column density $\sim 3 \times 10^{14}$ cm$^{-2}$ for both, that is, NH$_2$/NH$_3$ $\sim 1$ |

## Qualitative findings

- v~-4 km/s component is chemically peculiar (enhanced CH3OH, N2H+, SO2), variable on months timescales, possibly a cold dark cloud analog  
  > "Overall, these properties suggest that the $v = -4$  km s$^{-1}$ component could be associated with a cold dark cloud similar to those in the Milky Way." (Discussion)
- First detection of SO2 toward PKS 1830-211  
  > "which represents the first detection of SO$_2$ toward PKS 1830$-$211" (3.2)

## Claim tuples

- H: Deuterated molecules are detectable in the z=0.89 absorber | E: ALMA band 6/7 absorption spectra toward the SW image | R: ND, NH2D and HDO detected; fractionation up to ~1e-3 | F: First detection of deuterated species other than HD in this absorber, ~100x primordial D/H in a narrow component | **supported**
- H: Deuterium fractionation differs between velocity components | E: Gaussian decomposition and ratios per component | R: v=+5 component lower by about one order of magnitude | F: Two components have different fractionation | **partially**
- H: The -4 km/s component is a cold dense cloud | E: Compare profiles of many species and time variability | R: Enhanced CH3OH, N2H+, SO2; factor 2 variability in months | F: Speculated to be analog of Galactic dark cloud | **partially**
- H: LiH is detectable in molecular absorbers | E: 7LiH (1-0) spectrum toward PKS 1830-211 and archival B0218+357 | R: No detection; LiH/H2 < 4e-13 | F: Earlier tentative detections toward B0218+357 likely spurious; <1e-4 of Li in LiH | **supported**

## Reasoning

- Why this data: Data were secondary products of two projects not targeting the main isotopologues  
  > "all the D-species were discovered as secondary products of two projects with different science goals" (3.1)
- Why this method: _not stated_
- Alternative: Past 2012/2014 NH3 and H2O spectra not used directly because of time variations  
  > "preclude us from using these past observations directly without careful comparison of reference spectra" (3.1)
- How they decided it was enough: _not stated_
- Limitation (authors): Non-simultaneous XD and XH observations and time variability; high uncertainties  
  > "Measurements of deuterium fractionation toward PKS 1830$-$211 could be improved by simultaneous observations of the XD and XH isotopologues" (Summary and conclusions)
- Limitation (authors): Assumed covering factor of 1  
  > "We further assume that the absorbing gas completely and uniformly covers the background continuum emission from the quasar" (3.1)
- Caveat (inferred, ours): Fractionation ratios depend on assumed NH/NH2/NH3 ratios borrowed from Galactic sources
- Caveat (inferred, ours): Time-variation correction of factor 2 is inferred from CH3OH, not measured for the species
- Caveat (inferred, ours): Tex=TCMB assumption may fail given claimed cold dense component
- Caveat (inferred, ours): Absorption-line covering factor uncertainty for weak lines

## Reproducibility

- Data public (paper): Spectra available at CDS; ALMA data cited with project codes  
  > "Spectra are available in electronic form at the CDS via anonymous ftp to cdsarc.u-strasbg.fr" (Footnote 1)
- Products in archive: _not stated_
- Missing: CASA version, calibrators' flux scale
- Missing: Line-free channel ranges and normalization
- Missing: Fitting code/procedure for Gaussians
- Missing: Exact time-variation correction
- Data volume (inferred): ~100 GB–1 TB raw for three projects
- Score (inferred): 3/5, Data are public and the recipe is simple, but processing details (versions, fitting, line-free channels) and assumed corrections are loosely specified.
- Rediscovery candidate: yes, Archival data, simple spectra extraction and ratios, numeric results, though corrections are partly judgemental.

## Links

- Method: Martí-Vidal et al. 2014 (cite: mar14) (UVMULTIFIT visibility fitting)
- Method: Muller et al. 2013 (cite: mul13) (Excitation locked to CMB and alpha factors)
- Companion: Muller et al. 2014 (cite: mul14) (2012 ALMA spectra of NH2/NH3 and H2 column)
- Companion: Muller et al. 2016b (cite: mul16b) (2014 H2O spectra)

## Checks

```json
{
 "quotes": 71,
 "quotes_ok": 71,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 3,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 11,
 "numeric_problems": 0,
 "fill": {
  "facts": 84,
  "stated": 45,
  "rate": 0.536
 },
 "evidence_ok": true
}
```
