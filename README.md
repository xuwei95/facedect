# facedect
使用tensorflow object_detection API训练人脸检测器
# 数据集
数据集使用人脸检测数据集widerface 地址为http://mmlab.ie.cuhk.edu.hk/projects/WIDERFace/
001_download_data.py用于下载数据到data文件夹下
下载后依次运行002_data-to-pascal-xml.py,003_xml-to-csv.py,004_generate_tfrecord.py可生成tensorflow object_detection API训练需要的tfrecord文件
已处理好的tfrecord文件已放至百度云https://pan.baidu.com/s/1K-NURSjNHM2QRRVJt705YA
# 模型
预训练模型为ssd_inception_v2_coco,官方地址为https://github.com/tensorflow/models/blob/master/research/object_detection/g3doc/detection_model_zoo.md
# 训练
运行train.py 可以用自己的数据训练目标检测模型,模型输出在train_output文件夹下
# 导出模型
运行 python export_inference_graph.py --input_type image_tensor --pipeline_config_path train.config --trained_checkpoint_prefix train_output/model.ckpt-xxxx --output_directory outmodel 可将训练好的模型导出为.pb文件 xxxx为train_output中checkpoint最后一次的训练次数
# 运行测试
运行 test.py可以测试检测一张图片中的人脸
