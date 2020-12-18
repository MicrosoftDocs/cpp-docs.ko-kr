---
description: '자세한 정보: 문자열 리터럴 스토리지'
title: 문자열 리터럴 스토리지
ms.date: 11/04/2016
helpviewer_keywords:
- string literals, storage
ms.assetid: ba5e4d2c-d456-44b3-a8ca-354af547ac50
ms.openlocfilehash: 5139d480af6b808b5b2e008500794d95d63a9980
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97205267"
---
# <a name="storage-of-string-literals"></a>문자열 리터럴 스토리지

리터럴 문자열의 문자는 인접한 메모리 위치에 순서대로 저장됩니다. 문자열 리터럴 내의 이스케이프 시퀀스(예: **\\\\** 또는 **\\"** )는 단일 문자로 계산됩니다. null 문자( **\0** 이스케이프 시퀀스로 표현됨)가 각 문자열 리터럴에 자동으로 추가되어 끝을 표시합니다. (이러한 7번째 [변환 단계](../preprocessor/phases-of-translation.md) 중에 발생합니다.) 컴파일러는 서로 다른 두 주소에 동일한 두 문자열을 저장할 수 없습니다. [/GF](../build/reference/gf-eliminate-duplicate-strings.md)는 컴파일러가 동일한 문자열의 단일 복사본을 실행 파일에 배치하도록 합니다.

## <a name="remarks"></a>설명

**Microsoft 전용**

문자열에는 정적 스토리지 기간이 있습니다. 스토리지 기간에 대한 자세한 내용은 [스토리지 클래스](../c-language/c-storage-classes.md)를 참조하세요.

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[C 문자열 리터럴](../c-language/c-string-literals.md)
