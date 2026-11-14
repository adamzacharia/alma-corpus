# A Magnified View of Circumnuclear Star Formation and Feedback around an Active Galactic Nucleus at z = 2.6

`2018ApJ...866L..12G` | The Astrophysical Journal Letters 2018 | first author: Geach, J. E. | arXiv: 1807.03313 | DOI: 10.3847/2041-8213/aae375

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies, agn_and_quasars
- Question: What are the resolved molecular gas properties on sub-kpc scales around the AGN in the lensed galaxy 9io9 at z=2.6, and does the AGN affect star formation in the circumnuclear ring?  
  > "9io9 offers a unique opportunity to study the resolved properties of the cold and dense ISM on sub-kiloparsec scales around the central engine of a growing SMBH" (Introduction)
- Target **9io9**: coordinates 02h09m41.3s, +00d15m58.5s  
  > "9io9 (02$^{\rm h}$09$^{\rm m}$41.3$^{s}$, +00$^\circ$15$'$58.5$''$)" (Observations); "with $z=2.5543\pm0.0002$" (3.1 Basic properties); z/distance z=2.5543±0.0002  
  > "9io9 (02$^{\rm h}$09$^{\rm m}$41.3$^{s}$, +00$^\circ$15$'$58.5$''$)" (Observations); "with $z=2.5543\pm0.0002$" (3.1 Basic properties); distance from this work, from CO(4-3) and CI(1-0) line profiles  
  > "9io9 (02$^{\rm h}$09$^{\rm m}$41.3$^{s}$, +00$^\circ$15$'$58.5$''$)" (Observations); "with $z=2.5543\pm0.0002$" (3.1 Basic properties)

## Data provenance

- ALMA projects: 2017.1.00814.S
- bands: Band 4, tuning 139.2 GHz  
  > "The representative frequency of the tuning was 139.2 GHz in Band 4" (Observations)
- frequencies and spectral setup: four SPWs at 127.196, 129.071, 139.196, 141.071 GHz; 480 channels per 1.875 GHz baseband, FDM  
  > "with central frequencies of the four spectral windows 127.196, 129.071, 139.196, 141.071 GHz" (Observations); "480 channels per 1.875 GHz-wide baseband with a total bandwidth of 3.6 GHz" (Observations)
- continuum bandwidth: _not stated_
- arrays: ALMA 12 m array  
  > "was observed with the ALMA 12 m array on 11$^{\rm th}$ and 14$^{\rm th}$ December 2017" (Observations)
- configurations: C43-6, max baselines ~3000 m  
  > "The array was in configuration C43–6 with maximum baselines $\sim$3000 m" (Observations)
- baselines: _not stated_
- angular resolution: 0.27'' x 0.21'', PA 88 deg  
  > "giving a synthesized beam $0.27''\times0.21''$ at a position angle of 88 degrees" (Observations)
- max recoverable scale: _not stated_
- sensitivity: 150 uJy per 23 MHz (50 km/s) channel  
  > "we reached a 1$\sigma$ (rms) sensitivity of 150 $\mu$Jy per 23 MHz (50 km s$^{-1}$) channel" (Observations)
- time on source: 1.8 hours (two 53 min execution blocks)  
  > "After two executions that built up 1.8 hours on-source integration" (Observations)
- observing dates: 11 and 14 December 2017  
  > "on 11$^{\rm th}$ and 14$^{\rm th}$ December 2017" (Observations)
- pi or archival as stated: _not stated_
- Line: CI 3P1-3P0 (J=1-0) (492 GHz)
- Line: CO J=4-3 (461 GHz)
- Line: HNC J=5-4 (453.270 GHz)
- Line: CN N=4-3 (hyperfine groups ~452.6-453.6 GHz) (~452.628, 453.389, 453.606 GHz)
- Other facility **HST (MAST)**: some data obtained from MAST; use not detailed  
  > "Some of the data presented in this paper were obtained from the Mikulski Archive for Space Telescopes (MAST)." (Acknowledgements)
- External data: CN relative line intensities calculated at 300 K from CDMS  
  > "adopting the relative line intensities from the Cologne Database for Molecular Spectroscopy (Muller et al. 2005), calculated at 300 K" (4.2 A possible dense molecular outflow) [from Muller et al. 2005]
- External data: CO(3-2) derived M_H2 of 3.5e10 Msun (comparison)  
  > "deriving a slightly lower $M_{\rm
  H_2}=(3.5\pm 0.2)\times10^{10}M_\odot$" (3.4 Molecular gas mass) [from Rivera et al. (2018)]

## Processing

### Calibration

- pipeline or manual: ALMA Science Pipeline calibrated measurement set used  
  > "We make use of the ALMA Science Pipeline produced calibrated measurement set" (Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: pipeline-calibrated MS used  
  > "We make use of the ALMA Science Pipeline produced calibrated measurement set" (Observations)
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA (v.5.1.0-74.el7) clean, frequency mode  
  > "image the visibilities using the casa (v.5.1.0-74.el7) *clean* task" (Observations)
- deconvolver: multiscale, scales 0'', 0.5'', 1.25''  
  > "employing multiscale (scales of 0$''$, 0.5$''$ and 1.25$''$)" (Observations)
- weighting robust: natural weighting  
  > "use natural weighting in the imaging" (Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: clean to 1 sigma stopping threshold  
  > "We clean down to a stopping threshold of 1$\sigma$" (Observations)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.27'' x 0.21'', PA 88 deg  
  > "giving a synthesized beam $0.27''\times0.21''$ at a position angle of 88 degrees" (Observations)
- final rms: _not stated_

### Inherited from earlier work

- Molecular gas mass from CI formula, X_CI=3e-5 and Q10=0.5  
  > "we follow previous works (Weiß et al. 2003; Papadopoulos et al. 2004; Papadopoulos & Greve 2004; Wagg et al. 2006; Alaghband-Zadeh et al. 2013; Bothwell et al. 2017)" (3.4 Molecular gas mass) [from Papadopoulos & Greve 2004]
- Lens model similar to earlier model  
  > "generally the lens model is similar the one presented in Geach et al. (2015)" (3.2 Lens modelling) [from Geach et al. (2015)]
- f_d/t from CO(4-3)/CI ratio  
  > "indicating $f_{d/t}\sim0.5$ (Papadopoulos & Geach 2012)" (4.1 The molecular ring) [from Papadopoulos & Geach 2012]

### Not stated but needed to reproduce (our reading)

- Line-free channels used for continuum subtraction
- Cell size and image size
- Mask definition for clean
- Lens model priors, number of pixels, and Voronoi settings
- galpak3d starting values and priors, and the code modification
- Details of how HNC/CN fit was done (fitter, priors)
- Flux calibrator and flux scale uncertainty
- Whether CASA pipeline version was recorded
- Continuum flux measurement

## Analysis recipe

1. **Image cubes**: CASA clean, multiscale, natural weighting, to 1 sigma  
  > "employing multiscale (scales of 0$''$, 0.5$''$ and 1.25$''$) and cleaning in frequency mode" (Observations)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Redshift and line fluxes/luminosities**: Redshift from mid-point of fwzi of continuum-subtracted lines; fluxes summed in >=3 sigma region over |dV|<500 km/s; uncertainties by 1000 noise realisations  
  > "By repeating this process 1000 times we asses the standard deviation in $\int S_\nu dV$ and derived luminosity, which we take as the 1$\sigma$ uncertainty." (3.1 Basic properties)
   - assumption: Planck 2015 cosmology  
  > "we assume a ‘*Planck* 2015’ cosmology" (Introduction)
   - fitting: _not stated_
   - validation: _not stated_
3. **Lens modelling and source-plane cubes**: Semi-linear inversion with power-law primary lens, SIS companion, external shear, Bayesian evidence, MCMC on CO(4-3) integrated map, random Voronoi source pixelization; source-plane cube per channel  
  > "The set of parameters is optimized using the Markov Chain Monte Carlo (MCMC) method (Suyu et al. 2006)" (3.2 Lens modelling)
   - assumption: Both lenses at same redshift for M/L ratio  
  > "assuming that both lie at the same redshift" (3.2 Lens modelling)
   - fitting: MCMC, best fit by Bayesian evidence  
  > "until the global best fit has been obtained according to the Bayesian evidence (Suyu et al. 2006)" (3.2 Lens modelling)
   - validation: _not stated_
4. **Fit ring kinematics**: galpak3d ring/disk model on source-plane CO(4-3) cube after PSF homogenisation (135 mas kernel); tanh rotation curve; 1000 chains of up to 5000 iterations with 10% perturbed starts  
  > "run 1000 independent chains, each with a maximum of 5000 iterations" (3.3 Dynamical modelling)
   - software: galpak3d
   - assumption: alpha=0, Gaussian vertical profile  
  > "As in previous works, we fix $\alpha=0$" (3.3 Dynamical modelling)
   - fitting: Median of converged parameters, 16th/84th percentiles as uncertainty  
  > "We take the 50th percentile of the converged parameters over the 1000 chains as the final estimate" (3.3 Dynamical modelling)
   - validation: Median reduced chi2 = 1.08  
  > "with a median reduced $\chi^2=1.08$" (3.3 Dynamical modelling)
5. **Molecular gas mass**: CI(1-0) luminosity to M_H2 formula  
  > "we assume a Ci/H$_2$ abundance $X_{\rm CI}=3\times10^{-5}$ and excitation $Q_{10}=0.5$" (3.4 Molecular gas mass)
   - assumption: X_CI=3e-5, Q10=0.5, A10=7.93e-8 s^-1  
  > "$A_{10}=7.93\times10^{-8}$ s$^{-1}$" (3.4 Molecular gas mass)
   - fitting: _not stated_
   - validation: Compared with Rivera et al. CO(3-2) mass  
  > "however systematic uncertainties on $\alpha_{\rm CO}$ and lensing magnification could easily bring the values into parity" (3.4 Molecular gas mass)
6. **Dynamical mass and SFR**: Mdyn=Vmax^2 Rmax/G; SFR = eps f_d/t M_H2 with eps=500 Lsun/Msun  
  > "$\epsilon=500\,(L_\odot/M_\odot)$ (Shirley et al. 2003; Scoville et al. 2004)" (4.1 The molecular ring)
   - assumption: f_d/t~0.5 from L'CO(4-3)/L'CI  
  > "indicating $f_{d/t}\sim0.5$ (Papadopoulos & Geach 2012)" (4.1 The molecular ring)
   - fitting: _not stated_
   - validation: _not stated_
7. **Deblend HNC/CN feature**: Fit HNC(5-4)+CN(4-3) with shared Gaussian width and redshift, free amplitudes and constant continuum; CN LTE optically thin with CDMS intensities at 300 K  
  > "We fit the spectrum allowing the HNC$(J=5\rightarrow 4)$ and CN$(N=4\rightarrow 3)$ amplitudes, $\sigma_{\rm dense}$ and redshift (assuming the same for both species) to vary as free parameters." (4.2 A possible dense molecular outflow)
   - assumption: LTE, optically thin, 300 K  
  > "we assume local thermodynamic equilibrium and optically thin emission" (4.2 A possible dense molecular outflow)
   - fitting: _not stated_
   - validation: Noted deblending depends strongly on redshift (fixing z=2.5534 raises HNC)  
  > "we caution the reader that the deblending is highly dependent on redshift." (4.2 A possible dense molecular outflow)

## Software

- **CASA** 5.1.0-74.el7: imaging with clean  
  > "image the visibilities using the casa (v.5.1.0-74.el7) *clean* task" (Observations)
- **galpak3d** 1.8.8: rotating ring/disk fit to source-plane CO(4-3) cube  
  > "We use the code *galpak3d* (Bouché et al. 2015) (version 1.8.8)" (3.3 Dynamical modelling)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Redshift | 2.5543 | 0.0002 | dimensionless | 2 | $z=2.5543\pm0.0002$ |
| CO(4-3) integrated flux | 25.9 | 0.2 | Jy km/s | 2 | $S\Delta V=25.9\pm0.2$ Jy km s$^{-1}$ |
| CI(1-0) integrated flux | 9.5 | 0.1 | Jy km/s | 2 | $S\Delta V=9.5\pm0.1$ Jy km s$^{-1}$ |
| Total magnification | 14.7 | 0.3 | dimensionless | 3 | The total magnification is $\mu=14.7\pm0.3$ |
| Ring outer radius Rmax | 2647 | +88/-160 | pc | 4 | $R_{\rm
  max}=322^{+11}_{-20}$ mas ($2647^{+88}_{-160}$ pc) |
| Vmax | 360 | +49/-11 | km/s | 4 | $V_{\rm
  max}=360^{+49}_{-11}$ km s$^{-1}$ |
| Inclination | 50 | +3/-8 | degrees | 4 | $i=50^{+3}_{-8}$ degrees |
| Intrinsic CI luminosity | 8.7e9 | 0.1e9 | K km/s pc^2 | 2 | $L'_{\rm CI}=(8.7\pm0.1)\times10^9$ K km s$^{-1}$ pc$^2$ |
| M_H2 | 7.5e10 | 0.1e10 | Msun | 5 | $M_{\rm
  H_2}=(7.5\pm 0.1)\times10^{10}M_\odot$ |
| Dynamical mass | 8.1e10 | +1.5/-0.8 e10 | Msun | 6 | $M_{\rm dyn}=(8.1^{+1.5}_{-0.8})\times10^{10}M_\odot$ |
| L'CO(4-3)/L'CI | 3.7 | 0.1 | dimensionless | 6 | $L'_{\rm CO(4-3)}/L'_{\rm CI}=3.7\pm 0.1$ |
| Ring star formation rate | ~2800 | not stated | Msun/yr | 6 | $\psi_\star\approx2800$ $M_\odot$ yr$^{-1}$ |
| Dense gas line width sigma | 289 | 48 | km/s | 7 | $\sigma_{\rm dense}=(289\pm48)$ km s$^{-1}$ |

## Qualitative findings

- CN(4-3)/HNC blend is compact (~80% unresolved, <360 pc) and much broader than the ring, possibly a dense molecular outflow or SF-driven wind  
  > "with approximately 80% of the integrated flux unresolved, corresponding to emission on scales below 360 pc" (4.2 A possible dense molecular outflow)

## Claim tuples

- H: Is the molecular gas arranged in a resolved rotating ring? | E: Lens-model source-plane reconstruction and galpak3d fit of CO(4-3) | R: Ring Rmax~2.6 kpc, Vmax=360 km/s, i=50 deg | F: A 2.5 kpc radius molecular ring is resolved | **supported**
- H: Is there a dynamically distinct dense gas component near the AGN? | E: Fit HNC/CN blend line width | R: FWHM ~680 km/s, ~2x ring rotation speed | F: Possible dense outflow/interaction with AGN, but not unambiguous | **partially**
- H: Can AGN feedback quench star formation in the ring? | E: Compare M_H2 with SFR | R: Depletion time ~10s Myr | F: Feedback unlikely to curtail stellar mass assembly in ring | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Fixing HNC/CN width to ring dispersion 73 km/s gives no sensible fit  
  > "does not result in a sensible fit to the data" (4.2 A possible dense molecular outflow)
- How they decided it was enough: _not stated_
- Limitation (authors): Deblending of HNC/CN depends strongly on redshift; outflow rate cannot be estimated; limited tracers  
  > "deeper observations will be required to properly model the complex" (4.2 A possible dense molecular outflow)
- Caveat (inferred, ours): Gas mass relies on assumed X_CI and Q10 with no uncertainty on them
- Caveat (inferred, ours): SFR relies on assumed epsilon and f_d/t
- Caveat (inferred, ours): Outflow interpretation rests on a blended line with redshift-dependent decomposition
- Caveat (inferred, ours): Lens model uncertainties not propagated into ring parameters

## Reproducibility

- Data public (paper): ALMA project data cited; public status not stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2017.1.00814.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Lens model code (Dye et al. 2018) settings and priors
- Missing: Modified galpak3d code
- Missing: Cell/image size, line-free channels
- Missing: Fit details for CN/HNC blend
- Data volume (inferred): ~50-100 GB raw for two EBs
- Score (inferred): 5/5, Data identified and imaging basics given, but lens modelling and several fit settings are underspecified.
- Rediscovery candidate: no, Key results depend on a bespoke lens model and modified code with unstated settings.

## Links

- Method: Bouché et al. 2015 (galpak3d code)
- Method: Dye et al. 2018 (Voronoi source-plane lens inversion)
- Method: Suyu et al. 2006 (Bayesian evidence/MCMC lens optimisation)
- Companion: Geach et al. 2015 (Discovery and earlier lens model of 9io9)
- Companion: Harrington et al. 2016 (Earlier redshift measurement)
- Companion: Rivera et al. 2018 (CO(3-2) analysis of 9io9)
- Related: SpaceWarps

## Checks

```json
{
 "quotes": 75,
 "quotes_ok": 75,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 13,
 "numeric_problems": 0,
 "fill": {
  "facts": 81,
  "stated": 49,
  "rate": 0.605
 },
 "evidence_ok": true
}
```
