# ALMA Observations of a Candidate Molecular Outflow in an Obscured Quasar

`2014ApJ...790..160S` | The Astrophysical Journal 2014 | first author: Sun, Ai-Lei | arXiv: 1406.4520 | DOI: 10.1088/0004-637X/790/2/160

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: agn_and_quasars, nearby_galaxies
- Question: What are the morphology, kinematics and mass of molecular gas in the obscured quasar SDSS J1356+1026, and is there a molecular outflow related to the known ionized outflow?  
  > "allow us to constrain the morphology, kinematics, and mass of the molecular gas and to investigate the relation between the molecular gas and the ionized outflow." (Introduction)
- Target **SDSS J1356+1026**: coordinates 13:56:46.10, +10:26:09.09  
  > "At the redshift of the object (z=0.1231), 1$''$  corresponds to 2.2 kpc, and the luminosity distance is 580 Mpc." (Introduction); "The coordinate of SDSS J1356+1026 is (13:56:46.10, +10:26:09.09)." (SDSS J1356+1026); z/distance z=0.1231; luminosity distance 580 Mpc  
  > "At the redshift of the object (z=0.1231), 1$''$  corresponds to 2.2 kpc, and the luminosity distance is 580 Mpc." (Introduction); "The coordinate of SDSS J1356+1026 is (13:56:46.10, +10:26:09.09)." (SDSS J1356+1026); distance from redshift from SDSS spectrum fit; flat cosmology h=0.7, Om=0.3  
  > "At the redshift of the object (z=0.1231), 1$''$  corresponds to 2.2 kpc, and the luminosity distance is 580 Mpc." (Introduction); "The coordinate of SDSS J1356+1026 is (13:56:46.10, +10:26:09.09)." (SDSS J1356+1026)

## Data provenance

- ALMA projects: 2011.0.00652.S, 2012.1.00797.S
- bands: CO(1-0) Band 3 (102.6 GHz sky); CO(3-2) Band 7 (307.9 GHz sky)  
  > "The CO (3-2) at 307.9 GHz was observed in band 7" (2.1 ALMA CO (1-0) and CO (3-2) Observations)
- frequencies and spectral setup: 2 GHz total bandwidth, 128 channels of 15.625 MHz (46 km/s for CO 1-0; 15 km/s for CO 3-2); extra spw at 93 GHz for CO(1-0)  
  > "a total bandwidth of 2 GHz divided into 128 channels, each 15.625 MHz wide" (2.1 ALMA CO (1-0) and CO (3-2) Observations)
- continuum bandwidth: _not stated_
- arrays: 12-m antennae: 16 and 23 (CO 1-0, two blocks); 27 (CO 3-2)  
  > "using 16 and 23 12-m antennae for 68 and 63 minutes respectively" (2.1 ALMA CO (1-0) and CO (3-2) Observations)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 1.9"x1.3" PA -62 deg (CO 1-0); 0.35"x0.29" PA -60 deg (CO 3-2)  
  > "The beam size is $\theta_{\rm{beam}}=1.9\ensuremath{''} \times1.3\ensuremath{''}~(0.35\ensuremath{''} \times 0.29\ensuremath{''})$" (2.1 ALMA CO (1-0) and CO (3-2) Observations)
- max recoverable scale: 29" (CO 1-0); 10" (CO 3-2)  
  > "the maximum resolvable scale is $\theta_{\rm{MRS}}= 29\ensuremath{''}~(10\ensuremath{''})$" (2.1 ALMA CO (1-0) and CO (3-2) Observations)
- sensitivity: 0.37 mJy/beam (CO 1-0), 0.77 mJy/beam (CO 3-2) per channel  
  > "The resulting RMS noise level in each channel is 0.37 mJy beam$^{-1}$ (0.77 mJy beam $^{-1}$)." (2.1 ALMA CO (1-0) and CO (3-2) Observations)
- time on source: CO(1-0): 27 and 24 min; CO(3-2): 19 min  
  > "(27 and 24 minutes on-source)" (2.1 ALMA CO (1-0) and CO (3-2) Observations)
- observing dates: CO(1-0): May 9 and July 30, 2012; CO(3-2): July 6, 2013  
  > "on May 9 and July 30, 2012" (2.1 ALMA CO (1-0) and CO (3-2) Observations)
- pi or archival as stated: _not stated_
- Line: CO 1-0 (not stated)
- Line: CO 3-2 (not stated)
- Other facility **HST/WFC3 F814W**: I-band image used for positional alignment and stellar plume  
  > "The *HST*/WFC3 F814W image was observed on May 19 2012 with an integration time of 900 seconds" (2.2 Matching ALMA with Optical Data)
- Other facility **SDSS DR7**: spectrum for systemic velocity  
  > "We use the SDSS DR7 spectrum" (2.2 Matching ALMA with Optical Data)
- Other facility **WISE, IRAS, Herschel PACS/SPIRE**: IR photometry for SED decomposition  
  > "We further include data from the Wide-field Infrared Survey Explorer *WISE*" (3.4 SED)
- External data: Herschel PACS/SPIRE photometry  
  > "data from Petric et al. in prep." (3.4 SED) [from Petric et al. in prep.]
- External data: Ionized outflow properties (v~1000 km/s, t_dyn~1e7 yr, kinetic luminosity)  
  > "A simple geometric model yields a deprojected velocity $v \approx 1000$ km s$^{-1}$" (1.1 SDSS J1356+1026) [from (cite: 2012ApJ...746...86G)]
- External data: Stellar velocity dispersion 206±36 km/s  
  > "$\sigma_* = 206 \pm 36$ km s$^{-1}$  (cite: Greene:2009kt)" (4.1 The N nucleus) [from (cite: Greene:2009kt)]

## Processing

### Calibration

- pipeline or manual: calibration by the ALMA team  
  > "The data calibration was carried out by the ALMA team" (2.1 ALMA CO (1-0) and CO (3-2) Observations)
- casa version: CASA 3.3.0 (CO 1-0) and 4.1.0 (CO 3-2) for calibration; 4.1.0 for imaging  
  > "using CASA version 3.3.0 for CO (1-0) and 4.1.0 for CO (3-2)" (2.1 ALMA CO (1-0) and CO (3-2) Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Mars (CO 1-0), Titan (CO 3-2)  
  > "QSO 3C279 (J1516+0015), Mars (Titan), and J1415+133 (J1347+1217) were used for the bandpass, flux, and phase calibrators respectively." (2.1 ALMA CO (1-0) and CO (3-2) Observations)
- flux scale uncertainty: 5% Band 3, 10% Band 7  
  > "The absolute flux calibration accuracy is 5% for CO (1-0) (Band 3) and 10% for CO (3-2) (Band 7)." (2.1 ALMA CO (1-0) and CO (3-2) Observations)
- self calibration: _not stated_

### Imaging

- task: CASA clean  
  > "The imaging processing was carried out with the CASA task *clean*." (2.1 ALMA CO (1-0) and CO (3-2) Observations)
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 0.5  
  > "We used the *Briggs* visibility weighting with a *robustness* parameter of 0.5" (2.1 ALMA CO (1-0) and CO (3-2) Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: cleaned to 3 sigma per channel  
  > "All images are cleaned to the 3 $\sigma$ level in each channel." (2.1 ALMA CO (1-0) and CO (3-2) Observations)
- multiscale scales: _not stated_
- continuum subtraction: CO(1-0): uv-plane subtraction; none for CO(3-2)  
  > "Continuum subtraction was not applied to the CO (3-2) data cube as there are not enough line-free channels to determine the continuum level." (2.1 ALMA CO (1-0) and CO (3-2) Observations)
- line free channels: 36/43 channels on blue/red side (CO 1-0)  
  > "line free channels (36/43 channels on the blue/red side)" (2.1 ALMA CO (1-0) and CO (3-2) Observations)
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: CO(3-2) binned by two to 30 km/s channels; Hanning smoothing in correlator  
  > "giving a final channel width of 30 km s$^{-1}$" (2.1 ALMA CO (1-0) and CO (3-2) Observations)
- final beam: 1.9"x1.3" (CO 1-0); 0.35"x0.29" (CO 3-2)  
  > "with a PA=$-62^\circ~(-60^\circ)$" (2.1 ALMA CO (1-0) and CO (3-2) Observations)
- final rms: 0.37 / 0.77 mJy/beam per channel  
  > "The resulting RMS noise level in each channel is 0.37 mJy beam$^{-1}$ (0.77 mJy beam $^{-1}$)." (2.1 ALMA CO (1-0) and CO (3-2) Observations)

### Inherited from earlier work

- Two-temperature modified blackbody SED decomposition procedure, Tcold=35 K  
  > "Following the decomposition procedures of (cite: 2012ApJ...759..139K) we fit a two-temperature modified blackbody" (3.4 SED) [from (cite: 2012ApJ...759..139K)]
- ULIRG XCO = 0.4e20 with 0.5 dex error  
  > "we adopt an X$_{\rm{CO}}$ value for ULIRGs X$_{\rm{CO}}$= $0.4 \times 10^{20}$ cm$^{-2}$ (K km s$^{-1}$)$^{-1}$ with an error of 0.5 dex" (3.3 Molecular Gas Mass and Star Formation Rate) [from (cite: 1998ApJ...507..615D; 2013ARA&A..51..207B)]
- Volume-filling continuous outflow geometry  
  > "In the following we assume a volume-filling continuous outflow, as in (cite: 2012MNRAS.425L..66M) and (cite: 2014A&A...562A..21C)." (5.2.1 Properties of the Molecular Outflow) [from (cite: 2012MNRAS.425L..66M; 2014A&A...562A..21C)]

### Not stated but needed to reproduce (our reading)

- Exact clean parameters (cell size, image size, niter, masks, spectral-line channel ranges for CO 3-2)
- Line-free channel ranges for CO(3-2) 300 GHz continuum check
- Aperture sizes/centres for flux extraction
- Kinematic fitting details of 2D Gaussian per channel
- Herschel photometry values (Petric et al. in prep.)
- Exact formulae for outflow energetics and Kennicutt SFR conversion
- HST astrometric offset registration details

## Analysis recipe

1. **Measure 100 GHz continuum**: Moment-0 of line-free channels in 93/103 GHz spectral windows of CO(1-0) data  
  > "The radio 100 GHz continuum is measured from the line-free channels in two spectral windows at 93/103 GHz" (3.1 100 GHz Continuum)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Extract CO line fluxes**: Aperture photometry (apertures ≥2x beam) on CO(3-2); CO(1-0) N/W blend separated via point-source beam fit in 100-500 km/s and assumed CO(3-2) spectral shape  
  > "We use simple aperture photometry with apertures at least twice as large as the beam in order to enclose $\mathrel{\hbox{\rlap{\hbox{\lower 4pt\hbox{$\sim$}}}\hbox{\raise 2pt\hbox{$>$}}}}95 \%$ of the flux." (3.2 CO Flux Measurements); "We then recover the total N nucleus CO (1-0) flux in the entire velocity range ($-300$ to $500$ km s$^{-1}$) assuming that the CO (1-0) spectrum has a similar spectral shape to the CO (3-2) spectrum." (3.2 CO Flux Measurements)
   - parameter: Integration range -300 to 500 km/s (N, W); 300-500 (high-velocity); -80 to 50 (S)  
  > "A velocity range of 300 km s$^{-1}$$< v<$ 500 km s$^{-1}$ is used for the high velocity component of the N nucleus." (3.2 CO Flux Measurements)
   - fitting: Errors from beam-correlated noise with adjacent-channel correlation r=0.375  
  > "which has a Pearson correlation coefficient of $r = 0.375$" (3.2 CO Flux Measurements)
   - validation: _not stated_
3. **Derive molecular gas masses and SFR from CO**: Mass from CO(1-0) luminosity with ULIRG XCO; SFR via Schmidt-Kennicutt law assuming 300 pc disk  
  > "Using the Schmidt-Kennicutt law (cite: KennicuttJr:1998id), we find the star formation rate at the N nucleus to be SFR=1.2 $M_{\odot}$ yr$^{-1}$" (3.3 Molecular Gas Mass and Star Formation Rate)
   - assumption: alpha_CO = 0.86 Msun (K km/s pc^2)^-1, 0.5 dex error; outflow assumes L'(3-2)/L'(1-0)=1  
  > "This corresponds to $\alpha_{\rm{CO}}$= 0.86 $M_{\odot}$ (K kms pc$^{2}$)$^{-1}$" (3.3 Molecular Gas Mass and Star Formation Rate)
   - fitting: _not stated_
   - validation: _not stated_
4. **IR SED decomposition for SFR upper limit and Lbol**: Two-temperature modified blackbody fit to seven points; Tcold fixed 35 K, beta=1.5, 10% errors; Bell 2003 calibration for SFR  
  > "The temperature of the cold dust is fixed at $T_{\rm{cold}}=35$ K" (3.4 SED)
   - assumption: photometry errors 10%  
  > "All photometry errors are assumed to be 10%, which is representative of the systematic errors." (3.4 SED)
   - fitting: free: Twarm, Lwarm, Lcold; reduced chi2 of 1  
  > "The best-fit model (black line, Fig. [5](#fig:SED)) matches the data well with a reduced $\chi^2$ of 1." (3.4 SED)
   - validation: Fitting Tcold free recovers 35 K  
  > "Even if we fit the temperature of the cold component we recover $T_{\rm{cold}}=35$ K." (3.4 SED)
5. **N nucleus kinematics**: 2-D Gaussian fit per channel, linear fit of position vs velocity for PA, pv-diagram of width 0.5" along PA  
  > "In each channel we fit the emission with a 2-D Gaussian profile, and derive the best fit x and y positions" (4.1 The N nucleus)
   - assumption: Vc = sqrt2 sigma*  
  > "$V_c = \sqrt{2}\sigma_* = 291 \pm 50$ km s$^{-1}$ for an isothermal sphere" (4.1 The N nucleus)
   - fitting: linear model x=av+b within ±300 km/s  
  > "We fit a linear model $\textbf{\emph{x}}=\textbf{\emph{a}}v+\textbf{\emph{b}}$ to the best fit positions in the velocity range of $\pm300$ km s$^{-1}$" (4.1 The N nucleus)
   - validation: _not stated_
6. **Outflow energetics**: r=0.3 kpc, v=500 km/s, M=7e7; Mdot=3Mv/r for volume-filling outflow  
  > "If the outflow is continuous and volume filling inside a sphere or cone with a constant velocity, the mass outflow rate is $\dot{M}=3Mv/r \approx 350$ $M_{\odot}$ yr$^{-1}$" (5.2.1 Properties of the Molecular Outflow)
   - fitting: _not stated_
   - validation: Order-of-magnitude estimates only  
  > "These quantities are only order of magnitude estimates." (5.2.1 Properties of the Molecular Outflow)

## Software

- **CASA** 3.3.0 / 4.1.0: calibration, continuum subtraction, heliocentric correction, imaging (clean)  
  > "We further used CASA version 4.1.0 to apply continuum subtraction \[CO (1-0) only\], heliocentric correction, imaging, and cleaning." (2.1 ALMA CO (1-0) and CO (3-2) Observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Total molecular gas mass | 9e8 | +19/-6 e8 | Msun | 3 | / Sum / $9^{+19}_{-6}\times 10^8$ / |
| N nucleus molecular mass | 3e8 | +6/-2 e8 | Msun | 3 | the molecular gas mass is estimated to be $3^{+6}_{-2} \times10^8$ $M_{\odot}$ |
| W arm molecular mass | 5e8 | +11/-3 e8 | Msun | 3 | the W arm contains $5^{+11}_{-3} \times10^8$ $M_{\odot}$  of molecular gas |
| 100 GHz continuum flux density | 1.51 | ±0.07 (rms) ±0.07 (calibration) | mJy | 1 | a flux density of $1.51 \pm 0.07 \pm 0.07$ mJy |
| High-velocity component CO(3-2) flux | 0.99 | 0.10 | Jy km/s | 2 | / N Outflow       / 300 : 500     / $0.06\pm0.08$    / $2.2\pm2.7$ |
| Outflow molecular mass | 7e7 | +15/-5 e7 | Msun | 3 | $M_{\mathrm{mol}} =7^{+15}_{-5}\times10^7$ $M_{\odot}$ |
| Mass outflow rate (volume filling) | 350 | not stated | Msun/yr | 6 | $\dot{M}=3Mv/r \approx 350$ $M_{\odot}$ yr$^{-1}$ |
| Outflow kinetic luminosity | 3e43 | not stated | erg/s | 6 | $\dot{E}_{\rm{kin}} \approx 3\times10^{43}$ ergs s$^{-1}$ |
| Momentum boost | 3 | not stated | dimensionless | 6 | with a momentum boost of $\dot{p}/(\ensuremath{L_{\mathrm{bol}}}/c)\approx$ 3 |
| SFR upper limit from FIR SED | 21 | upper limit | Msun/yr | 4 | upper limit on the star formation rate of 21 $M_{\odot}$ yr$^{-1}$ |
| Warm dust temperature | 81 | not stated | K | 4 | The best-fit temperature of the warm component is high $T_{\rm{warm}}=81$ K |
| N nucleus velocity gradient | 1077 | not stated | km/s/kpc | 5 | best-fit gradient of 1077 km s$^{-1}$ kpc$^{-1}$ |

## Qualitative findings

- No molecular gas detected at the extended ionized bubble location (Mmol<8.6e7 Msun)  
  > "Therefore, the molecular gas does not dominate the mass of the extended ionized outflow." (4.4 Molecular Counterpart to the Ionized Bubble)

## Claim tuples

- H: Is there a molecular outflow at the N nucleus? | E: CO(3-2) channel maps and pv-diagram at 0.35" resolution | R: Compact red-shifted 300-500 km/s feature deviating from rotation, M~7e7 Msun | F: Candidate AGN-driven molecular outflow; accretion not ruled out | **partially**
- H: Can star formation power the outflow? | E: SFR limits from CO and FIR SED vs required SFR>43 | R: SFR<16 and <21 Msun/yr | F: Star formation insufficient; AGN likely drives | **supported**
- H: Origin of W arm gas | E: Flux/mass measurement and comparison with tidal features | R: 5e8 Msun in 4 kpc tidal arm | F: Massive tidal feature from elliptical/disk merger | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Accretion of tidal-arm material onto the disk considered as alternative to outflow  
  > "First, the high velocity feature may represent material accreting onto the disk from an external source, perhaps the W tidal arm." (5.2 High Velocity Molecular Gas at the N Nucleus)
- How they decided it was enough: _not stated_
- Limitation (authors): Outflow quantities order-of-magnitude; XCO and line ratio uncertain  
  > "First, the $X_{\rm{CO}}$ factor in the context of an outflow is uncertain." (5.2.1 Properties of the Molecular Outflow)
- Caveat (inferred, ours): Outflow identification rests on a 300-500 km/s feature in one marginally resolved line without CO(1-0) detection
- Caveat (inferred, ours): XCO factor dominates mass errors
- Caveat (inferred, ours): CO(3-2) not continuum-subtracted
- Caveat (inferred, ours): CO(1-0) deblending model-dependent

## Reproducibility

- Data public (paper): Project codes given; public status not explicitly stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2011.0.00652.S and 2012.1.00797.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Cell/image size and clean iteration settings
- Missing: Herschel photometry
- Missing: aperture definitions
- Data volume (inferred): ~10-50 GB raw for two small Cycle 0/1 datasets
- Score (inferred): 3/5, Data are well specified and key settings (robust, velocity ranges) given, but several imaging and photometry details and Herschel data are missing.
- Rediscovery candidate: yes, ALMA project codes are given, recipe mostly complete, and results (fluxes, masses) are numeric.

## Links

- Method: (cite: 2012ApJ...759..139K) (SED decomposition procedure)
- Method: (cite: 2014A&A...562A..21C) (outflow criteria and energetics)
- Companion: (cite: 2012ApJ...746...86G) (discovery of ionized outflow in this object)
- Related: SDSS
- Related: WISE
- Related: Herschel
- Related: FIRST
- Related: HST

## Checks

```json
{
 "quotes": 77,
 "quotes_ok": 77,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 12,
 "numeric_problems": 0,
 "fill": {
  "facts": 78,
  "stated": 53,
  "rate": 0.679
 },
 "evidence_ok": true
}
```
