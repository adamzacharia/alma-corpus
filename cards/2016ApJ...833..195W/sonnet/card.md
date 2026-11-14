# The SXDF-ALMA 2-arcmin<SUP>2</SUP> Deep Survey: Stacking Rest-frame Near-infrared Selected Objects

`2016ApJ...833..195W` | The Astrophysical Journal 2016 | first author: Wang, Wei-Hao | arXiv: 1609.08772 | DOI: 10.3847/1538-4357/833/2/195

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies, cosmology
- Question: How much of the 1.1 mm extragalactic background light is recovered by stacking rest-frame NIR (CANDELS 1.6 and 3.6 um) selected galaxies in deep ALMA imaging, and what does this imply for optically faint star formation?  
  > "A key question we would like to address with our SXDF-ALMA survey is how much of the 1.1 mm EBL can be directly detected (see H16) and recovered with stacking analyses." (4.2 Resolved EBL)
- Target **SXDF-ALMA 2 arcmin^2 field (CANDELS/SXDF)**: coordinates _not stated_; z/distance photometric redshifts, mostly z=0.5-3.0 for bright sources  
  > "Our SXDF-ALMA survey covers an area of 2.0 arcmin$^2$ within the footprint of the Cosmic Assembly Near-IR Deep Extragalactic Legacy Survey" (1 Introduction); distance from own photometric redshifts supplemented by Caputi et al. 2011  
  > "Our SXDF-ALMA survey covers an area of 2.0 arcmin$^2$ within the footprint of the Cosmic Assembly Near-IR Deep Extragalactic Legacy Survey" (1 Introduction)

## Data provenance

- ALMA projects: 2012.1.00756.S
- bands: Band 6 (1.1 mm, 274 GHz) continuum  
  > "We conducted Band 6 (1.1 mm, or 274 GHz) continuum imaging in the SXDF in ALMA Cycle 1, with a 19-pointing mosaic" (2.1 SXDF-ALMA Survey)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: 7.5 GHz total  
  > "a total bandwidth of 7.5 GHz, and a total observing time of 3.6 hr" (2.1 SXDF-ALMA Survey)
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.53'' x 0.41'' (PA = 64 deg)  
  > "synthesized beam of $0.53\ensuremath{''} \times 0.41\ensuremath{''}$ (PA = $64\ensuremath{^\circ}$)" (2.1 SXDF-ALMA Survey)
- max recoverable scale: _not stated_
- sensitivity: typical rms 62 uJy/beam in 1.58 arcmin^2 deep region  
  > "The area in this region is 1.58 arcmin$^2$ and the typical rms noise is 62 $\mu$Jy beam$^{-1}$." (2.1 SXDF-ALMA Survey)
- time on source: 3.6 hr total observing time  
  > "a total bandwidth of 7.5 GHz, and a total observing time of 3.6 hr" (2.1 SXDF-ALMA Survey)
- observing dates: _not stated_
- pi or archival as stated: PI K. Kohno, Cycle 1  
  > "(Program ID: 2012.1.00756.S; PI: K. Kohno)" (2.1 SXDF-ALMA Survey)
- Other facility **HST WFC3 / CANDELS**: NIR-selected source catalog for stacking positions  
  > "Our stacking analyses are based on the WFC3 detected objects in the CANDELS catalog of (cite: galametz13)." (2.2 Optical and NIR Data)
- Other facility **Spitzer IRAC (SEDS)**: 3.6 and 4.5 um fluxes at WFC3 positions  
  > "This catalog includes *Spitzer* IRAC fluxes of the WFC3 objects, extracted from the images of the *Spitzer* Extended Deep Survey" (2.2 Optical and NIR Data)
- Other facility **CFHT MegaCam**: U-band data for photometric redshifts  
  > "our own CFHT MegaCam $U$-band data obtained in a multi-year $U$-band imaging campaign for the SXDF" (2.2 Optical and NIR Data)
- External data: CANDELS WFC3 catalog with IRAC fluxes  
  > "Our stacking analyses are based on the WFC3 detected objects in the CANDELS catalog of (cite: galametz13)." (2.2 Optical and NIR Data) [from (cite: galametz13)]
- External data: COBE FIRAS 1.1 mm EBL values 18.5 and 25.1 Jy/deg^2  
  > "The 1.1 mm EBL measured by the *COBE* FIRAS experiments is 18.5 Jy deg$^{-2}$ (cite: puget96) or 25.1 Jy deg$^{-2}$ (cite: fixsen98)." (3.3 Results of Flux Stacking) [from (cite: puget96); (cite: fixsen98)]
- External data: Number counts and optically faint fraction (41%) from F16; ALMA source counts from H16  
  > "based the optically faint fraction in F16, for its larger sample size and higher ALMA sensitivity" (4.3 Optically Faint Sources) [from (cite: fujimoto16); (cite: hatsukade16)]

## Processing

### Calibration

- pipeline or manual: calibration and imaging done with CASA; details deferred to Kohno et al. in prep.  
  > "The calibration and imaging are performed with the Common Astronomy Software Application package (cite: mcmullin07)." (2.1 SXDF-ALMA Survey)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "The visibility data were naturally weighted to produce a CLEANed map" (2.1 SXDF-ALMA Survey)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: only region with effective coverage >75% of peak primary beam response used  
  > "we only consider the deep region where the effective coverage is greater than 75% of the peak primary beam response" (2.1 SXDF-ALMA Survey)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.53'' x 0.41'' (PA = 64 deg)  
  > "synthesized beam of $0.53\ensuremath{''} \times 0.41\ensuremath{''}$ (PA = $64\ensuremath{^\circ}$)" (2.1 SXDF-ALMA Survey)
- final rms: 62 uJy/beam typical  
  > "the typical rms noise is 62 $\mu$Jy beam$^{-1}$" (2.1 SXDF-ALMA Survey)

### Inherited from earlier work

- Observations and data reduction described elsewhere  
  > "the data reduction will be described in K. Kohno et al. (in prep., see also, (cite: kohno16))" (2.1 SXDF-ALMA Survey) [from K. Kohno et al. in prep.; (cite: kohno16)]
- Stacking method follows VLA stacking work  
  > "Our stacking analyses method is very similar to those developed by (cite: wang12) and (cite: to14) for Very Large Array images." (3.1 Method) [from (cite: wang12); (cite: to14)]
- Flux conversion 1.3 mm to 1.1 mm and 870 um to 1.1 mm  
  > "we assume $F_{1.1\,\rm mm} = 1.65 \times F_{1.3\,\rm mm}$ (F16) and $F_{1.1\,\rm mm} = F_{870\,\mu \rm m}/2.5$ (cite: oteo16)" (1 Introduction) [from F16; (cite: oteo16)]

### Not stated but needed to reproduce (our reading)

- CASA version and calibration details (flux calibrator, bandpass/gain calibrators)
- CLEAN threshold, masking, image size and cell size
- Exact source detection procedure and the list of >4-sigma source positions (H16)
- Photometric redshift code and templates
- Aperture correction values from dirty beam
- Random-aperture placement rules and exclusion radius for masks
- Conversion from stacked flux to EBL (area used) in detail

## Analysis recipe

1. **Select deep region and detect sources**: Restrict to >75% primary beam response; detect sources at >4 sigma and >4.5 sigma  
  > "There are 16 sources detected in this area at $>4~\sigma$, and eight sources at $>4.5~\sigma$." (2.1 SXDF-ALMA Survey)
   - software: CASA
   - fitting: _not stated_
   - validation: Spurious sources estimated from negative peaks (H16)  
  > "Up to 1/3 of the $>4~\sigma$ sources could be spurious, based on the number of negative peaks (H16)" (2.1 SXDF-ALMA Survey)
2. **Match NIR catalog to ALMA and mask bright sources**: 0.5'' counterpart search radius; mask the eight >4.5 sigma sources from stacks  
  > "We adopt a $0.5\ensuremath{''}$ search radius (approximately the beam FWHM) for our counterpart identification in this work." (2.2 Optical and NIR Data)
   - fitting: _not stated_
   - validation: _not stated_
3. **Image and flux stacking**: Average 1.1 mm images at NIR positions and measure 0.5'' diameter aperture fluxes; aperture correction from dirty beam assuming unresolved sources  
  > "we adopted a relatively small flux aperture, $D=0.5\ensuremath{''}$ (circles in Fig. [2](#fig2)). The aperture correction is derived based on the dirty beam assuming unresolved sources." (3.3 Results of Flux Stacking)
   - parameter: 2D Gaussian fit of stacked m3.6<23 image gave FWHM 0.76'' x 0.43''  
  > "The fitted Gaussian has a FWHM of $0.76\ensuremath{''} \times 0.43\ensuremath{''}$" (3.2 Results of Image Stacking)
   - assumption: Sources unresolved for aperture correction  
  > "The aperture correction is derived based on the dirty beam assuming unresolved sources." (3.3 Results of Flux Stacking)
   - fitting: _not stated_
   - validation: Artificial point sources injected (0.005-0.2 mJy), no systematic bias found  
  > "We did not find any systematic bias in the average of the $10^4$ mean fluxes for input fluxes ranging from 0.005 mJy to 0.2 mJy." (3.1 Method)
4. **Estimate background and uncertainty by Monte Carlo**: Random apertures equal in number to NIR sources, 10^5 repeats; mean subtracted as background, standard deviation as uncertainty; >4.5 sigma random apertures removed  
  > "We repeated this for $10^5$ times and calculated the mean and standard deviation of the $10^5$ mean fluxes." (3.1 Method)
   - fitting: _not stated_
   - validation: _not stated_
5. **Derive IR luminosity, SFR and EBL contribution**: IR luminosity from Chary & Elbaz SED, SFR with Kennicutt conversion at z=2; EBL = integrated flux divided by survey area; compare with COBE  
  > "if we adopt the luminosity-dependent dust spectral energy distribution (SED) in (cite: chary01), or $\sim3\times$ larger if assume an Arp 220 SED." (3.3 Results of Flux Stacking)
   - assumption: z=2; Chary & Elbaz 2001 SED; Kennicutt 1998 SFR conversion  
  > "The star formation rate (SFR) derived with the (cite: chary01) SED and a (cite: kennicutt98) conversion is $\sim 15~M_\ensuremath{\odot}$ yr$^{-1}$." (3.3 Results of Flux Stacking)
   - fitting: _not stated_
   - validation: _not stated_
6. **Optically faint fraction correction**: Apply 1/(1-0.41) completeness correction to NIR stacked EBL, using F16 fraction  
  > "This means a completeness correction of $1/(1-0.41)$ to our NIR stacked EBL." (4.3 Optically Faint Sources)
   - assumption: Optically faint population is 41% of faint-end EBL  
  > "We further assume that this population accounts for $\sim41\%$ of the EBL from the faint end" (4.3 Optically Faint Sources)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : calibration and imaging  
  > "The calibration and imaging are performed with the Common Astronomy Software Application package (cite: mcmullin07)." (2.1 SXDF-ALMA Survey)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Stacked 1.1 mm flux, m3.6<22 (28 sources) | 0.067 | 0.013 | mJy | 3 | $\langle F_{\rm1.1\,mm} \rangle = 0.067\pm0.013$ mJy |
| Stacked flux, m3.6=20-22 | 0.057 | 0.014 | mJy | 3 | the stacked flux of $0.057\pm0.014$ mJy corresponds to an infrared luminosity of $\sim9\times10^{10}~L_\ensuremath{\odot}$ |
| Stacked flux, m3.6<23 (49 sources) | 0.051 | 0.010 | mJy | 3 | $m_{\rm 3.6 \mu m} < 23$ / 49 / $0.051\pm0.010$ |
| Stacked flux, Ks-m4.5>1 (8 sources) | 0.131 | 0.024 | mJy | 3 | $K_s-m_{\rm 4.5 \mu m} >1$ / 8 / $0.131\pm0.024$ |
| Stacked flux, z=2-4 (13 sources) | 0.097 | 0.019 | mJy | 3 | $z = 2$–4 / 13 / $0.097\pm0.019$ |
| SFR at z=2 from stack | ~15 | not stated | Msun/yr | 5 | is $\sim 15~M_\ensuremath{\odot}$ yr$^{-1}$. |
| EBL from m3.6<23 sources with <4.5 sigma ALMA fluxes | 5.67 | 1.07 | Jy/deg^2 | 5 | the cumulative contributions are $5.67\pm1.07$ Jy deg$^{-2}$ from sources with $<4.5~\sigma$ ALMA fluxes |
| EBL from all m3.6<23 sources | 13.75 | 1.12 | Jy/deg^2 | 5 | $13.75\pm1.12$ Jy deg$^{-2}$ from all sources |
| Recovered EBL including >4 sigma ALMA sources (upper limit) | 20.3 | 1.2 | Jy/deg^2 | 5 | $16.1 \pm 1.2$ Jy deg$^{-2}$ and $20.3\pm1.2$ Jy deg$^{-2}$, respectively, for including $>4.5\sigma$ and $>4\sigma$ sources. |
| Combined EBL from H16 counts plus NIR stacking | 14.1 | not stated | Jy/deg^2 | 5 | Therefore, the combined EBL contribution from bright and faint sources is 14.1 Jy deg$^{-2}$. |
| EBL after optically faint correction | 17.5 to 24.2 | not stated | Jy/deg^2 | 6 | corresponding to 17.5 to 24.2 Jy deg$^{-2}$. |

## Qualitative findings

- Galaxies brighter at rest-frame NIR are brighter at 1.1 mm; sources fainter than m3.6=23 give no detection  
  > "galaxies fainter than $m_{\rm 3.6 \mu m} =23$ do not produce detectable 1.1 mm emission." (abstract)
- No evidence of bias from the bright AzTEC source  
  > "However, we do not find evidence of bias in our results caused by the bright source." (abstract)

## Claim tuples

- H: Does 1.1 mm flux correlate with rest-frame NIR brightness? | E: Stack ALMA 1.1 mm at CANDELS positions binned by 3.6 um magnitude | R: Stacked flux rises toward brighter magnitudes; null for m>23 | F: Suggests correlation between stellar mass and SFR, with outliers | **supported**
- H: Does the bright AzTEC source bias the stacking? | E: Compare flux and number density versus distance from AzTEC source | R: No elevated flux near the source; 2 sigma overdensity attributed to unrelated galaxies | F: No bias | **supported**
- H: How much of the 1.1 mm EBL is resolved, and what fraction of star formation is optically faint? | E: Sum ALMA-detected and stacked fluxes over survey area; compare to COBE and F16 | R: Up to 20.3 Jy/deg^2 recovered; optically faint correction gives 17.5-24.2 | F: About half of cosmic star formation may be missed by optical surveys | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Stacking used to reach faint population below the detection limit  
  > "Another way is to employ stacking analyses to obtain averaged mm/submm properties of high-redshift galaxies" (1 Introduction)
- How they decided it was enough: _not stated_
- Limitation (authors): Low S/N prevents meaningful size constraint; EBL values are upper limits; stacked sample misses optically faint sources  
  > "we do not think we can place a meaningful constraint on the source size." (3.2 Results of Image Stacking)
- Caveat (inferred, ours): Field selected around a bright AzTEC source, so not a blank field
- Caveat (inferred, ours): Optically faint fraction borrowed from F16 at a different wavelength and depth
- Caveat (inferred, ours): Single small field, cosmic variance
- Caveat (inferred, ours): Spurious fraction at 4-4.5 sigma affects EBL upper limit
- Caveat (inferred, ours): Stacked-flux to EBL conversion depends on assumed area and masking

## Reproducibility

- Data public (paper): ALMA data acknowledged by program ID; public status not explicitly stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2012.1.00756.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: CASA version and reduction details (in Kohno et al. in prep.)
- Missing: Source catalog from H16
- Missing: Own photometric redshift catalog and U-band data
- Missing: Exact aperture correction and random aperture procedure details
- Data volume (inferred): ~10-50 GB raw for one Cycle 1 Band 6 19-pointing mosaic (3.6 hr)
- Score (inferred): 3/5, Simple stacking recipe with CANDELS public catalog and public-ish ALMA data, but reduction details deferred and photo-z catalog not provided.
- Rediscovery candidate: no, Recipe depends on unpublished reduction and the authors' own photo-z catalog and source lists; results numeric but not fully reproducible from paper alone.

## Links

- Method: (cite: wang12); (cite: to14) (Stacking method)
- Companion: (cite: hatsukade16) H16 (SXDF-ALMA number counts and spurious fraction)
- Companion: (cite: yamaguchi16) (Detailed analysis of ALMA-detected sources with CANDELS counterparts)
- Companion: (cite: kohno16) (Survey observations and reduction)
- Related: CANDELS
- Related: SEDS
- Related: SXDF
- Related: Fujimoto et al. 2016 archival ALMA survey
- Related: Dunlop et al. 2016 HUDF ALMA

## Checks

```json
{
 "quotes": 57,
 "quotes_ok": 57,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 11,
 "numeric_problems": 0,
 "fill": {
  "facts": 78,
  "stated": 41,
  "rate": 0.526
 },
 "evidence_ok": true
}
```
