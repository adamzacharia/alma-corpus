# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2026ApJ..1006...39W\gemini4argon\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
# ASPIRE: The Environments and Dark Matter Halos of Luminous Quasars in the Epoch of Reionization

## Abstract

We present a systematic study of the environments of 25 luminous quasars at $z > 6.5$ from the ASPIRE program. Using JWST/NIRCam WFSS data, we identified 487 galaxies at $5.3 \lesssim z \lesssim 7.0$ exhibiting \[O III\] emission. Among these, 122 \[O III\] emitters lie within $|\Delta v_{\rm los}| < 1000~\mathrm{km~s^{-1}}$ of the quasars, corresponding to a $\sim9.4$-fold enhancement relative to the average galaxy density at other redshifts. Furthermore, we identified 16 \[C II\]-emitting galaxies at the quasar redshifts from ALMA mosaic observations. A cross-correlation function (CCF) analysis between quasars and \[O III\]+\[C II\] emitters yields a cross-correlation length of $r_0^{\rm QG} = 8.68^{+0.51}_{-0.55}~h^{-1}~\mathrm{cMpc}$ and a auto-correlation of $r_0^{\rm{QQ}}=15.76^{+2.48}_{-2.70}~h^{-1}~{\rm cMpc}$, indicating that $z \sim 7$ quasars reside in dark matter halos with $M_{\rm halo} = 10^{12.27^{+0.21}_{-0.26}}~M_\odot$ and has a quasar lifetime of $t_{\rm Q}=\rm 10^{{7.05}^{+0.95}_{-1.01}}~yr$. Notably, the number of \[O III\]-emitting galaxies at quasar redshifts varies significantly from field to field, ranging from zero to twenty, highlighting a diverse quasar environment. Remarkably, seven quasars trace significant galaxy overdensities (i.e., protoclusters), with $\delta_{\rm gal} > 5$ within a volume of $V \sim 500~{\rm cMpc^3}$. We also find that $|\Delta v_{\rm los}|$ increases rapidly toward smaller galaxy-quasar separations in protocluster fields, consistent with galaxy kinematics around extremely massive halos in cosmological simulations. By combining JWST and ALMA data, we reveal the complex and diverse environments of these early quasars, providing robust evidence that the earliest luminous quasars are effective tracers of galaxy overdensities, albeit with substantial field-to-field variation.

# Introduction

Understanding the formation of the earliest supermassive black holes (SMBHs) has been one of the frontiers of extragalactic astronomy. Since the discovery of the first $z > 6$ quasar (cite: Fan01), over two decades of painstaking searches have yielded a sample of $\sim$50 luminous quasars with absolute magnitudes of $M_{\rm 1450}\lesssim -25$ at $z > 6.5$, extending up to the current redshift record at $z = 7.6$ (cite: Wang21a). The existence of these quasars powered by $\sim10^9$ $M_\odot$ black holes (cite: Banados18a; Yang20a; Yang21; Farina22) during the Epoch of Reionization (EoR) challenges our understanding of supermassive black hole (SMBH) formation, and implies that these quasars must have grown rapidly within the first few hundred million years after the Big Bang. Such rapid growth requires either the formation of massive seed black holes, such as those formed via direct collapse (cite: Begelman06) or through dense stellar clusters (cite: Portegies04) , or sustained periods of accretion at or above the Eddington limit from smaller seeds (cite: Madau01). However, such conditions are difficult to achieve and maintain, given the expected low gas densities, strong radiative feedback from the central SMBHs, and short available timescales in the early Universe. Together with the low space density (cite: Wang19b) and large black hole masses of luminous quasars (cite: Yang21; Farina22) , most theoretical works favor the idea that the most distant luminous quasars reside in massive dark matter halos and can be traced by large-scale galaxy overdensities (cite: Costa14; DiMatteo17). Such environments can provide mechanisms that suppress cooling and fragmentation, enabling the formation of massive black hole seeds, and offer sufficient gas supplies to sustain continuous black hole growth (cite: Inayoshi20).

Indeed, an assortment of cosmological simulation models can produce such massive SMBHs (cite: DiMatteo05; Khandai15; DiMatteo17) powering quasars with roughly the observed abundance $0.4~{\rm Gpc}^{-3}$ (cite: Wang19b) starting with massive $\gtrsim 10^4~M_\odot$ seed BHs. These models generically predict that these SMBHs are hosted by massive $M_\star \gtrsim 10^{11}M_\odot$ galaxies and reside in the rarest $M_{\rm DM} > 10^{12}M_\odot$ dark matter halos situated in the most overdense regions in the early Universe (cite: Costa14). While these numerical works have established the plausibility of the existence of $z\sim7$ quasars in a cosmological context, to date, rigorously testing these theories remains highly challenging. Specifically, the following two critical questions need to be resolved observationally in order to test these theoretical works: (1) In which dark matter halos and large-scale environments do these SMBHs live? (2) Do the earliest supermassive black holes coevolve with their host galaxies?

If distant quasars inhabit massive dark-matter halos, they are expected to be good tracers of galaxy overdensities or protoclusters in the early Universe (cite: Overzier22). Extensive studies have been made in the past two decades for searching for galaxy overdensities around $z\gtrsim6$ quasars, however, no conclusive results have emerged from HST or ground-based observations (cite: Kim09; Simpson14; Mignoli20; Pudoka24). On the other hand, recent ALMA \[C II\] surveys have revealed key insights into the environments of high-redshift quasars (cite: Decarli17; Trakhtenbrot17; Neeleman19b; Nguyen20; Venemans20; Meyer22; Wang23; Wang24a). Notably, (cite: Meyer22) found a striking overdensity of \[C II\] emitters around $z>6$ quasars, with number densities several orders of magnitude above that of blank-field survey results, far exceeding results from UV- or optically-bright galaxies (cite: Pudoka24; Mignoli20). However, these ALMA studies typically probe only the immediate vicinity ($<1$ cMpc) with single-pointing ALMA observations, limiting the ability to distinguish small-scale mergers from the large-scale environment that traces massive dark matter halos. In addition, the small field of view of ALMA and the shallow depth of existing observations could introduce additional geometrical and luminosity biases, affecting our ability to interpret the scatter in the number of detected satellite galaxies (cite: Zana22; Zana23).

More recently, infrared surveys enabled by the wide-field slitless spectroscopy (WFSS) with JWST NIRCam is changing the game. The recent EIGER project enabled the first study of the clustering of galaxies around $z\sim 6$ quasars. It measured the quasar-galaxy cross-correlation function around four quasars and determined quasars’ host dark matter halos to be ${\rm log}~M_{\rm halo}=12.43^{+0.13}_{-0.15}~{\rm M_\odot}$ (cite: Eilers24). (cite: Schindler26) also attempted to constrain the host dark matter halos of $z>7$ quasars using two quasar fields observed with NIRCam imaging and NIRSpec/MSA follow-up spectroscopy. However, this measurement is significantly affected by cosmic variance due to the limited number of quasar sightlines used in these works.

The ASPIRE program, short for “A Spectroscopic Survey of Biased Halos in the Reionization Era" (GO-2078; PI Wang), is designed to overcome the above limitations. ASPIRE is a JWST quasar legacy survey which targets a sample of 25 luminous quasars at redshift between 6.5 and 6.8. Exploiting the excellent sensitivity of NIRCam/WFSS at $\sim3-4~\mu$m, ASPIRE aims to detect a large sample of star-forming galaxies with strong \[O III\] emission lines at $5.3\lesssim z \lesssim7$ along these quasar sight lines. In particular, ASPIRE obtains a complete sample of galaxies at the quasar redshifts down to a line flux limit of $\rm\sim2\times10^{-18}~erg~s^{-1}~cm^{-2}$. In addition, ASPIRE enables identification of galaxies from the local Universe up to $z\sim9$ using other line tracers (e.g., Pa$\alpha$, \[S III\], He I, Pa$\beta$, \[O II\]). Furthermore, ASPIRE includes coordinated NIRISS parallel imaging observations, which detects additional galaxies photometrically. Finally, ASPIRE is accompanied by an ALMA large program (Program ID:2022.1.01077.L; PI: Wang) which performs mosaic observations around these 25 quasars at 1mm. The ALMA observations are designed for detecting \[C II\] emitting galaxies at the quasar redshifts and dusty star-forming galaxies at both low- and high-redshifts.

A series of studies using ASPIRE data has already been published. For instance, (cite: Wang23) reported the discovery of a protocluster around one ASPIRE quasar; (cite: Yang23) analyzed the rest-frame optical spectral properties of a sample of ASPIRE quasars; (cite: Wu23) and (cite: Zou24) investigated the host galaxies of some metal absorbers and their circumgalactic medium (CGM) properties; (cite: Lin24) reported a sample of broad-line H$\alpha$ emitters in the early Universe; (cite: Jin24) and (cite: Kakiichi25) found direct evidence of early reionization around \[O III\] emitting galaxies; (cite: Champagne24a; Champagne24b) studied the structure of the protocluster discovered by (cite: Wang23) and environment-dependent galaxy evolution; (cite: Sun25) measured the obscured cosmic star formation rate density using a spectroscopically complete sample of galaxies at $z \simeq 4-6$; and (cite: Li25a; Li25b) studied the metal enrichment history of galaxies from the local universe up to redshift $z\sim9$.

In this paper, we provide an overview of the ASPIRE program, present data reduction procedures of JWST NIRCam and ALMA observations, report the discovery of 487 star-forming galaxies with \[O III\] emission lines at $5<z<7$ and 14 galaxies with \[C II\] emission lines at the quasar redshifts, and provide a detailed study of the environment and the dark matter halo mass of the ASPIRE quasars by combing JWST and ALMA observations. Throughout the paper, we adopt a $\Lambda$CDM cosmology with $H_0=70~{\rm km~s^{-1}~Mpc^{-1}}$, $\rm \Omega_M=0.3$, and $\Omega_\Lambda=0.7$. In this paper, we organize as follows: we present an overview of the ASPIRE program and the data used for this work in §[2](#sec:obs), show the \[O III\] emitting galaxy searching algorithms and report the discovery of 487 \[O III\] emitting galaxies in §[3](#sec:emitters), we also report the discovery of the \[C II\] emitting galaxies found at quasar redshifts in §[3](#sec:emitters), present clustering analyses for both \[O III\] emitting galaxies and \[C II\] emitting galaxies in §[4](#sec:clustering) and investigate the diversity of quasar environments and discuss implementations in §[5](#sec:environment), and summarize in §[6](#sec:summary).

![](fig_m1450.pdf)

| ID | $z$ | $M_{1450}$ | $L_{\rm bol}$ | $M_{\rm BH}$ | Disc. Ref. | $z$ Ref. | Ref. | Obs. ID |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
|  |  |  | $\rm 10^{46}~erg~s^{-1}$ | $\rm 10^9~M_\odot$ |  |  |  |  |  |  |  |  |  |  |
| \(1\) | \(2\) | \(3\) | \(4\) | \(5\) | \(6\) | \(7\) | \(8\) | \(9\) |  |  |  |  |  |  |
| J0109$-$3047 | 6.7904 | $-$25.41 | 7.69$\pm$0.20 | 1.11$\pm$0.40 | (cite: Venemans13) | (cite: Venemans20) | (cite: Farina22) | 1 |  |  |  |  |  |  |
| J0218$+$0007 | 6.7700 | $-$25.55 | 6.40$\pm$1.40 | 0.61$\pm$0.07 | (cite: Yang21) | (cite: Wang24b) | (cite: Yang21) | 2 |  |  |  |  |  |  |
| J0224$-$4711 | 6.5222 | $-$26.67 | 33.6$\pm$2.0 | 1.30$\pm$0.18 | (cite: Reed17) | (cite: Wang24b) | (cite: Wang21b) | 3 |  |  |  |  |  |  |
| J0226$+$0302 | 6.5405 | $-$27.15 | 24.96$\pm$0.15 | 3.74$\pm$0.59 | (cite: Venemans15a) | (cite: Venemans20) | (cite: Farina22) | 4 |  |  |  |  |  |  |
| J0229$-$0808 | 6.7249 | $-$25.68 | 10.47$\pm$0.24 | 0.38$\pm$0.02 | (cite: Belladitta25) | (cite: Wang24b) | (cite: Belladitta25) | 5 |  |  |  |  |  |  |
| J0244$-$5008 | 6.7240 | $-$26.72 | 14.4$\pm$0.2 | 1.15$\pm$0.39 | (cite: Reed19) | (cite: Reed19) | (cite: Reed19) | 6 |  |  |  |  |  |  |
| J0305$-$3150 | 6.6139 | $-$25.91 | 9.42$\pm$0.12 | 0.54$\pm$0.12 | (cite: Venemans19) | (cite: Venemans20) | (cite: Farina22) | 7 |  |  |  |  |  |  |
| J0430$-$1445 | 6.7142 | $-$25.82 | 10.23$\pm$0.24 | 1.29$\pm$0.03 | (cite: Belladitta25) | (cite: Wang24b) | (cite: Belladitta25) | 8 |  |  |  |  |  |  |
| J0525$-$2406 | 6.5397 | $-$25.47 | 6.8$\pm$3.5 | 0.29$\pm$0.04 | (cite: Yang21) | (cite: Wang24b) | (cite: Yang21) | 9 |  |  |  |  |  |  |
| J0706$+$2921 | 6.6037 | $-$27.44 | 33.9$\pm$1.5 | 2.11$\pm$0.16 | (cite: Wang19b) | (cite: Wang24b) | (cite: Yang21) | 10 |  |  |  |  |  |  |
| J0910$+$1656 | 6.7289 | $-$25.34 | 5.3$\pm$0.6 | 0.41$\pm$0.03 | (cite: Wang19b) | (cite: Wang24b) | (cite: Yang21) | 111 |  |  |  |  |  |  |
| J0910$-$0414 | 6.6363 | $-$26.61 | 15.0$\pm$1.1 | 3.59$\pm$0.61 | (cite: Wang19b) | (cite: Wang24b) | (cite: Yang21) | 12 |  |  |  |  |  |  |
| J0921$+$0007 | 6.5646 | $-$25.19 | 6.1$\pm$0.6 | 0.26$\pm$0.01 | (cite: Yang21) | (cite: Wang24b) | (cite: Yang21) | 13 |  |  |  |  |  |  |
| J0923$+$0402 | 6.6330 | $-$26.68 | 21.7$\pm$3.0 | 1.77$\pm$0.02 | (cite: Wang19b) | (cite: Wang24b) | (cite: Yang21) | 14 |  |  |  |  |  |  |
| J0923$+$0753 | 6.6817 | $-$25.50 | 4.9$\pm$2.0 | 0.49$\pm$0.15 | (cite: Yang21) | (cite: Wang24b) | (cite: Yang21) | 15 |  |  |  |  |  |  |
| J1048$-$0109 | 6.6759 | $-$26.20 | 10.55$\pm$0.30 | 2.29$\pm$0.64 | (cite: Wang17) | (cite: Venemans20) | (cite: Farina22) | 16 |  |  |  |  |  |  |
| J1058$+$2930 | 6.5846 | $-$25.68 | 5.8$\pm$1.5 | 0.54$\pm$0.03 | (cite: Yang21) | (cite: Wang24b) | (cite: Yang21) | 17 |  |  |  |  |  |  |
| J1104$+$2134 | 6.7662 | $-$26.63 | 15.1$\pm$0.9 | 1.69$\pm$0.15 | (cite: Wang19b) | (cite: Wang24b) | (cite: Yang21) | 18 |  |  |  |  |  |  |
| J1110$-$1329 | 6.5144 | $-$25.35 | 5.5$\pm$0.6 | 0.38$\pm$0.14 | (cite: Venemans15a) | (cite: Venemans20) | (cite: Wang21b) | 19 |  |  |  |  |  |  |
| J1129$+$1846 | 6.8240 | $-$25.73 | 8.4$\pm$1.9 | 0.29$\pm$0.02 | (cite: Banados21) | (cite: Yang21) | (cite: Yang21) | 20 |  |  |  |  |  |  |
| J1526$-$2050 | 6.5869 | $-$27.07 | 22.34$\pm$0.54 | 4.06$\pm$1.00 | (cite: Mazzucchelli17) | (cite: Venemans20) | (cite: Farina22) | 71 |  |  |  |  |  |  |
| J2002$-$3013 | 6.6876 | $-$26.90 | 15.4$\pm$1.9 | 1.62$\pm$0.27 | (cite: Yang21) | (cite: Wang24b) | (cite: Yang21) | 22 |  |  |  |  |  |  |
| J2102$-$1458 | 6.6645 | $-$25.53 | 6.0$\pm$0.5 | 0.74$\pm$0.11 | (cite: Wang19b) | (cite: Wang24b) | (cite: Yang21) | 23 |  |  |  |  |  |  |
| J2132$+$1217 | 6.5872 | $-$26.89 | 20.04$\pm$0.21 | 1.13$\pm$0.14 | (cite: Mazzucchelli17) | (cite: Venemans20) | (cite: Farina22) | 124 |  |  |  |  |  |  |
| J2232$+$2930 | 6.6660 | $-$26.26 | 10.0$\pm$1.7 | 3.06$\pm$0.36 | (cite: Venemans15a) | (cite: Mazzucchelli17) | (cite: Yang21) | 25 |  |  |  |  |  |  |

: ASPIRE Quasar Sample.

Table notes: $^{}$ (1): ID for ASPIRE quasar fields determined from quasar coordinates (i.e., JHHMM+/-DDMM). (2): The most accurate redshift measured for each quasar, mostly determined from \[C II\] observations. (3): The absolute magnitude at rest-frame 1450 $\rm \AA$ of each quasar. (4): The bolometric luminosity of each quasar. (5): The black hole mass of each quasar. (6): References for quasar discoveries. (7): References for quasar redshifts. (8): References for $M_{1450}$, bolometric luminosity and black hole mass. (9): JWST observation ID in ASPIRE program.

# ASPIRE Program Design and Observations

## Overview

As discussed in §[1](#sec:intro), one of the key science drivers of the ASPIRE program is to probe the large-scale environment and the dark matter halos of the earliest quasars. A fundamental result of the $\rm \Lambda$CDM structure formation paradigm is that the clustering of a population can be directly related to their host dark halo masses (cite: Mo02). However, the extremely low density of $z\simeq7$ quasars precludes the possibility of measuring their auto-correlation function. A complementary approach for determining quasar host halo masses is to measure the clustering of galaxies around them. If quasars and galaxies trace the same dark matter overdensities, the quasar-galaxy cross-correlation $\xi_{\rm QG}(r)$, can be uniquely predicted given the respective auto-correlation of quasars $\xi_{\rm QQ}$ and galaxies $\xi_{\rm GG}$ (cite: Garcia17). The key requirement on measuring the quasar-galaxy cross-correlation at high-redshift is to spectroscopically identify faint galaxies around quasars. Therefore, a spectroscopic redshift survey around a statistical sample of distant quasars is critically needed. Recent observations of high-$z$ galaxies suggest that young (1–10 Myr) stellar populations produce strong H$\beta$+\[O III\] lines (cite: Endsley21). This motivated us observing quasars at $6.5<z\lesssim6.8$, putting them at the sweet-spot of NIRCam/WFSS sensitivity (with the F356W filter) to the H$\beta$+\[O III\] of physically associated galaxies. In addition, such redshift cuts enables us finding galaxies associated to the full path-length of the Ly$\alpha$ and Ly$\beta$ transmission spikes and identifying host galaxies of metal absorbers at $z>5.3$ (with H$\beta$+\[O III\] lines) and at $z>4$ (with the H$\alpha$ line).

![](fig_nircam_dither.png)

The ASPIRE program aims to study the most luminous quasars, which potentially host the most extreme supermassive black holes (SMBHs) in the early Universe. To achieve this goal, we selected all quasars with $M_{\rm 1450} < -25$ at $6.5 < z \lesssim 6.8$ known at the time of the JWST Cycle 1 proposal deadline (Fig. [1](#fig:sample)). Additionally, we only targeted quasars with declinations less than $+30^\circ$, allowing us to utilize ALMA to identify dusty galaxies that could be missed by JWST observations. These selection criteria yield a sample of 25 quasars, large enough to minimize uncertainties caused by cosmic variance. Because we did not apply any cuts based on the quasars’ physical properties (except for luminosity), this selection also helps reduce potential sample selection biases in measurements of quasar dark matter halo masses. Since this work considers only quasars with $M_{1450} < -25$, the conclusions drawn here are applicable exclusively to these extremely luminous objects. Notably, the sample includes the only radio-loud quasar at $z > 6.5$ (cite: Banados21) known at that time, highlighted in Figure [1](#fig:sample) (red asterisk). We list the basic properties of all ASPIRE quasars in Table [\[tbl:targets\]](#tbl:targets) and provide detailed descriptions of our JWST observations in the following subsections.

## JWST observations

We utilize the NIRCam WFSS observation mode instead of NIRCam pre-imaging followed by NIRSpec/MSA observations for the ASPIRE program to select objects with strong emission lines. We used the F356W filter for the WFSS observation in the long wavelength (LW) channel, which provides a spectral wavelength coverage of $\sim3-4\mu$m. We simultaneously obtain F200W imaging in the short wavelength channel (SW). For most of the targets, except for J0910–0414, we choose the 3-point `INTRAMODULEX` primary dither pattern to cover the detector gaps in SW. In order to improve the PSF sampling, each primary position includes two sub-pixel dithers (Figure. [2](#fig:dither)). Such a dither pattern provides a survey area of $\sim$11 arcmin$^2$. For J0910–0414, we use a slightly different 4-point `INTRAMODULEX` primary dither pattern and each primary position includes two sub-pixel dithers. Each quasar was placed at a carefully designed position ($\rm X_{offset}=-60.5\ensuremath{''}$, $\rm Y_{offset}=7.5\ensuremath{''}$) in module A to ensure that we have full wavelength coverage and sufficient imaging depth for the target quasar and its vicinity (see Figure [2](#fig:dither)). We used the `SHALLOW4` readout pattern with nine groups and one integration for all observations. This configuration yields a total on-source exposure time of 3779.3s for the J0910–0414 field and 2834.5 s for all other fields.

We obtained both direct and out-of-field imaging using the F115W filter in the SW channel and the F356W filter in the LW channel. The same readout pattern as adopted for the main WFSS observations was employed. The total on-source integration times are 1417.3 s near the quasar and 472.4 s at the field edge, where the coverage is limited to a single exposure, for both the F115W and F356W bands.

In addition, ASPIRE performs NIRISS observations in parallel to expand the imaging coverage around the quasars. These observations are configured with the F356W and F444W filters. Combined with ground-based optical imaging, the NIRISS data are designed to enable the photometric selection of H$\beta$+\[O III\] emitters at $z \gtrsim 6.5$ using the $m_{\mathrm{356W}} - m_{\mathrm{444W}}$ color (cite: Smit15). The detailed description of the NIRISS and ground-based multi-wavelength observations, as well as their analysis, will be presented in a future publication and is beyond the scope of this work. We note that the initial observations for three ASPIRE quasar fields (J0910$+$1656, J1526$-$2050, and J2132$+$1217) failed due to guide star acquisition issues and were rescheduled for later execution. The observation IDs for all ASPIRE fields are listed in Table [\[tbl:targets\]](#tbl:targets).

|    Field     | Obs. Date  | F115W | F200W | F356W |
|:------------:|:----------:|:-----:|:-----:|:-----:|
| J0109$-$3047 | 2022-08-11 | 27.75 | 28.43 | 28.62 |
| J0218$+$0007 | 2022-08-10 | 27.57 | 28.22 | 28.46 |
| J0224$-$4711 | 2022-08-11 | 27.54 | 28.08 | 28.35 |
| J0226$+$0302 | 2022-08-10 | 27.64 | 28.35 | 28.58 |
| J0229$-$0808 | 2022-08-16 | 27.64 | 28.23 | 28.55 |
| J0244$-$5008 | 2022-08-11 | 27.84 | 28.35 | 28.69 |
| J0305$-$3150 | 2022-08-12 | 27.78 | 28.45 | 28.70 |
| J0430$-$1445 | 2022-09-11 | 27.68 | 28.24 | 28.56 |
| J0525$-$2406 | 2022-10-12 | 27.68 | 28.18 | 28.51 |
| J0706$+$2921 | 2022-10-18 | 27.49 | 28.09 | 28.20 |
| J0910$+$1656 | 2023-11-22 | 27.44 | 28.26 | 28.14 |
| J0910$-$0414 | 2022-11-13 | 27.51 | 28.26 | 28.41 |
| J0921$+$0007 | 2022-11-29 | 27.65 | 28.30 | 28.58 |
| J0923$+$0402 | 2022-11-29 | 27.69 | 28.31 | 28.55 |
| J0923$+$0753 | 2023-03-30 | 27.70 | 28.26 | 28.52 |
| J1048$-$0109 | 2023-04-27 | 27.71 | 28.31 | 28.55 |
| J1058$+$2930 | 2023-04-27 | 27.77 | 28.39 | 28.76 |
| J1104$+$2134 | 2022-11-28 | 27.57 | 28.29 | 28.42 |
| J1110$-$1329 | 2023-06-18 | 27.52 | 28.19 | 28.01 |
| J1129$+$1846 | 2023-06-07 | 27.48 | 28.23 | 28.15 |
| J1526$-$2050 | 2023-03-03 | 27.52 | 28.19 | 28.35 |
| J2002$-$3013 | 2022-09-22 | 27.54 | 28.09 | 28.32 |
| J2102$-$1458 | 2022-09-23 | 27.53 | 28.13 | 28.47 |
| J2132$+$1217 | 2023-10-10 | 27.15 | 27.65 | 27.81 |
| J2232$+$2930 | 2022-08-10 | 27.76 | 28.33 | 28.72 |

## NIRCam imaging data reduction

The NIRcam images were reduced using version 1.10.2 of the JWST Calibration Pipeline[^1](`CALWEBB`). We used the reference files (`jwst_1080.pmap`) from version 11.16.21 of the standard Calibration Reference Data System (CRDS) to calibrate our data. In addition to the standard processes, we introduced several additional steps as detailed in (cite: Wang23) and (cite: Yang23) and describe them briefly below. We modeled the *1/f* noise from the background subtracted `rate` files (`rate` files are Stage 1 outputs) on a row-by-row and column-by-column basis for each amplifier following the algorithm proposed by (cite: Schlawin2020). The background for the `rate` files was determined iteratively after masking out detected objects in the images. The *1/f* noise subtracted `rate` files were then fed into the Stage 2 pipeline. To remove extra detector-level noise features and sky background, we subtracted a master background from individual Stage 2 outputs, where the master background for each NIRCam detector was constructed from all exposures observed at a similar time. To remove astrometric offsets between individual exposures / detectors, we aligned individual images to stars selected from GAIA DR3[^2]. Since there are too few available reference stars in individual images (especially SW images), we first passed through all LW images for each quasar fields to Stage 3 pipeline to create an initial mosaic image. The initial mosaic image was aligned to GAIA DR3 using `tweakwcs`[^3] and then the individual images were aligned to the mosaic image. The calibrated and aligned files were then passed through the Stage 3 pipeline to create drizzled images in each bands. During the resampling step, we used a fixed pixel scale of 0.031$''$  for SW images and 0.0315$''$  for LW images with `pixfrac=0.8`. To improve the astrometry of the mosaic images, we further aligned all drizzled images for each quasar field to GAIA DR3. The aligned mosaic images have a precise astrometry and the comparison of NIRCam positions with Gaia catalog typically reveals small offsets of $\sim$50 mas after considering proper motions. Finally, we derived and subtract a background for each mosaic using `photutils`[^4].

Unlike (cite: Wang23), we use `SourcExtractor++` (cite: Bertin20) instead of `SExtractor` (cite: SExtractor) for source detection. Detailed descriptions of catalog construction can be found in (cite: Champagne24a; Champagne24b), but we also briefly summarize it in the following. First, we performed PSF matching on F115W and F200W images to match the resolution of F356W images using empirical PSF models. The empirical PSF models for each images were created by stacking GAIA stars (if available) and bright point sources detected by `daophot` from the `photutils` packages in each image. After matching PSF, we used the `SourcExtractor++` dual-image mode with the respective weight maps for each filter with F356W as the detection band to extract photometry. We set `DETECT_THRESH=3.0`, Kron parameters `k, Rmin = 1.2, 1.7`, `DETECT_MINAREA=10` pixels, and `PHOT_APERTURES= 12 ` pixels. To derive an aperture correction for each source, we ran `SourcExtractor++` twice, once with custom Kron settings optimized for small sources (`k, Rmin = 1.2, 1.5`) and then the default Kron settings (`k, Rmin=2.5, 3.5`). The aperture correction is the ratio between these two Kron fluxes measured in the F356W filter and applied to the photometry in every filter. The final photometry was measured as the forced aperture photometry multiplied by the aperture correction (`Kron_custom/Kron_default`) to account for flux outside of the circular aperture.

The Galactic extinctions in each filter were corrected on the basis of the dust reddening map from (cite: schlegel98) and the dust extinction law derived from (cite: Schlafly11). The signal-to-noise ratios are measured in a $0.32\ensuremath{''}$ arsec circular aperture, as listed in Table [\[tbl:depth\]](#tbl:depth). To determine the photometric uncertainties and limiting magnitudes in each ASPIRE fields, we placed 1000 empty apertures across the images after masking out real sources using the segmentation map, and measured the median absolute deviation of flux in the fixed aperture size. The entire workflow, including the NIRCam/WFSS data reduction and emission line searching algorithms described in the following sections, is integrated into a dedicated Python package, `unfold_jwst` (Wang et al., in prep.). The observing dates and the achieved $5\sigma$ limiting magnitudes, measured in $0.32\ensuremath{''}$ apertures for each of the ASPIRE quasar fields, are listed in Table  [\[tbl:depth\]](#tbl:depth).

## NIRCam WFSS data reduction

Similar to the reduction of imaging data, the WFSS data were reduced using the combination of `CALWEBB` (version 1.10.2) and some custom scripts in `unfold_jwst`. We use calibration reference files (`jwst_1080.pmap`) from version 11.16.21 of the standard Calibration Reference Data System (CRDS). We refer the reader to (cite: Wang23) and (cite: Yang23) for a more detailed description of the process. Briefly, we used the `CALWEBB` stage 1 pipeline to calibrate the detector-level signals and the ramp fitting for individual WFSS exposures. We then subtracted the $1/f$ noise pattern along each detector column. The $1/f$ noise-subtracted images were flat fielded and assigned `WCS` using routines in the `CALWEBB` pipeline. We also subtracted master median background models from the processed images. After that, we measured astrometric offsets between each of the SW images obtained simultaneously with WFSS exposures and the fully calibrated F356W mosaic. The offsets were applied to the tracing and dispersion models (cite: Sun22a; Sun22b) when extracting the spectra. We extracted both 2D and 1D spectra for all sources detected in the F356W imaging. The 2D spectrum of each source is extracted from each individual exposure, and the individual 2D spectra are then coadded into a 2D spectrum after resampling them to common wavelength (9.8 $\rm \AA~pixel^{-1}$) and spatial grids following the histogram2D technique in the `PypeIt` software (cite: Pypeit; Pypeit_ascl). We then extracted 1D spectra from the coadded 2D spectra using both the optimal (cite: Horne86) and the boxcar extraction algorithms. We used an aperture diameter of 7 pixels ($0.411\ensuremath{''}$) for the boxcar spectral extraction. In addition to extracting a 1D spectrum from the coadded 2D spectrum for each source, we optimally extracted 1D spectra from all individual 2D spectra. The extracted 1D spectra from individual exposures were then combined with inverse variance weighting and outlier rejection to a stacked 1D spectrum for each source. The main purpose for producing such stacked spectra is that such a method provides better removal of hot pixels or other outliers for sources with strong continuum (i.e., allow for a profile fitting for optimal extraction from individual exposures).

![](alma_23pts.pdf)

## ALMA observations and data reduction

To discover dusty galaxies in quasar environments beyond the one-megaparsec scale, we designed an ALMA mosaic program (2022.1.01077.L, PI: F. Wang), which consists of 23 Nyquist-sampled pointings in Band 6 (Figure [3](#fig:footprint)). This mosaic covers $\sim1.4$ arcmin$^2$ (or $\sim9$ cMpc$^2$ at $z\gtrsim6.5$) projected sky area around each quasar. In addition, the ALMA footprint falls into the full wavelength coverage region of NIRCam module A, which ensures that we could potentially determine the redshifts for dusty star-forming galaxies by combing ALMA observations with JWST NIRCam/WFSS observations (Figure [3](#fig:footprint)).

Our configuration is motivated by searching for \[C II\] line emitters at the quasar redshifts. To achieve this goal, we tune two spectral windows (SPW, 0 and 1) centered at the expected frequency of \[C II\] (LSB or lower side band). This enables us to search for \[C II\] line emitters physically associated ($\Delta v \lesssim \pm2000~{\rm km~s^{-1}}$) with the central quasars. We tune the other two SPWs (2 and 3) centered at about 15 GHz away from the expected \[C II\] line (USB or upper side band) for observing continuum emission and searching for \[C II\] or CO line emitters at different redshifts. We choose a spectral line setup, with 8 channel averaging, which leads to a velocity resolution of $\sim 5~{\rm km~s^{-1}}$.

The ALMA observation is designed to detect $z>6.5$ galaxies with \[C II\]-based star formation rate (SFR) of $\rm SFR\gtrsim30~{\rm M_\odot~yr^{-1}}$. This leads to $\sim4$ hr total time for each ASPIRE quasar field and a total time of $\sim$100 hours for the entire ALMA program. To balance maximizing the sensitivity and avoiding confusion when matching ALMA data with JWST, we chose to use C-2/3 configuration which delivers a resolution of 0.5$''$–1.0$''$. The ALMA observations were conducted from October 14, 2022 to February 14, 2023. The typical angular resolution of ALMA observation is $\sim$ 0.65$''$. The total survey area of the entire ALMA program is 34.9 arcmin$^2$ at above a primary beam response limit of 0.25.

All the ALMA data were calibrated and processed with the standard `CASA v6.4.1.12` pipeline (cite: CASA). Before making the continuum map, we visually identified and flagged the spectral channels affected by telluric absorption using the `plotms` command. The continuum map was imaged with the `tclean` command with a cell size of 0.12$''$. We used the automatic multi-threshold masking algorithm during the imaging process. To accommodate both compact sources and extended sources, we produced two sets of continuum maps. The first set of continuum maps was produced in the native ALMA resolution with a Briggs weight parameter of `robust=0.5` and the second set of continuum maps was produced with `robust=2.0` and tapered with a Gaussian kernel of FWHM = 1.0$''$. The resulting median synthesized beam (FWHM) is about $0.65\ensuremath{''}$ and $1.34\ensuremath{''}$ for native and tapered continuum images, respectively. The continuum RMS noises of our ALMA mosaics are 0.031$\pm$0.004 mJy beam$^{-1}$ and 0.034$\pm$0.004 mJy beam$^{-1}$ at native and tapered resolution, respectively. Before creating data cubes, we subtract the continuum with `fitorder=1`. The data cubes were created with a channel width of 30 km s$^{-1}$ using `robust=2.0`, `clark` deconvolver, $2\sigma$ threshold and a mask with a radius of 1.0$''$ centered on the central quasars. A more detailed ALMA reduction process can be found in (cite: Sun25) and Decarli et al. in prep.

![](fig_emitter_algorithm.pdf)

# Line emitting galaxies

## \[O III\] emitter finding algorithm

The NIRCam/WFSS observations allow us to search for line emitters in an unbiased way without any imaging preselection. In this work, we extract spectra for all sources detected in the F356W band and then identify \[O III\] emitters based on the extracted spectra directly. Based on the emission-line searching algorithm developed by (cite: Wang23), we further improved the efficiency and purity of the emission-line detections and performed a semiautomatic search using the continuum-subtracted 2D and 1D spectra. For the 1D case, we generated a median-filtered continuum model with a window size of 51 pixels (corresponding to $\sim0.05~\mu$m), which was then subtracted from the optimally extracted spectrum. (cite: Wang23) searched for peaks directly in the continuum-subtracted 1D spectra, which introduced a large number of hot pixels. To address this issue, we instead searched for $\mathrm{S/N} > 1.2$ peaks in a smoothed S/N spectrum rather than in the raw 1D spectrum. The smoothed S/N spectrum was obtained by convolving the continuum-subtracted S/N spectrum with the spectral resolution ($\sim 2.3$ pixels) of the WFSS observations. We found that peaks identified in the smoothed spectra could still be contaminated by hot pixels or other artifacts (e.g., residuals caused by imperfect contamination-model subtraction or background subtraction). To remove such artifacts, we only treat peaks with a total S/N of $\rm S/N>2$ as emission line candidates, where the total S/N was measured by integrating $\pm2$ original pixels (i.e., the S/N spectra without convolving with the spectral resolution) from the center of the peak. To identify if a certain object is a \[O III\] emitter candidate, we first assume that all identified lines with $\rm S/N>5$ (if exists) are the \[O III\] $\lambda5008$ line and then ask if a corresponding \[O III\] $\lambda4960$ or H$\beta$ line also exists (i.e., with $\rm S/N>2$). If \[O III\] $\lambda4960$ and/or H$\beta$ line exists, we then treat this object as a \[O III\] emitter candidate.

![](fig_spec_2dmap_heat_N487.png)

![](fig_redshift_all.png)

We also search for \[O III\] emitter candidates from the continuum subtracted 2D spectra independently. We first search for bright blobs from coadded 2D spectra using `Photutils` (cite: photutils). For each object, we identified bright blobs on a 2D spectral cutout image with a diameter of 5 pixels perpendicular to the dispersion direction. We treat all blobs that have at least three connected pixels with $\rm S/N>0.8$ and the integrated flux with $>2\sigma$ significance as emission line candidates. We then search for potential \[O III\] emitter candidates from the 2D emission line catalogs using the algorithm developed above (i.e., \[O III\] $\lambda5008$ with $\rm S/N>5$ and \[O III\] $\lambda4960$ or H$\beta$ with $\rm S/N>2$).

![](fig_quasar_Nall_color.pdf)

To ensure the robustness of the \[O III\] emitter candidate identification, we only kept objects that were identified as \[O III\] emitter candidates from both the 1D and 2D algorithms. This requirement also significantly reduced the required visual inspection efforts. To reduce the bias of visual inspection, we required that each object be inspected by at least three different team members (E.B., J.B.C., X.J., K.K., R.A.M., F.W., Y.W., J.Y.). During the first round of our visual inspection, each object was classified to be one of the following four categories: 1) `score=3` means a target is definitely an \[O III\] emitter, 2) `score=2` means a target could be an \[O III\] emitter but the corresponding \[O III\] $\lambda$4960 line is not detected and the corresponding H$\beta$ is very faint, 3) `score=1` means only one emission line was detected for the source, 4) `score=0` means a target is definitely not an \[O III\] emitter. After the first round inspection, we classify sources with at least two `score=3` as high confidence \[O III\] emitters, sources with at least one `score=3` or at least two `score=2` as \[O III\] emitter candidates, and other sources as unlikely to be \[O III\] emitters. Furthermore, we asked the inspectors to re-evaluate whether the first two classes (i.e., high-confidence \[O III\] emitters versus \[O III\] emitter candidates) should be interchanged, taking into account comments from other inspectors regarding the confidence of the line detections and potential line-confusion issues. Emitter candidates for which concerns were raised by more than one inspector about possible line confusion and/or significant contamination were reassigned to the lower-confidence \[O III\] emitter-candidate category. To ensure a high purity of the catalog, we decided to use only high-confidence \[O III\] emitters in this work. In future work, we will combine photometric redshifts derived from both JWST and ground-based imaging with our current catalog of \[O III\] emitter candidates to construct a more complete \[O III\] emitter sample at the faint end. The \[O III\] emitter search strategy is summarized in Figure [4](#fig:algorithm). We found that this strategy can recover all \[O III\] emitters except for the faintest one (ASPIRE-J0305M31-O3-023) in (cite: Wang23) and identified 10 additional new \[O III\] emitters in this field. By re-inspecting the spectra from (cite: Wang23), we found that these ten newly identified \[O III\] emitters exhibit relatively weak line detections and were missed in the earlier work primarily due to the slightly lower data sensitivity caused by different version of data reduction pipeline and/or the differences in the peak-detection algorithm used by (cite: Wang23). This indicates that our new line emitter searching method is more effective.

## A catalog of 487 \[O III\] emitters

Using the strategy discussed in the previous section, we successfully identified 487 high-confidence \[O III\] emitters at $5.2\lesssim z\lesssim 7$. We show the spectra of all 487 \[O III\] emitters in Figure [5](#fig:spec2d). A detailed characterization and the luminosity function of these spectroscopically confirmed \[O III\] emitters will be presented in a companion paper (Champagne et al., in prep). In the following sections, we focus our discussions on the quasar environment.

Figure [6](#fig:redshift) shows the redshift distribution of these \[O III\] emitters. From this plot, we can clearly see a number excess of \[O III\] emitters at $6.5<z<6.8$, the redshift range of ASPIRE quasars. This excess is also evident in Figure [5](#fig:spec2d), where a noticeable steepening in the distribution of \[O III\] emission lines appears at $6.5 < z < 6.8$. There are in total 122 \[O III\] emitters with a line-of-sight velocity differencing of $\Delta v_{\rm los}<1000~{\rm km~s^{-1}}$ relative to the central quasars. The $\Delta v_{\rm los}<1000~{\rm km~s^{-1}}$ criterion is widely used in the literature, which corresponds to $\sim9.5$ cMpc at $z\sim6.6$, comparable to the largest projected distance probed by the NIRCam field of view. After accounting for variations in survey volume and sensitivity across different locations and wavelengths (or redshifts), we find that the number density of galaxies at the quasar redshifts ($|\Delta v_{\rm los}| < 1000~{\rm km~s^{-1}}$, $n_{{\rm gal}, z_{\rm quasar}}= 10^{-2.33^{+0.04}_{-0.04}}~{\rm Mpc^{-3}}$) is approximately 9.4 times higher than that at other redshifts ($n_{\rm gal}= 10^{-3.31^{+0.02}_{-0.02}}~{\rm Mpc^{-3}}$). Such a significant overdensity strongly indicates that the ASPIRE quasars are excellent tracers of galaxy overdensities and may serve as reliable probes of massive dark matter halos in the early Universe. We note that the average galaxy number density at non-quasar redshifts is approximately twice as low as that measured in the ASPIRE J0305–3150 field by (cite: Wang23). To investigate this discrepancy, we present in Figure [7](#fig:ngal_all) the number of \[O III\] emitters identified in each ASPIRE field. A striking result is the large field-to-field variation in the number of detected galaxies, despite each ASPIRE field probing a survey volume of $\sim44,000~{\rm cMpc^3}$ over $5.2 \lesssim z \lesssim 7$. This finding underscores the strong influence of cosmic variance in pencil-beam surveys, especially those relying on single JWST pointings or only a few sightlines. Such large field-to-field variations may also explain the inconclusive results of quasar environment studies over the past two decades (see §[5](#sec:environment) for further discussion). Because the uncertainty in clustering measurements scales approximately with the intrinsic variance of the density field divided by the square root of the number of independent fields, ASPIRE’s 25 sightlines (compared to only four in (cite: Eilers24)) provide a significant improvement in constraining quasar environments and clustering properties. In §[4](#sec:clustering), we present a clustering analysis based on the \[O III\] emitters identified across these 25 ASPIRE quasar fields.

## The discovery of 17 \[C II\] emitters from ALMA data

| Name            | RA          | DEC            | $z$    |  S/N | $v_{\rm los}$ |  Dist |
|:----------------|:------------|:---------------|:-------|-----:|--------------:|------:|
|                 |             |                |        |      |          km/s |   kpc |
| J0226$+$0302.C2 | 02:26:00.92 | $+$03:03:17.03 | 6.5430 |  7.1 |          98.6 | 126.5 |
| J0226$+$0302.C3 | 02:26:00.93 | $+$03:03:16.74 | 6.5400 |  6.3 |       $-$20.4 | 124.7 |
| J0229$-$0808.C1 | 02:29:37.55 | $-$08:08:36.78 | 6.7004 |  6.6 |      $-$951.8 | 201.9 |
| J0229$-$0808.C2 | 02:29:35.32 | $-$08:08:22.70 | 6.7325 |  6.2 |         293.2 |   6.4 |
| J0244$-$5008.C1 | 02:44:00.16 | $-$50:08:39.30 | 6.7307 |  8.7 |         259.8 |  90.7 |
| J0244$-$5008.C2 | 02:43:58.98 | $-$50:08:27.71 | 6.3142 |  7.0 |    $-$15906.6 | 178.1 |
| J0305$-$3150.C1 | 03:05:16.39 | $-$31:50:55.14 | 6.6077 |  8.2 |      $-$243.5 |  37.4 |
| J0430$-$1445.C1 | 04:30:42.52 | $-$14:45:40.97 | 6.6843 |  9.6 |     $-$1162.9 |  90.4 |
| J0525$-$2406.C1 | 05:25:59.75 | $-$24:06:23.45 | 6.5373 | 19.4 |       $-$94.4 |   6.3 |
| J0706$+$2921.C1 | 07:06:26.50 | $+$29:21:14.44 | 6.5704 |  6.6 |     $-$1314.8 |  50.4 |
| J0910$-$0414.C1 | 09:10:53.60 | $-$04:14:09.13 | 6.6236 | 22.5 |      $-$500.4 |  77.8 |
| J0910$-$0414.C2 | 09:10:54.54 | $-$04:13:55.52 | 6.6292 | 15.7 |      $-$276.9 |  62.4 |
| J0923$+$0402.C1 | 09:23:44.83 | $+$04:02:41.35 | 6.6340 |  6.1 |          37.9 | 202.5 |
| J1110$-$1329.C1 | 11:10:34.02 | $-$13:29:46.25 | 6.5081 |  6.1 |      $-$249.5 |   6.1 |
| J1526$-$2050.C1 | 15:26:37.87 | $-$20:50:02.33 | 6.5923 | 11.5 |         214.9 |   9.5 |
| J1526$-$2050.C2 | 15:26:37.20 | $-$20:50:31.63 | 6.5954 |  6.0 |         334.8 | 178.5 |
| J2232$+$2930.C1 | 22:32:56.22 | $+$29:31:05.30 | 6.6575 |  6.2 |      $-$333.8 | 198.1 |

To understand the distribution of dusty galaxies in the quasar vicinity, we searched for galaxies with \[C II\] emission lines from the ASPIRE ALMA mosaic observations. The detailed description of the \[C II\] emission line searching will be presented in Decarli et al. in prep. Briefly, the \[C II\] line emitters were identified using the `INTERFEROPY` software (cite: Interferopy), which is a `Python` implementation of `FINDCLUMPs` (cite: Walter16). `INTERFEROPY` runs SExtractor (cite: SExtractor) on averaged channels of continuum subtracted cubes with a range of kernel widths and identifies objects with S/N$>$3. Each line emitter candidate was assigned with a *fidelity* by comparing the candidate’s S/N with the S/N distribution of positive and negative candidates for a given kernel width. In this work, we consider only line emitter candidates with S/N$>6$, a threshold at which the fidelity reaches $\sim$100%, ensuring a highly pure galaxy sample suitable for clustering analysis.

In total, we identify 17 positive line emitter candidates with S/N$>6$, 16 of which lie within the line search bandwidth (LSB) corresponding to the expected \[C II\] wavelength at the quasar redshifts. This strongly suggests that these sources are highly likely \[C II\]-emitting galaxies associated with the quasars. The basic properties of these \[C II\]-emitting galaxies are summarized in Table [\[tbl:c2\]](#tbl:c2). For a more detailed discussion of the individual line emitters, we refer the reader to Decarli et al. (in prep.). In this work, we focus on the statistical clustering analysis of these 15 ALMA \[C II\] emitter candidates and the \[O III\] emitters identified in §[3.2](#subsec:o3e) to probe the large-scale environments of the quasar fields.

| $R_{\rm min}$ | $R_{\rm max}$ | $\left <QG \right >$ | $\left <QR \right >$ | $\chi(R_{\rm{min}}, R_{\rm{max}})$ |
|:--:|:--:|:--:|:--:|:--:|
| ${\rm cMpc}\,h^{-1}$ | ${\rm cMpc}\,h^{-1}$ |  |  |  |
| 0.060 | 0.106 | 3 | 0.0082 | $364.5^{+355.5}_{-198.9}$ |
| 0.106 | 0.186 | 3 | 0.0367 | $80.8^{+79.6}_{-44.5}$ |
| 0.186 | 0.329 | 6 | 0.1344 | $43.6^{+26.7}_{-17.7}$ |
| 0.329 | 0.580 | 11 | 0.4359 | $24.2^{+10.1}_{-7.5}$ |
| 0.580 | 1.022 | 34 | 1.3353 | $24.5^{+5.2}_{-4.3}$ |
| 1.022 | 1.802 | 36 | 2.7924 | $11.9^{+2.5}_{-2.1}$ |
| 1.802 | 3.176 | 21 | 2.7692 | $6.6^{+2.0}_{-1.6}$ |
| 3.176 | 5.600 | 4 | 1.2167 | $2.3^{+2.6}_{-1.6}$ |
| 0.025 | 0.079 | 4 | 0.0035526 | $1124.9^{+890.2}_{-538.8}$ |
| 0.079 | 0.251 | 1 | 0.0355269 | $27.15^{+64.73}_{-23.29}$ |
| 0.251 | 0.794 | 7 | 0.3552692 | $18.70^{+10.61}_{-7.27}$ |
| 0.794 | 2.512 | 4 | 0.4819394 | $7.30^{+6.56}_{-3.97}$ |

# Clustering analyses

## Quasar-galaxy cross-correlation function

To determine the clustering of galaxies around ASPIRE quasars, we follow (cite: hennawi06b) and measure a volume-averaged projected cross-correlation function between quasars and line emitters (both \[O III\] and \[C II\] emitters) defined by $$\begin{equation}
    \chi(R_{\rm{min}}, R_{\rm{max}}) = \frac{\int \xi_{QG}(R, Z) dV_{\rm{eff}}}{V_{\rm{eff}}} \ ,
\label{eq:ccf}    
\end{equation}$$ where $\xi_{QG}(R, Z)$ is the real-space quasar-line emitter two-point correlation function and $V_{\rm{eff}}$ is the effective volume of the cylindrical shell between $R_{\rm{min}}$ and $R_{\rm{max}}$ and extending to a cylinder height $\pm Z$, $$\begin{equation}
Z = \frac{c}{H(z)}\delta z \ ,
\end{equation}$$ where $H(z)$ is the Hubble constant at redshift $z$. The volume averaged cross-correlation $\chi(R_{\rm{min}}, R_{\rm{max}})$ is calculated in radial bins with bin edges $R_{\rm{min}}, R_{\rm{max}}$ via $$\begin{equation}
    \chi(R_{\rm{min}}, R_{\rm{max}}) = \frac{\langle QG\rangle}{\langle QR \rangle} -1 \ ,
\end{equation}$$ where $\langle QG\rangle$ is the number of quasar-emitter pairs in the enclosed cylindrical volume, which is directly measured by counting the quasar-line emitter pairs found in ASPIRE data, and $\langle QR \rangle$ is the expected number of quasar-line emitter pairs in the same bin if they were randomly distributed around the quasar, with the background number density. The $\langle QR \rangle$ is computed from $$\begin{equation}
   \langle QR \rangle = n_{\rm G} (z) V_{\rm eff},
\end{equation}$$ where $n_{\rm G} (z)$ is the mean number density of line emitters at redshift $z$ within our survey.

Since the ALMA mosaic observations provide uniform survey depth in both the lower and upper sidebands (LSB and USB), corresponding to galaxies at the quasar redshifts and at slightly lower redshifts, respectively, we can directly estimate the field galaxy number density, $n_{\rm G}(z)$, from the USB data. After accounting for the survey volume of each ASPIRE quasar field and assuming that all line emitters with S/N$>$6 are \[C II\] emitters with a redshift-independent number density across the narrow redshift range of interest, we measure $n_{\rm G}(z) = 10^{-3.98^{+0.76}_{-0.52}}~{\rm cMpc^{-3}}$ using galaxies within USB. Given the limited number of \[C II\] emitter candidates, we use all galaxies in LSB to measure $\langle QG \rangle$, corresponding to a cylinder height of $Z\sim 14~{\rm cMpc}\,h^{-1}$ or line-of-sight velocity $\Delta v_{\rm los} \sim \pm2100 \, \text{km s}^{-1}$. The $\chi(R_{\rm{min}}, R_{\rm{max}})$ was measured in four bins and the results are presented in Table [\[tbl:ccf\]](#tbl:ccf).

The clustering analysis for \[O III\] emitters is more complex than that for \[C II\] due to the strong dependence of the NIRCam/WFSS line-flux limit on both wavelength (or redshift) and spatial position. To fully account for these spatial and spectral variations, we performed mock source injection experiments across all ASPIRE quasar fields to determine the corresponding flux limits as functions of both wavelength and position. Firstly, we generated a grid of mock sources at $5.3<z<7$ with a fixed line flux ($f = 10^{-17}~\rm erg\,s^{-1}\,cm^{-2}$, five times brighter than our flux limit determined by (cite: Wang23)) and applied the same line-searching algorithm described in §[3.1](#subsec:o3). The flux limit at each wavelength and position was then derived from the S/N of the detected emission lines. Using these line flux limit maps, we then constructed an `unfold_jwst` detected random source catalog and a corresponding selection function by injecting five million ($5\times10^{6}$) mock sources into the full F356W imaging footprint of each quasar field and identifying which mock sources met the detection threshold of the emitter search. The flux distribution of the injected sources was matched to the \[O III\] luminosity function from (cite: Matthee22), assuming no redshift evolution. We then used the `Corrfunc` python package (cite: Sinha20) to count quasar-galaxy pairs, $\langle QG \rangle$, and quasar-mock galaxy pairs, $\langle QR \rangle$, within cylindrical bins defined by $(R_{\rm min}, R_{\rm max})$ and a cylinder height of $Z = 7~{\rm cMpc}\,h^{-1}$, corresponding to a line-of-sight velocity of $\Delta v_{\rm los} \lesssim 1000~{\rm km~s^{-1}}$ at the ASPIRE quasar redshifts. The $\langle QR \rangle$ values were normalized using the expected number of \[O III\] emitters in blank fields after applying the selection function. A comprehensive description of this methodology and the measurement of \[O III\] emitter auto-correlation function will be presented in a companion paper by (cite: Huang26). The resulting $\chi(R_{\rm min}, R_{\rm max})$ measurements for the \[O III\] emitters are listed in Table [\[tbl:ccf\]](#tbl:ccf). Note that the uncertainties of all $\chi(R_{\rm min}, R_{\rm max})$ measurements in Table [\[tbl:ccf\]](#tbl:ccf) include only Poisson noise. In (cite: Huang26), we will further incorporate the effects of cosmic variance into the error budget using a covariance matrix constructed from mock realizations of cosmological simulations.

![](fig_corrfunc_final_v20251023.pdf)

![](fig_corrfunc_final_v20251023_corner.pdf)

We show the measured cross-correlation function, $\chi(R_{\rm{min}}, R_{\rm{max}})$, in figure [8](#fig:ccf). With Eq. [\[eq:ccf\]](#eq:ccf), we can fit $\chi(R_{\rm{min}}, R_{\rm{max}})$ in order to constrain the real-space quasar-line emitter two-point correlation function $\xi_{\rm{QG}}$ parameterized as $$\begin{equation}
\xi_{\rm{QG}} = \left(r/r_0^{\rm{QG}}\right)^{-\gamma_{\rm{QG}}} \ , 
\end{equation}$$ where $r=\sqrt{R^2+Z^2}$, and $r_0^{\rm{QG}}$ is the cross-correlation length, and $\gamma_{\rm{QG}}$ is its power-law slope. We perform an MCMC fit to the measured cross-correlation function using `emcee` (cite: emcee). Since the quasar-galaxy cross-correlation function measured from \[O III\] emitters is consistent with that of \[C II\] emitters, we fit all data together. When fixing the slope at $\gamma_{\rm{QG}} = 2.0$ to enable a comparison to other studies (cite: Shen10; Eilers24), we derive $r_0^{\rm{QG}} = 8.68^{+0.51}_{-0.55}~h^{-1}~{\rm cMpc}$ for ASPIRE quasars with an average redshift of $\langle z\rangle=6.6645$. The fitting result is shown in Figure [8](#fig:ccf). For comparison, (cite: Eilers24) derived $r_0^{\rm{QG}} = 9.1^{+0.5}_{-0.6}~h^{-1}~{\rm cMpc}$ using four EIGER quasars at $\langle z\rangle=6.25$.

If we do not freeze the slope during the fitting, we obtain $\gamma_{\rm{QG}} = 1.68^{+0.18}_{-0.20}$ and $r_0^{\rm{QG}} = 12.20^{+3.47}_{-2.30}~h^{-1}~{\rm cMpc}$. Nevertheless, there is a strong degeneracy between $\gamma_{\rm{QG}}$ and $r_0^{\rm{QG}}$ as shown in Figure [9](#fig:corner). Therefore, we use the value from the fixed $\gamma_{\rm{QG}}$ in the following analyses, similar to previous studies (cite: Eilers24).

## Quasar host dark matter halos and duty cycles

Assuming that quasars and \[O III\] emitters trace the same underlying dark matter density field (cite: Garcia17), the quasar auto-correlation $\xi_{\rm{QQ}}$ can be inferred from the galaxy-galaxy auto-correlation $\xi_{\rm{GG}}$ and the quasar-galaxy cross-correlation $\xi_{\rm{QG}}$ according to $$\begin{equation}
\xi_{\rm{QG}} = \sqrt{\xi_{\rm{QQ}}\xi_{\rm{GG}}}
\end{equation}$$ After applying the $r_0^{\rm{GG}}$ of \[O III\] emitter ($r_0^{\rm{GG}}=4.78^{+0.50}_{-0.55}\,\rm{h}^{-1}\,\rm{cMpc}$) measured directly from ASPIRE galaxies (Huang et al. in prep), we derive an quasar auto-correlation length of $r_0^{\rm{QQ}}=15.76^{+2.48}_{-2.70}~h^{-1}~{\rm cMpc}$. To the first order, we can constrain the minimum halo mass $M_{\rm{halo, min}}$ by linking $r_0^{\rm{QQ}}$ to the auto-correlation length of dark matter halos with $M_{\rm halo}>M_{\rm{halo, min}}$. Using the `halomod` (cite: Murray13; Murray21) tool[^5] with an assumption of a step-function Halo Occupation Distribution (HOD), we estimate that $\rm log(M_{\rm{halo, min}}/M_\odot)= 12.27^{+0.21}_{-0.26}$ with a cumulative abundance of dark matter halos $n_{\rm{halo,min}}= {\rm 54.6^{+510.0}_{-48.5}\, cGpc^{-3}}$ with $M>M_{\rm{halo, min}}$. This simple calculation suggests that the most distant luminous quasars, on average, reside in the most massive dark matter halos at their respective cosmic times, consistent with expectations from theoretical models (cite: Pizzati24a).

The spatial density of ASPIRE quasars (i.e., $6.5<z<7$ and $M_{1450}>-25$) are estimated to be $n_{\rm Q}=\rm 0.76~cGpc^{-3}$ based on the luminosity function from (cite: Wang19b) and (cite: Matsuoka18c). Together with $n_{\rm{halo,min}}$, we can then infer quasars’ duty cycle ($f_{\rm duty}$) and UV-luminous life time ($t_Q$) using $$\begin{equation}
n_{\rm Q} = f_{\rm duty} \times n_{\rm halo}
\end{equation}$$ , where $f_{\rm duty}\simeq\frac{t_Q}{t_{\rm H}(z)}$ and $t_{\rm H}(z)$ is the Hubble time at redshift $z$. After plugging in the numbers, we estimate that $t_{\rm Q}=\rm 10^{{7.05}^{+0.95}_{-1.01}}~yr$ and $f_{\rm duty}=1.4^{+11.1}_{-1.3}$%. We note that the minimum halo mass of ASPIRE quasars, $M_{\rm halo, min}$, lies at the extreme high-mass end of the dark matter halo distribution at these redshifts. Because the halo mass function is extremely steep in this regime, the corresponding number density, $n_{\rm halo, min}$, is highly sensitive to even small changes in $M_{\rm halo, min}$. As a result, estimates of the quasar duty cycle and lifetime are subject to substantial uncertainties. This sensitivity underscores the challenge of constraining the physical properties of high-redshift quasars using halo abundance matching, particularly for the rarest, most massive systems. The short UV-luminous quasar lifetime and small duty cycle inferred for the ASPIRE quasars suggest that most of the black hole mass growth likely took place during an obscured, non-UV-luminous phase. This scenario would help mitigate the otherwise severe tension associated with forming billion-solar-mass black holes from light seeds by such early cosmic times (cite: Davies19; Wang21a).

![](fig_mhalo_redshift.pdf)

We also compare the clustering of galaxies in these quasar fields with the predictions from the TRINITY model (cite: Zhang23). TRINITY infers the empirical mass and growth rate connections between dark matter halos, galaxies, and SMBHs, which match a compilation of galaxy data from $z=0-13$ and SMBH data from $z=0-7$ by construction. To make predictions of galaxy clustering around $z\sim 6.5$ quasars, we first generate mock halo–galaxy–SMBH catalogs based on the best-fitting TRINITY model and the *Uchuu* simulation (cite: Ishiyama21). To fully utilize the statistical power provided by this large catalog, we use *all* the AGNs in the catalog to calculate the weighted AGN–galaxy cross-correlation function, where each AGN is weighted to reflect their similarity to the ASPIRE quasars. Specifically, the weight $w$ for a simulated AGN with black hole mass $M_\mathrm{BH}$ and bolometric luminosity $L_\mathrm{bol}$ is a sum of its probability given the observed ASPIRE sample, $\{(M_{\mathrm{BH},i}, L_{\mathrm{bol},i})\}_{i=1}^{25}$:

$$\begin{align}
    w = &\sum_{i=1}^{N=25} P\left[(M_\mathrm{BH}, L_\mathrm{bol}) | (M_{\mathrm{BH},i}, L_{\mathrm{bol},i})\right]\nonumber\\
        =&\sum_{i=1}^{N=25} \frac{1}{2\pi \sigma_{\mathrm{L_\mathrm{bol}},i} \sigma_{M_\mathrm{BH},i}}\nonumber \\
                                &\times \exp{\left[-\frac{(\log M_\mathrm{BH} - \log M_{\mathrm{BH},i})^2}{2\sigma_{M_{\mathrm{BH},i}}^2}\right]}\nonumber\\
                                &\times \exp{\left[-\frac{(\log L_\mathrm{bol} - \log L_{\mathrm{bol},i})^2}{2\sigma_{\mathrm{L_\mathrm{bol}},i}^2}\right]}\ ,
\label{eq:gauss_weights}
\end{align}$$

where $\sigma_{M_{\mathrm{BH},i}}$ and $\sigma_{\mathrm{L_\mathrm{bol}},i}$ are the measurement uncertainties in SMBH mass and luminosity of the $i$th ASPIRE quasar, respectively. For $\sigma_{M_{\mathrm{BH},i}}$, we also add a scatter of 0.5 dex in quadrature to account for the random scatter in virial estimates of $M_\mathrm{BH}$ (cite: Vestergaard06; Shen13). To keep the consistency between our predictions and the observations, we applied the $L_\mathrm{\left[OIII\right],4960+5008}$–$M_\mathrm{UV}$ scaling relation from (cite: Matthee24) to calculate the predicted $L_\mathrm{\left[OIII\right],5008}$ for our mock galaxies, assuming $L_\mathrm{\left[OIII\right],5008}:L_\mathrm{\left[OIII\right],4960}=3:1$, and only include galaxies with $L_\mathrm{\left[OIII\right],5008} \geq 10^{42}$ erg/s when calculating the clustering. The TRINITY predicted quasar-\[O III\] emitter cross-correlation function is shown in Figure [8](#fig:ccf). The correlation length and slope are $r_0^{\rm{QG}} = 7.9\pm0.4~h^{-1}~{\rm cMpc}$ and $\gamma_{\rm{QG}} = 2.05\pm0.06$ which are consistent with the ASPIRE measurement. The corresponding median halo mass in TRINITY is $\rm log(M_{\rm{halo}}/M_\odot)= 12.04{\pm0.22}$, also similar to our measurements.

![](fig_quasar_Ncompanion_Delta_color.pdf)

As shown in Figure 8, both the ASPIRE measurements and the TRINITY predictions exhibit an excess in the quasar-galaxy cross-correlation function, $\xi_{\rm{QG}}$, relative to the power-law fit at $R \lesssim 0.2~h^{-1}~\mathrm{cMpc}$. This excess indicates the presence of the so-called *one-halo term* in HOD models, where an increased number of companion galaxies are found within quasar host halos or sub-halos. Such an enhancement is consistent with quasars residing in massive dark matter halos that can host multiple galaxies in close proximity, or with a high satellite galaxy fraction around quasars. Together with the strong \[C II\] detections of ASPIRE quasar host galaxies (cite: Wang24b), the observed small-scale excess from both \[O III\] and \[C II\] emitters, both indicative of galaxies with active star formation, suggests that the quasar environment is undergoing vigorous star-forming activity. This enhanced activity may be driven by the same gas-rich conditions that fuel quasar accretion, such as filamentary inflows or galaxy mergers. Furthermore, quasar feedback may not yet have suppressed star formation in nearby galaxies at these early cosmic epochs, consistent with the analyses of galaxy properties in quasar vicinity (cite: Champagne24a; Champagne24b).

In Figure [10](#fig:mhalo), we compare the derived $M_{\rm halo, min}$ and $r_0^{\rm QQ}$ with measurements of quasars at lower redshifts from the literature (cite: Shen07; Eftekharzadeh15; Laurent17; Arita23; Eilers24). Our results suggest that the characteristic dark matter halo mass of quasars does not evolve significantly with redshift up to $z \sim 7$, remaining at a few times $10^{12}~M_\odot$. This indicates that quasars can be triggered in halos of similar mass across cosmic time, consistent with previous findings at lower redshifts. This is strikingly close to the mass scale of $M_{\rm halo} \sim 10^{12}~M_\odot$, where galaxy formation is most efficient due to a balance between gas cooling and feedback processes that regulate star formation (cite: Wechsler18). If these quasars follow the stellar-to-halo mass relation of galaxies (cite: Behroozi19), our study suggests that these luminous $z \sim 7$ quasars are hosted by galaxies with stellar masses of a few times $10^{10}~M_\odot$, consistent with recent JWST observations of stellar light from quasar hosts (cite: Ding23; Yue24), as well as dynamical mass estimates from ALMA observations (cite: Neeleman21; Wang24b). Since the ASPIRE program also includes deep, high-resolution JWST/NIRCam imaging, the stellar masses of the ASPIRE quasar hosts will soon be available (Yang et al., in prep). Combined with the halo masses derived here, this will allow us to directly constrain the stellar-to-halo mass relation for the ASPIRE quasar sample. Furthermore, we will compare the ASPIRE measurements with cosmological simulations and discuss the constraints on the duty cycle of both quasars and the H$\beta$+\[O III\] emitting galaxies in a companion paper (Huang et al., in prep).

# Quasar Environment

## Diverse quasar environments

(cite: Habouzit19) investigated the number of companion galaxies around high-redshift SMBHs using the `Horizon-AGN` simulation. They found that, on average, SMBHs are surrounded by more companion galaxies than blank fields, particularly when observations are sensitive to faint or low-mass galaxies (i.e., $M_\ast > 10^8~M_\odot$; see their Figures 3 and 4). However, when only the most massive galaxies are detectable (e.g., $M_\ast > 10^{9\text{--}9.5}~M_\odot$) or when the field of view is restricted, the observed number of companions can vary significantly because of cosmic variance. The differing observational sensitivities, limited survey volumes, limited number of studied quasar fields and the high levels of incompleteness and contamination associated with photometric galaxy selections in previous studies have led to inconclusive results regarding whether the observed diversity in quasar environments arises from cosmic variance, selection bias or reflects intrinsic differences in their underlying environments.

In contrast to earlier studies (cite: Willott05; Kim09), the ASPIRE program provides substantially improved sensitivity to star-forming galaxies, reaching stellar masses as low as $M_\ast \gtrsim 10^{7\text{--}8}~M_\odot$ (cite: Champagne24b). The WFSS observations also probe much larger comoving volumes along the line of sight, enabling a more complete census of galaxies both in quasar environments and at other redshifts. Furthermore, the large number of independent sightlines observed by ASPIRE significantly reduces the impact of field-to-field cosmic variance, which has been a major limitation in previous surveys. As a result, the number of companion galaxies identified in this study is far less affected by selection biases and cosmic variance and can be compared with theoretical simulations in a more robust and physically meaningful manner.

In Figure [11](#fig:ngal), we show the number of quasar companion \[O III\] emitting galaxies and the galaxy overdensity, defined as $\delta_{\rm gal} = \frac{n_{\rm companion}}{\bar{n}} - 1$, in each of the ASPIRE fields. The galaxy overdensity $\delta_{\rm gal, [OIII]}$ is measured using galaxies within NIRCam module A (with $r_{\rm eff} \lesssim 3~{\rm cMpc}$, or $V \sim 500~{\rm cMpc}^3$ assuming a projected length of $\rm \Delta |v_{\rm los}|\le1000~km~s^{-1}$), where we have uniform depth and continuous coverage. Figure [11](#fig:ngal) demonstrates that the number of quasar companion galaxies ranges from zero to 20, corresponding to overdensities from zero to $\delta_{\rm gal, [OIII]} \simeq 22$. Specifically, there are seven quasar fields with $\delta_{\rm gal, [OIII]} > 5$, six quasar fields consistent with the number of galaxies in blank fields, one field without any companion galaxy, and the remaining fields with $1 < \delta_{\rm gal, [OIII]} < 5$.

![](fig_cumulative_number.png)

![image](fig_vicinity_J0218p0007_color.png) ![image](fig_vicinity_J0226p0302_color.png) ![image](fig_vicinity_J0244m5008_color.png) ![image](fig_vicinity_J0305m3150_color.png) ![image](fig_vicinity_J0910m0414_color.png) ![image](fig_vicinity_J1058p2930_color.png) ![image](fig_vicinity_J2102m1458_color.png)

As discussed in (cite: Wang23), the median number of companion galaxies around SMBHs at $z \sim 6$ with $M_\ast \geq 10^8~M_\odot$ is approximately four in both the `SIMBA` (cite: Dave19) and `EAGLE` (cite: Schaye15) simulations, when matched to the depth and survey volume of the ASPIRE program. This prediction is consistent with the average number of companion galaxies observed by ASPIRE ($\bar{n}_{\rm [OIII]} = 4.8$). Moreover, the simulated number of companion galaxies within a survey volume comparable to that of ASPIRE exhibits substantial field-to-field variation, ranging from 2 to 66 when considering all SMBHs with $M_{\rm BH} \gtrsim 10^{7.5}~M_\odot$ across multiple simulation suites, including `Horizon-AGN` (cite: Dubois14), `Illustris` (cite: Vogelsberger14), `TNG100/300` (cite: Pillepich18), `EAGLE`, `SIMBA`, `Astrid` (cite: Bird22; Ni22), and `BlueTides`. This broad range is consistent with the large field-to-field variance observed in ASPIRE, as shown in Figure [11](#fig:ngal). Taken together, these advantages allow us to interpret the observed variations in galaxy overdensity (Figure [11](#fig:ngal)) as evidence of intrinsically diverse quasar environments at high redshift, rather than selection bias or cosmic variance. This finding highlights the importance of statistical completeness in environmental studies of rare populations. Future investigations aiming to characterize the environments of luminous quasars, or other rare systems should therefore target a large number of sightlines to minimize the influence of cosmic variance and selection bias.

Interestingly, we find a clear correspondence between the overdensity of \[O III\] emitters and the presence of \[C II\]-emitting companion galaxies.

Specifically, four of the seven fields with significant \[O III\] overdensities ($\delta_{\rm gal,[OIII]} > 5$) contain \[C II\] companions, compared to only two of the seven fields with low overdensities ($\delta_{\rm gal,[OIII]} \le 1$). While the small number of fields limits the statistical significance, the relative fractions (57% versus 29%) point to a consistent trend in which \[C II\]-emitting galaxies preferentially reside in fields that exhibit enhanced \[O III\] emitter populations. This supports a connection between the large-scale environments traced by the two line-emitting galaxy populations. Given that \[C II\] emission arises from the neutral interstellar medium (ISM) in star-forming regions and is a good tracer of dust obscured star formation, whereas \[O III\] emission primarily traces galaxies with intense star formation and highly ionized gas in less dusty environment, the observed correspondence between these two populations suggests that they both trace the same underlying mass density field. In other words, regions with strong \[O III\] overdensities are also likely to host \[C II\]-emitting galaxies, and vice versa. This finding indicates that \[O III\]- and \[C II\]-emitting galaxies jointly map the large-scale structure surrounding high-redshift quasars, providing complementary perspectives on the physical conditions within early overdense regions.

The detection of both populations in the vicinity of high-redshift quasars therefore demonstrates that multiple modes of star formation, both dusty and relatively unobscured, coexist within the same large-scale structures. Such coexistence implies that the environments of early quasars were not uniform but instead hosted a diversity of interstellar conditions and star-formation processes. This complexity underscores the importance of multi-line studies in capturing the full picture of galaxy formation and feedback in the early Universe.

![](fig_velocity_abs_new.pdf)

## Distribution and kinematics of companion galaxies

To take a closer look at the structures of the seven fields with $\delta_{\rm gal, [OIII]} > 5$, we show the cumulative number of galaxies as a function of projected distance from the central quasars in these fields in Figure [12](#fig:cum_num) and the spatial distribution of companion galaxies in Figure [13](#fig:protocluster). In this work, we define these structures (i.e., regions with $\delta_{\rm gal, [OIII]} > 5$ within $V \sim 500,{\rm cMpc}^3$) as protocluster candidates. J0226+0302, the most overdense field ($\delta_{\rm gal, [OIII]} > 20$), exhibits the steepest rise within the central $R \lesssim 300~{\rm pkpc}$, where the galaxy survey is complete for sources with $L_{\rm [OIII], 5008\text{\AA}} > 10^{42}~{\rm erg~s^{-1}}$. A more detailed characterization of this structure, along with new JWST mosaic observations, will be presented in future works. J0218+0007 has a similar $\delta_{\rm gal, [OIII]}$ to that of J0305$-$3150 and J0910$-$0414, but shows a more rapid increase in galaxy counts, indicating that the structures traced by J0305$-$3150 and J0910$-$0414 are more spatially extended than that of the structure traced by J0218+0007. This is consistent with the fact that J0305$-$3150 extends well beyond the NIRCam field of view, and that the quasar does not reside in the densest region of the structure (cite: Champagne24a; Champagne24b).

Interestingly, the companion galaxies are not uniformly distributed but instead appear more consistent with filamentary structures commonly seen in cosmological simulations (cite: Costa24) in all seven protocluster fields. To investigate whether any coherent motions are present, we color-coded the symbols by the line-of-sight velocity, $v_{\rm los} = \frac{z_{\rm gal} - z_{\rm quasar}}{1 + z_{\rm quasar}}c$, of each galaxy relative to its central quasar in Figure [13](#fig:protocluster). We find no clear evidence of velocity gradients or coherent motions within individual structures. This is similar to what we have seen in cosmological simulations (cite: Costa24) and suggesting that we are observing unvirialized filamentary structures in the early Universe. To further study the kinematics of galaxies in these environments, we plot their relative line-of-sight velocities ($|v_{\rm los}|$) as a function of projected distance from the central quasars in Figure [14](#fig:velocity). In this figure, we also show the median $|v_{\rm los}|$ in seven protocluster fields across five bins. We find that, on average, companion galaxies within a projected distance of $\lesssim 100$ kpc from the quasars exhibit a steep rise in $v_{\rm los}$ in these fields, albeit with small number statistics. This is consistent with the increased velocities of galaxies within the virial radius of massive halos (i.e., the virial radius of a $10^{13}~M_\odot$ halo at $z\sim6.6$ is approximately $\sim100$ kpc). We also compare our results with the cosmological simulations by (cite: Costa24), which studied six extremely massive dark matter halos ($M_{\rm halo}>5\times10^{12}~M_\odot$) and six moderately massive dark matter halos ($M_{\rm halo}\simeq6\times10^{11}-1\times10^{12}~M_\odot$) at $z\sim6$ using high-resolution numerical simulations. The six massive halos represent the most extreme high-density peaks at these redshifts and serve as signposts of the earliest protoclusters, all of which evolve into galaxy clusters by $z=0$. (cite: Costa24) found that $\sim10\%$ of the satellite galaxies around the high-mass halos have $|v_{\rm los}|$ values close to or exceeding 800 km s$^{-1}$, whereas the steep rise in $|v_{\rm los}|$ was not observed in the lower-mass halos. In Figure [14](#fig:velocity), we show the fitted mean $|v_{\rm los}|$ values for the two halo samples from (cite: Costa24). The protocluster fields identified in this work exhibit $|v_{\rm los}|$ distributions similar to those of the high-mass halos in (cite: Costa24), with some galaxies reaching $|v_{\rm los}|$ of $\sim 800$ km s$^{-1}$, indicating that they reside in extremely massive halos.

To compare our results with simulations more quantitatively, we show the cumulative distribution of $|v_{\rm los}|$, i.e., the fraction of galaxies with $|v_{\rm los}|<v$ within $\rm 100~kpc$ of the central quasars, in Figure [15](#fig:velocity_cum). Overall, the $|v_{\rm los}|$ distribution from the ASPIRE program (black solid line) more closely resembles that of high-mass halos (i.e., $M_{\rm halo}>5\times10^{12}~M_\odot$). When separating the distributions for protocluster and non-protocluster fields, we find that the protocluster fields exhibit an even higher fraction of galaxies with large $|v_{\rm los}|$, suggesting that the seven ASPIRE quasars with $n_{\rm gal}>5$ likely reside in extreme protocluster environments. In contrast, the $|v_{\rm los}|$ distribution for the remaining ASPIRE fields aligns more closely with the moderately massive halo simulations. These comparisons imply that the host dark matter halos of ASPIRE quasars have a broad range, with some residing in very massive dark matter halos tracing extreme protocluster regions. However, our current measurements of $|v_{\rm los}|$ rely on a small number of galaxies, and we do not yet have evidence that these structures will be virialized. Therefore, no firm conclusion can yet be drawn about whether they will eventually evolve into massive galaxy clusters by $z=0$. Given the significant galaxy overdensities in these fields and the fact that these structures extend to the edges of the JWST/NIRCam field of view, we are conducting follow-up observations to investigate the extent and properties of these filamentary structures. These efforts will also explore the potential role of the central quasars in regulating galaxy formation within these environments (cite: Champagne24a; Champagne24b).

![](fig_cumulative_velocity.png)

## Implications for the early growth of SMBHs

Our study reveals that a substantial fraction of ASPIRE quasars do not reside in overdense regions, implying a far more diverse range of environments and host halo masses for the first quasars than traditionally assumed. This result stands in contrast to predictions from many cosmological simulations (cite: Costa14; DiMatteo17), which typically require both a massive dark matter halo and a highly overdense large-scale environment in order to grow a seed black hole into a billion-solar-mass quasar under Eddington-limited accretion. The discovery of such diverse quasar environments therefore poses significant challenges to these models. In particular, it suggests that the earliest supermassive black holes must, at least in a substantial subset of cases, follow more rapid or more efficient growth pathways, potentially involving sustained super-Eddington accretion, even for massive seeds, allowing them to reach $\sim10^9\,M_\odot$ within a few hundred million years without requiring exceptionally dense environments. Recent theoretical work provides additional support for this emerging picture. For example, (cite: Fontanot25), using the GAEA model coupled to the *Planck* Millennium Simulation, found that bright quasars can inhabit a wide range of environments and that secular processes such as disk instabilities may play an important role in triggering early quasar activity. In this scenario, the presence of a significant galaxy overdensity around a quasar is not a necessary condition.

On the other hand, JWST has revealed an unexpectedly large population of faint AGNs at $z>4$ (cite: Kocevski23; Greene24; Lin24; Matthee24), suggesting that our current framework for early black hole growth may be significantly incomplete. Their high abundance indicates that they cannot all reside in very massive dark matter halos (cite: Pizzati25) and that they may represent an alternative pathway toward assembling the $\sim 10^9\,M_\odot$ black holes that power luminous quasars. Notably, a subset of these JWST-detected faint AGNs exhibits strong Balmer breaks and/or Balmer absorption features (cite: Naidu25), pointing to early black hole growth occurring in dense, gas-rich environments and potentially proceeding at super-Eddington accretion rates (cite: Schleicher13; Coughlin24). However, it remains unclear whether these faint AGNs are connected to the population of luminous quasars, or whether they could serve as progenitors for a subset of them, particularly for those quasars that do not reside in overdense environments. Taken together, these findings underscore the need to revise theoretical expectations for early black hole growth and highlight the critical importance of conducting comprehensive studies of the environments and clustering properties of both luminous quasars and the faint AGNs uncovered by JWST.

# Summary

In this work, we presented an overview of the ASPIRE program, a legacy galaxy redshift survey with the JWST/NIRCam WFSS and ALMA mosaic observations along 25 high-redshift quasar sightlines. This program enabled the discovery of 487 \[O III\] emitting galaxies at $5.3 \lesssim z \lesssim 7$, including approximately 120 companion galaxies that are physically associated ($\Delta v_{\rm los} < 1000~\mathrm{km~s^{-1}}$) with the cosmic structures traced by the central luminous quasars. The ALMA observation also enabled the discovery of 17 high-confidence line emitter galaxies with 16 of them are potential \[C II\] emitters at the quasar redshifts. This large sample of spectroscopically confirmed galaxies allowed us to draw the following conclusions:

- On average, luminous $z \sim 7$ quasars are effective tracers of galaxy overdensities, with 18 out of 25 quasars hosting more than one companion \[O III\]-emitting galaxy and exhibiting overdensities relative to the expected cosmic average. The number of \[O III\]-emitting galaxies at ASPIRE quasar redshifts is 9.4 times higher than that of \[O III\]-emitting galaxies at other redshifts.

- The quasar–galaxy cross-correlation functions measured from both \[O III\] and \[C II\] emitters yield similar results: galaxies are strongly clustered around ASPIRE quasars, suggesting that distant luminous quasars generally reside in massive halos. Detailed clustering analyses based on quasar-\[O III\] and quasar-\[C II\] cross-correlation functions indicate that ASPIRE quasars have a auto-correlation length of $r_0^{\rm QQ} = 15.76^{+2.48}_{-2.70}~h^{-1}~{\rm cMpc}$, corresponding to a host halo mass of $\log(M_{\rm halo, min} / M_\odot) = 12.27^{+0.21}_{-0.26}$, the first precise measurement at $z>6.5$.

- The clustering analysis indicates that the UV-luminous duty cycle of ASPIRE quasars is low with $f_{\rm duty}=1.4^{+11.1}_{-1.3}$% and a UV-luminous lifetime of $t_{\rm Q}=\rm 10^{{7.05}^{+0.95}_{-1.01}}~yr$, reinforces that most of the black hole mass growth likely took place during an obscured UV-faint phase.

- The number of quasar companion \[O III\]-emitting galaxies varies significantly from field to field, ranging from zero to 20, corresponding to overdensity of zero to 22. By comparing with cosmological simulations, we conclude that the diverse number of quasar companion galaxies reflects the intrinsically diverse quasar environments rather than being driven by observational biases.

- A clear correspondence between the overdensity of \[O III\]-emitting galaxies and the presence of \[C II\]-emitting companion galaxies suggests that \[O III\]- and \[C II\]-emitting galaxies jointly map the large-scale structure surrounding high-redshift quasars and multiple modes of star formation, both dusty and relatively unobscured, coexist within the same large-scale structures.

- Seven ASPIRE quasars reside in extremely overdense structures ($\delta_{\rm gal} > 5$ within $V \sim 500\, {\rm cMpc}^3$) and present the “finger-of-god" effect, consistent with being among the most extreme protoclusters observed in the early Universe.

This study provides the first statistical constraint on the environments and dark matter halo masses of quasars at $z > 6.5$, using a sample of 25 quasar sight lines and leveraging both obscured and unobscured galaxies as large-scale structure tracers. These results represent a major step forward in our understanding of the large-scale environments of early quasars, complementing existing studies focused on individual systems or smaller samples. Together with forthcoming measurements of quasar host galaxy properties and central black hole masses (Yang et al., in prep), the ASPIRE program will establish a critical benchmark for high-redshift quasar studies, spanning spatial scales from the sub-parsec central engine to the several-Mpc-scale cosmic web. In the coming years, as more deep observations from JWST, ALMA, and other facilities (e.g., Euclid, Rubin, and Roman) become available, we expect to gain a clearer and more complete picture of how the earliest luminous quasars form, grow, and evolve. These results will also help to clarify how the emergence of bright quasars connects to the broader population of faint, narrow-line or broad-line AGN candidates recently discovered by JWST at high redshifts, shedding light on the earliest phases of supermassive black hole and galaxy co-evolution.

F.W. acknowledges support from NSF award AST-2513040. J.B.C. acknowledges funding from the JWST Arizona/Steward Postdoc in Early galaxies and Reionization (JASPER) Scholar contract at the University of Arizona. M.H. acknowledge support from the Swiss SNSF Starting Grant(grant no. 218032). SEIB is supported by the Deutsche Forschungsgemeinschaft (DFG) under Emmy Noether grant number BO 5771/1-1. J.-T.S. is supported by the Deutsche Forschungsgemeinschaft (DFG, German Research Foundation) - Project number 518006966. AL acknowledges support from PRIN MUR 2022935STW. C.M. acknowledges support from Fondecyt Iniciacion grant 11240336 and the ANID BASAL project FB210003. RAM acknowledges support from the Swiss National Science Foundation (SNSF) through project grant 200020_207349. B.T. acknowledges support from the European Research Council (ERC) under the European Union’s Horizon 2020 research and innovation program (grant agreement number 950533), and from the Excellence Cluster ORIGINS which is funded by the Deutsche Forschungsgemeinschaft (DFG, German Research Foundation) under Germany’s Excellence Strategy - EXC 2094 - 390783311. M.V. gratefully acknowledges financial support from the Independent Research Fund Denmark via grant numbers DFF 8021-00130 and 3103-00146 and from the Carlsberg Foundation (grant CF23-0417).

This work is based on observations made with the NASA/ESA/CSA James Webb Space Telescope. The data were obtained from the Mikulski Archive for Space Telescopes at the Space Telescope Science Institute, which is operated by the Association of Universities for Research in Astronomy, Inc., under NASA contract NAS 5-03127 for JWST. These observations are associated with program #2078 and can be accessed via . Support for program #2078 was provided by NASA through a grant from the Space Telescope Science Institute, which is operated by the Association of Universities for Research in Astronomy, Inc., under NASA contract NAS 5-03127. We acknowledge the strong support provided by the program coordinator Weston Eck and instrument reviewers Norbert Pirzkal and Stephanie La Massa.

This paper makes use of the following ALMA data: ADS/JAO.ALMA#2022.1.01077.L. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. The National Radio Astronomy Observatory is a facility of the National Science Foundation operated under cooperative agreement by Associated Universities, Inc.

# Facilities

JWST (NIRCam)

# Software

astropy (cite: Astropy), Matplotlib (cite: Matplotlib), Numpy (cite: Numpy), Photutils (cite: photutils), Scipy (cite: Scipy),

Source Extractor (cite: SExtractor)

natexlab

(ref: Arita23) Arita, J., Kashikawa, N., Matsuoka, Y., et al. 2023, ApJ, 954, 210, doi: [`10.3847/1538-4357/ace43a`](http://doi.org/10.3847/1538-4357/ace43a)

(ref: Astropy) Astropy Collaboration, Price-Whelan, A. M., Sipőcz, B. M., et al. 2018, AJ, 156, 123, doi: [`10.3847/1538-3881/aabc4f`](http://doi.org/10.3847/1538-3881/aabc4f)

(ref: Banados18a) Bañados, E., Venemans, B. P., Mazzucchelli, C., et al. 2018, Nature, 553, 473, doi: [`10.1038/nature25180`](http://doi.org/10.1038/nature25180)

(ref: Banados21) Bañados, E., Mazzucchelli, C., Momjian, E., et al. 2021, ApJ, 909, 80, doi: [`10.3847/1538-4357/abe239`](http://doi.org/10.3847/1538-4357/abe239)

(ref: Begelman06) Begelman, M. C., Volonteri, M., & Rees, M. J. 2006, MNRAS, 370, 289, doi: [`10.1111/j.1365-2966.2006.10467.x`](http://doi.org/10.1111/j.1365-2966.2006.10467.x)

(ref: Behroozi19) Behroozi, P., Wechsler, R. H., Hearin, A. P., & Conroy, C. 2019, MNRAS, 488, 3143, doi: [`10.1093/mnras/stz1182`](http://doi.org/10.1093/mnras/stz1182)

(ref: Belladitta25) Belladitta, S., Bañados, E., Xie, Z.-L., et al. 2025, A&A, 699, A335, doi: [`10.1051/0004-6361/202554859`](http://doi.org/10.1051/0004-6361/202554859)

(ref: SExtractor) Bertin, E., & Arnouts, S. 1996, A&AS, 117, 393, doi: [`10.1051/aas:1996164`](http://doi.org/10.1051/aas:1996164)

(ref: Bertin20) Bertin, E., Schefer, M., Apostolakos, N., et al. 2020, in Astronomical Society of the Pacific Conference Series, Vol. 527, Astronomical Data Analysis Software and Systems XXIX, ed. R. Pizzo, E. R. Deul, J. D. Mol, J. de Plaa, & H. Verkouter, 461

(ref: Bird22) Bird, S., Ni, Y., Di Matteo, T., et al. 2022, MNRAS, 512, 3703, doi: [`10.1093/mnras/stac648`](http://doi.org/10.1093/mnras/stac648)

(ref: Interferopy) Boogaard, L., Meyer, R. A., & Novak, M. 2021, Interferopy: Analyzing datacubes from radio-to-submm observations, Astrophysics Source Code Library, record ascl:2112.005

(ref: photutils) Bradley, L., Sipocz, B., Robitaille, T., et al. 2022, astropy/photutils: 1.5.0, 1.5.0, Zenodo, doi: [`10.5281/zenodo.6825092`](http://doi.org/10.5281/zenodo.6825092)

(ref: Champagne24a) Champagne, J. B., Wang, F., Zhang, H., et al. 2025, ApJ, 981, 2, 113. doi:10.3847/1538-4357/adb1bd

(ref: Champagne24b) Champagne, J. B., Wang, F., Yang, J., et al. 2025, ApJ, 981, 2, 114. doi:10.3847/1538-4357/adb1bc

(ref: Costa24) Costa, T. 2024, MNRAS, 531, 930, doi: [`10.1093/mnras/stae1157`](http://doi.org/10.1093/mnras/stae1157)

(ref: Costa14) Costa, T., Sijacki, D., Trenti, M., & Haehnelt, M. G. 2014, MNRAS, 439, 2146, doi: [`10.1093/mnras/stu101`](http://doi.org/10.1093/mnras/stu101)

(ref: Coughlin24) Coughlin, E. R., & Begelman, M. C. 2024, ApJ, 970, 158, doi: [`10.3847/1538-4357/ad5723`](http://doi.org/10.3847/1538-4357/ad5723)

(ref: Dave19) Davé, R., Anglés-Alcázar, D., Narayanan, D., et al. 2019, MNRAS, 486, 2827, doi: [`10.1093/mnras/stz937`](http://doi.org/10.1093/mnras/stz937)

(ref: Davies19) Davies, F. B., Hennawi, J. F., & Eilers, A.-C. 2019, ApJL, 884, L19, doi: [`10.3847/2041-8213/ab42e3`](http://doi.org/10.3847/2041-8213/ab42e3)

(ref: Decarli17) Decarli, R., Walter, F., Venemans, B. P., et al. 2017, Nature, 545, 457, doi: [`10.1038/nature22358`](http://doi.org/10.1038/nature22358)

(ref: DiMatteo17) Di Matteo, T., Croft, R. A. C., Feng, Y., Waters, D., & Wilkins, S. 2017, MNRAS, 467, 4243, doi: [`10.1093/mnras/stx319`](http://doi.org/10.1093/mnras/stx319)

(ref: DiMatteo05) Di Matteo, T., Springel, V., & Hernquist, L. 2005, Nature, 433, 604, doi: [`10.1038/nature03335`](http://doi.org/10.1038/nature03335)

(ref: Ding23) Ding, X., Onoue, M., Silverman, J. D., et al. 2023, Nature, 621, 51, doi: [`10.1038/s41586-023-06345-5`](http://doi.org/10.1038/s41586-023-06345-5)

(ref: Dubois14) Dubois, Y., Pichon, C., Welker, C., et al. 2014, MNRAS, 444, 1453, doi: [`10.1093/mnras/stu1227`](http://doi.org/10.1093/mnras/stu1227)

(ref: Eftekharzadeh15) Eftekharzadeh, S., Myers, A. D., White, M., et al. 2015, MNRAS, 453, 2779, doi: [`10.1093/mnras/stv1763`](http://doi.org/10.1093/mnras/stv1763)

(ref: Eilers24) Eilers, A.-C., Mackenzie, R., Pizzati, E., et al. 2024, arXiv e-prints, arXiv:2403.07986, doi: [`10.48550/arXiv.2403.07986`](http://doi.org/10.48550/arXiv.2403.07986)

(ref: Endsley21) Endsley, R., Stark, D. P., Chevallard, J., & Charlot, S. 2021, MNRAS, 500, 5229, doi: [`10.1093/mnras/staa3370`](http://doi.org/10.1093/mnras/staa3370)

(ref: Fan01) Fan, X., Narayanan, V. K., Lupton, R. H., et al. 2001, AJ, 122, 2833, doi: [`10.1086/324111`](http://doi.org/10.1086/324111)

(ref: Farina22) Farina, E. P., Schindler, J.-T., Walter, F., et al. 2022, ApJ, 941, 106, doi: [`10.3847/1538-4357/ac9626`](http://doi.org/10.3847/1538-4357/ac9626)

(ref: Fontanot25) Fontanot, F., Decarli, R., De Lucia, G., et al. 2025, arXiv:2511.15789. doi:10.48550/arXiv.2511.15789

(ref: emcee) Foreman-Mackey, D., Hogg, D. W., Lang, D., & Goodman, J. 2013, PASP, 125, 306, doi: [`10.1086/670067`](http://doi.org/10.1086/670067)

(ref: Garcia17) Garcı́a-Vergara, C., Hennawi, J. F., Barrientos, L. F., & Rix, H.-W. 2017, ApJ, 848, 7, doi: [`10.3847/1538-4357/aa8b69`](http://doi.org/10.3847/1538-4357/aa8b69)

(ref: Greene24) Greene, J. E., Labbe, I., Goulding, A. D., et al. 2024, ApJ, 964, 39, doi: [`10.3847/1538-4357/ad1e5f`](http://doi.org/10.3847/1538-4357/ad1e5f)

(ref: Habouzit19) Habouzit, M., Volonteri, M., Somerville, R. S., et al. 2019, MNRAS, 489, 1206, doi: [`10.1093/mnras/stz2105`](http://doi.org/10.1093/mnras/stz2105)

(ref: Numpy) Harris, C. R., Millman, K. J., van der Walt, S. J., et al. 2020, Nature, 585, 357, doi: [`10.1038/s41586-020-2649-2`](http://doi.org/10.1038/s41586-020-2649-2)

(ref: hennawi06b) Hennawi, J. F., Strauss, M. A., Oguri, M., et al. 2006, AJ, 131, 1

(ref: Horne86) Horne, K. 1986, PASP, 98, 609, doi: [`10.1086/131801`](http://doi.org/10.1086/131801)

(ref: Huang26) Huang, J., Hennawi, J., Pizzati, E., et al. 2026, arXiv:2602.04974. doi:10.48550/arXiv.2602.04974

(ref: Matplotlib) Hunter, J. D. 2007, Computing in Science & Engineering, 9, 90, doi: [`10.1109/MCSE.2007.55`](http://doi.org/10.1109/MCSE.2007.55)

(ref: Inayoshi20) Inayoshi, K., Visbal, E., & Haiman, Z. 2020, ARA&A, 58, 27. doi:10.1146/annurev-astro-120419-014455

(ref: Ishiyama21) Ishiyama, T., Prada, F., Klypin, A. A., et al. 2021, MNRAS, 506, 4210, doi: [`10.1093/mnras/stab1755`](http://doi.org/10.1093/mnras/stab1755)

(ref: Jin24) Jin, X., Yang, J., Fan, X., et al. 2024, ApJ, 976, 93, doi: [`10.3847/1538-4357/ad82de`](http://doi.org/10.3847/1538-4357/ad82de)

(ref: Kakiichi25) Kakiichi, K., Jin, X., Wang, F., et al. 2025, arXiv e-prints, arXiv:2503.07074, doi: [`10.48550/arXiv.2503.07074`](http://doi.org/10.48550/arXiv.2503.07074)

(ref: Khandai15) Khandai, N., Di Matteo, T., Croft, R., et al. 2015, MNRAS, 450, 1349, doi: [`10.1093/mnras/stv627`](http://doi.org/10.1093/mnras/stv627)

(ref: Kim09) Kim, S., Stiavelli, M., Trenti, M., et al. 2009, ApJ, 695, 809, doi: [`10.1088/0004-637X/695/2/809`](http://doi.org/10.1088/0004-637X/695/2/809)

(ref: Kocevski23) Kocevski, D. D., Onoue, M., Inayoshi, K., et al. 2023, ApJL, 954, L4, doi: [`10.3847/2041-8213/ace5a0`](http://doi.org/10.3847/2041-8213/ace5a0)

(ref: Laurent17) Laurent, P., Eftekharzadeh, S., Le Goff, J.-M., et al. 2017, JCAP, 2017, 017, doi: [`10.1088/1475-7516/2017/07/017`](http://doi.org/10.1088/1475-7516/2017/07/017)

(ref: Li25a) Li, Z., Cai, Z., Wang, X., et al. 2025a, ApJS, 280, 62, doi: [`10.3847/1538-4365/adfa70`](http://doi.org/10.3847/1538-4365/adfa70)

(ref: Li25b) Li, Z., Kakiichi, K., Christensen, L., et al. 2025b, arXiv e-prints, arXiv:2504.18616, doi: [`10.48550/arXiv.2504.18616`](http://doi.org/10.48550/arXiv.2504.18616)

(ref: Lin24) Lin, X., Wang, F., Fan, X., et al. 2024, arXiv e-prints, arXiv:2407.17570, doi: [`10.48550/arXiv.2407.17570`](http://doi.org/10.48550/arXiv.2407.17570)

(ref: Madau01) Madau, P., & Rees, M. J. 2001, ApJL, 551, L27, doi: [`10.1086/319848`](http://doi.org/10.1086/319848)

(ref: Matsuoka18c) Matsuoka, Y., Strauss, M. A., Kashikawa, N., et al. 2018, ApJ, 869, 150, doi: [`10.3847/1538-4357/aaee7a`](http://doi.org/10.3847/1538-4357/aaee7a)

(ref: Matthee22) Matthee, J., Mackenzie, R., Simcoe, R. A., et al. 2022, arXiv e-prints, arXiv:2211.08255. [`https://arxiv.org/abs/2211.08255`](https://arxiv.org/abs/2211.08255)

(ref: Matthee24) Matthee, J., Naidu, R. P., Brammer, G., et al. 2024, ApJ, 963, 129, doi: [`10.3847/1538-4357/ad2345`](http://doi.org/10.3847/1538-4357/ad2345)

(ref: Mazzucchelli17) Mazzucchelli, C., Bañados, E., Decarli, R., et al. 2017, ApJ, 834, 83, doi: [`10.3847/1538-4357/834/1/83`](http://doi.org/10.3847/1538-4357/834/1/83)

(ref: CASA) McMullin, J. P., Waters, B., Schiebel, D., Young, W., & Golap, K. 2007, in Astronomical Society of the Pacific Conference Series, Vol. 376, Astronomical Data Analysis Software and Systems XVI, ed. R. A. Shaw, F. Hill, & D. J. Bell, 127

(ref: Meyer22) Meyer, R. A., Decarli, R., Walter, F., et al. 2022, ApJ, 927, 141, doi: [`10.3847/1538-4357/ac4f67`](http://doi.org/10.3847/1538-4357/ac4f67)

(ref: Mignoli20) Mignoli, M., Gilli, R., Decarli, R., et al. 2020, A&A, 642, L1, doi: [`10.1051/0004-6361/202039045`](http://doi.org/10.1051/0004-6361/202039045)

(ref: Mo02) Mo, H. J., & White, S. D. M. 2002, MNRAS, 336, 112, doi: [`10.1046/j.1365-8711.2002.05723.x`](http://doi.org/10.1046/j.1365-8711.2002.05723.x)

(ref: Murray21) Murray, S. G., Diemer, B., Chen, Z., et al. 2021, Astronomy and Computing, 36, 100487, doi: [`10.1016/j.ascom.2021.100487`](http://doi.org/10.1016/j.ascom.2021.100487)

(ref: Murray13) Murray, S. G., Power, C., & Robotham, A. S. G. 2013, Astronomy and Computing, 3, 23, doi: [`10.1016/j.ascom.2013.11.001`](http://doi.org/10.1016/j.ascom.2013.11.001)

(ref: Naidu25) Naidu, R. P., Matthee, J., Katz, H., et al. 2025, arXiv e-prints, arXiv:2503.16596, doi: [`10.48550/arXiv.2503.16596`](http://doi.org/10.48550/arXiv.2503.16596)

(ref: Neeleman19b) Neeleman, M., Bañados, E., Walter, F., et al. 2019, ApJ, 882, 10, doi: [`10.3847/1538-4357/ab2ed3`](http://doi.org/10.3847/1538-4357/ab2ed3)

(ref: Neeleman21) Neeleman, M., Novak, M., Venemans, B. P., et al. 2021, ApJ, 911, 141, doi: [`10.3847/1538-4357/abe70f`](http://doi.org/10.3847/1538-4357/abe70f)

(ref: Nguyen20) Nguyen, N. H., Lira, P., Trakhtenbrot, B., et al. 2020, ApJ, 895, 1, 74. doi:10.3847/1538-4357/ab8bd3

(ref: Ni22) Ni, Y., Di Matteo, T., Bird, S., et al. 2022, MNRAS, 513, 670, doi: [`10.1093/mnras/stac351`](http://doi.org/10.1093/mnras/stac351)

(ref: Overzier22) Overzier, R. A. 2022, ApJ, 926, 114, doi: [`10.3847/1538-4357/ac448c`](http://doi.org/10.3847/1538-4357/ac448c)

(ref: Pillepich18) Pillepich, A., Nelson, D., Hernquist, L., et al. 2018, MNRAS, 475, 648, doi: [`10.1093/mnras/stx3112`](http://doi.org/10.1093/mnras/stx3112)

(ref: Pizzati24a) Pizzati, E., Hennawi, J. F., Schaye, J., et al. 2024, arXiv e-prints, arXiv:2403.12140, doi: [`10.48550/arXiv.2403.12140`](http://doi.org/10.48550/arXiv.2403.12140)

(ref: Pizzati25) Pizzati, E., Hennawi, J. F., Schaye, J., et al. 2025, MNRAS, 539, 4, 2910. doi:10.1093/mnras/staf660

(ref: Portegies04) Portegies Zwart, S. F., Baumgardt, H., Hut, P., Makino, J., & McMillan, S. L. W. 2004, Nature, 428, 724, doi: [`10.1038/nature02448`](http://doi.org/10.1038/nature02448)

(ref: Pypeit) Prochaska, J., Hennawi, J., Westfall, K., et al. 2020, The Journal of Open Source Software, 5, 2308, doi: [`10.21105/joss.02308`](http://doi.org/10.21105/joss.02308)

(ref: Pypeit_ascl) Prochaska, J. X., Hennawi, J., Cooke, R., et al. 2019, PypeIt: Python spectroscopic data reduction pipeline, Astrophysics Source Code Library, record ascl:1911.004. [`http://ascl.net/1911.004`](http://ascl.net/1911.004)

(ref: Pudoka24) Pudoka, M., Wang, F., Fan, X., et al. 2024, ApJ, 968, 118, doi: [`10.3847/1538-4357/ad488a`](http://doi.org/10.3847/1538-4357/ad488a)

(ref: Reed17) Reed, S. L., McMahon, R. G., Martini, P., et al. 2017, MNRAS, 468, 4702, doi: [`10.1093/mnras/stx728`](http://doi.org/10.1093/mnras/stx728)

(ref: Reed19) Reed, S. L., Banerji, M., Becker, G. D., et al. 2019, MNRAS, 487, 1874, doi: [`10.1093/mnras/stz1341`](http://doi.org/10.1093/mnras/stz1341)

(ref: Schaye15) Schaye, J., Crain, R. A., Bower, R. G., et al. 2015, MNRAS, 446, 521, doi: [`10.1093/mnras/stu2058`](http://doi.org/10.1093/mnras/stu2058)

(ref: Schindler26) Schindler, J.-T., Hennawi, J. F., Davies, F. B., et al. 2026, A&A, 708, A160. doi:10.1051/0004-6361/202557623

(ref: Schlafly11) Schlafly, E. F., & Finkbeiner, D. P. 2011, ApJ, 737, 103, doi: [`10.1088/0004-637X/737/2/103`](http://doi.org/10.1088/0004-637X/737/2/103)

(ref: Schlawin2020) Schlawin, E., Leisenring, J., Misselt, K., et al. 2020, AJ, 160, 231, doi: [`10.3847/1538-3881/abb811`](http://doi.org/10.3847/1538-3881/abb811)

(ref: schlegel98) Schlegel, D. J., Finkbeiner, D. P., & Davis, M. 1998, ApJ, 500, 525

(ref: Schleicher13) Schleicher, D. R. G., Palla, F., Ferrara, A., Galli, D., & Latif, M. 2013, A&A, 558, A59, doi: [`10.1051/0004-6361/201321949`](http://doi.org/10.1051/0004-6361/201321949)

(ref: Shen13) Shen, Y. 2013, Bulletin of the Astronomical Society of India, 41, 61, doi: [`10.48550/arXiv.1302.2643`](http://doi.org/10.48550/arXiv.1302.2643)

(ref: Shen10) Shen, Y., Hennawi, J. F., Shankar, F., et al. 2010, ApJ, 719, 2, 1693. doi:10.1088/0004-637X/719/2/1693

(ref: Shen07) Shen, Y., Strauss, M. A., Oguri, M., et al. 2007, AJ, 133, 2222, doi: [`10.1086/513517`](http://doi.org/10.1086/513517)

(ref: Simpson14) Simpson, C., Mortlock, D., Warren, S., et al. 2014, MNRAS, 442, 3454, doi: [`10.1093/mnras/stu1116`](http://doi.org/10.1093/mnras/stu1116)

(ref: Sinha20) Sinha, M., & Garrison, L. H. 2020, MNRAS, 491, 3022, doi: [`10.1093/mnras/stz3157`](http://doi.org/10.1093/mnras/stz3157)

(ref: Smit15) Smit, R., Bouwens, R. J., Franx, M., et al. 2015, ApJ, 801, 122, doi: [`10.1088/0004-637X/801/2/122`](http://doi.org/10.1088/0004-637X/801/2/122)

(ref: Sun22a) Sun, F., Egami, E., Pirzkal, N., et al. 2022a, ApJL, 936, L8, doi: [`10.3847/2041-8213/ac8938`](http://doi.org/10.3847/2041-8213/ac8938)

(ref: Sun22b) —. 2022b, arXiv e-prints, arXiv:2209.03374. [`https://arxiv.org/abs/2209.03374`](https://arxiv.org/abs/2209.03374)

(ref: Sun25) Sun, F., Wang, F., Yang, J., et al. 2025, ApJ, 980, 12, doi: [`10.3847/1538-4357/ad9d0e`](http://doi.org/10.3847/1538-4357/ad9d0e)

(ref: Trakhtenbrot17) Trakhtenbrot, B., Lira, P., Netzer, H., et al. 2017, ApJ, 836, 1, 8. doi:10.3847/1538-4357/836/1/8

(ref: Venemans19) Venemans, B. P., Neeleman, M., Walter, F., et al. 2019, ApJL, 874, L30, doi: [`10.3847/2041-8213/ab11cc`](http://doi.org/10.3847/2041-8213/ab11cc)

(ref: Venemans13) Venemans, B. P., Findlay, J. R., Sutherland, W. J., et al. 2013, ApJ, 779, 24, doi: [`10.1088/0004-637X/779/1/24`](http://doi.org/10.1088/0004-637X/779/1/24)

(ref: Venemans15a) Venemans, B. P., Bañados, E., Decarli, R., et al. 2015, ApJL, 801, L11, doi: [`10.1088/2041-8205/801/1/L11`](http://doi.org/10.1088/2041-8205/801/1/L11)

(ref: Venemans20) Venemans, B. P., Walter, F., Neeleman, M., et al. 2020, ApJ, 904, 130, doi: [`10.3847/1538-4357/abc563`](http://doi.org/10.3847/1538-4357/abc563)

(ref: Vestergaard06) Vestergaard, M., & Peterson, B. M. 2006, ApJ, 641, 689, doi: [`10.1086/500572`](http://doi.org/10.1086/500572)

(ref: Scipy) Virtanen, P., Gommers, R., Oliphant, T. E., et al. 2020, Nature Methods, 17, 261, doi: [`10.1038/s41592-019-0686-2`](http://doi.org/10.1038/s41592-019-0686-2)

(ref: Vogelsberger14) Vogelsberger, M., Genel, S., Springel, V., et al. 2014, MNRAS, 444, 1518, doi: [`10.1093/mnras/stu1536`](http://doi.org/10.1093/mnras/stu1536)

(ref: Walter16) Walter, F., Decarli, R., Aravena, M., et al. 2016, ApJ, 833, 67, doi: [`10.3847/1538-4357/833/1/67`](http://doi.org/10.3847/1538-4357/833/1/67)

(ref: Wang17) Wang, F., Fan, X., Yang, J., et al. 2017, ApJ, 839, 27, doi: [`10.3847/1538-4357/aa689f`](http://doi.org/10.3847/1538-4357/aa689f)

(ref: Wang19b) Wang, F., Yang, J., Fan, X., et al. 2019, ApJ, 884, 30, doi: [`10.3847/1538-4357/ab2be5`](http://doi.org/10.3847/1538-4357/ab2be5)

(ref: Wang21a) —. 2021a, ApJL, 907, L1, doi: [`10.3847/2041-8213/abd8c6`](http://doi.org/10.3847/2041-8213/abd8c6)

(ref: Wang21b) Wang, F., Fan, X., Yang, J., et al. 2021b, ApJ, 908, 53, doi: [`10.3847/1538-4357/abcc5e`](http://doi.org/10.3847/1538-4357/abcc5e)

(ref: Wang23) Wang, F., Yang, J., Hennawi, J. F., et al. 2023, ApJL, 951, L4, doi: [`10.3847/2041-8213/accd6f`](http://doi.org/10.3847/2041-8213/accd6f)

(ref: Wang24b) Wang, F., Yang, J., Fan, X., et al. 2024a, ApJ, 968, 9, doi: [`10.3847/1538-4357/ad3fb4`](http://doi.org/10.3847/1538-4357/ad3fb4)

(ref: Wang24a) Wang, F., Yang, J., Hennawi, J. F., et al. 2024b, ApJL, 962, L11, doi: [`10.3847/2041-8213/ad20ef`](http://doi.org/10.3847/2041-8213/ad20ef)

(ref: Wechsler18) Wechsler, R. H., & Tinker, J. L. 2018, ARA&A, 56, 435, doi: [`10.1146/annurev-astro-081817-051756`](http://doi.org/10.1146/annurev-astro-081817-051756)

(ref: Willott05) Willott, C. J., Percival, W. J., McLure, R. J., et al. 2005, ApJ, 626, 657, doi: [`10.1086/430168`](http://doi.org/10.1086/430168)

(ref: Wu23) Wu, Y., Wang, F., Cai, Z., et al. 2023, ApJL, 956, L40, doi: [`10.3847/2041-8213/acfee3`](http://doi.org/10.3847/2041-8213/acfee3)

(ref: Yang20a) Yang, J., Wang, F., Fan, X., et al. 2020, ApJL, 897, L14, doi: [`10.3847/2041-8213/ab9c26`](http://doi.org/10.3847/2041-8213/ab9c26)

(ref: Yang21) —. 2021, ApJ, 923, 262, doi: [`10.3847/1538-4357/ac2b32`](http://doi.org/10.3847/1538-4357/ac2b32)

(ref: Yang23) —. 2023, ApJL, 951, L5, doi: [`10.3847/2041-8213/acc9c8`](http://doi.org/10.3847/2041-8213/acc9c8)

(ref: Yue24) Yue, M., Eilers, A.-C., Simcoe, R. A., et al. 2024, ApJ, 966, 176, doi: [`10.3847/1538-4357/ad3914`](http://doi.org/10.3847/1538-4357/ad3914)

(ref: Zana23) Zana, T., Carniani, S., Prelogović, D., et al. 2023, A&A, 679, A77. doi:10.1051/0004-6361/202347172

(ref: Zana22) Zana, T., Gallerani, S., Carniani, S., et al. 2022, MNRAS, 513, 2, 2118. doi:10.1093/mnras/stac978

(ref: Zhang23) Zhang, H., Behroozi, P., Volonteri, M., et al. 2023, MNRAS, 518, 2123, doi: [`10.1093/mnras/stac2633`](http://doi.org/10.1093/mnras/stac2633)

(ref: Zou24) Zou, S., Cai, Z., Wang, F., et al. 2024, ApJL, 963, L28, doi: [`10.3847/2041-8213/ad23e7`](http://doi.org/10.3847/2041-8213/ad23e7)

[^1]: <https://github.com/spacetelescope/jwst>

[^2]: For a few quasar fields that do not have enough GAIA stars, we aligned images to the DESI Legacy Imaging Surveys

[^3]: <https://github.com/spacetelescope/tweakwcs>

[^4]: <https://photutils.readthedocs.io>

[^5]: <https://github.com/halomod/halomod>

</paper>

## Items to check

```json
[
 {
  "path": "analysis_steps[3].validation.evidence[1]",
  "value": "Consistent CCF between [O III] and [C II] emitters; compared with TRINITY + Uchuu simulation predictions",
  "failed_quote": "The TRINITY predicted quasar-[O III] emitter cross-correlation function is shown in Figure 8."
 }
]
```
