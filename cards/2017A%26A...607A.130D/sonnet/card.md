# The Flying Saucer: Tomography of the thermal and density gas structure of an edge-on protoplanetary disk

`2017A&A...607A.130D` | Astronomy and Astrophysics 2017 | first author: Dutrey, A. | arXiv: 1706.02608 | DOI: 10.1051/0004-6361/201730645

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks
- Question: Can the radial and vertical gas temperature and density structure of an edge-on disk be determined directly by a tomographic analysis of CO and CS position-velocity diagrams?  
  > "We attempt a direct determination of the radial and vertical temperature structure of the Flying Saucer disk, thanks to its favorable inclination of 90 degrees." (abstract)
- Target **Flying Saucer (edge-on disk in rho Oph L 1688)**: coordinates not stated (l=353.3, b=16.5)  
  > "which is about 260 au for the adopted distance of 120 pc (cite: Loinard+etal_2008)" (1 Introduction); z/distance 120 pc  
  > "which is about 260 au for the adopted distance of 120 pc (cite: Loinard+etal_2008)" (1 Introduction); distance from Loinard et al. 2008  
  > "which is about 260 au for the adopted distance of 120 pc (cite: Loinard+etal_2008)" (1 Introduction)

## Data provenance

- ALMA projects: 2013.1.00387.S
- bands: CO J=2-1 and CS J=5-4 near 242 GHz continuum (Band 6)  
  > "The total continuum flux is 35 mJy at 242 GHz (with about 7% calibration uncertainty)." (Observations)
- frequencies and spectral setup: 15 kHz channel spacing (40 m/s effective resolution); CO 2-1, CN 2-1 hyperfines and CS 5-4 observed simultaneously  
  > "The correlator was configured to deliver very high spectral resolution with a channel spacing of 15 kHz (and an effective velocity resolution of 40 m s${-1}$)." (Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: moderately compact configuration, ~34 antennas  
  > "Imaging observations were performed with the Atacama Large mm/submm Array (ALMA) in a moderately compact configuration." (Observations)
- baselines: _not stated_
- angular resolution: ~0.5'' (CS 0.48''x0.46'' PA 53; CO 0.51''x0.48'' PA 54)  
  > "the rms noise is 4 mJy/beam, i.e. about 0.37 K given the beam size of $0.51'' \times 0.48''$ at PA $54^\circ$." (Observations)
- max recoverable scale: _not stated_
- sensitivity: CS rms 3 mJy/beam (0.27 K) at 0.1 km/s; CO rms 4 mJy/beam (0.37 K) at 0.08 km/s  
  > "the rms noise is 3 mJy/beam, i.e. about 0.27 K given the beam size of $0.48'' \times 0.46''$ at PA $53^\circ$." (Observations)
- time on source: _not stated_
- observing dates: 17 and 18 May 2015  
  > "The project 2013.1.00387.S was observed on 17 and 18 May 2015 under excellent weather conditions." (Observations)
- pi or archival as stated: _not stated_
- Line: CO J=2-1 (not stated)
- Line: CS J=5-4 (not stated)
- Other facility **IRAM 30-m**: CO J=2-1 spectrum of the background clouds, used to correct the CO PV diagram  
  > "In addition, a CO J=2-1 spectrum of the clouds along the line of sight was obtained with the IRAM 30-m telescope" (Observations)
- External data: Continuum disk model parameters (Table 1) used for the continuum in CO models; dust scale height 12.7 au at 100 au  
  > "The continuum model uses, in particular for the density and temperature, the parameters defined in Table 1 of (cite: Guilloteau+etal_2016a)." (5 CO Modeling using DiskFit) [from (cite: Guilloteau+etal_2016a)]
- External data: IRAM 30-m background CO spectrum  
  > "by adding the background spectrum obtained with the IRAM 30m, (cite: Guilloteau+etal_2016a) to the observed CO emission" (3.3 PV-diagrams) [from (cite: Guilloteau+etal_2016a)]

## Processing

### Calibration

- pipeline or manual: standard ALMA calibration script in CASA  
  > "Data was calibrated via the standard ALMA calibration script in the CASA software package (Version 4.2.2)." (Observations)
- casa version: CASA 4.2.2  
  > "Data was calibrated via the standard ALMA calibration script in the CASA software package (Version 4.2.2)." (Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Titan  
  > "Titan was used as a flux calibrator." (Observations)
- flux scale uncertainty: about 7%  
  > "The total continuum flux is 35 mJy at 242 GHz (with about 7% calibration uncertainty)." (Observations)
- self calibration: _not stated_

### Imaging

- task: cvel regrid to LSR, export via UVFITS to GILDAS for imaging  
  > "The calibrated data was regridded in velocity to the LSR frame using the “cvel” task, and exported through UVFITS format to the GILDAS package for imaging and data analysis." (Observations)
- deconvolver: _not stated_
- weighting robust: robust weighting (value not given)  
  > "With robust weighting, the $uv$ coverage provided by the $\sim 34$ antennas yields a nearly circular beam size close to 0.5$''$." (Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: TRD derived from cubes without continuum subtraction  
  > "The derivations were performed onto data cubes without continuum subtraction" (4.1 Deriving the brightness distribution from the PV-diagram)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: CS 0.48''x0.46'' PA 53; CO 0.51''x0.48'' PA 54  
  > "the rms noise is 4 mJy/beam, i.e. about 0.37 K given the beam size of $0.51'' \times 0.48''$ at PA $54^\circ$." (Observations)
- final rms: CS 3 mJy/beam; CO 4 mJy/beam  
  > "the rms noise is 3 mJy/beam, i.e. about 0.27 K given the beam size of $0.48'' \times 0.46''$ at PA $53^\circ$." (Observations)

### Inherited from earlier work

- Background-cloud CO spectrum and continuum/dust modelling taken from earlier paper  
  > "The CO J=2-1 and continuum results were partially reported by (cite: Guilloteau+etal_2016a), who used them to measure the dust temperature." (3 Results) [from (cite: Guilloteau+etal_2016a)]
- DiskFit ray-tracing model  
  > "we make a simple model of the CS J=5-4 emission with DiskFit (cite: Pietu+etal_2007)" (3.2 Simple determination of the disk parameters) [from (cite: Pietu+etal_2007)]
- H2 density prescription (exponentially tapered)  
  > "we assume either power laws or exponentially tapered distribution following the prescription given in (cite: Guilloteau+etal_2011)." (5 CO Modeling using DiskFit) [from (cite: Guilloteau+etal_2011)]

### Not stated but needed to reproduce (our reading)

- robust value, uv range, cell and image size for GILDAS imaging
- how the IRAM 30-m spectrum was scaled/added to the CO PV diagram
- PV cut width and altitudes used
- fit procedure for DiskFit (minimizer, priors) and grid ranges
- DiskFit and TRD code availability
- continuum model values from Guilloteau et al. 2016a
- line-free channels

## Analysis recipe

1. **Calibrate and image**: Standard CASA calibration, cvel to LSR, export to GILDAS, imaging with robust weighting  
  > "The calibrated data was regridded in velocity to the LSR frame using the “cvel” task, and exported through UVFITS format to the GILDAS package for imaging and data analysis." (Observations)
   - software: CASA, GILDAS
   - fitting: _not stated_
   - validation: _not stated_
2. **Fit simple CS disk model**: DiskFit with power-law CS surface density and temperature, Gaussian vertical profile, LTE, sharp outer edge  
  > "The line emission is computed assuming a (total) local line width $dV$ independent of the radius and LTE" (3.2 Simple determination of the disk parameters)
   - software: DiskFit
   - assumption: Keplerian rotation  
  > "(a) Assuming Keplerian rotation." (3.2 Simple determination of the disk parameters)
   - fitting: formal errors from the fit; sampler not stated  
  > "Errors are formal errorbars from the fit." (3.2 Simple determination of the disk parameters)
   - validation: _not stated_
3. **Tomographically reconstruct brightness (TRD)**: Average/median brightness along radial lines of constant radius in PV diagrams at several altitudes; add IRAM 30-m background to CO  
  > "we can recover the disk temperature from the thermalized and optically thick CO J=2-1 transition by averaging the observed brightness along such radial lines" (4.1 Deriving the brightness distribution from the PV-diagram)
   - assumption: CO J=2-1 optically thick and thermalized  
  > "we can recover the disk temperature from the thermalized and optically thick CO J=2-1 transition" (4.1 Deriving the brightness distribution from the PV-diagram)
   - fitting: _not stated_
   - validation: CS mean and median differ by <1 K inside the disk at r<350 au  
  > "the mean and the median always give results which differ by less than 1 K inside the disk at $r < 350$ au" (4.1 Deriving the brightness distribution from the PV-diagram)
4. **Model CO with grid of DiskFit models**: Grids with parametrized T(r,z), power-law or tapered H2 density, with/without mid-plane CO depletion; compare TRDs with observations; convolve by 0.5'' beam  
  > "we study here the impact of several key parameters of the disk by performing grids of models to better constrain the disk geometry and structure." (5 CO Modeling using DiskFit)
   - software: DiskFit
   - parameter: r_out = 330 au, i = 87 deg, CO abundance 1e-4 in upper layers, depletion temperature 17 K  
  > "$T_{dep}$ | 17 | K | Depletion temperature" (Table 2)
   - assumption: LTE for CO; distance 120 pc  
  > "For simplicity, we assume LTE conditions, which is appropriate for CO." (5 CO Modeling using DiskFit)
   - fitting: grid exploration, no formal fit  
  > "we study here the impact of several key parameters of the disk by performing grids of models to better constrain the disk geometry and structure." (CO Modeling using DiskFit)
   - validation: Model TRD compared to observed brightness at 0.5'', 0.3'', 0.1''  
  > "The brightness temperature from the model is compared to the observations and also shown in Fig. 8 at three different angular resolutions" (5 CO Modeling using DiskFit)
5. **CS excitation check**: LVG calculation with Tk = 17 K, N = 4e13 cm-2, dV = 0.3 km/s  
  > "A simple LVG calculation using the CO freeze out temperature $T_k = 17$ K" (6.3 Deriving the gas density from CS excitation conditions)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.2.2: calibration and cvel  
  > "Data was calibrated via the standard ALMA calibration script in the CASA software package (Version 4.2.2)." (Observations)
- **GILDAS** : imaging and data analysis  
  > "exported through UVFITS format to the GILDAS package for imaging and data analysis" (Observations)
- **DiskFit** : ray-tracing disk models of CS and CO  
  > "We use the ray-tracing model DiskFit (cite: Pietu+etal_2007)." (5 CO Modeling using DiskFit)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Stellar mass (CS fit) | 0.58 | 0.01 | Msun | 2 | $M_*$ / $0.58 \pm 0.01$ |
| Inclination (CS fit) | 85.4 | 0.5 | deg | 2 | $i$ / $85.4 \pm 0.5$ |
| Systemic velocity | 3.755 | 0.003 | km/s | 2 | $V_\mathrm{LSR}$ / $3.755 \pm 0.003$ |
| CS temperature T0 at 100 au | 18.0 | 0.5 | K | 2 | $T_0$ / $18.0 \pm 0.5$ |
| Mid-plane temperature near 180 au (beam averaged) | 13 | not stated | K | 3 | we safely constrain the mean disk mid-plane temperature, averaged over one beam, to be 13 K near 180 au |
| Best-model mid-plane temperature at 100 au | 10 | not stated | K | 4 | $T_{mid}^0$ / 10 / K / Mid-plane temperature |
| Disk mass (best CO model, X(CO)=1e-4) | 0.7e-3 | not stated | Msun | 4 | $M_\mathrm{disk}$ / $0.7\,10^{-3}$ |
| Radius of emission dip | 185 | not stated | au | 3 | $r_\mathrm{dip} \simeq 185\,\mathrm{au}$ |

## Qualitative findings

- CO traces 1-3 scale heights while CS is around one scale height; CO is seen again in the mid-plane beyond ~200 au.  
  > "CO is also detected up to 3-4 scale heights while CS is confined around 1 scale height above the mid-plane." (abstract)

## Claim tuples

- H: The vertical and radial gas temperature can be measured directly from an edge-on disk silhouetted against CO background | E: TRD from CO PV diagrams plus DiskFit models | R: Vertical gradient seen; mid-plane ~10 K at 100 au, warmer atmosphere | F: Thermal structure consistent with models; limited by 0.5'' resolution | **supported**
- H: CO depletion vs cold mid-plane can be distinguished | E: Models with and without mid-plane depletion | R: Depletion only marginally better | F: Not possible at current resolution | **partially**
- H: Mid-plane CO beyond ~200 au indicates re-heating | E: Radial TRD profile | R: CO brightness rises beyond ~200 au | F: Consistent with higher UV penetration, but a gap at 185 au is not excluded | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Edge-on geometry allows full vertical structure retrieval  
  > "A purely edge-on disk can allow the retrieval of the full vertical structure of the molecules" (1 Introduction)
- Alternative: Constant-abundance CO models fail to reproduce the mid-plane CO depression, even with mid-plane T of 5-7 K  
  > "However none of these models, which assume CO molecules are present everywhere in the disk, properly reproduce the CO depression observed around the mid-plane" (5 CO Modeling using DiskFit)
- How they decided it was enough: _not stated_
- Limitation (authors): Linear resolution of ~56-60 au limits quantitative results; parameters coupled  
  > "Because of this limited angular resolution, parameters $T_{atm}^0,\delta,z_q$ are strongly coupled." (5 CO Modeling using DiskFit)
- Caveat (inferred, ours): Models explored by grid and eye, no formal uncertainties on CO model parameters
- Caveat (inferred, ours): CO background correction relies on 30-m spectrum added assuming optically thick line
- Caveat (inferred, ours): Interpretation of the 185 au dip is ambiguous

## Reproducibility

- Data public (paper): ALMA project 2013.1.00387.S cited; public status not stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2013.1.00387.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: imaging parameters
- Missing: DiskFit code and fit settings
- Missing: IRAM 30-m spectrum
- Missing: TRD extraction details
- Data volume (inferred): ~50-200 GB raw (high spectral resolution, 2 execution blocks)
- Score (inferred): 3/5, Data archival and method clear, but imaging and model fitting details and code are missing.
- Rediscovery candidate: no, Key results rely on DiskFit modelling with unstated settings and the 30-m spectrum.

## Links

- Method: (cite: Pietu+etal_2007) (DiskFit model)
- Companion: (cite: Guilloteau+etal_2016a) (Dust temperature and continuum modelling from the same ALMA data)

## Checks

```json
{
 "quotes": 61,
 "quotes_ok": 61,
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
  "facts": 74,
  "stated": 46,
  "rate": 0.622
 },
 "evidence_ok": true
}
```
