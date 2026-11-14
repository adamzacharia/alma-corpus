# The hidden heart of the luminous infrared galaxy IC 860. I. A molecular inflow feeding opaque, extreme nuclear activity

`2019A&A...627A.147A` | Astronomy and Astrophysics 2019 | first author: Aalto, S. | arXiv: 1905.07275 | DOI: 10.1051/0004-6361/201935480

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, agn_and_quasars, astrochemistry
- Question: What is the structure, dynamics and power source of the compact obscured nucleus of the LIRG IC 860, and is gas flowing in or out?  
  > "is an ideal object with which to study the distribution and dynamics of the HCN-VIB emission and the structure of the nuclear continuum." (1 Introduction)
- Target **IC 860**: coordinates 13:15:03.5088 +24:37:07.788 (J2000, phase centre)  
  > "The LIRG IC 860 ($D$=59 Mpc, log $L_{\rm IR}$=11.17 L$_{\odot}$, 1$''$=286 pc; (cite: sanders03))" (1 Introduction); "the phase centre was set to $\alpha$=13:15:03.5088 and $\delta$=$+$24:37:07.788 (J2000)" (2.1 ALMA observations); z/distance D=59 Mpc; z=0.01294  
  > "The LIRG IC 860 ($D$=59 Mpc, log $L_{\rm IR}$=11.17 L$_{\odot}$, 1$''$=286 pc; (cite: sanders03))" (1 Introduction); "the phase centre was set to $\alpha$=13:15:03.5088 and $\delta$=$+$24:37:07.788 (J2000)" (2.1 ALMA observations); distance from (cite: sanders03)  
  > "The LIRG IC 860 ($D$=59 Mpc, log $L_{\rm IR}$=11.17 L$_{\odot}$, 1$''$=286 pc; (cite: sanders03))" (1 Introduction); "the phase centre was set to $\alpha$=13:15:03.5088 and $\delta$=$+$24:37:07.788 (J2000)" (2.1 ALMA observations)

## Data provenance

- ALMA projects: 2016.1.00800.S, 2015.1.00823.S
- bands: ALMA Band 3, 6, 7 plus VLA Q-band  
  > "ALMA) band 3, 6, and 7 observations of the 3 to 0.8 mm continuum" (1 Introduction)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: B3 41 m-12.1 km; B6 113 m-13.9 km; B7 16 m-12.5/6.1 km  
  > "B6 $^{a1}$ | 2017 Nov 12 | 45 | $\sim 1$ | 30 | 113 / 13.9" (Table 1)
- angular resolution: B7 0.036x0.026 arcsec; B6 0.05x0.02; B3 0.1x0.07 (robust 0.5)  
  > "The synthesized beam is $0.\mbox{$''$}036 \times 0.\mbox{$''$}026$ with Briggs weighting (robust parameter set to 0.5)." (ALMA band 7)
- max recoverable scale: B7 0.25", B6 0.29", B3 0.66"  
  > "Largest recoverable scale: B7 0.$''$25, B6 0.$''$29, B3 0.$''$66." (Table 1)
- sensitivity: B7 1.4 mJy/beam, B6 0.35, B3 0.15 per 20 km/s channel  
  > "The resulting data have a sensitivity of 0.35 mJy per beam in a 20 ${\rm km\,s}^{-1}$ (18 MHz) channel width." (ALMA band 6)
- time on source: B3 40 min, B6 30 min, B7 25+40 min (table)  
  > "B3 $^{a1}$ | 2017 Sep 19 | 44 | $\sim 1$ | 40 | 41 / 12.1" (Table 1)
- observing dates: B7 2015 Nov 24 and Dec 5; B6 2017 Nov 12; B3 2017 Sep 19  
  > "B6 $^{a1}$ | 2017 Nov 12 | 45" (Table 1)
- pi or archival as stated: _not stated_
- Line: HCN J=3-2 and 4-3 v=0 and v2=1f (not stated)
- Line: HCO+ J=3-2, 4-3 (not stated)
- Other facility **VLA**: Q-band 45 GHz continuum, A configuration, 70 min on source  
  > "for a total of 70 minutes on-source with the VLA in its A configuration" (2.2 Observations with the VLA)
- External data: Systemic velocity cz=3880 km/s  
  > "we adopt $cz$=3880 $\pm$ 20 ${\rm km\,s}^{-1}$ ($z$=0.01294) for systemic velocity ($v_{\rm sys}$) from (cite: aalto15b)" (3.2 Spectral lines) [from (cite: aalto15b)]
- External data: 14 micron MIR flux 90 mJy  
  > "Our model over-predicts the observed 14 $\mu$ MIR flux (cite: lahuis07) (90 mJy)" (4.1.2 Dust temperature and opacities) [from (cite: lahuis07)]

## Processing

### Calibration

- pipeline or manual: calibrated in CASA, imported to AIPS for imaging  
  > "All data were calibrated within the CASA reduction package. The visibility set was then imported into the AIPS package for further imaging." (2.1 ALMA observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: 5-10% B3, 20% B6, 50-70% B7  
  > "Flux calibration errors are 5-10% for band 3, and 20% for band 6." (2.1 ALMA observations)
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: Briggs robust 0.5 (natural also used for B7)  
  > "with Briggs weighting (parameter robust set to 0.5)" (ALMA band 3)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: continuum from zeroth-order fit to line-free channels (image plane for ALMA, uv for Q-band)  
  > "Continuum levels were determined through a zeroth-order fit to line-free channels in the uv-plane for Q-band, and in the image plane for the ALMA continuum." (Table 2)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Systemic velocity adopted  
  > "for systemic velocity ($v_{\rm sys}$) from (cite: aalto15b)" (3.2 Spectral lines) [from (cite: aalto15b)]
- Opacity-column density relation  
  > "According to the formalism of (cite: keene82) and (cite: hildebrand83)" (4.1.2) [from (cite: keene82); (cite: hildebrand83)]

### Not stated but needed to reproduce (our reading)

- tclean/AIPS imaging parameters (cell, image size, masks, deconvolver)
- line-free channels used for continuum
- software versions (CASA, AIPS)
- modified blackbody fit details and mass absorption coefficients (only referenced)
- uv-taper and primary beam correction

## Analysis recipe

1. **make continuum images and fit sizes**: merge line-free channels; 2D Gaussian fits for size, flux, Tb  
  > "We merged line-free channels to produce continuum images from 45 up to 360 GHz." (3.1 Continuum)
   - software: CASA, AIPS
   - fitting: _not stated_
   - validation: astrometry checked with checksource  
  > "We use the procedure *checksource* to determine the accuracy of the astrometry." (2.1)
2. **moment maps of lines**: moments 0,1,2 with 3 sigma per-channel clipping  
  > "For all lines we (conservatively) clipped fluxes below the 3$\sigma$ level (per channel) before integration." (3.2)
   - parameter: velocity range 3650-4100 km/s  
  > "All moment maps cover the same velocity range: 3650 to 4100 ${\rm km\,s}^{-1}$." (3.2.2 Ground-state lines)
   - fitting: _not stated_
   - validation: _not stated_
3. **dust temperature, opacity and column density**: modified black body SED fit with opacity-dependent temperature  
  > "We used a modified black body to produce the SED. We calculate an optical depth at each wavelength and then we determine the dust temperature" (Footnote 4)
   - assumption: dust-to-gas ratio 1/100, smooth single-temperature structure  
  > "We assume a standard dust-to-gas ratio of 1/100, and adopt a simple, smooth (non-clumpy) single-temperature geometry." (5 Conclusions)
   - fitting: _not stated_
   - validation: model compared with 14 micron flux (overpredicts by 100-200)  
  > "Our model over-predicts the observed 14 $\mu$ MIR flux (cite: lahuis07) (90 mJy) by a factor of $\sim$100-200" (4.1.2)
4. **dynamical mass**: Mdyn=2.3e8 (v/100)^2 (r/100) Msun with inclination correction  
  > "A simple estimate of the dynamical mass is $M_{\rm dyn}=2.3 \times 10^8 \times (v_{\rm rot}/100)^2 \times (r/100)$ M$_{\odot}$." (Footnote 5)
   - assumption: i=30 deg (face-on) or >60 deg  
  > "If we assume that the structure is a near face-on disk with $i$=30$^{\circ}$, and a projected rotational velocity of 100 ${\rm km\,s}^{-1}$" (4.2.1)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : calibration of ALMA data  
  > "All data were calibrated within the CASA reduction package." (2.1)
- **AIPS** : imaging  
  > "The visibility set was then imported into the AIPS package for further imaging." (2.1)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Band 6 peak continuum (265 GHz) | 13.4 | 0.2 | mJy/beam | 1 | / 265$^b$ / $13.4 \pm 0.2$ / $49 \pm 5$ |
| Dust temperature | 280 | not stated | K | 3 | we fit a $T_{\rm d} \simeq$280 K and $\tau$ of $\sim$5 (at 1 mm) |
| N(H+H2) | 5e26 | not stated | cm^-2 | 3 | an extreme column density of $N$(H + H$_2)\simeq5 \times 10^{26}$ $\rm {cm^{-2}}$ |
| Dynamical mass r=10 pc, i=30 | 9e7 | not stated | Msun | 4 | $M_{\rm dyn}=9 \times 10^7$ M$_{\odot}$ |
| Inflow velocity upper limit | 50 | not stated | km/s | 0 | we adopt +50 ${\rm km\,s}^{-1}$ as an upper limit to the inflow velocity |

## Qualitative findings

- Continuum is opaque hot dust; HCN-VIB emission ring-like and suppressed at centre  
  > "The line-to-continuum ratio drops towards the inner $r$=4 pc, resulting in a ring-like morphology." (5 Conclusions)

## Claim tuples

- H: mm continuum is from opaque hot dust | E: Compare Q, B3, B6 continuum; SED fit | R: Td~280 K, tau~5, N~5e26 | F: nucleus extremely opaque | **supported**
- H: Gas is flowing into the nucleus | E: Ground-state line absorption profiles | R: Redshifted reversed P-Cygni profiles | F: inflow v<~50 km/s | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Elevated dust-to-gas ratio or mm-sized grains considered but no direct evidence  
  > "There is however currently no direct evidence to support this, and we will therefore continue to adopt a standard dust-to-gas ratio of 1/100." (4.1.3)
- How they decided it was enough: _not stated_
- Limitation (authors): Band 7 flux uncertain by factor of two due to calibrator issues  
  > "For band 7 we estimate a flux accuracy of 50 to 70% due to issues with the flux calibrator." (2.1)
- Caveat (inferred, ours): Single-temperature smooth dust model is crude
- Caveat (inferred, ours): Power source (AGN vs starburst) not decided
- Caveat (inferred, ours): Band 7 flux unreliable

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Imaging parameters
- Missing: SED fit code and opacities
- Missing: line-free channel selection
- Data volume (inferred): ~100-300 GB raw
- Score (inferred): 4/5, Data public and described but imaging and modelling details sparse.
- Rediscovery candidate: no, Imaging and SED modelling recipes incomplete.

## Links

- Companion: (cite: aalto15b) (earlier HCN-VIB detection in IC 860)

## Checks

```json
{
 "quotes": 49,
 "quotes_ok": 49,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 68,
  "stated": 34,
  "rate": 0.5
 },
 "evidence_ok": true
}
```
