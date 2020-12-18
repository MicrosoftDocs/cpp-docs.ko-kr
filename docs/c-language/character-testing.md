---
description: '자세한 정보: 문자 테스트'
title: 문자 테스트
ms.date: 11/04/2016
ms.assetid: 376ba061-bae3-427e-9569-33fa5949a199
ms.openlocfilehash: b7d73bce671787622814e11d8f3add7a1092572a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97190538"
---
# <a name="character-testing"></a>문자 테스트

**ANSI 4.3.1**`isalnum`, `isalpha`, `iscntrl`, `islower`, `isprint` 및 `isupper` 함수에서 테스트한 문자의 집합

다음 목록에서는 Microsoft C 컴파일러에 의해 구현되는 이러한 함수에 대해 설명합니다.

|기능|다음에 대해 테스트|
|--------------|---------------|
|`isalnum`|문자 0 - 9, A-Z, a-z ASCII 48-57, 65-90, 97-122|
|`isalpha`|문자 A-Z, a-z ASCII 65-90, 97-122|
|`iscntrl`|ASCII 0 -31, 127|
|`islower`|문자 a-z ASCII 97-122|
|`isprint`|문자 A-Z, a-z, 0 - 9, 문장 부호, 공백 ASCII 32-126|
|`isupper`|문자 A-Z ASCII 65-90|

## <a name="see-also"></a>참조

[라이브러리 함수](../c-language/library-functions.md)
