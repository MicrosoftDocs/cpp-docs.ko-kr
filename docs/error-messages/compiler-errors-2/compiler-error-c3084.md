---
description: '자세한 정보: 컴파일러 오류 C3084'
title: 컴파일러 오류 C3084
ms.date: 11/04/2016
f1_keywords:
- C3084
helpviewer_keywords:
- C3084
ms.assetid: 0362cb70-e24e-476f-a24d-8f5bb97c3afd
ms.openlocfilehash: 8603930e9087f1e407d5e8df65078604836b9a16
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97320121"
---
# <a name="compiler-error-c3084"></a>컴파일러 오류 C3084

'function': 종료자/소멸자는 'keyword'가 될 수 없습니다.

종료자 또는 소멸자를 잘못 선언했습니다.

예를 들어 소멸자를 sealed로 표시하면 안 됩니다.  파생 형식이 소멸자에 액세스할 수 없습니다.  자세한 내용은 [방법: 클래스 및 구조체 정의 및 사용 (c + +/cli)의](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers) [명시적 재정의](../../extensions/explicit-overrides-cpp-component-extensions.md) 및 소멸자 및 종료자를 참조 하세요.

## <a name="example"></a>예제

다음 샘플에서는 C3084를 생성합니다.

```cpp
// C3084.cpp
// compile with: /clr /c
ref struct R {
protected:
   !R() sealed;   // C3084
   !R() abstract;   // C3084
   !R();
};
```
