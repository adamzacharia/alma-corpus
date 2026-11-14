# ALMA observations of anisotropic dust mass loss in the inner circumstellar environment of the red supergiant VY Canis Majoris

`2015A&A...573L...1O` | Astronomy and Astrophysics 2015 | first author: O'Gorman, E. | arXiv: 1410.1622 | DOI: 10.1051/0004-6361/201425101

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: evolved_stars
- Question: What are the properties and distribution of dust in the inner circumstellar envelope of the red supergiant VY CMa, and what does it imply for mass-loss mechanisms?  
  > "In this Letter we report the results of a sub-100 mas study of this region using ALMA Science Verification data." (1 Introduction)
- Target **VY Canis Majoris**: coordinates _not stated_; z/distance 1.2 kpc  
  > "Using a distance of 1.2 kpc to VY CMa, this angular distance corresponds to 400 AU" (2 Observations and results); distance from not stated (relative proximity cited to Zhang et al. 2012)  
  > "Using a distance of 1.2 kpc to VY CMa, this angular distance corresponds to 400 AU" (2 Observations and results)

## Data provenance

- ALMA projects: 2011.0.00011.SV
- bands: _not stated_
- frequencies and spectral setup: 321 GHz, 325 GHz, 658 GHz observed; 1.74 GHz line-free continuum at 321 GHz and 0.4 GHz at 658 GHz used  
  > "we used a total of $1.74$ GHz line free continuum channels around 321 GHz and $0.4$ GHz centered on 658 GHz." (2 Observations and results)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 14 m to 2.7 km, 16 to 20 antennas  
  > "using 16 to 20 antennas of the main array with projected baselines ranging from 14 m to 2.7 km" (2 Observations and results)
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: 2013 16-19 August  
  > "as part of the ALMA Science Verification process on 2013 16-19 August" (2 Observations and results)
- pi or archival as stated: _not stated_
- Other facility **HST/WFPC2**: F1042M image from 1999 March 22 for comparison  
  > "an *HST*/WFPC2 exposure of VY CMa taken with the F1042M filter on 1999 March 22" (3.1 Comparison with HST)
- External data: Single-dish and SMA (sub-)mm flux density compilations  
  > "using the compilations of (cite: knapp_1993) and (cite: ladjal_2010)" (Appendix: Comparison with other (sub-)mm observations) [from Knapp et al. 1993; Ladjal et al. 2010; Shinnaga 2004; Muller 2007; Kaminski 2013]
- External data: Stellar radius 1420 Rsun and Teff 3490 K  
  > "we have assumed a stellar radius of $R_{\star}= 1420\,R_{\odot}$ (6.84 AU or 5.7 mas) and an effective temperature $T_{\mathrm{eff}}= 3490\,$K (cite: wittkowski_2012)" (Appendix: Stellar flux density contribution) [from Wittkowski et al. 2012]
- Simulation/model as data: Harper et al. (2001) semi-empirical Betelgeuse atmosphere model scaled to VY CMa for stellar contribution  
  > "we scaled the (cite: harper_2001) semi-empirical model for the M2 Iab RSG Betelgeuse (without the silicate dust) to the angular diameter of VY CMa." (Appendix: Stellar flux density contribution)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: ±15% absolute flux calibration  
  > "based on the $\pm 15\%$ uncertainty of the absolute flux calibration (R+14)" (2 Observations and results)
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
- smoothing: 658 GHz data convolved with 321 GHz synthesized beam and regridded for spectral index map  
  > "after convolving the 658 GHz data with the synthesized beam from the 321 GHz image, and regridding the convolved image to match the pixel scale" (2 Observations and results)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Observation details and data processing  
  > "Details of the observations and data processing are provided in (cite: richards_2014), hereafter R+14." (2 Observations and results) [from (cite: richards_2014)]

### Not stated but needed to reproduce (our reading)

- CASA version, calibration and imaging parameters (weighting, robust, cell, clean settings)
- Line-free channel selection
- Phase offset corrections beyond the quoted shift, and the beam sizes (in table not provided in the text)
- Dust temperature structure and masking used for the resolved-out flux estimate

## Analysis recipe

1. **Align 658 GHz to 321 GHz image**: 2-D cross-correlation over range of shifts; maximum correlation gives offset  
  > "we shifted the 658 GHz image relative the 321 GHz image and computed a 2-D cross-correlation function for a range of shifts." (2 Observations and results)
   - fitting: _not stated_
   - validation: Similar to correction found by R+14  
  > "similar to the correction found by R+14 when aligning the peak position of the second brightest continuum component" (2 Observations and results)
2. **Fit continuum components**: 2-D elliptical Gaussian fits, deconvolved sizes and fluxes  
  > "We fit 2-D elliptical Gaussian components to the two main continuum features" (2 Observations and results)
   - fitting: _not stated_
   - validation: _not stated_
3. **Spectral index map**: Ratio of beam-matched 658 and 321 GHz images, pixels above 6 sigma  
  > "All data below the $6\sigma _{\mathrm{rms}}$ noise level in the convolved 658 GHz image have been omitted" (2 Observations and results)
   - fitting: _not stated_
   - validation: _not stated_
4. **Dust mass and optical depth**: Optically thin Rayleigh-Jeans dust mass equation with stellar contribution subtracted; temperature from radiative heating  
  > "Equation [\[eq1\]](#eq1) can be re-arranged to find the total mass of dust in each of the two main continuum components." (3.2 Properties of the dust)
   - assumption: a_g = 0.2 micron, rho_g = 3.5 g cm^-3, Q = 5.65e-4 (nu/274.6 GHz)^0.7, Tstar = 3490 K  
  > "$a_{g} = 0.2\,\mu$m and $\rho _{g}=3.5\,$g cm$^{-3}$" (3.2 Properties of the dust)
   - fitting: _not stated_
   - validation: _not stated_
5. **Mass-loss rate from resolved-out emission**: Estimate resolved-out flux vs single-dish, dust mass over 8 arcsec shell at 200 K, divided by timescale  
  > "We assume the dust to be extended over the $\sim8\ensuremath{''}$ size of the *HST* image" (3.3 Dust mass-loss history and mechanisms)
   - assumption: Vd ~60 km/s, T = 200 K  
  > "We assume an average temperature of 200 K throughout the shell." (3.3 Dust mass-loss history and mechanisms)
   - fitting: _not stated_
   - validation: _not stated_

## Software


## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Spectral index of C | 1.9 | systematic ~0.22 | dimensionless | 3 | The middle region of the main continuum component C has a spectral index of $\alpha \sim 1.9$ |
| Spectral index of VY | 2.7 | not stated | dimensionless | 3 | has a spectral index of $\alpha \sim 2.7$ |
| Dust mass of C at 321 GHz | 2.5e-4 | not stated | Msun | 4 | We then derive dust masses of $2.5\times 10^{-4}\,M_{\odot}$ at 321 GHz |
| Dust mass-loss rate | 5e-6 (Vd/60 km/s) | not stated | Msun/yr | 5 | a dust mass-loss rate of $5\times10^{-6}(V_{\rm{d}}/60~$km s$^{-1})\,$M$_{\odot}\,$yr$^{-1}$ |
| Component C offset from star | 334 mas SE (400 AU) | not stated | mas | 2 | is 334 mas SE of the star in the plane of the sky |

## Qualitative findings

- Brightest continuum component C is offset from the star and is possibly optically thick/cool; thermal molecular emission avoids it  
  > "we find that the thermal molecular emission lines from the ALMA data avoids the C component" (3.2 Properties of the dust)

## Claim tuples

- H: Is dust mass loss from VY CMa isotropic? | E: Sub-100 mas ALMA continuum imaging at 321 and 658 GHz | R: Two resolved components and N-NE extension; C is 400 AU SE of star | F: Dust mass loss is anisotropic with clumps; >17% of dust is in clumps | **supported**
- H: Is convection alone driving the mass loss? | E: Compare the persistent directed clumps with expectations | R: Continuous directed dust loss over 30-50 yr | F: A localized, stable (possibly magnetic) mechanism is needed | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Dust mass of C is a lower limit as it may not be optically thin; much flux is resolved out  
  > "The main component C may not be fully optically thin at both frequencies and so its dust mass estimates will be lower limits." (3.2 Properties of the dust)
- Caveat (inferred, ours): Dust mass depends on assumed emissivity law and grain properties
- Caveat (inferred, ours): Magnetic mass-loss interpretation is speculative
- Caveat (inferred, ours): Resolved-out flux estimate assumes same spectral index at all scales

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Imaging parameters and calibrated products
- Missing: Beam and rms values (tables not in text)
- Data volume (inferred): tens of GB
- Score (inferred): 3/5, Public SV data and simple analysis, but processing is deferred to R+14 and imaging settings are absent.
- Rediscovery candidate: no, Processing details are inherited from R+14 and not given here.

## Links

- Method: Richards et al. 2014 (ALMA SV observation and data processing details)
- Companion: Richards et al. 2014 (Maser and continuum analysis of the same data)
- Related: ALMA Science Verification

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
  "facts": 67,
  "stated": 23,
  "rate": 0.343
 },
 "evidence_ok": true
}
```
