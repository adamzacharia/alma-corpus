# A Submillimeter Burst of S255IR SMA1: The Rise and Fall of Its Luminosity

`2018ApJ...863L..12L` | The Astrophysical Journal Letters 2018 | first author: Liu, Sheng-Yuan | arXiv: 1808.02192 | DOI: 10.3847/2041-8213/aad63a

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation
- Question: Does the massive YSO S255IR SMA1 show a submillimeter continuum and methanol maser burst, and how do its luminosity and duration compare with episodic accretion?  
  > "Does a similar luminosity variation phenomenon occur in the massive star formation process?" (Introduction)
- Target **S255IR SMA1**: coordinates _not stated_; z/distance 1.78 (+0.12/-0.11) kpc  
  > "S255IR is a massive cluster formation region with a bolometric luminosity of several 10$^{4}$ L$_\odot$ at a distance of 1.78$^{+0.12}_{-0.11}$ kpc (cite: Burns16)." (Introduction); distance from Burns et al. 2016  
  > "S255IR is a massive cluster formation region with a bolometric luminosity of several 10$^{4}$ L$_\odot$ at a distance of 1.78$^{+0.12}_{-0.11}$ kpc (cite: Burns16)." (Introduction)

## Data provenance

- ALMA projects: 2015.1.00500.S
- bands: _not stated_
- frequencies and spectral setup: maser window at 349.0 GHz, 0.244 MHz channels, 0.488 MHz resolution (0.42 km/s), Hanning smoothed  
  > "The window at 349.0 GHz, covering the methanol maser, has a spectral channel width of 0.244 MHz and a resolution of 0.488 MHz (0.42 km s$^{-1}$) with online Hanning-smooth applied." (Observations)
- continuum bandwidth: 1875.0 MHz centered at 335.4 GHz  
  > "The continuum window is centered at 335.4 GHz with a bandwidth of 1875.0 MHz." (Observations)
- arrays: _not stated_
- configurations: 2017 Jul: C40-5, 43 antennas; 2016 Apr C36-2/3; 2016 Sep C36(5)/6 [=C40-6]; SMA compact  
  > "Configuration & Compact & C36-2/3 & C36(5)/6 \[=C40-6\] & C40-5" (Table 1)
- baselines: 15 m to 3.0 km for the 2017 July epoch  
  > "The projected baselines range between 15 m and 3.0 km." (Observations)
- angular resolution: 0.14 arcsec for the comparison of 2016 Sep and 2017 Jul  
  > "we display in Figures [3](#fig:f3) (a)—(b) the high (0.14$''$) resolution 900 ${\mu}$m continuum observed in 2016 September and 2017 July." (Results)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: SMA 135 min; ALMA 43, 86, 43 min  
  > "On-source time (minutes)& 135 & 43 & 86 & 43" (Table 1)
- observing dates: SMA 2010 Dec 15; ALMA 2016 Apr 21, 2016 Sep 09, 2017 Jul 20  
  > "Observation date & 2010 Dec 15 & 2016 Apr 21 & 2016 Sep 09 & 2017 Jul 20" (Table 1)
- pi or archival as stated: _not stated_
- Line: CH3OH 14_1-14_0 A-+ maser (349.1 GHz)
- Other facility **SMA**: 2010 Dec 343 GHz continuum, pre-burst reference epoch  
  > "The SMA observations conducted in 2010 had been described in (cite: Zinchenko15)." (Observations)
- External data: First two ALMA epochs (2016 Apr, 2016 Sep) and the SMA 2010 data  
  > "The ALMA observations include three epochs, with the first two being introduced by (cite: Zinchenko17)." (Observations) [from Zinchenko17; Zinchenko15]
- External data: Pre-burst and 2016 Feb bolometric luminosity 3e4 to 1.6e5 Lsun  
  > "The bolometric luminosity of S255IR SMA1/NIRS3 grew from $3\times 10^4$ L$_\odot$ to $1.6 \times 10^5$ L$_\odot$, a factor of $\sim$ 5.5 increase." (Discussion) [from Caratti17]

## Processing

### Calibration

- pipeline or manual: calibration and reduction with CASA, delivered by the observatory  
  > "The calibration and reduction of ALMA data were carried out with the Common Astronomy Software Applications (cite: McMullin07) and delivered by the observatory." (Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0750+1231 flux, J0854+2006 bandpass, J0613+1708 gain  
  > "J0854+2006 and J0750+1231 were used as the bandpass and flux calibrators, respectively, and J0613+1708 served as the complex gain calibrator." (Observations)
- flux scale uncertainty: SMA absolute flux uncertainty 20-30%  
  > "the discrepancy likely arises from the absolute flux calibration uncertainties, which can be as much as 20 – 30% for the SMA observations in particular." (Results)
- self calibration: applied separately per epoch, as in Zinchenko17; gain solutions applied to continuum and 349.0 GHz window  
  > "Self-calibration were employed separately for different observational epochs as described in (cite: Zinchenko17) for improving the imaging quality and dynamical range." (Observations)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: continuum made from continuum window after obvious spectral contamination removed  
  > "Further imaging of the continuum emission is achieved by using the visibilities in the continuum window after obvious spectral contamination removed." (Observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: circular 0.14 arcsec beam  
  > "restoring the final resolution to a circular 0.14$''$ beam" (Results)
- final rms: _not stated_

### Inherited from earlier work

- Same spectral windows as Zinchenko17  
  > "The same set of spectral windows in (cite: Zinchenko17) are again employed." (Observations) [from (cite: Zinchenko17)]
- Self-calibration procedure  
  > "Self-calibration were employed separately for different observational epochs as described in (cite: Zinchenko17)" (Observations) [from (cite: Zinchenko17)]
- Mock SMA imaging approach from ALMA map  
  > "similar to the approach adopted in (cite: Hunter17)" (Results) [from (cite: Hunter17)]

### Not stated but needed to reproduce (our reading)

- CASA version
- Self-calibration solution intervals and reference model
- Weighting/robust, cleaning parameters and masks
- Which channels were excluded as contaminated
- Aperture center coordinates for photometry
- Details of the mock SMA image process and amplitude scaling

## Analysis recipe

1. **Compare 2010 SMA with 2016 ALMA continuum**: Resample ALMA map with SMA uv-coverage, image, scale SMA by 20%, subtract to make a difference map  
  > "we made mock SMA observations by re-sampling and imaging the ALMA map (panel (b)) using the $uv$-coverage achieved by the 2010 SMA observation" (Results)
   - software: CASA
   - parameter: SMA image scaled up by 20%  
  > "For that, (a) was scaled up by 20%, reasonably within calibration uncertainties, and subtracted from (c)." (Results)
   - assumption: SMA2 unchanged  
  > "if we assume that SMA2 has not changed" (Results)
   - fitting: _not stated_
   - validation: _not stated_
2. **Compare ALMA epochs 2016 Sep and 2017 Jul**: Images in common uv range 14.5-1765 m restored to a 0.14 arcsec circular beam, then subtracted  
  > "we generated synthesis images by using data within a common $uv$-range (14.5—1765 m) well shared by both observations" (Results)
   - software: CASA
   - fitting: _not stated_
   - validation: Visibilities of first two epochs compared in overlapping uv range  
  > "between the first two epochs the visibilities at overlapping $uv$ ranges are fully compatible" (Results)
3. **Convert flux changes to luminosity change**: Dust temperature change implies luminosity scaling as T^4  
  > "as total emission of the dust envelope scales with temperature to the 4th power (cite: Hunter17)" (Discussion)
   - assumption: Flux variation reflects dust temperature change; bulk dust column density and opacity unchanged  
  > "its brightness and flux density variation is reflecting a dust temperature change, unless there is a dramatic modification in dust column density and/or opacity" (Discussion)
   - fitting: _not stated_
   - validation: Compared with Caratti17 SED luminosity boost  
  > "This boost factor appears to be smaller than what we derived." (Discussion)

## Software

- **CASA** : calibration, reduction, imaging  
  > "The calibration and reduction of ALMA data were carried out with the Common Astronomy Software Applications (cite: McMullin07)" (Observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| SMA1 peak intensity 2010 (scaled SMA) | 0.50 | not stated | Jy/beam | 1 | the peak intensity in SMA1 rose from 0.50 Jy/beam in 2010 (after scaling) to 1.1 Jy/beam in 2016. |
| SMA1 peak intensity 2016 Apr | 1.1 | not stated | Jy/beam | 1 | the peak intensity in SMA1 rose from 0.50 Jy/beam in 2010 (after scaling) to 1.1 Jy/beam in 2016. |
| SMA1 total flux density 2010 to 2016 | 0.73 to 1.40 | not stated | Jy | 1 | picked up from 0.73 Jy in 2010 (also after scaling) to 1.40 Jy in 2016 |
| SMA1 peak intensity 2016 Sep to 2017 Jul | 0.237 to 0.137 (131 K to 76 K) | not stated | Jy/beam | 2 | dropped from 0.237 Jy/beam, corresponding to a brightness temperature of 131 K, in 2016 September to 0.137 Jy/beam, or equivalently 76 K, in 2017 July. |
| SMA1 flux density decrease in 0.5 arcsec aperture | 33 | not stated | percent | 2 | The flux density within a 0.5$''$ aperture centered at SMA1 decreased by 33% during this interval. |
| CH3OH maser peak 2017 Jul | 2380 K (3.6 Jy/beam) | not stated | K | 2 | has discernibly fallen to 2380 K (3.6 Jy/beam) in 2017 July, a reduction of 40%. |
| Luminosity increase factor in 2016 | ~16 | not stated | dimensionless | 3 | suggests an overall bolometric luminosity increase by a factor of about 16 in S255IR SMA1 |
| Luminosity decrease 2016-2017 | ~8 | not stated | dimensionless | 3 | as well as a factor of $\sim$ 8 decrease in its luminosity |

## Qualitative findings

- Burst lasted about two years; continuum and Class II methanol maser brightened and faded together, consistent with a disk-mediated accretion event similar to milder EXor-like bursts  
  > "marks the burst duration at around two years." (Discussion)

## Claim tuples

- H: SMA1 submillimeter continuum brightened during the 2015 flare | E: Compared 2010 SMA with 2016 ALMA using mock SMA imaging | R: Peak and flux density roughly doubled | F: Submillimeter flare accompanies the luminosity burst | **supported**
- H: The burst faded by 2017 | E: Compared ALMA 2016 Sep and 2017 Jul in common uv range | R: Continuum peak dropped to 0.137 from 0.237 Jy/beam; maser fell 40% | F: Burst waned within about two years | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Negative spectral index rejected as the explanation for SMA's lower intensity; calibration uncertainty favored  
  > "Instead of owing this to a negative spectral index, the discrepancy likely arises from the absolute flux calibration uncertainties" (Results)
- How they decided it was enough: _not stated_
- Limitation (authors): Fourth-power temperature dependence: 10% flux uncertainty gives 40% luminosity uncertainty  
  > "a 10% uncertainty in the flux density, hence temperature measurement could lead to 40% uncertainty in the derived luminosity" (Discussion)
- Caveat (inferred, ours): Luminosity scaling assumes optically thick/thin-independent temperature change and ignores dust column changes
- Caveat (inferred, ours): SMA-ALMA comparison relies on an ad hoc 20% scaling
- Caveat (inferred, ours): No fitted uncertainties on photometry

## Reproducibility

- Data public (paper): ALMA project cited by code; public status not stated  
  > "This Letter makes use of the following ALMA data: ADS/JAO.ALMA #2015.1.00500.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Self-calibration details
- Missing: Imaging parameters
- Missing: SMA data reduction (in Zinchenko15)
- Missing: Photometry method details
- Data volume (inferred): ~100-300 GB for three ALMA epochs
- Score (inferred): 3/5, Data identified and a simple difference analysis, but imaging and selfcal parameters are inherited or missing.
- Rediscovery candidate: no, Only the 2017 epoch project is listed; earlier epochs and imaging recipe are incomplete.

## Links

- Method: Zinchenko17 (Earlier ALMA epochs, spectral setup, self-calibration)
- Method: Hunter17 (Mock-observation approach and luminosity scaling)
- Companion: Caratti17 (NIR flare and luminosity boost)
- Companion: Cesaroni18 (VLA radio flare)

## Checks

```json
{
 "quotes": 48,
 "quotes_ok": 48,
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
  "facts": 65,
  "stated": 35,
  "rate": 0.538
 },
 "evidence_ok": true
}
```
