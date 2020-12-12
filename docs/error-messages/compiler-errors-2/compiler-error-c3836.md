---
description: '자세한 정보: 컴파일러 오류 C3836'
title: 컴파일러 오류 C3836
ms.date: 11/04/2016
f1_keywords:
- C3836
helpviewer_keywords:
- C3836
ms.assetid: 254f851b-7b7d-4c34-a740-fcf72f6a636a
ms.openlocfilehash: c7e05bbf95facf5b8552b4442138cc38b86703c0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97180879"
---
# <a name="compiler-error-c3836"></a>컴파일러 오류 C3836

정적 생성자에는 멤버 이니셜라이저 목록을 사용할 수 없습니다.

관리 되는 클래스에는 멤버 초기화 목록도 있는 정적 생성자가 있을 수 없습니다. 정적 클래스 생성자는 클래스 초기화를 수행 하기 위해 공용 언어 런타임에서 호출 되며, 정적 데이터 멤버를 초기화 합니다.

## <a name="example"></a>예제

다음 샘플에서는 C3836를 생성 합니다.

```cpp
// C3836a.cpp
// compile with: /clr
ref class M
{
   static int s_i;

public:
   static M() :  s_i(1234)   // C3836, delete initializer to resolve
   {
   }
};

int main()
{
}
```
