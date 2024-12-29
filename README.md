#yolov5识别快捷包使用声明
图片的批量命名用其他工具即可。
作为一个不是很专业的集合包，改包为初步训练成果，此包为半成品包修改而成，且未调教识别精度，仅仅一般识别精度。另附：dataset.py和train.py不建议非专业人士大改，由dataset运行仅第一条，无反应之谈。train.py494行小改。

此包作为快捷使用包，故特殊点为脚本使用提高了一定的便携性。
使用顺序：dataset文件夹下有train训练集，里面是存放图片的位置，放心存放图片，然后使用labelme框选物体的json文件会默认保存到这里，不要慌张，只需要把它们json文件剪切到json名的文件夹当中。 当然，备份是一种好习惯，可以把一些材料放入zhunbei文件夹当中，然后我们就可以开始了。
1.json文本转换成yolo的文件格式（txt）,那么你就运行boat.py文件，然后文本会放在txtrds文件夹当中。2.图片数量需要和标签数量，还有他们的名称需要对应，很麻烦，但是不要慌张，运行imageManger.py,仅仅会把训练集train里面的图片随机复制到验证集val下（按比例）。那么同样的，训练集的文本文件夹和验证集的文本文件夹下面也要有跟图片同名的txt文件。训练路径：D:\PyCun\xiaoxueqi\yololite\team\dataset\train\labels  验证路径：D:\PyCun\xiaoxueqi\yololite\team\dataset\val\labels 。
那么就得运行latroYun.py文件，它会把txt文件夹的文本复制到dataset\txtManager文件夹当中（这个文件夹应该得留着），或者有时不中转到这个地方（没问题），然后对于txtrds文件夹，train\images文件夹val\images文件夹，它会复制文本到对应的labels文件夹，然后把匹配不了的图片和文本丢进对应的、起名很明显的文件夹当中，目前没发现这些文件夹会导致错误，另外会有对应的yaml文件生成，记得检查里面的路径和nc数量。
然后fanlabel.py文件会给每个文本文件夹产生labels，dataset文件夹是否需要labels没有感觉到差异。
另外就是train.py的配置，使用权重文件一定要记得使用配套的yaml文件，并且把其中nc数量修改正确，与自己运行脚本产生的screentrain.yaml数量一致。这里只尝试v5lite-c.pt并且450轮以上成功。精度与训练轮数有关，而非启动train.py的次数。要提升精度就多框图，框细一点。
tryDetect.py检验训练的权重效果（记得改路径到runs)pipi文件夹为导出给树莓派使用。 train.py里使用gpu“0”，可自己修改。
该使用包为2024年暑假的异遗物。
