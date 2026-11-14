# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2020A%26A...640L...8U\sonnet\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
# ALMA Deep Field in SSA22:

Deep surveys with the Atacama Large Millimeter Array (ALMA) have uncovered a population of dusty star-forming galaxies which are faint or even undetected at optical to near-infrared wavelengths. Their faintness at short wavelengths makes the detailed characterization of the population challenging. Here we present a spectroscopic redshift identification and a characterization of one of these near-infrared-dark galaxies discovered by an ALMA deep survey. The detection of \[C i\](1-0) and CO(4-3) emission lines determines the precise redshift of the galaxy, ADF22.A2, to be $z=3.9913\pm 0.0008$. On the basis of a multi-wavelength analysis, ADF22.A2 is found to be a massive, star-forming galaxy with a stellar mass of $M_*=1.1_{-0.6}^{+1.3}$ $\times10^{11} M_\odot$ and SFR$=430_{-150}^{+230}$ $M_\odot$ yr$^{-1}$. The molecular gas mass was derived to be $M (H_2)^{\rm [CI]}=(5.9\pm1.5)\times10^{10}$ $M_\odot$, indicating a gas fraction of $\approx35\%$, and the ratios of $L_{\rm [CI](1-0)}/L_{\rm IR}$ and $L_{\rm [CI](1-0)}/L_{\rm CO(4-3)}$ suggest that the nature of the interstellar medium in ADF22.A2 is in accordance with those of other bright submillimeter galaxies. The properties of ADF22.A2, including the redshift, star-formation rate, stellar mass, and depletion time scale ($\tau_{\rm dep}\approx0.1-0.2$ Gyr), also suggest that ADF22.A2 has the characteristics expected for the progenitors of quiescent galaxies at $z\gtrsim3$. Our results demonstrate the power of ALMA contiguous mapping and line scan, which help us to obtain an unbiased view of galaxy formation in the early Universe.

# Introduction

![](Fig1v200717.pdf)

Intense star-forming activity in a growing galaxy is often obscured by dust in the early Universe. The absorption of stellar emission and reradiation by dust make the galaxy apparently faint at optical-to-near-infrared wavelengths even though they have star-formation rates of $\sim$ 100-1000 $M_\odot$ yr$^{-1}$ ((cite: 2002PhR...369..111B); (cite: 2014PhR...541...45C) for reviews). Consequently it is challenging to recognize a fraction of star-forming galaxies selected at (sub)millimeter even in a deep near-infrared image. Such a "near-infrared-dark" population was first identified among bright submillimeter galaxies (SMGs) (e.g., (cite: 1999ApJ...519..610D); (cite: 1999MNRAS.308.1061S); (cite: 2004AJ....127..728F)).

The faintness makes it difficult to determine spectroscopic redshift $z_{\rm spec}$ using traditional spectroscopic observations at (observed) optical-to-near infrared wavelengths, which has been a major obstacle in studying these populations. As an alternative, bright rest-frame far-infrared (FIR) lines such as \[C ii\] and CO lines has been utilized to determine $z_{\rm spec}$, which undoubtedly shows that they are heavily dust-obscured star-forming galaxies at high redshift. For instance, (cite: 2009ApJ...690..319W) placed a strong upper limit ($K_s$=27.3 AB at 3$\sigma$) on GN10 at $z=5.303$ (the redshift has been reported by (cite: 2018ApJ...864...49P)), and (cite: 2012Natur.486..233W) found that HDF850.1, which has no counterpart on an *HST* image, is located at $z=5.183$.

Following these works in the era when the Atacama Large Millimeter/submillimeter Array (ALMA) had not been available, the advent of interferometers such as ALMA has allowed us to detect and precisely locate fainter and more abundant (sub)millimeter populations. One avenue of research is follow-up observations of SMGs that were originally discovered by a single-dish telescope. For instance, (cite: 2014ApJ...788..125S) found ten SMGs which were detected at 3.6 $\mu$m, but they were blank at shorter wavelengths.

While obtaining a spectroscopic redshift of these types of near-infrared-dark SMGs is still not easy, a handful of these galaxies are now placed at $z\sim4-5$ via molecular and atomic line detections at (sub)millimeter and the number is increasing (e.g., (cite: 2012MNRAS.427.1066S); (cite: 2017ApJ...850....1R); (cite: 2018ApJ...856...72O); (cite: 2019ApJ...887...55C); (cite: 2019ApJ...887..144J); (cite: 2020ApJ...890..171J); (cite: 2020ApJ...895...81R)).

ALMA deep surveys, which use many pointings to create a contiguous field, are another avenue of research to measure dust-obscured star-forming activity across the cosmic time (e.g., (cite: 2015ApJ...811L...3T); (cite: 2015ApJ...815L...8U); (cite: 2016ApJ...833...67W); (cite: 2017MNRAS.466..861D)). Some of the galaxies identified by these types of surveys are known to be blank at the *H*-band (“*HST*-dark”; e.g., (cite: 2018A&A...620A.152F)) and *Ks*-band (e.g., (cite: 2015ApJ...815L...8U); (cite: 2016PASJ...68...82Y); (cite: 2019ApJ...878...73Y)).

The existence of the near-infrared-dark ALMA galaxies has also been uncovered using another approach. (cite: 2019Natur.572..211W) report the identifications of ALMA sources which were originally selected as “*H*-dropout” galaxies, which are IRAC sources without *HST*/WFC3 F160W counterparts. They suggest that these types of “ALMA-detected *H*-dropouts” are the bulk populations of massive ($M_*\gtrsim10^{10.3}$ $M_\odot$) star-forming galaxies at $z\approx3-6$ and that they dominate the total star-formation rate density at such a massive regime in the era (see also (cite: 2020MNRAS.tmp.1074D)).

These works suggest that some fraction of galaxies could have been missed in previous studies on the basis of the optical-to-near-infrared selection. Charting the nature of the near-infrared-dark ALMA galaxies is necessary for a comprehensive view of galaxy formation and evolution in the early Universe. While the faintness of the optical-to-near-infrared emission makes the spectroscopy in these types of bands quite challenging, the search for molecular and atomic lines at the (sub)millimeter wavelengths can be a solution.

In this letter, we report a secure redshift identification of a near-infrared-dark galaxy discovered by an ALMA deep survey. We derive properties of the interstellar medium (ISM) and discuss the role of these types of galaxies in the galaxy formation history. Throughout this letter, we adopt a cosmology with $\Omega_{\rm m}=0.3, \Omega_\Lambda=0.7$, and H$_0$=70 km s$^{-1}$ Mpc$^{-1}$.

# Observations

![](Fig2v200717.pdf)

Our target, ADF22.A2, was originally discovered through our ALMA deep survey in the SSA22 field. This field represents a significant proto-cluster at $z\approx3.1$ (e.g., (cite: 1998ApJ...492..428S); (cite: 2004AJ....128.2073H); (cite: 2012AJ....143...79Y)), and the ALMA mosaic was designed to observe a $6^\prime \times 3^\prime$ region located at the proto-cluster core at 1.1 mm (ALMA deep field in SSA22 or ADF22; (cite: 2015ApJ...815L...8U); (cite: 2017ApJ...835...98U); (cite: 2018PASJ...70...65U); (cite: 2019Sci...366...97U); (cite: 2017PASJ...69...45H)). ADF22.A2 is the second brightest source in a $2^\prime \times 3^\prime$ subregion among ADF22 (ADF22A) with a flux density of $S_{\rm 1.1~mm}=2.02\pm0.02$ mJy ((cite: 2017ApJ...835...98U)).

ADF22.A2 was detected at 3.6 $\mu$m and 4.5 $\mu$m, while it was completely invisible even at the *Ks*-band or shorter wavelengths (Table. [1](#table:photometry)).

In this work, we refer to ALMA-identified galaxies, which have no detectable counterpart at optical-to-near-infrared wavelengths, as “near-infrared-dark” galaxies. ADF22.A2 is then an example of the population. While this practical selection allows us to shed light on the populations which are missed in optical-to-near infrared surveys on the basis of an available data set, it is not straightforward to compare galaxies between different works since there are a wide variety of data sets, including bands and depths as well as the brightness of galaxies. Considering this ambiguity, we compared ADF22.A2 with other near-infrared-dark ALMA galaxies ((cite: 2009ApJ...690..319W); (cite: 2012MNRAS.427.1066S); (cite: 2014ApJ...788..125S); (cite: 2018A&A...620A.152F); (cite: 2019ApJ...878...73Y)) and a systematical sample of ALMA-identified SMGs ((cite: 2020MNRAS.tmp.1074D)) in Fig. [1](#fig:sample), where the *Ks*-band magnitude and a flux ratio (Log ($S_{1.2  \rm mm}/S_{3.6\mu \rm m}$)) are displayed. ADF22.A2 and the majority of the near-infrared-dark populations are characterized as faint at the $Ks$-band ($\gtrsim24$ AB) and have a low $S_{\rm 1.2mm}$/$S_{\rm 3.6um}$ flux ratio ($\gtrsim 3$), which naively suggests that they are at a higher redshift and/or have a lower stellar mass among the ALMA-identified galaxies (see also (cite: 2014ApJ...788..125S)).

![](Fig3v200717.pdf)

Band 3 observations of ADF22.A2 were performed at two frequency set-ups. The first was carried out as a part of project 2015.1.00212.S and 2016.1.00543.S (PI. H. Umehata for both) at 84.1–87.8 GHz and 96.1–99.8 GHz ((cite: 2019Sci...366...97U)). The 36–44 available antennas were used and observations were executed in two periods; the former one was between 2016 July 21 and 2016 August 19, and the latter one was between 2017 May 7 and 2017 July 4. These resulted in the total on-source time of 13.9 hours for a 13-point mosaic, covering the 7 arcmin$^2$ area which is nearly cospatial with the 1.1 mm mosaic in ADF22A. J2226+0052 and J2148+0657 were observed for bandpass and phase calibration. To set the absolute flux scale, Pallas, J2148+0657, J2232+1143 and Titan were observed.

Subsequently, ADF22.A2 was observed as a part of project 2017.1.00602.S (PI. N. H. Hayatsu) at 91.4–95.2 GHz and 103.4–107.2 GHz. Observations were carried out with 43-45 usable 12 m antennas between 2018 January 18 and 20. The total on-source time was 263 min. The quasar J2148+0657 was utilized for the bandpass, phase, and flux calibration.

The ALMA data were reduced using the Common Astronomy Software Application (casa) versions 4.7.0, 4.7.2, 5.1.0, and 5.4.0 ((cite: 2007ASPC..376..127M)). The data were processed using the standard casa pipeline. The calibrated visibility data were used for imaging with the casa task tclean.

We created dirty cubes with a 100 km s$^{-1}$ velocity bin, applying uvtaper, which yields the synthesized beam sizes of $\approx 1^{\prime\prime}.3$. The dirty cubes were utilized to identify emission lines. For the identified lines, cleaning was done down to $2\sigma$. As we show, we detected a bright CO(4-3) line, and hence we also repeated the clean process without any tapering for the spectral window which encompasses the line. A band 3 continuum map was also created using line-free channels without tapering, which have the synthesized beam $0^{\prime\prime}.90 \times 0^{\prime\prime}.71$ (P.A.$=-74$ deg) and a typical root mean square (RMS) noise of 44 $\mu$Jy beam$^{-1}$.

|                          |                            |
|:------------------------:|:--------------------------:|
|     RA (ALMA, ICRS)      |        22 17 36.11         |
|    Dec. (ALMA, ICRS)     |        00 17 36.70         |
| $S_{1.14\rm{mm}}$ (ALMA) |      2.02 $\pm$ 0.02       |
| $S_{3.13\rm{mm}}$ (ALMA) |  $(59\pm9)\times10^{-3}$   |
|   MegaCam 0.381 $\mu$m   |    $<8.3\times10^{-5}$     |
| Suprime-Cam 0.437 $\mu$m |    $<5.8\times10^{-5}$     |
| Suprime-Cam 0.545 $\mu$m |    $<5.2\times10^{-5}$     |
| Suprime-Cam 0.651 $\mu$m |    $<4.8\times10^{-5}$     |
| Suprime-Cam 0.768 $\mu$m |    $<6.3\times10^{-5}$     |
| Suprime-Cam 0.920 $\mu$m |    $<1.2\times10^{-4}$     |
|    MOIRCS 1.25 $\mu$m    |    $<4.2\times10^{-4}$     |
|    MOIRCS 1.63 $\mu$m    |    $<6.6\times10^{-4}$     |
|    MOIRCS 2.15 $\mu$m    |    $<5.5\times10^{-4}$     |
|     IRAC 3.6 $\mu$m      | $(1.0\pm0.2)\times10^{-3}$ |
|     IRAC 4.5 $\mu$m      | $(1.3\pm0.2)\times10^{-3}$ |
|     IRAC 5.6 $\mu$m      |    $<4.7\times10^{-3}$     |
|     IRAC 8.0 $\mu$m      |    $<6.3\times10^{-3}$     |
|     SPIRE 250 $\mu$m     |     $<11\times10^{-3}$     |
|     SPIRE 350 $\mu$m     |     $<12\times10^{-3}$     |
|     SPIRE 500 $\mu$m     |     $<16\times10^{-3}$     |
|    SCUBA2 850 $\mu$m     |      3.67 $\pm$ 1.18       |
|        JVLA 3 GHz        |  $(11\pm2)\times10^{-3}$   |
|                          |                            |

: Coordinate and multi-band photometry of ADF22.A2

Table notes: Fluxes in units of mJy that are shown and all limits are 3$\sigma$. MegaCam $U$-band, Suprime-Cam $B, V, R, i^{\prime},z^{\prime}$-band, MOIRCS $J, H, Ks$-band, and IRAC data are summarized in (cite: 2014MNRAS.440.3462U). We also use data taken by SPIRE ((cite: 2016MNRAS.460.3861K)), SCUBA2 ((cite: 2017MNRAS.465.1789G)), and JVLA ((cite: 2017ApJ...850..178A)).

# Results

## Line detections and spectroscopic redshift

As is shown in Fig. [2](#fig:stamp) and Fig. [3](#fig:spectra), we successfully detected two emission lines in the combined band 3 spectra at around 92.4 GHz and 98.6 GHz, which provides an unambiguous redshift of $z_{\rm spec}=3.9913\pm0.0008$ for CO(4-3) ($\nu_{\rm rest}=461.041$ GHz) and \[C i\](1-0) ($\nu_{\rm rest}=492.160$ GHz). The redshift was determined from a one-component Gaussian profile fitting to the CO(4-3) spectra, which has a superior signal-to-noise ratio (S/N), while the \[C i\](1-0) line profile shows a consistent value $z_{\rm [CI]}=3.9921\pm0.0012$. Line fluxes were primary estimated from the Gaussian profile fit to the spectra extracted at a centroid position in an integrated line-emission map. We also measured the CO(4-3) flux on the integrated emission map using the casa task imfit to find a slightly (16%) larger value. We finally adopted fluxes of $I_{\rm CO(4-3)}=0.56\pm 0.09$ Jy km s$^{-1}$ and $I_{\rm [CI](1-0)}=0.24\pm 0.06$ Jy km s$^{-1}$, while applying the aperture correction. These estimates correspond to line luminosities $L_{\rm CO(4-3)}=(0.69\pm 0.11$) $\times10^8$ $L_\odot$ and $L_{\rm [CI](1-0)}=(0.31\pm 0.08$) $\times10^8$ $L_\odot$, respectively.

We note that the brightness distributions of the \[C i\](1-0) and CO(4-3) emission lines can decrease due to the effect of the cosmic microwave background (CMB) at $z\approx4$ ((cite: 2013ApJ...766...13D); (cite: 2016RSOS....360025Z)), though it is difficult to properly estimate the effect on ADF22.A2.

## Stellar mass, IR luminosity, and SFR

To infer several physical parameters making use of the precise redshift, we applied the high-redshift extension of the SED-fitting algorithm magphys which includes the effects of dust attenuation ((cite: 2000ApJ...539..718C)) and describes star formation history by a range of ages and star formation time scales ((cite: 2008MNRAS.388.1595D); (cite: 2013ApJ...765....9D)). We used the available photometry, which cover optical-to-near infrared (from the *U* band to *Spitzer* IRAC 8 $\mu$m; (cite: 2014MNRAS.440.3462U) and references therein), *Herschel*/SPIRE bands ((cite: 2016MNRAS.460.3861K)), SCUBA2 ((cite: 2017MNRAS.465.1789G)), ALMA band 6 ((cite: 2017ApJ...835...98U)), band 3, and JVLA 3 GHz ((cite: 2017ApJ...850..178A)). The 3 mm continuum flux was measured to be $S_{\rm 3.13mm}=59.2\pm9.3$ $\mu$Jy using casa/imfit. While we measured flux densities at the optical to near-infrared through aperture photometries in the same manner as is reported in (cite: 2014MNRAS.440.3462U), the counterpart in IRAC 3.6 $\mu$m and 4.5 $\mu$m images is close to a foreground object and thus we estimated the fluxes deblending the two using GALFIT ((cite: 2002AJ....124..266P)) (see Appendix for details). The SPIRE fluxes were also deblended in same manner as in (cite: 2014MNRAS.438.1267S). The photometry and best-fit SED are shown in Fig. [4](#fig:sed) and Table. [1](#table:photometry). For comparison purposes, averaged SEDs, which were derived for $z>3$ SMGs in the UDS field using the same code, magphys, and scaled at 1.1 $\mu$m flux, are displayed ((cite: 2020MNRAS.tmp.1074D)). A large fraction of the ADF22.A2 photometry is also explainable by the template, which indicates that ADF22.A2 may have similar characteristics as the other SMGs at $z>3$.

We note that ADF22.A2 has no X-ray counterpart ((cite: 2009MNRAS.400..299L)) and thus the existence of an X-ray active galactic nucleus (AGN) has not been identified. The 3 GHz radio continuum emission is also well fitted by magphys, which suggests ADF22.A2 show a general, far-infrared correlation, and are not associated with a radio-loud AGN. Due to the relatively poor constraints around the peak of the SED, the derived dust properties might be more uncertain. The effect of the CMB on the continuum flux in the Rayleigh-Jeans regime (e.g., (cite: 2013ApJ...766...13D); (cite: 2019ApJ...887..144J)) is also not considered in this paper.

The fitting yields median values and 68% confidence intervals for the stellar mass $M_*=1.1_{-0.6}^{+1.3}$ $\times10^{11} M_\odot$, the infrared luminosity $L_{\rm IR:8-1000 \mu m}=5.5_{-1.7}^{+3.0}$ $\times10^{12}$ $L_\odot$, and the star-formation rate $430_{-150}^{+230}$ $M_\odot$ yr$^{-1}$. We note that the relatively large uncertainties principally arose due to the limited number of available photometry points. The faintness at optical-to-near-infrared wavelengths, including the non-detection at the restframe around 1.6 $\mu$m, hampered us from putting a constraint on the $A_{\rm V}$ and age as well as the stellar mass. The peak (or shorter wavelength) regime of the dust SED is only constrained by limits and hence it is difficult to constrain the related properties. The initial mass function (IMF) can also have an impact these derived properties. We adopted a Chabrier IMF ((cite: 2003PASP..115..763C)) (but see also (cite: 2018Natur.558..260Z)).

## Molecular gas mass and gas mass conversion factor

The total molecular gas mass stored in ADF22.A2 was also estimated in three ways.

First, we utilized the \[C i\](1–0) emission as a tracer of the gas mass. The \[C i\](1–0) line is proposed to be a measure of the molecular gas mass. The critical density is similar to that of CO(1–0).

Moreover \[C i\] is sensitive to CO-dark molecular gas where cosmic rays can destroy CO (e.g., (cite: 2004ApJ...615L..29P); (cite: 2017MNRAS.466.2825B); (cite: 2017ApJ...840L..18J)). We calculated the \[C i\]-based H$_2$ mass, assuming an optically thin case, following (cite: 2004ApJ...615L..29P):

$$\begin{equation}
\begin{split}
M({\rm H_2})^{\rm [CI]}&=1375.8 D_{\rm L}^2(1+z)^{-1}\left(\frac{X_{\rm [CI]}}{10^{-5}}\right)^{-1}\left(\frac{A_{10}}{10^{-7} {\rm s}^{-1}}\right)^{-1} \\
 &\quad\times Q_{10}^{-1}S_{\rm [CI]}\Delta v
\end{split}
,
\end{equation}$$ where $X_{\rm [CI]}$ is the abundance ratio of \[C i\]/H$_2$. Here we adopt $X_{\rm [CI]}=3\times10^{-5}$ ((cite: 2004ApJ...615L..29P); (cite: 2017MNRAS.466.2825B)). The Einstein $A$ coefficient $A_{10}=7.93\times10^{-8}$ s$^{-1}$ was incorporated. We used the excitation factor $Q_{10}=0.6$ ((cite: 2017MNRAS.466.2825B); (cite: 2018ApJ...856...72O)). Then Equation (1) gives $M (H_2)^{\rm [CI]}=(5.9\pm1.5)\times10^{10}$ $M_\odot$.

Second, we also estimated the total H$_2$ mass using CO(4–3), though caution should be exercised since such a mid-$J$ transition line traces relatively dense and warm molecular gas. If we assume a brightness temperature ratio of $r_{43/10}=0.41$ and the conversion factor $\alpha_{\rm CO}$=1.0 $M_\odot$ (K km s$^{-1}$pc$^{2}$)$^{-1}$ ((cite: 2011MNRAS.412.1913I); (cite: 2011ApJ...739L..31R); (cite: 2013MNRAS.429.3047B)), the observed CO(4-3) line intensity suggests a molecular gas mass of $M (H_2)^{\rm CO(4-3)}=(5.4\pm1.2)\times10^{10}$ $M_\odot$.

Thirdly, we made use of the dust mass as a tracer. The dust mass derived by SED fitting using magphys is $M_{\rm d}=4.3\pm0.9\times10^8$ $M_\odot$. Assuming a dust-to-gas mass conversion factor of 120 ((cite: 2008ApJS..178..189W)), this implies a molecular gas mass of $M (H_2)^{\rm dust}=(5.2\pm1.1)\times10^{10}$ $M_\odot$. Thus estimates using the three methods are consistent. In this paper, we use the \[C i\]-based gas mass in the following discussion.

Finally we checked a diversity of derived $\alpha_{\rm CO}$, which brought the derived molecular gas mass with different tracers into agreement. The measurements on the basis of \[C i\] and dust give $\alpha_{\rm CO}=1.1\pm0.4$ and $\alpha_{\rm CO}=1.0\pm0.3$ through the comparison with CO-based gas mass, respectively. Thus the conversion factors derived from three clues are generally in good agreement for ADF22.A2, while there are a number of assumed parameters including $X_{\rm [CI]}$ and a dust-to-gas mass conversion.

![](Fig4v200717.pdf)

# Discussion and conclusion

![](Fig5v200717.pdf)

The robust identification of its redshift, $z=3.991$, and the suite of multi-wavelength data sets pave the way to identify an example of near-infrared-dark galaxies in the history of galaxy assembly and understand the physical and chemical properties of these types of populations.

The left panel of Fig. [5](#fig:nature) shows the relation between the stellar mass and SFR for ADF22.A2, compared with two other samples of near-infrared-dark galaxies and the “main-sequence” relation at $z=4$ derived by (cite: 2017A&A...599A.134S) on the basis of ALMA band 7 observations. The panel suggests that ADF22.A2 is characterized by massive dusty star-forming galaxies, which are located around (or above) the main-sequence at $z\sim4$. ADF22.A2 is also located at a region where $z>3.5$ SMGs selected by an ALMA Survey of Submillimetre Galaxies in the Extended Chandra Deep Field South (ALESS, (cite: 2015ApJ...806..110D)) and "*H*-dropout" populations ((cite: 2019Natur.572..211W)), which tend to be fainter at (sub)millimeter than the SMGs originally sampled as a single-dish source overlap, which indicates that ADF22.A2 shares the properties with both populations. This would be reasonable, considering the fact that ADF22.A2 was first identified by an ALMA deep survey ((cite: 2015ApJ...815L...8U)) and successively identified by SCUBA2 ((cite: 2017MNRAS.465.1789G)), while it was missed by the previous AzTEC/ASTE survey ((cite: 2014MNRAS.440.3462U)).

Since ADF22.A2 was found in an ALMA deep survey which covers a significant cosmic volume contiguously, one can estimate the cosmic volume of the near-infrared-dark ALMA galaxies. (cite: 2019Natur.572..211W) estimated the number density of the *H*-dropout galaxies $\approx2\times10^{-5}$ Mpc$^{-3}$ on the basis of photometric redshifts. If we consider a similar redshift range ($z\approx3.4-5.4$) as was adopted in (cite: 2019Natur.572..211W), the cosmic volume covered by the $2^\prime \times 3^\prime$ region of ADF22A is $\approx3.5\times10^4$ Mpc$^{3}$, and the expected number of these types of populations is around unity. Considering the fact that the detection limit is comparable between the works ((cite: 2017ApJ...835...98U); (cite: 2019Natur.572..211W)) and that all of the 18 ADF22A sources now have spectroscopic redshifts ((cite: 2019Sci...366...97U)), both estimates are consistent. This gives another clue supporting the prevalence of the near-infrared-dark ALMA galaxies in the early Universe. We also note that there are some caveats, however. The sample in (cite: 2019Natur.572..211W) is for *H*-dropout galaxies, and the selection criteria are not perfectly equal to ours. Most of the spectroscopic redshifts of the *H*-dropout galaxies are still lacking; hence, they leave uncertainties as to the cosmic volume.

The detection of the \[C i\](1–0) and CO(4–3) lines, together with infrared luminosity, gives us a clue as to the nature of the ISM. We derived the gas density and the strength of the far-ultraviolet radiation field on the basis of the PDR model of (cite: 1999ApJ...527..795K) and (cite: 2006ApJ...644..283K). While dust continuum and \[C i\](1–0) emission are generally optically thin, CO emission is optically thick. We increase the observed CO luminosity by a factor of two to incorporate this effect. Fig. [6](#fig:pdr) shows the comparison between the observed ratios and the theoretical models. The PDR models suggest the atomic gas density of $n=(5.6_{-2.5}^{+4.6})\times10^4$ cm$^{-3}$ and the UV radiation field $(1.8_{-0.8}^{+7.8})\times10^3~G_0$ for ADF22.A2 (Fig. [6](#fig:pdr)). The right panel of Fig. [5](#fig:nature) shows the ratios of $L_{\rm [CI](1-0)}/L_{\rm IR}$ and $L_{\rm [CI](1-0)}/L_{\rm CO(4-3)}$ compared with $z\sim4$ lensed SMGs ((cite: 2017MNRAS.466.2825B); (cite: 2018A&A...620A..61C);(cite: 2019A&A...624A..23N)) and $z\sim3$ SMGs ((cite: 2013MNRAS.435.1493A)). The consistency of the line ratios suggests that these characteristics, the UV radiation field strength and gas density of the ISMs within ADF22.A2, are similar to those of other dusty starburst galaxies selected from traditional bright SMG surveys. More samples of near-infrared-dark ALMA galaxies, which have measurements of \[C i\](1–0) and CO(4–3) lines, will pave the way to further characterize ISM properties of the population.

We also placed ADF22.A2 in the context of galaxy evolution across the cosmic time.

Recently an increasing number of quiescent galaxies has been identified at $z\sim3-4$ (e.g., (cite: 2018A&A...618A..85S); (cite: 2019ApJ...885L..34T); (cite: 2019arXiv190910540V)). These findings invoke the prevalent galaxy populations which experience an active star-forming phase at higher redshifts. The measurements of ADF22.A2 suggest a gas-mass fraction of $\sim35\%$, which are defined as $f_{\rm gas}=M_{\rm gas}$/($M_{\rm gas}+M_*$). Together with a significant amount of stellar mass $M_*\approx10^{11}$ $M_\odot$, the gas mass fraction indicates that ADF22.A2 is a relatively evolved system. The gas depletion time of ADF22.A2 is $\tau_{\rm dep}=M_{\rm gas}/SFR\approx0.1-0.2$ Gyr; hence, ADF22.A2 would evolve into a massive (log($M_*/M_\odot \approx 10^{11}$)) quiescent system at $z=3.6-3.8$ on the simple assumption that the galaxy simply consumes the estimated molecular gas reservoir with the constant star-formation rate.

These results support the scenario that the near-infrared-dark ALMA populations are progenitors of quiescent galaxy populations at $z\approx3-4$.

![](Fig6v200717.pdf)

ADF22.A2 demonstrates that ALMA deep surveys are a powerful tool to obtain an unbiased picture of galaxy formation and evolution, exemplifying an intriguing galaxy which was identified and characterized by ALMA observations. Further systematic census will help us understand the general nature of the near-infrared-dark ALMA galaxies.

# Acknowledgements

We thank an anonymous referee for a number of constructive comments.

We thank Ms. Ugne Dudzevičiūtė for providing catalogs and a SED template.

We thank Prof. R. J. Ivison for useful discussions.

H.U. and K.K. acknowledge support from JSPS KAKENHI grant (17K14252, 20H01953, 17H06130). This work was supported by the NAOJ ALMA Scientific Research Grant Number 2017-06B. I.R.S. and A.M.S. acknowledge support by the Science and Technology Facilities Council \[grant number ST/P000541/1\]. Y.A. acknowledges financial support by NSFC grant 11933011.

This paper makes use of the following ALMA data: ADS/JAO. ALMA#2013.1.00162.S, #2015.1.00212.S, #2016.1.00543.S, #2017.1.00602.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ.

The National Radio Astronomy Observatory is a facility of the National Science Foundation operated under cooperative agreement by Associated Universities, Inc.

This paper is based on data collected at Subaru Telescope, which is operated by the National Astronomical Observatory of Japan. This work is based on observations made with the Spitzer Space Telescope, which is operated by the Jet Propulsion Laboratory, California Institute of Technology under a contract with NASA.

65 natexlab

(ref: 2013MNRAS.435.1493A) Alaghband-Zadeh, S., Chapman, S. C., Swinbank, A. M., et al. 2013, MNRAS, 435, 1493

(ref: 2017ApJ...850..178A) Ao, Y., Matsuda, Y., Henkel, C., et al. 2017, ApJ, 850, 178

(ref: 2002PhR...369..111B) Blain, A. W., Smail, I., Ivison, R. J., Kneib, J. P., & Frayer, D. T. 2002, Phys. Rep., 369, 111

(ref: 2017MNRAS.466.2825B) Bothwell, M. S., Aguirre, J. E., Aravena, M., et al. 2017, MNRAS, 466, 2825

(ref: 2013MNRAS.429.3047B) Bothwell, M. S., Smail, I., Chapman, S. C., et al. 2013, MNRAS, 429, 3047

(ref: 2018A&A...620A..61C) Cañameras, R., Yang, C., Nesvadba, N. P. H., et al. 2018, A&A, 620, A61

(ref: 2014PhR...541...45C) Casey, C. M., Narayanan, D., & Cooray, A. 2014, Phys. Rep., 541, 45

(ref: 2019ApJ...887...55C) Casey, C. M., Zavala, J. A., Aravena, M., et al. 2019, ApJ, 887, 55

(ref: 2003PASP..115..763C) Chabrier, G. 2003, PASP, 115, 763

(ref: 2000ApJ...539..718C) Charlot, S. & Fall, S. M. 2000, ApJ, 539, 718

(ref: 2008MNRAS.388.1595D) da Cunha, E., Charlot, S., & Elbaz, D. 2008, MNRAS, 388, 1595

(ref: 2013ApJ...766...13D) da Cunha, E., Groves, B., Walter, F., et al. 2013a, ApJ, 766, 13

(ref: 2013ApJ...765....9D) da Cunha, E., Walter, F., Decarli, R., et al. 2013b, ApJ, 765, 9

(ref: 2015ApJ...806..110D) da Cunha, E., Walter, F., Smail, I. R., et al. 2015, ApJ, 806, 110

(ref: 1999ApJ...519..610D) Dey, A., Graham, J. R., Ivison, R. J., et al. 1999, ApJ, 519, 610

(ref: 2020MNRAS.tmp.1074D) Dudzevičiūtė, U., Smail, I., Swinbank, A. M., et al. 2020, MNRAS \[\]

(ref: 2017MNRAS.466..861D) Dunlop, J. S., McLure, R. J., Biggs, A. D., et al. 2017, MNRAS, 466, 861

(ref: 2018A&A...620A.152F) Franco, M., Elbaz, D., Béthermin, M., et al. 2018, A&A, 620, A152

(ref: 2004AJ....127..728F) Frayer, D. T., Reddy, N. A., Armus, L., et al. 2004, AJ, 127, 728

(ref: 2017MNRAS.465.1789G) Geach, J. E., Dunlop, J. S., Halpern, M., et al. 2017, MNRAS, 465, 1789

(ref: 2009ApJ...699.1610H) Hainline, L. J., Blain, A. W., Smail, I., et al. 2009, ApJ, 699, 1610

(ref: 2004AJ....128.2073H) Hayashino, T., Matsuda, Y., Tamura, H., et al. 2004, AJ, 128, 2073

(ref: 2017PASJ...69...45H) Hayatsu, N. H., Matsuda, Y., Umehata, H., et al. 2017, PASJ, 69, 45

(ref: 2011MNRAS.412.1913I) Ivison, R. J., Papadopoulos, P. P., Smail, I., et al. 2011, MNRAS, 412, 1913

(ref: 2017ApJ...840L..18J) Jiao, Q., Zhao, Y., Zhu, M., et al. 2017, ApJL, 840, L18

(ref: 2020ApJ...890..171J) Jiménez-Andrade, E. F., Zavala, J. A., Magnelli, B., et al. 2020, ApJ, 890, 171

(ref: 2019ApJ...887..144J) Jin, S., Daddi, E., Magdis, G. E., et al. 2019, ApJ, 887, 144

(ref: 2016MNRAS.460.3861K) Kato, Y., Matsuda, Y., Smail, I., et al. 2016, MNRAS, 460, 3861

(ref: 2006ApJ...644..283K) Kaufman, M. J., Wolfire, M. G., & Hollenbach, D. J. 2006, ApJ, 644, 283

(ref: 1999ApJ...527..795K) Kaufman, M. J., Wolfire, M. G., Hollenbach, D. J., & Luhman, M. L. 1999, ApJ, 527, 795

(ref: 2009MNRAS.400..299L) Lehmer, B. D., Alexander, D. M., Chapman, S. C., et al. 2009, MNRAS, 400, 299

(ref: 2007ASPC..376..127M) McMullin, J. P., Waters, B., Schiebel, D., Young, W., & Golap, K. 2007, Astronomical Society of the Pacific Conference Series, Vol. 376, CASA Architecture and Applications, ed. R. A. Shaw, F. Hill, & D. J. Bell, 127

(ref: 2019A&A...624A..23N) Nesvadba, N. P. H., Cañameras, R., Kneissl, R., et al. 2019, A&A, 624, A23

(ref: 2018ApJ...856...72O) Oteo, I., Ivison, R. J., Dunne, L., et al. 2018, ApJ, 856, 72

(ref: 2004ApJ...615L..29P) Papadopoulos, P. P. & Greve, T. R. 2004, ApJL, 615, L29

(ref: 2018ApJ...864...49P) Pavesi, R., Sharon, C. E., Riechers, D. A., et al. 2018, ApJ, 864, 49

(ref: 2002AJ....124..266P) Peng, C. Y., Ho, L. C., Impey, C. D., & Rix, H.-W. 2002, AJ, 124, 266

(ref: 2011ApJ...739L..31R) Riechers, D. A., Hodge, J., Walter, F., Carilli, C. L., & Bertoldi, F. 2011, ApJL, 739, L31

(ref: 2020ApJ...895...81R) Riechers, D. A., Hodge, J. A., Pavesi, R., et al. 2020, ApJ, 895, 81

(ref: 2017ApJ...850....1R) Riechers, D. A., Leung, T. K. D., Ivison, R. J., et al. 2017, ApJ, 850, 1

(ref: 2018A&A...618A..85S) Schreiber, C., Glazebrook, K., Nanayakkara, T., et al. 2018, A&A, 618, A85

(ref: 2017A&A...599A.134S) Schreiber, C., Pannella, M., Leiton, R., et al. 2017, A&A, 599, A134

(ref: 2014ApJ...788..125S) Simpson, J. M., Swinbank, A. M., Smail, I., et al. 2014, ApJ, 788, 125

(ref: 1999MNRAS.308.1061S) Smail, I., Ivison, R. J., Kneib, J. P., et al. 1999, MNRAS, 308, 1061

(ref: 1998ApJ...492..428S) Steidel, C. C., Adelberger, K. L., Dickinson, M., et al. 1998, ApJ, 492, 428

(ref: 2012MNRAS.427.1066S) Swinbank, A. M., Karim, A., Smail, I., et al. 2012, MNRAS, 427, 1066

(ref: 2014MNRAS.438.1267S) Swinbank, A. M., Simpson, J. M., Smail, I., et al. 2014, MNRAS, 438, 1267

(ref: 2015ApJ...811L...3T) Tadaki, K.-i., Kohno, K., Kodama, T., et al. 2015, ApJL, 811, L3

(ref: 2019ApJ...885L..34T) Tanaka, M., Valentino, F., Toft, S., et al. 2019, ApJL, 885, L34

(ref: 2019Sci...366...97U) Umehata, H., Fumagalli, M., Smail, I., et al. 2019, Science, 366, 97

(ref: 2018PASJ...70...65U) Umehata, H., Hatsukade, B., Smail, I., et al. 2018, PASJ, 70, 65

(ref: 2014MNRAS.440.3462U) Umehata, H., Tamura, Y., Kohno, K., et al. 2014, MNRAS, 440, 3462

(ref: 2015ApJ...815L...8U) Umehata, H., Tamura, Y., Kohno, K., et al. 2015, ApJL, 815, L8

(ref: 2017ApJ...835...98U) Umehata, H., Tamura, Y., Kohno, K., et al. 2017, ApJ, 835, 98

(ref: 2019arXiv190910540V) Valentino, F., Tanaka, M., Davidzon, I., et al. 2019, arXiv e-prints, arXiv:1909.10540

(ref: 2016ApJ...833...67W) Walter, F., Decarli, R., Aravena, M., et al. 2016, ApJ, 833, 67

(ref: 2012Natur.486..233W) Walter, F., Decarli, R., Carilli, C., et al. 2012, Nature, 486, 233

(ref: 2019Natur.572..211W) Wang, T., Schreiber, C., Elbaz, D., et al. 2019, Nature, 572, 211

(ref: 2009ApJ...690..319W) Wang, W.-H., Barger, A. J., & Cowie, L. L. 2009, ApJ, 690, 319

(ref: 2008ApJS..178..189W) Wilson, C. D., Petitpas, G. R., Iono, D., et al. 2008, ApJS, 178, 189

(ref: 2012AJ....143...79Y) Yamada, T., Nakamura, Y., Matsuda, Y., et al. 2012, AJ, 143, 79

(ref: 2019ApJ...878...73Y) Yamaguchi, Y., Kohno, K., Hatsukade, B., et al. 2019, ApJ, 878, 73

(ref: 2016PASJ...68...82Y) Yamaguchi, Y., Tamura, Y., Kohno, K., et al. 2016, PASJ, 68, 82

(ref: 2016RSOS....360025Z) Zhang, Z.-Y., Papadopoulos, P. P., Ivison, R. J., et al. 2016, Royal Society Open Science, 3, 160025

(ref: 2018Natur.558..260Z) Zhang, Z.-Y., Romano, D., Ivison, R. J., Papadopoulos, P. P., & Matteucci, F. 2018, Nature, 558, 260

# Deblending IRAC photometry

Since the counterpart of ADF22.A2 has a close companion in the 3.6 $\mu$m and 4.5 $\mu$ images, we measured the flux density using galfit ((cite: 2002AJ....124..266P)). We fit the region around ADF22.A2 using three components, including two point sources and the sky. Fig. [7](#fig:galfit) shows the best-fit results. The derived fluxes are $S_{\rm 3.6\mu m}=1.0\pm0.2$ $\mu$Jy and $S_{\rm 4.5\mu m}=1.3\pm0.2$ $\mu$Jy, respectively (see also Table [1](#table:photometry)). These measurements exceed the 3$\sigma$ detection limits for a point source (0.4 $\mu$Jy and 0.8 $\mu$Jy at 3.6 $\mu$m and 4.5 $\mu$m, respectively), as was derived by (cite: 2009ApJ...699.1610H).

![](FigA1v200717.pdf)

</paper>

## Items to check

```json
[
 {
  "path": "processing.calibration.casa_version.evidence[0]",
  "value": "4.7.0, 4.7.2, 5.1.0, 5.4.0",
  "failed_quote": "casa versions 4.7.0, 4.7.2, 5.1.0, and 5.4.0"
 },
 {
  "path": "analysis_steps[1].fitting.evidence[0]",
  "value": "Gaussian profile",
  "failed_quote": "(no quote given)"
 },
 {
  "path": "analysis_steps[3].fitting.evidence[0]",
  "value": "median and 68% intervals",
  "failed_quote": "(no quote given)"
 },
 {
  "path": "analysis_steps[3].validation.evidence[0]",
  "value": "compared with z>3 SMG average SEDs",
  "failed_quote": "(no quote given)"
 }
]
```
