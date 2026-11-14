# The dense molecular gas in the z ∼ 6 QSO SDSS J231038.88+185519.7 resolved by ALMA

`2018A&A...619A..39F` | Astronomy and Astrophysics 2018 | first author: Feruglio, C. | arXiv: 1804.05566 | DOI: 10.1051/0004-6361/201833174

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies, agn_and_quasars
- Question: Resolve the dense molecular gas (CO(6-5)) and 3.3 mm continuum in the z~6 QSO J2310+1855 host to derive gas, dynamical and BH masses and compare CO(6-5) with [CII].  
  > "enabling us to resolve the molecular gas emission." (abstract); "In this paper we aim at comparing the kinematics and spatial distribution of CO- and [CII]-emitting gas." (Observations)
- Target **SDSS J231038.88+185519.7 (J2310+1855)**: coordinates continuum 23:10:38.90, 18:55:19.82 (J2000)  
  > "Using the Northern Extended Millimeter Array (NOEMA) W13 detected the CO(6-5) emission line from the host galaxy of the QSO and measured an emission redshift of $z=6.0025$." (Introduction); "The angular scale is 5.835 kpc/$''$  for the adopted cosmology." (Introduction); z/distance z=6.0025 (CO, from W13); z_CO=6.0028±0.0003 measured here  
  > "Using the Northern Extended Millimeter Array (NOEMA) W13 detected the CO(6-5) emission line from the host galaxy of the QSO and measured an emission redshift of $z=6.0025$." (Introduction); "The angular scale is 5.835 kpc/$''$  for the adopted cosmology." (Introduction); distance from redshift from W13; cosmology H0=70, OmegaM=0.3, OmegaL=0.7  
  > "Using the Northern Extended Millimeter Array (NOEMA) W13 detected the CO(6-5) emission line from the host galaxy of the QSO and measured an emission redshift of $z=6.0025$." (Introduction); "The angular scale is 5.835 kpc/$''$  for the adopted cosmology." (Introduction)

## Data provenance

- ALMA projects: 2015.1.00584.S, 2015.1.00997.S
- bands: Band 3 (CO(6-5), continuum); [CII] data separately; band 6 data also scanned  
  > "We observed J2310+1855 with ALMA band-3 receivers tuned to cover the frequency ranges 84.56-87.94, and 96.56-99.69 GHz." (2.1 ALMA observations)
- frequencies and spectral setup: 84.56-87.94 and 96.56-99.69 GHz; spw 1 at CO(6-5) 98.75 GHz; max spectral resolution 23.7 km/s  
  > "Spectral window 1 was tuned at the expected redshifted frequency of CO(6-5), 98.75 GHz." (2.1 ALMA observations)
- continuum bandwidth: _not stated_
- arrays: [CII]: ALMA 12-m array  
  > "[CII] observations were obtained with the ALMA 12-m array in project 2015.1.00997.S." (2.1 ALMA observations)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: Band 3 natural: 0.6x0.4 arcsec PA=-6 deg; Briggs: 0.51x0.28 arcsec; [CII]: 0.9x0.6 arcsec PA=49 deg  
  > "we obtain a synthesized beam of $0.6 \times 0.4$ arcsec$^2$ at a PA$=-6$ deg in the cubes" (2.1 ALMA observations)
- max recoverable scale: _not stated_
- sensitivity: Continuum 5.4 μJy/beam; 0.13 mJy/beam per 23.7 km/s channel; [CII] 0.20 mJy/beam per 100 km/s  
  > "The noise levels are 5.4 $\mu$Jy/beam in the continuum in the aggregated bandwidth, and 0.13 mJy/beam in the 23.7 km/s-wide channels" (2.1 ALMA observations)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: CO 6-5 (not stated (observed 98.75 GHz))
- Line: [CII] 158 μm (not stated)
- Other facility **VLT/X-SHOOTER**: Archival optical/NIR spectrum used for C IV BH mass and 1350 Å luminosity  
  > "We used archival data from X-SHOOTER at the VLT (Vernet et al. 2011) to investigate the optical/NIR spectrum of the QSO." (2.2 X-SHOOTER spectrum)
- External data: FIR luminosity used for SFR  
  > "derived from $\rm L_{FIR}$ (from W13) and the Kennicutt & Evans (2012) relation." (Table 2 notes) [from Wang et al. 2013 (W13)]
- External data: CO(6-5)/CO(2-1) ratio ~0.9 adopted  
  > "Since there is no measurement of lower J CO transition for J2310+1855, we adopt the same ratio." (3.3 BH mass, gas mass, and dynamical mass) [from Stefan et al. (2015); Wang et al. (2016)]
- External data: ASPECS molecular line number counts and CO luminosity function for expected emitters  
  > "In their work, they provide molecular emission line number counts, and the CO luminosity function" (3.4 Search for other line or continuum emitters.) [from Walter et al. (2016), Decarli et al. 2016]

## Processing

### Calibration

- pipeline or manual: Calibration performed in CASA; details not given  
  > "We performed calibration in the CASA environment (McMullin et al. 2007)." (2.1 ALMA observations)
- casa version: CASA v4.7 for [CII]  
  > "The data were calibrated and imaged in CASA v4.7" (2.1 ALMA observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: ≈5% at 91.5 GHz  
  > "the systematic error on the flux scale, which is of the order $\approx 5\%$ at this frequency" (3.1 The 3.3 mm continuum)
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: GILDAS hogbom (also mx, consistent); threshold 0.5 times noise per channel  
  > "We used both the *hogbom* and the *mx* cleaning algorithms within GILDAS, and found consistent results." (2.1 ALMA observations)
- weighting robust: Natural weighting (main); Briggs also tried, robust not stated  
  > "The continuum map and the data cubes were cleaned by adopting a natural weight scheme" (2.1 ALMA observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: No mask for detection  
  > "and without applying any mask for the detection" (2.1 ALMA observations)
- multiscale scales: _not stated_
- continuum subtraction: uvcontsub in CASA, zero-order fit, spw 1 and 2 combined  
  > "By eye, no slope is seen in the continuum, and we verified that a zero-order fit gives the best result." (3.2 CO(6-5) emission line)
- line free channels: velocity > |1000| km/s from line peak (continuum map excludes ±1000 km/s)  
  > "The continuum was then estimated by fitting the line-free channels (at velocity $>|1000| ~\rm km/s$ from the line peak)" (3.2 CO(6-5) emission line)
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: CO imaged with the [CII] restoring beam, 23.7 km/s binning  
  > "we imaged the CO(6-5) data with the same restoring beam as the \[CII\] data" (2.1 ALMA observations)
- final beam: 0.6x0.4 arcsec PA=-6 deg (natural)  
  > "we obtain a synthesized beam of $0.6 \times 0.4$ arcsec$^2$ at a PA$=-6$ deg in the cubes" (2.1 ALMA observations)
- final rms: _not stated_

### Inherited from earlier work

- Source size definition D = 1.5 x FWHM and dynamical mass relation  
  > "We adopt the definition of source size used by W13, equal to 1.5 times the FWHM size" (3.3 BH mass, gas mass, and dynamical mass) [from W13, Feruglio et al. 2014]
- [CII] luminosity, mass and host properties derived in separate paper  
  > "are the subject of a separate paper (Carniani et al. 2018 in prep.)" (2.1 ALMA observations) [from Carniani et al. 2018 in prep.]
- BH mass calibration for C IV  
  > "The calibration by Coatman et al. (2016) provides a correction for these effects." (3.3 BH mass, gas mass, and dynamical mass) [from Coatman et al. (2016)]

### Not stated but needed to reproduce (our reading)

- Briggs robust value
- CASA version and calibration details for band 3 data
- Image/cell sizes
- Exact mask regions for spectrum extraction beyond ≥2σ
- Bolometric luminosity details/1450 Å magnitude source
- Stellar mass uncertainty treatment
- Band 6 data project/details used in emitter search

## Analysis recipe

1. **Image cubes and continuum**: Calibrate in CASA, convert to GILDAS, clean with hogbom, natural weighting  
  > "Mapping and data analysis were performed both in the CASA and in the GILDAS (Guilloteau et al. 2000) environments" (2.1 ALMA observations)
   - software: CASA, GILDAS
   - parameter: threshold 0.5x noise per channel; 23.7 km/s channels  
  > "with detection threshold equal to 0.5 times the noise (per channel)" (2.1 ALMA observations)
   - fitting: _not stated_
   - validation: hogbom and mx give consistent results  
  > "We used both the *hogbom* and the *mx* cleaning algorithms within GILDAS, and found consistent results." (2.1 ALMA observations)
2. **Fit sizes and fluxes in uv plane**: Fit visibilities with point source, circular and elliptical Gaussians; elliptical best  
  > "We fitted the visibilities with a point source and a circular and an elliptical Gaussian function." (3.2 CO(6-5) emission line)
   - software: CASA, GILDAS
   - parameter: line visibilities averaged over -500 to 500 km/s  
  > "in the velocity range from $-500$ to 500 km/s from the systemic velocity" (3.2 CO(6-5) emission line)
   - fitting: 2D Gaussian visibility fit  
  > "the continuum source is best fitted by a 2D Gaussian function" (3.1 The 3.3 mm continuum)
   - validation: CASA and GILDAS consistent  
  > "Both methods give consistent results" (3.1 The 3.3 mm continuum)
3. **Spectrum and kinematics**: Extract spectrum with ≥2σ mask, single Gaussian fit, moment maps, PV diagrams; derive inclination, v_rot, sigma  
  > "We then extracted the spectrum in Fig. [1](#Fig-sp) using a mask that encompasses the $\geq2\sigma$ region in the velocity-integrated CO(6-5) map." (3.2 CO(6-5) emission line)
   - parameter: PV slit 0.5 arcsec, PA=30 deg  
  > "along $\rm PA=30$ $\deg$ (i.e., along the velocity gradient) and orthogonal to it, through the peak CO position, with a slit of 0.5 arcsec in width" (3.2 CO(6-5) emission line)
   - assumption: Velocity gradient due to rotating disk; i=cos^-1(minor/major); v_rot=1.3 Δv/2 sin i; sigma from outer parts  
  > "$i\rm= cos^{-1}~ (minor/major) = 53$ deg" (3.2 CO(6-5) emission line)
   - fitting: Single Gaussian  
  > "A Gaussian fit with a single component gives a peak intensity of the line of $I=2.94\pm0.06$ mJy," (Results, CO(6-5) emission line)
   - validation: _not stated_
4. **CO/[CII] comparison**: Compare CO and [CII] cubes at same beam and registered frame; ratio maps, spectra, PV  
  > "We computed the ratio of CO(6-5)/[CII] by combining the respective velocity-integrated data cubes." (3.2 [CII] and the CO(6-5)/[CII] ratio)
   - parameter: spectra from 0.5 arcsec radius region  
  > "and with a radius of 0.5 arcsec for both lines" (3.2 [CII] and the CO(6-5)/[CII] ratio)
   - fitting: _not stated_
   - validation: _not stated_
5. **BH mass from C IV**: Single-Gaussian fit to C IV in X-SHOOTER spectrum, Coatman et al. calibration with L1350  
  > "We fit the CIV line with a single Gaussian component" (3.3 BH mass, gas mass, and dynamical mass)
   - software: ESO pipeline, Molecfit
   - parameter: z=6.0025 systemic  
  > "By adopting the latter and a systemic redshift of $z=6.0025$" (3.3 BH mass, gas mass, and dynamical mass)
   - fitting: Gaussian, chi2=385.7 for 181 dof  
  > "a $\chi^2=385.7$ for 181 degrees of freedom" (3.3 BH mass, gas mass, and dynamical mass)
   - validation: _not stated_
6. **Gas and dynamical masses**: L'CO from Solomon & Vanden Bout relation; M(H2) with alpha_CO; Mdyn sin^2 i = 1.16e5 (0.75 FWHM)^2 D  
  > "$\rm M_{dyn} \times sin^2(i) = 1.16~ 10^5 \times (0.75\times FWHM_{CO})^2 \times D$" (3.3 BH mass, gas mass, and dynamical mass)
   - parameter: D=2.9 kpc  
  > "$D=2.9$ kpc" (3.3 BH mass, gas mass, and dynamical mass)
   - assumption: L'CO(6-5)=0.9 L'CO(2-1); thermalized; alpha_CO=0.8  
  > "We assume thermalized emission (i.e., $\rm L^\prime~CO(2-1)=L^\prime~CO(1-0)$), and a conversion factor of $\alpha_{CO}=0.8" (3.3 BH mass, gas mass, and dynamical mass)
   - fitting: _not stated_
   - validation: Virial relation gives similar Mdyn = 2.35e10  
  > "By using the virial relation $M_{dyn} =R~ v_{rot}^2 / G$ we find a similar value" (3.3 BH mass, gas mass, and dynamical mass)
7. **Search for other emitters**: Scan cubes at 47.4 km/s, ≥3 contiguous channels, ≥4.5σ; compare with ASPECS counts  
  > "Candidate detections are considered if signal is detected in at least three contiguous spectral channels with a global (i.e., velocity integrated) statistical significance of $\geq4.5\sigma$" (3.4 Search for other line or continuum emitters.)
   - fitting: Gaussian line fits  
  > "By fitting the lines with a Gaussian function we find $\rm FWHM = 300\pm100$ and $220\pm60$ km/s" (Results, Search for other line or continuum emitters)
   - validation: Compared with ASPECS expected counts  
  > "We therefore find a factor of $\sim 3-15$ excess in the number of line-emitting sources in our data compared to the expectation based on ASPECS." (Results, Search for other line or continuum emitters)

## Software

- **CASA** 4.7 (for [CII]): Calibration, imaging, uvcontsub, visibility fitting  
  > "We performed calibration in the CASA environment (McMullin et al. 2007)." (2.1 ALMA observations)
- **GILDAS** : Mapping, cleaning, analysis  
  > "Within GILDAS, we created two data cubes, one per baseband." (2.1 ALMA observations)
- **Molecfit** : Telluric correction of X-SHOOTER spectra  
  > "corrected for telluric absorption using the ESO tool `Molecfit`" (2.2 X-SHOOTER spectrum)
- **ESO X-SHOOTER pipeline** : Reduction of X-SHOOTER spectra  
  > "The spectra were reduced with the ESO pipeline (Modigliani et al. 2010)" (2.2 X-SHOOTER spectrum)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| 91.5 GHz continuum flux density | 416 | ±33 | μJy | 2 | The 91.5 GHz continuum flux density is $416\pm33~ \rm \mu Jy$ |
| CO(6-5) size (FWHM) | (0.33±0.06)x(0.20±0.04) | as given | arcsec | 2 | $(0.33\pm0.06) \times (0.20\pm 0.04)$ arcsec |
| CO(6-5) integrated flux (uv fit) | 1.26 | ±0.06 | Jy km/s | 2 | $Sdv_{\rm CO(6-5)}$ / $1.26\pm0.06$ |
| z_CO | 6.0028 | ±0.0003 | dimensionless | 3 | $z_{CO}=6.0028\pm0.0003$ |
| CO line FWHM | 361 | ±9 | km/s | 3 | FWHM$=361\pm9$ km/s |
| Mean CO(6-5)/[CII] ratio | 0.19 | not stated | dimensionless | 4 | with a velocity-averaged mean ratio of 0.19 |
| L'CO(6-5) | 4.3e10 | ±0.1e10 | K km/s pc^2 | 6 | $(4.3\pm0.1)\times 10^{10}$ |
| M(H2) | 3.2e10 | ±0.2e10 | Msun | 6 | we find a molecular gas mass of $\rm M(H_2)=(3.2 \pm0.2) \times 10^{10} |
| Mdyn sin^2(i) | 2.4e10 | ±0.5e10 | Msun | 6 | We find $\rm M_{dyn} \times sin^2(i) = (2.4\pm0.5) \times 10^{10}~ M_{\odot}$. |
| BH mass (C IV) | 1.8e9 | ±0.5e9 | Msun | 5 | we derive a $\rm M_{BH} = (1.8\pm 0.5) \times 10^{9}~ M_{\odot}$ |
| Inclination | 53 | lower limit 25 deg | deg | 3 | $i\rm= cos^{-1}~ (minor/major) = 53$ deg |
| Molecular gas fraction M(H2)/M* | 4.4 | not stated | dimensionless | 6 | we derive a molecular gas fraction of $\mu=M(H_2)/M^*\approx4.4$ |

## Qualitative findings

- CO(6-5) emission is more centrally concentrated than [CII].  
  > "finding that dense molecular gas is more centrally concentrated with respect to \[CII\]." (abstract)

## Claim tuples

- H: Resolved CO gives a smaller dynamical mass than [CII]-based estimate | E: Gaussian size and FWHM applied to dynamical mass relation | R: Mdyn sin^2 i = (2.4±0.5)e10 Msun | F: About a factor two smaller than W13 | **supported**
- H: Host disk is turbulent and gravitationally unstable | E: v_rot/sigma and Toomre Q | R: v_rot/sigma≈1-2; Q~0.2-0.5 | F: High turbulence and likely fragmentation | **partially**
- H: CO(6-5) and [CII] have different spatial distribution | E: Ratio maps at same beam | R: Ratio peaks near QSO, falls outwards | F: Dense gas more concentrated | **partially**
- H: Possible companions near the QSO | E: Blind line search in band 3 | R: Two 4.5σ candidates | F: Unconfirmed overdensity | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Mdyn from CO(6-5), which traces densest regions where most SF occurs  
  > "which traces the densest regions of molecular clouds, where most of the SF should occur" (Discussion)
- Alternative: Milky Way alpha_CO 4.3 would give M(H2)=1.8e11 Msun  
  > "would imply $\rm M(H_2)=(1.8 \pm0.2) \times 10^{11}~\rm M_{\odot}$" (3.3 BH mass, gas mass, and dynamical mass)
- How they decided it was enough: _not stated_
- Limitation (authors): Candidate emitters unconfirmed; CO/[CII] profile differences need more data; Q is global average  
  > "Confirmation of whether the small discrepancies in the line profiles are genuine would require additional observations." (3.2 [CII] and the CO(6-5)/[CII] ratio)
- Caveat (inferred, ours): No lower-J CO; L'CO(6-5)/CO(2-1) ratio borrowed from other QSOs
- Caveat (inferred, ours): Stellar mass taken as Mdyn minus gas and BH, with large inclination uncertainty
- Caveat (inferred, ours): Band 3 calibration and imaging details sparse
- Caveat (inferred, ours): Beam smearing affects sigma estimate

## Reproducibility

- Data public (paper): ALMA projects and archival X-SHOOTER given by code  
  > "archival X-SHOOTER/VLT (Programme 098.B-0537(A), P.I. Farina)" (Introduction)
- Products in archive: _not stated_
- Missing: Robust parameter for Briggs imaging
- Missing: Band 3 CASA version
- Missing: Band 6 data details
- Missing: Mask definitions
- Data volume (inferred): ~50-100 GB raw for two Band 3/[CII] projects
- Score (inferred): 3/5, Public data and clear formulas, but calibration and imaging details are limited.
- Rediscovery candidate: yes, Archival ALMA data with mostly numeric results and simple fits and formulas.

## Links

- Method: Coatman et al. (2016) (C IV BH mass calibration)
- Method: Solomon & Vanden Bout 2005 (L'CO relation)
- Companion: Wang et al. 2013 (W13) (Previous NOEMA observations of the same QSO)
- Companion: D'Odorico et al. 2018 (Companion emitter detection)
- Companion: Carniani et al. 2018 in prep. ([CII] analysis)
- Related: ASPECS
- Related: WISSH

## Checks

```json
{
 "quotes": 83,
 "quotes_ok": 83,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 12,
 "numeric_problems": 0,
 "fill": {
  "facts": 86,
  "stated": 58,
  "rate": 0.674
 },
 "evidence_ok": true
}
```
