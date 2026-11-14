# GOODS-ALMA: Using IRAC and VLA to probe fainter millimeter galaxies

`2020A&A...643A..53F` | Astronomy and Astrophysics 2020 | first author: Franco, M. | arXiv: 2005.03040 | DOI: 10.1051/0004-6361/202038310

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies
- Question: Can cross-matching 3.5-4.8 sigma ALMA 1.1 mm detections with IRAC, VLA and K-band catalogs yield a robust supplementary catalog of fainter millimeter galaxies, and how do their properties differ from the Main Catalog?  
  > "Here we extend the detection limit to 3.5-$\sigma$ by cross-matching the ALMA detections with catalogs in the near and mid-IR." (Introduction)
- Target **GOODS-ALMA field (GOODS-South)**: coordinates RA 03h32m30.0s, Dec -27d48m00s (J2000)  
  > "It is centered at $\alpha$ = 3$^{\rm h}$ 32$^{\rm m}$ 30.0$^{\rm s}$, $\delta$ = -27$\degree$ 48$\ensuremath{'}$ 00$\ensuremath{''}$ (J2000)." (2.1 ALMA data); z/distance sources at z = 0.65 – 4.73  
  > "It is centered at $\alpha$ = 3$^{\rm h}$ 32$^{\rm m}$ 30.0$^{\rm s}$, $\delta$ = -27$\degree$ 48$\ensuremath{'}$ 00$\ensuremath{''}$ (J2000)." (2.1 ALMA data); distance from spectroscopic redshifts where available, otherwise ZFOURGE photometric redshifts (CANDELS for AGS35)  
  > "It is centered at $\alpha$ = 3$^{\rm h}$ 32$^{\rm m}$ 30.0$^{\rm s}$, $\delta$ = -27$\degree$ 48$\ensuremath{'}$ 00$\ensuremath{''}$ (J2000)." (2.1 ALMA data)

## Data provenance

- ALMA projects: 2015.1.00543.S
- bands: Band 6, 1.1 mm  
  > "The survey performed using band 6 covers an effective area of 69 arcmin$^2$" (2.1 ALMA data)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: original 0.2'' (0.29'' mosaic), tapered to 0.60'' FWHM circular beam  
  > "The original 0.2$''$ angular resolution was tapered with a homogeneous and circular synthesized beam of $0.60\ensuremath{''}$ Full-Width Half Maximum" (2.1 ALMA data)
- max recoverable scale: _not stated_
- sensitivity: median ~0.18 mJy/beam in the 0.60'' mosaic  
  > "around a median value of $\simeq$ 0.18 mJy beam$^{-1}$" (2.1 ALMA data)
- time on source: _not stated_
- observing dates: August-September 2016  
  > "between August and September 2016" (2.1 ALMA data)
- pi or archival as stated: PI: D. Elbaz  
  > "(Project ID: 2015.1.00543.S; PI: D. Elbaz)" (2.1 ALMA data)
- Other facility **Spitzer/IRAC (S-CANDELS)**: 3.6 and 4.5 micron catalog used for counterparts  
  > "catalog of galaxies detected at 3.6 and 4.5 $\mu$m" (2.2.1 IRAC catalog)
- Other facility **VLA 3 GHz**: radio catalog, ~0.3'' resolution, RMS 2.1 uJy/beam  
  > "at a frequency of 3 GHz (10 cm) and an angular resolution of $\sim$0.3$''$ for a total of 177 hours" (2.2.3 Radio catalog)
- Other facility **ZFOURGE/Straatman K-band**: Ks catalog, photometric redshifts and stellar masses  
  > "We use the 2.2 $\mu$m catalog described in (cite: Straatman2016)" (2.2.2 Near-infrared Ks-band catalog)
- Other facility **HST/WFC3 CANDELS H-band**: H160 catalog, CANDELS redshifts and masses  
  > "The point source catalog reaches a 5-$\sigma$ depth of 28.16 mag (AB) in the $H_{160}$ filter" (2.2.4 HST H-band catalog)
- Other facility **Pan-STARRS DR2**: astrometric reference tied to Gaia  
  > "We take advantage of the Panoramic Survey Telescope and Rapid Response System (Pan-STARRS) Data Release 2" (3 Astrometric correction)
- External data: IRAC catalog of galaxies  
  > "We use the *Spitzer*-Cosmic Assembly Near-Infrared Deep Extragalactic Survey (*S*–CANDELS; (cite: Ashby2015)) catalog" (2.2.1 IRAC catalog) [from Ashby2015]
- External data: ZFOURGE K-band catalog, photometric redshifts and stellar masses  
  > "We use the 2.2 $\mu$m catalog described in (cite: Straatman2016)" (2.2.2 Near-infrared Ks-band catalog) [from Straatman2016]
- External data: HST H-band CANDELS catalog  
  > "(measured within a fixed aperture of 0.17$''$; (cite: Guo2013))" (2.2.4 HST H-band catalog) [from Guo2013]
- External data: Main Catalog ALMA sources AGS1-AGS23  
  > "The main ALMA catalog consists of 20 sources detected above 4.8 $\sigma$ ." (4.1 ALMA Main Catalog) [from Franco2018]
- External data: Redshifts and masses of the optically dark galaxies AGS24 and AGS4/11/15/17  
  > "This galaxy will be presented in detail in (cite: Zhou2020)" (4.2.2 Optically dark galaxies) [from Zhou2020]

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

- task: BLOBCAT blind source extraction (sigma_p=4.8, sigma_f=2.7 for the Main Catalog)  
  > "It is a blind source extraction down to 4.8 $\sigma$, using BLOBCAT (cite: Hales2012)." (4.1 ALMA Main Catalog)
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: tapered to 0.60'' FWHM circular beam  
  > "tapered with a homogeneous and circular synthesized beam of $0.60\ensuremath{''}$" (2.1 ALMA data)
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

- Imaging, tapering, calibration and Main Catalog construction follow the first GOODS-ALMA paper  
  > "This paper extends our previous analysis ((cite: Franco2018), hereafter ) of a deep continuum 1.1 mm survey" (Introduction) [from Franco2018]
- Size limit formula for minimum measurable size  
  > "We use the formula given by (cite: Marti-Vidal2012) (as in ) to determine the minimum size" (5.2 Flux and size measurements) [from Marti-Vidal2012]
- Scaling factors to convert survey RMS to 1.1 mm  
  > "Using the same scaling factors as those presented in , these depths correspond to RMS $\simeq$ 52 $\mu$Jy" (4.2.1) [from Franco2018]
- UVJ star-forming selection definition  
  > "using the same definition as in (see Fig. [10](#mass_redshift_combined))" (6.2 Stellar masses) [from Franco2018]

### Not stated but needed to reproduce (our reading)

- ALMA calibration and imaging details (CASA version, weighting, robust, clean parameters) deferred to Franco2018
- Tapering parameters (uv-taper values)
- Exact injection-recovery source distribution and flux model
- IRAC deblending GALFIT model parameters
- FAST++ input photometry and grid parameters
- Radio catalog is unpublished (Rujopakarn et al., in prep.)
- uvmodelfit starting parameters

## Analysis recipe

1. **Correct HST astrometry**: Compare HST and Pan-STARRS positions of 375 common sources, subtract global offset, then derive local distortion map from sliding median offsets  
  > "Each arrow represents the median offset between Pan-STARRS and HST positions, for a sliding median containing on average 15 sources." (3 Astrometric correction)
   - parameter: global offset DeltaRA = -96 ± 83 mas, DeltaDec = 252 ± 107 mas  
  > "$\Delta$RA = -96 $\pm$ 83 mas and $\Delta$Dec = 252 $\pm$ 107 mas" (3 Astrometric correction)
   - fitting: _not stated_
   - validation: VLA vs Pan-STARRS and ALMA vs VLA show no offset  
  > "we find no offset between our ALMA sources (both the Main catalog presented in and the supplementary catalog presented in the following) and their VLA counterparts" (3 Astrometric correction)
2. **Blind extraction at 3.5 sigma and counterpart cross-match**: Extract sources down to 3.5 sigma in the 0.60'' image, cross-match with IRAC, VLA and K-band; keep IRAC within 0.3'' or within 0.7'' plus radio counterpart  
  > "an IRAC counterpart either *(i)* closer than 0.3$''$ or *(ii)* closer than 0.7$''$ but associated with a radio counterpart in the 3 GHz catalog." (4.2.1)
   - software: BLOBCAT, GALFIT
   - parameter: cross-match radius 0.60'' for VLA and K-band; IRAC considered within 0.7''  
  > "It is equal to 0.60$''$, the FWHM of the tapered 1.1 mm ALMA image, for the cross-match with the VLA and ZFOURGE $K$-band catalogs." (4.2.1)
   - fitting: _not stated_
   - validation: Negative-image purity, Monte Carlo random association probabilities, comparison with ASAGAO/HUDF/ASPECS, KS test of stellar masses  
  > "We randomly define a position within GOODS–South and then measure the distance to its closest IRAC neighbor" (4.2.1)
3. **Measure fluxes and sizes**: uvmodelfit circular Gaussian in uv-plane; sizes below theta_min treated as unresolved and peak flux used  
  > "Flux densities of the Supplementary Catalog sources were measured by fitting the light profiles with a circular Gaussian in the *uv*-plane, using `uvmodelfit` in `CASA`" (5.2 Flux and size measurements)
   - software: CASA
   - parameter: theta_min = 0.88 theta_beam/sqrt(S/N), theta_beam=0.60''  
  > "\theta_{min}\,\simeq\,0.88\frac{\theta_{beam}}{\sqrt{\text{S/N}}}" (5.2 Flux and size measurements)
   - assumption: No flux boosting correction applied (10% at 0.9 mJy)  
  > "we decided not to apply the flux boosting correction to our results" (5.2 Flux and size measurements)
   - fitting: _not stated_
   - validation: Injection-recovery test for flux boosting  
  > "we compared the recovered flux to the injected flux" (5.2 Flux and size measurements)
4. **Derive redshifts and stellar masses**: Adopt spectroscopic z, else ZFOURGE photometric z; masses from ZFOURGE x1.7 to Salpeter; refit with FAST++ when new redshifts  
  > "We used the code `FAST++`[^3] based on `FAST` (cite: Kriek2009)." (5.1 Redshifts and stellar masses)
   - software: FAST++
   - assumption: exponentially declining SFH, Calzetti attenuation law, Salpeter IMF  
  > "Stellar masses have been derived from models assuming exponentially declining star-formation histories and a dust attenuation law as described by (cite: Calzetti2000)." (5.1 Redshifts and stellar masses)
   - fitting: _not stated_
   - validation: Median difference of ~8% vs ZFOURGE masses  
  > "We find a median difference of $\sim$8%." (5.1 Redshifts and stellar masses)

## Software

- **BLOBCAT** : blind source extraction  
  > "using BLOBCAT (cite: Hales2012)" (4.1 ALMA Main Catalog)
- **CASA (uvmodelfit)** : uv-plane Gaussian fits of fluxes and sizes  
  > "using `uvmodelfit` in `CASA` (cite: McMullin2007)" (5.2 Flux and size measurements)
- **GALFIT** : Sersic modeling of IRAC neighbor of AGS25  
  > "We subtracted it from the IRAC image by modeling a Sérsic profile with `GALFIT` (cite: Peng2010)" (4.2.2)
- **FAST++** : SED fitting for stellar masses  
  > "We used the code `FAST++`[^3] based on `FAST` (cite: Kriek2009)." (5.1 Redshifts and stellar masses)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Supplementary Catalog size | 16 | not stated | sources | 2 | In total we find 16 galaxies in the Supplementary Catalog that bring the total sample of GOODS-ALMA 1.1 mm sources to 35 galaxies. |
| Median redshift, Supplementary Catalog | 2.40 | not stated | dimensionless | 4 | $z_{med,SC}$ = 2.40 compared to that of the Main Catalog $z_{med,MC}$ = 2.73 |
| Median stellar mass, Supplementary Catalog | 7.6e10 | not stated | Msun | 4 | M$_{\star}^{\rm Supp}$ = 7.6$\times$10$^{10}$M$_\odot$ |
| Median 1.1 mm FWHM size, Supplementary vs Main | 0.32'' vs 0.18'' | not stated | arcsec | 3 | The median ALMA 1.1 mm FWHM of the galaxies in the Supplementary Catalog is indeed 0.32$''$ as compared to 0.18$''$ |
| Half-light radius, Supplementary vs Main | 1.3 kpc vs 0.65 kpc | not stated | kpc | 3 | is 1.3 kpc as compared to only 0.65 kpc for the Main Catalog |
| Purity within 0.7'' of IRAC sources | 48 | not stated | % | 2 | we get a much improved purity of 48% with 15 negative peaks |
| KS test p-value, massive counterparts in positive vs negative image | 1.2e-2 | not stated | dimensionless | 2 | A Kolmogorov-Smirnov (KS) test on these data gives a p-value of 1.2$\times$10$^{-2}$ between these two samples |
| Fraction of massive SFGs (logM 11-12, 2<z<4) detected | 38 (12/32) | not stated | % | 4 | GOODS-ALMA detects approximately 38% (12/32) of the most massive star-forming galaxies |

## Qualitative findings

- Six optically dark galaxies in the survey are all at z >= 3.5.  
  > "appear to be particularly distant ($z$ $\ge$ 3.5)" (4.2.2)
- HST astrometry has a global plus local distortion offset that needs correcting.  
  > "a local shift that results in the equivalent of a distortion map that was artificially introduced" (7 Conclusions)

## Claim tuples

- H: IRAC and VLA counterparts allow robust ALMA detections below 4.8 sigma | E: Cross-matching 3.5-4.8 sigma peaks with IRAC/VLA, with negative-image and deeper-survey checks | R: 16 sources with purity checks; all 3 in deeper surveys recovered; KS p=0.012 vs 0.88 after removal | F: The Supplementary Catalog is robust | **supported**
- H: Fainter ALMA sources differ in properties from the Main Catalog | E: Compare redshift, mass and size distributions | R: Lower median mass, wider redshift range, sizes ~twice larger | F: Pushing the limit reaches lower-mass galaxies with more extended dust emission | **supported**
- H: HST astrometry needs a local distortion correction | E: Compare HST, Pan-STARRS, VLA and ALMA positions | R: Spatially coherent residual offsets up to >0.15'' | F: Correction is needed to avoid wrong counterparts | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Asymmetric Gaussian fit rejected in favour of circular Gaussian to limit free parameters at low S/N  
  > "we chose to fit a circular Gaussian rather than an asymmetric Gaussian, in order to limit the number of free parameters" (5.2 Flux and size measurements)
- How they decided it was enough: _not stated_
- Limitation (authors): Requiring an IRAC counterpart may reject real sources and bias toward massive galaxies.  
  > "this criterion may lead us to reject real ALMA sources without any IRAC counterpart with the possible consequence of biasing our sample toward the most massive galaxies" (4.2.1)
- Limitation (authors): Peak fluxes for unresolved sources may be underestimated by about 20%.  
  > "they may be lower by about 20 %" (5.2 Flux and size measurements)
- Caveat (inferred, ours): Selection requires IRAC/radio counterparts so completeness is unquantified
- Caveat (inferred, ours): Counterpart purity rests on negative-image statistics at low S/N
- Caveat (inferred, ours): Flux boosting not corrected
- Caveat (inferred, ours): Radio catalog unpublished

## Reproducibility

- Data public (paper): ALMA project ID given; HST astrometric corrections released on GitHub  
  > "are given at <https://github.com/maximilienfranco/astrometry/>" (3 Astrometric correction)
- Products in archive: _not stated_
- Code: Astrometric correction table for Guo2013 sources on GitHub  
  > "<https://github.com/maximilienfranco/astrometry/>" (3 Astrometric correction)
- Missing: Calibration and imaging recipe in Franco2018
- Missing: Unpublished 3 GHz VLA catalog
- Missing: Injection simulation details
- Data volume (inferred): ~100s GB raw for a 69 arcmin2 mosaic; reproduction from the final mosaic would be tens of GB
- Score (inferred): 3/5, Catalog-level recipe is clear but the ALMA imaging is deferred to Franco2018 and the radio catalog is unpublished.
- Rediscovery candidate: no, Depends on the previous paper's imaging and an unpublished radio catalog.

## Links

- Method: Franco2018 (Data reduction, imaging and Main Catalog)
- Method: Marti-Vidal2012 (minimum measurable size formula)
- Method: Hales2012 (BLOBCAT source extraction)
- Companion: Franco2020 (Companion analysis of the full GOODS-ALMA sample properties)
- Companion: Zhou2020 (Optically dark galaxies)
- Related: ASAGAO
- Related: ASPECS
- Related: HUDF ALMA survey
- Related: CANDELS
- Related: ZFOURGE
- Related: S-CANDELS

## Checks

```json
{
 "quotes": 62,
 "quotes_ok": 62,
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
  "facts": 84,
  "stated": 49,
  "rate": 0.583
 },
 "evidence_ok": true
}
```
