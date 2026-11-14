# A Tight Relation between Spiral Arm Pitch Angle and Protoplanetary Disk Mass

`2019ApJ...877..100Y` | The Astrophysical Journal 2019 | first author: Yu, Si-Yue | arXiv: 1904.12781 | DOI: 10.3847/1538-4357/ab1d65

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type archival_reuse

## Science

- Fields: protoplanetary_disks
- Question: How does the pitch angle of the dominant spiral Fourier mode in protoplanetary disks depend on disk properties, especially disk mass?  
  > "We aim to establish the dependence of pitch angle on the properties of protoplanetary disks to probe the physical origin of spiral arms." (Introduction)
- Target **Elias 2-27**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_
- Target **IM Lup**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_
- Target **WaOph 6**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_
- Target **AS 205**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_
- Target **HT Lup**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2016.1.00484.L
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Other facility **VLT/SPHERE**: NIR scattered-light images of MWC 758, HD 142527, DZ Cha, HD 100453  
  > "VLT/SPHERE images of MWC 758 (cite: Benisty2015), HD 142527 (cite: Avenhaus2017), DZ Cha (cite: Canovas2018), and HD 100453 (cite: Benisty2017)" (Data)
- Other facility **Subaru/HiCIAO**: NIR images of AB Aur, LkHa 330, V1247 Ori  
  > "Subaru/HiCIAO images of AB Aur (cite: Hashimoto2011), LkH$\alpha$ 330 (cite: Uyama2018), and V1247 Ori (cite: Ohta2016)" (Data)
- Other facility **VLT/NACO**: NIR image of SAO 206462  
  > "VLT/NACO image of SAO 206462 (cite: Garufi2013)" (Data)
- External data: Disk masses of the other disks (not Elias 2-27, WaOph 6, AS 205, HT Lup)  
  > "the masses of the protoplanetary disks ($M_{D}$) are from (cite: Dong2018b)" (Data) [from (cite: Dong2018b)]
- External data: SEDs and other parameters for the four DSHARP disks  
  > "spectral energy distributions (SED) and other parameters collected by (cite: DSHARP1)" (Data) [from (cite: DSHARP1)]

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
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- 2DDFT pitch angle method and uncertainty estimate  
  > "This work uses the 2DDFT method discussed in detail by (cite: Yu2018a)." (Measurement of Pitch Angle) [from (cite: Yu2018a)]
- Disk mass procedure for four DSHARP disks  
  > "following the procedure described in (cite: Dong2018b)" (Data) [from (cite: Dong2018b)]
- Axisymmetric subtraction strategy for ALMA images  
  > "similar to the strategy in (cite: DSHARP3)" (Measurement of Pitch Angle) [from (cite: DSHARP3)]

### Not stated but needed to reproduce (our reading)

- Which DSHARP continuum image products (beam, weighting) were used
- Radial boundaries r_in and r_out chosen for each disk
- Number of Fourier modes m and range of p sampled
- Distances used to convert arcsec to AU
- Fitting method for the log relation and Pearson rho
- Gaussian star-removal parameters for HT Lup

## Analysis recipe

1. **Remove axisymmetric component**: Median intensity in 1 AU annuli subtracted from the ALMA image  
  > "we construct the axisymmetric component of the disk by finding the median intensity within annuli of 1 AU width" (Measurement of Pitch Angle)
   - fitting: _not stated_
   - validation: _not stated_
2. **Deproject images**: Deproject using i and PA with IRAF geotran  
  > "deproject the image from the previous step to its face-on orientation, employing the `IRAF` task `geotran`" (Measurement of Pitch Angle)
   - software: IRAF
   - fitting: _not stated_
   - validation: _not stated_
3. **Measure pitch angle by 2DDFT**: Log-polar 2D Fourier decomposition; pitch angle from the dominant peak, arctan(-m/p_max)  
  > "The most prominent peak $p_{\rm max}$ of the power spectrum of spiral Fourier mode $m$ is identified to calculate the pitch angle" (Measurement of Pitch Angle)
   - parameter: Uncertainty from three radial ranges with Delta r = 20% of (r_out - r_in)  
  > "where $\Delta r=(r_{\rm out}-r_{\rm in})*20\%$" (Measurement of Pitch Angle)
   - fitting: _not stated_
   - validation: Compared with DSHARP values  
  > "these values are consistent with those reported in (cite: DSHARP3) and (cite: DSHARP4)" (Measurement of Pitch Angle)
4. **Derive disk masses and Toomre Q**: Convert 880 um flux to mass; estimate mean Q from irradiated Keplerian disk  
  > "The mean $Q$ is derived as $Q=c_s\kappa/\pi G \overline{\Sigma}$" (Data)
   - parameter: flaring angle phi = 0.02  
  > "where $\phi$, set to 0.02 for simplicity, is the flaring angle" (Data)
   - assumption: dust opacity 3 cm2 g-1, gas-to-dust ratio 100  
  > "assuming a dust opacity of $\kappa$ = 3 cm$^2$ g$^{-1}$ and a gas-to-dust mass ratio of 100" (Data)
   - fitting: _not stated_
   - validation: _not stated_
5. **Fit pitch angle vs disk mass**: Logarithmic fit and Pearson correlations  
  > "Fitting a logarithmic function gives" (Results and Discussion)
   - fitting: _not stated_
   - validation: Tested excluding DZ Cha and using flux density instead of mass  
  > "pitch angle correlates nearly equally well with the model-independent submillimeter flux density" (Results and Discussion)

## Software

- **IRAF** : geotran deprojection  
  > "employing the `IRAF` task `geotran`" (Measurement of Pitch Angle)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Slope of |phi|-log(M_D) relation | -7.8 | 1.7 | deg per dex | 5 | /\varphi/ = -(7.8\pm1.7)\log(M_{D}/M_{\odot})+(2.7\pm2.6) |
| Pearson rho, pitch angle vs disk mass | -0.81 | not stated | dimensionless | 5 | (Figure 5e; $\rho=-0.81$) |
| Pitch angle HT Lup | 17.1 | 0.8 | deg | 3 | which yields $\varphi=17.1\ensuremath{^\circ}\pm0.8\ensuremath{^\circ}$ |
| Pitch angle Elias 2-27 | 15.9 | 2.4 | deg | 3 | $\varphi=15.9\ensuremath{^\circ}\pm2.4\ensuremath{^\circ}$ for Elias 2-27 |
| Pitch angle AS 205 | 12.9 | 1.1 | deg | 3 | $\varphi=12.9\ensuremath{^\circ}\pm1.1\ensuremath{^\circ}$ for AS 205 |

## Qualitative findings


## Claim tuples

- H: Spiral pitch angle depends on disk mass | E: 2DDFT pitch angles for 13 disks vs dust-derived disk masses | R: rho = -0.81; |phi| = -(7.8±1.7)log(M_D/Msun)+(2.7±2.6) | F: More massive disks have tighter arms, including those with companions | **supported**
- H: DZ Cha does not drive the trend | E: Exclude DZ Cha or set its pitch to 18 deg | R: rho' = -0.70 and -0.69 for M_D | F: DZ Cha weakens but does not alter the conclusions | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Planet-excited spirals (Zhu2015) judged unlikely to explain the relation since pitch angle does not depend explicitly on disk mass  
  > "Thus, this scenario is unlikely to explain our results." (Discussion)
- How they decided it was enough: _not stated_
- Limitation (authors): Disk masses are the largest uncertainty; gas-to-dust ratio unconstrained  
  > "The largest source of uncertainty in Equation (2) lies in the disk masses." (Results and Discussion)
- Caveat (inferred, ours): Small sample of 13, mixed NIR and ALMA tracers
- Caveat (inferred, ours): Fit using only ALMA subset is shallower
- Caveat (inferred, ours): Dust-based masses depend on assumed opacity and gas-to-dust ratio

## Reproducibility

- Data public (paper): DSHARP ALMA data cited; NIR images some provided by authors  
  > "We are grateful to Henning Avenhaus, Myriam Benisty, Hector Canovas, Antonio Garufi, and Jun Hashimoto for making available the observational images" (Acknowledgements)
- Products in archive: _not stated_
- Missing: Radial ranges per disk
- Missing: Exact image files
- Missing: Fit procedure details
- Data volume (inferred): <10 GB (DSHARP continuum images)
- Score (inferred): 3/5, Method is clear but several parameters and the NIR images are not fully specified.
- Rediscovery candidate: no, Needs NIR images and unstated radial ranges; ALMA part is only five images.

## Links

- Method: (cite: Yu2018a) (2DDFT pitch angle method)
- Method: (cite: Dong2018b) (disk mass procedure)
- Companion: (cite: DSHARP3) (DSHARP spiral analysis)
- Companion: (cite: DSHARP4) (AS 205 and HT Lup spirals)
- Related: DSHARP

## Checks

```json
{
 "quotes": 32,
 "quotes_ok": 32,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 84,
  "stated": 23,
  "rate": 0.274
 },
 "evidence_ok": true
}
```
