# Revealing the CO X-factor in Dark Molecular Gas through Sensitive ALMA Absorption Observations

`2020ApJ...889L...4L` | The Astrophysical Journal Letters 2020 | first author: Luo, Gan | arXiv: 1912.08984 | DOI: 10.3847/2041-8213/ab6337

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: milky_way_ism, astrochemistry
- Question: What are the properties of CO and HCO+ in diffuse, cold dark molecular gas, and what is the CO X-factor there, as probed by absorption toward continuum sources?  
  > "we aim to study the properties of molecules in diffuse, cold environments, where CO tends to be under-abundant and/or sub-thermally excited." (abstract)
- Target **13 mm-wave calibrator sources (3C454.3, 3C120, B0420-014, B0607-157, B0627-199, B1730-130, B1741-038, B1742-078, B1933-400, B1954-388, B2223-052, B2227-088, B2243-123)**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2015.1.00503.S
- bands: _not stated_
- frequencies and spectral setup: CO(1-0), HCO+(1-0) at 61.035 kHz (0.21 and 0.18 km/s); CO(2-1), HCO+(3-2) toward 3C454.3 at 122.070 kHz (0.159 and 0.137 km/s)  
  > "The frequency resolution of the CO (2–1) and HCO$^+$ (3–2) lines is 122.070 KHz, which corresponds to velocity resolutions of 0.159 $\mathrm{km\, s^{-1}\, }$at 230 GHz and 0.137 $\mathrm{km\, s^{-1}\, }$at 267 GHz." (2.1 Molecular lines)
- continuum bandwidth: 1.8 GHz bandwidth, 31 MHz resolution  
  > "The continuum data covers a 1.8 GHz bandwidth with a frequency resolution of 31 MHz." (2.1 Molecular lines)
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: tau_rms ~0.002 (CO), ~0.0008 (HCO+)  
  > "down to $\mathrm{\tau_{rms}^{CO} \sim 0.002}$ and $\mathrm{\tau_{rms}^{HCO^+} \sim 0.0008}$" (abstract)
- time on source: _not stated_
- observing dates: 2015  
  > "We observed CO (1–0) and HCO$^+$ (1–0) spectra toward 13 strong continuum sources with ALMA during 2015." (2.1 Molecular lines)
- pi or archival as stated: _not stated_
- Line: CO 1-0 (not stated)
- Line: CO 2-1 (not stated)
- Line: HCO+ 1-0 (not stated)
- Line: HCO+ 3-2 (not stated)
- Other facility **Pan-STARRS1/2MASS/Gaia E(B-V) map**: E(B-V) reddening to estimate total gas column density  
  > "We use the E(B-V) map of (cite: Green2018; Green2019) to estimate total gas column density." (2.2 Archival reddening data)
- Other facility **Millennium survey, GASS, EBHIS**: HI column densities  
  > "H  data for other sources are taken from the Parkes Galactic All Sky Survey (GASS)" (2.3 Archival H data)
- External data: HI column densities toward 3C454.3 and 3C120 from Millennium survey  
  > "We adopted the corrected H  column density derived from ON-OFF observations in the millennium survey for 3C454.3 and 3C120" (2.3 Archival H data) [from (cite: Heiles2003a; Nguyen2018)]
- External data: E(B-V) map  
  > "We use the E(B-V) map of (cite: Green2018; Green2019) to estimate total gas column density." (2.2 Archival reddening data) [from (cite: Green2018; Green2019)]
- External data: N_H/E(B-V) = 5.8e21 and (9.4±1.6)e21 cm-2 mag-1 conversions  
  > "$\mathrm{N_H /E(B-V) = 5.8 \times 10^{21} cm^{-2} mag^{-1}}$ (cite: Bohlin1978)" (5 HCO+ as a molecular gas tracer) [from (cite: Bohlin1978); (cite: Nguyen2018)]

## Processing

### Calibration

- pipeline or manual: standard ALMA pipeline with separate bandpass, phase, flux calibrators; self-calibration for 3C454.3, 3C120 and their bandpass calibrators  
  > "Thus, we performed our calibration using the standard ALMA pipeline, which uses separate bandpass, phase, and flux calibrators." (3.1 Detections and self-calibration)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: Self-calibration on 3C120, 3C454.3, 2148+0657, 2232+1143 to remove bandpass-calibrator contamination  
  > "Data reduction toward 3C454.3, 3C120, (and also 2148+0657 and 2232+1143, which were added to our sample) was therefore conducted by self-calibration." (3.1 Detections and self-calibration)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: Briggs weighting, Clean algorithm (robust not given)  
  > "Both calibrated continuum and spectral images were deconvolved with Briggs weighting using the Clean algorithm." (2.1 Molecular lines)
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
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Kinetic temperature 100 K for diffuse ISM  
  > "Adopting a kinetic temperature of 100 K for the diffuse ISM (cite: Goldsmith2013; Gerin2015)" (4 Radiative transfer analysis) [from (cite: Goldsmith2013; Gerin2015)]
- o-H2/p-H2 = 1e-3  
  > "\[o-H$_2$\]/\[p-H$_2$\] = 10$^{-3}$; (cite: Bourlot1991; Dislaire2012)" (4 Radiative transfer analysis) [from (cite: Bourlot1991; Dislaire2012)]

### Not stated but needed to reproduce (our reading)

- Robust value, cell size, image size, masking for imaging
- Spectral extraction method and continuum-free channels
- Number of Gaussian components and fitting priors/initial guesses
- RADEX grid ranges and collision-rate files
- How W_CO was reconstructed from tau and Tex (integration limits)
- Which sources enter the X-factor average
- Beam size, rms in K, CASA/pipeline version
- Source coordinates and background brightness temperatures per source

## Analysis recipe

1. **Calibrate data and self-calibrate bright sources**: Standard ALMA pipeline; self-calibration for 3C454.3, 3C120 and bandpass calibrators  
  > "Thus, we performed self-calibration on 3C120 and 3C454.3, as well as their calibrators." (3.1 Detections and self-calibration)
   - software: CASA
   - fitting: _not stated_
   - validation: HCO+ absorption detected toward bandpass calibrators confirmed emission features were contamination  
  > "HCO$^+$ (1–0) absorption was detected towards two bandpass calibrators (2232+1143 and 2148+0657), confirming that the “emission” components above are indeed contamination." (3.1 Detections and self-calibration)
2. **Derive optical depth profiles and fit Gaussians**: e^-tau from radiative transfer; multi-Gaussian fit to e^-tau profiles  
  > "The $\mathrm{\tau_\upsilon}$ of each velocity component was derived by fitting the $\mathrm{e^{-\tau_\upsilon}}$ profiles with multiple Gaussian components." (3.2 Gaussian fitting of absorption profiles)
   - assumption: For 3C454.3 Tbg>>Tex term neglected; other sources use Tex=4.1 K (CO), 2.7 K (HCO+)  
  > "For these, we adopt representative values of $\mathrm{T_{ex}}$ computed for 3C454 (4.1 K for CO and 2.7 K for HCO$^+$ in Section [4](#sec:analysis))." (3.2 Gaussian fitting of absorption profiles)
   - fitting: _not stated_
   - validation: _not stated_
3. **RADEX modeling for Tex and column densities**: Chi2 minimisation over n_H2, N_CO, N_HCO+ fitting four spectra toward 3C454.3; other sources use n_H2 from 3C454.3  
  > "we vary the free parameters $\mathrm{n_{H_2}}$, $\mathrm{N_{CO}}$, and $\mathrm{N_{HCO^+}}$ to find the optimum solutions by minimizing $\chi^2$" (4 Radiative transfer analysis)
   - software: RADEX
   - parameter: Tkin = 100 K  
  > "Adopting a kinetic temperature of 100 K for the diffuse ISM" (4 Radiative transfer analysis)
   - fitting: chi2 minimisation  
  > "we vary the free parameters $\mathrm{n_{H_2}}$, $\mathrm{N_{CO}}$, and $\mathrm{N_{HCO^+}}$ to find the optimum solutions by minimizing $\chi^2$" (Radiative transfer analysis)
   - validation: Varying Tkin 10-300 K changes Tex and N by <1% (CO), 0.1% (HCO+)  
  > "By varying the assumed $\mathrm{T_{kin}}$ value from 10 to 300 K, we found that the fractional difference are within 1$\%$ for $\mathrm{T_{ex} (CO)}$ and $\mathrm{N_{CO}}$" (4 Radiative transfer analysis)
4. **Derive N_H2 and abundances**: N_H2=(N_H-N_HI)/2 with N_H from E(B-V)  
  > "$\mathrm{N_{H_2} = \frac{N_H - N_{H\,{\uppercase{\romannumeral 1}}\ }}{2}}$" (5 HCO+ as a molecular gas tracer)
   - assumption: N_H/E(B-V)=5.8e21 for E(B-V)>0.5, (9.4±1.6)e21 for E(B-V)<0.5; Av/E(B-V)=3.1  
  > "we adopt the value of $\mathrm{(9.4 \pm 1.6) \times 10^{21} cm^{-2} mag^{-1}}$ for sightlines with $\mathrm{E(B-V)<0.5\,mag}$" (5 HCO+ as a molecular gas tracer)
   - fitting: _not stated_
   - validation: _not stated_
5. **Compute CO X-factor**: Reconstruct W_CO from tau and Tex; X_CO = N_H2/W_CO  
  > "We have reconstructed the CO integrated intensity from the $\tau$ and $\mathrm{T_{ex}}$ obtained from our RADEX modeling." (6 The CO X-factor)
   - fitting: _not stated_
   - validation: Compared with Taurus results and simulations  
  > "Our results are in agreement with observations in regions without $\mathrm{^{12}CO}$ and $\mathrm{^{13}CO}$ emission detections in Taurus (cite: Pineda2010)." (6 The CO X-factor)

## Software

- **CASA** : Calibration of raw data and imaging  
  > "The calibration of the raw data was performed using CASA (Common Astronomy Software Applications)" (2.1 Molecular lines)
- **RADEX** : Modeling observed absorption spectra  
  > "we are able to model the observed spectra with RADEX (cite: Van2007)." (4 Radiative transfer analysis)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Tex CO toward 3C454.3 | 4.1 | not stated | K | 3 | The derived excitation temperature values are 4.1 K for CO and 2.7 K for HCO$^+$. |
| Tex HCO+ toward 3C454.3 | 2.7 | not stated | K | 3 | The derived excitation temperature values are 4.1 K for CO and 2.7 K for HCO$^+$. |
| n_H2 toward 3C454.3 | 87 | not stated | cm^-3 | 3 | The best fit values for $\mathrm{n_{H_2}}$, $\mathrm{N_{CO}}$, and $\mathrm{N_{HCO^+}}$ toward 3C454.3 are 87 $\mathrm{cm^{-3}}$, 3.6$\times 10^{14}$ $\mathrm{cm^{-2}}$, and 1.8$\times 10^{11}$ $\mathrm{cm^{-2}}$ |
| N_CO toward 3C454.3 | 3.6e14 | not stated | cm^-2 | 3 | 3.6$\times 10^{14}$ $\mathrm{cm^{-2}}$ |
| Pearson correlation N_HCO+ vs N_H2 | 0.93 | not stated | dimensionless | 4 | are 0.33 for CO and 0.93 for HCO$^+$ |
| Pearson correlation N_CO vs N_H2 | 0.33 | not stated | dimensionless | 4 | are 0.33 for CO and 0.93 for HCO$^+$ |
| Mean CO abundance | 2.1e-6 | 1.1e-6 | relative to H2 | 4 | $\mathrm{(2.1 \pm 1.1) \times 10^{-6}}$ for CO and $\mathrm{(1.7 \pm 0.3) \times 10^{-9}}$ for HCO$^+$ |
| Mean HCO+ abundance | 1.7e-9 | 0.3e-9 | relative to H2 | 4 | $\mathrm{(1.7 \pm 0.3) \times 10^{-9}}$ for HCO$^+$ |
| CO X-factor | 14e20 | 3e20 | cm^-2 (K km/s)^-1 | 5 | The average X-factor we obtain in our sightlines is (14 $\pm$ 3) $\times$ 10$^{20}$ cm$^{-2}$ (K $\mathrm{km\, s^{-1}\, }$)$^{-1}$ |

## Qualitative findings

- CO and HCO+ absorption detected toward 6 of 13 sources; HCO+ detected without CO in two sightlines  
  > "Both CO (1–0) and HCO$^+$ (1–0) absorption lines were detected toward 6 of 13 sources" (3.1 Detections and self-calibration)

## Claim tuples

- H: CO and HCO+ excitation in diffuse gas is close to the CMB, explaining emission undercounting | E: Multi-transition RADEX fit toward 3C454.3 | R: Tex = 4.1 K (CO), 2.7 K (HCO+) | F: Tex near CMB makes the gas hard to detect in emission | **supported**
- H: HCO+ traces H2 better than CO in diffuse gas | E: Correlate N_mol with N_H2 | R: P ~0.93 for HCO+, ~0.33 for CO | F: HCO+ is a better H2 tracer | **supported**
- H: The CO X-factor in dark molecular gas exceeds the Galactic mean | E: Reconstruct W_CO and compare to N_H2 | R: (14±3)e20 | F: About 6 times Milky Way average | **supported**

## Reasoning

- Why this data: Absorption against strong point sources is more sensitive and less biased for cold diffuse gas  
  > "quasar absorption can be a much more sensitive and less biased probe of cold molecular gas" (1 Introduction)
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): HI column densities are lower limits for most sightlines (optically thin assumption)  
  > "for the majority of sightlines represents a lower limit under the optically thin assumption." (5 HCO+ as a molecular gas tracer)
- Caveat (inferred, ours): N_H from E(B-V) with variable gas-to-reddening ratio dominates the N_H2 uncertainty
- Caveat (inferred, ours): Tkin=100 K and a single n_H2 transferred from 3C454.3 to other sources
- Caveat (inferred, ours): Small sample (8 sightlines in table); X-factor averaging unclear
- Caveat (inferred, ours): Low-resolution HI/reddening maps vs point-source sightlines

## Reproducibility

- Data public (paper): ALMA project 2015.1.00503.S acknowledged; archival HI and reddening data public  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA$\#$2015.1.00503.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Imaging parameters
- Missing: Gaussian fitting details
- Missing: W_CO reconstruction details
- Missing: Per-source HI and background temperatures beyond Table 1
- Data volume (inferred): ~10-50 GB (13 sources, narrow-band spectral windows)
- Score (inferred): 3/5, Data are public and the RADEX/column-density chain is described, but imaging, fitting and X-factor details are missing.
- Rediscovery candidate: no, Recipe is too incomplete (fit details, W_CO reconstruction) to redo reliably.

## Links

- Method: (cite: Van2007) (RADEX non-LTE code)
- Method: (cite: Li2018) (DMG-threshold definition and absorption methodology)
- Companion: (cite: Nguyen2018) (HI absorption data and N_H/E(B-V))
- Related: Millennium survey
- Related: GASS
- Related: EBHIS
- Related: Dame2001 CO survey

## Checks

```json
{
 "quotes": 51,
 "quotes_ok": 51,
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
  "facts": 72,
  "stated": 33,
  "rate": 0.458
 },
 "evidence_ok": true
}
```
