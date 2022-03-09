# Evaluate performance of ONNX Runtime(Mask R-CNN) 
>ONNX runtime quantization is under active development. please use 1.6.0+ to get more quantization support. 

This example load an object detection model converted from [ONNX Model Zoo](https://github.com/onnx/models) and confirm its accuracy and speed based on [MS COCO 2017 dataset](https://cocodataset.org/#download). You need to download this dataset yourself.

### Environment
onnx: 1.9.0
onnxruntime: 1.8.0

### Prepare model
Download model from [ONNX Model Zoo](https://github.com/onnx/models)

```shell
https://github.com/onnx/models/blob/main/vision/object_detection_segmentation/mask-rcnn/model/MaskRCNN-12.onnx
```

### Quantization

```bash
bash run_tuning.sh --input_model=path/to/model  \ # model path as *.onnx
                   --config=mask_rcnn.yaml \ 
                   --data_path=path/to/COCO2017 \
                   --output_model=path/to/save
```
Make sure **anno_path** in mask_rcnn.yaml is updated to the path of label_map.yaml.

### Performance

```bash
bash run_benchmark.sh --input_model=path/to/model \  # model path as *.onnx
                      --config=mask_rcnn.yaml \
                      --data_path=path/to/COCO2017 \
                      --mode=performance
```