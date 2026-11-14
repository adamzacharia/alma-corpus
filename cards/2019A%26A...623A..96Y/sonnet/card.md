# Signs of outflow feedback from a nearby young stellar object on the protostellar envelope around HL Tauri

`2019A&A...623A..96Y` | Astronomy and Astrophysics 2019 | first author: Yen, Hsi-Wei | arXiv: 1901.03452 | DOI: 10.1051/0004-6361/201834209

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type multi_facility_alma_minor

## Science

- Fields: star_formation, protoplanetary_disks
- Question: What is the nature of the arc-like structures connected to the HL Tau disk, and can relative motion between the star and its envelope, possibly driven by a large-scale expanding shell, explain their kinematics?  
  > "In this work, we investigate the nature of these arc-like structures connected to the disk." (abstract)
- Target **HL Tau**: coordinates _not stated_; z/distance 140 pc  
  > "located in the Taurus star-forming region at a distance of 140 pc" (Introduction); distance from Kenyon94; Loinard13; Galli18  
  > "located in the Taurus star-forming region at a distance of 140 pc" (Introduction)

## Data provenance

- ALMA projects: 2015.1.00551.S
- bands: _not stated_
- frequencies and spectral setup: ACA: 2 continuum windows of 2 GHz; 13CO(2-1) 468.8 MHz, 122 kHz channels; C18O(2-1) 234.4 MHz, 244 kHz channels; SO window 234.4 MHz  
  > "The spectral setup of our ACA observations is the same as that of our observations with the 12-m array, which contains five spectral windows." (2.3 ACA 7-m array observations)
- continuum bandwidth: _not stated_
- arrays: ACA 7-m array (plus ALMA 12-m data from Yen17); JCMT HARP; IRAM 30m EMIR  
  > "The ACA 7-m array data were combined with the ALMA 12-m array data to generate images." (2.3 ACA 7-m array observations)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: Combined 30m+ACA+ALMA: 1" x 0.9"  
  > "$1\ensuremath{''} \times 0.9\ensuremath{''}$ (151$^\circ$)" (Table 1)
- max recoverable scale: _not stated_
- sensitivity: Combined noise 7.7 mJy/beam (13CO), 5.5 mJy/beam (C18O) per channel in Table; text gives 6 and 8 mJy/beam  
  > "the noise levels are 6 and 8 mJy beam$^{-1}$ in the $^{13}$CO (2–1) and C$^{18}$O (2–1) images, respectively" (2.4 Combined maps)
- time on source: ACA: 20 min per pointing; JCMT 4.4 h; IRAM 30m 4.7 h  
  > "The total on-source time per pointing is 20 minutes." (2.3 ACA 7-m array observations)
- observing dates: ACA: Jan 17, Jun 16, Sep 8 2016; JCMT: Jan–Feb and Aug 1 2017; IRAM 30m: Mar 28–29 2017  
  > "The observations were conducted on January 17, June 16, and September 8 in 2016." (2.3 ACA 7-m array observations)
- pi or archival as stated: _not stated_
- Line: 13CO 2-1 (220.398684 GHz)
- Line: C18O 2-1 (219.560358 GHz)
- Line: 13CO 3-2 (330.587960 GHz)
- Line: C18O 3-2 (329.330545 GHz)
- Other facility **JCMT**: 13CO and C18O (3-2) HARP maps, program M17AP086  
  > "The JCMT data were obtained under program ID M17AP086." (Acknowledgements)
- Other facility **IRAM 30m**: 13CO and C18O (2-1) OTF maps for short spacings and large-scale kinematics  
  > "On-the-fly mapping was performed to cover an area of $2\ensuremath{'} \times 2\ensuremath{'}$" (2.2 IRAM 30m observations)
- External data: ALMA 12-m 13CO and C18O (2-1) data, details of observations  
  > "The details of our ALMA observations were described in (cite: Yen17)." (2.4 Combined maps) [from (cite: Yen17)]
- External data: Disk inclination 47 deg, PA 138 deg, disk radius 100 au  
  > "are also adopted to be the same as the disk around , 47$\ensuremath{^\circ}$ and 138$\ensuremath{^\circ}$, respectively (cite: ALMA15)." (4.2 Kinematical model of the arc structure) [from (cite: ALMA15)]
- External data: Expanding shell radius 90" from 13CO(1-0)  
  > "is 90$\ensuremath{''}$, which is the radius of the shell observed in the $^{13}$CO emission by (cite: Welch00)." (4.1 Kinematics of the dense cloud) [from (cite: Welch00)]
- Simulation/model as data: Test-particle kinematical model of infalling, rotating envelope (Ulrich76) with added relative velocity, used to generate synthetic C18O channel maps  
  > "we constructed a new kinematical model by placing a set of test particles and calculating their trajectories and velocities with time evolution based on the equations of motion." (4.2 Kinematical model of the arc structure)

## Processing

### Calibration

- pipeline or manual: CASA pipeline  
  > "The data were reduced with the pipeline in Common Astronomy Software Applications (cite: McMullin07) of version 4.7.0-1." (2.3 ACA 7-m array observations)
- casa version: 4.7.0-1 (calibration); 4.7.0 (imaging)  
  > "of version 4.7.0-1" (2.3 ACA 7-m array observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Jan 17: J0510+1800 (3.4 Jy); Jun 16: Uranus; Sep: J0522-3627 (3.4 Jy)  
  > "On January 17, J0510+1800 (3.4 Jy at 220 GHz) was observed as flux and bandpass calibrators" (ACA 7-m array observations)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA clean, imagermode mosaic  
  > "We first adopted *imagermode* of “mosaic” and generated interferometric images with the ACA and ALMA data together using the CASA task, *clean*." (2.4 Combined maps)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "were generated with the natural weighting at velocity resolutions of 0.2 km s$^{-1}$ and 0.34 km s$^{-1}$, respectively." (2.4 Combined maps)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: 0, 2", 5", 10"  
  > "Multi-scale clean with the scale sizes of 0, 2$\ensuremath{''}$, 5$\ensuremath{''}$, and 10$\ensuremath{''}$ was performed." (2.4 Combined maps)
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: ACA+ALMA jointly cleaned, then feathered with IRAM 30m (regridded and multiplied by mosaic primary beam response) using feather/casafeather  
  > "we combined the interferometric and IRAM 30m images to generate the combined images using the CASA task, *feather*, and its visual interface, *casafeather*." (2.4 Combined maps)
- smoothing: _not stated_
- final beam: 1" (1" x 0.9")  
  > "The final resolutions of the combined images are 1$\ensuremath{''}$" (2.4 Combined maps)
- final rms: 6 and 8 mJy/beam (13CO, C18O)  
  > "the noise levels are 6 and 8 mJy beam$^{-1}$ in the $^{13}$CO (2–1) and C$^{18}$O (2–1) images, respectively" (2.4 Combined maps)

### Inherited from earlier work

- ALMA 12-m observation and reduction details; best-matched free-fall envelope model; stellar mass 1.8 Msun  
  > "the mass of the central star is adopted to be 1.8 $M_\ensuremath{\odot}$, the same as (cite: Yen17)" (4.2 Kinematical model of the arc structure) [from (cite: Yen17)]
- Optical depth ratio computed following equations for LTE  
  > "the ratio of $\tau_1$ to $\tau_2$ can be computed following the equations in (cite: Mangum15)." (3.1 Single-dish maps) [from (cite: Mangum15)]
- Temperature anchors: 60 K at 100 au and 15 K at 1000 au  
  > "The temperature at the disk outer radius of 100 au in is measured to be 60 K from the CO (1–0) brightness temperature observed with ALMA (cite: Yen16)" (4.2 Kinematical model of the arc structure) [from (cite: Yen16); (cite: Yen17)]

### Not stated but needed to reproduce (our reading)

- Number of test particles in the kinematical model and integration scheme/time step
- Exact C18O column density scaling applied to the model
- Pointing center and phase center coordinates for HL Tau
- Primary beam cutoff and clean threshold/mask and iteration count
- Flux calibration and continuum subtraction details of the 12-m data (in Yen17)
- Exact criteria for removing particles when deriving the asymmetric initial distribution
- Line-free channels for baseline fitting in single-dish data beyond the ORAC-DR recipe

## Analysis recipe

1. **Reduce single-dish data and make maps**: JCMT data reduced with Starlink ORAC-DR recipe reduce_science_narrowline; IRAM 30m with CLASS  
  > "the recipe of “reduce_science_narrowline” was adopted." (2.1 JCMT observations)
   - software: Starlink, ORAC-DR, CLASS
   - parameter: main beam efficiency 0.64 (HARP), 0.61 (IRAM 30m)  
  > "The main beam efficiency of HARP is 0.64." (2.1 JCMT observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **Combine ACA, ALMA and IRAM 30m data**: Joint mosaic multi-scale clean of ACA+ALMA, then feather with IRAM 30m  
  > "Finally, we combined the interferometric and IRAM 30m images to generate the combined images using the CASA task, *feather*" (2.4 Combined maps)
   - software: CASA
   - parameter: natural weighting; scales 0, 2", 5", 10"  
  > "Multi-scale clean with the scale sizes of 0, 2$\ensuremath{''}$, 5$\ensuremath{''}$, and 10$\ensuremath{''}$ was performed." (2.4 Combined maps)
   - fitting: _not stated_
   - validation: Known CASA mosaic imaging issue overestimates fluxes by 10%; analysis does not depend on flux level  
  > "the fluxes in our mosaic map are overestimated by 10%." (2.4 Combined maps)
3. **Derive excitation temperature and optical depth from line ratios**: LTE radiative transfer equation for 13CO (2-1)/(3-2) and C18O ratios with equal Tex  
  > "We assume that the $^{13}$CO (2–1) and (3–2) lines have the same $T_{\rm ex}$." (3.1 Single-dish maps)
   - parameter: Tbg = 2.73 K  
  > "$T_{\rm bg}$ is the cosmic background temperature of 2.73 K." (3.1 Single-dish maps)
   - assumption: LTE; same Tex for both transitions; 13CO/C18O abundance ratio 5.5-10  
  > "C$^{18}$O is less abundant than $^{13}$CO with a $^{13}$CO/C$^{18}$O abundance ratio of 5.5–10" (3.1 Single-dish maps)
   - fitting: Solved Tex and tau from brightness temperature ratio; errors from noise propagation, 10% flux uncertainty at high S/N  
  > "The uncertainties are estimated from the error propagation of the observational noise." (3.1 Single-dish maps)
   - validation: _not stated_
4. **Measure expanding shell velocity from PV diagrams**: C18O (2-1) PV diagrams at PA 10-170 deg compared with expected line-of-sight profile of a spherical expanding shell, Vex = 0.3, 0.6, 0.9 km/s  
  > "we computed the expected profiles for the expanding motion at three different velocities, $V_{\rm ex} = 0.3$, 0.6, and 0.9 km s$^{-1}$." (4.1 Kinematics of the dense cloud)
   - parameter: Rsh = 90"; Vsys = 7 km/s  
  > "we assume that the systemic velocity ($V_{\rm sys}$) of the large-scale cloud around and , meaning the cloud velocity before being swept up by wind or outflow from , is the same as $V_{\rm sys}$ of" (4.1 Kinematics of the dense cloud)
   - assumption: Spherical symmetric shell centred on the driving source  
  > "is spherical symmetric with respect to the position of , and that the current radius of the expanding shell ($R_{\rm sh}$) is 90$\ensuremath{''}$" (4.1 Kinematics of the dense cloud)
   - fitting: Visual comparison, no formal fit  
  > "we compared the observed velocity channel maps and the evolved particle distributions from our kinematical models projected on the plane of the sky at the same line-of-sight velocities." (Analysis, Kinematical model of the arc structure)
   - validation: _not stated_
5. **Model envelope kinematics with relative motion**: Test-particle Ulrich-type infall and rotation plus extra line-of-sight Vrel (0, 0.3, 0.6, 0.9 km/s); synthetic C18O channel maps convolved with the beam; initial distribution pruned using observed channel maps  
  > "we added an additional velocity component ($V_{\rm rel}$) to all the particles in addition to their initial infalling and rotational velocities." (4.2 Kinematical model of the arc structure)
   - parameter: M*=1.8 Msun, centrifugal radius 100 au, i=47 deg, PA=138 deg, envelope radius 3000 au, density ∝ r^-1.5, evolution 1e4 yr, disk cylinder 100 au radius and 10 au height  
  > "We let these model envelopes evolve for $10^4$ yr" (4.2 Kinematical model of the arc structure)
   - parameter: T(r) = 15 (r/1000 au)^-0.6 K  
  > "the temperature profile in our model envelope is adopted to be $T(r) = 15 \times (r/1000{\rm\ au})^{-0.6}\ {\rm K}$." (4.2 Kinematical model of the arc structure)
   - assumption: Self-gravity ignored, collisionless particles, accretion onto disk removes particles  
  > "all the particles are assumed to be collisionless." (4.2 Kinematical model of the arc structure)
   - fitting: no formal fit; qualitative comparison of synthetic and observed channel maps; particles not overlapping 3 sigma emission removed  
  > "Those particles that do not overlap with the observed intensity distributions above the 3$\sigma$ level are removed from the initial particle distribution" (Initial particle distributions in our kinematical models)
   - validation: Compared synthetic and observed channel maps; solution not unique in Vrel and evolution time  
  > "Thus, there is no unique combination of $V_{\rm rel}$ and an evolutionary time to explain the observation." (4.2 Kinematical model of the arc structure)
6. **Estimate impact on mass infall rate**: Run models for longer than 1e4 yr and count particles that do not enter the disk  
  > "there are 60%, 80%, and 90% of particles, respectively, which do not encounter the disk region and leave the system." (5.2 Impact on the kinematics)
   - assumption: No other angular momentum removal such as magnetic braking  
  > "if there is no other mechanism, such as magnetic braking, to transfer the angular momenta of the envelope material away" (5.2 Impact on the kinematics)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.7.0-1 (pipeline); 4.7.0 (imaging): ACA calibration, clean mosaic imaging, feather combination  
  > "using CASA of version 4.7.0" (2.4 Combined maps)
- **Starlink** : JCMT data reduction  
  > "The data were reduced with Starlink (cite: Currie14) and the ORAC-DR pipeline (cite: Jenness15)" (2.1 JCMT observations)
- **ORAC-DR** : JCMT pipeline with reduce_science_narrowline recipe  
  > "the recipe of “reduce_science_narrowline” was adopted." (2.1 JCMT observations)
- **CLASS** : IRAM 30m data reduction  
  > "The data were reduced with CLASS" (2.2 IRAM 30m observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Tex of 13CO at V_LSR 5.4 km/s | 25 | 9 | K | 3 | $T_{\rm ex}$ is estimated to be 25$\pm$9 K with both $\tau$ of 0.1$\pm$0.1 at $V_{\rm LSR}$ of 5.4 km s$^{-1}$. |
| Tex of 13CO at V_LSR 7.3 km/s | 27 | 6 | K | 3 | At $V_{\rm LSR}$ of 7.3 km s$^{-1}$, $T_{\rm ex}$ is estimated to be 27$\pm$6 K |
| Tex of 13CO at peak velocity 6.4 km/s | 14 | 1 | K | 3 | $T_{\rm ex}$ is estimated to be 14$\pm$1 K |
| Tex of C18O at 6.7 km/s | 15 | 7 | K | 3 | $T_{\rm ex}$ is estimated to be 15$\pm$7 K |
| Expanding shell velocity | 0.3–0.9 | not stated | km/s | 4 | the large-scale ambient gas around is likely expanding at velocities of 0.3–0.9 km s$^{-1}$. |
| Required relative velocity of far side of envelope | 0.6–0.9 | not stated | km/s | 5 | $V_{\rm rel}$ of 0.6–0.9 km s$^{-1}$ is needed in our kinematical models to explain the high velocity observed in the blueshifted arc-like structure. |
| Fraction of particles not accreted for Vrel 0.3/0.6/0.9 | 60%, 80%, 90% | not stated | percent | 6 | there are 60%, 80%, and 90% of particles, respectively, which do not encounter the disk region and leave the system. |
| Decrease in mass infall rate | factor of two | not stated | dimensionless | 6 | the mass infalling rate from the envelope onto the disk in likely decreases by a factor of two |

## Qualitative findings

- C18O traces ambient dense gas with less outflow contamination than 13CO; C18O optically thin  
  > "the C$^{18}$O emission is optically thin, while the $^{13}$CO emission is optically thick at the peak velocity" (Summary)
- Arc-like structures are likely infalling envelope material, not disk ejecta  
  > "Therefore, the arc-like structures more likely originate from the extended envelope around ." (3.2 Combined maps)

## Claim tuples

- H: Relative motion between star and envelope explains excess velocity of blueshifted arc | E: Test-particle infall/rotation model with added Vrel and synthetic C18O channel maps compared to combined data | R: Vrel of 0.6–0.9 km/s on far side reproduces blueshifted arc velocity; asymmetric initial density reproduces morphology | F: Envelope has relative motion toward us, higher on far side | **supported**
- H: Large-scale expanding shell exists and impacts the envelope | E: C18O (2-1) IRAM 30m PV diagrams compared with expanding shell profiles | R: Expansion velocity 0.3–0.9 km/s, only blueshifted arcs | F: HL Tau at edge of shell driven by nearby source, comparable to Vrel | **partially**
- H: Arc structures are mass ejection from disk vs envelope infall | E: Combined ACA+ALMA+30m maps across velocity channels | R: Arcs grow smoothly toward lower velocity and merge with cloud; higher velocity at smaller radius | F: Arcs most likely infalling ambient material | **supported**
- H: The impact reduces mass infall onto disk | E: Long-duration model runs with different Vrel | R: Half of envelope accreted in two-Vrel model | F: Infall rate decreases by factor of two | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Single-dish data added to recover missing flux in ALMA maps and test velocity excess  
  > "These combined maps do not suffer from the effect of the missing flux" (3.2 Combined maps)
- Alternative: Star attracted by nearby objects rejected because it cannot explain why the envelope does not move with the star  
  > "Therefore, this scenario of being attracted and leaving its protostellar envelope is unlikely." (5.1 Possible relative motion)
- How they decided it was enough: _not stated_
- Limitation (authors): Evolutionary time and Vrel combination not unique  
  > "this evolutionary time is an arbitrary choice and is not a unique solution to explain the observational results." (4.2 Kinematical model of the arc structure)
- Limitation (authors): Mosaic fluxes overestimated by 10% due to CASA imaging issue  
  > "the fluxes in our mosaic map are overestimated by 10%." (2.4 Combined maps)
- Caveat (inferred, ours): Models compared qualitatively with no quantitative goodness-of-fit or uncertainty on Vrel
- Caveat (inferred, ours): Initial particle distribution is tuned to the data, introducing circularity
- Caveat (inferred, ours): Spherical shell geometry and 90" radius taken from literature
- Caveat (inferred, ours): Model excludes the large-scale ambient gas and disk

## Reproducibility

- Data public (paper): ACA/ALMA data under project 2015.1.00551.S; JCMT program M17AP086; IRAM project 143-16  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2015.1.00551.S." (Acknowledgements)
- Products in archive: _not stated_
- Code: _not stated_
- Missing: Kinematical model code and particle count/time-step
- Missing: 12-m ALMA calibration details (in Yen17)
- Missing: Exact clean parameters, masks and thresholds
- Data volume (inferred): Tens of GB for ACA+12m raw data; JCMT/IRAM data small
- Score (inferred): 3/5, Data identified and imaging steps largely stated, but model code is custom and analysis qualitative with missing parameters.
- Rediscovery candidate: no, Key results rely on a custom model compared qualitatively to the data, and single-dish data are not ALMA-archive public.

## Links

- Method: (cite: Ulrich76) (Infalling rotating envelope model used as base)
- Method: (cite: Mangum15) (LTE optical depth equations)
- Companion: (cite: Yen17) (Previous ALMA 12-m observations and arc-like structure discovery)
- Companion: (cite: Welch00) (Expanding shell suggested from 13CO(1-0))
- Related: ALMA 2015.1.00551.S
- Related: JCMT M17AP086
- Related: IRAM 30m 143-16

## Checks

```json
{
 "quotes": 77,
 "quotes_ok": 77,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 90,
  "stated": 59,
  "rate": 0.656
 },
 "evidence_ok": true
}
```
