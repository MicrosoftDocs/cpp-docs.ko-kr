---
description: '자세한 정보: 32 비트 Windows 시간/날짜 형식'
title: 32비트 Windows 시간-날짜 서식
ms.date: 11/04/2016
f1_keywords:
- vc.time
helpviewer_keywords:
- 32-bit Windows
ms.assetid: ef1589db-84d7-4b24-8799-7c7a22cfe2bf
ms.openlocfilehash: 3893a2abc5d00cfba7ec83209470e907f87d3e94
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97135787"
---
# <a name="32-bit-windows-timedate-formats"></a>32비트 Windows 시간/날짜 서식

파일 시간 및 날짜는 부호 없는 정수를 비트 필드로 사용하여 개별적으로 저장됩니다. 파일 시간 및 날짜는 다음과 같이 채워집니다.

### <a name="time"></a>시간

|비트 위치:|0   1   2   3   4|5   6   7   8   9   A|B   C   D   E   F|
|-------------------|-----------------------|---------------------------|-----------------------|
|길이:|5|6|5|
|콘텐츠:|시간|minutes|2초 증가|
|값 범위:|0-23|0-59|2초 간격으로 0-29|

### <a name="date"></a>날짜

|비트 위치:|0   1   2   3   4   5   6|7   8   9   A|B   C   D   E   F|
|-------------------|-------------------------------|-------------------|-----------------------|
|길이:|7|4|5|
|콘텐츠:|연도|month|일|
|값 범위:|0-119|1-12|1-31|
||(1980에 상대적)|||

## <a name="see-also"></a>참고 항목

[전역 상수](../c-runtime-library/global-constants.md)
