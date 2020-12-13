---
description: '자세한 정보: 컴파일러 경고 (수준 4) C4820'
title: 컴파일러 경고(수준 4) C4820
ms.date: 11/04/2016
f1_keywords:
- C4820
helpviewer_keywords:
- C4820
ms.assetid: 17aa29f4-c287-49b8-bc43-8ed82ffed5ea
ms.openlocfilehash: 778bf605d6ee1441e9efd68380c64d231df03b69
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97330477"
---
# <a name="compiler-warning-level-4-c4820"></a>컴파일러 경고(수준 4) C4820

'bytes'바이트 채움 문자가 construct 'member_name' 뒤에 추가되었습니다.

요소의 형식 및 순서에 따라 컴파일러가 구조체의 끝에 패딩을 추가 했습니다. 구조체의 안쪽 여백에 대 한 자세한 내용은 [align](../../cpp/align-cpp.md) 을 참조 하세요.

기본적으로 이 경고는 해제되어 있습니다. 자세한 내용은 [기본적으로 해제되어 있는 컴파일러 경고](../../preprocessor/compiler-warnings-that-are-off-by-default.md) 를 참조하세요.

다음 샘플에서는 C4820를 생성 합니다.

```cpp
// C4820.cpp
// compile with: /W4 /c
#pragma warning(default : 4820)

// Delete the following 4 lines to resolve.
__declspec(align(2)) struct MyStruct {
   char a;
   int i;   // C4820
};

// OK
#pragma pack(1)
__declspec(align(1)) struct MyStruct2 {
   char a;
   int i;
};
```
