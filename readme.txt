
This repository open sources the code and models belonging to the public datasets used in:
	"Optimizing the Dice Score and Jaccard Index for Medical Image Segmentation: Theory and Practice":
		https://link.springer.com/chapter/10.1007/978-3-030-32245-8_11
		https://arxiv.org/abs/1911.01685
	"Optimization for Medical Image Segmentation: Theory and Practice when evaluating with Dice Score or Jaccard Index":
		https://ieeexplore.ieee.org/abstract/document/9116807

1. To obtain or get more information about the original data please go to:
	BRATS 2018: https://www.med.upenn.edu/sbia/brats2018/data.html
 	ISLES 2017: http://www.isles-challenge.org/ISLES2017/
	ISLES 2018: http://www.isles-challenge.org
	WMH 2017: https://wmh.isi.uu.nl/data/

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
