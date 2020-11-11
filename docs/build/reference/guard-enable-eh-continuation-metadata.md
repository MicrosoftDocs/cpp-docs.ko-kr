---
title: /guard:ehcont (EH 연속 메타데이터 사용)
description: 'Microsoft c + +/guard: ehcont 컴파일러 옵션에 대 한 참조 가이드입니다.'
ms.date: 06/03/2020
f1_keywords:
- /guard:ehcont
- VC.Project.VCCLCompilerTool.GuardEHContMetadata
helpviewer_keywords:
- /guard:ehcont
- /guard:ehcont compiler option
ms.openlocfilehash: ea6a225dce9bf76ff2dc69945916c006a0d5ec0b
ms.sourcegitcommit: 25f6d52eb9e5d84bd0218c46372db85572af81da
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94448375"
---
# <a name="guardehcont-enable-eh-continuation-metadata"></a>`/guard:ehcont` (EH 연속 메타 데이터 사용)

컴파일러에서 EH 연속 (EHCONT) 메타 데이터를 생성할 수 있도록 합니다.

## <a name="syntax"></a>구문

> **`/guard:ehcont`** [ **`-`** ]

## <a name="remarks"></a>설명

**`/guard:ehcont`** 옵션을 선택 하면 컴파일러가 이진에 대 한 모든 유효한 예외 처리 연속 대상의 RVA (상대 가상 주소)에 대 한 정렬 된 목록을 생성 합니다. `NtContinue`및 `SetThreadContext` 명령 포인터 유효성 검사를 위해 런타임에 사용 됩니다. 기본적으로 **`/guard:ehcont`** 는 해제 되어 있으며 명시적으로 사용 하도록 설정 해야 합니다. 이 옵션을 명시적으로 사용 하지 않도록 설정 하려면를 사용 **`/guard:ehcont-`** 합니다.

**`/guard:ehcont`** 이 옵션은 Visual Studio 2019 버전 16.7 이상에서 사용할 수 있습니다. 이 기능은 64 비트 OS에서 64 비트 프로세스에 대해 지원 됩니다.

[CET (제어 흐름 적용 기술)](https://software.intel.com/sites/default/files/managed/4d/2a/control-flow-enforcement-technology-preview.pdf) 는 ROP (Return-Oriented 프로그래밍) 기반 공격 으로부터 보호 하는 하드웨어 기반 보안 기능입니다. 제어 흐름 무결성을 적용 하기 위해 모든 호출 스택에 대 한 "섀도 스택"을 유지 관리 합니다.

ROP 공격을 방지 하기 위해 섀도 스택을 사용할 수 있는 경우 공격자는 다른 악용 기술을 사용 하 여 이동 합니다. 사용할 수 있는 방법 중 하나는 [컨텍스트](/windows/win32/api/winnt/ns-winnt-context) 구조 내에서 명령 포인터 값을 손상 시키는 것입니다. 이 구조체는,, 등의 스레드 실행을 리디렉션하는 시스템 호출에 전달 `NtContinue` [`RtlRestoreContext`](/windows/win32/api/winnt/nf-winnt-rtlrestorecontext) [`SetThreadContext`](/windows/win32/api/processthreadsapi/nf-processthreadsapi-setthreadcontext) 됩니다. `CONTEXT`구조는 메모리에 저장 됩니다. 포함 된 명령 포인터를 손상 하면 시스템 호출에서 공격자가 제어 하는 주소로 실행을 전송할 수 있습니다. 현재는 `NTContinue` 임의의 연속 지점과 함께 호출할 수 있습니다. 이는 섀도 스택을 사용할 때 명령 포인터의 유효성을 검사 하는 데 필수적입니다.

`RtlRestoreContext` 및 `NtContinue` 는 SEH (구조적 예외 처리) 예외 해제 중에 블록이 포함 된 대상 프레임에 대 한 해제를 사용 **`__except`** 합니다. 명령 포인터의 **`__except`** 유효성 검사에 실패 하기 때문에 블록의 명령 포인터가 그림자 스택에 있을 것으로 예상 되지 않습니다. **`/guard:ehcont`** 컴파일러 스위치는 "EH 연속 테이블"을 생성 합니다. 이진의 모든 유효한 예외 처리 연속 대상에 대 한 Rva의 정렬 된 목록을 포함 합니다. `NtContinue` 는 먼저 사용자가 제공한 명령 포인터에 대 한 섀도 스택을 확인 하 고 명령 포인터가 없는 경우 명령 포인터가 포함 된 이진 파일에서 EH 연속 테이블을 확인 합니다. 포함 하는 이진이 테이블을 사용 하 여 컴파일되지 않은 경우 레거시 바이너리와의 호환성을 위해을 `NtContinue` 계속 사용할 수 있습니다. EHCONT 데이터가 없는 레거시 바이너리와 EHCONT 데이터를 포함 하지만 테이블 항목은 포함 하지 않는 이진 파일을 구분 하는 것이 중요 합니다. 전자는 이진 내의 모든 주소를 유효한 연속 대상으로 허용 합니다. 후자는 이진 내의 모든 주소를 유효한 연속 대상으로 허용 하지 않습니다.

**`/guard:ehcont`** 이진에 대해 EH 연속 대상 rva를 생성 하려면이 옵션을 컴파일러와 링커 둘 다에 전달 해야 합니다. 단일 `cl` 명령을 사용하여 이진 파일이 빌드된 경우 컴파일러는 옵션을 링커에 전달합니다. 또한 컴파일러는 옵션을 [`/guard:cf`](guard-enable-control-flow-guard.md) 링커에 전달 합니다. 개별적으로 컴파일 및 연결 하는 경우 이러한 옵션은 컴파일러 및 링커 명령 둘 다에서 설정 해야 합니다.

를 사용 하 여 컴파일된 코드 **`/guard:ehcont`** 를 라이브러리 및 라이브러리를 사용 하지 않고 컴파일된 개체 파일에 연결할 수 있습니다. 링커는 다음과 같은 시나리오에서 심각한 오류를 반환 합니다.

- 코드 섹션에는 "로컬 해제"가 있습니다. 자세한 내용은 [try-Finally 문의](../../cpp/try-finally-statement.md#abnormal-termination)비정상 종료를 참조 하십시오.

- EH (.xdata) 섹션에는 코드 섹션에 대 한 포인터가 포함 되어 있으며 SEH 용이 아닙니다.

- 포인터는 SEH를 위한 것 이지만 개체 파일은 Comdat를 생성 하는 함수 수준 링크 ([/gy](gy-enable-function-level-linking.md))를 사용 하 여 컴파일되지 않았습니다.

이러한 시나리오에서 메타 데이터를 생성할 수 없기 때문에 링커가 심각한 오류를 반환 합니다. 즉, 예외가 throw 되 면 런타임에 충돌이 발생할 수 있습니다.

Comdat에서 찾았지만를 사용 하 여 컴파일되지 않은 SEH 섹션 정보의 경우 **`/guard:ehcont`** 링커에서 경고 **LNK4291** 을 내보냅니다. 이 경우 링커는 섹션에 대해 올바르지만 보수적인 메타 데이터를 생성 합니다. 이 경고를 무시 하려면 [/IGNORE (특정 경고 무시)](ignore-ignore-specific-warnings.md)를 사용 합니다.

링커가 메타 데이터를 생성할 수 없는 경우 다음 오류 중 하나를 내보냅니다.

- `LNK2046: module contains _local_unwind but was not compiled with /guard:ehcont`

- `LNK2047: module contains C++ EH or complex EH metadata but was not compiled with /guard:ehcont.`

이진 파일에 EHCONT 데이터가 포함 되어 있는지 확인 하려면 이진의 load config를 덤프할 때 다음 요소를 찾습니다.

```cmd
e:\>link /dump /loadconfig CETTest.exe
...
            10417500 Guard Flags
...
                       EH Continuation table present      // EHCONT guard flag present
...
    0000000180018640 Guard EH continuation table
                  37 Guard EH continuation count          // May be 0 if no exception handling is used in the binary. Still counts has having EHCONT data.
...
    Guard EH Continuation Table                           // List of RVAs

          Address
          --------
           0000000180002CF5
           0000000180002F03
           0000000180002F0A
...
```

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 컴파일러 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조합니다.

1. **구성 속성**  >  **C/c + +**  >  **코드 생성** 속성 페이지를 선택 합니다.

1. **EH 연속 메타 데이터 사용** 속성을 선택 합니다.

1. 드롭다운 컨트롤에서 **예 (/b가드: ehcont)** 를 선택 하 여 EH 연속 메타 데이터를 사용 하도록 설정 하거나 **No (/sguard: ehcont-)** 를 선택 하 여 사용 하지 않도록 설정 합니다.

## <a name="see-also"></a>참조

[/s가드 (제어 흐름 보호 사용)](guard-enable-control-flow-guard.md)\
[MSVC 컴파일러 옵션](compiler-options.md)\
[MSVC 컴파일러 Command-Line 구문](compiler-command-line-syntax.md)
