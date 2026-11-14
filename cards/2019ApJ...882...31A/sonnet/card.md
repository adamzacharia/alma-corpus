# A Superluminous Supernova in High Surface Density Molecular Gas within the Bar of a Metal-rich Galaxy

`2019ApJ...882...31A` | The Astrophysical Journal 2019 | first author: Arabsalmani, M. | arXiv: 1906.00972 | DOI: 10.3847/1538-4357/ab2897

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, transients, nearby_galaxies
- Question: Does the SLSN PTF10tpz progenitor form in dense molecular gas, and what are the distribution and kinematics of molecular gas in its metal-rich barred host?  
  > "In this letter we study the properties of molecular gas, the fuel for star formation, in the close environment of this SLSN, and investigate whether its progenitor is formed in a dense environment." (Introduction)
- Target **PTF10tpz host galaxy**: coordinates RA 21:58:31.77, Dec -15:33:02.61 (J2000)  
  > "| 21:58:31.77 | -15:33:02.61 | 0.03976$\pm$0.00007 |" (Table 1); z/distance z = 0.03976 ± 0.00007 (CO)  
  > "| 21:58:31.77 | -15:33:02.61 | 0.03976$\pm$0.00007 |" (Table 1); distance from _not stated_

## Data provenance

- ALMA projects: 2017.1.01568.S
- bands: Band 3  
  > "We used the Band-3 receivers of the ALMA 12-m Array" (Observations and data analysis)
- frequencies and spectral setup: 2 GHz band centred on 110.883 GHz, 1920 channels, ~2.6 km/s resolution, ~5400 km/s coverage  
  > "The observations used a 2 GHz band, centred on 110.883 GHz, covering the redshifted CO(1-0) emission line." (Observations and data analysis)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: C43-6  
  > "12-m Array in C43-6 configuration" (Observations and data analysis)
- baselines: _not stated_
- angular resolution: 0.36"x0.52" (natural weighting)  
  > "With Natural weighting, we yield a synthesised beam size of 0.36$^{\prime\prime}$$\times$0.52$^{\prime\prime}$" (Observations and data analysis)
- max recoverable scale: _not stated_
- sensitivity: 0.3 mJy per channel at 16 km/s  
  > "a root-mean-square noise of 0.3 mJy per channel in the cube" (Observations and data analysis)
- time on source: _not stated_
- observing dates: January 04, 2018  
  > "on January 04, 2018" (Observations and data analysis)
- pi or archival as stated: PI: Arabsalmani  
  > "PI: Arabsalmani" (Observations and data analysis)
- Line: CO J=1-0 (not stated)
- Other facility **Keck I/LRIS**: R-band image of host (from Perley et al. 2016)  
  > "This image was obtained on 26-November-2011 by the Low-Resolution Imaging Spectrometer" (Observations and data analysis)
- Other facility **Keck II/NIRC-2**: archival AO J, H, K' imaging to locate SLSN relative to nucleus  
  > "in order to establish the location of PTF10tpz" (Observations and data analysis)
- External data: Stellar mass 10^10.85 Msun and super-solar metallicity of the host  
  > "With the stellar mass of $\rm 10^{10.85}\,M_{\odot}$ (cite: Perley16-2016ApJ...830...13P)" (Results and Discussion) [from (cite: Perley16-2016ApJ...830...13P)]
- External data: Central SFR of 6.0 Msun/yr from Halpha  
  > "They reported an average ${\rm H}\alpha$-based SFR of $\rm 6.0\,M_{\odot}\,yr^{-1}$ for the central regions of the host" (Results and Discussion) [from (cite: Perley16-2016ApJ...830...13P)]
- External data: Molecular gas clumping factors  
  > "We use the molecular gas clumping factors from (cite: Leroy13-2013ApJ...769L..12L)" (Results and Discussion) [from (cite: Leroy13-2013ApJ...769L..12L)]

## Processing

### Calibration

- pipeline or manual: ALMA pipeline calibration by support staff  
  > "The initial calibration of the data is done by the ALMA support staff, using the ALMA data pipeline" (Observations and data analysis)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: Natural weighting  
  > "With Natural weighting, we yield a synthesised beam size" (Observations and data analysis)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: Mask original cube where smoothed cube is below threshold ~2x noise of a line-free channel  
  > "The threshold flux used to select pixels is approximately twice the noise in a line-free channel of the original spectral data cube." (Observations and data analysis)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: Hanning smoothing over 3 channels, then Gaussian spatial smoothing FWHM 6 pixels, used to build masks  
  > "applying Hanning smoothing across blocks of three consecutive velocity channels" (Observations and data analysis)
- final beam: 0.36"x0.52"  
  > "synthesised beam size of 0.36$^{\prime\prime}$$\times$0.52$^{\prime\prime}$" (Observations and data analysis)
- final rms: 0.3 mJy per channel (16 km/s)  
  > "a root-mean-square noise of 0.3 mJy per channel in the cube" (Observations and data analysis)

### Inherited from earlier work

- R-band image of the host taken from earlier work  
  > "We also use a R-band image of SLSN PTF10tpz host galaxy presented in (cite: Perley16-2016ApJ...830...13P)." (Observations and data analysis) [from (cite: Perley16-2016ApJ...830...13P)]

### Not stated but needed to reproduce (our reading)

- Software names are missing from the text (CASA, tasks for smoothing and moment maps)
- CASA/pipeline version
- Cell and image size, deconvolution settings and clean threshold
- Continuum subtraction and line-free channels
- Flux calibrator and flux scale uncertainty
- Primary-beam correction details
- Exact moment-map parameters and how the integration velocity range was chosen
- How the SLSN position was registered to the ALMA frame

## Analysis recipe

1. **make cube and moment maps**: Spectral cube at ~16 km/s, smoothed-mask moment 0 and 1 maps  
  > "We obtain the total intensity and the intensity-weighted velocity field maps of the CO(1-0) emission line" (Observations and data analysis)
   - parameter: mask threshold ~2x line-free rms  
  > "approximately twice the noise in a line-free channel" (Observations and data analysis)
   - fitting: _not stated_
   - validation: _not stated_
2. **derive molecular gas mass and surface densities**: CO luminosity from integrated flux, Galactic alpha_CO, inclination-corrected surface densities, clumping factors to cloud scale  
  > "We assume a Galactic CO-to-molecular-gas conversion factor of $\alpha_{\rm CO} = 4.36" (Results and Discussion)
   - parameter: inclination 68 deg from axial ratio 0.42, intrinsic 0.2  
  > "This yields an inclination angle of 68$^o$ for the optical disk of the galaxy" (Observations and data analysis)
   - assumption: alpha_CO = 4.36 Msun/(K km/s pc^2)  
  > "We assume a Galactic CO-to-molecular-gas conversion factor of $\alpha_{\rm CO} = 4.36" (Results and Discussion)
   - fitting: _not stated_
   - validation: Noted central alpha_CO may be a factor 2 lower; conclusions unaffected  
  > "This does not affect our conclusions." (Results and Discussion)
3. **estimate progenitor age and mass**: Age from ring orbital velocity ~250 km/s and offset, mapped to mass with stellar lifetime models  
  > "it would have an age of about 3 Myr when it reached the explosion site." (Results and Discussion)
   - assumption: orbital velocity equals radial velocity at apocentres of inner ellipse  
  > "we assume the orbital velocity along the ring to be same as the radial velocity at the apocenters of the inner ellipse" (Results and Discussion)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : Cube and moment-map production (name stripped from text, cited McMullin et al. 2007)  
  > "using the ALMA data pipeline in the package (cite: McMullin07-2007ASPC..376..127M)" (Observations and data analysis)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| CO(1-0) integrated flux | 18.39 | 0.32 | Jy km/s | 2 | We measure a velocity-integrated flux density of $18.39\pm0.32$ Jy km s$^{-1}$ |
| L'CO(1-0) | 1.45e9 | 0.03e9 | K km/s pc^2 | 2 | $L^{\rm T}_{\rm CO(1-0)}= (1.45\pm0.03) \times 10^{9} |
| Molecular gas mass | 10^9.8 | not stated | Msun | 2 | obtain a molecular gas mass of $10^{9.8}\,\rm M_{\odot}$ for the host galaxy |
| CO redshift | 0.03976 | 0.00007 | dimensionless | 1 | centred at a redshift of $z=0.03976 \pm 0.00007$ |
| Mean Sigma_mol | 160 | not stated | Msun/pc^2 | 2 | mean molecular gas surface-density of $\Sigma_{\rm mol} \sim 160\,\rm M_{\odot} pc^{-2}$ |
| Sigma_mol at SLSN beam | ~700 | not stated | Msun/pc^2 | 2 | we measure a $\Sigma_{\rm mol}$ of $\sim 700\,\rm M_{\odot} pc^{-2}$ over a beam centred on the SLSN location |
| Depletion time (central region) | 0.7 | not stated | Gyr | 2 | molecular-gas-depletion time ($M_{\rm mol}/\rm SFR$) of 0.7 Gyr |
| Progenitor mass lower limit | ~100 | not stated | Msun | 3 | the estimated 100 $\rm M_{\odot}$  is in fact a lower limit for the mass of the SLSN progenitor star |

## Qualitative findings

- CO is confined to the bar, consistent with two gas lanes ending in an inner structure likely tied to an inner Lindblad resonance  
  > "These gas lanes end in a gaseous structure in the inner region of the galaxy, likely associated with an inner Lindblad resonance." (abstract)

## Claim tuples

- H: High-density molecular gas favours SLSN progenitor formation | E: Measured Sigma_mol at beam scale around SLSN location | R: ~700 Msun/pc^2 at SLSN, up to ~1400 in inner region | F: Densities comparable to starbursts support dense-environment progenitors | **supported**
- H: Bar-driven gas flows set up the SLSN environment | E: Moment maps, channel maps and PV diagram | R: X-shaped PV pattern and two lanes into an inner structure | F: Lanes plausibly meet an inner resonance ring near the SLSN | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Data do not allow detailed dynamical modelling of the galaxy  
  > "The existing observations do not provide enough information on the pattern speed of the bar, the epicycle frequency, and the mass distribution" (Results and Discussion)
- Caveat (inferred, ours): Single galaxy; one SLSN
- Caveat (inferred, ours): alpha_CO assumed; central value may be 2x lower
- Caveat (inferred, ours): Lane/resonance interpretation qualitative, no dynamical model
- Caveat (inferred, ours): Progenitor mass depends on uncertain lifetime relations and assumed orbital speed

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Imaging parameters and software versions
- Missing: Moment-map and surface-density procedures in detail
- Data volume (inferred): ~50-100 GB raw
- Score (inferred): 4/5, Single public project and simple analysis, but imaging and processing details are sparse.
- Rediscovery candidate: no, Public status not stated in the paper and imaging details are incomplete.

## Links

- Companion: (cite: Arabsalmani19-2019arXiv190300485A) (Related work on dense gas and SLSN/GRB environments)

## Checks

```json
{
 "quotes": 46,
 "quotes_ok": 46,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 65,
  "stated": 33,
  "rate": 0.508
 },
 "evidence_ok": true
}
```
