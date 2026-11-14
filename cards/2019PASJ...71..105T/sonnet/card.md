# Rotating ionized gas ring around the Galactic center IRS13E3

`2019PASJ...71..105T` | Publications of the Astronomical Society of Japan 2019 | first author: Tsuboi, Masato | arXiv: 1907.12311 | DOI: 10.1093/pasj/psz089

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: milky_way_ism, agn_and_quasars
- Question: Is there a rotating ionized gas ring around IRS13E3 that would give a reliable enclosed mass supporting an intermediate-mass black hole?  
  > "If IRS13E3 is an IMBH, an ionized gas ring would be rotating around it." (Introduction); "We have searched such ionized gas with ALMA in order to prove our hypothesis that IRS13E3 is an IMBH." (Introduction)
- Target **IRS13E3 (Galactic Center IRS13E complex)**: coordinates continuum peak ICRS 17h45m39.7888s, -29d00m29.7614s  
  > "Throughout this paper, we adopt 8.0 kpc as the distance to the Galactic center" (Introduction); "The position is $\alpha_{\rm ICRS}=17^{\rm h}45^{\rm m}39^{\rm s}.7888(\pm0^{\rm s}.00005)$" (Results); z/distance 8.0 kpc (Galactic center distance)  
  > "Throughout this paper, we adopt 8.0 kpc as the distance to the Galactic center" (Introduction); "The position is $\alpha_{\rm ICRS}=17^{\rm h}45^{\rm m}39^{\rm s}.7888(\pm0^{\rm s}.00005)$" (Results); distance from adopted from literature (Ghez, Gillessen, Schodel2009, Boehle)  
  > "Throughout this paper, we adopt 8.0 kpc as the distance to the Galactic center" (Introduction); "The position is $\alpha_{\rm ICRS}=17^{\rm h}45^{\rm m}39^{\rm s}.7888(\pm0^{\rm s}.00005)$" (Results)

## Data provenance

- ALMA projects: 2017.1.00503.S
- bands: _not stated_
- frequencies and spectral setup: 4 spectral windows centered at 217.5, 219.5, 234.0, 231.9 GHz; last covers H30alpha; 2.0 GHz coverage, 15.625 MHz resolution (~20 km/s)  
  > "The center frequencies of the spectral windows are $f_c=217.5, 219.5, 234.0,$ and $231.9$ GHz, respectively." (Observation and Data Reduction); "The frequency coverage and frequency resolution are 2.0 GHz and 15.625 MHz, respectively." (Observation and Data Reduction)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: longest baseline antenna configuration of ALMA  
  > "The observation epochs were in the period of the longest baseline antenna configuration of ALMA." (Observation and Data Reduction)
- baselines: _not stated_
- angular resolution: 0.037" x 0.025", PA=85 deg (continuum, natural weighting); 0.037" x 0.024", PA=87 deg (channel maps)  
  > "The angular resolution using “natural weighting" is $0\ensuremath{''}.037 \times 0\ensuremath{''}.025, PA=85^\circ$" (Observation and Data Reduction)
- max recoverable scale: _not stated_
- sensitivity: channel maps 1 sigma = 90 uJy/beam (2.3 K); continuum 1 sigma = 50 uJy/beam (1.3 K)  
  > "$1\sigma=90~ \mu$Jy beam$^{-1}$ or 2.3 K in $T_\mathrm{B}$ in the emission-free areas" (Observation and Data Reduction); "The sensitivity is $1\sigma=50~ \mu$Jy beam$^{-1}$ or 1.3 K in $T_\mathrm{B}$ in the emission-free areas." (Observation and Data Reduction)
- time on source: _not stated_
- observing dates: 5 Oct. 2017 to 20 Oct. 2017 (ten days)  
  > "The observations were performed in ten days from 5 Oct. 2017 to 20 Oct. 2017." (Observation and Data Reduction)
- pi or archival as stated: Cycle 5 program, PI M. Tsuboi  
  > "as an ALMA Cy.5 program (2017.1.00503.S. PI M.Tsuboi)" (Observation and Data Reduction)
- Line: H30alpha recombination line H30alpha (231.9 GHz)
- Other facility **Chandra**: X-ray point source CXOGCJ174539.7-290029 counterpart (from Muno catalog)  
  > "IRS13E3 is located within the $95\%$ error circle ($0\ensuremath{''}.3$) of the X-ray point source detected by CHANDRA" (Discussion)
- External data: 340 GHz continuum map of Sgr A* vicinity and IRS13E complex (Figure 1a,b)  
  > "Figure 1a shows the continuum map of the vicinity of Sgr A$^\ast$ at 340 GHz (cite: Tsuboi2017b)." (Results) [from (cite: Tsuboi2017b)]
- External data: Chandra X-ray 2-8 keV fluxes of CXOGCJ174539.7-290029 and Sgr A*  
  > "The X-ray flux at $2-8$ keV of the source is reported to $F_\mathrm {2-8}=1.12\times10^{-5}$ ph cm$^{-2}$ s$^{-1}$" (Discussion) [from (cite: Muno)]
- External data: Correction factor a(nu,Te) = 0.763-0.892 at 232 GHz  
  > "The correction factor, $a(\nu, T^\ast_{\mathrm e})$, at $\nu=232$ GHz is calculated to be $a=0.763-0.892$" (Discussion) [from (cite: Mezger)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J1924-2914 (flux scale); phase calibrators J1744-3116 and J1752-2956  
  > "The flux density scale was determined using J1924-2914." (Observation and Data Reduction)
- flux scale uncertainty: _not stated_
- self calibration: complex gain errors minimized with self-calibration in CASA for the continuum map  
  > "The complex gain errors of the data were minimized using the “self-calibration" method in CASA." (Observation and Data Reduction)

### Imaging

- task: CASA 5.4 clean  
  > "The imaging to obtain channel maps was done using CASA 5.4 with `clean` task." (Observation and Data Reduction)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "The angular resolution using “natural weighting" is $0\ensuremath{''}.037 \times 0\ensuremath{''}.024, PA=87^\circ$." (Observation and Data Reduction)
- uv taper: no taper stated; baselines over 11 km removed for continuum, only first seven days used  
  > "the data with the baselines over 11 km is removed because this seems to increase the sidelobe effects in the continuum map." (Observation and Data Reduction)
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: uvcontsub fitorder=1 to remove Sgr A* and GCMS continuum, on combined ten-day data  
  > "were subtracted from the data using CASA task, `uvcontsub (fitorder=1)` for the combined data in the ten-day observations." (Observation and Data Reduction)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.037" x 0.025", PA=85 deg (continuum)  
  > "The angular resolution is $0\ensuremath{''}.037 \times 0\ensuremath{''}.025, PA=85^\circ$ in FWHM" (Results)
- final rms: 50 uJy/beam continuum; 90 uJy/beam per 20.2 km/s channel  
  > "The sensitivity is $1\sigma=50~ \mu$Jy beam$^{-1}$ or 1.3 K in $T_\mathrm{B}$ in the emission-free areas." (Observation and Data Reduction)

### Inherited from earlier work

- Flat mm spectrum interpreted as optically thin free-free emission  
  > "The flat spectrum in mm wavelength suggests that the emission is an optically thin free-free emission (cite: Tsuboi2017b)." (Results) [from (cite: Tsuboi2017b)]
- He+/H+ ratio of 0.09 adopted as typical for the Galactic center  
  > "a typical value in the Galactic center region (e.g. (cite: Tsuboi2017))" (Discussion) [from (cite: Tsuboi2017)]

### Not stated but needed to reproduce (our reading)

- Self-calibration solution intervals, reference model and number of iterations
- Line-free channels used for uvcontsub and the continuum image
- Image size, cell size, clean threshold and masks
- Which execution blocks/days were used and how dates map to the 7-day subset
- How Gaussian fit and integration regions for flux and line integrals were defined
- Method for deriving the PV-diagram end velocities (~150/cos i km/s) and uncertainties
- Path length and brightness temperature used in the density formula, and the alpha(nu,T) value
- Basis of orbital period range 50-100 yr
- Primary beam correction details

## Analysis recipe

1. **Calibrate and image continuum and H30alpha cube**: uvcontsub on combined data, CASA clean channel maps (20.2 km/s); continuum from line-free data of first seven days with baselines <11 km plus self-calibration  
  > "We used only the data of the first seven days to produce the resultant continuum map here." (Observation and Data Reduction)
   - software: CASA
   - parameter: uvcontsub fitorder=1; natural weighting  
  > "`uvcontsub (fitorder=1)`" (Observation and Data Reduction)
   - fitting: _not stated_
   - validation: _not stated_
2. **Measure size and flux of the oval structure**: two-dimensional Gaussian fit with beam size correction  
  > "by the two-dimensional Gaussian fit including beamsize correction" (Results)
   - software: CASA
   - assumption: distance 8.0 kpc  
  > "we adopt 8.0 kpc as the distance to the Galactic center" (Introduction)
   - fitting: _not stated_
   - validation: _not stated_
3. **Derive enclosed mass from PV diagram**: Rotation velocity from ends of inclined linear feature in PV diagram along major axis, corrected for thermal broadening; inclination from aspect ratio; M = r V_rot^2 / G  
  > "The inclination angle is derived to be $i \sim 50^\circ$ from the aspect ratio of the Gaussian-fit angular size mentioned in Results." (Discussion)
   - parameter: V_rot ~150/cos i km/s; r ~ 6e15 cm  
  > "$V_\mathrm{rot}\sim150/\cos{i}$ km/s" (Discussion)
   - assumption: gas on a single circular orbit  
  > "Assuming that the ionized gas obeys a single circular orbit simply" (Discussion)
   - fitting: _not stated_
   - validation: Cross-check with free-fall mass of south extended flow, M ~1.0e4/(cos j)^2 Msun, roughly consistent  
  > "This is roughly consistent with the enclosed mass mentioned above." (Discussion)
4. **Derive electron temperature, density and gas mass**: LTE Te from H30alpha line-to-continuum ratio solved iteratively; ne from brightness temperature (Altenhoff formula); mass from sphere of diameter L  
  > "The LTE electron temperature is obtained by iteratively solving the formula for $T^\ast_{\mathrm e}$." (Discussion)
   - parameter: N(He+)/N(H+)=0.09  
  > "$\frac{N(\mathrm{He^+})}{N(\mathrm{H^+})}=0.09$" (Discussion)
   - assumption: optically thin line and continuum; spherical geometry with L ~1.14e16 cm  
  > "assuming that the line and continuum emissions are optically thin" (Discussion)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 5.4: data analysis, uvcontsub, clean imaging, self-calibration  
  > "We performed the data analysis by Common Astronomy Software Applications (CASA)" (Observation and Data Reduction)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Oval structure angular size (maj x min) | 0.093 x 0.061 | ±0.006, ±0.004 | arcsec | 2 | $0.093\ensuremath{''}\pm0.006\ensuremath{''}\times 0.061\ensuremath{''}\pm0.004\ensuremath{''}$ |
| Total continuum flux density of oval at 232 GHz | 10.52 | 0.90 | mJy | 2 | The total flux density of the oval-like structure is $S_\nu=10.52\pm0.90$ mJy. |
| Rotation velocity | 230 | not stated | km/s | 3 | Then the rotating velocity is estimated to be $V_\mathrm {rot} \sim 230$ km s$^{-1}$. |
| Enclosed mass | 2.4e4 | not stated | Msun | 3 | the enclosed mass is estimated to be $M\sim2.4\times10^4$ $M_\odot$ |
| Mean electron temperature of ring | 6800 | 700 | K | 4 | $\bar{T}_{\mathrm e}=6800\pm700$ K |
| Mean electron density | 6e5 | not stated | cm^-3 | 4 | The mean electron density is $\bar{n}_{\mathrm e}=6\times10^5$ cm$^{-3}$ |
| Ionized gas mass | 4e-4 | not stated | Msun | 4 | $M=\frac{4\pi}{3}\big(\frac{L}{2}\big)^3\bar{n}_{\mathrm e}m_{\mathrm{H}}=4\times10^{-4} M_\odot$ |
| Lower limit mass density | 8e11 | not stated | Msun/pc^3 | 3 | the lower limit of the mass density is estimated to be $\rho \gtrsim8\times10^{11}  M_\odot pc^{-3}$ |

## Qualitative findings

- IRS13E3 is resolved into an oval structure also seen in H30alpha, with a velocity gradient along its major axis.  
  > "The components positionally shift from northeast to southwest along the major axis of the oval-like structure with increasing velocity." (Results)

## Claim tuples

- H: IRS13E3 hosts a rotating ionized gas ring around a massive object | E: 232 GHz continuum and H30alpha imaging with ALMA; PV diagram along major axis | R: Inclined linear PV feature, V_rot ~230 km/s, r ~6e15 cm | F: Ring rotates around a ~2.4e4 Msun enclosed mass, consistent with an IMBH | **supported**
- H: The enclosed mass is compatible with an IMBH rather than a normal cluster | E: Density estimate and comparison with X-ray counterpart and astrometric limits | R: rho >~ 8e11 Msun/pc^3; X-ray counterpart within error circle | F: Supporting evidence for an IMBH; a cluster would collapse within 1e7 yr | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: A simple rotating ring gives a more reliable enclosed mass than the complicated Keplerian orbit  
  > "If the rotating ring is discovered, the enclosed mass derived with the simple structure must be reliable." (Introduction)
- Alternative: Compact cluster of stars or remnants as alternative to a black hole  
  > "the alternate may be a compact cluster of star or star remnant and so on" (Discussion)
- How they decided it was enough: _not stated_
- Limitation (authors): Sidelobes of Sgr A* worsen sensitivity and remain in the continuum map; variability of Sgr A* limits data use  
  > "Although the sidelobe effects still remain around Sgr A$^\ast$, the dynamic range reaches to $>40000$ in the other areas of the map." (Observation and Data Reduction)
- Caveat (inferred, ours): Rotation inferred from a single PV diagram with 20 km/s resolution; no kinematic model fit or uncertainty on mass
- Caveat (inferred, ours): Inclination from the aspect ratio assumes a circular ring
- Caveat (inferred, ours): Mass has no stated uncertainty
- Caveat (inferred, ours): Gas ring may be non-gravitational flow or part of the larger flow

## Reproducibility

- Data public (paper): ALMA data cited by project code in acknowledgement  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2015.1. 01080.S and ALMA#2017.1.00503.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Self-calibration parameters
- Missing: Imaging parameters (cell, size, masks, threshold)
- Missing: PV extraction and velocity end measurement details
- Missing: Flux integration regions
- Data volume (inferred): ~1-3 TB raw for ten long-baseline execution blocks
- Score (inferred): 3/5, Public data and simple analysis formulas, but imaging, self-cal and PV measurement details are missing.
- Rediscovery candidate: no, Key numbers depend on unspecified self-cal and subjective PV reading; recipe incomplete.

## Links

- Method: (cite: McMullin) (CASA)
- Companion: (cite: Tsuboi2017b) (Previous ALMA detection of the ionized gas flow around IRS13E3 and 340 GHz data)
- Related: 2015.1.01080.S

## Checks

```json
{
 "quotes": 60,
 "quotes_ok": 60,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2015.1.01080.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 71,
  "stated": 41,
  "rate": 0.577
 },
 "evidence_ok": true
}
```
