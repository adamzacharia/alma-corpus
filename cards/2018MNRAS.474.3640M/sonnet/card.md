# CO excitation in the Seyfert galaxy NGC 34: stars, shock or AGN driven?

`2018MNRAS.474.3640M` | Monthly Notices of the Royal Astronomical Society 2018 | first author: Mingozzi, M. | arXiv: 1711.07995 | DOI: 10.1093/mnras/stx3011

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: nearby_galaxies, agn_and_quasars, astrochemistry
- Question: Whether and to what extent AGN X-ray radiation (versus stars/PDR or shocks) drives the CO excitation (CO SLED) in NGC 34  
  > "to constrain the properties of molecular gas, and assess whether, and to what extent, the radiation produced by the accretion onto the central black hole affects the CO line emission." (abstract)
- Target **NGC 34**: coordinates _not stated_; z/distance z≃0.0196; D_L=85.7 Mpc  
  > "yields a luminosity distance D$_L$=85.7 Mpc at $z \simeq0.0196$, with 1” corresponding to 0.4 kpc." (1 Introduction); distance from Lambda CDM with H0=69.9, Omega_M=0.29, Omega_Lambda=0.71  
  > "yields a luminosity distance D$_L$=85.7 Mpc at $z \simeq0.0196$, with 1” corresponding to 0.4 kpc." (1 Introduction)

## Data provenance

- ALMA projects: 2011.0.00182.S
- bands: Band 9  
  > "NGC 34 nuclear region was observed with ALMA in Band 9 during the Early Science Cycle 0" (2.3 ALMA data)
- frequencies and spectral setup: four SPWs of ≈2 GHz centred at 679.8, 678.0, 676.3, 674.3 GHz; TDM, 6.8 km/s resolution  
  > "with four spectral windows (SPWs) of $\approx2 \,$ GHz, centered at the sky frequencies of 679.8, 678.0, 676.3 and 674.3 GHz, respectively." (2.3 ALMA data)
- continuum bandwidth: _not stated_
- arrays: 12 m antennas; five EBs with 16 antennas, one EB with 27 antennas  
  > "five Execution Blocks (EBs) with 16 antennas, set up in an extended configuration, and in one EB with 27 antennas" (2.3 ALMA data)
- configurations: _not stated_
- baselines: 21 m to 402 m  
  > "the minimum baseline is 21 m, the maximum baseline is 402 m" (2.3 ALMA data)
- angular resolution: ≈0.2 arcsec (~100 pc)  
  > "the spatial resolution of the observation is $\theta \simeq 0.2$, corresponding to $\sim100$ pc." (2.3 ALMA data)
- max recoverable scale: ≈4 arcsec (~2 kpc)  
  > "the largest angular scale (LAS) recovered by ALMA is $\approx 4$, corresponding to $\sim2$ kpc" (2.3 ALMA data)
- sensitivity: _not stated_
- time on source: about 2.25 hr  
  > "The on-source integration time is about 2.25 hr." (2.3 ALMA data)
- observing dates: May and August 2012  
  > "during the Early Science Cycle 0 in May and August 2012" (2.3 ALMA data)
- pi or archival as stated: _not stated_
- Line: CO 6-5 (691.473 GHz)
- Other facility **XMM-Newton**: X-ray spectra  
  > "NGC 34 was observed by XMM-*Newton* on Dec. 22$^{nd}$, 2002." (2.2 X-ray data)
- Other facility **NuSTAR**: hard X-ray spectra  
  > "NuSTAR observed NGC 34 on July 31$^{st}$, 2015, for an exposure time of 21.2 ks." (2.2 X-ray data)
- Other facility **Herschel/SPIRE**: CO J=4-3 to 13-12 fluxes  
  > "the transitions from $J_{\mathrm{up}}=4$ to $J_{\mathrm{up}}=13$ (green circles) are Herschel/SPIRE observations" (2.4 CO data)
- External data: CO(1-0) flux from CARMA  
  > "The CO(1–0) transition (blue square) was observed by CARMA" (2.4 CO data) [from (cite: fernandez)]
- External data: CO(2-1) flux from SMA  
  > "The CO(2–1) transition (yellow triangle) was observed by the Submillimeter Array (SMA)" (2.4 CO data) [from (cite: ueda14)]
- External data: CO(3-2) from SMT, corrected  
  > "The observation of the CO(3–2) transition (purple pentagon) was conducted with the Submillimeter Telescope (SMT)" (2.4 CO data) [from (cite: kamenetzky16)]
- External data: Herschel/SPIRE CO lines J=4-13  
  > "transitions from $J_{\mathrm{up}}=4$ to $J_{\mathrm{up}}=13$ (green circles) are Herschel/SPIRE observations" (2.4 CO data) [from (cite: rosenberg)]
- External data: NGC 34 SFR ≃24 Msun/yr  
  > "normalised to NGC 34 SFR ($\simeq24\,$M$_{\odot}\,$yr$^{-1}$, (cite: gruppioni))" (3.1 PDR and XDR modelling) [from (cite: gruppioni)]
- Simulation/model as data: CLOUDY c13.03 PDR/XDR grids and Flower & Pineau des Forets C/J-shock models  
  > "we have modelled the effect of the FUV and X-ray radiation on the molecular gas with the version c13.03 of CLOUDY" (3 Interpreting the CO SLED of NGC 34)

## Processing

### Calibration

- pipeline or manual: Re-calibrated from raw archive data with new reduction scripts  
  > "we took the raw data from the archive, we generated new reduction scripts and we calibrated the data using CASA  4.5.2" (2.3 ALMA data)
- casa version: CASA 4.5.2  
  > "we calibrated the data using CASA  4.5.2" (2.3 ALMA data)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Pallas (flux), 3C 454.3 (bandpass), 2348-165 (phase); Butler-JPL-Horizons 2012 model  
  > "The phase, bandpass and flux calibrators observed are 2348-165, 3C 454.3 and the asteroid Pallas, respectively" (2.3 ALMA data)
- flux scale uncertainty: 15% of total flux in Band 9 for Cycle 0  
  > "that is the 15% of the total flux in Band 9 for Cycle 0 Data" (2.3 ALMA data)
- self calibration: Phase solint 600 s, then phase+amplitude 1200 s combining scans  
  > "we found phase solutions averaged on 600 s (i.e., approximately two scans). Then, we iterated again and we found phase and amplitude solutions, averaging 1200 s and combining scans." (2.3 ALMA data)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "selecting a natural weighting scheme of the visibilities" (2.3 ALMA data)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: continuum subtracted (method not given)  
  > "subtracting the continuum, binning into channels" (2.3 ALMA data)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: binned to ≈34 km/s channels  
  > "binning into channels with a width of $\approx 34$ kms$^{-1}$" (2.3 ALMA data)
- final beam: _not stated_
- final rms: ≈6.5 mJy/beam per channel  
  > "channel map of the CO(6–5) transition with a rms of $\approx6.5 \,$mJy/beam" (2.3 ALMA data)

### Inherited from earlier work

- Earlier standard-pipeline analysis of the same ALMA data  
  > "The analysis of the data obtained with a standard pipeline was reported by (cite: xu14)." (2.3 ALMA data) [from (cite: xu14)]
- Fisher F-test method  
  > "taking advantage of the Fisher-test, as presented by (cite: bevington)" (3.3 CO SLED fitting) [from (cite: bevington)]

### Not stated but needed to reproduce (our reading)

- Line-free channels and continuum subtraction method
- Cell size, image size, clean mask and threshold
- Bandpass/phase calibration details beyond solint
- Details of how line luminosities for the CO SLED were derived and uncertainties
- Full CLOUDY input parameters and shock grid steps
- Fixed X-ray model details (Cloudy table AGN normalisation exact)
- Coordinates of NGC 34 and phase centre

## Analysis recipe

1. **Fit X-ray spectra to get AGN luminosity**: Simultaneous fit of XMM pn/MOS and NuSTAR FPMA/B with absorbed power law plus mekal and scattered component  
  > "we adopted a model consisting of an absorbed power-law, accounting for the continuum emission above a few keV, and a thermal plus scattering component below 2 keV." (2.2 X-ray data)
   - software: xspec, mathpha, nupipeline, nuproducts
   - parameter: Gamma fixed to 1.9; errors at 90% confidence  
  > "we fixed the power-law photon indices (of the nuclear and scattered components) to $\Gamma=1.9$" (2.2 X-ray data)
   - fitting: chi2 statistics with binned spectra  
  > "pn (MOS1+2) spectra were binned to 20 (15) counts/bin to apply $\chi^2$ statistics" (2.2 X-ray data)
   - validation: Checked flux variability between XMM and NuSTAR within a factor of two  
  > "we verified that no large flux variability occurs between XMM-*Newton* and NuSTAR data, being well within a factor of two." (2.2 X-ray data)
2. **Recalibrate and image ALMA CO(6-5)**: Re-calibration with CASA, self-calibration, continuum subtraction, natural-weight cleaning, moment 0 flux within 3 sigma  
  > "we took the raw data from the archive, we generated new reduction scripts and we calibrated the data using CASA  4.5.2" (2.3 ALMA data)
   - software: CASA
   - parameter: phase solution 60 s, bandpass over 30 channels, S/N threshold 1.5  
  > "a phase solution over 60 s and a bandpass solution over 30 channels can be obtained." (2.3 ALMA data)
   - fitting: _not stated_
   - validation: ALMA CO(6-5) flux agrees within 1 sigma with Herschel  
  > "By comparing the two different data sets for the CO(6–5) transition, we find a good agreement within 1$\sigma$." (2.4 CO data)
3. **Build PDR, XDR and shock model grids**: CLOUDY PDR (Starburst99 SED) and XDR (table AGN) grids; Flower et al. C/J shock grids  
  > "We run 21 PDR models, varying $n$ in the range ${\rm log}$(n/cm$^{-3})=[2-4.5]$ and the distance of the gas slab from the radiation source in the range $d= [100-500]$ pc." (3.1 PDR and XDR modelling)
   - software: CLOUDY, Starburst99
   - parameter: XDR: 9 models, log n=[3.5-5.5], L(1-100 keV)=4e42 erg/s; shocks v=10-40 km/s, log n=3-6  
  > "We run 9 models, adopting a slightly higher range of densities ${\rm log}$(n/cm$^{-3})=[3.5-5.5]$" (3.1 PDR and XDR modelling)
   - assumption: Salpeter IMF 1-100 Msun, solar metallicity, continuous SF at 24 Msun/yr, gas-to-dust ratio ≈160, 1-D slab, log NH 19-23  
  > "We assume a Milky Way gas-to-dust ratio of $\approx160$ (e.g., (cite: dustgasratio)) for the gas slab." (3.1 PDR and XDR modelling)
   - fitting: _not stated_
   - validation: _not stated_
4. **Fit CO SLED with component combinations**: chi2 fit of PDR1+PDR2, PDR+shock, PDR+XDR; low-density PDR column fixed at log N=21.8, XDR at 23.0  
  > "we fixed the gas column density of the low-density PDR to ${\rm log}$($N_{\rm{H}}$/cm$^{-2})\simeq 21.8$" (3.3 CO SLED fitting)
   - fitting: chi2 minimisation; 1 sigma from Delta chi2=2.3  
  > "considering a $\Delta \chi^2 = 2.3$ (cite: lampton76)" (3.3 CO SLED fitting)
   - validation: F-test of three-component vs PDR+XDR: f=0.66, P=70%  
  > "We find a value of $f = 0.66$ that corresponds to a probability $P(F \leq f) = 70$%" (3.3 CO SLED fitting)

## Software

- **CASA** 4.5.2: ALMA calibration, self-calibration, imaging  
  > "we calibrated the data using CASA  4.5.2" (2.3 ALMA data)
- **CLOUDY** c13.03: PDR and XDR models  
  > "with the version c13.03 of CLOUDY" (3 Interpreting the CO SLED of NGC 34)
- **xspec** : X-ray spectral fitting  
  > "carried out using xspec; (cite: arnaud)" (2.2 X-ray data)
- **Starburst99** : stellar SED for PDR models  
  > "obtained using the stellar population synthesis code Starburst99" (3.1 PDR and XDR modelling)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| ALMA CO(6-5) integrated flux | 707 | 106 | Jy km/s | 2 | we obtain an integrated flux of $(707 \pm 106) \, \mathrm{Jy \, km \, s^{-1}}$ |
| Intrinsic 1-100 keV luminosity | 4.0e42 | not stated | erg/s | 1 | 4.0 $\times10^{42}$ erg s$^{-1}$, respectively |
| NH | 5.2e23 | +1.3/-1.1 e23 | cm^-2 | 1 | $N_{\rm{H}}=5.2^{+1.3}_{-1.1}\times 10^{23}\,$cm$^{-2}$ |
| Reduced chi2 PDR+XDR | 1.6 (chi2/dof 7.8/5) | not stated | dimensionless | 4 | ($\tilde{\chi}^2_{BF} = 1.6$), therefore it is our fiducial model |
| Total molecular gas mass | 3.1e9 | not stated | Msun | 4 | we estimate a total mass M$_{\rm{gas}} \simeq 3.1 \times 10^9$ M$_{\odot}$ |
| alpha_CO | 1.1 | not stated | Msun/(K km/s pc^2) | 4 | we infer that in NGC 34 $\alpha_{\mathrm{CO}}\simeq1.1\,$M$_{\odot}/($K$\,$km$\,$s$^{-1} \,$pc$^2)$ |

## Qualitative findings

- High-J CO is best explained by an XDR; shocks do not significantly improve the fit and require an emitting area ~10x too large  
  > "returns an emitting area (A=$785^2$ pc$^2$) that is 10x larger than the CO(6-5) emitting region" (3.3 CO SLED fitting)

## Claim tuples

- H: Is the AGN significant in heating molecular gas in NGC 34? | E: Fit CO SLED with PDR+PDR, PDR+shock, PDR+XDR models using X-ray-derived AGN luminosity | R: PDR+XDR has lowest reduced chi2 (1.6) vs 3.3 and 2.0 | F: AGN X-rays significantly heat molecular gas | **supported**
- H: Do shocks contribute to high-J CO? | E: Three-component PDR+XDR+shock fit with F-test | R: f=0.66, P=70% | F: Shocks do not significantly improve the fit | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: PDR1+PDR2 rejected for high chi2; PDR+shock rejected for implausibly large emitting area  
  > "The former is discarded because of the high value of the $\tilde{\chi}^2$" (Conclusion)
- How they decided it was enough: _not stated_
- Limitation (authors): ALMA flux is ≈30% lower than Xu et al. due to different calibration/CASA version  
  > "Our integrated flux is $\approx30\%$ lower than the one reported by (cite: xu14)." (2.3 ALMA data)
- Caveat (inferred, ours): Few data points (≈7-8 dof 4-5) so model degeneracies are significant
- Caveat (inferred, ours): Many parameters fixed (column densities)
- Caveat (inferred, ours): Unresolved clouds; single slab per component
- Caveat (inferred, ours): Flux 15% calibration error dominates

## Reproducibility

- Data public (paper): Archival ALMA, XMM, NuSTAR, Herschel data  
  > "we took the raw data from the archive" (2.3 ALMA data)
- Products in archive: _not stated_
- Missing: imaging parameters (cell, size, mask)
- Missing: line-free channels
- Missing: CO SLED fluxes table and uncertainties
- Missing: CLOUDY input files
- Data volume (inferred): ~50-100 GB raw ALMA Cycle 0 Band 9 data (6 EBs) plus small X-ray data
- Score (inferred): 3/5, Data public and key steps described, but imaging and fitting details missing.
- Rediscovery candidate: no, Imaging details and model grid inputs are incomplete.

## Links

- Method: (cite: flower2015) (shock models)
- Method: (cite: cloudy) (CLOUDY code)
- Companion: (cite: xu14) (earlier analysis of same ALMA data)

## Checks

```json
{
 "quotes": 63,
 "quotes_ok": 63,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 77,
  "stated": 52,
  "rate": 0.675
 },
 "evidence_ok": true
}
```
