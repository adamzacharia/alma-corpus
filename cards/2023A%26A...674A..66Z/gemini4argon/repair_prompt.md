# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2023A%26A...674A..66Z\gemini4argon\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
# New constraints on the presence of debris disks around\
G 196-3 B and VHS J125601.92$-$125723.9 b

The existence of warm (protoplanetary) disks around very young isolated planetary and brown dwarfs mass objects is known based on near- and mid-infrared flux excesses and millimeter observations. These disks may later evolve into debris disks/rings, although none has been observed/confirmed so far. Little is known about circum(sub)stellar and debris disks around substellar objects.

We aim at investigating the presence of debris disks around two of the closest ($\sim$20 pc), young substellar companions, namely G 196-3 B and VHS J125601.92$-$125723.9 b (VHS J1256$-$1257 b), whose masses straddle the borderline between planets and brown dwarfs. Both are companions at wide orbits ($\ge$100 au) of M-type dwarfs and their ages (50–100 Myr and 150–300 Myr, respectively) are thought to be adequate for the detection of second generation disks.

We obtained deep images of G 196-3 B and VHS J1256$-$1257 b with the NOrthern Extended Millimeter Array (NOEMA) at 1.3 mm. These data were combined with recently published Atacama Large Millimeter Array (ALMA) and Very Large Array (VLA) data of VHS J1256$-$1257 b at 0.87 mm and 0.9 cm, respectively.

Neither G 196-3 B nor VHS J1256$-$1257 b were detected in the NOEMA, ALMA and VLA data. At 1.3 mm, we imposed flux upper limits of 0.108 mJy (G 196-3 B) and 0.153 mJy (VHS J1256$-$1257 b) with a 3-$\sigma$ confidence. Using the flux upper limits at the millimeter and radio wavelength regimes, we derived maximum values of 1.38$\times10^{-2}$ $M_{\rm Earth}$ and 5.46$\times10^{-3}$ $M_{\rm Earth}$ for the mass of any cold dust that might be surrounding G 196-3 B and VHS J1256$-$1257 b, respectively.

We put our results in the context of other deep millimeter observations of free-floating and companion objects with substellar masses smaller than 20 M$_{\rm Jup}$ and ages between $\sim$1 and a few hundred million years. Only two very young (2–5.4 Myr) objects are detected out of a few tens. This implies that the disks around these very low-mass objects must have small masses, and possibly reduced sizes, in agreement with findings by other groups. If debris disks around substellar objects scale down (in mass and size) in a similar manner as protoplanetary disks do, millimeter observations of moderately young brown dwarfs and planets must be at least two orders of magnitude deeper for being able to detect and characterize their surrounding debris disks.

# Introduction

Substellar objects are known to host accretion and protoplanetary disks in a similar way as stars. First evidences of disks around brown dwarfs were given by the presence of strong and resolved H$\alpha$ emission line and near- and mid-infrared excesses (cite: Natta2001; Jaya2002; Jaya2003; Muzerolle2003; Muzerolle2005; Pascucci2003; Natta2004; Mohanty2005). The frequency of protoplanetary disks around brown dwarfs has been investigated in several star forming regions such as Taurus, IC 348, Chamaeleon, $\sigma$ and $\lambda$ Orionis, $\rho$ Ophiuchus, Upper Scorpius, and TW Hya, all regions with less than 20 Myr, resulting in a rate ($\sim$40 %) very similar to that of low-mass stars (cite: Luhman2005; Luhman2006; Luhman2010; Luhman2012; Guieu2007; Damjanov2007; Caballero2007; ZapateroOsorio2007; Hernandez2007; Barrado2007; Bouy2007; Scholz2007; Scholz2008; Alcala2008; Riaz2008; Riaz2009; Pena2012; Alves2013). Spatially resolved images of protoplanetary disks surrounding massive brown dwarfs and proto-brown dwarfs in young star-forming regions have also been obtained thanks to the power of the Atacama Large Millimeter Array (ALMA) observations (cite: Ricci2014; Testi2016; Riaz2019; Rilinger2021). These data indicate that the masses and sizes of young circumsubstellar disks are a scaled version of the disks around low-mass stars.

Protoplanetary disks around brown dwarfs show evidence of growth toward planetesimals (cite: Apai2005; Ricci2014) and are expected to evolve into debris disks/rings. The time scale for the protoplanetary–to–debris transition in the substellar regime is not well established so far and may depend from case to case. Preliminary studies suggest that brown dwarf disks transition to the debris phase by $\sim$40–50 Myr ages (cite: Riaz2014). In the stellar regime, protoplanetary disks with large amounts of gas survive up to $\sim$10 Myr (cite: Wyatt2015). Based on the high frequency of circumbsubstellar disks at very young ages, debris disks as descendants of the original disks around brown dwarfs should be common as well. But none is known/confirmed up to date to the best of our knowledge. Two candidates have been reported in the literature. V1400 Cen is a young, solar-mass star of the Sco-Cen OB association with an age of about 16 Myr. This star exhibited a remarkably long, deep, and complex eclipse event that was interpreted as it being eclipsed by a low-mass object (likely a brown dwarf or planet) orbited by a dense inner disk (cite: Mamajek2012; Kenworthy2015). In a subsequent paper, (cite: Kenworthy2020) reported a non-detection of any flux in the Atacama Large Millimeter/submillimeter Array (ALMA) Band 7 with an upper limit 3 $\sigma$ level of 57.6 $\mu$Jy at the position of the star. The authors concluded that the hypothesised bound ring system is composed of dust smaller than 1 mm in size, implying a young ring structure. The second candidate is G 196-3 B (L3 spectral type), the brown dwarf companion to a low-mass star with an age in the interval 50–100 Myr (cite: Rebolo1998). (cite: Zakhozhay2017) argued that a feasible scenario to account for the very red colors of the L3 dwarf is the presence of a debris disk/ring. The lack of evidence of substellar debris disks is likely because many of the known brown dwarfs are old, lie at far distances, or remain unresolved from their more massive primaries.

The aim of our current study is to investigate the possibility of circumplanetary or debris disk presence in two substellar companions that reunite unique conditions of youth, proximity, and companion–host separation: VHS J125601.92$-$125723.9 b (from now on VHS J1256$-$1257 b) and G 196-3 B. In this paper, we introduce the targets in Section [\[targets\]](#targets) and present the results of the 0.9 mm and 1.3 mm observations in Section [3](#sec:observ). The mass upper limits of any hypothetical cold dusty disk surrounding the targets are calculated in Section [4](#sec:upperLimits). Discussion and conclusions are presented in Sections [5](#sec:discussion) and [6](#sec:conclusions).

# Target selection 

VHS J1256$-$1257 is a multiple system formed by at least three low-mass objects, which is exceptional for its proximity, 22.2 pc, and young age, 150–300 Myr, (cite: Gauza2015; Stone2016; Dupuy2020). VHS J1256$-$1257 comprises a M7.5 primary component, which is actually an equal-magnitude close binary with a separation of 123 mas as revealed by the adaptive optics observations of (cite: Stone2016), and one L7$\pm$1.5 companion that lies at a distance of $8"$ from the binary (cite: Gauza2015). According to evolutionary models (cite: Chabrier2000), both components of the binary have equal effective temperatures $T_{\rm eff}\approx 2620$ K (cite: Stone2016) and masses of $M_{\rm \ast}=60-100$ M$_{\rm Jup}$ (cite: Dupuy2020). The mass of the L7 companion is estimated in the interval 10–35 M$_{\rm Jup}$. In the work by (cite: Dupuy2020), based on the trigonometric parallax of 22.2$^{+1.1}_{-1.2}$ pc[^1], the authors derived a mass of 19$\pm 5$ M$_{\rm Jup}$ and a temperature of 1240$\pm 50$ K for VHS J1256$-$1257 b. More recently, (cite: Dupuy2023), using Keck adaptive optics imaging and aperture masking interferometry, have determined the primary binary orbit (a=1.96$\pm$0.03 AU, $P$ = 7.1$\pm$0.02 yr) and measured its dynamical total mass (0.141$\pm$0.008 M$_{\odot}$), consistent with being a brown dwarf or very low-mass stellar binary of 70–80 M$_{\rm Jup}$. The brightness, relatively wide orbit, and a lower contrast between the host star than in the case of other known directly imaged exoplanets, makes VHS J1256$-$1257 b an exceptional object of which a thorough characterization is feasible. For example, intense photometric monitoring of this object has shown that this is the coolest object with larger photometric variability currently known (cite: Bowler2020; Zhou2022). More recently, an intermediate resolution near-infrared spectrum of this object has been obtained with X-Shooter (cite: Petrus2023) and JWST has obtained a high fidelity 1-20 micron spectrum (cite: Miles2022), which indicate the presence of water, methane, carbon monoxide, carbon dioxide, sodium, and potassium in its atmosphere, becoming a reference for exoplanet research. The spectral shape of VHS J1256$-$1257 b seems to be influenced by disequilibrium chemistry and silicate clouds.

The *Gaia* Early Data Release 3 (EDR3) (cite: GaiaCollaboration2016; Lindegren2021) provides a distance of 21.15$\pm$0.21 pc for the primary binary component. This is the value we adopted for this paper. With this new determination and following the approach explained in (cite: Gauza2015), the mass of VHS J1256$-$1257 b turns out to be 20.5$^{+6.0}_{-4.5}$ M$_{\rm Jup}$, using the BT-Settl evolutionary models (cite: 1998A&A...337..403B; 2003A&A...402..701B; Chabrier2000) with the (cite: 2011SoPh..268..255C) solar abundances and the luminosity of log($L$/${\rm L_{\odot}}$) = -4.57$\pm$0.2 which we computed from the observed flux integration following the procedure described in (cite: Zakhozhay2017). Uncertainty in the mass determination reflects the range of possible masses from the models given the age and luminosity in BT-Settl models. VHS J1256$-$1257 b is confirmed to be young for its spectroscopic properties revealing a low-gravity atmosphere summarized by (cite: Gauza2015). What is relevant for this work is the remarkable photometric property of VHS J1256$-$1257 b: it is a very red source with near- and mid-infrared colors in excess with respect to dwarfs of related spectral types. Actually, VHS J1256$-$1257 b is one of the reddest dwarfs known in the literature.

G 196-3 B is the 15.3$^{+7.7}_{-2.7}$ M$_{\rm Jup}$, L3-type substellar companion of the nearby, high proper motion, M2.5 star G 196-3 A (cite: Rebolo1998). The system has a projected orbital size of 16$"$ at the parallactic distance of 21.81$\pm$0.01 pc  (cite: GaiaCollaboration2016; Lindegren2021). The youth of G 196-3 B (50–100 Myr) is confirmed by the vast amount of optical and near-infrared spectroscopic observations: strong Li i and weak Na i and K i absorption, strong VO and H$_2$O bands, plus the peaked $H$-band continuum (cite: Martin1999; Kirkpatrick2001; McGovern2004; McLean2007; Allers2007; ZapateroOsorio2014). As VHS J1256$-$1257 b, G 196-3 B, with $T_{\rm eff} \approx 1850$ K, also has very red colors that clearly deviate from the indices of field dwarfs of similar spectral classification (cite: ZapateroOsorio2010). This reddening behavior is not observed in younger (lower gravity) objects of related temperatures (cite: Lodieu2013; Pena2012; ZapateroOsorio2017). Alternatively, (cite: Zakhozhay2017) studied the physical feasibility of a debris disk being responsible for the infrared flux excesses. The authors modeled the spectral energy distribution of G 196-3B from the optical through 24 $\mu$m and found that the best-fit solution is provided by a combination of an unreddened L3 atmosphere and a warm ($\sim$ 1300 K), optically thick, narrow debris disk (“ring”) containing sub-micron particles and a mass $\ge 7 \times 10^{-10}$ M$_{\rm earth}$ located very near the central substellar object. Such a disk may resemble the rings of Neptune and Jupiter, except for its high temperature.

# Observations and data reduction

## NOEMA

We observed both systems VHS J1256$-$1257 and G 196-3 B using ten 15-m antennas of the NOrthern Extended Millimeter Array (NOEMA). NOEMA is currently the most advanced millimeter interferometer in the Northern Hemisphere situated at 2550 m on the Plateau de Bure in the French Alps [^2]. The interferometer is equipped with a high-performance wide-band correlator named PolyFiX[^3].

All antennas are equipped with 2SB receivers, which provide low noise performance and long-term stability. Observations were performed on 2019 March 25 and 27 for VHS J1256$-$1256 and G 196-3 B, respectively. We used NOEMA in compact configuration D, with baselines between 24 and 176 m. This configuration allowed us to obtain images at 1.3 mm (230 GHz) with an angular resolution of 2.53$''$ $\times$ 1.43$''$ at $0^{\circ}$ for VHS J1256$-$1257 and 1.73$''$ $\times$ 1.33$''$ at $64^{\circ}$ for G 196-3 B. The NOEMA field of view of 21.9$''$ at 1.3 mm was centered at the middle distance between the primary and the companion of VHS J1256$-$1257 and at the substellar companion G 196-3 B (the primary G 196-3 A was outside of the field of view). The total on-source integration time was 1.5 h for VHS J1256$-$1257 and 2.1 h for G 196-3 B.

Data calibration was performed with the GILDAS-CLIC software (sep-2019 version)[^4]. Continuum was obtained by averaging line-free channels over the 7.744 MHz width (USB) centered at 230.0 GHz. We obtained a root mean square (rms) noise of 0.051 mJy beam$^{-1}$ (1-$\sigma$) for VHS J1256$-$1257 b and 0.036 mJy beam$^{-1}$ (1-$\sigma$) for G 196-3 B in the synthetized beam, corresponding to minimum detected signals of 0.153 mJy and 0.108 mJy (adopting a 3-$\sigma$ detection limit). Images were cleaned using robust weighting with the Högbom’s method (cite: hogbom2003) and a robust parameter of 3. To obtain the convergence of the flux 1700 iterations were used. Nevertheless, even by tapering baselines above 50 m projected length, no detections were found.

## ALMA

ALMA observations were obtained for the VHS J1256$-$1257 system on 2019 March 07 between 5:22 and 07:27 UT using 43 of the ALMA 12 m antennas in Band 7 or $\sim$0.9 mm (G 196-3 is not observable from ALMA latitude). The main scientific objective was to detect the continuum emission from a possible disk around the companion VHS J1256$-$1257 b. The central binary VHS J1256$-$1257 AB was observed simultaneously as it lies at the north-western border of the ALMA field of view. Two ALMA execution blocks were carried out, yielding a total on-source time of 73 min. The configuration was nominally TM1. The longest baseline was 313 m long, while the shortest was 15 m. This resulted in a synthetized beam of 0.91$''$ $\times$ 0.81$''$ with a position angle (P.A.) of $-$84.8$^{\circ}$. The precipitable water vapor (PWV) in the atmosphere above ALMA was between 1.21 mm and 1.26 mm during the observations. We used a full continuum sensitivity configuration. However, we adopted a mixed spectral (line and continuum) setup to maximize the potential scientific outcome of the project by also measuring the CO 3-2 line at 345.8 GHz in base band 1 with a spectral resolution of 0.98 km s$^{-1}$ covering a bandwidth of 1.875 GHz (1920 channels). Base band 2 was centered 1.8 GHz below the central frequency (344.0 GHz) to cover 2 GHz at a lower resolution (27.2 km s$^{-1}$; 128 channels). Likewise, the other two base bands were centered at the standard image band frequencies (357.8 and 356.0 GHz, respectively). Flux, band-pass, and phase calibrators were observed following the standard ALMA calibration procedure; VHS J1256$-$0547 served as band pass and flux calibrator, while J1305$-$1033 was used as phase calibrator.

The calibration of the ALMA data followed the standard ALMA Quality Assurance procedure for Cycle 6 using the calibration pipeline 42254 (ALMA pipeline team[^5]) based on the CASA data analysis package version 5.4.$-$70 (McMullin et al. 2007). The calibrated data were then imaged with the *tclean* task of the same CASA package in mfs mode, that is, combining all spectral channels into one image. VHS J1256$-$1257 data were imaged as a single field with a pixel size of 0.16$''$ and natural weighting in order to optimize the point-source sensitivity. No significant sources were found in the final image, resulting in an rms noise in the central region of 0.02 mJy beam$^{-1}$ (1-$\sigma$).

The same NOEMA and ALMA data of VHS J1256$-$1257 were presented in (cite: Climent2022), where the peculiar emission of the primary component was examined in detail. Here, we focus on the very low-mass companions VHS J1256$-$1257 b and G 196-3 B. To complement the NOEMA and ALMA data of VHS J1256$-$1257 b, we also used the *Karl G. Jansky* Very Large Array (VLA) data at 6 GHz and 33 GHz (5 and 0.9 cm) of (cite: Climent2022). While the (unresolved) primary component was clearly detected at both frequencies, the companion VHS J1256$-$1257 b remained below the sensitivity of the final VLA images with a 1-$\sigma$ rms noise of 0.004 and 0.010 mJy beam$^{-1}$ at 6 GHz and 33 GHz.

# Dusty disk mass upper limits

Neither VHS J1256$-$1257 b nor G 196-3 B are detected at the NOEMA 1.3-mm band. In addition, VHS J1256$-$1257 b remains undetected at the shorter ALMA and longer VLA wavelengths. There is no thermal emission detectable at the depth of our sub-mm, mm, and cm observations that may robustly confirm the presence of surrounding disks. We built the spectral energy distributions (SEDs) of both targets by adopting the flux upper limits with a 3-$\sigma$ confidence for all NOEMA, ALMA and VLA data. To complete the optical through mid-infrared wavelengths, we compiled all available photometry and spectroscopy from the literature (see references in (cite: ZapateroOsorio2010; Gauza2015; Guirado2018; Climent2022)). Figure [1](#fig:SEDs) shows the final SEDs.

To compute the mass upper limits on any hypothetical dusty disk surrounding VHS J1256$-$1257 b and G 196-3 B, we used the following equation (cite: Beckwith1990; Ricci2017), which is valid for optically-thin, gas-depleted disks (i.e., we assumed that very little gas is left by the ages of our targets): $$\begin{equation}
\label{Md}
  M_{\rm dust} = \frac{d^2F_{\nu}}{B_{\nu}(T_{\rm d})\kappa_{\nu}},
    
\end{equation}$$ where $d$ is the distance to the source, $B_{\nu}(T_{\rm d})$ is the Planck function evaluated at the characteristic temperature of the emitting dust ($T_{\rm d}$), and $F_{\nu}$ is the continuum flux density at the given frequency $\nu$. The wavelength-dependent opacity $\kappa_{\nu}$ was calculated for the NOEMA and ALMA data using the code `O`pacityTool available through the Project Diana[^6] introduced by (cite: 2016A&A...586A.103W) and for the default dust parameters therein[^7], except for the dust particles size distribution that we used for the range from 0.1 to 100 $\mu$m. For the VLA wavelengths, we used the extrapolation of the (cite: Beckwith1990) opacities to longer wavelengths[^8]. $\kappa_{\nu}$ suffers from a large uncertainty since it depends not only on the dust physical properties (e.g. (cite: Semenov2003; 2016A&A...586A.103W)) but on the physical processes happening inside the disk as well (cite: Isella2014; Wu2022).

The temperature of the dust was evaluated using the relation of (cite: vanderPlas2016): $T_{\rm d} = a\: (L_{\ast}/L_{\odot})^{b}$, where $L_{\ast}/L_{\odot}$ is the bolometric luminosity of the disk-host source in solar units, and $a$ and $b$ are coefficients dependent on the disk size[^9]. As in (cite: Shabram_2013) and (cite: Rab2019), for our targets, we assumed the disk outer radius ($R_{\rm d}$) as that given by 1/3 of the Hill sphere radius[^10]: $$\begin{equation}
\label{Rd}
  R_{\rm {Hill}} = r \left(\frac{1}{3}\frac{m}{M + m}\right)^{1/3}.
\end{equation}$$ where $m$ and $M$ correspond to the masses of the substellar companion and the primary, and $r$ stands for their orbital separation.

We made the general assumption that disk-host companions at separations larger than 220 au from their primaries are far enough and the disk heating from the companions is dominating over the hitting induced by the brighter primaries (i.e companion can be considered as isolated object). G 196-3 B falls in this category, but VHS J1256$-$1257 b lies closer to its primary. For this "close" companion, we computed the characteristic dust temperature assuming $T^{*4}_{d} = T_d^4 + T_{ir}^4$, where $T_{ir}$ is a temperature evaluated from the heat balance equation between the host source and the dust, roughly assuming that the distance to the dust equals to the separation of the companion and that there is no disk material in between them.

For VHS J1256$-$1257 b and G 196-3 B, we inferred sizes of the disks of $R_{d\:max}  \sim$18 and $\sim$30 au, respectively. These values are provided in Tables [1](#tab:properties_literature) and [2](#tab:properties_computed) together with the characteristic cold temperatures of the dusty disks. To determine the mass upper limits on the putative disks around our targets, we used the observations providing the most constraining results: the NOEMA datum for G 196-3 B and the ALMA datum for VHS J1256$-$1257 b. The spectral energy distributions of the cold disks containing the computed maximum dust masses are illustrated in Fig. [1](#fig:SEDs); the maximum mass values are listed in Table [2](#tab:properties_computed) in units of the Earth mass.

# Discussion

## Comparison to other substellar companions

We put our observations and results in the context of other substellar companions of similar mass with available long-wavelength observations. Over the past few years, a number of millimeter and sub-millimeter observations targeting the circumplanetary or debris disks ended-up with mostly non detections (cite: Booth2016; Wu2017; Ricci2017; Su2017; Perez2019; Matra2019; Pineda2019; Wu2020). Only two circumplanetary disks have been confirmed around the substellar companions PDS 70 c and SR 12 c (cite: Benisty2021; Wu2022). Table [1](#tab:properties_literature) lists all companions with masses smaller than $\sim$20 M$_{\rm Jup}$ that have been scrutinized for their cold disks using NOEMA, VLA and/or ALMA observations and for which only flux density upper limits are available. Their ages oscillate between 1 and a few hundred Myr. We compiled the mass determinations of each source from the literature and show the the most likely values in Table [1](#tab:properties_literature). $\beta$ Pic b has a dynamical mass derived by (cite: Lacour2021). The companion PZ Tel B was first published as a 3.2–24.4 M$_{\rm Jup}$ companion by (cite: schmidt2014). Its mass was later revised to 38–72 M$_{\rm Jup}$ by (cite: maire2016), which is the value we employed in our work.

Then, we computed dust mass upper limits for all objects in Table [2](#tab:properties_computed) following the procedure described in Section [4](#sec:upperLimits). Excluded from Tables [1](#tab:properties_literature) and [2](#tab:properties_computed) are LkCa15 b and HD 100546 b presented in (cite: Ricci2017) and (cite: Pineda2019), because their substellar mass and luminosity parameters are very uncertain. Moreover, the existence of the companions is questioned in the literature. In the case of LkCa15 b, (cite: Currie2019) claimed that all previously suspected planetary companions of the LkCa15 system (LkCa15 b,c,d) are most likely signals from the disk inner structure of the primary based on new near-infrared direct imaging/spectroscopy collected with Subaru Coronagraphic Extreme Adaptive Optics system coupled with Coronagraphic High Angular Resolution Imaging Spectrograph (CHARIS) integral field spectrograph and multi-epoch thermal infrared imaging from Keck/NIRC2. Also excluded is the V1400 Cen system (cite: Mamajek2012; Kenworthy2015; Kenworthy2020) because of the unconstrained mass of the companion (see also the Introduction section). Some of our mass upper limit estimates deviate from the literature values. GQ Lup B and GSC 6214-210 B’s maximum dust masses differ from the determinations presented in (cite: Ricci2017) because we are using new ALMA data published in (cite: Wu2017). The limits derived for PZ Tel B, 51 Eri b, AB Pic b, $\kappa$ And b, HR8799 b,c,d,e, $\beta$ Pic b, and HD 95086 b are also different by one order of magnitude when compared to those derived by (cite: Perez2019). The main reason is the radiative transfer model (RADMC-3D) used by (cite: Perez2019) that gives mostly lower dust temperatures by $\sim$30 K for disk sizes in the interval 1–10 au (for more details see Section 3 of (cite: Perez2019)).

![image](upperLimits_2023_Mz_Mj_Testi_debris_all_20K.eps) ![image](upperLimits_2023_Mz_Mj_Testi_debris_all_20K_Mc.eps)

In support of the hypothesis that many of these objects can host a surrounding disk, (cite: vanHolstein2021) recently obtained linear polarimetric images in the near-infrared for 20 known directly imaged exoplanets and brown dwarf companions, 11 of which are included in Table [1](#tab:properties_literature): PZ Tel B, AB Pic b, GSC 6214-2010 B, GQ Lup B, HR 8799 (b,c,d,e), 1 RXS1609 b, DH Tau B, and $\beta$ Pic b. They reported the first detection of linear polarization from substellar companions, with a polarization degree of several tenths of a percent for DH Tau B and GSC 6214-210 B. Given the very young ages of the two objects, the authors assumed that the polarization most likely originates from circumsubstellar protoplanetary disks. This interpretation also agrees with that of (cite: milespaez2017), where two free-floating Taurus objects of late-M spectral types and brown dwarf masses were reported to have significant near-infrared linear polarization, in one case clearly correlated with mid-infrared flux excesses, thus consistent with the presence of a surrounding disk. For the rest of the (cite: vanHolstein2021) sample, the authors reported a null polarimetric detection but it does not necessarily mean an absence of disk. Actually, (cite: Christiaens2019) announced evidence for a disk around PDS 70 b (included in the target list of (cite: vanHolstein2021)) based on near-infrared spectroscopic observations.

Figure [2](#fig:upperLimits_comanions) shows our computed upper limits on the disk dust mass as a function of the mass of the companion, which is the disk-host source. The left panel depicts the mass upper limits as measured while the right panel illustrates the mass upper limits normalized to the mass of the central companion to break any dependence of the disk dust mass on the mass or luminosity of the disk-host object. Both upper limits and the two solid detections are depicted together. As a reference, the masses of the rings of Saturn (cite: Zakhozhay2017), the Moon and total mass of the Jovian Moons (cite: Ricci2017) are also included in the left panel. Our targets are shown with dust mass upper limits of 0.014 M$_{\rm Earth}$ (G 196-3 B) and 0.005 M$_{\rm Earth}$ (VHS J1256$-$1257 b). These measurements are of the order of magnitude of the mass of the Moon.

There is a clear observational bias in both panels of Figure [2](#fig:upperLimits_comanions): the "older" objects ($>$10 Myr) have lower disk dust mass upper limits than the very young sources ($\le$10 Myr) because the former are typically located closer and, therefore, observations yield deeper absolute fluxes for them. This is better illustrated in Figure [3](#fig:Md_d_age), where the objects of Table [1](#tab:properties_literature) are depicted as a function of their distance. G 196-3 B, VHS J1256$-$1257 b (our two targets) and $\beta$ Pic b are the closest substellar companions for which an attempt to detect surrounding disks has been made to date. The $\beta$ Pic b observations (cite: Matra2019) are actually quite deep and our dust mass upper limit estimate is about two orders of magnitude more restrictive for $\beta$ Pic b than for our two targets (left panel of Figure [3](#fig:Md_d_age)). Regarding the group of younger objects (typical distance $\ge$ 100 pc), where there are two positive disk detections, both Figures [2](#fig:upperLimits_comanions) and [3](#fig:Md_d_age) indicate that SR 12 c and PDS 70 c may host relatively "bright" disks and that observations have to be at least one order of magnitude deeper to be able to detect similar disks around the other very young brown dwarf companions included in the Figures.

## Comparison to free-floating sources

For a wider view, we also compared what is known for substellar companions to the situation of free-floating brown dwarfs and stars in Figure [4](#fig:upperLimits_all), which shows the protoplanetary disk dust masses and dust mass upper limits using ALMA data provided by (cite: Testi2022) for the following star-forming regions and young star clusters: L1688 (in $\rho$-Ophiuchi), Taurus, Lupus, Corona Australis, Upper Scorpius, and Chameleon I. All of these regions are very young with typical ages below 10–20 Myr. For the computation of the disk dust masses around central objects with masses from substellar to several times the solar mass, (cite: Testi2022) adopted $\kappa_{\nu}$ = 2.3 cm$^{2}$ g$^{-1}$ and a constant $T_{dust}$ = 20 K.

For a proper comparison with the data of (cite: Testi2022), we redid our computations of the disk dust mass upper limits for the substellar companions following the same adoption[^11] (see also (cite: Pascucci2016)). Our new computations (provided in Table [2](#tab:properties_computed)), (cite: Testi2022) determinations, and Saturn’s rings (cite: Zakhozhay2017) are displayed in the upper panel of Figure [4](#fig:upperLimits_all), while the bottom panel shows the relative disk dust masses (disk mass over the mass of the central source) as a function of the disk-host object. The ages of the various objects are color coded in Figure [4](#fig:upperLimits_all). There are significant differences between our computations of disk dust mass upper limits and those obtained by adopting a constant dust temperature. As an example, our VHS J1256$-$1257 b’s estimate is 15 times larger than the one from the disk constant temperature. However, this difference is still within the large dispersion for a given mass of the central object as seen in Figure [4](#fig:upperLimits_all).

Similarly to stars, the detection of disks surrounding substellar objects appears to drastically depend on the systems age. The only sub-mm and mm detections in the substellar regime (OTS44, SR 12 c and PDS 70 c) in Figure [4](#fig:upperLimits_all) correspond to sources with an age of less than 10 Myr, while there is no single disk detection around brown dwarfs with older ages despite the observations are more sensitive (due to the closer distances). This could be explained by the natural evolution of the disks, which transists from protoplanetary to the debris phase. All three OTS44, SR 12 c and PDS 70 c likely host protoplanetary disks in which gas accretion still takes place on the central objects.

As already pointed out by many groups, the mass of the protoplanetary disks linearly depends on the mass of the central object including the substellar regime. This implies that the disks around brown dwarfs are scaled-down versions of the stellar disks. As illustrated in the bottom panel of Figure [4](#fig:upperLimits_all), for very young objects the relative disk dust masses appear to be constant for all stellar and substellar mass regimes, although with a relative large dispersion of about one order of magnitude. This implies that if planets form around substellar objects, the amount of dust mass available for planetary formation is small. Only rocky planets like Earth or smaller could form unless more massive planets are raised in earlier stages ($<$1 Myr) when the substellar disks might have been more massive.

Because of the age of G 196-3 B and VHS J1256$-$1257 b, we would expect them to host debris disks rather than protoplanetary disks. For completeness, we also included in both panels of Figure [4](#fig:upperLimits_all) ALMA detections of circumstellar debris disks from (cite: Sepulveda2019), (cite: Marino2020), and Matrà (2022, in preparation), and dust mass upper limits determined from the (cite: Sullivan2022) observations of Pleiades stellar members. All of these objects have typical ages greater than 20 Myr (the Pleiades age is 115 Myr, (cite: Stauffer1998; Sullivan2022)). To determine the masses of all the central objects with detected debris disks (presented in (cite: Sepulveda2019) and Matrà 2022, in preparation), we used a simple mass—luminosity relation $M_{\ast} = L_{\ast}^{0.25}$ (where both parameters are in solar units) applicable to the masses \> 0.43 M$_{\odot}$ (cite: Duric2003)[^12]. For consistency, we computed the dust masses and dust mass upper limits for all debris disks ((cite: Sepulveda2019; Marino2020; Sullivan2022), Matrà 2022, in preparation) following the approach of (cite: Testi2022).

In both panels of Figure [4](#fig:upperLimits_all), stars with debris disks are located below the stars with protoplanetary disks. As expected, the dust mass of debris disks is significantly smaller than that of protoplanetary disks for a given central source. Interestingly, the sequence described by the debris disks appears to be parallel to that of the protoplanetary disks for the central object mass interval between $\sim$0.5 and $\sim$2 M$_\odot$. Under the assumption that disks around brown dwarfs and planets of different ages behave similarly, that is, they scale down with the mass of the central body, the extrapolation of the debris disk stellar sequence into the substellar domain using the same decreasing slope observed for protoplanetary disks indicates that sub-mm and mm observations must be at least 100 times deeper than current observations in order to detect the presence of substellar debris disks surrounding moderately young brown dwarfs and planets. According to the bottom panel of Figure [4](#fig:upperLimits_all), only the ALMA observations of VHS J1256–1257 b marginally comply with this requirement, yet at the upper part of the large dispersion of the predicted debris disks dust masses. That is, current observations have largely missed substellar debris disks other than ruling out their existence. These observations are indeed challenging requiring tens to hundreds of hours of observations with ALMA. Future interferometers, as SKA1-MID at high frequencies (Band 6, 15–50 GHz), with the added benefit of improved sensitivity and spatial resolution, could provide signicant contributions to the debris disks of these objects (cite: Conway2020).

# Conclusions

In this paper we presented the results of NOEMA (1.3 mm) observations of G 96-3 B (15.3$^{+7.7}_{-2.7}$ M$_{\rm Jup}$), and ALMA (0.87 mm), NOEMA (1.3 mm) and VLA (0.9 cm and 5 cm) observations of VHS J1256$-$1257 b (20.5$^{+6.0}_{-4.5}$ $M_{\rm Jup}$), both of which are low-mass companions moving around more massive objects at relatively wide orbits. We reported non-detections for all of our observations. Based on the $rms$ noise of the millimeter observations, we determined the 3-$\sigma$ upper limits on the dust masses of any potential debris disks, and we compared them to the values (mostly obtained using ALMA observations) of other substellar companions (including brown dwarfs and planets) of different ages. Only three protoplanetary disks surrounding brown dwarfs have been detected at mm wavelengths in the literature: two around the companions PDS 70 c and SR 12 c (cite: Isella2019; Benisty2021; Wu2022), and one around the free-floating brown dwarf OTS44 (cite: Bayo2017) despite the fact that there are at least 30 brown dwarfs and planetary mass objects with strong evidence of hosting protoplanetary disks. This demonstrates the remarkable low luminosity of these circumbsubstellar disks, which likely become much fainter when they evolve into debris disks. Our observations of G 96-3 B and VHS J1256$-$1257 b add up to the list of brown dwarf and planetary companions with non-detected debris disks. Assuming that debris disks scale down with the mass of the central bodies in a similar way as their protoplanetary predecessors do, we estimate that mm observations 100 times deeper are required for positive detections, which would open a new door for the study of the potential of these low-mass objects for generating their own moons.

# Acknowledgements

The authors are indebted to Luca Ricci, Sebastian Marino and Paola Pinilla for helpful discussions and feedback. The authors kindly thank Leonardo Tesi and Luca Matrà for providing the machine-ready tables of the protoplanetary and debris disks parameters, respectively. This work is based on observations carried out under project number W18BP \[001-002\] with the IRAM NOEMA Interferometer \[30m telescope\]. IRAM is supported by INSU/CNRS (France), MPG (Germany) and IGN (Spain). OZ acknowledges support within the framework of the Ukraine aid package for individual grants of the Max-Planck Society 2022. MRZO acknowledges financial support from the Spanish Ministery for Science and Innovation through project PID2019-109522GB-C51. VB and NL acknowledge financial support from the Agencia Estatal de Investigación del Ministerio de Ciencia e Innovación (AEI-MCINN) under grant PID2019-109522GB-C53. BG is supported by the Polish National Science Center (NCN) under SONATA grant No. 2021/43/D/ST9/01940. JBC and JCG were supported by projects PID2020-117404GB-C22, funded by MCIN/AEI, PROMETEO/2020-080, funded by the Generalitat Valenciana, and by the Astrophysics and High Energy Physics programme by MCIN, with funding from European Union NextGenerationEU (PRTR-C17.I1) and the Generalitat Valenciana through grant ASFAE/2022/018. MPT acknowledges financial support through grants CEX2021-001131-S, PID2020-117404GB-C21 and PID2020-114461GB-I00, funded by the Spanish CIN/AEI/10.13039/501100011033. We also wish to thank the anonymous referee for constructive criticism that helped to improve the clarity of the paper.

110 natexlab

(ref: Alcala2008) Alcalá, J. M., Spezzi, L., Chapman, N., et al. 2008, ApJ, 676, 427

(ref: Allard2003) Allard, F., Guillot, T., Ludwig, H.-G., et al. 2003, in Brown Dwarfs, ed. E. Martı́n, Vol. 211, 325

(ref: Allard2012) Allard, F., Homeier, D., & Freytag, B. 2012, Philosophical Transactions of the Royal Society of London Series A, 370, 2765

(ref: Allers2007) Allers, K. N., Jaffe, D. T., Luhman, K. L., et al. 2007, ApJ, 657, 511

(ref: Alves2013) Alves de Oliveira, C., Ábrahám, P., Marton, G., et al. 2013, A&A, 559, A126

(ref: Apai2005) Apai, D., Pascucci, I., Bouwman, J., et al. 2005, Science, 310, 834

(ref: 1998A&A...337..403B) Baraffe, I., Chabrier, G., Allard, F., & Hauschildt, P. H. 1998, A&A, 337, 403

(ref: 2003A&A...402..701B) Baraffe, I., Chabrier, G., Barman, T. S., Allard, F., & Hauschildt, P. H. 2003, A&A, 402, 701

(ref: Barrado2007) Barrado y Navascués, D., Stauffer, J. R., Morales-Calderón, M., et al. 2007, ApJ, 664, 481

(ref: Bayo2017) Bayo, A., Joergens, V., Liu, Y., et al. 2017, ApJL, 841, L11

(ref: Beckwith1990) Beckwith, S. V. W., Sargent, A. I., Chini, R. S., & Guesten, R. 1990, AJ, 99, 924

(ref: Benisty2021) Benisty, M., Bae, J., Facchini, S., et al. 2021, ApJL, 916, L2

(ref: Booth2016) Booth, M., Jordán, A., Casassus, S., et al. 2016, MNRAS, 460, L10

(ref: Bouy2007) Bouy, H., Huélamo, N., Martı́n, E. L., et al. 2007, A&A, 463, 641

(ref: Bowler2015) Bowler, B. P., Andrews, S. M., Kraus, A. L., et al. 2015, ApJL, 805, L17

(ref: Bowler2020) Bowler, B. P., Zhou, Y., Morley, C. V., et al. 2020, ApJL, 893, L30

(ref: Brandt2021) Brandt, G. M., Brandt, T. D., Dupuy, T. J., Li, Y., & Michalik, D. 2021, AJ, 161, 179

(ref: Caballero2007) Caballero, J. A., Béjar, V. J. S., Rebolo, R., et al. 2007, A&A, 470, 903

(ref: 2011SoPh..268..255C) Caffau, E., Ludwig, H. G., Steffen, M., Freytag, B., & Bonifacio, P. 2011, Sol. Phys., 268, 255

(ref: Chabrier2000) Chabrier, G., Baraffe, I., Allard, F., & Hauschildt, P. 2000, ApJ, 542, 464

(ref: Chilcote2017) Chilcote, J., Pueyo, L., De Rosa, R. J., et al. 2017, AJ, 153, 182

(ref: Christiaens2019) Christiaens, V., Cantalloube, F., Casassus, S., et al. 2019, ApJL, 877, L33

(ref: Climent2022) Climent, J. B., Guirado, J. C., Zapatero Osorio, M. R., et al. 2022, A&A, 660, A65

(ref: Conway2020) Conway, J., Beswick, R., Bourke, T., et al. 2020, SKA Memorandum 20-21, 131

(ref: Currie2018) Currie, T., Brandt, T. D., Uyama, T., et al. 2018, AJ, 156, 291

(ref: Currie2019) Currie, T., Marois, C., Cieza, L., et al. 2019, ApJL, 877, L3

(ref: Damjanov2007) Damjanov, I., Jayawardhana, R., Scholz, A., et al. 2007, ApJ, 670, 1337

(ref: DaRosa2020) De Rosa, R. J., Nielsen, E. L., Wang, J. J., et al. 2020, AJ, 159, 1

(ref: Dupuy2022) Dupuy, T. J., Brandt, G. M., & Brandt, T. D. 2022, MNRAS, 509, 4411

(ref: Dupuy2023) Dupuy, T. J., Liu, M. C., Evans, E. L., et al. 2023, MNRAS, 519, 1688

(ref: Dupuy2020) Dupuy, T. J., Liu, M. C., Magnier, E. A., et al. 2020, Research Notes of the American Astronomical Society, 4, 54

(ref: Duric2003) Duric, N. 2003, Advanced Astrophysics

(ref: GaiaCollaboration2016) Gaia Collaboration, Brown, A. G. A., Vallenari, A., et al. 2016, A&A, 595, A2

(ref: Gauza2015) Gauza, B., Béjar, V. J. S., Pérez-Garrido, A., et al. 2015, ApJ, 804, 96

(ref: Guieu2007) Guieu, S., Pinte, C., Monin, J. L., et al. 2007, A&A, 465, 855

(ref: Guirado2018) Guirado, J. C., Azulay, R., Gauza, B., et al. 2018, A&A, 610, A23

(ref: Hernandez2007) Hernández, J., Hartmann, L., Megeath, T., et al. 2007, ApJ, 662, 1067

(ref: hogbom2003) Högbom, J. A. 2003, in Astronomical Society of the Pacific Conference Series, Vol. 300, Radio Astronomy at the Fringe, ed. J. A. Zensus, M. H. Cohen, & E. Ros, 17

(ref: Isella2019) Isella, A., Benisty, M., Teague, R., et al. 2019, ApJL, 879, L25

(ref: Isella2014) Isella, A., Chandler, C. J., Carpenter, J. M., Pérez, L. M., & Ricci, L. 2014, ApJ, 788, 129

(ref: Jaya2003) Jayawardhana, R., Ardila, D. R., Stelzer, B., & Haisch, Karl E., J. 2003, AJ, 126, 1515

(ref: Jaya2002) Jayawardhana, R., Mohanty, S., & Basri, G. 2002, ApJL, 578, L141

(ref: Kenworthy2020) Kenworthy, M. A., Klaassen, P. D., Min, M., et al. 2020, A&A, 633, A115

(ref: Kenworthy2015) Kenworthy, M. A. & Mamajek, E. E. 2015, ApJ, 800, 126

(ref: Kirkpatrick2001) Kirkpatrick, J. D., Dahn, C. C., Monet, D. G., et al. 2001, AJ, 121, 3235

(ref: Lacour2021) Lacour, S., Wang, J. J., Rodet, L., et al. 2021, A&A, 654, L2

(ref: Lindegren2021) Lindegren, L., Klioner, S. A., Hernández, J., et al. 2021, A&A, 649, A2

(ref: Lodieu2013) Lodieu, N., Dobbie, P. D., Cross, N. J. G., et al. 2013, MNRAS, 435, 2474

(ref: Luhman2005) Luhman, K. L., Adame, L., D’Alessio, P., et al. 2005, ApJL, 635, L93

(ref: Luhman2010) Luhman, K. L., Allen, P. R., Espaillat, C., Hartmann, L., & Calvet, N. 2010, ApJS, 186, 111

(ref: Luhman2012) Luhman, K. L. & Mamajek, E. E. 2012, ApJ, 758, 31

(ref: Luhman2006) Luhman, K. L., Whitney, B. A., Meade, M. R., et al. 2006, ApJ, 647, 1180

(ref: MacGregor2017) MacGregor, M. A., Wilner, D. J., Czekala, I., et al. 2017, ApJ, 835, 17

(ref: maire2016) Maire, A. L., Bonnefoy, M., Ginski, C., et al. 2016, A&A, 587, A56

(ref: Maire2018) Maire, A. L., Rodet, L., Lazzoni, C., et al. 2018, A&A, 615, A177

(ref: Mamajek2012) Mamajek, E. E., Quillen, A. C., Pecaut, M. J., et al. 2012, AJ, 143, 72

(ref: Marino2020) Marino, S., Zurlo, A., Faramaz, V., et al. 2020, MNRAS, 498, 1319

(ref: Martin1999) Martı́n, E. L., Delfosse, X., Basri, G., et al. 1999, AJ, 118, 2466

(ref: Matra2019) Matrà, L., Wyatt, M. C., Wilner, D. J., et al. 2019, AJ, 157, 135

(ref: McGovern2004) McGovern, M. R., Kirkpatrick, J. D., McLean, I. S., et al. 2004, ApJ, 600, 1020

(ref: McLean2007) McLean, I. S., Prato, L., McGovern, M. R., et al. 2007, ApJ, 658, 1217

(ref: Miles2022) Miles, B. & High Contrast Imaging of Exoplanets JWST ERS Team. 2023, in American Astronomical Society Meeting Abstracts, Vol. 55, American Astronomical Society Meeting Abstracts, 345.03

(ref: milespaez2017) Miles-Páez, P. A., Zapatero Osorio, M. R., Pallé, E., & Peña Ramı́rez, K. 2017, MNRAS, 466, 3184

(ref: Miret-Roig2018) Miret-Roig, N., Antoja, T., Romero-Gómez, M., & Figueras, F. 2018, A&A, 615, A51

(ref: Mohanty2005) Mohanty, S., Jayawardhana, R., & Basri, G. 2005, ApJ, 626, 498

(ref: Muzerolle2003) Muzerolle, J., Hillenbrand, L., Calvet, N., Briceño, C., & Hartmann, L. 2003, ApJ, 592, 266

(ref: Muzerolle2005) Muzerolle, J., Luhman, K. L., Briceño, C., Hartmann, L., & Calvet, N. 2005, ApJ, 625, 906

(ref: Natta2001) Natta, A. & Testi, L. 2001, A&A, 376, L22

(ref: Natta2004) Natta, A., Testi, L., Muzerolle, J., et al. 2004, A&A, 424, 603

(ref: Neuhauser2012) Neuhäuser, R. & Schmidt, T. 2012, in Topics in Adaptive Optics, ed. R. K. Tyson (Rijeka: IntechOpen)

(ref: Pascucci2003) Pascucci, I., Apai, D., Henning, T., & Dullemond, C. P. 2003, ApJL, 590, L111

(ref: Pascucci2016) Pascucci, I., Testi, L., Herczeg, G. J., et al. 2016, ApJ, 831, 125

(ref: Pena2012) Peña Ramı́rez, K., Béjar, V. J. S., Zapatero Osorio, M. R., Petr-Gotzens, M. G., & Martı́n, E. L. 2012, ApJ, 754, 30

(ref: Perez2019) Pérez, S., Marino, S., Casassus, S., et al. 2019, MNRAS, 488, 1005

(ref: Petrus2023) Petrus, S., Chauvin, G., Bonnefoy, M., et al. 2023, A&A, 670, L9

(ref: Pineda2019) Pineda, J. E., Szulágyi, J., Quanz, S. P., et al. 2019, ApJ, 871, 48

(ref: Rab2019) Rab, C., Kamp, I., Ginski, C., et al. 2019, A&A, 624, A16

(ref: Rebolo1998) Rebolo, R., Osorio, M. R. Z., Madruga, S., et al. 1998, Science, 282, 1309

(ref: Riaz2008) Riaz, B. & Gizis, J. E. 2008, ApJ, 681, 1584

(ref: Riaz2014) Riaz, B. & Kennedy, G. M. 2014, MNRAS, 442, 3065

(ref: Riaz2009) Riaz, B., Lodieu, N., & Gizis, J. E. 2009, ApJ, 705, 1173

(ref: Riaz2019) Riaz, B., Machida, M. N., & Stamatellos, D. 2019, MNRAS, 486, 4114

(ref: Ricci2017) Ricci, L., Cazzoletti, P., Czekala, I., et al. 2017, AJ, 154, 24

(ref: Ricci2014) Ricci, L., Testi, L., Natta, A., et al. 2014, ApJ, 791, 20

(ref: Rilinger2021) Rilinger, A. M. & Espaillat, C. C. 2021, ApJ, 921, 182

(ref: schmidt2014) Schmidt, T. O. B., Mugrauer, M., Neuhäuser, R., et al. 2014, A&A, 566, A85

(ref: Scholz2008) Scholz, A. & Jayawardhana, R. 2008, ApJL, 672, L49

(ref: Scholz2007) Scholz, A., Jayawardhana, R., Wood, K., et al. 2007, ApJ, 660, 1517

(ref: Semenov2003) Semenov, D., Henning, T., Helling, C., Ilgner, M., & Sedlmayr, E. 2003, A&A, 410, 611

(ref: Sepulveda2019) Sepulveda, A. G., Matrà, L., Kennedy, G. M., et al. 2019, ApJ, 881, 84

(ref: Shabram_2013) Shabram, M. & Boley, A. C. 2013, The Astrophysical Journal, 767, 63

(ref: Stauffer1998) Stauffer, J. R., Schultz, G., & Kirkpatrick, J. D. 1998, ApJL, 499, L199

(ref: Stone2016) Stone, J. M., Skemer, A. J., Kratter, K. M., et al. 2016, ApJL, 818, L12

(ref: Su2017) Su, K. Y. L., MacGregor, M. A., Booth, M., et al. 2017, AJ, 154, 225

(ref: Sullivan2022) Sullivan, D., Wilner, D. J., Matrà, L., et al. 2022, AJ, 164, 100

(ref: Testi2022) Testi, L., Natta, A., Manara, C. F., et al. 2022, A&A, 663, A98

(ref: Testi2016) Testi, L., Natta, A., Scholz, A., et al. 2016, A&A, 593, A111

(ref: vanderPlas2016) van der Plas, G., Ménard, F., Ward-Duong, K., et al. 2016, ApJ, 819, 102

(ref: vanHolstein2021) van Holstein, R. G., Stolker, T., Jensen-Clem, R., et al. 2021, A&A, 647, A21

(ref: 2016A&A...586A.103W) Woitke, P., Min, M., Pinte, C., et al. 2016, A&A, 586, A103

(ref: Wu2020) Wu, Y.-L., Bowler, B. P., Sheehan, P. D., et al. 2020, AJ, 159, 229

(ref: Wu2022) Wu, Y.-L., Bowler, B. P., Sheehan, P. D., et al. 2022, ApJL, 930, L3

(ref: Wu2017) Wu, Y.-L., Close, L. M., Eisner, J. A., & Sheehan, P. D. 2017, AJ, 154, 234

(ref: Wyatt2015) Wyatt, M. C., Panić, O., Kennedy, G. M., & Matrà, L. 2015, Ap&SS, 357, 103

(ref: Zakhozhay2017) Zakhozhay, O. V., Zapatero Osorio, M. R., Béjar, V. J. S., & Boehler, Y. 2017, MNRAS, 464, 1108

(ref: ZapateroOsorio2014) Zapatero Osorio, M. R., Béjar, V. J. S., Miles-Páez, P. A., et al. 2014, A&A, 568, A6

(ref: ZapateroOsorio2017) Zapatero Osorio, M. R., Béjar, V. J. S., & Peña Ramı́rez, K. 2017, ApJ, 842, 65

(ref: ZapateroOsorio2007) Zapatero Osorio, M. R., Caballero, J. A., Béjar, V. J. S., et al. 2007, A&A, 472, L9

(ref: ZapateroOsorio2010) Zapatero Osorio, M. R., Rebolo, R., Bihain, G., et al. 2010, ApJ, 715, 1408

(ref: Zhou2022) Zhou, Y., Bowler, B. P., Apai, D., et al. 2022, AJ, 164, 239

| Name | $d$$^{a}$, pc | age, Myr | $L_{\rm c}$$^{a}$, L$_{\odot}\times10^{-3}$ | $M_{\rm c}$, M$_{\rm Jup}$ | $a$, AU | $F_{\nu}$ (3$\sigma$), mJy | $F_{\nu}$ observed with | Refs.$^{b}$ |
|:---|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:---|
| G 196-3 B | 21.81$\pm0.01$ | 50–100 | 0.0927$\pm0.0001$ | 15.3$^{+7.7}_{-2.7}$ | $\sim$350$^{c}$ | 0.108 | NOEMA (1.3 mm) | this work |
| VHS J1256$-$1257 b | 21.15$\pm0.21$ | 150–300 | 0.027$\pm0.0001$$^{d}$ | 20.5$^{+6.0}_{-4.5}$ | $\sim$170$^{c}$ | 0.153 | NOEMA (1.3 mm) | this work |
|  |  |  |  |  |  | 0.060 | ALMA 0.87 mm) | this work |
|  |  |  |  |  |  | 0.030 | VLA (0.9 cm) | this work$^{e}$, 1 |
|  |  |  |  |  |  | 0.009 | VLA (3 cm) | this work$^{e}$, 1, 2 |
|  |  |  |  |  |  | 0.012 | VLA (5 cm) | this work$^{e}$, 1 |
|  |  |  |  |  |  | 0.024 | VLA (21.4 cm) | this work$^{e}$, 1, 2 |
| CT Cha B | 190.0$^{+0.4}_{-0.5}$ | 1–3 | 2.38 | 17$\pm$5 | $\sim$511 | 0.156 | ALMA(0.88 mm) | 3 |
| 1 RXS1609 b | 138.0$^{+0.4}_{-0.3}$ | 5–14 | 0.41 | 12$\pm$2 | $\sim$309 | 0.135 | ALMA(0.88 mm) | 3 |
| ROXs 12 B | 138.6$^{+0.3}_{-0.4}$ | 4–10 | 1.75 | 18$\pm$3 | $\sim$243 | 0.213 | ALMA(0.88 mm) | 3 |
| ROXs 42B b | 146.4$^{+0.7}_{-0.6}$ | 1–3 | 0.83 | 9$\pm$2 | $\sim$168 | 0.129 | ALMA(0.88 mm) | 3 |
| DH Tau B | 133.4$^{+0.6}_{-0.4}$ | 1–3 | 1.82 | 14$\pm$3 | $\sim$317 | 0.123 | ALMA(0.88 mm) | 3 |
| FU Tau B | 128.6$^{+1.4}_{-1.2}$ | 1–3 | 3.13 | 20$\pm$4 | $\sim$747 | 0.117 | ALMA(0.88 mm) | 3 |
| PZ Tel B | 47.25$\pm$0.05 | 20–25 | 2.6$\pm$0.6 | 38–72 | $\sim$23 | 0.084 | ALMA(1.3 mm) | 4, 5, 6 |
| 51 Eri b | 29.91$\pm$0.07 | 20–25 | 3$^{+2}_{-1}\times$10$^{-3}$ | 2.5–4.5 | 11.1$^{+4.2}_{-1.3}$ | 0.081 | ALMA(1.3 mm) | 4, 7, 8 |
| AB Pic b | 50.14$\pm$0.03 | 30–55 | 0.22$^{+0.05}_{-0.04}$ | 11–18 | $\sim$252 | 0.078 | ALMA(1.3 mm) | 4, 9 |
| $\kappa$ And b | 52.0$\pm$0.5 | 40–50 | 0.17$^{+0.02}_{-0.02}$ | 13$^{+12}_{-2}$ | $\sim$55 | 0.18 | ALMA(1.3 mm) | 4, 10 |
| $\beta$ Pic b | 19.63$^{+0.06}_{- 0.05}$ | 20–25 | 0.18$^{+0.01}_{-0.01}$ | 9.3$^{+2.6}_{-2.5}$ | 10.26$^{+0.1}_{-0.1}$ | 0.036 | ALMA(1.3 mm) | 4, 11-13 |
| GSC 6214-2010 B | 108.78$\pm$0.25 | 5–14 | 0.447 | 15$\pm$2 | 320 | 0.09 | ALMA(0.88 mm) | 14, 15 |
| GQ Lup B | 154.1$\pm$0.7 | 3$\pm$2 | 3.306 | 10–36 | $\sim$220 | 0.12 | ALMA(0.88 mm) | 14, 16 |
| HD 95086 b | 86.46${\pm}$0.14 | 17$\pm$4 | 0.017 | 4.4${\pm}$0.8 | 57.2$^{+19.2}_{-7.8}$ | 0.03 | ALMA(1.3 mm) | 4, 17 |
| 2M 1207 b | 64.7$\pm$0.5 | 10$\pm$3 | 0.225 | 5$\pm$2 | $\sim$40 | 0.078 | ALMA(0.89 mm) | 18 |
| HR 8799 b | 40.88$\pm$0.08 | 42$^{+6}_{-4}$ | 0.007 | 5.8 | 70 | 0.048 | ALMA(1.3 mm) | 4, 19 |
| HR 8799 c | 40.88$\pm$0.08 | 42$^{+6}_{-4}$ | 0.013 | 7–9 | 43 | 0.048 | ALMA(1.3 mm) | 4, 19 |
| HR 8799 d | 40.88$\pm$0.08 | 42$^{+6}_{-4}$ | 0.013 | 7–9 | 26 | 0.048 | ALMA(1.3 mm) | 4, 19 |
| HR 8799 e | 40.88$\pm$0.08 | 42$^{+6}_{-4}$ | 0.013 | 7–9 | 15 | 0.048 | ALMA(1.3 mm) | 4, 19 |

: Physical properties and information of mm and sub-mm observations of brown dwarfs/planetary-mass objects with non detected disks.

Table notes:

|  |  |  |  |  |  |
|:---|---:|---:|---:|---:|:---|
| Name | $R_{\rm out}$$^{a}$ | $T_{\rm d}$ | $M_{\rm dust}$$^{b}$ | $M_{\rm dust,20K}$$^{c}$ | $F_{\nu}$$^{d}$ observed with |
|  | (au) | \(K\) | (M$_{\oplus}$) | (M$_{\oplus}$) |  |
| G 196-3 B | 29.5 | 5.3 | 0.014 | 0.0015 | NOEMA (1.3 mm) |
| VHS J1256$-$1257 b | 18.1 | 4.5 | 0.028 | 0.0019 | NOEMA (1.3 mm) |
|  |  |  | 0.005 | 0.00019 | ALMA 0.87 mm) |
|  |  |  | 0.500 | 0.098 | VLA (0.9 cm) |
|  |  |  | 4.889 | 1.06 | VLA (3 cm) |
|  |  |  | 29.535 | 6.5 | VLA (5 cm) |
|  |  |  | 4519.046 | 1015.1 | VLA (21.4 cm) |
| CT Cha B | 32.0 | 10.9 | 0.111 | 0.040 | ALMA(0.88 mm) |
| 1 RXS1609 b | 16.9 | 7.4 | 0.118 | 0.018 | ALMA(0.88 mm) |
| ROXs 12 B | 15.1 | 10.1 | 0.092 | 0.029 | ALMA(0.88 mm) |
| ROXs 42B b | 8.2 | 11.1 | 0.052 | 0.020 | ALMA(0.88 mm) |
| DH Tau B | 21.7 | 11.7 | 0.037 | 0.016 | ALMA(0.88 mm) |
| FU Tau B | 101.0 | 8.7 | 0.060 | 0.014 | ALMA(0.88 mm) |
| PZ Tel B | 2.0 | 60.7 | 0.001 | 0.0053 | ALMA(1.3 mm) |
| 51 Eri b | 0.3 | 128.5 | 3$\times10^{-4}$ | 0.0021 | ALMA(1.3 mm) |
| AB Pic b | 15.0 | 6.4 | 0.035 | 0.0056 | ALMA(1.3 mm) |
| $\kappa$ And b | 2.2 | 113.4 | 0.002 | 0.014 | ALMA(1.3 mm)8 |
| $\beta$ Pic b | 0.4 | 152.1 | 4$\times10^{-5}$ | 0.00039 | ALMA(1.3 mm) |
| GSC 6214-2010 B | 18.5 | 7.5 | 0.047 | 0.0076 | ALMA(0.88 mm) |
| GQ Lup B | 13.9 | 18.9 | 0.022 | 0.020 | ALMA(0.88 mm) |
| HD 95086 b | 1.8 | 60.9 | 0.002 | 0.0064 | ALMA(1.3 mm) |
| 2M 1207 b | 5.1 | 12.1 | 0.005 | 0.0023 | ALMA(0.89 mm) |
| HR 8799 b | 2.5 | 51.2 | 7$\times10^{-4}$ | 0.0023 | ALMA(1.3 mm) |
| HR 8799 c | 1.7 | 65.3 | 6$\times10^{-4}$ | 0.0023 | ALMA(1.3 mm) |
| HR 8799 d | 1.0 | 84.0 | 4$\times10^{-4}$ | 0.0023 | ALMA(1.3 mm) |
| HR 8799 e | 0.6 | 110.6 | 3$\times10^{-4}$ | 0.0023 | ALMA(1.3 mm) |

: Radius and mass upper limits and temperature of potential dusty disks around brown dwarf and planets with non detections.

Table notes: .

# NOEMA and ALMA images for G 196-3 B and VHS J1256-1257 b.

Figure [5](#fig:maps) shows the NOEMA images of G 196-3 B and VHS J1256-1257, and ALMA image of VHS J1256-1257. No circumstellar dust emission is detected from any of these images.

[^1]: The parallax was computed based on the observations obtained on the Canada-France-Hawaii Telescope (CFHT) in the period 2016–2019.

[^2]: <https://www.iram-institute.org/EN/content-page-56-7-56-0-0-0.html>

[^3]: More details about NOEMA can be found here: <https://www.iram.fr/IRAMFR/GILDAS/doc/html/noema-intro-html/noema-intro.html>

[^4]: <http://www.iram.fr/IRAMFR/GILDAS/>

[^5]: ALMA Pipeline Team, 2017, ALMA Science Pipeline User’s Guide, ALMA Doc 6.13

[^6]: <https://diana.iwf.oeaw.ac.at/data-results-downloads/fortran-package/>

[^7]: The default dust parameters in the `O`pacityTool code are the following: dust particles size distribution from 0.005 $\mu m$ to 3000 $\mu m$ with the powerlaw of -3.5, the porosity (so the volume fraction of vacuum) of 0.25, mass and volume fraction of carbonaceous material of 0.13 and 0.15, respectively.

[^8]: $\kappa_{\nu} = 4.9$ cm$^2$/g at $\nu$ = 340 GHz ($\lambda$ = 0.88 mm),\
    $\kappa_{\nu} = 2.3$ cm$^2$/g at $\nu$ = 230 GHz ($\lambda$ = 1.3 mm),\
    $\kappa_{\nu} = 0.33$ cm$^2$/g at $\nu$ = 33 GHz ($\lambda$ = 0.9 cm),\
    $\kappa_{\nu} = 0.10$ cm$^2$/g at $\nu$ = 10 GHz ($\lambda$ = 3 cm),\
    $\kappa_{\nu} = 0.06$ cm$^2$/g at $\nu$ = 6 GHz ($\lambda$ = 5 cm),\
    $\kappa_{\nu} = 0.014$ cm$^2$/g at $\nu$ = 1.4 GHz ($\lambda$ = 21.4 cm)

[^9]: Depending on the disk possible $R_{\rm d}$ we used the following coefficients:\
    for $R_{\rm d}<10$ AU we used \[a,b\] = \[57,0.23\],\
    for $R_{\rm d} = 10-35$ AU: \[a,b\] = \[41,0.22\],\
    for $R_{\rm d} = 40-70$ AU: \[a,b\] = \[25,0.17\],\
    for $R_{\rm d} > 90$ AU: \[a,b\] = \[22,0.16\].

[^10]: The sum in denominator accounts for the fact that in some of the systems the mass of companion is non-negligible compared to the mass of the primary.

[^11]: For PDS 70 c, SR 12 c and OTS44 we also computed their disk masses adopting $T_{dust}$ = 20 K and the equations given in this work, resulting in disk dust masses of 0.007, 0.011 and 0.071 $M_{\rm Earth}$, respectively.

[^12]: $\alpha$ PsA C is the only one object resulted to have the mass smaller than 0.43 M$_{\odot}$, for it we recomputed the mass, using the following relation: $M_{\ast} = (L_{\ast}/0.23)^{1/2.3}$, following the prescription by (cite: Duric2003).

</paper>

## Items to check

```json
[
 {
  "path": "science.targets[0].redshift_or_distance.evidence[0]",
  "value": "21.15+-0.21 pc",
  "failed_quote": "The Gaia Early Data Release 3 (EDR3) (cite: GaiaCollaboration2016; Lindegren2021) provides a distance of 21.15+-0.21 pc for the primary binary component. This is the value we adopted for this paper."
 },
 {
  "path": "science.targets[0].distance_source.evidence[0]",
  "value": "Gaia EDR3 (cite: GaiaCollaboration2016; Lindegren2021)",
  "failed_quote": "The Gaia Early Data Release 3 (EDR3) (cite: GaiaCollaboration2016; Lindegren2021) provides a distance of 21.15+-0.21 pc for the primary binary component. This is the value we adopted for this paper."
 },
 {
  "path": "science.targets[1].redshift_or_distance.evidence[0]",
  "value": "21.81+-0.01 pc",
  "failed_quote": "The system has a projected orbital size of 16\" at the parallactic distance of 21.81+-0.01 pc  (cite: GaiaCollaboration2016; Lindegren2021)."
 },
 {
  "path": "science.targets[1].distance_source.evidence[0]",
  "value": "Gaia EDR3 (cite: GaiaCollaboration2016; Lindegren2021)",
  "failed_quote": "The system has a projected orbital size of 16\" at the parallactic distance of 21.81+-0.01 pc  (cite: GaiaCollaboration2016; Lindegren2021)."
 },
 {
  "path": "data.angular_resolution.evidence[0]",
  "value": "0.91'' x 0.81'', P.A. = -84.8 deg",
  "failed_quote": "This resulted in a synthetized beam of 0.91'' x 0.81'' with a position angle (P.A.) of -84.8^circ."
 },
 {
  "path": "data.other_facilities[0].provided.evidence[1]",
  "value": "1.3 mm (230 GHz) continuum observations of VHS J1256-1257 and G 196-3 B",
  "failed_quote": "This configuration allowed us to obtain images at 1.3 mm (230 GHz) with an angular resolution of 2.53'' x 1.43'' at 0^circ for VHS J1256-1257 and 1.73'' x 1.33'' at 64^circ for G 196-3 B."
 },
 {
  "path": "data.other_facilities[2].provided.evidence[0]",
  "value": "Early Data Release 3 (EDR3) parallactic distances for VHS J1256-1257 and G 196-3",
  "failed_quote": "The Gaia Early Data Release 3 (EDR3) (cite: GaiaCollaboration2016; Lindegren2021) provides a distance of 21.15+-0.21 pc for the primary binary component."
 },
 {
  "path": "data.other_facilities[2].provided.evidence[1]",
  "value": "Early Data Release 3 (EDR3) parallactic distances for VHS J1256-1257 and G 196-3",
  "failed_quote": "The system has a projected orbital size of 16\" at the parallactic distance of 21.81+-0.01 pc  (cite: GaiaCollaboration2016; Lindegren2021)."
 },
 {
  "path": "data.external_data_from_literature[2].what.evidence[0]",
  "value": "Protoplanetary disk dust masses and upper limits in young star-forming regions",
  "failed_quote": "Figure 4 shows the protoplanetary disk dust masses and dust mass upper limits using ALMA data provided by (cite: Testi2022) for the following star-forming regions and young star clusters: L1688 (in rho-Ophiuchi), Taurus, Lupus, Corona Australis, Upper Scorpius, and Chameleon I."
 },
 {
  "path": "processing.imaging.final_beam.evidence[0]",
  "value": "0.91'' x 0.81'', P.A. = -84.8 deg (ALMA); 2.53'' x 1.43'' at 0 deg and 1.73'' x 1.33'' at 64 deg (NOEMA)",
  "failed_quote": "This resulted in a synthetized beam of 0.91'' x 0.81'' with a position angle (P.A.) of -84.8^circ."
 },
 {
  "path": "processing.imaging.final_beam.evidence[1]",
  "value": "0.91'' x 0.81'', P.A. = -84.8 deg (ALMA); 2.53'' x 1.43'' at 0 deg and 1.73'' x 1.33'' at 64 deg (NOEMA)",
  "failed_quote": "This configuration allowed us to obtain images at 1.3 mm (230 GHz) with an angular resolution of 2.53'' x 1.43'' at 0^circ for VHS J1256-1257 and 1.73'' x 1.33'' at 64^circ for G 196-3 B."
 },
 {
  "path": "processing.inherited[1].what.evidence[0]",
  "value": "Procedure for computing bolometric luminosity from observed flux integration",
  "failed_quote": "and the luminosity of log(L/L_odot) = -4.57+-0.2 which we computed from the observed flux integration following the procedure described in (cite: Zakhozhay2017)."
 },
 {
  "path": "processing.inherited[4].what.evidence[0]",
  "value": "Dust temperature–luminosity relation and disk size-dependent coefficients",
  "failed_quote": "The temperature of the dust was evaluated using the relation of (cite: vanderPlas2016): T_d = a (L_ast/L_odot)^b"
 },
 {
  "path": "processing.inherited[6].what.evidence[0]",
  "value": "Constant dust temperature (20 K) and opacity (2.3 cm^2 g^-1) prescription for comparative disk mass calculation",
  "failed_quote": "For the computation of the disk dust masses around central objects with masses from substellar to several times the solar mass, (cite: Testi2022) adopted kappa_nu = 2.3 cm^2 g^-1 and a constant T_dust = 20 K."
 },
 {
  "path": "processing.inherited[7].what.evidence[0]",
  "value": "Mass-luminosity relations for central stars of debris disks",
  "failed_quote": "we used a simple mass—luminosity relation M_ast = L_ast^0.25 (where both parameters are in solar units) applicable to the masses > 0.43 M_odot (cite: Duric2003)."
 },
 {
  "path": "processing.inherited[7].what.evidence[1]",
  "value": "Mass-luminosity relations for central stars of debris disks",
  "failed_quote": "for it we recomputed the mass, using the following relation: M_ast = (L_ast/0.23)^1/2.3, following the prescription by (cite: Duric2003)."
 },
 {
  "path": "analysis_steps[0].method.evidence[1]",
  "value": "Integrate observed flux to compute bolometric luminosity using Gaia EDR3 distance, and compare with BT-Settl evolutionary models to derive companion mass",
  "failed_quote": "and the luminosity of log(L/L_odot) = -4.57+-0.2 which we computed from the observed flux integration following the procedure described in (cite: Zakhozhay2017)."
 },
 {
  "path": "analysis_steps[0].key_parameters[0].evidence[0]",
  "value": "d = 21.15+-0.21 pc, age = 150-300 Myr",
  "failed_quote": "The Gaia Early Data Release 3 (EDR3) (cite: GaiaCollaboration2016; Lindegren2021) provides a distance of 21.15+-0.21 pc for the primary binary component."
 },
 {
  "path": "analysis_steps[2].method.evidence[0]",
  "value": "Compute disk outer radius as 1/3 of the Hill sphere radius, and evaluate dust temperature from companion luminosity and primary irradiation",
  "failed_quote": "The temperature of the dust was evaluated using the relation of (cite: vanderPlas2016): T_d = a (L_ast/L_odot)^b"
 },
 {
  "path": "analysis_steps[3].method.evidence[1]",
  "value": "Compute wavelength-dependent dust opacities with OpacityTool (and Beckwith et al. 1990 extrapolation for VLA) and calculate optically-thin dust mass upper limits for target companions and literature sample",
  "failed_quote": "The wavelength-dependent opacity kappa_nu was calculated for the NOEMA and ALMA data using the code OpacityTool available through the Project Diana"
 },
 {
  "path": "analysis_steps[3].key_parameters[0].evidence[0]",
  "value": "kappa_nu = 4.9 cm^2/g at 340 GHz (0.88 mm), 2.3 cm^2/g at 230 GHz (1.3 mm), 0.33 cm^2/g at 33 GHz (0.9 cm), 0.10 cm^2/g at 10 GHz (3 cm), 0.06 cm^2/g at 6 GHz (5 cm), 0.014 cm^2/g at 1.4 GHz (21.4 cm)",
  "failed_quote": "kappa_nu = 4.9 cm^2/g at nu = 340 GHz (lambda = 0.88 mm), kappa_nu = 2.3 cm^2/g at nu = 230 GHz (lambda = 1.3 mm), kappa_nu = 0.33 cm^2/g at nu = 33 GHz (lambda = 0.9 cm)"
 },
 {
  "path": "analysis_steps[3].key_parameters[0].evidence[1]",
  "value": "kappa_nu = 4.9 cm^2/g at 340 GHz (0.88 mm), 2.3 cm^2/g at 230 GHz (1.3 mm), 0.33 cm^2/g at 33 GHz (0.9 cm), 0.10 cm^2/g at 10 GHz (3 cm), 0.06 cm^2/g at 6 GHz (5 cm), 0.014 cm^2/g at 1.4 GHz (21.4 cm)",
  "failed_quote": "kappa_nu = 0.10 cm^2/g at nu = 10 GHz (lambda = 3 cm), kappa_nu = 0.06 cm^2/g at nu = 6 GHz (lambda = 5 cm), kappa_nu = 0.014 cm^2/g at nu = 1.4 GHz (lambda = 21.4 cm)"
 },
 {
  "path": "analysis_steps[4].key_parameters[0].evidence[0]",
  "value": "T_dust = 20 K, kappa_nu = 2.3 cm^2 g^-1",
  "failed_quote": "For the computation of the disk dust masses around central objects with masses from substellar to several times the solar mass, (cite: Testi2022) adopted kappa_nu = 2.3 cm^2 g^-1 and a constant T_dust = 20 K."
 },
 {
  "path": "analysis_steps[4].assumptions[0].evidence[0]",
  "value": "Constant dust temperature of 20 K across all objects; stellar mass-luminosity relation M_* = L_*^0.25 for M_* > 0.43 M_sun and M_* = (L_*/0.23)^(1/2.3) for < 0.43 M_sun",
  "failed_quote": "we used a simple mass—luminosity relation M_ast = L_ast^0.25 (where both parameters are in solar units) applicable to the masses > 0.43 M_odot (cite: Duric2003)."
 },
 {
  "path": "analysis_steps[4].assumptions[0].evidence[1]",
  "value": "Constant dust temperature of 20 K across all objects; stellar mass-luminosity relation M_* = L_*^0.25 for M_* > 0.43 M_sun and M_* = (L_*/0.23)^(1/2.3) for < 0.43 M_sun",
  "failed_quote": "for it we recomputed the mass, using the following relation: M_ast = (L_ast/0.23)^1/2.3, following the prescription by (cite: Duric2003)."
 },
 {
  "path": "software[4].used_for.evidence[0]",
  "value": "Calculating wavelength-dependent dust opacity kappa_nu for NOEMA and ALMA wavelengths",
  "failed_quote": "The wavelength-dependent opacity kappa_nu was calculated for the NOEMA and ALMA data using the code OpacityTool available through the Project Diana introduced by (cite: 2016A&A...586A.103W)"
 },
 {
  "path": "results_numeric[0].evidence[0]",
  "value": "Bolometric luminosity of VHS J1256-1257 b, log(L/L_sun) = -4.57 dex",
  "failed_quote": "and the luminosity of log(L/L_odot) = -4.57+-0.2 which we computed from the observed flux integration following the procedure described in (cite: Zakhozhay2017)."
 },
 {
  "path": "results_numeric[12].evidence[0]",
  "value": "Maximum cold dust mass for G 196-3 B (at T_d = 5.3 K, NOEMA 1.3 mm) = 1.38e-2 M_Earth",
  "failed_quote": "we derived maximum values of 1.38x10^-2 M_Earth and 5.46x10^-3 M_Earth for the mass of any cold dust that might be surrounding G 196-3 B and VHS J1256-1257 b, respectively."
 },
 {
  "path": "results_numeric[13].evidence[0]",
  "value": "Maximum cold dust mass for VHS J1256-1257 b (at T_d = 4.5 K, ALMA 0.87 mm) = 5.46e-3 M_Earth",
  "failed_quote": "we derived maximum values of 1.38x10^-2 M_Earth and 5.46x10^-3 M_Earth for the mass of any cold dust that might be surrounding G 196-3 B and VHS J1256-1257 b, respectively."
 },
 {
  "path": "findings_qualitative[2].evidence[0]",
  "value": "Stellar debris disks form a sequence in dust mass versus host mass that is parallel to, and lower than, protoplanetary disks for central masses between ~0.5 and ~2 M_sun.",
  "failed_quote": "Interestingly, the sequence described by the debris disks appears to be parallel to that of the protoplanetary disks for the central object mass interval between ~0.5 and ~2 M_odot."
 },
 {
  "path": "claims[0].evidence[1]",
  "value": "No cold dusty emission is detected at current sensitivities, placing lunar-mass-scale upper limits on any putative cold debris disks around both companions.",
  "failed_quote": "Using the flux upper limits at the millimeter and radio wavelength regimes, we derived maximum values of 1.38x10^-2 M_Earth and 5.46x10^-3 M_Earth for the mass of any cold dust that might be surrounding G 196-3 B and VHS J1256-1257 b, respectively."
 },
 {
  "path": "reasoning.limitations_admitted[0].evidence[0]",
  "value": "Dust opacity kappa_nu has large uncertainties due to unknown dust physical properties and internal disk processes.",
  "failed_quote": "kappa_nu suffers from a large uncertainty since it depends not only on the dust physical properties (e.g. (cite: Semenov2003; 2016A&A...586A.103W)) but on the physical processes happening inside the disk as well (cite: Isella2014; Wu2022)."
 },
 {
  "path": "reproducibility.code_released[0].evidence[0]",
  "value": "OpacityTool is publicly available through Project Diana",
  "failed_quote": "The wavelength-dependent opacity kappa_nu was calculated for the NOEMA and ALMA data using the code OpacityTool available through the Project Diana"
 }
]
```
