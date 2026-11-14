# ALMA unveils rings and gaps in the protoplanetary system <ASTROBJ>HD 169142</ASTROBJ>: signatures of two giant protoplanets

`2017A&A...600A..72F` | Astronomy and Astrophysics 2017 | first author: Fedele, D. | arXiv: 1702.02844 | DOI: 10.1051/0004-6361/201629860

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks
- Question: What are the gas and dust surface density structures of HD 169142 (cavity, gap, rings), and do they indicate planets shaping the disk?  
  > "From these observations we place more stringent constraints on the dust and gas density structures." (Introduction)
- Target **HD 169142**: coordinates 18h24m29.776s, -29d46m49.900s (J2000)  
  > "HD 169142 (J2000: R.A. = 18$^{\rm{h}}$24$^{\rm{m}}$29.776$^{\rm{s}}$, DEC = –29$^\circ$46$\ensuremath{'}$49.900$\ensuremath{''}$)" (3 Observations and data reduction); "The most recent measurement of the parallax is $\varpi = 8.53 \pm 0.29$ mas (cite: Brown16) which translates to a distance $d = 117 \pm 4\,$pc." (HD 169142); z/distance 117 ± 4 pc  
  > "HD 169142 (J2000: R.A. = 18$^{\rm{h}}$24$^{\rm{m}}$29.776$^{\rm{s}}$, DEC = –29$^\circ$46$\ensuremath{'}$49.900$\ensuremath{''}$)" (3 Observations and data reduction); "The most recent measurement of the parallax is $\varpi = 8.53 \pm 0.29$ mas (cite: Brown16) which translates to a distance $d = 117 \pm 4\,$pc." (HD 169142); distance from Gaia parallax (Brown16)  
  > "HD 169142 (J2000: R.A. = 18$^{\rm{h}}$24$^{\rm{m}}$29.776$^{\rm{s}}$, DEC = –29$^\circ$46$\ensuremath{'}$49.900$\ensuremath{''}$)" (3 Observations and data reduction); "The most recent measurement of the parallax is $\varpi = 8.53 \pm 0.29$ mas (cite: Brown16) which translates to a distance $d = 117 \pm 4\,$pc." (HD 169142)

## Data provenance

- ALMA projects: 2013.1.00592.S
- bands: Band 6 (211–275 GHz)  
  > "with the Atacama Large Millimeter Array (ALMA) in band 6 (211–275 GHz)" (3 Observations and data reduction)
- frequencies and spectral setup: USB: 233 GHz TDM continuum (2 GHz) and 12CO FDM (0.040 km/s); LSB: 13CO and C18O FDM (0.084 km/s)  
  > "The upper sideband (USB) contained two spectral windows." (3 Observations and data reduction); "Each observed LSB line had a frequency (velocity) resolution of 61.0 kHz (0.084 km s$^{-1}$)." (3 Observations and data reduction)
- continuum bandwidth: 2 GHz centered at 233 GHz  
  > "with 2 GHz bandwidth centered at 233 GHz" (3 Observations and data reduction)
- arrays: _not stated_
- configurations: _not stated_
- baselines: 13 – 1445 m  
  > "13 – 1445 m" (Table 1)
- angular resolution: ~0.2''-0.3''  
  > "35 antennas were used to achieve a spatial resolution of $\sim 0.2\ensuremath{''} - 0.3\ensuremath{''}$" (3 Observations and data reduction)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: 50 minutes  
  > "for 50 minutes total on-source" (3 Observations and data reduction)
- observing dates: 2015 August 30  
  > "Dates Observed | 2015 August 30" (Table 1)
- pi or archival as stated: _not stated_
- Line: 12CO J=2-1 (230.538 GHz)
- Line: 13CO J=2-1 (220.39868 GHz)
- Line: C18O J=2-1 (219.56035 GHz)
- Other facility **VLT/NaCo**: H-band polarimetric differential imaging image for comparison  
  > "The NaCo H-band PDI image is shown in Figure [1](#fig:cont)" (4.1 Dust continuum emission)
- External data: Stellar distance from Gaia parallax 8.53 mas (117 pc)  
  > "$\varpi = 8.53 \pm 0.29$ mas (cite: Brown16)" (HD 169142) [from (cite: Brown16)]
- External data: Disk inclination 13 deg and PA 5 deg from SMA  
  > "measured a disk inclination of 13$^{\circ}$ and a position angle of 5$^{\circ}$ (cite: Raman06; Panic08)" (HD 169142) [from (cite: Raman06; Panic08)]
- External data: Dust mass absorption coefficient k = 2 cm2/g at 230 GHz  
  > "$k_{\nu}$ = 2 (cm$^{2}$  g$^{-1}$) the mass absorption coefficient at 230 GHz (cite: Beckwith90)" (4.1 Dust continuum emission) [from (cite: Beckwith90)]
- External data: Stellar mass 1.65 Msun  
  > "$M_{\star} = 1.65\,M_{\odot}$ (cite: Blondel06)" (HD 169142) [from (cite: Blondel06)]
- Simulation/model as data: DALI thermo-chemical model grid compared to the observations  
  > "We created a grid of disk models varying the most relevant geometrical and physical parameters" (5.3 Model grid)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Ceres (1.941 Jy LSB, 2.165 Jy USB); J1924-2914 bandpass; J1812-2836 gain  
  > "Calibration was done with $J1924-2914$ as the delay and bandpass calibrator, J1812-2836 as the gain calibrator, and Ceres as the flux calibrator." (3 Observations and data reduction)
- flux scale uncertainty: 10%  
  > "Flux calibration accuracy is taken to be 10%." (Table 1)
- self calibration: Two phase and one amplitude; first phase solint 300 s; reference antenna DA59; solutions from TDM window applied to FDM windows  
  > "Calibration solutions were calculated twice for phase and once for amplitude." (3 Observations and data reduction)

### Imaging

- task: CLEAN in CASA  
  > "Data reduction was performed with the Common Astronomy Software Applications (CASA, (cite: Mcmullin07))." (3 Observations and data reduction)
- deconvolver: _not stated_
- weighting robust: Continuum: Briggs robust=0.5 adopted (also uniform, superuniform tried); lines: natural  
  > "For the lines CLEAN imaging was done with natural weighting." (3 Observations and data reduction)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: uv-space single-order polynomial fit to line-free channels  
  > "Continuum subtraction of the line data was done in $uv-$space based on a single-order polynomial fit to all line-free channels in each spectral window." (3 Observations and data reduction)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: Channel maps resampled to 0.160 (12CO) and 0.168 km/s (13CO, C18O) with Hanning smoothing  
  > "the velocity resolution is resampled to 0.160 km s$^{-1}$ ($^{12}$CO) and 0.168 km s$^{-1}$($^{13}$CO and C$^{18}$O) with Hanning smoothing" (Channel maps)
- final beam: Continuum 0.28'' x 0.18'' PA -77.9 deg  
  > "0.28$''$ $\times$ 0.18$''$" (Table 1)
- final rms: Continuum 0.07 mJy/beam  
  > "r.m.s. noise \[mJy beam$^{-1}$\] | 0.07" (Table 1)

### Inherited from earlier work

- Two-population dust settling prescription (size ranges modified)  
  > "Following (cite: dAlessio06), the settling of the large dust particles is implemented adopting two different power-law grain size populations" (5.1 Disk model description) [from (cite: dAlessio06)]
- Dust opacities  
  > "Dust mass absorption cross sections are from (cite: Andrews11)." (5.1 Disk model description) [from (cite: Andrews11)]
- Isotope selective photodissociation  
  > "Isotope selective photodissociation is included in the chemistry as described in (cite: Miotello14)." (5.1 Disk model description) [from (cite: Miotello14)]

### Not stated but needed to reproduce (our reading)

- CASA version
- Line-free channel ranges
- Clean threshold, masks, cell and image size
- Self-cal solint for amplitude in explicit seconds and SNR thresholds
- Fitting metric/likelihood and weighting for grid comparison
- Grid fit is by-eye/minimum difference, no uncertainties
- Dust and gas temperature/DALI input details like cosmic-ray rate, PAH, inner-ring settings
- SED data used in fit

## Analysis recipe

1. **Self-calibrate and image continuum and CO lines**: Self-cal on continuum TDM window applied to line windows; uv continuum subtraction; CLEAN  
  > "Self-calibration solutions from the TDM spectral window were cross-applied to each FDM spectral window." (3 Observations and data reduction)
   - software: CASA
   - parameter: Briggs robust 0.5 continuum; natural weighting lines  
  > "Briggs, robust = 0.5" (Table 1)
   - fitting: _not stated_
   - validation: _not stated_
2. **Dust mass upper limits in cavity and gap**: Optically thin dust mass formula with 3 sigma flux upper limit over gap area  
  > "The flux density upper limit is computed adopting a constant flux of $2.1 \times 10^{-4}$ Jy beam$^{-1}$ (i.e., 3 $\times$ r.m.s.) over the entire gap area." (4.1 Dust continuum emission)
   - assumption: k=2 cm2/g at 230 GHz; Tdust gap 50 K, cavity 150 K  
  > "We assume $T_{\rm dust, gap} = 50\,$K (see Fig. [5](#fig:dali))." (4.1 Dust continuum emission)
   - fitting: _not stated_
   - validation: _not stated_
3. **Model gas and dust surface density with DALI grid**: Grid of DALI models; synthetic visibilities via simobserve and clean; observed radial profiles and SED compared to grid; fiducial = parameter set minimising difference  
  > "The fiducial model is defined by the set of parameters that minimise the difference between observations and model grid within the explored parameter space." (5.3 Model grid)
   - software: DALI, CASA
   - parameter: Free parameters psi, gamma, h_c, R_c, Delta_gd, Sigma_c, radii and depletion factors, ranges in Table  
  > "Table [\[tab:dali\]](#tab:dali) lists the definition, range and step size of the different parameters." (5.3 Model grid)
   - assumption: Teff 8400 K blackbody, L=10 Lsun, d=117 pc, i=13 deg, PA=5 deg, chi=f_large=0.2, [C]/[H]=2.4e-4  
  > "for the adopted standard carbon abundance of \[C\]/\[H\]=$2.4 \times 10^{-4}$" (5.4 Fiducial model)
   - fitting: Grid search varying one parameter at a time, no sampler  
  > "where we vary one parameter at a time" (Model grid)
   - validation: Residual images in uv-plane and radial profiles along major/minor axes  
  > "Figure [6](#fig:model) shows (from left to right) the ALMA observations (continuum or line integrated map), synthetic observations and residual images (computed in the $uv$-plane)" (5.4 Fiducial model)

## Software

- **CASA** : Calibration, imaging, simobserve for synthetic observations  
  > "For this task we used the CASA tools SIMOBSERVE and CLEAN." (5.3 Model grid)
- **DALI** : Thermo-chemical disk modelling  
  > "The simulations presented here were generated using the thermo-chemical disk code DALI" (5.1 Disk model description)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Dust mass upper limit in gap | ~0.3 | not stated | Earth masses | 2 | This corresponds to a dust mass 3 $\sigma$ upper limit of $\sim$ 0.3 M$_{\oplus}$. |
| Dust mass upper limit in cavity | ~1e-2 | not stated | Earth masses | 2 | is $\sim 10^{-2}$ M$_{\oplus}$ |
| Total dust mass | 1e-4 | not stated | Msun | 3 | The total dust mass is $1 \times 10^{-4}\,$M$_{\odot}$. |
| Total gas mass | 1.9e-2 | not stated | Msun | 3 | The total gas mass is $1.9 \times 10^{-2}\,$M$_{\odot}$ |
| Gas surface density reduction inward of dust gap | 30-40 | not stated | dimensionless | 3 | The gas surface density inward of the dust gap is decreased by a factor of $\sim$ 30 – 40 |
| Gas inner radius | 13 | not stated | au | 3 | down to an inner radius of $\sim 13\,$au |
| Outer gas radius | 180 | not stated | au | 3 | The outer gas radius of 180 au is set by the steep drop of the C$^{18}$O emission at large radii. |
| Inner ring dust depletion factor | ~3.7 | not stated | dimensionless | 3 | The inner ring is decreased by a factor of $\sim 3.7$ (=$1/\delta_{\rm dust}$) |
| Integrated continuum flux | 232 | 23 | mJy | 1 | 232$\pm$23 |

## Qualitative findings

- Dust is in two rings (20-35 au and 56-83 au) with no dust in cavity or gap, while gas is present inside and extends to ~180 au, indicating radial drift and decoupling  
  > "gas and dust in HD 169142 are physically decoupled with the dust particles concentrated in two rings between $\sim 20 - 35$ au and $\sim 56-83$ au." (7 Conclusions)

## Claim tuples

- H: Are the dust cavity and gap real dust depletions with gas remaining? | E: 1.3 mm continuum and CO isotopologue imaging plus DALI modelling | R: No dust above noise in cavity/gap; gas reduced by 30-40 inward of the gap | F: Gas filled gap and cavity with depleted surface density | **supported**
- H: Do the structures indicate multiple giant planets? | E: Compare gas/dust structures and absence of asymmetries with planet-disk theory | R: Inferred planet masses ~0.1-1 MJup inner and ~1-10 MJup outer | F: Two giant planets most likely scenario; MRI dead zone plus wind alternative not excluded | **partially**
- H: Does the dust disk being smaller than the gas disk imply radial drift? | E: Compare continuum and CO radial extents | R: Dust edge at 83 au, gas to ~180 au | F: Sharp dust edge hints at radial drift | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Multiple CO isotopologues with different optical depths allow detection of small gas amounts in the gap  
  > "thanks to the different optical depths, the spatially resolved channel maps of the three isotopologues allows us to detect and quantify the very small amount" (7 Conclusions)
- Alternative: MRI dead zones with photoevaporation or MHD wind could also explain the structure  
  > "An alternative scenario that could also explain the surface density profile of HD 169142 is the case of magneto-rotational (MRI) instability creating dead-zones" (6 Discussion)
- How they decided it was enough: _not stated_
- Limitation (authors): Azimuthal asymmetries are low significance (<~3 sigma); model 13CO flux underestimated ~10%  
  > "The significance of the asymmetric emission along the minor axis (continuum and C$^{18}$O) is low ($\lesssim 3\sigma$)" (4.3 Disk surface density)
- Caveat (inferred, ours): Grid fit has no formal uncertainties or degeneracy exploration
- Caveat (inferred, ours): Coarse parameter steps
- Caveat (inferred, ours): Fixed dust opacity and gas-to-dust ratio assumptions affect masses
- Caveat (inferred, ours): Resolution (~35 au) limits gap and cavity constraints
- Caveat (inferred, ours): Planet mass inferences are qualitative

## Reproducibility

- Data public (paper): ALMA data from project 2013.1.00592.S cited in acknowledgements  
  > "This paper makes use of the following ALMA data: ADS$/$JAO.ALMA$\#$2013.1.00592.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: CASA version and clean parameters
- Missing: DALI full input setup and fit metric
- Missing: line-free channels
- Data volume (inferred): ~20-50 GB single execution block
- Score (inferred): 3/5, Single public dataset with reasonable imaging description but modelling setup and fit criteria are underspecified.
- Rediscovery candidate: no, Main results depend on a DALI model grid without full specification; some numbers (ring/gap radii) are reproducible from imaging.

## Links

- Method: (cite: Bruderer12; Bruderer13) (DALI code)
- Method: (cite: Miotello14) (isotope selective photodissociation in chemistry)
- Companion: (cite: Quanz13; Momose15) (H-band polarimetric imaging compared with ALMA)

## Checks

```json
{
 "quotes": 66,
 "quotes_ok": 66,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 9,
 "numeric_problems": 0,
 "fill": {
  "facts": 70,
  "stated": 45,
  "rate": 0.643
 },
 "evidence_ok": true
}
```
