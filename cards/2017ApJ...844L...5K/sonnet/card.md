# The Evidence of Radio Polarization Induced by the Radiative Grain Alignment and Self-scattering of Dust Grains in a Protoplanetary Disk

`2017ApJ...844L...5K` | The Astrophysical Journal Letters 2017 | first author: Kataoka, Akimasa | arXiv: 1707.01612 | DOI: 10.3847/2041-8213/aa7e33

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks
- Question: Which mechanism (grain alignment vs self-scattering) produces millimeter-wave polarization in the HL Tau disk, and what maximum grain size does it imply?  
  > "The mechanisms causing millimeter-wave polarization in protoplanetary disks are under debate." (abstract)
- Target **HL Tau**: coordinates _not stated_; z/distance 140 pc  
  > "HL Tau is a young star in Taurus molecular cloud with the distance of 140 pc (cite: Rebull04)." (Introduction); distance from Rebull et al. 2004 (cite: Rebull04)  
  > "HL Tau is a young star in Taurus molecular cloud with the distance of 140 pc (cite: Rebull04)." (Introduction)

## Data provenance

- ALMA projects: 2016.1.00115.S
- bands: Band 3 (3.1 mm)  
  > "we observe the HL Tau disk with Atacama Large Millimeter/submillimeter Array (ALMA) with using Band 3." (Introduction)
- frequencies and spectral setup: four spectral windows at 90.5, 92.5, 102.5, 104.5 GHz, 1.75 GHz bandwidth each  
  > "The correlater processed four spectral windows centered at $90.5, 92.5, 102.5,$ and $104.5$ GHz with a bandwidth of 1.75 GHz each." (Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: C40-6, 41 antennas  
  > "The antenna configuration was C40-6, and 41 antennas were operating." (Observations)
- baselines: _not stated_
- angular resolution: 0.45" x 0.29" (~63 x 41 AU)  
  > "The beam size of the final product is $0.45\ensuremath{''} \times 0.29\ensuremath{''}$" (Observations)
- max recoverable scale: _not stated_
- sensitivity: rms Stokes I, Q, U = 9.6, 6.9, 6.9 uJy  
  > "The rms for Stokes I, Q, U is 9.6, 6.9, 6.9 $\mu$Jy, respectively." (Observations)
- time on source: _not stated_
- observing dates: October 12, 2016 (Cycle 4)  
  > "HL Tau was observed by ALMA on October 12, 2016 during its Cycle 4 operation" (Observations)
- pi or archival as stated: PI: A. Kataoka  
  > "(2016.1.00115.S, PI: A.Kataoka)" (Observations)
- Other facility **CARMA**: 1.3 mm polarization of HL Tau (Stephens et al. 2014) for comparison  
  > "We show the CARMA polarization observations by (cite: Stephens14) in Fig. [2](#fig:compareCARMA)(a)" (Discussions)
- Other facility **SMA**: 0.87 mm total polarization fraction  
  > "The polarization fraction with SMA is reported to be $0.86 \pm 0.4\%$ at 0.87 mm (cite: Stephens14)." (Discussions)
- Other facility **VLA**: 7 mm spectral index with ALMA 3 mm  
  > "spectral index between 3 mm with ALMA and 7 mm with VLA is around $3.0$ (cite: Carrasco-Gonzalez16)" (Discussions)
- External data: CARMA 1.3 mm polarization map and beam 0.65"x0.56", PA 79.5 deg  
  > "which is the beam size of the CARMA observations (cite: Stephens14)" (Discussions) [from Stephens et al. 2014 (cite: Stephens14)]
- External data: SMA total polarization fraction 0.86 ± 0.4% at 0.87 mm  
  > "The polarization fraction with SMA is reported to be $0.86 \pm 0.4\%$ at 0.87 mm (cite: Stephens14)." (Discussions) [from Stephens et al. 2014 (cite: Stephens14)]
- External data: 3 mm–7 mm spectral index ~3.0  
  > "spectral index between 3 mm with ALMA and 7 mm with VLA is around $3.0$ (cite: Carrasco-Gonzalez16)" (Discussions) [from Carrasco-González et al. 2016 (cite: Carrasco-Gonzalez16)]
- Simulation/model as data: Self-scattering polarization P = C P90 ω, C = 2.0%, spherical grains, n(a)∝a^-3.5, a_max = 50, 70, 100, 150 um  
  > "The contribution of the self-scattering is estimated as $P = CP_{90}\omega$, where C is the calibration factor set to be 2.0 %" (Discussions)

## Processing

### Calibration

- pipeline or manual: Raw data reduced by EA-ARC staff  
  > "The raw data were reduced by the EA-ARC staff." (Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Bandpass J0510+1800; amplitude J0423-0120; phase J0431+1731; polarization J0510+1800  
  > "The bandpass, amplitude and phase were calibrated by observations of J0510+1800, J0423-0120, and J0431+1731, respectively" (Observations)
- flux scale uncertainty: _not stated_
- self calibration: Self-calibration applied with iterative CLEAN  
  > "We further perform the iterative CLEAN deconvolution imaging with self-calibration to improve the image quality." (Observations)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: briggs, robust = 0.5  
  > "We employ the briggs weighting with the robust parameter of $0.5$" (Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: 0, 0.3, 0.9 arcsec  
  > "the multiscale option with scale parameters of 0, 0.3, 0.9 arcsec" (Observations)
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: Smoothed to 0.65"x0.56", PA 79.5 deg to compare with CARMA  
  > "we smooth the ALMA observations with the beam size of $0.65\ensuremath{''} \times 0.56\ensuremath{''}$ and PA of 79.5 degrees" (Comparison with the previous observations)
- final beam: 0.45" x 0.29"  
  > "The beam size of the final product is $0.45\ensuremath{''} \times 0.29\ensuremath{''}$" (Observations)
- final rms: Stokes I 9.6, Q 6.9, U 6.9 uJy  
  > "The rms for Stokes I, Q, U is 9.6, 6.9, 6.9 $\mu$Jy, respectively." (Observations)

### Inherited from earlier work

- Instrumental polarization contamination levels (0.1% on-axis, 0.3% within inner 1/3 FWHM)  
  > "More discussion is found in (cite: Nagai16)" (Results) [from ALMA technical handbook; Nagai et al. 2016 (cite: Nagai16)]
- Self-scattering polarization prescription, calibration factor, checked against radiative transfer within 50%  
  > "This prediction is confirmed to match the results radiative transfer calculations of the polarization due to the self-scattering within the error of 50 % (cite: Kataoka16a)." (Discussions) [from Kataoka et al. 2015, 2016a (cite: Kataoka15; Kataoka16a)]

### Not stated but needed to reproduce (our reading)

- CASA version and task details used for imaging and polarization
- Self-calibration solution intervals and number of iterations
- Cell size, image size, masking and CLEAN threshold
- Method for polarized intensity debiasing, and vector plotting details
- Whether the delivered pipeline products were used
- Albedo/opacity tables and refractive indices used for the grain model
- Aperture used for integrated Q, U and I fluxes

## Analysis recipe

1. **Image Stokes I, Q, U**: Iterative CLEAN with self-calibration, briggs weighting, multiscale  
  > "We further perform the iterative CLEAN deconvolution imaging with self-calibration to improve the image quality." (Observations)
   - parameter: robust 0.5; scales 0, 0.3, 0.9 arcsec  
  > "We employ the briggs weighting with the robust parameter of $0.5$ and the multiscale option with scale parameters of 0, 0.3, 0.9 arcsec." (Observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **Measure polarized intensity, fraction and integrated polarization**: Polarized intensity maps; integrated Q,U over disk with debiasing; divide by total Stokes I; compare to instrumental polarization  
  > "the integrated polarized intensity is $PI=\sqrt{Q^2 + U^2 - \sigma_{\rm PI}^2}=56.4$ $\mu$Jy." (Results)
   - assumption: Instrumental polarization 0.1% for on-axis point source  
  > "The derived polarization fraction of the integrated flux corresponds to the case of the point source." (Results)
   - fitting: _not stated_
   - validation: Upper limit set by instrumental polarization  
  > "the upper limit of the integrated polarization fraction of the HL Tau disk at 3.1 mm by our observations is 0.1 %." (Results)
3. **Compare with CARMA 1.3 mm morphology and mechanisms**: Smooth ALMA to CARMA beam and compare vectors with schematic predictions of three mechanisms  
  > "we consider three possibilities: alignment by magnetic fields, alignment by radiation anisotropy, and self-scattering of thermal dust emission." (Comparison with the previous observations)
   - fitting: _not stated_
   - validation: _not stated_
4. **Constrain maximum grain size from total polarization fraction vs wavelength**: Model total polarization as scattering (C P90 ω) plus radiative alignment 0.114 p; compare with SMA, CARMA, ALMA  
  > "The contribution is calculated to be $0.114\times p$ and the polarization vectors are parallel to the major axis." (Modeling the scattered components)
   - parameter: a_max = 50, 70, 100, 150 um; p = 0, 1.8, 3.6%  
  > "The contribution of the radiative alignment is estimated in three cases where the local polarization fraction is $p=0,1.8$, and $3.6 \%$." (Modeling the scattered components)
   - assumption: Disk geometrically and optically thin, uniform p, no wavelength dependence of alignment, spherical grains, a^-3.5 size distribution  
  > "assuming that the disk is geometrically and optically thin, the local alignment efficiency $p$ is the same in the entire disk" (Modeling the scattered components)
   - fitting: Grid comparison by eye, no formal fit  
  > "We vary the maximum grain size $a_{\rm max}$ for $a_{\rm max}=$ 50, 70, 100 and $150{\rm~\mu m}$." (Modeling the scattered components)
   - validation: _not stated_

## Software


## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Total flux density | 75.1 | not stated | mJy | 1 | The total flux density is 75.1 mJy |
| Peak polarized intensity | 145 | not stated | uJy/beam | 2 | The polarized intensity has a peak of 145 $\mu$Jy/beam, which corresponds to 21 sigma detection |
| Polarization fraction on ring | 1.8 | not stated | % | 2 | The polarization fraction is around 1.8 % on the ring. |
| Integrated polarized intensity | 56.4 | not stated | uJy | 2 | $PI=\sqrt{Q^2 + U^2 - \sigma_{\rm PI}^2}=56.4$ $\mu$Jy |
| Total polarization fraction at 3.1 mm | 0.08 | not stated | % | 2 | we obtain 0.08 % for the total polarization fraction |
| CARMA 1.3 mm total polarization fraction | 0.52 | 0.1 | % | 4 | which is $0.52 \pm 0.1 \%$ |
| Maximum grain size | 100 | not stated | um | 4 | we conclude that the maximum grain size is constrained to be $a_{\rm max}=100 {\rm~\mu m}$ |

## Qualitative findings

- 3.1 mm polarization is azimuthal, unlike the 1.3 mm vectors parallel to the minor axis  
  > "The 3.1-mm polarization morphology with our ALMA observation is completely different from that at 1.3 mm." (Comparison with the previous observations)

## Claim tuples

- H: Polarization at 3.1 mm in HL Tau arises from radiative grain alignment | E: ALMA Band 3 polarimetry compared to predicted vector patterns | R: Ring-like azimuthal polarization with 1.8% fraction on the ring | F: Consistent with alignment with radiation anisotropy; toroidal B-field alignment ruled out | **supported**
- H: Self-scattering dominates at 1.3 mm while alignment dominates at 3.1 mm | E: Compare smoothed ALMA with CARMA vectors | R: Morphologies completely different | F: Wavelength dependence favors scattering at 1.3 mm | **supported**
- H: Maximum grain size can be constrained from total polarization fractions | E: Single grain population model vs SMA, CARMA, ALMA total polarization | R: a_max = 100 um fits all | F: Grains smaller than inferred from 3-7 mm spectral index; tension unresolved | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Multi-wavelength polarization needed to distinguish alignment from self-scattering  
  > "To disentangle the mechanisms between the grain alignment and self-scattering, multi-wave polarization observations are essential." (Introduction)
- Alternative: Toroidal magnetic field alignment ruled out; porosity does not resolve grain size tension  
  > "thus we can rule out grain alignment with the toroidal magnetic fields at 3.1 mm." (Comparison with the previous observations)
- How they decided it was enough: _not stated_
- Limitation (authors): Poloidal field alignment not excluded; other parameters could affect total polarization  
  > "However, we cannot rule out the grain alignment with the poloidal magnetic fields." (Comparison with the previous observations)
- Limitation (authors): Low total polarization means detection required resolving the target; peak blobs may be interferometric  
  > "We see three blobs on the ring but it may be due to the interferometric effects." (Results)
- Caveat (inferred, ours): Grain size constrained by comparing three points by eye, no formal fit or uncertainties
- Caveat (inferred, ours): SMA detection only 2 sigma
- Caveat (inferred, ours): Single grain population conflicts with spectral index; uniform p assumed
- Caveat (inferred, ours): Beam dilution and instrumental polarization limit the integrated upper limit

## Reproducibility

- Data public (paper): ALMA project 2016.1.00115.S cited; public status not explicitly stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2016.1.00115.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: CASA version and imaging scripts
- Missing: Self-calibration parameters
- Missing: Grain opacity/albedo model inputs
- Missing: Region used for integrated fluxes
- Data volume (inferred): ~50-100 GB raw
- Score (inferred): 4/5, Single dataset with basic imaging parameters given, but software, self-cal and model details are missing.
- Rediscovery candidate: no, Polarization imaging details and the grain model inputs are insufficiently specified, and public status is not stated.

## Links

- Method: Kataoka et al. 2015 (cite: Kataoka15) (Self-scattering polarization model)
- Method: Tazaki et al. 2017 (cite: Tazaki17) (Radiative grain alignment theory)
- Companion: Stephens et al. 2014 (cite: Stephens14) (CARMA/SMA polarization of HL Tau)
- Companion: ALMA Partnership 2015 (cite: Partnership15) (HL Tau long-baseline campaign)
- Related: ALMA HL Tau long baseline campaign

## Checks

```json
{
 "quotes": 55,
 "quotes_ok": 55,
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
  "facts": 72,
  "stated": 43,
  "rate": 0.597
 },
 "evidence_ok": true
}
```
