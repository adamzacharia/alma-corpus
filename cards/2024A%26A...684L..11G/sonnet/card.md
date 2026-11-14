# A spectacular galactic scale magnetohydrodynamic powered wind in ESO 320-G030

`2024A&A...684L..11G` | Astronomy and Astrophysics 2024 | first author: Gorski, M. D. | arXiv: 2403.16759 | DOI: 10.1051/0004-6361/202348821

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, agn_and_quasars
- Question: What powers the molecular outflow in the compact obscured nucleus of ESO 320-G030 (AGN, starburst, jet, or MHD wind)?  
  > "we are able to reveal the launching region of the molecular outflow." (Introduction); "Our findings on the wind origin are summarized in Section [5](#sec:conclusions)." (Introduction)
- Target **ESO 320-G030 (IRAS F11506-3851)**: coordinates _not stated_; z/distance 36 Mpc (z = 0.0103)  
  > "It has a luminosity distance of 36 Mpc ($z = 0.0103$) (cite: Sanders2003)" (Introduction); distance from Sanders2003, flat cosmology H0=75, OmegaM=0.3, OmegaL=0.7  
  > "It has a luminosity distance of 36 Mpc ($z = 0.0103$) (cite: Sanders2003)" (Introduction)

## Data provenance

- ALMA projects: 2019.1.01612.S
- bands: _not stated_
- frequencies and spectral setup: two 1.875 GHz SPWs (240 channels) at 265.005 and 263.182 GHz; two 2.000 GHz SPWs (128 channels) at 248.447 and 250.427 GHz  
  > "The spectral setup consists of two 1.875 GHz spectral windows containing 240 channels centred at 265.005 GHz and 263.182 GHz." (2 Observations); "Two additional 2.000 GHz spectral windows with 128 channels are centred at 248.447 GHz and 250.427 GHz." (2 Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: longest baseline 16.2 km  
  > "The longest baseline was 16.2 km corresponding to the highest possible angular resolution of 20 mas at 260 GHz." (2 Observations)
- angular resolution: 30.9 mas x 28.8 mas natural-weighted original beam  
  > "The original synthesized beam is 30.9 mas $\times$ 28.8 mas with a natural weighting of the visibilities." (2 Observations)
- max recoverable scale: 0.4 arcsec  
  > "The fifth percentile baseline length corresponds to a maximum recoverable scale of 0.4$''$." (2 Observations)
- sensitivity: 0.22 mJy/beam per 18 MHz channel; continuum 21 uJy/beam  
  > "resulting in a root-mean-square (rms) of 0.22 mJy beam$^{-1}$." (2 Observations); "with a rms of 21 $\mu$Jy beam$^{-1}$" (3.1 Continuum)
- time on source: _not stated_
- observing dates: two scheduling blocks on 6 Sept 2021, one on 28 Sept 2021  
  > "two from September 6, 2021, and one from September 28, 2021" (2 Observations)
- pi or archival as stated: CONfirm project, PI Falstad  
  > "Our ALMA observations are part of the CONfirm project (PI Falstad, N., project code 2019.1.01612.S)" (2 Observations)
- Line: HCN v=0 J=3-2 (265.8864343 GHz)
- Line: HCN v2=1f J=3-2 (HCN-vib) (267.19928300 GHz)
- External data: Black hole mass 5e6-8e6 Msun from M_BH/sigma  
  > "(cite: Gonzalez-Alfonso2021) estimate the mass of the black hole, from the $M_{\rm BH}/\sigma$ relation, to be between 5$\times10^6$ M$_{\odot}$ and 8$\times10^6$ M$_{\odot}$." (3.3 Outflow momentum) [from Gonzalez-Alfonso2021]
- External data: Infrared luminosity ~1e11 Lsun and distance  
  > "it has an infrared luminosity of $\sim10^{11}$ L$_{\odot}$  (cite: Sanders2003)" (Introduction) [from Sanders2003]

## Processing

### Calibration

- pipeline or manual: calibration done in CASA; pipeline vs manual not stated  
  > "The calibration of and imaging of the data were done in CASA (cite: CASATeam2022PASP)." (2 Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "with a natural weighting of the visibilities" (2 Observations)
- uv taper: _not stated_
- cell size: 6.5 mas pixels  
  > "with 6.5 mas pixels" (2 Observations)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: STATCONT, sigma clipping, rms 0.22 mJy/beam per channel  
  > "We utilized the sigma clipping method and specify a rms of 0.22 mJy beam$^{-1}$ per channel." (3.2 HCN emission)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: Hanning kernel to 36 MHz (~40 km/s) giving rms 0.14 mJy/beam  
  > "degrading the spectral resolution to 36 MHz ($\sim 40$ km s$^{-1}$) and thus improving the rms to 0.14 mJy beam$^{-1}$" (4.1.1 Outflow morphology)
- final beam: 31 mas x 31 mas common beam  
  > "imaged to a common beam of 31 mas $\times$ 31 mas" (2 Observations)
- final rms: 0.22 mJy/beam per channel  
  > "resulting in a root-mean-square (rms) of 0.22 mJy beam$^{-1}$." (2 Observations)

### Inherited from earlier work

- HCN3-2 to 1-0 line ratio of 0.5  
  > "assuming a line ratio of 0.5 as in (cite: Aalto2015a)" (4.1.1 Outflow morphology) [from Aalto2015a]
- L(HCN)-to-H2 conversion calibrated by Gao & Solomon, modified for ULIRGs by Garcia-Burillo  
  > "we utilized the L(HCN)-to-H$_{2}$ conversion factor, calibrated for HCN J=1-0 (cite: Gao2004)" (4.1.1 Outflow morphology) [from Gao2004; Garcia-Burillo2012]
- Outflow kinetic energy formula  
  > "The kinetic energy of the outflow is $E_{\rm outflow}=(0.5  M_{\rm out} \times V_{\rm out}^2) + E_{\rm turb}$ (cite: Veilleux2001)." (3.3 Outflow momentum) [from Veilleux2001]

### Not stated but needed to reproduce (our reading)

- CASA version and whether pipeline or manual calibration
- flux, bandpass and phase calibrators and flux uncertainty
- self-calibration use
- clean threshold, mask and niter
- line-free channels used for continuum
- exact integration channel ranges for the outflow maps
- how radius and luminosity were measured and the mass-to-flux conversion details
- how the outflow rate and momentum flux were computed
- STATCONT parameters beyond sigma clipping

## Analysis recipe

1. **Image cubes and continuum**: Calibrate and image in CASA; common beam 31 mas; continuum from both 2 GHz SPWs plus line-free channels of the 1.875 GHz SPWs  
  > "We have combined the two 2.0 GHz spectral windows and the line-free channels from the 1.875 GHz spectral windows to generate a 256 GHz continuum image" (3.1 Continuum)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Fit continuum size**: 2D Gaussian fit masking pixels below 80% of peak  
  > "A two-dimensional Gaussian fit to the continuum emission, masking pixels below 80% of the peak intensity" (3.1 Continuum)
   - assumption: distance 36 Mpc; inclination from axial ratio  
  > "We adopted the inclination derived from the axial ratio of the continuum of 63.4$\pm$0.5$^{\circ}$" (3.3 Outflow momentum)
   - fitting: _not stated_
   - validation: _not stated_
3. **Continuum subtraction and moment maps**: STATCONT pixel-by-pixel continuum subtraction; moment 0 and 1 maps with >3 sigma pixels  
  > "The intensity-weighted velocity maps only include pixels $>3\times$ rms of the data cube." (3.2 HCN emission)
   - software: STATCONT
   - fitting: _not stated_
   - validation: _not stated_
4. **Outflow maps and mass**: Integrate channels with |v-vsys|>100 km/s chosen by eye; convert HCN 3-2 luminosity to 1-0 and to mass  
  > "We included channels that, by eye, are dominated by the outflow $|v-v_{sys}|>100$ km s$^{-1}$" (4.1.1 Outflow morphology)
   - parameter: line ratio 0.5; M_dense ~3.1 Msun/(K km/s pc2) x L'(HCN 1-0)  
  > "The conversion is $M_{\rm dense}\approx$ 3.1 M$_{\odot}$/L$^{\prime-1}$ $\times \rm{L}(\rm{HCN}~1\rm{-}0)$" (4.1.1 Outflow morphology)
   - assumption: mass is a lower limit  
  > "The mass is a lower limit as only the higher velocity gas is included in the outflow maps" (4.1.1 Outflow morphology)
   - fitting: _not stated_
   - validation: _not stated_
5. **Outflow energetics and momentum flux**: Kinetic energy 0.5 M V^2, turbulence neglected; deproject velocity with inclination; compute mechanical luminosity, outflow rate, momentum flux; compare with L_Edd/c and L_IR/c  
  > "We assumed that turbulent kinetic energy is insignificant." (3.3 Outflow momentum)
   - parameter: projected velocity 217±14 km/s; radius 52 pc  
  > "For a projected velocity of 217$\pm$14 km s$^{-1}$" (3.3 Outflow momentum)
   - fitting: _not stated_
   - validation: Compared to literature momentum limits for AGN and starburst winds  
  > "as this exceeds the factor of five limit estimated by (cite: Roth2012)" (3.3 Outflow momentum)

## Software

- **CASA** : calibration and imaging  
  > "The calibration of and imaging of the data were done in CASA (cite: CASATeam2022PASP)." (2 Observations)
- **STATCONT** : continuum subtraction of cubes  
  > "We used the `STATCONT` software package (cite: SanchezMonge2018) to perform the continuum subtraction on the image cubes." (3.2 HCN emission)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Deconvolved continuum FWHM major | 68.2 | 0.8 | mas | 2 | FWHM) of 68.2$\pm$0.8 mas by 30.5$\pm$0.4 mas |
| Continuum position angle | 120.8 | 0.5 | deg | 2 | at a position angle of 120.8$\pm0.5$$^{\circ}$ |
| Outflow mass | 2.1e7 | not stated | Msun | 4 | obtained an outflow mass of $2.1\times10^7$ M$_{\odot}$  within a radius of 52 pc |
| HCN 3-2 outflow luminosity | 3.4e6 | 0.1e6 | K km/s pc^2 | 4 | $3.4\pm0.1\times10^6$ K km s$^{-1}$ pc$^{-2}$ |
| Outflow velocity | 515 | 33 | km/s | 5 | $V_{\rm out}=515\pm33$ km s$^{-1}$ |
| Kinetic energy | 6.5e55 | 0.8e55 | erg | 5 | $(6.5\pm0.8)\times10^{55}$ erg |
| Outflow rate | 231 | 15 | Msun/yr | 5 | $231\pm15$ M$_{\odot}$ yr$^{-1}$ |
| Momentum flux | 30 | 7 | L_Edd/c | 5 | The momentum flux of the outflow is $30\pm7 \times L_{\rm Edd}/c$ |
| Momentum flux relative to L_IR/c | 63 | 8 | dimensionless | 5 | by a factor of $63\pm8$ |

## Qualitative findings

- Outflow shows rotation and launch regions connected to the rotating nuclear structure  
  > "the launching regions are apparent and connected to the rotating nuclear structure in the innermost $\sim12$ pc" (4.1.1 Outflow morphology)

## Claim tuples

- H: The outflow is driven by AGN or starburst momentum | E: Outflow mass and momentum flux compared with limits | R: Momentum flux 30 L_Edd/c and 63 L_IR/c | F: Momentum-driven AGN and starburst unlikely | **supported**
- H: The outflow is an MHD wind | E: Morpho-kinematics of HCN outflow, plus absence of AGN, jet and ionized outflow evidence | R: Rotating outflow launched from rotating nucleus | F: MHD wind most likely | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Radio jet rejected as incorrectly oriented; energy-driven AGN rejected for lack of AGN indicators  
  > "however, it is incorrectly oriented to power the molecular outflow" (3.4 The outflow power source)
- How they decided it was enough: _not stated_
- Limitation (authors): Mass, rate and momentum flux are lower limits  
  > "It is important to note that the following result is a lower limit to the outflow rate and momentum flux." (3.3 Outflow momentum)
- Caveat (inferred, ours): MHD wind conclusion is by elimination and analogy with protostars
- Caveat (inferred, ours): HCN-to-mass conversion and 0.5 line ratio are highly uncertain
- Caveat (inferred, ours): channels chosen by eye
- Caveat (inferred, ours): no kinematic modelling to prove rotation of outflow
- Caveat (inferred, ours): inclination from continuum axial ratio assumed for outflow

## Reproducibility

- Data public (paper): ALMA data cited by project code; public status not stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2019.1.01612.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: CASA version and calibration details
- Missing: imaging cleaning parameters
- Missing: exact channel ranges and aperture for outflow flux
- Missing: STATCONT settings
- Data volume (inferred): ~100-300 GB raw for three long-baseline EBs
- Score (inferred): 4/5, Data identified and main steps described, but calibration and imaging parameters and the channel ranges are missing.
- Rediscovery candidate: no, Key processing and measurement choices are unstated, so reproduction would be approximate.

## Links

- Method: SanchezMonge2018 (STATCONT continuum subtraction)
- Companion: Falstad2021 (CON identification of ESO 320-G030)
- Companion: Gorski2023 (protostellar analogy for MHD winds)
- Related: CONfirm

## Checks

```json
{
 "quotes": 56,
 "quotes_ok": 56,
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
  "facts": 72,
  "stated": 38,
  "rate": 0.528
 },
 "evidence_ok": true
}
```
