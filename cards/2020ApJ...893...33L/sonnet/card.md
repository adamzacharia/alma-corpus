# ALMA Polarimetry Measures Magnetically Aligned Dust Grains in the Torus of NGC 1068

`2020ApJ...893...33L` | The Astrophysical Journal 2020 | first author: Lopez-Rodriguez, Enrique | arXiv: 1905.08802 | DOI: 10.3847/1538-4357/ab8013

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: agn_and_quasars, nearby_galaxies
- Question: Is the 860 micron polarization in the torus of NGC 1068 from magnetically aligned dust grains, and what does it say about the torus and its magnetic field?  
  > "Our goal is to obtain the polarization signature of magnetically aligned dust grains using resolved images of the dust continuum emission of the torus of NGC 1068." (Introduction)
- Target **NGC 1068**: coordinates 02h42m40.80s, -00d00m47.8s ICRS (phase center)  
  > "observations of NGC 1068 using the full polarization mode centered at 02h42m40.80s, -00$^{\circ}$00$'$47.8$''$ ICRS" (Observations and data Reduction); "We use a distance of $14.4$ Mpc" (4.2 Synthetic observations); z/distance 14.4 Mpc  
  > "observations of NGC 1068 using the full polarization mode centered at 02h42m40.80s, -00$^{\circ}$00$'$47.8$''$ ICRS" (Observations and data Reduction); "We use a distance of $14.4$ Mpc" (4.2 Synthetic observations); distance from _not stated_

## Data provenance

- ALMA projects: 2016.1.00176.S
- bands: Band 7 (348.5 GHz, 860 um)  
  > "Cycle 4 ALMA band 7 (348.5 GHz, 4.78 GHz bandwidth) observations of NGC 1068 using the full polarization mode" (Observations and data Reduction)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: 8.0 GHz, 336.495-350.495 GHz  
  > "Our observations comprise 8.0 GHz of wide-band dust continuum ranging in the $336.495 - 350.495$ GHz centered at 348.5 GHz" (Observations and data Reduction)
- arrays: _not stated_
- configurations: C40-7  
  > "Our observations were performed using the C40-7 nominal configuration" (Observations and data Reduction)
- baselines: _not stated_
- angular resolution: 0.077" x 0.058", PA 75.13 deg  
  > "which provided an angular resolution of $0.077\ensuremath{''} \times 0.058\ensuremath{''}$ with a position angle of 75.13$^{\circ}$" (Observations and data Reduction)
- max recoverable scale: ~0.9"  
  > "The largest recoverable scale in the data is approximately $0.9\ensuremath{''}$" (Observations and data Reduction)
- sensitivity: Stokes I rms 100 uJy/beam; polarized flux rms 20 uJy/beam  
  > "The rms noise level of the final Stokes I is $\sigma_{I} = 100$ $\mu$Jy beam$^{-1}$, where the rms noise level of the polarized flux is $\sigma_{PI} = 20$ $\mu$Jy beam$^{-1}$." (Observations and data Reduction)
- time on source: 550.2 minutes execution time  
  > "execution time of 550.2 minutes on 20170824/25" (Observations and data Reduction)
- observing dates: 2017-08-24/25  
  > "execution time of 550.2 minutes on 20170824/25" (Observations and data Reduction)
- pi or archival as stated: Own proposal, PI Lopez-Rodriguez  
  > "We performed (ID: 2016.1.00176.S, PI: Lopez-Rodriguez)" (Observations and data Reduction)
- Line: CN N=3-2 J=7/2-5/2 and J=5/2-3/2 (not stated)
- Other facility **MERLIN 5 GHz**: radio jet map for overlay  
  > "We overlaid (Fig. [4](#fig:fig4)) the 860 $\mu$m polarized flux and polarization vectors with the radio jet at 5 GHz observed with MERLIN (cite: GBO2004)." (3.3 The Total and Polarized Flux of the Extended Emission)
- Other facility **CanariCam/GTC 8.7 um**: MIR polarization map for comparison  
  > "polarization degree at 8.7 $\mu$m observed with CanariCam on the 10.4-m Gran Telescopio Canarias (cite: LR2016)" (3.3 The Total and Polarized Flux of the Extended Emission)
- External data: Torus SED-fit parameters (sigma=43 deg, Y=18, N0=4, q=0.08, tau_V=70, i=75 deg)  
  > "we took the inferred torus parameters using the SED of NGC 1068 by (cite: LR2018)" (4.2 Synthetic observations) [from (cite: LR2018)]
- External data: Velocity dispersions of HCN 3-2 (40 km/s) and HCO+ 3-2 (10 km/s)  
  > "$\sigma_{v, HCN 3-2} = 40$ km s$^{-1}$ and $\sigma_{v, HCO^{+} 3-2} = 10$ km s$^{-1}$ using ALMA observations (cite: Imanishi2018)" (5.3 The magnetic field strength of the torus) [from (cite: Imanishi2018)]
- External data: Torus dust mass (1.6+-0.2)e3 Msun  
  > "(cite: GB2016) estimated a dust mass of the torus to be $(1.6\pm0.2) \times 10^{3}$ M$_{\odot}$" (5.3 The magnetic field strength of the torus) [from (cite: GB2016)]
- External data: B=52 mG at 0.4 pc, Bt/B0~0.1  
  > "The magnetic field strength at a distance of 0.4 pc of NGC 1068 was estimated to be $52^{+4}_{-8}$ mG (cite: LR2015)" (5.3 The magnetic field strength of the torus) [from (cite: LR2015)]
- Simulation/model as data: CLUMPY torus images from HYPERCAT as column density proxy, toroidal B-field model  
  > "we use the surface brightness and cloud distribution computed by the radiative transfer code CLUMPY torus (cite: nenkova2008)" (4.2 Synthetic observations)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0006-0623 (flux and bandpass); polarization calibrator J0006-0623; phase J0239-0234  
  > "The flux and bandpass calibrator was J0006-0623, and phase calibrator was J0239-0234" (Observations and data Reduction)
- flux scale uncertainty: ~10%  
  > "ALMA’s flux calibration is $\sim10$%, as determined by their flux monitoring program." (Observations and data Reduction)
- self calibration: _not stated_

### Imaging

- task: CASA tclean  
  > "using the Common Astronomy Software Applications (cite: mcmullin2007) with the task TCLEAN with a natural weighting parameter" (Observations and data Reduction)
- deconvolver: _not stated_
- weighting robust: natural  
  > "with the task TCLEAN with a natural weighting parameter" (Observations and data Reduction)
- uv taper: _not stated_
- cell size: 25 mas/pixel  
  > "the final images are pixelated to the pixel scale, 25 mas pixel$^{-1}$, of the ALMA observations" (4.2 Synthetic observations)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.077" x 0.058", PA 75.13 deg  
  > "convolved with the observed beam, $77 \times 58$ mas ($4.6 \times 3.5$ pc) and PA $= 75.13^{\circ}$" (4.2 Synthetic observations)
- final rms: Stokes I 100 uJy/beam; PI 20 uJy/beam  
  > "The rms noise level of the final Stokes I is $\sigma_{I} = 100$ $\mu$Jy beam$^{-1}$" (Observations and data Reduction)

### Inherited from earlier work

- Magnetic field model Stokes equations for optically thin dust  
  > "We here follow these standard approaches to estimate the expected polarization of the torus at $860$ $\mu$m by dust emission of magnetically aligned dust grains." (4.1 Model definition) [from (cite: king2018); (cite: FP2000)]
- Turbulent-to-ordered field ratio and modified DCF method  
  > "(cite: H2009) show that the ratio of turbulent to large-scale components of the magnetic field strength" (5.3 The magnetic field strength of the torus) [from (cite: H2009)]

### Not stated but needed to reproduce (our reading)

- Number of clean iterations, threshold, masks, and cell/image size in tclean
- Polarization calibration and self-calibration procedure and CASA version for data reduction
- Continuum channel selection excluding the CN line
- Debiasing method for polarization
- Parameters of HYPERCAT image generation (not yet published) and the bin position/aperture definitions
- Method for calculating the angular dispersion alpha in detail
- Line-fitting and continuum subtraction details for CN

## Analysis recipe

1. **Image Stokes I, Q, U**: tclean with natural weighting, continuum from 8 GHz bandwidth  
  > "The dust continuum and polarization images were estimated using the Common Astronomy Software Applications (cite: mcmullin2007) with the task TCLEAN with a natural weighting parameter." (Observations and data Reduction)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Compute polarization degree and PA**: P = sqrt(Q^2+U^2), PA = 0.5 arctan(U/Q), debiased  
  > "The degree of polarization was corrected by bias." (Observations and data Reduction)
   - software: CASA
   - parameter: minimum detectable polarization 0.1%, systematic 0.03%  
  > "ALMA provides a systematic uncertainty in linear polarization of 0.03%, which corresponds to a minimum detectible polarization of 0.1%." (Observations and data Reduction)
   - fitting: _not stated_
   - validation: vectors shown for P/sigma_P >= 3  
  > "Each polarization vector shows the E-vector with a statistically independent measurement of $P/\sigma_{P} \ge 3$." (3 Results)
3. **Torus profile along the equatorial axis**: Co-add Stokes IQU in bins of 25x83 mas along PA 105 deg within 12x5 pc region, then debias  
  > "we co-added the Stokes IQU at each location along the equatorial axis within bins of $25$ mas $\times$ $83$ mas ($1.5 \times 4.8$ pc)" (3.1 The Total and Polarized Flux of the Torus)
   - fitting: _not stated_
   - validation: independent aperture measurement at 0.12" east  
  > "To obtain an independent polarization measurement of the East region of the torus, we estimate the polarization within a $0.07\ensuremath{''} \times 0.06\ensuremath{''}$" (3.1 The Total and Polarized Flux of the Torus)
4. **Fit CN N=3-2 doublet**: Two 1D Gaussian profiles  
  > "We fit the emission lines with two 1D Gaussian profiles." (3.2 The CN Emission Line of the Torus)
   - fitting: two Gaussians  
  > "We fit the emission lines with two 1D Gaussian profiles." (3.2 The CN Emission Line of the Torus)
   - validation: _not stated_
5. **Synthetic polarimetric observations of toroidal B-field**: CLUMPY/HYPERCAT cloud distribution as column density, Stokes equations with toroidal field, convolve with ALMA beam via CASA  
  > "We obtain the synthetic Stokes IQU observations using CASA v5.4" (4.2 Synthetic observations)
   - software: CASA, HYPERCAT, CLUMPY
   - parameter: i=75 deg, theta=110 deg, p0=0.1, full resolution 1.2 mas, 14.4 Mpc  
  > "we adopt a $p_{0} = 0.1$ (cite: FP2000)" (4.1 Model definition)
   - assumption: toroidal field with constant strength B0(r)=const; homogeneous grain alignment; optically thin; extinction curve R_V=5.5 (WD2001)  
  > "We assume a magnetic field distribution with a constant strength as a function of the radial distance to the center, $B_{0}(r) = const.$" (4.1 Model definition)
   - fitting: no formal fit; manual parameter exploration  
  > "the nominal torus parameters used in Section [4.2](#sec:syntobs) were explored" (4.4 Exploration of torus model parameters)
   - validation: compare synthetic degree and PA profile along PA 105 deg with observations  
  > "we compute the profiles of the Stokes I, degree and polarized flux as a function of the radius at a PA of $105^{\circ}$ using the synthetic observations" (4.2 Synthetic observations)
6. **Magnetic field strength and turbulence**: Hildebrand 2009 angular dispersion ratio and modified DCF: B0 ~ sqrt(8 pi rho) sigma_v/alpha  
  > "$$\begin{equation} B_{o} \simeq \sqrt{8\pi\rho} \frac{\sigma_{v}}{\alpha} \end{equation}$$" (5.3 The magnetic field strength of the torus)
   - parameter: sigma_v=10 km/s, alpha=5+-2 deg  
  > "We take a velocity dispersion of $\sigma_{V} = 10$ km s$^{-1}$." (5.3 The magnetic field strength of the torus)
   - assumption: median volume mass density 1.4e-22 g/cm3 of whole torus (from LR2018)  
  > "yield a median volume mass density of $(1.4^{+1.43}_{-0.62}) \times 10^{-22}$ g cm$^{-3}$" (5.3 The magnetic field strength of the torus)
   - fitting: _not stated_
   - validation: compared with B scaled from 0.4 pc via B∝r^-2 (~0.14 mG at 8 pc)  
  > "we estimate a magnetic field strength at 8 pc of $\sim0.14$ mG, which is in agreement within the uncertainties of our measurements" (5.3 The magnetic field strength of the torus)

## Software

- **CASA** v5.4 (synthetic observations): imaging with tclean and synthetic observations  
  > "We obtain the synthetic Stokes IQU observations using CASA v5.4" (4.2 Synthetic observations)
- **HYPERCAT** : CLUMPY torus 2D images  
  > "HYPERCAT uses the CLUMPY torus models with any combination of torus model parameters to generate physically scaled and flux-calibrated 2D images" (4.2 Synthetic observations)
- **Astropy** : listed in software section  
  > "ASTROPY (cite: 2013A&A...558A..33A) CASA (cite: mcmullin2007)" (Software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Peak torus polarization (east) | 3.7 | 0.5 | % | 3 | we measure a statistically significant polarized peak of $3.7\pm0.5$% in three consecutive bins |
| Aperture polarization degree at 0.12" east | 2.2 | 0.3 | % | 3 | The degree and PA of polarization were measured to be $2.2\pm0.3$% and $19\pm2^{\circ}$, respectively. |
| Aperture E-vector PA | 19 | 2 | deg | 3 | $2.2\pm0.3$% and $19\pm2^{\circ}$ |
| CN J=7/2-5/2 peak flux | 10.62 | 0.32 | mJy | 4 | The J=7/2-5/2 component has a peak flux of $10.62\pm0.32$ mJy |
| CN J=5/2-3/2 peak flux | 7.84 | 0.52 | mJy | 4 | The J=5/2-3/2 component has a peak flux of $7.84\pm0.52$ mJy |
| Turbulent-to-ordered field ratio | 0.062 | 0.025 | dimensionless | 6 | $\langle B^{2}_{t}\rangle^{1/2} / B_{o} = 0.062\pm0.025$ |
| Large-scale B-field strength (east torus, 3-8 pc) | 0.67 | +0.94/-0.31 | mG | 6 | We estimate a magnetic field strength of $B = 0.67_{-0.31}^{+0.94}$ mG |
| Model torus constraints | i>65 deg, sigma=33-50 deg, q<<1, Y>=17 | not stated | mixed | 5 | the torus 1) is highly inclined, $i>65^{\circ}$, 2) has intermediate angular widths $\sigma = 33-50^{\circ}$ |

## Qualitative findings

- Core is unpolarized; polarization rises with radius along the equatorial plane in the east  
  > "We find that the polarization increases as a function of the distance from the core along the equatorial plane" (3.1 The Total and Polarized Flux of the Torus)

## Claim tuples

- H: The torus polarization at 860 um arises from magnetically aligned dust grains in a toroidal field | E: Synthetic polarimetry of CLUMPY torus with toroidal B-field compared to ALMA | R: Model with i=75, tilt 110 reproduces general polarization behavior | F: Polarization from aligned grains in an optically thin torus layer | **supported**
- H: East-west asymmetry is due to varying turbulence | E: Compare polarization with HCN/HCO+ velocity dispersion | R: Polarized region co-spatial with low velocity dispersion | F: Turbulence increases from east to west | **partially**
- H: Alternative mechanisms (synchrotron, self-scattering) explain the torus polarization | E: Compare location, degree, PA, and expected grain sizes | R: Inconsistent | F: Ruled out | **supported**

## Reasoning

- Why this data: Sub-mm dust is optically thin and ALMA alone resolves the torus  
  > "At sub-mm wavelengths, the dust is optically thin and the bulk emission of the dusty disk is well sampled." (Introduction)
- Why this method: _not stated_
- Alternative: Synchrotron and dust self-scattering rejected as origin of torus polarization  
  > "the location of the measured polarization, $\sim8$ pc east from the core, and the measured degree of polarization, $2.2\pm0.3$%, rule out this mechanism" (5.4 Alternative polarization mechanisms)
- How they decided it was enough: _not stated_
- Limitation (authors): B-field strength is an upper limit because median density of the whole torus was used; axisymmetric model cannot explain asymmetry  
  > "Thus, we estimate an upper-limit of the large-scale magnetic field strength in the eastern size of the torus." (5.3 The magnetic field strength of the torus)
- Caveat (inferred, ours): Model constrained only qualitatively by hand exploration, no formal fit or uncertainties
- Caveat (inferred, ours): Jet contamination in the core beam not removed
- Caveat (inferred, ours): DCF applied with whole-torus density and one assumed sigma_v
- Caveat (inferred, ours): Inconsistent PA quoted (109 vs 19 deg) and E vs B vector conventions

## Reproducibility

- Data public (paper): ALMA project 2016.1.00176.S cited in acknowledgments  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2016.1.00176.S." (Acknowledgments)
- Products in archive: _not stated_
- Code: _not stated_
- Missing: Polarization calibration and imaging details
- Missing: HYPERCAT model code not published
- Missing: Exact aperture definitions and alpha computation
- Data volume (inferred): ~100-300 GB raw for the full-polarization Band 7 C40-7 execution
- Score (inferred): 3/5, Public data and basic recipe, but imaging parameters and model implementation are incomplete.
- Rediscovery candidate: no, Imaging details are sparse and the model relies on unpublished HYPERCAT.

## Links

- Method: (cite: king2018) (Stokes parameter formalism for synthetic polarization)
- Method: (cite: H2009) (Turbulent-to-ordered ratio and modified DCF)
- Method: (cite: nenkova2008) (CLUMPY torus model)
- Companion: (cite: Imanishi2018) (ALMA HCN/HCO+ torus kinematics)
- Companion: (cite: GB2016) (ALMA Band 6 torus observations)
- Companion: (cite: LR2018) (SED-based torus parameters)

## Checks

```json
{
 "quotes": 69,
 "quotes_ok": 69,
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
  "facts": 82,
  "stated": 53,
  "rate": 0.646
 },
 "evidence_ok": true
}
```
