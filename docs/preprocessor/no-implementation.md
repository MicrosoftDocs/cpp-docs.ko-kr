---
description: '자세한 정보: 특성 가져오기 no_implementation'
title: no_implementation 가져오기 특성
ms.date: 08/29/2019
f1_keywords:
- no_implementation
helpviewer_keywords:
- no_implementation attribute
ms.assetid: bdc67785-e131-409c-87bc-f4d2f4abb07b
ms.openlocfilehash: 0cfd51b344847d2e5658fd4e4ec1a9f30db51fe6
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97333327"
---
# <a name="no_implementation-import-attribute"></a>no_implementation 가져오기 특성

**C++ 전용**

`.tli`래퍼 멤버 함수의 구현을 포함 하는 헤더 생성을 억제 합니다.

## <a name="syntax"></a>Syntax

> **#import** *형식 라이브러리* **no_implementation**

## <a name="remarks"></a>설명

이 특성을 지정 하면 `.tlh` `#include` 헤더 파일을 포함 하는 문을 사용 하지 않고 헤더에 형식 라이브러리 항목을 표시할 선언이 생성 됩니다 `.tli` .

이 특성은 [implementation_only](../preprocessor/implementation-only.md)와 함께 사용 됩니다.

**C++ 전용 종료**

## <a name="see-also"></a>참고 항목

[#import 특성](../preprocessor/hash-import-attributes-cpp.md)\
[#import 지시문](../preprocessor/hash-import-directive-cpp.md)
