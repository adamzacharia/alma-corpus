# Multiple-scale gas infall through gravity torques on Milky Way twins

`2024A&A...691A..58D` | Astronomy and Astrophysics 2024 | first author: da Silva, Patrícia | arXiv: 2410.01721 | DOI: 10.1051/0004-6361/202450500

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type archival_reuse

## Science

- Fields: nearby_galaxies, agn_and_quasars
- Question: How fast is molecular gas driven inward by gravity torques from bars and spirals in ten Milky Way (Sbc) morphological twins, barred and non-barred, at 100 pc to 1 kpc scales  
  > "The goal of this work is to quantify the rate of gas inflow due to gravity torques exerted by a bar (or spirals) on the molecular gas." (Method); "We study the molecular gas torques in order to understand the feeding processes in the MW analogues" (Introduction)
- Target **Ten Sbc galaxies: NGC 1300, NGC 1792, NGC 2903, NGC 3059, NGC 4303, NGC 4321, NGC 4536, NGC 4689, NGC 5248, NGC 5921**: coordinates _not stated_; z/distance D < 18 Mpc selection cut; individual distances are tabulated (Table of galaxy properties) but their source is not given in the text  
  > "We also only selected nearby galaxies (D$<$ 18 Mpc) to have enough spatial resolution" (Sample); "The availability of the data limited the sample to ten galaxies" (Sample); distance from _not stated_

## Data provenance

- ALMA projects: 2015.1.00925.S, 2015.1.00956.S, 2017.1.00886.L, 2018.1.00517.S, 2018.1.01651.S, 2019.1.00876.S, 2019.1.01718.S, 2019.1.01730.S, 2019.1.01742.S
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: moderate; results below 1 arcsec (66 pc at 13.7 Mpc) disregarded; per-dataset beam major axes are in the observation table  
  > "we disregarded results below 1 arcsec (corresponding to 66 pc at an average distance of 13.7 Mpc) in general" (Discussion); "The spatial resolution we used is considered moderate, and can only provide a general idea of what occurs in these galaxies at scales of 100 pc – 1 kpc." (Discussion)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: PHANGS survey data plus other ALMA archive programs  
  > "we used ALMA data mainly from the Phangs survey (cite: PHANGS) and from the ALMA archive" (Sample)
- Line: CO not stated (230.538 and 345.796/345.800 as printed in the observation table (column 'Rest Frequency (MHz)'))
- Other facility **HST (F814W)**: red stellar images used to compute the gravitational potential  
  > "We used HST images in the F814W filter" (Sample)
- Other facility **Legacy Surveys DR9 (R and Z bands)**: wider-FOV red stellar images used to compute the gravitational potential  
  > "Legacy survey DR9 images in the R (for NGC 4303 and NGC 4536 because their Z-band images are saturated at the nucleus) and Z bands" (Sample)
- Other facility **VLT/MUSE (ESO archive)**: H-alpha images for four galaxies, used for comparison torques  
  > "only four galaxies (NGC 1300, NGC 4303, NGC 4321 and NGC 5248) had Multi Unit Spectroscopic Explorer (MUSE) data cubes available." (H$\alpha$ gas torques with MUSE data); "The data were taken from the ESO public archive." (H$\alpha$ gas torques with MUSE data)
- Other facility **NASA/IPAC Extragalactic Database (NED)**: morphological classification used to select the sample  
  > "Based on the classification in the NASA/IPAC Extragalactic Database" (Sample)
- External data: PHANGS-ALMA CO data used for most galaxies  
  > "we used ALMA data mainly from the Phangs survey (cite: PHANGS)" (Sample) [from Leroy et al. 2021 (cite: PHANGS)]
- External data: Observed rotation curves of NGC 1300 used to check the model rotation curve  
  > "the rotation curve from the potential model is compared to the observed curves from (cite: Lang20), (cite: england89), and (cite: Lindblad97)" (Gas torque analysis) [from (cite: Lang20); (cite: england89); (cite: Lindblad97)]
- External data: Galaxy position angles, bar PAs, inclinations, distances, masses taken from the literature (tabulated with reference superscripts)  
  > "The images were rotated and deprojected according to the PAs and inclination angles given in Table" (Method) [from references numbered in the galaxy-properties table; not resolvable from the text]
- External data: Dark matter neglected in central parts of MW-like galaxies  
  > "while the dark matter can be neglected in the central parts of MW-like galaxies (cite: Persic1996)" (Method) [from (cite: Persic1996)]

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
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: all maps resampled to the same number of pixels and pixel size (values not given)  
  > "All maps were resampled to the same number of pixels and pixel sizes." (Method)
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

- Stellar exponential disk thickness ~1/12 of radial scale length  
  > "we assumed a stellar exponential disk thickness of $\sim$1/12th of the radial scale length of the galaxies (cite: Garcia-Burillo2005; audibert19)" (Method) [from (cite: Garcia-Burillo2005; audibert19)]
- Interpretation of t(R) as time derivative of specific angular momentum of azimuthally averaged gas (torque method)  
  > "of the gas averaged azimuthally (cite: Garcia-Burillo2005)" (Gas torque analysis) [from (cite: Garcia-Burillo2005)]
- Definition of the strength Q_m(R) as ratio of tangential to radial forces  
  > "that is, by the ratio between tangential and radial forces (cite: Combes1981)" (Gas torque analysis) [from (cite: Combes1981)]
- Processing and maps of the PHANGS ALMA data  
  > "we used ALMA data mainly from the Phangs survey (cite: PHANGS)" (Sample) [from (cite: PHANGS)]

### Not stated but needed to reproduce (our reading)

- Which PHANGS data release / product (resolution, moment-0 or cube) was used for each galaxy, and how the other archive projects were calibrated and imaged (CASA version, weighting, beam, rms, line-free channels)
- How the CO emission maps were made (moment definitions, clipping, masking) before being used as the gas density Sigma, and whether a CO-to-H2 factor was applied
- Final common pixel size and field of view for each (ALMA, HST/Legacy) pair
- Exact centre chosen per galaxy and the bulge/disk decomposition used before deprojection
- Which bright-star masking procedure and sky subtraction were applied to the HST and Legacy images
- Numerical method for the Fourier potential and force computation (radial grid, softening, boundary handling) and the torque code itself
- Uncertainties on Qmax, dL/L and on radii in the torque table
- Which Legacy band (R or Z) was used per galaxy beyond the NGC 4303 and NGC 4536 cases
- Details of the MUSE Halpha image construction (spectral interval, continuum interval)

## Analysis recipe

1. **assemble matched stellar and CO data per field of view**: Pair each ALMA CO data set with an HST or Legacy red image of matching FOV; combine two ALMA data sets for larger FOV in NGC 1300 and NGC 2903  
  > "two data sets were from the program 2015.1.00925.S and were combined in order to form a larger FOV" (Method); "For better results, we used HST data." (Method)
   - parameter: Sample selection: inclination below 65 deg, D < 18 Mpc, B magnitude below 12, giving 43 galaxies, then ten with data  
  > "these criteria led to 43 galaxies" (Sample); "The availability of the data limited the sample to ten galaxies" (Sample)
   - fitting: _not stated_
   - validation: _not stated_
2. **clean, centre, rotate and deproject images and cube**: Remove Milky Way stars, rotate by galaxy PA so major axis is horizontal, align centres of stellar and ALMA data, deproject by stretching the vertical axis; apply same rotation and deprojection to the ALMA cube converted to velocities relative to the centre  
  > "We then rotated the images using the PA of the galaxy" (Method); "The images were then deprojected by stretching the vertical axis." (Method); "For the ALMA data, the same rotation and deprojection were applied to the data cube converted into velocities relative to the centre." (Method)
   - software: Python, Gildas
   - parameter: Centre from emission peak of the nuclear source in the infrared image; ALMA centre from the emission peak or the ring centre, using the velocity field  
  > "We also centred the ALMA data cube according either to the emission peak or to the centre of the ring, and we used the velocity field." (Method)
   - assumption: Bulge treated as spherical and separated for deprojection  
  > "The bulge component was separated for the deprojection, because it was assumed to be spherical" (Method)
   - fitting: _not stated_
   - validation: _not stated_
3. **compute gravitational potential, forces and bar/spiral strength**: Fourier transform the deprojected red image to get potential and forces; decompose potential in Fourier components and derive Q_m(R) and Q_T(R)  
  > "After rotation and deprojection, the images were Fourier transformed to compute the gravitational potential and forces." (Method); "The strength of the total non-axisymmetric perturbation $Q_T(R)$ is defined similarly, with the maximum amplitude of the tangential force $F_T^{max}(R)$." (Gas torque analysis)
   - parameter: Disk thickness ~1/12 of radial scale length  
  > "we assumed a stellar exponential disk thickness of $\sim$1/12th of the radial scale length of the galaxies (cite: Garcia-Burillo2005; audibert19)" (Method)
   - assumption: Constant M/L throughout disk and bulge  
  > "The M/L was assumed to be constant throughout the disk and bulge." (Method)
   - assumption: Dark matter negligible in central parts  
  > "while the dark matter can be neglected in the central parts of MW-like galaxies (cite: Persic1996)" (Method)
   - fitting: _not stated_
   - validation: _not stated_
4. **compute gas-weighted torques and normalised angular momentum loss**: Torque per unit mass from forces at each pixel, weighted by the CO gas density, averaged over azimuth, and normalised by L divided by the rotation period to give dL/L per rotation  
  > "The net effect on the gas at each radius is then the product of the torque by the gas density $\Sigma$." (Gas torque analysis); "The efficiency of the gas flow was then estimated through normalising $t(R)$ at each radius by the angular momentum $L$, divided by the rotation period $T= 2\pi/\Omega$" (Gas torque analysis)
   - parameter: Sign of torque defined relative to sense of rotation in the galaxy plane  
  > "The sign of the torque was determined relative to the sense of rotation in the plane of the galaxy." (Gas torque analysis)
   - assumption: Gas stays in its radial range during one rotation (needed for the azimuthal average); orbits taken as circular  
  > "that the gas has time to remain in its radial range during one rotation" (Gas torque analysis); "although the orbits of the gas, when deprojected, are not circular" (Discussion)
   - fitting: _not stated_
   - validation: Results independent of M/L because torques are normalised; results below 1 arcsec disregarded  
  > "With this normalisation, the computations are independent of the constant M/L ratios used." (Gas torque analysis)
5. **normalise NGC 1300 torques with a rotation curve**: Where relative loss of angular momentum exceeds one, plot only the torque map normalised with physical quantities from a rotation curve derived from the potential, compared with observed curves  
  > "The latter was derived from the potential itself, assuming a constant mass-to-light ratio, and normalised to the CO, HI, and optical observations" (Gas torque analysis)
   - assumption: Constant mass-to-light ratio  
  > "assuming a constant mass-to-light ratio" (Gas torque analysis)
   - fitting: _not stated_
   - validation: Model rotation curve compared with observed curves from the literature  
  > "the rotation curve from the potential model is compared to the observed curves from (cite: Lang20), (cite: england89), and (cite: Lindblad97)" (Gas torque analysis)
6. **compare with torques on H-alpha gas from MUSE**: Build H-alpha images from MUSE cubes by summing the line interval and subtracting nearby continuum, cut to the matching FOV, and compute torques as for ALMA  
  > "by summing the spectral interval of the emission line and by subtracting the nearby continuum equivalent to the same interval" (H$\alpha$ gas torques with MUSE data); "We then computed the torques analogously to what was done with the ALMA data." (H$\alpha$ gas torques with MUSE data)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **Python** : scripts for rotation, deprojection of images and ALMA cube  
  > "These processes were performed with scripts in Python and Gildas environments." (Method)
- **Gildas** : scripts for rotation, deprojection of images and ALMA cube  
  > "These processes were performed with scripts in Python and Gildas environments." (Method)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| NGC 1300 nuclear ring radius | about 300 pc | not stated | pc | 0 | The morphology is that of a ring with a radius of about 300 pc |
| NGC 4303 nuclear ring radius | about 310 pc | not stated | pc | 0 | The ring radius is about 310 pc. |
| NGC 4321 nuclear ring radius | ~500 pc | not stated | pc | 0 | The nuclear ring radius is $\sim$ 500 pc. |
| NGC 5248 nuclear ring radius | about 88 pc | not stated | pc | 0 | a nuclear ring at the centre, with a radius of about 88 pc |
| NGC 5921 nuclear ring radius | about 230 pc | not stated | pc | 0 | a nuclear ring with a radius of about 230 pc is visible |
| NGC 4536 nuclear bar diameter | about 2.1 kpc (PA ~136 deg) | not stated | kpc | 0 | molecular gas images show a clear nuclear bar with a PA $\sim$ 136$^{\circ}$ and a diameter of about 2.1 kpc |
| NGC 3059 total-perturbation strength Qmax (bar), at 0.24 kpc | 0.928 | not stated | dimensionless | 3 | 0.928 B; but we found that this galaxy has the strongest bar in the sample. |
| NGC 3059 torque sign ranges | positive from 0.3 to 0.6 kpc, negative from 0.6 to 1 kpc, negative below 0.3 kpc | not stated | kpc | 4 | The torque is positive from 0.3 to 0.6 kpc, and then negative from 0.6 to 1 kpc; The torques are negative at radii lower than 0.3 kpc |
| Resolution cut applied to torque results | 1 arcsec = 66 pc at 13.7 Mpc | not stated | pc | 4 | we disregarded results below 1 arcsec (corresponding to 66 pc at an average distance of 13.7 Mpc) in general |
| Maximum relative loss of angular momentum per rotation (extreme cases) | nearly 100% | not stated | percent | 4 | The relative loss of angular momentum can be quite high and may reach nearly 100% in one rotation for extreme cases. |

## Qualitative findings

- Six galaxies show nuclear rings and two show nuclear bars; NGC 4689 shows no clear nuclear structure  
  > "Six galaxies present clear evidence of nuclear rings (N1300, N2903, N4303, N4321, N5248, and N5921). Two objects have a nuclear bar (N4536 and N5921)." (Gas morphology and kinematics)
- Torques are not significant in non-barred flocculent galaxies  
  > "The torques are not significant in non-barred flocculent galaxies, as for NGC 1792 in Fig." (Gas torque analysis)
- NGC 2903 torques are chaotic mainly because of patchy CO emission  
  > "The main factor is the patchiness of the CO emission, which prevents a spatial continuity in the torque computation." (Gas torque analysis)

## Claim tuples

- H: Do bars drive gas inward between corotation and the inner Lindblad resonance in MW twins? | E: Gas-density-weighted gravity torques from HST/Legacy potentials and ALMA CO maps in ten galaxies | R: Negative torques are seen in several barred galaxies when the FOV includes enough of the bar | F: For barred galaxies, torques are negative between corotation and the ILR, as expected | **supported**
- H: Are torques significant in inner resonant rings and non-barred flocculent galaxies? | E: Torque maps and azimuthal averages for ring-only FOVs and non-barred galaxies (NGC 1792, NGC 4689) | R: No single coherent behaviour in ring-only FOVs; torques not significant in flocculent galaxies | F: Torques are not significant in inner resonant rings or flocculent galaxies | **supported**
- H: How strong can the angular momentum loss be, and what happens for very strong thin bars? | E: Normalised torques dL/L per rotation across fields of view | R: Relative loss exceeds one in absolute value only for NGC 1300 | F: Loss can reach nearly 100% per rotation; very strong thin bars give elongated orbits and gas driven to the nucleus | **partially**
- H: Does AGN feedback leave a dynamical imprint on the gas in these nuclei? | E: Gas morphology and torques at moderate resolution | R: No dynamical influence of AGN feedback or radio jets detected | F: Not detected, but resolution and AGN activity are low, so no firm conclusion | **partially**
- H: Do torques on H-alpha gas agree with torques on molecular gas? | E: H-alpha images from MUSE for four galaxies, same torque method | R: Compatible but noisier and patchier | F: H-alpha torques are compatible with molecular gas torques | **supported**

## Reasoning

- Why this data: Red images chosen to trace stellar mass and avoid dust extinction and young-star bias  
  > "we needed red images of the galaxies to avoid dust extinction and to avoid biasing by the light of a small number of OB stars with low mass-to-light ratios (M/L)" (Sample)
- Why this method: Normalised torques make the result independent of the M/L value  
  > "Its precise value was considered not to be important because we computed normalised torques, corresponding to the relative loss of angular momentum per rotation." (Method)
- Alternative: Legacy image not used for NGC 5921 because small ALMA FOV would give the same result as HST  
  > "This galaxy has Legacy images; because the ALMA data have a small FOV, it would provide the same results as were obtained with HST images with a lower spatial resolution, however." (Method)
- Alternative: NGC 1255 and NGC 4030 excluded because the ALMA FOV was too small  
  > "Another two galaxies have ALMA data, but the FOV was too small for this work : NGC 1255 and NGC 4030" (Sample)
- How they decided it was enough: Sample size set by data availability  
  > "The availability of the data limited the sample to ten galaxies" (Sample)
- Limitation (authors): Spatial resolution is insufficient for gas dynamics at 10-100 pc scales  
  > "The spatial resolution of the data we analysed here is insufficient to compute the gas dynamics at these scales in detail." (Discussion)
- Limitation (authors): Results depend strongly on PA and inclination, which can be biased in barred galaxies  
  > "The results strongly depend on these values because the deprojection is important for the computation of the torques." (Discussion)
- Limitation (authors): Authors call the study preliminary  
  > "We consider this study as preliminary results that are to be pursued in the future with data that have a better spatial resolution" (Discussion)
- Caveat (inferred, ours): Constant M/L and a thin-disk, no-dark-matter potential are assumed; no uncertainty propagation on Qmax or dL/L is given
- Caveat (inferred, ours): Azimuthal average assumes circular orbits and gas staying in radial range for one rotation, which fails for NGC 1300
- Caveat (inferred, ours): CO surface density is used directly as gas density with no stated treatment of CO-to-H2 conversion or noise clipping
- Caveat (inferred, ours): Several galaxies sit at inclinations near or above the stated 65 deg limit
- Caveat (inferred, ours): Sample of ten is small and not independent of data availability

## Reproducibility

- Data public (paper): ALMA archive and PHANGS data, HST, Legacy Surveys and ESO MUSE public archive data  
  > "we used ALMA data mainly from the Phangs survey (cite: PHANGS) and from the ALMA archive" (Sample); "The data were taken from the ESO public archive." (H$\alpha$ gas torques with MUSE data)
- Products in archive: _not stated_
- Code: _not stated_
- Missing: Torque and potential code (only described by equations and prose)
- Missing: Which PHANGS or archive product and resolution per galaxy; CO map construction
- Missing: Pixel sizes, FOVs, centres and PA/inclination sources per galaxy
- Missing: Uncertainties on all tabulated torque quantities
- Data volume (inferred): Large: nine ALMA projects including the PHANGS-ALMA large program; CO cubes for ten galaxies, likely tens of GB to a few hundred GB if raw, far less if PHANGS products are used
- Score (inferred): 3/5, Data are public and the torque method is described with equations, but ALMA product choices, map construction, pixel grids, code and uncertainties are not given.
- Rediscovery candidate: no, Data are public, but the recipe lacks code and gas-map construction details, and the main results are a mix of tabulated values and qualitative torque-map descriptions.

## Links

- Method: Garcia-Burillo et al. 2005 (cite: Garcia-Burillo2005) (Torque method and disk-thickness assumption inherited)
- Method: Combes & Sanders 1981 (cite: Combes1981) (Definition of bar strength Q_m)
- Method: Audibert et al. 2019 (cite: audibert19) (Same torque approach and disk thickness assumption)
- Companion: Leroy et al. 2021 (cite: PHANGS) (Source of most ALMA CO data)
- Companion: Combes et al. 2014 (cite: combes14) (Earlier torque study of NGC 1566, excluded from this sample)
- Related: PHANGS-ALMA
- Related: Legacy Surveys DR9
- Related: HST F814W imaging
- Related: MUSE (ESO archive)

## Checks

```json
{
 "quotes": 94,
 "quotes_ok": 94,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 9,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 10,
 "numeric_problems": 0,
 "fill": {
  "facts": 93,
  "stated": 48,
  "rate": 0.516
 },
 "evidence_ok": true
}
```
