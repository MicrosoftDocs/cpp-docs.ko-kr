---
description: '자세한 정보: 디버그 루틴'
title: 디버그 루틴
ms.date: 04/10/2018
f1_keywords:
- c.debug
helpviewer_keywords:
- debugging [CRT], using macros
- macros, debugging with
- debug routines
- debug macros
- debugging [CRT], runtime routines
ms.assetid: cb4d2664-10f3-42f7-a516-595558075471
ms.openlocfilehash: 60857549cbbb0871da208708e9acd812444b3274
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97321286"
---
# <a name="debug-routines"></a>디버그 루틴

C 런타임 라이브러리의 디버그 버전은 디버깅 프로그램을 더 쉽게 만들고 개발자가 다음 작업을 수행할 수 있도록 하는 많은 진단 서비스를 제공합니다.

- 디버그하는 동안 런타임 함수에 대해 직접 한 단계씩 코드 실행

- 어설션, 오류 및 예외 해결

- 힙 할당 추적 및 메모리 누수 방지

- 사용자에게 디버그 메시지 보고

## <a name="debug-versions-of-the-c-runtime-library-routines"></a>C 런타임 라이브러리 루틴의 디버그 버전

이러한 루틴을 사용하려면 [_DEBUG](../c-runtime-library/debug.md) 플래그를 정의해야 합니다. 이러한 루틴은 모두 애플리케이션의 정품 빌드에서 아무 작업도 하지 않습니다. 새 디버그 루틴을 사용하는 방법에 대한 자세한 내용은 [CRT 디버깅 기술](/visualstudio/debugger/crt-debugging-techniques)을 참조하세요.

| 루틴에서 반환된 값 | 기능 |
|--|--|
| [`_ASSERT`](../c-runtime-library/reference/assert-asserte-assert-expr-macros.md) | 식을 계산하고 결과가 FALSE인 경우 디버그 보고서를 생성합니다. |
| [`_ASSERTE`](../c-runtime-library/reference/assert-asserte-assert-expr-macros.md) | 와 비슷하지만 **`_ASSERT`** 생성 된 보고서에 실패 한 식을 포함 합니다. |
| [`_CrtCheckMemory`](../c-runtime-library/reference/crtcheckmemory.md) | 디버그 힙에서 할당된 메모리 블록의 무결성을 확인합니다. |
| [`_CrtDbgBreak`](../c-runtime-library/reference/crtdbgbreak.md) | 중단점을 설정합니다. |
| [`_CrtDbgReport`, `_CrtDbgReportW`](../c-runtime-library/reference/crtdbgreport-crtdbgreportw.md) | 사용자 메시지가 포함된 디버그 보고서를 생성하고 이 보고서를 가능한 대상 3개로 보냅니다. |
| [`_CrtDoForAllClientObjects`](../c-runtime-library/reference/crtdoforallclientobjects.md) | 힙의 모든 `_CLIENT_BLOCK` 형식에 대해 애플리케이션에서 제공하는 함수를 호출합니다. |
| [`_CrtDumpMemoryLeaks`](../c-runtime-library/reference/crtdumpmemoryleaks.md) | 상당한 메모리 누수가 발생한 경우 디버그 힙의 모든 메모리 블록을 덤프합니다. |
| [`_CrtIsMemoryBlock`](../c-runtime-library/reference/crtismemoryblock.md) | 지정된 메모리 블록이 로컬 힙 내에 있고 유효한 디버그 힙 블록 형식 식별자를 포함하는지 확인합니다. |
| [`_CrtIsValidHeapPointer`](../c-runtime-library/reference/crtisvalidheappointer.md) | 지정된 포인터가 로컬 힙에 있는지 확인합니다. |
| [`_CrtIsValidPointer`](../c-runtime-library/reference/crtisvalidpointer.md) | 지정된 메모리 범위가 읽기 및 쓰기에 적합한지 확인합니다. |
| [`_CrtMemCheckpoint`](../c-runtime-library/reference/crtmemcheckpoint.md) | 디버그 힙의 현재 상태를 가져오고 애플리케이션에서 제공한 `_CrtMemState` 구조에 저장합니다. |
| [`_CrtMemDifference`](../c-runtime-library/reference/crtmemdifference.md) | 두 개의 메모리 상태에 큰 차이가 있는지 비교하고 결과를 반환합니다. |
| [`_CrtMemDumpAllObjectsSince`](../c-runtime-library/reference/crtmemdumpallobjectssince.md) | 지정된 검사점이 사용된 이후 또는 프로그램 실행 시작부터 힙에 있는 개체에 대한 정보를 덤프합니다. |
| [`_CrtMemDumpStatistics`](../c-runtime-library/reference/crtmemdumpstatistics.md) | 지정된 메모리 상태에 대한 디버그 헤더 정보를 사용자가 읽을 수 있는 형식으로 덤프합니다. |
| [`_CrtReportBlockType`](../c-runtime-library/reference/crtreportblocktype.md) | 지정된 디버그 힙 블록 포인터와 연결된 블록 형식/하위 형식을 반환합니다. |
| [`_CrtSetAllocHook`](../c-runtime-library/reference/crtsetallochook.md) | 클라이언트 정의 할당 함수를 C 런타임 디버그 메모리 할당 프로세스에 후크하여 함수를 설치합니다. |
| [`_CrtSetBreakAlloc`](../c-runtime-library/reference/crtsetbreakalloc.md) | 지정된 개체 할당 순서 번호에 대한 중단점을 설정합니다. |
| [`_CrtSetDbgFlag`](../c-runtime-library/reference/crtsetdbgflag.md) | `_crtDbgFlag` 플래그의 상태를 검색 또는 수정하여 디버그 힙 관리자의 할당 동작을 제어합니다. |
| [`_CrtSetDumpClient`](../c-runtime-library/reference/crtsetdumpclient.md) | `_CLIENT_BLOCK` 형식 메모리 블록을 덤프하기 위해 디버그 덤프 함수가 호출될 때마다 호출되는 애플리케이션 정의 함수를 설치합니다. |
| [`_CrtSetReportFile`](../c-runtime-library/reference/crtsetreportfile.md) | `_CrtDbgReport`에서 특정 보고서의 대상으로 사용할 파일 또는 스트림을 확인합니다. |
| [`_CrtSetReportHook`](../c-runtime-library/reference/crtsetreporthook.md) | 클라이언트 정의 보고 함수를 C 런타임 디버그 보고 프로세스에 후크하여 해당 함수를 설치합니다. |
| [`_CrtSetReportHook2`, `_CrtSetReportHookW2`](../c-runtime-library/reference/crtsetreporthook2-crtsetreporthookw2.md) | 클라이언트 정의 보고 함수를 C 런타임 디버그 보고 프로세스에 후크하여 해당 함수를 설치하거나 제거합니다. |
| [`_CrtSetReportMode`](../c-runtime-library/reference/crtsetreportmode.md) | `_CrtDbgReport`에서 생성되는 특정 보고서 형식에 대한 일반 대상을 지정합니다. |
| [_RPT&#91;0,1,2,3,4&#93;](../c-runtime-library/reference/rpt-rptf-rptw-rptfw-macros.md) | `_CrtDbgReport`를 서식 문자열 및 가변적인 개수의 인수와 함께 호출하여 디버그 보고서를 생성하는 방식으로 애플리케이션의 진행 상황을 추적합니다. 소스 파일 및 줄 번호 정보를 제공합니다. |
| [_RPTF&#91;0,1,2,3,4&#93;](../c-runtime-library/reference/rpt-rptf-rptw-rptfw-macros.md) | `_RPTn` 매크로와 비슷하지만 보고서 요청이 시작된 소스 파일 이름과 줄 번호를 제공합니다. |
| [`_calloc_dbg`](../c-runtime-library/reference/calloc-dbg.md) | 디버깅 헤더에 대한 추가 공간이 있는 힙에서 지정된 개수의 메모리 블록을 할당하고 버퍼를 덮어씁니다. |
| [`_expand_dbg`](../c-runtime-library/reference/expand-dbg.md) | 블록을 확장하거나 축소하여 힙에서 지정된 메모리 블록의 크기를 조정합니다. |
| [`_free_dbg`](../c-runtime-library/reference/free-dbg.md) | 힙에서 메모리 블록을 해제합니다. |
| [`_fullpath_dbg`, `_wfullpath_dbg`](../c-runtime-library/reference/fullpath-dbg-wfullpath-dbg.md) | 메모리를 할당 하는 데를 사용 하 여 지정 된 상대 경로 이름의 절대 또는 전체 경로 이름을 만듭니다 [`_malloc_dbg`](../c-runtime-library/reference/malloc-dbg.md) . |
| [`_getcwd_dbg`, `_wgetcwd_dbg`](../c-runtime-library/reference/getcwd-dbg-wgetcwd-dbg.md) | 를 사용 하 여 메모리를 할당 하는 현재 작업 디렉터리를 가져옵니다 [`_malloc_dbg`](../c-runtime-library/reference/malloc-dbg.md) . |
| [`_malloc_dbg`](../c-runtime-library/reference/malloc-dbg.md) | 디버깅 헤더에 대한 추가 공간이 있는 힙에서 메모리 블록을 할당하고 버퍼를 덮어씁니다. |
| [`_msize_dbg`](../c-runtime-library/reference/msize-dbg.md) | 힙에서 메모리 블록의 크기를 계산합니다. |
| [`_realloc_dbg`](../c-runtime-library/reference/realloc-dbg.md) | 블록을 이동하거나 크기를 조정하여 힙에서 지정된 메모리 블록을 재할당합니다. |
| [`_strdup_dbg`, `_wcsdup_dbg`](../c-runtime-library/reference/strdup-dbg-wcsdup-dbg.md) | 를 사용 하 여 메모리를 할당 하는 문자열을 복제 [`_malloc_dbg`](../c-runtime-library/reference/malloc-dbg.md) 합니다. |
| [`_tempnam_dbg`, `_wtempnam_dbg`](../c-runtime-library/reference/tempnam-dbg-wtempnam-dbg.md) | 메모리를 할당 하는 데를 사용 하 여 임시 파일을 만드는 데 사용할 수 있는 이름을 생성 [`_malloc_dbg`](../c-runtime-library/reference/malloc-dbg.md) 합니다. |

## <a name="c-runtime-routines-that-are-not-available-in-source-code-form"></a>소스 코드 양식에서 사용할 수 없는 C 런타임 루틴

디버거를 사용하여 디버깅 프로세스 중에 대부분의 C 런타임 루틴에 대한 소스 코드를 단계별로 실행할 수 있습니다. 그러나 Microsoft에서는 일부 기술을 독점적인 것으로 간주하고 이러한 루틴의 하위 집합에 대한 소스 코드를 제공하지 않습니다. 이러한 루틴은 대부분 예외 처리 또는 부동 소수점 처리 그룹에 속하지만 몇몇 기타 루틴도 포함됩니다. 다음 표에 이러한 루틴이 나와 있습니다.

:::row:::
   :::column span="":::
      [`acos`](../c-runtime-library/reference/acos-acosf-acosl.md)\
      [`acosh`](../c-runtime-library/reference/acosh-acoshf-acoshl.md)\
      [`asin`](../c-runtime-library/reference/asin-asinf-asinl.md)\
      [`asinh`](../c-runtime-library/reference/asinh-asinhf-asinhl.md)\
      [`atan`, `atan2`](../c-runtime-library/reference/atan-atanf-atanl-atan2-atan2f-atan2l.md)\
      [`atanh`](../c-runtime-library/reference/atanh-atanhf-atanhl.md)\
      [`Bessel functions`](../c-runtime-library/reference/bessel-functions-j0-j1-jn-y0-y1-yn.md)\
      [`_cabs`](../c-runtime-library/reference/cabs.md)\
      [`ceil`](../c-runtime-library/reference/ceil-ceilf-ceill.md)\
      [`_chgsign`](../c-runtime-library/reference/chgsign-chgsignf-chgsignl.md)\
      [`_clear87`, `_clearfp`](../c-runtime-library/reference/clear87-clearfp.md)\
      [`_control87`, `_controlfp`](../c-runtime-library/reference/control87-controlfp-control87-2.md)
   :::column-end:::
   :::column span="":::
      [`copysign`](../c-runtime-library/reference/copysign-copysignf-copysignl-copysign-copysignf-copysignl.md)\
      [`cos`](../c-runtime-library/reference/cos-cosf-cosl.md)\
      [`cosh`](../c-runtime-library/reference/cosh-coshf-coshl.md)\
      [`Exp`](../c-runtime-library/reference/exp-expf.md)\
      [`fabs`](../c-runtime-library/reference/fabs-fabsf-fabsl.md)\
      [`_finite`](../c-runtime-library/reference/finite-finitef.md)\
      [`floor`](../c-runtime-library/reference/floor-floorf-floorl.md)\
      [`fmod`](../c-runtime-library/reference/fmod-fmodf.md)\
      [`_fpclass`](../c-runtime-library/reference/fpclass-fpclassf.md)\
      [`_fpieee_flt`](../c-runtime-library/reference/fpieee-flt.md)\
      [`_fpreset`](../c-runtime-library/reference/fpreset.md)\
      [`frexp`](../c-runtime-library/reference/frexp.md)
   :::column-end:::
   :::column span="":::
      [`_hypot`](../c-runtime-library/reference/hypot-hypotf-hypotl-hypot-hypotf-hypotl.md)\
      [`_isnan`](../c-runtime-library/reference/isnan-isnan-isnanf.md)\
      [`ldexp`](../c-runtime-library/reference/ldexp.md)\
      [`log`](../c-runtime-library/reference/log-logf-log10-log10f.md)\
      [`_logb`](../c-runtime-library/reference/logb-logbf-logbl-logb-logbf.md)\
      [`log10`](../c-runtime-library/reference/log-logf-log10-log10f.md)\
      [`longjmp`](../c-runtime-library/reference/longjmp.md)\
      [`_matherr`](../c-runtime-library/reference/matherr.md)\
      [`modf`](../c-runtime-library/reference/modf-modff-modfl.md)\
      [`_nextafter`](../c-runtime-library/reference/nextafter-functions.md)\
      [`pow`](../c-runtime-library/reference/pow-powf-powl.md)\
      [`printf_s`](../c-runtime-library/reference/printf-s-printf-s-l-wprintf-s-wprintf-s-l.md)
   :::column-end:::
   :::column span="":::
      [`printf`](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)\
      [`_scalb`](../c-runtime-library/reference/scalb.md)\
      [`scanf_s`](../c-runtime-library/reference/scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md)\
      [`scanf`](../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md)\
      [`setjmp`](../c-runtime-library/reference/setjmp.md)\
      [`sin`](../c-runtime-library/reference/sin-sinf-sinl.md)\
      [`sinh`](../c-runtime-library/reference/sinh-sinhf-sinhl.md)\
      [`sqrt`](../c-runtime-library/reference/sqrt-sqrtf-sqrtl.md)\
      [`_status87`, `_statusfp`](../c-runtime-library/reference/status87-statusfp-statusfp2.md)\
      [`tan`](../c-runtime-library/reference/tan-tanf-tanl.md)\
      [`tanh`](../c-runtime-library/reference/tanh-tanhf-tanhl.md)
   :::column-end:::
:::row-end:::

소스 코드는 대부분의 **printf** 및 **scanf** 루틴에 사용할 수 있지만 소스 코드가 제공되지 않는 다른 루틴에 대한 내부 호출을 수행합니다.

## <a name="routines-that-behave-differently-in-a-debug-build-of-an-application"></a>애플리케이션의 디버그 빌드에서 다르게 동작하는 루틴

애플리케이션의 디버그 빌드에서 호출될 경우 일부 C 런타임 함수 및 C++ 연산자는 다르게 동작합니다. 응용 프로그램의 디버그 빌드는 플래그를 정의 하거나 `_DEBUG` C 런타임 라이브러리의 디버그 버전으로 연결 하 여 수행할 수 있습니다. 동작 차이는 일반적으로 디버깅 프로세스를 지원 하기 위해 루틴이 제공 하는 추가 기능 또는 정보로 구성 됩니다. 다음 표에 이러한 루틴이 나와 있습니다.

:::row:::
   :::column span="":::
      C [`abort`](../c-runtime-library/reference/abort.md) 루틴
   :::column-end:::
   :::column span="":::
      C [`assert`](../c-runtime-library/reference/assert-macro-assert-wassert.md) 루틴
   :::column-end:::
   :::column span="":::
      C + + [`delete`](../cpp/delete-operator-cpp.md) 연산자
   :::column-end:::
   :::column span="":::
      C + + [`new`](../cpp/new-operator-cpp.md) 연산자
   :::column-end:::
:::row-end:::

## <a name="see-also"></a>참고 항목

[범주별 유버니설 C 런타임 루틴](../c-runtime-library/run-time-routines-by-category.md)<br/>
[런타임 오류 검사](../c-runtime-library/run-time-error-checking.md)<br/>
