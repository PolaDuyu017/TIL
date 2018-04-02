# Linear Regression
## 손실함수를 이용하여 가중치(W)와 편향(b)를 구하는 소스코드
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

init = tf.global_variables_initializer()
# init = tf.initialize_all_variables()   구버전

sess = tf.Session()
sess.run(init)

for step in range(1001):
    sess.run(train)
    if step % 50 ==0:
        print(step, sess.run(cost), sess.run(W), sess.run(b))
</code></pre>

<pre><code>2018-04-02 17:22:04.806364: I C:\tf_jenkins\home\workspace\rel-win\M\windows\PY\35\tensorflow\core\platform\cpu_feature_guard.cc:137] Your CPU supports instructions that this TensorFlow binary was not compiled to use: AVX AVX2
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

## 손실함수를 이용하여 가중치(W)와 편향(b)를 구하는 소스코드(placeholder 적용)
<pre><code>import tensorflow as tf

x_data = [1.,2.,3.]
y_data = [1.,2.,3.]

W = tf.Variable(tf.random_uniform([1], -1.0, 1.0))
b = tf.Variable(tf.random_uniform([1], -1.0, 1.0))

X = tf.placeholder(tf.float32)
Y = tf.placeholder(tf.float32)


hypothesis = W * X + b

cost = tf.reduce_mean(tf.square(hypothesis-Y))

a = tf.Variable(0.1)
optimizer = tf.train.GradientDescentOptimizer(a)
train = optimizer.minimize(cost)

init = tf.global_variables_initializer()
# init = tf.initialize_all_variables()   구버전

sess = tf.Session()
sess.run(init)

for step in range(2001):
    sess.run(train, feed_dict={X:x_data, Y:y_data})
    if step % 20 ==0:
        print(step, sess.run(cost, feed_dict={X:x_data, Y:y_data}), sess.run(W), sess.run(b))

print(sess.run(hypothesis, feed_dict={X:5.0}))
print(sess.run(hypothesis, feed_dict={X:2.5}))
</code></pre>

<pre><code>2018-04-02 17:25:56.943609: I C:\tf_jenkins\home\workspace\rel-win\M\windows\PY\35\tensorflow\core\platform\cpu_feature_guard.cc:137] Your CPU supports instructions that this TensorFlow binary was not compiled to use: AVX AVX2
0 0.2794612 [0.5685705] [1.2570336]
20 0.07965017 [0.6722148] [0.7451328]
40 0.030093962 [0.79851824] [0.45801544]
60 0.011370323 [0.8761539] [0.2815312]
80 0.004296012 [0.92387474] [0.17305055]
100 0.0016231484 [0.9532076] [0.10637004]
120 0.0006132686 [0.97123784] [0.06538317]
140 0.00023171004 [0.98232055] [0.0401895]
160 8.754605e-05 [0.9891329] [0.02470355]
180 3.3077216e-05 [0.9933202] [0.01518468]
200 1.2497665e-05 [0.995894] [0.00933364]
220 4.7216568e-06 [0.9974762] [0.00573723]
240 1.7840812e-06 [0.99844867] [0.00352653]
260 6.7403107e-07 [0.99904644] [0.00216764]
280 2.547359e-07 [0.99941385] [0.00133238]
300 9.620553e-08 [0.9996397] [0.00081896]
320 3.6350368e-08 [0.99977857] [0.0005034]
340 1.3725095e-08 [0.99986386] [0.00030938]
360 5.183002e-09 [0.9999164] [0.00019015]
380 1.959999e-09 [0.9999486] [0.0001169]
400 7.440046e-10 [0.9999684] [7.184855e-05]
420 2.803565e-10 [0.9999805] [4.412842e-05]
440 1.0588034e-10 [0.9999881] [2.714507e-05]
460 4.0055664e-11 [0.9999926] [1.6662598e-05]
480 1.5101401e-11 [0.99999547] [1.027298e-05]
500 5.6464464e-12 [0.99999726] [6.299338e-06]
520 2.2926845e-12 [0.9999983] [3.875416e-06]
540 9.284425e-13 [0.999999] [2.4051687e-06]
560 3.2684966e-13 [0.99999934] [1.4753366e-06]
580 9.473903e-14 [0.9999996] [8.8723795e-07]
600 6.158037e-14 [0.99999964] [6.806087e-07]
620 6.158037e-14 [0.99999976] [5.534522e-07]
640 3.7895614e-14 [0.99999994] [3.0708625e-07]
660 4.7369517e-15 [0.99999994] [1.2429858e-07]
680 0.0 [1.] [5.277301e-08]
700 0.0 [1.] [5.277301e-08]
720 0.0 [1.] [5.277301e-08]
740 0.0 [1.] [5.277301e-08]
760 0.0 [1.] [5.277301e-08]
780 0.0 [1.] [5.277301e-08]
800 0.0 [1.] [5.277301e-08]
820 0.0 [1.] [5.277301e-08]
840 0.0 [1.] [5.277301e-08]
860 0.0 [1.] [5.277301e-08]
880 0.0 [1.] [5.277301e-08]
900 0.0 [1.] [5.277301e-08]
920 0.0 [1.] [5.277301e-08]
940 0.0 [1.] [5.277301e-08]
960 0.0 [1.] [5.277301e-08]
980 0.0 [1.] [5.277301e-08]
1000 0.0 [1.] [5.277301e-08]
[5.]
[2.5]
</code></pre>
