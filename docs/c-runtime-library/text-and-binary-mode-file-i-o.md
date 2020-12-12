---
description: '자세한 정보: 텍스트 및 이진 모드 파일 i/o'
title: 텍스트 및 이진 모드 파일 I/O
ms.date: 04/11/2018
helpviewer_keywords:
- files [C++], open functions
- I/O [CRT], text files
- functions [CRT], file access
- binary access, binary mode file I/O
- translation, modes
- I/O [CRT], binary
- text files, I/O
- I/O [CRT], translation modes
- translation modes (file I/O)
- binary access
ms.assetid: 3196e321-8b87-4609-b302-cd6f3c516051
ms.openlocfilehash: de4e7e7ea1792a23aac3507ec191f3433112b8dc
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97326897"
---
# <a name="text-and-binary-mode-file-io"></a>텍스트 및 이진 모드 파일 I/O

파일 i/o 작업은 파일이 열린 모드에 따라 두 변환 모드 ( *텍스트* 또는 *이진*) 중 하나에서 수행 됩니다. 데이터 파일은 일반적으로 텍스트 모드에서 처리됩니다. 파일 변환 모드를 제어하려면 다음과 같은 작업을 수행합니다.

- 현재 기본 설정을 유지하고 선택된 파일을 열 때만 대체 모드를 지정합니다.

- [_set_fmode](../c-runtime-library/reference/set-fmode.md) 함수를 사용하여 새로 열린 파일에 대한 기본 모드를 변경합니다. [_get_fmode](../c-runtime-library/reference/get-fmode.md)를 사용하여 현재 기본 모드를 찾습니다. 초기 기본 설정은 텍스트 모드(**_O_TEXT**)입니다.

- 프로그램에서 [_fmode](../c-runtime-library/fmode.md) 전역 변수를 설정하여 직접적으로 기본 변환 모드를 변경합니다. **_set_fmode** 함수는 이 변수의 값을 설정하지만 직접 설정할 수도 있습니다.

파일 열기 함수(예: [_open](../c-runtime-library/reference/open-wopen.md), [fopen](../c-runtime-library/reference/fopen-wfopen.md), [fopen_s](../c-runtime-library/reference/fopen-s-wfopen-s.md), [freopen](../c-runtime-library/reference/freopen-wfreopen.md), [freopen_s](../c-runtime-library/reference/freopen-s-wfreopen-s.md), [_fsopen](../c-runtime-library/reference/fsopen-wfsopen.md) 또는 [_sopen_s](../c-runtime-library/reference/sopen-s-wsopen-s.md))를 호출하는 경우 [_set_fmode](../c-runtime-library/reference/set-fmode.md) 함수에 적절한 인수를 지정하여 **_fmode** 의 현재 기본 설정을 재정의할 수 있습니다. **stdin**, **stdout** 및 **stderr** 스트림은 기본적으로 항상 텍스트 모드로 열립니다. 또한 이러한 파일을 열 때 이 기본값을 재정의할 수도 있습니다. [_setmode](../c-runtime-library/reference/setmode.md)를 사용하면 파일이 열린 후 파일 설명자를 사용하여 변환 모드를 변경할 수 있습니다.

## <a name="see-also"></a>참고 항목

[입력 및 출력](../c-runtime-library/input-and-output.md)<br/>
[범주별 유버니설 C 런타임 루틴](../c-runtime-library/run-time-routines-by-category.md)<br/>
