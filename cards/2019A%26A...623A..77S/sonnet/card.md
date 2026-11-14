# Discovery of a sub-Keplerian disk with jet around a 20 M<SUB>☉</SUB> young star. ALMA observations of G023.01-00.41

`2019A&A...623A..77S` | Astronomy and Astrophysics 2019 | first author: Sanna, A. | arXiv: 1805.09842 | DOI: 10.1051/0004-6361/201833411

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, astrochemistry
- Question: Is there a disk-jet system around the 20 Msun O-type young star in G023.01-00.41, and is the disk gas in centrifugal equilibrium (Keplerian) or infalling/sub-Keplerian?  
  > "we seek to simultaneously resolve the spatial morphology of the disk and the regions where the jet originates, and to determine whether or not the disk gas is in centrifugal equilibrium." (Introduction)
- Target **G023.01-00.41 (HMC)**: coordinates RA 18:34:40.290, Dec -09:00:38.30 (J2000, phase center)  
  > "at a parallax distance of 4.6 kpc (cite: Brunthaler2009)" (Introduction); "18:34:40.290 | –09:00:38.30" (Table 1); z/distance 4.6 kpc  
  > "at a parallax distance of 4.6 kpc (cite: Brunthaler2009)" (Introduction); "18:34:40.290 | –09:00:38.30" (Table 1); distance from parallax (Brunthaler2009)  
  > "at a parallax distance of 4.6 kpc (cite: Brunthaler2009)" (Introduction); "18:34:40.290 | –09:00:38.30" (Table 1)

## Data provenance

- ALMA projects: 2015.1.00615.S
- bands: Band 6 (211–275 GHz)  
  > "with the 12 m-array of ALMA in band 6 (211–275 GHz)" (2 Observations and calibration)
- frequencies and spectral setup: 12 narrow spws of 234 MHz (960 channels, Hanning smoothed, 0.7 km/s) plus one 1875 MHz wide band (3840 channels, centered 217.860 GHz)  
  > "to record 12 narrow spectral windows, each 234 MHz wide, and an additional wide band of 1875 MHz." (2 Observations and calibration); "The wide band was correlated with 3840 channels and centered at a rest frequency of 217.860 GHz." (2 Observations and calibration)
- continuum bandwidth: _not stated_
- arrays: 12 m array, 45 antennas  
  > "The 12 m-array observed with 45 antennas covering a baseline range between 16 m and 3143 m" (2 Observations and calibration)
- configurations: C36-6  
  > "C36–6" (Table 1)
- baselines: 16 m to 3143 m  
  > "covering a baseline range between 16 m and 3143 m" (2 Observations and calibration)
- angular resolution: 0.2 arcsec  
  > "with the aim to achieve an angular resolution of $0.2\ensuremath{''}$" (2 Observations and calibration)
- max recoverable scale: 2 arcsec  
  > "to recover extended emission over a maximum scale of $2''$" (2 Observations and calibration)
- sensitivity: ~2 mJy/beam per narrow channel (1.4 K) expected; continuum S/N about 100  
  > "thermal rms per (narrow) spectral channel of about 2 mJy beam$^{-1}$ (with 36 antennas)" (2 Observations and calibration)
- time on source: 1 hour on source, 2 hours total  
  > "We spent 1 hour of time on-source during a total observing time of 2 hours" (2 Observations and calibration)
- observing dates: 2016 September 5 and 16  
  > "on 2016 September 5 and 16 (Cycle 3)" (2 Observations and calibration)
- pi or archival as stated: _not stated_
- Line: CH3OH 4(2,2)-3(1,2) E (218.4400 GHz)
- Line: CH3OH 10(2,8)-9(3,7) A+ (232.4186 GHz)
- Line: CH3OH 18(3,16)-17(4,13) A+ (232.7835 GHz)
- Line: CH3CN 12(3)-11(3) (220.7090 GHz)
- Line: CH3CN 12(4)-11(4) (220.6793 GHz)
- Other facility **SMA**: Previous 1 mm observations used to set requirements for ALMA  
  > "We made use of our previous Submillimeter Array (SMA) observations at 1 mm (cite: Sanna2014)" (2 Observations and calibration)
- Other facility **VLA**: Radio continuum/jet position and orientation from earlier work  
  > "the peak position of the radio continuum emission observed with the Very Large Array at the same resolution as the ALMA beam (cite: Sanna2016)" (3 Results)
- External data: Outflow axis position angle +57 deg  
  > "which lies at a position angle of $+57^{\circ}$ on the sky plane (cite: Sanna2016)" (3 Results) [from Sanna2016]
- External data: HMC luminosity 4e4 Lsun  
  > "The HMC emits a luminosity of 4 $\times$ $10^4$ L$_{\odot}$ (cite: Sanna2014)" (Introduction) [from Sanna2014]
- External data: Average CH3CN rotational temperature 195 K from LTE analysis  
  > "(average) rotational temperature (195 K) of the CH$_3$CN ($12_{\rm K}$–$11_{\rm K}$) spectra" (6 Disk model) [from Sanna2014]
- Simulation/model as data: Semi-analytic disk model (RADMC-3D) for a 20 Msun star, infalling and Keplerian velocity fields, observed with CASA simobserve/simanalyze in config alma.cycle3.6.cfg  
  > "processed in CASA with the tasks “simobserve” and “simanalyze”, in order to produce synthetic maps with the same ALMA configuration (alma.cycle3.6.cfg)" (6 Disk model)

## Processing

### Calibration

- pipeline or manual: CASA pipeline calibration scripts  
  > "making use of the pipeline calibration scripts" (2 Observations and calibration)
- casa version: CASA 4.7.1 (r39339)  
  > "version 4.7.1 (r39339)" (2 Observations and calibration)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J1733-1304 (bandpass J1751+0939, phase J1851+0035)  
  > "J1751$+$0939 | J1851$+$0035 | J1733$-$1304" (Table 1)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA clean  
  > "We imaged the line and continuum emission with the task *clean* of CASA." (2 Observations and calibration)
- deconvolver: _not stated_
- weighting robust: Briggs robust 0.5 for continuum and CH3OH 218.44 GHz; robust 0 for other lines  
  > "DUST CONTINUUM | 217.8240 | ... | R0.5 | 0.207 | 0.16 | 14.63" (Table 2)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: uvcontsub, fitorder=0, per spectral window  
  > "The task *uvcontsub* of CASA was used to subtract a constant continuum level across the spectral window (*fitorder* $=$ 0)." (2 Observations and calibration)
- line free channels: selected from spectrum integrated over a 2 arcsec circular box on the target, in pipeline cubes (channel ranges not given)  
  > "selected the line-free channels from a spectrum integrated over a circular box of $2''$ in size" (2 Observations and calibration)
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: Circular beams 0.207" (continuum), 0.184" (CH3OH 218 GHz), 0.155" (other lines)  
  > "Column 5 reports the restoring (circular) beam size, set equal to the geometrical average of the major and minor axes of the dirty beam size." (Table 2)
- final rms: Continuum 0.16 mJy/beam; lines 1.0–3.4 (see Table 2)  
  > "DUST CONTINUUM | 217.8240 | ... | R0.5 | 0.207 | 0.16 | 14.63" (Table 2)

### Inherited from earlier work

- Disk density and temperature at 500 au  
  > "1.0\times10^{-15}$ g cm$^{-3}$ and 300 K at a radius R$_0=500$ au, following (cite: Kuiper2013)" (6 Disk model) [from Kuiper2013]
- Density and temperature power-law exponents -1.5 and -0.4  
  > "Their respective exponents, *a* and *t*, are $-1.5$ and $-0.4$, following (cite: Gerner2014)." (6 Disk model) [from Gerner2014]
- Disk mass from continuum following Hildebrand  
  > "Following (cite: Hildebrand1983), we estimate the disk mass from the continuum flux of 62.9 mJy within the 20% contour." (4.2 Disk mass) [from Hildebrand1983]

### Not stated but needed to reproduce (our reading)

- Line-free channel ranges for continuum and uvcontsub
- Clean masks, niter and threshold, cell and image size
- Velocity ranges and moment-map settings
- Exact algorithm for the 60% contour Gaussian fit and deconvolution
- Model power-law abundance exponent q and the model velocity prescriptions (inner/outer cutoffs, v_ff fraction) details for reproduction
- Simobserve integration time/thermal noise settings
- Flux calibrator flux values and pipeline version

## Analysis recipe

1. **Calibrate and image line and continuum data**: CASA pipeline calibration, uvcontsub, clean  
  > "The visibility data were calibrated with the Common Astronomy Software Applications (CASA) package, version 4.7.1 (r39339)" (2 Observations and calibration)
   - software: CASA
   - parameter: Briggs robust 0 or 0.5; continuum from 218 MHz line-free bandwidth  
  > "we integrated over a line-free bandwidth of 218 MHz selected from the wide spectral window" (2 Observations and calibration)
   - fitting: _not stated_
   - validation: Image rms compared with ALMA sensitivity calculator, ratio near unity  
  > "the ratio between the image rms and the thermal noise, expected from the ALMA sensitivity calculator, is near unity" (2 Observations and calibration)
2. **Map disk morphology and kinematics**: Moment maps and channel maps of CH3OH; Gaussian fit of emission within the 60% contour to get disk size and axis ratio; stellar velocity from the median of two channel-map transitions  
  > "These values are calculated by Gaussian fitting the CH$_3$OH emission within the 60% contour level" (3 Results)
   - parameter: disk plane PA -33 deg; outflow axis PA +57 deg  
  > "along a position angle of $-33^{\circ}$ on the sky plane (measured east of north)" (3 Results)
   - fitting: _not stated_
   - validation: Star position chosen to maximize symmetry of blue and red sides  
  > "The position of the central star was set as to maximize the symmetry of the blue- and redshifted sides of the disk" (3 Results)
3. **Build a radiative transfer disk model and compare pv-diagrams**: Semi-analytic disk, RADMC-3D ray-tracing in LTE, observed with simobserve/simanalyze; pv-diagrams along the disk plane compared for infalling (70% free-fall) and Keplerian velocity fields  
  > "the gas is moving radially at $70\%$ of the corresponding free-fall velocity" (4.1 Position-velocity diagrams)
   - software: RADMC-3D, CASA
   - parameter: H/R=0.1, inclination 10 deg, 20 Msun, CH3CN abundance 2e-8 at 500 au, grid 152x20  
  > "We set a CH$_3$CN abundance relative to H$_2$ of $2\times10^{-8}$ at 500 au" (6 Disk model)
   - assumption: Gas-to-dust 100, dust opacity 1.0 cm2/g at 1.3 mm, dust and gas temperature equal, LTE  
  > "with a gas-to-dust mass ratio of 100 and a dust opacity of 1.0 cm$^2$ g$^{-1}$ at 1.3 mm" (6 Disk model)
   - fitting: _not stated_
   - validation: Modeled peak dust and line brightness compared to observed  
  > "the modeled peak brightness of both the CH$_3$CN line and the dust continuum coincides with the observed values." (6 Disk model)
4. **Estimate disk mass from dust continuum**: Optically thin dust mass from 62.9 mJy within 20% contour, compared with model mass  
  > "we estimate the disk mass from the continuum flux of 62.9 mJy within the 20% contour." (4.2 Disk mass)
   - parameter: T = 279 K averaged from model between 10 and 2000 au  
  > "We use an average gas temperature of 279 K, determined from the model between radii of 10 au and 2000 au" (4.2 Disk mass)
   - assumption: gas-to-dust 100, kappa 1.0 cm2/g at 1.3 mm (Ossenkopf1994), distance 4.6 kpc  
  > "assume a standard gas-to-dust mass ratio of 100 and a dust opacity of 1.0 cm$^2$ g$^{-1}$ at 1.3 mm (cite: Ossenkopf1994)" (4.2 Disk mass)
   - fitting: _not stated_
   - validation: Agreement with model mass 1.4 Msun at 2000 au  
  > "Our model predicts a disk mass of 2.5 M$_{\odot}$ within a radius of 3000 au, which decreases to 1.4 M$_{\odot}$ at 2000 au." (4.2 Disk mass)

## Software

- **CASA** 4.7.1 (r39339): Calibration, uvcontsub, clean imaging, simobserve/simanalyze  
  > "The task *uvcontsub* of CASA was used to subtract a constant continuum level" (2 Observations and calibration)
- **RADMC-3D** : Radiative transfer of the disk model  
  > "usable for the radiative transfer code RADMC-3D (cite: Dullemond2012)" (6 Disk model)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Deconvolved CH3OH disk radius | 2380 | ±840 | au | 2 | extends up to a deconvolved radius of 2380 $\pm$ 840 au (or 520 mas) |
| Disk minor-to-major axis ratio | 0.2 | not stated | dimensionless | 2 | has a ratio between the minor-to-major axes of 0.2 |
| Stellar rest velocity | +79.1 | ±0.4 | km/s | 2 | is set to $+79.1$ km s$^{-1}$ with an uncertainty of $\pm$ 0.4 km s$^{-1}$ |
| Jet width | 1510 | ±73 | au | 2 | The jet width of 1510 $\pm$ 73 au (or 329 mas) |
| Mass infall rate at 500 au | 6e-4 | not stated | Msun/yr | 3 | Our model predicts a mass infall rate at a radius of 500 au of $6\times10^{-4}$ M$_{\odot}$ yr$^{-1}$. |
| Disk mass from dust continuum | 1.6 | ±0.3 | Msun | 4 | we calculate a disk mass of 1.6 M$_{\odot}$ and assign an uncertainty of $\pm$ 0.3 M$_{\odot}$ |
| Continuum flux within 20% contour | 62.9 | not stated | mJy | 4 | continuum flux of 62.9 mJy within the 20% contour |
| Continuum peak | 14.63 | rms 0.16 | mJy/beam | 1 | DUST CONTINUUM / 217.8240 / ... / R0.5 / 0.207 / 0.16 / 14.63 |

## Qualitative findings

- Disk gas is infalling near free-fall and sub-Keplerian outside ~500 au; Keplerian-like rotation possible only inside  
  > "gas is falling in close to free-fall, and slowly rotating with sub-Keplerian velocities" (1 Introduction)
- A compact blueshifted molecular jet is detected from inner disk (<800 au); the redshifted lobe is not seen, interpreted as optically thick inner disk  
  > "we do not detect the redshifted lobe of the jet" (4.1 Position-velocity diagrams)

## Claim tuples

- H: A disk perpendicular to the outflow exists around the O-type YSO | E: CH3OH moment maps and channel maps | R: Flattened structure to ~2380 au with velocity gradient along major axis | F: A disk is present, warped in outer regions | **supported**
- H: Disk gas is in centrifugal equilibrium | E: Compare observed CH3CN pv-diagram with infalling and Keplerian RADMC-3D models | R: Infall profile reproduces forbidden quadrants; Keplerian only needed at inner radii | F: Gas is infalling and sub-Keplerian outside ~500 au | **supported**
- H: The disk mass is small relative to the star | E: Dust continuum mass estimate and model | R: 1.6 ± 0.3 Msun vs model 1.4 Msun at 2000 au | F: Disk mass ~10% of the stellar mass | **supported**

## Reasoning

- Why this data: SMA data used to set requirements for higher-resolution ALMA observations  
  > "to set up the requirements for higher resolution observations with ALMA" (2 Observations and calibration)
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Inner regions sampled by only two beams; inner Keplerian possibility speculative  
  > "the inner regions are sampled by only two beams with the current resolution" (4.1 Position-velocity diagrams)
- Limitation (authors): Model does not include envelope and uses simple power laws  
  > "the model does not account for a dusty envelope surrounding the disk" (4.2 Disk mass)
- Caveat (inferred, ours): Model comparison is by eye with no quantitative fit or uncertainty on infall fraction
- Caveat (inferred, ours): Stellar mass fixed from luminosity, so rotation/infall degeneracy not tested
- Caveat (inferred, ours): Outflow contamination of CH3OH/CH3CN pv-diagrams complicates the interpretation
- Caveat (inferred, ours): Disk mass depends on assumed opacity and temperature

## Reproducibility

- Data public (paper): Data from ALMA program 2015.1.00615.S cited in acknowledgements  
  > "This study makes use of the following ALMA data: ADS/JAO.ALMA$\#$2015.1.00615.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Model velocity-field implementation and RADMC-3D inputs
- Missing: Imaging masks and cleaning parameters
- Missing: Line-free channel ranges
- Data volume (inferred): ~50-100 GB raw, a few tens of GB of products
- Score (inferred): 3/5, Public data and clear numeric results, but model and imaging details are incomplete
- Rediscovery candidate: no, Key conclusions depend on a custom by-eye model comparison lacking full specification.

## Links

- Method: Sanna2014 (Previous SMA study of the source, LTE analysis)
- Method: Sanna2016 (Radio jet and outflow axis)
- Companion: Johnston2015 (Comparison disk in AFGL 4176)

## Checks

```json
{
 "quotes": 76,
 "quotes_ok": 76,
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
  "facts": 76,
  "stated": 54,
  "rate": 0.711
 },
 "evidence_ok": true
}
```
