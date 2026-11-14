# An Episodic Wide-angle Outflow in HH 46/47

`2019ApJ...883....1Z` | The Astrophysical Journal 2019 | first author: Zhang, Yichen | arXiv: 1908.00689 | DOI: 10.3847/1538-4357/ab3850

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation
- Question: Does the wide-angle wind of the HH 46/47 protostar show episodic outbursts, seen as multiple outflowing shells in 12CO (2-1)?  
  > "we identify multiple wide-angle outflowing shell structures in both the blue and red-shifted outflow lobes." (abstract)
- Target **HH 46/47 (HH 47 IRS)**: coordinates 8h25m43.8s, -51d00m36.0s (J2000), pointing center  
  > "The observations included only one pointing centered at $8^{\mathrm{h}}25^{\mathrm{m}}43^{\mathrm{s}}.8$, $-51^\circ00\ensuremath{'}36\ensuremath{''}.0$ (J2000)" (Observations); "located on the outskirts of the Gum Nebula at a distance of 450 pc" (Introduction); z/distance 450 pc  
  > "The observations included only one pointing centered at $8^{\mathrm{h}}25^{\mathrm{m}}43^{\mathrm{s}}.8$, $-51^\circ00\ensuremath{'}36\ensuremath{''}.0$ (J2000)" (Observations); "located on the outskirts of the Gum Nebula at a distance of 450 pc" (Introduction); distance from Schwartz77; Reipurth00; Noriega04  
  > "The observations included only one pointing centered at $8^{\mathrm{h}}25^{\mathrm{m}}43^{\mathrm{s}}.8$, $-51^\circ00\ensuremath{'}36\ensuremath{''}.0$ (J2000)" (Observations); "located on the outskirts of the Gum Nebula at a distance of 450 pc" (Introduction)

## Data provenance

- ALMA projects: 2015.1.01068.S
- bands: Band 6 (1.3 mm continuum, 12CO 2-1)  
  > "The observations were carried out using ALMA band 6 on Jan 6, 2016" (Observations)
- frequencies and spectral setup: 12CO window 117 MHz wide, ~0.09 km/s resolution, shifted 18 MHz; continuum window 1875 MHz  
  > "a spectral window with a bandwidth of 1875 MHz was used to map the 1.3 mm continuum" (Observations); "observed with a velocity resolution of about 0.09 $\mbox{km s}^{-1}$" (Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: C36-2 (Jan 6, 2016) and C36-4 (June 21, 30, July 6, 2016)  
  > "with the C36-2 configuration and on June 21, 30 and July 6, 2016 with the C36-4 configuration" (Observations)
- baselines: 15-310 m (C36-2); 15-704 m (C36-4)  
  > "the baselines ranged from 15 to 704 m" (Observations)
- angular resolution: 0.67" x 0.48" (CO); 0.65" x 0.47" (continuum)  
  > "The resulting synthesized beam is $0.65\ensuremath{''} \times 0.47\ensuremath{''}$ (P.A. = $87.8^\circ$) for the continuum data" (Observations)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: 75 min (C36-2); 150 min (C36-4)  
  > "The total on source integration time was 75 min." (Observations); "The total integration time was 150 min." (Observations)
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: 12CO 2-1 (230.54 GHz)
- External data: Cloud LSR velocity 5.3 km/s  
  > "which is 5.3 $\mbox{km s}^{-1}$" (Observations) [from vanKempen09]
- External data: Optical jet inclinations 34±3 and 37.5±2.5 deg  
  > "which are $34^\circ\pm3^\circ$ and $37^\circ.5\pm2^\circ.5$, respectively" (Discussion) [from Eisloffel94; Hartigan05]

## Processing

### Calibration

- pipeline or manual: Calibrated in CASA 4.5.3  
  > "The data were calibrated and imaged in CASA ((cite: McMullin07); version 4.5.3)." (Observations)
- casa version: 4.5.3  
  > "version 4.5.3" (Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: Applied using continuum data after normal calibration  
  > "Self-calibration was applied by using the continuum data after normal calibration." (Observations)

### Imaging

- task: CLEAN  
  > "The task CLEAN was used to image the data." (Observations)
- deconvolver: _not stated_
- weighting robust: robust = 0.5  
  > "Robust weighting with a robust parameter of 0.5 was used in the CLEAN process." (Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: Different clean region for each channel  
  > "For the spectral data we defined a different clean region for each channel." (Observations)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.67" x 0.48", PA 88.2 deg (CO)  
  > "$0.67\ensuremath{''} \times 0.48\ensuremath{''}$ (P.A. = $88.2^\circ$) for the $^{12}\mbox{CO}$ data" (Observations)
- final rms: _not stated_

### Inherited from earlier work

- Pointing center taken from the 3 mm continuum peak of Cycle 1 observations  
  > "which is the 3mm continuum peak obtained from the Cycle 1 observations (Paper II)" (Observations) [from Paper II (Zhang16)]
- Excitation temperature of 15 K  
  > "Following Paper II, we adopt an excitation temperature of $T_\mathrm{ex}=15~{\rm K}$." (Discussion) [from Paper II (cite: Zhang16)]
- Parabolic shell model  
  > "Following the method by (cite: Lee00), the morphology and velocity of a single expanding parabolic shell can be described" (Discussion) [from (cite: Lee00)]
- Central mass 0.3 Msun  
  > "assuming a mass of $0.3~M_\odot$ for the central object (see Paper II)" (Implications for Wind Launching) [from Paper II]

### Not stated but needed to reproduce (our reading)

- Line-free channels and continuum subtraction method
- Cell and image size, clean threshold, cleaning niter
- Self-calibration solution intervals
- Which calibrators were used for each execution (list contains a repeated name)
- Exact channel width of the imaged cubes
- Outflow axis position angle used for PV cuts
- Mask/threshold used to isolate shell emission for mass and momentum

## Analysis recipe

1. **Calibrate and image CO and continuum**: CASA calibration, self-calibration on continuum, CLEAN per-channel masks  
  > "The data were calibrated and imaged in CASA ((cite: McMullin07); version 4.5.3)." (Observations)
   - software: CASA
   - parameter: robust = 0.5  
  > "Robust weighting with a robust parameter of 0.5 was used in the CLEAN process." (Observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **Identify shells in PPV, channel maps and PV diagrams**: Visual identification of coherent shell structures in channel maps, PPV and PV cuts along and perpendicular to outflow axis  
  > "The shell structures are best seen in the position-position-velocity (PPV) diagrams (Figure [2](#fig:PPV)), where they appear to be highly coherent in space and velocity." (Results)
   - fitting: _not stated_
   - validation: _not stated_
3. **Fit expanding parabolic shell models**: Grid search of i, t0, R0 for shells compared to channel maps and PV diagrams; location only, not intensity  
  > "Here we only focus on the location of the emission in space and velocity, and do not attempt to reproduce the intensity distribution." (Discussion)
   - parameter: i 30-45 deg step 5; t0 0.05-1 arcsec km-1 s step 0.05; R0 1-3 arcsec step 0.01  
  > "the inclination $i$ is searched within a range $30^\circ\leq i \leq 45^\circ$ with an interval of $5^\circ$" (Discussion)
   - assumption: Same inclination for shells in the same lobe; distance 450 pc for ages  
  > "we adopt a constant inclination angle for shells in the same lobe" (Discussion)
   - fitting: Grid search, best fit chosen by visual comparison  
  > "The best-fit models are selected by visually comparing the model curves" (Discussion)
   - validation: Inclinations compared with optical jet values  
  > "These are consistent with the values derived from observations of the optical (blue-shifted) jet" (Discussion)
4. **Estimate shell mass, momentum and rates**: Optically thin CO mass per channel, summed above 3 sigma with primary beam response >0.2, excluding |vout|<2 km/s  
  > "we only include the primary beam corrected emission above $3\sigma$ and within a primary beam response greater than $0.2$ relative to the phase center" (Discussion)
   - parameter: Tex=15 K  
  > "we adopt an excitation temperature of $T_\mathrm{ex}=15~{\rm K}$" (Discussion)
   - assumption: 12CO abundance 1e-4 relative to H2; 2.34e-24 g per H2  
  > "adopt an abundance of $^{12}$CO of $10^{-4}$ relative to H$_2$ and a gas mass of $2.34\times10^{-24}$ g per H$_2$ molecule" (Discussion)
   - fitting: _not stated_
   - validation: Tex=50 K would raise mass by factor 1.5  
  > "An excitation temperature of 50 K would increase the mass estimate by a factor of 1.5." (Discussion)

## Software

- **CASA** 4.5.3: Calibration, self-calibration and imaging  
  > "The data were calibrated and imaged in CASA ((cite: McMullin07); version 4.5.3)." (Observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Best-fit inclination blue lobe | 40 | not stated | deg | 3 | Sb1 / $40^\circ$ |
| Best-fit inclination red lobe | 35 | not stated | deg | 3 | $i=35^\circ$ between the outflow axis and the plane of sky for the blue-shifted and red-shifted outflows |
| Age difference Sr1-Sr2 | 2.1e2 | not stated | yr | 3 | $2.1\times 10^2~\mathrm{yr}$ |
| Age difference Sb1-Sb2 | 3.2e2 | not stated | yr | 3 | $3.2\times 10^2~\mathrm{yr}$ |
| Shell mass, blue and red | 5.6e-3 and 1.0e-2 | not stated | Msun | 4 | total mass of $5.6\times 10^{-3}$ and $1.0\times 10^{-2}~M_\odot$ |
| Shell momentum, blue and red | 4.4e-2 and 8.7e-2 | not stated | Msun km/s | 4 | momentum of $4.4\times 10^{-2}$ and $8.7\times 10^{-2}~M_\odot~\mbox{km s}^{-1}$ |
| Time-averaged mass outflow rate, blue and red | 3.1e-6 and 1.8e-5 | not stated | Msun/yr | 4 | $3.1\times10^{-6}$ and $1.8\times10^{-5}~M_\odot~{\rm yr}^{-1}$ |
| Launching radius from outburst interval | 10-13 | not stated | au | 0 | The resultant radius is $10-13$ au |

## Qualitative findings

- Multiple coherent wide-angle shells exist in both lobes, consistent with entrainment by an episodic wide-angle wind; shells are not formed by direct launching.  
  > "Our results provide strong evidence that wide-angle disk winds can be episodic, just as protostellar jets." (Conclusions)

## Claim tuples

- H: Wide-angle wind in HH 46/47 is episodic | E: Identify and fit parabolic shells in 12CO (2-1) PPV and PV data | R: At least two shells per lobe with age spacing of 210-320 yr | F: Shells arise from repeated wide-angle wind outbursts matching the jet knot interval | **supported**
- H: Shells are entrained ambient gas rather than launched material | E: Compare shell mass and momentum rates to jet/wind values | R: Mass rates 1-2 orders higher, momentum rates similar | F: Shells are mostly entrained material | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Jet bow-shock entrainment judged unlikely for the shells, though not ruled out.  
  > "we think these shells are unlikely to be formed by jet entrainment" (Origin of the Multiple Shell Structure)
- How they decided it was enough: _not stated_
- Limitation (authors): Dynamical ages may be upper limits; mass and momentum are lower limits  
  > "it is likely that the estimated dynamical ages are upper limits of their true ages." (Origin of the Multiple Shell Structure)
- Caveat (inferred, ours): Best-fit selection by eye with no uncertainties on parameters
- Caveat (inferred, ours): Shell identification is subjective
- Caveat (inferred, ours): Single pointing truncates the outflow at ~20 arcsec

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Imaging parameters beyond robust
- Missing: Quantitative fit uncertainties
- Missing: Axis and PV cut definitions
- Data volume (inferred): ~50-100 GB raw
- Score (inferred): 3/5, Data are from a single project and the basic imaging is described, but the shell fitting is visual and many parameters are missing.
- Rediscovery candidate: no, Main results depend on visual shell identification and by-eye fitting, and the public status of the data is not stated in the paper.

## Links

- Method: Lee00 (Parabolic shell model)
- Companion: Arce13 (Paper I) (Earlier ALMA 12CO (1-0) observations of the outflow)
- Companion: Zhang16 (Paper II) (Earlier ALMA 12CO (1-0) observations of the outflow)

## Checks

```json
{
 "quotes": 57,
 "quotes_ok": 57,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 70,
  "stated": 39,
  "rate": 0.557
 },
 "evidence_ok": true
}
```
