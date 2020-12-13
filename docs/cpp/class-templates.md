---
description: '자세히 알아보기: 클래스 템플릿'
title: 클래스 템플릿
ms.date: 11/04/2016
helpviewer_keywords:
- classes [C++], operating on type
- class templates
- templates, class templates
ms.assetid: 633a53c8-24ee-4c23-8c88-e7c3cb0b7ac3
ms.openlocfilehash: 3b82cb03fb6f33b8895a6877de98665419902333
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97335574"
---
# <a name="class-templates"></a>클래스 템플릿

이 항목에서는 c + + 클래스 템플릿과 관련 된 규칙을 설명 합니다.

## <a name="member-functions-of-class-templates"></a>클래스 템플릿의 멤버 함수

멤버 함수는 클래스 템플릿의 내부 또는 외부에서 정의할 수 있습니다. 클래스 템플릿의 외부에서 정의하는 경우 함수 템플릿과 마찬가지로 정의됩니다.

```cpp
// member_function_templates1.cpp
template<class T, int i> class MyStack
{
    T*  pStack;
    T StackBuffer[i];
    static const int cItems = i * sizeof(T);
public:
    MyStack( void );
    void push( const T item );
    T& pop( void );
};

template< class T, int i > MyStack< T, i >::MyStack( void )
{
};

template< class T, int i > void MyStack< T, i >::push( const T item )
{
};

template< class T, int i > T& MyStack< T, i >::pop( void )
{
};

int main()
{
}
```

템플릿 클래스 멤버 함수의 경우와 마찬가지로 클래스의 생성자 멤버 함수에 대한 정의에는 템플릿 인수 목록이 두 번 포함됩니다.

다음 예제와 같이 멤버 함수는 추가 매개 변수를 지정하여 그 자체가 함수 템플릿이 될 수 있습니다.

```cpp
// member_templates.cpp
template<typename T>
class X
{
public:
   template<typename U>
   void mf(const U &u);
};

template<typename T> template <typename U>
void X<T>::mf(const U &u)
{
}

int main()
{
}
```

## <a name="nested-class-templates"></a>중첩 된 클래스 템플릿

클래스 또는 클래스 템플릿 안에 템플릿을 정의할 수 있으며 이 경우 멤버 템플릿이라고 합니다. 클래스인 멤버 템플릿은 중첩된 클래스 템플릿이라고 합니다. 함수에 해당 하는 멤버 템플릿은 [멤버 함수 템플릿에서](../cpp/member-function-templates.md)설명 합니다.

중첩된 클래스 템플릿은 바깥쪽 클래스의 범위 안에 클래스 템플릿으로 선언되며 바깥쪽 클래스 안이나 밖에 정의할 수 있습니다.

다음 코드에서는 일반 클래스 안에 중첩된 클래스 템플릿을 보여 줍니다.

```cpp
// nested_class_template1.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

class X
{

   template <class T>
   struct Y
   {
      T m_t;
      Y(T t): m_t(t) { }
   };

   Y<int> yInt;
   Y<char> yChar;

public:
   X(int i, char c) : yInt(i), yChar(c) { }
   void print()
   {
      cout << yInt.m_t << " " << yChar.m_t << endl;
   }
};

int main()
{
   X x(1, 'a');
   x.print();
}
```

```cpp
// nested_class_template2.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

template <class T>
class X
{
   template <class U> class Y
   {
      U* u;
   public:
      Y();
      U& Value();
      void print();
      ~Y();
   };

   Y<int> y;
public:
   X(T t) { y.Value() = t; }
   void print() { y.print(); }
};

template <class T>
template <class U>
X<T>::Y<U>::Y()
{
   cout << "X<T>::Y<U>::Y()" << endl;
   u = new U();
}

template <class T>
template <class U>
U& X<T>::Y<U>::Value()
{
   return *u;
}

template <class T>
template <class U>
void X<T>::Y<U>::print()
{
   cout << this->Value() << endl;
}

template <class T>
template <class U>
X<T>::Y<U>::~Y()
{
   cout << "X<T>::Y<U>::~Y()" << endl;
   delete u;
}

int main()
{
   X<int>* xi = new X<int>(10);
   X<char>* xc = new X<char>('c');
   xi->print();
   xc->print();
   delete xi;
   delete xc;
}

//Output:
X<T>::Y<U>::Y()
X<T>::Y<U>::Y()
10
99
X<T>::Y<U>::~Y()
X<T>::Y<U>::~Y()
```

지역 클래스에는 멤버 템플릿이 허용되지 않습니다.

## <a name="template-friends"></a>템플릿 친구

클래스 템플릿에는 [친구가](friend-cpp.md)있을 수 있습니다. 클래스 또는 클래스 템플릿, 함수 또는 함수 템플릿은 템플릿 클래스에 대한 friend일 수 있습니다. friends는 클래스 템플릿 또는 함수 템플릿의 특수화가 될 수도 있지만 부분 특수화는 될 수 없습니다.

다음 예제에서 friend 함수는 클래스 템플릿 내에서 함수 템플릿으로 정의됩니다. 이 코드는 모든 템플릿 인스턴스화에 대한 friend 함수 버전을 만듭니다. 이 구문은 사용자의 friend 함수가 클래스와 같은 템플릿 매개 변수로 결정될 경우 유용합니다.

```cpp
// template_friend1.cpp
// compile with: /EHsc

#include <iostream>
using namespace std;

template <class T> class Array {
   T* array;
   int size;

public:
   Array(int sz): size(sz) {
      array = new T[size];
      memset(array, 0, size * sizeof(T));
   }

   Array(const Array& a) {
      size = a.size;
      array = new T[size];
      memcpy_s(array, a.array, sizeof(T));
   }

   T& operator[](int i) {
      return *(array + i);
   }

   int Length() { return size; }

   void print() {
      for (int i = 0; i < size; i++)
         cout << *(array + i) << " ";

      cout << endl;
   }

   template<class T>
   friend Array<T>* combine(Array<T>& a1, Array<T>& a2);
};

template<class T>
Array<T>* combine(Array<T>& a1, Array<T>& a2) {
   Array<T>* a = new Array<T>(a1.size + a2.size);
   for (int i = 0; i < a1.size; i++)
      (*a)[i] = *(a1.array + i);

   for (int i = 0; i < a2.size; i++)
      (*a)[i + a1.size] = *(a2.array + i);

   return a;
}

int main() {
   Array<char> alpha1(26);
   for (int i = 0 ; i < alpha1.Length() ; i++)
      alpha1[i] = 'A' + i;

   alpha1.print();

   Array<char> alpha2(26);
   for (int i = 0 ; i < alpha2.Length() ; i++)
      alpha2[i] = 'a' + i;

   alpha2.print();
   Array<char>*alpha3 = combine(alpha1, alpha2);
   alpha3->print();
   delete alpha3;
}
//Output:
A B C D E F G H I J K L M N O P Q R S T U V W X Y Z
a b c d e f g h i j k l m n o p q r s t u v w x y z
A B C D E F G H I J K L M N O P Q R S T U V W X Y Z a b c d e f g h i j k l m n o p q r s t u v w x y z
```

다음 예제에서는 템플릿 특수화를 가진 friend를 다룹니다. 원본 함수 템플릿이 friend인 경우 함수 템플릿 특수화는 자동으로 friend입니다.

또한 다음 코드의 friend 선언 앞의 주석이 나타내는 것처럼 템플릿의 특수화 버전만 friend로 선언할 수 있습니다. 이렇게 하면 friend 템플릿 특수화 정의를 템플릿 클래스 외부에 배치해야 합니다.

```cpp
// template_friend2.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

template <class T>
class Array;

template <class T>
void f(Array<T>& a);

template <class T> class Array
{
    T* array;
    int size;

public:
    Array(int sz): size(sz)
    {
        array = new T[size];
        memset(array, 0, size * sizeof(T));
    }
    Array(const Array& a)
    {
        size = a.size;
        array = new T[size];
        memcpy_s(array, a.array, sizeof(T));
    }
    T& operator[](int i)
    {
        return *(array + i);
    }
    int Length()
    {
        return size;
    }
    void print()
    {
        for (int i = 0; i < size; i++)
        {
            cout << *(array + i) << " ";
        }
        cout << endl;
    }
    // If you replace the friend declaration with the int-specific
    // version, only the int specialization will be a friend.
    // The code in the generic f will fail
    // with C2248: 'Array<T>::size' :
    // cannot access private member declared in class 'Array<T>'.
    //friend void f<int>(Array<int>& a);

    friend void f<>(Array<T>& a);
};

// f function template, friend of Array<T>
template <class T>
void f(Array<T>& a)
{
    cout << a.size << " generic" << endl;
}

// Specialization of f for int arrays
// will be a friend because the template f is a friend.
template<> void f(Array<int>& a)
{
    cout << a.size << " int" << endl;
}

int main()
{
    Array<char> ac(10);
    f(ac);

    Array<int> a(10);
    f(a);
}
//Output:
10 generic
10 int
```

다음 예제에서는 클래스 템플릿 내에 선언된 friend 클래스 템플릿을 보여 줍니다. 클래스 템플릿은 friend 클래스의 템플릿 인수로 사용됩니다. friend 클래스 템플릿은 선언된 클래스 템플릿의 외부에 정의되어야 합니다. 또한 friend 템플릿의 모든 특수화 또는 부분 특수화는 원본 클래스 템플릿의 friend입니다.

```cpp
// template_friend3.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

template <class T>
class X
{
private:
   T* data;
   void InitData(int seed) { data = new T(seed); }
public:
   void print() { cout << *data << endl; }
   template <class U> friend class Factory;
};

template <class U>
class Factory
{
public:
   U* GetNewObject(int seed)
   {
      U* pu = new U;
      pu->InitData(seed);
      return pu;
   }
};

int main()
{
   Factory< X<int> > XintFactory;
   X<int>* x1 = XintFactory.GetNewObject(65);
   X<int>* x2 = XintFactory.GetNewObject(97);

   Factory< X<char> > XcharFactory;
   X<char>* x3 = XcharFactory.GetNewObject(65);
   X<char>* x4 = XcharFactory.GetNewObject(97);
   x1->print();
   x2->print();
   x3->print();
   x4->print();
}
//Output:
65
97
A
a
```

## <a name="reuse-of-template-parameters"></a>템플릿 매개 변수 다시 사용

템플릿 매개 변수는 템플릿 매개 변수 목록에서 다시 사용할 수 있습니다. 예를 들어 다음 코드는 허용됩니다.

```cpp
// template_specifications2.cpp

class Y
{
};
template<class T, T* pT> class X1
{
};
template<class T1, class T2 = T1> class X2
{
};

Y aY;

X1<Y, &aY> x1;
X2<int> x2;

int main()
{
}
```

## <a name="see-also"></a>참고 항목

[템플릿](../cpp/templates-cpp.md)
