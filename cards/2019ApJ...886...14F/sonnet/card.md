# An ALMA View of Molecular Filaments in the Large Magellanic Cloud. I. The Formation of High-mass Stars and Pillars in the N159E-Papillon Nebula Triggered by a Cloud-Cloud Collision

`2019ApJ...886...14F` | The Astrophysical Journal 2019 | first author: Fukui, Yasuo | arXiv: 1811.00812 | DOI: 10.3847/1538-4357/ab4900

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, nearby_galaxies
- Question: What are the filamentary, pillar and protostellar structures of the N159E-Papillon Nebula at 0.06-0.07 pc resolution, and did a cloud-cloud collision trigger their formation?  
  > "We suggest that a cloud–cloud collision triggered the formation of the filaments and protostar within the last $\sim$2 Myr." (abstract)
- Target **N159E-Papillon Nebula (LMC)**: coordinates RA 5h40m04.0s, Dec -69d44m34.0s (J2000)  
  > "The central coordinate of the observed field toward the N159E-Papillon region was ($\alpha_{\rm J2000.0}$, $\delta_{\rm J2000.0}$) = (5$^{\rm h}$40$^{\rm m}$04.0s, -69$^\circ$44$'$34.0$''$)." (2 Observations); "the Large Magellanic Cloud (LMC) is close to us at a distance of $\sim$50 kpc (cite: Schaefer08; de14)" (Introduction); z/distance ~50 kpc  
  > "The central coordinate of the observed field toward the N159E-Papillon region was ($\alpha_{\rm J2000.0}$, $\delta_{\rm J2000.0}$) = (5$^{\rm h}$40$^{\rm m}$04.0s, -69$^\circ$44$'$34.0$''$)." (2 Observations); "the Large Magellanic Cloud (LMC) is close to us at a distance of $\sim$50 kpc (cite: Schaefer08; de14)" (Introduction); distance from Schaefer08; de Grijs et al. 2014  
  > "The central coordinate of the observed field toward the N159E-Papillon region was ($\alpha_{\rm J2000.0}$, $\delta_{\rm J2000.0}$) = (5$^{\rm h}$40$^{\rm m}$04.0s, -69$^\circ$44$'$34.0$''$)." (2 Observations); "the Large Magellanic Cloud (LMC) is close to us at a distance of $\sim$50 kpc (cite: Schaefer08; de14)" (Introduction)

## Data provenance

- ALMA projects: 2016.1.01173.S, 2012.1.00554.S
- bands: Band 6 (211–275 GHz), Cycle 4  
  > "with Band 6 (211–275 GHz) in Cycle 4" (2 Observations)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: 12 m array alone  
  > "by using the 12 m array alone" (2 Observations)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.28'' x 0.25'' for lines (0.06-0.07 pc); 0.26'' x 0.23'' continuum  
  > "The synthesized beam sizes of the molecular lines ($^{12}$CO, $^{13}$CO, and C$^{18}$O) are 0.28$''$ $\times$ 0.25$''$" (2 Observations)
- max recoverable scale: _not stated_
- sensitivity: ~4.0 mJy/beam (1.4 K) 12CO, ~4.5 mJy/beam 13CO and C18O at 0.2 km/s; continuum ~0.027 mJy/beam  
  > "The beam size and RMS noise level for the 1.3 mm continuum map are 0.26$''$ $\times$ 0.23$''$, and $\sim$0.027 mJy beam$^{-1}$, respectively." (2 Observations)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: Cycle 4 PI Y. Fukui program; Cycle 1 data from Paper I used for comparison  
  > "as a part of the multi-objects survey in N159 (P.I. Y. Fukui #2016.1.01173.S.)" (2 Observations)
- Line: 12CO J=2-1 (not stated)
- Line: 13CO J=2-1 (not stated)
- Line: C18O J=2-1 (not stated)
- Other facility **ALMA Cycle 1 (2012.1.00554.S)**: Lower-resolution CO data for comparison and missing flux check  
  > "We estimated the missing flux of our Cycle 4 image in the N159E-Papillon region using the Cycle 1 data (Paper I)." (Appendix)
- External data: Outflow mass conversion Xco = 7e20 cm-2 (K km/s)-1 and CO 2-1/1-0 ratio of 1.0  
  > "$X_{\rm co}$ = 7 $\times$ 10$^{20}$ cm$^{-2}$ (K km s$^{-1}$)$^{-1}$ cm$^{-2}$ (cite: Fukui08)" (Table 2) [from (cite: Fukui08)]
- External data: Dust emissivity kappa_1.3mm = 1 cm2/g  
  > "$\kappa_{\rm 1.3 mm}$ of 1 cm$^{2}$ g$^{-1}$ for protostellar envelopes (cite: Oss94)" (3.3 Protostellar sources) [from (cite: Oss94)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: not applied  
  > "We did not apply the self-calibration process." (2 Observations)

### Imaging

- task: tclean in CASA  
  > "we used $``$tclean$"$, which is implemented in the Common Astronomy Software Application package (cite: McMullin07)" (2 Observations)
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 0.5  
  > "using the Briggs weighting with a robust parameter of 0.5" (2 Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: tclean noise threshold ~1 sigma; moment-masked cubes for velocity analysis  
  > "with a noise threshold of the $\sim$1$\sigma$ noise level" (2 Observations)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.28'' x 0.25'' lines; 0.26'' x 0.23'' continuum  
  > "The beam size and RMS noise level for the 1.3 mm continuum map are 0.26$''$ $\times$ 0.23$''$" (2 Observations)
- final rms: _not stated_

### Inherited from earlier work

- Observation settings and data reduction processes  
  > "The observation settings and the data reduction processes are described in TFH19." (2 Observations) [from Tokuda et al. 2019 (cite: Tokuda19), TFH19]
- Moment-masked cube method  
  > "We made moment-masked cube data (cite: Dame11; Nishimura15) to suppress the noise effect in the velocity analyses." (2 Observations) [from (cite: Dame11; Nishimura15)]
- Mean molecular weight  
  > "using the mean molecular weight, $\mu$, of (cite: Kauffmann08)" (3.1 13CO Filaments) [from (cite: Kauffmann08)]

### Not stated but needed to reproduce (our reading)

- Calibrators, CASA version and pipeline details (deferred to TFH19)
- Frequency setup, rest frequencies and channel widths
- Line-free channels and continuum subtraction method
- Image size, cell size, clean mask and iteration limits
- Smoothing parameters for the moment-mask
- DisPerSE parameters beyond persistence 20 K (smoothing, cut levels), and radial profile procedure
- Details of the Tex derivation and 13CO column density formulas
- Which channels were used for outflow mass and the dust-continuum boundary details

## Analysis recipe

1. **Image the calibrated data**: tclean with Briggs weighting, no self-calibration  
  > "We did not apply the self-calibration process." (2 Observations)
   - software: CASA
   - parameter: robust = 0.5; threshold ~1 sigma  
  > "using the Briggs weighting with a robust parameter of 0.5" (2 Observations)
   - fitting: _not stated_
   - validation: Compared with Cycle 1 data; fluxes ~20% lower, no significant missing flux  
  > "There is no significant missing flux in the present data set compared to our Cycle 1 observations (Paper I)." (2 Observations)
2. **Identify filaments and measure widths**: DisPerSE on 13CO cube with persistence 20 K; aspect ratio >3:1; Gaussian fits to normalized radial profiles  
  > "We defined structures with an aspect ratio $>$3:1 as the filaments after the measurements of the width (see below) and length." (3.1 13CO Filaments)
   - software: DisPerSE
   - parameter: persistence = 20 K in 13CO brightness temperature  
  > "of 20 K in brightness temperature of $^{13}$CO ($J$ = 2–1)" (3.1 13CO Filaments)
   - fitting: Gaussian fit to radial profile  
  > "we performed Gaussian fits to the normalized radial intensity profile to the filament along the identified skeleton" (3.1 13CO Filaments)
   - validation: Width not an artifact of averaging profiles  
  > "the derived width is not an effect of the averaging of the radial profile across all the identified filaments" (3.1 13CO Filaments)
3. **Column density, mass and line mass of filaments**: LTE; Tex from optically thick 12CO, 13CO optical depth, N(H2) from abundance; Mline = Sigma0 x Wfil  
  > "We obtained the excitation temperature ($T_{\rm ex}$) map from the $^{12}$CO data assuming that the line is optically thick." (3.1 13CO Filaments)
   - assumption: 13CO/H2 = 3.1e-7 (12CO/H2 = 1.6e-5, 12CO/13CO = 50)  
  > "We adopted a $^{13}$CO/H$_2$ abundance ratio of 3.1 $\times$ 10$^{-7}$" (3.1 13CO Filaments)
   - fitting: _not stated_
   - validation: Compared with Galactic filaments Vela C and NGC 6334  
  > "This is consistent with filaments found in the Galactic high-mass star-forming regions" (3.1 13CO Filaments)
4. **Velocity gradient of filament system**: Gaussian centroid per bin in PV diagram, linear least-squares fit over X = -1.8 to 1.0 pc  
  > "then the velocity gradient was derived by the least-squares fitting with a linear function within the X-range of -1.8 to 1.0 pc" (3.1 13CO Filaments)
   - fitting: linear least squares  
  > "the velocity gradient was derived by the least-squares fitting with a linear function" (3.1 13CO Filaments)
   - validation: _not stated_
5. **Pillar properties**: Pillars defined by eye; Gaussian fit to averaged perpendicular column density profile; average density = N_ave/width  
  > "We derived the width (FWHM) of the pillars by Gaussian fitting to the averaged column density profile perpendicular to the white lines" (3.2 CO Pillars)
   - fitting: Gaussian  
  > "We derived the width (FWHM) of the pillars by Gaussian fitting to the averaged column density profile perpendicular to the white lines in Figure" (Results: CO Pillars around the Papillon Nebula)
   - validation: Compared with Eagle Nebula pillars  
  > "In this section, we compare our study with the early results for the Eagle Nebula in M16, the most famous $``$pillars of creation$"$ in the Galaxy" (Discussions: Comparison with Galactic Pillars of creation)
6. **Core masses and outflow parameters**: Core mass from 1.3 mm dust continuum above 30% of peak; outflow wings via 2 sigma limits on smoothed spectra; F_out = M_out V_out / t_d  
  > "We roughly estimated the mechanical forces of the outflow lobes ($F_{\rm out}$) using the following equation: $F_{\rm out}$ = $M_{\rm out}V_{\rm out}$/$t_{\rm d}$ (cite: Beuther02)" (3.3 Protostellar sources)
   - parameter: smoothing kernel 9 ch (=1.8 km/s); outflow inclination 30-70 deg  
  > "with a smoothing kernel of 9 ch (=1.8 km s$^{-1}$)" (3.3 Protostellar sources)
   - assumption: kappa_1.3mm = 1 cm2/g; dust-to-gas 3.0e-3; Tdust = 20 K  
  > "a dust-to-gas ratio of 3.0 $\times$ 10$^{-3}$ (cite: Herrera13; Gordon14) and a uniform dust temperature of 20 K" (3.3 Protostellar sources)
   - fitting: _not stated_
   - validation: Compared with Galactic high-mass protostars and N159W-South  
  > "consistent with those of Galactic high-mass protostars (cite: Beuther02) and the N159W-South region (TFH19)" (3.3 Protostellar sources)

## Software

- **CASA** : tclean imaging  
  > "we used $``$tclean$"$, which is implemented in the Common Astronomy Software Application package (cite: McMullin07)" (2 Observations)
- **DisPerSE** : Filament identification in 13CO cube  
  > "we applied the DisPerSE algorithm (cite: Sousbie11)" (3.1 13CO Filaments)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Typical filament FWHM width | ~0.1 | std 0.08 pc | pc | 2 | has a remarkable peak at $\sim$0.1 pc with the standard deviation of 0.08 pc |
| Number of filaments identified | ~50 | not stated | dimensionless | 2 | In total, we identified $\sim$50 filaments |
| Velocity gradient | ~1.5 | not stated | km/s/pc | 4 | The velocity gradient is $\sim$1.5 km s$^{-1}$ pc$^{-1}$ |
| Filament line mass | ~(1–7)e2 | not stated | Msun/pc | 3 | the resultant line masses ($M_{\rm line}$) are calculated to be $\sim$(1–7) $\times$ 10$^2$ $M_{\odot}$ pc$^{-1}$ |
| Cumulated filament mass | ~1e4 | not stated | Msun | 3 | is $\sim$1 $\times$ 10$^4$ $M_{\odot}$ |
| Virial line mass | ~1.4e2 | not stated | Msun/pc | 3 | is calculated to be $\sim$1.4 $\times$ 10$^2$ $M_{\odot}$ pc$^{-1}$ |
| Pillar average column density | (0.9–3.0)e23 | not stated | cm-2 | 5 | The averaged column densities of the CO pillars are (0.9–3.0) $\times$ 10$^{23}$ cm$^{-2}$. |
| Pillar width | ~0.1–0.2 | not stated | pc | 5 | The resultant width of the pillars is $\sim$0.1–0.2 pc |
| MMS-1/MMS-2 envelope mass | ~2e2 | not stated | Msun | 6 | $\sim$1 $\times$ 10$^{24}$ cm$^{-2}$, and $\sim$2 $\times$ 10$^2$ $M_{\odot}$, respectively |
| Outflow force | ~1e-3–1e-2 | not stated | Msun km/s/yr | 6 | The estimated $F_{\rm out}$ is $\sim$10$^{-3}$–10$^{-2}$ $M_{\odot}$ km s$^{-1}$ yr$^{-1}$ |
| Outflow dynamical time | <1e4 | not stated | yr | 6 | is roughly estimated to be $<$10$^{4}$ yr from a ratio of 0.1 pc/20 km s$^{-1}$ |

## Qualitative findings

- Filaments show hub-filament structure toward the Papillon Nebula, with pillar-like CO features  
  > "The filaments (more than ten in number) show an outstanding hub-filament structure emanating from the nebular center toward the north." (abstract)

## Claim tuples

- H: Are there narrow, high line-mass filaments in the LMC? | E: DisPerSE on 13CO cube and radial profile fits | R: width ~0.1 pc, line mass (1-7)e2 Msun/pc | F: Filaments are similar to Galactic ones and gravitationally unstable | **supported**
- H: Do embedded protostars drive outflows along filaments? | E: 12CO wings towards 1.3 mm continuum peaks | R: Two outflows, dynamical time <1e4 yr | F: Two very young high-mass protostars | **supported**
- H: Are CO pillars forming early around the Nebula? | E: Comparison of pillar column densities with M16 | R: Column density an order of magnitude higher than Eagle pillars | F: Early stage of pillar formation, Rayleigh-Taylor excluded | **partially**
- H: Did a cloud-cloud collision trigger the filament and star formation? | E: Compare morphology and kinematics with HI flow and MHD simulations | R: Consistent with Inoue18 simulations and HI flow scenario | F: Collision triggered formation within ~2 Myr | **partially**

## Reasoning

- Why this data: Higher resolution needed to resolve filaments missed by Cycle 1 data  
  > "we present new ALMA Cycle 4 observations toward the N159E-Papillon region with a factor of three higher angular resolution than the previous study." (Introduction)
- Why this method: _not stated_
- Alternative: Filamentary cloud collision model of Paper I deemed inappropriate; Rayleigh-Taylor instability excluded for pillars  
  > "We thus exclude the Rayleigh-Taylor instability as a candidate mechanism to form the CO pillars in the Papillon Nebula." (4.2 Comparison with Galactic Pillars)
- How they decided it was enough: _not stated_
- Limitation (authors): Available HI data (~1') cannot resolve relation to molecular filaments  
  > "the currently available H$\;$i data with an angular resolution of $\sim$1$'$ (cite: Kim03) are not high enough to distinguish the relation" (4.1 Filament/Protostar formation)
- Caveat (inferred, ours): Collision evidence is indirect (morphology and a velocity gradient), with no direct test of alternative origins
- Caveat (inferred, ours): Cycle 4 fluxes ~20% below Cycle 1 with no explanation
- Caveat (inferred, ours): Single-temperature and fixed-abundance assumptions give uncertain masses with no error budget
- Caveat (inferred, ours): Outflow properties assume inclination and Xco from the Galaxy-like conversion

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: Data from ALMA projects 2016.1.01173.S and 2012.1.00554.S  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2012.1.00554.S, and #2016.1.01173.S." (Acknowledgments)
- Missing: Calibration and observing details (in TFH19)
- Missing: Full DisPerSE and imaging parameters
- Missing: Tex and column density formulas and masks
- Data volume (inferred): ~100-300 GB raw for Cycle 4 Band 6 project
- Score (inferred): 3/5, Data are archival and the approach is clear, but processing details are deferred to TFH19 and many parameters are missing.
- Rediscovery candidate: no, Calibration and analysis settings are not given in sufficient detail.

## Links

- Method: Sousbie 2011 (cite: Sousbie11) (DisPerSE filament identification)
- Companion: Tokuda et al. 2019 (cite: Tokuda19) (Observation settings, reduction, and N159W-South results)
- Companion: Saigo et al. 2017 (cite: Saigo17) (Paper I, ALMA Cycle 1 observations of N159E)
- Related: Herschel Gould Belt survey
- Related: N159 multi-object ALMA survey

## Checks

```json
{
 "quotes": 70,
 "quotes_ok": 70,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 11,
 "numeric_problems": 0,
 "fill": {
  "facts": 77,
  "stated": 46,
  "rate": 0.597
 },
 "evidence_ok": true
}
```
