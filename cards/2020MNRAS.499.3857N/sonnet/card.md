# Spirals, shadows &amp; precession in HD 100453 - II. The hidden companion

`2020MNRAS.499.3857N` | Monthly Notices of the Royal Astronomical Society 2020 | first author: Nealon, Rebecca | arXiv: 2009.10505 | DOI: 10.1093/mnras/staa2721

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type theory_or_simulation_compared_to_alma

## Science

- Fields: protoplanetary_disks
- Question: What are the properties of the hidden inner companion in HD 100453, and how did the inner/outer disc misalignment arise?  
  > "Here we investigate the properties of the inner companion and the origin of the misalignment between the inner and outer disc." (abstract)
- Target **HD 100453**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2017.1.01424.S
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: 12CO J=3-2 (not stated)
- External data: ALMA 12CO J=3-2 channel maps and CLEAN beam, calibration described there  
  > "we have reproduced the ALMA channel maps and refer to (cite: Rosotti:2020nj) for details of its calibration." (3.2.2 Kinematics) [from (cite: Rosotti:2020nj)]
- External data: Best-fit outer binary orbit and disc parameters from companion paper (Table 1)  
  > "In this work we thus adopt the binary parameters from , summarised in the top of Table [1](#table:properties)." (2 Observational constraints) [from (cite: Gonzalez:sub); (cite: vanderPlas:2019gy)]
- Simulation/model as data: PHANTOM SPH simulations with N=10^6 particles; 12CO J=3-2 channel maps via MCFOST  
  > "As in , the disc is modelled with $N=10^6$ particles (corresponding to $\sim2.5$ smoothing lengths per scale-height)." (3.2.1 Hydrodynamics)

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
- final beam: 0.054 x 0.052 (stated as mas, apparently arcsec) CLEAN beam, from Rosotti et al. 2020  
  > "are convolved with the ALMA CLEAN beam of $0.054 \times 0.052$ mas (cite: Rosotti:2020nj)." (3.2.2 Kinematics)
- final rms: _not stated_

### Inherited from earlier work

- ALMA data calibration and channel maps  
  > "refer to (cite: Rosotti:2020nj) for details of its calibration." (3.2.2 Kinematics) [from (cite: Rosotti:2020nj)]
- Outer binary orbit and numerical parameters adopted from companion paper  
  > "We adopt the numerical parameters of the best fit orbit in with several alterations." (3.2.1 Hydrodynamics) [from (cite: Gonzalez:sub)]

### Not stated but needed to reproduce (our reading)

- Companion-paper (Paper I) setup details for the SPH runs
- MCFOST inclination/PA and disc geometry for synthetic maps
- Velocity channels and noise treatment when comparing to ALMA
- Disc surface density profile parameters
- Inner disc and dust properties for radiative transfer

## Analysis recipe

1. **Compare sound-crossing and precession timescales**: Analytic estimates of sound crossing time and Bate et al. precession time  
  > "To test whether this scenario occurs for HD 100453 we compare the sound crossing and precession time-scales." (3.1 Can HD 100453 B explain the broken inner disc?)
   - assumption: H/R = 0.05 at 1 au, q=0.25, R_in = 0.01 au  
  > "Assuming a typical aspect ratio of $H/R = 0.05$ at 1 au" (3.1 Can HD 100453 B explain the broken inner disc?)
   - fitting: _not stated_
   - validation: _not stated_
2. **SPH simulations of inner planet**: Grid of planet masses 5, 10, 20 MJ at 10, 15, 20 au; inner edge defined at 10% of max surface density  
  > "We measure the inner edge of the outer disc (shown in Figure [3](#fig:C_OD_P_sigma) with vertical, dashed lines) where the surface density profile drops below $10\%$ of the maximum surface density." (3.2.1 Hydrodynamics)
   - software: PHANTOM
   - assumption: alpha=5e-3, dust and gas well coupled  
  > "For these simulations we have adopted $\alpha=5 \times 10^{-3}$ as in ." (3.2.1 Hydrodynamics)
   - fitting: _not stated_
   - validation: Inner edge compared with observed 18-23 au range  
  > "We find five cases that show agreement between the inner edge of the disc in our simulations and the range from observations." (3.2.1 Hydrodynamics)
3. **Synthetic 12CO channel maps**: MCFOST radiative transfer, convolved with ALMA beam, compared with ALMA maps  
  > "Here we use a Voronoi tessellation built around the SPH particles with $10^8$ photon packets." (3.2.2 Kinematics)
   - software: MCFOST
   - parameter: CO/H2 = 1e-4; 100 grain sizes 0.03-1000 micron, exponent -3.5; 0.042 km/s channels  
  > "The grains are distributed across 100 sizes between 0.03 and 1000$\mu$m with a power-law exponent of -3.5." (3.2.2 Kinematics)
   - fitting: _not stated_
   - validation: Visual comparison of high-velocity channel emission with ALMA  
  > "As the channel maps shown in presented from ALMA show emission at these velocities which is more consistent with the $5$ M$_{\rm J}$ mass planet, we favour the lower planet mass" (3.2.2 Kinematics)
4. **Long-term N-body evolution**: REBOUND test particles for rigid discs at Kozai-Lidov equivalent radii  
  > "We use the $N$-body code REBOUND (cite: REBOUND; Rein:2015nj) to show how the Kozai-Lidov mechanism can generate such misalignments on long timescales." (4.1 Kozai-Lidov oscillations)
   - software: REBOUND
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **PHANTOM** : SPH hydrodynamics  
  > "using the smoothed particle hydrodynamics code PHANTOM (cite: Phantom)" (3.2 Properties of the inner companion)
- **MCFOST** : Radiative transfer, CO channel maps  
  > "We use MCFOST (cite: Pinte:2006nw; Pinte:2009ye) to calculate the $^{12}$CO $J=3-2$ molecular line emission" (3.2.2 Kinematics)
- **REBOUND** : N-body evolution  
  > "We use the $N$-body code REBOUND (cite: REBOUND; Rein:2015nj)" (4.1 Kozai-Lidov oscillations)
- **SPLASH** : Rendering Figure 2  
  > "Figure [2](#fig:render) was plotted with SPLASH (cite: Price:2007kx) and Figure [4](#fig:CO_map) with PYMCFOST." (Acknowledgements)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Inner companion mass upper limit | 5 | not stated | M_J | 3 | We thus place an upper limit on the planet mass of $5$ M$_{\rm J}$ |
| Outer disc precession timescale | 8.8e5 | not stated | yr | 4 | yields a precession rate of $8.8 \times 10^5$ yrs |
| Kozai-Lidov timescale for unbroken disc | 1.1e5 | not stated | yr | 4 | $\langle T_{\rm KL} \rangle \approx 1.1 \times 10^5$ yrs |

## Qualitative findings


## Claim tuples

- H: Can the outer companion alone break the disc? | E: Compared sound crossing and precession timescales | R: T_p ~6.5e5 yr exceeds T_s (~1.5 binary orbits) | F: An unseen inner companion is needed | **supported**
- H: What inner companion mass and location fit the data? | E: SPH plus MCFOST grid compared with ALMA CO | R: Inner edge consistent for 5-10 MJ at 15-20 au | F: Planet of ≲5 MJ at 15-20 au | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Kozai-Lidov oscillations were not seen in hydrodynamic simulations; N-body neglects gas effects  
  > "our simulation in that goes for twice this length of time does not show any evidence of these oscillations" (5.2 Limitations)
- Caveat (inferred, ours): Planet mass depends strongly on assumed alpha
- Caveat (inferred, ours): Qualitative visual comparison with ALMA maps
- Caveat (inferred, ours): Rigid-disc test-particle approximation

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Code: Codes public; input files on request  
  > "The input files for generating the SPH simulations, radiative transfer models and REBOUND calculations will be shared on reasonable request to the corresponding author." (Data Availability Statement)
- Missing: Paper I setup
- Missing: MCFOST not freely available
- Missing: Input files only on request
- Data volume (inferred): small (published ALMA maps only; simulations dominate)
- Score (inferred): 3/5, Simulation-focused, with ALMA used only as reference maps; inputs partly in companion paper.
- Rediscovery candidate: no, Main results are simulation-based and need unreleased inputs.

## Links

- Companion: (cite: Gonzalez:sub) (Companion paper on outer-companion orbit and disc simulations)
- Companion: (cite: Rosotti:2020nj) (Source of ALMA CO data and calibration)

## Checks

```json
{
 "quotes": 30,
 "quotes_ok": 30,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 3,
 "numeric_problems": 0,
 "fill": {
  "facts": 69,
  "stated": 22,
  "rate": 0.319
 },
 "evidence_ok": true
}
```
