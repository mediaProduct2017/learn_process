# learn-process

190103: 在程序中调用api时，要想好当api调用失败时（比如因网络问题）应该怎么处理，是自己处理呢，还是抛出异常让调用者处理呢

190106：学习bert等模型的意义有二，第一，bert是一个学术上的模型，在工业应用时，还需要进一步的优化；第二，bert被google开源了，所以大家都可以用了，但如果以后大厂不再开源，一般公司与大厂的差距就会越来越大，最后就是小学生与大学生的差距，在这种情况下，必须用心搞研究或者去大厂搞研究。在移动互联网时代，不同公司的技术差距是很小的，技术逻辑还是比较简单，差距最多是大学生和研究生的差距，所以大家都有机会。

190108: 当用简单的平均或者加和方法由词向量求句向量的时候，平均或者加和各有优势。因为经常需要把句子补成一样的长度，也就是在最后加0，或者因为有词表中没有的单词，词向量也用0代替。如果用加和的话，加0是没有影响的。但如果用平均的话，句子补的长度越长，句子中未知的词越多，分母也就越大，但分子并没有相应增大，也就是说，计算出向量的模会比实际值偏小。用求和的问题是，不容易理解，但实际上没问题，因为高维向量的cosine similarity主要是由方向决定的，向量模的影响不大（没必要求平均，但反过来说，求了平均也没事，不影响）。fasttext由词向量求句向量就是用的求和，不是用的平均。tensorflow中用的是tf.reduce_sum()，reduce的意思是可以降维，所以有axis参数，决定从哪个方向降维。

更准确的说，反正计算cosine similarity的时候，向量要normalize成模为1的向量，所以向量的模并不重要，所以不管是tf.reduce_mean()还是tf.reduce_sum()，结果都是一样的。tf.reduce_mean()更容易理解，tf.reduce_sum()计算时步骤更少，更省时间。

如上所说，用mean和用sum没有大的差异，但微小差异还是有的，很多paper表示，mean的效果最好。
