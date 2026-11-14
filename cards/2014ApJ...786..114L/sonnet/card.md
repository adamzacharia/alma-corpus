# ALMA Results of the Pseudodisk, Rotating Disk, and Jet in the Continuum and HCO<SUP>+</SUP> in the Protostellar System HH 212

`2014ApJ...786..114L` | The Astrophysical Journal 2014 | first author: Lee, Chin-Fei | arXiv: 1403.5853 | DOI: 10.1088/0004-637X/786/2/114

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, protoplanetary_disks
- Question: Does the Class 0 protostar HH 212 host a rotationally supported disk inside an infalling flattened envelope (pseudodisk), and what are the properties of the HCO+ jet?  
  > "In order to confirm the presence of a RSD in this system, we have mapped this system in 350 GHz continuum and HCO$^+$ J=4-3 using Atacama Large Millimeter/Submillimeter Array (ALMA) at higher resolution and sensitivity." (Introduction)
- Target **HH 212 (IRAS 05413-0104)**: coordinates RA(J2000) 05h43m51.4107s, Dec -01d02m53.167s (continuum peak)  
  > "This system is deeply embedded in a compact molecular cloud core in the L1630 cloud of Orion at a distance of 400 pc." (Introduction); "The continuum peak is at $\alpha_{(2000)}=05^\mathrm{h} 43^\mathrm{m} 51^\mathrm{s}_{^\textrm{.}} 4107$" (3.1 350 GHz Continuum); z/distance 400 pc  
  > "This system is deeply embedded in a compact molecular cloud core in the L1630 cloud of Orion at a distance of 400 pc." (Introduction); "The continuum peak is at $\alpha_{(2000)}=05^\mathrm{h} 43^\mathrm{m} 51^\mathrm{s}_{^\textrm{.}} 4107$" (3.1 350 GHz Continuum); distance from _not stated_

## Data provenance

- ALMA projects: 2011.0.00647.S
- bands: Band 7 (~350 GHz)  
  > "Two scheduling blocks (SBs) were obtained in Band 7 at $\sim$ 350 GHz with 21-24 antennas" (2 Observations)
- frequencies and spectral setup: 4 spectral windows (CO 3-2, SiO 8-7, HCO+ 4-3, continuum); ~0.2 km/s channels for the line windows; 9-pointing mosaic  
  > "The correlator was set up to have 4 spectral windows, with one for CO J=3-2, one for SiO J=8-7, one for HCO$^+$ J=4-3, and one for the continuum." (2 Observations); "A 9-pointing mosaic was used to observe the jet in this system within $\sim$ $35''$ from the central source." (2 Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: Cycle 0 extended configuration, 21-24 antennas  
  > "with 21-24 antennas in the (Cycle 0) extended configuration, with projected baselines ranging from $\sim$ 20 to 360 m." (2 Observations)
- baselines: ~20 to 360 m projected  
  > "with projected baselines ranging from $\sim$ 20 to 360 m." (2 Observations)
- angular resolution: 0.50x0.45 arcsec (continuum), 0.48x0.45 arcsec (HCO+), super-uniform weighting  
  > "With super-uniform weighting, the synthesized beam has a size of $0^{\prime\prime}_{^\textrm{.}}50$$\times$$0^{\prime\prime}_{^\textrm{.}}45$ at a position angle (P.A.) of 52$^\circ$ in continuum" (2 Observations)
- max recoverable scale: _not stated_
- sensitivity: 0.61 mJy/beam continuum; ~10 mJy/beam HCO+ channel maps  
  > "The rms noise level is 0.61 mJy beam$^{-1}$ (i.e., 27 mK) for the continuum, and $\sim$ 10 mJy beam$^{-1}$ (i.e., 0.45 K) for the HCO$^+$ channel maps." (2 Observations)
- time on source: _not stated_
- observing dates: 2012 December 1, Early Science Cycle 0  
  > "Observations of the HH 212 protostellar system were carried out with ALMA on 2012 December 1 during the Early Science Cycle 0 phase." (2 Observations)
- pi or archival as stated: Data from proposal 2011.0.00647.S made available to the author via his proposal 2011.0.00122.S, which duplicated it  
  > "These data were made available to Chin-Fei Lee, as part of his ALMA proposal 2011.0.00122.S (PI: Chin-Fei Lee), which requested observations duplicating those of proposal 2011.0.00647.S." (Acknowledgments)
- Line: HCO+ J=4-3 (not stated)
- Other facility **SMA**: Earlier continuum, HCO+, C18O, 13CO and SO observations used for comparison and model inputs  
  > "Previous observations in C$^{18}$O ($J=2-1$) and $^{13}$CO ($J=2-1$) with the Submillimeter Array (SMA) at $\sim$ $2^{\prime\prime}_{^\textrm{.}}5$ resolutions showed a flattened envelope around the central source" (Introduction)
- External data: Envelope temperature, density, infall and rotation power-law profiles from C18O modeling  
  > "the temperature, number density of molecular hydrogen, infall velocity, and rotation velocity are assumed to follow those obtained from modeling the outer part of the flattened envelope in C$^{18}$O" (4 Model of the envelope and disk) [from (cite: Lee2006)]
- External data: Dust opacity law kappa=0.1 (nu/1e12 Hz)^beta cm2/g with beta=1 from SED fit  
  > "we assume a dust mass opacity law given by (cite: Beckwith1990)" (4 Model of the envelope and disk); "with $\beta= 1$, as found in (cite: Lee2007) from fitting the SED." (4 Model of the envelope and disk) [from (cite: Beckwith1990); (cite: Lee2007)]
- External data: Jet velocity ~150 km/s and jet diameter ~0.2 arcsec  
  > "where $v_j \sim 150$ km s$^{-1}$ is the jet velocity (cite: Lee2008)" (6.3 HCO+ Jet and Abundance); "The jet was found to have a diameter of $d_j\sim$ $0^{\prime\prime}_{^\textrm{.}}2$ (80 AU) (cite: Cabrit2007; Lee2008)" (6.3 HCO+ Jet and Abundance) [from (cite: Lee2008); (cite: Cabrit2007)]
- External data: Outflow cavity shapes from CO outflow shell fits  
  > "Two outflow cavities (obtained by fitting the CO outflows, Lee et al. in prep) are also included" (4 Model of the envelope and disk) [from Lee et al. in prep]

## Processing

### Calibration

- pipeline or manual: Calibrated with CASA; details not given  
  > "The data were calibrated with the CASA package" (2 Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Callisto and Ganymede; passband J0538-440 and J0607-085; gain J0607-085  
  > "Quasar J0607-085 as a gain calibrator, and Callisto and Ganymede as flux calibrators." (2 Observations)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: super-uniform weighting  
  > "With super-uniform weighting, the synthesized beam has a size of" (2 Observations)
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
- final beam: 0.50x0.45 arcsec PA 52 deg (continuum); 0.48x0.45 arcsec PA 26 deg (HCO+)  
  > "and $0^{\prime\prime}_{^\textrm{.}}48$$\times$$0^{\prime\prime}_{^\textrm{.}}45$ at a P.A. of 26$^\circ$ in HCO$^+$." (2 Observations)
- final rms: 0.61 mJy/beam continuum; ~10 mJy/beam HCO+  
  > "The rms noise level is 0.61 mJy beam$^{-1}$ (i.e., 27 mK) for the continuum" (2 Observations)

### Inherited from earlier work

- Systemic velocity 1.7+-0.1 km/s LSR  
  > "The systemic velocity in this region is assumed to be $V_\textrm{\scriptsize sys}= 1.7\pm0.1$ km s$^{-1}$ LSR, as in (cite: Lee2007)." (2 Observations) [from (cite: Lee2007)]
- Two-Gaussian uv-plane fit of the continuum (extended envelope plus compact disk)  
  > "It can be fitted with two circular Gaussian components, one extended tracing the flattened envelope and one compact tracing the disk, as seen in (cite: Lee2008)." (3.1 350 GHz Continuum) [from (cite: Lee2008)]
- Model inspired by the HH 111 envelope-to-Keplerian-disk rotation change  
  > "This model is inspired by the previous work on the Class I system HH 111 in Orion in the later stage of star formation (cite: Lee2010)." (6.1 Comparing to Class 0 and I disks) [from (cite: Lee2010)]

### Not stated but needed to reproduce (our reading)

- CASA version and details of the calibration (bandpass, gain, flux scale, self-calibration)
- Line-free channels and the continuum subtraction method for HCO+
- Cleaning parameters (deconvolver, mask, threshold, cell and image size, robust beyond 'super-uniform')
- Radiative transfer code, grid, and the fitting procedure and merit function for the 7 free parameters
- HCO+ rest frequency and molecular data (collisional rates, partition function) used
- Parameters of the outflow cavity shapes (paper in prep)
- Parameters of the Gaussian used to mimic the extended envelope absorption
- uv-plane fit details of the two-Gaussian model

## Analysis recipe

1. **Image continuum and HCO+ and characterize the continuum**: Continuum map, visibility amplitude vs uv-distance fitted with two circular Gaussians; uv>120 klambda data imaged separately to isolate the disk  
  > "The visibility data with $uv$-distance greater than 120 k$\lambda$ trace only the compact component and thus can be used to reveal the disk structure of the compact component." (3.1 350 GHz Continuum)
   - software: CASA
   - fitting: _not stated_
   - validation: Compared with earlier SMA fluxes and sizes  
  > "The extended component has a Gaussian deconvolved size of $\sim$ $2''$ and a flux of $\sim$ 260 mJy, as found before." (3.1 350 GHz Continuum)
2. **Analyze HCO+ kinematics (spectra, channel maps, PV diagrams)**: Velocity split into 3 ranges; spectrum, PV diagrams along the equator and the jet axis compared with infall and Keplerian signatures  
  > "we divide the velocity into 3 ranges: $|V_\textrm{\scriptsize off}| \leq 1$ km s$^{-1}$, $1\leq |V_\textrm{\scriptsize off}| \leq 2$ km s$^{-1}$, and $2\leq
|V_\textrm{\scriptsize off}| \leq 3$ km s$^{-1}$." (3.2.1 Flattened Envelope, Disk, and Outflow)
   - fitting: _not stated_
   - validation: _not stated_
3. **Spatio-kinematic radiative transfer model of envelope and disk**: Model with a flattened envelope (power laws) and a disk (Keplerian) with a density jump m at the interface, LTE radiative transfer, channel maps resampled with the observed uv coverage; fit to continuum and HCO+ simultaneously  
  > "We first calculate the channel maps with radiative transfer and next map them with the observed $uv$-coverage and velocity resolutions." (4 Model of the envelope and disk)
   - parameter: 7 free parameters: T0, n0, vr0, vphi0, m, q, x(HCO+)  
  > "In our model, there are 7 free parameters, with their best-fit values of $T_\textrm{\scriptsize 0}^e \sim 45$ K" (4 Model of the envelope and disk)
   - parameter: Disk outer radius 0.3 arcsec (120 AU), half thickness 0.1 arcsec, inner radius 0.01 arcsec; envelope outer radius 5 arcsec  
  > "It is assumed to be a flat disk with an outer radius of $r_D=$$0^{\prime\prime}_{^\textrm{.}}3$ (120 AU) and a constant half thickness of $H=$$0^{\prime\prime}_{^\textrm{.}}1$ (40 AU)" (4 Model of the envelope and disk)
   - assumption: Dust and gas same temperature; LTE; kappa from Beckwith1990 with beta=1; thermal line width only; free-fall infall and constant specific angular momentum in the envelope  
  > "For simplicity, dust and HCO$^+$ gas are assumed to have the same temperature." (4 Model of the envelope and disk); "The line width of the HCO$^+$ emission is assumed to be given by the thermal line width only." (4 Model of the envelope and disk)
   - fitting: Best-fit by matching the continuum map, HCO+ channel maps, spectrum and PV diagram; no formal sampler stated  
  > "The best-fit parameters are obtained by matching the continuum map, HCO$^+$ channel maps, spectrum, and PV diagram in our model to those in the observations" (4 Model of the envelope and disk)
   - validation: Compared with model maps; extended envelope effect mimicked by a Gaussian subtracted from the model spectrum  
  > "After we subtract this Gaussian component from our model spectrum (red spectrum), we can obtain a spectrum (green spectrum) that matches the observed spectrum toward the center at low velocity" (4 Model of the envelope and disk)
4. **Consistency checks and derived masses**: Keplerian radius, isothermal shock Mach number vs density jump, stellar and disk masses, accretion rate and luminosity  
  > "Therefore, $m\sim 8.0$, the same as that obtained from our model, and thus the jump condition is self-consistent in our model." (4.1 Consistency Checks)
   - assumption: R* ~ 2 Rsun for accretion luminosity  
  > "Assuming $R_\ast \sim 2 R_\odot$, then $L_\textrm{acc} \sim 14$ L$_\odot$" (4.1 Consistency Checks)
   - fitting: _not stated_
   - validation: Disk mass checked against disk continuum flux assuming optically thin emission  
  > "Assuming that the observed disk continuum emission is optically thin, this mass requires the disk to have a representative temperature of $\sim$ 91 K." (4.1 Consistency Checks)
5. **HCO+ jet abundance and mass-loss rate**: Flux of |Voff|>=2 km/s scaled by 1.4, optically thin column density at Tex=50 K, mass-loss rate set to 20% of accretion rate to derive abundance  
  > "The excitation temperature of the HCO$^+$ emission of the jet is assumed to be 50 K, like that of the CO emission of the jet" (6.3 HCO+ Jet and Abundance)
   - assumption: Jet velocity 150 km/s; mass-loss = 20% of accretion rate  
  > "In the current MHD jet launching models, the mass-loss rate can have a mean of 20% of the accretion rate" (6.3 HCO+ Jet and Abundance)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : Data calibration  
  > "The data were calibrated with the CASA package" (2 Observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Continuum extended component flux | ~260 | not stated | mJy | 1 | a flux of $\sim$ 260 mJy, as found before |
| Compact component flux | ~200 | not stated | mJy | 1 | it has a flux of $\sim$ 200 mJy, higher than that found before |
| Total continuum flux within 2 arcsec | 460 | 43 | mJy | 1 | The total flux integrated over a region within $2^{\prime\prime}_{^\textrm{.}}0$ from the source is 460$\pm43$ mJy |
| Density jump m | ~8.0 | not stated | dimensionless | 3 | $m \sim 8.0$, $q \sim 0.6$, and $x_{\textrm{\scriptsize HCO}^{+}}$ $\sim 10^{-9}$ |
| Envelope reference temperature T0 at 1 arcsec | ~45 | not stated | K | 3 | $T_\textrm{\scriptsize 0}^e \sim 45$ K, $n_\textrm{\scriptsize 0}^e \sim 5\times10^6$ cm$^{-3}$ |
| Infall velocity v_r0 at 1 arcsec | ~0.9 | not stated | km/s | 3 | $v_{r\textrm{\scriptsize 0}}^e \sim 0.9$ km s$^{-1}$, $v_{\phi\textrm{\scriptsize 0}}^e \sim 0.35$ km s$^{-1}$ |
| Central stellar mass | ~0.18 | not stated | Msun | 4 | the mass of the central star is found to be $\sim$ 0.18 $M_\odot$ |
| Disk mass | ~0.014 | not stated | Msun | 4 | M_D = 1.4m_{\textrm{\scriptsize H}_2}
\int^{r_D} 2 \pi r (2 H) n^D dr \sim 0.014 \; M_\odot |
| Flattened envelope mass | ~0.10 | not stated | Msun | 4 | \sim 0.10 \; M_\odot |
| Accretion rate | ~5.0e-6 | not stated | Msun/yr | 4 | \sim
5.0\times 10^{-6} \; M_\odot{}\; \textrm{yr}^{-1} |
| Accretion luminosity | ~14 | not stated | Lsun | 4 | then $L_\textrm{acc} \sim 14$ L$_\odot$, comparable to the bolometric luminosity |
| Keplerian radius | ~0.3 | not stated | arcsec (120 AU) | 4 | the Keplerian radius is found to be $\sim$ $0^{\prime\prime}_{^\textrm{.}}3$ |
| Jet HCO+ abundance | ~1e-7 | not stated | relative to H2 | 5 | we have $x \sim 1\times 10^{-7}$, higher than that derived in the flattened envelope by a factor of $\sim$ 100. |
| Jet mean density | ~4.2e5 | not stated | cm^-3 | 5 | the mean density in the jet is $\sim 4.2 \times 10^5$ cm$^{-3}$ |

## Qualitative findings

- The flattened envelope is infalling with small rotation and is identified as a pseudodisk; an extended infalling envelope flowing roughly parallel to the jet axis is needed to explain the missing low-redshifted HCO+ emission.  
  > "an extended infalling envelope is required, with its material flowing roughly parallel to the jet axis toward the pseudodisk." (abstract)

## Claim tuples

- H: The flattened envelope is a pseudodisk with infall and small rotation. | E: HCO+ spectrum, channel maps and PV diagrams | R: Blue-brighter double peak with redshifted dip and triangular PV structure | F: Envelope is infalling and spiraling; identified as a pseudodisk | **supported**
- H: A rotationally supported disk exists at the center. | E: Continuum CLEAN map and HCO+ kinematics at high velocity, plus modeling | R: Compact disk radius ~120 AU with Keplerian-like rotation; Keplerian radius equals model disk radius | F: Disk is rotating and can be rotationally supported, though it is unresolved and Keplerian rotation needs confirmation | **partially**
- H: A density jump exists at the envelope-disk interface. | E: Simultaneous continuum and HCO+ modeling | R: m ~ 8, consistent with an isothermal shock with Mach number ~2.82 | F: A density jump is required to match disk continuum emission | **supported**
- H: The HCO+ jet traces internal shocks. | E: Jet map and PV diagram for |Voff|>=2 km/s, abundance estimate | R: Peaks upstream of SiO, velocity range ~14 km/s, abundance ~1e-7 | F: HCO+ traces internal shocks in the jet with enhanced abundance | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Disk is not well resolved, so its radius is an upper limit and the temperature index is rough; model is simple and symmetric and excludes outflow, jet and extended envelope.  
  > "The disk is not well resolved in our observations, especially in the minor axis." (4 Model of the envelope and disk); "Our model here is simple and can be considered as a first step to disentangle the envelope and disk in our system." (4 Model of the envelope and disk)
- Caveat (inferred, ours): Model fit is by eye with no uncertainties or parameter degeneracies quantified
- Caveat (inferred, ours): Disk is unresolved, so the Keplerian and density-jump conclusions rest on model assumptions
- Caveat (inferred, ours): Extended envelope treated ad hoc with a Gaussian
- Caveat (inferred, ours): Fixed assumptions (beta=1, Tex=50 K, 20% mass-loss fraction) drive the abundance

## Reproducibility

- Data public (paper): Data from project 2011.0.00647.S made available to the author via a duplicate proposal  
  > "These data were made available to Chin-Fei Lee, as part of his ALMA proposal 2011.0.00122.S (PI: Chin-Fei Lee), which requested observations duplicating those of proposal 2011.0.00647.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Radiative transfer model code and fitting procedure
- Missing: Calibration scripts and CASA version
- Missing: Imaging parameters
- Missing: Outflow cavity model (paper in prep)
- Data volume (inferred): ~20-50 GB (two Cycle 0 Band 7 scheduling blocks, 9-pointing mosaic)
- Score (inferred): 4/5, Public Cycle 0 data and well-described model equations, but the radiative transfer code, fitting and imaging details are missing.
- Rediscovery candidate: no, Main results come from a custom model fit with unspecified code and by-eye matching, so exact numbers are hard to redo.

## Links

- Method: (cite: Lee2010) (HH 111 envelope-disk model that inspired this model)
- Method: (cite: Lee2006) (C18O envelope model parameters adopted)
- Companion: (cite: Lee2007) (Earlier SMA study of HH 212; systemic velocity and SED fit)
- Companion: (cite: Lee2008) (Earlier SMA continuum and SiO study of the disk and jet)
- Related: ALMA proposal 2011.0.00122.S

## Checks

```json
{
 "quotes": 70,
 "quotes_ok": 70,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [
  "2011.0.00122.S"
 ],
 "numeric_results": 14,
 "numeric_problems": 0,
 "fill": {
  "facts": 74,
  "stated": 42,
  "rate": 0.568
 },
 "evidence_ok": true
}
```
