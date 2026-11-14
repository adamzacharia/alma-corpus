# Star Formation and the Interstellar Medium in z &gt; 6 UV-luminous Lyman-break Galaxies

`2015ApJ...807..180W` | The Astrophysical Journal 2015 | first author: Willott, Chris J. | arXiv: 1504.05875 | DOI: 10.1088/0004-637X/807/2/180

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies
- Question: What are the [C II] and FIR dust properties (SFR, [CII]/FIR ratio, dynamics) of two UV-luminous z>6 LBGs, and what do systemic redshifts from [C II] imply for Lyα velocity shifts at z~6?  
  > "Using the interstellar atomic carbon line to derive the systemic redshifts we investigate the velocity of Ly$\alpha$ emission emerging from high-$z$ galaxies." (abstract)
- Target **CLM 1**: coordinates _not stated_; z/distance z=6.1657 ± 0.0003 ([C II])  
  > "The galaxy which we name here as CLM 1 was discovered by (cite: Cuby:2003) at a redshift of $z=6.17$." (1 Introduction); distance from [C II] Gaussian peak frequency (this paper)  
  > "The galaxy which we name here as CLM 1 was discovered by (cite: Cuby:2003) at a redshift of $z=6.17$." (1 Introduction)
- Target **WMH 5**: coordinates _not stated_; z/distance z=6.0695 ± 0.0003 (component A), 6.0639 ± 0.0003 (component B)  
  > "The other galaxy, WMH 5 at $z=6.07$, was discovered in (cite: Willott:2013a)." (1 Introduction); distance from [C II] line fits (Table 1)  
  > "The other galaxy, WMH 5 at $z=6.07$, was discovered in (cite: Willott:2013a)." (1 Introduction)

## Data provenance

- ALMA projects: 2013.1.00815.S
- bands: Band 6, 4 sub-bands between 249 and 272 GHz  
  > "A total bandwidth of 7.2 GHz was employed in Band 6 using 4 dual-polarization sub-bands between 249 and 272 GHz." (2.1 ALMA)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: max baseline 650 m; 29-32 antennas  
  > "Observations were made during ALMA cycle 2, in June 2014, with between 29 and 32 antennas, and a maximum baseline of 650m." (2.1 ALMA)
- angular resolution: beam FWHM = 0.50"  
  > "For both sources, the Gaussian restoring beam was close to circular, with a FWHM = 0.50"." (2.1 ALMA)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: 95 minutes per galaxy  
  > "A total of 95 minutes on-source integration time was obtained for each galaxy." (2.1 ALMA)
- observing dates: June 2014 (Cycle 2)  
  > "Observations were made during ALMA cycle 2, in June 2014" (2.1 ALMA)
- pi or archival as stated: _not stated_
- Line: [C II] 2P3/2-2P1/2 (1900.5369 GHz)
- Other facility **VISTA VIDEO**: NIR Z,Y,J,H,Ks images (DR3)  
  > "Images from Data Release 3 in bands $Z, Y, J, H$ and $Ks$ were obtained" (2.2 Near- and Mid-Infrared)
- Other facility **Spitzer IRAC (SERVS)**: 3.6 and 4.5 micron photometry  
  > "Both $z>6$ galaxies are clearly detected at both 3.6 and 4.5$\mu$m" (2.2 Near- and Mid-Infrared)
- Other facility **VLT FORS2 / Gemini GMOS**: Lyα spectra from discovery papers  
  > "The spectrum of CLM 1 was obtained using FORS2 at the ESO VLT with a spectral resolution of $R=1400$" (2.3 Lyman-$\alpha$ spectroscopy)
- External data: Lyα spectra of CLM 1 and WMH 5  
  > "Optical spectroscopy, including the detection of asymmetric Ly$\alpha$ emission lines and continuum breaks, of both galaxies were presented in their discovery papers" (2.3 Lyman-$\alpha$ spectroscopy) [from (cite: Cuby:2003; Willott:2013a)]
- External data: Lyα velocity shifts of A383-5.2 and GN-108036  
  > "The first measurement of Ly$\alpha$ velocity shifts at redshifts relevant to the reionization epoch have recently been made by (cite: Stark:2014a)." (5 Lyα velocity shifts) [from (cite: Stark:2014a)]
- External data: Lyα shifts at 2<z<3.1 comparison sample  
  > "we show for comparison a sample selected at lower redshift ($2<z<3.1$) as LAEs and LBGs (cite: Erb:2014)" (5 Lyα velocity shifts) [from (cite: Erb:2014)]

## Processing

### Calibration

- pipeline or manual: Standard ALMA staff processing, then additional flagging by authors  
  > "The initial data editing and calibration were performed as part of standard data processing by the ALMA staff." (2.1 ALMA)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: 10% added in quadrature  
  > "Flux uncertainties have 10% added in quadrature for absolute flux calibration uncertainty." (2.1 ALMA)
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: Briggs, Robust = 1  
  > "The data were re-imaged using the CASA Briggs weighting of the visibility data with Robust = 1 to create continuum and channel images." (2.1 ALMA)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: image-plane, using off-line channels in line cube  
  > "The continuum was subtracted in the image-plane, using the off-line channels in the line cube." (2.1 ALMA)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: cubes at 15.625 MHz (17.5 km/s), smoothed spectrally as required  
  > "Spectral cubes at 15.625 MHz resolution ($17.5 \,{\rm km\,s}^{-1}$) were synthesized, and smoothed spectrally for subsequent analysis, as required." (2.1 ALMA)
- final beam: 0.52" x 0.44" PA=55 (CLM 1)  
  > "compared with a beam size of $0.52\ensuremath{''} \times 0.44\ensuremath{''}$ at PA = 55" (3.1 CLM 1)
- final rms: _not stated_

### Inherited from earlier work

- Dynamical mass procedure  
  > "Following the procedure of (cite: Wang:2013) we derive $M_{\rm dyn}< 6.9\times 10^9 / \sin^2i \,M_\odot$" (3.1 CLM 1) [from (cite: Wang:2013)]
- SFR-[CII] relation  
  > "For the \[C ii\] luminosity we use the relation SFR $(M_\odot\,{\rm yr}^{-1}) = 1.0\times10^{-7}L_{\rm [CII]} \," (3.1 CLM 1) [from (cite: Sargsyan:2014)]
- SFR-FIR relation for Chabrier IMF  
  > "we use the relation SFR $(M_\odot\,{\rm yr}^{-1})=1.5\times10^{-10}L_{\rm FIR}\, (L_\odot)$ appropriate for a Chabrier IMF (cite: Carilli:2013)" (3.1 CLM 1) [from (cite: Carilli:2013)]

### Not stated but needed to reproduce (our reading)

- CASA version
- flux, bandpass and phase calibrators
- line-free channels and channel ranges used for continuum subtraction
- image size and cell size, clean threshold/masks
- primary beam correction details
- code for custom Gaussian fitting
- CIGALE parameter grids and fitting details
- dynamical mass formula and size/inclination assumptions
- how the 42.5-122.5 micron greybody integration was done

## Analysis recipe

1. **Image and extract [C II] line and continuum**: Re-image calibrated data with Briggs weighting, make cubes, subtract continuum in image plane, Gaussian fit spectra and maps  
  > "Spectral and spatial Gaussian fitting was performed using the CASA viewer, CASA fitting tools and custom software." (2.1 ALMA)
   - software: CASA
   - parameter: robust = 1; 15.625 MHz channels  
  > "Spectral cubes at 15.625 MHz resolution ($17.5 \,{\rm km\,s}^{-1}$) were synthesized" (2.1 ALMA)
   - fitting: single Gaussian plus flat continuum for CLM 1; two Gaussians for WMH 5  
  > "The \[C ii\] spectrum is well fit by a single Gaussian plus a very low level, flat continuum." (3.1 CLM 1)
   - validation: _not stated_
2. **Derive FIR luminosity and SFRs**: Greybody from 1.2 mm continuum; SFR from L_FIR and L_[CII] calibrations  
  > "We calculate the far-IR luminosity $L_{\rm FIR}$ (integrated over rest-frame 42.5 to 122.5 $\mu$m) from the observed 1.2 mm continuum assuming a greybody spectrum" (3.1 CLM 1)
   - assumption: Td=30 K, beta=1.6; no CMB correction  
  > "assuming a greybody spectrum with dust temperature, $T_{\rm d} =30$ K and emissivity index, $\beta=1.6$." (3.1 CLM 1)
   - fitting: _not stated_
   - validation: Compared three SFR indicators; Td=45 K alternative  
  > "a higher dust temperature of $T_{\rm d} =45$ K would increase the $L_{\rm FIR}$ value by a factor of about three" (3.1 CLM 1)
3. **SED fitting and photometry**: CIGALE fit to UV-optical-IR plus ALMA continuum filter; NIR/IRAC photometry via GALFIT and PyGFIT  
  > "We use the Python implementation of the CIGALE package (cite: Roehlly:2012) to fit the SED." (3.1 CLM 1)
   - software: CIGALE, GALFIT, PyGFIT
   - assumption: Bruzual & Charlot SSP, constant SFR, Chabrier IMF, Z=0.008, Calzetti attenuation, Dale 2014 IR templates  
  > "Stellar light is modeled with a single (cite: Bruzual:2003) stellar population with constant star formation rate, Chabrier initial mass function and metallicity = 0.008." (3.1 CLM 1)
   - fitting: highest likelihood parameters  
  > "The highest likelihood parameters are a stellar mass of $1.3 \times
10^{10} \,M_\odot$" (3.1 CLM 1)
   - validation: residuals inspected  
  > "With almost as many free parameters as data points, a good fit has been found." (3.1 CLM 1)
4. **Lyα velocity shifts from systemic [C II]**: Convert spectra to LSR, compare Lyα centroid to [C II] redshift, compare with literature vs equivalent width  
  > "For CLM 1 the measured offset is $+430 \pm 69$ km s$^{-1}$" (5 Lyα velocity shifts)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : imaging, viewer and fitting tools  
  > "Spectral and spatial Gaussian fitting was performed using the CASA viewer, CASA fitting tools and custom software." (2.1 ALMA)
- **CIGALE** : SED fitting  
  > "We use the Python implementation of the CIGALE package (cite: Roehlly:2012) to fit the SED." (3.1 CLM 1)
- **GALFIT** : model fits to NIR images  
  > "Models were fit to the NIR images using GALFIT (cite: Peng:2010)" (2.2 Near- and Mid-Infrared)
- **PyGFIT** : IRAC photometry  
  > "subsequent fitting of the IRAC data was done with PyGFIT (cite: Mancone:2013)" (2.2 Near- and Mid-Infrared)
- **FAST** : SED fit of foreground elliptical for lensing estimate  
  > "using the FAST code (cite: Kriek:2009)" (3.1 CLM 1)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| z_[CII] CLM 1 | 6.1657 | 0.0003 | dimensionless | 1 | we determine the systemic redshift of the galaxy as $z=6.1657 \pm 0.0003$ |
| [CII] FWHM CLM 1 | 162 | 23 | km/s | 1 | The Gaussian FWHM is $162 \pm 23$ km s$^{-1}$. |
| L_[CII] CLM 1 | 2.40e8 | 0.32e8 | Lsun | 1 | $(2.40 \pm 0.32) \times 10^8$ |
| L_[CII] WMH 5 | 6.60e8 | 0.72e8 | Lsun | 1 | $(6.60  \pm 0.72) \times 10^8$ |
| f_1.2mm CLM 1 | 44 | 26 | μJy | 1 | $44 \pm 26$ |
| f_1.2mm WMH 5 | 218 | 41 | μJy | 1 | $218 \pm 41$ |
| L_FIR WMH 5 | 1.25e11 | 0.24e11 | Lsun | 2 | $(1.25 \pm 0.24) \times 10^{11}$ |
| L_[CII]/L_FIR CLM 1 | 9.5e-3 | 5.7e-3 | dimensionless | 2 | $(9.5 \pm 5.7) \times 10^{-3}$ |
| L_[CII]/L_FIR WMH 5 | 5.3e-3 | 1.2e-3 | dimensionless | 2 | $(5.3 \pm 1.2) \times 10^{-3}$ |
| Lyα velocity shift CLM 1 | +430 | 69 | km/s | 4 | For CLM 1 the measured offset is $+430 \pm 69$ km s$^{-1}$ |
| Lyα shift WMH 5 (A / B) | +265 / +504 | 52 | km/s | 4 | then the offset is $+265 \pm 52$ km s$^{-1}$ |
| SED stellar mass CLM 1 | 1.3e10 | not stated | Msun | 3 | a stellar mass of $1.3 \times
10^{10} \,M_\odot$ |
| lensing magnification of CLM 1 | 1.13 | not stated | dimensionless | 0 | this lensing configuration provides a magnification factor of only 1.13 |

## Qualitative findings

- WMH 5 appears to be an ongoing merger; A dominates FIR/[CII], B coincides with UV  
  > "From this analysis the system appears to be an on-going merger of two galaxies." (3.2 WMH 5)

## Claim tuples

- H: Do UV-luminous z~6 LBGs have low FIR luminosity and high [CII]/FIR? | E: ALMA Band 6 [CII] and 1.2 mm continuum of two LBGs | R: [CII]/FIR ~5e-3 to 1e-2, FIR low relative to SFR | F: [CII] should be readily detectable in the reionization epoch | **supported**
- H: Do Lyα velocity shifts decrease at high z? | E: Lyα offsets relative to [CII] systemic redshift compared with lower-z sample | R: +430 km/s for CLM 1; +265 or +504 km/s for WMH 5 | F: No evidence for decreasing shifts | **supported**

## Reasoning

- Why this data: Targets chosen because UV luminosity, stellar mass and redshift comparable to Himiko  
  > "CLM 1 and WMH 5 were selected for study because their UV luminosity, stellar mass and redshift are comparable to the galaxy *Himiko*" (6 Conclusions)
- Why this method: _not stated_
- Alternative: No CMB correction applied since the effects are comparable and opposite  
  > "the two effects are of comparable size and opposite sign for likely dust temperatures at this redshift, so we make no correction." (3.1 CLM 1)
- How they decided it was enough: _not stated_
- Limitation (authors): Single continuum point; dust temperature unconstrained  
  > "Since we only have one continuum point and no constraints on dust temperature, we cannot make an accurate correction" (3.1 CLM 1)
- Caveat (inferred, ours): CLM 1 continuum is only a 2 sigma marginal detection
- Caveat (inferred, ours): L_FIR depends strongly on assumed Td
- Caveat (inferred, ours): Systemic redshift of WMH 5 ambiguous; only 4 high-z Lyα comparison points
- Caveat (inferred, ours): Dynamical masses depend on unknown inclination

## Reproducibility

- Data public (paper): ALMA project cited; public status not stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2013.1.00815.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: CASA version and calibrator details
- Missing: CIGALE configuration
- Missing: custom fitting software
- Missing: dynamical mass formula details
- Data volume (inferred): ~10-50 GB raw
- Score (inferred): 5/5, Simple data and clear table of results, but imaging details, versions and SED fit configuration missing.
- Rediscovery candidate: yes, Cycle 2 data likely public, key results (line fluxes, redshifts, continuum) are numeric and recipe mostly sufficient.

## Links

- Method: (cite: Wang:2013) (dynamical mass procedure)
- Method: (cite: Roehlly:2012) (CIGALE SED fitting)
- Companion: (cite: Cuby:2003) (CLM 1 discovery and Lyα spectrum)
- Companion: (cite: Willott:2013a) (WMH 5 discovery and Lyα spectrum)
- Related: VIDEO
- Related: SERVS
- Related: KINGFISH

## Checks

```json
{
 "quotes": 64,
 "quotes_ok": 64,
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
  "facts": 78,
  "stated": 46,
  "rate": 0.59
 },
 "evidence_ok": true
}
```
