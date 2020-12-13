---
description: '자세한 정보: 특성 가져오기 raw_property_prefixes'
title: raw_property_prefixes 가져오기 특성
ms.date: 08/29/2019
f1_keywords:
- raw_property_prefixes
helpviewer_keywords:
- raw_property_prefixes attribute
ms.assetid: 03a0f48c-c460-4175-a762-9f7f8d84b12f
ms.openlocfilehash: 7289f9aeba249249ecf78ffb3ad3b32669ac9fe3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97142716"
---
# <a name="raw_property_prefixes-import-attribute"></a>raw_property_prefixes 가져오기 특성

**C++ 전용**

세 가지 속성 메서드의 대체 접두사를 지정합니다.

## <a name="syntax"></a>Syntax

> **#import** *형식 라이브러리* **raw_property_prefixes (** "*getprefix*" **,** "*putprefix*" **,** "*putrefprefix*" **)**

### <a name="parameters"></a>매개 변수

*GetPrefix*\
메서드에 사용할 접두사 `propget` 입니다.

*PutPrefix*\
메서드에 사용할 접두사 `propput` 입니다.

*PutRefPrefix*\
메서드에 사용할 접두사 `propputref` 입니다.

## <a name="remarks"></a>설명

기본적으로 하위 수준, 및 `propget` `propput` `propputref` 메서드는 `get_` 각각, 및 접두사를 사용 하 여 이라는 멤버 함수에 의해 노출 됩니다 `put_` `putref_` . 이 접두사는 MIDL로 생성한 헤더 파일에 사용되는 이름과 호환됩니다.

**C++ 전용 종료**

## <a name="see-also"></a>참고 항목

[#import 특성](../preprocessor/hash-import-attributes-cpp.md)\
[#import 지시문](../preprocessor/hash-import-directive-cpp.md)
