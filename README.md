# cs224n
This is my solution to Standford [CS224n: Natural Language Processing with Deep Learning](http://web.stanford.edu/class/cs224n/syllabus.html)
No guarantee to be all correct. Do let me know if there's any mistakes.

I haven't finished the entire video lectures but finished reading the lecture notes. [cs231n](https://cs231n.github.io/) has some more interesting aspects to explore.

### ASSIGNMENT 1
In order to understand the Word2vec model, concrete samples are needed. This [link](https://www.analyticsvidhya.com/blog/2017/06/word-embeddings-count-word2veec/) helps for providing a conrete example. Excel is very useful in POC.

### ASSIGNMENT 2
Embedding tensor with pretrained_embeddings is a bit tricky. 
More hints:
1. Create a tensor variable using [tf.Variable](https://www.tensorflow.org/api_docs/python/tf/Variable).
2. Initialize it with the pretrained_embeddings
3. Use the tf.nn.embedding_loop to index the variable tensor created in step 1.

### ASSIGNMENT 3
Gradient clip should be done in the following way as discussed this [Stackoverflow](https://stackoverflow.com/questions/36498127/how-to-effectively-apply-gradient-clipping-in-tensor-flow)
~~~~
gradients, variables = zip(*optimizer.compute_gradients(loss))
gradients, _ = tf.clip_by_global_norm(gradients, 5.0)
optimize = optimizer.apply_gradients(zip(gradients, variables))
~~~~
