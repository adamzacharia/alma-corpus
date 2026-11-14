# ALMA Reveals the Anatomy of the mm-sized Dust and Molecular Gas in the HD 97048 Disk

`2016ApJ...831..200W` | The Astrophysical Journal 2016 | first author: Walsh, Catherine | arXiv: 1609.02011 | DOI: 10.3847/0004-637X/831/2/200

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks
- Question: What are the spatial distributions of the mm-sized dust and CO gas in the HD 97048 disk, and does the disk have a cavity and substructure?  
  > "The observations reveal for the first time the spatial distribution of the large ( mm-sized) dust grains and molecular gas in this otherwise well-studied source." (1. INTRODUCTION)
- Target **HD 97048**: coordinates not stated (decl. ≈ -77 deg)  
  > "located in the Chameleon I star-forming region at a distance of ≈160 pc (van den Ancker et al. 1998; van Leeuwen et al. 2007)" (2. THE SOURCE: HD 97048); z/distance ≈160 pc  
  > "located in the Chameleon I star-forming region at a distance of ≈160 pc (van den Ancker et al. 1998; van Leeuwen et al. 2007)" (2. THE SOURCE: HD 97048); distance from van den Ancker et al. 1998; van Leeuwen et al. 2007  
  > "located in the Chameleon I star-forming region at a distance of ≈160 pc (van den Ancker et al. 1998; van Leeuwen et al. 2007)" (2. THE SOURCE: HD 97048)

## Data provenance

- ALMA projects: 2011.0.00863.S
- bands: _not stated_
- frequencies and spectral setup: seven spectral windows 300.506-347.331 GHz; channel width 122.070 kHz  
  > "the target was observed in seven spectral windows centered at 300.506, 301.286, 303.927, 344.311, 345.798, 346.998, and 347.331 GHz" (3. OBSERVATIONS)
- continuum bandwidth: 1.39 GHz at 302 GHz; 1.86 GHz at 346 GHz  
  > "the total available continuum bandwidth amounted to 1.39 GHz at 302 GHz (993 µm) and 1.86 GHz at 346 GHz (866 µm)" (3. OBSERVATIONS)
- arrays: 25 antennas, compact configuration (Cycle 0)  
  > "HD 97048 was observed with 25 antennas in a compact configuration during ALMA Cycle 0 operations" (3. OBSERVATIONS)
- configurations: _not stated_
- baselines: 15.1 to 402 m  
  > "Baselines ranged from 15.1 to 402 m" (3. OBSERVATIONS)
- angular resolution: 0.88x0.52 arcsec (302 GHz), 0.69x0.43 arcsec (346 GHz) Briggs; superuniform 0.73x0.40 and 0.61x0.36  
  > "This resulted in synthesized beams of 0 ′′ .88×0 ′′ .52 (-43 ◦ .9) at 302 GHz and 0 ′′ .69×0 ′′ .43 (-23 ◦ .2) at 346 GHz." (4.1.1 Continuum images)
- max recoverable scale: _not stated_
- sensitivity: rms 0.34 and 0.36 mJy/beam (continuum); 18.1 mJy/beam per channel (CO)  
  > "The respective rms noise is 0.34 and 0.36 mJy/beam." (4.1.1 Continuum images)
- time on source: 24 min 17 s (low freq) and 23 min 59 s (high freq)  
  > "The total on-source time was 24 minutes 17 s for the first execution (at the lower frequency) and 23 minutes 59 s for the second execution" (3. OBSERVATIONS)
- observing dates: 2012 December 14  
  > "on 2012 December 14 (program 2011.0.00863.S, P.I. C. Walsh)" (3. OBSERVATIONS)
- pi or archival as stated: _not stated_
- Line: CO J=3-2 (345.796 GHz)
- External data: Cavity radius 34 ± 4 au from mid-IR imaging/SED fits  
  > "The authors find that the SED and brightness profile are best fit with a dust cavity 34 ± 4 au in radius" (2. THE SOURCE: HD 97048) [from Maaskant et al. 2013]
- External data: Scattered light disk radius ≈640 au  
  > "revealed the radial extent of the small dust grains, ≈ 640 au (assuming a source distance of 160 pc)" (2. THE SOURCE: HD 97048) [from Doering et al. 2007]

## Processing

### Calibration

- pipeline or manual: Band 7 data recalibrated from raw data with 3c279 as flux calibrator (flux scaling not set in delivered data)  
  > "we recalibrated the raw data using 3c279 as the flux calibrator." (3. OBSERVATIONS)
- casa version: CASA 4.3  
  > "The data were self-calibrated using CASA version 4.3" (3. OBSERVATIONS)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Callisto (~302 GHz); 3c279 (~346 GHz), flux 8.86 ± 0.51 Jy bootstrapped from Band 3 monitoring via GetALMAFlux  
  > "This reported the spectral index for 3c279 as 0.73 ± 0.01 and the flux at Band 7 (346 GHz) as 8.86 ± 0.51 Jy." (3. OBSERVATIONS)
- flux scale uncertainty: ≈15% at 346 GHz (possibly underestimated)  
  > "we estimate a total error on the flux of the source at 346 GHz as closer to ≈15%, but this could be underestimated." (3. OBSERVATIONS)
- self calibration: continuum self-cal applied to continuum and lines; 20 s timescale; dynamic range increased ~20  
  > "We used a timescale of 20 s (corresponding to ≈ 3 times the integration step), and increased the dynamic range of the continuum data by a factor of ≈ 20." (3. OBSERVATIONS)

### Imaging

- task: CLEAN (CASA)  
  > "we display the continuum emission at 302 and 346 GHz imaged using the" (4.1.1. Continuum images)
- deconvolver: _not stated_
- weighting robust: Briggs robust = 0.5; also superuniform weighting for continuum  
  > "we present the resulting images using superuniform weighting." (4.1.1 Continuum images)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: interactive, channel by channel (CO)  
  > "Masking was done interactively on a channel-per channel basis." (4.2.1 Channel maps and line profile)
- multiscale scales: _not stated_
- continuum subtraction: uvcontsub in uv-plane for CO  
  > "continuum subtracted in the uv -plane using the CASA task uvcontsub" (4.2.1 Channel maps and line profile)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: CO: 0.69x0.44 arcsec (-23.2 deg)  
  > "The resulting synthesized beam is 0 ′′ .69×0 ′′ .44 (-23 ◦ .2)." (4.2.1 Channel maps and line profile)
- final rms: CO 18.1 mJy/beam per channel; velocity sampling 0.15 km/s  
  > "The resulting rms noise is 18.1 mJy/beam in the channels, and the peak signal-to-noise is 122." (4.2.1 Channel maps and line profile)

### Inherited from earlier work

- Intensity profile extraction by summing modulated Gaussians in visibility domain  
  > "we use the method recently proposed by Zhang et al. (2016)." (4.1.3 Continuum modeling) [from Zhang et al. (2016)]

### Not stated but needed to reproduce (our reading)

- Number of antennas/execution-specific details and exact line-free channel ranges for continuum
- Prior/likelihood details, MCMC chain length, burn-in and final best-fit Gaussian parameters
- Image size and cell size, clean thresholds, and masks for continuum
- Binning and deprojection procedure details beyond 10 kλ bins
- Flux scale for 302 GHz data in the delivered calibration

## Analysis recipe

1. **Image continuum**: CLEAN with Briggs (robust 0.5) and superuniform weighting at 302 and 346 GHz  
  > "In the bottom panels of Figure 1, we present" (4.1.1. Continuum images)
   - software: CASA
   - fitting: _not stated_
   - validation: Two independent frequencies used to assess low-level features  
  > "Having two essentially independent observations at different frequencies allowed us to assess the reality of low-level features in the data." (3. OBSERVATIONS)
2. **Fit disk geometry**: uvmodelfit with elliptical disk on continuum visibilities  
  > "the CASA task `uvmodelfit` [4], was used to fit the continuum visibilities" (4.1.1. Continuum images)
   - software: CASA uvmodelfit
   - fitting: _not stated_
   - validation: Two data sets fit independently gave almost identical parameters  
  > "The two measurement sets (at 302 and 346 GHz) were fit independently and resulted in almost identical disk parameters" (4.1.1 Continuum images)
3. **Dust mass estimate**: Optically thin M_dust = D^2 F/(kappa B(T))  
  > "For κ ν = 5 cm 2 g −1 and a dust temperature of 30 K (Beckwith et al. 1990; Andrews et al. 2011)" (4.1.1 Continuum images)
   - assumption: kappa = 5 cm2/g, T_dust = 30 K, D = 160 pc, optically thin  
  > "where D is the source distance (160 pc), κ ν is the dust mass opacity at a frequency" (4.1.1 Continuum images)
   - fitting: _not stated_
   - validation: _not stated_
4. **Fit radial intensity profile in visibility domain**: MCMC fit of sum of Gaussians modulated by cosines to binned, deprojected real visibilities, adding components until residuals stop improving  
  > "The addition of components is halted when an incremental improvement in the real residuals of the visibilities is found." (4.1.3 Continuum modeling)
   - software: pymc
   - parameter: 10 au radial grid; priors uniform within ≲500 au and ≲500 kλ; flux normal with 10% (302 GHz) and 15% (346 GHz) sigma  
  > "A radial grid of 10 au resolution was deemed sufficient to model the data." (4.1.3 Continuum modeling)
   - fitting: MCMC (pymc) with uniform priors  
  > "We assume all prior distributions for the fitted parameters, [ a i, σ i, ρ i ], are uniform" (4.1.3 Continuum modeling)
   - validation: Residuals in visibilities and imaged residuals; extra central component not significant  
  > "the improvement in fit was not significant, and higher spatial resolution data are needed" (4.1.3 Continuum modeling)
5. **CO imaging, source velocity and disk radius**: Continuum-subtracted CO cube, moment maps, uvmodelfit of integrated intensity as thin disk  
  > "we use the CASA task uvmodelfit, to model the integrated intensity of the line emission as arising from a geometrically thin disk" (4.2.2 The radius of the molecular disk)
   - software: CASA
   - parameter: moment 1 clipped at 5σ; moment 0 masks <3σ  
  > "The first moment map was generated using a conservative clip at a 5σ level" (4.2.2 The radius of the molecular disk)
   - fitting: _not stated_
   - validation: Line profile mirrored to confirm source velocity  
  > "The line profile has been mirrored and shifted (gray lines) to confirm the determination of the source velocity" (4.2.1 Channel maps and line profile)
6. **Constrain CO flaring angle**: Mirror positive/negative velocity channels and compare to projected layers of 30, 35, 40 deg opening angle at i=41 deg  
  > "we plot the channel maps mirroring the positive and negative channels at the same velocity" (4.2.3 Constraining the flaring angle of the CO-emitting layer)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.3: self-calibration, CLEAN imaging, uvmodelfit, uvcontsub  
  > "The data were self-calibrated using CASA version 4.3" (3. OBSERVATIONS)
- **ALMA Analysis Utilities GetALMAFlux** : bootstrap Band 3 flux of 3c279 to Band 7  
  > "flux to our Band 7 data (using the ALMA Analysis Utilities [1] task, `GetALMAFlux` [2] )." (3. OBSERVATIONS)
- **pymc** : MCMC fitting of intensity profile  
  > "Python module, pymc [6], was used (Patil et al. 2010)." (4.1.3. Continuum modeling)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Continuum flux density at 302 GHz | 2.14 | not stated | Jy | 1 | The total continuum flux density is 2.14 and 2.23 Jy at 302 and 346 GHz, respectively. |
| Continuum flux density at 346 GHz | 2.23 | ~15% | Jy | 1 | The total continuum flux density is 2.14 and 2.23 Jy at 302 and 346 GHz, respectively. |
| Spectral index | 0.30 | 0.03 | dimensionless | 1 | α = 0.30 ± 0.03, where F ν ∝ ν α |
| Total dust mass upper limit | 1.3e30 g (0.70 M_Jup) | not stated | g | 3 | this suggests a total dust mass of 1.3 × 10 30 g which corresponds to 0.70 M Jup |
| Dust disk radius, inclination, P.A. | 2.2 arcsec (350 au), 41 deg, 3 deg | not stated | arcsec/deg | 2 | a disk radius of 2 ′′ .2 (350 au), an inclination of 41 ◦, and a position angle (P.A.) of 3 ◦ |
| Continuum ring peaks / gaps | peaks ≈50,150,300 au; gaps ≈100, 250 au | not stated | au | 4 | show ring-like structures with peaks at ≈ 50, 150, and 300 au, with associated gaps at ≈ 100 and 250 au |
| CO disk radius | >4.7 arcsec (>750 au) | lower limit | arcsec | 5 | This gives a result for the radius of >4 ′′ .7 corresponding to > 750 au |
| Source velocity V_LSRK | 4.65 | 0.075 | km/s | 5 | V LSRK = 4.65 ± 0.075 km s −1 |
| CO emitting layer opening angle | 35 | 5 | deg | 6 | the opening angle of CO-emitting layer is ≈ 35 ± 5 ◦ |
| Outer unseen dust mass upper limit (350-750 au) | <2.5e28 | upper limit | g | 3 | gives a total unseen dust mass, M dust out < 2.5 × 10 28 g |

## Qualitative findings

- Mm-dust more centrally concentrated than CO gas and small grains, consistent with radial drift (dust ≈350 au vs gas ≳750 au).  
  > "the molecular gas and small (µm-sized) dust grains have a larger radial extent than the large (mm-sized) dust grains (750 au versus 350 au)" (5.1 On the transitional nature of HD 97048)
- CO emission lacks flux at -1.20 to 0.90 km/s, from foreground absorption and/or spatial filtering.  
  > "Line emission is suppressed or missing in velocity channels from -1.20 to 0.90 km s −1 inclusive." (4.2.1 Channel maps and line profile)

## Claim tuples

- H: Is HD 97048 a transitional disk with a mm-dust cavity and substructure? | E: Visibility-domain MCMC modeling of 302 and 346 GHz continuum | R: Decrement within ≈50 au; peaks ≈50,150,300 au; gaps ≈100, 250 au | F: Disk is transitional with multiple ring-like structures, to be confirmed at higher resolution | **partially**
- H: Is the gas disk more extended than the mm dust disk? | E: Compared CO 3-2 integrated intensity with 346 GHz continuum | R: CO to >750 au vs dust ≈350 au | F: Consistent with radial drift (lower limit on gas extent) | **supported**
- H: Is the CO emitting layer flared? | E: Mirrored channel maps compared with projected layers | R: Opening angle ≈35 ± 5 deg | F: HD 97048 is highly flared, consistent with Group I | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Visibility-domain modelling recovers substructure smoothed over in images given high S/N  
  > "We emphasize here that the recovery of this substructure is only possible due to the high signal-to-noise of the data (≳ 1000) and the direct modeling of the visibility data." (4.1.3 Continuum modeling)
- Alternative: CO freeze-out in midplane as alternative to drift for outer gas morphology; not clearly seen  
  > "However, we do not see a clear decrement in emission between the front and back side of the disk" (4.2.2 The radius of the molecular disk)
- How they decided it was enough: _not stated_
- Limitation (authors): 346 GHz flux calibration uncertain; spectral index/dust mass not robust.  
  > "it is possible that we have underestimated the error on the flux at this frequency." (4.1.1 Continuum images)
- Limitation (authors): Missing CO emission means only lower limits on gas disk extent.  
  > "it is only possible to determine a lower limit to the spatial extent of the molecular disk." (4.2.2 The radius of the molecular disk)
- Caveat (inferred, ours): Substructure is inferred from ~0.5 arcsec data with a flexible Gaussian-cosine model; model dependence and component count are poorly tested
- Caveat (inferred, ours): Cavity and ring significance not quantified with uncertainties
- Caveat (inferred, ours): CO analysis hampered by cloud contamination
- Caveat (inferred, ours): Dust temperature/opacity assumptions simple

## Reproducibility

- Data public (paper): Data cited as ADS/JAO.ALMA#2011.0.00863.S  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2011.0.00863.S." (5.4 Future outlook)
- Products in archive: _not stated_
- Missing: Gaussian-model best-fit parameters and MCMC settings
- Missing: Line-free channel selection
- Missing: Image sizes/cell sizes/clean thresholds
- Data volume (inferred): ~10-30 GB raw (two Cycle 0 executions)
- Score (inferred): 3/5, Single public Cycle 0 dataset and clear recipe, but MCMC settings, masks and imaging parameters are missing.
- Rediscovery candidate: yes, Public data, numeric results (flux, geometry, V_LSRK, CO radius), mostly reproducible recipe.

## Links

- Method: Zhang et al. 2016 (Visibility-domain intensity profile fitting method)
- Companion: van der Plas et al. 2016 (Later ALMA Cycle 2 data resolving the cavity)
- Companion: Ginski et al. 2016 (SPHERE scattered light rings in HD 97048)
- Related: Herschel GASPS
- Related: Herschel DIGIT

## Checks

```json
{
 "quotes": 66,
 "quotes_ok": 66,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 10,
 "numeric_problems": 0,
 "fill": {
  "facts": 75,
  "stated": 50,
  "rate": 0.667
 },
 "evidence_ok": true
}
```
