---
title: '방법: 빌드할 프로젝트 출력 파일 구성 | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Visual C++, output files
- output files, organizing
ms.assetid: 521d95ea-2dcc-4da0-b5eb-ac3e57941446
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5058493e93a89e64c87ef52b73ff8fe3272f8f99
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34705347"
---
# <a name="how-to-organize-project-output-files-for-builds"></a>방법: 빌드할 프로젝트 출력 파일 구성
이 항목에서는 프로젝트 출력 파일을 구성하는 모범 사례를 설명합니다. 프로젝트 출력 파일을 잘못 설정하는 경우 빌드 오류가 발생할 수 있습니다. 이 항목에서는 프로젝트 출력 파일을 구성하는 각 대안의 장단점도 간략하게 설명합니다.  
  
## <a name="referencing-clr-assemblies"></a>CLR 어셈블리 참조  
  
#### <a name="to-reference-assemblies-with-using"></a>#using에서 어셈블리를 참조하려면  
  
1.  #using 지시문을 사용하여 코드에서 직접 어셈블리를 참조할 수 있습니다(예: `#using <System.Data.dll>`). 자세한 내용은 [#using 지시문](../preprocessor/hash-using-directive-cpp.md)을 참조하세요.  
  
     지정된 파일이 MSIL에 위치하면 .dll, .exe, .netmodule 또는 .obj일 수 있습니다. 참조된 구성 요소는 임의의 언어로 빌드될 수 있습니다. 이 옵션을 사용하면 메타데이터를 MSIL에서 추출하므로 IntelliSense에 대한 액세스 권한이 있습니다. 해당 파일은 프로젝트의 경로에 있어야 합니다. 그렇지 않으면 프로젝트가 컴파일되지 않고 IntelliSense가 지원되지 않습니다. 파일이 경로에 있는지 확인하는 쉬운 방법은 #using 줄을 마우스 오른쪽 단추로 클릭하고, **문서 열기** 명령을 선택하는 것입니다. 파일을 찾을 수 없는 경우 알림이 표시됩니다.  
  
     파일에 전체 경로를 저장하지 않으려는 경우 **/AI** 컴파일러 옵션을 사용하여 #using 참조에 대한 검색 경로를 편집할 수 있습니다. 자세한 내용은 [/AI(메타데이터 디렉터리 지정)](../build/reference/ai-specify-metadata-directories.md)를 참조하세요.  
  
#### <a name="to-reference-assemblies-with-fu"></a>/FU에서 어셈블리를 참조하려면  
  
1.  위에서 설명한 대로 코드 파일에서 직접 어셈블리를 참조하는 대신 **/FU** 컴파일러 옵션을 사용할 수 있습니다. 이 방법의 장점은 별도의 #using 문을 지정된 어셈블리를 참조하는 모든 파일에 추가할 필요가 없다는 것입니다.  
  
     이 옵션을 설정하려면 프로젝트의 **속성 페이지**를 엽니다. **구성 속성** 노드를 확장한 다음, **C/C++** 노드를 확장하고 **고급**을 선택합니다. **#using 적용** 옆에 원하는 어셈블리를 추가합니다. 자세한 내용은 [/FU(강제 #using 파일 이름 지정)](../build/reference/fu-name-forced-hash-using-file.md)를 참조하세요.  
  
#### <a name="to-reference-assemblies-with-add-new-reference"></a>새 참조 추가에서 어셈블리를 참조하려면  
  
1.  CLR 어셈블리를 사용하는 가장 쉬운 방법은 다음과 같습니다. 첫째 프로젝트가 **/clr** 컴파일러 옵션을 사용하여 컴파일되었는지 확인합니다. 그런 다음, **솔루션 탐색기**에서 프로젝트를 마우스 오른쪽 단추로 클릭하고, **추가**, **참조**를 선택합니다. **속성 페이지** 대화 상자가 나타납니다.  
  
2.  **속성 페이지** 대화 상자에서 **새 참조 추가**를 선택합니다. 모든 .NET, COM 및 현재 프로젝트에서 사용할 수 있는 기타 어셈블리를 나열하는 대화 상자가 표시됩니다. 원하는 어셈블리를 선택하고 **확인**을 클릭합니다.  
  
     프로젝트 참조를 설정하면 해당하는 종속성은 자동으로 처리됩니다. 또한 메타데이터가 어셈블리의 일부이므로 관리 어셈블리에서 사용되는 헤더 파일을 추가하거나 요소를 프로토타입으로 사용할 필요가 없습니다.  
  
## <a name="referencing-native-dlls-or-static-libraries"></a>네이티브 DLL 또는 고정 라이브러리 참조  
  
#### <a name="to-reference-native-dlls-or-static-libraries"></a>네이티브 DLL 또는 고정 라이브러리를 참조하려면  
  
1.  #include 지시문을 사용하여 코드에서 적절한 헤더 파일을 참조합니다. 헤더 파일은 include 경로에 위치하거나 현재 프로젝트의 일부여야 합니다. 자세한 내용은 [#include 지시문(C/C++)](../preprocessor/hash-include-directive-c-cpp.md)을 참조하세요.  
  
2.  프로젝트 종속성을 설정할 수도 있습니다. 프로젝트 종속성을 설정하면 다음 두 가지를 보장합니다. 먼저 프로젝트가 필요한 종속 파일을 항상 찾을 수 있도록 프로젝트를 적절한 순서로 빌드하는지 확인합니다. 둘째, 링크 타임 시 파일을 쉽게 찾을 수 있도록 종속 프로젝트의 출력 디렉터리를 경로에 암시적으로 추가합니다.  
  
3.  응용 프로그램을 배포하려면 DLL을 적절한 위치에 배치해야 합니다. 다음 중 하나일 수 있습니다.  
  
    1.  실행 파일과 동일한 경로  
  
    2.  시스템 경로의 모든 위치(**경로** 환경 변수)  
  
    3.  병렬 어셈블리 내부 자세한 내용은 [C/C++ 병렬 어셈블리 빌드](../build/building-c-cpp-side-by-side-assemblies.md)를 참조하세요.  
  
## <a name="working-with-multiple-projects"></a>여러 프로젝트 사용  
 기본적으로 프로젝트가 빌드되면 모든 출력 파일이 프로젝트 디렉터리의 하위 디렉터리에서 생성됩니다. 빌드 구성에 따라 디렉터리의 이름이 지정됩니다(예: 디버그 또는 릴리스). 형제 프로젝트의 상호 참조의 경우 각 프로젝트는 성공적으로 연결하기 위해 다른 프로젝트 출력 디렉터리를 해당 경로에 명시적으로 추가해야 합니다. 이 작업은 프로젝트 종속성을 설정할 때 자동으로 수행됩니다. 그러나 종속성을 사용하지 않는 경우 이 빌드를 관리하기 매우 어려울 수 있기 때문에 신중하게 처리해야 합니다. 예를 들어 프로젝트가 디버그 및 릴리스 구성을 포함하고 형제 프로젝트의 외부 라이브러리를 포함하는 경우 빌드 중인 구성에 따라 다른 라이브러리 파일을 사용해야 합니다. 따라서 이러한 경로를 하드 코딩하는 작업은 까다로울 수 있습니다.  
  
 모든 필수 출력 파일(예: 실행 파일, 증분 링커 파일 및 PDB 파일)은 일반적인 솔루션 디렉터리로 복사됩니다. 따라서 동일한 구성을 가진 많은 C++ 프로젝트를 포함하는 솔루션을 사용할 때 모든 출력 파일은 간소화된 연결 및 배포를 위해 중앙 집중화됩니다. 해당 파일을 함께 유지하는 경우 파일이 경로에 위치하도록 하므로 해당 응용 프로그램/라이브러리가 예상대로 작동하는지 확인할 수 있습니다.  
  
 프로덕션 환경에 배포하는 경우 출력 파일의 위치는 중요한 문제일 수 있습니다. IDE에서 프로젝트를 실행하는 동안 포함된 라이브러리에 대한 경로는 프로덕션 환경과 동일할 필요가 없습니다. 예를 들어 코드에 `#using "../../lib/debug/mylib.dll"`이 있지만 mylib.dll을 다른 상대적 위치에 배포하는 경우 런타임 시 응용 프로그램이 실패하게 됩니다. 이를 방지하려면 코드의 #include 문에서 상대 경로를 사용하지 않도록 방지해야 합니다. 필요한 파일이 프로젝트 빌드 경로에 있는지 확인하고 마찬가지로 해당 프로덕션 파일이 제대로 배치되었는지 확인하는 것이 좋습니다.  
  
#### <a name="how-to-specify-where-output-files-go"></a>출력 파일의 위치를 지정하는 방법  
  
1.  프로젝트 출력 설정의 위치는 프로젝트의 **속성 페이지**에서 찾을 수 있습니다. **구성 속성** 옆에 있는 노드를 확장하고, **일반**을 선택합니다. 출력 위치는 **출력 디렉터리** 옆에 지정됩니다. 자세한 내용은 [일반 속성 페이지(프로젝트)](../ide/general-property-page-project.md)를 참조하세요.  
  
## <a name="see-also"></a>참고 항목  
 [Visual C++ 프로젝트 형식](../ide/visual-cpp-project-types.md)