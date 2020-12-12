---
description: '자세한 정보: 병합 모듈을 사용 하 여 구성 요소 재배포'
title: 병합 모듈을 사용하여 구성 요소 재배포
ms.date: 11/04/2016
helpviewer_keywords:
- merge modules, using
- redistributing applications, using merge modules
ms.assetid: 93b84211-bf9b-4a78-9f22-474ac2ef7840
ms.openlocfilehash: ecfc2904be7451c96226e91ed8e7f98d565d35ac
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97179904"
---
# <a name="redistributing-components-by-using-merge-modules"></a>병합 모듈을 사용하여 구성 요소 재배포

Visual Studio에는 애플리케이션으로 재배포할 권한이 있는 각 Visual C++ 구성 요소에 대한 [병합 모듈](/windows/win32/Msi/about-merge-modules)이 포함됩니다. 병합 모듈이 Windows Installer 설치 파일에서 컴파일되면 특정 플랫폼이 있는 컴퓨터에 특정 DLL을 배포할 수 있습니다. 설치 파일에서 병합 모듈을 애플리케이션의 필수 구성 요소로 지정합니다. Visual Studio가 설치되면 병합 모듈이 \Program Files\Common Files\Merge Modules\\\에 설치됩니다. Visual C++ Dll의 디버그가 아닌 버전만 재배포할 수 있습니다. 재배포에 사용이 허가 된 병합 모듈의 목록에 대 한 자세한 내용 및 링크는 [Visual C++ 파일 재배포](redistributing-visual-cpp-files.md)를 참조 하세요.

병합 모듈을 사용하여 재배포 가능 Visual C++ DLL을 %SYSTEMROOT%\system32\ 폴더에 설치할 수 있습니다. Visual Studio 자체에서는이 기법을 사용 합니다. 그러나 설치 하는 사용자에 게 관리자 권한이 없는 경우에는이 폴더에 대 한 설치가 실패 합니다.

애플리케이션을 제공할 필요가 없고 둘 이상의 DLL 버전에 대한 종속성이 없는 경우를 제외하고 병합 모듈을 사용하지 않는 것이 좋습니다. 동일한 DLL의 여러 버전에 대한 병합 모듈은 하나의 설치 관리자에 포함될 수 없고 병합 모듈은 애플리케이션에 관계없이 DLL을 제공하기 어렵습니다. 대신에 Visual C++ 재배포 가능 패키지를 설치하는 것이 좋습니다.

## <a name="see-also"></a>참고 항목

[Visual C++ 파일 재배포](redistributing-visual-cpp-files.md)
