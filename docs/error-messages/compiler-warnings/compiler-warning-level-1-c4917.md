---
description: '자세한 정보: 컴파일러 경고 (수준 1) C4917'
title: 컴파일러 경고(수준 1) C4917
ms.date: 11/04/2016
f1_keywords:
- C4917
helpviewer_keywords:
- C4917
ms.assetid: c05e2610-4a5d-4f4b-a99b-c15fd7f1d5f1
ms.openlocfilehash: b85d9dced285eade22cf6b8ff61657cd53703b88
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97291430"
---
# <a name="compiler-warning-level-1-c4917"></a>컴파일러 경고(수준 1) C4917

' 선언 자 ': GUID는 클래스, 인터페이스 또는 네임 스페이스와만 연결할 수 있습니다.

[클래스](../../cpp/class-cpp.md), [인터페이스](../../cpp/interface.md)또는 [네임 스페이스](../../cpp/namespaces-cpp.md) 이외의 사용자 정의 구조에는 GUID를 사용할 수 없습니다.

기본적으로 이 경고는 해제되어 있습니다. 자세한 내용은 [기본적으로 해제되어 있는 컴파일러 경고](../../preprocessor/compiler-warnings-that-are-off-by-default.md) 를 참조하세요.

## <a name="example"></a>예제

다음 코드 샘플에서는 C4917를 생성 합니다.

```cpp
// C4917.cpp
// compile with: /W1
#pragma warning(default : 4917)
__declspec(uuid("00000000-0000-0000-0000-000000000001")) struct S
{
} s;   // C4917, don't put uuid on a struct

int main()
{
}
```
