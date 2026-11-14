# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2023Ap%26SS.368...33M\gemini4argon\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
# Identification of interstellar cyanamide towards the hot molecular core G358.93–0.03 MM1

## Abstract

The amide-related molecules are essential for the formation of the other complex bio-molecules and an understanding of the prebiotic chemistry in the interstellar medium (ISM). We presented the first detection of the rotational emission lines of the amide-like molecule cyanamide () towards the hot molecular core G358.93–0.03 MM1 using the Atacama Large Millimeter/Submillimeter Array (ALMA). Using the rotational diagram model, the derived column density of towards the G358.93–0.03 MM1 was (5.9$\pm$2.5)$\times$10$^{14}$ cm$^{-2}$ with a rotational temperature of 100.6$\pm$30.4 K. The derived fractional abundance of towards the G358.93–0.03 MM1 with respect to was (4.72$\pm$2.0)$\times$10$^{-10}$, which is very similar to the existent three-phase warm-up chemical model abundances of . We compare the estimated abundance of towards G358.93–0.03 MM1 with other sources, and we observe the abundance of towards G358.93–0.03 MM1 is nearly similar to that of the sculptor galaxy NGC 253 and the low-mass protostars IRAS 16293–2422 B and NGC 1333 IRAS4A2. We also discussed the possible formation mechanisms of towards the hot molecular cores and hot corinos, and we find that the molecule was created in the grain-surfaces of G358.93–0.03 MM1 via the neutral-neutral reaction between and CN.

,

Department of Physics and Astronomy, Midnapore City College, Paschim Medinipur, West Bengal, India 721129\
ignoredarg: arijitmanna@mcconline.org.in

|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Band | Date of observation | Start time | End time | Number | Frequency range | Spectral resolution | Field of View (FOV) |  |  |  |  |  |  |  |  |  |
|  | (YYYY MMM DD) | (hh:mm) | (hh:mm) | of antennas | (GHz) | (kHz) | ($\prime\prime$) |  |  |  |  |  |  |  |  |  |
| 6 | 2019 Oct 07 | 22:01 | 22:23 | 42 | 216.44–217.38 | 488.28 | 26.599 |  |  |  |  |  |  |  |  |  |
|  |  |  |  |  | 218.08–218.55 | 282.23 |  |  |  |  |  |  |  |  |  |  |
|  |  |  |  |  | 219.88–220.35 | 282.23 |  |  |  |  |  |  |  |  |  |  |
|  |  |  |  |  | 220.33–220.80 | 282.23 |  |  |  |  |  |  |  |  |  |  |

# Introduction

The amide-type molecule cyanamide () was formed with amide and cyanide functional groups, which acted as a possible precursor of urea () in the ISM. The urea was formed via the hydrolysis of in the ISM (cite: kil47). The carbodiimide (HNCNH) molecule is known as one of the isomer of , which contains the –NCN– frame (cite: tur75; cou18). The molecules with the –NCN– frame play a major role in linking biological processes and in the assembly of amino acids into peptides (cite: wil81). The HNCNH molecule forms due to photochemical and thermally induced reactions of in interstellar ice analogues (cite: duv05). Except for urea, the molecule also acts as a possible precursor of 2-amino-oxazole, cytosine, 3’-cyclic phosphate (pyrimidine ribonucleotide), and beta-ribocytidine-2 via biochemistry synthesis routes towards the hot cores/corinos (cite: jim20). The molecule contains 0$^{+}$ and 0$^{-}$ substates with a pyramidal equilibrium structure (cite: sharma21). The dipole moments of the 0$^{+}$ and 0$^{-}$ substrates are $\mu_{a}=4.25\pm0.02$ D and $\mu_{a}=4.24\pm0.02$ D, respectively (cite: bro85; sharma21). In the ISM, evidence of was found towards the hot molecular cores Sgr B2 (N), Orion KL, IRAS 20126+410, and NGC 6334I (cite: tur75; whi03; pa17; lig20). The rotational emission lines of were also detected towards the low-mass solar-like protostars IRAS 16293–2422 B and NGC 1333 IRAS2A using the ALMA and Plateau de Bure Interferometer (PdBI) (cite: cou18). Outside of the Milky Way, evidence of the molecule was also found towards the sculptor galaxy NGC 253 and the starburst galaxy M82 (cite: mar06; ala11). Recently, the emission lines of were also detected towards the hot molecular core G10.47+0.03 using the ALMA band 4, with an estimated column density of 6.60$\times$10$^{15}$ cm$^{-2}$ and a rotational temperature of 201.2 K (cite: man22a).

The search for complex organic molecules using the millimeter and submillimeter telescopes in the star-formation regions gives us an idea about the chemistry in the ISM. The hot molecular cores are one of the highly chemically rich phases that are located in the high-mass star-formation regions, and they play an important role in increasing the chemical complexity in the ISM (cite: shi21). The hot molecular cores are the ideal astronomical objects in the ISM to study the different complex and prebiotic molecular lines because they have a warm temperature ($\geq$100 K), a high gas density ($n_{\ce{H2}}$$\geq$10$^{6}$ cm$^{-3}$), and a small source size ($\leq$0.1 pc) (cite: van98). The chemistry of the hot core is characterised by the sublimation of ice mantles, which accumulate during the star-formation activities (cite: shi21). The gaseous molecules and atoms are frozen onto the dust grains of cold molecular clouds and prestellar cores. When the temperature increases due to star-formation activities, the chemical interaction between heavy compounds becomes active on the grain surfaces, and the complex organic molecules are formed in the star-formation regions (cite: gar06; gar13; shi21). So, the highly dense, warm, and chemically rich abundant molecules around the protostars produce the strongest molecular line emitters, known as the hot molecular cores (cite: shi21). The period of the hot molecular cores is thought to last about 10$^{5}$ years (medium warm-up phase) to 10$^{6}$ years (slow warm-up phase) (cite: van98; gar06; gar13).

![](cont.pdf)

The hot molecular core G358.93–0.03 MM1 is located in the high-mass star-formation region G358.93–0.03. The high-mass star-formation region G358.93–0.03 is located at a distance of 6.75$\,{}\,^{\,+0.37}_{\,-0.68}$ kpc from the earth (cite: re14; bro19). The luminosity of the high-mass star-formation region G358.93–0.03 was $\sim$7.660$\times$10$^{3}$L$_{\odot}$ with total gas mass 167$\pm$12M$_{\odot}$ (cite: bro19). The high-mass star-formation region G358.93–0.03 has eight sub-millimeter wavelength continuum sources, i.e., G358.93–0.03 MM1 to G358.93–0.03 MM8. Among the eight sources, G358.93–0.03 MM1 and G358.93–0.03 MM3 emit the molecular line emission (cite: bro19). That means G358.93–0.03 MM1 and G358.93–0.03 MM3 are hot molecular cores because those two sources emit both continuum and line emission (cite: bro19; bay22). Earlier, (cite: bro19) claimed that G358.93–0.03 MM1 is more chemically rich than G358.93–0.03 MM3. Earlier, the maser lines of methanol (), durated water (HDO), and isocyanic acid (HNCO) were detected towards the G358.93–0.03 MM1 using the ALMA, TMRT, and VLA radio telescopes (cite: bro19; chen20). The emission lines of methyl cyanide () were also detected towards the G358.93–0.03 MM1 and the G358.93–0.03 MM3 using the ALMA (cite: bro19).

In this article, we present the first detection of the rotational emission lines of towards the hot molecular core region G358.93–0.03 MM1 using the ALMA band 6. The ALMA observations and data reduction of the high-mass star-formation region G358.93–0.03 were presented in Section [2](#obs). The result of the detection of emission lines of towards the G358.93–0.03 MM1 was shown in Section [3](#res). The discussion and conclusion of the detection of towards the G358.93–0.03 MM1 were shown in Section [4](#dis) and [5](#con).

# Observations and data reduction

The high-mass star-formation region G358.93–0.03 was observed using the Atacama Large Millimeter/Submillimeter Array (ALMA) band 6 (frequency range of 216.44–220.80 GHz) receiver to study the massive protostellar accretion outburst (ID: 2019.1.00768.S., PI: Crystal Brogan). The observations were conducted on October 7th, 2019 with on-source integration times of 604.80 sec. The phase centre of G358.93–0.03 was ($\alpha,\delta$)$_{\rm J2000}$ = 17:43:10.000, –29:51:46.000. The observation was carried out using the forty-two antennas, with a minimum baseline of 15 m and a maximum baseline of 783 m. During the observation, J1744–3116 was used as a phase calibrator, and J1924–2914 was used as a flux calibrator and bandpass calibrator. The observation details are shown in Table [\[tab:obs\]](#tab:obs).

We used the Common Astronomy Software Application (`CASA 5.4.1`) for the reduction of data using the ALMA data analysis pipeline (cite: mc07). For flux calibration, we applied the CASA task `SETJY` using the Perley-Butler 2017 flux calibrator model (cite: pal17). For bandpass calibration and flagging the band antenna data, we applied the CASA pipeline tasks `hifa_bandpassflag` and `hifa_flagdata`. After the flux calibration, bandpass calibration, and flagging of the bad channels, we employed the task `MSTRANSFORM` to separate the target object G358.93–0.03 with all available rest frequencies. We created four continuum emission images of G358.93–0.03 using the CASA task `TCLEAN` with the `HOGBOM` deconvolver using the frequency ranges of 216.44–217.38 GHz, 218.08–218.55 GHz, 219.88–220.35 GHz, and 220.33–220.80 GHz, respectively. Among the four individual continuum emission images, we have shown the sub-millimeter wavelength continuum emission map of the high-mass star-formation region G358.93–0.03 at frequency 218.316 GHz (1.37 mm) in Figure [1](#fig:cont) as an example. The continuum emission image of G358.93–0.03 was created using the Cube Analysis and Rendering Tool for Astronomy (CARTA) software package (cite: cm21). The bandwidth of this continuum emission image of G358.93–0.03 at frequency 218.316 GHz is 0.47 GHz. The effect of bandwidth smearing in those observed frequency ranges is minimal as according to (cite: mur20) the maximum bandwidth to avoid amplitude smearing between the frequency ranges of 216.44 GHz and 220.80 GHz is $\sim$1.2 GHz. From the continuum emission map of G358.93–0.03 at frequency 218.316 GHz, we identified the eight sub-millimeter wavelength continuum sources, G358.93–0.03 MM1 to G358.93–0.03 MM8. Among the eight sources, G358.93–0.03 MM1 and G358.93–0.03 MM3 are hot molecular cores because both sources emit the line emission as well as the emission lines of (cite: bro19). Earlier, (cite: bro19) showed the first sub-millimeter continuum emission map of G358.93–0.03, but the authors were unable to clearly identify the continuum sources G358.93–0.03 MM6 and G358.93–0.03 MM8 due to the lower image resolution. We first individually detected all eight sub-millimeter wavelength continuum sources in the massive star-formation region G358.93–0.03 using the ALMA at wavelength 1.37 mm with an angular resolution of 0.508$^{\prime\prime}$$\times$0.454$^{\prime\prime}$. After the continuum analysis, we employed the task `UVCONTSUB` to subtract the background continuum emission from the UV plane of the calibrated data. Now we created the spectral images at frequency ranges of 216.44–217.38 GHz, 218.08–218.55 GHz, 219.88–220.35 GHz, and 220.33–220.80 GHz using the task `TCLEAN` with the `SPECMODE` = `CUBE` parameter. Finally, we used the CASA task `IMPBCOR` for the correction of the synthesised beam pattern in the continuum and spectral images of G358.93–0.03.

|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Frequency | Wavelength | Integrated Flux | Peak flux | Beam size | RMS | Position angle |  |  |  |  |  |  |  |  |  |  |
| (GHz) | \(mm\) | (mJy) | (mJy beam$^{-1}$) | ($^{\prime\prime}$$\times$$^{\prime\prime}$) | ($\mu$Jy) | ($^{\circ}$) |  |  |  |  |  |  |  |  |  |  |
| 216.90 | 1.38 | 61.72$\pm$3.7 | 50.60$\pm$1.9 | 0.507$\times$0.456 | 22.12 | 88.879 |  |  |  |  |  |  |  |  |  |  |
| 218.31 | 1.37 | 72.31$\pm$3.8 | 56.83$\pm$1.8 | 0.508$\times$0.454 | 16.40 | 87.515 |  |  |  |  |  |  |  |  |  |  |
| 220.11 | 1.36 | 72.12$\pm$3.5 | 61.35$\pm$2.0 | 0.497$\times$0.455 | 28.23 | 89.169 |  |  |  |  |  |  |  |  |  |  |
| 220.56 | 1.35 | 77.91$\pm$4.2 | 69.42$\pm$2.2 | 0.494$\times$0.454 | 22.22 | 86.827 |  |  |  |  |  |  |  |  |  |  |

# Results

## Sub-millimeter wavelength continuum emission towards the G358.93–0.03 MM1

Among the eight sub-millimeter wavelength continuum sources, we mainly focus on the G358.93–0.03 MM1 ($\alpha,\delta_{\rm J2000}$ = 17:43:10.102, –29:51:45.714) because that source is the brightest sub-millimeter wavelength continuum source in the massive star-formation region G358.93–0.03, which hosts the line-rich hot core (cite: bro19; bay22). We presented the sub-millimeter wavelength continuum emission images of the G358.93–0.03 MM1 at frequencies of 216.90 GHz (1.38 mm), 218.31 GHz (1.37 mm), 220.11 GHz (1.36 mm), and 220.56 GHz (1.35 mm) in Figure [2](#fig:gcont). Now we used the CASA task `IMFIT` to fit the 2D Gaussian over all the continuum images and obtained an integrated flux density, peak flux density, synthesised beam size, position angle, and RMS, which are presented in Table [\[tab:cont\]](#tab:cont). We notice that the hot molecular core G358.93–0.03 MM1 was resolved in ALMA band 6 as it was found that the source was larger than the synthesised beam size. Earlier, (cite: bro19) also detected the millimeter-wavelength continuum emission from the eight individual continuum sources (G358.93–0.03 MM1 to G358.93–0.03 MM8) of G358.93–0.03 at frequencies of 195.58 GHz, 233.75 GHz, and 337.26 GHz, and the author mentioned the continuum emission maps of the eight individual continuum sources were resolved within the observable frequency ranges.

![](gcont.pdf)

## Estimation of hydrogen () column density and dust optical depth ($\tau_\nu$) towards the G358.93–0.03 MM1

The peak flux density (S$_\nu$) of optically thin dust continuum emission can be expressed as,

$$\begin{equation}
    S_\nu = B_\nu(T_d)\tau_\nu\Omega_{beam}
    
\end{equation}$$ where $\tau_\nu$ presented the optical depth, $B_\nu(T_d)$ indicated the Planck function at dust temperature $T_d$ (cite: whi92), and $\Omega_{beam} = (\pi/4 \ln 2)\times \theta_{major} \times \theta_{minor}$ is the solid angle of the synthesised beam. The expression of optical depth in terms of the mass density of dust can be written as,

$$\begin{equation}
    \tau_\nu =\rho_d\kappa_\nu L
    
\end{equation}$$ where $\kappa_{\nu}$ is the mass absorption coefficient, L is the path length, and $\rho_d$ indicates the mass density of dust. The mass density of the dust can be expressed in terms of the dust-to-gas mass ratio ($Z$).

$$\begin{equation}
    \rho_d = Z\mu_H\rho_{H_2}=Z\mu_HN_{H_2}2m_H/L
    
\end{equation}$$ where $\rho_{H_2}$ is the hydrogen mass density, $\mu_H$ presented the mean atomic mass per hydrogen, m$_H$ indicated the mass of hydrogen, and $N_{H_2}$ is the column density of hydrogen. We take the dust temperature $T_d$ to be 150 K (cite: chen20), $\mu_H = 1.41$, and $Z = 0.01$ (cite: cox00). The estimated peak flux density of the dust continuum of the G358.93–0.03 MM1 at different frequencies is presented in Table. [\[tab:cont\]](#tab:cont). From equations 1, 2, and 3, the column density of molecular hydrogen can be expressed as,

$$\begin{equation}
    N_{H_2} = \frac{S_\nu /\Omega}{2\kappa_\nu B_\nu(T_d)Z\mu_H m_H}
    
\end{equation}$$ During the estimation of the mass absorption coefficient ($\kappa_{\nu}$), we adopted the formula $\kappa_\nu = 0.90(\nu/230 GHz)^{\beta}\ cm^{2}\ g^{-1}$ (cite: moto19), where ${k_{230} = 0.90 \ cm^{2}\ g^{-1}}$ indicated the emissivity of the dust grains at a gas density of $\rm{10^{6}\ cm^{-3}}$, which covered by a thin ice mantle at 230 GHz. We used the dust spectral index $\beta$ $\sim$ 1.7 (cite: bro19). Using the mass absorption coefficient formula, we estimated the value of $\kappa_{\nu}$ to be 0.814, 0.823, 0.835, and 0.838 for frequencies of 216.90, 218.31, 220.11, and 220.56 GHz, respectively. We estimated the column density of hydrogen ($N_{\ce{H2}}$) for the four frequency regions towards the G358.93–0.03 MM1, which was presented in Table. [1](#table:column density). We take the average value to estimate the resultant hydrogen column density towards the G358.93–0.03 MM1. The estimated column density of hydrogen towards the G358.93–0.03 MM1 was (1.25$\pm$0.11)$\times$10$^{24}$ cm$^{-2}$. We also determine the value of optical depth ($\tau_\nu$) using the following equation,

$$\begin{equation}
    T_{mb} = T_{d}(1-exp(-\tau_\nu))
    
\end{equation}$$ where $T_{mb}$ is the brightness temperature and $T_{d}$ is the dust temperature of G358.93–0.03 MM1. For estimation of the brightness temperature, we used the Rayleigh-Jeans approximation, 1 Jy beam$^{-1} \equiv$ 118 K (cite: gor21). The calculated dust optical depth of G358.93–0.03 MM1 with individual frequencies was presented in Table. [1](#table:column density). The average dust optical depth was 0.0475. The estimated dust optical depth indicated that the G358.93–0.03 MM1 is optically thin between the frequency ranges of 216.44–220.80 GHz.

|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Wavelength | Hydrogen column density | Optical depth |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| (mm) | (cm$^{-2}$) | ($\tau_\nu$) |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| 1.38 | $\rm{(1.28\pm0.10)\times10^{24}}$ |  0.0397 |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| 1.37 | $\rm{(1.19\pm0.30)\times10^{24}}$ |  0.0457 |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| 1.36 | $\rm{(1.32\pm0.20)\times10^{24}}$ |  0.0502 |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| 1.35 | $\rm{(1.20\pm0.20)\times10^{24}}$ |  0.0561 |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  Average Value | $\rm{(1.25\pm0.11)\times10^{24}}$ |  0.0475 |  |  |  |  |  |  |  |  |  |  |  |  |  |  |

: Column density of hydrogen and optical depth towards G358.93–0.03 MM1.

![](NH2CN.pdf)

|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Observed frequency | Transition | $E_{u}$ | $A_{ij}$ | Peak intensity | S$\mu^{2}$ | FWHM | V$_{LSR}$ | $\rm{\int T_{mb}dV}$ | Remark |  |  |  |  |  |  |  |
| (GHz) | (${\rm J^{'}_{K_a^{'}K_c^{'}}}$–${\rm J^{''}_{K_a^{''}K_c^{''}}}$) | \(K\) | (s$^{-1}$) | \(K\) | (Debye$^{2}$)$^{\dagger}$ | (km s$^{-1}$) | (km s$^{-1}$) | (K km s$^{-1}$) |  |  |  |  |  |  |  |  |
| 218.394 | 11(1,11)–10(1,10), V = 1 | 148.33 | 1.05$\times$10$^{-3}$ |   3.459 | 199.330 | 3.358$\pm$0.18 | –16.51$\pm$0.21 | 10.457$\pm$1.21 | Non blended |  |  |  |  |  |  |  |
| 218.461 | 11(1,11)–10(1,10), V = 0 |   77.40 | 1.08$\times$10$^{-3}$ |   8.663 | 612.666 | 8.310$\pm$0.35 | –16.50$\pm$0.12 | 47.415$\pm$0.22 | Blended with |  |  |  |  |  |  |  |
| 219.875 | 11(2,10)–10(2,9), V = 0 | 121.29 | 1.07$\times$10$^{-3}$ |   6.266 | 198.970 | 3.534$\pm$0.13 | –16.49$\pm$0.94 | 18.059$\pm$0.22 | Non blended |  |  |  |  |  |  |  |
| 219.893 | 11(0,11)–10(0,10), V = 0 |   63.32 | 1.11$\times$10$^{-3}$ |   6.228 | 205.927 | 3.696$\pm$0.28 | –16.51$\pm$0.82 | 18.732$\pm$0.11 | Non blended |  |  |  |  |  |  |  |
| 219.914 | 11(2,9)–10(2,8), V = 0 | 121.29 | 1.07$\times$10$^{-3}$ |   6.025 | 198.996 | 3.728$\pm$0.25 | –16.52$\pm$0.23 | 17.249$\pm$0.51 | Non blended |  |  |  |  |  |  |  |
| 220.126 | 11(3,9)–10(3,8), V = 0 | 193.72 | 1.04$\times$10$^{-3}$ |   6.861 | 579.630 | 4.508$\pm$0.17 | –16.52$\pm$0.29 | 28.392$\pm$0.26 | Non blended |  |  |  |  |  |  |  |
| 220.127 | 11(3,8)–10(3,7), V = 0 | 193.72 | 10.4$\times$10$^{-3}$ |   6.861 | 579.624 | 4.506$\pm$0.36 | –16.49$\pm$0.17 | 28.389$\pm$0.29 | Non blended |  |  |  |  |  |  |  |

$^{\dagger}$–The values of the S$\mu^{2}$ were taken from the JPL molecular database (cite: pic98).

## Identification of the towards the G358.93–0.03 MM1

After the production of the spectral images of G358.9–0.03 from the observable frequency ranges, we see that only the spectra of G358.93–0.03 MM1 and G358.93–0.03 MM3 show any line emission. We did not observe any line emission from other sources in G358.93–0.03. We focus to study of the complex organic molecules on the G358.93–0.03 MM1 rather than the G358.93–0.03 MM3 because the G358.93–0.03 MM1 is more chemically rich than the G358.93–0.03 MM3. We extracted the sub-millimeter wavelength molecular rich spectra from the spectral images of G358.93–0.03 to create a 0.781$^{\prime\prime}$ diameter circular region over the hot molecular core G358.93–0.03 MM1 ($\alpha,\delta_{\rm J2000}$ = 17:43:10.102, –29:51:45.714). The systematic velocity of G358.93–0.03 MM1 was –16.5 km s$^{-1}$ (cite: bro19). We used the CASSIS (cite: vas15) with the `Line Analysis` module to examine the molecular emission lines from the sub-millimeter spectra of G358.93–0.03 MM1. After the spectral analysis, we identified the rotational emission lines of amide-like molecules from the sub-millimeter spectra G358.93–0.03 MM1 using the Jet Population Laboratory (JPL) (cite: pic98) spectroscopic database. We detected the seven rotational emission lines of at frequencies ranging from 216.44 to 220.80 GHz. There are no missing transition lines of within the observable frequency ranges as per the JPL molecular database.

After the identification, we fitted the Gaussian model over the detected rotational emission spectra of using the Levenberg-Marquardt algorithm, which was available in CASSIS. After fitting a Gaussian model over the detected spectra of , we obtained molecular transitions (${\rm J^{'}_{K_a^{'}K_c^{'}}}$–${\rm J^{''}_{K_a^{''}K_c^{''}}}$), upper state energy ($E_u$) in K, line intensity ($S\mu^{2}$) in Debye$^{2}$, FWHM in km s$^{-1}$, Einstein coefficients ($A_{ij}$) in s$^{-1}$, peak intensity in K, and integrated intensity ($\rm{\int T_{mb}dV}$) in K km s$^{-1}$. After the spectral analysis, we noticed J = 11(1,11)–10(1,10) V = 1, J = 11(2,10)–10(2,9) V = 0, J = 11(0,11)–10(0,10) V = 0, J = 11(2,9)–10(2,8) V = 0, J = 11(3,9)–10(3,8) V = 0, and J = 11(3,8)–10(3,7) V = 0 transition lines of are not contaminated with other nearby molecular transitions. We also observed that the J = 11(1,11)–10(1,10), V = 0 transition line of is blended with the molecular transition. During the spectral analysis, we notice the J = 11(3,9)–10(3,8) V = 0, and J = 11(3,8)–10(3,7) V = 0 transition lines of are present in a single spectral profile, which indicates the current spectral resolution is insufficient to resolve those two transition lines of towards the G358.93–0.03 MM1. The Gaussian-fitting rotational emission spectra of were shown in Figure [3](#fig:emission) and a summary of the Gaussian-fitting spectral line properties of was presented in Table [\[tab:MOLECULAR DATA\]](#tab:MOLECULAR DATA).

## Spatial distribution of towards the G358.93–0.03 MM1

We created the integrated emission maps of the non-blended transitions of towards the G358.93–0.03 MM1 using the CASA task `IMMOMENTS`. During the run of the task `IMMOMENTS`, we specified the channel ranges of the spectral images where the emission lines of were identified. The resultant integrated emission maps of the towards the G358.93–0.03 MM1 were shown in Figure [4](#fig:map), which was overlaid on the 1.37 mm continuum emission map. We observed that the integrated emission maps show a peak at the position of continuum emission. The integrated emission maps indicated that the rotational emission lines of mainly come from the highly dense, warm inner hot core region of the G358.93–0.03 MM1. Now we used the CASA task `IMFIT` for fitting the 2D Gaussian over the integrated emission maps of to estimate the emitting regions of . The deconvolved synthesised beam sizes of the emitting regions were derived by the following equation:\
$$\begin{equation}
    \theta_{S}=\sqrt{\theta^2_{50}-\theta^2_{beam}}     
    
\end{equation}$$ where $\theta_{beam}$ was the half-power width of the synthesised beam of the integrated emission maps and $\theta_{50} = 2\sqrt{A/\pi}$ presented the diameter of the circle whose area was surrounding the $50\%$ line peak of (cite: man22a; man22b). The derived emitting regions of are presented in Table [2](#tab:emittingregion). The emitting regions of were found to be in the range of 0.496$^{\prime\prime}$–0.513$^{\prime\prime}$. We observed that the derived emitting regions are comparable to or slightly greater than the synthesised beam sizes of the integrated emission maps. That indicates the transitions of were not well resolved spatially or, at best, marginally resolved towards the G358.93–0.03 MM1. So it is not possible to present any conclusions about the morphology of the spatial distribution of towards the G358.93–0.03 MM1. High-sensitivity data with higher spatial and angular resolution observations are required to understand the spatial distribution of towards the hot molecular core G358.93–0.03 MM1.

![](map.pdf)

|  |  |  |  |  |  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Transition | Frequency | E$_{up}$ | Emitting region |  |  |  |  |  |  |  |  |
| \[${\rm J^{'}_{K_a^{'}K_c^{'}}}$–${\rm J^{''}_{K_a^{''}K_c^{''}}}$\] | \[GHz\] | \[K\] | \[$^{\prime\prime}$\] |  |  |  |  |  |  |  |  |
| 11(1,11)–10(1,10), V = 1 | 218.394 | 148.33 | 0.501 |  |  |  |  |  |  |  |  |
| 11(2,10)–10(2,9), V = 0 | 219.875 | 121.29 | 0.496 |  |  |  |  |  |  |  |  |
| 11(0,11)–10(0,10), V = 0 | 219.893 |   63.32 | 0.512 |  |  |  |  |  |  |  |  |
| 11(2,9)–10(2,8), V = 0 | 219.914 | 121.29 | 0.498 |  |  |  |  |  |  |  |  |
| 11(3,9)–10(3,8), V = 0 | 220.126 | 193.72 | 0.513 |  |  |  |  |  |  |  |  |
| 11(3,8)–10(3,7), V = 0 | 220.127 | 193.72 | 0.513 |  |  |  |  |  |  |  |  |

: The emitting regions of non-blended transitions of towards the G358.93–0.03 MM1.

![](rotd.pdf)

## Rotational diagram analysis of 

In this work, we have identified the seven rotational emission lines of towards the G358.93–0.03 MM1. Rotational diagram analysis is the most efficient way to estimate the rotational temperature ($T_{rot}$) in K and the column density ($N$) in cm$^{-2}$ of the detected emission lines of . We used the rotational diagram model since we assumed that the observed rotational emission lines of are optically thin and that they are populated in local thermodynamic equilibrium (LTE) conditions. The LTE assumption was appropriate for the G358.93–0.03 MM1 because the gas density of the warm inner region of the hot core was $\sim$2$\times$10$^{7}$ cm$^{-3}$ (cite: ste21). The equation of column density of the optically thin molecular emission lines can be expressed as (cite: gold99),

$$\begin{equation}
    {N_u^{thin}}=\frac{3{g_u}k_B\int{T_{mb}dV}}{8\pi^{3}\nu S\mu^{2}}
    
\end{equation}$$ where $\mu$ indicates the dipole moments of the , $\nu$ is the rest frequency, $S$ indicates the line strength, $g_u$ is the degeneracy of the upper state, $\int T_{mb}dV$ indicates the integrated intensity of the detected emission lines of the , and $k_B$ is the Boltzmann constant. The total column density of under the LTE condition can be expressed as,

$$\begin{equation}
    \frac{N_u^{thin}}{g_u} = \frac{N_{total}}{Q(T_{rot})}\exp(-E_u/k_BT_{rot})
    
\end{equation}$$ where, $E_u$ is the upper-state energy of , $T_{rot}$ is the rotational temperature of , and ${Q(T_{rot})}$ indicates the partition function of rotational temperature ($T_{rot}$). The partition function of at 75 K, 150 K, and 300 K is 1730.290, 5730.062, and 17902.30, respectively. Equation 8 can be rearranged as,

$$\begin{equation}
    \ln\left(\frac{N_u^{thin}}{g_u}\right) = \ln(N)-\ln(Q(T_{rot}))-\left(\frac{E_u}{k_BT_{rot}}\right)
    
\end{equation}$$ The equation 9 presents a linear relation between $\ln(N_{u}/g_{u})$ and upper-state energy ($E_{u}$). After the estimation of $\ln(N_{u}/g_{u})$ from equation 7, we fit a straight line to the estimated values of $\ln(N_{u}/g_{u})$, which vary with $E_{u}$. After fitting the straight line, the rotational temperature was estimated from the inverse of the slope, and the column density was estimated from the intercept of the slope. For rotational diagram analysis, the spectral line parameters of are estimated by fitting a Gaussian model over the observed emission lines of , which were presented in Table [\[tab:MOLECULAR DATA\]](#tab:MOLECULAR DATA). After spectral analysis, we notice only the J = 11(1,11)–10(1,10) V = 0 transition line of is blended with , and that transition was excluded from the rotational diagram analysis. We observed that J = 11(2,10)–10(2,9) V = 0 and J = 11(2,9)–10(2,8) V = 0 transitions have the same upper-state energy of 121.29 K. During the rotational diagram, we used the J = 11(2,9)–10(2,8) V = 0 transition line because the line intensity of the J = 11(2,9)–10(2,8) V = 0 transition line is slightly higher than that of the J = 11(2,10)–10(2,9) V = 0 transition line. Similarly, we also observed that the J = 11(3,9)–10(3,8) V = 0 and J = 11(3,8)–10(3,7) V = 0 transitions of are present in the single spectral profile, and the upper-state energy of those two transitions is the same (193.72 K). So, we take the J = 11(3,9)–10(3,8) V = 0 transition line for the rotational diagram because the line intensity of J = 11(3,9)–10(3,8) V = 0 is slightly higher than the J = 11(3,8)–10(3,7) V = 0 transition line. The rotational diagram analysis was carried out using the J = 11(1,11)–10(1,10) V = 1, J = 11(0,11)–10(0,10) V = 0, J = 11(2,9)–10(2,8), V = 0, and J = 11(3,9)–10(3,8) V = 0 transition lines of . The resultant rotational diagram of , which was computed using the `ROTATIONAL DIAGRAM` module in CASSIS, is shown in Figure [5](#fig:rotd). In the rotational diagram, the vertical red error bars represent the absolute uncertainty of $\ln(N_{u}/g_{u})$, which was calculated from the $\int T_{mb}dV$ of the emission spectra. From the rotational diagram, the estimated column density of was (5.9$\pm$2.5)$\times$10$^{14}$ cm$^{-2}$ with a rotational temperature ($T_{rot}$) of 100.6$\pm$30.4 K. The derive rotational temperature indicates that the emission lines of arise from the warm inner region of the G358.93–0.03 MM1 because the temperature of the hot molecular core is above 100 K (cite: van98). The derived fractional abundance of with respect to towards the G358.93–0.03 MM1 was (4.72$\pm$2.0)$\times$10$^{-10}$, where the column density was (1.25$\pm$0.11)$\times$10$^{24}$ cm$^{-2}$.

# Discussion

## Comparison with other sources

Here we compare the observed abundance of in G358.93–0.03 MM1 and other hot molecular cores, galaxies, high and low-mass protostars, and molecular clouds, which are shown in Table [\[tab:comparision\]](#tab:comparision). The estimated abundance of towards the G358.93–0.03 MM1 is (4.72$\pm$2.0)$\times$10$^{-10}$. This means the abundance of towards the G358.93–0.03 MM1 is nearly similar to that of the sculptor galaxy NGC 253 and the low-mass protostars IRAS 16293–2422 B and NGC 1333 IRAS4A2. The abundance of towards G358.93–0.03 MM1 is approximately one order of magnitude higher as compared to the hot molecular cores Sgr B2(OH), Sgr B2(N), and Sgr B2(M), and the low-mass protostar NGC 1333 IRAS2A. Similarly, the abundance of towards G358.93–0.03 MM1 is approximately one order of magnitude lower as compared to the high-mass protostar IRAS 20126+4104 and the molecular cloud G+0.693. We also observed that the abundance of towards G358.93–0.03 MM1 is approximately two orders of magnitude lower as compared to the hot molecular core G10.47+0.03. This result indicates the formation route(s) of towards G358.93–0.03 MM1 is similar to NGC 253, IRAS 16293–2422 B, and NGC 1333 IRAS4A2.

|  |  |  |  |  |  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Source name | Type | $N$() | Tex | $N$() | Abundance | Reference |  |  |  |  |  |
|  |  | (cm$^{-2}$) | \(K\) | (cm$^{-2}$) |  |  |  |  |  |  |  |
| G358.93–0.03 MM1 | Hot molecular core | (5.90$\pm$2.5)$\times$10$^{14}$ | 100.6$\pm$30.4 | (1.25$\pm$0.11)$\times$10$^{24}$ | (4.72$\pm$2.0)$\times$10$^{-10}$ | This work |  |  |  |  |  |
| G10.47+0.03 | Hot molecular core | (6.60$\pm$0.1)$\times$10$^{15}$ | 201.2$\pm$3.3 | 1.30$\times$10$^{23}$ | 5.07$\times$10$^{-8}$ | (cite: man22a) |  |  |  |  |  |
| Sgr B2(OH) | Hot molecular core | 2.0$\times$10$^{15}$ | 15 | 5.0$\times$10$^{23}$ | 4.0$\times$10$^{-11}$ | (cite: cu86) |  |  |  |  |  |
| Sgr B2(N) | Hot molecular core | 2.3$\times$10$^{14}$ | 500 | 3.0$\times$10$^{24}$ | 7.6$\times$10$^{-11}$ | (cite: nu00) |  |  |  |  |  |
| Sgr B2(M) | Hot molecular core | 3.0$\times$10$^{13}$ | 68 | 2.0$\times$10$^{24}$ | 1.5$\times$10$^{-11}$ | (cite: nu00) |  |  |  |  |  |
| NGC 253 | Sculptor Galaxy | 1.2$\times$10$^{13}$ | 67 | 6.5$\times$10$^{22}$ | 2.0$\times$10$^{-10}$ | (cite: mar06) |  |  |  |  |  |
| IRAS 20126+4104 | High-mass protostar | 3.3$\times$10$^{15}$ | 210 | 2.7$\times$10$^{24}$ | 1.2$\times$10$^{-9}$ | (cite: pa17) |  |  |  |  |  |
| IRAS 16293–2422 B | Low-mass protostar | 7.0$\times$10$^{13}$ | 300 | 1.2$\times$10$^{25}$ | 2.0$\times$10$^{-10}$ | (cite: cou18) |  |  |  |  |  |
| NGC 1333 IRAS2A | Low-mass protostar | 2.5$\times$10$^{14}$ | 130 | 5.0$\times$10$^{24}$ | 5.0$\times$10$^{-11}$ | (cite: cou18) |  |  |  |  |  |
| NGC 1333 IRAS4A2 | Low-mass protostar | 8.5$\times$10$^{14}$ | 150 | 5.0$\times$10$^{24}$ | 1.7$\times$10$^{-10}$ | (cite: bel20) |  |  |  |  |  |
| G+0.693 | Giant molecular cloud | 3.8$\times$10$^{13}$ | 6.3 | 1.35$\times$10$^{23}$ | 2.3$\times$10$^{-9}$ | (cite: zh18) |  |  |  |  |  |

## Possible formation and destruction pathways of 

In the hot core and corino objects, the formation mechanism of was poorly understood. According to the KIDA (cite: wak12) astrochemistry molecular reactions database, there are no gas-phase reactions that produce the abundance of . We found two gas-phase reactions of in the UMIST 2012 (cite: mce13) astrochemistry chemical network database that have the ability to synthesise . According to the UMIST 2012 database, the molecule was created via the neutral-neutral reaction between NH$_{3}$ and CN (CN + NH$_{3} \longrightarrow$ NH$_{2}$CN + H) and electron recombination of NH$_{2}$CNH$^{+}$ (NH$_{2}$CNH$^{+}$ + e$^{-} \longrightarrow$ NH$_{2}$CN + H). Earlier, (cite: cou18) also proposed another pathway for the formation of via the neutral-neutral reaction between and CN (NH$_{2}$ + CN $\longrightarrow$ NH$_{2}$CN). Earlier, (cite: man22a) claimed the neutral-neutral reaction between and CN is responsible for the formation of towards the hot molecular core G10.47+0.03. The electron recombination of NH$_{2}$CNH$^{+}$ was assumed to create only in 5% of cases (cite: bel17). Earlier, (cite: cou18) claimed the neutral-neutral reaction between and CN is the most effective pathway to produce on the grain surface of hot cores and corinos. Recently, (cite: zh23) also claimed the neutral-neutral reaction between and HNC is responsible for the formation of towards the hot corinos and hot molecular cores. Similarly, will be destroyed via photochemical reaction (NH$_{2}$CN + h$\nu$ $\longrightarrow$ NH$_{2}$ + CN), cosmic ray-induced photoreaction (NH$_{2}$CN + CRPHOT $\longrightarrow$ NH$_{2}$ + CN), and ion-neutral reaction (H$_{3}$$^{+}$ + NH$_{2}$CN $\longrightarrow$ NH$_{2}$CNH$^{+}$ + H$_{2}$) (cite: mce13). Recently, (cite: zh23) also presented more destruction pathways of in Table 2 in the context of hot corinos and hot molecular cores.

## Previous chemical modelling of in the hot molecular cores

To understand the formation mechanisms and abundance of towards hot molecular cores and hot corinos, (cite: cou18) used the three-phase (gas + dust + ice) warm-up chemical model using the chemical kinetics code MAGICKAL (cite: gar13). The chemical modelling of (cite: cou18) is similar to the three-phase warm-up chemical model of (cite: gar13) which was applied towards the hot molecular cores. During the chemical modelling, (cite: cou18) used both low-density (1.6$\times$10$^{7}$ cm$^{-3}$) and high-density (6.0$\times$10$^{10}$ cm$^{-3}$) conditions. The high-density (6.0$\times$10$^{10}$ cm$^{-3}$) model is reasonable towards the hot corinos objects (IRAS 16293–2422, NGC 1333 IRAS2A, etc.) because the gas density of the hot corinos varies between $\sim$10$^{9}$ and $\sim$10$^{10}$ cm$^{-3}$ (cite: cou18). The low-density (1.6$\times$10$^{7}$ cm$^{-3}$) model is reasonable towards the hot molecular core objects (G10.47+0.03, G31.41+0.31, Sgr B2, Orion KL, etc.) because the gas density of the hot molecular core varies between $\sim$10$^{6}$ to $\sim$10$^{8}$ cm$^{-3}$ (cite: van98; gar13). During the chemical modelling of in low-density conditions, (cite: cou18) used the neutral-neutral reaction between and CN ( + CN $\rightarrow$ ) in the grain/ice chemical network to estimate the abundance of . During the chemical modelling of in low-density conditions, (cite: cou18) considered an isothermal collapse phase followed by a static warm-up phase. In the first phase (the free-fall collapse stage), the gas density rapidly increased from $\sim$1.1$\times$10$^{3}$ to 1.6$\times$10$^{7}$ cm$^{-3}$, while the dust temperature decreased from 16 K to 8 K. In the second phase (the warm-up stage), the density of gas was fixed at 1.6$\times$10$^{7}$ cm$^{-3}$ and the temperature of the dust fluctuated between 8 K and 400 K. After the modelling, (cite: cou18) estimated that the abundance of was 3.7$\times$10$^{-10}$ in the case of the low-density model in the warm-up stage.

To ensure the chemical modelling of (cite: cou18), we also examined another three-phase warm-up chemical modelling of created by (cite: zh23). For chemical modelling of towards the hot molecular cores, (cite: zh23) used the NAUTILUS chemical code, which includes the gas, dust surface, and icy mantle. In the first phase (the freefall collapse stage), (cite: zh23) assumed the hot molecular cores undergoes the isothermal collapse phase at 10 K, and gas density rapidly increases from $n_{H}$ = 3$\times$10$^{3}$ cm$^{-3}$ to 1.6$\times$10$^{7}$ cm$^{-3}$. The first phase begins at $A_{V}$ = 2 mag and progresses to more than 200 mag. In the second phase (the warm-up phase), the gas density is fixed at 1.6$\times$10$^{7}$ cm$^{-3}$, and the temperature increases from 10 K to 200 K over the time scale 4$\times$10$^{5}$ yr. During the chemical modelling of , (cite: zh23) used the reaction + CN$\rightarrow$ in the grain surface to estimate the abundance of . In the warm-up phase, (cite: zh23) observed that the abundance of varies between 2.0$\times$10$^{-10}$ to 6.0$\times$10$^{-9}$.

## Comparision between observed and modelled abundances of 

To understand the formation pathways of towards G358.93–0.03 MM1, we compare our estimated observed abundance of with the modelled abundance of estimated by the low-density model of (cite: cou18) and (cite: zh23). This comparison is physically reasonable because the temperature and gas density of G358.93–0.03 MM1 are $\sim$150 K (cite: chen20) and $\sim$2$\times$10$^{7}$ cm$^{-3}$ (cite: ste21), respectively. Earlier, (cite: cou18) showed that the modelled abundance of is 3.7$\times$10$^{-10}$. Similarly, (cite: zh23) observed the abundance of varies between 2.0$\times$10$^{-10}$ to 6.0$\times$10$^{-9}$. We find that our estimated abundance of towards G358.93–0.03 MM1 is (4.72$\pm$2.0)$\times$10$^{-10}$, which is very close to the range of the modelled abundance of in (cite: cou18) and (cite: zh23). This comparison indicates that molecule is created in the grain surfaces of G358.93–0.03 MM1 via the neutral-neutral reaction between and CN ( + CN $\rightarrow$ ).

## Searching of urea () towards the G358.93–0.03 MM1

After the detection of the possible urea () precursor molecule from the G358.93–0.03 MM1, we also attempted to search for the rotational emission lines of from the sub-millimeter spectra of the G358.93–0.03 MM1. After careful spectral analysis, we did not detect the emission lines of within the limits of our LTE spectral modelling. We estimated the upper limit column density of was $\leq$(1.2$\pm$0.8)$\times$10$^{13}$ cm$^{-2}$. Furthermore, we calculated the upper limit of the and column density ratios towards the G358.93–0.03 MM1 as 0.020$\pm$0.016. For searching the emission lines of , we used the Cologne Database for Molecular Spectroscopy (CDMS) spectroscopic molecular database (cite: mu05). Our detection of the amide-like molecule towards the hot molecular core G358.93–0.03 MM1 using the ALMA gives more confidence that the G358.93–0.03 MM1 has the ability to create other amide-related molecules. We propose a spectral line survey of formamide (), acetamide (), and N-methyl formamide () with better spectral resolution and a higher integration time to solve the prebiotic chemistry of the amide-related molecules in the ISM.

# Conclusion

We analysed the ALMA band 6 data of the high-mass star-formation region G358.93–0.03, and we extracted the molecular lines from the hot molecular core G358.93–0.03 MM1. The main conclusions of this work are as follows:\
\
1. We identified a total of seven rotational emission lines of towards the hot molecular core G358.93–0.03 MM1 using the ALMA band 6 observations.\
\
2. The estimated column density of towards the G358.93–0.03 MM1 was (5.9$\pm$2.5)$\times$10$^{14}$ cm$^{-2}$ with a rotational temperature of 100.6$\pm$30.4 K. The derived abundance of towards the G358.93–0.03 MM1 with respect to was (4.72$\pm$2.0)$\times$10$^{-10}$.\
\
3. We compared the estimated abundance of towards G358.93–0.03 MM1 with other sources. We observe the abundance of towards G358.93–0.03 MM1 is nearly similar to that of the sculptor galaxy NGC 253 and the low-mass protostars IRAS 16293–2422 B and NGC 1333 IRAS4A2. That means the formation route(s) of towards G358.93–0.03 MM1 are similar to NGC 253, IRAS 16293–2422 B, and NGC 1333 IRAS4A2.\
\
4. We compared our estimated abundance of with the modelled abundances of , which was estimated by (cite: cou18) and (cite: zh23). After the comparison, we found that the observed abundance of is nearly similar to the modelled abundances of . This comparison indicates that the molecule was created in the grain surfaces of G358.93–0.03 MM1 via the neutral-neutral reaction between and CN ( + CN $\rightarrow$ ).\
\
5. After the identification of the towards the G358.93–0.03 MM1, we also looked for the emission lines of urea (). After the spectral analysis, we did not detect the emission lines of within the limits of LTE analysis. We estimated the upper limit column density of as $\leq$(1.2$\pm$0.8)$\times$10$^{13}$ cm$^{-2}$. We also derive the upper limit of the and column density ratios towards the G358.93–0.03 MM1 as 0.020$\pm$0.016. The unsuccessful detection of using the ALMA indicated that the emission lines of may be below the confusion limit towards the G358.93–0.03 MM1.

# Acknowledgments

We thank the anonymous referee for the helpful comments that improved the manuscript. A.M. acknowledges the Swami Vivekananda Merit-cum-Means Scholarship (SVMCM) for financial support for this research. This paper makes use of the following ALMA data: ADS /JAO.ALMA#2019.1.00768.S. ALMA is a partnership of ESO (representing its member states), NSF (USA), and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in co-operation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO, and NAOJ. \
\

# Data availability

The data that support the plots within this paper and other findings of this study are available from the corresponding author upon reasonable request. The raw ALMA data are publicly available at <https://almascience.nao.ac.jp/asax/> (project id: 2019.1.00768.S).

# Funding

No funds or grants were received during the preparation of this manuscript.

# Conflicts of interest

The authors declare no conflict of interest.

# Author Contributions

S.P. conceptualize the project. A.M. analysed the ALMA data and identify the emission lines of cyanamide () from G358.93–0.03 MM1. A.M. analyses the rotational diagram to derive the column density and rotational temperature of . A.M. and S.P. wrote the main manuscript text. All authors reviewed the manuscript.

(ref: ala11) Aladro, R., Martı́n, S., Martı́n-Pintado, J. et al. 2011, A&A, 535, A84

(ref: bay22) Bayandina, O.S., Brogan, C.L., Burns, R.A., et al. 2022, AJ, 163(2), p.83

(ref: bel17) Belloche, A., Meshcheryakov, A. A., Garrod, R. T., et al. 2017, A&A, 601, A49

(ref: bel20) Belloche A. et al., 2020, A&A , 635, A198

(ref: bro19) Brogan, C. L., Hunter, T. R., Towner, A. P. M., et al. 2019, ApJL, 881, L39

(ref: bro85) Brown, R. D., Godfrey, P. D., Kleibömer, B., 1985, Journal of Molecular Spectroscopy, 2, 257-273

(ref: chen20) Chen, X., Sobolev, A. M., Ren, Z.-Y., et al. 2020, NatAs, 4, 1170

(ref: cou18) Coutens, A., Willis, E. R., Garrod, R. T., et al. 2018, A&A, 612, A107

(ref: cm21) Comrie, A., Wang, K.-S., Ford, P., et al. 2021, CARTA: The Cube Analysis and Rendering Tool for Astronomy, 1.3.0, Zenodo

(ref: cu86) Cummins S. E., Linke R. A., Thaddeus P., 1986, ApJS , 60, 819

(ref: duv05) Duvernay, F., Chiavassa, T., Borget, F., & Aycard, J.-P. 2005, J. Phys. Chem. A, 109, 603

(ref: gar06) Garrod, R. T., & Herbst, E. 2006, A&A, 457, 927

(ref: gar13) Garrod, R. T. 2013, ApJ, 765, 60

(ref: gold99) Goldsmith, P. F., & Langer, W. D. 1999, ApJ, 517, 209

(ref: gor21) Gorai, P., Das, A., Shimonishi, T., et al. 2021, ApJ, 907, 108

(ref: jim20) Jiménez-Serra, I., Martı́n-Pintado, J., Rivilla, V. M., Rodrı́guez-Almeida, L., Alonso, A. E. R., Zeng, S., Cocinero, E. J., Martı́n, S., Requena-Torres, M., Martı́n-Domenech, R., Testi, L.,2020, Astrobiology, 20, 9, 1048-1066

(ref: kil47) Kilpatrick, M. L. 1947, J. Am. Chem. Soc., 69, 40

(ref: lig20) Ligterink, N. F. W., El-Abd, S. J., Brogan, C. L., et al. 2020, ApJ, 901, 37

(ref: man22a) Manna, A. & Pal, S., 2022, Journal of Astrophysics and Astronomy, 43, 83

(ref: man22b) Manna, A. & Pal, S., 2022, Life Sciences in Space Research, 34, 9

(ref: mar06) Martı́n S., Mauersberger R., Martı́n-Pintado J., Henkel C., Garcı́a-Burillo S., 2006, ApJS , 164, 450

(ref: mu05) Müller, H. S. P., SchlM$\ddot{o}$der, F., Stutzki, J. & Winnewisser, G. 2005, Journal of Molecular Structure, 742, 215–227

(ref: mce13) McElroy, D., Walsh, C., Markwick, A. J., Cordiner, M. A., Smith, K., Millar, T. J., 2013, A&A, 550, A36

(ref: mc07) McMullin, J. P., Waters, B., Schiebel, D., et al. 2007, San Francisco, CA: ASP, 127

(ref: moto19) Motogi, K., Hirota, T., Machida, M. N., et al. 2019, ApJL, 877, L25

(ref: mur20) Mangum, J., 2020, How to Calculate Bandwidth Smearing in Radio Synthesis Measurements, NRAO

(ref: nu00) Nummelin A., Bergman P ., Hjalmarson Å., Friberg P ., Irvine W. M., Millar T. J., Ohishi M., Saito S., 2000, ApJS , 128, 213

(ref: cox00) Cox, A. N., & Pilachowski, C. A. 2000, Physics Today, 53, 77

(ref: pic98) Pickett, H. M., Poynter, R. L., Cohen, E. A., et al. 1998, Journal of Quantitative Spectroscopy and Radiative Transfer, 60, 883

(ref: pa17) Palau, A., Walsh, C., Sánchez-Monge, Á., Girart, J. M., Cesaroni, R., Jiménez-Serra, I., Fuente, A., Zapata, L. A., Neri, R., 2017, MNRAS, 467, 2723

(ref: pal17) Perley, R. A., Butler, B. J. 2017, ApJ, 230, 1538

(ref: re14) Reid, M. J., Menten, K. M., Brunthaler, A., et al. 2014, ApJ, 783, 130

(ref: shi21) Shimonishi, T., Izumi, N., Furuya, K., & Yasui, C., 2021, ApJ, 2, 206

(ref: sharma21) Sharma, M. K., Astrophysics, 2021, 64,71-80

(ref: ste21) Stecklum, B., Wolf, V., Linz, H., et al., 2021. A&A, 646, p.A161

(ref: tur75) Turner, B. E., Liszt, H. S., Kaifu, N., & Kisliakov, A. G. 1975, ApJ, 201, L149

(ref: van98) van Dishoeck E. F., & Blake G. A. 1998, Annu Rev Astron Astrophys, 36, 317

(ref: vas15) Vastel, C., Bottinelli, S., Caux, E., et al. 2015, Proceedings of the Annual meeting of the French Society of Astronomy and Astrophysics, 313-316

(ref: wil81) Williams, A., & Ibrahim, I. T. 1981, Chem. Rev., 81, 589

(ref: whi03) White, G. J., Araki, M., Greaves, J. S., Ohishi, M., & Higginbottom, N. S. 2003, A&A, 407, 589

(ref: whi92) Whittet, D. C. B. 1992, Journal of the British Astronomical Association, 102, 230

(ref: wak12) Wakelam V., et al., 2012, The Astrophysical Journal Supplement, 199, 21

(ref: zh18) Zeng S. et al., 2018, MNRAS , 478, 2962

(ref: zh23) Zhang, X., et al., 2023, MNRAS, 521, 1578

</paper>

## Items to check

```json
[
 {
  "path": "data.external_data_from_literature[5].what.evidence[0]",
  "value": "NH2CN column densities, excitation temperatures, H2 column densities, and abundances in other astronomical sources",
  "failed_quote": "Here we compare the observed abundance of in G358.93–0.03 MM1 and other hot molecular cores, galaxies, high and low-mass protostars, and molecular clouds, which are shown in Table [\\tab:comparision](#tab:comparision)."
 },
 {
  "path": "processing.inherited[0].what.evidence[0]",
  "value": "Dust mass absorption coefficient formula kappa_nu = 0.90 (nu / 230 GHz)^beta cm^2 g^-1",
  "failed_quote": "During the estimation of the mass absorption coefficient ($\\kappa_{\nu}$), we adopted the formula $\\kappa_\nu = 0.90(\nu/230 GHz)^{\beta}\\ cm^{2}\\ g^{-1}$ (cite: moto19),"
 },
 {
  "path": "analysis_steps[1].method.evidence[0]",
  "value": "Fit 2D Gaussian to G358.93–0.03 MM1 continuum images at four frequencies using CASA IMFIT, then calculate H2 column density and dust optical depth from the peak flux densities assuming optically thin dust emission.",
  "failed_quote": "Now we used the CASA task `IMFIT` to fit the 2D Gaussian over all the continuum images and obtained an integrated flux density, peak flux density, synthesised beam size, position angle, and RMS, which are presented in Table [\\tab:cont](#tab:cont)."
 },
 {
  "path": "analysis_steps[1].key_parameters[0].evidence[0]",
  "value": "Frequencies: 216.90, 218.31, 220.11, and 220.56 GHz",
  "failed_quote": "Using the mass absorption coefficient formula, we estimated the value of $\\kappa_{\nu}$ to be 0.814, 0.823, 0.835, and 0.838 for frequencies of 216.90, 218.31, 220.11, and 220.56 GHz, respectively."
 },
 {
  "path": "analysis_steps[1].assumptions[0].evidence[0]",
  "value": "Optically thin dust emission, dust temperature T_d = 150 K, mean atomic mass per hydrogen mu_H = 1.41, dust-to-gas mass ratio Z = 0.01",
  "failed_quote": "The peak flux density (S$_\nu$) of optically thin dust continuum emission can be expressed as,"
 },
 {
  "path": "analysis_steps[1].assumptions[1].evidence[0]",
  "value": "Dust opacity law kappa_nu = 0.90*(nu/230 GHz)^beta cm^2 g^-1 with beta ~ 1.7 (giving kappa_nu = 0.814, 0.823, 0.835, 0.838 cm^2 g^-1), and Rayleigh-Jeans approximation 1 Jy beam^-1 = 118 K",
  "failed_quote": "During the estimation of the mass absorption coefficient ($\\kappa_{\nu}$), we adopted the formula $\\kappa_\nu = 0.90(\nu/230 GHz)^{\beta}\\ cm^{2}\\ g^{-1}$ (cite: moto19),"
 },
 {
  "path": "analysis_steps[1].fitting.evidence[0]",
  "value": "2D Gaussian fitting with CASA IMFIT",
  "failed_quote": "Now we used the CASA task `IMFIT` to fit the 2D Gaussian over all the continuum images and obtained an integrated flux density, peak flux density, synthesised beam size, position angle, and RMS, which are presented in Table [\\tab:cont](#tab:cont)."
 },
 {
  "path": "analysis_steps[3].assumptions[0].evidence[0]",
  "value": "Deconvolved source size given by theta_S = sqrt(theta_50^2 - theta_beam^2)",
  "failed_quote": "The deconvolved synthesised beam sizes of the emitting regions were derived by the following equation:\n$$\begin{equation}\n    \\theta_{S}=\\sqrt{\\theta^2_{50}-\\theta^2_{beam}}     \n    \n\\end{equation}$$"
 },
 {
  "path": "software[0].used_for.evidence[1]",
  "value": "Data reduction via the ALMA pipeline (SETJY, hifa_bandpassflag, hifa_flagdata), visibility splitting (MSTRANSFORM), continuum subtraction (UVCONTSUB), continuum and spectral cube imaging (TCLEAN), primary beam correction (IMPBCOR), 2D Gaussian fitting (IMFIT), and moment maps (IMMOMENTS).",
  "failed_quote": "Now we used the CASA task `IMFIT` to fit the 2D Gaussian over all the continuum images and obtained an integrated flux density, peak flux density, synthesised beam size, position angle, and RMS, which are presented in Table [\\tab:cont](#tab:cont)."
 }
]
```
