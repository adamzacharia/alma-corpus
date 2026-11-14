# Physical Characterization of an Unlensed, Dusty Star-forming Galaxy at z = 5.85

`2019ApJ...887...55C` | The Astrophysical Journal 2019 | first author: Casey, Caitlin M. | arXiv: 1910.13331 | DOI: 10.3847/1538-4357/ab52ff

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies
- Question: What are the redshift, physical properties (gas, dust, stellar, dynamical and halo mass, SFR) and drivers of the unlensed z=5.85 DSFG Mambo-9, found in a 2 mm ALMA blank-field map?  
  > "Here we present a multi-wavelength characterization of the source in order to constrain its physical drivers and characteristics." (1 Introduction)
- Target **MM J100026.36+021527.9 (Mambo-9)**: coordinates A: 10:00:26.356 +02:15:27.94; B: 10:00:26.356 +02:15:26.63  
  > "MM J100026.36$+$021527.9 (a.k.a. “Mambo–9”), a dusty star-forming galaxy (DSFG) at $z=5.850\pm0.001$." (abstract); "| RA                                           | —                               | 10:00:26.356                         | 10:00:26.356                         | —                                    |" (Table 2); z/distance z=5.850 (A), 5.852 (B)  
  > "MM J100026.36$+$021527.9 (a.k.a. “Mambo–9”), a dusty star-forming galaxy (DSFG) at $z=5.850\pm0.001$." (abstract); "| RA                                           | —                               | 10:00:26.356                         | 10:00:26.356                         | —                                    |" (Table 2); distance from CO(6-5) detected in this work's ALMA data  
  > "MM J100026.36$+$021527.9 (a.k.a. “Mambo–9”), a dusty star-forming galaxy (DSFG) at $z=5.850\pm0.001$." (abstract); "| RA                                           | —                               | 10:00:26.356                         | 10:00:26.356                         | —                                    |" (Table 2)

## Data provenance

- ALMA projects: 2018.1.00037.A, 2018.1.00231.S, 2017.1.00373.S, 2016.1.00279.S
- bands: Band 3, Band 7 (new); Band 6 and Band 4 from other programs  
  > "two in band 3 (3 mm) and one in band 7 (870$\mu$m)" (2.2 ALMA Data)
- frequencies and spectral setup: Band 7: 329.5–333.5 and 341.5–345.5 GHz; Band 3 tuning 1: 86.6–90.3 and 98.6–102.4 GHz; tuning 2: 94.8–98.5 and 106.6–110.4 GHz  
  > "Band 7 observations covered frequencies 329.5–333.5 GHz and 341.5–345.5 GHz." (2.2 ALMA Data); "The first covers frequencies 86.6–90.3 GHz and 98.6–102.4 GHz." (2.2 ALMA Data)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: C43-4  
  > "They were taken on 2019-05-02 in the C43-4 configuration" (2.2 ALMA Data)
- baselines: _not stated_
- angular resolution: Band 7 0.36''x0.30'' (natural); Band 3 1.19''x1.09'' and 1.14''x0.93'' (natural)  
  > "with a synthesized beam of $0.36\ensuremath{''}\times0.30\ensuremath{''}$ (using natural weighting)" (2.2 ALMA Data)
- max recoverable scale: _not stated_
- sensitivity: Band 7 continuum RMS 26.9 uJy/beam; Band 3 line RMS 0.124 and 0.088 mJy/beam per 50 km/s; band 3 continuum 5.2 uJy  
  > "The continuum RMS reached over the 7.5 GHz bandwidth is 26.9 $\mu$Jy/beam." (2.2 ALMA Data)
- time on source: Band 7 6383 s; Band 3 14668 s and 15010 s (plus ~1500 s archival)  
  > "a total integration time of 6383 s, and a mean precipitable water vapor (PWV) of 0.9 mm." (2.2 ALMA Data)
- observing dates: Band 7 2019-05-02; Band 3 2019-04-30 to 2019-05-02  
  > "These data were taken on 2019-04-30 and 2019-05-01 in C43-4" (2.2 ALMA Data)
- pi or archival as stated: _not stated_
- Line: 12CO J=6-5 (not stated)
- Line: p-H2O 2(1,1)-2(0,2) (752 GHz)
- Other facility **HST, Spitzer IRAC (S-CANDELS)**: Optical/near-IR photometry for stellar mass  
  > "we use only the *HST* imaging from COSMOS (cite: scoville07a) and CANDELS (cite: koekemoer11a; grogin11a) data" (3.7.1 Optical/Near-Infrared SED Fit)
- Other facility **SCUBA-2, AzTEC, MAMBO, Herschel, VLA**: Archival (sub)mm/FIR/radio photometry  
  > "| SCUBA-2 | 850$\mu$m  | mJy | — | — | 5.84$\pm$0.87 | (cite: geach17b) |" (Table 1)
- External data: Archival ALMA band 3 spectral scan co-added with new data  
  > "co-added in the visibility plane with the archival spectral scan from (cite: jin19a) (2017.1.00373.S)" (2.2 ALMA Data) [from (cite: jin19a)]
- External data: 3 GHz VLA photometry  
  > "| VLA-3 GHz | 10 cm | $\mu$Jy  | 7.34$\pm$2.29 | (3.69$\pm$2.26) | 10.6$\pm$4.1 | (cite: smolcic17a) |" (Table 1) [from (cite: smolcic17a)]
- External data: alpha_850 = (6.7±1.7)e19 erg/s/Hz/Msun  
  > "is the empirically calibrated conversion factor from 850$\mu$m luminosity to ISM mass from (cite: scoville16a)" (3.4 Gas Mass) [from (cite: scoville16a)]

## Processing

### Calibration

- pipeline or manual: Standard reduction pipeline scripts, CASA 5.4.0; self-calibration for band 7  
  > "version 5.4.0 following the standard reduction pipeline scripts and using manually defined clean boxes during the cleaning process." (2.2 ALMA Data)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: Applied to band 7 (111 sigma detection)  
  > "Mambo–9 is detected at very high signal-to-noise (111$\sigma$) such that we performed self-calibration." (2.2 ALMA Data)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: Natural for fluxes; Briggs robust=0.0 for resolution; robust 0.5 for some maps  
  > "We use Briggs weighting with robust=0.0 where the signal-to-noise is sufficiently high to provide improved spatial resolution, while we use natural weighting to measure sources’ integrated flux densities" (2.2 ALMA Data)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: Manually defined clean boxes  
  > "using manually defined clean boxes during the cleaning process" (2.2 ALMA Data)
- multiscale scales: _not stated_
- continuum subtraction: Line analysis done on continuum-subtracted data  
  > "thus analysis of molecular line emission requires continuum-subtracted data" (3.1 Millimeter Spectral Line Measurements)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- uv-plane size fitting method  
  > "We perform this analysis in the $uv$-plane following the methodology outlined in (cite: spilker16a)." (3.5 Size Measurements) [from (cite: spilker16a)]
- Image-plane Gaussian size measurement  
  > "following the methodology of (cite: simpson15a) and (cite: hodge16a)" (3.5 Size Measurements) [from (cite: simpson15a); (cite: hodge16a)]
- Stellar population SED fit method  
  > "We use this isophotal photometry to estimate the stellar population modeling parameters following the methodology of (cite: finkelstein15a)." (3.7.1 Optical/Near-Infrared SED Fit) [from (cite: finkelstein15a)]
- Gas mass from dust continuum  
  > "We follow the methodology described in the Appendix of (cite: scoville16a) to derive a gas mass from dust continuum" (3.4 Gas Mass) [from (cite: scoville16a)]
- Halo mass assumptions  
  > "these are the same assumptions as used to estimate the halo mass of SPT0311" (4.1 Mass Budget and Halo Mass Rarity) [from (cite: marrone18a)]

### Not stated but needed to reproduce (our reading)

- CASA tclean parameters (cell, image size, niter, thresholds, deconvolver)
- Line-free channels and continuum-subtraction order
- Self-calibration solution intervals and number of rounds
- Which quantities used which beams/robust values for each flux
- CO SLED ratio used to convert CO(6-5) to CO(1-0)
- MCMC priors, chain length and likelihood for the IR SED fit
- Details of the Monte Carlo line-width estimation
- Aperture/region definitions for flux extraction
- Pipeline version and flux calibrators

## Analysis recipe

1. **Reduce and image ALMA data, measure continuum photometry**: CASA 5.4.0 pipeline, self-cal band 7, natural/Briggs imaging, co-add band 3 with archival scan  
  > "reduced and imaged using the Common Astronomy Software Application[^3] ( CASA) version 5.4.0 following the standard reduction pipeline scripts" (2.2 ALMA Data)
   - software: CASA
   - fitting: _not stated_
   - validation: 3 mm continuum consistent with Jin et al. measurement  
  > "Our 3 mm continuum flux density is consistent with the measurement from the (cite: jin19a) data." (2.2 ALMA Data)
2. **Measure line fluxes, widths and redshift**: Continuum-subtracted band 3 spectra; Gaussian fits; widths and uncertainties by Monte Carlo noise injection  
  > "We measure the FWHM and estimate uncertainties of both the $^{12}$CO($J\!=$6$\rightarrow$5) and p-H$_{2}$O(2$_{1,1}\!\rightarrow$2$_{0,2}$) features by using Monte Carlo simulations where noise is injected and the line-width remeasured." (3.1 Millimeter Spectral Line Measurements)
   - fitting: single and double Gaussian  
  > "we note that component A is best fit by a double Gaussian separated by 400 km s$^{-1}$" (3.1 Millimeter Spectral Line Measurements)
   - validation: Sum of A and B (Briggs) agrees with natural-weighted totals  
  > "the sum of band 3 measurements of component A and component B separately (using Briggs weighting and robust=0.0) are in agreement with the total integrated quantities" (3.1 Millimeter Spectral Line Measurements)
3. **Measure sizes**: uv-plane Sersic fit (n=1) to self-calibrated 870um data; image-plane 2D Gaussian cross-check  
  > "the size is measured with a fixed Sersic index of $n=1$ consistent with an exponential disk" (3.5 Size Measurements)
   - fitting: _not stated_
   - validation: Image-plane Gaussian sizes broadly consistent with uv-plane  
  > "they are broadly consistent with the $uv$-plane analysis" (3.5 Size Measurements)
4. **Derive dust mass and gas masses**: 3 mm continuum with CMB-corrected RJ formulae; Scoville alpha_850 gas mass; CO(6-5) gas mass via SLED and alpha_CO  
  > "We derive dust masses from our 3 mm continuum photometry centered on a wavelength of 3085 $\mu$m (rest-frame 450$\mu$m)." (3.3 Dust Mass)
   - assumption: beta=1.95, mass-weighted Tdust=25 K, kappa(450um)=1.3 cm2/g, alpha_CO=6.5  
  > "We adopt a mass-weighted dust temperature of 25 K throughout to be consistent with (cite: scoville16a)." (3.3 Dust Mass)
   - fitting: _not stated_
   - validation: CO-derived gas mass broadly consistent with dust-derived  
  > "These are broadly consistent with, yet more uncertain than, the dust continuum derived gas masses." (3.4 Gas Mass)
5. **Dynamical masses**: Mdyn=5 Re sigma^2/G (with 3/2 inclination factor) and Vmax^2 Rmax/G from PV diagram  
  > "the factor of five is a constant of proportionality determined to best represent galaxies in the local mass plane" (3.6 Dynamical Mass)
   - assumption: 870um sizes used with CO velocity dispersion  
  > "we use the measured 870$\mu$m dust-emitting sizes to estimate the galaxies’ dynamical masses" (3.6 Dynamical Mass)
   - fitting: _not stated_
   - validation: _not stated_
6. **SED fitting (OIR, FIR, energy balance)**: EAZY/FSPS then BC03 chi2 for OIR; Metropolis-Hastings MCMC modified blackbody + MIR power law (alpha=4) for FIR; Magphys for joint  
  > "The SED is fit using a simple Metropolis Hastings Markov Chain Monte Carlo with free parameters of $\lambda_{\rm peak}$" (3.7.2 Far-IR/millimeter SED Fit)
   - software: Source Extractor, EAZY, FSPS, Magphys
   - assumption: General opacity tau=1 at 200 um for A; optically thin for B; CMB heating included  
  > "we adopt the more general opacity model (with $\tau=1$ at $\lambda_{\rm rest}=200$ $\mu$m) for component A and the optically-thin model for component B" (3.7.2 Far-IR/millimeter SED Fit)
   - fitting: _not stated_
   - validation: _not stated_
7. **Halo mass and rarity**: Baryon budget to halo mass via 5% baryon fraction; compare to exclusion curves of Harrison & Hotchkiss for 135 arcmin2 survey  
  > "The alternate technique assumes that baryons, at most, are 5% of the halo mass" (4.1 Mass Budget and Halo Mass Rarity)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 5.4.0: Reduction and imaging  
  > "version 5.4.0 following the standard reduction pipeline scripts" (2.2 ALMA Data)
- **Source Extractor** : OIR photometry  
  > "We measure photometry using Source Extractor (cite: bertin96a)" (3.7.1 Optical/Near-Infrared SED Fit)
- **EAZY** : photo-z/SED fit with FSPS templates  
  > "we use the EAZY software (cite: brammer08a) to fit the photometry" (3.7.1 Optical/Near-Infrared SED Fit)
- **Magphys** : Energy-balance SED fit  
  > "to fit the full SED (both components together) using Magphys" (3.7.3 Energy Balance SED Fit)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Redshift (A+B) | 5.850 | 0.001 | dimensionless | 2 | $z=5.850\pm0.001$ |
| CO(6-5) integrated flux (total) | 0.48 | 0.03 | Jy km/s | 2 | The integrated $^{12}$CO($J\!=$6$\rightarrow$5) line flux is 0.48$\pm$0.03 Jy km s$^{-1}$ |
| p-H2O flux | 0.09 | 0.02 | Jy km/s | 2 | the p-H$_{2}$O(2$_{1,1}\!\rightarrow$2$_{0,2}$) line flux is 0.09$\pm$0.02 Jy km s$^{-1}$ |
| Re(A) 870um | 408 pc (uv-plane) | 12 pc | pc | 3 | $R_{\rm e}(A)=$$0.068\ensuremath{''}\pm0.002\ensuremath{''}=408\pm12$ pc |
| Dust mass A | 1.3e9 | 0.3e9 | Msun | 4 | We infer a dust mass of (1.3$\pm$0.3)$\times10^{9}$  M$_\odot$ for component A |
| Gas mass from dust (total) | 1.7e11 | 0.4e11 | Msun | 4 | (1.7$\pm$0.4)$\times10^{11}$ |
| Dynamical mass A | 2.0e11 | 0.8e11 | Msun | 5 | we adopt the more conservative higher-mass dynamical constraint for component A of (2.0$\pm$0.8)$\times10^{11}$  M$_\odot$ |
| SFR A | 590 | +140/-100 | Msun/yr | 6 | 590$^{+140}_{-100}$  M$_\odot$ yr$^{-1}$ for component A |
| Stellar mass (OIR-only) | 3.2e9 | +1.0/-1.5 e9 | Msun | 6 | with a median of (3.2$^{+1.0}_{-1.5}$)$\times$10$^{9}$  M$_\odot$ |
| Halo mass | 3.3e12 | 0.8e12 | Msun | 7 | the total halo mass is predicted to be (3.3$\pm$0.8)$\times$10$^{12}$  M$_\odot$, with a 13% likelihood |
| Gas fraction | 96 | +1/-2 | % | 7 | $f_{\rm gas}=96^{+1}_{-2}$% |

## Qualitative findings

- Mambo-9 is a close pair (6 kpc) likely merging; component A optically thick near the peak, B optically thin  
  > "This system is comprised of (at least) two galaxies that are separated by 6 kpc likely undergoing a merger or interaction." (5 Conclusions)

## Claim tuples

- H: Is Mambo-9 at z=5.85, as proposed by Jin et al.? | E: Deep ALMA band 3 tunings co-added with archival scan | R: CO(6-5) at 14.7 sigma, p-H2O at 4.3 sigma, z=5.850 | F: Independent confirmation of redshift | **supported**
- H: Is Mambo-9 unlensed? | E: Search for foreground lenses in optical/NIR | R: Nearest possible lens gives mu=1.15-1.3 | F: Highest-redshift unlensed DSFG | **supported**
- H: What is the halo mass and gas/stellar content? | E: Mass budget with alpha_CO and stellar mass alternatives vs survey exclusion curves | R: Mhalo=3.3e12 Msun, fgas 96%, depletion 40-80 Myr | F: Gas-dominated merger-driven starburst in a rare halo | **partially**

## Reasoning

- Why this data: Additional tunings were needed because the 84 GHz line was at the band 3 edge and low S/N  
  > "additional tunings were needed to elucidate the redshift solution and characterize Mambo–9" (2.1 Source Selection & Prior Identification)
- Why this method: _not stated_
- Alternative: alpha_CO=1 and Magphys stellar mass considered; rejected low-mass option because GDR~16 anomalously low  
  > "the implied gas-to-dust ratio would be anomalously low, at GDR$\sim$16" (4.1 Mass Budget and Halo Mass Rarity)
- How they decided it was enough: _not stated_
- Limitation (authors): alpha_CO and stellar mass unconstrained  
  > "the unconstrained CO-to-H$_{\rm 2}$ conversion factor, and the unconstrained stellar mass chief among them" (5 Conclusions)
- Caveat (inferred, ours): Stellar mass differs by ~60x between fitting methods
- Caveat (inferred, ours): Component B has only a single line
- Caveat (inferred, ours): Dynamical mass relies on dust size with CO width
- Caveat (inferred, ours): Fixed Sersic index and assumed Td=25 K

## Reproducibility

- Data public (paper): ALMA programs listed in acknowledgments  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA #2018.1.00037.A, ADS/JAO.ALMA #2018.1.00231.S, ADS/JAO.ALMA #2017.1.00373.S, and ADS/JAO.ALMA #2016.1.00279.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: tclean parameters
- Missing: MCMC priors and SED code (forthcoming P. Drew paper)
- Missing: CO SLED ratio
- Missing: line-free channels
- Data volume (inferred): ~100-300 GB raw across four programs
- Score (inferred): 3/5, Data identifiable and many equations given, but imaging settings, SED code and priors missing.
- Rediscovery candidate: no, Recipe incomplete for imaging and SED fit, and 2018.1.00037.A data may be proprietary-period dependent.

## Links

- Method: (cite: scoville16a) (Gas mass from dust continuum)
- Method: (cite: da-cunha13a) (CMB correction)
- Method: (cite: spilker16a) (uv-plane size fitting)
- Method: (cite: casey12a) (SED fitting framework)
- Companion: (cite: jin19a) (Independent redshift identification with ALMA spectral scan)
- Related: ALMA 2 mm COSMOS blank-field map
- Related: COSMOS
- Related: CANDELS

## Checks

```json
{
 "quotes": 75,
 "quotes_ok": 75,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 4,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [
  "2018.1.00037.A"
 ],
 "obscore_codes_not_in_card": [
  "2018.A.00037.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 11,
 "numeric_problems": 0,
 "fill": {
  "facts": 84,
  "stated": 50,
  "rate": 0.595
 },
 "evidence_ok": true
}
```
