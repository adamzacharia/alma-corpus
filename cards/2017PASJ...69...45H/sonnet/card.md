# ALMA deep field in SSA22: Blindly detected CO emitters and [C II] emitter candidates

`2017PASJ...69...45H` | Publications of the Astronomical Society of Japan 2017 | first author: Hayatsu, Natsuki H. | arXiv: 1702.07512 | DOI: 10.1093/pasj/psx018

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: high_z_galaxies
- Question: Can a blind line search in the ADF22 1.1 mm ALMA survey cube find CO and [CII] emitters, and what do they imply for the [CII] luminosity function and star formation rate density at z~6?  
  > "In this paper, we present a blind search for [Cii] emitters using ALMA Cycle 2 data" (Introduction)
- Target **ADF22 (SSA22 proto-cluster field)**: coordinates RA (J2000) = 22h17m34s, Dec (J2000) = +00d17'00''  
  > "ADF22 is a survey field with an area of $2' \times 3'$ centered on a $z = 3.09$ proto-cluster" (2 Observation); z/distance proto-cluster z = 3.09  
  > "ADF22 is a survey field with an area of $2' \times 3'$ centered on a $z = 3.09$ proto-cluster" (2 Observation); distance from _not stated_

## Data provenance

- ALMA projects: 2013.1.00162.S
- bands: Band 6 (1.1 mm)  
  > "observed in Band 6 in ALMA Cycle 2" (2 Observation)
- frequencies and spectral setup: four 1.875 GHz SPWs, central 263 GHz; searched 253.1–272.8 GHz  
  > "The field was observed using four 1.875 GHz spectral windows (SPW) with the central frequency of 263 GHz" (2 Observation)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.72'' x 0.62'' combined  
  > "The typical angular resolution of a combined data is $0''.72 \times 0''.62$" (2 Observation)
- max recoverable scale: _not stated_
- sensitivity: 0.7–0.9 mJy/beam at 36 km/s  
  > "The four SPWs have root-mean-square (RMS) noise level of 0.7, 0.7, 0.8 or 0.9 mJy beam$^{-1}$ at a 36 km s$^{-1}$ velocity resolution." (2 Observation)
- time on source: 4.5 min per pointing  
  > "The on-source time per pointing in the fields is 4.5 min." (2 Observation)
- observing dates: June 2014 and April 2015  
  > "ALMA Cycle 2 in June 2014 and April 2015" (2 Observation)
- pi or archival as stated: PI H. Umehata  
  > "Proposal ID 2013.1.00162.S, PI: H. Umehata" (2 Observation)
- Line: [CII] 158 um (1900.543 GHz)
- Line: CO J=9-8 (1036.912 GHz)
- Line: CO J=4-3 (461.041 GHz)
- Other facility **Subaru, CFHT, Spitzer, Chandra**: optical/NIR/MIR/X-ray counterpart data  
  > "we search for their counterparts in $u^*$ band taken with the Canada France Hawaii Telescope/MegaCam" (3 Method)
- External data: SFR-L[CII] relation for low-metallicity dwarfs  
  > "SFR-[Cii] luminosity relation (cite: delooze2014)" (4.3) [from (cite: delooze2014)]
- External data: SFR function at z = 6  
  > "SFR function at $z = 6$ (cite: smit2012)" (4.3) [from (cite: smit2012)]
- External data: L_IR of ADF22.4 (LineC)  
  > "$L_{\rm IR}$ of ADF22-LineC is referred to estimation of (cite: umehata2017)." (5 Discussion) [from (cite: umehata2017)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: CASA 4.5.3  
  > "The data are analyzed with Common Astronomy Software Application (casa) ver. 4.5.3" (3 Method)
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
- continuum subtraction: uvcontsub and clean  
  > "We make continuum-subtracted datacube by using uvcontsub and clean." (3 Method)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: boxcar window 0,2,...,12,15,18,21 slices (~18 km/s each)  
  > "The top-hat spectral smoothing window is set to be 0, 2, 4, ..., 12, 15, 18, ..., 21 slices" (3 Method)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Observation details  
  > "The details of the observation are described in (cite: umehata2017)." (2 Observation) [from (cite: umehata2017)]

### Not stated but needed to reproduce (our reading)

- clean parameters (weighting, robust, cell size, image size, threshold)
- line-free channels for uvcontsub
- calibration/flux scale details
- clumpfind other parameters and completeness
- hyperz settings
- spectral-line fitting details

## Analysis recipe

1. **Build S/N cubes**: Continuum-subtract, boxcar smooth spectra, normalize each slice by RMS  
  > "we normalise each slice by its RMS. We call a datacube thus-generated as “S/N cube”." (3 Method)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Blind source detection**: clumpfind on S/N cubes, match across smoothings, select >6 sigma and above max negative in inverted cube  
  > "We select clumps that have the S/N ratio larger than $6.0 \sigma$ and also larger than the maximum negative S/N ratio measured in the inverted S/N cube" (3 Method)
   - software: clumpfind
   - parameter: low threshold >= 4.5  
  > "threshold value “low” of clumpfind of $\geq$ 4.5" (3 Method)
   - fitting: _not stated_
   - validation: Compared 2014 and 2015 epochs and inverted cube  
  > "We also check line spectral features of the detected clumps (sources) in the datacube separately for those observed in 2014 and 2015." (3 Method)
3. **Identify counterparts and redshifts**: Multiwavelength counterpart search and SED fitting with hyperz  
  > "We fit the SED templates by (cite: bruzual1993) to the spectral coverage from UV to 8 $\rm \mu m$, assuming a Calzetti dust extinction law" (4.2)
   - software: hyperz
   - fitting: hyperz chi2 minimization  
  > "The result of SED fitting shows that reduced $\chi^2$ values becomes minimum at $z \sim 0.6-0.8$ (Figure B left)." (Result, Line Identification)
   - validation: _not stated_
4. **Derive L[CII], SFR, LF and SFRD**: L[CII] formula, De Looze SFR relation, divide mean SFR by survey volume  
  > "We calculate a conservative limit of [Cii] SFRD from the mean of the SFR$_{\rm [CII]}$ of the two sources divided by the survey volume" (5 Discussion)
   - assumption: LCDM Om=0.3, OL=0.7, h=0.7; Chabrier IMF  
  > "We calculate SFR assuming Chabrier initial mass function (IMF)" (Introduction)
   - fitting: _not stated_
   - validation: Compared with UV+IR SFR upper limit  
  > "The obtained SFR$_{\rm UV + FIR}$ is $<$ 30 $\rm M_\odot yr^{-1}$, being consistent with the SFR-$L_{\rm [CII]}$ relation of (cite: delooze2014)" (Discussion)

## Software

- **CASA** 4.5.3: data analysis, uvcontsub, clean  
  > "The data are analyzed with Common Astronomy Software Application (casa) ver. 4.5.3" (3 Method)
- **clumpfind** : line source search  
  > "We use clumpfind (cite: williams1994) to search emission line sources in the S/N cube." (3 Method)
- **hyperz** : SED fitting  
  > "SED fitting is calculated by using hyperz software" (3 Method)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Peak S/N of LineA | 6.5 | not stated | sigma | 2 | The peak S/N ratio are $6.5 \sigma$, $6.2 \sigma$, $7.7 \sigma$ and $6.5 \sigma$ |
| SFR[CII] LineA | 13 | +4/-5 | Msun/yr | 4 | 13$^{+4}_{-5}$ and 20$^{+9}_{-10}$ M$_\odot$/yr for ADF22-LineA and LineB |
| SFR[CII] LineB | 20 | +9/-10 | Msun/yr | 4 | 13$^{+4}_{-5}$ and 20$^{+9}_{-10}$ M$_\odot$/yr for ADF22-LineA and LineB |
| [CII] SFRD lower limit | > 7.5e-3 | not stated | Msun/yr/Mpc^3 | 4 | The derived [Cii] SFRD is $> 7.5 \times 10^{-3} \rm M_\odot yr^{-1}  Mpc^{-3}$. |

## Qualitative findings

- LineC is CO(9-8) at z=3.091; LineD likely CO(4-3) at z=0.71; LineA/B likely [CII] at z=6.5/6.0  
  > "two CO emitters at $z = 0.7$ and $3.1$ and two [Cii] emitter candidates at $z = 6.0$ and $6.5$" (Summary)

## Claim tuples

- H: Blind line search finds [CII] emitters at z~6 | E: clumpfind search of ADF22 S/N cubes | R: Four >6 sigma candidates; two without counterparts | F: Two [CII] candidates at z=6.0 and 6.5; one may be spurious | **partially**
- H: [CII]-based SFRD compares with UV SFRD | E: mean SFR divided by volume | R: > 7.5e-3 Msun/yr/Mpc^3 | F: Consistent with dust-uncorrected UV SFRD | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: LineA/B as 12CO, H2O, [NII], [OI], [OIII] emitters considered, disfavored by equivalent widths  
  > "we argue that ADF22-LineA and B are more likely [Cii] emitters at $z = 6.5$ and $6.0$, rather than CO emitters at $z \leq 3.1$" (4.3)
- How they decided it was enough: _not stated_
- Limitation (authors): One candidate may be spurious; LF from one source  
  > "one of the two [Cii] candidates has a relatively low-$\sigma$ and thus could possibly be a spurious source" (5 Discussion)
- Caveat (inferred, ours): No spectroscopic confirmation of [CII] candidates
- Caveat (inferred, ours): Completeness not quantified
- Caveat (inferred, ours): Few sources, small volume

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: clean imaging parameters
- Missing: clumpfind settings beyond threshold
- Missing: completeness and SFRD calculation details
- Data volume (inferred): ~100s GB (80 pointings, 4 SPWs, 2 epochs)
- Score (inferred): 3/5, Public data and recipe outline, but imaging and detection parameters are incomplete.
- Rediscovery candidate: no, Imaging parameters are missing and the results are largely candidate lists.

## Links

- Companion: (cite: umehata2017) (Source of the ADF22 data and observation details)
- Related: ADF22
- Related: ASPECS

## Checks

```json
{
 "quotes": 44,
 "quotes_ok": 44,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 4,
 "numeric_problems": 0,
 "fill": {
  "facts": 68,
  "stated": 33,
  "rate": 0.485
 },
 "evidence_ok": true
}
```
