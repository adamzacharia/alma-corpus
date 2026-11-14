# Widespread Molecular Outflows in the Infrared Dark Cloud G28.37+0.07: Indications of Orthogonal Outflow-filament Alignment

`2019ApJ...874..104K` | The Astrophysical Journal 2019 | first author: Kong, Shuo | arXiv: 1903.05273 | DOI: 10.3847/1538-4357/ab07b9

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, milky_way_ism
- Question: Are CO outflows in IRDC G28.37+0.07 preferentially oriented relative to their parent filaments (and in a preferred plane-of-sky direction)?  
  > "We can therefore compare the position angle between outflows and filaments, both easily observable in large-scale maps of clouds, to search for evidence of the accretion-filament correlation." (Introduction)
- Target **IRDC G28.37+0.07 (G28)**: coordinates _not stated_; z/distance 5 kpc  
  > "IRDC G28.37+0.07[^1] (hereafter G28) is a massive (10$^5$ M$_\odot$) IRDC at a distance of 5 kpc." (Introduction); distance from _not stated_

## Data provenance

- ALMA projects: 2015.1.00183.S, 2013.1.00183.S
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.6"x0.4" synthesized beam (~0.012 pc)  
  > "resulting in a final synthesized beam of 0.6$''$$\times$0.4$''$, providing a linear resolution of about 0.012 pc" (ALMA Observations)
- max recoverable scale: ~20" (~0.5 pc)  
  > "The maximum recoverable scale is $\sim$20$''$ (corresponding to the shortest baseline of 10 k$\lambda$ with $\lambda$ being 1.3 mm)" (ALMA Observations)
- sensitivity: ~2.5 mJy/beam (0.22 K) in 1.3 km/s channels  
  > "The final cube sensitivity, with 1.3 km s$^{-1}$ wide velocity channels, is $\sim$ 2.5 mJy beam$^{-1}$, or 0.22 K." (ALMA Observations)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: PI Kong; 86-pointing mosaic  
  > "It is a 86-pointing mosaic that covers the majority of the IRDC G28." (ALMA Observations)
- Line: CO 2-1 (not stated)
- Line: SiO 5-4 (not stated)
- Other facility **Spitzer GLIMPSE 8 um**: image used to define filament spines  
  > "we use the 8 $\mu$m image from the Spitzer GLIMPSE survey" (2.2 Filament Definition)
- External data: Catalog of 280 1.3 mm continuum cores (astrograph)  
  > "In total, 280 cores were defined in K19 using their *astrograph* method." (3.1 CO Outflow Definition) [from (cite: 2019ApJ...873...31K)]
- External data: Cloud centroid velocity of 79.3 km/s  
  > "cloud centroid velocity of 79.3 km s$^{-1}$, which previous studies obtained by analyzing the spectral line data of dense gas tracers" (3.1 CO Outflow Definition) [from (cite: 2006A&A...450..569P; 2013ApJ...779...96T; 2016ApJ...821...94K)]

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

- task: tclean in CASA 5.1  
  > "The CO line data cube was cleaned using the `tclean` task in CASA 5.1." (ALMA Observations)
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 0.5  
  > "Briggs weighting with a robust number of 0.5 was used" (ALMA Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: SiO cube: joint deconvolution of 2015.1.00183.S and 2013.1.00183.S  
  > "The SiO data cube is from a joint de-convolution of the data from 2015.1.00183.S and the data from 2013.1.00183.S" (ALMA Observations)
- smoothing: _not stated_
- final beam: 0.6"x0.4"  
  > "resulting in a final synthesized beam of 0.6$''$$\times$0.4$''$" (ALMA Observations)
- final rms: _not stated_

### Inherited from earlier work

- Details of ALMA observations and 1.3 mm continuum  
  > "We refer the readers to that paper for details on the ALMA observations." (ALMA Observations) [from (cite: 2018ApJ...855L..25K)]
- Angle conventions, PA_Out, gamma, AD tests, Monte Carlo projection of gamma_3D  
  > "Hereafter, we follow the angle naming conventions in Stephens17" (3.3 Outflow PA Statistics) [from Stephens17 (cite: 2017ApJ...846...16S)]

### Not stated but needed to reproduce (our reading)

- Spectral setup, calibration and pipeline details (only in Kong et al. 2018a)
- Cell size, image size, masking, continuum subtraction and line-free channels for the CO cube
- Exact filament spine coordinates and PA_Fil definitions beyond the table
- Velocity-integrated outflow lobe PA measurement method
- Outflow lobe velocity ranges per source

## Analysis recipe

1. **Image CO cube**: tclean with Briggs weighting  
  > "The CO line data cube was cleaned using the `tclean` task in CASA 5.1." (ALMA Observations)
   - software: CASA
   - parameter: robust = 0.5  
  > "Briggs weighting with a robust number of 0.5 was used" (ALMA Observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **Identify CO outflows**: Visual search of ten pairs of red/blue integrated maps symmetric about 79.3 km/s, assign driving continuum source, check channels and SiO  
  > "We visually identify bipolar red-blue pairs that are symmetric around mm continuum sources." (3.1 CO Outflow Definition)
   - parameter: 6.5 km/s (5 channel) integrated chunks; rms 7.3 mJy/beam km/s  
  > "The RMS noise for each 6.5 km s$^{-1}$ wide integrated intensity map is 7.3 mJy beam$^{-1}$ km s$^{-1}$" (3.1 CO Outflow Definition)
   - fitting: _not stated_
   - validation: Checked by inspecting individual channels and SiO(5-4)  
  > "We then verify our outflow catalog by carefully inspecting the CO emission from each channel in the cube" (3.1 CO Outflow Definition)
3. **Define filament spines**: Visually trace dark lanes in Spitzer 8 um (plus ALMA 1.3 mm continuum in some regions)  
  > "We visually follow dark paths (i.e., filaments in absorption) in the cloud and overlay segments on top of the paths to define the filament spines" (3.2 Filament Definition)
   - fitting: _not stated_
   - validation: Visual definition judged most reliable versus other techniques  
  > "Comparing with other techniques we find the visual definition to give the most reliable results." (3.2 Filament Definition)
4. **PA statistics and AD test vs uniform**: Compute PA_Out from blue/red lobes; AD test against uniform distribution  
  > "we carry out Anderson-Darling (AD) tests between the distribution of PA$_{\rm Out}$ and a uniform distribution" (3.3.1 Distribution of PA_Out)
   - fitting: _not stated_
   - validation: _not stated_
5. **Outflow-filament angle and Monte Carlo**: Compute gamma; simulate projection of random 3D vectors and compare CDFs via two-sample AD tests for parallel, perpendicular and random scenarios  
  > "We use $N$=10$^6$ (the same as Stephens17) and reproduce their $\gamma_{\rm 3D}$ CDF" (3.3.2 Outflow-filament Orientation)
   - parameter: scenarios: 0-20, 70-90, 0-90 deg  
  > "(1) $\gamma_{\rm 3D}$ with values only from 0$^\circ$ to 20$^\circ$; (2) $\gamma_{\rm 3D}$ with values only from 70$^\circ$ to 90$^\circ$; (3) $\gamma_{\rm 3D}$ with values from 0$^\circ$ to 90$^\circ$." (3.3.2 Outflow-filament Orientation)
   - assumption: Uniform random 3D orientations in simulation  
  > "We randomly generate $N$ pairs of unit vectors with their 3D PA following the uniform distribution." (3.3.2 Outflow-filament Orientation)
   - fitting: _not stated_
   - validation: Reproduced Stephens17 gamma_3D CDF  
  > "reproduce their $\gamma_{\rm 3D}$ CDF, shown in Figure [4](#fig:gamma)(a)" (3.3.2 Outflow-filament Orientation)

## Software

- **CASA** 5.1: tclean imaging of CO cube  
  > "The CO line data cube was cleaned using the `tclean` task in CASA 5.1." (ALMA Observations)
- **Astropy** : listed software  
  > "Astropy (cite: Astropy-Collaboration13), Numpy (cite: numpy), APLpy (cite: Robitaille12)" (Software)
- **Glue** : listed software  
  > "Glue (cite: 2015ASPC..495..101B; robitaille_thomas_2017_1237692)" (Software)
- **SAOImageDS9** : listed software  
  > "SAOImageDS9 (cite: 2003ASPC..295..489J)" (Software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Continuum cores driving CO outflows | 62 | not stated | cores | 2 | In total, 62 continuum sources are associated with at least one CO outflow lobe. |
| AD test p-value of PA_Out vs uniform | 0.15 | not stated | dimensionless | 4 | The p-value of the AD test is 0.15 |
| AD p-value, observed gamma vs random scenario | 6.5e-5 | not stated | dimensionless | 5 | gives a p-value of 6.5$\times$10$^{-5}$ |
| AD p-value, observed gamma vs only-perpendicular scenario | 0.53 | not stated | dimensionless | 5 | gives a p-value of 0.53 |
| Number of outflows with gamma 60-90 / 30-60 / 0-30 deg | 32 / 19 / 7 | not stated | outflows | 5 | between 60$^\circ$ and 90$^\circ$ (32), compared to outflows with $\gamma$ between 30$^\circ$ and 60$^\circ$ (19), and between 0$^\circ$ and 30$^\circ$ (7) |

## Qualitative findings

- Outflow position angles peak near 100 deg (east-west); outflows appear mostly perpendicular to parent filaments in 3D.  
  > "the distribution of the plane-of-sky outflow position angles peaks at about 100$^\circ$" (abstract)

## Claim tuples

- H: Outflow PAs are randomly distributed | E: AD test of PA_Out against uniform | R: p = 0.15, peak near 100 deg | F: Outflow orientations are not random; east-west preference | **partially**
- H: Outflows are parallel, random or perpendicular to filaments in 3D | E: Monte Carlo projection and two-sample AD tests | R: random p=6.5e-5; perpendicular p=0.53 | F: Outflows mostly perpendicular to parent filaments | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Outflow catalog likely incomplete, especially low-velocity or near plane-of-sky outflows in crowded regions.  
  > "We note that our outflow catalog for G28 is likely incomplete." (3.1 CO Outflow Definition)
- Caveat (inferred, ours): Visual outflow and filament identification is subjective and not reproducible quantitatively
- Caveat (inferred, ours): AD p-value 0.15 is weak evidence for non-uniform PA_Out
- Caveat (inferred, ours): Filament PA from 8 um may not trace 3D structure; foreground/background confusion
- Caveat (inferred, ours): Single cloud

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Imaging parameters beyond robust and tclean
- Missing: Visual selections underlying lobe PAs (table gives results only)
- Data volume (inferred): ~100-300 GB for the 86-pointing mosaic raw data
- Score (inferred): 3/5, Data are archival-type and final PA table is given, but the outflow and filament identification is visual and imaging details are sparse.
- Rediscovery candidate: no, Key results rely on visual identification and the statistics could be redone only from the table, not from the data recipe.

## Links

- Method: Stephens17 (cite: 2017ApJ...846...16S) (Statistical method for outflow-filament angles)
- Companion: (cite: 2018ApJ...855L..25K) (Same ALMA project; 1.3 mm continuum observation details)
- Companion: (cite: 2019ApJ...873...31K) (Core catalog)
- Related: Spitzer GLIMPSE

## Checks

```json
{
 "quotes": 45,
 "quotes_ok": 45,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 73,
  "stated": 33,
  "rate": 0.452
 },
 "evidence_ok": true
}
```
