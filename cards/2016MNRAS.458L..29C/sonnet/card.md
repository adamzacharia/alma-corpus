# A ring-like concentration of mm-sized particles in Sz 91

`2016MNRAS.458L..29C` | Monthly Notices of the Royal Astronomical Society 2016 | first author: Canovas, H. | arXiv: 1601.06801 | DOI: 10.1093/mnrasl/slw006

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks
- Question: What is the radial distribution of mm-sized dust grains versus 12CO gas in the transition disc Sz 91, and is it consistent with planet-disc interaction models?  
  > "the continuum emission at 870$\mu$m, which is dominated by emission from large dust grains, is localized in an optically thin narrow ring." (abstract)
- Target **Sz 91**: coordinates ALMA phase centre RA 16h07m11.56s, Dec -39d03m47.82s (J2000)  
  > "is located in the Lupus III star forming region at a distance of 200 pc (cite: 2008ApJS..177..551M)" (Introduction); "from the ALMA phase centre ($\alpha_{2000} = 16^{\mathrm{h}}07^{\mathrm{m}}11^{\mathrm{s}}.56$ and $\delta_{2000} = -39{\ensuremath{^\circ}}03.47\ensuremath{'}.82\ensuremath{''}$)" (Continuum); z/distance 200 pc  
  > "is located in the Lupus III star forming region at a distance of 200 pc (cite: 2008ApJS..177..551M)" (Introduction); "from the ALMA phase centre ($\alpha_{2000} = 16^{\mathrm{h}}07^{\mathrm{m}}11^{\mathrm{s}}.56$ and $\delta_{2000} = -39{\ensuremath{^\circ}}03.47\ensuremath{'}.82\ensuremath{''}$)" (Continuum); distance from Merin et al. 2008 (2008ApJS..177..551M)  
  > "is located in the Lupus III star forming region at a distance of 200 pc (cite: 2008ApJS..177..551M)" (Introduction); "from the ALMA phase centre ($\alpha_{2000} = 16^{\mathrm{h}}07^{\mathrm{m}}11^{\mathrm{s}}.56$ and $\delta_{2000} = -39{\ensuremath{^\circ}}03.47\ensuremath{'}.82\ensuremath{''}$)" (Continuum)

## Data provenance

- ALMA projects: 2013.1.00663.S, 2011.0.00733.S
- bands: Band 6 and Band 7  
  > "Sz 91 was observed with ALMA in band-6 and band-7 with two different configurations during Cycle-2" (Observations)
- frequencies and spectral setup: B6: 2 GHz continuum at 231.6 GHz plus three 58.6 MHz windows (61.035 kHz channels); B7: continuum at 332.5 and 343.7 GHz plus two 58.6 MHz windows  
  > "one continuum spectral window with a total bandwidth of 2 GHz centred at 231.6 GHz and three spectral windows with bandwidths of 58.6 MHz and channel widths of 61.035 KHz." (Observations); "two continuum spectral windows with a total bandwidth of 2 GHz centred at 332.5 and 343.7 GHz" (Observations)
- continuum bandwidth: _not stated_
- arrays: 12-m antennas: 40 (Band 6), 42 (Band 7)  
  > "The Band 7 observations were performed with 42 (12-m) antennas" (Observations)
- configurations: _not stated_
- baselines: B6: 23.3-558.2 m; B7: 15.1-1574.4 m  
  > "baselines ranging from 15.1 to 1574.4 m (17.3 to 1789.1 $\mathrm{k\lambda}$)" (Observations)
- angular resolution: Continuum beam 0.21x0.15 arcsec (42x30 au), PA 79.9 deg; 12CO beam 0.60x0.57 arcsec  
  > "beam size of 0.21 arcsec $\times$ 0.15 arcsec ($42\times30$ au) and position angle (PA) of $79.9\ensuremath{^\circ}$" (Observations)
- max recoverable scale: _not stated_
- sensitivity: continuum median rms 0.95 mJy/beam; 12CO line-free rms 20.12 mJy/beam  
  > "The median rms in the continuum is 0.95 $\mbox{${\rm mJy\,beam}^{-1}$}$" (Observations)
- time on source: 207 s (Band 6), 1430 s (Band 7)  
  > "amounting to a total exposure time for the science observations of 207 and 1430 s in Band 6 and Band 7, respectively" (Observations)
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: 12CO 3-2 (345.8 GHz)
- External data: Distance of 200 pc  
  > "Using a distance of 200 pc (cite: 2008ApJS..177..551M)" (Continuum) [from 2008ApJS..177..551M]
- External data: Dust mass–flux relation calibrated from literature  
  > "linear relations derived by (cite: 2005ApJ...631.1134A; 2007ApJ...671.1800A) and calibrated by (cite: 2008ApJ...686L.115C)" (Continuum) [from 2005ApJ...631.1134A; 2007ApJ...671.1800A; 2008ApJ...686L.115C]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Titan (Band 6), Ceres (Band 7)  
  > "Titan and Ceres were observed to perform flux calibration in Band 6 and Band 7, respectively." (Observations)
- flux scale uncertainty: ~10%  
  > "The uncertainty associated with the flux calibration is $\sim10\%$" (Observations)
- self calibration: One round, marginal S/N increase, no more  
  > "We applied one round of self-calibration finding a marginal increment in S/N, so no more iterations were applied." (Observations)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: Briggs for 12CO, natural for continuum (robust not given)  
  > "using Briggs and natural weighting for the $\mbox{$^{12}{\rm CO}$}$ and continuum, respectively" (Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: Fit and subtract continuum using line-free channels  
  > "The line-free channels were used to fit and subtract the continuum to the emission-line bearing channels." (Observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: Continuum 0.21x0.15 arcsec; 12CO 0.60x0.57 arcsec  
  > "The beam size in the $\mbox{$^{12}{\rm CO}$}$ data is 0.60 arcsec $\times$ 0.57 arcsec" (Observations)
- final rms: Continuum 0.95 mJy/beam; 12CO 20.12 mJy/beam  
  > "with a median rms in the line-free channels of $20.12$ $\mbox{${\rm mJy\,beam}^{-1}$}$" (Observations)

### Not stated but needed to reproduce (our reading)

- Briggs robust value
- line-free channel ranges
- which channels were flagged
- self-calibration solint and reference data
- cell and image size, clean threshold and masks
- uvfit ring model functional form and parameters
- MCMC sampler, priors and number of steps
- CASA version
- Band 6 results are not used so no analysis details given
- which of the two projects (2011.0.00733.S or 2013.1.00663.S) is used beyond the Band 7 data

## Analysis recipe

1. **Process visibilities and image continuum and 12CO**: CASA calibration/imaging, continuum subtraction, CLEAN with natural (continuum) and Briggs (CO) weighting, one round self-cal  
  > "We used CASA (cite: 2007ASPC..376..127M) to process the visibilities." (Observations)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Fit ring geometry to continuum visibilities**: Fit ring profile to visibilities with uvfit  
  > "We derive the geometry of the continuum disc by fitting a ring profile to the continuum visibilities using *uvfit*/." (Continuum)
   - software: uvfit
   - fitting: _not stated_
   - validation: _not stated_
3. **Estimate dust mass**: Linear flux-mass relation at 0.86 mm with d=200 pc, 10% flux and distance uncertainties  
  > "we derive a total mass of $23\pm6\,M_\mathrm{Earth}$" (Continuum)
   - assumption: ISM grain size distribution with power-law index p = -3.5; optically thin emission; d = 200 pc  
  > "the grain size distribution follows an interstellar medium (ISM) distribution with power law index $p = -3.5$" (Continuum)
   - fitting: _not stated_
   - validation: Compared with previous mass estimates  
  > "in agreement with previous estimates for the disc’s mass in large grains" (Continuum)
4. **Make 12CO moment maps**: Moment-0 and Moment-1 from >3 sigma channels, pixels below 2.5x median rms excluded, Gaussian fitted along spectral axis  
  > "A Gaussian profile was fitted along the spectral axis at each spatial position to ensure that the full $\mbox{$^{12}{\rm CO}$}$ profile was included at each location." (12CO Moments)
   - fitting: _not stated_
   - validation: _not stated_
5. **Fit radial surface brightness profile of the ring**: Fit Gaussian, hat-like and r^-1 power-law profiles along the major axis, convolved with 0.16 arcsec FWHM Gaussian; MCMC  
  > "We then perform a Monte Carlo Markov Chain (MCMC) exploration to identify the best fit to the observations." (Surface brightness profile of mm emission)
   - parameter: Beam FWHM 0.16 arcsec along major axis  
  > "full width at half-maximum FWHM = 0.16 arcsec" (Surface brightness profile of mm emission)
   - fitting: MCMC; reduced chi2 compared among profiles  
  > "We vary the widths and central positions of these profiles" (Surface brightness profile of mm emission)
   - validation: Same result using averaging in ellipsoids with disc inclination and PA  
  > "Averaging the emission in ellipsoids which have the same inclination and PA as the disc provides the same results." (Surface brightness profile of mm emission)

## Software

- **CASA** : Visibility processing, imaging  
  > "We used CASA (cite: 2007ASPC..376..127M) to process the visibilities." (Observations)
- **uvfit** : Fit ring profile to continuum visibilities  
  > "fitting a ring profile to the continuum visibilities using *uvfit*/." (Continuum)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Integrated continuum flux (S/N>3) | 40.15 | 0.95 | mJy | 1 | $\mathrm{F_{1.3\mathrm{mm}}} = 40.15 \pm 0.95$ mJy |
| Total continuum flux from uvfit | 42.43 | 0.95 | mJy | 2 | a total flux of $42.43 \pm 0.95$ mJy |
| Disc inclination | 51.7 | 0.4 | deg | 2 | inclination $i = 51.7\pm0.4\ensuremath{^\circ}$ |
| Disc position angle | 17.4 | 0.4 | deg | 2 | We derive a PA = 17.4$\pm0.4\ensuremath{^\circ}$ |
| Dust mass | 23 | 6 | M_Earth | 3 | we derive a total mass of $23\pm6\,M_\mathrm{Earth}$ |
| 12CO Moment-0 integrated flux | 4.932 | 0.023 | Jy km/s | 4 | its integrated flux is $4.932\pm0.023$ Jy $\mbox{${\rm km\,s}^{-1}$}$ |
| Gaussian ring centre | 110.5 | 0.3 | au | 5 | a Gaussian profile centred at $110.5\pm0.3$ au and with $1\sigma$ width of $22.2\pm0.5$ au |
| Gaussian ring 1-sigma width | 22.2 | 0.5 | au | 5 | a Gaussian profile centred at $110.5\pm0.3$ au and with $1\sigma$ width of $22.2\pm0.5$ au |
| Reduced chi2 Gaussian / hat / power-law | 1.27 / 1.61 / 2.39 | not stated | dimensionless | 5 | the hat-like and the power-law distribution result in $\chi_{\nu}^2 = 1.61$ and $\chi_{\nu}^2 = 2.39$, respectively |
| 12CO extent (blue side) | ~488 au (2.44 arcsec) | not stated | au | 4 | shows $\mbox{$^{12}{\rm CO}$}$ emission up to $\sim2.44$ arcsec ($\sim$488 au) from the disc’s centre |

## Qualitative findings

- Large grains are concentrated in a narrow ring while 12CO extends much further in and out, consistent with planet-disc interaction plus radial drift models.  
  > "The concentration of large grains in a ring-like structure while the gas disc extends much further in and further out is in qualitative agreement" (abstract)

## Claim tuples

- H: Are mm-sized grains in Sz 91 confined to a narrow ring? | E: Band 7 continuum imaging and radial profile fit with three functional forms | R: Gaussian ring at 110.5 au, sigma 22.2 au, 95.5% of dust within 88-132 au | F: Large grains are in a narrow ring | **supported**
- H: Do gas and large dust have different outer radii not due to observational effects? | E: Compare 12CO moment maps with continuum | R: CO detected to ~488 au vs dust to ~150 au | F: Difference not explained by beam dilution or sensitivity | **supported**
- H: Is the structure consistent with planet-induced dust trapping? | E: Qualitative comparison with hydrodynamical models | R: Ring and cavity size differences match predictions | F: Consistent with pile-up by planets | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Focus on Band 7 continuum and 12CO moments for best trade-off between resolution and sensitivity  
  > "as they provide the best trade-off between spatial resolution and sensitivity" (Observations)
- How they decided it was enough: _not stated_
- Limitation (authors): Dust mass relies on ISM grain size distribution assumption that may not hold for large-grain-dominated disc; detailed modelling deferred  
  > "this may not be the case when the dust population is dominated by large grains" (Continuum)
- Limitation (authors): Red-shifted CO side affected by cloud filtering  
  > "The asymmetric shape of the images is a consequence of the filtering-out of the interferometer due to cloud emission" (12CO Moments)
- Caveat (inferred, ours): Dust mass uses a simple scaling with no temperature treatment
- Caveat (inferred, ours): Ring profile fits use only the major-axis profile with uncertain error treatment
- Caveat (inferred, ours): Continuum flux differs from literature, attributed to calibration without test
- Caveat (inferred, ours): Short Band 6 data unused

## Reproducibility

- Data public (paper): Programme codes given; archive data  
  > "(programme 2013.1.00663.S, PI: Canovas)" (Observations)
- Products in archive: _not stated_
- Missing: robust value
- Missing: CASA version and calibration script
- Missing: MCMC details
- Missing: uvfit model specification
- Missing: image parameters
- Data volume (inferred): ~10-50 GB
- Score (inferred): 3/5, Public data and simple analysis but many imaging and fitting parameters are unstated.
- Rediscovery candidate: yes, Public Band 7 data, numeric results (ring radius, width, flux, inclination), fairly simple recipe.

## Links

- Companion: 2015ApJ...805...21C (Earlier ALMA Cycle-0 Band 6 observations of Sz 91 (C2015))
- Related: 2011.0.00733.S

## Checks

```json
{
 "quotes": 58,
 "quotes_ok": 58,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 10,
 "numeric_problems": 0,
 "fill": {
  "facts": 67,
  "stated": 37,
  "rate": 0.552
 },
 "evidence_ok": true
}
```
