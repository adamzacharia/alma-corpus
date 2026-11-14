# High Dense Gas Fraction in Intensely Star-forming Dusty Galaxies

`2017ApJ...850..170O` | The Astrophysical Journal 2017 | first author: Oteo, I. | arXiv: 1701.05901 | DOI: 10.3847/1538-4357/aa8ee3

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies
- Question: Do lensed high-z dusty starbursts (SDP.9, SDP.11) have dense gas excitation, line ratios and L_IR-L_dense relations like local (U)LIRGs, and is their dense gas fraction higher?  
  > "Our results suggest that the intense star formation found in some high-redshift dusty, luminous starbursts is associated with more massive dense molecular gas reservoirs and higher dense molecular gas fractions." (abstract)
- Target **SDP.9 (H-ATLAS J090740.0-004200)**: coordinates RA 09:07:40.0, Dec -00:41:59.8  
  > "| $z_{\rm spec}$$^{(b)}$ | $1.575 \pm 0.005$ | $1.786 \pm 0.005$ |" (Table 1); "| DEC | $-$00:41:59.8 | $-$00:03:22.8 |" (Table 1); z/distance z_spec = 1.575 ± 0.005  
  > "| $z_{\rm spec}$$^{(b)}$ | $1.575 \pm 0.005$ | $1.786 \pm 0.005$ |" (Table 1); "| DEC | $-$00:41:59.8 | $-$00:03:22.8 |" (Table 1); distance from Bussmann2013 (values taken from it)  
  > "| $z_{\rm spec}$$^{(b)}$ | $1.575 \pm 0.005$ | $1.786 \pm 0.005$ |" (Table 1); "| DEC | $-$00:41:59.8 | $-$00:03:22.8 |" (Table 1)
- Target **SDP.11 (H-ATLAS J091043.1-000321)**: coordinates RA 09:10:43.1, Dec -00:03:22.8  
  > "| $z_{\rm spec}$$^{(b)}$ | $1.575 \pm 0.005$ | $1.786 \pm 0.005$ |" (Table 1); z/distance z_spec = 1.786 ± 0.005  
  > "| $z_{\rm spec}$$^{(b)}$ | $1.575 \pm 0.005$ | $1.786 \pm 0.005$ |" (Table 1); distance from Bussmann2013 (values taken from it)  
  > "| $z_{\rm spec}$$^{(b)}$ | $1.575 \pm 0.005$ | $1.786 \pm 0.005$ |" (Table 1)

## Data provenance

- ALMA projects: 2012.1.00915.S
- bands: ALMA 3 mm band  
  > "SDP.9 and SDP.11 were observed with ALMA in the 3 mm band in compact configuration" (2 Data sets)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: compact configuration  
  > "observed with ALMA in the 3 mm band in compact configuration" (2 Data sets)
- baselines: _not stated_
- angular resolution: restoring beam 3.7'' x 2.3''  
  > "with a restoring beam of $3.7'' \times 2.3''$" (2 Data sets)
- max recoverable scale: _not stated_
- sensitivity: rms ~0.14 mJy/beam in 100 km/s channels  
  > "The ${\rm r.m.s}$ of the cubes is $\sim 0.14 \, {\rm mJy \, beam^{-1}}$ in $100 \, {\rm km \, s^{-1}}$ wide channels" (2 Data sets)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: PI: R. Lupu  
  > "project 2012.1.00915.S, PI: R. Lupu" (2 Data sets)
- Line: HCN J=3-2 (not stated)
- Line: HCO+ J=3-2 (not stated)
- Line: HNC J=3-2 (not stated)
- Other facility **VLA**: HCN/HCO+/HNC(1-0) in SDP.9 (14B-259); 12CO(1-0) (12A-201); 7 GHz continuum  
  > "the spectral setup was defined to cover the HCN(1–0), HCO$^+$(1–0), and HNC(1–0) transitions in SDP.9 simultaneously" (2 Data sets)
- Other facility **PdBI**: 12CO(3-2) in SDP.9 and SDP.11, used for lens modelling  
  > "The $^{12}$CO(3-2) emission in SDP.9 and SDP.11 was carried out by the PdBI in its most extended configuration" (2 Data sets)
- Other facility **SMA**: 880 um dust continuum for lens modelling  
  > "We have modeled the lensed dust continuum (observed with the SMA at $880 \, {\rm \mu m}$)" (3 Lens modelling)
- Other facility **HST**: near-IR stellar emission  
  > "stellar emission observed with HST at near-IR wavelengths" (2 Data sets)
- External data: Redshifts, coordinates, unlensed L_IR, SFR, T_dust  
  > "All these values have been taken from (cite: Bussmann2013ApJ...779...25B)." (1 Introduction) [from Bussmann2013ApJ...779...25B]
- External data: Stellar magnification from HST model  
  > "along with the amplifications derived for the stellar emission by (cite: Dye2014MNRAS.440.2013D)" (3 Lens modelling) [from Dye2014MNRAS.440.2013D]
- External data: Local and high-z dense gas line luminosities for comparison  
  > "with a sample of local and high-redshift starbursts and QSOs taken from the literature" (4.4) [from Gao2007, Greve2006, Bussmann2008, GraciaCarpio2008, Juneau2009, Danielson2011, GarciaBurillo2012, Riechers2006]
- Simulation/model as data: PDR/XDR models of Meijerink et al. 2007 for HCN/HNC and HCN/CO ratios  
  > "According to the models of (cite: Meijerink2007A&A...461..793M), the high HCN(1–0)/HNC(1–0) ratios found for SDP.9 and SDP.11 could be only explained by PDR dominated regions" (4.6.1)

## Processing

### Calibration

- pipeline or manual: ALMA: standard techniques in CASA; VLA manual calibration  
  > "The data for each galaxy were reduced independently using standard techniques in CASA." (2 Data sets); "The data were manually calibrated by following the standard procedures, including manual flagging and re-calibration." (2 Data sets)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "Imaging was done using natural weighting to improve the signal to noise of the detections." (2 Data sets)
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
- final beam: 3.7'' x 2.3'' (ALMA)  
  > "with a restoring beam of $3.7'' \times 2.3''$" (2 Data sets)
- final rms: ~0.14 mJy/beam in 100 km/s channels  
  > "$\sim 0.14 \, {\rm mJy \, beam^{-1}}$ in $100 \, {\rm km \, s^{-1}}$ wide channels" (2 Data sets)

### Inherited from earlier work

- SMA continuum and HST data calibration/reduction taken from earlier works  
  > "We refer the reader to those works for details on the data calibration and reduction." (2 Data sets) [from Bussmann2013ApJ...779...25B; Negrello2014MNRAS.440.1999N]
- Dense gas mass conversion M_dense = 10 L'_HCN(1-0)  
  > "assuming $M_{\rm dense} [M_\odot] = 10 \, L^{'}_{\rm HCN(1-0)}" (4.5) [from GarciaBurillo2012A&A...539A...8G]
- Velocity gradient to column density conversion  
  > "following (cite: Zhang2014A&A...568A.122Z)" (4.2) [from Zhang2014A&A...568A.122Z]
- Likelihood distribution of LVG grid  
  > "we calculate the likelihood distributions for all parameter combinations following (cite: Ward2003ApJ...587..171W)" (4.2) [from Ward2003ApJ...587..171W]

### Not stated but needed to reproduce (our reading)

- ALMA CASA version and calibrators
- Line-free channels and moment-map velocity ranges
- Image size and cell size
- uvmcmcfit priors and run settings
- Myradex grid sampling and priors
- Uncertainty derivation for line fluxes
- Conversion of L' used for CO(1-0) and HCN luminosities, incl. L_IR demagnification details

## Analysis recipe

1. **Image ALMA and VLA cubes**: Calibrate and image with natural weighting  
  > "Imaging was done using natural weighting to improve the signal to noise of the detections." (2 Data sets)
   - software: CASA
   - assumption: VLA gain solutions combined over all 24 spws, assuming spw responses do not vary with frequency  
  > "By doing this we assume that the responses of different spws do not vary with frequency." (2 Data sets)
   - fitting: _not stated_
   - validation: _not stated_
2. **Lens modelling for magnification**: uv-plane modelling of SMA 880um and PdBI CO(3-2) with elliptical Gaussian source and SIE lens  
  > "`uvmcmcfit` assumes a pre-defined shape for the background source (elliptical gaussian profile) and that the lens galaxy can be described by singular isothermal ellipsoid (SIE) profiles." (3 Lens modelling)
   - software: uvmcmcfit
   - assumption: Dense gas and low-J CO magnification equal to dust and CO(3-2) values  
  > "we need to assume that their amplification factors are similar to the derived from the $^{12}$CO(3–2) line and dust continuum emission, respectively." (3 Lens modelling)
   - fitting: MCMC; uncertainties from FWHM of posterior  
  > "uncertainties are derived from the FWHM of the posterior probability distribution function" (3 Lens modelling)
   - validation: Dust results compared with earlier gravlens-based model  
  > "for consistency, we have also modeled the SMA emission in our two sources with the last version of `uvmcmcfit`" (3 Lens modelling)
3. **Measure line fluxes**: Velocity-integrated fluxes from zero-moment maps; 3 sigma upper limits  
  > "All velocity-integrated line fluxes have been calculated from the zero-moment maps." (4.3)
   - assumption: HNC(3-2) upper limit in SDP.11 assumes same width as CO and no velocity offset  
  > "we have assumed that its width is the same as the detected CO line and there is no velocity offset" (4.3)
   - fitting: _not stated_
   - validation: _not stated_
4. **Non-LTE modelling of CO SLED and CO+HCN SLEDs**: Grid of Myradex LVG models, likelihood marginalised over parameters  
  > "We marginalize the parameters by integrating the likelihood distribution over all other parameters." (4.2)
   - software: Myradex
   - parameter: n_H2 = 1e2-1e8 cm^-3; Tkin = 10^0.5-10^3 K; dv/dr = 1-1e3 km/s/pc  
  > "number density of molecular hydrogen $n_{\rm H_2} = 10^2$ – $10^8$ cm$^{-3}$, kinetic temperature $T_{\rm kin} = 10^{0.5} - 10^3 \, {\rm K}$" (4.2)
   - assumption: CO abundance 1e-4, T_CMB=7.004 K, HCN abundance 2e-8, single component  
  > "We adopt a CO abundance relative to H$_2$ of $10^{-4}$." (4.2); "We keep the HCN abundance (relative to ${\rm H_2}$) to be 2$\times 10^{-8}$" (4.3)
   - fitting: Likelihood grid, marginalisation  
  > "we calculate the likelihood distributions for all parameter combinations following (cite: Ward2003ApJ...587..171W)" (4.2)
   - validation: Consistency of Tkin and column density between CO-only and CO+HCN fits  
  > "We see that the $T_{\rm kin}$ and column density are consistent with the CO-based results." (4.3)
5. **Dense gas mass, depletion time and line ratios**: Demagnified L_IR and line luminosities compared to literature; M_dense from L'_HCN(1-0)  
  > "$M_{\rm dense} \sim 8.4 \times 10^{10} \, M_\odot$" (4.7)
   - assumption: M_dense = 10 L'_HCN(1-0)  
  > "Assuming the relation between the dense molecular gas mass and the HCN(1–0) luminosity $M_{\rm dense} \sim 10 \times L'_{\rm HCN(1-0)}" (4.7)
   - fitting: _not stated_
   - validation: Compared with local galaxies and PDR/XDR models  
  > "According to the models of (cite: Meijerink2007A&A...461..793M), the high HCN(1–0)/HNC(1–0) ratios found for SDP.9 and SDP.11 could be only explained by PDR dominated regions" (Results and discussion, The HCN/HNC ratio)

## Software

- **CASA** : ALMA data reduction and imaging  
  > "The data for each galaxy were reduced independently using standard techniques in CASA." (2 Data sets)
- **AIPS** : calibration of VLA 7 GHz and CO(1-0) data  
  > "Both datasets were calibrated in AIPS following the standard prescriptions" (2 Data sets)
- **GILDAS** : PdBI calibration  
  > "The data were calibrated by using the standard techniques with GILDAS." (2 Data sets)
- **uvmcmcfit** : uv-plane lens modelling  
  > "by using `uvmcmcfit` (cite: Bussmann2015arXiv150405256B)" (3 Lens modelling)
- **GALFIT** : subtract foreground lens in HST image  
  > "the foreground lensing source has been subtracted using `GALFIT`" (4.1)
- **Myradex** : non-LTE LVG modelling  
  > "we use the non-LTE radiative transfer code Myradex" (4.2)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| HCN(3-2) flux SDP.9 | 0.66 | 0.11 | Jy km/s | 3 | / HCN(3–2) \[${\rm Jy} \, {\rm km} \, {\rm s}^{-1}$\] / $0.66 \pm 0.11$ / $0.54 \pm 0.08$ / |
| HCN(3-2) flux SDP.11 | 0.54 | 0.08 | Jy km/s | 3 | / HCN(3–2) \[${\rm Jy} \, {\rm km} \, {\rm s}^{-1}$\] / $0.66 \pm 0.11$ / $0.54 \pm 0.08$ / |
| HCN(1-0) flux SDP.9 | 0.17 | 0.06 | Jy km/s | 3 | / HCN(1–0) \[${\rm Jy} \, {\rm km} \, {\rm s}^{-1}$\] / $0.17 \pm 0.06$ / – / |
| CO SLED best-fit n(H2) | 3.2e5 | not stated | cm^-3 | 4 | $n(\rm H_2) = 3.2 \times 10^{5} \, {\rm cm^{-3}}$ |
| CO SLED M_H2 SDP.9 | 1.3e11 | not stated | Msun | 4 | $M_{\rm H_2} = 1.3 \times 10^{11} \, M_\odot$ |
| M_dense SDP.9 | 8.4e10 | not stated | Msun | 5 | we obtain $M_{\rm dense} \sim 8.4 \times 10^{10} \, M_\odot$ |
| L'HCN(1-0)/L'CO(1-0) SDP.9 | ~0.37 | not stated | dimensionless | 5 | The $L'_{\rm HCN(1-0)} / L'_{\rm CO(1-0)} \sim 0.37$ found for SDP.9 |
| Dense gas depletion time SDP.9 | ~40 | not stated | Myr | 5 | implying a dense gas depletion time of $\tau_{\rm dep} \sim 40 \, {\rm Myr}$ |

## Qualitative findings

- HCN(1-0)/HNC(1-0) in SDP.9 suggests PDR-dominated gas, like local (U)LIRGs  
  > "the high HCN(1–0)/HNC(1–0) ratios found for SDP.9 and SDP.11 could be only explained by PDR dominated regions" (4.6.1)

## Claim tuples

- H: High-z lensed starbursts follow the local L_IR-L_dense relation | E: Compare demagnified L_IR and dense line luminosities with literature | R: Points fall on a single relation with local galaxies; local scatter ±0.5 dex | F: No evidence of enhanced SFR per dense gas luminosity; higher SFR from more dense gas | **supported**
- H: SDP.9 has a higher dense gas fraction | E: HCN/CO ratio and M_dense vs M_H2 | R: J=1-0 HCN/CO higher than most local sources; M_dense 8.4e10 vs M_H2 1.3e11 | F: Large fraction of gas is dense | **partially**
- H: Excitation of SDP.9 is like local IR-bright galaxies | E: CO, HCN, HCO+ SLEDs | R: Compatible with local sources | F: Similar excitation conditions | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Natural weighting to improve S/N of detections  
  > "Imaging was done using natural weighting to improve the signal to noise of the detections." (2 Data sets)
- How they decided it was enough: _not stated_
- Limitation (authors): Differential magnification is a main uncertainty  
  > "The possible differential magnification between different transitions represents one of the main sources of uncertainty in the analysis presented in this work." (3 Lens modelling)
- Limitation (authors): Scatter and lack of homogeneous high-z samples prevent redshift trends  
  > "prevents us from distinguishing differential trends with redshift" (abstract)
- Caveat (inferred, ours): alpha_HCN assumption uncertain in extreme starbursts
- Caveat (inferred, ours): Single-component LVG with shared region for CO and HCN is simplistic
- Caveat (inferred, ours): Possible AGN or IR pumping could boost HCN
- Caveat (inferred, ours): Low S/N detections in several lines

## Reproducibility

- Data public (paper): ALMA project cited with PI; archive data  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2012.1.00915.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: CASA version and imaging parameters
- Missing: Line integration windows
- Missing: uvmcmcfit configuration
- Missing: LVG priors and likelihood details
- Data volume (inferred): ~10-50 GB
- Score (inferred): 3/5, ALMA data public with project code, but few processing parameters; modelling details partly inherited.
- Rediscovery candidate: no, Recipe incomplete for imaging and flux extraction; lens model needs non-ALMA data.

## Links

- Method: Bussmann2015arXiv150405256B (uvmcmcfit lens modelling code)
- Method: Zhang2014A&A...568A.122Z (velocity gradient to column density conversion)
- Method: Ward2003ApJ...587..171W (likelihood method for LVG grids)
- Companion: Bussmann2013ApJ...779...25B (source properties and SMA modelling)
- Companion: Lupu2012ApJ...757..135L (earlier CO SLED of SDP.9)
- Related: H-ATLAS

## Checks

```json
{
 "quotes": 76,
 "quotes_ok": 76,
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
  "facts": 88,
  "stated": 55,
  "rate": 0.625
 },
 "evidence_ok": true
}
```
