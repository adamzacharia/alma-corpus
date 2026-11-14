# An ALMA survey of the SCUBA-2 Cosmology Legacy Survey UKIDSS/UDS field: source catalogue and properties

`2019MNRAS.487.4648S` | Monthly Notices of the Royal Astronomical Society 2019 | first author: Stach, Stuart M. | arXiv: 1903.02602 | DOI: 10.1093/mnras/stz1536

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type large_program_or_survey

## Science

- Fields: high_z_galaxies, agn_and_quasars
- Question: What are the catalogue, redshift distribution, blank-map nature, AGN fraction and evolutionary links of SMGs found in an ALMA follow-up of all 716 SCUBA-2 S2CLS sources in the UDS field?  
  > "In this paper we present the final catalogue for the AS2UDS survey" (1 Introduction)
- Target **AS2UDS: 716 SCUBA-2 S2CLS sources in the UKIDSS UDS field**: coordinates _not stated_; z/distance median z_phot = 2.61 ± 0.09 (MAGPHYS)  
  > "Across four ALMA cycles (1, 3, 4, and 5) we observed all 716 $>4\sigma$ sources from the SCUBA-2 S2CLS map" (2.1 Sample Selection); distance from MAGPHYS-photoz SED fitting  
  > "Across four ALMA cycles (1, 3, 4, and 5) we observed all 716 $>4\sigma$ sources from the SCUBA-2 S2CLS map" (2.1 Sample Selection)

## Data provenance

- ALMA projects: 2012.1.00090.S, 2015.1.01528.S, 2016.1.00434.S, 2017.1.01492.S
- bands: Band 7 (344 GHz, ~870 um)  
  > "Our ALMA targets were observed in Band 7 (central frequency 344 GHz  $\sim$ 870 $\mu$m)." (2.2 Data Reduction)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: 7.5 GHz in four spectral windows centred at 344.00 GHz  
  > "with the 7.5 GHz bandwidth of the four spectral windows centred at 344.00 GHz" (2.2 Data Reduction)
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: Untapered median beams 0.35x0.25'' (C1), 0.19x0.18'' (C3), 0.81x0.54'' (C5); tapered detection maps 0.73x0.59'' (C1), 0.56x0.50'' (C3), 0.58x0.55'' (C4)  
  > "Combined with natural weighting this resulted in ‘detection’ maps with median synthesized beam sizes of 0.73$''$ $\times$ 0.59$''$ for Cycle 1, 0.56$''$ $\times$ 0.50$''$ for Cycle 3 and 0.58$''$ $\times$ 0.55$''$ for Cycle 4" (2.2 Data Reduction)
- max recoverable scale: _not stated_
- sensitivity: Mean rms 0.25 (C1), 0.34 (C3), 0.23 (C4), 0.085 (C5) mJy/beam; median 0.3 mJy/beam  
  > "mean depths of $\sigma_{\rm 870}=$ 0.25 mJy beam$^{-1}$ for Cycle 1, $\sigma_{870}=$ 0.34 mJy beam$^{-1}$ for Cycle 3" (2.2 Data Reduction)
- time on source: 150 s (Cycle 1), 40 s (Cycles 3 and 4), 285 s (Cycle 5) per source  
  > "150 second integrations in Cycle 1 using 26 dishes, 40 second integrations in Cycle 3 and 4 (with 45–50 dishes), and 285 second integrations using 44 dishes in Cycle 5" (2.2 Data Reduction)
- observing dates: Cycle 1: 2013 Nov 1; Cycle 3: 2016 Jul 23-Aug 11; Cycle 4: 2016 Nov 9-17 and 2017 May 6; Cycle 5: 2018 Aug 24  
  > "Cycle 3 between 2016 July 23 and August 11, Cycle 4 between 2016 November 9 and 17 and 2017 May 6, and Cycle 5 on 2018 August 24." (2.2 Data Reduction)
- pi or archival as stated: _not stated_
- Other facility **SCUBA-2 S2CLS**: Parent 850 um single-dish catalogue  
  > "The parent single-dish survey covers an area of 0.96 deg$^{2}$" (2.1 Sample Selection)
- Other facility **UKIDSS UDS DR11, SXDS, VIDEO, SpUDS, HerMES, CANDELS, UDS20 VLA, X-UDS Chandra**: Multiwavelength photometry for SED fitting, counterparts, and AGN selection  
  > "This analysis exploits the wealth of deep, multi-wavelength observations available in this field" (2.3 Additional Multiwavelength Observations)
- External data: S2CLS DR1 SCUBA-2 source catalogue  
  > "S2CLS DR1 sub-millimetre source catalogue (cite: geach2017scuba)" (2.2 Data Reduction) [from (cite: geach2017scuba)]
- External data: X-UDS Chandra catalogue and count-rate conversion factors  
  > "Deep *Chandra* observations of part of the UDS field have been obtained by the X-UDS survey (cite: kocevski2018x)." (2.3.5 X-ray) [from (cite: kocevski2018x)]
- External data: ALESS composite SED used for S870/S850=0.95 and IRAC colour tracks  
  > "using a $S_{870}/S_{850}=0.95$ factor derived from the ALESS survey composite spectral energy distribution (SED) (cite: swinbank2014alma)" (3.3 Flux Recovery) [from (cite: swinbank2014alma)]
- Simulation/model as data: 60,000 simulated ALMA maps with injected sources into residual noise maps for completeness and deboosting  
  > "estimated from a suite of 60,000 simulated ALMA maps, as described in (cite: stach2018alma)" (3.1 Completeness and Flux Deboosting)

## Processing

### Calibration

- pipeline or manual: Standard ALMA calibration scripts  
  > "were used to calibrate the datasets from Cycle 1, 3, 4, and 5 respectively using the standard ALMA calibration scripts" (2.2 Data Reduction)
- casa version: CASA v4.1, v4.5.3, v4.7.2, v5.3.0 for Cycles 1, 3, 4, 5; imaging with v4.7.2  
  > "v4.1, v4.5.3, v4.7.2, v5.3.0 were used to calibrate the datasets from Cycle 1, 3, 4, and 5 respectively" (2.2 Data Reduction)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0217-0820 and J0238+1636  
  > "for the absolute flux scaling: J0217$-$0820 and J0238+1636" (2.2 Data Reduction)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA CLEAN, multi-frequency synthesis; CONCAT for 125 maps observed in Cycles 3 and 4  
  > "To create the continuum maps we used the CLEAN task in multi-frequency synthesis mode." (2.2 Data Reduction)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "Combined with natural weighting this resulted in ‘detection’ maps" (2.2 Data Reduction)
- uv taper: 0.5'' FWHM Gaussian taper for Cycles 1, 3, 4; Cycle 5 untapered  
  > "we employed a 0.5$''$ FWHM Gaussian taper in the *uv*-plane using the *uvtaper* parameter in CLEAN for the Cycle 1,3, and 4 data" (2.2 Data Reduction)
- cell size: 0.06''  
  > "512$\times$512 pixels in size with a pixel scale of 0.06$''$ (30.7$''$ square)" (2.2 Data Reduction)
- image size: 512x512 pixels  
  > "512$\times$512 pixels in size with a pixel scale of 0.06$''$ (30.7$''$ square)" (2.2 Data Reduction)
- masking: Clean to 3 sigma; islands above 4 sigma convolved with beam used as mask; then clean to 1.5 sigma  
  > "islands of pixels with flux densities above 4 $\sigma$ were convolved with the reconstructed beam to create cleaning masks" (2.2 Data Reduction)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Completeness and flux-deboosting simulation method  
  > "estimated from a suite of 60,000 simulated ALMA maps, as described in (cite: stach2018alma)" (3.1 Completeness and Flux Deboosting) [from (cite: stach2018alma)]
- Limiting simulated source FWHM<0.6'' for deboosting  
  > "we follow (cite: simpson2015scuba) and limit our simulated sources to FWHM $<$ 0.6$''$" (3.1 Completeness and Flux Deboosting) [from (cite: simpson2015scuba)]
- SPIRE deblending technique and detection limits from simulations  
  > "to deblend the low resolution images we apply the technique described in (cite: swinbank2014alma)" (2.3.1 Far-Infrared) [from (cite: swinbank2014alma)]
- MAGPHYS-photoz version for simultaneous photometric redshift fitting  
  > "(cite: da2015alma) extended this method to include the computation of photometric redshifts simultaneously with the constraints on other physical parameters" (3.4 Photometric Redshifts) [from (cite: da2015alma)]
- Full MAGPHYS SED fitting details  
  > "The complete description of our MAGPHYS SED fitting and the resulting multiwavelength properties is described in U. Dudzevičiūtė et al (in prep.)." (3.4 Photometric Redshifts) [from Dudzevičiūtė et al. (in prep.)]

### Not stated but needed to reproduce (our reading)

- CLEAN niter, threshold and exact sigma-clipping parameters
- Per-source flux-scale uncertainty and calibrator flux models
- Details of MAGPHYS priors, templates and redshift grid (in companion paper)
- Exact spectral-window setup beyond the 7.5 GHz total
- Which Cycle 3/4 duplicates are used and how combined fluxes were chosen
- Full catalogue content beyond the first row (hosted externally)
- Binning details for the z-S870 linear fit
- Stacking apertures for blank-map Herschel and ALMA stacks

## Analysis recipe

1. **Calibrate and image continuum maps**: Standard ALMA calibration, then CLEAN with uv-taper and natural weighting, cleaning to 3 sigma then masked to 1.5 sigma  
  > "Each map was then initially cleaned to 3 $\sigma$, and islands of pixels with flux densities above 4 $\sigma$ were convolved with the reconstructed beam to create cleaning masks." (2.2 Data Reduction)
   - software: CASA
   - parameter: 0.5'' FWHM uv-taper  
  > "we employed a 0.5$''$ FWHM Gaussian taper in the *uv*-plane using the *uvtaper* parameter in CLEAN" (2.2 Data Reduction)
   - fitting: _not stated_
   - validation: _not stated_
2. **Detect sources and set catalogue threshold**: SExtractor finds >2 sigma peaks; 0.5'' aperture SNR from random-aperture noise; catalogue at SNR>=4.3 chosen for <=2% contamination  
  > "The AS2UDS catalogue comprises the 708 sources which have 0.5$''$-diameter aperture SNR $\geq$ 4.3." (3 Analysis)
   - software: SExtractor
   - parameter: 50 random 0.5'' apertures in primary beam for noise  
  > "randomly placing 50 apertures within the area of the primary beam and calculating the standard deviation" (3 Analysis)
   - fitting: _not stated_
   - validation: False positive rate from inverted maps  
  > "This is based on the ratio of ‘negative’ sources found in the inverted ALMA maps" (3 Analysis)
3. **Measure fluxes, completeness and deboosting**: 1.0'' aperture fluxes on primary-beam-corrected maps, 20% aperture correction, deboosting from running median of recovered/input flux versus SNR in simulations  
  > "1.0$''$ diameter aperture fluxes were extracted for the 708 sources from the primary beam corrected maps. A 20 % aperture correction is applied" (3 Analysis)
   - software: CASA
   - parameter: Injected fluxes from power law index -2, sizes uniform 0 to 0.9'' FWHM, recovery within 0.6''  
  > "randomly sampled from a steeply declining power-law distribution with an index of $-$2" (3.1 Completeness and Flux Deboosting)
   - assumption: Intrinsic source sizes <0.6'' FWHM  
  > "limit our simulated sources to FWHM $<$ 0.6$''$" (3.1 Completeness and Flux Deboosting)
   - fitting: _not stated_
   - validation: Compared completeness and flux recovery against SCUBA-2 fluxes  
  > "we have a median recovery rate of 97$^{+1}_{-2}$ % of the flux in the ALMA pointings" (3.3 Flux Recovery)
4. **Derive photometric redshifts and properties**: MAGPHYS-photoz fit to up to 22 filters, with BC03 models and Chabrier IMF  
  > "MAGPHYS employs the stellar population synthesis models of (cite: bruzual2003stellar) with a (cite: chabrier2003galactic) IMF" (3.4 Photometric Redshifts)
   - software: MAGPHYS
   - parameter: 0.6'' matching radius to UDS DR11  
  > "We use a 0.6$''$ matching radius to cross-match the DR11 UDS catalogue to our AS2UDS sub-millimetre galaxy catalogue." (2.3 Additional Multiwavelength Observations)
   - fitting: _not stated_
   - validation: Compared to spectroscopic redshifts of 7316 UDS sources and 44 SMGs  
  > "for the 44 AS2UDS SMGs with spectroscopic redshifts we find a median $\Delta z=-0.02$ with a standard deviation of 0.25" (3.4 Photometric Redshifts)
5. **Test blank maps**: Stack Herschel/SPIRE and SCUBA-2 at 101 blank-map positions, fit modified blackbody to predict 850 um, compare K-band overdensity to random fields, re-observe ten blank maps in Cycle 5  
  > "we predict 850 $\mu$m flux from the SPIRE stacks by fitting a modified blackbody SED with $z=$ 2.5, a dust temperature $T_{d}=$ 35 K, and emissivity $\beta=$ 1.5" (4.3 Blank Maps)
   - assumption: z=2.5, Td=35 K, beta=1.5  
  > "a modified blackbody SED with $z=$ 2.5, a dust temperature $T_{d}=$ 35 K, and emissivity $\beta=$ 1.5" (4.3 Blank Maps)
   - fitting: _not stated_
   - validation: Cycle 5 deeper re-observations  
  > "From the ten single-dish sources we detect 16 $>$ 4.3 $\sigma$ SMGs." (4.3 Blank Maps)
6. **Determine AGN fraction**: X-UDS matching with Lx>=1e43 erg/s, CSTACK stacking of undetected SMGs, Donley IRAC colour selection with z<3 cut  
  > "we adopt a conservative full-band X-ray luminosity limit of $L_{\rm X}\geq$ 10$^{43}$ erg s$^{-1}$ for classification as an AGN" (4.4.1 X-ray-selected AGN)
   - software: CSTACK
   - parameter: photon index Gamma=1.7; bolometric correction 15; efficiency 0.1  
  > "by assuming a power-law X-ray spectrum with photon index $\Gamma=$ 1.7" (4.4.1 X-ray-selected AGN)
   - fitting: _not stated_
   - validation: Stacked X-ray of colour-selected versus control samples  
  > "We test the efficacy of the (cite: donley2012identifying) selection by employing CSTACK" (4.4.2 Colour-selected AGN)
7. **Compare with passive galaxy formation redshifts and number density**: Add +200 Myr offset to SMG ages, compare to quiescent formation redshifts, burst duration t_burst = t_obs*(n_SMG/n_qg)  
  > "We estimate (and apply) a typical +200 Myr offset to our observed redshifts" (4.5 Passive Galaxy Progenitors)
   - parameter: M* > 10^9.85 Msun  
  > "We adopt a mass limit of M$_{\ast}>$ 10$^{9.85}$ M$_{\odot}$" (4.5 Passive Galaxy Progenitors)
   - assumption: SMGs are progenitors of z=1-1.8 quiescent galaxies, each with a single burst  
  > "(ii) each SMG has a single burst of intense star-formation" (4.5 Passive Galaxy Progenitors)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** v4.1, v4.5.3, v4.7.2, v5.3.0: Calibration and imaging (CLEAN, CONCAT)  
  > "For the imaging CASA v 4.7.2 was used, with the CONCAT task to combine the visibilities" (2.2 Data Reduction)
- **SExtractor** : Source extraction in ALMA maps and UKIDSS photometry  
  > "We extract sources by initially using SEXTRACTOR to find $>$ 2 $\sigma$ peaks in the ‘detection’ maps." (3 Analysis)
- **MAGPHYS** MAGPHYS-photoz: SED fitting and photometric redshifts  
  > "We use that version of the code in this paper" (3.4 Photometric Redshifts)
- **CSTACK** : X-ray stacking  
  > "To perform this stacking we use the CSTACK stacking software" (4.4.1 X-ray-selected AGN)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Number of SMGs detected (SNR>=4.3) | 708 | not stated | sources | 2 | we detect 708 sub-millimetre galaxies (SMGs) at $>$ 4.3$\sigma$ significance |
| Median photometric redshift | 2.61 | ±0.09 | dimensionless | 4 | We derive a median redshift of $z_{\rm phot}=$ 2.61 $\pm$ 0.09 |
| Gradient of median z vs S870 | 0.09 | ±0.02 | mJy^-1 | 4 | highly significant gradient of 0.09 $\pm$ 0.02 mJy$^{-1}$ |
| Number of blank maps | 101 | not stated | maps | 5 | There are 101 ALMA maps of SCUBA-2 sources in which we find no ALMA detected source above our 4.3 $\sigma$ detection threshold |
| AGN fraction lower limit (X-ray) | 21/274 (8%) | ±2% | percent | 6 | we derive a lower limit on the X-ray detected AGN fraction of 21/274 (8 $\pm$ 2 %) |
| AGN fraction upper limit | 45/162 (28%) | ±4% | percent | 6 | we estimate an upper limit of 45/162 (28 $\pm$ 4 %) AGN in the AS2UDS population |
| Median SMG mass-weighted age | 11.4 | +0.1/-0.2 | Gyr | 7 | 11.4$^{+0.1}_{-0.2}$ Gyr for AS2UDS and 11.5 $\pm$ 0.3 Gyr for the comparison sample |
| SMG burst duration | 190 | +50/-40 | Myr | 7 | we find a burst duration of 190$^{+50}_{-40}$ Myr |
| Deboosting factor at 4.3 sigma | 32 | not stated | percent | 3 | This results in flux deboosting factors of 32 % for sources at our 4.3 $\sigma$ detection threshold |

## Qualitative findings

- Most blank ALMA maps correspond to real SCUBA-2 sources blended from faint SMGs below the detection threshold.  
  > "These deeper observations thus confirm that multiplicity is a significant driver of the ‘blank’ maps" (4.3 Blank Maps)

## Claim tuples

- H: Does SMG redshift increase with 870 um flux? | E: Linear fit to median z in equal-number bins of the full MAGPHYS sample | R: Gradient 0.09 ± 0.02 mJy^-1; subsamples of 100 give only ~1.5 sigma | F: Significant trend suggestive of downsizing | **supported**
- H: Are ALMA-blank maps spurious single-dish detections? | E: SPIRE stacking, K-band overdensity and deeper Cycle 5 re-observations | R: SPIRE emission detected; 153 excess galaxies at z=1.5-4; 16 SMGs in ten re-observed maps | F: Blank maps are mostly blends of faint SMGs | **supported**
- H: What fraction of SMGs host AGN? | E: X-UDS matching, stacking, IRAC colour selection | R: 8±2% to 28±4% | F: Most SMGs do not host luminous AGN | **supported**
- H: Are SMGs progenitors of high-z quiescent galaxies? | E: Compare ages and number densities with quiescent samples | R: Median ages 11.4 vs 11.5 Gyr; burst duration ~190 Myr | F: Consistent with an evolutionary link | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: 0.5'' taper to remain sensitive to marginally resolved extended SMGs  
  > "To ensure we are not biased against selecting extended sources, by remaining sensitive to extended flux from our SMGs" (2.2 Data Reduction)
- How they decided it was enough: _not stated_
- Limitation (authors): Phase-centre rounding error may have missed ~11 galaxies at primary beam edges  
  > "We estimate a constraint of $\sim$ 11 potentially missed galaxies due to this offset" (3.2 SCUBA-2 Positional Offsets)
- Caveat (inferred, ours): Photometric redshift scatter (std 0.25-0.30) may affect trend and age comparisons
- Caveat (inferred, ours): Flux-redshift trend could be influenced by selection effects
- Caveat (inferred, ours): AGN upper limit depends on a redshift cut and ambiguous IRAC selection
- Caveat (inferred, ours): Many key details deferred to papers in preparation

## Reproducibility

- Data public (paper): Catalogue available online at the Durham URL; ALMA data programs listed  
  > "Catalogue can be found at http://astro.dur.ac.uk/AS2UDS" (1 Introduction)
- Products in archive: _not stated_
- Missing: Companion in-prep papers for MAGPHYS details
- Missing: Proprietary-like multiwavelength catalogues (UDS DR11, UDS20 radio) in prep
- Missing: CLEAN iteration settings
- Data volume (inferred): Large: ~700 short Band 7 pointings; likely hundreds of GB raw across four projects
- Score (inferred): 3/5, ALMA data and the catalogue are public and the ALMA recipe is mostly described, but SED fitting and multiwavelength data rely on in-prep papers.
- Rediscovery candidate: no, The full results depend on unpublished multiwavelength catalogues and MAGPHYS fits, although the ALMA catalogue part is reproducible.

## Links

- Method: (cite: stach2018alma) (Completeness and deboosting simulations)
- Method: (cite: da2015alma) (MAGPHYS-photoz)
- Companion: Dudzevičiūtė et al. (in prep.) (Full MAGPHYS multiwavelength properties)
- Companion: (cite: simpson2015scuba2) (Cycle 1 pilot sample)
- Companion: (cite: cooke2018alma) (Serendipitous [CII] emitters)
- Companion: Gullberg et al. (in prep.) (Sizes and morphologies)
- Related: ALESS
- Related: S2CLS
- Related: UKIDSS UDS
- Related: X-UDS

## Checks

```json
{
 "quotes": 76,
 "quotes_ok": 76,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 4,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 9,
 "numeric_problems": 0,
 "fill": {
  "facts": 90,
  "stated": 58,
  "rate": 0.644
 },
 "evidence_ok": true
}
```
