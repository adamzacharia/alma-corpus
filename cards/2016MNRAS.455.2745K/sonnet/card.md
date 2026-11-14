# ALMA probes the molecular gas reservoirs in the changing-look Seyfert galaxy Mrk 590

`2016MNRAS.455.2745K` | Monthly Notices of the Royal Astronomical Society 2016 | first author: Koay, J. Y. | arXiv: 1509.09203 | DOI: 10.1093/mnras/stv2495

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, agn_and_quasars
- Question: Is the AGN in Mrk 590 turning off because of a lack of central molecular gas to fuel it?  
  > "We investigate if the active galactic nucleus (AGN) of Mrk 590, whose supermassive black hole was until recently highly accreting, is turning off due to a lack of central gas to fuel it." (abstract)
- Target **Mrk 590**: coordinates RA 02h14m33.5s, Dec -00d46m00s (J2000)  
  > "Redshift | 0.0264 | 1" (Table 1); "Luminosity distance, ${D_{\rm L}}^a$ | 115.4 Mpc" (Table 1); z/distance z = 0.0264; D_L = 115.4 Mpc; 1'' = 531 pc  
  > "Redshift | 0.0264 | 1" (Table 1); "Luminosity distance, ${D_{\rm L}}^a$ | 115.4 Mpc" (Table 1); distance from redshift from NED, adopted cosmology (Om=0.3, OL=0.7, H0=70)  
  > "Redshift | 0.0264 | 1" (Table 1); "Luminosity distance, ${D_{\rm L}}^a$ | 115.4 Mpc" (Table 1)

## Data provenance

- ALMA projects: 2013.1.00534.S
- bands: Band 7  
  > "The source was observed in Band 7 with four separate spectral windows centred at sky frequencies of 336.7 GHz, 338.0 GHz, 346.8 GHz, and 348.7 GHz." (2.1 ALMA Observations)
- frequencies and spectral setup: 4 spws; CO(3-2) and HCO+(4-3) in FDM with 0.488 MHz channels, 1.875 GHz each; 2 TDM continuum spws with 15.625 MHz channels  
  > "configured to Frequency Division Mode (FDM) with channel widths of 0.488 MHz and a total bandwidth of 1.875 GHz per spectral window." (2.1 ALMA Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: CO cube beam 0.47'' x 0.42'' (P.A. -76 deg); Briggs continuum beam 0.34'' x 0.24''  
  > "We obtain a synthesized beam size of 0$\ensuremath{''}$47 $\times$ 0$\ensuremath{''}$42 at a position angle, P.A., of $-76^{\circ}$." (2.1 ALMA Observations)
- max recoverable scale: ~4'' (2 kpc)  
  > "We estimate the maximum recoverable scale to be $\sim 4''$ (2 kpc) based on the shortest projected baselines" (3.2 CO Maps and Spectra)
- sensitivity: CO 1sigma ~0.5 mJy/beam per 20 km/s channel; continuum rms 0.031-0.109 mJy/beam depending on weighting  
  > "down to the image sensitivity limits of 1$\sigma \sim 0.5{\rm\,mJy\,beam^{-1}}$ in the central 150 pc" (3.4 Molecular Gas Masses)
- time on source: 1.8 hours on source, 31 antennas, two execution blocks  
  > "Mrk 590 was observed with 31 antennas for a total duration of 1.8 hours on source, over two execution blocks." (2.1 ALMA Observations)
- observing dates: 2014 July 27 (Cycle 2)  
  > "Observations were carried out with ALMA during Cycle 2 on 2014 July 27." (2.1 ALMA Observations)
- pi or archival as stated: _not stated_
- Line: 12CO J=3-2 (345.7959 GHz)
- Line: HCO+ J=4-3 (not stated)
- Other facility **SMA**: 219 GHz continuum and CO(2-1) upper limits at ~3'' resolution  
  > "These ALMA data are complemented by Submillimetre Array (SMA) observations of the $^{12}$CO(2–1) emission line, albeit at a lower angular resolution of $\sim 3''$." (1 Introduction)
- Other facility **VLA (NVAS archive)**: 8.4 GHz A-configuration continuum image  
  > "We extracted 8.4 GHz Very Large Array (VLA) continuum data of Mrk 590 from the NRAO VLA Archive Survey (NVAS)" (2.3.1 VLA)
- Other facility **HST/ACS**: F550M V-band image and structure map  
  > "observed on 2003 December 18 with an exposure time of 1020 s using the F550M (*V*-band) filter (proposal ID: 9851)" (2.3.2 HST)
- External data: Near-IR to far-IR and radio flux densities used for SED fit (UKIRT, VLT, ISO, IRAS, OVRO, VLA, MERLIN)  
  > "We include in our analysis published measurements (summarised in Table [\[continuumfluxpub\]]) of the near-IR to far-IR flux densities of Mrk 590" (4.4.1 Thermal Dust Emission) [from (cite: wardetal87; horstetal09; garciaespinosa01; edelsonetal87; edelson87; kukulaetal95; theanetal01)]
- External data: Narrow H-alpha flux 1.2e-14 erg/s/cm2 from 2013 LBT spectrum  
  > "The narrow H$\alpha$ line has a flux of $1.2 \times 10^{-14 }\,\rm erg\,s^{-1}\,cm^{-2}$ (cite: denneyetal14)" (3.7.2 SFR from Halpha) [from (cite: denneyetal14)]
- External data: Black hole mass 4.75e7 Msun from reverberation mapping  
  > "based on a black hole mass of $4.75 \times 10^7\,{M}_{\odot}$ measured from reverberation mapping (cite: petersonetal04)" (4.2.1 Gas Consumption Time-scales) [from (cite: petersonetal04)]
- External data: CO(1-0) single-dish fluxes of Mrk 590 (55'' beam)  
  > "Based on the single dish $^{12}$CO(1–0) integrated flux densities (cite: maiolinoetal97), we obtain $M({\rm H_2}) \sim 7.9 \times 10^9 \,M_{\odot}$ within the 55$''$ beam" (3.4 Molecular Gas Masses) [from (cite: maiolinoetal97)]

## Processing

### Calibration

- pipeline or manual: Calibration done at Italian ARC node as quality assurance; authors re-examined calibrated data and tables and flagged  
  > "Calibration was performed as part of the quality assurance by the Italian node of the European ALMA Regional Centre." (2.1 ALMA Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0238+166 (flux); J0217+0144 gain; J0224+0659 bandpass  
  > "The quasar J0238+166 was used to set the absolute flux scales of the target source." (2.1 ALMA Observations)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA clean; uvcontsub; impbcor; imfit; immoments  
  > "Imaging and deconvolution were performed using the `clean` task in CASA." (2.1 ALMA Observations)
- deconvolver: _not stated_
- weighting robust: Continuum: natural, Briggs robust=0.5, uniform; CO cube: natural  
  > "We produced three separate images, for each image using a different weighting scheme: natural, Briggs (robustness $= 0.5$) or uniform weighting." (2.1 ALMA Observations)
- uv taper: 300,000 times the central observed wavelength of the CO spw  
  > "We applied uv-tapering at a lengthscale (uv-distance) of $300,000$ times the central observed wavelength of the CO spectral window" (2.1 ALMA Observations)
- cell size: 0.05'' pixels  
  > "We generated images of 640 pixels $\times$ 640 pixels with pixel sizes of $0.05\ensuremath{''} \times 0.05\ensuremath{''}$." (2.1 ALMA Observations)
- image size: 640 x 640 pixels  
  > "We generated images of 640 pixels $\times$ 640 pixels with pixel sizes of $0.05\ensuremath{''} \times 0.05\ensuremath{''}$." (2.1 ALMA Observations)
- masking: Iterative 4 sigma mask per channel; 4000 clean iterations, gain 0.05, repeated five times  
  > "we applied a mask generated by selecting pixels with intensities greater than $4 \sigma$ (with $\sigma$ calculated over the entire image) in each channel." (2.1 ALMA Observations)
- multiscale scales: _not stated_
- continuum subtraction: uvcontsub using line-free channels in the CO spw  
  > "channels without line emission within the spectral window were used to model the continuum emission." (2.1 ALMA Observations)
- line free channels: _not stated_
- primary beam correction: impbcor  
  > "Thereafter, we applied primary beam corrections to the image intensities using the task `impbcor`." (2.1 ALMA Observations)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- SED fitting model (greybody + near-IR power law)  
  > "The fitting procedure, the model SED and the model parameters are described in further detail by (cite: casey12)." (Appendix) [from (cite: casey12)]
- SFR from Kennicutt-Schmidt relation and Halpha calibration  
  > "we estimate the SFR in the central 150 pc to be ${\rm SFR(H_2)} \lesssim 2 \times 10^{-4}\,M_{\odot}\, \rm yr^{-1}$ following the Kennicutt-Schmidt relation (cite: kennicutt98)." (3.7.1) [from (cite: kennicutt98)]

### Not stated but needed to reproduce (our reading)

- Channel ranges treated as line-free for uvcontsub
- CASA version
- Exact uv-taper implementation parameters in clean
- Details of KinMS fit priors, sampler and parameter grid
- SED fit initial values/free-parameter bounds and uncertainty treatment
- Region definitions for spectra extraction (apertures, components A-F)
- Conversion from L_FIR to SFR and dust mass calculation (opacity)

## Analysis recipe

1. **Image continuum and fit source**: Combine continuum + HCO+ spws, clean with three weightings, fit 2D Gaussian with imfit  
  > "We used the CASA task `imfit` to fit a 2-dimensional Gaussian distribution to this compact component in all three images." (3.1 Continuum Maps)
   - software: CASA
   - fitting: _not stated_
   - validation: Compared position with 8.4 GHz VLA source; checked jet-like feature with tapered image  
  > "The 344 GHz continuum emission also spatially coincides with the unresolved 8.4 GHz radio source in the NVAS image" (3.1 Continuum Maps)
2. **Make CO(3-2) cube and moment maps**: Continuum subtraction, tapered natural-weighted 20 km/s cube, masked clean, pb correction, moments with 3 sigma clip  
  > "In generating these moment maps, we set pixels with less than 3$\sigma$ intensities in the channel maps to zero." (3.2)
   - software: CASA, GILDAS
   - fitting: _not stated_
   - validation: _not stated_
3. **Model inner ring kinematics**: Fit rotating annulus to velocity map  
  > "We confirmed this using the Kinematic Molecular Simulation software of (cite: davisetal13)." (3.3)
   - software: KinMS
   - fitting: best fit of numerous trial models; not well constrained  
  > "we quote the best fit solution of numerous trial models." (3.3)
   - validation: _not stated_
4. **Derive H2 mass upper limits and masses**: 3 sigma integrated flux limit assuming FWHM 230 km/s, convert to L'CO(3-2) and to M(H2) with alpha_CO and CO ratio  
  > "the $3\sigma$ upper limit of the integrated flux can be estimated to be: $$\begin{equation} \label{uplimit} I \leq 3\sigma \Delta v_{\rm FWHM} \sqrt{\dfrac{\Delta v}{\Delta v_{\rm FWHM}}} \end{equation}$$" (3.4)
   - parameter: sigma=0.5 mJy/beam, dv=20 km/s, FWHM=230 km/s  
  > "For $\sigma = 0.5{\rm\,mJy\,beam^{-1}}$ and channel widths of $\Delta v = 20\,{\rm km\,s^{-1}}$" (3.4)
   - assumption: alpha_CO=0.8 and L'32/L'10=0.9 (central); MW 4 and 0.27 (conservative)  
  > "Assuming these values of $\alpha_{\rm CO}$ and $L'_{\rm CO(3-2)}/L'_{\rm CO(1-0)}$, we obtain a stronger upper limit of $M({\rm H_2}) \lesssim 1.6 \times 10^5\, {M_{\odot}}$" (3.4)
   - fitting: _not stated_
   - validation: Checked non-continuum-subtracted cubes for broad CO components  
  > "we examined the spectra of the inner 150 pc using the datacubes without continuum subtraction" (3.4)
5. **Upper limits on HCO+ and CO(2-1)**: Same limit equation with assumed line widths  
  > "Following Equation [\[uplimit\]], we constrain the velocity-integrated flux density of HCO$^+$(4–3) to $I_{\rm HCO(4-3)} \lesssim \rm 0.48\, Jy\,km\,s^{-1}$" (3.5)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
6. **Estimate star formation rates**: Kennicutt-Schmidt relation from M(H2); Halpha luminosity  
  > "We derive the SFR using two independent methods, (1) based on the Kennicutt-Schmidt relation using $M({\rm H_2})$" (3.7)
   - assumption: negligible HI in the centre  
  > "We note that our SFR limits assume negligible HI gas masses in the centre." (3.7.1)
   - fitting: _not stated_
   - validation: SFR(Halpha) compared to SFR(H2)  
  > "SFR(H$\alpha$) is also consistent with the estimated $\rm SFR{(H_2)}$ in the central 4$''$, to within the uncertainties arising from the use of different conversion factors" (3.7.2 SFR Estimate Derived from the Halpha Luminosity)
7. **Fit IR-mm SED**: Greybody plus near-IR power law fit with ALMA 344 GHz point (and separately SMA)  
  > "We use the far-IR SED fitting code developed by (cite: casey12) to fit a near-IR power-law distribution and a modified blackbody (greybody) spectrum" (4.4.1)
   - software: Casey (2012) SED code
   - parameter: beta fixed at 1.5; other five parameters free  
  > "We fix the mean emissivity index of dust particles at the typical value of $\beta = 1.5$" (Appendix)
   - assumption: dust to gas ratio ~0.01, solar metallicity  
  > "Adopting a dust to total gas mass ratio of $\sim 0.01$ and assuming solar metallicities" (4.4.1)
   - fitting: _not stated_
   - validation: Discussed heterogeneous beams, flux scaling, variability caveats  
  > "We note that there will be large uncertainties associated with the SED model-fitting, and in the parameters (e.g., dust temperatures, dust masses and total far-IR luminosity) derived from the fitted model." (Appendix: IR Continuum SED Modelling and Caveats)

## Software

- **CASA** : Imaging, continuum subtraction, moments, imfit, SMA processing  
  > "Further data processing and imaging were carried out using the Common Astronomy Software Applications (CASA) package" (2.1)
- **GILDAS** : Channel maps  
  > "These channel maps were generated using the GILDAS software package" (3.2)
- **KinMS** : Kinematic model of inner ring  
  > "We confirmed this using the Kinematic Molecular Simulation software of (cite: davisetal13)." (3.3)
- **sma2casa.py / smaImportFix.py** : Convert SMA data to CASA ms  
  > "The SMA data were converted to FITS-IDI files using the Python script `sma2casa.py`" (2.2 SMA Observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| M(H2) upper limit, central 150 pc (alpha_CO=0.8, ratio 0.9) | 1.6e5 | upper limit | Msun | 4 | constraining the central molecular gas mass to $M({\rm H_2}) \lesssim 1.6 \times 10^5\, {M_{\odot}}$ |
| M(H2) upper limit, central 150 pc (MW values) | 5.3e6 | upper limit | Msun | 4 | This value of $5.3 \times 10^6\, {M_{\odot}}$ is a very conservative upper limit of $M(\rm H_2)$. |
| CO(3-2) flux upper limit, central 150 pc | 0.1 | upper limit (3 sigma) | Jy km/s | 4 | $I _{\rm CO(3-2)} \leq 0.1\,{\rm  Jy\,km\,s^{-1}}$ |
| Integrated CO(3-2) flux, central 4'' | 3.33 | not stated | Jy km/s | 4 | we obtain an integrated flux density of 3.33 $\rm Jy\,km\,s^{-1}$ over all channels with CO line emission |
| Integrated CO(3-2) flux, primary beam | 8.34 | not stated | Jy km/s | 4 | we obtain a total velocity-integrated flux density of 8.34 $\rm Jy\,km\,s^{-1}$ |
| Gaussian FWHM of CO(3-2) spectrum, inner 4'' | 231 | 80 | km/s | 2 | we obtain FWHM widths of $231 \pm 80 \, \rm km\,s^{-1}$ for the inner 4$^{\prime\prime}$ integrated spectrum |
| Inner ring annulus radius from KinMS model | 0.93 | 0.01 | kpc | 3 | a rotating annulus of radius (to midpoint) of 0.93$\pm$0.01 kpc and a width of 65 pc |
| Ring inclination from model | 64 | +3/-1 | degrees | 3 | an inclination angle of 64$\substack{+3\\-1}$ degrees to our line of sight and a mean rotational velocity of 117 km s$^{-1}$ |
| ALMA 344 GHz Briggs integrated flux density | 0.830 | 0.048 | mJy | 1 | Briggs                  / 0.036                   / $0.34 \times 0.24$      / $-$67.45                / $0.263 \times 0.069$    / $93.0^{\circ}$          / $0.830 \pm 0.048$ |
| Eddington-limited gas consumption time for 1.6e5 Msun | 2.6e5 | not stated | yr | 4 | there is potentially sufficient gas to support the AGN activity in Mrk 590 for $2.6 \times 10^5$ years at the Eddington accretion limit |
| SED dust temperature (ALMA fit) | 53 | not stated | K | 7 | The dust temperature of the far-IR component is estimated from the model SED to be 53 K |
| Dust mass (ALMA fit) | ~1e5 | not stated | Msun | 7 | The model SED yields a dust mass of $M_{\rm dust}\sim 10^5\, M_{\odot}$. |
| Spectral index 8.4 GHz to 344 GHz | -0.36 | not stated | dimensionless | 7 | we estimate the spectral index to be $\alpha^{8.4\,{\rm GHz}}_{344\,{\rm GHz}} \sim −0.36$ |
| HCO+(4-3)/CO(3-2) ratio upper limit, central 4'' | 0.14 | upper limit | dimensionless | 5 | We obtain upper limits of $R^{\rm HCO43}_{\rm CO32} \lesssim 0.14$ |

## Qualitative findings

- Two CO ring structures (~1 kpc elliptical and ~3 kpc circular) with no CO detected in central ~150 pc; bright clump ~200 pc west with disturbed kinematics  
  > "We observe two ring-like CO gas structures (Figure [4]): an outer ‘circular ring’ at a radius of $\sim 6''$ (3 kpc) from the centre of the galaxy" (3.2)
- No strong molecular outflows detected in integrated spectra  
  > "Therefore, it is unlikely that *strong* molecular outflows are responsible for depleting the circumnuclear gas in Mrk 590." (4.2.3)

## Claim tuples

- H: The Mrk 590 AGN is turning off because the central gas is exhausted | E: ALMA CO(3-2) mapping and gas mass upper limit in central 150 pc | R: M(H2) <~ 1.6e5 Msun, enough for 2.6e5 yr of Eddington accretion | F: Cannot rule out a temporary feeding break; AGN may turn on again | **partially**
- H: Mrk 590 has less kpc-scale gas than other Seyferts | E: Compare inner 2 kpc and primary-beam H2 masses to NUGA and other Seyferts | R: M(H2) ~1e7-1.7e8 Msun, comparable | F: No significant deficit at kpc scales | **supported**
- H: Gas is being transported toward the centre | E: Kinematic analysis of ring and clump C | R: Clump ~200 pc west with velocity deviation up to 80 km/s from rotation | F: Clump may be refuelling the centre | **partially**
- H: Origin of the central 344 GHz continuum | E: SED fit and spectral index comparison with radio | R: T ~53 K dust, L_FIR-based SFR far above SFR(H2); alpha ~ -0.36 | F: Likely AGN-heated dust; synchrotron/free-free not excluded | **partially**

## Reasoning

- Why this data: ALMA's resolution and sensitivity allow measuring or tightly constraining central molecular gas mass at ~100 pc scales  
  > "The combination of high angular resolution and high sensitivity observations provided by ALMA enable us to measure the mass of the molecular gas (or place very strong constraints on it) in the centre of Mrk 590." (1 Introduction)
- Why this method: _not stated_
- Alternative: Rotating annulus vs expanding shell (~115 km/s) both consistent with inner ring  
  > "the morphology and kinematics of the inner $^{12}$CO(3–2) gas structure is also consistent with an expanding shell (radial velocity $\sim$115 km s$^{-1}$)" (3.3)
- How they decided it was enough: _not stated_
- Limitation (authors): Kinematic model not well constrained; potential unknown CO excitation and alpha_CO; missing flux from spatial filtering  
  > "We emphasize that this rotational model is not well constrained by the $^{12}$CO(3–2) data alone" (3.3); "There is also very likely to be missing flux not recovered in our interferometric images due to spatial filtering of the extended emission." (3.4)
- Caveat (inferred, ours): Gas mass limit depends strongly on assumed alpha_CO and CO excitation ratio
- Caveat (inferred, ours): Only a partial array/sensitivity; line width of 230 km/s assumed for the limit
- Caveat (inferred, ours): SED fit uses mismatched beams and non-contemporaneous data
- Caveat (inferred, ours): Kinematic model crude with no quoted fit procedure

## Reproducibility

- Data public (paper): ALMA project cited in acknowledgements; HST, VLA data from public archives  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2013.1.00534.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Line-free channel selection
- Missing: CASA version
- Missing: KinMS fit details
- Missing: SED fit code settings
- Data volume (inferred): ~10-30 GB raw
- Score (inferred): 3/5, Imaging recipe fairly detailed, and key numbers derive from simple equations, but several settings (versions, channel selection, KinMS, SED fit) are missing.
- Rediscovery candidate: yes, ALMA data are archival-public after proprietary period and the main results (gas mass limits, fluxes) are numeric and computable from described steps.

## Links

- Method: (cite: casey12) (SED fitting code)
- Method: (cite: davisetal13) (KinMS kinematic modelling)
- Method: (cite: wrobelwalker99) (Upper limit on integrated flux)
- Companion: (cite: denneyetal14) (Documents the changing-look behaviour of Mrk 590)
- Related: NUGA

## Checks

```json
{
 "quotes": 83,
 "quotes_ok": 83,
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
  "facts": 86,
  "stated": 57,
  "rate": 0.663
 },
 "evidence_ok": true
}
```
