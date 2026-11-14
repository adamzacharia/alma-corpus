# First Abundance Measurement of Organic Molecules in the Atmosphere of HH 212 Protostellar Disk

`2019ApJ...876...63L` | The Astrophysical Journal 2019 | first author: Lee, Chin-Fei | arXiv: 1904.10572 | DOI: 10.3847/1538-4357/ab15db

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, astrochemistry, protoplanetary_disks
- Question: Which organic molecules are present in the HH 212 protostellar disk atmosphere, what are their abundances, and how do they compare with hot corinos around other protostars?  
  > "we report the first systematic survey and abundance measurement of organic molecules in the disk atmosphere within $\sim$ 40 au of the central protostar." (abstract)
- Target **HH 212**: coordinates _not stated_; z/distance ~400 pc  
  > "HH 212 is a young Class 0 protostellar system deeply embedded in a compact molecular cloud core in the L1630 cloud of Orion at a distance of $\sim$ 400 pc (cite: Kounkel2017)." (Introduction); distance from Kounkel2017  
  > "HH 212 is a young Class 0 protostellar system deeply embedded in a compact molecular cloud core in the L1630 cloud of Orion at a distance of $\sim$ 400 pc (cite: Kounkel2017)." (Introduction)

## Data provenance

- ALMA projects: 2017.1.00044.S
- bands: Band 7 (~341.5 GHz)  
  > "The HH 212 protostellar system was observed with ALMA in Band 7 at $\sim$ 341.5 GHz in Cycle 5." (Observations)
- frequencies and spectral setup: 4 spws; 3 continuum (2 GHz each), one spectral 1.875 GHz covering 345.635-347.510 GHz, 1.953 MHz/channel (~1.69 km/s)  
  > "The correlator was set up to have 4 spectral windows, with 3 in continuum mode having a bandwidth of 2 GHz, and one in spectral mode having a bandwidth of 1.875 GHz." (Observations); "The spectral resolution was 1.953 MHz per channel, resulting in a velocity resolution of $\sim$ 1.69 km s$^{-1}$ per channel at 346.5 GHz." (Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: ~60-8500 m  
  > "The projected baselines were $\sim$ 60-8500 m." (Observations)
- angular resolution: 0.036" x 0.03", PA ~ -78 deg  
  > "a synthesized beam of $0^{\prime\prime}_{^\textrm{.}}036$$\times$$0^{\prime\prime}_{^\textrm{.}}03$ at a position angle of $\sim$ $-$78$^\circ$" (Observations)
- max recoverable scale: ~0.4 arcsec  
  > "The maximum recoverable size scale was $\sim$ $0^{\prime\prime}_{^\textrm{.}}4$" (Observations)
- sensitivity: 0.121 mJy/beam continuum; 0.80 mJy/beam channel maps  
  > "The noise levels are $\sim$ 0.121 mJy beam$^{-1}$ (or $\sim$ 1.13 K) in the continuum map and 0.80 mJy beam$^{-1}$ (or $\sim$ 7.45 K) in the channel maps." (Observations)
- time on source: ~98 min total (3 x ~32.7 min)  
  > "Thus, the total time on the target was $\sim$ 98 minutes." (Observations)
- observing dates: 2017 November 27  
  > "Three observations were executed on the same day on 2017 November 27 with 47 antennas" (Observations)
- pi or archival as stated: _not stated_
- Line: CH3OH, CH2DOH, 13CH3OH, H2CCO, CH3CHO, HCOOCH3, t-HCOOH, CH3CH2OH, CH2DCN many lines (see Table 1) (345.635-347.510 GHz)
- External data: Disk atmosphere mean H2 column density ~3.8e24 cm^-2 from dust disk model  
  > "In that disk model, the disk atmosphere has a mean H$_2$ column density of $\sim$ 3.8$\times 10^{24}$ cm$^{-2}$." (Results) [from (cite: Lee2017Disk)]
- External data: 12C/13C ratio of 50 (Orion Complex)  
  > "a $^{12}$C/$^{13}$C ratio of 50 as obtained in the Orion Complex (cite: Kahane2018)" (Results) [from (cite: Kahane2018)]
- External data: NH2CHO, D2CO, CH3SH column densities  
  > "Also shown in the table are the column densities of NH$_2$CHO, D$_2$CO, and CH$_3$SH measured in (cite: Lee2017COM), adjusted with the mean excitation temperature here." (Results) [from (cite: Lee2017COM)]
- External data: Systemic velocity 1.7+-0.1 km/s LSR  
  > "The systemic velocity is $V_\textrm{\scriptsize sys}= 1.7\pm0.1$ km s$^{-1}$ LSR (cite: Lee2014)." (Results) [from (cite: Lee2014)]
- External data: Comparison abundances in IRAS 16293-2422B, B335, NGC 1333 IRAS4A2  
  > "5.8$\times10^{-9}$ in IRAS 16293-2422B (cite: Jorgensen2016), 2.4$\times10^{-9}$ in B335 (cite: Imai2016), and 4.2$\times10^{-9}$ in NGC 1333 IRAS4A2 (cite: Lopez2017)" (Discussion) [from Jorgensen2016; Imai2016; Lopez2017]

## Processing

### Calibration

- pipeline or manual: CASA; passband/flux calibrator J0510+1800, gain calibrator J0541-0211  
  > "The data were calibrated with the CASA package, with quasar J0510+1800 as a passband and flux calibrator, and quasar J0541-0211 (a flux of 0.137 Jy) as a gain calibrator." (Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0510+1800  
  > "quasar J0510+1800 as a passband and flux calibrator" (Observations)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: robust = 0.5  
  > "We used a robust factor of 0.5 for the visibility weighting to generate the channel maps" (Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: continuum from line-free channels, subtracted before line channel maps  
  > "We used the line-free channels to generate a continuum map centered at 356.5 GHz. The channel maps of the molecular lines were generated after continuum subtraction." (Observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.036" x 0.03", PA ~ -78 deg  
  > "a synthesized beam of $0^{\prime\prime}_{^\textrm{.}}036$$\times$$0^{\prime\prime}_{^\textrm{.}}03$ at a position angle of $\sim$ $-$78$^\circ$" (Observations)
- final rms: 0.80 mJy/beam in channel maps; 0.121 mJy/beam continuum  
  > "0.80 mJy beam$^{-1}$ (or $\sim$ 7.45 K) in the channel maps" (Observations)

### Inherited from earlier work

- Disk model (dust opacity, H2 column) and disk geometry used for abundances  
  > "Based on our disk model that reproduced the dust continuum emission at a similar wavelength of $\sim$ 850 $\mu$m (cite: Lee2017Disk)" (Results) [from (cite: Lee2017Disk)]
- Linear position-frequency structure interpretation as warm rotating ring near the centrifugal barrier  
  > "As discussed in that paper, this linear PF structure likely arises from a warm rotating ring of the disk atmosphere near the centrifugal barrier." (Results) [from (cite: Lee2017COM)]

### Not stated but needed to reproduce (our reading)

- CASA version and whether pipeline or manual calibration was used
- Image cell size, image size, deconvolver, cleaning masks and threshold
- Line-free channel selection and continuum subtraction method
- Flux calibrator flux value and flux scale uncertainty
- Exact rectangular region position for line intensity averaging and coordinates of the target
- Line list handling (Splatalogue, partition functions) and how stacking was done
- Dust opacity used in the disk model for the H2 column

## Analysis recipe

1. **Make continuum and line channel maps**: Calibrate in CASA, image with robust 0.5, subtract continuum from line-free channels  
  > "We used a robust factor of 0.5 for the visibility weighting to generate the channel maps" (Observations)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Identify lines and map molecular emission**: Use position-frequency diagrams along the lower atmosphere to identify lines with the linear PF structure; stack unblended detected lines per species into mean intensity maps  
  > "we stacked the line intensity maps in different transitions, excluding those tentatively detected (marked with T) and blended (marked with B)" (Results)
   - fitting: _not stated_
   - validation: _not stated_
3. **Derive excitation temperature and column densities**: Rotation diagrams in the optically thin limit for lines measured in a rectangular region (0.2" x 0.05") of the lower atmosphere (2 sigma cutoff, lines >3 sigma); fixed T=150+-50 K for other molecules; single lines from integrated intensity  
  > "Here we derive the mean excitation temperature and column density in the disk atmosphere by fitting the rotation diagram of the molecular lines." (Results)
   - parameter: Line intensity uncertainty assumed 40%  
  > "The line intensities here are assumed to have an uncertainty of 40%." (Table 1)
   - assumption: Optically thin lines, mean Tex 150+-50 K for molecules with weak lines  
  > "Assuming this mean temperature for the disk atmosphere, we can estimate the column densities of other molecules with weaker lines." (Results)
   - fitting: _not stated_
   - validation: Upper atmosphere temperatures checked: 138+-32 K (CH3OH), 168+-24 K (CH2DOH)  
  > "we also obtained similar temperatures of $\sim$ $138\pm32$ K and $\sim$ $168\pm24$ K for the upper atmosphere" (Results)
4. **Correct CH3OH column using 13CH3OH**: Remove expected CH2DCN contamination (~21 K km/s, ~18%) from 13CH3OH line and multiply 13CH3OH column by 12C/13C = 50  
  > "it is estimated to be $\sim$ 21 K km s$^{-1}$, or $\sim$ 18% of the total intensity there." (Results)
   - assumption: 12C/13C = 50  
  > "a $^{12}$C/$^{13}$C ratio of 50 as obtained in the Orion Complex (cite: Kahane2018)" (Results)
   - fitting: _not stated_
   - validation: Derived CH3OH column about twice the rotation-diagram value, indicating optically thick CH3OH lines  
  > "the CH$_3$OH column density derived this way is about twice that derived from the rotation diagram, suggesting that the CH$_3$OH lines are indeed optically thick." (Results)
5. **Derive abundances and compare**: Divide column densities by mean H2 column 3.8e24 cm^-2; compare abundances relative to CH3CHO with other hot corinos  
  > "the abundances of the molecules, as listed in Table [2](#tab:colabun), can be obtained by dividing the column density of the molecules by this mean H$_2$ column density." (Results)
   - assumption: Dust optical depth tau<~1, so columns could be underestimated by factor e; abundances uncertain by a factor of a few due to dust opacity  
  > "The abundances here can be uncertain by a factor a few because the mean H$_2$ column density depends on dust opacity" (Results)
   - fitting: _not stated_
   - validation: Relative abundances similar to other hot corinos within a factor of few  
  > "the relative abundances of most molecules here in HH 212 are similar to those in other hot corinos to within a factor of few" (Discussion)

## Software

- **CASA** : Calibration and imaging  
  > "The data were calibrated with the CASA package" (Observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| CH3OH excitation temperature (lower atmosphere) | 160 | 45 | K | 3 | With the CH$_3$OH lines, we derived an excitation temperature of $\sim$ $160\pm45$ K. |
| CH2DOH excitation temperature | 148 | 19 | K | 3 | we derived a similar temperature of $\sim$ $148\pm19$ K |
| Mean excitation temperature | 150 | 50 | K | 3 | we obtain a mean excitation temperature of $\sim$ $150\pm50$ K in the lower disk atmosphere |
| CH3OH column density (adopted, from 13CH3OH) | 1.3e18 | 0.7e18 | cm^-2 | 4 | CH$_3$OH...$^b$ / $150\pm50^c$ / ($1.3\pm 0.7$)$\times 10^{18}$ |
| CH3CHO column density | 1.5e16 | 0.6e16 | cm^-2 | 3 | CH$_3$CHO / $150\pm50^c$ / ($1.5\pm 0.6$)$\times 10^{16}$ / ($3.9\pm 1.6$)$\times 10^{-9}$ |
| CH3CHO abundance | 3.9e-9 | 1.6e-9 | dimensionless | 5 | ($3.9\pm 1.6$)$\times 10^{-9}$ |
| CH3CH2OH column density | 2.7e16 | 1.2e16 | cm^-2 | 3 | CH$_3$CH$_2$OH / $150\pm50^c$ / ($2.7\pm 1.2$)$\times 10^{16}$ / ($7.1\pm 3.2$)$\times 10^{-9}$ |
| HCOOCH3 column density | 3.2e16 | 1.6e16 | cm^-2 | 3 | HCOOCH$_3$ / $150\pm50^c$ / ($3.2\pm 1.6$)$\times 10^{16}$ / ($8.4\pm 4.2$)$\times 10^{-9}$ |
| CH2DCN column density | 3.6e14 | 1.6e14 | cm^-2 | 3 | CH$_2$DCN / $150\pm50^c$ / ($3.6\pm 1.6$)$\times 10^{14}$ |
| Alcohol degree by mass | >~2.8 | not stated | percent | 5 | the alcohol degree by mass is estimated to be $\gtrsim$ 2.8% |

## Qualitative findings

- Molecular emission is only in the upper and lower disk atmosphere, brighter below the midplane, within the centrifugal barrier (~0.11", 44 au)  
  > "Molecular line emissions are only detected in the upper (above the midplane) and lower disk atmosphere, with the emission brighter in the lower disk atmosphere below the midplane." (Results)

## Claim tuples

- H: The HH 212 hot corino is the warm disk atmosphere | E: Image organic molecule lines at 0.03" resolution | R: 9 organic molecules detected in the disk atmosphere within the centrifugal barrier | F: Hot corino is the warm disk atmosphere | **supported**
- H: Disk-atmosphere abundances are similar to other hot corinos | E: Compare abundances relative to CH3CHO with IRAS 16293B, B335, IRAS4A2 | R: Similar within a factor of few | F: Similar formation mechanism possible | **supported**
- H: CH3OH lines are optically thick | E: Compare rotation-diagram CH3OH column with 13CH3OH x 50 | R: Latter about twice the former | F: CH3OH lines are optically thick | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Stack multiple lines for better detection of faint molecules  
  > "the maps of the molecular emissions are obtained by stacking a number of lines" (Results)
- How they decided it was enough: _not stated_
- Limitation (authors): Abundances uncertain by a factor of a few due to dust opacity; columns possibly underestimated by factor e  
  > "The abundances here can be uncertain by a factor a few because the mean H$_2$ column density depends on dust opacity" (Results)
- Caveat (inferred, ours): Single mean Tex assumed for most molecules
- Caveat (inferred, ours): Rotation-diagram LTE with possible opacity and line blending
- Caveat (inferred, ours): Abundances depend on a model-based H2 column from earlier work

## Reproducibility

- Data public (paper): Project code given and ALMA data acknowledged; public status not explicitly stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2017.1.00044.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Imaging parameters (cell, size, masks, cleaning)
- Missing: Region coordinates and rotation-diagram fitting details
- Missing: Disk model details for H2 column
- Data volume (inferred): ~100-300 GB raw
- Score (inferred): 3/5, Data identified and key steps given, but many imaging and fitting details are missing.
- Rediscovery candidate: no, Imaging details and extraction regions are underspecified, and abundances rely on a model H2 column from earlier work.

## Links

- Method: (cite: Lee2017Disk) (Disk model providing H2 column and geometry)
- Companion: (cite: Lee2017COM) (Earlier detection of organic molecules in HH 212 atmosphere)
- Companion: (cite: Codella2018) (Lower-resolution CH3CHO and HDO observations)

## Checks

```json
{
 "quotes": 58,
 "quotes_ok": 58,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 10,
 "numeric_problems": 0,
 "fill": {
  "facts": 72,
  "stated": 41,
  "rate": 0.569
 },
 "evidence_ok": true
}
```
