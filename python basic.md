##����

###��������
    print("hello, world")
    print("hello,", "world")
    print('300 + 200',  300 + 200)
    name = input()

###������������
    - ����
        1�� -8080�� 0�� 0xff00 ��ʮ�����ƣ�
    - ������
        1.23��3.14,1.23e10��1.2e-5
    - �ַ���
        print('I\'m learning \nPython')
        print(r'\\\t\\') ��r' ' ��ת�壩
        print('''line1
        ...line2''')     ��'''...'''��ʾ�������ݣ�
        print('''line1
        line2
        line3''')
    - BOOL
        True 
        False
        and or not
    - None
    - ����
        a = 2
    - ����
        PI = 3.1415926 ��ȫ����д��
        10/3 = 3.333
        10//3 = 3

###�ַ����ͱ���
    - Python 3��Unicode��ʽ
    - �ַ�ת��
        ord()
        chr()
    - ռλ��
        %d %f %s %x

### list �� tuple
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
    �����޸ģ�û�� append() inser() pop() ����
        classmatesTuple = ('Mike', 'Bob', 'Tracy')
        t = ()
        t = (1, ) '''��Ҫע�⣬��Ϊ�������������壬����ޣ��ڲ������壩
        
###�����ж�
    age = 3
    if age >= 18:
        print('adult')
    elif age >-0:
        print('teanager')
    else:
        print('kid')

### ѭ��
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
�ַ�����֤�鶼������Ϊkey

    d = {'Michael': 95, 'Bob': 75, 'Tracy': 85}
    d['Michael']
    '''Ϊ��ֹ������key������ʹ�����·���'''
    if 'Michael' in d:
        print(d['Michael'])
    d.get('Thomas')
    d.get('Thomas', -1)
    d.pop('Bob')

### set
һ��key�ļ��ϣ����洢value����set��û���ظ���key

    s = set([1, 2, 3])
    s.add(5)
    s.remove(5)
    s1 & s2 (������
    s1 | s2 ��������

## ����
###�����ĵ��úͶ���

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
    '''ʵ���ϣ����ص���һ��tupleֵ'''

### �����Ĳ���
Ĭ�ϲ����ں�

    def power(x, n=2):
        s = s
        while n >0:
            n = n -1
            s = s*x
        return s

�ɱ����

    def calc(*numbers):
        sum = 0
        for n in numbers:
            sum = sum + n * n
        reutnr sum
     
    cals(1, 2)

    nums = (1, 2, 3)
    clas(*nums)

�ؼ��ֲ�������չ�����Ĺ���

    def person(name, age, **kw):
        print(' name', name, 'other', kw)
        if 'city' in kw:
            pass
        if 'job' in kw:
            pass

    extra = {'city': 'Beijing', 'job': 'Enginear'}
    person('Jack', 23, **extra)

�����ؼ��ֲ�������*�ָ������Ĭ��ֵ

    def person(name, age, *, city, job):
        pass

    person('Jack', 24, city='Beijing', job= 'Engineer')

���������˳�򣬱�ѡ������Ĭ�ϲ������ɱ�/�����������ؼ��ֲ���

    def f2(a, b, c=0 *, d, **kw):
        pass

    f2(1, 2, d=99, ext=None)
    args = (1, 2, 3)
    kw = {'d': 88, 'x': '#'}
    f2(*args, **kw)

###�ݹ麯��
    def fact(n):
        if n==1:
            return 1
        return n * fact(n-1)

ʹ��ʱҪ��ֹջ�������Ҫͨ��β�ݹ��Ż�����pythonû����β�ݹ��Ż������ã�

    def fact(n):
        return fact_iter(n, 1)
    
    def fact_iter(num, product):
        if num == 1;
            return product
        return fact_iter(num-1, num * product)

##�߼�����

###��Ƭ
    L[0:3]
    L[-2:]
    L[-2: -1]
    L[ : ]
    my_tuple[:3]
    'abc'[0:1]

###����
    for key in my_dict:
        pass
    for ch in 'ABCDD':
        pass
    '''�ж��Ƿ���Ե���'''
    from collections import Iterable
    isinstance('abc', Iterable)
    
    for i, value in enumerate(['A', 'b', 'c']):
        print(i, value)

###�б�ʽ����
    a = list(range(1, 11))
    [x * x for x in range(1, 11) if x % 2 == 0]
    [m + n for m in 'ABC' for n in 'XYZ']

    b = {x *2 for x in a } # set

    c = [x * 2 for x in a] # list

    d = {x*2: x for x in a} # dict

    e = (x*2 for x in a) # generator




###������
generrator����������㷨

    g = (x * x for x in range(10))
    for n in g:
        print(n)

    def fib(max):
        n, a, b = 0, 0, 1
        while n < max:
            yield b '''��Ҫ��fib�Ǹ���������'''
            a, b = b, a + b
            n +=1
        return 'done'

### ������
forѭ��ʹ�÷�Χ��Iterable��
- list, tuple, dict, set, str
- generator //Iterator

##����ʽ���

###����

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

lambda ����

    from functools import reduce
    def char2num(s):
         return {'0': 0, '1': 1, '2': 2, '3': 3, '4': 4, '5': 5, '6': 6, '7': 7, '8': 8, '9': 9}[s]

    def str2int(s):
    return reduce(lambdax, y: x * 10 + y, map(char2num, s))

###filter

    list(filter(lambda x: x % 2 == 1, list(range(10))))
    list(filter(lambda x: x % 2 == 1, range(10)))
    
    list(filter(lambda x: x and x.strip(), ['a', 'b ', None, 'c  ']))

����ɸѡ

    def _not_devisible(n):
        return lambad x: x%n > 0
    #������
    def primes():
        yield 2
        it = _odd_iter() # ��ʼ����
        while True:
            n = next(it)
            yield n 
            it = filter(_not_devisible(n)m it)

    for n in primes():
        if n < 1000:
            print(n)
        else:
            break

### sorted �����㷨

    sorted(my_list, key=abs)

    sorted(my_str_list, key=str.lower, reverse=True)

###���غ���

    def lazy_sum(*args):
        def sum():
            ax = 0
            for n in args:
                ax = ax + n
            return ax
        return sum

    f = lazy_sum(1, 3, 4, 5)
    f()

�հ�

    def count():
        def f(j)
            def g():
                return j*j
        fs = []
        for i in range(1, 4):
            fs.append(f(i))
        return fs

    f1, f2 , f3 = count()
    
###װ����

    def log(func):
        def wrapper(*args, **kw):
            print('call %s()', % func.__name__)
                ruturn func(*args, **kw)
        return wrapper

    @log
    def now():
        pass
    now.__name__

###ƫ����

    import functools
    int2 = functools.partial(int, base=2)
    int('10000')

##ģ��

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

    #��ֱ�������ļ�ʱ�����У������ļ�����ʱ��������
    if __name__== '__main__'
        test()

�ⲿ�����õĺ�������Ϊprivate�� _private_sss()

������ģ��
    pypi.python.org
    pip install Pillow

����ʱ����Ŀ¼Ϊ  sys.path�����Զ���Ŀ¼��������Ŀ¼

    import sys
    sys.path.append('/xxx/')

���� �޸Ļ������� PYTHONPATH

##���������
###���ʵ��

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

- `__x`��˽�б��������ܷ��ʣ�ʵ�ʿ���ͨ�� _classname__x���ʣ������Ƽ�
- `__x__`��������������Է���
- `_name` ���Է��ʣ�������Լ�������Ҳ��Ҫ����

### �̳кͶ�̬

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

###��ȡ������Ϣ

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

###ʵ�����Ժ�������
    class Student(object):
        name = 'Student' #�����ԣ���ʵ��û��name���ԣ���Ĭ�Ϸ������

##�������߼����

### __slots__
- ��̬�����Ժͷ���
        class Student(object):            
            pass

        s = Student()
        s.name = 'Michael'

        def set_age(self, age)
            self.age = age
        from types import MethodType
        s.set_age = MethodType(set_age, s) # ��ʵ����
        Student.set_score = MethodType(set_score, Student)

- ����ʵ�������ԣ������಻������
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

###���ؼ̳�

    class Dog(Anamal, RunableMixIn, CarnivorousMixIn):
        pass

    class MyTcpServer(TCPServer, ForkingMixIn):
        pass

###������
- __str__ ����print�е����
- __iter__ ���ڵ��������ص������Σ��Զ�����__next()��֪������StopIteration
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
- __getitem__ �����±꣬��Ƭȡ����
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
- __getattr__ �ض���
        class Student(object):
            def __getattr__(self, attr):
                if attr == ��age':
                    return lambda: 25
- __call__ ֱ�Ӷ�ʵ������
        class Student(object):
            def __call__:
                pass

        s = Student()
        s()

        callable(Student)

###ö�ٷ�

    from enum import Enum, unique
    
    @unique
    class WeekEnd(Enum):
        Sun = 0
        Sat = 6

    day1 = Weekday.Sun
    Weekday['Sun']
    Weekday[0]

###ʹ��Ԫ��
 type()

    def fn(self, name='world'):
        pass
    
    Hello = type('Hello', (object,), dict(hello=fn)) #����Hello class
    h = Hello()
    h.hello()

metaclass()���ȶ���metaclass�� �����࣬����ʵ��

    class ListMetaclass(type):
        def __new__(cls, name, bases, attrs):
            attrs['add'] = lambda self, value: self.append(value)
            return type.__new__(cls, name, bases, attrs)

    class MyList(list, metaclass=ListMetaclass): # �Զ����add����
        pass

ORM "Object Relational Mapping" �����ϵӳ��
����
    
    class User(Model):
        id = IntegerField('id')
        #...

���и���Model��IntegerField��ORM����ṩ��save��ħ��������metaclass�ṩ

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
            

���û�����һ��class User(Model)ʱ��Python������������User������Ѱ��metaclass�������У��ڸ�����Ѱ�ң���ModelMetaclass�У��ų��˶�Model���޸ģ��ڵ�ǰ���в��Ҷ�������ԣ�����__mappings__�У�ͬʱ����������ɾ�����ѱ����洢��__table__��

##���󡢵��ԺͲ���

##IO���

###�ļ���д
####���ļ�
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
�� read()�����Ķ���
####������
    f = open('./test.txt', 'rb')

####�ַ�����
    f = open('./test.txt', 'rb', encoding = 'gbk', error='ignor')

####д�ļ�
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
    f.write('���ġ�, encode('utf-8'))

###�����ļ���Ŀ¼
    import os

####ϵͳ��Ϣ
    os.name
    os.uname()
    os.environ
    os.enviro.get('key')
    
####�����ļ���Ŀ¼
    os.path.abspath('.')
    tmp_path = os.path.join('/Users/'. 'testdor')
    os.mkdir(tmp_path)
    os.path.split(tmp_path)
    os.path.splitext('/path/to/file.txt')

    os.rename('test.txt', 'test.py')
    os.remove('test.py')

    from shutil import copyfile
 
    [x for x in os.listdir('.') if os.path.isfile(x) and os.path.splittext(x)[1]=='py]

###���л�
�ɱ������ڴ��̿δ洢�ʹ���Ĺ��̳�Ϊ���л���Python�н� pickling������������serialization, marshaling, flattening

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

�����json����

    print(json.dumps(s, default=student2dict))
    (json.dumps(s, default=lambda obj: obj.__dict__)

##���̺��߳�

### �����
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

####�ӽ���
    import subprocess
    r = subprocess.call(['nslookup', 'www.python.org'])

####���̼�ͨ��
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

    
###���߳�
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

###�ֲ�ʽ����
- Ӧ����ѡ���̣����ȶ������Բ��𵽶�̨����
- multiprocessing �е� managers ģ��֧�ְѽ��̷ֲ�����̨������

�������
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
��һ̨��������������
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


##������ʽ
###����������ʽ
- \dƥ��һ�����֣�\w ƥ�����ֻ���ĸ�� . ƥ�������ַ�
- \* ��ʾ������ַ��� +��ʾ����һ��1���ַ��� {n, m}��ʾn��m���ַ�
        \d{3}\s+\d{3,8}
        \d(3)\-\d(3,8)
- ��ȷƥ��
        [0-9a-zA-Z\_]{0, 19}
        [P|python]
- ^�п�ͷ
        ^\d
- \$�н���
       \ \d\$
###reģ��
- ʹ��rǰ׺����ʾ��һ��������ʽ s = r'ABC\-001'
- �Ƿ�ƥ��
        import re
        re.match(r'\d{3}\-\d{3,8}$', '010-12315')
- �з��ַ���
        re.split(r'\s+', 'a, b  c')
- ���飬 ����()��ʾҪ��ȡ�ķ���
        m = re.match(r'^(\d{3})-(\d{3, 8})$', '010-12345')
        m.group(0)
        m.group(1)
        m.group(2)
        #ʱ��ƥ��
        m = re.match(r'^(0[0-9]|1[0-9]|2[0-3]|[0-9])\:(0[0-9]|1[0-9]|2[0-9]|3[0-9]|4[0-9]|5[0-9]|[0-9])\:(0[0-9]|1[0-9]|2[0-9]|3[0-9]|4[0-9]|5[0-9]|[0-9])$', t)

## �����ڽ�ģ��
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
- deque ��Чʵ�ֲ����ɾ����˫���б�ʹ������к�ջ
        from collections import deque
        q = deque(['a'. 'b'. 'c'])
        q.append('x')
        q.appendleft('y') #��ʼ����
- defaultdict dict�����Բ�����ʱ����Ĭ��ֵ�����Ƿ���KeyError
        from collections import defaultdict
        dd = defaultdict(lambda: 'N/A')
        dd['key1'] = 'abc'
        dd['key2']
- OrderedDict keyʱ�����
        from collections import OrderedDict
        d = dict([('a',1), ('b', 2), ('c', 3)])
        od = OrderedDict([('a',1), ('b', 2), ('c', 3)])
- Counter
        from collection import Counter
        c = Counter()
        for ch in 'programing':
            c[ch] = c[ch] +1

###base64
- ԭ��
    - ׼��һ������64���ַ������� ['A', 'B', ... 'a', 'b', ... '0', '1', ... '+', '/']
    - �Զ����ƴ���ÿ3���ֽ�һ�飬һ��3*8=24bit������Ϊ4�飬ÿ������6bit
    - ��4��ֱ���64�ַ��������ʾ���õ��������ַ���
    - ���ý�3�ֽڵĶ��������ݱ���Ϊ4�ֽڵ��ı�����
    - �������ֽ�������3�ı�������\x00���룬���ڱ����ĩβ����1������2��=�ţ���ʾ�����ֽ���
- ����base64ģ��
        import base64
        base64.b64encode('...')
        base64.b64decode('...')
- urlsafe + /  --> -_
        base64.urlsafe_b64encode()
        base64.urlsafe_b64decode()
- ����= ��url���е����壬�ܶ��㷨������=ȥ��

### struct ���bytes�������������������͵�ת��
    import struct
    struct.pack('>I', 10240099)
    s = b'\x42\x4d\x38\x8c\x0a\x00\x00\x00\x00\x00\x36\x00\x00\x00\x28\x00\x00\x00\x80\x02\x00\x00\x68\x01\x00\x00\x01\x00\x18\x00'
    s.unpack('<ccIIIIIIHH', s)

### hahslib �ṩ��Ҫ����Ҫ�㷨����MD5��SHA1��
- �����÷�
       import hashlib
    
        md5 = hashlib.md5()
        md5.update('hh')
        md5.update('11')
        print(md5.hexdigest())

        sha1 = hashlib.sha1()
        #...

- ���Σ����Խ���¼����Ϊsalt��һ����
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
- ����������DOM��SAX��DOM������XML�����ڴ棬ռ���ڴ�󣬵���������������Ľڵ㡣SAX��ģʽ��ռ���ڴ�С�������죬��Ҫ�����Լ������¼�
- python��ʹ��SAX����XML�����ĵ�ʱ��ͨ����start_element(<a href="/">), end_element(</a>), char_data(python)
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

- ����XML��ƴ���ַ���
        
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
            
## ���õ�����ģ��
�������е�����ģ�鶼��PyPI��ע��
    
### PIL (2.7) Pillow(3.x) 
ͼ�����

## virtualenv 
python ��汾����

##ͼ�ν���
�Դ�Tkinter��������wxWiddgets, Qt, GTK

## ������

### TCP���
####�ͻ���
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

####������
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

###UDP���
������
    s = socket.socket(socket.AF_INET, socket.SOCK_DGRAM)
    # �󶨶˿�:
    s.bind(('127.0.0.1', 9999))
    print('Bind UDP on 9999...')
    while True:
        # ��������:
        data, addr = s.recvfrom(1024)
        print('Received from %s:%s.' % addr)
        s.sendto(b'Hello, %s!' % data, addr)
�ͻ���
    s = socket.socket(socket.AF_INET, socket.SOCK_DGRAM)
    for data in [b'Michael', b'Tracy', b'Sarah']:
        # ��������:
        s.sendto(data, ('127.0.0.1', 9999))
        # ��������:
        print(s.recv(1024).decode('utf-8'))
    s.close()

## �����ʼ�
###SMTP
###POP3

## ���ݿ�
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
    ##��������

###ʹ��SQLAlchemy
 Python ����������ORM���
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


## Web����
### HTTP���
####��������
1. ����������������HTTP�������������
    - ������GET��������Դ��POST�����û�����
    - ·����/full/url/path
    - ��������Hostͷָ����Host: www.sina.com.cn
    - �������Header
    - POST��������һ��Body�������û�����
2. ��������Ӧ�����������
    - ��Ӧ���룺200 ��ʾ�ɹ���3xx��ʾ�ض���4xx��ʾ�ͻ��˷��������д���5xx��ʾ�������˴���ʱ�����˴���
    - ��Ӧ���ͣ��� Content-Type ָ��
    - �������Header
    - Body
3. �������������������Դ������ͼƬ���ٴη���HTTP�����ظ�������

####HTTP��ʽ
1. GET��ʽ������ \r\n ����
        GET /path HTTP/1.1
        Header1: Value1
2. POST��ʽ����������\r\n �ָ�Header��Body
        POST /path HTTP/1.1
        Header1: Value1

        body data goes here
3. ��Ӧ��ʽ
        200 OK
        Header1: Value1

        body goes here

### HTML���
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

###WSGI�ӿڣ�Web Server Gateway Interface)
####�ӿڶ���
    def application(environ, start_response):
        start_response('200 OK', [{'Content-Type', 'text/html'}])
        return [b'<h1>Hello, web!</h1>']

���� environ Ϊ����HTTP������Ϣ��dict����start_responseΪһ������HTTP��Ӧ�ĺ���

server.py
    
    from wsgiref.simple_server import make_server

    from hello import application

    httpd = make_server('', 8000, application)
    
    httpd.server_forever()

###ʹ��Web���
    $ pip install flask

### ʹ��ģ��       


##�첽IO
�첽IOģ����Ҫһ����Ϣѭ��������Ϣѭ���У����̲߳����ظ�����ȡ��Ϣ-������Ϣ����һ���̣�

    loop = get_event_loop()
    while True:
        evernt = loop.get_enent()
        process_event(event)

###Э�� Coroutine
�ӳ�����ͨ��ջʵ�ֵ�
Э�̿���ȥ���ӳ��򣬵�ִ�й����У����ӳ����ڲ����жϣ�Ȼ��ת��ִ�б���ӳ������ʵ���ʱ���ٷ���������ִ��
####Э�̵��ص�����һ���߳�ִ�У��ŵ���
- ����Ҫ�л��̣߳�ִ��Ч�ʸ�
- ����Ҫ���̵߳�������

####Э�̵�ʵ�֣�ͨ�� generator ʵ�֣��� generator �У����ǿ��Բ��ϵ���next()��ȡ��yield��䷵�ص���һ��ֵ�������Խ��յ����ߵĲ��� 

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


    

     



    
    
    
    




        

    

        

        







    


    





        