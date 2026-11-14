# Rotational spectroscopy, tentative interstellar detection, and chemical modeling of N-methylformamide

`2017A&A...601A..49B` | Astronomy and Astrophysics 2017 | first author: Belloche, A. | arXiv: 1701.04640 | DOI: 10.1051/0004-6361/201629724

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: astrochemistry, star_formation
- Question: Can improved laboratory rotational spectroscopy of trans N-methylformamide enable its detection toward Sgr B2(N2) in the ALMA EMoCA survey, and how can its abundance relative to related molecules be explained by chemical modelling?  
  > "our goal is to improve the characterization of the rotational spectrum of N-methylformamide." (abstract); "The astronomical results are put into a broader astrochemical context with the help of a gas-grain chemical kinetics model." (abstract)
- Target **Sgr B2(N2)**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2011.0.00017.S, 2012.1.00012.S
- bands: _not stated_
- frequencies and spectral setup: 84.1-114.4 GHz, spectral resolution 488.3 kHz (1.7 to 1.3 km/s)  
  > "The survey covers the frequency range between 84.1 and 114.4 GHz with a spectral resolution of 488.3 kHz (1.7 to 1.3 km s$^{-1}$)." (4.1 Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: median 1.6"  
  > "The median angular resolution is 1.6$\ensuremath{''}$." (4.1 Observations)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: ALMA Cycles 0 and 1  
  > "We use the full data set of the EMoCA spectral line survey obtained toward Sgr B2(N) with ALMA in its Cycles 0 and 1." (4.1 Observations)
- pi or archival as stated: _not stated_
- Other facility **Kharkiv and Lille absorption spectrometers**: Laboratory rotational spectra of N-methylformamide, 45-630 GHz  
  > "The experimental investigation of the absorption spectrum of N-methylformamide was carried out over the frequency range 45–630 GHz using two microwave spectrometers." (2 Experimental setup)
- External data: Earlier laboratory data for trans N-methylformamide refitted together with new data  
  > "We started our analysis of the *trans* N-methylformamide spectrum from refitting the data available from the literature" (3 Spectroscopic analysis and results) [from (cite: fantoni1996rotational; fantoni2002very; kawashima2010dynamical)]
- External data: CDMS/JPL spectroscopic entries for CH3NCO, formamide, HNCO and isotopologues  
  > "we use the predictions available in the Cologne database for molecular spectroscopy" (4.3 Methyl isocyanate) [from (cite: Mueller05)]
- External data: Acetamide predictions recomputed with RAM36  
  > "We use predictions that are based on the measurements and analysis presented in (cite: ilyushin2004acetamide) but were recomputed by one of us (VVI) with the RAM36 code." (4.6 Acetamide) [from (cite: ilyushin2004acetamide)]
- External data: Activation barrier for H + HNCO of 1390 K  
  > "The barrier to the similar reaction of H with HNCO has been determined experimentally in the gas phase by (cite: Nguyen96) to be 1390 K" (5 Chemical modelling) [from (cite: Nguyen96)]

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

- Observations, data reduction, line identification and column density method  
  > "A detailed description of the observations, the data reduction process, and the method used to identify the detected lines and derive column densities was presented in (cite: Belloche16)." (4.1 Observations) [from (cite: Belloche16)]
- Population diagrams constructed as in previous work  
  > "Population diagrams are constructed in the same way as in our previous work." (4.1 Observations) [from Belloche16]
- Chemical network extended from earlier work; physical model and initial abundances follow earlier papers  
  > "The initial chemical compositions used in the model follow those of (cite: Garrod13)." (5 Chemical modelling) [from (cite: Belloche14), (cite: Mueller16a), (cite: Garrod13)]

### Not stated but needed to reproduce (our reading)

- Imaging and calibration parameters (CASA version, weighting, spectral extraction position/aperture) not given; only in Belloche et al. 2016
- Coordinates and distance of Sgr B2(N2) not given here
- Details of the full LTE model of all other molecules needed to remove contamination
- Uncertainties on LTE column densities not tabulated
- Network files for MAGICKAL not provided

## Analysis recipe

1. **Fit laboratory rotational spectrum**: Rho-axis method Hamiltonian fitted with RAM36 to new plus literature data  
  > "To fit and predict the rotational spectra we used the RAM36 (Rho-axis method for 3 and 6-fold barriers) program" (3 Spectroscopic analysis and results)
   - software: RAM36
   - parameter: 103 parameters; 12456 transitions, 9469 distinct frequencies, J<=62  
  > "The fit chosen as the "best" one uses a model consisting of 103 parameters." (3 Spectroscopic analysis and results)
   - fitting: _not stated_
   - validation: Weighted rms 0.84  
  > "The weighted root-mean-square deviation of the fit of 12456 microwave transition frequencies with $J \leq 62$ is 0.84" (3 Spectroscopic analysis and results)
2. **Compute partition functions**: Direct summation over rotational-torsional states plus harmonic vibrational part from DFT B3LYP  
  > "The values of $Q_{\rm tr}$ were calculated from first principles, i.e. via direct summation over the rotational-torsional states." (3 Spectroscopic analysis and results)
   - parameter: J up to 130, vt up to 8; B3LYP/6-311++(3df,2pd)  
  > "The maximum value of the $J$ quantum number of the energy levels taken into account to calculate the partition function is 130, and excited torsional states up to $\varv_{\rm t} = 8$ were considered." (3 Spectroscopic analysis and results)
   - fitting: _not stated_
   - validation: _not stated_
3. **Search for CH3NHCHO and model LTE spectra**: Compare ALMA spectrum with LTE synthetic spectra and a full model of all identified molecules; assess unblended lines  
  > "We compared the observed ALMA spectrum of Sgr B2(N2) to synthetic spectra of CH$_3$NHCHO produced under the assumption of local thermodynamic equilibrium (LTE)" (4.2 Tentative detection of N-methylformamide)
   - parameter: size 0.9", Trot 180 K, N = 1.0e17 cm-2, FWHM 5.0 km/s  
  > "CH$_3$NHCHO, $\varv_{\rm t}=0$$^\star$ | t | 4 | 0.9 | 180 | 1.0 (17) | 1.26 | 5.0 | 0.5 | 1" (Table 3)
   - assumption: LTE valid given high densities of hot cores  
  > "which is expected to be valid given the high densities of the hot core regions probed by the EMoCA survey" (4.2 Tentative detection of N-methylformamide)
   - fitting: _not stated_
   - validation: Five unblended lines match linewidths and peak temperatures; detection called tentative  
  > "Given the small number of clearly detected lines, we consider our detection of CH$_3$NHCHO as tentative rather than secure." (4.2 Tentative detection of N-methylformamide)
4. **Derive rotational temperatures and sizes**: Population diagrams and Gaussian fits to integrated intensity maps for each molecule  
  > "A fit to this diagram yields a rotational temperature of $149 \pm 20$ K, with a significant uncertainty" (4.2 Tentative detection of N-methylformamide)
   - fitting: _not stated_
   - validation: _not stated_
5. **Fit related molecules (CH3NCO, NH2CHO, HNCO, CH3CONH2)**: LTE modelling with adopted temperatures and sizes to derive column densities  
  > "We adopt a temperature of 150 K for our LTE modelling." (4.3 Methyl isocyanate)
   - fitting: _not stated_
   - validation: _not stated_
6. **Chemical kinetics modelling**: MAGICKAL gas-grain model with cold collapse then warm-up 8-400 K, varying activation energies of NH + CO and H + CH3NCO  
  > "we use the chemical kinetics model *MAGICKAL* (Garrod 2013) with an expanded gas-grain chemical network." (5 Chemical modelling)
   - software: MAGICKAL
   - parameter: nH = 2e8 cm-3, 8 K minimum dust temperature, intermediate warm-up timescale  
  > "we use the intermediate warm-up timescale, which generally produces the best match between models and observed abundances" (5 Chemical modelling)
   - assumption: Binding energies 3575 K (CH3NCO) and 6281 K (CH3NHCHO) estimated  
  > "Binding energy values for CH$_3$NCO and CH$_3$NHCHO are 3575 K and 6281 K, respectively" (5 Chemical modelling)
   - fitting: _not stated_
   - validation: Model abundance ratios compared with observed ratios  
  > "Table [\[RTG-tab5\]](#RTG-tab5) shows ratios of the abundances of the main molecules with that of HNCO" (5.1 Model results)

## Software

- **RAM36** : Fit and predict rotational spectra  
  > "To fit and predict the rotational spectra we used the RAM36" (3 Spectroscopic analysis and results)
- **MAGICKAL** : Gas-grain chemical kinetics modelling  
  > "we use the chemical kinetics model *MAGICKAL* (Garrod 2013)" (5 Chemical modelling)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Laboratory line frequencies (distinct) | 9469 | not stated | lines | 1 | consists of 9469 distinct line frequencies with $J \leq 62$ |
| Weighted rms of fit | 0.84 | not stated | dimensionless | 1 | The weighted root-mean-square deviation of the fit of 12456 microwave transition frequencies with $J \leq 62$ is 0.84 |
| V3 barrier | 51.7199088 | 0.0000090 | cm-1 | 1 | $V_3$ (cm$^{-1}$) / 51.7199088(90) / 53.91824(11) |
| CH3NHCHO rotational temperature | 149 | 20 | K | 4 | A fit to this diagram yields a rotational temperature of $149 \pm 20$ K |
| CH3NHCHO column density | ~1e17 | not stated | cm-2 | 3 | We derive a column density of $\sim$$1 \times 10^{17}$ cm$^{-2}$ for N-methylformamide. |
| CH3NCO column density | 2.2e17 | not stated | cm-2 | 5 | CH$_3$NCO, $\varv_{\rm b}=0$$^\star$ / d / 60 / 1.2 / 150 / 2.2 (17) |
| NH2CHO column density | 3.5e18 | not stated | cm-2 | 5 | NH$_2$CHO, $\varv=0$$^\star$ / d / 30 / 0.8 / 200 / 3.5 (18) |
| CH3CONH2 column density | 1.4e17 | not stated | cm-2 | 5 | CH$_3$CONH$_2$, $\varv_{\rm t}=0$$^\star$ / d / 10 / 0.9 / 180 / 1.4 (17) |
| CH3NHCHO/CH3NCO ratio | 0.45 | not stated | dimensionless | 5 | CH$_3$NHCHO / CH$_3$NCO      /    52 /  0.22 /  1.3 /  0.18 /         0.45 |
| CH3NHCHO/CH3CONH2 ratio | 0.71 | not stated | dimensionless | 5 | CH$_3$NHCHO / CH$_3$CONH$_2$ /  0.48 / 0.050 / 0.17 / 0.037 /         0.71 |
| 14N/15N ratio in formamide | 300 | not stated | dimensionless | 5 | with one clearly detected line consistent with a $^{14}$N/$^{15}$N isotopic ratio of 300 |

## Qualitative findings

- Five unblended lines assigned to CH3NHCHO (four in vt=0, one in vt=1); detection tentative  
  > "In total, five lines can be clearly assigned to CH$_3$NHCHO, four within its torsional ground state and one within its first torsionally excited state." (4.2 Tentative detection of N-methylformamide)
- Efficient HNCO formation via NH + CO on grains is needed to reproduce CH3NCO  
  > "The chemical models indicate that the efficient formation of HNCO via NH + CO on grains is a necessary step in the achievement of the observed gas-phase abundance of CH$_3$NCO." (abstract)

## Claim tuples

- H: Improved spectroscopy allows reliable detection of N-methylformamide in Sgr B2(N2) | E: LTE modelling of ALMA EMoCA spectrum with new predictions | R: Five unblended lines match; N ~1e17 cm-2 | F: Tentative detection | **partially**
- H: Formation of CH3NHCHO and CH3NCO can be explained by grain chemistry | E: MAGICKAL models M1-M5, M4A-E | R: Models with NH+CO barrier <~1500 K and H+CH3NCO barrier ~2000 K reproduce ratios | F: Radical addition or hydrogenation of CH3NCO plausible | **supported**
- H: Isomer ratio follows minimum energy principle | E: Compare CH3NHCHO/CH3CONH2 with predicted ratio | R: Observed factor 1.4 vs predicted ~3.5 | F: Kinetics rather than thermodynamics likely controls abundances | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Removing NH2 + H2CO route reduces NH2CHO by an order of magnitude but acetamide still overproduced  
  > "However, even the better match to observed NH$_2$CHO is not sufficient to bring down acetamide abundances to appropriate levels" (5.1 Model results)
- How they decided it was enough: _not stated_
- Limitation (authors): Only five clean lines, so detection tentative  
  > "Given the small number of clearly detected lines, we consider our detection of CH$_3$NHCHO as tentative rather than secure." (4.2 Tentative detection of N-methylformamide)
- Limitation (authors): Models overproduce NH2CHO and CH3CONH2 by more than an order of magnitude  
  > "all four models produce an overabundance of NH$_2$CHO and CH$_3$CONH$_2$ by more than an order of magnitude" (5.1 Model results)
- Caveat (inferred, ours): Detection rests on five lines in a confused spectrum; no formal significance given
- Caveat (inferred, ours): Adopted temperature (180 K) differs from fitted 149 K
- Caveat (inferred, ours): Chemical model has many free barriers, weak constraint
- Caveat (inferred, ours): No uncertainties on column densities

## Reproducibility

- Data public (paper): Interferometric data in ALMA archive  
  > "The interferometric data are available in the ALMA archive at https://almascience.eso.org/aq/." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Calibration/imaging details (in Belloche et al. 2016)
- Missing: Full LTE model of other species
- Missing: Chemical network files and model inputs
- Data volume (inferred): Large (hundreds of GB for full EMoCA survey)
- Score (inferred): 3/5, Data public and approach clear, but processing inherited and numeric results lack uncertainties.
- Rediscovery candidate: no, Depends on inherited reduction and full line model; detection tentative.

## Links

- Method: (cite: Belloche16) (EMoCA survey observations, reduction and LTE method)
- Method: (cite: ilyushin2010new) (RAM36 code)
- Companion: (cite: Belloche13) (Earlier Sgr B2(N) line survey and models)
- Related: EMoCA survey

## Checks

```json
{
 "quotes": 53,
 "quotes_ok": 53,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 11,
 "numeric_problems": 0,
 "fill": {
  "facts": 82,
  "stated": 35,
  "rate": 0.427
 },
 "evidence_ok": true
}
```
