# smart-home-abnormal-event-detection
# v1 2020.1.14  created by  wanghao

本项目应用智能家居的异常事件检测

本项目保存为ipynb格式，使用Python语言编写
需要的环境为 大于或等于python3.6.5 的编译环境

需要安装的包有：
numpy  pandas  和tqdm


事件的原始输入为 event_result.log

待检测的异常事件在文件： attacked_rub_house_from_window_new.csv当中

为了方便一些代码的书写，将事件对应的id存在了event2id.json当中

三个模块运行的顺序为：

1 statistic_by_state_and_event.ipynb

这一模块用来对原始智能家居事件数据集进行概率统计，得到全部事件的转移概率矩阵，存储在event_trans_pro.npy当中


2 get_attack_from_orignal.ipynb

这一模块用来生成一个跳窗入室抢劫的异常序列，结果保存在attacked_rub_house_from_window_new.csv当中


3 detect_by_weight.ipynb

这一模块的作用是使用第一个模块的统计得到的转移概率矩阵，来检测第二个模块当中生成的异常事件序列


最终通过分割，生成16个事件子序列，而包含异常事件的子序列位于第11个，被第三个模块检测出异常
