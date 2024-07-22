
### Introduction

+ ***./DsDTW***  代码所在的文件夹
+ ***./DsDTW/main_VitDTW*** Vit的训练脚本
+ ***./DsDTW/main_SigDTW*** 我们的工作的训练脚本
+ ***Task for you***
+ ***Task1: reproduce the result*** 
  + 首先可以看一下数据集MCYT，我之前在这上面跑Vit模型的结果是4.89，baseline是1.86，baseline的原文可以看./DsDTW里面的ReadMe。
    + 环境配置
      这是我在本地跑的，配环境需要
      ```
      pip install DsDTW/requirements.txt
      ```      
    + 重新训练VitDTW模型，需要更改一些路径，比如data_dir
      ```
      python main_VitDTW.py
      ```
    + 重新训练我们的模型
      ```
      python main_DsDTW.py
      ```
    + 测试结果
      ```
      python evaluate DsDTW.py --train-shot-g 4 --epoch 3 --seed 24316
      ```
    到这一步看一下能否复现出来之前的4.89，之后可以顺便跑一下我们的模型看结果怎么样，不管结果多少到这里可以先和我交流一下。
  + ***Task2: load Vit pretrained model*** 
    + 在huggingface[https://huggingface.co/google/vit-base-patch16-224-21k]上下载vit的模型，这份代码中的模型可能会跟上面的不太一样，看一下能否通过修改应用完全一致, 只需要修改backbone部分就好。
    ```
        self.backbone = Vit(depth=depth,img_shape=(150,220),embedding_dim=embedding_dim,p_w=p_w,\
                            p_h=p_h,num_class=n_hidden,v_dim=embedding_dim//8,original=orignial)
    ```
  + ***Task3: finetune Vit-based model*** 
    + 如果上一步不行，可以修改一下Vit的层数，看一下有没有涨点，最近读论文发现时间序列需要Transformer的层数都很少，但这里不单纯是Transformer，所以不一定会有效。
    + 同理可以试一下在我们的模型上是否有效。
+ 如果上述有效的话，可以开始着手写论文，否则可能就是一段科研经历，主要贡献点还是ViT在手写笔迹这种时序序列上面的拓展。
+ 有一篇文章强烈建议参考 https://github.com/Leezekun/ViTST



### Requirements

+ torch = 1.7.1
+ torchvision = 0.8.2
+ signatory = 1.2.3.1.6.0






