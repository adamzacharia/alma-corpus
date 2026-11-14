# ALMA Observations of the Molecular Clouds in NGC 625

`2020ApJ...895...21I` | The Astrophysical Journal 2020 | first author: Imara, Nia | arXiv: 2002.09498 | DOI: 10.3847/1538-4357/ab8883

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, star_formation
- Question: What are the global and cloud-scale properties of the molecular gas in the dwarf starburst NGC 625, and how do the clouds relate to HII regions and star formation?  
  > "Our main goals in this study are to present the new data, to describe the global properties of the molecular gas as inferred from the CO observations, and to identify and characterize the properties of molecular clouds in NGC 625." (Introduction)
- Target **NGC 625**: coordinates phase center 01h35m06.90s, -41d26m13.47s (J2000)  
  > "a relatively isolated, gas-rich galaxy in the Sculptor Group, at a distance of $3.89\pm 0.22$ Mpc (cite: Cannon_2003)" (Introduction); "The overlapping beams had a phase center of $01^{\rm h}35^{\rm m}06.90s, -41\ensuremath{^\circ} 26\ensuremath{'}13.47\ensuremath{''}$ \[J2000\]" (2.1 New ALMA CO observations); z/distance 3.89±0.22 Mpc  
  > "a relatively isolated, gas-rich galaxy in the Sculptor Group, at a distance of $3.89\pm 0.22$ Mpc (cite: Cannon_2003)" (Introduction); "The overlapping beams had a phase center of $01^{\rm h}35^{\rm m}06.90s, -41\ensuremath{^\circ} 26\ensuremath{'}13.47\ensuremath{''}$ \[J2000\]" (2.1 New ALMA CO observations); distance from Cannon et al. 2003  
  > "a relatively isolated, gas-rich galaxy in the Sculptor Group, at a distance of $3.89\pm 0.22$ Mpc (cite: Cannon_2003)" (Introduction); "The overlapping beams had a phase center of $01^{\rm h}35^{\rm m}06.90s, -41\ensuremath{^\circ} 26\ensuremath{'}13.47\ensuremath{''}$ \[J2000\]" (2.1 New ALMA CO observations)

## Data provenance

- ALMA projects: 2015.1.01395.S
- bands: Band 3  
  > "The ALMA Band 3 correlator was set up to have a velocity resolution of 564.453 kHz (1.470 km s$^{-1}$)" (2.1 New ALMA CO observations)
- frequencies and spectral setup: CO(1-0) baseband 937.50 MHz centered at 114.936 GHz; continuum basebands at 102, 101, 113 GHz  
  > "a bandwidth of 937.50 MHz, centered at 114.936 GHz to cover the $^{12}$CO(1-0) line" (2.1 New ALMA CO observations); "centering the remaining basebands at 102 GHz, 101 GHz, and 113 GHz, each with bandwidths of 1.875 GHz" (2.1 New ALMA CO observations)
- continuum bandwidth: _not stated_
- arrays: 12-m array, 36 antennas, two pointings  
  > "with 36 antennas every night" (2.1 New ALMA CO observations)
- configurations: C36-3  
  > "The ALMA 12-m array was in configuration C36-3 for the five observing nights" (2.1 New ALMA CO observations)
- baselines: 15 m to 639 m  
  > "arranged with baselines from 15 m to 639 m" (2.1 New ALMA CO observations)
- angular resolution: ~1.1'' minimum; final beam 1.31''x1.08''  
  > "The synthesized beam was measured to be $1.31\ensuremath{''}\times 1.08\ensuremath{''}$" (2.1 New ALMA CO observations)
- max recoverable scale: ~10.7'' at 115.27 GHz  
  > "a maximum recoverable scale of $\sim 10.7\ensuremath{''}$ (at 115.27 GHz)" (2.1 New ALMA CO observations)
- sensitivity: 10.3 mJy per 1.5 km/s channel (0.7 K)  
  > "The rms sensitivity is $10.3$ mJy per $1.5~\mbox{km~s$^{-1}$}$ channel." (2.1 New ALMA CO observations)
- time on source: ~48 min per night, five nights  
  > "On-source time | 48.12 min | 48.15 min | 48.12 min | 48.13 min | 48.13" (Table 2)
- observing dates: 2016 May 3, 7, 8  
  > "Date | 2016 May 3 | 2016 May 7 | 2016 May 7 | 2016 May 8 | 2016 May 8" (Table 2)
- pi or archival as stated: PI Nia Imara, Cycle 3  
  > "(project code 2015.1.01395.S; PI: Nia Imara)" (2.1 New ALMA CO observations)
- Line: 12CO J=1-0 (115.2712 GHz)
- Other facility **HST WFPC2 (Hubble Legacy Archive)**: Halpha, Hbeta, F555W, F814W images for SFR map  
  > "We retrieved images from the *Hubble* Legacy Archive in four passbands" (2.2 Archival Hubble Halpha observations)
- Other facility **Spitzer MIPS 24 micron**: mid-IR check of embedded star formation  
  > "Based on the peak of MIPS 24 $\mu$m emission in those two brightest H regions" (2.2 Archival Hubble Halpha observations)
- Other facility **Mopra 22m**: single-dish CO comparison (Cormier et al.)  
  > "(cite: Cormier_2014) reported single-dish CO(1-0) observations obtained with the ATNF Mopra 22-m telescope" (3.1 Integrated intensity)
- External data: HII region sizes and Halpha SFR comparison/stellar populations  
  > "assuming the sizes of these regions as determined by (cite: Cannon_2003)" (6.2 Small scales) [from (cite: Cannon_2003)]
- External data: Single-dish CO mass 5.0e6 Msun  
  > "a molecular gas mass of $(5.0\pm0.7)\times10^6$ $M_\odot$, assuming a Galactic conversion factor" (3.1 Integrated intensity) [from (cite: Cormier_2014)]
- External data: Galactic extinction E(B-V)=0.16 mag  
  > "following the reddening $E(B-V)=0.16$ mag reported by (cite: Schlegel_1998)" (2.2 Archival Hubble Halpha observations) [from (cite: Schlegel_1998)]

## Processing

### Calibration

- pipeline or manual: manual calibration by the North American ALMA Science team  
  > "The North American ALMA Science team used CASA version 4.5.3 to manually calibrate the data." (2.1 New ALMA CO observations)
- casa version: CASA 4.5.3  
  > "The North American ALMA Science team used CASA version 4.5.3 to manually calibrate the data." (2.1 New ALMA CO observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Neptune / J2357-5311 / J0334-4008 (varies by night)  
  > "Flux calibrator | Neptune | J2357-5311 | J0334-4008 | J2357-5311 | J0334-4088" (Table 2)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA multiscale CLEAN  
  > "We imaged our data in CASA using the `multiscale` CLEAN algorithm." (2.1 New ALMA CO observations)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "natural weighting was chosen in order to maximize sensitivity" (2.1 New ALMA CO observations)
- uv taper: Gaussian tapers giving ~3'' and ~6'' resolution  
  > "We used Gaussian taper functions that yielded final resolutions of roughly $3\mbox{$^{\prime\prime}$}$ and $6\mbox{$^{\prime\prime}$}$." (2.1 New ALMA CO observations)
- cell size: 0.25'' x 0.25'' x 1.5 km/s  
  > "The final data cube has voxels with dimensions of $0.25\ensuremath{''}\times 0.25\ensuremath{''} \times 1.5~\mbox{km~s$^{-1}$}$" (2.1 New ALMA CO observations)
- image size: _not stated_
- masking: hand-drawn mask around significant coherent emission; stop when cumulative flux converges  
  > "a mask was drawn around all the significant and coherent emission." (2.1 New ALMA CO observations); "The deconvolution was stopped when the cumulative flux as a function of the number of CLEAN iterations converged." (2.1 New ALMA CO observations)
- multiscale scales: _not stated_
- continuum subtraction: continuum (~4 mJy) imaged and subtracted from line emission  
  > "We imaged the continuum emission, detected a total flux of about 4 mJy, and subtracted this from the line emission." (2.1 New ALMA CO observations)
- line free channels: _not stated_
- primary beam correction: applied using combined beam pattern of the two pointings  
  > "we applied a primary beam correction, using the combined beam pattern of the two pointings" (2.1 New ALMA CO observations)
- array combination: no total power/short-spacing data  
  > "We did not have total power observations" (2.1 New ALMA CO observations)
- smoothing: _not stated_
- final beam: 1.31''x1.08'' (24.6 x 20.3 pc)  
  > "The synthesized beam was measured to be $1.31\ensuremath{''}\times 1.08\ensuremath{''}$" (2.1 New ALMA CO observations)
- final rms: 10.3 mJy per 1.5 km/s channel  
  > "The rms sensitivity is $10.3$ mJy per $1.5~\mbox{km~s$^{-1}$}$ channel." (2.1 New ALMA CO observations)

### Inherited from earlier work

- CPROPS algorithm and default parameters (t=4, e=2)  
  > "We adopted the default values, $t=4$ and $e=2$, similar to previous studies." (4.1 GMC Identification) [from (cite: Rosolowsky_2006)]
- Resolution limit of ~11 pc  
  > "Following (cite: Faesi_2018), who in their study of NGC 300 molecular clouds found that GMC sizes smaller than half the beamsize were not well recovered" (4.2 GMC Properties) [from (cite: Faesi_2018)]
- False-detection test  
  > "This procedure precisely follows that outlined in (cite: Utomo_2015) (Appendix C; see also (cite: Engargiola_2003))." (4.2 GMC Properties) [from (cite: Utomo_2015)]
- Internal extinction correction via Balmer decrement  
  > "We applied the Balmer decrement (i.e., the ratio of the H$\alpha$/H$\beta$ lines) to correct for internal dust extinction, following (cite: Kreckel_2013)." (2.2 Archival Hubble Halpha observations) [from (cite: Kreckel_2013)]
- Continuum subtraction strategy for Halpha  
  > "following the strategy suggested by (cite: Cannon_2002; Cannon_2003)" (2.2 Archival Hubble Halpha observations) [from (cite: Cannon_2002; Cannon_2003)]

### Not stated but needed to reproduce (our reading)

- Multiscale scales, cell/image size in pixels, number of CLEAN iterations and threshold
- Line-free channels used for continuum subtraction
- Exact uv-taper parameters
- Flux scale uncertainty and calibrator flux values
- Whether archive-delivered or reprocessed calibrated data were used
- CPROPS settings beyond defaults (e.g. exact masks, MAXPEAK/fudge values)
- Halpha flux values/aperture definitions for regions A-D and the Butterfly/Serpent boundaries
- Project-code discrepancy: acknowledgments print 2015.1.01569.S

## Analysis recipe

1. **Image the CO cube and continuum**: Multiscale CLEAN with natural weighting, masked, continuum subtracted, primary-beam corrected; tapered cubes for flux recovery  
  > "We imaged our data in CASA using the `multiscale` CLEAN algorithm." (2.1 New ALMA CO observations)
   - software: CASA
   - parameter: 1.5 km/s channels, 0.25'' pixels  
  > "voxels with dimensions of $0.25\ensuremath{''}\times 0.25\ensuremath{''} \times 1.5~\mbox{km~s$^{-1}$}$" (2.1 New ALMA CO observations)
   - fitting: _not stated_
   - validation: Residual cubes look like noise; repeat with double CLEAN iterations; tapered cubes recover 96% (3'') and 71% (6'') of flux  
  > "the $3\mbox{$^{\prime\prime}$}$ cube captures 96% of the total flux, and the $6\mbox{$^{\prime\prime}$}$ cube captures $71\%$ of the total flux" (2.1 New ALMA CO observations)
2. **Global CO spectrum and molecular mass**: Average brightness temperature per channel, fit a Gaussian, convert luminosity to mass with Galactic alpha_CO  
  > "We fit a Gaussian to the spectrum, and we measure a peak temperature of $146\pm6$ mK" (3.1 Integrated intensity)
   - assumption: alpha_CO = 4.35 Msun (K km/s pc^2)^-1  
  > "The conversion factor typically used for the Milky Way is $\alpha_{\rm CO}=4.35$ $M_\odot$ (K km s$^{-1}$ pc$^2$)$^{-1}$" (3.1 Integrated intensity)
   - fitting: _not stated_
   - validation: Compared with Mopra single-dish luminosity and mass  
  > "The values obtained by (cite: Cormier_2014) are in good agreement with our total values" (3.1 Integrated intensity)
3. **Identify GMCs and measure properties**: CPROPS with CLUMPFIND modification, extrapolation to 0 K, beam/channel deconvolution, 50 bootstraps  
  > "We used 50 bootstrap iterations to estimate the uncertainties." (4.1 GMC Identification)
   - software: CPROPS
   - parameter: t=4, e=2, 15 pc x 15 pc x 2 km/s search box, EDGE=2  
  > "CPROPS searches for local emission peaks by scanning the islands with a moving box having dimensions $15~\ensuremath{\mbox{pc}}\times 15~\ensuremath{\mbox{pc}}\times 2~\mbox{km~s$^{-1}$}$." (4.1 GMC Identification)
   - assumption: Mvir=1040 R sigma_v^2, spherical clouds with rho ~ R^-1; Milky Way alpha_CO  
  > "assumes that clouds are spherically symmetric and have power law volume density ($\rho$) profile $\rho \propto R^{-1}$" (4.2 GMC Properties)
   - fitting: _not stated_
   - validation: Poisson false-detection test and false-source injection/recovery (~7000 sources, 1000 iterations)  
  > "We conducted 1000 iterations of this process, resulting in approximately 7000 false sources injected in total." (4.2 GMC Properties)
4. **Larson scaling relations**: Spearman rank correlation and BCES fits of size-linewidth, C-Sigma, Mvir-Mlum, mass-size  
  > "We fit correlations using the "BCES" (bivariate, correlated errors with intrinsic scatter) method of (cite: Akritas_1996)." (4.3 The Larson Relations in NGC 625)
   - software: BCES
   - fitting: _not stated_
   - validation: Repeated fits excluding clouds below resolution/completeness limits  
  > "If we exclude these 3 GMCs and only fit data points with values of $R$ and $\sigma_v$ above these limits, the correlation remains poor $(r_s=0.19)$." (4.3.1 Size-linewidth relation)
5. **Halpha SFR map and extinction correction**: HST Halpha continuum-subtracted, corrected for Galactic extinction and Balmer decrement, converted with Kennicutt & Evans relation  
  > "we use the conversion provided by (cite: Kennicutt_2012)" (6.2 Small scales)
   - assumption: Case B, T=10,000 K, ne=100 cm^-3, Halpha/Hbeta=2.86; SFR constant over 10 Myr  
  > "Theoretically, the (unobscured) H$\alpha$/H$\beta$ ratio is equal to 2.86, under the assumption of Case B recombination" (2.2 Archival Hubble Halpha observations)
   - fitting: _not stated_
   - validation: Total SFR agrees with Cannon et al. 2003  
  > "is furthermore in excellent agreement with the SFR estimate from (cite: Cannon_2003)" (2.2 Archival Hubble Halpha observations)
6. **Depletion times**: tau_dep = M_H2/SFR globally and in HII regions A-D, Butterfly, Serpent  
  > "$$\tau_{\rm dep}\equiv \frac{\ensuremath{M_{{\rm H}_2}}}{\rm{SFR}},$$" (6.1 Global scales)
   - parameter: upper limit SFR <~5e-4 Msun/yr for Butterfly and Serpent  
  > "we assume an upper limit of SFR$\lesssim 5\times10^{-4} \ensuremath{M_\odot}$ yr$^{-1}$" (6.2 Small scales)
   - assumption: Galactic alpha_CO; possibly higher (3x, ~9x with metallicity scaling)  
  > "assuming that $\alpha_{\rm CO}\propto Z^{-2}$ (cite: Schruba_2012), the CO-to-$\mbox{H$_2$}$ conversion factor in NGC 625 is $\sim 9$ times the standard Galactic value." (6.1 Global scales)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.5.3: calibration and imaging  
  > "Our data were processed and imaged using the Common Astronomy Software Applications (CASA) package" (2.1 New ALMA CO observations)
- **CPROPS** : cloud identification and property measurement  
  > "We used the `CPROPS` algorithm (cite: Rosolowsky_2006) to find clouds in our $1\mbox{$^{\prime\prime}$}$ data cube" (4.1 GMC Identification)
- **BCES** : fitting scaling relations  
  > "We fit correlations using the "BCES" (bivariate, correlated errors with intrinsic scatter) method of (cite: Akritas_1996)." (4.3 The Larson Relations in NGC 625)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Total molecular gas mass (Galactic alpha_CO) | 5.34e6 | 0.34e6 | Msun | 2 | corresponds to a total molecular mass of $(5.34\pm0.34)\times 10^6$ $M_\odot$ |
| Integrated CO intensity | 3.00 | 0.19 | K km/s | 2 | $I_{\rm CO}=(3.00\pm 0.19)$ K km s$^{-1}$ |
| CO luminosity | 1.2e6 | not stated | K km/s pc^2 | 2 | the luminosity of this region is $1.2\times10^6$ K km s$^{-1}$ pc$^2$ |
| Clouds identified / resolved | 33 / 19 | not stated | dimensionless | 3 | we catalog 33 clouds. Fourteen clouds have deconvolved radii smaller than the telescope beam |
| Median cloud surface density | 169 | not stated | Msun pc^-2 | 3 | $20$ pc, $2.5$ km s$^{-1}$, $1.7\times 10^5$ $M_\odot$, and 169 $M_\odot$ pc$^{-2}$ |
| 50% completeness limits | 6.5e4 Msun and 55 Msun pc^-2 | not stated | Msun; Msun pc^-2 | 3 | 50% completeness limits of $6.5\times10^4~\ensuremath{M_\odot}$ and $55~\ensuremath{M_\odot}$ pc$^{-2}$ |
| Size-linewidth slope | 0.91 | 0.36 | dimensionless | 4 | $\sigma_v\propto R^{0.91\pm0.36}$ |
| Virial fit Mvir vs Mlum | Mvir=0.50 Mlum^1.04 | 0.16 (norm), 0.03 (slope) | dimensionless | 4 | $\ensuremath{M_{\rm vir}}=(0.50\pm0.16)\ensuremath{M_{\rm lum}}^{1.04\pm0.03}$ |
| Mass-size fit | Mlum=466 R^2.06 | 0.11 (slope) | dimensionless | 4 | $\ensuremath{M_{\rm lum}}= 466 R^{2.06\pm0.11}$ |
| Global molecular depletion time | 106-134 | not stated | Myr | 6 | $\tau_{\rm dep}\approx 106$-134 Myr |
| Butterfly depletion time | >=5.0 | not stated | Gyr | 6 | $\ge 5.0$ Gyr |

## Qualitative findings

- Molecular gas is in discrete clouds with no well-ordered large-scale motions.  
  > "Molecular gas is distributed in discrete clouds within an area of $0.4$ kpc$^2$ and does not have well-ordered large-scale motions." (abstract)

## Claim tuples

- H: Are NGC 625 clouds in virial equilibrium? | E: Compared Mvir with Mlum for 19 resolved clouds | R: r_s=0.90, Mvir ∝ Mlum^1.04 | F: Clouds are mostly in virial equilibrium (assuming Galactic alpha_CO) | **supported**
- H: Do NGC 625 clouds follow the size-linewidth relation? | E: BCES fit and Spearman test | R: r_s=0.18, slope 0.91±0.36 | F: Linewidth and size are at best weakly correlated | **partially**
- H: How do GMCs relate to star formation sites? | E: Compare CO clouds with HST Halpha SFR map and compute depletion times | R: Bright HII regions have tau_dep 35-230 Myr; Butterfly >=5 Gyr, Serpent >=1.5 Gyr | F: About half of clouds are on bright HII regions; Butterfly and Serpent are quiescent | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Natural weighting chosen to maximize sensitivity for cloud properties  
  > "natural weighting was chosen in order to maximize sensitivity" (2.1 New ALMA CO observations)
- Alternative: Tapered 3'' and 6'' cubes tested for missing flux; they recovered less flux than the full-resolution cube  
  > "they suppressed enough information at small scales that the overall recovered flux was less than that in the high-resolution cube" (2.1 New ALMA CO observations)
- How they decided it was enough: _not stated_
- Limitation (authors): CO-to-H2 conversion factor in NGC 625 is uncertain and may be higher, lengthening depletion times  
  > "we repeat the caveat that the average CO-to-$\mbox{H$_2$}$ conversion factor in NGC 625 may be higher than the Milky Way value" (6.1 Global scales)
- Limitation (authors): No total power data  
  > "We did not have total power observations" (2.1 New ALMA CO observations)
- Caveat (inferred, ours): Mass-size slope near 2 may be an observational artifact
- Caveat (inferred, ours): Resolution of ~1.3'' means few clouds are well resolved
- Caveat (inferred, ours): Halpha upper limits for Butterfly/Serpent are crude
- Caveat (inferred, ours): Depletion times depend strongly on alpha_CO

## Reproducibility

- Data public (paper): ALMA project code is given; HST data from Hubble Legacy Archive  
  > "(project code 2015.1.01395.S; PI: Nia Imara)" (2.1 New ALMA CO observations)
- Products in archive: _not stated_
- Missing: CLEAN parameters (scales, iterations, threshold)
- Missing: Line-free channels
- Missing: Halpha region flux measurements
- Missing: Exact CPROPS extra settings
- Data volume (inferred): ~50-100 GB raw for five execution blocks
- Score (inferred): 3/5, Public ALMA data and stated cloud-finding recipe, but imaging parameters and the Halpha SFR steps are only partly specified.
- Rediscovery candidate: yes, Data are public, the CPROPS recipe is largely stated, and the main results are numeric (mass, cloud medians, scaling fits).

## Links

- Method: Rosolowsky & Leroy 2006 (cite: Rosolowsky_2006) (CPROPS algorithm)
- Method: Utomo et al. 2015 (cite: Utomo_2015) (false-detection test)
- Method: Faesi et al. 2018 (cite: Faesi_2018) (resolution limit and CPROPS parameter effects)
- Companion: Imara & Faesi 2019 (cite: Imara_2019) (similar ALMA cloud study of Henize 2-10)
- Companion: Cannon et al. 2003 (cite: Cannon_2003) (HST Halpha data and HII regions)

## Checks

```json
{
 "quotes": 88,
 "quotes_ok": 88,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [
  "2015.1.01569.S"
 ],
 "numeric_results": 11,
 "numeric_problems": 0,
 "fill": {
  "facts": 86,
  "stated": 66,
  "rate": 0.767
 },
 "evidence_ok": true
}
```
