# FAUST: XXV. A potential new molecular outflow in [BHB2007] 11

`2025A&A...699A.382M` | Astronomy and Astrophysics 2025 | first author: Martínez-Henares, A. | arXiv: 2505.13333 | DOI: 10.1051/0004-6361/202554755

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, astrochemistry
- Question: What is the nature of the elongated H2CO structures around the Class 0/I binary [BHB2007] 11: a second outflow, cavity walls, relic outflow or streamers, from the kinematics at ~50-3000 au  
  > "Our aim is to study the kinematics of the molecular gas at intermediate scales of $\sim50-3000$ au around \[BHB2007\] 11 to verify the nature of these elongated structures." (abstract)
- Target **[BHB2007] 11 (B59#11)**: coordinates RA(J2000)=17h11m23.125s, Dec=-27d24m32.87s (phase center)  
  > "Also known as B59#11, it is a Class 0/I protostellar object located at a distance of 163 $\pm$ 5 pc (cite: dzib2018)." (Introduction); "The observations were centered at $\alpha$(2000)=17h11m23.125s, $\delta$(2000)=–27$^{\circ}$24’32.87”." (Observations and data reduction); z/distance 163 ± 5 pc  
  > "Also known as B59#11, it is a Class 0/I protostellar object located at a distance of 163 $\pm$ 5 pc (cite: dzib2018)." (Introduction); "The observations were centered at $\alpha$(2000)=17h11m23.125s, $\delta$(2000)=–27$^{\circ}$24’32.87”." (Observations and data reduction); distance from Dzib et al. 2018  
  > "Also known as B59#11, it is a Class 0/I protostellar object located at a distance of 163 $\pm$ 5 pc (cite: dzib2018)." (Introduction); "The observations were centered at $\alpha$(2000)=17h11m23.125s, $\delta$(2000)=–27$^{\circ}$24’32.87”." (Observations and data reduction)

## Data provenance

- ALMA projects: 2018.1.01205.L, 2019.1.01566.S, 2013.1.00291.S
- bands: Band 6 (setups 1,2) and Band 3 (setup 3); lines used from setups 1 and 2  
  > "The spectral setup consisted of two frequency setups (setups 1 and 2) in Band 6 and one (setup 3) in Band 3." (Observations and data reduction)
- frequencies and spectral setup: channel width 122.07 kHz (0.14 km/s); archival CO(3-2) cube 0.24 MHz (~0.11 km/s)  
  > "with a spectral channel width of 122.07 kHz (equivalent to a velocity resolution of 0.14 km s$^{-1}$)" (Observations and data reduction)
- continuum bandwidth: _not stated_
- arrays: 12 m and 7 m  
  > "Observations for the two relevant setups were performed with the 12 m and 7 m antennas" (Observations and data reduction)
- configurations: _not stated_
- baselines: 15 m-1.3 km (12m); 8.9-48.9 m (7m)  
  > "with baseline lengths from 15 m to 1.3 km for the 12m array and from 8.9 m to 48.9 m for the 7 m array" (Observations and data reduction)
- angular resolution: ~0.42" (FAUST); 0.11" (CO 3-2)  
  > "The resulting beam size after applying Briggs weighting with a robust parameter of 0.5 is $\sim0.42$" across the two setups." (Observations and data reduction)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: between 2018 and 2020  
  > "between 2018 and 2020" (Observations and data reduction)
- pi or archival as stated: _not stated_
- Line: H13CO+ J=3-2, F1=5/2-3/2, F=2-1 (260.255 GHz)
- Line: CCH N=3-2, J=7/2-5/2, F=4-3 (262.004 GHz)
- Line: c-C3H2 6(0,6)-5(1,5) (217.822 GHz)
- Line: SiO 5-4 (217.105 GHz)
- Line: CS 5-4 (244.935 GHz)
- Line: C18O 2-1 (not stated)
- Line: CO 3-2 (not stated)
- External data: Distance 163±5 pc  
  > "located at a distance of 163 $\pm$ 5 pc (cite: dzib2018)" (Introduction) [from (cite: dzib2018)]
- External data: Circumstellar disk inclination 40±10 deg and combined mass 2.25±0.13 Msun  
  > "The inclinations of the circumstellar disks with respect to the line of sight are of $40\pm10^{\circ}$ (cite: alves2019)." (Physical properties); "$2.25\pm0.13$ $M_{\odot}$ (cite: alves2019)" (Alternative interpretations) [from (cite: alves2019)]
- External data: 16O/18O=560±25  
  > "isotopic ratio $^{16}$O$/^{18}$O$=560\pm25$ (cite: wilson1994)" (Physical properties) [from (cite: wilson1994)]
- External data: 12C/13C~69  
  > "$^{12}$C$/^{13}$C$\sim69$ (cite: milam2005)" (Shocked material at smaller scales) [from (cite: milam2005)]
- External data: 1.3 mm continuum image overlaid  
  > "we show the 1.3 mm continuum emission (cite: alves2017)" (Results) [from (cite: alves2017)]

## Processing

### Calibration

- pipeline or manual: CASA with modified FAUST pipeline; archival CO(3-2) imaged by ALMA pipeline  
  > "The calibration and imaging of the data was performed with CASA using a modified version of the pipeline developed by the FAUST data reduction team" (Observations and data reduction)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: Briggs robust = 0.5  
  > "The resulting beam size after applying Briggs weighting with a robust parameter of 0.5 is $\sim0.42$" across the two setups." (Observations and data reduction)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: applied  
  > "The images have been corrected from the primary beam response." (Observations and data reduction)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: ~0.42" (FAUST), 0.11" (CO 3-2)  
  > "a synthesized beam size of 0.11"." (Observations and data reduction)
- final rms: _not stated_

### Inherited from earlier work

- Observations, data reduction and imaging of FAUST data  
  > "Observations, data reduction and imaging are described in detail in previous FAUST articles on the source (cite: vastel2022; evans2023; vastel2024)." (Observations and data reduction) [from (cite: vastel2022; evans2023; vastel2024)]
- Transversal PV analysis of outflow rotation  
  > "We then employ the PV diagrams to quantify the rotation of the outflow as done in (cite: zhang2018)." (Rotation of the outflow) [from (cite: zhang2018); (cite: ohashi2022)]
- Pixel Flux-tracing Technique for outflow rates  
  > "Following the procedure from (cite: hsieh2023), we have employed their Pixel Flux-tracing Technique (PFT) code" (Physical properties) [from (cite: hsieh2023)]
- Launching radius formula  
  > "we estimate the launching radius $r_0$ of the outflow employing the method from (cite: anderson2003)" (Rotation of the outflow) [from (cite: anderson2003)]

### Not stated but needed to reproduce (our reading)

- Velocity ranges used for moment maps (chosen by eye, not tabulated)
- Exact polygon regions for kinematic analysis and PV cut definitions
- Continuum subtraction and line-free channels
- Self-calibration details of FAUST pipeline
- Spatial masks and clipping for moment 0 maps
- Setup for the PFT code run and the MADCUBA fit linewidth/velocity settings
- Which of the three project codes (e.g. 2013.1.00291.S) supplies the continuum or what data were used

## Analysis recipe

1. **Map morphology**: Moment 0 maps of H13CO+, CCH, c-C3H2, SiO and CO(3-2) in red/blue velocity ranges chosen by inspecting channels  
  > "The velocity ranges in the figure have been selected after inspecting the data cubes channel per channel to obtain the clearest view of the structures." (Results)
   - fitting: Linear fit of outermost CO contours for outflow PA; Gaussian fit for SiO PA  
  > "we have performed a linear fit of the outermost contours that delineate the outflow" (Results)
   - validation: _not stated_
2. **Kinematics via PV diagrams**: PV diagrams of emission within polygons to identify outflowing motion  
  > "We investigate the kinematics of the elongated components with the position-velocity (PV) diagrams" (Kinematics)
   - fitting: _not stated_
   - validation: _not stated_
3. **Outflow mass, momentum, energy and mass loss rate**: C18O column density from integrated profile, LTE optically thin, T=50-100 K; mass from column density; t_dyn=R/v_exp; compared to PFT method  
  > "assuming optically thin emission under LTE conditions and a warm outflow with a range of temperatures of 50 to 100 K" (Physical properties)
   - software: MADCUBA (SLIM), PFT code
   - parameter: v_exp = largest velocity offset 1.68±0.14 km/s, inclination-corrected to 2.2±0.4 km/s  
  > "$v_{exp}$ is corrected to $2.2\pm0.4$ km s$^{-1}$" (Physical properties)
   - assumption: chi(CO)~1e-4, mu_g=2.3, 16O/18O=560, inclination 40±10 deg, d=163 pc  
  > "the relative abundance of CO to H$_2$, $\chi(\textrm{CO})\sim10^{-4}$, $\mu_g=2.3$ is the mean atomic weight of the gas" (Physical properties)
   - fitting: SLIM-MADCUBA line profile fit; sampler not stated  
  > "The Spectral Line Identification and Modelling (SLIM) tool within the MADCUBA package (cite: martin2019) is employed to fit the integrated C$^{18}$O line profile, assuming optically thin emission under LTE conditions" (3.3.1 Mass, momentum and energy)
   - validation: Compared with PFT method  
  > "we have employed their Pixel Flux-tracing Technique (PFT) code to compare the results with the $t_{dyn}$ method" (Physical properties)
4. **Outflow rotation and launching radius**: Transversal PV diagrams of red lobe, extreme points at 0.6 of peak; R_out, V_rot, specific angular momentum; r0 from Anderson et al. formula  
  > "within the pixels of 0.6 times the value of the peak intensity, which adequately trace the extent of the curve" (Rotation of the outflow)
   - parameter: transversal cuts perpendicular to PA = 8 deg  
  > "perpendicular to the elongated H$^{13}$CO$^+$ emission with a PA = 8$^{\circ}$" (Rotation of the outflow)
   - assumption: equal-mass system, combined mass from Alves 2019  
  > "considering an equal-mass system as an approximation, the estimated launching radius is $r_0=90\pm30$ au" (Rotation of the outflow)
   - fitting: _not stated_
   - validation: Constant specific angular momentum curve overplotted on 60% contours of PV diagrams  
  > "The curve encloses the emission from the velocity curves at different offsets" (Rotation of the outflow)
5. **SiO abundance**: SiO and C18O (or H13CO+) column densities in 3sigma SiO region, LTE optically thin, T=50-100 K, central ±3 km/s excluded  
  > "We integrate the line profiles avoiding the central $\pm$3 km s$^{-1}$ velocities from the systemic velocity of 3.6 km s$^{-1}$" (Shocked material at smaller scales)
   - assumption: chi(HCO+)~1e-8, 12C/13C~69  
  > "$\chi(\textrm{HCO}^+)\sim10^{-8}$ (cite: irvine1987)" (Shocked material at smaller scales)
   - fitting: _not stated_
   - validation: Two independent abundance estimates give lower limits  
  > "the derived SiO abundances should be considered as lower limits" (Shocked material at smaller scales)

## Software

- **CASA** : calibration and imaging with modified FAUST pipeline  
  > "The calibration and imaging of the data was performed with CASA using a modified version of the pipeline" (Observations and data reduction)
- **MADCUBA (SLIM)** : fit C18O integrated line profile  
  > "The Spectral Line Identification and Modelling (SLIM) tool within the MADCUBA package (cite: martin2019) is employed to fit the integrated C$^{18}$O line profile" (Physical properties)
- **PFT code** : pixel-by-pixel outflow rates  
  > "we have employed their Pixel Flux-tracing Technique (PFT) code" (Physical properties)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| CO outflow axis PA | 58 | ±2 | deg | 1 | Hence, we derive a CO outflow axis of $58\pm2^{\circ}$ |
| SiO emission PA | 114 | ±6 | deg | 1 | a PA of 114 $\pm$ 6$^{\circ}$ obtained from Gaussian fitting |
| Expansion velocity (inclination corrected) | 2.2 | ±0.4 | km/s | 3 | $v_{exp}$ is corrected to $2.2\pm0.4$ km s$^{-1}$ |
| Length of single lobe | 3300 | ±700 | au | 3 | we obtain a physical extent of $3300\pm700$ au |
| Dynamical timescale | 7000 | ±1900 | yr | 3 | $t_{dyn}=7000\pm1900$ yr |
| Total outflow mass | 1.29e-2 | ±0.11e-2 | Msun | 3 | $M=(1.29\pm0.11)\times10^{-2}M_{\odot}$ |
| Mass loss rate | 1.8e-6 | ±0.5e-6 | Msun/yr | 3 | $\dot{M}=M/t_{dyn}=(1.8\pm0.5)\times10^{-6}M_{\odot}\textrm{ yr}^{-1}$ |
| Momentum injection rate | 4.0e-6 | ±1.3e-6 | Msun km/s /yr | 3 | $\dot{P}=\dot{M}v_{exp}=(4.0\pm1.3)\times10^{-6}M_{\odot}$ km s$^{-1}$ yr$^{-1}$ |
| Kinetic energy | 6e41 | ±2e41 | erg | 3 | $E=\frac{1}{2}Mv_{exp}^2=(6\pm2)\times10^{41}$ erg |
| Specific angular momentum | 70 | ±25 | au km/s | 4 | The derived mean and standard deviation of the specific angular momentum is $70\pm25$ au km s$^{-1}$ |
| Launching radius | 90 | ±30 | au | 4 | the estimated launching radius is $r_0=90\pm30$ au |
| SiO abundance (lower limit) | >=(0.11-2.0)e-9 | not stated | relative to H2 | 5 | with a relative abundance of $\geq(0.11-2.0)\times10^{-9}$ |
| PFT mass loss rate | 4.2e-8 | not stated | Msun/yr | 3 | $4.2\times10^{-8}M_{\odot}\textrm{yr}^{-1}$ |

## Qualitative findings

- H13CO+, CCH, c-C3H2 show elongated SE/NW structures like H2CO, with kinematics consistent with outflow and opposite-sense rotation to main CO outflow  
  > "whose gas kinematics are consistent with outflowing motions and with rotation in the opposite sense to the main CO outflow" (abstract)
- SiO is compact, aligned with the large-scale structures, tracing shocked base of the potential outflow  
  > "The SiO image reveals compact emission close to the binary system, with a slight elongation aligned with the larger-scale structures." (abstract)

## Claim tuples

- H: The elongated structures trace a second outflow | E: Moment maps and PV diagrams of H13CO+, CCH, c-C3H2 | R: Blueshifted lobe accelerates; redshifted flat/tentative acceleration | F: Consistent with second outflow, though other scenarios not excluded | **partially**
- H: Mass loss rate resembles Class 0/I outflows | E: C18O column density, t_dyn method | R: 1.8e-6 Msun/yr | F: In line with Class 0/I values, though PFT gives 1-2 orders lower | **partially**
- H: SiO arises from shocks at base of the new outflow | E: SiO morphology and abundance | R: Aligned with large-scale structures, abundance >=(0.11-2.0)e-9, velocity 13±3 km/s | F: Supports sputtering; streamer accretion shock disfavoured | **supported**
- H: Outflow rotates | E: Transversal PV analysis | R: l=70±25 au km/s, gradient comparable to velocity resolution | F: Tentative rotation, shear possible | **partially**

## Reasoning

- Why this data: Molecules trace ambient-velocity gas unobservable in self-absorbed CO  
  > "These molecules trace the material moving at velocities close to the ambient cloud velocity, which could not be probed in previous observations of the self-absorbed emission of CO." (abstract)
- Why this method: _not stated_
- Alternative: Cavity walls of wide-angle CO outflow component: not excluded  
  > "these images alone do not allow us to discern between the new outflow scenario or the case of a wide-angle, slow molecular wind" (Alternative interpretations)
- Alternative: Relic outflow considered unlikely  
  > "Consequently, we consider the possibility of a relic emission from the main CO outflow as unlikely." (Alternative interpretations)
- Alternative: Accretion streamers disfavoured  
  > "which seems to rule out the accretion streamer scenario for the SiO emission" (Alternative interpretations)
- How they decided it was enough: _not stated_
- Limitation (authors): Field of view truncates the outflow; velocity resolution comparable to gradients; expansion velocity poorly constrained  
  > "one of the main limitations of our data is that the outflow is potentially not fully covered by the field of view of the observations." (Discussion)
- Caveat (inferred, ours): Redshifted lobe flat velocity profile and the transverse gradient can be explained by cavity shear
- Caveat (inferred, ours): Assumed v_exp is the max velocity offset, very uncertain; r0 varies from 90 au to 10 au
- Caveat (inferred, ours): Mass loss rates differ by 1-2 orders between t_dyn and PFT
- Caveat (inferred, ours): Fixed 50-100 K and CO abundance assumptions drive masses; SiO abundance limits

## Reproducibility

- Data public (paper): Data from ALMA archive (CO 3-2 retrieved from archive); FAUST large program data  
  > "we have retrieved the CO (3-2) line cube from the ALMA archive (project 2019.1.01566.S)" (Observations and data reduction)
- Products in archive: _not stated_
- Code: FAUST pipeline described at faust-imaging.readthedocs.io  
  > "[^1]: <https://faust-imaging.readthedocs.io/en/latest/>" (Observations and data reduction)
- Missing: Velocity ranges and polygon regions
- Missing: Continuum subtraction and line-free channels
- Missing: PFT code parameters
- Missing: Version of CASA and pipeline
- Data volume (inferred): ~100-300 GB (FAUST 12m+7m Band 6 for one source plus archival CO 3-2 cube)
- Score (inferred): 3/5, Public data and clear formulae, but regions, velocity ranges and pipeline details are only in earlier papers or not given.
- Rediscovery candidate: no, Reduction details are inherited from earlier FAUST papers and the key regions and velocity ranges are not tabulated; the interpretation is partly qualitative.

## Links

- Method: Zhang et al. 2018 (cite: zhang2018) (transversal PV rotation method)
- Method: Hsieh et al. 2023 (cite: hsieh2023) (PFT outflow rate method)
- Method: Anderson et al. 2003 (cite: anderson2003) (launching radius estimate)
- Companion: Evans et al. 2023 (cite: evans2023) (discovery of the H2CO elongated structures)
- Companion: Vastel et al. 2022, 2024 (cite: vastel2022; vastel2024) (FAUST data reduction and COM studies of this source)
- Companion: Alves et al. 2017, 2019 (cite: alves2017; alves2019) (CO outflow and circumbinary disk)
- Related: FAUST (ALMA Large Program 2018.1.01205.L)

## Checks

```json
{
 "quotes": 82,
 "quotes_ok": 82,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 3,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 13,
 "numeric_problems": 0,
 "fill": {
  "facts": 82,
  "stated": 50,
  "rate": 0.61
 },
 "evidence_ok": true
}
```
