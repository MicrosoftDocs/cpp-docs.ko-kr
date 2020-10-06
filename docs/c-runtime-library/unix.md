---
title: UNIX
description: 프로그램을 Unix로 이식 하는 방법에 대 한 지침입니다.
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- unix
helpviewer_keywords:
- UNIX
- POSIX compatibility
- POSIX file names
- UNIX, compatibility
ms.assetid: 40792414-7a5b-415d-bfa8-2bfb1ebb3731
ms.openlocfilehash: 3975db2407943b329fa7eded0d72d63524428210
ms.sourcegitcommit: 30792632548d1c71894f9fecbe2f554294b86020
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/06/2020
ms.locfileid: "91765217"
---
# <a name="unix"></a>UNIX

프로그램을 UNIX로 이식하려면 다음 지침을 따르십시오.

- SYS 하위 디렉터리에서 헤더 파일을 제거 하지 마십시오. 프로그램을 UNIX로 전송할 계획이 없는 경우에만 SYS 헤더 파일을 다른 위치에 둘 수 있습니다.

- 경로 및 파일 이름을 나타내는 문자열을 인수로 사용하는 루틴에서 UNIX와 호환되는 경로 구분 기호를 사용합니다. UNIX에서는 이러한 용도로 슬래시 (/)만 지원 하지만 Win32 운영 체제에서는 백슬래시 ( \\ )와 슬래시 (/)를 모두 지원 합니다. 이 설명서에서는 문에서 UNIX와 호환 되는 슬래시를 경로 구분 기호로 사용 `#include` 합니다. 그러나 Windows 운영 체제 명령 셸 CMD.EXE은 명령 프롬프트에 입력 한 명령에서 슬래시를 지원 하지 않습니다.)

- UNIX에서 제대로 작동 하는 경로 및 파일 이름을 사용 합니다 .이는 대/소문자를 구분 합니다. Win32 운영 체제의 FAT (파일 할당 테이블) 파일 시스템은 대/소문자를 구분 하지 않습니다. NTFS 파일 시스템은 디렉터리 목록에 대 한 대/소문자를 유지 하지만 파일 검색 및 기타 시스템 작업에서 대/소문자를 무시 합니다.

> [!NOTE]
> 이 버전의 Visual C++에서는 UNIX 호환성 정보가 함수 설명에서 제외되었습니다.

## <a name="see-also"></a>참조

[호환성](../c-runtime-library/compatibility.md)
