# The Synthetic ALMA Multiband Analysis of the Dust Properties of the TW Hya Protoplanetary Disk

`2019ApJ...872..179K` | The Astrophysical Journal 2019 | first author: Kim, Seongjoong | arXiv: 1902.00168 | DOI: 10.3847/1538-4357/ab0304

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: protoplanetary_disks
- Question: Which ALMA band set best constrains dust temperature, optical depth and beta in the TW Hya disk, and do archival data agree with the synthetic predictions?  
  > "We perform the synthetic ALMA multiband analysis to find the best ALMA band set for constraining the dust properties of the TW Hya protoplanetary disk." (abstract)
- Target **TW Hya**: coordinates _not stated_; z/distance d ~ 59 pc  
  > "Its proximity, $d\sim59\pm1~pc$ (cite: GAIA2016), provides good chance to see the detailed structure of the disk" (INTRODUCTION); distance from Gaia (cite: GAIA2016)  
  > "Its proximity, $d\sim59\pm1~pc$ (cite: GAIA2016), provides good chance to see the detailed structure of the disk" (INTRODUCTION)

## Data provenance

- ALMA projects: 2012.1.00422.S, 2015.1.00005.S, 2015.1.00686.S
- bands: Bands 4, 6, 7, 9 archival continuum  
  > "ALMA archival dust continuum data of the TW Hya protoplanetary disk at Band 4, 6, 7, and 9" (4 Applications)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: Band 4 ~88.1x62.1 mas; Band 6 ~75.4x55.2 mas; Band 7 ~24x18 mas; Band 9 ~434x247 mas  
  > "| 9    | 661           | $\sim$434$\times$247   | $\sim$-85.8    | $\sim$ 10       |" (Table 2)
- max recoverable scale: _not stated_
- sensitivity: 1 sigma: Band 4 0.0124, Band 6 0.0287, Band 7 0.0350, Band 9 ~10 mJy/beam  
  > "| 4    | 145           | $\sim$88.1$\times$62.1 | $\sim$57.8     | $\sim$ 0.0124   |" (Table 2)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- External data: Band 4 and 6 continuum images and 190 GHz MFS intensity/spectral index profiles  
  > "We use Band 4 and 6 data in (cite: Tsukagoshi2016) and Band 7 fits image at Sean Andrews’s science homepage" (4 Applications) [from (cite: Tsukagoshi2016)]
- External data: Band 7 FITS image  
  > "Band 7 fits image at Sean Andrews’s science homepage" (4 Applications) [from (cite: Andrews2016)]
- External data: Band 9 observation of TW Hya  
  > "we also find Band 9 observation of the TW Hya disk (cite: Schwarz2016) which is low spatial resolution data" (4 Applications) [from (cite: Schwarz2016)]
- External data: Midplane dust temperature profile Td=26K(r/10AU)^-0.4 fitted from radiative transfer models  
  > "The $T_{d,model}(r)$ profile is obtained by fitting the temperature profile at the disk midplane in (cite: Andrews2012; Andrews2016)" (2.1) [from (cite: Andrews2012; Andrews2016)]
- External data: Amplitude calibration accuracy 10/15/20% by band  
  > "the accuracy of amplitude calibration for ALMA data $x=10\%$ for Band 3, 4, 5 and 6, $x=15\%$ for Band 7 and 8, $x=20\%$ for Band 9 and 10 (cite: ALMATech2018)" (2.2) [from (cite: ALMATech2018)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: Published images from Tsukagoshi2016, Andrews homepage, and JVO archive Band 9 data used  
  > "We retrieved this data from JVO portal[^2] operated by the NAOJ." (4 Applications)
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
- smoothing: Beams matched with imsmooth in CASA: ~88.1x62.1 mas for [7,6,4]; ~434x247 mas for [9,6,4]  
  > "we match the beam size of the continuum images in each set using $imsmooth$ command in CASA." (4 Applications)
- final beam: 88.1x62.1 mas and 434x247 mas  
  > "We match the beam size of $\sim88.1\times62.1$ mas for Band \[7,6,4\] set and $\sim434\times247$ mas for Band \[9,6,4\] set." (4 Applications)
- final rms: _not stated_

### Inherited from earlier work

- Band 4/6 images, 190 GHz MFS profile and beta/tau model derivation  
  > "We use Band 4 and 6 data in (cite: Tsukagoshi2016)" (4 Applications) [from (cite: Tsukagoshi2016)]

### Not stated but needed to reproduce (our reading)

- Disk inclination and position angle used for deprojection
- Radial bin width and annulus averaging details
- Grid of radii and parameter grid resolution for sensitivity analysis
- Grid for tau and beta ranges
- Reference frequency nu0 and tau0 definition
- Exact archive files or project-to-band mapping
- Treatment of beam convolution of Td model (mean beam)

## Analysis recipe

1. **Build model intensity profiles**: Solve I=B(Td)[1-exp(-tau)] with tau=tau0(nu/nu0)^beta; derive tau0(r), beta(r) from observed 190 GHz intensity and alpha with assumed Td  
  > "we derive the frequency independent radial profiles $\tau_{0,model}(r)$ and $\beta_{model}(r)$ using Equation (1)$-$(3) and the observed radial intensity profiles" (2.1)
   - assumption: Td=26K(r/10AU)^-0.4, d=59 pc, constant Td and absorption along line of sight  
  > "together with the assumption of $T_{d, model}(r)=26K(r/10AU)^{-0.4}$" (2.1)
   - fitting: _not stated_
   - validation: _not stated_
2. **Sensitivity analysis over band sets**: For each of 56 three-band sets, range of Td (5-60 K), tau, beta whose synthetic intensities lie within calibration error x of model at all three bands  
  > "we extract the sets of $[T_{d,syn},\tau_{\nu,syn},\beta_{syn}]$ which satisfy $(100\%-x)I_{\nu_3, model}\leq I_{\nu_3, syn}\leq(100\%+x)I_{\nu_3, model}$" (2.2)
   - parameter: x=10% B3-6, 15% B7-8, 20% B9-10; Td 5-60 K  
  > "with the synthetic dust temperature $T_{d,syn}=5-60~K$" (2.2)
   - fitting: _not stated_
   - validation: Ranking by mean normalized deviation of Td,syn,max from model over 20-45 AU  
  > "we calculate the average normalized deviation of $T_{d,syn,max}$ from $T_{d,model}$ for quantitative comparison" (3.1)
3. **Monte Carlo degeneracy and general-condition test for Band [10,6,3]**: 1000 random intensity combinations with errors within +-10% (B6,B3) and +-20% (B10); derive properties; +-1sigma ranges for grid of Td, tau190, beta  
  > "we generate 1000 combinations of the synthetic intensity with the random errors within $\pm10\%$ for Band 6 and 3 and $\pm20\%$ for Band 10." (3.3.1)
   - fitting: _not stated_
   - validation: _not stated_
4. **Apply to archival TW Hya data**: Smooth images to common beam, azimuthally averaged deprojected profiles, derive Td, tau_B4, beta for [7,6,4] and [9,6,4] sets, with constraint ranges from observational errors  
  > "After matching the beam size, we extract the azimuthally-averaged de-projected radial intensity profiles." (4 Applications)
   - software: CASA
   - fitting: _not stated_
   - validation: Compared with model profile convolved to mean circular beam (~75 mas or ~340 mas)  
  > "The $T_{d,model}(r)$ profile is derived from the profile $T_{d}(r)=26K~(r/10~AU)^{-0.4}$ by convolution to $\sim75$ mas circular beam" (4.1)

## Software

- **CASA** : imsmooth to match beam sizes  
  > "using $imsmooth$ command in CASA" (4 Applications)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Td,syn,max deviation for Band [10,6,3] | ~21 | not stated | % | 2 | Band \[10,6,3\] set gives us $T_{d,syn,max}$ deviates $\sim21\%$ from $T_{d,model}$ in average within $20~AU<r<45~AU$. |
| Td,syn,max deviation for Band [10,6,1] | ~10 | not stated | % | 2 | The deviation of $T_{d,syn,max}$ for Band \[10,6,1\] set is $\sim$10% |
| Monte Carlo points with solutions | 827 of 1000 | not stated | points | 3 | The 827 points are plotted from 1000 combinations of the randomly generated synthetic intensities |
| Td from Band [9,6,4] set | 15-27 for r<=40 AU | not stated | K | 4 | having $T_{d}(r)\approx15-27~K$ in $r\leq40~AU$ region |

## Qualitative findings

- Good band sets include Band 9 or 10 and have large frequency separations; need both optically thick and thin bands, large beta, low Td  
  > "(1) Band 9 or 10 is included in the band set and (2) Enough frequency intervals between the bands." (abstract)

## Claim tuples

- H: Which three-band ALMA set best constrains dust properties of TW Hya | E: Synthetic sensitivity analysis of 56 band combinations | R: Band [10,6,3] best, ~21% Td deviation | F: Need Band 9/10 and wide frequency spacing | **supported**
- H: Synthetic predictions agree with real data | E: Apply analysis to archival Bands 4,6,7,9 | R: [9,6,4] close to model; [7,6,4] deviates with broad ranges | F: Synthetic analysis consistent with real data | **supported**
- H: Band 1 would improve constraints | E: Synthetic analysis with Band 1 | R: [10,6,1] ~10% vs ~21% | F: Band 1 improves constraints | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Homogeneous vertical structure and frequency-independent beta assumed  
  > "First, we assume the vertical structure of the disk is homogeneous in the calculation" (6 Summary)
- Limitation (authors): Band 9 beam is large and smooths out small-scale structure  
  > "the large beam size of Band 9 smoothes out the small-scale structures" (6 Summary)
- Caveat (inferred, ours): Model is built from same data used for test, so validation is partly circular
- Caveat (inferred, ours): Only 10-20% calibration errors considered; no systematic opacity or scattering effects
- Caveat (inferred, ours): Real-data results lack formal fitting or uncertainty estimation

## Reproducibility

- Data public (paper): Archival ALMA data retrieved from JVO; Band 7 image on a public homepage  
  > "We retrieved this data from JVO portal[^2] operated by the NAOJ." (4 Applications)
- Products in archive: _not stated_
- Missing: Inclination/PA for deprojection
- Missing: Radial grid details
- Missing: Exact data files used
- Data volume (inferred): small (~ <10 GB; mostly published images)
- Score (inferred): 3/5, Analytic synthetic method is clearly specified, but real-data processing details are sparse.
- Rediscovery candidate: yes, Public data, simple analytic recipe, numeric outputs like deviation percentages.

## Links

- Companion: (cite: Tsukagoshi2016) (Source of Band 4/6 images and beta/tau profiles)

## Checks

```json
{
 "quotes": 39,
 "quotes_ok": 39,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 3,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [
  "2015.1.00005.S"
 ],
 "obscore_codes_not_in_card": [
  "2015.A.00005.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 4,
 "numeric_problems": 0,
 "fill": {
  "facts": 67,
  "stated": 28,
  "rate": 0.418
 },
 "evidence_ok": true
}
```
