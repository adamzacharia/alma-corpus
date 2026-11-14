# Investigating Overdensities around z &gt; 6 Galaxies through ALMA Observations of [C II]

`2020ApJ...889...98M` | The Astrophysical Journal 2020 | first author: Miller, Tim B. | arXiv: 1611.08552 | DOI: 10.3847/1538-4357/ab63dd

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: high_z_galaxies, agn_and_quasars
- Question: Do luminous z>6 quasars and starbursts reside in overdense environments, as traced by companion [CII] emitters in deep archival ALMA Band 6 data?  
  > "In this paper we investigate the hypothesis that the environments of extreme objects at $z>6$ should possess overdensities of galaxies by performing a sensitive search for companions around quasars using [CII] emission lines." (Introduction)
- Target **CLM1**: coordinates _not stated_; z/distance z>6 (companion CLM1-A at z=6.180)  
  > "| $z_{\rm [CII]}$ | 6.180 | 6.432 | 6.427 |" (Results); distance from _not stated_
- Target **WMH5**: coordinates _not stated_; z/distance z>6  
  > "Our sample consists of deep $\sim$ 1.2 mm ALMA observations (Band-6) of five luminous objects at $z>6$." (Sample and Methods); distance from _not stated_
- Target **CFHQSJ0210-0546**: coordinates _not stated_; z/distance z>6 (companions at z=6.432 and 6.427)  
  > "| $z_{\rm [CII]}$ | 6.180 | 6.432 | 6.427 |" (Results); distance from _not stated_
- Target **J2329-0301**: coordinates _not stated_; z/distance z>6  
  > "Our sample consists of deep $\sim$ 1.2 mm ALMA observations (Band-6) of five luminous objects at $z>6$." (Sample and Methods); distance from _not stated_
- Target **J2054-0005**: coordinates _not stated_; z/distance z>6  
  > "Our sample consists of deep $\sim$ 1.2 mm ALMA observations (Band-6) of five luminous objects at $z>6$." (Sample and Methods); distance from _not stated_

## Data provenance

- ALMA projects: 2013.1.00815.S, 2011.0.00243.S, 2011.0.00206.S
- bands: Band 6 (~1.2 mm)  
  > "Our sample consists of deep $\sim$ 1.2 mm ALMA observations (Band-6) of five luminous objects at $z>6$." (2.1 Sample and Methods)
- frequencies and spectral setup: Four basebands (~8 GHz) for the first four cubes; only the 2 GHz baseband for J2054-0005; 15 MHz channels  
  > "we analyze the full $\sim$ 8 GHz from the four base bands, two centred on the extreme object, and two spaced $\sim15$ GHz away (in the upper sideband)." (2.1 Sample and Methods); "we were only able to retrieve the 2 GHz baseband containing the quasar itself" (2.1 Sample and Methods)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: typical beam ~0.6 arcsec  
  > "The typical beam size of the observations is $\sim 0.6^{\prime \prime}$." (2.1 Sample and Methods)
- max recoverable scale: _not stated_
- sensitivity: RMS 0.18-0.38 mJy per 15 MHz channel; 5 sigma ~ L_[CII] 1e8 Lsun at z=6  
  > "RMS Noise^\*^ (mJy)" (Table 1); "deep enough to detect sources down to a $5\sigma$ detection threshold of L$_{\rm [CII]} \approx 10^8 ~\mathrm{L_{\odot}}$ at $z=6$" (2.1 Sample and Methods)
- time on source: _not stated_
- observing dates: between 2012 and 2014  
  > "All of this data was obtained between 2012 and 2014" (2.1 Sample and Methods)
- pi or archival as stated: _not stated_
- Line: [CII] 2P3/2 -> 2P1/2 (157.7 micron)
- Other facility **Spitzer IRAC**: Checked for counterparts of companions (none found; ~100 s integrations)  
  > "We find no sources in Spitzer IRAC (CH1 & CH2) images at the locations of any of the three companions" (4 Discussion)
- Other facility **DECaLS DR8**: Optical g,r,z counterpart search (none found)  
  > "We also do not find optical counterparts in either the g,r or z band of the DECaLS DR8 images" (4 Discussion)
- External data: Field [CII] luminosity function measurements at z~6 (ASPECS blind search)  
  > "The most constraining field measurement comes from the ASPECS survey (cite: Aravena2016)" (2.2 Results) [from (cite: Aravena2016)]
- External data: Theoretical [CII] luminosity function predictions  
  > "Also shown are theoretical predictions of the [CII] luminosity function from previous studies (cite: Popping2016; Lagache2017)" (2.2 Results) [from (cite: Popping2016; Lagache2017)]
- External data: CO luminosity function models used to estimate number of low-z interlopers  
  > "Based on the  (cite: Popping2016) models for the luminosity functions of the CO rotational lines at various redshifts" (2.1 Purity of sample) [from (cite: Popping2016)]
- Simulation/model as data: Hayward et al. 2013 mock galaxy catalog: 8 light cones from Bolshoi halos, 15.7 deg^2, z up to 8, [CII] assigned from SFR via De Looze 2014 relation with 0.42 dex scatter  
  > "The eight mock galaxy catalogs cover a total area of 15.7 deg$^2$ extending out to $z=8$" (3.1 Mock Galaxy Catalogs); "applied with 0.42 dex of scatter, as quoted in their study" (3.1 Mock Galaxy Catalogs)

## Processing

### Calibration

- pipeline or manual: Raw archive data re-imaged with CASA using ScriptforImaging.py supplied with the data  
  > "The raw data from the archive was re-imaged using the Common Astronomy Software Applications package (CASA v. 4.2.2, (cite: Mcmullin2007)) task `clean`" (2.1 Sample and Methods)
- casa version: CASA v. 4.2.2  
  > "CASA v. 4.2.2, (cite: Mcmullin2007)" (2.1 Sample and Methods)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA clean, with parameters from ScriptforImaging.py  
  > "task `clean` using the parameters suggested in the `ScriptforImaging.py` provided by the joint ALMA observatory along with the raw data" (2.1 Sample and Methods)
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: Primary beam assumed Gaussian with FWHM = 23 arcsec at this frequency (used in volume calculation)  
  > "assumed to be a gaussian with FWHM = $23^{\prime \prime}$ at this frequency" (2.2 Results)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.5x0.5 to 0.79x0.5 arcsec (Table 1)  
  > "$0.79^{\prime \prime} \times 0.5^{\prime \prime}$" (Table 1)
- final rms: 0.18-0.38 mJy per 15 MHz channel  
  > "^\*^Per 15 MHz channel" (Table 1)

### Inherited from earlier work

- Imaging parameters taken from the ScriptforImaging.py supplied with the archive data; observing strategies from original papers  
  > "we refer the reader to the papers cited for full information about observing strategies" (2.1 Sample and Methods) [from (cite: Willott2013; Willott2015a; Wang2013)]
- Mock catalog construction follows Hayward et al. 2013  
  > "We provide a brief description of the methodology here but refer the reader to the original paper for full details." (3.1 Mock Galaxy Catalogs) [from (cite: Hayward2013)]
- S850 assignment following Hayward 2013 number counts  
  > "The 850$\mu$m flux densities (S$_{850}$) are assigned following (cite: Hayward:2013number_counts)" (3.1 Mock Galaxy Catalogs) [from (cite: Hayward:2013number_counts)]

### Not stated but needed to reproduce (our reading)

- clean parameters (robust, cell, image size, niter, threshold, mask) not given
- Whether continuum was subtracted before the search (not stated)
- Exact line-free channels used for continuum maps
- Exact observation-based details (flux calibrator, calibration steps) delegated to the archive
- Detailed volume and completeness calculation for the luminosity function and overdensity uncertainties
- Selection of mock primary galaxies and how the 'overdensity of 50' was normalised
- Mapping between L_[CII] and integrated flux (cosmology details, line-flux conversion)

## Analysis recipe

1. **Re-image archival data**: Re-imaged raw archive data with CASA clean using ALMA-provided ScriptforImaging.py parameters  
  > "The raw data from the archive was re-imaged using the Common Astronomy Software Applications package (CASA v. 4.2.2, (cite: Mcmullin2007)) task `clean`" (2.1 Sample and Methods)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Blind line search in cubes**: Find voxels >3 sigma in a 15 MHz channel, then require four neighbouring channels >2 sigma; fit Gaussian for FWHM, build moment 0 over FWHM, require S/N>5 with primary target masked and within primary beam FWHM; visual inspection  
  > "First, the entire cube was searched to find all points in the cube which exhibited a flux greater than 3$\times$ the rms noise in a single 15-MHz channel (typically 0.75 mJy beam$^{-1}$)." (2.1 Sample and Methods); "Any object with a S/N ratio greater than 5 that lies within the FWHM of the primary beam is deemed a possible candidate." (2.1 Sample and Methods)
   - software: Python, SpectralCube
   - parameter: 3 sigma peak, 4 channels >2 sigma (~50 km/s minimum width), S/N>5  
  > "If four surrounding channels (a minimal physical line width of $\sim50$ km s$^{-1}$) had fluxes greater than 2$\times$ the rms noise" (2.1 Sample and Methods)
   - fitting: Gaussian fit to line profile for redshift, FWHM and integrated flux  
  > "A Gaussian function was fit to each line in order to extract a redshift as well as the integrated flux and FWHM of the line." (2.2 Results)
   - validation: Recovers known WMH5-B; algorithm also recovers all [CII] emitters in a z=4.3 survey  
  > "Our approach to selecting sources based on the peak flux recovers all [CII] emitters found in a survey of galaxies at $z$=4.3 (cite: Miller2018)." (2.1 Sample and Methods)
3. **Assess purity and interlopers**: Search for negative peaks; check dirty beam sidelobes; estimate CO interlopers from Popping models; Monte Carlo test of velocity-offset distribution vs uniform; voxel flux distribution  
  > "To estimate the rate at which false positives could occur we apply our search algorithm to find negative peaks in the data." (2.1 Purity of sample)
   - software: CASA
   - parameter: 10,000 Monte Carlo iterations  
  > "After 10,000 iterations we find that 95% of the realizations contain at least 1 of the randomly selected velocity offsets" (2.1 Purity of sample)
   - fitting: _not stated_
   - validation: False positive rate 25%±25%, consistent with ASPECS ~35%  
  > "This false positive rate, of $25\% \pm 25\%$, is consistent with the statistical analysis performed by (cite: Aravena2016) on the ASPECS field" (2.1 Purity of sample)
4. **Compute [CII] luminosity function and overdensity**: Integrate detectable volume per luminosity accounting for per-field noise and Gaussian primary beam; compare with Aravena2016 and Lagache2017  
  > "We integrate the volume possible to detect a line emitting galaxy at a given luminosity by taking into account the differing noise properties of each field as well as the effect of the ALMA primary beam" (2.2 Results)
   - assumption: Flat LCDM, h=0.7, Omega_L=0.73, Omega_M=0.27  
  > "Throughout this study we assume a $\Lambda$CDM cosmology with parameters h$=0.7$ Mpc$^{-1}$, $\Omega_{\Lambda} = 0.73$ and $\Omega_{M} = 0.27$" (Introduction)
   - fitting: _not stated_
   - validation: _not stated_
5. **Mock catalog comparison**: Select simulated galaxies with L_[CII]=5e8-1e9 Lsun at 6<z<6.5, count companions within 15 arcsec and dz=0.05; compare dark matter mass in 2'x2', dz=0.2 volumes with random locations  
  > "We search the simulation around these galaxies for companions within a $15''$ radius and $dz = 0.05$, comparable to the search volume of the ALMA observations." (3.2 Simulation Results)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.2.2: Re-imaging raw data with clean; synthesized beam/sidelobe analysis  
  > "CASA v. 4.2.2, (cite: Mcmullin2007)) task `clean`" (2.1 Sample and Methods)
- **SpectralCube** : Analysis of data cubes in python  
  > "further analysis of the data cubes was performed with python, relying on the `SpectralCube`[^1] python package." (2.1 Sample and Methods)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| New robust [CII] companions | 3 | not stated | count | 2 | We identify 3 new robust line detections from a blind search of five deep fields |
| Relative overdensity of companions vs Aravena2016 | 6 | +4/-3 | dimensionless | 4 | find a relative over density of $6^{+4}_{-3}$ and $86^{+60}_{-37}$ |
| Relative overdensity of companions vs Lagache2017 | 86 | +60/-47 | dimensionless | 4 | we calculate relative overdensities of $6^{+4}_{-3}$ and $86^{+60}_{-47}$ at $L_{\rm [CII]} > 10^8\ L_\odot$ |
| False positive rate | 25% | ±25% | percent | 3 | This false positive rate, of $25\% \pm 25\%$ |
| Companion rate | 60% | ±34% | percent | 4 | We find companions at a rate of $60 \pm 34 \%$ (3 companions for 5 targets). |
| Simulated overdensity for matched L_[CII] sample | 50 | ±1 | dimensionless | 5 | of the matched L$_{\rm [CII]}$ sample of simulated galaxies of $50\pm 1$ |
| CLM1-A L_[CII] | 0.7 | ±0.2 | 1e8 Lsun | 2 | / L$_{\rm [CII]}$ ($10^8$ L$_{\odot}$) / 0.7 $\pm$ 0.2 / 1.8 $\pm$ 0.5 / 1.6 $\pm$ 0.4 / |
| Dark matter mass around matched simulated galaxies | 10^12.1 | ±0.3 dex | Msun | 5 | mean mass of $10^{12.1\pm 0.3} \rm \ M_\odot$ compared to $10^{11.5} \rm \ M_\odot$ for the random sample |

## Qualitative findings

- Companions have [CII] properties comparable to known z~5-6 galaxies, extending the L_[CII]-FWHM relation to lower values  
  > "extending the apparent relation to slightly lower values of L$_{\rm [CII]}$ and FWHM" (2.2 Results)
- Mock catalog shows luminous [CII] emitters sit in overdense dark matter regions  
  > "the luminous [CII] emitters during EOR reside in overdense regions of space" (5 Conclusion)

## Claim tuples

- H: Extreme z>6 sources have overdense environments traced by [CII] companions | E: Blind search of five deep archival ALMA cubes and luminosity function comparison with field measurements and predictions | R: 3 new companions, overdensity 6 (+4/-3) vs observed and 86 (+60/-47) vs predicted field | F: Central sources are likely highly biased tracers of mass | **supported**
- H: Candidates are real and not interlopers or noise | E: Negative-peak test, sidelobe check, velocity-offset Monte Carlo, interloper estimates | R: False positive rate 25%±25%; velocity offsets inconsistent with uniform at ~2-3 sigma; expected interlopers 0.25 | F: Candidates are probably mostly real but at least one may be false | **partially**
- H: Simulations reproduce the observed companion excess | E: Companion counts around luminosity-matched galaxies in Hayward13 mock catalog | R: Overdensity 50±1, consistent with observations | F: Simulations support the overdensity result | **supported**

## Reasoning

- Why this data: Deep pointed observations have lower noise than large-area surveys, allowing lower-luminosity detections  
  > "We are able to robustly detect lower-luminosity galaxies then other studies because the noise in these pointed deep fields is much lower than in larger area surveys." (4 Discussion)
- Why this method: _not stated_
- Alternative: Other Wang2013 quasar fields excluded because of higher RMS and coarser spectral resolution  
  > "however the RMS noise is larger ($\rm RMS > 0.5 mJy/channel$) and a larger spectral resolution of $\sim 80 \rm MHz$" (2.1 Sample and Methods)
- Alternative: WMH5-B excluded from analysis as part of an ongoing merger  
  > "They conclude it cannot be classified as two distinct sources and therefore we do not consider WMH5-B for the following analysis." (2.2 Results)
- How they decided it was enough: _not stated_
- Limitation (authors): Excess of large negative voxels suggests non-Gaussian correlated noise that can cause false positives  
  > "The excess of voxels with large negative fluxes is concerning as they are likely caused by correlated, non-Gaussian noise." (2.1 Voxel Flux Distribution)
- Limitation (authors): Lack of continuum/optical/NIR counterparts cannot rule out low-z CO interlopers  
  > "thus the lack of detection cannot rule out the possibility of interlopers." (4 Discussion)
- Limitation (authors): Simulations assign [CII] solely from SFR and do not treat quasar phase  
  > "The quasar-phase of galaxies and the growth of the super massive black holes is not specifically treated in this implementation." (4 Discussion)
- Caveat (inferred, ours): Only 3 candidates near S/N=5 with ~25% false positive rate; overdensity uncertainties are large
- Caveat (inferred, ours): Overdensity depends on extrapolating field LFs to L~1e8 where they are poorly constrained
- Caveat (inferred, ours): Targeted fields are biased by selection; comparison to blank-field LFs is not like-for-like
- Caveat (inferred, ours): Mock catalog uses a local L_[CII]-SFR relation and a simple model

## Reproducibility

- Data public (paper): Archival ALMA data retrieved from the archive  
  > "as well as the data retrieved from the archive for an additional quasar J054-0005 (cite: Wang2013)" (2.1 Sample and Methods)
- Products in archive: _not stated_
- Code: _not stated_
- Missing: clean parameters
- Missing: exact search code and thresholds for volume/completeness calculation
- Missing: mock catalog access and selection details
- Data volume (inferred): ~100-300 GB raw for five Band 6 datasets
- Score (inferred): 3/5, Public data and algorithm described, but imaging parameters, LF volume calculation, and mock catalog details are incomplete and code is not released.
- Rediscovery candidate: no, The search algorithm is described but imaging settings are delegated to archive scripts, and the LF/overdensity calculation and mock-catalog analysis are not fully specified.

## Links

- Method: (cite: Aravena2016) (Blind [CII] search purity statistics and field LF)
- Method: (cite: Hayward2013) (Mock galaxy catalog used for simulations)
- Companion: (cite: Decarli2017) (Companion [CII] emitters around z>6 quasars)
- Companion: (cite: Willott2015a) (Original CLM1 and WMH5 ALMA observations)
- Related: ASPECS

## Checks

```json
{
 "quotes": 68,
 "quotes_ok": 68,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 3,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 92,
  "stated": 48,
  "rate": 0.522
 },
 "evidence_ok": true
}
```
