# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2019ApJ...887..235L\sonnet\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
# Automated Mining of the ALMA Archive in the COSMOS Field (A$^3$COSMOS): II. Cold Molecular Gas Evolution out to Redshift 6

## Abstract

We present new measurements of the cosmic cold molecular gas evolution out to redshift 6 based on systematic mining of the ALMA public archive in the COSMOS deep field (A$^3$COSMOS). Our A$^3$COSMOS dataset contains $\sim700$ galaxies ($0.3 \lesssim z \lesssim 6$) with high-confidence ALMA detections in the (sub-)millimeter continuum and multi-wavelength spectral energy distributions (SEDs). Multiple gas mass calibration methods are compared and biases in band conversions (from observed ALMA wavelength to rest-frame Rayleigh-Jeans(RJ)-tail continuum) have been tested. Combining our A$^3$COSMOS sample with $\sim1,000$ CO-observed galaxies at $0 \lesssim z \lesssim 4$ (75% at $z < 0.1$), we parameterize galaxies’ molecular gas depletion time ($\tau_{\mathrm{depl}}$) and molecular gas to stellar mass ratio ($\mu_{\mathrm{molgas}}$) each as a function of the stellar mass ($M_{\star}$), offset from the star-forming main sequence ($\Delta{\mathrm{MS}}$) and cosmic age (or redshift). Our proposed functional form provides a statistically better fit to current data (than functional forms in the literature), and implies a “downsizing” effect (i.e., more-massive galaxies evolve earlier than less-massive ones) and “mass-quenching” (gas consumption slows down with cosmic time for massive galaxies but speeds up for low-mass ones). Adopting galaxy stellar mass functions and applying our $\mu_{\mathrm{molgas}}$ function for gas mass calculation, we for the first time infer the cosmic cold molecular gas density evolution out to redshift 6 and find agreement with CO blind surveys as well as semi-analytic modeling. These together provide a coherent picture of cold molecular gas, SFR and stellar mass evolution in galaxies across cosmic time.

# Introduction

The interstellar medium (ISM), especially the cold molecular gas, is the fuel of star formation activity in galaxies. In recent years, our knowledge of the cosmic evolution of star formation and stellar mass growth has been obtained out to redshift $\sim5$ (e.g., see latest reviews by (cite: Lutz2014Review) and (cite: Madau2014Review); see also (cite: Davidzon2017); (cite: Liudz2017); to name a few). However, the cosmic evolution of the cold molecular gas is much less well constrained and the validity of different tracers are debated (e.g., (cite: Magdis2012SED); (cite: Santini2014); (cite: Genzel2015); (cite: Tacconi2018); (cite: Riechers2019); (cite: Decarli2019)).

There are several widely used tracers of the molecular gas content in galaxies, including the commonly used carbon monoxide (CO) rotational transition lines, dust masses from dust spectral energy distribution (SED), and the cold dust continua at the Rayleigh-Jeans (RJ) tail of dust SED. We introduce each case below.

Observationally, CO lines at the rest-frame millimeter (mm) wavelengths have been established as the most-commonly used tracers of total molecular gas content in galaxies near and far since 1970s (e.g., see latest reviews by (cite: Carilli2013Review); (cite: Combes2018Review)). At high-redshift, this method relies on galaxy samples with accurate spectroscopic redshifts and usually has uncertainties from the CO-to-H$_2$ conversion factor ($\alpha_{\mathrm{CO}}\equiv M_{\mathrm{mol\,gas}}/L^{\prime}_{\mathrm{CO}}$) and CO excitation. With this method, (cite: Genzel2010) and (cite: Tacconi2013; Tacconi2018) conducted the largest survey for individual galaxies (named PHIBSS) by observing hundreds of star-forming galaxies at $z\sim1-3$ to study the molecular gas scaling relation and evolution. Meanwhile, (cite: Walter2016) and (cite: Decarli2016; Decarli2019) have been conducting the largest blank-field survey (named ASPECS) by scanning a range of mm spectra within a fixed sky area to determine the CO luminosity function and thereby study the molecular gas mass density evolution.

Alternatively, in the past few years, emission from dust grains located in the star-forming regions of galaxies has also been widely used as a proxy of the ISM. These dust grains absorb rest-frame ultra-violet (UV) photons from massive stars and re-emit thermal radiation in the infrared(IR)-to-mm wavelengths. By fitting a galaxy’s full dust SED with models, e.g., modified blackbody models or multi-component physical models (e.g., (cite: Draine2007SED)), the dust mass and dust temperature (or mean radiation field) can be obtained (e.g., (cite: Santini2010; Santini2014); (cite: Magdis2011SED; Magdis2012SED); (cite: Magnelli2012; Magnelli2014); (cite: Saintonge2013); (cite: Sandstrom2013); (cite: Tan2014); (cite: Bethermin2015); (cite: Berta2016); (cite: Hunt2019)). The dust mass can then be converted to gas mass via the application of empirical gas-to-dust ratios ($\delta_{\mathrm{GDR}}$).

However, a galaxy’s full dust SED is a composite of a variety of dust components with different temperatures. Warmer dust exposed to strong radiation fields (e.g., photo-dominated regions; (cite: Dale2001); (cite: Draine2007SED)) globally outshines the colder dust at shorter wavelengths of the SED, but the former is much less abundant (e.g., $<10\%$ in mass) and does not represent the bulk of dust in a galaxy. Thus obtaining reliable dust mass usually requires longer wavelength coverage that includes the RJ tail (e.g., $\lambda_{\mathrm{rest}} \gtrsim 250\,\mu$m). Also, different dust SED models can result in strong and not-easily-predictable systematic effects ((cite: Berta2016)). Therefore, the RJ-tail method has been proposed by (cite: Scoville2013b; Scoville2014), which directly uses the RJ-tail dust continuum to trace gas (yet the underlying physics of using dust mass to trace gas mass is the same as the in the dust SED method above).

The RJ-tail method has recently been proven to be as reliable as the CO method (e.g., (cite: Scoville2014; Scoville2016); (cite: Groves2015); (cite: Hughes2017); (cite: Bertemes2018); (cite: Saintonge2018); (cite: Kaasinen2019); and theoretical works, e.g., (cite: Privon2018)) and is much more efficient in surveying large galaxy samples at high redshift. This method relies on the assumption that the dust grains providing most of the dust mass in galaxies are cold and mixed within the ISM. Their temperatures are likely always as cold as $T_{\mathrm{dust}}\approx 25 \, \mathrm{K}$ (see (cite: Scoville2014; Scoville2016)), and hence they can trace the total gas content via a relatively stable gas-to-dust ratio ($\delta_{\mathrm{GDR}}$; e.g., (cite: Leroy2011GDR); (cite: RemyRuyer2014)). Yet we bear in mind that metallicity, true dust temperature and mass distributions are all unsolved issue.

These studies have led to a rough picture of dust and gas evolution from redshift 3 to present, where: (a) the fraction of molecular gas mass to the total of molecular gas and stellar masses,

$$\begin{equation}
\begin{split}
\quad & f_{\mathrm{mol\,gas}}\equiv M_{\mathrm{mol\,gas}}/(M_{\mathrm{mol\,gas}}+M_{\star}), \\
\quad & \textnormal{or} \ \mu_{\mathrm{molgas}}\equiv M_{\mathrm{mol\,gas}}/M_{\star}, \\
\end{split}
\label{Equation_mugas}
\end{equation}$$

decreases with cosmic age from $z\sim3$ to $z\sim0$, and depends on SFR and stellar mass; (b) the molecular gas depletion time,

$$\begin{equation}
\begin{split}
\quad & \tau_{\mathrm{depl}}\equiv M_{\mathrm{mol\,gas}}/\mathrm{SFR}, \\
\end{split}
\end{equation}$$

increases from $z\sim3$ to present, and is significantly different between typical star-forming galaxies (which follow a tight $M_{\star}-\mathrm{SFR}$ main sequence (hereafter MS) at each redshift; e.g., (cite: Brinchmann2004); (cite: Noeske2007); (cite: Elbaz2007); (cite: Daddi2007)) and starbursts (i.e., located significantly above the MS; e.g., (cite: Rodighiero2011; Rodighiero2014)). (cite: Genzel2015) first compiled a large sample of local and high-redshift ($0<z<3$) galaxies with both CO (500 galaxies) and dust SED (512 galaxies) methods. They studied the gas scaling relations by characterizing $f_{\mathrm{mol\,gas}}$ and $\tau_{\mathrm{depl}}$ as functions of $M_{\star}$, SFR and redshift. More precisely, they found that gas fraction and depletion time are more strongly correlated with the SFR offset to the MS,

$$\begin{equation}
\begin{split}
\quad & \delta{\mathrm{MS}}\equiv \mathrm{SFR}/\mathrm{SFR}_\mathrm{MS}, \\
\quad & \textnormal{or} \ \Delta{\mathrm{MS}}\equiv \log_{10}(\mathrm{SFR}/\mathrm{SFR}_\mathrm{MS}), \\
\end{split}
\end{equation}$$

rather than the absolute SFR.

Utilizing the RJ-tail dust continuum method (at rest-frame 850 $\mu$m), (cite: Scoville2017) studied the gas ($f_{\mathrm{mol\,gas}}$ and $\tau_{\mathrm{depl}}$) scaling relations with a large sample of 708 high-redshift *Herschel* far-IR-selected galaxies ($0.3 < z < 4.5$), including a large number of public data in the Atacama Large Millimeter/submillimeter Array (ALMA) archive (at a 2.5–3$\,\sigma$ detection threshold), and characterized the $f_{\mathrm{mol\,gas}}$ and $\tau_{\mathrm{depl}}$ functional forms:

$$\begin{equation}
\begin{split}
&\mu_{\mathrm{molgas}}= 0.71 
\times (\delta{\mathrm{MS}})^{+0.32} 
\times M_{\star,10}^{-0.70}
\times (1+z)^{+1.84} , \\[3pt]
&\tau_{\mathrm{depl}}= 3.23 \; \mathrm{Gyr} 
\times (\delta{\mathrm{MS}})^{-0.70} 
\times M_{\star,10}^{-0.01}
\times (1+z)^{-1.04} , 
\end{split}
\label{Equation_Scoville2017}
\end{equation}$$

where $M_{\star,10}$ is $M_{\star}/(10^{10}\;\mathrm{M}_{\odot})$. With the same method but at rest-frame 250–500 $\mu$m, (cite: Schinnerer2016) studied a smaller sample of optically-selected galaxies at $z=2.8-3.6$. However, discrepancies exist due to the slightly different methods and samples.

(cite: Tacconi2018) expanded the work of (cite: Genzel2015) by obtaining nearly a hundred new CO detections in the PHIBSS2 survey and compiling more samples of local to high-redshift galaxies in the literature. They used all three methods for obtaining molecular gas measurements for 1,444 galaxies at $0<z<4$, and fitted them all together to derive the $f_{\mathrm{mol\,gas}}$ and $\tau_{\mathrm{depl}}$ functions:

$$\begin{align}
\quad 
&\mu_{\mathrm{molgas}}= 2.32 
\times (\delta{\mathrm{MS}})^{+0.53} 
\times M_{\star,10}^{-0.35} \notag\\
\quad 
&\hspace{3em}
\times 10^{-3.62 \times (\log_{10}(1+z)-0.66)^{2}}, \notag\\[3pt]
\quad 
&\tau_{\mathrm{depl}}= 1.06 \ \mathrm{Gyr} 
\times (\delta{\mathrm{MS}})^{-0.44} 
\times M_{\star,10}^{+0.09} \notag\\
\quad 
&\hspace{3em}
\times (1+z)^{-0.62},
\label{Equation_Tacconi2018}
\end{align}$$

where we adopted their $\beta=2$ best-fit with the (cite: Speagle2014) MS and expressed their stellar mass in $M_{\star,10}$ to match Eq. [\[Equation_Scoville2017\]](#Equation_Scoville2017).

Comparing Eqs. [\[Equation_Scoville2017\]](#Equation_Scoville2017) and [\[Equation_Tacconi2018\]](#Equation_Tacconi2018) at redshift 3 and $M_{\star}=5\times10^{10}\;\mathrm{M}_{\odot}$ reveals a factor of 2.3 difference in $\mu_{\mathrm{molgas}}$ and a factor of 1.5 in $\tau_{\mathrm{depl}}$. Such noticeable differences exist for other parameter values as well, raising concerns on the validity of the $\mu_{\mathrm{molgas}}$ and $\tau_{\mathrm{depl}}$ functions and the predictability of $\mu_{\mathrm{molgas}}$ and $\tau_{\mathrm{depl}}$ from a galaxy’s redshift, stellar mass and SFR properties. In addition, previous works have constraints only for $z \lesssim 3-4$.

To solve the discrepancies and understand systematic bias especially for the latest RJ-tail dust method, a large, robust, galaxy sample from local to high redshift is needed to carry out the comprehensive analysis. Therefore, in this work, we present an independent study on the characterization of the molecular gas fraction ($\mu_{\mathrm{molgas}}$) and depletion time ($\tau_{\mathrm{depl}}$) functional forms utilizing a large ($\sim700$), robust galaxy sample at $0.3 < z \lesssim 6$ in the 2 deg$^2$ COSMOS field (cite: Scoville2007) from the A$^3$COSMOS project [^1], together with $\sim1,000$ CO-detected galaxies at $0 \lesssim z \lesssim 4$ (75% at $z < 0.1$) from recent large surveys in the literature. All A$^3$COSMOS galaxies have robust (sub-)mm continuum detections from public ALMA archival data (release date up to Aug. 1st, 2018) with an expected spurious fraction close to zero and flux bias being corrected statistically ((cite: Liudz2019); hereafter paper ).

With such a combined large sample, we provide new molecular gas fraction ($\mu_{\mathrm{molgas}}$) and depletion time ($\tau_{\mathrm{depl}}$) functional forms that are valid from redshift 0 to 6. We adopt galaxies’ stellar mass functions and/or realistic galaxy modeling to analytically derive the cosmic molecular gas mass density evolution for the first time with such a large dataset out to redshift 6. The result supports a coherent picture of the evolution of galaxies’ stellar mass, star formation and cold molecular gas.

This paper is organized as follows. Galaxy samples are presented in Sect. [2](#Section_Sample_and_Data), with the A$^3$COSMOS high-redshift sample in Sect. [2.1](#Section_A3COSMOS_Pipelines) and complementary local-to-high-redshift samples from the literature in Sect. [2.2](#Section_Complementary_Galaxy_Samples). Molecular gas mass calculation and comparison are presented in Sect. [3](#Section_Molecular_Gas_Mass_Calculation) (dust SED method in Sect. [3.1](#Section_Deriving_Gas_Mass_1), RJ-tail method in Sect. [3.2](#Section_Deriving_Gas_Mass_234), and comparison in Sect. [3.3](#Section_comparing_gas_mass_calibration)). The complexity and apparent correlations between $\mu_{\mathrm{molgas}}$, $\tau_{\mathrm{depl}}$ and galaxies’ redshifts, stellar masses and SFRs are discussed in Sect. [4](#Section_Galaxy_Properties). The characterization of the functional forms for $\mu_{\mathrm{molgas}}$ and $\tau_{\mathrm{depl}}$ are presented in Sect. [5](#Section_Fitting_Multi_Variate_Function), and their implications are discussed in Sect. [6](#Section: Predictions from Galaxy Molecular Gas Evolution Functions). Finally, the cosmic evolution of molecular gas mass density is analytically obtained in Sect. [7](#Section_Implication), followed by the summary in Sect. [8](#Section_Summary).

In the Appendices, we thoroughly compare several important correlations related to our analysis: CO-to-H$_2$ conversion factor versus metallicity in Appx. [9.1](#Section_ZACO); gas-to-dust ratio versus metallicity in Appx. [9.2](#Section_ZGDR); molecular to total gas fraction versus stellar mass and/or metallicity in Appx. [9.3](#Section_ZFMOL); and stellar mass-metallicity relation in Appx. [9.4](#Section_MZR). These comparisons give useful insights into how different correlations impact the results presented in this work, as well as supporting our fiducial model in this work.

We adopt a flat $\Lambda$CDM cosmology with $H_0=70\;\mathrm{km\,s^{-1}\,Mpc^{-1}}$, $\Omega_M=0.3$ and $\Lambda_0=0.7$ [^2], and a (cite: Chabrier2003) initial mass function (IMF).

# Sample and Data

## The A$^3$COSMOS Galaxy Sample

In paper  we presented the A$^3$COSMOS project, i.e., an Automated ALMA Archive mining in the COSMOS field. We developed pipelines for producing continuum images using nearly all publicly available ALMA archival data in COSMOS (regardless of observing bands but discarded very high resolution (beam size $< 0.1''$) data; see paper ). We performed two major (sub-)mm continuum photometry extractions: one prior-based and one blind extraction, to make sure the photometries are robust and outliers are identified (see below). Both photometries are verified by extensive Monte Carlo simulations and corrected for flux bias and uncertainty. Additional photometry task using apertures following show good consistency for isolated sources ($<20\%$ difference in average; but significant differ for blended or merger-like sources for which aperture photometry is not suitable).

In order to obtain a most robust galaxy catalog from the initial (sub-)mm continuum detections, we applied very strict criteria to select ALMA detections: a peak flux to rms noise ratio of 5.40 for blind extraction and 4.35 for prior photometry, which correspond to an expected spurious source fraction of $\sim10\%$ (according to our statistical analysis). These spurious sources are statistically unavoidable in the initial photometry catalogs, but we developed a series of assessments to identify the most reliable detections. We hence removed ALMA detections which: (1) have inconsistent fluxes between blind- and prior-based (sub-)mm photometry (identified by the

`Flag_inconsistent_flux`

in the A$^3$COSMOS catalog, which are about ten sources likely being mergers or blended sources and exhibit a $\gtrsim0.5\,$dex difference between blind-/prior-photometry fluxes; see examples in Appendix B of paper ); (2) have a peculiar counterpart association quality (

`Flag_outlier_CPA`

; which are likely because of chance alignment between a prior source and a noise peak); and/or (3) show an excess in ALMA flux relative to the galaxy SED (

`Flag_outlier_SED`

; which are likely because of inconsistent photometric redshift, blended sources or noise). These criteria exclude sources that are either boosted by noise in the ALMA image or multiple galaxies co-aligned, plus other less-clear situations. For more details we refer the reader to paper .

After removing the spurious sources, our robust galaxy catalog from A$^3$COSMOS (version

`20180801`

) contains 669 galaxies (36% have spectroscopic redshifts mainly from the COSMOS spec-$z$ catalog compiled by M. Salvato; see references in paper ). Due to the strict additional selection criteria, the spurious fraction is reduced to close to zero according to our statistics in paper . Yet this implies that we miss a significant number of low ALMA $\mathrm{S/N}$ sources which have a $<50\%$ chance of being real, faint galaxies. For comparison, explored all ALMA Band 6 and 7 data in the ALMA public archive and selected sources with total flux of $\mathrm{S/N}>2$. (cite: Betti2019) analyzed ALMA continuum data for 101 galaxies and selected 68 as detections with an aperture-based total flux of $\mathrm{S/N}>2$ or peak flux of $\mathrm{S/N}>3$. The data used in (cite: Betti2019) have been public in the ALMA archive before Aug. 2018, and are therefore in our catalog. 90 of their galaxies appear in our prior-fitting catalog without applying a $\mathrm{S/N}$ selection, however, only 8 galaxies have a peak flux $\mathrm{S/N}>4.35$, which is our selection criterion based on statistics (corresponding to a spurious fraction $\sim10\%$). This quick comparison demonstrates that our catalog has very strict constraints and only considers the statistically most-robust ALMA detections. Lowering the selection criterion for A$^3$COSMOS from a (peak flux) $\mathrm{S/N}$ of 4.35 to 3.0 doubles the A$^3$COSMOS galaxy sample, however 40% of the sample will be spurious based on our simulation statistics. Given this trade-off between increased sample size and decreased reliability, we resort to the original robust galaxy catalog containing only highly-reliable sources from A$^3$COSMOS.

Galaxy properties in the A$^3$COSMOS galaxy catalog, including stellar mass ($M_{\star}$), IR luminosity ($L_{\mathrm{IR}}$) and dust mass ($M_{\mathrm{dust}}$), are obtained from MAGPHYS ((cite: daCunha2008; daCunha2015)) SED fitting to their optical-to-radio SEDs (see paper ). We compute the dust-obscured SFR from IR luminosity following the (cite: Kennicutt1998SFL) calibration and (cite: Chabrier2003) IMF: $\mathrm{SFR} = L_{\mathrm{IR}} \, / \, 1\times10^{10} \ \mathrm{M}_{\odot}\, \mathrm{yr^{-1}}$.

In addition, to understand whether using MAGPHYS SED fitting is biased due to the built-in SED templates or the assumption of energy balance, we performed two more independent SED fittings for each galaxy to fit the stellar (up to IRAC ch2) and near-IR-to-radio data points separately, with the FAST ((cite: Kriek2009)) and “SUPER-DEBLENDED” ((cite: Liudz2017; Jin2018)) SED fitting tools, respectively. We find that the MAGPHYS-fitted stellar masses are systematically larger by about 0.25 dex than the FAST fitted values (with a scatter of 0.30 dex), while the dust-obscured SFRs are fully consistent between the MAGPHYS and SUPER-DEBLENDED SED fitting. The systematic discrepancy in stellar mass has also been found by (cite: Battisti2019) and reproduced in SED modeling with various non-parametric star formation histories (e.g., (cite: Leja2019)). Since this is not yet fully understood, we still adopt the MAGPHYS SED fitting results. We tested that using FAST-fitted stellar masses will not change our main results, but only alter the coefficients in our equations (by $\lesssim20\%$).

| Sample Name | $z$ | $\log_{10} (M_{\star}/\mathrm{M}_{\odot})$ | $N_{\mathrm{det.}}$ $^{a}$ | References |
|:---|:---|:---|:---|:---|
| A$^3$COSMOS (Paper ) | 0.29–5.667 $^{b}$ | $\sim$10.–12. | 658 $^{b}$ | (cite: Liudz2019) |
| DGS | 0–0.045 | 6.5–10.6 | 32 | (cite: RemyRuyer2014; RemyRuyer2015) |
| HRS | 0.0034–0.006 | 8.7–11.7 | 99 | (cite: Andreani2018) |
| KINGFISH | 0.0005–0.006 | 6.3–10.7 | 28 | (cite: Groves2015) |
| Saintonge+2017 (xCOLDGASS) | 0.01–0.05 | 9.0–11.4 | 330 | (cite: Saintonge2017) |
| Cicone+2017 (ALLSMOG) | 0.01–0.03 | 8.5–11.5 | 48 | (cite: Cicone2017) |
| Lisenfeld+2017 | 0.01–0.07 | 9.0–11.3 | 41 | (cite: Lisenfeld2017) |
| Cortzen+2019 | 0.03–0.29 | 8.9–11.5 | 51 | (cite: Cortzen2019) |
| Villanueva+2017 (VALES) | 0.03–0.33 | 10.1–11.3 | 49 | (cite: Villanueva2017) |
| Bertemes+2018 (Stripe82) | 0.03–0.20 | 10.0–11.3 | 78 | (cite: Bertemes2018) |
| Kirkpatrick+2014 (5MUSE) | 0.05–0.29 | 10.5–11.4 | 17 | (cite: Kirkpatrick2014) |
| Bauermeister+2013 (EGNOG) | 0.06–0.31 | 10.7–11.5 | 14 | (cite: Bauermeister2013) |
| Lee+2017 | 0.27–0.62 | 10.0–11.1 | 20 | (cite: Lee2017) |
| Spilker+2018 | 0.60–0.75 | $\sim 11.0$ | 4 | (cite: Spilker2018) |
| Combes+2013 (ULIRGs) | 0.61–0.97 | 9.3–12. | 12 (14) | (cite: Combes2013) |
| Magdis+2012a (BzK) | 0.51–1.60 | 10.5–11.0 | 9 | (cite: Magdis2012SED) |
| Tacconi+2018 (PHIBSS 1&2) | 0.50–2.49 | 9.8–11.6 | 148 | (cite: Tacconi2018) |
| Kaasinen+2019 | 1.78–2.93 | 10.6–11.7 | 10 | (cite: Kaasinen2019) |
| Magdis+2017 (LBG) | 2.8–2.9 | 11.28–11.38 | 1 | (cite: Magdis2017) |
| Magdis+2012b (LBG) | 2.9–3.2 | 11.0–11.3 | 1 | (cite: Magdis2012LBG) |
| Tan+2014 (GN20) | 4.05–4.06 | 10.6–11.0 | 3 | (cite: Tan2014) |

$^{a}$

We only include sources with $>3\sigma$ detections.\
$^{b}$ The largest photometric redshift in the A$^3$COSMOS catalog is 5.54 based on the prior redshift information from (cite: Laigle2016) and/or (cite: Davidzon2017), and 7.2 based on (cite: Jin2018). The largest spectroscopic redshift is 5.667 based on the prior information from (cite: Capak2015). There are 11 sources which have IR/mm photo-$z=5.7-7.2$ only from (cite: Jin2018) and are very uncertain. However, our test in Sect. [5](#Section_Fitting_Multi_Variate_Function) shows that including or excluding them does not obviously alter our results.

## Complementary Local-to-High-Redshift Galaxy Samples

We include 20 samples of galaxies with CO observations and well-constrained stellar mass and SFR properties from the literature as complementary information to our analysis. The full list is presented in Table [\[Table_galaxy_samples\]](#Table_galaxy_samples) (starting from the second row). It encompasses most of the CO-observed samples analyzed by . Most of these samples are galaxies in the local Universe, and the largest sample is the xCOLD GASS survey sample (cite: Saintonge2017).

(cite: Saintonge2017) applied a metallicity-dependent $\alpha_{\mathrm{CO}}$ according to (cite: Accurso2017) to convert their CO observations into molecular gas mass. A similar metallicity-dependent $\alpha_{\mathrm{CO}}$ is also adopted by the (cite: Bertemes2018) and samples (with slightly different equations; see Appx. [9.1](#Section_ZACO)). While most other complementary samples either assume only a single $\alpha_{\mathrm{CO}}$ value, i.e., either a Galactic value or an Ultra-Luminous Infrared Galaxy (ULIRG) value (see Appx. [9.1](#Section_ZACO)), or bimodal values depending on the galaxy type (e.g., (cite: Villanueva2017)).

To homogenize the complementary sample, we recalculated all molecular gas masses from the CO line luminosities by applying the metallicity-dependent $\alpha_{\mathrm{CO}}$ following . We use metallicity to calculate $\alpha_{\mathrm{CO}}$ when available (mostly for $z \lesssim 0.3$ galaxies; where metallicity is from optical emission lines using the (cite: PP04) calibration, or converted to that calibration following (cite: Kewley2008) where necessary). Otherwise we first estimate the metallicity using the mass-metallicity relation following (cite: Genzel2015), then calculates the $\alpha_{\mathrm{CO}}$. The re-computed molecular gas masses are within a factor of 2 ($\lesssim 0.36$ dex in logarithm) from their originally obtained values.

# Molecular Gas Mass Calculation

We summarize the three most commonly used molecular gas mass calibration methods for high-redshift galaxies in Fig. [1](#Figure_gas_mass_calibration_flow_chart). As mentioned in the introduction, they are (a) CO lines, (b) SED-fitted dust mass, and (c) RJ-tail dust continuum [^3]. The CO method infers the molecular gas mass via the $\alpha_{\mathrm{CO}}$ conversion factor, which relates to CO luminosity to H$_2$ gas mass and is correlated with metallicity (see details in Appx. [9.1](#Section_ZACO)). When the observed CO line is not the ground transition ($J=1\to0$), an excitation ladder is needed to convert the higher-$J$ line luminosity to the $J=1\to0$ one (e.g., (cite: Carilli2013Review)).

Given that the CO and dust RJ-tail 850 $\mu$m-based gas mass calibrations have been extensively verified to be tightly correlated in a number of recent works at local and high redshift up to $z\sim2-3$ (e.g., (cite: Scoville2014; Scoville2017; Hughes2017; Bertemes2018; Saintonge2018; Kaasinen2019)), we do not further discuss the CO method here, but focus on popular dust-based methods. In Sect. [3.1](#Section_Deriving_Gas_Mass_1) we describe the use of SED-fitted dust mass to compute molecular gas mass, and in Sect. [3.2](#Section_Deriving_Gas_Mass_234) we describe the use of the RJ-tail dust continuum for molecular gas mass calculation. There are multiple choices for calibration factors and wavelengths, thus we compare these methods thoroughly in Sect. [3.3](#Section_comparing_gas_mass_calibration).

Later we will combine CO- and dust-based samples together for our data fitting analysis (in Sects. [4](#Section_Galaxy_Properties) and [5](#Section_Fitting_Multi_Variate_Function)). We assume that the consistency between CO- and (our adopted) dust-based gas mass calibration extends to all galaxies in our combined sample, which is at least supported by the aforementioned CO and dust calibration studies (but we also discussed the current caveats at the end of Sect. [5](#Section_Fitting_Multi_Variate_Function)).

## Molecular Gas Mass from SED-fitted Dust Mass

In the SED-fitted dust mass method, we first obtain the dust mass ($M_{\mathrm{dust}}$), dust mean temperature ($T_{\mathrm{dust}}$) and dust emissivity ($\beta_{\mathrm{dust}}$; describing the dust opacity $\kappa$’s wavelength dependency; e.g., (cite: Li2001)) from optical-to-mm SED fitting, then apply a gas-to-dust ratio, $\delta_{\mathrm{GDR}}\equiv M_{\mathrm{total\,gas}}/M_{\mathrm{dust}}$, which relates total gas (molecular and atomic) mass to dust mass.

In the first step, different assumptions on dust grain models can lead to variations in the determined dust properties. Yet simulations (e.g., (cite: Hayward2015)) and observations of local galaxies (e.g., (cite: Hunt2019; Hayward2015)) indicate that SED fitting tools like MAGPHYS are able to reasonably recover galaxies’ dust properties (at least for $L_{\mathrm{IR}}>10^{11}\;\mathrm{L}_{\odot}$). For our work we ignore the systematic uncertainty introduced by different dust grain models (i.e., different SED fitting tools). This might not be entirely correct but further investigation of this topic requires a subsample of galaxies with well-sampled SEDs and accurate spectroscopic redshifts, and is beyond the scope of this paper.

In the second step, $\delta_{\mathrm{GDR}}$ is found to strongly depend on metallicity (e.g., (cite: Leroy2011GDR); (cite: RemyRuyer2014); (cite: DeVis2019); see more details in Appx. [9.2](#Section_ZGDR)), and the latter is correlated with the stellar mass (known as the mass–metallicity relation; see detailed discussion in Appx. [9.4](#Section_MZR)). Differences exist among the empirical scaling relations in the literature, whereas our ALMA continuum observations preferentially select intensely star-forming galaxies with $M_{\star}>  2 \times 10^{10} \; \mathrm{M}_{\odot}$, which exhibit a close-to-solar metallicity based on the mass-metallicity relation at $z\sim2.3$ of (cite: Erb2006). Our analysis is, therefore, only affected by the relative small offset of 0.1–0.2 dex between the relations of (cite: Leroy2011GDR) and (cite: RemyRuyer2014) at $>0.5$ solar metallicity.

As A$^3$COSMOS galaxies do not have homogeneous metallicity measurements, we compute the metallicity based on redshift and stellar mass for each of the galaxies using the mass–metallicity relation of (cite: Genzel2015) and compute the $\delta_{\mathrm{GDR}}$ using the (cite: RemyRuyer2014) prescription. Our detailed comparison of various forms of the mass–metallicity relation and the “Fundamental Metallicity Relation” (e.g., (cite: Mannucci2010; Mannucci2011); yet still debated) in Appx. [9.4](#Section_MZR) shows that the Eq. 12a of (cite: Genzel2015) provides the most plausible predictions for the metallicity of high-redshift $z>1$ galaxies. Here we adopt a slightly modified form of:

$$\begin{equation}
\begin{split}
&12+\log_{10}(\mathrm{O/H})= \\
&\begin{cases}
a, \quad \quad \quad \quad \quad \quad \quad \quad \ \ \textnormal{if} \ \log_{10} (M_{\star}/\mathrm{M}_{\odot}) \ge b(z), \\
a - 0.087 \times (\log_{10} (M_{\star}/\mathrm{M}_{\odot}) - b(z))^2, \quad \quad \ \textnormal{else.}
\end{cases}\\
&\textnormal{where} \ a = 8.74 \ \textnormal{and} \
b(z) = 10.4 + 4.46 \times \log_{10}(1+z) \\& - 1.78 \times (\log_{10}(1+z))^{2}.
\end{split}
\label{Equation_metallicity}
\end{equation}$$

The modification (under the $\log_{10} (M_{\star}/\mathrm{M}_{\odot}) \ge b(z)$ condition) prevents a drop in metallicity for very massive galaxies at $z<1$ (see Fig. [16](#Plot_metalZ_Mstar_SFR_z_bins)).

Finally, we consider that our A$^3$COSMOS high-redshift galaxies are molecular-rich (same as assumed by at $z>0.4$), i.e., the molecular-to-total-gas ratio $f_{\mathrm{mol\,frac}}$ is unity. In this way, we obtain the dust-SED-based $M_{\mathrm{mol\,gas}}$ by multiplying $M_{\mathrm{dust}}$ with the mass–metallicity-derived $\delta_{\mathrm{GDR}}$ and ignore the contribution from atomic gas. Hereafter we refer to this method as the “$\delta_{\mathrm{GDR},\,Z}$” method.

We caution that, as discussed in Appx. [9.3](#Section_ZFMOL), observations of local galaxies actually indicate that $f_{\mathrm{mol\,frac}}$ is usually below 50% even for a galaxy with $M_{\star}\sim 1 \times 10^{11} \; \mathrm{M}_{\odot}$. Applying an actual $f_{\mathrm{mol\,frac}}$, e.g., based on the (cite: KMT09) correlation with stellar mass or metallicity, will lead to a lower $M_{\mathrm{mol\,gas}}$. Based on our next comparison of $M_{\mathrm{mol\,gas}}$ calibrations (see Sect. [3.3](#Section_comparing_gas_mass_calibration)), this will cause even larger difference to the RJ-tail dust continuum methods where atomic gas is also not considered. Therefore, here we choose to not account for the atomic gas, and leave the consideration of an actual $f_{\mathrm{mol\,frac}}$ to future work.

## Molecular Gas Mass from RJ-tail Dust Continuum

Recent studies show that dust continuum luminosity at rest-frame RJ-tail wavelengths tightly correlates with gas mass or CO line luminosity across two orders of magnitude in local and high-redshift galaxies (e.g., (cite: Bourne2013); (cite: Scoville2014; Scoville2016); (cite: Groves2015); (cite: Hughes2017); (cite: Saintonge2017); (cite: Bertemes2018); (cite: Kaasinen2019)). (cite: Scoville2014) found a constant ratio between dust continuum luminosity and $M_{\mathrm{total\,gas}}$:

$$\begin{equation}
\quad \alpha_{\textsc{rj},\,\mathrm{tot}}\equiv \frac{
L_{\nu_{\textsc{rj}}} \ / \ [\mathrm{erg\,s^{-1}\,Hz^{-1}}]
}{
M_{\mathrm{total\,gas}}\ / \ [\mathrm{M}_{\odot}]
}
\label{Equation_alphaRJtot}
\end{equation}$$

where they calibrated $\alpha_{\textsc{rj},\,\mathrm{tot}}$ to be $1.0 \pm 0.23 \times 10^{20}$ $[\mathrm{erg\,s^{-1}\,Hz^{-1}\,\mathrm{M}_{\odot}^{-1}}]$ at rest-frame 850 $\mu$m with a small sample of 12 local galaxies. Meanwhile, (cite: Groves2015) studied the atomic, molecular gas and dust continuum at rest-frame 70, 100, 160, 250, 350 and 500 $\mu$m in 36 local spiral galaxies. They found a mean $M_{\mathrm{total\,gas}}/\nu L_{\nu,500} = 28.5$ for near-solar metallicity galaxies, corresponding to $\alpha_{\mathrm{500,tot}} = 2.2 \times 10^{20}$ $[\mathrm{erg\,s^{-1}\,Hz^{-1}\,\mathrm{M}_{\odot}^{-1}}]$, and a factor of ten lower values for much more metal-poor galaxies. According to Eq. 9 of (cite: Scoville2014), $\alpha_{\textsc{rj},\,\mathrm{tot}}$ is proportional to dust opacity $\kappa_{\nu}$, which scales with frequency by $\kappa_{\nu} \propto \nu^{1.7-2.0}$ ((cite: Li2001)), thus it is expected that $\alpha_{\textsc{rj},\,\mathrm{tot}}$ is a factor of 2.5 higher at 500 $\mu$m than at 850 $\mu$m. Therefore the calibrations are consistent between (cite: Groves2015) and (cite: Scoville2014). Meanwhile, the variation from metal-rich to metal-poor galaxies can also be explained by a dramatic change in $\delta_{\mathrm{GDR}}$ (Appx. [9.2](#Section_ZGDR)).

Focusing on molecular gas only, (cite: Scoville2016) calibrated the ratio between the RJ-tail dust continuum luminosity and $M_{\mathrm{mol\,gas}}$:

$$\begin{equation}
\quad \alpha_{\textsc{rj},\,\mathrm{mol}}\equiv \frac{
L_{\nu_{\textsc{rj}}} \ / \ [\mathrm{erg\,s^{-1}\,Hz^{-1}}]
}{
M_{\mathrm{mol\,gas}}\ / \ [\mathrm{M}_{\odot}]
}
\label{Equation_alphaRJmol}
\end{equation}$$

to be $6.7 \pm 1.7 \times 10^{19}$ $[\mathrm{erg\,s^{-1}\,Hz^{-1}\,\mathrm{M}_{\odot}^{-1}}]$ at rest-frame 850 $\mu$m for a few tens of local spirals, ULIRGs and $z\sim2$ submillimeter galaxies (SMGs). Later studies with larger samples of CO and RJ-tail continuum observations found slightly non-linear correlations, i.e., $\alpha_{\textsc{rj},\,\mathrm{mol}}$ has a dependency on $L_{\nu_{\textsc{rj}}}$ or $L^{\prime}_{\mathrm{CO}}$ (e.g., (cite: Hughes2017), (cite: Bertemes2018) and (cite: Saintonge2018)). As their samples span a wide range of stellar mass from $10^{9}$ to $10^{12}\;\mathrm{M}_{\odot}$, and CO $J=1\to0$ line luminosity $L^{\prime}_{\mathrm{CO(1-0)}}$ from $10^{7}$ to $10^{12}\;\mathrm{K\,km\,s^{-1}\,pc^{2}}$, galaxies have significantly varied metallicity, $f_{\mathrm{mol\,frac}}$ and $\delta_{\mathrm{GDR}}$. A simple explanation for the variations is that $\alpha_{\textsc{rj},\,\mathrm{mol}}$ scales with $f_{\mathrm{mol\,frac}}^{-1}$ and $\delta_{\mathrm{GDR}}^{-1}$, which both relate to metallicity (see Appx. [9.3](#Section_ZFMOL) and [9.2](#Section_ZGDR) respectively).

Since the literature on the calibration of $\alpha_{\textsc{rj},\,\mathrm{mol}}$ is already very rich, we do not further discuss it here. In the following we will adopt the three calibrations from , (cite: Hughes2017) and (cite: Groves2015), referred to as the “$\alpha_{850,\mathrm{S17}}$”, “$\alpha_{850,\mathrm{H17}}$” and “$\alpha_{160{\textendash}500,\mathrm{G15}}$” method, respectively. For the “$\alpha_{160{\textendash}500,\mathrm{G15}}$” method, we use the calibration factors for the $\log_{10}(M_{\star}/\mathrm{M}_{\odot})>9$ galaxies in the Table 5 of (cite: Groves2015), and assume that our A$^3$COSMOS galaxies have negligible atomic gas contribution. These works directly calibrate the ratio between $L_{\nu_{\textsc{rj}}}$ and $M_{\mathrm{mol\,gas}}$ (and “$\alpha_{850,\mathrm{H17}}$” and “$\alpha_{160{\textendash}500,\mathrm{G15}}$” include a luminosity dependency), therefore the need for a calibration of the underlying $f_{\mathrm{mol\,frac}}$ and $\delta_{\mathrm{GDR}}$ is bypassed.

### Band conversion from observed-frame to rest-frame RJ-tail

The good agreement between RJ-tail dust continuum-to-gas mass calibrations and the overwhelming observational efficiency compared to (sub-)mm line observations make the RJ-tail dust method very favorable and promising for large surveys at high-redshift.

Our high-redshift galaxies are most commonly observed in ALMA Band 6 and 7, which correspond to rest-frame $\lesssim 250\,\mu$m and $\lesssim 160\,\mu$m, respectively, for galaxies at $z\gtrsim4$. In Fig. [2](#Plot_rest_frame_wavelength_vs_redshift), we show the longest rest-frame wavelengths of the available ALMA data for each galaxy in our sample. 85% of our sources have $\lambda_{\mathrm{rest}} \ge 250\,\mu\mathrm{m}$, while the rest only probe shorter-wavelength dust continua.

![](Plot_rest_frame_wavelength_vs_redshift)

In order to apply the $\alpha_{\textsc{rj},\,\mathrm{mol}}$ conversion from dust continuum to molecular gas mass, a “band conversion” [^4] is needed to obtain the corresponding flux density at the calibrated rest-frame wavelength, i.e., rest-frame 850 $\mu$m for applying the $\alpha_{850,\mathrm{S17}}$ and $\alpha_{850,\mathrm{H17}}$ methods, and either 160, 250, 350 or 500 $\mu$m for applying the $\alpha_{160{\textendash}500,\mathrm{G15}}$ method.

We use our MAGPHYS SED fitting for the band conversion, i.e., predicting longer-wavelength flux density with an SED covering only shorter wavelengths. MAGPHYS fits the dust SED with two dust components, one associated with actual star-forming birth clouds and the other exposed to the ambient interstellar radiation field. The former dust usually has a high temperature and dominates the short-wavelength (e.g., $\lambda_{\mathrm{rest}}<60\,\mu\mathrm{m}$) flux density, while the latter dust is constrained to have a temperature in the range of 15–25 K ((cite: daCunha2008; daCunha2015)) and dominates the long-wavelength flux density. A similar idea of composite dust models is also adopted by (cite: Draine2007SED) and used in fitting local star-forming galaxies (e.g., (cite: Draine2007SINGS); (cite: Aniano2012)) and high-redshift galaxies (e.g., (cite: Magdis2012SED; Magdis2014; Magdis2017)).

Using such composite-model SED fitting for band conversion has a large advantage over using a single-temperature modified blackbody, as it is much less biased toward the luminosity-weighted dust temperature. (cite: Privon2018) studied the systematic bias of the band conversion using their zoomed-in cosmological simulations, finding that assuming a single-temperature modified blackbody SED for conversion leads to a more than 0.5 dex overestimation in $L_{\nu_{850\mu\mathrm{m,rest}}}$ when the true dust temperature is a factor of two different than assumed (see their Fig. 5).

Whereas MAGPHYS performs well in fitting the dust SED shape, the sampling of the dust SED is usually limited by the available data for $z>4$ sources (as shown in Fig. [2](#Plot_rest_frame_wavelength_vs_redshift)). In Appx. [10](#Section_Appendix_SED_band_conversion) we perform a test to estimate the bias of lacking long-wavelength data in predicting longer wavelength flux density. We find that when having only $\lambda_{\mathrm{rest}} \le 160\,\mu\mathrm{m}$ data points, MAGPHYS under-predicts the rest-frame 850 $\mu$m flux density by up to 0.8 dex (on average 0.4 dex) when the dust continua photometries have a quadratic-added mean $\mathrm{S/N}\lesssim 15$. Meanwhile, the worse case of having only the rest-frame 160 $\mu$m data point available over the 8 $\mu$m to 3 mm range causes a similar bias by MAGPHYS.

To apply the band conversion, we first compute the ratio between the SED-predicted flux densities at $850\times(1+z)\,\mu\mathrm{m}$ and the observed wavelength:

$$\begin{equation}
\begin{split}
&\Gamma^{\mathrm{SED}} \equiv {S_{\nu_{\mathrm{850\times(1+z)\,\mu\mathrm{m}}}}^{\;\mathrm{SED}}} / {S_{\nu_{\mathrm{obs}}}^{\;\mathrm{SED}}},
\end{split}
\end{equation}$$

then we scale the observed ALMA flux density by $\Gamma^{\mathrm{SED}}$ and compute the luminosity:

$$\begin{equation}
\begin{split}
&L_{\nu_{850\mu\mathrm{m,rest}}} = 4 \pi d_{\mathrm{L}}^2 \times S_{\nu_{\mathrm{obs}}}^{\mathrm{ALMA}} \times \Gamma^{\mathrm{SED}} \,/\, (1+z). \\
\end{split}
\end{equation}$$

In principle we can also directly take the SED-predicted rest-frame 850 $\mu$m flux density $S_{\nu_\mathrm{850\times(1+z)\,\mu\mathrm{m}}}^{\;\mathrm{SED}}$. But this would lead to under-predicted scatter in our analysis due to the degeneracy within SED models.

Finally, we divide the luminosity $L_{\nu_{850\mu\mathrm{m,rest}}}$ by $\alpha_{850}$ derived from and (cite: Hughes2017) to obtain the “$\alpha_{850,\mathrm{S17}}$” and “$\alpha_{850,\mathrm{H17}}$” molecular gas masses. In the “$\alpha_{160{\textendash}500,\mathrm{G15}}$” method, as (cite: Groves2015) provided calibrations at six calibration wavelengths (70, 100, 160, 250, 350 and 500 $\mu$m), we perform the band conversion from the longest-wavelength ALMA data to its nearest calibration wavelength.

![](Plot_Mmolgas_vs_Mmolgas_x4)

## Comparing gas mass calibrations

In Fig. [3](#Plot_Mmolgas_vs_Mmolgas) we compare the molecular gas masses estimated from the above mentioned “$\delta_{\mathrm{GDR},\,Z}$”, “$\alpha_{850,\mathrm{S17}}$”, “$\alpha_{850,\mathrm{H17}}$” and “$\alpha_{160{\textendash}500,\mathrm{G15}}$” methods. As shown in the bottom row of the figure, “$\delta_{\mathrm{GDR},\,Z}$” leads to systematically lower gas masses than the other three RJ-tail continuum methods. The bias is stronger for sources which do not have long-wavelength ($\lambda_{\mathrm{rest}}>250\,\mu\mathrm{m}$) coverage. This is closely related to the MAGPHYS SED fitting feature, where missing long-wavelength data seems to lead to an underestimation of the cold, ambient dust which dominates the total dust mass (consistent with the tests in Appx. [10](#Section_Appendix_SED_band_conversion)).

In the first-row panel, “$\alpha_{850,\mathrm{S17}}$” and “$\alpha_{850,\mathrm{H17}}$” methods agree within 0.1 dex for sources with long-wavelength coverage (but up to about 0.3 dex for sources lacking $>160\,\mu\mathrm{m}$ data). However, a systematic offset of about 0.1 dex exists, which is likely because “$\alpha_{850,\mathrm{S17}}$” uses a single conversion factor while “$\alpha_{850,\mathrm{H17}}$” uses a luminosity-dependent conversion factor. The latter has been confirmed by many other works (e.g., (cite: Bertemes2018); (cite: Saintonge2018)) and therefore is more reliable.

For panels in the second row, the gas masses based on the “$\alpha_{850,\mathrm{S17}}$” and “$\alpha_{850,\mathrm{H17}}$” methods are compared to those using the “$\alpha_{160{\textendash}500,\mathrm{G15}}$” method. The “$\alpha_{160{\textendash}500,\mathrm{G15}}$” method leads to 0.25 dex lower molecular gas masses than “$\alpha_{850,\mathrm{S17}}$”, or 0.15 dex lower than “$\alpha_{850,\mathrm{H17}}$” for the majority of sources. A small number of sources with poor long-wavelength coverage, however, have smaller differences. This is probably due to the smaller $M_{\star}>10^{9}\;\mathrm{M}_{\odot}$ sample in (cite: Groves2015) and the intrinsic variation in $L_{\nu_{\mathrm{RJ,rest}}}/M_{\mathrm{mol\,gas}}$.

To summarize, we find that the gas mass calibrations are: $M_{\mathrm{mol\,gas}}\, _{(\delta_{\mathrm{GDR},\,Z})} \lesssim M_{\mathrm{mol\,gas}}\, _{(\alpha_{160{\textendash}500,\mathrm{G15}})} < M_{\mathrm{mol\,gas}}\, _{(\alpha_{850,\mathrm{H17}})} < M_{\mathrm{mol\,gas}}\, _{(\alpha_{850,\mathrm{S17}})}$. The systematic offsets are about 0.15–0.25 dex, but are comparable to the scatter of the data. Considering the relatively better agreement of the “$\alpha_{850,\mathrm{H17}}$” method to other methods as well as recent observations ((cite: Bertemes2018); (cite: Saintonge2018)), we choose the “$\alpha_{850,\mathrm{H17}}$” method as our final gas mass calculation for the A$^3$COSMOS galaxies. We also tested our full analysis with other gas mass calibrations in Sect. [5](#Section_Fitting_Multi_Variate_Function), finding that our results are not obviously altered.

# Galaxy Molecular Gas and Star Formation Properties

![](Plot_z_DeltaMS_two_panels)

After the calculation of molecular gas mass for A$^3$COSMOS galaxies, we combine them with our complementary galaxy samples listed in Table [\[Table_galaxy_samples\]](#Table_galaxy_samples), allowing us to study galaxy molecular gas and star formation scaling relations and gas evolution in the following sections. In total, we have 1,663 galaxies with redshift, SFR, stellar mass and molecular gas mass measurements. All complementary galaxies are selected to have CO detections and their molecular gas masses are homogenized with metallicity-dependent $\alpha_{\mathrm{CO}}$ as detailed in Sect. [2.2](#Section_Complementary_Galaxy_Samples). Such a combined sample is the largest, most-robust individually-detected sample so far, yet it still exhibits certain incompleteness in the parameter space of redshift, stellar mass and star formation due to sample selection biases. Therefore, before analyzing the gas scaling relations and the resulting gas evolution, we first provide detailed inspections below to constrain potential sample selection biases.

![](Plot_z_tauDepl_multi_panel_6x1_with_contours)

![](Plot_z_deltaGas_multi_panel_6x1_with_contours)

## Sample distribution across the MS

In Fig. [4](#Plot_z_DeltaMS) we show the specific star formation rate ($\mathrm{sSFR}$) versus redshift distribution, where sSFR is normalized by the MS sSFR of (cite: Speagle2014) at each redshift. The left and right panels have the same data points but have different X-axis scales and color schemes: the X-axis (redshift) is logarithmic in the left panel and only the complementary samples are color coded, while the redshift is linear in the right panel and only A$^3$COSMOS data points are color coded. Whereas our A$^3$COSMOS sample primely populates the $z>1$ regime, the complementary samples provide coverage at $z<1$. However, we do notice that the MS is not well sampled at $0.1 \lesssim z \lesssim 0.5$ and $z>1$. Only the most massive A$^3$COSMOS galaxies ($\log_{10}(M_{\star}/\mathrm{M}_{\odot})\gtrsim11.5$) sample well the MS, while less massive ones lie above.

The majority of $1 \lesssim z \lesssim 2$ complementary sample sources are from the PHIBSS 1&2 surveys () and (cite: Kaasinen2019). Compared to the A$^3$COSMOS galaxies, they are slightly less massive (see Table [\[Table_galaxy_samples\]](#Table_galaxy_samples)), thus sources are able to represent the $\log_{10}(M_{\star}/\mathrm{M}_{\odot})\sim10-11$ MS while the A$^3$COSMOS galaxies are probing the $\log_{10}(M_{\star}/\mathrm{M}_{\odot})\sim11-12$ MS at $z>1$.

We also notice that only very low redshift ($z \lesssim 0.03$) galaxies cover the $\log_{10}(M_{\star}/\mathrm{M}_{\odot})\sim9-10$ parameter space. In this low stellar mass range, the metallicity-dependent $\alpha_{\mathrm{CO}}$ might be more uncertain and so are the estimated molecular gas masses. However, this regime is important in understanding molecular gas scaling relations as shown in latter sections, thus here we still fit these galaxies from the complementary samples.

jsPlot_z_Mstar_deltaGas_DeltaMS_in_3D.x3d ![image]({Plot_z_Mstar_deltaGas_DeltaMS_in_3D_Screenshot.png})

## Correlating molecular gas fraction and depletion time to galaxy stellar mass and star formation properties

Here we study the scaling relations for the two most important molecular gas properties: molecular gas depletion time, $\tau_{\mathrm{depl}}\equiv M_{\mathrm{mol\,gas}}/ \mathrm{SFR}$, and molecular gas to stellar mass ratio, $\mu_{\mathrm{molgas}}\equiv M_{\mathrm{mol\,gas}}/ M_{\star}$. In Figs. [\[Plot_z_tauDepl_multi_panel\]](#Plot_z_tauDepl_multi_panel) and [5](#Plot_z_deltaGas_multi_panel), we show their distributions versus other galaxy properties, i.e., redshift, cosmic age, offset to the MS ($\Delta{\mathrm{MS}}$; using the MS of (cite: Speagle2014)), $M_{\star}$, SFR and sSFR. Two diagrams are shown for each distribution: a scatter plot (*upper panels*) and a contour plot (*lower panels*). In the contour plot, we show three sets of contours representing the data densities of A$^3$COSMOS galaxies (orange), PHIBSS 1&2 $0.5 \lesssim z \lesssim 2$ galaxies (green) and all other local/low-redshift galaxies (gray), respectively.

The molecular gas depletion time $\tau_{\mathrm{depl}}$ spans about one order of magnitude in the high-redshift range from $z\sim1$ to 6, but has more than two orders of magnitude variation at $z\sim0$. The latter can be due to the strong correlations with either $\Delta{\mathrm{MS}}$, SFR and/or sSFR, as shown in the corresponding scatter plots in Fig. [\[Plot_z_tauDepl_multi_panel\]](#Plot_z_tauDepl_multi_panel).

However, as the SFR and sSFR have redshift dependency, and the $M_{\star}$ distribution is biased differently from low to high redshift, it is unclear from just this figure which galaxy property mostly determines $\tau_{\mathrm{depl}}$. There is even a break or turn-over feature in the cosmic age and SFR versus $\tau_{\mathrm{depl}}$ panels, which is likely caused by the selection bias at $z>3$ where we only cover the most massive galaxies ($\log_{10} M_{\star}\sim 11-12$). In the intermediate redshift range ($1 \lesssim z \lesssim 3$), the A$^3$COSMOS and PHIBSS 1&2 surveys’ galaxies have very similar distributions as can be seen in the contour plots.

Similar plots are shown in Fig. [5](#Plot_z_deltaGas_multi_panel) for the molecular-gas-to-stellar mass ratio, $\mu_{\mathrm{molgas}}$. Compared to gas depletion time distributions, $\mu_{\mathrm{molgas}}$ has a nearly three orders of magnitude variation from local to high redshift, and even at $z>1$ the variation is still as large as two orders of magnitude. From the first two panels, we see a moderate redshift evolution and a strong dependency on stellar mass, respectively. $\mu_{\mathrm{molgas}}$ also exhibit a strong dependency on $\Delta{\mathrm{MS}}$, but local galaxies are systematically offset from the high-redshift ones by nearly one dex.

As shown in the $M_{\star}$–$\mu_{\mathrm{molgas}}$ panel, local galaxies and high-redshift galaxies seem to follow different distributions: local galaxies have similar $\mu_{\mathrm{molgas}}$ across different stellar mass, while high-redshift ones exhibit a steep slope. However, we caution that this is likely an artifact of the high-redshift sample selection using submm data, as the submm selection is similar to an SFR-selection or a dust-mass-selection, picking up massive MS galaxies and less massive but starbursty galaxies (see Fig. [4](#Plot_z_DeltaMS)).

The last two columns of Fig. [5](#Plot_z_deltaGas_multi_panel) show clear and tight correlations between $\mu_{\mathrm{molgas}}$ and SFR and sSFR. Local, PHIBSS 1&2 intermediate-redshift and A$^3$COSMOS higher-redshift galaxies form a contiguous distribution from SFR $\sim0.1$ to $>$1000$\;\mathrm{M}_{\odot} \, \mathrm{yr}^{-1}$ and sSFR $\sim0.01$ to $\sim50\;\mathrm{Gyr}^{-1}$. This is likely a combined effect of the SFR or sSFR evolution and the evolution of molecular gas content.

The last scatter plot, when canceling out the $M_{\star}$ term in both axes, is equivalent to the $M_{\mathrm{mol\,gas}}$ versus SFR correlation, i.e., Kennicutt-Schmidt law ((cite: Schmidt1959; Kennicutt1998SFL)). A log-log space linear fitting gives a slope of $\sim0.7$ with a scatter of 0.3 dex, consistent with (cite: Kennicutt1998SFL), as well as the slope of $\sim0.8$ as measured by (cite: Sargent2014) for MS and strong starbursts separately (see also Sect. [4.4](#Section_Results_SF_Law)).

![](Plot_z_sSFR_gas_evolution)

Again, while Figs. [\[Plot_z_tauDepl_multi_panel\]](#Plot_z_tauDepl_multi_panel) and [5](#Plot_z_deltaGas_multi_panel) show that observational data from a variety of samples span a wide range of parameters space and are consistent where they overlap, we caution that not all parameters are independent in these plots and the apparent correlations have degeneracies. Therefore, a high-dimensional-space fitting to the data is important to characterize the relative contribution of each key parameters to the observed gas fraction and depletion time. In Fig. [6](#Plot_z_deltaGas_3D) (online-only), we show our data points in three-dimensional (3D) space to better illustrate the complexity. And we perform such a high-dimensional-space function fitting in the next section.

![](Plot_Kennicutt_Schmidt_Law_with_Large_Samples)

## Composite view of galaxy gas fraction and MS evolution

We show in Fig. [7](#Plot_z_sSFR_gas_evolution) the composite view of the distributions among the four parameters: gas fraction, redshift, stellar mass and SFR. The first-level information in the figure is the sSFR evolution of our galaxies binned by redshift and stellar mass (curves are the (cite: Speagle2014) MS). The second-level information is that in each redshift and stellar mass bin (the boxes in the figure), the horizontal spanning represents the gas fraction $f_{\mathrm{mol\,gas}}$ (Eq. [\[Equation_mugas\]](#Equation_mugas); 0% to 100% from bin center to edges; shown symmetric for illustration purpose) and the Y position is still sSFR as indicated by the global Y-axis. We can see that in the high-redshift bins if a galaxy has a high sSFR in each box, it spans more, meaning a higher gas fraction.

Since all data in these boxes share the same Y-axis, the sSFR of the data can be directly read off from the figure and compared to the MS curves. The inhomogeneity of our sample is obvious in the less-massive galaxy bins (i.e., blue and yellow boxes) extending one to two dex above their corresponding MS, while the most-massive galaxies (i.e., the red boxes) merely extend more than one dex above the MS.

To summarize, with this “spindle” diagram, we can more clearly see that:

1.  At a fixed redshift, more-massive galaxies have both lower sSFR and gas fraction than less-massive ones.

2.  At a fixed redshift, galaxies that lie further above the MS exhibit higher gas fractions ($f_{\mathrm{mol\,gas}}$ approaching 100% for the ones with lowest mass and highest sSFR). (Yet such a trend is debated for individual or small ($\sim10$) samples of strong starburst galaxies ($\Delta{\mathrm{MS}}>0.6$), e.g., (cite: Silverman2015CO; Silverman2018CO).)

3.  Similar to the sSFR evolution, gas fraction evolves with redshift: galaxies of similar stellar mass and distance to the MS but at an earlier cosmic time tend to have a higher gas fraction. (These trends have been known anecdotally for more than ten years, e.g., (cite: Daddi2008BzK; Daddi2010BzK), (cite: Tacconi2008; Tacconi2010; Tacconi2013), (cite: Genzel2010), (cite: Magdis2012LBG), to name a few, but they have only been quantified recently with sufficiently large samples as presented here.)

![](Plot_DeltaMS_tauDepl_with_Large_Samples_in_Sargent2014_style_bin_by_lgMstar_color_by_lgSFR)

## Linking to the galaxy star formation law

The star formation law (or Kennicutt-Schmidt law; (cite: Schmidt1959); (cite: Kennicutt1998SFL); hereafter SF law) describes the correlation between molecular gas mass and star formation rate and has an empirical form of $\mathrm{SFR}= A \times M_{\mathrm{mol\,gas}}^{N}$, with a slope $N \approx 1.4$ in the log-log space ((cite: Kennicutt1998SFL); (cite: Gao2004b)). It is physically motivated by the fact that star formation is fueled by molecular gas. However, galaxies show a large scatter in the $M_{\mathrm{mol\,gas}}$–$\mathrm{SFR}$ plane, and some galaxies like local ultra-luminous infrared galaxies (ULIRGs; e.g., (cite: Sanders2003)) and bright high-redshift submm galaxies (SMGs; e.g., (cite: Smail1997; Blain2002)) are more than a one dex offset from “normal” star-forming galaxies. This is also referred to as the bimodal SF law (e.g., (cite: Daddi2010SFL); (cite: Genzel2010) for a strictly bimodal scenario; and (cite: Sargent2014) for a continuous dichotomy between “normal” star-forming and starburst galaxies). However, why these galaxies are offset from the normal star-forming SF law and whether they are also starbursts in the MS relations is still poorly explored. Given the popular assumption (or intense debate) on the main-sequence/starburst dichotomy and bimodality of SF laws, e.g., in analytic galaxy modeling ((cite: Sargent2012; Sargent2014; Bethermin2012; Bethermin2017Model)), and observational studies ((cite: Daddi2010SFL; Genzel2010; Silverman2015CO; Silverman2018CO; Elbaz2018; Cibinel2019)), we investigate these two topics with our large A$^3$COSMOS and compiled sample and present how current models are fitting the data.

Fig. [8](#Plot_SF_Law) shows the correlation between SFR and $M_{\mathrm{mol\,gas}}$ for all galaxies in this work. Data points are color-coded by $\Delta{\mathrm{MS}}$, and the A$^3$COSMOS and complementary samples are distinguished by different symbols (circle and cross, respectively). For A$^3$COSMOS galaxies with large SFR ($\sim100-3000\;\mathrm{M}_{\odot} \, \mathrm{yr}^{-1}$) and $M_{\mathrm{mol\,gas}}$ ($\sim5\times10^{10}-5\times10^{11}\;\mathrm{M}_{\odot}$), a higher $\Delta{\mathrm{MS}}$ means more deviation from the normal star-forming SF law (see the blue line in Fig. [8](#Plot_SF_Law); adopted from (cite: Sargent2014)). The strongest starbursts with more than one dex offset from the MS show a $0.43$ dex (median) offset from the star-forming SF law, while the offset for MS galaxies ($\Delta{\mathrm{MS}}<0.5$) is only $-0.12$ dex (median). Considering that the A$^3$COSMOS sample does not sample well the below-MS region, the $0.12$ dex offset does not prevent us from drawing the conclusion that MS galaxies also follow the normal star-forming SF law.

However, the starbursts which lie significantly above the MS ($\Delta{\mathrm{MS}}\sim 1$) seem to behave differently between the high-redshift and low-redshift/local samples. High-redshift starbursts do not show large enough offsets to reach the starburst SF law as indicated by the red line in Fig. [8](#Plot_SF_Law), which is offset by about one dex from the star-forming galaxies’ SF law. This is also recently found by CO observations of a small sample of 12 strong starbursts at $z\sim1.5$ by (cite: Silverman2015CO; Silverman2018CO). Meanwhile, some low-redshift/local MS starbursts with $\Delta{\mathrm{MS}}\sim0.5$ are able to reach the red line, and the trend between $\Delta{\mathrm{MS}}$ and the offset to the star-forming SF law is more clear there.

In Fig. [9](#Plot_DeltaMS_Delta_SF_Law), we more clearly illustrate the correlation between galaxies’ offsets to MS and SF law. The X-axis, $\mathrm{sSFR} / \mathrm{sSFR_{MS}}$, represents the offset to the MS, with $\mathrm{sSFR_{MS}}$ computed following (cite: Speagle2014). The Y-axis, $\tau_{\mathrm{mol\,gas}} / \tau_{\mathrm{mol\,gas,\,MS\,SF\,law}}$, represents the offset to the star-forming galaxies’ SF law, where $\tau_{\mathrm{mol\,gas,\,MS\,SF\,law}} \equiv M_{\mathrm{mol\,gas,\,SF\,law}} / \mathrm{SFR}_{\mathrm{MS}} = \alpha \times \mathrm{SFR}^{\beta} / \mathrm{SFR}_{\mathrm{MS}}$, and the $\alpha$ and $\beta$ coefficients are taken from (cite: Sargent2014). Galaxies are binned into four panels by their stellar masses in Fig. [9](#Plot_DeltaMS_Delta_SF_Law). Data points are color-coded by SFR. Model-predicted curves from (cite: Sargent2014) are shown for comparison. Their model, named the two-star-formation-mode (2-SFM) model, assumes that galaxies have two modes of star formation — a MS mode and a starburst mode. MS galaxies (e.g., $\mathrm{sSFR} \lesssim 3\times\mathrm{sSFR_{MS}}$) obey the SF law with a Galactic-like $\alpha_{\mathrm{CO}}$, while starbursts with sSFR above the MS (e.g., $\mathrm{sSFR} \gtrsim 3\times\mathrm{sSFR_{MS}}$) are shifted toward the starbursts’ SF law and they also have a much lower $\alpha_{\mathrm{CO}}$. The shift in the SF law plane happens most rapidly when the sSFR increases from $\sim3$ to $\sim4\times$ the MS’s sSFR (see Fig. 9 of (cite: Sargent2014)), thus causing the steep model turnover seen in Fig. [9](#Plot_DeltaMS_Delta_SF_Law).

The data are more complicated than what the 2-SFM model predicts. Galaxies in the lowest mass bin ($\log_{10} M_{\star}<9.8$) are below the model-predicted curve, while in the mid-stellar-mass bins ($\log_{10} M_{\star}\sim9.8-11.2$) some galaxies are above it. The turnover is likely seen in the two higher mass bins ($\log_{10} M_{\star}>10.5$ whereas it is less obvious in the two lower mass bins. The difference can not be explained by the calibration of the MS because of the reasonably good agreement between MS calibrations (see Fig. [9](#Plot_DeltaMS_Delta_SF_Law) caption). The molecular gas masses for the lowest-mass galaxies, which are mostly from complementary samples, are calculated via a metallicity-dependent $\alpha_{\mathrm{CO}}$ (see Sect. [2.2](#Section_Complementary_Galaxy_Samples)), therefore, $\alpha_{\mathrm{CO}}$ seems to be not strong biased. While their SFRs are derived using optical photometry and lack far-IR data, they intrinsically have a low metallicity and are dust poor, thus the lack of far-IR/mm should not introduce a significant bias. Unfortunately, observational evidence is still scarce. (cite: Coogan2019) presented CO non-detections for five low-mass ($\langle\log_{10} M_{\star}\rangle=9.8$) galaxies at $z\sim2$, resulting in an upper limit on their gas depletion times of $<0.8\,$Gyr, or $\tau_{\mathrm{mol\,gas}}/\tau_{\mathrm{MS,\,SF\,law}}<0.6$ (assuming a Galactic $\alpha_{\mathrm{CO}}$), in agreement with our findings. If the difference between data and model is truly significant, then it implies that low-mass ($\log_{10} M_{\star}\lesssim 10.0$) MS galaxies might follow a different SF law with $3\times$ faster molecular gas depletion than higher-mass MS galaxies. But this is yet to confirm with more observations.

In the other three higher-mass bins, from MS to starburst regime, we find good agreements between the data and model for galaxies close to and below the MS, meaning again that MS galaxies also obey the SF law. Nevertheless, a number of strong starburst galaxies show slower gas depletion (longer gas depletion times) than they should have according to the model. The majority of these strongest starburst outliers with long gas depletion times are from the complementary samples (e.g., (cite: Villanueva2017) and (cite: Combes2013)) with CO observations but without metallicity information. In this case, their $\alpha_{\mathrm{CO}}$ values are indirectly inferred from their stellar masses and SFRs (see Appx. [9.4](#Section_MZR)). (cite: Silverman2015CO; Silverman2018CO) found that a different choice of $\alpha_{\mathrm{CO}}$ alters the $\tau_{\mathrm{mol\,gas}}/\tau_{\mathrm{MS,\,SF\,law}}$ ratio from close to one to 0.2 for a starburst galaxy with $\Delta{\mathrm{MS}}\sim1$ dex (see their Fig. 8). Therefore it is still unclear how well the molecular gas masses (or stellar mass) can be constrained in these strongest starbursts (more detailed multi-line gas studies are needed, e.g., with RJ-tail dust continuum plus multi-$J$ CO \[e.g., (cite: Liudz2015)\] plus other tracers, to settle this issue).

We also caution that our high-redshift, intermediate-mass ($\log_{10}M_{\star}\sim 10 - 11$) sample has a strong bias toward a higher $\Delta{\mathrm{MS}}$, thus we sample better the region above the model curve than below it. This sample bias is less significant for the most massive bin ($\log_{10}M_{\star}\gtrsim 11$) where we most clearly see the turnover.

To summarize the link between the MS and the SF law, we find that: *(a)* massive ($\log_{10}M_{\star}\sim 10 - 12$) MS galaxies obey the star-forming galaxies’ SF law; *(b)* from the MS to $\Delta{\mathrm{MS}}\gtrsim1$, galaxies start to deviate from the star-forming galaxies’ SF law toward the starbursts’ SF law, with a rapid change at $\Delta{\mathrm{MS}}\sim0.4-0.6$ dex roughly in agreement with the 2-SFM prediction; *(c)* low-mass ($\log_{10}M_{\star}\lesssim 10$) galaxies appears to have systematically shorter gas depletion times and even the MS ones do not obey the star-forming galaxies’ SF law.

These details will likely stimulate further refinement of the popular models and observing strategies.

## Intermediate summary on the advantage and caveats of this sample

In the previous sections, we illustrated the wide dynamical range of our sample. Such a data set is the largest sample for the study of gas scaling relation and its evolution to-date, and will grow with future processing of the ALMA archive in the COSMOS deep field under A$^3$COSMOS. The distribution of our sample in the ($z$,$M_{\star}$,$\Delta{\mathrm{MS}}$) high-dimensional space is roughly contiguous from $(z,\,\log_{10} M_{\star},\,\Delta{\mathrm{MS}}) \sim (0.0,\,9.5,\,-1)$ to $\sim(5.0,\,12.0,\,+1)$. The gas mass calibrations for the CO and dust sub-samples are in good agreement where they overlap in the parameter space.

Nevertheless, the comprehensive presentation of our data set in previous figures also reveals that the sample is non-uniformly distributed and only partially covers the full parameter space. Our sample is biased toward submm-detected (i.e. IR-bright), massive high-redshift galaxies, as well as CO-detected (gas-rich), massive local/low-redshift galaxies. The impact of such sample biases on the results are hard to quantify with the current dataset. Stacking ALMA data for sufficient numbers of faint galaxies with similar properties can help to cover additional portions of the parameter space and will be presented in future work. Meanwhile, low-$J$ CO and RJ-tail dust observations toward samples covering the less-probed areas of the parameter space hold the key to further improve such studies.

# Characterizing Galaxy Molecular Gas Scaling Relation via Functional Fitting

Through our previous discussion of galaxy properties (molecular gas to stellar mass ratio $\mu_{\mathrm{molgas}}$, molecular gas depletion time $\tau_{\mathrm{depl}}$, stellar mass $M_{\star}$, star formation rate $\mathrm{SFR}$, and redshift $z$ or the corresponding cosmic age $t_{\mathrm{cosmic age}}$), we can already see the complexity inherent in the their scaling relations. In this section, we provide high-dimensional functional fittings to simultaneously quantify the underlying dependencies of $\mu_{\mathrm{molgas}}$ and $\tau_{\mathrm{depl}}$ on $z$ (or $t_{\mathrm{cosmic age}}$), $M_{\star}$ and $\mathrm{SFR}$.

![image](Plot_z_tauDepl_multi_variate_function_fitting) ![image](Plot_z_deltaGas_multi_variate_function_fitting)

We propose a new functional form which accounts for the different behaviors of galaxies due to their stellar masses seen in the previous figures: $$\begin{equation}
\begin{split}
\log_{10} \tau_{\mathrm{depl}}
&= (\mathsf{a} + \mathsf{ak} \times \log_{10} (M_{\star}/10^{10})) \times \Delta{\mathrm{MS}}\\
& \; + \mathsf{b} \times \log_{10} (M_{\star}/10^{10}) \\
& \; + (\mathsf{c} + \mathsf{ck} \times \log_{10} (M_{\star}/10^{10})) \times t_{\mathrm{cosmic\,age}} \\
& \; + \mathsf{d} \\[0.5ex]
(\textnormal{best-fit:} \ 
& \mathsf{a}  = -0.5724, 
\ \mathsf{b}  = -0.5174, \ \\
& \mathsf{c}  = -0.002997, 
\ \mathsf{d}  = +0.02964, \ \\
& \mathsf{ak} = +0.1120 \ \textnormal{and} 
\ \mathsf{ck} = +0.0568) 
\\[1.25ex]
\log_{10} \mu_{\mathrm{molgas}}
&= (\mathsf{a} + \mathsf{ak} \times \log_{10} (M_{\star}/10^{10})) \times \Delta{\mathrm{MS}}\\
& \; + \mathsf{b} \times \log_{10} (M_{\star}/10^{10}) \\
& \; + (\mathsf{c} + \mathsf{ck} \times \log_{10} (M_{\star}/10^{10})) \times t_{\mathrm{cosmic\,age}} \\
& \; + \mathsf{d} \\[0.5ex]
(\textnormal{best-fit} \ 
& \mathsf{a}  = +0.4195, 
\ \mathsf{b}  = -0.6906, \ \\
& \mathsf{c}  = -0.1543, 
\ \mathsf{d}  = +0.9339, \ \\
& \mathsf{ak} = +0.1195 \ \textnormal{and} 
\ \mathsf{ck} = +0.0320) 
\end{split}
\label{Equation_tauDepl_deltaGas}
\end{equation}$$ where $t_{\mathrm{cosmic\,age}}$ and $M_{\star}$ are in units of Gyr and $\mathrm{M}_{\odot}$ respectively.  [^5]

Here we adopt the MS function from the #49 fitting of Table 7 of (cite: Speagle2014), which is their preferred fit (see their abstract and Table 9). This functional form also uses cosmic age as a free parameter (as in our function).  [^6] We compared various MS in the literature (e.g., (cite: Whitaker2014); (cite: Sargent2014); (cite: Bethermin2015); (cite: Schreiber2015); (cite: Lee2015); (cite: Tomczak2016); (cite: Pearson2018)), finding that the (cite: Speagle2014) cosmic age MS function provides the most reasonable fitting (see Appx. [9.5](#Section_MS)). It can be rewritten in the same style as the above functions as: $$\begin{equation}
\begin{split}
\log_{10} \mathrm{SFR}_{\mathrm{MS}} 
&= \mathsf{b} \times \log_{10} (M_{\star}/10^{10}) \\
& \; + (\mathsf{c} + \mathsf{ck} \times \log_{10} (M_{\star}/10^{10}) ) \times t_{\mathrm{cosmic\,age}} \\
& \; + \mathsf{d} \\[0.5ex]
\textnormal{where} 
\ & \mathsf{b} = +0.84, 
\   \mathsf{c} = -0.15, 
\   \mathsf{d} = +1.89, \ \textnormal{and} \\
\ & \mathsf{ck} = -0.026, 
\end{split}
\label{Equation_Speagle2014}
\end{equation}$$

We fit our new functional form to the combined sample in this work, as well as re-fitted both the and functional forms, i.e., described in Eq. [\[Equation_Scoville2017\]](#Equation_Scoville2017) and Eq. [\[Equation_Tacconi2018\]](#Equation_Tacconi2018), respectively. We use the

`Python`

packages

`pymc3`

and

`scipy.optimize.curve_fit`

for the fitting [^7]. The former package performs Markov chain Monte Carlo (MCMC) fitting to calculate the probability distribution of the fitting, while the latter one performs least-chi-square minimization to find the best fit. The two algorithms agree very well, and the former one provides better uncertainty estimates for the fitted parameters.

We list our best-fit parameters in Table [\[Table_functions\]](#Table_functions) as well as in Eq. [\[Equation_tauDepl_deltaGas\]](#Equation_tauDepl_deltaGas). The parameters fitted by and for their own functional forms are also provided in Table [\[Table_functions\]](#Table_functions) for comparison.

Our re-fitting of the function agrees with their original fitting: only the redshift coefficient is slightly changed by about 10%, which implies that the two fittings are consistent ($<30\%$) at $z<2$ and slightly discrepant at $z\sim3-5$ where our fitting predicts about 30%-50% lower gas fractions and shorter depletion times, mainly driven by the new data coverage from this work (their data only covers $z\sim0-3$).

For our new function, the fitted dependencies of gas fraction and depletion time on each parameter are presented in Fig. [10](#Plot_multi_variate_function_fitting). We show in each panel the best-fit function curve and the data points with a rescaling to remove the dependencies on other parameters than the current one presented by the X-axis of that panel. This rescaling uses our best-fit result, for example, for the rescaling in the first panel, the gas-to-stellar mass ratio $\mu_{\mathrm{molgas}}$ of a galaxy with $\Delta{\mathrm{MS}}=1$ and $\log_{10} M_{\star}=10.5$ will be scaled by $-0.4123\times\Delta{\mathrm{MS}}$ dex, bringing it down to the MS galaxy level. In this way, each panel only indicates the dependency of our function fitting on the parameter presented by the X-axis.

We also show the original best-fits of and (to their own functional forms, i.e., Eqs. [\[Equation_Tacconi2018\]](#Equation_Tacconi2018) and [\[Equation_Scoville2017\]](#Equation_Scoville2017), respectively) in Fig. [10](#Plot_multi_variate_function_fitting). In comparison, our new functional form has a log-linear dependency on cosmic age, therefore $\mu_{\mathrm{molgas}}$ and $\tau_{\mathrm{depl}}$ almost flatten beyond redshift $\sim4$ for the same stellar mass and $\Delta{\mathrm{MS}}$ galaxies. The best-fit function predicts a drop at $z\sim4$ in $\mu_{\mathrm{molgas}}$, while the best-fit function predicts $\mu_{\mathrm{molgas}}$ to continue increasing with redshift. In the $\Delta{\mathrm{MS}}$ and $M_{\star}$ panels, we also see certain differences, but our function is in between the and ones.

The current fitting still has some minor caveats. For example, in the redshift panel, the limited number of $z>4.5$ data points are mostly below our best-fit function. But as we discussed in Sect. [3.2.1](#Section_Band_conversion), the band conversion for rest-frame R-J tail dust continuum has a large uncertainty when there are no long-wavelength data, which is the case for $z>4$ galaxies. The test in Appx. [10](#Section_Appendix_SED_band_conversion) shows that our SED fitting tends to underestimate their true R-J tail dust continuum by a factor of 2–6.

In addition, we tested the stability of our fitting for subsamples of galaxies: (a) only $z<4$ data, and (b) without $z>1$ CO (which are mostly from the PHIBSS 1&2 surveys from ), i.e., only using A$^3$COSMOS dust-based data at $z>1$. The tests show that the $z>4$ data and $z>1$ CO data do not statistically bias our fitting results, likely because their numbers are not large enough compared to the full sample. The $\chi^2$ information of these test fittings are listed in Table [\[Table_function_fittings\]](#Table_function_fittings), which shows that our proposed functional form in Eq. [\[Equation_tauDepl_deltaGas\]](#Equation_tauDepl_deltaGas) gives statistically better fits to the data in this work than both the (Eq. [\[Equation_Tacconi2018\]](#Equation_Tacconi2018)) and (Eq. [\[Equation_Scoville2017\]](#Equation_Scoville2017)) functions, and that the one is better than the one. This is likely because our function (Eq. [\[Equation_tauDepl_deltaGas\]](#Equation_tauDepl_deltaGas)) has one more free parameter than the function, which further has one more degree of freedom than the function.

Moreover, we have run our full fitting process for other gas mass calibration methods. We find that using the gas mass calibration, which slightly overpredicts gas masses compared to the H17 calibration, leads to $\lesssim11\%$ changes in the coefficients in Eq. [\[Equation_tauDepl_deltaGas\]](#Equation_tauDepl_deltaGas), and results in a $11\%$ shallower $\mu_{\mathrm{molgas}}$ versus stellar mass (negative) dependency. This in turn increases the prediction of $\mu_{\mathrm{molgas}}$ for main-sequence, $\log_{10} M_{\star}\sim10.5$ galaxies by a small amount of about $20\%$ at $z\sim6$. On the other hand, using the $\delta_{\mathrm{GDR},\,Z}$ gas mass calibration which tends to underestimate the gas masses, the coefficients change by $\lesssim40\%$. This results in a $\sim40\%$ steeper $\mu_{\mathrm{molgas}}$ versus stellar mass (negative) dependency, and consequently lower $\mu_{\mathrm{molgas}}$ for main-sequence, $\log_{10} M_{\star}\sim10.5$ galaxies at $z\sim6$ by about $50\%$. The scatters in the diagnostic plots similar to those in Fig. [10](#Plot_multi_variate_function_fitting) are also larger by about 0.06 dex (e.g., the scatters around the best-fit lines in Fig. [10](#Plot_multi_variate_function_fitting) are about 0.28–0.30 dex with the $\alpha_{850,\mathrm{H17}}$ calibration, while they are 0.33–0.36 dex with the $\delta_{\mathrm{GDR},\,Z}$ calibration). We also note that the slope of the $\mu_{\mathrm{molgas}}$ versus $\Delta{\mathrm{MS}}$ correlation is much less obviously affected ($\mathsf{a}\sim0.39$–0.41), and the fits close to $z\sim0$ are not obviously affected due to the large number of local/low-$z$ galaxies in our sample with CO-based gas masses. These tests show that the choice of gas mass calibration method is not significantly altering our result — by at most a factor of two at $z\sim6$ and $\log_{10} M_{\star}\sim10.5$, and less at lower redshifts.

Finally, we emphasize that, despite the fact that nearly all gas masses for our high-redshift ($z>2.5$) galaxies are dust-based and similarly those for local/low-redshift ($z<1$) galaxies are CO-based, we verified that our results are not significantly biased. Specificially we have: (a) excluded all CO-based galaxies and (b) all dust-based galaxies from our fitting. We find that the slopes of both the $\mu_{\mathrm{molgas}}$ versus $\Delta{\mathrm{MS}}$ and $\mu_{\mathrm{molgas}}$ versus $\log_{10} M_{\star}$ correlation are quite stable within 20%. However, the trend of the time evolution is significantly driven by the lack of constraining data at either low- or high-redshift: Excluding all CO-based galaxies leads to a factor of 10 higher gas fraction at $z\sim0$, because there is basically no constraint at $z<1$. While excluding all dust-based galaxies gives a factor of 2 higher gas fraction at $z\sim4$–6, due to little constraint at $z>3$. Taking together the good consistency when fitting the non-redshift-dependent correlations, and the good agreement between CO- and dust-based gas mass calibrations in the literature (see beginning of Sect. [3](#Section_Molecular_Gas_Mass_Calculation)), it is not only very reasonable to combine the CO- and dust-based samples and but also necessary to achieve sensible results.

# Predictions from The Fitted Gas Evolution Functions

![](Plot_z_tauDepl_comparison)

![](Plot_z_deltaGas_comparison)

## Evolution of molecular gas depletion time

Here we discuss the cosmic evolution of the molecular gas depletion time $\tau_{\mathrm{depl}}$ as predicted by our best-fit function (Eq. [\[Equation_tauDepl_deltaGas\]](#Equation_tauDepl_deltaGas)) for galaxies in bins of stellar mass and MS offset. In Fig. [\[Plot_z_tauDepl_comparison\]](#Plot_z_tauDepl_comparison), we bin all our 1,653 galaxies into $4\times3$ bins, with the $\log_{10} M_{\star}$ bin center ranging from $9.0$ to $12.0$ (bin width 1.0) and the $\Delta{\mathrm{MS}}$ bin center ranging from $-0.5$ to $+0.5$ (bin width 0.5). The predictions of our best-fit function are shown as solid lines, while the predictions from and functions (with their fitting) are shown as long- and short-dashed lines, respectively, for comparison. Galaxies in each panel are also binned in small redshift interval so as to show the mean and scatter at each redshift.

From the figure, we can see that our function behaves differently than the other two functions. The evolution of $\tau_{\mathrm{depl}}$ exhibits a much stronger dependency on stellar mass in our function. For very massive ($\log_{10} M_{\star}\sim12.0$) galaxies, our function predicts a factor of about 20 increase in $\tau_{\mathrm{depl}}$ from very early cosmic time to the present, while the and functions predict only a factor of 5–8 increase. Data from this work favors our function in these bins. Meanwhile, for low-mass ($\log_{10} M_{\star}\sim9.0$) galaxies, our function predicts a reversed evolutionary trend than the and functions. That means, a galaxy with a stellar mass as low as $\log_{10} M_{\star}\sim9.0$ has a longer depletion time at an earlier cosmic time, and its star formation speeds up with cosmic age. Current data in these bins are not sufficient to clearly distinguish which function is better.

The few CO observations available for local dwarf galaxies (e.g., (cite: Bolatto2011), (cite: Cormier2014)) show that $\tau_{\mathrm{depl}}$ ranges from $0.1$ to $1.0\;\mathrm{Gyr}$ (with SFR$\sim20-30$ to $0.04\;\mathrm{M}_{\odot} \, \mathrm{yr}^{-1}$, i.e., from high to low $\Delta{\mathrm{MS}}$, respectively). These observations still agree with the predictions of our function.

We caution that this figure does not track the evolution of individual galaxies, as they grow in stellar mass and may have rapidly changed $\Delta{\mathrm{MS}}$ with time. Thus, for example, the flat $\tau_{\mathrm{depl}}$ versus redshift trend for less-massive ($\log_{10} M_{\star}\sim10.0$) galaxies seen in the middle columns of the figure does not imply a constant $\tau_{\mathrm{depl}}$ for an individual galaxy across its evolution history — its stellar mass growth will move it into a higher stellar mass $\tau_{\mathrm{depl}}$ evolution track. In the $\log_{10} M_{\star}\sim10.0$ and $\Delta{\mathrm{MS}}\sim0.5$ bin, our function does not fit well the $z\sim3-5$ galaxies while the and functions do. This is mainly driven by the small number of low-mass starburst galaxies in this redshift range. As already discussed in Sect. [4.4](#Section_Results_SF_Law), our sample within this range is sparse, biased and the statistics is expected to be less significant.

If only looking at the function predictions, our function actually provides a coherent picture of galaxy “down-sizing” (e.g., (cite: Cowie1996); (cite: Thomas2005)), i.e., more-massive galaxies (possibly in more-massive dark matter halos) evolve earlier than less-massive galaxies. Meanwhile, the star formation in the most massive galaxies quickly slows down at redshift 2–3, which probably points to the “mass-quenching” effect (e.g., (cite: PengYingJie2010_SMF)).

Below we also compare the predictions of our functions with other works in the literature. Our formula predicts that, for local galaxies with stellar mass $3 \times 10^{9}$, $3 \times 10^{10}$, $3 \times 10^{11}$ and $3 \times 10^{12} \, \mathrm{M}_{\odot}$, their $\tau_{\mathrm{depl}}=0.7$, 1.3, 2.6 and 5.0 Gyr, respectively. In comparison, (cite: HuangMeiLing2014; HuangMeiLing2015) studied about 600 local galaxies from the HERACLES ((cite: Leroy2009)), ATLAS3D ((cite: Cappellari2011); (cite: Alatalo2013)) and COLD GASS ((cite: Saintonge2011a; Saintonge2011b)) surveys, and found $\tau_{\mathrm{depl}}= -0.36 \log_{10} \mathrm{sSFR} - 0.14 \log_{10} (\Sigma_{\star}) + 5.87$ [^8]. This translates into $\tau_{\mathrm{depl}}=1.2$, 1.5, 2.0 and 2.9 Gyr for the four aforementioned stellar masses, assuming that the galaxy size follows the (cite: FernandezLorenzo2013) and (cite: Shen_2003_Galaxy_Sizes) size–mass relation. Thus the predictions agree within 20% for the two intermediate stellar mass ranges, or $\sim50\%$ for all ranges. We note that the $3 \times 10^{12} \, \mathrm{M}_{\odot}$ case is an extrapolation of their function as their data only probe galaxies with $10^{10} < M_{\star}/\mathrm{M}_{\odot}< 10^{11.5}$.

New observations are needed in the future to clearly distinguish which function is better, and confirm whether our function can reproduce “down-sizing” and “mass-quenching”. Such observations should prioritize low-mass galaxies at high redshift (with enough sensitivity and integration time), as well as highest-mass but below-MS galaxies at the early cosmic time (though such galaxies are still rarely found).

## Evolution of molecular gas fraction

Similar to the previous section, we show in Fig. [11](#Plot_z_deltaGas_comparison) the binned view of the evolution of $\mu_{\mathrm{molgas}}$ as predicted by our best-fit function Eq. [\[Equation_tauDepl_deltaGas\]](#Equation_tauDepl_deltaGas). The three evolution functions in Fig. [11](#Plot_z_deltaGas_comparison), i.e., from our Eq. [\[Equation_tauDepl_deltaGas\]](#Equation_tauDepl_deltaGas), and consistently show that $\mu_{\mathrm{molgas}}$ has a strong dependency on stellar mass. More-massive galaxies have a lower gas fraction at the same redshift. These functions are also very close to each other for $\log_{10} M_{\star}\gtrsim 11$ galaxies at all redshifts below $\sim3$. For lower-mass galaxies, our function locates between the and ones. ’s function does not fit well local galaxies because they do not include local samples in their analysis. But at high redshift our function in this work predicts similarly high gas fraction as the function, which are a factor of ten higher than those expected from the function (for $\log_{10} M_{\star}\sim9$ galaxies).

The dependency of $\mu_{\mathrm{molgas}}$ or $f_{\mathrm{gas}}$ on stellar mass has also been found much earlier for local galaxies (cite: Young_and_Scoville_1991_ARAA; Kennicutt1998ARAA; McGaugh1997; Schombert2001). (cite: Young_and_Scoville_1991_ARAA) reported an increase in gas fraction by two orders of magnitude from early-type to late-type galaxies (along the Hubble sequence) in the local Universe. This is equivalent to similar orders of magnitude increase in their IR to $H$-band luminosity ratio, i.e., $\propto$ sSFR (cite: Kennicutt1998ARAA). (cite: McGaugh1997) and (cite: Schombert2001) also found strong decreases in the gas fraction with brighter $B$-band magnitude (higher stellar mass) and higher stellar surface density including low surface brightness local galaxies. This is in agreement with our function’s prediction.

More recently, (cite: JiangXueJian2015) reported a similarly strong decrease in gas fraction versus stellar mass as reported here, down to a stellar mass of $10^{8.5-9.0}\;\mathrm{M}_{\odot}$ (see also (cite: CaoTianWen2017); (cite: Saintonge2017)) with a non-linear behavior. In their sample, $\mu_{\mathrm{molgas}}$ is about 0.08–0.3 for $\log_{10} M_{\star}\sim9-10$ galaxies, then decreases to about 0.02–0.1 for $\log_{10} M_{\star}\sim10-11$ galaxies, which is slightly below this work at $z\sim0$ and is likely caused by their use of a constant $\alpha_{\mathrm{CO}}$ while the true $\alpha_{\mathrm{CO}}$ might be higher for low-mass metal-poor galaxies.

In summary, the predictions from this work, and only obviously differ in those regimes where not much data are currently available, i.e. at low stellar masses across cosmic time and for all stellar masses at $z>5-6$. This work’s predictions agree with other individual observations in the literature, and our evolution function has the physical implications of “down-sizing” and “mass-quenching” in galaxy evolution. In general our analysis also raises the need for future CO and RJ-dust observations of below-MS and/or less-massive ($\log_{10} M_{\star}\lesssim10$) galaxy samples.

![](Plot_cosmic_evolution_of_rho_molgas_with_data)

![](Plot_cosmic_evolution_of_rho_molgas_via_galaxy_model)

# Implication for the Cosmic Evolution of Cold Molecular Gas Density

In this section, we study the implication of our cold molecular gas fraction function (Eq. [\[Equation_tauDepl_deltaGas\]](#Equation_tauDepl_deltaGas)) for the cosmic molecular gas mass density evolution. This requires us to know: (a) the number density of star-forming galaxies at each redshift; (b) their stellar mass distribution at each redshift; and (c) their SFRs.

The number density and stellar mass distribution evolution of star-forming galaxies have been reasonably well measured through star-forming galaxies’ stellar mass function (SMF) studies. We discuss them in detail in Sect. [7.1](#Section_Adopting_the_SMFs).

Then, by either simply assuming that all star-forming galaxies are MS galaxies (Sect. [7.2](#Section_Results_z_rhomolgas)), or more realistically adopting the aforementioned 2-SFM galaxy modeling ((cite: Sargent2014); (cite: Bethermin2017Model)) as we do later in Sect. [7.3](#Section_Results_z_rhomolgas_2SFM), we obtain a SFR for each galaxy corresponding to its stellar mass and redshift. With the SFR and $\Delta{\mathrm{MS}}$, the stellar mass is further converted to gas mass by applying our gas fraction function. Finally, by integrating over all star-forming galaxies, we obtain the cosmic molecular gas mass density at each redshift as presented in Sects. [7.2](#Section_Results_z_rhomolgas) and [7.3](#Section_Results_z_rhomolgas_2SFM).

Such a method is also used by (cite: Maeda2017), who fitted molecular gas fraction versus stellar mass correlations at two redshift bins ($z\sim0$ and $z=1-1.5$), and then integrated the cosmic molecular gas mass density using stellar mass functions. Other earlier works ((cite: Sargent2013); see also (cite: Carilli2013Review)) instead fitted a molecular gas mass versus SFR correlation (i.e., SF law; independent of redshift and stellar mass) to infer gas mass and integrate over stellar mass functions to obtain the cosmic molecular gas mass density.

## Adopting the stellar mass functions (SMFs)

In recent years, deep *HST*, *Spitzer* and ground-based near-IR observations in deep fields have pushed the accurate measurements of the star-forming galaxies’ SMFs out to $z\sim4-5$ (e.g., (cite: Marchesini2009); (cite: PengYingJie2010_SMF); (cite: Baldry2012_SMF); (cite: Santini2012_SMF); (cite: Moustakas2013_SMF); (cite: Muzzin2013); (cite: Ilbert2013); (cite: Grazian2015); (cite: Song2016); (cite: Davidzon2017); (cite: Wright2017_SMF; Wright2018_SMF)). Similarly, deep *Herschel* far-infrared/sub-mm and ground-based sub-mm surveys pushed the accurate measurements of cosmic SFR density (CSFRD) out to $z\sim3-4$ as well (e.g., (cite: Madau2014Review); (cite: Liudz2017); and references therein). The CSFRD represents the SFR at each cosmic epoch, thus by integrating the SFR across all the previous cosmic times, we will be able to obtain the total stellar mass density at that time. Meanwhile, the integration of the (star-forming galaxies’) SMF at that cosmic time should in principle equal to the total stellar mass integrated from the CSFRD. In Appx. [12](#Section_Appendix_SMF_CSFRD), we verify that they are in good agreement for the redshift bins where empirical SMFs are available.

Note that the CSFRD has been described as a function of redshift (double-powerlaw; (cite: Madau2014Review)), while it is still difficult to characterize the SMF as a contiguous function of redshift. (cite: Wright2018_SMF) provide such a functional form, however, their function exhibits certain deviations from direct measurements (see Appx. [12](#Section_Appendix_SMF_CSFRD)). Therefore we construct our SMFs by adopting the $z$-evolving shape of the SMFs in the literature and normalize them according to the integrated CSFRD. The full description of this procedure and its verification on observational data can be found in Appx. [12](#Section_Appendix_SMF_CSFRD). Thus our assumed (star-forming galaxies’) SMFs and CSFRDs are consistent with each other at each redshift.

## Integrating cosmic molecular gas mass density

Based on the assumption that “all” star-forming galaxies exactly follow our gas fraction function (Eq. [\[Equation_tauDepl_deltaGas\]](#Equation_tauDepl_deltaGas)), and their number density obeys the SMF at each redshift, we can compute the molecular gas mass density by integrating the product of gas fraction, stellar mass and SMF in each stellar mass bin at each redshift: $$\begin{equation}
\begin{split}
&\rho_{\mathrm{molgas}} (z) = \\[1ex] 
&\ \sum\limits_{M_{\star}\;\mathrm{bins}} \Phi_{\mathrm{SMF}} (z,M_{\star}) \times M_{\star}\times \mu_{\mathrm{molgas}}(z, M_{\star},\Delta{\mathrm{MS}})
\end{split}
\label{Equation_integrating_SMF}
\end{equation}$$

In Fig. [12](#Plot_cosmic_evolution_of_rho_molgas_with_data) we present the integrated cosmic cold molecular gas mass density versus redshift, using three different gas fraction functions $\mu_{\mathrm{molgas}}(z, M_{\star},\Delta{\mathrm{MS}})$, our Eq.  [\[Equation_tauDepl_deltaGas\]](#Equation_tauDepl_deltaGas) (orange solid line), (green long-dashed line) and (pink short-dashed line). The same SMFs are used for the three gas fraction functions.

Note that the result is sensitive to the lower stellar mass limit down to which the integration is performed. (cite: Davidzon2017) adopt a lower limit of $M_{\star}=10^{8.0}\;\mathrm{M}_{\odot}$ when integrating SMFs to compute the cosmic stellar mass density. To match the CO blind deep field data (e.g., (cite: Riechers2019); (cite: Decarli2019)), we integrate only down to $M_{\star}=10^{9.0}\;\mathrm{M}_{\odot}$, i.e., an order of magnitude shallower.

In Fig. [12](#Plot_cosmic_evolution_of_rho_molgas_with_data), we compare results from three recent CO blind deep field surveys ((cite: Decarli2016), (cite: Riechers2019) and (cite: Decarli2019), from the ASPECS-pilot, COLDz and ASPECS-LP surveys, respectively), to the gas evolution curves derived from our, and functions. The form of the function $\mu_{\mathrm{molgas}}(z, M_{\star},\Delta{\mathrm{MS}})$ significantly impacts the resulting cosmic cold gas mass density curve. Both our and the functions provide very reasonable fits to the data without any tuning (except for the integration limit). Due to the fact that observationally CO luminosity detection limit varies with redshift and sample (or excitation “correction”), and is in general higher than the integration limits we chose, the currently available data can not sufficiently constrain these functions.

## Alternative method: Cosmic molecular gas mass density with mock galaxy models

The drawback of the SMF$\times\mu_{\mathrm{molgas}}$ integration in the previous section is that it only accounts for galaxies located exactly on the MS. In order to account for starburst galaxies as well as the scatter of the MS, we adopt here an alternative approach to derive the cosmic cold molecular gas mass density — we calculate for each mock galaxy (cite: Bethermin2017Model) the cold molecular gas mass using our $\mu_{\mathrm{molgas}}$ function before summing them up within each redshift bin.

The “SIDES” simulation (cite: Bethermin2017Model) generated 1,489,629 mock galaxies within a 2 deg$^2$ lightcone from redshift 0.02 to 9.95. Different sets of SMFs were adopted according to redshift ((cite: Kelvin2014) for local galaxies, (cite: Moutard2016) at $z<1.5$, (cite: Davidzon2017) at $1.5<z<4$ and (cite: Grazian2015) at $z>4$). Stellar masses were assigned to dark matter halos via abundance matching, and a certain recipe for the star-forming galaxy fraction was assumed at each redshift. The modeling also accounts for the scatter of the star-forming MS coming from both the MS population itself and starburst galaxies, thus it reasonably reproduces true galaxy distributions.

We use the SIDES mock galaxy catalog and select $\log_{10}M_{\star}>9.0$ star-forming galaxies (as in the previous section to match CO luminosity function studies), then apply Eq. [\[Equation_tauDepl_deltaGas\]](#Equation_tauDepl_deltaGas) (as well as the and functions) to each galaxy to obtain its gas fraction, and hence to derive its molecular gas mass. We integrate the molecular gas mass for all galaxies in a given redshift bin, then divide it by the corresponding comoving volume to obtain the cosmic cold gas mass density $\rho_{\mathrm{mol\,gas}}$. We sample the redshift range from 0 to 15 with 500 bins (i.e., bin size $\sim$0.00253 in $\log_{10}(1+z)$; as in the previous section).

The results are presented in Fig. [13](#Plot_cosmic_evolution_of_rho_molgas_via_galaxy_model). The wiggling at the low-redshift end is likely due to the cosmic variance. At higher redshifts ($z>0.5$) our curve coincidentally agrees with the Semi-Analytic Model (SAM) simulation by (cite: Popping2019). Other simulations, (cite: Obreschkow2009) and (cite: Lagos2011), can be seen in Fig. 5 of (cite: Riechers2019): at $z\sim5$, the (cite: Popping2019) simulation exhibit a 0.2 dex lower $\rho_{\mathrm{mol\,gas}}$ than that of (cite: Lagos2011), and the (cite: Obreschkow2009) $\rho_{\mathrm{mol\,gas}}$ is 0.1 dex lower than (cite: Lagos2011); while the three are reversed at $z\sim0.5$, but still within 0.2 dex. Thus in general the simulations and the predictions with the functional form derived here are in good agreement.

When using the and functions for the computation, the corresponding cold molecular gas mass density curves show large difference. The function leads to a much higher cold molecular gas mass density at all redshifts, which is likely because their function predicts significantly higher $\mu_{\mathrm{molgas}}$ (see Fig. [11](#Plot_z_deltaGas_comparison)).  [^9] The function results in fully (marginally) consistent cold molecular gas mass densities as our function at $z \lesssim 1$ ($z\sim2-3$), however, it predicts 0.4–0.9 dex lower values at $z>4$. This is mainly driven by the downturn of their $\mu_{\mathrm{molgas}}$ function at $z\gtrsim4$ (as mentioned in Sect. [5](#Section_Fitting_Multi_Variate_Function)) and probably also affected by their systematic lower $\mu_{\mathrm{molgas}}$ for low-mass galaxies (see Fig. [11](#Plot_z_deltaGas_comparison)). Nevertheless, due to the large uncertainties in the CO blind deep field data, it is still hard to distinguish whether our function is statistically better than the function. We will further investigate this with simulated galaxies ((cite: Popping2019)) in future work.

In summary, the above comparisons indicate that our knowledge on galaxy star-forming MS (e.g., the two-star-formation model (2-SFM); (cite: Sargent2014)), stellar mass functions (see references in (cite: Bethermin2017Model)) and molecular gas fraction parametrization (using our functional form of $\mu_{\mathrm{molgas}}$ in Eq. [\[Equation_tauDepl_deltaGas\]](#Equation_tauDepl_deltaGas)) are moving towards a coherent picture.

# Summary

In this work, we present a comprehensive analysis of galaxy molecular gas scaling relations and their evolution using a robust ALMA-detected galaxy catalog from our paper  (A$^3$COSMOS). Each galaxy in the catalog has a redshift, stellar mass, SFR and dust mass from far-infrared spectral energy distribution (SED) fitting including the ALMA data and rich multi-wavelength data from the literature (see paper  for the details). We compared four methods of molecular gas mass calibration using SED-fitted dust mass and/or Rayleigh-Jeans (RJ)-tail dust continuum (Sect. [3.3](#Section_comparing_gas_mass_calibration)), from which we determine that the RJ-dust continuum method (with (cite: Hughes2017) luminosity-dependent calibration) better infers the gas mass. Meanwhile, we also comprehensively discuss several related topics in the gas mass calibration, i.e., $\alpha_{\mathrm{CO}}$, $\delta_{\mathrm{GDR}}$, molecular-to-atomic fraction and metallicity, and their biases to this work in the Appendix (Appx. [9.1](#Section_ZACO) to [9.4](#Section_MZR)).

Due to the sample inhomogeneity, higher-redshift (e.g., $z>4$) galaxies do not always have RJ-tail wavelength coverage. Thus we investigated the effect of band conversion with MAGPHYS high-$z$ SED fitting for galaxies whose longest-wavelength ALMA data do not cover RJ-tail wavelengths. We found that it potentially results in a factor of 2–6 underestimation of gas mass at $z>4$ (see Sect. [3.2.1](#Section_Band_conversion) and Appx. [10](#Section_Appendix_SED_band_conversion)).

We combine our A$^3$COSMOS sample with 20 complementary samples in the literature from local to high redshift (see Table [\[Table_galaxy_samples\]](#Table_galaxy_samples)) to study the scaling relations and cosmic evolution of molecular gas depletion time $\tau_{\mathrm{depl}}$ and molecular gas to stellar mass ratio $\mu_{\mathrm{molgas}}$. We parameterize the $\tau_{\mathrm{depl}}$ and $\mu_{\mathrm{molgas}}$ as functions of galaxy’s cosmic age, stellar mass and SFR. We tested both (cite: Tacconi2018) and (cite: Scoville2017) functions (shown in Eqs. [\[Equation_Tacconi2018\]](#Equation_Tacconi2018) and [\[Equation_Scoville2017\]](#Equation_Scoville2017) respectively), meanwhile also propose a new functional form in Eq. [\[Equation_tauDepl_deltaGas\]](#Equation_tauDepl_deltaGas) which accounts for the galaxies’ different evolution driven by their stellar masses. Then, by applying the gas fraction scaling relation to galaxies’ stellar mass functions and integrating over all stellar masses, we obtain the evolution of cosmic cold molecular gas mass density, which is in a coherent picture with the known cosmic SFR density evolution and the semi-analytic modeling of galaxies in the cosmological simulations (Figs. [12](#Plot_cosmic_evolution_of_rho_molgas_with_data) and [13](#Plot_cosmic_evolution_of_rho_molgas_via_galaxy_model) respectively).

Further more, we emphasize the following points:

- The distribution of our sample’s redshifts, stellar masses and SFRs are consistent with previous studies where they overlap in the parameter space (e.g., see contours in Figs. [\[Plot_z_tauDepl_multi_panel\]](#Plot_z_tauDepl_multi_panel) and [5](#Plot_z_deltaGas_multi_panel)). Given our total sample of more than 1,600 galaxies, we see that the composite sample selection is biased to strong starbursts with $\Delta{\mathrm{MS}}\sim0.5-1.5$ and $\log_{10} M_{\star}\sim10-11$ at $z\sim0.08-1.0$ (see Fig. [4](#Plot_z_DeltaMS)), and biased to the most massive galaxies with $\Delta{\mathrm{MS}}\sim0.0$ and $\log_{10} M_{\star}\sim12$ at $z>3$ (see Figs. [6](#Plot_z_deltaGas_3D) and [7](#Plot_z_sSFR_gas_evolution)). In particular at $z>4$ the dust continuum observations are mainly probing rest-frame wavelengths shorter than 250 $\mu$m, for which the SED-fitting-extrapolated RJ-tail flux might be under-predicted. However, they do not statistically affect our functional fitting due to their low number.

- The parametrizations of $\tau_{\mathrm{depl}}$ and $\mu_{\mathrm{molgas}}$ with the functions in this work, and are roughly consistent where the data are commonly sampled in the parameter space, i.e., $z\sim1-3$, $\Delta{\mathrm{MS}}>0$ and $\log_{10} M_{\star}>10.5$ (see Figs. [\[Plot_z_tauDepl_comparison\]](#Plot_z_tauDepl_comparison) and [11](#Plot_z_deltaGas_comparison)). They differ significantly for low-mass and/or main-sequence or below-main-sequence galaxies, which, however, could not be verified with the current dataset. The chi-square statistics for these parametrization show that our new functional form and the are similarly good, and are better than the functional form which has one (two) less free parameter(s) than the one (ours). We emphasize that our new functional form implicitly leads to a *“down-sizing”* in galaxy evolution and probably a *“mass-quenching”* effect. Although further data are needed to verify these effects (see Sects. [6.1](#Section_Results_z_tauDepl) and [6.2](#Section_Results_z_deltaGas) as well as Figs. [\[Plot_z_tauDepl_comparison\]](#Plot_z_tauDepl_comparison) and [11](#Plot_z_deltaGas_comparison)), the results are promising to build a most comprehensive picture of gas evolution.

- The integration of galaxies’ stellar mass function with the application of gas fraction scaling relation involves many assumptions. Noticeable differences are found between the simpler assumption that all star-forming galaxies exactly follow the main sequence (Fig. [12](#Plot_cosmic_evolution_of_rho_molgas_with_data)) and the more realistic 2-SFM galaxy modeling (Fig. [13](#Plot_cosmic_evolution_of_rho_molgas_via_galaxy_model)) which accounts for the starburst/main-sequence dichotomy and uses different stellar mass functions than in this work (Appx. [12](#Section_Appendix_SMF_CSFRD)). The realistic galaxy modeling has a better agreement with semi analytic models ((cite: Popping2014; Popping2019)). Among the three functional forms discussed in this work, only our new functional form (Eq. [\[Equation_tauDepl_deltaGas\]](#Equation_tauDepl_deltaGas)) of the gas fraction scaling relation could achieve such a high consistency.

- Compared to CO blind deep field surveys, our analytically-derived cold molecular gas mass densities agree within their upper boundary. This is understandable as the current CO surveys usually could not sample well enough the faint-end of the CO line luminosity function, thus the integration of CO luminosity functions is usually down to only $\log_{10} (L^{\prime}_{\mathrm{CO}}/[\mathrm{K\,km\,s^{-1}\,pc^2}])\sim 9.5$ (to avoid extrapolating the faint-end; see e.g., (cite: Riechers2019); (cite: Decarli2019)).

- Finally, our large, robust dataset strongly supports a coherent picture of the evolution galaxies’ gas, stellar and SFR which can be parameterized by the main sequence functions (e.g., (cite: Speagle2014); Leslie et al. submitted; Appx. [9.5](#Section_MS)), stellar mass functions (e.g., (cite: Davidzon2017); Appx. [12](#Section_Appendix_SMF_CSFRD)) and gas scaling functions (Eq. [\[Equation_tauDepl_deltaGas\]](#Equation_tauDepl_deltaGas)). The integration of stellar mass function times the main sequence function (over stellar mass at each redshift) gives the cosmic SFR density, and the integration of stellar mass function times the molecular gas fraction function (over stellar mass at each redshift) results in the cosmic molecular gas mass density. Integrating the cosmic SFR density curve (across cosmic time) further leads to the cosmic stellar mass density growth curve, which in return is consistent with the integration of stellar mass functions across cosmic time.

# Acknowledgments

DL, ES and PL acknowledge funding from the European Research Council (ERC) under the European Union’s Horizon 2020 research and innovation programme (grant agreement No. 694343). B.M., E.F.J.A. and F.B. acknowledge support of the Collaborative Research Center 956, subproject A1 and C4, funded by the Deutsche Forschungsgemeinschaft (DFG) – project ID 184018867. SL acknowledges funding from Deutsche Forschungsgemeinschaft (DFG) Grant SCH 536/9-1. D.R. acknowledges support from the National Science Foundation under grant numbers AST-1614213 and AST-1910107 and from the Alexander von Humboldt Foundation through a Humboldt Research Fellowship for Experienced Researchers. GEM acknowledges support from the Villum Fonden research grant 13160 “Gas to stars, stars to dust: tracing star formation across cosmic time”, the Cosmic Dawn Center of Excellence funded by the Danish National Research Foundation and the ERC Consolidator Grant funding scheme (project ConTExt, grant number No. 648179). YG’s research is supported by National Key Basic Research and Development Program of China (grant No. 2017YFA0402704), National Natural Science Foundation of China (grant Nos. 11861131007, 11420101002), and Chinese Academy of Sciences Key Research Program of Frontier Sciences (grant No. QYZDJSSW-SLH008). We thank the anonymous referee for constructive comments. We thank Matthieu Béthermin for a very helpful discussion on galaxy modeling.

This paper makes use of the following ALMA data: , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , . ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ.

ALMA

|  |  |  |  |  |
|:---|:--:|:--:|:--:|:--:|
| $\log_{10} ( \mu_{\mathrm{molgas}})$ | $\mathsf{a}$ ($+ \mathsf{ak}$) | $\mathsf{b}$ | $\mathsf{c}$ ($+ \mathsf{ck}$) | $\mathsf{d}$ |
| $(\equiv \log_{10} (M_{\mathrm{mol\,gas}}/ M_{\star}))$ | ($\Delta{\mathrm{MS}}$) | ($\log_{10} M_{\star,10}$)$^{\dagger}$ | ($\log_{10} (1+z)$ or $t$) | (norm.) |
| 2-5 |  |  |  |  |
| This work, Eq. [\[Equation_tauDepl_deltaGas\]](#Equation_tauDepl_deltaGas) | $+0.4195+0.1195{\times}\log_{10}M_{\star,10}$ | $-0.6907$ | $(-0.1543+0.0320{\times}\log_{10}M_{\star,10}){\times}t$ | $+0.9339$ |
| This work, Eq. [\[Equation_Tacconi2018\]](#Equation_Tacconi2018) | $+0.54$ | $-0.39$ | $-4.42{\times}(\log_{10}(1+z)-0.58)^{2}$ | $+0.309$ |
| best-fit, Eq. [\[Equation_Tacconi2018\]](#Equation_Tacconi2018) | $+0.53$ | $-0.35$ | $-3.62{\times}(\log_{10}(1+z)-0.66)^{2}$ | $+0.365$ |
| best-fit, Eq. [\[Equation_Tacconi2018\]](#Equation_Tacconi2018) | $+0.53$ | $-0.35$ | $-3.62{\times}(\log_{10}(1+z)-0.66)^{2}$ | $+0.120$ |
| This work, Eq. [\[Equation_Scoville2017\]](#Equation_Scoville2017) | $+0.57$ | $-0.28$ | $+2.27{\times}\log_{10}(1+z)$ | $-1.106$ |
| best-fit, Eq. [\[Equation_Scoville2017\]](#Equation_Scoville2017) | $+0.32$ | $-0.70$ | $+1.84{\times}\log_{10}(1+z)$ | $-0.149$ |
| $\log_{10} (\tau_{\mathrm{depl}}/ \mathrm{[Gyr]})$ |  |  |  |  |
| $(\equiv \log_{10} (M_{\mathrm{mol\,gas}}/ \mathrm{SFR}))$ |  |  |  |  |
| 2-5 |  |  |  |  |
| This work, Eq. [\[Equation_tauDepl_deltaGas\]](#Equation_tauDepl_deltaGas) | $-0.5724+0.1120{\times}\log_{10}M_{\star,10}$ | $-0.5174$ | $(-0.0030+0.0568{\times}\log_{10}M_{\star,10}){\times}t$ | $+0.0269$ |
| This work, Eq. [\[Equation_Tacconi2018\]](#Equation_Tacconi2018) | $-0.40$ | $+0.08$ | $-0.91{\times}\log_{10}(1+z)$ | $+0.022$ |
| best-fit, Eq. [\[Equation_Tacconi2018\]](#Equation_Tacconi2018) | $-0.44$ | $+0.09$ | $-0.62{\times}\log_{10}(1+z)$ | $+0.027$ |
| This work, Eq. [\[Equation_Scoville2017\]](#Equation_Scoville2017) | $-0.39$ | $+0.08$ | $-0.91{\times}\log_{10}(1+z)$ | $+0.021$ |
| best-fit, Eq. [\[Equation_Scoville2017\]](#Equation_Scoville2017) | $-0.70$ | $-0.01$ | $-1.04{\times}\log_{10}(1+z)$ | $+0.509$ |

$^{\dagger}$ $\log_{10} M_{\star,10}$ represents $\log_{10} (M_{\star}/10^{10}\,\mathrm{M_{\odot}})$.\

+-----------------------------------------------------------------------------+----------------------------------------------+-----------------------------------------------+-----------------------------------------------+
| Fitting Function                                                            | All data points                              | Without $z>4$ data                            | Without $z>1$ CO                              |
+:============================================================================+:======+:=========+:==========================+:=======+:=========+:==========================+:=======+:=========+:==========================+
| 2-4                                                                         | $N$   | $\chi^2$ | $\chi^2_{\mathrm{redu.}}$ | $N$    | $\chi^2$ | $\chi^2_{\mathrm{redu.}}$ | $N$    | $\chi^2$ | $\chi^2_{\mathrm{redu.}}$ |
|                                                                             |       |          |                           |        |          |                           |        |          |                           |
| (For $\mu_{\mathrm{molgas}}$)                                               |       |          |                           |        |          |                           |        |          |                           |
+-----------------------------------------------------------------------------+-------+----------+---------------------------+--------+----------+---------------------------+--------+----------+---------------------------+
| Eq. [\[Equation_tauDepl_deltaGas\]](#Equation_tauDepl_deltaGas) (This work) | 1663  | 1426.98  | 0.86                      | 1617   | 1390.16  | 0.86                      | 1554   | 1349.56  | 0.87                      |
+-----------------------------------------------------------------------------+-------+----------+---------------------------+--------+----------+---------------------------+--------+----------+---------------------------+
| Eq. [\[Equation_Tacconi2018\]](#Equation_Tacconi2018) (This work)           | 1663  | 1444.83  | 0.87                      | 1617   | 1404.74  | 0.87                      | 1554   | 1369.32  | 0.88                      |
+-----------------------------------------------------------------------------+-------+----------+---------------------------+--------+----------+---------------------------+--------+----------+---------------------------+
| Eq. [\[Equation_Tacconi2018\]](#Equation_Tacconi2018) (’s fit)              | 1663  | 1503.94  | 0.91                      | 1617   | 1478.11  | 0.92                      | 1554   | 1427.91  | 0.92                      |
+-----------------------------------------------------------------------------+-------+----------+---------------------------+--------+----------+---------------------------+--------+----------+---------------------------+
| Eq. [\[Equation_Scoville2017\]](#Equation_Scoville2017) (This work)         | 1663  | 2086.55  | 1.26                      | 1617   | 1863.42  | 1.16                      | 1554   | 1921.61  | 1.24                      |
+-----------------------------------------------------------------------------+-------+----------+---------------------------+--------+----------+---------------------------+--------+----------+---------------------------+
| Eq. [\[Equation_Scoville2017\]](#Equation_Scoville2017) (’s fit)            | 1663  | 10230.35 | 6.17                      | 1617   | 10029.8  | 6.22                      | 1554   | 10141.08 | 6.54                      |
+-----------------------------------------------------------------------------+-------+----------+---------------------------+--------+----------+---------------------------+--------+----------+---------------------------+

# Empirical Galaxy Scaling Relations Used in This Work

Scaling relations describe how galaxy properties correlate with each other and are important for understanding galaxy populations and their evolution over cosmic time. As this work studies the molecular gas evolution in galaxies, the four scaling relations below are relevant and sometimes needed for our analysis. Calibrations of these correlations are widely studied in the literature, however, their validity for different types of galaxies (i.e., different $z$, $M_{\star}$ and SFR) are rarely studied. Here we compare a number of empirical calibrations and discuss their biases. This comparison guides our choice of the most suitable correlations to use in the analysis described in the main body of the paper.

## CO-to-H$_2$ conversion factor ($\alpha_{\mathrm{CO}}$) versus metallicity

The CO-to-H$_2$ conversion factor, $\alpha_{\mathrm{CO}}$, is an empirical ratio converting CO line luminosity to total molecular gas mass. It has been found to be relatively constant in the inner Galactic Giant Molecular Clouds (GMCs), being around $4.6 \; \mathrm{\mathrm{M}_{\odot}\, (K\,km\,s^{-1}\,pc^{2})^{-1}}$ ($X_{\mathrm{CO}} = 2.1 \times 10^{20} \; \mathrm{cm^{-2}\,(K\,km\,s^{-1}\,pc^2)^{-1}}$) ((cite: Solomon1987); (cite: Solomon1991); (cite: Solomon2005)), or $6.5 \; \mathrm{\mathrm{M}_{\odot}\, (K\,km\,s^{-1}\,pc^2)^{-1}}$ ($X_{\mathrm{CO}} = 3.0 \times 10^{20} \; \mathrm{cm^{-2}\,(K\,km\,s^{-1}\,pc^2)^{-1}}$) when including heavy elements which are mostly helium. While it is as low as $0.8 \; \mathrm{\mathrm{M}_{\odot}\, (K\,km\,s^{-1}\,pc^{2})^{-1}}$ ($X_{\mathrm{CO}} = 2.0 \times 10^{20} \; \mathrm{cm^{-2}\,(K\,km\,s^{-1}\,pc^2)^{-1}}$; $\pm0.5\,\mathrm{dex}$) in local ULIRGs ((cite: Solomon1997); (cite: Downes1998); (cite: Solomon2005)). The calibration of $\alpha_{\mathrm{CO}}$ relies on a number of other (molecular) gas mass tracers, including virial mass, optically-thin CO isotopologues, dust extinction, dust emission (via the gas-to-dust ratio, e.g., Sect. [9.2](#Section_ZGDR)), and diffuse $\gamma$-ray radiation. More details are given in the recent review by (cite: Bolatto2013ARAA). In this work, we only focus on the established $\alpha_{\mathrm{CO}}$–metallicity relations presented in (cite: Genzel2015) and , as shown in the left panel of Fig. [14](#Plot_metalZ_deltaGD), to homogenize the molecular gas mass calculation for our complementary samples.

![image](Plot_metalZ_alphaCO) ![image](Plot_metalZ_deltaGD)

## Gas-to-dust ratio ($\delta_{\mathrm{GDR}}$) versus metallicity

The gas-to-dust mass ratio, $\delta_{\mathrm{GDR}}\equiv M_{\mathrm{total\,gas}}\, / \, M_{\mathrm{dust}}$, describes the correlation between the total amount of gas (molecular plus atomic, compositing almost all of the ISM) and dust. As dust grains are usually assumed to be well-mixed within the ISM, $\delta_{\mathrm{GDR}}$ should be predictable by ISM chemical models (e.g., see recent review by (cite: Galliano2018ARAA)). We will skip the physical mechanism behind this and refer the reader to (cite: Galliano2018ARAA). Here we aim at understanding how $\delta_{\mathrm{GDR}}$ can be applied for molecular gas mass estimation for high-redshift galaxies.

The calibration of $\delta_{\mathrm{GDR}}$ is usually based on observations of CO and H i emission lines plus multi-wavelength photometry to which SED fitting is performed (e.g., (cite: Leroy2011GDR); (cite: Sandstrom2013); (cite: RemyRuyer2014); (cite: Lisenfeld2000); (cite: Magdis2011SED); (cite: Tan2014)). These works found that $\delta_{\mathrm{GDR}}$ is correlated with galaxies’ gas phase metallicity, as illustrated by data from our sample compilation (see Tab. [\[Table_galaxy_samples\]](#Table_galaxy_samples)) in Fig. [14](#Plot_metalZ_deltaGD) (*right panel*). $\delta_{\mathrm{GDR}}$ is around 100 for galaxies with solar- and super-solar-metallicity, while it increases non-linearly toward lower metallicity, reaching over 1000 in extremely metal-poor ($<10\%\,Z_{\odot}$) galaxies (e.g., (cite: Elmegreen2013); (cite: Shi2014; Shi2016)). The difference between the derived relations of (cite: Leroy2011GDR) and (cite: RemyRuyer2014) is about 0.1 dex in the super-solar metallicity regime, increases to 0.2 dex at 0.2 solar metallicity, and then quickly becomes much larger at even lower metallicity.

As $\delta_{\mathrm{GDR}}$ is calibrated with total gas mass instead of molecular gas mass, a molecular-to-total gas mass ratio, $f_{\mathrm{mol\,frac}}\equiv M_{\mathrm{mol\,gas}}/M_{\mathrm{total\,gas}}$, needs to be considered. It is discussed in the next section (Appx. [9.3](#Section_ZFMOL)).

![image](Plot_metalZ_molecular2atomic) ![image](Plot_Mstar_molecular2atomic)

## Molecular hydrogen fraction ($f_{\mathrm{mol\,frac}}$) versus metallicity

The molecular hydrogen fraction, $f_{\mathrm{mol\,frac}}\equiv M_{\mathrm{mol\,gas}}/M_{\mathrm{total\,gas}}$, is the ratio between molecular gas and molecular+atomic gas. In the following, we use $\mu_{\mathrm{mol\,frac}}\equiv M_{\mathrm{mol\,gas}}/M_{\mathrm{atomic\,gas}}$ for the molecular-to-atomic gas mass ratio.

$f_{\mathrm{mol\,frac}}$ (or $\mu_{\mathrm{mol\,frac}}$) also correlates with metallicity, e.g., the amount of dust grains, as Hydrogen molecules form mainly on the surface of dust grains (e.g., (cite: Hollenbach1971)), and the abundance of dust grains depends on the metal enrichment by recent star formation activities (e.g., (cite: Draine2003ARAA)). The correlations between $f_{\mathrm{mol\,frac}}$ and $12+\log_{10}(\mathrm{O/H})$ and $M_{\star}$ are illustrated in Fig. [15](#Plot_metalZ_molecular2atomic), where theoretical models from (cite: KMT09), (cite: Popping2014) and (cite: Dave2016) are compared to the data.

In Fig. [15](#Plot_metalZ_molecular2atomic), we show $\mu_{\mathrm{mol\,frac}}$ versus metallicity and stellar mass with a large compilation of 524 galaxies from the literature (see labels and figure caption). All galaxies have $M_{\mathrm{mol\,gas}}$ from CO observations, $M_{\mathrm{atomic\,gas}}$ from Hi observations, $12+\log_{10}(\mathrm{O/H})$ from optical spectroscopy and $M_{\star}$ from multi-wavelength optical/near-infrared data. The data points exhibit a large scatter in both panels, which is probably caused by the uncertainties in $M_{\mathrm{mol\,gas}}$, $M_{\mathrm{atomic\,gas}}$ and metallicity. The metallicity-dependent CO-to-H$_2$ conversion factor has on average a $\sim38\%$ uncertainty in the (cite: Saintonge2017) catalog, where the conversion factor is computed based on (cite: Accurso2017), and the observed CO line flux has a $\sim5-30\%$ uncertainty. Hi line flux has a $\sim2-20\%$ uncertainty in their catalog, and in addition the conversion from Hi line flux to $M_{\mathrm{atomic\,gas}}$ may have a $30\%$ or higher uncertainty due to the assumption of optically thin Hi (e.g., (cite: Fukui2018)). These uncertainties add up in total to at least $\sim50-60\%$ uncertainty for the Y-axis.

Three theoretical models from (cite: Popping2014), (cite: Dave2016) and (cite: KMT09) are overlaid as colored lines. Comparing with the data, the (cite: KMT09) model provides the best fit at the low-metallicity end. While at high metallicities, it seems the data is not statistically meaningful and all three models provide reasonable predictions.

The figure shows that for local galaxies with solar-abundant metallicity and $M_{\star}>10^{10}\;\mathrm{M}_{\odot}$, molecular gas nearly dominates the total gas mass ($\left<{f_{\mathrm{mol\,frac}}}\right> > 50\%$). At higher redshifts, however, there is no observational constraint. We can only assume such scaling relations are still valid at higher redshifts. In principle, higher-redshift galaxies have higher SFRs and gas density at the same stellar mass (see Appx. [9.5](#Section_MS)), $f_{\mathrm{mol\,frac}}$ should be at least as high as those of similar stellar mass and metallicity local analogs. Thus it is common to ignore the atomic gas contribution in high-redshift galaxies with $M_{\star}>10^{10}\;\mathrm{M}_{\odot}$ (e.g., ).

## Mass metallicity relation (MZR)

The Fundamental Metallicity Relation (FMR; the correlation between metallicity, stellar mass and SFR; (cite: Mannucci2010; Mannucci2011)) and Mass-Metallicity Relation (MZR; the correlation between metallicity and stellar mass; e.g., (cite: Kewley2008)) are usually used to infer the metallicity and metallicity-related properties (e.g., $\alpha_{\mathrm{CO}}$, $\delta_{\mathrm{GDR}}$) of high-redshift galaxies when no sufficient optical nebular emission line information is available. A number of FMR and MZRs exist in the literature (see below), with metallicity ($12+\log_{10} (\mathrm{O/H})$) parameterized as a function of $M_{\star}$ and/or $z$ or SFR. However, whether the FMR and MZRs are valid across cosmic time or within a given stellar mass range is less studied.

![image]({Plot_metalZ_Mstar_SFR_z0.07}.pdf) ![image]({Plot_metalZ_Mstar_SFR_z0.8}.pdf) ![image]({Plot_metalZ_Mstar_SFR_z1.6}.pdf) ![image]({Plot_metalZ_Mstar_SFR_z1.9}.pdf) ![image]({Plot_metalZ_Mstar_SFR_z2.3}.pdf) ![image]({Plot_metalZ_Mstar_SFR_z5}.pdf) ![image]({Plot_metalZ_Mstar_SFR_z1.9_starburst}.pdf) ![image]({Plot_metalZ_Mstar_SFR_z2.3_starburst}.pdf) ![image]({Plot_metalZ_Mstar_SFR_z5_starburst}.pdf)

Here we take the following seven most widely used FMR and MZRs for high-redshift studies and compared them in Fig. [16](#Plot_metalZ_Mstar_SFR_z_bins) so that their validities can be more clearly seen in bins of redshift:

- (cite: Mannucci2010) presented their FMR in their Eqs. 2 and 4 for local galaxies. Their metallicity values are originally calibrated from optical emission lines following the (cite: Maiolino2008) prescription instead of (cite: PP04) therefore we converted their derived metallicity to the PP04 calibration by solving both (cite: Mannucci2010) Eq. 1 (the polynomial form, instead of their Eq. 2) and (cite: Maiolino2008) Eq. 1 (with their Table 4’s second row coefficients). Both their Eqs. 2 and 4 are shown in Fig. [16](#Plot_metalZ_Mstar_SFR_z_bins). The caveat of their Eq. 2 includes that: (a) at a given redshift and SFR, it first increases with stellar mass then drops quickly when $\log_{10} M_{\star}>11.2$; and (b) it predicts the lowest metallicity for starburst galaxies at $z>1$. And the caveat of their Eq. 4 is the nonphysical extrapolation for (a) main-sequence galaxies at all redshift with $\log_{10} M_{\star}>11.2$; and (b) $z\gtrsim1$ main-sequence galaxies with $\log_{10} M_{\star}<9.5$.

- (cite: Mannucci2011) provided an updated version of their FMR in (cite: Mannucci2010) for lower-mass galaxies. The update is only for $\log_{10} M_{\star}- 0.32 \times \log_{10}\mathrm{SFR} < 9.5$ case, i.e., low mass and/or high SFR. Therefore we show this equation only in the bottom panels for starburst galaxies. Note that there is a nonphysical jump in metallicity at $\log_{10} M_{\star}\sim10.2-10.5$.

- (cite: Genzel2015) Eq.(12a) is originally from (cite: Wuyts2014) and also adopted by in the identical form. This formula considers both redshift and stellar mass as the parameters determining metallicity. It predicts reasonable metallicities except at $\log_{10} M_{\star}\gtrsim11$ at local (or $\log_{10} M_{\star}\gtrsim11.5-12$ at $z\gtrsim1$). This motivates our modification of this equation as described in Eq. [\[Equation_metallicity\]](#Equation_metallicity).

- (cite: Genzel2015) Eq.(12b) is based on (cite: Mannucci2010)’s Eq. 4, with a M08-to-PP04 conversion applied by solving both (cite: Mannucci2010) Eq. 2 and (cite: Maiolino2008) Eq. 1 (see their Table 4’s second row coefficients). Therefore the curve of this equation is very similar to the (cite: Mannucci2010) Eq. 4 curve, yet we caution that the M08-to-PP04 conversion is different in their work than here, and our conversion (by solving (cite: Mannucci2010) Eq. 2 and (cite: Maiolino2008) Eq. 1) should be more precise.

- (cite: Magnelli2012) Eq. 5 uses the (cite: Denicolo2002) calibration. Thus we convert this calibration to the PP04 N2 calibration following (cite: Kewley2008). They assumed two different MZRs distinguished by redshift at 1.5. We caution that it is much lower at low-redshift ($z\lesssim1$). It also always predicts sub-solar metallicity for galaxies at $z>1$.

- (cite: Kewley2008) PP04 O3N2 and N2 MZRs as listed in their Table 2 [^10]. Their equation only depends on stellar mass and has no redshift evolution, therefore we only show their curve in the first panel. It predicts too high metallicity for high-redshift galaxies with $\log_{10} M_{\star}<10.5$, and like (cite: Mannucci2010) Eq. 2, it also has a nonphysical drop with increasing stellar mass when $\log_{10} M_{\star}>11.2$.

- (cite: Maiolino2008) Eq. 2 with the coefficients listed in their Table 5. They fitted five different MZRs at five redshifts they analyzed. Here we linearly interpolate their coefficients in redshift so as to plot their curves in Fig. [16](#Plot_metalZ_Mstar_SFR_z_bins). The equation seems reasonable at low-$z$ ($z<2-3$) but predicts significantly sub-solar metallicity at $z\gtrsim5$ even for starbursts.

Fig. [16](#Plot_metalZ_Mstar_SFR_z_bins) shows that most of these formulae are consistent (within 0.2 dex) only for main-sequence galaxies at $z\lesssim2$ and with $\log_{10} M_{\star}\sim10-11.2$. Subtle differences exist among these curves and the reader should consider the proper choice of MZR or FMR to use. A small difference, e.g., a 0.1 dex lower/higher metallicity, could translate into a factor of 1.6 higher/lower $\delta_{\mathrm{GDR}}$ when assuming the $\delta_{\mathrm{GDR}}$–metallicity relation in Fig. [14](#Plot_metalZ_deltaGD). Also note that the prescription for deriving $12+\log_{10}(\mathrm{O/H})$ from optical emission lines is important, as can be seen by comparing the first and third formulae at the high-mass end. Finally, we caution that these formulae do not agree well at the low-mass regime ($M_{\star}< 10^{10.0} \; \mathrm{M}_{\odot}$). But for the study in this work, although with such a large ALMA sample, we still do not probe such low-mass galaxies. Therefore these discrepancies are currently not an issue.

## Stellar mass–SFR main sequence (MS)

In Sect. [5](#Section_Fitting_Multi_Variate_Function) we mentioned that we adopt the (cite: Speagle2014) MS (the #49 fitting in their Table 7) with cosmic time as the variable. In Fig. [17](#Plot_SF_MS_bin_by_lgMstar_horizontal) we compare a number of MS relations in the literature (see the labels therein). The (cite: Whitaker2014), (cite: Lee2015) and (cite: Tomczak2016) MS are only valid at $z \lesssim 3$. The (cite: Sargent2014) MS predicts the lowest $\mathrm{sSFR_{MS}}$ at $z > 5$, while the (cite: Bethermin2015) MS predicts a factor of 2 higher $\mathrm{sSFR_{MS}}$ than average at $z > 5$ and is in general higher for $\log_{10} M_{\star}> 10^{11}$ galaxies. The (cite: Pearson2018) MS is a factor of $<2$ lower than others at $z\sim2-3$ and in general lower for $\log_{10} M_{\star}< 10^{10}$ galaxies. These MS calibrations have large scatter in the $\log_{10} M_{\star}< 10^{9}$ and $\log_{10} M_{\star}\gtrsim 10^{12}$ regimes which lack observational data. The (cite: Speagle2014) MS (with cosmic age) is closer to the average of all MS analyzed, therefore we adopt it for our work.

The Leslie et al. (subm.) MS is potentially an alternative choice for a most reasonable MS to use. They derived the MS correlation from redshift $\sim0.2$ to $\sim6$ by stacking the VLA 3GHz large program data ((cite: Smolcic2017a); covering 2 sq. deg. COSMOS field with a sensitivity of $1\,\sigma\sim2.3\,\mu\mathrm{Jy}/\mathrm{beam}$ at a spatial resolution of 0.75”) using a large sample of $\sim300,000$ galaxies from the (cite: Laigle2016) and (cite: Davidzon2017) catalogs. The largest difference between the Leslie et al. MS and the (cite: Speagle2014) one is that the former exhibits a flattening for a higher stellar mass, while the latter is a straight line at each redshift. Such a flattening, yet debated, has also been reported by other stacking studies (e.g., (cite: Schreiber2015); (cite: Lee2015); (cite: Tomczak2016)). We refer the reader to these papers and Leslie et al. (subm.) for details on the shapes of different MS functions. Here we investigate how an MS with flattening affects our functional form by adopting the Leslie et al. MS and repeating our analysis from Sects. [5](#Section_Fitting_Multi_Variate_Function) to [6.2](#Section_Results_z_deltaGas). In Fig. [18](#Plot_z_deltaGas_comparison_with_Leslie2019_MS), we compare the obtained $\mu_{\mathrm{molgas}}$ evolution curves using the Leslie et al. MS to those using the (cite: Speagle2014) MS.

Fig. [18](#Plot_z_deltaGas_comparison_with_Leslie2019_MS) shows that adopting the Leslie et al. MS results in an at most factor of two higher gas fraction for low-mass, high-redshift galaxies ($\log_{10} M_{\star}\lesssim9.2$, $z\sim2-6$), while being indistinguishable from using the (cite: Speagle2014) MS for galaxies with $\log_{10} M_{\star}\gtrsim10-11$. The difference at the low-mass end is likely because the Leslie et al. MS predicts two times higher sSFRs for low-mass galaxies at $z\sim0$ while a factor of two lower sSFR at $z\sim3$, as shown in the left panel of Fig. [17](#Plot_SF_MS_bin_by_lgMstar_horizontal). This leads to a systematically lower $\Delta{\mathrm{MS}}$ for low-mass galaxies at $z\sim0$, altering the slope of $\mu_{\mathrm{molgas}}$ versus $\Delta{\mathrm{MS}}$ to be shallower (by a small change of 0.04 in the coefficient $\mathsf{a}$ in Eq. [\[Equation_tauDepl_deltaGas\]](#Equation_tauDepl_deltaGas)), meanwhile steepening the slope of $\mu_{\mathrm{molgas}}$ versus $\log_{10} M_{\star}$ (by a change of 0.14 in the coefficient $\mathsf{b}$ in Eq. [\[Equation_tauDepl_deltaGas\]](#Equation_tauDepl_deltaGas)). Thus it results in a $<2\times$ higher extrapolation for the gas fraction at the low-mass end. We note that the fits are indistinguishable where data are rich, i.e., using either Leslie et al. or (cite: Speagle2014) MS makes no obvious difference for $\log_{10} M_{\star}\gtrsim10-11$ galaxies at all redshifts ($z\sim0-6$).

In Fig. [17](#Plot_SF_MS_bin_by_lgMstar_horizontal), we additionally show the MS relations used in following the equations in their Sects. 2.1 and 2.2. Although their equation is not aimed for extrapolating out to $z>3-4$ (and exhibits a large excess compared to others), here we show their curve and use their MS to compute $\Delta{\mathrm{MS}}$ for our data out to $z\sim6$ for the sole purpose of evaluating the validity of their MS at these redshifts. In Fig. [18](#Plot_z_deltaGas_comparison_with_Leslie2019_MS) we also repeated the fitting with our Eq. [\[Equation_tauDepl_deltaGas\]](#Equation_tauDepl_deltaGas) functional form and used the MS for $\Delta{\mathrm{MS}}$ normalization. The implied gas fraction evolution curve is $\sim2\times$ ($\sim4\times$) higher than that using the Leslie et al. MS ((cite: Speagle2014) MS) at the low-mass end, meanwhile it also exhibits a $\sim2.5\times$ lower gas fraction at the massive end. This means that the difference in MS can indeed explain about half of the difference between our and molecular gas mass density curves seen in Fig. [11](#Plot_z_deltaGas_comparison) (the shape of the functional form is likely responsible for the other half of the difference).

![](Plot_SF_MS_bin_by_lgMstar_horizontal)

![](Plot_z_deltaGas_comparison_with_Leslie2019_MS)

# Biases in Band Conversion with MAGPHYS SED Fitting

To verify the potential bias in using MAGPHYS SED fitting to predict the rest-frame RJ-tail (i.e., 850 $\mu$m) dust continuum, we have done some tests using the multi-wavelength data from UV to submm for the JINGLE survey galaxy sample ((cite: Saintonge2018); (cite: Smith2019)). JINGLE galaxies are main-sequence star-forming galaxies in the local Universe ($z<0.05$) with well-sampled SEDs including: JCMT/SCUBA2 850 $\mu$m ((cite: Smith2019)), *Herschel* 70–500 $\mu$m ((cite: Pilbratt2010); (cite: Poglitsch2010); (cite: Griffin2010)), *Spitzer* 3.6–24 $\mu$m ((cite: Werner2004)), *WISE* 3.4–22 $\mu$m ((cite: Wright2010)), VISTA 1.2–2.2 $\mu$m (Sutherland et al. 2015), 2MASS $J$, $H$ and $K$ (Skrutskie et al. 2006), SDSS optical (York et al. 2000; Eisenstein et al. 2011) and GALEX UV (Morrissey et al. 2007).

We run the following MAGPHYS fitting tests: (a) fitting all data points at $\lambda \le 250\,\mu\mathrm{m}$, mimicking the $\lambda_{\mathrm{rest}} \le 250 \,\mu\mathrm{m}$ cases in Fig. [2](#Plot_rest_frame_wavelength_vs_redshift) in the main text; (b) fitting all $\lambda < 8\,\mu\mathrm{m}$ photometry data points plus only one $\lambda = 160\,\mu\mathrm{m}$ data point, mimicking the cases where we have only one ALMA data point for fitting the whole dust SED (see Fig. [2](#Plot_rest_frame_wavelength_vs_redshift)).

We compare the SED-predicted 850 $\mu$m fluxes from both tests to the true observed 850 $\mu$m fluxes in Fig. [19](#Plot_rest_frame_SED_flux_difference_no_250um) (left and right panels, respectively). As also mentioned in Sect. [3.2.1](#Section_Band_conversion), the SED-predicted fluxes tend to be lower than the true fluxes, and the accuracy of predicting 850 $\mu$m flux seems to depend on the $\mathrm{S/N}$ of all data points fitted for the dust component SED. When dust SED data points have a $\mathrm{S/N}\sim20$, the rest-frame 850 $\mu$m fluxes tend to be underestimated by $\sim$0.5 dex. If $\mathrm{S/N}>30$, it seems some galaxies have no bias while some still are under-predicted. For $\mathrm{S/N}<20$, the 850 $\mu$m fluxes are significantly underestimated by $0.3-0.8\,$dex.

![image](Plot_rest_frame_SED_flux_difference_no_350um_NEW) ![image](Plot_rest_frame_SED_flux_difference_no_dust_except_for_160um_NEW)

# Markov chain Monte Carlo (MCMC) fitting

Fig. [20](#Plot_pymc3_corner_a3cosmos_function) shows the probability distributions of the coefficients in Eq. [\[Equation_tauDepl_deltaGas\]](#Equation_tauDepl_deltaGas) obtained from our MCMC fitting in Sect. [5](#Section_Fitting_Multi_Variate_Function). In the fitting we allow the coefficients to vary within a relatively large range of $(-10,10)$. The probability distribution of each coefficient is shown to include the most probably areas as automatically determined by the

`Python`

package

`corner`

. All coefficients have a clear peak in their probability distribution with a small width (uncertainty) of about 10%. The $\tau_{\mathrm{depl}}$ function’s coefficients seem to have some second peaks which are probably due to the non-uniform, complicated sample biases (see Sect. [2](#Section_Sample_and_Data)). The overall constraint of our fitting (to Eq. [\[Equation_tauDepl_deltaGas\]](#Equation_tauDepl_deltaGas) and other fittings) is tight.

![image](Plot_pymc3_corner_a3cosmos_function_tauDepl) ![image](Plot_pymc3_corner_a3cosmos_function_deltaGas)

# Stellar mass function (SMF)

The galaxies’ stellar mass function (SMF) at each redshift should in principle be consistent with the evolution of the cosmic SFR density (CSFRD). As mentioned in Sect. [7.1](#Section_Adopting_the_SMFs), at a given cosmic time, the integration of the CSFRD over previous cosmic times should be equal to the integration of the SMF at that cosmic time over all stellar masses. Note that the SMF is usually divided into two galaxy types: star-forming galaxies (SFGs) and quiescent galaxies (QGs), and the integration of the SMF should be the sum of both SFGs and QGs.

Therefore we adopt SMFs for this work by adjusting known SMFs according to the integration of the CSFRD. For example at $z<0.085$, we adopt a SMF with the shape same as the SMF from (cite: PengYingJie2010_SMF), for both SFG and QG types, and with the normalization of SFG+QG adjusted to the CSFRD-integrated total stellar mass at that redshift, while keeping the SFG and QG SMFs’ relative normalization the same as in (cite: PengYingJie2010_SMF). Similarly at higher redshifts, we adopt the shape of our SMF from an interpolation of the (cite: Davidzon2017) SMFs, as their SMFs are measured over multiple redshift bins ($0.2<z<5.0$). In the cases of $0.085<z<0.2$ and $z>4.0$, we adopt their $z=0.2$ and $z=4.0$ SMF shapes, respectively. The normalization is also adjusted such that SFG+QG SMFs’ integrated total stellar mass equals the CSFRD-integrated total stellar mass.

Note that during the integration of CSFRD over cosmic time, we have considered the loss of mass due to stellar evolution following (cite: Conroy2009). The choice of the mass losing timescale can be different, e.g., (cite: Ilbert2013) adopt 3 Myr and (cite: Behroozi2015) adopt 1.4 Myr. Compared to the (cite: Conroy2009) timescale, adopting 3 Myr would lead to a 0.09 dex higher integrated total stellar mass at $z=0$.

In Fig. [21](#Plot_SMF) we compare our adjusted SMFs with the measured SMFs from (cite: Davidzon2017) and (cite: PengYingJie2010_SMF), which are recent measurements with the deepest data available at high redshift and in the local Universe, respectively. The very good agreement between our SMFs and theirs supports our knowledge of galaxy evolution characterized by SMFs and CSFRD. We also compare the SMFs from (cite: Wright2018_SMF), who compiled a large number of data and performed a function fitting to characterize the evolution of SMF. We show both their single- and double-Schechter function fitting in Fig. [21](#Plot_SMF), however, their SMFs are too high at the massive end, while changing rapidly in shape at $z>6$. This perhaps shows the difficulty in obtaining a best fitting function, and is the reason that we adopt the CSFRD-adjusted SMFs rather than the function-characterized ones.

![image](Plot_SMF_SFG) ![image](Plot_SMF_QG) ![image](Plot_SMF_ALL)

natexlab

(ref: Accurso2017) Accurso, G., Saintonge, A., Catinella, B., et al. 2017, MNRAS, 470, 4750, doi: [`10.1093/mnras/stx1556`](http://doi.org/10.1093/mnras/stx1556)

(ref: Alatalo2013) Alatalo, K., Davis, T. A., Bureau, M., et al. 2013, MNRAS, 432, 1796, doi: [`10.1093/mnras/sts299`](http://doi.org/10.1093/mnras/sts299)

(ref: Andreani2018) Andreani, P., Boselli, A., Ciesla, L., et al. 2018, A&A, 617, A33, doi: [`10.1051/0004-6361/201832873`](http://doi.org/10.1051/0004-6361/201832873)

(ref: Aniano2012) Aniano, G., Draine, B. T., Calzetti, D., et al. 2012, ApJ, 756, 138, doi: [`10.1088/0004-637X/756/2/138`](http://doi.org/10.1088/0004-637X/756/2/138)

(ref: Asplund2009) Asplund, M., Grevesse, N., Sauval, A. J., & Scott, P. 2009, ARA&A, 47, 481, doi: [`10.1146/annurev.astro.46.060407.145222`](http://doi.org/10.1146/annurev.astro.46.060407.145222)

(ref: Baldry2012_SMF) Baldry, I. K., Driver, S. P., Loveday, J., et al. 2012, MNRAS, 421, 621, doi: [`10.1111/j.1365-2966.2012.20340.x`](http://doi.org/10.1111/j.1365-2966.2012.20340.x)

(ref: Battisti2019) Battisti, A. J., da Cunha, E., Grasha, K., et al. 2019, arXiv e-prints, arXiv:1908.00771. [`https://arxiv.org/abs/1908.00771`](https://arxiv.org/abs/1908.00771)

(ref: Bauermeister2013) Bauermeister, A., Blitz, L., Bolatto, A., et al. 2013, ApJ, 763, 64, doi: [`10.1088/0004-637X/763/1/64`](http://doi.org/10.1088/0004-637X/763/1/64)

(ref: Behroozi2015) Behroozi, P. S., & Silk, J. 2015, ApJ, 799, 32, doi: [`10.1088/0004-637X/799/1/32`](http://doi.org/10.1088/0004-637X/799/1/32)

(ref: Berta2016) Berta, S., Lutz, D., Genzel, R., Förster-Schreiber, N. M., & Tacconi, L. J. 2016, A&A, 587, A73, doi: [`10.1051/0004-6361/201527746`](http://doi.org/10.1051/0004-6361/201527746)

(ref: Bertemes2018) Bertemes, C., Wuyts, S., Lutz, D., et al. 2018, MNRAS, 478, 1442, doi: [`10.1093/mnras/sty963`](http://doi.org/10.1093/mnras/sty963)

(ref: Bethermin2012) Béthermin, M., Le Floc’h, E., Ilbert, O., et al. 2012, A&A, 542, A58, doi: [`10.1051/0004-6361/201118698`](http://doi.org/10.1051/0004-6361/201118698)

(ref: Bethermin2015) Béthermin, M., Daddi, E., Magdis, G., et al. 2015, A&A, 573, A113, doi: [`10.1051/0004-6361/201425031`](http://doi.org/10.1051/0004-6361/201425031)

(ref: Bethermin2017Model) Béthermin, M., Wu, H.-Y., Lagache, G., et al. 2017, A&A, 607, A89, doi: [`10.1051/0004-6361/201730866`](http://doi.org/10.1051/0004-6361/201730866)

(ref: Betti2019) Betti, S. K., Pope, A., Scoville, N., et al. 2019, arXiv e-prints. [`https://arxiv.org/abs/1902.08216`](https://arxiv.org/abs/1902.08216)

(ref: Blain2002) Blain, A. W., Smail, I., Ivison, R. J., Kneib, J.-P., & Frayer, D. T. 2002, Phys. Rep., 369, 111, doi: [`10.1016/S0370-1573(02)00134-5`](http://doi.org/10.1016/S0370-1573(02)00134-5)

(ref: Bolatto2013ARAA) Bolatto, A. D., Wolfire, M., & Leroy, A. K. 2013, ARA&A, 51, 207, doi: [`10.1146/annurev-astro-082812-140944`](http://doi.org/10.1146/annurev-astro-082812-140944)

(ref: Bolatto2011) Bolatto, A. D., Leroy, A. K., Jameson, K., et al. 2011, ApJ, 741, 12, doi: [`10.1088/0004-637X/741/1/12`](http://doi.org/10.1088/0004-637X/741/1/12)

(ref: Bourne2013) Bourne, N., Dunne, L., Bendo, G. J., et al. 2013, MNRAS, 436, 479, doi: [`10.1093/mnras/stt1584`](http://doi.org/10.1093/mnras/stt1584)

(ref: Brinchmann2004) Brinchmann, J., Charlot, S., White, S. D. M., et al. 2004, MNRAS, 351, 1151, doi: [`10.1111/j.1365-2966.2004.07881.x`](http://doi.org/10.1111/j.1365-2966.2004.07881.x)

(ref: CaoTianWen2017) Cao, T.-W., Wu, H., Du, W., et al. 2017, AJ, 154, 116, doi: [`10.3847/1538-3881/aa845a`](http://doi.org/10.3847/1538-3881/aa845a)

(ref: Capak2015) Capak, P. L., Carilli, C., Jones, G., et al. 2015, Nature, 522, 455, doi: [`10.1038/nature14500`](http://doi.org/10.1038/nature14500)

(ref: Cappellari2011) Cappellari, M., Emsellem, E., Krajnović, D., et al. 2011, MNRAS, 413, 813, doi: [`10.1111/j.1365-2966.2010.18174.x`](http://doi.org/10.1111/j.1365-2966.2010.18174.x)

(ref: Carilli2013Review) Carilli, C. L., & Walter, F. 2013, ARA&A, 51, 105, doi: [`10.1146/annurev-astro-082812-140953`](http://doi.org/10.1146/annurev-astro-082812-140953)

(ref: Catinella2018) Catinella, B., Saintonge, A., Janowiecki, S., et al. 2018, MNRAS, 476, 875, doi: [`10.1093/mnras/sty089`](http://doi.org/10.1093/mnras/sty089)

(ref: Chabrier2003) Chabrier, G. 2003, PASP, 115, 763, doi: [`10.1086/376392`](http://doi.org/10.1086/376392)

(ref: Cibinel2019) Cibinel, A., Daddi, E., Sargent, M. T., et al. 2019, MNRAS, 485, 5631, doi: [`10.1093/mnras/stz690`](http://doi.org/10.1093/mnras/stz690)

(ref: Cicone2017) Cicone, C., Bothwell, M., Wagg, J., et al. 2017, A&A, 604, A53, doi: [`10.1051/0004-6361/201730605`](http://doi.org/10.1051/0004-6361/201730605)

(ref: Combes2018Review) Combes, F. 2018, A&ARv, 26, 5, doi: [`10.1007/s00159-018-0110-4`](http://doi.org/10.1007/s00159-018-0110-4)

(ref: Combes2013) Combes, F., Garcı́a-Burillo, S., Braine, J., et al. 2013, A&A, 550, A41, doi: [`10.1051/0004-6361/201220392`](http://doi.org/10.1051/0004-6361/201220392)

(ref: Conroy2009) Conroy, C., & Wechsler, R. H. 2009, ApJ, 696, 620, doi: [`10.1088/0004-637X/696/1/620`](http://doi.org/10.1088/0004-637X/696/1/620)

(ref: Coogan2019) Coogan, R. T., Sargent, M. T., Daddi, E., et al. 2019, MNRAS, 485, 2092, doi: [`10.1093/mnras/stz409`](http://doi.org/10.1093/mnras/stz409)

(ref: Cormier2014) Cormier, D., Madden, S. C., Lebouteiller, V., et al. 2014, A&A, 564, A121, doi: [`10.1051/0004-6361/201322096`](http://doi.org/10.1051/0004-6361/201322096)

(ref: Cortzen2019) Cortzen, I., Garrett, J., Magdis, G., et al. 2019, MNRAS, 482, 1618, doi: [`10.1093/mnras/sty2777`](http://doi.org/10.1093/mnras/sty2777)

(ref: Cowie1996) Cowie, L. L., Songaila, A., Hu, E. M., & Cohen, J. G. 1996, AJ, 112, 839, doi: [`10.1086/118058`](http://doi.org/10.1086/118058)

(ref: daCunha2008) da Cunha, E., Charlot, S., & Elbaz, D. 2008, MNRAS, 388, 1595, doi: [`10.1111/j.1365-2966.2008.13535.x`](http://doi.org/10.1111/j.1365-2966.2008.13535.x)

(ref: daCunha2015) da Cunha, E., Walter, F., Smail, I. R., et al. 2015, ApJ, 806, 110, doi: [`10.1088/0004-637X/806/1/110`](http://doi.org/10.1088/0004-637X/806/1/110)

(ref: Daddi2008BzK) Daddi, E., Dannerbauer, H., Elbaz, D., et al. 2008, ApJL, 673, L21, doi: [`10.1086/527377`](http://doi.org/10.1086/527377)

(ref: Daddi2007) Daddi, E., Dickinson, M., Morrison, G., et al. 2007, ApJ, 670, 156, doi: [`10.1086/521818`](http://doi.org/10.1086/521818)

(ref: Daddi2010BzK) Daddi, E., Bournaud, F., Walter, F., et al. 2010a, ApJ, 713, 686, doi: [`10.1088/0004-637X/713/1/686`](http://doi.org/10.1088/0004-637X/713/1/686)

(ref: Daddi2010SFL) Daddi, E., Elbaz, D., Walter, F., et al. 2010b, ApJL, 714, L118, doi: [`10.1088/2041-8205/714/1/L118`](http://doi.org/10.1088/2041-8205/714/1/L118)

(ref: Dale2001) Dale, D. A., Helou, G., Contursi, A., Silbermann, N. A., & Kolhatkar, S. 2001, ApJ, 549, 215, doi: [`10.1086/319077`](http://doi.org/10.1086/319077)

(ref: Dave2016) Davé, R., Thompson, R., & Hopkins, P. F. 2016, MNRAS, 462, 3265, doi: [`10.1093/mnras/stw1862`](http://doi.org/10.1093/mnras/stw1862)

(ref: Davidzon2017) Davidzon, I., Ilbert, O., Laigle, C., et al. 2017, A&A, 605, A70, doi: [`10.1051/0004-6361/201730419`](http://doi.org/10.1051/0004-6361/201730419)

(ref: DeVis2019) De Vis, P., Jones, A., Viaene, S., et al. 2019, A&A, 623, A5, doi: [`10.1051/0004-6361/201834444`](http://doi.org/10.1051/0004-6361/201834444)

(ref: Decarli2016) Decarli, R., Walter, F., Aravena, M., et al. 2016, ApJ, 833, 69, doi: [`10.3847/1538-4357/833/1/69`](http://doi.org/10.3847/1538-4357/833/1/69)

(ref: Decarli2019) Decarli, R., Walter, F., Gónzalez-López, J., et al. 2019, arXiv e-prints. [`https://arxiv.org/abs/1903.09164`](https://arxiv.org/abs/1903.09164)

(ref: Denicolo2002) Denicoló, G., Terlevich, R., & Terlevich, E. 2002, MNRAS, 330, 69, doi: [`10.1046/j.1365-8711.2002.05041.x`](http://doi.org/10.1046/j.1365-8711.2002.05041.x)

(ref: Downes1998) Downes, D., & Solomon, P. M. 1998, ApJ, 507, 615, doi: [`10.1086/306339`](http://doi.org/10.1086/306339)

(ref: Draine2003ARAA) Draine, B. T. 2003, ARA&A, 41, 241, doi: [`10.1146/annurev.astro.41.011802.094840`](http://doi.org/10.1146/annurev.astro.41.011802.094840)

(ref: Draine2007SED) Draine, B. T., & Li, A. 2007, ApJ, 657, 810, doi: [`10.1086/511055`](http://doi.org/10.1086/511055)

(ref: Draine2007SINGS) Draine, B. T., Dale, D. A., Bendo, G., et al. 2007, ApJ, 663, 866, doi: [`10.1086/518306`](http://doi.org/10.1086/518306)

(ref: Elbaz2007) Elbaz, D., Daddi, E., Le Borgne, D., et al. 2007, A&A, 468, 33, doi: [`10.1051/0004-6361:20077525`](http://doi.org/10.1051/0004-6361:20077525)

(ref: Elbaz2018) Elbaz, D., Leiton, R., Nagar, N., et al. 2018, A&A, 616, A110, doi: [`10.1051/0004-6361/201732370`](http://doi.org/10.1051/0004-6361/201732370)

(ref: Elmegreen2013) Elmegreen, B. G., Rubio, M., Hunter, D. A., et al. 2013, Nature, 495, 487, doi: [`10.1038/nature11933`](http://doi.org/10.1038/nature11933)

(ref: Erb2006) Erb, D. K., Shapley, A. E., Pettini, M., et al. 2006, ApJ, 644, 813, doi: [`10.1086/503623`](http://doi.org/10.1086/503623)

(ref: FernandezLorenzo2013) Fernández Lorenzo, M., Sulentic, J., Verdes-Montenegro, L., & Argudo-Fernández, M. 2013, MNRAS, 434, 325, doi: [`10.1093/mnras/stt1020`](http://doi.org/10.1093/mnras/stt1020)

(ref: Fukui2018) Fukui, Y., Hayakawa, T., Inoue, T., et al. 2018, ApJ, 860, 33, doi: [`10.3847/1538-4357/aac16c`](http://doi.org/10.3847/1538-4357/aac16c)

(ref: Galliano2018ARAA) Galliano, F., Galametz, M., & Jones, A. P. 2018, ARA&A, 56, 673, doi: [`10.1146/annurev-astro-081817-051900`](http://doi.org/10.1146/annurev-astro-081817-051900)

(ref: Gao2004b) Gao, Y., & Solomon, P. M. 2004, ApJ, 606, 271, doi: [`10.1086/382999`](http://doi.org/10.1086/382999)

(ref: Genzel2010) Genzel, R., Tacconi, L. J., Gracia-Carpio, J., et al. 2010, MNRAS, 407, 2091, doi: [`10.1111/j.1365-2966.2010.16969.x`](http://doi.org/10.1111/j.1365-2966.2010.16969.x)

(ref: Genzel2015) Genzel, R., Tacconi, L. J., Lutz, D., et al. 2015, ApJ, 800, 20, doi: [`10.1088/0004-637X/800/1/20`](http://doi.org/10.1088/0004-637X/800/1/20)

(ref: Grazian2015) Grazian, A., Fontana, A., Santini, P., et al. 2015, A&A, 575, A96, doi: [`10.1051/0004-6361/201424750`](http://doi.org/10.1051/0004-6361/201424750)

(ref: Griffin2010) Griffin, M. J., Abergel, A., Abreu, A., et al. 2010, A&A, 518, L3, doi: [`10.1051/0004-6361/201014519`](http://doi.org/10.1051/0004-6361/201014519)

(ref: Groves2015) Groves, B. A., Schinnerer, E., Leroy, A., et al. 2015, ApJ, 799, 96, doi: [`10.1088/0004-637X/799/1/96`](http://doi.org/10.1088/0004-637X/799/1/96)

(ref: Hayward2015) Hayward, C. C., & Smith, D. J. B. 2015, MNRAS, 446, 1512, doi: [`10.1093/mnras/stu2195`](http://doi.org/10.1093/mnras/stu2195)

(ref: Hollenbach1971) Hollenbach, D., & Salpeter, E. E. 1971, ApJ, 163, 155, doi: [`10.1086/150754`](http://doi.org/10.1086/150754)

(ref: HuangMeiLing2014) Huang, M.-L., & Kauffmann, G. 2014, MNRAS, 443, 1329, doi: [`10.1093/mnras/stu1232`](http://doi.org/10.1093/mnras/stu1232)

(ref: HuangMeiLing2015) —. 2015, MNRAS, 450, 1375, doi: [`10.1093/mnras/stv709`](http://doi.org/10.1093/mnras/stv709)

(ref: Hughes2017) Hughes, T. M., Ibar, E., Villanueva, V., et al. 2017, MNRAS, 468, L103, doi: [`10.1093/mnrasl/slx033`](http://doi.org/10.1093/mnrasl/slx033)

(ref: Humason1956) Humason, M. L., Mayall, N. U., & Sandage, A. R. 1956, AJ, 61, 97, doi: [`10.1086/107297`](http://doi.org/10.1086/107297)

(ref: Hunt2019) Hunt, L. K., De Looze, I., Boquien, M., et al. 2019, A&A, 621, A51, doi: [`10.1051/0004-6361/201834212`](http://doi.org/10.1051/0004-6361/201834212)

(ref: Ilbert2013) Ilbert, O., McCracken, H. J., Le Fèvre, O., et al. 2013, A&A, 556, A55, doi: [`10.1051/0004-6361/201321100`](http://doi.org/10.1051/0004-6361/201321100)

(ref: JiangXueJian2015) Jiang, X.-J., Wang, Z., Gu, Q., Wang, J., & Zhang, Z.-Y. 2015, ApJ, 799, 92, doi: [`10.1088/0004-637X/799/1/92`](http://doi.org/10.1088/0004-637X/799/1/92)

(ref: Jin2018) Jin, S., Daddi, E., Liu, D., et al. 2018, ApJ, 864, 56, doi: [`10.3847/1538-4357/aad4af`](http://doi.org/10.3847/1538-4357/aad4af)

(ref: Kaasinen2019) Kaasinen, M., Scoville, N. Z., Walter, F., et al. 2019, arXiv e-prints, arXiv:1905.11417. [`https://arxiv.org/abs/1905.11417`](https://arxiv.org/abs/1905.11417)

(ref: Kelvin2014) Kelvin, L. S., Driver, S. P., Robotham, A. S. G., et al. 2014, MNRAS, 444, 1647, doi: [`10.1093/mnras/stu1507`](http://doi.org/10.1093/mnras/stu1507)

(ref: Kennicutt1998SFL) Kennicutt, Jr., R. C. 1998a, ApJ, 498, 541, doi: [`10.1086/305588`](http://doi.org/10.1086/305588)

(ref: Kennicutt1998ARAA) —. 1998b, ARA&A, 36, 189, doi: [`10.1146/annurev.astro.36.1.189`](http://doi.org/10.1146/annurev.astro.36.1.189)

(ref: Kewley2008) Kewley, L. J., & Ellison, S. L. 2008, ApJ, 681, 1183, doi: [`10.1086/587500`](http://doi.org/10.1086/587500)

(ref: Kirkpatrick2014) Kirkpatrick, A., Pope, A., Aretxaga, I., et al. 2014, ApJ, 796, 135, doi: [`10.1088/0004-637X/796/2/135`](http://doi.org/10.1088/0004-637X/796/2/135)

(ref: Kriek2009) Kriek, M., van Dokkum, P. G., Labbé, I., et al. 2009, ApJ, 700, 221, doi: [`10.1088/0004-637X/700/1/221`](http://doi.org/10.1088/0004-637X/700/1/221)

(ref: KMT09) Krumholz, M. R., McKee, C. F., & Tumlinson, J. 2009, ApJ, 699, 850, doi: [`10.1088/0004-637X/699/1/850`](http://doi.org/10.1088/0004-637X/699/1/850)

(ref: Lagos2011) Lagos, C. D. P., Baugh, C. M., Lacey, C. G., et al. 2011, MNRAS, 418, 1649, doi: [`10.1111/j.1365-2966.2011.19583.x`](http://doi.org/10.1111/j.1365-2966.2011.19583.x)

(ref: Laigle2016) Laigle, C., McCracken, H. J., Ilbert, O., et al. 2016, ApJS, 224, 24, doi: [`10.3847/0067-0049/224/2/24`](http://doi.org/10.3847/0067-0049/224/2/24)

(ref: Lee2015) Lee, N., Sanders, D. B., Casey, C. M., et al. 2015, ApJ, 801, 80, doi: [`10.1088/0004-637X/801/2/80`](http://doi.org/10.1088/0004-637X/801/2/80)

(ref: Lee2017) Lee, N., Sheth, K., Scott, K. S., et al. 2017, MNRAS, 471, 2124, doi: [`10.1093/mnras/stx1753`](http://doi.org/10.1093/mnras/stx1753)

(ref: Leja2019) Leja, J., Carnall, A. C., Johnson, B. D., Conroy, C., & Speagle, J. S. 2019, ApJ, 876, 3, doi: [`10.3847/1538-4357/ab133c`](http://doi.org/10.3847/1538-4357/ab133c)

(ref: Leroy2009) Leroy, A. K., Walter, F., Bigiel, F., et al. 2009, AJ, 137, 4670, doi: [`10.1088/0004-6256/137/6/4670`](http://doi.org/10.1088/0004-6256/137/6/4670)

(ref: Leroy2011GDR) Leroy, A. K., Bolatto, A., Gordon, K., et al. 2011, ApJ, 737, 12, doi: [`10.1088/0004-637X/737/1/12`](http://doi.org/10.1088/0004-637X/737/1/12)

(ref: Li2001) Li, A., & Draine, B. T. 2001, ApJ, 554, 778, doi: [`10.1086/323147`](http://doi.org/10.1086/323147)

(ref: Lisenfeld2017) Lisenfeld, U., Alatalo, K., Zucker, C., et al. 2017, A&A, 607, A110, doi: [`10.1051/0004-6361/201730898`](http://doi.org/10.1051/0004-6361/201730898)

(ref: Lisenfeld2000) Lisenfeld, U., Isaak, K. G., & Hills, R. 2000, MNRAS, 312, 433, doi: [`10.1046/j.1365-8711.2000.03150.x`](http://doi.org/10.1046/j.1365-8711.2000.03150.x)

(ref: Liudz2015) Liu, D., Gao, Y., Isaak, K., et al. 2015, ApJL, 810, L14, doi: [`10.1088/2041-8205/810/2/L14`](http://doi.org/10.1088/2041-8205/810/2/L14)

(ref: Liudz2017) Liu, D., Daddi, E., Dickinson, M., et al. 2018, ApJ, 853, 172, doi: [`10.3847/1538-4357/aaa600`](http://doi.org/10.3847/1538-4357/aaa600)

(ref: Liudz2019) Liu, D., Lang, P., Magnelli, B., et al. 2019, The Astrophysical Journal Supplement Series, 244, 40, doi: [`10.3847/1538-4365/ab42da`](http://doi.org/10.3847/1538-4365/ab42da)

(ref: Lutz2014Review) Lutz, D. 2014, ARA&A, 52, 373, doi: [`10.1146/annurev-astro-081913-035953`](http://doi.org/10.1146/annurev-astro-081913-035953)

(ref: Madau2014Review) Madau, P., & Dickinson, M. 2014, ARA&A, 52, 415, doi: [`10.1146/annurev-astro-081811-125615`](http://doi.org/10.1146/annurev-astro-081811-125615)

(ref: Maeda2017) Maeda, F., Ohta, K., & Seko, A. 2017, ApJ, 835, 120, doi: [`10.3847/1538-4357/835/2/120`](http://doi.org/10.3847/1538-4357/835/2/120)

(ref: Magdis2011SED) Magdis, G. E., Daddi, E., Elbaz, D., et al. 2011, ApJL, 740, L15, doi: [`10.1088/2041-8205/740/1/L15`](http://doi.org/10.1088/2041-8205/740/1/L15)

(ref: Magdis2012SED) Magdis, G. E., Daddi, E., Béthermin, M., et al. 2012a, ApJ, 760, 6, doi: [`10.1088/0004-637X/760/1/6`](http://doi.org/10.1088/0004-637X/760/1/6)

(ref: Magdis2012LBG) Magdis, G. E., Daddi, E., Sargent, M., et al. 2012b, ApJL, 758, L9, doi: [`10.1088/2041-8205/758/1/L9`](http://doi.org/10.1088/2041-8205/758/1/L9)

(ref: Magdis2014) Magdis, G. E., Rigopoulou, D., Hopwood, R., et al. 2014, ApJ, 796, 63, doi: [`10.1088/0004-637X/796/1/63`](http://doi.org/10.1088/0004-637X/796/1/63)

(ref: Magdis2017) Magdis, G. E., Rigopoulou, D., Daddi, E., et al. 2017, A&A, 603, A93, doi: [`10.1051/0004-6361/201731037`](http://doi.org/10.1051/0004-6361/201731037)

(ref: Magnelli2012) Magnelli, B., Saintonge, A., Lutz, D., et al. 2012, A&A, 548, A22, doi: [`10.1051/0004-6361/201220074`](http://doi.org/10.1051/0004-6361/201220074)

(ref: Magnelli2014) Magnelli, B., Lutz, D., Saintonge, A., et al. 2014, A&A, 561, A86, doi: [`10.1051/0004-6361/201322217`](http://doi.org/10.1051/0004-6361/201322217)

(ref: Maiolino2008) Maiolino, R., Nagao, T., Grazian, A., et al. 2008, A&A, 488, 463, doi: [`10.1051/0004-6361:200809678`](http://doi.org/10.1051/0004-6361:200809678)

(ref: Mannucci2010) Mannucci, F., Cresci, G., Maiolino, R., Marconi, A., & Gnerucci, A. 2010, MNRAS, 408, 2115, doi: [`10.1111/j.1365-2966.2010.17291.x`](http://doi.org/10.1111/j.1365-2966.2010.17291.x)

(ref: Mannucci2011) Mannucci, F., Salvaterra, R., & Campisi, M. A. 2011, MNRAS, 414, 1263, doi: [`10.1111/j.1365-2966.2011.18459.x`](http://doi.org/10.1111/j.1365-2966.2011.18459.x)

(ref: Marchesini2009) Marchesini, D., van Dokkum, P. G., Förster Schreiber, N. M., et al. 2009, ApJ, 701, 1765, doi: [`10.1088/0004-637X/701/2/1765`](http://doi.org/10.1088/0004-637X/701/2/1765)

(ref: McGaugh1997) McGaugh, S. S., & de Blok, W. J. G. 1997, ApJ, 481, 689, doi: [`10.1086/304100`](http://doi.org/10.1086/304100)

(ref: Moustakas2013_SMF) Moustakas, J., Coil, A. L., Aird, J., et al. 2013, ApJ, 767, 50, doi: [`10.1088/0004-637X/767/1/50`](http://doi.org/10.1088/0004-637X/767/1/50)

(ref: Moutard2016) Moutard, T., Arnouts, S., Ilbert, O., et al. 2016, A&A, 590, A103, doi: [`10.1051/0004-6361/201527294`](http://doi.org/10.1051/0004-6361/201527294)

(ref: Muzzin2013) Muzzin, A., Marchesini, D., Stefanon, M., et al. 2013, ApJ, 777, 18, doi: [`10.1088/0004-637X/777/1/18`](http://doi.org/10.1088/0004-637X/777/1/18)

(ref: Noeske2007) Noeske, K. G., Weiner, B. J., Faber, S. M., et al. 2007, ApJL, 660, L43, doi: [`10.1086/517926`](http://doi.org/10.1086/517926)

(ref: Obreschkow2009) Obreschkow, D., & Rawlings, S. 2009, MNRAS, 394, 1857, doi: [`10.1111/j.1365-2966.2009.14497.x`](http://doi.org/10.1111/j.1365-2966.2009.14497.x)

(ref: Oke1968) Oke, J. B., & Sandage, A. 1968, ApJ, 154, 21, doi: [`10.1086/149737`](http://doi.org/10.1086/149737)

(ref: Pearson2018) Pearson, W. J., Wang, L., Hurley, P. D., et al. 2018, A&A, 615, A146, doi: [`10.1051/0004-6361/201832821`](http://doi.org/10.1051/0004-6361/201832821)

(ref: PengYingJie2010_SMF) Peng, Y.-j., Lilly, S. J., Kovač, K., et al. 2010, ApJ, 721, 193, doi: [`10.1088/0004-637X/721/1/193`](http://doi.org/10.1088/0004-637X/721/1/193)

(ref: PP04) Pettini, M., & Pagel, B. E. J. 2004, MNRAS, 348, L59, doi: [`10.1111/j.1365-2966.2004.07591.x`](http://doi.org/10.1111/j.1365-2966.2004.07591.x)

(ref: Pilbratt2010) Pilbratt, G. L., Riedinger, J. R., Passvogel, T., et al. 2010, A&A, 518, L1, doi: [`10.1051/0004-6361/201014759`](http://doi.org/10.1051/0004-6361/201014759)

(ref: Poglitsch2010) Poglitsch, A., Waelkens, C., Geis, N., et al. 2010, A&A, 518, L2, doi: [`10.1051/0004-6361/201014535`](http://doi.org/10.1051/0004-6361/201014535)

(ref: Popping2014) Popping, G., Somerville, R. S., & Trager, S. C. 2014, MNRAS, 442, 2398, doi: [`10.1093/mnras/stu991`](http://doi.org/10.1093/mnras/stu991)

(ref: Popping2019) Popping, G., Pillepich, A., Somerville, R. S., et al. 2019, arXiv e-prints, arXiv:1903.09158. [`https://arxiv.org/abs/1903.09158`](https://arxiv.org/abs/1903.09158)

(ref: Privon2018) Privon, G. C., Narayanan, D., & Davé, R. 2018, ArXiv e-prints. [`https://arxiv.org/abs/1805.03649`](https://arxiv.org/abs/1805.03649)

(ref: RemyRuyer2014) Rémy-Ruyer, A., Madden, S. C., Galliano, F., et al. 2014, A&A, 563, A31, doi: [`10.1051/0004-6361/201322803`](http://doi.org/10.1051/0004-6361/201322803)

(ref: RemyRuyer2015) —. 2015, A&A, 582, A121, doi: [`10.1051/0004-6361/201526067`](http://doi.org/10.1051/0004-6361/201526067)

(ref: Riechers2019) Riechers, D. A., Pavesi, R., Sharon, C. E., et al. 2019, ApJ, 872, 7, doi: [`10.3847/1538-4357/aafc27`](http://doi.org/10.3847/1538-4357/aafc27)

(ref: Rodighiero2011) Rodighiero, G., Daddi, E., Baronchelli, I., et al. 2011, ApJL, 739, L40, doi: [`10.1088/2041-8205/739/2/L40`](http://doi.org/10.1088/2041-8205/739/2/L40)

(ref: Rodighiero2014) Rodighiero, G., Renzini, A., Daddi, E., et al. 2014, MNRAS, 443, 19, doi: [`10.1093/mnras/stu1110`](http://doi.org/10.1093/mnras/stu1110)

(ref: Saintonge2011a) Saintonge, A., Kauffmann, G., Kramer, C., et al. 2011a, MNRAS, 415, 32, doi: [`10.1111/j.1365-2966.2011.18677.x`](http://doi.org/10.1111/j.1365-2966.2011.18677.x)

(ref: Saintonge2011b) Saintonge, A., Kauffmann, G., Wang, J., et al. 2011b, MNRAS, 415, 61, doi: [`10.1111/j.1365-2966.2011.18823.x`](http://doi.org/10.1111/j.1365-2966.2011.18823.x)

(ref: Saintonge2013) Saintonge, A., Lutz, D., Genzel, R., et al. 2013, ApJ, 778, 2, doi: [`10.1088/0004-637X/778/1/2`](http://doi.org/10.1088/0004-637X/778/1/2)

(ref: Saintonge2017) Saintonge, A., Catinella, B., Tacconi, L. J., et al. 2017, ApJS, 233, 22, doi: [`10.3847/1538-4365/aa97e0`](http://doi.org/10.3847/1538-4365/aa97e0)

(ref: Saintonge2018) Saintonge, A., Wilson, C. D., Xiao, T., et al. 2018, MNRAS, 481, 3497, doi: [`10.1093/mnras/sty2499`](http://doi.org/10.1093/mnras/sty2499)

(ref: Sanders2003) Sanders, D. B., Mazzarella, J. M., Kim, D.-C., Surace, J. A., & Soifer, B. T. 2003, AJ, 126, 1607, doi: [`10.1086/376841`](http://doi.org/10.1086/376841)

(ref: Sandstrom2013) Sandstrom, K. M., Leroy, A. K., Walter, F., et al. 2013, ApJ, 777, 5, doi: [`10.1088/0004-637X/777/1/5`](http://doi.org/10.1088/0004-637X/777/1/5)

(ref: Santini2010) Santini, P., Maiolino, R., Magnelli, B., et al. 2010, A&A, 518, L154, doi: [`10.1051/0004-6361/201014748`](http://doi.org/10.1051/0004-6361/201014748)

(ref: Santini2012_SMF) Santini, P., Fontana, A., Grazian, A., et al. 2012, A&A, 538, A33, doi: [`10.1051/0004-6361/201117513`](http://doi.org/10.1051/0004-6361/201117513)

(ref: Santini2014) Santini, P., Maiolino, R., Magnelli, B., et al. 2014, A&A, 562, A30, doi: [`10.1051/0004-6361/201322835`](http://doi.org/10.1051/0004-6361/201322835)

(ref: Sargent2012) Sargent, M. T., Béthermin, M., Daddi, E., & Elbaz, D. 2012, ApJ, 747, L31, doi: [`10.1088/2041-8205/747/2/L31`](http://doi.org/10.1088/2041-8205/747/2/L31)

(ref: Sargent2013) Sargent, M. T., Daddi, E., Béthermin, M., & Elbaz, D. 2013, Asociacion Argentina de Astronomia La Plata Argentina Book Series, 4, 116

(ref: Sargent2014) Sargent, M. T., Daddi, E., Béthermin, M., et al. 2014, ApJ, 793, 19, doi: [`10.1088/0004-637X/793/1/19`](http://doi.org/10.1088/0004-637X/793/1/19)

(ref: Schinnerer2016) Schinnerer, E., Groves, B., Sargent, M. T., et al. 2016, ApJ, 833, 112, doi: [`10.3847/1538-4357/833/1/112`](http://doi.org/10.3847/1538-4357/833/1/112)

(ref: Schmidt1959) Schmidt, M. 1959, ApJ, 129, 243, doi: [`10.1086/146614`](http://doi.org/10.1086/146614)

(ref: Schombert2001) Schombert, J. M., McGaugh, S. S., & Eder, J. A. 2001, AJ, 121, 2420, doi: [`10.1086/320398`](http://doi.org/10.1086/320398)

(ref: Schreiber2015) Schreiber, C., Pannella, M., Elbaz, D., et al. 2015, A&A, 575, A74, doi: [`10.1051/0004-6361/201425017`](http://doi.org/10.1051/0004-6361/201425017)

(ref: Scoville2007) Scoville, N., Aussel, H., Brusa, M., et al. 2007, ApJS, 172, 1, doi: [`10.1086/516585`](http://doi.org/10.1086/516585)

(ref: Scoville2014) Scoville, N., Aussel, H., Sheth, K., et al. 2014, ApJ, 783, 84, doi: [`10.1088/0004-637X/783/2/84`](http://doi.org/10.1088/0004-637X/783/2/84)

(ref: Scoville2016) Scoville, N., Sheth, K., Aussel, H., et al. 2016, ApJ, 820, 83, doi: [`10.3847/0004-637X/820/2/83`](http://doi.org/10.3847/0004-637X/820/2/83)

(ref: Scoville2017) Scoville, N., Lee, N., Vanden Bout, P., et al. 2017, ApJ, 837, 150, doi: [`10.3847/1538-4357/aa61a0`](http://doi.org/10.3847/1538-4357/aa61a0)

(ref: Scoville2013b) Scoville, N. Z. 2013, Evolution of star formation and gas, ed. J. Falcón-Barroso & J. H. Knapen, 491

(ref: Shen_2003_Galaxy_Sizes) Shen, S., Mo, H. J., White, S. D. M., et al. 2003, MNRAS, 343, 978, doi: [`10.1046/j.1365-8711.2003.06740.x`](http://doi.org/10.1046/j.1365-8711.2003.06740.x)

(ref: Shi2014) Shi, Y., Armus, L., Helou, G., et al. 2014, Nature, 514, 335, doi: [`10.1038/nature13820`](http://doi.org/10.1038/nature13820)

(ref: Shi2016) Shi, Y., Wang, J., Zhang, Z.-Y., et al. 2016, Nature Communications, 7, 13789, doi: [`10.1038/ncomms13789`](http://doi.org/10.1038/ncomms13789)

(ref: Silverman2015CO) Silverman, J. D., Daddi, E., Rodighiero, G., et al. 2015, ApJL, 812, L23, doi: [`10.1088/2041-8205/812/2/L23`](http://doi.org/10.1088/2041-8205/812/2/L23)

(ref: Silverman2018CO) Silverman, J. D., Rujopakarn, W., Daddi, E., et al. 2018, ApJ, 867, 92, doi: [`10.3847/1538-4357/aae25e`](http://doi.org/10.3847/1538-4357/aae25e)

(ref: Smail1997) Smail, I., Ivison, R. J., & Blain, A. W. 1997, ApJL, 490, L5, doi: [`10.1086/311017`](http://doi.org/10.1086/311017)

(ref: Smith2019) Smith, M. W. L., Clark, C. J. R., De Looze, I., et al. 2019, MNRAS, 486, 4166, doi: [`10.1093/mnras/stz1102`](http://doi.org/10.1093/mnras/stz1102)

(ref: Smolcic2017a) Smolčić, V., Novak, M., Bondi, M., et al. 2017, A&A, 602, A1, doi: [`10.1051/0004-6361/201628704`](http://doi.org/10.1051/0004-6361/201628704)

(ref: Solomon1991) Solomon, P. M., & Barrett, J. W. 1991, in IAU Symposium, Vol. 146, Dynamics of Galaxies and Their Molecular Cloud Distributions, ed. F. Combes & F. Casoli, 235

(ref: Solomon1997) Solomon, P. M., Downes, D., Radford, S. J. E., & Barrett, J. W. 1997, ApJ, 478, 144, doi: [`10.1086/303765`](http://doi.org/10.1086/303765)

(ref: Solomon1987) Solomon, P. M., Rivolo, A. R., Barrett, J., & Yahil, A. 1987, ApJ, 319, 730, doi: [`10.1086/165493`](http://doi.org/10.1086/165493)

(ref: Solomon2005) Solomon, P. M., & Vanden Bout, P. A. 2005, ARA&A, 43, 677, doi: [`10.1146/annurev.astro.43.051804.102221`](http://doi.org/10.1146/annurev.astro.43.051804.102221)

(ref: Song2016) Song, M., Finkelstein, S. L., Ashby, M. L. N., et al. 2016, ApJ, 825, 5, doi: [`10.3847/0004-637X/825/1/5`](http://doi.org/10.3847/0004-637X/825/1/5)

(ref: Speagle2014) Speagle, J. S., Steinhardt, C. L., Capak, P. L., & Silverman, J. D. 2014, ApJS, 214, 15, doi: [`10.1088/0067-0049/214/2/15`](http://doi.org/10.1088/0067-0049/214/2/15)

(ref: Spilker2018) Spilker, J., Bezanson, R., Barišić, I., et al. 2018, ApJ, 860, 103, doi: [`10.3847/1538-4357/aac438`](http://doi.org/10.3847/1538-4357/aac438)

(ref: Tacconi2008) Tacconi, L. J., Genzel, R., Smail, I., et al. 2008, ApJ, 680, 246, doi: [`10.1086/587168`](http://doi.org/10.1086/587168)

(ref: Tacconi2010) Tacconi, L. J., Genzel, R., Neri, R., et al. 2010, Nature, 463, 781, doi: [`10.1038/nature08773`](http://doi.org/10.1038/nature08773)

(ref: Tacconi2013) Tacconi, L. J., Neri, R., Genzel, R., et al. 2013, ApJ, 768, 74, doi: [`10.1088/0004-637X/768/1/74`](http://doi.org/10.1088/0004-637X/768/1/74)

(ref: Tacconi2018) Tacconi, L. J., Genzel, R., Saintonge, A., et al. 2018, ApJ, 853, 179, doi: [`10.3847/1538-4357/aaa4b4`](http://doi.org/10.3847/1538-4357/aaa4b4)

(ref: Tan2014) Tan, Q., Daddi, E., Magdis, G., et al. 2014, A&A, 569, A98, doi: [`10.1051/0004-6361/201423905`](http://doi.org/10.1051/0004-6361/201423905)

(ref: Thomas2005) Thomas, D., Maraston, C., Bender, R., & Mendes de Oliveira, C. 2005, ApJ, 621, 673, doi: [`10.1086/426932`](http://doi.org/10.1086/426932)

(ref: Tomczak2016) Tomczak, A. R., Quadri, R. F., Tran, K.-V. H., et al. 2016, ApJ, 817, 118, doi: [`10.3847/0004-637X/817/2/118`](http://doi.org/10.3847/0004-637X/817/2/118)

(ref: Villanueva2017) Villanueva, V., Ibar, E., Hughes, T. M., et al. 2017, MNRAS, 470, 3775, doi: [`10.1093/mnras/stx1338`](http://doi.org/10.1093/mnras/stx1338)

(ref: Walter2016) Walter, F., Decarli, R., Aravena, M., et al. 2016, ApJ, 833, 67, doi: [`10.3847/1538-4357/833/1/67`](http://doi.org/10.3847/1538-4357/833/1/67)

(ref: Werner2004) Werner, M. W., Roellig, T. L., Low, F. J., et al. 2004, ApJS, 154, 1, doi: [`10.1086/422992`](http://doi.org/10.1086/422992)

(ref: Whitaker2014) Whitaker, K. E., Franx, M., Leja, J., et al. 2014, ApJ, 795, 104, doi: [`10.1088/0004-637X/795/2/104`](http://doi.org/10.1088/0004-637X/795/2/104)

(ref: Wilson1995) Wilson, C. D. 1995, ApJL, 448, L97, doi: [`10.1086/309615`](http://doi.org/10.1086/309615)

(ref: Wright2018_SMF) Wright, A. H., Driver, S. P., & Robotham, A. S. G. 2018, MNRAS, 480, 3491, doi: [`10.1093/mnras/sty2136`](http://doi.org/10.1093/mnras/sty2136)

(ref: Wright2017_SMF) Wright, A. H., Robotham, A. S. G., Driver, S. P., et al. 2017, MNRAS, 470, 283, doi: [`10.1093/mnras/stx1149`](http://doi.org/10.1093/mnras/stx1149)

(ref: Wright2010) Wright, E. L., Eisenhardt, P. R. M., Mainzer, A. K., et al. 2010, AJ, 140, 1868, doi: [`10.1088/0004-6256/140/6/1868`](http://doi.org/10.1088/0004-6256/140/6/1868)

(ref: Wuyts2014) Wuyts, E., Kurk, J., Förster Schreiber, N. M., et al. 2014, ApJL, 789, L40, doi: [`10.1088/2041-8205/789/2/L40`](http://doi.org/10.1088/2041-8205/789/2/L40)

(ref: Young_and_Scoville_1991_ARAA) Young, J. S., & Scoville, N. Z. 1991, ARA&A, 29, 581, doi: [`10.1146/annurev.aa.29.090191.003053`](http://doi.org/10.1146/annurev.aa.29.090191.003053)

[^1]: <https://sites.google.com/view/a3cosmos>

[^2]: Same as those adopted by .

[^3]: The (b) and (c) methods have the same underlying physics, which is using dust mass to trace the total gas mass. Here we separate them because they have different technical steps and assumptions. See details in Sects. [3.1](#Section_Deriving_Gas_Mass_1) and [3.2](#Section_Deriving_Gas_Mass_234).

[^4]: This means first applying the $K$-correction ((cite: Humason1956; Oke1968)) to the best-fit SED, then interpolating/extrapolating to certain calibration wavelengths, then scale the observed ALMA flux accordingly, see details afterwards.

[^5]: See Appx. [11](#Section_Appendix_MCMC_Corner_Diagram) for the probability distributions of the fitted coefficients. We also provide a

    `Python`

    package for the calculation with our functions: <https://ascl.net/code/v/2377>.

[^6]: We remind the reader that in (cite: Speagle2014) the functional fitting with redshift ($\log_{10} (1+z)$) in their Table 8 is not suitable to use at high redshifts, e.g., $z\gtrsim4$. Those fits are much different from the functions with cosmic age. For example, with the same #49 fitting set, the two MS functions agree only at $z\lesssim 1.5$, while the difference can be 0.5 dex at $z\sim4.3$ (with the MS function with $\log_{10} (1+z)$ being higher).

[^7]: `pymc3`

    documentation: <https://docs.pymc.io/>; and

    `scipy.optimize.curve_fit`

    : <https://docs.scipy.org/doc/scipy/reference/generated/scipy.optimize.curve_fit.html>.

[^8]: Note that we are using their $\mathrm{sSFR}$ function instead of the $\Sigma_{\mathrm{SFR}}$ function in their abstract.

[^9]: We caution that used a different MS function than this work and . Our test in Appx. [9.5](#Section_MS) shows that their MS can explain half of the discrepancy seen in Figs. [12](#Plot_cosmic_evolution_of_rho_molgas_with_data) and [13](#Plot_cosmic_evolution_of_rho_molgas_via_galaxy_model). The other major contributor to the discrepancy is the functional form. As shown in Figs. [11](#Plot_z_deltaGas_comparison), their gas fraction’s functional form is too high at both low- and high-redshift ($z<1$ and $z>4$) and for less-massive ($\log_{10} M_{\star}<10$) galaxies. While integrating all galaxies to compute the cosmic gas mass density, such a difference in the functional forms causes a large discrepancy.

[^10]: Note that their equation in the Table 2 caption should be $y = a + b x + c x^2 + d x^3$.

</paper>

## Items to check

```json
[
 {
  "path": "claims[0].evidence[0]",
  "value": "The new form is statistically better",
  "failed_quote": "our proposed functional form ... gives statistically better fits to the data in this work than both the"
 }
]
```
