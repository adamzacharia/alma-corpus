# ALMA view of RX J1131-1231: Sub-kpc CO (2-1) mapping of a molecular disk in a lensed star-forming quasar host galaxy

`2018A&A...613A..34P` | Astronomy and Astrophysics 2018 | first author: Paraficz, D. | arXiv: 1705.09931 | DOI: 10.1051/0004-6361/201731250

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies, agn_and_quasars
- Question: What are the distribution, kinematics and intrinsic properties of the molecular gas in the lensed quasar host galaxy RX J1131-1231, recovered by source reconstruction of ALMA CO(2-1) visibilities?  
  > "to study the distribution and kinematics of the molecular gas in the host galaxy of RX  J1131$-$1231" (1 Introduction)
- Target **RX J1131-1231**: coordinates _not stated_; z/distance z_q = 0.654 (quasar), z_l = 0.295 (lens)  
  > "It consists of four images of a $z_q = 0.654$ quasar" (1 Introduction); "lensed by a foreground early-type galaxy at $z_l$ = 0.295" (1 Introduction); distance from Sluse et al. 2003, 2007 (cite: 2003A&A...406L..43S; 2007A&A...468..885S)  
  > "It consists of four images of a $z_q = 0.654$ quasar" (1 Introduction); "lensed by a foreground early-type galaxy at $z_l$ = 0.295" (1 Introduction)

## Data provenance

- ALMA projects: 2013.1.01207.S
- bands: Band 4 (145 GHz)  
  > "The data, obtained in Band 4 (145 GHz)" (1 Introduction)
- frequencies and spectral setup: 3 continuum SPWs (128 channels, 2 GHz each) at 137.169, 149.118, 150.993 GHz; one line SPW at 139.044 GHz with 480 channels, 1.875 GHz bandwidth, 8.4 km/s per channel  
  > "One spectral window was used in spectral line mode, centred on the redshifted CO (2-1) line at 139.044 GHz, with 480 spectral channels and a total bandwidth of 1.875 GHz." (2.1 Atacama Large Millimetre Array)
- continuum bandwidth: _not stated_
- arrays: 12 m array, 37 of 54 antennas  
  > "using 37 out of 54 of the 12 m array antennas" (2.1 Atacama Large Millimetre Array)
- configurations: _not stated_
- baselines: 27.5 m to 1.6 km  
  > "projected baselines between 27.5 m and 1.6 km" (2.1 Atacama Large Millimetre Array)
- angular resolution: _not stated_
- max recoverable scale: about 16.2 arcsec  
  > "which provided a sensitivity to structures with a largest angular size of about 16.2$''$" (2.1 Atacama Large Millimetre Array)
- sensitivity: _not stated_
- time on source: about 2.5 h total, about 1.3 h on-source  
  > "The total observing time was about 2.5 h, with about 1.3 h on-source." (2.1 Atacama Large Millimetre Array)
- observing dates: 2015 July 19  
  > "RX  J1131$-$1231 was observed with ALMA on 2015 July 19" (2.1 Atacama Large Millimetre Array)
- pi or archival as stated: PI D. Paraficz  
  > "(Proposal Code: 2013.1.01207.S; PI: D. Paraficz)" (2.1 Atacama Large Millimetre Array)
- Line: CO 2-1 (230.538 GHz)
- Other facility **Herschel SPIRE**: 250, 350, 500 um flux densities for the SED  
  > "The target was observed at 250, 350 and 500 $\mu$m for 90-s using the Spectral and Photometric Imaging Receiver (SPIRE)" (2.2 Herschel Space Observatory)
- Other facility **VLA**: 4.86 GHz archival A-configuration imaging  
  > "RX  J1131$-$1231 was observed with the VLA at 4.86 GHz on 2008 December 29" (2.3 Very Large Array)
- Other facility **HST**: optical/infrared imaging of the host Einstein ring  
  > "The host galaxy of the quasar is seen as a prominent Einstein ring in optical and infrared imaging" (1 Introduction)
- External data: Stellar mass M* = 3.0±1.0e10 Msun from magnification-corrected SED  
  > "the latter derived by (cite: 2017ApJ...836..180L) from the magnification corrected optical/infrared spectral energy distribution" (5.3 Dynamical mass and CO–H$_2$ conversion factor) [from (cite: 2017ApJ...836..180L)]
- External data: Comparison samples of galaxies for L'CO, LIR, SFE  
  > "in comparison, as in (cite: 2010ApJ...713..686D), with various local and distant samples of dusty star-forming galaxies" (5.4 Comparison with far-infrared bright galaxy populations) [from (cite: 2010ApJ...713..686D)]

## Processing

### Calibration

- pipeline or manual: standard ALMA pipeline in CASA  
  > "The data were reduced and calibrated using the standard ALMA pipeline using the Common Astronomy Software Application package" (2.1 Atacama Large Millimetre Array)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Titan and Ganymede; bandpass J1058+0133; delays J1118-1232; phase reference J1130-1449  
  > "Titan and Ganymede were used to determine the absolute flux-density calibration" (2.1 Atacama Large Millimetre Array)
- flux scale uncertainty: _not stated_
- self calibration: not used (insufficient S/N)  
  > "Self-calibration was not used as there was an insufficient signal-to-noise ratio on the continuum emission to provide good calibration solutions." (2.1 Atacama Large Millimetre Array)

### Imaging

- task: CASA standard clean  
  > "were also carried out within casa using the standard clean method" (2.1 Atacama Large Millimetre Array)
- deconvolver: _not stated_
- weighting robust: continuum Briggs robust 0 and 2; line cube natural  
  > "Images were made using a Briggs weighting scheme with a robust parameter of 0 and 2 (2 being equivalent to natural weighting)" (2.1 Atacama Large Millimetre Array)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: mask with 3-sigma detection threshold  
  > "These data were cleaned using a mask and a detection threshold of $3-\sigma$" (2.1 Atacama Large Millimetre Array)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: continuum 0.28x0.24 arcsec (robust 0), 0.41x0.34 arcsec (robust 2); cube 0.44x0.36 arcsec  
  > "The resulting beam size is $0.44\ensuremath{''} \times 0.36\ensuremath{''}$" (2.1 Atacama Large Millimetre Array)
- final rms: continuum 15 and 10 uJy/beam; cube about 340 uJy/beam per 8.4 km/s channel  
  > "with an rms map noise of about 340 $\mu$Jy beam$^{-1}$ for a 8.4 km s$^{-1}$ channel width" (2.1 Atacama Large Millimetre Array)

### Inherited from earlier work

- Visibility-domain lens modelling technique  
  > "using the visibility-fitting lens modelling technique (see (cite: Rybak2015b; Rybak2015a))" (4 Lens modelling and source reconstruction) [from (cite: Rybak2015b; Rybak2015a)]
- Bayesian pixellated source reconstruction on adaptive Delaunay tessellation  
  > "an extension to the visibility domain of the Bayesian pixellated technique developed by (cite: 2009MNRAS.392..945V)" (4 Lens modelling and source reconstruction) [from (cite: 2009MNRAS.392..945V)]
- L'CO calculation  
  > "which corresponds to a line luminosity of $L'_{CO}= 1.2\pm0.3\times10^{10}$ K km s$^{-1}$ pc$^2$ (see Solomon at al 1997)" (5.1 CO (2-1) intensity and velocity distribution) [from Solomon et al. 1997]

### Not stated but needed to reproduce (our reading)

- Line-free channels used for continuum imaging
- Clean threshold, cell and image size
- Lens-model sampler, priors and optimisation details
- Regularisation form H and prior ranges
- Modified blackbody fit method and photometry for SED
- Dust and temperature assumptions for LIR and SFR conversion
- How magnification of 7.3 was derived
- Uncertainty derivation for dynamical mass and alpha
- Surface density used for the Toomre Q

## Analysis recipe

1. **Image continuum and CO cube**: CASA clean continuum (robust 0, 2) and natural-weighted cube; moments 0,1,2 for S/N>3  
  > "intensity weighted velocity (moment-one) and velocity dispersion (moment-two) maps were made using those pixels with a signal-to-noise ratio $>3$" (2.1 Atacama Large Millimetre Array)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Fit lens mass model on visibilities**: Fit elliptical power-law main lens plus isothermal satellite, with external shear, to all CO channels combined in visibility space  
  > "We find the best fitting mass distribution parameters $\boldsymbol{\eta}_{best}$ by combining all channels in the CO (2-1) emission line together" (4 Lens modelling and source reconstruction)
   - parameter: eight free parameters  
  > "our mass model has eight free parameters" (4 Lens modelling and source reconstruction)
   - assumption: Gaussian uncorrelated noise  
  > "(assumed to be Gaussian and uncorrelated)" (4 Lens modelling and source reconstruction)
   - fitting: Penalty function with chi2 plus regularisation lambda^2||Hs||^2  
  > "The optimisation is performed in the visibility space via the following penalty function" (4 Lens modelling and source reconstruction)
   - validation: Compared with HST and Keck lens models; within 2 sigma  
  > "are in agreement generally within 2-$\sigma$ with those derived by" (4 Lens modelling and source reconstruction)
3. **Reconstruct source per velocity channel**: Split into 8 channels of 84 km/s, remodel each with mass model fixed  
  > "We then split the data into eight velocity channels and remodel them individually by keeping the mass model fixed" (4 Lens modelling and source reconstruction)
   - fitting: _not stated_
   - validation: Good agreement between observed and model image plane data  
  > "which shows a good agreement between the observed and model image plane data" (4 Lens modelling and source reconstruction)
4. **Dust SED, LIR and SFR**: Modified blackbody fit to FIR and mm continuum; LIR 8-1000 um and SFR  
  > "modified black body spectrum that was fitted to the far-infrared and mm-wavelength continuum emission" (5.2 Star-formation rate, far-infrared luminosity and dust mass)
   - software: HIPE
   - assumption: dust traced by molecular gas, same magnification mu_CO = 7.3  
  > "we assume that the dust emission is traced by the molecular gas distribution and hence has the same magnification ($\mu_{CO} = 7.3$)" (5.2 Star-formation rate, far-infrared luminosity and dust mass)
   - fitting: _not stated_
   - validation: _not stated_
5. **Dynamical mass, Toomre Q, alpha_CO**: Rotation curve from major axis of 8 bins, M=sigma^2 R/G; Toomre Q; gas mass from Mdyn minus 30% dark matter and stellar mass  
  > "we estimate the gas mass by assuming a contribution of 30% from the dark matter halo" (5.3 Dynamical mass and CO–H$_2$ conversion factor)
   - assumption: gas virialized; inclination 54 deg from axial ratio  
  > "The rotation curve is corrected for the inclination of the disk $i=54^{\circ}$" (5.3 Dynamical mass and CO–H$_2$ conversion factor)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : pipeline calibration, imaging, VLA calibration  
  > "The data were reduced and calibrated using the standard ALMA pipeline using the Common Astronomy Software Application package" (2.1 Atacama Large Millimetre Array)
- **HIPE** 14.2.1: Herschel SPIRE processing  
  > "processed within the Herschel Interactive Processing Environment (HIPE; version 14.2.1)" (2.2 Herschel Space Observatory)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Intrinsic CO(2-1) line intensity | 2.06 | 0.43 | Jy km/s | 3 | $I_{\rm CO}=2.06\pm0.43$ Jy km s$^{-1}$ |
| L'CO | 1.2e10 | 0.3e10 | K km/s pc^2 | 3 | $L'_{CO}= 1.2\pm0.3\times10^{10}$ K km s$^{-1}$ pc$^2$ |
| CO major-axis FWHM | 9.4 | 1.0 | kpc | 3 | The major-axis FWHM of the CO (2-1) surface brightness distribution is 9.4$\pm$1.0 kpc. |
| Dust temperature | 21.0 | +6.0/-4.6 | K | 4 | $T_{\rm dust} = 21.0^{+6.0}_{-4.6}$ K |
| SFR | 69 x (7.3/mu_IR) | +41/-25 | Msun/yr | 4 | ${\rm SFR} = 69^{+41}_{-25} \times (7.3 / \mu_{\rm IR})$ M$_{\odot}$ yr$^{-1}$ |
| Dynamical mass within 5 kpc | 1.46e11 | 0.31e11 | Msun | 5 | $M(r<5~{\rm kpc})=1.46\pm0.31 \times 10^{11}$ M$_\odot$ |
| Toomre Q | 1.07 | not stated | dimensionless | 5 | $Q = 1.07$ for the RX  J1131$-$1231 molecular gas distribution |
| CO-H2 conversion factor | 5.5 | 2.0 | Msun (K km/s pc^2)^-1 | 5 | $\alpha = 5.5\pm2.0$ M$_{\odot}$ (K km s$^{-1}$ pc$^2$)$^{-1}$ |

## Qualitative findings

- CO(2-1) forms a complete Einstein ring; reconstructed source is a clumpy rotating disk with two spiral arms, ~21 kpc extent  
  > "We find that the CO (2-1) emission has a complex distribution that is clumpy, showing a two spiral arm structure." (5.1 CO (2-1) intensity and velocity distribution)

## Claim tuples

- H: Is the molecular gas in the quasar host a rotating disk? | E: Source reconstruction of CO(2-1) visibilities in 8 velocity channels | R: Velocity field typical of rotating disk, Q=1.07, extent ~21 kpc | F: Extended, stable rotating molecular disk | **supported**
- H: Are the gas properties like those of quasars or disk galaxies? | E: Compare L'CO, SFE, size, alpha_CO with literature samples | R: alpha=5.5, size ~10 kpc similar to BzK and spirals | F: Host resembles disk galaxies rather than high-z quasars | **supported**

## Reasoning

- Why this data: Lensing magnification plus ALMA resolution enables sub-kpc mapping  
  > "we take advantage of both the enhanced spatial resolution provided by ALMA and of the magnifying power of strong gravitational lensing" (1 Introduction)
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): SED fit limited by differential magnification precision and lack of short-wavelength data  
  > "This fit is limited by the precision of differential magnification and the lack of short wavelength data" (5.2 Star-formation rate, far-infrared luminosity and dust mass)
- Caveat (inferred, ours): Dynamical mass from simple virial estimate with assumed 30% dark matter
- Caveat (inferred, ours): alpha_CO depends on assumed stellar mass from another paper
- Caveat (inferred, ours): Single-magnification assumption for dust vs CO

## Reproducibility

- Data public (paper): ALMA data cited by project code; public status not explicitly stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA 2013.1.01207.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Lens modelling code and settings
- Missing: Priors and sampler details
- Missing: Line-free channel selection
- Data volume (inferred): ~20-50 GB
- Score (inferred): 3/5, Data identified by project code, but the visibility lens-modelling code and settings are not given.
- Rediscovery candidate: no, Key results depend on a custom visibility-plane lens modelling code with incomplete settings.

## Links

- Method: (cite: Rybak2015b; Rybak2015a) (visibility-domain lens modelling)
- Method: (cite: 2009MNRAS.392..945V) (Bayesian pixellated source reconstruction)
- Companion: Sluse et al. 2017 (ALMA continuum flux ratios and microlensing)
- Related: COSMOGRAIL

## Checks

```json
{
 "quotes": 60,
 "quotes_ok": 60,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 74,
  "stated": 45,
  "rate": 0.608
 },
 "evidence_ok": true
}
```
