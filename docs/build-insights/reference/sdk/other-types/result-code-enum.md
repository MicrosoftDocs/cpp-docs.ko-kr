---
title: RESULT_CODE 열거형
description: C++ Build Insights SDK RESULT_CODE 열거형 참조입니다.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- RESULT_CODE
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 3d9d18d535d15d04a2e449bdbbf693364276a518
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92922416"
---
# <a name="result_code-enum"></a>RESULT_CODE 열거형

::: moniker range="<=msvc-140"

C++ Build Insights SDK는 Visual Studio 2017 이상 버전과 호환됩니다. 이러한 버전에 대한 설명서를 보려면 이 문서에 대한 Visual Studio **버전** 선택기 컨트롤을 Visual Studio 2017 또는 Visual Studio 2019로 설정하세요. 이 페이지의 목차 맨 위에 있습니다.

::: moniker-end
::: moniker range=">=msvc-150"

`RESULT_CODE` 열거형은 성공 및 실패 조건을 설명합니다.

## <a name="members"></a>멤버

| Name | 값 | Description |
|--|--|--|
| `RESULT_CODE_SUCCESS` | 0 (0x00000000) | 작업이 완료되었습니다. |
| `RESULT_CODE_FAILURE_ANALYSIS_ERROR` | 1 (0x00000001) | [ANALYSIS_DESCRIPTOR](analysis-descriptor-struct.md) 또는 [RELOG_DESCRIPTOR](relog-descriptor-struct.md)에서 `CALLBACK_CODE_ANALYSIS_FAILURE` 값을 반환한 콜백 함수 중 하나입니다. 이 값은 [CALLBACK_CODE](callback-code-enum.md) 열거형의 멤버입니다. |
| `RESULT_CODE_FAILURE_CANCELLED` | 2 (0x00000002) | [ANALYSIS_DESCRIPTOR](analysis-descriptor-struct.md) 또는 [RELOG_DESCRIPTOR](relog-descriptor-struct.md)에서 `CALLBACK_CODE_ANALYSIS_CANCEL` 값을 반환한 콜백 함수 중 하나입니다. 이 값은 [CALLBACK_CODE](callback-code-enum.md) 열거형의 멤버입니다. |
| `RESULT_CODE_FAILURE_INVALID_INPUT_LOG_FILE` | 3 (0x00000003) | 지정된 입력 ETW(Windows용 이벤트 추적) 추적이 올바르지 않습니다. |
| `RESULT_CODE_FAILURE_INVALID_OUTPUT_LOG_FILE` | 4 (0x00000004) | 지정된 출력 ETW 추적이 올바르지 않습니다. |
| `RESULT_CODE_FAILURE_MISSING_ANALYSIS_CALLBACK` | 5 (0x00000005) | [ANALYSIS_CALLBACKS](analysis-callbacks-struct.md) 구조체가 올바르게 초기화되지 않았습니다. |
| `RESULT_CODE_FAILURE_MISSING_RELOG_CALLBACK` | 6 (0x00000006) | [RELOG_CALLBACKS](relog-callbacks-struct.md) 구조체가 올바르게 초기화되지 않았습니다. |
| `RESULT_CODE_FAILURE_OPEN_INPUT_TRACE` | 7 (0x00000007) | 입력 ETW 추적을 열지 못했습니다. |
| `RESULT_CODE_FAILURE_PROCESS_TRACE` | 8 (0x00000008) | 입력 ETW 추적을 처리하는 도중 오류가 발생했습니다. |
| `RESULT_CODE_FAILURE_START_RELOGGER` | 9 (0x00000009) | 다시 로깅 세션을 시작하는 도중 오류가 발생했습니다. |
| `RESULT_CODE_FAILURE_DROPPED_EVENTS` | 10 (0x0000000A) | 입력 ETW 추적에 중요 이벤트가 누락되었습니다. |
| `RESULT_CODE_FAILURE_UNSUPPORTED_OS` | 11 (0x0000000B) | 지원되지 않는 Windows 버전에서 C++ Build Insights를 사용하고 있습니다. |
| `RESULT_CODE_FAILURE_INVALID_TRACING_SESSION_NAME` | 12 (0x0000000C) | 제공된 서버 이름이 올바르지 않습니다. |
| `RESULT_CODE_FAILURE_INSUFFICIENT_PRIVILEGES` | 13 (0x0000000D) | 이 작업은 관리자 권한이 필요합니다. |
| `RESULT_CODE_FAILURE_GENERATE_GUID` | 14 (0x0000000E) | GUID를 생성하는 도중 오류가 발생했습니다. |
| `RESULT_CODE_FAILURE_OBTAINING_TEMP_DIRECTORY` | 15 (0x0000000F) | 임시 디렉터리 경로를 확인하는 도중 오류가 발생했습니다. |
| `RESULT_CODE_FAILURE_CREATE_TEMPORARY_DIRECTORY` | 16 (0x00000010) | 추적 세션을 시작할 임시 디렉터리를 만드는 도중 오류가 발생했습니다. |
| `RESULT_CODE_FAILURE_START_SYSTEM_TRACE` | 17 (0x00000011) | 시스템 추적을 시작하는 도중 오류가 발생했습니다. |
| `RESULT_CODE_FAILURE_START_MSVC_TRACE` | 18 (0x00000012) | MSVC 추적을 시작하는 도중 오류가 발생했습니다. |
| `RESULT_CODE_FAILURE_STOP_MSVC_TRACE` | 19 (0x00000013) | MSVC 추적을 중지하는 도중 오류가 발생했습니다. |
| `RESULT_CODE_FAILURE_STOP_SYSTEM_TRACE` | 20 (0x00000014) | 시스템 추적을 시작하는 도중 오류가 발생했습니다. |
| `RESULT_CODE_FAILURE_SESSION_DIRECTORY_RESOLUTION` | 21 (0x00000015) | 추적이 중지되었지만 추적 세션의 임시 디렉터리를 찾을 수 없습니다. |
| `RESULT_CODE_FAILURE_MSVC_TRACE_FILE_NOT_FOUND` | 22 (0x00000016) | 중지하는 MSVC 추적에 대한 추적 파일을 찾을 수 없습니다. |
| `RESULT_CODE_FAILURE_MERGE_TRACES` | 23 (0x00000017) | Kernel Trace Control(커널 추적 제어)로 추적을 병합하는 동안 오류가 발생했습니다. |
| `RESULT_CODE_FAILURE_UNKNOWN_ERROR` | 24 (0x00000018) | 알 수 없는 오류가 발생했습니다. |

::: moniker-end
