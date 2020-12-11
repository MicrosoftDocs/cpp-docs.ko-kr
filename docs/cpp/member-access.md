---
description: '자세한 정보: 멤버 액세스'
title: 멤버 액세스
ms.date: 11/04/2016
helpviewer_keywords:
- member-selection operators [C++]
- pointers, smart
- member access, overloaded operators
- operator overloading [C++], member access operators
- smart pointers, definition
- smart pointers
ms.assetid: 8c7b2c43-eb92-4d42-9a8e-61aa37d71333
ms.openlocfilehash: c35eb2e7e24da9f8e8988b47ebfd8a59df815cee
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97161717"
---
# <a name="member-access"></a>멤버 액세스

멤버 액세스 연산자 ()를 오버 로드 하 여 클래스 멤버 액세스를 제어할 수 있습니다 **->** . 이 연산자는 이 사용법에서 단항 연산자로 간주되며 오버로드된 연산자 함수가 클래스 멤버 함수여야 합니다. 따라서 이러한 함수의 선언은 다음과 같습니다.

## <a name="syntax"></a>구문

```
class-type *operator->()
```

## <a name="remarks"></a>설명

여기서 *class-type* 은이 연산자가 속한 클래스의 이름입니다. 멤버 액세스 연산자 함수는 비정적 멤버 함수여야 합니다.

이 연산자는 역참조나 개수 사용법에 앞서 포인터의 유효성을 검사하는 "스마트 포인터"를 구현하는 데 사용되며 종종 포인터 역참조 연산자와 함께 사용됩니다.

**.** 멤버 액세스 연산자를 오버 로드할 수 없습니다.

## <a name="see-also"></a>참고 항목

[연산자 오버로드](../cpp/operator-overloading.md)
