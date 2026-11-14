# Magnetic Field Structure of Orion Source I

`2020ApJ...896..157H` | The Astrophysical Journal 2020 | first author: Hirota, Tomoya | arXiv: 2005.13077 | DOI: 10.3847/1538-4357/ab959e

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, astrochemistry
- Question: What is the magnetic field structure in the bipolar outflow of Orion Source I, probed by polarization of SiO maser/thermal emission at 43 and 86 GHz?  
  > "We observed polarization of the SiO rotational transitions from Orion Source I (SrcI) to probe the magnetic field in bipolar outflows from this high mass protostar." (abstract)
- Target **Orion Source I (SrcI)**: coordinates RA(J2000)=05h35m14.5129s, Dec(J2000)=-05d22m30.576s (tracking center)  
  > "The tracking center position of SrcI was RA(J2000)=$05^{\rm h}35^{\rm m}14.5129s$ and Dec(J2000)=$-05\ensuremath{^\circ}22\ensuremath{'}30.576\ensuremath{''}$." (2.1 ALMA); z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2017.1.00497.S
- bands: ALMA Band 3 (86 GHz SiO lines; continuum at 96-99 GHz); VLA Q-band (43 GHz)  
  > "We used the ALMA band 3 receiver to detect 86 GHz SiO lines and their isotopologues listed in Table [1](#tab-line)." (2.1 ALMA)
- frequencies and spectral setup: 28SiO v=0,1 J=2-1: 58.6 MHz windows at 122 kHz resolution; other lines 244 kHz; two 1875 MHz continuum windows at 96-99 GHz  
  > "we set up spectral windows with total bandwidths of 58.6 MHz and spectral resolutions of 122 kHz." (2.1 ALMA); "two broad spectral windows were configured at 96-99 GHz for continuum emission with total bandwidths of 1875 MHz each." (2.1 ALMA)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: C43-10 with 51 antennas  
  > "The array was in the C43-10 configuration with 51 antennas, providing the longest baseline length of 16 km available with ALMA." (2.1 ALMA)
- baselines: 41 m to 16 km  
  > "The shortest baseline length of 41 m provides a maximum recoverable scale of $\sim$1.0$''$ at band 3." (2.1 ALMA)
- angular resolution: 49 mas x 47 mas (96 GHz continuum); ~55 mas for lines  
  > "The synthesized beam size was 49 mas$\times$47 mas with a position angle of -35 degrees for the 96 GHz continuum image." (2.1 ALMA)
- max recoverable scale: ~1.0 arcsec at band 3  
  > "The shortest baseline length of 41 m provides a maximum recoverable scale of $\sim$1.0$''$ at band 3." (2.1 ALMA)
- sensitivity: 96 GHz continuum polarization rms 0.012 mJy/beam  
  > "rms of Pol. Intensity | 0.014 mJy beam$^{-1}$ | 0.012 mJy beam$^{-1}$" (Table 2)
- time on source: 3.5 hours total, 2.5 hours on source  
  > "The total time of observations was 3.5 hours for both days, and total on-source time was 2.5 hours." (2.1 ALMA)
- observing dates: 2017 October 12 and 17  
  > "Observations with ALMA were carried out on 2017 October 12 and 17 in the full polarization mode consisting of 2 execution blocks (EBs) for each day." (2.1 ALMA)
- pi or archival as stated: _not stated_
- Line: 28SiO v=0 J=2-1 (86846.9850 MHz)
- Line: 28SiO v=1 J=2-1 (86243.4277 MHz)
- Line: 29SiO v=0 J=2-1 (85759.1940 MHz)
- Line: 28SiO v=2 J=2-1 (85640.4531 MHz)
- Line: 29SiO v=1 J=2-1 (85166.9579 MHz)
- Line: 30SiO v=0 J=2-1 (84746.1663 MHz)
- Other facility **VLA**: Q-band 43 GHz full-polarization A-configuration SiO J=1-0 data on 2018 March 6  
  > "Observations with VLA were made on 2018 March 6 with the most extended A-configuration in the full-polarization observing mode." (2.2 VLA)
- External data: 3C286 polarization (13.2%, 36 deg at 43.50 GHz) used for VLA polarization calibration  
  > "A fractional polarization of 13.2% and polarization angle of 36 degrees were employed for 3C286 at the frequency of 43.50 GHz (cite: Perley2013)." (2.2 VLA) [from (cite: Perley2013)]
- External data: Zeeman Lande g-factor of SiO, -0.15  
  > "where $g$ is the Landé g-factor of the SiO line, $-0.15$ (cite: Davis1974)" (4.1 Physical conditions for polarized masers) [from (cite: Davis1974)]
- External data: Einstein A coefficients 3.0e-6 and 2.9e-5 s-1 for J=1-0 and 2-1  
  > "3.0$\times10^{-6}$ s$^{-1}$ and 2.9$\times10^{-5}$ s$^{-1}$ for the $^{28}$SiO $v$=0 $J$=1-0 and 2-1 lines, respectively (cite: Barton2013)" (4.1 Physical conditions for polarized masers) [from (cite: Barton2013)]

## Processing

### Calibration

- pipeline or manual: ALMA: EA-ARC pipeline script via CASA; VLA: NRAO pipeline for Stokes I continuum only, then manual polarization calibration in CASA  
  > "Calibration used the pipeline script provided by East-Asian ALMA Regional Center (EA-ARC) through the CASA (Common Astronomy Software Applications) package." (2.1 ALMA); "Thus, we conducted polarization calibration for both continuum and spectral line data using the CASA package." (2.2 VLA)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0423-0120 (ALMA first EBs); J0522-3627 flux used as reference for second EBs; 3C286 for VLA  
  > "The absolute flux densities were calibrated using J0423-0120 for the first EBs in both days." (2.1 ALMA)
- flux scale uncertainty: J0522-3627 measured fluxes differ by ~5% from catalog, within ALMA band 3 flux accuracy  
  > "These values were different by 5% from the cataloged value of 5.18$\pm$0.31 Jy and 5.63$\pm$0.20 Jy probably because of its variability" (2.1 ALMA)
- self calibration: ALMA: none (no significant improvement, ~4%); VLA: self-cal on a single 28SiO v=1 J=1-0 channel, continuum increased 20%  
  > "We did not apply self-calibration to the ALMA data because it provided no significant improvement" (2.1 ALMA); "Self-calibration was made using a single channel of the strong and compact $^{28}$SiO $v$=1 $J$=1-0 maser line." (2.2 VLA)

### Imaging

- task: synthesis images made with CASA and Miriad  
  > "synthesis images were made using CASA and Miriad software." (2.1 ALMA)
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: continuum images use only line-free channels (mfs)  
  > "For the continuum emission we used only line-free channels to make mfs (multi-frequency synthesis) images." (2.1 ALMA)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: J=1-0 and J=2-1 images convolved to 0.1 arcsec for comparison  
  > "both images were convolved to 0.1$''$ resolution." (3.2.2 Linear polarization)
- final beam: 49x47 mas PA -35 deg (continuum); ~55 mas lines  
  > "In the case of spectral lines, typical beam sizes are slightly larger, $\sim$55 mas with an almost circular beam shape." (2.1 ALMA)
- final rms: _not stated_

### Inherited from earlier work

- Stimulated emission rate parameters (B=1 mG, mu=3.1 D, TB) taken from BIMA analysis  
  > "We estimated the stimulated emission rate $R$ for the polarized masers listed in Table [1](#tab-line) using the same parameters employed by (cite: Plambeck2003)" (4.1 Physical conditions for polarized masers) [from (cite: Plambeck2003)]
- Simpler DCF strategy of subtracting a smoothed position angle map  
  > "Here, however, we adopt the simpler strategy used by (cite: Pattle2017) in which a smoothed position angle map is subtracted from the high resolution map before the dispersion is calculated." (4.2.4 Estimate of the magnetic field strength) [from (cite: Pattle2017)]
- DCF formulation of the plane-of-sky field  
  > "Following the formulation in (cite: Crutcher2004), the plane of sky component of the magnetic field is given by" (4.2.4 Estimate of the magnetic field strength) [from (cite: Crutcher2004)]

### Not stated but needed to reproduce (our reading)

- CASA version used for ALMA and VLA
- tclean parameters (weighting/robust, cell, image size, deconvolver, masking, threshold)
- line-free channels for continuum
- how Stokes V and polarization leakage were calibrated in CASA (tasks, solints)
- how the 5 sigma cutoff and moment velocity ranges were chosen exactly
- pixel-level procedure for the Faraday rotation measure solution
- how Zeeman fits to Stokes V were performed

## Analysis recipe

1. **Image continuum and line cubes in full Stokes**: Synthesis imaging with CASA and Miriad; 0.5 km/s channels for 28SiO v=0,1 and 1.0 km/s others; 2 km/s for display  
  > "Full-Stokes velocity channel maps were first made with the common velocity resolution of 0.5 km s$^{-1}$ for $^{28}$SiO $v$=0 and $v$=1 transitions" (2.1 ALMA)
   - software: CASA, Miriad
   - fitting: _not stated_
   - validation: no self-cal for ALMA since improvement ~4%  
  > "the flux density increased only $\sim$4% )" (2.1 ALMA)
2. **Derive debiased linear polarization and angles**: P=sqrt(Q^2+U^2-sigma^2); line-averaged angles from Q,U over 30 km/s centered at 5 km/s; fractional polarization from P and I  
  > "the linearly polarized intensity images were debiased by subtracting the rms noise over the emission-free channels/regions in the images; $P=\sqrt{Q^{2}+U^{2}-\sigma^{2}}$." (2.1 ALMA)
   - parameter: angle error Delta(PA)=DeltaP/2P; vectors plotted for S/N>=4 (errors <7 deg)  
  > "we plot the vectors with the signal-to-noise ratio of 4 or higher, and hence, the errors in the polarization angle, $\Delta{\rm (PA)}$ are smaller than 7 degrees." (3.2.2 Linear polarization)
   - fitting: _not stated_
   - validation: _not stated_
3. **Constrain Faraday rotation from J=1-0 vs J=2-1 angle differences**: Map position angle differences between lines; convert to RM via theta=lambda^2 RM; compute intrinsic angles  
  > "The maximum position angle difference of $\sim$60 degrees in the SW lobe corresponds to a rotation measure of 3$\times10^{4}$ rad m$^{-2}$." (4.2.2 Faraday rotation)
   - parameter: 1 degree difference corresponds to RM of 460 rad m-2  
  > "a polarization angle difference of 1 degree corresponds to $RM$ of 460 rad m$^{-2}$." (4.2.2 Faraday rotation)
   - assumption: both lines trace the same gas volume  
  > "If both the $J$=1-0 and 2-1 lines originate from the same volume of gas, the different polarization structures could be explained by the propagation effects." (4.2.2 Faraday rotation)
   - fitting: _not stated_
   - validation: searched for correlation with velocity, position, circular polarization; none found  
  > "We searched unsuccessfully for such a correlation." (4.2.3 Foreground absorption or scattering?)
4. **Estimate field strength with DCF method**: Davis-Chandrasekhar-Fermi on 28SiO v=0 J=2-1 angle residuals after subtracting 0.5 arcsec-smoothed angle map  
  > "we convolved the SiO Stokes I, Q, and U images with an 0.5$''$  FWHM Gaussian, generated a low resolution polarization angle map from these data, then subtracted this image from the 0.1$''$  resolution image" (4.2.4 Estimate of the magnetic field strength)
   - parameter: delta phi = 4 deg; Delta V ~ 10 km/s; n(H2)=1e6 cm-3  
  > "Therefore, we adopt a somewhat smaller dispersion $\delta\phi$ = 4$^\circ$" (4.2.4 Estimate of the magnetic field strength)
   - assumption: density 1e6 cm-3 from maser pumping; correction factor 0.5; total field 4B/pi  
  > "we adopt a density of $10^{6}$ cm$^{-3}$ in the $^{28}$SiO $v$=0 $J$=2-1 emission region in order to satisfy the maser pumping model" (4.2.4 Estimate of the magnetic field strength)
   - fitting: _not stated_
   - validation: compared with OH maser and scaling laws with density  
  > "a magnetic field strength $\sim$30 mG is consistent with that estimated from OH maser observations (cite: Cohen2006)" (4.2.4 Estimate of the magnetic field strength)
5. **Test Zeeman interpretation of Stokes V**: Fit V = b dI/dnu to Stokes V spectra at selected positions  
  > "we were able to fit some of the velocity components in the Stokes V spectra to the Zeeman pattern" (4.2.5 Circular Polarization)
   - parameter: g Omega/2pi=230 Hz/G  
  > "The magnitude of the Zeeman splitting, $g \Omega/2\pi$=230 Hz G$^{-1}$" (4.2.5 Circular Polarization)
   - assumption: uniform field for all velocity components  
  > "Assuming uniform magnetic field strengths for all the velocity components" (4.2.5 Circular Polarization)
   - fitting: _not stated_
   - validation: implied fields of ~10 G implausible; opposite signs in J=1-0 and 2-1  
  > "Such large magnetic fields are implausible." (4.2.5 Circular Polarization)

## Software

- **CASA** : calibration and imaging  
  > "Calibration used the pipeline script provided by East-Asian ALMA Regional Center (EA-ARC) through the CASA (Common Astronomy Software Applications) package." (2.1 ALMA)
- **Miriad** : synthesis imaging  
  > "synthesis images were made using CASA and Miriad software." (2.1 ALMA)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| 96 GHz continuum integrated flux density of SrcI | 58 | 6 | mJy | 1 | Integrated Flux$^{a}$ / 10$\pm$1 mJy / 58$\pm$6 mJy |
| DCF plane-of-sky field strength | 23 | not stated | mG | 4 | gives a plane of sky magnetic field strength of 23 mG. |
| Total field strength | ~30 | not stated | mG | 4 | An estimate for the total field strength is $4B_{\rm los}/\pi$ (cite: Crutcher2004), or $\sim$30 mG. |
| Max rotation measure (SW lobe) | 3e4 | not stated | rad m-2 | 3 | The maximum position angle difference of $\sim$60 degrees in the SW lobe corresponds to a rotation measure of 3$\times10^{4}$ rad m$^{-2}$. |
| Fractional linear polarization 28SiO v=0 J=2-1 (average) | ~20-50 | not stated | percent | 2 | the fractional linear polarizations of the $^{28}$SiO $v$=0 $J$=1-0 and 2-1 lines are $\sim$50-70% and $\sim$20-50%, respectively. |
| Polarization angle residual dispersion adopted | 4 | not stated | degrees | 4 | we adopt a somewhat smaller dispersion $\delta\phi$ = 4$^\circ$ |
| Peak 29SiO v=0 J=2-1 brightness temperature | 1.3e6 | not stated | K | 1 | The peak brightness temperature of 1.3$\times$10$^{6}$ K at the LSR velocity of $-1$ km s$^{-1}$ indicates strong maser emission |

## Qualitative findings

- Continuum from SrcI is not significantly polarized at 43 or 96 GHz.  
  > "We did not detect polarization in the continuum emission, with 5$\sigma$ upper limits of 0.07 mJy beam$^{-1}$ at 43 GHz and 0.06 mJy beam$^{-1}$ at 96 GHz." (3.1 Continuum)
- ARS rather than Zeeman likely explains high circular polarization.  
  > "The extremely high circular polarization fractions are most likely due to ARS rather than the Zeeman splitting" (Summary)

## Claim tuples

- H: Is Faraday rotation large between 43 and 86 GHz SiO polarization? | E: Compared J=1-0 and J=2-1 polarization angles | R: Differences up to ~60 deg in SW lobe, RM ~1e4 rad m-2 | F: Upper limit on Faraday rotation ~1e4 rad m-2; rotation of J=2-1 angles typically <10 deg | **supported**
- H: Does the outflow host a strong ordered magnetic field? | E: DCF analysis of 28SiO v=0 J=2-1 polarization | R: ~30 mG | F: Field strong enough to shape the outflow and perhaps cause sub-Keplerian rotation | **supported**
- H: What produces the high circular polarization? | E: Stokes V maps and Zeeman fits | R: up to 60% in J=1-0; Zeeman would need ~10 G fields with inconsistent signs | F: Anisotropic resonant scattering is likely | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Large number of polarization vectors makes DCF feasible  
  > "The large number of polarization vectors measured across the outflow lobes in the $^{28}$SiO $v$=0 $J$=2-1 line makes it feasible to estimate the magnetic field strength" (4.2.4 Estimate of the magnetic field strength)
- Alternative: Zeeman splitting rejected as origin of Stokes V  
  > "We conclude that Zeeman splitting cannot explain the observed circular polarizations." (4.2.5 Circular Polarization)
- How they decided it was enough: _not stated_
- Limitation (authors): ALMA Stokes V calibration not guaranteed in Cycle 5  
  > "We note that circular polarization measurements were not assured in these ALMA cycle 5 observations." (2.1 ALMA)
- Limitation (authors): Fractional polarization may be overestimated because short baselines lack  
  > "fractional linear polarizations derived from our aperture synthesis images may be overestimated" (3.2.2 Linear polarization)
- Caveat (inferred, ours): DCF assumes turbulence-dominated dispersion and density 1e6 cm-3 which is uncertain for masers
- Caveat (inferred, ours): 90-degree ambiguity of maser polarization vs field
- Caveat (inferred, ours): Faraday rotation and ARS cannot be separated cleanly
- Caveat (inferred, ours): VLA and ALMA epochs differ by months; maser variability

## Reproducibility

- Data public (paper): ALMA project 2017.1.00497.S cited; public status not explicitly stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2017.1.00497.S." (Summary)
- Products in archive: _not stated_
- Missing: CASA version and tclean parameters
- Missing: polarization calibration details
- Missing: VLA data (not ALMA) required for J=1-0 comparison
- Missing: exact velocity ranges and masks
- Data volume (inferred): ~100-500 GB raw for four long-baseline full-polarization EBs with high spectral resolution
- Score (inferred): 3/5, ALMA project code given, but imaging parameters, CASA version and polarization calibration details missing; VLA data also needed.
- Rediscovery candidate: no, Recipe lacks imaging parameters and requires VLA data and custom analysis.

## Links

- Method: (cite: Crutcher2004) (DCF formulation)
- Method: (cite: Pattle2017) (smoothed angle map subtraction for DCF)
- Companion: (cite: Plambeck2003) (BIMA SiO J=2-1 polarization of SrcI)
- Companion: (cite: Wright2020) (disk inclination and related SrcI work)

## Checks

```json
{
 "quotes": 72,
 "quotes_ok": 72,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 79,
  "stated": 51,
  "rate": 0.646
 },
 "evidence_ok": true
}
```
