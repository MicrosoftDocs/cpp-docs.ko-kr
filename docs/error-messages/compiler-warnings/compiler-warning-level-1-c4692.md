---
description: '자세한 정보: 컴파일러 경고 (수준 1) C4692'
title: 컴파일러 경고(수준 1) C4692
ms.date: 11/04/2016
f1_keywords:
- C4692
helpviewer_keywords:
- C4692
ms.assetid: f6fb3acc-8228-491a-9c30-ce302d8a9c75
ms.openlocfilehash: 7c38a2bd4bfd4de943f64483cd8a9e96ece0b580
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97249128"
---
# <a name="compiler-warning-level-1-c4692"></a>컴파일러 경고(수준 1) C4692

'function': 전용이 아닌 멤버의 시그니처에 어셈블리 전용 네이티브 형식 'native_type'이(가) 있습니다.

어셈블리 외부에 표시 되는 형식에 어셈블리 외부에 표시 되지 않는 네이티브 형식을 포함 하는 멤버 함수가 포함 되어 있습니다. 따라서 포함 하는 형식이 어셈블리 외부에서 인스턴스화되면 멤버 함수를 호출 하면 안 됩니다.

자세한 내용은 [형식 표시 유형](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Type_visibility)을 참조 하세요.

기본적으로 이 경고는 해제되어 있습니다. 자세한 내용은 [Compiler Warnings That Are Off by Default](../../preprocessor/compiler-warnings-that-are-off-by-default.md)을 참조하세요.

## <a name="example"></a>예제

다음 샘플에서는 C4692를 생성 합니다.

```cpp
// C4692.cpp
// compile with: /W1 /c /clr
#pragma warning(default:4692)
class Private_Native_Class {};
public class Public_Native_Class {};
public ref class Public_Ref_Class {
public:
   void Test(Private_Native_Class *) {}   // C4692
   void Test2(Public_Native_Class *) {}   // OK
};
```
