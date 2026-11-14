# Unveiling Sizes of Compact AGN Hosts with ALMA

`2020ApJ...888...44C` | The Astrophysical Journal 2020 | first author: Chang, Yu-Yen | arXiv: 1911.07858 | DOI: 10.3847/1538-4357/ab595b

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, agn_and_quasars, high_z_galaxies
- Question: Are obscured AGN host galaxies more compact in rest-frame FIR (ALMA 1 mm) and optical (HST/F814W) size than non-AGN star-forming galaxies at similar redshift and stellar mass?  
  > "it is still unclear whether the existence of AGNs affects the structures of their host galaxies, and whether AGN host galaxies show different rest-frame FIR sizes compared to other star-forming galaxies." (Introduction)
- Target **27 COSMOS galaxies (IR-selected AGN, X-ray AGN, star-forming) at z<2.5**: coordinates COSMOS field; per-source ra/dec in Table 1 (e.g. 972308: 150.40459, 2.78053 deg)  
  > "We matched these sources with the COSMOS2015 catalog (cite: 2016ApJS..224...24L). The redshifts we adopted are firstly taken from the Chandra COSMOS Legacy Survey" (2.2 Complementary Sample from the Archive); z/distance z<2.5; Table gives per-source z (e.g. 0.56-2.42)  
  > "We matched these sources with the COSMOS2015 catalog (cite: 2016ApJS..224...24L). The redshifts we adopted are firstly taken from the Chandra COSMOS Legacy Survey" (2.2 Complementary Sample from the Archive); distance from Chandra COSMOS Legacy Survey spec-z, then COSMOS2015 photo-z  
  > "We matched these sources with the COSMOS2015 catalog (cite: 2016ApJS..224...24L). The redshifts we adopted are firstly taken from the Chandra COSMOS Legacy Survey" (2.2 Complementary Sample from the Archive)

## Data provenance

- ALMA projects: 2016.1.01355.S, 2013.1.00034.S, 2015.1.00026.S, 2016.1.00478.S, 2016.1.00735.S, 2016.1.00778.S, 2016.1.01426.S, 2016.1.01604.S
- bands: Band 7 for own program; Band 6/7 for archival sample  
  > "including AGNs and non-AGN galaxies in Band 6/7 with angular resolution smaller than 0$\ensuremath{''}$.4" (2.2 Complementary Sample from the Archive)
- frequencies and spectral setup: single continuum centered at 343.5 GHz of Band 7 over 7.5 GHz bandwidth (own program)  
  > "We proposed the standard set-up for single continuum centered at 343.5 GHz of Band 7 over a 7.5 GHz bandwidth." (2.1 Our ALMA Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: C40-6 with 40 antennas (own program)  
  > "The array configuration was C40-6 with 40 antennas, and the proposed rms value is 0.1 mJy/beam per 7.5 GHz." (2.1 Our ALMA Observations)
- baselines: _not stated_
- angular resolution: 0.1-0.4 arcsec; own program beam 0.12 x 0.10 arcsec  
  > "The final images are characterized by a synthesized beam size of 0$\ensuremath{''}$.12 $\times$ 0$\ensuremath{''}$.10" (2.1 Our ALMA Observations)
- max recoverable scale: _not stated_
- sensitivity: rms 0.096 mJy/beam per 8 GHz bandwidth (own detected source)  
  > "The rms value is 0.096 mJy/beam per 8 GHz bandwidth ($\sim$ 0.099 mJy/beam per 7.5 GHz)." (2.1 Our ALMA Observations)
- time on source: _not stated_
- observing dates: archival public data searched up to 2019 May  
  > "We searched all available ALMA public data by 2019 May to acquire a complementary sample." (2.2 Complementary Sample from the Archive)
- pi or archival as stated: _not stated_
- Other facility **HST/ACS F814W**: rest-frame optical/UV sizes (FWHM 0.09 arcsec)  
  > "the FWHM of the HST/$F814W$ imaging is 0$\ensuremath{''}$.09" (2.4 Size Measurements)
- Other facility **HST/WFC3 F125W/F160W (CANDELS)**: Sersic sizes for 2 sources in CANDELS  
  > "we used the single Sérsic profile measurement of available $F125W$ and $F160W$ imaging from (cite: 2012ApJS..203...24V)" (2.4 Size Measurements)
- Other facility **Herschel**: detections used for sample selection and SEDs  
  > "we restricted our sample to *Herschel*-detected sources." (2.1 Our ALMA Observations)
- External data: COSMOS2015 catalog matching and photometry  
  > "We matched these sources with the COSMOS2015 catalog (cite: 2016ApJS..224...24L)." (2.2 Complementary Sample from the Archive) [from (cite: 2016ApJS..224...24L)]
- External data: AGN classification and SED photometry/AGN templates  
  > "We included ALMA detections or upper limits in addition to the photometry in (cite: 2017ApJS..233...19C)." (2.3 SED Fitting Results) [from (cite: 2017ApJS..233...19C)]
- External data: Redshifts from Chandra COSMOS Legacy Survey  
  > "The redshifts we adopted are firstly taken from the Chandra COSMOS Legacy Survey (cite: 2011ApJ...742...61S; 2016ApJ...817...34M; 2016ApJ...819...62C)" (2.2 Complementary Sample from the Archive) [from (cite: 2011ApJ...742...61S; 2016ApJ...817...34M; 2016ApJ...819...62C)]
- External data: CANDELS F125W/F160W Sersic sizes  
  > "we used the single Sérsic profile measurement of available $F125W$ and $F160W$ imaging from (cite: 2012ApJS..203...24V)" (2.4 Size Measurements) [from (cite: 2012ApJS..203...24V)]
- External data: Main sequence relations for comparison  
  > "We also show the main sequence relations from (cite: 2014ApJS..214...15S) and (cite: 2014ApJ...795..104W)." (3 Analysis) [from (cite: 2014ApJS..214...15S; 2014ApJ...795..104W)]
- Simulation/model as data: Simulated Gaussian-source ALMA observations (SIMOBSERVE/SIMANALYZE) to test UVMODELFIT size recovery vs resolution  
  > "We simulated ALMA images by assuming Gaussian profiles, observed the images by `SIMOBSERVE`, and analyzed the observations by `SIMANALYZE`" (2.2 Complementary Sample from the Archive)

## Processing

### Calibration

- pipeline or manual: scripts provided by the ALMA observatory (own data)  
  > "the steps of data reduction and calibration were performed with the scripts provided by the ALMA observatory." (2.1 Our ALMA Observations)
- casa version: CASA 5.1.0 (size measurements)  
  > "in CASA (version 5.1.0)" (2.4 Size Measurements)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: TCLEAN  
  > "The entire map was produced by the CLEAN algorithm with the `TCLEAN` task." (2.1 Our ALMA Observations)
- deconvolver: _not stated_
- weighting robust: Briggs robust 0.5 (beam 0.12x0.10); natural weighting for stacking (beam 0.14x0.12)  
  > "corresponds to Briggs weighitng with 0.5 robustness parameter in CASA." (Footnote 1); "we used natural weighting with `TCLEAN` in CASA." (Footnote 2)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: IMSMOOTH to 0.4 arcsec for tests  
  > "We also did a simulation by `IMSMOOTH` function in CASA to create images with $0\ensuremath{''}.4$ angular resolution" (2.2 Complementary Sample from the Archive)
- final beam: 0.12 x 0.10 arcsec  
  > "The final images are characterized by a synthesized beam size of 0$\ensuremath{''}$.12 $\times$ 0$\ensuremath{''}$.10" (2.1 Our ALMA Observations)
- final rms: _not stated_

### Inherited from earlier work

- AGN classification (IR/X-ray) and MAGPHYS+AGN SED decomposition  
  > "Here we decompose the AGN and star formation components according to the SEDs by MAGPHYS+AGN as described in (cite: 2017ApJS..233...19C)." (3 Analysis) [from (cite: 2017ApJS..233...19C)]
- Compact F814W radial profile criterion for target selection  
  > "We confirmed that these objects show compact $F814W$-band radial profiles as described in (cite: 2017MNRAS.466L.103C)." (2.1 Our ALMA Observations) [from (cite: 2017MNRAS.466L.103C)]

### Not stated but needed to reproduce (our reading)

- Archival data reduction details (pipeline vs manual, CASA versions, calibrators)
- Cell size, image size, masking, cleaning threshold and deconvolver
- Per-source archival weighting/robust used for size measurement
- UVMODELFIT initial parameters and error handling beyond five iterations
- GALFIT setup (PSF, masks, stamp sizes, constraints)
- Bootstrap details
- Details of image-plane median stacking (centering, weighting)
- Exact SED-fit priors/settings for MAGPHYS+AGN
- Conversion of SFR and sizes for uncertain redshift sources

## Analysis recipe

1. **Image own ALMA data and stack non-detections**: TCLEAN imaging; median stack in image plane of nine undetected sources; check with uv-plane STACKER  
  > "we stacked their imaging and computed the median values in each pixel to create a stacked imaging" (2.1 Our ALMA Observations)
   - software: CASA, STACKER
   - parameter: Briggs robust 0.5; natural weighting for stack  
  > "we used natural weighting with `TCLEAN` in CASA." (Footnote 2)
   - fitting: _not stated_
   - validation: Image-plane and uv-plane stack peak fluxes agree (0.09 vs 0.08 mJy)  
  > "which is consistent with the stacking results from the image plane." (2.1 Our ALMA Observations)
2. **Test size-recovery vs resolution to select archival sample**: Simulate Gaussian sources with SIMOBSERVE/SIMANALYZE and fit with UVMODELFIT; smooth images with IMSMOOTH  
  > "Nevertheless, the measured size differences are within 20% of the simulated galaxies if the resolution is around $0\ensuremath{''}.1$ to $0\ensuremath{''}.4$." (2.2 Complementary Sample from the Archive)
   - software: CASA SIMOBSERVE, SIMANALYZE, UVMODELFIT, IMSMOOTH
   - parameter: sizes 0.10-0.40 arcsec, fluxes 0.25-2.00 mJy, 300 s  
  > "as well as fluxes in a range of 0.25 mJy to 2.00 mJy (signal-to-noise ratios in a range of 4 to 50 with 300 seconds total time)" (2.2 Complementary Sample from the Archive)
   - fitting: _not stated_
   - validation: resolution range 0.1-0.4 arcsec adopted  
  > "we decided to have a range of $0\ensuremath{''}.1$-$0\ensuremath{''}.4$ as our complementary sample." (Footnote 3)
3. **SED fitting for M*, SFR and AGN decomposition**: MAGPHYS with AGN templates; SFR from decomposed IR+UV luminosities  
  > "we calculated the decomposed infrared and UV luminosity from the star formation component after subtracting the AGN contribution by our SEDs." (2.3 SED Fitting Results)
   - software: MAGPHYS
   - assumption: Chabrier IMF; Kennicutt conversions  
  > "assume the stellar initial mass function of (cite: 2003PASP..115..763C)" (Introduction)
   - fitting: _not stated_
   - validation: visual inspection of fits  
  > "We also visually inspected the SED fitting results, and found that the fit quality was adequate" (2.3 SED Fitting Results)
4. **Measure FIR and optical sizes**: IMFIT image-plane Gaussians; UVMODELFIT in uv plane (adopted); GALFIT Sersic for ALMA and HST; Re = sqrt(Rmaj*Rmin)/2  
  > "The effective radius by `IMFIT` is calculated by $R_e=\sqrt{R_{Maj} \times R_{Min}}/2$" (2.4 Size Measurements)
   - software: CASA IMFIT, UVMODELFIT, GALFIT
   - parameter: UVMODELFIT starts from IMFIT values, five iterations  
  > "fitted Gaussian models with five iterations by `UVMODELFIT` task" (2.4 Size Measurements)
   - fitting: _not stated_
   - validation: UVMODELFIT ~2% lower than IMFIT; GALFIT ~10% larger; 20 matches with Fujimoto+18 differ ~0.05±0.10 kpc  
  > "The difference of the sizes are with a 2% systematic difference (`UVMODELFIT` gives lower values)." (2.4 Size Measurements)
5. **Compare sizes and SFR surface density across AGN/SFG classes**: Median/mean sizes in bins of z and mass with bootstrap errors; Sigma_SFR=SFR/(pi Re^2)  
  > "$\Sigma_{SFR}=\rm{SFR}/ (\pi R_e^{2})$, where $R_e$ is the rest-frame FIR size" (3 Analysis)
   - fitting: _not stated_
   - validation: uncertainties from bootstrapping  
  > "The uncertainties here and below are estimated from a bootstrapping analysis." (3 Analysis)

## Software

- **CASA** 5.1.0: reduction, TCLEAN, IMFIT, UVMODELFIT, simulations  
  > "in CASA (version 5.1.0)" (2.4 Size Measurements)
- **STACKER** : uv-plane stacking  
  > "We also stacked these objects by `STACKER` (cite: 2015MNRAS.446.3502L) in the uv plane." (2.1 Our ALMA Observations)
- **GALFIT** : Sersic fits to ALMA and HST images  
  > "We also measured the rest-frame FIR sizes with `GALFIT` (cite: 2010AJ....139.2097P)" (2.4 Size Measurements)
- **MAGPHYS** : SED fitting with AGN component  
  > "with an updated version of the MAGPHYS fitting technique" (2.3 SED Fitting Results)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| FIR size, detected obscured AGN host (972308) | 0.43 | 0.28 | kpc | 4 | The sizes of our detected (0.43$\pm$0.28 kpc) and stacked (0.90$\pm$0.21 kpc) obscured AGN hosts |
| FIR size, stacked obscured AGN hosts | 0.90 | 0.21 | kpc | 4 | The sizes of our detected (0.43$\pm$0.28 kpc) and stacked (0.90$\pm$0.21 kpc) obscured AGN hosts |
| Stacked peak flux (image plane) | 0.09 | 0.03 | mJy | 1 | The peak flux is 0.09 mJy$\pm$0.03 mJy (3.39 $\sigma$ |
| Archival FIR size at z~1, logM*~11 | mean 1.76, median 1.67 | 0.25 (mean), 0.30 (median) | kpc | 5 | mean=1.76$\pm$0.25 kpc and median=1.67$\pm$0.30 kpc at $z\sim$1 and $\log \rm{M}_* \sim 11$ |
| Median FIR size IRAGN at z~1 (logM*~11) | 0.77 | 0.50 | kpc | 5 | IRAGN / 0.77$\pm$0.50 (0.76$\pm$0.48) |
| Median FIR size SFG at z~1 (logM*~11) | 1.74 | 0.50 | kpc | 5 | SFG  / 1.74$\pm$0.50 (1.62$\pm$0.50) |
| SFR offset of decomposed vs original SED SFRs | 0.17 | 0.02 | dex | 3 | about 0.17$\pm$0.02 dex higher than the original SFRs estimated by SED fitting |

## Qualitative findings

- FIR sizes are similar to or more compact than optical sizes for AGN and SFGs; AGN contribution to 1 mm flux negligible (<1%).  
  > "the AGN contribution in the FIR range is negligible ($<$1% of the total flux)" (3 Analysis)

## Claim tuples

- H: Obscured AGN hosts are more compact than non-AGN SFGs at similar z and M* | E: Compare ALMA 1 mm and HST F814W sizes of IRAGN, XAGN, SFG | R: IRAGN median FIR size 0.77 kpc vs SFG 1.74 kpc at z~1 | F: Obscured AGN hosts at z~1 are more compact | **partially**
- H: FIR sizes are smaller than optical sizes in AGN hosts | E: Compare ALMA and F814W sizes | R: Mean FIR sizes smaller for SFG and XAGN; IRAGN similar | F: FIR sizes similar or more compact than optical | **supported**
- H: Obscured AGN hosts have higher SFR surface density | E: Sigma_SFR vs sSFR | R: Median Sigma_SFR more than two times higher than other ALMA sources at z~1 | F: Possible transition phase to compact quiescent galaxies | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: UVMODELFIT adopted to avoid fidelity concerns of ALMA imaging  
  > "To avoid the question about the fidelity of the ALMA imaging, we adopted the size measurements from `UVMODELFIT` for single objects in this paper." (2.4 Size Measurements)
- Alternative: uv-plane stacking not adopted since angular-to-physical conversion is not straightforward  
  > "It is not straightforward to convert stacked image in the uv plane from angular scale to physical scale, so we adopted the FIR stacked image in the image plane" (2.1 Our ALMA Observations)
- How they decided it was enough: _not stated_
- Limitation (authors): Small sample and mismatched control sample (archival sources mostly above main sequence).  
  > "Most importantly, the number of objects in each sample is limited, especially for AGN sample." (3 Analysis)
- Caveat (inferred, ours): Only one detected own-program source; the other nine are a ~3 sigma stack
- Caveat (inferred, ours): Heterogeneous archival data and mixed bands 6/7
- Caveat (inferred, ours): Optical size comparisons mix rest-frame UV and optical
- Caveat (inferred, ours): Small AGN subsamples; bootstrap errors on n=1-3 questionable

## Reproducibility

- Data public (paper): Archival ALMA public data used; project codes listed  
  > "We searched all available ALMA public data by 2019 May to acquire a complementary sample." (2.2 Complementary Sample from the Archive)
- Products in archive: _not stated_
- Missing: Archival imaging parameters
- Missing: GALFIT settings
- Missing: SED fitting configuration
- Missing: Bootstrap procedure
- Data volume (inferred): ~50-200 GB for 8 projects (calibrated MS subsets)
- Score (inferred): 5/5, Public data and named tools, but many imaging and fitting parameters unstated.
- Rediscovery candidate: no, Recipe incompletely specified for archival data and SED/GALFIT steps.

## Links

- Method: (cite: 2017ApJS..233...19C) (AGN selection and MAGPHYS+AGN SED fitting)
- Method: (cite: 2015MNRAS.446.3502L) (STACKER uv stacking)
- Companion: (cite: 2017MNRAS.466L.103C) (HST F814W compactness of IR AGN hosts)
- Related: COSMOS
- Related: COSMOS2015
- Related: Chandra COSMOS Legacy Survey
- Related: CANDELS

## Checks

```json
{
 "quotes": 70,
 "quotes_ok": 70,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 8,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 80,
  "stated": 50,
  "rate": 0.625
 },
 "evidence_ok": true
}
```
