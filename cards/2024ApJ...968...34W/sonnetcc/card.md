# The Galaxies Missed by Hubble and ALMA: The Contribution of Extremely Red Galaxies to the Cosmic Census at 3 &lt; z &lt; 8

`2024ApJ...968...34W` | The Astrophysical Journal 2024 | first author: Williams, Christina C. | arXiv: 2311.07483 | DOI: 10.3847/1538-4357/ad3f17

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth light | type multi_facility_alma_minor

## Science

- Fields: high_z_galaxies
- Question: What types of galaxies were missed by HST (and mostly Spitzer and ALMA) at z>3, and what fraction of the cosmic star formation and stellar mass census they account for  
  > "The goal of this work is to determine what types of galaxies we have been missing, and, what fraction of the cosmic census has been unaccounted for as a result." (Introduction)
- Target **HST-dark extremely red galaxies in JADES/GOODS-S (66 candidates; 29 inside the MIRI footprint)**: coordinates per-source RA/Dec given in the sample tables (GOODS-S field)  
  > "of which we identify 66 candidate objects" (3 Color selection of targets); "We measure the redshift as the probability weighted average peak of the photometric redshift distribution without any priors." (4.1 Redshift estimations); z/distance photometric redshifts, with some spectroscopic redshifts from FRESCO and JADES NIRSpec; sample spans 3<z<8  
  > "of which we identify 66 candidate objects" (3 Color selection of targets); "We measure the redshift as the probability weighted average peak of the photometric redshift distribution without any priors." (4.1 Redshift estimations); distance from EAZY photometric redshifts (prior for prospector), spectroscopic redshifts from FRESCO and JADES NIRSpec where available  
  > "of which we identify 66 candidate objects" (3 Color selection of targets); "We measure the redshift as the probability weighted average peak of the photometric redshift distribution without any priors." (4.1 Redshift estimations)

## Data provenance

- ALMA projects: _none stated_
- bands: ~1 mm continuum (1.1 mm GOODS-ALMA maps used for stacks)  
  > "In cases where galaxies are significantly detected at 1-mm in either the deep ASAGAO imaging (cite: Hatsukade2018) or the wider-area GOODS-ALMA program (cite: Franco2018) we use the published total fluxes in our SED modeling." (2.2.4 ALMA imaging); "we stack the 1.1mm ALMA images for all sources that are not individually detected" (5.2.1 Dusty star forming galaxies in our sample)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: beam ~0.5" x 0.5" FWHM (combined ALMA data)  
  > "The resolution of the combined ALMA data is relatively high (beam size $\sim0.5"\times0.5"$ FWHM)" (2.2.4 ALMA imaging)
- max recoverable scale: _not stated_
- sensitivity: GOODS-ALMA map sigma_rms ~180 uJy/beam (limits used outside ASAGAO coverage)  
  > "provide GOODS-ALMA limits (map $\sigma_{rms}\sim180\mu$Jy/beam) for the objects outside the ASAGAO coverage" (2.2.4 ALMA imaging)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: published/shared maps from other teams (ASAGAO combined map, HUDF ALMA footprint, GOODS-ALMA); no new ALMA observations  
  > "The data we use for our analysis include the deep combined map built by the ASAGAO team (cite: Hatsukade2018) combined with data from the deep HUDF ALMA footprint (cite: Dunlop2017)" (2.2.4 ALMA imaging); "We thank Carlos Gomez-Guijarro and David Elbaz for sharing the GOODS-ALMA imaging." (Acknowledgements)
- Other facility **JWST/NIRCam (JADES, JEMS, FRESCO)**: Deep 0.9-5 micron imaging used for sample selection and photometry  
  > "We identify our sample using data from the JWST Advanced Deep Extragalactic Survey (cite: Eisenstein2023)." (2.1.2 JWST NIRCam Imaging)
- Other facility **JWST/MIRI (SMILES)**: 5-25.5 micron imaging, forced photometry in seven filters out to 21 micron  
  > "Systematic Mid-infrared Instrument Legacy Extragalactic Survey program (SMILES; PID 1207; PI Rieke)" (2.2.1 JWST MIRI Imaging)
- Other facility **HST ACS and WFC3 (Hubble Legacy Field)**: Optical and near-IR imaging in nine filters, 0.4-1.6 micron  
  > "We include data from ACS (F435W, F606W, F775W, F814W, F850LP) and WFC3/IR (F105W, F125W, F140W, F160W)." (2.1.1 HST Imaging)
- Other facility **JWST NIRSpec (JADES) and NIRCam grism (FRESCO)**: Spectroscopic redshifts for a small number of sources  
  > "We make use of the public spectroscopic confirmations released by the JADES-NIRSpec program (cite: Bunker2023; Eisenstein2023b)." (2.3 JWST spectroscopy)
- Other facility **Spitzer (GREATS)**: Deep 3.6 and 4.5 micron imaging depth used as a comparison limit  
  > "the deepest Spitzer 3.6 and 4.5 $\mu$m imaging to date from the GREATS program (cite: Labbe2015) which reached a 3$\sigma$ limiting depth of 27.2 (AB magnitude)" (3 Color selection of targets)
- External data: ASAGAO deep combined 1 mm map and published total fluxes  
  > "The data we use for our analysis include the deep combined map built by the ASAGAO team (cite: Hatsukade2018)" (2.2.4 ALMA imaging) [from Hatsukade et al. 2018 (cite: Hatsukade2018)]
- External data: GOODS-ALMA 1.1 mm map and published total fluxes, and limits outside ASAGAO coverage  
  > "overlapping coverage from the shallower, but much wider GOODS-ALMA program (cite: Franco2018; GomezGuijarro2022)" (2.2.4 ALMA imaging) [from Franco et al. 2018; Gomez-Guijarro et al. 2022 (cite: Franco2018; GomezGuijarro2022)]
- External data: Deep HUDF ALMA footprint data  
  > "combined with data from the deep HUDF ALMA footprint (cite: Dunlop2017)" (2.2.4 ALMA imaging) [from Dunlop et al. 2017 (cite: Dunlop2017)]
- External data: Obscured SFRD and extrapolated infrared luminosity function used for comparison  
  > "Since ALMA and far-infrared detections become sparse at $z>3$, the orange region representing the obscured SFRD is measured by combining individual bright detections along with an extrapolation of the infrared luminosity function to faint infrared luminosities (cite: Zavala2021)." (6.1 The cosmic star formation rate density) [from Zavala et al. 2021 (cite: Zavala2021)]
- External data: LRD color selection criteria  
  > "We cross-check our sample with the following selection criteria for LRD: $-0.5<$F115W–F200W$<1$ and F277W–F444W$>$1.6 (cite: Greene2023)." (5.2.2 Possible evidence of AGN among red galaxies) [from Greene et al. 2023 (cite: Greene2023)]
- External data: Pre-JWST AGN catalog of GOODS-S  
  > "we have matched our sample to the pre-JWST AGN catalog built by (cite: Lyu2022)" (5.2.2 Possible evidence of AGN among red galaxies) [from Lyu et al. 2022 (cite: Lyu2022)]
- External data: Haro-11 far-infrared template for hotter dust  
  > "we scale a far-infrared template for Haro-11, an analog for a high-redshift dusty SFG" (6.1.1 Impact of modeling assumptions on the cosmic SFRD) [from Lyu et al. 2016 (cite: Lyu2016)]
- External data: SFR calibration from total infrared luminosity  
  > "We then convert this to SFR using the indicator based on total infrared luminosity of (cite: KennicuttEvans2012)." (6.1 The cosmic star formation rate density) [from Kennicutt & Evans 2012 (cite: KennicuttEvans2012)]
- Simulation/model as data: Obscured-AGN template for NIRCam-MIRI color tracks (Lyu & Rieke 2018)  
  > "along with the redshift evolution in colors for a template dominated by an obscured AGN (cite: LyuRieke2018)" (5.2.3 Nature of the LRDs in Our Sample)
- Simulation/model as data: Haro-11 far-infrared template scaled to ALMA stacked flux  
  > "we scale a far-infrared template for Haro-11, an analog for a high-redshift dusty SFG" (6.1.1 Impact of modeling assumptions on the cosmic SFRD)

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
- primary beam correction: flux measured on the primary beam corrected map  
  > "to measure the flux within a circular aperture of 1.0" diameter from the primary beam corrected map" (2.2.4 ALMA imaging)
- array combination: ASAGAO combined map prioritized where sources appear in several datasets  
  > "We prioritize the combined map from (cite: Hatsukade2018) if objects appear in multiple datasets" (2.2.4 ALMA imaging)
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- ALMA forced aperture photometry method  
  > "To perform forced photometry on ALMA, we broadly follow the methodology of (cite: Sun2021; Shivaei2022; Betti2019)." (2.2.4 ALMA imaging) [from (cite: Sun2021; Shivaei2022; Betti2019)]
- Fiducial prospector setup  
  > "setup broadly follows that outlined in (cite: Ji2023) with a few alterations." (4.2 SED Modeling) [from (cite: Ji2023)]
- NIRCam data reduction  
  > "Our data reduction procedure follows the methods outlined in (cite: Rieke2023b) for the JADES data release 1." (2.1.2 JWST NIRCam Imaging) [from (cite: Rieke2023b)]
- Photometric catalog construction and photometry  
  > "Also following the methods outlined in the JADES first data release (cite: Rieke2023b) we measure photometry jointly for the HST and NIRCam imaging" (2.1.3 Photometric catalogs) [from (cite: Rieke2023b)]
- MIRI survey design, data reduction and source extraction  
  > "Survey design, data reduction, and source extraction are described in (cite: Lyu2023)" (2.2.1 JWST MIRI Imaging) [from (cite: Lyu2023)]
- Dust emission priors allowing hotter dust  
  > "We adopt the (cite: DraineLi2007) dust emission model with priors as defined in (cite: Williams2019)" (4.2 SED Modeling) [from (cite: Williams2019)]
- Prospector setup with empirical AGN templates  
  > "setup as outlined in (cite: Lyu2023)" (5.2.3 Nature of the LRDs in Our Sample) [from (cite: Lyu2023)]

### Not stated but needed to reproduce (our reading)

- ALMA project codes, bands, array configurations and observing dates for the maps used
- How the ASAGAO combined map and GOODS-ALMA maps were calibrated, imaged and primary-beam corrected (done by the cited teams)
- Exact stacking recipe: positions, weights per source, how stack uncertainties were estimated, any masking of detected neighbours
- Which sources went into each redshift-bin stack and the bin boundaries used for GOODS-ALMA versus ASAGAO
- Flux scale uncertainty of the ALMA maps and how it enters the SED fit
- How ALMA flux density and limits were entered into prospector (as detections or upper limits, and with what likelihood)
- The final JADES/SMILES photometric catalogue values for each source (only the sample table of derived properties is given)
- Prospector run settings such as number of live points, convergence criteria, and the U_min range used for dust
- Normalization and redshift treatment when scaling the Haro-11 template to each stacked flux

## Analysis recipe

1. **Measure forced ALMA 1 mm photometry at NIRCam positions**: Forced circular aperture photometry at the NIRCam centroid on the deepest available map  
  > "we perform forced aperture photometry at the location of the NIRCam centroid, using a 1.0" diameter." (2.2.4 ALMA imaging)
   - software: photutils
   - parameter: Map units multiplied by pixels per beam; flux in 1.0" diameter aperture on primary beam corrected map  
  > "we multiply the map units (flux/beam) by the number of pixels per beam" (2.2.4 ALMA imaging)
   - parameter: Uncertainty = standard deviation of 100 random apertures within 30" (15" near map edge; none closer than 15" to the edge)  
  > "We assess the uncertainty as the standard deviation of the fluxes within 100 randomly placed apertures within 30" distance from the NIRCam source." (2.2.4 ALMA imaging); "Where the source is within 30" of the edge of the mosaic, we decrease this distance to 15", and do not assess forced photometry for sources closer than 15" to the edge of the map." (2.2.4 ALMA imaging)
   - parameter: ASAGAO combined map prioritized; GOODS-ALMA limits outside ASAGAO coverage  
  > "We prioritize the combined map from (cite: Hatsukade2018) if objects appear in multiple datasets" (2.2.4 ALMA imaging)
   - assumption: Source far-infrared size unknown, so a 1.0" aperture is used to capture extended flux  
  > "Without knowledge of the actual size of our sources at far-infrared wavelengths, to ensure we include any extended flux" (2.2.4 ALMA imaging)
   - fitting: _not stated_
   - validation: _not stated_
2. **Preliminary photometric redshifts**: EAZY fit to HST and NIRCam photometry, probability-weighted average peak of the redshift distribution, no priors  
  > "We measure the redshift as the probability weighted average peak of the photometric redshift distribution without any priors." (4.1 Redshift estimations)
   - software: EAZY
   - parameter: Single-line FRESCO and NIRSpec redshifts checked against the EAZY chi2 surface and SED shape  
  > "In these cases, we visually inspect the EAZY $\chi^{2}$ surface in conjunction with the SED shape" (4.1 Redshift estimations)
   - fitting: _not stated_
   - validation: Redshift free versus fixed to tentative spectroscopic redshift gives consistent results  
  > "We get consistent results within the uncertainties either using the tentative spectroscopic redshifts or leaving the redshift free." (4.1 Redshift estimations)
3. **SED modeling of stellar mass, SFR, dust and AGN fraction with HST+NIRCam+MIRI+ALMA**: Bayesian non-parametric SED fitting with FSPS, nebular emission, Draine & Li dust emission and AGN torus templates  
  > "Bayesian code to model the SEDs (cite: Johnson2021)" (4.2 SED Modeling); "using the Flexible Stellar Population Synthesis (FSPS) models (cite: Conroy2009)" (4.2 SED Modeling)
   - software: prospector, FSPS, dynesty
   - parameter: Non-parametric SFH, nine time bins with first two bins 0-30 and 30-100 Myr, continuity prior  
  > "We use a non-parametric star formation history (SFH) composed of nine time bins with a constant star formation rate in each bin." (4.2 SED Modeling); "We further adopt the continuity prior (to weight for physically plausible SFH forms, thus mitigating overfitting the data)" (4.2 SED Modeling)
   - parameter: Redshift fixed to spectroscopic value where available; EAZY redshift used as Gaussian prior otherwise  
  > "For the sources with spectroscopic redshift constraints, we fix to the spectroscopic redshift that was identified in the last Section." (4.2 SED Modeling)
   - parameter: Photometric S/N capped at 20 (minimum 5% uncertainty)  
  > "We further limit the S/N of any photometric point, which is capped at 20 (minimum 5% uncertainty, reflecting uncertainties in relative photometric calibration between filters)." (4.2 SED Modeling)
   - assumption: Kroupa IMF  
  > "and a (cite: Kroupa2001) initial mass function (IMF)" (Introduction)
   - assumption: Madau 1995 IGM absorption  
  > "We adopt the (cite: Madau1995) IGM absorption model." (4.2 SED Modeling)
   - assumption: Two-component dust attenuation (Charlot & Fall) with modified Calzetti law for older stars  
  > "We assume a two-component dust attenuation model where the dust attenuation of nebular emission and young stellar populations, and of old stellar populations, are treated differently (cite: Charlot2000)." (4.2 SED Modeling)
   - fitting: Nested sampling with dynesty; flat priors in log for metallicities and AGN parameters  
  > "We use the MCMC sampling code dynesty (cite: Speagle2020), adopting the nested sampling procedure (cite: Skilling2004)." (4.2 SED Modeling)
   - validation: Rerun for six high-mass sources with a Dirichlet SFH prior; masses consistent within uncertainties  
  > "instead using the Dirichlet prior (cite: Leja2017), which allows for sudden and extreme changes in SFR in adjacent time bins" (6.2.2 Potentially errant modeling assumptions)
4. **Stack ALMA 1.1 mm images of non-detections**: Inverse-variance weighted average stack of GOODS-ALMA 1.1 mm images of undetected sources, repeated inside the deeper ASAGAO footprint and in redshift bins  
  > "we stack the 1.1mm ALMA images for all sources that are not individually detected (calculating the inverse variance weighted average) from the GOODS-ALMA program (cite: Franco2018)" (5.2.1 Dusty star forming galaxies in our sample); "We perform the stack again for sources inside ASAGAO" (5.2.1 Dusty star forming galaxies in our sample)
   - parameter: Also stacked the broader NIRCam-only sample in GOODS-ALMA, roughly doubling the sample  
  > "we repeat the stacking while including our broader NIRCam-only sample within the GOODS-ALMA footprint, which roughly doubles the sample size" (5.2.1 Dusty star forming galaxies in our sample)
   - fitting: _not stated_
   - validation: _not stated_
5. **Derive L_IR, SFR and the cosmic SFRD contribution**: Sum SED-modeled SFR (last 30 Myr) over sources, divided by comoving volume in redshift bins; L_IR integrated from the best-fit SED and converted to SFR  
  > "We do a simple estimate of the total SFRD by summing the total SFR among our sample" (6.1 The cosmic star formation rate density); "We then convert this to SFR using the indicator based on total infrared luminosity of (cite: KennicuttEvans2012)." (6.1 The cosmic star formation rate density)
   - software: prospector
   - parameter: Sources with MIRI and ALMA constraints only; F444W S/N>20 selection treated as complete to F444W of 29.4  
  > "Thus, we expect that selection of H-dropouts is complete for sources brighter than our limiting F444W AB magnitude of 29.4." (6.1 The cosmic star formation rate density)
   - assumption: Measurements treated as lower limits without completeness correction  
  > "Without completeness our measurements should be considered lower limits" (6.1 The cosmic star formation rate density)
   - fitting: _not stated_
   - validation: Compared with obscured SFRD of Zavala et al. 2021, and repeated with LRDs removed  
  > "Thus we plot a second estimate with these LRD sources removed (open red circles)." (6.1 The cosmic star formation rate density)
6. **Test hotter dust using stacked ALMA fluxes**: Scale a Haro-11 far-infrared template to the stacked 1.1 mm flux in each bin, integrate 8-1100 micron for L_IR and convert to SFR  
  > "we scale a far-infrared template for Haro-11, an analog for a high-redshift dusty SFG" (6.1.1 Impact of modeling assumptions on the cosmic SFRD)
   - assumption: Hotter dust SED from compact high-redshift dusty galaxies  
  > "However, to interpret the stacked 1.1 mm flux, we now assume a hotter dust SED template." (6.1.1 Impact of modeling assumptions on the cosmic SFRD)
   - fitting: _not stated_
   - validation: Compared with prospector average SFR per bin, similar within 2 sigma  
  > "the average SFR per bin based on the prospector SED modeling is similar within 2$\sigma$" (6.1.1 Impact of modeling assumptions on the cosmic SFRD)

## Software

- **prospector** : Bayesian SED modeling  
  > "Bayesian code to model the SEDs (cite: Johnson2021)" (4.2 SED Modeling)
- **FSPS** : Stellar population synthesis models  
  > "using the Flexible Stellar Population Synthesis (FSPS) models (cite: Conroy2009)" (4.2 SED Modeling)
- **dynesty** : Nested sampling of SED posteriors  
  > "We use the MCMC sampling code dynesty (cite: Speagle2020), adopting the nested sampling procedure (cite: Skilling2004)." (4.2 SED Modeling)
- **EAZY** : Preliminary photometric redshifts  
  > "we first measure preliminary photometric redshifts based on the HST and JWST/NIRCam photometry using EAZY (cite: Brammer2008)" (4.1 Redshift estimations)
- **photutils** 1.5.0 (per reference list): Source detection and forced aperture photometry, including on the ALMA map  
  > "package to identify source detections, and measure forced circular aperture photometry" (2.1.3 Photometric catalogs); "(cite: photutils) to measure the flux within a circular aperture of 1.0" diameter from the primary beam corrected map" (2.2.4 ALMA imaging)
- **WebbPSF** : Encircled energy curves and aperture corrections  
  > "using encircled energy curves constructed using WebbPSF (cite: Perrin2014)" (2.1.3 Photometric catalogs)
- **JWST Calibration Pipeline** v1.10.0: MIRI data reduction  
  > "data reduction was performed using the JWST Calibration Pipeline v1.10.0 (cite: Bushouse2023)" (2.2.1 JWST MIRI Imaging)
- **CIGALE** : Alternative SED fits with the SKIRTOR AGN model  
  > "Further, we do a similar exploration using CIGALE (cite: Boquien2019)" (5.2.3 Nature of the LRDs in Our Sample)
- **SKIRTOR** : Clumpy two-phase torus AGN model within CIGALE  
  > "AGN model, a clumpy two-phase torus model from (cite: Stalevski2012; Stalevski2016)" (5.2.3 Nature of the LRDs in Our Sample)
- **HMF** : Halo mass function calculator for expected stellar mass limit  
  > "To estimate this we use the halo mass function calculator" (6.2 Stellar mass census: the abundance of massive galaxies)
- **astropy** : _not stated_
- **Cloudy** : _not stated_

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| HST-dark red galaxy candidates in JADES | 66 | not stated | sources | 0 | of which we identify 66 candidate objects |
| Sources inside the MIRI footprint used for the MIRI+ALMA modeling | 29 | not stated | sources | 3 | for the 29 sources inside the MIRI footprint using only the HST+NIRCam data |
| Sources not detected in any 1-mm ALMA data | 25 of 29 | not stated | sources | 1 | (25 out of 29) |
| Median stellar mass decrease when MIRI+ALMA added (HST+NIRCam logM>10) | 0.6 (as large as 1) | not stated | dex | 3 | In particular, we find a systematic reduction in stellar mass of (median decrease of 0.6 dex, and as large as 1 dex) |
| Median SFR decrease factor when MIRI+ALMA added (SFR>~100 Msun/yr) | 10 | not stated | dimensionless | 3 | we calculate a median factor of 10 decrease in SFR inferred when including MIRI+ALMA |
| ASAGAO stacked 1.1 mm flux for 3<z<5 sources | 55 | 24 | uJy/beam | 4 | 55$\pm$24 $\mu$Jy/beam |
| GOODS-ALMA stacked 1.1 mm flux of 9 LRDs | 3 | 37 | uJy/beam | 4 | We find that the 1.1mm flux is not detected (3$\pm37\mu$Jy/beam). |
| Stacked 1.1 mm fluxes at z~3.5, 4.5, 5.5, 7 including detected sources | 83, 213, 2, 25 | 44, 39, 48, 38 | uJy/beam | 6 | we find that in the above redshift bins, the stacked fluxes are 83$\pm$44, 213$\pm$39, 2$\pm$48, and 25$\pm$38 $\mu$Jy/beam |
| Typical dust temperature from prospector fits | 37 | not stated | K | 3 | yielded a typical T$_{\rm dust}\sim37$K |
| Candidate LRDs among the 66 objects | 13 | not stated | sources | 0 | We find that 13 out of 66 objects in the NIRCam footprint are candidate LRDs by this criterion |
| Fraction of obscured SFRD from log L_IR<12 sources at 4<z<5 | 26% | not stated | percent | 5 | (26%) at $4<z<5$, compared to 20% estimated by Zavala et al |
| SFRD at z~7 from SED modeling | -2.44 | +0.12/-0.18 | log10 Msun/yr/Mpc^3 | 5 | log$_{10}\rho_{SFR}=-2.44^{+0.12}_{- 0.18}$ |
| Galaxies above z>3.5 with logM*>10 | 16 | not stated | sources | 3 | we still identify a remarkably large number of galaxies (16) above $z>3.5$ |

## Qualitative findings

- Most of the sample is individually undetected at 1 mm; stacks suggest faint dust-obscured star formation at z<5 and no detection at 6<z<8  
  > "This result suggests that our $6<z<8$ sample is not actually dominated by similar lower luminosity DSFGs." (5.2.1 Dusty star forming galaxies in our sample)
- MIRI colors of LRDs show a turnover disfavoring a dominant reddened AGN  
  > "It is immediately clear that the turnover in the median MIRI SED strongly disfavors a reddened AGN shape" (5.2.3 Nature of the LRDs in Our Sample)
- Several high-redshift sources have stellar masses above expectations for the survey area  
  > "these galaxies remain well above stellar mass expectations for their redshifts" (6.2 Stellar mass census: the abundance of massive galaxies)

## Claim tuples

- H: Adding MIRI and ALMA data changes the SED-derived stellar mass and SFR of extremely red galaxies | E: Ran prospector on 29 sources with HST+NIRCam only and again with MIRI+ALMA added | R: Median 0.6 dex lower stellar mass and median factor 10 lower SFR for the most massive and star-forming sources | F: HST+NIRCam-only modeling overestimates mass and SFR for very red sources | **supported**
- H: The sample is dominated by faint dusty star-forming galaxies below the ALMA detection limit | E: Forced ALMA photometry and stacking in redshift bins from GOODS-ALMA and ASAGAO | R: 25 of 29 undetected; marginal stacked detections at z<5 and no stacked detection at 6<z<8 | F: Sample is likely faint, with small dust-obscured star formation at z<5 and not dominated by lower-luminosity DSFGs at 6<z<8 | **partially**
- H: The red rest-optical continuum of LRDs is dominated by obscured AGN emission | E: NIRCam-MIRI color-color diagrams, median MIRI stacks, prospector with empirical AGN templates, CIGALE, and ALMA stacks | R: MIRI SEDs turn over rather than rising; ALMA stack not detected | F: Stellar emission favored over a dominant obscured AGN, though not definitive | **partially**
- H: These previously missed sources contribute significantly to the obscured cosmic SFRD at 4<z<6 | E: Summed prospector SFRs per redshift bin and compared with the Zavala et al. 2021 obscured SFRD; repeated with ALMA stacks and a hotter-dust template | R: 26% of the obscured SFRD from log L_IR<12 sources at 4<z<5 versus 20% estimated previously, with a larger factor at z>5 | F: Obscured SFRD from faint sources could be underestimated, possibly doubling the obscured fraction at these redshifts | **partially**
- H: Some sources have stellar masses too high for the surveyed area under standard assumptions | E: Compared MIRI+ALMA stellar masses with a halo-mass-function based limit (HMF, Behroozi et al. 2013) for the MIRI area | R: One source at z=5.5 and five at z>~6.5 are improbably massive or require very efficient baryon conversion | F: Possible explanations are sub-dominant AGN light or errant modeling assumptions; spectroscopy needed | **partially**

## Reasoning

- Why this data: Exceptional ancillary data in GOODS-S/HUDF, including deep ALMA maps and MIRI, allow a detailed look at this population  
  > "Given the exceptional ancillary data that is available in this prime region of the sky, we focus on providing a detailed look at this population" (2 Datasets)
- Why this method: ALMA forced photometry and stacking constrain the far-infrared emission and thus the dust-obscured star formation  
  > "This critical constraint allows a more robust estimate of the dust-obscured star formation" (2.2.4 ALMA imaging)
- Alternative: Dirichlet SFH prior instead of continuity prior for six high-mass sources; masses consistent within uncertainties  
  > "instead using the Dirichlet prior (cite: Leja2017), which allows for sudden and extreme changes in SFR in adjacent time bins" (6.2.2 Potentially errant modeling assumptions)
- Alternative: CIGALE with SKIRTOR AGN models overpredicts MIRI flux, so AGN-dominant fits are disfavored  
  > "but these AGN dominant models significantly overpredict the MIRI observed SED at F1800W–F2100W" (5.2.3 Nature of the LRDs in Our Sample)
- How they decided it was enough: _not stated_
- Limitation (authors): Dust temperature assumed by prospector may bias SFR low; true uncertainty in stellar mass larger than quoted  
  > "More data sampling the far infrared SED to constrain the dust temperature would be needed to resolve the discrepancies between the different measurements." (6.1.1 Impact of modeling assumptions on the cosmic SFRD); "Thus, the true uncertainty in stellar mass is larger than implied in" (6.2.2 Potentially errant modeling assumptions)
- Caveat (inferred, ours): ALMA constraints come from inhomogeneous published maps with unspecified calibration, and detections versus limits are handled only in outline
- Caveat (inferred, ours): Stacks of non-detections are low significance and the SFRD result depends on assumed dust temperature
- Caveat (inferred, ours): Sample is small (29 with MIRI) and in a single field, so cosmic variance affects SFRD and mass-census claims
- Caveat (inferred, ours): Many conclusions rest on photometric redshifts and SED model assumptions, including the LRD nature

## Reproducibility

- Data public (paper): JWST data public via MAST; GOODS-ALMA imaging shared by the survey team, ASAGAO and HUDF maps from published works  
  > "Data used in this work are available via MAST at , and ." (Acknowledgements); "We thank Carlos Gomez-Guijarro and David Elbaz for sharing the GOODS-ALMA imaging." (Acknowledgements)
- Products in archive: _not stated_
- Missing: ALMA project codes and exact maps used
- Missing: Photometric catalog with fluxes for each source
- Missing: Stacking and likelihood details for ALMA constraints
- Missing: prospector sampler and run settings
- Missing: Spectroscopic redshift extraction (Sun et al. in preparation)
- Data volume (inferred): Large: JWST NIRCam and MIRI mosaics of GOODS-S plus HST HLF and ALMA maps; tens of GB
- Score (inferred): 2/5, Analysis relies on a JADES/SMILES photometric catalogue not released with the paper, ALMA maps made by other teams, and an unpublished stacking recipe; only the derived properties table is given.
- Rediscovery candidate: no, ALMA role is small, catalog photometry and stacking details are not provided, and the main results depend on a heavy SED-fitting pipeline.

## Links

- Method: Hatsukade et al. 2018 (cite: Hatsukade2018) (ASAGAO ALMA map and fluxes)
- Method: Franco et al. 2018 (cite: Franco2018) (GOODS-ALMA map and fluxes)
- Method: Rieke et al. 2023 (cite: Rieke2023b) (JADES photometric catalog methods)
- Method: Lyu et al. 2023 (cite: Lyu2023) (SMILES MIRI survey, reduction and extraction)
- Method: Ji et al. 2023 (cite: Ji2023) (Fiducial prospector setup)
- Method: Sun et al. 2021; Shivaei et al. 2022; Betti et al. 2019 (cite: Sun2021; Shivaei2022; Betti2019) (ALMA forced photometry method)
- Companion: Barrufet et al. 2023 (cite: Barrufet2023) (Earlier HST-dark selection and SFRD estimate)
- Companion: Labbe et al. 2023 (cite: Labbe2023b) (LRDs and deep ALMA limits)
- Companion: Greene et al. 2023 (cite: Greene2023) (LRD selection criteria)
- Companion: Zavala et al. 2021 (cite: Zavala2021) (Obscured SFRD comparison)
- Related: ASAGAO
- Related: GOODS-ALMA
- Related: HUDF ALMA footprint
- Related: JADES
- Related: JEMS
- Related: SMILES
- Related: FRESCO

## Checks

```json
{
 "quotes": 113,
 "quotes_ok": 113,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 0,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2012.1.00173.S",
  "2015.1.00098.S",
  "2015.1.00543.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 13,
 "numeric_problems": 0,
 "fill": {
  "facts": 116,
  "stated": 77,
  "rate": 0.664
 },
 "evidence_ok": true
}
```
