FROM gnes/build-base:latest

RUN cd /; wget -q https://gnes-1252847528.cos.ap-guangzhou.myqcloud.com/zhs.model.tar.bz2 -qO zhs.model.tar.bz2; tar -xvjf zhs.model.tar.bz2; rm zhs.model.tar.bz2

RUN cd /; wget -q https://gnes-1252847528.cos.ap-guangzhou.myqcloud.com/openai_gpt.tar.bz2 -qO openai_gpt.tar.bz2; tar -xvjf openai_gpt.tar.bz2; rm openai_gpt.tar.bz2

RUN cd /; wget -q https://gnes-1252847528.cos.ap-guangzhou.myqcloud.com/openai_gpt2.tar.bz2 -qO openai_gpt2.tar.bz2; tar -xvjf openai_gpt2.tar.bz2; rm openai_gpt2.tar.bz2

RUN cd /; wget -q https://gnes-1252847528.cos.ap-guangzhou.myqcloud.com/transformer_xl_wt103.tar.bz2 -qO transformer_xl_wt103.tar.bz2; tar -xvjf transformer_xl_wt103.tar.bz2; rm transformer_xl_wt103.tar.bz2

RUN cd /; wget https://gnes-1252847528.cos.ap-guangzhou.myqcloud.com/sgns.wiki.bigram-char.sample -qO sgns.wiki.bigram-char.sample

RUN mkdir checkpoints \
    && cd /checkpoints \
    && wget -q https://download.pytorch.org/models/fasterrcnn_resnet50_fpn_coco-258fb6c6.pth \
    && wget -q https://download.pytorch.org/models/mobilenet_v2-b0353104.pth


