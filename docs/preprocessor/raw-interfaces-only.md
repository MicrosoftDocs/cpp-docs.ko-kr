---
description: '자세한 정보: 특성 가져오기 raw_interfaces_only'
title: raw_interfaces_only 가져오기 특성
ms.date: 08/29/2019
f1_keywords:
- raw_interfaces_only
helpviewer_keywords:
- raw_interfaces_only attribute
ms.assetid: 87056c6d-3f34-4248-af58-f5775a35bfb7
ms.openlocfilehash: f043bef5cde0454ce9f08f45efb0417aa7fdbb2d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97142742"
---
# <a name="raw_interfaces_only-import-attribute"></a>raw_interfaces_only 가져오기 특성

**C++ 전용**

오류 처리 래퍼 함수와 이러한 래퍼 함수를 사용 하는 [속성](../cpp/property-cpp.md) 선언을 생성 하지 않습니다.

## <a name="syntax"></a>Syntax

> **#import** *형식 라이브러리* **raw_interfaces_only**

## <a name="remarks"></a>설명

또한 **raw_interfaces_only** 특성을 사용 하면 비 속성 함수의 이름을 지정할 때 사용 되는 기본 접두사를 제거할 수 있습니다. 일반적으로 접두사는 `raw_` 입니다. 이 특성을 지정 하는 경우 함수 이름은 형식 라이브러리에서 직접 가져옵니다.

이 특성을 사용하면 형식 라이브러리의 하위 내용만 노출할 수 있습니다.

**C++ 전용 종료**

## <a name="see-also"></a>참고 항목

[#import 특성](../preprocessor/hash-import-attributes-cpp.md)\
[#import 지시문](../preprocessor/hash-import-directive-cpp.md)
