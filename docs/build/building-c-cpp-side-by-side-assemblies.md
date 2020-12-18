---
description: '자세한 정보: C/C++ side-by-side 어셈블리 빌드'
title: C/C++ side-by-side 어셈블리 빌드
ms.date: 11/04/2016
helpviewer_keywords:
- side-by-side applications [C++]
ms.assetid: 7fa20b16-3737-4f76-a0b5-1dacea19a1e8
ms.openlocfilehash: 174104157653eef15e67f66c67c935b7f386b71e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97157063"
---
# <a name="building-cc-side-by-side-assemblies"></a>C/C++ side-by-side 어셈블리 빌드

[side-by-side](/windows/win32/SbsCs/about-side-by-side-assemblies-) 어셈블리는 런타임에 실행할 애플리케이션에 사용할 수 있는 리소스(DLL 그룹, windows 클래스, COM 서버, 형식 라이브러리 또는 인터페이스)의 컬렉션입니다. DLL을 어셈블리로 다시 패키지하는 경우의 주된 이점은 애플리케이션에서 여러 버전의 어셈블리를 동시에 사용할 수 있으며 업데이트 릴리스의 경우 현재 설치된 어셈블리를 서비스할 수 있다는 것입니다.

C++ 애플리케이션은 애플리케이션의 여러 부분에서 하나 이상의 DLL을 사용할 수 있습니다. 런타임에 DLL이 주 프로세스로 로드되고 필요한 코드가 실행됩니다. 애플리케이션은 운영 체제를 사용하여 요청된 DLL을 찾고, 로드할 다른 종속 DLL을 파악한 다음 요청된 DLL과 함께 로드합니다. Windows XP, Windows Server 2003, Windows Vista 이전 버전의 Windows 운영 체제에서는 운영 체제 로더가 애플리케이션의 로컬 폴더나 시스템 경로에 지정된 다른 폴더에서 종속 DLL을 검색합니다. Windows XP, Windows Server 2003 및 Windows Vista에서는 운영 체제 로더가 [매니페스트](/windows/win32/sbscs/manifests) 파일을 사용하여 종속 DLL을 검색하고 종속 DLL을 포함하는 side-by-side 어셈블리를 검색할 수도 있습니다.

기본적으로 DLL이 Visual Studio로 빌드된 경우 [애플리케이션 매니페스트](/windows/win32/SbsCs/application-manifests)가 ID가 2인 RT_MANIFEST 리소스로 DLL에 포함되어 있습니다. 실행 파일의 경우와 마찬가지로 이 매니페스트는 이 DLL의 다른 어셈블리에 대한 종속성을 설명합니다. 여기서는 DLL이 side-by-side 어셈블리의 일부가 아니고 이 DLL에 종속된 애플리케이션이 애플리케이션 매니페스트를 사용하여 DLL을 로드하지 않고 대신 운영 체제 로더를 사용하여 시스템 경로에서 이 DLL을 찾는다고 가정합니다.

> [!NOTE]
> 애플리케이션 매니페스트를 사용하는 DLL에 ID가 2인 리소스로 매니페스트를 포함하고 있다는 것이 중요합니다. DLL이 런타임에 동적으로 로드되는 경우(예: [LoadLibrary](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryw) 함수 사용) 운영 체제 로더가 DLL의 매니페스트에 지정된 종속 어셈블리를 로드합니다. DLL의 외부 애플리케이션 매니페스트는 `LoadLibrary` 호출 중에 검사하지 않습니다. 매니페스트가 포함되지 않은 경우 로더는 잘못된 버전의 어셈블리를 로드하려고 하거나 종속 어셈블리를 찾지 못할 수 있습니다.

어셈블리를 구성하는 파일과 어셈블리의 다른 side-by-side 어셈블리에 대한 종속성을 설명하는 해당하는 [어셈블리 매니페스트](/windows/win32/SbsCs/assembly-manifests)를 사용하여 하나 이상의 관련 DLL을 side-by-side 어셈블리로 다시 패키지 할 수 있습니다.

> [!NOTE]
> 어셈블리에 하나의 DLL이 포함된 경우 이 DLL에 어셈블리 매니페스트를 ID가 1인 리소스로 포함하고 이 프라이빗 어셈블리에 DLL과 같은 이름을 지정하는 것이 좋습니다. 예를 들어 DLL의 이름이 mylibrary.dll인 경우 매니페스트의 \<assemblyIdentity> 요소에 사용되는 이름 특성의 값도 mylibrary일 수 있습니다. 때에 따라 라이브러리에 .dll 이외의 확장이 있으면(예: MFC ActiveX 컨트롤 프로젝트에서 .ocx 라이브러리를 만드는 경우) 외부 어셈블리 매니페스트를 만들 수 있습니다. 이 경우 어셈블리와 해당 매니페스트의 이름은 DLL의 이름과 달라야 합니다(예: MyAssembly, MyAssembly.manifest 및 mylibrary .ocx). 그러나 관련 라이브러리 이름을 extension.dll로 바꾸고 매니페스트를 리소스로 포함하여 이 어셈블리의 이후 유지 관리 비용을 줄이는 것이 좋습니다. 운영 체제에서 프라이빗 어셈블리를 검색하는 방법에 대한 자세한 내용은 [어셈블리 검색 시퀀스](/windows/win32/SbsCs/assembly-searching-sequence)를 참조하세요.

이렇게 변경하면 해당 DLL을 애플리케이션 로컬 폴더에 [프라이빗 어셈블리](/windows/win32/Msi/private-assemblies)로 배포하거나 WinSxS 어셈블리 캐시에 [공유 어셈블리](/windows/win32/Msi/shared-assemblies)로 배포할 수 있습니다. 이 새 어셈블리의 올바른 런타임 동작을 얻기 위해 몇 가지 단계를 수행해야 합니다. 관련 내용은 [Side-by-side 어셈블리 만들기 지침](/windows/win32/SbsCs/guidelines-for-creating-side-by-side-assemblies)에서 설명되어 있습니다. 어셈블리를 올바르게 작성한 후에는 해당 어셈블리에 종속된 애플리케이션과 함께 공유 또는 프라이빗 어셈블리로 배포할 수 있습니다. Side-by-side 어셈블리를 공유 어셈블리로 설치할 경우 [Windows XP에서 Side-by-Side 공유를 위해 Win32 어셈블리 설치](/windows/win32/Msi/installing-win32-assemblies-for-side-by-side-sharing-on-windows-xp)에 설명된 지침을 따르거나 [병합 모듈](/windows/win32/msi/merge-modules)을 사용할 수 있습니다. Side-by-side 어셈블리를 프라이빗 어셈블리로 설치할 경우에는 설치 프로세스의 일부로 해당하는 DLL, 리소스 및 어셈블리 매니페스트를 대상 컴퓨터의 애플리케이션 로컬 폴더에 복사하여 런타임에 로더가 이 어셈블리를 찾을 수 있게만 하면 됩니다([어셈블리 검색 시퀀스](/windows/win32/SbsCs/assembly-searching-sequence) 참조). 또 다른 방법은 [Windows Installer](/windows/win32/Msi/windows-installer-portal)를 사용하고 [Windows XP에서 애플리케이션의 프라이빗 사용을 위해 Win32 어셈블리 설치](/windows/win32/Msi/installing-win32-assemblies-for-the-private-use-of-an-application-on-windows-xp)에 설명된 지침을 따르는 것입니다.

## <a name="see-also"></a>참조

[ 격리된 애플리케이션 빌드](building-c-cpp-isolated-applications.md)<br/>
[C/C++ 격리된 애플리케이션 및 side-by-side 어셈블리 빌드](building-c-cpp-isolated-applications-and-side-by-side-assemblies.md)
