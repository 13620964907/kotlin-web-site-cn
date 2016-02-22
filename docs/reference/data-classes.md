---
type: doc
layout: reference
category: "Classes and Objects"
title: "Data Classes"
---

# ������

���Ǿ�������һЩֻ�Ǵ������ݵ��ࡣ����Щ����Ĺ��ܾ�����
���������������е����ݡ���Kotlin�У�����������Ա����Ϊ`data`��
 
``` kotlin
data class User(val name: String, val age: Int)
```

�ⱻ����һ�� _������_���������Զ����������캯�������ȫ�������еõ����³�Ա��
  
  * `equals()`/`hashCode()` �ԣ�
  * `toString()` ��ʽ�� `"User(name=John, age=42)"`��
  * [`componentN()` functions](multi-declarations.html) ��Ӧ������˳����ֵ��������ԣ�
  * `copy()` �����������棩��
  
�����ĳ����������ȷ�ض�����������߱��̳У��������Ͳ����������������

To ensure consistency and meaningful behavior of the generated code, data classes have to fulfil the following requirements:

  * The primary constructor needs to have at least one parameter;
  * All primary constructor parameters need to be marked as `val` or `var`;
  * Data classes cannot be abstract, open, sealed or inner;
  * Data classes may not extend other classes (but may implement interfaces).
  
> ��JVM�У�������ɵ�����Ҫ����һ���޲εĹ��캯���������е����Ա�����Ĭ��ֵ��
> (�鿴 [Constructors](classes.html#constructors)).
>
> ``` kotlin
> data class User(val name: String = "", val age: Int = 0)
> ```

## ����
  
�ںܶ�����£�����������Ҫ��һЩ�������޸Ķ������Ĳ��䡣
�����`copy()`�����������Դ���������ĵ�`User`�࣬Ӧ������ôʵ�����������
     
``` kotlin
fun copy(name: String = this.name, age: Int = this.age) = User(name, age)     
```     

Ҳ������ôд

``` kotlin
val jack = User(name = "Jack", age = 1)
val olderJack = jack.copy(age = 2)
```

## ������Ͷ�������

_��Ա����_����ʹ���������[������](multi-declarations.html)��

``` kotlin
val jane = User("Jane", 35) 
val (name, age) = jane
println("$name, $age years of age") // prints "Jane, 35 years of age"
```

## ��׼������

�ڱ�׼���ṩ��`Pair`��`Triple`���ںܶ�����£���ʹ������������һ�����õ����ѡ��
��Ϊ�����ô���ɶ��Ը�ǿ��

---

����By Wahchi
