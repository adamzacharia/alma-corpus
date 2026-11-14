# Characterizing elusive, faint dusty star-forming galaxies: a lensed, optically undetected ALMA galaxy at z   3.3

`2016A&A...596A..75S` | Astronomy and Astrophysics 2016 | first author: Santini, P. | arXiv: 1610.08515 | DOI: 10.1051/0004-6361/201629339

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: high_z_galaxies
- Question: What are the physical properties (redshift, stellar mass, SFR, dust mass, magnification) of a serendipitously detected, optically undetected, lensed faint submm galaxy at z~3.3 in COSMOS, and is it representative of elusive dust-obscured star-forming galaxies missing from the cosmic SFH census?  
  > "We present here a serendipitous ALMA detection of a lensed, optically undetected $z$$\sim$3.3 faint SMG" (Introduction)
- Target **ALMA-detected SMG (lensed source) behind z=1.1458 galaxy, COSMOS**: coordinates RA=10:01:38.547 DEC=+02:37:36.70  
  > "located at RA=10:01:38.547 DEC=+02:37:36.70, which was undetected in the (cite: muzzin13) catalogue" (2 Target identification); "$z$ | 3.28 *(phot.)* | 1.1458 *(spec.)*" (Table 1); z/distance z=3.28 (photometric); lens z=1.1458 (spectroscopic)  
  > "located at RA=10:01:38.547 DEC=+02:37:36.70, which was undetected in the (cite: muzzin13) catalogue" (2 Target identification); "$z$ | 3.28 *(phot.)* | 1.1458 *(spec.)*" (Table 1); distance from SED fitting with PEGASE 2.0 (zphot.exe); lens from zCOSMOS Nov. 2015 release  
  > "located at RA=10:01:38.547 DEC=+02:37:36.70, which was undetected in the (cite: muzzin13) catalogue" (2 Target identification); "$z$ | 3.28 *(phot.)* | 1.1458 *(spec.)*" (Table 1)

## Data provenance

- ALMA projects: 2013.1.00034.S
- bands: Band 7  
  > "The spectral configuration covered a 8 GHz band centred around 343.463 GHz (Band 7)." (3 ALMA observations and data analysis)
- frequencies and spectral setup: 8 GHz band centred at 343.463 GHz; four 2 GHz spectral windows, 128 channels each  
  > "Each of the four 2 GHz spectral windows was sampled in 128 channels." (3 ALMA observations and data analysis)
- continuum bandwidth: _not stated_
- arrays: 12 m antennae (32 and 39 in the two runs)  
  > "The 12 m antennae (32 and 39) were distributed in compact configuration" (3 ALMA observations and data analysis)
- configurations: _not stated_
- baselines: ~150 m to 1.09 km  
  > "with baselines ranging from $\sim$150 m to 1.09 km" (3 ALMA observations and data analysis)
- angular resolution: 0.54x0.37 arcsec, PA -77.92 deg  
  > "the beam has a size of 0.54$\times$0.37 arcsec and a position angle of -77.92 deg" (3 ALMA observations and data analysis)
- max recoverable scale: _not stated_
- sensitivity: RMS 0.14 mJy/beam  
  > "The RMS is 0.14 mJy/beam" (3 ALMA observations and data analysis)
- time on source: 242 seconds  
  > "The on-source integration time was 242 seconds." (3 ALMA observations and data analysis)
- observing dates: 2014 July and December  
  > "split into two runs (2014 July and December)" (3 ALMA observations and data analysis)
- pi or archival as stated: Archival, PI N. Scoville  
  > "ALMA archival observations of this sky region were carried out as part of the Cycle 2 project 2013.1.00034.S (PI N. Scoville)" (3 ALMA observations and data analysis)
- Other facility **UltraVISTA-DR3**: Y, J, H, Ks photometry  
  > "we extracted the photometry from the UltraVISTA-DR3 Y, J, H, K$_s$ bands (cite: mccracken12)" (4 Optical and near-infrared photometry)
- Other facility **HST ACS**: I814 band (upper limit for SMG)  
  > "from the HST I814 band (cite: koekemoer07)" (4 Optical and near-infrared photometry)
- Other facility **Spitzer IRAC**: 3.6, 4.5, 5.0, 8.0 micron photometry  
  > "and from IRAC 3.6, 4.5, 5.0, 8.0$\mu$m  bands (cite: sanders07)" (4 Optical and near-infrared photometry)
- Other facility **Herschel PACS/SPIRE and Spitzer MIPS**: FIR photometry from PEP and HerMES, MIPS 24 micron  
  > "fit the MIPS 24$\mu$m  (cite: lefloch09) and *Herschel* photometry from the PEP (cite: lutz11) and HerMES (cite: oliver12) surveys" (2 Target identification)
- Other facility **VLA**: 20 cm radio flux 64+-11 uJy from catalogue  
  > "In the 20 cm VLA catalogue of (cite: bondi08) we found a radio counterpart of our faint SMG" (5 Physical properties)
- External data: UltraVISTA-DR1 Ks-selected catalogue photometry (30 bands) used for target selection  
  > "on the photometry from the UltraVISTA-DR1 $\rm K_s$–selected catalogue of (cite: muzzin13) (30 photometric bands)" (2 Target identification) [from (cite: muzzin13)]
- External data: Spectroscopic redshift of lens z=1.1458  
  > "spectroscopic redshift of $z$=1.1458 (from the Nov. 2015 zCOSMOS release, (cite: lilly09))" (2 Target identification) [from (cite: lilly09)]
- External data: VLA 20 cm radio flux of the counterpart  
  > "In the 20 cm VLA catalogue of (cite: bondi08) we found a radio counterpart of our faint SMG" (5 Physical properties) [from (cite: bondi08)]
- External data: Chandra X-ray catalogue (non-detection)  
  > "we looked for X-ray counterparts in the *Chandra* catalogue of (cite: civano16) but found none" (5 Physical properties) [from (cite: civano16)]
- External data: Main Sequence template used to model the lens FIR emission  
  > "We assumed that the optical galaxy can be described by the Main Sequence template of (cite: elbaz11)" (5 Physical properties) [from (cite: elbaz11)]

## Processing

### Calibration

- pipeline or manual: CASA pipeline (Pipeline-Cycle2-R1-B)  
  > "Observations were calibrated using the CASA pipeline version number 31667 (Pipeline-Cycle2-R1-B)." (3 ALMA observations and data analysis)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Titan and J1037-295  
  > "The flux calibrators were Titan and J1037-295, respectively." (3 ALMA observations and data analysis)
- flux scale uncertainty: 10% of flux added in quadrature to account for calibration error  
  > "we added 10% of the flux in quadrature to the RMS to take the error in the calibration into account" (3 ALMA observations and data analysis)
- self calibration: _not stated_

### Imaging

- task: CASA clean, mode mfs, CASA 4.5.1  
  > "The field was imaged using the *clean* task of CASA down to 0.3 mJy ($\sim$2-3$\times$ the thermal noise) with mode *’mfs’*" (3 ALMA observations and data analysis)
- deconvolver: _not stated_
- weighting robust: briggs (robust value not stated)  
  > "with mode *’mfs’* (cite: rau11) and weight *’briggs’*, using CASA version 4.5.1" (3 ALMA observations and data analysis)
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
- final beam: 0.54x0.37 arcsec, PA -77.92 deg  
  > "the beam has a size of 0.54$\times$0.37 arcsec and a position angle of -77.92 deg" (3 ALMA observations and data analysis)
- final rms: 0.14 mJy/beam  
  > "The RMS is 0.14 mJy/beam" (3 ALMA observations and data analysis)

### Inherited from earlier work

- Stellar-mass SED-fitting setup (parameter grid, priors) from Santini et al. 2015 Table 1 (BC03, exponentially declining SFH), except metallicity not super-solar  
  > "adopting the very same assumptions in terms of parameter grid, priors, etc. as detailed in Table 1 of (cite: santini15), except for the metallicity that cannot be super-solar" (5 Physical properties) [from (cite: santini15)]
- RMS map and background calibration via fake-source injection  
  > "we calibrated the RMS map and the background by injecting fake sources in empty areas of the images as described in (cite: merlin16)" (4 Optical and near-infrared photometry) [from (cite: merlin16)]
- SFR prescription combining UV and IR luminosity  
  > "The total SFR is computed by adding the obscured and unobscured components following the prescriptions adopted by (cite: santini09)" (5 Physical properties) [from (cite: santini09)]
- Dust mass inference technique  
  > "Dust masses were inferred by using the (cite: draineli07) model (with the same technique as adopted by (cite: santini14))" (2 Target identification) [from (cite: santini14)]

### Not stated but needed to reproduce (our reading)

- Briggs robust value, cell size, image size and masking for clean
- Which UltraVISTA/other files and cutouts exactly used; SExtractor parameter values
- uvmodelfit starting parameters and spw/channel selection for continuum
- Details of the lens model input (rotation velocity-K-band relation numbers) and the Monte Carlo realisation count
- Full PEGASE/BC03 grid parameters (depends on Santini15 Table 1)
- How the Herschel 100 micron upper limit was set in T-PHOT
- CIGALE module and parameter choices

## Analysis recipe

1. **Measure ALMA continuum flux and size**: Gaussian model fit directly to visibilities with uvmodelfit; checked by image-plane Gaussian fit deconvolved from beam  
  > "we measured the flux directly on the visibilities using the *uvmodelfit* task of CASA, assuming a Gaussian model." (3 ALMA observations and data analysis)
   - software: CASA uvmodelfit
   - parameter: 10% calibration error added in quadrature  
  > "we added 10% of the flux in quadrature to the RMS to take the error in the calibration into account" (3 ALMA observations and data analysis)
   - fitting: _not stated_
   - validation: Similar results from image-plane Gaussian fit  
  > "Similar results are obtained when fitting a Gaussian source on the image and then deconvolving from the synthesized beam." (3 ALMA observations and data analysis)
2. **Deblended optical/NIR/IRAC photometry**: Ks-band detection with SExtractor; template-fitting photometry with T-PHOT using I814 priors (Ks priors for IRAC); HST flux scaled via colour  
  > "we estimated the total flux in all UltraVISTA bands by adopting T-PHOT (cite: merlin15) on an area of 60x60 arcsec" (4 Optical and near-infrared photometry)
   - software: SExtractor, T-PHOT
   - assumption: ALMA source treated as point-like at Ks position in I814 prior  
  > "For this source, we assumed a point-like object at the position detected by SExtractor on the K$_s$-band image." (4 Optical and near-infrared photometry)
   - fitting: _not stated_
   - validation: T-PHOT covariance index ~1e-2 for Y and J indicates reliable fit  
  > "The covariance indexes for the Y and J bands are of the order of $10^{-2}$, indicating that the fit is reliable" (4 Optical and near-infrared photometry)
3. **Photometric redshift and stellar mass**: SED fit I814-IRAC with PEGASE 2.0 templates; stellar mass from BC03 with exponentially declining SFH at best-fit z  
  > "We fit the photometry from the I814 band to IRAC with the PEGASE 2.0 templates (cite: fioc97) using our own code *zphot.exe*" (5 Physical properties)
   - software: zphot.exe
   - assumption: Chabrier IMF; LCDM H0=70, Om=0.3, OL=0.7  
  > "we adopt the $\Lambda$-CDM concordance cosmological model (H$_0$ = 70 km/s/Mpc, $\Omega_M
= 0.3$ and $\Omega_{\Lambda} =
0.7$) and a (cite: chabrier03) IMF" (Introduction)
   - fitting: chi2 minimisation template fit  
  > "We fit the photometry from the I814 band to IRAC with the PEGASE 2.0 templates (cite: fioc97) using our own code *zphot.exe* (cite: fontana00; santini15)." (Physical properties)
   - validation: BC03 library gives z=3.25; FIR-radio SED of Yun & Carilli confirms z between 3 and 3.5  
  > "a value for the photometric redshift between 3 and 3.5 is also confirmed by the starburst FIR-radio SED of (cite: yun02)" (5 Physical properties)
4. **Deblend FIR fluxes and derive IR luminosity**: Assume 24um and part of Herschel flux belongs to lens (Elbaz Main Sequence template), subtract from Herschel photometry, iterate with Draine&Li fit (4 iterations); fit SMG templates of Michalowski10 and Pope08; adopt mean and dispersion of L_IR  
  > "We then subtracted the 24$\mu$m flux predicted by fitting the *Herschel*+ALMA bands of the ALMA-detected galaxy with the (cite: draineli07) templates from the total value and repeated the procedure, which converged after four iterations." (5 Physical properties)
   - parameter: 35% uncertainty on model added in quadrature  
  > "adding in quadrature an uncertainty of 35% on the model (cite: elbaz11)" (5 Physical properties)
   - assumption: All 24um emission initially attributed to the optical lens  
  > "the 24$\mu$m emission ($S_{24\mu m}=233\pm16$ $\mu$Jy) is completely associated with the optically detected source" (5 Physical properties)
   - fitting: template fits  
  > "We can therefore build the full I814-to-submm SED of the ALMA source and fit it with the SMG library of (cite: michalowski10)." (Physical properties)
   - validation: Result unchanged excluding Herschel bands  
  > "we verified that the result is unchanged if we exclude *Herschel* bands from the fit" (5 Physical properties)
5. **SFR and dust mass**: SFR_IR+UV = 1e-10 L_bol with L_bol = 2.2 L_UV + L_IR; radio SFR via Barger12; dust mass from Draine&Li fit and modified blackbody (beta=2)  
  > "gives $M_{dust}=5.97^{+0.13}_{-0.12} \cdot 10^8 M_\odot$ and $T_{dust}=37^{+4}_{-3}K$" (5 Physical properties)
   - parameter: kappa at 240um 5.17 cm2/g; 100um band excluded from MBB fit  
  > "absorption cross section per unit dust mass at 240$\mu$m of 5.17 cm$^2$/g" (5 Physical properties)
   - assumption: T~40K for ALMA-only dust mass  
  > "we also computed the dust mass from the ALMA flux only by assuming a temperature of $\sim$40K" (5 Physical properties)
   - fitting: _not stated_
   - validation: CIGALE full-SED fit as sanity check  
  > "As a sanity check, we also fit the full SED of our source with CIGALE" (5 Physical properties)
6. **Estimate lensing magnification**: Singular isothermal sphere lens with velocity dispersion from Tully-Fisher relation at z~1 (Tiley16), distribution of mu; +10% for ellipticity correction  
  > "The magnification factor arising from the lens has been estimated by modelling the lens as a singular isothermal sphere (cite: mason15)" (6 Discussion and conclusions)
   - parameter: sigma ~209+-20 km/s  
  > "The estimated velocity dispersion for the lens is $\sim$209$\pm$20 km/s." (6 Discussion and conclusions)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.5.1 (imaging); pipeline Pipeline-Cycle2-R1-B: calibration, clean imaging, uvmodelfit  
  > "using CASA version 4.5.1" (3 ALMA observations and data analysis)
- **SExtractor** : source detection and photometry  
  > "Detection is obtained with SExtractor (cite: bertin96)" (4 Optical and near-infrared photometry)
- **T-PHOT** : template-fitting photometry of blended sources  
  > "by adopting T-PHOT[^2] (cite: merlin15)" (4 Optical and near-infrared photometry)
- **zphot.exe** : photometric redshift and SED fitting  
  > "using our own code *zphot.exe* (cite: fontana00; santini15)" (5 Physical properties)
- **CIGALE** : full-SED sanity-check fit  
  > "we also fit the full SED of our source with CIGALE[^3] (cite: noll09)" (5 Physical properties)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| ALMA 870um integrated flux | 3.90 | 0.41 | mJy | 1 | The integrated flux over the source is $3.90 \pm 0.41$ mJy |
| Photometric redshift | 3.28 | not stated | dimensionless | 3 | We infer a photometric redshift of 3.28 |
| L_IR | 4.57e12 | 1.38e12 | Lsun | 4 | We obtain $L_{IR} = (4.57 \pm 1.38) \cdot 10^{12} L_\odot$. |
| SFR_IR+UV | 463 | 137 | Msun/yr | 5 | We infer $\rm SFR_{IR+UV} = 463 \pm 137 M_\odot/yr$. |
| Radio SFR | 237 | 41 | Msun/yr | 5 | translates into an SFR estimate of $237 \pm 41 M_\odot/yr$ |
| Dust mass (Draine&Li) | 1.12e9 | +0.16/-0.08 e9 | Msun | 5 | gives a dust mass of $M_{dust}=1.12^{+0.16}_{-0.08} \cdot 10^9 M_\odot$ |
| T_dust (modified blackbody) | 37 | +4/-3 | K | 5 | $T_{dust}=37^{+4}_{-3}K$ |
| Magnification adopted | 1.54 | +0.13/-0.08 | dimensionless | 6 | We therefore adopted a value of $1.54$ as an estimate of the magnification factor. |
| Starburstiness R_SB | 2 to 3.8 | not stated | dimensionless | 0 | is between 2 and 3.8 (depending on the adopted SFR tracer) |

## Qualitative findings

- The source is undetected in HST I814 but detected in all NIR bands; it is a dusty starburst-like, compact system (1.8x1.6 kpc) that would be missed in UV-based SFH censuses.  
  > "being undetected in optical, this galaxy is representative of the elusive dust-enshrouded star-forming population" (6 Discussion and conclusions)

## Claim tuples

- H: The ALMA flux comes from a distinct background galaxy rather than the optical z~1 galaxy | E: Astrometric comparison of ALMA, optical and VLA positions | R: ALMA source is 2 arcsec from the optical galaxy, offset not explained by astrometric accuracy, consistent with the VLA position | F: The SMG is a separate, optically undetected background galaxy at z~3.3 | **supported**
- H: The SMG is a faint, dust-rich star-forming galaxy with a starburst nature | E: SED fitting, SFR and dust mass estimates, lensing correction | R: SFR 463 Msun/yr (observed), intrinsic 154-300 Msun/yr, Mdust/Mstar ~0.03, R_SB 2-3.8 | F: Consistent with faint SMGs and starburst properties | **supported**

## Reasoning

- Why this data: Archival ALMA data serendipitously covered the target region of a dust-rich COSMOS galaxy.  
  > "which happened to be observed by ALMA" (2 Target identification)
- Why this method: _not stated_
- Alternative: Singular isothermal ellipsoid considered as more realistic lens model than SIS  
  > "a singular isothermal ellipsoid may be a more realistic parameterization" (6 Discussion and conclusions)
- How they decided it was enough: _not stated_
- Limitation (authors): Herschel fluxes of the SMG derived through indirect procedure with unverified assumptions; Y-band scatters ~2 sigma from best fit  
  > "Since *Herschel* fluxes are estimated through an indirect procedure and through assumptions that are not necessarily verified" (5 Physical properties)
- Caveat (inferred, ours): Single object; lens model crude (SIS from Tully-Fisher), magnification low and uncertain
- Caveat (inferred, ours): Photometric redshift broad chi2; no spectroscopic confirmation
- Caveat (inferred, ours): Deblending of Herschel flux depends on assumed lens template
- Caveat (inferred, ours): Short 242 s observation; CASA clean parameters incompletely specified

## Reproducibility

- Data public (paper): Archival ALMA project 2013.1.00034.S  
  > "ALMA archival observations of this sky region were carried out as part of the Cycle 2 project 2013.1.00034.S" (3 ALMA observations and data analysis)
- Products in archive: _not stated_
- Missing: Briggs robust, image size and cell
- Missing: SExtractor and T-PHOT configuration
- Missing: Lens modelling Monte Carlo details
- Data volume (inferred): ~5-20 GB (two short Band 7 runs, plus public ancillary images)
- Score (inferred): 5/5, ALMA data public and flux measurement simple, but SED/deblending analysis relies on external imaging, catalogs and unspecified parameters.
- Rediscovery candidate: yes, Public archival data, simple uvmodelfit flux and size measurement gives numeric result 3.90+-0.41 mJy.

## Links

- Method: (cite: merlin15) (T-PHOT template-fitting photometry)
- Method: (cite: santini15) (SED fitting setup (grid, priors))
- Method: (cite: merlin16) (RMS and background calibration with fake sources)
- Companion: (cite: scoville16) (Same ALMA data of COSMOS sources; source ID=288391, flux attributed to optical galaxy)
- Related: COSMOS
- Related: UltraVISTA
- Related: PEP
- Related: HerMES
- Related: zCOSMOS

## Checks

```json
{
 "quotes": 81,
 "quotes_ok": 81,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 9,
 "numeric_problems": 0,
 "fill": {
  "facts": 91,
  "stated": 65,
  "rate": 0.714
 },
 "evidence_ok": true
}
```
