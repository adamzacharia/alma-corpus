# JWST and ALMA Joint Analysis with [O II] λλ3726, 3729, [O III] λ4363, [O III] 88 μm, and [O III] 52 μm: Multizone Evolution of Electron Densities at z ∼ 0─14 and its Impact on Metallicity Measurements

`2025ApJ...993..204H` | The Astrophysical Journal 2025 | first author: Harikane, Yuichi | arXiv: 2505.09186 | DOI: 10.3847/1538-4357/ae0e53

Card schema 1.0 | model gpt-6.1-sol | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies
- Question: Test the robustness of direct-Te metallicities by relaxing the single-density ISM assumption and jointly analyzing optical and FIR lines.  
  > "We aim to investigate the impact of assuming a 1-zone ISM model on the derived ISM properties by first relaxing the single-density criterion and evaluating the effects on measurements such as metallicity and the mass-metallicity relation." (Introduction)
- Target **J0217-0208**: coordinates R.A. 02:17:21.60; Decl. -02:08:52.7  
  > "| J0217-0208 | 02:17:21.60 | $-$02:08:52.7 | $6.204$ | JWST/NIRCam | F150W,F200W,F300M,F410M | 0.2 hours |" (Table 1); z/distance z_spec = 6.204  
  > "| J0217-0208 | 02:17:21.60 | $-$02:08:52.7 | $6.204$ | JWST/NIRCam | F150W,F200W,F300M,F410M | 0.2 hours |" (Table 1); distance from _not stated_
- Target **SXDF-NB1006-2**: coordinates R.A. 02:18:56.54; Decl. -05:19:58.9  
  > "| SXDF-NB1006-2 | 02:18:56.54 | $-$05:19:58.9 | $7.212$ | JWST/NIRCam | F150W,F200W,F360M,F430M | 0.6 hours |" (Table 1); z/distance z_spec = 7.212  
  > "| SXDF-NB1006-2 | 02:18:56.54 | $-$05:19:58.9 | $7.212$ | JWST/NIRCam | F150W,F200W,F360M,F430M | 0.6 hours |" (Table 1); distance from _not stated_
- Target **J1211-0118**: coordinates R.A. 12:11:37.09; Decl. -01:18:16.5  
  > "| J1211-0118 | 12:11:37.09 | $-$01:18:16.5 | $6.031$ | JWST/NIRCam | F150W,F200W,F300M,F410M | 0.2 hours |" (Table 1); z/distance z_spec = 6.031  
  > "| J1211-0118 | 12:11:37.09 | $-$01:18:16.5 | $6.031$ | JWST/NIRCam | F150W,F200W,F300M,F410M | 0.2 hours |" (Table 1); distance from _not stated_
- Target **COS-3018555981**: coordinates _not stated_; z/distance z_spec = 6.854  
  > "| COS-3018555981 | $6.854$ |" (Table 5); distance from _not stated_
- Target **MACS1149-JD1**: coordinates _not stated_; z/distance z_spec = 9.110  
  > "| MACS1149-JD1 | $9.110$ |" (Table 5); distance from _not stated_

## Data provenance

- ALMA projects: 2022.1.00012.S, 2023.1.00022.S
- bands: Band 9: SXDF-NB1006-2; Band 10: J0217-0208 and J1211-0118  
  > "using Band 9 for SXDF-NB1006-2 and Band 10 for J0217-0208 and J1211-0118." (ALMA Dataset)
- frequencies and spectral setup: Four 1.875 GHz SPWs in FDM; total 7.5 GHz; velocity resolution ~3 km/s; one SPW centered on the expected 52 μm line  
  > "We used four spectral windows (SPWs) with 1.875 GHz bandwidths in Frequency Division Mode (FDM), yielding a total bandwidth of 7.5 GHz." (ALMA Dataset); "The velocity resolution was set to $\sim3$ km/s." (ALMA Dataset); "One of the SPWs was centered on the 52$\mu$m line frequency, expected from the redshift of the 88$\mu$m emission reported in (cite: 2020ApJ...896...93H) and (cite: 2023ApJ...945...69R)." (ALMA Dataset)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: C43-1, C43-2, and C43-3  
  > "The antenna configurations were C43-1, C43-2, and C43-3, achieving beam sizes of $0.$$''$$3-0.$$''$$4$," (ALMA Dataset)
- baselines: _not stated_
- angular resolution: 0.3–0.4 arcsec  
  > "achieving beam sizes of $0.$$''$$3-0.$$''$$4$" (ALMA Dataset)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: Total integration: 7.3, 17.7, and 12.8 hours for J0217-0208, SXDF-NB1006-2, and J1211-0118  
  > "total integration times were 7.3, 17.7, and 12.8 hours for J0217-0208, SXDF-NB1006-2, and J1211-0118, respectively." (ALMA Dataset)
- observing dates: _not stated_
- pi or archival as stated: ALMA Cycles 9 and 10; PI: Y. Harikane  
  > "The 52$\mu$m observations were carried out during ALMA Cycles 9 and 10 (2022.1.00012.S and 2023.1.00022.S, PI: Y. Harikane)" (ALMA Dataset)
- Line: [OIII] 52 μm (not stated)
- Line: [OIII] 88 μm (not stated)
- Other facility **JWST/NIRCam**: Images for morphologies and stellar populations; GO-1657 and GO-1840  
  > "NIRCam images of the three galaxies were taken to investigate their morphologies as well as stellar populations." (NIRCam Image); "We conducted JWST NIRCam (cite: 2023PASP..135b8001R) and NIRSpec/IFU (cite: 2022A&A...661A..80J) observations targeting the three galaxies (J0217-0208, SXDF-NB1006-2, and J1211-0118) in GO-1657 (PIs: Y. Harikane & R. Sanders)." (JWST Datasets); "In addition to the NIRCam data obtained in our program, we also use NIRCam images obtained in GO-1840 (PIs: J. Alvarez-Marquez & T. Hashimoto)." (NIRCam Image)
- Other facility **JWST/NIRSpec IFU**: Rest-frame optical spectroscopy; G235H, G395H, and G395M; additional MACS1149-JD1 data from GTO-1262  
  > "For J0217$-$0208 and J1211$-$0118 at $z=6.0-6.2$, we used the grating-filter pairs G235H/F170LP for $\lambda\lambda$3726,3729 and G395H/F290LP for H$\beta$, $\lambda\lambda$4959,5007, and H$\alpha$." (NIRSpec Spectrum); "additionally employed G395M/F290LP to fill the wavelength gap present in the G395H/F290LP coverage and observe $\lambda\lambda$4959,5007." (NIRSpec Spectrum); "For the rest-frame optical emission lines in MACS1149-JD1, we reduced the NIRSpec IFU data taken in GTO-1262 (PI: N. Lützgendorf) and measured the emission line fluxes in the same manner as in Section [2.2.2](#ss_nirspec)." (Galaxy Sample for the Analysis)
- Other facility **Subaru/HSC; HSC-SSP**: Ground-based morphology information used to select compact targets  
  > "their compact morphologies in the ground-based Subaru/Hyper Suprime-Cam (HSC; (cite: 2018PASJ...70S...1M)) images obtained from the HSC-Subaru Strategic Program (HSC-SSP) survey (cite: 2018PASJ...70S...4A)" (Galaxy Sample)
- Other facility **GTC/OSIRIS and Subaru/FOCAS**: Previous spectroscopic confirmations of the target galaxies  
  > "J0217-0208 and J1211-0118 were spectroscopically confirmed in (cite: 2018PASJ...70S..35M) via their Ly$\alpha$ emission line and the Lyman break feature, respectively," (Galaxy Sample); "with Gran Telescopio Canarias (GTC)/Optical System for Imaging and low-Intermediate-Resolution Integrated Spectroscopy (OSIRIS; (cite: 2000SPIE.4008..623C)) and Subaru/Faint Object Camera and Spectrograph (FOCAS; (cite: 2002PASJ...54..819K))" (Galaxy Sample); "SXDF-NB1006-2 was spectroscopically confirmed via its Ly$\alpha$ emission line with Subaru/FOCAS in (cite: 2012ApJ...752..114S)," (Galaxy Sample)
- Other facility **MAST**: Raw JWST data  
  > "We downloaded raw data from the MAST archive and ran Stage 1 calibration with `calwebb_detector1`." (NIRSpec Spectrum)
- External data: J0217-0208 and J1211-0118: existing ALMA 88 μm detections  
  > "their 88$\mu$m emission lines were detected with ALMA in (cite: 2020ApJ...896...93H)." (Galaxy Sample) [from (cite: 2020ApJ...896...93H)]
- External data: SXDF-NB1006-2: existing ALMA 88 μm detections  
  > "its 88$\mu$m emission line was reported in (cite: 2016Sci...352.1559I) and (cite: 2023ApJ...945...69R)." (Galaxy Sample) [from (cite: 2016Sci...352.1559I) and (cite: 2023ApJ...945...69R)]
- External data: 88 μm redshifts and FWHMs used for spectral-window placement and 52 μm integration  
  > "One of the SPWs was centered on the 52$\mu$m line frequency, expected from the redshift of the 88$\mu$m emission reported in (cite: 2020ApJ...896...93H) and (cite: 2023ApJ...945...69R)." (ALMA Dataset); "is the FWHM of the 88$\mu$m line reported in (cite: 2020ApJ...896...93H) and (cite: 2023ApJ...945...69R)." (ALMA Dataset) [from (cite: 2020ApJ...896...93H) and (cite: 2023ApJ...945...69R)]
- External data: COS-3018555981: 88 μm and optical emission-line fluxes; sum of main, north, and south optical components  
  > "using the 88$\mu$m and optical emission line fluxes reported by (cite: 2022MNRAS.515.1751W) and (cite: 2024arXiv241107695S), respectively." (Comparison of Densities from Optical and FIR); "We sum the fluxes of the main, north, and south components of COS-3018555981 defined in (cite: 2024arXiv241107695S) to obtain the total optical flux, which we compare with the ALMA 88$\mu$m line flux." (Comparison of Densities from Optical and FIR) [from (cite: 2022MNRAS.515.1751W) and (cite: 2024arXiv241107695S)]
- External data: MACS1149-JD1: 88 μm line flux  
  > "For the 88$\mu$m line flux, we adopt the value obtained in (cite: 2018Natur.557..392H)." (Galaxy Sample for the Analysis) [from (cite: 2018Natur.557..392H)]
- External data: COS-3018555981: total stellar mass including main, north, and south components  
  > "Total stellar mass including the main, north, and south components in (cite: 2024arXiv241107695S)." (Table 5) [from (cite: 2024arXiv241107695S)]
- External data: MACS1149-JD1: stellar mass assuming magnification μ = 10  
  > "Taken from (cite: 2024MNRAS.533.2488M) assuming the magnification factor of $\mu=10$." (Table 5) [from (cite: 2024MNRAS.533.2488M)]
- External data: Nearby-galaxy optical and FIR emission-line fluxes for density comparisons  
  > "(cite: 2006ApJS..164...81M) and (cite: 2008ApJS..178..280B) present rest-frame optical and FIR emission line fluxes of nearby galaxies, respectively." (Comparison of Densities from Optical and FIR) [from (cite: 2006ApJS..164...81M) and (cite: 2008ApJS..178..280B)]
- External data: Mrk71 and Haro3 optical/FIR electron densities  
  > "(cite: 2023NatAs...7..771C; 2024arXiv240518476C) measure the electron densities of local galaxies Mrk71 and Haro3," (Comparison of Densities from Optical and FIR) [from (cite: 2023NatAs...7..771C; 2024arXiv240518476C)]
- External data: MACS1149-JD1: previous FIR and optical density measurements for comparison  
  > "(cite: 2023ApJ...957L..18S) report the electron density of MACS1149-JD1 at $z=9.1$ to be $n_\mathrm{e,FIR}\simeq400$ cm$^{-3}$" (Comparison of Densities from Optical and FIR); "$n_\mathrm{e,optical}\simeq700$ cm$^{-3}$ reported by (cite: 2024MNRAS.533.2488M) using the $\lambda$3729/$\lambda$3726 ratio." (Comparison of Densities from Optical and FIR) [from (cite: 2023ApJ...957L..18S) and (cite: 2024MNRAS.533.2488M)]
- External data: Literature electron-density measurements used for redshift-evolution comparisons  
  > "previous JWST studies using the optical and/or lines (cite: 2023ApJ...956..139I; 2025arXiv250208712T)." (Redshift Evolution); "are comparable to those of galaxies at $z\sim0$ (cite: 2016ApJS..226...19F; 2008ApJS..178..280B)." (Redshift Evolution); "As reported in (cite: 2022ApJ...939..110M) and (cite: 2025arXiv250208712T), the densities measured with the rest-frame UV Ciii\] lines are very high," (Redshift Evolution) [from (cite: 2023ApJ...956..139I; 2025arXiv250208712T); (cite: 2016ApJS..226...19F; 2008ApJS..178..280B); (cite: 2022ApJ...939..110M)]
- External data: Additional z > 6 JWST/ALMA 88 μm detections used in the FIR density comparison  
  > "with detections of the 88$\mu$m line (cite: 2024arXiv240920533C; 2024ApJ...964..146F; 2024ApJ...977L..36H; 2023ApJ...957L..18S; 2024arXiv241107695S; 2024arXiv240920549S; 2022MNRAS.515.1751W)." (Redshift Evolution) [from (cite: 2024arXiv240920533C; 2024ApJ...964..146F; 2024ApJ...977L..36H; 2023ApJ...957L..18S; 2024arXiv241107695S; 2024arXiv240920549S; 2022MNRAS.515.1751W)]
- External data: SXDF-NB1006-2 and MACS1149-JD1: deep ALMA continuum nondetections used to constrain obscured star formation  
  > "SXDF-NB1006-2 and MACS1149-JD1 do not show dust continuum emission in the deep ALMA data in (cite: 2023ApJ...945...69R) and (cite: 2018Natur.557..392H)" (1-Zone Model Fitting) [from (cite: 2023ApJ...945...69R) and (cite: 2018Natur.557..392H)]
- External data: J0217-0208 and COS-3018555981: dust-obscured SFRs ~15 M_sun yr^-1  
  > "their dust-obscured SFRs are $\sim15$ $M_\odot\ \mathrm{yr^{-1}}$ (cite: 2020ApJ...896...93H; 2022MNRAS.515.1751W)." (1-Zone Model Fitting) [from (cite: 2020ApJ...896...93H; 2022MNRAS.515.1751W)]
- External data: Observed mass-metallicity relations for comparison  
  > "mass-metallicity relations observationally constrained with low-mass galaxies in (cite: 2023ApJS..269...33N) and (cite: 2024A&A...684A..75C)," (Comparison of Metallicities); "recent determinations for massive galaxies at $z\sim6-8$ in (cite: 2025arXiv250110559R)." (Comparison of Metallicities) [from (cite: 2023ApJS..269...33N); (cite: 2024A&A...684A..75C); (cite: 2025arXiv250110559R)]
- External data: Planck cosmology: Ωm = 0.3111, ΩΛ = 0.6899, Ωb = 0.0489, h = 0.6766, σ8 = 0.8102  
  > "Throughout this paper, we adopt the Planck cosmological parameter sets from the TT, TE, EE+lowP+lensing+BAO results (cite: 2020A&A...641A...6P): $\Omega_\mathrm{m}=0.3111$, $\Omega_\Lambda=0.6899$, $\Omega_\mathrm{b}=0.0489$, $h=0.6766$, and $\sigma_8=0.8102$." (Introduction) [from (cite: 2020A&A...641A...6P)]
- External data: Solar metallicity: 12+log(O/H) = 8.69; Z_sun = 0.0142  
  > "We define the solar metallicity as $\mathrm{12+log(O/H)}=8.69$ and $Z_\odot=0.0142$ (cite: 2009ARA&A..47..481A)." (Introduction) [from (cite: 2009ARA&A..47..481A)]
- External data: Theoretical [OIII]5007/[OIII]4959 = 2.98  
  > "an assumed line ratio of $f_\mathrm{\sc[OIII]5007}/f_\mathrm{[OIII]4959}=2.98$, based on theoretical calculations (cite: 2000MNRAS.312..813S)." (NIRSpec Spectrum) [from (cite: 2000MNRAS.312..813S)]
- External data: Theoretical [NII]6584/[NII]6548 = 2.94  
  > "we assumed the line ratio of $f_\mathrm{\sc[NII]6584}/f_\mathrm{[NII]6548}=2.94$, based on a theoretical value in (cite: 2020MNRAS.495.1016R)." (NIRSpec Spectrum) [from (cite: 2020MNRAS.495.1016R)]
- External data: 10,000 K intrinsic Balmer ratios: Hα/Hβ = 2.86; Hγ/Hβ = 0.468  
  > "We assume intrinsic line ratios for a temperature of 10,000 K from (cite: 1989agna.book.....O), namely $\mathrm{H\alpha/H\beta=2.86}$ and $\mathrm{H\gamma/H\beta=0.468}$," (Dust Attenuation) [from (cite: 1989agna.book.....O)]
- External data: Ionic oxygen-abundance equations and O+/O2+ electron-temperature relation  
  > "We then estimate the ionic oxygen abundance ratios of O$^+$/H$^+$ and O$^{2+}$/H$^+$ using the equations in (cite: 2006A&A...448..955I)," (Electron Temperature and Metallicity); "assuming an extrapolation of the electron temperature relation between O$^+$ and O$^{2+}$." (Electron Temperature and Metallicity) [from (cite: 2006A&A...448..955I)]
- External data: Alternative O+/O2+ electron-temperature relation used for a robustness check  
  > "Adopting the more recent $\mathrm{O}^+-\mathrm{O}^{2+}$ electron temperature relation from (cite: 2025arXiv250403839C) changes the derived oxygen abundances by less than 5%." (Electron Temperature and Metallicity) [from (cite: 2025arXiv250403839C)]
- External data: JWST-constrained R23 and O32 strong-line metallicity calibrations  
  > "we apply the R23 strong-line calibration, with parameters constrained by JWST spectroscopy in (cite: 2024ApJ...962...24S)," (Electron Temperature and Metallicity); "if we instead use the O32 calibration in (cite: 2024ApJ...962...24S), we obtain a metallicity estimate of $12+\mathrm{log(O/H)}\simeq 8.2$," (Electron Temperature and Metallicity) [from (cite: 2024ApJ...962...24S)]
- External data: Hβ luminosity-to-SFR conversion factor  
  > "SFR estimated from $L_\mathrm{H\beta}$ adopting the conversion factor in (cite: 2024ApJ...977..133C)." (Table 4) [from (cite: 2024ApJ...977..133C)]
- External data: Stellar IMF, dust attenuation law, and IGM attenuation model used in SED fitting  
  > "We assume the stellar IMF from (cite: 2003PASP..115..763C), the dust attenuation law of (cite: 2000ApJ...533..682C), and the intergalactic medium (IGM) attenuation model by (cite: 1995ApJ...441...18M)." (SED Fitting) [from (cite: 2003PASP..115..763C); (cite: 2000ApJ...533..682C); (cite: 1995ApJ...441...18M)]
- Simulation/model as data: Flexible Stellar Population Synthesis with MIST isochrones, including rotation-enhanced ionizing flux production  
  > "Model spectra are generated using the Flexible Stellar Population Synthesis (cite: 2009ApJ...699..486C; 2010ApJ...712..833C) package with the Modules for Experiments in Stellar Astrophysics Isochrones and Stellar Tracks (MIST; (cite: 2016ApJ...823..102C))." (SED Fitting); "The boost in ionizing flux production from massive stars due to rotation is included in the MIST isochrones (cite: 2017ApJ...838..159C)." (SED Fitting)
- Simulation/model as data: Cosmological mass-metallicity predictions from First Light, FLARES, and FIRE-2  
  > "some simulations predicting steep slopes in the relation, such as First Light (cite: 2023ApJ...953..140N), FLARES (cite: 2023MNRAS.518.3935W), and FIRE-2 (cite: 2024ApJ...967L..41M)." (Comparison of Metallicities)

## Processing

### Calibration

- pipeline or manual: CASA pipeline  
  > "The data were processed using the Common Astronomy Software (CASA; (cite: 2007ASPC..376..127M)) pipeline version 6.4.1.12." (ALMA Dataset)
- casa version: _not stated_
- pipeline version: 6.4.1.12  
  > "The data were processed using the Common Astronomy Software (CASA; (cite: 2007ASPC..376..127M)) pipeline version 6.4.1.12." (ALMA Dataset)
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: tclean  
  > "Using the task `tclean`, we produced images and cubes with natural weighting without taper to maximize point-source sensitivities." (ALMA Dataset)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "Using the task `tclean`, we produced images and cubes with natural weighting without taper to maximize point-source sensitivities." (ALMA Dataset)
- uv taper: without taper  
  > "Using the task `tclean`, we produced images and cubes with natural weighting without taper to maximize point-source sensitivities." (ALMA Dataset)
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: uvcontsub using off-line channels  
  > "To create a pure line image, we subtracted the continuum using off-line channels in the line cube with the CASA task `uvcontsub`." (ALMA Dataset)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.3–0.4 arcsec  
  > "achieving beam sizes of $0.$$''$$3-0.$$''$$4$" (ALMA Dataset)
- final rms: _not stated_

### Inherited from earlier work

- 52 μm tuning and velocity integration use previously measured 88 μm redshifts and FWHMs  
  > "One of the SPWs was centered on the 52$\mu$m line frequency, expected from the redshift of the 88$\mu$m emission reported in (cite: 2020ApJ...896...93H) and (cite: 2023ApJ...945...69R)." (ALMA Dataset); "is the FWHM of the 88$\mu$m line reported in (cite: 2020ApJ...896...93H) and (cite: 2023ApJ...945...69R)." (ALMA Dataset) [from (cite: 2020ApJ...896...93H) and (cite: 2023ApJ...945...69R)]
- Custom NIRCam pipeline modifications  
  > "We reduced these data using the JWST Calibration Pipeline (versions 1.12.5) and the Calibration Reference Data System context file `jwst_1193.pmap` with custom modifications described in (cite: 2023ApJS..265....5H)." (NIRCam Image) [from (cite: 2023ApJS..265....5H)]
- NIRSpec pipeline modifications  
  > "We reduced the NIRSpec IFU data using the JWST Calibration Pipeline (versions 1.12.5) and the Calibration Reference Data System context file of `jwst_1189.pmap` with several modifications (cite: 2024ApJ...976..142X)." (NIRSpec Spectrum) [from (cite: 2024ApJ...976..142X)]
- Q3D procedure for combining dithered cubes with reproject_interp  
  > "Following the procedure used by the Q3D team (cite: 2022ApJ...940L...7W; 2023ApJ...955...92V; 2023ApJ...953...56V)," (NIRSpec Spectrum); "we used the reproject package (cite: 2023zndo...7584411R) to combine the 3D data cubes taken in different dither positions into a single data cube using the `reproject_interp` routine." (NIRSpec Spectrum) [from Q3D team (cite: 2022ApJ...940L...7W; 2023ApJ...955...92V; 2023ApJ...953...56V)]
- Rescale pipeline error spectra to the line-free standard deviation, accounting for spatial noise correlations  
  > "Following (cite: 2023A&A...677A.145U), we scaled an error spectrum from the pipeline to match the standard deviation in line-free regions, taking into account the spatial correlations of the noise due to the PSF size." (NIRSpec Spectrum) [from (cite: 2023A&A...677A.145U)]
- Aperture-corrected NIRCam total magnitudes  
  > "with an aperture correction, following the method of (cite: 2023ApJS..265....5H)." (SED Fitting) [from (cite: 2023ApJS..265....5H)]
- Planck TT, TE, EE+lowP+lensing+BAO cosmology  
  > "Throughout this paper, we adopt the Planck cosmological parameter sets from the TT, TE, EE+lowP+lensing+BAO results (cite: 2020A&A...641A...6P):" (Introduction) [from (cite: 2020A&A...641A...6P)]
- SED stellar IMF, dust attenuation law, and IGM attenuation model  
  > "We assume the stellar IMF from (cite: 2003PASP..115..763C), the dust attenuation law of (cite: 2000ApJ...533..682C), and the intergalactic medium (IGM) attenuation model by (cite: 1995ApJ...441...18M)." (SED Fitting) [from (cite: 2003PASP..115..763C); (cite: 2000ApJ...533..682C); (cite: 1995ApJ...441...18M)]
- Theoretical [OIII] and [NII] doublet ratios fixed in Gaussian fitting  
  > "an assumed line ratio of $f_\mathrm{\sc[OIII]5007}/f_\mathrm{[OIII]4959}=2.98$, based on theoretical calculations (cite: 2000MNRAS.312..813S)." (NIRSpec Spectrum); "we assumed the line ratio of $f_\mathrm{\sc[NII]6584}/f_\mathrm{[NII]6548}=2.94$, based on a theoretical value in (cite: 2020MNRAS.495.1016R)." (NIRSpec Spectrum) [from (cite: 2000MNRAS.312..813S); (cite: 2020MNRAS.495.1016R)]
- Balmer-decrement dust law and intrinsic ratios at 10,000 K  
  > "calculate the color excess assuming the (cite: 2000ApJ...533..682C) dust attenuation law." (Dust Attenuation); "We assume intrinsic line ratios for a temperature of 10,000 K from (cite: 1989agna.book.....O), namely $\mathrm{H\alpha/H\beta=2.86}$ and $\mathrm{H\gamma/H\beta=0.468}$," (Dust Attenuation) [from (cite: 2000ApJ...533..682C); (cite: 1989agna.book.....O)]
- Direct-Te ionic-abundance equations and extrapolated O+/O2+ temperature relation  
  > "We then estimate the ionic oxygen abundance ratios of O$^+$/H$^+$ and O$^{2+}$/H$^+$ using the equations in (cite: 2006A&A...448..955I)," (Electron Temperature and Metallicity); "assuming an extrapolation of the electron temperature relation between O$^+$ and O$^{2+}$." (Electron Temperature and Metallicity) [from (cite: 2006A&A...448..955I)]
- R23 calibration for J1211-0118; O32 calibration as an alternative  
  > "we apply the R23 strong-line calibration, with parameters constrained by JWST spectroscopy in (cite: 2024ApJ...962...24S)," (Electron Temperature and Metallicity); "if we instead use the O32 calibration in (cite: 2024ApJ...962...24S), we obtain a metallicity estimate of $12+\mathrm{log(O/H)}\simeq 8.2$," (Electron Temperature and Metallicity) [from (cite: 2024ApJ...962...24S)]
- Cloudy emission-line calculations follow the previous paper  
  > "We use Cloudy version 17.01 and compute the emission-line luminosities in the same manner as (cite: 2020ApJ...896...93H)." (1-Zone Model Fitting) [from (cite: 2020ApJ...896...93H)]
- Hβ-to-SFR conversion  
  > "SFR estimated from $L_\mathrm{H\beta}$ adopting the conversion factor in (cite: 2024ApJ...977..133C)." (Table 4) [from (cite: 2024ApJ...977..133C)]

### Not stated but needed to reproduce (our reading)

- Exact 52 μm observed frequencies, SPW channel selections, and final cube channel binning.
- Numerical 88 μm redshifts and FWHMs used for each 52 μm tuning and integration interval.
- tclean cell size, image size, deconvolver, masks, stopping threshold, and iteration limit.
- Exact uvcontsub line-free channel ranges and polynomial order.
- Primary-beam correction and per-target synthesized beam dimensions.
- Aperture-noise calculation, correlated-noise treatment, and construction of ALMA line upper limits.
- Flux calibrators, absolute flux-scale uncertainty, and whether calibration uncertainty enters the joint fit.
- PyNeb version and atomic datasets.
- Joint-model MCMC sampler, likelihood, treatment of upper limits and flux covariance, walkers, burn-in, and convergence criteria.
- Priors and bounds for metallicity, O32, and the inter-zone λ5007 luminosity ratio.
- Full inherited Cloudy inputs and configuration.
- Numerical NIRCam aperture corrections and the referenced custom JWST reduction modifications.

## Analysis recipe

1. **Measure ALMA line and continuum emission**: Integrate 52 μm cubes over 2 × FWHM of the literature 88 μm line; measure total fluxes or limits in 0.8-arcsec-diameter apertures; extract spectra and continuum images.  
  > "We generated 52$\mu$m maps by integrating the ALMA data cubes over the velocity range corresponding to $2\times \mathrm{FWHM}_\mathrm{[OIII]88\mu m}$," (ALMA Dataset); "The total line flux or the upper limits are measured on the 52$\mu$m maps in a large $0.$$''$$8$-diameter circular aperture" (ALMA Dataset); "We also generated a dust continuum image but did not detect any dust continuum emission," (ALMA Dataset)
   - software: CASA, tclean, uvcontsub
   - parameter: 1D spectra: 0.3-arcsec-diameter circular aperture  
  > "1D spectra were extracted from the data cube using a $0.$$''$$3$-diameter circular aperture." (ALMA Dataset)
   - parameter: Continuum nondetections reported as 3σ upper limits  
  > "resulting in $3\sigma$ upper limits of $0.61$, $0.25$, and $0.60$ mJy/beam for J0217-0208, SXDF-NB1006-2, and J1211-0118, respectively." (ALMA Dataset)
   - assumption: Planck cosmology: Ωm = 0.3111, ΩΛ = 0.6899, Ωb = 0.0489, h = 0.6766, σ8 = 0.8102  
  > "Throughout this paper, we adopt the Planck cosmological parameter sets from the TT, TE, EE+lowP+lensing+BAO results (cite: 2020A&A...641A...6P): $\Omega_\mathrm{m}=0.3111$, $\Omega_\Lambda=0.6899$, $\Omega_\mathrm{b}=0.0489$, $h=0.6766$, and $\sigma_8=0.8102$." (Introduction)
   - fitting: _not stated_
   - validation: Line fluxes remain consistent within uncertainties without continuum subtraction.  
  > "However, the measured line fluxes remain consistent within the uncertainties even without applying `uvcontsub`." (ALMA Dataset)
2. **Extract and fit optical emission lines**: Extract aperture-corrected 1D NIRSpec spectra; subtract a cubic-polynomial continuum fitted in line-free regions; fit Gaussian emission lines.  
  > "Aperture correction for each spectrum obtained with a filter-grating pair was calculated by comparing emission line fluxes in the spectrum with those in a large $2.$$''$$0$-diameter aperture." (NIRSpec Spectrum); "By fitting line-free regions of each spectrum with a cubic polynomial, we estimated the continuum emission and subtracted it to make a continuum-subtracted spectrum." (NIRSpec Spectrum); "We measured emission line fluxes by fitting each emission line with a Gaussian." (NIRSpec Spectrum)
   - parameter: Extraction diameters: 0.6 arcsec for J0217-0208 and J1211-0118; 1.0 arcsec for SXDF-NB1006-2  
  > "We extracted a 1D spectrum from the data cube using a circular aperture whose diameter was $0.$$''$$6$ ($1.$$''$$0$) for J0217-0208 and J1211-0118 (for SXDF-NB1006-2)." (NIRSpec Spectrum)
   - parameter: Scale pipeline error spectra to line-free standard deviations, accounting for spatial correlations  
  > "Following (cite: 2023A&A...677A.145U), we scaled an error spectrum from the pipeline to match the standard deviation in line-free regions, taking into account the spatial correlations of the noise due to the PSF size." (NIRSpec Spectrum)
   - assumption: [OIII]5007/4959 = 2.98; [NII]6584/6548 = 2.94; equal widths within each doublet  
  > "an assumed line ratio of $f_\mathrm{\sc[OIII]5007}/f_\mathrm{[OIII]4959}=2.98$, based on theoretical calculations (cite: 2000MNRAS.312..813S)." (NIRSpec Spectrum); "we assumed the line ratio of $f_\mathrm{\sc[NII]6584}/f_\mathrm{[NII]6548}=2.94$, based on a theoretical value in (cite: 2020MNRAS.495.1016R)." (NIRSpec Spectrum); "We assumed the same line width for each set of the doublet lines," (NIRSpec Spectrum)
   - fitting: Determine redshift from Hβ and [OIII]4959,5007 and fix it for other lines; jointly fit the [OII] doublet with correlated uncertainties; use two Gaussian components for J0217-0208 [OIII]4959,5007 and Hα.  
  > "Then, we fit other emission lines with Gaussian functions with fixing the redshift to the value determined with the H$\beta$ and $\lambda\lambda$4959,5007 lines." (NIRSpec Spectrum); "We simultaneously fit the $\lambda\lambda$3726,3729 lines with two Gaussian functions to estimate the line ratio and its error with taking the correlated uncertainties into account." (NIRSpec Spectrum); "Because the $\lambda\lambda$4959,5007 and H$\alpha$ lines in J0217-0208 show a weak moderately broad component" (NIRSpec Spectrum)
   - validation: Conclusions do not change when using only narrow-component fluxes instead of total narrow-plus-broad fluxes.  
  > "the conclusions do not change if we use only the narrow-component flux given the small fraction of the broad-component flux ($\sim10\%$)." (NIRSpec Spectrum)
3. **Infer stellar populations**: Fit aperture-corrected photometry with PROSPECTOR and Flexible Stellar Population Synthesis/MIST model spectra.  
  > "For the SED fitting, we use PROSPECTOR (cite: 2021ApJS..254...22J)," (SED Fitting); "Model spectra are generated using the Flexible Stellar Population Synthesis (cite: 2009ApJ...699..486C; 2010ApJ...712..833C) package with the Modules for Experiments in Stellar Astrophysics Isochrones and Stellar Tracks (MIST; (cite: 2016ApJ...823..102C))." (SED Fitting)
   - software: PROSPECTOR, Flexible Stellar Population Synthesis, MIST, emcee
   - parameter: Free parameters: V-band dust optical depth, metallicity, star formation history, total stellar mass; fixed spectroscopic redshift  
  > "varying the dust optical depth in the $V$-band, metallicity, star formation history, and total stellar mass as free parameters, while fixing the redshift to the spectroscopically determined value." (SED Fitting)
   - parameter: Five SFH bins: 0–10 Myr first bin; remaining bins logarithmically spaced to z = 30; constant SFR in each bin  
  > "We adopt a flexible star formation history with five bins:" (SED Fitting); "the first bin is fixed at 0-10 Myr, and the other bins are spaced equally in logarithmic time between 10 Myr and a lookback time corresponding to $z=30$," (SED Fitting); "assuming a constant SFR within each bin." (SED Fitting)
   - assumption: Referenced stellar IMF, dust attenuation law, and IGM attenuation model  
  > "We assume the stellar IMF from (cite: 2003PASP..115..763C), the dust attenuation law of (cite: 2000ApJ...533..682C), and the intergalactic medium (IGM) attenuation model by (cite: 1995ApJ...441...18M)." (SED Fitting)
   - fitting: MCMC with emcee; SFH continuity prior; flat priors 0 < τV < 2, -2.0 < log(Z/Zsun) < 0.4, 6 < log(M*/Msun) < 12  
  > "A continuity prior is applied to the star formation history, with flat priors for other parameters in the ranges $0<\tau_\mathrm{V}<2$, $-2.0<\mathrm{log}(Z/Z_\odot)<0.4$, and $6<\mathrm{log}(M_*/M_\ensuremath{\odot})<12$." (SED Fitting); "We search for the best-fit model to the observed photometric data points using the Markov Chain Monte Carlo (MCMC) method with emcee (cite: 2013PASP..125..306F)." (SED Fitting)
   - validation: _not stated_
4. **Correct nebular dust attenuation**: Estimate E(B-V) from Hα, Hβ, and Hγ Balmer decrements and correct emission-line fluxes.  
  > "We evaluate the dust attenuation of our galaxies using the color excess, $E(B-V)$, estimated from the Balmer decrement." (Dust Attenuation); "we use emission line fluxes corrected for dust attenuation based on the $E(B-V)$ values measured from the Balmer decrement." (Dust Attenuation)
   - assumption: Dust law from (cite: 2000ApJ...533..682C); intrinsic ratios at 10,000 K: Hα/Hβ = 2.86 and Hγ/Hβ = 0.468  
  > "calculate the color excess assuming the (cite: 2000ApJ...533..682C) dust attenuation law." (Dust Attenuation); "We assume intrinsic line ratios for a temperature of 10,000 K from (cite: 1989agna.book.....O), namely $\mathrm{H\alpha/H\beta=2.86}$ and $\mathrm{H\gamma/H\beta=0.468}$," (Dust Attenuation)
   - fitting: _not stated_
   - validation: E(B-V) agrees with both Balmer ratios within errors; conclusions unchanged across the inferred temperature range.  
  > "The estimated $E(B-V)$ value for each galaxy is consistent with the $\mathrm{H\alpha/H\beta}$ and $\mathrm{H\gamma/H\beta}$ ratios within errors," (Dust Attenuation); "although the conclusions of this paper do not change for the range of temperatures inferred in Section [5.3](#ss_2zone)." (Dust Attenuation)
5. **Measure optical and FIR electron densities**: Use PyNeb with [OII]3729/3726 for optical densities and 52 μm/88 μm for FIR densities; derive spatially resolved optical density maps.  
  > "We calculate the electron densities of our galaxies from the measured $\lambda$3729/$\lambda$3726 ratios using PyNeb." (Density from the $\lambda\lambda$3726,3729 Line Ratio); "We use PyNeb to calculate the line ratio as a function of electron density and temperature." (Density from the 52$\mu$m/88$\mu$m Line Ratio); "Thanks to the IFU data, we can also investigate the spatially-resolved density map." (Density from the $\lambda\lambda$3726,3729 Line Ratio)
   - software: PyNeb
   - parameter: 52 μm/88 μm = a(b+ne)/(c+ne); a = 10.53, b = 224.46, c = 4181.45 at Te = 13000 K  
  > "The ratio for an electron temperature of $T_\mathrm{e}=13000$ K is well fitted by the following function:" (Density from the 52$\mu$m/88$\mu$m Line Ratio); "f_\mathrm{[OIII]52\mu m}/f_\mathrm{[OIII]88\mu m}=a\frac{b+n_\mathrm{e}}{c+n_\mathrm{e}}," (Density from the 52$\mu$m/88$\mu$m Line Ratio); "where $a=10.53$, $b=224.46$, and $c=4181.45$." (Density from the 52$\mu$m/88$\mu$m Line Ratio)
   - assumption: Te = 13000 K for optical density measurements  
  > "We assume the electron temperature of $T_\mathrm{e}=13000$ K," (Density from the $\lambda\lambda$3726,3729 Line Ratio)
   - fitting: _not stated_
   - validation: Optical densities agree within errors with the 10000 K literature calibration; changing ionization parameter does not significantly alter FIR estimates or limits.  
  > "using the calibration presented in (cite: 2016ApJ...816...23S) assuming $T_\mathrm{e}=10000$ K gives results consistent within errors." (Density from the $\lambda\lambda$3726,3729 Line Ratio); "our estimates and upper limits do not significantly change by changing the ionization parameter." (Density from the 52$\mu$m/88$\mu$m Line Ratio)
6. **Derive direct-Te metallicities**: Calculate Te from λ4363/λ5007 with PyNeb; derive O+/H+ and O2+/H+ with the referenced ionic-abundance equations.  
  > "We calculate the electron temperatures based on the $\lambda$4363/$\lambda$5007 line ratios using PyNeb (cite: 2015A&A...573A..42L)." (Electron Temperature and Metallicity); "We then estimate the ionic oxygen abundance ratios of O$^+$/H$^+$ and O$^{2+}$/H$^+$ using the equations in (cite: 2006A&A...448..955I)," (Electron Temperature and Metallicity)
   - software: PyNeb
   - assumption: Adopt optical electron densities and extrapolate the O+/O2+ temperature relation  
  > "Here, we adopt the electron densities measured with the optical lines from Section [4.3.1](#ss_den_opt)." (Electron Temperature and Metallicity); "assuming an extrapolation of the electron temperature relation between O$^+$ and O$^{2+}$." (Electron Temperature and Metallicity)
   - assumption: Ignore O3+/H+ because high-ionization lines are absent  
  > "We do not account for a higher ionization state of O$^{3+}$/H$^+$," (Electron Temperature and Metallicity); "our galaxies, which do not exhibit high-ionization lines (e.g., Heii)." (Electron Temperature and Metallicity)
   - fitting: _not stated_
   - validation: Using FIR densities increases Te by up to 1%; an alternative O+/O2+ temperature relation changes oxygen abundance by less than 5%.  
  > "If we instead use the densities measured with the FIR lines from Section [4.3.2](#ss_den_fir), the obtained temperatures increase by up to 1%." (Electron Temperature and Metallicity); "Adopting the more recent $\mathrm{O}^+-\mathrm{O}^{2+}$ electron temperature relation from (cite: 2025arXiv250403839C) changes the derived oxygen abundances by less than 5%." (Electron Temperature and Metallicity)
7. **Constrain J1211-0118 metallicity**: Use the λ4363 nondetection for a Te upper limit and metallicity lower limit; apply the JWST-constrained R23 strong-line calibration.  
  > "We estimate an upper limit on the electron temperature of $T_\mathrm{e}<12900$ K, which corresponds to a metallicity lower limit of $12+\mathrm{log(O/H)}>8.1$." (Electron Temperature and Metallicity); "we apply the R23 strong-line calibration, with parameters constrained by JWST spectroscopy in (cite: 2024ApJ...962...24S)," (Electron Temperature and Metallicity)
   - assumption: Adopt the high-metallicity R23 branch because of the λ4363-based lower limit  
  > "Given the lower limit of metallicity from $\lambda$4363, we adopt the value for the high-metallicity branch as a fiducial value." (Electron Temperature and Metallicity)
   - fitting: _not stated_
   - validation: Alternative O32 calibration gives 12+log(O/H) ≃ 8.2, consistent with the λ4363 lower limit.  
  > "if we instead use the O32 calibration in (cite: 2024ApJ...962...24S), we obtain a metallicity estimate of $12+\mathrm{log(O/H)}\simeq 8.2$, consistent with the lower limit from $\lambda$4363." (Electron Temperature and Metallicity)
8. **Extend density comparisons across redshift**: Combine literature fluxes and densities with the new sample; infer FIR densities from dust-corrected 88 μm/λ5007 and λ4363 temperatures when 52 μm is unavailable; compare optical and FIR redshift trends.  
  > "$n_\mathrm{e,FIR}$ can be calculated from the dust-corrected 88$\mu$m/$\lambda$5007 ratio combined with the $\lambda$4363-based electron temperature," (Comparison of Densities from Optical and FIR); "For these local galaxies, we derive $n_\mathrm{e,optical}$ and $n_\mathrm{e,FIR}$ using the optical $\lambda$6716/$\lambda$6731 and FIR 52$\mu$m/88$\mu$m line ratios reported therein." (Comparison of Densities from Optical and FIR); "Figure [12](#fig_ne_z) compiles the electron density measurements obtained in this study and from the literature using rest-frame UV, optical, and FIR lines." (Redshift Evolution)
   - parameter: COS-3018555981: sum main, north, and south optical components before comparison with ALMA  
  > "We sum the fluxes of the main, north, and south components of COS-3018555981 defined in (cite: 2024arXiv241107695S) to obtain the total optical flux, which we compare with the ALMA 88$\mu$m line flux." (Comparison of Densities from Optical and FIR)
   - fitting: _not stated_
   - validation: High-redshift optical/FIR density differences persist with either 52 μm/88 μm or 88 μm/λ5007.  
  > "regardless of whether $n_\mathrm{e,FIR}$ is measured with 52$\mu$m/88$\mu$m or 88$\mu$m/$\lambda$5007 ratios." (Comparison of Densities from Optical and FIR)
9. **Test homogeneous ISM predictions**: Predict 88 μm and 52 μm luminosities from optical-derived densities, temperatures, and metallicities with PyNeb; repeat with Cloudy 17.01; test obscured star formation as an explanation.  
  > "With these parameters, we can predict the luminosities of the 88$\mu$m and 52$\mu$m lines using PyNeb." (1-Zone Model Fitting); "We use Cloudy version 17.01 and compute the emission-line luminosities in the same manner as (cite: 2020ApJ...896...93H)." (1-Zone Model Fitting); "Clearly the 88$\mu$m and 52$\mu$m emission lines could originate in highly obscured dusty regions for which no optical emission emerges," (1-Zone Model Fitting)
   - software: PyNeb, Cloudy
   - parameter: Joint sample: J0217-0208, SXDF-NB1006-2, COS-3018555981, MACS1149-JD1; exclude J1211-0118 because λ4363 is not detected  
  > "From our three galaxies, we select J0217-0208 and SXDF-NB1006-2 for the joint analysis." (Galaxy Sample for the Analysis); "We do not include J1211-0118, as its $\lambda$4363 line is not detected." (Galaxy Sample for the Analysis); "In addition, we analyze COS-3018555981 at $z=6.9$ and MACS1149-JD1 at $z=9.1$, taken from the literature." (Galaxy Sample for the Analysis)
   - assumption: One homogeneous set of density, temperature, and metallicity  
  > "We hereafter refer to this model as a 1-zone model, as we assume only one set of parameters with a homogeneous condition." (1-Zone Model Fitting)
   - assumption: Tdust = 40 K for obscured-SFR upper limits in SXDF-NB1006-2 and MACS1149-JD1  
  > "with the $2\sigma$ upper limits on the obscured SFRs of $<3$ and $<0.6\ M_\odot\ \mathrm{yr^{-1}}$, respectively, assuming the dust temperature of $T_\mathrm{dust}=40$ K." (1-Zone Model Fitting)
   - fitting: _not stated_
   - validation: Compare observed and predicted luminosities; Cloudy and PyNeb both underpredict FIR lines by ~2–10; obscured gas does not resolve the discrepancy.  
  > "We find that the JWST optical emission lines are well reproduced, whereas the ALMA 88$\mu$m and 52$\mu$m line luminosities are underestimated by a factor of $\sim 2$-10, consistent with the results obtained using PyNeb." (1-Zone Model Fitting); "These comparisons indicate that heavily obscured dusty gas cannot explain the discrepancies seen in the 1-zone modeling." (1-Zone Model Fitting)
10. **Fit a two-zone ISM**: Fit dust-corrected optical and FIR luminosities with PyNeb emission from two regions with different densities and temperatures.  
  > "We fit the dust-corrected luminosities of the $\lambda\lambda$3726,3729, $\lambda$4363, H$\beta$, $\lambda\lambda$4959,5007, 52$\mu$m (if available), and 88$\mu$m lines with the 2-zone model." (2-Zone Model Fitting); "In the 2-zone model, the luminosities of the emission lines are calculated with PyNeb for each parameter set in each region," (2-Zone Model Fitting)
   - software: PyNeb
   - parameter: Seven free parameters: ne,1, ne,2, Te,1, Te,2, 12+log(O/H), O32, and L[OIII]5007,1/L[OIII]5007,2  
  > "the densities in the two regions ($n_\mathrm{e,1}$ and $n_\mathrm{e,2}$), the temperatures in the two regions ($T_\mathrm{e,1}$ and $T_\mathrm{e,2}$), the metallicity ($\mathrm{12+log(O/H)}$), the O32 ratio (O32)," (2-Zone Model Fitting); "the ratio of the $\lambda$5007 line luminosities between the two regions ($L_\mathrm{[OIII]5007,1}/L_\mathrm{[OIII]5007,2}$)," (2-Zone Model Fitting)
   - assumption: Two regions share metallicity and O32; region 1 is lower density  
  > "we assume that the two ionized gas regions have different densities and temperatures but share the same metallicity and O32 ratio" (2-Zone Model Fitting); "where subscripts 1 and 2 refer to the low- and high-density regions, respectively." (2-Zone Model Fitting)
   - fitting: MCMC, 200,000 steps; ne,1 < ne,2; flat log-density priors 0 < log(ne,1/[cm^-3]), log(ne,2/[cm^-3]) < 5; flat linear-temperature priors 5000 < Te,1, Te,2 < 30000 K  
  > "We use the MCMC method with 200,000 steps to estimate the best-fit parameters." (2-Zone Model Fitting); "We assume $n_\mathrm{e,1}<n_\mathrm{e,2}$ and flat priors for densities (in log space) and temperatures (in linear space)" (2-Zone Model Fitting); "in the ranges of $0<\mathrm{log}(n_\mathrm{e,1}/\mathrm{[cm^{-3}]})<5$, $0<\mathrm{log}(n_\mathrm{e,2}/\mathrm{[cm^{-3}]})<5$, $5000<T_\mathrm{e,1}/\mathrm{[K]}<30000$, and $5000<T_\mathrm{e,2}/\mathrm{[K]}<30000$." (2-Zone Model Fitting)
   - validation: Compare observed and predicted optical-to-FIR luminosities; two-zone modeling reproduces all observed lines.  
  > "Figure [14](#fig_2zone) compares the observed and predicted luminosities with the 2-zone model," (2-Zone Model Fitting); "the 2-zone model self-consistently reproduces all the emission line luminosities observed from the optical to FIR," (Comparison of Metallicities)
11. **Assess metallicity bias and model assumptions**: Compare direct-Te and two-zone metallicities in the mass-metallicity plane; refit with different O32 values and analyze unequal zone metallicities.  
  > "we test the robustness of direct-$T_\mathrm{e}$ metallicities assuming a 1-zone ISM by comparing them with metallicities derived from 2-zone modeling." (Comparison of Metallicities); "we conduct the MCMC fitting again, allowing different O32 ratios in the high- and low-density regions with $\mathrm{O32}_\mathrm{1}<\mathrm{O32}_\mathrm{2}$," (Effect of Different Ionization Parameters); "we discuss how the total hydrogen abundance changes if we change $L_\mathrm{H\beta,1}$ and $L_\mathrm{H\beta,2}$ while conserving the total observed H$\beta$ luminosity" (Effect of Different Metallicities)
   - assumption: Adopt two-zone metallicities as fiducial; test higher ionization parameter in the dense region and higher metallicity in the cooler low-density region  
  > "We adopt the metallicities from the 2-zone modeling as the fiducial values" (Comparison of Metallicities); "corresponding to different ionization parameters with $U_\mathrm{ion,1}<U_\mathrm{ion,2}$," (Effect of Different Ionization Parameters); "Since the temperature in the low-density region is lower, it is reasonable to assume that the metallicity in the low-density region is higher than that in the high-density region." (Effect of Different Metallicities)
   - fitting: Repeat MCMC with O32,1 < O32,2  
  > "we conduct the MCMC fitting again, allowing different O32 ratios in the high- and low-density regions with $\mathrm{O32}_\mathrm{1}<\mathrm{O32}_\mathrm{2}$," (Effect of Different Ionization Parameters)
   - validation: Under the tested changes, J0217-0208 and COS-3018555981 metallicities remain above direct-Te values.  
  > "the inferred metallicities from the JWST and ALMA joint analysis for J0217-0208 and COS-3018555981 remain higher than those obtained with the direct-$T_\mathrm{e}$ method." (Systematic Uncertainty of the 2-Zone Model)
12. **Construct joint optical/FIR metallicity estimators**: Fit quadratic relations between two-zone metallicity and log(88 μm/Hβ) or log(88 μm/λ5007) for four galaxies.  
  > "we plot the emission line ratios of 88$\mu$m/H$\beta$ and 88$\mu$m/$\lambda$5007 as a function of the metallicity obtained via the 2-zone modeling for the four galaxies analyzed here." (JWST+ALMA Metallicity Estimator); "We find that these line ratios correlate well with the metallicity, and obtain the best-fitting relations as follows:" (JWST+ALMA Metallicity Estimator)
   - parameter: x = 12+log(O/H) - 8.69  
  > "where $x=12+\mathrm{log(O/H)}-8.69$." (JWST+ALMA Metallicity Estimator)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : ALMA processing with pipeline version 6.4.1.12  
  > "The data were processed using the Common Astronomy Software (CASA; (cite: 2007ASPC..376..127M)) pipeline version 6.4.1.12." (ALMA Dataset)
- **tclean** : Natural-weighted ALMA images and cubes without taper  
  > "Using the task `tclean`, we produced images and cubes with natural weighting without taper to maximize point-source sensitivities." (ALMA Dataset)
- **uvcontsub** : ALMA continuum subtraction using off-line channels  
  > "To create a pure line image, we subtracted the continuum using off-line channels in the line cube with the CASA task `uvcontsub`." (ALMA Dataset)
- **JWST Calibration Pipeline** 1.12.5: NIRCam and NIRSpec IFU reduction  
  > "We reduced these data using the JWST Calibration Pipeline (versions 1.12.5) and the Calibration Reference Data System context file `jwst_1193.pmap` with custom modifications described in (cite: 2023ApJS..265....5H)." (NIRCam Image); "We reduced the NIRSpec IFU data using the JWST Calibration Pipeline (versions 1.12.5) and the Calibration Reference Data System context file of `jwst_1189.pmap` with several modifications (cite: 2024ApJ...976..142X)." (NIRSpec Spectrum)
- **Calibration Reference Data System** : Context files jwst_1193.pmap for NIRCam and jwst_1189.pmap for NIRSpec  
  > "the Calibration Reference Data System context file `jwst_1193.pmap`" (NIRCam Image); "the Calibration Reference Data System context file of `jwst_1189.pmap`" (NIRSpec Spectrum)
- **calwebb_detector1** : Stage 1 calibration of raw NIRSpec data  
  > "We downloaded raw data from the MAST archive and ran Stage 1 calibration with `calwebb_detector1`." (NIRSpec Spectrum)
- **NSClean** : Correct 1/f noise in count-rate frames  
  > "The resulting count-rate frames were corrected for 1/f noise using NSClean (cite: 2024PASP..136a5001R)." (NIRSpec Spectrum)
- **calwebb_spec2** : Stage 2 calibration and per-exposure 3D cubes with 0.05-arcsec pixels  
  > "We then ran Stage 2 calibration with `calwebb_spec2` and produced the 3D data cube for each exposure with a pixel scale of $0.$$''$$05$." (NIRSpec Spectrum)
- **reproject** : Combine dithered NIRSpec cubes  
  > "we used the reproject package (cite: 2023zndo...7584411R) to combine the 3D data cubes taken in different dither positions into a single data cube using the `reproject_interp` routine." (NIRSpec Spectrum)
- **reproject_interp** : Reproject dithered 3D cubes for combination  
  > "we used the reproject package (cite: 2023zndo...7584411R) to combine the 3D data cubes taken in different dither positions into a single data cube using the `reproject_interp` routine." (NIRSpec Spectrum)
- **PROSPECTOR** : SED fitting  
  > "For the SED fitting, we use PROSPECTOR (cite: 2021ApJS..254...22J)," (SED Fitting)
- **Flexible Stellar Population Synthesis** : Generate stellar model spectra with MIST  
  > "Model spectra are generated using the Flexible Stellar Population Synthesis (cite: 2009ApJ...699..486C; 2010ApJ...712..833C) package with the Modules for Experiments in Stellar Astrophysics Isochrones and Stellar Tracks (MIST; (cite: 2016ApJ...823..102C))." (SED Fitting)
- **MIST** : Stellar isochrones and tracks for SED model spectra, including rotation  
  > "The boost in ionizing flux production from massive stars due to rotation is included in the MIST isochrones (cite: 2017ApJ...838..159C)." (SED Fitting)
- **emcee** : MCMC SED fitting  
  > "We search for the best-fit model to the observed photometric data points using the Markov Chain Monte Carlo (MCMC) method with emcee (cite: 2013PASP..125..306F)." (SED Fitting)
- **PyNeb** : Electron temperatures, electron densities, and one-/two-zone emission-line luminosities  
  > "We calculate the electron temperatures based on the $\lambda$4363/$\lambda$5007 line ratios using PyNeb (cite: 2015A&A...573A..42L)." (Electron Temperature and Metallicity); "We calculate the electron densities of our galaxies from the measured $\lambda$3729/$\lambda$3726 ratios using PyNeb." (Density from the $\lambda\lambda$3726,3729 Line Ratio); "In the 2-zone model, the luminosities of the emission lines are calculated with PyNeb for each parameter set in each region," (2-Zone Model Fitting)
- **Cloudy** 17.01: Independent photoionization-model test of optical and FIR luminosities  
  > "We use Cloudy version 17.01 and compute the emission-line luminosities in the same manner as (cite: 2020ApJ...896...93H)." (1-Zone Model Fitting)
- **MAST** : Download raw JWST data  
  > "We downloaded raw data from the MAST archive and ran Stage 1 calibration with `calwebb_detector1`." (NIRSpec Spectrum)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| J0217-0208: 52 μm detection significance | 6.7 | not stated | σ | 1 | We clearly detect the 52$\mu$m emission line in J0217-0208 at the $6.7\sigma$ significance level. |
| J0217-0208: L[OIII]52μm | 1.4×10^10 | ±0.2×10^10 | L_sun | 1 | / $L_\mathrm{[OIII]52\mu m}$ \[$L_\odot$\] / $(1.4\pm0.2)\times10^{10}$ / $<1.0\times10^{9}$ / $<3.8\times10^{9}$ / |
| SXDF-NB1006-2: L[OIII]52μm | <1.0×10^9 | 2σ upper limit | L_sun | 1 | / $L_\mathrm{[OIII]52\mu m}$ \[$L_\odot$\] / $(1.4\pm0.2)\times10^{10}$ / $<1.0\times10^{9}$ / $<3.8\times10^{9}$ /; Errors are $1\sigma$ and upper limits are $2\sigma$. |
| J1211-0118: L[OIII]52μm | <3.8×10^9 | 2σ upper limit | L_sun | 1 | / $L_\mathrm{[OIII]52\mu m}$ \[$L_\odot$\] / $(1.4\pm0.2)\times10^{10}$ / $<1.0\times10^{9}$ / $<3.8\times10^{9}$ /; Errors are $1\sigma$ and upper limits are $2\sigma$. |
| J0217-0208: dust continuum | <0.61 | 3σ upper limit | mJy/beam | 1 | resulting in $3\sigma$ upper limits of $0.61$, $0.25$, and $0.60$ mJy/beam for J0217-0208, SXDF-NB1006-2, and J1211-0118, respectively. |
| SXDF-NB1006-2: dust continuum | <0.25 | 3σ upper limit | mJy/beam | 1 | resulting in $3\sigma$ upper limits of $0.61$, $0.25$, and $0.60$ mJy/beam for J0217-0208, SXDF-NB1006-2, and J1211-0118, respectively. |
| J1211-0118: dust continuum | <0.60 | 3σ upper limit | mJy/beam | 1 | resulting in $3\sigma$ upper limits of $0.61$, $0.25$, and $0.60$ mJy/beam for J0217-0208, SXDF-NB1006-2, and J1211-0118, respectively. |
| J0217-0208: log M* | 10.2 | +0.1/-0.2 | log(M_sun) | 3 | / J0217-0208 / $97.6_{-24.5}^{+0.1}$ / $10.2_{-0.2}^{+0.1}$ / $14.6_{-6.6}^{+4.3}$ / $0.05_{-0.02}^{+0.01}$ / |
| SXDF-NB1006-2: log M* | 8.7 | +0.1/-0.1 | log(M_sun) | 3 | / SXDF-NB1006-2 / $8.1_{-0.1}^{+1.6}$ / $8.7_{-0.1}^{+0.1}$ / $1.8_{-0.4}^{+1.2}$ / $0.01_{-0.01}^{+0.01}$ / |
| J1211-0118: log M* | 10.4 | +0.1/-0.2 | log(M_sun) | 3 | / J1211-0118 / $102.4_{-20.5}^{+61.9}$ / $10.4_{-0.2}^{+0.1}$ / $23.3_{-1.5}^{+14.5}$ / $0.01_{-0.01}^{+0.02}$ / |
| J0217-0208: Balmer-decrement E(B-V) | 0.10 | ±0.08 | ABmag | 4 | $E(B-V)$; / J0217-0208 / $6.204$ / $10.2_{-0.2}^{+0.1}$ / $3.23^{+0.23}_{-0.19}$ / $12300^{+1100}_{-1200}$ / $8.20^{+0.15}_{-0.11}$ / $0.10\pm0.08$ / |
| SXDF-NB1006-2: Balmer-decrement E(B-V) | 0.00 | ±0.11 | ABmag | 4 | / SXDF-NB1006-2 / $7.212$ / $8.7_{-0.1}^{+0.1}$ / $2.84^{+0.30}_{-0.29}$ / $13900^{+1000}_{-1100}$ / $7.99^{+0.10}_{-0.09}$ / $0.00\pm0.11$ / |
| J1211-0118: Balmer-decrement E(B-V) | 0.10 | ±0.08 | ABmag | 4 | We find small but non-negligible dust attenuation, with $E(B-V)\simeq0.1$, in J0217-0208 and J1211-0118.; \[ABmag\] / $0.10\pm0.08$ / $0.00\pm0.11$ / $0.10\pm0.08$ / |
| J0217-0208: ne,optical | 1782 | +1092/-584 | cm^-3 | 5 | \[cm$^{-3}$\] / $1782^{+1092}_{-584}$ / $774^{+695}_{-360}$ / $258^{+171}_{-127}$ / |
| SXDF-NB1006-2: ne,optical | 774 | +695/-360 | cm^-3 | 5 | \[cm$^{-3}$\] / $1782^{+1092}_{-584}$ / $774^{+695}_{-360}$ / $258^{+171}_{-127}$ / |
| J1211-0118: ne,optical | 258 | +171/-127 | cm^-3 | 5 | \[cm$^{-3}$\] / $1782^{+1092}_{-584}$ / $774^{+695}_{-360}$ / $258^{+171}_{-127}$ / |
| J0217-0208: ne,FIR | 505 | +253/-228 | cm^-3 | 5 | \[cm$^{-3}$\] / $505^{+253}_{-228}$ / $<87$ / $<97$ / |
| SXDF-NB1006-2: ne,FIR | <87 | 2σ upper limit | cm^-3 | 5 | \[cm$^{-3}$\] / $505^{+253}_{-228}$ / $<87$ / $<97$ /; Errors are $1\sigma$ and upper limits are $2\sigma$. |
| J1211-0118: ne,FIR | <97 | 2σ upper limit | cm^-3 | 5 | \[cm$^{-3}$\] / $505^{+253}_{-228}$ / $<87$ / $<97$ /; Errors are $1\sigma$ and upper limits are $2\sigma$. |
| J0217-0208: direct-Te temperature | 12300 | +1100/-1200 | K | 6 | / J0217-0208 / $6.204$ / $10.2_{-0.2}^{+0.1}$ / $3.23^{+0.23}_{-0.19}$ / $12300^{+1100}_{-1200}$ / $8.20^{+0.15}_{-0.11}$ / $0.10\pm0.08$ / |
| SXDF-NB1006-2: direct-Te temperature | 13900 | +1000/-1100 | K | 6 | / SXDF-NB1006-2 / $7.212$ / $8.7_{-0.1}^{+0.1}$ / $2.84^{+0.30}_{-0.29}$ / $13900^{+1000}_{-1100}$ / $7.99^{+0.10}_{-0.09}$ / $0.00\pm0.11$ / |
| J0217-0208: direct-Te 12+log(O/H) | 8.20 | +0.15/-0.11 | dimensionless | 6 | / J0217-0208 / $6.204$ / $10.2_{-0.2}^{+0.1}$ / $3.23^{+0.23}_{-0.19}$ / $12300^{+1100}_{-1200}$ / $8.20^{+0.15}_{-0.11}$ / $0.10\pm0.08$ / |
| SXDF-NB1006-2: direct-Te 12+log(O/H) | 7.99 | +0.10/-0.09 | dimensionless | 6 | / SXDF-NB1006-2 / $7.212$ / $8.7_{-0.1}^{+0.1}$ / $2.84^{+0.30}_{-0.29}$ / $13900^{+1000}_{-1100}$ / $7.99^{+0.10}_{-0.09}$ / $0.00\pm0.11$ / |
| COS-3018555981: direct-Te 12+log(O/H) | 8.06 | +0.06/-0.06 | dimensionless | 6 | $13400^{+700}_{-700}$ / $8.06^{+0.06}_{-0.06}$ / $0.17\pm0.01$ / |
| MACS1149-JD1: direct-Te 12+log(O/H) | 7.89 | +0.14/-0.12 | dimensionless | 6 | $15100^{+1500}_{-1500}$ / $7.89^{+0.14}_{-0.12}$ / $0.00\pm0.18$ / |
| J1211-0118: Te upper limit | <12900 | not stated | K | 7 | We estimate an upper limit on the electron temperature of $T_\mathrm{e}<12900$ K, which corresponds to a metallicity lower limit of $12+\mathrm{log(O/H)}>8.1$. |
| J1211-0118: 12+log(O/H) lower limit | >8.1 | not stated | dimensionless | 7 | We estimate an upper limit on the electron temperature of $T_\mathrm{e}<12900$ K, which corresponds to a metallicity lower limit of $12+\mathrm{log(O/H)}>8.1$. |
| J1211-0118: R23 high-branch 12+log(O/H) | 8.51 | +0.13/-0.15 | dimensionless | 7 | / $12+\mathrm{log(O/H)}$; / $8.20^{+0.15}_{-0.11}$ / $7.99^{+0.10}_{-0.09}$ / ($8.51^{+0.13}_{-0.15}$) /; the metallicity (in parentheses) is estimated based on the strong-line R23 calibrator |
| COS-3018555981: dust-corrected 88 μm/λ5007 | 0.22 | ±0.04 | dimensionless | 8 | the dust-corrected 88$\mu$m/$\lambda$5007 ratio, $f_\mathrm{[OIII]88\mu m}/f_\mathrm{[OIII]\lambda 5007}=0.22\pm0.04$, |
| COS-3018555981: ne,FIR | <90 | 2σ upper limit | cm^-3 | 8 | We derive a 2$\sigma$ upper limit of $n_\mathrm{e,FIR}<90$ cm$^{-3}$ |
| One-zone predicted 88 μm luminosity deficit | ~2-10 | not stated | dimensionless | 9 | with the predicted 88$\mu$m luminosities being $\sim2-10$ times lower than the observations. |
| J0217-0208: two-zone 12+log(O/H) | 9.03 | +0.08/-0.10 | dimensionless | 10 | / J0217-0208 / $9.03^{+0.08}_{-0.10}$ / |
| COS-3018555981: two-zone 12+log(O/H) | 8.45 | +0.34/-0.31 | dimensionless | 10 | / COS-3018555981 / $8.45^{+0.34}_{-0.31}$ / |
| SXDF-NB1006-2: two-zone 12+log(O/H) | 8.04 | +0.27/-0.07 | dimensionless | 10 | / SXDF-NB1006-2 / $8.04^{+0.27}_{-0.07}$ / |
| MACS1149-JD1: two-zone 12+log(O/H) | 7.86 | +0.14/-0.22 | dimensionless | 10 | / MACS1149-JD1 / $7.86^{+0.14}_{-0.22}$ / |
| J0217-0208: low-density-zone temperature | 6200 | +800/-1200 | K | 10 | / J0217-0208 / $9.03^{+0.08}_{-0.10}$ / $2.7^{+0.2}_{-0.3}$ / $3.7^{+1.3}_{-0.5}$ / $6200^{+800}_{-1200}$ / $15800^{+12900}_{-3600}$ / $0.59^{+0.04}_{-0.03}$ / $0.0^{+0.8}_{-0.7}$ / |
| J0217-0208: high-density-zone temperature | 15800 | +12900/-3600 | K | 10 | / J0217-0208 / $9.03^{+0.08}_{-0.10}$ / $2.7^{+0.2}_{-0.3}$ / $3.7^{+1.3}_{-0.5}$ / $6200^{+800}_{-1200}$ / $15800^{+12900}_{-3600}$ / $0.59^{+0.04}_{-0.03}$ / $0.0^{+0.8}_{-0.7}$ / |
| Low-density-region electron density | <1000 | not stated | cm^-3 | 10 | the low- and high-density regions have electron densities of $n_\mathrm{e,1}<1000\ \mathrm{cm}^{-3}$ and $n_\mathrm{e,2}>1000\ \mathrm{cm}^{-3}$, respectively. |
| High-density-region electron density | >1000 | not stated | cm^-3 | 10 | the low- and high-density regions have electron densities of $n_\mathrm{e,1}<1000\ \mathrm{cm}^{-3}$ and $n_\mathrm{e,2}>1000\ \mathrm{cm}^{-3}$, respectively. |
| Low-/high-density-region volume ratio | >1000 | not stated | dimensionless | 10 | the results also suggest that the volume of the low-density region is $>1000$ times larger than that of the high-density region, |
| COS-3018555981: direct-Te metallicity underestimate | 0.4 | not stated | dex | 11 | are significantly underestimated in the two more massive galaxies, COS-3018555981 and J0217-0208, by 0.4 and 0.8 dex, respectively. |
| J0217-0208: direct-Te metallicity underestimate | 0.8 | not stated | dex | 11 | are significantly underestimated in the two more massive galaxies, COS-3018555981 and J0217-0208, by 0.4 and 0.8 dex, respectively. |
| log([OIII]88μm/Hβ) calibration: constant, x, x² coefficients | 0.265, 0.428, -0.209 | not stated | dimensionless | 12 | \mathrm{log\left(\frac{\textsc{[Oiii]}88\mu m}{H\beta}\right)}&=0.265+0.428x-0.209x^2 |
| log([OIII]88μm/[OIII]λ5007) calibration: constant, x, x² coefficients | -0.509, 0.376, -0.362 | not stated | dimensionless | 12 | \mathrm{log\left(\frac{\textsc{[Oiii]}88\mu m}{\textsc{[Oiii]}\lambda 5007}\right)}&=-0.509+0.376x-0.362x^2, |

## Qualitative findings

- FIR-based electron densities are systematically lower than optical-based densities in the high-redshift sample.  
  > "The electron densities measured with the 52$\mu$m/88$\mu$m ratios (the red diamonds) are systematically lower than those measured with the $\lambda$3729/$\lambda$3726 ratios." (Comparison of Densities from Optical and FIR)
- FIR lines predominantly trace low-density gas; optical lines receive contributions from both density regions.  
  > "the FIR luminosities are dominated by emission from the low-density region." (2-Zone Model Fitting); "The luminosities of the $\lambda\lambda$3726,3729 lines receive contributions from both low- and high-density regions," (2-Zone Model Fitting)
- Optical densities increase with redshift, while FIR densities show no redshift evolution.  
  > "Combined with results from the literature, it is clear that the density measured with the optical or lines increases toward higher redshifts." (Redshift Evolution); "These results indicate that $n_\mathrm{e,FIR}$ of high-redshift galaxies are low and do not show redshift evolution," (Redshift Evolution)
- A high-temperature dense component can dominate λ4363 and bias direct-Te metallicities downward.  
  > "the $\lambda$4363 emission from the high-density, high-temperature region dominates the observed luminosity because its emissivity strongly depends on electron temperature." (Comparison of Metallicities); "As a result, the temperature estimated from $\lambda$4363 is overestimated compared to the effective temperature of the whole system, and the derived metallicity is significantly underestimated." (Comparison of Metallicities)

## Claim tuples

- H: Optical and FIR density diagnostics trace the same gas density. | E: Compare [OII]3729/3726 densities with 52 μm/88 μm densities. | R: FIR-derived densities are systematically lower. | F: The lines trace different density components, motivating multi-zone ISM models. | **refuted**
- H: A homogeneous one-zone model constrained by optical lines reproduces ALMA FIR luminosities. | E: Predict FIR luminosities with PyNeb and Cloudy and compare with four galaxies. | R: FIR luminosities are underestimated by ~2–10. | F: A one-zone model fails; heavily obscured gas does not explain the discrepancy. | **refuted**
- H: Two regions with different densities and temperatures can jointly reproduce optical and FIR emission. | E: Fit dust-corrected line luminosities with a seven-parameter two-zone model. | R: The model reproduces the optical-to-FIR luminosities, with substantial parameter degeneracies. | F: A low-density and high-density mixture explains the observed lines. | **supported**
- H: Direct-Te metallicities remain accurate when galaxies contain multiple density and temperature components. | E: Compare direct-Te metallicities with fiducial two-zone metallicities. | R: Agreement in the two less massive galaxies; underestimates of 0.4 and 0.8 dex in the two more massive galaxies. | F: Direct-Te metallicities can be significantly underestimated. | **partially**
- H: FIR-derived densities evolve with redshift in the same way as optical densities. | E: Compile optical, UV, and FIR density measurements across redshift. | R: Optical densities increase; FIR densities remain low and comparable to local values. | F: The diagnostics show contrasting redshift trends. | **refuted**
- H: Joint optical/FIR line ratios can indicate metallicities and flag direct-Te underestimation. | E: Fit line-ratio versus two-zone metallicity relations for four galaxies. | R: 88 μm/Hβ and 88 μm/λ5007 correlate with inferred metallicity. | F: The relations provide provisional guidelines requiring a larger calibration sample. | **partially**

## Reasoning

- Why this data: Existing 88 μm detections and compact HSC morphologies enable integrated-flux joint analysis; 52 μm adds complementary density constraints.  
  > "This sample was chosen based on existing 88$\mu$m detections from ALMA," (Galaxy Sample); "allowing us to conduct a JWST and ALMA joint analysis as simply as possible, based on the total line fluxes rather than a spatially resolved analysis." (Galaxy Sample); "we observed the 52$\mu$m line, which has a higher critical density and thus provides complementary constraints to the 88$\mu$m line." (ALMA Dataset)
- Why this method: One-zone failures motivate relaxing the single-density and single-temperature assumptions; natural weighting without taper maximizes point-source sensitivity.  
  > "Motivated by the failures of the 1-zone modeling in Section [5.2](#ss_1zone), we introduce a 2-zone model and relax the single-density and single-temperature assumptions" (2-Zone Model Fitting); "Using the task `tclean`, we produced images and cubes with natural weighting without taper to maximize point-source sensitivities." (ALMA Dataset)
- Alternative: Heavily obscured dusty gas cannot explain the one-zone FIR discrepancy.  
  > "These comparisons indicate that heavily obscured dusty gas cannot explain the discrepancies seen in the 1-zone modeling." (1-Zone Model Fitting)
- Alternative: Cloudy independently reproduces the one-zone FIR underprediction found with PyNeb.  
  > "We find that the JWST optical emission lines are well reproduced, whereas the ALMA 88$\mu$m and 52$\mu$m line luminosities are underestimated by a factor of $\sim 2$-10, consistent with the results obtained using PyNeb." (1-Zone Model Fitting)
- Alternative: Spatially distinct ionic regions without mixing cannot reproduce J0217-0208.  
  > "a model with spatially distinct and regions without mixing cannot reproduce the observed lines of J0217-0208." (2-Zone Model Fitting)
- Alternative: Clumpy star formation and AGN activity are possible explanations of the density structure; neither is uniquely established.  
  > "Here, we discuss two scenarios that can explain this evolution: (a) clumpy galaxies and (b) AGN activity." (Evolution of the ISM Structure); "Although we do not observe any obvious AGN signatures, such as broad hydrogen Balmer lines, in the galaxies studied here," (Evolution of the ISM Structure)
- Alternative: Porous density-bounded Hii regions, shocks, and diffuse ionized gas may also contribute.  
  > "porous, density-bounded Hii regions with high Lyman continuum escape have been proposed to explain both optical and FIR line properties (cite: 2022A&A...667A..35R)." (Evolution of the ISM Structure); "Shocks, which can strongly affect the density structure of the ISM, may also play a role" (Evolution of the ISM Structure); "Moreover, diffuse ionized gas could influence both the observed line ratios and the inferred electron densities." (Evolution of the ISM Structure)
- How they decided it was enough: Adopt two-zone metallicities because the model reproduces optical and FIR luminosities simultaneously.  
  > "We adopt the metallicities from the 2-zone modeling as the fiducial values because the 2-zone model self-consistently reproduces all the emission line luminosities observed from the optical to FIR," (Comparison of Metallicities)
- Limitation (authors): Seven effective emission lines are insufficient to fully determine seven free parameters; most parameters are degenerate.  
  > "effectively we have seven emission lines, which are insufficient to fully determine the seven free parameters." (2-Zone Model Fitting); "As a result, most of the obtained parameters exhibit significant degeneracies, although some parameters, such as metallicity, are well constrained." (2-Zone Model Fitting)
- Limitation (authors): The lower limit of ne,1 and upper limit of ne,2 are not constrained.  
  > "Although the lower limit of $n_\mathrm{e,1}$ and the upper limit of $n_\mathrm{e,2}$ are not constrained," (2-Zone Model Fitting)
- Limitation (authors): Equal metallicity and ionization parameter across zones are simplifying assumptions.  
  > "In the 2-zone modeling, we assume the same ionization parameters and metallicities in the high- and low-density regions to keep the model as simple as possible." (Systematic Uncertainty of the 2-Zone Model)
- Limitation (authors): The metallicity-estimator calibration is constrained by only four galaxies.  
  > "We provide strong-line metallicity calibrations using optical and FIR lines (Figure [18](#fig_Z_OIIIr)), although they are currently constrained by only four galaxies." (Summary)
- Limitation (authors): A larger sample is required for firm conclusions about simulation comparisons.  
  > "Although a larger sample is needed for firm conclusions," (Comparison of Metallicities)
- Limitation (authors): The sample is restricted to galaxies with ALMA 88 μm detections.  
  > "The galaxies studied here are limited to those with ALMA 88$\mu$m detections." (Selection Bias)
- Caveat (inferred, ours): The two-zone metallicities are conditional on a simplified model with strong degeneracies; successful line reproduction alone does not establish uniqueness.
- Caveat (inferred, ours): The systematic tests impose directional changes in O32 and zone metallicity rather than exploring all possible structures.
- Caveat (inferred, ours): The four-galaxy estimator has no stated independent validation sample or coefficient uncertainties.
- Caveat (inferred, ours): A high detection fraction among previously observed galaxies does not establish an unbiased parent population; the joint analysis also requires λ4363 detection.
- Caveat (inferred, ours): The Electron Temperature and Metallicity subsection initially names J1211-0118 as a λ4363 detection, contradicting its later nondetection statement, the tables, and the joint-sample selection.
- Caveat (inferred, ours): Cross-facility aperture matching and flux-calibration covariance need explicit treatment when reproducing the joint fit.

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: Raw JWST data obtained from MAST  
  > "We downloaded raw data from the MAST archive and ran Stage 1 calibration with `calwebb_detector1`." (NIRSpec Spectrum)
- Missing: Public availability of the ALMA datasets is not explicitly stated.
- Missing: No analysis-code release, fit chains, or machine-readable model implementation is identified.
- Missing: ALMA imaging and continuum-subtraction parameters are incomplete.
- Missing: Numerical 88 μm measurements and integration widths must be recovered from the cited papers.
- Missing: Complete joint-fit likelihood, priors, normalization, upper-limit treatment, and convergence information are absent.
- Missing: PyNeb atomic data and version are absent.
- Missing: Custom JWST reduction and photometric corrections are delegated to earlier work.
- Missing: Full COS-3018555981 and MACS1149-JD1 input fluxes and inherited Cloudy configuration require external papers.
- Data volume (inferred): Not reliably estimable from the text: antenna counts, execution details, visibility sampling, and final channel counts are absent.
- Score (inferred): 6/5, 6/10: project codes, main extraction choices, diagnostics, model structure, several priors, and numeric answer keys are supplied; exact imaging, atomic data, likelihood, code, and inherited inputs remain incomplete.
- Rediscovery candidate: no, The main results are numeric, but ALMA public availability is not stated and the joint-fitting recipe lacks essential implementation details.

## Links

- Method: (cite: 2007ASPC..376..127M) (CASA processing.)
- Method: (cite: 2023ApJS..265....5H) (Inherited NIRCam reduction modifications and aperture-corrected photometry.)
- Method: (cite: 2024ApJ...976..142X) (Inherited NIRSpec reduction modifications.)
- Method: (cite: 2024PASP..136a5001R) (NSClean 1/f-noise correction.)
- Method: (cite: 2022ApJ...940L...7W; 2023ApJ...955...92V; 2023ApJ...953...56V) (Q3D cube-combination procedure.)
- Method: (cite: 2023zndo...7584411R) (reproject cube alignment.)
- Method: (cite: 2023A&A...677A.145U) (Error-spectrum rescaling for correlated noise.)
- Method: (cite: 2021ApJS..254...22J) (PROSPECTOR SED fitting.)
- Method: (cite: 2009ApJ...699..486C; 2010ApJ...712..833C) (Flexible Stellar Population Synthesis.)
- Method: (cite: 2016ApJ...823..102C); (cite: 2017ApJ...838..159C) (MIST tracks and rotation-enhanced ionizing flux.)
- Method: (cite: 2013PASP..125..306F) (emcee SED sampling.)
- Method: (cite: 2015A&A...573A..42L) (PyNeb density, temperature, and line-emissivity calculations.)
- Method: (cite: 2006A&A...448..955I) (Ionic oxygen-abundance equations and temperature relation.)
- Method: (cite: 2025arXiv250403839C) (Alternative ionic-temperature relation for robustness testing.)
- Method: (cite: 2024ApJ...962...24S) (R23 and O32 strong-line metallicity calibrations.)
- Method: (cite: 2017RMxAA..53..385F) (Cloudy photoionization modeling.)
- Method: (cite: 2020ApJ...896...93H) (Inherited Cloudy emission-line calculation procedure and ALMA input measurements.)
- Method: (cite: 2000MNRAS.312..813S); (cite: 2020MNRAS.495.1016R) (Fixed theoretical doublet ratios.)
- Method: (cite: 2000ApJ...533..682C); (cite: 1989agna.book.....O) (Dust attenuation law and intrinsic Balmer ratios.)
- Method: (cite: 2024ApJ...977..133C) (Hβ-to-SFR conversion.)
- Companion: (cite: 2020ApJ...896...93H) (Previous J0217-0208 and J1211-0118 ALMA measurements.)
- Companion: (cite: 2016Sci...352.1559I); (cite: 2023ApJ...945...69R) (Previous SXDF-NB1006-2 ALMA measurements.)
- Companion: (cite: 2022MNRAS.515.1751W); (cite: 2024arXiv241107695S) (COS-3018555981 input fluxes and component information.)
- Companion: (cite: 2018Natur.557..392H); (cite: 2024MNRAS.533.2488M) (MACS1149-JD1 ALMA flux and stellar mass.)
- Companion: (cite: 2025ApJ...991L..38U) (Independent similar optical/FIR multi-zone analysis at z ~ 6.8.)
- Related: HSC-Subaru Strategic Program (HSC-SSP)
- Related: JWST GO-1657
- Related: JWST GO-1840
- Related: JWST GTO-1262

## Checks

```json
{
 "quotes": 304,
 "quotes_ok": 304,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 44,
 "numeric_problems": 0,
 "fill": {
  "facts": 192,
  "stated": 153,
  "rate": 0.797
 },
 "evidence_ok": true
}
```
