# A massive dense gas cloud close to the nucleus of the Seyfert galaxy NGC 1068

`2016PASJ...68..103F` | Publications of the Astronomical Society of Japan 2016 | first author: Furuya, Ray S. | arXiv: 1609.02400 | DOI: 10.1093/pasj/psw095

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: nearby_galaxies, agn_and_quasars, star_formation
- Question: What is the nature of the 689 GHz continuum peak close to the nucleus S1 of NGC 1068, and what role does it play in nuclear star formation and gas inflow?  
  > "In order to address the nature of the continuum source and its role in the dynamics of the nuclear region, we analyzed their ALMA data." (1 Introduction)
- Target **NGC 1068**: coordinates continuum peak RA(J2000)=2h42m40.714s; S1 at 2h42m40.70912s  
  > "the distance of 15.9 Mpc (cite: KH13) is adopted throughout this paper" (1 Introduction); z/distance 15.9 Mpc  
  > "the distance of 15.9 Mpc (cite: KH13) is adopted throughout this paper" (1 Introduction); distance from Kormendy & Ho 2013  
  > "the distance of 15.9 Mpc (cite: KH13) is adopted throughout this paper" (1 Introduction)

## Data provenance

- ALMA projects: 2011.0.00083.S
- bands: Band 9 (689 GHz continuum, CO(6-5))  
  > "for the ALMA Band 9 CO (6–5) line image cube data" (2 Data)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: four 1.875 GHz spectral windows concatenated  
  > "obtained from concatenating four 1.875 GHz bandwidth spectral windows by (cite: GB14a)" (2 Data)
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: beam ~0.328" x 0.215"  
  > "$\sqrt{\timeform{0.328"}\times \timeform{0.215"}}/5\sim \timeform{0.05"}$" (3.1 The Nuclear 689 GHz Continuum Peak)
- max recoverable scale: _not stated_
- sensitivity: 1σ = 16.8 mJy/beam per 14 km/s (CO 6-5); 1.67 mJy/beam (continuum)  
  > "1$\sigma$ $=$ 16.8 mJy beam$^{-1}$ in specific intensity per 14 km s$^{-1}$ resolution for the CO (6–5) line, and 1.67 mJy beam$^{-1}$ for the 689 GHz continuum image" (2 Data)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: Archival data originally taken by Garcia-Burillo et al.  
  > "The ALMA data analyzed here were originally taken by Garcia-Burillo et al." (2 Data)
- Line: 12CO J=6-5 (691.473076 GHz)
- External data: S1 nuclear position from 8.4 GHz VLBA/VLA astrometry  
  > "The position of S1 reported in (cite: G04) was obtained through astrometry between the 8.4 GHz continuum image taken by VLBA" (3.1 The Nuclear 689 GHz Continuum Peak) [from (cite: G04)]
- External data: SMBH mass (8.4±0.4)e6 Msun  
  > "$M_\mathrm{SMBH} \simeq (8.4\pm 0.4) \times 10^6$ $M_\odot$(cite: KH13)" (5.2 Origin of the Massive Dense Gas Cloud) [from (cite: KH13)]
- External data: Stellar population ages 300 Myr and 30 Myr  
  > "one is the relatively young stellar population with an age of 300 Myr" (1 Introduction) [from (cite: SB12)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: Used reduced image products from JVO, calibrated by Garcia-Burillo et al.  
  > "We retrieved their image data from the data archive system of the Japanese Virtual Observatory" (2 Data)
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
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
- smoothing: Velocity smoothed by 2 channels with imrebin; 58 channels, 13.97 km/s  
  > "The resultant CO data have 58 channels with a resolution of 13.97 km s$^{-1}$." (2 Data)
- final beam: _not stated_
- final rms: 16.8 mJy/beam (line), 1.67 mJy/beam (continuum)  
  > "1$\sigma$ $=$ 16.8 mJy beam$^{-1}$ in specific intensity per 14 km s$^{-1}$ resolution for the CO (6–5) line, and 1.67 mJy beam$^{-1}$ for the 689 GHz continuum image" (2 Data)

### Inherited from earlier work

- SED/grey-body analysis approach  
  > "Following the spectral energy distribution (SED) analysis in (cite: GB14a)" (4.2 Star Formation and Gas Properties) [from (cite: GB14a)]
- GILDAS analysis scripts  
  > "Using our own scripts running on GILDAS package used in previous works, e.g., (cite: RSF14)" (2 Data) [from (cite: RSF14)]

### Not stated but needed to reproduce (our reading)

- Image pixel size and beam parameters (blank in text)
- Exact aperture/beam geometry and peak-pixel fitting procedure
- Scripts not released
- Flux scale uncertainty
- Details of RADEX inputs beyond those given

## Analysis recipe

1. **Prepare archival cubes**: Set rest frequency, rebin velocity by 2 channels, export to FITS, import into GILDAS, shift origin to S1  
  > "we smoothed the line data along the velocity axis every 2 channels using task `imrebin`" (2 Data)
   - software: CASA, GILDAS
   - fitting: _not stated_
   - validation: _not stated_
2. **Measure continuum peak and moment maps**: Peak intensity and flux in beam; moments over 1020-1240 km/s  
  > "over velocity range of 1020 km s$^{-1}$ $< v_\mathrm{sys}$(LSR)$<1240$ km s$^{-1}$" (3.1 The Nuclear 689 GHz Continuum Peak)
   - software: GILDAS
   - assumption: Position accuracy assumed ~beam/5 ~0.05"  
  > "We therefore arbitrary assume the widely accepted idea that absolute position accuracy of a point source imaged by a connected-type interferometer is typically better than a fraction of its synthesized beam size." (3.1 The Nuclear 689 GHz Continuum Peak)
   - fitting: _not stated_
   - validation: _not stated_
3. **Dust SED gas mass, Lbol, SFR**: Single-temperature grey body fit of 689 GHz flux; Lbol from optically thin dust; SFR from Kennicutt 1998  
  > "approximated by a single temperature grey body emission" (4.2 Star Formation and Gas Properties)
   - parameter: Td 50-70 K, beta=1.7, kappa0=0.005 cm/g at 231 GHz  
  > "Adopting a range for dust temperature ($T_\mathrm{d}$) of 50 –70 K, frequency-index of emissivity of dusts ($\beta$) of 1.7" (4.2 Star Formation and Gas Properties)
   - assumption: Lbol ≈ LFIR  
  > "with another assumption of $L_\mathrm{bol}\approx L_\mathrm{FIR}$" (4.2 Star Formation and Gas Properties)
   - fitting: _not stated_
   - validation: _not stated_
4. **Estimate cloud size via RADEX beam filling and peak positions**: RADEX non-LTE with CO/H2~1e-4, Tgas=Td, FWHM 30 km/s; Tsb/TR gives filling factor and size; compared to peak-pixel scatter  
  > "we obtain $2r\sim 10$ pc by solving $\langle T_\mathrm{SB}\rangle / T_\mathrm{R}\sim \left(r/21\,\mathrm{pc}\right)^2$" (4.2 Star Formation and Gas Properties)
   - software: RADEX
   - fitting: _not stated_
   - validation: Compared with 2Reff~5 pc from peak pixel positions  
  > "has a reasonable consistency with the estimate of 2$R_\mathrm{eff}$$\sim$5 pc which is independently obtained" (4.2 Star Formation and Gas Properties)
5. **Virial mass and stellar mass**: Mvir from Reff and sigma_3D; M* = eps*Mgas with SFE a few-10%  
  > "yield an “effective" virial mass which includes both thermal and non-thermal contributions" (4.2 Star Formation and Gas Properties)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : imhead, imrebin  
  > "We used the task `imhead` in the CASA package to set rest-frequency" (2 Data)
- **GILDAS** : scientific analysis, moments  
  > "imported them into GILDAS package for scientific analysis" (2 Data)
- **RADEX** : non-LTE radiative transfer  
  > "using non-LTE radiative transfer code of `RADEX` (cite: vdTak07)" (4.2 Star Formation and Gas Properties)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| 689 GHz peak intensity | 16.2 | not stated | mJy/beam | 2 | peak intensity of $I_{\tiny 689\mathrm{GHz}} =$ 16.2 mJy beam$^{-1}$ |
| Projected separation from S1 | 14 | not stated | pc | 2 | the angular separation corresponds to the projected separation of $\simeq$ 14 pc |
| Gas mass | (5±3)e5 | ±3e5 | Msun | 3 | $M_\mathrm{gas} = (5\pm 3)\times 10^5$ $M_\odot$ |
| Lbol | (0.4–4)e8 | not stated | Lsun | 3 | $L_\mathrm{bol}$ would range (0.4 – 4)$\times 10^8$ $L_{\odot}$ |
| SFR | ~0.1 | not stated | Msun/yr | 3 | we calculated SFR to be $\sim$ 0.1 $M_\odot$ yr$^{-1}$ |
| Virial mass | ~6e5 | not stated | Msun | 5 | $M_\mathrm{vir}\sim 6\times 10^5$ $M_\odot$ |
| CO(6-5) optical depth | ~15 | not stated | dimensionless | 4 | optical depth of the line of $\tau_\mathrm{\tiny CO6-5}\sim 15$ |
| Gas diameter | ~10 (blue), ~8 (red) | not stated | pc | 4 | Repeating the same analysis for the red, we obtained $2r\sim 8$ pc. |

## Qualitative findings

- Cloud lies between Galactic and extragalactic clouds in SFR-Mgas and Sigma_g-Sigma_SFR diagrams; consistent with turbulence-regulated star formation  
  > "We found that the gas stands a unique position between galactic and extraglactic clouds" (abstract)

## Claim tuples

- H: The 689 GHz peak near S1 is a distinct massive dense gas cloud | E: Analysis of archival Band 9 continuum and CO(6-5) cubes plus grey-body SED and RADEX | R: Mgas ~(2-5)e5 Msun, size ~10 pc, n~1e5 cm-3, SFR~0.1 Msun/yr | F: A proto star cluster forming cloud 14 pc from S1 | **supported**
- H: Gas inflow to the nucleus was driven by a past minor merger | E: Qualitative comparison with literature on decoupled nuclear dynamics | R: Nuclear region decoupled from disk | F: Minor merger proposed as most natural mechanism | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Single static opaque gas with self-absorption rejected because no double-peaked profile with central dip  
  > "we detected the weak emission labeled with green bar" (3.2 Molecular Gas Associated with the 689 GHz Continuum Peak)
- Alternative: Pure rotation rejected due to too high specific angular momentum  
  > "we argue that the gas is not in equilibrium by a pure rotation" (4.1 Dynamical Properties)
- How they decided it was enough: _not stated_
- Limitation (authors): Beam does not resolve the cloud; higher resolution and sensitivity needed  
  > "we need to have higher resolution observations with higher sensitivity to assess physical properties of the gas on more firm ground" (5.1 Nature of the Massive Dense Gas Cloud)
- Caveat (inferred, ours): Unresolved source; size from indirect arguments
- Caveat (inferred, ours): Single-temperature dust and assumed kappa0 give large mass uncertainty
- Caveat (inferred, ours): Position accuracy assumed arbitrarily
- Caveat (inferred, ours): Minor merger claim is speculative

## Reproducibility

- Data public (paper): Retrieved from Japanese Virtual Observatory (JVO)  
  > "We retrieved their image data from the data archive system of the Japanese Virtual Observatory" (2 Data)
- Products in archive: _not stated_
- Missing: Pixel size and beam values
- Missing: Aperture definition details
- Missing: RADEX input details
- Missing: Custom GILDAS scripts
- Data volume (inferred): <1 GB (reduced image cubes)
- Score (inferred): 6/5, Public image products and clear recipe with simple formulae, but some parameters missing and results are order-of-magnitude.
- Rediscovery candidate: yes, Public image products and numeric results derivable from stated assumptions.

## Links

- Method: (cite: vdTak07) (RADEX)
- Companion: (cite: GB14a) (Original observations and SED analysis)
- Companion: (cite: GB16) (Higher-resolution ALMA observations of NGC 1068)
- Related: 2011.0.00083.S

## Checks

```json
{
 "quotes": 47,
 "quotes_ok": 47,
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
  "facts": 73,
  "stated": 34,
  "rate": 0.466
 },
 "evidence_ok": true
}
```
