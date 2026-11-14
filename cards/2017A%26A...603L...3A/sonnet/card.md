# Molecular outflow launched beyond the disk edge

`2017A&A...603L...3A` | Astronomy and Astrophysics 2017 | first author: Alves, F. O. | arXiv: 1707.01501 | DOI: 10.1051/0004-6361/201731077

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, protoplanetary_disks
- Question: Where is the molecular outflow launched relative to the disk, and what are the kinematics in the envelope-disk transition zone of the Class I object BHB07-11?  
  > "we investigate the kinematics in the envelope-disk transition zone of the Class I object BHB07-11, in the B59 core." (abstract)
- Target **BHB07-11**: coordinates _not stated_; z/distance 145 pc  
  > "The star-forming cloud B59 is located at a distance of 145 pc (cite: Alves07)" (Introduction); distance from Alves & Franco 2007 (cite: Alves07)  
  > "The star-forming cloud B59 is located at a distance of 145 pc (cite: Alves07)" (Introduction)

## Data provenance

- ALMA projects: 2013.1.00291.S
- bands: Band 6 (230 GHz, ~1.3 mm)  
  > "at an atmospheric spectral window of 230 GHz ($\lambda \sim 1.3$ mm)" (Observations)
- frequencies and spectral setup: 4 spectral windows: one TDM continuum, three FDM line windows; resolution 0.32 km/s (CO), 0.17 km/s (H2CO)  
  > "The observing setup contained four spectral windows, one of which was dedicated to continuum observations (in time-domain mode, TDM), and the other three dedicated to molecular line observations" (Observations)
- continuum bandwidth: about 2.3 GHz  
  > "was about 2.3 GHz, leading to an *rms* of $62~\mu$Jy beam$^{-1}$" (Observations)
- arrays: 44 antennas, extended configuration  
  > "using 44 antennas in an extended configuration (baselines between 0.02 and 1.6 km)" (Observations)
- configurations: _not stated_
- baselines: 0.02 to 1.6 km  
  > "baselines between 0.02 and 1.6 km" (Observations)
- angular resolution: ~32 AU (~30 AU)  
  > "The processed maps have a spatial resolution of $\sim$ 32 AU." (Observations)
- max recoverable scale: _not stated_
- sensitivity: continuum rms 62 uJy/beam; line rms 0.4 (CO) and 1.5 (H2CO) mJy/beam  
  > "with an *rms* noise for the line-free channels of 0.4 and 1.5 mJy beam$^{-1}$, respectively." (Observations)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: CO J = 2-1 (not stated)
- Line: C18O J = 2-1 (not stated)
- Line: H2CO 3(0,3)-2(0,2) (not stated)
- External data: Dust temperature ~31 K  
  > "Adopting the dust temperature of $\sim 31$ K measured by (cite: Hara13)" (Results) [from (cite: Hara13)]
- External data: Dust opacity for mass estimate  
  > "we estimate a disk plus envelope mass of $0.17 \pm 0.06$ M$_{\odot}$ (cite: Ossenkopf94)" (Results) [from (cite: Ossenkopf94)]
- Simulation/model as data: Self-calibrated-free LIME radiative transfer of a self-gravitating 0.17 Msun disk model (Evans et al. 2015), observed with simulated CASA ALMA observation  
  > "The model was a self-gravitating disk of 0.17 M$_{\odot}$ surrounding a solar-type star (cite: EIB15)." (Modeling gravitational instabilities)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Titan  
  > "The absolute flux calibration was obtained using Titan." (Observations)
- flux scale uncertainty: about 7%  
  > "the uncertainty on the absolute flux density scale is about 7%." (Observations)
- self calibration: continuum maps self-calibrated, noise improved by ~40%  
  > "The final continuum maps were self-calibrated and improved by about 40% in noise level." (Observations)

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

### Not stated but needed to reproduce (our reading)

- CASA version and calibration route (pipeline vs manual)
- imaging task, weighting/robust, cell and image size, masks
- line-free channels and continuum subtraction method
- self-calibration solution intervals
- how the stellar mass 1.70 Msun was derived
- PV cut widths and Keplerian model parameters
- dust opacity value and gas-to-dust ratio used
- CASA simulation parameters (simobserve configuration, PWV)

## Analysis recipe

1. **Dust continuum disk/envelope structure and mass**: Measure disk and envelope sizes, PA, inclination from continuum map; mass from dust emission  
  > "The minor-to-major axis ratio indicates an inclination of $70\ensuremath{^\circ}$ with respect to the line of sight." (Results)
   - software: CASA
   - assumption: Dust temperature ~31 K; Ossenkopf & Henning opacities; distance 145 pc  
  > "Adopting the dust temperature of $\sim 31$ K measured by (cite: Hara13)" (Results)
   - fitting: _not stated_
   - validation: _not stated_
2. **Outflow identification in CO**: CO channel maps, comparison with escape velocity at 90-130 AU for stellar mass 1.70 Msun  
  > "At 90$-$130 AU, the escape velocity of the system is 4.8 km s$^{-1}$ to 5.8 km s$^{-1}$" (Molecular emission)
   - fitting: _not stated_
   - validation: _not stated_
3. **Kinematics via PV diagrams (C18O, H2CO)**: PV cuts along major axis compared with Keplerian curves to find centrifugal barrier  
  > "The molecular emission exceeds the Keplerian curves in velocity and reaches a maximum at 225 AU" (Disk-envelope transition zone)
   - fitting: _not stated_
   - validation: _not stated_
4. **Test gravitational instability origin of asymmetry**: LIME radiative transfer of self-gravitating disk model, simulated ALMA observation in CASA  
  > "we used CASA to simulate an observation of this model under the same conditions as our observations" (Modeling gravitational instabilities)
   - software: LIME, CASA
   - assumption: Model at 145 pc, inclination 70 deg, 0.17 Msun disk  
  > "placed at the same distance (145 pc) and inclination (70$^\circ$) as BHB07-11" (Modeling gravitational instabilities)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : calibration, imaging, simulated observations  
  > "The data were calibrated and imaged using CASA" (Observations)
- **LIME** : non-LTE radiative transfer of disk model  
  > "using LIME (cite: Brinch10)" (Modeling gravitational instabilities)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Disk radius | ~80 | not stated | AU | 1 | a bright and sharp compact disk with a radius of $\sim 80$ AU |
| Envelope radius | 435 | not stated | AU | 1 | a radius of 435 AU with a PA of 167$\ensuremath{^\circ}$ |
| Disk plus envelope mass | 0.17 | 0.06 | Msun | 1 | we estimate a disk plus envelope mass of $0.17 \pm 0.06$ M$_{\odot}$ |
| Inclination | 70 | not stated | deg | 1 | indicates an inclination of $70\ensuremath{^\circ}$ with respect to the line of sight |
| Stellar mass | 1.70 | 0.04 | Msun | 3 | for our estimated stellar mass of $1.70\pm0.04$ M$_{\odot}$ |
| Outflow launch distance | 90-130 | not stated | AU | 2 | This molecular component originates at a distance of $\sim$ 90$-$130 AU from the disk center |
| Kinematic center offset from dust peak | 14 | not stated | AU | 2 | the kinematical center is 14 AU removed from the dust peak |

## Qualitative findings

- Spiral structures are likely infall streams, not gravitational instabilities; the centrifugal barrier lies at the tip of the spirals  
  > "the location of the centrifugal barrier is at the tip of the spiral structures" (Disk-envelope transition zone)

## Claim tuples

- H: Outflow can be launched outside the disk edge | E: CO channel maps vs dust continuum | R: Conical CO outflow originating at 90-130 AU, unbound | F: Bipolar outflow launched at infall landing site beyond disk edge | **supported**
- H: Centrifugal barrier located at tip of spiral | E: H2CO PV cut vs Keplerian curves | R: Velocity discontinuity and deceleration at ~87-188 AU | F: Centrifugal barrier pinpointed at spiral tip | **supported**
- H: Disk asymmetry/spirals arise from gravitational instability | E: LIME+CASA simulation of self-gravitating disk | R: Spirals unresolved in simulation | F: Asymmetries must have another origin | **refuted**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Gravitational instability origin of spirals rejected  
  > "The large-scale spiral structures are unlikely to originate in gravitational instabilities" (Disk-envelope transition zone)
- How they decided it was enough: _not stated_
- Caveat (inferred, ours): Single source; launching-site claim rests on visual channel-map morphology without quantitative fit
- Caveat (inferred, ours): Mass depends on assumed temperature and opacity, no uncertainty on dust law
- Caveat (inferred, ours): Centrifugal barrier identification not tested against alternative models quantitatively

## Reproducibility

- Data public (paper): Data archived in ALMA Science Archive  
  > "The data reported in this paper are archived in the ALMA Science Archive." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Imaging parameters
- Missing: CASA version
- Missing: PV extraction details
- Missing: Keplerian model parameters
- Data volume (inferred): ~50-100 GB raw
- Score (inferred): 4/5, Public single-project data, but processing and analysis details are largely unstated and the results are mostly qualitative.
- Rediscovery candidate: no, Recipe incomplete and main results mostly morphological.

## Links

- Companion: Zhao et al. 2016 (cite: Zhao16) (MHD models of centrifugal barrier and pinched fields)

## Checks

```json
{
 "quotes": 42,
 "quotes_ok": 42,
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
  "facts": 64,
  "stated": 27,
  "rate": 0.422
 },
 "evidence_ok": true
}
```
