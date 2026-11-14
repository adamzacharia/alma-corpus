# Bulge-forming Galaxies with an Extended Rotating Disk at z ~ 2

`2017ApJ...834..135T` | The Astrophysical Journal 2017 | first author: Tadaki, Ken-ichi | arXiv: 1608.05412 | DOI: 10.3847/1538-4357/834/2/135

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies
- Question: Do massive main-sequence star-forming galaxies at z~2 host compact central dust-obscured starbursts that build bulges within extended rotating disks, rather than via major mergers?  
  > "the key goal is to address the issue of morphological transformation from extended exponential disks to quiescent spheroids using the high-resolution ALMA/870 $\mu$m maps." (Introduction)
- Target **25 Halpha-selected star-forming galaxies in SXDF-UDS-CANDELS (z=2.19 and 2.53)**: coordinates _not stated_; z/distance z = 2.19 or 2.53  
  > "tracing H$\alpha$ emission at $z=2.19\pm0.02$ or $2.53\pm0.02$" (2.1 Sample selection); distance from narrow-band imaging survey (Tadaki+13), confirmed with KMOS spectroscopy  
  > "tracing H$\alpha$ emission at $z=2.19\pm0.02$ or $2.53\pm0.02$" (2.1 Sample selection)

## Data provenance

- ALMA projects: 2012.1.00245.S, 2013.1.00566.S
- bands: Band 7 (~870 um), central frequency 345 or 350 GHz  
  > "We use the band 7 receivers with the 64-input correlator in Time Division Mode in a central frequency of 345 or 350 GHz ($\sim$870 $\mu$m)." (2.2 ALMA observations)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 20-1600 m, 32-49 antennas  
  > "with 32–49 antennas and baseline lengths of 20–1600 m" (2.2 ALMA observations)
- angular resolution: 0.47-0.54" (tapered) and 0.15-0.21" (natural)  
  > "The synthesized beamsizes are 0$''$.47-0$''$.54 and 0$''$.15-0$''$.21, respectively." (2.2 ALMA observations)
- max recoverable scale: _not stated_
- sensitivity: rms 98-142 uJy/beam (low-res), 56-74 uJy/beam (high-res)  
  > "The rms levels are 98-142 $\mu$Jy beam$^{-1}$ for the low-resolution maps and 56-74 $\mu$Jy beam$^{-1}$ for the high-resolution maps" (2.2 ALMA observations)
- time on source: 6-8 minutes per object  
  > "On-source time is 6–8 minutes per object." (2.2 ALMA observations)
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Other facility **VLT/KMOS (KMOS3D)**: Halpha IFU kinematics for 12 of 25 galaxies  
  > "We have observed 12 of 25 galaxies with the near-infrared integral-field spectrometer KMOS on the Very Large Telescope (VLT)" (2.3 KMOS observations)
- Other facility **HST (CANDELS)**: H160 rest-optical sizes and Sersic indices, ACS I814 images  
  > "where 0$''$.18-resolution HST images at four passbands ($V_{606}$, $I_{814}$, $J_{125}$, and $H_{160}$) are publicly available" (2.1 Sample selection)
- Other facility **Subaru/MOIRCS**: narrow-band Halpha sample selection  
  > "Our sample is selected from a narrow-band imaging survey with the MOIRCS on the Subaru Telescope" (2.1 Sample selection)
- Other facility **Spitzer MIPS 24um / Herschel PACS 160um**: infrared luminosities for total SFRs; 24um priority for target selection  
  > "we compute total SFRs from a combination of the rest-frame 2800 Å and infrared luminosities with PACS 160 $\mu$m or MIPS 24 $\mu$m fluxes" (2.2 Galaxy properties)
- External data: 3D-HST photometric catalog (18 bands) used for SED fitting  
  > "we use the 3D-HST catalog, including photometric data at 18 bands from $U-$band to 8.0 $\mu$m" (2.2 Galaxy properties) [from (cite: 2014ApJS..214...24S; 2016ApJS..225...27M)]
- External data: KMOS3D kinematic parameters and specific angular momentum comparison sample at z=0.8-2.6  
  > "Figure [6](#fig;AM) shows specific angular momenta as a function of stellar mass for galaxies at $z=0.8-2.6$ from the KMOS$^\mathrm{3D}$ survey" (4 Bulge formation) [from (cite: 2016ApJ...826..214B)]
- External data: Gas depletion scaling relation (updated version)  
  > "We use the updated version of this scaling relation (Tacconi et al. in prep)" (4 Bulge formation) [from (cite: 2015ApJ...800...20G)]

## Processing

### Calibration

- pipeline or manual: calibration with CASA; details not given  
  > "We utilize the Common Astronomy Software Application package (`CASA`; (cite: 2007ASPC..376..127M)) for the data calibration." (2.2 ALMA observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: natural weighting for high-resolution maps  
  > "high-resolution ones with natural weighting" (2.2 ALMA observations)
- uv taper: on-sky FWHM = 0.5" for low-resolution maps  
  > "We reconstruct two kinds of clean maps: low-resolution maps with $uv$-taper of the on-sky FWHM=0$''$.5 and high-resolution ones with natural weighting." (2.2 ALMA observations)
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

- Kinematic parameter derivation (vrot, sigma0, jdisk) follows Burkert et al.  
  > "Our method to derive kinematic parameters is described in detail by (cite: 2016ApJ...826..214B)" (2.3 KMOS observations) [from (cite: 2016ApJ...826..214B)]
- Total SFR recipe from UV+IR luminosities  
  > "Following the recipes of (cite: 2011ApJ...738..106W), we compute total SFRs" (2.2 Galaxy properties) [from (cite: 2011ApJ...738..106W)]
- Spatially resolved stellar mass maps via multi-band HST SED modeling  
  > "we create stellar mass maps by spatially resolved SED modeling with multi-band HST data (cite: 2012ApJ...753..114W; 2014ApJ...788...11L)" (4 Bulge formation) [from (cite: 2012ApJ...753..114W; 2014ApJ...788...11L)]

### Not stated but needed to reproduce (our reading)

- CASA version and calibrator details
- Cleaning parameters (threshold, masks, iterations, cell and image size)
- uv range binning used for visibility plots
- Model of serendipitous interloper sources subtracted from visibilities
- Tacconi et al. in prep scaling relation not published
- Which galaxies' visibilities were stacked, stacking weights

## Analysis recipe

1. **Calibrate and image ALMA data**: CASA calibration; tapered (0.5") and natural-weighted clean maps; aperture photometry with uncertainties from 50 random apertures  
  > "Uncertainties of total fluxes are derived by computing standard deviations of 50 random apertures in each of the maps." (2.2 ALMA observations)
   - software: CASA
   - parameter: detection threshold 4 sigma (low-res) or 5 sigma (high-res); aperture 1.5" or 1.0"  
  > "we adopt a 4$\sigma$ threshold in a peak flux density on the low-resolution maps or 5$\sigma$ on the high-resolution maps" (2.2 ALMA observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **Derive stellar masses, SFRs and rest-optical structure**: FAST SED fitting, IR+UV SFRs, GALFIT H160 profiles  
  > "The structural parameters such as circularized half-light radius and S$\acute{\mathrm{e}}$rsic index are derived with `GALFIT`" (2.2 Galaxy properties)
   - software: FAST, UNIMAP, GALFIT
   - assumption: Chabrier IMF, BC03 models, solar metallicity, exponentially declining SFH, Calzetti attenuation  
  > "under a solar metallicity, exponentially declining star formation histories (SFHs), and dust attenuation law of (cite: 2000ApJ...533..682C) to estimate stellar masses" (2.2 Galaxy properties)
   - fitting: _not stated_
   - validation: _not stated_
3. **Measure 870um half-light radii**: Visibility fitting with circular exponential profile using UVMULTIFIT after subtracting interloper models  
  > "we perform visibility fitting with a circular exponential profile as seen in the rest-optical light." (3.2 Size measurements)
   - software: UVMULTIFIT
   - parameter: FWHM = 0.826 R1/2  
  > "which outputs full width at half maximum (FWHM) of a two-dimensional flux distribution (FWHM=0.826 $R_{1/2}$)" (3.2 Size measurements)
   - assumption: dust emission traces star formation if dust temperature is constant  
  > "to approximately provide the spatial distribution of star formation within galaxies if the dust temperature is constant across galaxies" (3 Spatial extent)
   - fitting: uncertainties from fitting errors  
  > "We obtain uncertainties in the sizes from fitting errors." (3.2 Size measurements)
   - validation: Gaussian model gives sizes smaller by 7±6%; no >3 sigma residuals in model-subtracted clean maps  
  > "If adopting a circular Gaussian model, the estimated 870 $\mu$m sizes would become smaller by 7$\pm$6%." (3.2 Size measurements)
4. **Correct for extended residual emission**: Stack model-subtracted visibilities of nine compact sources, image with 1" taper, measure S_extra, recompute R1/2,cor  
  > "we perform a stacking analysis of the model-subtracted visibilities for nine compact sources, using the `STACKER` tool" (3.2 Size measurements)
   - software: STACKER, CASA
   - parameter: S_extra = 0.42 mJy within 2.0" aperture, 4.3 sigma  
  > "The residual emission is detected at 4.3$\sigma$ and its flux density within 2$''$.0 aperture is $S_\mathrm{extra}$=0.42 mJy" (3.2 Size measurements)
   - assumption: residual flux originates outside the half-light radius  
  > "Conservatively assuming that this residual flux originates outside the half-light radius" (3.2 Size measurements)
   - fitting: _not stated_
   - validation: _not stated_
5. **Estimate bulge formation and gas depletion timescales**: tau_bulge=(1e10-Sigma M*1kpc)/(w*Sigma SFR1kpc); tau_depl=Mgas/(SFR(1+eta)) with scaling-relation Mgas  
  > "taking into account mass loss due to stellar winds ($w=0.6$ in Chabrier initial mass function" (4 Bulge formation)
   - parameter: w=0.6, eta~1, Mgas/SFR uncertainty ±0.24 dex  
  > "We adopt uncertainties of $\pm$0.24 dex for the $\log(M_\mathrm{gas}/\mathrm{SFR})$" (4 Bulge formation)
   - assumption: current SFR maintained; outflow rate comparable to SFR (eta~1)  
  > "with comparable rates to SFR, $\eta\times$SFR ($\eta\sim1$)" (4 Bulge formation)
   - fitting: _not stated_
   - validation: _not stated_
6. **Measure ionized gas kinematics and angular momentum**: Gaussian fits per pixel for velocity and dispersion maps, corrected for inclination, beam smearing, pressure support; j_disk=k_disk*v_circ*R1/2  
  > "First, we create velocity field and velocity dispersion maps by fitting Gaussian profiles to the data in each spatial pixel." (2.3 KMOS observations)
   - software: SPARK
   - parameter: q_int=0.15-0.25  
  > "with an intrinsic finite thickness of $q_\mathrm{int}=0.15-0.25$" (2.3 KMOS observations)
   - assumption: symmetric oblate thick exponential disks  
  > "A fundamental assumption is that high-redshift star-forming galaxies are symmetric oblate, thick disks with an exponential profile" (2.3 KMOS observations)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : data calibration and imaging  
  > "We utilize the Common Astronomy Software Application package (`CASA`; (cite: 2007ASPC..376..127M)) for the data calibration." (2.2 ALMA observations)
- **UVMULTIFIT** : visibility fitting of exponential models  
  > "For the visibility fitting, we use the `UVMULTIFIT` tool (cite: 2014A&A...563A.136M)" (3.2 Size measurements)
- **STACKER** : stacking model-subtracted visibilities  
  > "using the `STACKER` tool (cite: 2015MNRAS.446.3502L)" (3.2 Size measurements)
- **FAST** : SED fitting for stellar masses  
  > "Using the `FAST` code (cite: 2009ApJ...700..221K), we perform spectral energy distribution (SED) fitting" (2.2 Galaxy properties)
- **GALFIT** : Sersic fits to H160 maps  
  > "are derived with `GALFIT` (cite: 2010AJ....139.2097P) in the $H_{160}$-band maps" (2.2 Galaxy properties)
- **UNIMAP** : PACS 160um map making  
  > "We also create a deep PACS 160 $\mu$m map from archival data with `UNIMAP`" (2.2 Galaxy properties)
- **SPARK** : KMOS data reduction  
  > "We reduced the data with the Software Package for Astronomical Reduction (`SPARK`; (cite: 2013A&A...558A..56D))." (2.3 KMOS observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Number of detected galaxies | 16 of 25 (64%) | not stated | galaxies | 1 | We have detected 16 out of the 25 galaxies either in the low-resolution or the high-resolution maps. |
| Mean total 870um flux of detections | 2.0 (0.6-4.9) | not stated | mJy | 1 | The total average flux is $\langle S_\mathrm{aper}\rangle$=2.0 mJy (0.6-4.9) in all detected objects |
| Residual extended flux S_extra from stacking | 0.42 | not stated | mJy | 4 | $S_\mathrm{extra}$=0.42 mJy, corresponding to 21% of the total average flux |
| Mean 1.6um half-light radius of nine compact galaxies | 3.2 (1.5-5.8) | not stated | kpc | 2 | $R_{1/2,1.6\mu\mathrm{m}}$=3.2 (1.5–5.8) kpc |
| Mean Sersic index at 1.6um | 1.2 (0.5-1.9) | not stated | dimensionless | 2 | S$\acute{\mathrm{e}}$rsic index $n$=1.2 (0.5–1.9) in the rest-optical maps |
| Sigma SFR within central 1 kpc (nine compact galaxies) | 40 (19-65) | not stated | Msun/yr/kpc^2 | 5 | $\Sigma$SFR$_\mathrm{1kpc}$=40 (19–65) $M_\odot$yr$^{-1}$kpc$^{-2}$ |
| Mean log bulge formation timescale | 8.47 (8.16-8.79) | not stated | log yr | 5 | $\langle\log \tau_\mathrm{bulge}\rangle= 8.47$ (8.16–8.79) |
| Mean tau_bulge/tau_depl | ~1.2 | not stated | dimensionless | 5 | $\langle\tau_\mathrm{bulge}/\tau_\mathrm{depl}\rangle\sim1.2$ |
| Mean vrot/sigma0 (nine galaxies) | 5.1 (3.5-7.1) | not stated | dimensionless | 6 | $\langle v_\mathrm{rot}/\sigma_0\rangle=5.1~(3.5-7.1)$ |
| Galaxies with compact 870um R1/2 < 1.5 kpc | 9 of 12 massive galaxies | not stated | galaxies | 4 | For nine out of the 12 star-forming galaxies, the corrected 870 $\mu$m sizes are less than 1.5 kpc |

## Qualitative findings

- 870um emission arises from a single region near the rest-optical center rather than multiple clumps.  
  > "A common remarkable feature is that 870 $\mu$m emission is radiated from a single region close to the rest-optical center" (3.1 High-resolution maps)

## Claim tuples

- H: Massive main-sequence galaxies at z~2 have dust emission more compact than their stellar disks | E: uv visibility fitting of exponential models to 12 massive galaxies, compared with HST H160 sizes | R: nine of 12 have R1/2,870um < 1.5 kpc versus mean optical 3.2 kpc | F: Compact circumnuclear starbursts are common in extended exponential disks | **supported**
- H: Central starbursts can build a dense bulge quickly | E: compute tau_bulge from Sigma SFR 1kpc and Sigma M* 1kpc, compare with tau_depl | R: log tau_bulge ~8.47, comparable to depletion times | F: Bulge formation within several hundred Myr, with natural quenching | **supported**
- H: Bulge formation occurs in rotating disks by internal processes, not mergers | E: KMOS Halpha kinematics and specific angular momentum compared with KMOS3D | R: all rotation-supported, angular momenta consistent with mass-selected sample | F: Internal angular momentum redistribution is favored over major mergers | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Visibility fitting avoids dependence on clean parameters; exponential model chosen for consistency with rest-optical profiles  
  > "To avoid these uncertainties, we perform visibility fitting with a circular exponential profile as seen in the rest-optical light." (3.2 Size measurements)
- Alternative: Gaussian visibility model (commonly used) rejected in favor of exponential; gives 7% smaller sizes  
  > "In previous studies, a Gaussian model is commonly used for size measurements in $u-v$ plane" (3.2 Size measurements)
- How they decided it was enough: _not stated_
- Limitation (authors): High-resolution maps might miss extended, diffuse components  
  > "Also note that these high-resolution maps are sensitive to compact components with a spatial scale of $\sim$0$''$.2 and we might miss extended, diffuse components." (3.1 High-resolution maps)
- Caveat (inferred, ours): Dust temperature assumed constant across galaxies to equate dust size to SFR distribution
- Caveat (inferred, ours): Sample of 12 small and prioritized by 24um brightness
- Caveat (inferred, ours): Only six galaxies have both ALMA size and kinematics
- Caveat (inferred, ours): Gas masses come from a scaling relation, not measured

## Reproducibility

- Data public (paper): ALMA project codes given; KMOS3D and HST CANDELS data cited as public  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2012.1.00245.S and 2013.1.00566.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: CASA version and calibration scripts
- Missing: Clean parameters
- Missing: Interloper models
- Missing: Unpublished Tacconi et al. scaling relation
- Missing: Stellar mass maps and KMOS reductions are not provided
- Data volume (inferred): ~50-150 GB for two ALMA Band 7 projects (25 short snapshots)
- Score (inferred): 3/5, Public ALMA data and clear fitting recipe, but imaging parameters, versions and external kinematic and mass-map inputs are missing.
- Rediscovery candidate: no, Key results also rely on KMOS, HST mass maps and 3D-HST catalogs and unpublished scaling relations, and imaging details are missing.

## Links

- Method: (cite: 2014A&A...563A.136M) (UVMULTIFIT visibility fitting)
- Method: (cite: 2015MNRAS.446.3502L) (STACKER visibility stacking)
- Method: (cite: 2016ApJ...826..214B) (kinematic parameter derivation)
- Companion: (cite: 2015ApJ...811L...3T) (earlier ALMA study of Halpha-selected galaxies)
- Companion: (cite: 2016ApJ...827L..32B) (independent ALMA study of compact star-forming galaxies)
- Related: KMOS3D
- Related: 3D-HST
- Related: CANDELS
- Related: SpUDS

## Checks

```json
{
 "quotes": 67,
 "quotes_ok": 67,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 10,
 "numeric_problems": 0,
 "fill": {
  "facts": 91,
  "stated": 51,
  "rate": 0.56
 },
 "evidence_ok": true
}
```
