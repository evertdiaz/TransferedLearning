#Uso de Inception V3 para Transfered Learning

Dataset de DBZ: https://drive.google.com/file/d/0B4VlXJBwLtTHRTZSWTR1eFFvSDA/view?usp=sharing

================
Ejecucion de Inception en Contenedor
python retrain.py \
  --bottleneck_dir=bottlenecks \
  --how_many_training_steps=500 \
  --model_dir=inception \
  --summaries_dir=training_summaries/basic \
  --output_graph=retrained_graph.pb \
  --output_labels=retrained_labels.txt \
  --image_dir=dbz
================
Levantar el contenedor:
docker run -it \
  --publish 6006:6006 \
  --volume ${HOME}/tf_files:/tf_files \
  --workdir /tf_files \
  tensorflow/tensorflow:1.1.0 bash

Abrir tensorboard
tensorboard --logdir training_summaries &
