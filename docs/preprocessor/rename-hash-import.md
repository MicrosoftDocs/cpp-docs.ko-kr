---
description: '자세한 정보: 가져오기 특성 이름 바꾸기'
title: 가져오기 특성 이름 바꾸기
ms.date: 08/29/2019
helpviewer_keywords:
- rename attribute
ms.assetid: 5c5c6153-1087-4b7b-87fb-fc59b90b9975
ms.openlocfilehash: 3003300887dadbab5cf05396ff3fa38b6dd29026
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97176602"
---
# <a name="rename-import-attribute"></a>가져오기 특성 이름 바꾸기

**C++ 전용**

이름 충돌 문제 해결 작업

## <a name="syntax"></a>Syntax

> **#import** *형식 라이브러리* **이름 바꾸기 (** "*OldName*" **,** "*NewName*" **)**

### <a name="parameters"></a>매개 변수

*OldName*\
형식 라이브러리에 있는 이전 이름입니다.

*이름*\
이전 이름 대신 사용할 이름입니다.

## <a name="remarks"></a>설명

**Rename** 특성을 지정 하면 컴파일러가 *OldName* 의 모든 항목을 결과 헤더 파일의 사용자 제공 *NewName* *으로 바꿉니다* .

이름 **바꾸기** 특성은 형식 라이브러리의 이름이 시스템 헤더 파일의 매크로 정의와 일치 하는 경우에 사용할 수 있습니다. 이러한 상황이 해결 되지 않으면 컴파일러는 컴파일러 [오류 C2059](../error-messages/compiler-errors-1/compiler-error-c2059.md) 및 [컴파일러 오류 C2061](../error-messages/compiler-errors-1/compiler-error-c2061.md)같은 다양 한 구문 오류를 발행할 수 있습니다.

> [!NOTE]
> 결과 헤더 파일에 사용된 이름이 아니라 형식 라이브러리에 사용된 이름이 바뀝니다.

예를 들어, 이름이 `MyParent`인 속성이 형식 라이브러리에 있고 `GetMyParent` 매크로가 헤더 파일에 정의되어 `#import` 앞에 사용된다고 가정해 보겠습니다. `GetMyParent`가 오류 처리 속성에 대 한 래퍼 함수의 기본 이름이 기 때문에 `get` 이름 충돌이 발생 합니다. 이 문제를 해결하려면 `#import` 문에 다음 특성을 사용합니다.

```cpp
#import MyTypeLib.tlb rename("MyParent","MyParentX")
```

위의 특성은 형식 라이브러리에서 `MyParent`를 다른 이름으로 바꿉니다. `GetMyParent` 래퍼 이름을 바꾸려고 하면 오류가 발생합니다.

```cpp
#import MyTypeLib.tlb rename("GetMyParent","GetMyParentX")
```

그 이유는 이름이 `GetMyParent` 결과 형식 라이브러리 헤더 파일 에서만 발생 하기 때문입니다.

**C++ 전용 종료**

## <a name="see-also"></a>참고 항목

[#import 특성](../preprocessor/hash-import-attributes-cpp.md)\
[#import 지시문](../preprocessor/hash-import-directive-cpp.md)
