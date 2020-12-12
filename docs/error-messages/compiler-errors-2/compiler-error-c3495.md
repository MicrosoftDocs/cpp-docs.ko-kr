---
description: '자세한 정보: 컴파일러 오류 C3495'
title: 컴파일러 오류 C3495
ms.date: 11/04/2016
f1_keywords:
- C3495
helpviewer_keywords:
- C3495
ms.assetid: 1fd40cb8-8373-403d-b8a8-f08424a50807
ms.openlocfilehash: 3c04c80182dad32b539e09224fd9e303b3325578
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97113170"
---
# <a name="compiler-error-c3495"></a>컴파일러 오류 C3495

'var': 람다 캡처에는 자동 스토리지 기간이 있어야 합니다.

또는로 표시 된 변수와 같이 자동 저장 기간이 없는 변수를 캡처할 수 없습니다 **`static`** **`extern`** .

### <a name="to-correct-this-error"></a>이 오류를 해결하려면

- **`static`** **`extern`** 람다 식의 캡처 목록에 또는 변수를 전달 하지 마십시오.

## <a name="example"></a>예제

다음 예제에서는 **`static`** 변수가 `n` 람다 식의 캡처 목록에 표시 되기 때문에 C3495를 생성 합니다.

```cpp
// C3495.cpp

int main()
{
   static int n = 66;
   [&n]() { return n; }(); // C3495
}
```

## <a name="see-also"></a>참조

[람다 식](../../cpp/lambda-expressions-in-cpp.md)
