# The ortho-to-para ratio of H<SUB>2</SUB>Cl<SUP>+</SUP>: Quasi-classical trajectory calculations and new simulations in light of new observations

`2017A&A...608A..96L` | Astronomy and Astrophysics 2017 | first author: Le Gal, R. | arXiv: 1708.08980 | DOI: 10.1051/0004-6361/201731566

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: astrochemistry, milky_way_ism
- Question: What is the ortho-to-para ratio of H2Cl+ in the z=0.89 absorber toward PKS 1830-211, and which formation mechanism (H-abstraction vs full scrambling) explains it?  
  > "In both sightlines, we measured an OPR consistent with a 3:1 ratio." (Summary and conclusions)
- Target **PKS 1830-211 (z=0.89 absorber, SW and NE lines of sight)**: coordinates _not stated_; z/distance z_abs = 0.88582  
  > "Sky frequencies are given assuming a redshift $z_{abs}=0.88582$, heliocentric frame." (Table 1); distance from _not stated_

## Data provenance

- ALMA projects: 2013.1.00020.S
- bands: Band 3 (ortho, ~100 GHz sky) and Band 6 (para, ~257 GHz sky)  
  > "redshifted to $\sim 100$ GHz, within ALMA Band 3) and the $1_{11}$-$0_{00}$ transitions of para- (rest frequencies $\sim 485$ GHz, redshifted to $\sim 257$ GHz, within ALMA Band 6)" (3.1 Description of the observations)
- frequencies and spectral setup: 1.875 GHz spectral windows; 1.3 km/s (Band 6) and 2.9 km/s (Band 3) after Hanning smoothing  
  > "The correlator was set up with spectral windows of 1.875 GHz, providing a velocity resolution of 1.3 km s$^{-1}$ (Band 6) and 2.9 km s$^{-1}$ (Band 3), after Hanning smoothing." (3.1 Description of the observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: better than 0.5 arcsec  
  > "The array was maintained in a configuration providing a synthesized beam resolution of better than 0.5$''$" (3.1 Description of the observations)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: Ortho: 2014 Jul 21 and Aug 26; para: 2014 Jun 06 and Jul 29  
  > "2014, Jul. 21 and Aug. 26" (Table 1)
- pi or archival as stated: _not stated_
- Line: ortho-H2Cl+ 1_10-1_01 (189.225 GHz)
- Line: para-H2Cl+ 1_11-0_00 (485.418 GHz)
- External data: Cosmic-ray ionization rates for SW (3e-14 s-1) and NE (5e-15 s-1) used in models  
  > "we set equal to the values estimated by (cite: muller2016a)" (4.1 Model description) [from (cite: muller2016a)]
- External data: Diffuse ISM gas-phase elemental abundances  
  > "typical diffuse ISM gas-phase elemental abundances relative to total hydrogen (cite: gerin2016)" (4.1 Model description) [from (cite: gerin2016)]

## Processing

### Calibration

- pipeline or manual: CASA, standard procedure  
  > "The data calibration was performed within CASA[^1] following a standard procedure." (3.1 Description of the observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: One run of self-calibration on the bright continuum of PKS 1830-211  
  > "A further run of self-calibration using the bright continuum of PKS 1830$-$211 helped us to significantly improve the data quality." (3.1 Description of the observations)

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

- Nuclear-spin network and QCT zero-point-energy treatment taken from earlier NH2 work  
  > "We enlarged the nuclear spin chemical network used in (cite: legal2016)" (4.1 Model description) [from (cite: legal2016)]

### Not stated but needed to reproduce (our reading)

- CASA version
- Line-free channels and continuum handling
- Self-calibration solution intervals
- Starting model, priors and fit method for the Gaussian velocity components
- Number of ALMA data sets/executions used
- Which model Av and density were adopted

## Analysis recipe

1. **Extract spectra toward both lensed images**: Fit a two-point-source model to visibilities  
  > "by fitting a model of two point sources to the interferometric visibilities" (3.1 Description of the observations)
   - software: CASA, UVMULTIFIT
   - fitting: _not stated_
   - validation: _not stated_
2. **Fit OPR from simultaneous ortho/para absorption**: Simultaneous fit with five Gaussian components (four SW, one NE) with OPR free  
  > "We perform a simultaneous fit of the ortho- and para- absorption profile with five Gaussian velocity components (four for the SW line-of-sight and one for the NE one), with the OPR as a free parameter of the fit." (3.3 Observed absorption spectra)
   - fitting: _not stated_
   - validation: _not stated_
3. **Chemical modeling of OPR**: Pseudo-time-dependent gas-phase models with nuclear-spin network, grid in density and temperature  
  > "we ran grids of models where the density, $n_\ce{H} = n(\ce{H}) +
2n(\ce{H2})$, varies from $2\ensuremath{{\,\times 10^{2}}}$ to $2\ensuremath{{\,\times 10^{4}}}$  and the gas temperature from 10 to 100 K." (4.2 Modeling results)
   - software: NAUTILUS
   - assumption: One to three magnitudes of visual extinction; dust grain radius 0.1 micron; dust-to-gas 1%  
  > "We adopted a single dust grain radius of 0.1 $\mu$m, satisfying a dust-to-gas mass ratio of 1%." (4.1 Model description)
   - fitting: _not stated_
   - validation: Compared with analytic OPR0 model  
  > "The excellent agreement at steady-state between these two latter models shows that the importance of reaction ([\[reaction6\]](#reaction6)) is negligible." (4.2 Modeling results)
4. **Ab initio PES, fit and QCT**: B3LYP and MP2 searches, F12 coupled cluster refinement, PIP-NN PES fit, QCT trajectories  
  > "A total of 37767 points below 69 kcal/mol relative to the global minimum on the PES were selected and fit using the permutation invariant polynomial-neural network (PIP-NN) method" (5.2 PES fitting)
   - software: Gaussian 09, MOLPRO, VENUS
   - parameter: More than 20000 trajectories per temperature, 20-300 K  
  > "In the QCT calculations, more than 20000 trajectories were calculated at each temperature" (5.3 QCT calculations)
   - fitting: PIP-NN with 90/5/5 train/validation/test split  
  > "the training (90% of the data points), validation (5%), and testing (5%) sets" (5.2 PES fitting)
   - validation: RMSE of averaged PES 23.0 cal/mol; geometries and frequencies compared to ab initio  
  > "The RMSE of the averaged PIP-NN PES is 23.0 cal/mol" (5.2 PES fitting)

## Software

- **CASA** : Calibration and self-calibration  
  > "The data calibration was performed within CASA[^1] following a standard procedure." (3.1 Description of the observations)
- **UVMULTIFIT** : Spectra extraction by fitting point sources to visibilities  
  > "using the CASA-python task UVMULTIFIT (cite: marti-vidal2014)" (3.1 Description of the observations)
- **NAUTILUS** : Gas-phase pseudo-time-dependent chemical simulations  
  > "we coupled our network to the NAUTILUS code (cite: ruaud2016), used in the gas-phase mode" (4.1 Model description)
- **Gaussian 09** Revision B.01: Ab initio calculations  
  > "All calculations were carried out by Gaussian 09 software (cite: gaussian09)." (5.1 Ab initio calculations)
- **MOLPRO** 2015.1: F12b coupled-cluster recalculation  
  > "as implemented in MOLPRO (cite: MOLPRO_brief)" (5.1 Ab initio calculations)
- **VENUS** : QCT calculations  
  > "QCT calculations in this work were implemented in VENUS (cite: hu1991)." (5.3 QCT calculations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| OPR of H2Cl+ SW line of sight | 3.15 | 0.13 | dimensionless | 2 | We obtained $\rm OPR_{\rm SW} = 3.15 \pm 0.13$ and $\rm OPR_{\rm NE} =
3.1 \pm 0.5$, respectively. |
| OPR of H2Cl+ NE line of sight | 3.1 | 0.5 | dimensionless | 2 | We obtained $\rm OPR_{\rm SW} = 3.15 \pm 0.13$ and $\rm OPR_{\rm NE} =
3.1 \pm 0.5$, respectively. |
| H-exchange to H-abstraction ratio at 20 K | 0.85% | not stated | percent | 4 | at the lowest temperature studied, 20 K, the ratio between the H-exchange and H-abstraction channels is still small (0.85%) |
| Barrier for H + H2Cl+ interconversion (TS3) | 14.547 kcal/mol (7320 K) | not stated | kcal/mol | 4 | involves a very high energy barrier of 14.547 kcal/mol (7320 K) |

## Qualitative findings

- The H-abstraction mechanism dominates and thermalization by H is blocked by a high barrier, so a 3:1 OPR is retained.  
  > "the reaction proceeds overwhelmingly by an H-abstraction mechanism, which leads to a 3:1 OPR" (5.3 QCT calculations)

## Claim tuples

- H: H2Cl+ OPR in the absorber is consistent with 3:1 in both sightlines | E: Simultaneous Gaussian fit of ALMA ortho and para absorption | R: OPR_SW=3.15±0.13, OPR_NE=3.1±0.5 | F: Consistent with 3:1 | **supported**
- H: H2 + HCl+ forms H2Cl+ via H-abstraction rather than scrambling | E: PES with QCT trajectories at 20-300 K | R: H-exchange is a tiny fraction of trajectories | F: Abstraction dominates giving 3:1 | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Full scrambling excluded: it cannot give 3:1 even at 80 K.  
  > "Thus we clearly see that an OPR of 3:1, even at a temperature as high as 80 K, is excluded with the consideration of a full scrambling mechanism." (4.2 Modeling results)
- How they decided it was enough: _not stated_
- Limitation (authors): A more efficient thermalization route may be missed.  
  > "it is possible that there is another and more efficient direction to thermal equilibrium, which we are missing, but it is, in our view, unlikely." (4.2 Modeling results)
- Caveat (inferred, ours): Observational fit details (priors, components) are not given
- Caveat (inferred, ours): Calculated reaction energy about 3 kcal/mol below JANAF value
- Caveat (inferred, ours): Uses constant-physical-condition models only

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: CASA version and calibration scripts
- Missing: Fit method and parameters for Gaussian components
- Missing: Model network files and grid details
- Data volume (inferred): tens of GB
- Score (inferred): 3/5, The ALMA part is brief; the theory part has well-specified methods but no released code.
- Rediscovery candidate: no, The ALMA data processing recipe is incomplete and the main results involve custom theory calculations.

## Links

- Method: (cite: marti-vidal2014) (UVMULTIFIT)
- Method: (cite: oka2004) (nuclear-spin selection theory)
- Companion: (cite: muller2014b) (Earlier para-H2Cl+ detection in the same absorber)
- Companion: (cite: legal2016) (Prior NH2 OPR work with the same methods)

## Checks

```json
{
 "quotes": 39,
 "quotes_ok": 39,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 4,
 "numeric_problems": 0,
 "fill": {
  "facts": 69,
  "stated": 29,
  "rate": 0.42
 },
 "evidence_ok": true
}
```
