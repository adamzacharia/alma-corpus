# A New Feedback Cycle in the Archetypal Cooling Flow Group NGC 5044

`2021ApJ...906...16S` | The Astrophysical Journal 2021 | first author: Schellenberger, Gerrit | arXiv: 2010.13804 | DOI: 10.3847/1538-4357/abc488

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: star_formation, nearby_galaxies, agn_and_quasars
- Question: What is the current state of the central AGN in the cooling-flow group NGC 5044 (jets, accretion) and does it mark a new feedback cycle?  
  > "We conclude that the age of the jets is much younger than the innermost cavities, marking the start of a new feedback cycle." (abstract)
- Target **NGC 5044**: coordinates RA 13h15m23.9613s, Dec -16d23m7.549s  
  > "We adopt a systemic velocity of $\SI{2757}{km\,s^{-1}}$ (heliocentric) for NGC 5044 and a luminosity distance of $\SI{31.2}{Mpc}$ ((cite: Tonry2001-wi))" (1.3 The central radio source in NGC 5044); "The position of the core is R.A. $13^{\rm h}\,15^{\rm m}\,23.9613^{\rm s}$  Dec. $\ang{-16;23;7.549}$" (3.1 VLBA observations); z/distance 31.2 Mpc; 2757 km/s  
  > "We adopt a systemic velocity of $\SI{2757}{km\,s^{-1}}$ (heliocentric) for NGC 5044 and a luminosity distance of $\SI{31.2}{Mpc}$ ((cite: Tonry2001-wi))" (1.3 The central radio source in NGC 5044); "The position of the core is R.A. $13^{\rm h}\,15^{\rm m}\,23.9613^{\rm s}$  Dec. $\ang{-16;23;7.549}$" (3.1 VLBA observations); distance from Tonry et al. 2001  
  > "We adopt a systemic velocity of $\SI{2757}{km\,s^{-1}}$ (heliocentric) for NGC 5044 and a luminosity distance of $\SI{31.2}{Mpc}$ ((cite: Tonry2001-wi))" (1.3 The central radio source in NGC 5044); "The position of the core is R.A. $13^{\rm h}\,15^{\rm m}\,23.9613^{\rm s}$  Dec. $\ang{-16;23;7.549}$" (3.1 VLBA observations)

## Data provenance

- ALMA projects: _none stated_
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: CO 1-0 and 2-1 (line-free windows used for continuum) (around 110 GHz and 230 GHz)
- Other facility **VLBA**: C and X band imaging of the parsec-scale core and jets (project BS283)  
  > "Our VLBA program (NRAO project ID BS283, PI: Schellenberger) to observe the central continuum source in NGC 5044 with VLBA was carried out in March and April 2020." (2.1 VLBA)
- Other facility **JCMT/SCUBA-2**: 450 and 850 micron fluxes and variability light curve  
  > "NGC 5044 has been observed several times in various projects (see Tab. [1](#tab:jcmt)), from which obtained the reduced datasets from the Canadian Astronomy Data Centre (CADC)." (2.2 JCMT)
- Other facility **ATCA**: 4.8 and 8.6 GHz fluxes from 2008 data  
  > "The 2008 dataset was downloaded from the Australia Telescope Online archive" (2.3 ATCA)
- Other facility **GMRT, VLA, VLASS**: low-frequency fluxes for SED  
  > "We also used the data products of the VLA Sky Survey (VLASS, (cite: Lacy2020-kg)) at $\SI{3}{GHz}$ taken in 2019." (3.2 SED)
- External data: ALMA 100-243 GHz continuum fluxes and CO absorption results (previously published ALMA data)  
  > "As seen already with ALMA ((cite: Schellenberger2020-vl; David2014-jn)) the total flux of the continuum source keeps rising with increasing frequency." (3.2 SED) [from (cite: Schellenberger2020-vl)]
- External data: Reduced GMRT datasets at 235, 320, 610 MHz  
  > "we use the reduced GMRT datasets at 235, 320, and $\SI{610}{MHz}$ (from (cite: Giacintucci2011-ru))" (3.2 SED) [from (cite: Giacintucci2011-ru)]
- External data: Black hole mass from stellar dynamics, 2.27e8 Msun  
  > "The ADAF black hole mass is only 3% below the value derived from stellar dynamics ($\SI{2.27e8}{M_\odot}$, (cite: David2009-hn))" (4.3 Advection dominated accretion) [from (cite: David2009-hn)]

## Processing

### Calibration

- pipeline or manual: VLBA: AIPS and VLBAUTIL tasks, then CASA self-calibration; ALMA: not stated  
  > "The correlator output was reduced using the NRAO Astronomical Image Processing System (AIPS; (cite: Greisen2003-le)) Version 31DEC19 and the VLBAUTIL tools." (2.1 VLBA)
- casa version: CASA 5.7.0 (VLBA imaging)  
  > "Common Astronomy Software Applications package (CASA; (cite: McMullin2007-ed)) Version 5.7.0." (2.1 VLBA)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: tclean (VLBA)  
  > "Imaging was performed using tclean with the mtmfs deconvolver algorithm ((cite: Rau2011-gx)), Briggs weighting scheme (robust $=1$)" (2.1 VLBA)
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: scales 0 and 10  
  > "cleaning done on scales 0 and 10, so we are able to map extended emission more accurately." (2.1 VLBA)
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: 5 mas for spectral index map  
  > "We use this as our spectral index map after some smoothing (5 mas)." (2.1 VLBA)
- final beam: 4.5 x 2.5 mas  
  > "a resolution of $4.5 \times \SI{2.5}{mas}$ ($0.68 \times \SI{0.38}{pc}$" (3.1 VLBA observations)
- final rms: 21 uJy/beam  
  > "we are able to reach a noise level of $\SI{21}{\mu Jy\,bm^{-1}}$" (3.1 VLBA observations)

### Inherited from earlier work

- ALMA continuum measurements, absorption features and variability from earlier ALMA analysis  
  > "(cite: Schellenberger2020-vl) note a time variability of the continuum source on timescales of years at mm wavelength" (1.3 The central radio source in NGC 5044) [from (cite: Schellenberger2020-vl)]
- ADAF viscosity alpha=0.3 and beta=0.5 priors  
  > "We set both, $\alpha_\text{ADAF}$ and $\beta$, with tight priors to the values in (cite: Mahadevan1997-rx), $0.3$ and $0.5$, respectively." (3.2 SED) [from (cite: Mahadevan1997-rx)]

### Not stated but needed to reproduce (our reading)

- ALMA project codes, dates, array configs and how the ALMA continuum fluxes were measured (task, channels, uv-range, flux scale)
- MCMC sampler, priors and likelihood for the SED fit
- Which ALMA data underlie Table fluxes at 230 and 243 GHz
- VLBA robust weighting details, self-cal solints

## Analysis recipe

1. **Image VLBA data and measure jets/core**: AIPS calibration, CASA tclean mtmfs with two Taylor terms, self-calibration; compact component via baselines >35 Mlambda and uvsub  
  > "We also map only the compact emission by selecting baselines larger than $\SI{35}{M\lambda}$, where we find a total emission of $\SI{11(1)}{mJy}$" (3.1 VLBA observations)
   - software: AIPS, CASA
   - fitting: _not stated_
   - validation: Flux consistent with ATCA and VLASS  
  > "consistent with measurements from ATCA (at 4.8 and $\SI{8.6}{GHz}$)" (3.1 VLBA observations)
2. **Build radio to sub-mm SED**: Combine fluxes from GMRT, VLA, VLASS, ATCA, VLBA, ALMA line-free windows, JCMT  
  > "The fluxes used for our SED fitting are listed in Tab. [\[tab:fluxes\]](#tab:fluxes) and shown in Fig. [3](#fig:sed)." (3.2 SED)
   - software: Starlink, CASA
   - fitting: _not stated_
   - validation: _not stated_
3. **Fit CI plus ADAF model**: MCMC fit of absorbed continuous injection model plus ADAF  
  > "The combined absorbed CI plus ADAF model fits our observations reasonably well, which is reflected in the $\chi^2_{\rm red} \approx 5$." (3.2 SED)
   - assumption: alpha_ADAF=0.3, beta=0.5 fixed with tight priors  
  > "We set both, $\alpha_\text{ADAF}$ and $\beta$, with tight priors to the values in (cite: Mahadevan1997-rx), $0.3$ and $0.5$, respectively." (3.2 SED)
   - fitting: MCMC, multiple chains from different regions  
  > "the parameter space is sufficiently explored, as tested by multiple chains starting from different regions in parameter space." (3.2 SED)
   - validation: Compared with VLBA jet and core fluxes and independent mass  
  > "We also note, that the two model components show very good agreement with the VLBA fluxes for the jet and core" (3.2 SED)
4. **Variability and jet age**: Sinusoid fit to SCUBA-2 lightcurve; jet age from break frequency with equipartition B  
  > "Assuming a periodicity by fitting a sinusoidal to the lightcurve results in a period $T=\SI{2.5(3)}{yr}$" (3.3 Variability)
   - assumption: B = 4.7 mG from minimum energy  
  > "which yields $B = \SI{4.7}{mG}$" (4.4 Energy injection to the jets)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **AIPS** 31DEC19: VLBA calibration  
  > "Version 31DEC19 and the VLBAUTIL tools." (2.1 VLBA)
- **CASA** 5.7.0: VLBA imaging and self-cal; ATCA uvmodelfit  
  > "Common Astronomy Software Applications package (CASA; (cite: McMullin2007-ed)) Version 5.7.0." (2.1 VLBA)
- **Starlink** 2018A: SCUBA-2 processing  
  > "Further processing of the data products was done with the Starlink Software Package Version 2018A" (2.2 JCMT)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| VLBA integrated flux at 6.7 GHz | 22.2 | 0.5 | mJy | 1 | The integrated flux at $\SI{6.7}{GHz}$ is $\SI{22.2(5)}{mJy}$ |
| Overall spectral index | -0.09 | 0.08 | dimensionless | 1 | $\alpha = \num{-0.09(8)}$ |
| Compact core spectral index | 0.18 | 0.10 | dimensionless | 1 | $\alpha_{\rm compact} = \num{0.18(10)}$ |
| Black hole mass (ADAF fit) | 2.2 | +1.2/-0.7 | 1e8 Msun | 3 | $M$ & $2.2^{+1.2}_{-0.7}$ |
| Accretion rate | 5.2e-2 | +4/-2 (e-2) | Msun/yr | 3 | $\dot M$ & $5.2^{+4}_{-2}$ |
| Jet age | 1.7 | +0.8/-0.3 | kyr | 4 | we derive an age of $1.7^{+0.8}_{-0.3}\si{kyr}$ |
| Variability period | 2.5 | 0.3 | yr | 4 | period $T=\SI{2.5(3)}{yr}$ |

## Qualitative findings

- Core-jet structure with jets in plane of sky and orthogonal to cavities.  
  > "We find a compact core and two small jets aligned almost in the plane of the sky, and in the orthogonal direction to the location of cavities." (abstract)

## Claim tuples

- H: Does the SED reflect jets plus ADAF accretion? | E: Fit CI plus ADAF model to 0.24-670 GHz SED | R: chi2_red about 5, M and Mdot consistent with independent values | F: ADAF describes high-frequency emission | **supported**
- H: Are the jets young? | E: Break-frequency age with equipartition B | R: age about 1.7 kyr | F: New feedback cycle started | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Precession, bent jets and binary black hole considered for jet-cavity misalignment; all deemed unlikely  
  > "However, all these possibilities seem unlikely based on the current data." (Summary)
- How they decided it was enough: _not stated_
- Limitation (authors): Poor sampling of 10-100 GHz and limited variability data  
  > "However, we emphasize that the current data is not sufficient to describe the temporal flux variation of the source completely." (3.3 Variability)
- Caveat (inferred, ours): ALMA fluxes are not documented in this paper
- Caveat (inferred, ours): chi2_red about 5 shows imperfect fit
- Caveat (inferred, ours): Non-simultaneous multi-epoch SED despite variability

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: ALMA continuum extraction details
- Missing: MCMC code and priors
- Data volume (inferred): Large for VLBA; ALMA portion small
- Score (inferred): 3/5, ALMA is minor and details are unstated, though VLBA and ATCA recipes are given.
- Rediscovery candidate: no, ALMA role is minor and key fit setup is unstated.

## Links

- Companion: (cite: Schellenberger2020-vl) (Earlier ALMA study of NGC 5044 CO and continuum)
- Related: VLASS
- Related: CARMA cf0076

## Checks

```json
{
 "quotes": 49,
 "quotes_ok": 49,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 0,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2016.1.00533.S",
  "2016.2.00134.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 72,
  "stated": 35,
  "rate": 0.486
 },
 "evidence_ok": true
}
```
