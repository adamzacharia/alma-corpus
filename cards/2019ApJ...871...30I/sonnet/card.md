# The Size, Shape, and Scattering of Sagittarius A* at 86 GHz: First VLBI with ALMA

`2019ApJ...871...30I` | The Astrophysical Journal 2019 | first author: Issaoun, S. | arXiv: 1901.06226 | DOI: 10.3847/1538-4357/aaf732

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: milky_way_ism, agn_and_quasars
- Question: What are the intrinsic size and shape of Sgr A* at 86 GHz, and what do long ALMA baselines imply for accretion/jet models and interstellar scattering?  
  > "We reconstruct a first image of the unscattered source structure of Sgr A$^{\ast}$at 3.5 mm, mitigating effects of interstellar scattering." (abstract)
- Target **Sgr A***: coordinates RA 17h45m40.0361s, Dec -29d00m28.168s (J2000)  
  > "Observations of Sgr A$^{\ast}$ ($\alpha_\mathrm{J2000} = 17^\mathrm{h}45^\mathrm{m}40^\mathrm{s}.0361$, $\delta_\mathrm{J2000} = -29^\mathrm{\circ}00\mathrm{'}28\mathrm{''}.168$)" (3 Observations and data reduction); "at a distance $D \sim 8.1$ kpc (cite: Ghez_2008; Reid_2009; Gillessen_2009; Gravity_2018)" (Introduction); z/distance D ~ 8.1 kpc  
  > "Observations of Sgr A$^{\ast}$ ($\alpha_\mathrm{J2000} = 17^\mathrm{h}45^\mathrm{m}40^\mathrm{s}.0361$, $\delta_\mathrm{J2000} = -29^\mathrm{\circ}00\mathrm{'}28\mathrm{''}.168$)" (3 Observations and data reduction); "at a distance $D \sim 8.1$ kpc (cite: Ghez_2008; Reid_2009; Gillessen_2009; Gravity_2018)" (Introduction); distance from Ghez 2008; Reid 2009; Gillessen 2009; Gravity 2018  
  > "Observations of Sgr A$^{\ast}$ ($\alpha_\mathrm{J2000} = 17^\mathrm{h}45^\mathrm{m}40^\mathrm{s}.0361$, $\delta_\mathrm{J2000} = -29^\mathrm{\circ}00\mathrm{'}28\mathrm{''}.168$)" (3 Observations and data reduction); "at a distance $D \sim 8.1$ kpc (cite: Ghez_2008; Reid_2009; Gillessen_2009; Gravity_2018)" (Introduction)
- Target **NRAO 530**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_
- Target **J1924-2914**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: _none stated_
- bands: _not stated_
- frequencies and spectral setup: 86 GHz; 256 MHz per polarization in 4 IFs of 116 channels each  
  > "We recorded a total bandwidth of 256 MHz per polarization divided in 4 intermediate frequencies (IFs) of 116 channels each." (3 Observations and data reduction)
- continuum bandwidth: _not stated_
- arrays: GMVA (8 VLBA, GBT, Yebes, IRAM 30m, Effelsberg) plus phased ALMA (37 antennas)  
  > "the ALMA phased array (AA) consisting of 37 phased antennas" (3 Observations and data reduction)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ~87 uas; uniform-weighted beam 235 x 87 uas, PA 53.6 deg  
  > "The (uniform-weighted) beam size of the Sgr A$^{\ast}$ observations is $(235 \times 87)$ $\mu$as, with a position angle (east of north) of 53.6$^\circ$." (5.1 Intrinsic source constraints from imaging)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: 5.76 h on Sgr A* with ALMA; 12 h track  
  > "The total integration time on Sgr A$^{\ast}$ with ALMA was 5.76 h." (3 Observations and data reduction)
- observing dates: 3 April 2017  
  > "The observations were conducted on 3 April 2017 as part of the first offered VLBI session with ALMA (project code MB007)." (3 Observations and data reduction)
- pi or archival as stated: _not stated_
- Other facility **GMVA (VLBA, GBT, Yebes, IRAM 30m, Effelsberg)**: VLBI stations observing together with phased ALMA  
  > "were made with the GMVA, composed of the eight Very Long Baseline Array (VLBA) antennas equipped with 86 GHz receivers" (3 Observations and data reduction)
- External data: J18 scattering model: kernel 1.380/0.703 lambda_cm^2 mas, PA 81.9 deg; alpha=1.38, r_in=800 km  
  > "with the major axis at a position angle $81.9^\circ \pm 0.2^\circ$ east of north (cite: Johnson_2018)" (2.2 Interstellar Scattering of Sgr A*) [from Johnson et al. 2018 (cite: Johnson_2018)]
- External data: GRMHD model images and KORAL simulations used for comparison  
  > "We also explored another set of 3D simulations from (cite: Chael_2018b)" (6.2 Constraints on accretion flow and jet models) [from Chael et al. 2018 (cite: Chael_2018b); Moscibrodzka 2009, 2014, 2016; Davelaar 2018]
- Simulation/model as data: Four 3D GRMHD snapshots at 86 GHz used for imaging tests  
  > "We tested our imaging method on four snapshots from 3D GRMHD simulations of Sgr A$^{\ast}$at 86 GHz" (4.2.3 Uncertainties of image-derived parameters)

## Processing

### Calibration

- pipeline or manual: HOPS fringe fitting with round-robin phase calibration; DiFX correlation  
  > "After correlation, reduction was carried out using the Haystack Observatory Postprocessing System[^1] (`HOPS`)" (3 Observations and data reduction)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: ALMA calibration provided by ALMA QA2 team; SEFDs from PolConvert  
  > "The calibration for ALMA was fully provided by the ALMA quality assurance (QA2) team" (3 Observations and data reduction)
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: Station gains from self-cal to closure-only calibrator images and to Gaussian (215x140 uas, PA 80 deg, 2.0 Jy) on <0.75 Glambda  
  > "we used a visibility function corresponding to a Gaussian source size of 215 by 140 $\mu$as with a position angle of 80$^\circ$ (east of north) and a total flux density of 2.0$\pm 0.2$ Jy" (4.2.1 Self-calibration)

### Imaging

- task: eht-imaging regularized maximum likelihood with stochastic optics scattering mitigation  
  > "We employ the `eht-imaging` library[^2], a regularized maximum likelihood imaging software package, to image our sources" (4 Imaging)
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
- final beam: (235 x 87) uas, PA 53.6 deg  
  > "The (uniform-weighted) beam size of the Sgr A$^{\ast}$ observations is $(235 \times 87)$ $\mu$as" (5.1 Intrinsic source constraints from imaging)
- final rms: _not stated_

### Inherited from earlier work

- Closure-only imaging of calibrators  
  > "We thus imaged both sources using only closure quantities, following the method from (cite: Chael_2018)" (4.1 Calibrators) [from Chael_2018]
- Stochastic optics scattering mitigation method  
  > "See (cite: Johnson_2016) for a more detailed description of the method." (4.2.2 Imaging with regularized maximum likelihood) [from Johnson_2016]
- Gaussian prior size from previous 3.5 mm experiments  
  > "we used the previously fitted Gaussian source as the prior" (4.2.2 Imaging with regularized maximum likelihood) [from previous 3.5 mm experiments (citation stripped in text)]

### Not stated but needed to reproduce (our reading)

- Final eht-imaging parameters (image size, pixel size, field of view, iterations, regularizer weights beyond 10%)
- Exact flagging and scan-averaging times
- Details of HOPS calibration scripts (in prep. reference)
- Flux scale uncertainty for ALMA
- Access to the correlated VLBI data (MB007 / 2016.1.00413.V) and its format
- Which previous experiments' Gaussian fit was used for second-moment constraint

## Analysis recipe

1. **Correlate and fringe-fit VLBI data**: DiFX correlation, HOPS fringe fitting with round-robin phase calibration  
  > "a round-robin calibration was used to avoid self-tuning" (3 Observations and data reduction)
   - software: DiFX, HOPS, PolConvert
   - parameter: median effective integration time 4.5 s  
  > "The median effective integration time was 4.5 seconds." (3 Observations and data reduction)
   - fitting: _not stated_
   - validation: cross-checks with AIPS  
  > "with additional validation and cross-checks from the NRAO Astronomical Image Processing System" (3 Observations and data reduction)
2. **Amplitude self-calibration of stations**: Self-cal to calibrator closure images and to Gaussian Sgr A* model on short baselines; flag NL and PT  
  > "We flagged the VLBA stations NL and PT, which showed extreme signal loss in both methods." (4.2.1 Self-calibration)
   - software: eht-imaging
   - assumption: Gaussian 215x140 uas, 2.0 Jy on baselines <0.75 Glambda  
  > "self-calibrated all Sgr A$^{\ast}$ visibility amplitudes within 0.75G$\lambda$" (4.2.1 Self-calibration)
   - fitting: _not stated_
   - validation: Two methods gave comparable gains  
  > "The two methods gave comparable gain solutions, hence validating the Gaussian assumption for short-baseline measurements" (4.2.1 Self-calibration)
3. **Image scattered and intrinsic Sgr A***: RML imaging with MEM, TV and second-moment regularizers (10% weight), then stochastic optics, two iterations with self-cal  
  > "Two iterations of stochastic imaging and self-calibration are done for convergence." (4.2.2 Imaging with regularized maximum likelihood)
   - software: eht-imaging, Stochastic Optics
   - parameter: J18 kernel 159.9 x 79.5 uas, PA 81.9 deg; alpha=1.38, r_in=800 km  
  > "we used the scattering kernel (with a size of (159.9 $\times$ 79.5) $\mu$as, PA of 81.9$^\circ$) and power spectrum (with $\alpha=1.38$ and $r_\mathrm{in}=800$ km)" (4.2.2 Imaging with regularized maximum likelihood)
   - fitting: gradient descent regularized maximum likelihood  
  > "This method is now included and implemented in the `eht-imaging library` via gradient descent minimization" (4.2.2 Imaging with regularized maximum likelihood)
   - validation: Synthetic data tests on four GRMHD snapshots  
  > "we performed imaging tests on simulated observations where the intrinsic model image was known" (4.2.3 Uncertainties of image-derived parameters)
4. **Measure source size and uncertainties**: Second-moment and 2D Gaussian LSQ fit to image; uncertainties from largest errors on simulated reconstructions; LSQ adopted  
  > "We adopt the LSQ method to quantify the size of Sgr A$^{\ast}$  via image-domain fitting." (4.2.3 Uncertainties of image-derived parameters)
   - software: eht-imaging
   - fitting: 2D Gaussian least squares  
  > "second by doing a 2D Gaussian fit with a least-squares minimization (LSQ) onto the image." (4.2.3 Uncertainties of image-derived parameters)
   - validation: Compared with historical measurements  
  > "We present the measured source sizes using our two methods ($2^\mathrm{nd}$ mom. and LSQ) in Table [3](#tab:sgra_size), along with historical measurements and estimates." (5.1 Intrinsic source constraints from imaging)
5. **Closure phases and refractive noise constraints; model comparison**: Weighted mean closure phases on three triangles; Monte Carlo refractive noise comparison of J18 and GS06; compare GRMHD model sizes and asymmetries  
  > "Following the Monte Carlo approach of , we find that combining baselines longer than $1.8\,{\rm G}\lambda$" (6.1 Constraints on the Refractive Scattering of Sgr A*)
   - software: KORAL
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **eht-imaging** : RML imaging and scattering mitigation  
  > "We employ the `eht-imaging` library" (4 Imaging)
- **HOPS** : VLBI post-correlation reduction and fringe fitting (fourfit)  
  > "reduction was carried out using the Haystack Observatory Postprocessing System" (3 Observations and data reduction)
- **DiFX** : correlation  
  > "using DiFX (cite: Deller_2011)" (3 Observations and data reduction)
- **PolConvert** : ALMA SEFDs  
  > "system equivalent flux densities (SEFDs) were generated with a high time cadence by `PolConvert`" (3 Observations and data reduction)
- **AIPS** : validation cross-checks  
  > "with additional validation and cross-checks from the NRAO Astronomical Image Processing System" (3 Observations and data reduction)
- **KORAL** : two-temperature radiative GRMHD simulations (from Chael 2018)  
  > "performed with the two-temperature, radiative GRMHD code `KORAL`" (6.2 Constraints on accretion flow and jet models)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Intrinsic major axis (LSQ) | 120 | 34 | uas | 4 | The unscattered source has a major axis size of $120 \pm 34\mu$as |
| Intrinsic axial ratio | 1.2 | +0.3/-0.2 | dimensionless | 4 | axial ratio of $1.2^{+0.3}_{-0.2}$ |
| Intrinsic minor axis (LSQ) | 100 | 18 | uas | 4 | This work (LSQ)$^*$ / $228 \pm 46$ / $143 \pm 20$ / $86 \pm 2$ / $1.6 \pm 0.3$ / $120 \pm 34$ / $100 \pm 18$ |
| Closure phase AA-GB-FD | -1.1 | 2.4 | deg | 5 | the weighted mean closure phase on AA-GB-FD is $-1.1 \pm 2.4^\circ$ |
| Mean debiased amplitude on baselines >1.8 Glambda | 6 | not stated | mJy | 5 | on baselines longer than 1.8 G$\lambda$ is 6 mJy |

## Qualitative findings

- GS06 scattering model is ruled out; refractive scattering likely weak for EHT 1.3 mm images  
  > "Thus, this model for the scattering of Sgr A$^{\ast}$ is conclusively ruled out by our observations." (7 Summary)

## Claim tuples

- H: Sgr A* intrinsic structure at 3.5 mm is symmetric and compact | E: RML imaging with stochastic optics of GMVA+ALMA data | R: Major axis 120±34 uas, axial ratio 1.2, closure phases consistent with zero | F: Intrinsic source is nearly symmetric | **supported**
- H: Disk or jet models match the constraints | E: Compare GRMHD model sizes, asymmetry, and closure phases | R: Hybrid disks and jets at small inclination match | F: Jet models restricted to small viewing angles | **supported**
- H: Refractive scattering strength discriminates GS06 from J18 | E: Compare long-baseline ALMA correlated flux with predictions | R: GS06 predicts 60 mJy vs observed 3-18 mJy range | F: GS06 ruled out | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: AIPS and Difmap not used for imaging because lacking flexibility for unscattered images  
  > "standard imaging software packages like `AIPS` (cite: Greisen_2003) or `Difmap` (cite: Shepherd_1995) do not offer the flexibility and necessary tools" (4 Imaging)
- How they decided it was enough: _not stated_
- Limitation (authors): Single epoch cannot separate refractive noise from intrinsic substructure; VLBA performance poor  
  > "using our single observation with ALMA, we cannot conclusively determine whether those detections are entirely due to refractive noise" (7 Summary)
- Caveat (inferred, ours): Uncertainties derived from only four simulated models
- Caveat (inferred, ours): Gaussian assumption for short baselines drives gain calibration
- Caveat (inferred, ours): Position angle unconstrained
- Caveat (inferred, ours): Model comparison does not involve parameter fitting

## Reproducibility

- Data public (paper): ALMA data cited as ADS/JAO.ALMA2016.1.00413.V  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA2016.1.00413.V." (Acknowledgments)
- Products in archive: _not stated_
- Code: eht-imaging is public on GitHub; second-moment regularizer now included  
  > "This method is now included and implemented in the `eht-imaging library` via gradient descent minimization" (4.2.2 Imaging with regularized maximum likelihood)
- Missing: Full eht-imaging script and parameters
- Missing: Calibrated VLBI visibilities
- Missing: HOPS calibration scripts details (in prep.)
- Data volume (inferred): VLBI correlated data; likely tens of GB raw, small after averaging
- Score (inferred): 3/5, Methods well described qualitatively, but key imaging parameters and calibrated data are not provided and VLBI data are specialized.
- Rediscovery candidate: no, VLBI calibration and imaging recipe incomplete and data access non-trivial.

## Links

- Method: Chael et al. 2016, 2018 (eht-imaging) (imaging library and closure-only method)
- Method: Johnson 2016 (stochastic optics scattering mitigation)
- Companion: Johnson et al. 2018 (J18 scattering model)
- Companion: Issaoun et al. 2018, in prep. (second-moment regularizer)
- Related: Global Millimeter VLBI Array
- Related: Event Horizon Telescope

## Checks

```json
{
 "quotes": 58,
 "quotes_ok": 58,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 0,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2016.1.00413.V"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 84,
  "stated": 46,
  "rate": 0.548
 },
 "evidence_ok": true
}
```
