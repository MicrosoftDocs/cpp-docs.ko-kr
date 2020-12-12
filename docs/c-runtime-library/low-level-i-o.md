---
description: Low-Level i/o에 대해 자세히 알아보세요.
title: 하위 수준 I/O
ms.date: 11/04/2016
helpviewer_keywords:
- I/O [CRT], low-level
- I/O [CRT], functions
- low-level I/O routines
- file handles [C++]
- file handles [C++], I/O functions
ms.assetid: 53e11bdd-6720-481c-8b2b-3a3a569ed534
ms.openlocfilehash: 88e159e9f85cd4f893616d3aef935417f5abde52
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97164980"
---
# <a name="low-level-io"></a>하위 수준 I/O

이러한 함수는 스트림 I/O에서 제공하는 연산보다 낮은 수준의 연산에 대해 직접적으로 운영 체제를 호출합니다. 하위 수준 입/출력 호출은 데이터를 버퍼링하지 않고 서식을 지정하지도 않습니다.

하위 수준 루틴에서는 다음과 같은 미리 정의된 파일 설명자를 사용하여 프로그램을 시작할 때 열린 표준 스트림에 액세스할 수 있습니다.

|스트림|파일 설명자|
|------------|---------------------|
|**stdin**|0|
|**stdout**|1|
|**stderr**|2|

하위 수준 I/O 루틴은 오류가 발생할 때 [errno](../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) 전역 변수를 설정합니다. 파일 끝 표시기(**EOF**)와 같이 STDIO.H에 정의된 상수가 프로그램에 필요한 경우에만 하위 수준 함수를 사용할 때 STDIO.H를 포함해야 합니다.

## <a name="low-level-io-functions"></a>하위 수준 I/O 함수

|함수|기능|
|--------------|---------|
|[_close](../c-runtime-library/reference/close.md)|파일 닫기|
|[_commit](../c-runtime-library/reference/commit.md)|디스크에 파일 플러시|
|[_creat, _wcreat](../c-runtime-library/reference/creat-wcreat.md)|파일 만들기|
|[_dup](../c-runtime-library/reference/dup-dup2.md)|지정된 파일에 대해 다음으로 사용 가능한 파일 설명자 반환|
|[_dup2](../c-runtime-library/reference/dup-dup2.md)|지정 파일에 대해 두 번째 설명자 만들기|
|[_eof](../c-runtime-library/reference/eof.md)|파일 끝에 대한 테스트|
|[_lseek, _lseeki64](../c-runtime-library/reference/lseek-lseeki64.md)|지정된 위치로 파일 포인터 위치 재지정|
|[_open, _wopen](../c-runtime-library/reference/open-wopen.md)|파일 열기|
|[_read](../c-runtime-library/reference/read.md)|파일에서 데이터 읽기|
|[_sopen, _wsopen](../c-runtime-library/reference/sopen-wsopen.md), [_sopen_s, _wsopen_s](../c-runtime-library/reference/sopen-s-wsopen-s.md)|파일 공유를 위한 파일 열기|
|[_tell, _telli64](../c-runtime-library/reference/tell-telli64.md)|현재 파일 포인터 위치 가져오기|
|[_umask](../c-runtime-library/reference/umask.md), [_umask_s](../c-runtime-library/reference/umask-s.md)|파일 사용 권한 마스크 설정|
|[_write](../c-runtime-library/reference/write.md)|파일에 데이터 쓰기|

**_dup** 및 **_dup2** 는 일반적으로 미리 정의된 파일 설명자를 다른 파일에 연결하는 데 사용됩니다.

## <a name="see-also"></a>참고 항목

[입력 및 출력](../c-runtime-library/input-and-output.md)<br/>
[범주별 유버니설 C 런타임 루틴](../c-runtime-library/run-time-routines-by-category.md)<br/>
[시스템 호출](../c-runtime-library/system-calls.md)<br/>
