---
description: '자세한 정보: 특성 가져오기 raw_native_types'
title: raw_native_types 가져오기 특성
ms.date: 08/29/2019
f1_keywords:
- raw_native_types
helpviewer_keywords:
- raw_native_types attribute
ms.assetid: 9f38daa8-8dc0-46a5-aff9-f1ff9c1e6f48
ms.openlocfilehash: 64eaadcbb3d9f07d47dd4a33bc16a222cae50f38
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97240535"
---
# <a name="raw_native_types-import-attribute"></a>raw_native_types 가져오기 특성

**C++ 전용**

상위 수준 래퍼 함수에서 COM 지원 클래스를 사용 하지 않도록 설정 하 고 대신 하위 수준 데이터 형식을 사용 하도록 합니다.

## <a name="syntax"></a>Syntax

> **#import** *형식 라이브러리* **raw_native_types**

## <a name="remarks"></a>설명

기본적으로 상위 수준 오류 처리 메서드는 [](../cpp/bstr-t-class.md) 및 [](../cpp/variant-t-class.md) `BSTR` `VARIANT` 데이터 형식 및 원시 com 인터페이스 포인터 대신 COM 지원 클래스 _bstr_t 및 _variant_t를 사용 합니다. 이 클래스는 이러한 데이터 형식의 메모리 스토리지 할당 및 할당 해제에 대한 정보를 캡슐화합니다.

**C++ 전용 종료**

## <a name="see-also"></a>참고 항목

[#import 특성](../preprocessor/hash-import-attributes-cpp.md)\
[#import 지시문](../preprocessor/hash-import-directive-cpp.md)
