# Protoplanetary Disks in the Orion OMC1 Region Imaged with ALMA

`2016ApJ...826...16E` | The Astrophysical Journal 2016 | first author: Eisner, J. A. | arXiv: 1604.03134 | DOI: 10.3847/0004-637X/826/1/16

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks, star_formation
- Question: How many protoplanetary disks in the ONC OMC1 region are detected at 1.3 mm, what are their dust/total masses and gas content, and what does the mass distribution imply for giant planet formation?  
  > "We mosaicked a field containing $\sim 600$ near-IR-identified young stars, around which we can search for sub-mm emission tracing dusty disks." (abstract)
- Target **Orion Nebula Cluster, OMC1 BN/KL outflow region**: coordinates _not stated_; z/distance ~400 pc  
  > "At the distance to Orion, $\sim 400$ pc (cite: SANDSTROM+07; MENTEN+07; KRAUS+07), the linear resolution is approximately 400 AU." (2.1 ALMA Cycle 2 Observations); distance from Sandstrom+07; Menten+07; Kraus+07  
  > "At the distance to Orion, $\sim 400$ pc (cite: SANDSTROM+07; MENTEN+07; KRAUS+07), the linear resolution is approximately 400 AU." (2.1 ALMA Cycle 2 Observations)

## Data provenance

- ALMA projects: _none stated_
- bands: Band 6 (1.3 mm, 230 GHz)  
  > "The fields were observed at 230 GHz frequency (Band 6), corresponding to a wavelength of 1.3 mm." (2.1 ALMA Cycle 2 Observations)
- frequencies and spectral setup: four 1.875 GHz continuum bands centered at 216, 228, 231, 233 GHz; effective central frequency 225 GHz; ~1 MHz resolution (1.3 km/s)  
  > "We observed continuum emission using four 1.875 GHz- wide bands centered at 216, 228, 231, and 233 GHz." (2.1 ALMA Cycle 2 Observations); "All spectral windows had frequency resolution of about 1 MHz, providing velocity resolution of 1.3 km s$^{-1}$." (2.1 ALMA Cycle 2 Observations)
- continuum bandwidth: _not stated_
- arrays: ALMA 12m mosaic (108 NW + 39 SE pointings); ACA obtained but not used  
  > "ALMA Compact Array (ACA) observations were also obtained as part of this program in order to map the extended outflow well, but we do not use these data here" (2.1 ALMA Cycle 2 Observations)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ~1 arcsec; beam ~1.4x0.8 arcsec  
  > "The angular resolution of the observations was approximately $1''$." (2.1 ALMA Cycle 2 Observations)
- max recoverable scale: _not stated_
- sensitivity: 0.5 mJy/beam typical continuum; 5 mJy km/s per channel  
  > "Typical noise values in clean regions of the continuum image are 0.5 mJy/beam." (2.1 ALMA Cycle 2 Observations)
- time on source: _not stated_
- observing dates: 19 July 2014 to 05 April 2015  
  > "Observations were taken between 19 July 2014 and 05 April 2015." (2.1 ALMA Cycle 2 Observations)
- pi or archival as stated: _not stated_
- Line: CO 2-1 (231 GHz)
- Line: C18O 2-1 (218 GHz)
- Other facility **Gemini South GeMS**: Ks-band near-IR imaging yielding 40 new sources  
  > "We observed the OMC1 region in Orion with GeMS at the Gemini South telescope between 30 December 2012 and 28 February 2013" (2.2 GeMS Near-IR Imaging)
- Other facility **JVLA (Sheehan et al. 2016)**: 3.6 and 6 cm continuum for free-free constraints  
  > "Their maps of 3.6 and 6 cm continuum emission cover the entire area of the ALMA mosaic presented here." (3 Results)
- External data: Near-IR cluster member catalog  
  > "We therefore make use of previous near-IR observations that identified cluster members (cite: HC00)." (2.2 GeMS Near-IR Imaging) [from (cite: HC00)]
- External data: HST proplyd catalog  
  > "We searched for 1.3 mm continuum emission towards the positions of HST-detected proplyds (cite: RRS08)" (3 Results) [from (cite: RRS08)]
- External data: cm-wavelength fluxes for free-free modeling  
  > "We used previous observations of the ONC at cm wavelengths from (cite: FELLI+93a; FELLI+93b; ZAPATA+04; FORBICH+07)" (3 Results) [from (cite: FELLI+93a; FELLI+93b; ZAPATA+04; FORBICH+07); Sheehan et al. 2016]
- External data: Spectroscopic stellar masses  
  > "Stellar masses, where available, are taken from the literature" (Table 2) [from (cite: HILLENBRAND97; LUHMAN+00; SLESNICK+04; HILLENBRAND+13; INGRAHAM+14)]
- External data: Disk masses of Mann et al. ALMA Cycle 0 sample  
  > "If we include the ALMA data of (cite: MANN+14), which are sensitive to the same range of disk masses probed in this work" (4.3 Disk Mass versus Cluster Radius) [from (cite: MANN+14)]
- Simulation/model as data: Williams & Best 2014 disk models predict 12CO(2-1) flux 0.1-5 Jy km/s for 0.01 Msun disk  
  > "Models presented in (cite: WB14) suggest that a disk with total mass of 0.01 M$_{\odot}$ should exhibit a $^{12}$CO(2-1) flux of $\sim 0.1$–5 Jy km s$^{-1}$." (4.5 Gas-to-Dust Ratios)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: Reduced ALMA data products adopted  
  > "We adopted the reduced ALMA data products." (2.1 ALMA Cycle 2 Observations)
- flux calibrator: Uranus and Ganymede among calibrators (with J0607-0834, J0541-0541, J0423-013, J0725-0054)  
  > "The sources used for calibration included J0607-0834, J0541-0541, J0423-013, J0725-0054, Uranus, and Ganymede." (2.1 ALMA Cycle 2 Observations)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: Briggs robust = 0.5  
  > "The $uv$ data were inverted using a Briggs robust weighting parameter of 0.5" (2.1 ALMA Cycle 2 Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: Line-contaminated parts of bandpass flagged for continuum  
  > "Substantial parts of the bandpass contained spectral line emission and were flagged for the continuum data reduction." (2.1 ALMA Cycle 2 Observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: ~1.4 x 0.8 arcsec  
  > "resulting in a synthesized beam with dimensions $\sim 1\rlap{.}''4 \times 0\rlap{.}''8$." (2.1 ALMA Cycle 2 Observations)
- final rms: 0.5 mJy/beam typical in clean regions; line channel 5 mJy km/s (up to ~20)  
  > "The rms varies across the field because of strong extended emission from OMC1." (2.1 ALMA Cycle 2 Observations)

### Inherited from earlier work

- Free-free plus optically thin dust (beta=1) model approach for mm flux decomposition  
  > "thin free-free emission short-ward of that turnover, and optically-thin dust with $\beta=1$ (cite: EISNER+08)" (3 Results) [from (cite: EISNER+08)]
- Dust opacity kappa_0=2 cm2/g at 1.3 mm, beta=1  
  > "We assume $d \approx 400$ pc, $\kappa_0=2$ cm$^{2}$ g$^{-1}$ at 1.3 mm, $\beta=1.0$ (cite: HILDEBRAND83; BECKWITH+90)" (3 Results) [from (cite: HILDEBRAND83; BECKWITH+90)]
- Dust temperature 20 K from Taurus average  
  > "$T_{\rm dust} = 20$ K (based on the average dust temperature inferred for Taurus; Andrews & Williams 2005" (3 Results) [from Andrews & Williams 2005]

### Not stated but needed to reproduce (our reading)

- ALMA project code and member OUS identifiers in the text
- CASA/pipeline version and imaging task parameters (cell, image size, deconvolver, masking, niter/threshold)
- Line-free channel selection used for continuum
- Primary-beam correction details and flux scale uncertainty
- How fluxes were measured (aperture or peak, fitting) at source positions
- Local noise determination procedure
- Free-free fit details (fitting method, priors) and the JVLA fluxes
- Spectral line imaging parameters and the aperture for CO upper limits
- Stellar-mass-based cluster radii calculation details

## Analysis recipe

1. **Build near-IR source list**: IDL find on GeMS Ks image, cross-matched with Hillenbrand & Carpenter 2000, visual inspection; aperture photometry calibrated to HC00  
  > "We used the IDL implementation of the *find* algorithm to identify stellar sources in the $K_{\rm s}$-band image." (2.2 GeMS Near-IR Imaging)
   - software: IDL find
   - parameter: 40 new sources  
  > "40 new detections remain after this process." (2.2 GeMS Near-IR Imaging)
   - fitting: _not stated_
   - validation: Compared color-magnitude relations with HC00 sources  
  > "Comparison of the color-magnitude relations of new detections and previously cataloged sources in (cite: HC00) suggest that they trace the same stellar population." (2.2 GeMS Near-IR Imaging)
2. **Detect 1.3 mm continuum at known source positions**: Measure flux at near-IR/proplyd positions; 4 sigma over local noise; subtract annular background  
  > "We employed a detection threshold of 4$\sigma$ above the locally-determined noise level for each optical/near-IR source." (3 Results); "We corrected the measured fluxes by subtracting the background emission measured in annuli around each target." (3 Results)
   - parameter: 4 sigma threshold  
  > "This threshold ensures that $\ll 1$ detection is expected from noise fluctuations across the entire sample of known cluster members" (3 Results)
   - fitting: _not stated_
   - validation: Compared with previous detections  
  > "Of these, 11 were detected in previous, less sensitive observations at a similar wavelength (cite: EISNER+08)." (3 Results)
3. **Remove free-free contamination**: Fit SED with turnover free-free plus optically thin dust for 14 sources with cm detections  
  > "Free parameters in the model are the turnover wavelength of free-free emission, and the free-free and dust fluxes at the observed ALMA wavelength." (3 Results)
   - assumption: dust beta=1  
  > "optically-thin dust with $\beta=1$ (cite: EISNER+08)" (3 Results)
   - fitting: _not stated_
   - validation: Non-cm detections imply free-free <~0.03 mJy  
  > "is $\ensuremath{\lesssim} 0.03$ mJy for these sources." (3 Results)
4. **Convert dust flux to disk mass**: Optically thin M_dust = S d^2/(kappa B(T)); total mass with gas-to-dust 100  
  > "The dust mass can be converted into a total circumstellar mass by assuming the canonical gas-to-dust mass ratio of 100." (3 Results)
   - assumption: d=400 pc, kappa0=2 cm2/g at 1.3 mm, beta=1, T=20 K, gas-to-dust 100  
  > "We assume $d \approx 400$ pc, $\kappa_0=2$ cm$^{2}$ g$^{-1}$ at 1.3 mm, $\beta=1.0$" (3 Results)
   - fitting: _not stated_
   - validation: _not stated_
5. **Search for CO(2-1) and C18O emission**: Line-integrated maps; 3 sigma threshold at continuum-detected positions; compare to Williams & Best 2014 models  
  > "for the sample of continuum detections, where a 3$\sigma$ threshold of 12 mJy km s$^{-1}$ can be employed with minimal risk of false positives, we still detect no line emission" (3 Results)
   - fitting: _not stated_
   - validation: _not stated_
6. **Statistical comparison of disk masses vs cluster radius**: Fisher exact test of masses within vs beyond 0.03 pc of theta1 Ori C, also combined with Mann et al. 2014  
  > "The Fisher exact test suggests that there is a 9% probability that a single disk mass distribution applies within 0.03 pc and at larger radial distances." (4.3 Disk Mass versus Cluster Radius)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **IDL find** : Identify stellar sources in GeMS Ks image  
  > "We used the IDL implementation of the *find* algorithm to identify stellar sources in the $K_{\rm s}$-band image." (2.2 GeMS Near-IR Imaging)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Continuum detections in proplyds | 21 (~20%) | not stated | sources | 2 | We detected ALMA emission towards 21 of the known proplyds, a detection rate of $\sim 20\%$. |
| Detections among near-IR sample (593 targets) | 47 (~8%) | not stated | sources | 2 | with ALMA emission seen toward 47 objects |
| Total cluster members detected above 4 sigma | 49; 38 first mm detections | not stated | sources | 2 | ALMA emission above the 4$\sigma$ level was seen towards 49 cluster members |
| Disks with total mass >10 MJ | 12 (~25% of detections, ~2% of members) | not stated | sources | 4 | we see that 12 sources have disk masses above this level, representing $\sim 25\%$ of all detections, and $\sim 2\%$ of all cluster members surveyed. |
| 4 sigma detection threshold (total mass) | ~1.5 (flux ~1.5 mJy) | not stated | M_Jup | 4 | The 4$\sigma$ detection threshold in our map corresponds to a (dust+gas) disk mass of $\sim 1.5$ M$_{\rm J}$. |
| CO(2-1) 4 sigma line-integrated noise | 17 | not stated | mJy km/s | 5 | The 4$\sigma$ noise level in the line-integrated map is 17 mJy km s$^{-1}$. |
| Fisher test probability of single mass distribution (ALMA only / with Mann+14) | 9% / 0.7% | not stated | percent | 6 | Using both datasets, the Fisher exact test gives only a 0.7% probability of a single distribution |

## Qualitative findings

- No continuum-detected disk is detected in CO(2-1) or C18O, suggesting low gas-to-dust ratios  
  > "The non-detection of any disk in the CO data suggests a relative lack of gas in these disks." (4.5 Gas-to-Dust Ratios)
- No disk mass vs stellar mass correlation seen, limited by statistics  
  > "While we see no such correlation in the ONC, at present the statistical significance of this result is limited" (4.4 Disk Mass versus Stellar Mass)

## Claim tuples

- H: Do ONC disks have gas-to-dust ratios near 100? | E: Search for CO(2-1) and C18O at continuum-detected disks, compared to Williams & Best models | R: No CO or C18O detections down to ~12 mJy km/s | F: Gas-to-dust ratio likely much lower than 100 | **supported**
- H: Does the fraction of massive disks match giant-planet occurrence around M dwarfs? | E: Count disks >10 MJ from 1.3 mm fluxes | R: ~2% of members | F: Consistent with ~2% giant planet rate around M dwarfs | **supported**
- H: Disk mass distribution differs within 0.03 pc of theta1 Ori C | E: Fisher exact test | R: 9% alone, 0.7% combined with Mann+14 | F: Supports Mann+14 but not significant with this data alone | **partially**

## Reasoning

- Why this data: ONC is the logical first choice for rich-cluster ALMA surveys  
  > "The ONC is the logical first choice for early ALMA observations" (1 Introduction)
- Why this method: _not stated_
- Alternative: Unusually compact disks as explanation for CO non-detections judged unlikely  
  > "Thus it seems unlikely that the lack of CO detections can be explained by unusually compact disks." (4.5 Gas-to-Dust Ratios)
- How they decided it was enough: _not stated_
- Limitation (authors): Background molecular cloud emission could hide gas from background disks  
  > "it is possible that some gas-rich disks in the background could be missed." (4.5 Gas-to-Dust Ratios)
- Limitation (authors): Cluster membership of new GeMS sources uncertain  
  > "Without proper motions, the cluster membership of these newly identified sources is uncertain." (2.2 GeMS Near-IR Imaging)
- Caveat (inferred, ours): Mass depends strongly on assumed opacity and fixed 20 K temperature, which is likely too low near Trapezium
- Caveat (inferred, ours): 1 arcsec beam in bright extended emission may affect flux and background subtraction
- Caveat (inferred, ours): Free-free correction only for 14 sources
- Caveat (inferred, ours): CO non-detection interpretation depends on uncertain models

## Reproducibility

- Data public (paper): Not explicitly stated; reduced archive products used  
  > "We adopted the reduced ALMA data products." (2.1 ALMA Cycle 2 Observations)
- Products in archive: _not stated_
- Missing: Project code not printed
- Missing: Flux extraction method
- Missing: Sheehan et al. 2016 cm fluxes
- Missing: Imaging parameters beyond robust=0.5
- Data volume (inferred): ~100-300 GB for the 147-pointing mosaic (12m only)
- Score (inferred): 5/5, Simple analysis and mostly tabulated results, but flux extraction, imaging details and project code not given.
- Rediscovery candidate: no, Recipe lacks flux extraction and imaging details and depends on external cm data.

## Links

- Method: (cite: EISNER+08) (Free-free plus dust model and detection methodology)
- Companion: Sheehan et al. 2016 (cite: SHEEHAN+16) (JVLA cm survey of ONC for free-free)
- Companion: (cite: MANN+14) (ALMA Cycle 0 ONC disk survey)
- Related: ALMA Cycle 0 ONC survey (Mann et al. 2014)

## Checks

```json
{
 "quotes": 62,
 "quotes_ok": 62,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 0,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2013.1.00546.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 82,
  "stated": 47,
  "rate": 0.573
 },
 "evidence_ok": true
}
```
