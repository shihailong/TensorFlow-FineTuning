# TensorFlow-FineTuning

# Step 1: 下载并解压数据集  
curl http://download.tensorflow.org/example_images/flower_photos.tgz  
tar xz -C /home/shl/Datasets/
# Step 2: 训练
python3 retrain.py --bottleneck_dir=./train/bottlenecks --how_many_training_steps=4000 --model_dir=./pretrained/ --summaries_dir=./train/training_summaries --output_graph=./train/retrained_graph.pb --output_labels=./train/retrained_labels.txt --image_dir=/home/shl/Datasets/flower_photos  
  
训练完成之后会生成两个文件：retrained_graph.pb & retrained_labels.txt。  
这两个文件在预测的时候要用到  
# Step 3: 预测
python3 label_image.py --graph=train/retrained_graph.pb --labels=./train/retrained_labels.txt --image=./data/test.jpg  
  
**输出：**  
dandelion 0.933346  
sunflowers 0.0382961  
tulips 0.0261172  
daisy 0.00190484  
roses 0.000335968  
