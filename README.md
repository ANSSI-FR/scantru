# scantru

This repository provides the EM traces used in the following article:

**Security Assessment of NTRU Against Non-Profiled SCA**, Luk Bettale, Julien Eynard, Simon Montoya, Guénaël Renault, Rémi Strullu, *CARDIS 2022, 7-9 November, 2022, Birmingham, UK*.

These datasets are provided to ensure the reproducibility of the results claimed in the above mentioned article as well as to encourage the community to use them to experiment with any kind of SCA technique.

- Traces: 

	They can be found at the following address: https://www.data.gouv.fr/fr/datasets/scantru/

	There are 200 compressed files named *data_1.zip*, *data_2.zip*, ..., *data_200.zip*, each of them weighting around 19.8MB.

	Each file corresponds to one random, fixed, secret NTRU key to be found (509 coefficients uniformly sampled in {0,1,2047}).

	Each file contains two datasets, named ***traces*** and ***key***.

	The dataset ***key*** is a 1D array composed of 509 integers in {0,1,2047}. It is an NTRU key that is aimed to be found through the attack.

	The dataset ***traces*** is a 3D array of 8-bit integers corresponding to the EM traces collected by the attacker. Its shape is (100,507,950). It corresponds to 100 executions of the attacked algorithm. Each execution contains the 507 extracted peaks which have been re-aligned (as explained in the article, the first and last peaks were removed because of dissimilarities). Each peak contains 950 samples. To sum up, each one of the 100 sets of 507 peaks corresponds to 507 consecutive coefficients of the key to be found.

	There is an extra file named *data_LA.h5*. It contains the few executions of key 1. It contains a single dataset **traces** with shape (15, 507, 950). These traces are used to perform the leakage assessments described in the article. Since the leakage assessment is not supervised, the key is not given.
	
- Scripts:

	There are two scripts provided in jupyter notebook format.
	
	*LA_NTRU.ipynb* contains the scripts used to perform the non profiled leakage assessment as described in the article.
	
	*SCA_on_NTRU.ipynb* contains explanations on how to open and to load the traces datasets, and it contains the attack script.
