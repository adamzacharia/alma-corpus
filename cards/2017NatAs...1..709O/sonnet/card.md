# Millimetre-wave emission from an intermediate-mass black hole candidate in the Milky Way

`2017NatAs...1..709O` | Nature Astronomy 2017 | first author: Oka, Tomoharu | arXiv: 1707.07603 | DOI: 10.1038/s41550-017-0224-z

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: milky_way_ism, agn_and_quasars
- Question: Is there a compact object (IMBH candidate) at the centre of the broad-velocity-width cloud CO–0.40–0.22, as suggested by the gravitational kick model?  
  > "Based on the careful analysis of gas kinematics, we concluded that a compact object with a mass of $\sim\!10^5$ $M_{\hbox{$\odot$}}$ is lurking in this cloud(cite: Oka16)." (abstract)
- Target **CO–0.40–0.22 / CO–0.40–0.22***: coordinates (l, b) = (-0.3983°, -0.2235°) for the continuum source  
  > "It is located at $(l, b)\!=\!(-0.3983\hbox{$^\circ$}, -0.2235\hbox{$^\circ$})$ in galactic coordinates." (main text); "at a distance of 8.3 kpc(cite: Gillessen09)" (main text); z/distance 8.3 kpc  
  > "It is located at $(l, b)\!=\!(-0.3983\hbox{$^\circ$}, -0.2235\hbox{$^\circ$})$ in galactic coordinates." (main text); "at a distance of 8.3 kpc(cite: Gillessen09)" (main text); distance from Gillessen09  
  > "It is located at $(l, b)\!=\!(-0.3983\hbox{$^\circ$}, -0.2235\hbox{$^\circ$})$ in galactic coordinates." (main text); "at a distance of 8.3 kpc(cite: Gillessen09)" (main text)

## Data provenance

- ALMA projects: 2012.1.00940.S
- bands: Band 6  
  > "Our cycle 1 ALMA observations (ALMA/2012.1.00940.S) in Band 6 were taken on" (ALMA observations and data reduction.)
- frequencies and spectral setup: 937.5 MHz bandwidth (3840 channels) mode, each target line centred in one spectral window  
  > "we configured the correlators to the 937.5 MHz bandwidth (3840 channels) mode. Each target line was centered in one spectral window." (ALMA observations and data reduction.)
- continuum bandwidth: _not stated_
- arrays: 7-m and 12-m arrays  
  > "The 230.5 GHz (CO *J*=2–1) data were obtained with seven 7-m antennas and 39 12-m antennas" (ALMA observations and data reduction.)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: Line beams 1.87"x1.14" (230.5 GHz), 1.52"x0.60" (265.9 GHz); continuum 1.71"x1.02" and 1.35"x0.55"  
  > "The angular sizes of the cleaned beam full-width at half-maximum are $1.87\hbox{$^{\prime\prime}$}\!\times\! 1.14\hbox{$^{\prime\prime}$}$ and $1.52\hbox{$^{\prime\prime}$}\!\times\! 0.60\hbox{$^{\prime\prime}$}$" (ALMA observations and data reduction.)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: 2013 July 8, October 6–7, 2014 April 13, May 11, December 29, 2015 January 22  
  > "2013 July 8, October 6–7, 2014 April 13, May 11, December 29, and 2015 January 22." (ALMA observations and data reduction.)
- pi or archival as stated: _not stated_
- Line: HCN J=3–2 (265.9 GHz)
- Line: CO J=2–1 (230.5 GHz)
- Other facility **XMM-Newton**: 1–7 keV X-ray flux upper limit  
  > "By inspecting the X-ray data obtained by XMM Newton, we obtained an upper limit to the $1\mbox{--}7$ keV flux density" (main text)
- Other facility **ASTE**: coarse-resolution HCN J=4–3 map  
  > "previously determined by the coarse-resolution ASTE HCN *J*=4–3 map (Fig. 1a)" (main text)
- External data: Submillimetre galaxy number density used for chance probability (~0.1%)  
  > "estimated to be only $\sim 0.1\,\%$ based on the observed number density of such objects(cite: Hatsukade11)" (main text) [from Hatsukade11]
- External data: Typical CMZ dust temperature 21±2 K  
  > "the central molecular zone of our Galaxy ($T_{\rm d}=21\pm 2$ K)(cite: Pierce00)" (main text) [from Pierce00]
- Simulation/model as data: N-body gravitational kick simulation: 10^5 Msun point mass plus virialized cloud of 1000 1 Msun particles  
  > "We set a $10^5\,M_{\hbox{$\odot$}}$ point-like mass and a spherical cloud of a thousand 1 $M_{\hbox{$\odot$}}$ particles." (N-body simulations)

## Processing

### Calibration

- pipeline or manual: Calibration script supplied by EA ARC  
  > "We reduced the data with Common Astronomy Software Applications (CASA) version 4.4.0-REL with the calibration script supplied by the East Asian ALMA Regional Centre (EA ARC)." (ALMA observations and data reduction.)
- casa version: CASA 4.4.0-REL  
  > "Common Astronomy Software Applications (CASA) version 4.4.0-REL" (ALMA observations and data reduction.)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Mars, Titan, Neptune, J2232+117  
  > "Amplitude calibration was based on Mars, Titan, Neptune, and J2232+117." (ALMA observations and data reduction.)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: Natural weighting for lines; briggs for continuum (robust not given)  
  > "We ran the cleaning algorithm with natural weighting." (ALMA observations and data reduction.); "We averaged the data over the bandwidths and cleaned with briggs weighting." (ALMA observations and data reduction.)
- uv taper: _not stated_
- cell size: 0.2"  
  > "with a $2$ km s$^{-1}$ width and a cell size of $0.2\hbox{$^{\prime\prime}$}$" (ALMA observations and data reduction.)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: uvcontsub()  
  > "The data were splitted into line and continuum data sets by using the task *uvcontsub()*." (ALMA observations and data reduction.)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: Line: 7-m + 12-m; continuum: 12-m only  
  > "For continuum data, we used the 12-m array data only to drop spatially extended emission." (ALMA observations and data reduction.)
- smoothing: _not stated_
- final beam: Continuum 1.71"x1.02" PA 73.2° (230.5 GHz); 1.35"x0.55" PA 70.2° (265.9 GHz)  
  > "$1.35\hbox{$^{\prime\prime}$}\!\times\! 0.55\hbox{$^{\prime\prime}$}$, $70.2\hbox{$^\circ$}$, at 230.5 GHz and 265.9 GHz, respectively." (ALMA observations and data reduction.)
- final rms: _not stated_

### Inherited from earlier work

- Geometrical parameters of the gravitational kick model, except inclination (70° vs 90°) and VLSR (-120 vs -110 km/s)  
  > "Geometrical parameters were chosen basically in accordance with those of the previous paper(cite: Oka16)." (N-body simulations) [from Oka16]

### Not stated but needed to reproduce (our reading)

- Briggs robust value for continuum imaging
- Line-free channels used for uvcontsub and fit order
- Which calibrators were used in which epoch
- Clean threshold, masks and iterations
- Method for measuring continuum flux densities and their errors
- Excitation model details for HCN clump mass (60 K, 10^6.5 cm^-3)
- Method for XMM-Newton upper limit
- Mapping of simulation to observed PV diagram, how the simulation parameters were tuned

## Analysis recipe

1. **Image line and continuum data**: CASA calibration script from EA ARC, uvcontsub, cleaning with natural weighting (lines, 2 km/s channels) and briggs (12-m continuum)  
  > "We ran the cleaning algorithm with natural weighting." (ALMA observations and data reduction.)
   - software: CASA
   - parameter: cell 0.2"; velocity range -150 to +50 km/s  
  > "we reduced the data with channels from $-150$ km s$^{-1}$ to $+50$ km s$^{-1}$ with a $2$ km s$^{-1}$ width" (ALMA observations and data reduction.)
   - fitting: _not stated_
   - validation: _not stated_
2. **Characterise continuum source spectrum and luminosity**: Flux densities at 231 and 266 GHz, spectral index, Planck-function least-squares fit, luminosity at 8.3 kpc, comparison to Sgr A* and X-ray limit  
  > "A least-squares fit to the 231 and 266 GHz fluxes by the Planck function gives $T\simeq\! 9$ K." (main text)
   - assumption: Distance 8.3 kpc  
  > "at a distance of 8.3 kpc(cite: Gillessen09)" (main text)
   - fitting: least-squares Planck fit  
  > "A least-squares fit to the 231 and 266 GHz fluxes by the Planck function gives $T\simeq\! 9$ K." (main text)
   - validation: Chance probability of a background submillimetre galaxy ~0.1%  
  > "the chance probability of a submillimetre galaxy with a flux greater than 10 mJy within a $10\hbox{$^{\prime\prime}$}$ diameter circle is estimated to be only $\sim 0.1\,\%$" (main text)
3. **Estimate HCN clump mass and virial mass**: Excitation model mass from HCN J=3–2 integrated intensity; virial mass from size and velocity dispersion  
  > "The mass of the clump was estimated from the HCN *J*=3–2 integrated intensity to be $40$ $M_{\hbox{$\odot$}}$ according to an excitation model" (main text)
   - parameter: S = 0.15 pc, sigma_V = 22 km/s  
  > "the size parameter $S\!=\!0.15$ pc and velocity dispersion $\sigma_{\rm V}\!=\!22$ km s$^{-1}$" (main text)
   - assumption: Tk = 60 K, n(H2) = 10^6.5 cm^-3  
  > "$T_{\rm k}\!=\!60$ K and $n({\rm H}_2)\!=\!10^{6.5}$ cm$^{-3}$" (main text)
   - fitting: _not stated_
   - validation: _not stated_
4. **N-body gravitational kick simulation**: Leapfrog integration of a virialized cloud of 1000 particles passing a 10^5 Msun point mass, inclination 70°  
  > "We employed the leapfrog method to integrate Newton’s equaion of motion." (N-body simulations)
   - parameter: time step 4.6e3 yr; radial dispersion 0.2 pc; velocity dispersion 1.43 km/s; start (9.8, -0.65) pc; v=(-8.19, 0.4) km/s  
  > "The time step was set to $4.6\times 10^3$ yr." (N-body simulations)
   - assumption: VLSR of centre of gravity = -120 km/s; PA of orbital plane 41.6°  
  > "The line of sight velocity of the centre of gravity was set to $\hbox{$V_{\rm LSR}$}\!=\!-120$ km s$^{-1}$." (N-body simulations)
   - fitting: _not stated_
   - validation: Qualitative comparison to observed bulk kinematics and clump position-velocity behaviour  
  > "The simulated cloud just after the pericentre passage reproduced the bulk kinematics of CO–0.40–0.22 well." (main text)

## Software

- **CASA** 4.4.0-REL: Data reduction, uvcontsub, cleaning  
  > "We reduced the data with Common Astronomy Software Applications (CASA) version 4.4.0-REL" (ALMA observations and data reduction.)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Continuum flux density at 231 GHz | 8.38 | 0.34 | mJy | 2 | flux densities of $8.38\!\pm\!0.34$ and $9.91\!\pm\!0.74$ mJy, respectively |
| Continuum flux density at 266 GHz | 9.91 | 0.74 | mJy | 2 | flux densities of $8.38\!\pm\!0.34$ and $9.91\!\pm\!0.74$ mJy, respectively |
| Spectral index 231/266 GHz | 1.18 | 0.65 | dimensionless | 2 | The spectral index at 231/266 GHz is $\alpha\!=\!1.18\!\pm\!0.65$ |
| Planck-fit temperature | 9 | not stated | K | 2 | gives $T\simeq\! 9$ K |
| Millimetre-wave luminosity nuL_nu | 10^32.3 | not stated | erg/s | 2 | $\nu L_{\nu}\!\sim\! 10^{32.3}$ erg s$^{-1}$ |
| X-ray 1–7 keV flux upper limit | 1.4e-14 | not stated | erg cm^-2 s^-1 | 2 | $1.4\!\times\!10^{-14}$ erg cm$^{-2}$ s$^{-1}$ ($\sim\!1$ nJy) |
| HCN clump mass (excitation model) | 40 | not stated | Msun | 3 | estimated from the HCN *J*=3–2 integrated intensity to be $40$ $M_{\hbox{$\odot$}}$ |
| Virial mass of clump | 4.1e3 | not stated | Msun | 3 | $M_{\rm vir}\!\simeq\!4.1\!\times\! 10^3$ $M_{\hbox{$\odot$}}$ |
| Lower limit on mean mass density of CO–0.40–0.22* | 10^9.4 | not stated | Msun pc^-3 | 4 | gives a lower limit to the average mass density of $\rho\!\simeq\! 10^{9.4}$ $M_{\hbox{$\odot$}} \mbox{pc}^{-3}$ |

## Qualitative findings

- The point-like source is the only significant continuum source in the 80" field and lies near the dense HCN clump.  
  > "This CO–0.40–0.22$^*$ was the only significant source within the $80\hbox{$^{\prime\prime}$}$ diameter field of view." (main text)

## Claim tuples

- H: Does CO–0.40–0.22 host a compact radio source consistent with an IMBH? | E: ALMA Band 6 continuum at 231 and 266 GHz, compared with Sgr A*, submillimetre galaxy counts, and an X-ray limit | R: A point-like source with 8.4 and 9.9 mJy and an inverted spectrum, ~1/500 of Sgr A* luminosity | F: CO–0.40–0.22* is a promising IMBH candidate | **supported**
- H: Does a point-mass gravitational kick reproduce the dense clump kinematics? | E: N-body simulation with a 10^5 Msun point mass | R: Simulated cloud reproduces the bulk kinematics and the clump spatial-velocity behaviour | F: Supports a 10^5 Msun compact object | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Thermal dust emission rejected (T~9 K too low); background submillimetre galaxy rejected (~0.1% chance); stellar cluster disfavoured by no IR counterpart  
  > "Thus, the thermal origin of millimetre-wave emission from CO–0.40–0.22$^*$ is implausible." (main text); "Non-detection of an infrared counterpart disfavours the stellar cluster interpretation" (main text)
- How they decided it was enough: _not stated_
- Caveat (inferred, ours): Spectral index from only two close frequencies with large error
- Caveat (inferred, ours): Flux values in different beams/epochs combined without variability check
- Caveat (inferred, ours): Simulation parameters tuned by hand; uniqueness not tested
- Caveat (inferred, ours): Low-temperature thermal and submillimetre galaxy alternatives rely on rough probabilities
- Caveat (inferred, ours): Assumes the continuum is associated with an IMBH rather than e.g. a protostar or pulsar

## Reproducibility

- Data public (paper): Cycle 1 data available from ALMA Science Archive  
  > "Data from our ALMA cycle 1 observations (ALMA/2012.1.00940.S) can be obtained from the ALMA Science Archive Query" (Data Availability)
- Products in archive: _not stated_
- Missing: Briggs robust value
- Missing: Line-free channels for uvcontsub
- Missing: Flux measurement method
- Missing: N-body code not released
- Missing: XMM-Newton upper limit procedure
- Data volume (inferred): ~100-300 GB raw across 7 epochs and 7-m/12-m arrays
- Score (inferred): 3/5, Public data and simple numbers, but imaging details and simulation code are missing.
- Rediscovery candidate: no, Imaging parameters are incomplete and the key N-body model is not reproducible from the text alone.

## Links

- Companion: Oka16 (Original discovery and gravitational kick model of CO–0.40–0.22)

## Checks

```json
{
 "quotes": 60,
 "quotes_ok": 60,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 9,
 "numeric_problems": 0,
 "fill": {
  "facts": 70,
  "stated": 40,
  "rate": 0.571
 },
 "evidence_ok": true
}
```
