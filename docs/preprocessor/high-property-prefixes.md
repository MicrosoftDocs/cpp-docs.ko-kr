---
description: '자세한 정보: 특성 가져오기 high_property_prefixes'
title: high_property_prefixes 가져오기 특성
ms.date: 08/29/2019
f1_keywords:
- high_property_prefixes
helpviewer_keywords:
- high_property_prefixes attribute
ms.assetid: 91c6cc2b-19b6-4aba-8831-d9e5cccb58b5
ms.openlocfilehash: af6835f5835c23dceadbb5152e36b0dabcbb8c98
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97167476"
---
# <a name="high_property_prefixes-import-attribute"></a>high_property_prefixes 가져오기 특성

**C++ 전용**

세 가지 속성 메서드의 대체 접두사를 지정합니다.

## <a name="syntax"></a>Syntax

> **#import** *형식 라이브러리* **high_property_prefixes (** "*getprefix*" **,** "*putprefix*" **,** "*putrefprefix*" **)**

### <a name="parameters"></a>매개 변수

*GetPrefix*\
메서드에 사용할 접두사 `propget` 입니다.

*PutPrefix*\
메서드에 사용할 접두사 `propput` 입니다.

*PutRefPrefix*\
메서드에 사용할 접두사 `propputref` 입니다.

## <a name="remarks"></a>설명

기본적으로 상위 수준 오류 처리 `propget` , `propput` 및 `propputref` 메서드는 각각 접두사, 및로 명명 된 멤버 함수에 의해 노출 됩니다 `Get` `Put` `PutRef` .

**C++ 전용 종료**

## <a name="see-also"></a>참고 항목

[#import 특성](../preprocessor/hash-import-attributes-cpp.md)\
[#import 지시문](../preprocessor/hash-import-directive-cpp.md)
