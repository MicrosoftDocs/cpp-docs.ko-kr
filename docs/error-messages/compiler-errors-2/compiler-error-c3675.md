---
title: 컴파일러 오류 C3675 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3675
dev_langs:
- C++
helpviewer_keywords:
- C3675
ms.assetid: 87461613-6633-430b-b95d-c7cb1bb63776
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c4b6656753ab4a611dcb80d1473e0b44bf47a270
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46094782"
---
# <a name="compiler-error-c3675"></a>컴파일러 오류 C3675

'function': 'property' 정의 되어 있기 때문에 예약 되어

단순 속성을 선언 하면 컴파일러 생성 get 및 set 접근자 메서드 및 해당 이름은 프로그램의 범위에 존재 합니다.  컴파일러에서 생성 된 이름은 get_ 및 set_ 속성 이름에 추가 하 여 구성 됩니다.  따라서 컴파일러에서 생성 된 접근자와 같은 이름 사용 하 여 함수를 선언할 수 없습니다.

자세한 내용은 [property](../../windows/property-cpp-component-extensions.md) 를 참조하세요.

## <a name="example"></a>예제

다음 샘플 C3675를 생성합니다.

```
// C3675.cpp
// compile with: /clr /c
ref struct C {
public:
   property int Size;
   int get_Size() { return 0; }   // C3675
};
```