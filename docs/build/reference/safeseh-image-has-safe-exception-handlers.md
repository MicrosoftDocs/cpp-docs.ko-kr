---
description: 자세히 알아보기:/SAFESEH (이미지에 안전한 예외 처리기 포함)
title: /SAFESEH(이미지에 안전한 예외 처리기 포함)
ms.date: 11/04/2016
f1_keywords:
- /SAFESEH
helpviewer_keywords:
- /SAFESEH linker option
- -SAFESEH linker option
- SAFESEH linker option
ms.assetid: 7722ff99-b833-4c65-a855-aaca902ffcb7
ms.openlocfilehash: 723b5503bca1d98d7df0c638df1dfc8101fc116f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97224987"
---
# <a name="safeseh-image-has-safe-exception-handlers"></a>/SAFESEH(이미지에 안전한 예외 처리기 포함)

```
/SAFESEH[:NO]
```

**/Safeseh** 를 지정 하는 경우 링커에서는 이미지의 안전한 예외 처리기 테이블을 생성할 수 있는 경우에만 이미지를 생성 합니다. 이 테이블은 운영 체제에서 이미지에 대해 유효한 예외 처리기를 지정 합니다.

**/Safeseh** 는 x86 대상에 연결 하는 경우에만 유효 합니다. 이미 표시 된 예외 처리기가 있는 플랫폼에는 **/safeseh** 를 사용할 수 없습니다. 예를 들어 x64 및 ARM에서는 모든 예외 처리기가 .PDATA에 기록 됩니다. ML64.exe는 SEH 정보 (.XDATA 및 .PDATA)를 이미지에 내보내는 주석을 추가 하 여 ml64.exe 함수를 통해 해제할 수 있도록 지원 합니다. 자세한 내용은 x [64 용 MASM (ml64.exe)](../../assembler/masm/masm-for-x64-ml64-exe.md) 을 참조 하세요.

**/Safeseh** 를 지정 하지 않으면 모든 모듈이 안전한 예외 처리 기능과 호환 되는 경우 링커에서 안전한 예외 처리기 테이블을 포함 하는 이미지를 생성 합니다. 모듈이 안전 예외 처리 기능과 호환 되지 않는 경우 결과 이미지는 안전한 예외 처리기 테이블을 포함 하지 않습니다. [/SUBSYSTEM](subsystem-specify-subsystem.md) 에서 WINDOWSCE 또는 EFI_ * 옵션 중 하나를 지정 하는 경우 해당 하위 시스템에서 정보를 사용할 수 없으므로 링커에서 안전한 예외 처리기 테이블을 사용 하 여 이미지를 생성 하려고 시도 하지 않습니다.

**/Safeseh: NO** 를 지정 하면 모든 모듈이 안전한 예외 처리 기능과 호환 되더라도 링커에서 안전 예외 처리기 테이블을 사용 하 여 이미지를 생성 하지 않습니다.

링커가 이미지를 생성할 수 없는 가장 일반적인 이유는 링커에 대 한 하나 이상의 입력 파일 (모듈)이 안전한 예외 처리기 기능과 호환 되지 않기 때문입니다. 모듈이 안전한 예외 처리기와 호환 되지 않는 일반적인 이유는 이전 버전의 Visual C++에서 컴파일러를 사용 하 여 생성 되었기 때문입니다.

를 사용 하 여 구조화 된 예외 처리기로 함수를 등록할 수도 있습니다 [. SAFESEH](../../assembler/masm/dot-safeseh.md).

기존 이진 파일을 안전한 예외 처리기가 있는 것으로 표시할 수 없습니다 (또는 예외 처리기 없음). 안전 예외 처리에 대 한 정보는 빌드 시에 추가 해야 합니다.

안전한 예외 처리기 테이블을 빌드하는 링커 기능은 C 런타임 라이브러리를 사용 하는 응용 프로그램에 따라 달라 집니다. [/Nodefaultlib](nodefaultlib-ignore-libraries.md) 를 사용 하 여 연결 하 고 안전한 예외 처리기의 테이블을 사용 하려는 경우 Visual C++에 대해 정의 된 모든 항목을 포함 하는 로드 구성 구조체 (예: loadcfg. c CRT 소스 파일에서 찾을 수 있음)를 제공 해야 합니다. 예를 들어:

```
#include <windows.h>
extern DWORD_PTR __security_cookie;  /* /GS security cookie */

/*
* The following two names are automatically created by the linker for any
* image that has the safe exception table present.
*/

extern PVOID __safe_se_handler_table[]; /* base of safe handler entry table */
extern BYTE  __safe_se_handler_count;  /* absolute symbol whose address is
                                           the count of table entries */
typedef struct {
    DWORD       Size;
    DWORD       TimeDateStamp;
    WORD        MajorVersion;
    WORD        MinorVersion;
    DWORD       GlobalFlagsClear;
    DWORD       GlobalFlagsSet;
    DWORD       CriticalSectionDefaultTimeout;
    DWORD       DeCommitFreeBlockThreshold;
    DWORD       DeCommitTotalFreeThreshold;
    DWORD       LockPrefixTable;            // VA
    DWORD       MaximumAllocationSize;
    DWORD       VirtualMemoryThreshold;
    DWORD       ProcessHeapFlags;
    DWORD       ProcessAffinityMask;
    WORD        CSDVersion;
    WORD        Reserved1;
    DWORD       EditList;                   // VA
    DWORD_PTR   *SecurityCookie;
    PVOID       *SEHandlerTable;
    DWORD       SEHandlerCount;
} IMAGE_LOAD_CONFIG_DIRECTORY32_2;

const IMAGE_LOAD_CONFIG_DIRECTORY32_2 _load_config_used = {
    sizeof(IMAGE_LOAD_CONFIG_DIRECTORY32_2),
    0,
    0,
    0,
    0,
    0,
    0,
    0,
    0,
    0,
    0,
    0,
    0,
    0,
    0,
    0,
    0,
    &__security_cookie,
    __safe_se_handler_table,
    (DWORD)(DWORD_PTR) &__safe_se_handler_count
};
```

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 링커 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조합니다.

1. **링커** 폴더를 선택 합니다.

1. **명령줄** 속성 페이지를 선택 합니다.

1. **추가 옵션** 상자에 옵션을 입력 합니다.

### <a name="to-set-this-linker-option-programmatically"></a>프로그래밍 방식으로 이 링커 옵션을 설정하려면

- <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>을 참조하세요.

## <a name="see-also"></a>참고 항목

[MSVC 링커 참조](linking.md)<br/>
[MSVC 링커 옵션](linker-options.md)
