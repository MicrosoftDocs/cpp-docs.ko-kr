---
title: ATL 마법사로 추가한 ATL 지원에 대한 세부 정보
ms.date: 08/20/2019
f1_keywords:
- vc.codewiz.atl.support
helpviewer_keywords:
- MFC, ATL support
- ATL, MFC projects
ms.assetid: aa66bad0-008f-4886-94c1-2a0a0d04bce4
ms.openlocfilehash: aeac01ce58deb429f14058c06524dff53abde060
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92924438"
---
# <a name="details-of-atl-support-added-by-the-atl-wizard"></a>ATL 마법사로 추가한 ATL 지원에 대한 세부 정보

::: moniker range=">=msvc-160"

[기존 MFC 실행 파일 또는 DLL에 atl 지원을 추가](../../mfc/reference/adding-atl-support-to-your-mfc-project.md)하는 경우 Visual Studio는 기본적으로 *프레임 워크* 라는 헤더 파일을 추가 합니다. 여기에는 `#include` 및 `#define` 전처리기 지시문을 포함 하 여 프로젝트에서 atl을 사용할 수 있습니다. 이전 버전의 Visual Studio에서와 같이 추가 파일이 나 클래스는 추가 되지 않습니다.

::: moniker-end

::: moniker range="<=msvc-150"

[기존 mfc 실행 파일 또는 DLL에 ATL 지원을 추가](../../mfc/reference/adding-atl-support-to-your-mfc-project.md)하는 경우 Visual Studio는 기존 mfc 프로젝트를 다음과 같이 수정 합니다 (이 예제에서는 프로젝트가 호출 됨 `MFCEXE` ).

- 서버를 등록 하는 데 사용 되는 두 개의 새 파일 (.idl 파일 및 .rgs 파일)이 추가 됩니다.

- 주 응용 프로그램 헤더 및 구현 파일 (Mfcexe 및 Mfcexe)에서 새 클래스 (에서 파생 됨 `CAtlMFCModule` )가 추가 됩니다. 새 클래스 외에도 등록을 위해 코드를에 추가 `InitInstance` 합니다. 코드는 클래스 개체를 취소 `ExitInstance` 하기 위한 함수에도 추가 됩니다. 마지막으로 헤더 파일에서 두 개의 새 헤더 파일 (Initguid. h 및 Mfcexe_i .c)이 구현 파일에 포함 되어 파생 클래스에 대 한 새 Guid를 선언 하 고 초기화 합니다 `CAtlMFCModule` .

- 서버를 제대로 등록 하기 위해 새 .rgs 파일의 항목이 프로젝트의 리소스 파일에 추가 됩니다.

::: moniker-end

## <a name="notes-for-dll-projects"></a>DLL 프로젝트에 대 한 참고 사항

MFC DLL 프로젝트에 ATL 지원을 추가 하면 몇 가지 차이점이 표시 됩니다. `DLLRegisterServer` `DLLUnregisterServer` DLL을 등록 하 고 등록을 취소 하기 위해 및 함수에 코드가 추가 됩니다. [DllCanUnloadNow](../../atl/reference/catldllmodulet-class.md#dllcanunloadnow) 및 [DllGetClassObject](../../atl/reference/catldllmodulet-class.md#dllgetclassobject)에도 코드가 추가 됩니다.

## <a name="see-also"></a>참고 항목

[MFC 프로젝트의 ATL 지원](../../mfc/reference/adding-atl-support-to-your-mfc-project.md)<br/>
[코드 마법사에서 기능 추가](../../ide/adding-functionality-with-code-wizards-cpp.md)<br/>
[클래스 추가](../../ide/adding-a-class-visual-cpp.md)<br/>
[멤버 함수 추가](../../ide/adding-a-member-function-visual-cpp.md)<br/>
[멤버 변수 추가](../../ide/adding-a-member-variable-visual-cpp.md)<br/>
[가상 함수 재정의](../../ide/overriding-a-virtual-function-visual-cpp.md)<br/>
[MFC 메시지 처리기](../../mfc/reference/adding-an-mfc-message-handler.md)<br/>
[클래스 구조 탐색](../../ide/navigate-code-cpp.md)
