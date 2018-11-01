---
title: 컴파일러 오류 C3888
ms.date: 11/04/2016
f1_keywords:
- C3888
helpviewer_keywords:
- C3888
ms.assetid: 40820812-79c5-4dcd-a19d-b4164d25fc8a
ms.openlocfilehash: 067412e59041cb98b68cb373c4671c243ab8a0ec
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50479068"
---
# <a name="compiler-error-c3888"></a>컴파일러 오류 C3888

'name': 이 리터럴 데이터 멤버와 연관된 const 식은 C++/CLI에서 지원되지 않습니다.

*literal* 키워드로 선언된 [name](../../windows/literal-cpp-component-extensions.md) 데이터 멤버가 컴파일러에서 지원하지 않는 값으로 초기화되었습니다. 컴파일러는 상수 정수, 열거형 또는 문자열 형식만 지원합니다. **C3888** 오류의 일반적인 원인은 데이터 멤버가 바이트 배열로 초기화되었기 때문입니다.

### <a name="to-correct-this-error"></a>이 오류를 해결하려면

1. 선언된 리터럴 데이터 멤버가 지원되는 형식인지 확인합니다.

## <a name="see-also"></a>참고 항목

[name](../../windows/literal-cpp-component-extensions.md)