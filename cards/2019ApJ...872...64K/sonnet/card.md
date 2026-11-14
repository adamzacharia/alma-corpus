# Extremely High Excitation SiO Lines in Disk-outflow Systems in Orion Source I

`2019ApJ...872...64K` | The Astrophysical Journal 2019 | first author: Kim, Mi Kyoung | arXiv: 1901.07208 | DOI: 10.3847/1538-4357/aafb6b

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation
- Question: What do high-excitation SiO lines (v=2, v=4) trace in the disk-outflow system of Orion Source I, and what central mass and ring radii do they imply?  
  > "In this paper, we present the results of ALMA observations at 0.1$''$ resolution to study dynamical properties of the disk-outflow system in the close vicinity to Source I." (Introduction)
- Target **Orion Source I**: coordinates RA(J2000)=05h35m14.512s, Dec(J2000)=-05d22m30.57s  
  > "The tracking center position of the target source was RA(J2000)=05h35m14.512s, Decl(J2000)=$-$05$^{\circ}$22$'$30.57$''$." (Observations); "Due to its proximity (D$\sim$420 pc) (cite: Menten2007; Hirota2007; Kim2008)" (Introduction); z/distance D~420 pc  
  > "The tracking center position of the target source was RA(J2000)=05h35m14.512s, Decl(J2000)=$-$05$^{\circ}$22$'$30.57$''$." (Observations); "Due to its proximity (D$\sim$420 pc) (cite: Menten2007; Hirota2007; Kim2008)" (Introduction); distance from Menten2007; Hirota2007; Kim2008  
  > "The tracking center position of the target source was RA(J2000)=05h35m14.512s, Decl(J2000)=$-$05$^{\circ}$22$'$30.57$''$." (Observations); "Due to its proximity (D$\sim$420 pc) (cite: Menten2007; Hirota2007; Kim2008)" (Introduction)

## Data provenance

- ALMA projects: 2013.1.00048.S
- bands: Band 8 (460 GHz and 430 GHz tunings)  
  > "using the Atacama Large Millimeter/Submillimeter Array (ALMA) at band 8" (abstract)
- frequencies and spectral setup: SPWs centered at 428.0 and 464.6 GHz; channel spacing 976.562 kHz (~0.6 km/s)  
  > "The spectral window centered at 428.0 GHz and 464.6 GHz included observed SiO line emissions." (Observations); "the channel spacing was 976.562 kHz, corresponding the velocity resolution of $\sim$0.6 km s$^{-1}$" (Observations)
- continuum bandwidth: total bandwidth 1875 MHz  
  > "The total bandwidth of the spectral bands was 1875 MHz" (Observations)
- arrays: 40 and 35 antennas at 460 and 430 GHz  
  > "The array was composed of 40 and 35 antennas with the maximum baseline length of 1575 m and 2270 m at 460 GHz and 430 GHz, respectively." (Observations)
- configurations: _not stated_
- baselines: maximum baseline 1575 m (460 GHz), 2270 m (430 GHz)  
  > "maximum baseline length of 1575 m and 2270 m at 460 GHz and 430 GHz, respectively" (Observations)
- angular resolution: 0.13x0.11" (29SiO), 0.12x0.11" (v=4), 0.09x0.07" (428 GHz)  
  > "The synthesized beam sizes were 0.13$''$ $\times$0.11$''$ with the position angle of 82$^\circ$ for the 465 GHz $^{29}$SiO $v$=2 $J$=11-10 line" (Observations)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: 458 s (460 GHz), 2065 s (430 GHz)  
  > "The total on-source integration times of the target source were 458 seconds, and 2065 seconds for 460 GHz, and 430 GHz, respectively." (Observations)
- observing dates: August 27 (460 GHz) and September 22 (430 GHz) 2015, Cycle 2  
  > "Observations were executed on August 27 (460 GHz), and September 22 (430 GHz) in 2015" (Observations)
- pi or archival as stated: _not stated_
- Line: 29SiO v=2 J=11-10 (465014.010 MHz)
- Line: SiO v=2 J=10-9 (428087.451 MHz)
- Line: SiO v=4 J=11-10 (464244.956 MHz)
- External data: Line rest frequencies and lower-state energies  
  > "Line information are taken from the Cologne Database for Molecular Spectroscopy (CDMS)" (Table 1) [from (cite: Muller2005)]
- External data: 43 GHz SiO v=1,2 maser absolute positions used for overlay  
  > "using the absolute positions measured by (cite: Kim2008) and (cite: Goddi2011)" (Discussion) [from (cite: Kim2008); (cite: Goddi2011)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0423-013 (primary); bandpass J0522-3627; gain J0607-0834 (460 GHz), J0501-0159 (430 GHz)  
  > "a primary flux calibrator was J0423$-$013, and a band-pass calibrator was J0522$-$3627." (Observations)
- flux scale uncertainty: _not stated_
- self calibration: self-calibration carried out in CASA; details in Hirota2016b, 2017  
  > "The self-calibration and the synthesized imaging were carried out using the CASA software package." (Observations)

### Imaging

- task: CASA clean, per-channel images  
  > "The synthesized images of each velocity channels were made for all lines by using the CASA task `clean` with uniform-weighting." (Observations)
- deconvolver: _not stated_
- weighting robust: uniform weighting  
  > "with uniform-weighting" (Observations)
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
- final beam: 0.13x0.11" PA 82 (29SiO), 0.12x0.11" PA 87 (v=4), 0.09x0.07" PA 82 (428 GHz)  
  > "0.12$''$ $\times$0.11$''$ with the position angle of 87$^\circ$ for the 464 GHz SiO $v$=4 $J$=11-10 line" (Observations)
- final rms: _not stated_

### Inherited from earlier work

- Observation details  
  > "Details of observations are summarized in (cite: Hirota2016b; Hirota2017)." (Observations) [from (cite: Hirota2016b; Hirota2017)]
- Data analysis (self-calibration, imaging) details  
  > "The details of the data analysis are summarized in (cite: Hirota2016b; Hirota2017)." (Observations) [from (cite: Hirota2016b; Hirota2017)]
- Ring Keplerian model similar to earlier works  
  > "using a simple model similar to those of (cite: Hirota2014) and (cite: Plambeck2016)" (Discussion) [from (cite: Hirota2014); (cite: Plambeck2016)]

### Not stated but needed to reproduce (our reading)

- Self-calibration solution intervals and reference data
- Image size, cell size, cleaning threshold and masks
- Continuum subtraction and line-free channels
- Fitting statistic and grid steps for ring model
- Flux scale uncertainty and CASA version
- Integrated intensity and moment velocity ranges

## Analysis recipe

1. **Image line channels**: Self-calibrate and clean each velocity channel with uniform weighting  
  > "The synthesized images of each velocity channels were made for all lines by using the CASA task `clean` with uniform-weighting." (Observations)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Moment maps and centroid maps**: immoments for moment maps; 2D Gaussian fit to each channel for position centroids  
  > "To make a position centroid maps of the line emission, we did a two-dimensional Gaussian fitting to each velocity channel maps using the task JMFIT with the AIPS software package." (Observations)
   - software: CASA immoments, AIPS JMFIT
   - fitting: _not stated_
   - validation: Positional accuracy ~1 mas (v=4) and ~2 mas (29SiO) from beam and SNR  
  > "the positional accuracy was as high as $\sim$1 mas for the $v$=4 $J$=11-10 line and $\sim$2 mas for the $v$=2 $J$=11-10 line" (Discussion)
3. **Brightness temperature**: From peak flux density and Gaussian source size per channel  
  > "Using measured flux densities and the source sizes, the brightness temperatures of $^{29}$SiO $v$=2 $J$=11-10 and SiO $v$=4 $J$=11-10 lines are estimated to be 229 K and 349 K." (Results)
   - fitting: _not stated_
   - validation: _not stated_
4. **Fit Keplerian ring to velocity centroids**: Compare simulated rotation curves of thin edge-on Keplerian ring to observed centroids over grid of r_in, r_out and mass 5-15 Msun  
  > "We simulated the rotation curve for a range of inner radii $r_{in}$ and outer radii $r_{out}$ with the central masses ranges from 5 to 15$M_{\odot}$." (Discussion)
   - parameter: thermal width 3 km/s; systemic velocity 6 km/s; PA 140 deg  
  > "The thermal width of 3 km s$^{-1}$ was assumed. We set the systemic velocity of 6 km s$^{-1}$" (Discussion)
   - assumption: Thin edge-on ring, uniform temperature and density, optically thin emission  
  > "We assumed a thin, edge-on ring structure in Keplerian rotation around a central star." (Discussion)
   - fitting: _not stated_
   - validation: Compared with curves for 5, 10, 15 Msun  
  > "We also display the rotation curves with the central mass of 5, 10, and 15$M_{\odot}$." (Discussion)

## Software

- **CASA** : self-calibration, clean imaging, immoments  
  > "We made the moment maps using the CASA task `immoments`." (Observations)
- **AIPS (JMFIT)** : 2D Gaussian fits to channel maps  
  > "using the task JMFIT with the AIPS software package" (Observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Central mass lower limit | 7 | not stated | Msun | 4 | $r_{in}$=12 AU, $r_{out}$=26 AU, and the central mass of 7$M_{\odot}$ for the best parameter |
| Ring radii | 12-26 | not stated | AU | 4 | $r_{in}$=12 AU, $r_{out}$=26 AU |
| Brightness temperature 29SiO v=2 J=11-10 | 229 | not stated | K | 3 | estimated to be 229 K and 349 K |
| Brightness temperature SiO v=4 J=11-10 | 349 | not stated | K | 3 | estimated to be 229 K and 349 K |
| Peak flux densities 29SiO v=2 and SiO v=4 | 1.3 and 1.2 | not stated | Jy | 2 | The peak flux densities of $^{29}$SiO $v$=2 $J$=11-10 and SiO $v$=4 $J$=11-10 lines are 1.3 Jy and 1.2 Jy |
| Deconvolved size 29SiO and SiO v=4 | 0.13x0.13 and 0.08x0.06 | not stated | arcsec | 2 | with the deconvolved size of 0.13$''$$\times$0.13$''$ and 0.08$''$$\times$0.06$''$, respectively |

## Qualitative findings

- First detection of SiO v=4 in a star-forming region  
  > "this is the first time to detect the SiO $v$=4 $J$=11-10 line in star-forming regions" (Results)

## Claim tuples

- H: Do high-excitation SiO lines trace the inner disk surface and outflow base? | E: Moment, centroid and PV analysis of three SiO lines | R: v=4 and 29SiO v=2 compact (<80 AU), offset from midplane; v=2 J=10-9 bipolar ~0.5" | F: Lines trace disk surface and outflow base | **supported**
- H: What is the central mass of Source I? | E: Keplerian ring model fit to v=4 centroids | R: 7 Msun, 12-26 AU | F: Lower limit of 7 Msun, below Ginsburg2018's >15 Msun | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Self-absorption rejected for the SiO v=2 J=10-9 absorption; SO 9(10)-8(9) proposed instead  
  > "It is unlikely to be explained by a self-absorption because the SiO $v$=2 $J$=10-9 line has a high excitation temperature" (Results)
- How they decided it was enough: _not stated_
- Limitation (authors): Resolution and sensitivity insufficient; model omits midplane offset and outflow; mass is a lower limit  
  > "we cannot exclude the possibility of the higher central mass because we did not consider the offset from the disk midplane and the effect of the outflow" (Discussion)
- Caveat (inferred, ours): Best-fit ring parameters have no uncertainties or fit statistic
- Caveat (inferred, ours): Maser versus thermal nature unresolved
- Caveat (inferred, ours): Absolute astrometry uncertain by 100 mas

## Reproducibility

- Data public (paper): Project 2013.1.00048.S cited; public status not stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2013.1.00048.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Self-cal and imaging parameters (deferred to earlier papers)
- Missing: Ring model code and grid details
- Missing: Moment integration ranges
- Data volume (inferred): ~50-100 GB raw
- Score (inferred): 3/5, Data identifiable but imaging and model-fit details are sparse and deferred to earlier papers.
- Rediscovery candidate: no, Recipe is incomplete: the self-calibration and imaging settings are deferred to earlier papers, and the ring fit is unspecified.

## Links

- Method: (cite: Hirota2016b) (Observation and data analysis details)
- Method: (cite: Hirota2017) (Observation and data analysis details)
- Companion: (cite: Ginsburg2018) (Higher-resolution ALMA data of Source I with a larger mass estimate)

## Checks

```json
{
 "quotes": 53,
 "quotes_ok": 53,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 67,
  "stated": 36,
  "rate": 0.537
 },
 "evidence_ok": true
}
```
