# The Galaxy Activity, Torus, and Outflow Survey (GATOS): VI. Black hole mass estimation using machine learning

`2025A&A...693A.311P` | Astronomy and Astrophysics 2025 | first author: Poitevineau, R. | arXiv: 2411.18200 | DOI: 10.1051/0004-6361/202347566

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type observational_alma_primary

## Science

- Fields: nearby_galaxies, agn_and_quasars
- Question: Can supervised CNNs trained on simulated gas-disk cubes estimate black hole masses from ALMA CO(3-2) position-velocity diagrams or first-moment maps of seven GATOS Seyferts?  
  > "We use the high spatial resolution of ALMA to resolve the CO(3-2) emission within $\sim$100 pc around the supermassive black hole (SMBH) of seven GATOS galaxies and try to estimate their BH mass" (abstract)
- Target **NGC 4388, NGC 5506, NGC 5643, NGC 6300, NGC 7314, NGC 7465, NGC 7582**: coordinates _not stated_; z/distance <28 Mpc  
  > "The core sample is composed of nearby galaxies ($<$28Mpc) and luminous nuclei, $L_{AGN}(14-150\mathrm{keV}) \geq 10^{42}\mathrm{erg/s}$." (2 Sample); distance from _not stated_

## Data provenance

- ALMA projects: _none stated_
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: pixel size 4 to 7 pc depending on galaxy (simulated cubes matched to observed data)  
  > "The pixel size in the data cubes was chosen to match that of the observed data (ranging from 4 to 7 pc, depending on the galaxy), with velocity channels of 10 km/s." (4.2 Numerical simulations)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: CO(3-2) cubes from the GATOS core sample; details given in García-Burillo et al. 2021  
  > "All the details of the GATOS core sample and their observations are given in (cite: garcia-burillo_galaxy_2021)." (2 Sample)
- Line: CO J=3-2 (not stated)
- Other facility **HST (Hubble Legacy Archive)**: WFC3 images for own Galfit decomposition of NGC 5643 and NGC 6300  
  > "except for NGC5643 and NGC6300 where the Galfit decomposition is our own fit from the WCF3 Hubble Legacy Archive image." (Table 1 notes)
- Other facility **Spitzer S4G**: 3.6 micron decomposition for stellar mass components (Salo et al. 2015)  
  > "we use the (cite: salo_spitzer_2015) Galfit (cite: peng2010AJ....139.2097P) decomposition from the Spitzer Survey of Stellar Structure in Galaxies $3.6 \mathrm{\mu m}$ infrared images" (3.1 Dynamical estimation)
- External data: Inclination and position angles of nuclear gas disks  
  > "Inclination and position angles are fixed to the values estimated from the observations (cite: garcia-burillo_galaxy_2021)" (4.1 Supervised learning method) [from (cite: garcia-burillo_galaxy_2021)]
- External data: Stellar velocity dispersions for M-sigma from Hyperleda  
  > "For our sample, it was taken from the Hyperleda compilation (cite: makarov_hyperleda_2014)." (3.2 M-sigma relation) [from (cite: makarov_hyperleda_2014)]
- External data: Literature BH masses (reverberation, M-sigma, FPBH) used for comparison  
  > "Table summarizing the different $M_{\mathrm{BH}}$  estimations found in the literature and the one we made with ML." (Table notes (BH mass estimations table)) [from (cite: peterson_central_2004; bian_eddington_2007; wang_millimeter_2007; beckmann_second_2009; van_den_bosch_unification_2016; she_chandra_2017)]
- Simulation/model as data: 25,000 simulated cubes per galaxy (16,500 train, 3,500 validation, 5,000 test) of gas particles in galaxy+BH potential  
  > "For each observed galaxy, we generated 25,000 simulated data cubes, dividing them into a training set of 16,500 simulations, a validation set of 3,500 simulations, and a test set of 5,000 simulations." (4.1 Supervised learning method)

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

- Simulation model of gas particles in galaxy potential  
  > "To simulate our data cubes, we used the model described in (cite: melchior2011) and (cite: combes_alma_2019)." (4.2 Numerical simulations) [from (cite: melchior2011); (cite: combes_alma_2019)]
- Fitting of models to moment maps and PVDs  
  > "The models are fitted with the same methodology as in (cite: combes_alma_2019)." (6 Individual galaxies) [from (cite: combes_alma_2019)]
- Observations and data reduction of the GATOS core sample  
  > "All the details of the GATOS core sample and their observations are given in (cite: garcia-burillo_galaxy_2021)." (2 Sample) [from (cite: garcia-burillo_galaxy_2021)]

### Not stated but needed to reproduce (our reading)

- ALMA project codes, calibration and imaging details (CASA version, robust, beam, rms) for the cubes
- Which ALMA cubes/products were used and how they were obtained
- Moment-map clipping thresholds and PVD slit width and position angle
- Distances adopted per galaxy
- Parameter ranges for the uniform sampling of simulations (only best-fit values tabulated)
- Random seeds, number of dropout inferences' pre-processing, and the PVD axis choice
- K and details of nearest-neighbour interpolation and chi-squared comparison

## Analysis recipe

1. **Model stellar mass distribution**: Galfit decomposition of S4G 3.6 micron images (own HST fit for NGC 5643, NGC 6300)  
  > "Stellar mass components from the (cite: salo_spitzer_2015) Galfit decomposition from $S^4G$ $3.6\mathrm{\mu m}$" (Table 1 notes)
   - software: Galfit
   - fitting: _not stated_
   - validation: _not stated_
2. **Simulate training cubes**: Gas particle disk (10^6 particles, Toomre Q=1) in galaxy+BH potential, projected with fixed IA/PA, smoothed to beam, normalised by observed moment-0 map; parameters drawn uniformly  
  > "To ensure sufficient statistics, we fixed the number of particles at $10^6$." (4.2 Numerical simulations); "we normalized the model cube pixel by pixel in the 2D projection using the zeroth moment map of the CO observations." (4.2 Numerical simulations)
   - parameter: cube dimensions (250, 250, 60); 10 km/s channels  
  > "resulting in a cube of dimensions (250, 250, 60) for each simulation." (4.2 Numerical simulations)
   - assumption: axisymmetric homogeneous thin gas disk, negligible dark matter, H_gas/R_gas<0.1  
  > "we choose to keep the ratio $H_{\mathrm{gas}}/R_{\mathrm{gas}}<0.1$." (4.2 Numerical simulations)
   - fitting: _not stated_
   - validation: _not stated_
3. **Build CNN inputs**: Compute PVD (symmetrised for observed) and 1st-moment maps per cube; normalise each by maximum pixel  
  > "Finally, moment by moment, and for the PVD, we normalize the value of each pixel by dividing it by the highest one." (4.3 Preparing the inputs)
   - fitting: _not stated_
   - validation: _not stated_
4. **Train one CNN per galaxy and input type**: Keras CNN regression, RMSE loss, Adam lr 1e-4, batch 128, 2000 epochs, best validation epoch, dropout 20% on dense2  
  > "We trained our models during 2000 epochs and took the weights of the epoch with the lowest RMSE on the validation set." (4.4 ML architecture); "The training was made with a mini-batch size of 128 images." (4.4 ML architecture)
   - software: Keras
   - fitting: RMSE loss, Adam optimizer; output normalised by max M_BH  
  > "We used an initial learning rate of 0.0001 and the Adam optimizer (cite: adamopt)." (4.4 ML architecture)
   - validation: RMSE, R^2 and mean relative error on 5000-sample test sets; RE vs each parameter  
  > "The RMSE values are at worst 0.0367 and the $R^2$ are all above 0.946" (5.1 Reliability of ML models)
5. **Infer M_BH from observations**: 10^5 MC-dropout predictions per galaxy give a probability distribution  
  > "We made $10^{5}$ predictions per galaxy. The observed scatter on the $M_{\mathrm{BH}}$ predictions comes from the MC dropout." (5.2 M_BH estimations results)
   - software: Keras
   - fitting: _not stated_
   - validation: Compared with literature M-sigma, reverberation and FPBH masses  
  > "For the seven galaxies in our sample, the $M_{\mathrm{BH}}$ predicted by our models is coherent with previous estimations." (5.2 M_BH estimations results)

## Software

- **Keras** : building and training CNNs  
  > "Our NNs were developed using Python’s library Keras (cite: chollet2015keras)." (4.4 ML architecture)
- **Galfit** : stellar mass decomposition of images  
  > "we use the (cite: salo_spitzer_2015) Galfit (cite: peng2010AJ....139.2097P) decomposition" (3.1 Dynamical estimation)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| log M_BH NGC 4388 (PVD) | 7.18 | 0.16 | log(Msun) | 5 | NGC4388 / 7.18 $\pm$ 0.16 / 6.61 $\pm$ 0.02 |
| log M_BH NGC 5643 (moment map) | 6.99 | 0.02 | log(Msun) | 5 | NGC5643 / 6.13 $\pm$ 0.10 / 6.99 $\pm$ 0.02 |
| log M_BH NGC 6300 (moment map) | 6.39 | 0.01 | log(Msun) | 5 | NGC6300 / 7.15 $\pm$ 0.12 / 6.39 $\pm$ 0.01 |
| worst test RMSE | 0.0367 | not stated | normalised | 4 | The RMSE values are at worst 0.0367 and the $R^2$ are all above 0.946 |

## Qualitative findings

- Models are unreliable below log M_BH ~6 dex; predicted uncertainties are likely overconfident because simulations use simplified physics  
  > "The narrow error bars observed in our results are likely indicative of the network’s overconfidence" (7 Conclusion)

## Claim tuples

- H: CNNs trained on simulations can estimate BH mass from ALMA CO(3-2) kinematics | E: Trained 14 CNNs (PVD and moment-1) on simulated cubes and applied to 7 galaxies | R: Masses log 6.39 to 7.18; consistent with literature except NGC 7314 and NGC 7582 (between prior values) | F: Proof of concept works | **supported**
- H: ML outperforms classical interpolation and chi-squared fitting | E: Applied both to NGC 7582 simulations | R: Classical methods unreliable for 4-8 dex vs ML 4-6 dex | F: ML more robust | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Scaling relations have intrinsic errors limiting use of high-resolution data; ML offers automation and error estimates  
  > "Although scaling relations offer a certain level of automation, their intrinsic errors restrict the full exploitation of the high-resolution data." (4 ML approach)
- How they decided it was enough: _not stated_
- Limitation (authors): One network per galaxy; simulations lack bars, clumps and misalignments; uncertainties not physical  
  > "a key limitation of this work is that we trained and applied the NNs on one galaxy at a time." (7 Conclusion)
- Caveat (inferred, ours): PVD and moment-map estimates disagree for 4 of 7 galaxies
- Caveat (inferred, ours): Symmetrisation may bias masses high
- Caveat (inferred, ours): Train/test on same simulation family so reliability is not independent validation
- Caveat (inferred, ours): Fixed IA/PA and no bars in models

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Project codes and reduced cubes
- Missing: Sampling ranges for simulation parameters
- Missing: Code for simulations and CNNs
- Data volume (inferred): ~10-50 GB for seven ALMA CO(3-2) cubes
- Score (inferred): 3/5, Architectures and training are described but ALMA data, code and parameter ranges are not specified.
- Rediscovery candidate: no, Project codes and simulation setup are not given, so redoing is hard.

## Links

- Method: (cite: melchior2011) (simulation model)
- Method: (cite: combes_alma_2019) (fitting methodology)
- Companion: (cite: garcia-burillo_galaxy_2021) (GATOS core sample observations)
- Related: GATOS
- Related: NUGA
- Related: WISDOM

## Checks

```json
{
 "quotes": 38,
 "quotes_ok": 38,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 0,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2016.1.00254.S",
  "2017.1.00082.S",
  "2018.1.00113.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 4,
 "numeric_problems": 0,
 "fill": {
  "facts": 73,
  "stated": 28,
  "rate": 0.384
 },
 "evidence_ok": true
}
```
