  #### 一、任务要求：
  最近工作，要求从pdf文本中抽取特定名字的参数值，这些参数包括：数值，名词，一些描述。。。
  
  #### 二、方案选择：
  - word2vec
  - 深度学习的完形填空，信息抽取的办法
  - NER
  - 搜索
  
  #### 三、最终方案
  最后选择了搜索，原因是：
  - 这些pdf就十几个，就这点数据量，深度学习跑不起来，而且还要人工标注
  - word2vec，本来打算用参数名的词向量和每个句子计算相似度，然后从句子里面抽取参数。但是，我们这是专业领域，词向量必须自己训练，训练数据从哪里来？放弃
  - NER，对命名实体识别报以很大期望，希望用它直接抽出答案。但是，现有的NLP中NER大约都是地名、机构名等训练的，专业领域中那些拗口的名词根本无法识别。
  - 那就只能选搜索了。
  
  #### 四、怎么做的搜索？
  1. 把文本做成一个以句子为单位的list
  2. 利用自定义词典分词，把list做成倒排表
  3. 为每个参数值提出几个搜索关键词
  4. 利用这些搜索关键词在倒排表中找，哪个句子关键词包含的多，哪个句子的排序就优先
  5. 提出一些参数的与或非逻辑关系，选出一个句子
  6. 利用正则把参数值提取出来。
  
  #### 五、效果
  效果不错，精确程度取决于参数的搜索关键词。
  
