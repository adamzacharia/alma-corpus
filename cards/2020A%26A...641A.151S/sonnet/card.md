# Molecular gas in the central region of NGC 7213

`2020A&A...641A.151S` | Astronomy and Astrophysics 2020 | first author: Salvestrini, F. | arXiv: 2007.02990 | DOI: 10.1051/0004-6361/202037660

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: nearby_galaxies, agn_and_quasars
- Question: What are the AGN power, molecular gas kinematics, gas mass and depletion time in the central region of the LLAGN NGC 7213, and what is the AGN impact on the host ISM and star formation?  
  > "we present a test study to show the potential of this multi-waveband method, focusing our attention on one object out of the 76 by G16." (1 Introduction)
- Target **NGC 7213**: coordinates not stated (NED radio position used)  
  > "NGC 7213 is a nearby (D=23 Mpc, z=0.0058) S0 galaxy, hosting an active nucleus" (2 NGC 7213); z/distance D=23 Mpc, z=0.0058  
  > "NGC 7213 is a nearby (D=23 Mpc, z=0.0058) S0 galaxy, hosting an active nucleus" (2 NGC 7213); distance from not stated (z from NED)  
  > "NGC 7213 is a nearby (D=23 Mpc, z=0.0058) S0 galaxy, hosting an active nucleus" (2 NGC 7213)

## Data provenance

- ALMA projects: 2012.1.00474.S
- bands: Band 6 (230 GHz)  
  > "at 230 GHz (Band 6), in configuration C32-5, including 31 12m antennas" (3.2 ALMA data)
- frequencies and spectral setup: three high-res SPWs (1920 channels of 976.562 kHz) plus one low-res SPW (128 channels of 15.626 MHz); 12CO(2-1) at 229.2 GHz, CS(5-4) at 243.5 GHz, continuum windows at 240.4 and 227.8 GHz  
  > "The spectral setup consisted of three high-resolution spectral windows with 1920 channels of 976.562 kHz width each, and a low-resolution spectral window of 128 channels of 15.626 MHz width." (3.2 ALMA data)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: C32-5, 31 12m antennas  
  > "in configuration C32-5, including 31 12m antennas" (3.2 ALMA data)
- baselines: _not stated_
- angular resolution: 0.5 arcsec (60 pc)  
  > "where 0.5$^{\prime\prime}$ is the spatial resolution" (3.2 ALMA data)
- max recoverable scale: 6.2 arcsec (750 pc)  
  > "the largest angular scale that was recovered with the adopted antenna configuration is 6.2$^{\prime\prime}$, or 750 pc." (3.2 ALMA data)
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: May 2014  
  > "The ALMA observations of NGC 7213 were taken in May 2014" (3.2 ALMA data)
- pi or archival as stated: Archival, PI N. Nagar  
  > "early science, project: 2012.1.00474.S, PI: N. Nagar" (3.2 ALMA data)
- Line: 12CO J=2-1 (not stated (observed 229.2 GHz))
- Line: CS J=5-4 (not stated (observed 243.5 GHz))
- Other facility **APEX (PI230)**: Single-dish CO(2-1) flux for total gas mass  
  > "project 0103.F-9311, PI: F. Salvestrini" (3.3 APEX data)
- Other facility **XMM-Newton and NuSTAR**: X-ray spectra to derive AGN 2-10 keV luminosity  
  > "XMM-*Newton* (ID: 605800301; starting in Nov. 11th 2009; t$_{\rm exp}=132.5$ ks)" (3.1.1 X-ray data reduction)
- Other facility **HST/WFPC2**: Archival optical images for comparison with CO  
  > "archival *HST* optical observation (taken with the F606W filter on the WFPC2" (3.2.2 The CO(2-1) emission line)
- Other facility **Herschel/PACS**: 70 um flux ratio to scale SFR to APEX aperture  
  > "We considered the *Herschel*/PACS observation at 70 $\mu$m" (4.4 The molecular gas mass)
- External data: SED decomposition results (M*, SFR, L_IR, SED fit) and photometry  
  > "NGC 7213 benefits from a detailed SED decomposition performed by G16" (3.4 SED decomposition) [from (cite: Gruppioni16)]
- External data: ATCA 5, 8, 20 GHz radio flux densities  
  > "radio flux densities at 5, 8 and 20 GHz (obtained simultaneously at the Australia Telescope Compact Array, ATCA; (cite: Murphy10))" (4.1 The point-like continuum) [from (cite: Murphy10)]
- External data: Disc inclination i=30 deg  
  > "We also fixed the inclination of the disc with respect to the line of sight to $i=30^\circ$, as estimated in literature works" (4.2 The molecular gas kinematics) [from (cite: StorchiBergmann96); (cite: Lin18)]
- External data: Bolometric correction k_bol=9±5  
  > "Assuming a bolometric conversion factor of $k_{bol}=9\pm$5 as from (cite: Lusso12)" (3.1.2 X-ray data analysis) [from (cite: Lusso12)]
- External data: Black hole mass ~1e8 Msun  
  > "assuming a black hole mass M$_{BH}\sim10^8$ M$_{\odot}$, as from (cite: WooUrry02)" (3.1.2 X-ray data analysis) [from (cite: WooUrry02)]

## Processing

### Calibration

- pipeline or manual: ALMA calibration scripts  
  > "The data were calibrated using the ALMA calibration scripts, with CASA version 4.5.3." (3.2 ALMA data)
- casa version: CASA 4.5.3  
  > "with CASA version 4.5.3" (3.2 ALMA data)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Neptune, Butler-JPL-Horizons 2012 model; bandpass J2056-4714, phase J2235-4835  
  > "while Neptune was used as amplitude calibrator, assuming the Butler-JPL-Horizons 2012 model." (3.2 ALMA data)
- flux scale uncertainty: ~5%  
  > "the flux calibration uncertainty ($\sim$5%, as suggested when using Neptune as flux calibrator)" (3.2.2 The CO(2-1) emission line)
- self calibration: _not stated_

### Imaging

- task: CASA clean  
  > "continuum and line images were obtained using the CASA task *clean*" (3.2 ALMA data)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "We adopted the natural weighting to get the best signal-to-noise ratio." (3.2 ALMA data)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: CO(2-1) from continuum-subtracted cube; continuum from line-free channels in all four SPWs  
  > "The CO(2-1) emission line was extracted from the continuum-subtracted cube of the first spectral window." (3.2.2 The CO(2-1) emission line)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: cube binned to 10 km/s resolution  
  > "requiring a spectral resolution of 10 km s$^{-1}$" (3.2.2 The CO(2-1) emission line)
- final beam: continuum 0.48x0.44 arcsec PA 81.1 deg; CO 0.50x0.47 arcsec PA 73.4 deg  
  > "synthesized beam of 0.50$^{\prime\prime}\times0.47^{\prime\prime}$, with a position angle of 73.4 deg" (3.2.2 The CO(2-1) emission line)
- final rms: continuum 8.9e-5 Jy/beam; CO 0.1 mJy/beam per channel  
  > "a 1$\sigma$ RMS level of 8.9$\times10^{-5}$ Jy beam$^{-1}$" (3.2.1 The continuum emission); "an average 1$\sigma$ RMS is 0.1 mJy beam$^{-1}$ per channel" (3.2.2 The CO(2-1) emission line)

### Inherited from earlier work

- 3DBarolo kinematic modelling approach  
  > "Following a similar approach to that adopted by (cite: Sabatini18), we used the $^{\rm 3D}$BAROLO" (4.2 The molecular gas kinematics) [from (cite: Sabatini18)]
- SED decomposition procedure  
  > "the SED decomposition procedure adopted by G16" (3.4 SED decomposition) [from (cite: Gruppioni16)]
- Gaussian line normalisations fitted with energies fixed (NuSTAR)  
  > "then we left the normalisation free to vary (as in (cite: Ursini15))" (3.1.2 X-ray data analysis) [from (cite: Ursini15)]

### Not stated but needed to reproduce (our reading)

- Clean threshold, niter, masks, cell and image size
- Line-free channels and continuum-subtraction order
- Primary-beam correction details
- Moment-map clipping thresholds
- 3DBarolo parameter file details (e.g. normalisation, fitting mode, VDISP initial)
- How APEX baseline/windows and double-Gaussian fit were set
- Outflow velocity/size/flux extraction details for Regions A and C
- Exact NED coordinates used

## Analysis recipe

1. **Continuum flux**: Elliptical Gaussian fit to 235.1 GHz continuum map  
  > "Using the *imfit* task from the CASA software, we fitted the map with an elliptical Gaussian profile." (3.2.1 The continuum emission)
   - software: CASA imfit
   - fitting: _not stated_
   - validation: Centroid compared with NED radio position  
  > "The best-fit centroid is consistent, within the uncertainties, with the NGC 7213 radio position" (3.2.1 The continuum emission)
2. **CO(2-1) flux in ALMA and APEX**: ALMA flux in 25 arcsec circular aperture; APEX double-Gaussian fit converted K to Jy with 35 Jy/K  
  > "The integrated CO(2-1) surface brightness has been obtained performing a fit using a double Gaussian function to the line profile." (3.3 APEX data)
   - software: CASA, CLASS/GILDAS
   - parameter: APEX Jy/K = 35±3; calibration uncertainty 15%  
  > "the conversion factor is 35$\pm$3" (3.3 APEX data)
   - fitting: double Gaussian  
  > "The integrated CO(2-1) surface brightness has been obtained performing a fit using a double Gaussian function to the line profile." (APEX data)
   - validation: ALMA recovers ~30% of APEX flux  
  > "the ALMA interferometric observations only recovered about 30% of the CO(2-1) flux density measured with APEX" (3.3 APEX data)
3. **Model CO kinematics**: 3D tilted-ring fit of the CO(2-1) cube with local normalisation, smoothing factor 2, S/N cut 4  
  > "to cut the smoothed cube at a signal-to-noise ratio of 4" (4.2 The molecular gas kinematics)
   - software: 3DBarolo
   - parameter: PA=330 deg, i=30 deg fixed, centre at continuum centroid, 8 rings separated by 1.5 arcsec; free: v_circ, v_sys, dispersion  
  > "We set the maximum number of radii to 8, separated by 1.5$^{\prime\prime}$ or $\sim$180 pc" (4.2 The molecular gas kinematics)
   - assumption: Thin disc, rotation dominated  
  > "the material which is responsible for the observed emission has to be contained in a thin disc" (4.2 The molecular gas kinematics)
   - fitting: not stated beyond 3DBarolo  
  > "$^{\rm 3D}$BAROLO is a code specifically developed to fit 3D tilted-rings models on two main assumptions" (The molecular gas kinematics)
   - validation: Tested PA 320-340 and i 20-40 deg one at a time; radial velocity consistent with zero  
  > "We run the code with this additional free parameter, but its best-fit value was consistent with zero." (4.2 The molecular gas kinematics)
4. **Outflow rates from residuals**: Mass from residual flux with alpha_CO=1.1; Mdot=3 v_max M/R spherical  
  > "assuming a spherical geometry (i.e., $\dot{M}_{OF}=3v_{max}M_{OF}/R_{OF}$)" (4.3 Complex structures in the CO emission)
   - software: 3DBarolo
   - assumption: alpha_CO=1.1 Msun pc^-2 (K km/s)^-1  
  > "The molecular gas outflow mass was calculated by assuming an $\alpha_{\rm CO}$=1.1" (4.3 Complex structures in the CO emission)
   - fitting: _not stated_
   - validation: Compared to Mdot-L_AGN relation  
  > "This prediction is at least two orders of magnitudes larger than what we measured" (4.3 Complex structures in the CO emission)
5. **Gas mass and depletion time**: APEX CO(2-1) -> CO(1-0) with ratio 3, L' via Carilli & Walter, M_gas=alpha_CO L'; SFR scaled by Herschel 70um aperture ratio; t_depl=M_gas/SFR  
  > "We therefore assumed $f_{\rm CO(2-1)}$/$f_{\rm CO(1-0)}=3$" (4.4 The molecular gas mass)
   - parameter: F_tot/F_25" = 2.0±0.3 at 70 um  
  > "F$_{tot}$/F$_{25^{\prime\prime}}$=2.0$\pm$0.3" (4.4 The molecular gas mass)
   - assumption: alpha_CO=1.1, solar metallicity, CO(2-1)/CO(1-0)=3  
  > "we assume it to be solar-like" (4.4 The molecular gas mass)
   - fitting: _not stated_
   - validation: L'_CO compared with L_IR-L'_CO relation; consistent within uncertainties  
  > "the two values are consistent within the uncertainties" (4.4 The molecular gas mass)

## Software

- **CASA** 4.5.3: calibration, clean imaging, imfit  
  > "with CASA version 4.5.3" (3.2 ALMA data)
- **3DBarolo** : tilted-ring kinematic modelling of CO(2-1)  
  > "to model the kinematics of the molecular gas, as traced by the CO(2-1) emission line" (4.2 The molecular gas kinematics)
- **CLASS/GILDAS** : APEX data reduction  
  > "Data reduction was performed using the CLASS program, which is part of the GILDAS" (3.3 APEX data)
- **XSPEC** 12.10.0c: X-ray spectral fitting  
  > "X-Ray Spectral Fitting Package (`XSPEC`) v. 12.10.0c" (3.1.2 X-ray data analysis)
- **SAS** 16.1.0: XMM-Newton reduction  
  > "Science Analysis Software (`SAS`) v.16.1.0 for XMM-*Newton*" (3.1.1 X-ray data reduction)
- **HEASOFT/NuSTARDAS** 6.19 / 1.7.1: NuSTAR reduction  
  > "the `HEASOFT` (v. 6.19) distribution for *NuSTAR* Focal Plane Modules" (3.1.1 X-ray data reduction)
- **SED3FIT** : SED decomposition (by G16)  
  > "The adopted SED-fitting code was `SED3FIT`" (3.4 SED decomposition)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| ALMA continuum flux density at 235.1 GHz | 40.1 | 0.1 | mJy | 1 | F$_{\nu, \rm cont}=40.1\pm0.1$ mJy |
| CO(2-1) flux, ALMA | 112 | 5 | Jy km/s | 2 | f$_{\rm CO, ALMA}= 112\pm$5 Jy km s$^{-1}$ |
| CO(2-1) flux, APEX | 340 | 60 | Jy km/s | 2 | f$_{\rm CO, APEX}= 340\pm$60 Jy km s$^{-1}$ |
| X-ray photon index (NuSTAR) | 1.81 | 0.02 | dimensionless | 0 | 1.81$\pm$0.02 |
| L_2-10keV | 1.25e42 | 0.02e42 | erg/s | 0 | L$_{\rm 2-10 keV}=(1.25\pm0.02)\times10^{42}$ ergs s$^{-1}$ |
| Bolometric luminosity | 1.1e43 | 0.6e43 | erg/s | 0 | L$_{bol}=(1.1\pm0.6)\times10^{43}$ ergs s$^{-1}$ |
| Radio spectral slope | 0.54 | 0.03 | dimensionless | 0 | We obtained a slope $\alpha=0.54\pm$0.03 |
| Systemic velocity | 1716 | 10 | km/s | 3 | V$_{\rm sys}=1716\pm$10 km s$^{-1}$ |
| Outflow rate Region C | 0.03 | 0.02 | Msun/yr | 4 | $\dot{M}_{OF}\sim0.03\pm0.02$ M$_{\odot}$ yr$^{-1}$ |
| L'_CO(1-0) APEX | 1.8e8 | 0.3e8 | K km/s pc^2 | 5 | L$^{\prime}_{\rm CO(1-0), APEX}=(1.8\pm0.3)\times10^8$K km s$^{-1}$ pc$^2$ |
| Molecular gas mass | 2.0e8 | 0.3e8 | Msun | 5 | M$_{\rm gas}=(2.0\pm0.3)\times10^8$ M$_{\odot}$ |
| Depletion time | 0.4 | 0.1 | Gyr | 5 | t$_{\rm depl}$=0.4$\pm$0.1 Gyr |

## Qualitative findings

- CO(2-1) traces spiral arms, with no CO at the nuclear continuum position; kinematics dominated by circular rotation  
  > "is clearly dominated by purely circular rotational motion around the nucleus" (4.2 The molecular gas kinematics)

## Claim tuples

- H: Is the 1.3 mm continuum nuclear synchrotron or thermal dust? | E: Compare ALMA flux with extrapolated ATCA power law and torus SED models | R: ALMA point is consistent with the radio extrapolation; torus models underpredict it | F: Continuum is most likely synchrotron | **supported**
- H: Does the AGN disturb the central molecular gas? | E: 3DBarolo model of CO(2-1) and residual analysis | R: Rotation-dominated; no non-rotational motion within ~60 pc | F: No evidence of nuclear inflows or AGN-driven disturbance | **supported**
- H: Are there outflows and what drives them? | E: PV diagrams, moment maps, outflow rate vs L_AGN relation | R: Two candidate outflows with Mdot ~0.03-0.05 Msun/yr, far below the AGN prediction | F: Likely stellar-driven; better data needed | **partially**
- H: Does the AGN affect star formation via gas depletion? | E: APEX-based M_gas and scaled SFR | R: M_gas=2.0e8 Msun, t_depl=0.4 Gyr | F: Negligible impact of AGN on SF | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: APEX single-dish used because interferometer resolves out extended CO  
  > "The need for the single-dish observation was motivated by the potential filtering of the CO emission at intermediate and large scales" (3.3 APEX data)
- Alternative: Thermal dust (FIR bump tail or torus, including extreme tori) rejected as the origin of the 1.3 mm continuum  
  > "Then we excluded the thermal emission from dust to be the major contribution to the observed continuum emission at 1.3 mm." (4.1 The point-like continuum)
- How they decided it was enough: _not stated_
- Limitation (authors): ALMA configuration resolves out diffuse gas; MRS 6.2 arcsec  
  > "that has most likely been resolved out because of the extended antenna configuration" (3.2.2 The CO(2-1) emission line)
- Limitation (authors): Cannot exclude free-free contribution to continuum  
  > "With the current data, we are not able to exclude the contribution from other mechanisms" (4.1 The point-like continuum)
- Caveat (inferred, ours): Fixed inclination and PA with a face-on disc (i=30) make rotation curve degenerate
- Caveat (inferred, ours): alpha_CO and CO(2-1)/CO(1-0)=3 assumed; gas mass uncertainty likely underestimated
- Caveat (inferred, ours): APEX 25 arcsec beam vs ALMA recovered flux; extended-gas inference rests on single-dish only
- Caveat (inferred, ours): SFR aperture scaling uses 70 um ratio only
- Caveat (inferred, ours): Outflow identification is tentative with ~1 beam sized regions

## Reproducibility

- Data public (paper): Archival ALMA, XMM and NuSTAR data  
  > "we re-analyse and combine the following archival observations" (3.1.1 X-ray data reduction)
- Products in archive: _not stated_
- Missing: Clean parameters and masks
- Missing: 3DBarolo input parameters
- Missing: APEX raw data reduction details
- Missing: G16 SED outputs needed externally
- Data volume (inferred): ~10-50 GB for ALMA raw data; small for APEX and X-ray
- Score (inferred): 5/5, ALMA project and software versions are given, but imaging and 3DBarolo parameters are partly unstated and key inputs come from G16.
- Rediscovery candidate: yes, Public ALMA data, a fairly clear recipe, and numeric results (continuum flux, CO flux, v_sys).

## Links

- Method: (cite: 3DBAROLO) (Kinematic fitting code)
- Method: (cite: Berta13) (SED3FIT code)
- Companion: (cite: Gruppioni16) (SED decomposition and SFR/L_IR source)
- Companion: (cite: Ramakrishnan19) (Previous ALMA analysis of NGC 7213)
- Companion: (cite: Sabatini18) (Similar kinematic approach)
- Related: 12 micron galaxy sample (Rush et al. 1993)

## Checks

```json
{
 "quotes": 86,
 "quotes_ok": 86,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 12,
 "numeric_problems": 0,
 "fill": {
  "facts": 87,
  "stated": 64,
  "rate": 0.736
 },
 "evidence_ok": true
}
```
