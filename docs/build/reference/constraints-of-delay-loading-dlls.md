---
description: '자세한 정보: Dll 지연 로드의 제약 조건'
title: DLL 지연 로드의 제약 조건
ms.date: 01/19/2021
helpviewer_keywords:
- constraints [C++], delayed loading of DLLs
- delayed loading of DLLs, constraints
- DLLs [C++], constraints
ms.openlocfilehash: 0bc29695aa48fea08a0126d4b814329656a5d3bf
ms.sourcegitcommit: 3d9cfde85df33002e3b3d7f3509ff6a8dc4c0a21
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/21/2021
ms.locfileid: "98666981"
---
# <a name="constraints-of-delay-loading-dlls"></a>DLL 지연 로드의 제약 조건

DLL 가져오기의 지연 로드에 대 한 몇 가지 제약 조건이 있습니다.

- 데이터 가져오기는 지원 되지 않습니다. 해결 방법은를 사용 하 여 데이터 가져오기를 직접 처리 하거나, `LoadLibrary` `GetModuleHandle` 지연 로드 도우미가 DLL을 로드 한 후를 사용 하 여 데이터 가져오기를 명시적으로 처리 하는 것입니다 `GetProcAddress` .

- 지연 로드는 *`Kernel32.dll`* 지원 되지 않습니다. 지연 로드 도우미 루틴이 작동 하려면이 DLL을 로드 해야 합니다.

- 전달 된 진입점의 [바인딩은](binding-imports.md) 지원 되지 않습니다.

- DLL이 시작 시 로드 되지 않고 지연 로드 되는 경우 프로세스는 다른 동작을 가질 수 있습니다. 지연 로드 된 DLL의 진입점에서 발생 하는 프로세스별 초기화가 있는 경우 볼 수 있습니다. 다른 경우에는를 사용 하 여 선언 된 정적 TLS (스레드 로컬 저장소)가 [`__declspec(thread)`](../../cpp/thread.md) 있습니다 .이는를 통해 DLL이 로드 될 때 처리 되지 않습니다 `LoadLibrary` . `TlsAlloc`, `TlsFree`, `TlsGetValue` 및 `TlsSetValue`를 사용하는 동적 TLS는 정적 또는 지연 로드된 DLL에 계속해서 사용할 수 있습니다.

- 각 함수를 처음 호출 하 고 나면 가져온 함수에 대 한 정적 전역 함수 포인터를 다시 초기화 합니다. 함수 포인터를 처음 사용 하는 것은 로드 된 함수가 아닌 썽크를 가리키기 때문에 필요 합니다.

- 현재 일반 가져오기 메커니즘을 사용 하는 동안에는 DLL에서 특정 프로시저의 로드를 지연할 수 있는 방법이 없습니다.

- 사용자 지정 호출 규칙 (예: x86 아키텍처의 조건 코드 사용)은 지원 되지 않습니다. 또한 부동 소수점 레지스터는 플랫폼에 저장 되지 않습니다. 사용자 지정 도우미 루틴 또는 후크 루틴이 부동 소수점 형식을 사용 하는 경우 부동 소수점 매개 변수와 함께 등록 호출 규칙을 사용 하는 컴퓨터에 전체 부동 소수점 상태를 저장 하 고 복원 해야 합니다. 특히 help 함수의 NDP (숫자 데이터 프로세서) 스택에서 부동 소수점 매개 변수를 사용 하는 CRT 함수를 호출 하는 경우 CRT DLL을 지연 로드 하는 데 주의 해야 합니다.

## <a name="see-also"></a>참고 항목

[링커에서 지연 로드 된 Dll 지원](linker-support-for-delay-loaded-dlls.md)\
[`LoadLibrary` 칩셋용으로](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryw)\
[`GetModuleHandle` 칩셋용으로](/windows/win32/api/libloaderapi/nf-libloaderapi-getmodulehandlew)\
[`GetProcAddress` 칩셋용으로](/windows/win32/api/libloaderapi/nf-libloaderapi-getprocaddress)\
[`TlsAlloc` 칩셋용으로](/windows/win32/api/processthreadsapi/nf-processthreadsapi-tlsalloc)\
[`TlsFree` 칩셋용으로](/windows/win32/api/processthreadsapi/nf-processthreadsapi-tlsfree)\
[`TlsGetValue` 칩셋용으로](/windows/win32/api/processthreadsapi/nf-processthreadsapi-tlsgetvalue)\
[`TlsSetValue` 함수](/windows/win32/api/processthreadsapi/nf-processthreadsapi-tlssetvalue)
