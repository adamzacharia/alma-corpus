# Evidence for a CO Desorption Front in the Outer AS 209 Disk

`2016ApJ...823L..18H` | The Astrophysical Journal Letters 2016 | first author: Huang, Jane | arXiv: 1605.06516 | DOI: 10.3847/2041-8205/823/1/L18

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks, astrochemistry
- Question: Does CO isotopologue emission in the AS 209 disk show CO enhancement (desorption) in the outer disk, beyond the expected CO snowline?  
  > "In this letter, we present evidence for a CO desorption front in the outer disk of AS 209, based primarily on the emission pattern of C$^{18}$O." (Introduction)
- Target **AS 209**: coordinates RA 16h49m15.29s, Dec -14d22'08.6" (J2000)  
  > "AS 209 (J2000.0 R.A. $16^{\textup{h}}49^{\textup{m}}15^{\textup{s}}.29$, decl. $-14\ensuremath{^\circ} 22'08.6\ensuremath{''}$)" (Observations and Data Reduction); "The system is thought to be part of the Ophiuchus star-forming region about 120 pc away (cite: 2008ApJ...675L..29L)." (Introduction); z/distance about 120 pc  
  > "AS 209 (J2000.0 R.A. $16^{\textup{h}}49^{\textup{m}}15^{\textup{s}}.29$, decl. $-14\ensuremath{^\circ} 22'08.6\ensuremath{''}$)" (Observations and Data Reduction); "The system is thought to be part of the Ophiuchus star-forming region about 120 pc away (cite: 2008ApJ...675L..29L)." (Introduction); distance from Loinard et al. 2008 (cite: 2008ApJ...675L..29L)  
  > "AS 209 (J2000.0 R.A. $16^{\textup{h}}49^{\textup{m}}15^{\textup{s}}.29$, decl. $-14\ensuremath{^\circ} 22'08.6\ensuremath{''}$)" (Observations and Data Reduction); "The system is thought to be part of the Ophiuchus star-forming region about 120 pc away (cite: 2008ApJ...675L..29L)." (Introduction)

## Data provenance

- ALMA projects: 2013.1.00226.S
- bands: Band 6 (1.4 mm continuum)  
  > "Observations were set up with thirteen Band 6 spectral windows (SPWs)." (Observations and Data Reduction)
- frequencies and spectral setup: 12 SPWs with 61 kHz resolution and 59 MHz bandwidth; one with 122 kHz resolution and 469 MHz bandwidth  
  > "Twelve (including those with CO isotopologue lines) had spectral resolutions of 61 kHz and bandwidths of 59 MHz, while the thirteenth had a resolution of 122 kHz and bandwidth of 469 MHz." (Observations and Data Reduction)
- continuum bandwidth: _not stated_
- arrays: thirty-four 12 m antennae  
  > "The configuration consisted of thirty-four 12 m antennae, with baselines between 20 and 650 m." (Observations and Data Reduction)
- configurations: _not stated_
- baselines: 20 to 650 m  
  > "The configuration consisted of thirty-four 12 m antennae, with baselines between 20 and 650 m." (Observations and Data Reduction)
- angular resolution: line beams about 0.62-0.65" x 0.57-0.59"; continuum 0.53" x 0.51"  
  > "(synthesized beam: $0.53\ensuremath{''}\times0.51\ensuremath{''}$ $(-78.07\ensuremath{^\circ})$)" (Observational Results)
- max recoverable scale: _not stated_
- sensitivity: continuum 0.27 mJy/beam; channel rms 8-15 mJy/beam in 0.1 km/s bins  
  > "The 1.4 mm dust continuum noise level is $\sigma =0.27$ mJy beam$^{-1}$" (Observations and Data Reduction)
- time on source: 21 minutes  
  > "with 21 minutes on source" (Observations and Data Reduction)
- observing dates: 2014 July 2  
  > "on 2014 July 2 (project code ADS/JAO.ALMA#2013.1.00226)" (Observations and Data Reduction)
- pi or archival as stated: _not stated_
- Line: 12CO J=2-1 (230.53800 GHz)
- Line: 13CO J=2-1 (220.39868 GHz)
- Line: C18O J=2-1 (219.56035 GHz)
- External data: Position angle 86 deg and inclination 38 deg  
  > "The position angle and inclination of 86$\ensuremath{^\circ}$ and 38$\ensuremath{^\circ}$, respectively, are adopted from (cite: 2009ApJ...700.1502A)." (Observational Results) [from (cite: 2009ApJ...700.1502A)]
- External data: Midplane dust temperature power-law fit T10,mid=47.3 K, q_mid=0.48  
  > "From a power-law fit to the midplane dust temperature that Andrews et al. (cite: 2009ApJ...700.1502A) calculated for the AS 209 disk, $T_\text{10,mid} =47.3$ K and $q_\text{mid}$ = 0.48." (A toy model for CO desorption in the outer disk) [from (cite: 2009ApJ...700.1502A)]
- External data: ISM isotopologue ratios 12CO/13CO=69 and 12CO/C18O=557  
  > "We fix the $^{12}$CO/$^{13}$CO and $^{12}$CO/C$^{18}$O ratios to the ISM values of 69 and 557, respectively (cite: 1999RPPh...62..143W)." (A toy model for CO desorption in the outer disk) [from (cite: 1999RPPh...62..143W)]
- Simulation/model as data: Parametric toy model (Lynden-Bell & Pringle surface density plus Gaussian CO ring) with RADMC-3D synthetic observations, with and without ring (B=3 vs B=0)  
  > "For comparison, we also model CO abundances without an outer ring by setting $B = 0$ in Eq. [\[eq:1\]](#eq:1), holding other parameters the same." (A toy model for CO desorption in the outer disk)

## Processing

### Calibration

- pipeline or manual: NAASC-provided calibration script, modified to scale visibility weights  
  > "ALMA/NAASC staff provided a calibration script using the quasar J1733-1304 for bandpass and phase calibration and Titan for flux calibration." (Observations and Data Reduction)
- casa version: CASA 4.4.0  
  > "executed in CASA 4.4.0 to calibrate visibilities" (Observations and Data Reduction)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Titan (bandpass/phase: J1733-1304)  
  > "ALMA/NAASC staff provided a calibration script using the quasar J1733-1304 for bandpass and phase calibration and Titan for flux calibration." (Observations and Data Reduction)
- flux scale uncertainty: ~10%  
  > "the ALMA systematic flux uncertainty is $\sim$10$\%$" (Observations and Data Reduction)
- self calibration: Phase self-cal of CO SPWs using solutions from six SPWs free of strong line emission  
  > "The CO isotopologue SPWs were phase self-calibrated with solutions obtained from averaging six SPWs free of strong line emission." (Observations and Data Reduction)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: Keplerian rotation masks  
  > "each line was imaged and CLEANed with Keplerian rotation masks" (Observations and Data Reduction)
- multiscale scales: _not stated_
- continuum subtraction: in the uv-plane  
  > "After subtracting the continuum in the uv-plane, each line was imaged and CLEANed with Keplerian rotation masks." (Observations and Data Reduction)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 12CO 0.62"x0.57"; 13CO 0.63"x0.58"; C18O 0.65"x0.59"  
  > "$0.65\ensuremath{''}\times 0.59\ensuremath{''}$ $(-72.99\ensuremath{^\circ})$" (Table 1)
- final rms: channel rms 10, 15, 8 mJy/beam (0.1 km/s bins) for 12CO, 13CO, C18O  
  > "Channel rms for 0.1 km s$^{-1}$ bins and integrated flux values are listed in Table [1](#Table1)." (Observations and Data Reduction)

### Inherited from earlier work

- Earlier reduction of 1.4 mm continuum and 13CO data published previously  
  > "An earlier reduction of the 1.4 mm continuum and $^{13}$CO data was published in (cite: 2015ApJ...809L..26H) as part of an N$_2$D$^+$ analysis." (Observations and Data Reduction) [from (cite: 2015ApJ...809L..26H)]
- Toy model parametrization adapted from earlier parametric disk models  
  > "Similarly to Rosenfeld et al. (cite: 2013ApJ...774...16R) and Dartois et al. (cite: 2003AA...399..773D), we model the vertical temperature gradient in cylindrical coordinates as" (A toy model for CO desorption in the outer disk) [from (cite: 2013ApJ...774...16R); (cite: 2003AA...399..773D)]

### Not stated but needed to reproduce (our reading)

- tclean/clean parameters: weighting/robust, cell size, image size, deconvolution threshold
- Which SPWs were used for self-calibration and solution interval
- Velocity range and channel width of final image cubes beyond 0.1 km/s
- Details of the Keplerian mask parameters
- Stellar mass/distance adopted in toy model beyond 0.9 Msun and 120 pc; grid setup and photon/radiative transfer settings in RADMC-3D
- Method of azimuthal averaging/deprojection bins
- Noise-added simulated visibilities random seed

## Analysis recipe

1. **Calibrate and image data**: Modified NAASC calibration script in CASA, phase self-cal, uv continuum subtraction, CLEAN with Keplerian masks  
  > "After subtracting the continuum in the uv-plane, each line was imaged and CLEANed with Keplerian rotation masks." (Observations and Data Reduction)
   - software: CASA 4.4.0
   - parameter: 0.1 km/s channels  
  > "Channel rms for 0.1 km s$^{-1}$ bins and integrated flux values are listed in Table [1](#Table1)." (Observations and Data Reduction)
   - fitting: _not stated_
   - validation: Continuum flux consistent with SMA measurement  
  > "which is consistent with Submillimeter Array observations of AS 209 presented in (cite: 2011ApJ...734...98O)" (Observations and Data Reduction)
2. **Make integrated intensity maps and deprojected radial profiles**: Sum -2.0 to 11.0 km/s; deproject and azimuthally average using PA 86 deg, inc 38 deg  
  > "integrated intensity maps (summed from -2.0 to 11.0 km s$^{-1}$)" (Observational Results)
   - assumption: PA 86 deg, inclination 38 deg from Andrews et al. 2009  
  > "The position angle and inclination of 86$\ensuremath{^\circ}$ and 38$\ensuremath{^\circ}$, respectively, are adopted from (cite: 2009ApJ...700.1502A)." (Observational Results)
   - fitting: _not stated_
   - validation: _not stated_
3. **Toy model of CO desorption ring and synthetic observations**: Parametric density/temperature model with Gaussian ring in CO surface density; RADMC-3D line images; sampled at observed uv with VIS_SAMPLE; noise added; CLEANed in CASA; compared with and without ring  
  > "After computing sky brightness images at the orientation of the AS 209 disk, model visibilities were produced at the same spatial frequencies as the AS 209 data by using Python package VIS_SAMPLE." (A toy model for CO desorption in the outer disk)
   - software: RADMC-3D, VIS_SAMPLE, CASA 4.4.0
   - parameter: Sigma_c=5e-5 g/cm2, gamma=1, r_c=100 AU, B=3, r_ring=150 AU, sigma_ring=20 AU  
  > "we set $\Sigma_c = 5\times 10^{-5} \text{ g cm}^{-2}$, $\gamma = 1$, $r_c = 100$ AU, $B = 3$, $r_\text{ring} = 150$ AU, and $\sigma_\text{ring} = 20$ AU." (A toy model for CO desorption in the outer disk)
   - parameter: turbulent broadening xi = 0.01 km/s  
  > "the turbulent broadening parameter was set to $\xi =$ 0.01 km s$^{-1}$" (A toy model for CO desorption in the outer disk)
   - assumption: LTE; Keplerian velocities; ISM isotopologue ratios 69 and 557; T_atm,10=150 K, q_atm=0.5; C18O traces CO column  
  > "Local thermal equilibrium was assumed because CO and its isotopologues have low critical densities relative to disk gas densities" (A toy model for CO desorption in the outer disk)
   - fitting: No formal fit; parameters set by experimentation to reproduce main features  
  > "After some experimentation to determine parameter values that could reproduce the main features of the observations" (A toy model for CO desorption in the outer disk)
   - validation: Qualitative morphology comparison with and without ring (B=0)  
  > "only the model with an outer CO ring, shown in Figure [3](#fig3), reproduces the central peak and ring in the C$^{18}$O emission, and the shoulder in $^{13}$CO emission." (A toy model for CO desorption in the outer disk)

## Software

- **CASA** 4.4.0: calibration, imaging, and imaging of model visibilities  
  > "executed in CASA 4.4.0 to calibrate visibilities" (Observations and Data Reduction)
- **RADMC-3D** : radiative transfer for model CO line emission  
  > "with the radiative transfer code RADMC-3D (cite: 2012ascl.soft02015D)" (A toy model for CO desorption in the outer disk)
- **VIS_SAMPLE** : sampling model images at observed spatial frequencies  
  > "model visibilities were produced at the same spatial frequencies as the AS 209 data by using Python package VIS_SAMPLE." (A toy model for CO desorption in the outer disk)
- **PWKIT** : listed in software section; use not stated  
  > "PWKIT (<https://github.com/pkgw/pwkit>)" (Software)
- **CUBEHELIX** : listed in software section; use not stated  
  > "CUBEHELIX (<https://github.com/jradavenport/cubehelix>)" (Software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| 1.4 mm continuum flux density | 252 | 25 | mJy | 1 | is 252 $\pm$ 25 mJy |
| 12CO J=2-1 integrated flux | 7.5 | 0.8 | Jy km/s | 1 | 7.5$\pm$0.8 |
| 13CO J=2-1 integrated flux | 2.1 | 0.2 | Jy km/s | 1 | 2.1$\pm$0.2 |
| C18O J=2-1 integrated flux | 0.54 | 0.05 | Jy km/s | 1 | 0.54$\pm$0.05 |
| C18O ring radius | ~1 (120) | not stated | arcsec (AU) | 2 | but also has a ring at $\sim1''$ coinciding with the $^{13}$CO “bulge." |
| Peak 1.4 mm continuum brightness temperature | 7 | not stated | K | 2 | The peak brightness temperature of the 1.4 mm AS 209 continuum is only 7 K |

## Qualitative findings

- C18O shows central peak plus ring at ~1" (120 AU), 13CO shows a shoulder, 12CO decreases monotonically  
  > "In contrast to $^{12}$CO, the $^{13}$CO profile bulges outward at $\sim1''$ (120 AU)." (Observational Results)

## Claim tuples

- H: CO is enhanced in the outer AS 209 disk via a desorption front outside the CO snowline | E: ALMA 12CO, 13CO, C18O J=2-1 imaging and radial profiles | R: C18O has a central peak plus ring at ~1" well outside the expected snowline (30-80 AU) | F: The ring is interpreted as onset of CO desorption near the edge of the mm dust disk | **supported**
- H: An outer CO abundance enhancement can explain differing isotopologue morphologies | E: Toy model with and without Gaussian CO ring, synthetic ALMA observations | R: Only model with ring reproduces C18O ring and 13CO shoulder | F: Opacity differences hide non-monotonic column density in 12CO/13CO | **supported**
- H: Alternatives (selective photodissociation, dust opacity) explain the ring | E: Comparison with literature models and continuum brightness temperature | R: Photodissociation predicts lower outer C18O; continuum optically thin | F: These are less likely, though narrow optically thick dust rings not excluded | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Toy model used to explore qualitatively how a CO ring would affect different isotopologues  
  > "To explore qualitatively how such a CO distribution can affect the emission profiles of different isotopologues, we simulated observations of a T Tauri disk" (A toy model for CO desorption in the outer disk)
- Alternative: Selective photodissociation rejected as less likely because it lowers outer C18O intensity  
  > "whereas we observe an increase in C$^{18}$O intensity in the outer disk of AS 209." (Discussion)
- How they decided it was enough: _not stated_
- Limitation (authors): Thermal vs non-thermal desorption contributions not constrained; narrow optically thick dust rings need higher resolution  
  > "Further observations and modeling are necessary to constrain the relative contributions of thermal versus non-thermal processes." (Discussion)
- Caveat (inferred, ours): Toy model is not fitted; parameters tuned by hand, no uncertainties or degeneracy exploration
- Caveat (inferred, ours): Ring may reflect temperature or unresolved dust structure rather than abundance
- Caveat (inferred, ours): Cloud contamination on west side affects profiles
- Caveat (inferred, ours): Single short observation with ~0.6" beam

## Reproducibility

- Data public (paper): ALMA project data acknowledged; public status not explicitly stated  
  > "This paper makes use of ALMA data ADS/JAO.ALMA#2013.1.00226.S." (Acknowledgments)
- Products in archive: _not stated_
- Code: VIS_SAMPLE and PWKIT are public on GitHub; toy model scripts not released  
  > "VIS_SAMPLE (<https://github.com/AstroChem/vis_sample>)" (Software)
- Missing: Imaging parameters (weighting, cell, size, thresholds)
- Missing: Toy model code and RADMC-3D grid settings
- Missing: Radial profile extraction details
- Data volume (inferred): ~10-30 GB raw single-EB data
- Score (inferred): 3/5, Public single-EB data with stated calibration, but imaging parameters and toy model setup are incomplete and model is qualitative.
- Rediscovery candidate: no, Key results are mostly morphological; imaging details and model setup are not fully specified.

## Links

- Method: Rosenfeld et al. 2013a (cite: 2013ApJ...774...16R) (Parametric disk temperature/density model basis)
- Companion: Huang & Öberg 2015 (cite: 2015ApJ...809L..26H) (Earlier reduction of the same continuum and 13CO data)

## Checks

```json
{
 "quotes": 66,
 "quotes_ok": 66,
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
  "facts": 72,
  "stated": 49,
  "rate": 0.681
 },
 "evidence_ok": true
}
```
