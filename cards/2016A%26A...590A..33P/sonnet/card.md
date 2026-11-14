# Constraining the physical structure of the inner few 100 AU scales of deeply embedded low-mass protostars

`2016A&A...590A..33P` | Astronomy and Astrophysics 2016 | first author: Persson, M. V. | arXiv: 1603.01061 | DOI: 10.1051/0004-6361/201527666

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: star_formation, astrochemistry
- Question: Do deeply embedded Class 0 protostars host compact disk-like structures on scales of a few 100 AU, what are their radii, masses and temperature structure, and how does this affect gas-phase water abundances on hot-core scales?  
  > "We determine the presence and characteristics of compact, disk-like structures in deeply embedded low-mass protostars." (abstract)
- Target **VLA 1623 A**: coordinates _not stated_; z/distance 120 pc  
  > "VLA 1623 in the $\rho$ Ophiuchus star forming region (cite: loinard08)" (Sample and observations); "VLA 1623 A" (Table 1); distance from Loinard et al. 2008  
  > "VLA 1623 in the $\rho$ Ophiuchus star forming region (cite: loinard08)" (Sample and observations); "VLA 1623 A" (Table 1)
- Target **NGC 1333 IRAS 2A, IRAS 4A-NW/SE, IRAS 4B**: coordinates _not stated_; z/distance 235 pc  
  > "Distances are taken from (cite: hirota08) and (cite: loinard08)." (Table 1 notes); distance from Hirota et al. 2008  
  > "Distances are taken from (cite: hirota08) and (cite: loinard08)." (Table 1 notes)

## Data provenance

- ALMA projects: 2013.1.01004.S
- bands: VLA 1623 A ALMA data at 219.0 GHz (1.3 mm)  
  > "the ALMA Cycle 2 VLA 1623 data are from (cite: murillo15) at 219.0 GHz" (Sample and observations)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 13.8–796.6 kλ (18''–0.3'')  
  > "cover baselines from 13.8–796.6 $k\lambda$ (18$''$–0.3$''$)" (Sample and observations)
- angular resolution: beam 0.3x0.5'' (92 deg) for VLA 1623 A  
  > "| VLA 1623 A | 0.6 | 140 | $0.3\times0.5$ (92$^{\circ}$) |" (Table 2)
- max recoverable scale: _not stated_
- sensitivity: 0.6 mJy/beam rms for VLA 1623 A  
  > "| VLA 1623 A | 0.6 | 140 | $0.3\times0.5$ (92$^{\circ}$) |" (Table 2)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Other facility **IRAM PdBI**: 203.4 GHz continuum for IRAS 2A and 4B  
  > "The continuum toward NGC 1333 IRAS 2A and 4B at 203.4 GHz has been obtained with the Plateau de Bure Interferometer" (Sample and observations)
- Other facility **SMA**: 335 GHz continuum for IRAS 4A  
  > "IRAS 4A was observed with the Submillimeter Array (SMA) at 335 GHz (Lai et al. in prep)." (Sample and observations)
- External data: Envelope density/temperature models and parameters (Table of envelope parameters)  
  > "From (cite: kristensen12; jorgensen02; murillo13a; murillo13b) and references therein." (Envelope parameters) [from Kristensen et al. 2012; Jørgensen et al. 2002]
- External data: VLA 1623 A disk PA, inclination and stellar mass 0.2 Msun from kinematics  
  > "3. Kinematic line analysis (cite: murillo13b)" (Table 3) [from Murillo et al. 2013b]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: Natural weighting, Hogbom CLEAN for display images; analysis done in uv-plane  
  > "The resulting continuum maps from standard imaging (natural weighting, Hogbom CLEAN algorithm) are shown in Fig." (Sample and observations)
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
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- ALMA VLA 1623 data taken from earlier paper  
  > "the ALMA Cycle 2 VLA 1623 data are from (cite: murillo15)" (Sample and observations) [from Murillo et al. 2015 (cite: murillo15)]
- Visibility de-projection approach  
  > "The de-projection is performed on the visibilities using the same approach as given in (cite: hughes07)" (Application of models to data) [from Hughes et al. 2007 (cite: hughes07)]

### Not stated but needed to reproduce (our reading)

- ALMA calibration and reduction details for VLA 1623 data (deferred to Murillo et al. 2015)
- Initial guesses/bounds for fits
- Exact visibility bin widths in kλ
- Companion subtraction fit parameters

## Analysis recipe

1. **Subtract envelope model**: Simulate observations of spherical envelope model images (TRANSPHERE + RATRAN) with uv_fmodel and subtract from visibilities  
  > "The routine simulates observations of the model image by sampling the same $\mathit{u}$-$\mathit{v}$ coverage as the observations." (3.1 Envelope model)
   - software: TRANSPHERE, RATRAN, GILDAS
   - assumption: Gas-to-dust ratio 100; Ossenkopf & Henning opacities; optically thin envelope  
  > "assuming a gas-to-dust ratio of $\Delta_{g/d}=100$" (3.1 Envelope model)
   - fitting: _not stated_
   - validation: _not stated_
2. **Subtract companions, recenter, de-project**: Fit Gaussian+point source to companions and subtract; shift phase center; de-project with PA and inclination  
  > "A Gaussian and a point source are fitted to all components and those corresponding to companion(s) are subtracted from the visibilities." (3.4 Application of models to data)
   - parameter: Assumed inclination 60 deg when unknown, varied by 15 deg  
  > "which is then assumed to be $60^{\circ}$" (3.4 Application of models to data)
   - fitting: _not stated_
   - validation: Visual inspection of residual image  
  > "Visual inspection of the residual image confirms the success of the subtraction." (3.4 Application of models to data)
3. **Fit Gaussian + point source and power-law disk to binned real visibilities**: Fit Gaussian plus point source, then Berger & Segransan thin power-law disk with r_c from Gaussian  
  > "The models are fitted to the data using the Levenberg-Marquardt algorithm through the SciPy.optimize module" (3.4 Application of models to data)
   - software: SciPy
   - parameter: q=0.5, T0=1500 K at 0.1 AU, Tmin=10 K, inner radius 0.1 AU, Tavg=30 K for Gaussian mass  
  > "We assume $q=0.5$ for all modeled disks." (3.3 Power-law disk)
   - assumption: Stellar mass 0.05 Msun (0.2 for VLA 1623 A)  
  > "The density is then calculated for a central source of $M_{\star}=0.05~M_\odot$ for all sources except VLA 1623 A" (3.3 Power-law disk)
   - fitting: Levenberg-Marquardt least squares; free parameters p and Sigma_0  
  > "The free parameters in fitting this power-law disk are those for the surface density, $p$ and $\Sigma_0$." (3.3 Power-law disk)
   - validation: Compared with literature radii and masses  
  > "While the disk radii agree with previous estimates the masses are different for some of the sources studied." (Discussion, Disk radii and masses)

## Software

- **GILDAS** : PdBI calibration/imaging and uv_fmodel  
  > "The calibration and imaging was done in IRAM GILDAS." (Sample and observations)
- **TRANSPHERE** : Dust temperature of envelope  
  > "using the dust continuum radiative transfer code TRANSPHERE" (3.1 Envelope model)
- **RATRAN** : Envelope model continuum images  
  > "Monte Carlo radiative transfer code RATRAN" (3.1 Envelope model)
- **SciPy** : Levenberg-Marquardt fitting  
  > "through the SciPy.optimize module" (3.4 Application of models to data)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| VLA 1623 disk radius (Gaussian fit) | 40 | ±2 | AU | 3 | $40\pm2$ |
| VLA 1623 power-law disk mass | 9 | ±1 | 1e-3 Msun | 3 | / VLA 1623 / $1.2\pm0.2$ / $2.4\pm0.5$ / $9\pm1$ / $30\pm3$ / |
| IRAS 4B power-law disk mass | 140 | +105/-15 | 1e-3 Msun | 3 | $140$$\substack{+105\\-15}$ |
| Gas surface density range at r0=50 AU | 2.4-51 | not stated | g cm^-2 | 3 | The gas surface density varies between 2.4 and 51 g cm$^{-2}$ at $r_0= 50$ AU. |
| IRAS 2A envelope-only power-law index a | -0.78 | ±0.03 | dimensionless | 0 | $a=-0.78\pm0.03$ |

## Qualitative findings

- A thin disk model approximates the inner few 100 AU emission; a single power-law envelope cannot reproduce both small- and large-scale emission.  
  > "A spherically symmetric single power-law envelope model fails to simultaneously reproduce both the small- and large-scale emission." (abstract)

## Claim tuples

- H: Compact disk-like structures can be characterized from continuum visibilities of Class 0 sources | E: Fit Gaussian and power-law disk models to envelope-subtracted de-projected visibilities of five sources | R: Radii 90-170 AU; power-law disk masses 9-140e-3 Msun | F: Thin disk model approximates the emission, but kinematics are needed to confirm Keplerian disks | **supported**
- H: Disk structure changes inferred water abundances | E: Compute mass above 100 K and recompute abundances from H2(18)O | R: 7-30% of mass above 100 K; water abundance up to 6.2e-5 in IRAS 2A | F: Abundances are about an order of magnitude higher than with warm and cold H2 | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Single power-law envelope fit rejected as it cannot match large-scale emission  
  > "Thus, the single power-law envelope cannot reproduce the interferometric visibilities and the large-scale emission at the same time." (5.3 Envelope-only model)
- How they decided it was enough: _not stated_
- Limitation (authors): Fixed temperature profile and no vertical structure; most sources lack long baselines  
  > "For some of the sources in the study there are no observations with longer baseline coverage, thus adding degeneracy to the fitting" (5.2 Disk radii and masses)
- Caveat (inferred, ours): Fixed q=0.5 and Tavg=30 K drive masses
- Caveat (inferred, ours): Envelope subtraction depends on prior models
- Caveat (inferred, ours): Uncertainties from fits not independent of assumed inclination

## Reproducibility

- Data public (paper): Continuum data available via vilhelm.nu and CDS  
  > "Continuum data for the sources are available through <http://vilhelm.nu> and at CDS" (footnote)
- Products in archive: _not stated_
- Missing: Reduced visibilities of SMA/PdBI data not in archive; ALMA calibration deferred to Murillo et al. 2015
- Data volume (inferred): ~10 GB for the ALMA part
- Score (inferred): 3/5, Models are described analytically but multi-facility data and inherited envelope models need extra sources.
- Rediscovery candidate: no, Only VLA 1623 is ALMA; other data are PdBI/SMA and the recipe depends on external models.

## Links

- Method: Berger & Segransan 2007 (Analytic visibilities of thin power-law disk)
- Method: Hughes et al. 2007 (Visibility de-projection)
- Companion: Murillo et al. 2015 (Source of the ALMA VLA 1623 data)

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
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 72,
  "stated": 34,
  "rate": 0.472
 },
 "evidence_ok": true
}
```
