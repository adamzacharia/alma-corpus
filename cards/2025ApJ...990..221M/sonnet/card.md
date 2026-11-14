# Spatially and Dynamically Extended Molecular Gas in Stephan's Quintet Revealed by ALMA CO(1─0) Total Power Mapping

`2025ApJ...990..221M` | The Astrophysical Journal 2025 | first author: Maeda, Fumiya | arXiv: 2508.12616 | DOI: 10.3847/1538-4357/adfc56

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, milky_way_ism
- Question: How much molecular gas is in Stephan's Quintet overall, how is it distributed and kinematically structured, and how does it relate to star formation and gas stripping?  
  > "aiming to reveal the total CO flux and its spatial distribution across the entire system." (Introduction)
- Target **Stephan's Quintet**: coordinates 22h36m05.11s, +33d57m58.1s (field center)  
  > "is a well-known compact galaxy group located at a distance of 88.6 Mpc (from the NASA/IPAC Extragalactic Database)" (Introduction); "centered at ($22^\mathrm{h}36^\mathrm{m}05^\mathrm{s}.11$, $33^\circ57^\prime58^{\prime\prime}.1$)" (Observation and Data Reduction); z/distance 88.6 Mpc  
  > "is a well-known compact galaxy group located at a distance of 88.6 Mpc (from the NASA/IPAC Extragalactic Database)" (Introduction); "centered at ($22^\mathrm{h}36^\mathrm{m}05^\mathrm{s}.11$, $33^\circ57^\prime58^{\prime\prime}.1$)" (Observation and Data Reduction); distance from NASA/IPAC Extragalactic Database  
  > "is a well-known compact galaxy group located at a distance of 88.6 Mpc (from the NASA/IPAC Extragalactic Database)" (Introduction); "centered at ($22^\mathrm{h}36^\mathrm{m}05^\mathrm{s}.11$, $33^\circ57^\prime58^{\prime\prime}.1$)" (Observation and Data Reduction)

## Data provenance

- ALMA projects: 2023.1.01101.S
- bands: _not stated_
- frequencies and spectral setup: One spectral window centred at 112.697 GHz, 2.000 GHz bandwidth, 976.562 kHz channels (~2.5 km/s)  
  > "The ACA spectrometer was used to obtain spectra with a bandwidth of 2.000 GHz and a channel spacing of 976.562 kHz" (Observation and Data Reduction)
- continuum bandwidth: _not stated_
- arrays: ALMA Total Power (TP), on-the-fly  
  > "On-the-fly observations were carried out between October 2, 2023, and May 4, 2024, resulting in a total of 197 execution blocks (EBs)." (Observation and Data Reduction)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: beam 58.0 arcsec (24.9 kpc)  
  > "has a beam size of $58^{\prime\prime}.0$ corresponding to 24.9 kpc" (Observation and Data Reduction)
- max recoverable scale: _not stated_
- sensitivity: rms 0.31 mK per 25 km/s channel, uniform  
  > "a uniform rms noise level of $\sigma_\mathrm{rms}=0.31$ mK" (Observation and Data Reduction)
- time on source: 197.2 h total, 107.0 h on source; 197 EBs; mean 2.72 TP antennas per EB  
  > "The total observing time was 197.2 hours, with an on-source integration time of 107.0 hours." (Observation and Data Reduction)
- observing dates: October 2, 2023 to May 4, 2024  
  > "On-the-fly observations were carried out between October 2, 2023, and May 4, 2024" (Observation and Data Reduction)
- pi or archival as stated: _not stated_
- Line: CO J=1-0 (not stated)
- External data: Dust-corrected spectroscopic Halpha SFR and HII region catalog/BPT classification  
  > "estimated to be 3.1 $M_\odot~\mathrm{yr^{-1}}$ from dust-corrected spectroscopic H$\alpha$ emission" (3.1 Global properties) [from (cite: Duarte_Puertas_2021AA)]
- External data: Dust-corrected UV SFR of 7.5 Msun/yr  
  > "7.5 $M_\odot~\mathrm{yr^{-1}}$ from dust-corrected UV emission" (3.1 Global properties) [from (cite: Natale_2010ApJ)]
- External data: HI map of SQ  
  > "The extended molecular gas is different from the HI map by (cite: Williams_2002AJ)" (3.1 Global properties) [from (cite: Williams_2002AJ)]
- External data: Galactic alpha_CO = 4.35  
  > "Assuming the Galactic CO-to-H$_2$ conversion factor of $\alpha_\mathrm{CO}=4.35~M_\odot~\mathrm{ (K~km~s^{-1}~pc^2)^{-1}}$" (3.1 Global properties) [from (cite: bolatto_conversion_2013)]
- External data: Systemic velocities of NGC 7318B (5765 km/s) and NGC 7319 (6550 km/s)  
  > "whose systemic velocity is 6550 $\mathrm{km~s^{-1}}$" (3.2 Velocity structures) [from (cite: Sulentic_2001AJ)]

## Processing

### Calibration

- pipeline or manual: Observatory-provided script reproducing standard pipeline; baseline-subtraction mask modified to exclude 112.578-113.172 GHz  
  > "Calibration was performed using CASA (version 6.5.4.9) with the observatory-provided script to reproduce the standard pipeline processing" (Observation and Data Reduction)
- casa version: CASA 6.5.4.9  
  > "Calibration was performed using CASA (version 6.5.4.9)" (Observation and Data Reduction)
- pipeline version: 2023.1.0.124  
  > "(Pipeline version 2023.1.0.124)" (Observation and Data Reduction)
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: ±5% absolute flux calibration  
  > "accounting for the absolute flux calibration accuracy of $\pm 5\%$ (ALMA Technical Handbook)" (3.1 Global properties)
- self calibration: _not stated_

### Imaging

- task: CASA sdimaging per EB; cubes combined with sdimaging weights  
  > "Each EB was imaged using CASA task `sdimaging`, and the resulting cubes were combined using the weights provided by `sdimaging`." (Observation and Data Reduction)
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: Baseline subtraction with line masked; extra FFT high-pass filter (components below 1/1000 (km/s)^-1 removed) for low-linewidth pixels in SQ-B and tail  
  > "low-frequency components below $1/1000~\mathrm{(km~s^{-1})^{-1}}$ were removed, and the data were transformed back into the velocity domain" (Observation and Data Reduction)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: Binned to 25 km/s  
  > "The final cube, binned to 25 $\mathrm{km~s^{-1}}$ resolution" (Observation and Data Reduction)
- final beam: 58.0 arcsec  
  > "has a beam size of $58^{\prime\prime}.0$" (Observation and Data Reduction)
- final rms: 0.31 mK  
  > "a uniform rms noise level of $\sigma_\mathrm{rms}=0.31$ mK" (Observation and Data Reduction)

### Not stated but needed to reproduce (our reading)

- sdimaging gridding parameters (cell size, image size, convolution kernel)
- Exact baseline fit order and pipeline masking details
- Spatial pixels selected for the FFT filter
- Conversion from K km/s to luminosity (formula, line-width/velocity handling)
- How SFRs were attributed to velocity ranges and regions (matching of HII regions)
- Region boundaries for tail and high-velocity sums
- Moment-2 computation details

## Analysis recipe

1. **Calibrate and image TP data into a cube**: Observatory script with modified baseline mask; sdimaging per EB; weighted combination; FFT high-pass filter on low-linewidth pixels; bin to 25 km/s  
  > "Each EB was imaged using CASA task `sdimaging`, and the resulting cubes were combined using the weights provided by `sdimaging`." (Observation and Data Reduction)
   - software: CASA
   - parameter: Mask 112.578-113.172 GHz (5550-7150 km/s)  
  > "we modified the masking range to exclude the frequency range from 112.578 GHz to 113.172 GHz" (Observation and Data Reduction)
   - fitting: _not stated_
   - validation: _not stated_
2. **Identify significant emission and make moment maps**: Voxels >5 sigma in at least two consecutive channels, expanded to adjacent pixels >2 sigma  
  > "selecting voxels with signal exceeding 5.0$\sigma_\mathrm{rms}$ in at least two consecutive velocity channels." (3.1 Global properties)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
3. **Derive total CO luminosity and molecular gas mass**: Integrate L'CO(1-0); multiply by alpha_CO  
  > "the total molecular gas mass is estimated to be $(1.07\pm0.05)\times 10^{10}~M_\odot$" (3.1 Global properties)
   - assumption: Galactic alpha_CO = 4.35; D = 88.6 Mpc; uncertainty from 5% flux calibration  
  > "We adopt this conversion factor because most HII regions in SQ are metal-rich" (3.1 Global properties)
   - fitting: _not stated_
   - validation: Compared with Emonts et al. 2025 7m CO(2-1)-based luminosity  
  > "In the same region, our moment-0 map yields $2.20\times10^9~\mathrm{K~km~s^{-1}~pc^2}$, which is 1.8 times higher." (3.1 Global properties)
4. **Compute star formation efficiency**: SFE = SFR/M_H2 using literature Halpha and UV SFRs  
  > "global star formation efficiency (SFE) for SQ of 0.29–0.70 $\mathrm{Gyr^{-1}}$, defined as the ratio of SFR to molecular gas mass" (3.1 Global properties)
   - fitting: _not stated_
   - validation: _not stated_
5. **Split into velocity components and measure per-component properties**: Boundaries from global profile and channel maps; moment-2 maps; masses summed by velocity dispersion thresholds (>50 km/s for high component, <50 km/s for tail)  
  > "We define these as 5636–5900 $\mathrm{km~s^{-1}}$ (low-velocity component), 5900–6243 $\mathrm{km~s^{-1}}$ (mid-velocity component), and 6243–7013 $\mathrm{km~s^{-1}}$ (high-velocity component)." (3.2 Velocity structures)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 6.5.4.9: Calibration and sdimaging  
  > "Calibration was performed using CASA (version 6.5.4.9)" (Observation and Data Reduction)
- **Astropy** : Listed in software section  
  > "CASA (cite: CASA_2022PASP), Astropy (cite: astropy_2018), APLpy (cite: Robitaille_2012)" (Software)
- **APLpy** : Plotting  
  > "an open-source plotting package for Python" (Conclusions)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Total CO(1-0) luminosity | 2.47e9 | 0.12e9 | K km/s pc^2 | 3 | The total CO(1–0) luminosity is $(2.47\pm0.12)\times10^9~\mathrm{K~km~s^{-1}~pc^2}$ |
| Total molecular gas mass | 1.07e10 | 0.05e10 | Msun | 3 | a molecular gas mass of $(1.07\pm0.05)\times10^{10}~M_\odot$ |
| Global SFE | 0.29-0.70 | not stated | Gyr^-1 | 4 | The global star formation efficiency of SQ is estimated at $0.29$–$0.70~\mathrm{Gyr^{-1}}$ |
| Tail molecular gas mass | 1.64e9 | 0.08e9 | Msun | 5 | The molecular gas mass in the tail is $(1.64\pm0.08)\times10^9~M_\odot$ |
| Low-velocity component gas mass | 6.78e8 | 0.34e8 | Msun | 5 | the molecular gas mass is $(6.78\pm0.34)\times10^8~M_\odot$ |
| Mid-velocity component gas mass | 1.62e9 | 0.08e9 | Msun | 5 | $(1.62\pm0.08)\times10^9~M_\odot$ |
| High-velocity component gas mass | 8.43e9 | 0.42e9 | Msun | 5 | $(8.43\pm0.42)\times 10^9~M_\odot$ |
| Tail SFE | 0.32 | not stated | Gyr^-1 | 5 | the corresponding SFE is 0.32 $\mathrm{Gyr^{-1}}$ |
| Luminosity ratio vs Emonts+25 in same region | 1.8 | not stated | dimensionless | 3 | which is 1.8 times higher |

## Qualitative findings

- CO extends from NGC 7319 along the inner tail and north of it, unlike HI  
  > "A new finding from our observations is that molecular gas extends from NGC 7319 along the inner tail and further north beyond the tail." (3.1 Global properties)

## Claim tuples

- H: Molecular gas in SQ is more extended than previously mapped | E: Wide-field ALMA TP CO(1-0) mapping | R: Gas over ~120x80 kpc incl. tail and north intergalactic regions | F: Extended molecular gas inconsistent with HI morphology | **supported**
- H: Star formation is globally efficient in SQ | E: SFE from SFR and CO mass | R: 0.29-0.70 Gyr^-1 | F: Comparable to or lower than nearby star-forming galaxies | **supported**
- H: Tail molecular gas formed only in situ | E: CO distribution compared to HI | R: CO traces inner tail from NGC 7319 toward SQ-B | F: Possible additional contribution from gas stripped from NGC 7319 | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: TP data are free from imaging uncertainties and missing flux of interferometers  
  > "they are free from uncertainties that can potentially be introduced in the imaging process of interferometric data" (Introduction)
- How they decided it was enough: _not stated_
- Limitation (authors): Large beam may blend gas from different regions, causing apparent connections; alpha_CO uncertain so mass may be an upper limit  
  > "the limited resolution of the TP observations may partly cause the apparent connection between NGC 7319 and regions such as SQ-A or SQ-B" (3.3 Molecular gas in tidal tails)
- Caveat (inferred, ours): Velocity-component boundaries and dispersion thresholds are somewhat subjective
- Caveat (inferred, ours): Galactic alpha_CO applied across shocked and tidal regions
- Caveat (inferred, ours): Residual baseline from FFT filtering could bias faint tail flux
- Caveat (inferred, ours): Stripping interpretation rests on 58 arcsec beam

## Reproducibility

- Data public (paper): Project code given; public status not explicitly stated  
  > "as part of project 2023.1.01101.S (PI: F. Maeda)" (Observation and Data Reduction)
- Products in archive: _not stated_
- Missing: sdimaging parameters
- Missing: FFT filter pixel selection
- Missing: region definitions for mass sums
- Missing: HII region/SFR tables per velocity range
- Data volume (inferred): Large raw (197 EBs TP); about tens of GB
- Score (inferred): 3/5, Data identified and processing outlined, but imaging and region-selection details are missing.
- Rediscovery candidate: no, Key numbers depend on unspecified imaging and region choices and external SFR tables.

## Links

- Companion: Emonts et al. 2025 (cite: Emonts_2025ApJ) (7m CO(2-1) of SQ, compared)
- Companion: Yamamoto et al., in prep. (Combination of TP with 7m CO(1-0))

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
 "numeric_results": 9,
 "numeric_problems": 0,
 "fill": {
  "facts": 70,
  "stated": 39,
  "rate": 0.557
 },
 "evidence_ok": true
}
```
