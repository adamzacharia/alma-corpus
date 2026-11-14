# Simultaneous radio and optical polarimetry of GRB 191221B afterglow

`2023NatAs...7...80U` | Nature Astronomy 2023 | first author: Urata, Yuji | arXiv: 2212.05085 | DOI: 10.1038/s41550-022-01832-7

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: transients
- Question: Is the radio (97.5 GHz) polarization of the GRB 191221B afterglow depolarized relative to the optical, and what does this say about magnetic field configuration and cool electrons / jet energy?  
  > "show that the emission is depolarized in the radio band compared to the optical one." (abstract)
- Target **GRB 191221B**: coordinates _not stated_; z/distance z = 1.148  
  > "The redshift was measured as $z =1.148$ based on metal absorption lines in the optical afterglow observed by VLT/X-shooter(cite: gcn26553)." (Introduction); distance from VLT/X-shooter metal absorption lines (cite: gcn26553)  
  > "The redshift was measured as $z =1.148$ based on metal absorption lines in the optical afterglow observed by VLT/X-shooter(cite: gcn26553)." (Introduction)

## Data provenance

- ALMA projects: 2019.1.01016.T, 2019.1.01484.T
- bands: Band 3, 97.5 GHz polarization; photometry at 145 and 203 GHz  
  > "Four epochs (0.5, 1.5, 2.5, and 9.5 days) of observations were performed with the polarization mode at 97.5 GHz (i.e., Band 3)." (Methods)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: ALMA and ACA  
  > "A total of 11 epochs of radio observations were conducted using the Atacama Large Millimetre/submillimetre Array (ALMA) and Atacama Compact Array" (Methods)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: 11 epochs from 0.5 to ~33 days after burst  
  > "| 33.444 |        97.5        |  0.200 $\pm$ 0.019   |" (Table 3)
- pi or archival as stated: _not stated_
- Other facility **VLT/FORS2**: R-band imaging polarimetry at 2.5 days  
  > "Polarimetric observations were acquired using the Focal Reducer and low dispersion Spectrograph (FORS2) mounted on the VLT." (Methods)
- Other facility **VLT/X-shooter**: Spectra at ~10 and ~34 hr to derive extinction  
  > "The VLT also obtained X-shooter spectra for the afterglow of GRB 191221B at $\sim 10$ and $\sim 34$ hr after the GRB onset." (Methods)
- Other facility **Swift/XRT**: X-ray spectra for N_H  
  > "The X-ray data obtained by the *Swfit*/XRT were collected from the UK Swift Science Data Centre" (Methods)
- External data: Optical polarimetry at 0.121 and 0.417 d (SALT/VLT)  
  > "The values for 0.121 and 0.417 days were derived in the wavelength range of $R$ band based on data reported by Buckley et al (2021)" (Table 2) [from Buckley et al. 2021 (cite: buckley21)]
- External data: Prompt emission E_iso and E_peak from Konus-Wind  
  > "$E_{\gamma, {\rm iso}}$ = $(3.6 \pm 0.4)\times10^{53}$ erg" (Introduction) [from (cite: gcn26576)]

## Processing

### Calibration

- pipeline or manual: Raw data reduced at EA-ARC with CASA  
  > "The raw data were reduced at the East Asian ALMA Regional Center (EA-ARC) using CASA (version 5.6.1)(cite: casa)." (Methods)
- casa version: CASA 5.6.1  
  > "using CASA (version 5.6.1)(cite: casa)" (Methods)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J1037-2934 (bandpass and flux); J1036-3744 phase; J1058+0133 polarization  
  > "the bandpass and flux were calibrated using observations of J1037-2934, and J1036-3744 was used for the phase calibration." (Methods)
- flux scale uncertainty: _not stated_
- self calibration: Interactive CLEAN with self-calibration  
  > "We further performed interactive CLEAN deconvolution imaging with self-calibration." (Methods)

### Imaging

- task: Interactive CLEAN of Stokes I, Q, U maps  
  > "The Stokes $I$, $Q$, and $U$ maps were CLEANed with an appropriate number of CLEAN iterations after the final round of self-calibration." (Methods)
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Optical polarimetric analysis details  
  > "More details on polarimetric data analysis are reported in Covino et al. (2003)(cite: covino03) and Wiersema et al. (2012)(cite: wiersema12)." (Methods) [from Covino et al. 2003 (cite: covino03); Wiersema et al. 2012 (cite: wiersema12)]

### Not stated but needed to reproduce (our reading)

- tclean parameters: weighting/robust, cell size, image size, masks
- Self-calibration solution intervals
- Beam sizes and image rms values
- Fitting method/priors for the afterglow model and light curve broken power law
- Numerical afterglow polarization code is not public
- ALMA configurations and on-source times
- Source coordinates

## Analysis recipe

1. **Calibrate and image ALMA Stokes I, Q, U**: CASA reduction, interactive CLEAN with self-calibration, derive PD and PA from Q, U, I  
  > "The quantities that can be derived from the polarization maps are the polarized intensity ($\sqrt{Q^2+U^2}$), polarization degree ($100\sqrt{Q^2+U^2}/I$ %, PD)" (Methods)
   - software: CASA
   - fitting: _not stated_
   - validation: Phase calibrator polarization stability <0.02%, consistent with 0.033% systematic  
  > "we confirm that the stability of linear polarization degree is $<$0.02 %" (Methods)
2. **Constrain dust-induced optical polarization**: Fit X-shooter UVB spectrum with power law plus SMC/LMC/MW extinction; Serkowski-law fit; X-ray N_H via XSPEC  
  > "We fit the afterglow spectrum in this wavelength range by a simple power-law affected by rest-frame extinction" (Methods)
   - software: XSPEC
   - fitting: _not stated_
   - validation: Compared with other GRBs with polarimetry  
  > "There are 8 known-$z$ GRB afterglows, including GRB 191221B, available with optical polarimetry and *Swift* X-ray observations." (Methods)
3. **Model afterglow light curves and SED**: Numerical forward-shock synchrotron model with Blandford-McKee solution, equal arrival time surface, fixed theta_j; adjust parameters to fit radio-optical-X-ray data  
  > "We performed numerical calculations of flux from the shock with a fixed $\theta_j$ which evolves as the Blandford-McKee (BM) self-similar solution" (Methods)
   - assumption: Uniform density medium, energy injection E_iso propto t^0.25  
  > "the ambient density is uniform and the energy continues to be injected to the shock by long activity of the central engine" (Methods)
   - fitting: _not stated_
   - validation: Model also explains X-ray and optical  
  > "The model also explains the X-ray and optical afterglows" (Introduction)
4. **Test polarization models**: Compare plasma-scale anisotropic field model and Faraday depolarization by cool electrons (one-zone, N random cells) with PD and PA data  
  > "the plasma in the visible region consist of $N$ random cells in each of which magnetic field is ordered." (Methods)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 5.6.1: ALMA and ACA calibration and imaging  
  > "The ACA data were flagged, calibrated, and imaged with standard procedures with CASA (version 5.6.1)." (Methods)
- **XSPEC** 12: X-ray spectral fitting  
  > "Using the software XSPEC 12, we perform spectral fitting" (Methods)
- **astropy** : custom optical polarimetry tools  
  > "We used custom software tools based on the python astropy library" (Methods)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Optical R-band PD at 2.5 d | 1.3 | 0.2 | % | 0 | linear polarization degree (PD) of 1.3 $\pm$ 0.2 % |
| Optical PA | 61.6 | 6.3 | deg | 0 | polarization angle (PA) of 61.6 $\pm$ 6.3 deg |
| Radio PD upper limit at 97.5 GHz | <0.6 (3 sigma) | not stated | % | 1 | The ALMA observation put the upper limit on PD of 0.6% with $3\sigma$ confidence level at 97.5 GHz. |
| Radio PA range | 37.7-52.3 | 1 sigma range | deg | 1 | constrained the range of PA as 37.7$-$52.3 deg with $1\sigma$ confidence level |
| 97.5 GHz light curve break time | 3.77 | 0.35 | days | 3 | a break-time at $3.77\pm 0.35$ days |
| Pre-break index alpha | 0.26 | 0.02 | dimensionless | 3 | $\alpha = 0.26\pm 0.02$ (before the break) |
| Post-break index alpha | -1.62 | 0.13 | dimensionless | 3 | $\alpha = -1.62\pm 0.13$ (after the break) |
| Upper limit on non-thermal electron fraction f | <~0.3 | not stated | dimensionless | 4 | This leads to an upper limit $f \lesssim 0.3$. |
| Extinction E(B-V) | <0.038 (95%) | not stated | mag | 2 | E$_{\rm B-V} < 0.038$ (95% upper limit) |
| Intrinsic N_H | 1.6 | +0.9/-0.8 | 1e21 cm^-2 | 2 | $N_{H}=1.6^{+0.9}_{-0.8}\times10^{21}$ |

## Qualitative findings

- Radio emission is depolarized relative to optical; PAs differ; SSA does not explain it.  
  > "this simultaneous polarimetry between optical and radio bands indicates depolarization in the radio band." (Introduction)

## Claim tuples

- H: Radio emission is depolarized relative to optical | E: Simultaneous ALMA 97.5 GHz and VLT R-band polarimetry at 2.5 d | R: Radio PD <0.6% vs optical 1.3% | F: Depolarization in the radio band | **supported**
- H: Plasma-scale (Weibel) anisotropic field explains the depolarization | E: Numerical polarization model vs PD, PA and temporal evolution | R: Predicts same PA or 90 deg difference and too high early PD | F: Disfavored | **refuted**
- H: Faraday depolarization by cool electrons explains it | E: One-zone Faraday depolarization model | R: Requires f <~ 0.3 | F: Jet energy increased by factor >4 | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Reverse shock origin of radio emission rejected as requiring eps_e ~0.53 or ~1  
  > "requires $\epsilon_e \sim 0.53$. This value is unusually high" (Methods)
- Alternative: Dust-induced optical polarization disfavored by low extinction  
  > "an intrinsic origin (i.e., due to the afterglow) of the observed polarisation compared to the dust-induced hypothesis appears to be more in agreement with the data." (Methods)
- How they decided it was enough: _not stated_
- Limitation (authors): PA difference between radio and optical only ~90% significant  
  > "the PA between radio and optical is different at $\sim$90% confidence level." (Methods)
- Caveat (inferred, ours): Only one epoch of simultaneous polarimetry; radio PD only an upper limit
- Caveat (inferred, ours): Model parameters are degenerate and uncertainties not given
- Caveat (inferred, ours): Faraday model one-zone and PA difference only qualitatively explained

## Reproducibility

- Data public (paper): ALMA data in ALMA Science Archive; VLT in ESO archive  
  > "The ALMA data are available at ALMA Science Archive. The VLT data are available at ESO Science Archive Facility." (Data availability)
- Products in archive: _not stated_
- Code: Theory code not public  
  > "The theoretical calculation code of flux and polarization used in this work is not publicly available." (Code availability)
- Missing: Imaging parameters
- Missing: Model fitting procedure
- Missing: Unreleased theory code
- Data volume (inferred): ~100 GB to a few hundred GB
- Score (inferred): 3/5, Public data and photometry tables, but imaging and model fitting details and code are missing.
- Rediscovery candidate: no, Key results depend on unreleased theoretical code and unspecified imaging settings.

## Links

- Method: Shimoda & Toma 2021 (cite: shimoda21) (Multi-band afterglow polarization model)
- Method: Toma et al. 2008 (cite: toma08) (Faraday depolarization by cool electrons)
- Companion: Buckley et al. 2021 (cite: buckley21) (Early optical spectropolarimetry)
- Companion: Urata et al. 2019 (cite: urata19) (First radio polarization detection in a GRB afterglow)

## Checks

```json
{
 "quotes": 50,
 "quotes_ok": 50,
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
  "facts": 70,
  "stated": 34,
  "rate": 0.486
 },
 "evidence_ok": true
}
```
