---
description: '자세히 알아보기: 형식 검사 (CRT)'
title: 형식 검사(CRT)
ms.date: 11/04/2016
f1_keywords:
- c.types
helpviewer_keywords:
- checking type
- variable argument functions
- type checking
ms.assetid: 1ba7590b-d1c0-4636-b6a0-e231395abdad
ms.openlocfilehash: cf27847bf2aeef278fb4699cea5a0cf74a961086
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97162355"
---
# <a name="type-checking-crt"></a>형식 검사(CRT)

컴파일러는 아래와 같이 다양한 수의 인수를 사용할 수 있는 함수에서 제한된 형식 검사를 수행합니다.

|함수 호출|형식이 검사된 인수|
|-------------------|-----------------------------|
|`_cprintf_s`, `_cscanf_s`, `printf_s`, `scanf_s`|첫 번째 인수(형식 문자열)|
|`fprintf_s`, `fscanf_s`, `sprintf_s`, `sscanf_s`|처음 두 개의 인수(파일 또는 버퍼 및 형식 문자열)|
|`_snprintf_s`|처음 세 개의 인수(파일 또는 버퍼, 개수 및 형식 문자열)|
|`_open`|처음 두 개의 인수(경로 및 `_open` 플래그)|
|`_sopen_s`|처음 세 개의 인수(경로, `_open` 플래그 및 공유 모드)|
|`_execl`, `_execle`, `_execlp`, `_execlpe`|처음 두 개의 인수(경로 첫 번째 인수 포인터)|
|`_spawnl`, `_spawnle`, `_spawnlp`, `_spawnlpe`|처음 세 개의 인수(모드 플래그, 경로 및 첫 번째 인수 포인터)|

컴파일러는 이러한 함수들의 와이드 형식 기반 함수들에서도 동일한 제한된 형식 검사를 수행합니다.

## <a name="see-also"></a>참고 항목

[CRT 라이브러리 기능](../c-runtime-library/crt-library-features.md)
