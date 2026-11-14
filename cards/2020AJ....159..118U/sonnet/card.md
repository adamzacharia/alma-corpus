# Near-infrared Imaging of a Spiral in the CQ Tau Disk

`2020AJ....159..118U` | The Astronomical Journal 2020 | first author: Uyama, Taichi | arXiv: 1910.07605 | DOI: 10.3847/1538-3881/ab7006

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: protoplanetary_disks
- Question: Does the CQ Tau disk host a spiral or companion candidates in L'-band and H-band imaging, and what are its nature (thermal vs scattered) and origin?  
  > "To further search for protoplanets as well as asymmetric features in the CQ Tau disk, we used two high-contrast imaging observations with Keck/NIRC2 and Subaru/AO188+HiCIAO." (Introduction)
- Target **CQ Tau**: coordinates RA = 05:35:58.47, Dec = +24:44:54.1  
  > "CQ Tau (RA = 05:35:58.47, Dec = +24:44:54.1) is a YSO in the Taurus star forming region" (Introduction); z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2017.1.01404.S
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 69 mas x 51 mas beam  
  > "a beam size of 69 mas and 51 mas for major-axis and minor-axis, respectively" (Observations and Results)
- max recoverable scale: _not stated_
- sensitivity: ~23 uJy/beam noise  
  > "which achieved a noise level of $\sim$23 $\mu$Jy/beam" (Observations and Results)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: Archival, Cycle 5, PI L. Testi  
  > "We also used an ALMA archival image, observed in Cycle 5 (ID: 2017.1.01404.S, PI: L. Testi)" (Observations and Results)
- Other facility **Keck/NIRC2**: L'-band vortex coronagraph ADI imaging, 2018 Dec 24, 1800 s  
  > "CQ Tau was observed on UT 2018 Dec 24 (PI: D. Mawet) using the Keck/NIRC2 vortex coronagraph" (Observations and Results)
- Other facility **Subaru/AO188+HiCIAO**: H-band polarimetric imaging (SEEDS), 2015 Dec 31, 540 s  
  > "Subaru/AO188+HiCIAO observed CQ Tau in a combination of PDI and ADI as part of the SEEDS project" (Subaru/HiCIAO)
- External data: Disk inclination 35 deg and major-axis PA 55 deg  
  > "derived by (cite: Ubeira2019): $i=35\ensuremath{^\circ}$ and PA$_a = 55\ensuremath{^\circ}$" (Comparison of the Two Data Sets) [from (cite: Ubeira2019)]
- External data: L'-band photometry used to convert ADU to surface brightness  
  > "We converted ADU into the surface brightness using a previous $L^\prime$-band photometry (cite: McDonald2017)" (Keck/NIRC2) [from (cite: McDonald2017)]
- External data: Stellar T=6900 K, L=10 Lsun  
  > "$T_\star$=6900 K and $L_\star=10L_{\odot}$ (cite: Testi2001; Ubeira2019)" (Scattering) [from (cite: Testi2001; Ubeira2019)]
- External data: Small grain surface density 0.0375 g/cm2  
  > "With the small grain surface density of 0.0375 g/cm$^2$ of CQ Tau’s disk (cite: Ubeira2019)" (Disk Temperature) [from (cite: Ubeira2019)]

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

- Details of the ALMA data set described elsewhere  
  > "Details of this data set as well as other ALMA data of CQ Tau are described in (cite: Ubeira2019)." (Observations and Results) [from (cite: Ubeira2019)]
- HiCIAO PDI reduction with IRAF pipeline as in earlier studies  
  > "we reduced the polarimetric data sets by means of an `IRAF` pipeline, which was used in previous HiCIAO PDI studies (cite: Hashimoto2011; Hashimoto2012)" (Subaru/HiCIAO) [from (cite: Hashimoto2011; Hashimoto2012)]

### Not stated but needed to reproduce (our reading)

- ALMA calibration and imaging details (robust, CASA version) not given
- Which ALMA image product used
- Exact ALMA continuum band/frequency
- VIP parameters beyond PC=8 and IWA=16 pix (FoV, PCA options)
- Details of forward-model injection positions and fluxes
- Distance to CQ Tau

## Analysis recipe

1. **ADI reduction of NIRC2**: PCA-based ADI with VIP, PC=8, IWA=16 pix  
  > "We adopted IWA=16 pix so that the asymmetric feature is reproduced with a higher SNR." (Keck/NIRC2)
   - software: VIP
   - fitting: _not stated_
   - validation: Feature survives wide range of PC values  
  > "The feature appears robust because it survives for a wide range of PC values" (Keck/NIRC2)
2. **Fit spiral pitch angle in HiCIAO PI**: Best-fit logarithmic spiral to radial maxima in 1 deg azimuthal bins of deprojected image  
  > "The trace was identified as radial maxima in azimuthal bins of $1\ensuremath{^\circ}$ in the image obtained after deprojection" (Comparison of the Two Data Sets)
   - fitting: _not stated_
   - validation: _not stated_
3. **Forward modeling throughput**: Inject fake PSFs along fitted spiral and measure input/output flux ratio  
  > "We used the off-axis PSF of CQ Tau and injected fake PSFs at several separations and position angles to produce fake spiral features" (Comparison of the Two Data Sets)
   - fitting: _not stated_
   - validation: _not stated_
4. **Grain temperature and scattering estimates**: Optically thick thermal balance for grain temperature; analytic scattered-light formula with single scattering  
  > "Here, we assume $H(1,\omega_\nu)=1$ (single scattering) for simplicity." (Scattering)
   - assumption: Gas-to-dust ratio 100; disk optically thick at L'  
  > "We assume that the disk is optically thick at L$^\prime$-band." (Disk Temperature)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **VIP** : PCA ADI reduction of NIRC2 data  
  > "the data set was processed via the vortex image processing (cite: Gonzalez2017) package that applies principal component analysis (PCA) for the ADI reduction" (Keck/NIRC2)
- **IRAF** : HiCIAO PDI reduction  
  > "we reduced the polarimetric data sets by means of an `IRAF` pipeline" (Subaru/HiCIAO)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Spiral pitch angle (HiCIAO) | 34 | 2 | deg | 2 | The fitted result for the spiral (the central image in Figure [\[fig: HiCIAO\]](#fig: HiCIAO)) is $34\ensuremath{^\circ}\pm2\ensuremath{^\circ}$. |
| Throughput at 50 au | 0.54 | not stated | dimensionless | 3 | a flux recovered by a throughput of 0.54 at 50 au, which corresponds to 126 mJy/arcsec$^2$ at the brightest region in the spiral |
| Grain temperature | 202.5 | not stated | K | 4 | the temperature of the grains is expected to be $T_{\rm grain}\sim$202.5K |
| Observed NIRC2 spiral brightness | 68 | 8.5 | mJy/arcsec^2 | 1 | the brightest region in this feature has 68$\pm$8.5 mJy/arcsec$^2$ |

## Qualitative findings

- No companion candidates detected; new spiral overlapping ALMA dust ring  
  > "Apart from the spiral feature our observations could not detect any companion candidates." (abstract)

## Claim tuples

- H: Is the L'-band spiral explained by scattering alone? | E: Analytic scattered-light estimate vs observed brightness | R: Predicted 8.5 mJy/arcsec2 vs much brighter observed | F: Thermal emission (~200 K) needed unless inner disk acts as light source | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Pitch angle approximate due to inclination/projection effects  
  > "Therefore, our measurements of the arm pitch angles are approximations only." (Comparison of the Two Data Sets)
- Caveat (inferred, ours): Spiral SNR only ~5-8
- Caveat (inferred, ours): Throughput correction model dependent
- Caveat (inferred, ours): Single-scattering and optically thick assumptions crude

## Reproducibility

- Data public (paper): ALMA archival data used; Subaru data via SMOKA  
  > "obtained from the SMOKA, which is operated by the Astronomy Data Center" (Acknowledgments)
- Products in archive: _not stated_
- Missing: ALMA image processing details
- Missing: VIP parameter details
- Data volume (inferred): small (<10 GB)
- Score (inferred): 3/5, ALMA only for overlay; IR data and recipe partly specified.
- Rediscovery candidate: no, ALMA minor and main results rely on non-ALMA IR data.

## Links

- Method: (cite: Gonzalez2017) (VIP package)
- Companion: (cite: Ubeira2019) (ALMA data of CQ Tau)
- Related: SEEDS

## Checks

```json
{
 "quotes": 31,
 "quotes_ok": 31,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 4,
 "numeric_problems": 0,
 "fill": {
  "facts": 68,
  "stated": 24,
  "rate": 0.353
 },
 "evidence_ok": true
}
```
