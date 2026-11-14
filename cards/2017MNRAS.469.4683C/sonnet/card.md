# ALMA constraints on star-forming gas in a prototypical z = 1.5 clumpy galaxy: the dearth of CO(5-4) emission from UV-bright clumps

`2017MNRAS.469.4683C` | Monthly Notices of the Royal Astronomical Society 2017 | first author: Cibinel, A. | arXiv: 1703.02550 | DOI: 10.1093/mnras/stx1112

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies
- Question: Do UV-bright star-forming clumps in a z=1.5 main-sequence galaxy show CO(5-4) emission, and what does the resolved CO(5-4) distribution imply for gas content and star formation efficiency?  
  > "Conversely, we do not detect any CO(5-4) emission from the UV-bright clumps." (abstract)
- Target **UDF6462**: coordinates RA 53.18172 deg, Dec -27.78298 deg (J2000)  
  > "$z_{\rm spec}$ | 1.570" (Table 1); "All measurements are consistent with a $z_{\rm spec}$ = 1.570." (2.1 Multiwavelength data); z/distance z_spec = 1.570  
  > "$z_{\rm spec}$ | 1.570" (Table 1); "All measurements are consistent with a $z_{\rm spec}$ = 1.570." (2.1 Multiwavelength data); distance from 3D-HST grism, FORS2 and SINFONI spectroscopy  
  > "$z_{\rm spec}$ | 1.570" (Table 1); "All measurements are consistent with a $z_{\rm spec}$ = 1.570." (2.1 Multiwavelength data)

## Data provenance

- ALMA projects: 2013.1.01271.S
- bands: Band 6, Cycle 2  
  > "ALMA Band 6 observations for UDF6462 were carried out during Cycle 2" (4.1 Observations)
- frequencies and spectral setup: CO(5-4) at nu_obs=224.23 GHz in first baseband, 0.976 MHz resolution; other three basebands TDM continuum  
  > "with a spectral resolution of 0.976 MHz. The other three baseband were used in Time Division Mode (TDM) mode for continuum observations." (4.1 Observations)
- continuum bandwidth: 7.4 GHz line-free  
  > "our continuum observations cover 7.4 GHz" (4.1 Observations)
- arrays: _not stated_
- configurations: C34-4/5, C34-5, C34-7/(6)  
  > "| 2015 August 28 | C34-7/(6) | 40 | 1.6 | 0.77 | 0.26 | 1.75 | 4.0 |" (Table 2)
- baselines: _not stated_
- angular resolution: 0.2-0.6 arcsec; synthesized beam 0.62x0.40 arcsec (natural weighting)  
  > "resulting in a synthesized beam of FWHM $\theta_{\rm beam}$=0$\ensuremath{''}$62$\times$0$\ensuremath{''}$40" (4.1 Observations)
- max recoverable scale: ~4 arcsec  
  > "The maximum recoverable scale of our observations is $\sim$4$^{\prime\prime}$." (4.1 Observations)
- sensitivity: 7.6 uJy/beam continuum; 0.066 mJy/beam per 100 km/s channel  
  > "$\sigma_{\rm cont}$ = 7.6$\mu$Jy/beam (natural weighting) for the continuum and $\sigma_{\rm CO(5-4)}$ = 0.066mJy/beam over a 100km/s channel" (4.1 Observations)
- time on source: 4.4 hr  
  > "We integrated for a total of 4.4hr on source" (4.1 Observations)
- observing dates: 2014 July 18 to 2015 August 28  
  > "| 2014 July 18 | C34-4/5 | 32 | 0.65 | 0.56 | 0.65 | 0.58 | 8.4 |" (Table 2)
- pi or archival as stated: PI: Cibinel  
  > "(Project ID: 2013.1.01271.S, PI: Cibinel)" (4.1 Observations)
- Line: CO 5-4 (576.26 GHz)
- Other facility **HST (XDF, HDUV, CANDELS)**: Multiband imaging for clump identification and resolved stellar mass/SFR maps  
  > "we specifically use $B_{435}$ to $H_{160}$ data extracted from the eXtreme Deep Field (XDF)" (2.1 Multiwavelength data)
- Other facility **VLA 6 GHz**: Radio SFR and size of nuclear region  
  > "we can also derive an extinction-free SFR from the VLA C-band observations of (cite: Rujopakarn+16)" (2.2 Integrated stellar mass and star formation rate estimates)
- Other facility **Spitzer/Herschel**: IR photometry for SED fitting and L_IR  
  > "Near- to far-infrared (FIR) coverage at wavelengths between 3.6$\mu$m and 500$\mu$m is also available" (2.1 Multiwavelength data)
- Other facility **VLT/SINFONI**: Halpha velocity field, dispersion and metallicity  
  > "maps of $H\alpha$, \[NII\] and \[SII\] emission and the velocity field in UDF6462 were derived from the SINFONI integral-field spectroscopic observations" (2.1 Multiwavelength data)
- External data: VLA 6 GHz map and flux method  
  > "were obtained from the VLA C-band (6GHz, $\sim$ 5 cm) survey described in (cite: Rujopakarn+16)" (2.1 Multiwavelength data) [from (cite: Rujopakarn+16)]
- External data: Integrated stellar mass from 3D-HST catalogue  
  > "(4) integrated stellar mass from 3D-HST (cite: Skelton+14)" (Table 1) [from (cite: Skelton+14)]
- External data: Halpha velocity field, dispersion, metallicity, inclination  
  > "we thus shifted each spectrum by a velocity offset determined from the $H\alpha$ velocity field published in (cite: Bournaud+08)" (4.2.2 Clumps) [from (cite: Bournaud+08)]
- External data: L_IR-L'CO(5-4) correlations and R51=0.23 for MS galaxies  
  > "we used an excitation correction $R_{51}=0.23$ as derived in (cite: Daddi+15) for normal, MS galaxies" (5.3.2 Molecular gas mass from CO(5-4) emission) [from (cite: Daddi+15)]
- External data: Clump alpha_CO=2.9 and R51=0.6 from simulations  
  > "from fig. 5 of (cite: Bournaud+15) we derive an $\alpha_{\rm CO}$ = 2.9" (5.3.2 Molecular gas mass from CO(5-4) emission) [from (cite: Bournaud+15)]
- Simulation/model as data: Simulated ALMA observations with CASA simobserve from a sky model built from the HST UV-based SFR map, renormalized to the observed nuclear CO flux  
  > "We then employed the simobserve task within CASA to simulate ALMA observations." (9 Tests on Simulated Images)

## Processing

### Calibration

- pipeline or manual: CASA with standard ALMA pipeline  
  > "Calibration of the ALMA raw data was carried out using Common Astronomy Software Applications (cite: McMullin+07) and the standard ALMA pipeline." (4.1 Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: GILDAS imaging; uv-plane fitting with UV_FIT  
  > "Imaging of visibilities and the scientific analysis of the data cubes were instead mostly performed with the GILDAS software package" (4.1 Observations)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "To maximize sensitivity, a natural weighting was used to generate the maps" (4.1 Observations)
- uv taper: 1 arcsec taper for continuum image  
  > "We therefore generated a $1^{\prime \prime}$ tapered image" (4.3 Rest-frame 500$\mu$m continuum)
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: Continuum flux from Gaussian fit subtracted directly from the line flux; uv-space UV_SUBTRACT check agrees to <5%  
  > "We directly subtracted this continuum flux from the line integrated flux derived with the Gaussian fit" (Footnote 6)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.62x0.40 arcsec  
  > "resulting in a synthesized beam of FWHM $\theta_{\rm beam}$=0$\ensuremath{''}$62$\times$0$\ensuremath{''}$40" (4.1 Observations)
- final rms: _not stated_

### Inherited from earlier work

- Resolved HST SED-fitting maps of mass, SFR and extinction  
  > "we derived resolved colour maps and maps of stellar mass, SFR and dust extinction for UDF6462 following the approach in (cite: Cibinel+15)" (3.1 Resolved maps of physical parameters) [from (cite: Cibinel+15)]
- Clump identification approach  
  > "we followed an approach similar to that outlined in (cite: Guo+12)" (3.2 Clump identification) [from (cite: Guo+12)]
- IR SED fitting with Draine & Li models and gas-to-dust method  
  > "following the approach described in (cite: Magdis+2011; Magdis+12)" (2.2 Integrated stellar mass and star formation rate estimates) [from (cite: Magdis+2011; Magdis+12)]
- 6 GHz flux measurement with PYBDSM  
  > "following the Gaussian fitting approach with the PYBDSM software described in (cite: Rujopakarn+16)" (2.2 Integrated stellar mass and star formation rate estimates) [from (cite: Rujopakarn+16)]
- IR and deblended photometry  
  > "based on new, improved deblending algorithms (see (cite: Liu+17), for fluxes at $\lambda$ $\leq$ 250 $\mu$m and Wang et al., in preparation" (2.1 Multiwavelength data) [from (cite: Liu+17); Wang et al., in preparation]

### Not stated but needed to reproduce (our reading)

- Per-execution calibrators and CASA/pipeline version
- Channel/velocity range used for continuum and line-free channels
- Number of pixels, cell size and clean parameters for GILDAS maps
- Exact UV_FIT initial guesses and fixed parameters per clump
- Details of simobserve configuration and noise model
- Wang et al. in preparation 500 um photometry
- Flux calibrators and ALMA flux scale uncertainty

## Analysis recipe

1. **Calibrate and image ALMA data**: Standard pipeline calibration in CASA; imaging and analysis with GILDAS, natural weighting  
  > "Calibration of the ALMA raw data was carried out using Common Astronomy Software Applications (cite: McMullin+07) and the standard ALMA pipeline." (4.1 Observations)
   - software: CASA, GILDAS
   - fitting: _not stated_
   - validation: _not stated_
2. **Measure nuclear CO(5-4) flux, size and line width**: uv-plane elliptical Gaussian fit with UV_FIT over 1680 km/s; spectrum from Gaussian with fixed parameters; Gaussian fit to spectrum  
  > "We extracted the total CO(5-4) flux associated with UDF6462 through $uv$-plane fitting with an elliptical Gaussian model, using the GILDAS task UV_FIT." (4.2.1 Nuclear Region)
   - software: GILDAS UV_FIT
   - parameter: Delta v ~ 1680 km/s  
  > "The fitting was performed over a velocity range $\Delta$*v* $\simeq$ 1680 km s$^{-1}$" (4.2.1 Nuclear Region)
   - fitting: Free-parameter elliptical Gaussian with initial guesses at optical peak and beam  
  > "As initial guesses for the model centre and size, we assumed the coordinates of the peak in the optical images and the ALMA synthesized beam, respectively, and let the parameters vary freely." (4.2.1 Nuclear Region)
   - validation: _not stated_
3. **Extract clump spectra, stack and derive upper limits**: Fit visibilities with multiple Gaussians at fixed clump positions/sizes on the residual uv-table after subtracting the nuclear model; velocity-shifted weighted mean stack; 3 sigma upper limits assuming 100 km/s FWHM  
  > "the extraction was performed on the residual $uv$-table obtained after subtracting the best-fitting elliptical Gaussian model for the nuclear region described above." (4.2.2 Clumps)
   - software: GILDAS
   - parameter: Assumed clump line FWHM 100 km/s; mean clump FWHM 0.18 arcsec for stack  
  > "resulting in an FWHM of the order 100 km/s, which we assume to be the typical clump line width" (4.2.2 Clumps)
   - fitting: _not stated_
   - validation: Median stacking without velocity shift and image-plane stacking give consistent results  
  > "consistent results are obtained when performing median stacking" (4.2.2 Clumps)
4. **Measure rest-frame 500 um continuum**: uv-plane elliptical Gaussian fit of untapered visibilities; second fit tied to CO geometry; stack at clump positions  
  > "From a $uv$-plane modelling of the (untapered) visibilities with an elliptical Gaussian we obtain a total flux density of $S_{\rm cont}$ = (106.7$\pm$26.2)$\mu$Jy." (4.3 Rest-frame 500$\mu$m continuum)
   - software: GILDAS
   - fitting: _not stated_
   - validation: _not stated_
5. **Fit IR SED and derive L_IR, SFR, dust and gas mass**: Draine & Li fit to IR+radio photometry including ALMA 1300 um; gas from dust mass via metallicity-dependent gas-to-dust ratio  
  > "fitting the IR (3.6$\mu$m to 350$\mu$m) and radio photometry of UDF6462 with the (cite: Draine_Li_2007) models" (2.2 Integrated stellar mass and star formation rate estimates)
   - assumption: delta_GDR ~ 120 from 12+log(O/H)=8.53; Kennicutt 1998 L_IR-SFR, Chabrier IMF  
  > "We find a ratio $\delta_{\rm GDR}$ $\simeq$ 120 for UDF6462." (5.3.1 Gas mass from sub-mm continuum)
   - fitting: _not stated_
   - validation: Other SED codes and templates give results within ~0.1 dex  
  > "Very similar results (within $\sim$ 0.1 dex) are obtained when fitting the SED using other commonly used codes" (2.2 Integrated stellar mass and star formation rate estimates)
6. **Derive clump masses and SFRs from HST**: Pixel-by-pixel SED fitting with CSF Bruzual & Charlot templates and Calzetti law; clump detection with SExtractor on residuals; multiple photometric/GALFIT approaches averaged  
  > "we used CSF models with ages between 100 Myr and 2 Gyr and a solar metallicity" (3.1 Resolved maps of physical parameters)
   - software: SExtractor, GALFIT
   - parameter: Clumps: >=5 pixels above 5 sigma residual  
  > "sources of at least 5 pixels with a residual flux above the 5$\sigma$ level were identified as clumps" (3.2 Clump identification)
   - assumption: E(B-V) 0 to 0.9 mag, Calzetti law  
  > "with $E(B-V)$ ranging between 0 and 0.9 mag" (3.1 Resolved maps of physical parameters)
   - fitting: _not stated_
   - validation: Compared SED-based SFR profiles with the radio profile  
  > "we compare in Fig. [14](#fig:App:SFRProfiles) the SFR density profile from the pixel-by-pixel SED fitting with that inferred from the VLA, dust-free radio map" (7.1 Comparison of resolved SFR maps)
7. **Convert CO(5-4) to molecular gas mass and compute SFE and gas fractions**: L'CO(5-4) converted with R51 and alpha_CO; average of MS and SB assumptions for nucleus; simulation-motivated R51=0.6 and alpha_CO=2.9 for clumps  
  > "The average of these two estimates yield a molecular gas mass equal to $M_{\rm mol, nuc}$ = $(1.9\pm1.6)\times 10^{10}\mbox{$M_{\odot}$}$" (5.3.2 Molecular gas mass from CO(5-4) emission)
   - assumption: MS: R51=0.23, alpha_CO=4.87; SB: R51=0.6, alpha_CO=1  
  > "For the SB case, we instead used $\alpha_{\rm CO}$ = 1 and an excitation correction equal to $R_{51}$ = 0.6" (5.3.2 Molecular gas mass from CO(5-4) emission)
   - fitting: _not stated_
   - validation: Range of R51 and alpha_CO explored  
  > "we carry out the calculation of $M_{\rm mol}$ for a range of plausible values for $R_{51}$ and $\alpha_{\rm CO}$" (5.3.2 Molecular gas mass from CO(5-4) emission)
8. **Dynamical mass and gas mass of nucleus**: Average of virial and high-z clumpy disc dynamical mass estimators; subtract stellar and dark matter  
  > "We use the average of these two estimates $M_{\rm dyn} (r<r_{\rm CO})$ = (5.36$\pm$2.0)$\times10^{10}$ $\mbox{$M_{\odot}$}$ as our fiducial value" (5.3.3 Dynamically-inferred gas mass)
   - assumption: inclination 63 deg; f_star~0.5; M_dark between 0 and 0.25 M_dyn  
  > "$M_{\rm dark}$ = 0, for a baryon-dominated nucleus" (5.3.3 Dynamically-inferred gas mass)
   - fitting: _not stated_
   - validation: _not stated_
9. **Test CO size bias with simulated observations**: Simulate observations of an extended UV-SFR-based CO model, process like real data, refit size  
  > "We fit the simulated $uv$-plane with a Gaussian source, using the UV_FIT task as done for the real observation" (9 Tests on Simulated Images)
   - software: CASA simobserve, GILDAS UV_FIT
   - fitting: _not stated_
   - validation: Recovered intrinsic ~1 arcsec size of the model  
  > "we were able to recover the intrinsic $\sim$ $1^{\prime \prime}$ size of the input model and its total flux" (5.1 Star formation, cold dust and CO(5-4) distribution)

## Software

- **CASA** : Calibration and simobserve simulations  
  > "Calibration of the ALMA raw data was carried out using Common Astronomy Software Applications (cite: McMullin+07)" (4.1 Observations)
- **GILDAS** : Imaging, UV_FIT, UV_SUBTRACT, analysis  
  > "mostly performed with the GILDAS software package" (4.1 Observations)
- **GALFIT** : Galaxy and clump structural fits  
  > "modelling the galaxy surface brightness with GALFIT" (3.2 Clump identification)
- **SExtractor** : Clump detection  
  > "run the Source Extractor code (SEXTRACTOR, (cite: Bertin_Arnouts_1996)) on the residual image" (3.2 Clump identification)
- **PYBDSM** : 6 GHz flux density  
  > "measured following the Gaussian fitting approach with the PYBDSM software" (2.2 Integrated stellar mass and star formation rate estimates)
- **decompir** : AGN/star-forming IR SED decomposition  
  > "the public IDL code decompir for the fitting" (2.3 Quantifying the AGN contribution)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Nuclear CO(5-4) integrated intensity | 308.1 | 54.6 | mJy km/s | 2 | $(308.1\pm54.6)$ mJy km s$^{-1}$ |
| L'CO(5-4) of nuclear region | 1.65e9 | 0.39e9 | K km/s pc^2 | 2 | (1.65\pm0.39)\times 10^9{\rm \,K\,km\,s^{-1}\,pc^{-2}} |
| CO(5-4) line FWHM | 394 | 50 | km/s | 2 | $\Delta$*v*$_{\rm FWHM}$ = (394$\pm$50) km/s |
| Individual clump 3-sigma CO(5-4) upper limits | 19-25 | not stated | mJy km/s | 3 | range between $I_{\rm CO(5-4),\rm ul}$ = 19 and 25 mJy km s$^{-1}$ |
| Stacked clump CO(5-4) upper limit | 9 | not stated | mJy km/s | 3 | $I_{\rm CO(5-4),\rm ul.  stack}$ = 9 mJy km s$^{-1}$ |
| Total 1300 um continuum flux | 106.7 | 26.2 | uJy | 4 | $S_{\rm cont}$ = (106.7$\pm$26.2)$\mu$Jy |
| Galaxy L_IR | 33e10 | 9e10 | Lsun | 5 | $L_{\rm IR}$= (33$\pm$9)$\times10^{10}\mbox{$L_{\odot}$}$ |
| Galaxy gas mass from SED | 2.0e10 | +4.4/-1.4 e10 | Msun | 5 | $M_{\rm gas, gal}$ = $2.0^{+4.4}_{-1.4}\times 10^{10}\mbox{$M_{\odot}$}$ |
| Galaxy depletion time | 0.51 | not stated | Gyr | 5 | a depletion time-scale $\tau_{\rm depl, gal}$ = 0.51 Gyr |
| Nuclear molecular gas mass from CO | 1.9e10 | 1.6e10 | Msun | 7 | $M_{\rm mol, nuc}$ = $(1.9\pm1.6)\times 10^{10}\mbox{$M_{\odot}$}$ |
| Average clump gas mass from stack | 2e8 | range 1-6e8 | Msun | 7 | average clump gas mass of $M_{\rm mol, cl}$ $\simeq$ $2\times 10^{8}\mbox{$M_{\odot}$}$ |
| Average clump gas fraction from stack | ~30% (20-60%) | not stated | dimensionless | 7 | gas fraction of $f_{\rm gas, cl}$ $\simeq$ 30% (20-60%) |
| Nuclear dynamical-based gas mass | 3.3e10 | +2.7/-2.2 e10 | Msun | 8 | $M_{\rm gas, nuc}$ = $3.3^{+2.7}_{-2.2} \times 10^{10}\mbox{$M_{\odot}$}$ |

## Qualitative findings

- CO(5-4) is more centrally concentrated than SFR tracers and dust, and this is not caused by observational bias  
  > "From the analysis of simulated ALMA observations, we conclude that this difference is intrinsic and not caused by observational biases." (6 Summary and Discussion)

## Claim tuples

- H: Do UV-bright clumps show CO(5-4) emission? | E: uv-plane extraction of clump spectra and stacking | R: No detection; stack upper limit 9 mJy km/s | F: Clumps contribute <~18% of CO(5-4) emission, below their 10-40% SFR share | **supported**
- H: Clumps have high SFE or gas fractions above their host | E: Convert stack limits to gas mass with simulation-motivated R51 and alpha_CO | R: f_gas ~30% (20-60%), tau_depl ~0.15 Gyr | F: Clumps not more gas-rich than host; SFE may be high, but dependent on SFR and conversion assumptions | **partially**
- H: CO(5-4) distribution follows that of star formation and dust | E: uv-plane size fit and simulated observations | R: CO ~0.5 arcsec vs ~1 arcsec SFR and ~2 arcsec dust | F: CO(5-4) is intrinsically more concentrated | **supported**
- H: Nuclear region lies on the L_IR-L'CO(5-4) relation | E: Compare nuclear L'CO and radio SFR with literature relations | R: Falls on the correlations | F: Consistent with ongoing nuclear star formation | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: CO(5-4) traces dense gas actually forming stars, a good tracer of clump star formation  
  > "the CO(5-4) transition is particularly advantageous for studying star formation occurring in a dense, clumpy medium" (1 Introduction)
- Alternative: Tau-model SFH maps rejected for clump properties due to noise and step-like SFH variations  
  > "this map is not considered further for deriving clump properties" (7.1 Comparison of resolved SFR maps)
- How they decided it was enough: _not stated_
- Limitation (authors): Clump SFRs vary by up to ~1 dex between methods and clump R51/alpha_CO are poorly constrained  
  > "the SFR estimates for individual clumps can vary by up to $\sim$1 dex" (6.1 Scaling relations for giant clumps)
- Caveat (inferred, ours): Clump gas mass limits depend on assumed R51, alpha_CO and line width
- Caveat (inferred, ours): Non-detection depth only probes a factor of ~10 above typical clump SFR; low-SFR scenario makes it uninformative
- Caveat (inferred, ours): HST-ALMA astrometric shift correction affects clump positions used in uv extraction
- Caveat (inferred, ours): Single galaxy limits generality

## Reproducibility

- Data public (paper): ALMA data acknowledged by project code; public status not explicitly stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2013.1.01271.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: CASA version
- Missing: GILDAS imaging parameters
- Missing: Clump uv-fit details
- Missing: Wang et al. photometry beyond 250 um
- Data volume (inferred): ~50-100 GB raw for six executions in Band 6
- Score (inferred): 3/5, Data and main steps are described with numbers, but imaging parameters and calibration details are missing and GILDAS uv-fitting is hard to replicate exactly.
- Rediscovery candidate: no, Recipe incomplete (version, imaging parameters) and relies on much ancillary non-ALMA data and inherited methods.

## Links

- Method: (cite: Cibinel+15) (Resolved HST SED fitting maps)
- Method: (cite: Magdis+2011; Magdis+12) (IR SED fitting and gas-to-dust method)
- Method: (cite: Daddi+15) (CO(5-4)-IR relation and excitation correction)
- Companion: (cite: Rujopakarn+16) (VLA 6 GHz and ALMA HUDF astrometry)
- Companion: (cite: Bournaud+08) (SINFONI kinematics of UDF6462)
- Companion: (cite: Dunlop+17) (ALMA HUDF 1.3 mm survey)
- Related: HUDF
- Related: CANDELS
- Related: 3D-HST
- Related: GOODS-Herschel
- Related: HerMES

## Checks

```json
{
 "quotes": 91,
 "quotes_ok": 91,
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
  "facts": 101,
  "stated": 68,
  "rate": 0.673
 },
 "evidence_ok": true
}
```
