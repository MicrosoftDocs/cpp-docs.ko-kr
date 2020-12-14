---
description: '자세한 정보: 컴파일러 오류 C2244'
title: 컴파일러 오류 C2244
ms.date: 11/04/2016
f1_keywords:
- C2244
helpviewer_keywords:
- C2244
ms.assetid: d9911c12-ceb5-4f93-ac47-b44a485215c2
ms.openlocfilehash: 9f541eca155b9d728f0bbf7cb1578a6e3424c49c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97302245"
---
# <a name="compiler-error-c2244"></a>컴파일러 오류 C2244

' identifier ': 함수 정의를 기존 선언과 일치 시킬 수 없습니다.

괄호를 포함 하지 않는 함수 호출 앞에 단항 + 연산자의 비정상적인 사용이 사용 되었습니다.

이 오류는 c + + 프로젝트 에서만 발생 합니다.

다음 샘플에서는 C2244를 생성 합니다.

```cpp
// C2244.cpp
int func(char) {
   return 0;
}

int func(int) {
   return 0;
}

int main() {
   +func;   // C2244
}
```

C2244는 클래스 템플릿의 멤버 함수에 잘못 된 함수 시그니처를 사용 하는 경우에도 발생할 수 있습니다.

```cpp
// C2244b.cpp
// compile with: /c
template<class T>
class XYZ {
   void func(T t);
};

template<class T>
void XYZ<T>::func(int i) {}   // C2244 wrong function signature
// try the following line instead
// void XYZ<T>::func(T t) {}
```

C2244는 멤버 함수 템플릿에 잘못 된 함수 시그니처를 사용 하는 경우에도 발생할 수 있습니다.

```cpp
// C2244c.cpp
// compile with: /c
class ABC {
   template<class T>
   void func(int i, T t);
};

template<class T>
void ABC::func(int i) {}   // C2244 wrong signature
// try the following line instead
// void ABC::func(int i, T t) {}
```

함수 템플릿은 부분적으로 특수화할 수 없습니다.

```cpp
// C2244d.cpp
template<class T, class U>
class QRS {
   void func(T t, U u);
};

template<class T>
void QRS<T,int>::func(T t, int u) {}   // C2244
```
