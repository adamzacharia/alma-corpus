# ALMA imaging of SDP.81 - II. A pixelated reconstruction of the CO emission lines

`2015MNRAS.453L..26R` | Monthly Notices of the Royal Astronomical Society 2015 | first author: Rybak, M. | arXiv: 1506.01425 | DOI: 10.1093/mnrasl/slv092

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies
- Question: What are the molecular gas distribution, excitation and kinematics of the lensed starburst SDP.81 at sub-100 pc scales, from visibility-plane reconstruction of CO (5-4) and CO (8-7)?  
  > "Here, we focus on a detailed analysis of the CO emission line data that were also taken during the science verification of the ALMA long baseline array." (Introduction)
- Target **SDP.81 (H-ATLAS J090311.6+003906)**: coordinates _not stated_; z/distance z = 3.042 ± 0.001  
  > "H-ATLAS J090311.6+003906; $z =$ 3.042 $\pm$ 0.001" (Introduction); distance from Negrello2010; Negrello14; Frayer2011; Bussmann2013; Dye14  
  > "H-ATLAS J090311.6+003906; $z =$ 3.042 $\pm$ 0.001" (Introduction)

## Data provenance

- ALMA projects: 2011.0.00016.SV
- bands: Bands 4, 6 and 7  
  > "observed for between 4.4 and 5.9 h in Bands 4, 6 and 7" (2.1 ALMA CO emission line imaging)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 15 m to 15 km, 22-36 antennas  
  > "The array consisted of between 22 and 36 antennas with baselines ranging from 15 m to 15 km." (2.1 ALMA CO emission line imaging)
- angular resolution: 180 x 131 mas at PA 77.7 deg (Robust=0, 1 Mλ uv cut)  
  > "this corresponds to a synthesised beam with a full width at half-maximum (FWHM) of 180 $\times$ 131 mas at a position angle of 77.7 deg" (2.1 ALMA CO emission line imaging)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: 4.4 to 5.9 h  
  > "observed for between 4.4 and 5.9 h in Bands 4, 6 and 7" (2.1 ALMA CO emission line imaging)
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: CO 5-4 (not stated)
- Line: CO 8-7 (not stated)
- Other facility **HST WFC3**: F110W and F160W imaging for stellar component  
  > "The data were taken through the F110W and F160W filters, with exposure times of 712 and 4418 s, respectively" (2.2 Archival HST-WFC3 infrared imaging)
- Other facility **VLA**: CO (1-0) D-configuration archival data, 1.5 h  
  > "The integration time was 1.5 h and 16 VLA antennas that had been upgraded with the new receiver systems were used." (2.3 Archival VLA imaging)
- External data: Systemic velocity from CO (1-0) measurement  
  > "offset by about $-$80 km s$^{-1}$ from the systemic velocity, as defined by the CO (1-0) measurement (cite: Frayer2011)" (3 Reconstructions & Analysis) [from (cite: Frayer2011)]

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

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: Briggs, Robust = 0  
  > "For a Briggs weighting scheme with Robust = 0" (2.1 ALMA CO emission line imaging)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: uv-plane subtraction using line-free channels  
  > "we first subtracted the continuum emission from the *uv*-dataset using the line-free channels" (2.1 ALMA CO emission line imaging)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: averaged by 2 channels, 41 km/s resolution  
  > "we averaged the data by 2 channels resulting in a velocity resolution lines of 41 km s$^{-1}$ for both lines" (2.1 ALMA CO emission line imaging)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- ALMA observations and image processing  
  > "The ALMA spectral line observations of SDP.81 and the image processing are discussed in detail by the (cite: alma15b)." (2.1 ALMA CO emission line imaging) [from (cite: alma15b)]
- Lens mass model parameters fixed at Paper I values  
  > "the lens parameters are kept fixed at the most probable values derived in Paper I" (2.1 ALMA CO emission line imaging) [from (cite: Rybak15a)]

### Not stated but needed to reproduce (our reading)

- Calibration steps and CASA version
- Line-free channel ranges
- Regularization settings and priors of the pixelated source reconstruction (code not yet published)
- Kinemetry setup (number of harmonics, centre choices)
- Conversion from intensity to line luminosity details
- Dynamical mass formula

## Analysis recipe

1. **Visibility-plane source reconstruction of CO lines**: Bayesian pixelated lens modelling of continuum-subtracted, channel-averaged visibilities with fixed lens model  
  > "the lens parameters are kept fixed at the most probable values derived in Paper I, while the emission line structure and its regularization level are left as free parameters" (2.1 ALMA CO emission line imaging)
   - parameter: 1 Mλ uv cut; 2-channel averaging (41 km/s)  
  > "a 1 M$\lambda$ cut in the *uv*-distance was imposed" (2.1 ALMA CO emission line imaging)
   - fitting: _not stated_
   - validation: Compared with image-plane zeroth-moment maps of the counter-arc  
  > "We find that our source-plane reconstructions are in good agreement with the observed image-plane structure of the counter-arc." (3 Reconstructions & Analysis)
2. **Integrated line intensities, luminosities and ratio**: Directly integrate zeroth-moment maps over reconstructed source  
  > "determined by directly integrating the zeroth-moment maps over the total extent of the reconstructed source" (3 Reconstructions & Analysis)
   - fitting: _not stated_
   - validation: _not stated_
3. **Kinematic asymmetry and dynamical mass**: Kinemetry of velocity and dispersion maps; mass from maximum radius, velocity and inclination of outermost ordered ellipse  
  > "We estimate the dynamical mass of the disk structure by considering the maximum radius (1.56 $\pm$ 0.07 kpc), maximum velocity (150 $\pm$ 20 km s$^{-1}$)" (3 Reconstructions & Analysis)
   - software: kinemetry
   - assumption: inclination 45 ± 8 deg  
  > "the inclination angle (45 $\pm$ 8 deg)" (3 Reconstructions & Analysis)
   - fitting: _not stated_
   - validation: Downgrading resolution does not change Kasym  
  > "we find that downgrading our resolution does not affect the derived $K_{\rm asym}$ values" (3 Reconstructions & Analysis)

## Software

- **kinemetry** : Fourier decomposition of moment maps  
  > "we model the moment maps using the kinemetry method by (cite: kranovic06)" (3 Reconstructions & Analysis)
- **CASA** : reprocessing VLA CO (1-0) data  
  > "reprocessed them in the standard manner using the Common Astronomy Software Applications (casa) package" (2.3 Archival VLA imaging)
- **galfit** : subtraction of lensing galaxy in HST  
  > "the subtraction of the lensing galaxy emission was done using galfit (cite: peng10)" (2.2 Archival HST-WFC3 infrared imaging)
- **astrodrizzle** : HST reprocessing  
  > "The data were reprocessed using the standard astrodrizzle pipeline (using a pixel size of 65 mas)" (2.2 Archival HST-WFC3 infrared imaging)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| r_8-7/5-4 line luminosity ratio | 0.30 | 0.04 | dimensionless | 2 | intrinsic line luminosity ratio of $r_{\rm 8-7 / 5-4} =$ 0.30 $\pm$ 0.04 |
| CO(5-4) magnification | 17.0 | 0.4 | dimensionless | 1 | 17.0 $\pm$ 0.4 and 16.9 $\pm$ 1.1 |
| CO(5-4) integrated intensity | 0.54 | 0.06 | Jy km/s | 2 | 0.54 $\pm$ 0.06 and 0.45 $\pm$ 0.03 Jy km s$^{-1}$ |
| Dynamical mass within 1.56 kpc | 1.6e10 | 0.6e10 | Msun | 3 | M$($<$ 1.56 kpc) = 1.6 $\pm$ 0.6 $\times$ 10$^{10}$ M$_{\odot}$ |
| K_asym,S08 CO(5-4) | 0.65 | 0.10 | dimensionless | 3 | $K_{\rm asym,S08} =$ 0.65 $\pm$ 0.10 |

## Qualitative findings

- CO (5-4) is more diffuse and structured than CO (8-7); stellar component offset from gas and dust  
  > "emission in CO (5-4) being significantly more diffuse and structured than in CO (8-7)" (abstract)

## Claim tuples

- H: Molecular gas structure depends on excitation | E: Source reconstruction of CO (5-4) and (8-7) | R: CO (5-4) extends ~3 kpc, CO (8-7) ~1.5 kpc | F: Excitation-dependent gas structure | **supported**
- H: SDP.81 is a disk or a merger | E: Kinemetry of velocity maps | R: Kasym above merger thresholds | F: Consistent with merger/post-coalescence | **supported**
- H: Visibility-plane reconstructions are more robust than image-plane | E: Comparison with Dye et al. 2015 | R: More extended structure found | F: Image-plane results need caution | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Dynamical mass should be interpreted with care as system is far from equilibrium  
  > "as the system is far from being in equilibrium, such dynamical mass estimates should be interpreted with care" (3 Reconstructions & Analysis)
- Caveat (inferred, ours): Fixed lens model ignores its uncertainty
- Caveat (inferred, ours): Kasym criteria calibrated at lower resolution

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Lens-modelling code (in prep.)
- Missing: Regularization and calibration details
- Data volume (inferred): tens to hundreds of GB
- Score (inferred): 3/5, Public SV data but the reconstruction code and settings are not given.
- Rediscovery candidate: no, Custom unreleased reconstruction code.

## Links

- Method: (cite: kranovic06) (kinemetry)
- Method: (cite: Vegetti09) (pixelated lensing)
- Companion: (cite: Rybak15a) (Paper I)
- Companion: (cite: alma15b) (ALMA observations)

## Checks

```json
{
 "quotes": 40,
 "quotes_ok": 40,
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
  "facts": 65,
  "stated": 28,
  "rate": 0.431
 },
 "evidence_ok": true
}
```
