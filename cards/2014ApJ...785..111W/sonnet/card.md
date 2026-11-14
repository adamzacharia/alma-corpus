# Properties of Submillimeter Galaxies in the CANDELS GOODS-South Field

`2014ApJ...785..111W` | The Astrophysical Journal 2014 | first author: Wiklind, Tommy | arXiv: 1402.3268 | DOI: 10.1088/0004-637X/785/2/111

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: high_z_galaxies
- Question: What are the stellar, morphological, gas and dust properties of ALMA-identified LESS submillimeter galaxies in the CANDELS GOODS-S field?  
  > "We derive physical properties of 10 submillimeter galaxies located in the CANDELS coverage of the GOODS-S field." (abstract)
- Target **LESS submillimeter galaxies in GOODS-S (10 counterparts)**: coordinates e.g. LESS 10: RA 53.079417, Dec -27.870778 (J2000, Table 1)  
  > "LESS J033219.0$-$275219 | LESS 10$^{a)}$ | 4414 | 53.079417 | $-$27.870778" (Table 1); z/distance z = 1.65-4.76 (photometric/spectroscopic)  
  > "LESS J033219.0$-$275219 | LESS 10$^{a)}$ | 4414 | 53.079417 | $-$27.870778" (Table 1); distance from SED-fitting photometric redshifts; spectroscopic for 4 sources (Balestra 2010, Kriek 2008, Vanzella 2008)  
  > "LESS J033219.0$-$275219 | LESS 10$^{a)}$ | 4414 | 53.079417 | $-$27.870778" (Table 1)

## Data provenance

- ALMA projects: 2011.0.00294.S
- bands: 870 micron continuum  
  > "The submm data for the galaxies discussed in this paper are taken from the ALMA 870$\mu$m survey presented in Hodge et al. (2013)." (2.1 The Data)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: median 1.60 x 1.15 arcsec  
  > "The median angular resolution of the interferometric data is 1$\,.\!\!^{\prime\prime}$60$\times$1$\,.\!\!^{\prime\prime}$15." (2.1 The Data)
- max recoverable scale: _not stated_
- sensitivity: ~0.55 mJy/beam for LESS 34  
  > "The noise level of the ALMA map is as good as any of the LESS sources in the ‘Primary sample’ with $\sim$0.55 mJy/beam." (3.1 Identification of the counterparts)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Other facility **HST CANDELS/GOODS (ACS, WFC3)**: optical/NIR photometry and F160W images for counterparts, morphology  
  > "CANDELS is a HST Multi-Cycle Treasury Program to image five legacy fields, including the GOODS-South, with the Wide Field Camera 3 (WFC3) in the near-infrared." (2.1 The Data)
- Other facility **Spitzer IRAC and MIPS 24um**: mid-IR photometry; 24um used to constrain power-law  
  > "The 24$\mu$m flux is not used in the SED fitting procedure, but is used in estimating the potential influence of a power-law continuum." (2.1 The Data)
- External data: ALMA 870um fluxes and positions of LESS sources  
  > "Submm continuum flux from Hodge et al. (2013)." (Table 1) [from Hodge et al. (2013)]
- External data: CANDELS GOODS-S F160W-selected photometric catalog (18 bands)  
  > "A catalog (Guo et al. 2013) was made based on source detection in the WFC3 F160W band." (2.1 The Data) [from Guo et al. (2013)]
- External data: Sample of local galaxies and z~2 LBGs for Gini-M20 comparison  
  > "The comparison samples are the same as in Conselice (2003; see Table 1, 4 and 5) and Lotz et al. (2004)." (3.3 Morphology and environment) [from Conselice (2003); Lotz et al. (2004)]
- External data: SFR relation from simulations  
  > "The parametrization is valid for $S_{850}<15$ mJy and for $z\approx1-6$:" (3.4 Star formation and gas/dust content) [from Hayward et al. 2013]

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

- ALMA data reduction, flux and positions taken from the ALMA LESS survey  
  > "For sources detected at more than 3$\sigma$, the positional uncertainty of the center of emission is estimated to be 0$\,.\!\!^{\prime\prime}$2–0$\,.\!\!^{\prime\prime}$3 (Hodge et al. 2013)." (2.1 The Data) [from Hodge et al. (2013)]
- SED fitting algorithm is updated version of earlier code  
  > "The current version of the SED fitting algorithm is an updated version of the one described in Wiklind et al (2008)." (2.2 Analysis) [from Wiklind et al (2008)]
- Photometry via PSF matching and TFIT  
  > "Photometry of lower resolution images is done using the TFIT template-fitting method (see Laidler et al. 2007; Lee et al. 2012; Guo et al. 2013)." (2.1 The Data) [from Guo et al. 2013]

### Not stated but needed to reproduce (our reading)

- ALMA calibration, CASA version and imaging parameters (reimaging of LESS 17 and 34 mentioned but not specified)
- Exact aperture/photometry values per band for the SED fits
- CAS measurement parameters (apertures, segmentation) for morphology
- SED fitting code not released

## Analysis recipe

1. **identify counterparts**: Match ALMA LESS positions to CANDELS F160W catalog; nearest galaxy within 1 arcsec is counterpart  
  > "If the separation between the center of the ALMA 870$\mu$m emission and the nearest galaxy exceeds 1$\,.\!\!^{\prime\prime}$0, we do not consider the galaxy and the SMG to be associated" (2.2 Analysis)
   - fitting: _not stated_
   - validation: _not stated_
2. **SED fitting for redshift, mass, age**: BC03 templates with delayed-tau SFH, Chabrier IMF, Calzetti extinction, Madau IGM; chi2 minimisation; optional power-law subtraction scaled to 8um  
  > "Dust obscuration is introduced using the attenuation law of Calzetti et al. (2000)." (2.2 Analysis)
   - software: Wiklind et al. 2008 SED code
   - parameter: z=0.05-10 step 0.05; E(B-V)=0-1 step 0.025; age 50 Myr-7 Gyr; Z=0.2,0.4,1.0,2.5 Zsun  
  > "Four different metallicities are used, 0.2, 0.4, 1.0, and 2.5 Z$_{\odot}$." (2.2 Analysis)
   - assumption: power-law alpha=2.0 for AGN continuum  
  > "The latter sample contains SMGs similar to the ones discussed here, and we will assume $\alpha=2.0$." (2.2 Analysis)
   - fitting: chi2 minimization with 10^3 Monte Carlo realisations of photometry; P(z) ∝ exp(-chi2)  
  > "We generate $10^{3}$ photometric data sets for each galaxy." (2.2 Analysis)
   - validation: Tested with 11 other codes against spectroscopic redshifts (Dahlen et al. 2013)  
  > "The photometric redshifts obtained in the SED fitting process with this code has been tested together with 11 other codes" (2.2 Analysis)
3. **morphology**: CAS, Gini and M20 on F160W images, comparison with mass/z-matched control samples, visual classification  
  > "We measure the CAS (concentration, asymmetry and clumpiness) parameters of the SMG counterparts using HST/WFC3 F160W images." (2.3 Morphological parameters)
   - fitting: _not stated_
   - validation: Monte Carlo of randomized control galaxies, 10^3 times  
  > "Repeating this procedure $10^{3}$ times, we find that in 99% of the Monte Carlo realizations" (3.3 Morphology and environment)
4. **dust, gas mass, SFR**: Optically thin dust mass from 870um flux; gas from dust-to-gas ratio and H2/HI; SFR from Hayward et al. 2013 relation; LFIR from SFR  
  > "As shown by Scoville (2012) and Scoville et al. (2014), the observed submm flux is linearly dependent on the dust mass as long as the emission remains optically thin." (3.4 Star formation and gas/dust content)
   - parameter: Td=35 K, beta=1.8  
  > "assuming a dust temperature of $T_{d}={\bf35}$ K, we derive the dust masses listed in Table [5]" (3.4 Star formation and gas/dust content)
   - assumption: dust-to-gas ratio 0.0052 (Draine 2007); H2/HI ~2  
  > "The average H$_2$/HI ratio for this sample is $\sim$2 and we will assume that this is the case for our SMGs as well." (3.4 Star formation and gas/dust content)
   - fitting: _not stated_
   - validation: Compared with CO-derived gas mass of LESS 73  
  > "we estimate a molecular gas mass of $5.2\times10^{10}$ M$_{\odot}$ for LESS 73." (3.4 Star formation and gas/dust content)

## Software

- **SExtractor** : source extraction in CANDELS catalog (from Guo et al.)  
  > "The sources were extracted using SExtractor in both a hot and cold mode." (2.1 The Data)
- **TFIT** : photometry of low-resolution images  
  > "Photometry of lower resolution images is done using the TFIT template-fitting method" (2.1 The Data)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| redshift range of counterparts | 1.65-4.76 | not stated | dimensionless | 2 | The redshift range is z$=$1.65-4.76, with two of the galaxies located at z$>$4. |
| mean M* excluding LESS 10 and 34 | 1.1e11 | 0.4e11 | Msun | 2 | Disregarding LESS 10 and LESS 34, the average stellar mass is $M_{*} = (1.1 \pm 0.4) \times 10^{11}$ M$_{\odot}$ |
| mean dust mass | 4.0e8 | 1.3e8 | Msun | 4 | M$_{\mathrm{dust}}=(4.0\pm1.3)\times10^{8}$ M$_{\odot}$ |
| mean H2 mass | 5.1e10 | 1.7e10 | Msun | 4 | the average H$_2$ mass is $M_{\mathrm{H_2}}=(5.1\pm1.7)\times10^{10}$ M$_{\odot}$ |
| mean molecular gas fraction (8 SMGs) | 0.28 | 0.07 | dimensionless | 4 | the average gas fraction for the remaining 8 SMGs is $0.28\pm0.07$ (sample standard deviation) |
| mean SFR | 0.8e3 | 0.7e3 | Msun/yr | 4 | with an average of $(0.8\pm0.7)\times10^{3}$ M$_{\odot}$ yr$^{-1}$ |

## Qualitative findings

- 3 of 10 SMG counterparts are mergers, 2 have neighbours, 5 are isolated  
  > "we find 3 SMGs that are part of mergers (LESS 13, 67 and 79.2), 2 SMGs with neighbors within 30 kpc (LESS 34 and 45), and 5 that appears to be completely isolated" (3.3 Morphology and environment)

## Claim tuples

- H: Are SMG counterparts mostly mergers and more asymmetric than comparable galaxies? | E: CAS morphology vs mass/z-matched control samples and visual inspection of F160W images | R: 3 mergers, 7 not; average asymmetry higher than controls in 99% of Monte Carlo realizations | F: SMGs are more asymmetric but mostly isolated, unlike local ULIRGs | **supported**
- H: Do SMG counterparts have uniform stellar masses? | E: SED fitting of 10 counterparts | R: Two have masses 2-3 orders lower; rest ~1e11 Msun | F: Two stellar mass groups; SMG stellar populations older than the SMG phase | **supported**

## Reasoning

- Why this data: Interferometric submm positions give less biased counterpart identification than radio or IRAC  
  > "Submm interferometry represents the least biased method at our disposal to identify the counterparts of SMGs." (4.1 The SMG counterparts)
- Why this method: _not stated_
- Alternative: Low masses of LESS 10 and 34 not due to power-law subtraction or obscured stars; may be background source  
  > "The low masses are not due to the subtraction of a power-law continuum." (3.2 Photometric redshift and stellar properties)
- How they decided it was enough: _not stated_
- Limitation (authors): Single-component SFH cannot model multiple bursts; ages and masses uncertain  
  > "It is, however, not able to model a multiple-burst star formation history." (4.2 Stellar properties)
- Caveat (inferred, ours): Single 870um flux with assumed Td=35 K gives dust/gas masses uncertain by factor of a few
- Caveat (inferred, ours): SFR from a simulation-calibrated relation, not measured
- Caveat (inferred, ours): Counterpart association for offset sources (LESS 17) could be wrong

## Reproducibility

- Data public (paper): ALMA data cited by project code in acknowledgments  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2011.0.00294.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: SED code not public
- Missing: ALMA reduction details deferred to Hodge et al. 2013
- Data volume (inferred): Small if using published ALMA fluxes and CANDELS catalog (~GB); raw ALMA ~tens of GB
- Score (inferred): 3/5, Analysis relies on published ALMA products and CANDELS catalogs with a custom, unreleased SED code; ALMA processing is deferred.
- Rediscovery candidate: no, Custom SED code not released and ALMA is a minor ingredient taken from Hodge et al.

## Links

- Method: Hodge et al. (2013) (ALMA LESS survey data and reduction)
- Method: Guo et al. (2013) (CANDELS GOODS-S catalog and photometry)
- Method: Wiklind et al. (2008) (SED fitting method)
- Companion: Targett et al. (2013) (Compared SMG sample in GOODS-S)
- Related: LESS (LABOCA ECDFS Submillimeter Survey)
- Related: CANDELS
- Related: GOODS

## Checks

```json
{
 "quotes": 46,
 "quotes_ok": 46,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 73,
  "stated": 35,
  "rate": 0.479
 },
 "evidence_ok": true
}
```
