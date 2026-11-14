# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2019ApJ...871...37H\sonnet\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
# The Molecular and Ionized Gas Phases of an AGN-driven Outflow in a Typical Massive Galaxy at $z\approx2$

## Abstract

Nuclear outflows driven by accreting massive black holes are one of the main feedback mechanisms invoked at high-$z$ to reproduce the distinct separation between star-forming, disk galaxies and quiescent spheroidal systems. Yet, our knowledge of feedback at high-$z$ remains limited by the lack of observations of the multiple gas phases in galaxy outflows. In this work we use new deep, high-spatial resolution ALMA CO(3-2) and archival VLT/SINFONI H$\alpha$ observations to study the molecular and ionized components of the AGN-driven outflow in zC400528 —a massive, main sequence galaxy at $z=2.3$ in the process of quenching. We detect a powerful molecular outflow that shows a positive velocity gradient and extends for at least $\sim$10 kpc from the nuclear region, about three times the projected size of the ionized wind. The molecular gas in the outflow does not reach velocities high enough to escape the galaxy and is therefore expected to be reaccreted. Keeping in mind the various assumptions involved in the analysis, we find that the mass and energetics of the outflow are dominated by the molecular phase. The AGN-driven outflow in zC400528 is powerful enough to deplete the molecular gas reservoir on a timescale at least twice shorter than that needed to exhaust it by star formation. This suggests that the nuclear outflow is one of the main quenching engines at work in the observed suppression of the central star-formation activity in zC400528.

# Introduction

Powerful galaxy outflows induced by active galactic nuclei (AGN) have been invoked as one of the main drivers behind the transition experienced by massive star-forming galaxies during the main epoch of star-formation activity into “red and dead” systems (cite: rhc_silk98; rhc_springel05; rhc_king15). Outflows are expected to play (at least) a twofold role in quenching the star formation activity in massive galaxies. First, they have the power to expel the star-forming material in nuclear regions to large distances ($\gtrsim5$ kpc) on short timescales ($\lesssim1$ Gyr) (cite: rhc_feruglio10; rhc_cicone14; rhc_sturm11; rhc_morganti16; rhc_veilleux17). Second, outflows can transfer enough radiative energy to the circumgalactic medium to drastically reduce the gas accretion rate onto the host galaxy (cite: rhc_dimatteo05; rhc_gabor11; rhc_vdv11).

To quantify the impact of AGN feedback in galaxy evolution it is important to understand the complex, multi-phase nature of AGN-driven outflows. This is a challenging task that requires probing winds on a wide range of physical scales ($\sim1~{\rm pc}-10$ kpc), temperatures ($\sim10^2-10^7$ K) and densities ($\sim10^2-10^8$ cm$^{-3}$). The multiple outflow components include (1) very hot, quasi-relativistic winds from accretion disks observed on $\sim$pc scales in X-ray spectra (cite: rhc_nardini15; rhc_tombesi15), and (2) $\sim$hundred to kilo-parsec scale atomic, molecular, and ionized winds traced by a variety of lines in absorption (cite: rhc_rupke02; rhc_sturm11; rhc_veilleux13; rhc_kornei12; rhc_gonzalez-alfonso17) and emission (cite: rhc_rupke11; rhc_contursi13; rhc_garcia-burillo14; rhc_woo16; rhc_harrison16; rhc_janssen16; rhc_concas17). Accurate measurements of the extent, mass and energetics of AGN-driven outflows can only be achieved when more than one gas phase measurement is available, and even then, they are challenging (cite: rhc_feruglio10; rhc_alatalo15; rhc_morganti16). Part of the problem is that the electron density and the CO-to-H$_2$ factor are required to convert ionized and molecular luminosities into outflow masses, respectively. These quantities are poorly constrained, and can introduce up to an order of magnitude uncertainty in the derived outflow masses.

Powerful AGN-driven outflows are found to be ubiquitous in *typical* massive galaxies at $z\sim2$ (cite: rhc_genzel14; rhc_f-s14; rhc_leung17; rhc_f-s18b), the epoch when both star formation and nuclear activity peaks. These outflows, mostly detected in ionized gas in near-infrared spectroscopic surveys, are fast ($v_{\rm out}\sim1000-2000$ km s$^{-1}$), can extend on large scales ($R_{\rm out}\sim5-10$ kpc), and have mass loading factors ($\eta\equiv \dot{M}_{\rm out}/{\rm SFR}$) in the $\eta\sim0.1-2$ range (cite: rhc_genzel14; rhc_f-s18b).

AGN-feedback in the form of outflows is one of the main candidates to explain the observed suppression of star formation activity from nuclear regions outwards in massive, main-sequence galaxies at $z\sim2$ (cite: rhc_tacchella15b; rhc_barro16; rhc_nelson16). However, this would probably require mass loading factors higher than those measured in the ionized phase, which is the reason why it is so important to detect the molecular gas in outflows –most likely the wind phase carrying most of the ejected mass from the host galaxy (cite: rhc_fiore17).

Wide-band receivers on new or upgraded mm-wave arrays such as ALMA (Atacama Large Millimeter/submillimeter Array) and NOEMA (NOrthern Extended Millimeter Array) opened new windows to detect and characterize the faint (relative to the disk luminosity) molecular outflow signatures in *typical* massive galaxies at high $z$. In this paper we present one case where we combine sensitive, high-spatial resolution ALMA and Very Large telescope (VLT) observations to study the molecular and ionized gas phases of the powerful galactic outflow detected in zC400528 at $z\sim2$.

## zC400528

zC400528 (R.A.$=09:59:47.6$, Decl.$=+01:44:19.0$) is a massive ($M_{\star}=1.1\times10^{11}~M_{\odot}$), star-forming (${\rm SFR}=148~M_{\odot}~{\rm yr}^{-1}$[^1]) galaxy at $z=2.3873$ (cite: rhc_f-s18) located at the tip of the main-sequence relation of star-forming galaxies at $z\sim2-2.5$ (see Figure [1](#fig_MS)). This galaxy has a detected powerful ionized gas outflow that extends for about $\sim5$ kpc (cite: rhc_genzel14; rhc_f-s14). As discussed in (cite: rhc_f-s14), there is evidence for a central AGN driving the outflow that includes an observed high nuclear \[N II\]/H$\alpha$ line ratio of 0.75 (cite: rhc_genzel14), and a detection at 1.4 GHz that implies a ${\rm SFR}\approx790$ M$_{\odot}$ yr$^{-1}$ (cite: rhc_schinnerer10), exceeding its ${\rm SFR}=148~M_{\odot}~{\rm yr}^{-1}$. The galaxy remains undetected in the *Chandra* X-ray data of the COSMOS field (cite: rhc_elvis09). The flux upper limit implies $L_{\rm X-ray}\lesssim10^{44}$ erg s$^{-1}$ (assuming $\Gamma=1.9$ and $N_{\rm H}=10^{22}$ cm$^{-2}$), although this upper-limit could be substantially higher in the Compton-thick case.

Finally, zC400528 is one of the galaxies in the study of (cite: rhc_tacchella15b) that shows evidence for inside-out quenching on short timescales ($\lesssim1$ Gyr) in the inner $\sim$kiloparsec region (see their Figure S4, last panel). From a statistical point of view we would also expect that zC400528 will experience star-formation quenching as the fraction of quiescent galaxies with the stellar mass of zC400528 increase from $\sim$20% at $2<z<2.5$ to $\sim$70% at $1<z<1.5$ (cite: rhc_muzzin13).

This paper is organized as follows. In Section [2](#sec:observations) we describe the observations and the data reduction. In Section [3](#sec:results) we describe the properties (mass, size, energetics) of the molecular gas in the disk and the outflow. In Section [4](#sec:comp) we compare the molecular and ionized phases of the outflow. In Section [5](#sec:escape) we discuss whether the ejected molecular gas can escape the host, the impact of AGN-flickering and the expansion of the outflow, and the effect of AGN-feedback in quenching the star formation activity in the galaxy. Finally, in Section [6](#sec:conclusions) we present our conclusions.

![](M-S.jpg)

![](moment01_wNat_panel_v2.jpg)

# Observations and Data Reduction

The main goal of our observations was to detect and spatially resolve the molecular gas outflow in zC400528 using the redshifted CO(3-2) line emission as a tracer of molecular gas. Our target was first observed by ALMA in Cycle 2 for a total of 0.75 hours (0.6 hours on-source) as part of project 2013.1.00092.S (PI R. Genzel). The observations were carried out in the C34-5/6 configuration, resulting in an angular resolution of $1.1\ensuremath{''} \times 0.6\ensuremath{''}$ in Band 3. During the next ALMA cycle, our source was observed as part of project 2015.1.00220.S (PI R. Genzel) in a more extended configuration, C40-6, resulting in an angular resolution of $0.4\ensuremath{''} \times 0.3\ensuremath{''}$ in Band 3. The total observation time was 5.4 hours (4.5 hours on-source). In both cases the spectral setup included one of the spectral windows in Band 3 centered around the redshifted CO(3-2) line emission ($\nu_{\rm obs}=102.004$ GHz).

The data were processed using the Common Astronomy Software Applications package (cite: rhc_casa). The pipeline-calibrated interferometric visibilities delivered by ALMA from both cycles were then combined and imaged at 50 km s$^{-1}$ resolution using natural weighting. In the combination process we took into account the different CASA visibility weights applied during Cycle 2 and 3 using the CASA task STATWT.[^2] The size of the restoring beam of the combined data was $0.51\ensuremath{''}\times 0.47\ensuremath{''}$ ($4.2\times3.9$ kpc) at a position angle of ${\rm PA=-12.13^{\circ}}$. By combining the data from the more extended and compact array configurations we achieved high enough spatial resolution to resolve the galaxy, and at the same time improve our ability to detect and characterize a potential extended, more diffuse component of the molecular outflow.

All values were primary beam corrected for all quantitative analyses. We reached an rms noise of 0.08 mJy beam$^{-1}$ in 50 km s$^{-1}$ channels for CO(3-2). No continuum emission was detected at 100 GHz.

For a detail description of the observations of the H$\alpha$ and \[N II\] lines in zC400528 carried out with the near-IR integral field spectrograph SINFONI (cite: rhc_eisenhauer03) at the Very Large Telescope of the European Southern Observatory (ESO) we refer to (cite: rhc_f-s14). In summary the galaxy was observed in $K$-band for an on-source time of 4 hr using a natural guide star for the adaptive optics correction. The achieved angular resolution (PSF FWHM) of the final reduced data was 0.15$''$.

# Results

## The molecular disk

Figure [2](#fig_moms) shows the CO(3-2) integrated intensity and velocity maps of zC400528. We measure an integrated CO(3-2) flux of $F_{\rm CO}=1.11\pm0.05$ Jy km s$^{-1}$, which corresponds to a luminosity of $L_{\rm CO}=3.45\times10^{10}~L_{\odot}$. [^3] The molecular gas mass ($M_{\rm mol,disk}$), assuming a conversion factor $\alpha_{\rm CO(1-0),T18}=4.3~M_{\odot}~({\rm K~km~s^{-1}~pc^{-2}})^{-1}$ (cite: rhc_tacconi18)[^4] and a velocity-integrated Rayleigh-Jeans brightness temperature line ratio $R_{13}=1.3$ (cite: rhc_dannerbauer09; rhc_daddi15; rhc_bolatto15), is $M_{\rm mol,disk}=1.1\times10^{11}~M_{\odot}$.[^5] This corresponds to a gas to stellar ratio of $\mu_{\rm mol,disk}=M_{\rm mol}/M_{*}\approx1$, which is consistent with typical gas mass fractions observed in massive, star-forming galaxies at $z\sim2$ (cite: rhc_tacconi10; rhc_tacconi13; rhc_tacconi18).

The integrated velocity map on the right panel of Figure [2](#fig_moms) shows that the molecular disk is rotating approximately in the east-west direction, consistent with the observed rotation in the ionized gas (cite: rhc_newman13; rhc_f-s18).

Figure [3](#fig_spectra) (left) compares the spatial distribution of the molecular gas, the ionized gas disk traced by H$\alpha$ emission (cite: rhc_f-s14), and the stellar mass traced by the *HST* $H$-band (cite: rhc_tacchella15). Both molecular and ionized gas components share a similar spatial structure, including a more diffuse component that extends towards the south-east region. The peak of the $H$-band emission is shifted $\sim0.2\ensuremath{''}$ north-east with respect to the peak of the ALMA CO(3-2) emission. The astrometric precision of our ALMA data is $\sim0.025\ensuremath{''}$,[^6] which is at least a factor of $\sim10$ better than the astrometrical accuracy of the *HST* data. Therefore, it is not possible to determine whether the spatial offset is due to physical reasons or astrometric errors.

The right panel of Figure [3](#fig_spectra) shows the CO(3-2) and H$\alpha$+\[N II\] spectrum from within a $0.6\ensuremath{''}$-radius circular aperture centered at the peak of emission. The \[N II\]/H$\alpha$ line peak ratio is 0.8 (cite: rhc_genzel14) which is characteristic of galaxies where the AGN contributes to the ionizing radiation or shocks affect the ionization balance (cite: rhc_kewley13; rhc_newman14). As described in detail in (cite: rhc_genzel14) and (cite: rhc_f-s14), an ionized outflow is detected as a strong nuclear broad component in the H$\alpha$ spectrum (detected out to velocities $\sim\pm1000$ km s$^{-1}$ relative to the systemic velocity). In the case of the CO(3-2) spectrum, we observe a high-velocity wing on the red side (\[+300,+500\] km s$^{-1}$) that is likely the molecular component of the outflow. We analyze and interpret this high-velocity feature in the CO(3-2) spectrum in the next Section.

![](HaCO_spectra_mom.jpg)

![](PV_panel_COHa_edited.jpg)

![](CO_kin_comp_edited.jpg)

![](redwing_chanmap_2x4.jpg)

## The molecular outflow

As a first step to study the high-velocity components in the ionized and molecular spectrum of zC400528, we make position-velocity (P-V) diagrams extracted along the vertical (south-north), horizontal (west-east), and $-45^{\circ}$ (south-east to north-west) directions through the emission peak. The top panel in Figure [4](#fig_pv) shows the results for the CO(3-2) data. We identify the rotation pattern of the galaxy in the $[-250,+250]$ km s$^{-1}$ velocity range, and a high-velocity ($v\gtrsim+300$ km s$^{-1}$) component along all the examined directions, and that preferentially extends along the north-west direction for about $\sim1$$''$ (which corresponds to a projected distance of $\approx8.4$ kpc). The contours in the bottom panels of Figure [4](#fig_pv) show the P-V curves for the H$\alpha$ and \[N II\] lines (the systemic velocity is set to match the H$\alpha$ line central velocity) plotted on top the CO(3-2) P-V diagram. On the receding side, the outflow is detected both in ionized and molecular gas, with the latter showing a more extended spatial distribution. On the other hand, there is no molecular counterpart to the high-velocity ionized gas observed at velocities $v\lesssim-300$ km s$^{-1}$.

### Disentangling the molecular emission from disk and outflow

To quantify the total amount of molecular gas in the outflow it is necessary to identify and remove the CO(3-2) line emission associated with the rotating disk of the galaxy. One common approach is to fit two Gaussian profiles to the spectrum where a narrow component centered at the systemic velocity is used to characterize the rotating disk, and a broad component to characterize the outflow. The flux in the broad component, however, only represents an upper limit to the actual flux from the outflowing material since it may include CO line emission at low velocities that is associated with the rotating disk. Given that we have sufficient spatial resolution and signal-to-noise (S/N) in our ALMA CO(3-2) data, here we try a different strategy to attempt to remove the low-velocity gas material.

First, we use the CASA task IMFIT to fit in each 50 km s$^{-1}$ channel of the CO(3-2) cube a two-dimensional Gaussian to the image in the region where the source is detected. We then use the resulting fits to make a source model where the Gaussian position, orientation, and intensity changes as a function of velocity. The last step in our procedure is to remove from each slice the source model, resulting in a residual cube where the high-velocity outflowing gas is now disentangled from the emission associated with the rotating disk. A similar approach was used by (cite: rhc_veilleux17) to study the molecular outflow in a luminous infrared galaxy using CO(1-0) observations.

The first two panels in Figure [5](#model) show the integrated intensity map calculated on the \[$-$250,+250\] km s$^{-1}$ range of the original cube (left), and the cube resulting after we subtract the rotating disk model (i.e., the residual cube; right). The model does a good job at removing the CO(3-2) line emission associated with the rotating disk, and we only observe a relatively high residual at the level of $\sim$0.06 Jy km s$^{-1}$ in the more diffuse and extended south-east component. The third panel in Figure [5](#model) shows the CO(3-2) spectrum integrated over a circular aperture with a radius of 0.5$''$. The black and green lines correspond to the spectrum extracted in the original cube and the residual cube, respectively. The integrated signal of the high-velocity red wing emission in the residual cube is clear, and there is no evidence for a molecular outflow component on the approaching side of the spectrum. The last panel of Figure [5](#model) shows the integrated intensity map of the residual cube in the velocity range where we identified the red wing emission (\[+300,+700\] km s$^{-1}$). The outflow emission peaks about 0.2$''$ ($\sim2$ kpc) west of the molecular disk center, and there is a tail of outflowing gas line emission that extends beyond the molecular disk towards the north-west for about 1$''$, which corresponds to a projected distance of $\sim8$ kpc.

### The structure of the molecular outflow

A more detailed view of the molecular outflow components as a function of velocity is shown in the velocity channel map of the residual cube in Figure [6](#vel_chan_map). For reference, overplotted on each panel are the contours from the velocity integrated CO(3-2) emission of the rotating disk. The first significant outflow structure appears at $v=+300$ km s$^{-1}$ and is spatially coincident with the central region of the molecular gas disk. Between $v=+350$ and +400 km s$^{-1}$ the main component of the outflow moves towards the west about 0.2$''$ –which corresponds to a projected distance of $\sim2$ kpc. At $v=+450$ km s$^{-1}$ the main outflow component starts to extend towards the north and continues until $v=+500$ km s$^{-1}$, which is the last channel at which we detect CO(3-2) line emission.

The last two panels in Figure [6](#vel_chan_map) show the integrated intensity and velocity maps of the molecular outflow detected in the \[+300,+500\] km s$^{-1}$ range. The bulk of the line emission associated with the outflow is shifted about 0.2$''$ (projected distance of $\sim2$ kpc) west of the center of the molecular disk and extends to the north for approximately 0.7$''$ (projected distance of $\sim6$ kpc), where it shifts to the west in what seems to appear a second outflow component –still connected to the main component– at about 1.2$''$ (projected distance of $\sim10$ kpc) from the center. One could suspect that this spatially extended feature of the outflow is in reality a tidal tail product of the interaction with a lower mass companion, but visual inspection of a deep *HST* F160W image of the field reveals no stellar emission associated to a close neighbor in the north-east quadrant.

We observe a velocity gradient in the outflow: the gas velocity increases from $\sim+350$ to $\sim+500$ km s$^{-1}$ as the outflow extends north of the nucleus. This could be indicative of an accelerating continuous outflow. Another possibility could be that the ejection of molecular gas triggered during the last outflow burst had a distribution of velocities, so the faster ejecta components traveled further away than the slower components. The velocity of the most distant outflow component in the north-west has a velocity of $\sim+350$ km s$^{-1}$, a lower velocity that could be the result of gravitational pull.

In summary, perhaps the most striking characteristic of the molecular outflow in zC400528 is its asymmetry: we only detect the receding component of the wind. In the local universe is not uncommon to observe asymmetric outflows. For example, (cite: rhc_p-s18) find that in four out of five spatially resolved molecular gas outflows in ULIRGs the receding component of the wind is stronger than the approaching one. This is also true for the molecular outflow in Mrk 231 (cite: rhc_cicone12; rhc_feruglio15) and the western nucleus of Arp 220 (cite: rhc_barcos18). High-resolution simulations of $z\sim2$ isolated disks also find that AGN-driven outflows are typically unipolar as a result of dense cloud structures in the vicinity of the black hole blocking the expansion in one direction (cite: rhc_gabor14). Another possibility is that the molecular outflow on the approaching side experienced a change of phase, similar to what is observed in M82 where the dominant phase of the wind transitions from molecular to atomic at about one kiloparsec distance from the disk (cite: rhc_leroy15).

![](redwing_apertures_ink.jpg)

### The molecular gas mass in the outflow

For each outflow component, we measure CO(3-2) flux densities with Gaussian fits to the spectra in the residual cube extracted from the circular and elliptical apertures shown in Figure [7](#flux). The flux densities are listed in Table [1](#table:flux).

How to convert these flux densities associated with the outflow into molecular gas masses is still an open question. The CO-to-H$_{2}$ conversion factor depends mainly on the metallicity and the surface density of the gas (cite: rhc_bolatto13). In the case of the CO gas in the outflow, in the literature there are three CO-to-H$_{2}$ conversion factors commonly used: (1) a Galactic conversion factor of $\alpha_{\rm CO,MW}=4.3~M_{\odot}~({\rm K~km~s^{-1}~pc^{-2}})^{-1}$ (cite: rhc_bolatto13); (2) a ULIRG-like conversion factor of $\alpha_{\rm CO,ULIRG}=0.8~M_{\odot}~({\rm K~km~s^{-1}~pc^{-2}})^{-1}$ (cite: rhc_cicone14; rhc_feruglio15; rhc_veilleux17), and (3) an optically-thin conversion factor of $\alpha_{\rm CO,thin}=0.34~M_{\odot}~({\rm K~km~s^{-1}~pc^{-2}})^{-1}$ (cite: rhc_bolatto13b; rhc_richings18). Assuming that the molecular gas in outflows is optically thin –as observed for example in the jet accelerated wind of IC 5063 (cite: rhc_dasyra16)–, would yield the most conservative (or “minimum”) estimate of the molecular gas masses.

In this paper we adopt the ULIRG-like conversion factor ($\alpha_{\rm CO,ULIRG}$), which seems to be a good compromise given the range of conversion factors available. In addition, the detection of dense molecular gas entrained in the outflow of starbursts and LIRGs (cite: rhc_aalto12; rhc_aalto15; rhc_walter17) argues in favor a conversion factor higher than $\alpha_{\rm CO,thin}$. In the main streamer of NGC 253, for example, the outflowing gas is not optically thin, as a the observed CO(2-1) to CO(1-0) brightness temperature line ratio is about unity (Zschaechner et al., submitted to ApJ). We also expect that the molecular gas in the outflow is likely not cold but warm, because it has been shocked at some level and/or it is immersed in hot gas and subjected to a substantial external radiation field. In that case the physical conditions of the molecular gas in the wind better resemble those found in the ISM of (U)LIRGs rather than the Milky Way.

The molecular gas masses for each of the outflow components are listed in Table [1](#table:flux). The total molecular gas mass in the outflow of zC400528 is

$$\begin{equation*}
M_{\rm out,mol}=3.36\times10^{9}~M_{\odot}\times\bigg(\frac{\alpha_{\rm CO}}{\alpha_{\rm CO,ULIRG}}\bigg),
\end{equation*}$$

which corresponds to $\sim3\%$ of the molecular gas mass in the disk. As Figure [8](#frac) shows, this fraction is similar to those measured in local (U)LIRG and Seyfert galaxies of similar stellar mass (cite: rhc_fiore17)[^7].

![](diskvsout.jpg)

|           |                    |                         |     |     |     |
|:---------:|:------------------:|:-----------------------:|:---:|:---:|:---:|
| Component |  Integrated Flux   | $M_{\rm out,mol}$$^{a}$ |     |     |     |
|    \#     | \[Jy km s$^{-1}$\] | \[$10^{9}~M_{\odot}$\]  |     |     |     |
|     1     |  $0.098\pm0.016$   |   1.81 $(0.77-9.72)$    |     |     |     |
|     2     |  $0.029\pm0.007$   |   0.50 $(0.21-2.68)$    |     |     |     |
|     3     |  $0.032\pm0.007$   |   0.59 $(0.25-3.17)$    |     |     |     |
|     4     |  $0.184\pm0.029$   |   3.36 $(1.42-18.06)$   |     |     |     |

: Molecular outflow mass in zC400528

Table notes: $^{a}$ Molecular gas masses calculated using an $\alpha_{\rm CO,ULIRG}$ conversion factor. The values in parenthesis correspond to the molecular gas masses we would obtain if we apply a $\alpha_{\rm CO,thin}$ or $\alpha_{\rm CO,MW}$ conversion factor, respectively.

![](outflow_dMS_inv.jpg)

### Molecular mass outflow rate

There are two common approaches to measure outflow mass rates in galaxies. There are often referred as *instantaneous* (maximum) and *average* (minimum), and a detailed description of the assumptions that go into the calculations can be found in (cite: rhc_rupke05). In the *instantaneous* approach the outflow mass rate ($dM_{\rm out}/dt$) is calculated as the product of the outflow gas mass and the timescale taken by the gas to cross the thickness of the outflowing shell, i.e.,

$$\begin{equation}
\dot{M}_{\rm out}^{\rm inst} = M_{\rm out}\times\frac{v_{\rm out}}{\Delta R},
\end{equation}$$

where $v_{\rm out}$ is the velocity of the outflow and $\Delta R$ ($=R_{\rm out}-R_{\rm int}$) is the thickness of the outflow shell. This approach has been used in a number of studies including (cite: rhc_sturm11) and (cite: rhc_gonzalez-alfonso14).

In the case of the *average* approach, the assumption is that the outflowing gas extends to $r = 0$, so the outflow mass rate ($\dot{M}_{\rm out}$) is given by the outflow gas mass time-averaged over the flow timescale, i.e.,

$$\begin{equation}
 \label{eq:avg}
{\dot M}_{\rm out}^{\rm avg} = M_{\rm out}\times \frac{v_{\rm out}}{R_{\rm out}}.
\end{equation}$$

If the emitting volume (spherical or multi-conical) is filled with uniform density, then the mass outflow rate in Eq. [\[eq:avg\]](#eq:avg) should be a factor of 3 higher (cite: rhc_feruglio10; rhc_maiolino12; rhc_r-z13; rhc_fiore17).

In this paper we use the *average* approach, which represents a more conservative way to characterize the outflow than the *instantaneous* method as $\dot{M}_{\rm out}^{\rm avg}$ is smaller than $\dot{M}_{\rm out}^{\rm inst}$ by a factor $(R_{\rm out}/\Delta R)$. Following this, the first step is to calculate the flow timescale, $t_{\rm out} = R_{\rm out}/v_{\rm out}$. As described in §[3.2.2](#section:structure), zC400528 has three main molecular outflow components. If we estimate the flow timescale based on the maximal extension of the outflow, then $t_{\rm out,mol}\approx8.5~{\rm kpc}/400~{\rm km~s}^{-1}\approx2\times10^7$ yr. A more representative or characteristic timescale would result from considering only the main outflow component (which corresponds to regions 1 and 2 in Figure [7](#flux)). This component encompasses $\sim80$% of the outflow total mass, has a size of $R_{\rm out,mol}=0.5\ensuremath{''}$ ($\approx4.2$ kpc; calculated from a two-dimensional Gaussian fit and deconvolved from the beam), and shows a positive velocity gradient in the \[+350,+500\] km s$^{-1}$ range. From these values the resulting flow timescale is $t_{\rm out,mol}\approx4.2~{\rm kpc}/450~{\rm km~s}^{-1}\approx9\times10^6$ yr, which yields a mass outflow rate of:

$$\begin{equation*}
\begin{split}
\dot{M}_{\rm out,mol}^{\rm avg}\approx256~M_{\odot}~{\rm yr}^{-1}\times\bigg(\frac{\alpha_{\rm CO,out}}{\alpha_{\rm CO,ULIRG}}\bigg)\\
\times\bigg(\frac{v_{\rm out}}{450~{\rm km}~{\rm s}^{-1}}\bigg)\times\bigg(\frac{4.2~{\rm kpc}}{R_{\rm out}}\bigg)
\end{split}
\end{equation*}$$

This translates into an outflow depletion time ($\tau_{\rm dep,out}= M_{\rm mol,disk}/\dot{M}_{\rm out,mol}^{\rm avg}$) of

$$\begin{equation*}
\begin{split}
\tau_{\rm dep,out}\approx4.7\times10^8~{\rm yr} \times \bigg(\frac{\alpha_{\rm CO,disk}}{\alpha_{\rm CO,T18}}\bigg) 
\times \bigg(\frac{\alpha_{\rm CO,ULIRG}}{\alpha_{\rm CO,out}}\bigg) \\
\times \bigg(\frac{450~{\rm km}~{\rm s}^{-1}}{v_{\rm out}}\bigg)\times
\bigg(\frac{R_{\rm out}}{4.2~{\rm kpc}}\bigg).
\end{split}
\end{equation*}$$

Compared to the star-formation depletion timescale ($\tau_{\rm dep,SF}=M_{\rm mol,disk}/{\rm SFR}$), $\tau_{\rm dep,out}$ is a factor of $\sim2$ shorter – or equivalently, the mass loading factor in the molecular phase ($\eta=\dot{M}_{\rm out,mol}/{\rm SFR}$) is $\sim2$.

A more common approach used in outflow studies to measure mass loss rates consist in fitting the system line emission using two Gaussian components – a narrow component for the disk and a broad component for the outflow. The “maximum” projected velocity of the outflow component is then defined as the centroid velocity plus one-half the velocity width (cite: rhc_rupke05; rhc_veilleux05). Following this method we measure $M_{\rm out}=3.6\times10^{9}$ M$_{\odot}$ and $v_{\rm out,max}=590$ km s$^{-1}$. If we consider these values and the maximum projected extension of the outflow, $R_{\rm max}\approx8.5$ kpc, we calculate a mass loss rate of $\dot{M}_{\rm out}=180$ M$_{\odot}$ yr$^{-1}$. This result is consistent, within the uncertainties involved in the calculation, to that we derived using the method adopted in this work described in §[3.2.1](#separation).

So far we have ignored the effect that the inclination of the outflow has on the determination of the mass outflow rate, and consequently, the outflow depletion timescale. The reason is that we do not have enough information to constrain the geometry of the outflow. If $\theta$ corresponds to the inclination angle of the outflow with respect to the line-of-sight, then the deprojected outflow size is $R_{\rm out}=R_{\rm out,proj}/{\rm sin}(\theta)$ and the deprojected outflow velocity is $v_{\rm out}=v_{\rm out,proj}/{\rm cos}(\theta)$. This implies that the inclination corrected mass outflow rate is proportional to ${\rm tan}(\theta)$. zC400528 has an inclination of $i\approx37^{\circ}$ (cite: rhc_f-s18). If we assume that the outflow is perpendicular to the disk, then the deprojection effects in velocity and radius almost cancel out and the correction is small and of the order of $\sim0.75$.

Figure [9](#dMS) compares the outflow and star formation depletion timescales of galaxies as a function of their separation from the main-sequence (after removing the dependence with $z$ using (cite: rhc_tacconi18) scaling relations). The plot includes zC400528 and a compilation of local (U)LIRG and Seyfert galaxies (cite: rhc_fiore17). We observe that local systems where the depletion of the molecular gas is dominated by star formation lie at least $\sim1.5$ dex above the main-sequence. On the other hand, galaxies where the depletion of molecular gas is dominated by outflows are located within $\sim1$ dex of the main-sequence, with the exception of the above outlier Mrk 231 (cite: rhc_feruglio10). Similar to Mrk 231, our target galaxy zC400528 is exhausting its nuclear molecular gas reservoir via the outflow about twice as fast as due to its star formation activity. Note, however, that in contrast to Mrk 231 zC400528 is not a $\times100$ outlier but only +0.4 dex above the main-sequence of star-forming galaxies at $z\approx2$. We discuss in more detail the effect that the powerful molecular outflow detected in zC400528 may have on quenching its star formation in Section [5.3](#sec:quenching).

![](energetics.jpg)

![](outflow_molecular_ionized_CO_photoshop_numbered_ink.jpg)

## Energetics of the molecular outflow

We calculate the momentum flux ($\dot{P}_{\rm out}$) and mechanical power ($\dot{E}_{\rm out}$) in the outflow following $\dot{P}_{\rm out} = \dot{M}_{\rm out} \times v_{\rm out}$ and $\dot{E}_{\rm out} = \frac{1}{2} \dot{M}_{\rm out} \times v_{\rm out}^2$.

From the mass outflow rate $\dot{M}_{\rm out}^{\rm avg}$ calculated in §[3.2.4](#section:Mdot), the momentum flux is

$$\begin{equation*}
\begin{split}
\dot{P}_{\rm out,mol}\approx7.2\times10^{35}~{\rm dynes}\times\bigg(\frac{\alpha_{\rm CO,out}}{\alpha_{\rm CO,ULIRG}}\bigg)\\
\times\bigg(\frac{v_{\rm out}}{450~{\rm km}~{\rm s}^{-1}}\bigg)^2\times\bigg(\frac{4.2~{\rm kpc}}{R_{\rm out}}\bigg)
\end{split}
\end{equation*}$$

and the mechanical luminosity is

$$\begin{equation*}
\begin{split}
\dot{E}_{\rm out,mol}\approx1.6\times10^{43}~{\rm erg~s}^{-1}\times\bigg(\frac{\alpha_{\rm CO,out}}{\alpha_{\rm CO,ULIRG}}\bigg)\\
\times\bigg(\frac{v_{\rm out}}{450~{\rm km}~{\rm s}^{-1}}\bigg)^3\times\bigg(\frac{4.2~{\rm kpc}}{R_{\rm out}}\bigg).
\end{split}
\end{equation*}$$

Relative to the AGN bolometric luminosity $(L_{\rm AGN,bol}; see Appendix~\ref{agn_bol})$ and radiation momentum rate ($L_{\rm AGN,bol}/{\rm c}$) measured in zC400528, the momentum boost is $\dot{P}_{\rm out,mol}/(L_{\rm AGN,bol}/c)\approx3$ and $\dot{E}_{\rm out,mol}\approx0.2\%L_{\rm AGN,bol}$.

As Figure [10](#energetics) shows, the momentum boost in zC400528 is at the low end of the distribution of momentum boost observed in local (U)LIRGs (cite: rhc_gonzalez-alfonso17), and suggest that if the gas in the molecular outflow is not optically thin, then the outflow is not momentum conserving ($\lesssim2 L_{\rm AGN,bol}/c$) but rather energy conserving (cite: rhc_zubovas12; rhc_f-g12). In addition, the outflow energy flux in zC400528 is $0.2\%$ of $L_{\rm bol,AGN}$, in agreement with the theoretical expectations that AGN-driven, energy-conserving bubbles should be able to supply a power up to $\sim5\%$ of $L_{\rm AGN,bol}$ (cite: rhc_f-g12; rhc_king15).

A summary of the molecular outflow mass and energetics measured in zC400528 for different assumptions on $\alpha_{\rm CO}$ can be found in Table [2](#table:energetics).

![](Enuc_HaCO.jpg)

![](budget.jpg)

# Comparison between molecular and ionized outflow

Our current knowledge of the multi-phase structure and energetics of galactic outflows at high-$z$ remains greatly limited by the scarcity of observations that target both the ionized and neutral phases of the outflow. The subject of this study, zC400528, represents an exception, with high-resolution observations of the ionized (VLT/SINFONI adaptive optics-assisted) and molecular (ALMA) outflow gas available. In this section we use these complementary datasets to compare the spatial distribution and energetics of the ionized and molecular phases of the outflow.

## Morphology

Figure [11](#outflow_mom0) shows the spatial distribution of the molecular disk (background), the H$\alpha$ blue and red broad (outflow) component (green), and the molecular wind (red). The bulk of the projected H$\alpha$ broad emission extends $\sim4$ kpc north from the nuclear region. Beyond this point, the only two extra-nuclear ionized outflow components detected, A and B, are co-spatial with the molecular outflow gas and at least in the case of region A, as Figure [12](#Enuc) shows, the molecular and ionized gas velocities are comparable.

The spatial distribution of the outflow in zC400528 suggests that the ionized gas is outflowing inclined ($\sim60^{\circ}$) with respect to the major kinematic axis, likely along the path of least resistance outside the galaxy plane. There are two main molecular outflow components in the inner $\sim4$ kpc region: one that extends alongside the ionized wind (from the center to region A), and one that is aligned with the major kinematic axis, and could therefore be equatorial. This picture resembles the structure of the AGN-driven outflow in NGC 1068 (cite: rhc_tecza01; rhc_cecil02). There the ionized cone is inclined $\sim40^{\circ}$ with respect to the galaxy disk, and the molecular outflow extends preferentially along the galaxy plane launched as a result of the ionization cone sweeping the molecular gas in the inner disk (cite: rhc_garcia-burillo14). The fact that the outflow in zC400528 appears to be not perpendicular to the disk is a common feature observed in AGN-driven outflows. Star-formation-driven outflows, on the other hand, tend to be align with the minor kinematic axis of the disk (cite: rhc_leroy15; rhc_p-s18).

The configuration of the ionized and molecular phases of the outflow in zC400528 is also in qualitatively agreement with the modeling work of (cite: rhc_zubovas14b). They find that AGN-driven outflows that start spherical quickly develop a bipolar morphology that expands faster and further in the polar direction (the direction of least resistance) than in the equatorial direction. After $\sim10$ Myr (the flow timescale in zC400528), several cold dense clumps have formed embedded in the hot gas and are moving upward, while in the plane of the galaxy, the cold gas, squeezed by the expanding bubbles, is being pushed outwards with a mean velocity of $\sim400$ km s$^{-1}$.

## Mass and energetics

The ionized mass in the outflow of zC400528 is $M_{\rm out,ion}=2.2\times(300~{\rm cm}^{-3}/n_{\rm e})\times10^8~M_{\odot}$ (cite: rhc_genzel14), where $n_{\rm e}$ corresponds to the electron density of the ionized gas in the outflow. Recent results by (cite: rhc_f-s18b) find that the mean electron density in the outflow gas of $z\sim2$ galaxies is $n_{\rm e}\sim350$ cm$^{-3}$.

For an outflow size of $R_{\rm out,ion}=3$ kpc (cite: rhc_f-s14) and an outflow velocity of $v_{\rm out,ion}=802$ km s$^{-1}$ (cite: rhc_genzel14), the ionized mass outflow rate is $\dot{M}_{\rm ion,out}=53$ M$_{\odot}~{\rm yr}^{-1}$. Based on the same assumptions, the ionized momentum and energy outflow rates are $\dot{P}_{\rm out,ion}=2.7\times10^{35}$ dynes and $\dot{E}_{\rm out,ion}=1.1\times10^{43}$ erg s$^{-1}$, respectively. Figure [13](#bar_fraction) summarizes the mass and mass loss rates measured in the molecular and ionized outflow gas in zC400528. The molecular phase dominates the total *observed* budget of both $M_{\rm out}$ and $\dot{M}_{\rm out}$. Note, however, that there are gas phases in the outflow that remain unobserved and could change the overall balance, including very hot gas that could significantly contribute to the ionized outflow mass (cite: rhc_veilleux05).

A summary of the ionized outflow mass and energetics measured in zC400528 for different assumptions on $n_{\rm e}$, and the comparison to the quantities measured in the molecular phase, can be found in Table [2](#table:energetics).

Another quantity of interest in the study of galactic outflows is the mass loading factor ($\eta_{\rm phase}$), which is defined as a the ratio between the mass outflow rate and the SFR. Figure [14](#eta) shows the molecular and ionized mass loading factors as a function of the separation from the main-sequence of galaxies (removing the $z$ dependence using (cite: rhc_tacconi18) scaling relations) for nearby starbursts and AGN galaxies (cite: rhc_heckman15; rhc_fiore17) and massive (log$(M_{*}/M_{\odot})\geq10.9$), star-forming galaxies at $z\sim1-3$ (cite: rhc_genzel14). The ionized mass loading factors of these high-$z$ galaxies[^8] are found to be comparable to those observed in local main-sequence outliers.

The molecular mass outflow rate of zC400528 is higher than its SFR ($\eta_{\rm mol}=1.7$), and comparable to some of the powerful molecular outflows observed in local starbursts and Seyfert galaxies (see also §[3.2.4](#section:Mdot)). In addition, the molecular mass loading factor is $\sim4$ times higher than its ionized counterpart. Note, however, that these results depend on assumptions of the properties of the outflow gas that are not yet fully constrained (e.g., the CO-to-H$_2$ conversion factor, the electron density, geometry, etc). The same caveat applies to all the other measurements shown in the figure.

|  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|
| Phase | Mass | $\dot{M}_{\rm out}$ | $\dot{P}_{\rm out}$ | $\dot{E}_{\rm out}$ |
|  | $10^9~M_{\odot}$ | $M_{\odot}~{\rm yr}^{-1}$ | $10^{35}$ dynes | $10^{43}$ erg $s^{-1}$ |
| Molecular$^{a}$ | 3.36 $(1.42-18.06)$ | 256 $(108.8-1376.0)$ | 7.2 $(3.1-38.7)$ | 1.6 $(0.68-8.6)$ |
| Ionized$^{b}$ | 0.22 $(0.07-0.66)$ | 53 $(15.9-159.0)$ | 2.7 $(0.81-8.1)$ | 1.10 $(0.33-3.30)$ |

: Molecular and Ionized gas outflow Masses and Energetics

Table notes: $^{a}$ For molecular gas quantities we assume an $\alpha_{\rm CO,ULIRG}$ conversion factor. The values in parenthesis correspond to the values we would obtain if we apply a $\alpha_{\rm CO,thin}$ or $\alpha_{\rm CO,MW}$ conversion factor, respectively. $^{b}$ For ionized gas quantities we assume $n_{\rm e}=300~{\rm cm}^{-3}$ following (cite: rhc_f-s18b). The values in parenthesis correspond to the values we would obtain if we assume $n_{\rm e}=10^3~{\rm cm}^{-3}$ or $n_{\rm e}=100~{\rm cm}^{-3}$, respectively.

![](dMS_vs_SFR_eta_inv.jpg)

# Discussion

## Can the outflowing material escape the gravitational potential of its host?

Understanding whether baryons ejected by winds escape the galaxy or rain back to the disk is key to reproduce the observed galaxy stellar masses and the metal enrichment of the IGM (cite: rhc_oppenheimer10; rhc_muratov15). Simulations show that about half of the ejected outflow mass across all galaxy masses is later re-accreted (cite: rhc_uebler14; rhc_christensen16), and that in massive $z\sim2$ galaxies about $\sim30-40\%$ of the stellar mass forms from gas contributed by wind recycling (cite: rhc_a-c17).

To determine if the molecular gas in the outflow of zC400528 can permanently escape the galaxy, first we estimate the escape velocity ($v_{\rm esc}$) from the host. For this we follow (cite: rhc_rupke02) and use a simple gravitational model based on a truncated ($r<r_{\rm max}$) isothermal sphere, so $v_{\rm esc}(r) = \sqrt{2}v_{\rm circ}[1+{\rm ln}(r_{\rm max}/r)]^{1/2}$ [^9]. Assuming that the dark matter halo extends to $r_{\rm max}\sim100$ kpc and using a circular velocity for zC400528 of $v_{\rm circ}=344$ km s$^{-1}$ (cite: rhc_f-s18), the escape velocity at $r=10$ kpc is $v_{\rm esc, 10kpc}\sim880$ km s$^{-1}$. The highest velocity molecular outflow material we detect in zC400528 has a velocity of $v_{\rm out}\approx500$ km s$^{-1}$. If we take into account inclination effects (see §[3.2.4](#section:Mdot)) the deprojected outflow velocity could increase to $v_{out}\sim650$ km s$^{-1}$, which is still lower than the escape velocity. This suggests that the bulk of the expelled molecular gas mass will be re-accreted back onto the galaxy on timescales –according to simulations– no shorter than $\sim1$ Gyr (cite: rhc_oppenheimer10; rhc_uebler14; rhc_christensen16).

In the case of the ionized outflowing gas, the escape velocity at 3 kpc –the distance about the size of the ionized outflow– is $v_{\rm esc, 3kpc}\sim1,000$ km s$^{-1}$. The highest velocity gas in the ionized wind can reach velocities up to $\sim800$ km s$^{-1}$ (cite: rhc_genzel14), which if we correct by inclination can increase to $\sim1,000$ km s$^{-1}$ and potentially escape the galaxy.

The very small fraction of the molecular and ionized outflow gas that can escape the gravitational field of zC400528 is consistent with the low escape fractions ($\lesssim20\%$) measured in neutral, ionized and molecular gas winds in local (U)LIRGs (cite: rhc_rupke05; rhc_arribas14; rhc_p-s18; rhc_fluetsch18).

## AGN flickering and outflow expansion

Observational and theoretical arguments suggest that the AGN lifetime of $\sim10^{7}-10^{9}$ yr is in reality a succession of hundreds or thousands of short ($\sim10^{5}$ yr) phases of supermassive black hole growth (cite: rhc_schawinski15) – a process called AGN flickering. These periods of episodic AGN activity inflate large-scale outflows which can continue to expand even after the AGN finally switches off as a result of clearing the gas in the central region.

(cite: rhc_zubovas16) used an analytical model to follow the evolution of the molecular and ionized phases in an outflow driven by an AGN that ‘flickers’ on timescales of $5\times10^{4}$ yr. They find that the oscillations caused by the AGN flickering smooth out relatively fast ($\sim3$ Myr), so from an observational standpoint it would appear that the outflow is driven by an AGN with constant luminosity. For a massive galaxy similar to zC400528 (cite: rhc_moster13) the model predicts that in the outflow timescale of zC400528 ($\sim10^7$ yr) the wind should have expanded between $\sim4$ and 8 kpc with expansion velocities at that distance of $\sim300$ and 700 km s$^{-1}$ for AGN duty cycles of $f_{\rm AGN}=20\%$ and 100%, respectively. The observed extent ($\sim8$ kpc) and velocity ($\sim500$ km s$^{-1}$) in the molecular outflow of zC400528 is consistent with these model results and favors the scenario with a high AGN duty cycle, in agreement with the results of (cite: rhc_genzel14) and (cite: rhc_f-s18b).

## Is zC400528 moving down from the main-sequence of star-forming galaxies to join the population of compact, passive galaxies?

There is growing evidence that suggests that when massive, star-forming galaxies at $z\approx2$ reach central stellar surface densities similar to those observed in massive ellipticals at $z\approx0$ ($\Sigma_{\star}\gtrsim10^{10}$ M$_{\odot}$ kpc$^{-2}$ inside the inner $\sim$kiloparsec region), then an effective quenching mechanism must act on relatively short timescales to shut down the star formation activity (cite: rhc_tacchella15b). AGN-feedback, prevalent in massive $z\sim2$ galaxies (cite: rhc_genzel14; rhc_f-s18b), is one of the obvious quenching candidates.

zC400528 is one of the galaxies in the study of (cite: rhc_tacchella15b) that shows evidence for inside-out quenching on timescales $\lesssim1$ Gyr in the inner $\sim3$ kpc region. The fact that we detect a powerful nuclear outflow in zC400528 that is removing the molecular gas on a timescale of only half a billion years argues strongly in favor of the outflow as one of the main internal mechanisms responsible for the central suppression of the star formation activity. This conclusion is reinforced if we consider that the nuclear outflow is in reality not capable of clearing the whole galaxy of its star-forming material, but only the central region. If we recalculate the outflow depletion timescale only considering the molecular gas mass in the inner $\sim 4$ kpc region we obtain a depletion timescale that is a factor of $\sim3$ shorter ($t_{\rm dep,out}^{\rm 4~kpc}\approx1.5\times10^{8}$ yr). Note that for the nuclear outflow in zC400528 to be responsible for the quenching of the star-formation activity in the *entire* galaxy would require an efficient mode of “preventive” feedback, i.e., that the outflow injects enough energy into the halo to keep it hot, drastically reducing the accretion of gas into the disk, including the recycling of molecular gas expelled by the nuclear outflow (cite: rhc_gabor11; rhc_king15; rhc_costa17; rhc_dave17).

Keeping in mind the many uncertainties associated to the calculation of the mass outflow rate described in §4, we can attempt to further explore the quenching scenario with a simple back-of-the-envelope calculation. We start by estimating the balance of gas input and drainage $B={\rm inflow~rate/(outflow~rate + SFR)}$, which is one the key parameters regulating the movement of galaxies relative to the main-sequence. To calculate the inflow rate, we use the expression for the mean gas accretion rate in (cite: rhc_bouche10) (cite: rhc_lilly13):

$$\begin{equation}
\dot{M}_{\rm gas,in}\simeq 90~\epsilon_{\rm in}~f_{\rm b,0.18}~(M_{\rm h,12})^{1.1}~\bigg(\frac{1+z}{3.2}\bigg)^{2.2}~M_{\odot}~{\rm yr}^{-1},
\end{equation}$$

where $\epsilon_{\rm in}$ is the accretion efficiency, $f_{\rm b,0.18}$ ($\equiv f_{\rm b}/0.18$) is the cosmic baryonic fraction, and $M_{\rm h,12}$ $(\equiv M_{\rm h}/10^{12}~M_{\odot})$ is the mass of the halo. Assuming a fiducial value for the accretion efficiency of $\epsilon_{\rm in}=0.7$ (cite: rhc_bauermesiter10), a cosmic baryonic fraction of $f_{\rm b}=0.18$, and a halo mass of $M_{\rm h}\approx10^{12.5}~M_{\odot}$ (cite: rhc_moster13), we obtain a mean gas accretion rate for zC400528 of $\dot{M}_{\rm gas,in}\approx240~M_{\odot}~{\rm yr}^{-1}$. Then, the balance of gas input and drainage in zC400528 is

$$\begin{equation*}
B=\frac{240~M_{\odot}~{\rm yr}^{-1}}{(148+256)~M_{\odot}~{\rm yr}^{-1}}=0.6. 
\end{equation*}$$

From the scaling relation described in (cite: rhc_tacchella16) between the balance term $B$ (in the central 5 kpc) and the rate of change of distance from the main-sequence, $\dot{\Delta}_{\rm MS}$, we speculate that zC400528 is *moving down from* the main-sequence at a rate of $\dot{\Delta}_{\rm MS}\sim1$ dex Gyr$^{-1}$. At this rate, and ignoring other mechanisms that could contribute to the star formation activity on timescales $\lesssim1$ Gyr (e.g., re-accretion of ejected molecular gas expelled by the outflow; see §[5.1](#section:escape)), it should only take zC400538 about $\sim2$ Gyr to transition from the main-sequence to the regime of passive, quenched galaxies $\sim2$ dex below the main-sequence. This is consistent with the expectations from inside-out quenching that claims that massive, star-forming galaxies such as zC400528 should be fully quenched by $z\sim1$ ($\sim3$ Gyr later than the $z\sim2$ epoch).

# Conclusions

In this paper we use ALMA CO(3-2) observations to study the molecular gas properties of the disk and the AGN-driven outflow in zC400528, a *typical* massive galaxy at $z=2.3$ in the process of quenching (cite: rhc_tacchella15). We complement these observations with VLT/SINFONI adaptive-optics H$\alpha$ data (cite: rhc_f-s14; rhc_f-s18) which allowed us to conduct one of the first spatially-resolved, multi-phase studies of a galactic outflow at $z\sim2$.

We highlight the following points:

1.  **Molecular disk:** The molecular gas mass in the rotating disk of zC400528 (assuming a CO-to-H$_2$ conversion factor of $\alpha_{\rm CO(1-0),T18}=4.3~M_{\odot}~({\rm K~km~s^{-1}~pc^{-2}})^{-1}$) is $M_{\rm mol,disk}=1.1\times10^{11}$ $M_{\odot}$, which translates to a molecular gas to stellar ratio of $M_{\rm mol}/M_{\star}\approx1$. This high gas mass fraction is comparable to those observed in massive star-forming galaxies at $z\sim2$ (cite: rhc_genzel15; rhc_tacconi18).

2.  **Molecular outflow:** The molecular outflow in zC400528 is asymmetrical, with only its receding component detected out to a projected distance of $\sim10$ kpc. The bulk of the emission is concentrated in the nuclear region and aligned with the major kinematic axis of the disk. We observe a positive velocity gradient in the outflow with projected velocities that range from $\sim300$ km s$^{-1}$ in the nuclear part to $\sim400-500$ km s$^{-1}$ in the furthest components.

    We measure a molecular outflow mass and mass loss rate of $M_{\rm out,mol}=3.36\times10^{9}~M_{\odot}$ and $\dot{M}_{\rm out,mol}^{\rm avg}\approx256~M_{\odot}~{\rm yr^{-1}}$, respectively (these assume a ULIRG-like CO-to-H$_2$ conversion factor). With this powerful molecular mass loss rate zC400528 is depleting its nuclear molecular gas twice as fast as due to its star formation activity.

    The momentum boost in the molecular phase of the outflow is $\dot{P}_{\rm out,mol}/(L_{\rm AGN,bol}/c)\approx3$ and the energy flux is $\dot{E}_{\rm out,mol}\approx0.2\%L_{\rm AGN,bol}$, in agreement with theoretical expectations for an AGN-driven, energy-conserving outflow.

3.  **Molecular and ionized phases in the outflow:** The ionized and molecular phases of the outflow in zC400528 have different morphological properties. While the ionized outflow extends for $\sim4$ kpc from the nuclear region inclined about $60^{\circ}$ with respect to the major kinematic axis of the disk, the central component of the molecular outflow is found preferentially in between the ionized wind and the major kinematic axis. This type of configuration is not uncommon in AGN-driven outflows as found in observational and simulation studies (cite: rhc_garcia-burillo14; rhc_zubovas14a). We also observe that in the extended molecular component of the outflow ($\gtrsim5$ kpc) there are at least two regions (A and B in Fig. [11](#outflow_mom0)) where ionized and molecular gas are co-spatial and moving at similar high-velocities.

    Keeping in mind all the uncertainties that affect the determination of the ionized and molecular outflow properties (e.g., electron density, CO-to-H$_2$ conversion factor, geometry, etc.), both the mass and energetics of the outflow are dominated by the molecular phase. For the ionized phase to be dominant would require the combination of low electron densities and optically thin molecular gas in the wind. Both of these conditions seem unlikely (cite: rhc_aalto15; rhc_walter17; rhc_f-s18b). The mass loading factors ($\dot{M}_{\rm out}/{\rm SFR}$) of the molecular and ionized outflow phases are 1.7 and 0.4, respectively.

4.  **AGN-driven outflow quenching in action?** Kilo-parsec scale observations of the stellar content and the star formation activity in zC400528 reveal that one or more quenching mechanisms are shutting down the star formation activity from the inside-out on short timescales (cite: rhc_tacchella15b). The fact that we detect an AGN-driven outflow powerful enough to expel the star-forming material in the central region on short timescales ($t_{\rm dep,out}\sim0.2$ Gyr if we consider the molecular gas in the inner four kiloparsecs) points at the outflow as one of the main quenching engines at work. Although it is true that the expelled molecular gas is not fast enough to escape the system, the energy input of the outflow into the halo should reduce the accretion of both fresh and recycled gas into the disk, facilitating even more the transition of zC400528 into the realm of passive systems below the main-sequence of galaxies.

# Acknowledgments

RHC would like to thank the support and encouragement from Fares Bravo Garrido and dedicates this paper with love to Fares and Olivia. SGB thanks economic support from funding grant AYA2016-76682-C3-2-P. CF acknowledges support from the European Union Horizon 2020 research and innovation programme under the Marie Sklodowska-Curie grant agreement No 664931. LC acknowledges financial support by the Spanish Ministry for Science, Innovation and Universities under grants AYA2015-68964 and ESP2017-83197. The Cosmic Dawn Center is funded by the Danish National Research Foundation. This paper makes use of the following ALMA data: ADS/JAO.ALMA#2013.1.00092.S and #2015.1.00220.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada) and NSC and ASIAA (Taiwan) and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. This work is based on observations taken by the 3D-HST Treasury Program (GO 12177 and 12328) with the NASA/ESA HST, which is operated by the Association of Universities for Research in Astronomy, Inc., under NASA contract NAS5-26555.

# AGN bolometric luminosity of zC400528

Given the non-detection of zC400528 in X-ray emission described in §[1.1](#galaxy_info), we estimate its AGN bolometric luminosity in two ways: (1) We convert its SFR into a total infrared luminosity ($L_{\rm TIR}$) using the prescription by (cite: rhc_murphy11). Then, we use the common assumption that $L_{\rm bol}=1.15 L_{\rm TIR}$, and that a fraction $f_{\rm AGN}=0.5$ (cite: rhc_veilleux09) of $L_{\rm bol}$ is associated to the bolometric AGN luminosity. This results in $log_{10}(L_{\rm AGN, bol}/[{\rm erg~s}^{-1}])\approx45.3$. (2) We follow the methodology described in (cite: rhc_f-s18b) and use the \[N II\]$\lambda$6584 luminosity in the narrow component after subtracting the contribution by star-forming regions based on the mass-metallicity relation. The resulting AGN bolometric luminosity is $log_{10}(L_{\rm AGN, bol}/[{\rm erg~s}^{-1}])\approx46.1$, a factor of $\sim6$ higher than the TIR-based estimate in (1). In the analysis we use the average between these two values, i.e., $log_{10}(L_{\rm AGN, bol}/[{\rm erg~s}^{-1}])\approx45.8$.

natexlab

(ref: rhc_aalto12) Aalto, S., Garcia-Burillo, S., Muller, S., et al. 2012, A&A, 537, A44

(ref: rhc_aalto15) —. 2015, A&A, 574, A85

(ref: rhc_alatalo15) Alatalo, K. 2015, ApJL, 801, L17

(ref: rhc_a-c17) Anglés-Alcázar, D., Faucher-Giguère, C.-A., Kereš, D., et al. 2017, MNRAS, 470, 4698

(ref: rhc_arribas14) Arribas, S., Colina, L., Bellocchi, E., Maiolino, R., & Villar-Martı́n, M. 2014, A&A, 568, A14

(ref: rhc_barcos18) Barcos-Muñoz, L., Aalto, S., Thompson, T. A., et al. 2018, ApJL, 853, L28

(ref: rhc_barro16) Barro, G., Kriek, M., Pérez-González, P. G., et al. 2016, ApJL, 827, L32

(ref: rhc_bauermesiter10) Bauermeister, A., Blitz, L., & Ma, C.-P. 2010, ApJ, 717, 323

(ref: rhc_bolatto13) Bolatto, A. D., Wolfire, M., & Leroy, A. K. 2013a, ARA&A, 51, 207

(ref: rhc_bolatto13b) Bolatto, A. D., Warren, S. R., Leroy, A. K., et al. 2013b, Nature, 499, 450

(ref: rhc_bolatto15) —. 2015, ApJ, 809, 175

(ref: rhc_bouche10) Bouché, N., Dekel, A., Genzel, R., et al. 2010, ApJ, 718, 1001

(ref: rhc_cecil02) Cecil, G., Dopita, M. A., Groves, B., et al. 2002, ApJ, 568, 627

(ref: rhc_christensen16) Christensen, C. R., Davé, R., Governato, F., et al. 2016, ApJ, 824, 57

(ref: rhc_cicone12) Cicone, C., Feruglio, C., Maiolino, R., et al. 2012, A&A, 543, A99

(ref: rhc_cicone14) Cicone, C., Maiolino, R., Sturm, E., et al. 2014, A&A, 562, A21

(ref: rhc_concas17) Concas, A., Popesso, P., Brusa, M., et al. 2017, A&A, 606, A36

(ref: rhc_contursi13) Contursi, A., Poglitsch, A., Grácia Carpio, J., et al. 2013, A&A, 549, A118

(ref: rhc_costa17) Costa, T., Rosdahl, J., Sijacki, D., & Haehnelt, M. G. 2017, ArXiv e-prints, arXiv:1709.08638

(ref: rhc_daddi15) Daddi, E., Dannerbauer, H., Liu, D., et al. 2015, A&A, 577, A46

(ref: rhc_dannerbauer09) Dannerbauer, H., Daddi, E., Riechers, D. A., et al. 2009, ApJL, 698, L178

(ref: rhc_dasyra16) Dasyra, K. M., Combes, F., Oosterloo, T., et al. 2016, A&A, 595, L7

(ref: rhc_dave17) Davé, R., Rafieferantsoa, M. H., & Thompson, R. J. 2017, MNRAS, 471, 1671

(ref: rhc_dimatteo05) Di Matteo, T., Springel, V., & Hernquist, L. 2005, Nature, 433, 604

(ref: rhc_eisenhauer03) Eisenhauer, F., Abuter, R., Bickert, K., et al. 2003, in Proc. SPIE, Vol. 4841, Instrument Design and Performance for Optical/Infrared Ground-based Telescopes, ed. M. Iye & A. F. M. Moorwood, 1548–1561

(ref: rhc_elvis09) Elvis, M., Civano, F., Vignali, C., et al. 2009, ApJS, 184, 158

(ref: rhc_f-g12) Faucher-Giguère, C.-A., & Quataert, E. 2012, MNRAS, 425, 605

(ref: rhc_feruglio10) Feruglio, C., Maiolino, R., Piconcelli, E., et al. 2010, A&A, 518, L155

(ref: rhc_feruglio15) Feruglio, C., Fiore, F., Carniani, S., et al. 2015, A&A, 583, A99

(ref: rhc_fiore17) Fiore, F., Feruglio, C., Shankar, F., et al. 2017, A&A, 601, A143

(ref: rhc_fluetsch18) Fluetsch, A., Maiolino, R., Carniani, S., et al. 2018, ArXiv e-prints, arXiv:1805.05352

(ref: rhc_f-s14) Förster Schreiber, N. M., Genzel, R., Newman, S. F., et al. 2014, ApJ, 787, 38

(ref: rhc_f-s18b) Förster Schreiber, N. M., Übler, H., Davies, R. L., et al. 2018a, ArXiv e-prints, arXiv:1807.04738

(ref: rhc_f-s18) Förster Schreiber, N. M., Renzini, A., Mancini, C., et al. 2018b, ArXiv e-prints, arXiv:1802.07276

(ref: rhc_gabor14) Gabor, J. M., & Bournaud, F. 2014, MNRAS, 441, 1615

(ref: rhc_gabor11) Gabor, J. M., Davé, R., Oppenheimer, B. D., & Finlator, K. 2011, MNRAS, 417, 2676

(ref: rhc_garcia-burillo14) Garcı́a-Burillo, S., Combes, F., Usero, A., et al. 2014, A&A, 567, A125

(ref: rhc_genzel14) Genzel, R., Förster Schreiber, N. M., Rosario, D., et al. 2014, ApJ, 796, 7

(ref: rhc_genzel15) Genzel, R., Tacconi, L. J., Lutz, D., et al. 2015, ApJ, 800, 20

(ref: rhc_gonzalez-alfonso14) González-Alfonso, E., Fischer, J., Graciá-Carpio, J., et al. 2014, A&A, 561, A27

(ref: rhc_gonzalez-alfonso17) González-Alfonso, E., Fischer, J., Spoon, H. W. W., et al. 2017, ApJ, 836, 11

(ref: rhc_harrison16) Harrison, C. M., Alexander, D. M., Mullaney, J. R., et al. 2016, MNRAS, 456, 1195

(ref: rhc_heckman15) Heckman, T. M., Alexandroff, R. M., Borthakur, S., Overzier, R., & Leitherer, C. 2015, ApJ, 809, 147

(ref: rhc_janssen16) Janssen, A. W., Christopher, N., Sturm, E., et al. 2016, ApJ, 822, 43

(ref: rhc_kewley13) Kewley, L. J., Maier, C., Yabe, K., et al. 2013, ApJL, 774, L10

(ref: rhc_king15) King, A., & Pounds, K. 2015, ARA&A, 53, 115

(ref: rhc_kornei12) Kornei, K. A., Shapley, A. E., Martin, C. L., et al. 2012, ApJ, 758, 135

(ref: rhc_leroy15) Leroy, A. K., Walter, F., Martini, P., et al. 2015, ApJ, 814, 83

(ref: rhc_leung17) Leung, G. C. K., Coil, A. L., Azadi, M., et al. 2017, ApJ, 849, 48

(ref: rhc_lilly13) Lilly, S. J., Carollo, C. M., Pipino, A., Renzini, A., & Peng, Y. 2013, ApJ, 772, 119

(ref: rhc_maiolino12) Maiolino, R., Gallerani, S., Neri, R., et al. 2012, MNRAS, 425, L66

(ref: rhc_casa) McMullin, J. P., Waters, B., Schiebel, D., Young, W., & Golap, K. 2007, in Astronomical Society of the Pacific Conference Series, Vol. 376, Astronomical Data Analysis Software and Systems XVI, ed. R. A. Shaw, F. Hill, & D. J. Bell, 127

(ref: rhc_morganti16) Morganti, R., Veilleux, S., Oosterloo, T., Teng, S. H., & Rupke, D. 2016, A&A, 593, A30

(ref: rhc_moster13) Moster, B. P., Naab, T., & White, S. D. M. 2013, MNRAS, 428, 3121

(ref: rhc_muratov15) Muratov, A. L., Kereš, D., Faucher-Giguère, C.-A., et al. 2015, MNRAS, 454, 2691

(ref: rhc_murphy11) Murphy, E. J., Condon, J. J., Schinnerer, E., et al. 2011, ApJ, 737, 67

(ref: rhc_muzzin13) Muzzin, A., Marchesini, D., Stefanon, M., et al. 2013, ApJ, 777, 18

(ref: rhc_nardini15) Nardini, E., Reeves, J. N., Gofford, J., et al. 2015, Science, 347, 860

(ref: rhc_nelson16) Nelson, E. J., van Dokkum, P. G., Förster Schreiber, N. M., et al. 2016, ApJ, 828, 27

(ref: rhc_newman13) Newman, S. F., Genzel, R., Förster Schreiber, N. M., et al. 2013, ApJ, 767, 104

(ref: rhc_newman14) Newman, S. F., Buschkamp, P., Genzel, R., et al. 2014, ApJ, 781, 21

(ref: rhc_oppenheimer10) Oppenheimer, B. D., Davé, R., Kereš, D., et al. 2010, MNRAS, 406, 2325

(ref: rhc_p-s18) Pereira-Santaella, M., Colina, L., Garcia-Burillo, S., et al. 2018, ArXiv e-prints, arXiv:1805.03667

(ref: rhc_pp04) Pettini, M., & Pagel, B. E. J. 2004, MNRAS, 348, L59

(ref: rhc_richings18) Richings, A. J., & Faucher-Giguère, C.-A. 2018, MNRAS, 474, 3673

(ref: rhc_r-z13) Rodrı́guez Zaurı́n, J., Tadhunter, C. N., Rose, M., & Holt, J. 2013, MNRAS, 432, 138

(ref: rhc_rupke02) Rupke, D. S., Veilleux, S., & Sanders, D. B. 2002, ApJ, 570, 588

(ref: rhc_rupke05) —. 2005, ApJ, 632, 751

(ref: rhc_rupke11) Rupke, D. S. N., & Veilleux, S. 2011, ApJL, 729, L27

(ref: rhc_schawinski15) Schawinski, K., Koss, M., Berney, S., & Sartori, L. F. 2015, MNRAS, 451, 2517

(ref: rhc_schinnerer10) Schinnerer, E., Sargent, M. T., Bondi, M., et al. 2010, ApJS, 188, 384

(ref: rhc_silk98) Silk, J., & Rees, M. J. 1998, A&A, 331, L1

(ref: rhc_skelton14) Skelton, R. E., Whitaker, K. E., Momcheva, I. G., et al. 2014, ApJS, 214, 24

(ref: rhc_springel05) Springel, V., Di Matteo, T., & Hernquist, L. 2005, ApJL, 620, L79

(ref: rhc_sturm11) Sturm, E., González-Alfonso, E., Veilleux, S., et al. 2011, ApJL, 733, L16

(ref: rhc_tacchella16) Tacchella, S., Dekel, A., Carollo, C. M., et al. 2016, MNRAS, 457, 2790

(ref: rhc_tacchella15b) Tacchella, S., Carollo, C. M., Renzini, A., et al. 2015a, Science, 348, 314

(ref: rhc_tacchella15) Tacchella, S., Lang, P., Carollo, C. M., et al. 2015b, ApJ, 802, 101

(ref: rhc_tacconi10) Tacconi, L. J., Genzel, R., Neri, R., et al. 2010, Nature, 463, 781

(ref: rhc_tacconi13) Tacconi, L. J., Neri, R., Genzel, R., et al. 2013, ApJ, 768, 74

(ref: rhc_tacconi18) Tacconi, L. J., Genzel, R., Saintonge, A., et al. 2018, ApJ, 853, 179

(ref: rhc_tecza01) Tecza, M., Thatte, N., & Maiolino, R. 2001, in IAU Symposium, Vol. 205, Galaxies and their Constituents at the Highest Angular Resolutions, ed. R. T. Schilizzi, 216

(ref: rhc_tombesi15) Tombesi, F., Meléndez, M., Veilleux, S., et al. 2015, Nature, 519, 436

(ref: rhc_uebler14) Übler, H., Naab, T., Oser, L., et al. 2014, MNRAS, 443, 2092

(ref: rhc_vdv11) van de Voort, F., Schaye, J., Booth, C. M., Haas, M. R., & Dalla Vecchia, C. 2011, MNRAS, 414, 2458

(ref: rhc_veilleux17) Veilleux, S., Bolatto, A., Tombesi, F., et al. 2017, ApJ, 843, 18

(ref: rhc_veilleux05) Veilleux, S., Cecil, G., & Bland-Hawthorn, J. 2005, ARA&A, 43, 769

(ref: rhc_veilleux09) Veilleux, S., Rupke, D. S. N., Kim, D.-C., et al. 2009, ApJS, 182, 628

(ref: rhc_veilleux13) Veilleux, S., Meléndez, M., Sturm, E., et al. 2013, ApJ, 776, 27

(ref: rhc_walter17) Walter, F., Bolatto, A. D., Leroy, A. K., et al. 2017, ApJ, 835, 265

(ref: rhc_woo16) Woo, J.-H., Bae, H.-J., Son, D., & Karouzos, M. 2016, ApJ, 817, 108

(ref: rhc_zubovas12) Zubovas, K., & King, A. 2012, ApJL, 745, L34

(ref: rhc_zubovas16) —. 2016, MNRAS, 462, 4055

(ref: rhc_zubovas14a) Zubovas, K., & King, A. R. 2014, MNRAS, 439, 400

(ref: rhc_zubovas14b) Zubovas, K., & Nayakshin, S. 2014, MNRAS, 440, 2625

[^1]: Position of CO(3-2) peak.

[^2]: For more details see: <https://casaguides.nrao.edu/index.php/DataWeightsAndCombination>

[^3]: This measurement does not include the contribution of the outflow to the CO(3-2) emission. Please see § [3.2.1](#separation) for a description of how the molecular gas emission of the disk and the outflow was disentangled.

[^4]: The $\alpha_{\rm CO}$ conversion function in (cite: rhc_tacconi18) corresponds to the geometric mean between the $\alpha_{\rm CO}$ recipes as a function of metallicity of (cite: rhc_bolatto13) and (cite: rhc_genzel15). zC400528 is a massive ($M_{*}=1.1\times10^{11}~M_{\odot}$), main-sequence galaxy at $z=2.38$ that according to the scaling relations in (cite: rhc_tacconi18) has a metallicity near solar ($12+log(\rm O/H)=8.6$) in the (cite: rhc_pp04) scale.

[^5]: The calculation of the molecular gas mass includes a helium correction factor of 1.36.

[^6]: According to the ALMA Technical Handbook, Chapter 10.6.6, Astrometric Observations

[^7]: Note that for the bodies of starburst and (U)LIRGs drawn from the literature that are outliers in the local main-sequence relation ($\Delta_{\rm MS}\gtrsim1$ dex) we use the CO-to-H$_{2}$ conversion factor from the scaling relation in (cite: rhc_genzel15) to calculate their molecular gas masses. This conversion factor is a factor $\sim2$ lower for starbursts and (U)LIRGs galaxies depending on their specific star formation rate, and similar to that in (cite: rhc_tacconi18) for main-sequence galaxies.

[^8]: The ionized gas outflow masses reported in (cite: rhc_genzel14) are calculated assuming $n_{\rm e}=80$ cm$^{-3}$ in the ionized outflowing gas. Here we rescaled those values to match our assumption of $n_{\rm e}=300$ cm$^{-3}$.

[^9]: The escape velocity is only weakly sensitive to the exact value of $r_{\rm max}/r$.

</paper>

## Items to check

```json
[
 {
  "path": "claims[2].evidence[0]",
  "value": "Outflow is one of the main quenching engines",
  "failed_quote": "depleting the molecular gas reservoir on a timescale at least twice shorter than that needed to exhaust it by star formation"
 },
 {
  "path": "analysis_steps[2].fitting.evidence[0]",
  "value": "2D Gaussian per channel",
  "failed_quote": "(no quote given)"
 }
]
```
