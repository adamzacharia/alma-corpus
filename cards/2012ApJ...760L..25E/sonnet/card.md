# Giant Molecular Clouds and Star Formation in the Tidal Molecular Arm of NGC 4039

`2012ApJ...760L..25E` | The Astrophysical Journal Letters 2012 | first author: Espada, D. | arXiv: 1211.0767 | DOI: 10.1088/2041-8205/760/2/L25

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: nearby_galaxies, star_formation, milky_way_ism
- Question: What are the properties of the newly found tidal molecular arm south of NGC 4039, and how do its clumps and star formation efficiency compare with other arms and tidal features?  
  > "We report the properties of a newly discovered molecular gas arm of likely tidal origin at the south of NGC 4039 and the overlap region in the Antennae galaxies" (abstract)
- Target **Antennae galaxies (NGC 4038/9), southern mosaic**: coordinates _not stated_; z/distance 22 Mpc  
  > "it is only at 22 Mpc **distance** from us (cite: 2008AJ....136.1482S)" (Introduction); distance from Schweizer et al. 2008 (cite: 2008AJ....136.1482S)  
  > "it is only at 22 Mpc **distance** from us (cite: 2008AJ....136.1482S)" (Introduction)

## Data provenance

- ALMA projects: 2011.0.00003.SV
- bands: Band 6, CO(2-1)  
  > "Band 6 observations with 14 antennas (11 North American and 3 East Asian antennas) were carried out in 2011 May and June" (CO(2-1) ALMA Observations and data reduction)
- frequencies and spectral setup: two spectral windows of 1.875 GHz, 3840 channels of 0.488 MHz, one centered on CO(2-1)  
  > "using two spectral windows of 1.875 GHz bandwidth (or $\sim$1600 km s$^{-1}$) and 3840 0.488 MHz channels" (CO(2-1) ALMA Observations and data reduction)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: UV range 14-236 m  
  > "The observed UV range was 14 – 236 m." (CO(2-1) ALMA Observations and data reduction)
- angular resolution: 1.68'' x 0.85'', PA 78 deg  
  > "The synthesized beam is characterized by a FWHM size of 1.68$''$ $\times$ 0.85$''$ and a position angle of 78$^{\rm  o}$." (CO(2-1) ALMA Observations and data reduction)
- max recoverable scale: _not stated_
- sensitivity: 1.2 mJy/beam per 20 km/s line-free channel; ~6 mJy/beam near bright emission  
  > "The rms of a free-line 20 km s$^{-1}$ channel is 1.2 mJy beam$^{-1}$." (CO(2-1) ALMA Observations and data reduction)
- time on source: _not stated_
- observing dates: 2011 May and June  
  > "were carried out in 2011 May and June" (CO(2-1) ALMA Observations and data reduction)
- pi or archival as stated: ALMA science verification data from the ALMA science portal  
  > "science verification CO(2–1) data of the Antennae galaxies, retrieved from the ALMA science portal" (CO(2-1) ALMA Observations and data reduction)
- Line: CO J=2-1 (not stated)
- Other facility **GALEX (Nearby Galaxy Survey)**: FUV maps for SFR  
  > "We used FUV data from the Nearby Galaxy Survey (cite: 2007ApJS..173..185G)." (Star Formation Law and Stellar Clusters)
- Other facility **Spitzer MIPS**: 24 micron map for SFR  
  > "which was obtained with the MIPS (cite: 2004ApJS..154...25R) on board the Spitzer Space Telescope" (Star Formation Law and Stellar Clusters)
- Other facility **ALMA CO(3-2) science verification data**: comparison of CO(3-2) distribution with CO(2-1)  
  > "This component is also partially seen in the ALMA CO(3–2) maps, although with a considerably lower signal-to-noise ratio." (Distribution and kinematics of the molecular arm)
- External data: 24 micron Spitzer MIPS map of the Antennae  
  > "We use the 24 $\mu$m map presented in (cite: 2010MNRAS.401.1839Z)" (Star Formation Law and Stellar Clusters) [from (cite: 2010MNRAS.401.1839Z)]
- External data: HI map of the Antennae  
  > "The H I integrated density distribution (cite: 2001AJ....122.2969H) does not show any clear correlation with the molecular arm" (Discussion: Origin of the Molecular Arm) [from (cite: 2001AJ....122.2969H)]
- External data: E(B-V) = 0.046 mag foreground extinction  
  > "where $E(B--V)$ = 0.046 mag as estimated by (cite: schlegel98)" (Star Formation Law and Stellar Clusters) [from (cite: schlegel98)]

## Processing

### Calibration

- pipeline or manual: standard CASA editing, calibration, imaging, similar to CASA guide for CO(3-2) SV data  
  > "Editing, calibration, and imaging were performed in a standard manner using CASA[^2], similar to that presented in the CASA guide[^3]" (CO(2-1) ALMA Observations and data reduction)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: about 10%  
  > "The absolute flux accuracy is estimated to be about 10%." (CO(2-1) ALMA Observations and data reduction)
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: 0.2'' per pixel  
  > "a data cube that was convolved to 5 pixels (0.2$''$ pixel$^{-1}$)" (CO(2-1) ALMA Observations and data reduction)
- image size: _not stated_
- masking: cleaning restricted to manually selected boxes where emission was apparent in each channel  
  > "we restricted the cleaning to manually selected boxes where emission was apparent for each channel." (CO(2-1) ALMA Observations and data reduction)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 1.68'' x 0.85'', PA 78 deg  
  > "The synthesized beam is characterized by a FWHM size of 1.68$''$ $\times$ 0.85$''$" (CO(2-1) ALMA Observations and data reduction)
- final rms: 1.2 mJy/beam (20 km/s line-free channel)  
  > "The rms of a free-line 20 km s$^{-1}$ channel is 1.2 mJy beam$^{-1}$." (CO(2-1) ALMA Observations and data reduction)

### Inherited from earlier work

- Calibration and imaging steps similar to the CASA guide for Antennae CO(3-2) SV data  
  > "similar to that presented in the CASA guide[^3] for the CO(3–2) science verification data of Antennae galaxies" (CO(2-1) ALMA Observations and data reduction) [from CASA guide AntennaeBand7]
- SFR surface density formula from FUV and 24 micron  
  > "The $\Sigma_{\rm SFR}$ was calculated following (cite: 2008AJ....136.2782L)" (Star Formation Law and Stellar Clusters) [from (cite: 2008AJ....136.2782L)]
- I(2-1)/I(1-0)=1.0 and X=3.0e20 cm^-2 (K km/s)^-1  
  > "We adopted an intensity CO(2–1) to CO(1–0) ratio $I(2--1)/I(1--0)$ = 1.0" (Distribution and kinematics of the molecular arm) [from (cite: 2012ApJ...750..136W)]
- virial geometric factor alpha_g = 5/3  
  > "a geometric factor $\alpha_g$ for the density profile of 5/3 as in (cite: 2012ApJ...750..136W)" (Distribution and kinematics of the molecular arm) [from (cite: 2012ApJ...750..136W)]

### Not stated but needed to reproduce (our reading)

- tclean/clean parameters (weighting, robust, deconvolver, threshold, niter)
- Exact CASA version and calibration scripts used
- Mosaic imaging details and primary beam correction
- Continuum subtraction and line-free channels
- How clumps were identified and their apertures/fluxes measured
- Pixel-to-pixel SF law regridding details and region definitions
- Exact conversion of FUV/24 micron maps to MJy/sr and background level

## Analysis recipe

1. **Calibrate and image CO(2-1) cube**: Standard CASA calibration and imaging of SV data with manually boxed cleaning  
  > "Editing, calibration, and imaging were performed in a standard manner using CASA" (CO(2-1) ALMA Observations and data reduction)
   - software: CASA
   - fitting: _not stated_
   - validation: Compared total flux with Wei et al. 2012 and CO(3-2) maps  
  > "A comparison with these previous maps, as well as ALMA CO(3–2) data, showed that the brightest complexes are well collocated." (Distribution and kinematics of the molecular arm)
2. **Make moment maps**: Moments 0,1,2 using regions with emission in three consecutive 10 km/s channels in cube convolved to 5 pixels  
  > "we computed only those regions which show emission in three consecutive channels of 10 km s$^{-1}$ in a data cube that was convolved to 5 pixels" (CO(2-1) ALMA Observations and data reduction)
   - parameter: velocity range 1300-1800 km/s; clip 1.2 mJy/beam (mom0), 1.5 mJy/beam (mom1, mom2)  
  > "we used a clipping of 1.2 mJy beam$^{-1}$ per channel for the moment 0 map, and 1.5 mJy beam$^{-1}$ for the moment 1 and 2 maps." (CO(2-1) ALMA Observations and data reduction)
   - fitting: _not stated_
   - validation: _not stated_
3. **Derive gas surface densities and clump masses**: Convert CO(2-1) integrated flux to Sigma_H2 with a fixed X factor; virial mass estimate  
  > "The molecular gas surface densities were derived using $\Sigma_{\rm H2}$ ($M_\odot$ pc$^{-2}$ ) = 156 $\times$ ($X$/3.0 $\times$ 10$^{20}$)" (Distribution and kinematics of the molecular arm)
   - assumption: X = 3.0e20 cm^-2 (K km/s)^-1, I(2-1)/I(1-0)=1.0, no He correction, distance 22 Mpc  
  > "We did not correct by 1.36 to account for He." (Distribution and kinematics of the molecular arm)
   - fitting: _not stated_
   - validation: _not stated_
4. **Derive SFR surface density and SFE**: Combine FUV (extinction-corrected) and 24 micron maps at 6'' resolution, regrid to 3'' pixels, compare with gas surface density pixel by pixel  
  > "We also convolved the molecular gas surface densities to 6$''$  and converted the molecular gas and SFR surface density maps to a pixel size of 3$''$ ." (Star Formation Law and Stellar Clusters)
   - software: MOPEX
   - parameter: Sigma_SFR = 3.2e-3 I24 + 8.1e-2 IFUV; 3 sigma SFR threshold 0.018 Msun/yr; A_FUV = 8.24 E(B-V)  
  > "For the SFR map, a 3$\sigma$ threshold was used, or 0.018 $M_\odot$ yr$^{-1}$." (Star Formation Law and Stellar Clusters)
   - fitting: _not stated_
   - validation: Estimated 24 micron PSF Airy ring contamination (~0.1 dex) and excluded pixels within 11'' of bright peaks  
  > "so the PSF contamination in this case is about 25%, or about 0.1 dex on the SF law plot." (Star Formation Law and Stellar Clusters)

## Software

- **CASA** : editing, calibration, imaging of ALMA data  
  > "Editing, calibration, and imaging were performed in a standard manner using CASA" (CO(2-1) ALMA Observations and data reduction)
- **MOPEX** : processing of Spitzer 24 micron maps (as in cited work)  
  > "flat-fielding and mosaicking using MOPEX" (Star Formation Law and Stellar Clusters)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Arm length | 34'' (3.4 kpc) | not stated | arcsec / kpc | 2 | The arm extends 34$''$ end to end, or 3.4 kpc. |
| CO(2-1) flux of arm | 60 | not stated | Jy km/s | 2 | The CO(2–1) flux of this feature is 60 Jy km s$^{-1}$, a 4% of the total flux |
| Total CO(2-1) flux of southern mosaic | 1460 | not stated | Jy km/s | 2 | The total CO(2–1) flux of the entire southern mosaic map is 1460 Jy km s$^{-1}$. |
| Clump masses | (1-8)e6 | not stated | Msun | 3 | The masses of these clumps span from (1–8) $\times$ 10$^6$ $M_\odot$ |
| Clump separation | 350 | not stated | pc | 3 | almost equidistant at about 350 pc |
| Arm SFE | -8.2 | 0.3 | log(yr^-1) | 4 | log(SFE \[yr$^{-1}$\]) = –8.2 $\pm$ 0.3 |
| NGC 4039 region SFE | -8.8 | 0.3 | log(yr^-1) | 4 | log(SFE \[yr$^{-1}$\]) = –8.8 $\pm$ 0.3 |
| Virial mass for 100 pc, sigma=10 km/s | 7e6 | not stated | Msun | 3 | the virial mass is 7$\times$10$^6$ $M_\odot$ |

## Qualitative findings

- The arm is linked in distribution and kinematics to the base of NGC 4039's western spiral arm, and likely of tidal origin.  
  > "we believe that the most plausible explanation is that the molecular arm is of tidal origin" (Discussion: Origin of the Molecular Arm)

## Claim tuples

- H: Does the tidal arm host clumps with regular spacing consistent with filament fragmentation? | E: Identified clumps in CO(2-1) and measured peak-to-peak separations | R: About 10 clumps, ~350 pc spacing, lambda/D ~2 | F: Beads-on-a-string morphology consistent with Jeans-type fragmentation models | **supported**
- H: Is SF efficiency in the arm like that of disks and other tidal features? | E: Pixel-to-pixel SF law at 6'' using FUV+24um SFR and CO gas | R: log SFE = -8.2 vs -9.3 for normal galaxies | F: SFE is about a factor of 10 higher than in disk galaxies and other tidal arms | **supported**
- H: Is the arm of tidal origin and does it match simulations? | E: Kinematic continuity, HI comparison, energetics, comparison with Karl et al. 2010 | R: Continuous velocity link to NGC 4039 arm; no HI; morphology differs from simulation | F: Likely tidal, but simulated morphology does not match | **partially**

## Reasoning

- Why this data: Narrow, elongated feature not affected by projection, suited to studying GMC formation in a filament  
  > "it is a quite narrow and elongated molecular feature that allows us to study giant molecular **cloud** formation in a filamentary structure" (Introduction)
- Why this method: _not stated_
- Alternative: Bubble from massive star formation rejected: would need ~1e7 supernovae  
  > "this is unlikely due to the necessary energy output, $E$ $\sim$ 10$^{51}$ J" (Discussion: Origin of the Molecular Arm)
- How they decided it was enough: _not stated_
- Limitation (authors): Clumps mostly unresolved; higher resolution needed; short spacings needed  
  > "Higher resolution observations to resolve these complexes are necessary to set stronger constraints." (Distribution and kinematics of the molecular arm)
- Limitation (authors): Inclination of the arm is uncertain  
  > "Although the inclination of this structure is rather uncertain" (Distribution and kinematics of the molecular arm)
- Caveat (inferred, ours): Emission is dynamic range limited near bright regions; missing short spacings may bias fluxes
- Caveat (inferred, ours): Single fixed X factor and I21/I10 for a merger
- Caveat (inferred, ours): Clump identification subjective and unresolved
- Caveat (inferred, ours): Pixel SFE comparison at 6'' limited by 24 micron PSF contamination
- Caveat (inferred, ours): Tidal origin argued qualitatively

## Reproducibility

- Data public (paper): Science verification data retrieved from the ALMA science portal  
  > "retrieved from the ALMA science portal" (CO(2-1) ALMA Observations and data reduction)
- Products in archive: _not stated_
- Missing: Exact imaging parameters and clean boxes
- Missing: Clump identification procedure
- Missing: Reduced FUV and 24 micron maps and regridding details
- Data volume (inferred): ~tens of GB
- Score (inferred): 3/5, Public SV data and simple formulae, but imaging and clump finding are underspecified.
- Rediscovery candidate: no, Clump identification and imaging details are not given enough for exact redo, though the main numbers are public-data based.

## Links

- Method: (cite: 2008AJ....136.2782L) (SFR calibration from FUV and 24 micron)
- Method: (cite: 2012ApJ...750..136W) (X factor, line ratio, virial geometry)
- Companion: (cite: 2012ApJ...750..136W) (SMA CO(2-1) maps and cloud mass function of the Antennae)
- Companion: (cite: 2012ApJ...745...65U) (PdBI CO maps of the Antennae)
- Related: ALMA science verification Antennae Band 6 and Band 7
- Related: GALEX Nearby Galaxy Survey

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
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 74,
  "stated": 43,
  "rate": 0.581
 },
 "evidence_ok": true
}
```
