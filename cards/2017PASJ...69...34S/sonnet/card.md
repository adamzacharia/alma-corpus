# Detailed modeling of dust distribution in the disk of HD 142527

`2017PASJ...69...34S` | Publications of the Astronomical Society of Japan 2017 | first author: Soon, Kang-Lou | arXiv: 1701.06706 | DOI: 10.1093/pasj/psx007

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: protoplanetary_disks
- Question: What is the dust surface density distribution along all position angles of the crescent disk around HD 142527, and how does it depend on the assumed scattering opacity?  
  > "The map is divided into 18 azimuthal sectors, and the radial intensity profile in each sector is reproduced with a 2D disk model." (abstract)
- Target **HD 142527**: coordinates _not stated_; z/distance 140 pc  
  > "Considering its association with Sco OB2, the distance to the star is assumed to be 140 pc." (1 Introduction); distance from assumed from association with Sco OB2  
  > "Considering its association with Sco OB2, the distance to the star is assumed to be 140 pc." (1 Introduction)

## Data provenance

- ALMA projects: 2011.0.00318.S
- bands: 890 µm continuum (336 GHz), Cycle 0  
  > "we obtain a 1.8 GHz bandwidth for the continuum data at 336 GHz, or λ obs = 890 µm." (2 Observational data)
- frequencies and spectral setup: Four spectral windows at 330.588, 329.331, 342.883, 342.400 GHz; 469 MHz bandwidth, 3840 channels each  
  > "The central frequencies for the windows are 330.588, 329.331, 342.883, and 342.400 GHz;" (2 Observational data); "each window has a 469 MHz bandwidth over 3840 channels." (2 Observational data)
- continuum bandwidth: 1.8 GHz from line-free channels  
  > "Aggregating all the line-free channels in the spectral windows, we obtain a 1.8 GHz bandwidth for the continuum data at 336 GHz" (2 Observational data)
- arrays: 12-m array, 20 to 26 antennas, six scheduling blocks  
  > "Six scheduling blocks were carried out by using the Extended Array Configuration in Cycle 0 consisting of 20 to 26 12-meter antennas" (2 Observational data)
- configurations: _not stated_
- baselines: maximum about 480 m  
  > "forming a maximum baseline of about 480 m." (2 Observational data)
- angular resolution: 0.40'' × 0.47'' (PA 59.9°), 56 au × 66 au  
  > "The synthesized beam (FWHM) is 0 ′′ . 40 × 0 ′′ . 47 (PA = 59 ◦ .9), or 56 au × 66 au" (2 Observational data)
- max recoverable scale: _not stated_
- sensitivity: RMS 0.61 mJy asec^-2  
  > "The RMS noise level is 0.61 mJy asec −2 ." (2 Observational data)
- time on source: three hours  
  > "The on-source integration time is three hours after flagging aberrant data." (2 Observational data)
- observing dates: 2012 June to August  
  > "over the period from 2012 June to August" (2 Observational data)
- pi or archival as stated: _not stated_
- External data: Dust opacities (kappa_a=2.9, kappa_s=26.2 cm2/g at 890 µm)  
  > "κ a = 2.9 cm 2 g −1 and κ s = 26.2 cm 2 g −1 at λ obs = 890 µm (Aikawa & Nomura 2006)." (3.1 Assumptions on dust properties) [from Aikawa & Nomura 2006]
- External data: Disk inclination 27 deg from 13CO kinematics  
  > "the inclination of the disk axis to the line of sight is derived to be 27 ◦ (Fukagawa et al. 2013)." (1 Introduction) [from Fukagawa et al. 2013]
- External data: Grain composition mass fractions consistent with solar abundance  
  > "which are consistent with the solar elemental abundance (Anders & Grevesse 1989)" (3.1 Assumptions on dust properties) [from Anders & Grevesse 1989]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: CASA 3.4  
  > "Calibration and data reduction are made with the Common Astronomy Software Applications package version 3.4." (2 Observational data)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: Self-calibration performed, Briggs robust 0.5  
  > "We use Briggs weighting with a robust parameter of 0.5 during the self-calibration" (2 Observational data)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 0.5  
  > "We use Briggs weighting with a robust parameter of 0.5 during the self-calibration" (2 Observational data)
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
- final beam: 0.40'' × 0.47'', PA 59.9°  
  > "The synthesized beam (FWHM) is 0 ′′ . 40 × 0 ′′ . 47 (PA = 59 ◦ .9)" (2 Observational data)
- final rms: 0.61 mJy asec^-2  
  > "The RMS noise level is 0.61 mJy asec −2 ." (2 Observational data)

### Inherited from earlier work

- Modeling method (2D axisymmetric, radiative and hydrostatic equilibrium)  
  > "We use the same modeling method adopted by Muto et al. (2015)." (1 Introduction) [from Muto et al. (2015)]
- Robust 0.5 weighting to recover extended emission  
  > "in order to recover the weak and extended components of the dust emission (Muto et al. 2015)" (2 Observational data) [from Muto et al. (2015)]
- Gas-to-dust ratio 100, well-mixed  
  > "Following Muto et al. (2015), we assume that the gas and dust are well mixed in the vertical direction and use the constant gas-to-dust ratio of 100" (Appendix 1) [from Muto et al. (2015)]

### Not stated but needed to reproduce (our reading)

- Phase center, imaging task, cell and image size, and CLEAN settings
- Self-calibration solution intervals and reference datasets
- Flux calibrator and flux scale
- Line-free channel selection
- Radiative transfer M1 code is not released
- Exact PA offset conventions and sector extraction procedure
- Stellar and disk model parameters beyond those listed (e.g. inner boundary, luminosity)

## Analysis recipe

1. **Extract observed radial profiles**: Divide image into 18 azimuthal sectors (20 deg), radial bins of 14 au, fit Gaussian to each profile for I0, w0, r0  
  > "we create radial intensity profiles of the continuum emission for 18 azimuthal sectors with a radial bin width of 14 au." (2 Observational data)
   - parameter: PA' = PA + 19 deg  
  > "PA ′ = PA + 19 ◦" (2 Observational data)
   - assumption: distance 140 pc  
  > "the distance to the star is assumed to be 140 pc." (1 Introduction)
   - fitting: Gaussian fit to radial profile  
  > "We fit these discrete averaged intensities in every sector by using a Gaussian function" (2 Observational data)
   - validation: _not stated_
2. **Compute disk structure grid**: M1 radiative transfer with hydrostatic equilibrium over a grid of (Sigma0, w0, r0) with Gaussian surface density  
  > "we solve the radiative transfer of the disk by the M1 model" (3.2 Disk models)
   - parameter: -2.1<=logSigma0<=0.1 step 0.1; 21<=w0<=31 au step 2; 159<=r0<=199 au step 8  
  > "−2.1 ≤ logΣ 0 (g cm −2 ) ≤ 0.1 with the interval ∆logΣ 0 = 0.1, in 21 au ≤ w 0 ≤ 31 au with ∆w 0 = 2 au" (3 Modeling procedure)
   - assumption: Grains: silicate, carbonaceous, ice; a^-3.5 size distribution, amax = 1 mm; Mie theory; gas-to-dust 100; M*=2.2 Msun, Teff=6250 K; i=27 deg  
  > "The grains have a power-law size distribution," (3.1 Assumptions on dust properties)
   - fitting: _not stated_
   - validation: _not stated_
3. **Ray-trace and compare with observation**: Ray-trace model images, convolve with the synthesized beam, fit Gaussians, and search for models meeting tolerance criteria; interpolate in Sigma0 and r0  
  > "|∆w 0 [∗] [| ≡] ��� w 0∗,obs [−] [w] 0 [∗] ��� ≤ 1 au, (11b)" (3.4 Comparison between observation and simulation)
   - parameter: |ΔI|<=1% of I_obs, |Δw|<=1 au, |Δr|<=1 au  
  > "criteria better than the beam resolution are set." (3.4 Comparison between observation and simulation)
   - fitting: Grid search with interpolation in Sigma0 and r0  
  > "we interpolate models to complement our sample on Σ 0 and r 0 ." (3.4 Comparison between observation and simulation)
   - validation: Compared uncertainties for optically thin and thick sectors using alternative parameter sets  
  > "The uncertainties in the optically thin and optically thick sectors are discussed separately" (4.3 Uncertainties in the best fit values)
4. **Test reduced scattering opacity**: Repeat fits with scattering opacity reduced by 90% (kappa_s=2.62 cm2/g) in all sectors  
  > "we reduce the scattering opacity across all the wavelengths by 90%, as depicted in figure 2." (5.1 Reducing scattering opacities)
   - assumption: Absorption opacity unchanged  
  > "The absorption opacity of the dust particles is kept the same." (5.1 Reducing scattering opacities)
   - fitting: same as step 3  
  > "Fit the radial profiles of the model intensity with the Gaussian function and obtain their (I 0 [∗] [,w] 0 [∗] [,r] 0 [∗] [)]" (3 Modeling procedure)
   - validation: Compared with conventional model; checked validity of 2D axisymmetric approximation via photon escape length (~10 au vs 56 au arc length)  
  > "this length is approximately 10 au, much shorter than the arc length subtended by the 20 ◦ -sector" (5.2 Intensity Dependence on Scattering Opacity and PA')

## Software

- **CASA** 3.4: calibration, data reduction, self-calibration  
  > "Calibration and data reduction are made with the Common Astronomy Software Applications package version 3.4." (2 Observational data)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Sigma0 in brightest sector PA'=30-50 deg (conventional) | 1.12 | factor ~2 | g cm^-2 | 3 | We derived Σ 0 = 1.12 g cm −2 for the brightest PA ′ = 30 ◦ − 50 ◦ |
| Sigma0 in faintest sector PA'=230-250 deg (conventional) | 8.31e-3 | not stated | g cm^-2 | 3 | Σ 0 = 8.31 × 10 −3 g cm −2 for the faintest PA ′ = 230 ◦ − 250 ◦ |
| Sigma0 contrast, conventional | ~130 | not stated | dimensionless | 3 | The contrast in Σ 0 between these two sectors is about a factor of 130 |
| Sigma0 contrast, reduced-scattering | ~40 | not stated | dimensionless | 4 | is reduced to about a factor of 40 |
| Sector mass uncertainty, optically thin sector | ~5% | not stated | percent | 3 | M sec is uncertain only by approximately ±5%. |

## Qualitative findings

- The conventional model cannot reproduce the NW sectors (PA'=310-10 deg) because heavy self-scattering lowers the intensity ceiling.  
  > "This is because the model intensity gets insensitive to the increase in surface density due to heavy self-scattering" (abstract)

## Claim tuples

- H: Conventional dust opacity (amax=1 mm) can reproduce the radial profiles in all azimuthal sectors | E: Grid-search fit of 2D model in 18 sectors | R: Fails in PA'=310-10 deg; model is 16% too low in PA'=330-350 | F: Conventional opacity cannot explain the NW region | **supported**
- H: Reduced scattering opacity reproduces all sectors | E: Repeat fits with kappa_s reduced by 90% | R: All sectors reproduced; Sigma0 contrast ~40 | F: Albedo is probably lower than assumed in the NW region | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Extend Muto et al. (2015) to all PA to reveal the whole dust distribution  
  > "we extend the modeling of dust continuum emission in all the PA directions." (1 Introduction)
- How they decided it was enough: _not stated_
- Limitation (authors): Resolution is insufficient to strictly constrain best fit values; optically thick Sigma0 uncertain by ~2  
  > "The best fit values cannot be strictly constrained because of the insufficient angular resolution" (4.3 Uncertainties in the best fit values)
- Limitation (authors): Shadowing by warped inner disk not considered; temperature may be overestimated in north and south  
  > "as we did not consider the possible shadowing effects caused by the warped inner disk" (4.1 Derived best fit values)
- Caveat (inferred, ours): Reducing scattering opacity by 10x is ad hoc and no lower limit is set
- Caveat (inferred, ours): Only a single dust composition and amax tested
- Caveat (inferred, ours): Fit uses three Gaussian parameters per sector rather than visibility-space fitting
- Caveat (inferred, ours): Tolerance of 1% is tighter than the data uncertainties

## Reproducibility

- Data public (paper): Cycle 0 ALMA project code given  
  > "(ADS/JAO.ALMA#2011.0.00318.S)" (2 Observational data)
- Products in archive: _not stated_
- Missing: Radiative transfer code (M1) not released
- Missing: Imaging and self-calibration parameters
- Missing: Opacity tables provided privately by H. Nomura
- Data volume (inferred): ~10-50 GB
- Score (inferred): 3/5, Data public and equations detailed, but custom RT code, opacities and imaging details missing.
- Rediscovery candidate: no, Requires unreleased radiative transfer code and privately supplied opacities.

## Links

- Method: Muto et al. (2015) (Same modeling method)
- Method: Gonzalez et al. 2007; Kanno et al. 2013 (M1 radiative transfer approach)
- Companion: Muto et al. 2015 (Modeling of two PA sectors in the same disk)

## Checks

```json
{
 "quotes": 54,
 "quotes_ok": 54,
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
  "facts": 71,
  "stated": 44,
  "rate": 0.62
 },
 "evidence_ok": true
}
```
