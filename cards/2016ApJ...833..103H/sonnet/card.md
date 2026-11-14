# Kiloparsec-scale Dust Disks in High-redshift Luminous Submillimeter Galaxies

`2016ApJ...833..103H` | The Astrophysical Journal 2016 | first author: Hodge, J. A. | arXiv: 1609.09649 | DOI: 10.3847/1538-4357/833/1/103

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies
- Question: How is the dust-obscured star formation distributed (size, profile, clumpiness) in luminous z~2.5 SMGs at ~1 kpc resolution, and how does it compare with the stellar emission?  
  > "This dust imaging traces the dust–obscured star formation in these $z\sim2.5$ galaxies on $\sim$1.3 kpc scales." (abstract)
- Target **16 ALESS SMGs in the ECDFS (e.g. ALESS 1.1, 15.1, 73.1)**: coordinates _not stated_; z/distance z=0.76-4.95, median z=2.6±0.5  
  > "These sources span a redshift range $z=0.76-4.95$, with a median redshift ($z=2.6\pm0.5$)" (2.2 Data Reduction & Imaging); distance from Simpson et al. 2014 / Swinbank et al. 2014 (cite)  
  > "These sources span a redshift range $z=0.76-4.95$, with a median redshift ($z=2.6\pm0.5$)" (2.2 Data Reduction & Imaging)

## Data provenance

- ALMA projects: 2012.1.00307.S
- bands: Band 7, 344 GHz / 870 um  
  > "we observed all fields with ALMA’s Band 7 centered at 344 GHz/870$\mu$m" (2.1 Sample Selection & Observations)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: 8 GHz, single continuum mode, 4 x 128 channels  
  > "with 4 $\times$ 128 dual polarization channels over the 8 GHz bandwidth" (2.1 Sample Selection & Observations)
- arrays: _not stated_
- configurations: C32-6, 46 antennas  
  > "requested in the C32-6 configuration and carried out with 46 antennas in an extended configuration" (2.1 Sample Selection & Observations)
- baselines: ~15 m to ~1.6 km  
  > "minimum baseline of $\sim$15m, maximum baseline of $\sim$1.6 km" (2.1 Sample Selection & Observations)
- angular resolution: 0.17x0.15 arcsec natural; 0.12x0.11 arcsec robust -0.5  
  > "the naturally weighted maps achieve a typical synthesized beam of 0.17$''$$\times$0.15$''$" (2.2 Data Reduction & Imaging)
- max recoverable scale: >~2 arcsec  
  > "consistent with the maximum recoverable scale expected for this configuration ($\gtrsim$2$''$)" (2.3 Recovered Flux Density)
- sensitivity: ~64 uJy/beam natural; ~130 uJy/beam robust -0.5  
  > "RMS noise of $\sim$64 $\mu$Jy beam$^{-1}$" (2.2 Data Reduction & Imaging)
- time on source: ~8 minutes per field  
  > "the total integration time on each of the target fields was approximately 8 minutes" (2.1 Sample Selection & Observations)
- observing dates: 11–27 Aug 2015  
  > "taken between 11–27 Aug 2015" (2.1 Sample Selection & Observations)
- pi or archival as stated: _not stated_
- Other facility **HST WFC3 (CANDELS and Cycle 20 program)**: H160-band imaging for stellar morphology comparison  
  > "Our SMGs were selected to have *HST* WFC3 imaging at comparable (0.15$''$) resolution in one or more bands" (3.2 Comparison to stellar emission)
- External data: Cycle 0 ALESS 870um flux densities, flux-boost corrected  
  > "The Cycle 0 flux densities were taken from (cite: 2013ApJ...768...91H) and have been corrected for the effect of flux boosting" (2.3 Recovered Flux Density) [from (cite: 2013ApJ...768...91H); (cite: 2015ApJ...807..128S)]
- External data: LFIR, Tdust, SFR, dust masses and redshifts for SMGs  
  > "we have used the $L_{\rm FIR}$ and $T_{\rm dust}$ values reported in (cite: 2014MNRAS.438.1267S)" (3.4 The L_IR–T relation and gas surface densities) [from (cite: 2014MNRAS.438.1267S)]

## Processing

### Calibration

- pipeline or manual: Delivered reduction used without modification  
  > "The delivered reduction produced $uv$–data products of high quality and was therefore used without further modifications." (2.2 Data Reduction & Imaging)
- casa version: CASA 4.3.1 reduction and imaging; 4.5.0 analysis  
  > "The $uv$–data were imaged using casa version 4.3.1, with subsequent analysis carried out in casa version 4.5.0." (2.2 Data Reduction & Imaging)
- pipeline version: _not stated_
- archive products used as is: yes  
  > "was therefore used without further modifications" (2.2 Data Reduction & Imaging)
- flux calibrator: J0522-3627 (bandpass listed third)  
  > "The phase, flux, and bandpass calibrators were J0348$-$2749, J0334$-$401, and J0522$-$3627, respectively" (2.1 Sample Selection & Observations)
- flux scale uncertainty: ~10%  
  > "The absolute flux calibration has an uncertainty of $\sim$10%" (2.2 Data Reduction & Imaging)
- self calibration: not attempted  
  > "We did not attempt to self-calibrate the data." (2.2 Data Reduction & Imaging)

### Imaging

- task: CASA clean, interactive  
  > "All maps were cleaned interactively using 1.5$''$ circular regions around sources" (2.2 Data Reduction & Imaging)
- deconvolver: multi-scale clean  
  > "multi-scale clean (cite: 2008ISTSP...2..793C) was employed using scales of \[0$''$, 0.3$''$, 0.6$''$, 1.2$''$\]" (2.2 Data Reduction & Imaging)
- weighting robust: natural; Briggs robust = -0.5 for high-res  
  > "Briggs weighting with a robust parameter of $R=-0.5$" (2.2 Data Reduction & Imaging)
- uv taper: tapered maps at 0.3 and 0.5 arcsec  
  > "median fractions of $f=110\pm6\%$ and $f=112\pm6\%$ in the 0.3$''$ and 0.5$''$ maps" (2.3 Recovered Flux Density)
- cell size: 0.02 arcsec  
  > "have a pixel scale of 0.02$''$" (2.2 Data Reduction & Imaging)
- image size: 25.6 arcsec per side  
  > "The resulting images are 25.6$^{\prime\prime}$ per side" (2.2 Data Reduction & Imaging)
- masking: 1.5 arcsec circular regions, cleaned to ~2.5 sigma  
  > "These sources were cleaned down to $\sim$2.5$\sigma$, a process which typically required 1–5 major clean cycles of 50 iterations each." (2.2 Data Reduction & Imaging)
- multiscale scales: 0, 0.3, 0.6, 1.2 arcsec  
  > "scales of \[0$''$, 0.3$''$, 0.6$''$, 1.2$''$\]" (2.2 Data Reduction & Imaging)
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: Cycle 0 data not combined  
  > "The (compact configuration) Cycle 0 data were not co–added to the new data" (2.2 Data Reduction & Imaging)
- smoothing: _not stated_
- final beam: 0.17x0.15 arcsec (natural); 0.12x0.11 arcsec (R=-0.5)  
  > "resulting in a resolution of 0.12$''$$\times$0.11$''$" (2.2 Data Reduction & Imaging)
- final rms: ~64 uJy/beam (natural); ~130 uJy/beam (R=-0.5)  
  > "typical RMS noise values of $\sim$130 $\mu$Jy beam$^{-1}$" (2.2 Data Reduction & Imaging)

### Inherited from earlier work

- Image-plane fitting with point source, 2D Gaussian and 2D Sérsic models  
  > "Following (cite: 2015ApJ...799...81S), we quantified the morphology and extent of the emission by fitting each source in the image plane with three models" (3.1.1 Image plane) [from (cite: 2015ApJ...799...81S)]
- Extinction Av calculated following Güver & Özel  
  > "The corresponding extinction ($A_{\rm v}$) values were calculated as in (cite: 2009MNRAS.400.2050G)." (3.4 The L_IR–T relation and gas surface densities) [from (cite: 2009MNRAS.400.2050G)]

### Not stated but needed to reproduce (our reading)

- Which calibrator was used for which role (flux vs phase) is ambiguous in the order given
- Fitting software and uncertainty method for the image-plane 2D Gaussian/Sérsic fits
- Priors/likelihood and tool for the uv-plane fits
- CASA simulation setup (simobserve parameters, noise injection) for disk simulations
- Exact SED-derived dust masses and temperatures used for gas surface densities
- Whether the ALMA project 2011.0.00294.S Cycle 0 data were re-reduced

## Analysis recipe

1. **Image the data**: CASA clean with natural, R=-0.5 and uv-tapered weightings; multi-scale clean  
  > "Imaging was carried out using the clean algorithm with a variety of different weightings and $uv$–taperings" (2.2 Data Reduction & Imaging)
   - software: CASA
   - parameter: scales 0, 0.3, 0.6, 1.2 arcsec; R=-0.5  
  > "scales of \[0$''$, 0.3$''$, 0.6$''$, 1.2$''$\]" (2.2 Data Reduction & Imaging)
   - fitting: _not stated_
   - validation: _not stated_
2. **Check recovered flux versus Cycle 0**: Mask below 2 sigma, sum in aperture of 3 x b_maj, compare with Cycle 0 flux across resolutions  
  > "we calculated the flux density recovered by masking the emission below 2$\sigma$" (2.3 Recovered Flux Density)
   - fitting: _not stated_
   - validation: Compared uv-tapered and natural maps  
  > "However, there appears to be a potentially small increase in the recovered fraction in the $uv$–tapered data, with median fractions of $f=110\pm6\%$ and $f=112\pm6\%$ in the 0.3$''$ and 0.5$''$ maps, respectively." (2.3 Recovered Flux Density)
3. **Measure sizes and profiles**: Fit 2D Gaussian and 2D Sérsic in image plane; stack rotated 2 arcsec cutouts  
  > "fitting each source in the image plane with three models: (1) a point source (assuming the CLEAN beam); (2) a two–dimensional Gaussian; and (3) a two–dimensional Sérsic profile." (3.1.1 Image plane)
   - fitting: _not stated_
   - validation: 10,000 injected model sources recovered with ~1% bias; tapered, half-light and 15% added-emission tests; uv-plane fits  
  > "we inserted 10,000 model sources with S/N ratios similar to our observations into the naturally weighted maps" (3.1.1 Image plane)
4. **uv-plane size fits**: Radially average visibilities in 75 klambda bins; fit Gaussian and Gaussian+constant  
  > "the data have then been radially averaged in bins of 75 k$\lambda$" (3.1.2 uv–plane fits)
   - fitting: _not stated_
   - validation: Compared with image-plane sizes  
  > "When we include a point source component in the $uv$–plane model, we find that the FWHM sizes derived from fitting in the image and $uv$–planes agree (within the uncertainties)." (3.1.2 uv–plane fits)
5. **Compare to HST stellar emission**: Curves of growth in 1.5 arcsec aperture on ALMA and H160 images  
  > "calculated using a 1.5$''$ radius aperture centered on the ALMA emission" (3.2 Comparison to stellar emission)
   - fitting: _not stated_
   - validation: _not stated_
6. **Search for clumps**: Image at R=-0.5, subtract 2D Gaussian, compare with 16 simulated smooth exponential disks  
  > "we used casa to simulate 16 observations of smooth exponential disks with the same angular resolution and noise levels" (3.3 Clumps)
   - software: CASA
   - parameter: Re=0.26 arcsec, axis ratio 0.5, S870~6.5 mJy  
  > "an effective radius of $R_e = 0.26''$, an axis ratio of 0.5, and a total flux density of S$_{870\mu m}\sim6.5$ mJy" (3.3 Clumps)
   - fitting: _not stated_
   - validation: Simulated disks show similar apparent clumps  
  > "Indeed, many of the simulated exponential disks break up into a small number of closely-spaced emission peaks, similar to the observed high-resolution maps." (3.3 Clumps)
7. **Tdust–LIR–size and gas surface density**: Compare sizes with blackbody Stefan–Boltzmann predictions; convert SED dust mass to gas surface density  
  > "We have then converted these measurements to gas surface density by scaling the SED–derived dust mass and assuming a gas–to–dust ratio of 100." (3.4 The L_IR–T relation and gas surface densities)
   - assumption: optically thick blackbody; gas-to-dust ratio 100  
  > "we assume optically thick radiation" (3.4 The L_IR–T relation and gas surface densities)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.3.1 (reduction, imaging); 4.5.0 (analysis): data reduction, imaging, simulations  
  > "The ALMA data were reduced using the Common Astronomy Software Application[^1] (casa) version 4.3.1." (2.2 Data Reduction & Imaging)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Median Sérsic effective radius | 0.24 | ±0.02 | arcsec | 3 | median effective radius of $R_e=0.24$$''$$\pm$0.02$''$ |
| Median physical Re | 1.8 | ±0.2 | kpc | 3 | typical physical size of $R_{e}=1.8\pm$0.2 kpc |
| Median Sérsic index | 0.9 | ±0.2 | dimensionless | 3 | median Sérsic index of $n=0.9$$\pm$0.2 |
| Median Gaussian FWHM | 0.42 | ±0.04 | arcsec | 3 | FWHM$=$0.42$''$$\pm$0.04$''$ |
| Median ALMA half-light radius (curve of growth) | 0.16 | ±0.02 | arcsec | 5 | the median half–light radius of the ALMA 870$\mu$m emission is 0.16$''$$\pm$0.02$''$ |
| Median H160 half-light radius | 0.5 | ±0.1 | arcsec | 5 | the median half–light radius of the *H*$_{\rm 160}$–band imaging is 0.5$''$$\pm$0.1$''$ |
| Median recovered flux fraction, natural weighting | 101 | ±6 | % | 2 | median fraction of $f=101\pm6\%$ |

## Qualitative findings

- Dust emission is smooth and disk-like; no significant clumping in most sources; clump candidates in ALESS 15.1 only.  
  > "we find no significant evidence for clumping in the majority of cases" (abstract)
- Stellar H160 morphologies are more extended and disturbed, and uncorrelated with dust.  
  > "the stellar morphologies appear significantly more extended and disturbed" (abstract)

## Claim tuples

- H: Are SMG dust disks clumpy at ~1 kpc scales? | E: R=-0.5 imaging, Gaussian subtraction, simulations of smooth disks | R: No residuals >3 sigma; simulated smooth disks show similar peaks | F: No significant clumping; caution needed with moderate S/N | **supported**
- H: What are the dust sizes and profiles? | E: Image-plane Sérsic fits | R: Re=1.8 kpc, n=0.9 | F: Compact exponential disks | **supported**
- H: Dust and stars share morphology | E: Compare ALMA and HST H160 curves of growth | R: Stellar half-light radius factor ~3 larger | F: Stellar emission more extended and uncorrelated; suggests mergers | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Resolution/sensitivity may be too coarse for clumps; ~10–15% of emission may be missing from natural maps.  
  > "it is possible that the resolution of the current ALMA data ($\sim$0.16$''$; $\sim$1.3 kpc at $z\sim2.5$) is still slightly too coarse" (3.2 Comparison to stellar emission)
- Caveat (inferred, ours): Small sample of bright SMGs
- Caveat (inferred, ours): Fit uncertainties and sizes depend on S/N; stellar masses inherited from SED fits

## Reproducibility

- Data public (paper): Project codes given in acknowledgments  
  > "ADS/JAO.ALMA#2011.1.00294.S and ADS/JAO.ALMA#2012.1.00307.S" (Acknowledgments)
- Products in archive: _not stated_
- Missing: Fitting code and error estimation details
- Missing: Simulation scripts
- Data volume (inferred): ~tens of GB (15 fields, short integrations, Band 7)
- Score (inferred): 3/5, Imaging and analysis recipe mostly described but fitting tools and some parameters missing.
- Rediscovery candidate: yes, Public data, clear imaging recipe, numeric size/index results.

## Links

- Method: (cite: 2015ApJ...799...81S) (Image-plane fitting approach)
- Companion: (cite: 2013ApJ...768...91H) (Cycle 0 ALESS survey)
- Companion: (cite: 2015ApJ...799..194C) (HST morphologies of ALESS SMGs)
- Related: ALESS
- Related: LESS
- Related: CANDELS

## Checks

```json
{
 "quotes": 65,
 "quotes_ok": 65,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2011.0.00294.S"
 ],
 "codes_printed_but_missing": [
  "2011.1.00294.S"
 ],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 76,
  "stated": 53,
  "rate": 0.697
 },
 "evidence_ok": true
}
```
