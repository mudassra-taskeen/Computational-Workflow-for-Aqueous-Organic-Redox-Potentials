# Computational Workflow for Aqueous Organic Redox Potentials

This proof of concept prepares NWChem inputs for aqueous organic redox couples and uses the computational hydrogen electrode (CHE) method to estimate reduction potentials from completed calculations. The motivating application is screening organic molecules for aqueous redox flow batteries.

**Repository status.** This repository currently contains the project overview and license. The implementation, environment file, demonstration notebook, and NWChem input and output files are required to reproduce the workflow and are pending publication.

## How the calculation works

1. Propose organic candidates and their reduced products using molecular generation and functional-group rules. The prototype restricts candidate elements to C, N, O, and F.
2. Search conformers and prepare NWChem inputs for the oxidized and reduced states. The proof of concept uses PBE/def2-SV(P) with an implicit aqueous environment at room temperature.
3. Run NWChem jobs externally. The workflow uses the completed outputs for post-processing.
4. For a modeled reduction consuming $x$ protons and $n$ electrons, use the CHE thermodynamic cycle and calculate $E = -\Delta G/(nF)$, where $\Delta G$ is the molar reaction free energy at the stated conditions and $F$ is the Faraday constant. Report the pH and reference electrode with the potential.

The prototype uses rule-based product proposals and a fixed calculation setup. Its estimates address thermodynamic driving force. Battery performance also depends on properties such as solubility, stability, and reaction kinetics.

## Proof of concept and next step

The original demonstration was described as testing the preparation and post-processing workflow on a small set of candidate couples, including an intentionally incomplete run to illustrate error handling. The first reproducible example should include the balanced half-reaction, paired NWChem input and output files, the extracted energies and corrections, and the resulting potential with its reference scale.

A follow-up benchmark would compare one calculated quinone/hydroquinone potential with a published measurement under comparable aqueous conditions. Record the pH, temperature, and reference electrode so readers can interpret the difference.

## License

[MIT License](LICENSE)
