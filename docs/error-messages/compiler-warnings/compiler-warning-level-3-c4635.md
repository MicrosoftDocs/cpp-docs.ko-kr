---
description: '자세한 정보: 컴파일러 경고 (수준 3) C4635'
title: 컴파일러 경고(수준 3) C4635
ms.date: 11/04/2016
f1_keywords:
- C4635
helpviewer_keywords:
- C4635
ms.assetid: b2ba90de-c093-4a76-8076-b65878467574
ms.openlocfilehash: e885c501e4f10719618bb552c153dc13a481332d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97168334"
---
# <a name="compiler-warning-level-3-c4635"></a>컴파일러 경고(수준 3) C4635

XML 문서 주석 대상: 잘못된 형식의 XML: 이유

컴파일러가 XML 태그에서 일부 문제를 발견했습니다.  문제를 수정하고 다시 컴파일합니다.

다음 샘플에서는 C4635를 생성합니다.

```cpp
// C4635.cpp
// compile with: /doc /clr /W3 /c
/// <summary>
/// The contents of the folder have changed.
/// <summary/>   // C4635

// try the following line instead
// /// </summary>
public ref class Test {};
```

이 샘플은 **끝 태그 'member'가 시작 태그 'summary'와 일치하지 않습니다** 를 출력합니다.

이 샘플의 문제는의 끝 태그 \<summary> 형식이 잘못 되었고 컴파일러가 끝 태그로 인식 하지 못하는 것입니다 \<summary> .  \<member>태그는 모든/doc 컴파일의 컴파일러에 의해 .xdc 파일에 포함 됩니다.  따라서 여기서의 문제는 \</member> 컴파일러에서 처리 된 이전 시작 태그와 일치 하지 않는 끝 태그입니다 \<summary> .
