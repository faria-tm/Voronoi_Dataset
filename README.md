# Voronoi Shape Memory Polymer Metamaterials — Dataset

This repository contains the dataset supporting the paper *"[Paper title]"* by [Authors] ([Journal/Preprint], [Year], DOI: [add DOI]). It provides the recovery-force performance data and geometric descriptions of 2,015 architected Voronoi shape memory polymer (SMP) metamaterials generated and simulated for a physics-guided, data-driven inverse design framework.

Each structure is a bounded three-dimensional Voronoi lattice defined by five seed points and evaluated with a full finite element simulation of the thermomechanical shape-memory cycle in Abaqus/Standard.

## Contents

| File | Description |
|------|-------------|
| `Elasticmodulus_with_Mass_and_SpecificForce.xlsx` | Master table with one row per structure: performance metrics, mass, and specific recovery force. |
| `Properties_files.rar` | One text file per structure (`<ID>.txt`) containing the seed coordinates and geometric properties of the Voronoi lattice. |

Every structure is identified by a unique ID (a UUID). The `CAE File Name` column in the spreadsheet matches the filename of the corresponding properties file, so the two datasets can be joined on the ID.

## Dataset table (`Elasticmodulus_with_Mass_and_SpecificForce.xlsx`)

2,015 rows, one per structure, with the following columns:

| Column | Description | Units |
|--------|-------------|-------|
| `CAE File Name` | Unique structure ID; matches the properties filename. | — |
| `Maximum Compression force in step-1` | Peak reaction force during the compression (deformation) step. | N |
| `Buckle` | Buckling flag: `1` if strut buckling occurred during compression, `0` otherwise. | — |
| `Maximum Recovery Force` | Peak recovery force generated during the constrained-recovery step. | N |
| `Spring back` | Springback after unloading. | [confirm] |
| `Mass` | Total mass of the structure. | [confirm, e.g. g] |
| `Specific Maximum Recovery Force` | Maximum recovery force normalized by mass (`Maximum Recovery Force / Mass`). This is the target variable (SRF) used for model training. | N per unit mass |

## Properties files (`Properties_files.rar`)

Each `<ID>.txt` describes the geometry of one Voronoi structure with the following sections:

- **ID** — the structure's unique identifier.
- **Coordinates** — the five Voronoi seed points, each as `{x, y, z}`.
- **Volumes** — the volume of each of the five Voronoi cells.
- **Areas** — the surface area of each cell.
- **Centroids** — the centroid of each cell, as `{x, y, z}`.
- **Lines** — the strut centerlines (edges) of the lattice, each as a pair of endpoints `((x1, y1, z1), (x2, y2, z2))`.

Coordinates and geometric quantities are given in the length units of the generated geometry [confirm units, e.g. mm].

## Notes

- The dataset was obtained after excluding structures that failed to converge in the nonlinear finite element analysis, yielding the final set of 2,015 structures.
- The seed count was fixed at five for all structures; geometric variability arises solely from the spatial distribution of the seeds.

## Citation

If you use this dataset, please cite:

> [Authors]. "[Paper title]." [Journal], [Year]. DOI: [add DOI].

## License

[Add a license, e.g. CC BY 4.0 for data.]

## Contact

Amir Teimouri — fteymori16@gmail.com
