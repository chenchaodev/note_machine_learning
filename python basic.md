##基础

###输入和输出
    print("hello, world")
    print("hello,", "world")
    print('300 + 200',  300 + 200)
    name = input()

###常见数据类型
    - 整数
        1， -8080， 0， 0xff00 （十六进制）
    - 浮点数
        1.23，3.14,1.23e10，1.2e-5
    - 字符串
        print('I\'m learning \nPython')
        print(r'\\\t\\') （r' ' 不转义）
        print('''line1
        ...line2''')     （'''...'''表示多行内容）
        print('''line1
        line2
        line3''')
    - BOOL
        True 
        False
        and or not
    - None
    - 变量
        a = 2
    - 常量
        PI = 3.1415926 （全部大写）
        10/3 = 3.333
        10//3 = 3

###字符串和编码
    - Python 3，Unicode格式
    - 字符转换
        ord()
        chr()
    - 占位符
        %d %f %s %x

### list 和 tuple
- list
        classmates = ['Mike', 'Bob', 'Tracy']
        len(classmates)
        classmates[0]
        classmates[-1]
        classmates.append('Adam')
        classmates.pop()
        classmates.pop(i)
        classmates[1] = 'Sarah'
        classmates.insert(i, value)
- tuple
    不能修改，没有 append() inser() pop() 方法
        classmatesTuple = ('Mike', 'Bob', 'Tracy')
        t = ()
        t = (1, ) '''需要注意，因为（）有两重意义，如果无，悔产生歧义）
        
###条件判断
    age = 3
    if age >= 18:
        print('adult')
    elif age >-0:
        print('teanager')
    else:
        print('kid')

### 循环
    sum = 0
    for x in range(101):
        sum += x
    print(sum)


    sum = 0
    n = 99
    while n >0:
        sum = sum + n
        n = n -2
    print sum

### dict
字符串、证书都可以作为key

    d = {'Michael': 95, 'Bob': 75, 'Tracy': 85}
    d['Michael']
    '''为防止不存在key，可以使用以下方法'''
    if 'Michael' in d:
        print(d['Michael'])
    d.get('Thomas')
    d.get('Thomas', -1)
    d.pop('Bob')

### set
一组key的集合，不存储value，在set中没有重复的key

    s = set([1, 2, 3])
    s.add(5)
    s.remove(5)
    s1 & s2 (交集）
    s1 | s2 （并集）

## 函数
###函数的调用和定义

    abs(100)
    
    def my_abs(x):
        if x >= 0:
            return x
        else:
            return -x

    def nop()
        pass

    import math
    def move(x,  y, step, angle=0):
        nx = x + step * math.cos(angle)
        ny = x + step * math.sin(angle)
        reutnr nx, ny

    x, y = move(100, 100, 60, math.pi /6)
    '''实际上，返回的是一个tuple值'''

### 函数的参数
默认参数在后

    def power(x, n=2):
        s = s
        while n >0:
            n = n -1
            s = s*x
        return s

可变参数

    def calc(*numbers):
        sum = 0
        for n in numbers:
            sum = sum + n * n
        reutnr sum
     
    cals(1, 2)

    nums = (1, 2, 3)
    clas(*nums)

关键字参数，扩展函数的功能

    def person(name, age, **kw):
        print(' name', name, 'other', kw)
        if 'city' in kw:
            pass
        if 'job' in kw:
            pass

    extra = {'city': 'Beijing', 'job': 'Enginear'}
    person('Jack', 23, **extra)

命名关键字参数，用*分割，可以有默认值

    def person(name, age, *, city, job):
        pass

    person('Jack', 24, city='Beijing', job= 'Engineer')

参数定义的顺序，必选参数、默认参数、可变/命名参数、关键字参数

    def f2(a, b, c=0 *, d, **kw):
        pass

    f2(1, 2, d=99, ext=None)
    args = (1, 2, 3)
    kw = {'d': 88, 'x': '#'}
    f2(*args, **kw)

###递归函数
    def fact(n):
        if n==1:
            return 1
        return n * fact(n-1)

使用时要防止栈溢出，需要通过尾递归优化（但python没有做尾递归优化，无用）

    def fact(n):
        return fact_iter(n, 1)
    
    def fact_iter(num, product):
        if num == 1;
            return product
        return fact_iter(num-1, num * product)

##高级特性

###切片
    L[0:3]
    L[-2:]
    L[-2: -1]
    L[ : ]
    my_tuple[:3]
    'abc'[0:1]

###迭代
    for key in my_dict:
        pass
    for ch in 'ABCDD':
        pass
    '''判断是否可以迭代'''
    from collections import Iterable
    isinstance('abc', Iterable)
    
    for i, value in enumerate(['A', 'b', 'c']):
        print(i, value)

###列表式生成
    a = list(range(1, 11))
    [x * x for x in range(1, 11) if x % 2 == 0]
    [m + n for m in 'ABC' for n in 'XYZ']

    b = {x *2 for x in a } # set

    c = [x * 2 for x in a] # list

    d = {x*2: x for x in a} # dict

    e = (x*2 for x in a) # generator




###生成器
generrator，保存的是算法

    g = (x * x for x in range(10))
    for n in g:
        print(n)

    def fib(max):
        n, a, b = 0, 0, 1
        while n < max:
            yield b '''重要，fib是个生成器了'''
            a, b = b, a + b
            n +=1
        return 'done'

### 迭代器
for循环使用范围，Iterable，
- list, tuple, dict, set, str
- generator //Iterator

##函数式编程

###基本

    def testFunc(x, func):
        return func(x)

    testFunc(-5, abs)

### map/reduce

    def f(x):
        return x * x

    r = map(f, [1, 2, 3])

    list(map(str, [1, 2, 3]))
    
    def f(x, y):
        pass
    reduce(f, [x1, x2, x3, x4]) = f(f(f(x1, x2), x3),x4)

str2int

    from functools import reduce
    def str2int(s)
        def fn(x, y):
            return 10 * x +y
        def char2num(s):
            return {'0': 0, '1': 1, '2': 2, '3': 3, '4': 4, '5': 5, '6': 6, '7': 7, '8': 8, '9': 9}[s]
    return reduce(fn, map(char2num, '13579'))

lambda 函数

    from functools import reduce
    def char2num(s):
         return {'0': 0, '1': 1, '2': 2, '3': 3, '4': 4, '5': 5, '6': 6, '7': 7, '8': 8, '9': 9}[s]

    def str2int(s):
    return reduce(lambdax, y: x * 10 + y, map(char2num, s))

###filter

    list(filter(lambda x: x % 2 == 1, list(range(10))))
    list(filter(lambda x: x % 2 == 1, range(10)))
    
    list(filter(lambda x: x and x.strip(), ['a', 'b ', None, 'c  ']))

素数筛选

    def _not_devisible(n):
        return lambad x: x%n > 0
    #生成器
    def primes():
        yield 2
        it = _odd_iter() # 初始序列
        while True:
            n = next(it)
            yield n 
            it = filter(_not_devisible(n)m it)

    for n in primes():
        if n < 1000:
            print(n)
        else:
            break

### sorted 排序算法

    sorted(my_list, key=abs)

    sorted(my_str_list, key=str.lower, reverse=True)

###返回函数

    def lazy_sum(*args):
        def sum():
            ax = 0
            for n in args:
                ax = ax + n
            return ax
        return sum

    f = lazy_sum(1, 3, 4, 5)
    f()

闭包

    def count():
        def f(j)
            def g():
                return j*j
        fs = []
        for i in range(1, 4):
            fs.append(f(i))
        return fs

    f1, f2 , f3 = count()
    
###装饰器

    def log(func):
        def wrapper(*args, **kw):
            print('call %s()', % func.__name__)
                ruturn func(*args, **kw)
        return wrapper

    @log
    def now():
        pass
    now.__name__

###偏函数

    import functools
    int2 = functools.partial(int, base=2)
    int('10000')

##模块

    #!/usr/bin/env python3
    #-*- coding: utf-8 -*-
    ' a test module'
    __author__ = 'Michael Liao'
    import sys
    
    def test():
        args = sys.argv
        if len(args) == 1:
            print('wordl')
        elif len(args) ==2:
            print(args[1])
        else:
            print('Too many arguments!')

    #在直接运行文件时才运行，其他文件导入时，不运行
    if __name__== '__main__'
        test()

外部不引用的函数定义为private， _private_sss()

第三方模块
    pypi.python.org
    pip install Pillow

运行时搜索目录为  sys.path，将自定义目录加入搜索目录

    import sys
    sys.path.append('/xxx/')

或者 修改环境变量 PYTHONPATH

##面向对象编程
###类和实例

    class Student(object):
        def __init__(self, name, score =0):
            self.__name = name
            self.__score = score

        def print_score(self):
            print('%s: %s', %(self,__name. __self,score))

        def get_name(self):
            return self.__name
        
        def get_score(self):
            return self.__score

        def set_score(self, score):
            if socre < 0 or score > 100:
                raise ValueError('bad score')
            self.__score = score

- `__x`是私有变量，不能访问，实际可以通过 _classname__x访问，但不推荐
- `__x__`是特殊变量，可以访问
- `_name` 可以访问，但按照约定，最好也不要访问

### 继承和多态

    class Animal(object):
        def run(self):
            pass

    class Dog(Animal):
        def run(self):
            pass

    dog = Dog()
    isinstance(dog, Dog)

    def run_twice(animal):
        animal.run()
        animal.run()

###获取对象信息

- type()
        type(123)
        type(None)
        type(dog)
        type(abs)
- isinstance()
- dir()
        getattr()
        stattr()
        hasattr()

###实例属性和类属性
    class Student(object):
        name = 'Student' #类属性，如实例没有name属性，则默认返回这个

##面向对象高级编程

### __slots__
- 动态绑定属性和方法
        class Student(object):            
            pass

        s = Student()
        s.name = 'Michael'

        def set_age(self, age)
            self.age = age
        from types import MethodType
        s.set_age = MethodType(set_age, s) # 给实例绑定
        Student.set_score = MethodType(set_score, Student)

- 闲置实例的属性，对子类不起作用
    class Student(object):
        __slots__ =  ('name', 'age')

### @roperty
    class Student(object):
 
        @property
        def birth(self):
        return self._birth
 
        @birth.setter
        def birth(self, value):
        self._birth = value
 
        @property
        def age(self):
        return 2015 - self._birth

###多重继承

    class Dog(Anamal, RunableMixIn, CarnivorousMixIn):
        pass

    class MyTcpServer(TCPServer, ForkingMixIn):
        pass

###定制类
- __str__ 更改print中的输出
- __iter__ 用于迭代，返回迭代队形，自动调用__next()，知道遇到StopIteration
        class Fib(Object):
            def __init__(self):
                self a, self, b = 0, 1

            def __iter__(self):
                return self

            def __next(self):
                self.a, self.b = self.b, self.a + self.b
                if self.a > 10000:
                    raise StopIteration()
                return self.a
- __getitem__ 利用下标，切片取数据
        class Fib(object):
            def __getitem__(self, n):
                if isinstance(n, int):
                    a, b = 1, 1
                    for x in range(n):
                        a, b = b, a+b
                    return a
                if isinstance(n, slice):
                    start = n.start
                    stop = n.stop
                    if start is None:
                        start = 0
                    a, b = 1, 1
                    L = []
                    for x in range (stop):
                        if x>= start:
                            L.append(a)
                        a, b = b, a+b
                    return L
- __getattr__ 重定向
        class Student(object):
            def __getattr__(self, attr):
                if attr == ’age':
                    return lambda: 25
- __call__ 直接对实例调用
        class Student(object):
            def __call__:
                pass

        s = Student()
        s()

        callable(Student)

###枚举法

    from enum import Enum, unique
    
    @unique
    class WeekEnd(Enum):
        Sun = 0
        Sat = 6

    day1 = Weekday.Sun
    Weekday['Sun']
    Weekday[0]

###使用元类
 type()

    def fn(self, name='world'):
        pass
    
    Hello = type('Hello', (object,), dict(hello=fn)) #创建Hello class
    h = Hello()
    h.hello()

metaclass()，先定义metaclass， 创建类，创建实例

    class ListMetaclass(type):
        def __new__(cls, name, bases, attrs):
            attrs['add'] = lambda self, value: self.append(value)
            return type.__new__(cls, name, bases, attrs)

    class MyList(list, metaclass=ListMetaclass): # 自动添加add方法
        pass

ORM "Object Relational Mapping" 对象关系映射
例子
    
    class User(Model):
        id = IntegerField('id')
        #...

其中父类Model和IntegerField由ORM框架提供，save等魔术方法由metaclass提供

    def FIeld(object):
        def __init__(self, name, column_type):
            self.name = name
            self.column_type = column_type

        def __str__(self):
            return '<%s: %s>' %(self.__class__.__name__, self.name)

    def StringField(Field):
        def __init__(self, name):
            super(StringField, self).__init__(name, 'varchar(100)')

    def IntegerField(Field):
        def __init__(self, name):
            super(IntegerField, self).__init__(name, 'bigint')

    class ModelMetaclass(type):
        def __new__(cls, name, bases, attrs):
            if name=='Model':
                return type.__new__(cls, name, bases, attrs)
            print('Found model %s' % name)
            mappings = dict()
            for k, v in attrs.items():
                if isinstance(v, Field):
                    print('Found mapping: %s ==> %s' %(k, v))
                    mappings[k] = v
            for k in mapping.keys():
                attrs.pop(k)
            attrs['__mapping__'] = mappings
            attrs['__table++'] = name
            return type.__new__(cls, name, bases, attrs)

    class Model(dict, metaclass= ModelMetaclass):
        
        def __init__(self, **kw):
            super(Model, self).__init__(**kw)

        def __getattr__(self, key):
            try:
                return self[key]
            except KeyError:
                raise AttributeError(r'''Model' object has no attribute '%s%'" %key)

        def __setattr__(self, key, value):
            self[key] = value

        def save(self):
            sql = 'insert into %s (%s) values (%s)' %(self.__table__, ','.join(fields), ','.join(params))
            

当用户定义一个class User(Model)时，Python解释器首先在User定义中寻找metaclass，如灭有，在父类中寻找，在ModelMetaclass中，排除了对Model的修改，在当前类中查找定义的属性，加入__mappings__中，同时从类属性中删除，把表名存储到__table__中

##错误、调试和测试

##IO编程

###文件读写
####读文件
    f = open('./test.txt', 'r')
    f.read()
    f.close()

    try:
        f = open('./test.txt', 'r')
        print(f.read())
    finally:
        if f:
            f.close()

    with open('./test.txt', 'r') as f:
        print(f.read())

    for line in f.readline():
        print(line.strip())

####file-like Object
有 read()方法的对象
####二进制
    f = open('./test.txt', 'rb')

####字符编码
    f = open('./test.txt', 'rb', encoding = 'gbk', error='ignor')

####写文件
    with open('./test.txt', 'w') as f:
        f.write('he;')

### StringIO
    from io import StringIO
    f = StringIO()
    f.write('he')
    f.getvalue()
    
    f = StringIO('ss\nss\b')
    while True:
        s = f.realine()
        if  s = '':
            break
        print(s.strip())

###BytesIO
    form io import ByteIO
    f = ByteIO()
    f.write('中文‘, encode('utf-8'))

###操作文件和目录
    import os

####系统信息
    os.name
    os.uname()
    os.environ
    os.enviro.get('key')
    
####操作文件和目录
    os.path.abspath('.')
    tmp_path = os.path.join('/Users/'. 'testdor')
    os.mkdir(tmp_path)
    os.path.split(tmp_path)
    os.path.splitext('/path/to/file.txt')

    os.rename('test.txt', 'test.py')
    os.remove('test.py')

    from shutil import copyfile
 
    [x for x in os.listdir('.') if os.path.isfile(x) and os.path.splittext(x)[1]=='py]

###序列化
吧变量从内存编程课存储和传输的过程称为序列化，Python中叫 pickling，其他语言中serialization, marshaling, flattening

    import pickle
    d = dict('name='bob', age=20, score=88)
    pickle.dump(d)
    f = open('./test.txt', 'wb')
    pickle.dump(d, f)
    f.close()
    
    f = open('./test.txt', 'rb')
    d = pickle.load(f)
    f.close()
    d

###JSON
    #{} dict    [] list

    import json
    d = dict('name='bob', age=20, score=88)
    json.dump(d) # return a str

    json.load(json_str)

对象的json方法

    print(json.dumps(s, default=student2dict))
    (json.dumps(s, default=lambda obj: obj.__dict__)

##进程和线程

### 多进程
#### fork()
    import os
    
    print(os.getpid())
    # Unix, Linux, Mac
    pid = os.fork()
    #do sth

#### multiprocessing
    from multiprocessing import Process
    import os

    def run_proc(name)
        print('run child %s (%s)', %(name, os.getpid())

    if __name__ =='main':
        p = Process(target=run_proc, args=('test'))
        p.start()
        p.join()

####Pool
    from multiprocessing import Pool

    def long_time_task(name):
        pass;

    if __name__=='__main__':
        p = Pool(4)
        for i  in range(5):
            p.apply_async(long_time_task, args=(i,))
        p.close()
        p.join()

####子进程
    import subprocess
    r = subprocess.call(['nslookup', 'www.python.org'])

####进程间通信
    from multiprocessing import Process, Queue
    import os, time, random

    def wtite(q):
        q.put('x')

    def read(q):
        value = q.get(True)
        print(value)

    if __name__='__main__':
        q = Queue()
        pw = Process(target=write, args=(q,)
        pr = Process(targer=read, args=(q,)

        pw.start()
        pr.start()
        pw.join()
        pr.terminate()

    
###多线程
    import time, threading
    
    def loop():
        pass
    
    t = threading.Thread(target=loop, name='LoopThread')
    t.start()
    t.join()

Lock

    def run_thread(n):
        for i in range(1000000):
            lock acquire()
        #do sth

### ThreadLocal
    import threading
    local_school = threading.local()

###分布式进程
- 应该优选进程，更稳定，可以部署到多台机器
- multiprocessing 中的 managers 模块支持把进程分布到多台机器上

服务进程
    # task_master.py
    import random, time, queue
    form multiprocessing.managers import BaseManager

    task_queue = queue.Queue()
    result_queue = queue.Queue()

    class QueueManager(BaseManager):
        pass
    
    QueueManager.register('get_task_queue', callable=lambda: task_queue)
    QueueManager.register('get_result_queue', callable= lambda: result_queue)

    manager = QueueManager(address=('', 5000), authkey=b'abc')

    manager.start()

    task = manager.get_task_queue()
    result = manager.get_result_queue()

    for i in range(10):
        n = random.randint(0, 1000)
        print('put task %d ...', %n)
        task.put(n)

    for i in range(10):
        r = result.get(timeout=10):
            print ('result: %s', %r)

    manager.shutdown()
另一台机器上启动进程
    # task_worker.py
    import time, sys, queue
    from multiprocessing.managers import BaseManager

    class QueueManager(BaseManager):
        pass

    QueueManager.register('get_task_queue')
    QueueManager.register('get_result_queue')

    server_addr = '127.0.0.1'
    print('Connect to server %s..' %server_addr)
    m = QueueManager(address=(server_addr, 5000), authkey=b'abc')
    
    m.connect()

    task = m.get_task_queue()
    result = m.get_result_queue()

    for i in range(0):
        try:
            n = task.get(timeout=1)
            r = '%d * %d = %d' % (n, n , n*n)
            time.sleep(1)
            result.put(r)
        except Queue.Empty:
            print('task queue is empty.')

    print(' worker exit')    


##正则表达式
###基本正则表达式
- \d匹配一个数字，\w 匹配数字或字母， . 匹配任意字符
- \* 表示任意个字符， +表示至少一个1个字符， {n, m}表示n到m个字符
        \d{3}\s+\d{3,8}
        \d(3)\-\d(3,8)
- 精确匹配
        [0-9a-zA-Z\_]{0, 19}
        [P|python]
- ^行开头
        ^\d
- \$行结束
       \ \d\$
###re模块
- 使用r前缀，表示是一个正则表达式 s = r'ABC\-001'
- 是否匹配
        import re
        re.match(r'\d{3}\-\d{3,8}$', '010-12315')
- 切分字符串
        re.split(r'\s+', 'a, b  c')
- 分组， 利用()表示要提取的分组
        m = re.match(r'^(\d{3})-(\d{3, 8})$', '010-12345')
        m.group(0)
        m.group(1)
        m.group(2)
        #时间匹配
        m = re.match(r'^(0[0-9]|1[0-9]|2[0-3]|[0-9])\:(0[0-9]|1[0-9]|2[0-9]|3[0-9]|4[0-9]|5[0-9]|[0-9])\:(0[0-9]|1[0-9]|2[0-9]|3[0-9]|4[0-9]|5[0-9]|[0-9])$', t)

## 常用内建模块
###datetime
    from datetime import datetime
    now = datetime.now()
    dt = datetime(2015, 4, 19, 12, 20)
    dt.timestamp()
    t = 1429417200.0
    dt1 = datetime.fromtimestamp(t)
    cday = datetime.strptime('2015-6-1 18:19:59', '%Y-%m-%d %H:%M:%S')
    now.strftime('%a, %b %d, %H:%M')
    now + timedate(hours=10)
    now - timedate(days=1)
    now + timedate(days=2, hours=12)

    from datetime import datetime, timedelta, timezone
    tz_utc_8 = timezone(timedelta)
    now = datetime.now()
    dt = now.replace(tzinfo=tz_utc_8)

    utc_dt = datetime.utcnow().replace(tzinfo=timezone.utc)
    bj_dt = utc_dt.astimezone(timezone(timedelta(hours=8)))

###collections
- namedtuple
        from collections imort namedtuple
        Point = namedtuple('Point', ['x', 'y'])
        p = Point(1, 2)
        p.x
- deque 高效实现插入和删除的双向列表，使用与队列和栈
        from collections import deque
        q = deque(['a'. 'b'. 'c'])
        q.append('x')
        q.appendleft('y') #开始插入
- defaultdict dict，可以不存在时返回默认值而不是返回KeyError
        from collections import defaultdict
        dd = defaultdict(lambda: 'N/A')
        dd['key1'] = 'abc'
        dd['key2']
- OrderedDict key时有序的
        from collections import OrderedDict
        d = dict([('a',1), ('b', 2), ('c', 3)])
        od = OrderedDict([('a',1), ('b', 2), ('c', 3)])
- Counter
        from collection import Counter
        c = Counter()
        for ch in 'programing':
            c[ch] = c[ch] +1

###base64
- 原理
    - 准备一个包含64个字符的数组 ['A', 'B', ... 'a', 'b', ... '0', '1', ... '+', '/']
    - 对二进制处理，每3个字节一组，一共3*8=24bit，划分为4组，每组正好6bit
    - 把4组分别用64字符的数组表示，得到编码后的字符串
    - 作用将3字节的二进制数据编码为4字节的文本数据
    - 二进制字节数不是3的倍数，用\x00补齐，并在编码的末尾加上1个或者2个=号，表示补的字节数
- 内置base64模块
        import base64
        base64.b64encode('...')
        base64.b64decode('...')
- urlsafe + /  --> -_
        base64.urlsafe_b64encode()
        base64.urlsafe_b64decode()
- 由于= 在url等中的歧义，很多算法编码后把=去掉

### struct 解决bytes和其他二进制数据类型的转换
    import struct
    struct.pack('>I', 10240099)
    s = b'\x42\x4d\x38\x8c\x0a\x00\x00\x00\x00\x00\x36\x00\x00\x00\x28\x00\x00\x00\x80\x02\x00\x00\x68\x01\x00\x00\x01\x00\x18\x00'
    s.unpack('<ccIIIIIIHH', s)

### hahslib 提供重要的再要算法，如MD5，SHA1等
- 基本用法
       import hashlib
    
        md5 = hashlib.md5()
        md5.update('hh')
        md5.update('11')
        print(md5.hexdigest())

        sha1 = hashlib.sha1()
        #...

- 加盐，可以将登录名作为salt的一部分
        def calc_md5(password):
            return get_md5(password + 'the-Salt')

### itertools
    import itertools 
    cs = itertools.cycle('abc')
    for c in cs:
        print(c)
    ns = itertools.repeat('a', 3)

    natuals = itertools.count(1)
    ns = itertools.takewhile(lambda x: x <= 10, natuals)
    list(ns)

    for c in itertools.chain('a', 'xxx'):
        pass

    for key, group in itertools.groupby('aasssaacc'):
        print(key, list(group))

###XML
- 操作方法有DOM和SAX，DOM将整个XML读入内存，占用内存大，但可以任意遍历树的节点。SAX流模式，占用内存小，解析快，但要我们自己处理事件
- python中使用SAX解析XML，关心的时间通常有start_element(<a href="/">), end_element(</a>), char_data(python)
        <a href="/">python</a>

        from xml.parsers.expat import PaserCreate

        class DefaultSaxHandler(object):
            def start_element(self, name, attrs):
                print('%s, %s', %(name, str(attrs)))

            def end_element(self, name):
                print('%s', name)

            def char_data(self, text):
                print(text)

        xml = r'''<?xml version="1.0"?>
            <ol>
            <li><a href="/python">Python</a></li>
            <li><a href="/ruby">Ruby</a></li>
            </ol>'''
        
        handler = DefaultSaxHandler()
        parser = ParserCreate()
        parser.StartElementHandler = handler.start_element
        parser.EndElementHandler = handler.end_element
        parser.CharacterDataHandler = handler.char_data
        parser.Parser(xml)

- 生成XML，拼接字符串
        
### HTMLParser
    from html.parser import HTMLParser
    from html.entities import name2codepoint

    class MyHTMLParser(HTMLParser):
        
        def handle_starttag(self, tag, attrs):
            pass
    
        def handle_endtag(self, tag):
            pass
    
        def handle_startendtag(self, tag, attrs):
            pass

        def handle_data(self, data):
            pass

        def handle_comment(self, data):
            pass

        def handle_entityref(self, data):
            pass

        def handle_charref(self, name):
            pass

        parser = MyHTMLParser()
        parser.feed('...')

### urllib
- get
        from urllib import request

        with request.urlopen('https://api.douban.com/v2/book/2129650') as f:
            data = f.read()
            for k, v in f.getheaders():
                pass

- post
- handler
            
## 常用第三方模块
基本所有第三方模块都在PyPI上注册
    
### PIL (2.7) Pillow(3.x) 
图像操作

## virtualenv 
python 多版本并存

##图形界面
自带Tkinter，其他有wxWiddgets, Qt, GTK

## 网络编程

### TCP编程
####客户端
    import socket

    s = socket.socket(socket.AF_INET, SOCK_STREAM)
    s.connect(('www.sina.com.cn', 80))

    s.send(b'GET / HTTP/1.1\r\nHost: www.sina.com.cn\r\nConnection: close\r\n\r\n')

    buffer = []
    while True:
        d = s.recv(1024)
        if d:
            buffer.append(d)
        else:
            break

    data = b''.join(buffer)
    
    s.close()

####服务器
    s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
    s.bind(('127.0.0.1', 9999))
    s.listen(5)

    while True:
        sock, addr = s.accept()
        t = threading.Thread(target=tcplink, args=(sock, addr))
        t.start()

    def tcplink(sock, addr):
        sock.send(b'Welcom!')
        while True:
            data = sock.recv(1024)
            time.sleep(1)
            if not data or data.decode('utf-8') == 'exit':
                break
            sock.send(('hello, %s' %data).encode('utf-8'))
        sock.close()

###UDP编程
服务器
    s = socket.socket(socket.AF_INET, socket.SOCK_DGRAM)
    # 绑定端口:
    s.bind(('127.0.0.1', 9999))
    print('Bind UDP on 9999...')
    while True:
        # 接收数据:
        data, addr = s.recvfrom(1024)
        print('Received from %s:%s.' % addr)
        s.sendto(b'Hello, %s!' % data, addr)
客户端
    s = socket.socket(socket.AF_INET, socket.SOCK_DGRAM)
    for data in [b'Michael', b'Tracy', b'Sarah']:
        # 发送数据:
        s.sendto(data, ('127.0.0.1', 9999))
        # 接收数据:
        print(s.recv(1024).decode('utf-8'))
    s.close()

## 电子邮件
###SMTP
###POP3

## 数据库
###SQLLite
    import sqlite3
    conn = sqlite3.connect('test.db')
    cursor = conn.cursor()
    cursor.execute('..')
    values = cursor.fetchall()
    cursor.rowcount
    cursor.close()
    conn.commit()
    conn.close()

###MySQL
    $ pip3 install mysql-connector-python --allow-external mysql-connector-python

    import mysql.connector
    conn = mysql.connector.connect(user='root', passowrd='', database='test')
    cursor = conn.cursor()    
    ##其他类似

###使用SQLAlchemy
 Python 中最有名的ORM框架
    $ pip3 install sqlalchemy
    
    from sqlalchemy import Column, String, create_engine
    form sqlalchemy.orm import sessionmaker
    form sqlalchemy.ext.declarative import declarative

    class User(Base):
        __tablename__ = 'user'

        id = Column(String(20), primary_key=True)
        name = Column(String(20))

    engine = create_engine('mysql+mysqlconnector://root:password@localhost:3306/test')
    DBSession = sessionmaker(bind=engin)

    session = DBSession()
    new_user = User(id='5', name='Bob')
    
    session.add(new_user)
    session.commit()
    session.close()

    session = DBSession()
    user = session.query(User).filter(User.id=='5').one()
    session.close()


## Web开发
### HTTP简介
####请求流程
1. 浏览器向服务器发送HTTP请求，请求包括：
    - 方法：GET仅请求资源，POST附带用户数据
    - 路径：/full/url/path
    - 域名：由Host头指定：Host: www.sina.com.cn
    - 其他相关Header
    - POST方法包含一个Body，包含用户数据
2. 服务器响应请求，请求包括
    - 响应代码：200 表示成功，3xx表示重定向，4xx表示客户端发送请求有错误，5xx表示服务器端处理时发生了错误
    - 响应类型：由 Content-Type 指定
    - 其他相关Header
    - Body
3. 浏览器继续请求其他资源，比如图片，再次发出HTTP请求，重复上两步

####HTTP格式
1. GET格式，利用 \r\n 换行
        GET /path HTTP/1.1
        Header1: Value1
2. POST格式，利用两个\r\n 分割Header与Body
        POST /path HTTP/1.1
        Header1: Value1

        body data goes here
3. 响应格式
        200 OK
        Header1: Value1

        body goes here

### HTML简介
    <html>
    <head>
      <title>Hello</title>
      <style>
        h1 {
          color: #333333;
          font-size: 48px;
          text-shadow: 3px 3px 3px #666666;
        }
      </style>
      <script>
        function change() {
          document.getElementsByTagName('h1')[0].style.color = '#ff0000';
        }
      </script>
    </head>
    <body>
      <h1 onclick="change()">Hello, world!</h1>
    </body>
    </html>

###WSGI接口（Web Server Gateway Interface)
####接口定义
    def application(environ, start_response):
        start_response('200 OK', [{'Content-Type', 'text/html'}])
        return [b'<h1>Hello, web!</h1>']

其中 environ 为包含HTTP请求信息的dict对象，start_response为一个发送HTTP响应的函数

server.py
    
    from wsgiref.simple_server import make_server

    from hello import application

    httpd = make_server('', 8000, application)
    
    httpd.server_forever()

###使用Web框架
    $ pip install flask

### 使用模板       


##异步IO
异步IO模型需要一个消息循环，在消息循环中，主线程不断重复“读取消息-处理消息”这一过程：

    loop = get_event_loop()
    while True:
        evernt = loop.get_enent()
        process_event(event)

###协程 Coroutine
子程序是通过栈实现的
协程看上去是子程序，但执行过程中，在子程序内部可中断，然后转而执行别的子程序，在适当的时候再反悔啦接着执行
####协程的特点是在一个线程执行，优点有
- 不需要切换线程，执行效率高
- 不需要多线程的锁机制

####协程的实现，通过 generator 实现，在 generator 中，我们可以不断调用next()获取由yield语句返回的下一个值，还可以接收调用者的参数 

    def consumer():
        r = ''
        while True:
            n = yield r
            if not n:
                return
            print('[CONSUMER] %s' %n)
            r = '200 OK'

    def produce(c)
        c.send(None)
        n = 0
        while n < 5:
            n = n + 1
            r = c.send(n)
        c.close()

    c = consumer()
    produce(c)

### asyncio
    import asyncio

    @asyncio.coroutine
    def hello():
        print('Hello world!')
        r = yield from asyncio.sleep(1)
        print('hello again')

    loop = asyncio.get_event_loop()
    tasks = [hello(), helllo()]
    loop.run_until_complete(asyncio.wait(tasks))
    loop.close()

### aiohttp
    $ pip install aiohttp
    
    import asyncio
    from aiohttp import web
    
    def index(request):
        return web.Response(body=b'<h1>Index</h1>')

    def hello(request):
        yield from asyncio.sleep(0.5)
        text = '<h1>hello %s!</h1>' % request.match_info['name']
        return web.response(body=text.encode('utf-8'))

    @asyncio.coroutine
    def init(loop):
        app = web.Application(loop=loop)
        app.router.add_route('GET', '/',index)
        app.router.add_route('Get', '/hello/{name}', hello)
        srv = yield from loop.create_server(app.make_handler(), '127.0.0.1', 8000)
        return srv

    loop = asyncio.get_event_loop()
    loop ren_until_complete(init(loop))
    loop.run_forever()


    

     



    
    
    
    




        

    

        

        







    


    





        