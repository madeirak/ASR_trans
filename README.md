# ASR_combination

分别参考了两个开源项目，声学模型是cnn+ctc，语言模型是2-gram（[使用不分词词频统计方法](https://blog.ailemon.me/2017/04/27/statistical-language-model-chinese-pinyin-to-words/)） ，解码使用维特比算法。

对两个模型都有一定程度上的改进：
2-gram超低频词间过渡处理(比如，“迷彩背包”的“彩背”，声学模型单个错误拼音如“mí cāi shū bāo”)

声学模型的输出是“kǎo yán yān yǔ cí huì”  时，因为“yān”会使连同之前的三个拼音的联合概率过低，低于设定阈值，被丢弃，只输出“语词汇”，造成理解困难。
修改后的2-gram会输出“ 考研烟语词汇 ”，不会造成词语的丢失。

增加了transformer的中英翻译模型，把结果再翻译成英文，大杂烩:)

[参考声学模型项目](https://github.com/audier/DeepSpeechRecognition)
[参考语言模型项目](https://github.com/madeirak/ASRT_SpeechRecognition)
