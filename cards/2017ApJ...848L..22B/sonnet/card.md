# The Electromagnetic Counterpart of the Binary Neutron Star Merger LIGO/Virgo GW170817. VII. Properties of the Host Galaxy and Constraints on the Merger Timescale

`2017ApJ...848L..22B` | The Astrophysical Journal Letters 2017 | first author: Blanchard, P. K. | arXiv: 1710.05458 | DOI: 10.3847/2041-8213/aa9055

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: nearby_galaxies, transients, agn_and_quasars
- Question: What are the properties of NGC 4993, the host galaxy of GW170817, and what do its star formation history and the counterpart's location imply for the BNS merger timescale, initial separation and natal kick?  
  > "we use our follow-up observations and archival data of NGC 4993 to measure the precise location of the BNS system at the time of merger and to infer the physical properties of the host" (Introduction)
- Target **NGC 4993 (host of GW170817)**: coordinates _not stated_; z/distance d ≈ 39.5 Mpc  
  > "associated with the galaxy NGC 4993 at a distance of $d\approx 39.5$ Mpc" (Introduction); distance from cited DECam discovery papers (DECAMgcn; DECamPaper1)  
  > "associated with the galaxy NGC 4993 at a distance of $d\approx 39.5$ Mpc" (Introduction)

## Data provenance

- ALMA projects: _none stated_
- bands: _not stated_
- frequencies and spectral setup: ALMA host flux density at 97.5 GHz (Table 1)  
  > "|    ALMA    |  97.5 GHz  |       210 (20)        |" (Table 1)
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
- Other facility **HST (ACS, WFC3)**: Imaging of counterpart and host for offset, Sérsic fitting, and archival pre-merger limit  
  > "We also retrieved and analyzed an archival observation of NGC 4993 from 2017 April 28 using ACS/WFC with the F606W filter" (2.1 Hubble Space Telescope (HST) Observations)
- Other facility **VLA**: Radio host flux densities (6-15 GHz)  
  > "|    VLA     |  6.0 GHz   |       330 (20)        |" (Table 1)
- Other facility **Chandra**: Host X-ray flux, 2-10 keV  
  > "| *Chandra*  | $2-10$ keV | $1.7 \times 10^{-14}$ |" (Table 1)
- Other facility **SOAR/Goodman**: Optical spectrum of host  
  > "Observations were carried out with the 400 l/mm grating and 1” slit (R$\sim$830" (2.4 Optical Spectra)
- Other facility **Pan-STARRS1, GALEX, 2MASS, WISE**: Archival UV-IR photometry for SED  
  > "including UV and IR photometry from the *GALEX*, 2MASS, and *WISE* catalogs via the NASA/IPAC Extragalactic Database" (2.2 Additional Archival Data)
- External data: Radio and X-ray observations of GW170817 (ALMA, VLA, Chandra)  
  > "As described in (cite: DECamPaper5) and (cite: DECamPaper6), we obtained radio and X-ray observations of GW170817" (Radio and X-Ray Observations: An Active Galactic Nucleus (AGN) Origin) [from (cite: DECamPaper5); (cite: DECamPaper6)]
- External data: Simulated BNS population initial separations and eccentricities  
  > "the simulated population of BNS systems from (cite: Dominik2012) using their standard model (sub-model A) with solar metallicity" (7 BNS Merger Timescale, Initial Separation, and Kick Velocity) [from (cite: Dominik2012)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
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
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- HST data analysis  
  > "The data analysis is described in (cite: DECamPaper2)." (2.1 Hubble Space Telescope (HST) Observations) [from (cite: DECamPaper2)]
- ALMA/VLA/Chandra observations and reduction  
  > "As described in (cite: DECamPaper5) and (cite: DECamPaper6), we obtained radio and X-ray observations" (Radio and X-Ray Observations: An Active Galactic Nucleus (AGN) Origin) [from (cite: DECamPaper5); (cite: DECamPaper6)]
- SOAR spectroscopy details  
  > "see (cite: DECamPaper3) for details" (2.4 Optical Spectra) [from (cite: DECamPaper3)]

### Not stated but needed to reproduce (our reading)

- ALMA project codes, band, array configuration, calibration and imaging for the 97.5 GHz flux
- How the 210 uJy ALMA flux was measured
- Prospector priors and MCMC settings
- alf fit settings
- Counterpart-subtracted host flux handling in radio data

## Analysis recipe

1. **Host morphology and counterpart offset**: GALFIT Sérsic fit of HST images; SExtractor centroids for offsets; fractional flux from pixel histogram  
  > "We used GALFIT v3.0.5 (cite: phi+10) to fit the 2D surface brightness profile of NGC 4993 with a standard Sérsic function" (3 Morphological Properties of NGC 4993)
   - software: GALFIT, SExtractor, IRAF
   - parameter: DEBLEND MINCONT = 0.0005  
  > "setting `DEBLEND MINCONT` = 0.0005 to detect the optical counterpart against the high background emission from the galaxy" (4.1 Offset)
   - fitting: _not stated_
   - validation: Compared with IRAF ellipse isophote fitting  
  > "we also used the `ellipse` task in IRAF to fit isophotes to the galaxy images" (3 Morphological Properties of NGC 4993)
2. **SED and spectral modelling for star formation history**: Prospector-alpha SED fit; alf fit of SOAR spectrum  
  > "Prospector-$\alpha$ uses a Bayesian Markov Chain Monte Carlo (MCMC) approach to modeling galaxy SEDs." (5 Host Galaxy SED and Spectral Modeling)
   - software: Prospector, alf, CLOUDY
   - assumption: Chabrier IMF  
  > "assume a Chabrier initial mass function" (5 Host Galaxy SED and Spectral Modeling)
   - fitting: MCMC; six-component non-parametric SFH  
  > "the model fits a six-component non-parametric star formation history (SFH)" (5 Host Galaxy SED and Spectral Modeling)
   - validation: Spectral age consistent with SED age  
  > "the age inferred here is consistent with the SED modeling results" (5 Host Galaxy SED and Spectral Modeling)
3. **Merger timescale, separation and kick**: Cumulative stellar mass build-up taken as merger-time distribution; Peters (1964) converts to a0 vs e0; velocity dispersion gives kick limit  
  > "The cumulative stellar mass build-up history, shown in Figure [2](#SED), can therefore be interpreted as the integral of the merger timescale probability distribution." (7 BNS Merger Timescale, Initial Separation, and Kick Velocity)
   - assumption: Equal merger times probable; NS masses 1.4 Msun  
  > "this interpretation makes the assumption that all merger times are equally probable" (7 BNS Merger Timescale, Initial Separation, and Kick Velocity)
   - fitting: _not stated_
   - validation: Repeated with tau^-1 DTD, median 10.3 Gyr  
  > "which results in a median merger time of $10.3^{+1.1}_{-0.8}$ Gyr" (7 BNS Merger Timescale, Initial Separation, and Kick Velocity)

## Software

- **GALFIT** v3.0.5: Sérsic fits to HST images  
  > "We used GALFIT v3.0.5 (cite: phi+10)" (3 Morphological Properties of NGC 4993)
- **SExtractor** : PS1 photometry and offset centroids  
  > "performed photometry using `SExtractor`" (2.2 Additional Archival Data)
- **IRAF** : psf/addstar upper limit, ellipse, spectral reduction  
  > "we use the IRAF/`psf` task to create a point-spread function from the image" (2.1 Hubble Space Telescope (HST) Observations)
- **Prospector-alpha** : SED fitting  
  > "We model the UV to mid-IR SED of NGC 4993 using Prospector-$\alpha$" (5 Host Galaxy SED and Spectral Modeling)
- **alf** : Optical spectrum stellar population fit  
  > "the `alf` stellar population synthesis modeling code" (5 Host Galaxy SED and Spectral Modeling)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| ALMA host flux density at 97.5 GHz | 210 | 20 | uJy | 0 | /    ALMA    /  97.5 GHz  /       210 (20)        / |
| Radio-millimeter spectral index | -0.25 | not stated | dimensionless | 0 | The radio-millimeter spectral index is $\beta\approx -0.25$ |
| Median merger timescale | 11.2 | +0.7/-1.4 | Gyr | 3 | We find a median merger timescale of $11.2^{+0.7}_{-1.4}$ Gyr |
| Projected offset | 2.125 | 0.001 | kpc | 1 | We find a weighted mean offset of $2.125 \pm 0.001$ kpc |
| log stellar mass | 10.65 | +0.03/-0.03 | log Msun | 2 | log($M_{*}/M_{\Sun}$)                        / $10.65^{+0.03}_{-0.03}$ |
| Kick velocity upper limit | 200 | not stated | km/s | 3 | which yields $v_{kick} \lesssim 200$ km s$^{-1}$ |

## Qualitative findings

- Radio and X-ray emission indicate a low-luminosity AGN in NGC 4993  
  > "Thus, the radio and X-ray emission point to the presence of a low-luminosity AGN." (Radio and X-Ray Observations: An Active Galactic Nucleus (AGN) Origin)

## Claim tuples

- H: Does the host's old stellar population imply a long BNS merger delay? | E: Prospector-alpha SFH converted to a merger time distribution | R: Median 11.2 Gyr, 90% range 6.8-13.6 Gyr | F: Long delay time; initial separation about 4.5 Rsun for low eccentricity | **supported**
- H: Was the radio/mm/X-ray emission from star formation or an AGN? | E: Compared radio/X-ray inferred SFRs with SED SFR and spectral index | R: SFRs are 1 and 0.1 Msun/yr versus 0.01 from SED; beta ≈ -0.25 | F: Low-luminosity AGN | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Globular cluster origin: pre-merger limit rules out the brighter half of the GCLF but not a definitive exclusion  
  > "Thus, the archival limit rules out the brighter half of the GCLF." (7 BNS Merger Timescale, Initial Separation, and Kick Velocity)
- How they decided it was enough: _not stated_
- Limitation (authors): Merger-time interpretation assumes equal probability of all merger times  
  > "this interpretation makes the assumption that all merger times are equally probable" (7 BNS Merger Timescale, Initial Separation, and Kick Velocity)
- Caveat (inferred, ours): ALMA data provenance is entirely deferred to companion papers
- Caveat (inferred, ours): Only projected offset is measured
- Caveat (inferred, ours): Nominal 1.4 Msun masses assumed

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: ALMA observation details and project codes
- Missing: Prospector priors and MCMC settings
- Missing: Reduced HST images
- Data volume (inferred): small (<10 GB for the ALMA part; the HST and photometry work is mostly archival)
- Score (inferred): 2/5, ALMA is a minor supporting flux; the paper defers its processing to companion papers.
- Rediscovery candidate: no, The ALMA part is a single flux density with no recipe given, and the main results come from non-ALMA SED modelling.

## Links

- Method: (cite: Leja2017a) (Prospector-alpha SED model)
- Companion: (cite: DECamPaper5) (Radio, X-ray and ALMA observations)
- Companion: (cite: DECamPaper6) (Radio and X-ray observations)
- Companion: (cite: DECamPaper2) (HST observations and analysis)
- Related: Pan-STARRS1 3pi

## Checks

```json
{
 "quotes": 41,
 "quotes_ok": 41,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 0,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2016.A.00043.T",
  "2016.A.00046.T"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 73,
  "stated": 32,
  "rate": 0.438
 },
 "evidence_ok": true
}
```
