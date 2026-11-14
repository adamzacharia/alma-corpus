# ALMA Detection of Vibrationally Excited (v <SUB>t</SUB> = 1, 2) Acetic Acid toward NGC 6334I

`2019ApJ...882..118X` | The Astrophysical Journal 2019 | first author: Xue, Ci | arXiv: 1907.07117 | DOI: 10.3847/1538-4357/ab32e0

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: astrochemistry, star_formation
- Question: Are vibrationally excited (vt = 1, 2) acetic acid lines present toward NGC 6334I, and what are their excitation temperature, column density and spatial distribution?  
  > "Here, we present the first interstellar detection of the first and second vibrationally excited torsional states of acetic acid ($v_\mathrm{t} = 1, 2$) toward the high-mass star-forming region NGC 6334I." (abstract)
- Target **NGC 6334I (MM1, MM2)**: coordinates spectra extracted at RA 17h20m53.374s, Dec -35d46m58.34s (J2000)  
  > "NGC 6334I is a massive star-forming core located at the northeastern end of the NGC 6334 molecular cloud (cite: 2008A&A...481..169B) with a distance of ${\sim} 1.3\,\mathrm{kpc}$ (cite: 2014ApJ...783..130R)." (1 Introduction); "from a single pixel centered at $\alpha_\text{J2000}=17\mathrm{h}20\mathrm{m}53.374\mathrm{s}$, $\delta_\text{J2000}=-35\ensuremath{^\circ}46\ensuremath{'}58.34\ensuremath{''}$." (2 Observations); z/distance ~1.3 kpc  
  > "NGC 6334I is a massive star-forming core located at the northeastern end of the NGC 6334 molecular cloud (cite: 2008A&A...481..169B) with a distance of ${\sim} 1.3\,\mathrm{kpc}$ (cite: 2014ApJ...783..130R)." (1 Introduction); "from a single pixel centered at $\alpha_\text{J2000}=17\mathrm{h}20\mathrm{m}53.374\mathrm{s}$, $\delta_\text{J2000}=-35\ensuremath{^\circ}46\ensuremath{'}58.34\ensuremath{''}$." (2 Observations); distance from Reid et al. 2014 (cite: 2014ApJ...783..130R)  
  > "NGC 6334I is a massive star-forming core located at the northeastern end of the NGC 6334 molecular cloud (cite: 2008A&A...481..169B) with a distance of ${\sim} 1.3\,\mathrm{kpc}$ (cite: 2014ApJ...783..130R)." (1 Introduction); "from a single pixel centered at $\alpha_\text{J2000}=17\mathrm{h}20\mathrm{m}53.374\mathrm{s}$, $\delta_\text{J2000}=-35\ensuremath{^\circ}46\ensuremath{'}58.34\ensuremath{''}$." (2 Observations)

## Data provenance

- ALMA projects: 2017.1.00370.S, 2017.1.00661.S, 2015.A.00022.T
- bands: Bands 4, 6, 7 (130-352 GHz)  
  > "The observations presented were taken with the Atacama Large Millimeter/submillimeter Array in bands 4, 6, and 7 covering a frequency range of 130 – 352 GHz." (abstract)
- frequencies and spectral setup: Band 6 SPW centers 251.4, 251.8, 266.3, 270.7 GHz, 468.75 MHz bandwidth, 0.244 MHz resolution  
  > "| SPW Center Frequency (GHz) | 251.4, 251.8, 266.3, 270.7 |" (Table 1)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: Band 6: C43-5/C43-6  
  > "| Configuration | C43-5/C43-6 |" (Table 1)
- baselines: Band 6: 15 m to 2.5 km  
  > "with a baseline range from 15 m to 2.5 km." (2 Observations)
- angular resolution: Band 6: 0.18'' x 0.15''; smoothed to 0.26'' circular  
  > "The images were smoothed to a 0.26$\ensuremath{''}$ uniform, circular beam size from the image plane for consistency among the 3 datasets." (2 Observations)
- max recoverable scale: ~3''  
  > "the maximum recoverable scale of the ALMA observations presented in this study ($\sim 3 \ensuremath{''}$)" (3.1 Line Identification)
- sensitivity: Band 6 rms 4.0 mJy/beam per channel; Band 4 ~0.8; Band 7 ~2.0 (1.1 mm), 3.3 (0.87 mm)  
  > "| rms per Channel ($\mathrm{mJy\,beam^{-1}}$) | 4.0 |" (Table 1)
- time on source: Band 6: 48 minutes  
  > "| Time on Source (minutes) | 48 |" (Table 1)
- observing dates: Band 6: 2017 December 28  
  > "The Band 6 observation was performed on 2017 December 28" (2 Observations)
- pi or archival as stated: _not stated_
- Line: CH3COOH (acetic acid) vt = 1, 2 torsional excited states; nine line complexes (130306.8 to 282044.2 MHz)
- External data: Spectroscopic data for vt=1,2 acetic acid (frequencies, Eu, Aul) 130-352 GHz  
  > "The spectroscopic data of the vibrationally excited states in the 130-352 GHz frequency range are taken from (cite: 2013JMoSp.290...31I)." (3.1 Line Identification) [from (cite: 2013JMoSp.290...31I)]
- External data: Band 4 and Band 7 ALMA data previously presented  
  > "a detailed description of the Band 4 and 7 data have been presented elsewhere (cite: 2018ApJ...863L..35M; 2017ApJ...837L..29H; 2017ApJ...851L..46M)" (2 Observations) [from (cite: 2018ApJ...863L..35M; 2017ApJ...837L..29H; 2017ApJ...851L..46M)]
- External data: Dust temperatures and densities of MM1/MM2 cores  
  > "Seven dust clumps were resolved toward the hot core MM1, namely MM1A–G, with associated dust temperatures ranging from 116 to 450 K (cite: 2016ApJ...832..187B)." (4 Discussion) [from (cite: 2016ApJ...832..187B)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Band 6: J1517-2422 (bandpass and flux)  
  > "| Bandpass and Flux Calibrator | J1517-2422 |" (Table 1)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA TCLEAN  
  > "were used in the `TCLEAN` task of CASA for imaging, which resulted in elliptical beam shapes." (2 Observations)
- deconvolver: _not stated_
- weighting robust: Briggs, robust 0.5 (Bands 4 and 6), 0.0 (Band 7)  
  > "The Briggs weighting scheme and a Robust parameter of 0.5 for the Band 4 and 6 data and 0.0 for the Band 7 data" (2 Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: UV-plane subtraction using relatively line-free channels  
  > "used to subtract the continuum emission in the UV-plane." (2 Observations)
- line free channels: selected with techniques of Brogan et al. 2018 (channels not listed)  
  > "The relatively line-free continuum channels were selected with the techniques described in (cite: 2018ApJ...866...87B)" (2 Observations)
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: Smoothed to 0.26'' circular beam in image plane  
  > "The images were smoothed to a 0.26$\ensuremath{''}$ uniform, circular beam size from the image plane" (2 Observations)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Line-free channel selection for continuum subtraction  
  > "selected with the techniques described in (cite: 2018ApJ...866...87B)" (2 Observations) [from (cite: 2018ApJ...866...87B)]
- Snyder criteria line identification and P/D factor procedure  
  > "we will highlight the main points here, and refer the reader to Section 3.1 in (cite: 2019ApJ...871..112X) for more detail." (3.1 Line Identification) [from (cite: 2019ApJ...871..112X)]
- Thermalized single-Tex spectral simulation  
  > "we simulated the spectrum of in each state with the assumption that the transitions of are thermalized, as in (cite: 2018ApJ...863L..35M)." (3.1 Line Identification) [from (cite: 2018ApJ...863L..35M)]

### Not stated but needed to reproduce (our reading)

- Actual line-free channel ranges
- CASA version
- Calibration/pipeline details and flux uncertainty
- tclean cell size, image size, niter, threshold, masks
- Details of Gaussian fits and chi2 fit implementation
- How T_bg values were measured
- Band 4 and Band 7 observing parameters (arrays, dates) in this paper

## Analysis recipe

1. **Image and continuum-subtract**: UV-plane continuum subtraction, tclean imaging, smoothing to 0.26'' beam  
  > "used to subtract the continuum emission in the UV-plane." (2 Observations)
   - software: CASA
   - parameter: Briggs robust 0.5 (B4, B6), 0.0 (B7)  
  > "a Robust parameter of 0.5 for the Band 4 and 6 data and 0.0 for the Band 7 data" (2 Observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **Simulate LTE spectra and identify lines**: Simulate thermalized spectra per Turner 1991 with background continuum; apply Snyder criteria and P/D factors  
  > "Following the convention of (cite: 1991ApJS...76..617T), we simulated the spectrum of in each state with the assumption that the transitions of are thermalized" (3.1 Line Identification)
   - parameter: Tbg 11.5, 27.4, 33.9, 43.1 K for Band 4, Band 6, Band 7 1.1 mm, 0.87 mm  
  > "$T_\mathrm{bg}$ is estimated to be $11.5~\mathrm{K}$, $27.4~\mathrm{K}$, $33.9~\mathrm{K}$ and $43.1~\mathrm{K}$" (3.1 Line Identification)
   - assumption: Negligible beam dilution; thermalized transitions since n_H2 >> n_crit (~1e5 cm-3)  
  > "As $n_\text{\ce{H2}} \gg n_\mathrm{crit}$, it is reasonable to assume that these transitions are thermalized toward MM1." (3.1 Line Identification)
   - fitting: _not stated_
   - validation: Six vt=1 and three vt=2 clean features identified using P and D factors  
  > "We identify a total of six $v_\mathrm{t} = 1$ features and three $v_\mathrm{t} = 2$ features" (3.1 Line Identification)
3. **Fit Tex and column density**: chi2 fit of single-Tex model to clean features only, with dV and Vlsr fixed to medians  
  > "$\chi^2$ fitting is performed to statistically optimize the model and determine $T_\mathrm{ex}$ and $N_\mathrm{T}$." (3.1 Line Identification)
   - parameter: dV = 2.72 km/s, Vlsr = -6.90 km/s fixed  
  > "The $\Delta V$ is fixed to $2.72~\mathrm{km\,s^{-1}}$ and the $V_\mathrm{lsr}$ is fixed to $-6.90~\mathrm{km\,s^{-1}}$." (3.1 Line Identification)
   - assumption: Partition function approximated by sixth-order polynomial  
  > "The torsional-rotational partition function $Q_\mathrm{rv}$ is approximated by fitting the total internal partition function as a function of temperature ($T$) using a sixth order polynomial" (3.1 Line Identification)
   - fitting: chi2 minimization; errors from inverse Hessian plus rms propagation (1 sigma)  
  > "which include the fitting error derived from the inverse of the Hessian matrix and the error propagation from the rms noise of the observed spectra." (3.1 Line Identification)
   - validation: Compared with ground-state results of El-Abd et al. (Tex 135 K, N 1.24e17)  
  > "who measure an $N_\mathrm{T}$ of $1.24 \times 10^{17}~\mathrm{cm^{-2}}$ and a $T_\mathrm{ex}$ of 135 K" (3.1 Line Identification)
4. **Map peak intensity and locate emission peaks**: Peak intensity maps over Vlsr -3 to -9 km/s compared with 287 GHz continuum; two contaminated maps discarded  
  > "All the 9 peak intensity maps of vibrationally excited within the $V_\mathrm{lsr}$ range of $-3$ to $-9~\mathrm{km\,s^{-1}}$ are presented in color." (3.2 Spatial Distribution)
   - fitting: _not stated_
   - validation: Spatial coherence among transitions used to rule out contamination  
  > "the spatial distribution coherence can serve as an additional criterion for securing the morphology determination" (3.2 Spatial Distribution)

## Software

- **CASA** : Data analysis, continuum subtraction and tclean imaging  
  > "The data have been analyzed with the Common Astronomy Software Applications (CASA) package" (2 Observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Excitation temperature | 142 | 25 K | K | 3 | the best-fit excitation temperature and column density are obtained to be 142(25) K and $1.12(7) \times 10^{17} \mathrm{cm^{-2}}$ respectively |
| Column density | 1.12e17 | 0.07e17 | cm^-2 | 3 | $1.12(7) \times 10^{17} \mathrm{cm^{-2}}$ |
| Line width (fixed) | 2.72 | not stated | km/s | 3 | The $\Delta V$ is fixed to $2.72~\mathrm{km\,s^{-1}}$ |
| Source size toward MM1 | ~2'' x 1.2'' | not stated | arcsec | 4 | is resolved to be $\sim 2 \ensuremath{''} \times 1.2\ensuremath{''}$ toward MM1 and $\sim 1 \ensuremath{''} \times 0.4\ensuremath{''}$ toward MM2 |

## Qualitative findings

- Emission is compact and concentrated toward MM1 and MM2, offset from continuum peaks  
  > "we found that the emissions are compact and concentrated toward the MM1 and MM2 regions with a source size smaller than 2$''$." (abstract)

## Claim tuples

- H: Vibrationally excited acetic acid is detectable toward NGC 6334I | E: Line identification with Snyder criteria and P/D factors over Bands 4, 6, 7 | R: Six vt=1 and three vt=2 clean features | F: First interstellar detection of vt=1,2 acetic acid | **supported**
- H: A single Tex model describes the emission | E: chi2 fit to clean features | R: Tex 142(25) K, N 1.12(7)e17 cm-2 | F: Consistent with ground-state values | **supported**
- H: Variation of AcA3 peak positions has a physical cause | E: Compared peak positions of transitions across Eu and frequency | R: AcA3 peaks shift with energy/frequency | F: Explained by continuum absorption or outflows; cannot be distinguished | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Dust opacity vs outflow explanations for AcA3 shift both considered; undistinguished  
  > "Although both of the mechanisms could account for the change in the AcA3 peak positions" (4 Discussion)
- How they decided it was enough: _not stated_
- Limitation (authors): Uncertainties may be underestimated since continuum subtraction systematics not included  
  > "the uncertainties listed here might be underestimated as we have not incorporated the systematic uncertainties introduced by continuum subtraction." (3.1 Line Identification)
- Caveat (inferred, ours): Tex and N fit uses only 9 clean features with fixed dV and Vlsr
- Caveat (inferred, ours): Assumes LTE and negligible beam dilution with source size not fitted
- Caveat (inferred, ours): Offset interpretation degenerate between opacity and outflow

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Line-free channels
- Missing: CASA version and calibration details
- Missing: Imaging parameters beyond robust
- Missing: Fit code
- Data volume (inferred): Several hundred GB across three projects
- Score (inferred): 5/5, Projects are named and the fitting recipe is described, but imaging details, CASA version and the fitting code are missing.
- Rediscovery candidate: no, Key imaging and calibration details are missing, and line identification relies on inherited procedures.

## Links

- Method: (cite: 2019ApJ...871..112X) (Line identification and P/D factor method)
- Method: (cite: 2005ApJ...619..914S) (Snyder criteria)
- Companion: (cite: 2018ApJ...863L..35M) (Band 4 data and single-Tex approach)

## Checks

```json
{
 "quotes": 57,
 "quotes_ok": 57,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 3,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 4,
 "numeric_problems": 0,
 "fill": {
  "facts": 70,
  "stated": 42,
  "rate": 0.6
 },
 "evidence_ok": true
}
```
