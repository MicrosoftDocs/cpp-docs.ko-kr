---
description: 'TN057: MFC 구성 요소 지역화에 대 한 자세한 정보'
title: 'TN057: MFC 구성 요소 지역화'
ms.date: 06/28/2018
helpviewer_keywords:
- components [MFC], localizing
- TN057
- resources [MFC], localization
- localization [MFC], MFC resources
- localization [MFC], MFC components
- MFC DLLs [MFC], localizing
- DLLs [MFC], localizing MFC
- localization [MFC], resources
ms.assetid: 5376d329-bd45-41bd-97f5-3d895a9a0af5
ms.openlocfilehash: d4a331e74acd2b5b38ae059ea180a0a2148e3a0f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97214808"
---
# <a name="tn057-localization-of-mfc-components"></a>TN057: MFC 구성 요소 지역화

> [!NOTE]
> 다음 기술 노트는 온라인 설명서에 먼저 포함되어 있었으므로 업데이트되지 않았습니다. 따라서 일부 절차 및 항목은 만료되거나 올바르지 않을 수 있습니다. 최신 정보를 보려면 온라인 설명서 색인에서 관심 있는 항목을 검색하는 것이 좋습니다.

이 참고는 응용 프로그램 또는 OLE 컨트롤이 나 MFC를 사용 하는 DLL 인 경우 구성 요소를 지역화 하는 데 사용할 수 있는 몇 가지 디자인 및 절차를 설명 합니다.

## <a name="overview"></a>개요

MFC를 사용 하는 구성 요소를 지역화할 때 두 가지 문제를 해결 해야 합니다. 먼저 사용자 고유의 리소스 (문자열, 대화 상자 및 구성 요소와 관련 된 기타 리소스)를 지역화 해야 합니다. MFC를 사용 하 여 빌드된 대부분의 구성 요소는 MFC로 정의 된 많은 리소스를 포함 하 고 사용 합니다. 지역화 된 MFC 리소스도 제공 해야 합니다. 다행히 MFC 자체에서 여러 언어를 이미 제공 하 고 있습니다.

또한 구성 요소를 대상 환경 (유럽 또는 DBCS 사용 환경)에서 실행할 수 있도록 준비 해야 합니다. 대부분의 경우이는 상위 비트를 올바르게 설정 하 고 더블 바이트 문자를 사용 하 여 문자열을 처리 하는 문자를 처리 하는 응용 프로그램에 따라 달라 집니다. 기본적으로 MFC는 이러한 두 환경 모두에 대해 기본적으로 사용 하도록 설정 되어 있으며,이는 설치 시에 다른 리소스가 연결 되어 있는 모든 플랫폼에서 사용 되는 단일 세계 이진 파일을 사용할 수 있도록 합니다.

## <a name="localizing-your-components-resources"></a>구성 요소의 리소스 지역화

응용 프로그램 또는 DLL에 대 한 지역화는 단순히 리소스를 대상 언어와 일치 하는 리소스로 바꾸는 것을 포함 해야 합니다. 사용자 고유의 리소스의 경우 리소스 편집기에서 리소스를 편집 하 고 응용 프로그램을 빌드하여 비교적 간단 합니다. 코드가 제대로 작성 된 경우에는 c + + 소스 코드에 하드 코딩 된 문자열이 나 텍스트가 없습니다. 모든 지역화는 단순히 리소스를 수정 하 여 수행할 수 있습니다. 실제로 지역화 된 버전을 제공 하는 모든에 원래 코드의 빌드가 포함 되지 않도록 구성 요소를 구현할 수 있습니다. 이는 좀 더 복잡 하지만 매우 가치가 있으며 MFC 자체에 대해 선택 되는 메커니즘입니다. 리소스 편집기에 EXE 또는 DLL 파일을 로드 하 고 리소스를 직접 편집 하 여 응용 프로그램을 지역화할 수도 있습니다. 가능 하면 응용 프로그램의 새 버전을 빌드할 때마다 해당 변경 내용을 reapplication 해야 합니다.

이를 방지 하는 한 가지 방법은 위성 DLL이 라고도 하는 별도의 DLL에서 모든 리소스를 찾는 것입니다. 그런 다음이 DLL은 런타임에 동적으로 로드 되 고 모든 코드를 사용 하 여 주 모듈이 아니라 해당 DLL에서 리소스를 로드 합니다. MFC는이 방법을 직접 지원 합니다. MYAPP.EXE 라는 응용 프로그램을 고려 합니다. 이 클래스에는 MYRES.DLL 이라는 DLL에 있는 모든 리소스가 있을 수 있습니다. 응용 프로그램에서는 `InitInstance` 다음을 수행 하 여 해당 DLL을 로드 하 고 MFC가 해당 위치에서 리소스를 로드 하도록 합니다.

```cpp
CMyApp::InitInstance()
{
    // one of the first things in the init code
    HINSTANCE hInst = LoadLibrary("myres.dll");

    if (hInst != NULL)
        AfxSetResourceHandle(hInst);

    // other initialization code would follow
    // ...
}
```

그런 다음부터 MFC는 myapp.exe 대신 해당 DLL에서 리소스를 로드 합니다. 그러나이 DLL에는 모든 리소스가 있어야 합니다. MFC는 지정 된 리소스를 검색 하는 응용 프로그램의 인스턴스를 검색 하지 않습니다. 이 기법은 일반 MFC Dll 뿐만 아니라 OLE 컨트롤에도 동일 하 게 적용 됩니다. 설치 프로그램은 사용자가 원하는 리소스 로캘에 따라 적절 한 버전의 MYRES.DLL를 복사 합니다.

리소스 전용 DLL은 비교적 쉽게 만들 수 있습니다. DLL 프로젝트를 만들고를 추가 합니다. RC 파일에 추가 하 고 필요한 리소스를 추가 합니다. 이 기법을 사용 하지 않는 기존 프로젝트가 있는 경우 해당 프로젝트에서 리소스를 복사할 수 있습니다. 리소스 파일을 프로젝트에 추가한 후에는 프로젝트를 빌드할 준비가 거의 되었습니다. **/NOENTRY** 를 포함 하도록 링커 옵션을 설정 해야 합니다. 이렇게 하면 DLL에 진입점이 없음을 링커에 지시할 수 있습니다. 여기에는 코드가 없기 때문에 진입점이 없습니다.

> [!NOTE]
> Visual C++ 4.0 이상에서 리소스 편집기는 당 여러 언어를 지원 합니다. RC 파일. 이를 통해 단일 프로젝트에서 지역화를 매우 쉽게 관리할 수 있습니다. 각 언어에 대 한 리소스는 리소스 편집기에 의해 생성 된 전처리기 지시문에 의해 제어 됩니다.

## <a name="using-the-provided-mfc-localized-resources"></a>제공 된 MFC 지역화 된 리소스 사용

작성 하는 모든 MFC 응용 프로그램은 MFC의 두 가지 코드, 코드 및 리소스를 다시 사용할 수 있습니다. 즉, MFC에는 다양 한 오류 메시지, 기본 제공 대화 상자 및 MFC 클래스에서 사용 하는 기타 리소스가 있습니다. 응용 프로그램을 완전히 지역화 하기 위해 응용 프로그램의 리소스 뿐만 아니라 MFC에서 직접 제공 되는 리소스도 지역화 해야 합니다. MFC는 다양 한 언어 리소스 파일을 자동으로 제공 하므로 대상 언어가 MFC에서 이미 지 원하는 언어 중 하나인 경우 지역화 된 리소스를 사용 하 고 있는지 확인 해야 합니다.

이 문서를 작성할 당시에는 MFC가 중국어, 독일어, 스페인어, 프랑스어, 이탈리아어, 일본어 및 한국어를 지원 합니다. 이러한 지역화 된 버전을 포함 하는 파일은 MFC\INCLUDE\L. *에 있습니다 (' L '은 지역화 된 디렉터리를 나타냄). 예를 들어 독일어 파일은 MFC\INCLUDE\L.DEU에 있습니다. 응용 프로그램에서 MFC\INCLUDE에 있는 파일 대신 이러한 RC 파일을 사용 하도록 하려면 RC 명령줄에를 추가 합니다 .이는 한 가지 방법입니다. 원하는 로캘을 사용 하 여 `/IC:\PROGRAM FILES\MICROSOFT VISUAL STUDIO .NET 2003\VC7\MFC\INCLUDE\L.DEU` Visual C++ 설치 된 디렉터리를 대체 해야 합니다.

응용 프로그램이 정적으로 MFC에 연결 되는 경우 위의 지침이 작동 합니다. 대부분의 응용 프로그램은 동적으로 연결 됩니다 (응용 프로그램의 기본값). 이 시나리오에서는 코드를 동적으로 연결 하는 것이 아니라 리소스입니다. 결과적으로 응용 프로그램에서 리소스를 지역화할 수 있지만 MFC 구현 리소스는 아직 MFC7x.DLL (이상 버전)에서 로드 되거나 존재 하는 경우 MFC7xLOC.DLL에서 로드 됩니다. 서로 다른 두 각도에서이를 사용할 수 있습니다.

더 복잡 한 방법은 지역화 된 MFC7xLOC.DLLs (예: 독일어, 스페인어 용 MFC7xESP.DLL 등) 또는 이후 버전 중 하나를 제공 하 고 사용자가 응용 프로그램을 설치할 때 시스템 디렉터리에 적절 한 MFC7xLOC.DLL을 설치 하는 것입니다. 이는 개발자와 최종 사용자 모두에 게 매우 복잡할 수 있으므로 권장 되지 않습니다. 이 기술 및 해당 주의 사항에 대 한 자세한 내용은 [Technical Note 56](../mfc/tn056-installation-of-localized-mfc-components.md) 을 참조 하세요.

가장 간단 하 고 안전한 방법은 지역화 된 MFC 리소스를 응용 프로그램 또는 DLL 자체 (또는 사용 중인 경우 위성 DLL)에 포함 하는 것입니다. 이렇게 하면 MFC7xLOC.DLL을 제대로 설치 하지 않아도 됩니다. 이렇게 하려면 `/D_AFXDLL` 응용 프로그램 마법사에 의해 추가 된 정의도 제거 해야 한다는 점을 제외 하 고 위에 지정 된 정적 사례에 대 한 동일한 지침을 따릅니다 (RC 명령줄을 제대로 설정). `/D_AFXDLL`가 정의 되 면 afxres.h를 지정 합니다. H (및 다른 MFC RC 파일)는 실제로 리소스를 정의 하지 않습니다 (대신 MFC Dll에서 가져오기 때문).

## <a name="see-also"></a>참고 항목

[번호로 기술 참고 사항](../mfc/technical-notes-by-number.md)<br/>
[범주별 기술 참고 사항](../mfc/technical-notes-by-category.md)
