Bootstrap: docker
From: lsstdesc/stack-sims:w_2018_26-sims_2_9_0

%post
   set +e
   source scl_source enable devtoolset-6
   set -e
   source /opt/lsst/software/stack/loadLSST.bash
   setup lsst_sims
   mkdir /DC2
   cd /DC2
   git clone https://github.com/LSSTDESC/imSim.git
   cd imSim
   git checkout u/jchiang/fix_raw_file_packager
   setup -r . -j
   scons
   cd ../..
 

%environment
   source /opt/lsst/software/stack/loadLSST.bash
   setup lsst_sims
   cd /DC2
   setup -r imSim -j
   cd
   export OMP_NUM_THREADS=1

#%runscript
#   exec python /DC2/ALCF_1.2i/scripts/run_imsim.py "$@"
