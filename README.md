
| Model | Paper | Venue | Year | Code | Time |
|:-------:|:-------:|:-------:|:-------:|:-------:|:-------:|
| faster rcnn | [Faster R-CNN: Towards Real-Time Object Detection with Region Proposal Networks](https://arxiv.org/abs/1506.01497) | CVPR | 2016 | [fasterrcnn_res50+fpn](https://github.com/WZMIAOMIAO/deep-learning-for-image-processing/blob/master/pytorch_object_detection/faster_rcnn/network_files/faster_rcnn_framework.py) | 2023.10.15 |
| YOLOV9 | [YOLOv9: Learning What You Want to Learn Using Programmable Gradient Information]([https://github.com/WongKinYiu/yolov9](https://arxiv.org/pdf/2402.13616)) | arxiv | 2024 | https://github.com/WongKinYiu/yolov9 | 2024.4.8 |































# 小目标检测
  小目标检测是计算机视觉领域中的一个挑战性课题，尤其因为在图像中这些目标通常分辨率低、对比度差、易受噪声影响。
## 小目标检测改进方法
### 数据增强：
  通过旋转、缩放、剪切、颜色变换等手段增加训练样本的多样性，使模型能够学习到更泛化的特征，提高对小目标的检测能力。
### 特征金字塔网络（FPN）：
  构建特征金字塔，使得网络能够在多个尺度上检测目标，从而提高对小目标的检测性能。
### 锚框优化：
  针对小目标设计更小的锚框（anchor boxes），或者调整锚框的生成策略，以更好地适应小目标的尺寸。
### 注意力机制：
  引入注意力模块，如SENet（Squeeze-and-Excitation Networks）或Non-local Neural Networks，帮助网络集中学习小目标的关键特征。
### 上下文信息利用：
  利用目标周围的上下文信息来辅助检测，例如，在图像中，一个很小的飞机可能周围有大量的天空，利用这种上下文关系可以提高检测的准确性。
### 多尺度训练和检测：
  在训练和测试时，将图像进行多尺度处理，提供不同尺度的输入给检测网络，以提高检测不同尺寸小目标的能力。
### 高级图像处理：
  在检测之前对图像进行去噪、增强对比度、调整亮度等预处理，以突出小目标特征。
### 深度学习模型的选择和优化：
  选择适合小目标检测的网络结构，如RetinaNet、Faster R-CNN with FPN等，并根据任务特点进行模型参数的调整和优化。
### 损失函数的改进：
  使用更适合小目标检测的损失函数，例如，Focal Loss是为了解决类别不平衡问题而设计的，特别适合于小目标的检测。
### 模型集成：
  训练多个模型并在测试时进行集成，可以综合各个模型的优点，提高检测的鲁棒性和准确性。
### 实时检测框架：
  对于实时性有要求的场景，可以通过模型剪枝、量化、知识蒸馏等方法减小模型大小，降低计算复杂度，以满足实时检测的需求。
### 目标跟踪：
  在视频序列中，利用目标跟踪算法对小目标进行连续跟踪，可以提高检测的稳定性和准确性。

## 2023.11.15汇报内容
### 论文1：Adaptive multiscale feature for object detection（目标检测的自适应多尺度特征）
为了解决FPN+的单向特征融合问题，提出了一种双向特征融合模块AMF。为了证明提出的方法是有效的，进行了大量的实验。实验结果表明，该方法对无锚框检测器和基于锚框检测器都是有效的。
### 论文2：An effective method for small object detection in low-resolution images(低分辨率图像中小目标检测的一种有效方法)
* 指出了YOLOF算法在低分辨率小目标检测中的局限性，提出了一种简单有效的YOLOFs算法。设计了三个增强小目标检测能力的关键模块，并与YOLOF进行了比较。
* 提出特征融合模块丰富了对象的语义信息和特征表示，视觉感知模块捕获感兴趣的实例，特征编码模块扩展了感受野减少了计算复杂度和参数。
* 在COCO, VOC和Fire数据集上进行了丰富的实验，将YOLOFs与其他最先进的检测器进行了比较，并证明了所提出的方法更有效。在没有附加条件的情况下，YOLOFs在精度上完全超过了YOLOF，特别是在COCO数据集上608 × 608像素的小目标检测精度提高了6.2 AP。
## 2023.12.13汇报内容
### 论文1：Small Object Detection via Coarse-to-fine Proposal Generation and Imitation Learning(基于粗到精建议生成和模仿学习的小目标检测)
* 提出了Coarse-to-fine RPN(CRPN)来提供充足的高质量的proposals，主要是通过动态的anchor选择机制和级联回归来实现。
* 然后还给传统的检测头装备了一个特征模仿分支来促进那些让模型感到迷惑的小目标的特征信息。并用一个遵循有监督对比学习范式的辅助损失函数来优化这个分支。
## 2024.1.3汇报内容
### 论文1：HIC-YOLOv5: Improved YOLOv5 For Small Object Detection（改进的YOLOv5小目标检测）
* 附加的SODH预测头是专门为小物体设计的。它在高分辨率的特征图中检测物体，这些特征图包含更多关于微小物体的信息。 
* 在主干网络和颈部网络之间增加内卷积(involution block)，从而增加特征映射的通道信息。
* 在主干网络的末端应用CBAM，可以提取更重要的通道信息和空间信息，而忽略冗余信息。
### 论文2：Field-matching attention network for object detection（用于目标检测的场匹配注意网络）   
* 提出了一种名为接收域扩展模块(RFDM)，用于在特征金字塔网络的不同层级之间调整接收域大小，从而提高特征融合的效果。
* 双注意力模块(DAM)：该模块结合了空间注意力和通道注意力，用于增强特征金字塔网络中较浅层特征的表示能力，并捕获更多的空间细节信息。
* 将RFDM和DAM模块集成到特征金字塔网络中，形成了一个名为FMANet的端到端目标检测网络结构。
* 在PASCAL VOC和MS COCO数据集上对FMANet进行了验证，结果显示该网络结构相比一些经典的目标检测方法具有更高的检测精度。通过Ablation实验分析了RFDM和DAM模块的互补性，验证了两者结合能获得更好的性能。FMANet是一个可插拔的模块，能够集成到基于特征金字塔网络的多种检测网络结构中，具有广泛的应用潜力。
## 2024.4.8汇报内容
### 论文1：GhostFormer: Efficiently amalgamated CNN-transformer architecture for object detection（GhostFormer:用于目标检测的高效合并CNN-transformer架构）
* 提出了一种基于CNN-Transformer混合特征提取网络的轻量级目标检测模型GhostFormer，该模型在目标检测中找到了计算成本和检测精度之间更好的平衡点，并在Pascal VOC和MS COCO中取得了具有竞争力的结果。
* 结合CNN和Transformer的优点，设计了轻量级卷积块(Lightweight Convolution block, LCB)和轻量级transformer块(Lightweight Transformer block, LTB)，有效降低了模型的计算成本，在目标检测中表现出良好的泛化性能。本文从CNN-Transformer的角度出发，探索了一种新的模型设计思路，对网络轻量化设计进行了新的尝试。
### 论文2：YOLOv9: Learning What You Want to Learn Using Programmable Gradient Information（YOLOv9:使用可编程梯度信息学你想学的）
* 从可逆函数的角度对现有的深度神经网络架构进行了理论分析，并通过这个过程成功地解释了许多过去难以解释的现象。在此基础上，还设计了PGI和辅助可逆分支，并取得了良好的效果。
* 设计的PGI解决了深度监督只能用于极深度神经网络架构的问题，从而使新的轻量级架构能够真正应用于日常生活。
* 设计的GELAN仅使用传统卷积，比基于最先进技术的深度卷积设计实现了更高的参数使用率，同时显示出轻、快、准确的巨大优势。
* 将所提出的PGI和GELAN相结合，YOLOv9在MS COCO数据集上的目标检测性能在各个方面都大大超过了现有的实时目标检测器。
## 2024.4.24汇报内容
### 论文1：RFLA: Gaussian Receptive Field based Label Assignment for Tiny Object Detection（基于高斯接受场的微小目标检测标签分配）
* 实验表明，当前基于锚框和无锚框的检测器在微小目标标签分配中存在尺度样本不平衡问题。
* 为了缓解上述问题，引入了一种简单但有效的基于感受野的标签分配（RFLA）策略。RFLA很容易取代主流检测器中的标准盒和基于点的标签分配策略，提高了它们在TOD上的性能。
* 在四个数据集上的大量实验验证了提出的方法的性能优越性。在具有挑战性的AI-TOD数据集上，引入的方法在推理阶段没有额外成本的情况下显著优于最先进的竞争对手。
### 论文2：GhostNet: More Features from Cheap Operations(GhostNet:更廉价的操作获得更多的特征)
* 高计算成本问题：提出Ghost Module，通过少量卷积核生成少量内在特征图，然后利用线性变换生成更多的特征图，以减少参数量和计算量。
* 特征图冗余问题：Ghost Module通过学习内在特征图和特征图之间的映射关系，能够生成具有相似信息但计算成本更低的特征图，从而减少冗余计算。
* 速度和精度的权衡问题：基于Ghost Module构建的GhostNet可以在降低计算成本的同时保持较高的识别精度，在速度和精度之间取得平衡。








