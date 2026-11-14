# A highly non-Keplerian protoplanetary disc. Spiral structure in the gas disc of CQ Tau

`2021A&A...648A..19W` | Astronomy and Astrophysics 2021 | first author: Wölfer, L. | arXiv: 2012.04680 | DOI: 10.1051/0004-6361/202039469

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks
- Question: Are there substructures (spirals) in the gas brightness temperature and kinematics of the CQ Tau transition disc that trace a perturber such as an embedded planet or companion?  
  > "we aim to analyze the gas brightness temperature and kinematics of the transitional disc around the intermediate mass star CQ Tau in order to resolve and characterize substructure in the gas" (abstract)
- Target **CQ Tau**: coordinates RA 05h35m58.47s, Dec +24d44m54.09s (J2000)  
  > "located in the Taurus star forming region at a distance of $\sim 162\,\mathrm{pc}$ (cite: Gaia2018)" (2.1 Target); "$(\mathrm{RA} = 05^{\mathrm{h}}$:35$^{\mathrm{m}}:58.47^{\mathrm{s}}$, $\mathrm{Dec} = +24\degree:44':54.09'', \mathrm{J}2000)$" (2.1 Target); z/distance ~162 pc  
  > "located in the Taurus star forming region at a distance of $\sim 162\,\mathrm{pc}$ (cite: Gaia2018)" (2.1 Target); "$(\mathrm{RA} = 05^{\mathrm{h}}$:35$^{\mathrm{m}}:58.47^{\mathrm{s}}$, $\mathrm{Dec} = +24\degree:44':54.09'', \mathrm{J}2000)$" (2.1 Target); distance from Gaia (Gaia2018)  
  > "located in the Taurus star forming region at a distance of $\sim 162\,\mathrm{pc}$ (cite: Gaia2018)" (2.1 Target); "$(\mathrm{RA} = 05^{\mathrm{h}}$:35$^{\mathrm{m}}:58.47^{\mathrm{s}}$, $\mathrm{Dec} = +24\degree:44':54.09'', \mathrm{J}2000)$" (2.1 Target)

## Data provenance

- ALMA projects: 2013.1.00498.S, 2016.A.00026.S, 2017.1.01404.S
- bands: Band 6 (1.3 mm)  
  > "We present 1.3 mm ALMA observations of the CQ Tau system in band 6" (2.2 Data reduction)
- frequencies and spectral setup: Channel widths 500, 700, 1000 m/s for 12CO, 13CO, C18O; intrinsic 244/488/488 kHz  
  > "| $^{13}$CO | 488 | 700 | 0.128 | 0.103 | 7.676 | 1.0e-3 |" (Table 1)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: C34-6, C40-7, C43-8  
  > "| 1 | 2013.1.00498.S | 30 Aug 2015 | C34-6 | 20 - 1091 | 35 | 15.12 |" (ALMA observing log); "| 2 | 2016.A.00026.S | 07 Aug 2017 | C40-7 | 81 - 3700 | 40 | 19.66 |" (ALMA observing log)
- baselines: 20-1091 m, 81-3700 m, 92-8500 m  
  > "The longest baseline from the first project extends to 1091 m, while for the latest two it is increased to 3700 m and 8500 m respectively" (2.2 Data reduction)
- angular resolution: 12CO beam 0.121" x 0.098"; 13CO 0.128" x 0.103"; C18O 0.129" x 0.103"  
  > "| $^{12}$CO | 244 | 500 | 0.121 | 0.098 | 8.004 | 1.2e-3 |" (Table 1)
- max recoverable scale: _not stated_
- sensitivity: channel rms 1.2e-3 (12CO), 1.0e-3 (13CO), 0.7e-3 (C18O) Jy/beam  
  > "| C$^{18}$O | 488 | 1000 | 0.129 | 0.103 | 8.814 | 0.7e-3 |" (Table 1)
- time on source: 15.12, 19.66, 28.73 (x2) min per execution  
  > "|  |  | 23 Nov 2017 | C43-8 | 92 - 8500 | 48 | 28.73 |" (ALMA observing log)
- observing dates: 30 Aug 2015; 07 Aug 2017; 20 and 23 Nov 2017  
  > "| 3 | 2017.1.01404.S | 20 Nov 2017 | C43-8 | 92 - 8500 | 44 | 28.73 |" (ALMA observing log)
- pi or archival as stated: _not stated_
- Line: 12CO J=2-1 (not stated)
- Line: 13CO J=2-1 (not stated)
- Line: C18O J=2-1 (not stated)
- Other facility **Keck/NIRC2 and Subaru/AO188+HiCIAO**: NIR scattered-light spiral compared with the gas spirals (Uyama2019)  
  > "the data reveal the presence of a small spiral seen in small dust grains on scales of 30-60 au, that might be induced by a companion candidate." (2.1 Target)
- External data: DALI thermochemical model of CQ Tau used to test beam dilution  
  > "we have used the DALI (Dust And LInes (cite: Bruderer2012; Bruderer2013)) model presented by (cite: Gabellini2019)" (3.1 Integrated and peak brightness temperature maps) [from Gabellini2019]
- External data: Inclination 35 deg and distance 162 pc fixed in the thin disc models  
  > "we fixed the object’s distance and inclination to 162 pc and 35 $\degree$ ((cite: Gabellini2019)) respectively" (4.2.2 Razor-thin disc model) [from Gabellini2019]
- External data: NIR spiral fit (r = a + b phi^n; pitch angle ~34 deg)  
  > "The pitch angle of the NIR spiral, which is given as $\sim 34\,\degree$" (4.3 Analysis of the spiral structure) [from Uyama2019]
- Simulation/model as data: DALI model convolved with the observing beam to test beam dilution  
  > "convolved the spectral image cubes with the beam of our observation." (3.1 Integrated and peak brightness temperature maps)

## Processing

### Calibration

- pipeline or manual: ALMA standard pipeline, then DSHARP-like processing  
  > "After applying ALMA standard pipeline calibration, we follow a similar processing as for the DSHARP data calibration (cite: Andrews2018), using `CASA 5.4.1`." (2.2 Data reduction)
- casa version: CASA 5.4.1  
  > "using `CASA 5.4.1`" (2.2 Data reduction)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: Short-baseline data: 3 phase-only (300, 120, 30 s) + 1 amplitude (whole observation); then combined: 4 phase (900, 360, 150, 90 s) + 1 amplitude (360 s)  
  > "by applying three steps of phase-only calibration using solution intervals of $300$, $120$ and $30\,$s, and one step of amplitude calibration using the whole observation time range as a solution interval." (2.2 Data reduction); "four phase calibrations with solution intervals of $900$, $360$, $150$, $90\,$s, as well as one amplitude calibration with solution interval of $360\,$s." (2.2 Data reduction)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: robust = 0.6  
  > "using a robust parameter of $0.6$ and Keplerian masking. This value was found to give the best trade off between spatial resolution and sensitivity." (2.2 Data reduction)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: Keplerian mask (keplerian_mask): i=35, PA=235, d=162 pc, M*=1.54 Msun, vsys=6.17 km/s, radii 0-2", convolved with 1.5x beam  
  > "We further choose an inner and outer radius of 0 and 2$''$ respectively and convolve with the beam rescaled by 1.5 times its size." (2.2 Data reduction)
- multiscale scales: _not stated_
- continuum subtraction: uvcontsub task  
  > "The continuum emission is subtracted using the `uvcontsub` task" (2.2 Data reduction)
- line free channels: Channels within ±25 km/s of each line flagged to form continuum, averaged to 125 MHz  
  > "We start by flagging the channels located at $\pm 25\,\mathrm{km}\,\mathrm{s}^{-1}$ from each spectral line, and average the remaining channels to 125 MHz width channels" (2.2 Data reduction)
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.121x0.098" (12CO), 0.128x0.103" (13CO), 0.129x0.103" (C18O)  
  > "| $^{12}$CO | 244 | 500 | 0.121 | 0.098 | 8.004 | 1.2e-3 |" (Table 1)
- final rms: 1.2e-3, 1.0e-3, 0.7e-3 Jy/beam per channel  
  > "| $^{13}$CO | 488 | 700 | 0.128 | 0.103 | 7.676 | 1.0e-3 |" (Table 1)

### Inherited from earlier work

- Calibration/processing follows DSHARP data calibration  
  > "we follow a similar processing as for the DSHARP data calibration (cite: Andrews2018)" (2.2 Data reduction) [from (cite: Andrews2018)]
- Subtraction of azimuthally averaged radial TB profile to reveal spirals  
  > "similar to (cite: Teague2019Spiral) we subtract an azimuthally averaged radial $T_{\mathrm{B}}$ profile" (4.1 Temperature structure) [from (cite: Teague2019Spiral)]
- Datasets previously presented at lower resolution  
  > "previously presented at a lower angular resolution in (cite: Gabellini2019)" (2.2 Data reduction) [from (cite: Gabellini2019)]

### Not stated but needed to reproduce (our reading)

- Rest frequencies and spectral window layout
- Line-free channel ranges for uvcontsub and its fit order
- Cell size, image size, clean threshold and number of iterations
- Flux calibrator and flux-scale uncertainty
- Details of how continuum alignment/centroid shifts were done
- bettermoments settings (mask, fit method options)
- Details of the by-eye spiral parameterization
- Whether DALI model post-processing details are reproducible

## Analysis recipe

1. **Calibrate, self-calibrate and image**: Pipeline calibration, DSHARP-like continuum self-cal, applied to lines, uvcontsub, tclean-style cubes with robust 0.6 and Keplerian mask  
  > "All the dust continuum emission calibration steps, including the centroid shifting and self-calibration tables, are then applied to the molecular line emission channels." (2.2 Data reduction)
   - software: CASA 5.4.1, keplerian_mask
   - parameter: robust = 0.6  
  > "using a robust parameter of $0.6$ and Keplerian masking." (2.2 Data reduction)
   - fitting: _not stated_
   - validation: Flux calibration of each execution checked for consistency  
  > "check by comparison the flux calibration of each individual execution, to ensure they all have the same flux." (2.2 Data reduction)
2. **Make integrated and peak intensity maps**: bettermoments moment-0 (Keplerian-masked) and peak maps, converted to Kelvin via Planck law  
  > "we have used the `bettermoments` code described in (cite: bettermoments) and then converted from flux density units to units of Kelvin with the Planck law." (3.1 Integrated and peak brightness temperature maps)
   - software: bettermoments
   - assumption: 12CO optically thick and LTE so TB traces kinetic temperature  
  > "Since the $^{12}$CO emission is optically thick and in LTE at these low rotational transitions" (4.1 Temperature structure)
   - fitting: _not stated_
   - validation: Beam dilution tested with convolved DALI model  
  > "Thus, beam dilution can mostly account for the strong under-brightness seen in the data." (3.1 Integrated and peak brightness temperature maps)
3. **Radial and azimuthal profiles**: Deprojected with i=35, PA=235; azimuthal profile of ring 0.12-0.25"; radial profile in 0.02" annuli  
  > "The curves are obtained from the azimuthally averaged intensity per annuli of size $0.02'' (\sim 3.2\,\mathrm{au})$ from the peak intensity maps" (3.2 Radial and azimuthal cuts)
   - fitting: _not stated_
   - validation: _not stated_
4. **Temperature residual spirals**: Subtract azimuthally averaged radial TB profile from 12CO peak TB map  
  > "This leaves significant spiral structure in the resulting residuals as shown in [Fig. [4]" (4.1 Temperature structure)
   - fitting: _not stated_
   - validation: _not stated_
5. **Extract rotation velocity map**: bettermoments quadratic fit to brightest pixel and two neighbours; mask below 4 sigma (12CO) and 3.5 sigma (13CO, C18O)  
  > "The code fits a quadratic model to the brightest pixel as well as the two neighbouring pixels to find the centroid of the line in pixel coordinates." (4.2 Velocity structure)
   - software: bettermoments
   - parameter: masking below 4 sigma for 12CO and 3.5 sigma for 13CO and C18O  
  > "masking regions below 4 $\sigma$ for $^{12}$CO and 3.5 $\sigma$ for $^{13}$CO and C$^{18}$O" (4.2 Velocity structure)
   - fitting: _not stated_
   - validation: _not stated_
6. **Fit razor-thin Keplerian model to velocity map**: eddy fit of Keplerian rotation with free x0, y0, PA, vLSR, M*; i=35 and d=162 pc fixed; residuals from run 2 used; models for full disc, inner, outer, annuli  
  > "fitted for the disc centre $(x_0, y_0 \in \{-0.5'',0.5''\})$, systemic velocity $(v_{\mathrm{LSR}} \in \{-5\,\mathrm{km}\,\mathrm{s}^{-1},20\,\mathrm{km}\,\mathrm{s}^{-1}\})$" (4.2.2 Razor-thin disc model)
   - software: eddy, scipy.optimize, MCMC sampler
   - parameter: 200 walkers, 5000 burn-in steps, 5000 sampling steps  
  > "we used 200 walkers, 5000 steps to burn in and 5000 additional steps to sample the posterior distribution function." (4.2.1 Analysis of the gas rotation velocity)
   - assumption: Razor-thin disc, distance 162 pc, inclination 35 deg  
  > "we fixed the object’s distance and inclination to 162 pc and 35 $\degree$" (4.2.2 Razor-thin disc model)
   - fitting: Flat wide priors; scipy.optimize start then MCMC; uncertainties 16th-84th percentiles  
  > "For all of our models we assumed flat priors that were allowed to vary over a wide range." (4.2.1 Analysis of the gas rotation velocity)
   - validation: Run with velocity errors x10 and with/without beam convolution gave comparable results; uncertainties likely underestimated due to systematics  
  > "We tried both convolving the models with the beam of the observation and not using the convolution, with both approaches returning comparable results." (4.2.2 Razor-thin disc model)
7. **Velocity residuals and spiral parameterization**: Subtract best-fit model (run 2), mask inside 1.5 beam FWHM; fit linear and logarithmic spirals by eye; compute pitch angle tan(beta)=|dr/dphi|/r  
  > "we calculate the pitch angle $\beta$ for all three spirals." (4.3 Analysis of the spiral structure)
   - assumption: Spirals assumed trailing for sense of rotation  
  > "suggesting a counter-clockwise rotation of the disc if the spirals are trailing" (4.3 Analysis of the spiral structure)
   - fitting: By-eye parameterization, no actual fit  
  > "(keeping in mind an uncertainty due to the by-eye parameterization)" (4.3 Analysis of the spiral structure)
   - validation: Compared with NIR spiral of Uyama2019 and with 13CO/C18O residuals  
  > "The NIR spiral matches the anchoring point of the temperature spirals and follows the course of Sp$_\mathrm{T2}$ at the inner edge" (4.3 Analysis of the spiral structure)

## Software

- **CASA** 5.4.1: Calibration, self-calibration, uvcontsub, imaging  
  > "using `CASA 5.4.1`" (2.2 Data reduction)
- **keplerian_mask** : Keplerian masks for cleaning and moment maps  
  > "The Keplerian mask is calculated with the package `keplerian_mask`" (2.2 Data reduction)
- **bettermoments** : Integrated, peak intensity and line-centroid velocity maps  
  > "The `bettermoments` package can also be used to generate the observed rotation velocity of the gas" (4.2 Velocity structure)
- **eddy** : Keplerian fits to the rotation map  
  > "to the rotation map of $^{12}$CO shown in [Fig. [5](#fig:velocitymaps)](#fig:velocitymaps) using the `eddy` code (cite: eddy)." (4.2.1 Analysis of the gas rotation velocity)
- **scipy.optimize** : Optimising starting positions of fit parameters  
  > "the starting positions of the free fit parameters are optimized with `scipy.optimize`" (4.2.1 Analysis of the gas rotation velocity)
- **DALI** : Model cubes convolved to test beam dilution  
  > "To test for this effect we have used the DALI (Dust And LInes (cite: Bruderer2012; Bruderer2013)) model" (3.1 Integrated and peak brightness temperature maps)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Stellar mass, run 2 best fit | 1.570 | 0.002 | Msun | 6 | / 2            / 0.25                       / 1.0                         / 0.0072 $\pm$ 0.0003 / 0.0273 $\pm$ 0.0003 / 234.58 $\pm$ 0.03 / 6172.9 $\pm$ 0.8                  / 1.570 $\pm$ 0.002     /   / |
| Stellar mass range across runs | 1.47 to 1.65 | not stated | Msun | 6 | The largest scatter is found for the stellar mass $M_*$, that is ranging from 1.47 to 1.65 M$_{\odot}$ |
| Systemic velocity, run 2 | 6172.9 | 0.8 | m/s | 6 | / 2            / 0.25                       / 1.0                         / 0.0072 $\pm$ 0.0003 / 0.0273 $\pm$ 0.0003 / 234.58 $\pm$ 0.03 / 6172.9 $\pm$ 0.8                  / 1.570 $\pm$ 0.002     /   / |
| Position angle, run 2 | 234.58 | 0.03 | deg | 6 | / 2            / 0.25                       / 1.0                         / 0.0072 $\pm$ 0.0003 / 0.0273 $\pm$ 0.0003 / 234.58 $\pm$ 0.03 / 6172.9 $\pm$ 0.8                  / 1.570 $\pm$ 0.002     /   / |
| Peak SNR of 12CO integrated intensity | 40 | not stated | dimensionless | 2 | This results in a peak SNR of 40 for the $^{12}$CO, 20 for the $^{13}$CO and 14 for the C$^{18}$O velocity integrated intensity |
| Peak intensity drop at minor-axis dips | 35-60 | not stated | percent | 2 | we clearly note a drop of the peak intensity of all isotopologues and integrated intensity of C$^{18}$O by roughly 35-60 % (with respect to the peak) |
| C18O radial intensity dip at 65-85 au | about 3 | not stated | percent | 3 | we notice a drop of the peak intensity in the radial profile of C$^{18}$O between $\sim$ 65-85 au of about 3 % |
| Maximum 12CO gas temperature | up to 75 | not stated | K | 2 | the gas temperatures up to 75 K that we observe |
| Spiral radial extent (temperature) | 10-180 | not stated | au | 4 | a smaller one (Sp$_{\mathrm{T1}}$) spanning an azimuth of $\sim 100\,\degree$ between $\sim 10-180\,\mathrm{au}$ |
| Spiral SNR | 2-6 | not stated | dimensionless | 7 | with a SNR of 2-6 suggests them to be real features |
| Expected companion location | inside ~25 | not stated | au | 7 | a possible companion is expected to be located inside of $\sim$ 25 au in our case |

## Qualitative findings

- 12CO and 13CO velocity fields show twisted and bent iso-velocity curves in the inner disc (<~0.5")  
  > "significant distortions can be noticed in the inner disc (up to $\sim$ 0.5$''$)" (4.2 Velocity structure)
- Symmetric minor-axis dips are mostly due to beam dilution; the SE dip is deeper, possibly extra shadowing  
  > "Since the dip in the south-east appears to be more pronounced, and is co-located with the under-brightness in scattered light, some additional shadowing may still occur" (Summary)
- Warp and emission surface fits did not converge  
  > "we performed several runs, adding the parameterization of a potential warp in the (flat disc) model. Yet none of these models converged." (4.2.2 Razor-thin disc model)

## Claim tuples

- H: Does the CQ Tau gas disc show non-Keplerian substructure? | E: Centroid velocity maps and razor-thin Keplerian fits with eddy | R: Bent, twisted isovelocities and spiral residuals at 40-180 au | F: The disc is highly non-Keplerian | **supported**
- H: Are there spirals in 12CO brightness temperature and velocity? | E: Subtract azimuthally symmetric models and parameterize residuals | R: Three spirals: two in TB, one in velocity, spanning large azimuth and radius | F: Significant spirals detected | **supported**
- H: Are the TB spirals linked to NIR spirals? | E: Overlay NIR spiral from Uyama2019 on TB residuals | R: NIR spiral matches the anchoring point of the TB spirals | F: Common origin indicated | **supported**
- H: What drives the spirals? | E: Pitch angles and number of arms compared with expectations | R: Loosely wound, few arms, large pitch angles | F: Supports a massive embedded companion over gravitational instability, though GI is not ruled out | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Centroid fitting via bettermoments is more robust to noise and gives precision better than channel width  
  > "Compared to other methods this approach is more robust to noise or errors in the line shape, allowing a precision that is greater than the velocity resolution." (4.2 Velocity structure)
- Alternative: Warped disc and emission-surface models attempted but did not converge  
  > "We still attempted to fit for the emission surface, however none of the fits converged." (4.2 Velocity structure)
- Alternative: Convolving channel maps before collapsing was not done as it needs more model assumptions  
  > "Generating channels maps, as opposed to a simple rotation map, however requires far more model assumptions which is why we choose not to do it." (4.2.2 Razor-thin disc model)
- How they decided it was enough: _not stated_
- Limitation (authors): Posterior uncertainties are small and likely underestimated; systematic model uncertainties  
  > "show very small and likely underestimated uncertainties, especially in context of the scatter that is found in the stellar mass." (4.2.2 Razor-thin disc model)
- Limitation (authors): Pitch angles are only rough estimates from by-eye spiral parameterization  
  > "the pitch angles are only a rough estimate, since no actual fit was performed" (5 Discussion)
- Caveat (inferred, ours): Spirals have low SNR (2-6) and rely on by-eye parameterization
- Caveat (inferred, ours): Axisymmetric model subtraction may leave residuals from imperfect geometry or beam smearing
- Caveat (inferred, ours): Fixed inclination from earlier work may bias residuals
- Caveat (inferred, ours): Moment/centroid fit on a single-peak assumption in a perturbed, possibly unresolved inner disc

## Reproducibility

- Data public (paper): Archival ALMA projects cited in the acknowledgements  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2013.1.00498.S, ADS/JAO.ALMA#2016.A.000026.S, and ADS/JAO.ALMA#2017.1.01404.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Cell/image size, clean threshold
- Missing: Flux calibrator and uncertainty
- Missing: Spiral by-eye selection procedure
- Missing: Exact bettermoments settings
- Data volume (inferred): ~100-300 GB raw for three projects
- Score (inferred): 3/5, Public data and named tools with MCMC settings and fit tables, but imaging details and by-eye spiral fitting are incomplete.
- Rediscovery candidate: no, Spiral identification is by-eye and imaging parameters are incomplete, though the Keplerian fit values are numeric.

## Links

- Method: (cite: bettermoments) (Line centroid and moment maps)
- Method: (cite: eddy) (Keplerian rotation map fitting)
- Method: (cite: Andrews2018) (DSHARP calibration procedure)
- Companion: (cite: Gabellini2019) (Earlier lower-resolution ALMA analysis of the same disc and DALI model)
- Companion: (cite: Uyama2019) (NIR scattered-light spiral in CQ Tau)
- Related: DSHARP

## Checks

```json
{
 "quotes": 90,
 "quotes_ok": 90,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 3,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [
  "2016.A.000026.S"
 ],
 "numeric_results": 11,
 "numeric_problems": 0,
 "fill": {
  "facts": 91,
  "stated": 63,
  "rate": 0.692
 },
 "evidence_ok": true
}
```
