# IRC +10 216 in 3D: morphology of a TP-AGB star envelope

`2018A&A...610A...4G` | Astronomy and Astrophysics 2018 | first author: Guélin, M. | arXiv: 1709.04738 | DOI: 10.1051/0004-6361/201731619

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: evolved_stars
- Question: What is the 3-D morphology, kinematics, temperature and mass-loss history of the IRC +10 216 envelope, from SMA and ALMA CO(2-1) maps combined with single-dish data, and what does it imply for a binary companion?  
  > "In Sec. 2, we describe the observations and data reduction procedures, and in Sec. 3 & 4 derive the envelope morphology, velocity field and gas physical properties." (1 Introduction)
- Target **IRC +10 216 (CW Leo)**: coordinates 09:47:57.4492 +13:16:43.884 (J2000, June 2015 epoch)  
  > "Located at a distance of $\sim 130$ pc (cite: Menten2012)" (1 Introduction); "is 09$^h$ 47$^m$ 57.4492$^s$ 13$^\circ\,16'\,43.884''$" (3.2 Continuum emission); z/distance ~130 pc; systemic velocity -26.5 km/s (LSR)  
  > "Located at a distance of $\sim 130$ pc (cite: Menten2012)" (1 Introduction); "is 09$^h$ 47$^m$ 57.4492$^s$ 13$^\circ\,16'\,43.884''$" (3.2 Continuum emission); distance from Menten et al. 2012 (VLBA)  
  > "Located at a distance of $\sim 130$ pc (cite: Menten2012)" (1 Introduction); "is 09$^h$ 47$^m$ 57.4492$^s$ 13$^\circ\,16'\,43.884''$" (3.2 Continuum emission)

## Data provenance

- ALMA projects: 2013.1.01215.S, 2013.1.00432.S
- bands: Band 6 (1 mm) and 3 mm  
  > "the usable band of the ALMA Band 6 receiver covered several molecular lines of interest" (2.2 ALMA observations)
- frequencies and spectral setup: CO(2-1), CN(2-1), C4H(24-23), CS(5-4) in several windows; channels 0.2, 0.3, 0.4, 0.6 km/s; continuum from 244.2-246.1 GHz subband  
  > "The channel separation for the CO, CN, C$_4$H and CS lines was 0.2 kms$^{-1}$, 0.3 kms$^{-1}$ 0.4 kms$^{-1}$ and 0.6 kms$^{-1}$, respectively" (2.2 ALMA observations)
- continuum bandwidth: _not stated_
- arrays: ALMA 12-m array, Compact and Extended; also SMA, IRAM 30-m, PdBI  
  > "were made with the 12-m array in the Compact configuration (Dec 2014 and Jan 2015, 32 antennas) and in the Extended configuration (June 2015, 39 antennas)" (2.2 ALMA observations)
- configurations: _not stated_
- baselines: 12.7 m to 1569.4 m (1-mm)  
  > "The baselines ranged from 12.7 m to 1569.4 m." (2.2 ALMA observations)
- angular resolution: 1-mm ALMA 0.34"x0.31" (ALMA+SD 0.35"x0.33"); CO(1-0) 0.48"x0.45"; SMA 3.7"x3.0"  
  > "The synthesized HPBW is $0.34''
\times 0.31''$ (PA=+36$^\circ$) for the ALMA maps and $0.35'' \times 0.33''$ (PA=+38$^\circ$) for the ALMA+SD maps." (2.2 ALMA observations)
- max recoverable scale: _not stated_
- sensitivity: 1-mm: 3 mJy/beam per 2 km/s channel; 50 uJy/beam continuum  
  > "The r.m.s noise is 3 mJy/beam per 2 kms$^{-1}$ channel and 50 $\mu$Jy/beam in the continuum 1.9 GHz subband." (2.2 ALMA observations)
- time on source: _not stated_
- observing dates: 1-mm: Dec 2014, Jan 2015, June 2015; 3-mm: 2015  
  > "The 3-mm ALMA observations (project code 2013.1.00432.S) were obtained in 2015" (2.2 ALMA observations)
- pi or archival as stated: _not stated_
- Line: CO J=2-1 (230.53797 GHz)
- Line: C4H N=24-23 (228.3486 and 228.3870 GHz)
- Line: CS J=5-4 (244.9350 GHz)
- Line: CN N=2-1 (around 226.9 GHz)
- Other facility **SMA**: CO(2-1) mosaic of the full envelope at ~3" resolution  
  > "The envelope was fully mapped in CO(2-1) with the SMA at $3\ensuremath{''}$ resolution" (1 Introduction)
- Other facility **IRAM 30-m**: Single-dish short spacings and maps of CO, 13CO, C4H, CN, CS  
  > "They provide the total flux and short spacings for the ALMA maps." (2.3 IRAM 30-m single-dish telescope and PdBI observations)
- Other facility **PdBI**: Preliminary CO(2-1) mosaic of part of the outer envelope  
  > "The synthesized HPBW was $1.4\ensuremath{''} \times 1.2 \ensuremath{''}$ and the noise 30 mJy/beam in 3 kms$^{-1}$-wide channels." (2.3 IRAM 30-m single-dish telescope and PdBI observations)
- External data: 30-m CO(2-1) SD maps and outer-envelope physical conditions  
  > "The CO(2-1) 30-m SD observations were reported in (cite: Cernicharo2015)." (2.3 IRAM 30-m single-dish telescope and PdBI observations) [from (cite: Cernicharo2015)]
- External data: Rotational temperatures at r<=1" from ro-vibrational SiS and C2H4 lines  
  > "using the rotational temperatures derived by (cite: Fonfria2015; Fonfria2017) from ro-vibrational SiS and C$_2$H$_4$ lines" (4.3.1 Rotational and kinetic temperatures) [from (cite: Fonfria2015; Fonfria2017)]
- External data: CO/H2 abundance 6e-4  
  > "the $^{12}$CO abundance with respect to H$_2$ of $6\times 10^{-4}$ estimated by (cite: Agundez2012)" (4.3.3 Mass-loss rate) [from (cite: Agundez2012)]

## Processing

### Calibration

- pipeline or manual: ALMA data calibrated through the ALMA/CASA pipeline; SMA data with MIRIAD  
  > "The data were calibrated through the ALMA/*CASA* pipeline." (2.2 ALMA observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: ALMA: Ganymede; SMA: Titan and/or Callisto  
  > "Ganymede and the quasars 0854+2006 and J1008+0621 were observed on every track for flux and phase calibration." (2.2 ALMA observations)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: GILDAS/MAPPING/MOSAIC  
  > "further processing was made with the *GILDAS/MAPPING/MOSAIC* software package" (2.2 ALMA observations)
- deconvolver: modified Hogbom algorithm (SMA; ALMA similar)  
  > "using a modified Hogböm algorithm that proceeds iteratively by order of decreasing signal-to-noise ratio" (2.1 SMA observations)
- weighting robust: SMA natural weights; SD weights lowered to constant  
  > "the SMA visibilities were processed with their natural weights" (2.1 SMA observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: SMA: continuum from line-free channels subtracted; ALMA continuum from 244.2-246.1 GHz subband after discarding CS channels  
  > "The continuum signal was derived for each pointing by averaging the line emission-free channels of the 4 GHz-wide correlator and was subtracted" (2.1 SMA observations)
- line free channels: _not stated_
- primary beam correction: maps truncated at 20% attenuation level, corrected, combined into one dirty image  
  > "correct these maps for primary beam attenuation after truncating them at the 20% attenuation level and combine them into a single dirty image" (2.1 SMA observations)
- array combination: SD pseudo-visibilities 0-20 m added, scaled by 1.7 (SMA), low weight  
  > "The amplitudes of the single-dish pseudo-visibilities were scaled by a factor 1.7 to match the azimuthally-averaged SMA amplitudes in the overlap region." (2.1 SMA observations)
- smoothing: CO(2-1) smoothed to CO(1-0) resolution 0.48"x0.45"; CO(1-0) degraded to 0.86"x0.76" for 13CO comparison  
  > "we degraded the spatial resolution of the $^{12}$CO($1-0$) central velocity-channel maps to $(0.86''\times 0.76'')$" (4.3.2 12CO/13CO abundance ratio)
- final beam: ALMA 0.34"x0.31"; ALMA+SD 0.35"x0.33"  
  > "The synthesized HPBW is $0.34''
\times 0.31''$ (PA=+36$^\circ$) for the ALMA maps" (2.2 ALMA observations)
- final rms: _not stated_

### Inherited from earlier work

- Processing of the 3-mm data follows the 1-mm procedure; spectral survey description deferred  
  > "The 3-mm data were processed like the 1-mm data and similarly combined with 30-m SD data." (2.2 ALMA observations) [from Cernicharo et al., in preparation]
- SD reduction procedures for CO(1-0)/13CO(1-0) maps  
  > "as part of a spectral survey (cite: Agundez2017; Quintana2017)" (2.3 IRAM 30-m single-dish telescope and PdBI observations) [from (cite: Agundez2017; Quintana2017)]
- Outer-envelope physical conditions analysis  
  > "This was done for the outer envelope in our previous study (cite: Cernicharo2015)" (4.3 Physical conditions and mass loss rate) [from (cite: Cernicharo2015)]

### Not stated but needed to reproduce (our reading)

- CLEAN parameters, cell size, image size, masks and iteration/threshold for GILDAS imaging
- Line-free channels used for continuum
- Details of ALMA pipeline version and CASA version
- Flux scale uncertainty and flux values of calibrators
- Details of SD-ALMA scaling factor and overlap used for ALMA
- MADEX collisional rates and model setup
- Cernicharo et al. 3-mm survey details
- Exact sector/ring averaging centre and error treatment for Trot fit

## Analysis recipe

1. **Merge interferometer and single-dish data and image**: Convert calibrated uvfits to GILDAS, add SD pseudo-visibilities, mosaic dirty maps, primary-beam correct, Hogbom clean  
  > "to produce a second position-velocity datacube" (2.1 SMA observations)
   - software: MIRIAD, GILDAS
   - parameter: SD 0-20 m added, scaled by 1.7 (SMA)  
  > "adding for each field the single-dish pseudo-visibilities with spatial frequencies between 0 and 20 m to the SMA visibilities" (2.1 SMA observations)
   - fitting: _not stated_
   - validation: ALMA+SD smoothed to SMA+SD resolution compared with SMA+SD map  
  > "A comparison of the ALMA+SD map, smoothed to the resolution of the SMA+SD map, shows the same bright structures than the latter" (2.2 ALMA observations)
2. **Measure arc periodicity and offsets in the plane of the sky**: Azimuthal average of SMA map in four quadrants, Fourier transform of radial profiles r=20"-150"; fit circular arcs  
  > "by azimuthally averaging the SMA map of Fig. 7 in the NW, NE, SE and SW quarters and by Fourier transforming the resulting 4 radial profiles from $r= 20''$ to $r=150''$" (3.1.1 Outer envelope)
   - assumption: Distance 130 pc, expansion 14.5 km/s  
  > "for an expansion velocity of 14.5 km s$^{-1}$ and a distance of 130 pc" (3.1.1 Outer envelope)
   - fitting: _not stated_
   - validation: _not stated_
3. **3-D deprojection of shells**: Non-iterative and iterative spherical deprojection of CO (x,y,V) cubes assuming uniform expansion  
  > "Two different approaches, respectively dubbed *Non-iterative* and *Iterative*, were used for this 3-D reconstruction." (4.2 Spherical deprojection of the outer envelope)
   - parameter: Vexp=14.5 km/s, 1 km/s channels  
  > "We thus adopt in the following a uniform expansion velocity of $V_{exp}=14.5$ km s$^{-1}$ and neglect turbulent motions." (4.2 Spherical deprojection of the outer envelope)
   - assumption: CO signal proportional to column density; constant expansion  
  > "Both also assume that the observed CO signals are proportional to the gas column density." (Appendix A)
   - fitting: _not stated_
   - validation: Two independent methods compared; tests on model envelopes  
  > "The great similarity of the images derived by two independent methods gives us confidence that the deprojected XYZ representation of the envelope is unequivocal and correct." (4.2 Spherical deprojection of the outer envelope)
4. **Derive rotation/kinetic temperature profile**: Azimuthal average of smoothed CO(2-1) and CO(1-0) central-channel maps in 0.53" rings; R21 ratio gives Trot; power-law fit  
  > "azimuthally averaged over $0.53\ensuremath{''}$-thick concentric rings centred on CW Leo$\star$" (4.3.1 Rotational and kinetic temperatures)
   - software: MADEX
   - assumption: low-J 12CO at LTE so Trot=Tk  
  > "which represents the kinetic temperature $T_{k}$ under the assumption that the low J $^{12}$CO levels are at LTE" (4.3.1 Rotational and kinetic temperatures)
   - fitting: power law in r  
  > "At lower radii, $T_\textnormal{\tiny rot}$ closely follows a power-law" (Rotational and kinetic temperatures)
   - validation: MADEX shows Trot deviates from Tk by <~10% for r<=25"  
  > "we find that $T_\textnormal{\tiny rot}$ deviates from $T_k$ by $\lesssim 10\%$ in the range of radii considered here" (4.3.1 Rotational and kinetic temperatures)
5. **Derive 12CO/13CO ratio and mass-loss rate**: Self-consistent iterative MADEX modelling of 12CO(1-0) and 13CO(1-0) brightness; mass-loss from 13CO(1-0) in four 5-deg sectors  
  > "The mass-loss rate has been calculated from the brightness temperature averaged over the position angle in four 5$^\circ$-wide sectors oriented along the N, S, E and W directions" (4.3.3 Mass-loss rate)
   - software: MADEX
   - parameter: converges after ~10 iterations, variation <=0.1%  
  > "can be assumed to converge after $\simeq 10$ iterations, when the variation between consecutive iterations was $\lesssim 0.1\%$" (4.3.2 12CO/13CO abundance ratio)
   - assumption: [12CO]/[H2]=6e-4  
  > "This value was calculated assuming the $^{12}$CO abundance with respect to H$_2$ of $6\times 10^{-4}$" (4.3.3 Mass-loss rate)
   - fitting: _not stated_
   - validation: Compared with literature mass-loss rates (1.5-4.0)e-5 Msun/yr  
  > "The derived average mass-loss rate agrees quite well with most of the values commonly derived or adopted in the literature" (4.3.3 Mass-loss rate)

## Software

- **MIRIAD** : SMA calibration  
  > "The SMA data were calibrated using the *MIRIAD* calibration package" (2.1 SMA observations)
- **GILDAS/MAPPING/MOSAIC** : Imaging, merging with SD data, cleaning  
  > "further data processing and analysis was made with the *GILDAS/MAPPING/MOSAIC* data reduction software" (2.1 SMA observations)
- **CASA** : ALMA pipeline calibration  
  > "The data were calibrated through the ALMA/*CASA* pipeline." (2.2 ALMA observations)
- **MADEX** : Statistical equilibrium modelling of CO lines for Trot, opacity, isotopic ratio, mass loss  
  > "modelling the $J=1-0$ and $2-1$ lines and the $^{13}$CO (1-0) line with the *MADEX* statistical equilibrium code" (4.3.1 Rotational and kinetic temperatures)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Continuum compact source peak flux (245 GHz) | 0.33 | not stated | Jy | 0 | yields a peak flux of 0.33 Jy and a FWHP of 0.22 $\pm 0.01$ arcsec |
| Continuum compact source FWHP | 0.22 | 0.01 | arcsec | 0 | yields a peak flux of 0.33 Jy and a FWHP of 0.22 $\pm 0.01$ arcsec |
| Outer arc spacing | 16 | not stated | arcsec (~700 yr) | 2 | the FT shows a marked peak that corresponds to a period of 16$''$ (Fig. 8), i.e. to a time lag of 700 yr |
| Turbulent velocity upper limit | 0.6 | not stated | km/s | 0 | allowing us to set an upper limit to the turbulent velocity $V_{turb}$ of 0.6 km s$^{-1}$ |
| Trot power-law normalisation (at r=0.8") | 256.9 | 1.5 | K | 4 | $T_\textnormal{\tiny rot}=(256.9\pm 1.5)\left(r/0.8\right)^{-(0.675\pm 0.003)}$ K |
| Trot power-law exponent | -0.675 | 0.003 | dimensionless | 4 | $T_\textnormal{\tiny rot}=(256.9\pm 1.5)\left(r/0.8\right)^{-(0.675\pm 0.003)}$ K |
| 12CO/13CO ratio | 42 | not stated | dimensionless | 5 | Its value up to the $r=15''$ shell, $42$, agrees well |
| Mean mass-loss rate | 2.7e-5 | 0.5e-5 | Msun/yr | 5 | $\langle\dot M\rangle=(2.7\pm 0.5)\times 10^{-5}$ M$_\odot$ yr$^{-1}$ |

## Qualitative findings

- Dense shells are near-spherical, not an oblate or spiral structure; inner arcs are off-centred circular filaments  
  > "We thus conclude that the dense shells, traced by CO in the outer envelope, have spherical or near-spherical shapes and that the envelope is not manifestly oblate." (4.2 Spherical deprojection of the outer envelope)

## Claim tuples

- H: Are the CO shells spherical or confined to the plane of the sky/oblate? | E: PV diagrams and 3-D deprojection of SMA+SD CO cubes with two methods | R: Arcs follow spherical-shell ellipses; reconstructions show near-circular arcs in cuts | F: Shells are spherical or near-spherical with no clear flattening | **supported**
- H: Is the inner arc pattern a spiral and how does it differ from outer arcs? | E: ALMA CO, CN, C4H maps of the central region | R: Denser, less regular off-centred circular filaments, no obvious spiral | F: Inner structure is not a simple spiral; requires mass transfer or more bodies | **partially**
- H: What are the temperature and mass-loss rate in the central envelope? | E: CO(2-1)/(1-0) ratio and 13CO analysis with MADEX | R: Tk power law exponent -0.675 to 15", ~35 K beyond; Mdot 2.7e-5 Msun/yr, variations x3 | F: Gas is heated more than adiabatic; mass loss varied by factor 3 over ~100 yr | **supported**

## Reasoning

- Why this data: SMA data cannot be cleaned near the bright central source, so the centre was re-observed with ALMA  
  > "To obtain reliable images of this region, we have re-observed the central 1 arcmin with ALMA." (2.1 SMA observations)
- Why this method: _not stated_
- Alternative: Archimedean spiral fits are poorer than off-centred circular arcs  
  > "We note that the fits become poorer when replacing the circular arcs by segments of spirals with significant pitch angles." (3.1.1 Outer envelope)
- How they decided it was enough: _not stated_
- Limitation (authors): 3-D reconstruction fails near polar caps due to opacity and velocity degeneracy  
  > "prevents us from localizing the gas cells along the line of sight in the approaching and receding polar caps." (4.2 Spherical deprojection of the outer envelope)
- Limitation (authors): Mass-loss estimates beyond r=20" unreliable due to LTE departures  
  > "The estimates beyond $r=20''$, which seem to show a 30% decrease of the mass loss rate, are not reliable" (4.3.3 Mass-loss rate)
- Caveat (inferred, ours): Binary scenario is speculative and not tested quantitatively
- Caveat (inferred, ours): Uncertainties on Mdot and Trot appear statistical; systematics from abundance, distance, and flux scaling not propagated
- Caveat (inferred, ours): Deprojection assumes constant expansion and optically thin emission

## Reproducibility

- Data public (paper): ALMA project codes given; SMA project numbers in acknowledgements  
  > "ALMA (ADS/JAO.ALMA#2013.1.01215.S)" (Acknowledgements)
- Products in archive: _not stated_
- Missing: Deprojection codes not released
- Missing: GILDAS imaging parameters
- Missing: MADEX model inputs
- Data volume (inferred): ~100s GB (ALMA multi-config mosaic plus 3-mm; SMA and 30-m data separate)
- Score (inferred): 3/5, Data public and steps described, but imaging parameters, SD merging and custom deprojection/MADEX setups are incompletely specified.
- Rediscovery candidate: no, Requires SMA/30-m data and custom unreleased codes; recipe incomplete.

## Links

- Method: (cite: Cernicharo2012) (MADEX statistical equilibrium code)
- Companion: (cite: Cernicharo2015) (IRAM 30-m CO maps and outer-envelope analysis)
- Companion: (cite: Decin2015) (ALMA 13CO(6-5) inner envelope spiral model)
- Related: ALMA 3-mm spectral survey of IRC +10 216 (Cernicharo et al., in prep.)

## Checks

```json
{
 "quotes": 78,
 "quotes_ok": 78,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 82,
  "stated": 57,
  "rate": 0.695
 },
 "evidence_ok": true
}
```
