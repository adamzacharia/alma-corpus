# Molecular Gas Excitation in z ∼ 0.7 Gas-rich Poststarburst Galaxies from SQuIGG<inline-formula> <mml:math><mml:mover><mml:mrow><mml:mi>L</mml:mi></mml:mrow><mml:mrow><mml:mo>→</mml:mo></mml:mrow></mml:mover></mml:math> </inline-formula>E

`2026ApJ..1003...52D` | The Astrophysical Journal 2026 | first author: D'Onofrio, Vincenzo R. | arXiv: 2602.17766 | DOI: 10.3847/1538-4357/ae64e7

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, high_z_galaxies
- Question: What is the CO excitation (r52) of the molecular gas in gas-rich z~0.7 post-starburst galaxies, and does it indicate buried star formation or non-stellar heating?  
  > "Together, these data allow us to assess whether gas-rich SQuIGG$\vec{L}$E PSBs host molecular gas with CO excitation consistent with diffuse and quiescent systems" (Introduction)
- Target **Nine SQuIGGLE PSBs (J0907+0423, J0909-0108, J0912+1523, J1142+0006, J1157+0132, J1436+0447, J1448+1010, J2258+2313, J2310-0047)**: coordinates _not stated_; z/distance z = 0.5935-0.7559 (Table 1)  
  > "| J0907+0423 | 0.6635 |" (Table 1); distance from _not stated_

## Data provenance

- ALMA projects: 2024.1.01252.S, 2018.1.01240.S, 2018.1.01264.S
- bands: Band 7 (CO(5-4)); Band 6 and 7 for CO(4-3) in two objects  
  > "we obtained ALMA Band 7 observations of the CO(5–4) transition" (ALMA CO Observations)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ≈0.5'' (≈3-4 kpc)  
  > "The observations yield angular resolutions of $\approx$0.5$''$" (ALMA CO Observations)
- max recoverable scale: _not stated_
- sensitivity: ≈300-500 μJy/beam per 50 km/s channel  
  > "spectral line sensitivities that range $\approx$300-500 $\mu\rm{Jy}\,\rm{beam}^{-1}$ per channel" (ALMA CO Observations)
- time on source: ≈25 minutes per source  
  > "Each target was observed with an average on-source integration time of $\approx$25 minutes per source." (ALMA CO Observations)
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: CO 5-4 (576.27 GHz)
- Line: CO 4-3 (461.04 GHz)
- Other facility **HSC / HST WFC3**: Optical/NIR imaging for overlays  
  > "Hyper Suprime-Cam (HSC) $i$-band" (3.1)
- External data: CO(2-1) luminosities, H2 masses for sample  
  > "The ALMA CO(2–1) properties for the rest of the sources are from (cite: bezanson_now_2022) and (cite: setton_squigg_2025)." (Table 1) [from (cite: bezanson_now_2022; setton_squigg_2025)]
- External data: SFRs from SED fitting incl. buried models  
  > "we adopt the paired (cite: setton_squigg_2025) values as our SFR estimates" (SFR Measurements) [from (cite: setton_squigg_2025; suess_mathrmsquiggecle_2022)]
- External data: z~1.25 MS and SB CO SLED comparison sample  
  > "those of $z\sim1.25$ main-sequence (MS) and starburst (SB) galaxies (cite: valentino_co_2020)" (Results) [from (cite: valentino_co_2020)]
- Simulation/model as data: Narayanan & Krumholz star-formation-driven CO excitation model sequence  
  > "the star formation driven model excitation sequence from (cite: narayanan_theory_2014)" (Results)

## Processing

### Calibration

- pipeline or manual: standard ALMA pipeline in CASA  
  > "All data were calibrated with the standard ALMA pipeline in `CASA`." (ALMA CO Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "Imaging was carried out using natural weighting to maximize sensitivity" (ALMA CO Observations)
- uv taper: tapered cubes matched to ~1-2'' beam as a test  
  > "We produced tapered image cubes matched to the $\sim$1-2$''$ beam size of the CO(2–1) data" (Results)
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: subtracted in uv plane  
  > "was subtracted in the $uv$ plane prior to imaging" (ALMA CO Observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: 50 km/s channels; 100 and 150 km/s binned for J0912+1523  
  > "we additionally image spectral cubes binned to 100 and 150 $\rm{km\,s}^{-1}$ channels" (Results)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Natural weighting follows earlier SQuIGGLE CO(2-1) analyses  
  > "consistent with previous analyses of SQuIGG$\vec{L}$E CO(2–1) data (cite: bezanson_now_2022; setton_squigg_2025)" (ALMA CO Observations) [from (cite: bezanson_now_2022; setton_squigg_2025)]
- MH2 from r21=1.0 and alpha_CO=4.0  
  > "assuming thermalized emission $r_{21}=1.0$ and the CO-to-H2 conversion factor $\ensuremath{\alpha_{\rm{CO}}}= 4.0$" (Target Galaxies) [from (cite: bezanson_now_2022; setton_squigg_2025)]

### Not stated but needed to reproduce (our reading)

- Robust/weighting details, cell and image size, clean thresholds and masks
- CASA version
- Line-free channels for continuum subtraction
- Fit details for single Gaussian spectra (initial guesses, aperture sizes)
- Flux scale uncertainty
- Exact CO(2-1) line widths used for upper limits
- Radii for Sigma_SFR beyond Table 1 and area definition
- Archival CO(2-1) project mapping to targets

## Analysis recipe

1. **Image CO cubes**: Pipeline calibration, uv continuum subtraction, natural-weighted cubes at 50 km/s  
  > "The resulting spectral cubes have a spectral resolution of 50 $\rm{km\,s}^{-1}$" (ALMA CO Observations)
   - software: CASA
   - fitting: _not stated_
   - validation: Tapered vs natural images give consistent fluxes  
  > "The tapered and natural-weighted images recover consistent integrated fluxes" (Results)
2. **Measure CO(5-4) flux and size**: Aperture from 2D Gaussian fit of integrated map; spectrum fit with single Gaussian; 3 sigma upper limit for nondetection  
  > "Integrated line fluxes were derived by fitting each spectrum with a single Gaussian profile" (Results)
   - software: CASA IMFIT
   - fitting: single Gaussian line profile  
  > "fitting each spectrum with a single Gaussian profile" (Results)
   - validation: Consistent with channel summation and IMFIT fluxes  
  > "yielding values consistent with both direct channel summation and the fluxes returned via `IMFIT`" (Results)
3. **Compute r52 and compare to SFR and comparison samples**: Ratio of L'CO(5-4)/L'CO(2-1); K-S test vs z~1.25 MS and SB; compare r52 with SFR and Sigma_SFR using CO(5-4) sizes  
  > "A two-sample Kolmogorov-Smirnov test of the SQuIGG$\vec{L}$E galaxies including the nondetection but excluding J1448+1010" (Results)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : calibration, imaging, IMFIT  
  > "using the `IMFIT` task in `CASA`" (Results)
- **astropy** : listed in software  
  > "`astropy` (cite: astropy_collaboration_astropy_2013" (Software)
- **matplotlib** : plotting (listed)  
  > "`matplotlib` (cite: hunter_matplotlib_2007)" (Software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| CO(5-4) detections | 8/9 | not stated | dimensionless | 2 | We detect CO(5–4) emission in 8/9 galaxies |
| r52 of J1448+1010 | 0.57 | 0.08 | dimensionless | 3 | / J1448+1010 / 0.6462 / 3.21 $\pm$ 0.21 / 1.28 $\pm$ 0.08 / 3.43 $\pm$ 0.39 / 1.93 $\pm$ 0.25 / 1.82 $\pm$ 0.24 / 0.57 $\pm$ 0.08 / |
| r52 of J1157+0132 | 0.30 | 0.03 | dimensionless | 3 | / J1157+0132 / 0.7559 / 28.26 $\pm$ 0.40 / 11.30 $\pm$ 0.16 / 3.22 $\pm$ 0.36 / 6.54 $\pm$ 0.73 / 8.47 $\pm$ 0.94 / 0.30 $\pm$ 0.03 / |
| K-S p-value vs MS / SB | 0.607 / 0.037 | not stated | dimensionless | 3 | yields $p$-values of 0.607 and 0.037 when compared to the MS and SB populations, respectively |
| r42 J0912+1523 | 0.11 | 0.05 | dimensionless | 2 | we find $r_{42}=0.11\pm0.05$ for J0912+1523 |

## Qualitative findings

- No clear trend between r52 and total or surface-density SFR  
  > "The SQuIGG$\vec{L}$E galaxies show no clear trend between excitation ratio and either total or surface-density SFR." (Results)

## Claim tuples

- H: Gas-rich PSBs at z~0.7 have high CO excitation from buried star formation | E: CO(5-4) ALMA observations of 9 PSBs, r52 vs SFR and Sigma_SFR | R: r52≈0.1-0.3 for most, no trend with SFR | F: Moderate excitation, suppressed SF efficiency, no strong buried starburst needed | **supported**
- H: Some objects need non-stellar heating | E: Compare J1448+1010 to SFR-driven models and AGN indicators | R: r52≈0.6 | F: Likely AGN heating plus possible obscured SF | **partially**

## Reasoning

- Why this data: Most gas-rich objects chosen to ensure efficient CO(5-4) detection  
  > "selected as the most molecular gas-rich systems ($M_{\rm{H}_2}$$>10^{10.25}$ $M_\odot$) ensuring efficient detection of the CO(5–4) transition" (Target Galaxies)
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Small sample with limited dynamic range in excitation  
  > "though the sample is small and spans a limited dynamic range in excitation" (Conclusions)
- Caveat (inferred, ours): Only two CO transitions; no radiative transfer modeling
- Caveat (inferred, ours): alpha_CO and r21 assumptions affect masses
- Caveat (inferred, ours): Comparison sample differs in mass and redshift
- Caveat (inferred, ours): Extended emission only compared with central regions

## Reproducibility

- Data public (paper): ALMA programs acknowledged by code; public status not stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2016.1.01126.S" (Acknowledgements)
- Products in archive: _not stated_
- Missing: Imaging parameters
- Missing: Exact aperture definitions
- Missing: CO(2-1) inputs from prior papers
- Missing: SFRs from Setton et al.
- Data volume (inferred): ~50-150 GB raw for 9 Band 7 targets
- Score (inferred): 5/5, Data identified and workflow simple, but imaging and fitting details sparse and key inputs inherited.
- Rediscovery candidate: no, Imaging details are missing and key CO(2-1) and SFR inputs come from earlier papers.

## Links

- Method: (cite: bezanson_now_2022) (CO(2-1) data and methods)
- Method: (cite: setton_squigg_2025) (CO(2-1) data and SFR modeling)
- Companion: (cite: donofrio_quenching_2025) (J1448+1010 and J2258+2313 extended gas, CO(4-3))
- Related: SQuIGGLE

## Checks

```json
{
 "quotes": 44,
 "quotes_ok": 44,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 3,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2016.1.01126.S",
  "2017.1.01109.S",
  "2019.1.00221.S",
  "2021.1.00761.S",
  "2021.1.00988.S",
  "2021.1.01535.S"
 ],
 "codes_printed_but_missing": [
  "2016.1.01126.S",
  "2017.1.01109.S",
  "2019.1.00221.S",
  "2021.1.00761.S",
  "2021.1.00988.S",
  "2021.1.01535.S"
 ],
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 64,
  "stated": 31,
  "rate": 0.484
 },
 "evidence_ok": true
}
```
