# Investigating Fragmentation of Gas Structures in OB Cluster-forming Molecular Clump G33.92+0.11 with 1000 au Resolution Observations of ALMA

`2019ApJ...871..185L` | The Astrophysical Journal 2019 | first author: Liu, Hauyu Baobab | arXiv: 1808.07702 | DOI: 10.3847/1538-4357/aaf6b4

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, milky_way_ism
- Question: How do gas structures in the OB cluster-forming clump G33.92+0.11 fragment into YSO candidates, and is the fragmentation consistent with Toomre instability and Jeans lengths?  
  > "How these gas structures fragment to subsequently form 10$^{3}$-10$^{4}$ AU scales gas cores and YSOs, remain uncertain." (Introduction)
- Target **G33.92+0.11**: coordinates RA 18h52m50.272s, Dec +00d55m29.604s (J2000, pointing center)  
  > "we selected to observe the target source G33.92+0.11 ($d\sim$7.1 kpc)." (Introduction); "The pointing and phase referencing center is R.A. (J2000) = 18$^{\mbox{\scriptsize h}}$52$^{\mbox{\scriptsize m}}$50$^{\mbox{\scriptsize s}}$.272, and Decl. (J2000) = 00$^{\circ}$55$'$29$''$.604." (Observation and data reduction); z/distance d ~7.1 kpc; vlsr ~107.6 km/s  
  > "we selected to observe the target source G33.92+0.11 ($d\sim$7.1 kpc)." (Introduction); "The pointing and phase referencing center is R.A. (J2000) = 18$^{\mbox{\scriptsize h}}$52$^{\mbox{\scriptsize m}}$50$^{\mbox{\scriptsize s}}$.272, and Decl. (J2000) = 00$^{\circ}$55$'$29$''$.604." (Observation and data reduction); distance from _not stated_

## Data provenance

- ALMA projects: 2012.1.00387.S, 2016.1.00362.S
- bands: _not stated_
- frequencies and spectral setup: Two 234.4 MHz windows (61 kHz channels) at 231.220690 and 220.679320 GHz; two 1875 MHz windows (488 kHz channels) at 231.900928 and 217.104980 GHz  
  > "There were two 234.4 MHz wide spectral windows (channel spacing 61 kHz, $\sim$0.085 km s$^{-1}$) centered at 231.220690 GHz and 220.679320 GHz" (Observation and data reduction)
- continuum bandwidth: _not stated_
- arrays: ALMA 12m and ACA  
  > "We have resolved G33.92+0.11 using the Atacama Large Millimeter Array (ALMA) and Atacama Compact Array (ACA), with a $\sim$1000 AU spatial resolution." (Introduction)
- configurations: _not stated_
- baselines: 2017 data uv distance ~18-3400 m; combined 7-3400 m  
  > "Combining all existing data yields an overall *uv* distance range of 7-3400 meters." (Observation and data reduction)
- angular resolution: 0.16" x 0.093" (~1100 x 660 AU), PA 75 deg (Briggs robust 0); earlier data 0.67" x 0.47"  
  > "$\theta_{\mbox{\scriptsize maj}}\times\theta_{\mbox{\scriptsize min}}$= 0.16$''$$\times$0.093$''$ ($\sim$1100 AU $\times$660 AU; P.A.=75$^{\circ}$)" (Observation and data reduction)
- max recoverable scale: _not stated_
- sensitivity: RMS 25 uJy/beam (~41 mK)  
  > "is 25 $\mu$Jy beam$^{-1}$($\sim$41 mK)" (Observation and data reduction)
- time on source: _not stated_
- observing dates: ALMA 2014 Apr 29 (previously failed QA2) and 2014 May 04; ACA 2014 May 03 and 04; new ALMA 2017 Aug 19  
  > "We carried out the new, long baseline array configuration observations of ALMA on 2017 August 19 (UTC 01:54-04:31)" (Observation and data reduction)
- pi or archival as stated: PI H. B. Liu, H.-R. Chen; 2014 data previously reported by Liu et al. 2015  
  > "The ALMA observations on 2014 May 04, and the ACA observations on 2014 May 03 and 04, were reported by (cite: Liu2015)." (Observation and data reduction)
- Line: H30alpha recombination line (not stated)
- Line: CH3CN J=12-11 (not stated)
- Line: SiO 5-4 (not stated)
- External data: NH3 rotational temperature used to motivate temperature profile and 30 K assumption  
  > "Motivated by the NH$_{3}$ rotational temperature presented in (cite: Liu2012b), our fiducial analysis assumes a constant 30 K temperature across the entire source." (Toomre instability) [from (cite: Liu2012b)]
- External data: Dust mass opacity kappa_225GHz = 0.6 (+0.7/-0.3)  
  > "dust mass opacity $\kappa_{\mbox{\scriptsize 225 GHz}}=$0.6$^{+0.7}_{-0.3}$ (cite: Draine2006)" (Results) [from (cite: Draine2006)]
- External data: Electron temperature ~8000 K  
  > "We adopted the nominal value of $T_{e}\sim$8000 K for the electron temperature (cite: Keto2008)" (Results) [from (cite: Keto2008)]
- External data: Thickness profile motivated by G10.6-0.4  
  > "Our assumption of $H(r)$ is motivated by observations of the similar but edge-on system, G10.6-0.4 (cite: Liu2017)." (Spatial separations of young stellar objects) [from (cite: Liu2017)]

## Processing

### Calibration

- pipeline or manual: Failed-QA2 epoch manually calibrated; data calibrated and phase self-calibrated in CASA  
  > "We manually calibrated these observations and found that the data can be used, and thus included them in our present analysis." (Observation and data reduction)
- casa version: CASA 5.0.0  
  > "The data were calibrated and phase self-calibrated using the CASA software package (cite: McMullin2007) version 5.0.0." (Observation and data reduction)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: phase self-calibration  
  > "The data were calibrated and phase self-calibrated using the CASA software package" (Observation and data reduction)

### Imaging

- task: CASA clean, jointly on all continuum data; uvcontsub for continuum fitting  
  > "We fit the continuum baselines using the CASA task `uvcontsub`, and then jointly imaged all continuum data using the CASA task `clean`." (Observation and data reduction)
- deconvolver: _not stated_
- weighting robust: Briggs robust = 0  
  > "As restoring beam we used Briggs Robust = 0 weighted continuum image" (Observation and data reduction)
- uv taper: _not stated_
- cell size: 0.01 arcsec  
  > "Images are created with 6000 pixels in the R.A. and Decl. dimensions, with 0.01$''$ pixel size." (Observation and data reduction)
- image size: 6000 x 6000 pixels  
  > "Images are created with 6000 pixels in the R.A. and Decl. dimensions" (Observation and data reduction)
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: Peak intensity quoted in primary-beam-corrected image; dendrogram run on uncorrected image  
  > "the peak intensity in the primary beam corrected image is 17 mJy beam$^{-1}$($\sim$28 K)" (Observation and data reduction)
- array combination: _not stated_
- smoothing: Upper and lower sideband MFS (nterms=1) images smoothed to common resolution and linearly combined  
  > "we performed MFS imaging for the upper and lower sidebands separately using only one Taylor term, and then linearly combined the upper and lower sideband images after smoothing to an identical angular resolution." (Observation and data reduction)
- final beam: 0.16" x 0.093", PA 75 deg  
  > "0.16$''$$\times$0.093$''$ ($\sim$1100 AU $\times$660 AU; P.A.=75$^{\circ}$)" (Observation and data reduction)
- final rms: 25 uJy/beam from sideband difference  
  > "The root mean square (RMS) noise estimated based on the difference of the upper and lower sidebands images is 25 $\mu$Jy beam$^{-1}$" (Observation and data reduction)

### Inherited from earlier work

- Toomre/Jeans analysis strategy follows G10.6-0.4 study  
  > "by adopting a strategy similar to what was used for analyzing the other OB cluster-forming massive molecular clump, G10.6-0.4 (cite: Liu2017)." (Toomre instability) [from (cite: Liu2017)]
- MSDC analysis prescription  
  > "We followed the prescription of (cite: simon97), also described in detail in (cite: Palau2018)" (Clustering of candidates of young stellar objects) [from (cite: simon97); (cite: Palau2018)]
- CH3CN temperature procedure  
  > "We also based on the procedure outlined in (cite: Chen2006) to derive gas temperature from the CH$_{3}$CN J=12-11 lines" (Toomre instability) [from (cite: Chen2006)]

### Not stated but needed to reproduce (our reading)

- Calibrator names and flux scale
- Line-free channels used for uvcontsub
- clean threshold, masks, niter
- Weights used to combine ALMA and ACA data
- Electron temperature/line width used for the H30alpha free-free model
- Details of the CH3CN temperature fit
- Dendrogram settings beyond thresholds, and exact manual source edits

## Analysis recipe

1. **Continuum imaging**: Joint clean of ALMA+ACA continuum, upper and lower sidebands separately with nterms=1, smoothed and combined  
  > "we performed MFS imaging for the upper and lower sidebands separately using only one Taylor term" (Observation and data reduction)
   - software: CASA
   - parameter: Briggs robust=0; 0.01" pixels; 6000 pixels  
  > "Images are created with 6000 pixels in the R.A. and Decl. dimensions, with 0.01$''$ pixel size." (Observation and data reduction)
   - fitting: _not stated_
   - validation: RMS from sideband difference  
  > "The root mean square (RMS) noise estimated based on the difference of the upper and lower sidebands images" (Observation and data reduction)
2. **Free-free subtraction**: Model free-free image from H30alpha using line-to-continuum ratio, smoothed and subtracted from continuum  
  > "We smoothed our model of free-free emission to the same angular resolution of our ALMA continuum image, and then subtracted the model from the continuum image to yield a dust continuum image." (Results)
   - software: CASA
   - parameter: N(He+)/N(H+)=0.08  
  > "which is adopted to be 0.08" (Results)
   - assumption: Te~8000 K  
  > "We adopted the nominal value of $T_{e}\sim$8000 K for the electron temperature (cite: Keto2008)" (Results)
   - fitting: _not stated_
   - validation: Free-free faint; subtraction does not significantly impact analysis  
  > "we found that free-free emission is likely faint, such that subtracting the free-free emission or not does not significantly impact our analysis." (Results)
3. **Toomre Q**: Enclosed gas mass from 225 GHz flux, assumed T(r); centrifugal balance; Q = kappa cs/(pi G Sigma)  
  > "We then estimate the enclosed gas mass in radius $r$ based on the observed 225 GHz flux and an assumed gas temperature profile $T(r)$" (Toomre instability)
   - parameter: 0 or 30 Msun central stellar mass  
  > "(2) there is a total of 30 $M_{\odot}$ of stellar mass embedded at the center of the system." (Toomre instability)
   - assumption: Constant 30 K fiducial, or radial profile; optically thin; gas-to-dust 100; flattened rotating  
  > "our fiducial analysis assumes a constant 30 K temperature across the entire source." (Toomre instability)
   - fitting: _not stated_
   - validation: CH3CN temperatures broadly consistent with profile  
  > "These measurements are in general consistent with the temperature model described by Equation" (Toomre instability)
4. **Identify YSO candidates**: astrodendro leaves on primary-beam-uncorrected image, then selection criteria and manual edit  
  > "we set the minimum pixel value to be two times our RMS noise level, and set the minimum delta pixel value to be five times our RMS noise level." (Identifying candidates of young stellar objects)
   - software: astrodendro
   - parameter: min area 25 pixel^2; initial 33 sources; final 28  
  > "In the end we obtain a catalogue with a total of 28 Class 0/I candidates" (Identifying candidates of young stellar objects)
   - fitting: _not stated_
   - validation: Expected spurious sources 0.04 at 5 sigma; unedited catalogue also analysed  
  > "the expected number of spuriously identified sources is 0.04" (Identifying candidates of young stellar objects)
5. **Clustering analysis**: MSDC/TPCF with Monte Carlo random distributions; hierarchical n-clusters via minimum spanning tree with xi=1.7  
  > "In this paper, we chose $\xi$ to be 1.7." (Clustering of candidates of young stellar objects)
   - parameter: bins of 0.2 dex; 10^4 random distributions  
  > "The random distribution was calculated from $10^4$ distributions constructed with a Monte Carlo routine." (Clustering of candidates of young stellar objects)
   - fitting: _not stated_
   - validation: Compare two MSDC estimators  
  > "when the points are similar, we can assure that those points are reliable" (Clustering of candidates of young stellar objects)
6. **Compare linking lengths with Jeans lengths**: Convert Tb at link midpoints to density with thickness profile H(r); compute Jeans lengths; compare with link lengths and regress log sqrt(Tb) vs log l  
  > "we convert $T_{b}^{\mbox{\scriptsize 225 GHz}}$ to gas volume density $\rho$ based on the assumed radial characteristic thickness profile $H(r)$" (Spatial separations of young stellar objects)
   - parameter: H(r)=0.05+0.3 sqrt(r/0.3) pc; T=30 K  
  > "H(r) [pc] = 0.05 + 0.3\times\sqrt{r [pc] / 0.3}." (Spatial separations of young stellar objects)
   - assumption: kappa=0.6 cm2/g, gas-to-dust 100  
  > "assuming $\kappa_{\mbox{\scriptsize 225 GHz}}=$0.6 cm$^{2}$ g$^{-1}$ and gas to dust mass ratio 100" (Spatial separations of young stellar objects)
   - fitting: Linear regression in log-log, upper limits excluded  
  > "A linear regression of $\log{(\sqrt{T_{b}^{\mbox{\scriptsize 225 GHz}}})}$ and $\log{(\ell)}$ (without including upper limits)" (Spatial separations of young stellar objects)
   - validation: Alternative T and H(r) and alternative catalogues  
  > "for the catalogue directly given by `deodrogram` without any further edits, gives slopes of -0.54 and -0.52, respectively." (Spatial separations of young stellar objects)

## Software

- **CASA** 5.0.0: Calibration, self-calibration, uvcontsub, clean  
  > "phase self-calibrated using the CASA software package (cite: McMullin2007) version 5.0.0." (Observation and data reduction)
- **astrodendro** : Identify compact sources (leaves)  
  > "we first used the `dendrogram` algorithm (cite: Rosolowsky2008) to yield a complete list of independent sources" (Identifying candidates of young stellar objects)
- **Numpy** : Listed in software  
  > "Numpy (cite: VanDerWalt2011), APLpy (cite: Robitaille2012)" (Software)
- **APLpy** : Plotting  
  > "APLpy (cite: Robitaille2012)" (Software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Synthesized beam (robust 0) | 0.16 x 0.093 | not stated | arcsec | 1 | 0.16$''$$\times$0.093$''$ ($\sim$1100 AU $\times$660 AU; P.A.=75$^{\circ}$) |
| Continuum RMS | 25 | not stated | uJy/beam | 1 | is 25 $\mu$Jy beam$^{-1}$($\sim$41 mK) |
| Gas mass equivalent of 1-sigma RMS | 0.026 | +0.026/-0.014 | Msun | 1 | corresponds to a gas mass of 0.026$^{+0.026}_{-0.014}$ $M_{\odot}$ |
| Number of Class 0/I candidates | 28 | not stated | dimensionless | 4 | we obtain a catalogue with a total of 28 Class 0/I candidates |
| Regression slope log sqrt(Tb) vs log l, final catalogue | -0.68 | not stated | dimensionless | 6 | gives a slope of -0.68. |
| MSDC steep slope | -3.6 | not stated | dimensionless | 5 | the very steep slope of -3.6 |

## Qualitative findings

- Only one compact source (C) lies outside known arm-like dense gas structures  
  > "Besides source C, there appears to be no Class 0/I candidates forming outside of the known arm-like dense gas structures." (Results)

## Claim tuples

- H: The clump is a Toomre-unstable rotating flow | E: Toomre Q computed with assumed T(r) and stellar mass cases | R: Q<1 on resolved scales in all assumptions | F: System is Toomre unstable, consistent with observed fragmentation | **supported**
- H: Source separations are set by Jeans lengths | E: Compare link lengths with Jeans lengths from Tb and assumed thickness | R: Jeans lengths consistent with linking lengths; central 3-cluster sensitive to thickness | F: Separations explained by thermal Jeans fragmentation | **supported**

## Reasoning

- Why this data: Face-on geometry minimizes line-of-sight confusion  
  > "then the studies of its matter distribution will be minimally affected by line-of-sight confusion." (Introduction)
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Source catalogue edits are subjective  
  > "Our edits to the identified source catalogue is subjective to some extent." (Identifying candidates of young stellar objects)
- Limitation (authors): Thickness H(r) cannot be measured; assumption oversimplified  
  > "This assumption of the thickness of gas structure is likely yet oversimplified." (Spatial separations of young stellar objects)
- Caveat (inferred, ours): Jeans-length agreement depends on assumed thickness and temperature
- Caveat (inferred, ours): Class 0/I identification is not confirmed by line tracers
- Caveat (inferred, ours): Only dust continuum used; thermal-only support assumed

## Reproducibility

- Data public (paper): Project codes given and acknowledged  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA #2012.1.00387.S, #2016.1.00362.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Calibration and clean parameters
- Missing: Manual source edits
- Missing: Jeans-length calculation details
- Data volume (inferred): Several hundred GB raw for combined multi-epoch ALMA+ACA data
- Score (inferred): 3/5, Data identified and main steps described but imaging parameters and manual edits are incomplete.
- Rediscovery candidate: no, Subjective catalogue edits and missing clean/calibration details prevent exact recovery of numbers.

## Links

- Method: (cite: Rosolowsky2008) (dendrogram algorithm)
- Method: (cite: Palau2018) (MSDC analysis prescription)
- Companion: (cite: Liu2015) (Previous ALMA/ACA observations of G33.92+0.11)
- Companion: (cite: Liu2017) (Similar analysis of G10.6-0.4)

## Checks

```json
{
 "quotes": 75,
 "quotes_ok": 75,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 84,
  "stated": 59,
  "rate": 0.702
 },
 "evidence_ok": true
}
```
