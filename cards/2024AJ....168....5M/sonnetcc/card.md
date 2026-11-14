# Hα Emission and H II Regions at the Locations of Recent Supernovae in Nearby Galaxies

`2024AJ....168....5M` | The Astronomical Journal 2024 | first author: Mayker Chen, Ness | arXiv: 2404.10762 | DOI: 10.3847/1538-3881/ad3fb7

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth light | type multi_facility_alma_minor

## Science

- Fields: nearby_galaxies, transients, star_formation
- Question: How often do recent (<=125 yr) supernovae in nearby star-forming galaxies occur coincident with H II regions (Halpha at 50-100 pc scale), after controlling for chance overlap, and how does this depend on SN type and CO (2-1) presence  
  > "to assess the coincidence between recent supernovae (SNe) and H II regions" (Introduction); "This measurement can help constrain both the nature of SN progenitors and the environments into which SNe explode." (Introduction)
- Target **32 recent SNe in 10 PHANGS-MUSE galaxies (NGC 1087, 1300, 1365, 1433, 1566, 1672, 3627, 4254, 4303, 4321)**: coordinates SN RA/Dec given in decimal degrees in the SN table (per SN)  
  > "We select a population of 32 SNe within 10 galaxies in the PHANGS–MUSE galaxy footprints." (2.2 SN selection); "distance in Mpc" (Table 3 notes); z/distance 11.32-19.57 Mpc per host galaxy (SN measurements table)  
  > "We select a population of 32 SNe within 10 galaxies in the PHANGS–MUSE galaxy footprints." (2.2 SN selection); "distance in Mpc" (Table 3 notes); distance from _not stated_

## Data provenance

- ALMA projects: 2012.1.00650.S, 2013.1.00803.S, 2013.1.01161.S, 2015.1.00121.S, 2015.1.00782.S, 2015.1.00925.S, 2015.1.00956.S, 2016.1.00386.S, 2017.1.00392.S, 2017.1.00766.S, 2017.1.00886.L, 2018.1.00484.S, 2018.1.01321.S, 2018.1.01651.S, 2018.A.00062.S, 2019.1.01235.S, 2019.2.00129.S
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: PHANGS-ALMA CO (2-1) maps have resolution similar to the MUSE Halpha maps (text gives approx. 1 arcsec)  
  > "These data have similar resolution to the MUSE" (2.1 Data); "Those ALMA CO data have resolution" (3.6 Zooming in on individual regions)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: PHANGS-ALMA CO (2-1) survey data processed by the survey team (Leroy et al. 2021)  
  > "We trace molecular gas surface density using CO (2–1) maps from the PHANGS–ALMA survey (cite: Leroy2021)." (2.1 Data); "This paper makes use of the following ALMA data, which have been processed as part of the PHANGS–ALMA CO (2–1) survey" (Acknowledgments)
- Line: CO J=2-1 (not stated)
- Other facility **VLT/MUSE (PHANGS-MUSE survey)**: Attenuation-corrected Halpha maps (copt products), Balmer decrement extinction, nebular catalog; core comparison data set  
  > "We use the “copt” convolved and optimized standard products." (2.1 Data); "PHANGS–MUSE, our core comparison data set" (Introduction)
- Other facility **Hubble Space Telescope (narrowband Halpha, program 15654)**: New ~0.1 arcsec narrowband Halpha maps used only for qualitative comparison  
  > "Because these data are quite new and still in a preliminary state, we use them here primarily for a qualitative comparison" (2.1 Data); "These observations are associated with program 15654." (Acknowledgments)
- Other facility **Spitzer/IRAC 3.6 micron (S4G)**: Near-IR stellar mass tracer used to draw a control SN population  
  > "We trace the surface density of stellar mass using near-IR ($3.6\mu$m) maps from the Infrared Array Camera (IRAC) on the *Spitzer Space Telescope*." (2.1 Data)
- Other facility **Open Supernova Catalog and Transient Name Server**: SN positions, discovery dates and types for the <125 yr sample  
  > "we gather a population of recent ($<$ 125 years) SNe using the Open Supernova Catalog (OSC)[^1] and the Transient Name Server (TNS)[^2]" (2.2 SN selection)
- External data: Attenuation-corrected PHANGS-MUSE Halpha maps (copt)  
  > "produced by (cite: Belfiore2023) (cite: Pessa2021)" (2.1 Data) [from (cite: Belfiore2023) (cite: Pessa2021)]
- External data: PHANGS nebular catalog giving H II region footprints, BPT flags, metallicities, velocity dispersions and A_V  
  > "we use the PHANGS nebular catalog (cite: Groves2023; Santoro2022) to determine where there is an H II region along the line of sight" (2.1 Data) [from (cite: Groves2023; Santoro2022)]
- External data: PHANGS-ALMA CO (2-1) broad moment-0 maps for CO detection  
  > "we require a signal-to-noise ratio of 3 in the integrated intensity maps masked with a" (4.1 H-alpha and CO) [from (cite: Leroy2021)]
- External data: Spitzer 3.6 micron maps as processed for PHANGS  
  > "details of their processing and origin in the context of PHANGS is described in (cite: Querejeta2021)" (2.1 Data) [from (cite: Sheth2010; Querejeta2021)]
- External data: MUSE-based Balmer-decrement extinction (A_V) method, R_V = 3.1 with O'Donnell 1994 curve  
  > "We adopt the calculations from (cite: Belfiore2023; Belfiore2022)" (4.2 H-alpha and the Balmer Decrement) [from (cite: Belfiore2023; Belfiore2022; Odonnell1994)]
- External data: Scal metallicity estimates for individual H II regions  
  > "These estimates use the metallicity reported in (cite: Groves2023) based on" (4.3 Additional Diagnostics) [from (cite: Groves2023; Pilyugin:2016)]
- External data: SN classification references for each SN (type column of SN table)  
  > "the reference paper used for their type classification" (2.2 SN selection) [from per-SN references in the SN table (e.g. cite: Leonard2013, cite: Andrews2021)]
- Simulation/model as data: STARBURST99 simple stellar population (default assumptions) used for SN delay-time and ionizing-photon CDFs  
  > "using the default assumptions from STARBURST99 (cite: Leitherer1999; Leitherer2014)" (3.3 Comparisons to expectations from SSP Models)

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
- masking: CO detection requires S/N >= 3 in PHANGS-ALMA integrated intensity maps masked with the 'broad' mask  
  > "we require a signal-to-noise ratio of 3 in the integrated intensity maps masked with a" (4.1 H-alpha and CO)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- SN sample compilation approach (OSC + TNS, <125 yr)  
  > "Following (cite: MaykerChen2023a), we gather a population of recent" (2.2 SN selection) [from (cite: MaykerChen2023a)]
- Control model populations  
  > "Similar to (cite: MaykerChen2023a), we use several model populations as controls" (2.3 Relative positions of SNe, HII regions, and statistical controls) [from (cite: MaykerChen2023a)]
- Expected overlap with CO and with CO plus H II region  
  > "Following (cite: MaykerChen2023a) we also calculate the expected overlap with CO emission" (2.3 Relative positions of SNe, HII regions, and statistical controls) [from (cite: MaykerChen2023a)]
- Handling of PHANGS-ALMA CO (2-1) data  
  > "with more description of how we handle the PHANGS–ALMA CO (2–1) data, see (cite: MaykerChen2023a)" (2.1 Data) [from (cite: MaykerChen2023a)]
- HST narrowband Halpha processing  
  > "these data have been processed following a scheme similar to that described in (cite: Lee2022) and (cite: Barnes2022)" (3.6 Zooming in on individual regions) [from (cite: Lee2022) and (cite: Barnes2022)]
- MUSE astrometry calibration against Gaia  
  > "The MUSE astrometry is calibrated against Gaia via a procedure detailed in (cite: Emsellem2022)" (2.1 Data) [from (cite: Emsellem2022)]
- H II region identification with HIIphot using a single termination gradient  
  > "For more information, see §3.1 of (cite: Groves2023)." (2.1 Data) [from (cite: Groves2023)]

### Not stated but needed to reproduce (our reading)

- ALMA bands, array configurations, and observing details are not given; the CO maps are only referenced to Leroy et al. 2021
- Which PHANGS-ALMA CO data release/product version and the noise maps used for the S/N>=3 test
- Exact definition of the 'excess' (how 41% is combined with the local/near-IR control fractions to give 7.6% and 19.2%) and of the binomial error
- How a SN position is assigned to a MUSE pixel and how positional uncertainty is propagated (none applied beyond discussion)
- Exact footprint masks and sampling scheme used to draw the 1,000 model SNe per SN, and random seeds
- KDE bandwidth and CDF/NCR binning choices
- MUSE data release version of the copt maps and nebular catalog
- HST Halpha maps are unpublished ('in preparation') and not obtainable for reproduction
- SB99 inputs beyond 'default assumptions' (metallicity, IMF limits, mass)

## Analysis recipe

1. **compile recent SN sample**: Select SNe discovered <125 yr ago from OSC and TNS with a recorded discovery date in PHANGS-MUSE footprints; remove 4 objects to leave 32 SNe in 10 galaxies  
  > "To avoid including these, we only select SNe that have a recorded discovery date." (2.2 SN selection); "This reduces our working sample to 32 SNe within 10 galaxies" (2.2 SN selection)
   - parameter: Age < 125 years; 36 SNe in 11 galaxies initially, 4 removed (2 outside map coverage, SN2019krl uncertain type, SN2017gax contaminated spectrum)  
  > "A total of 36 SNe in 11 galaxies were originally identified" (2.2 SN selection)
   - assumption: Positional uncertainty of order 1 arcsec for modern SNe, up to ~10 arcsec for early SNe such as SN1926A  
  > "However positional uncertainties for early SNe, such as SN1926A, could be as high as" (2.2 SN selection)
   - fitting: _not stated_
   - validation: _not stated_
2. **test SN coincidence with H II regions**: For each SN, check whether its pixel lies inside a Groves et al. 2023 nebular-catalog H II region (HIIphot masks), measure distance to nearest H II-region pixel, and record Halpha intensity at the SN  
  > "We measure whether each SN occurs inside a known H II region, note the distance to the nearest pixel in the H II region" (2.3 Relative positions of SNe, HII regions, and statistical controls)
   - software: HIIphot
   - parameter: MUSE copt convolved-and-optimized Halpha maps, native resolution 33-104 pc  
  > "We use the “copt” convolved and optimized standard products." (2.1 Data)
   - assumption: Line-of-sight coincidence at MUSE resolution; Halpha within H II regions treated as star-formation powered (BPT flags all star-forming)  
  > "We emphasize that this calculation is focused on coincidence *along the line of sight at the MUSE resolution*." (3.1 Fraction of SNe in H II regions)
   - fitting: _not stated_
   - validation: BPT flags and low velocity dispersions checked to confirm emission is consistent with H II regions  
  > "all 13 SNe that are within the line of sight of nebular emission show diagnostics suggesting that the nebular emission is caused by star formation" (2.1 Data)
3. **build random-coincidence control populations**: Draw model SNe under four scenarios (purely random, random within 500 pc or 1 kpc box around each SN, following Halpha intensity, following 3.6 micron near-IR intensity) and compute their H II/CO coincidence  
  > "We generate 1,000 model SNe for each SN in our sample. This gives us a total of 32,000 model SNe from 10 galaxies generated for each model." (2.3 Relative positions of SNe, HII regions, and statistical controls)
   - parameter: 1,000 model SNe per real SN; 32,000 per model  
  > "We generate 1,000 model SNe for each SN in our sample." (2.3 Relative positions of SNe, HII regions, and statistical controls)
   - parameter: Local boxes of 500 pc x 500 pc or 1 kpc x 1 kpc centred on each SN  
  > "Here we define “nearby” as boxes" (3.1 Fraction of SNe in H II regions)
   - assumption: Near-IR 3.6 micron intensity traces stellar mass with no mass-to-light correction  
  > "We use the near-IR intensity for this purpose and do not make any corrections to account for local variations in the stellar mass-to-light ratio." (2.1 Data)
   - fitting: _not stated_
   - validation: _not stated_
4. **estimate excess of SNe in H II regions over chance**: Contrast fraction of SNe coincident with H II regions with local covering fractions of H II regions; uncertainty from binomial distribution  
  > "Contrasting these local covering fractions with the fraction of SNe coincident with H II regions" (3.1 Fraction of SNe in H II regions); "Using a binomial distribution we estimate the uncertainty due to stochasticity to be" (3.1 Fraction of SNe in H II regions)
   - fitting: _not stated_
   - validation: _not stated_
5. **break results down by SN type**: Repeat coincidence and excess statistics for SESNe, SNe II, SNe Ia and unclassified SNe, and for CCSNe combined  
  > "shows the fraction of SNe coincident with H II regions broken down by type." (3.2 Breakdown by type)
   - assumption: Progenitor mass sequence SNe Ia < SNe II < SESNe  
  > "As a reminder the progenitor mass sequence from lowest to higher is believed to be" (3.2 Breakdown by type)
   - fitting: _not stated_
   - validation: Probability that controls place 4/4 SESNe in H II regions is 1.2%  
  > "the probability of our controls randomly placing SNe coincident to an H II region 4/4 times is only 1.2%" (3.2 Breakdown by type)
6. **compare distances to H II regions and Halpha intensities with controls**: KDE and CDF of distance to nearest H II-region pixel; normalized cumulative rank (NCR) and CDFs of Halpha intensity at SN sites versus model populations  
  > "assigning a percentile in the CDF to each" (3.5 Intensity of H-alpha emission); "The left panel of Figure [6](#fig:Distances) shows the kernel density estimation (KDE) of the distances from each SN to the nearest H II region" (3.4 Distance from SNe to H II regions)
   - parameter: NCR evaluated at native, 150 pc and 1 kpc resolutions  
  > "at native, 150 pc, and 1 kpc resolutions" (3.5 Intensity of H-alpha emission)
   - fitting: _not stated_
   - validation: Compared with 32,000-SN model populations; model scatter shown as 16th-84th percentile  
  > "Shaded regions represent the" (3.5 Intensity of H-alpha emission)
7. **compare with SSP expectations**: STARBURST99 simple stellar population CDFs of SN counts and H-ionizing photon production versus time  
  > "We plot the cumulative distribution functions (CDFs) as a function of time for both number of SNe explosions and H ionizing photon production" (3.3 Comparisons to expectations from SSP Models)
   - software: STARBURST99
   - parameter: Default STARBURST99 assumptions, fully sampled IMF  
  > "using the default assumptions from STARBURST99 (cite: Leitherer1999; Leitherer2014)" (3.3 Comparisons to expectations from SSP Models)
   - assumption: Fully sampled IMF  
  > "the Starburst99 models assume a fully-sampled IMF" (3.3 Comparisons to expectations from SSP Models)
   - fitting: _not stated_
   - validation: _not stated_
8. **assess CO (2-1) coincidence**: Classify each SN as H II only, H II+CO, CO only or neither using PHANGS-ALMA broad moment-0 CO (2-1) maps with S/N >= 3, and repeat control scenarios  
  > "we identify which SNe in our sample occur coincident with only CO (2–1) emission, an H II region, both, or neither" (4.1 H-alpha and CO)
   - parameter: CO detection when S/N >= 3 in integrated intensity map with broad mask  
  > "we require a signal-to-noise ratio of 3 in the integrated intensity maps masked with a" (4.1 H-alpha and CO)
   - assumption: Only CO (2-1) detection used; no alpha_CO variation accounted for  
  > "We are only considering CO (2-1) detections in this work and not accounting for" (4.1 H-alpha and CO)
   - fitting: _not stated_
   - validation: _not stated_
9. **measure extinction at SN sites**: A_V from the Balmer decrement (Hbeta/Halpha) maps along each SN line of sight, compared inside versus outside H II regions and with all MUSE pixels  
  > "we measure extinction, expressed as $A_V$ values, based on the Balmer decrement along the line-of-sight towards each of our SNe" (4.2 H-alpha and the Balmer Decrement)
   - parameter: R_V = 3.1 with O'Donnell 1994 extinction curve  
  > "which adopts $R_{\rm V} = 3.1$ and an (cite: Odonnell1994) extinction curve" (4.2 H-alpha and the Balmer Decrement)
   - assumption: Foreground screen geometry; extinction is toward the ionized gas, not necessarily the SN  
  > "assuming a foreground screen geometry" (4.2 H-alpha and the Balmer Decrement)
   - fitting: _not stated_
   - validation: _not stated_
10. **qualitative zoom comparison of MUSE and HST Halpha**: 500 pc x 500 pc cutouts of MUSE and HST Halpha around each SN with H II region and CO footprints overplotted  
  > "plotting $500~{\rm pc} \times 500~{\rm pc}$ cutouts of H$\alpha$ emission around each of the 32 SNe in our sample" (3.6 Zooming in on individual regions)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **HIIphot** : Identify H II regions in the PHANGS nebular catalog (Groves et al. 2023)  
  > "These H II regions are identified using the HIIphot algorithm (cite: Thilker2000)" (2.1 Data)
- **STARBURST99** : Simple stellar population SN and ionizing photon CDFs  
  > "using the default assumptions from STARBURST99 (cite: Leitherer1999; Leitherer2014)" (3.3 Comparisons to expectations from SSP Models)
- **Astropy** : listed as software used in this work; specific purpose not stated  
  > "This work has utilized the following software: Jupyter (cite: Kluyver2016), Astropy (cite: Astropy2013; Price-Whelan2018), Pandas (cite: McKinney2010), NumPy (cite: VanDerWalt2011; Harris2020), SciPy (cite: Virtanen2020), Seaborn (cite: Waskom2017), Matplotlib (cite: Hunter2007), & GitHub (cite: github)." (Acknowledgments)
- **Pandas** : listed as software used in this work; specific purpose not stated  
  > "This work has utilized the following software: Jupyter (cite: Kluyver2016), Astropy (cite: Astropy2013; Price-Whelan2018), Pandas (cite: McKinney2010), NumPy (cite: VanDerWalt2011; Harris2020), SciPy (cite: Virtanen2020), Seaborn (cite: Waskom2017), Matplotlib (cite: Hunter2007), & GitHub (cite: github)." (Acknowledgments)
- **NumPy** : listed as software used in this work; specific purpose not stated  
  > "This work has utilized the following software: Jupyter (cite: Kluyver2016), Astropy (cite: Astropy2013; Price-Whelan2018), Pandas (cite: McKinney2010), NumPy (cite: VanDerWalt2011; Harris2020), SciPy (cite: Virtanen2020), Seaborn (cite: Waskom2017), Matplotlib (cite: Hunter2007), & GitHub (cite: github)." (Acknowledgments)
- **SciPy** : listed as software used in this work; specific purpose not stated  
  > "This work has utilized the following software: Jupyter (cite: Kluyver2016), Astropy (cite: Astropy2013; Price-Whelan2018), Pandas (cite: McKinney2010), NumPy (cite: VanDerWalt2011; Harris2020), SciPy (cite: Virtanen2020), Seaborn (cite: Waskom2017), Matplotlib (cite: Hunter2007), & GitHub (cite: github)." (Acknowledgments)
- **Seaborn** : listed as software used in this work; specific purpose not stated  
  > "This work has utilized the following software: Jupyter (cite: Kluyver2016), Astropy (cite: Astropy2013; Price-Whelan2018), Pandas (cite: McKinney2010), NumPy (cite: VanDerWalt2011; Harris2020), SciPy (cite: Virtanen2020), Seaborn (cite: Waskom2017), Matplotlib (cite: Hunter2007), & GitHub (cite: github)." (Acknowledgments)
- **Matplotlib** : listed as software used in this work; specific purpose not stated  
  > "This work has utilized the following software: Jupyter (cite: Kluyver2016), Astropy (cite: Astropy2013; Price-Whelan2018), Pandas (cite: McKinney2010), NumPy (cite: VanDerWalt2011; Harris2020), SciPy (cite: Virtanen2020), Seaborn (cite: Waskom2017), Matplotlib (cite: Hunter2007), & GitHub (cite: github)." (Acknowledgments)
- **Jupyter** : listed as software used in this work; specific purpose not stated  
  > "This work has utilized the following software: Jupyter (cite: Kluyver2016), Astropy (cite: Astropy2013; Price-Whelan2018), Pandas (cite: McKinney2010), NumPy (cite: VanDerWalt2011; Harris2020), SciPy (cite: Virtanen2020), Seaborn (cite: Waskom2017), Matplotlib (cite: Hunter2007), & GitHub (cite: github)." (Acknowledgments)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Fraction of SNe coincident with an H II region | 41% (13/32) | binomial stochasticity +/-8.7% | percent | 2 | We find that 41% (13/32) of our SNe occur coincident with an H II region. |
| Fraction of map pixels coincident with H II regions (purely random control) | 13.7% | not stated | percent | 3 | across our galaxy sample, 13.7% of map pixels are coincident with H II regions |
| Local covering fraction of H II regions, 1 kpc box (control) | 32% | not stated | percent | 3 | For comparison, H II regions cover 32% of the area within |
| Local covering fraction of H II regions, 500 pc box (control) | 36% | not stated | percent | 3 | This fraction increases to 36% if we instead consider fields of size |
| Fraction of near-IR emission within H II regions (control) | 32% | not stated | percent | 3 | We find that 32% of near-IR emission emerges from regions coincident with H II regions. |
| Excess of all SNe associated with H II regions | 7.6% | 8.7% | percent | 4 | we find a statistical excess of 7.6% $\pm$ 8.7% of all SNe to be associated with H II regions |
| Excess of core-collapse SNe associated with H II regions | 19.2% | 10.4% | percent | 5 | This increases to an excess of 19.2% $\pm$ 10.4% when considering only core-collapse SNe. |
| Excess of stripped-envelope SNe associated with H II regions | 38% | 23.5% | percent | 5 | when considering only SESNe we find an excess of 38% $\pm$ 23.5% |
| Fraction of SNe II and SESNe in H II regions | SNe II 42% (8/19); SESNe 100% (4/4) | not stated | percent | 5 | (8/19) of SNe II, and 100% (4/4) of our stripped envelope SNe |
| Fraction of SNe Ia in H II regions (text) | 20% (1/6) | not stated | percent | 5 | We find that 20% (1/6) of SNe Ia |
| Probability that controls place 4/4 SESNe in H II regions | 1.2% | not stated | percent | 5 | the probability of our controls randomly placing SNe coincident to an H II region 4/4 times is only 1.2% |
| Median distance to nearest H II region, SNe II | 10 | not stated | pc | 6 | with a median distance of 10 pc |
| Median distance to nearest H II region, SNe Ia | 110 | not stated | pc | 6 | with a median distance of 110 pc |
| SB99 CCSN delay-time range and time of first 20% of SNe | 3-37 Myr; first 20% of SNe by 7.11 Myr | not stated | Myr | 7 | In the SB99 model, the delay-time for CCSNe ranges from $3-37$ Myr, with the first $20\%$ of SNe occurring by 7.11 Myr. |
| Fraction of H II-region SNe with CO (2-1) detected | 85% (11/13) | not stated | percent | 8 | Of the H II region associated SNe, 85% (11/13) also have associated detected CO (2–1) emission |
| Median A_V of SN sites inside H II regions (16-84% range 0.75-1.47) | 1.03 | 16-84% range 0.75-1.47 | mag | 9 | median $A_V=$ 1.03 mag with a $16{-}84\%$ range of $0.75-1.47$ mag |
| Median A_V of SN sites outside H II regions (16-84% range 0-0.92) | 0.33 | 16-84% range 0-0.92 | mag | 9 | median $A_V=$ 0.33 mag with a $16{-}84\%$ range of 0–0.92 mag |
| Highest A_V at any SN site | 2.35 | not stated | mag | 9 | the highest extinction value associated with any SN in our sample is $A_V =$ 2.35 mag |

## Qualitative findings

- SNe tend to explode near but not within H II regions; no SN with HST Halpha coverage lies on a high-resolution Halpha peak  
  > "We overwhelmingly see that our SN sites are off to the sides of the H II region, rather than enclosed at least partially by shells." (3.6 Zooming in on individual regions)
- Association with H II regions and Halpha rises with progenitor mass (SNe Ia < SNe II < SESNe)  
  > "As the progenitor mass increases, we find an increasing association with higher" (3.5 Intensity of H-alpha emission)
- SN sites show typical extinctions with no strong evidence for a deeply embedded population, supporting pre-SN gas clearing  
  > "These results indicate that SNe appear associated with typical extinctions, providing no strong evidence that there is a large population of deeply embedded SNe." (4.2 H-alpha and the Balmer Decrement)

## Claim tuples

- H: Do recent SNe preferentially occur within H II regions beyond chance overlap | E: Coincidence of 32 SNe with Groves et al. 2023 H II regions versus four control populations | R: 41% (13/32) of SNe coincide with H II regions versus ~32-36% expected from local/near-IR controls; excess 7.6% +/- 8.7% (all), 19.2% +/- 10.4% (CCSNe) | F: Only a modest fraction of SNe are truly associated with H II regions; much of the overlap is chance | **supported**
- H: Does H II region association depend on SN type (progenitor mass) | E: Type-split coincidence fractions, distances and Halpha intensity CDFs | R: SESNe 4/4 in H II regions, SNe II 8/19, SNe Ia 1/6; SESNe intensity distribution resembles Halpha maps | F: Association increases with progenitor mass, consistent with earlier lower-resolution work | **supported**
- H: Do SNe explode near rather than in H II regions at higher resolution | E: Qualitative comparison of MUSE and new HST Halpha cutouts around each SN | R: SN sites lie off to the sides of H II regions; none on a high-resolution Halpha peak | F: Many SNe detonate near but not in H II regions, consistent with the statistical estimate, but SN astrometry limits firm conclusions | **partially**
- H: Do H II-region SNe also coincide with molecular gas | E: Coincidence with PHANGS-ALMA CO (2-1) detections (S/N >= 3) with H II regions and controls | R: 85% (11/13) of H II-region SNe have CO (2-1); CO-only sightlines consistent with random coincidence | F: SNe in H II regions almost always also coincide with CO, though resolution is coarse so blending is likely | **supported**
- H: Are SNe preferentially located in high-extinction (embedded) regions | E: Balmer-decrement A_V at each SN site compared to all MUSE pixels | R: A_V 0-2.35 mag; median 1.03 mag inside and 0.33 mag outside H II regions | F: Typical extinctions, consistent with pre-clearing of gas before explosion | **supported**

## Reasoning

- Why this data: PHANGS galaxies are nearby so ground-based MUSE reaches <~100 pc resolution, allowing better localization of SNe and rich multi-wavelength controls  
  > "Because PHANGS targets very nearby galaxies, even seeing-limited ground-based observations achieve physical resolution" (Introduction)
- Why this method: Control populations are needed because H II regions cover a large fraction of the maps, so random coincidence is high  
  > "we also construct several control scenarios to assess the probability of random coincidence" (2.3 Relative positions of SNe, HII regions, and statistical controls)
- Alternative: SNe Ia expected to trace near-IR stellar light rather than Halpha, so the near-IR control is used alongside the Halpha-following control  
  > "This helps model SNe that trace the distribution of stellar masses, which should be appropriate for populations with longer delay times" (2.3 Relative positions of SNe, HII regions, and statistical controls)
- How they decided it was enough: _not stated_
- Limitation (authors): SN positional uncertainty (up to ~10 arcsec for old SNe) limits coincidence and HST comparison  
  > "We caution that the positional uncertainty for the SNe represents a major limiting factor when comparing to the HST" (3.6 Zooming in on individual regions)
- Limitation (authors): HST Halpha data are preliminary and used only qualitatively  
  > "Because these data are quite new and still in a preliminary state, we use them here primarily for a qualitative comparison" (2.1 Data)
- Limitation (authors): SESNe sample is extremely small (4 SNe)  
  > "Although the SESNe sample is extremely small (only 4 SNe)" (3.2 Breakdown by type)
- Limitation (authors): Heterogeneous SN compilation unsuitable for SN rate studies  
  > "the heterogeneous nature of our SN compilation makes it poorly suited to study SN rates" (4.3 Additional Diagnostics)
- Limitation (authors): Extinction measured toward ionized gas assuming a foreground screen, not necessarily toward the SN  
  > "assuming a foreground screen geometry" (4.2 H-alpha and the Balmer Decrement)
- Caveat (inferred, ours): The excess estimate depends on an ad hoc choice of control fraction (32-36%) and the binomial error ignores positional uncertainty and control-sample variance
- Caveat (inferred, ours): Small samples (32 SNe, 4 SESNe, 6 SNe Ia) give large uncertainties; the SN Ia value is quoted as 17% in the table and 20% in the text
- Caveat (inferred, ours): MUSE resolution of 33-104 pc exceeds typical H II region sizes so coincidence is line-of-sight overlap, not physical association
- Caveat (inferred, ours): ALMA data are only used as a detection flag, so ALMA-specific processing is entirely delegated to Leroy et al. 2021 and Mayker Chen et al. 2023

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Analysis code not released and no repository link given
- Missing: HST narrowband Halpha maps are unpublished
- Missing: Exact excess/binomial uncertainty formulas and control-sampling details
- Missing: ALMA observing and processing details (delegated to PHANGS-ALMA paper)
- Data volume (inferred): Moderate: PHANGS-MUSE Halpha maps and nebular catalog for 10 galaxies, PHANGS-ALMA CO moment-0 maps (not raw visibilities), 3.6 micron images; roughly a few GB of derived products
- Score (inferred): 3/5, SN table with coordinates and types, named public-survey maps/catalogs and numeric results are given, but control and excess definitions are only partly specified, no code is released, and HST maps are unpublished.
- Rediscovery candidate: no, The recipe for the excess statistic and controls is not fully specified and the HST comparison uses unpublished data; ALMA plays only a CO-detection role.

## Links

- Method: (cite: Leroy2021) (PHANGS-ALMA CO (2-1) survey data and maps used for CO detection)
- Method: (cite: Emsellem2022) (PHANGS-MUSE survey data and astrometry)
- Method: (cite: Groves2023) (Nebular catalog giving H II region footprints and BPT/metallicity diagnostics)
- Method: (cite: Belfiore2023) (Attenuation-corrected Halpha maps and Balmer-decrement extinction)
- Companion: (cite: MaykerChen2023a) (First paper comparing SNe to PHANGS-ALMA CO (2-1); source of the SN selection and control approach)
- Companion: (cite: Barnes2022) (HST Halpha imaging approach for NGC 1672)
- Related: PHANGS-MUSE
- Related: PHANGS-ALMA
- Related: PHANGS-HST Halpha
- Related: S4G

## Checks

```json
{
 "quotes": 130,
 "quotes_ok": 130,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 17,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [
  "2019.1.01235.S",
  "2019.2.00129.S"
 ],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 18,
 "numeric_problems": 0,
 "fill": {
  "facts": 125,
  "stated": 73,
  "rate": 0.584
 },
 "evidence_ok": true
}
```
