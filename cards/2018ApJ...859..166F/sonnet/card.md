# A New Look at the Molecular Gas in M42 and M43: Possible Evidence for Cloud-Cloud Collision that Triggered Formation of the OB Stars in the Orion Nebula Cluster

`2018ApJ...859..166F` | The Astrophysical Journal 2018 | first author: Fukui, Yasuo | arXiv: 1701.04669 | DOI: 10.3847/1538-4357/aac217

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type archival_reuse

## Science

- Fields: star_formation, milky_way_ism
- Question: Did a cloud-cloud collision between two velocity components (8 and 13 km/s) trigger formation of the OB stars in M42 and M43 (Orion Nebula Cluster)?  
  > "aiming to test the scenario of cloud-cloud collision as a possible mechanism of high-mass star formation." (Introduction)
- Target **M42 / M43 (Orion Nebula Cluster, Orion A)**: coordinates _not stated_; z/distance 410 pc  
  > "The nearest young O star cluster is the Orion Nebula Cluster (ONC) including M42 and M43 located at 410 pc from the sun" (Introduction); distance from (cite: mue2008; ode2008; pet2008)  
  > "The nearest young O star cluster is the Orion Nebula Cluster (ONC) including M42 and M43 located at 410 pc from the sun" (Introduction)

## Data provenance

- ALMA projects: 2012.1.00554.S
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: effective beam 21'' (FWHM 15'') for NRO 45-m 12CO(1-0)  
  > "Effective beam size | 21$''$" (Table 3)
- max recoverable scale: _not stated_
- sensitivity: T_rms 0.94 K; velocity resolution 0.5 km/s (NRO 45 m)  
  > "T$_{\rm rms}$ | 0.94 K" (Table 3)
- time on source: 40 hr (NRO 45 m)  
  > "Observation time | 40 hr" (Table 3)
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: 12CO J=1-0 (115.271 GHz)
- Other facility **NRO 45-m telescope**: Archival 12CO(J=1-0) map of M42-M43 used for all analysis  
  > "The $^{12}$CO($J$ = 1–0) distributions in the M42 – M43 region obtained with the NRO 45-m telescope are presented and discussed by (cite: shi2011)." (3.1 12CO datasets)
- Other facility **2MASS**: Variable-star distribution of low-mass ONC members compared with gas  
  > "2MASS variables stars in Figure [18](#fig15) (cite: car2001)" (4.4 The age of the ONC)
- External data: NRO 45 m 12CO(1-0) dataset  
  > "The $^{12}$CO($J$ = 1–0) distributions in the M42 – M43 region obtained with the NRO 45-m telescope are presented and discussed by (cite: shi2011)." (3.1 12CO datasets) [from Shimajiri et al. 2011 (cite: shi2011)]
- External data: Simulation of cloud-cloud collision used for synthetic observations  
  > "we adopt the numerical simulations by (cite: tak2014), and Table [2](#table:4) lists the simulation parameters." (2.3) [from Takahira et al. 2014 (cite: tak2014)]
- Simulation/model as data: Takahira et al. 2014 hydrodynamical collision simulation, 5-10 km/s collision, viewing angles 0, 45, 90 deg  
  > "In Figure [2](#fig:takahira) surface density plots of the 10 km s$^{-1}$ collision model are presented" (2.3)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: _not stated_
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
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- X_CO factor of 2e20 for CO-to-H2 conversion  
  > "we apply an X$_{CO}$ factor of 2 $\times$ 10$^{20}$ (K km s$^{-1}$)$^{-1}$ cm$^{-2}$ (cite: str1988)" (3.1 12CO datasets) [from (cite: str1988)]
- Observational signatures of collision and O-star number vs column density threshold  
  > "(cite: fuk2016a) argued that the number of O stars formed by collisional triggering depends on the initial column density" (4.3) [from (cite: fuk2016a)]

### Not stated but needed to reproduce (our reading)

- The ALMA data (2012.1.00554.S) are acknowledged but no use of them is described
- Velocity channel integration ranges and masking for cloud mass calculation are only partly given
- Distance of each cloud and how masses were summed (contour levels used)
- Coordinates of targets

## Analysis recipe

1. **Search for two velocity components**: Decl.-velocity diagram and velocity-channel maps of 12CO  
  > "Figure [8](#fig6) shows the Decl.-velocity diagram covering $\sim1^\circ$ in Decl." (3.2)
   - fitting: _not stated_
   - validation: Compared with synthetic observations of simulated collisions  
  > "It is also notable that synthetic observations present observable characteristics of cloud-cloud collision including the complementary distribution at the two velocities and the bridging feature between the two colliding clouds" (Cloud-cloud collision; observational and theoretical signatures)
2. **Find complementary distributions and column density/mass**: Contour definition of blue/red-shifted clouds; overlay with displacements; mass via X_CO  
  > "we define the OMC-1 clump in the blue-shifted cloud at the contour level of 15 K km s$^{-1}$." (3.3)
   - parameter: X_CO = 2e20  
  > "we apply an X$_{CO}$ factor of 2 $\times$ 10$^{20}$ (K km s$^{-1}$)$^{-1}$ cm$^{-2}$ (cite: str1988)" (3.1 12CO datasets)
   - fitting: _not stated_
   - validation: _not stated_
3. **Fit displacement between Orion Key and Keyhole**: Maximize overlap function H(Delta) over displacement and position angle  
  > "indicates that $\Delta$ = 0.3 pc gives the optimum fit." (3.3)
   - parameter: position angle 108 deg, tested 103-113 deg  
  > "by changing the angle in a range $103^\circ$ – $113^\circ$" (3.3)
   - fitting: maximum of H(Delta)  
  > "We confirmed that the present position angle adopted gives the best fit, i.e., the maximum value of $H(\Delta)$, by changing the angle in a range $103^\circ$ – $113^\circ$" (The complementary distributions)
   - validation: Tested on synthetic observation  
  > "The method is applied to the synthetic observations" (Appendix)
4. **Collision timescale**: Size/relative velocity corrected for assumed 45 deg inclination  
  > "the time scale of the collision is estimated to be 0.4 pc / 5.7 km s$^{-1}$ = 0.07 Myr" (4.2)
   - assumption: 45 deg angle to line of sight, no deceleration  
  > "If we assume 45 deg as the angle of the relative motion to the line of sight" (4.2)
   - fitting: _not stated_
   - validation: _not stated_

## Software


## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Displacement Orion Key-Keyhole | 0.3 | not stated | pc | 3 | indicates that $\Delta$ = 0.3 pc gives the optimum fit. |
| Collision timescale (Orion Key/Keyhole) | 0.07 | not stated | Myr | 4 | the time scale of the collision is estimated to be 0.4 pc / 5.7 km s$^{-1}$ = 0.07 Myr |
| Mass of blue-shifted cloud (4.0-11.1 km/s) | 1.5e4 | not stated | Msun | 2 | Mass [$M_\odot$] / 1.5 $\times$ 10$^{4}$ / 3.4 $\times$ 10$^{3}$ |
| Mass of red-shifted cloud (11.1-14.9 km/s) | 3.4e3 | not stated | Msun | 2 | Mass [$M_\odot$] / 1.5 $\times$ 10$^{4}$ / 3.4 $\times$ 10$^{3}$ |
| OMC-1 clump molecular mass | 3.3e3 | not stated | Msun | 2 | the molecular mass of the OMC-1 clump is 3.3 $\times$ 10$^{3}$ $M_\odot$ |

## Qualitative findings

- V-shaped features in position-velocity diagrams resemble synthetic collision cases  
  > "the V-shape in Figure [14](#fig:pv_abc)(a) resembles the position-velocity diagram of the synthetic CO data" (3.4)

## Claim tuples

- H: Two colliding clouds triggered the O/B stars in M42 and M43 | E: Analysis of archival NRO 12CO(1-0) maps compared to collision simulations | R: Three complementary pairs, V-shaped PV diagrams, timescale ~0.1 Myr | F: Cloud-cloud collision is a consistent interpretation | **partially**
- H: HII expansion could explain the gas motion instead | E: Examined velocity spans in PV cuts | R: No enhancement toward HII region peak | F: HII expansion not dominant | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: HII region expansion rejected as dominant driver of gas motion  
  > "These current kinematic signatures are consistent with the conclusion reached by (cite: sug1986)." (4.5)
- How they decided it was enough: _not stated_
- Limitation (authors): Collision identification is ambiguous; projection and ionization can erase signatures  
  > "observational discrimination of cloud-cloud collision involves intrinsically some ambiguity." (2.4)
- Caveat (inferred, ours): Interpretation is qualitative; complementary pairs identified by eye and displacement chosen by eye in one region
- Caveat (inferred, ours): Inclination of 45 deg assumed
- Caveat (inferred, ours): ALMA data cited but not apparently analyzed
- Caveat (inferred, ours): Alternative explanations such as feedback not tested quantitatively

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Exact velocity channel maps and contour definitions
- Missing: Data cube from Shimajiri et al. 2011 access
- Missing: No code released
- Data volume (inferred): A few GB (single-dish CO cube)
- Score (inferred): 3/5, Public single-dish archival data and simple methods, but interpretive steps are by eye and details sparse.
- Rediscovery candidate: no, Main results are partly qualitative and ALMA data are not actually analyzed.

## Links

- Method: Takahira et al. 2014 (cite: tak2014) (Collision simulations used for synthetic observations)
- Method: Fukui et al. 2016 (cite: fuk2016a) (Signatures of collision and column density threshold)
- Companion: Shimajiri et al. 2011 (cite: shi2011) (Source of the NRO 45-m CO dataset)

## Checks

```json
{
 "quotes": 36,
 "quotes_ok": 36,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 68,
  "stated": 26,
  "rate": 0.382
 },
 "evidence_ok": true
}
```
