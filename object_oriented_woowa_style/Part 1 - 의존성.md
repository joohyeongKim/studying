# ππ»ββοΈ Reference 
- [μ°μν νν¬ μΈλ―Έλ](https://www.youtube.com/watch?v=dJ5C4qRqAgA&t=1785s)λ₯Ό μ°Έκ³ νμ¬ μμ±λ λ΄μ©μλλ€.

---

### κ°μ


>'μ€κ³', 'μμ‘΄μ±', 'λ³κ²½'μ κ°μ₯ λ§μ΄ μ¬μ©λλ λ¨μ΄μλλ€.


- μ£Όμ  : μμ‘΄μ±μ ν΅ν΄ μ€κ³ μ§νμν€κΈ°

- μ€κ³μ ν΅μ¬ -> 'μμ‘΄μ±μ μ΄λ»κ² κ΄λ¦¬νλλ'

- μ€κ³λ ? -> μ½λλ₯Ό μ΄λ»κ² λ°°μΉν  κ²μΈμ§μ λν μμ¬κ²°μ 

- μ΄λμ μ΄λ€ μ½λλ₯Ό λ¬μΌν κΉ -> 'λ³κ²½μ μν μ΄μ '

- λ³κ²½μ ν΅μ¬ -> μμ‘΄μ±

- Dependency(μμ‘΄μ±)μ΄λ? 
->__λ³κ²½μ μν μν₯μ λ°μ μ μλ κ°λ₯μ±__

---


### ν΄λμ€ μμ‘΄μ±

![class_dependency](https://velog.velcdn.com/images/urtimeislimited/post/2829d699-6a38-439d-8fe9-70b7755d1b3a/image.png)

Assosiation μ°κ΄κ΄κ³
Aν΄λμ€μ Bλ‘ κ° μ μλ κ²½λ‘λ₯Ό κ°μ§κ³  μλ κ²½μ° (μ½λ μ κ°μ²΄ μ°Έμ‘°)
```java
class A {
    private B b;
}
```


Dependency μμ‘΄κ΄κ³
νλΌλ―Έν°, λ¦¬ν΄ νμμ ν΄λΉ νμμ΄ λμ€κ±°λ λ©μλ λ΄λΆμμ ν΄λΉ νμ μΈμ€ν΄μ€λ₯Ό μμ±νλ κ²½μ°
(νλ ₯ μμ μ μΌμμ μΌλ‘ κ΄κ³ λ§Ίκ³  ππ)
```java
class A {
    public B method(B b) {
    	return new B();
    }
}
```

Inheritance μμ κ΄κ³
Bμ κ΅¬νμ Aκ° κ³μΉ -> Bμ λ³κ²½μ΄ μΌμ΄λ  λ Aλ ν¨κ» λ³κ²½
```java
class A extends B {

}
```

Realization μ€μ²΄ν κ΄κ³
```java
class A implements B {

}
```


### ν¨ν€μ§ μμ‘΄μ±

![package_dependency](https://velog.velcdn.com/images/urtimeislimited/post/025355fe-657d-4d44-a1d5-a82928e6c762/image.png)

A ν΄λμ€ μ½λμ import B ν¨ν€μ§κ° μλ€
-> ν¨ν€μ§ Aκ° ν¨ν€μ§ Bμ μμ‘΄μ ν΄μ
-> ν¨ν€μ§ Bμ μλ ν΄λμ€κ° λ°λ λ  A ν΄λμ€λ λ³κ²½

### μμ‘΄μ± κ΄λ¦¬μ μ’μ κ·μΉ
μ λ΅μ μλλΌκ³  νμ¬. νμ§λ§ μκ²¨ λ£μ.

#### μλ°©ν₯ μμ‘΄μ±μ νΌνλΌ


```java
class A {
    private B b;

    public void setA(B b) {
        this.b = b;
        this.b.setA(this);
    }
}

class B {

    private A a;

    public void setA(A a) {
        this.a = a;
    }
}

```

>Bκ° λ°λ λ Aλ λ³κ²½,
  λμμ Aκ° λ°λ λ Bλ λ³κ²½λκΈ° λλ¬Έ



κ°κΈμ μ΄λ©΄ μλ°©ν₯ κ΄κ³λ₯Ό νΌνκ³  λ¨λ°©ν₯μΌλ‘ λ°κΏμΌ νλ€.

λ¨λ°©ν₯
```java
class A {
    private B b;

    public void setA(B b) {
        this.b = b;
    }
}

class B {

}
```


#### λ€μ€μ±μ΄ μ μ λ°©ν₯μ μ ννλΌ

![2](https://velog.velcdn.com/images/urtimeislimited/post/7d284125-8203-4692-b158-f4f0d7ec91a5/image.png)


```java
class A {
     private Collection<B> bs;
}
class B{

}
```
Aμμ Bμ μ»¬λ μμ μΈμ€ν΄μ€ λ³μλ‘ μ‘κ±°λ, μ»¬λ μμ λν΄μμ‘΄μ±μ κ°μ§κ² νλ κ² λ³΄λ€λ λ°λ λ°©ν₯μ μμ‘΄μ±μ κ°μ§λλ‘ νλ κ²μ΄ ν¨μ¬ μ’λ€.

μ΄λ₯Ό μ μ§νκΈ° μν΄μ λ€μν μ΄μκ° λ°μνλ€. μ±λ₯μ΄μ, κ°μ²΄λ€μ κ΄κ³λ₯Ό μ μ§νκΈ° μν λΈλ ₯λ€μ΄ νμνλ―λ‘

__κ°κΈμ μ΄λ©΄ λ€μ€μ±μ΄ μ μ λ°©ν₯μΌλ‘ κ°μ²΄λ₯Ό μ€κ³νλ€.__



```java
class A{

}

class B {
     private A a;
}
```

Aκ° Bμ μ»¬λ μμ κ°μ§λ κ²λ³΄λ€ Bκ° Aμ λ¨λ°©ν₯ μ°Έμ‘°λ₯Ό κ°μ§λκ² κ°μ₯ μ’λ€.


#### μμ‘΄μ±μ΄ νμμλ€λ©΄ μ κ±°νλΌ

μ μΌ μ’μ κ±΄ μμ‘΄μ±μ΄ λΆνμνλ€λ©΄ μ κ±°ν΄λ²λ¦¬λ κ²

```java
class A {
    private B b;
}

class B {

}
```

```java
class A {

}
class B {

}
```
```java
class A {
    private B b;
}

class B {

}
```

```java
class A {

}
class B {

}
```


#### ν¨ν€μ§ μ¬μ΄ν΄ μμ‘΄μ±


ν¨ν€μ§ μ¬μ΄ μλ°©ν₯(λλ nλ°©ν₯)μμ‘΄μ± μ¬μ΄ν΄μ΄ μκΈ°μ§ μλλ‘ ν΄λΌ.
-> __λ³κ²½__μ΄ λμμ μΌμ΄λκΈ° λλ¬Έ!

![2](https://velog.velcdn.com/images/urtimeislimited/post/068fc2ed-6c20-45bf-9a6b-14f5da322ec5/image.png)

> __μ€κ³μ μμΉμ λ¬΄μ‘°κ±΄ 'λ³κ²½'__
λ΄κ° λ°°μΉνλ μ½λκ° μ΄λ»κ² λ°λ κ²μΈμ§μ λν΄ ν¬μ»€μ€λ₯Ό λ§μΆλ©΄ λλ€κ³  νμ¬.

---
