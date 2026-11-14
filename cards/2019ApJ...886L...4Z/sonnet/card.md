# Discovery of a Photoionized Bipolar Outflow toward the Massive Protostar G45.47+0.05

`2019ApJ...886L...4Z` | The Astrophysical Journal Letters 2019 | first author: Zhang, Yichen | arXiv: 1910.04271 | DOI: 10.3847/2041-8213/ab5309

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation
- Question: Does the massive protostar G45 drive a photoionized (photoevaporative) bipolar outflow, and what do its properties imply for radiation feedback and ongoing accretion?  
  > "Massive protostars generate strong radiation feedback, which may help set the mass they achieve by the end of the accretion process." (abstract)
- Target **G45.47+0.05**: coordinates _not stated_; z/distance d = 8.4 kpc  
  > "The protostar G45.47+0.05 (hereafter G45; $d=8.4~\mbox{kpc}$, (cite: Wu19))" (Introduction); distance from Wu et al. 2019  
  > "The protostar G45.47+0.05 (hereafter G45; $d=8.4~\mbox{kpc}$, (cite: Wu19))" (Introduction)

## Data provenance

- ALMA projects: 2015.1.01454.S, 2017.1.00181.S
- bands: ALMA 1.3 mm (plus VLA 7 mm)  
  > "ALMA 1.3 mm observations were performed on 2016 April 24, 2016 September 4 and 2017 November 2" (Observations)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: 2 GHz  
  > "using the continuum data (bandwidth of 2 GHz)" (Observations)
- arrays: _not stated_
- configurations: C36-3, C36-6, C43-9 (C3, C6, C9)  
  > "with C36-3, C36-6 and C43-9 configurations (hereafter C3, C6 and C9)" (Observations)
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: 3.6, 7.3 and 17.7 min  
  > "with on-source integration times of 3.6, 7.3 and 17.7 min, respectively" (Observations)
- observing dates: 2016 Apr 24, 2016 Sep 4, 2017 Nov 2  
  > "ALMA 1.3 mm observations were performed on 2016 April 24, 2016 September 4 and 2017 November 2" (Observations)
- pi or archival as stated: _not stated_
- Line: H30alpha recombination line (231.90093 GHz)
- Line: He30alpha recombination line (231.99543 GHz)
- Other facility **VLA**: 7 mm continuum, A configuration, project 14A-113  
  > "The VLA 7 mm observation was performed in 2014 with A configuration and two 4-GHz basebands centered at 41.9 and 45.9 GHz (project ID: 14A-113)." (Observations)
- External data: VLA 7 mm data details, and 1.3 cm fluxes/SED  
  > "Details of the VLA data is summarized by (cite: Rosero19)." (Observations) [from (cite: Rosero19)]
- External data: Infrared SED fitting: inclination i>55 deg, mass ~20-50 Msun  
  > "a mass of $\sim20-50~M_\odot$ ((cite: Debuizer17)), based on infrared spectral energy distribution (SED) fitting" (Introduction) [from (cite: Debuizer17)]
- Simulation/model as data: Free-free radiative transfer model grid (Tanaka16 code) of isothermal ionized bipolar outflow cavities  
  > "Free-free RT calculations ((cite: Tanaka16)) are performed to produce model images at 1.3 and 7 mm." (Model Fitting of 1.3 and 7 mm Free-free Emissions)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Titan, J2148+0657, J2000-1748  
  > "Titan, J2148+0657 and J2000-1748 were used for flux calibration" (Observations)
- flux scale uncertainty: _not stated_
- self calibration: Done separately for each configuration on continuum, applied to line data  
  > "Self-calibration was performed for the three configuration data separately using the continuum data (bandwidth of 2 GHz), and applied to the line data." (Observations)

### Imaging

- task: CASA tclean  
  > "Images are made with the CASA task tclean using robust weighting" (Observations)
- deconvolver: _not stated_
- weighting robust: robust = 0.5  
  > "with the robust parameter of 0.5" (Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: C3+C6 and C3+C6+C9 combined images  
  > "More extended emissions are recovered by combining with more compact configuration data (panels c and d)." (1.3 and 7 mm continuum)
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- VLA 7 mm data processing  
  > "Details of the VLA data is summarized by (cite: Rosero19)." (Observations) [from (cite: Rosero19)]
- Free-free radiative transfer code  
  > "Free-free RT calculations ((cite: Tanaka16)) are performed" (Model Fitting of 1.3 and 7 mm Free-free Emissions) [from (cite: Tanaka16)]
- Synchrotron k=40 adopted  
  > "We also adopt $k=40$ following (cite: Carrasco10) and (cite: Sanna19)." (Estimating the Magnetic Field Strength from Synchrotron Emission) [from (cite: Carrasco10; Sanna19)]

### Not stated but needed to reproduce (our reading)

- Image sizes, cell sizes, deconvolver, masking and clean thresholds
- Line-free channels and continuum subtraction method
- Self-calibration solution intervals and number of iterations
- CASA version and whether pipeline used
- Channel width for H30alpha cubes
- Final beams (only in figure) and rms noise
- Spectral window setup
- VLA calibration/imaging details
- Model grid sampling steps for chi2 minimization
- Departure coefficient interpolation for maser estimate

## Analysis recipe

1. **Calibrate, self-calibrate and image ALMA data**: CASA calibration, per-configuration continuum self-cal applied to lines, tclean imaging  
  > "The data were calibrated and imaged in CASA ((cite: McMullin07))." (Observations)
   - software: CASA
   - parameter: robust = 0.5  
  > "with the robust parameter of 0.5" (Observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **Spectral index map and dust mass**: Spectral index from 7 mm and 1.3 mm intensities after aligning 7 mm image; dust mass from extended flux difference  
  > "we manually shift the 7 mm image by 7 mas in the R.A. direction and 13 mas in the Dec. direction" (1.3 and 7 mm continuum)
   - assumption: kappa_1.3mm=0.899 cm2/g, gas-to-dust 141, T=30 or 60 K  
  > "we adopt a dust opacity of $\kappa_\mathrm{1.3mm}=0.899~\mathrm{cm}^2~\mathrm{g}^{-1}$ ((cite: Ossenkopf94)) and a gas-to-dust mass ratio of 141" (1.3 and 7 mm continuum)
   - fitting: _not stated_
   - validation: _not stated_
3. **Quantify H30alpha maser via integrated line-to-continuum ratio**: ILTC map compared with LTE optically thin value from formula in Wilson et al.  
  > "Assuming a characteristic ionized gas temperature of $T_\mathrm{e}=10^4\:{\rm K}$, $\int_v I_{\mathrm{H30}\alpha}
dv/I_\mathrm{1.3~mm}=81\:\mbox{km s}^{-1}$" (H30alpha line)
   - assumption: N(He+)/N(H+)=0.08, Te=1e4 K  
  > "typically $N\left(\mathrm{He}^+\right)/N\left(\mathrm{H}^+\right)=0.08$" (H30alpha line)
   - fitting: _not stated_
   - validation: _not stated_
4. **Fit free-free model to 1.3 and 7 mm images**: Grid of isothermal bipolar cavity models with density power law n~r'^-2; minimize chi2_tot over Te, n0, varpi0, theta_w  
  > "we minimize $\chi^2_\mathrm{tot}\equiv
(\chi^2_\mathrm{1.3mm}+\chi^2_\mathrm{7mm})/2$ by varying the free parameters within reasonable ranges" (Model Fitting of 1.3 and 7 mm Free-free Emissions)
   - parameter: theta_w,sky fixed at 40 deg; PA 3 deg; Te 5e3-2e4 K; n0 3e6-3e8 cm-3; varpi0 30-300 au; theta_w 20-40 deg  
  > "we fix $\theta_{w,\mathrm{sky}}=40^\circ$ based on the observed 1.3 mm continuum morphology" (Model Fitting of 1.3 and 7 mm Free-free Emissions)
   - assumption: Each ion has single charge  
  > "Here we only consider a situation that each ion has only one charge (1$e$)" (Model Fitting of 1.3 and 7 mm Free-free Emissions)
   - fitting: Grid chi2 minimization over regions with I_obs>0.1 I_center  
  > "Here the integration is over a region with $I_\mathrm{obs}>0.1 I_\mathrm{obs,center}$ at each wavelength." (Model Fitting of 1.3 and 7 mm Free-free Emissions)
   - validation: Compared with images, spectral index, SED and profiles; model fluxes within 5% of observed  
  > "The model fluxes are slightly lower (within $5\%$) than the observed values." (Model Fitting of 1.3 and 7 mm Free-free Emissions)
5. **Derive ionizing photon rate, mass loss rate and stellar mass**: S computed from model density; mass from ZAMS and protostellar evolution relations; outflow rate with V_out=30 km/s  
  > "Panel h shows the mass outflow rates in the model (assuming a velocity of $30~\mbox{km s}^{-1}$" (Model Fitting of 1.3 and 7 mm Free-free Emissions)
   - assumption: All ions H+, total mass 1.4x hydrogen mass  
  > "assuming all the ions are H$^+$ and the total mass is 1.4 times of the hydrogen mass" (Model Fitting of 1.3 and 7 mm Free-free Emissions)
   - fitting: _not stated_
   - validation: Consistent with IR SED mass 20-50 Msun  
  > "These mass estimates are consistent with those estimated from infrared SED fitting" (Model for Free-free Emission)
6. **H30alpha centroid kinematics and dynamical mass**: Gaussian ellipse fits to channels in C9 with peak >10 sigma; linear fits of offset vs velocity; m_dyn=dV^2 dvarpi/(8G sin^2 i)  
  > "The centroid positions are determined by fitting Gaussian ellipses to the H30$\alpha$ emissions observed in the C9 configuration at channels with peak intensities $>10\sigma$." (Determining the H30alpha emission positional centroids.)
   - assumption: Rotating ring; 55<i<90 deg from IR SED  
  > "For $55^\circ<i<90^\circ$ determined by the infrared SED fitting, we obtain $m_\mathrm{dyn}=28-40~M_\odot$." (Dynamics of the Ionized Gas)
   - fitting: Linear fits; errors from beam/(2 S/N) and bandpass phase noise  
  > "the uncertainties in the centroid positions are $\Delta
\theta_\mathrm{centroid}=\sqrt{\Delta \theta_\mathrm{fit}^2+\Delta
  \theta_\mathrm{bandpass}^2}$" (Determining the H30alpha emission positional centroids.)
   - validation: _not stated_
7. **Minimum-energy magnetic field from synchrotron regions**: Classical equipartition formula for regions with alpha<-0.3 and >5 sigma  
  > "We define the synchrotron emission region as the region with intensity spectral indices of $\alpha<-0.3$ and both 1.3 and 7 mm emissions $>5\sigma$." (Estimating the Magnetic Field Strength from Synchrotron Emission)
   - parameter: c12=3.2e6, k=40  
  > "we obtain $c_{12}=3.2\times 10^6$ following (cite: Govoni04)" (Estimating the Magnetic Field Strength from Synchrotron Emission)
   - assumption: All emission in these regions is synchrotron (upper limit)  
  > "Assuming all the 1.3 and 7 mm emissions from these regions are due to synchrotron emission" (Estimating the Magnetic Field Strength from Synchrotron Emission)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : Calibration, self-calibration and imaging (tclean)  
  > "The data were calibrated and imaged in CASA ((cite: McMullin07))." (Observations)
- **IDL Astronomy User's Library** : Listed as software used  
  > "The IDL Astronomy User’s Library" (Software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Best-fit electron temperature | 10,000 | not stated | K | 4 | The best-fit model (minimum $\chi^2_\mathrm{tot}$) has $T_\mathrm{e}\approx10,000\:{\rm K}$ |
| Central electron density n0 | 1.5e7 | not stated | cm^-3 | 4 | $n_0\approx1.5\times 10^7~\mathrm{cm}^{-3}$ |
| Launching region outer radius | 110 | not stated | au | 4 | $\varpi_0\approx110~\mbox{au}$ |
| Ionizing photon rate (probable inclination range) | 1.4-1.8e49 | not stated | s^-1 | 5 | gives a range $1.4 \times
10^{49}~\mathrm{s}^{-1}<S< 1.8 \times 10^{49}~\mathrm{s}^{-1}$ |
| Mass outflow rate | (2-3.5)e-5 (v/30 km/s) | not stated | Msun/yr | 5 | The best-fit models have rates from $2\times 10^{-5}
(v/30~\mbox{km s}^{-1})~M_\odot~\mathrm{yr}^{-1}$ to $3.5\times 10^{-5} |
| Dynamical mass | 28-40 | not stated | Msun | 6 | we obtain $m_\mathrm{dyn}=28-40~M_\odot$ |
| Rotation velocity gradient | 7.0 | 0.21 | km/s/mas | 6 | The fitted velocity gradient within this velocity range is $7.0\pm0.21~\mbox{km s}^{-1}~\mathrm{mas}^{-1}$ |
| Peak ILTC ratio of H30alpha | ~300 (LTE 81) | not stated | km/s | 3 | the measured ILTC ratio is $>200~\mbox{km s}^{-1}$ and reaching $\sim300~\mbox{km s}^{-1}$ |
| Minimum-energy B field (north, south) | 15 and 17 | not stated | mG | 7 | These values give $B_\mathrm{min}=15$ and 17 mG in the northern and southern regions, respectively. |
| Total 1.3 mm flux within 5" (C3+C6) | 0.77 | not stated | Jy | 2 | The total 1.3 mm continuum flux $>3\sigma$ within $5\ensuremath{''}$ from the central source measured from the C3+C6 image is 0.77 Jy. |

## Qualitative findings

- H30alpha shows strong maser amplification concentrated along the disk plane  
  > "the strong maser effect is concentrated toward the east and west of the central source along a direction nearly perpendicular to the outflow axis" (H30alpha line)

## Claim tuples

- H: G45 hosts a photoionized photoevaporative bipolar outflow | E: Free-free model fit to 1.3 and 7 mm images | R: Te~1e4 K, n0~1.5e7 cm-3, varpi0~110 au | F: The ionized outflow is a photoevaporation flow from a disk | **supported**
- H: H30alpha is masing | E: Compare ILTC ratio to LTE value | R: ILTC up to ~300 vs 81 km/s | F: Strong maser amplification | **supported**
- H: Mass of the driving source | E: Ionizing photon rate and H30alpha centroid kinematics | R: 28-48 Msun and 28-40 Msun | F: Protostar mass ~30-50 Msun | **supported**
- H: A jet is embedded in the ionized outflow and accretion continues | E: Spectral index map and equipartition field | R: Negative indices -0.5 to -0.2; Bmin 15-17 mG | F: Possible jet with non-thermal emission; accretion likely ongoing | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: MHD disk wind rejected for the dense ~1e7 cm-3 outflow  
  > "Such high density suggests that this outflow is not an MHD disk wind, but instead a photoevaporative outflow launched from the disk." (Model for Free-free Emission)
- How they decided it was enough: _not stated_
- Limitation (authors): Opening angle and inclination weakly constrained by the model  
  > "The model constraints on the true outflow opening angle (which depends on the inclination) are weak." (Model for Free-free Emission)
- Limitation (authors): Detailed non-LTE H30alpha modeling not done  
  > "detailed modeling of the H30$\alpha$ emission including the maser effects is out of the scope of this paper" (Model for Free-free Emission)
- Caveat (inferred, ours): Simple isothermal geometry degenerate with inclination
- Caveat (inferred, ours): Free-free vs dust contribution at 1.3 mm uncertain
- Caveat (inferred, ours): Negative spectral indices may be affected by VLA sidelobes and image alignment (manual shift)
- Caveat (inferred, ours): Synchrotron field is a minimum-energy estimate with assumed k

## Reproducibility

- Data public (paper): ALMA project IDs given; archival  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2015.1.01454.S, and ADS/JAO. ALMA#2017.1.00181.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Imaging parameters beyond robust
- Missing: Self-cal details
- Missing: Model grid and RT code settings
- Missing: VLA reduction
- Data volume (inferred): ~50-200 GB for three ALMA configurations plus VLA
- Score (inferred): 3/5, Public data and clear model equations, but imaging and self-calibration details and RT code setup are sparse.
- Rediscovery candidate: no, Key results depend on a custom RT model grid and unstated imaging details.

## Links

- Method: Tanaka, Tan, Zhang 2016, ApJ, 818, 52 (Free-free radiative transfer calculations)
- Method: Rosero et al. 2019, ApJ, 873, 20 (VLA data details)
- Companion: Zhang & Tan 2018, ApJ, 853, 18 (Dust continuum RT model grid for SED)
- Companion: De Buizer et al. 2017, ApJ, 843, 33 (IR SED fitting of G45)
- Related: VLA 14A-113

## Checks

```json
{
 "quotes": 66,
 "quotes_ok": 66,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 10,
 "numeric_problems": 0,
 "fill": {
  "facts": 86,
  "stated": 47,
  "rate": 0.547
 },
 "evidence_ok": true
}
```
