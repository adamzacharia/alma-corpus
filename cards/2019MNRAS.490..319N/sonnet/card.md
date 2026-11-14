# WISDOM project - V. Resolving molecular gas in Keplerian rotation around the supermassive black hole in NGC 0383

`2019MNRAS.490..319N` | Monthly Notices of the Royal Astronomical Society 2019 | first author: North, Eve V. | arXiv: 1909.05884 | DOI: 10.1093/mnras/stz2598

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, agn_and_quasars
- Question: What is the mass of the supermassive black hole in NGC 0383, measured by forward-modelling resolved 12CO(2-1) gas kinematics?  
  > "we present a measurement of the mass of the supermassive black hole (SMBH) in the nearby early-type galaxy NGC 0383 (radio source 3C 031)." (abstract)
- Target **NGC 0383 (3C 031)**: coordinates RA=01h07m24.96s, Dec=+32d24m45.11s (continuum point source)  
  > "NGC 0383 is a dusty lenticular galaxy at a distance of $66.6\pm9.9$ Mpc (cite: Freedman2001)." (2 Target: NGC 0383); z/distance 66.6±9.9 Mpc  
  > "NGC 0383 is a dusty lenticular galaxy at a distance of $66.6\pm9.9$ Mpc (cite: Freedman2001)." (2 Target: NGC 0383); distance from Tully-Fisher relation, Freedman2001  
  > "NGC 0383 is a dusty lenticular galaxy at a distance of $66.6\pm9.9$ Mpc (cite: Freedman2001)." (2 Target: NGC 0383)

## Data provenance

- ALMA projects: 2015.1.00419.S, 2016.1.00437.S
- bands: _not stated_
- frequencies and spectral setup: 1850 MHz window centred at 226.6 GHz, raw channel ≈1.3 km/s; three 2 GHz continuum windows  
  > "A 1850 MHz correlator window was placed over the CO(2–1) line and centred at 226.6 GHz" (2.1 ALMA Observations); "Three additional low spectral resolution correlator windows were included to detect continuum emission, each of 2 GHz width." (2.1 ALMA Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: C36-5 (15–704 m) and C40-8 (21–3637 m)  
  > "Configurations C36-5 (baselines 15–704 m) and C40-8 (baselines 21–3637 m) were used" (2.1 ALMA Observations)
- baselines: _not stated_
- angular resolution: 0.18''x0.1'' (58x32 pc)  
  > "spatial resolution of $58\times32$ pc$^{2}$ ($0.18\ensuremath{''}\times0.1\ensuremath{''}$)" (abstract)
- max recoverable scale: up to 4''  
  > "to achieve sensitivity to emission on scales up to 4$''$" (2.1 ALMA Observations)
- sensitivity: continuum rms 35 uJy/beam; cube rms 0.4 mJy/beam per 10 km/s channel  
  > "with a RMS noise level of 0.4 mJy beam$^{-1}$ in each 10 km s$^{-1}$ channel." (2.1 ALMA Observations)
- time on source: 2.22 and 28.8 min  
  > "with on-source integration times of 2.22 and 28.8 min, respectively." (2.1 ALMA Observations)
- observing dates: 21 June 2016 and 16 August 2017  
  > "observed with ALMA on the 21st of June 2016 at moderate resolution (0.5$''$) and then on the 16th of August 2017 at high resolution (0.1$''$)" (2.1 ALMA Observations)
- pi or archival as stated: WISDOM project programmes  
  > "both as part of the WISDOM project" (2.1 ALMA Observations)
- Line: 12CO J=2-1 (not stated)
- Other facility **HST NICMOS F160W + 2MASS H-band**: Images for MGE stellar light model  
  > "We use a combined *Hubble Space Telescope (HST)* Near Infrared Camera and Multi-Object Spectrometer (NICMOS) F160W and Two Micron All-Sky Survey (2MASS) $H$-band image." (3.1 Mass Model)
- Other facility **NED**: Literature radio–sub-mm fluxes for SED  
  > "Adding to our flux those tabulated in the NASA/IPAC Extragalactic Database (NED)" (2.3 Continuum Emission)
- External data: Stellar velocity dispersion sigma_e=239±16 km/s  
  > "$\sigma_{\rm e}=239\pm16$  km s$^{-1}$" (2 Target: NGC 0383) [from Bosch2016; Beifiori2009]
- External data: IRAM 30-m CO(2-1) flux 74.4±2.8 Jy km/s and CO(1-0) 29.8 Jy km/s  
  > "Their CO(2–1) flux is $74.4\pm2.8$ Jy km s$^{-1}$." (2.2 Line Emission) [from OcanaFlaquer2010]
- External data: Distance 66.6±9.9 Mpc  
  > "at a distance of $66.6\pm9.9$ Mpc (cite: Freedman2001)" (2 Target: NGC 0383) [from Freedman2001]

## Processing

### Calibration

- pipeline or manual: standard ALMA pipeline by ARC staff  
  > "The raw ALMA data were calibrated using the standard ALMA pipeline, as provided by the ALMA regional centre staff." (2.1 ALMA Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0237+2848 (amplitude), J2253+1608 (bandpass), for the two observations respectively  
  > "The amplitude and bandpass calibrator used in the two observations was respectively J0237+2848 and J2253+1608." (2.1 ALMA Observations)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA; configurations combined and imaged; CLEAN  
  > "We then used the COMMON ASTRONOMY SOFTWARE APPLICATIONS (CASA; (cite: McMullin2007)) package to combine the two configurations and image the resultant visibilities." (2.1 ALMA Observations)
- deconvolver: _not stated_
- weighting robust: Briggs, robust 0.5  
  > "The data presented here were produced using Briggs weighting with a robust parameter of 0.5" (2.1 ALMA Observations)
- uv taper: _not stated_
- cell size: 0.035''  
  > "pixels of 0.035$''$$\times$0.035$''$ were chosen" (2.1 ALMA Observations)
- image size: _not stated_
- masking: interactively identified regions per channel; clean to threshold of dirty-channel RMS  
  > "cleaned (see (cite: Hogbom1969) for the CLEAN procedure) in interactively-identified regions of source emission in each channel, to a threshold equal to the RMS noise of the dirty channels." (2.1 ALMA Observations)
- multiscale scales: _not stated_
- continuum subtraction: uv-plane with UVCONTSUB over full line-free bandwidth  
  > "measured over the full line-free bandwidth, and then subtracted from the data in the $uv$–plane using the CASA task UVCONTSUB." (2.1 ALMA Observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.18''x0.1'' at PA 6.6 deg  
  > "$\theta_{\mathrm{maj}}\times\theta_{\mathrm{min}}\approx0.18\ensuremath{''}\times0.1\ensuremath{''}$ at a position angle of 6.6$^\circ$" (2.1 ALMA Observations)
- final rms: 0.4 mJy/beam per 10 km/s channel  
  > "with a RMS noise level of 0.4 mJy beam$^{-1}$ in each 10 km s$^{-1}$ channel." (2.1 ALMA Observations)

### Inherited from earlier work

- SMBH mass modelling method  
  > "The method we use to estimate the SMBH mass is described in detail in (cite: Davis2017) and was used in the previous WISDOM papers" (3 Dynamical Modelling) [from (cite: Davis2017)]
- Chi2 rescaling for systematic uncertainties  
  > "The same method was applied and discussed in detail by (cite: Smith2019), and we use it here in the MCMC fitting of NGC 0383." (3.2 Bayesian analysis) [from VanDenBosch2009; Smith2019]
- Masked moment technique  
  > "created using a masked moment technique (cite: Dame2011)" (2.2 Line Emission) [from (cite: Dame2011)]

### Not stated but needed to reproduce (our reading)

- Line-free channels used for continuum
- Exact clean mask regions (interactive)
- MCMC prior limits beyond table, convergence/burn-in details
- X_CO and gas mass conversion used for gas disc
- Beam/pixel treatment for KinMS gas particle number
- Whether archive pipeline products were reused as is, and CASA version

## Analysis recipe

1. **Calibrate, combine and image CO cube**: Standard pipeline calibration; combine two configs in CASA; uvcontsub; clean with Briggs 0.5 to 10 km/s channels  
  > "A three-dimensional RA-Dec-velocity data cube was produced with a binned channel width of 10 km s$^{-1}$." (2.1 ALMA Observations)
   - software: CASA
   - fitting: _not stated_
   - validation: Compared total flux with IRAM 30-m: 87.1 vs 74.4 Jy km/s, concluding no flux resolved out  
  > "it is unlikely that we resolve out flux in our observations." (2.2 Line Emission)
2. **Moment maps and PVD**: Masked moments with smoothed-cube mask at 0.8 x RMS; PVD from 5-pixel pseudo-slit at PA 142 deg  
  > "The mask selects pixels with an amplitude in the smoothed cube greater than 0.8 times the RMS of the unsmoothed data cube." (2.2 Line Emission)
   - fitting: _not stated_
   - validation: _not stated_
3. **Stellar mass model**: MGE fit to HST F160W + 2MASS H image; circular velocity from MGE_CIRCULAR_VELOCITY with M/L=1, scaled and SMBH point mass added  
  > "The circular velocity is then multiplied element-wise by the square root of the mass-to-light ratio adopted, and a point mass representing the SMBH is added in the centre." (3.1 Mass Model)
   - software: MGE_FIT_SECTORS, MGE_CIRCULAR_VELOCITY
   - assumption: Stellar mass dominates potential in inner parts; dark matter negligible  
  > "We assume that the stellar mass dominates the potential in the inner parts of the galaxy" (3.1 Mass Model)
   - fitting: _not stated_
   - validation: _not stated_
4. **Forward-model cube and fit SMBH mass**: KinMS with gas particles from SkySampler of CLEAN components; MCMC fit to whole cube, 100,000 iterations; linear M/L profile; thin disc  
  > "A single fit was made to the whole clean data cube, with one hundred thousand iterations." (3.2 Bayesian analysis)
   - software: KinMS, KinMS_MCMC, SkySampler
   - parameter: Flat priors, SMBH mass flat in log-space; errors = RMS of line-free channels  
  > "the only exception being the SMBH mass prior that was flat in log-space." (3.2 Bayesian analysis)
   - assumption: Distance 66.6 Mpc; thin disc  
  > "With no evidence to the contrary, we use the thin disc approximation for NGC 0383." (3.2 Bayesian analysis)
   - fitting: MCMC; chi2 rescaled by sqrt(2N), N≈5.9e6, P=10; covariance of beam not included  
  > "This sets the 68.3% (99.7%) confidence level at $\chi^{2}_{\mathrm{min}} +\sqrt{2N}$ ($\chi^{2}_{\mathrm{min}} +3\sqrt{2N}$)." (3.2 Bayesian analysis)
   - validation: Reduced chi2 1.01; models without SMBH or without stars compared on PVD  
  > "It has a reduced $\chi^{2}$ of 1.01." (3.2 Bayesian analysis)
5. **Continuum SED**: Point-source continuum flux plus NED data fitted with power law  
  > "the data are fitted well with a simple power law for the flux $F$ as a function of frequency" (2.3 Continuum Emission)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : combining configs, imaging, UVCONTSUB  
  > "to combine the two configurations and image the resultant visibilities" (2.1 ALMA Observations)
- **KinMS** : forward-modelling the data cube  
  > "We make use of the publicly available KINEMATIC MOLECULAR SIMULATION (KinMS)" (3 Dynamical Modelling)
- **KinMS_MCMC** : MCMC fitting  
  > "making use of the IDL KINMS_MCMC" (3.2 Bayesian analysis)
- **SkySampler** : sampling CLEAN components into gas particles  
  > "Using the SKYSAMPLER" (3.2 Bayesian analysis)
- **MGE_FIT_SECTORS** v4.12: Multi-Gaussian Expansion of stellar light  
  > "using the method implemented in the MGE_FIT_SECTORS Interactive Data Language (IDL) software" (3.1 Mass Model)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| SMBH mass | 4.2e9 | ±0.7e9 (3σ) | Msun | 4 | SMBH mass of $(4.2\pm0.7)\times10^{9}$ M$_{\odot}$ |
| Inner stellar M/L (F160W) | 2.78 | 0.61 (3σ) | Msun/Lsun | 4 | Stellar $M/L$ inner ( M$_{\odot}$/ L$_{\odot,\,\mathrm{F160W}}$) / 0.01–10 / 2.78 / 0.21 / 0.61 |
| Inclination | 37.58 | 3.48 (3σ) | deg | 4 | Inclination ($^\circ$) / 26–89 / 37.58 / 1.67 / 3.48 |
| Gas velocity dispersion | 8.32 | 2.11 (3σ) | km/s | 4 | Velocity dispersion (km s$^{-1}$) / 0–15 / 8.32 / 0.72 / 2.11 |
| R_SOI | 316 | ±60 | pc | 4 | the latter also yielding an exact $R_{\rm SOI}=316\pm60$ pc |
| Total CO(2-1) flux | 87.1 | not stated | Jy km/s | 2 | The total CO(2–1) flux is 87.1 Jy km s$^{-1}$. |
| Continuum flux at 235.33 GHz | 65.2 | 0.1 | mJy | 5 | total integrated intensity of 65.2$\pm$0.1 mJy at a central frequency of 235.33 GHz |
| SED power-law index | -0.66 | 0.03 | dimensionless | 5 | power-law index $\alpha = -0.66\pm0.03$ |
| Systemic velocity | 4925 | ±4 | km/s | 4 | defines a systemic velocity of $V=4925\pm4$  km s$^{-1}$ |

## Qualitative findings

- Smooth, relaxed nuclear gas disc with weak ring/spiral features, not disturbed by AGN jets; clear Keplerian rise within R_SOI  
  > "NGC 0383 has a kinematically-relaxed, smooth nuclear molecular gas disc with weak ring/spiral features." (abstract)

## Claim tuples

- H: Can resolved CO(2-1) kinematics measure the SMBH mass in NGC 0383? | E: KinMS forward-modelling with MCMC of ALMA cube | R: M_BH=(4.2±0.7)e9 Msun (3σ) | F: SMBH detected with R_SOI well resolved; mass nearly independent of M/L | **supported**
- H: Does low-J CO probe the same gas as megamasers? | E: Convert max observed velocity to Schwarzschild radii | R: ≈1.36e5 Schwarzschild radii vs 5e4–1.5e6 for megamasers | F: Molecular gas method probes same material as megamasers | **supported**
- H: Does NGC 0383 lie on the M_BH–sigma relation? | E: Compare with Bosch2016 relation | R: On upper edge of scatter | F: Possibly an over-massive black hole | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Constant M/L fit did not fit the entire cube, so a linear M/L profile adopted  
  > "Initial fits used a single mass-to-light ratio for the whole disc, but this did not provide a good fit to the entire data cube." (3.2 Bayesian analysis)
- How they decided it was enough: _not stated_
- Limitation (authors): Distance uncertainty ≈15% dominates and is not included; inclination degeneracy dominates error budget  
  > "as is customary we do not include the distance uncertainty in our result." (4.1 Uncertainties)
- Caveat (inferred, ours): Low inclination (~38 deg) with strong inclination–mass degeneracy
- Caveat (inferred, ours): Short 2.2 min moderate-resolution track
- Caveat (inferred, ours): chi2 rescaling is approximate
- Caveat (inferred, ours): Thin disc assumption untested

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Code: KinMS, KinMS_MCMC and SkySampler on GitHub  
  > "<https://github.com/TimothyADavis/KinMS_MCMC>" (footnotes)
- Missing: Line-free channels
- Missing: CASA version
- Missing: Interactive clean masks
- Missing: Exact MCMC code settings
- Data volume (inferred): ~50-150 GB raw for two ALMA execution blocks
- Score (inferred): 3/5, Data programmes and code public and method well described, but interactive clean masks and some settings are unspecified.
- Rediscovery candidate: yes, Archival data with named codes, public KinMS code, and numeric results; some imaging details missing.

## Links

- Method: Davis2017 (Detailed SMBH mass method)
- Method: Davis2013a (KinMS)
- Method: Smith2019 (SkySampler and chi2 rescaling)
- Method: VanDenBosch2009 (chi2 rescaling)
- Companion: Davis2013b; Onishi2017; Davis2018; Smith2019 (Previous WISDOM papers)
- Related: WISDOM

## Checks

```json
{
 "quotes": 66,
 "quotes_ok": 66,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 9,
 "numeric_problems": 0,
 "fill": {
  "facts": 78,
  "stated": 49,
  "rate": 0.628
 },
 "evidence_ok": true
}
```
