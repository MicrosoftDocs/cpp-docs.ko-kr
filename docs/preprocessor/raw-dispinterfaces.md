---
description: '자세한 정보: 특성 가져오기 raw_dispinterfaces'
title: raw_dispinterfaces 가져오기 특성
ms.date: 08/29/2019
f1_keywords:
- raw_dispinterfaces
helpviewer_keywords:
- raw_dispinterfaces attribute
ms.assetid: f762864d-29bf-445b-825a-ba7b29a95409
ms.openlocfilehash: 447f76bdee16d2719c02ad4a73883f8f176f2584
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97202017"
---
# <a name="raw_dispinterfaces-import-attribute"></a>raw_dispinterfaces 가져오기 특성

**C++ 전용**

는 대상 메서드에 대 한 하위 수준 래퍼 함수를 생성 하 고를 호출 하 `IDispatch::Invoke` 고 HRESULT 오류 코드를 반환 하는 속성에 대해 컴파일러에 지시 합니다.

## <a name="syntax"></a>Syntax

> **#import** *형식 라이브러리* **raw_dispinterfaces**

## <a name="remarks"></a>설명

이 특성이 지정 되지 않은 경우에는 오류 발생 시 c + + 예외를 throw 하는 상위 수준 래퍼로 생성 됩니다.

**C++ 전용 종료**

## <a name="see-also"></a>참고 항목

[#import 특성](../preprocessor/hash-import-attributes-cpp.md)\
[#import 지시문](../preprocessor/hash-import-directive-cpp.md)
