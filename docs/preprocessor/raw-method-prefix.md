---
description: '다음에 대 한 자세한 정보: raw_method_prefix'
title: raw_method_prefix
ms.date: 08/29/2019
f1_keywords:
- raw_method_prefix
helpviewer_keywords:
- raw_method_prefix attribute
ms.assetid: 71490313-af78-4bb2-b28a-eee67950d30b
ms.openlocfilehash: 9e05f70814e48a4460287e96905b543f7d76dde6
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97201991"
---
# <a name="raw_method_prefix"></a>raw_method_prefix

**C++ 전용**

이름 충돌을 방지하기 위해 다른 접두사를 지정합니다.

## <a name="syntax"></a>Syntax

> **#import** *형식 라이브러리* **raw_method_prefix (** "*prefix*" **)**

### <a name="parameters"></a>매개 변수

*접두사*\
사용할 접두사입니다.

## <a name="remarks"></a>설명

상위 수준 오류 처리 멤버 함수와의 이름 충돌을 방지 하기 위해 기본 접두사 **raw_** 를 사용 하 여 라는 멤버 함수에서 하위 수준 속성 및 메서드를 노출 합니다.

> [!NOTE]
> **Raw_method_prefix** 특성의 효과는 [raw_interfaces_only](raw-interfaces-only.md) 특성이 있는지 여부에 따라 변경 되지 않습니다. **Raw_method_prefix** 항상 `raw_interfaces_only` 접두사를 지정 하는 것 보다 우선 합니다. 동일한 문에서 두 특성을 모두 사용 하는 경우 `#import` **raw_method_prefix** 특성으로 지정 된 접두사가 사용 됩니다.

**C++ 전용 종료**

## <a name="see-also"></a>참고 항목

[#import 특성](../preprocessor/hash-import-attributes-cpp.md)\
[#import 지시문](../preprocessor/hash-import-directive-cpp.md)
