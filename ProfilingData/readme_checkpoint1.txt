How to extract features from profiled files (dup example):
--------------------------------------------
1. copy the dup folder to ~/ProfilingData/dup (worrking directory)
2. remove *Output* files from the dup folder
3. run 'python extract.py dup/' - this will generate 'testing.csv'
4. open ipython notebook

checkpoint 1 (with numactl) :
- data from 22July: numactl bound to node0 (64GB ram) and varies CPUs: 3,6,9,12
- features: #cpu, inputdataset size, TARGET: totaltime=user+sys
- random forest with cross validation
- * notebook: 22July Analysis-ModelTraining (CPU, DataSize, Y_Time) Notebook1.ipynb
- * job submission script: submitTests_v5/6.py (moved to subfolder under jobscripts folder)
- * workflow name: comet_LS002_thirdOnly_V3.xml
- * data folder: ProfilingData/22July2016

17-Jan-2017:
------------

