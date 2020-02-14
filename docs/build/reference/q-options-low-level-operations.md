---
title: /Q 옵션(하위 수준 작업)
ms.date: 01/08/2020
f1_keywords:
- /q
helpviewer_keywords:
- Q compiler option [C++]
- -Q compiler option [C++]
- /Q compiler option [C++]
ms.openlocfilehash: 722a63a43e5e08fe80b26f908c7ae92df2fdb29c
ms.sourcegitcommit: 0f4ee9056d65043fa5a715f0ad1031c0ed30e2b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/05/2020
ms.locfileid: "77034521"
---
# <a name="q-options-low-level-operations"></a>/Q 옵션(하위 수준 작업)

**/Q** 컴파일러 옵션을 사용 하 여 다음과 같은 하위 수준 컴파일러 작업을 수행할 수 있습니다.

- [/Qfast_transcendentals (Force Fast 초월수 강제 적용)](qfast-transcendentals-force-fast-transcendentals.md): fast 초월수 강제 적용을 생성 합니다.

- [/Qifist (_Ftol 표시 안 함)](qifist-suppress-ftol.md): 부동 소수점 형식에서 정수 형식으로 변환 해야 하는 경우 `_ftol`를 표시 하지 않습니다 (x 86에만 해당).

- [/Qimprecise_fwaits (Try 블록 내의 fwait 제거)](qimprecise-fwaits-remove-fwaits-inside-try-blocks.md): `try` 블록 내의 `fwait` 명령을 제거 합니다.

- [/QIntel-jcc-erratum](qintel-jcc-erratum.md): Intel 점프 조건부 코드 (jcc) erratum 마이크로코드 업데이트로 인 한 성능 영향을 완화 합니다.

- [/Qpar (자동 평행 화 도우미)](qpar-auto-parallelizer.md): [#pragma loop ()](../../preprocessor/loop.md) 지시문으로 표시 된 루프의 자동 병렬화를 사용 하도록 설정 합니다.

- [/Qpar-report (자동 평행 화 도우미 보고 수준)](qpar-report-auto-parallelizer-reporting-level.md): 자동 병렬화에 대 한 보고 수준을 활성화 합니다.

- [/Qsafe_fp_loads](qsafe-fp-loads.md): 부동 소수점 레지스터 로드 및 메모리와 MMX 레지스터 간 이동에 대 한 최적화를 표시 하지 않습니다.

- [/Qspectre](qspectre.md): 특정 스펙터 보안 취약성을 완화 하기 위한 지침을 생성 합니다.

- [/Qspectre-load](qspectre-load.md): 로드를 기반으로 스펙터 보안 취약점을 완화 하는 명령을 생성 합니다.

- [/Qspectre-load-cf](qspectre-load-cf.md): 로드 되는 제어 흐름 지침에 따라 스펙터 보안 취약점을 완화 하는 명령을 생성 합니다.

- [/Qvec-report (자동 벡터화 계층 보고 수준)](qvec-report-auto-vectorizer-reporting-level.md): 자동 벡터화에 대 한 보고 수준을 사용 하도록 설정 합니다.

## <a name="see-also"></a>참고 항목

[MSVC 컴파일러 옵션](compiler-options.md)<br/>
[MSVC 컴파일러 명령줄 구문](compiler-command-line-syntax.md)
