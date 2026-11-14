# A statistical study of giant molecular clouds traced by <SUP>13</SUP>CO, C<SUP>18</SUP>O, CS, and CH<SUB>3</SUB>OH in the disk of NGC 1068 based on ALMA observations

`2017PASJ...69...18T` | Publications of the Astronomical Society of Japan 2017 | first author: Tosaki, Tomoka | arXiv: 1612.00948 | DOI: 10.1093/pasj/psw122

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, astrochemistry, star_formation
- Question: What are the physical and chemical properties of GMCs in the disk of NGC 1068, and are they linked to the larger-scale galactic environment?  
  > "to study the physical and chemical properties of giant molecular clouds (GMCs) and to test whether these GMC-scale properties are linked to the larger-scale galactic environment" (abstract)
- Target **NGC 1068**: coordinates _not stated_; z/distance 14.4 Mpc  
  > "$1''.4$ or 98 pc at a distance of 14.4 Mpc, (cite: Tully1988); (cite: Bland-Hawthorn1997)" (Introduction); distance from Tully 1988; Bland-Hawthorn et al. 1997  
  > "$1''.4$ or 98 pc at a distance of 14.4 Mpc, (cite: Tully1988); (cite: Bland-Hawthorn1997)" (Introduction)

## Data provenance

- ALMA projects: 2013.0.00060.S, 2012.1.00060.S
- bands: Band 3  
  > "was observed using the Band 3 receiver on ALMA with the 2SB dual-polarization setup" (Observations and Data Reduction)
- frequencies and spectral setup: 4 spws centred at 110.000, 109.174, 97.174, 96.741 GHz; 1.875 GHz each, 3840 channels, 0.488 MHz resolution  
  > "Each spectral window has a bandwidth of 1.875 GHz with 3840 channels, giving a total frequency coverage of 7.5 GHz and a spectral resolution of 0.488 MHz." (Observations and Data Reduction)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: compact and extended; six execution blocks  
  > "compact" (Table 1); "The ALMA observations were taken during three separated periods with six execution blocks in total." (Observations and Data Reduction)
- baselines: 5.5 kλ – 290 kλ (15–783 m)  
  > "corresponding to 5.5 k$\lambda$ – 290 k$\lambda$" (Results)
- angular resolution: 1.4 arcsec (98 pc) after convolution  
  > "The CLEANed images were then finally convolved to a circular Gaussian with the FWHM of $1''.4$" (Observations and Data Reduction)
- max recoverable scale: _not stated_
- sensitivity: 1σ = 0.64, 0.61, 0.59, 0.70 mJy/beam (13CO, C18O, CS, CH3OH) at 1.5 km/s  
  > "are 0.64, 0.61, 0.59, and 0.70 mJy beam$^{-1}$ for $^{13}$CO, C$^{18}$O, CS, and CH$_3$OH, respectively, at a velocity resolution of 1.5 km s$^{-1}$" (Observations and Data Reduction)
- time on source: 20.6–44.9 min per execution block  
  > "44.13" (Table 1)
- observing dates: 2014/07/02 – 2015/05/17  
  > "2015/05/17 16:38:48" (Table 1)
- pi or archival as stated: Cycle 2 early science, PI T. Tosaki  
  > "as a cycle 2 early science program (Project code = 2013.0.00060.S; PI name = T. Tosaki)" (Observations and Data Reduction)
- Line: 13CO J=1-0 (110.201353 GHz)
- Line: C18O J=1-0 (109.782160 GHz)
- Line: CS J=2-1 (97.980968 GHz)
- Line: CH3OH J_K=2_K-1_K group (96.74142 GHz)
- Other facility **NRO 45-m**: 13CO(1-0) single-dish flux for recovered-flux comparison  
  > "a NRO 45-m telescope measurement gives a $^{13}$CO($J$=1–0) flux of $8.9\pm0.2$ K km s$^{-1}$ in the main-beam temperature scale" (3.2)
- Other facility **IRAM 30-m**: 13CO(1-0) single-dish flux for recovered-flux comparison  
  > "the IRAM 30-m measurement gave $13.10 \pm 0.24$ K km s$^{-1}$ ((cite: Aladro2015))" (3.2)
- External data: NRO 45-m 13CO(1-0) flux 8.9±0.2 K km/s (in preparation)  
  > "(Takano et al., in preparation)" (3.2) [from Takano et al., in preparation]
- External data: IRAM 30-m 13CO(1-0) flux 13.10±0.24 K km/s  
  > "the IRAM 30-m measurement gave $13.10 \pm 0.24$ K km s$^{-1}$ ((cite: Aladro2015))" (3.2) [from (cite: Aladro2015)]
- External data: Excitation temperature Tex = 8.5 K  
  > "an excitation temperature $T_{\rm ex}$ of 8.5 K ((cite: Nakajima2015))" (3.4) [from (cite: Nakajima2015)]
- External data: [H2]/[13CO] = 5.0e5  
  > "Adopting an abundance ratio of $[{\rm H}_2]/[^{13}{\rm CO}] = 5.0 \times 10^5$ ((cite: Dickman1978))" (3.4) [from (cite: Dickman1978)]

## Processing

### Calibration

- pipeline or manual: CASA calibration; pipeline for the last four datasets  
  > "Version 4.3.1 of the program was used for the first two data sets, whereas the remaining four data sets were processed using the version 4.2.2 with pipeline." (Observations and Data Reduction)
- casa version: CASA 4.3.1 and 4.2.2 (calibration); 4.5.0 (imaging)  
  > "The image reconstruction from the calibrated visibilities and deconvolution were done with the task `CLEAN` in CASA version 4.5.0." (Observations and Data Reduction)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Mars, Uranus, Neptune  
  > "Mars, Uranus, and Neptune were used as primary flux calibrators." (Observations and Data Reduction)
- flux scale uncertainty: better than 10% (5% adopted in flux comparison)  
  > "The resultant accuracy of the absolute flux scale is reported to be better than 10% according to the ALMA Technical Handbook" (Observations and Data Reduction)
- self calibration: _not stated_

### Imaging

- task: CASA clean  
  > "The image reconstruction from the calibrated visibilities and deconvolution were done with the task `CLEAN` in CASA version 4.5.0." (Observations and Data Reduction)
- deconvolver: multi-scale CLEAN  
  > "we employed the multi-scale CLEAN algorithm" (Observations and Data Reduction)
- weighting robust: Briggs; robust = 0.4 (13CO, C18O), 0.2 (CS), 0.1 (CH3OH)  
  > "`robust` = 0.4 for $^{13}$CO and C$^{18}$O, 0.2 for CS, and 0.1 for CH$_3$OH" (Observations and Data Reduction)
- uv taper: _not stated_
- cell size: 0.25 arcsec  
  > "We adopt the `multiscale = [0, 10, 25]` with `cell = '0.25arcsec'`" (Observations and Data Reduction)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: [0, 10, 25] pixels  
  > "We adopt the `multiscale = [0, 10, 25]` with `cell = '0.25arcsec'`" (Observations and Data Reduction)
- continuum subtraction: uvcontsub on visibilities  
  > "continuum emission was subtracted from the visibilities using the task `uvcontsub`" (Observations and Data Reduction)
- line free channels: determined from initial naturally weighted imaging; ranges not given  
  > "After the initial imaging with natural weighting, we determined the line-free channels" (Observations and Data Reduction)
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: convolved to circular 1.4 arcsec Gaussian  
  > "The CLEANed images were then finally convolved to a circular Gaussian with the FWHM of $1''.4$" (Observations and Data Reduction)
- final beam: native 1.39x1.09, 1.33x1.06, 1.38x1.12, 1.39x1.12 arcsec; final 1.4 arcsec circular  
  > "These parameters give the native beam sizes of $1''.39 \times 1''.09$, $1''.33 \times 1''.06$, $1''.38 \times 1''.12$, and $1''.39 \times 1''.12$" (Observations and Data Reduction)
- final rms: 0.64, 0.61, 0.59, 0.70 mJy/beam per 1.5 km/s channel  
  > "are 0.64, 0.61, 0.59, and 0.70 mJy beam$^{-1}$ for $^{13}$CO, C$^{18}$O, CS, and CH$_3$OH, respectively" (Observations and Data Reduction)

### Inherited from earlier work

- CLUMPFIND cloud decomposition  
  > "We applied the `CLUMPFIND` algorithm ((cite: Williams1994); (cite: Rosolowsky2005a))" (3.3) [from (cite: Williams1994); (cite: Rosolowsky2005a)]
- Virial mass formula with beta=1  
  > "Here we adopt $\beta=1$ for consistency with previous similar measurements." (3.4) [from (cite: MacLaren1988); Hirota2011; DonovanMeyer2012]
- Truncated power-law mass function  
  > "(e.g., (cite: Mckee1997); (cite: Wong2011); (cite: Colombo2014))" (4.2) [from McKee & Williams 1997; Wong 2011; Colombo 2014]

### Not stated but needed to reproduce (our reading)

- Line-free channel ranges for uvcontsub
- Clean threshold, masks and iteration count
- CLUMPFIND implementation and exact parameters beyond threshold and increment (e.g. velocity handling, pixel-based area)
- Fitting method, binning and error estimation for the truncated power law
- Calibration/flux-scaling details for datasets and which pipeline version per dataset
- Primary-beam correction details
- Velocity-width definition per cloud and treatment of beam deconvolution
- Position of FOV centre (blank in text)

## Analysis recipe

1. **Image line cubes**: CASA clean with Briggs weighting, multiscale, uvcontsub, convolution to 1.4 arcsec  
  > "we created images using Briggs weighting with different robust parameters" (Observations and Data Reduction)
   - software: CASA
   - parameter: robust 0.4/0.4/0.2/0.1; multiscale [0,10,25]; cell 0.25 arcsec; 1.5 km/s channels  
  > "We adopt the `multiscale = [0, 10, 25]` with `cell = '0.25arcsec'`" (Observations and Data Reduction)
   - fitting: _not stated_
   - validation: _not stated_
2. **Check recovered flux against single dish**: Convolve 13CO cube to 16" and 21", compare integrated flux with NRO 45-m and IRAM 30-m  
  > "First, the $^{13}$CO($J$=1–0) data cube was convolved to $16''$, the beam size of the NRO 45-m telescope at 110 GHz." (3.2)
   - fitting: _not stated_
   - validation: ALMA/45-m = 84±13%, ALMA/30-m = 65±7%  
  > "ALMA/45-m = $84 \pm 13$%, and ALMA/30-m = $65 \pm 7$%" (3.2)
3. **Identify GMCs**: CLUMPFIND on 13CO cube; remove clumps smaller than beam  
  > "We adopt a peak threshold of 8$\sigma$ (5.12 mJy beam$^{-1}$) and a contour increment of 4$\sigma$." (3.3)
   - software: CLUMPFIND
   - parameter: threshold 8σ, increment 4σ; 265 clumps → 187 after excluding diameter < 1.4 arcsec  
  > "This resulted in the detection of 265 clumps." (3.3)
   - fitting: _not stated_
   - validation: _not stated_
4. **Derive LTE gas mass and virial mass**: Optically thin LTE column density × clump area; virial mass with beta=1  
  > "which assumes local thermodynamic equilibrium (LTE) and optically thin emission" (3.4)
   - assumption: [H2]/[13CO]=5.0e5, Tex=8.5 K, beta=1  
  > "an excitation temperature $T_{\rm ex}$ of 8.5 K ((cite: Nakajima2015))" (3.4)
   - fitting: _not stated_
   - validation: Compared Mvir vs M13CO; average values similar  
  > "is similar to that of $M_{^{13}{\rm CO}}$" (3.4)
5. **Fit GMC mass function**: Fit truncated power law to integral mass distribution for M>1e5 Msun  
  > "The fit to the data (for $M>10^5 M_\odot$) gives the slope $\gamma=-1.25\pm0.07$" (4.2)
   - fitting: truncated power law N(M'>M)=N0[(M/M0)^(γ+1)-1]; fitting method not stated  
  > "Here we adopt a truncated power law" (4.2)
   - validation: Comparison with MW, M51, NGC 300 slopes  
  > "is significantly shallower compared with those of Galactic GMCs ($\gamma = -1.6$: (cite: Williams1997), $\gamma = -1.9$: (cite: Heyer2001)) and the disk GMCs in M51 ($\gamma = -1.8$ to $-2.5$, (cite: Colombo2014)) and NGC 300" (Discussion, Mass function of GMCs in the disk of NGC 1068)
6. **Line ratios and methanol vs velocity width**: Integrated intensities per GMC, ratios to 13CO, compare linewidths of methanol-detected vs non-detected GMCs with two-sample KS test  
  > "a two-sample Kolmogorov-Smirnov test gives a $p$ value of less than $10^{-5}$" (4.4)
   - parameter: detection = peak > 3σ  
  > "187, 182, and 121 GMCs with peak intensities of larger than $3\sigma$ are detected for C$^{18}$O, CS and CH$_3$OH, respectively." (3.4)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.3.1, 4.2.2, 4.5.0: Calibration, clean imaging, uvcontsub, immoments  
  > "Calibration of the raw visibility data was conducted using the Common Astronomy Software Applications (CASA" (Observations and Data Reduction)
- **CLUMPFIND** : GMC identification in 13CO cube  
  > "We applied the `CLUMPFIND` algorithm" (3.3)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Number of GMCs identified | 187 | not stated | dimensionless | 3 | we have identified 187 high-significance ($> 8\sigma$) GMCs |
| GMC mass function slope γ (M≥1e5 Msun) | -1.25 | 0.07 | dimensionless | 5 | gives the slope $\gamma=-1.25\pm0.07$ |
| Maximum mass M0 | 5.92e7 | 0.63e7 | Msun | 5 | $M_0 = (5.92 \pm 0.63) \times 10^7$ $M_\odot$ |
| N0 | 54.4 | 28.2 | dimensionless | 5 | $N_0$ = $54.4 \pm 28.2$ |
| GMC 13CO mass range | 1.8e4 – 4.2e7 | not stated | Msun | 4 | ranging from $1.8 \times 10^4$ to $4.2 \times 10^7 M_\odot$ |
| Mean C18O/13CO ratio | 0.27 | 0.05 | dimensionless | 6 | fairly uniform (0.27 $\pm$ 0.05) |
| Mean velocity width, methanol-detected GMCs | 16.56 | σ = 5.61 | km/s | 6 | The mean and standard deviation are 16.56 km s$^{-1}$ and 5.61 km s$^{-1}$ for methanol-detected GMCs |
| Mean velocity width, methanol-lacking GMCs | 11.97 | σ = 4.87 | km/s | 6 | 11.97 km s$^{-1}$ and 4.87 km s$^{-1}$ for methanol-lacking GMCs |
| Recovered flux ALMA/NRO45m | 0.84 | 0.13 | dimensionless | 2 | $(18.8 \pm 0.9)}/(22.5 \pm 3.4) = 0.84 \pm 0.13$ |
| Recovered flux ALMA/IRAM30m | 0.65 | 0.07 | dimensionless | 2 | (37.2 \pm 1.9)/(57.0 \pm 5.7) = 0.65 \pm 0.07 |
| Mean GMC size and velocity width | 102 pc; 14.9 km/s | not stated | pc; km/s | 3 | The averaged size and velocity width of the identified clouds are 102 pc and 14.9 km s$^{-1}$, respectively. |

## Qualitative findings

- CH3OH/13CO ratios smallest around bar-end (<0.03) and larger along spiral arms (~0.1–0.2)  
  > "with the smallest values around the bar-end ($<$ 0.03), and larger ratios along the spiral arms ($\sim$ 0.1–0.2)" (abstract)
- Supercritical GMCs preferentially on the starburst ring  
  > "the supercritical GMCs, i.e., $M_{\rm ^{13}CO}/M_{\rm vir} > 1$, are preferentially found on the starburst ring" (4.3)

## Claim tuples

- H: Is the GMC mass function in NGC 1068 different from other disks? | E: Fit truncated power law to 13CO-based masses of 187 GMCs | R: γ=-1.25±0.07, M0≈6e7 Msun | F: Shallower slope and larger cutoff than MW, M51, NGC 300: massive clouds dominate | **supported**
- H: Do C18O/13CO ratios vary among GMCs? | E: Ratios of integrated intensities for each GMC | R: 0.27±0.05 | F: Fairly uniform | **supported**
- H: Are weak shocks responsible for CH3OH enhancement? | E: Compare velocity widths of methanol-detected and non-detected GMCs with KS test | R: Larger widths for detected GMCs, p<1e-5 | F: Suggests weak (spiral) shocks drive enhancement; temperature in bar-end also proposed, not verified | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: High 8σ CLUMPFIND threshold chosen for robust detection of rarer species and to avoid algorithm issues at low S/N  
  > "By setting such a high threshold, we can construct a robust GMC catalog which is less affected by software issues." (3.3)
- Alternative: CPROPS, dendrogram, intensity-based approaches not used; beyond scope  
  > "is beyond the scope of this paper, and such analysis will be presented elsewhere." (3.3)
- How they decided it was enough: _not stated_
- Limitation (authors): No ACA/total power data; some missing flux, though judged minor  
  > "despite the lack of Atacama Compact Array (ACA, a.k.a. Morita Array) measurements" (3.2)
- Limitation (authors): Abundance and Tex adopted from Galactic/other measurements; may vary cloud to cloud  
  > "some cloud-to-cloud variation of $T_{\rm ex}$ may exist" (3.4)
- Caveat (inferred, ours): Mass function fit method and binning unspecified; slope sensitive to completeness
- Caveat (inferred, ours): Single Tex and abundance assumed for all clouds
- Caveat (inferred, ours): CLUMPFIND resolution-limited sizes; mass/virial comparisons affected
- Caveat (inferred, ours): Shock/temperature interpretation of methanol is qualitative

## Reproducibility

- Data public (paper): Data products incl. 13CO FITS cube to be publicly available on a web page  
  > "The data products of this study, including the FITS file of the $^{13}$CO data cube, will be publicly available from a dedicated web page" (Introduction)
- Products in archive: _not stated_
- Missing: Line-free channels
- Missing: Clean threshold/mask settings
- Missing: Mass function fit procedure details
- Missing: FOV center coordinates
- Data volume (inferred): ~100–300 GB raw for six execution blocks in Band 3
- Score (inferred): 3/5, ALMA data public, imaging parameters mostly given and catalog tabulated, but CLUMPFIND settings and fit details partly missing.
- Rediscovery candidate: yes, Data public (project 2013.0.00060.S), recipe largely specified, results numeric (slope, ratios, catalog).

## Links

- Method: Williams et al. 1994; Rosolowsky & Blitz 2005 (CLUMPFIND algorithm)
- Companion: Takano et al. 2014 (cite: Takano2014) (Previous cycle 0 ALMA observations of NGC 1068)
- Related: ALMA cycle 0 NGC 1068 observations
- Related: PAWS

## Checks

```json
{
 "quotes": 80,
 "quotes_ok": 80,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [
  "2013.0.00060.S"
 ],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 11,
 "numeric_problems": 0,
 "fill": {
  "facts": 81,
  "stated": 58,
  "rate": 0.716
 },
 "evidence_ok": true
}
```
