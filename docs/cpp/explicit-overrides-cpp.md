---
description: '자세히 알아보기: 명시적 재정의 (c + +)'
title: 명시적 재정의 (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- virtual functions [C++], explicit overrides
- overriding, functions
- derived classes [C++], virtual functions
- explicit virtual function overrides
- explicit override of virtual function
ms.assetid: ee583234-5cda-4e90-b55e-3f9fbf079ced
ms.openlocfilehash: 4abb57c16f8fc4105b4fe3bb598cb84f66d07de9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97273412"
---
# <a name="explicit-overrides-c"></a>명시적 재정의 (C++)

**Microsoft 전용**

둘 이상의 [인터페이스](../cpp/interface.md) 에서 동일한 가상 함수를 선언 하 고 클래스가 이러한 인터페이스에서 파생 되는 경우 각 가상 함수를 명시적으로 재정의할 수 있습니다.

C + +/CLI를 사용 하 여 관리 코드의 명시적 재정의에 대 한 자세한 내용은 [명시적 재정의](../extensions/explicit-overrides-cpp-component-extensions.md)를 참조 하세요.

**Microsoft 전용 종료**

## <a name="example"></a>예제

다음 코드 예제에서는 명시적 재정의를 사용하는 방법을 보여 줍니다.

```cpp
// deriv_ExplicitOverrides.cpp
// compile with: /GR
extern "C" int printf_s(const char *, ...);

__interface IMyInt1 {
   void mf1();
   void mf1(int);
   void mf2();
   void mf2(int);
};

__interface IMyInt2 {
   void mf1();
   void mf1(int);
   void mf2();
   void mf2(int);
};

class CMyClass : public IMyInt1, public IMyInt2 {
public:
   void IMyInt1::mf1() {
      printf_s("In CMyClass::IMyInt1::mf1()\n");
   }

   void IMyInt1::mf1(int) {
      printf_s("In CMyClass::IMyInt1::mf1(int)\n");
   }

   void IMyInt1::mf2();
   void IMyInt1::mf2(int);

   void IMyInt2::mf1() {
      printf_s("In CMyClass::IMyInt2::mf1()\n");
   }

   void IMyInt2::mf1(int) {
         printf_s("In CMyClass::IMyInt2::mf1(int)\n");
   }

   void IMyInt2::mf2();
   void IMyInt2::mf2(int);
};

void CMyClass::IMyInt1::mf2() {
   printf_s("In CMyClass::IMyInt1::mf2()\n");
}

void CMyClass::IMyInt1::mf2(int) {
   printf_s("In CMyClass::IMyInt1::mf2(int)\n");
}

void CMyClass::IMyInt2::mf2() {
   printf_s("In CMyClass::IMyInt2::mf2()\n");
}

void CMyClass::IMyInt2::mf2(int) {
   printf_s("In CMyClass::IMyInt2::mf2(int)\n");
}

int main() {
   IMyInt1 *pIMyInt1 = new CMyClass();
   IMyInt2 *pIMyInt2 = dynamic_cast<IMyInt2 *>(pIMyInt1);

   pIMyInt1->mf1();
   pIMyInt1->mf1(1);
   pIMyInt1->mf2();
   pIMyInt1->mf2(2);
   pIMyInt2->mf1();
   pIMyInt2->mf1(3);
   pIMyInt2->mf2();
   pIMyInt2->mf2(4);

   // Cast to a CMyClass pointer so that the destructor gets called
      CMyClass *p = dynamic_cast<CMyClass *>(pIMyInt1);
      delete p;
}
```

```Output
In CMyClass::IMyInt1::mf1()
In CMyClass::IMyInt1::mf1(int)
In CMyClass::IMyInt1::mf2()
In CMyClass::IMyInt1::mf2(int)
In CMyClass::IMyInt2::mf1()
In CMyClass::IMyInt2::mf1(int)
In CMyClass::IMyInt2::mf2()
In CMyClass::IMyInt2::mf2(int)
```

## <a name="see-also"></a>추가 정보

[상속](../cpp/inheritance-cpp.md)
