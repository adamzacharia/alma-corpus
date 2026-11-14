# Free-free and H42α emission from the dusty starburst within NGC 4945 as observed by ALMA

`2016MNRAS.463..252B` | Monthly Notices of the Royal Astronomical Society 2016 | first author: Bendo, G. J. | arXiv: 1607.02304 | DOI: 10.1093/mnras/stw1659

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, star_formation
- Question: Measure free-free emission, electron temperature and star formation rate in the NGC 4945 central starburst from ALMA 85.69 GHz continuum and H42α, and compare with infrared and radio SFRs  
  > "The star formation rate (SFR) based on the H42$\alpha$ and 85.69 GHz free-free emission (and using a distance of 3.8 Mpc) is 4.35$\pm$0.25 M$_\odot$ yr$^{-1}$." (abstract)
- Target **NGC 4945**: coordinates _not stated_; z/distance 3.8 Mpc (±0.3 Mpc)  
  > "Dimensions in pc are calculated using a distance of 3.8 Mpc. The uncertainties include the 0.3 Mpc uncertainty in the distance." (Table 2 (model fits)); distance from _not stated_

## Data provenance

- ALMA projects: 2012.1.00912.S
- bands: Band 3, 85.69 GHz continuum and H42α  
  > "the measurements in band 3 vary by 6% over this time period" (2.1 ALMA data)
- frequencies and spectral setup: one spw centred on 85.895 GHz, 1920 channels of 976.6 kHz (3.4 km/s)  
  > "The spectral window containing the H42$\alpha$ line was centered on 85.895 GHz, contained 1920 channels with a width of 976.6 kHz (3.4 km s$^{-1}$)" (2.1 ALMA data)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: compact configuration, baselines 15-445 m, 31 antennas  
  > "The array was in a compact configuration with baselines extending from 15 to 445 m." (2.1 ALMA data)
- baselines: _not stated_
- angular resolution: 2.6x2.3 arcsec  
  > "The full-width at half-maximum (FWHM) of the reconstructed beams are 2.6$\times$2.3 arcsec." (2.1 ALMA data)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: 33.94 min  
  > "the total on-source integration time was 33.94 min" (2.1 ALMA data)
- observing dates: 24 January 2013  
  > "were performed in a single execution block on 24 January 2013" (2.1 ALMA data)
- pi or archival as stated: Project PI C. Henkel; reprocessed by the authors  
  > "project 2012.1.00912.S (PI: C. Henkel)" (2.1 ALMA data)
- Line: H42α recombination line (not stated)
- Other facility **Spitzer MIPS 24 um**: mid-infrared flux for SFR and total IR  
  > "we calculated SFR using 24 $\mu$m data from the *Spitzer* Space Telescope" (2.2 Infrared data)
- Other facility **WISE 22 um**: mid-infrared flux for SFR  
  > "22 $\mu$m data from the Wide-field Infrared Survey Explorer" (2.2 Infrared data)
- Other facility **Herschel PACS/SPIRE**: 70-500 um photometry for total IR flux  
  > "70-500 $\mu$m data from the *Herschel* Space Observatory" (2.2 Infrared data)
- External data: Radio/mm flux densities 4.8-345 GHz used in SED fit  
  > "4.8 | 3.055 | (cite: healey07)" (Table 1) [from healey07, lenc09, forbes98, roy10, massardi08, wang04, chou07, weiss08]
- External data: Case B emissivities and recombination coefficients  
  > "$\epsilon_\nu$ is the emissivity from (cite: storey95)" (6 Electron temperature) [from storey95]

## Processing

### Calibration

- pipeline or manual: reprocessed by authors in CASA with a priori, flagging, bandpass/gain steps  
  > "The data were reprocessed using the Common Astronomy Software Applications (CASA) version 4.5.0." (2.1 ALMA data)
- casa version: CASA 4.5.0  
  > "The data were reprocessed using the Common Astronomy Software Applications (CASA) version 4.5.0." (2.1 ALMA data)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J1107-448, 1.44±0.03 Jy at 85.895 GHz  
  > "the flux density at the central frequency of 85.895 GHz is estimated as $1.44\pm0.03$ Jy" (2.1 ALMA data)
- flux scale uncertainty: 6%  
  > "we will assume that the ALMA flux calibration is reliable to within 6% for our analysis." (2.1 ALMA data)
- self calibration: _not stated_

### Imaging

- task: clean in CASA, Cotton-Schwab  
  > "converted into image cubes using clean in CASA with the Cotton-Schwab imager algorithm and with natural weighting" (2.1 ALMA data)
- deconvolver: _not stated_
- weighting robust: natural  
  > "with the Cotton-Schwab imager algorithm and with natural weighting" (2.1 ALMA data)
- uv taper: _not stated_
- cell size: 0.5 arcsec  
  > "The final image cubes have pixel scales of 0.5 arcsec" (2.1 ALMA data)
- image size: 256x256 pixels  
  > "dimensions of 256$\times$256 pixels (128$\times$128 arcsec)" (2.1 ALMA data)
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: linear fit to line-free channels  
  > "continuum-subtracted based on a linear fit to line-free regions in visibility channels 400-560" (2.1 ALMA data)
- line free channels: channels 400-560, 1000-1200, 1440-1500  
  > "visibility channels 400-560 (sky frequencies 86.288-86.444 GHz), 1000-1200 (sky frequencies 85.663-85.859 GHz), and 1440-1500" (2.1 ALMA data)
- primary beam correction: applied after imaging  
  > "Primary beam corrections are applied to the images after they are created." (2.1 ALMA data)
- array combination: _not stated_
- smoothing: channels averaged by 4 to 3.906 MHz (13.7 km/s)  
  > "results in a channel width of 3.906 MHz (13.7 km s$^{-1}$)" (2.1 ALMA data)
- final beam: 2.6x2.3 arcsec  
  > "The full-width at half-maximum (FWHM) of the reconstructed beams are 2.6$\times$2.3 arcsec." (2.1 ALMA data)
- final rms: _not stated_

### Inherited from earlier work

- Disc model fitting technique (updated version)  
  > "using an updated version of the techniques from (cite: bendo06) and (cite: young09)" (3 ALMA images) [from (cite: bendo06); (cite: young09)]
- SFR-Q conversion coefficient from Starburst99  
  > "which was derived by (cite: bendo15b) using version 7.0.1 of the Starburst99 models" (7.1) [from (cite: bendo15b)]
- Spitzer MIPS processing steps  
  > "along with additional processing steps described by (cite: bendo12)" (2.2.1) [from (cite: bendo12)]

### Not stated but needed to reproduce (our reading)

- Exact clean parameters (niter, threshold, masks)
- Region definitions for T, N, C, S apertures (only in figure)
- Image rms values
- Monte Carlo and Gauss-Hermite fitting algorithm details
- Phase centre coordinates
- Fit algorithm and optimizer for disc model

## Analysis recipe

1. **Image cubes and moment maps**: clean cubes, continuum-subtract, sum channels 310-365 for H42α; median continuum over same channels  
  > "The total H42$\alpha$ flux in each map pixel was calculated by summing the signal between channels 310 and 365" (2.1 ALMA data)
   - software: CASA
   - fitting: _not stated_
   - validation: flux calibrator and J1427-4207 checked against archival monitoring  
  > "we compared the flux densities from a continuum image of J1427-4207 to archival flux monitoring data" (2.1 ALMA data)
2. **Model spatial structure**: fit inclined thin exponential disc convolved with beam, and Gaussian  
  > "we fit the images with a thin exponential disc that is projected at an inclined angle and convolved with a Gaussian function equivalent to the reconstructed beam" (3 ALMA images)
   - fitting: _not stated_
   - validation: models replicate pixel values within 15% where H42α >5σ  
  > "Both models replicate the observed pixel values to within 15% where the H42$\alpha$ emission is detected at the 5$\sigma$ level." (3 ALMA images)
3. **Line profile parameterisation**: fit Gauss-Hermite functions (A, v0, sigma, h3, h4 free) to spectra and per pixel  
  > "The amplitude ($A$), mean velocity ($v_0$), Gaussian width parameter ($\sigma$), $h_3$, and $h_4$ are all treated as free parameters." (4 ALMA spectra)
   - fitting: _not stated_
   - validation: compared with two-Gaussian fits for N and S  
  > "we fit the N and S regions with two Gaussian functions" (4 ALMA spectra)
4. **SED decomposition for free-free fraction**: fit power laws for synchrotron (free index), free-free (Gaunt factor, Te=5000 K), dust (index 4) to 3-350 GHz data  
  > "We model the synchrotron, free-free, and thermal dust emission components as power laws." (5 SED)
   - parameter: Te fixed 5000 K; dust index 4  
  > "The spectral index of the dust emission is fixed to 4" (5 SED)
   - fitting: Monte Carlo for uncertainty; 10% errors for two datasets  
  > "Using a Monte Carlo approach, we found that the uncertainty in the percent of total emission from free-free emission is 7%." (5 SED)
   - validation: tests varying Te 3000-10000 K and indices; fraction varied ≤10%  
  > "we found that the percent of the flux density from free-free emission at 85.69 GHz varied by $\leq$10%." (5 SED)
5. **Electron temperature**: line-to-free-free continuum ratio with Storey & Hummer emissivities, case B, ne=1e3 cm-3  
  > "we use $\epsilon_\nu$ values corresponding to case B recombination and a fixed $n_e$ value of $10^3$ cm$^{-3}$" (6 Electron temperature)
   - assumption: 84±10% of continuum is free-free  
  > "All $T_e$ are derived assuming that 84$\pm$10% of the continuum emission originates from free-free emission." (6 Electron temperature)
   - fitting: _not stated_
   - validation: compared with Milky Way Te  
  > "The $T_e$ measurements are broadly consistent with the low end of $T_e$ measurements within the Milky Way" (6 Electron temperature)
6. **SFR from ALMA, mid-IR, total IR, radio**: Q from line/continuum; SFR=5.41e-54 Q; mid-IR via Rieke09; TIR via Murphy11; radio via Condon/Murphy  
  > "SFR}{\mbox{M}_\odot~\mbox{yr}^{-1}} =5.41\times10^{-54}\frac{Q}{\mbox{s}^{-1}}" (7.1)
   - software: HIPE
   - assumption: Kroupa IMF, Z=0.040, continuous SFR >3 Myr  
  > "The SFR is assumed to be continuous and to have been ongoing for greater that 3 Myr" (7.1)
   - fitting: _not stated_
   - validation: cross-comparison of SFR tracers  
  > "We first discuss how the ALMA SFR measurements compare to the SFR measurements from total infrared and radio data" (7.5)

## Software

- **CASA** 4.5.0: reprocessing and imaging ALMA data  
  > "The data were reprocessed using the Common Astronomy Software Applications (CASA) version 4.5.0." (2.1 ALMA data)
- **HIPE** 14.0.0: Herschel PACS/SPIRE processing  
  > "The data were processed using the standard SPIRE pipeline in HIPE version 14.0.0" (2.2.4)
- **MIPS Data Analysis Tools** 3.10: Spitzer 24 um reprocessing  
  > "reprocessed using the MIPS Data Analysis Tools version 3.10" (2.2.1)
- **JScanam** : PACS map making  
  > "Images were created using JScanam, the Java version of SCANAMORPHOS" (2.2.3)
- **Starburst99** 7.0.1: SFR-Q conversion  
  > "using version 7.0.1 of the Starburst99 models" (7.1)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Free-free fraction at 85.69 GHz | 84 | 10% | % | 4 | 84%$\pm$10% of the 85.69 GHz continuum emission originates from free-free emission |
| Electron temperature (T region) | 5400 | 600 | K | 5 | T / $0.31 \pm 0.04$ / $12.9 \pm 0.8$ / $42 \pm 5$ / $5400 \pm 600$ |
| SFR from ALMA (average) | 4.35 | 0.25 | Msun/yr | 6 | is 4.35$\pm$0.25 M$_\odot$ yr$^{-1}$ |
| Total 85.69 GHz continuum flux | 0.36 | 0.02 | Jy | 1 | The total continuum emission we measure with ALMA at 85.69 GHz is 0.36$\pm$0.02 Jy |
| Continuum disc scale length | 1.99 | 0.08 | arcsec | 2 | Major Axis Scale Length (arcsec) / $1.99 \pm 0.08$ / $2.33 \pm 0.09$ |
| SFR from total IR | 3.0 | 0.3 | Msun/yr | 6 | The final SFR measured for the central source based on the total infrared flux is $3.0 \pm 0.3$ M$_\odot$ yr$^{-1}$. |
| Mid-IR SFR | 0.4 | 0.20 dex | Msun/yr | 6 | we will work with a mid-infrared SFR measurement of 0.4 M$_\odot$ yr$^{-1}$ |
| Mean H42α velocity (total) | 611 | 7 | km/s | 3 | The mean barycentric velocity of 611$\pm$7 km s$^{-1}$ |

## Qualitative findings

- Continuum and H42α trace the same circumnuclear starburst disc with no AGN central peak  
  > "The absence of such a central peak implies that virtually all of the H42$\alpha$ and continuum emission originates from the circumnuclear starburst." (3 ALMA images)

## Claim tuples

- H: Does the AGN contribute significantly to the mm emission? | E: Fit disc models and inspect for central excess | R: No central excess; line widths <300 km/s FWHM | F: Emission is from circumnuclear starburst | **supported**
- H: What are Te and SFR from ALMA? | E: SED decomposition plus line/continuum ratio | R: Te=5400±600 K; SFR 4.35±0.25 | F: Consistent with total IR SFR and within factor ~2 of radio | **supported**
- H: Are mid-IR SFRs reliable for dusty compact starbursts? | E: Compare Spitzer/WISE SFR with ALMA SFR | R: Mid-IR SFR ~10x lower | F: Mid-IR is optically thick (A_V~150); SFRs underestimated | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Two-Gaussian line fits rejected for per-pixel use as unreliable; Gauss-Hermite used  
  > "it is impractical to do this for the individual pixels in the image cube" (4 ALMA spectra)
- How they decided it was enough: _not stated_
- Limitation (authors): Herschel photometry may include extended emission biasing SFR high; mid-IR Spitzer central pixels may be saturated  
  > "these measurements may include additional emission from circumnuclear structures that are more extended than the structures seen in the ALMA data" (7.3)
- Caveat (inferred, ours): Free-free fraction depends on assumed Te and sparse SED data with heterogeneous apertures
- Caveat (inferred, ours): Continuum and line SFRs are coupled through Te so not independent
- Caveat (inferred, ours): Single ALMA pointing, flux scale 6% uncertain

## Reproducibility

- Data public (paper): ALMA data from project 2012.1.00912.S (archival, PI Henkel)  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2012.1.00912.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: clean niter/threshold/mask
- Missing: aperture region definitions for T/N/C/S
- Missing: fitting code
- Data volume (inferred): ~10-30 GB raw
- Score (inferred): 3/5, Data public, recipe mostly specified with numeric results, but some imaging and fitting details missing.
- Rediscovery candidate: yes, Public single-EB dataset, described imaging, numeric results (Te, SFR, scale length) can be checked.

## Links

- Method: (cite: bendo15b) (Method for Te and SFR from recombination lines and conversion coefficient)
- Method: (cite: scoville13) (Recombination line and free-free equations)
- Companion: Henkel et al. (2016, in preparation) (Molecular line emission from same data)

## Checks

```json
{
 "quotes": 69,
 "quotes_ok": 69,
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
  "facts": 80,
  "stated": 55,
  "rate": 0.688
 },
 "evidence_ok": true
}
```
