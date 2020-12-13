---
description: '자세한 정보: Windows 공용 컨트롤에 대 한 빌드 요구 사항'
title: Windows 공용 컨트롤에 대 한 빌드 요구 사항
ms.date: 08/19/2019
helpviewer_keywords:
- Common Controls (MFC), build requirements
- Common Controls (MFC)
ms.assetid: 025f7d55-55a2-4dcd-8f62-02424e3dcc04
ms.openlocfilehash: 4d11b4da2fb1ff616ab077390c2d603e76382313
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97339802"
---
# <a name="build-requirements-for-windows-common-controls"></a>Windows 공용 컨트롤에 대 한 빌드 요구 사항

MFC (Microsoft Foundation Class) 라이브러리는 [Windows 공용 컨트롤](/windows/win32/controls/common-controls-intro)을 지원 합니다. 공용 컨트롤은 Windows에 포함 되어 있으며 라이브러리는 Visual Studio에 포함 되어 있습니다. MFC 라이브러리는 기존 클래스를 향상 시키는 새로운 메서드와 Windows 공용 컨트롤을 지 원하는 추가 클래스 및 메서드를 제공 합니다. 애플리케이션을 빌드할 때는 다음 섹션에 설명된 컴파일 및 마이그레이션 요구 사항을 따라야 합니다.

## <a name="compilation-requirements"></a>컴파일 요구 사항

### <a name="supported-versions"></a>지원되는 버전

MFC는 모든 버전의 공용 컨트롤을 지원 합니다. Windows 공용 컨트롤 버전에 대 한 자세한 내용은 [공용 컨트롤 버전](/windows/win32/controls/common-control-versions)을 참조 하세요.

### <a name="supported-character-sets"></a>지원되는 문자 집합

Windows 공용 컨트롤은 ANSI 문자 집합이 아닌 유니코드 문자 집합만 지원 합니다. 명령 줄에서 애플리케이션을 빌드할 때는 다음 정의 컴파일러 옵션(/D)을 모두 사용해서 기본 문자 집합으로 유니코드를 지정합니다.

```
/D_UNICODE /DUNICODE
```

Visual Studio IDE (통합 개발 환경)에서 응용 프로그램을 빌드하는 경우 프로젝트 속성의 **일반** 노드에서 **문자 집합** 속성의 **유니코드 문자 집합** 옵션을 지정 합니다.

## <a name="migration-requirements"></a>마이그레이션 요구 사항

Visual Studio IDE를 사용 하 여 Windows 공용 컨트롤을 사용 하는 새 MFC 응용 프로그램을 빌드하는 경우 IDE에서 적절 한 매니페스트를 자동으로 선언 합니다. 그러나 Visual Studio 2005 이전 버전에서 기존 MFC 응용 프로그램을 마이그레이션하는 경우 공용 컨트롤을 사용 하려면 IDE에서 응용 프로그램을 업그레이드 하기 위한 매니페스트 정보를 자동으로 제공 하지 않습니다. 대신, 미리 컴파일된 헤더 파일에 다음 소스 코드를 수동으로 삽입 해야 합니다.

```
#ifdef UNICODE
#if defined _M_IX86
#pragma comment(linker,"/manifestdependency:\"type='win32' name='Microsoft.Windows.Common-Controls' version='6.0.0.0' processorArchitecture='x86' publicKeyToken='6595b64144ccf1df' language='*'\"")
#elif defined _M_IA64
#pragma comment(linker,"/manifestdependency:\"type='win32' name='Microsoft.Windows.Common-Controls' version='6.0.0.0' processorArchitecture='ia64' publicKeyToken='6595b64144ccf1df' language='*'\"")
#elif defined _M_X64
#pragma comment(linker,"/manifestdependency:\"type='win32' name='Microsoft.Windows.Common-Controls' version='6.0.0.0' processorArchitecture='amd64' publicKeyToken='6595b64144ccf1df' language='*'\"")
#else
#pragma comment(linker,"/manifestdependency:\"type='win32' name='Microsoft.Windows.Common-Controls' version='6.0.0.0' processorArchitecture='*' publicKeyToken='6595b64144ccf1df' language='*'\"")
#endif
#endif
```

## <a name="see-also"></a>참고 항목

[일반 MFC 항목](general-mfc-topics.md)<br/>
[계층 구조 차트](hierarchy-chart.md)<br/>
[사용되지 않는 ANSI API](deprecated-ansi-apis.md)
