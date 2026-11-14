# ALMA and HST Kiloparsec-scale Imaging of a Quasar-galaxy Merger at Z ≈ 6.2

`2019ApJ...880..157D` | The Astrophysical Journal 2019 | first author: Decarli, Roberto | arXiv: 1906.05308 | DOI: 10.3847/1538-4357/ab297f

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: agn_and_quasars, high_z_galaxies
- Question: What are the morphology, kinematics and ISM/star-formation properties of the z=6.23 quasar PJ308-21 and its extended companion components, and are they a merger or an outflow?  
  > "An outflow interpretation of the unique features in PJ308–21 is not supported by the data." (abstract)
- Target **PJ308-21 (PSO J308.0416-21.2339)**: coordinates PSO J308.0416-21.2339  
  > "the quasar+companion system PSO J308.0416–21.2339 ((cite: banados16); hereafter PJ308–21) at $z$=$6.2342$" (1 Introduction); z/distance z=6.2342  
  > "the quasar+companion system PSO J308.0416–21.2339 ((cite: banados16); hereafter PJ308–21) at $z$=$6.2342$" (1 Introduction); distance from _not stated_

## Data provenance

- ALMA projects: 2015.1.01115.S, 2016.A.00018.S
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: C40-5 for high-resolution data  
  > "while the array was in C40-5 configuration" (2.1 ALMA)
- baselines: longest ~1.1 km  
  > "even at the longest baselines ($\approx 1.1$ km)" (2.1 ALMA)
- angular resolution: ~0.3'' (synthesized beam 0.38''x0.30'', PA 82 deg)  
  > "The synthesized beam size is $0.38''\times 0.30''$ (at Position Angle=$82^\circ$)." (2.1 ALMA)
- max recoverable scale: _not stated_
- sensitivity: 0.20 mJy/beam per 30 km/s channel; continuum rms 10.6 uJy/beam  
  > "The typical rms of the noise is 0.20 mJy beam$^{-1}$ per 30 km s$^{-1}$ channel." (2.1 ALMA)
- time on source: ~1 hr (high-res)  
  > "The high–resolution observations include $\sim1$ hr of on-source data." (2.1 ALMA)
- observing dates: May 3 and 5, 2017 (high-res)  
  > "These high–resolution observations were collected in two executions on May 3 and 5, 2017" (2.1 ALMA)
- pi or archival as stated: low-res from survey program 2015.1.01115.S; new DDT high-res 2016.A.00018.S  
  > "we present new follow–up observations at high resolution ($\sim 0.3''$) obtained in a Director’s Discretional Time allocation" (2.1 ALMA)
- Line: [C II] 158 um (1900.547 GHz)
- Other facility **HST WFC3-IR F140W**: Rest-frame UV imaging (program 14876), 2611.75 s  
  > "The total integration was 2611.75 s, split into 4 frames" (2.2 HST)
- Other facility **Pan-STARRS**: i and z photometry of a foreground source  
  > "visible also in the Pan–STARRS $i$ and $z$ bands" (3.1 Morphology of the system)
- External data: Original low-resolution [C II]/continuum data and companion identification  
  > "the original low–resolution ($\sim1''$) data from the survey of \[C ii\] and underlying dust continuum" (2.1 ALMA) [from (cite: decarli18); (cite: venemans18)]
- External data: [CII]-to-H2 conversion alpha_[CII]=30 Msun/Lsun  
  > "empirically–calibrated \[C ii\]–to–H$_2$ mass ratio $\alpha_{\rm [CII]}=30$ M$_\odot$/L$_\odot$" (3.2 Gas and dust masses) [from (cite: zanella18)]
- External data: Dust emissivity beta=1.6  
  > "fixed dust emissivity $\beta=1.6$ (cite: beelen06)" (3.2 Gas and dust masses) [from (cite: beelen06)]

## Processing

### Calibration

- pipeline or manual: ALMA pipeline in CASA  
  > "We ran the ALMA pipeline in Common Astronomy Software Applications, CASA (cite: mcmullin07) for data calibration." (2.1 ALMA)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J2056-4714  
  > "The quasars J1924-2914, J2056-4714, J2042-2255 served as bandpass, flux, and phase calibrator, respectively." (2.1 ALMA)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: tclean  
  > "inverted the visibilities using the task tclean" (2.1 ALMA)
- deconvolver: _not stated_
- weighting robust: Briggs robust=2 (natural)  
  > "Briggs weighting with robustness parameter set to 2 (i.e., ‘natural’ visibility weighting)" (2.1 ALMA)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: S/N>1.5 mask for moment maps  
  > "after applying a S/N$>$1.5 mask" (2.1 ALMA)
- multiscale scales: _not stated_
- continuum subtraction: uvsub using line-free continuum image  
  > "we also create a line–free continuum image, which is then used to perform continuum–subtraction via the task uvsub" (2.1 ALMA)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: low- and high-resolution datasets concatenated  
  > "We concatenated the low– and high–resolution datasets" (2.1 ALMA)
- smoothing: _not stated_
- final beam: 0.38''x0.30'', PA 82 deg  
  > "The synthesized beam size is $0.38''\times 0.30''$ (at Position Angle=$82^\circ$)." (2.1 ALMA)
- final rms: 0.20 mJy/beam per 30 km/s channel; continuum 10.6 uJy/beam  
  > "reaches a rms of $10.6$ $\mu$Jy beam$^{-1}$" (2.1 ALMA)

### Inherited from earlier work

- Continuum image creation and continuum subtraction approach  
  > "Following (cite: decarli18), we also create a line–free continuum image" (2.1 ALMA) [from (cite: decarli18)]
- Gas mass from [CII] emissivity  
  > "following (cite: venemans17)" (3.2 Gas and dust masses) [from (cite: venemans17)]
- SFR calibrations from UV and IR luminosities  
  > "Following (cite: kennicutt12), these luminosities translate into UV–based SFRs" (3.3 Star formation rate surface density) [from (cite: kennicutt12)]

### Not stated but needed to reproduce (our reading)

- Cell size and image size of the cube
- Line-free channel ranges for continuum
- Aperture definitions for Q, E, W flux extraction
- CASA version
- Cleaning threshold/masking in tclean
- Whether archive products or own calibration were used
- HST aperture shapes and UV luminosity-to-SFR details
- Toy tidal model code and parameter grid; the Q circular velocity and host mass values

## Analysis recipe

1. **Image [CII] cube and continuum**: tclean natural-weighted cube in 30 km/s channels; line-free continuum; uvsub subtraction; moment 0/1 maps, PV diagrams, 3D renderings  
  > "The continuum–subtracted \[C ii\] cube is then collapsed along the frequency axis, after applying a S/N$>$1.5 mask, in order to create moment 0 and 1 maps." (2.1 ALMA)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **PSF-subtract HST image**: Empirical PSF from median of 8 stars, fitted to the quasar with GALFIT, centroid free <1 pixel  
  > "We create a model of the Point Spread Function (PSF) by median–averaging the normalized images of 8 stars in the field" (2.2 HST)
   - software: GALFIT, IRAF
   - fitting: PSF scaled with centroid allowed to move <1 pixel  
  > "allowing the PSF centroid to move by $<1$ pixel" (2.2 HST)
   - validation: Diffraction spikes well subtracted  
  > "our empirical PSF model appears to work well in subtracting the color-sensitive diffraction spikes" (2.2 HST)
3. **Derive gas and dust masses, IR luminosities**: [CII] optically thin LTE C+ mass, converted with solar C/H; alternative alpha_[CII]=30; modified blackbody for IR and dust mass  
  > "we infer $M_{\rm C+}$ = $(13.9,\,5.1,\,2.7)\times10^6$ M$_\odot$ for Q, E, and W, respectively." (3.2 Gas and dust masses)
   - parameter: Tex=100 K; Tdust=35-45 K; beta=1.6  
  > "where the range refers to dust temperatures spanning between 35 and 45 K" (3.2 Gas and dust masses)
   - assumption: Optically thin [CII], LTE, C/H=2.95e-4, gas-to-dust 100 for comparison, Tdust=35 K adopted  
  > "in the following we assume $T_{\rm dust}$=35 K everywhere in the system" (3.2 Gas and dust masses)
   - fitting: _not stated_
   - validation: Compared the [CII]-based and gas-to-dust gas masses  
  > "a typical gas–to–dust ratio of 100 (cite: berta16) would yield a significantly lower gas mass" (3.2 Gas and dust masses)
4. **Derive SFRs and surface densities**: UV SFR from F140W luminosity and IR SFR from L_IR following Kennicutt & Evans; Sigma_SFR over apertures  
  > "The obscured SFRs are derived from IR luminosities following (cite: kennicutt12): 290, 60, and 32 M$_\odot$ yr$^{-1}$ for Q, E, and W" (3.3 Star formation rate surface density)
   - assumption: Reflected quasar light ignored  
  > "We will ignore the impact of reflected light in the remainder of our analysis." (Footnote 3)
   - fitting: _not stated_
   - validation: Compared to Eddington limit and main-sequence galaxies  
  > "are in line with the values typically observed in global observations of main sequence galaxies at $z$=1–3" (3.3 Star formation rate surface density)
5. **Toy tidal-disruption model**: Parabolic orbit at pericenter, escape velocity from baryonic + NFW potential (c=10); stretch DeltaR = Delta v x Delta t; not a fit  
  > "This simplistic approach is not a fit to the data, but rather a proof of concept that the tidal disruption scenario works for this system." (3.4 Dynamics of the system)
   - parameter: Example: R_peri=10 kpc, R_sat=5 kpc, R_h=3 kpc, alpha=2, M_host=1e11 Msun  
  > "$R_{\rm per}$=10 kpc, an initial satellite radius $R_{\rm sat}$=5 kpc, a scale radius of the quasar host of $R_{\rm h}$=3 kpc, $\alpha$=2, and a host mass of $10^{11}$ M$_\odot$" (3.4 Dynamics of the system)
   - assumption: DM/baryon ratio between 3 and 30; concentration c=10  
  > "We only consider cases that yield a total DM–to–baryon mass ratio of the quasar host $3<M_{\rm host,DM}/M_{\rm host,bar}<30$." (3.4 Dynamics of the system)
   - fitting: _not stated_
   - validation: Compared predicted velocity and extent with observations  
  > "we test whether the proposed dynamical description of PJ308–21 succeeds in predicting the observed range of line–of–sight gas velocity, and the spatial extent" (3.4 Dynamics of the system)

## Software

- **CASA** : Pipeline calibration, tclean imaging, uvsub  
  > "We ran the ALMA pipeline in Common Astronomy Software Applications, CASA (cite: mcmullin07) for data calibration." (2.1 ALMA)
- **AstroDrizzle** 2.1.3.dev: HST data reduction  
  > "the AstroDrizzle package (version 2.1.3.dev)" (2.2 HST)
- **GALFIT** : Quasar PSF subtraction in HST image  
  > "We do so using GALFIT (cite: peng06)" (2.2 HST)
- **IRAF** : Custom tasks for PSF handling  
  > "combined with a suite of custom IRAF[^1]–based tasks" (2.2 HST)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| [CII] flux Q/E/W | 4.7 / 1.7 / 0.9 | ~10% | Jy km/s | 1 | $F_{\rm [CII]}$ \[Jy km s$^{-1}$\] / $4.7$ / $1.7$ / $0.9$ |
| 1.1 mm continuum flux Q/E/W | 1.01 / 0.19 / 0.13 | not stated | mJy | 3 | $F_{\rm 1.1mm}$=1.01, 0.19, and 0.13 mJy for Q, E, and W respectively |
| F140W magnitude Q/E/W | 25.33 / 25.17 / 24.44 | not stated | AB mag | 2 | F140W \[mag\] / $25.33$ / $25.17$ / $24.44$ |
| gas mass from [CII] (alpha=30) Q/E/W | 13.9 / 5.1 / 2.7 e10 | not stated | Msun | 3 | $M_{\rm gas}=(13.9, 5.1, 2.7)\times 10^{10}$ M$_\odot$ |
| UV SFR Q/E/W | 11 / 13 / 25 | not stated | Msun/yr | 4 | UV–based SFRs of 11, 13, and 25 M$_\odot$ yr$^{-1}$ |
| IR SFR Q/E/W (Tdust=35 K) | 290 / 60 / 32 | not stated | Msun/yr | 4 | 290, 60, and 32 M$_\odot$ yr$^{-1}$ for Q, E, and W |
| max Sigma_SFR (IR, at quasar) | 14 | not stated | Msun/yr/kpc^2 | 4 | We find the highest value of $\Sigma_{\rm SFR}$=14 M$_\odot$ yr$^{-1}$ kpc$^{-2}$ |
| toy model outputs | Delta v ~240 km/s, Delta t ~45 Myr, Delta R ~11 kpc | not stated | mixed | 5 | we obtain $\Delta v\approx 240$ km s$^{-1}$, $\Delta t\approx 45$ Myr, and a major semi-axis of the satellite of $\Delta R\approx 11$ kpc |

## Qualitative findings

- E and W [CII], dust and rest-UV emission are spatially aligned, associating the UV with young stars at the quasar redshift.  
  > "the \[C ii\] emission in both E and W is spatially aligned with and shows a similar morphology to the diffuse emission detected with *HST*" (3.1 Morphology of the system)

## Claim tuples

- H: Are E and W components physically associated with the quasar rather than foreground objects? | E: Compared ALMA [CII]/dust maps with PSF-subtracted HST image | R: Morphological match of UV, dust and [CII] | F: Extended emission is associated with the quasar environment | **supported**
- H: Is the system an outflow? | E: Examined velocity structure and dispersion | R: Opposite velocity signs/gradients and low dispersion in E | F: Outflow not supported | **supported**
- H: Can tidal disruption of one satellite explain the kinematics? | E: Toy escape-velocity model | R: Reproduces velocity range and ~11 kpc extent for reasonable parameters | F: Merger scenario consistent | **partially**
- H: Are ISM properties typical of high-z star-forming galaxies? | E: [CII]/IR, IRX, Sigma_SFR vs Sigma_gas | R: In line with main-sequence galaxies | F: Typical star-forming properties | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Outflow interpretation rejected  
  > "An outflow interpretation of the unique features in PJ308–21 is not supported by the data." (abstract)
- Alternative: Dust-scattered quasar light could contribute to UV; cannot be distinguished  
  > "At present, we cannot unambiguously distinguish between the two scenarios" (Footnote 3)
- How they decided it was enough: _not stated_
- Limitation (authors): Gas masses are lower limits/order-of-magnitude; PSF color systematics; Q UV is a lower limit  
  > "These are lower limits in that the estimated gas mass would increase" (3.2 Gas and dust masses)
- Caveat (inferred, ours): Dust temperature assumed, not measured
- Caveat (inferred, ours): Single alpha_[CII] applied across components
- Caveat (inferred, ours): Toy model is not fitted and has degenerate parameters
- Caveat (inferred, ours): Aperture-dependent fluxes with ~10% errors
- Caveat (inferred, ours): No CO or stellar mass constraint

## Reproducibility

- Data public (paper): ALMA and HST program IDs given; HST obtained from the STScI archive  
  > "obtained from the Data Archive at the Space Telescope Science Institute" (Acknowledgments)
- Products in archive: _not stated_
- Missing: Aperture definitions
- Missing: Cell/image size, cleaning parameters
- Missing: Toy model code and Q velocity inputs
- Data volume (inferred): ~10-50 GB for two ALMA datasets plus small HST images
- Score (inferred): 5/5, Public data and main steps described but imaging details, apertures and model inputs are missing.
- Rediscovery candidate: no, Key aperture and imaging settings are missing; the dynamical model is not fully specified.

## Links

- Method: (cite: decarli18) (Continuum imaging and survey data processing)
- Method: (cite: venemans17) ([CII] gas mass method)
- Companion: (cite: decarli17) (Original discovery of the [CII] companion)
- Companion: (cite: venemans18) (Low-resolution survey data)
- Related: ALMA survey of [CII] in z>5.94 quasars

## Checks

```json
{
 "quotes": 67,
 "quotes_ok": 67,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 79,
  "stated": 51,
  "rate": 0.646
 },
 "evidence_ok": true
}
```
