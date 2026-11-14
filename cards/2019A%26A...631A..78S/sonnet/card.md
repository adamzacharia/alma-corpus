# A spectral stacking analysis to search for faint outflow signatures in z ∼ 6 quasars

`2019A&A...631A..78S` | Astronomy and Astrophysics 2019 | first author: Stanley, F. | arXiv: 1908.11395 | DOI: 10.1051/0004-6361/201834530

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: agn_and_quasars, high_z_galaxies
- Question: Is there a faint broad high-velocity [C II] component indicating outflows in the stacked spectra and cubes of z~6 quasars?  
  > "In this study we use spectral stacking methods to search for faint high velocity outflow signal in a sample of \[C ii\] detected, $z\sim6$ quasars." (abstract)
- Target **26 [C II]-detected z~6 optically selected quasars (e.g. PSO J007.0273+04.9571, SDSS J2310+1855)**: coordinates given per source in the sample table (RA/Dec)  
  > "The sample has redshifts of $5.779 < z < 6.661$" (Sample); z/distance 5.779 < z < 6.661; mean z = 6.236  
  > "The sample has redshifts of $5.779 < z < 6.661$" (Sample); distance from [C II] line redshift; H0=70, OmegaM=0.3, OmegaL=0.7  
  > "The sample has redshifts of $5.779 < z < 6.661$" (Sample)

## Data provenance

- ALMA projects: 2015.1.00606.S, 2015.1.00997.S, 2015.1.01115.S
- bands: [C II] at rest 1900.537 GHz, observed ~247-280 GHz  
  > "at a rest frequency of 1900.537 GHz ($\lambda$ $\sim$158 $\mu$m)" (Sample)
- frequencies and spectral setup: 2015.1.01115.S: 960 channels of 1.953 MHz in four 1.875 GHz spws; 2015.1.00997.S: four 1.875 GHz spws, 480 channels, 3.9 MHz; 2015.1.00606.S: four 2.0 GHz spws, 128 channels of 15.625 MHz  
  > "For the spectral setup, 960 channels of 1.953 MHz width covered each of the four 1.875 GHz wide spectral windows." (3 ALMA data reduction and analysis)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 15.1 m to 1.0 km across projects  
  > "Between 37 and 49 antennas were included in the arrays with baselines between 15.1 m and 1.0 km." (3 ALMA data reduction and analysis)
- angular resolution: natural weighting beams ~0.4" to 1.7"; all cubes imaged to 0.8"x0.8"  
  > "Finally, all data cubes were imaged to the same angular resolution of $0.8''\times0.8''$ and spectral resolution of 30 km s$^{\rm -1}$" (3 ALMA data reduction and analysis)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: January to July 2016 (various)  
  > "The data were obtained between January and June 2016" (3 ALMA data reduction and analysis)
- pi or archival as stated: archival data, public by January 2018  
  > "the sample was limited to the sources for which the data was public by January 2018" (Sample)
- Line: [C II] 2P3/2-2P1/2 (1900.537 GHz)
- External data: Star-forming galaxy templates for IR luminosity  
  > "normalising a set of star-forming galaxy templates (from (cite: Mullaney11), see also (cite: Stanley18)) to the measured $S_{\rm cont}$ values" (3 ALMA data reduction and analysis) [from (cite: Mullaney11)]
- External data: Bolometric luminosity conversion from M1450  
  > "that correspond to bolometric luminosities of $3.9\times10^{45}<L_{\rm bol}<10^{47}$ erg s$^{-1}$ (cite: Runnoe12; Venemans16)" (Sample) [from (cite: Runnoe12; Venemans16)]
- Simulation/model as data: Mock samples built from one-component fits of observed lines, with/without added broad component and random noise, for 10 000 iterations  
  > "For 10 000 iterations, we add random noise to the individual \[C ii\] lines, based on the range of the observed rms, and stack following our 1-D stacking analysis." (5.3 Testing the feasibility)

## Processing

### Calibration

- pipeline or manual: manual calibration for ~70% of sources; ALMA pipeline for ~30%  
  > "For about 70% of the sources, a careful manual calibration of the observations was necessary" (3 ALMA data reduction and analysis)
- casa version: CASA 5.1.1 for manual calibration  
  > "we used the CASA software version 5.1.1" (3 ALMA data reduction and analysis)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: 5-10%  
  > "The uncertainty of the absolute flux calibration for all sources falls within 5–10%." (3 ALMA data reduction and analysis)
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "Natural weighting led to synthesised beam sizes between $\sim$0.4$^{\prime\prime}$ and 1.7$^{\prime\prime}$." (3 ALMA data reduction and analysis)
- uv taper: _not stated_
- cell size: 0.2"  
  > "with a pixel scale of 0.2$^{\prime\prime}$" (3 ALMA data reduction and analysis)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: CASA uvcontsub using line-free channels  
  > "Continuum subtraction was performed using the CASA task uvcontsub, using the channels with no line emission." (3 ALMA data reduction and analysis)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: all cubes at 30 km/s resolution and 0.8"x0.8" beam  
  > "all data cubes were imaged to the same angular resolution of $0.8''\times0.8''$ and spectral resolution of 30 km s$^{\rm -1}$" (3 ALMA data reduction and analysis)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Further observation details for 2015.1.01115.S  
  > "For more extensive details see (cite: Decarli18)." (3 ALMA data reduction and analysis) [from (cite: Decarli18)]
- Outflow mass equation  
  > "We use the equation of (cite: Hailey-Dunsheath10) to calculate the outflow gas mass from the integrated \[C ii\] luminosity of the broad component" (5.2 A sub-sample with outflow signatures) [from (cite: Hailey-Dunsheath10)]
- C+ abundance, T=200 K, n>>ncrit assumptions  
  > "Following (cite: Maiolino12), and (cite: Cicone15), we assume that X$_{\rm C^+} = 1.4\times10^{-4}$, T $=$ 200 K" (5.2 A sub-sample with outflow signatures) [from (cite: Maiolino12; Cicone15)]

### Not stated but needed to reproduce (our reading)

- Line Stacker code is 'Jolly et al. in prep' and not released
- Line-free channel ranges for uvcontsub and fit orders
- Exact manual calibration scripts, flagging and which sources were recalibrated
- How sigma significance of excess emission is normalised
- Fitting method and starting guesses for the two-Gaussian fit
- Grade definition and exact threshold details of sub-sample ranking
- Exact moment-0 construction and channel ranges
- Cube noise estimation per channel for weights

## Analysis recipe

1. **Calibrate and image archival cubes**: Manual or pipeline calibration, imaging to common 0.8" and 30 km/s, uvcontsub  
  > "we calibrated and imaged (including continuum subtraction) each data set with the Common Astronomy Software Applications" (3 ALMA data reduction and analysis)
   - software: CASA
   - parameter: 0.8"x0.8" beam, 30 km/s channels, 0.2" pixels  
  > "imaged to the same angular resolution of $0.8''\times0.8''$ and spectral resolution of 30 km s$^{\rm -1}$, with a pixel scale of 0.2$^{\prime\prime}$" (3 ALMA data reduction and analysis)
   - fitting: _not stated_
   - validation: _not stated_
2. **Extract 1-D spectra and continuum**: Moment-0 maps; spectra from brightest pixel and 2 and 3 sigma contour regions; 2D Gaussian continuum fit  
  > "we extracted 1-D spectra from the position of the brightest pixel, and the individual areas enclosed by the 2 and 3$\sigma$ integrated intensity contours" (3 ALMA data reduction and analysis)
   - software: GILDAS MAPPING
   - fitting: _not stated_
   - validation: _not stated_
3. **Velocity re-binning to common FWHM**: Rebin channels so each [CII] FWHM covers same number of channels, normalised to narrowest line  
  > "$cw_{rebin}\,=\,cw_{orig}\,\times\,\rm FWHM_{orig}/FWHM_{min}$" (4.1 Velocity re-binning)
   - software: Line Stacker
   - parameter: FWHM_min = 270 km/s; mean stacked channel width 60 km/s  
  > "the channel width of the stacked spectrum is taken as the mean channel width of all the individual spectra once re-binned, for our sample that corresponds to 60 km s$^{\rm -1}$" (4.1 Velocity re-binning)
   - fitting: _not stated_
   - validation: Mock stacking without outflow: >2 sigma broad excess in 2-5% of straightforward stacks, none without noise  
  > "excess emission due to a broad component is found at $>2\sigma$ 2-5% of the time" (6.1 Spectral line stacking methods)
4. **Stack spectra (1-D) and cubes (3-D) with three weightings**: Stack extracted spectra from >2 sigma moment-0 region, and full cubes pixel by pixel; weights 1, 1/sigma_rms^2, 1/S_peak  
  > "The cubes are then stacked pixel by pixel in order to create the stacked cube." (4.2 1-D and 3-D stacking)
   - software: Line Stacker
   - parameter: 3-D spectra extracted over 2" region  
  > "we use a larger integration area (2$^{\prime\prime}$)" (5.1 Stacking the full sample)
   - fitting: One- and two-component Gaussian fits; chi2 improvement and excess significance from residuals summed within ±800 km/s  
  > "we subtract the single component fit from the spectrum, and take the sum of the residuals within $\pm800$ km/s." (5.1 Stacking the full sample)
   - validation: Noise-only and broad-component mock stacks (10 000 iterations)  
  > "14-17% of the iterations return a $>0.4\sigma$ excess signal in the stacked lines" (5.3 Testing the feasibility)
5. **Select max/min sub-samples**: 10 000 random sub-sets of 3-25 sources; integrate line-free channels (>2 FWHM) at radii 0.2-3"; rank sources by summed grades; max sub-sample above mean rank  
  > "The sub-sample selection is done by randomly selecting sub-sets of $n$ sources, where $n$ is in the range 3$-$25, and repeated 10 000 times." (5.2 A sub-sample with outflow signatures)
   - software: Line Stacker
   - fitting: _not stated_
   - validation: Leave-one-out stacks; min sub-sample shows no outflow; broad parameters stay within 20%  
  > "the FWHM, $S_{\rm peak}$ values of the broad component remain within 20% of those found for the stack of the complete *max sub-sample*" (5.2 A sub-sample with outflow signatures)
6. **Estimate mean outflow rate**: Hailey-Dunsheath mass from broad [CII] luminosity; v = 0.5 FWHM; Mdot = M v / R  
  > "$\dot{M}_{outf} = M_{outf}/\tau_{dyn} = M_{outf}\times\upsilon_{outf}/R$" (5.2 A sub-sample with outflow signatures)
   - parameter: z=6.236, R=11.5 kpc (2"), v=493 km/s  
  > "For the mean redshift of 6.236, a radius of $R = 11.5kpc$ (2$^{\prime\prime}$), and $\upsilon_{outf} = 493$ km s$^{\rm -1}$" (5.2 A sub-sample with outflow signatures)
   - assumption: X_C+=1.4e-4, T=200 K, n>>ncrit~3e3 cm^-3, constant outflow velocity  
  > "we assume that X$_{\rm C^+} = 1.4\times10^{-4}$, T $=$ 200 K, and $n>>n_{crit}$" (5.2 A sub-sample with outflow signatures)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 5.1.1 (manual calibration): Calibration, imaging, uvcontsub  
  > "we calibrated and imaged (including continuum subtraction) each data set with the Common Astronomy Software Applications" (3 ALMA data reduction and analysis)
- **GILDAS MAPPING** : Moment-0 maps and spectral extraction  
  > "the resulting data cubes were imported into the MAPPING software package within GILDAS" (3 ALMA data reduction and analysis)
- **Line Stacker** : Spectral stacking of interferometric data  
  > "we use the spectral stacking analysis tool Line Stacker (Jolly et al. in prep)" (4 Spectral line stacking techniques)
- **APLpy** : Plotting  
  > "This research made use of APLpy, an open-source plotting package for Python" (Acknowledgements)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Excess significance, full sample, 3-D stack | 1.1-1.5 | not stated | sigma | 4 | we calculate the significance of the excess emission to be 1.1–1.5$\sigma$ |
| Excess significance, full sample, 1-D stack | 0.4-0.7 | not stated | sigma | 4 | We find a significance of 0.4–0.7$\sigma$, depending on the weighting scheme used |
| Excess significance, max sub-sample, 3-D | 1.2-2.5 | not stated | sigma | 5 | the significance of excess emission rises to 1.2–2.5$\sigma$ |
| Number of sources in max sub-sample | 12 | not stated | sources | 5 | The *max sub-sample* consists of 12 sources |
| Broad component FWHM, max sub-sample 3-D, w=1 | 986 | ±210 | km/s | 4 | / $w=1$                      / $6.14\pm0.69$  / $305\pm36$      / $2.0\pm0.3$        / $-1\pm10$       / $1.87\pm0.68$  / $986\pm210$     / |
| Mean outflow rate, max sub-sample | 45 | ±21 | Msun/yr | 6 | calculate that $\dot{M}_{outf} = 45\pm21$ M$_\odot$ yr$^{-1}$ |
| False detection probability of >0.4 sigma excess in no-outflow mocks | 14-17 | not stated | % | 4 | 14-17% of the iterations return a $>0.4\sigma$ excess signal in the stacked lines |

## Qualitative findings

- Outflow emission is spatially extended (~2") beyond the beam, so central-pixel stacking misses it  
  > "This suggests that the emission of the outflow is spatially extended beyond the beam" (5.2 A sub-sample with outflow signatures)
- The min sub-sample shows no broad component  
  > "A stack for these sources shows no evidence of an outflow component" (5.2 A sub-sample with outflow signatures)

## Claim tuples

- H: Does the full sample of z~6 quasars show a stacked broad [CII] component? | E: 1-D and 3-D stacking with three weightings and two-Gaussian fits | R: Excess 0.4-0.7 sigma (1-D) and 1.1-1.5 sigma (3-D); FWHM>700 km/s | F: Only tentative broad component in the full sample | **partially**
- H: Does a sub-sample contribute the outflow signal? | E: Random sub-sampling ranking of sources | R: 12-source max sub-sample, 1.2-2.5 sigma, FWHM>775 km/s | F: Evidence for outflows in 12 of 26 sources, though low significance | **partially**
- H: Could the method create artificial broad components? | E: Mock stacks without outflow | R: <17% false excess >0.4 sigma; none >2 sigma | F: Method is unlikely to produce spurious signal | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Individual spectra lack sensitivity, so stacking is the only available method  
  > "spectral stacking is the only available method at present to determine the presence of outflow signatures" (6.1 Spectral line stacking methods)
- How they decided it was enough: _not stated_
- Limitation (authors): Assumes a single broad Gaussian outflow profile; broad emission could be from interacting galaxies; low-velocity outflows not detectable  
  > "we have assumed that the outflow emission signature has the spectral profile of a single broad Gaussian" (5.2 A sub-sample with outflow signatures)
- Caveat (inferred, ours): Significances of 1-2.5 sigma are marginal, and the sub-sample selection from the same data risks selection bias
- Caveat (inferred, ours): Mock test shows weak broad components are only recovered at 1-2 sigma
- Caveat (inferred, ours): Manual recalibration choices may affect results

## Reproducibility

- Data public (paper): Archival ALMA data public by January 2018  
  > "the sample was limited to the sources for which the data was public by January 2018" (Sample)
- Products in archive: _not stated_
- Code: Line Stacker is 'Jolly et al. in prep'; no release stated  
  > "Line Stacker (Jolly et al. in prep)" (4 Spectral line stacking techniques)
- Missing: Line Stacker code
- Missing: Manual calibration details
- Missing: Exact fit and significance procedures
- Data volume (inferred): ~0.5-1 TB raw for 31 datasets
- Score (inferred): 3/5, Public data and clear stacking recipe, but unreleased stacking code and vague calibration/fit details.
- Rediscovery candidate: no, Key tool unreleased and results are marginal-significance with underspecified fitting.

## Links

- Method: (cite: Decarli18) (Original data description and central-pixel stacking)
- Companion: (cite: Bischetti18) (Parallel stacking study of quasars)
- Related: Decarli et al. 2018 z~6 quasar [CII] survey

## Checks

```json
{
 "quotes": 63,
 "quotes_ok": 63,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 3,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [
  "2015.0.00606.S",
  "2015.0.00997.S",
  "2015.0.01115.S"
 ],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 80,
  "stated": 48,
  "rate": 0.6
 },
 "evidence_ok": true
}
```
