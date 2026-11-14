# Subaru High-z Exploration of Low-Luminosity Quasars (SHELLQs). VIII. A less biased view of the early co-evolution of black holes and host galaxies

`2019PASJ...71..111I` | Publications of the Astronomical Society of Japan 2019 | first author: Izumi, Takuma | arXiv: 1904.07345 | DOI: 10.1093/pasj/psz096

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies, agn_and_quasars
- Question: Do low-luminosity z>6 quasars follow the local M_BH-M_bulge relation, and what are their [CII] and FIR properties, in a less luminosity-biased sample?  
  > "Given the low luminosities of our targets, we are exploring the nature of the early co-evolution of supermassive black holes and their hosts in a less biased way." (abstract)
- Target **J1208-0200**: coordinates _not stated_; z/distance z_[CII] = 6.1165  
  > "$z_{\rm Ly\alpha}$ | 6.2$^\dag$ | 6.08 | 6.26$^\dag$" (Table 1); distance from [CII] line fit (this paper)  
  > "$z_{\rm Ly\alpha}$ | 6.2$^\dag$ | 6.08 | 6.26$^\dag$" (Table 1)
- Target **J2228+0152**: coordinates _not stated_; z/distance z_[CII] = 6.0805  
  > "$z_{\rm Ly\alpha}$ | 6.2$^\dag$ | 6.08 | 6.26$^\dag$" (Table 1); distance from [CII] line fit (this paper)  
  > "$z_{\rm Ly\alpha}$ | 6.2$^\dag$ | 6.08 | 6.26$^\dag$" (Table 1)
- Target **J2239+0207**: coordinates _not stated_; z/distance z_[CII] = 6.2497  
  > "$z_{\rm Ly\alpha}$ | 6.2$^\dag$ | 6.08 | 6.26$^\dag$" (Table 1); distance from [CII] line fit (this paper)  
  > "$z_{\rm Ly\alpha}$ | 6.2$^\dag$ | 6.08 | 6.26$^\dag$" (Table 1)

## Data provenance

- ALMA projects: 2017.1.00541.S
- bands: Band 6  
  > "observed during ALMA Cycle 5 (ID = 2017.1.00541.S, PI: T. Izumi) at band 6 between 2018 March 20 and 26" (2 Observations and data reduction)
- frequencies and spectral setup: J2228+0152: 4 spws of 1.875 GHz (~7.5 GHz); others: 3 spws (~5.6 GHz) in one sideband; native 7.813 MHz, binned to ~100 km/s  
  > "The native spectral resolution was 7.813 MHz (8.7–8.9 km s$^{-1}$), but 11–12 channels were binned to improve the signal-to-noise ratio ($S/N$), resulting in a final common velocity resolution of $\simeq 100$ km s$^{-1}$." (2 Observations and data reduction)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 15.1–783.5 m  
  > "Baseline (m) | 15.1–783.5 | 15.1–783.5 | 15.1–783.5" (Table 1)
- angular resolution: ~0.4-0.5 arcsec beams  
  > "Beam size | 0$\ensuremath{''}$.48 $\times$ 0$\ensuremath{''}$.39 | 0$\ensuremath{''}$.44 $\times$ 0$\ensuremath{''}$.40 | 0$\ensuremath{''}$.45 $\times$ 0$\ensuremath{''}$.38" (Table 1)
- max recoverable scale: ~9.5 arcsec  
  > "With the minimum baseline length (15.1 m), the maximum recoverable scales of our observations are $\sim 9.5\ensuremath{''}$." (2 Observations and data reduction)
- sensitivity: [CII] cube rms 0.10, 0.10, 0.11 mJy/beam per 100 km/s; continuum rms 16.3, 11.2, 19.1 uJy/beam  
  > "rms noise per 100 km s$^{-1}$            | 0.10                                                 | 0.10                                                 | 0.11" (Table 1)
- time on source: 87, 87, 65 min (J1208, J2228, J2239)  
  > "On-source time (minutes) | 87 | 87 | 65" (Table 1)
- observing dates: 2018 March 20-26  
  > "at band 6 between 2018 March 20 and 26" (2 Observations and data reduction)
- pi or archival as stated: PI: T. Izumi  
  > "(ID = 2017.1.00541.S, PI: T. Izumi)" (2 Observations and data reduction)
- Line: [CII] 2P3/2 -> 2P1/2 (157.74 um) (1900.5369 GHz)
- Other facility **Subaru HSC**: Discovery of quasars and HSC optical photometry of a continuum emitter  
  > "We found that this object is also detected in the HSC optical bands as $g = 25.12 \pm 0.21$ mag" (4.4 Continuum emitters)
- External data: Mg II-based M_BH of J1208-0200 and J2239+0207, Mg II redshifts, CIV blueshifts  
  > "$M_{\rm BH}$ of J1208$-$0200 and J2239+0207 are measured with Mg  emission line, which are reported in (cite: Onoue19)." (4.2.1) [from (cite: Onoue19)]
- External data: Literature compilation of M_BH, M_1450, L_FIR, [CII] data for z>~6 quasars  
  > "We also compiled $M_{\rm BH}$ and $M_{\rm 1450}$ values of other $z \geq 5.7$ quasars from the literature" (4.2.1) [from (cite: 2018ApJ...854...97D); (cite: 2018ApJ...866..159V)]
- External data: Cycle 4 HSC quasar results  
  > "In (cite: 2018PASJ...70...36I), we presented Cycle 4 ALMA observations toward four $z \gtrsim 6$ HSC quasars in the [C ] line and 1.2 mm continuum." (1 Introduction) [from (cite: 2018PASJ...70...36I)]

## Processing

### Calibration

- pipeline or manual: standard manner  
  > "Reduction and calibration of the data were performed with the Common Astronomy Software Applications package (cite: 2007ASPC..376..127M) version 5.1.1, in the standard manner." (2 Observations and data reduction)
- casa version: CASA 5.1.1  
  > "Common Astronomy Software Applications package (cite: 2007ASPC..376..127M) version 5.1.1" (2 Observations and data reduction)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J1229+0203 (J1208) and J2148+0657 (J2228, J2239)  
  > "Flux calibrator                          | J1229+0203                                         | J2148+0657                                         | J2148+0657" (Table 1)
- flux scale uncertainty: 10%  
  > "The systematic uncertainty of the absolute flux calibration at ALMA band 6 is 10%, according to the ALMA Cycle 5 Proposer’s Guide." (2 Observations and data reduction)
- self calibration: _not stated_

### Imaging

- task: CASA clean  
  > "All images were reconstructed with the CASA task `clean` with the Briggs weighting (gain = 0.1, robust = 0.5)." (2 Observations and data reduction)
- deconvolver: _not stated_
- weighting robust: Briggs robust = 0.5, gain = 0.1  
  > "with the Briggs weighting (gain = 0.1, robust = 0.5)" (2 Observations and data reduction)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: line-free channels averaged for continuum, subtracted in uv plane  
  > "which was subtracted in the $uv$ plane before making the line cube." (2 Observations and data reduction)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: channels binned to ~100 km/s  
  > "11–12 channels were binned to improve the signal-to-noise ratio" (2 Observations and data reduction)
- final beam: see Table 1 ([CII] ~0.44-0.48 x 0.38-0.40 arcsec)  
  > "Beam size | 0$\ensuremath{''}$.48 $\times$ 0$\ensuremath{''}$.39 | 0$\ensuremath{''}$.44 $\times$ 0$\ensuremath{''}$.40 | 0$\ensuremath{''}$.45 $\times$ 0$\ensuremath{''}$.38" (Table 1)
- final rms: 0.10/0.10/0.11 mJy/beam per 100 km/s  
  > "rms noise per 100 km s$^{-1}$            | 0.10                                                 | 0.10                                                 | 0.11" (Table 1)

### Inherited from earlier work

- Graybody Td=47 K, beta=1.6 for L_FIR, for consistency with previous work  
  > "to be consistent with previous work (cite: 2013ApJ...773...44W; 2013ApJ...770...13W; 2016ApJ...816...37V)" (3.2 FIR continuum properties) [from (cite: 2013ApJ...773...44W; 2013ApJ...770...13W; 2016ApJ...816...37V)]
- Thin rotating disk M_dyn procedure  
  > "by following the standard procedure used in $z \gtrsim 6$ quasar studies" (4.2.1) [from (cite: 2013ApJ...773...44W; 2015ApJ...801..123W; 2016ApJ...816...37V; 2018PASJ...70...36I)]
- M_BH from Mg II virial calibration; procedure details  
  > "Details of the procedure are described in (cite: Onoue19)." (4.2.1) [from (cite: Onoue19); (cite: 2009ApJ...699..800V)]

### Not stated but needed to reproduce (our reading)

- Line-free channel ranges used for the continuum
- Cell size, image size, masks and clean threshold
- Velocity range for moment 0 maps (only given for J2239+0207)
- Aperture centering and spectrum extraction details for the 1 arcsec aperture
- Gaussian fit initial conditions and baseline treatment for line fits
- Radiative efficiency eta used for Mdot_BH
- Inclination handling for sources with axis ratios near unity
- Exact coordinates (lost in table conversion)

## Analysis recipe

1. **Calibrate and image cubes and continuum**: CASA calibration; clean with Briggs weighting; uv-plane continuum subtraction; channels binned to ~100 km/s  
  > "All images were reconstructed with the CASA task `clean` with the Briggs weighting (gain = 0.1, robust = 0.5)." (2 Observations and data reduction)
   - software: CASA
   - parameter: robust = 0.5, gain = 0.1  
  > "(gain = 0.1, robust = 0.5)" (2 Observations and data reduction)
   - fitting: _not stated_
   - validation: _not stated_
2. **Measure [CII] line properties**: Single Gaussian fit to 1 arcsec aperture spectra for z, FWHM, flux; L_CII from standard equation  
  > "we simply fitted each spectrum with a single Gaussian profile, which delivered the velocity centroid" (3.1 [CII] line properties)
   - software: CASA
   - fitting: single Gaussian  
  > "we simply fitted each spectrum with a single Gaussian profile" (3.1 [CII] line properties)
   - validation: _not stated_
3. **Measure spatial extents**: 2D Gaussian fit to moment 0 maps at original resolution  
  > "We used the CASA task `imfit` to fit a two-dimensional Gaussian profile to the [C ] integrated intensity (0$^{\rm th}$ moment) maps" (3.1 [CII] line properties)
   - software: CASA imfit, CASA immoments
   - fitting: _not stated_
   - validation: _not stated_
4. **Derive FIR luminosity, SFR, dust mass**: Graybody scaling of 1.2 mm flux in 1 arcsec aperture; L_FIR over 42.5-122.5 um; SFR_TIR and SFR_CII relations; dust mass from kappa  
  > "Here we assume a graybody spectrum with dust temperature of $T_{\rm d} = 47$ K and emissivity index of $\beta = 1.6$" (3.2 FIR continuum properties)
   - assumption: Td=47 K, beta=1.6, kappa_250=0.4 cm2/g  
  > "Assumption: $T_{\rm d}$ = 47 K, $\beta$ = 1.6, $\kappa_{\rm 250}$ = 0.4 cm$^2$ g$^{-1}$" (Table 2)
   - fitting: _not stated_
   - validation: Compared with lower Td: L_FIR ~3x lower  
  > "the resultant inferred $L_{\rm FIR}$ values would be $\sim 3 \times$ lower." (3.2 FIR continuum properties)
5. **Compute dynamical masses**: Thin disk: v_circ=0.75 FWHM/sin i, D=1.5 a_maj, M_dyn=1.16e5 v^2 D  
  > "The circular velocity is expressed as $v_{\rm circ} = 0.75 {\rm FWHM}_{\rm [C\,\emissiontype{II}] }/\sin i$." (4.2.1)
   - assumption: Thin rotating circular disk; inclination from axis ratio  
  > "Here the [C ] emission is assumed to originate from a thin rotating circular disk." (4.2.1)
   - fitting: _not stated_
   - validation: _not stated_
6. **Compare M_BH-M_dyn and L_Bol-L_FIR with literature**: Compiled literature quasars; linear regression with upper limits via IRAF STSDAS; Spearman tests  
  > "Fitting a linear regression, including the upper limits, we find" (4.2.2)
   - software: IRAF STSDAS
   - assumption: Eddington-limited accretion where no Mg II M_BH; bolometric correction 4.4  
  > "The bolometric luminosity was calculated from the 1450 Å monochromatic luminosity with a correction factor of 4.4" (4.2.1)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 5.1.1: calibration, clean imaging, immoments, imfit  
  > "Common Astronomy Software Applications package (cite: 2007ASPC..376..127M) version 5.1.1" (2 Observations and data reduction)
- **MIRIAD** : [CII] velocity channel maps  
  > "we constructed [C ] velocity channel maps of J2228+0152 using the MIRIAD software" (3.3)
- **IRAF STSDAS** : linear regression with upper limits  
  > "using the IRAF STSDAS package" (4.2.2)
- **Mizuki** : HSC photometric redshift of a continuum emitter  
  > "along with the Bayesian-based Mizuki code" (4.4)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| L_[CII] range | (2.4-9.5)e8 | not stated | L_sun | 2 | luminosities of $(2.4 - 9.5) \times 10^8~L_\odot$ |
| FWHM_[CII] J1208/J2228/J2239 | 184 / 266 / 607 | 28 / 48 / 44 | km/s | 2 | FWHM$_{\rm [C\,\emissiontype{II}] }$ (km s$^{-1}$)        / 184 $\pm$ 28                                / 266 $\pm$ 48                                / 607 $\pm$ 44 |
| z_[CII] J1208/J2228/J2239 | 6.1165 / 6.0805 / 6.2497 | 0.0002 / 0.0004 / 0.0004 | dimensionless | 2 | 6.1165 $\pm$ 0.0002                         / 6.0805 $\pm$ 0.0004                         / 6.2497 $\pm$ 0.0004 |
| L_FIR J1208/J2228/J2239 | 1.62 / <0.94 / 21.74 (1e11) | 0.37 / - / 0.51 | L_sun | 4 | $L_{\rm FIR}$ (10$^{11}$ $L_\odot$)                       / 1.62 $\pm$ 0.37                             / $<$0.94                                     / 21.74 $\pm$ 0.51 |
| 1.2 mm flux density | 85 / <47 / 1110 | 20 / - / 26 | uJy | 4 | $f_{\rm 1.2mm}$ ($\mu$Jy)                                 / 85 $\pm$ 20                                 / $<$47                                       / 1110 $\pm$ 26 |
| SFR_[CII] | 18 / 16 / 63 | 4 / 5 / 8 | Msun/yr | 4 | SFR$_{\rm [C\,\emissiontype{II}] }$ ($M_\odot$ yr$^{-1}$) / 18 $\pm$ 4                                  / 16 $\pm$ 5                                  / 63 $\pm$ 8 |
| M_dyn | 1.3 / 2.0 / 29 (1e10) | not stated | M_sun | 5 | / J2239+0207 / 6.4 $\pm$ 1.3 / 29 / 11$^{+3}_{-2}$ / |
| L_CII/L_FIR vs L_FIR slope | -0.50 | 0.05 | dimensionless | 6 | (3.05 \pm 0.67) + (-0.50 \pm 0.05) |
| L_FIR vs L_Bol slope | 0.69 | 0.11 | dimensionless | 6 | (2.94 \pm 1.47) + (0.69 \pm 0.11) \log |

## Qualitative findings

- One continuum emitter found 13.7 arcsec from J2228+0152; no excess of submm sources around HSC quasars  
  > "our results will not support that these HSC quasars reside in overdense regions of submm sources." (3.4 Continuum emitters)

## Claim tuples

- H: Low-luminosity quasars have lower [CII] luminosity than luminous quasars | E: ALMA [CII] in three HSC quasars | R: L_CII (2.4-9.5)e8 Lsun, ~10x smaller | F: Host [CII] luminosities scale with quasar luminosity | **supported**
- H: Low-luminosity quasars lie on the local M_BH-M_bulge relation | E: M_dyn from [CII] vs M_BH, with literature | R: Many on or below local relation at M_dyn>~4e10 | F: Luminous quasar overmassive BHs reflect bias | **partially**
- H: Quasars grow BHs faster than parallel growth | E: L_Bol-L_FIR plane | R: Nearly all on or below parallel growth line | F: Earlier starburst phase needed | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): M_dyn lacks formal errors; rotation vs dispersion dominance unknown; Td assumed  
  > "Formal errors on $M_{\rm dyn}$ are not given due to multiple unconstrained uncertainties" (4.2.1)
- Caveat (inferred, ours): M_dyn from barely resolved data with thin-disk assumption
- Caveat (inferred, ours): L_FIR depends on assumed Td=47 K
- Caveat (inferred, ours): Small sample; Eddington assumption for unmeasured M_BH
- Caveat (inferred, ours): Companion emitter candidates are marginal

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: ALMA project 2017.1.00541.S cited  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA 2017.1.00541.S." (Acknowledgments)
- Missing: Line-free channels, cell/image sizes, masks
- Missing: Literature compilation values for regression
- Missing: Coordinates in table
- Data volume (inferred): ~tens of GB (three Band 6 12-m datasets)
- Score (inferred): 3/5, Data and main steps stated; imaging details and literature compilation partly missing.
- Rediscovery candidate: yes, Data from a single ALMA project, simple recipe, numeric results in tables.

## Links

- Method: (cite: Onoue19) (M_BH measurements)
- Method: (cite: 2011MNRAS.416.2712D) (SFR-L_CII relation)
- Companion: (cite: 2018PASJ...70...36I) (Cycle 4 HSC quasars ALMA)
- Related: SHELLQs
- Related: Subaru HSC-SSP
- Related: CFHQS

## Checks

```json
{
 "quotes": 67,
 "quotes_ok": 67,
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
  "facts": 84,
  "stated": 52,
  "rate": 0.619
 },
 "evidence_ok": true
}
```
