# The JWST UNCOVER Treasury Survey: Ultradeep NIRSpec and NIRCam Observations before the Epoch of Reionization

`2024ApJ...974...92B` | The Astrophysical Journal 2024 | first author: Bezanson, Rachel | arXiv: 2212.04026 | DOI: 10.3847/1538-4357/ad66cf

Card schema 1.0 | model gpt-6.1-sol | depth light | type multi_facility_alma_minor

## Science

- Fields: high_z_galaxies
- Question: Detecting and spectroscopically characterizing the properties of the first galaxies.  
  > "The *JWST* UNCOVER survey is designed to address a primary objective of the observatory: detecting and spectroscopically characterizing the properties of the first galaxies, while enabling a broad range of scientific explorations." (Discussion and Scientific Objectives of the UNCOVER survey)
- Target **Abell 2744**: coordinates _not stated_; z/distance z=0.308  
  > "Abell 2744 galaxy cluster at $z=0.308$" (abstract); distance from _not stated_

## Data provenance

- ALMA projects: 2013.1.00999.S, 2018.1.00035.L, 2022.1.00073.S
- bands: DUALZ: ALMA band 6.  
  > "the Deep UNCOVER-ALMA Legacy High-z (DUALZ) Survey ALMA band 6 spectral scans (cite: fujimoto:23dualz)." (Ancillary Datasets in Abell 2744)
- frequencies and spectral setup: HFF-ALMA: 1.1mm imaging; ALCS: 15GHz-wide spectral scan at 1.2mm; 2022.1.00073.S: 30GHz spectral scan.  
  > "1.1mm imaging of the cluster through the HFF-ALMA program (cite: gonzalez-lopez:17) and a 15GHz-wide spectral scan at 1.2mm through the ALMA lensing cluster survey (ALCS) (cite: kohno:19)." (Ancillary Datasets in Abell 2744); "| Cluster (4’x6’)    | 30GHz spectral scan        | ALMA#2022.1.00073.S, PI: Fujimoto                  | 37.2h         |" (Table 2)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: 2013.1.00999.S: PI Bauer; 2018.1.00035.L: PI Kohno; 2022.1.00073.S: PI Fujimoto.  
  > "ALMA#2013.1.00999.S, PI: Bauer" (Table 2); "ALMA#2018.1.00035.L, PI: Kohno" (Table 2); "ALMA#2022.1.00073.S, PI: Fujimoto" (Table 2)
- Other facility **JWST: NIRCam, NIRSpec, NIRISS**: NIRCam pre-imaging, NIRSpec/PRISM spectroscopy and parallel imaging.  
  > "The first UNCOVER data consist of deep (4-6 hour per filter) NIRCam pre-imaging on the A2744 cluster" (Observational Strategy); "Nine months later July/August 2023 we targeted sources detected in NIRCam with ultra-deep 19 hour NIRSpec/PRISM low-resolution spectroscopy." (Observational Strategy); "Both sets of observations include deep parallel imaging (in NIRISS and NIRCam, respectively)" (Observational Strategy)
- Other facility **HST: ACS and WFC3**: Historical imaging, reprocessed onto the JWST mosaic grids.  
  > "*HST*(ACS and WFC3)" (Facilities); "We also compute mosaics of all of the historical *Hubble* imaging of the Abell 2744 field, drizzled to the same pixel grid and with datasets described by (cite: kokorev:22) and references therein." (Image Reduction)
- Other facility **VLT/MUSE**: Ancillary spectroscopy and redshifts for 514 galaxies.  
  > "One such rich dataset is provided by deep *VLT*/Multi Unit Spectroscopic Explorer (MUSE) observations." (Ancillary Datasets in Abell 2744); "This mosaic of MUSE pointings covers 2’ x 2’ and yields untargeted spectroscopic redshifts for 514 galaxies (cite: mahler:18)." (Ancillary Datasets in Abell 2744)
- Other facility **Subaru/Suprime-Cam**: Ancillary deep optical imaging.  
  > "Deep ground-based optical imaging exist from *Subaru/Suprime-Cam* in *B, R$_C$, i’*, and *z’* (cite: medezinski:16)." (Ancillary Datasets in Abell 2744)
- Other facility **XMM-Newton, Suzaku and Chandra**: Ancillary X-ray observations.  
  > "the field has also been observed in the X-ray for 110 ks by *XMM-Newton* (#074385010, PI: Kneib), 75 ks with *Suzaku* (cite: eckert:16), and *Chandra* (#23700107, PI Bogdan)." (Ancillary Datasets in Abell 2744)
- External data: HFF-ALMA 1.1mm imaging of Abell 2744.  
  > "1.1mm imaging of the cluster through the HFF-ALMA program (cite: gonzalez-lopez:17)" (Ancillary Datasets in Abell 2744) [from (cite: gonzalez-lopez:17)]
- External data: ALCS 15GHz-wide spectral scan at 1.2mm.  
  > "a 15GHz-wide spectral scan at 1.2mm through the ALMA lensing cluster survey (ALCS) (cite: kohno:19)." (Ancillary Datasets in Abell 2744) [from (cite: kohno:19)]
- External data: DUALZ ALMA band 6 spectral scans.  
  > "the Deep UNCOVER-ALMA Legacy High-z (DUALZ) Survey ALMA band 6 spectral scans (cite: fujimoto:23dualz)." (Ancillary Datasets in Abell 2744) [from (cite: fujimoto:23dualz)]
- External data: Theoretical luminosity functions for survey design.  
  > "forward-modeling the theoretical luminosity functions of (cite: mason:15)" (Deep NIRCam and NIRISS imaging) [from (cite: mason:15)]
- External data: DELPHI model for predicted galaxy counts.  
  > "from the `DELPHI` model (cite: dayal:14; dayal:22)" (Deep NIRCam and NIRISS imaging) [from (cite: dayal:14; dayal:22)]
- External data: CATS v4.1 lens model of A2744.  
  > "using the CATS v4.1 lens model of A2744 (cite: jauzac:15)" (Deep NIRCam and NIRISS imaging) [from (cite: jauzac:15)]
- External data: JAGUAR Mock Catalog below z<6 for predicted target counts.  
  > "All numbers are rough estimates derived from the JAdes extraGalactic Ultradeep Artificial Realizations (JAGUAR) Mock Catalog (cite: williams:18) below $z<6$" (Scheduled NIRSpec/PRISM spectroscopic followup) [from (cite: williams:18)]
- External data: NOAO LegacySurvey DR9 catalog for absolute image alignment.  
  > "The absolute alignment is performed by aligning (shift and rotation) the UNCOVER F444W exposures to sources in the ground-based NOAO LegacySurvey DR9 catalog (cite: dey:19)." (Image Reduction) [from (cite: dey:19)]
- External data: Gaia DR3 absolute reference frame for alignment verification.  
  > "We have verified that with this procedure the UNCOVER mosaic is aligned to the absolute frame defined by Gaia DR3 (cite: gaia:22) at a level of 12 mas (cite: Weaver:23)." (Image Reduction) [from (cite: gaia:22)]
- External data: Historical Hubble imaging datasets.  
  > "We also compute mosaics of all of the historical *Hubble* imaging of the Abell 2744 field, drizzled to the same pixel grid and with datasets described by (cite: kokorev:22) and references therein." (Image Reduction) [from (cite: kokorev:22) and references therein]
- External data: Ancillary MUSE spectroscopic redshifts for 514 galaxies.  
  > "This mosaic of MUSE pointings covers 2’ x 2’ and yields untargeted spectroscopic redshifts for 514 galaxies (cite: mahler:18)." (Ancillary Datasets in Abell 2744) [from (cite: mahler:18)]
- External data: Ancillary Subaru/Suprime-Cam optical imaging.  
  > "Deep ground-based optical imaging exist from *Subaru/Suprime-Cam* in *B, R$_C$, i’*, and *z’* (cite: medezinski:16)." (Ancillary Datasets in Abell 2744) [from (cite: medezinski:16)]
- External data: Ancillary Suzaku X-ray observations.  
  > "75 ks with *Suzaku* (cite: eckert:16)" (Ancillary Datasets in Abell 2744) [from (cite: eckert:16)]
- External data: Updated lensing maps and catalog magnification estimates.  
  > "our team has published lensing maps that have been updated with new JWST sources (cite: furtak:23lensing), magnification estimates and uncertainties from this model are included in photometric catalogs." (Planned Data Release Schedule) [from (cite: furtak:23lensing)]
- External data: Dust-rich and dust-poor star formation rate density evolution models.  
  > "Individual objects are plotted against the backdrop of dust-rich and dust-poor models for the evolution of the star formation rate density from (cite: casey:18)." (Discussion and Scientific Objectives of the UNCOVER survey) [from (cite: casey:18)]
- Simulation/model as data: Mason luminosity functions and DELPHI models, forward-modeled with the CATS v4.1 lens model to predict galaxy counts.  
  > "forward-modeling the theoretical luminosity functions of (cite: mason:15) and from the `DELPHI` model (cite: dayal:14; dayal:22)" (Deep NIRCam and NIRISS imaging); "using the CATS v4.1 lens model of A2744 (cite: jauzac:15) to predict the number of $6{<}z{<}16$ galaxies to our detection limit." (Deep NIRCam and NIRISS imaging)
- Simulation/model as data: JAGUAR Mock Catalog below z<6 and Mason model at higher redshifts for predicted galaxy counts.  
  > "All numbers are rough estimates derived from the JAdes extraGalactic Ultradeep Artificial Realizations (JAGUAR) Mock Catalog (cite: williams:18) below $z<6$ and at higher redshifts from the (cite: mason:15) model." (Scheduled NIRSpec/PRISM spectroscopic followup)
- Simulation/model as data: Representative Bagpipes SEDs using delayed tau models.  
  > "In that Figure, we show representative SEDs generated using `Bagpipes` (cite: carnall:18) with the NIRCam primary filters." (Deep NIRCam and NIRISS imaging); "We show delayed tau models" (Deep NIRCam and NIRISS imaging)
- Simulation/model as data: Casey dust-rich and dust-poor star formation rate density evolution models for the science-target comparison.  
  > "Individual objects are plotted against the backdrop of dust-rich and dust-poor models for the evolution of the star formation rate density from (cite: casey:18)." (Discussion and Scientific Objectives of the UNCOVER survey)

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
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Post-correction Grizli processing follows the earlier HST procedure.  
  > "After the JWST-specific corrections to the exposures described above, the `grizli` pipeline processing is essentially identical to the procedure adopted earlier for data from the *Hubble Space Telescope* (cite: kokorev:22)." (Image Reduction) [from (cite: kokorev:22)]
- Historical Hubble dataset selection follows Kokorev and references therein.  
  > "We also compute mosaics of all of the historical *Hubble* imaging of the Abell 2744 field, drizzled to the same pixel grid and with datasets described by (cite: kokorev:22) and references therein." (Image Reduction) [from (cite: kokorev:22) and references therein]
- Detailed pipeline description deferred to G. Brammer et al.  
  > "A detailed description of the pipeline is provided in G. Brammer et al. in preparation." (Image Reduction) [from G. Brammer et al. in preparation]
- Detailed effective photometric-catalog depths deferred to Weaver.  
  > "We refer the reader to (cite: Weaver:23) for a more detailed discussion of effective depths of our photometric catalogs" (Table 1) [from (cite: Weaver:23)]
- Final spectroscopic program design, observational strategy and MSA implementation deferred to Price.  
  > "We describe the final spectroscopic program design and observational strategy in (cite: price:24)." (Scheduled NIRSpec/PRISM spectroscopic followup); "The full implementation of this MSA design will be presented in (cite: price:24)." (Scheduled NIRSpec/PRISM spectroscopic followup) [from (cite: price:24)]
- GLASS program details deferred to its survey design paper.  
  > "For details about that program, the reader is referred to the survey design paper (cite: treu:22)." (Ancillary Datasets in Abell 2744) [from (cite: treu:22)]
- Updated accounting of subsequent JWST programs and footprints deferred to Suess.  
  > "A number of subsequent JWST programs have been completed in Abell 2744; we refer the reader to (cite: suess:24) for an updated accounting and similar figures." (Ancillary Datasets in Abell 2744) [from (cite: suess:24)]
- Planned wavelength-dependent slit-loss corrections use flexible, spatially-resolved galaxy models.  
  > "perform corrections for these wavelength-dependent aperture effects, leveraging flexible, spatially-resolved galaxy models (cite: leja:21)." (Scheduled NIRSpec/PRISM spectroscopic followup) [from (cite: leja:21)]

### Not stated but needed to reproduce (our reading)

- ALMA execution identifiers, observing dates, array configurations and baseline ranges.
- ALMA spectral-window centers, channel widths and scan tuning boundaries.
- ALMA calibration software versions, calibrators and flux-scale uncertainties.
- ALMA imaging weighting, robust values, cell sizes, masks, cleaning thresholds, beams and noise.
- ALMA continuum-channel selection, continuum subtraction and spectral-cube construction.
- Whether the listed ALMA data or products are public; no ALMA reduction or measurement recipe is provided.

## Analysis recipe

1. **Correct the calibrated JWST exposures**: Start from MAST rate.fits; correct 1/f noise, mask snowballs, apply custom sky flats, subtract wisps and apply photometric corrections.  
  > "We start with the MAST `rate.fits` products produced by Stage 1 of the *JWST* calibration pipeline (v1.8.4) using calibration set `jwst_0995.pmap`." (Image Reduction); "We derive a correction for the “$1/f$ noise” (cite: rauscher:15) by subtracting the source-masked median image values computed along detector rows and columns." (Image Reduction); "After applying the flat-field calibration, we fit and subtract the additive “wisp” structure in some of the short-wavelength filter/detector combinations (cite: Rigby:22) using wisp templates" (Image Reduction)
   - software: Grizli, JWST calibration pipeline
   - parameter: JWST calibration pipeline v1.8.4; jwst_0995.pmap.  
  > "We start with the MAST `rate.fits` products produced by Stage 1 of the *JWST* calibration pipeline (v1.8.4) using calibration set `jwst_0995.pmap`." (Image Reduction)
   - parameter: Snowballs: large groups of DQ=4 pixels, with a conservatively grown mask.  
  > "we identify likely snowballs as large groups of pixels with the $\mathrm{DQ}=4$ bit set in the exposure data quality array and grow a conservative mask around them." (Image Reduction)
   - parameter: Mask sky-flat values outside [0.7, 1.4].  
  > "We apply an additional mask to the exposure data quality arrays to ignore any pixels where the sky flat is outside of the range \[0.7, 1.4\]" (Image Reduction)
   - parameter: Custom sky flats from COM-1063 commissioning exposures.  
  > "from on-sky commissioning data from program COM-1063 (PI: Sunnquist) from normalized, source-masked exposures in each of the filter/detector combinations used in the UNCOVER field." (Image Reduction)
   - parameter: Residual relative correction: 0.94 for F277W in NIRCam module A.  
  > "we adopt a residual relative correction of 0.94 for the F277W filter in the NIRCam A module based on observations from the PRIMER program" (Image Reduction)
   - fitting: Fit and subtract additive wisp structure using templates derived from GO-2561 UNCOVER data.  
  > "we fit and subtract the additive “wisp” structure in some of the short-wavelength filter/detector combinations (cite: Rigby:22) using wisp templates" (Image Reduction); "derived from the GO-2561 UNCOVER data themselves." (Image Reduction)
   - validation: F277W relative correction based on PRIMER observations of the same sources on both detectors.  
  > "based on observations from the PRIMER program (GO-1837, PI: Dunlop) where the same sources were observed in the same filter on both detectors" (Image Reduction)
2. **Align the JWST exposures**: Compute exposure shifts from sources; align F444W to LegacySurvey DR9 with shifts and rotation; align other filters to the F444W source list.  
  > "The first computes shift translations based on the positions of sources identified in each individual exposure" (Image Reduction); "The absolute alignment is performed by aligning (shift and rotation) the UNCOVER F444W exposures to sources in the ground-based NOAO LegacySurvey DR9 catalog (cite: dey:19)." (Image Reduction); "We then create a source list from the aligned F444W mosaic to which the exposures in all of the other filters are aligned." (Image Reduction)
   - software: Grizli
   - fitting: Shift translations; absolute shift and rotation.  
  > "The first computes shift translations based on the positions of sources identified in each individual exposure" (Image Reduction); "The absolute alignment is performed by aligning (shift and rotation) the UNCOVER F444W exposures to sources in the ground-based NOAO LegacySurvey DR9 catalog (cite: dey:19)." (Image Reduction)
   - validation: Alignment to Gaia DR3 absolute frame at 12 mas.  
  > "We have verified that with this procedure the UNCOVER mosaic is aligned to the absolute frame defined by Gaia DR3 (cite: gaia:22) at a level of 12 mas (cite: Weaver:23)." (Image Reduction)
3. **Construct the JWST mosaics**: Compute exposure background pedestals and drizzle each filter onto a common grid; propagate ERR models into inverse-variance weight maps.  
  > "The background pedestal level of each exposure are computed with the AstroDrizzle software (cite: Gonzaga:12)" (Image Reduction); "which is then also used to create the final mosaics of each filter drizzled to a common pixel grid" (Image Reduction); "AstroDrizzle produces a “weight” image that has units of inverse variance of the “science” images and is made by propagating the total ERR noise model of each input exposure through the drizzle resampling." (Image Reduction)
   - software: AstroDrizzle, Grizli
   - parameter: pixfrac=0.75; kernel=square.  
  > "drizzle parameters $\mathtt{pixfrac}=0.75$, $\mathtt{kernel}=\mathtt{square}$." (Image Reduction)
   - parameter: 20 mas pixels: NIRCam short wavelengths; 40 mas pixels: NIRCam long wavelengths and NIRISS.  
  > "with 20 mas pixels in NIRCam short-wavelengths and 40 mas pixels in the NIRCam long-wavelength filters and NIRISS imaging." (DR1: Initial Release of NIRCam/NIRISS Mosaics)
   - fitting: _not stated_
   - validation: _not stated_
4. **Measure JWST imaging depths**: Infer aperture noise from weight maps and correct to total for point sources; report two-visit-region 5σ depths.  
  > "based on the noise properties inferred from the weight maps and corrected to total assuming point sources." (Table 1); "The depths correspond the two-visit depth regions of the mosaic." (Table 1)
   - parameter: 0.08" radius apertures at short wavelengths; 0.16" radius apertures at long wavelengths.  
  > "Imaging depths in the NIRISS/NIRCam mosaics are calculated using 0.08" radius apertures in the short wavelength bands, 0.16" radius apertures in the long wavelength bands" (Table 1)
   - assumption: Point sources for the correction to total.  
  > "corrected to total assuming point sources." (Table 1)
   - fitting: _not stated_
   - validation: Compare final mosaic depths with JWST ETC v2.0 predictions.  
  > "ETC values correspond to S/N=5 point source depths using JWST ETC v2.0." (Table 1); "These depths compare favorably to those achieved in our final mosaic" (Deep NIRCam and NIRISS imaging)

## Software

- **astropy** : _not stated_
- **Bagpipes** : Generate representative SEDs.  
  > "In that Figure, we show representative SEDs generated using `Bagpipes` (cite: carnall:18) with the NIRCam primary filters." (Deep NIRCam and NIRISS imaging)
- **Grizli** 1.6.0.dev99: Process, align and co-add exposures.  
  > "The data reduction pipeline Grism redshift and line analysis software for space-based spectroscopy (`Grizli`, version 1.6.0.dev99) was used to process, align, and co-add the exposures." (Image Reduction)
- **Prospector** : Stellar population synthesis modeling in the associated physical-property catalog.  
  > "including photometric redshifts and stellar population synthesis modeling with `Prospector` (cite: johnson:21) (cite: wang:24catalog)." (Planned Data Release Schedule)
- **DrizzlePac** : _not stated_
- **AstroDrizzle** : Exposure background pedestals, final mosaics and inverse-variance weight images.  
  > "The background pedestal level of each exposure are computed with the AstroDrizzle software (cite: Gonzaga:12)" (Image Reduction); "which is then also used to create the final mosaics of each filter drizzled to a common pixel grid" (Image Reduction); "AstroDrizzle produces a “weight” image that has units of inverse variance of the “science” images" (Image Reduction)
- **JWST calibration pipeline** 1.8.4: Stage 1 rate.fits products used as processing inputs.  
  > "We start with the MAST `rate.fits` products produced by Stage 1 of the *JWST* calibration pipeline (v1.8.4) using calibration set `jwst_0995.pmap`." (Image Reduction)
- **JWST ETC** 2.0: Predicted S/N=5 point-source imaging depths.  
  > "ETC values correspond to S/N=5 point source depths using JWST ETC v2.0." (Table 1)
- **JWST Calibration Reference Data System (CRDS)** : Calibration reference files and photometric calibrations.  
  > "the flat-field reference files available in the JWST Calibration Reference Data System (CRDS)" (Image Reduction); "This discussion was largely resolved with calibrations derived from in-flight data and provided by CRDS `jwst_0989.pmap`." (Image Reduction)
- **Mikulski Archive for Space Telescopes (MAST)** : Download public JWST exposures and rate.fits products.  
  > "All public *JWST* NIRCam and NIRISS exposures in the Abell 2744 cluster field were downloaded from the Mikulski Archive for Space Telescopes" (Image Reduction); "We start with the MAST `rate.fits` products" (Image Reduction)
- **Amazon Web Services** : Cloud-based processing, file storage and initial data-product hosting.  
  > "Cloud-based data processing and file storage for this work is provided by the AWS Cloud Credits for Research program." (Discussion and Scientific Objectives of the UNCOVER survey); "All of these data products will be hosted initially through Amazon Web Services" (DR1: Initial Release of NIRCam/NIRISS Mosaics)
- **DELPHI** : Model galaxy counts for NIRCam survey design.  
  > "from the `DELPHI` model (cite: dayal:14; dayal:22)" (Deep NIRCam and NIRISS imaging); "to predict the number of $6{<}z{<}16$ galaxies to our detection limit." (Deep NIRCam and NIRISS imaging)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| UNCOVER primary NIRCam mosaic area | 28.8 | not stated | arcmin^2 | 3 | The UNCOVER primary NIRCam mosaic spans 28.8 arcmin$^2$ in seven filters |
| UNCOVER NIRISS parallel mosaic area | 16.8 | not stated | arcmin^2 | 3 | 16.8 arcmin$^2$ in our NIRISS parallel (F115W, F150W, F200W, F356W, and F444W). |
| Publicly released NIRCam mosaic area including other public JWST imaging | 45 | not stated | arcmin^2 | 3 | including 45 arcmin$^2$ NIRCam and 17 arcmin$^2$ NIRISS mosaics on and around the Abell 2744 cluster |
| Publicly released NIRISS mosaic area | 17 | not stated | arcmin^2 | 3 | including 45 arcmin$^2$ NIRCam and 17 arcmin$^2$ NIRISS mosaics on and around the Abell 2744 cluster |
| Absolute mosaic alignment to Gaia DR3 | 12 | not stated | mas | 2 | We have verified that with this procedure the UNCOVER mosaic is aligned to the absolute frame defined by Gaia DR3 (cite: gaia:22) at a level of 12 mas (cite: Weaver:23). |
| NIRCam primary F115W 5σ depth | 30.05 | not stated | AB | 4 | /   NIRCam   / F115W  /   6.0h   / Nov. 2,4,7,15, 2022 /      30.05      / 29.9 /     / |
| NIRCam primary F150W 5σ depth | 30.18 | not stated | AB | 4 | / (Primary)  / F150W  /   6.0h   /                     /      30.18      / 30.1 /     / |
| NIRCam primary F200W 5σ depth | 30.12 | not stated | AB | 4 | /            / F200W  /   3.7h   /                     /      30.12      / 30.0 /     / |
| NIRCam primary F277W 5σ depth | 29.75 | not stated | AB | 4 | /            / F277W  /   3.7h   /                     /      29.75      / 29.5 /     / |
| NIRCam primary F356W 5σ depth | 29.79 | not stated | AB | 4 | /            / F356W  /   3.7h   /                     /      29.79      / 29.5 /     / |
| NIRCam primary F410M 5σ depth | 29.03 | not stated | AB | 4 | /            / F410M  /   3.7h   /                     /      29.03      / 28.8 /     / |
| NIRCam primary F444W 5σ depth | 29.25 | not stated | AB | 4 | /            / F444W  /   4.6h   /                     /      29.25      / 29.2 /     / |
| NIRISS parallel F115W 5σ depth | 30.19 | not stated | AB | 4 | /   NIRISS   / F115W  /   3.7h   /    (see primary)    /      30.19      / 30.1 /     / |
| NIRISS parallel F150W 5σ depth | 30.13 | not stated | AB | 4 | / (Parallel) / F150W  /   3.7h   /                     /      30.13      / 30.2 /     / |
| NIRISS parallel F200W 5σ depth | 30.25 | not stated | AB | 4 | /            / F200W  /   3.7h   /                     /      30.25      / 30.2 /     / |
| NIRISS parallel F356W 5σ depth | 29.40 | not stated | AB | 4 | /            / F356W  /   2.1h   /                     /      29.40      / 29.2 /     / |
| NIRISS parallel F444W 5σ depth | 28.8 | not stated | AB | 4 | /            / F444W  /   2.1h   /                     /      28.8       / 28.6 /     / |

## Qualitative findings

- Public release of fully reduced NIRCam cluster and NIRISS parallel mosaics, with matched-grid HST imaging.  
  > "With this publication, we publicly release fully reduced, multiband mosaics for the first NIRCam cluster and NIRISS parallel imaging" (DR1: Initial Release of NIRCam/NIRISS Mosaics); "We also provide reduced *HST* imaging on the same WCS grids." (DR1: Initial Release of NIRCam/NIRISS Mosaics)
- Expected imaging depths compare favorably with final mosaic depths.  
  > "These depths compare favorably to those achieved in our final mosaic" (Deep NIRCam and NIRISS imaging)

## Claim tuples

- H: Can the early UNCOVER imaging be delivered as reduced multiband mosaics for community use? | E: Process, align and co-add public JWST exposures and release matched-grid imaging. | R: Primary NIRCam and NIRISS footprints span 28.8 and 16.8 arcmin^2, respectively. | F: Fully reduced NIRCam and NIRISS mosaics are publicly released. | **supported**
- H: Can the UNCOVER mosaic be placed accurately on an absolute astrometric frame? | E: Align F444W exposures to LegacySurvey DR9 and verify against Gaia DR3. | R: Absolute alignment at a level of 12 mas. | F: The absolute-frame alignment is verified at 12 mas. | **supported**

## Reasoning

- Why this data: Gravitational lensing pushes the imaging and spectroscopy beyond blank-field depths; Abell 2744 also has complementary data and ALMA access.  
  > "The imaging and spectroscopy leverages the gravitational lensing boost to push beyond depths achievable in blank fields." (Introduction); "The field also contains some of the best complementary multi-wavelength data (including deep $29$AB *HST*/ACS optical data) and is accessible by the Atacama Large Millimeter/submillimeter Array (ALMA)" (Field selection)
- Why this method: Four-pointing gap-filled NIRCam mosaic maximizes predicted z>10 galaxy detections.  
  > "The number of $z{>}10$ galaxies is maximized by a 4-pointing gap-filled NIRCam mosaic." (Deep NIRCam and NIRISS imaging)
- Alternative: Mask snowball residuals rather than rerun exposure ramp fits.  
  > "Rather than re-running the ramp fits, we identify likely snowballs as large groups of pixels with the $\mathrm{DQ}=4$ bit set in the exposure data quality array and grow a conservative mask around them." (Image Reduction)
- Alternative: Use uniform custom sky flats despite updated in-flight long-wavelength CRDS flats.  
  > "however, we use the custom sky flats that were computed in a uniform way for all short- and long-wavelength filter/detector combinations." (Image Reduction)
- How they decided it was enough: _not stated_
- Limitation (authors): Weight maps omit correlated noise from drizzle resampling.  
  > "The weight map does not account for correlated noise of the finite drizzle pixel resampling (cite: casertano:00)." (Image Reduction)
- Limitation (authors): Masked pixels reduce local effective exposure time.  
  > "Any masked pixels will not contribute to the mosaic and the total effective exposure time at those positions will therefore decrease." (Image Reduction)
- Limitation (authors): Wavelength-dependent MSA slit losses complicate precise spectroscopic flux calibration.  
  > "Slit loss through the MSA will be significant and wavelength dependent due to variation in the PSF, complicating precise flux calibration." (Scheduled NIRSpec/PRISM spectroscopic followup)
- Limitation (authors): Theoretical models dominate uncertainty in predicted galaxy counts.  
  > "The dominant uncertainty in expected numbers is the difference between theoretical models, which can differ by factors of $>10$ at $z>10$" (Deep NIRCam and NIRISS imaging)
- Limitation (authors): Some NIRSpec observations failed and required repeat visits.  
  > "The spectroscopic component of the UNCOVER survey were completed in July-August 2023, aside from a failed visit that was impacted by an electrical short." (Scheduled NIRSpec/PRISM spectroscopic followup)
- Caveat (inferred, ours): ALMA is ancillary context; this paper supplies no original ALMA measurements or ALMA analysis recipe.
- Caveat (inferred, ours): The calibration and imaging setting lists are restricted to ALMA; the numbered recipe describes the explicitly documented JWST mosaic work.
- Caveat (inferred, ours): Table 2 lists ALMA times under Notes/Depth without establishing that they are on-source integration times.
- Caveat (inferred, ours): Depths describe point sources in two-visit regions, not uniform completeness across the mosaics or extended-source sensitivity.
- Caveat (inferred, ours): Weight-map depths require scrutiny because the stated weight maps omit drizzle-correlated noise.
- Caveat (inferred, ours): Predicted galaxy counts and future spectroscopic capabilities are not measured galaxy-population results.

## Reproducibility

- Data public (paper): UNCOVER JWST data have no proprietary period; public JWST exposures were downloaded from MAST.  
  > "While there is no proprietary period associated with the UNCOVER dataset" (Planned Data Release Schedule); "All public *JWST* NIRCam and NIRISS exposures in the Abell 2744 cluster field were downloaded from the Mikulski Archive for Space Telescopes" (Image Reduction)
- Products in archive: JWST Stage 1 rate.fits products in MAST; reduced mosaics planned for MAST upon publication.  
  > "We start with the MAST `rate.fits` products produced by Stage 1 of the *JWST* calibration pipeline (v1.8.4) using calibration set `jwst_0995.pmap`." (Image Reduction); "and upon publication uploaded to the Barbara A. Mikulski Archive for Space Telescopes (MAST)." (DR1: Initial Release of NIRCam/NIRISS Mosaics)
- Missing: For ALMA: public-data status, execution selection, calibration instructions, imaging settings and any measurement procedure.
- Missing: For exact JWST reprocessing: full exposure manifest, complete Grizli configuration, source-mask construction, snowball-mask growth parameters and wisp-fit settings.
- Missing: For exact depth reproduction: aperture corrections, treatment of correlated noise and the precise two-visit region selection.
- Missing: The detailed pipeline description is deferred to an in-preparation work; catalog and spectroscopy methods are distributed across companion papers.
- Data volume (inferred): Cannot estimate bytes reliably: ALMA visibility counts, channelization and array details are absent.
- Score (inferred): 2/5, 2/5 for ALMA reproduction: three project codes and broad observing descriptions are supplied, but no ALMA processing recipe or original numeric ALMA result. JWST mosaicking is substantially better documented.
- Rediscovery candidate: no, ALMA public availability is not stated, the ALMA recipe is absent, and the numeric results concern JWST imaging rather than an ALMA discovery.

## Links

- Method: (cite: brammer:2021) (Grizli software reference.)
- Method: G. Brammer et al. in preparation (Deferred detailed reduction-pipeline description.)
- Method: (cite: kokorev:22) (Inherited HST processing procedure and historical imaging datasets.)
- Method: (cite: Gonzaga:12) (AstroDrizzle and DrizzlePac reference.)
- Method: (cite: rauscher:15) (1/f noise reference.)
- Method: (cite: Rigby:22) (Snowballs, wisps and pointing-performance references.)
- Method: (cite: carnall:18) (Bagpipes representative SED models.)
- Method: (cite: johnson:21) (Prospector stellar population synthesis modeling in the associated catalog.)
- Method: (cite: casertano:00) (Correlated noise from drizzle resampling.)
- Method: (cite: shupe:05) (Simple Imaging Polynomial WCS convention.)
- Method: (cite: leja:21) (Flexible spatially resolved galaxy models for planned slit-loss corrections.)
- Companion: (cite: Weaver:23) (Photometric catalogs and detailed effective-depth discussion.)
- Companion: (cite: wang:24catalog) (Photometric redshifts and stellar population properties.)
- Companion: (cite: furtak:23lensing) (Updated gravitational lens model and magnification estimates.)
- Companion: (cite: suess:24) (Additional broad- and medium-band imaging and DR3 photometric products.)
- Companion: (cite: price:24) (Spectroscopic design, MSA implementation, NIRCam parallel imaging and reduced PRISM spectra.)
- Companion: (cite: fujimoto:23dualz) (Ancillary DUALZ ALMA band 6 survey.)
- Related: UNCOVER
- Related: HFF-ALMA
- Related: ALMA lensing cluster survey (ALCS)
- Related: Deep UNCOVER-ALMA Legacy High-z (DUALZ) Survey
- Related: Hubble Frontier Fields
- Related: HST/BUFFALO
- Related: GLASS-JWST
- Related: JWST DD-2756
- Related: GTO-PEARLS
- Related: PRIMER

## Checks

```json
{
 "quotes": 135,
 "quotes_ok": 135,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 3,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 17,
 "numeric_problems": 0,
 "fill": {
  "facts": 117,
  "stated": 78,
  "rate": 0.667
 },
 "evidence_ok": true
}
```
