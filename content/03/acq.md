Data acquisition
=========================================================

```{admonition} Issue
Data acquisition is largely carried out with vendored systems. Manufacturers typically keep their software and hardware closed or semi-open at most. As a result, researchers often receive highly processed (e.g., reconstructed) data as ‘raw’ data from the devices. The lack of transparency in the acquisition details and downstream proprietary processing prevents end-to-end reproducible neuroimaging workflows. Reproducibility is endangered, for instance, by heterogeneity in data formats, definition of critical experimental parameters, and technological differences that are translated into the data as spurious, non-biological differences between acquisition devices.
```

```{admonition} What do we provide
These shortcomings of mostly closed solutions have triggered a growing interest in open-source acquisition hardware and software {cite:p}`Winter2016-nb`. **Here, we provide a brief review of these developments and accompanying solutions aimed at fostering open and collaborative acquisition method development across imaging modalities.**
```

```{figure} ../figures/fig2.png
---
name: fig2
---
Data acquisition [^footnote2].
```

:::{dropdown} {fa}`brain` Brain data acquisition
:title: bg-ch3 font-weight-bold
:animate: fade-in

A common approach advocated by MRI researchers is establishing consensus protocols to standardize data acquisition. One of the flagship applications of this strategy is the Human Connectome Project (HCP) protocol, which achieved this within the confines of a single vendor (Smith et al. 2013). The HCP acquisition sequences and reconstruction software are compiled for different MRI scanner versions of a single vendor, openly distributed and maintained for fMRI applications (Uğurbil et al. 2013). However, it is generally difficult to achieve good inter vendor agreement using off the shelf software even for widely used protocols, such as apparent diffusion coefficient and longitudinal relaxation time (Sasaki et al. 2008; Lee et al. 2019). In addition, not all software options are available from all vendors (for example, compressed sensing (Lustig et al. 2008) and frequency-domain based parallel imaging methods (Breuer et al. 2005; Griswold et al. 2002)). Moreover, even seemingly simple image enhancement protocols, such as image inhomogeneity corrections, are often scarcely documented and validated but can affect inferences drawn from an experiment (Schmitt and Rieger 2021; e.g., Jellús and Kannengiesser 2014). Users typically have access to key parameters of pulse sequences, which are at the center of data acquisition. The exact pulse sequence descriptions are vendor-specific and may even change between software upgrades of a single vendor. This makes it difficult to evaluate multi-center validity of new acquisition methods or to acquire longitudinal data with confidence.
Fortunately, in the last decade, several vendor-neutral data acquisition pulse sequences and reconstruction frameworks have been developed to mitigate this problem: Pulseq (Layton et al. 2017), PyPulseq (Ravi, Geethanath, and Vaughan 2019), GammaStar (Cordes et al. 2020), TOPPE (Nielsen and Noll 2018), ODIN (Jochimsen and von Mengershausen 2004), and SequenceTree (Magland et al. 2016) (see Table S1). Although these tools vary in vendor compatibility and the flexibility of their acquisition runtime, they enable vendor-neutral deployment of pulse sequences with transparent access to all the details needed. Nevertheless, vendor-neutral raw data (k-space, i.e. the 2D or 3D Fourier space representation of the image) collection is half the battle.
To complete the puzzle of MR image acquisition, interoperable and open-source reconstruction frameworks are essential. Thanks to ISMRM-RD (Inati et al. 2017), a k-space data standard, community-developed reconstruction tools can have a unified way to run advanced reconstruction algorithms against undersampled raw data (Maier et al. 2021). Some of these tools include Gadgetron (Hansen and Sørensen 2013), BART (Uecker et al. 2015), MRIReco.Jl (Knopp and Grosser 2021) (see Table S1 for further tools and details). By streamlining these acquisition and reconstruction tools using data standards at multiple levels (Karakuzu, Appelhoff, et al. 2021; Inati et al. 2017) on a data-driven and container-mediated workflow engine (Di Tommaso et al. 2017), end-to-end reproducible MRI workflows can be developed. A recent study has shown that this approach can significantly reduce inter-vendor variability of quantitative MRI measurements {cite:p}`Karakuzu2020-xw` (Karakuzu, Biswas, et al. 2021; Karakuzu et al. 2020). Given the growing open-source MRI acquisition ecosystem, a variety of end-to-end workflows are possible. Therefore, community-driven validation frameworks have a key importance for interoperable solutions (Tong et al. 2021). Facilitated by these standards, effective and open communication methods development sets the future direction for reproducible MRI research (Stikov, Trzasko, and Bernstein 2019).

In PET, the variety between different scanners is even larger than in MRI. An overview over different scanner types based on their usage for a specific radiotracer targeting the serotonin transporter, namely [11C]DASB, is given in (Nørgaard, Ganz, et al. 2019). Different PET scanners export images in slightly different data formats with little overlap in the Digital Imaging and Communications in Medicine (DICOM) PET specific tags. As with MRI, reconstruction is vendor/machine specific but open source solutions to image reconstruction are being developed, for instance the OMEGA toolbox (Wettenhovi, Vauhkonen, and Kolehmainen 2021). Data acquisition for PET is further complicated by the use of different PET tracers, injection methods, scan duration and scan framing or injected radioactivity dose.

In MEG and EEG, the problem of standardized data acquisition starts even earlier: unlike the common DICOM data format used across vendors in MRI or PET, MEG and EEG manufacturers do not use a common data format, and format specifications are rarely made public. More importantly, equipment implementation significantly differs between vendors, for example with respect to MEG sensor types,(software noise suppression techniques, and EEG amplifiers and electrodes. There have been some efforts on developing open versions of some proprietary tools, for example, the Maxwell filtering for signal space separation by the MNE-python team (Gramfort et al. 2014). Additionally, initiatives, such as the OpenBCI, offer open EEG hardware and tools for biosensing and brain computer interfacing through continuous community driven development. As we have mentioned, very little is known on how the variability of data acquisition parameters affect downstream comparability of results. The EEGManyLabs project (Pavlov et al. 2021) will provide a comprehensive dataset in this regard, as many labs with different equipment try to replicate the same studies.

Given the large variations across different vendors for all neuroimaging modalities, which often cannot be overcome, it is crucial to report all data acquisition parameters in a comprehensive and standardized manner to make potential differences in data acquisition across studies and sites transparent (for a discussion of reporting guidelines see section 6.4).

:::


:::{dropdown} {fa}`bolt` Stimulus presentation and behavior
:title: bg-ch3 font-weight-bold
:animate: fade-in
Several actively maintained programs for stimulus presentation and response logging are available. Open source software includes PsychoPy (Peirce et al. 2019) in Python and Psychtoolbox (Brainard 1997; Pelli 1997; Kleiner, Brainard, and Pelli 2007) in MATLAB. Both have many users, making it possible to get assistance and perhaps find an already-implemented task protocol (e.g., on Pavlovia for Psychopy). Modality specific resources also exist, for instance the ERP CORE (Compendium of Open Resources and Experiments; Kappenman et al. 2021) openly provides optimized paradigms for several widely used ERP components, along with scripts, data processing pipelines, and sample data.

Using open stimuli and presentation software generally increases the likelihood that other researchers can perform replications, because the stimuli and software will be accessible to them. Although desirable, it is not always possible to use fully open stimuli, particularly in the case of commercial movies, audio plays, and image databases. The license of stimuli one wishes to use should always be checked, as should the license one chooses to attach to a dataset when sharing. Stimuli, presentation scripts, behavioral tests and related material should be shared whenever possible (see DuPre, Hanke, and Poline 2019 for a list of datasets sharing naturalistic stimuli and section 6). To facilitate stimuli feature analysis and exact reproducibility of the experimental paradigms, such projects as ReproNim’s ReproStim (Connolly and Halchenko 2022) could automate recording and archival of the delivered to audio-video stimulation. When specific stimuli or material can not be released, they should be described as unambiguously as possible and, if possible, providing the source, such as identification number (e.g., a GTIN), and scripts to (re)produce used stimuli from the commercial media.
:::


[^footnote2]: Sources: Icons from the Noun Project: Brain by parkjisun; Computer Screen by Icon Solid (adapted with a star); Logos: used with permission by the copyright holders.

:::{dropdown} References on this page
```{bibliography}
:filter: docname in docnames
:labelprefix: C
```
:::
