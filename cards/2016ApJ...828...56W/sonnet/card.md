# Discovery of a Galaxy Cluster with a Violently Starbursting Core at z = 2.506

`2016ApJ...828...56W` | The Astrophysical Journal 2016 | first author: Wang, Tao | arXiv: 1604.07404 | DOI: 10.3847/0004-637X/828/1/56

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: high_z_galaxies, galaxy_clusters_and_sz
- Question: Is the massive DRG overdensity CL J1001 at z~2.5 a collapsed, cluster-sized halo, and what are the star formation and quiescent properties of its members?  
  > "We report the discovery of a remarkable concentration of massive galaxies with extended X-ray emission at $z_{spec} = 2.506$" (abstract)
- Target **CL J1001+0220**: coordinates RA 10:00:57.13, Dec +02:20:11.83  
  > "The most significant outlier (centered at R.A.=10:00:57.13, decl. = +02:20:11.83)" (2 Target selection and multwavelength imaging); z/distance z = 2.506  
  > "The most significant outlier (centered at R.A.=10:00:57.13, decl. = +02:20:11.83)" (2 Target selection and multwavelength imaging); distance from biweight mean of spectroscopic redshifts of 17 members (CO and Halpha)  
  > "The most significant outlier (centered at R.A.=10:00:57.13, decl. = +02:20:11.83)" (2 Target selection and multwavelength imaging)

## Data provenance

- ALMA projects: 2011.0.00539.S
- bands: Band 7 (870 um)  
  > "observed as a candidate of lensed sources with ALMA at band-7 (870 $\mu$m)" (2 Target selection and multwavelength imaging)
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
- pi or archival as stated: _not stated_
- Other facility **IRAM-NOEMA**: CO(5-4) and CO(3-2) spectroscopic redshifts  
  > "we detected three sources in CO(5-4) down to integrated line fluxes of $\sim$0.6 Jy km s$^{-1}$ (5$\sigma$)" (3.1 IRAM-NOEMA)
- Other facility **VLT/KMOS**: Halpha redshifts for members  
  > "Seven of them are at $2.494 \leq z_{spec} \leq 2.512$, which are consistent with being cluster members." (3.2 VLT/K-band Multi-object Spectrograph (KMOS))
- Other facility **JVLA**: CO(1-0) redshifts and gas content  
  > "Eleven galaxies were detected in CO(1-0) down to integrated line fluxes 0.05 Jy km s$^{-1}$" (3.3 VLA)
- Other facility **Chandra and XMM-Newton**: extended X-ray emission and luminosity  
  > "We combined the latest Chandra and $XMM-Newton$ surveys of the COSMOS field" (4 XMM-Newton and Chandra imaging)
- Other facility **Herschel/SPIRE**: FIR flux densities of the core  
  > "with flux densities of $\sim$ 61, 77, and 66 mJy at SPIRE 250, 350, and 500 $\mu$m, respectively" (2 Target selection and multwavelength imaging)
- External data: ALMA 870 um flux densities of individual galaxies  
  > "flux densities for individual galaxies at 870 $\mu$m are from (cite: Bussmann:2015)" (Table 2 footnote) [from (cite: Bussmann:2015)]
- External data: 850 um SCUBA-2 flux of the core  
  > "the combined flux (at a slightly different wavelength, 850 $\mu$m) in the core is from (cite: Casey:2013)" (Table 2 footnote) [from (cite: Casey:2013)]

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

- ALMA data reduction and 870 um flux measurements  
  > "as described in (cite: Bussmann:2015)" (2 Target selection and multwavelength imaging) [from (cite: Bussmann:2015)]

### Not stated but needed to reproduce (our reading)

- ALMA calibration, imaging parameters and CASA version
- ALMA flux extraction method for individual galaxies (only quoted from Bussmann et al.)
- Photometry for 1.8 mm and 1.1 mm data sources
- Full details of VLA CO(1-0) reduction (deferred to future paper)

## Analysis recipe

1. **Fit core IR SED for L_IR and SFR**: Single-temperature blackbody plus mid-IR power law fit to 250 um-1.1 mm; cross-checked with Chary & Elbaz templates; SFR from Kennicutt 1998  
  > "we fit the 250 $\mu$m to 1.1mm data points with an FIR SED consisting of a coupled single-dust-temperature blackbody and mid-infrared power law described in (cite: Casey:2012a)" (6.1 Star Formation and Supermassive Black Hole Accretion in the Cluster Core)
   - assumption: Salpeter IMF  
  > "A (cite: Salpeter:1955) initial mass function (IMF) is adopted to derive stellar masses and SFRs." (1 Introduction)
   - fitting: _not stated_
   - validation: Two SED methods yielded similar results  
  > "The two methods yielded similar results, $L_{IR} = 10^{13.2\pm0.1} L_{\odot}$." (6.1 Star Formation and Supermassive Black Hole Accretion in the Cluster Core)
2. **Derive dust and gas mass of the core**: Graybody fit with beta fixed; dust-to-gas via mass-metallicity relation at z=2.5  
  > "During the fit, the dust emissivity index is fixed at $\beta = 1.5$ to reduce the number of free parameters." (6.1 Star Formation and Supermassive Black Hole Accretion in the Cluster Core)
   - assumption: Metallicity of M*~10^11.2 galaxy from Erb et al. 2006  
  > "For the conversion we assumed a metallicity corresponding to a galaxy with $M_{*} \sim 10^{11.2} M_{\odot}$" (6.1 Star Formation and Supermassive Black Hole Accretion in the Cluster Core)
   - fitting: _not stated_
   - validation: _not stated_
3. **Individual galaxy L_IR for ALMA detections**: Prior-based PSF-fitting at 24, 100, 160 um then IR SED fit with 870 um and 1.8 mm points  
  > "we performed a prior-based PSF-fitting using FASTPHOT (cite: Bethermin:2010) at shorter wavelengths" (6.1 Star Formation and Supermassive Black Hole Accretion in the Cluster Core)
   - software: FASTPHOT
   - fitting: _not stated_
   - validation: Sum of SFRs consistent with combined SED SFR  
  > "adds up to an SFR $\sim 2700 M_{\odot}$ yr$^{-1}$, which is consistent with our SFR estimation using the combined infrared SED" (6.1 Star Formation and Supermassive Black Hole Accretion in the Cluster Core)

## Software

- **GILDAS** : NOEMA calibration  
  > "Calibration was carried out with GILDAS" (3.1 IRAM-NOEMA)
- **CASA** : VLA data reduction and CLEAN imaging  
  > "were imaged using the CLEAN algorithm in CASA with a natural weighting scheme" (3.3 VLA)
- **FAST** : stellar mass SED fitting  
  > "The stellar mass of individual galaxies was derived from SED fitting with FAST" (5.1 Structure and masses of CL J1001)
- **FASTPHOT** : prior-based PSF-fitting photometry  
  > "we performed a prior-based PSF-fitting using FASTPHOT (cite: Bethermin:2010)" (6.1 Star Formation and Supermassive Black Hole Accretion in the Cluster Core)
- **GALFIT** : Sersic fits to HST sizes  
  > "With the algorithm GALFIT (cite: PengC:2010) we fitted the galaxy light distribution with a single Sérsic law" (6.2 Structural properties of member galaxies)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Cluster redshift | 2.506 | not stated | dimensionless | 0 | The biweight mean of the redshifts of these 21 galaxies yields $z_{mean} = 2.506$ |
| Velocity dispersion | 530 | 120 | km/s | 0 | $\sigma_{v} = 530 \pm 120$ km s$^{-1}$ |
| Core infrared luminosity | 10^13.2 | 0.1 dex | Lsun | 1 | $L_{IR} = 10^{13.2\pm0.1} L_{\odot}$ |
| Core SFR | ~3400 | not stated | Msun/yr | 1 | This infrared luminosity translates to an SFR of $\sim 3400 M_{\odot}$ yr$^{-1}$ |
| Core molecular gas mass | 5e11 | 1e11 | Msun | 2 | $M_{gas} = 5\pm1 \times 10^{11} M_{\odot}$ |
| Halo mass M200c | 10^13.9 | 0.2 dex | Msun | 0 | our best estimate of the halo mass is $M_{200c} = 10^{13.9 \pm 0.2} M_{\odot}$ |
| X-ray luminosity 0.1-2.4 keV | 8.8e43 | 2.6e43 | erg/s | 0 | $L_{0.1 - 2.4~\mathrm{keV}} = 8.8\pm2.6 \times 10^{43}$ erg s$^{-1}$ |

## Qualitative findings

- Core is dominated by star-forming galaxies; quiescent fraction ~20%, similar to field.  
  > "the quiescent fraction in CL J1001 is significantly lower, $\sim 20\%$, indistinguishable from that in the field at the same redshifts." (6.1 Star Formation and Supermassive Black Hole Accretion in the Cluster Core)

## Claim tuples

- H: Is the overdensity embedded in a collapsed cluster-sized halo? | E: X-ray, velocity dispersion and stellar mass halo estimates | R: M200c=10^13.9±0.2 Msun with extended X-ray emission | F: Most distant X-ray-detected cluster | **supported**
- H: Does the core have elevated star formation and starburst fraction? | E: IR SED fits using ALMA and other submm data | R: SFR ~3400 Msun/yr, starburst fraction ~25% | F: Core is rapidly building up | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: X-ray emission from star formation (at most ~14%) or inverse Compton from central radio source judged unlikely  
  > "Therefore we estimate that at most $\sim$14% of the X-ray flux originates from star formation." (4 XMM-Newton and Chandra imaging)
- How they decided it was enough: _not stated_
- Limitation (authors): Velocity dispersion uses only star-forming members  
  > "We are aware that the sample used to estimate the velocity dispersion only includes SFGs." (5.1 Structure and masses of CL J1001)
- Caveat (inferred, ours): Starburst fraction of 2/8 has tiny-number statistics
- Caveat (inferred, ours): Halo mass depends on scaling relations calibrated at lower z
- Caveat (inferred, ours): Core SFR from unresolved SED may include blending

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Code: KMOS reduction scripts at github.com/cschreib/kmos-scripts  
  > "Detailed procedure and related codes are fully described here: https://github.com/cschreib/kmos-scripts" (3.2 VLT/K-band Multi-object Spectrograph (KMOS))
- Missing: ALMA processing details
- Missing: VLA reduction details
- Data volume (inferred): small for ALMA (single archival Band 7 pointing); multi-facility overall
- Score (inferred): 2/5, ALMA used only through published fluxes; multi-facility analysis with many deferred details.
- Rediscovery candidate: no, ALMA role is minor and recipe incomplete.

## Links

- Method: (cite: Casey:2012a) (IR SED fitting method)
- Companion: (cite: Bussmann:2015) (ALMA Band 7 observations and 870 um fluxes)
- Related: COSMOS
- Related: CANDELS-Herschel

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
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 71,
  "stated": 29,
  "rate": 0.408
 },
 "evidence_ok": true
}
```
