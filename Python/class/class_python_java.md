#  Python과 Java의 클래스 생성 비교
## Python에서의 클래스 생성
<pre><code>class Test_class:
    def set_info(self, name, age, gender):
        self.name = name
        self.age = age
        slef.gender = gender
    def print_info(self):
        print('name : ', self.name)
        print('age : ', self.age)
        print('gender : ', self.gender)
</code></pre>
<pre><code>TC = Test_class()
TC.set_info('김인턴',25,'남자')
TC.print_info()
</code></pre>
<pre><code>name :  김인턴
age :  25
gender :  남자
</code></pre>

