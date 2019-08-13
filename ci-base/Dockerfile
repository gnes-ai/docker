FROM gnes/build-base:latest

MAINTAINER team@gnes.ai

RUN cd /; wget -q https://gnes-1252847528.cos.ap-guangzhou.myqcloud.com/zhs.model.tar.bz2 -qO zhs.model.tar.bz2; tar -xvjf zhs.model.tar.bz2; rm zhs.model.tar.bz2

RUN cd /; wget -q https://gnes-1252847528.cos.ap-guangzhou.myqcloud.com/openai_gpt.tar.bz2 -qO openai_gpt.tar.bz2; tar -xvjf openai_gpt.tar.bz2; rm openai_gpt.tar.bz2

RUN cd /; wget -q https://gnes-1252847528.cos.ap-guangzhou.myqcloud.com/openai_gpt2.tar.bz2 -qO openai_gpt2.tar.bz2; tar -xvjf openai_gpt2.tar.bz2; rm openai_gpt2.tar.bz2

RUN cd /; wget -q https://gnes-1252847528.cos.ap-guangzhou.myqcloud.com/transformer_xl_wt103.tar.bz2 -qO transformer_xl_wt103.tar.bz2; tar -xvjf transformer_xl_wt103.tar.bz2; rm transformer_xl_wt103.tar.bz2

RUN cd /; wget -q https://gnes-1252847528.cos.ap-guangzhou.myqcloud.com/sgns.wiki.bigram-char.sample -qO sgns.wiki.bigram-char.sample

RUN mkdir checkpoints \
    && cd /checkpoints \
    && wget -q https://download.pytorch.org/models/vgg16-397923af.pth \
    && wget -q https://download.pytorch.org/models/resnet50-19c8e357.pth \
    && wget -q https://download.pytorch.org/models/inception_v3_google-1a9a5a14.pth \
    && wget -q https://download.pytorch.org/models/fasterrcnn_resnet50_fpn_coco-258fb6c6.pth \
    && wget -q https://download.pytorch.org/models/mobilenet_v2-b0353104.pth

RUN cd / \
    && wget -q https://s3.amazonaws.com/onnx-model-zoo/resnet/resnet50v2/resnet50v2.onnx -qO resnet50.onnx \
    && wget -q https://s3.amazonaws.com/onnx-model-zoo/vgg/vgg16/vgg16.onnx -qO vgg16.onnx \
	&& wget -q https://s3.amazonaws.com/onnx-model-zoo/mobilenet/mobilenetv2-1.0/mobilenetv2-1.0.onnx -qO mobilenetv2.onnx \
	&& wget -q https://s3.amazonaws.com/download.onnx/models/opset_9/inception_v2.tar.gz -qO inception_v2.tar.gz \
	&& tar -zxvf inception_v2.tar.gz \
	&& cp inception_v2/model.onnx inception_v2.onnx \
	&& rm inception_v2.tar.gz \
	&& rm inception_v2 -rf

RUN mkdir torch_transformer \
    && cd torch_transformer \
    && wget -q https://s3.amazonaws.com/models.huggingface.co/bert/bert-base-uncased-pytorch_model.bin -qO pytorch_model.bin \
    && wget -q https://s3.amazonaws.com/models.huggingface.co/bert/bert-base-uncased-config.json -qO config.json \
    && wget -q https://s3.amazonaws.com/models.huggingface.co/bert/bert-base-uncased-vocab.txt -qO vocab.txt