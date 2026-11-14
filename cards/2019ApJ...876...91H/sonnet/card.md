# Molecular Gas Properties in the Host Galaxy of GRB 080207

`2019ApJ...876...91H` | The Astrophysical Journal 2019 | first author: Hatsukade, Bunyo | arXiv: 1904.02292 | DOI: 10.3847/1538-4357/ab1649

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies, star_formation
- Question: What are the molecular gas mass, dust properties, kinematics and CO excitation of the GRB 080207 host galaxy, and do they match normal star-forming galaxies at z~2?  
  > "Comparison of molecular gas properties between the host and normal (main-sequence) galaxies at similar redshifts shows that they share common properties" (abstract)
- Target **GRB 080207 host galaxy**: coordinates _not stated_; z/distance z = 2.0858 ± 0.0003  
  > "host galaxy of a long-duration gamma-ray burst GRB 080207 at $z = 2.0858$" (abstract); "The redshift of $z = 2.0858 \pm 0.0003$ is determined from the emission line in from the host galaxy (cite: kruh12)." (2 The Host Galaxy of GRB 080207); distance from emission line of host (Krühler et al. 2012)  
  > "host galaxy of a long-duration gamma-ray burst GRB 080207 at $z = 2.0858$" (abstract); "The redshift of $z = 2.0858 \pm 0.0003$ is determined from the emission line in from the host galaxy (cite: kruh12)." (2 The Host Galaxy of GRB 080207)

## Data provenance

- ALMA projects: 2015.1.00939.S
- bands: ALMA Band 4 (2.1 mm); VLA Ka-band  
  > "The redshifted CO(4–3) line was observed with Band 4." (3.2 ALMA CO(4–3))
- frequencies and spectral setup: 1875 MHz per baseband (488.28 kHz x 3840 channels), four basebands, 7.5 GHz total  
  > "The correlator was used in the time domain mode with a bandwidth of 1875 MHz (488.28 kHz $\times$ 3840 channels)." (3.2 ALMA CO(4–3))
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: C36-2/3  
  > "The array configuration was C36-2/3 with the baseline lengths of 15.1–640.0 m." (3.2 ALMA CO(4–3))
- baselines: 15.1–640.0 m  
  > "The array configuration was C36-2/3 with the baseline lengths of 15.1–640.0 m." (3.2 ALMA CO(4–3))
- angular resolution: 0.90'' x 0.83'' (CO map); 1.21'' x 1.03'' (continuum)  
  > "The synthesized beamsize is $0.90\ensuremath{''} \times 0.83\ensuremath{''}$ (PA $= -1.0^{\circ}$) for a velocity-integrated CO map" (3.2 ALMA CO(4–3))
- max recoverable scale: _not stated_
- sensitivity: 12.9 µJy/beam continuum; 0.42 mJy/beam per 20 km/s channel  
  > "The rms noise level is 12.9 $\mu$Jy beam$^{-1}$ for the continuum map, and 0.42 mJy beam$^{-1}$ for a spectra with a velocity resolution of 20 km s$^{-1}$." (3.2 ALMA CO(4–3))
- time on source: 41 min (ALMA); 3.7 h (VLA)  
  > "the on-source integration time is 41 min" (3.2 ALMA CO(4–3))
- observing dates: 2016 Apr 29 (ALMA); 2018 Nov 11–16 (VLA)  
  > "ALMA observations were conducted in Apr. 29, 2016" (3.2 ALMA CO(4–3))
- pi or archival as stated: _not stated_
- Line: CO 4–3 (not stated)
- Line: CO 1–0 (VLA) (observed at 37.355 GHz)
- Other facility **VLA**: CO(1–0) and 0.81 cm continuum  
  > "The VLA Ka-band observations (Project ID: 18A-103) were performed on Nov. 11–16, 2018 using 26 antennas." (3.1 VLA CO(1–0))
- Other facility **HST/WFC3**: F110W image for overlay  
  > "overlaid on the image of *HST*/Wide Field Camera-3 (WFC3) with the F110W filter" (3.3 Results)
- External data: SED-fit M* = 1.7e11 Msun, SFR = 1.2e2 Msun/yr, and ALMA Band 8/9 photometry (480, 650 µm)  
  > "We adopt the results of SED fitting ($M_* = 1.7 \times 10^{11}$ $M_{\odot}$ and SFR $= 1.2 \times 10^2$ $M_{\odot}$ yr$^{-1}$) by T. Hashimoto et al. (in prep.)" (4.1 Molecular Gas Mass) [from T. Hashimoto et al. (in prep.)]
- External data: Herschel/PACS 160 µm photometry  
  > "we fit a modified black body to the photometry at 160 $\mu$m obtained with *Herschel*/PACS (cite: hunt14)" (4.2 Dust Properties) [from (cite: hunt14)]
- External data: Host metallicity 12+log(O/H) = 8.74 ± 0.15  
  > "The metallicity of the host galaxy is $12 + \log{\rm (O/H)} = 8.74 \pm 0.15$ (cite: kruh15)" (2 The Host Galaxy of GRB 080207) [from (cite: kruh15)]
- External data: CO(2–1) and CO(3–2) line fluxes for line ratios  
  > "the GRB 080207 host was detected with CO(2–1) and CO(3–2) in (cite: mich18) and (cite: arab15)" (4.5 CO Line Ratios) [from (cite: mich18); (cite: arab18)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Titan (ALMA); 3C286 (VLA)  
  > "Bandpass, flux, and phase calibrations were done with J1256$-$0547, Titan, and J1347+1217, respectively." (3.2 ALMA CO(4–3))
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA tclean  
  > "The data were reduced with CASA, and maps were processed with a `tclean` task." (3.2 ALMA CO(4–3))
- deconvolver: _not stated_
- weighting robust: Briggs robust = 0.5 for CO maps; natural for continuum  
  > "While Briggs weighting with `robust` parameter of 0.5 was adopted for CO maps, natural weighting was adopted for a continuum map to maximize the sensitivity." (3.2 ALMA CO(4–3))
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: Clean boxes where peak S/N>5; cleaned to 2σ  
  > "Clean boxes were placed when a component with a peak signal-to-noise ratio (S/N) above 5 is identified, and `CLEAN`ed down to a $2\sigma$ level." (3.2 ALMA CO(4–3))
- multiscale scales: _not stated_
- continuum subtraction: Continuum map from ~7.5 GHz excluding line channels  
  > "The continuum map was created with a total bandwidth of $\sim$7.5 GHz, excluding channels with emission line." (3.2 ALMA CO(4–3))
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.90'' x 0.83'' CO; 1.21'' x 1.03'' continuum  
  > "and $1.21\ensuremath{''} \times 1.03\ensuremath{''}$ (PA $= -32^{\circ}$) for the continuum map" (3.2 ALMA CO(4–3))
- final rms: 12.9 µJy/beam continuum  
  > "The rms noise level is 12.9 $\mu$Jy beam$^{-1}$ for the continuum map" (3.2 ALMA CO(4–3))

### Inherited from earlier work

- CO-to-H2 conversion factor vs metallicity relation  
  > "We adopt the relation between metallicity and $\alpha_{\rm CO}$ of (cite: genz12) and (cite: genz15)" (4.1 Molecular Gas Mass) [from (cite: genz12); (cite: genz15)]
- Dust mass formalism  
  > "we derived the FIR luminosity ($L_{\rm FIR}$) and dust mass ($M_{\rm dust}$) following (cite: debr03)" (4.2 Dust Properties) [from (cite: debr03)]
- Systematic error of ~10% in GalPaK3D parameters from imaging  
  > "Note that the output parameters have systematic errors of $\sim$10% for different imaging parameters (cite: tada19)." (4.3 Kinematics) [from (cite: tada19)]

### Not stated but needed to reproduce (our reading)

- ALMA calibration software version and CASA version
- Line-free channels and channel width/cell/image size used in tclean
- GalPaK3D settings (PSF/LSF, priors, initial guesses, cube preparation)
- Hashimoto et al. ALMA Band 8/9 photometry values
- Method to convert metallicity and exact alpha_CO calculation
- Self-calibration not mentioned

## Analysis recipe

1. **image CO(4–3) and continuum**: CASA tclean with Briggs robust 0.5 (CO) and natural (continuum); imfit for 2D Gaussian size and flux  
  > "While Briggs weighting with `robust` parameter of 0.5 was adopted for CO maps, natural weighting was adopted for a continuum map to maximize the sensitivity." (3.2 ALMA CO(4–3))
   - software: CASA
   - parameter: Line integrated over −200 to +400 km/s  
  > "Velocity-integrated CO intensity derived by integrating the velocity from $-200$ to $+400$ km s$^{-1}$." (Table 1)
   - fitting: 2D Gaussian with imfit  
  > "Derived from 2D Gaussian fit with CASA imfit." (Table 1)
   - validation: Positive vs negative peak counts for CO(1–0) spurious detection (10 vs 1 above S/N 3.6)  
  > "The number of positive and negative peaks with S/N above 3.6 is 10 and 1, respectively" (3.3 Results)
2. **molecular gas mass**: L'CO from Solomon & Vanden Bout formula; Mgas = alpha_CO L'CO(1-0)  
  > "The molecular gas mass is derived from $$\begin{eqnarray} M_{\rm gas} = \alpha_{\rm CO} L'_{\rm CO(1-0)}, \end{eqnarray}$$" (4.1 Molecular Gas Mass)
   - parameter: alpha_CO = 5.1 Msun (K km/s pc^2)^-1  
  > "The metallicity of the host galaxy corresponds to a metallicity-dependent conversion factor of $\alpha_{\rm CO} = 5.1$ $M_{\odot}$ (K km s$^{-1}$ pc$^2$)$^{-1}$." (4.1 Molecular Gas Mass)
   - assumption: Cosmology H0=70, OmegaM=0.3, OmegaL=0.7; metallicity-dependent alpha_CO including helium  
  > "we adopt a cosmology with $H_0=70$ km s$^{-1}$ Mpc$^{-1}$, $\Omega_{\rm{M}}=0.3$, and $\Omega_{\Lambda}=0.7$" (1 Introduction)
   - fitting: _not stated_
   - validation: _not stated_
3. **dust SED fit**: Modified blackbody fit to 160 µm, 480, 650 µm, 2.1 mm photometry  
  > "The best-fit values are $T_{\rm dust} = 37 \pm 4$ K and $\beta = 1.5 \pm 0.3$." (4.2 Dust Properties)
   - assumption: kappa_d(125 µm) = 2.64 ± 0.29 m^2/kg, kappa ∝ nu^beta  
  > "adopt $\kappa_d(125\ \mu m) = 2.64 \pm 0.29$ m$^2$ kg$^{-1}$ (cite: dunn03)" (4.2 Dust Properties)
   - fitting: _not stated_
   - validation: SFR from L_FIR consistent with SED fitting result  
  > "The SFR is consistent with the results of SED fitting by Hashimoto et al. (in prep.)." (4.2 Dust Properties)
4. **kinematic modelling**: Fit CO(4–3) cube with GalPaK3D disk model (exponential flux profile, arctangent rotation curve, thick disk dispersion)  
  > "We adopt a disk model object with exponential flux profile, arctangent rotation profile, and thick disk dispersion." (4.3 Kinematics)
   - software: GalPaK3D
   - parameter: 10 free parameters  
  > "The algorithm directly compares data-cubes with a disk parametric model with 10 free parameters" (4.3 Kinematics)
   - fitting: MCMC; uncertainty is 95% interval from last 60% of 15000 iterations  
  > "The uncertainty is the 95% confidence interval calculated from the last 60% of the MCMC chain for 15000 iterations." (4.3 Kinematics)
   - validation: reduced chi2 = 1.12  
  > "The procedure of model fitting converged with a reduced-$\chi^2$ of 1.12." (4.3 Kinematics)
5. **CO line ratios and comparison**: Brightness temperature ratios from CO(1–0), (2–1), (3–2), (4–3); compare with SLEDs and scaling relations  
  > "The derived brightness temperature line ratios are summarized in Table [2](#tab:line_ratio)." (4.5 CO Line Ratios)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : data reduction, tclean imaging, imfit  
  > "The data were reduced with Common Astronomy Software Applications (cite: mcmu07)." (3.1 VLA CO(1–0))
- **GalPaK3D** : 3D kinematic disk modelling of CO(4–3) cube  
  > "we fit the spatially resolved CO(4–3) data with GalPaK$^{\rm 3D}$ (cite: bouc15)" (4.3 Kinematics)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| CO(4–3) velocity-integrated flux | 1.1 | 0.1 | Jy km/s | 1 | $1.1 \pm 0.1$$^\dagger$ |
| L'CO(4–3) | 1.5e10 | 0.1e10 | K km/s pc^2 | 1 | $L'_{\rm CO}$(4–3) $= (1.5 \pm 0.1) \times 10^{10}$ (K km s$^{-1}$ pc$^2$) |
| L'CO(1–0) | 1.7e10 | 0.5e10 | K km/s pc^2 | 1 | $L'_{\rm CO}$(1–0) $= (1.7 \pm 0.5) \times 10^{10}$ (K km s$^{-1}$ pc$^2$) |
| 2.1 mm continuum flux | 120 | 20 | µJy | 1 | $S_{\rm 2.1mm} = 120 \pm 20$ $\mu$Jy |
| Molecular gas mass | 8.7e10 | 2.4e10 | Msun | 2 | $M_{\rm gas} = (8.7 \pm 2.4) \times 10^{10}$ $M_{\odot}$ |
| Gas mass fraction | 0.34 | not stated | dimensionless | 2 | is 0.34, which is comparable to those of $z \sim 1$–2 MS galaxies |
| Gas depletion time | 0.71 | not stated | Gyr | 2 | are estimate to be 1.4 Gyr$^{-1}$ and 0.71 Gyr, respectively |
| Dust temperature | 37 | 4 | K | 3 | $T_{\rm dust} = 37 \pm 4$ K and $\beta = 1.5 \pm 0.3$ |
| Dust mass | 1.5e8 | not stated | Msun | 3 | $M_{\rm dust} = 1.5 \times 10^8$ $M_{\odot}$ and $L_{\rm FIR} = 1.4 \times 10^{12}$ $L_{\odot}$ |
| Gas-to-dust ratio | 560 | not stated | dimensionless | 3 | $M_{\rm gas}/M_{\rm dust} \sim 560$ |
| CO half-light radius | 2.39 | +0.15/-0.14 (95%) | kpc | 4 | $R_{\rm 1/2,CO}$ (kpc)       / $2.39_{-0.14}^{+0.15}$ |
| Rotation velocity | 347.59 | +2.25/-8.08 (95%) | km/s | 4 | $347.59_{-8.08}^{+2.25}$ |
| Velocity dispersion | 63.44 | +8.38/-5.95 (95%) | km/s | 4 | $63.44_{-5.95}^{+8.38}$ |
| Inclination | 38.74 | +1.34/-1.41 (95%) | deg | 4 | $38.74_{-1.41}^{+1.34}$ |
| r43 | 0.90 | 0.26 | dimensionless | 5 | $r_{43}$         / $0.90 \pm 0.26$ |

## Qualitative findings

- CO SLED similar to starburst galaxies, indicating high excitation  
  > "The CO spectral line energy distribution derived from the four CO transitions is similar to that of starburst galaxies, suggesting a high excitation condition." (abstract)

## Claim tuples

- H: Does the host's molecular gas content resemble normal star-forming galaxies? | E: CO(1–0)-based gas mass with metallicity-dependent alpha_CO compared with MS galaxies | R: Mgas = 8.7e10 Msun, fgas 0.34, tdepl 0.71 Gyr | F: Host lies on the normal star-forming sequence | **supported**
- H: Is the host kinematically a rotating disk? | E: GalPaK3D fit to CO(4–3) cube | R: vrot 348 km/s, R1/2 2.4 kpc, vrot/sigma 5.5 | F: Rotation-dominated disk like MS galaxies | **supported**
- H: Is the CO excitation of the host high? | E: Line ratios from four CO transitions | R: ratios close to unity up to J=4 | F: High excitation like starbursts | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Galactic alpha_CO = 4.3 would lower gas mass by factor 1.2  
  > "a derived molecular gas mass would be smaller by a factor of 1.2" (4.1 Molecular Gas Mass)
- How they decided it was enough: _not stated_
- Limitation (authors): CO(1–0) detection significance is low (peak S/N 3.65)  
  > "Since the significance for the CO(1–0) is not high" (3.3 Results)
- Limitation (authors): Only one CO-detected GRB host at z>1; sample limited  
  > "Currently the sample of GRB host galaxies with CO detection is limited and only one host galaxy is detected at $z > 1$." (4.6 Implication)
- Caveat (inferred, ours): Single object; conclusion about GRBs in normal environments cannot be generalized
- Caveat (inferred, ours): CO(1–0) S/N of 3.65 makes r21 and gas mass uncertain
- Caveat (inferred, ours): Heavy dependence on unpublished SED results (Hashimoto et al. in prep.)
- Caveat (inferred, ours): alpha_CO choice dominates gas mass uncertainty

## Reproducibility

- Data public (paper): ALMA project code printed; public status not stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2015.1.00939.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Hashimoto et al. photometry and SED results
- Missing: GalPaK3D configuration details
- Missing: CASA version and line-free channels
- Missing: VLA data (project 18A-103) availability
- Data volume (inferred): ~10-30 GB for the single ALMA Band 4 execution (plus VLA)
- Score (inferred): 5/5, Data and main steps stated and code public, but imaging details and external in-prep inputs are missing.
- Rediscovery candidate: no, Key inputs (Hashimoto SED results, VLA data) are unpublished and GalPaK setup is incomplete, though ALMA data are archival.

## Links

- Method: Bouché et al. 2015 (cite: bouc15) (GalPaK3D code)
- Method: Tadaki et al. 2019 (cite: tada19) (systematic errors of GalPaK3D parameters)
- Companion: Arabsalmani et al. 2018 (cite: arab18) (CO(3–2) detection of same host)
- Companion: Michałowski et al. 2018 (cite: mich18) (CO(2–1) detection of same host)
- Related: ALMA CO search toward long-duration GRB hosts (B. Hatsukade et al. in prep.)

## Checks

```json
{
 "quotes": 73,
 "quotes_ok": 73,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 15,
 "numeric_problems": 0,
 "fill": {
  "facts": 78,
  "stated": 49,
  "rate": 0.628
 },
 "evidence_ok": true
}
```
