---
description: '자세한 정보: 특성 가져오기 implementation_only'
title: implementation_only 가져오기 특성
ms.date: 08/29/2019
f1_keywords:
- implementation_only
helpviewer_keywords:
- implementation_only attribute
ms.assetid: d8cabc86-4425-45a0-9587-d57536980088
ms.openlocfilehash: 8afeb9981c5931596fc500419755521a41a3d7c7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97236544"
---
# <a name="implementation_only-import-attribute"></a>implementation_only 가져오기 특성

**C++ 전용**

`.tlh`기본 형식 라이브러리 헤더 파일의 생성을 억제 합니다.

## <a name="syntax"></a>Syntax

> **#import** *형식 라이브러리* **implementation_only**

## <a name="remarks"></a>설명

이 파일에는 형식 라이브러리 내용을 노출하는 데 사용되는 모든 선언이 포함되어 있습니다. `.tli`래퍼 멤버 함수의 구현이 포함 된 헤더 파일이 생성 되 고 컴파일에 포함 됩니다.

이 특성을 지정 하면 헤더의 내용이 `.tli` 헤더에서 일반적으로 사용 되는 네임 스페이스와 동일한 네임 스페이스에 `.tlh` 있습니다. 또한 멤버 함수가 인라인으로 선언되지 않습니다.

**Implementation_only** 특성은 미리 컴파일된 헤더 (PCH) 파일의 구현을 유지 하는 방법으로 [no_implementation](../preprocessor/no-implementation.md) 특성과 함께 사용 하기 위한 것입니다. `#import` 특성이 포함된 `no_implementation` 문은 PCH를 만드는 데 사용되는 소스 영역에 배치됩니다. 생성된 PCH는 많은 소스 파일에서 사용됩니다. `#import`그러면 **implementation_only** 특성이 있는 문이 PCH 영역 외부에서 사용 됩니다. 이 문은 소스 파일 중 하나에서 한 번만 사용 해야 합니다. 각 소스 파일에 대 한 추가 재컴파일을 하지 않고 필요한 모든 래퍼 멤버 함수를 생성 합니다.

> [!NOTE]
> 한 문의 **implementation_only** 특성은 `#import` 특성을 `#import` 사용 하 여 동일한 형식 라이브러리의 다른 문과 함께 사용 해야 합니다 `no_implementation` . 그렇지 않으면 컴파일러 오류가 생성 됩니다. 이는 특성을 사용 하 여 문에서 생성 된 래퍼 클래스 정의가 `#import` `no_implementation` **implementation_only** 특성에 의해 생성 된 구현을 컴파일하는 데 필요 하기 때문입니다.

**C++ 전용 종료**

## <a name="see-also"></a>참고 항목

[#import 특성](../preprocessor/hash-import-attributes-cpp.md)\
[#import 지시문](../preprocessor/hash-import-directive-cpp.md)
