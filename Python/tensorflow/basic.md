# Tensorflow basic
## Tensorflow 기본 동작

<pre><code>import tensorflow as tf

hello = tf.constant('hello?')

print(hello)

sess = tf.Session()

print(sess.run(hello))
sess.close()
</code></pre>

출력값
<pre><code>Tensor("Const:0", shape=(), dtype=string)
2018-04-02 17:09:51.413863: I C:\tf_jenkins\home\workspace\rel-win\M\windows\PY\35\tensorflow\core\platform\cpu_feature_guard.cc:137] Your CPU supports instructions that this TensorFlow binary was not compiled to use: AVX AVX2
b'hello?'
</code></pre>
