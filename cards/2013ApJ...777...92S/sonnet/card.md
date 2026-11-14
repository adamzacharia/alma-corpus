# ALMA Observations of the Coldest Place in the Universe: The Boomerang Nebula

`2013ApJ...777...92S` | The Astrophysical Journal 2013 | first author: Sahai, R. | arXiv: 1308.4360 | DOI: 10.1088/0004-637X/777/2/92

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: evolved_stars
- Question: What is the structure of the ultra-cold Boomerang Nebula's molecular outflow, how does it relate to the visible-light nebula, and what do the mm continuum data say about the dust in the waist?  
  > "High angular resolution mapping of the molecular gas distribution in the Boomerang was needed to resolve the apparent discrepancy between the molecular and visible-light morphology." (Introduction)
- Target **Boomerang Nebula**: coordinates RA 12h44m45.45s, Dec -54d31'11.4" (Simbad)  
  > "We adopt a value of 1.5 kpc for the distance to the Boomerang (as inferred by SN97)." (Introduction); "The pointing position corresponds to the Simbad coordinates of the Boomerang Nebula, R.A.$=12^h44^m45.45^s$ and Dec$=-54^\circ31'11.4{''}$." (Observations); z/distance 1.5 kpc  
  > "We adopt a value of 1.5 kpc for the distance to the Boomerang (as inferred by SN97)." (Introduction); "The pointing position corresponds to the Simbad coordinates of the Boomerang Nebula, R.A.$=12^h44^m45.45^s$ and Dec$=-54^\circ31'11.4{''}$." (Observations); distance from inferred by Sahai & Nyman 1997 (SN97)  
  > "We adopt a value of 1.5 kpc for the distance to the Boomerang (as inferred by SN97)." (Introduction); "The pointing position corresponds to the Simbad coordinates of the Boomerang Nebula, R.A.$=12^h44^m45.45^s$ and Dec$=-54^\circ31'11.4{''}$." (Observations)

## Data provenance

- ALMA projects: 2011.0.00510.S
- bands: Band 3 (CO 1-0) and Band 6 (CO 2-1)  
  > "were observed using ALMA band 3 on November 29 and December 31, 2011." (Observations)
- frequencies and spectral setup: 4 spectral windows of 1.875 GHz, 3840 channels; band 3 windows ~100.7, 102.6, 112.7, 114.6 GHz; band 6 ~228.4, 230.4, 242.4, 244.4 GHz; channel 0.488 MHz  
  > "the data contains four spectral windows of $1.875$ GHz width and with 3840 channels." (Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: compact Cycle 0 configuration  
  > "The data was taken using the compact ALMA cycle 0 configuration, with baselines ranging from 14 m up to 200 m." (Observations)
- baselines: 14 m to 200 m  
  > "with baselines ranging from 14 m up to 200 m." (Observations)
- angular resolution: ~2"-4"  
  > "with $\sim2\ensuremath{''}-4\ensuremath{''}$ resolution, in the CO J=2-1 and J=1-0 lines" (Introduction)
- max recoverable scale: >~17" (Band 6); >~35" (Band 3)  
  > "the angular scale at which the ALMA observations are expected to resolve out structures ($\gtrsim17{''}$)" (CO (J=2-1)); "the array was not sensitive to structure on scales $\gtrsim35{''}$" (CO (J=1-0))
- sensitivity: rms ~2.5 mJy/beam (CO 1-0), ~7.5 mJy/beam (CO 2-1)  
  > "In the line-free channels, the resulting rms noise was $\sim2.5$ mJy beam$^{-1}$." (Observations)
- time on source: CO 1-0: 3.25 h total (7-point mosaic, ~19 min per pointing); CO 2-1: 6 min  
  > "The total observing time for the CO (J=1-0) line was 3.25 hours with each mosaic pointing observed for $\sim19$ min in total." (Observations)
- observing dates: Band 3: 29 Nov and 31 Dec 2011; Band 6: 28 Nov 2011  
  > "was observed, using ALMA band 6, on November 28 2011." (Observations)
- pi or archival as stated: _not stated_
- Line: CO J=1-0 (115.2712 GHz)
- Line: CO J=2-1 (230.3581 GHz)
- Other facility **HST (ACS/HRC, WFPC2)**: archival F606W visible-light images  
  > "through the F606W wide-band filter, on March 25, 2005, and March 23, 1998 via programs GO 10378 and GO 6856" (Observations)
- Other facility **ATCA**: radio continuum at 5.5, 9, 23 GHz (upper limits), project CX241  
  > "A 10-h observation run (project code CX241) was carried out with the 6D array configuration" (Observations)
- Other facility **SEST**: single-dish CO 1-0 data feathered with ALMA  
  > "we combined a CO (J=1-0) image cube with a spectral resolution of $8$ km s$^{-1}$ with the original SEST observations (SN97)" (Observations)
- External data: SN97 two-shell model (inner 2.5-6" at 35 km/s; outer 6-33" at 164 km/s), T_kin(r) profile, distance  
  > "a warm inner shell extending 2.5$''$–6$''$ with an expansion velocity of about 35 km s$^{-1}$" (Discussion) [from Sahai & Nyman 1997: SN97]
- External data: SEST CO(1-0) single-dish observations  
  > "with the original SEST observations (SN97)" (Observations) [from Sahai & Nyman 1997 (SN97)]

## Processing

### Calibration

- pipeline or manual: Manual-style CASA reduction: WVR/Tsys corrections, antenna position improvement, bandpass and gain calibration  
  > "After corrections for time and frequency dependence of the system temperatures and rapid atmospheric variations at each antenna using WVR data, we improved the antenna positions." (Observations)
- casa version: CASA 3.4.0  
  > "The data were reduced using the Common Astronomy Software Application (CASA 3.4.0)." (Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Mars (flux); J1329-5608 (bandpass and gain)  
  > "bandpass and gain calibration were performed on the quasar J1329-5608, while flux calibration was done using Mars." (Observations)
- flux scale uncertainty: 3% Band 3, 5% Band 6  
  > "We estimate the final absolute flux calibration to be accurate to within $3\%$ in band 3 and $5\%$ in band 6." (Observations)
- self calibration: _not stated_

### Imaging

- task: CASA clean; feather for ALMA+SEST combination  
  > "Imaging was done using the CASA clean algorithm after a continuum subtraction was performed on the emission line data." (Observations)
- deconvolver: _not stated_
- weighting robust: CO 1-0: natural; CO 2-1: Briggs (robust not given)  
  > "The CO (J=2-1) map was imaged at a spectral resolution of $0.63$ km s$^{-1}$, Briggs weighing and a Gaussian taper of $100$ k$\lambda$" (Observations)
- uv taper: 50 kλ (CO 1-0); 100 kλ (CO 2-1)  
  > "using natural weighing, a Gaussian taper of $50$ k$\lambda$ and a restoring beam of $4.5\ensuremath{''}\times3.0\ensuremath{''}$" (Observations)
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: performed on line data before clean  
  > "after a continuum subtraction was performed on the emission line data" (Observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: ALMA CO(1-0) cube at 8 km/s feathered with SEST  
  > "using the CASA task *feather*, in which the regridded image data is combined in the Fourier plane" (Observations)
- smoothing: CO 1-0 channel-averaged to 6.25 km/s; 8 km/s for feathering  
  > "Our final CO (J=1-0) image was created by channel averaging to a spectral resolution of $6.25$ km s$^{-1}$" (Observations)
- final beam: CO 1-0: 4.5"x3.0" PA -30deg; CO 2-1: 2.40"x1.55" PA -3.5deg  
  > "the beam was $2.40\ensuremath{''}\times1.55\ensuremath{''}$ at a position angle of $-3.5^\circ$" (Observations)
- final rms: ~2.5 mJy/beam (CO 1-0); ~7.5 mJy/beam (CO 2-1)  
  > "this resulted in an rms noise of $\sim7.5$ mJy beam$^{-1}$" (Observations)

### Inherited from earlier work

- Distance of 1.5 kpc, systemic velocity ~-10 km/s, kinetic temperature profile and shell model taken from SN97  
  > "We adopt a value of 1.5 kpc for the distance to the Boomerang (as inferred by SN97)." (Introduction) [from Sahai & Nyman 1997: SN97]
- Photoelectric heating rate k_pe=1e-26 and dust-optical-depth formula  
  > "$k_{pe}=10^{-26}$ (e.g., Huggins et al. 1988)" (Re-Heating) [from Huggins et al. 1988; Morris & Jura 1983]

### Not stated but needed to reproduce (our reading)

- Briggs robust value and clean parameters (image size, cell size, masks, threshold, niter)
- Line-free channels used for continuum subtraction
- Continuum image weighting, taper and spectral windows used for 1.3 and 2.6 mm
- How the S/N-modest 1.3 mm continuum was imaged and sparse uv coverage handled
- Details of the dust SED fit (beam-matching, uncertainties on R)
- Feather parameters and SEST data processing/scaling
- Mosaic imaging details for the Band 3 7-point mosaic

## Analysis recipe

1. **Calibrate and image ALMA CO and continuum data**: CASA calibration with J1329-5608 and Mars, continuum subtraction, clean with several weightings/tapers to test robustness  
  > "we performed various cleaning rounds using different weighing schemes (from natural to uniform) and different data tapering to assess the robustness of the observed structure." (Observations)
   - software: CASA
   - parameter: CO 1-0 natural weighting, 50 kλ taper; CO 2-1 Briggs, 100 kλ taper  
  > "using natural weighing, a Gaussian taper of $50$ k$\lambda$" (Observations)
   - fitting: _not stated_
   - validation: consistent structure recovered across cleaning runs, so not missing-spacing artifacts  
  > "As consistent structure was recovered in the different cleaning runs, we conclude that these are not artifacts of the missing short spacings." (Observations)
2. **Combine ALMA CO(1-0) with SEST**: Feather in Fourier plane at 8 km/s resolution  
  > "using the CASA task *feather*, in which the regridded image data is combined in the Fourier plane." (Observations)
   - software: CASA feather
   - fitting: _not stated_
   - validation: ALMA emission peak (5 Jy) within ~20% of ALMA+SEST value  
  > "the peak flux of the emission component in the ALMA spectrum (5 Jy) is only about 20% different from (larger than) that in the ALMA+SEST spectrum" (CO (J=1-0))
3. **Derive lobe inclination and kinematics from CO(2-1) PV diagrams**: Cylindrical-lobe geometry with radial expansion, using lobe diameter 3.3" and projected length 6.5", to limit inclination  
  > "we can set an upper limit of $15\ensuremath{^\circ}$ on the inclination of the nebula axis to the sky-plane" (Spatio-Kinematic Structure of the Lobes)
   - assumption: radial expansion and cylindrical S-lobe geometry  
  > "assuming radial expansion and a cylindrical geometry for the S-lobe" (Spatio-Kinematic Structure of the Lobes)
   - fitting: _not stated_
   - validation: _not stated_
4. **Estimate radius of photoelectric re-heating**: Equate adiabatic cooling rate with photoelectric heating rate to find r_pe  
  > "by equating the adiabatic cooling rate per $H_2$ molecule, $Q_{adiab}=2\,k_B\,V_{exp}\,T_{kin}(r)/r$, with the photoelectric heating rate" (Re-Heating)
   - parameter: k_pe=1e-26, delta=200, Mdot=1.3e-3 Msun/yr  
  > "with the gas-to-dust ratio, $\delta=200$, and $\mbox{$\dot{M}$}=1.3\times10^{-3}\,\mbox{$M_{\odot}$~yr$^{-1}$}$, we compare $Q_{pe}(r)$ to $Q_{adiab}$, for $k_{pe}=10^{-26}$" (Discussion: Re-Heating of the Ultra-cold Outflow: Photoelectric Dust Grain Heating)
   - assumption: constant expansion velocity (also tested power-law V with alpha=1)  
  > "We set $V'(r)=164\,\mbox{km~s$^{-1}$}\,(r/r_o)^{\alpha}$, with $\alpha=1$" (Re-Heating)
   - fitting: _not stated_
   - validation: compared with observed outer emission radius ~25"  
  > "larger than the observed value ($\sim25{''}$, or $0.56\times10^{18}$ cm) by almost a factor 2" (Re-Heating)
5. **Derive dust emissivity index, temperature, mass of waist**: Fit 1.3/2.6 mm peak flux ratio with power-law emissivity; choose beta, T_d consistent with compact size r_d~2"; compute dust and total mass  
  > "Since the continuum emission arises from a compact source with an observed value of $r_d\sim2{''}$, we conclude $\beta\sim0.6$ and $T_d\sim45$ K" (Thermal Dust Emission from the Waist)
   - parameter: kappa(1.3mm)~1.5 cm2/g, gas-to-dust 200  
  > "assuming a dust opacity of $\kappa(1.3mm)\sim1.5$ cm$^2$ g$^{-1}$ and the gas-to-dust ratio, $\delta=200$" (Thermal Dust Emission from the Waist)
   - assumption: power-law dust emissivity; ATCA non-detections rule out free-free  
  > "so free-­free emission is unlikely to contribute to the 1.3 and 2.6 mm fluxes" (Thermal Dust Emission from the Waist)
   - fitting: analytic, no sampler  
  > "re-derive the radial dependence of the kinetic temperature and adiabatic cooling analytically." (Discussion: Re-Heating of the Ultra-cold Outflow: Photoelectric Dust Grain Heating)
   - validation: _not stated_

## Software

- **CASA** 3.4.0: calibration, clean imaging, feather  
  > "The data were reduced using the Common Astronomy Software Application (CASA 3.4.0)." (Observations)
- **MIRIAD** : ATCA calibration and imaging  
  > "The calibration and the imaging of the data were done using the MIRIAD package." (Observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| 1.3 to 2.6 mm peak flux ratio | 5.7 | not stated | dimensionless | 5 | $R=5.7$ |
| dust emissivity index beta | ~0.6 | not stated | dimensionless | 5 | we conclude $\beta\sim0.6$ and $T_d\sim45$ K |
| dust temperature | ~45 | not stated | K | 5 | we conclude $\beta\sim0.6$ and $T_d\sim45$ K |
| dust mass in waist | 3.5e-4 | not stated | Msun | 5 | is $M_d\sim3.5\times10^{-4}$ $M_{\odot}$ |
| total mass of waist | 0.071 | not stated | Msun | 5 | the total mass is $M\sim0.071$ $M_{\odot}$ |
| mass-loss rate of waist | 1.8e-4 | not stated | Msun/yr | 5 | implying a mass-loss rate $\sim1.8\times10^{-4}$ $M_{\odot}$ yr$^{-1}$ |
| upper limit on inclination of nebula axis to sky plane | 15 | not stated | deg | 3 | we can set an upper limit of $15\ensuremath{^\circ}$ on the inclination |
| peak fluxes of 1.3 and 2.6 mm continuum (2.6mm beam) | 3.64 and 0.64 | not stated | mJy/beam | 1 | are 3.64 mJy and 0.64 mJy, respectively |
| ATCA 1-sigma upper limits at 5.5, 9, 23 GHz | 23, 34, 21 | not stated | uJy/beam | 0 | with $1\sigma$ upper limits of $23, 34,$ and $21~\mu$Jy/beam at 5.5, 9, and 23 GHz |
| estimated photoelectric heating radius r_pe | ~1e18 | not stated | cm | 4 | find that $r_{pe}\sim10^{18}$ cm |

## Qualitative findings

- CO(2-1) shows hourglass-shaped bipolar nebula matching HST limb-brightened hollow lobes; CO(1-0) shows patchy absorbing ultra-cold outflow  
  > "We find a central hourglass-shaped nebula surrounded by a patchy, but roughly round, cold high-velocity outflow." (abstract)

## Claim tuples

- H: Do the CO lobes correspond to the HST limb-brightened lobes as hollow dense-walled cavities? | E: Compare ALMA CO(2-1) channel maps with HST WFPC2/HRC images | R: Detailed association between CO and HST features | F: Lobes are hollow cavities with dense molecular gas and dust walls | **supported**
- H: Are large grains present in the waist? | E: 1.3/2.6 mm flux ratio plus ATCA radio limits | R: R=5.7, beta~0.6, no radio detection | F: Waist contains mm-sized grains | **supported**
- H: Is the outer CO emission due to re-warming by photoelectric heating? | E: Compare adiabatic cooling and photoelectric heating | R: r_pe~1e18 cm vs observed 0.56e18 cm, within a factor 2 | F: Photoelectric heating is a viable mechanism | **partially**

## Reasoning

- Why this data: High-resolution mapping needed to resolve molecular vs visible morphology discrepancy  
  > "High angular resolution mapping of the molecular gas distribution in the Boomerang was needed" (Introduction)
- Why this method: _not stated_
- Alternative: Projection effect from high-velocity material near center rejected as explanation of low-velocity absorption  
  > "contrary to what is observed" (CO (J=1-0))
- How they decided it was enough: _not stated_
- Limitation (authors): 1.3 mm data S/N modest with sparse uv coverage; large fraction of CO(1-0) absorption resolved out  
  > "although S/N is modest and 1.3 mm UV-coverage is still sparse" (Thermal Dust Emission from the Waist)
- Caveat (inferred, ours): Only 6 minutes on CO(2-1) and sparse 1.3 mm continuum; beta and T_d degenerate and chosen by assumed r_d
- Caveat (inferred, ours): Dust opacity and gas-to-dust ratio assumed, no uncertainties
- Caveat (inferred, ours): No radiative transfer modelling of temperature or velocity

## Reproducibility

- Data public (paper): ALMA project code given; HST from MAST archive  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2011.0.00510.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Exact clean parameters, robust, masks
- Missing: Line-free channel ranges
- Missing: SEST data and feather settings
- Missing: Dust fit details
- Data volume (inferred): ~10-30 GB raw (Cycle 0, three EBs, 3840-channel spws)
- Score (inferred): 3/5, Public data and basic steps given, but imaging parameters missing; results partly qualitative.
- Rediscovery candidate: no, Imaging details are incomplete and the main results are mostly morphological; numeric results derive from assumption-dependent estimates.

## Links

- Companion: Sahai & Nyman 1997 (SN97) (Original single-dish CO model of the Boomerang)
- Related: HST GO 10378
- Related: HST GO 6856
- Related: ATCA CX241

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
 "numeric_results": 10,
 "numeric_problems": 0,
 "fill": {
  "facts": 76,
  "stated": 54,
  "rate": 0.711
 },
 "evidence_ok": true
}
```
