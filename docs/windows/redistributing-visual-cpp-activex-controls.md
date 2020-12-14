---
description: '자세한 정보: ActiveX 컨트롤 Visual C++ 재배포'
title: Visual C++ ActiveX 컨트롤 재배포
ms.date: 11/04/2016
helpviewer_keywords:
- controls [C++], redistributing
- controls [C++], distributing
ms.assetid: eefbb7e4-d28c-4c35-98bf-d9540cfaae83
ms.openlocfilehash: 4960af93b140e883ff50f6ff81824cd9e67d44f6
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97247347"
---
# <a name="redistributing-visual-c-activex-controls"></a>Visual C++ ActiveX 컨트롤 재배포

Visual C++ 6.0은 다시 배포할 애플리케이션에서 사용할 수 있는 ActiveX 컨트롤을 제공합니다. 이러한 컨트롤은 더 이상 Visual C++에 포함되지 않습니다. Visual C++ 6.0에 대한 사용권 계약에 따라 Visual C++에서 개발된 애플리케이션으로 이러한 컨트롤을 재배포할 수 있습니다.

> [!NOTE]
> Visual C++ 6.0은 Microsoft에서 더 이상 지원하지 않습니다.

재배포 가능 Visual C++ 6.0 ActiveX 컨트롤 목록은 Visual C++ 6.0 제품 CD의 디스크 1에 있는 Common\Redist\Redist.txt를 참조하세요.

애플리케이션을 배포할 때는 ActiveX 컨트롤용 .ocx를 설치하고 등록해야 합니다(Regsvr32.exe 사용). 또한 대상 컴퓨터에 다음 시스템 파일의 최신 버전이 있는지 확인해야 합니다(별표는 파일을 등록해야 함을 나타냄).

- Asycfilt.dll

- Comcat.dll \*

- Oleaut32.dll \*

- Olepro32.dll \*

- Stdole2.tlb

이러한 DLL을 대상 시스템에서 사용할 수 없는 경우 해당 운영 체제를 업데이트하기 위해 미리 지정된 메커니즘을 사용하여 해당 DLL을 업데이트해야 합니다. 에서 Windows 운영 체제의 최신 서비스 팩을 다운로드할 수 있습니다 [http://windowsupdate.microsoft.com](https://windowsupdate.microsoft.com) .

데이터베이스에 연결하는 ActiveX 컨트롤을 사용하는 경우 대상 컴퓨터에서 데이터 원본 이름도 복제해야 합니다. 이 작업은 `ConfigDSN`과 같은 함수를 사용하여 프로그래밍 방식으로 수행할 수 있습니다.

재배포 가능한 일부 ActiveX 컨트롤에는 추가 종속성이 있습니다. Visual C++ 6.0 제품 CD의 Os\System 폴더에 있는 각 .ocx 파일에는 .dep 파일도 있습니다. 재배포할 각.ocx 파일의 해당 .dep 파일에서 하나 이상의 USES 항목을 찾습니다. 파일이 나열된 경우 파일이 대상 컴퓨터에 있는지 확인해야 합니다. .ocx 파일을 직접 지원하는 모든 DLL을 등록해야 합니다. Regsvr32.exe 성공 하려면 먼저 컨트롤이 정적으로 로드 하는 모든 Dll이 대상 컴퓨터에 포함 되어 있어야 합니다. 또한 종속성으로 나열 된 DLL에 Visual C++ 6.0 CD의 Os\System 폴더에 있는 dep 파일이 있는 경우의 dep 파일도 사용 항목을 조사 해야 합니다.

## <a name="see-also"></a>참고 항목

[Visual C++ 파일 재배포](redistributing-visual-cpp-files.md)
