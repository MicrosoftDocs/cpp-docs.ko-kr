---
description: '자세히 알아보기: 할당'
title: 할당
ms.date: 11/04/2016
f1_keywords:
- allocate_cpp
helpviewer_keywords:
- __declspec keyword [C++], allocate
- allocate __declspec keyword
ms.assetid: 67828b31-de60-4c0e-b0a6-ef3aab22641d
ms.openlocfilehash: 0a30b113ca9271dc53777073ea0a80bac0f16bcb
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97288284"
---
# <a name="allocate"></a>할당

**Microsoft 전용**

**`allocate`** 선언 지정자는 데이터 항목이 할당 되는 데이터 세그먼트의 이름을 지정 합니다.

## <a name="syntax"></a>Syntax

> **`__declspec(allocate("`***segname* **`))`** *선언 자*

## <a name="remarks"></a>설명

*Segname* 이름은 다음 pragma 중 하나를 사용 하 여 선언 해야 합니다.

- [code_seg](../preprocessor/code-seg.md)

- [const_seg](../preprocessor/const-seg.md)

- [data_seg](../preprocessor/data-seg.md)

- [init_seg](../preprocessor/init-seg.md)

- [여기서](../preprocessor/section.md)

## <a name="example"></a>예제

```cpp
// allocate.cpp
#pragma section("mycode", read)
__declspec(allocate("mycode"))  int i = 0;

int main() {
}
```

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[`__declspec`](../cpp/declspec.md)<br/>
[키워드](../cpp/keywords-cpp.md)
