# ProVean
PROVEAN (Protein Variation Effect Analyzer) is a software tool which predicts whether an amino acid substitution or indel has an impact on the biological function of a protein.

## Resources and Installation
1. provean-1.1.5  (https://sourceforge.net/projects/provean/)
2. NCBI protein db V4 (https://ftp.ncbi.nlm.nih.gov/blast/db/v4/)
wget --recursive -e robots=off --reject "indexl.html" --no-host-directories --cut-dirs=6 https://ftp.ncbi.nlm.nih.gov/blast/db/v4/ -A "nr_v4*"
3. NCBI blast 2.4.0  (https://ftp.ncbi.nlm.nih.gov/blast/executables/blast+/2.4.0/)
wget --recursive -e robots=off --reject "index.html" --no-host-directories --cut-dirs=6  https://ftp.ncbi.nlm.nih.gov/blast/executables/blast+/2.4.0/
4. CD-Hit (https://anaconda.org/bioconda/cd-hit)
Step1: $ python --version 
Step2: download Miniconda3 Linux 64-bit https://docs.conda.io/en/latest/miniconda.html#linux-installers
Step3: $ bash Miniconda3-4.5.4-Linux-x86_64.sh
Step4: $ source ~/.bashrc
Step5: Set up channels ( bioconda ) 
       $ conda config --add channels defaults
       $ conda config --add channels bioconda
       $ conda config --add channels conda-forge
Step6: $ conda install -c bioconda cd-hit

## Unpack distribution,run configure,compile and install
       $ tar zxvf provean-1.1.5.tar.gz
       $ cd provean-1.1.5
       $ ./configure PSIBLAST= /path/ncbi-blast-2.4.0+/bin/psiblast CDHIT=/path/cd-hit-v4.8.1-2019-0228 BLASTDBCMD=/path/ncbi-blast-2.4.0+/bin/blastdbcmd BLAST_DB=/path/ncbi_db/nr --prefix=/path/provean-1.1.5/
       $ make
       $ make install
       $ export PATH="/path/provean-1.1.5/bin:$PATH"

## Execution
       $ cd provean-1.1.5/bin 
       $ ./provean.sh -q /path/example/P04637.fasta -v /path/example/P04637.var --save_supporting_set /path/example/P04637.sss

## Example
 ### PROVEAN v1.1 output ###
	# Query sequence file:  P04637.fasta
	# Variation file:       P04637.var
	# Protein database:     /usr/local/projects/SIFT/ychoi/provean_genome/provean_result/nr_db/nr
	# Number of clusters:   30
	# Number of supporting sequences used:  413
	[14:05:40] computing delta alignment scores...
	## PROVEAN scores ##
	# VARIATION     SCORE
	P72R    -0.461
	G105C   -8.119
	K370del -2.201
	H178_H179insPHP -10.945
	L22_W23delinsQS -10.392

## Note
The latest verions of db (latest+)  and blast are not working (Segmentation fault $COMMAND), 
please see the discussion https://sourceforge.net/p/provean/discussion/general/thread/dc1e8204/

## Credit
Yongwook Choi
ychoi@jcvi.org
