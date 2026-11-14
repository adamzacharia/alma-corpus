# The ALPINE-ALMA [C II] Survey: Size of Individual Star-forming Galaxies at z = 4-6 and Their Extended Halo Structure

`2020ApJ...900....1F` | The Astrophysical Journal 2020 | first author: Fujimoto, Seiji | arXiv: 2003.00013 | DOI: 10.3847/1538-4357/ab94b3

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type large_program_or_survey

## Science

- Fields: high_z_galaxies
- Question: How large is the [C II] emitting gas in individual z=4-6 star-forming galaxies compared with rest-frame UV, and do individual galaxies show extended [C II] halos?  
  > "In this paper, we study the individual size and structure of emission from star-forming galaxies at $z=4-6$, drawn from the ALPINE survey." (1 Introduction)
- Target **ALPINE sources (46 with [CII] SNR>5)**: coordinates _not stated_; z/distance z = 4.4-5.8 ([CII] redshifts in Table)  
  > "a representative sample of 118 main-sequence galaxies at $4.4<z<5.8$." (2.1 Overview); distance from [CII] line redshift; flat cosmology H0 = 70, Om = 0.3  
  > "a representative sample of 118 main-sequence galaxies at $4.4<z<5.8$." (2.1 Overview)

## Data provenance

- ALMA projects: 2017.1.00428.L
- bands: [CII] 158 um redshifted, ~330 GHz  
  > "$\nu\sim$ 330 GHz" (4.3 Spatial Offsets)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: C43-1  
  > "$B=0.2$ in the configuration of C43-1" (4.3 Spatial Offsets)
- baselines: _not stated_
- angular resolution: typical 0.9 arcsec  
  > "achieving a typical angular resolution $0.''9$ and a sensitivity of 0.35 mJy beam$^{-1}$ per spectral channel." (2.2 Data Products)
- max recoverable scale: _not stated_
- sensitivity: 0.35 mJy/beam per 25 km/s channel  
  > "a sensitivity of 0.35 mJy beam$^{-1}$ per spectral channel." (2.2 Data Products)
- time on source: _not stated_
- observing dates: May 2018 - February 2019  
  > "Observations were carried out between May 2018 and February 2019." (2.1 Overview)
- pi or archival as stated: _not stated_
- Line: [C II] 158 um (not stated)
- Other facility **HST ACS/WFC3**: F814W and F160W rest-frame UV images for size measurement  
  > "high spatial resolution images of HST ACS (F814W image in most cases;" (3.2 HST Size Measurements)
- External data: SFR and Mstar from SED fitting, ancillary data  
  > "The details of the physical properties and the ancillary data sets for our ALPINE sources are presented in (cite: faisst2020) and (cite: schaerer2020)." (2.1 Overview) [from (cite: faisst2020); (cite: schaerer2020)]
- External data: Lya EW and velocity offsets  
  > "The details of the Ly$\alpha$ EW measurements are presented in (cite: cassata2020)." (5.1.2 Lya EW) [from (cite: cassata2020)]
- External data: Photometric redshift catalogs for foreground removal  
  > "Based on available photometric redshift $z_{\rm ph}$ catalogs (cite: laigle2016; momcheva2016)" (3.2 HST Size Measurements) [from (cite: laigle2016; momcheva2016)]

## Processing

### Calibration

- pipeline or manual: Scripts provided by ALMA Observatory, plus extra flags for bad antennas  
  > "The major steps were performed with the scripts provided by the ALMA Observatory. We applied additional flags, especially for a few bad antennas" (2.2 Data Products)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA tclean; uvcontsub for continuum subtraction  
  > "With the CASA task tclean, continuum maps were produced by utilizing the line-free channels in all spectral windows" (2.2 Data Products)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "We adopted a natural weighting for imaging with a pixel scale of $0.''15$" (2.2 Data Products)
- uv taper: _not stated_
- cell size: 0.15 arcsec  
  > "We adopted a natural weighting for imaging with a pixel scale of $0.''15$" (2.2 Data Products)
- image size: _not stated_
- masking: clean to 3 sigma, max 500 iterations  
  > "The tclean routines were executed down to the 3$\sigma$ level with a maximum iteration number of 500." (2.2 Data Products)
- multiscale scales: _not stated_
- continuum subtraction: uvcontsub in visibility  
  > "[C ii] line cubes were generated after continuum subtraction from the observed visibility data with uvcontsub." (2.2 Data Products)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: ALMA and HST maps convolved with the other's PSF to match resolution  
  > "the ALMA (HST) maps are both convolved with the PSF of HST (ALMA) for matching their resolutions." (4.2 [C ii] Halo)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Calibration, reduction and [CII] line extraction  
  > "The details of data calibration, reduction, and [C ii] line extractions are described in (cite: bethermin2020)." (2.2 Data Products) [from (cite: bethermin2020)]
- Galaxy morphological classification  
  > "The details of the classification procedure are described in Le Fèvre et al. (2019)." (2.2 Data Products) [from Le Fèvre et al. (2019)]
- HST astrometry correction with GAIA DR2  
  > "We corrected the HST astrometry in advance using the GAIA DR2 catalog (cite: faisst2020)." (2.2 Data Products) [from (cite: faisst2020)]

### Not stated but needed to reproduce (our reading)

- Line-free channels and channel ranges used for continuum and moment-0 maps
- uvmultifit initial guesses, bounds and error treatment
- Number of random apertures and exact masking radius in the halo significance estimate
- FIR continuum image properties
- Moment-0 velocity ranges
- 3DBarolo parameters (inclination, PA, ring setup)
- Data volume/ALMA MOUS identifiers

## Analysis recipe

1. **measure [CII] sizes in uv plane**: Extract [CII] channels from continuum-subtracted visibilities, imfit initial values, then uvmultifit exponential (n=1) profile fit; convert FWHM to circularized r_e  
  > "Next, we measure sizes in the [C ii] line visibility using uvmultifit ((cite: marti2014)), a tool for simultaneous fitting multiple objects in the visibility plane." (3.1 ALMA Size Measurements)
   - software: CASA, uvmultifit
   - parameter: FWHM_major = 0.826 r_e,major; r_e = r_e,major sqrt(q); source center fixed from imfit  
  > "We fix the source center as estimated from imfit to improve the convergence of the free parameters." (3.1 ALMA Size Measurements)
   - assumption: Sersic index n=1  
  > "assuming a fixed S$\acute{\rm e}$rsic index n=1 (i.e., exponential-disk profile)" (3.1 ALMA Size Measurements)
   - fitting: _not stated_
   - validation: n=0.5 gives consistent r_e within ~5%; residual maps inspected and bad fits flagged  
  > "We confirm that a different model in S$\acute{\rm e}$rsic index of $n=0.5$ returns consistent $r_{\rm e}$ values within $\sim 5\%$." (3.1 ALMA Size Measurements)
2. **measure rest-frame UV sizes**: GALFIT single Sersic n=1 fit to 5x5 arcsec HST cutouts with 3D-HST PSF; foreground objects modeled and removed  
  > "We fit a single S$\acute{\rm e}$rsic profile (cite: sersic1963) to the 2D SB distribution of each galaxy. Here, we fix $n=1$" (3.2 HST Size Measurements)
   - software: GALFIT
   - fitting: _not stated_
   - validation: Monte Carlo with 1000 artificial r_e=2.1 kpc sources recovers 2.15 kpc, so PSF difference is not cause of small UV size  
  > "We obtain the median and the standard deviation of the $r_{\rm e}$ measurements of 2.15 kpc and 0.14 kpc for the 1000 artificial sources." (4.1 [CII] and rest-frame UV sizes)
3. **identify individual [CII] halos**: Extended intensity in 10 kpc aperture with beam masked, errors by random apertures; compare [CII], FIR, UV significance for 23 isolated sources  
  > "we calculate the extended [C ii] line intensity in an aperture having a radius of 10 kpc and masking the emission in a central area corresponding to the ALMA synthesized beam." (4.2 [C ii] Halo)
   - parameter: Halo: S_ext,[CII] >= 4 sigma, FIR and UV < 3 sigma  
  > "$S_{\rm ext, \, [CII]} \geq 4\sigma$" (Table 1)
   - fitting: _not stated_
   - validation: _not stated_
4. **measure spatial offsets**: Peak pixel positions in resolution-matched maps; KS test of radial offset distribution against Gaussians  
  > "we measure the emission peaks at the peak pixel positions in the smoothed HST and ALMA maps whose resolutions are matched." (4.3 Spatial Offsets)
   - fitting: _not stated_
   - validation: Same offsets recovered with 0.03 arcsec pixel scale  
  > "we obtain the consistent median and standard deviation of the spatial offsets in the smaller pixel scale" (4.3 Spatial Offsets)
5. **3D kinematic model of VC5110377875**: Tilted-ring fit with 3DBarolo, mask of signal above 2 sigma from SEARCH  
  > "we perform 3D modeling with the tilted ring fitting code $^{\rm 3D}$Barolo (cite: diteodoro2015)." (5.1.5 Kinematics of [CII] Halo)
   - software: 3DBarolo
   - assumption: single large disk  
  > "Assuming a single large disk for VC5110377875" (5.1.5 Kinematics of [CII] Halo)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : data reduction, tclean, uvcontsub, imfit  
  > "The data were reduced with the Common Astronomy Software Applications package (CASA;" (2.2 Data Products)
- **uvmultifit** : visibility-plane size fitting  
  > "using uvmultifit ((cite: marti2014))" (3.1 ALMA Size Measurements)
- **GALFIT** : UV size fits and foreground removal  
  > "based on two-dimensional (2D) surface-brightness (SB) profile fitting with galfit (cite: peng2010)" (3.2 HST Size Measurements)
- **3DBarolo** : 3D tilted-ring modeling  
  > "tilted ring fitting code $^{\rm 3D}$Barolo (cite: diteodoro2015)" (5.1.5 Kinematics of [CII] Halo)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| median r_e,[CII] (non-mergers) | 2.1 | 0.16 | kpc | 1 | $r_{\rm e, [CII]} = 2.1 \pm 0.16$ kpc |
| median r_e,F160W | 0.91 | 0.06 | kpc | 2 | $r_{\rm e, F160W} = 0.91\pm0.06$ kpc |
| median r_e,F814W | 0.66 | 0.04 | kpc | 2 | $r_{\rm e, F814W} = 0.66\pm 0.04$ kpc |
| fraction of isolated sources with [CII] halo | 7/23 (~30%) | not stated | dimensionless | 3 | at least 30% ($\sim$ 7/23) of the isolated ALPINE sources have an individual [C ii] halo |
| median offset [CII]-UV | 0.15 | std 0.09 | arcsec | 4 | $0.15\ensuremath{''}$ ($0.09\ensuremath{''}$) |
| VC5110377875 [CII] disk r_e (3DBarolo) | 4.1 | 0.5 | kpc | 5 | We obtain the best-fit effective radius for the single rotating [C ii]-gas disk of 4.1 $\pm$ 0.5 kpc. |

## Qualitative findings

- Halo objects have higher SFR and Mstar, lower Lya EW, more red-shifted Lya and blue-shifted ISM absorption  
  > "[C ii] Halo objects generally have higher SFR and $M_{\rm star}$, more blue-shifted (red-shifted) rest-frame UV metal absorption (Ly$\alpha$ line), but lower Ly$\alpha$ EW" (6 Summary)

## Claim tuples

- H: Is [CII] more extended than rest-frame UV in z=4-6 galaxies? | E: uv-plane exponential fits to [CII] vs GALFIT fits to HST | R: Median [CII] size 2.1 kpc vs 0.66-0.91 kpc UV | F: [CII] larger by factor ~2-3, ratio increasing with Mstar | **supported**
- H: Do individual galaxies host 10-kpc [CII] halos? | E: Extended-emission significance in 10 kpc apertures for 23 isolated sources | R: 12 above 4 sigma, 7 with FIR and UV below 3 sigma | F: ~30% have individual [CII] halos | **supported**
- H: Are [CII], FIR and UV peaks displaced by ~1 kpc? | E: Peak offsets and KS tests | R: Offsets 0.15-0.25 arcsec comparable to astrometric uncertainty | F: No strong evidence of systematic displacement | **partially**
- H: What drives the halo? | E: Compare halo vs non-halo properties | R: Halo objects: higher SFR, Mstar, lower Lya EW, larger velocity offsets | F: Star-formation driven outflow most likely, selection bias not excluded | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Parametric UV sizing used so UV and ALMA comparisons are not dependent on data properties  
  > "This is because the non-parametric approach largely depends on the data properties (e.g., depth and resolution)" (3.2)
- Alternative: Six halo-origin scenarios (satellites, PDR, HII region, cold streams, outflow, tidal stripping); outflow favored  
  > "We investigate these 6 ($=5+1$) scenarios based on the physical properties" (5.2)
- How they decided it was enough: _not stated_
- Limitation (authors): Selection bias toward luminous objects cannot be ruled out; deeper data needed  
  > "Although we cannot rule out the possibility that a selection bias towards luminous objects may be responsible for such trends" (abstract)
- Caveat (inferred, ours): Small samples (7 halo, 6 non-halo; 12 reliable size pairs)
- Caveat (inferred, ours): Many uvmultifit sizes flagged or with huge errors
- Caveat (inferred, ours): Halo significance depends on random-aperture noise and 4/3 sigma thresholds
- Caveat (inferred, ours): Offsets comparable to astrometric errors

## Reproducibility

- Data public (paper): ALPINE ALMA large program data; public availability not explicitly stated  
  > "This paper makes use of the ALMA data: ADS/JAO. ALMA #2017.1.00428.L." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Exact uvmultifit configuration
- Missing: Moment-map velocity windows and aperture details
- Missing: Reduced ALPINE products defined in Bethermin et al. 2020
- Data volume (inferred): Large program, hundreds of GB raw; imaged cubes for 46 sources tens of GB
- Score (inferred): 3/5, Methods outlined and data from a large program, but key parameters and calibration are deferred to companion papers.
- Rediscovery candidate: no, Recipe lacks parameters and relies on companion-paper products and HST processing.

## Links

- Method: (cite: bethermin2020) (ALPINE data reduction and line extraction)
- Method: (cite: marti2014) (uvmultifit)
- Method: (cite: faisst2020) (ancillary data and astrometry)
- Companion: (cite: ginolfi2020) (ALPINE stacking detection of [CII] halo)
- Companion: (cite: fujimoto2019) (earlier stacked [CII] halo)
- Companion: (cite: lefevre2019) (ALPINE overview and classification)
- Related: ALPINE
- Related: VUDS
- Related: COSMOS
- Related: CANDELS
- Related: 3D-HST

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
  "facts": 76,
  "stated": 43,
  "rate": 0.566
 },
 "evidence_ok": true
}
```
