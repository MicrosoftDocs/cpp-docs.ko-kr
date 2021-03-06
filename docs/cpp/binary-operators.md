---
description: '자세한 정보: 이항 연산자'
title: 이항 연산자
ms.date: 06/14/2018
helpviewer_keywords:
- member-selection operators [C++]
- operators [C++], binary
- binary operators [C++]
ms.assetid: c0e7fbff-bc87-4708-8333-504ac09ee83e
ms.openlocfilehash: cfb897a3df7cdb3d76f7af82f694e1cf09284cc7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97229602"
---
# <a name="binary-operators"></a>이항 연산자

다음 표에서는 오버로드될 수 있는 연산자 목록을 보여 줍니다.

## <a name="redefinable-binary-operators"></a>다시 정의 가능 이항 연산자

|연산자|Name|
|--------------|----------|
|**,**|쉼표|
|**!=**|같지 않음|
|**%**|모듈러스|
|**%=**|모듈러스/할당|
|**&**|비트 AND|
|**&&**|논리적 AND|
|**&=**|비트 AND/할당|
|**&#42;**|곱하기|
|**&#42;=**|곱하기/할당|
|**+**|더하기|
|**+=**|더하기/할당|
|**-**|빼기|
|**-=**|빼기/할당|
|**->**|멤버 선택|
|**->&#42;**|멤버 포인터 선택|
|**/**|사업부|
|**/=**|나누기/할당|
|**<**|보다 작음|
|**<<**|왼쪽 |
|**<<=**|왼쪽 시프트/할당|
|**<=**|작거나 같음|
|**=**|할당|
|**==**|같음|
|**>**|초과|
|**>=**|크거나 같음|
|**>>**|오른쪽 Shift|
|**>>=**|오른쪽 시프트/할당|
|**^**|배타적 OR|
|**^=**|배타적 OR/할당|
|**&#124;**|포괄적 비트 OR|
|**&#124;=**|포괄적 비트 OR/할당|
|**&#124;&#124;**|논리적 OR|

이항 연산자 함수를 비정적 멤버로 선언하려면 해당 함수를 다음과 같은 형태로 선언해야 합니다.

> *ret-형식* **`operator`** *op* **(** *arg* **)**

여기서 *ret* 는 반환 형식이 고, *op* 는 앞의 표에 나와 있는 연산자 중 하나 이며, *arg* 는 모든 형식의 인수입니다.

이항 연산자 함수를 전역 함수로 선언하려면 해당 함수를 다음과 같은 형태로 선언해야 합니다.

> *ret-형식* **`operator`** *op* **(** _arg1_**,** _arg2_ **)**

여기서 *ret-형식* 및 *op* 는 멤버 연산자 함수에 대해 설명 된 대로, *arg1* 및 *arg2* 는 인수입니다. 인수 중 하나 이상이 클래스 형식이어야 합니다.

> [!NOTE]
> 이항 연산자의 반환 형식에 대한 제한은 없지만 대부분의 사용자 정의 이항 연산자는 클래스 형식이나 클래스 형식에 대한 참조를 반환합니다.

## <a name="see-also"></a>참고 항목

[연산자 오버로드](../cpp/operator-overloading.md)
