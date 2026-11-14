# AGN X-Ray Irradiation of CO Gas in NGC 2110 Revealed by Chandra and ALMA

`2020ApJ...895..135K` | The Astrophysical Journal 2020 | first author: Kawamuro, Taiki | arXiv: 2004.09394 | DOI: 10.3847/1538-4357/ab8b62

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type multi_facility_alma_minor

## Science

- Fields: nearby_galaxies, agn_and_quasars
- Question: Does AGN X-ray irradiation, traced by extended Fe-Kα emission, explain the weak CO(J=2–1) emission in the central ~1.3 kpc of NGC 2110?  
  > "we provide further pieces of information obtained by constraining the Fe-K$\alpha$ distribution, eventually enabling quantitative discussion for the weak CO($J$ = 2–1) emission." (Introduction)
- Target **NGC 2110**: coordinates R.A., Dec. = 88.047420, -7.456212 (optical center, Clements 1983)  
  > "NGC 2110 is located at a redshift of 0.00779 ($cz$ = 2335$\pm$20 km s$^{-1}$), determined from an optical Mg $b$ absorption line by (cite: Nel95)." (2 NGC 2110); "the luminosity and angular distances are 33.6 Mpc and 33.0 Mpc (i.e., 1 arcsec $\approx$ 160 pc)" (2 NGC 2110); z/distance z = 0.00779; D_L = 33.6 Mpc, D_A = 33.0 Mpc  
  > "NGC 2110 is located at a redshift of 0.00779 ($cz$ = 2335$\pm$20 km s$^{-1}$), determined from an optical Mg $b$ absorption line by (cite: Nel95)." (2 NGC 2110); "the luminosity and angular distances are 33.6 Mpc and 33.0 Mpc (i.e., 1 arcsec $\approx$ 160 pc)" (2 NGC 2110); distance from Redshift from Nelson & Whittle 1995; distances from LambdaCDM (H0=70, Om=0.3, OL=0.7)  
  > "NGC 2110 is located at a redshift of 0.00779 ($cz$ = 2335$\pm$20 km s$^{-1}$), determined from an optical Mg $b$ absorption line by (cite: Nel95)." (2 NGC 2110); "the luminosity and angular distances are 33.6 Mpc and 33.0 Mpc (i.e., 1 arcsec $\approx$ 160 pc)" (2 NGC 2110)

## Data provenance

- ALMA projects: 2012.1.00474.S
- bands: Band 6 (~270 GHz)  
  > "We utilized the Band 6 ($\sim$ 270 GHz) ALMA data with the program ID = #2012.1.00474.S (PI: N. Nagar)." (3.2 ALMA)
- frequencies and spectral setup: One spw with 1.875 GHz bandwidth, centre 228.792 GHz, 1920 channels; raw 0.98 MHz (~1.3 km/s), binned to ~10 km/s  
  > "A spectral window that covered CO($J$ = 2–1) emission had a total bandwidth of 1.875 GHz with a central frequency of 228.792 GHz and 1920 channels." (3.2 ALMA)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: CO beam 0.52x0.83 arcsec, PA -75.17 deg  
  > "The achieved synthesized beam was $0.52\times0.83$ arcsec$^2$ with P.A. = $-75.17$ degrees." (4.2.1)
- max recoverable scale: ~8.6 arcsec (≈1.38 kpc), from minimum baseline 19 m  
  > "The maximum angular scale, which can be recovered from observations, was $\sim$ 8.6 arcsec ($\approx$ 1.38 kpc) from a minimum projected baseline of 19 m." (3.2 ALMA)
- sensitivity: RMS 0.76 mJy/beam (10 km/s channels)  
  > "The final continuum-subtracted data had a RMS noise of 0.76 mJy beam$^{-1}$." (4.2.1)
- time on source: 2.2 ksec  
  > "The data was taken with an on-source exposure of 2.2 ksec on 2015 March 14, when 37 antennas were operated." (3.2 ALMA)
- observing dates: 2015 March 14  
  > "The data was taken with an on-source exposure of 2.2 ksec on 2015 March 14, when 37 antennas were operated." (3.2 ALMA)
- pi or archival as stated: Program of PI N. Nagar (archival data, found via JVO)  
  > "We utilized the Band 6 ($\sim$ 270 GHz) ALMA data with the program ID = #2012.1.00474.S (PI: N. Nagar)." (3.2 ALMA)
- Line: CO J = 2–1 (230.538 GHz)
- Other facility **Chandra/ACIS-S**: ObsID 883 imaging, ~45 ks, Fe-Kα and continuum maps and spectra  
  > "We analyzed one *Chandra*/ACIS-S ((cite: Gar03)) imaging data of NGC 2110 (ObsID = 883)" (3.1 Chandra data)
- External data: Unabsorbed 2–10 keV luminosity range 0.4–3.5e43 erg/s over epochs  
  > "Un-absorbed 2–10 keV luminosity was estimated in various epochs, and varied within 0.4–3.5$\times10^{43}$ erg s$^{-1}$(cite: Mar15)." (5.2) [from (cite: Mar15)]
- External data: H2 gas surface density of 650 Msun/pc^2 in the central region with faint CO emission  
  > "by adopting a hydrogen molecular gas surface density of 650 $M_\odot$ pc$^{-2}$ in the central region with faint CO($J$ = 2–1) emission" (5.2) [from (cite: Ros19)]
- External data: Hα+[N II] distribution used for comparison with CO rings (Figure 3 of Rosario+10)  
  > "the distribution of the H$\alpha$+\[N II\] emission, drawn based on Figure 3 in (cite: Ros10)" (5.3) [from (cite: Ros10)]
- Simulation/model as data: MARX Monte-Carlo simulations of nuclear-only Chandra emission (1000 images averaged) used to subtract the PSF  
  > "To mitigate uncertainty of each Monte-Carlo simulation result, we created 1000 images, and took their average." (4.1.2)

## Processing

### Calibration

- pipeline or manual: Reduced with CASA 4.2.2, same as ALMA Regional Center QA  
  > "ver. 4.2.2, the same as in the Quality Verification by the ALMA Regional Center" (4.2.1)
- casa version: CASA 4.2.2 for reduction; 5.1.1 for analysis  
  > "The ALMA data was reduced via the Common Astronomy Software Applications (CASA) (cite: McM07) with ver. 4.2.2" (4.2.1)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Ganymede (flux), J0423-0120 (bandpass), J0541-0541 (phase)  
  > "Standard flux, bandpass, and phase calibrations were made by observing Ganymede, J0423-0120, and J0541-0541, respectively." (3.2 ALMA)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: clean (CASA 5.1.1)  
  > "The product was then deconvolved by the `clean` task with the Briggs-weighting with robust = 0.5 and gain = 0.1." (4.2.1)
- deconvolver: _not stated_
- weighting robust: Briggs robust = 0.5, gain = 0.1  
  > "The product was then deconvolved by the `clean` task with the Briggs-weighting with robust = 0.5 and gain = 0.1." (4.2.1)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: uvcontsub with 1st-order fit to line-free channels  
  > "continuum level was determined by fitting line-free channels with the 1st-ordered function, and was subtracted from the data cube via the task `uvcontsub`." (4.2.1)
- line free channels: _not stated_
- primary beam correction: impbcor  
  > "The primary beam image correction was made via `impbcor`." (4.2.1)
- array combination: _not stated_
- smoothing: Channels binned to ~10 km/s  
  > "The channels were binned so that the velocity resolution was $\approx$ 10 km s$^{-1}$." (4.2.1)
- final beam: 0.52x0.83 arcsec (line); 0.49x0.81 arcsec (continuum)  
  > "The achieved synthesized beam was $0.49\times0.81$ arcsec$^2$ with P.A. = $-73.80$ degrees." (4.2.1)
- final rms: 0.76 mJy/beam from emission-free channels  
  > "This was estimated from the CO emission-free channels." (4.2.1)

### Inherited from earlier work

- Molecular gas mass of the red component from Equation (1) of Rosario+19  
  > "By adopting Equation (1) in (cite: Ros19), the molecular gas mass was estimated to be $\sim10^{6}~M_{\rm sun}$." (4.2.2) [from (cite: Ros19)]
- Flow-rate formula (thin shell geometry)  
  > "the equation we considered was the same as for a thin shell-like geometry (i.e., Equation (4) of (cite: Mai12))." (4.2.2) [from (cite: Mai12)]
- XDR effective ionization parameter formulation  
  > "We quantitatively discuss the physical origin of the anti-correlation, while referring to an XDR model (cite: Mal96)." (5.2) [from (cite: Mal96)]
- Photon index fixed to 1.65  
  > "the photon indices of the power-law components were fixed to 1.65, a canonical value suggested from past studies of NGC 2110 (cite: Eva07; Kaw16b)." (4.1.2) [from (cite: Eva07; Kaw16b)]
- C-statistic goodness-of-fit procedure  
  > "Goodness of fit was examined by following the procedure given in (cite: Kaa17)." (4.1.2) [from (cite: Kaa17)]

### Not stated but needed to reproduce (our reading)

- Line-free channel ranges for uvcontsub
- clean mask, threshold, niter and image/cell size
- Which ALMA execution blocks/ calibration scripts were used and any flux scale uncertainty
- 3D Barolo input settings (fit mode, ring-fitting weights, normalisation, mask threshold details)
- Initial guesses for PA and Vrot/sigma
- Exact CASA 4.2.2 vs 5.1.1 steps and which products were re-calibrated
- XSPEC version and the exact Ikeda torus model implementation
- MARX simulation parameters (aspect, dither, exposure)
- Source regions' exact geometry in sky coordinates

## Analysis recipe

1. **Reduce Chandra data and make images**: Reprocess with chandra_repro, filter background flares (~45 ks left), make sub-pixel-repositioned images in 3.0–6.0 and 6.2–6.5 keV, smooth with Gaussian FWHM 0.492 arcsec  
  > "The raw data was reprocessed with the standard `chandra_repro` command." (3.1 Chandra data); "Then, we made smoothing via a Gaussian kernel with FWHM = 0.492 arcsec, corresponding to the ACIS CCD pixel size." (4.1.1)
   - software: CIAO, CALDB, pileup_map
   - parameter: CIAO 4.9, CALDB 4.7.6; sub-pixel 0.0615 arcsec  
  > "Our analysis utilized the standard data analysis package CIAO (ver. 4.9) and a calibration database of CALDB (ver. 4.7.6)." (3.1 Chandra data)
   - fitting: _not stated_
   - validation: Absolute astrometry checked against radio peak (offset ≈0.15 arcsec; no correction)  
  > "This differed only by $\approx$ 0.15 arcsec from the radio emission peak" (3.1 Chandra data)
2. **Model the nuclear spectrum and simulate the nuclear PSF**: Fit 1–2 arcsec annulus spectrum (0.5–7 keV) with absorbed+unabsorbed power laws, two Gaussians, apec; define nuclear part as absorbed PL plus lines; simulate with MARX, average 1000 images  
  > "The 0.5–7.0 keV spectrum was fitted with absorbed and un-absorbed power-law components, two Gaussian functions (`zgauss` in XSPEC terminology)" (4.1.2)
   - software: XSPEC, MARX
   - parameter: Gamma fixed 1.65; line widths fixed 0.1 eV; MARX 5.3.3  
  > "Also, because of the CCD poor energy resolution, we fixed the line widths at 0.1 eV." (4.1.2)
   - fitting: C-statistic; acceptable if Cobs < Cexp + 1.28 sqrt(Cvar)  
  > "A model would be acceptable at the 90% confidence level if $C_{\rm obs} < C_{\rm exp} + 1.28\times \sqrt{C_{\rm var}}$" (4.1.2)
   - validation: Compared radial profiles of observed and simulated images; consistent except a factor ~2 in innermost pixels  
  > "Although a factor of $\sim$ 2 difference was seen in the innermost pixels, this would be due to incompleteness of the simulation software" (4.1.2)
3. **Map extended Fe-Kα via ratio image**: Subtract simulated nuclear images, take ratio of 6.2–6.5 to 3.0–6.0 keV at 0.49 arcsec pixels, exclude pixels with <2 counts in 3–6 keV, smooth FWHM 1.0 arcsec  
  > "The image of the ratios was smoothed with the Gaussian kernel with FWHM = 1.0 arcsec." (4.1.2)
   - software: CIAO
   - fitting: _not stated_
   - validation: Ratio image changes with count criterion but extended morphology generally seen; consistent with model-independent 6.2–6.5 keV image and spectra  
  > "However, the extended morphology can be seen generally in most cases." (4.1.2)
4. **Spatially resolved Fe-Kα spectroscopy**: Four 90-degree fan regions (2–5 arcsec) fitted with power law + Gaussian plus fixed nuclear component; NW and SE also fitted with Ikeda torus reflection model  
  > "Their inner and outer radii were 2 arcsec and 5 arcsec, respectively." (4.1.3); "We further fitted a reflection model of the Ikeda torus model (cite: Ike09) to the spectra in the NW and SE regions" (4.1.3)
   - software: CIAO specextract, XSPEC
   - parameter: Torus half opening angle 60 deg, inclination 30 deg, Gamma 1.65  
  > "The half opening angle and our inclination angle from the polar axis were by default set to 60 degrees and 30 degrees." (4.1.3)
   - fitting: C-statistic; spectra binned to >=1 count per bin  
  > "The spectra were binned so as to have at least one count at each bin." (4.1.3)
   - validation: Delta Cobs ~12 with vs without line in NW and SE  
  > "The difference in $C_{\rm obs}$ between the models with and without the line was found $\sim$ 12 in the NW and SE cases" (4.1.3)
5. **Make CO(2–1) cubes and moment maps**: uvcontsub, clean (Briggs 0.5), impbcor, moments over 1900–2800 km/s; moments 1,2 with 5 sigma clipping  
  > "The zeroth moment was calculated over the $V_{\rm LSR}$ range of 1900–2800 km s$^{-1}$." (4.2.1)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
6. **Fit tilted-ring model to CO kinematics**: 3D Barolo with rings every 0.25 arcsec from 0.75 arcsec; fixed centre (radio), Vsys 2335 km/s, thickness 0.5 arcsec; free Vrot, sigma, inclination, PA; initial i=65 deg  
  > "We determined the free parameters every 0.25 arcsec from the starting point at 0.75 arcsec, given the beam size of $0.52\times0.83$ arcsec$^2$." (4.2.2)
   - software: 3D Barolo
   - parameter: Channels 1900–2800 km/s above 5 sigma (3.8 mJy/beam)  
  > "Our fit took account of channels in the velocity range 1900 km s$^{-1}$–2800 km s$^{-1}$ with significance larger than 5$\sigma$ (= 3.8 mJy beam$^{-1}$)." (4.2.2)
   - assumption: i=65 deg chosen because it gives monotonically increasing rotation curve; i=53 deg gives same conclusions  
  > "Finally, our choice ($i$ = 65 degrees) was made because we obtained a rotation curve that monotonously increased with radius" (4.2.2)
   - fitting: Beam-smearing-aware tilted-ring fit; sampler/priors not stated  
  > "A fit of the concentric titled rings to the observed CO($J$ = 2–1) data was made by adopting the 3D Barolo code (cite: Dit15). This code takes account of beam-smearing of an intrinsic structure." (4.2.2 Geometrical structure and kinetic properties of CO gas)
   - validation: Moment-1 residual map and PV diagrams; scale heights consistent with assumed 80 pc thickness  
  > "This range is consistent with the assumed thicknesses (i.e., 80 pc) of the rings." (4.2.2)
7. **Estimate ionization parameter in NW/SE**: Compute xi_eff = 0.1 L44/(n4 R100^2 N22^alpha) with L(1–100 keV) 2–15e43 erg/s, n=120–270 cm^-3 from Σ=650 Msun/pc^2 and thickness 50–110 pc, R=3 arcsec, N_H~3e23  
  > "As a result, the ionization parameters in NW and SE are conservatively calculated to be $\log \xi_{\rm eff} > -2.4$." (5.2)
   - parameter: alpha = (Gamma+2/3)/(8/3) ≈ 0.87 for Gamma=1.65  
  > "Note that this index corresponds to $\alpha\approx$ 0.87." (5.2)
   - assumption: Uniform gas density distribution  
  > "where we assume the uniform gas density distribution" (5.2)
   - fitting: _not stated_
   - validation: Expected N_H compared with spectral-fit N_H < 1e23  
  > "This is close to the upper bound of those from the spectral fittings" (5.2)

## Software

- **CIAO** 4.9: Chandra data reduction and spectral extraction  
  > "Our analysis utilized the standard data analysis package CIAO (ver. 4.9)" (3.1 Chandra data)
- **CALDB** 4.7.6: Chandra calibration database  
  > "a calibration database of CALDB (ver. 4.7.6)" (3.1 Chandra data)
- **MARX** 5.3.3: Monte-Carlo simulation of nuclear emission/PSF  
  > "Our simulations were made using a Monte-Carlo simulator of the MARX software (ver. 5.3.3; (cite: Dav12))" (4.1.2)
- **XSPEC** : Spectral fitting (zgauss, apec models)  
  > "two Gaussian functions (`zgauss` in XSPEC terminology)" (4.1.2)
- **CASA** 4.2.2 (reduction); 5.1.1 (analysis): ALMA reduction, uvcontsub, clean, impbcor, imfit  
  > "and then was analyzed via the CASA with ver. 5.1.1." (4.2.1)
- **3D Barolo** : Tilted-ring fit of CO velocity field  
  > "A fit of the concentric titled rings to the observed CO($J$ = 2–1) data was made by adopting the 3D Barolo code (cite: Dit15)." (4.2.2)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Nuclear annulus Fe-Kα EW | 152 | +141/-107 | eV | 2 | The equivalent width of the Fe-K$\alpha$ line was 152$^{+141}_{-107}$ eV |
| Fe-Kα EW in NW and SE regions | 1.5 (NW), 1.6 (SE) | +2.1/-1.0 (NW); +2.6/-1.1 (SE) | keV | 4 | EW$_{\rm Fe-K{\alpha}}$ / — / 1.5$^{+2.1}_{-1.0}$ / 1.6$^{+2.6}_{-1.1}$ / — / keV |
| Extended-to-nuclear Fe-Kα ratio | ~7 | not stated | percent | 4 | The ratio between the sum of the NW and SE extended components and the unresolved nuclear one was estimated to be $\sim$ 7%. |
| Nuclear N_H (annulus fit) | 4.0 | +0.7/-0.6 | 1e22 cm^-2 | 2 | $N_{\rm H}$ / $4.0^{+0.7}_{-0.6}$ / 10$^{22}$ cm$^{-2}$ |
| Intrinsic 2–10 keV luminosity of nucleus | 3.7e42 | not stated | erg/s | 2 | $L_{\rm 2-10~keV,PL}$ / 3.7 / 10$^{42}$ erg s$^{-1}$ |
| CO(2–1) synthesized beam | 0.52x0.83, PA -75.17 | not stated | arcsec, deg | 5 | The achieved synthesized beam was $0.52\times0.83$ arcsec$^2$ with P.A. = $-75.17$ degrees. |
| CO cube RMS | 0.76 | not stated | mJy/beam | 5 | The final continuum-subtracted data had a RMS noise of 0.76 mJy beam$^{-1}$. |
| Molecular mass of SE red component | ~1e6 | not stated | Msun | 6 | the molecular gas mass was estimated to be $\sim10^{6}~M_{\rm sun}$. |
| Characteristic flow rate | ~0.2 | not stated | Msun/yr | 6 | the characteristic flow rate was calculated to be $\sim$ 0.2 $M_{\rm sun}$ yr$^{-1}$. |
| Vrot/sigma ratio at 160–640 pc | 0.05–0.15 | not stated | dimensionless | 6 | The ratios between the rotation velocity and velocity dispersion were $\approx$ 0.05–0.15 in the range 160–640 pc. |
| Ring thickness | 50–110 | not stated | pc | 6 | the thicknesses, $\approx2\times$ the scale heights, were estimated to be within $\sim$ 50–110 pc. |
| Molecular gas density | 120–270 | not stated | cm^-3 | 7 | The density of the molecular hydrogen gas is estimated to be 120–270 cm$^{-3}$ |
| Effective ionization parameter in NW/SE | log xi_eff > -2.4 | lower limit | dimensionless | 7 | the ionization parameters in NW and SE are conservatively calculated to be $\log \xi_{\rm eff} > -2.4$. |

## Qualitative findings

- Fe-Kα emission extends NW-SE out to ~3 arcsec (~500 pc) per side, anti-correlated with CO(2–1) which is brighter in NE and SW islands  
  > "Their spatial anti-correlation is seen; the CO emission is stronger in the northeast and southwest islands" (5.2)

## Claim tuples

- H: Is there extended Fe-Kα fluorescence tracing nuclear X-ray irradiation? | E: Chandra ratio image and fan-region spectral fits after nuclear PSF subtraction | R: Significant Fe-Kα only in NW and SE, EW ~1.5 keV, ~7% of nuclear | F: Fe-Kα extends NW-SE to ~500 pc, consistent with fluorescence from nuclear irradiation | **supported**
- H: Does X-ray irradiation account for weak CO(2–1) in the irradiated regions? | E: Estimate xi_eff from XDR model with CO-derived density and disk thickness | R: log xi_eff > -2.4 | F: High enough for CO and/or H2 dissociation or super-thermal CO, though not conclusive | **partially**
- H: What is the geometry of the torus/ionization cone? | E: Compare CO tilted rings with optical Hα+[N II] and [O III] asymmetry | R: Polar axis inclination ≲30 deg | F: Nucleus viewed at an intermediate angle | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Fe-Kα maps trace X-ray-irradiated dense gas with little stellar contamination  
  > "Little contamination from stellar light above 7.1 keV (cite: LaM12; Kaw13; Lam17) is also an advantage to purely trace regions subject to AGN emission." (Introduction)
- Alternative: Jet, scattering and collisional ionization rejected as Fe-Kα origin; low CO opacity judged unlikely  
  > "Also, the collisional ionization would be unlikely as the primary process because a lower EW is expected" (5.1)
- How they decided it was enough: _not stated_
- Limitation (authors): Anti-correlation is tentative; H2 dissociation conflicts with Spitzer-based H2 surface density of Rosario+19; follow-up observations needed  
  > "The tentative spatial anti-correlation between the Fe-K$\alpha$ and CO($J$ = 2–1) emission was found" (6 Summary)
- Caveat (inferred, ours): Fe-Kα detection in NW/SE rests on low counts (Delta C ~12) with large EW uncertainties
- Caveat (inferred, ours): Photon index in some fan regions is unphysical (negative), so continuum is poorly constrained
- Caveat (inferred, ours): Short 2.2 ks ALMA exposure, with nuclear CO sensitive to continuum subtraction and resolution
- Caveat (inferred, ours): Constant-density and R=3 arcsec assumptions in xi_eff with order-of-magnitude uncertainties
- Caveat (inferred, ours): Anti-correlation is qualitative with no statistical test

## Reproducibility

- Data public (paper): ALMA data from archive program 2012.1.00474.S; Chandra ObsID 883 from Chandra Data Archive  
  > "The scientific results reported in this article are based on data obtained from the Chandra Data Archive." (Acknowledgments)
- Products in archive: _not stated_
- Code: _not stated_
- Missing: clean parameters (mask, threshold, niter, imsize, cell)
- Missing: line-free channel selection
- Missing: 3D Barolo parameter file
- Missing: XSPEC model definitions and region files
- Data volume (inferred): ~10-30 GB for ALMA raw plus ~0.1 GB Chandra
- Score (inferred): 3/5, Public data and key parameters given (robust, beam, rms, Barolo setup), but imaging and fit details are missing and the X-ray part needs specialist modelling.
- Rediscovery candidate: no, Key results are mostly X-ray based with many unstated settings, and the ALMA part is a supporting piece.

## Links

- Method: (cite: Dit15) (3D Barolo tilted-ring code)
- Method: (cite: Mal96) (XDR model and effective ionization parameter)
- Method: (cite: Kaa17) (C-statistic goodness of fit)
- Companion: (cite: Ros19) (CO(2–1) and H2 study of NGC 2110 that found weak CO region)
- Companion: (cite: Fab19b) (Soft X-ray photons in the weak-CO region)
- Companion: (cite: Ram19) (Also studied CO(2–1) kinematics of NGC 2110)

## Checks

```json
{
 "quotes": 90,
 "quotes_ok": 90,
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
  "facts": 91,
  "stated": 66,
  "rate": 0.725
 },
 "evidence_ok": true
}
```
