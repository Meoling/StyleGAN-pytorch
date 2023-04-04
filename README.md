# Style-Based GAN in PyTorch

github库地址：[GitHub - rosinality/style-based-gan-pytorch: Implementation A Style-Based Generator Architecture for Generative Adversarial Networks in PyTorch](https://github.com/rosinality/style-based-gan-pytorch)

## 用法

环境：pytorch常用环境即可

### 数据集

**采用lmdb数据集，坦克数据集已经准备好，~~在pic文件夹中~~在总目录处下载到pic文件夹。**

如果需要制作自己的数据集，命令行命令如下

> python prepare_data.py --out LMDB_PATH --n_worker N_WORKER DATASET_PATH

### 训练

命令行cd到库文件夹下运行如下命令

> python train.py --mixing --loss r1 --sched --phase 50000 --ckpt checkpoint/train_step-7.model pic 2>&1 | tee train_log.txt

phase参数控制每一个阶段的训练次数，原代码默认3,000,000次，我自己设定50000次训练时间还是较长，可根据情况酌情调整。

ckpt参数为预训练模型，地址自行更改。

---

## 资源

人脸预训练模型

| Resolution | Model & Optimizer                                            |
| ---------- | ------------------------------------------------------------ |
| 256px      | [Link](https://drive.google.com/open?id=1QlXFPIOFzsJyjZ1AtfpnVhqW4Z0r8GLZ) |
| 512px      | [Link](https://drive.google.com/open?id=13f0tXPX0EfHdac0zcudfC8osD4OdsxZQ) |
| 1024px     | [Link](https://drive.google.com/open?id=1NJMqp2AN1de8cPXTBzYC7mX2wXF9ox-i) |

FFHQ人脸图像数据集 [Link](https://drive.google.com/uc?id=13f0tXPX0EfHdac0zcudfC8osD4OdsxZQ)

# 测试

> python generate.py checkpoint/train_step-8.model