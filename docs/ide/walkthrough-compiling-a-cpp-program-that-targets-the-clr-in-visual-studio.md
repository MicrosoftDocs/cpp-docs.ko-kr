---
title: CLR을 대상으로 하는 C++ 프로그램 컴파일 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- command-line applications [C++], managed code
- compiling programs [C++]
- Visual C++, managed code
- managed code [C++]
ms.assetid: 339f89df-a5d2-4040-831a-ddbe25b5dce4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d2a7bcb0eead62730f0b70b0b1df64e5ed08f1f0
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33336097"
---
# <a name="walkthrough-compiling-a-c-program-that-targets-the-clr-in-visual-studio"></a>연습: Visual Studio에서 CLR을 대상으로 하는 C++ 프로그램 컴파일
Visual Studio 개발 환경을 사용하여 .NET 클래스를 사용하고 컴파일하는 Visual C++ 프로그램을 만들 수 있습니다.  
  
 이 프로시저의 경우 고유한 Visual C++ 프로그램을 입력하거나 샘플 프로그램 중 하나를 사용할 수 있습니다. 이 프로시저에서 사용하는 샘플 프로그램은 textfile.txt라는 텍스트 파일을 만들고 프로젝트 디렉터리에 저장합니다.  
  
## <a name="prerequisites"></a>전제 조건  
 이러한 항목에서는 사용자가 C++ 언어의 기본적인 사항을 알고 있는 것으로 가정합니다.  
  
### <a name="to-create-a-new-project-in-visual-studio-and-add-a-new-source-file"></a>Visual Studio에서 새 프로젝트를 만들고 새 원본 파일을 추가하려면  
  
1.  새 프로젝트를 만듭니다. **파일** 메뉴에서 **새로 만들기**를 가리킨 다음 **프로젝트**를 클릭합니다.  
  
2.  Visual C++ 프로젝트 형식에서 **CLR**을 클릭한 다음, **CLR 빈 프로젝트**를 클릭합니다.  
  
3.  프로젝트 이름을 입력합니다.  
  
     기본적으로 프로젝트를 포함하는 솔루션에는 새 프로젝트와 동일한 이름이 있지만 다른 이름을 입력할 수 있습니다. 원하는 경우 프로젝트에 다른 위치를 입력할 수 있습니다.  
  
     **확인**을 클릭하여 새 프로젝트를 만듭니다.  
  
4.  솔루션 탐색기가 보이지 않으면 **보기** 메뉴에서 **솔루션 탐색기**를 클릭합니다.  
  
5.  프로젝트에 새 원본 파일을 추가합니다.  
  
    -   솔루션 탐색기에서 **원본 파일** 폴더를 마우스 오른쪽 단추로 클릭하고, **추가**를 가리키고, **새 항목**을 클릭합니다.  
  
    -   **C++ 파일(.cpp)** 을 클릭하고, 파일 이름을 입력한 다음, **추가**를 클릭합니다.  
  
     **.cpp** 파일은 솔루션 탐색기의 **원본 파일** 폴더에 나타나고, 탭된 창은 해당 파일에 원하는 코드를 입력한 위치에 나타납니다.  
  
6.  Visual Studio에서 새로 만든 탭을 클릭하고, 유효한 Visual C++ 프로그램을 입력하거나 샘플 프로그램 중 하나를 복사하고 붙여넣습니다.  
  
     예를 들어 프로그래밍 가이드의 **파일 처리 및 I/O** 노드에서 [방법: 텍스트 파일 쓰기(C++/CLI)](../dotnet/how-to-write-a-text-file-cpp-cli.md) 샘플 프로그램을 사용할 수 있습니다.  
  
     샘플 프로그램을 사용하는 경우 .NET 개체를 만들 때 `new` 대신 `gcnew` 키워드를 사용하고 `gcnew`는 포인터(`*`) 대신 핸들(`^`)을 반환합니다.  
  
     `StreamWriter^ sw = gcnew StreamWriter(fileName);`  
  
     새로운 Visual C++ 구문에 대한 자세한 내용은 [런타임 플랫폼의 구성 요소 확장](../windows/component-extensions-for-runtime-platforms.md)을 참조하세요.  
  
7.  **빌드** 메뉴에서 **솔루션 빌드**를 클릭합니다.  
  
     **출력** 창은 빌드 로그의 위치 및 빌드 상태를 나타내는 메시지와 같은 컴파일 진행 상황에 대한 정보를 표시합니다.  
  
     빌드 작업을 수행하지 않고 프로그램을 변경하고 실행하는 경우 대화 상자는 프로젝트가 만료되었다고 표시할 수 있습니다. Visual Studio가 항상 최신 버전의 파일을 사용하도록 하려면 응용 프로그램을 빌드할 때마다 메시지를 표시하는 대신 **확인**을 클릭하기 전에 이 대화 상자에서 확인란을 선택합니다.  
  
8.  **디버그** 메뉴에서 **디버깅하지 않고 시작**을 클릭합니다.  
  
9. 샘플 프로그램을 사용한 경우 프로그램을 실행할 때 텍스트 파일이 만들어졌는지 여부를 나타내는 명령 창이 표시됩니다. 명령 창을 닫으려면 아무 키나 누릅니다.  
  
     **textfile.txt** 텍스트 파일은 이제 프로젝트 디렉터리에 위치합니다. 메모장을 사용하여 이 파일을 열 수 있습니다.  
  
    > [!NOTE]
    >  빈 CLR 템플릿을 자동으로 선택하면 **/clr** 컴파일러 옵션을 설정합니다. 이를 확인하려면 **솔루션 탐색기**에서 프로젝트를 마우스 오른쪽 단추로 클릭하고, **속성**을 클릭한 다음, **구성 속성**의 **일반** 노드에서 **공용 언어 런타임 지원** 옵션을 선택합니다.  
  
## <a name="whats-next"></a>새로운 기능  
 **이전:** [연습: 명령줄에서 네이티브 C++ 프로그램 컴파일](../build/walkthrough-compiling-a-native-cpp-program-on-the-command-line.md) &#124; **다음:**[연습: 명령줄에서 C 프로그램 컴파일](../build/walkthrough-compile-a-c-program-on-the-command-line.md)  
  
## <a name="see-also"></a>참고 항목  
 [C++ 언어 참조](../cpp/cpp-language-reference.md)   
 [C/C++ 프로그램 빌드](../build/building-c-cpp-programs.md)