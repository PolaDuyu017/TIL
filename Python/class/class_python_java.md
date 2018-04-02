#  Python과 Java의 클래스 생성 비교
## Python에서의 클래스 생성
<pre><code>class test_class:
    def set_info(self, name, age, gender):
        self.name = name
        self.age = age
        slef.gender = gender
    
    def print_info(self):
        print('name : ', self.name)
        print('age : ', self.age)
        print('gender : ', self.gender)
</code></pre>

<pre><code>TC = test_class()
TC.set_info('김인턴',25,'남자')
TC.print_info()
</code></pre>

<pre><code>name :  김인턴
age :  25
gender :  남자
</code></pre>

## Java에서의 클래스 생성

<pre><code>class TestClass{
    String name = "";
    int age = 0;
    String gender = "";
    
    void SetInfo(String name, int age, String gender){
        this.name = name;
        this.age = age;
        this.gender = gender;
    }
    
    void PrintInfo(){
        System.out.println("name : "+this.name);
        System.out.println("age : "+this.age);
        System.out.println("gender : "+this.gender);
    }
}
</code></pre>
<pre><code>class TestStart{
    public static void main(String args[]) {
	TestClass TC = new TestClass();
	TC.SetInfo("김인턴", 25, "남자");
	TC.PrintInfo();
	}
}
</code></pre>

<pre><code>name :  김인턴
age :  25
gender :  남자
</code></pre>
