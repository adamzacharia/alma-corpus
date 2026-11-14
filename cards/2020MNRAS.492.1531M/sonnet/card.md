# NaCo polarimetric observations of Sz 91 transitional disc: a remarkable case of dust filtering

`2020MNRAS.492.1531M` | Monthly Notices of the Royal Astronomical Society 2020 | first author: Maucó, Karina | arXiv: 1912.01925 | DOI: 10.1093/mnras/stz3380

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: protoplanetary_disks
- Question: What are the dust properties and cavity structure of the Sz 91 transitional disk in polarized near-IR light, what companions can be ruled out, and what does this imply for the origin of its large sub-mm cavity?  
  > "We found that the emission is best explained by small, porous grains distributed in a disk with a $\sim$45 au cavity." (abstract)
- Target **Sz 91**: coordinates _not stated_; z/distance 159.06±1.63 pc  
  > "Sz 91 is an M0 T Tauri Star (TTS), located in the Lupus III molecular cloud (cite: romero2012)" (1 Introduction); "we used a distance to the source of $d$ = 159.06$\pm$1.63 pc (cite: bailer-jones2018)" (3.1 Stellar Properties: VOSA); distance from Gaia DR2 (bailer-jones2018)  
  > "Sz 91 is an M0 T Tauri Star (TTS), located in the Lupus III molecular cloud (cite: romero2012)" (1 Introduction); "we used a distance to the source of $d$ = 159.06$\pm$1.63 pc (cite: bailer-jones2018)" (3.1 Stellar Properties: VOSA)

## Data provenance

- ALMA projects: 2015.1.01301.S
- bands: Band 7 continuum (archival, used for overlay)  
  > "we show the ALMA Band 7 continuum archival image of Sz 91 from project ID 2015.1.01301.S (white contours)" (5 Discussion)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Other facility **VLT/NaCo**: H, Ks polarimetric imaging and L' ADI imaging  
  > "we report new PDI observations of Sz 91 obtained in the NIR ($H$ and $K_s$ bands) and new high-contrast ADI observations in the thermal IR ($L'$ band), both obtained with VLT/NaCo." (1 Introduction)
- Other facility **2MASS**: H and Ks photometry used to calibrate the NaCo data and scale the models  
  > "We therefore use the 2MASS photometry to calibrate our observations." (2.1 H and Ks band Polarimetry)
- Other facility **Las Campanas/MIKE**: single-epoch high-resolution spectrum used to exclude an SB2 companion  
  > "From this single epoch we can discard an SB2 nature of the object" (5.1.1 Dynamical clearing)
- External data: ALMA-derived inclination 49.7 deg and PA 18.1 deg used as fixed model geometry  
  > "We used an inclination of 49.7$^\circ$ and a position angle (PA) of 18.1$^\circ$ derived from ALMA observations (cite: tsukagoshi2019)" (3.2.1 MCFOST Model) [from (cite: tsukagoshi2019)]
- External data: Gaia DR2 distance 159.06±1.63 pc  
  > "we used a distance to the source of $d$ = 159.06$\pm$1.63 pc (cite: bailer-jones2018)" (3.1 Stellar Properties: VOSA) [from (cite: bailer-jones2018)]
- Simulation/model as data: MCFOST grid of 13500 radiative transfer models (DHS grains) fit to Qphi images  
  > "We ran a grid of 13500 models varying the following parameters: the minimum/maximum grain size ($a_{\rm min}$, $a_{\rm max}$), the grain porosity, the size of the cavity ($R_{\rm in}$) and the dust mass" (3.2.2 Best fit)

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

- Model H100, gamma and psi adopted from earlier work  
  > "We adopted the same $H_{100}$, $\gamma$ and $\psi$ values of (cite: canovas2015a)." (3.2.1 MCFOST Model) [from (cite: canovas2015a)]
- Polarimetric reduction follows an established imaging polarimetry pipeline  
  > "We used customised scripts to process the raw data following the imaging polarimetry pipeline described by (cite: canovas2011)." (2.1 H and Ks band Polarimetry) [from (cite: canovas2011)]

### Not stated but needed to reproduce (our reading)

- ALMA calibration, imaging parameters and reduction of the 2015.1.01301.S Band 7 image are not given
- MCFOST version and number of photon packets
- Exact frame selection for H band
- Number of principal components used per separation in PCA-ADI
- Dust composition fractions beyond 'small amount of carbonaceous particles'

## Analysis recipe

1. **Reduce polarimetric data**: Double-difference Stokes Q,U, then Qphi/Uphi maps  
  > "corrected for instrumental polarization using the double-difference method as described in (cite: canovas2011) to produce the final Stokes Q and U images." (2.1 H and Ks band Polarimetry)
   - software: custom scripts
   - parameter: central r < 4 px masked  
  > "The central r $<$ 4 px are dominated by noise, and therefore this region has been masked out" (2.1 H and Ks band Polarimetry)
   - fitting: _not stated_
   - validation: flux consistent with 2MASS within 0.05 mag  
  > "the measured flux is consistent, within an error bar of 0.05 mag, with the published 2MASS photometry" (2.1 H and Ks band Polarimetry)
2. **Estimate stellar parameters**: SED fit with BT-Settl-CIFIST models, then HR diagram with Baraffe 2015 tracks  
  > "The best fit was found for the BT-Settl-CIFIST models which are used to infer the total observed flux from the star." (3.1 Stellar Properties: VOSA)
   - software: VOSA
   - assumption: d = 159.06 pc; Av upper limit 2.5 mag  
  > "consider the extinction in the line of sight, $A_{\rm v}$, also as a fit parameter with an initial upper limit of 2.5 mag" (3.1 Stellar Properties: VOSA)
   - fitting: chi2 test against synthetic photometry  
  > "The observed (stellar) SED of the source is compared to the synthetic photometry obtained using a suit of theoretical models via a $\chi^2$ test." (3.1 Stellar Properties: VOSA)
   - validation: _not stated_
3. **Fit radiative transfer model to Qphi**: MCFOST grid with Bayesian PDFs, weights exp(-chi2/2)  
  > "where for each model we assign a relative probability as: $$\begin{equation} W_i = {\rm exp} (-\chi_i^2/2) \end{equation}$$" (3.2.2 Best fit)
   - software: MCFOST
   - parameter: Rin 35-55 au, porosity 0.1-0.9, amin 0.05-0.175 um, delta s 0.05-0.25 um, mdust 1e-6 to 1e-7 Msun  
  > "$R_{\rm in}$ (au) | 35-55, steps = 5" (Table 3)
   - assumption: DHS grains, max void fraction 0.8; inclination 49.7 deg, PA 18.1 deg fixed; Draine & Lee opacities  
  > "assuming a distribution of hollow spheres (DHS) as our grain type with a maximum volume void fraction of 0.8 (cite: min2005)" (3.2.1 MCFOST Model)
   - fitting: chi2 over pixels, sigma from annuli of Uphi image; r<0.15'' and r>0.63'' masked  
  > "the central r $<$ 0.$''$15 region (dominated by noise) as well as the outer r $>$ 0.$''$63 region (free of disk emission) of each image have been masked out" (3.2.2 Best fit)
   - validation: residual maps show no significant emission beyond noise  
  > "we do not see any significant emission on our residual maps besides the noise induced by the faint $U_{\phi}$ signal structure" (3.2.2 Best fit)
4. **L' companion detection limits**: PCA-ADI with VIP, 5 sigma contrast curves converted to mass with COND/Dusty models  
  > "We then used the COND/Dusty models for brown dwarfs and giant planets atmospheres (cite: allard2001) to convert the contrast curve into mass sensitivity limits." (3.3 Companion detection limits)
   - software: VIP
   - parameter: age 5 Myr; 2-FWHM annuli, 1 FWHM parallactic threshold  
  > "We used an age of 5 Myr." (3.3 Companion detection limits)
   - assumption: hot-start models  
  > "which in our case are based on “hot start models"" (3.3 Companion detection limits)
   - fitting: _not stated_
   - validation: _not stated_
5. **Polarized phase function**: Adjacent 0.04'' apertures along an ellipse on Qphi image, north vs south  
  > "The size of the aperture was fixed to 0.04$''$." (5.2 Polarized phase function)
   - parameter: a=0.34'', PA 18.1 deg, i 49.1 deg  
  > "semi-major axis $a$ of 0.34$''$, position angle PA of 18.1$^\circ$ and inclination $i$ of 49.1$^\circ$" (5.2 Polarized phase function)
   - fitting: _not stated_
   - validation: compared with best fit model  
  > "Our best model represents relatively well both functions" (5.2 Polarized phase function)

## Software

- **VIP** : L' calibration and PCA-ADI post-processing  
  > "we used principal component analysis coupled with ADI (cite: Amara2012; Soummer2012) as implemented in `VIP`." (2.2 L' band imaging)
- **MCFOST** : radiative transfer modelling of polarized images  
  > "We used 3D radiative transfer code MCFOST (cite: pinte2006; pinte2009) to model the polarimetric images" (3.2.1 MCFOST Model)
- **VOSA** : stellar SED fitting  
  > "We estimated the stellar properties of Sz 91 using the Virtual Observatory (VO), VO-tool VOSA" (3.1 Stellar Properties: VOSA)
- **CarPy** : reduction of MIKE spectrum  
  > "The data were reduced using the MIKE pipeline in the Carnegie Observatories’ CarPy package" (5.1.1 Dynamical clearing)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Cavity radius Rin (H and Ks) | 45 | [43, 47] | au | 3 | $R_{\rm in}$ (au)                   /   45 /     \[43, 47\] /   45 /     \[43, 47\] |
| Minimum grain size amin | 0.15 (H and Ks) | [0.12,0.16] H; [0.13,0.16] Ks | um | 3 | $a_{\rm min}$ ($\mu$m)              / 0.15 / \[0.12, 0.16\] / 0.15 / \[0.13, 0.16\] |
| Dust mass (H / Ks) | 1.29 / 1.67 | [1.07,1.35] / [1.59,2.27] | 1e-7 Msun | 3 | $m_{\rm dust}$ ($10^{-7}M_{\odot}$) / 1.29 / \[1.07, 1.35\] / 1.67 / \[1.59, 2.27\] |
| Stellar mass | 0.58 | [0.51, 0.62] | Msun | 2 | $M_{*}$ ($M_{\odot}$)     /  0.58 /   \[0.51, 0.62\] |
| Stellar age | 5.0 | [3.6, 7.4] | Myr | 2 | Age (Myr)                 /   5.0 /     \[3.6, 7.4\] |
| Companion mass limit beyond 45 au | ~8 | not stated | MJup | 4 | Giant planets with masses above $\sim$8 $M_\mathrm{Jup}$ orbiting beyond 45au could be detected in our observations |
| Significance of Qphi dip | 1.2 | not stated | sigma | 0 | found that it is significant by only 1.2$\sigma$ |
| PA minimizing N-S phase function peak offset | 9 | not stated | deg | 5 | We found that for a PA of 9$^\circ$ this difference is minimized. |

## Qualitative findings

- Polarized emission peaks inside the sub-mm cavity, suggesting partial dust filtration  
  > "The fact that the emission from small ($\mu$m) grains, as probed by our NaCo observations, peaks inside the sub-mm cavity, suggests partial filtration of dust." (5.1.1 Dynamical clearing)

## Claim tuples

- H: Small porous grains in a cavity explain the NIR polarized emission | E: MCFOST grid fit to H and Ks Qphi | R: Rin ~45 au, grains <0.4 um, porosity <40% | F: Surface layers contain small (or monomer-dominated) grains inside the sub-mm cavity | **supported**
- H: Which mechanism opens the cavity | E: Compare NaCo and ALMA with planet and dead-zone predictions | R: Different dust sizes of cavity and gas inside the cavity | F: Multiple low-mass planets most likely | **partially**
- H: Massive companions exist | E: L' PCA-ADI contrast curves | R: No detection | F: Mp < 8 MJup beyond 45 au excluded | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Internal photoevaporation rejected due to large cavity and high accretion rate  
  > "make this mechanism very unlikely" (5.1 A large cavity)
- How they decided it was enough: _not stated_
- Limitation (authors): Grain size distribution may be biased to small sizes; dust mass and optical depth uncertain  
  > "both the total dust mass and the optical depth reported here should be treated carefully" (3.2.3 Caveats of the modeling)
- Caveat (inferred, ours): ALMA data only used for overlay and literature geometry
- Caveat (inferred, ours): Models are centro-symmetric and PA fixed
- Caveat (inferred, ours): H band uses a subset of data selected for S/N

## Reproducibility

- Data public (paper): ALMA data archival; NaCo from ESO programs 098.C-0420 and 099.C-0336  
  > "ALMA Band 7 continuum archival image of Sz 91 from project ID 2015.1.01301.S" (5 Discussion)
- Products in archive: _not stated_
- Missing: Custom polarimetry scripts not released
- Missing: ALMA image processing not described
- Data volume (inferred): NaCo data a few GB; ALMA overlay optional ~ few GB
- Score (inferred): 3/5, NIR modeling well described with grid and priors, but custom scripts and ALMA processing absent.
- Rediscovery candidate: no, ALMA is minor and the main results rely on VLT/NaCo data and custom pipelines.

## Links

- Method: (cite: canovas2011) (polarimetric reduction pipeline)
- Method: (cite: GomezGonzalez2017) (VIP package)
- Companion: (cite: tsukagoshi2019) (ALMA observations of Sz 91 providing geometry)
- Companion: (cite: tsukagoshi2014) (earlier Subaru PDI of Sz 91)

## Checks

```json
{
 "quotes": 53,
 "quotes_ok": 53,
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
  "facts": 80,
  "stated": 37,
  "rate": 0.463
 },
 "evidence_ok": true
}
```
