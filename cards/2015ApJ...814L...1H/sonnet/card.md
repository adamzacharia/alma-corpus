# Molecular Gas and Star Formation in the Cartwheel

`2015ApJ...814L...1H` | The Astrophysical Journal Letters 2015 | first author: Higdon, James L. | arXiv: 1511.07227 | DOI: 10.1088/2041-8205/814/1/L1

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, star_formation
- Question: How much molecular gas does the Cartwheel ring galaxy contain in its inner and outer rings, and how does it relate to HI and star formation (SF laws, depletion times)?  
  > "Is AM0644-741 unique or is its ISM characteristic of other large and robustly star forming ring galaxies?" (Introduction)
- Target **Cartwheel ring galaxy**: coordinates _not stated_; z/distance not stated (V_sys = 9138.5 km/s from fit)  
  > "a similarly large ($45$ kpc), evolved (age $\approx R_{\rm ring}/V_{\rm exp} = 440$ Myr), and gas rich (M$_{\rm HI}=2.9\times10^{10}$ M$_{\odot}$) ring galaxy" (Introduction); distance from _not stated_

## Data provenance

- ALMA projects: 2012.1.00720.S
- bands: _not stated_
- frequencies and spectral setup: 468.8 MHz (1256 km/s) bandwidth, 244.2 kHz (0.65 km/s) channels, centered on redshifted 115.2712 GHz line  
  > "The correlator provided a $468.8$ MHz ($1256$ km s$^{-1}$) total bandwidth with $244.2$ kHz ($0.65$ km s$^{-1}$) channels centered on the redshifted $115.2712$ GHz line." (Observations and Analysis)
- continuum bandwidth: _not stated_
- arrays: 7-array (ACA) pointings, mosaic  
  > "The Cartwheel was mosaiced with ALMA using $7$-array pointings on $2013$ December $24$ (2012.1.00720.S)" (Observations and Analysis)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 2.43" x 1.50" (1.47 x 0.91 kpc)  
  > "giving a $2.43\ensuremath{''}\times1.50\ensuremath{''}$ ($1.47\times0.91$ kpc) synthesized beam" (Observations and Analysis)
- max recoverable scale: _not stated_
- sensitivity: 1.39 mJy/beam rms (2 km/s channels)  
  > "a $1.39$ mJy beam$^{-1}$ rms" (Observations and Analysis)
- time on source: _not stated_
- observing dates: 2013 December 24  
  > "on $2013$ December $24$ (2012.1.00720.S)" (Observations and Analysis)
- pi or archival as stated: _not stated_
- Line: 12CO J=1-0 (115.2712 GHz)
- Other facility **VLA**: HI integrated and velocity maps  
  > "Very Large Array integrated HI and velocity maps (cite: wof2)" (Observations and Analysis)
- Other facility **CFHT**: calibrated Halpha image  
  > "a calibrated H$\alpha$ emission-line image from the Canada France Hawaii Telescope" (Observations and Analysis)
- Other facility **Spitzer MIPS**: 24 micron image  
  > "a MIPS $24~\mu$m image" (Observations and Analysis)
- Other facility **MSSSO 2.3m**: long-slit optical spectra of both rings  
  > "long-slit optical spectra of both rings from the Mt. Stromlo & Siding Springs Observatory $2.3$m telescope’s double-beam spectrograph" (Observations and Analysis)
- External data: alpha_CO vs metallicity relation (alpha_CO = 25 for outer ring)  
  > "Fig. $3$ in (cite: magdis) gives $\alpha_{\rm CO} = 25$ M$_{\odot}$ (K km s$^{-1}$ pc$^{2}$)$^{-1}$ for the outer ring" (Observations and Analysis) [from Magdis et al. 2011 (cite: magdis)]
- External data: Galactic alpha_CO  
  > "we adopt a Galactic $\alpha_{\rm CO}$ (cite: strong)" (CO Moment Maps) [from Strong et al. 1988 (cite: strong)]
- External data: HI maps, Halpha, 24um, spectra  
  > "Very Large Array integrated HI and velocity maps (cite: wof2)" (Observations and Analysis) [from Higdon 1996 (cite: wof2)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: CASA 4.2.1  
  > "CASA $4.2.1$ was used for reduction (cite: mcmullin)." (Observations and Analysis)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Uranus (absolute flux scale); J0026-3512 for gains and bandpass  
  > "Antenna gains and bandpass were calibrated using J0026-3512 while observations of Uranus set the absolute flux scale." (Observations and Analysis)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: imager (cube of 600 channels, 2.0 km/s)  
  > "was created and deconvolved using *imager*" (Observations and Analysis)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "A *natural*-weighted image cube consisting of $600$ channels separated by $2.0$ km s$^{-1}$" (Observations and Analysis)
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
- final beam: 2.43" x 1.50"  
  > "giving a $2.43\ensuremath{''}\times1.50\ensuremath{''}$ ($1.47\times0.91$ kpc) synthesized beam" (Observations and Analysis)
- final rms: 1.39 mJy/beam  
  > "a $1.39$ mJy beam$^{-1}$ rms" (Observations and Analysis)

### Inherited from earlier work

- Ring kinematic model with expansion  
  > "we fit its radial velocity distribution with models of rotating circular rings both with and without expansion ($V_{\rm exp}$; see HHR)" (CO Moment Maps) [from HHR (Higdon, Higdon & Rand 2011)]
- Metallicity from line ratios  
  > "used to determine metallicity following (cite: nagao)" (Observations and Analysis) [from (cite: nagao)]
- Extinction formula Halpha+24um  
  > "H$\alpha$ and $24~\mu$m emission is combined to derive internal extinction using" (Observations and Analysis) [from K07]

### Not stated but needed to reproduce (our reading)

- ALMA/ACA flagging and calibration details; whether the archive product or a custom script was used
- Cartwheel distance and redshift used for L'_CO
- Primary beam correction and mask for moment maps
- Velocity range and clipping for moment maps
- Exact definition of the stacking annuli and the HI-velocity shifting
- SFR calibration from Halpha+24um
- Fitting method and uncertainty derivation for the ring kinematic model
- Whether 12-m data were included (only 7-m stated)

## Analysis recipe

1. **Image CO cube and make moment maps**: Natural-weighted cube, moment-0 and moment-1 maps, integrated flux measured  
  > "Integrated line flux (moment-$0$) and flux-weighted radial velocity (moment-$1$) maps are shown in Figs.$~1 ~\& ~2$." (Observations and Analysis)
   - software: CASA
   - fitting: _not stated_
   - validation: Compared total flux with single-dish  
  > "in agreement with single dish observations (cite: horellou), implying that ALMA recovers essentially all of the Cartwheel’s CO emission" (CO Moment Maps)
2. **Derive H2 masses**: CO line luminosity times alpha_CO  
  > "$M_{\rm H_2}$ is derived by multiplying the CO line luminosity ($L^{'}_{\rm CO}$)" (Observations and Analysis)
   - assumption: Galactic alpha_CO for inner ring and nucleus; alpha_CO = 25 for outer ring; factor 1.36 for helium  
  > "All surface densities and masses are scaled by $1.36$ to account for helium." (Observations and Analysis)
   - fitting: _not stated_
   - validation: _not stated_
3. **Fit inner ring kinematics**: Model rotating circular rings with and without expansion fitted to velocity field  
  > "An *expanding* circular ring ($i=56.6^{\circ}$) provides the best fit" (CO Moment Maps)
   - fitting: _not stated_
   - validation: Compared expanding vs non-expanding models  
  > "we fit its radial velocity distribution with models of rotating circular rings both with and without expansion ($V_{\rm exp}$; see HHR). An *expanding* circular ring ($i=56.6^{\circ}$) provides the best fit" (Results and Discussion, CO Moment Maps)
4. **Stack CO spectra in outer ring sections**: Coadd spectra after shifting by HI velocity, smooth (24 km/s boxcar), rebin (8 km/s); later 8 sections with 30 km/s boxcar and 10 km/s rebin  
  > "CO spectra within a given section are coadded after being first shifted using the HI velocity at that position to place the $115$ GHz line at the origin." (CO Stacking Analysis)
   - fitting: _not stated_
   - validation: _not stated_
5. **Compute extinction, metallicity, tau_mol and SF laws**: A_Halpha from Halpha and 24um; metallicity from [NII]/Halpha and [SII]/Halpha; tau_mol = M_H2/SFR; compare to SF laws of spirals  
  > "The Cartwheel’s H$_2$ depletion timescale ($\tau_{\rm mol}=M_{\rm H_2}/SFR$) exhibits a wide range." (H2 Depletion Timescale and Star Formation Law)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.2.1: data reduction and imaging  
  > "CASA $4.2.1$ was used for reduction (cite: mcmullin)." (Observations and Analysis)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Integrated CO flux | 12.86 | 0.28 | Jy km/s | 1 | We measure an integrated line flux of $12.86\pm0.28$ Jy km s$^{-1}$ |
| Inner ring expansion velocity | 68.9 | 4.9 | km/s | 3 | $V_{\rm exp}=68.9\pm4.9$ km s$^{-1}$ |
| Inner ring circular velocity | 170.3 | 5.2 | km/s | 3 | $V_{\rm circ}=170.3\pm5.2$ |
| H2 mass of inner ring (Galactic alpha_CO) | 1.94e9 | 0.04e9 | Msun | 2 | a total $M_{\rm H_2}$ of $(1.94\pm0.04)\times10^{9}$ M$_{\odot}$ |
| H2 mass of outer ring section II | 7.5e8 | 0.8e8 | Msun | 4 | $M_{\rm H_2} = (7.5\pm0.8)\times10^{8}$ M$_{\odot}$ |
| Molecular fraction in section II | 0.10 | 0.01 | dimensionless | 4 | $f_{\rm mol} = 0.10\pm0.01$ |

## Qualitative findings

- Outer ring is H2-poor and its SF is independent of Sigma_H2, Sigma_HI and total gas; inner ring and nucleus H2-dominated and consistent with spiral SF laws.  
  > "The inner ring and nucleus are H$_2$-dominated and are consistent with local spiral SF laws." (abstract)

## Claim tuples

- H: The Cartwheel outer ring has an H2-poor ISM like AM0644-741 | E: Stack CO spectra in outer ring sections using HI velocity shifts | R: CO detected only in HI-rich sections; f_mol ~0.1 or less | F: Outer ring is HI-dominated with low H2 and short tau_mol | **supported**
- H: The inner ring is expanding | E: Fit CO velocity field with ring models | R: V_exp=68.9±4.9 km/s | F: Inner ring age ~70 Myr | **supported**
- H: The outer ring has a peculiar SF law | E: Compare Sigma_SFR with Sigma_H2 and Sigma_HI against spiral SF laws | R: Outer ring SF independent of gas surface density | F: Peculiar SF law, possibly due to CO-faint H2 | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Gas depletion and a brief CO-faint phase rejected as sole explanations  
  > "While gas depletion effects may be at work they cannot be entirely responsible for the observed SF law" (H2 Depletion Timescale and Star Formation Law)
- How they decided it was enough: _not stated_
- Limitation (authors): alpha_CO uncertainty is large and gives a large systematic uncertainty in Sigma_H2  
  > "the wide range in $\Sigma_{\rm H_2}$ allowed by the $\alpha_{\rm CO}$ dispersion, which together comprise a large systematic uncertainty" (H2 Depletion Timescale and Star Formation Law)
- Caveat (inferred, ours): Results depend strongly on the assumed alpha_CO
- Caveat (inferred, ours): Interpretation of CO-faint H2 is untested without dense-gas or dust tracers
- Caveat (inferred, ours): Stacking depends on HI velocity shifts and section definitions

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Calibration scripts and flagging
- Missing: Distance
- Missing: Moment-map masks
- Missing: Ancillary HI/Halpha/24um data from Higdon 1996
- Missing: SFR conversion
- Data volume (inferred): ~5-20 GB
- Score (inferred): 3/5, The ALMA project code and imaging parameters are given, but many analysis details are missing and ancillary data come from earlier papers.
- Rediscovery candidate: no, Key results need ancillary HI/Halpha/24um data and unspecified stacking details.

## Links

- Method: Higdon, Higdon & Rand 2011 (HHR) (Ring kinematic model and AM0644-741 analysis)
- Companion: Higdon 1996 (cite: wof2) (HI, Halpha and optical data on the Cartwheel)
- Related: HERACLES

## Checks

```json
{
 "quotes": 47,
 "quotes_ok": 47,
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
  "facts": 73,
  "stated": 35,
  "rate": 0.479
 },
 "evidence_ok": true
}
```
