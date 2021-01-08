---
title: vcpkg 명령줄 참조
description: Windows, macOS 및 Linux에서 vcpkg의 명령줄 옵션을 사용하는 방법을 알아봅니다.
ms.date: 12/17/2020
ms.topic: reference
ms.technology: cpp-ide
ms.openlocfilehash: d60ebf983fea2eb41430f05b8c12e4a4a6fe370b
ms.sourcegitcommit: 2b2c3fa9244e31db35ea33554dea0efcab490f3c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/18/2020
ms.locfileid: "97684116"
---
# <a name="vcpkg-command-line-reference"></a>vcpkg 명령줄 참조

vcpkg에서 사용할 수 있는 명령에 대한 빠른 참조입니다.

## <a name="commands"></a>명령

| 명령 | 설명 |
|--|--|
| **`vcpkg search [pat]`** | 설치할 수 있는 패키지 검색 |
| **`vcpkg install <pkg>...`** | 패키지 설치 |
| **`vcpkg remove <pkg>...`** | 패키지 제거 |
| **`vcpkg remove --outdated`** | 만료된 패키지 모두 제거 |
| **`vcpkg list`** | 설치된 패키지 나열 |
| **`vcpkg update`** | 업데이트할 패키지 목록 표시 |
| **`vcpkg upgrade`** | 만료된 모든 패키지 다시 빌드 |
| **`vcpkg hash <file> [alg]`** | 특정 알고리즘에 따라 파일 해시, 기본 SHA512 |
| **`vcpkg integrate install`** | 설치된 패키지를 누구나 사용할 수 있도록 설정 처음 사용할 때 관리자 권한 필요 |
| **`vcpkg integrate remove`** | 사용자 수준 통합 제거 |
| **`vcpkg integrate project`** | 개별 VS 프로젝트 사용을 위한 참조 NuGet 패키지 생성 |
| **`vcpkg export <pkg>... [opt]...`** | 패키지 내보내기 |
| **`vcpkg edit <pkg>`** | 편집할 포트 열기(%EDITOR% 사용, 기본 '코드') |
| **`vcpkg create <pkg> <url> [archivename]`** | 새 패키지 만들기 |
| **`vcpkg cache`** | 컴파일된 캐시 패키지 나열 |
| **`vcpkg version`** | 버전 정보 표시 |
| **`vcpkg contact --survey`** | 사용자 의견을 보낼 연락처 정보를 표시합니다. |

## <a name="options"></a>옵션

| 옵션 | 설명 |
|--|--|
| **`--triplet <t>`** | 세 가지 대상 아키텍처를 지정합니다. (기본값: `%VCPKG_DEFAULT_TRIPLET%`, **`vcpkg help triplet`** 참조) |
| **`--vcpkg-root <path>`** | vcpkg 루트 디렉터리 지정(기본값: `%VCPKG_ROOT%`) |

## <a name="see-also"></a>추가 정보

[vcpkg: Windows, Linux 및 macOS용 C++ 패키지 관리자](./vcpkg.md)\
[GitHub의 vcpkg](https://github.com/Microsoft/vcpkg)\
[vcpkg 설치](install-vcpkg.md)\
[vcpkg 통합](integrate-vcpkg.md)\
[vcpkg를 사용하여 라이브러리 관리](manage-libraries-with-vcpkg.md)\
[빠른 시작](https://github.com/microsoft/vcpkg/blob/master/docs/index.md)\
[자주 묻는 질문](https://github.com/microsoft/vcpkg/blob/master/docs/about/faq.md)
