# Chemical Evolution along the Circumnuclear Ring of M83

`2019ApJ...884..100H` | The Astrophysical Journal 2019 | first author: Harada, Nanase | arXiv: 1909.01549 | DOI: 10.3847/1538-4357/ab41ff

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, astrochemistry
- Question: How does the chemistry of molecular gas change along the circumnuclear ring of M83 as gas flows from bar lanes into the ring, and does it indicate collision-induced star formation?  
  > "We propose that the observed chemical variation or lack of it is due to the presence or absence of collision-induced evolution of molecular clouds and induced star formation." (abstract)
- Target **M83 circumnuclear ring**: coordinates Analysis positions N1 at 13h37m00.745s -29d51m43.752s (ICRS); 12 positions listed in Table 3  
  > "We targeted the entire circumnuclear ring, and we mosaicked the area of $25\ensuremath{''} \times 25\ensuremath{''}$" (Observations and data reduction); "| N1 | 13h37m00.745s | -29d51m43.752s |" (Table 3); z/distance not stated (22 pc per arcsec implied: 2.8'' = 62 pc)  
  > "We targeted the entire circumnuclear ring, and we mosaicked the area of $25\ensuremath{''} \times 25\ensuremath{''}$" (Observations and data reduction); "| N1 | 13h37m00.745s | -29d51m43.752s |" (Table 3); distance from _not stated_

## Data provenance

- ALMA projects: 2016.1.00164.S, 2012.1.00762.S, 2015.1.01177.S
- bands: Bands 3, 6, 7  
  > "The absolute flux calibration is accurate to 5 % for ALMA Bands 3, 6, and 7" (Observations and data reduction)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: 12-m and 7-m arrays (2012.1.00762.S includes 7-m; 2015.1.01177.S 12-m only)  
  > "The former obervations included the 7-m array while the latter only had the 12-m array." (Observations and data reduction)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: beams ~1.2-2.7'' per line (Table 2); analysis at 2.8'' (62 pc)  
  > "This analysis used data cubes convolved to 2.8$''$ (62 pc), which is the lowest resolution in our data." (Molecular abundances)
- max recoverable scale: at least 16'' in Band 7  
  > "The maximum recoverable scale is at least 16$''$ in our Band 7 observations" (Observations and data reduction)
- sensitivity: rms 0.3-4.4 mJy/beam per 10 km/s channel (Table 2)  
  > "RMS noise is measured for cubes with $\Delta v = 10$ km s$^{-1}$ before the primary beam correction." (Table 2 notes)
- time on source: _not stated_
- observing dates: 2013-2017 (Table 1)  
  > "| 12m | C40-1 | 2017-03-11 | 38 |" (Table 1)
- pi or archival as stated: _not stated_
- Line: 13CO 1-0, 2-1 (110.201, 220.399 GHz)
- Line: SiO 2-1 (86.847 GHz)
- Line: N2H+ 1-0, 3-2 (93.172, 279.512 GHz)
- Line: CH3OH 2k-1k, 5k-4k (96.741, 241.791 GHz)
- Line: H41alpha RRL (92.034 GHz)
- Line: CN, CCH, CS, HNCO, HC3N, CH3CN, CH3CCH, H2CO, C18O, C17O, HNC multiple (see Table 2)
- Other facility **IRAM 30m**: 3-mm line survey used to assess missing flux in Band 3  
  > "comparing our line fluxes with those from the IRAM 30-meter line survey in the 3-mm band by (cite: 2015A&A...579A.101A)" (Observations and data reduction)
- External data: IRAM 30m 3-mm line fluxes for flux recovery  
  > "comparing our line fluxes with those from the IRAM 30-meter line survey in the 3-mm band by (cite: 2015A&A...579A.101A)" (Observations and data reduction) [from (cite: 2015A&A...579A.101A)]
- External data: Inclination 24 deg  
  > "With the inclination angle of 24$^{\circ}$(cite: 1981A&AS...44..441C)" (4.2.1 Orbital timescale) [from (cite: 1981A&AS...44..441C)]
- External data: Bar pattern speed 57±3 km/s/kpc  
  > "the pattern speed of the bar $\Omega_{p}$ is $57\pm3$ km s$^{-1}$ kpc$^{-1}$ (cite: 2014PASJ...66...46H)" (4.2.1 Orbital timescale) [from (cite: 2014PASJ...66...46H)]

## Processing

### Calibration

- pipeline or manual: CASA pipeline  
  > "Measurement sets were calibrated with the CASA pipeline versions 4.6, 4.7 or 4.7.2." (Observations and data reduction)
- casa version: _not stated_
- pipeline version: CASA pipeline 4.6, 4.7 or 4.7.2  
  > "Measurement sets were calibrated with the CASA pipeline versions 4.6, 4.7 or 4.7.2." (Observations and data reduction)
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: 5% for ALMA Bands 3, 6, 7  
  > "The absolute flux calibration is accurate to 5 % for ALMA Bands 3, 6, and 7" (Observations and data reduction)
- self calibration: _not stated_

### Imaging

- task: tclean in CASA 5.4  
  > "Imaging was conducted with CASA version 5.4 using the task tclean" (Observations and data reduction)
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: uvtaper = 1arcsec for CCH(1-0) and SiO(2-1)  
  > "Data of CCH($N=1-0$) and SiO($2-1$) were tapered with the CASA parameter uvtaper = 1arcsec." (Table 2 notes)
- cell size: _not stated_
- image size: _not stated_
- masking: Moment 0: masked 13CO emission below 5 sigma per channel  
  > "we masked out the region with $^{13}$CO emission below 5 $\sigma$ in each velocity channel." (Velocity-integrated intensity maps)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: Applied before ratio maps, after 6 sigma cutoff  
  > "The image division for ratio was then performed after applying a cutoff at $6\sigma$ and correction for the primary beam to each convolved image." (3.2 Spatial variation)
- array combination: _not stated_
- smoothing: Cubes smoothed to 10 km/s (CN 1-0 to 10.6 km/s); convolved to 2.8'' for analysis  
  > "All the cubes were smoothed to 10 km s$^{-1}$ resolution except for CN(1-0) lines smoothed to 10.6 km s$^{-1}$." (Observations and data reduction)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- 2012.1.00762.S cubes created with the reduction of Hirota et al. 2018, smoothed to 10.6 km/s  
  > "The data cubes from 2012.1.00762.S were created in the data reduction procedure described in (cite: 2018PASJ...70...73H)" (Observations and data reduction) [from (cite: 2018PASJ...70...73H)]
- MADCUBA software description  
  > "We used the MADCUBA software (S. Martín et al., 2019, submitted)" (3.3 Molecular abundances) [from S. Martín et al., 2019, submitted]

### Not stated but needed to reproduce (our reading)

- tclean weighting/robust, cell size, image size, deconvolver, threshold and masks
- Continuum subtraction method and line-free channels
- How 7-m and 12-m data were combined
- MADCUBA fitting setup: line widths, velocity components, priors, source size/beam filling assumed
- Distance to M83 and conversion to pc/arcsec
- Self-calibration, if any
- Exact beam-matching details between lines for 2.8'' convolution
- Spectrum extraction aperture for the 12 positions

## Analysis recipe

1. **Image cubes and moment maps**: tclean imaging, smoothing to 10 km/s, moment 0 with 13CO-based mask via immoments  
  > "velocity-integrated intensity maps were created with the task immoments" (Velocity-integrated intensity maps)
   - software: CASA
   - fitting: _not stated_
   - validation: Flux recovery vs IRAM 30m for Band 3 lines, >70% for most  
  > "Most lines have the flux recovery rates higher than 70 % except for CH$_3$CCH (63 %) and HNCO (65 %)." (Observations and data reduction)
2. **Line intensity ratio maps vs 13CO(1-0)**: Convolve pairs to the larger beam, apply 6 sigma cutoff and primary beam correction, divide  
  > "The two images for each ratio map were next convolved to the largest beam among the two images." (3.2 Spatial variation)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
3. **LTE column densities and Tex at 12 positions**: Fit spectra under LTE with MADCUBA at 2.8'' resolution; assumed Tex for single-transition species  
  > "We derived column densities of species by fitting the spectra at our twelve sampling positions under the assumption of the local thermodynamic equilibrium (LTE)." (3.3 Molecular abundances)
   - software: MADCUBA
   - parameter: Assumed Tex: CS 8±2 K, CCH 3.5±1.5 K, N2H+ 6±1 K, H2CO 20±10 K, HC3N 15±10 K, CH3CCH 20±10 K  
  > "CS: $8 \pm 2$ K, CCH: $3.5 \pm 1.5$ K, N$_2$H$^+$: $6\pm1$ K, H$_2$CO: $20 \pm 10$ K, HC$_3$N: $15 \pm 10$ K, CH$_3$CCH: $20 \pm 10$ K" (3.3 Molecular abundances)
   - assumption: H2CO ortho-to-para ratio 3; 13CO fractional abundance constant among positions; C17O Tex similar to C18O and 13CO  
  > "we used the ortho-to-para ratio of 3, which is the value of the statistical weight." (3.3 Molecular abundances)
   - fitting: _not stated_
   - validation: _not stated_
4. **Fractional abundance trends along streams**: Column density ratios over 13CO, normalized to N3, for N1-5, S1-5, C1-2; intensity ratios for single-transition species and H41alpha  
  > "we refer to the column density ratios as fractional abundances" (3.3 Molecular abundances)
   - fitting: _not stated_
   - validation: _not stated_
5. **Orbital and collision timescales**: Orbital period from moment 1 velocity, radius, inclination and bar pattern speed; collision time from mean free path of clouds  
  > "The orbital period $\tau$ is obtained as $\tau = \frac{2\pi}{\Omega - \Omega_{p}} = 10 \pm 2$ Myr." (4.2.1 Orbital timescale)
   - assumption: Galactic GMC R=20 pc, M=1.5e5 Msun; N13CO=1e-6 NH2; inclination 24 deg  
  > "Assuming the $N_{13CO} = 10^{-6} N_{H2}$, $R_{cl} = 20$ pc, and $M_{cl}= 1.5 \times 10^5$ $M_{\odot}$" (Estimate of collision frequency)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** pipeline 4.6/4.7/4.7.2; imaging 5.4: Calibration, tclean imaging, immoments  
  > "Imaging was conducted with CASA version 5.4 using the task tclean" (Observations and data reduction)
- **MADCUBA** : LTE spectral fitting for column densities and Tex  
  > "We used the MADCUBA software (S. Martín et al., 2019, submitted)" (3.3 Molecular abundances)
- **APLpy** : Plotting  
  > "This research made use of APLpy, an open-source plotting package for Python" (Acknowledgments)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Orbital period of circumnuclear ring | 10 | ±2 | Myr | 5 | The orbital period $\tau$ is obtained as $\tau = \frac{2\pi}{\Omega - \Omega_{p}} = 10 \pm 2$ Myr. |
| Ring gas angular velocity | 690 | ±120 | km/s/kpc | 5 | $\Omega = v/R = 690 \pm 120$ km s$^{-1}$ kpc$^{-1}$ |
| Collision timescale | ~1.6 | not stated | Myr | 5 | t \sim {\rm 1.6\,Myr}~ \left (\frac{R_{cl}}{\rm 20\,pc}\right )^{-2} |
| CH3OH fractional abundance decrease N1 to N5 | ~10 | not stated | factor | 4 | The largest change from the upstream to the downstream is seen in CH$_3$OH, and it is by a factor of $\sim 10$ |
| CN fractional abundance N2 vs N1 | ~4 | not stated | factor | 4 | The fractional abundance of CN is the lowest at N1, $\sim4$ times higher at N2 |
| Free-free fraction of Band 3 continuum | 45-100 | not stated | % | 0 | which turns out to be 45-100 % |
| 13CO(1-0) column density at N3 | 7.1e16 | 0.6e16 | cm^-2 | 3 | $(7.1 \pm 0.6) \times 10^{16}$ |

## Qualitative findings

- Shock tracers CH3OH and SiO are enhanced at both orbit-intersection locations; the northeastern stream shows downstream CN and H41alpha peaks while the southwestern stream shows no sign of star formation.  
  > "Shock tracers (SiO and CH$_3$OH) are found to be enhanced at the two locations where the leading-edge gas lanes on the bar are connected to the circumnuclear ring." (5 Summary)

## Claim tuples

- H: Chemistry varies along the NE stream consistent with collision-induced star formation | E: Abundance and intensity ratio analysis at N1-N5 with timescale estimates | R: CH3OH, SiO, N2H+ elevated at N1-N2; CN and H41alpha peak downstream at N2-N3 | F: Star formation at N2-N3 plausibly triggered by collisions at the orbit intersection if gas is compressed to n=1e3-1e4 cm^-3 | **partially**
- H: SW stream shows same evolution | E: Same analysis at S1-S5 | R: Similar shock tracer enhancement but weaker SiO, no H41alpha | F: No sign of collision-induced star formation in the SW stream | **supported**

## Reasoning

- Why this data: M83 is proximate, face-on, ALMA-accessible with a circumnuclear ring  
  > "M83 provides an excellent laboratory due to its proximity" (Introduction)
- Why this method: _not stated_
- Alternative: Lack of gas supply, lack of strong shocks, or turbulence as reasons for no star formation in SW stream; self-gravity-dominated mode rejected as unlikely  
  > "However, this scenario is unlikely in this particular case of the southwestern stream of M83" (4.3 Comparison)
- How they decided it was enough: _not stated_
- Limitation (authors): Stellar ages cannot confirm the scenario; no single-dish flux for Bands 6/7 missing-flux check  
  > "Therefore, these studies on stellar ages cannot be used to confirm the scenario of collision-induced star formation." (4.2.4 Timescale of star formation)
- Caveat (inferred, ours): LTE with assumed Tex for several species and a constant 13CO abundance may bias abundance trends
- Caveat (inferred, ours): Only two streams, so the collision interpretation is weakly constrained
- Caveat (inferred, ours): Beam-averaged quantities at 62 pc mix shocked, dense, and UV-irradiated gas
- Caveat (inferred, ours): Timescales rely on Galactic GMC properties

## Reproducibility

- Data public (paper): ALMA archival data used and cited  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2012.1.00762.S, #2015.1.01177.S, and #2016.1.00164.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: MADCUBA fit configuration
- Missing: tclean parameters beyond Table 2
- Missing: Line-free channels and continuum subtraction
- Missing: Distance adopted
- Data volume (inferred): ~1-2 TB raw across three projects (many 7m and 12m EBs)
- Score (inferred): 3/5, Data public and tools named, but imaging and MADCUBA fitting details are missing.
- Rediscovery candidate: no, Key recipe details (MADCUBA setup, imaging parameters) are not given, and the main conclusions are interpretive.

## Links

- Method: (cite: 2018PASJ...70...73H) (Data reduction for 2012.1.00762.S cubes)
- Companion: (cite: 2018ApJ...855...49H) (Earlier Harada et al. astrochemistry of NGC 253)
- Related: IRAM 30m 3-mm line survey (Aladro et al. 2015)

## Checks

```json
{
 "quotes": 61,
 "quotes_ok": 61,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 3,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 73,
  "stated": 40,
  "rate": 0.548
 },
 "evidence_ok": true
}
```
