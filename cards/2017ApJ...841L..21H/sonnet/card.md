# Evolutionary Phases of Gas-rich Galaxies in a Galaxy Cluster at z = 1.46

`2017ApJ...841L..21H` | The Astrophysical Journal Letters 2017 | first author: Hayashi, Masao | arXiv: 1705.02567 | DOI: 10.3847/2041-8213/aa71ad

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies, galaxy_clusters_and_sz
- Question: Where do gas-rich (CO-detected) galaxies sit in the cluster and phase-space diagram, and what does this imply for environmental quenching in a z=1.46 cluster?  
  > "the cluster galaxies’ gas content allows us to better understand the quenching mechanisms of galaxies in dense environments." (Introduction)
- Target **XMMXCS J2215.9-1738 cluster**: coordinates not stated (member CO emitters near RA 22:15:58, Dec -17:38)  
  > "XMMXCS J2215.9-1738 galaxy cluster at $z=1.457$ (cite: Stanford2006) is one of the best-studied high-$z$ galaxy clusters." (Introduction); "The velocity dispersion of the cluster member galaxies is $\sigma=720$ km s$^{-1}$ and the radius of the galaxy cluster is $R_{200}=0.8$ Mpc (cite: Hilton2010)." (Introduction); z/distance z = 1.457  
  > "XMMXCS J2215.9-1738 galaxy cluster at $z=1.457$ (cite: Stanford2006) is one of the best-studied high-$z$ galaxy clusters." (Introduction); "The velocity dispersion of the cluster member galaxies is $\sigma=720$ km s$^{-1}$ and the radius of the galaxy cluster is $R_{200}=0.8$ Mpc (cite: Hilton2010)." (Introduction); distance from Stanford2006  
  > "XMMXCS J2215.9-1738 galaxy cluster at $z=1.457$ (cite: Stanford2006) is one of the best-studied high-$z$ galaxy clusters." (Introduction); "The velocity dispersion of the cluster member galaxies is $\sigma=720$ km s$^{-1}$ and the radius of the galaxy cluster is $R_{200}=0.8$ Mpc (cite: Hilton2010)." (Introduction)

## Data provenance

- ALMA projects: 2015.1.00779.S
- bands: Band 3  
  > "Our ALMA Cycle 3 program, 2015.1.00779.S, in Band 3 was conducted in 2016 May." (Data)
- frequencies and spectral setup: 93.03–94.86 GHz, 13.906 MHz resolution (~12.5 km/s)  
  > "The spectral coverage is 93.03 – 94.86 GHz with a spectral resolution of 13.906 MHz ($\sim$ 12.5 km s$^{-1}$)" (Data)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 1.79'' x 1.41'', PA -80 deg  
  > "The synthesized beam size is 1.79$''$ $\times$ 1.41$''$ with a position angle of $-80$ degrees." (Data)
- max recoverable scale: _not stated_
- sensitivity: 0.17, 0.12, 0.11, 0.12, 0.12 mJy/beam at 50, 100, 200, 400, 600 km/s (upper limits)  
  > "Typical noise levels of these cubes are 0.17, 0.12, 0.11, 0.12, and 0.12 mJy beam$^{-1}$." (Data)
- time on source: 1.04 hours per pointing, three pointings  
  > "Integration time is 1.04 hours per each pointing." (Data)
- observing dates: 2016 May  
  > "Our ALMA Cycle 3 program, 2015.1.00779.S, in Band 3 was conducted in 2016 May." (Data)
- pi or archival as stated: _not stated_
- Line: CO J=2-1 (230.538 GHz)
- Other facility **Subaru Suprime-Cam**: NB912/NB921 [O II] emitter catalogs and optical/NIR counterparts  
  > "We have created catalogs of \[O II\] emission-line galaxies selected with two narrowband filters, NB912 and NB921, (cite: Hayashi2014)." (Data)
- Other facility **HST WFC3**: archival imaging for counterparts  
  > "We also retrieve Hubble Space Telescope (HST) data taken with a Wide Field Camera 3 (WFC3) (GO-13687, PI: A. Beifiori) from the HST archive." (Data)
- External data: Spectroscopic cluster members (34 within R200)  
  > "The optical and NIR spectroscopies already confirm 34 cluster member galaxies within a radius of $R_{200}$ (cite: Hilton2010; Hayashi2011)." (Data) [from (cite: Hilton2010; Hayashi2011)]
- External data: Median SFR of star-forming members = 88 Msun/yr  
  > "(the median SFR = 88 M$_{\odot}$ yr$^{-1}$) (cite: Hayashi2010)" (Implications for the evolution of cluster galaxies) [from (cite: Hayashi2010)]

## Processing

### Calibration

- pipeline or manual: CASA standard pipeline  
  > "Calibration of the raw data was conducted using the Common Astronomy Software Applications (cite: McMullin2007) with a standard pipeline." (Data)
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
  > "The calibrated visibilities were inverted using natural weighting to produce mosaicked 3D cubes" (Data)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: CLEAN boxes of 2''x2'' at each emitter; threshold 5 sigma  
  > "image deconvolution was made with a CLEAN threshold of 5$\sigma$ of each cube, where we set CLEAN boxes of $2'' \times 2''$" (Data)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Narrowband [O II] catalogs and optical/NIR counterpart catalogs  
  > "we cross-match the coordinates of the detections in the ALMA data with those of the objects in the optical and NIR data catalogs by (cite: Hayashi2014)." (CO(2–1) emission lines from cluster galaxies) [from (cite: Hayashi2014)]
- Luminosity computation method  
  > "following (cite: Solomon1992)" (CO(2–1) emission lines from cluster galaxies) [from (cite: Solomon1992)]

### Not stated but needed to reproduce (our reading)

- CASA version
- Flux calibrator and flux scale uncertainty
- Cube channel/pixel size and image size
- Continuum subtraction and line-free channels
- Primary-beam correction details
- Clumpfind implementation details and beam handling
- Exact aperture/mask for intensity maps
- Velocity dispersion/phase-space velocity computation details

## Analysis recipe

1. **Image cubes**: Natural weighted mosaicked cubes at 50–600 km/s resolution  
  > "The calibrated visibilities were inverted using natural weighting to produce mosaicked 3D cubes with different velocity resolutions (50, 100, 200, 400, and 600 km s$^{-1}$)." (Data)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Search emission lines**: Clumpfind on cubes without PB correction in each velocity resolution  
  > "We run `Clumpfind` (cite: Williams1994) on the data cube without the primary beam correction to search for emission lines" (CO(2–1) emission lines from cluster galaxies)
   - software: Clumpfind
   - parameter: Delta T = 2 sigma, T_low = 5 sigma  
  > "we adopt the source extraction parameters of $\Delta T = 2\sigma$ and $T_{\rm low} = 5\sigma$." (CO(2–1) emission lines from cluster galaxies)
   - fitting: _not stated_
   - validation: Negative detections in inverted cubes: 0,0,0,2,3; about five false detections expected  
  > "This implies that there can be about five false detections at $>5\sigma$ in our line search." (CO(2–1) emission lines from cluster galaxies)
3. **Counterpart cross-match**: Match to optical/NIR catalogs within 1 arcsec; drop candidates without counterparts  
  > "We use a search radius of 1 arcsec for the object matching." (CO(2–1) emission lines from cluster galaxies)
   - fitting: _not stated_
   - validation: Four unmatched removed, consistent with false-detection rate  
  > "Note that this is consistent with the rate of false detection we estimate." (CO(2–1) emission lines from cluster galaxies)
4. **Fit line profiles and derive luminosities and gas masses**: Gaussian fit to spectra; L'CO from map integrated over 2xFWHM; M_H2 from L'CO  
  > "We measure the frequency at the peak of an emission line, its width and the peak line flux by fitting a Gaussian kernel to the spectrum." (CO(2–1) emission lines from cluster galaxies)
   - assumption: L'CO(2-1)/L'CO(1-0)=1; alpha_CO=4.36  
  > "under the assumptions of $L'_{\rm CO(2-1)}/L'_{\rm CO(1-0)}=1$ (cite: Dannerbauer2009), and $\alpha_{\rm CO}=$4.36 (cite: Tacconi2013)" (Implications for the evolution of cluster galaxies)
   - fitting: Single Gaussian, no sampler stated  
  > "We measure the frequency at the peak of an emission line, its width and the peak line flux by fitting a Gaussian kernel to the spectrum." (CO(2–1) emission lines from cluster galaxies)
   - validation: _not stated_
5. **Phase-space analysis**: Place CO emitters, [O II] emitters and other members on velocity vs radius diagram with Jaffe2015 virialized region and Noble2016 zones  
  > "These defined areas on the phase-space diagram are used to interpret our data." (Phase-space diagram)
   - assumption: sigma=720 km/s, R200=0.8 Mpc, H0=70, Om=0.3, OL=0.7  
  > "The cosmological parameters of $H_0=70$ km s$^{-1}$ Mpc$^{-1}$, $\Omega_m=0.3$, and $\Omega_\Lambda=0.7$ are adopted." (Introduction)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : Calibration with standard pipeline and imaging  
  > "Calibration of the raw data was conducted using the Common Astronomy Software Applications (cite: McMullin2007) with a standard pipeline." (Data)
- **Clumpfind** : Emission line search in cubes  
  > "We run `Clumpfind` (cite: Williams1994) on the data cube without the primary beam correction to search for emission lines" (CO(2–1) emission lines from cluster galaxies)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Number of CO(2-1) emitters within R200 | 17 | not stated | galaxies | 3 | We have detected emission lines from 17 galaxies within a radius of $R_{200}$ from the cluster center |
| L'CO(2-1) range | 4.5–22 x10^9 | not stated | K km/s pc^2 | 4 | ranges (4.5–22) $\times10^{9}$ K km $^{-1}$ pc$^2$ |
| M_H2 range | 2.0–9.4 x10^10 | not stated | Msun | 4 | $M_{\rm H2}$=(2.0–9.4)$\times10^{10}$M$_{\odot}$ |
| Line width range | 207–593 | not stated | km/s | 4 | The width of the lines ranges from 207 to 593 km s$^{-1}$. |
| No CO detection inside | R < 0.14 R200 (0.11 Mpc) | not stated | R200 | 3 | i.e., $R < 0.14 R_{200}$ or 0.11 Mpc |
| Fraction of CO emitters in central phase-space zone | 29% (5 galaxies) | not stated | percent | 5 | The five CO emitters (29%) are in the “central” phase-space |
| Depletion time | ~1e9 | order of magnitude | yr | 4 | a depletion time scale is estimated to be an order of $\sim10^{9}$ yr |

## Qualitative findings

- CO emitters avoid the cluster center and have redshift distribution bimodal at z~1.452 and 1.466  
  > "the redshifts of the CO emitters show a bimodal distribution with the peaks at $z\sim$ 1.452 and 1.466" (CO(2–1) emission lines from cluster galaxies)

## Claim tuples

- H: Gas-rich galaxies are distributed differently from other members | E: Cumulative radial distributions of CO emitters, [O II] emitters and other members | R: No CO within 0.14 R200; [O II] emitters more centrally concentrated | F: Gas-rich galaxies disappear from the cluster center | **supported**
- H: CO emitters are recent infallers | E: Phase-space diagram | R: CO emitters at the edge of the virialized region or recent accretion zone | F: Gas-rich galaxies entered more recently; ram-pressure stripping/strangulation then star formation depletes gas | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Noise levels are upper limits; member comparison affected by spectroscopic sampling bias  
  > "although their distribution can be affected by a sampling bias in spectroscopic confirmation" (CO(2–1) emission lines from cluster galaxies)
- Caveat (inferred, ours): Small sample and ~5 expected false detections
- Caveat (inferred, ours): Scenario inferred without HI data
- Caveat (inferred, ours): Assumed alpha_CO and r21 uncertain
- Caveat (inferred, ours): Phase-space interpretation depends on low-z calibrated zones

## Reproducibility

- Data public (paper): ALMA data cited by project code; Cycle 3 data  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2015.1.00779.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: CASA version
- Missing: Cube pixel/image parameters
- Missing: Noise and Clumpfind implementation details
- Missing: Ancillary narrowband/HST catalogs from other papers
- Data volume (inferred): ~30-100 GB raw
- Score (inferred): 3/5, Public data and standard steps with a numeric catalog, but imaging details and ancillary catalogs are missing.
- Rediscovery candidate: yes, Public data, line search recipe and a numeric line table give a checkable answer key.

## Links

- Method: (cite: Williams1994) (Clumpfind algorithm)
- Method: (cite: Solomon1992) (CO luminosity formula)
- Companion: (cite: Hayashi2014) (Narrowband [O II] and counterpart catalogs)
- Related: Suprime-Cam NB912/NB921 survey
- Related: HST GO-13687

## Checks

```json
{
 "quotes": 50,
 "quotes_ok": 50,
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
  "stated": 35,
  "rate": 0.493
 },
 "evidence_ok": true
}
```
