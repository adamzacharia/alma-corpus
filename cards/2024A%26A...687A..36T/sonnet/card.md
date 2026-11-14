# JWST Observations of Young protoStars (JOYS). Linked accretion and ejection in a Class I protobinary system

`2024A&A...687A..36T` | Astronomy and Astrophysics 2024 | first author: Tychoniec, Łukasz | arXiv: 2402.04343 | DOI: 10.1051/0004-6361/202348889

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: star_formation
- Question: How do accretion and ejection interact in the Class I protobinary TMC1 (TMC1-W and TMC1-E), as seen with JWST MIRI-MRS and compared with ALMA cold gas and dust maps?  
  > "We aim to characterize the interplay between accretion and ejection in the low-mass Class I protobinary system TMC1, comprising two young stellar objects: TMC1-W and TMC1-E at a 85 au separation." (abstract)
- Target **TMC1 (IRAS 04381+2540; TMC1-W and TMC1-E)**: coordinates 4h41m12.7s +25d46m34.8s (J2000)  
  > "The target position was 4$^h$41$^m$12$^s$.7 +25${^\circ}$46$'$34.8$''$ (J2000)." (Observations); "the binary stars were resolved with the projected separation of 85 au" (Introduction); z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2017.1.01350.S, 2017.1.01413.S
- bands: _not stated_
- frequencies and spectral setup: CO 2-1 230.538 GHz (0.63 km/s), SO 5_6-4_5 219.9494 GHz (0.33 km/s), CN 2-1 225.632 GHz (0.08 km/s)  
  > "CO 2–1 and SO $5_6$–$4_5$ has 0.63 km s$^{-1}$ and 0.33 km s$^{-1}$ velocity resolution data, respectively." (Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: CO/SO beam 0.41'' x 0.29''; CN beam 0.57'' x 0.38''  
  > "with a synthesized beam (resolution element) of 0.41$''$ $\times$ 0.29$''$" (Observations); "CN $J$$=$2–1 225.632 GHz data with a synthesized beam of 0.57$''$ $\times$ 0.38$''$" (Observations)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: Archival ALMA data; PI Tychoniec (2017.1.01350.S), PI van 't Hoff (2017.1.01413.S)  
  > "For the analysis, we also used archival ALMA data." (Observations)
- Line: CO J=2-1 (230.538 GHz)
- Line: SO 5_6-4_5 (219.9494 GHz)
- Line: CN J=2-1 (225.632 GHz)
- Other facility **JWST MIRI-MRS**: 4.9-28.6 micron IFU spectra and line maps (program 1290, JOYS)  
  > "JWST MIRI-MRS observations were obtained on March 4, 2023, as part of the JWST Observations of Young ProtoStars (JOYS) Guaranteed Time Observations (GTO) PID 1290" (Observations)
- Other facility **HST NICMOS**: Archival 1.6 micron scattered light image  
  > "We show an archival *Hubble* Space Telescope NICMOS 1.6 $\mu$m image of the TMC1 system" (3.3)
- External data: ALMA CO, SO, CN maps previously presented  
  > "Complementary ALMA observations already presented in (cite: Tychoniec.vanDishoeck.ea2021) are used to compare the MIR emission with cold gas tracers." (Introduction) [from (cite: Tychoniec.vanDishoeck.ea2021)]
- External data: Stellar properties M*=0.15-0.20 Msun, R*=3.0-2.48 Rsun  
  > "M$_\star$=0.15-0.20 $\mbox{M}_\odot$ and R$_\star$=3.0-2.48 $R_\odot$ for birthline and 1 Myr" (3.1) [from (cite: Fiorellino.Tychoniec.ea2023)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: Pipeline-calibrated ALMA images from the archive  
  > "We used pipeline-calibrated data images obtained from the ALMA archive for both projects." (Observations)
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
- continuum subtraction: 1.3 mm continuum image built from line-free spectral regions of the CN dataset  
  > "we used it to construct a continuum image at 1.3 mm from line-free spectral regions for further analysis" (Observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- ALMA data/maps of CO, SO, CN taken from earlier paper  
  > "we present ALMA maps of CO 2–1 (central panel), SO $5_6$–$4_5$ (right panel), and CN 2–1 (contours in the central and right panel) from (cite: Tychoniec.vanDishoeck.ea2021)" (3.3) [from (cite: Tychoniec.vanDishoeck.ea2021)]

### Not stated but needed to reproduce (our reading)

- ALMA CASA/pipeline versions and imaging parameters (weighting, cleaning, masks)
- Line-free channels for the continuum
- Distance to TMC1
- Moment map construction details for ALMA

## Analysis recipe

1. **Extract MIRI-MRS spectra and line intensities**: Extract spectra with apertures, fit Gaussians to lines, divide flux by aperture area  
  > "A Gaussian profile was fitted to each identified emission line in the spectra and the flux value of the line was estimated by integrating the region under the Gaussian." (3.1)
   - software: JWST pipeline
   - parameter: point-source aperture r = 0.033 x lambda + 0.106''; outflow aperture 0.25'' radius  
  > "The extraction aperture at the point source was set to $r_{a} = 0.033 \times \lambda + 0.106\ensuremath{''}$" (3.1)
   - fitting: _not stated_
   - validation: _not stated_
2. **Derive extinction**: Silicate 9.7 um depth with polynomial continuum on sources; simultaneous H2 rotational temperature and A_K fit at outflow positions  
  > "We fit simultaneously for the rotational temperature and extinction value" (3.1)
   - assumption: A_V=18.5 x tau (ISM) or 9 x tau (dense clouds); A_V/A_K=7.75 for R_V=5  
  > "convert to visual extinction with A$_V$/A$_K$ = 7.75 for R$_V$ = 5" (Extinction measurement)
   - fitting: _not stated_
   - validation: _not stated_
3. **H2 rotation diagram**: Two linear components fit to v=0-0 transitions  
  > "By fitting simultaneously two linear functions to the data, the negative inverse of the slope provides the rotational temperature" (3.1.2)
   - software: pdrtpy
   - fitting: _not stated_
   - validation: _not stated_
4. **Accretion rate from HI 7-6**: Rigliaco et al. 2015 line-L_acc relation, then Mdot = L_acc G M*/R*  
  > "\dot{M}= L_{\rm acc}GM_{*}R_{*}^{-1}," (3.1.1)
   - fitting: _not stated_
   - validation: _not stated_
5. **Compare MIRI maps with ALMA and HST maps**: Qualitative comparison of CO, SO, CN maps with H2 and ion maps  
  > "CO emission traces the entrained outflow material piling up at the outflow cavity walls of TMC1-E." (3.3)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **JWST calibration pipeline** 1.11.2: Reduction of MIRI-MRS data  
  > "The data were reduced with the JWST pipeline v.1.11.2" (2.1)
- **VIP** : Bad-pixel routine  
  > "a bad-pixel routine is applied to calibrated files using the Vortex Image Processing (VIP) package" (2.1)
- **pdrtpy** : H2 rotational diagram  
  > "we construct a rotational diagram using `pdrtpy` package" (3.1.2)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| tau_9.7 TMC1-W | 1.30 | not stated | dimensionless | 2 | We find $\tau_{\textrm 9.7}=1.30$ and $\tau_{\textrm 9.7}=1.95$ for TMC1-W and TMC1-E, respectively. |
| tau_9.7 TMC1-E | 1.95 | not stated | dimensionless | 2 | We find $\tau_{\textrm 9.7}=1.30$ and $\tau_{\textrm 9.7}=1.95$ for TMC1-W and TMC1-E, respectively. |
| H2 warm component temperature | 661 | 28 | K | 3 | a warm component at 661 $\pm$ 28 K and a hot component at 1849 $\pm$ 167 K |
| H2 hot component temperature | 1849 | 167 | K | 3 | a warm component at 661 $\pm$ 28 K and a hot component at 1849 $\pm$ 167 K |
| Accretion rate TMC1-W | (0.16-14.8)e-11 | range | Msun/yr | 4 | TMC1-W to be $(0.16-14.8) \times 10^{-11}\ \mbox{M}_\odot\ {\rm yr}^{-1}$ |
| Jet mass-loss rate from [Fe II] 25.96 um | 6.7e-9 | not stated | Msun/yr | 0 | We derived a mass-loss rate of 6.7 $\times 10^{-9}\ \mbox{M}_\odot\ {\rm yr}^{-1}$. |

## Qualitative findings

- Streamer seen in CN and SO infalls onto TMC1-E, which hosts the H2 disk wind; TMC1-W drives a collimated [Fe II] jet; jets are parallel.  
  > "With ALMA, we detected an accretion streamer infalling from $>$ 1000 au scaling onto the TMC1-E component." (abstract)

## Claim tuples

- H: Envelope infall onto the disk affects the wide-angle wind of TMC1-E | E: Compare MIRI H2 maps with ALMA CO, SO, CN | R: Streamer lands on TMC1-E, which has the H2 disk wind | F: Infall may feed the disk wind | **partially**
- H: Disk-to-star accretion relates to the TMC1-W jet | E: HI recombination lines to accretion rate | R: HI lines brighter toward TMC1-W | F: TMC1-W is a stronger accretor with a collimated jet | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Different evolutionary stages, disk truncation or magnetic fields could explain the outflow differences  
  > "It is possible that the two protostars have followed different evolution histories and that, at present, TMC1-W has ended up to be more evolved than TMC1-E." (4.3)
- How they decided it was enough: _not stated_
- Limitation (authors): Extinction and accretion rate highly uncertain; TMC1-W contamination of TMC1-E aperture  
  > "The considerable uncertainty on the extinction correction also adds to the difficulty when comparing the two sources." (3.1.1)
- Caveat (inferred, ours): ALMA streamer interpretation is qualitative, with no kinematic modelling
- Caveat (inferred, ours): Accretion rate relies on one line with a large calibration scatter

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: ALMA imaging parameters
- Missing: Details of MIRI custom steps (in prep. references)
- Data volume (inferred): ALMA: pipeline products, a few GB; JWST: a few GB
- Score (inferred): 3/5, ALMA role is minor and qualitative; the main results come from JWST with limited ALMA processing detail.
- Rediscovery candidate: no, ALMA part is qualitative and the main numeric results come from JWST data.

## Links

- Method: (cite: Rigliaco.Pascucci.ea2015) (HI 7-6 to accretion luminosity relation)
- Method: (cite: Watson.Calvet.ea2016) ([Fe II] mass-loss rate relation)
- Companion: (cite: Tychoniec.vanDishoeck.ea2021) (Presents the ALMA data used)
- Related: JOYS

## Checks

```json
{
 "quotes": 42,
 "quotes_ok": 42,
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
  "facts": 71,
  "stated": 25,
  "rate": 0.352
 },
 "evidence_ok": true
}
```
