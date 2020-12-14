---
description: '자세한 정보: 컴파일러 오류 C2011'
title: 컴파일러 오류 C2011
ms.date: 11/04/2016
f1_keywords:
- C2011
helpviewer_keywords:
- C2011
ms.assetid: 992c9d51-e850-4d53-b86b-02e73b38249c
ms.openlocfilehash: c310495c570a2259cf5abe6acea951ca996bfb26
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97221022"
---
# <a name="compiler-error-c2011"></a>컴파일러 오류 C2011

'identifier': 'type' 형식 재정의

식별자가 `type`으로 이미 정의되었습니다. 식별자 재정의를 확인하세요.

헤더 파일 또는 형식 라이브러리를 동일한 파일로 두 번 이상 가져오는 경우 C2011 오류가 발생할 수도 있습니다. 헤더 파일에 정의 된 형식이 여러 번 포함 되는 것을 방지 하려면 헤더 파일의 include 가드 또는 `#pragma` [once](../../preprocessor/once.md) 지시문을 사용 합니다.

재정의 된 형식의 초기 선언을 찾아야 하는 경우 [/p](../../build/reference/p-preprocess-to-a-file.md) 컴파일러 플래그를 사용 하 여 컴파일러에 전달 되는 전처리 된 출력을 생성할 수 있습니다. 텍스트 검색 도구를 사용하여 출력 파일에서 다시 정의된 식별자의 인스턴스를 찾을 수 있습니다.

다음 샘플에서는 C2011 오류가 발생하는 경우 및 이를 해결하는 한 가지 방법을 보여 줍니다.

```cpp
// C2011.cpp
// compile with: /c
struct S;
union S;   // C2011
union S2;   // OK
```
