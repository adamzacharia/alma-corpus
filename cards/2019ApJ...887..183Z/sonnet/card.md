# On the Gas Content, Star Formation Efficiency, and Environmental Quenching of Massive Galaxies in Protoclusters at z ≈ 2.0-2.5

`2019ApJ...887..183Z` | The Astrophysical Journal 2019 | first author: Zavala, J. A. | arXiv: 1910.13457 | DOI: 10.3847/1538-4357/ab5302

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies, nearby_galaxies
- Question: What are the gas content, star formation efficiency and environmental quenching of massive galaxies in two proto-clusters at z=2.10 and 2.47, compared with field galaxies?  
  > "we characterize the gas mass fraction and the star formation efficiency, and infer the impact of the environment on galaxies’ evolution." (abstract)
- Target **z=2.10 and z=2.47 proto-clusters in COSMOS (68 galaxies)**: coordinates _not stated_; z/distance z=2.10 and z=2.47 (spectroscopic)  
  > "This study focuses on two particularly unique rich protoclusters at $z=2.10$ and $z=2.47$ in the COSMOS field" (1 Introduction); distance from spectroscopic redshifts from Casey2015, Casey2016, Hung2016  
  > "This study focuses on two particularly unique rich protoclusters at $z=2.10$ and $z=2.47$ in the COSMOS field" (1 Introduction)

## Data provenance

- ALMA projects: 2016.1.00646.S
- bands: Band 6 (233 GHz, 1.3 mm)  
  > "ALMA Band 6 observations were conducted on 4 April 2017" (2.2 ALMA observations and detection of dust continuum)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: 7.5 GHz centered at 233 GHz  
  > "providing a total bandwidth of 7.5 GHz centered at 233 GHz ($\approx1.3$ mm)" (2.2 ALMA observations and detection of dust continuum)
- arrays: 12 m antennae  
  > "using the 12 m antennae in a relatively compact configuration" (2.2 ALMA observations and detection of dust continuum)
- configurations: _not stated_
- baselines: longest baseline 0.46 km  
  > "with the longest baselines at 0.46 km" (2.2 ALMA observations and detection of dust continuum)
- angular resolution: ~0.9 arcsec  
  > "a typical synthesized beamsize of $\theta_{\rm FWHM}\approx0.9''$" (2.2 ALMA observations and detection of dust continuum)
- max recoverable scale: _not stated_
- sensitivity: 40-50 uJy/beam  
  > "yielding central noises between $\sigma_{1.3\rm mm}=40-50\,\rm\mu Jy/beam$" (2.2 ALMA observations and detection of dust continuum)
- time on source: ~5 min per pointing, 46 pointings  
  > "a total of 46 pointings with an average on-source integration time of $\sim5$ min" (2.2 ALMA observations and detection of dust continuum)
- observing dates: 4 April 2017  
  > "ALMA Band 6 observations were conducted on 4 April 2017" (2.2 ALMA observations and detection of dust continuum)
- pi or archival as stated: Cycle 4 program, PI C. Casey  
  > "Cycle 4 program 2016.1.00646.S (PI: C. Casey)" (2.2 ALMA observations and detection of dust continuum)
- Other facility **COSMOS2015 catalog (UltraVISTA, Subaru, Spitzer, GALEX, Herschel)**: Multiwavelength photometry (>30 bands) for SED fitting  
  > "comprising more than 30 bands." (3.2 Stellar masses and star formation rates)
- Other facility **Chandra**: X-ray AGN identification via matches in Laigle2016  
  > "we identify those galaxies which are likely to host an AGN based on their detection with *Chandra* X-ray Observatory" (4.3 Environmental quenching)
- External data: Field control sample and gas scaling relations (ALMA Band 7, ~55 targets)  
  > "The adopted field scaling relations comes from (cite: Scoville2016a)" (2.1 Target selection and control sample) [from (cite: Scoville2016a)]
- External data: Spectroscopic proto-cluster member samples  
  > "drawn from (cite: Casey2015a; Casey2016a); and (cite: Hung2016a)" (2.1 Target selection and control sample) [from (cite: Casey2015a; Casey2016a; Hung2016a)]
- External data: COSMOS2015 photometry  
  > "We use the COSMOS2015 catalog ((cite: Laigle2016a)" (3.2 Stellar masses and star formation rates) [from (cite: Laigle2016a)]
- External data: Structure volume of 15000 cMpc^3  
  > "This estimation assumes a volume of $15000\,\rm cMpc^3$ for each structure, as estimated by (cite: Casey2016a)." (4.2 Gas content and gas fraction) [from (cite: Casey2016a)]

## Processing

### Calibration

- pipeline or manual: ALMA reduction pipeline scripts  
  > "Data reduction was individually performed following the ALMA reduction pipeline scripts in CASA (version 4.7.2)." (2.2 ALMA observations and detection of dust continuum)
- casa version: CASA 4.7.2  
  > "ALMA reduction pipeline scripts in CASA (version 4.7.2)" (2.2 ALMA observations and detection of dust continuum)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "The continuum maps were obtained using a natural weighting of the visibilities" (2.2 ALMA observations and detection of dust continuum)
- uv taper: _not stated_
- cell size: 0.12 arcsec  
  > "using a pixel size of $0.12''$" (2.2 ALMA observations and detection of dust continuum)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: flux measured on primary-beam corrected images  
  > "a simple peak-finding algorithm is implemented on the primary-beam corrected images" (2.2 ALMA observations and detection of dust continuum)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: ~0.9 arcsec  
  > "a typical synthesized beamsize of $\theta_{\rm FWHM}\approx0.9''$" (2.2 ALMA observations and detection of dust continuum)
- final rms: 40-50 uJy/beam  
  > "central noises between $\sigma_{1.3\rm mm}=40-50\,\rm\mu Jy/beam$" (2.2 ALMA observations and detection of dust continuum)

### Inherited from earlier work

- ISM mass calibration from Rayleigh-Jeans dust continuum (alpha_850, Gamma factors)  
  > "Following (cite: Scoville2016a) we derive the ISM masses using:" (3.1 ISM masses) [from (cite: Scoville2014a; Scoville2016a)]
- SED fitting setup similar to COSMOS2015  
  > "similar to the parameters adopted in the work by (cite: Laigle2016a)" (3.2 Stellar masses and star formation rates) [from (cite: Laigle2016a)]
- Tau-model quenching path on UVJ  
  > "(see details in (cite: Belli2019a))" (4.3 Environmental quenching) [from (cite: Belli2019a)]

### Not stated but needed to reproduce (our reading)

- Which spectral windows/channels were flagged
- Number and parameters of CLEAN iterations/threshold and masking
- Exact peak-finding and stacking implementation
- MAGPHYS priors and settings, star formation history parameters
- How passive and star-forming fractions and their errors were computed for the quenching efficiency
- Field detection fractions binned by mass used in Figure 7
- Flux scale uncertainty and calibrators

## Analysis recipe

1. **Image continuum and detect sources**: Natural-weighted continuum images; peak-finding within 1 arcsec of optical positions on primary-beam corrected maps; 3 sigma threshold  
  > "A source is considered detected only if it satisfies a detection threshold of $\ge3\sigma$" (2.2 ALMA observations and detection of dust continuum)
   - software: CASA
   - parameter: local noise = 68th percentile of pixel distribution  
  > "the local noise is computed to be the $68^{th}$ percentile of the distribution of pixel values" (2.2 ALMA observations and detection of dust continuum)
   - fitting: _not stated_
   - validation: Errors consistent with std of small off-source apertures  
  > "The errors calculated with this method are consistent with those derived by measuring the standard deviation of small off-source apertures." (2.2 ALMA observations and detection of dust continuum)
2. **Stack non-detections**: Weighted average of image cutouts; weights inverse square of noise; peak within 1 arcsec of center  
  > "We extract small cutouts in the image plane centered at the position of each galaxy and then combine them in a weighted average." (2.2 ALMA observations and detection of dust continuum)
   - fitting: _not stated_
   - validation: _not stated_
3. **Derive ISM masses**: Scoville et al. 2016 calibration of RJ dust continuum to ISM mass  
  > "calibrating a ratio between the specific luminosity at rest-frame $850\,\rm\mu m$ to the total ISM mass." (3.1 ISM masses)
   - assumption: Td=25 K for Gamma_0; uncertainty <25%  
  > "with ${ \Gamma_{0}} = {\Gamma}(T_{\rm d}=25\,{\rm K}, \lambda=850\,{\rm\mu m}, z=0)$" (3.1 ISM masses)
   - fitting: _not stated_
   - validation: _not stated_
4. **Derive stellar masses and SFRs**: MAGPHYS SED fitting of COSMOS2015 photometry plus ALMA, fixed spectroscopic redshift, BC03, Chabrier IMF, delayed exponential SFH  
  > "using the spectral population synthesis models of (cite: Bruzual2003a), with a (cite: Chabrier2003a) IMF, and a continuous delayed exponential star formation history" (3.2 Stellar masses and star formation rates)
   - software: MAGPHYS
   - fitting: _not stated_
   - validation: Stellar masses agree with COSMOS2015, mean ratio 1.01±0.06  
  > "${\rm log}(M_{*_{\rm \small{COSMOS}}})/{\rm log}(M_{*_{\rm  \small{MAGPHYS}}})=1.01\pm0.06$" (3.2 Stellar masses and star formation rates)
5. **Compare SFE, gas fractions and quenching with field**: KS test on SFE vs field; gas fraction f_gas=Mmol/(Mmol+M*); detection fraction vs field; quenching efficiency and timescale from stellar age  
  > "we estimate an average quenching efficiency of $\epsilon_q=0.45^{+0.16}_{-0.13}$" (4.3 Environmental quenching)
   - assumption: Planck cosmology H0=68, OmegaLambda=0.69; Chabrier IMF  
  > "We assume a standard Planck cosmology throughout this paper, with $H_0 = 68\rm\,km\,s^{-1}\,Mpc^{-1}$ and $\Omega_\Lambda= 0.69$" (1 Introduction)
   - fitting: _not stated_
   - validation: Results checked with Tacconi2018 scaling relations  
  > "The main results of this paper remain if we instead adopt the scaling relations derived by (cite: Tacconi2018a)" (Comparison to other scaling relations.)

## Software

- **CASA** 4.7.2: Data reduction with ALMA pipeline scripts and imaging  
  > "Data reduction was individually performed following the ALMA reduction pipeline scripts in CASA (version 4.7.2)." (2.2 ALMA observations and detection of dust continuum)
- **MAGPHYS** : SED fitting for stellar masses, SFRs, ages  
  > "using the MAGPHYS code ((cite: da-Cunha2008a; da-Cunha2015a))" (3.2 Stellar masses and star formation rates)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Detected galaxies in continuum | 19 of 68 | not stated | sources | 1 | From all the 68 proto-cluster galaxies which lie within our surveyed area, 19 sources were detected above our adopted threshold |
| KS probability SFE same as field (M*>1e10) | 0.81 | not stated | dimensionless | 5 | we derive a probability of $p=0.81$ that both of them are drawn from the same parent distribution |
| Quenching efficiency | 0.45 | +0.16/-0.13 | dimensionless | 5 | we estimate an average quenching efficiency of $\epsilon_q=0.45^{+0.16}_{-0.13}$ |
| Quenching timescale upper limit | <1 | not stated | Gyr | 5 | resulting in an upper limit on quenching timescale of $\tau_q<1\,\rm Gyr$ |
| Gas fraction of massive gas-poor galaxies | ≲6-10 | not stated | percent | 5 | some of the most massive galaxies studied in this work show very low gas mass fractions, $f_{\rm gas}\lesssim 6-10\,\%$ |

## Qualitative findings

- Most detected galaxies (~70%) have SFE and gas fractions like coeval field galaxies  
  > "Most of our detected galaxies ($\gtrsim70\%$) have star formation efficiencies and gas fractions similar to those found for coeval field galaxies" (abstract)
- Proto-clusters show lower ALMA detection fraction than field, especially for high-mass galaxies  
  > "the observations towards proto-cluster member galaxies show a lower detection fraction than those for the field samples, particularly for the high-mass galaxies" (4.3 Environmental quenching)

## Claim tuples

- H: Do proto-cluster galaxies have SFE like field galaxies? | E: Compare SFR vs Mmol with Scoville2016 field relation, KS test | R: 13 of 18 detections on relation; p=0.81 | F: SFEs of most massive galaxies are consistent with field | **supported**
- H: Is there accelerated quenching in proto-clusters? | E: Compare ALMA detection fractions, gas fractions and colors with field | R: Lower detection fraction, more massive gas-poor red galaxies | F: Environmental quenching occurs before virialization, epsilon_q≈0.45, tau_q<1 Gyr | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Continuum as proxy for gas masses since spectroscopic observations of large samples are prohibitive  
  > "deeper ALMA spectroscopic observations would require several hours of on-source time per target, making spectroscopic observations of larger samples prohibitive." (4.2 Gas content and gas fraction)
- Alternative: Earlier onset of star formation as explanation for advanced evolution, disfavoured by similar stellar ages  
  > "Nevertheless, the mean stellar age of the red, massive gas-poor galaxies is consistent with the ages derived for the ALMA-detected galaxies" (4.3 Environmental quenching)
- How they decided it was enough: _not stated_
- Limitation (authors): Sample incomplete at low mass; conclusions restricted to M*>1e10  
  > "Given that the completeness of our sample drops at $M_\star\lesssim10^{10}\,M_\odot$ where, additionally, we lack a control sample" (2.1 Target selection and control sample)
- Caveat (inferred, ours): Single Rayleigh-Jeans continuum point with assumed Td=25 K and alpha_850 calibrated on field galaxies
- Caveat (inferred, ours): Passive classification of non-detections is based on shallow upper limits
- Caveat (inferred, ours): Spectroscopic selection biases of member lists may differ from field comparison
- Caveat (inferred, ours): Small numbers in quenching efficiency

## Reproducibility

- Data public (paper): Data from ALMA project 2016.1.00646.S  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2016.1.00646.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Imaging details beyond natural weighting
- Missing: MAGPHYS configuration
- Missing: Field comparison data digitized from Scoville2016, Bouwens2016, Dunlop2017
- Data volume (inferred): ~50-100 GB raw for 46 short pointings
- Score (inferred): 3/5, Public data and a simple method but several parameters (imaging, SED setup, fraction calculations) unstated.
- Rediscovery candidate: yes, Public data, simple continuum flux to mass recipe with numeric tables, though SED parts need external photometry.

## Links

- Method: (cite: Scoville2016a) (ISM mass calibration and field control sample)
- Method: (cite: da-Cunha2008a; da-Cunha2015a) (MAGPHYS SED fitting)
- Companion: (cite: Casey2016a) (proto-cluster samples and volume)
- Companion: (cite: Hung2016a) (z=2.10 structure members)
- Related: COSMOS
- Related: COSMOS2015

## Checks

```json
{
 "quotes": 56,
 "quotes_ok": 56,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 76,
  "stated": 47,
  "rate": 0.618
 },
 "evidence_ok": true
}
```
