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
ms.openlocfilehash: 9afb4146f7bbd08b35df20972345285bb353e4d3
ms.sourcegitcommit: 90c300b74f6556cb5d989802d2e80d79542f55e7
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/09/2021
ms.locfileid: "102514228"
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

## <a name="see-also"></a>추가 정보

[CRT (c 런타임) 및 STL (c + + 표준 라이브러리) `.lib` 파일](../c-runtime-library/crt-library-features.md)
