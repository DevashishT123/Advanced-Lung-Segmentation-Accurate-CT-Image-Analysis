# Advanced-Lung-Segmentation-Accurate-CT-Image-Analysis
Lung_images_segmentation

This package provides trained U-net models for lung segmentation. For now, four models are available:

U-net(R231): This model was trained on a large and diverse dataset that covers a wide range of visual variabiliy. The model performs segmentation on individual slices, extracts right-left lung seperately includes airpockets, tumors and effusions. The trachea will not be included in the lung segmentation. https://doi.org/10.1186/s41747-020-00173-2

U-net(LTRCLobes): This model was trained on a subset of the LTRC dataset. The model performs segmentation of individual lung-lobes but yields limited performance when dense pathologies are present or when fissures are not visible at every slice.

U-net(LTRCLobes_R231): This will run the R231 and LTRCLobes model and fuse the results. False negatives from LTRCLobes will be filled by R231 predictions and mapped to a neighbor label. False positives from LTRCLobes will be removed. The fusing process is computationally intensive and can, depdending on the data and results, take up to several minutes per volume.

U-net(R231CovidWeb)

Examples of the two models applied. Left: U-net(R231), will distinguish between left and right lung and include very dense areas such as effusions (third row), tumor or severe fibrosis (fourth row) . Right: U-net(LTRLobes), will distinguish between lung lobes but will not include very dense areas. LTRCLobes_R231 will fuse LTRCLobes and R231 results. R231CovidWeb is trained with aditional COVID-19 data.

# jpg, png and non HU images

As of version 0.2.5 these images are supported. Use the --noHU tag if you process images that are not encoded in HU. Keep in mind that the models were trained on proper CT scans encoded in HU. The results on cropped, annotated, very high and very low intensity shifted images may not be very reliable. When using the --noHU tag only single slices can be processed.
