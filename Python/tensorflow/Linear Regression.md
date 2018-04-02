#Linear Regression
## 소스코드
<pre><code>import tensorflow as tf

x_data = [1,2,3]
y_data = [1,2,3]

W = tf.Variable(tf.random_uniform([1], -1.0, 1.0))
b = tf.Variable(tf.random_uniform([1], -1.0, 1.0))

hypothesis = W * x_data + b

cost = tf.reduce_mean(tf.square(hypothesis-y_data))

a = tf.Variable(0.1)
optimizer = tf.train.GradientDescentOptimizer(a)
train = optimizer.minimize(cost)

init = tf.initialize_all_variables()

sess = tf.Session()
sess.run(init)

for step in range(1001):
    sess.run(train)
    if step % 50 ==0:
        print(step, sess.run(cost), sess.run(W), sess.run(b))
</code></pre>

<pre><code>WARNING:tensorflow:From C:\project\common\Python\Python35\lib\site-packages\tensorflow\python\util\tf_should_use.py:107: initialize_all_variables (from tensorflow.python.ops.variables) is deprecated and will be removed after 2017-03-02.
Instructions for updating:
Use `tf.global_variables_initializer` instead.
2018-04-02 17:22:04.806364: I C:\tf_jenkins\home\workspace\rel-win\M\windows\PY\35\tensorflow\core\platform\cpu_feature_guard.cc:137] Your CPU supports instructions that this TensorFlow binary was not compiled to use: AVX AVX2
0 0.057105657 [0.7493387] [0.62468493]
50 0.0047732485 [0.9197578] [0.1824095]
100 0.00041884196 [0.9762305] [0.05403358]
150 3.6751957e-05 [0.99295896] [0.01600591]
200 3.224963e-06 [0.9979143] [0.00474128]
250 2.8295997e-07 [0.9993822] [0.00140441]
300 2.4818883e-08 [0.999817] [0.00041601]
350 2.1767097e-09 [0.99994576] [0.00012324]
400 1.9014597e-10 [0.9999839] [3.6489368e-05]
450 1.7057763e-11 [0.99999523] [1.0819629e-05]
500 1.558457e-12 [0.99999857] [3.166394e-06]
550 9.473903e-14 [0.9999996] [9.3320733e-07]
600 1.8947807e-14 [0.9999998] [4.563705e-07]
650 0.0 [1.] [5.9006e-08]
700 0.0 [1.] [5.9006e-08]
750 0.0 [1.] [5.9006e-08]
800 0.0 [1.] [5.9006e-08]
850 0.0 [1.] [5.9006e-08]
900 0.0 [1.] [5.9006e-08]
950 0.0 [1.] [5.9006e-08]
1000 0.0 [1.] [5.9006e-08]
</code></pre>
