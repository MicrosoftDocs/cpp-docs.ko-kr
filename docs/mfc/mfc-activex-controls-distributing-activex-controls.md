---
description: '자세한 정보: MFC ActiveX 컨트롤: ActiveX 컨트롤 배포'
title: 'MFC ActiveX 컨트롤: ActiveX 컨트롤 배포'
ms.date: 09/12/2018
f1_keywords:
- GetWindowsDirectory
- GetSystemDirectory
helpviewer_keywords:
- MFC ActiveX controls [MFC], ANSI or Unicode versions
- RegSvr32.exe
- MFC ActiveX controls [MFC], distributing
- distributing MFC ActiveX controls
- redistributable files, MFC ActiveX controls
- GetSystemDirectory method [MFC]
- registering ActiveX controls
- MSVCRT40.dll
- registry [MFC], registering controls
- LoadLibrary method, registering ActiveX controls
- MFC40U.DLL
- MFC40.DLL
- GetWindowsDirectory method [MFC]
- installing ActiveX controls
- GetProcAddress method, registering ActiveX controls
- MFC ActiveX controls [MFC], installing
- MFC ActiveX controls [MFC], registering
- registering controls
- OLEPRO32.DLL
ms.assetid: cd70ac9b-f613-4879-9e81-6381fdfda2a1
ms.openlocfilehash: faf85bffd9911c38764aea19d1ddb682fd719be1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97280718"
---
# <a name="mfc-activex-controls-distributing-activex-controls"></a>MFC ActiveX 컨트롤: ActiveX 컨트롤 배포

이 문서에서는 ActiveX 컨트롤 재배포와 관련 된 몇 가지 문제에 대해 설명 합니다.

- [ANSI 또는 유니코드 컨트롤 버전](#_core_ansi_or_unicode_control_versions)

- [ActiveX 컨트롤 및 재배포 가능 Dll 설치](#_core_installing_activex_controls_and_redistributable_dlls)

- [컨트롤 등록](#_core_registering_controls)

>[!IMPORTANT]
> ActiveX는 새로운 개발에 사용 하지 않아야 하는 레거시 기술입니다. ActiveX를 대체 하는 최신 기술에 대 한 자세한 내용은 [Activex Controls](activex-controls.md)을 참조 하세요.

## <a name="ansi-or-unicode-control-versions"></a><a name="_core_ansi_or_unicode_control_versions"></a> ANSI 또는 유니코드 컨트롤 버전

컨트롤의 ANSI 또는 유니코드 버전을 제공할지 아니면 둘 다 제공할지를 결정 해야 합니다. 이러한 결정은 ANSI 및 유니코드 문자 집합의 고유한 이식성 요인을 기반으로 합니다.

모든 Win32 운영 체제에서 작동 하는 ANSI 컨트롤은 다양 한 Win32 운영 체제 간의 이식성을 극대화 합니다. 유니코드 컨트롤은 windows NT (버전 3.51 이상) 에서만 작동 하지만 Windows 95 또는 Windows 98에서는 작동 하지 않습니다. 이식성이 중요 한 경우 ANSI 컨트롤을 제공 합니다. 컨트롤이 Windows NT 에서만 실행 되는 경우 유니코드 컨트롤을 제공할 수 있습니다. 또한를 제공 하 고 응용 프로그램에서 사용자 운영 체제에 가장 적합 한 버전을 설치 하도록 선택할 수도 있습니다.

## <a name="installing-activex-controls-and-redistributable-dlls"></a><a name="_core_installing_activex_controls_and_redistributable_dlls"></a> ActiveX 컨트롤 및 재배포 가능 Dll 설치

ActiveX 컨트롤을 사용 하 여 제공 하는 설치 프로그램은 Windows 디렉터리의 특수 한 하위 디렉터리를 만들고 컨트롤을 설치 해야 합니다. 여기에는 OCX 파일이 있습니다.

> [!NOTE]
> `GetWindowsDirectory`설치 프로그램에서 windows API를 사용 하 여 windows 디렉터리의 이름을 가져옵니다. 회사 또는 제품의 이름에서 하위 디렉터리 이름을 파생 시킬 수 있습니다.

설치 프로그램에서 필요한 재배포 가능 DLL 파일을 Windows 시스템 디렉터리에 설치 해야 합니다. Dll이 사용자의 컴퓨터에 이미 있는 경우 설치 프로그램에서 해당 버전을 설치 하는 버전과 비교 해야 합니다. 버전 번호가 이미 설치 된 파일 보다 높은 경우에만 파일을 다시 설치 하십시오.

ActiveX 컨트롤은 OLE 컨테이너 응용 프로그램 에서만 사용할 수 있기 때문에 OLE Dll의 전체 집합을 컨트롤에 배포할 필요가 없습니다. 포함 하는 응용 프로그램 (또는 운영 체제 자체)에 표준 OLE Dll이 설치 되어 있다고 가정할 수 있습니다.

## <a name="registering-controls"></a><a name="_core_registering_controls"></a> 컨트롤 등록

컨트롤을 사용 하려면 먼저 Windows 등록 데이터베이스에서 해당 항목에 대 한 적절 한 항목을 만들어야 합니다. 일부 ActiveX 컨트롤 컨테이너는 사용자가 새 컨트롤을 등록 하는 데 사용할 수 있는 메뉴 항목을 제공 하지만 일부 컨테이너에서는이 기능을 사용할 수 없습니다. 따라서 설치 프로그램에서 컨트롤을 설치할 때 등록 하도록 할 수 있습니다.

원하는 경우 대신 컨트롤을 직접 등록 하는 설치 프로그램을 작성할 수 있습니다.

`LoadLibrary`WINDOWS API를 사용 하 여 컨트롤 DLL을 로드 합니다. 그런 다음를 사용 `GetProcAddress` 하 여 "DllRegisterServer" 함수의 주소를 가져옵니다. 마지막으로 함수를 호출 `DllRegisterServer` 합니다. 다음 코드 샘플에서는에서 `hLib` 컨트롤 라이브러리의 핸들을 저장 하 고 `lpDllEntryPoint` "DllRegisterServer" 함수의 주소를 저장 하는 한 가지 가능한 메서드를 보여 줍니다.

[!code-cpp[NVC_MFC_AxCont#16](codesnippet/cpp/mfc-activex-controls-distributing-activex-controls_1.cpp)]

컨트롤을 직접 등록 하는 경우에는 별도의 프로세스 (예를 들어 REGSVR32)를 호출 하 고 로드 하지 않아도 되므로 설치 시간이 단축 될 수 있다는 장점이 있습니다. 또한 등록이 내부 프로세스 이기 때문에 설치 프로그램은 외부 프로세스 보다 오류 및 예측할 수 없는 상황을 처리할 수 있습니다.

> [!NOTE]
> 설치 프로그램에서 ActiveX 컨트롤을 설치 하기 전에를 호출 해야 `OleInitialize` 합니다. 설치 프로그램이 완료 되 면를 호출 `OleUnitialize` 합니다. 이렇게 하면 OLE 시스템 Dll이 ActiveX 컨트롤을 등록 하는 데 적합 한 상태가 됩니다.

MFCx0.DLL를 등록 해야 합니다.

## <a name="see-also"></a>참고 항목

[MFC ActiveX 컨트롤](mfc-activex-controls.md)
