# Optimizing Dice score and Jaccard Index for Medical Image Segmentation

This repository open sources the code and models belonging to the public datasets used in:

- Optimizing the Dice Score and Jaccard Index for Medical Image Segmentation: Theory and Practice
	```
	Bertels, J., Eelbode, T., Berman, M., Vandermeulen, D., Maes, F., Bisschops, R., & Blaschko, M. B. (2019, October).
	Optimizing the Dice score and Jaccard index for medical image segmentation: Theory and practice.
	In International Conference on Medical Image Computing and Computer-Assisted Intervention (pp. 92-100). Springer, Cham.
	```
	Links: [Springer](https://link.springer.com/chapter/10.1007/978-3-030-32245-8_11) | [arXiv](https://arxiv.org/abs/1911.01685)

- Optimization for Medical Image Segmentation: Theory and Practice when evaluating with Dice Score or Jaccard Index
	```
	Eelbode, T., Bertels, J., Berman, M., Vandermeulen, D., Maes, F., Bisschops, R., & Blaschko, M. B. (2020).
	Optimization for medical image segmentation: Theory and practice when evaluating with dice score or jaccard index.
	IEEE Transactions on Medical Imaging.
	```
	Links: [IEEE](https://ieeexplore.ieee.org/abstract/document/9116807)

If you find the code useful for your research, please consider citing these works.

## Get started
1. To obtain or get more information about the original data please go to:
	- BRATS 2018: https://www.med.upenn.edu/sbia/brats2018/data.html
 	- ISLES 2017: http://www.isles-challenge.org/ISLES2017/
	- ISLES 2018: http://www.isles-challenge.org
	- WMH 2017: https://wmh.isi.uu.nl/data/

2. The original public data was resampled to a 2 mm isotropic voxel size (using scipy.ndimage.zoom with order=1).

3. Make Keras model using ./unet_generalized.py and using the information in ./<DATASET>/model_info.txt (models are the same in general, but the model for ISLES_2018 has less parameters).

4. To do predictions the information in ./<DATASET>/other_info.txt is necessary. For example for BRATS 2018:
	- Order of inputs (in feature dimension): ["FLAIR", "T1", "T1_CE", "T2"]
	- Normalize inputs using: (input - shift) / scale
		shifts: [420.884688397679, 568.7868683246469, 639.4882077323609, 629.919352934067]
		scales: [1320.6450427506038, 1160.6822019612432, 1181.144425870453, 1363.6117673325714]
	- Extract central patch of spatial size: [136, 136, 82]
	- Masking the predictions with FLAIR > 0 (can be done by setting mask argument to True when creating the model (see step 3.) and providing this as an extra input)

5. Validation splits can be found in ./<DATASET>/validation_splits.txt

## Contacts
- Bertels Jeroen 	| GitHub: [JeroenBertels](https://github.com/JeroenBertels) | ResearchGate: [Jeroen Bertels](https://www.researchgate.net/profile/Jeroen_Bertels)
- Eelbode Tom		| GitHub: [TomEelbode](https://github.com/TomEelbode) | ResearchGate: [Tom Eelbode](https://www.researchgate.net/profile/Tom_Eelbode) | LinkedIn: [tomeelbode](https://www.linkedin.com/in/tomeelbode/)

## License

All the code in this repository is covered by the [LICENSE](https://github.com/JeroenBertels/optimizingdice/blob/master/LICENSE). Please refer to the LICENSE for details.
