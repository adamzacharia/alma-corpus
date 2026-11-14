# ALMA Deep Field in SSA22: A Concentration of Dusty Starbursts in a z = 3.09 Protocluster Core

`2015ApJ...815L...8U` | The Astrophysical Journal Letters 2015 | first author: Umehata, H. | arXiv: 1510.08861 | DOI: 10.1088/2041-8205/815/1/L8

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies, agn_and_quasars, cosmology
- Question: Are dusty starburst SMGs overabundant in the node of the z=3.09 SSA22 protocluster, and how do they relate to AGN and Lyman-alpha blobs?  
  > "In this letter, we present the first results focusing on the SMGs at $z=3.09$." (1 Introduction)
- Target **ADF22 (SSA22 protocluster core)**: coordinates RA 22h17m34s, Dec +00d17m00s (J2000)  
  > "we observed a $2^\prime \times 3^\prime$ area centered at RA (J2000) = 22$^{\rm h}$17$^{\rm m}$34$^{\rm s}$, Dec (J2000) = $+00^\circ17^{\prime}00^{\prime\prime}$ using 103 discrete pointing fields" (2 Observations and Data Reduction); z/distance z=3.09  
  > "we observed a $2^\prime \times 3^\prime$ area centered at RA (J2000) = 22$^{\rm h}$17$^{\rm m}$34$^{\rm s}$, Dec (J2000) = $+00^\circ17^{\prime}00^{\prime\prime}$ using 103 discrete pointing fields" (2 Observations and Data Reduction); distance from spectroscopic redshifts from archival catalogs  
  > "we observed a $2^\prime \times 3^\prime$ area centered at RA (J2000) = 22$^{\rm h}$17$^{\rm m}$34$^{\rm s}$, Dec (J2000) = $+00^\circ17^{\prime}00^{\prime\prime}$ using 103 discrete pointing fields" (2 Observations and Data Reduction)

## Data provenance

- ALMA projects: 2013.1.00162.S
- bands: Band 6 (1.1 mm), central frequency 263 GHz  
  > "We utilized the band 6 receiver with the TDM correlator to select a central frequency of 263 GHz (1.1 mm)." (2 Observations and Data Reduction)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: 12m, 33–36 antennas  
  > "using 33–36 12m anntenas" (2 Observations and Data Reduction)
- configurations: C34-4  
  > "The array configuration was C34-4, which results in baseline lengths of 20–450 m." (2 Observations and Data Reduction)
- baselines: 20–450 m  
  > "baseline lengths of 20–450 m" (2 Observations and Data Reduction)
- angular resolution: 0.53"x0.50" (PA -84 deg)  
  > "The resulting map has a synthesized beam of $0.^{\prime\prime}53\times0.^{\prime\prime}50$ (P.A. $= -84$ deg)" (2 Observations and Data Reduction)
- max recoverable scale: _not stated_
- sensitivity: typical rms 0.07 mJy/beam  
  > "a typical rms revel of 0.07 mJy beam$^{-1}$" (2 Observations and Data Reduction)
- time on source: 2.0–2.5 min per pointing  
  > "The on-source time per pointing is 2.0–2.5 min." (2 Observations and Data Reduction)
- observing dates: 6–10 June 2014  
  > "(6–10 June 2014)" (2 Observations and Data Reduction)
- pi or archival as stated: _not stated_
- Other facility **Chandra**: X-ray data (0.5–2 and 2–8 keV) for AGN identification  
  > "The whole area of ADF22 was observed by $Chandra$ at 0.5–2 keV and 2–8 keV" (3.2 SMGs in the node of the Cosmic Web)
- Other facility **Subaru/MOIRCS**: near-IR spectroscopic redshifts via [OIII] from Kubo et al.  
  > "determined using near-infrared spectroscopy performed with Subaru/MOIRCS" (3.1 Extraction of z=3.09 SMGs)
- Other facility **Spitzer MIPS**: 24 micron flux densities for AGN contribution  
  > "using MIPS 24 $\mu$m flux densities ($S_{24\mu \rm{m}}$)" (3.1 Extraction of z=3.09 SMGs)
- External data: Archival spectroscopic/photometric redshifts  
  > "we compared our 1.1 mm source catalog with archival catalogs of spectroscopic and photometric redshifts" (3.1 Extraction of z=3.09 SMGs) [from Bothwell 2013; Tamura 2010; Kubo 2015; Chapman 2005; Yun et al. in preparation]
- External data: X-ray counterpart catalog  
  > "have X-ray counterparts listed in (cite: 2009ApJ...691..687L) within 0$^{\prime\prime}$.5" (3.2 SMGs in the node of the Cosmic Web) [from (cite: 2009ApJ...691..687L)]
- External data: SMG volume density from ALESS, about 4e-6 Mpc^-3 at z=2.5-3.5 for LIR>~10^12.5  
  > "the volume density of SMGs at $z=2.5-3.5$ is about $4\times10^{-6}$ Mpc$^{-3}$ for $L_{\rm IR}\gtrsim10^{12.5}L_\odot$" (3.2 SMGs in the node of the Cosmic Web) [from (cite: 2014MNRAS.438.1267S)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J2148+0657 used for bandpass, amplitude, phase and flux  
  > "The quasar J2148+0657 was observed for bandpass, amplitude, phase, and flux calibration." (2 Observations and Data Reduction)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA clean, mosaic mode  
  > "through the ’clean’ process (with natural weighting and by setting the imager mode to ’mosaic’ in casa)" (2 Observations and Data Reduction)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "with natural weighting and by setting the imager mode to ’mosaic’" (2 Observations and Data Reduction)
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
- final beam: 0.53"x0.50", PA -84 deg  
  > "synthesized beam of $0.^{\prime\prime}53\times0.^{\prime\prime}50$" (2 Observations and Data Reduction)
- final rms: 0.07 mJy/beam  
  > "a typical rms revel of 0.07 mJy beam$^{-1}$" (2 Observations and Data Reduction)

### Inherited from earlier work

- Photo-z method for ADF22i  
  > "we derive an optical to near-infrared photo-$z$ of 3.08$^{+0.17}_{-0.15}$ using a method in (cite: 2014MNRAS.440.3462U)" (3.1 Extraction of z=3.09 SMGs) [from (cite: 2014MNRAS.440.3462U)]
- AGN contribution estimate from 24 micron  
  > "following Alexander et al. in preparation" (3.1 Extraction of z=3.09 SMGs) [from Alexander et al. in preparation]
- Survey design and full catalog deferred  
  > "The survey design and source catalog of the ALMA observations will be described in more detail in an upcoming paper (Umehata et al. in preparation)." (1 Introduction) [from Umehata et al. in preparation]

### Not stated but needed to reproduce (our reading)

- CASA version
- Calibration pipeline vs manual and flux-scale uncertainty
- Clean threshold, masks, cell and image size
- How the 80 pointings were selected
- Aegean parameters beyond 4 sigma threshold
- Flux-boosting or primary-beam correction treatment
- Details of SED template fitting and how LIR uncertainties were derived
- Redshift catalogs from Yun et al. unpublished
- Volume used for SFRD calculation

## Analysis recipe

1. **Image mosaic**: CASA clean, natural weighting, mosaic mode  
  > "The final entire map was created through the ’clean’ process (with natural weighting and by setting the imager mode to ’mosaic’ in casa)." (2 Observations and Data Reduction)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Source extraction and flux measurement**: Aegean source finding at 4 sigma; fluxes via imfit  
  > "to extract sources on the final mosaic image with a detection threshold of 4$\sigma$. The flux densities of the detected sources were measured with casa task, imfit." (2 Observations and Data Reduction)
   - software: aegean, CASA imfit
   - fitting: _not stated_
   - validation: _not stated_
3. **Redshift matching and counterpart identification**: Cross-match with archival spectroscopic/photometric redshift catalogs and Ks-band counterparts  
  > "we yielded eight 1.1 mm sources with $z_{\rm spec}=3.08-3.10$ and a further SMG with $z_{\rm phot}\sim3.1$." (3.1 Extraction of z=3.09 SMGs)
   - parameter: Ks counterparts within 0.18"; expected astrometric accuracy <~0.15"  
  > "All SMGs except for ADF22a has *Ks*-band counterparts within 0$^{\prime\prime}$.18" (3.1 Extraction of z=3.09 SMGs)
   - fitting: _not stated_
   - validation: Astrometric accuracy from beam and S/N  
  > "yield an expected astrometric accuracy of $\lesssim0^{\prime\prime}$.15" (3.1 Extraction of z=3.09 SMGs)
4. **Derive LIR and SFR**: Scale SED templates (Arp 220, M82, ALESS composite, Cosmic Eyelash) to S1.1mm at z, integrate 8–1000 um, take median and min/max; convert to SFR  
  > "We created best-fit SED for each template based on redshift and $S_{\rm 1.1~mm}$. The spectra between 8 and 1000 $\mu$m in the restframe were integrated and we derive a median value as well as minimum/maximum values." (3.1 Extraction of z=3.09 SMGs)
   - software: GRASIL templates
   - assumption: SFR = 1.0e-10 LIR/Lsun (Kennicutt 1998), Chabrier IMF  
  > "SFR/$M_\odot$yr$^{-1}$ = 1.0$\times10^{-10}$ $L_{\rm IR}$/$L_\odot$ ((cite: 1998ARA&A..36..189K)), assuming a Chabrier initial mass function" (3.1 Extraction of z=3.09 SMGs)
   - fitting: template scaling to single flux point  
  > "We created best-fit SED for each template based on redshift and $S_{\rm 1.1~mm}$." (Results, Extraction of z=3.09 SMGs)
   - validation: _not stated_
5. **AGN contamination of 1.1 mm**: Predict S1.1mm from 24 um flux assuming all 24 um from AGN, using Mullaney et al. 2011 AGN SED template  
  > "Assuming conservatively that $S_{24\mu \rm{m}}$ is fully powered by AGN, the predicted $S_{\rm 1.1~mm}$ based on the averaged empirical AGN spectral energy distribution (SED) template" (3.1 Extraction of z=3.09 SMGs)
   - fitting: _not stated_
   - validation: _not stated_
6. **Overdensity and SFRD**: Compare number of SMGs with LIR>~10^12.5 at z=3.08–3.10 to expected number from ALESS luminosity function volume density; compute SFRD in node from 8 SMGs  
  > "the predicted number of SMGs is 1$\times10^{-3}$ within this 1.5$^\prime \times 3^\prime$ field" (3.2 SMGs in the node of the Cosmic Web)
   - assumption: Redshift slice z=3.08–3.10; flat LCDM Om=0.3, H0=70  
  > "Assuming a redshift slice of $z=3.08-3.10$" (3.2 SMGs in the node of the Cosmic Web)
   - fitting: _not stated_
   - validation: _not stated_
7. **X-ray AGN and LAB association**: Match SMGs to Chandra catalog within 0.5" and to LAB list  
  > "We found that four SMGs at $z=3.09$ (ADF22a, ADF22c, ADF22e, ADF22g) have X-ray counterparts listed in (cite: 2009ApJ...691..687L) within 0$^{\prime\prime}$.5" (3.2 SMGs in the node of the Cosmic Web)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : data processing, clean imaging, imfit  
  > "The data were processed with the Common Astronomy Software Application (casa)" (2 Observations and Data Reduction)
- **aegean** v1.9.5-56: source extraction  
  > "We utilize a source-finding code, aegean v1.9.5-56" (2 Observations and Data Reduction)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Number of SMGs with zspec=3.08–3.10 | 8 | not stated | count | 3 | we yielded eight 1.1 mm sources with $z_{\rm spec}=3.08-3.10$ |
| SFRD in the node | ~10 | not stated | Msun/yr/Mpc^3 | 6 | We calculate a star-formation rate density (SFRD) in the node of $\sim$10 $M_\odot$ yr$^{-1}$ Mpc$^{-3}$ |
| X-ray AGN fraction among node SMGs | 50 | +39/-24 | % | 7 | 50$^{+39}_{-24}$% of SMGs in the node host X-ray luminous AGNs |
| Max AGN contribution to S1.1mm for ADF22e | ~110 uJy (~11%) | not stated | uJy | 5 | $S_{1.1\rm{mm}}\sim110$ $\mu$Jy (or $\sim$11% of the observed flux density) |
| ADF22a S1.1mm | 6.4 | 0.2 | mJy | 2 | 6.4 $\pm$ 0.2 |
| Expected number of SMGs in field for general fields | 1e-3 | not stated | count | 6 | the predicted number of SMGs is 1$\times10^{-3}$ within this 1.5$^\prime \times 3^\prime$ field |

## Qualitative findings

- Two SMGs (ADF22c, ADF22g) are associated with LABs.  
  > "two SMGs in the node are found to be associated with LABs" (3.2 SMGs in the node of the Cosmic Web)

## Claim tuples

- H: SMGs are overabundant in the SSA22 protocluster node | E: Compare number of z=3.08–3.10 SMGs with LIR>1e12.5 to field expectation | R: 3 observed versus 1e-3 expected; SFRD ~10 Msun/yr/Mpc^3 | F: SMGs are overabundant and star formation is two orders above global SFRD | **supported**
- H: SMGs in the node have high AGN fraction | E: Cross-match with Chandra catalog | R: 4 of 8 host X-ray AGN versus ~10% in field | F: AGN fraction is relatively high | **supported**
- H: SMGs connect to LABs | E: Match with LAB catalog | R: Two SMGs associated with LABs | F: coexist in a few cases; majority lack giant nebulae | **partially**

## Reasoning

- Why this data: Single-dish resolution is insufficient to identify counterparts, so ALMA used for an unconfused survey.  
  > "the angular resolution of single-dish telescopes is insufficient" (1 Introduction)
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): ALMA view limited to the central part; no other comparable submm data to constrain dust SEDs.  
  > "though we should note that our ALMA view is limited to only the central part" (4 Discussion & Conclusions); "The lack of any other submm/mm data with comparable angular resolution prevents from putting a constraint on dust SEDs." (3.1 Extraction of z=3.09 SMGs)
- Caveat (inferred, ours): LIR from single 1.1 mm point scaled with templates gives large systematic uncertainty
- Caveat (inferred, ours): Small-number statistics (8 SMGs, 3 above LF limit)
- Caveat (inferred, ours): Comparison volume density from ECDF-S which may be underdense
- Caveat (inferred, ours): Preliminary 80 of 103 pointings; no completeness or flux boosting discussion

## Reproducibility

- Data public (paper): ALMA data identified by project code; public status not stated  
  > "ADS/JAO.ALMA#2013.1.00162.S (PI: H. Umehata)" (Acknowledgments)
- Products in archive: _not stated_
- Missing: CASA version and clean parameters
- Missing: Selection of the 80 pointings
- Missing: Unpublished redshift catalogs (Yun et al.)
- Missing: Template fitting details
- Data volume (inferred): ~50-100 GB for 80 pointings of Band 6 TDM data
- Score (inferred): 3/5, Short letter with basic imaging steps; many parameters missing, though analysis is simple and public catalogs used.
- Rediscovery candidate: no, Imaging recipe incomplete and relies on unpublished redshifts and in-preparation work.

## Links

- Method: (cite: 2012MNRAS.422.1812H) (Aegean source finder)
- Method: (cite: 2014MNRAS.438.1267S) (ALESS luminosity function and SED template)
- Companion: Umehata et al. in preparation (Full survey design and source catalog)
- Companion: (cite: 2015ApJ...799...38K) (MOIRCS spectroscopic redshifts)
- Related: ALESS
- Related: SSA22 protocluster LAE survey

## Checks

```json
{
 "quotes": 56,
 "quotes_ok": 56,
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
  "facts": 80,
  "stated": 44,
  "rate": 0.55
 },
 "evidence_ok": true
}
```
