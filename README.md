# pRFs / Benson14-Retinotopy

[![Abcdspec-compliant](https://img.shields.io/badge/ABCD_Spec-v1.1-green.svg)](https://github.com/brain-life/abcd-spec)
[![Run on Brainlife.io](https://img.shields.io/badge/Brainlife-brainlife.app.559-blue.svg)](https://doi.org/10.25663/brainlife.app.559)

This app automatically maps population receptive field (pRF) estimates to the cortical surface using only a FreeSurfer subject as input. The method follows Benson et al. (2014) and is implemented via the neuropythy framework.

The pipeline has been updated to improve compatibility with modern Python environments, container execution constraints, and NumPy deprecations.

## Authors

* Brad Caron ([bacaron@utexas.edu](mailto:bacaron@utexas.edu))
* David Hunt ([dhunt@iu.edu](mailto:dhunt@iu.edu))
* Gabriele Amorosino ([g.amorosino@gmail.com](mailto:g.amorosino@gmail.com))

---

## Contributors
* Yang Zhang (yangzhang@utexas.edu)
* Soichi Hayashi ([shayashi@iu.edu](mailto:shayashi@iu.edu))

---

## Funding Acknowledgement

brainlife.io is publicly funded and for the sustainability of the project it is helpful to acknowledge the use of the platform. We kindly ask that you include the following funding sources in your publications and derivative work.

[![NSF-BCS-1734853](https://img.shields.io/badge/NSF_BCS-1734853-blue.svg)](https://nsf.gov/awardsearch/showAward?AWD_ID=1734853)
[![NSF-BCS-1636893](https://img.shields.io/badge/NSF_BCS-1636893-blue.svg)](https://nsf.gov/awardsearch/showAward?AWD_ID=1636893)
[![NSF-ACI-1916518](https://img.shields.io/badge/NSF_ACI-1916518-blue.svg)](https://nsf.gov/awardsearch/showAward?AWD_ID=1916518)
[![NSF-IIS-1912270](https://img.shields.io/badge/NSF_IIS-1912270-blue.svg)](https://nsf.gov/awardsearch/showAward?AWD_ID=1912270)
[![NIH-NIBIB-R01EB029272](https://img.shields.io/badge/NIH_NIBIB-R01EB029272-green.svg)](https://grantome.com/grant/NIH/R01-EB029272-01)

---

## Citations

Please cite the following when using this app:

1. Hayashi, S., Caron, B.A., Heinsfeld, A.S. et al.
   brainlife.io: a decentralized and open-source cloud platform to support neuroscience research.
   Nat Methods 21, 809–813 (2024). https://doi.org/10.1038/s41592-024-02237-2

4. Benson NC, Butt OH, Datta R, Radoeva PD, Brainard DH, Aguirre GK.
   *The retinotopic organization of striate cortex is well predicted by surface topology.*

5. Benson NC, Butt OH, Brainard DH, Aguirre GK.
   *Correction of distortion in flattened cortical representations...*
   PLoS Computational Biology. 2014;10:e1003538.
   [https://doi.org/10.1371/journal.pcbi.1003538](https://doi.org/10.1371/journal.pcbi.1003538)

6. Benson NC, Winawer J.
   *Bayesian analysis of retinotopic maps.*
   eLife. 2018;7:e40224.
   [https://doi.org/10.7554/eLife.40224](https://doi.org/10.7554/eLife.40224)

---

## Running the App

### On Brainlife.io

Run directly via:
[https://doi.org/10.25663/brainlife.app.559](https://doi.org/10.25663/brainlife.app.559)

---

### Running Locally

#### 1. Clone the repository

```bash
git clone <repo>
cd <repo>
```

#### 2. Create `config.json`

```json
{
  "freesurfer": "/input/freesurfer/output",
  "template": "Benson14"
}
```

---

#### 3. Run

```bash
./main
```

---

### Notes on Execution

* The pipeline:

  * copies the FreeSurfer subject locally (`./output`)
  * runs neuropythy directly via Python API inside the container
* No bind mounts are required
* Environment variables are used for passing parameters into the container
* Compatible with restricted HPC environments

---

## Output

The app produces:

* **prf/**
  pRF estimates on cortical surfaces

* **Volume outputs**
  Retinotopic maps in volumetric space

* **Surface outputs**
  Surface data and geometry (pial/white)

* **Derived datatypes**

  * surface/data
  * surface/vertices
  * parcellation/volume
  * prf

---

### product.json

Provides structured metadata for:

* web visualization
* API queries
* downstream processing

---

## Dependencies

Primary dependency:

* [Singularity / Apptainer](https://apptainer.org)

If running without containers:

* neuropythy
  [https://github.com/noahbenson/neuropythy](https://github.com/noahbenson/neuropythy)

---

## License

MIT License
