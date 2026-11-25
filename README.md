<h1 align="center">pRFs / Benson14-Retinotopy</h1>

<p align="center">
  Predicts retinotopic maps (polar angle, eccentricity, pRF size) and visual area labels V1-V3a from a FreeSurfer subject with the Benson 2014 anatomical template in neuropythy.
</p>

<p align="center">
  <a href="https://github.com/brainlife/abcd-spec"><img src="https://img.shields.io/badge/ABCD_Spec-v1.1-green.svg" alt="ABCD Spec v1.1"></a>
  <a href="https://doi.org/10.25663/brainlife.app.559"><img src="https://img.shields.io/badge/Brainlife-brainlife.app.559-blue.svg" alt="Run on brainlife.io"></a>
  <a href="LICENSE"><img src="https://img.shields.io/badge/License-see_LICENSE-lightgrey.svg" alt="License"></a>
</p>

## At a glance

<!-- brainlife-app:begin (generated from the App manifest; edit the manifest, not this block) -->

> **Predicts retinotopic maps (polar angle, eccentricity, pRF size) and visual area labels V1-V3a from a FreeSurfer subject with the Benson 2014 anatomical template in neuropythy.**

Runs neuropythy benson14_retinotopy on a FreeSurfer recon-all directory and reorganises the results into pRF maps (volume and surface), a 12-region visual area parcellation (V1, V2, V3, hV4, VO1, VO2, LO1, LO2, TO1, TO2, V3b, V3a) in volume and on the surface, and GIfTI surfaces. Use it to obtain visual cortex ROIs and retinotopy without functional mapping data. Needs a FreeSurfer license.

| | |
|---|---|
| **Inputs** | `neuro/freesurfer` |
| **Outputs** | `neuro/prf` · `neuro/parcellation/volume` · `neuro/surface/data` · `neuro/surface/vertices` · `neuro/parcellation/surface-deprecated` |
| **Container** | `brainlife/neuropythy:0.12.16` |
| **Resources** | 2 CPUs · 20 GB memory · 4 h walltime |
| **Requires** | `FREESURFER_LICENSE` |
| **Run it** | [doi.org/10.25663/brainlife.app.559](https://doi.org/10.25663/brainlife.app.559) |

#### Inputs

| Input | Datatype | Required | Description |
|---|---|---|---|
| `freesurfer` | `neuro/freesurfer` | yes | Completed FreeSurfer recon-all subject directory. |

#### Outputs

| Output | Datatype | Description |
|---|---|---|
| `prf` | `neuro/prf` | Predicted pRF maps: polar angle, eccentricity, receptive field size and visual area, as volumes and surface overlays. |
| `varea` | `neuro/parcellation/volume` | Parcellation of visually-responsive cortex into 12 regions12 regions (V1, V2, V3, hV4, VO1, VO2, LO1, LO2, TO1, TO2, V3b, V3a) |
| `varea_surface` | `neuro/surface/data` | Parcellation of visually-responsive cortex into 12 regions12 regions (V1, V2, V3, hV4, VO1, VO2, LO1, LO2, TO1, TO2, V3b, V3a) |
| `surfaces` | `neuro/surface/vertices` | White, pial and inflated surfaces of both hemispheres (GIfTI). |
| `parc_deprecated` | `neuro/parcellation/surface-deprecated` | Parcellation of visually-responsive cortex into 12 regions12 regions (V1, V2, V3, hV4, VO1, VO2, LO1, LO2, TO1, TO2, V3b, V3a) |

<details>
<summary><b>Parameters</b> (1)</summary>

| Parameter | Type | Default | Description |
|---|---|---|---|
| `template` | enum | `Benson14` | the template to use Options: `Benson14`. |

</details>

<!-- brainlife-app:end -->

## Running the App

### On brainlife.io

Open the App at [doi.org/10.25663/brainlife.app.559](https://doi.org/10.25663/brainlife.app.559), choose `neuro/freesurfer` from your project, set the parameters and press **Execute**. The results are saved to your project as `neuro/prf`, `neuro/parcellation/volume`, `neuro/surface/data`, `neuro/surface/vertices`, `neuro/parcellation/surface-deprecated`.

### Locally

You need [Singularity/Apptainer](https://apptainer.org/) (the App runs in `brainlife/neuropythy:0.12.16`), [`jq`](https://jqlang.github.io/jq/), `FREESURFER_LICENSE`.

1. Clone this repository.
2. Create `config.json` with the paths to your inputs and the parameters:

   ```json
   {
       "freesurfer": "/path/to/freesurfer/freesurfer",
       "template": "Benson14"
   }
   ```

3. Run `./main`.

## Notes on Execution

* The pipeline:

  * copies the FreeSurfer subject locally (`./output`)
  * runs neuropythy directly via Python API inside the container
* No bind mounts are required
* Environment variables are used for passing parameters into the container
* Compatible with restricted HPC environments

---

## product.json

Provides structured metadata for:

* web visualization
* API queries
* downstream processing

---

## Citing

If you use this App, please cite it, the software it builds on and brainlife.io:

- pRFs / Benson14-Retinotopy. brainlife.io App. [doi:10.25663/brainlife.app.559](https://doi.org/10.25663/brainlife.app.559)
- Benson NC, Butt OH, Brainard DH, Aguirre GK. Correction of distortion in flattened representations of the cortical surface allows prediction of V1-V3 functional organization from anatomy. PLoS Comput Biol 10:e1003538 (2014). [doi:10.1371/journal.pcbi.1003538](https://doi.org/10.1371/journal.pcbi.1003538)
- Benson NC, Butt OH, Datta R, Radoeva PD, Brainard DH, Aguirre GK. *The retinotopic organization of striate cortex is well predicted by surface topology.*
- Benson NC, Winawer J. *Bayesian analysis of retinotopic maps.* eLife. 2018;7:e40224. [https://doi.org/10.7554/eLife.40224](https://doi.org/10.7554/eLife.40224) ---
- Fischl. FreeSurfer. *NeuroImage* 62:774-781 (2012). [doi:10.1016/j.neuroimage.2012.01.021](https://doi.org/10.1016/j.neuroimage.2012.01.021)
- Hayashi S, Caron BA, Heinsfeld AS, et al. brainlife.io: a decentralized and open-source cloud platform to support neuroscience research. *Nature Methods* 21:809–813 (2024). [doi:10.1038/s41592-024-02237-2](https://doi.org/10.1038/s41592-024-02237-2)
- Avesani P, McPherson B, Hayashi S, et al. The open diffusion data derivatives, brain data upcycling via integrated publishing of derivatives and reproducible open cloud services. *Scientific Data* 6:69 (2019). [doi:10.1038/s41597-019-0073-y](https://doi.org/10.1038/s41597-019-0073-y)

## Authors

* Brad Caron
* David Hunt
* Gabriele Amorosino

---

**Contributors**

* Yang Zhang
* Soichi Hayashi

---

## Funding

[![Wellcome-226486/Z/22/Z](https://img.shields.io/badge/Wellcome-226486%2FZ%2F22%2FZ-purple.svg)](https://wellcome.org/)
[![NIH-NINDS-U24NS140384](https://img.shields.io/badge/NIH_NINDS-U24NS140384-green.svg)](https://reporter.nih.gov/project-details/11261037)
[![NIH-NINDS-UM1NS132207](https://img.shields.io/badge/NIH_NINDS-UM1NS132207-green.svg)](https://reporter.nih.gov/project-details/11411328)
[![NIH-NIBIB-R01EB029272](https://img.shields.io/badge/NIH_NIBIB-R01EB029272-green.svg)](https://reporter.nih.gov/project-details/10262925)
[![NIH-NIBIB-R01EB030896](https://img.shields.io/badge/NIH_NIBIB-R01EB030896-green.svg)](https://reporter.nih.gov/project-details/10428625)
[![NIH-NIMH-R01MH126699](https://img.shields.io/badge/NIH_NIMH-R01MH126699-green.svg)](https://reporter.nih.gov/project-details/10460628)
[![NIH-NIDCD-R01DC020088](https://img.shields.io/badge/NIH_NIDCD-R01DC020088-green.svg)](https://reporter.nih.gov/project-details/11140284)
[![NSF-BCS-1734853](https://img.shields.io/badge/NSF_BCS-1734853-blue.svg)](https://www.nsf.gov/awardsearch/showAward?AWD_ID=1734853)
[![NSF-BCS-2203524](https://img.shields.io/badge/NSF_BCS-2203524-blue.svg)](https://www.nsf.gov/awardsearch/showAward?AWD_ID=2203524)
[![NSF-IIS-1636893](https://img.shields.io/badge/NSF_IIS-1636893-blue.svg)](https://www.nsf.gov/awardsearch/showAward?AWD_ID=1636893)
[![NSF-OAC-2148729](https://img.shields.io/badge/NSF_OAC-2148729-blue.svg)](https://www.nsf.gov/awardsearch/showAward?AWD_ID=2148729)
[![NSF-IIS-1912270](https://img.shields.io/badge/NSF_IIS-1912270-blue.svg)](https://www.nsf.gov/awardsearch/showAward?AWD_ID=1912270)
[![NSF-IIS-2148700](https://img.shields.io/badge/NSF_IIS-2148700-blue.svg)](https://www.nsf.gov/awardsearch/showAward?AWD_ID=2148700)
[![NSF-OAC-1916518](https://img.shields.io/badge/NSF_OAC-1916518-blue.svg)](https://www.nsf.gov/awardsearch/showAward?AWD_ID=1916518)

<sub>brainlife.io, which runs this App, is publicly funded by Wellcome, the U.S. National Institutes of Health and the U.S. National Science Foundation; acknowledging that support helps keep it running.</sub>

## License

See [LICENSE](LICENSE).
