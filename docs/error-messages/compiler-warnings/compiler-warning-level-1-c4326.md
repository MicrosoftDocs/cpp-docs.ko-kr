---
description: '자세한 정보: 컴파일러 경고 (수준 1) C4326'
title: 컴파일러 경고(수준 1) C4326
ms.date: 08/27/2018
f1_keywords:
- C4326
helpviewer_keywords:
- C4326
ms.assetid: d44d2c4e-9456-42d3-b35b-4ba4b2d42ec7
ms.openlocfilehash: d7c82d7a0157b53e60281bbe7c45a38cc765a73d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97340048"
---
# <a name="compiler-warning-level-1-c4326"></a>컴파일러 경고(수준 1) C4326

> '*function*'의 반환 형식은 '*type2*' 대신 '*type1*' 이어야 합니다.

## <a name="remarks"></a>설명

함수가 *type1* 이외의 형식을 반환 했습니다. 예를 들어 [/za](../../build/reference/za-ze-disable-language-extensions.md)를 사용 하는 경우 **main** 은를 반환 하지 않습니다 **`int`** .

## <a name="example"></a>예제

다음 샘플에서는 C4326을 생성 하 고 수정 하는 방법을 보여 줍니다.

```cpp
// C4326.cpp
// compile with: /Za /W1
char main()
{
    // C4326, instead use int main()
}
```
