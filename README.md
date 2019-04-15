SimRNA is a computational method that performs a Monte Carlo simulation of a system composed of one or several chains of ribonucleic acid (RNA). This repository contains data for SimRNA Replica Exchange Monte Carlo (REMC) simulations. The simulations were performed to model the three dimensional structure of 3D structure of adenine riboswitch aptamer domain (PDB ID: 5SWE).

1. 5SWE_norest directory
    The directory consits of files from a SimRNA REMC simulations with ten replicas, without any restraints. The commands used for running and processing the simulations are below:
        $ SimRNA -c config.dat -s 5SWE.seq -o 5SWE_norest -E 10
        $ cat 5SWE_norest_??.trafl > 5SWE_norest_ALL.trafl
        $ clustering 5SWE_norest_ALL.trafl 0.01 7.1 >& 5SWE_norest_clustering.log
        $ SimRNA_trafl2pdbs 5SWE_norest_01-000001.pdb  5SWE_norest_ALL_thrs7.10A_clust01.trafl 1 AA
        $ SimRNA_trafl2pdbs 5SWE_norest_01-000001.pdb  5SWE_norest_ALL_thrs7.10A_clust02.trafl 1 AA
        $ SimRNA_trafl2pdbs 5SWE_norest_01-000001.pdb  5SWE_norest_ALL_thrs7.10A_clust03.trafl 1 AA

2. 5SWE_ss
    The directory consits of files from a SimRNA REMC simulations with ten replicas, with secondary structural restraints. The commands used for running and processing the simulations are below:
        $ SimRNA -c config.dat -s 5SWE.seq -S 5SWE_PDB.ss -o 5SWE_ss -E 10
        $ cat 5SWE_ss_??.trafl > 5SWE_ss_ALL.trafl
        $ clustering 5SWE_ss_ALL.trafl 0.01 7.1 >& 5SWE_ss_clustering.log
        $ SimRNA_trafl2pdbs 5SWE_ss_01-000001.pdb 5SWE_ss_ALL_thrs7.10A_clust01.trafl 1 AA
        $ SimRNA_trafl2pdbs 5SWE_ss_01-000001.pdb 5SWE_ss_ALL_thrs7.10A_clust02.trafl 1 AA
        $ SimRNA_trafl2pdbs 5SWE_ss_01-000001.pdb 5SWE_ss_ALL_thrs7.10A_clust03.trafl 1 AA
        
3. 5SWE_ss_3dr
    The directory consits of files from a SimRNA REMC simulations with ten replicas, with secondary structural restraints and 3D distance restraints. The commands used for running and processing the simulations are below:
        $ SimRNA -c config_n0.dat -p region-to-restrain.pdb
        $ python pdb_2_SimRNA_dist_restrs.py region-to-restrain.pdb-000001.pdb > restraints.dat
        $ SimRNA -c config.dat -s 5SWE.seq -S 5SWE_PDB.ss -r restraints.dat -o 5SWE_ss_3dr -E 10
        $ cat 5SWE_ss_3dr_??.trafl >5SWE_ss_3dr_ALL.trafl
        $ clustering 5SWE_ss_3dr_ALL.trafl 0.01 7.1 >& 5SWE_ss_3dr_clustering.log
        $ SimRNA_trafl2pdbs 5SWE_ss_3dr_01-000001.pdb 5SWE_ss_3dr_ALL_thrs7.10A_clust01.trafl 1 AA
        $ SimRNA_trafl2pdbs 5SWE_ss_3dr_01-000001.pdb 5SWE_ss_3dr_ALL_thrs7.10A_clust02.trafl 1 AA
        $ SimRNA_trafl2pdbs 5SWE_ss_3dr_01-000001.pdb 5SWE_ss_3dr_ALL_thrs7.10A_clust03.trafl 1 AA
