# The Link between Turbulence, Magnetic Fields, Filaments, and Star Formation in the Central Molecular Zone Cloud G0.253+0.016

`2016ApJ...832..143F` | The Astrophysical Journal 2016 | first author: Federrath, C. | arXiv: 1609.05911 | DOI: 10.3847/0004-637X/832/2/143

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: milky_way_ism, star_formation
- Question: What are the turbulence, magnetic field, filament structure and turbulence driving mode of the CMZ cloud G0.253+0.016, and how do they affect its star formation rate?  
  > "Here we determine the physical parameters of the central molecular zone (CMZ) cloud G0.253+0.016, its turbulence, magnetic field and filamentary structure." (abstract)
- Target **G0.253+0.016 (the 'Brick')**: coordinates _not stated_; z/distance 8.3 (0.3) kpc  
  > "assuming a distance of $8.3\,(0.3)\,\mathrm{k}\mathrm{pc}$ (cite: Malkin2013; ZhuShen2013; ReidEtAl2014)" (Table 1 notes); distance from Malkin2013; ZhuShen2013; ReidEtAl2014  
  > "assuming a distance of $8.3\,(0.3)\,\mathrm{k}\mathrm{pc}$ (cite: Malkin2013; ZhuShen2013; ReidEtAl2014)" (Table 1 notes)

## Data provenance

- ALMA projects: 2011.0.00217.S
- bands: 3 mm (90 GHz), Cycle 0  
  > "mosaic of the 3 mm (90 GHz) dust continuum and molecular line emission across G0.253+0.016" (2 Observational data)
- frequencies and spectral setup: four spectral windows centered at 87.2, 89.1, 99.1, 101.1 GHz, 1875 MHz bandwidth each, 488 kHz channels  
  > "four spectral windows in dual polarization mode centered at 87.2, 89.1, 99.1, and 101.1 GHz, each with 1875 MHz bandwidth and 488 kHz ($1.4$–$1.7\,\mathrm{km}\,\mathrm{s}^{-1}$) velocity channel spacing" (2 Observational data)
- continuum bandwidth: _not stated_
- arrays: 25 antennas  
  > "using 25 antennas as part of ALMA’s Early Science Cycle 0" (2 Observational data)
- configurations: _not stated_
- baselines: 13–455 m projected  
  > "The interferometer used projected baselines in the range $13$–$455\,\mathrm{m}$." (2 Observational data)
- angular resolution: 1.7 arcsec (~0.07 pc) in column density map  
  > "an angular resolution of $1.7''$ ($\mathrm{FWHW}\sim0.07\,\mathrm{pc}$)" (2.1)
- max recoverable scale: _not stated_
- sensitivity: 10 sigma ~0.25 mJy/beam; HNCO ~1 mJy/beam per 3.4 km/s channel  
  > "The HNCO line brightness sensitivity is $\sim1\,\mathrm{mJy}\,\mathrm{beam}^{-1}$ per $3.4\,\mathrm{km}\,\mathrm{s}^{-1}$ channel." (2.2)
- time on source: _not stated_
- observing dates: six occasions, July 29 to August 1, 2012  
  > "The G0.253+0.016 cloud was imaged on six occasions between July 29 and August 1 in 2012." (2 Observational data)
- pi or archival as stated: _not stated_
- Line: HNCO not stated (not stated)
- Other facility **Herschel**: Single-dish dust emission to recover large scales; pure Herschel column density map (70-500 micron Hi-GAL)  
  > "The ALMA dust continuum data were complemented with single-dish data from the *Herschel* space observatory to recover the large-scale component of the dust emission." (2.1)
- Other facility **Mopra**: Single-dish data combined with ALMA for HNCO maps (named in abstract)  
  > "HNCO intensity-weighted velocity maps obtained with ALMA+Mopra" (abstract)
- External data: ALMA+Herschel column density map, log-normal column density PDF (N0=9e22, sigma_eta=0.34)  
  > "They find an average column density of $N_0=(9\pm2)\times10^{22}\,\mbox{cm}^{-2}$ and a logarithmic column density dispersion of $\sigma_\eta = 0.34\pm0.02$" (3.1.2) [from (cite: RathborneEtAl2014)]
- External data: Herschel-only column density map  
  > "we also use the *Herschel*-only column density map published in (cite: LongmoreEtAl2012)" (2.1) [from (cite: LongmoreEtAl2012)]
- External data: HNCO data cubes  
  > "Here we use the HNCO line emission of G0.253+0.016 by (cite: RathborneEtAl2015)" (3.2) [from (cite: RathborneEtAl2015)]
- External data: Ordered magnetic field B_tot = 5.4 mG and polarization angle dispersion 9.3 deg, adjusted to 2.2 mG  
  > "find a total magnetic field strength of $B_\mathrm{tot}=5.4\pm0.5\,\mathrm{m}\mbox{G}$" (3.3) [from (cite: PillaiEtAl2015)]
- External data: Gas temperature T=100(50) K  
  > "Gas temperature | $T$ | $100\,(50)\,\mathrm{K}$" (Table 1) [from (cite: LisEtAl2001; MillsMorris2013; AoEtAl2013; BallyEtAl2014; GinsburgEtAl2016)]
- Simulation/model as data: 8 MHD turbulence simulations (256^3, B0=1000/2000/3000 microG, two seeds, one 512^3, one compressive) to derive B_turb  
  > "We initialize three different values for the ordered magnetic field, $B_0=1000$, $2000$, and $3000\,\mu\mbox{G}$" (3.3)

## Processing

### Calibration

- pipeline or manual: each data set independently calibrated before merging; CASA and Miriad  
  > "Each data set was independently calibrated before being merged. All data reduction was performed using CASA (cite: casa) and Miriad (cite: Miriad)." (2 Observational data)
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
- image size: column density pixel size 0.35 arcsec  
  > "The final column density image has a pixel size of $0.35''$" (2.1)
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: ALMA combined with Herschel (500 micron scaled to 3 mm, graybody beta=1.2, Tdust=20 K)  
  > "global spectral index $\beta_\mathrm{SED}=1.2\pm0.1$ and a global dust temperature $T_\mathrm{dust}=20\pm1\,\mathrm{K}$" (7.1)
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Conversion of dust emission to column density and ALMA+Herschel combination  
  > "converted to gas column densities with the techniques and assumptions explained in detail in (cite: RathborneEtAl2014)" (2.1) [from (cite: RathborneEtAl2014)]
- Filament profile procedure  
  > "The procedure is similar to that applied in previous studies (cite: ArzoumanianEtAl2011; Federrath2016)." (3.1.1) [from (cite: ArzoumanianEtAl2011; Federrath2016)]
- 2D-to-3D density dispersion method  
  > "Here we apply the technique by (cite: BruntFederrathPrice2010a) in order to reconstruct the 3D density dispersion of G0.253+0.016." (3.1.2) [from (cite: BruntFederrathPrice2010a)]
- MHD simulation methods  
  > "running magnetohydrodynamical turbulence simulations following the methods in (cite: FederrathDuvalKlessenSchmidtMacLow2010; FederrathEtAl2011PRL)" (3.3) [from (cite: FederrathDuvalKlessenSchmidtMacLow2010; FederrathEtAl2011PRL)]
- SFR theory and parameters phi_x, 1/phi_t  
  > "best-fit theory parameter $\phi_x=0.17\pm0.02$ (cite: FederrathKlessen2012)" (6.2) [from (cite: FederrathKlessen2012)]

### Not stated but needed to reproduce (our reading)

- Exact CASA version and calibration/imaging parameters (all inherited from Rathborne et al.)
- Archive project/member IDs and flux calibrators
- Mopra/ALMA combination details for HNCO
- Plane-fit method and masks for the velocity gradient
- Fit ranges, binning and optimizer for filament profile fits
- Simulation code setup details (FLASH version, driving parameters, Mach number)
- Number and location of filament pixels used

## Analysis recipe

1. **identify filaments**: DisPerSE on ALMA+Herschel column density map  
  > "These filaments were identified with the DisPerSE algorithm (cite: Sousbie2011; SousbieEtAl2011)" (3.1)
   - software: DisPerSE
   - parameter: persistence threshold 5e22 cm^-2 (10 sigma); min 5 pixels per filament; -cut 4.75e22, smooth 6, assemble 70  
  > "We further enforced a minimum number of 5 pixels per filament." (footnote 4)
   - fitting: _not stated_
   - validation: Varying threshold by factor of two did not change filaments or properties  
  > "Decreasing or increasing the threshold by a factor of two neither significantly affects the number of identified filaments nor their average properties." (3.1)
2. **measure filament width**: Radial column density profiles fitted with Gaussian and Plummer profiles, beam deconvolved  
  > "we apply two fits, one with a Gaussian profile, the other with a Plummer profile." (3.1.1)
   - parameter: Sigma_offset = 1e23 cm^-2; W_fil = 2.355 sigma_Gauss; W_fil ~ 3 R_flat for p=2  
  > "The constant column density offset $\Sigma_\mathrm{offset}=1\times10^{23}\,\mbox{cm}^{-2}$ was chosen" (3.1.1)
   - assumption: Width uncertainty from projection: factor 2 (Smith et al. 2014)  
  > "showing that the average intrinsic 3D filament width can be up to 50% smaller than the average projected (2D) filament width" (3.1.1)
   - fitting: Gaussian and Plummer fits to average profile; also each of 11 filaments  
  > "we have also fitted each of the 11 individual filaments" (3.1.1)
   - validation: Fourier deconvolution and beam-in-fit agree; analytic deconvolution 0.17 pc  
  > "Both techniques yield consistent results." (3.1.1)
3. **reconstruct 3D density dispersion**: Brunt et al. method: ratio of 2D to 3D power spectra of N/N0-1 with mirrored map; sigma_N/N0 from log-normal fit  
  > "Here we apply mirroring of the column density map to generate a periodic dataset" (3.1.2)
   - parameter: Fourier anisotropy axis ratio 1.4; error <40%  
  > "The maximum major-to-minor axis ratio is $1.4$" (3.1.2)
   - assumption: isotropy  
  > "assuming isotropy of the clouds" (3.1.2)
   - fitting: _not stated_
   - validation: consistent with R^1/2 = 0.27 from simulations  
  > "consistent with the average dispersion ratio of $0.27\pm0.05$ obtained from numerical simulations" (3.1.2)
4. **measure turbulent velocity dispersion**: Fit plane to HNCO centroid velocity map, subtract, compute velocity PDFs and Gaussian fit  
  > "we fit the gradient with a plane, shown in the middle panel, and then subtract it from the original velocity map" (3.2.1)
   - fitting: Gaussian fit to PDF; also standard deviation  
  > "the Gaussian fit in Figure [4](#fig:velocities) and the standard deviation of the velocity data (without fitting) yield a consistent 1D *turbulent* velocity dispersion" (3.2.2)
   - validation: Gaussian fit and direct standard deviation agree  
  > "the Gaussian fit in Figure 4 and the standard deviation of the velocity data (without fitting) yield a consistent 1D *turbulent* velocity dispersion" (3.2.2 Velocity PDF)
5. **derive turbulent magnetic field**: MHD turbulence simulations with measured velocity dispersion and ordered field, time- and simulation-averaged B_turb  
  > "We determine the time- and simulation-averaged value and find $B_\mathrm{turb}=130\pm50\,\mu\mbox{G}$" (3.3)
   - software: FLASH
   - parameter: B0 = 1000, 2000, 3000 microG; 256^3 grid; two seeds; solenoidal driving  
  > "All simulations use a resolution of $256^3$ grid points and purely solenoidal driving of the turbulence" (3.3)
   - assumption: relative uncertainty same as B_tot (40%); corrected n=1.3e4 cm^-3  
  > "where we have assumed the same relative uncertainty as in $B_\mathrm{tot}$ from the observations, i.e., 40%" (3.3)
   - fitting: _not stated_
   - validation: Re-ran with 512^3 and compressive driving; no significant difference  
  > "We find no significant difference in $B_\mathrm{turb}$ for either resolution or different driving of the turbulence." (3.3)
6. **derive physical parameters, sonic scale, driving parameter and SFR**: Analytic relations (Table 1): lambda_sonic = L M^-2 (1+1/beta); b = sigma_rho M^-1 (1+1/beta)^1/2; Federrath & Klessen 2012 SFR model  
  > "$b=\sigma_{\rho/\rho_0}\mathcal{M}^{-1}(1+\beta^{-1})^{1/2}=0.22\pm0.12$" (6)
   - parameter: mu_mol=2.8, mu_p=2.33, T=100 K, distance 8.3 kpc, epsilon=0.5, phi_x=0.17, 1/phi_t=0.46  
  > "core-to-star efficiency $\epsilon=0.5$ (cite: FederrathEtAl2014)" (6.2)
   - assumption: isothermal turbulence  
  > "both rest on the assumption of isothermal turbulence, i.e., gas at constant temperature" (7.4)
   - fitting: Uncertainties propagated from each independent parameter  
  > "All uncertainties were propagated based on each independent parameter." (Table 1 notes)
   - validation: SFR compared to b=0.5 case  
  > "predicts $\mathrm{SFR}=7.6\times10^{-2}\,\mbox{$M_{\ensuremath{\odot}}$}\,\mathrm{yr}^{-1}$ if a turbulence driving parameter $b=0.5$ is used" (6.2)

## Software

- **CASA** : data reduction  
  > "All data reduction was performed using CASA (cite: casa) and Miriad (cite: Miriad)." (2 Observational data)
- **Miriad** : data reduction  
  > "All data reduction was performed using CASA (cite: casa) and Miriad (cite: Miriad)." (2 Observational data)
- **DisPerSE** : filament identification  
  > "These filaments were identified with the DisPerSE algorithm" (3.1)
- **FLASH** : MHD turbulence simulations  
  > "The simulation software FLASH used in this work was in part developed by the DOE-supported Flash Center" (Acknowledgments)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Filament width | 0.17 | 0.08 | pc | 2 | We measure the filament width $W_\mathrm{fil}=0.17\pm0.08\,\mathrm{pc}$ |
| Plummer exponent p | 2.1 | 1.0 | dimensionless | 2 | Here we find $p=2.1\pm1.0$ for G0.253+0.016 |
| Sonic scale | 0.15 | 0.11 | pc | 6 | the sonic scale $\lambda_\mathrm{sonic}=0.15\pm0.11\,\mathrm{pc}$ |
| Total 1D velocity dispersion | 8.8 | 0.2 | km/s | 4 | $8.8\pm0.2\,\mathrm{km}\,\mathrm{s}^{-1}$ and $3.9\pm0.1\,\mathrm{km}\,\mathrm{s}^{-1}$ |
| Turbulent 1D velocity dispersion | 3.9 | 0.1 | km/s | 4 | $\sigma_{v,\mathrm{1D}}=3.9\pm0.1\,\mathrm{km}\,\mathrm{s}^{-1}$ |
| 2D-to-3D ratio R^1/2 | 0.28 | 0.11 | dimensionless | 3 | we find $\mathcal{R}^{1/2}=0.28\pm0.11$ |
| 3D density dispersion | 1.3 | 0.5 | dimensionless | 3 | $\sigma_{\rho/\rho_0}=1.3\pm0.5$ |
| Turbulent magnetic field | 130 | 50 | microG | 5 | $B_\mathrm{turb}=130\pm50\,\mu\mbox{G}$ |
| Driving parameter b | 0.22 | 0.12 | dimensionless | 6 | $b=\sigma_{\rho/\rho_0}\mathcal{M}^{-1}(1+\beta^{-1})^{1/2}=0.22\pm0.12$ |
| Cloud mass | 7.2e4 | 3.8e4 | Msun | 6 | $7.2\,(3.8)\times10^4\,\mbox{$M_{\ensuremath{\odot}}$}$ |
| 3D sonic Mach number | 11 | 3 | dimensionless | 6 | 3D turbulent sonic Mach number / $\mathcal{M}=\sigma_{v,\mathrm{3D}}/c_\mathrm{s}$ / $11\,(3)$ |
| Plasma beta | 0.34 | 0.35 | dimensionless | 6 | Turbulent plasma beta / $\beta=2\,c_\mathrm{s}^2/v_\mathrm{A}^2$ / $0.34\,(0.35)$ |
| Star formation rate | 1.1e-2 | 0.8e-2 | Msun/yr | 6 | $(1.1\pm0.8)\times10^{-2}\,\mbox{$M_{\ensuremath{\odot}}$}\,\mathrm{yr}^{-1}$ |
| SFR reduction factor vs b=0.5 | 6.9 | not stated | dimensionless | 6 | this is a factor of $6.9$ higher than what we derived |

## Qualitative findings

- Dense core candidates lie along filaments; filaments show no preferred orientation relative to the large-scale magnetic field  
  > "We do not find that the filaments have a preferred orientation with respect to the large-scale magnetic field." (3.1)

## Claim tuples

- H: Filament width equals the sonic scale in the CMZ cloud | E: Fit filament profiles; compute sonic scale from measured parameters | R: W_fil=0.17±0.08 pc vs lambda_sonic=0.15±0.11 pc | F: Sonic scale may control filament width in CMZ as in nearby clouds | **supported**
- H: Turbulence in G0.253+0.016 is driven differently than spiral-arm clouds | E: Combine density dispersion, Mach number and plasma beta | R: b=0.22±0.12 | F: Solenoidal driving, likely by shear | **supported**
- H: Solenoidal driving reduces the SFR | E: Federrath & Klessen SFR model with b=0.22 vs 0.5 | R: SFR lower by factor 6.9 | F: Driving mode is critical for the low SFR | **partially**
- H: Turbulent field is small relative to ordered field | E: MHD simulations | R: B_turb=130±50 microG, ≲1/10 of B_tot | F: Ordered field dominates | **supported**

## Reasoning

- Why this data: HNCO gives best correlation with dust and good coverage  
  > "The HNCO line measurements from (cite: RathborneEtAl2015) provide the best available correlation with the ALMA dust emission" (3.2)
- Why this method: _not stated_
- Alternative: Hydrostatic filaments (p=4) ruled out by observed p≈2  
  > "which gives significantly steeper profiles, $p=4$, ruled out by our observations of G0.253+0.016" (3.1.1)
- How they decided it was enough: _not stated_
- Limitation (authors): Column density absolute calibration uncertain by factor 2; poor local dust-line correlation; projection effects on filaments  
  > "actually introduced uncertainties by a factor of 2 in the average column density $N_0$" (7.1)
- Caveat (inferred, ours): Sonic scale formula is valid for turbulence-dominated field, but ordered field dominates
- Caveat (inferred, ours): B_turb from simulations with assumed relative uncertainty
- Caveat (inferred, ours): Single-tracer velocity from HNCO centroid maps; planar gradient subtraction assumed
- Caveat (inferred, ours): Uncertainties on b are large, mixed driving excluded only at 1 sigma

## Reproducibility

- Data public (paper): ALMA data used under project 2011.0.00217.S; derived maps from earlier papers  
  > "ADS/JAO.ALMA#2011.0.00217.S" (Acknowledgments)
- Products in archive: _not stated_
- Missing: Calibrated maps (column density, HNCO) rely on earlier papers
- Missing: Simulation setup details
- Missing: Velocity-map fitting details
- Data volume (inferred): tens of GB (Cycle 0 mosaic, four spectral windows)
- Score (inferred): 3/5, Analysis recipe is mostly given with equations and table, but input maps and calibration are inherited and simulation details are thin.
- Rediscovery candidate: no, Key inputs are derived products from previous papers plus custom MHD simulations; not a clean redo from archive data.

## Links

- Method: (cite: BruntFederrathPrice2010a) (2D-to-3D density dispersion)
- Method: (cite: Federrath2016) (filament width and sonic scale model)
- Method: (cite: FederrathKlessen2012) (SFR theory)
- Companion: (cite: RathborneEtAl2014) (ALMA+Herschel column density map)
- Companion: (cite: RathborneEtAl2015) (HNCO and molecular line cubes)
- Companion: (cite: PillaiEtAl2015) (magnetic field measurement)
- Related: Herschel Hi-GAL

## Checks

```json
{
 "quotes": 80,
 "quotes_ok": 80,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 14,
 "numeric_problems": 0,
 "fill": {
  "facts": 90,
  "stated": 59,
  "rate": 0.656
 },
 "evidence_ok": true
}
```
