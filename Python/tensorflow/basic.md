# Tensorflow basic
## Tensorflow 기본 동작(text 출력)

<pre><code>import tensorflow as tf
hello = tf.constant('hello')

print(hello)

sess = tf.Session()

print(sess.run(hello))
sess.close()
</code></pre>

<pre><code>Tensor("Const:0", shape=(), dtype=string)
2018-04-02 17:09:51.413863: I C:\tf_jenkins\home\workspace\rel-win\M\windows\PY\35\tensorflow\core\platform\cpu_feature_guard.cc:137] Your CPU supports instructions that this TensorFlow binary was not compiled to use: AVX AVX2
b'hello?'
</code></pre>

## Tensorflow 기본 동작(숫자연산)

<pre><code>import tensorflow as tf
a = tf.constant(2)
b = tf.constant(3)
c = a+b

print(c)

sess = tf.Session()

print(sess.run(c))

sess.close()
</code></pre>

<pre><code>Tensor("add:0", shape=(), dtype=int32)
2018-04-02 17:15:05.298996: I C:\tf_jenkins\home\workspace\rel-win\M\windows\PY\35\tensorflow\core\platform\cpu_feature_guard.cc:137] Your CPU supports instructions that this TensorFlow binary was not compiled to use: AVX AVX2
5
</code></pre>

## Tensorflow 기본 동작(숫자연산/placeholder사용)

<pre><code>import tensorflow as tf
a = tf.placeholder(tf.int16)
b = tf.placeholder(tf.int16)

add = tf.add(a, b)
mul = tf.multiply(a, b)

with tf.Session() as sess:
    print("Addition wuth variables: %i" %sess.run(add, feed_dict={a:2, b:3}))
    print("Multiplication with variables: %i" %sess.run(mul, feed_dict={a:2, b:3}))
sess.close()
</code></pre>

<pre><code>2018-04-02 17:16:54.678746: I C:\tf_jenkins\home\workspace\rel-win\M\windows\PY\35\tensorflow\core\platform\cpu_feature_guard.cc:137] Your CPU supports instructions that this TensorFlow binary was not compiled to use: AVX AVX2
Addition wuth variables: 5
Multiplication with variables: 6
</code></pre>


