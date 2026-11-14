# Variable structure in the PDS 70 disc and uncertainties in radio-interferometric image restoration

`2022MNRAS.513.5790C` | Monthly Notices of the Royal Astronomical Society 2022 | first author: Casassus, Simon | arXiv: 2204.08589 | DOI: 10.1093/mnras/stac1285

Card schema 1.0 | model gemini-4-argon | depth full | type archival_reuse

## Science

- Fields: protoplanetary_disks, exoplanets, instrumentation
- Question: What is the impact of the JvM correction on restored radio-interferometric image uncertainties, and what do alternative non-parametric imaging and multi-epoch visibility alignment reveal about the circum-planetary disc PDS 70c and the inner disc of PDS 70?  
  > "We revisit the available ALMA data on PDS 70c with alternative imaging strategies, and with special attention to uncertainties and to the impact of the so-called “JvM correction”, which is thought to improve the dynamic range of restored images." (abstract); "We also propose a procedure for the alignment and joint imaging of multi-epoch visibility data." (abstract)
- Target **PDS 70**: coordinates _not stated_; z/distance 113.4 pc  
  > "For a ∼ 0.9 M_⊙ star (Keppler et al. 2019), and at a distance of 113.4 pc, material at a radius of 0''.04 (4.5 au) would rotate by 62 deg, or 95 deg at 0''.03 (3.4 au)." (3.2.3 The inner disc); distance from Keppler et al. 2019  
  > "For a ∼ 0.9 M_⊙ star (Keppler et al. 2019), and at a distance of 113.4 pc, material at a radius of 0''.04 (4.5 au) would rotate by 62 deg, or 95 deg at 0''.03 (3.4 au)." (3.2.3 The inner disc)
- Target **PDS 70c**: coordinates _not stated_; z/distance 113.4 pc  
  > "The compact mm-wavelength signal in the central cavity of the PDS 70 disc, revealed by deep ALMA observations, is aligned with unresolved Hα emission, and is thought to stem from a circum-planetary disc (CPD) around PDS 70c." (abstract); distance from Keppler et al. 2019  
  > "The compact mm-wavelength signal in the central cavity of the PDS 70 disc, revealed by deep ALMA observations, is aligned with unresolved Hα emission, and is thought to stem from a circum-planetary disc (CPD) around PDS 70c." (abstract)

## Data provenance

- ALMA projects: 2015.1.00888.S, 2017.A.00006.S, 2018.A.00030.S
- bands: Band 7 (351 GHz)  
  > "An absolute flux scale difference of ∼ 20% between SB16 and IB17 or LB19 is not surprising for ALMA Band 7 (Francis et al. 2020)." (3.1 Imaging); "Multi-configuration imaging at 351 GHz in PDS 70." (Figure 4 caption)
- frequencies and spectral setup: 351 GHz  
  > "Multi-configuration imaging at 351 GHz in PDS 70." (Figure 4 caption)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: SB16: 15 m to 1.5 km; IB17: 15 m and 6.9 km; LB19: 92 m to 8.5 km  
  > "In summary, we used the datasets corresponding to the following ALMA programmes: 2015.1.00888.S, from August 2016, with short baselines (15 m to 1.5 km) and referred to as SB16;" (3.1 Imaging); "2017.A.00006.S, from Dec. 2017, with intermediate baselines (15 m and 6.9 km) and referred to as IB17; and 2018.A.00030.S, from July 2019, with long baselines (92 m to 8.5 km) and referred to as LB19." (3.1 Imaging)
- angular resolution: LB19 (r=2.0): 0''.048 x 0''.039; LB19+SB16 (r=1): 0''.048 x 0''.039; LB19+SB16+IB17 (r=1): 0''.058 x 0''.047; IB17 (r=1): 0''.078 x 0''.064; SB16+IB17 (r=0.3): 0''.067 x 0''.049; SB16+IB17 uvmem model: ~0''.033 x 0''.029  
  > "a: Restored uvmem image for LB19, with Briggs robustness parameter r = 2.0, resulting in a clean beam of Ω_b = 0''.048 × 0''.039 / 59 deg" (Figure 4 caption); "d: Same as a) but for IB17, restored with r = 1, with Ω_b = 0''.078 × 0''.064 / 59 deg, and σ = 29.6 µJy beam^-1." (Figure 4 caption); "f: uvmem model image for SB16+IB17, with an approximate resolution of 1/3 the natural weight beam (Cárcamo et al. 2018), or Ω_b ≈ 0''.033 × 0''.029 / 88 deg." (Figure 4 caption)
- max recoverable scale: _not stated_
- sensitivity: LB19 (r=2.0): 16.4 uJy beam^-1; LB19+SB16 (r=1): 15.7 uJy beam^-1; LB19+SB16+IB17 (r=1): 15.8 uJy beam^-1; IB17 (r=1): 29.6 uJy beam^-1; SB16+IB17 (r=0.3): 31.9 uJy beam^-1  
  > "The noise in the residual image is σ = 16.4 µJy beam^-1." (Figure 4 caption); "b: same as a) but for the concatenation LB19+SB16, with Ω_b = 0''.048 × 0''.039 / 58deg, and σ = 15.7 µJy beam^-1 c: same as a) but for the concatenation LB19+SB16+IB17, with Ω_b = 0''.058 × 0''.047 / 58deg, and σ = 15.8 µJy beam^-1." (Figure 4 caption); "e: Same as c) but for SB16+IB17, restored with r = 0.3, with Ω_b = 0''.067 × 0''.049 / 60 deg, and σ = 31.9 µJy beam^-1." (Figure 4 caption)
- time on source: 3.7 h total execution time for LB19  
  > "This seems fairly consistent with the actual total execution time for the LB19 dataset, of 3.7h, considering that is was carried out under very good weather conditions (with precipitable water vapour columns ranging from 0.6 to 0.7 mm)." (3.2.1 Noise level in the LB19 image)
- observing dates: August 2016 (SB16), Dec. 2017 (IB17), July 2019 (LB19)  
  > "In summary, we used the datasets corresponding to the following ALMA programmes: 2015.1.00888.S, from August 2016, with short baselines (15 m to 1.5 km) and referred to as SB16;" (3.1 Imaging); "2017.A.00006.S, from Dec. 2017, with intermediate baselines (15 m and 6.9 km) and referred to as IB17; and 2018.A.00030.S, from July 2019, with long baselines (92 m to 8.5 km) and referred to as LB19." (3.1 Imaging)
- pi or archival as stated: archival  
  > "We revisit the available ALMA data on PDS 70c with alternative imaging strategies, and with special attention to uncertainties and to the impact of the so-called “JvM correction”, which is thought to improve the dynamic range of restored images." (abstract); "We refer to Long et al. (2018), Keppler et al. (2019), Isella et al. (2019) and Benisty et al. (2021) for a description of the observations." (3.1 Imaging)
- External data: Stellar mass of ~0.9 M_sun and distance of 113.4 pc for PDS 70  
  > "For a ∼ 0.9 M_⊙ star (Keppler et al. 2019), and at a distance of 113.4 pc, material at a radius of 0''.04 (4.5 au) would rotate by 62 deg, or 95 deg at 0''.03 (3.4 au)." (3.2.3 The inner disc) [from Keppler et al. 2019]
- External data: Dust mass estimates for the CPD  
  > "Using the dust mass estimates from Benisty et al. (2021) and Portilla-Revelo et al. (2022), the Rosseland opacities from Casassus et al. (2019b), and for a flat surface density out to 1 au in radius" (3.2.2 PDS 70c) [from Benisty et al. (2021); Portilla-Revelo et al. (2022)]
- External data: Rosseland opacities  
  > "Using the dust mass estimates from Benisty et al. (2021) and Portilla-Revelo et al. (2022), the Rosseland opacities from Casassus et al. (2019b), and for a flat surface density out to 1 au in radius" (3.2.2 PDS 70c) [from Casassus et al. (2019b)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: ~10% (general ALMA), ~20% difference observed between SB16 and IB17/LB19 in Band 7  
  > "For instance, the flux calibration accuracy for ALMA is thought to be around ∼ 10%, and the phase center accuracy (absolute positional accuracy) is, very approximately, about 1/10 the size of the clean beam major axis (see for instance Remijan et al. 2019)." (2 ALIGNMENT OF VISIBILITY DATA); "An absolute flux scale difference of ∼ 20% between SB16 and IB17 or LB19 is not surprising for ALMA Band 7 (Francis et al. 2020)." (3.1 Imaging)
- self calibration: Independent self-calibration of each dataset and joint self-calibration of concatenated datasets using OOselfcal (wrapping CASA gaincal and applycal with uvmem models); phase-only loops halving solint from ~50s scan length until PSNR decreases, followed by one amp+phase loop. Also tested standard CASA tclean self-calibration.  
  > "This framework starts with phase-calibration only, in selfcal iterations that progressively lower the solution interval by half, starting from the scan length (about 50s)." (3.1 Imaging); "This framework starts with phase-calibration only, in selfcal iterations that progressively lower the solution interval by half, starting from the scan length (about 50s)." (3.1 Imaging); "The phase-calibration stage is then followed by a single loop of amplitude and phase self-calibration, also tested for improvement using the PSNR." (3.1 Imaging)

### Imaging

- task: uvmem and CASA tclean  
  > "we first applied the standard self-calibration procedure, as implemented in casa, and composed of successive iterations of the tasks tclean, gaincal and applycal." (3.1 Imaging); "As an alternative imaging strategy, we used the uvmem package to replace the tclean model in the casa selfcal loop (see Casassus et al. 2018, 2019a, 2021b, for more details on uvmem and recent applications to ALMA data of protoplanetary discs)." (3.1 Imaging)
- deconvolver: uvmem non-parametric pure least-squares (chi^2) optimization regularized by image positivity (and entropy regularization tested)  
  > "regularized only by the requirement of image positivity (i.e. no entropy term was applied)" (3.1 Imaging); "For all datasets, we used a pure least-squared (χ^2) optimization, regularized only by the requirement of image positivity (i.e. no entropy term was applied)." (3.1 Imaging)
- weighting robust: Briggs weighting with r = 2.0, r = 1, r = 0.3; natural weights used for visibility alignment gridding  
  > "in natural weights, so according to Eqs. A3 and A5" (2 ALIGNMENT OF VISIBILITY DATA); "a: Restored uvmem image for LB19, with Briggs robustness parameter r = 2.0, resulting in a clean beam of Ω_b = 0''.048 × 0''.039 / 59 deg" (Figure 4 caption); "Restored uvmem image for LB19, with Briggs robustness parameter" (Figure 4 caption)
- uv taper: _not stated_
- cell size: 3 mas and 4 mas (for common uv-grids in alignment)  
  > "The common uv-grids correspond to 2048 × 2048 images with pixel sizes of 3 mas and 4 mas, respectively." (3.1 Imaging)
- image size: 2048 x 2048 pixels (for common uv-grids); 4 arcsec field of view for residual noise calculation  
  > "The common uv-grids correspond to 2048 × 2048 images with pixel sizes of 3 mas and 4 mas, respectively." (3.1 Imaging); "signal in the restored images to the noise in the whole residual image, with a field of view of 4 arcsec in the case of PDS 70" (3.1 Imaging, footnote 5)
- masking: elliptical mask enclosing the source  
  > "We used an elliptical mask enclosing the source that restricts the number of free parameters (as in Casassus et al. 2021b, who used Keplerian masks for line data)." (3.1 Imaging)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: Aligned in uv-plane using VisAlign, concatenated directly, visibility weights replaced via CASA statwt, followed by joint self-calibration and imaging with OOselfcal/uvmem  
  > "Having self-calibrated each dataset independently, they were concatenated for joint imaging. This required alignment to a common reference dataset, for which we chose LB19, both for position and absolute flux calibration." (3.1 Imaging); "We concatenated the visibility data directly, i.e. with the application of the statwt task in CASA to replace the visibility weights by those corresponding to the dispersion of each datum, but without additional modification." (3.1 Imaging)
- smoothing: _not stated_
- final beam: LB19 (r=2.0): 0''.048 x 0''.039 / 59 deg; LB19+SB16 (r=1): 0''.048 x 0''.039 / 58 deg; LB19+SB16+IB17 (r=1): 0''.058 x 0''.047 / 58 deg; IB17 (r=1): 0''.078 x 0''.064 / 59 deg; SB16+IB17 (r=0.3): 0''.067 x 0''.049 / 60 deg; SB16+IB17 uvmem model: ~0''.033 x 0''.029 / 88 deg  
  > "a: Restored uvmem image for LB19, with Briggs robustness parameter r = 2.0, resulting in a clean beam of Ω_b = 0''.048 × 0''.039 / 59 deg" (Figure 4 caption); "b: same as a) but for the concatenation LB19+SB16, with Ω_b = 0''.048 × 0''.039 / 58deg, and σ = 15.7 µJy beam^-1 c: same as a) but for the concatenation LB19+SB16+IB17, with Ω_b = 0''.058 × 0''.047 / 58deg, and σ = 15.8 µJy beam^-1. d: Same as a) but for IB17, restored with r = 1, with Ω_b = 0''.078 × 0''.064 / 59 deg" (Figure 4 caption); "e: Same as c) but for SB16+IB17, restored with r = 0.3, with Ω_b = 0''.067 × 0''.049 / 60 deg, and σ = 31.9 µJy beam^-1. f: uvmem model image for SB16+IB17, with an approximate resolution of 1/3 the natural weight beam (Cárcamo et al. 2018), or Ω_b ≈ 0''.033 × 0''.029 / 88 deg." (Figure 4 caption)
- final rms: LB19 (r=2.0): 16.4 uJy beam^-1; LB19+SB16 (r=1): 15.7 uJy beam^-1; LB19+SB16+IB17 (r=1): 15.8 uJy beam^-1; IB17 (r=1): 29.6 uJy beam^-1; SB16+IB17 (r=0.3): 31.9 uJy beam^-1; SB16+IB17 uvmem model: ~0.1 uJy pix^-1  
  > "The noise in the residual image is σ = 16.4 µJy beam^-1." (Figure 4 caption); "b: same as a) but for the concatenation LB19+SB16, with Ω_b = 0''.048 × 0''.039 / 58deg, and σ = 15.7 µJy beam^-1 c: same as a) but for the concatenation LB19+SB16+IB17, with Ω_b = 0''.058 × 0''.047 / 58deg, and σ = 15.8 µJy beam^-1. d: Same as a) but for IB17, restored with r = 1, with Ω_b = 0''.078 × 0''.064 / 59 deg, and σ = 29.6 µJy beam^-1." (Figure 4 caption); "The noise level in Fig. 4e being 31.9" (3.2.2 PDS 70c)

### Inherited from earlier work

- Procedures for the extraction of the continuum visibility data, spectral window combination, and dataset nomenclature  
  > "We followed the same procedures for the extraction of the continuum visibility data, and adopt the same nomenclature as in Benisty et al. (2021) to refer to the various datasets." (3.1 Imaging); "We combined all spectral windows (spws), proceeding as in Benisty et al. (2021), and reached a peak signal to noise ratio (PSNR) in the final restored images of 36.3 using Briggs weighting with r = 2." (3.1 Imaging) [from Benisty et al. (2021)]
- Elliptical mask restricting free parameters in uvmem  
  > "We used an elliptical mask enclosing the source that restricts the number of free parameters (as in Casassus et al. 2021b, who used Keplerian masks for line data)." (3.1 Imaging) [from Casassus et al. 2021b]

### Not stated but needed to reproduce (our reading)

- ExactCASA version and pipeline version used for initial calibration and continuum extraction
- Exact spectral windows, channel ranges flagged for spectral lines, and frequency averaging width used during continuum extraction (inherited from Benisty et al. 2021)
- Exact dimensions and orientation of the elliptical mask used in uvmem

## Analysis recipe

1. **Extract continuum visibility data and perform independent self-calibration and non-parametric imaging**: Extract continuum visibilities and combine all spectral windows as in Benisty et al. (2021). Perform iterative self-calibration using OOselfcal (wrapping CASA gaincal and applycal with uvmem image models), starting with phase-only loops halving the solution interval from scan length (~50s) until PSNR decreases, followed by one amplitude+phase loop.  
  > "We followed the same procedures for the extraction of the continuum visibility data, and adopt the same nomenclature as in Benisty et al. (2021) to refer to the various datasets." (3.1 Imaging); "This framework starts with phase-calibration only, in selfcal iterations that progressively lower the solution interval by half, starting from the scan length (about 50s)." (3.1 Imaging); "This framework starts with phase-calibration only, in selfcal iterations that progressively lower the solution interval by half, starting from the scan length (about 50s)." (3.1 Imaging)
   - software: CASA, gaincal, applycal, tclean, uvmem, OOselfcal
   - parameter: Initial solution interval = scan length (about 50s), halved each iteration  
  > "This framework starts with phase-calibration only, in selfcal iterations that progressively lower the solution interval by half, starting from the scan length (about 50s)." (3.1 Imaging)
   - parameter: Briggs weighting r = 2 for PSNR checks; elliptical mask enclosing the source  
  > "We used an elliptical mask enclosing the source that restricts the number of free parameters (as in Casassus et al. 2021b, who used Keplerian masks for line data)." (3.1 Imaging); "For LB19 the phase-calibration progressed until the first iteration, which was enough to reach a PSNR of 56 with r = 2." (3.1 Imaging)
   - assumption: Image positivity (no entropy term)  
  > "For all datasets, we used a pure least-squared (χ^2) optimization, regularized only by the requirement of image positivity (i.e. no entropy term was applied)." (3.1 Imaging)
   - fitting: Pure least-squares (chi^2) optimization regularized by image positivity in uvmem  
  > "For all datasets, we used a pure least-squared (χ^2) optimization, regularized only by the requirement of image positivity (i.e. no entropy term was applied)." (3.1 Imaging)
   - validation: Checked PSNR at each self-calibration loop (ratio of peak signal to noise in whole 4 arcsec residual image) and compared noise level of LB19 (16.4 uJy/beam) against ALMA Observing Tool predictions.  
  > "tables that yielded the highest PSNR. The phase-calibration stage is then followed by a single loop of amplitude and phase self-calibration, also tested for improvement using the PSNR." (3.1 Imaging); "The noise level reported in Fig. 4a, of 16.4 µJy beam^-1, appears to match the expected instrumental sensitivity." (3.2.1 Noise level in the LB19 image)
2. **Align multi-epoch visibility datasets in the uv-plane**: Extract subsets with identical spectral domains in LSRK, grid each dataset to a common uv-grid in natural weights using pyralysis, and minimize chi^2_align over overlapping uv-radii (where azimuthally averaged weights are >1/10 peak) to fit for a spatial shift (delta x) and flux scale factor (alpha_R) relative to LB19 using VisAlign.  
  > "We extract subsets of each dataset with exactly the same spectral domains in LSRK." (2 ALIGNMENT OF VISIBILITY DATA); "over which the optimisation was carried out, was determined by taking azimuthal averages in the gridded weights" (3.1 Imaging); "This required alignment to a common reference dataset, for which we chose LB19, both for position and absolute flux calibration. The alignment was achieved in the uv-plane, using VisAlign (as described in Sec. 2)." (3.1 Imaging)
   - software: pyralysis, VisAlign, MPolarMaps
   - parameter: 2048 x 2048 grid with pixel sizes of 3 mas (SB16/LB19) and 4 mas (IB17/LB19); uv-range 0.17 to 0.47 Mlambda (SB16/LB19) and 0.17 to 0.71 Mlambda (IB17/LB19)  
  > "The common uv-grids correspond to 2048 × 2048 images with pixel sizes of 3 mas and 4 mas, respectively." (3.1 Imaging); "For the SB16 and LB19 alignment, the common range in uv-radii extended from 0.17 Mλ to 0.47 Mλ." (3.1 Imaging); "For the IB17 and LB19 alignment, uv-range extended from 0.17 Mλ to 0.71 Mλ, α_R = 1.001 ± 0.002 and δ⃗x = (−0''.01401 ± 0''.0003, −0''.0203 ± 0''.0004)." (3.1 Imaging)
   - assumption: The bulk of PDS 70 is not time-variable between epochs  
  > "Here we propose to align such datasets in the uv−plane, assuming that the source is not variable in time." (2 ALIGNMENT OF VISIBILITY DATA); "We therefore assume that the bulk of PDS 70 is not variable between the two epochs" (3.1 Imaging)
   - fitting: Least-squares minimization of chi^2_align (Eq. 1) for spatial shift delta x and real flux scale factor alpha_R  
  > "it restricts the number of unknowns to only a single position shift and a flux scale factor" (2 ALIGNMENT OF VISIBILITY DATA)
   - validation: Independent check of ring centers and orientation (PA, inclination) between LB19 and IB17 using MPolarMaps, confirming ring centers coincide within ~1 mas (1.5 sigma).  
  > "As the disc of PDS 70 is essentially a ring, we can use the center of the ring to test the accuracy of our alignment procedure. The MPolarMaps package (Casassus et al. 2021b) estimates the disc orientation, under the assumption of axial symmetry, by minimizing the azimuthal dispersion of radial intensity profiles." (3.1 Imaging); "As the disc of PDS 70 is essentially a ring, we can use the center of the ring to test the accuracy of our alignment procedure." (3.1 Imaging)
3. **Perform joint multi-epoch imaging and image restoration**: Concatenate aligned visibility datasets directly, apply CASA statwt to recompute visibility weights from dispersion, run OOselfcal for joint self-calibration and uvmem modeling, and restore images with various Briggs robustness parameters without applying the JvM correction.  
  > "We concatenated the visibility data directly, i.e. with the application of the statwt task in CASA to replace the visibility weights by those corresponding to the dispersion of each datum, but without additional modification." (3.1 Imaging); "We applied the OOselfcal framework, which yielded improvements for SB16+IB17+LB19 (PSNR=95) and also for SB16+IB17 (PSNR=94), both after a single round of phase calibration." (3.1 Imaging)
   - software: CASA, statwt, OOselfcal, uvmem
   - parameter: Briggs robustness r = 2.0 (LB19), r = 1 (LB19+SB16, LB19+SB16+IB17, IB17), r = 0.3 (SB16+IB17)  
  > "a: Restored uvmem image for LB19, with Briggs robustness parameter r = 2.0" (Figure 4 caption); "b: same as a) but for the concatenation LB19+SB16, with Ω_b = 0''.048 × 0''.039 / 58deg, and σ = 15.7 µJy beam^-1 c: same as a) but for the concatenation LB19+SB16+IB17, with Ω_b = 0''.058 × 0''.047 / 58deg, and σ = 15.8 µJy beam^-1. d: Same as a) but for IB17, restored with r = 1" (Figure 4 caption); "e: Same as c) but for SB16+IB17, restored with r = 0.3, with Ω_b = 0''.067 × 0''.049 / 60 deg, and σ = 31.9 µJy beam^-1." (Figure 4 caption)
   - fitting: _not stated_
   - validation: Analytical derivation and unit-spike simulation test in CASA tclean and difmap mapplot showing standard dirty maps already have consistent Jy/clean-beam units, whereas the JvM correction artificially downscales residual noise.  
  > "We have checked that the synthesis imaging packages casa(McMullin et al. 2007) and difmap (Shepherd 1997) produce dirty maps with consistent units." (A4 Dirty map, Dirty beam); "Neither options are consistent with the requirement set by Eq. A14, since they both re-scale the units for the dirty maps. The result is an artificial increase of sensitivity by up to a factor of 1/ϵ." (A5 The JvM correction)
4. **Analyze variability and Keplerian rotation of PDS 70c and the inner disc**: Measure flux density and upper limits for PDS 70c across epochs. Test orbital smearing by de-projecting LB19+SB16, rotating by Keplerian motion over 1.75 yr, re-projecting and averaging. Test point-source sensitivity in SB16+IB17 by injecting four 126 uJy fake point sources into residual visibilities. Compare face-on deprojected views of the inner disc across epochs.  
  > "In order to test whether this is an effect of averaging different Keplerian rotation phases, we have de-projected the LB19+SB16 data, transformed the map by Keplerian rotation over a period of 1.75 yr around a 0.9 M_⊙ star, re-projected onto the sky plane and averaged the result with the initial image." (3.2.2 PDS 70c); "In order to test for synthesis imaging limitations due to the vicinity of the strong and extended emission from the cavity wall, we injected 4 point sources in the residual visibility data, at the expected location of PDS 70c, and at symmetrical positions relative to the disc axes." (3.2.2 PDS 70c); "The face-on view in Fig. 7b, obtained with the disc orientation given above, shows extended substructure in the inner disc, with a peak at 8σ (labeled ‘Clump 1’in Fig. 7)." (3.2.3 The inner disc)
   - software: uvmem
   - parameter: Time interval = 1.75 yr; fake point source flux = 126 uJy; disc inclination i = 130 deg, PA = 160.4 deg  
  > "Since the source is a fairly axially symmetric disc, albeit projected on the sky, we rotated and compressed the uv-plane to compensate for the disc orientation, with an inclination i = 130 deg and PA = 160.4 deg (see below)." (3.1 Imaging); "Since its flux in LB19 is (126 ± 16.4) µJy beam^-1, if we assign the upper limit flux density to PDS 70c in IB17, then it brightened by 42% ± 13% in the interval of ∼ 1.75 yr between IB17 and LB19." (3.2.2 PDS 70c); "b): same as a), but with the addition of fake 126 µJy point sources at all 4 locations." (Figure 6 caption)
   - assumption: Stellar mass = 0.9 M_sun, distance = 113.4 pc; flat surface density out to 1 au radius for CPD optical depth estimate  
  > "Using the dust mass estimates from Benisty et al. (2021) and Portilla-Revelo et al. (2022), the Rosseland opacities from Casassus et al. (2019b), and for a flat surface density out to 1 au in radius" (3.2.2 PDS 70c); "For a ∼ 0.9 M_⊙ star (Keppler et al. 2019), and at a distance of 113.4 pc, material at a radius of 0''.04 (4.5 au) would rotate by 62 deg, or 95 deg at 0''.03 (3.4 au)." (3.2.3 The inner disc)
   - fitting: _not stated_
   - validation: Fake 126 uJy point sources injected into SB16+IB17 residual visibilities were recovered at all 4 locations within 2 sigma, confirming non-detection of PDS 70c in IB17 is genuine.  
  > "As summarised in Fig. 6, the corresponding restored image is consistent a 126 µJy point source at all 4 locations within 2σ." (3.2.2 PDS 70c)

## Software

- **CASA** : Standard self-calibration, imaging with tclean, gaincal, applycal, and visibility weight calculation with statwt  
  > "we first applied the standard self-calibration procedure, as implemented in casa, and composed of successive iterations of the tasks tclean, gaincal and applycal." (3.1 Imaging); "We concatenated the visibility data directly, i.e. with the application of the statwt task in CASA to replace the visibility weights by those corresponding to the dispersion of each datum, but without additional modification." (3.1 Imaging)
- **tclean** : Standard CLEAN imaging in CASA for self-calibration comparison and unit spike dirty map verification  
  > "we first applied the standard self-calibration procedure, as implemented in casa, and composed of successive iterations of the tasks tclean, gaincal and applycal." (3.1 Imaging); "This can be confirmed by simulating visibility data onto a unit spike in the absence of noise, and deriving the corresponding dirty map (using task tclean in casa or mapplot in difmap), which yields peak intensities of unity." (A4 Dirty map, Dirty beam)
- **gaincal** : Antenna gain calibration in CASA self-calibration loops  
  > "which is essentially a wrapper for casa tasks `gaincal` and `applycal` and any choice of imager (in this case uvmem)." (3.1 Imaging)
- **applycal** : Applying calibration tables in CASA self-calibration loops  
  > "which is essentially a wrapper for casa tasks `gaincal` and `applycal` and any choice of imager (in this case uvmem)." (3.1 Imaging)
- **statwt** : Replacing visibility weights by those corresponding to the dispersion of each datum after concatenation  
  > "We concatenated the visibility data directly, i.e. with the application of the statwt task in CASA to replace the visibility weights by those corresponding to the dispersion of each datum, but without additional modification." (3.1 Imaging)
- **uvmem** : Non-parametric image synthesis and model generation in the self-calibration loop  
  > "Here we perform nonparametric image synthesis using the uvmem package (Casassus et al. 2006; Cárcamo et al. 2018) as an alternative to the more commonly used clean algorithm" (1 INTRODUCTION); "As an alternative imaging strategy, we used the uvmem package to replace the tclean model in the casa selfcal loop (see Casassus et al. 2018, 2019a, 2021b, for more details on uvmem and recent applications to ALMA data of protoplanetary discs)." (3.1 Imaging)
- **OOselfcal** : Automated self-calibration framework wrapping CASA gaincal and applycal with uvmem  
  > "which is essentially a wrapper for casa tasks `gaincal` and `applycal` and any choice of imager (in this case uvmem)." (3.1 Imaging)
- **pyralysis** : Gridding visibility datasets to a common uv-grid in natural weights  
  > "in natural weights, so according to Eqs. A3 and A5" (2 ALIGNMENT OF VISIBILITY DATA)
- **VisAlign** : Aligning multi-epoch visibility datasets in the uv-plane in position and flux scale  
  > "This visibility alignment procedure is implemented in the package VisAlign" (2 ALIGNMENT OF VISIBILITY DATA); "The alignment was achieved in the uv-plane, using VisAlign (as described in Sec. 2)." (3.1 Imaging)
- **MPolarMaps** : Estimating disc orientation (PA, inclination) and ring center by minimizing azimuthal dispersion of radial intensity profiles  
  > "The MPolarMaps package (Casassus et al. 2021b) estimates the disc orientation, under the assumption of axial symmetry, by minimizing the azimuthal dispersion of radial intensity profiles." (3.1 Imaging)
- **ALMA Observing Tool (OT)** : Predicting expected instrumental sensitivity and execution time  
  > "The ALMA Observing Tool (OT, provided by the Joint ALMA Observatory to prepare ALMA proposals) predicts about 6 h total execution time to reach a noise level of 17 µJy beam^-1, under default weather conditions." (3.2.1 Noise level in the LB19 image)
- **difmap** : Checking dirty map unit consistency via task mapplot  
  > "We have checked that the synthesis imaging packages casa(McMullin et al. 2007) and difmap (Shepherd 1997) produce dirty maps with consistent units." (A4 Dirty map, Dirty beam)
- **dask** : Underlying library used in the development of VisAlign and pyralysis  
  > "We acknowledge the help of the dask and astropy communities for their technical support in the development of VisAlign and pyralysis." (ACKNOWLEDGEMENTS)
- **astropy** : Underlying library used in the development of VisAlign and pyralysis  
  > "We acknowledge the help of the dask and astropy communities for their technical support in the development of VisAlign and pyralysis." (ACKNOWLEDGEMENTS)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Peak signal-to-noise ratio (PSNR) in LB19 with standard tclean self-calibration (r=2) | 36.3 | not stated | dimensionless | 1 | We combined all spectral windows (spws), proceeding as in Benisty et al. (2021), and reached a peak signal to noise ratio (PSNR) in the final restored images of 36.3 using Briggs weighting with r = 2. |
| PSNR in LB19 with OOselfcal/uvmem (r=2) | 56 | not stated | dimensionless | 1 | For LB19 the phase-calibration progressed until the first iteration, which was enough to reach a PSNR of 56 with r = 2. |
| PSNR in SB16 with OOselfcal/uvmem (r=2) | 266 | not stated | dimensionless | 1 | For SB16, a PSNR of 266 (r = 2)was reached after two phase calibration loops. |
| PSNR in IB17 with OOselfcal/uvmem (r=2) | 75 | not stated | dimensionless | 1 | For IB17, a single iteration in phase yielded a PSNR of 75 (r = 2). |
| Spatial shift delta x for SB16 relative to LB19 | (-0.012, -0.019) | (+-0.001, +-0.001) | arcsec | 2 | The fit yielded δ⃗x = (−0''.012 ± 0''.001, −0''.019 ± 0''.001). |
| Flux scale factor alpha_R for SB16 relative to LB19 | 0.788 | +-0.004 | dimensionless | 2 | The flux scale factor was α_R = 0.788 ± 0.004, which is somewhat smaller than the ratio of flux densities extracted within the mask, of 0.861 ± 0.004. |
| Spatial shift delta x for IB17 relative to LB19 | (-0.01401, -0.0203) | (+-0.0003, +-0.0004) | arcsec | 2 | For the IB17 and LB19 alignment, uv-range extended from 0.17 Mλ to 0.71 Mλ, α_R = 1.001 ± 0.002 and δ⃗x = (−0''.01401 ± 0''.0003, −0''.0203 ± 0''.0004). |
| Flux scale factor alpha_R for IB17 relative to LB19 | 1.001 | +-0.002 | dimensionless | 2 | For the IB17 and LB19 alignment, uv-range extended from 0.17 Mλ to 0.71 Mλ, α_R = 1.001 ± 0.002 and δ⃗x = (−0''.01401 ± 0''.0003, −0''.0203 ± 0''.0004). |
| PDS 70 disc Position Angle (PA) in LB19 | 160.4 | +-0.08 | deg | 2 | For LB19, the best fit orientation corresponds to PA= 160 _._ 4 _±_ 0 _._ 08 deg, _i_ = 130 _._ 0 _±_ 0 _._ 06 deg, and a ring center |
| PDS 70 disc inclination (i) in LB19 | 130.0 | +-0.06 | deg | 2 | For LB19, the best fit orientation corresponds to PA= 160 _._ 4 _±_ 0 _._ 08 deg, _i_ = 130 _._ 0 _±_ 0 _._ 06 deg, and a ring center |
| PDS 70 disc Position Angle (PA) in IB17 | 160.5 | +-0.18 | deg | 2 | For IB17, we obtained PA= 160 _._ 5 _±_ 0 _._ 18 deg, _i_ = 129 _._ 9 |
| PDS 70 disc inclination (i) in IB17 | 129.9 | +0.16/-0.14 | deg | 2 | For IB17, we obtained PA= 160 _._ 5 _±_ 0 _._ 18 deg, _i_ = 129 _._ 9 |
| PSNR in concatenated SB16+IB17+LB19 | 95 | not stated | dimensionless | 3 | We applied the OOselfcal framework, which yielded improvements for SB16+IB17+LB19 (PSNR=95) and also for SB16+IB17 (PSNR=94), both after a single round of phase calibration. |
| PSNR in concatenated SB16+IB17 | 94 | not stated | dimensionless | 3 | We applied the OOselfcal framework, which yielded improvements for SB16+IB17+LB19 (PSNR=95) and also for SB16+IB17 (PSNR=94), both after a single round of phase calibration. |
| PSNR in concatenated SB16+LB19 | 84 | not stated | dimensionless | 3 | The amplitude and phase self-calibration resulted in an improvement only for SB16+LB19 (PSNR=84). |
| Noise level in LB19 restored image (r=2.0) | 16.4 | not stated | uJy beam^-1 | 3 | The noise level reported in Fig. 4a, of 16.4 µJy beam^-1, appears to match the expected instrumental sensitivity. |
| Peak intensity of PDS 70c in LB19 (r=2.0) | 126 | +-16.4 | uJy beam^-1 | 4 | This is best seen in Fig. 4a, with point-like signal reaching 126 µJy beam^-1, or 8σ.; Since its flux in LB19 is (126 ± 16.4) µJy beam^-1, if we assign the upper limit flux density to PDS 70c in IB17, then it brightened by 42% ± 13% in the interval of ∼ 1.75 yr between IB17 and LB19. |
| Detection significance of PDS 70c in LB19 | 8 | not stated | sigma | 4 | In the case of PDS 70, we recover the detection of PDS 70c from the July 2019 data, but only at 8σ.; This is best seen in Fig. 4a, with point-like signal reaching 126 µJy beam^-1, or 8σ. |
| Specific intensity at PDS 70c position in SB16+IB17 (r=0.3) | -51 | +-31.9 | uJy beam^-1 | 4 | The noise level in Fig. 4e being 31.9 µJy beam^-1, and since the data are aligned in position and flux, a 126 µJy point source should have been picked up at 4σ. Instead, the intensity at the location of PDS 70c is −51 µJy beam^-1. |
| 3-sigma upper limit on PDS 70c flux density in IB17 | 89 | not stated | uJy | 4 | The non-detection of PDS 70c in IB17 (Fig. 4d) places a 3σ upper limit on its flux density of 89 µJy. |
| Variability (brightening) of PDS 70c between IB17 and LB19 (1.75 yr) | 42 | +-13 | % | 4 | However, its non-detection in Dec. 2017 suggests that PDS 70c is variable by at least 42% ± 13% over a 1.75 yr time-span, so similar to models of the Hα variability.; Since its flux in LB19 is (126 ± 16.4) µJy beam^-1, if we assign the upper limit flux density to PDS 70c in IB17, then it brightened by 42% ± 13% in the interval of ∼ 1.75 yr between IB17 and LB19. |
| Inner disc peak (Clump 1) offset from ring center | 0.04 | not stated | arcsec | 4 | We also pick up fine structure in the inner disc, such that its peak is offset by ∼ 0''.04 from the disc centre.; Intriguingly, Clump 1 is offset from the ring center by ∼ 0''.03 to 0''.04, which is comparable to the natural-weights beam. |
| Azimuthal rotation of Clump 1 between SB16+IB17 and SB16+LB19 | 70 | not stated | deg | 4 | We find Clump 1 offset by ∼ 70 deg in azimuth relative to SB16+LB19, as expected for Keplerian rotation if the centre of mass coincides with the ring center. |
| Clump 2 offset from ring center in IB17 | 0.08 | not stated | arcsec | 4 | labeled Clump 2 in Fig. 7, more compact and that reaches the same peak intensity as Clump 1, is found offset by _∼_ 0 _[′′]_ _._ 08. |

## Qualitative findings

- The JvM correction artificially down-scales the residual dirty map and exaggerates the peak signal-to-noise ratio of restored images by up to a factor of 10.  
  > "We find that the JvM correction exaggerates the peak signal-to-noise of the data, by up to a factor of 10." (abstract); "The dirty map of the residuals is then scaled by the ratio of the dirty and clean beams, thereby artificially down-scaling the noise level by up to one order of magnitude." (A1 Motivation for image restoration, and for a reconsideration of the JvM correction)
- PDS 70c is surrounded by a faint (3-sigma) extended filament or spur connecting it to the cavity wall in the LB19+SB16 image.  
  > "We note that this point source is surrounded by extended emission, in the form of a filament or spur, that connects with the cavity wall. This spur is best seen in Fig. 4b, where it is detected at 3σ." (3.2.2 PDS 70c)
- The inner disc of PDS 70 is structured (with a V-shaped feature and peaks Clump 1 and Clump 2) and time-variable, showing evidence of both Keplerian rotation and intrinsic morphological changes.  
  > "The inner disc is variable too, which we tentatively ascribe to Keplerian rotation as well as intrinsic morphological changes." (abstract); "The V-shaped structure with Clump 1 at its vertex appears to rotate as a rigid body, which might reflect a wave launched by Clump 1." (3.2.3 The inner disc)

## Claim tuples

- H: The JvM correction accurately represents the noise and dynamic range in restored radio-interferometric images. | E: Analytical derivation of dirty map and point-source flux uncertainty units, unit-spike simulation tests in CASA and difmap, and comparison of LB19 noise level with ALMA Observing Tool predictions. | R: Standard dirty maps already carry consistent units of Jy per clean beam (sigma = 16.4 uJy/beam in LB19, matching OT predictions), whereas the JvM correction scales residuals by epsilon (down to 1/10), artificially lowering LB19 noise to 6.2 uJy/beam. | F: The JvM correction is inconsistent with visibility flux scale uncertainties and exaggerates the peak signal-to-noise ratio of restored images by up to a factor of 10. | **refuted**
- H: A compact mm-wavelength continuum source is present at the location of PDS 70c in the July 2019 (LB19) ALMA observations. | E: Non-parametric image synthesis and self-calibration of LB19 and LB19+SB16 datasets using uvmem and OOselfcal, followed by standard image restoration without the JvM correction. | R: Point-like signal coincident with PDS 70c is recovered at 126 +- 16.4 uJy/beam, corresponding to an 8-sigma detection. | F: The detection of the compact source at PDS 70c in July 2019 is confirmed, though at 8-sigma rather than the higher significance implied by JvM-corrected images. | **supported**
- H: The mm continuum emission from PDS 70c is constant between Dec. 2017 (IB17) and July 2019 (LB19), and its absence in the concatenated LB19+IB17+SB16 image is merely due to Keplerian orbital smearing. | E: Simulated Keplerian rotation averaging over 1.75 yr on the LB19+SB16 image, imaged IB17 and SB16+IB17 directly, and injected four 126 uJy fake point sources into the SB16+IB17 residual visibilities. | R: Keplerian smearing leaves PDS 70c conspicuous; fake 126 uJy sources are recovered within 2-sigma in SB16+IB17, whereas the actual intensity at PDS 70c is -51 uJy/beam in SB16+IB17 and <89 uJy (3-sigma) in IB17. | F: PDS 70c was absent in Dec. 2017 and brightened by at least 42% +- 13% over the 1.75 yr timespan between IB17 and LB19. | **refuted**
- H: The inner disc of PDS 70 contains fine, time-variable substructure that rotates and evolves between epochs. | E: Deprojected face-on comparison of the restored LB19+SB16 image and the super-resolved SB16+IB17 uvmem model image. | R: An 8-sigma peak (Clump 1) offset by ~0''.03-0''.04 from the ring center rotates by ~70 deg in azimuth between IB17 and LB19 (consistent with Keplerian rotation at 3.4-4.5 au), while a second peak (Clump 2 at ~0''.08 in IB17) cannot be explained by circular Keplerian rotation alone. | F: The inner disc of PDS 70 is structured and variable, exhibiting both Keplerian rotation of Clump 1 and intrinsic morphological changes. | **partially**

## Reasoning

- Why this data: The direct detection of a CPD around PDS 70c in deep long-baseline ALMA observations is a momentous achievement in planetary sciences, motivating a reanalysis of the available multi-epoch ALMA datasets with careful attention to uncertainties.  
  > "The direct detection of a CPD, thanks to deep ALMA observations, is a momentous achievement in planetary sciences, whose relevance motivates us to revisit these data with alternative synthesis imaging tools." (1 INTRODUCTION)
- Why this method: Non-parametric image synthesis with uvmem provides an alternative to CLEAN, and uv-plane alignment via VisAlign restricts free parameters to a single position shift and flux scale factor without requiring a bright source model like joint self-calibration.  
  > "Here we perform nonparametric image synthesis using the uvmem package (Casassus et al. 2006; Cárcamo et al. 2018) as an alternative to the more commonly used clean algorithm" (1 INTRODUCTION); "The result of our procedure is similar to that of joint self-calibration (described in Sec. 3.1), but it restricts the number of unknowns to only a single position shift and a flux scale factor, while self-calibration adjusts time-series for the antenna gains." (2 ALIGNMENT OF VISIBILITY DATA)
- Alternative: Entropy regularization in uvmem was tested, yielding a lower flux density ratio of 0.77 +- 0.004, but was rejected in favor of pure chi^2 optimization with image positivity because entropy regularization produced stronger synthesis imaging artifacts.  
  > "Using entropy regularization resulted in a lower flux density ratio of 0.77 ± 0.004 (but with stronger synthesis imaging artifacts, which is why we use the pure χ^2 versions)." (3.1 Imaging)
- Alternative: Time-variability of the bulk outer disc flux density as the cause of the ~20% flux scale difference between SB16 and IB17/LB19 was rejected as unlikely because IB17 and LB19 have consistent flux scales over a similar time interval.  
  > "The alternative, that the flux of the disc itself is time-variable, is unlikely since the flux scales between IB17 and LB19 are consistent, while the time separations between IB17 and SB16, and between LB19 and IB17, are similar." (3.1 Imaging)
- How they decided it was enough: Self-calibration iterations were stopped when the peak signal-to-noise ratio (PSNR) decreased, reverting to the calibration tables that yielded the highest PSNR.  
  > "These iterations are interrupted when the PSNR" (3.1 Imaging)
- Limitation (authors): The LB19 flux density is biased upwards in the pure chi^2 uvmem reconstructions due to positive-definite noise in the model images.  
  > "The LB19 flux density is biased upwards in our pure χ^2 reconstructions, because of the positive-definite noise in the model images." (3.1 Imaging)
- Limitation (authors): The statistical properties and uncertainties of the unconvolved uvmem model image are not well constrained, making the comparison of the SB16+IB17 model image with the restored SB16+LB19 image for the inner disc tentative.  
  > "Since the statistical properties of the model image are not well constrained, the comparison is tentative." (3.2.3 The inner disc); "However, the model images by themselves usually lack noise estimates. This is because the inverse problem in image synthesis, i.e. the production of a model image from sparse Fourier data, is intrinsically ill-posed." (A1 Motivation for image restoration, and for a reconsideration of the JvM correction)
- Caveat (inferred, ours): The comparison of inner disc substructure across epochs relies on comparing an unconvolved super-resolved uvmem model image (SB16+IB17) against a convolved restored image (SB16+LB19), which have different effective PSF responses and noise statistics.
- Caveat (inferred, ours): The initial continuum visibility extraction and spectral window flagging are not explicitly detailed and rely entirely on the procedures of Benisty et al. (2021).

## Reproducibility

- Data public (paper): Raw data are in the ALMA archive under project codes 2015.1.00888.S, 2017.A.00006.S, and 2018.A.00030.S; reduced ALMA data are available upon reasonable request to the corresponding author.  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2015.1.00888.S, 2017.A.00006.S, 2018.A.00030.S." (ACKNOWLEDGEMENTS); "The reduced ALMA data presented in this article are available upon reasonable request to the corresponding author." (DATA AVAILABILITY)
- Products in archive: _not stated_
- Code: All five custom software packages underlying the analysis are publicly released on GitHub/GitLab: MPolarMaps (https://github.com/simoncasassus/MPolarMaps), uvmem (https://github.com/miguelcarcamov/gpuvmem), pyralysis (https://gitlab.com/miguelcarcamov/pyralysis), VisAlign (https://github.com/simoncasassus/VisAlign), and OOselfcal (https://github.com/miguelcarcamov/objectoriented_selfcal).  
  > "The original or else non-standard software packages underlying the analysis are available at the following URLs:" (DATA AVAILABILITY)
- Missing: Exact channel flagging and spectral averaging parameters used to extract the continuum visibilities (deferred to Benisty et al. 2021)
- Missing: Exact CASA version used
- Missing: Exact parameters (semi-major axis, semi-minor axis, position angle) of the elliptical mask applied in uvmem
- Data volume (inferred): ~50-200 GB (three Band 7 ALMA projects including long-baseline execution blocks, reduced to continuum visibility measurement sets)
- Score (inferred): 88/5, All three ALMA project codes are stated and public, all five custom analysis/imaging codes (uvmem, OOselfcal, VisAlign, pyralysis, MPolarMaps) are open-source with URLs provided, and key quantitative parameters (grid sizes, uv-ranges, Briggs robust values, alignment shifts, scale factors, and noise levels) are thoroughly documented. Minor deductions for deferring initial continuum extraction details to Benisty et al. (2021) and not stating the CASA version.
- Rediscovery candidate: yes, Public archival ALMA data, complete open-source software stack provided via GitHub/GitLab links, well-specified algorithmic steps, and clear numeric answer keys (alignment shifts, scale factors, PSNR values, and PDS 70c flux density and SNR).

## Links

- Method: Casassus et al. 2006; Cárcamo et al. 2018 (Introduces and describes the GPU-accelerated uvmem non-parametric image synthesis package)
- Method: Casassus et al. 2021b (Describes the MPolarMaps package for disc orientation fitting and masking strategies in uvmem)
- Method: Jorsater & van Moorsel 1995; Czekala et al. 2021 (Formulates the JvM correction for residual scaling in interferometric image restoration that this paper critiques)
- Companion: Benisty et al. 2021 (Original publication of the July 2019 long-baseline ALMA observations of PDS 70c and source of the continuum extraction procedure and nomenclature)
- Companion: Long et al. 2018; Keppler et al. 2019; Isella et al. 2019 (Original publications describing the earlier ALMA observations (SB16, IB17) of PDS 70)

## Checks

```json
{
 "quotes": 169,
 "quotes_ok": 169,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 19,
 "unsupported_facts": 0,
 "project_codes": 3,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 24,
 "numeric_problems": 0,
 "fill": {
  "facts": 93,
  "stated": 73,
  "rate": 0.785
 },
 "evidence_ok": true
}
```
