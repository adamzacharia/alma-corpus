# Shadowing in the Protoplanetary Disk of ZZ Tau IRS with HST

`2024AJ....167...75H` | The Astronomical Journal 2024 | first author: Hashimoto, Jun | arXiv: 2401.02004 | DOI: 10.3847/1538-3881/ad1b5e

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth light | type multi_facility_alma_minor

## Science

- Fields: protoplanetary_disks
- Question: Is the outer disk of ZZ Tau IRS shadowed by a misaligned inner disk, as seen in HST NIR scattered light and supported by ALMA 12CO and radiative transfer modeling?  
  > "We present a new instance of shadowing on the outer disk around a very low mass star, ZZ Tau IRS." (abstract); "The brighter sides in the top and bottom halves are on the opposite sides, which we attributed to shadows cast by a misaligned inner disk." (abstract)
- Target **ZZ Tau IRS**: coordinates _not stated_; z/distance 130.7 pc (assumed)  
  > "is classified as a very low-mass (VLM) star and is situated at an assumed distance of 130.7 pc" (1 Introduction); distance from akeson2019 (Gaia DR3 distance of 105.7 pc not used because of poor astrometric solution, RUWE 2.490)  
  > "is classified as a very low-mass (VLM) star and is situated at an assumed distance of 130.7 pc" (1 Introduction)

## Data provenance

- ALMA projects: 2016.1.01511.S
- bands: lambda = 870 um (ALMA data from Hashimoto et al. 2021)  
  > "ZZ Tau IRS was observed with ALMA at $\lambda=870$ $\mu$m" (5.1 Comparison with ALMA (sub)mm results)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: ALMA data previously published in Hashimoto et al. 2021 (revisited, not newly reduced)  
  > "To explore additional observational evidence of the presence of a misaligned inner disk, we revisited ALMA" (3 Results)
- Line: 12CO J=3-2 (not stated)
- Other facility **HST/WFC3 F160W (Proposal 14181)**: Archival 1.6 um scattered light image of ZZ Tau IRS, observed 2017-08-23, exposure 1,596.9 s; the main dataset of the paper  
  > "The observations were executed on August 23, 2017, with an exposure time of 1,596.9 seconds." (2 HST archive data and PSF subtraction); "The broad-band filter F160W, centered on 1536.9 nm with a bandwidth of 268.3 nm, was employed for these observations." (2 HST archive data and PSF subtraction)
- Other facility **HST/WFC3 F160W PSF of U Car (Program 13335)**: Reference PSF used to subtract the PSF of ZZ Tau  
  > "U Car observed with WFC3/F160W as part of HST Program 13335" (2 HST archive data and PSF subtraction)
- Other facility **Gaia DR3**: Source of the PSF reference star (Gaia DR3 147869474824734208) in the same image as ZZ Tau IRS  
  > "we selected a PSF star, Gaia DR3 147869474824734208, in the same image as ZZ Tau IRS, with no visible stars within 3" (2 HST archive data and PSF subtraction)
- External data: ALMA 12CO (3-2) and 870 um dust continuum images of ZZ Tau IRS (including moment 1 map)  
  > "We revisited ALMA images of the $^{12}$CO brightness temperature and the dust continuum at $\lambda=870$ $\mu$m in Figure" (Appendix: ALMA results of ZZ Tau IRS) [from Hashimoto et al. 2021 (cite: Hashimoto2021zztauirs)]
- External data: Outer disk inclination of about 60 deg  
  > "representing a disk inclination of 60 deg (cite: Hashimoto2021zztauirs)" (4.1 Setup and results) [from Hashimoto et al. 2021 (cite: Hashimoto2021zztauirs)]
- External data: Total disk mass M_disk = 0.01 Msun used in the model  
  > "We set $M_{\rm disk}$ to 0.01 $M_\ensuremath{\odot}$ based on previous ALMA (sub)mm observation (cite: Hashimoto2021zztauirs)" (4.1 Setup and results) [from Hashimoto et al. 2021 (cite: Hashimoto2021zztauirs)]
- External data: Inner radius of the outer disk (60 au) taken from ALMA dust observations  
  > "based on ALMA dust observations (cite: Hashimoto2021zztauirs)" (4.1 Setup and results) [from Hashimoto et al. 2021 (cite: Hashimoto2021zztauirs)]
- External data: Assumed distance of 130.7 pc  
  > "is situated at an assumed distance of 130.7 pc" (1 Introduction) [from (cite: akeson2019)]
- External data: Nearly edge-on innermost disk proposed from SED, excluded from the model  
  > "The innermost disk is likely nearly edge-on (cite: white2004; furlan2011)" (1 Introduction) [from (cite: white2004; furlan2011)]
- External data: Small-grain dust model (composite of silicates and graphites, n(s) proportional to s^-3.5, 0.0025 to 0.2 um)  
  > "we utilize the standard interstellar-medium dust model for the small dust grains" (4.1 Setup and results) [from (cite: Kim1994SmallDust)]
- External data: Large-grain dust Model 2 (carbons and silicates, n(s) proportional to s^-3.5, 0.01 to 1000 um)  
  > "dust Model 2 in (cite: Wood2002LargeDust) for the large dust grains" (4.1 Setup and results) [from (cite: Wood2002LargeDust)]
- Simulation/model as data: HOCHUNK3D Monte Carlo radiative transfer model of a misaligned inner disk and shadowed outer disk, used to produce synthetic 1.6 um scattered light and 0.9 mm continuum images  
  > "we assess the aforementioned hypothesis by employing radiative transfer modeling through the Monte Carlo radiative transfer (MCRT) code" (4 Radiative transfer modeling)

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

- ALMA observations, calibration and imaging of ZZ Tau IRS are taken from the earlier paper; this paper only revisits the images  
  > "To explore additional observational evidence of the presence of a misaligned inner disk, we revisited ALMA" (3 Results) [from Hashimoto et al. 2021 (cite: Hashimoto2021zztauirs)]
- Disk structure and dust properties of the MCRT model  
  > "The disk structure and dust properties are described in (cite: hashimoto+15)." (4.1 Setup and results) [from (cite: hashimoto+15)]
- Two-layer disk model with small grains well-mixed with gas and large grains in the midplane  
  > "The MCRT code follows a two-layer disk model featuring small dust grains (up to micron size) well-mixed with the gas and large dust grains (up to millimeter size) in the disk midplane (cite: DAlessio2006Disk)." (4.1 Setup and results) [from (cite: DAlessio2006Disk)]
- Expected 'S' or 'Z' pattern in the velocity field (moment 1 minor axis tilt) as a signature of a misaligned inner disk  
  > "is expected to be tilted relative to the outer disk’s minor axis (cite: Rosenfeld2014Radialflow)" (3 Results) [from (cite: Rosenfeld2014Radialflow)]

### Not stated but needed to reproduce (our reading)

- ALMA calibration, imaging parameters (robust, beam, rms, CASA version) and spectral setup for the 12CO (3-2) and 870 um images; all deferred to Hashimoto et al. 2021
- How the 15 deg moment 1 minor axis tilt was measured (method, region, beam correction)
- How the 12CO brightness temperature map was derived and the beam and rms of the ALMA images shown in Figure 9
- HST image mask radius and shape, scaling factors and fitting method for the PSF subtraction, and the IRAF tasks used
- MCRT photon count, stellar parameters (Teff, luminosity, radius), grid, inner disk mass and inner disk scale height, dust grain composition fractions and the exact process for finding the 15 deg tilt
- Whether the MCRT code HOCHUNK3D and the model input files are available

## Analysis recipe

1. **Obtain and calibrate the HST/WFC3 F160W image**: Archival WFC3 data calibrated with calwf3, distortion-corrected with AstroDrizzle, final _drz product from MAST; flux in Jy from PHOTFNU  
  > "The data underwent calibration through the `calwf3` data processing pipeline." (2 HST archive data and PSF subtraction); "`AstroDrizzle`, part of the `Drizzlepac` package, was utilized for distortion correction." (2 HST archive data and PSF subtraction)
   - software: calwf3, AstroDrizzle, Drizzlepac
   - parameter: Stellar FWHM in field stars 0.23 arcsec  
  > "The stellar Full Width at Half Maximum (FWHM), measured in field stars within the field of view (FoV), was found to be 0.23$''$." (2 HST archive data and PSF subtraction)
   - fitting: _not stated_
   - validation: _not stated_
2. **Subtract PSFs of ZZ Tau and ZZ Tau IRS and smooth the image**: Subtract scaled U Car PSF (F160W) to remove the ZZ Tau spider diffraction pattern, then subtract a scaled PSF star (Gaia DR3 147869474824734208) from the ZZ Tau IRS image, then convolve with a 0.64 arcsec Gaussian kernel  
  > "the PSF of ZZ Tau, situated 35$\ensuremath{''}$ to the north" (2 HST archive data and PSF subtraction); "The PSF of ZZ Tau IRS was then subtracted by scaling the PSF star." (2 HST archive data and PSF subtraction)
   - software: IRAF
   - parameter: Gaussian kernel of 0.64 arcsec diameter to mitigate PSF-subtraction residuals  
  > "we convolved the image with a larger Gaussian kernel of 0.64$''$ in diameter to mitigate residuals from the PSF subtraction process" (2 HST archive data and PSF subtraction)
   - fitting: _not stated_
   - validation: Radial profile of the PSF reference star shows monotonic decrease while ZZ Tau IRS shows a dip, so the dark lane is not a subtraction artifact  
  > "As the PSF reference star exhibits monotonic decrease, the dip in the radial profile of ZZ Tau IRS is not attributed to artifacts" (3 Results)
3. **Identify dark lane and brightness asymmetries in the scattered light image**: Inspect the PSF-subtracted image and radial profiles along PA = 265 deg for ZZ Tau IRS and the PSF reference star  
  > "We assessed the existence of the dark lane by examining the radial profiles." (3 Results)
   - fitting: _not stated_
   - validation: _not stated_
4. **Check ALMA 12CO moment 1 map for a tilted inner disk minor axis**: Revisit the 12CO (3-2) moment 1 map from the earlier ALMA study and compare the inner disk minor axis with the outer disk minor axis  
  > "We found an approximate 15-deg tilt of the minor axis in the inner disk relative to the outer disk" (3 Results)
   - fitting: _not stated_
   - validation: Authors note the tilt may be affected by the beam size  
  > "may be affected by the beam size" (3 Results)
5. **Radiative transfer modeling of a misaligned inner disk shadowing the outer disk**: HOCHUNK3D MCRT with a two-layer disk, power-law surface density Sigma proportional to r^-1 with a gap between inner and outer disks; inner disk tilted until synthetic 1.6 um image matches HST; model image convolved with a 0.64 arcsec Gaussian and compared with the HST image  
  > "is tilted within the $yz$-plane by 5 to 30 deg towards the $-y$-direction." (4.1 Setup and results); "After several iterations, we set the tilt angle to 15 deg to achieve a good agreement with HST observations." (4.1 Setup and results)
   - software: HOCHUNK3D
   - parameter: Outer disk radius 300 au; inner radius of the outer disk 60 au; inner disk outer radius 1 au assumed  
  > "given its poorly constrained size" (4.1 Setup and results)
   - parameter: Mass fraction of large dust grains 0.9 of total dust mass  
  > "The mass fraction of large dust grains in the total dust mass is set to 0.9." (4.1 Setup and results)
   - parameter: Scale height h proportional to r^p with p = 1.15; at r = 100 au h = 1 au (large grains) and 7 au (small grains)  
  > "At $r=100$ au, we set $h$ to be 1 au for the large dust grain disk and 7 au for the small dust grain disk." (4.1 Setup and results)
   - parameter: Viewing direction theta = 0 deg, phi = 60 deg (inclination 60 deg)  
  > "Finally, we observe the system at $\theta=0$ deg and $\phi=60$ deg (i.e., the direction of the line of sight)" (4.1 Setup and results)
   - assumption: Gas-to-dust mass ratio of 100  
  > "assuming a gas-to-dust mass ratio of 100" (4.1 Setup and results)
   - assumption: Gap between inner and outer disks is devoid of material  
  > "To simplify the model, we assume this gap to be devoid of material." (4.1 Setup and results)
   - assumption: Edge-on innermost disk excluded from the model  
  > "we excluded the edge-on innermost disk proposed by (cite: white2004; furlan2011)" (4 Radiative transfer modeling)
   - fitting: Manual iteration of the tilt angle (5 to 30 deg explored), no sampler or likelihood  
  > "After several iterations, we set the tilt angle to 15 deg to achieve a good agreement with HST observations." (4.1 Setup and results)
   - validation: Visual comparison of model and HST image; the model does not reproduce the SED  
  > "it does not reproduce the SED" (4.2 Caveat)
6. **Compare NIR shadowing with ALMA 12CO brightness temperature and dust continuum**: Compare the NIR image with the ALMA 12CO brightness temperature and 870 um continuum; synthetic 0.9 mm continuum from the model checked for symmetry  
  > "Indeed our modeling in dust continuum at $\lambda=0.9$ mm in Figure [5](#fig:mcrt)(c) exhibits symmetric brightness distributions." (5.1 Comparison with ALMA (sub)mm results)
   - assumption: 12CO is optically thick and traces the upper disk surface; large grains are in the thin, vertically isothermal midplane  
  > "The $^{12}$CO is generally optically thick, effectively tracing the surface of the upper disk." (5.1 Comparison with ALMA (sub)mm results)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **calwf3** : HST WFC3 basic calibration  
  > "The data underwent calibration through the `calwf3` data processing pipeline." (2 HST archive data and PSF subtraction)
- **AstroDrizzle (Drizzlepac)** : Geometric distortion correction  
  > "`AstroDrizzle`, part of the `Drizzlepac` package, was utilized for distortion correction." (2 HST archive data and PSF subtraction)
- **IRAF** : Subtracting the PSF of ZZ Tau  
  > "was subtracted using the Image Reduction and Analysis Facility (cite: Tody1986IRAF)" (2 HST archive data and PSF subtraction)
- **HOCHUNK3D** : Monte Carlo radiative transfer modeling of the misaligned disk system  
  > "we assess the aforementioned hypothesis by employing radiative transfer modeling through the Monte Carlo radiative transfer (MCRT) code" (4 Radiative transfer modeling)
- **astropy** : Listed under Software; specific use not stated in the text  
  > "astropy (cite: Astropy2013; Astropy2018; Astropy2022), Numpy (cite: VanDerWalt2011)" (Software)
- **Numpy** : Listed under Software; specific use not stated in the text  
  > "Numpy (cite: VanDerWalt2011), IRAF (cite: Tody1986IRAF)" (Software)
- **Matplotlib** : Listed under Software; specific use not stated in the text  
  > "IRAF (cite: Tody1986IRAF), Matplotlib (cite: Hunter2007Matplotlib)" (Software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| HST stellar FWHM in field stars | 0.23 | not stated | arcsec | 1 | The stellar Full Width at Half Maximum (FWHM), measured in field stars within the field of view (FoV), was found to be 0.23$''$. |
| Dip radius of the dark lane in the radial profile at PA = 265 deg | about 1 | not stated | arcsec | 3 | We distinctly observed a dip at approximately $r=1$ arcsec in the radial profile of ZZ Tau IRS. |
| Tilt of inner disk minor axis relative to outer disk minor axis in 12CO moment 1 map | approximately 15 | not stated (may be affected by beam size) | deg | 4 | We found an approximate 15-deg tilt of the minor axis in the inner disk relative to the outer disk |
| Misalignment angle between inner and outer disks in the best-matching model | 15 | not stated (5 to 30 deg explored) | deg | 5 | After several iterations, we set the tilt angle to 15 deg to achieve a good agreement with HST observations. |
| Scale-height power-law index p in the model | 1.15 | not stated | dimensionless | 5 | We assumed $p=1.15$ as it yielded a favorable fit to the observations. |
| Precession timescale of the inner disk for a 10 Mjup planet at 0.05 au from the sublimation radius | approximately 10^3 | not stated | days | 0 | the precession timescale for the inner disk around ZZ Tau IRS is approximately 10$^3$ days. |

## Qualitative findings

- A dark lane separates the top and bottom halves of the highly inclined outer disk in the HST F160W image, and the brighter sides of the two halves are on opposite sides (southeast in the top half, northwest in the bottom half)  
  > "The southeast side is brighter in the top half, while the northwest side is brighter in the bottom half." (3 Results)
- No narrow shadows or cavity/gap are apparent in the HST image, possibly because of the 0.23 arcsec resolution  
  > "Additionally, no narrow shadows are apparent in the outer disk in Figure" (3 Results)
- The 870 um dust continuum asymmetry cannot be attributed to shadows and may reflect asymmetric dust surface density or dust properties  
  > "Consequently, the observed brightness asymmetry in the dust continuum cannot be attributed to shadows." (5.1 Comparison with ALMA (sub)mm results)

## Claim tuples

- H: The opposite-side brightness asymmetries in the top and bottom halves of the outer disk are shadows cast by a misaligned inner disk | E: PSF-subtracted HST WFC3 F160W image analysis | R: Brightness asymmetries on opposite sides separated by a dark lane | F: Shadows cast by a misaligned inner disk on the outer disk of ZZ Tau IRS | **supported**
- H: A misaligned inner disk is independently indicated in the ALMA 12CO velocity field | E: Inspect the 12CO (3-2) moment 1 map for a tilted minor axis of the inner disk | R: About 15 deg tilt of the inner disk minor axis relative to the outer disk | F: Presence of a misaligned inner disk, with the caveat that beam size may affect the tilt | **supported**
- H: A 15 deg misaligned inner disk can reproduce the HST morphology | E: HOCHUNK3D MCRT model with the inner disk tilted by 5 to 30 deg and compared with the HST image | R: Good agreement with the HST image at 15 deg, but the SED is not reproduced | F: The model reproduces the scattered light asymmetries but not the SED | **partially**
- H: Shadowing explains the brightness asymmetries seen in ALMA 12CO and 870 um continuum | E: Compare ALMA images with the NIR image and with model synthetic 0.9 mm continuum | R: Both ALMA images are brighter on the southeast side; model 0.9 mm continuum is symmetric | F: 12CO brightness temperature asymmetry can be explained by shadowing; continuum asymmetry cannot | **partially**

## Reasoning

- Why this data: HST archival NIR data and previously published ALMA CO data were used because shadows are seen in scattered light and a tilted velocity field gives independent evidence of misalignment  
  > "To explore additional observational evidence of the presence of a misaligned inner disk, we revisited ALMA" (3 Results)
- Why this method: Radiative transfer modeling was used to test whether a misaligned inner disk reproduces the shadowing  
  > "we assess the aforementioned hypothesis by employing radiative transfer modeling through the Monte Carlo radiative transfer (MCRT) code" (4 Radiative transfer modeling)
- Alternative: The nearly edge-on innermost disk proposed from SED was excluded because the HST image did not reveal the expected two narrow shadows  
  > "we excluded the edge-on innermost disk proposed by (cite: white2004; furlan2011)" (4 Radiative transfer modeling)
- How they decided it was enough: Tilt angle was iterated until good visual agreement with the HST image  
  > "After several iterations, we set the tilt angle to 15 deg to achieve a good agreement with HST observations." (4.1 Setup and results)
- Limitation (authors): The model does not reproduce the SED and a comprehensive parameter-space exploration was not done  
  > "it does not reproduce the SED" (4.2 Caveat)
- Limitation (authors): The 15 deg tilt in the moment 1 map may be affected by the beam size  
  > "may be affected by the beam size" (3 Results)
- Limitation (authors): Narrow shadows or a cavity/gap may be undetectable at the 0.23 arcsec resolution; only one epoch of HST/WFC3 NIR data exists, so variability was not tested  
  > "may be challenging due to the low angular resolution of 0.23$''$" (3 Results)
- Caveat (inferred, ours): The 15 deg misalignment is set by manual iteration without uncertainty or a degeneracy study against scale height, mass or inner disk size
- Caveat (inferred, ours): The moment 1 tilt comes from a different, earlier ALMA reduction and is only qualitatively quantified; inner disk is barely resolved
- Caveat (inferred, ours): Residual PSF-subtraction artifacts and central masking of r < 80 au limit the shadow morphology near the inner disk
- Caveat (inferred, ours): The model fails to reproduce the SED, so the inner disk geometry is not unique

## Reproducibility

- Data public (paper): HST data obtained from MAST (archival Proposal 14181)  
  > "Some/all of the data presented in this article were obtained from the Mikulski Archive for Space Telescopes (MAST) at the Space Telescope Science Institute." (Acknowledgments)
- Products in archive: _not stated_
- Missing: ALMA reduction and imaging details (deferred to Hashimoto et al. 2021)
- Missing: Stellar parameters and MCRT run settings; model inputs not released
- Missing: PSF subtraction scaling factors and masks
- Data volume (inferred): Small: one HST/WFC3 F160W drz image (about tens of MB) plus the published ALMA images; the ALMA part would be a few GB if re-reduced
- Score (inferred): 3/5, The HST data are public and the PSF subtraction and model geometry are described in useful detail, but the ALMA processing is inherited, the MCRT setup is incomplete and the main results are mostly qualitative morphology.
- Rediscovery candidate: no, Main results are qualitative image morphology and a hand-tuned model; ALMA is a minor, previously published supporting dataset.

## Links

- Method: Hashimoto et al. 2021, AJ, 161, 264 (cite: Hashimoto2021zztauirs) (Source of the ALMA 12CO and 870 um data and the disk parameters used in the model)
- Method: Hashimoto et al. 2015, ApJ, 799, 43 (cite: hashimoto+15) (Describes the disk structure and dust properties used in the MCRT model)
- Method: Whitney et al. 2013, ApJS, 207, 30 (cite: Whitney2013MCRT) (Reference for the HOCHUNK3D Monte Carlo radiative transfer code)
- Companion: Hashimoto et al. 2022, ApJ, 941, 66 (cite: Hashimoto2022ZZTauIRS) (Earlier study of dust grain growth in the ZZ Tau IRS crescent)
- Related: HST Proposal 14181
- Related: ALMA 2016.1.01511.S

## Checks

```json
{
 "quotes": 80,
 "quotes_ok": 80,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 101,
  "stated": 59,
  "rate": 0.584
 },
 "evidence_ok": true
}
```
