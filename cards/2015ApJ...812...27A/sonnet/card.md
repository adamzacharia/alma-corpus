# ALMA Observations of the Transition from Infall Motion to Keplerian Rotation around the Late-phase Protostar TMC-1A

`2015ApJ...812...27A` | The Astrophysical Journal 2015 | first author: Aso, Yusuke | arXiv: 1508.07013 | DOI: 10.1088/0004-637X/812/1/27

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, protoplanetary_disks
- Question: How does infall motion in the envelope of the Class I protostar TMC-1A transition to Keplerian rotation in the disk, and what does this imply for Keplerian disk formation?  
  > "In order to investigate the expected transition from the infall motion to Keplerian rotation, we made observations of the Class I protostar TMC-1A (IRAS 04365+2535)" (Introduction)
- Target **TMC-1A (IRAS 04365+2535)**: coordinates map center RA(J2000)=4h39m35.010s, Dec=25d41m45.500s  
  > "our target TMC-1A is in the Taurus molecular cloud, which is one of the closest star-forming regions ($d=140$ pc)" (Introduction); "The coordinate of map center is $\alpha$(J2000)=4$^{\rm h}$39$^{\rm m}$35$^{\rm s}\!\!$.010" (2 ALMA Observations); z/distance d = 140 pc  
  > "our target TMC-1A is in the Taurus molecular cloud, which is one of the closest star-forming regions ($d=140$ pc)" (Introduction); "The coordinate of map center is $\alpha$(J2000)=4$^{\rm h}$39$^{\rm m}$35$^{\rm s}\!\!$.010" (2 ALMA Observations); distance from Taurus molecular cloud distance (no citation given)  
  > "our target TMC-1A is in the Taurus molecular cloud, which is one of the closest star-forming regions ($d=140$ pc)" (Introduction); "The coordinate of map center is $\alpha$(J2000)=4$^{\rm h}$39$^{\rm m}$35$^{\rm s}\!\!$.010" (2 ALMA Observations)

## Data provenance

- ALMA projects: 2011.0.00210.S
- bands: Band 6 (1.3 mm)  
  > "1.3-mm continuum emission in Band 6 were observed for 63 minutes (on source)" (2 ALMA Observations)
- frequencies and spectral setup: FDM, four spectral windows, each 3,840 channels over 234 MHz  
  > "we configured the correlator in Frequency Division Mode (FDM) for four spectral windows. Each spectral window has 3,840 channels covering 234 MHz bandwidth." (2 ALMA Observations)
- continuum bandwidth: ~920 MHz, centered at 225 GHz, from emission-free channels  
  > "The total integrated frequency width of the continuum map is $\sim 920$ MHz." (2 ALMA Observations)
- arrays: ALMA Cycle 0, 23 antennas  
  > "The configuration is “extended” with 23 antennas." (2 ALMA Observations)
- configurations: _not stated_
- baselines: 16 m to 285 m (11.7-208.7 kλ in C18O)  
  > "Extended configuration covers projected uv distances from 16 m to 285 m (11.7$-$208.7 k$\lambda$ in C$^{18}$O $J=2-1$)." (2 ALMA Observations)
- angular resolution: 1.06x0.90 arcsec C18O; 1.02x0.90 12CO; 1.01x0.87 continuum  
  > "$1\hbox{$.\!\!^{\prime\prime}$}06\times 0\hbox{$.\!\!^{\prime\prime}$}90$ for the C$^{18}$O line" (2 ALMA Observations)
- max recoverable scale: 50% flux resolved out beyond 7.7 arcsec (~1100 AU)  
  > "This minimum baseline resolves out more than 50% of the flux if a structure is extended more than $7\hbox{$.\!\!^{\prime\prime}$}7$" (2 ALMA Observations)
- sensitivity: C18O rms 4.6 mJy/beam (no emission), 7.1 (detected channel); continuum 0.96 mJy/beam  
  > "Noise level (detected channel) | 20 mJy$\,$beam$^{-1}$ | 7.1 mJy$\,$beam$^{-1}$ | 0.96 mJy$\,$beam$^{-1}$" (Table 1)
- time on source: 63 minutes  
  > "were observed for 63 minutes (on source)" (2 ALMA Observations)
- observing dates: November 6, 2012  
  > "We observed our target, TMC-1A during Cycle 0 using the Atacama Large Millimeter/Submillimeter Array (ALMA) on November 6, 2012." (2 ALMA Observations)
- pi or archival as stated: _not stated_
- Line: 12CO J=2-1 (230.5380 GHz)
- Line: C18O J=2-1 (219.5604 GHz)
- External data: Dust temperature Tc=28 K from SED fit; also used as C18O excitation temperature  
  > "a dust temperature $T_{c}=28$ K (cite: ch1998), which is a temperature estimated from a fitting to the SED of TMC-1A" (3.1 Continuum and 12CO) [from (cite: ch1998)]
- External data: Dust opacity kappa(1 THz)=10.0 cm2/g  
  > "assuming a standard opacity coefficient $\kappa (1\ {\rm THz})=10.0\ {\rm cm}^{2}\,{\rm g}^{-1}$ (cite: be1990)" (3.1 Continuum and 12CO) [from (cite: be1990)]
- External data: C18O abundance X=3.0e-7 relative to H2  
  > "the abundance of C$^{18}$O relative to H$_{2}$ of $X({\rm C^{18}O})=3.0\times 10^{-7}$ (cite: fr1982)" (3.2 C18O J=2-1) [from (cite: fr1982)]
- External data: Systemic velocity 6.4 km/s  
  > "The systemic velocity of TMC-1A was measured at $V_{\rm LSR}=6.4\ {\rm km\ s^{-1}}$ by (cite: te1989)." (Introduction) [from (cite: te1989)]
- External data: Lbol=2.7 Lsun and Tbol=118 K  
  > "Its bolometric luminosity $L_{\rm bol}=2.7\ L_{\odot}$ and bolometric temperature $T_{\rm bol}=118$ K (cite: kr2012)" (Introduction) [from (cite: kr2012)]
- External data: Parameters of other protostars with Keplerian disks (Table 3)  
  > "Parameters of Keplerian disks around protostars" (Table 3) [from refs 1-17 in Table 3 (e.g. oh2014, ye2014, ta2014, mu2013)]
- Simulation/model as data: Flattened-envelope (FE) and spherical-envelope (SE) models of infalling envelope plus Keplerian disk, simulated with simobserve and compared with observed PV diagrams  
  > "we use the CASA task $simobserve$ to include the spatial filtering." (5.2 Nature of the infall motion)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Callisto; delivered intensities multiplied by 0.85 to correct Butler-Horizons-2010 to Butler-JPL-2012  
  > "Following the value (Callisto: $-0.15$, 241 GHz), we multiplied the delivered intensities by 0.85." (2 ALMA Observations)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA CLEAN  
  > "The observed visibilities were Fourier transformed and CLEANed with Common Astronomy Software Applications (CASA)." (2 ALMA Observations)
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 0.5  
  > "we adopted Briggs weighting with the robust parameter of 0.5" (2 ALMA Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: CLEAN boxes enclosing only positive emission in dirty maps  
  > "We also set CLEAN boxes to enclose only positive emission in dirty maps." (2 ALMA Observations)
- multiscale scales: _not stated_
- continuum subtraction: continuum map made from emission-free channels  
  > "Emission-free channels are used to make the continuum map centered at 225 GHz." (2 ALMA Observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: 2 channels binned; 122 kHz = 0.16 km/s (12CO), 0.17 km/s (C18O)  
  > "binned 2 channels thus the frequency (velocity) resolution in this paper is 122 kHz" (2 ALMA Observations)
- final beam: 1.06x0.90 arcsec (C18O), 1.02x0.90 (12CO), 1.01x0.87 (continuum)  
  > "Synthesized beam (P.A.)" (Table 1)
- final rms: C18O 7.1 mJy/beam in detected channels; continuum 0.96 mJy/beam  
  > "Noise level (detected channel) | 20 mJy$\,$beam$^{-1}$ | 7.1 mJy$\,$beam$^{-1}$ | 0.96 mJy$\,$beam$^{-1}$" (Table 1)

### Inherited from earlier work

- PV mean-position method for rotation profile  
  > "We also note that a similar analysis was performed by (cite: ye2013)." (4.2 Rotation Profile) [from (cite: ye2013)]
- Disk model code  
  > "We use a disk model with a code described in (cite: oh2014)." (4.3 Rotating Disk Models) [from (cite: oh2014); standard disk model (cite: du1994)]
- Inside-out collapse R_kep relation  
  > "the dependence of $R_{\rm kep}$ on $t$ (time) and $M_{*}$ can be expressed as shown in (cite: ye2013)" (5.4 A Possible scenario) [from (cite: ye2013)]

### Not stated but needed to reproduce (our reading)

- MCMC details for disk model fit (sampler, priors, steps, convergence)
- CASA version and calibration pipeline/script version
- CLEAN iterations/threshold, cell and image size
- Line-free channel ranges for continuum
- Exact flux-correction handling beyond the 0.85 factor
- Mask definitions and uncertainty computation for mean positions
- Disk code is from Ohashi et al. 2014, not available here
- Continuum opacity inconsistency (kappa 10 cm2/g at 1 THz vs 1.2 cm2/g in conclusions)

## Analysis recipe

1. **Image and characterise continuum and CO lines**: CLEAN imaging, 2D Gaussian fit to continuum, moment maps of 12CO and C18O  
  > "its deconvolved size can be estimated from a 2D Gaussian fitting" (3.1 Continuum and 12CO)
   - software: CASA
   - assumption: dust kappa(1 THz)=10 cm2/g, beta=1.46, Tc=28 K, gas/dust=100, d=140 pc  
  > "an opacity index $\beta =1.46$, and a dust temperature $T_{c}=28$ K" (3.1 Continuum and 12CO)
   - fitting: _not stated_
   - validation: _not stated_
2. **Measure rotation profile from major-axis PV diagram**: Intensity-weighted mean position per channel (>6 sigma) on PV along disk major axis (PA 73 deg); double power-law chi2 fit in log R - log V  
  > "We performed a $\chi^{2}$ fitting to Fig. [9](#fig:ll) with a double power model" (4.2 Rotation Profile)
   - parameter: mean positions not measured for |dV|<1.2 km/s; Vsys=6.4 km/s  
  > "The mean position is not measured at low velocities ($|\Delta V|<1.2\ {\rm km\ s^{-1}}$)" (4.2 Rotation Profile)
   - assumption: errors: Gaussian for log R, rectangular for log V  
  > "We adopted a Gaussian distribution for the error of $\log R$ and a rectangular distribution for the error of $\log V$" (4.2 Rotation Profile)
   - fitting: chi2 with Monte Carlo dispersal of points within errors; compared with single power law  
  > "The error of each parameter is derived by dispersing the data points randomly within the error bars of $\log R$ and $\log V$." (4.2 Rotation Profile)
   - validation: reduced chi2 1.6 (double) vs 2.0 (single); resolution bias analysed in Appendix  
  > "giving reduced $\chi^{2}=1.6$" (4.2 Rotation Profile)
3. **Fit Keplerian disk model to high-velocity C18O channel maps**: 3D LTE radiative transfer disk model, MCMC chi2 minimisation on pixels >3 sigma with |dV|>2.4 km/s  
  > "We use Markov Chain Monte Carlo (MCMC) method to find the minimum $\chi^{2}$ efficiently." (4.3 Rotating Disk Models)
   - software: MCMC (unnamed code of Ohashi et al. 2014)
   - parameter: fixed i=65 deg, Rin=0.1 AU, Rout=200 AU; 7 free parameters  
  > "fixed | $i$ | $R_{\rm in}$ | $R_{\rm out}$" (Table 2)
   - assumption: LTE, X(C18O)=3.0e-7, zero turbulence, mean molecular weight 2.37 mH, position/PA from continuum, Vsys 6.4  
  > "we assume Local Thermodynamic Equilibrium (LTE) and a typical abundance of C$^{18}$O relative to H$_{2}$, $X($C$^{18}$O$)=3.0\times 10^{-7}$" (4.3 Rotating Disk Models)
   - fitting: reduced chi2 minimisation; uncertainties from range where chi2 < min+1  
  > "The uncertainty of each parameter is defined by the range of the parameter where the reduced $\chi^{2}$ is below the minimum plus one" (4.3 Rotating Disk Models)
   - validation: reduced chi2=0.72; inclination scan 5-85 deg  
  > "Reduced $\chi^{2}=0.72$" (4.3 Rotating Disk Models)
4. **Model infalling envelope plus disk and compare with PV diagrams**: FE models (A-F) with Vr = alpha x free-fall, varied v_out, R_kep, alpha, i, compared with major and minor axis PV diagrams; simobserve for spatial filtering  
  > "Four parameters of the model mentioned above, $v_{\rm out}$, $R_{\rm kep}$, $\alpha$, and the inclination angle of the disk $i$ are changed to reproduce the observed PV diagrams." (5.2 Nature of the infall motion)
   - software: CASA simobserve
   - parameter: best model A: (v_out, R_kep, alpha, i)=(0.85, 100 AU, 0.3, 65 deg)  
  > "$(v_{\rm out},\ R_{\rm kep},\ \alpha,\ i)=(0.85,\ 100\ {\rm AU},\ 0.3,\ 65^{\circ})$" (5.2 Nature of the infall motion)
   - assumption: flattened envelope to 900 AU; envelope surface density beyond 200 AU reduced by factor 2  
  > "the surface density of the envelope at radii more than 200 AU is reduced by a factor of two" (5.2 Nature of the infall motion)
   - fitting: by-eye comparison of models, no formal fit  
  > "such fittings are not performed here. This is because models including the infalling envelope must be compared with the channel maps not only at higher velocities, but also at lower velocities" (Discussion, Nature of the infall motion)
   - validation: spherical envelope (SE) models compared in Appendix; q=-0.5 tested  
  > "It is found that models with a spherical envelope cannot explain the observations better than FE models." (5.2 Nature of the infall motion)
5. **Estimate magnetic field required for slow infall**: Order-of-magnitude radial equation of motion with magnetic pressure and tension at 200 AU  
  > "The magnetic flux density required to make the infall velocity as small as $0.3 V_{\rm ff}$ is estimated from the equation of motion" (5.3 Magnetic Pressure and Tension)
   - assumption: R_curv ~ scale height H; B ∝ rho^(2/3); steady state; gas pressure ignored  
  > "We also assume $B\propto \rho ^{2/3}$" (5.3 Magnetic Pressure and Tension)
   - fitting: _not stated_
   - validation: same estimate at 100 and 300 AU gives similar results  
  > "The same estimations are also done at radii of 100 AU and 300 AU, providing results similar to that at 200 AU." (5.3 Magnetic Pressure and Tension)
6. **Compare with sample of protostars with Keplerian disks**: Correlations of Tbol, Lbol/Lsubmm, M*, R_kep from Table 3 sources; compared with inside-out collapse R_kep ∝ M*^3  
  > "Fig. [13](#fig:rkms) shows correlations between $T_{\rm bol}$ vs the central protostellar masses" (5.4 A Possible scenario)
   - assumption: omega ~ 1 km/s/pc (x2, x0.5), cs=0.19 km/s (10 K)  
  > "with $c_{s}=0.19\ {\rm km\ s^{-1}}$ (i.e., $T_{k} = 10$ K)" (5.4 A Possible scenario)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : Fourier transform and CLEAN imaging; simobserve for model spatial filtering  
  > "The observed visibilities were Fourier transformed and CLEANed with Common Astronomy Software Applications (CASA)." (2 ALMA Observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Continuum deconvolved size | 0.50 x 0.37 arcsec, PA 73 deg | ±0.03, ±0.05 arcsec; ±16 deg | arcsec | 1 | $0\hbox{$.\!\!^{\prime\prime}$}50\pm 0\hbox{$.\!\!^{\prime\prime}$}03\times 0\hbox{$.\!\!^{\prime\prime}$}37\pm 0\hbox{$.\!\!^{\prime\prime}$}05$, P.A.$=73^{\circ}\pm 16^{\circ}$ |
| Continuum total flux density | 182.1 | ±2.6 | mJy | 1 | $182.1\pm2.6\ {\rm mJy}$ |
| Dust mass | 4.2e-4 | ±0.9e-4 | Msun | 1 | $M_{\rm dust}=(4.2\pm 0.9)\times 10^{-4}\ M_{\odot}$ |
| C18O deconvolved size | 3.3 x 2.2 arcsec, PA 67 deg | ±0.1 arcsec; ±2 deg | arcsec | 1 | $3.3^{\prime\prime}\pm 0.1 ^{\prime\prime}\times 2.2^{\prime\prime}\pm 0.1 ^{\prime\prime}$ with P.A.$=67^{\circ}\pm 2^{\circ}$ |
| C18O gas mass | 4.4e-3 | not stated | Msun | 1 | $M_{\rm gas}=4.4\times 10^{-3}\ M_{\odot}$ |
| Double power-law inner index p_in | 0.54 | ±0.14 | dimensionless | 2 | $(67\ {\rm AU},\ 2.4\ {\rm km\ s^{-1}},\ 0.54\pm 0.14,\ 0.85\pm 0.04)$ |
| Outer index p_out | 0.85 | ±0.04 | dimensionless | 2 | $(67\ {\rm AU},\ 2.4\ {\rm km\ s^{-1}},\ 0.54\pm 0.14,\ 0.85\pm 0.04)$ |
| Apparent break radius | 67 AU (corrected ~90 AU) | ~1% | AU | 2 | the real break radius can be estimated to be $\sim 90$ AU from the apparent break radius of 67 AU |
| Disk model M*sin^2 i | 0.56 | ±0.05 | Msun | 3 | $0.56^{+0.05}_{-0.05}\ M_{\odot}$ |
| Disk model rotation index v | 0.53 | ±0.05 | dimensionless | 3 | $0.53^{+0.05}_{-0.05}$ |
| Inclination-corrected dynamical mass | 0.68 | not stated | Msun | 4 | the inclination-corrected central stellar mass is calculated at $M_{*}=0.68\ M_{\odot}$ |
| Infall velocity factor alpha | 0.3 | not stated | dimensionless | 4 | $(v_{\rm out},\ R_{\rm kep},\ \alpha,\ i)=(0.85,\ 100\ {\rm AU},\ 0.3,\ 65^{\circ})$ |
| Mass infall rate | (1.5-3.0)e-6 at R=100-200 AU | not stated | Msun/yr | 4 | $\dot{M}=2\pi RV_{r}\Sigma =(1.5-3.0)\times 10^{-6}\ M_{\odot}\,{\rm yr}^{-1}\ (R=100-200\ {\rm AU})$ |
| Keplerian disk mass (R_kep=100 AU) | 2.5e-3 | not stated | Msun | 4 | $M_{\rm disk}=\int \Sigma 2\pi RdR=2.5\times 10^{-3}\ M_{\odot}$ |
| Magnetic field for slow infall | ~2 | not stated | mG | 5 | the magnetic flux density required for $V_{r}=0.3V_{\rm ff}$ is estimated to be $B\sim 2$ mG |

## Qualitative findings

- C18O traces a flattened rotating/infalling envelope; 12CO traces an outflow at PA -17 deg perpendicular to the continuum disk.  
  > "indicating that C$^{18}$O traces mainly a flattened envelope surrounding the disk and the central protostar" (abstract)

## Claim tuples

- H: The high-velocity C18O emission traces Keplerian rotation around TMC-1A | E: Double power-law fit to major-axis PV mean positions and 3D disk-model fit to channel maps | R: p_in=0.54±0.14 and v=0.53 with M*=0.68 Msun | F: Inner part is Keplerian rotation | **supported**
- H: The envelope is infalling at free-fall speed | E: Compare FE/SE model PV diagrams with observations | R: Best alpha=0.3; free-fall model D fails | F: Infall is ~0.3 times free fall | **supported**
- H: Magnetic fields can explain slow infall | E: Equation of motion estimate with pressure and tension at 200 AU | R: B ~ 2 mG required | F: Plausible given mG fields at high density | **partially**
- H: Disk radii and protostellar masses grow with evolution | E: Correlations in sources with infall-to-Keplerian transitions (Table 3) | R: Correlation coefficients 0.97, 0.95, 0.91 | F: Consistent with inside-out collapse; small sample | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: PV analysis along major axis avoids contamination from outflow/infall; channel-map fit restricted to rotation-dominated velocities  
  > "it is required that only the velocity channels where rotation is dominant should be used for comparison with a disk model." (4.3 Rotating Disk Models)
- Alternative: Spherical envelope with bipolar cavities cannot explain observations better than flattened envelope  
  > "we, therefore, conclude that SE models cannot explain the observations better than FE models" (Appendix: Comparison between the flattened and spherical envelope models)
- Alternative: Outflow-only explanation of minor-axis gradient rejected because most emission is slower than escape velocity  
  > "This suggests that the major part of the velocity gradient along the minor axis cannot be explained by outflow motions." (5.1 Velocity gradient along the disk minor axis)
- How they decided it was enough: _not stated_
- Limitation (authors): Inclination poorly constrained by the disk model; mass estimates are uncertain by optical depth, temperature, abundance  
  > "it is difficult to give a constraint on the inclination angle in this model fitting" (4.3 Rotating Disk Models)
- Limitation (authors): PV mean-position method underestimates break radius at limited resolution  
  > "may systematically underestimate $R_{b}$ when the spatial resolution is not high enough" (4.2 Rotation Profile)
- Caveat (inferred, ours): Single ~1 arcsec resolution observation; disk (~100 AU) barely resolved
- Caveat (inferred, ours): Inclination degenerate, so M* and infall factor depend on assumed 65 deg
- Caveat (inferred, ours): Flattened-envelope model fit by eye with no uncertainties on alpha
- Caveat (inferred, ours): Dust mass opacity values inconsistent between text and conclusions
- Caveat (inferred, ours): 12CO resolved out near systemic velocity; missing short spacings affect low-velocity infall signature

## Reproducibility

- Data public (paper): ALMA Cycle 0 data 2011.0.00210.S acknowledged  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2011.0.00210.S (P.I. N. Ohashi)." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Disk-modelling/MCMC code and settings
- Missing: CASA version and CLEAN parameters
- Missing: FE/SE model code and exact density and temperature setups
- Missing: Line-free channels
- Data volume (inferred): ~10-30 GB raw Cycle 0 single-track dataset
- Score (inferred): 5/5, Public single-track data and clear observables, but model code and imaging details are missing; infall comparison is qualitative.
- Rediscovery candidate: no, Key results rely on a non-public disk model code and by-eye PV model comparison, so full recipe cannot be redone.

## Links

- Method: (cite: ye2013) (PV mean-position method for rotation profile)
- Method: (cite: oh2014) (disk model code and similar analysis for L1527 IRS)
- Method: (cite: du1994) (standard rotating disk model)
- Companion: (cite: oh2014) (ALMA L1527 IRS in same series)
- Companion: (cite: ye2014) (ALMA L1489 IRS in same series)

## Checks

```json
{
 "quotes": 88,
 "quotes_ok": 88,
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
  "facts": 86,
  "stated": 62,
  "rate": 0.721
 },
 "evidence_ok": true
}
```
