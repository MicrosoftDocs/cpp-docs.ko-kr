---
description: '자세한 정보: 컴파일러 오류 C3227'
title: 컴파일러 오류 C3227
ms.date: 11/04/2016
f1_keywords:
- C3227
helpviewer_keywords:
- C3227
ms.assetid: 7939c23a-96c8-43c2-89e9-f217d132d155
ms.openlocfilehash: 26d66bf3e0c3bc3a6f391d66608f3e6790b2d11d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97304144"
---
# <a name="compiler-error-c3227"></a>컴파일러 오류 C3227

' parameter ': ' keyword '를 사용 하 여 제네릭 형식을 할당할 수 없습니다.

형식을 인스턴스화하기 위해 적절 한 생성자가 필요 합니다. 그러나 컴파일러에서 적절 한 생성자를 사용할 수 있는지 확인할 수 없습니다.

제네릭을 사용 하는 대신 템플릿을 사용 하 여이 오류를 해결 하거나 여러 가지 방법 중 하나를 사용 하 여 형식의 인스턴스를 만들 수 있습니다.

## <a name="example"></a>예제

다음 샘플에서는 C3227를 생성 합니다.

```cpp
// C3227.cpp
// compile with: /clr /c
generic<class T> interface class ICreate {
   static T Create();
};

generic <class T>
where T : ICreate<T>
ref class C {
   void f() {
      T t = new T;   // C3227

      // OK
      T t2 = ICreate<T>::Create();
      T t3 = safe_cast<T>( System::Activator::CreateInstance(T::typeid) );
   }
};
```
