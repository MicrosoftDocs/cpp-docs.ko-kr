---
title: 컴파일러 경고 (수준 1) C4190 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4190
dev_langs:
- C++
helpviewer_keywords:
- C4190
ms.assetid: a4d0ad93-a19a-4063-addd-36d605831567
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d398331c159c6fc639160dbe54d6ab5f969d3dbd
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46063738"
---
# <a name="compiler-warning-level-1-c4190"></a>컴파일러 경고 (수준 1) C4190

'identifier1' C 링크를 지정 했지만 'identifier2' C와 호환 되지 않는 UDT를 반환 합니다.

반환 형식으로 함수 또는 함수에 대 한 포인터에 UDT (사용자 정의 형식, 클래스, 구조체, 열거형 또는 공용 구조체) 및 `extern` "C" 링크가 있습니다. 이 유효 하는 경우:

- 이 함수에 대 한 모든 호출 c + +에서 발생합니다.

- C + +에서 함수 정의.

## <a name="example"></a>예제

```cpp
// C4190.cpp
// compile with: /W1 /LD
struct X
{
   int i;
   X ();
   virtual ~X ();
};

extern "C" X func ();   // C4190
```