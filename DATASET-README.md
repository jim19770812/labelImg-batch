# 教程
## 数据集的格式
datasets/<你的数据集名字>/<你的数据集名字>.yaml    #可以用于训练的数据集配置文件
datasets/<你的数据集名字>/images/train             #训练用的图片文件
datasets/<你的数据集名字>/images/val               #验证用的图片文件
datasets/<你的数据集名字>/images/test              #测试用的图片文件
datasets/<你的数据集名字>/labels/train             #训练图片对应的的标注文件，yolov5格式
datasets/<你的数据集名字>/labels/val               #验证图片对应的的标注文件，yolov5格式
datasets/<你的数据集名字>/labels/test              #验证图片对应的的标注文件，yolov5格式
datasets/<你的数据集名字>/labels/classes.txt       #labelImg标注时生成的分类列表文件

1.工具
1.1.创建空白数据集
1.2.检查数据集格式是否有效，特别是验证训练图片和训练标注是否一致，遇到不一致会返回一个差异报告

2.数据集
2.1.创建数据集，如果数据集没有会自动创建，按照设置的比例从来源目录把图片按照比例分成训练/验证/测试用途，如果有标注文件也一起复制

--root=/home/jim/source/pytorch/deep-learn3/datasets --ds=givvy-shorts --create-dataset --src=/home/jim/source/pytorch/deep-learn3/datasets/test --ratio=7,2,1
--root=/home/jim/source/pytorch/deep-learn3/datasets --ds=givvy-shorts --empty
--root=/home/jim/source/pytorch/deep-learn3/datasets --ds=givvy-shorts --check
--root=/media/jim/0f31b817-3cd1-47d9-9f5c-c1f37e27255f/earn-works/datasets --ds=givvy-shorts --create-dataset --src=/media/jim/0f31b817-3cd1-47d9-9f5c-c1f37e27255f/earn-works/datasets/givvy-shorts-resources/train/ --ratio=7,2,1
--root=/media/jim/0f31b817-3cd1-47d9-9f5c-c1f37e27255f/earn-works/datasets --ds=givvy-shorts --check


## 用法

### 图片的路径
操作labelImg打开目录所指向的目录，标注保存目录要和图片目录保持一致

### 标注数据
操作labelImg改变存放目录需要指向的目录
datasets/<你的数据集名字>/labels/train             #训练图片对应的标注文件
datasets/<你的数据集名字>/labels/val               #验证图片对应的标注文件

### 标注
用labelImg标注，需要把数据类型从默认的PascalVOC改成YOLO

### 批量对所有图片生成标注
需要实现对图片进行分类，确保每个目录下的图片都是同一类，适配批量标注

### 生成数据集
$ .venv/bin/python dsutils.py --root=/home/jim/source/pytorch/deep-learn3/datasets --ds=ds1 --create-dataset --src=/data/images --ratio=7,2,1
在生成之前，数据集里要有图片和标注数据
标注完成后用dsutils.py生成数据集配置文件(.yaml)，之后就可以训练了
