---
description: '자세히 알아보기: 관리 되는 리소스 속성 페이지'
title: 관리되는 리소스 속성 페이지
ms.date: 08/28/2019
f1_keywords:
- VC.Project.VCManagedResourceCompilerTool.ResourceFileName
- VC.Project.VCManagedResourceCompilerTool.OutputFileName
- VC.Project.VCManagedResourceCompilerTool.DefaultLocalizedResources
helpviewer_keywords:
- Managed Resources property page
ms.assetid: 80b80384-ee55-494d-9f0e-907bb98cfc19
ms.openlocfilehash: 42816e2b4625bc5ab4620f4caafb627f55bd9cd5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97190720"
---
# <a name="managed-resources-property-page"></a>관리되는 리소스 속성 페이지

**관리 되는 리소스** 속성 페이지는 c + +/cli 프로그램에서 .net 리소스를 사용 하는 경우 관리 되는 리소스 컴파일러 [resgen.exe](/dotnet/framework/tools/resgen-exe-resource-file-generator) 에 대 한 다음 속성을 노출 합니다.

- **리소스 논리적 이름**

   생성된 중간 .resources 파일의 *논리적 이름* 을 지정합니다. 논리적 이름은 리소스를 로드하는 데 사용되는 이름입니다. 논리적 이름이 지정되지 않는 경우 리소스(.resx) 파일 이름이 논리적 이름으로 사용됩니다.

- **출력 파일 이름**

   리소스(.resx) 파일이 적용되는 최종 출력 파일 이름을 지정합니다.

- **기본 지역화 리소스**

   기존 .resx 파일이 기본 리소스 또는 위성 .dll에 적용되는지 여부를 지정합니다.

**관리 되는 리소스** 속성 페이지에 액세스 하는 방법에 대 한 자세한 내용은 [Visual Studio에서 c + + 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조 하세요.

## <a name="see-also"></a>참고 항목

[RC(RC 명령줄) 사용](/windows/win32/menurc/using-rc-the-rc-command-line-)<br>
[C++ 프로젝트 속성 페이지 참조](property-pages-visual-cpp.md)<br>
[/ASSEMBLYRESOURCE (관리 되는 리소스 포함)](assemblyresource-embed-a-managed-resource.md)
