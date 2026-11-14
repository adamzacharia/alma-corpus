# Hyperluminous starburst gives up its secrets

`2019MNRAS.489..427I` | Monthly Notices of the Royal Astronomical Society 2019 | first author: Ivison, R. J. | arXiv: 1908.03199 | DOI: 10.1093/mnras/stz2180

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: high_z_galaxies, agn_and_quasars
- Question: What is the nature of the hyperluminous starburst HATLAS J084933-W: does it host an AGN, and is there a fifth protocluster member?  
  > "Here, we use ALMA to confirm a more distant, fifth protocluster member, and present X-ray and rest-frame optical imaging spectroscopy of the brightest, an unlensed hyperluminous IR galaxy (HyLIRG)." (abstract)
- Target **HATLAS J084933.4+021443**: coordinates X-ray source at 08h49m33.59s, +02d14m44.6s (J2000), component W  
  > "Its redshift was determined quickly via multiple CO lines ($z=2.41$" (Introduction); "such that 1 arcsec corresponds to 8.1 kpc at $z=2.41$" (Introduction); z/distance z=2.41  
  > "Its redshift was determined quickly via multiple CO lines ($z=2.41$" (Introduction); "such that 1 arcsec corresponds to 8.1 kpc at $z=2.41$" (Introduction); distance from CO lines (harris12; ivison13; gomez18)  
  > "Its redshift was determined quickly via multiple CO lines ($z=2.41$" (Introduction); "such that 1 arcsec corresponds to 8.1 kpc at $z=2.41$" (Introduction)

## Data provenance

- ALMA projects: 2013.1.00164.S
- bands: Band 6, 245 GHz (1.22 mm)  
  > "The ALMA band-6 245-GHz (1.22-mm) data used here were obtained for project 2013.1.00164.S" (2.3 ALMA)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.49 x 0.48 arcsec2 FWHM, PA 127 deg  
  > "the synthesised beam measures $0.49 \times 0.48$ arcsec$^2$ FWHM, with the major axis at a position angle, measured East of North, of $127^{\circ}$." (2.3 ALMA)
- max recoverable scale: _not stated_
- sensitivity: rms 38 uJy/beam  
  > "The image has an r.m.s. noise level, $\sigma= 38\,\mu$Jy beam$^{-1}$" (2.3 ALMA)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: Archival data from a project targeting CH+ (falgarone17)  
  > "targeting the CH$^+$ line (cite: falgarone17)" (2.3 ALMA)
- Other facility **XMM-Newton**: X-ray spectrum and detection of W; upper limit for E  
  > "HATLAS J084933 was observed with *XMM-Newton* on 2017 April 22–23 (AO15, proposal 078435)." (2.2 XMM-Newton)
- Other facility **VLT/KMOS**: K-band IFU spectrum of W (Halpha, [N II])  
  > "The target was observed in the $K$ band, with a total integration time (on source) of 80 min, with a median seeing of 0.7 arcsec." (2.1 KMOS/VLT)
- External data: JVLA CO J=1-0 and Spitzer IRAC imaging, HST F110W image used with the ALMA map  
  > "we show the JVLA $^{12}$CO $J=1$–0 imaging and the *Spitzer* IRAC imaging from" (3 Results) [from ivison13 (as referenced)]
- External data: Component W SED and S1.22mm used to scale E's IR luminosity  
  > "Scaled from component W, where $S_{\rm 1.22mm}=8.29\pm 0.13$ mJy and log $L_{\rm IR}$ = 13.52" (Table 1) [from not stated explicitly]

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

- task: CASA clean  
  > "was made using the clean task in the Common Astronomy Software Application package (cite: mcmullin07)" (2.3 ALMA)
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: Channels around the CH+ line discarded  
  > "where we have discarded the channels around the CH$^+$ line" (2.3 ALMA)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.49 x 0.48 arcsec2, PA 127 deg  
  > "the synthesised beam measures $0.49 \times 0.48$ arcsec$^2$ FWHM" (2.3 ALMA)
- final rms: 38 uJy/beam  
  > "The image has an r.m.s. noise level, $\sigma= 38\,\mu$Jy beam$^{-1}$" (2.3 ALMA)

### Inherited from earlier work

- ALMA data from a project targeting CH+  
  > "targeting the CH$^+$ line (cite: falgarone17)" (2.3 ALMA) [from falgarone17]

### Not stated but needed to reproduce (our reading)

- CASA version
- weighting/robust, cell and image size, clean threshold
- line-free channels and CH+ channel range
- primary beam correction
- calibration details and flux scale uncertainty
- how the 1.47 mJy flux of E was measured

## Analysis recipe

1. **Make ALMA band-6 continuum image**: clean in CASA with CH+ line channels discarded  
  > "Our resulting continuum image, where we have discarded the channels around the CH$^+$ line, was made using the clean task" (2.3 ALMA)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Identify component E and derive its properties**: Detect 6 sigma continuum source, match to IRAC/CO; scale IR luminosity from W's SED; SFR via Kennicutt98 with Chabrier IMF  
  > "Scaling from the band-6 flux density and SED of component W, component E has an IR luminosity of approximately $6\times 10^{12}$ L$_\odot$." (3 Results)
   - assumption: Same SED as W; alpha_CO=0.8  
  > "thereby adopting the same SED as W for component E." (Table 1)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : continuum imaging with clean  
  > "was made using the clean task in the Common Astronomy Software Application package (cite: mcmullin07)" (2.3 ALMA)
- **XSPEC** 11.3: X-ray spectral fitting  
  > "The X-ray spectrum was modelled using version 11.3 of the X-ray spectral fitting package, XSPEC." (3 Results)
- **SAS** 15.0: XMM-Newton reduction  
  > "were reduced with version 15.0 of the *XMM-Newton* Science Analysis Software (SAS)" (2.2 XMM-Newton)
- **SPARK/ESOREX** : KMOS data reduction  
  > "The data reduction was performed by using SPARK (cite: davies13), implemented using ESOREX (cite: freudling13)." (2.1 KMOS/VLT)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| ALMA band-6 rms | 38 | not stated | uJy/beam | 1 | $\sigma= 38\,\mu$Jy beam$^{-1}$ |
| E 1.22-mm flux density | 1.47 | 0.24 | mJy | 2 | / 1.22 mm$^{\rm a}$ / $1.47\pm 0.24$ / mJy; ALMA / |
| E IR luminosity | log L_IR = 12.8 | +0.1/-0.2 | Lsun | 2 | $12.8^{+0.1}_{-0.2}$ |
| E SFR | 650 | not stated | Msun/yr | 2 | this implies an SFR of 650 M$_\odot$ yr$^{-1}$ |
| Black hole mass of W | 2e9 | not stated | Msun | 0 | $M_{\rm bh} \approx 2\times 10^9$ M$_\odot$ (cite: schulze18) |
| Intrinsic N_H of W | 5e21 | 3e21 | cm^-2 | 0 | $N_{\rm H} =(5\pm 3) \times
10^{21}$ cm$^{-2}$ |
| 2-10 keV luminosity of W | 1.4e45 | not stated | erg/s | 0 | $L_{\rm X}=1.4\times 10^{45}$ erg s$^{-1}$ |

## Qualitative findings

- E is a dusty, gas-rich fifth protocluster member, coincident with a very red IRAC galaxy  
  > "Component E can thus be added to the inventory of dusty, gas-rich galaxies that form part of the protocluster" (3 Results)

## Claim tuples

- H: Is there a fifth protocluster member? | E: ALMA band-6 continuum compared with IRAC, CO and HST | R: 6 sigma source E coincident with red IRAC and CO source | F: E is a fifth member; protocluster spans about 120 kpc | **supported**
- H: Does W host an AGN? | E: KMOS Halpha fit and XMM-Newton spectrum | R: Broad Halpha 9,700 km/s FWHM, L_X 1.4e45 erg/s | F: W hosts a Type-1 AGN with M_bh about 2e9 Msun | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): E's CO line width is uncertain because of low signal to noise  
  > "The signal to noise is too low for us to be fully confident" (3 Results)
- Caveat (inferred, ours): ALMA processing is minimally described
- Caveat (inferred, ours): E's IR luminosity assumes W's SED
- Caveat (inferred, ours): The AGN bolometric correction is uncertain by about a factor of two

## Reproducibility

- Data public (paper): ALMA project code given and acknowledged; archival  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2013.1.00164.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: CASA version and clean parameters
- Missing: flux measurement method for E
- Data volume (inferred): about 10-50 GB for the ALMA project
- Score (inferred): 3/5, The ALMA part is archival and public, but the processing is described in only a few lines.
- Rediscovery candidate: no, ALMA is a minor part, imaging parameters are missing, and the main results come from XMM and KMOS.

## Links

- Companion: ivison13 (cite) (Earlier multi-wavelength study of HATLAS J084933)
- Companion: gomez18 (cite) (ALMA greybody and dynamics of W)
- Related: H-ATLAS

## Checks

```json
{
 "quotes": 41,
 "quotes_ok": 41,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 61,
  "stated": 27,
  "rate": 0.443
 },
 "evidence_ok": true
}
```
