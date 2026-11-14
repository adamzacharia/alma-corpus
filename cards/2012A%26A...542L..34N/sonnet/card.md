# ALMA reveals a chemically evolved submillimeter galaxy at z = 4.76

`2012A&A...542L..34N` | Astronomy and Astrophysics 2012 | first author: Nagao, T. | arXiv: 1205.4834 | DOI: 10.1051/0004-6361/201219518

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies
- Question: What is the gas metallicity of the z=4.76 SMG LESS J0332, as inferred from the [N II] 205 um/[C II] 158 um flux ratio, and is an AGN contributing significantly?  
  > "Here we show that the \[N ii\]/\[C ii\] flux ratio is a good metallicity indicator based on photoionization models, and apply this new method to a high-$z$ luminous SMG" (Introduction)
- Target **LESS J033229.4–275619 (LESS J0332)**: coordinates _not stated_; z/distance z = 4.76 (z_[NII] = 4.7555 ± 0.0002)  
  > "We observed LESS J0332 at $z$ = 4.76, with the band 6 receiver" (Observations and results); "$z_{\rm Ly\alpha}$ | 4.762$\pm$0.002 | (cite: 2009MNRAS.395.1905C)" (Table 1); distance from Lyα (Coppin et al. 2009), CO(2-1), [CII] (De Breuck 2011); [NII] this work  
  > "We observed LESS J0332 at $z$ = 4.76, with the band 6 receiver" (Observations and results); "$z_{\rm Ly\alpha}$ | 4.762$\pm$0.002 | (cite: 2009MNRAS.395.1905C)" (Table 1)

## Data provenance

- ALMA projects: 2011.0.00268.S
- bands: Band 6  
  > "with the band 6 receiver on the Atacama Large Millimeter/submillimeter Array (ALMA) in the dual-polarization setup" (Observations and results)
- frequencies and spectral setup: Tuned to 253.96001 GHz (USB, [NII]); LSB covers CO(12-11); 1875 MHz bandwidth, 488.28 kHz x 3840 channels  
  > "The receiver was tuned to 253.96001 GHz to cover the redshifted \[N ii\] 205 $\mu$m emission with the upper sideband" (Observations and results); "bandwidth of 1875 MHz (488.28 kHz $\times$ 3840 channels)" (Observations and results)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: 18 antennas, compact configuration (one antenna flagged in last run)  
  > "The observation was performed with 18 antennas in the compact configuration" (Observations and results)
- baselines: _not stated_
- angular resolution: 1.67" x 1.48" (PA 26.8 deg)  
  > "which gives a final synthesized beam size of $1.67^{\prime\prime} \times 1.48^{\prime\prime}$ (position angle = 26.8 degree)" (Observations and results)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: 3 runs of 1.2 h each; total 3.6 h including overheads  
  > "Each observing run consisted of 1.2 hours and the total observing time is 3.6 hours, including overheads." (Observations and results)
- observing dates: 2011 Oct 1, 2012 Jan 12, 2012 Jan 13  
  > "on 2011 October 1, 2012 January 12, and 2012 January 13" (Observations and results)
- pi or archival as stated: Cycle 0 program, PI T. Nagao  
  > "ADS/JAO.ALMA#2011.0.00268.S (PI: T. Nagao)" (Acknowledgements)
- Line: [N II] 205 um (1461.132 GHz)
- Line: CO J=12-11 (1381.995 GHz)
- External data: [C II] 158 um flux 14.7±2.2 Jy km/s, z, FWHM and spectrum  
  > "$I_{\rm [CII]}$ | 14.7$\pm$2.2 Jy km s$^{-1}$ | De Breuck et al. (2011)" (Table 1) [from De Breuck et al. (2011) (cite: 2011A&A...530L...8D)]
- External data: CO(2-1) flux 0.09±0.02 Jy km/s, redshift and width  
  > "$I_{\rm CO(2-1)}$ | 0.09$\pm$0.02 Jy km s$^{-1}$ | (cite: 2010MNRAS.407L.103C)" (Table 1) [from Coppin et al. 2010 (cite: 2010MNRAS.407L.103C)]
- External data: Lyα redshift 4.762±0.002  
  > "$z_{\rm Ly\alpha}$ | 4.762$\pm$0.002 | (cite: 2009MNRAS.395.1905C)" (Table 1) [from Coppin et al. 2009 (cite: 2009MNRAS.395.1905C)]
- External data: Compton-thick AGN with L2-10keV = 2.5e44 erg/s  
  > "absorption-corrected X-ray luminosity of $L_{\rm 2-10 keV} = 2.5 \times 
10^{44}$ erg s$^{-1}$ (cite: 2011ApJ...730L..28G)" (3.1 Possible AGN contribution) [from Gilli et al. 2011 (cite: 2011ApJ...730L..28G)]
- Simulation/model as data: Cloudy 08.00 photoionization models, Starburst99 1 Myr constant-SF input, log n_HII=1.5,3.0, log U=-3.5,-2.5, Zgas/Zsun=0.05-3.0  
  > "Here we examine gas clouds with $\log n_{\rm HII} =$ 1.5 and 3.0, and $\log U_{\rm HII} =$ –3.5 and –2.5, for $Z_{\rm gas}/Z_\odot =$ 0.05 – 3.0." (3.2 Gas metallicity)

## Processing

### Calibration

- pipeline or manual: CASA, 'standard manner'  
  > "The data were processed with Common Astronomy Software Applications (CASA; (cite: 2007ASPC..376..127M; 2012arXiv1201.3454P)) in a standard manner." (Observations and results)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Callisto (flux); J0522–364 bandpass; J0403–360 phase  
  > "Callisto was also observed as a flux calibrator. The bandpass and phase were calibrated with J0522–364 and J0403–360, respectively." (Observations and results)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "the clean process was applied with the natural weighting" (Observations and results)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: continuum-subtracted channel maps; continuum from USB+LSB excluding line and edge channels  
  > "These measurements were made by combining the upper and lower sideband data and excluding the channels affected by the \[N ii\] 205 $\mu$m emission" (Observations and results)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: 70-channel binning (40.54 km/s)  
  > "A 70-channel (or equivalently, 40.54 km s$^{-1}$) binning was applied to the data cube" (Observations and results)
- final beam: 1.67" x 1.48", PA 26.8 deg  
  > "which gives a final synthesized beam size of $1.67^{\prime\prime} \times 1.48^{\prime\prime}$ (position angle = 26.8 degree)" (Observations and results)
- final rms: _not stated_

### Inherited from earlier work

- Cloudy model calculation details  
  > "The calculation details are given in (cite: 2011A&A...526A.149N)." (3.2 Gas metallicity) [from Nagao et al. 2011 (cite: 2011A&A...526A.149N)]
- Cloud stopping depth A_V=100 mag  
  > "Calculations are stopped at the depth of $A_{\rm V} = 100$ mag to cover the whole \[C ii\] 158 $\mu$m emitting regions, following (cite: 2005ApJS..161...65A)." (3.2 Gas metallicity) [from Abel et al. 2005 (cite: 2005ApJS..161...65A)]

### Not stated but needed to reproduce (our reading)

- Line-free channels and continuum-subtraction method
- Number of iterations/threshold/mask and cell/image size for clean
- Calibration flux-scale uncertainty and CASA version
- Aperture position/shape (4.8 arcsec^2) and how uncertainties of the Gaussian fit were derived
- Exact Cloudy model grid and how flux ratio was mapped to metallicity
- Whether the [CII] spectrum was re-extracted for velocity-component ratios

## Analysis recipe

1. **Calibrate and image the cube**: CASA standard processing, 70-channel binning, natural-weight clean  
  > "A 70-channel (or equivalently, 40.54 km s$^{-1}$) binning was applied to the data cube, and then the clean process was applied with the natural weighting" (Observations and results)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Measure [NII] line and continuum**: Extract spectrum in 4.8 arcsec^2 aperture; fit single Gaussian; measure CO(12-11) 3σ limit and continuum  
  > "The emission line is fitted with a single Gaussian profile." (Observations and results)
   - software: CASA
   - parameter: aperture 4.8 arcsec^2  
  > "adopting an aperture size of 4.8 arcsec$^2$" (Observations and results)
   - assumption: CO(12-11) limit assumes same velocity profile as [NII]  
  > "adopting the same aperture size as adopted for the \[N ii\] 205 $\mu$m line and assuming the same velocity profile" (Observations and results)
   - fitting: single Gaussian; sampler not stated  
  > "The emission line is fitted with a single Gaussian profile." (Observations and results)
   - validation: 2D Gaussian fits show sources unresolved, consistent with beam  
  > "Both results are consistent with the synthesized-beam image shape." (Observations and results)
3. **Test AGN contribution via CO(12-11)/CO(2-1)**: Compare 3σ upper limit ratio of 3.8 with CO SLEDs of APM 08279+5255 and SF-dominated galaxies  
  > "we obtain a 3$\sigma$ upper limit on the flux ratio of CO(12-11)/CO(2-1) of 3.8." (3.1 Possible AGN contribution)
   - fitting: _not stated_
   - validation: _not stated_
4. **Derive gas metallicity from [NII]/[CII]**: Compare observed ratio with Cloudy photoionization models  
  > "The observed \[N ii\]/\[C ii\] flux ratio ($\sim 0.043$) infers $\log (Z_{\rm gas}/Z_\odot) \sim 0.0 \pm 0.3$" (3.2 Gas metallicity)
   - software: Cloudy, Starburst99
   - parameter: pressure-equilibrium cloud; N scales as Z^2 above 0.23 Zsun; Orion grains  
  > "nitrogen, which scales as $Z_{\rm gas}^2$ at $Z_{\rm gas} > 0.23 Z_\odot$ (cite: 2002ApJS..142...35K)" (3.2 Gas metallicity)
   - assumption: No AGN in models  
  > "We did not take AGN effects into account in the models since the expected AGN contribution is small" (3.2 Gas metallicity)
   - fitting: _not stated_
   - validation: _not stated_
5. **Ratios in velocity components**: Measure [NII]/[CII] in red and blue velocity ranges  
  > "resulting in a flux ratio of 0.086 and 0.020, respectively" (3.2 Gas metallicity)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : data processing and imaging  
  > "The data were processed with Common Astronomy Software Applications (CASA" (Observations and results)
- **Cloudy** 08.00: photoionization models of [NII]/[CII]  
  > "we carried out model calculations using Cloudy (cite: 1998PASP..110..761F) version 08.00" (3.2 Gas metallicity)
- **Starburst99** : input ionizing continua  
  > "The input continua are the starburst99 constant star-formation model spectra" (3.2 Gas metallicity)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| [NII] 205um peak frequency | 253.868 | 0.007 | GHz | 2 | peak frequency of 253.868$\pm$0.007 GHz |
| [NII] peak intensity | 2.58 | 0.21 | mJy | 2 | peak intensity of 2.58 $\pm$ 0.21 mJy |
| [NII] FWHM | 230 | 22 | km/s | 2 | FWHM of 230 $\pm$ 22 km s$^{-1}$ |
| [NII] velocity-integrated flux | 630 | 78 | mJy km/s | 2 | velocity-integrated flux of 630 $\pm$ 78 mJy km s$^{-1}$ |
| z_[NII] | 4.7555 | 0.0002 | dimensionless | 2 | $z_{\rm [NII]} = 4.7555 \pm 0.0002$ |
| CO(12-11) 3σ upper limit | <344 | not stated | mJy km/s | 2 | The inferred 3$\sigma$ upper limit on the velocity-integrated flux is 344 mJy km s$^{-1}$ |
| 1.2 mm continuum flux | 3.5 | 0.1 | mJy | 2 | Its flux is $3.5 \pm 0.1$ mJy |
| CO(12-11)/CO(2-1) upper limit | 3.8 | 3σ limit | dimensionless | 3 | flux ratio of CO(12-11)/CO(2-1) of 3.8 |
| [NII]/[CII] flux ratio | 0.043 | 0.008 | dimensionless | 4 | is inferred to be $0.043 \pm 0.008$ |
| log(Zgas/Zsun) | ~0.0 | 0.3 | dex | 4 | infers $\log (Z_{\rm gas}/Z_\odot) \sim 0.0 \pm 0.3$ |
| [NII]/[CII] in red and blue parts | 0.086 (red), 0.020 (blue) | not stated | dimensionless | 5 | resulting in a flux ratio of 0.086 and 0.020, respectively |

## Qualitative findings

- First measurement of [NII]/[CII] ratio at high z; the system hosts a metal-rich component and appears chemically inhomogeneous, possibly a merger  
  > "this system does also host a significant metal-rich component (with solar–supersolar metallicity)" (3.2 Gas metallicity)

## Claim tuples

- H: Is the AGN contribution to heating/excitation in LESS J0332 significant? | E: CO(12-11) ALMA limit combined with CO(2-1) | R: CO(12-11)/CO(2-1) < 3.8 (3σ) | F: AGN/XDR contribution not significant | **supported**
- H: What is the gas metallicity of LESS J0332? | E: [NII]/[CII] ratio compared with Cloudy models | R: ratio 0.043 gives log Z/Zsun ~ 0.0±0.3 | F: Consistent with solar metallicity; chemically evolved at z=4.76 | **supported**
- H: Is the system chemically homogeneous? | E: [NII]/[CII] in red vs blue velocity ranges | R: 0.086 vs 0.020 | F: Possibly an unmixed merger of metal-rich and metal-poor components | **partially**

## Reasoning

- Why this data: Starburst-dominated SMG with intense [CII] makes a good [NII] target  
  > "this object is starburst-dominated and shows intense \[C ii\] 158 $\mu$m emission" (Introduction)
- Why this method: _not stated_
- Alternative: Inferring [NII] 205 from [NII] 122 rejected as risking large systematic errors due to density dependence  
  > "this method may introduce a large systematic error" (3.2 Gas metallicity)
- How they decided it was enough: _not stated_
- Limitation (authors): Metallicity constraint is loose due to degeneracy with density and ionization parameter  
  > "the constraint on the gas metallicity is currently fairly loose" (3.2 Gas metallicity)
- Limitation (authors): Velocity offset between [NII] and [CII] may reflect modest S/N  
  > "This velocity offset may be a consequence of the modest signal-to-noise ratio in the two spectra" (Observations and results)
- Caveat (inferred, ours): Metallicity relies on a handful of Cloudy models with degenerate density/U
- Caveat (inferred, ours): [CII] data are from a different instrument with low S/N and different beam/aperture, so component ratios are uncertain
- Caveat (inferred, ours): Red/blue component ratios given without uncertainties

## Reproducibility

- Data public (paper): Cycle 0 data cited by project code  
  > "This paper makes use of the following cycle 0 ALMA data: ADS/JAO.ALMA#2011.0.00268.S (PI: T. Nagao)." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Imaging parameters (cell, size, threshold, mask)
- Missing: Aperture definition
- Missing: Detailed Cloudy input grid
- Missing: [CII] spectrum data from De Breuck 2011
- Data volume (inferred): ~10-30 GB raw (3 cycle 0 execution blocks)
- Score (inferred): 3/5, Public data and simple measurements, but sparse processing and model details.
- Rediscovery candidate: no, Imaging details and model grid are insufficiently specified; the metallicity inference needs external [CII] data and an unspecified Cloudy grid.

## Links

- Method: Nagao et al. 2011 (cite: 2011A&A...526A.149N) (Far-IR line metallicity diagnostics and Cloudy calculation details)
- Companion: De Breuck et al. 2011 (cite: 2011A&A...530L...8D) (Previous [CII] detection of LESS J0332)

## Checks

```json
{
 "quotes": 64,
 "quotes_ok": 64,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 11,
 "numeric_problems": 0,
 "fill": {
  "facts": 76,
  "stated": 43,
  "rate": 0.566
 },
 "evidence_ok": true
}
```
