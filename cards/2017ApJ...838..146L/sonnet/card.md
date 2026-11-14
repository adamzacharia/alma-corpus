# ALMA Observations of the Interaction of a Radio Jet with Molecular Gas in Minkowski's Object

`2017ApJ...838..146L` | The Astrophysical Journal 2017 | first author: Lacy, Mark | arXiv: 1703.03006 | DOI: 10.3847/1538-4357/aa65d7

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, agn_and_quasars
- Question: Is there molecular gas in Minkowski's Object, and do its properties support jet-induced star formation (positive AGN feedback)?  
  > "These observations are the first to detect molecular gas in Minkowski’s Object." (abstract)
- Target **Minkowski's Object**: coordinates 01:25:47.40 -01:22:19.0 (J2000, integrated CO region)  
  > "a redshift of $z=0.0189$ for Minkowski’s Object, at which the luminosity distance is 82Mpc and 1-arcsec corresponds to 381pc." (Introduction); z/distance z=0.0189; D_L=82 Mpc  
  > "a redshift of $z=0.0189$ for Minkowski’s Object, at which the luminosity distance is 82Mpc and 1-arcsec corresponds to 381pc." (Introduction); distance from assumed cosmology H0=70, OmegaL=0.7, OmegaM=0.3  
  > "a redshift of $z=0.0189$ for Minkowski’s Object, at which the luminosity distance is 82Mpc and 1-arcsec corresponds to 381pc." (Introduction)

## Data provenance

- ALMA projects: 2015.1.00570.S
- bands: CO(1-0) at 113.15 GHz plus continuum windows at 99.2, 101.1, 111.2 GHz (Band 3)  
  > "one centered on the expected velocity of the CO(1-0) emission line at 113.15 GHz, and three (centered at 99.2, 101.1 and 111.2 GHz) to provide continuum." (2.1 ALMA Observations)
- frequencies and spectral setup: 4 spectral windows, 1875 MHz each; 3.0 km/s spectral resolution  
  > "Four spectral windows were observed with a bandwidth of 1875 MHz each" (2.1 ALMA Observations); "The spectral resolution is 3.0 km s$^{-1}$" (2.1 ALMA Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: CO beam 3.2" x 2.4", PA 275 deg; continuum 3.5" x 2.6"  
  > "The synthesized beam size in the CO(1-0) image is $3.2^{\prime \prime} \times 2.4^{\prime \prime}$ at a position angle of 275$^{\circ}$" (2.1 ALMA Observations)
- max recoverable scale: ≈25"  
  > "the maximum recoverable scale (MRS) in our observations is $\approx 25^{\prime \prime}$" (4.4 Molecular gas content)
- sensitivity: CO: 0.5 mJy/beam per 3 km/s channel; continuum: 60 uJy/beam  
  > "the rms noise in a single 3kms $^{-1}$ channel is 0.5 mJy beam$^{-1}$" (2.1 ALMA Observations); "an rms noise of 60 $\mu$Jy beam$^{-1}$" (2.1 ALMA Observations)
- time on source: 173 minutes  
  > "The total time on source was 173 minutes." (2.1 ALMA Observations)
- observing dates: 2016 January 2 and 3, four executions  
  > "observed over four executions of a single scheduling block on 2016 January 2 and 2016 January 3." (2.1 ALMA Observations)
- pi or archival as stated: _not stated_
- Line: CO 1-0 (115.27 GHz)
- Other facility **VLA (AV0102)**: 1.5 GHz continuum, B and C configs  
  > "We retrieved VLA continuum data (project AV0102) observed in the B and C configurations" (2.2 Archival VLA data)
- Other facility **VLA HI (AM789, AB1159)**: HI cube, tapered, 15.6"x15.0" beam  
  > "we applied a $uv$-plane taper that resulted in a beam of $15.6^{\prime \prime} \times 15.0^{\prime \prime}$" (2.2 Archival VLA data)
- External data: H-alpha image used for SFR surface density  
  > "by scaling the CO(1-0) image and the H$\alpha$ image (from C06)" (5.1 Star formation rate and gas depletion time) [from Croft et al. 2006 (cite: 2006ApJ...647.1040C)]
- External data: Total SFR 0.47 Msun/yr  
  > "we assume a SFR of 0.47 M$_{\odot}$ yr$^{-1}$ (Salomé et al. 2015)" (5.1 Star formation rate and gas depletion time) [from Salomé et al. 2015]
- External data: HI gas mass 4.9e8 Msun  
  > "C06 give the atomic gas mass in H`I` as $4.9\times 10^8 M_{\odot}$" (4.4 Molecular gas content) [from Croft et al. 2006]
- Simulation/model as data: CASA ALMA simulator with uniform 16" disk model to estimate flux loss (factor 1.4)  
  > "modeled the emission as a uniform disk of diameter 16$^{\prime \prime}$ and used the ALMA simulator in CASA" (4.4 Molecular gas content)

## Processing

### Calibration

- pipeline or manual: ALMA pipeline  
  > "The data were calibrated using the ALMA pipeline" (2.1 ALMA Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Uranus  
  > "with Uranus being observed as the flux density calibrator" (2.1 ALMA Observations)
- flux scale uncertainty: ≈5%  
  > "this should result in flux densities accurate to $\approx 5$%" (2.1 ALMA Observations)
- self calibration: _not stated_

### Imaging

- task: CASA clean, MFS with two Taylor terms (continuum)  
  > "We formed the continuum image using the multifrequency synthesis mode of the clean task, employing two Taylor terms." (2.1 ALMA Observations)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "we used natural weighting during imaging" (2.1 ALMA Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: uvcontsub using line-free channels  
  > "we used the CASA task uvcontsub to model and subtract the continuum emission using the line-free channels" (2.1 ALMA Observations)
- line free channels: _not stated_
- primary beam correction: applied to continuum for spectral index map only; not applied to CO  
  > "As the CO emission is completely contained within the 95% power point of the primary beam, no primary beam correction was applied to the CO images." (2.1 ALMA Observations)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: 60 uJy/beam continuum; 0.5 mJy/beam per channel CO  
  > "an rms noise of 60 $\mu$Jy beam$^{-1}$" (2.1 ALMA Observations)

### Inherited from earlier work

- alpha_CO prescription from Narayanan et al.  
  > "so we also use the following prescription of Narayanan et al. (2012)" (4.4 Molecular gas content) [from Narayanan et al. 2012 (cite: 2012MNRAS.426.1178N)]
- CO luminosity conversion equation  
  > "We convert the CO line flux to a luminosity $L_{\mathrm{CO}}$ via Equation [\[eq:Lco\]](#eq:Lco) below (Obreschkow et al. 2009)" (4.4 Molecular gas content) [from Obreschkow et al. 2009]

### Not stated but needed to reproduce (our reading)

- Line-free channel ranges for uvcontsub
- Clean threshold, masking, cell and image size
- Pipeline/CASA version
- Details of the ALMA simulator setup (configuration, noise)
- Method for moment map clipping
- How pixel-level Sigma_SFR was derived from H-alpha (extinction, calibration)
- Spectral-fitting method for clump line parameters

## Analysis recipe

1. **Image continuum and CO cube**: CASA clean MFS (2 Taylor terms) for continuum, natural weighting; uvcontsub for CO cube  
  > "We formed the continuum image using the multifrequency synthesis mode of the clean task, employing two Taylor terms." (2.1 ALMA Observations)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Spectral index map 1.5-106 GHz**: convolve ALMA image to VLA resolution and compute per-pixel spectral index  
  > "made by convolving the ALMA image to the slightly lower resolution of the VLA image and then calculating the per-pixel spectral index" (3.2 Continuum emission)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
3. **Measure CO flux and correct for resolved-out emission**: Integrate over 16" aperture, 5535-5586 km/s; simulate spatial filtering to derive factor 1.4  
  > "The simulation showed that we may be underestimating the integrated CO flux density by as much as a factor of 1.4." (4.4 Molecular gas content)
   - software: CASA
   - assumption: emission is a uniform disk of 16" diameter; 20% uncertainty  
  > "We therefore scale our measured 289 mJy km s$^{-1}$ flux by this amount and assume a 20% uncertainty" (4.4 Molecular gas content)
   - fitting: _not stated_
   - validation: ALMA simulator test  
  > "To test whether we are likely to have underestimated the integrated CO flux density" (4.4 Molecular gas content)
4. **Derive L_CO and H2 mass**: Obreschkow L_CO formula; M_H2 = alpha_CO * L_CO for alpha_CO=4.6 and 27  
  > "This results in a conversion factor of $\alpha_{\rm CO} = 27$ M$_{\odot}{\rm (K~km~s^{-1}~pc^2)^{-1}}$" (4.4 Molecular gas content)
   - assumption: Z'=0.5, source area 201 arcsec^2 (29.2 kpc^2)  
  > "We assume $Z^{\prime}=0.5$ based on the ionized gas metallicity" (4.4 Molecular gas content)
   - fitting: _not stated_
   - validation: compared with HI mass and Fragile et al. 2004 predictions  
  > "so $f_{\rm mol}$ is in the range 6-36%" (4.4 Molecular gas content)
5. **Star formation law and depletion time**: Scale CO and H-alpha images to Sigma_H2 and Sigma_SFR; depletion time = ratio; compare with Kennicutt-Schmidt  
  > "calculated simply as the ratio of gas surface density divided by star formation rate surface density" (5.1 Star formation rate and gas depletion time)
   - assumption: normal IMF  
  > "assume a normal initial mass function (IMF) for star formation in Minkowski’s Object" (5.1 Star formation rate and gas depletion time)
   - fitting: _not stated_
   - validation: _not stated_
6. **Minimum-energy pressure in interaction region**: standard equipartition formulation from VLA 1.5 GHz  
  > "Using these equations we find a minimum pressure of $1.3 \times 10^{-12}$ Pa." (5.2 Physical conditions in the ISM)
   - assumption: kappa=100, filling factor 1, path length 4.0 kpc, phi=45 deg, alpha=-0.8  
  > "$\kappa$ is the ratio of energy in heavy particles to that in electrons (assumed to be 100)" (5.2 Physical conditions in the ISM)
   - fitting: _not stated_
   - validation: compared with X-ray gas pressure of Bogdan et al. 2011  
  > "This is comparable to the estimate from the X-ray gas in Abell 194 by Bogdán et al. (2011), $1.7\times 10^{-12}$ Pa" (5.2 Physical conditions in the ISM)

## Software

- **CASA** : calibration/imaging, clean, uvcontsub, ALMA simulator  
  > "imaged using the Common Astronomy Software Applications (CASA) package" (2.1 ALMA Observations)
- **Astropy** : acknowledged as used  
  > "This research made use of Astropy, a community-developed core Python package for Astronomy" (Acknowledgments)
- **Montage** : acknowledged as used  
  > "This research made use of Montage." (Acknowledgments)
- **APLpy** : plotting  
  > "This research made use of APLpy, an open-source plotting package for Python" (Acknowledgments)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Integrated CO(1-0) flux (corrected) | 405 | 81 | mJy km/s | 3 | Integrated &01:25:47.40 -01:22:19.0 &16 & 5556$\pm$1 & 26$\pm$3 & $405\pm 81$ & 3-18 |
| M_H2 (alpha_CO=4.6) | 3.0e7 | not stated | Msun | 4 | $M_{\rm H_2} =3.0 \times 10^7~M_{\odot}$, 6% of the H`I` gas mass |
| M_H2 (alpha_CO=27) | 1.8e8 | not stated | Msun | 4 | $M_{\rm H_2} =1.8 \times 10^8~M_{\odot}$, 36% of the H`I` mass |
| Integrated CO line FWHM | 26 | 3 | km/s | 3 | 5556$\pm$1 & 26$\pm$3 |
| Minimum pressure | 1.3e-12 | not stated | Pa | 6 | we find a minimum pressure of $1.3 \times 10^{-12}$ Pa |
| Background source 106 GHz peak flux | 118 | 8 | uJy | 0 | $S_{\rm 106\,GHz}=118 \pm 8 \mu{\rm Jy}$ |
| Average gas depletion time | 0.6-3.8e8 | not stated | yr | 5 | this leads to a short average gas depletion timescale $\sim 0.6-3.8\times 10^8$ yr |

## Qualitative findings

- Spectral index steepens from about -0.6 at the jet base to -0.8/-0.9 near the interaction region.  
  > "the spectral index of the jet steepens from $\approx -0.6$ near the base of the jet to $\approx -0.8$ to $-0.9$" (3.2 Continuum emission)

## Claim tuples

- H: Does Minkowski's Object contain molecular gas? | E: ALMA CO(1-0) imaging | R: CO detected in clumps A-D, integrated flux 405 mJy km/s | F: First molecular gas detection, M_H2 3e7-1.8e8 Msun | **supported**
- H: Is star formation jet-induced and more efficient upstream? | E: Compare Sigma_H2-Sigma_SFR, depletion times, velocity dispersions | R: Above Kennicutt-Schmidt by ~10 in main region; shorter depletion upstream | F: Consistent with jet-triggered star formation | **supported**
- H: Does the jet re-accelerate electrons near the CO clumps? | E: Spectral index map | R: Flattening to -0.77 near clump D | F: Marginal evidence for re-acceleration | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Low-metallicity dwarf, so MW alpha_CO may be inappropriate; two values bracket the mass  
  > "may not be appropriate for a low metallicity dwarf galaxy" (4.4 Molecular gas content)
- Alternative: Thermal origin of 106 GHz continuum rejected as SFR too low  
  > "The star formation rate in Minkowski’s Object is much too low for the continuum emission at 106 GHz to arise from thermal processes." (3.2 Continuum emission)
- How they decided it was enough: _not stated_
- Limitation (authors): Flux may be resolved out on large scales; low S/N for dispersion differences  
  > "any emission present on even larger angular scales will be resolved out in our ALMA data" (4.4 Molecular gas content); "Although the signal-to-noise is not very high" (4.3 Molecular gas velocity structure)
- Caveat (inferred, ours): alpha_CO uncertain by factor ~6; conclusions depend on it
- Caveat (inferred, ours): Flux correction factor 1.4 from a simple uniform-disk model
- Caveat (inferred, ours): Top-heavy IMF possibility affects SFR
- Caveat (inferred, ours): Velocity dispersion difference marginal

## Reproducibility

- Data public (paper): ALMA data cited by project code; VLA data retrieved from archive  
  > "We extracted these data from the archive" (2.2 Archival VLA data)
- Products in archive: _not stated_
- Missing: Clean parameters and line-free channels
- Missing: CASA version
- Missing: Simulator setup
- Missing: H-alpha SFR calibration
- Data volume (inferred): ~10-50 GB (four executions, Band 3, 4 spws)
- Score (inferred): 3/5, Data public and main numbers clear, but many imaging parameters are unstated.
- Rediscovery candidate: yes, Public ALMA data, simple flux and mass derivation with numeric results.

## Links

- Method: Narayanan et al. 2012 (alpha_CO prescription)
- Method: Obreschkow et al. 2009 (L_CO formula)
- Companion: Croft et al. 2006 (C06) (Previous definitive study of Minkowski's Object)
- Companion: Fragile et al. 2017 (Companion numerical simulations)
- Related: VLA AV0102
- Related: VLA AM789
- Related: VLA AB1159

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
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 80,
  "stated": 49,
  "rate": 0.613
 },
 "evidence_ok": true
}
```
