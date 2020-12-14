---
description: '자세한 정보: 컴파일러 오류 C3646'
title: 컴파일러 오류 C3646
ms.date: 06/14/2018
f1_keywords:
- C3646
helpviewer_keywords:
- C3646
ms.assetid: 4391ead2-9637-4ca3-aeda-5a991b18d66d
ms.openlocfilehash: 0c6f731a09612e6c128756de8d0690c922047e49
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97203785"
---
# <a name="compiler-error-c3646"></a>컴파일러 오류 C3646

> ' 지정자 ': 알 수 없는 재정의 지정자입니다.

## <a name="remarks"></a>설명

컴파일러가 재정의 지정자를 찾을 것으로 예상 되는 위치에서 토큰을 찾았지만 컴파일러가 토큰을 인식 하지 못했습니다.

예를 들어, 인식할 수 없는 *지정 자가* **_NOEXCEPT** 이면이를 키워드로 바꿉니다 **`noexcept`** .

자세한 내용은 [Override 지정자](../../extensions/override-specifiers-cpp-component-extensions.md)를 참조 하세요.

## <a name="example"></a>예제

다음 샘플에서는 C3646를 생성 하 고 수정 하는 방법을 보여 줍니다.

```cpp
// C3646.cpp
// compile with: /clr /c
ref class C {
   void f() unknown;   // C3646
   // try the following line instead
   // virtual void f() abstract;
};
```
