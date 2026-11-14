# Organic molecules in the protoplanetary disk of DG Tauri revealed by ALMA

`2019A&A...623L...6P` | Astronomy and Astrophysics 2019 | first author: Podio, L. | arXiv: 1902.02720 | DOI: 10.1051/0004-6361/201834475

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks, astrochemistry
- Question: Where is formaldehyde and methanol emission located in the DG Tau disk, and what does it say about how these simple organics form?  
  > "It is thus crucial to map the distribution and investigate the formation of simple organics, such as formaldehyde and methanol, in protoplanetary disks." (abstract)
- Target **DG Tau**: coordinates RA(J2000)=04h27m04.70s, Dec=+26d06m15.72s (continuum peak)  
  > "The nearby T Tauri star DG Tau ($d=121\pm2$ pc, (cite: gaia16; gaia18))" (Introduction); "peak intensity of $33$ mJy/beam at R.A.(J2000)$=04^h 27^m 04^s.70$, Dec(J2000)$=+26\ensuremath{^\circ} 06\ensuremath{'} 15.72\ensuremath{''}$." (3 Ring of formaldehyde in the disk of DG Tau); z/distance 121 +/- 2 pc  
  > "The nearby T Tauri star DG Tau ($d=121\pm2$ pc, (cite: gaia16; gaia18))" (Introduction); "peak intensity of $33$ mJy/beam at R.A.(J2000)$=04^h 27^m 04^s.70$, Dec(J2000)$=+26\ensuremath{^\circ} 06\ensuremath{'} 15.72\ensuremath{''}$." (3 Ring of formaldehyde in the disk of DG Tau); distance from Gaia (cite: gaia16; gaia18)  
  > "The nearby T Tauri star DG Tau ($d=121\pm2$ pc, (cite: gaia16; gaia18))" (Introduction); "peak intensity of $33$ mJy/beam at R.A.(J2000)$=04^h 27^m 04^s.70$, Dec(J2000)$=+26\ensuremath{^\circ} 06\ensuremath{'} 15.72\ensuremath{''}$." (3 Ring of formaldehyde in the disk of DG Tau)

## Data provenance

- ALMA projects: 2016.1.00846.S
- bands: _not stated_
- frequencies and spectral setup: 12 high-resolution (0.122 MHz) spectral windows covering several molecular transitions  
  > "The correlator setup consists of 12 high-resolution (0.122 MHz) spectral windows (SPWs) covering several molecular transitions" (2 Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 17 m to 3.7 km  
  > "ALMA observations of DG Tau were performed during Cycle 4 in August 2017 with baselines ranging from 17 m to 3.7 km." (2 Observations)
- angular resolution: ~0.15 arcsec (~18 au)  
  > "at an unprecedented resolution of $\sim 0.15\ensuremath{''}$, i.e., $\sim 18$ au at a distance of 121 pc." (abstract)
- max recoverable scale: _not stated_
- sensitivity: line rms 1.7 mJy/beam (H2CO), 3 mJy/beam (CH3OH) per 0.162 km/s channel; continuum 0.3 mJy/beam  
  > "The continuum image has an r.m.s. of 0.3 mJy/beam." (2 Observations); "1.7" (Table 1)
- time on source: _not stated_
- observing dates: Cycle 4, August 2017  
  > "ALMA observations of DG Tau were performed during Cycle 4 in August 2017 with baselines ranging from 17 m to 3.7 km." (2 Observations)
- pi or archival as stated: _not stated_
- Line: o-H2CO 3(1,2)-2(1,1) (225697.775 MHz)
- Line: CH3OH 3(-2,2)-4(-1,4) E (230027.060 MHz)
- Line: CH3OH 5(0,5)-4(0,4) A (241791.431 MHz)
- Other facility **IRAM 30m**: H2CO line flux from literature for comparison with ALMA filtered flux  
  > "The H$_2$CO line peak and integrated flux collected with the 11$\ensuremath{''}$ beam of the IRAM 30m telescope (cite: guilloteau13)" (3 Ring of formaldehyde in the disk of DG Tau)
- External data: ProDiMo disk model (gas density, temperature, H2 column, CO iceline ~30 au)  
  > "Using the H$_2$ column density in the outer disk ($> 40$ au) from the disk model by (cite: podio13)" (4 Abundance of organic molecules) [from (cite: podio13)]
- External data: Continuum dust opacity and surface density at 1.3 mm  
  > "we estimate the optical depth of the disk at 1.3 mm from the dust opacity and surface density given by (cite: isella10)" (5 H2CO formation) [from (cite: isella10)]
- External data: ortho-to-para ratio 1.8-2.8  
  > "assuming an ortho-to-para ratio of $1.8-2.8$ (cite: guzman18a)" (4 Abundance of organic molecules) [from (cite: guzman18a)]
- External data: Molecular parameters and partition functions from CDMS  
  > "adopting the molecular parameters and partition function from the Cologne Database of Molecular Spectroscopy (CDMS, (cite: muller01))" (4 Abundance of organic molecules) [from (cite: muller01)]
- External data: Polarization map at 0.87 mm  
  > "The map by (cite: bacciotti18) also indicates that the orientation of the linear polarization vector changes" (6 Disk chemistry and dust properties) [from (cite: bacciotti18)]
- Simulation/model as data: ProDiMo DG Tau model used for gas density/temperature in RADEX line-opacity check  
  > "gas densities and temperatures from our ProDiMo DG Tau model (n$_{\rm H_2} \sim 10^{10} - 10^{12}$ cm$^{-3}$ and T$_{\rm gas} > 30$ K" (5 H2CO formation)

## Processing

### Calibration

- pipeline or manual: ALMA pipeline, standard procedures  
  > "Data reduction was carried out following standard procedures using the ALMA pipeline in CASA 4.7.2." (2 Observations)
- casa version: CASA 4.7.2  
  > "using the ALMA pipeline in CASA 4.7.2" (2 Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: quasars J0238+1636 and J0510+1800  
  > "The flux calibration was performed using quasars J0238+1636 and J0510+1800" (2 Observations)
- flux scale uncertainty: ~10%  
  > "obtaining an accuracy of $\sim 10\%$" (2 Observations)
- self calibration: Phase self-cal on continuum using line-free channels, applied to continuum-subtracted SPWs  
  > "Self-calibration was performed on the source continuum emission, by combining a selection of line-free channels, and applying the phase solutions to the continuum-subtracted SPWs." (2 Observations)

### Imaging

- task: tclean  
  > "Continuum images and spectral cubes were produced with tclean applying a manually selected mask and Briggs parameter of 0.5." (2 Observations)
- deconvolver: _not stated_
- weighting robust: Briggs 0.5  
  > "applying a manually selected mask and Briggs parameter of 0.5" (2 Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: manually selected mask  
  > "applying a manually selected mask and Briggs parameter of 0.5" (2 Observations)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: H2CO 0.17x0.13 arcsec (PA -20); CH3OH 0.16x0.13 (-21) and 0.16x0.12 (-21)  
  > "$0.17\ensuremath{''} \times 0.13\ensuremath{''}$ ($-20\ensuremath{^\circ}$)" (Table 1)
- final rms: 1.7 mJy/beam (H2CO), 3 mJy/beam (CH3OH) per 0.162 km/s channel; continuum 0.3 mJy/beam  
  > "The continuum image has an r.m.s. of 0.3 mJy/beam." (2 Observations)

### Inherited from earlier work

- Stellar mass 0.7 Msun for Keplerian rotation  
  > "Assuming Keplerian rotation around a $0.7$ M$_{\odot}$ star as in (cite: podio13)" (3 Ring of formaldehyde in the disk of DG Tau) [from (cite: podio13)]
- LTE optically thin column density method  
  > "by assuming local thermodynamic equilibrium (LTE) and optically thin emission (cite: bianchi17a)" (4 Abundance of organic molecules) [from (cite: bianchi17a)]

### Not stated but needed to reproduce (our reading)

- Line-free channel ranges for continuum and self-cal
- Self-calibration solution intervals and number of iterations
- Mask definitions and clean thresholds
- Image size, cell size, and whether channel binning was used
- Details of the column density equation and treatment of beam/ring integration
- Radial profile bin width and deprojection details
- Observation integration times and array configuration details

## Analysis recipe

1. **Calibrate and image continuum and line cubes**: ALMA pipeline, self-calibration on continuum, tclean with Briggs 0.5 and manual mask  
  > "Continuum images and spectral cubes were produced with tclean applying a manually selected mask and Briggs parameter of 0.5." (2 Observations)
   - software: CASA, tclean
   - fitting: _not stated_
   - validation: _not stated_
2. **Measure continuum disk geometry**: 2D Gaussian fit of 1.3 mm continuum for deconvolved axes, inclination and PA  
  > "By applying a 2D Gaussian fit, we determine the disk major and minor axes deconvolved from the beam" (3 Ring of formaldehyde in the disk of DG Tau)
   - fitting: 2D Gaussian  
  > "By applying a 2D Gaussian fit, we determine the disk major and minor axes deconvolved from the beam" (3 Ring of formaldehyde in the disk of DG Tau)
   - validation: Compared with 0.87 and 1.3 mm estimates and jet geometry  
  > "These values are in good agreement with the estimates obtained at 0.87 mm and 1.3 mm" (3 Ring of formaldehyde in the disk of DG Tau)
3. **Moment maps and radial profiles**: Moment 0/1 over 3.24-9.24 km/s with 3 sigma mask; azimuthally averaged deprojected radial profiles  
  > "Then radial intensity profiles of the H$_2$CO $3_{1,2} - 2_{1,1}$ line and of the 1.3 mm continuum are obtained by azimuthally averaging the intensity maps after deprojecting" (3 Ring of formaldehyde in the disk of DG Tau)
   - software: CASA
   - parameter: i=41 deg, PA=128 deg  
  > "after deprojecting for $i= 41\ensuremath{^\circ}$ and PA$= 128\ensuremath{^\circ}$" (3 Ring of formaldehyde in the disk of DG Tau)
   - fitting: _not stated_
   - validation: Moment 8 map without threshold supports ring (S/N~5)  
  > "The moment 8 map strongly supports the ring detection with a S/N $\sim 5$." (Appendix A)
4. **Derive column densities and abundances**: LTE optically thin ring-integrated intensities; CH3OH upper limits from same pixels/velocities; o/p ratio 1.8-2.8; abundances from ProDiMo H column  
  > "The maps of the undetected CH$_3$OH lines are integrated over the same spatial region and velocity range as for the H$_2$CO line" (4 Abundance of organic molecules)
   - software: CDMS
   - parameter: Tex = 30-300 K; ring 0.33-0.75 arcsec (40-90 au)  
  > "assuming an excitation temperature T$_{\rm ex} = 30-300$ K" (4 Abundance of organic molecules)
   - assumption: LTE, optically thin, CH3OH co-spatial with H2CO  
  > "under the assumption that CH$_3$OH originates from the same disk region as H$_2$CO" (4 Abundance of organic molecules)
   - fitting: _not stated_
   - validation: Compared with disk chemistry models and other disks  
  > "are in agreement with the predictions of chemistry models of protoplanetary disks around T Tauri stars" (4 Abundance of organic molecules)
5. **Check continuum and line optical depth**: Continuum brightness temperature vs dust temperature from model; RADEX non-LTE for line opacity  
  > "we checked the H$_2$CO $3_{1,2} - 2_{1,1}$ line opacity by using the non-LTE radiative transfer code RADEX" (5 H2CO formation)
   - software: RADEX, ProDiMo
   - parameter: N_H2CO up to 1e15 cm-2, line width ~6 km/s  
  > "a line width of $\sim 6$ km s$^{-1}$" (5 H2CO formation)
   - fitting: _not stated_
   - validation: Line opacity max ~1  
  > "the H$_2$CO line optical depth reach a maximum value of $\sim 1$" (5 H2CO formation)
6. **Search for continuum substructure**: Second derivative of major-axis continuum profile in 5 au bins, averaged NW and SE  
  > "we computed the second derivative of the radial intensity profile (by calculating the differentials over bins of 5 au, averaged between the the NW and SE sides)" (Appendix B)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.7.2: pipeline calibration, tclean imaging, moment maps  
  > "using the ALMA pipeline in CASA 4.7.2" (2 Observations)
- **RADEX** : non-LTE H2CO line opacity check  
  > "using the non-LTE radiative transfer code RADEX (cite: vandertak07)" (5 H2CO formation)
- **ProDiMo** : DG Tau thermo-chemical disk model for densities/temperatures  
  > "gas densities and temperatures from our ProDiMo DG Tau model" (5 H2CO formation)
- **CDMS** : molecular parameters and partition functions  
  > "adopting the molecular parameters and partition function from the Cologne Database of Molecular Spectroscopy" (4 Abundance of organic molecules)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Continuum integrated flux at 1.3 mm | 297 | not stated | mJy | 1 | shows a smooth distribution, with integrated flux of $297$ mJy |
| Disk inclination | 41 | 2 | deg | 2 | $i= 41\ensuremath{^\circ} \pm 2\ensuremath{^\circ}$ |
| Disk position angle | 128 | 16 | deg | 2 | PA$= 128\ensuremath{^\circ} \pm 16\ensuremath{^\circ}$ |
| H2CO ring peak radius | ~62 | not stated | au | 3 | the peak of the H$_2$CO emission is at $\sim 62$ au |
| Continuum edge radius (3 sigma) | 66 | not stated | au | 3 | R$_{\rm 1.3~mm} = 66$ au at 3$\sigma$ |
| H2CO integrated flux | 292 | not stated | mJy km/s | 4 | 292 |
| Total H2CO column density | 0.3-4e14 | not stated | cm-2 | 4 | N$_{\rm H_2CO}\sim 0.3-4 \times 10^{14}$ cm$^{-2}$ |
| CH3OH column density upper limit | <0.04-0.7e14 | not stated | cm-2 | 4 | N$_{\rm CH_3OH} < 0.04-0.7 \times 10^{14}$ cm$^{-2}$ |
| Inner 40 au o-H2CO beam-averaged column density upper limit | ~0.5-6e13 | not stated | cm-2 | 4 | upper limit on the o-H$_2$CO beam-averaged column density of $\sim 0.5-6 \times 10^{13}$ cm$^{-2}$ |
| H2CO abundance | 6e-12 - 3e-10 | not stated | dimensionless | 4 | X$_{\rm H_2CO} \sim 6 \times 10^{-12} - 3 \times 10^{-10}$ |
| Continuum shoulder radius | ~41 | not stated | au | 6 | the center of the observed continuum intensity enhancement is located at $\sim41$ au. |

## Qualitative findings

- H2CO ring is asymmetric, redshifted side ~1.5 times brighter than blueshifted side  
  > "the redshifted side is $\sim 1.5$ times brighter than the blueshifted side" (6 Disk chemistry and dust properties)
- ALMA filters out extended H2CO emission relative to IRAM 30m  
  > "This indicates that ALMA filters out the extended H$_2$CO emission from the outflow or the envelope" (3 Ring of formaldehyde in the disk of DG Tau)

## Claim tuples

- H: Is H2CO in the DG Tau disk distributed as a ring tied to grain-surface formation? | E: Imaged o-H2CO 3_12-2_11 at 0.15 arcsec and built radial profiles | R: Ring from ~40 au, peak ~62 au, outside CO iceline (~30 au) | F: H2CO abundance enhanced in outer disk by CO hydrogenation on grains | **supported**
- H: Is the inner H2CO hole due to continuum absorption? | E: Optical depth estimates from continuum brightness temperature and models, RADEX line opacity | R: Continuum thin beyond ~25 au, line tau max ~1 | F: Ring reflects a real abundance increase beyond ~40 au | **supported**
- H: Is CH3OH detected and what is CH3OH/H2CO? | E: Integrated CH3OH cubes over H2CO ring region | R: No detection, rms 3 mJy/beam | F: CH3OH/H2CO <1, consistent with models | **supported**
- H: Is H2CO chemistry linked to dust properties? | E: Compared ring inner edge with polarization flip and continuum shoulder | R: Both near 40 au | F: Hints at link and possible dust substructure | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Continuum absorption as cause of inner H2CO depression is considered but argued not dominant beyond ~25 au  
  > "To evaluate if absorption by the dust continuum affects the observed H$_2$CO intensity" (5 H2CO formation)
- How they decided it was enough: _not stated_
- Limitation (authors): Testing desorption mechanisms needs higher resolution and multi-molecule modeling  
  > "a test of the proposed mechanisms would require higher angular resolution observations of multiple molecules and detailed modeling" (5 H2CO formation)
- Caveat (inferred, ours): Column densities rely on a model-derived temperature range and LTE; uncertainties are large
- Caveat (inferred, ours): No uncertainties on ring peak radius or fluxes
- Caveat (inferred, ours): Polarization link is qualitative

## Reproducibility

- Data public (paper): Project code given; public status not stated  
  > "This paper uses ALMA data from project 2016.1.00846.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Self-cal parameters
- Missing: Line-free channels
- Missing: Image size/cell
- Missing: Column density formula details
- Data volume (inferred): ~100-300 GB raw for one Cycle 4 long-baseline EB
- Score (inferred): 3/5, Project code and key imaging settings given, but several parameters and model inputs are missing.
- Rediscovery candidate: no, Data likely public after proprietary period, but the recipe depends on model inputs and unstated details; results partly model-dependent.

## Links

- Method: (cite: bianchi17a) (LTE optically thin column density method)
- Companion: (cite: bacciotti18) (ALMA polarization of the DG Tau disk)
- Companion: (cite: podio13) (ProDiMo disk model of DG Tau)

## Checks

```json
{
 "quotes": 76,
 "quotes_ok": 76,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 11,
 "numeric_problems": 0,
 "fill": {
  "facts": 82,
  "stated": 52,
  "rate": 0.634
 },
 "evidence_ok": true
}
```
