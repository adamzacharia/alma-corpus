# Evidence for the start of planet formation in a young circumstellar disk

`2018NatAs...2..646H` | Nature Astronomy 2018 | first author: Harsono, Daniel | arXiv: 1806.09649 | DOI: 10.1038/s41550-018-0497-x

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks, star_formation
- Question: Why are 13CO and C18O emission missing inside ~15 au of the young TMC1A disk, and does this indicate mm-size grain growth in a massive young disk?  
  > "we report observations on a lack of emission of carbon monoxide isotopologues within the inner $\sim$15 au of a very young (age $\sim$100,000 years) disk around the Solar-type protostar TMC1A." (abstract)
- Target **TMC1A (IRAS 04365+2535)**: coordinates _not stated_; z/distance 140 pc  
  > "corresponding to a spatial scale of 8.4 au $\times$ 7.0 au when adopting a distance of 140 parsecs to the Taurus Molecular Cloud." (main text); distance from adopted distance to the Taurus Molecular Cloud  
  > "corresponding to a spatial scale of 8.4 au $\times$ 7.0 au when adopting a distance of 140 parsecs to the Taurus Molecular Cloud." (main text)

## Data provenance

- ALMA projects: 2015.1.01415.S
- bands: 1.3 mm continuum (225 GHz)  
  > "The dust continuum is observed at 225 GHz (1.33 mm)" (Thermal dust emission.)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.06'' x 0.05'' (PA=25 deg), 8.4 x 7.0 au  
  > "angular resolution of 0.06$'' \times$ 0.05$''$(PA=$25^{\circ}$)" (main text)
- max recoverable scale: _not stated_
- sensitivity: continuum 45 uJy/beam; line 2.1, 2.3, 1.7 mJy/beam per 0.35 km/s channel (12CO, 13CO, C18O)  
  > "The image noise level is 45 $\mu$Jy beam$^{-1}$." (Thermal dust emission.)
- time on source: _not stated_
- observing dates: 2015 Oct 16 (EB1), Oct 23 (EB2), Oct 30 (EB3)  
  > "TMC1A was observed with ALMA on three different dates: October 16 2015 (Execution Block 1; EB1), October 23 2015 (EB2) and October 30 2015 (EB3)." (Observations and calibration.)
- pi or archival as stated: _not stated_
- Line: 12CO 2-1 (230.538 GHz)
- Line: 13CO 2-1 (220.399 GHz)
- Line: C18O 2-1 (219.560 GHz)
- External data: Ossenkopf & Henning dust opacity, 0.0085 cm2/g at 1.3 mm  
  > "similar to a $\kappa_{\nu}$ value of 0.0085 cm$^{2}$ g$^{-1}$ at 1.3 mm from Ossenkopf & Henning" (Thermal dust emission.) [from Ossenkopf & Henning 1994 (ref: OH94)]
- External data: Optical constants for dust  
  > "Optical constants were taken from Weingartner & Draine and Draine." (Dust mass absorption coefficients and properties.) [from Weingartner & Draine; Draine]
- Simulation/model as data: Hyperion dust radiative transfer plus escape-probability line radiative transfer models (fiducial 1e-2 Msun small-grain, massive, large-grain, flared, flat variants) compared to observed CO emission  
  > "Our fiducial disk model has a mass of $10^{-2}$ $M_{\rm Sun}$ and uses small grain dust opacities" (Molecular emission.)

## Processing

### Calibration

- pipeline or manual: Re-calibration with 12 s phase solutions, manual flux calibrator checks, non-standard WVR scaling  
  > "The flux calibrators were manually checked for consistency between execution blocks." (Observations and calibration.)
- casa version: CASA v4.7.2  
  > "The entire data set (all three EBs) were re-calibrated with CASA v4.7.2." (Observations and calibration.)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: Phase self-cal on continuum, 5 min first then down to 20 s  
  > "allowing us to perform self-calibration on the target down to a 20s timescale." (Observations and calibration.)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: superuniform vs Briggs 1 compared for free-free check  
  > "By comparing the images obtained from applying different weightings (superuniform versus Briggs weighting of 1)" (Thermal dust emission.)
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
- final beam: 0.06'' x 0.05'', PA = 25 deg  
  > "the resulting synthesized beam ($0.06'' \times 0.05''$,\ PA = $25^{\circ}$)" (Thermal dust emission.)
- final rms: 45 uJy/beam continuum  
  > "The image noise level is 45 $\mu$Jy beam$^{-1}$." (Thermal dust emission.)

### Inherited from earlier work

- Imaging details  
  > "We refer to Bjerkeli et al. for imaging details." (Observations and calibration.) [from Bjerkeli et al. 2016 (ref: bjerkeli2016)]
- Flat thin disk model  
  > "we also generated a flat, thin disk model following Murillo et al. and a density profile" (Molecular emission.) [from Murillo et al.]
- Small grain size range  
  > "the sizes are between 0.01 – 1 microns following Andrews et al.." (Dust mass absorption coefficients and properties.) [from Andrews et al.]

### Not stated but needed to reproduce (our reading)

- Briggs robust, cell and image size, deconvolver, masks
- Continuum-subtraction channels
- Reference antenna/flux calibrator names and flux scale
- Self-calibration solution intervals and iteration details
- emcee priors, walkers and likelihood
- Radiative transfer grid and full model parameters (R0, Sigma0, T0)
- Line radiative transfer code not public

## Analysis recipe

1. **Re-calibrate and self-calibrate**: CASA re-calibration of all three EBs, 12 s phase solutions, WVR scaling, phase self-cal  
  > "Instead of using the observed integration time (3s) to obtain the phase solutions, we opted to use 12s" (Observations and calibration.)
   - software: CASA
   - fitting: _not stated_
   - validation: noise improved by factors four and two for continuum and CO relative to earlier maps  
  > "The resulting noise levels amount to an improvement of a factor four and two relative to the previously presented continuum image and CO maps, respectively." (Observations and calibration.)
2. **Dust mass from continuum**: Optically thin mass formula with assumed Td and kappa  
  > "Under the assumption of optically thin dust thermal emission, the total mass is given by" (Thermal dust emission.)
   - parameter: Td 30-80 K; kappa = 0.01 (nu/230GHz) cm2/g  
  > "using dust temperatures in the 30 to 80 K range" (Thermal dust emission.)
   - assumption: gas-to-dust ratio 100  
  > "corrected for a standard gas-to-dust mass ratio (100)" (Thermal dust emission.)
   - fitting: _not stated_
   - validation: free-free at most 3 mJy  
  > "at most, a flux of 3 mJy can be attributed to free-free emission" (Thermal dust emission.)
3. **Gas mass from C18O and kinematics**: Moment maps (>3 sigma, 2-11 km/s), optically thin C18O mass, Keplerian iso-velocity contours for stellar mass  
  > "Moment maps were constructed by considering pixels whose intensities $>3\sigma$" (Molecular emission.)
   - parameter: Trot 40-80 K  
  > "a rotational temperature between 40 to 80 K" (Molecular emission.)
   - assumption: CO abundance 1e-4, 16O/18O = 560  
  > "adopting a CO abundance of 10$^{-4}$ with respect to H$_2$, a $^{16}$O/$^{18}$O isotopic ratio of 560" (Molecular emission.)
   - fitting: _not stated_
   - validation: gas mass comparable to dust mass  
  > "These values are roughly comparable to the gas mass derived from the dust continuum flux" (Molecular emission.)
4. **Fit continuum disk structure**: Least squares and MCMC fit of power-law with exponential taper to pixels >5 sigma  
  > "we have fitted the continuum image using Least Square Minimization and a Markov Chain Monte Carlo package (“*emcee*”)." (Molecular emission.)
   - software: emcee
   - fitting: _not stated_
   - validation: visibility fitting consistent  
  > "Visibility fitting using power-law disk structures with different values of $p$ provided disk parameters that are consistent with the above results." (Molecular emission.)
5. **Radiative transfer models of CO suppression**: Hyperion dust temperature plus escape-probability line code; vary disk mass, scale height, opacity (amax 1 mm)  
  > "The Monte Carlo frequency-dependent radiative transfer code, *Hyperion*, was used to derive the temperature structure" (Molecular emission.)
   - software: Hyperion, BHMie
   - parameter: L=2.7 Lsun, Teff=4000 K, p=1, H=0.12 au at 1 au  
  > "A stellar luminosity of 2.7 $L_{\rm Sun}$ and an effective stellar temperature of 4000 K were adopted." (Molecular emission.)
   - assumption: gas temperature equals dust temperature  
  > "The gas temperature is assumed to be perfectly coupled to the dust temperature." (Molecular emission.)
   - fitting: not a best-fit  
  > "Our goal with the radiative transfer modelling is not to provide a best-fit model to the data" (Molecular emission.)
   - validation: _not stated_

## Software

- **CASA** 4.7.2: re-calibration  
  > "re-calibrated with CASA v4.7.2" (Observations and calibration.)
- **emcee** : MCMC continuum fit  
  > "a Markov Chain Monte Carlo package (“*emcee*”)" (Molecular emission.)
- **Hyperion** : dust radiative transfer and opacities  
  > "*Hyperion* is a public Monte Carlo continuum radiative transfer" (Molecular emission.)
- **BHMie** : Mie opacities  
  > "They were calculated using the Bohren and Huffman Mie (“BHMie”) code distributed with *Hyperion*." (Dust mass absorption coefficients and properties.)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Continuum integrated flux density | 145 | 2 | mJy | 2 | integrated flux density of 145$\pm 2$ mJy at 225 GHz inside a $1''$ box |
| Disk inclination | 51 | not stated | deg | 2 | The disk is inclined at 51$^{\circ}$ |
| C18O integrated flux | 1.04 | 0.1 | Jy km/s | 3 | $0.99 \pm 0.2$ Jy km s$^{-1}$ and $1.04 \pm 0.1$ Jy km s$^{-1}$ |
| Protostellar mass | 0.4-0.8 | not stated | Msun | 3 | the protostellar mass is between 0.4–0.8 $M_{\rm Sun}$ |
| Disk mass from dust | 0.012-0.036 | not stated | Msun | 2 | A total disk mass (gas$+$dust) of 0.012–0.036 $M_{\rm Sun}$ |
| Gas mass from C18O | 0.03-0.07 | not stated | Msun | 3 | the C$^{18}$O line gives a derived gas mass of $0.03-0.07 M_{\rm Sun}$ |
| Surface density index p | 0.6 | +0.1/-0.1 | dimensionless | 4 | $p\sim 0.6^{+0.1}_{-0.1}$ and $q\sim 0.6^{+0.1}_{-0.1}$ |

## Qualitative findings

- 13CO and C18O emission is absent within ~15 au while dust is optically thick there  
  > "$^{13}$CO and C$^{18}$O emission is absent within the inner 15 au." (Molecular emission.)

## Claim tuples

- H: Missing CO isotopologue emission inside 15 au is caused by optically thick dust with mm-size grains | E: Radiative transfer models varying mass, opacity, scale height, with checks on photodissociation and temperature inversion | R: Large-grain (amax 1 mm) low-mass disk reproduces suppression; standard grains need >0.2 Msun, which would be gravitationally unstable | F: mm-size grains are present in the inner ~30 au of a ~1e5 yr disk with giant-planet mass reservoir | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Massive disk, flat cold disk, temperature inversion, photodissociation and X-ray destruction were considered and disfavoured  
  > "Therefore, a temperature inversion is unlikely to be responsible for the missing molecular lines." (Molecular emission.)
- How they decided it was enough: _not stated_
- Limitation (authors): Image fitting does not explore full parameter space; mass estimates approximate  
  > "Our image fitting does not fully explore all of the possible parameter space." (Molecular emission.)
- Caveat (inferred, ours): Models are illustrative, not fitted; grain growth inference is non-unique
- Caveat (inferred, ours): Missing short spacings affect line fluxes
- Caveat (inferred, ours): Assumed Td, CO abundance and gas-to-dust ratio drive masses

## Reproducibility

- Data public (paper): Data in ALMA archive  
  > "The datasets generated and/or analysed during the current study are available in the ALMA archive" (Data availability)
- Products in archive: _not stated_
- Code: Hyperion public; line radiative transfer code not public  
  > "The code is not public due to the lack of documentation and its non-trivial usage." (Code availability)
- Missing: Line radiative transfer code
- Missing: Imaging parameters (in Bjerkeli et al. 2016)
- Missing: Model grids and parameters
- Data volume (inferred): ~50-100 GB raw for three EBs
- Score (inferred): 3/5, Public data and clear mass estimates, but imaging details deferred and key line RT code is private.
- Rediscovery candidate: no, Main conclusion relies on a non-public radiative transfer code and qualitative model comparison.

## Links

- Method: Bjerkeli et al. 2016 (ref: bjerkeli2016) (imaging details and earlier data analysis)
- Method: Bruderer et al. 2012 (ref: bruderer12) (line radiative transfer code)
- Method: Robitaille 2011 (ref: hyperion) (Hyperion)
- Companion: Bjerkeli et al. 2016 (ref: bjerkeli2016) (earlier 12CO disk wind analysis of same data)

## Checks

```json
{
 "quotes": 57,
 "quotes_ok": 57,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 78,
  "stated": 44,
  "rate": 0.564
 },
 "evidence_ok": true
}
```
