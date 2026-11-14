# ALMA observations of AGN fuelling. The case of PKS B1718-649

`2018A&A...614A..42M` | Astronomy and Astrophysics 2018 | first author: Maccagni, F. M. | arXiv: 1801.03514 | DOI: 10.1051/0004-6361/201732269

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: agn_and_quasars, nearby_galaxies
- Question: Is cold molecular gas falling onto the SMBH of the young radio AGN PKS B1718-649, and does it fuel the radio source (e.g. via chaotic cold accretion)?  
  > "If this was the case, higher resolution and sensitivity observations of the molecular gas in the central regions of the galaxy could provide us a detailed view of the interplay between the gas and the nuclear activity" (Introduction)
- Target **PKS B1718-649**: coordinates _not stated_; z/distance z=0.01442; 62.4 Mpc  
  > "a nearby (z=$0.01442$)[^2] young radio AGN" (A baby radio source: PKS B1718–649); "At the distance of PKS B1718–649 (62.4 Mpc): $1\ensuremath{''} = 294$ pc." (footnote 2); distance from redshift with H0=70 km/s/Mpc, Omega_M=0.3, Omega_Lambda=0.7  
  > "a nearby (z=$0.01442$)[^2] young radio AGN" (A baby radio source: PKS B1718–649); "At the distance of PKS B1718–649 (62.4 Mpc): $1\ensuremath{''} = 294$ pc." (footnote 2)

## Data provenance

- ALMA projects: 2015.1.01359.S
- bands: Band 6  
  > "The Band 6 receivers were used for the observations." (Observations)
- frequencies and spectral setup: CO(2-1) at 227.591 GHz; one 1.875 GHz window, 240 channels of 7.81 MHz (~10.3 km/s)  
  > "The spectral window of the observation was $1.875$ GHz, divided in $240$ channels of $7.81$ MHz ($\sim10.3$$\,$km s$^{-1}$)." (Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: C36-6, maximum baseline 16 km  
  > "The ALMA extended antenna configuration ($C36-6$, maximum baseline of $16$ km)" (Observations)
- baselines: _not stated_
- angular resolution: 0.28" x 0.19" (~82 pc)  
  > "The size of the synthesized beam of the final data cube is $0.28\ensuremath{''} \times 0.19\ensuremath{''}$ (PA $= 41^\circ$)" (Observations)
- max recoverable scale: 2 arcsec  
  > "is sensitive to a maximum recoverable scale of $2\ensuremath{''}$" (Observations)
- sensitivity: 0.09 mJy/beam per channel (48 km/s)  
  > "The r.m.s. noise per channel of the data cube is $0.09$ mJy beam$^{-1}$." (Observations)
- time on source: 3.4 hours including calibration  
  > "The duration of the observation, including the time for calibration, was 3.4 hours." (Observations)
- observing dates: September 2016 (Cycle 3)  
  > "observed by ALMA during Cycle 3 in September 2016" (Observations)
- pi or archival as stated: _not stated_
- Line: 12CO J=2-1 (not stated (observed 227.591 GHz))
- Other facility **SINFONI**: warm H2 1-0 S(1) data from earlier paper  
  > "in warm molecular hydrogen (H$_{\,2}$, $2.12 \mu$m) with SINFONI" (A baby radio source: PKS B1718–649)
- Other facility **ATCA**: HI data from earlier paper  
  > "we observed the source in atomic hydrogen (H I) with the Australia Telescope Compact Array (ATCA)" (A baby radio source: PKS B1718–649)
- Other facility **HST WFPC2**: optical image  
  > "observed by the Hubble Space Telescope WFPC2" (A baby radio source: PKS B1718–649)
- External data: SINFONI H2 1-0 S(1) data, rotation curve model and H2 spectra  
  > "In (cite: maccagni2016), we estimated a model of the rotation curve of the inner disk" (Discussion) [from (cite: maccagni2016)]
- External data: HI spectra and expected accretion rate ~1e-2 Msun/yr  
  > "the expected accretion rate is $\dot{M}\sim 10^{-2}$ ${\rm M}_\odot$ yr$^{-1}$(cite: maccagni2014)" (Discussion) [from (cite: maccagni2014)]
- External data: CO-to-H2 abundance ratio 1.6e-4  
  > "we assume a CO-to-H$_{\,2}$ abundance ratio, $A_C= 1.6\times10^{-4}$ (cite: sofia2004)" (Results) [from (cite: sofia2004)]

## Processing

### Calibration

- pipeline or manual: Initial calibration in CASA with ALMA data reduction scripts; self-calibration on continuum point source in MIRIAD  
  > "The initial calibration was done in `CASA` (cite: mcmullin2007) using the ALMA data reduction scripts." (Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: ~10%, allowing for gain calibrator flux uncertainties  
  > "We estimate that the error in the flux is $\sim 10\%$, to allow for uncertainties in the flux of the gain calibrator." (Results)
- self calibration: MIRIAD self-calibration of the continuum point source  
  > "which was used to perform additional self-calibration of the continuum point source." (Observations)

### Imaging

- task: MIRIAD for continuum subtraction and mapping/cleaning  
  > "All further reduction steps (continuum subtraction, mapping/cleaning) were also done in `MIRIAD`." (Observations)
- deconvolver: _not stated_
- weighting robust: Cube: natural weighting, various Briggs weightings explored; continuum: uniform  
  > "we show the data cube obtained using natural weighting and smoothed to a velocity resolution of $48$$\,$km s$^{-1}$" (Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: total intensity maps corrected for the primary beam  
  > "From the total intensity map, corrected for the primary beam of ALMA, we measure the total flux" (Results)
- array combination: _not stated_
- smoothing: velocity smoothed to 48 km/s  
  > "smoothed to a velocity resolution of $48$$\,$km s$^{-1}$" (Observations)
- final beam: 0.28" x 0.19" PA 41 deg; continuum 0.24" x 0.15"  
  > "the restoring beam is $0.24\ensuremath{''} \times 0.15\ensuremath{''}$ (PA $= 37^\circ$)" (Observations)
- final rms: 0.09 mJy/beam per channel; continuum 0.1 mJy/beam  
  > "The r.m.s noise of the continuum image is $0.1$ mJy beam$^{-1}$" (Observations)

### Inherited from earlier work

- SINFONI H2 observations and stellar light/rotation-curve modelling  
  > "studying the light distribution seen in our SINFONI data (cite: maccagni2016)" (Results) [from (cite: maccagni2016)]

### Not stated but needed to reproduce (our reading)

- Briggs robust values explored and the continuum-free channels for subtraction
- MIRIAD self-calibration parameters and CASA version
- Clean masks, thresholds and cell/image size
- How moment maps and PV cuts were made (clipping)
- Cosmology-based D_L value used and exact absorption spectrum extraction aperture
- Inconsistencies: L'CO 7.4e7 vs 7.3e7, FWHM 57.4 vs 54, Delta v 365 vs 345 km/s

## Analysis recipe

1. **Calibrate, self-calibrate and image**: CASA reduction scripts, then MIRIAD self-cal, continuum subtraction and cleaning; cube and continuum image  
  > "All further reduction steps (continuum subtraction, mapping/cleaning) were also done in `MIRIAD`." (Observations)
   - software: CASA, MIRIAD
   - fitting: _not stated_
   - validation: _not stated_
2. **Moment maps, flux and kinematics of CO emission**: Total intensity and velocity maps, PV diagram along disk major axis; systemic velocity from mean of velocity range  
  > "We measure the systemic velocity of the $^{12}$CO (2–1) as the mean point of this range of velocities, $4250\pm20$$\,$km s$^{-1}$." (Results)
   - fitting: _not stated_
   - validation: Compared with HI systemic velocity  
  > "This velocity is comparable to the systemic velocity measured from the kinematics of the H I gas" (Results)
3. **CO absorption column density**: Optical depth from line against 230 GHz continuum; LTE column density equation, partition function, CO/H2 ratio  
  > "we can determine the column density of the carbon monoxide in the level $J=2$ ($N_{\rm CO\, (2)}$) from the integrated optical depth of the absorption line" (Results)
   - assumption: Tex ~16 K, LTE, homogeneous absorber, A_C=1.6e-4  
  > "we assume the $^{12}$CO (2–1) is in thermal equilibrium at $T_\mathrm{ex}\sim16$" (Results)
   - fitting: _not stated_
   - validation: Compared with 3 sigma emission limit N_H2~4.8e21  
  > "This result is compatible with the $3\sigma$ detection limit of the $^{12}$CO (2–1) line emission on the same line of sight" (Results)
4. **CO luminosity and H2 masses**: L'CO from flux (Solomon & Vanden Bout formula), M_H2 = alpha_CO L'CO  
  > "The H$_{\,2}$ mass-to-CO luminosity relation can be expressed as $M_{{\rm H}_2} =$ $\alpha_{\rm CO}$$L'_{\rm CO}$" (Results)
   - assumption: L'CO(2-1)=L'CO(1-0); alpha_CO 0.8 to 4.6  
  > "for simplicity, we assume $L'_{\rm CO (2-1)}=L'_{\rm CO (1-0)}$" (Results)
   - fitting: _not stated_
   - validation: _not stated_
5. **Infall time-scale and accretion rate**: Distance limit from co-spatial red-shifted H2 (75 pc) and infall velocity, with absorber mass range  
  > "the time-scale of accretion is $t_\mathrm{accretion}\sim5\times10^5$ years." (Discussion)
   - assumption: all absorbing gas at 75 pc  
  > "assuming that all the absorbing $^{12}$CO (2–1) gas is at the maximum distance of in-fall, $d_\mathrm{infall}\sim 75$ pc" (Discussion)
   - fitting: _not stated_
   - validation: Compared with expected accretion rate ~1e-2 Msun/yr  
  > "is compatible with the expected accretion rate of PKS B1718–649" (Discussion)

## Software

- **CASA** : initial calibration with ALMA scripts  
  > "The initial calibration was done in `CASA` (cite: mcmullin2007) using the ALMA data reduction scripts." (Observations)
- **MIRIAD** : self-calibration, continuum subtraction, imaging  
  > "All further reduction steps (continuum subtraction, mapping/cleaning) were also done in `MIRIAD`." (Observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Total CO(2-1) flux | 174 | 17.4 | Jy km/s | 2 | $S_{\rm CO} \Delta v = 174\pm17.4$  Jy km s$^{-1}$ |
| Circumnuclear disk CO flux | 29.5 | 2.95 | Jy km/s | 2 | $S_{\rm CO} \Delta v =29.5\pm 2.95$ Jy km s$^{-1}$ |
| CO systemic velocity | 4250 | 20 | km/s | 2 | $4250\pm20$$\,$km s$^{-1}$ |
| Absorption line velocity offset | +365 | 22 | km/s | 3 | $\Delta v = v_\mathrm{peak} - v_\mathrm{sys} = + 365\pm22$$\,$km s$^{-1}$ |
| Absorption FWHM | 57.4 | 20 | km/s | 3 | FWHM$=57.4\pm20$$\,$km s$^{-1}$ |
| N_CO (absorption) | 1.0e17 | not stated | cm^-2 | 3 | obtaining $N_\mathrm{CO} = 1.0\times10^{17}$ cm$^{-2}$ |
| N_H2 (absorption) | 1.6e21 | not stated | cm^-2 | 3 | we find $N_\mathrm{H_2}= 1.6\times10^{21}$ cm$^{-2}$ |
| Total H2 mass | 3.26e8 to 1.88e9 | not stated | Msun | 4 | varies between $3.26\times10^8$ ${\rm M}_\odot$ for ($\alpha_{\rm CO}$$=0.8$ |
| Circumnuclear disk H2 mass | 5.35e7 to 3.08e8 | not stated | Msun | 4 | The mass of the circumnuclear disk ranges between $5.35\times10^7$ ${\rm M}_\odot$ and $3.08\times10^8$ ${\rm M}_\odot$. |
| Infalling absorber mass | 3e2 to 5e5 | not stated | Msun | 3 | the mass of the in-falling molecular gas ranges between $3\times10^2$ ${\rm M}_\odot$ and $5\times10^5$ ${\rm M}_\odot$. |
| Accretion rate | 1.6e-3 to 2.2 | not stated | Msun/yr | 5 | $1.6\times10^{-3}$ ${\rm M}_\odot$ yr$^{-1}$ $\lesssim\dot{M}_{\rm H_2}\lesssim2.2$ ${\rm M}_\odot$ yr$^{-1}$ |
| 230 GHz continuum flux | 303 | not stated | mJy | 1 | ($S_\mathrm{cont}=303$ mJy) |

## Qualitative findings

- CO emission traces a clumpy warped disk, with an edge-on east-west circumnuclear disk of radius 700 pc  
  > "The rotating structure is oriented along the east-west direction (PA $=72^\circ$), it has a radius of $700$ pc." (Results)

## Claim tuples

- H: Cold molecular clouds fall onto the SMBH of the young radio AGN | E: CO(2-1) absorption against the compact 230 GHz continuum compared with red-shifted H2 | R: Absorption at +365 km/s offset, co-spatial with red-shifted H2 within 75 pc | F: Molecular clouds are likely falling onto the SMBH, consistent with chaotic cold accretion | **supported**
- H: The molecular gas is distributed in a warped disk | E: Moment maps of CO emission | R: Kinematic major axis changes from north-south to east-west | F: Warped disk with 700 pc circumnuclear disk | **supported**
- H: Central gas conditions differ from the outer disk | E: Compare H2 column density from H2 1-0 S(1) and CO(2-1) | R: Ratio 110 within 75 pc vs 16 in the disk | F: CO may be photo-dissociated near the AGN | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Young compact radio source chosen because jets have not yet perturbed the ISM  
  > "The ideal candidate would be a very young radio source, where the radio jets extend for at most a few parsecs" (Introduction)
- Alternative: Bar-induced non-circular motions mimicking a warp ruled out: no bar signature in residuals  
  > "The residuals (Fig. [4](#fig:stars)) show that no signature of a bar is found." (Results)
- How they decided it was enough: _not stated_
- Limitation (authors): Only CO(2-1) available; cannot constrain temperature, pressure, heating  
  > "do not allow us to constrain the physical conditions of the circumnuclear disk, such as temperature, pressure and heating mechanism of the gas" (Conclusions)
- Caveat (inferred, ours): Excitation temperature of 16 K assumed; column densities are lower limits
- Caveat (inferred, ours): Infall inferred from velocity sign and line of sight; distance relies on H2 coincidence at low resolution
- Caveat (inferred, ours): Accretion rate range spans three orders of magnitude
- Caveat (inferred, ours): Continuum variable and half of cm extrapolation

## Reproducibility

- Data public (paper): Project ID given; public status not stated  
  > "(ID: 2015.1.01359.S, PI: F. M. Maccagni)" (Observations)
- Products in archive: _not stated_
- Missing: Clean parameters and continuum-free channels
- Missing: MIRIAD self-cal settings
- Missing: Moment/PV extraction details
- Data volume (inferred): ~10-50 GB raw single-EB Band 6 data
- Score (inferred): 3/5, Public ALMA data and simple analysis, but imaging parameters and some numbers are missing or inconsistent.
- Rediscovery candidate: yes, Single project, simple numeric measurements (fluxes, masses, absorption line properties) are redoable, though imaging details are missing.

## Links

- Companion: (cite: maccagni2014) (HI observations of PKS B1718-649)
- Companion: (cite: maccagni2016) (SINFONI warm H2 observations)

## Checks

```json
{
 "quotes": 65,
 "quotes_ok": 65,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 12,
 "numeric_problems": 0,
 "fill": {
  "facts": 73,
  "stated": 45,
  "rate": 0.616
 },
 "evidence_ok": true
}
```
