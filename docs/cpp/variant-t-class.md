---
description: _Variant_t 클래스에 대해 자세히 알아보세요.
title: _variant_t 클래스
ms.date: 11/04/2016
f1_keywords:
- _variant_t
helpviewer_keywords:
- _variant_t class [C++], operators
- _variant_t class
- _variant_t class [C++], member functions
- VARIANT object
- VARIANT object [C++], COM encapsulation
ms.assetid: 6a3cbd4e-0ae8-425e-b4cf-ca0df894c93f
ms.openlocfilehash: e720d78e6f7fd22fc369d4b39804260892e235c1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97116615"
---
# <a name="_variant_t-class"></a>_variant_t 클래스

**Microsoft 전용**

**_Variant_t** 개체는 `VARIANT` 데이터 형식을 캡슐화 합니다. 클래스는 리소스 할당 및 할당 취소를 관리 하 고 적절 하 게 및에 대 한 함수 호출을 수행 `VariantInit` `VariantClear` 합니다.

### <a name="construction"></a>건설

| Name | 설명 |
|--|--|
| [_variant_t](../cpp/variant-t-variant-t.md) | **_Variant_t** 개체를 생성 합니다. |

### <a name="operations"></a>작업

| Name | 설명 |
|--|--|
| [연결](../cpp/variant-t-attach.md) | 개체를 `VARIANT` **_variant_t** 개체에 연결 합니다. |
| [지우기](../cpp/variant-t-clear.md) | 캡슐화 된 개체를 지웁니다 `VARIANT` . |
| [ChangeType](../cpp/variant-t-changetype.md) | **_Variant_t** 개체의 형식을 지정 된로 변경 합니다 `VARTYPE` . |
| [분리](../cpp/variant-t-detach.md) | `VARIANT`이 **_variant_t** 개체에서 캡슐화 된 개체를 분리 합니다. |
| [SetString](../cpp/variant-t-setstring.md) | 이 **_variant_t** 개체에 문자열을 할당 합니다. |

### <a name="operators"></a>연산자

| Name | 설명 |
|--|--|
| [연산자 =](../cpp/variant-t-operator-equal.md) | 기존 **_variant_t** 개체에 새 값을 할당 합니다. |
| [operator = =,! =](../cpp/variant-t-relational-operators.md) | 두 **_variant_t** 개체의 같음 또는 같지 않은지 비교 합니다. |
| [추출기](../cpp/variant-t-extractors.md) | 캡슐화 된 개체에서 데이터를 추출 `VARIANT` 합니다. |

**Microsoft 전용 종료**

## <a name="requirements"></a>요구 사항

**헤더:**\<comutil.h>

**Lib:** comsuppw 또는 comsuppw .lib (자세한 내용은 [/zc: Wchar_t (wchar_t 네이티브 형식)](../build/reference/zc-wchar-t-wchar-t-is-native-type.md) 참조)

## <a name="see-also"></a>참고 항목

[컴파일러 COM 지원 클래스](../cpp/compiler-com-support-classes.md)
