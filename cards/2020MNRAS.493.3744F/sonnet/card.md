# SMM J04135+10277: a distant QSO-starburst system caught by ALMA

`2020MNRAS.493.3744F` | Monthly Notices of the Royal Astronomical Society 2020 | first author: Fogasy, Judit | arXiv: 2002.06925 | DOI: 10.1093/mnras/staa472

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: agn_and_quasars, high_z_galaxies
- Question: What are the dust continuum, molecular gas content and CO excitation of the quasar and its star-forming companion in SMM J04135+10277, and is the quasar really gas-poor?  
  > "Our goal is to constrain the excitation properties of SMM J04135+10277 through modelling of the spectral line energy distribution (SLED) of both sources" (Introduction)
- Target **SMM J04135+10277 (QSO and companion)**: coordinates QSO 04:13:27.28 +10:27:40.41; Companion 04:13:26.98 +10:27:37.89  
  > "R.A.                                |    04:13:27.28    |    04:13:26.98" (Table 2); "the quasar–star-forming companion galaxy system SMM J04135+10277 ($z=2.84$)" (Introduction); z/distance z=2.84 (CO z=2.8460 QSO, 2.8438 companion)  
  > "R.A.                                |    04:13:27.28    |    04:13:26.98" (Table 2); "the quasar–star-forming companion galaxy system SMM J04135+10277 ($z=2.84$)" (Introduction); distance from CO lines from this work; z_UV from Knudsen et al. 2003  
  > "R.A.                                |    04:13:27.28    |    04:13:26.98" (Table 2); "the quasar–star-forming companion galaxy system SMM J04135+10277 ($z=2.84$)" (Introduction)

## Data provenance

- ALMA projects: 2015.1.00661.S
- bands: Band 4 and Band 6  
  > "to cover the redshifted CO(5-4) line in band 4, and to 239.648 GHz to cover the redshifted CO(8-7) line in band 6" (2 Observations)
- frequencies and spectral setup: One 1.875 GHz SPW at 149.843 GHz (Band 4) and 239.648 GHz (Band 6); three 2 GHz SPWs per band for continuum  
  > "The other three spectral windows of each band, with a bandwidth of 2 GHz each, were used to observe the continuum." (2 Observations)
- continuum bandwidth: _not stated_
- arrays: 12-m array, 37 (Band 4) and 44 (Band 6) antennas  
  > "observed with the 12-m ALMA array during cycle 3" (2 Observations)
- configurations: C40-4 (Band 4), C36-2/3 (Band 6)  
  > "Configuration                              | C40-4                   | C36-2/3" (Table 1)
- baselines: _not stated_
- angular resolution: 1.01x0.92 arcsec (Band 4); 1.0x0.78 arcsec (Band 6)  
  > "Beam size ($\ensuremath{''}$)              | $1.01\times0.92$        | $1.0\times0.78$" (Table 1)
- max recoverable scale: _not stated_
- sensitivity: Continuum RMS 27.8 uJy/beam (B4), 46.7 uJy/beam (B6); line RMS 0.32 and 0.38 mJy/beam at 77 km/s  
  > "$0.32$                  | $0.38$" (Table 1)
- time on source: 10.6 min (B4), 10.1 min (B6)  
  > "$\rm T_{\rm exp}$ (min)                    | 10.6                    | 10.1" (Table 1)
- observing dates: 2016-06-02 (B4), 2016-03-31 (B6)  
  > "Date                                       | 2016-06-02              | 2016-03-31" (Table 1)
- pi or archival as stated: Own proposal, P.I. Fogasy  
  > "(project code 2015.1.00661.S; P.I.: Fogasy)" (2 Observations)
- Line: CO 5-4 (not stated)
- Line: CO 8-7 (not stated)
- Other facility **SCUBA / ArTeMiS**: Single-dish submm data for the FIR SED  
  > "To complement our ALMA observations we used previous SCUBA and ArTeMiS data to obtain the SED" (3.1)
- External data: CO(1-0) line luminosity and width of companion; QSO 3 sigma upper limit  
  > "(cite: 2016ApJ...827...18S) reported a line luminosity of $L_{\rm CO(1-0)}^{'}=(8.6\pm1.7)\times10^{10}\, \rm K\,km\,s^{-1}\,pc^{2}$" (3.3) [from (cite: 2016ApJ...827...18S)]
- External data: CO(1-0) and CO(3-2) observations used in SLED  
  > "combined with CO(1-0) and CO(3-2) line observations from the literature" (3.4) [from (cite: 2013ApJ...765L..31R)]
- External data: Lensing magnifications mu_QSO=1.3, mu_Comp=1.6  
  > "$\mu_{\rm QSO}=1.3$ (cite: 2003A&A...411..343K); $\mu_{\rm Comp.}=1.6$ (cite: 2013ApJ...765L..31R)" (Table 3) [from (cite: 2003A&A...411..343K); (cite: 2013ApJ...765L..31R)]
- External data: SCUBA data and z_UV  
  > "($z_{\rm UV}=2.837\pm0.003$; (cite: 2003A&A...411..343K))" (3.2) [from (cite: 2003A&A...411..343K)]
- Simulation/model as data: Empirical IR SED template grid of 105 templates  
  > "The grid includes 105 templates with a wide range of infrared luminosities." (3.1)

## Processing

### Calibration

- pipeline or manual: ALMA Science Pipeline  
  > "The calibration of the data was done using the ALMA Science Pipeline." (2 Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Flux calibration redone with updated flux values due to ~10% variability; J0423-0120 was bandpass calibrator  
  > "the flux calibration was redone with updated flux values" (2 Observations)
- flux scale uncertainty: 10% absolute flux error, not included in reported flux densities  
  > "we assume a conservative 10% absolute flux calibration error, which is not included in the flux densities reported in this paper" (2 Observations)
- self calibration: _not stated_

### Imaging

- task: CASA CLEAN with ARC Node provided scripts  
  > "To image the data we used the Common Astronomy Software Applications (CASA; (cite: 2007ASPC..376..127M)) with the ARC Node provided scripts." (2 Observations)
- deconvolver: _not stated_
- weighting robust: Natural weighting (Briggs robust 0.5 and -1.0 only for GalPak tests)  
  > "using natural weighting" (2 Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: Continuum fit to line-free channels per SPW, subtracted in uv-plane with UVCONTSUB  
  > "was subtracted in the $uv$-plane using the UVCONTSUB task in CASA" (2 Observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: 77 km/s channel width  
  > "imaged with $77\,\rm km\,s^{-1}$ channel width" (2 Observations)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Imaging scripts provided by the ARC node  
  > "with the ARC Node provided scripts" (2 Observations) [from Nordic ARC node scripts]
- UV-to-IR SED of the companion  
  > "The UV-to-IR SED of the companion galaxy was constructed in (cite: 2017A&A...597A.123F)" (3.1) [from (cite: 2017A&A...597A.123F)]
- SFR-L_IR relation  
  > "$\rm SFR\sim\delta_{MF}\times10^{-10}\,\it L_{\rm IR}$ (cite: 2013ARA&A..51..105C)" (3.1) [from (cite: 2013ARA&A..51..105C)]
- alpha_CO=0.8 for starbursts  
  > "we adopt a conversion factor of $\alpha_{\rm CO}=0.8" (3.3) [from (cite: 1998ApJ...507..615D)]

### Not stated but needed to reproduce (our reading)

- Updated flux values used to redo flux calibration
- CASA and pipeline versions
- Line-free channels and clean thresholds/masks, cell and image size
- Rest frequencies and integration windows for line fluxes
- MR-MOOSE priors and setup, and ArTeMiS/SCUBA fluxes used
- RADEX grid step sizes and observed SLED inputs with errors
- How continuum fluxes and sizes were measured (fitting method)
- Which Gaussian fitting procedure was used for spectra

## Analysis recipe

1. **Image continuum and measure source fluxes**: Natural-weighted CLEAN continuum images; fluxes and sizes of QSO and companion measured  
  > "We applied the CLEAN algorithm to create the continuum images and line data cubes using natural weighting." (2 Observations)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Fit FIR SED and derive L_IR and SFR**: MR-MOOSE Bayesian fit of ALMA+SCUBA+ArTeMiS, and alternative Chary & Elbaz templates  
  > "MR-MOOSE simultaneously fits the SEDs of the quasar and the companion, and the total emission when it is impossible to resolve sources individually" (3.1)
   - software: MR-MOOSE
   - parameter: 25% QSO contribution assumed in SCUBA bands for templates  
  > "For the SCUBA bands we assumed a $25\%$ contribution from the quasar, based on the ALMA detections." (3.1)
   - assumption: Dust heated by star formation; Chabrier IMF; lensing corrected  
  > "assuming that the dust is heated by star formation" (3.1)
   - fitting: Bayesian (MR-MOOSE); templates chosen as best fit to ALMA points  
  > "As the SED templates have no free parameters, we chose the templates that fit our ALMA detections the best." (3.1)
   - validation: Two approaches compared as lower and upper limits  
  > "the results of these two approaches can be treated as lower and upper limits" (3.1)
3. **Extract spectra and fit CO lines**: Spectra extracted from cubes and fitted with Gaussians for widths and integrated fluxes  
  > "We fitted the spectra using Gaussian line profiles in order to determine the line widths and velocity integrated fluxes of the sources." (3.2)
   - software: CASA
   - fitting: Single Gaussian  
  > "when fitting a single Gaussian profile" (3.2)
   - validation: _not stated_
4. **Kinematics of companion**: Moment 1/2 maps, PV diagram at -30 deg, GalPak3D rotating disk model  
  > "For the PV diagram we chose the angle towards the highest velocity gradient ($-30\ensuremath{^\circ}$)" (3.3)
   - software: GalPak3D
   - parameter: Exponential disk, arctan rotation curve, default settings  
  > "we use the default settings as the resolution of the data is insufficient to distinguish between different models" (Appendix A)
   - fitting: Bayesian parametric fit to cube  
  > "GalPak$^{\rm3D}$ is a Bayesian parametric tool to constrain galaxy parameters directly from three-dimensional data cubes" (Appendix A)
   - validation: Repeated with robust 0.5 and -1.0 cubes  
  > "we also repeated the fitting using the data cubes that were imaged using Briggs weighting with a robust parameter of 0.5 and -1.0" (Appendix A)
5. **CO luminosities and gas masses**: Solomon et al. 1997 L'CO equation; M_H2 = alpha_CO L'CO(1-0); QSO assuming thermalised CO(5-4)  
  > "We assume that the CO(5-4) transition is thermally excited" (3.4)
   - assumption: alpha_CO=0.8; lensing corrected; L'(4-3)/L'(1-0)=1 for QSO  
  > "we adopt a conversion factor of $\alpha_{\rm CO}=0.8" (3.4)
   - fitting: _not stated_
   - validation: _not stated_
6. **CO SLED excitation modelling**: RADEX grid of Tkin and nH2 with fixed N_CO, chi2 comparison to CO SLED J=1-8  
  > "We compared our observations with the models using $\chi^{2}$-analysis." (3.5)
   - software: RADEX
   - parameter: QSO: width 300 km/s, N_CO=1e16 cm-2; companion: 850 km/s, 1e17; Tkin 10-400 K, log nH2 2-7  
  > "run `RADEX` on a grid of $T_{\rm kin}=[10-400]\,\rm\,K$ and $\rm log(\it n_{\rm H_{2}})=[\rm 2-7]\,\rm\,cm^{-3}$" (3.5)
   - assumption: Spherical geometry, H2 only collision partner, CMB background at z=2.84  
  > "adopted spherical geometry and assumed that the only collisional partner of CO is molecular hydrogen" (3.5)
   - fitting: chi2 grid  
  > "We compared our observations with the models using $\chi^{2}$-analysis." (RADEX modelling of the CO spectra)
   - validation: _not stated_

## Software

- **CASA** : Calibration imaging, UVCONTSUB  
  > "To image the data we used the Common Astronomy Software Applications (CASA; (cite: 2007ASPC..376..127M))" (2 Observations)
- **MR-MOOSE** : SED fitting  
  > "we use the multi-wavelength SED fitting code MR-MOOSE" (3.1)
- **RADEX** : Non-LTE CO SLED modelling  
  > "We used the non-LTE molecular radiative transfer code `RADEX`" (3.5)
- **GalPak3D** : Kinematic disk model  
  > "we carry out a simple analysis of the kinematics, assuming a rotating system, using GalPak$^{\rm3D}$" (Appendix A)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Continuum flux QSO at 150 GHz | 0.399 | 0.015 | mJy | 1 | $0.399\pm0.015$ |
| Continuum flux companion at 150 GHz | 1.233 | 0.037 | mJy | 1 | $1.233\pm0.037$ |
| Continuum flux QSO at 240 GHz | 2.174 | 0.023 | mJy | 1 | $2.174\pm0.023$ |
| Continuum flux companion at 240 GHz | 7.64 | 0.30 | mJy | 1 | $7.64\pm0.30$ |
| T_dust QSO | 24 | 6 | K | 2 | $T_{\rm dust, QSO}=24\pm6\,\rm K$ |
| T_dust companion | 16 | 3 | K | 2 | $T_{\rm dust, Comp.}=16\pm3\,\rm K$ |
| L_FIR QSO (MR-MOOSE) | 2.1e12 | +1.7/-1.2 e12 | Lsun | 2 | $L_{\rm FIR, QSO}=(2.1^{+1.7}_{-1.2})\times10^{12}\,\rm L_{\ensuremath{\odot}}$ |
| L_FIR companion (MR-MOOSE) | 2.4e12 | 1e12 | Lsun | 2 | $L_{\rm FIR, Comp.}=(2.4\pm1)\times10^{12}\,\rm L_{\ensuremath{\odot}}$ |
| CO(5-4) FWHM companion | 1127 | 49 | km/s | 3 | $1127\pm49$ |
| CO(5-4) integrated flux companion | 8.77 | 0.50 | Jy km/s | 3 | $8.77\pm0.50$ |
| CO(5-4) integrated flux QSO | 2.50 | 0.22 | Jy km/s | 3 | $2.50\pm0.22$ |
| Molecular gas mass companion (CO(1-0)) | 6.8e10 | 1.4e10 | Msun | 5 | $(6.8\pm1.4)\times10^{10}\,\rm M_{\ensuremath{\odot}}$ |
| Molecular gas mass QSO (from CO(5-4)) | 2.3e10 | 0.2e10 | Msun | 5 | the molecular gas mass of the quasar is $(2.3\pm0.2)\times10^{10}\,\rm M_{\ensuremath{\odot}}$ |
| GalPak3D effective radius | 3.0 | 0.04 | kpc | 4 | effective radius of $3.0\pm0.04\,\rm kpc$ |

## Qualitative findings

- The QSO is bright in CO(5-4) and CO(8-7) despite low-J non-detections, so it hosts warm, highly excited gas.  
  > "This indicates that the host galaxy of the quasar has a significant amount of warm, highly-excited molecular gas." (3.2)

## Claim tuples

- H: The quasar host is gas-poor | E: CO(5-4) and CO(8-7) ALMA detections converted to gas mass | R: M_H2 ~ (0.7-2.3)e10 Msun | F: Quasar is not gas-poor; low-J non-detections reflect excitation | **supported**
- H: Companion dominates the dust emission | E: Resolved ALMA continuum | R: QSO ~22-25% of emission | F: Companion dominates | **supported**
- H: Broad CO lines of the companion arise from rotation | E: Moment maps, PV diagrams, GalPak3D | R: Consistent with rotation, resolution insufficient | F: Signs of rotation, possibly beam smeared; no outflow | **partially**
- H: CO SLED excitation can be constrained | E: RADEX chi2 grid | R: Degenerate temperature, density narrowed | F: Limited constraints | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): FIR SED poorly sampled so L_IR and SFR are lower limits; kinematics unresolved; SLED has too few points  
  > "adequate observations around the peak of the FIR SED are lacking" (4.1)
- Caveat (inferred, ours): Gas mass of QSO relies on assumed thermalised CO(5-4) and alpha_CO=0.8
- Caveat (inferred, ours): SED L_IR spans a wide range with few data points
- Caveat (inferred, ours): Short snapshot observations, beam-smeared kinematics

## Reproducibility

- Data public (paper): ALMA project code given  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2015.1.00661.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Updated flux calibrator values
- Missing: MR-MOOSE configuration and priors
- Missing: CLEAN parameters
- Missing: RADEX SLED input details
- Data volume (inferred): ~10-30 GB raw for two short EBs
- Score (inferred): 6/5, Public data and moderate recipe, but several imaging and fitting details missing.
- Rediscovery candidate: yes, Public data, short observations, numeric fluxes, line widths and gas masses reproducible.

## Links

- Method: (cite: 2018MNRAS.477.4981D) (MR-MOOSE SED fitting)
- Method: (cite: 2015AJ....150...92B) (GalPak3D)
- Method: (cite: 2007A&A...468..627V) (RADEX)
- Companion: (cite: 2013ApJ...765L..31R) (Interferometric low-J CO of the system)
- Companion: (cite: 2017A&A...597A.123F) (Earlier SED and GALFORM study)
- Companion: (cite: 2016ApJ...827...18S) (CO(1-0) detection of companion)

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
  "facts": 83,
  "stated": 55,
  "rate": 0.663
 },
 "evidence_ok": true
}
```
