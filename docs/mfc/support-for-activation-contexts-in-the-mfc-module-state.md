---
description: '자세한 정보: MFC 모듈 상태의 활성화 컨텍스트 지원'
title: MFC 모듈 상태의 활성화 컨텍스트 지원
ms.date: 11/04/2016
helpviewer_keywords:
- activation contexts [MFC]
- activation contexts [MFC], MFC support
ms.assetid: 1e49eea9-3620-46dd-bc5f-d664749567c7
ms.openlocfilehash: e7f7434824956ca2a62d75fbd50eb9dd5e01f34e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97216472"
---
# <a name="support-for-activation-contexts-in-the-mfc-module-state"></a>MFC 모듈 상태의 활성화 컨텍스트 지원

MFC는 사용자 모듈에서 제공되는 매니페스트 리소스를 사용하여 활성화 컨텍스트를 만듭니다. 활성화 컨텍스트를 만드는 방법에 대한 자세한 내용은 다음 항목을 참조하십시오.

- [활성화 컨텍스트](/windows/win32/SbsCs/activation-contexts)

- [응용 프로그램 매니페스트](/windows/win32/SbsCs/application-manifests)

- [어셈블리 매니페스트](/windows/win32/SbsCs/assembly-manifests)

## <a name="remarks"></a>설명

이러한 Windows SDK 항목을 읽을 때 mfc 활성화 컨텍스트 메커니즘은 MFC에서 Windows SDK 활성화 컨텍스트 API를 사용 하지 않는다는 점을 제외 하 고는 Windows SDK 활성화 컨텍스트와 비슷합니다.

활성화 컨텍스트는 다음과 같은 방법으로 MFC 응용 프로그램, 사용자 Dll 및 MFC 확장명 Dll에서 작동 합니다.

- MFC 애플리케이션은 매니페스트 리소스에 대해 리소스 ID 1을 사용합니다. 이 경우 MFC는 자체 활성화 컨텍스트를 만들지 않지만 기본 애플리케이션 컨텍스트는 사용합니다.

- MFC 사용자 DLL은 매니페스트 리소스에 대해 리소스 ID 2를 사용합니다. 여기에서 MFC는 각 사용자 DLL에 대해 활성화 컨텍스트를 만들므로 다른 사용자 DLL은 동일한 라이브러리의 다른 버전을 사용합니다(예: 공용 컨트롤 라이브러리).

- MFC 확장 DLL은 활성화 컨텍스트를 설정하기 위해 호스팅 애플리케이션 또는 사용자 DLL을 사용합니다.

활성화 컨텍스트 [API 사용](/windows/win32/SbsCs/using-the-activation-context-api)에 설명 된 프로세스를 사용 하 여 활성화 컨텍스트 상태를 수정할 수 있지만, MFC 활성화 컨텍스트 메커니즘을 사용 하면 외부 플러그 인에 대 한 개별 호출 전후에 수동으로 활성화 상태를 전환 하는 것이 용이 하거나 불가능 한 DLL 기반 플러그 인 아키텍처를 개발할 때 유용할 수 있습니다.

활성화 컨텍스트는 [AfxWinInit](../mfc/reference/application-information-and-management.md#afxwininit)에서 만들어집니다. 이러한 활성화 컨텍스트는 `AFX_MODULE_STATE` 소멸자에서 제거됩니다. 활성화 컨텍스트 핸들은 `AFX_MODULE_STATE`에서 유지됩니다. `AFX_MODULE_STATE` [AfxGetStaticModuleState](reference/extension-dll-macros.md#afxgetstaticmodulestate)에 설명 되어 있습니다.

[AFX_MANAGE_STATE](reference/extension-dll-macros.md#afx_manage_state) 매크로는 활성화 컨텍스트를 활성화 하 고 비활성화 합니다. `AFX_MANAGE_STATE`는 정적 MFC 라이브러리와 MFC DLL을 활성화하고 사용자 DLL이 선택한 해당 활성화 컨텍스트에서 실행되도록 MFC 코드를 허용합니다.

## <a name="see-also"></a>참고 항목

[활성화 컨텍스트](/windows/win32/SbsCs/activation-contexts)<br/>
[응용 프로그램 매니페스트](/windows/win32/SbsCs/application-manifests)<br/>
[어셈블리 매니페스트](/windows/win32/SbsCs/assembly-manifests)<br/>
[AfxWinInit](../mfc/reference/application-information-and-management.md#afxwininit)<br/>
[AfxGetStaticModuleState](reference/extension-dll-macros.md#afxgetstaticmodulestate)<br/>
[AFX_MANAGE_STATE](reference/extension-dll-macros.md#afx_manage_state)
