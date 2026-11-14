# Nuclear molecular outflow in the Seyfert galaxy NGC 3227

`2019A&A...628A..65A` | Astronomy and Astrophysics 2019 | first author: Alonso-Herrero, A. | arXiv: 1906.06889 | DOI: 10.1051/0004-6361/201935431

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, agn_and_quasars
- Question: What are the morphology and kinematics of the cold molecular gas and (sub)mm continuum in the nuclear region of NGC 3227, and is there a compact torus or a nuclear outflow?  
  > "In this paper we present a detailed study of the cold molecular gas emission of the nearby Seyfert 1.5 galaxy NGC 3227." (Introduction)
- Target **NGC 3227**: coordinates RA 10h23m30.574s, Dec +19d51m54.278s (ICRS, unresolved 1.3 mm component)  
  > "We use a distance of $14.5\pm0.6$ Mpc as derived from AGN lags (cite: Yoshii2014) and thus 1$''$$\sim$73 pc." (Introduction); "RA(ICRS)=10$^{\rm h}$23$^{\rm m}$30.574$^{\rm s}$ and Dec(ICRS)=+19$\ensuremath{^\circ}$51$'$54.278$''$" (3.1 Morphology); z/distance 14.5±0.6 Mpc (1'' ~ 73 pc)  
  > "We use a distance of $14.5\pm0.6$ Mpc as derived from AGN lags (cite: Yoshii2014) and thus 1$''$$\sim$73 pc." (Introduction); "RA(ICRS)=10$^{\rm h}$23$^{\rm m}$30.574$^{\rm s}$ and Dec(ICRS)=+19$\ensuremath{^\circ}$51$'$54.278$''$" (3.1 Morphology); distance from AGN lags (Yoshii2014)  
  > "We use a distance of $14.5\pm0.6$ Mpc as derived from AGN lags (cite: Yoshii2014) and thus 1$''$$\sim$73 pc." (Introduction); "RA(ICRS)=10$^{\rm h}$23$^{\rm m}$30.574$^{\rm s}$ and Dec(ICRS)=+19$\ensuremath{^\circ}$51$'$54.278$''$" (3.1 Morphology)

## Data provenance

- ALMA projects: 2016.1.00254.S, 2016.1.01236.S
- bands: Band 6 (1.3 mm) and Band 7 (850 um)  
  > "We also used Band 7 ALMA data of NGC 3227 observed between August and September 2017" (2.1 ALMA Band 6 and Band 7 observations)
- frequencies and spectral setup: Band 6: two 1.875 GHz windows, 3.9 MHz (~5 km/s) channels, CO(2-1) at 229.8 GHz and continuum ~231 GHz; Band 7: CO(3-2) window at 344.4 GHz plus continuum windows at 342.6, 354.6, 356.5 GHz  
  > "We defined two spectral windows of 1.875 GHz bandwidth (with 3.9 MHz $\sim$ 5 km s$^{-1}$ channels), at the observed frequency of the CO(2-1) transition (229.8 GHz)" (2.1 ALMA Band 6 and Band 7 observations)
- continuum bandwidth: _not stated_
- arrays: Band 6: 12 m (compact and extended) plus ACA; Band 7: 12 m single configuration  
  > "using the 12 m array in two configurations (compact with baselines between 15 and 460 m and extended with baselines between 20 and 3700 m) and the Atacama Compact Array (ACA)" (2.1 ALMA Band 6 and Band 7 observations)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.085-0.21'' (7-15 pc)  
  > "our ALMA observations have angular resolutions between 0.085 and 0.21$''$." (2.1 ALMA Band 6 and Band 7 observations)
- max recoverable scale: _not stated_
- sensitivity: Continuum rms 3.9e-2 (b=0.5), 7.7e-2 (b=-0.5) mJy/beam Band 6; 2.0e-2 mJy/beam Band 7  
  > "| Band 7 | natural | $0.094\times0.085$ | 16.6 | $2.0\times 10^{-2}$ |" (Table 1)
- time on source: _not stated_
- observing dates: Band 6 March-September 2017; Band 7 August-September 2017  
  > "between March and September 2017" (2.1 ALMA Band 6 and Band 7 observations)
- pi or archival as stated: _not stated_
- Line: CO J=2-1 (not stated)
- Line: CO J=3-2 (not stated)
- Other facility **HST/ACS (Hubble Legacy Archive)**: F658N and F814W images used to build a pseudo Halpha+[NII] map  
  > "we constructed a pseudo H$\alpha$+\[N ii\] line map by dividing the F658N image by that of the nearby broad-band continuum traced by the F814W image" (2.2 Ancillary archival HST images)
- External data: MERLIN 18 cm and 6 cm nuclear flux densities used in the SED  
  > "we used the small aperture ($\sim 0.1-0.2\ensuremath{''}$) MERLIN 18 cm and 6 cm data points of the southern source of (cite: Mundell1995)" (3.3 Nuclear radio to sub-millimeter SED) [from (cite: Mundell1995)]
- External data: Clumpy torus model fit to nuclear IR emission  
  > "using the (cite: Nenkova2008a; Nenkova2008b) clumpy torus models derived by (cite: GarciaBernete2019)" (3.3 Nuclear radio to sub-millimeter SED) [from (cite: GarciaBernete2019)]
- External data: Bar hydrodynamical simulation model 0S20r  
  > "we used the same (cite: Maciejewski2004) bar simulation (model termed 0S20r) used by (cite: Davies2014)" (5.1 Streaming motions) [from (cite: Maciejewski2004)]

## Processing

### Calibration

- pipeline or manual: Calibrated and imaged with CASA; whether pipeline or manual not stated  
  > "We calibrated and imaged the data using the ALMA reduction software CASA (cite: McMullin2007)." (2.1 ALMA Band 6 and Band 7 observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: 12 m: J0854+2006 or J1058+0133 (bandpass and amplitude); ACA: Ganymede (Butler-JPL-Horizons 2012 model)  
  > "The Ganymede flux was estimated using the Butler-JPL-Horizons 2012 model." (2.1 ALMA Band 6 and Band 7 observations)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA clean  
  > "Then, we combined and cleaned the data using the CASA clean task." (2.1 ALMA Band 6 and Band 7 observations)
- deconvolver: _not stated_
- weighting robust: Band 6 continuum Briggs b=0.5 and -0.5; Band 7 natural; CO(2-1) b=0.5, CO(3-2) natural  
  > "with robustness parameters of $b=0.5$ and $b=-0.5$" (2.1 ALMA Band 6 and Band 7 observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: Constant fit to line-free channels in the uv plane  
  > "by fitting the continuum emission with a constant in the line-free channels" (2.1 ALMA Band 6 and Band 7 observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: 850 um map convolved to the 1.3 mm b=0.5 beam for the spectral index map  
  > "We used GILDAS to convolve the $850\,\mu$m continuum map to the beam size and orientation of the 1.3 mm continuum map" (3.2 Spectral index)
- final beam: CO(2-1) 0.214x0.161'' PA 42.0; CO(3-2) 0.095x0.085'' PA 21.3  
  > "| Band 7 | CO(3–2) | natural | $0.095\times0.085$ | 21.3 |" (Table 2)
- final rms: _not stated_

### Inherited from earlier work

- Parent sample and series approach  
  > "This is the second paper of a series (cite: AlonsoHerrero2018) based on several ALMA programs" (Introduction) [from (cite: AlonsoHerrero2018)]
- Molecular gas mass relation and CO-to-H2 factor  
  > "use the relation of (cite: Sakamoto1999) with a Galactic CO-to-H$_2$ conversion factor $X=2 \times 10^{20}\,{\rm cm}^{-2}$" (6 Nuclear molecular gas mass and column density) [from (cite: Sakamoto1999)]
- Outflow rate expression  
  > "taking expression given in equation 4 of (cite: GarciaBurillo2014)" (7 Discussion and Conclusions) [from (cite: GarciaBurillo2014)]

### Not stated but needed to reproduce (our reading)

- Number of clean iterations, thresholds and masks
- Line-free channel ranges
- Image and cell sizes
- Whether pipeline or manual calibration and CASA version
- uv-plane fitting software for the point plus Gaussian model
- 3DBarolo ring setup, mask and fit options
- How the aperture fluxes and moment-map thresholds were applied exactly

## Analysis recipe

1. **Image continuum and cubes**: Continuum subtraction in uv plane then CASA clean with Briggs/natural weighting  
  > "Then, we combined and cleaned the data using the CASA clean task." (2.1 ALMA Band 6 and Band 7 observations)
   - software: CASA
   - fitting: _not stated_
   - validation: Flux calibration consistency checked via amplitude vs uv distance in overlapping baselines  
  > "Since the amplitudes of the overlapping baselines are similar we can conclude that the flux calibration is consistent." (2.1 ALMA Band 6 and Band 7 observations)
2. **Fit 1.3 mm continuum in uv plane**: Point source plus Gaussian, positions free, Gaussian FWHM fixed to 0.35''  
  > "We left the positions of the two sources free and we only fixed the width of the extended component to FWHM=$0.35\ensuremath{''}$" (3.1 Morphology)
   - fitting: _not stated_
   - validation: _not stated_
3. **Spectral index map and SED**: 850 um convolved to 1.3 mm beam; pixels detected at >=2.5 sigma in both bands; aperture fluxes in 0.2'' and 0.5'' squares  
  > "we only used pixels where both continua were detected at a $2.5\sigma$ level or higher" (3.2 Spectral index)
   - software: GILDAS
   - fitting: _not stated_
   - validation: _not stated_
4. **Moment maps of CO**: GILDAS moment task with 3 sigma and 5 sigma thresholds  
  > "we used the GILDAS[^1] moment task and set the threshold limit to $3\sigma$ and $5\sigma$" (2.1 ALMA Band 6 and Band 7 observations)
   - software: GILDAS
   - fitting: _not stated_
   - validation: _not stated_
5. **Model CO(2-1) kinematics**: 3D tilted-ring fits: disk (vsys, i, PA fitted), then nuclear warp, radial velocity component (V_RAD=180 km/s) and combination; compared in p-v diagrams and residual velocity fields  
  > "we model the CO(2–1) data cube with $^{\rm 3D}$BAROLO (cite: DiTeodoro2015)." (5 CO(2–1) and CO(3–2) kinematics)
   - software: 3DBarolo
   - parameter: Kinematic center at AGN position of the unresolved 1.3 mm component  
  > "For the kinematic center we used the position of the AGN as that of the unresolved component from the two component fit to the 1.3 mm continuum emission" (5 CO(2–1) and CO(3–2) kinematics)
   - fitting: 3DBarolo tilted-ring fitting  
  > "This code was developed to fit 3D tilted-ring models to emission-line data cubes using simple rotating disks." (CO(2–1) and CO(3–2) kinematics)
   - validation: Visual comparison of model and observed p-v diagrams  
  > "Visually this last model (Figure [8](#fig:ALMACO21pv), 5th row) produces a better fit to p-v diagrams along both the major and minor axes" (5.3 Nuclear non-circular motions)
6. **Test bar-driven streaming**: Smoothed Maciejewski 0S20r simulation (0.2'' FWHM) scaled to observed velocities and compared with p-v diagrams  
  > "Then we smoothed it to the angular resolution of our ALMA CO(2–1) data (assuming a circular Gaussian with a FWHM of 0.2$''$)" (5.1 Streaming motions)
   - fitting: _not stated_
   - validation: _not stated_
7. **Molecular gas mass, column density, outflow rates**: CO(2-1) flux in 0.2'' aperture, CO(1-0)/CO(2-1) = 1, Sakamoto relation, then dM/dt = 3 v M/(R tan i)  
  > "$dM/dt = 3 \times v_{\rm out} \times M_{\rm mol}/(R_{\rm out} \times \tan(i_{\rm disk}))$ for a multi-conical outflow uniformly filled by the outflowing clouds" (7 Discussion and Conclusions)
   - parameter: v_out = 100 km/s, R_out = 35 pc  
  > "we take a typical value of $v_{\rm out} = 100\,{\rm km\,s}^{-1}$ and a size for the outflow of $R_{\rm out } = 35\,$pc" (7 Discussion and Conclusions)
   - assumption: X = 2e20 cm-2 (K km/s)-1, CO(1-0)/CO(2-1) brightness ratio 1  
  > "We take a CO(1–0)/CO(2–1) brightness temperature ratio of one" (6 Nuclear molecular gas mass and column density)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : Calibration and imaging (clean)  
  > "We calibrated and imaged the data using the ALMA reduction software CASA" (2.1 ALMA Band 6 and Band 7 observations)
- **GILDAS** : Moment maps and convolution  
  > "We used GILDAS to convolve the $850\,\mu$m continuum map" (3.2 Spectral index)
- **3DBarolo** : 3D tilted-ring kinematic modelling of CO(2-1)  
  > "This code was developed to fit 3D tilted-ring models to emission-line data cubes using simple rotating disks." (5 CO(2–1) and CO(3–2) kinematics)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| 1.3 mm flux, unresolved component | 0.51 | 0.15 | mJy | 2 | $0.51\pm 0.15\,$mJy and $1.92\pm0.21\,$mJy for the unresolved and resolved components |
| 1.3 mm flux, extended component | 1.92 | 0.21 | mJy | 2 | $0.51\pm 0.15\,$mJy and $1.92\pm0.21\,$mJy for the unresolved and resolved components |
| Host disk systemic velocity | 1140 | not stated | km/s | 5 | derived an average value of $v_{\rm sys} =1140$ km s$^{-1}$ |
| Host disk PA and inclination | PA_MAJ=152 deg, i=52 deg | not stated | deg | 5 | PA$_{\rm MAJ}=152\ensuremath{^\circ}$ and $i_{\rm disk}=52\ensuremath{^\circ}$ |
| Nuclear molecular gas mass (0.2'' aperture, ~15 pc) | 5e5 | not stated | Msun | 7 | We obtained a molecular gas mass in the inner 15 pc of approximately $5\times 10^5\,M_\odot$. |
| Molecular gas mass (0.5'' aperture) | 3e6 | not stated | Msun | 7 | we derived a mass in molecular gas of $3 \times 10^6\,M_\odot$ |
| Average H2 column density, inner ~15 pc | 2-3e23 | not stated | cm-2 | 7 | $N({\rm H}_2) = 2-3 \times 10^{23}\,{\rm cm}^{-2}$ |
| Molecular outflow rate NE | 5 | not stated | Msun/yr | 7 | $dM/dt = 5\,M_\odot\,{\rm
  yr}^{-1}$ and $dM/dt = 0.6\,M_\odot\,{\rm
  yr}^{-1}$ to the northeast and southwest of the AGN |
| Molecular outflow rate SW | 0.6 | not stated | Msun/yr | 7 | $dM/dt = 5\,M_\odot\,{\rm
  yr}^{-1}$ and $dM/dt = 0.6\,M_\odot\,{\rm
  yr}^{-1}$ to the northeast and southwest of the AGN |
| Maximum outflow velocity (inclination corrected) | 190-250 | not stated | km/s | 5 | maximum velocity of $150-200\,{\rm km\,s}^{-1}/\sin i_{\rm
  disk}\sim 190-250\,{\rm km\,s}^{-1}$ |

## Qualitative findings

- Nuclear CO and sub-mm continuum extend over tens of pc and connect to the circumnuclear ring, not a classical compact torus  
  > "do not resemble the *classical* compact torus" (abstract)

## Claim tuples

- H: Are the nuclear non-circular motions explained by the bar or a nuclear warp alone? | E: 3DBarolo disk, warp and radial models plus a bar simulation compared with p-v diagrams | R: Bar reproduces streaming at 1.5-3.5'' but not r<1'' minor-axis motions; warps do not reproduce them | F: Non-circular motions of 150-200 km/s are interpreted as a nuclear molecular outflow if in the host disk plane | **partially**
- H: Does NGC 3227 show a compact molecular torus? | E: CO(2-1), CO(3-2) and continuum morphology | R: Emission spans several tens of pc with clumps not coinciding with the AGN | F: No classical compact torus | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Inflow in nuclear disk plane rejected because required velocities are unrealistically high  
  > "would be unrealistically high for a nuclear inflow" (5.4 A nuclear molecular outflow)
- How they decided it was enough: _not stated_
- Limitation (authors): 3DBarolo cannot include radial components of opposite sign at one radius; warp not conclusively shown  
  > "with $^{\rm
  3D}$BAROLO we cannot include simultaneously at a particular radial distance radial velocity components with different signs" (5.3 Nuclear non-circular motions)
- Caveat (inferred, ours): Outflow interpretation depends on assumed geometry (plane of host disk)
- Caveat (inferred, ours): Fixed v_out=100 km/s is a 'typical value' and drives outflow rates
- Caveat (inferred, ours): Gas masses depend on assumed CO ratio and X factor
- Caveat (inferred, ours): Models compared only visually, no goodness-of-fit

## Reproducibility

- Data public (paper): Archive project codes given; public status not explicitly stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA.2016.1.00254.S and JAO.ALMA.2016.1.01236.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Clean parameters and masks
- Missing: Barolo configuration
- Missing: Exact aperture positions
- Data volume (inferred): ~50-200 GB raw for the two projects
- Score (inferred): 3/5, Data codes and main steps are given but imaging and 3DBarolo settings are largely missing.
- Rediscovery candidate: no, Model fitting is visual and many settings are unstated.

## Links

- Method: (cite: DiTeodoro2015) (3DBarolo)
- Method: (cite: GarciaBurillo2014) (outflow rate formula)
- Companion: (cite: AlonsoHerrero2018) (first paper of the series)
- Related: Swift/BAT 70-month catalog sample

## Checks

```json
{
 "quotes": 64,
 "quotes_ok": 64,
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
  "facts": 80,
  "stated": 44,
  "rate": 0.55
 },
 "evidence_ok": true
}
```
