# High Star Formation Rates in Turbulent Atomic-dominated Gas in the Interacting Galaxies IC 2163 and NGC 2207

`2016ApJ...823...26E` | The Astrophysical Journal 2016 | first author: Elmegreen, Bruce G. | arXiv: 1603.04533 | DOI: 10.3847/0004-637X/823/1/26

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, star_formation
- Question: How does the star formation rate surface density depend on atomic, molecular and total gas surface density at 2.4 kpc scales in the interacting pair IC 2163 and NGC 2207, and does it differ from other galaxies?  
  > "We are interested in whether this relation on a scale of $2.4$ kpc diameter differs from that in other galaxies, and whether it is the same in both galaxies here." (Introduction)
- Target **IC 2163 and NGC 2207**: coordinates _not stated_; z/distance D = 35±2.5 Mpc  
  > "a distance $D = 35\pm2.5$ Mpc from the NASA/IPAC Extragalactic Database (NED) for a Hubble constant of $H = 73$ km s$^{-1}$ Mpc$^{-1}$ corrected for infall towards Virgo." (Observations); distance from NED, H = 73 km/s/Mpc corrected for Virgo infall  
  > "a distance $D = 35\pm2.5$ Mpc from the NASA/IPAC Extragalactic Database (NED) for a Hubble constant of $H = 73$ km s$^{-1}$ Mpc$^{-1}$ corrected for infall towards Virgo." (Observations)

## Data provenance

- ALMA projects: 2012.1.00357.S
- bands: _not stated_
- frequencies and spectral setup: 12CO(1-0) at 115.27 GHz; 10 km/s channels  
  > "IC 2163 and NGC 2207 were observed in 34 pointings using ALMA at the $^{12}$CO(1-0) frequency of 115.27 GHz ($\lambda$ 2.6 mm)." (Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 2.00" x 1.52" HPBW, PA 68.5 deg (natural weighting)  
  > "We made naturally weighted maps of CO emission with a point spread function of $2.00^{\prime\prime} \times 1.52^{\prime\prime}$ (HPBW), beam position angle $68.5^\circ$" (Observations)
- max recoverable scale: _not stated_
- sensitivity: rms 3.7 mJy/beam per 10 km/s channel  
  > "The rms noise per channel is $3.7$ mJy beam$^{-1}$" (Observations)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: 12CO J=1-0 (115.27 GHz)
- Other facility **VLA (HI)**: HI cube, 21 km/s channels, beam 13.5"x12", 6 hr on source, obtained 1990  
  > "The HI is from VLA observations obtained in 1990 using a hybrid CnB array with an extended north arm" (Observations)
- Other facility **Spitzer MIPS 24 um**: 24 um images for SFR (MIPS 1 pBCD and HiRes deconvolution)  
  > "were measured from the MIPS 1 pBCD image obtained from the Spitzer archive in 2013; the resolution is $6^{\prime\prime}$." (Observations)
- Other facility **Lowell 1.1m telescope**: Halpha and R images (1999)  
  > "obtained by Deidre Hunter with the Lowell 1.1m telescope in 1999" (Observations)
- External data: HiRes deconvolved 24 um image  
  > "who provided their HiRes 24 $\mu$m data to us as a FITS image" (Observations) [from (cite: velusamy08)]
- External data: XCO = 1.8±0.3e20 H2 cm-2 (K km/s)-1  
  > "we use $X_{\rm CO}= 1.8 \pm 0.3 \times10^{20}$ H$_2$ cm$^{-2}$ (K km s$^{-1}$)$^{-1}$ from (cite: dame01)" (Observations) [from (cite: dame01)]
- External data: Inclinations 40 deg (IC 2163), 35 deg (NGC 2207)  
  > "we took inclinations of $i = 40^\circ$ for IC 2163 and $35^\circ$ for NGC 2207 (cite: elmegreen95b)" (Observations) [from (cite: elmegreen95b)]

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
- weighting robust: natural weighting  
  > "We made naturally weighted maps of CO emission" (Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: mask from cube convolved to 6"x6"; unblanked if >2.5x rms (7.9 mJy/beam) in >=2 adjacent channels  
  > "Regions were left unblanked if they exceeded 2.5 times this rms noise for at least 2 adjacent channels in an area of at least 1 arc sec." (Observations)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: applied before making the 551x301 pixel x 64 channel subcube  
  > "After correcting for primary beam attenuation, we made the $551\times301$ pixel $\times64$ channel subcube" (Observations)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- CO observing procedure details  
  > "For more details on the observing procedure, see (cite: kaufman16)." (Observations) [from (cite: kaufman16)]
- SFR calibration combining Halpha and 24 um  
  > "was used to obtain the SFR, following (cite: kennicutt09)" (Star formation rates) [from (cite: kennicutt09)]

### Not stated but needed to reproduce (our reading)

- ALMA calibration, CASA version, arrays/configurations and observing dates
- Imaging details (cell size, deconvolver, cleaning threshold)
- Details of the CO data reduction, deferred to Kaufman et al. 2016
- Exact aperture positions are tabulated, but the HI kinematic separation of the two galaxies is not described

## Analysis recipe

1. **Make CO cube and mask**: Natural-weighted cube, blanking mask from 6" convolved cube, primary beam correction, subcube  
  > "we made a blanking mask by convolving this cube to $6^{\prime\prime}\times6^{\prime\prime}$ HPBW, where the noise was 7.9 mJy/beam." (Observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **Derive H2 mass and surface density**: Convert CO to H2 with XCO, deproject with inclinations  
  > "To convert surface density to face-on, we took inclinations of $i = 40^\circ$ for IC 2163 and $35^\circ$ for NGC 2207 (cite: elmegreen95b)." (Observations)
   - assumption: XCO = 1.8e20, D = 35 Mpc  
  > "The scale is 170 pc per arcsec." (Observations)
   - fitting: _not stated_
   - validation: Discussed effect of different XCO and i  
  > "We discuss the implications of different $X_{\rm CO}$ and $i$ in Section [4](#sfrcorrel)." (Observations)
3. **Compute SFR in 14" apertures**: SFR = 5.5e-42 (L[Halpha] + 0.031 L[24um]) in apertures 14" = 2.4 kpc, with extinction corrections  
  > "We chose source apertures with a diameter of $14^{\prime\prime} = 2.4$ kpc." (Star formation rates)
   - parameter: 24 um aperture correction 1.61 for Feature i; Galactic A_V = 0.238 mag  
  > "applied an aperture flux correction factor of 1.61 from the MIPS Instrument Handbook" (Star formation rates)
   - fitting: _not stated_
   - validation: Repeated with all images convolved to 14"x14"; conclusions unchanged  
  > "None of the conclusions of this paper were affected by this change." (Star formation - surface density correlation)
4. **Kennicutt-Schmidt relations**: Plot Sigma_SFR vs Sigma_HI, Sigma_H2 and total gas, and vs molecular ratio; compare with THINGS  
  > "Figure [3](#fig:n2207_alma_ks1c) shows these correlations." (Star formation - surface density correlation)
   - fitting: _not stated_
   - validation: _not stated_

## Software


## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Total CO flux in subcube | 505 | not stated | Jy km/s | 1 | The total integrated CO line flux in the subcube is $S(CO)=505$ Jy km s$^{-1}$. |
| M(H2) IC 2163 | 2.1e9 | not stated | Msun | 2 | IC 2163 / $2.1\times10^9$ |
| M(H2) NGC 2207 | 2.3e9 | not stated | Msun | 2 | NGC 2207 has $M(H_2) = 2.3\times10^9\;M_\odot$ for a CO line flux of 265 Jy km s$^{-1}$. |
| Feature i molecular consumption time | 50 | not stated | Myr | 4 | $\Sigma_{\rm H2}/\Sigma_{\rm SFR}=50$ Myr |
| Mean HI velocity dispersion of 16 HI-dominated regions in NGC 2207 | 42 | not stated | km/s | 4 | The mean HI velocity dispersion for the 16 green circles in N2207 (Fig. [4](#fig:n2207_alma_ks3)) is 42 km s$^{-1}$ |

## Qualitative findings

- HI-dominated high-SFR regions lie mostly in the outer NGC 2207; H2-dominated ones in the IC 2163 ocular ridge.  
  > "The HI-rich regions of high $\Sigma_{\rm SFR}$ are on the periphery of the galaxy that underwent the retrograde, perpendicular encounter (NGC 2207)" (Star formation - surface density correlation)

## Claim tuples

- H: Do HI-dominated regions follow the normal molecular Kennicutt-Schmidt relation? | E: Compare Sigma_SFR vs Sigma_H2 for 44 apertures with THINGS | R: HI-dominated high-SFR regions lie high above the linear molecular relation (H2 consumption time ~300 Myr) | F: They have excess SFR relative to molecular gas but normal SFR relative to total gas (~1 Gyr) | **supported**
- H: Turbulence explains the atomic-dominated star-forming regions | E: Compare locations with HI velocity dispersion | R: Mean dispersion 42 km/s vs ~10 km/s in normal galaxies | F: Consistent with flattened density PDF from compressive high Mach number turbulence | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Different XCO or inclination (including warp) do not remove the HI-rich peculiarity  
  > "Inclination effects would not seem to be causing the peculiar HI either." (Star formation - surface density correlation)
- How they decided it was enough: _not stated_
- Limitation (authors): About 25% absolute SFR uncertainty from 24 um calibration  
  > "The absolute calibration of the 24 $\mu$m term in the SFR leads to an uncertainty of about 25% in the absolute determination of the SFR" (Observations)
- Caveat (inferred, ours): Only 44 apertures, no formal fits or uncertainties on relations
- Caveat (inferred, ours): Single XCO assumed; dark H2 in HI regions not constrained
- Caveat (inferred, ours): Halpha NII contamination and extinction corrections uncertain

## Reproducibility

- Data public (paper): ALMA project listed in acknowledgments; other data from literature or provided privately  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2012.1.00357.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: ALMA reduction details (in Kaufman et al. 2016)
- Missing: HI cube, Halpha image and HiRes 24 um image not directly available
- Missing: Kinematic separation of HI between galaxies
- Data volume (inferred): ~50-100 GB for 34-pointing ALMA CO(1-0) mosaic, plus small ancillary images
- Score (inferred): 3/5, Aperture table is given and the SFR recipe is explicit, but ALMA processing is deferred and ancillary data are not public.
- Rediscovery candidate: no, Requires non-archival HI, Halpha and HiRes 24 um data and unstated ALMA reduction.

## Links

- Method: (cite: kennicutt09) (SFR calibration from Halpha and 24 um)
- Method: (cite: leroy12) (SFR reliability limits and 24 um calibration)
- Companion: (cite: kaufman16) (Observing procedure and other CO properties)
- Related: THINGS

## Checks

```json
{
 "quotes": 39,
 "quotes_ok": 39,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 68,
  "stated": 29,
  "rate": 0.426
 },
 "evidence_ok": true
}
```
