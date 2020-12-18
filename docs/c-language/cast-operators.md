---
description: '자세한 정보: 캐스트 연산자'
title: 캐스트 연산자
ms.date: 11/04/2016
helpviewer_keywords:
- cast operators
- type casts, operators
- operators [C++], cast
- type conversion, cast operators
ms.assetid: 43b90bbd-39ef-43e6-ae5d-e8a67a01de40
ms.openlocfilehash: 181d402e260cf4bf0970881226bf558282297333
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97214118"
---
# <a name="cast-operators"></a>캐스트 연산자

형식 캐스팅은 특정 상황에서의 개체 형식에 대한 명시적 변환을 위한 메서드를 제공합니다.

## <a name="syntax"></a>구문

*cast-expression*: *unary-expression*

**(**  *type-name*  **)**  *cast-expression*

형식 캐스팅이 만들어지면 컴파일러에서 *cast-expression* 을 *type-name* 형식으로 처리합니다. 모든 스칼라 형식의 개체로 또는 다른 모든 스칼라 형식에서 변환하는 데 캐스트를 사용할 수 있습니다. [할당 변환](../c-language/assignment-conversions.md)에 나와 있는 대로 명시적 형식 캐스팅은 암시적 변환 결과를 확인하는 동일한 규칙으로 제한됩니다. 캐스팅에 대한 추가 제한은 특정 형식의 실제 크기 또는 표현에서 발생할 수 있습니다. 정수 계열 형식의 실제 크기에 대한 자세한 내용은 [기본 형식 스토리지](../c-language/storage-of-basic-types.md)를 참조하세요. 형식 캐스팅에 대한 자세한 내용은 [형식 캐스팅 변환](../c-language/type-cast-conversions.md)을 참조하세요.

## <a name="see-also"></a>참조

[캐스트 연산자: ()](../cpp/cast-operator-parens.md)
