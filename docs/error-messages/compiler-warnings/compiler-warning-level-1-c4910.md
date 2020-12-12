---
description: '자세한 정보: 컴파일러 경고 (수준 1) C4910'
title: 컴파일러 경고(수준 1) C4910
ms.date: 11/04/2016
f1_keywords:
- C4910
helpviewer_keywords:
- C4910
ms.assetid: 67963560-fbca-4ca7-93db-06beaf7055f0
ms.openlocfilehash: 4798ba8ae8005239c9cf83e109bdb0f9e4c01928
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97291456"
---
# <a name="compiler-warning-level-1-c4910"></a>컴파일러 경고(수준 1) C4910

' \<identifier> ': ' __declspec (dllexport) ' 및 ' extern '은 (는) 명시적 인스턴스화에 호환 되지 않습니다.

이라는 명시적 템플릿 인스턴스화는 *\<identifier>* 및 키워드에 의해 수정 `__declspec(dllexport)` 됩니다 **`extern`** . 그러나 이러한 키워드는 함께 사용할 수 없습니다. `__declspec(dllexport)`키워드는 템플릿 클래스의 인스턴스화를 의미 하는 반면, **`extern`** 키워드는 템플릿 클래스를 자동으로 인스턴스화하지 않음을 의미 합니다.

## <a name="see-also"></a>참고 항목

[명시적 인스턴스화](../../cpp/explicit-instantiation.md)<br/>
[dllexport, dllimport](../../cpp/dllexport-dllimport.md)<br/>
[일반 규칙 및 제한 사항](../../cpp/general-rules-and-limitations.md)
