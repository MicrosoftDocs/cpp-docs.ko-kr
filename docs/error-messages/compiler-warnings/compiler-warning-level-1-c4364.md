---
description: '자세한 정보: 컴파일러 경고 (수준 1) C4364'
title: 컴파일러 경고(수준 1) C4364
ms.date: 11/04/2016
f1_keywords:
- C4364
helpviewer_keywords:
- C4364
ms.assetid: 1477634c-d60f-4570-ad16-1aaeae24ac7f
ms.openlocfilehash: 760676be4ba431ffa9c514316142b1a14ce87c8e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97311398"
---
# <a name="compiler-warning-level-1-c4364"></a>컴파일러 경고(수준 1) C4364

\#as_friend 특성이 없는 위치 (line_number)에 이전에 표시 되는 ' file ' 어셈블리에 대해를 사용 하 고 있습니다. as_friend 적용 되지 않음

`#using`지정 된 메타 데이터 파일에 대해 지시어가 반복 되었지만 **`as_friend`** 처음 발견 되는 한정자가 사용 되지 않았습니다. 컴파일러가 두 번째를 무시 합니다 **`as_friend`** .

자세한 내용은 [Friend 어셈블리 (c + +)](../../dotnet/friend-assemblies-cpp.md)를 참조 하세요.

## <a name="examples"></a>예제

다음 샘플에서는 구성 요소를 만듭니다.

```cpp
// C4364.cpp
// compile with: /clr /LD
ref class A {};
```

다음 샘플에서는 C4364를 생성 합니다.

```cpp
// C4364_b.cpp
// compile with: /clr /W1 /c
#using " C4364.dll"
#using " C4364.dll" as_friend   // C4364
```
