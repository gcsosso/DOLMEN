## Descriptors 

### Standard descriptors

The standard descriptors represent a collection of ~45 molecular properties that are accessible via RDKit [^1]. These include:

- BalabanJ - accessed via `Chem.GraphDescriptors.BalabanJ`
- BertzCT - accessed via `Chem.GraphDescriptors.BertzCT`
- HallKierAlpha - accessed via `Chem.GraphDescriptors.HallKierAlpha`
- MolLogP - accessed via `Chem.Crippen.MolLogP`
- ExactMolWt - accessed via `Chem.Descriptors.ExactMolWt`
- FpDensityMorgan1 - accessed via `Chem.Descriptors.FpDensityMorgan1`
- MaxPartialCharge - accessed via `Chem.Descriptors.MaxPartialCharge`
- FractionCSP3 - accessed via `Chem.Lipinski.FractionCSP3`
- NHOHCount - accessed via `Chem.Lipinski.NHOHCount`
- NOCount - accessed via `Chem.Lipinski.NOCount`
- CalcAsphericity - accessed via `Chem.rdMolDescriptors.CalcAsphericity`
- CalcChi0n - accessed via `Chem.rdMolDescriptors.CalcChi0n`
- CalcChi1n - accessed via `Chem.rdMolDescriptors.CalcChi1n`
- CalcChi1v - accessed via `Chem.rdMolDescriptors.CalcChi1v`
- CalcEccentricity - accessed via `Chem.rdMolDescriptors.CalcEccentricity`
- CalcFractionCSP3 - accessed via `Chem.rdMolDescriptors.CalcFractionCSP3`
- CalcHallKierAlpha - accessed via `Chem.rdMolDescriptors.CalcHallKierAlpha`
- CalcInertialShapeFactor - accessed via `Chem.rdMolDescriptors.CalcInertialShapeFactor`
- CalcKappa1 - accessed via `Chem.rdMolDescriptors.CalcKappa1`
- CalcKappa2 - accessed via `Chem.rdMolDescriptors.CalcKappa2`
- CalcKappa3 - accessed via `Chem.rdMolDescriptors.CalcKappa3`
- CalcNPR1 - accessed via `Chem.rdMolDescriptors.CalcNPR1`
- CalcNPR2 - accessed via `Chem.rdMolDescriptors.CalcNPR2`
- CalcNumAliphaticCarbocycles - accessed via `Chem.rdMolDescriptors.CalcNumAliphaticCarbocycles`
- CalcNumAliphaticHeterocycles - accessed via `Chem.rdMolDescriptors.CalcNumAliphaticHeterocycles`
- CalcNumAliphaticRings - accessed via `Chem.rdMolDescriptors.CalcNumAliphaticRings`
- CalcNumAmideBonds - accessed via `Chem.rdMolDescriptors.CalcNumAmideBonds`
- CalcNumAromaticCarbocycles - accessed via `Chem.rdMolDescriptors.CalcNumAromaticCarbocycles`
- CalcNumAromaticHeterocycles - accessed via `Chem.rdMolDescriptors.CalcNumAromaticHeterocycles`
- CalcNumAromaticRings - accessed via `Chem.rdMolDescriptors.CalcNumAromaticRings`
- CalcNumHBA - accessed via `Chem.rdMolDescriptors.CalcNumHBA`
- CalcNumHBD - accessed via `Chem.rdMolDescriptors.CalcNumHBD`
- CalcNumHeteroatoms - accessed via `Chem.rdMolDescriptors.CalcNumHeteroatoms`
- CalcNumHeterocycles - accessed via `Chem.rdMolDescriptors.CalcNumHeterocycles`
- CalcNumLipinskiHBA - accessed via `Chem.rdMolDescriptors.CalcNumLipinskiHBA`
- CalcNumLipinskiHBD - accessed via `Chem.rdMolDescriptors.CalcNumLipinskiHBD`
- CalcNumRings - accessed via `Chem.rdMolDescriptors.CalcNumRings`
- CalcNumRotatableBonds - accessed via `Chem.rdMolDescriptors.CalcNumRotatableBonds`
- CalcNumSaturatedCarbocycles - accessed via `Chem.rdMolDescriptors.CalcNumSaturatedCarbocycles`
- CalcNumSaturatedHeterocycles - accessed via `Chem.rdMolDescriptors.CalcNumSaturatedHeterocycles`
- CalcNumSaturatedRings - accessed via `Chem.rdMolDescriptors.CalcNumSaturatedRings`
- CalcPBF - accessed via `Chem.rdMolDescriptors.CalcPBF`
- CalcPMI1 - accessed via `Chem.rdMolDescriptors.CalcPMI1`
- CalcSpherocityIndex - accessed via `Chem.rdMolDescriptors.CalcSpherocityIndex`
- CalcTPSA - accessed via `Chem.rdMolDescriptors.CalcTPSA`

The `std_<dataset>.csv` files contain these descriptors computed in this order from the compound's SMILES in the respective dataset.

### Molecular cliques

Considering a molecule as a collection of nodes (atoms) and edges (bonds), i.e. a 2D graph, a clique represents a subgraph of a molecule. A vocabulary of cliques is constructed for a given dataset, and the cliques for each molecule are encoded as a fingerprint. 

The `clq_<dataset>.csv` files contain the frequency of each clique for each molecule in the respective dataset. Each set of cliques (vocabulary) is distinct for each dataset. 

### Histograms of weighted atom-centered symmetry functions (H-wACSFs)

Symmetry functions describe the local (3D) chemical environment of an atom in a molecule using radial and angular symmetry functions based on the distance and angles between pairs and triplets of atoms, respectively. In this formulation, element-dependent weighted symmetry functions are computed and the values then binned to obtain a histogram-like descriptor with the same (reduced) dimensionality for all molecules, independent of their size and atomic composition.

The `wacsf_<dataset>.csv` files contain the histograms of symmetry functions for each compound in the respective dataset. 

### Smooth overlap of atomic positions (SOAPs)

Smooth overlap of atomic positions (SOAP) descriptors encode 3D atomic environments using atomic density fields composed of Gaussian functions centred on each atom. This formalism is extended to describe molecules by averaging the density field across the constituent atoms. 

The `soaps_<dataset>.csv` files contain the SOAPs for each compound in the respective dataset. Different parameter sets used in the generation of SOAPs result in different descriptor lengths for each dataset.

### Hydration histograms

From short MD simulations, we compute a probability density histogram by calculating the pairwise distances between each water molecule and the solute at many points along the trajectory. These distances $d$ are then binned and normalised based on the total number of distances considered, and the interval width $\Delta d$, resulting in probability densities $P(d)$ for each bin, given by $P(d) = \frac{n_d}{\sum_{i}^{D_\mathrm{cut}}{n_i} \dot \Delta d}$. 

The `hydhist_<dataset>.csv` files contain the values for each of 100 bins in the histogram, ranging between 0 and 0.5 nm, for each compound in the respective dataset.

_Note: Hydration histograms were not computed for the Amino prediction set._

### Hydration indices

From short MD simulations, we compute a probability density histogram by calculating the pairwise distances between each water molecule and the solute at many points along the trajectory. These distances $d$ are then binned and normalised based on the total number of distances considered, and the interval width $\Delta d$, resulting in probability densities $P(d)$ for each bin, given by $P(d) = \frac{n_d}{\sum_{i}^{D_\mathrm{cut}}{n_i} \dot \Delta d}$. 

The `hydidx_<dataset>.csv` files contain the hydration indices for each compound in the respective dataset. The hydration numbers were computed using seven fixed cutoff distances in the range 0.20 - 0.50 nm, the distances corresponding to the first and second solvation shells, and hydrogen bond numbers

_Note: Hydration indices were not computed for the Amino prediction set._

---
#### References
[^1] RDKit: Open-source cheminformatics. (2016). https://rdkit.org/
