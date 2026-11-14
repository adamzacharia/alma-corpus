# Complex organic molecules in diffuse clouds along the line of sight to Sagittarius B2

`2017A&A...605L...6T` | Astronomy and Astrophysics 2017 | first author: Thiel, V. | arXiv: 1708.07292 | DOI: 10.1051/0004-6361/201731495

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: astrochemistry, milky_way_ism
- Question: Do complex organic molecules exist in diffuse molecular clouds along the line of sight to Sgr B2(N), and is their composition similar to the z = 0.89 absorber?  
  > "We aim at searching for complex organic molecules (COMs) in diffuse molecular clouds along the line of sight to Sgr B2(N)" (abstract)
- Target **Sgr B2(N), ultracompact HII region K4 (absorption background)**: coordinates K4: 17h47m20.02s, -28d22m04.7s (J2000)  
  > "This source is located at ($\alpha$,$\delta$)$_\mathrm{J2000}=(17^\mathrm{h}47^\mathrm{m}20.02^\mathrm{s},-28^\circ$22$'$ 04.7$''$)" (Results); "a distance of $8.34\pm0.16$ kpc to the sun (cite: reid2014)" (Introduction); z/distance 8.34±0.16 kpc  
  > "This source is located at ($\alpha$,$\delta$)$_\mathrm{J2000}=(17^\mathrm{h}47^\mathrm{m}20.02^\mathrm{s},-28^\circ$22$'$ 04.7$''$)" (Results); "a distance of $8.34\pm0.16$ kpc to the sun (cite: reid2014)" (Introduction); distance from Reid et al. 2014 (cite: reid2014)  
  > "This source is located at ($\alpha$,$\delta$)$_\mathrm{J2000}=(17^\mathrm{h}47^\mathrm{m}20.02^\mathrm{s},-28^\circ$22$'$ 04.7$''$)" (Results); "a distance of $8.34\pm0.16$ kpc to the sun (cite: reid2014)" (Introduction)

## Data provenance

- ALMA projects: 2011.0.00017.S, 2012.1.00012.S
- bands: _not stated_
- frequencies and spectral setup: 84.1-114.4 GHz survey; 488 kHz (1.3-1.7 km/s) resolution  
  > "The survey covers the frequency range from 84.1 to 114.4 GHz with a median angular resolution of $1.6\ensuremath{''}$." (Observations and analysis method); "The spectral resolution is 488 kHz or 1.3–1.7 km s$^{-1}$." (Observations and analysis method)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: median 1.6"  
  > "median angular resolution of $1.6\ensuremath{''}$" (Observations and analysis method)
- max recoverable scale: _not stated_
- sensitivity: ~3 mJy/beam average noise  
  > "The average noise level is \~3 mJy beam$^{-1}$." (Observations and analysis method)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: CH3OH 2_0,1,0-1_0,1,0 (96741.371 MHz)
- Line: CH3CN 5_0,0-4_0,0 (91987.088 MHz)
- Line: HC3N 10-9 (90979.023 MHz)
- Line: NH2CHO 4_0,4-3_0,3 (84542.330 MHz)
- Other facility **Herschel HIFI (HF)**: HF data used for H2 column densities (~40")  
  > "the HF data used to determine the H$_2$ column densities $\sim$ 40$\ensuremath{''}$ (cite: bergin2010)" (Results)
- External data: HI and H2 column density distributions integrated over velocity ranges  
  > "They were calculated by integrating the column density distributions of (cite: winkel2017) over velocity ranges" (Results) [from (cite: winkel2017)]
- External data: 12C/13C ratio 20 (GC) and 40 (Scutum arm)  
  > "assuming an isotopic ratio $^{12}$C/$^{13}$C equal to 20 for the GC and 40 for the Scutum arm (cite: milam2005)" (Results) [from (cite: milam2005)]
- External data: Column densities for PKS 1830-211 absorber, Horsehead, Sgr B2(N2), IRAS 2A for comparison  
  > "the $z=0.89$ spiral galaxy in front of the QSO PKS 1830–211 (cite: muller2011; muller2013)" (Results) [from muller2011; muller2013; guzman2014; belloche2016; taquet2015]

## Processing

### Calibration

- pipeline or manual: calibration and deconvolution done by Belloche et al. 2016  
  > "The calibration and deconvolution of the data were performed by (cite: belloche2016)." (Observations and analysis method)
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
- primary beam correction: spectra corrected for primary beam attenuation  
  > "We corrected the spectra for the primary beam attenuation." (Observations and analysis method)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Data calibration and deconvolution  
  > "The calibration and deconvolution of the data were performed by (cite: belloche2016)." (Observations and analysis method) [from Belloche et al. 2016 (cite: belloche2016)]

### Not stated but needed to reproduce (our reading)

- CASA version and imaging parameters (in EMoCA paper)
- Spectral extraction position/aperture at K4
- Fitting algorithm and uncertainty estimation for Weeds fits
- Detection criteria and how upper limits were defined
- Continuum level/handling for absorption optical depth
- Uncertainties for column densities

## Analysis recipe

1. **Extract K4 absorption spectra**: Use EMoCA calibrated data, primary-beam corrected spectra toward K4  
  > "We corrected the spectra for the primary beam attenuation." (Observations and analysis method)
   - fitting: _not stated_
   - validation: _not stated_
2. **Fit synthetic spectra**: Model with Weeds; fit column density, linewidth, centroid velocity; Tex = 2.73 K unless several transitions allow population diagram  
  > "We assume the excitation temperature to be equal to the temperature of the CMB (2.73 K) except in the cases where several transitions are detected" (Observations and analysis method)
   - software: Weeds
   - parameter: beam filling factor 1; same Tex for all transitions of a molecule  
  > "We assume that all transitions of a molecule have the same excitation temperature and that the beam filling factor is 1." (Observations and analysis method)
   - fitting: _not stated_
   - validation: _not stated_
3. **Compare with H2 and other sources**: Compute abundances relative to methanol and H2 and compare with literature sources  
  > "Figure [2](#ntots)b shows the abundances relative to methanol." (Results)
   - assumption: 12C/13C = 20 (GC), 40 (Scutum)  
  > "isotopic ratio $^{12}$C/$^{13}$C equal to 20 for the GC and 40 for the Scutum arm" (Results)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **Weeds** : model spectra  
  > "We use Weeds (cite: maret2011) to model the spectra." (Observations and analysis method)
- **CDMS** : line identification  
  > "For the identification we used the CDMS database (cite: mueller2005; mueller2001)" (Results)
- **JPL catalogue** : line identification  
  > "the JPL catalogue (cite: pickett1998)" (Results)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| CH3OH column density, GC cloud at 3.4 km/s | 3.8e14 | not stated | cm^-2 | 2 | CH$_3$OH / 3.8$\times 10^{14}$ / 9.4 / 4.0 |
| CH3OH column density, Scutum arm cloud | 6.2e13 | not stated | cm^-2 | 2 | CH$_3$OH / 6.2$\times10^{13}$ / 26.6 / 5.0 / 2.73 |
| CH3CN Tex (9.4 km/s component) | 4.2 | 0.7 | K | 2 | $4.2\pm0.7$ |
| Molecular fraction Scutum arm cloud | 0.70 | not stated | dimensionless | 3 | The molecular fraction is 0.70 for the Scutum-arm cloud and 0.4–0.6 for the GC clouds |

## Qualitative findings

- Linewidths 3-6 km/s for GC clouds, 3.5-5 km/s for Scutum cloud  
  > "The linewidths range between 3 and 6 km s$^{-1}$ for the GC centre clouds and between 3.5 and 5 km s$^{-1}$ for the Scutum arm cloud." (Results)

## Claim tuples

- H: COMs exist in Galactic diffuse clouds | E: Search for absorption toward K4 in EMoCA data | R: CH3OH, CH3CN, CH3CHO, HC3N, NH2CHO in GC clouds; CH3OH, CH3CN in Scutum arm | F: COMs are present in diffuse clouds | **supported**
- H: Diffuse GC cloud chemistry resembles z=0.89 absorber | E: Compare abundances relative to methanol | R: Similar apart from HC3N | F: Chemical processes similar since z=0.89 | **partially**

## Reasoning

- Why this data: K4 is strong continuum source away from hot cores, giving absorption sensitivity along the whole line of sight  
  > "The ultracompact H ii region K4 (cite: gaume1995) fulfills these requirements." (Introduction)
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Methanol abundances may be overestimated because H2 may be underestimated due to clumpiness and coarse HF resolution  
  > "it may be that the abundances we obtain are overestimated due to an underestimate of the H$_2$ column density" (Discussion)
- Caveat (inferred, ours): Absorption toward a single position; beam filling factor assumed 1
- Caveat (inferred, ours): No uncertainties for most column densities
- Caveat (inferred, ours): Tex assumed CMB for many species
- Caveat (inferred, ours): H2 from 40" data mismatched with 1.6" ALMA

## Reproducibility

- Data public (paper): Interferometric data in ALMA archive  
  > "The interferometric data are available in the ALMA archive at https://almascience.eso.org/aq/." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Calibrated EMoCA products/imaging details (in Belloche et al. 2016)
- Missing: Fit uncertainties and procedure
- Missing: Winkel et al. 2017 data
- Data volume (inferred): Large (full EMoCA survey, hundreds of GB raw); calibrated cubes tens of GB
- Score (inferred): 3/5, Public data and simple Weeds modelling, but calibration inherited and fit details sparse.
- Rediscovery candidate: no, Recipe depends on inherited EMoCA reduction and lacks fit details.

## Links

- Method: Belloche et al. 2016 (cite: belloche2016) (EMoCA survey calibration and deconvolution)
- Method: Maret et al. 2011 (cite: maret2011) (Weeds)
- Companion: Winkel et al. 2017 (cite: winkel2017) (HI and H2 column densities)
- Related: EMoCA

## Checks

```json
{
 "quotes": 44,
 "quotes_ok": 44,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 4,
 "numeric_problems": 0,
 "fill": {
  "facts": 64,
  "stated": 26,
  "rate": 0.406
 },
 "evidence_ok": true
}
```
