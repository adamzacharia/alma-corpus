# The Second Galactic Center Black Hole? A Possible Detection of Ionized Gas Orbiting around an IMBH Embedded in the Galactic Center IRS13E Complex

`2017ApJ...850L...5T` | The Astrophysical Journal Letters 2017 | first author: Tsuboi, Masato | arXiv: 1711.00612 | DOI: 10.3847/2041-8213/aa97d3

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: milky_way_ism, star_formation
- Question: Does the IRS13E complex near Sgr A* contain an intermediate mass black hole, tested by searching for compact, wide-velocity-width ionized gas in H30alpha with ALMA  
  > "We searched such ionized gas with ALMA in order to prove the IMBH hypothesis." (Introduction)
- Target **IRS13E complex (IRS13E3)**: coordinates IRS13E3 offset from Sgr A*: dRA=-3.19", dDec=-1.55"; H30a peak 17h45m39.785s, -29d00'29.84" (ICRS)  
  > "It is located approximately 3.5$\ensuremath{''}$ southwest of Sgr A$^\ast$ in projection ($r=0.13$ pc)" (Introduction); "we adopt 8.0 kpc as the distance to the Galactic center" (Introduction); z/distance 8.0 kpc  
  > "It is located approximately 3.5$\ensuremath{''}$ southwest of Sgr A$^\ast$ in projection ($r=0.13$ pc)" (Introduction); "we adopt 8.0 kpc as the distance to the Galactic center" (Introduction); distance from adopted Galactic center distance (cite: Ghez; Gillessen; Schodel2009; Boehle)  
  > "It is located approximately 3.5$\ensuremath{''}$ southwest of Sgr A$^\ast$ in projection ($r=0.13$ pc)" (Introduction); "we adopt 8.0 kpc as the distance to the Galactic center" (Introduction)

## Data provenance

- ALMA projects: 2015.1.01080.S, 2015.A.00021.S
- bands: 340 GHz continuum; H30alpha at 231.9 GHz rest  
  > "We observed the continuum emission of Sgr A$^\ast$ and the GCMS at 340 GHz" (340 GHz continuum)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 340 GHz: 0.14"x0.13" (natural), 0.101"x0.090" (uniform); H30a: 0.41"x0.30"  
  > "are $0.14\ensuremath{''} \times 0.13\ensuremath{''}, PA=82.5^\circ$ and $0.101\ensuremath{''} \times 0.090\ensuremath{''}, PA=3.8^\circ$, respectively." (340 GHz continuum)
- max recoverable scale: _not stated_
- sensitivity: 340 GHz 1sigma=0.10 (natural) and 0.18 (uniform) mJy/beam; H30a 0.2 mJy/beam  
  > "high sensitivity (0.2 mJy beam$^{-1}$ at a line-free channel)" (H30$\alpha$ recombination line)
- time on source: _not stated_
- observing dates: 340 GHz: 23 Apr, 30/31 Aug, 08 Sep 2016; H30a: 12/13 and 18/19 July 2016  
  > "(23 Apr. 2016, 30/31 Aug. 2016, and 08 Sep. 2016)" (340 GHz continuum); "(12/13 July 2016 and 18/19 July 2016)" (H30$\alpha$ recombination line)
- pi or archival as stated: 340 GHz own Cy.3 program (PI Tsuboi); H30a DDT data released autumn 2016  
  > "We analyzed the DDT observation toward the Galactic Center with ALMA, which was released in the autumn of 2016" (H30$\alpha$ recombination line)
- Line: H30alpha recombination line (231.9 GHz)
- Other facility **Chandra (X-ray catalog)**: X-ray source CXOGCJ174539.7-290029 position and flux from literature  
  > "a discrete X-ray source detected in the IRS 13E complex, CXOGCJ174539.7-290029" (X-ray Counterpart of IRS13E3?)
- External data: IRS13E3 flux density 13.1 mJy at 42 GHz and 34 GHz size 0.08"x0.04"  
  > "Comparing with $S_{\nu {\mathrm 42}}=13.1$ mJy at 42 GHz (cite: Yusef-Zadeh2014)" (Results) [from (cite: Yusef-Zadeh2014)]
- External data: VLBA astrometry limit on second black hole mass  
  > "This indicates that the upper limit mass of the second black hole is $M\lesssim 10^{4}$ M$_\odot$" (The Enclosed Mass of IRS13E3) [from (cite: Reid)]
- External data: X-ray photon flux of the counterpart  
  > "The X-ray photon flux is $F_\mathrm{2-8 keV}=3.092\times10^{-7}$ cm$^{-2}$ s$^{-1}$ at 1999.72 yr" (X-ray Counterpart of IRS13E3?) [from (cite: Muno)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Titan and J1733-1304 (both datasets)  
  > "The flux density scale was determined using Titan and J1733-1304." (340 GHz continuum)
- flux scale uncertainty: _not stated_
- self calibration: self-calibration in CASA applied to 340 GHz data  
  > "We used the self-calibration method in CASA to improve the dynamic range of the map." (340 GHz continuum)

### Imaging

- task: CASA 5.0 tclean  
  > "Imaging for the combined data for the two-day observations was done using CASA 5.0 with `tclean` task" (H30$\alpha$ recombination line)
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 0.5 (H30a); natural and uniform for 340 GHz  
  > "Briggs weighting with a robust parameter of 0.5 was used." (H30$\alpha$ recombination line)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: auto-multithresh auto-boxing  
  > "`usemask=‘auto-multithresh’`" (H30$\alpha$ recombination line)
- multiscale scales: _not stated_
- continuum subtraction: mstransform (fitorder=1) per observing day  
  > "using CASA task, `mstransform (fitorder=1)` for each day of the observations" (H30$\alpha$ recombination line)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.41"x0.30", PA=-77 deg (H30a)  
  > "($0.41\ensuremath{''} \times 0.30\ensuremath{''}, PA = -77^{\circ}$)" (H30$\alpha$ recombination line)
- final rms: 0.2 mJy/beam (H30a line-free channel)  
  > "high sensitivity (0.2 mJy beam$^{-1}$ at a line-free channel)" (H30$\alpha$ recombination line)

### Inherited from earlier work

- Full 340 GHz continuum analysis and improved results deferred to another paper  
  > "We will present the improvement of the analysis and the full results in another paper (cite: Tsuboi2017b)." (340 GHz continuum) [from (cite: Tsuboi2017b)]
- Keplerian orbit PV-diagram morphology  
  > "Such Keplerian orbits have a nearly linear part with large velocity gradient and double curved ridges with relatively small velocity gradient in the position velocity diagram (cite: Tsuboi2017)" (Keplerian Orbit with High Eccentricity around IRS13E3?) [from (cite: Tsuboi2017)]
- Positional errors derived nominally per ALMA Technical Handbook  
  > "The error is derived nominally according to ALMA Technical Handbook (10.6.6)." (Results) [from ALMA Technical Handbook (10.6.6)]

### Not stated but needed to reproduce (our reading)

- Image size, cell size and channel width/line-free channels for H30a cube and continuum fit
- Self-calibration solution intervals and reference datasets
- Number of tclean iterations and thresholds
- Flux scale uncertainty
- Pipeline vs manual calibration and CASA version for calibration
- Orbit model details: how e=0.97 was chosen from PV comparison, and the 650 vs 600 km/s velocity width definition
- Electron temperature/density derivation of gas mass 6e-3 Msun
- Array configurations and time on source

## Analysis recipe

1. **Image 340 GHz continuum and fit compact sources**: Self-calibrated continuum imaging, 2D Gaussian fits in CASA for positions, sizes, fluxes  
  > "The positions and angular sizes of these objects are estimated by the two-dimensional Gaussian fit of CASA (see Table 1)." (Results)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Make H30alpha cube and moment/PV maps**: Continuum subtraction, tclean with auto-multithresh, channel maps (50 km/s), integrated intensity and PV diagram  
  > "The velocity width of the channel maps is $\Delta v=50$ km s$^{-1}$." (Results)
   - software: CASA
   - parameter: robust 0.5; integration -400 to +400 km/s  
  > "integrated velocity range from -400 km s$^{-1}$ to +400 km s$^{-1}$ in $V_{\mathrm {LSR}}$" (Results)
   - fitting: _not stated_
   - validation: Positional agreement of continuum and H30a checked using IRS16NE  
  > "according to the comparison between the 340 GHz continuum and H30$\alpha$ moment 0 positions of IRS16NE" (Compactness of the Ionized Gas toward IRS13E3)
3. **Estimate enclosed mass from Keplerian eccentric orbit**: Compare PV shape with calculated Keplerian orbits to get a and e; mass from M ~ a dV^2 (...)^-2 / G  
  > "The observed velocity width is $\Delta V\sim 600$ km s$^{-1}$, and the enclosed mass of the object is estimated to be $M\sim4-7\times10^{4}$ M$_\odot$" (The Enclosed Mass of IRS13E3)
   - parameter: a~1.4e17 cm, e=0.96-0.98, dV~600 km/s  
  > "for $e=0.96-0.98$ and $a\sim1.4\times10^{17}$ cm" (The Enclosed Mass of IRS13E3)
   - assumption: inclination i~0 deg (edge-on orbit); apoastron PA~60 deg to line of sight  
  > "The inclination angle of the orbit would be $i\sim0^\circ$" (Keplerian Orbit with High Eccentricity around IRS13E3?)
   - fitting: not stated (no formal fit; orbit compared by eye)  
  > "it is difficult to determine exclusively the accurate orbital parameters by fitting in the position velocity diagram because the full orbit is not completely occupied by ionized gas" (Discussion, Keplerian Orbit with High Eccentricity around IRS13E3?)
   - validation: Consistency with VLBA upper limit on second black hole mass  
  > "there is no conflict between our derived enclosed mass and the upper limit mass of the second black hole" (The Enclosed Mass of IRS13E3)
4. **Estimate ionized gas mass and accretion rate**: Gas mass from observation with assumed Te and ne; divide by orbital period  
  > "the upper limit of the mass accretion rate is estimated to be $M/T\lesssim1\times10^{-6}$ M$_\odot$ yr$^{-1}$" (The Enclosed Mass of IRS13E3)
   - assumption: Te~1e4 K, ne~1e6 cm^-3, 1% accretion efficiency  
  > "assuming the electron temperature of $T_{\mathrm e}\sim1\times10^4$ K and the electron density of $n_{\mathrm e}\sim1\times10^6$ cm$^{-3}$" (The Enclosed Mass of IRS13E3)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 5.0 (imaging of H30a): Calibration, imaging, self-calibration, continuum subtraction, Gaussian fits  
  > "The calibration and imaging of both the data were done by Common Astronomy Software Applications (CASA)" (Observation and Data Reduction)
- **tclean** : H30a cube imaging with auto-multithresh  
  > "Imaging for the combined data for the two-day observations was done using CASA 5.0 with `tclean` task" (H30$\alpha$ recombination line)
- **mstransform** : Continuum subtraction (fitorder=1)  
  > "using CASA task, `mstransform (fitorder=1)` for each day of the observations" (H30$\alpha$ recombination line)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| IRS13E3 340 GHz total flux density | 10.5 | 0.5 | mJy | 1 | $S_{\nu {\mathrm 340}}=10.5\pm0.5$ mJy at 340 GHz by the Gaussian fit |
| Spectral index IRS13E3 (42-340 GHz) | ~-0.1 | not stated | dimensionless | 1 | the spectrum index is estimated to be $\alpha=log(S_{\nu {\mathrm 340}}/S_{\nu {\mathrm 42}})/log(340/42)\sim-0.1$ |
| Sgr A* flux density at 340 GHz | 2.8 | not stated | Jy | 1 | the flux density of Sgr A$^\ast$ was $S_\nu=2.8$ Jy at 340 GHz |
| H30a velocity width at IRS13E3 | ~650 | not stated | km/s (FWZI) | 2 | reaches to $\Delta v_{\mathrm{FWZI}} \sim 650$ km s$^{-1}$ |
| Enclosed mass | 4-7e4 | not stated | Msun | 3 | $M\sim4-7\times10^{4}$ M$_\odot$, comparable to the mass of an IMBH, for $e=0.96-0.98$ |
| Orbital eccentricity | ~0.97 | not stated | dimensionless | 3 | the eccentricity of the orbit is estimated to be $e\sim0.97$ |
| Semi-major axis | 1.4e17 cm (1e4 AU) | not stated | cm | 3 | the semi-major axis of the orbit is estimated to be $a\sim1.4\times10^{17}$ cm $=1\times10^4$ AU |
| Ionized gas mass on orbit | 6e-3 | not stated | Msun | 4 | The ionized gas mass on the orbit is estimated to be $M\sim6\times10^{-3}$M$_\odot$ |
| Upper limit accretion rate | 1e-6 | not stated | Msun/yr | 4 | $M/T\lesssim1\times10^{-6}$ M$_\odot$ yr$^{-1}$ |

## Qualitative findings

- Ionized gas is independent of the Eastern and Northern Arms of the minispiral  
  > "The ionized gas would be independent from the NA." (Results)

## Claim tuples

- H: Does IRS13E host compact, wide-velocity ionized gas expected for an IMBH? | E: ALMA H30alpha cube and 340 GHz continuum of IRS13E3 | R: FWZI ~650 km/s with r~400 AU | F: Compactness and large velocity width suggest an IMBH | **partially**
- H: Is the gas on a high-eccentricity Keplerian orbit giving an IMBH-scale mass? | E: Compare PV diagram ridges with Keplerian orbits | R: e~0.97, a~1.4e17 cm, M~4-7e4 Msun | F: Enclosed mass consistent with ~1e4 Msun, below the VLBA limit | **partially**
- H: Does IRS13E3 have an X-ray counterpart? | E: Compare positions with Chandra source | R: Positional difference ~0.2" within uncertainty | F: The X-ray source is considered its counterpart | **partially**

## Reasoning

- Why this data: If an IMBH exists, ALMA can detect ionized gas accreting onto it with large velocity width and compact size  
  > "If the IMBH exists, Atacama Large Millimeter/Submillimetr Array (ALMA) can detect the ionized gas accreting onto the IMBH in the IRS13E complex." (Introduction)
- Why this method: _not stated_
- Alternative: Weak component D as He30alpha counterpart rejected: intensity ratio ~0.3 too high and velocity shift ~-100 km/s less than -122 km/s  
  > "This is too high as $\frac{I(\mathrm {He}30\alpha)}{I(\mathrm {H}30\alpha)}$." (Keplerian Orbit with High Eccentricity around IRS13E3?)
- How they decided it was enough: _not stated_
- Limitation (authors): Orbital parameters cannot be uniquely determined from the PV diagram  
  > "it is difficult to determine exclusively the accurate orbital parameters by fitting in the position velocity diagram" (Keplerian Orbit with High Eccentricity around IRS13E3?)
- Caveat (inferred, ours): Orbit parameters chosen by eye with no fit or uncertainties; mass depends strongly on e
- Caveat (inferred, ours): Size upper limit from continuum is assumed to equal H30a emitting region
- Caveat (inferred, ours): Ionized gas could be a part of the minispiral flow rather than orbiting an IMBH
- Caveat (inferred, ours): X-ray association rests on 0.76" absolute astrometric uncertainty and 1999 data
- Caveat (inferred, ours): Inclination i~0 assumed

## Reproducibility

- Data public (paper): H30a DDT data released publicly in autumn 2016  
  > "which was released in the autumn of 2016" (H30$\alpha$ recombination line)
- Products in archive: _not stated_
- Missing: Imaging grid and channel parameters
- Missing: Self-cal details
- Missing: Orbit model code and fitting procedure
- Missing: Exact velocity width definition
- Data volume (inferred): ~100-300 GB raw for two projects
- Score (inferred): 3/5, Public data and the imaging recipe are partly given; the orbit analysis is by eye and key parameters are missing.
- Rediscovery candidate: no, Main mass result relies on a subjective orbit comparison rather than a reproducible fit.

## Links

- Method: (cite: McMullin) (CASA)
- Companion: (cite: Tsuboi2017b) (Full 340 GHz continuum results, in preparation)
- Companion: (cite: Tsuboi2016) (Finding charts of minispiral structures)

## Checks

```json
{
 "quotes": 63,
 "quotes_ok": 63,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 9,
 "numeric_problems": 0,
 "fill": {
  "facts": 72,
  "stated": 43,
  "rate": 0.597
 },
 "evidence_ok": true
}
```
