---
description: '자세한 정보: 컴파일러 경고 (수준 1) C4829'
title: 컴파일러 경고(수준 1) C4829
ms.date: 11/04/2016
f1_keywords:
- C4829
helpviewer_keywords:
- C4829
ms.assetid: 4ffabe2b-2ddc-4c52-8564-d1355c93cfa6
ms.openlocfilehash: ae44c50e7b680dff94427896eea2e10c4ed33483
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97198026"
---
# <a name="compiler-warning-level-1-c4829"></a>컴파일러 경고(수준 1) C4829

main 함수에 대한 매개 변수가 잘못된 것 같습니다. ' Intmain (Platform:: Array \<Platform::String^> ^ argv) ' 고려

main과 같은 특정 함수는 참조 형식 매개 변수를 사용할 수 없습니다. 컴파일은 성공하지만 결과 이미지가 실행되지 않을 수 있습니다.

다음 샘플에서는 C4829를 생성합니다.

```cpp
// C4829.cpp
// compile by using: cl /EHsc /ZW /W4 /c C4829.cpp
int main(Platform::String ^ s) {}   // C4829
```
