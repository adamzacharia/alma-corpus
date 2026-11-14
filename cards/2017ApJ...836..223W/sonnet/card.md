# An ALMA and MagAO Study of the Substellar Companion GQ Lup B*

`2017ApJ...836..223W` | The Astrophysical Journal 2017 | first author: Wu, Ya-Lin | arXiv: 1701.07541 | DOI: 10.3847/1538-4357/aa5b96

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks, star_formation
- Question: What are the properties of the dust disks around GQ Lup A and its substellar companion GQ Lup B, and what do they imply for the formation and orbit of GQ Lup B?  
  > "No gaps or inner cavity are found in the disk, so there is unlikely a massive inner companion to scatter GQ Lup B outward." (abstract)
- Target **GQ Lup A and B**: coordinates 15h49m12.10s, -35d39m05.12s (J2000)  
  > "15$^{\mathrm{h}}$49$^{\mathrm{m}}$12.10s, $-$35$^\circ$39$'$05.12$''$ (J2000)" (Sources in the ALMA Image); "in the Lupus I cloud ($\sim$150 pc; (cite: C00); (cite: F02))" (GQ Lup A and B); z/distance ~150 pc  
  > "15$^{\mathrm{h}}$49$^{\mathrm{m}}$12.10s, $-$35$^\circ$39$'$05.12$''$ (J2000)" (Sources in the ALMA Image); "in the Lupus I cloud ($\sim$150 pc; (cite: C00); (cite: F02))" (GQ Lup A and B); distance from Crawford 2000; Franco 2002  
  > "15$^{\mathrm{h}}$49$^{\mathrm{m}}$12.10s, $-$35$^\circ$39$'$05.12$''$ (J2000)" (Sources in the ALMA Image); "in the Lupus I cloud ($\sim$150 pc; (cite: C00); (cite: F02))" (GQ Lup A and B)

## Data provenance

- ALMA projects: 2015.1.00773.S
- bands: Band 6 (1.3 mm)  
  > "with the Band 6 receiver and 41 12-m antennas reaching a maximum baseline of 14969.3 meters" (ALMA 1.3 mm)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: 2 GHz total, centered at 233.0, 246.0, 248.0 GHz  
  > "each with 128 15.625 MHz channels for a total of 2 GHz continuum bandwidth, and centered at 233.0, 246.0, and 248.0 GHz" (ALMA 1.3 mm)
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.054" x 0.031", PA 68.7 deg  
  > "with a synthesized beam of $0.054\ensuremath{''}\times0.031\ensuremath{''}$ and position angle of $68.7\ensuremath{^\circ}$" (ALMA 1.3 mm)
- max recoverable scale: _not stated_
- sensitivity: rms 39 uJy/beam  
  > "The continuum map has an rms of 39 $\mu$Jy beam$^{-1}$" (ALMA 1.3 mm)
- time on source: 11.19 minutes  
  > "The total on-source time was 11.19 minutes." (ALMA 1.3 mm)
- observing dates: UT 2015 November 1 (Cycle 3)  
  > "GQ Lup was observed with ALMA in Cycle 3 on UT 2015, November 1" (ALMA 1.3 mm)
- pi or archival as stated: _not stated_
- Line: 12CO 2-1 (230.538 GHz)
- Other facility **MagAO (VisAO)**: Halpha, i', z', Ys imaging, photometry and astrometry of GQ Lup A and B  
  > "GQ Lup was observed on UT 2015, April 16 in the simultaneous differential imaging (SDI) mode" (MagAO H$\alpha$ Photometry)
- External data: Gas mass of 71.3 +/- 8.3 Earth masses used for total disk mass  
  > "Total mass is calculated by adding our dust mass to the gas mass of 71.3 $\pm$ 8.3 $M_\ensuremath{\oplus}$ measured by (cite: M16)." (Table 2) [from MacGregor et al. 2017 (cite: M16)]
- External data: Disk radius of 46.5 AU from CO (3-2) used for tidal truncation analysis  
  > "We adopt a disk radius of 46.5 AU determined by (cite: M16) from CO (3–2) emission" (Orbital Constraints from Disk Size) [from MacGregor et al. 2017 (cite: M16)]
- External data: Orbit groups (a, e, i) of GQ Lup B  
  > "showed that the semi-major axis $a$, eccentricity $e$, and inclination $i$ of GQ Lup B’s orbit fall into three groups" (Orbital Constraints from Disk Size) [from Schwarz et al. 2016 (cite: S16)]

## Processing

### Calibration

- pipeline or manual: Standard CASA reduction  
  > "The data were reduced in the standard way with the `CASA` software package" (ALMA 1.3 mm)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: QSO J1337-1257 (bandpass J1427-4206, gain J1534-3526)  
  > "QSO J1427-4206 for bandpass calibration, and QSO J1337-1257 for flux calibration" (ALMA 1.3 mm)
- flux scale uncertainty: _not stated_
- self calibration: Four iterations of phase-only self-calibration  
  > "The final 1.3 mm continuum map was produced after four iterations of phase-only self-calibration using a model produced from the CLEAN algorithm." (ALMA 1.3 mm)

### Imaging

- task: _not stated_
- deconvolver: MSMFS-CLEAN, no frequency dependence, point sources and 1, 2, 4, 8 times beam size  
  > "MSMFS-CLEAN algorithm (cite: RC11) with no frequency dependence, CLEAN components which are point sources and 1, 2, 4, and 8 times the size of the beam" (ALMA 1.3 mm)
- weighting robust: natural weighting  
  > "natural weighting for the best sensitivity" (ALMA 1.3 mm)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: Excluded -15 to 15 km/s of CO baseband  
  > "excluding channels in the $-15$ to 15 km s$^{-1}$ range of the CO baseband" (ALMA 1.3 mm)
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.054" x 0.031", PA 68.7 deg  
  > "with a synthesized beam of $0.054\ensuremath{''}\times0.031\ensuremath{''}$ and position angle of $68.7\ensuremath{^\circ}$" (ALMA 1.3 mm)
- final rms: 39 uJy/beam  
  > "The continuum map has an rms of 39 $\mu$Jy beam$^{-1}$" (ALMA 1.3 mm)

### Inherited from earlier work

- Accretion rate derivation method  
  > "We derived the mass accretion rates for GQ Lup A and B following (cite: R12) and (cite: C14)." (Derivation of Accretion Rates from H$\alpha$ Fluxes) [from Rigliaco et al. 2012 (cite: R12); Close et al. 2014 (cite: C14)]
- MagAO astrometric calibration  
  > "Following the calibrations in (cite: C13) and (cite: Males14)" (MagAO Astrometry of GQ Lup B) [from Close et al. 2013 (cite: C13); Males et al. 2014 (cite: Males14)]
- Dust mass prescription (optically thin)  
  > "using the standard prescription (cite: B90)" (GQ Lup B’s Disk Mass) [from Beckwith et al. 1990 (cite: B90)]

### Not stated but needed to reproduce (our reading)

- CASA version
- Channel-selection and mask details for CLEAN and self-calibration solution intervals
- Priors, parameter ranges, number of steps and burn-in for emcee fits
- Fixed parameters in RADMC-3D (photon counts, grid, distance, stellar mass)
- Source-finding routine details for the fake-source injection
- Lupus I distance error treatment

## Analysis recipe

1. **Calibrate and image 1.3 mm continuum**: CASA calibration, MSMFS CLEAN with natural weighting, four rounds of phase-only self-calibration  
  > "The final 1.3 mm continuum map was produced after four iterations of phase-only self-calibration using a model produced from the CLEAN algorithm." (ALMA 1.3 mm)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Upper limit on GQ Lup B disk mass**: Inject fake sources in 0.1" region, find 99.7% recovery flux per disk size, convert to dust mass with optically thin formula  
  > "For each disk size, we set the upper limit on disk flux to be the minimum flux for which 99.7% ($3\sigma$) of the input fake sources were detected." (GQ Lup B’s Disk Mass)
   - assumption: T = 20 K, kappa(1.3 mm) = 2.3 cm2/g, distance 150 pc  
  > "We used the standard assumption of a characteristic dust temperature of $T=20\,$K and a 1.3 mm dust opacity of $\kappa_{\nu} =$ 2.3 cm$^2$ g$^{-1}$." (GQ Lup B’s Disk Mass)
   - fitting: _not stated_
   - validation: _not stated_
3. **Fit GQ Lup A disk visibilities**: RADMC-3D radiative transfer models (power-law Model A and Lynden-Bell & Pringle Model B), Fourier transformed and fit to visibilities  
  > "We fit these models directly to the visibility data using the Markov Chain Monte Carlo code `emcee`" (GQ Lup A Disk Modeling)
   - software: RADMC-3D, emcee
   - parameter: 200 walkers; star 4300 K, 1 Lsun  
  > "We positioned 200 walkers throughout a large region of parameter space" (GQ Lup A Disk Modeling)
   - assumption: 70% silicate/30% graphite, grain size 5 nm to 3 mm, power-law -3.5, giving 2.25 cm2/g at 1.3 mm  
  > "This produced a 1.3 mm opacity of 2.25 cm$^{2}$ g$^{-1}$" (GQ Lup A Disk Modeling)
   - fitting: emcee affine-invariant ensemble sampler, chi^2 minimization  
  > "`emcee` uses an affine-invariant MCMC ensemble sampler" (GQ Lup A Disk Modeling)
   - validation: Two different density prescriptions give consistent parameters  
  > "Both models match the data well, and produce similar best-fit parameter values." (GQ Lup A’s Disk)
4. **MagAO photometry of GQ Lup B**: ADI+KLIP with grid search over parameters using injected fake planets; fake-planet injection for i', z', Ys  
  > "The optimum parameters were determined as those which maximized the mean S/N on the ensemble of positive fake planets injected at 8.7 mag brightness." (MagAO H$\alpha$ Photometry)
   - software: KLIP, Findr, IRAF, MATLAB
   - fitting: _not stated_
   - validation: Uncertainties from the standard deviation of fake planet results  
  > "Uncertainties were estimated from the standard deviation of the results from the fake planets." (MagAO H$\alpha$ Photometry)
5. **Accretion rates from Halpha**: L_Halpha to L_acc relation of Rigliaco et al. 2012, then L_acc ∝ G M Mdot / R  
  > "log$(L_\mathrm{acc}) =  2.99 + 1.49~\times$ log$(L_{\mathrm{H}\alpha})$" (Derivation of Accretion Rates from H$\alpha$ Fluxes)
   - assumption: A_V ~0.4 mag for A; no extinction correction for B; A's R mag 11.0 from literature  
  > "we estimated GQ Lup A’s average $R$ brightness to be 11.0 mag by averaging literature fluxes" (Derivation of Accretion Rates from H$\alpha$ Fluxes)
   - fitting: _not stated_
   - validation: Compared with literature accretion rates  
  > "Our measurement for A is similar to previous results" (Derivation of Accretion Rates from H$\alpha$ Fluxes)
6. **Tidal truncation constraint on GQ Lup B orbit**: Eggleton/Pichardo truncation radius formula compared to 46.5 AU disk radius for orbit groups  
  > "We hence arbitrarily use 25 $M_{\text{Jup}}$ for this calculation." (Orbital Constraints from Disk Size)
   - assumption: Secondary mass 25 MJup; disk radius 46.5 AU  
  > "We hence arbitrarily use 25 $M_{\text{Jup}}$ for this calculation." (Orbital Constraints from Disk Size)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : Data reduction and MSMFS imaging  
  > "The data were reduced in the standard way with the `CASA` software package" (ALMA 1.3 mm)
- **RADMC-3D** : Radiative transfer disk models  
  > "using the RADMC-3D code (cite: Dullemond12) to produce disk models" (GQ Lup A Disk Modeling)
- **emcee** : MCMC visibility fitting  
  > "using the Markov Chain Monte Carlo code `emcee` (cite: FM13)" (GQ Lup A Disk Modeling)
- **KLIP** : PSF subtraction for Halpha ADI  
  > "we then proceeded to employ the KLIP algorithm (cite: S12) for PSF subtraction with ADI" (MagAO H$\alpha$ Photometry)
- **Findr** : Cloud-based grid search of KLIP reductions  
  > "we employed the “Findr” distributed computing (cloud-based) data reduction system (cite: HB16)" (MagAO H$\alpha$ Photometry)
- **IRAF** : MagAO i', z', Ys reduction and photometry  
  > "Data reduction and photometry were carried out with IRAF((cite: T86), (cite: T93)) and MATLAB." (MagAO $i'$, $z'$, $Y_S$ Photometry)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| GQ Lup A 1.3 mm flux | 27.5 | 0.6 | mJy | 1 | We measured a flux of $27.5\pm0.6$ mJy for this source. |
| GQ Lup A dust mass (Model A) | 5.9 | 1.0 | Earth masses | 3 | Dust Mass ($M_\ensuremath{\oplus}$) / $5.9~\pm~1.0$ / $5.5~\pm~0.8$ |
| Disk radius (Model A / B) | 23.8 / 19.5 | 1.6 / 1.4 | AU | 3 | Radius (AU) / $23.8~\pm~1.6$ / $19.5~\pm~1.4$ |
| Disk inclination (Model A / B) | 56.2 / 55.3 | 4.8 / 6.0 | deg | 3 | Inclination ($^\circ$) / $56.2~\pm~4.8$ / $55.3~\pm~6.0$ |
| Disk position angle (Model A) | 348.8 | 4.8 | deg | 3 | PA ($^\circ$) / $348.8~\pm~4.8$ / $348.6~\pm~5.0$ |
| Surface density index gamma (Model A / B) | 0.10 / -0.21 | 0.22 / 0.20 | dimensionless | 3 | $\gamma$ / $0.10~\pm~0.22$ / $-0.21~\pm~0.20$ |
| GQ Lup B disk dust mass upper limit | <0.25-1 | not stated | Earth masses | 2 | our data put a upper limit on the disk mass for GQ Lup B at $<$0.25–1 $M_\ensuremath{\oplus}$ from a point source to 1/3 of the Hill radius |
| GQ Lup B Halpha contrast | 8.60 | 0.16 | mag | 4 | GQ Lup B was detected in H$\alpha$ at S/N $\sim$ 6.3 with a contrast of 8.60 $\pm$ 0.16 mag. |
| GQ Lup B separation | 0.721 | 0.003 | arcsec | 0 | GQ Lup B is 0.721$''$ $\pm$ 0.003$''$ from its host star, with a position angle of 277.6$^\circ$ $\pm$ 0.4$^\circ$ |
| GQ Lup B z' magnitude | 16.40 | 0.10 | mag | 4 | $z'=16.40\pm0.10$ mag |
| Accretion rate GQ Lup A | 1e-8 to 1e-7 | not stated | Msun/yr | 5 | The resulting accretion rates for GQ Lup A and B are $\dot{M}\sim10^{-8}$ to $10^{-7}~M_\ensuremath{\odot}~\mathrm{yr}^{-1}$ |

## Qualitative findings

- No gaps or inner cavity in GQ Lup A's disk; disk misaligned with stellar spin axis and probably with B's orbit  
  > "All these orbits are unlikely in the same plane of the disk." (Geometry of the System)

## Claim tuples

- H: Is GQ Lup A's disk compact, and does it have gaps? | E: Resolved 1.3 mm imaging and RADMC-3D visibility fitting | R: R~22 AU, i~56 deg, dust mass ~6 Earth masses, flat surface density, no gaps | F: Flat profile suggests radial grain-size variation; no inner massive scatterer is likely | **supported**
- H: Does GQ Lup B host a detectable dust disk? | E: Fake-source injection upper limit | R: No detection; <0.25-1 Earth masses | F: B's disk is dust-depleted | **supported**
- H: Does disk size constrain B's orbit? | E: Tidal truncation vs 46.5 AU disk | R: Only a~160-180 AU, e~0.2-0.3 survives | F: B's orbit likely has low eccentricity | **partially**
- H: How did GQ Lup B form? | E: Combine disk morphology, orbit and disk mass | R: No inner perturber, low eccentricity, low disk mass | F: In situ formation favored over scattering | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Scattering formation rejected for lack of disk gap or inner massive companion  
  > "Thus, it is quite unlikely that another massive body is very close to the primary star to serve as the scatterer." (Formation of GQ Lup B: Scattering)
- How they decided it was enough: _not stated_
- Limitation (authors): Orbit and geometry results are preliminary because many orbital solutions share similar chi^2  
  > "We caution that the results presented here and in Section [4.3](#Section:tidaltruncation) are preliminary." (Geometry of the System)
- Limitation (authors): Accretion rate for B is a lower limit due to unknown extinction  
  > "our $\dot{M}$ estimate for GQ Lup B should be considered a lower limit" (Derivation of Accretion Rates from H$\alpha$ Fluxes)
- Caveat (inferred, ours): Short 11-minute observation; B upper limit weaker than MacGregor et al.
- Caveat (inferred, ours): Dust mass depends on assumed opacity and RADMC-3D temperature
- Caveat (inferred, ours): Primary R magnitude from heterogeneous literature photometry
- Caveat (inferred, ours): Tidal truncation formula may fail for misaligned orbit

## Reproducibility

- Data public (paper): ALMA project code cited; MagAO data not stated as public  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2015.1.00773.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: CASA version and self-cal parameters
- Missing: emcee priors, bounds and chain lengths
- Missing: RADMC-3D setup details
- Missing: MagAO raw data availability
- Data volume (inferred): ~10-50 GB raw ALMA data
- Score (inferred): 5/5, ALMA data identified and imaging described, but key fitting and CASA parameters are missing.
- Rediscovery candidate: yes, Public ALMA data, an explicit recipe for imaging and disk fitting, and numeric results in Table 2.

## Links

- Method: Rau & Cornwell 2011 (cite: RC11) (MSMFS-CLEAN algorithm)
- Method: Foreman-Mackey et al. 2013 (cite: FM13) (emcee sampler)
- Companion: MacGregor et al. 2017 (cite: M16) (ALMA 870 um and CO(3-2) study of GQ Lup)

## Checks

```json
{
 "quotes": 72,
 "quotes_ok": 72,
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
  "facts": 83,
  "stated": 51,
  "rate": 0.614
 },
 "evidence_ok": true
}
```
