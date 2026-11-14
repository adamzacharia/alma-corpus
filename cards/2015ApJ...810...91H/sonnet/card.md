# Optical-Infrared Properties of Faint 1.3 mm Sources Detected with ALMA

`2015ApJ...810...91H` | The Astrophysical Journal 2015 | first author: Hatsukade, Bunyo | arXiv: 1508.00644 | DOI: 10.1088/0004-637X/810/2/91

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies
- Question: What are the optical-IR properties of faint (0.2-1.0 mJy) 1.3 mm ALMA sources, and are they more like normal star-forming galaxies than classical SMGs?  
  > "In this paper, we present the optical–IR properties of ALMA-detected faint sources ($S_{\rm 1.3mm} = 0.2$–1.0 mJy)." (Introduction)
- Target **SXDS field, 20 pointings on z~1.4 star-forming galaxies (8 ALMA sources AS1-AS8)**: coordinates AS1 02 17 13.63 -05 09 40.0 (J2000); others in Table  
  > "The targets were extracted from a stellar mass limit ($>$$10^{9.5}$ $M_{\odot}$) sample whose redshifts and H$\alpha$ SFR were obtained by near-infrared (NIR) spectroscopy" (Data); z/distance z ~ 1.4 (z_spec 1.348-1.451 for targets)  
  > "The targets were extracted from a stellar mass limit ($>$$10^{9.5}$ $M_{\odot}$) sample whose redshifts and H$\alpha$ SFR were obtained by near-infrared (NIR) spectroscopy" (Data); distance from NIR spectroscopy with FMOS (Yabe et al.); photometric redshifts from SED fits  
  > "The targets were extracted from a stellar mass limit ($>$$10^{9.5}$ $M_{\odot}$) sample whose redshifts and H$\alpha$ SFR were obtained by near-infrared (NIR) spectroscopy" (Data)

## Data provenance

- ALMA projects: 2011.0.00648.S
- bands: Band 6 (1.3 mm)  
  > "We conducted ALMA band 6 observations toward 20 star-forming galaxies" (Data)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: 1875 MHz (488.28 kHz x 3840 channels), frequency domain mode  
  > "The correlator was used in the frequency domain mode with a bandwidth of 1875 MHz (488.28 kHz $\times$ 3840 channels)." (Data)
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: synthesized beam ~0.6''-1.3'' (major axis FWHM)  
  > "The synthesized beam size of the ALMA observations is $\sim$0.6$''$–1.3$''$ (major axis FWHM)" (Counterpart Identification)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: 8-15 minutes per pointing, 20 pointings  
  > "We obtained 20 pointings centered on the 20 targets, each with on-source observing time of 8–15 minutes." (Data)
- observing dates: August 2012, Cycle 0, 23-25 antennas  
  > "The ALMA observations were carried out in August 2012 with 23–25 antennas during the cycle 0 session." (Data)
- pi or archival as stated: _not stated_
- Other facility **Subaru/FMOS**: NIR spectroscopy for target redshifts and Halpha SFR  
  > "redshifts and H$\alpha$ SFR were obtained by near-infrared (NIR) spectroscopy with the Fibre Multi-Object Spectro-graph" (Data)
- Other facility **UKIRT/WFCAM**: K-band (and J, H) imaging and K-selected catalog  
  > "UKIRT/Wide Field Camera (WFCAM) $K_s$ (cite: lawr07)" (Counterpart Identification)
- Other facility **Spitzer IRAC/MIPS**: 3.6-8.0 micron and 24 micron imaging  
  > "*Spitzer*/Infrared Array Camera (IRAC) 3.6 $\mu$m, and MIPS 24 $\mu$m (Dunlop et al. in preparation)" (Counterpart Identification)
- External data: K-band selected source catalog with photometric redshifts, stellar masses, SFRs (limit Ks=24.6)  
  > "Optical/IR counterparts for the ALMA sources are searched in the $K$-band-selected source catalog of (cite: yabe12; yabe14)." (Counterpart Identification) [from (cite: yabe12; yabe14)]
- External data: ALESS SMG sample at 1<z<2 for comparison  
  > "The ALESS SMGs in the same redshift range ($1.0 < z < 2.0$) are taken from (cite: simp14)." (Optical–IR Properties) [from (cite: simp14)]

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

- Photometric redshift, stellar mass, color excess and UV SFR from SED fitting  
  > "The color excess was derived from the rest-frame UV color, and the SFR was derived from the rest-frame UV luminosity density corrected for extinction by using the color excess (cite: yabe12; yabe14)." (Optical–IR Properties) [from (cite: yabe12; yabe14)]
- Source detection, flux measurement and spurious probability for ALMA sources (Hatsukade 2013 method)  
  > "the expected number of submm sources with $S_{\rm 1.3mm} \ge 0.2$ mJy is $\sim$0.1–0.2 (cite: hats13)." (Overdense around ALMA sources) [from (cite: hats13)]

### Not stated but needed to reproduce (our reading)

- ALMA calibration, CASA version, flux calibrator and imaging parameters (robust, taper, cleaning)
- Source extraction and C_spurious derivation method
- SED fitting code and templates details (in Yabe et al.)
- Primary-beam correction and rms per field
- Method for expected number counts of K-band sources in 5'' radius

## Analysis recipe

1. **Identify K-band counterparts of ALMA sources**: Positional match of ALMA sources (SN>=4.0) to K-band catalog; sources with offsets above expected accuracy ~0.3-0.4'' regarded unidentified  
  > "AS2 and AS7 have a larger offset (0.5$''$–0.6$''$) than the expected positional accuracy of $\sim$0.3$''$–0.4$''$, and we regard them as unidentified." (Counterpart Identification)
   - fitting: _not stated_
   - validation: Sum of C_spurious ~1 used to assess spurious contamination  
  > "The sum of $C_{\rm spurious}$ of the 8 ALMA sources is $\sim$1" (Counterpart Identification)
2. **Derive physical properties of counterparts**: SED fits to far-UV to mid-IR photometry for z_phot and stellar mass; SFR from extinction-corrected UV  
  > "The photometric redshift and the stellar mass are derived from SED fits to far-UV–mid-IR data" (Optical–IR Properties)
   - parameter: Delta z = 0.05 adopted for photo-z error  
  > "We adopt $\Delta z = 0.05$ for the error of photometric redshifts." (Optical–IR Properties)
   - assumption: Salpeter IMF, 0.1-100 Msun  
  > "The Salpeter IMF (cite: salp55) with a mass range of 0.1–100 $M_{\odot}$ was assumed." (Optical–IR Properties)
   - fitting: _not stated_
   - validation: Photo-z scatter vs spec-z sigma~0.05  
  > "The standard deviation of the difference between photometric and spectroscopic redshifts in the sample of (cite: yabe14) is $\sigma \sim 0.05$." (Optical–IR Properties)
3. **Compare ALMA-detected and undetected K-band sources, expected SFR for 0.2 mJy**: Modified blackbody dust mass and L_FIR, converted to SFR with Kennicutt 1998 relation, as function of redshift  
  > "We estimate the SFR by using the SFR–far-IR (FIR) luminosity ($L_{\rm FIR}$) relation of (cite: kenn98)." (ALMA-detected and undetected sources)
   - assumption: kappa_d(125 um)=2.64±0.29 m^2/kg, beta=1.5, T_dust=30-40 K  
  > "We adopt $\kappa_d(125\ \mu m) = 2.64 \pm 0.29$ m$^2$ kg$^{-1}$ (cite: dunn03), $\beta = 1.5$, and $T_{\rm dust} = 30$–40 K" (ALMA-detected and undetected sources)
   - fitting: _not stated_
   - validation: _not stated_
4. **Test for overdensity around AS4/AS5**: Compare observed count of K-band and submm sources within 5'' with expected counts  
  > "The expected number of $K$-band sources with $K_s \le 23.55$ mag (the magnitude of the faintest source in this region) or with $K_s \le 22.44$ mag" (Overdense around ALMA sources)
   - fitting: _not stated_
   - validation: _not stated_

## Software


## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| K-band counterparts identified | 4 of 8 ALMA sources | not stated | dimensionless | 1 | We identified $K$-band counterparts for four out of the 8 ALMA sources. |
| Average ALMA-K offset (4 sources) | (-0.10, +0.09) | ±0.13'', ±0.20'' | arcsec | 1 | $(\Delta$RA, $\Delta$Dec) $= (-0.10\ensuremath{''} \pm 0.13\ensuremath{''}, +0.09\ensuremath{''} \pm 0.20\ensuremath{''})$ |
| Expected K-band sources within 5'' (Ks<=23.55 / 22.44) | 0.7 / 0.3 | not stated | dimensionless | 4 | is 0.7 and 0.3, respectively. |
| AS1 stellar mass | 1.87e11 | +0.28/-0.00 e11 | Msun | 2 | $1.87^{+0.28}_{-0.00} \times 10^{11}$ |

## Qualitative findings

- ALMA-detected K-band sources are brighter, more massive and more actively star-forming than undetected ones  
  > "ALMA-detected sources tend to be brighter, more massive, and more actively forming stars." (abstract)

## Claim tuples

- H: Faint ALMA sources are more like normal star-forming galaxies than classical SMGs | E: Placed counterparts in stellar mass-SFR plane against ALESS SMGs and main sequence | R: Serendipitous source lies on the main sequence while over half of ALESS SMGs lie above | F: Faint ALMA sources resemble normal star-forming galaxies | **partially**
- H: A multi-source overdense region exists near AS4/AS5 | E: Counted K-band and ALMA sources within 5'' and compared to expectations | R: Five K-band sources, two ALMA, z~1.3-1.6; expected 0.3-0.7 K-band and 0.1-0.2 submm | F: Possible pre-merging system | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Non-detection in K may be due to spurious ALMA source, dust obscuration, higher redshift or larger offset  
  > "Another possibility is that they are obscured by dust or at higher redshift" (Counterpart Identification)
- How they decided it was enough: _not stated_
- Limitation (authors): Fields centered on z~1.4 galaxies could be biased regions  
  > "We note that the ALMA observing fields were centered on $z \sim 1.4$ star-forming galaxies, which could be biased regions." (Optical–IR Properties)
- Caveat (inferred, ours): Very small sample (8 sources, 4 with counterparts); main-sequence conclusion rests on one serendipitous source
- Caveat (inferred, ours): Overdensity significance not quantified beyond crude expected counts
- Caveat (inferred, ours): No ALMA data processing details

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: ALMA imaging/cleaning parameters and source-finding procedure
- Missing: K-band catalog and SED results are from Yabe et al.
- Missing: MIPS/IRAC data from unpublished Dunlop et al.
- Data volume (inferred): ~10-30 GB raw (20 Cycle 0 pointings)
- Score (inferred): 3/5, ALMA project code given and counterpart matching is simple, but ALMA reduction and source extraction are not described and the catalog comes from other papers.
- Rediscovery candidate: no, Key ALMA processing and the catalog and SED inputs are not specified here.

## Links

- Method: (cite: hats13) (ALMA faint source detection and number counts)
- Method: (cite: yabe14) (K-band catalog and SED fitting)
- Related: ALESS
- Related: SXDS

## Checks

```json
{
 "quotes": 36,
 "quotes_ok": 36,
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
  "stated": 28,
  "rate": 0.412
 },
 "evidence_ok": true
}
```
