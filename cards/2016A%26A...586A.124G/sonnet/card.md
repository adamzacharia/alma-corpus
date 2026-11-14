# The mysterious morphology of MRC0943-242 as revealed by ALMA and MUSE

`2016A&A...586A.124G` | Astronomy and Astrophysics 2016 | first author: Gullberg, Bitten | arXiv: 1510.03442 | DOI: 10.1051/0004-6361/201526858

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: agn_and_quasars, high_z_galaxies
- Question: What is the spatially resolved distribution of dust, molecular gas and ionised/neutral gas in the z=2.9 radio galaxy MRC0943-242, and where is the star formation relative to the AGN host?  
  > "This ALMA-MUSE-pilot study reveals an even more complex morphology of MRC0943-242 than previously seen with star-formation taking place far outside the AGN host galaxy." (Introduction)
- Target **MRC0943-242**: coordinates Yggdrasil (AGN): 09:45:32.769 -24:28:49.29  
  > "we conducted a pilot study of MRC0943-242 at $z=2.9$" (Introduction); "The HeII emission line is best fitted by a Lorentzian profile, with a centre corresponding to a redshift of $2.92296\pm0.00001$" (3.2 Ionised gas); "| Yggdrasil | 09:45:32.769 | -24.28.49.29 | $0.8\pm0.2$ |" (Table 4); z/distance z=2.92296±0.00001  
  > "we conducted a pilot study of MRC0943-242 at $z=2.9$" (Introduction); "The HeII emission line is best fitted by a Lorentzian profile, with a centre corresponding to a redshift of $2.92296\pm0.00001$" (3.2 Ionised gas); "| Yggdrasil | 09:45:32.769 | -24.28.49.29 | $0.8\pm0.2$ |" (Table 4); distance from HeII line fitted in the MUSE data  
  > "we conducted a pilot study of MRC0943-242 at $z=2.9$" (Introduction); "The HeII emission line is best fitted by a Lorentzian profile, with a centre corresponding to a redshift of $2.92296\pm0.00001$" (3.2 Ionised gas); "| Yggdrasil | 09:45:32.769 | -24.28.49.29 | $0.8\pm0.2$ |" (Table 4)

## Data provenance

- ALMA projects: 2012.1.00039.S
- bands: Band 6 (235 GHz)  
  > "The Atacama Large Milimeter/submilimeter Array (ALMA) cycle 1 observations in Band 6 were carried out on 2014 April 29 for 3 min on-source time with 36 working antennas." (2.1 ALMA observations)
- frequencies and spectral setup: four 1.875 GHz spectral windows covering 233.6-237.1 and 248.6-252.3 GHz  
  > "The four 1.875 GHz spectral windows were tuned to cover the frequency ranges $233.6-237.1$ GHz and $248.6-252.3$ GHz." (2.1 ALMA observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.7'' x 0.6'' beam, pa=75 deg (natural weighting)  
  > "This results in a $0.7\ensuremath{''}\times0.6\ensuremath{''}$ beam with pa $=75^{\circ}$ and an RMS of 0.1 mJy for the continuum." (2.1 ALMA observations)
- max recoverable scale: _not stated_
- sensitivity: continuum RMS 0.1 mJy; line RMS 1.7 mJy at 10 km/s  
  > "We binned the line data to 10 km/s which has an RMS of 1.7 mJy." (2.1 ALMA observations)
- time on source: 3 min, 36 antennas  
  > "observations in Band 6 were carried out on 2014 April 29 for 3 min on-source time with 36 working antennas." (2.1 ALMA observations)
- observing dates: 2014 April 29  
  > "carried out on 2014 April 29 for 3 min on-source time" (2.1 ALMA observations)
- pi or archival as stated: _not stated_
- Line: CO 8-7 (921.80 GHz)
- Other facility **VLT/MUSE**: Optical IFU cube (Lyα, HeII, CIV etc.), 1 hr, 460-935 nm  
  > "This one hour observation taken under $\sim1\ensuremath{''}$ seeing was split into three 20 min exposures" (2.2 MUSE observations)
- Other facility **Spitzer (IRAC, MIPS, IRS)**: Near/mid-IR photometry for stellar mass and SED  
  > "MRC0943-242 was observed with the Infrared Array Camera (IRAC), the Infrared Spectrograph (IRS) and the Multiband Imaging Photometer (MIPS) on *Spitzer*" (2.3 Previous Supporting Spitzer Observations)
- Other facility **ATCA**: Archival CO(1-0) data  
  > "Searching the archival Australian Telescope Compact Array (ATCA) data for Yggdrasil" (3.1.2 Molecular emission lines)
- Other facility **Herschel**: Far-IR photometry (PACS, SPIRE) for SED  
  > "Yggdrasil has a well-sampled SED with IRAC, MIPS, SPIRE ($250$ $\mu$m, $350$ $\mu$m and $500$ $\mu$m) and PACS" (3.4 Disentangling the SED)
- External data: ATCA CO(1-0) data reduction and characteristics  
  > "(see (cite: emonts11) for more details about the data reduction and data characteristics)" (3.1.2 Molecular emission lines) [from (cite: emonts11)]
- External data: Herschel/PACS/SPIRE and earlier SED photometry  
  > "from previous studies (cite: debreuck10; drouart14)" (3.4 Disentangling the SED) [from (cite: debreuck10; drouart14)]
- External data: Stellar mass of Yggdrasil from Spitzer SED fit, 1.7e11 Msun  
  > "which is converted to a stellar mass of $1.7\cdot10^{11}$ M$_{\odot}$" (3.3 Stellar mass) [from (cite: seymour07; debreuck10)]
- Simulation/model as data: Shock/photoionisation line-ratio diagrams from De Breuck et al. 2000 and Villar-Martin et al. 2007 used for ionisation mechanism  
  > "along with the diagrams of (cite: debreuck00) (their Fig. 13, adapted in Fig [9](#fig:lineratios))" (4.3 Ionisation mechanism)

## Processing

### Calibration

- pipeline or manual: supplied calibration script used in CASA  
  > "We used the Common Astronomy Software Applications (CASA) and the supplied calibration script to calibrate the data" (2.1 ALMA observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: 15% flux calibration error  
  > "The uncertainty includes the 15% flux calibration error." (Table 4)
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: natural weighting (robust parameter of 2)  
  > "we use a natural weighting (robust parameter of 2)" (2.1 ALMA observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: UV-plane first-order polynomial fit to all four spectral windows  
  > "we subtracted the continuum in the UV-plane by fitting a first-order polynomial to all four spectral windows" (2.1 ALMA observations)
- line free channels: _not stated_
- primary beam correction: applied to all maps and spectra  
  > "we applied a primary beam correction on all our maps and spectra." (2.1 ALMA observations)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: 0.1 mJy continuum; 1.7 mJy per 10 km/s channel  
  > "an RMS of 0.1 mJy for the continuum" (2.1 ALMA observations)

### Inherited from earlier work

- Spitzer observations and reductions  
  > "(see (cite: seymour07) for details on the observations and reductions)" (2.3 Previous Supporting Spitzer Observations) [from (cite: seymour07)]
- SED fitting with AGN and starburst components  
  > "Relying on the method of (cite: drouart14) by fitting an SED with AGN and starburst components" (3.4 Disentangling the SED) [from (cite: drouart14)]
- Ionised and neutral gas mass formulae  
  > "Following (cite: debreuck03), we estimate the ionised gas masses of Yggdrasil." (4.2 Distribution of masses) [from (cite: debreuck03)]

### Not stated but needed to reproduce (our reading)

- CASA version and imaging task parameters (cell, image size, masks)
- Aperture/region definitions for continuum flux extraction
- Details of the SED fit (priors, templates, how the extra starburst was set)
- Line-free channels and the Gaussian fitting procedure
- Number of weblog/QA flags or phase calibrator names

## Analysis recipe

1. **Calibrate and image ALMA data**: Supplied calibration script, UV continuum subtraction, natural-weighted imaging, primary beam correction  
  > "we use a natural weighting (robust parameter of 2)" (2.1 ALMA observations)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Search and verify CO(8-7) detections**: Moment-0 maps, Gaussian fits to spectra, chance-probability test with 13 moment maps and 81 peaks  
  > "we create 13 moment-0 maps at different frequencies in the cube by collapsing a velocity ranges in the cube of 180 km/s." (3.1.2 Molecular emission lines)
   - software: CASA
   - fitting: single Gaussian per line  
  > "Fitting a single Gaussian to this narrow velocity profile yields a FWHM of $47\pm13$ km/s" (3.1.2 Molecular emission lines)
   - validation: Combined chance probability of the CO configuration 0.84%  
  > "The combined probability of finding the observed CO(8–7) configuration in Loke and Yggdrasil is therefore only 0.84%." (3.1.2 Molecular emission lines)
3. **Fit MUSE emission and absorption lines**: HeII Lorentzian for systemic redshift; Voigt profile fits to Lyα and CIV troughs; fluxes integrated within 3 sigma  
  > "By fitting a Voigt-profile to the absorption trough, we estimate a column density of the neutral gas for component 2" (3.2 Ionised gas)
   - software: MUSE pipeline, ZAP
   - fitting: Lorentzian and Voigt profiles  
  > "The HeII emission line is best fitted by a Lorentzian profile, with a centre corresponding to a redshift of $2.92296\pm0.00001$ and a FWHM of $862\pm30$ km/s." (Ionised gas)
   - validation: Comparison with Binette+00 and Jarvis+03 values  
  > "For components 1, 3 and 4, we find good agreement with the values in (cite: jarvis03) for the column densities and velocities." (3.2 Ionised gas)
4. **Decompose SED into AGN and starburst spatially**: Fit separate SEDs for Yggdrasil and Freja+Thor+Odin using ALMA and de-blended Spitzer points, Herschel total as constraint  
  > "all solutions where the sum is inconsistent with the *Herschel* photometry are excluded." (3.4 Disentangling the SED)
   - software: DecompIR
   - assumption: Kennicutt98 relation for SFR  
  > "According to the (cite: Kennicutt98) relation, Yggdrasil and Freja, Thor and Odin have SFR of $\sim 200$ and $\sim 1400$ M$_{\odot}$ yr$^{-1}$" (3.4 Disentangling the SED)
   - fitting: _not stated_
   - validation: Sum must be consistent with Herschel photometry  
  > "all solutions where the sum is inconsistent with the *Herschel* photometry are excluded." (Disentangling the SED)
5. **Estimate gas and stellar masses**: Ionised mass from Lyα luminosity and volume; neutral shell mass from HI column; molecular mass from CO(1-0) with alpha_CO=0.8  
  > "choosing a conservative $\alpha_{\text{CO}}=0.8$ M$_{\odot}$ K km s$^{-1}$ pc$^{-2}$ (cite: downes98)" (4.2 Distribution of masses)
   - assumption: filling factor 1e-5; spherical shell for absorber 2  
  > "We assume a filling factor of $10^{-5}$ (cite: mccarthy90)" (4.2 Distribution of masses)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : Calibration, imaging, moment maps, flux extraction  
  > "We used the Common Astronomy Software Applications (CASA) and the supplied calibration script" (2.1 ALMA observations)
- **MUSE pipeline** 1.0: MUSE data reduction  
  > "All data were processed with the version 1.0 of the MUSE pipeline (cite: weilbacher12)" (2.2 MUSE observations)
- **ZAP** : PCA sky residual cleaning  
  > "cleaned for sky subtraction residuals with the Principal Component Analysis (PCA) based algorithm ZAP" (2.2 MUSE observations)
- **DecompIR** : Starburst model in SED  
  > "reproduced by the starburst model from DecompIR (cite: mullaney11)" (3.4 Disentangling the SED)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Yggdrasil 235 GHz flux density | 0.8 | 0.2 | mJy | 1 | / Yggdrasil / 09:45:32.769 / -24.28.49.29 / $0.8\pm0.2$ / |
| Odin 235 GHz flux density | 2.0 | 1.0 | mJy | 1 | / Odin      / 09:45:32.222 / -24.28.55.06 / $2.0\pm1.0$           / |
| Thor 235 GHz flux density | 1.9 | 0.8 | mJy | 1 | / Thor      / 09:45:32.386 / -24.28.54.05 / $1.9\pm0.8$           / |
| CO(8-7) line flux Yggdrasil | 0.33 | 0.07 | Jy km/s | 2 | / CO(8–7)    / 921.8                   / $234.94\pm0.1$               / $0.33\pm0.07$              / $43\pm13$    / |
| CO(8-7) line flux Loke | 0.54 | 0.10 | Jy km/s | 2 | / CO(8–7)    / 921.8                   / $234.96\pm0.1$               / $0.54\pm0.10$              / $57\pm17$    / |
| HeII redshift | 2.92296 | 0.00001 | dimensionless | 3 | a redshift of $2.92296\pm0.00001$ and a FWHM of $862\pm30$ km/s |
| N_HI absorber 2 (Yggdrasil) | 1.3e19 | not stated (lower limit) | cm^-2 | 3 | $N_{\text{H{\scriptsize I}}}$ $=1.3\cdot10^{19}$ cm$^{-2}$ and a Doppler width of 64 km/s |
| Total IR luminosity | 1.7e13 | not stated | Lsun | 4 | ($L_{\rm total}^{\rm IR}=1.7\times10^{13}$ L$_{\ensuremath{\odot}}$) |
| SFR Freja+Thor+Odin | ~1400 | not stated | Msun/yr | 4 | have SFR of $\sim 200$ and $\sim 1400$ M$_{\odot}$ yr$^{-1}$, respectively. |
| Molecular gas mass Loke | 2.3e10 | not stated | Msun | 5 | we estimate a molecular gas mass of $2.3\times10^{10}$ M$_{\odot}$ for Loke. |
| Ionised gas mass Yggdrasil | 5.2e8 | not stated | Msun | 5 | find M$_{\text{ion}}=5.2\times10^{8}$ M$_{\odot}$ |

## Qualitative findings

- Most dust emission (star formation) lies 48-65 kpc SW of the AGN in three components; CO(8-7) found at Loke ~90 kpc away with no continuum or optical counterpart.  
  > "the vast majority of the 235 GHz dust emission originates from three components (Freja, Thor and Odin) aligned along a “string” shifted $48-65$ kpc towards the SW" (3.1.1 Dust continuum emission)

## Claim tuples

- H: Is the star formation in MRC0943-242 associated with the AGN host? | E: ALMA 235 GHz continuum plus SED decomposition | R: Yggdrasil flux 0.8 mJy; Freja/Thor/Odin dominate, ~50% of IR luminosity | F: Most star formation is in companions 48-65 kpc from the AGN | **supported**
- H: Is there molecular gas offset from the AGN? | E: CO(8-7) search in ALMA cube, ATCA CO(1-0) recheck | R: 3.5 sigma CO(8-7) at Loke, 2.8 sigma CO(1-0) | F: Tentative low-excitation molecular reservoir at ~90 kpc | **partially**
- H: Is there extended neutral absorbing gas? | E: Voigt fits to Lyα absorption in MUSE | R: Component 2 black core across Bifrost, N_HI ~1e19 | F: Optically thick unity-covering absorber extends >60 kpc | **supported**

## Reasoning

- Why this data: Pilot study to combine ALMA and MUSE for spatially resolved gas phases of HzRGs  
  > "This combination allows us to trace the spatially-resolved distributions of the ionisation state of the warm ionised medium" (Introduction)
- Why this method: _not stated_
- Alternative: Tapering ALMA data to ATCA beam to find extended CO(8-7) gave no useful result  
  > "tapering the ALMA 235 GHz data and convolving them with a beam comparable to that of ATCA did not produce useful results" (3.1.2 Molecular emission lines)
- How they decided it was enough: _not stated_
- Limitation (authors): Shallow ALMA data lack short baselines; CO detections only 3.5 sigma; N_HI lower limit due to saturation  
  > "We note that because the line is saturated, this estimate is very uncertain and likely a lower limit to the true value." (3.2 Ionised gas)
- Caveat (inferred, ours): CO(8-7) detections at 3.5 sigma are marginal and a posteriori
- Caveat (inferred, ours): Flux uncertainties large (~50%) for components
- Caveat (inferred, ours): SED decomposition relies on few points and an ad hoc extra starburst

## Reproducibility

- Data public (paper): MUSE data in ESO archive; ALMA code given  
  > "All of the MUSE data used in this paper are available through the ESO science archive." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Exact CASA version and clean parameters
- Missing: SED fitting details and template settings
- Missing: Aperture definitions
- Data volume (inferred): ~1-5 GB ALMA (3 min, Band 6) plus MUSE cube of a few GB
- Score (inferred): 3/5, Data public and simple, but SED fitting and imaging details are sparse.
- Rediscovery candidate: yes, Short single-track public ALMA dataset with numeric flux and CO line results that can be redone.

## Links

- Method: (cite: drouart14) (SED fitting method for AGN and starburst)
- Method: (cite: debreuck03) (Gas mass formulae)
- Companion: (cite: emonts11) (ATCA CO(1-0) data of MRC0943-242)
- Related: HERGÉ (Herschel Radio Galaxy Evolution)
- Related: Clusters Around Radio Loud AGN (CARLA)

## Checks

```json
{
 "quotes": 71,
 "quotes_ok": 71,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 11,
 "numeric_problems": 0,
 "fill": {
  "facts": 78,
  "stated": 48,
  "rate": 0.615
 },
 "evidence_ok": true
}
```
