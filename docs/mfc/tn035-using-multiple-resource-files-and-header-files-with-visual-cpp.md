---
description: '자세히 알아보기: TN035: 여러 리소스 파일 및 헤더 파일을 사용 하 여 Visual C++'
title: 'TN035: Visual C++에서 여러 개의 리소스 파일 및 헤더 파일 사용'
ms.date: 11/04/2016
f1_keywords:
- vc.resources
helpviewer_keywords:
- resource files, multiple
- TN035
ms.assetid: 1f08ce5e-a912-44cc-ac56-7dd93ad73fb6
ms.openlocfilehash: 347c816040d6e20cd9b7ee01f07662066981b8aa
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97215471"
---
# <a name="tn035-using-multiple-resource-files-and-header-files-with-visual-c"></a>TN035: Visual C++에서 여러 개의 리소스 파일 및 헤더 파일 사용

> [!NOTE]
> 다음 기술 노트는 온라인 설명서에 먼저 포함되어 있었으므로 업데이트되지 않았습니다. 따라서 일부 절차 및 항목은 만료되거나 올바르지 않을 수 있습니다. 최신 정보를 보려면 온라인 설명서 색인에서 관심 있는 항목을 검색하는 것이 좋습니다.

이 노트는 단일 프로젝트 또는 여러 프로젝트에서 공유되는 Visual C++ 리소스 편집기에서 여러 리소스 파일과 헤더 파일을 지원하는 방식과 이러한 지용을 활용하는 방법에 대해 설명합니다. 이 노트는 다음 질문에 대한 답변을 제공합니다.

- 프로젝트를 여러 리소스 파일 및/또는 헤더 파일에 분할 하 고 수행 하는 방법을 확인할 수 있는 경우

- 공용 헤더를 공유 하는 방법 두 사이의 H 파일입니다. RC 파일

- 프로젝트 리소스를 여러 개로 나누는 방법 RC 파일

- (및 도구)는 간의 빌드 종속성을 관리 하는 방법입니다. RC,. CPP, 및 H 파일

프로젝트에 리소스 파일을 추가하는 경우 클래스 마법사는 추가된 파일의 리소스를 인식하지 못합니다.

이 노트는 다음과 같은 구성으로 위의 질문에 대한 답변을 제공합니다.

- **리소스 파일 및 헤더 파일을 Visual C++ 관리 하는 방법에 대 한** 개요에서는 리소스 집합의 명령을 사용 하 여 동일한 프로젝트에서 여러 리소스 파일 및 헤더 파일을 사용할 수 있도록 하는 방법에 대 한 개요를 제공 Visual C++.

- **응용 프로그램 마법사를 분석 하 여 만들었습니다. RC 및 H 파일** 은 응용 프로그램 마법사가 만든 응용 프로그램에서 사용 하는 여러 리소스 및 헤더 파일을 살펴봅니다. 이러한 파일은 프로젝트에 추가할 추가 리소스 파일 및 헤더 파일의 좋은 모델이 됩니다.

- **추가 헤더 파일을 포함 하 여** 여러 헤더 파일을 포함할 수 있는 위치를 설명 하 고이 작업을 수행 하는 방법에 대해 자세히 설명 합니다.

- **두 파일 간에 헤더 파일을 공유 합니다. RC 파일** 은 여러에서 하나의 헤더 파일을 공유 하는 방법을 보여 줍니다. 다른 프로젝트의 RC 파일 또는 동일한 프로젝트에 있습니다.

- **동일한 프로젝트에서 여러 리소스 파일을 사용 하는** 경우 프로젝트를 여러 개로 분할할 수 있는 위치에 대해 설명 합니다. RC 파일 및이 작업을 수행 하는 방법에 대해 자세히 설명 합니다.

- **편집할 수 없는 Visual C++ 파일을 적용** 하면 Visual C++에서 사용자 지정 리소스를 편집 하 고 실수로 다시 포맷 하지 않도록 하는 방법에 대해 설명 합니다.

- **여러 Visual C++ 편집에서 공유 하는 기호 관리 RC 파일** 은 여러에서 동일한 기호를 공유 하는 방법을 설명 합니다. RC 파일 및 중복 ID 숫자 값 할당을 방지 하는 방법

- **간의 종속성을 관리 하는 중입니다. RC,. CPP, 및 H 파일** Visual C++ 불필요 한 다시 컴파일 방지 방법을 설명 합니다. 리소스 기호 파일에 종속 된 CPP 파일입니다.

- **Visual C++ 관리 집합에 포함 되는 방법** 에는 Visual C++ 여러 (중첩 된)를 추적 하는 방법에 대 한 기술 정보가 포함 됩니다. 에서 #include 된 RC 파일 및 여러 헤더 파일 RC 파일.

## <a name="overview-of-how-visual-c-manages-resource-files-and-header-files"></a>Visual C++에서 리소스 파일 및 헤더 파일을 관리하는 방법 개요

Visual C++는 단일 .RC 리소스 파일과 해당하는 .H 헤더 파일을 밀접하게 결합된 파일 쌍으로 관리합니다. .RC 파일에서 리소스를 편집하고 저장하면 해당하는 .H 파일의 기호도 간접적으로 편집하고 저장하게 됩니다. (Visual C++의 MDI 사용자 인터페이스를 사용하여) 한 번에 여러 .RC 파일을 열고 편집할 수 있지만 지정된 .RC 파일에 대해 해당하는 헤더 파일 하나만 간접적으로 편집할 수 있습니다.

### <a name="symbol-header-file"></a>기호 헤더 파일

기본적으로 Visual C++에서는 리소스 파일의 이름(예: MYAPP.RC)과 관계없이 해당하는 헤더 파일의 이름을 RESOURCE.H로 지정합니다. Visual C++의 **보기** 메뉴에 있는 **리소스 내용** 명령을 사용 하 여 **집합 포함** 대화 상자에서 기호 헤더 파일 파일을 업데이트 하 여이 헤더 파일의 이름을 변경할 수 있습니다.

### <a name="read-only-symbol-directives"></a>읽기 전용 기호 지시문

Visual C++에서는 지정된 .RC 파일에 대해 헤더 파일 하나만 편집하지만, 추가 읽기 전용 헤더 파일에 정의된 기호에 대한 참조를 지원합니다. Visual C++의 **보기** 메뉴에 있는 **리소스 내용** 명령을 사용 하 여 추가 읽기 전용 헤더 파일을 개수에 관계 없이 Read-Only 기호 지시문으로 지정할 수 있습니다. "읽기 전용" 제한은 .RC 파일에 새 리소스를 추가할 경우 읽기 전용 헤더 파일에 정의된 기호를 사용할 수 있지만 리소스를 삭제할 경우 기호가 읽기 전용 헤더 파일에 여전히 정의되어 있음을 의미합니다. 읽기 전용 기호에 할당된 숫자 값은 변경할 수 없습니다.

### <a name="compile-time-directives"></a>컴파일 타임 지시문

Visual C++에서는 .RC 파일이 다른 .RC 파일 안에 #include로 지정되는 리소스 파일 중첩 기능도 지원됩니다. Visual C++를 사용하여 지정된 .RC 파일을 편집할 경우 #include로 지정된 파일의 리소스를 볼 수 없습니다. 하지만 .RC 파일을 컴파일할 때 #include로 지정된 파일도 컴파일됩니다. Visual C++의 **보기** 메뉴에 있는 **리소스 내용** 명령을 사용 하 여 원하는 수의 #include를 지정할 수 있습니다. Compile-Time 지시문으로 RC 파일

Visual C++으로 읽으면 어떻게 되는지 확인 합니다. 다른 #include 하는 RC 파일입니다. Compile-Time 지시문으로 지정 *되지* 않은 RC 파일입니다. 이 상황은 이전에 텍스트 편집기를 사용하여 수동으로 관리해 왔던 .RC 파일을 Visual C++로 가져올 때 발생할 수 있습니다. Visual C++에서 #include로 지정된 .RC 파일을 읽을 때 #include로 지정된 리소스가 부모 .RC 파일에 병합됩니다. 부모 .RC 파일을 저장할 경우 #include 문이 사실상 #include로 지정된 리소스로 대체됩니다. 이러한 병합이 발생 하지 않도록 하려면 부모에서 #include 문을 제거 해야 합니다. Visual C++로 읽기 *전에* RC 파일 그런 다음 Visual C++를 사용 하 여 Compile-Time 지시문과 동일한 #include 문을 다시 추가 합니다.

Visual C++을에 저장 합니다. RC 파일 #include 지시문 *및* textinclude 리소스에는 위의 세 가지 집합에 정보 (기호 헤더 파일, Read-Only 기호 지시문 및 Compile-Time 지시문)가 포함 되어 있습니다. TEXTINCLUDE 리소스의 경우 일반적으로 처리 하지 않아도 되는 구현 세부 [정보는 Visual C++ 관리 집합에 포함 된 정보를 포함 하는 방법](#_mfcnotes_tn035_set_includes)에 설명 되어 있습니다.

## <a name="analysis-of-appwizard-created-rc-and-h-files"></a>응용 프로그램 마법사가 만든 .RC 및 .H 파일 분석

애플리케이션 마법사가 만든 애플리케이션 코드를 살펴보면 Visual C++에서 여러 리소스 파일 및 헤더 파일이 어떻게 관리되는지 파악할 수 있습니다. 아래에서 살펴보는 코드는 애플리케이션 마법사에서 기본 옵션을 사용하여 만든 MYAPP 애플리케이션의 코드를 발췌한 것입니다.

애플리케이션 마법사가 만든 애플리케이션에는 아래 다이어그램에 요약된 것처럼 여러 리소스 파일과 여러 헤더 파일이 사용됩니다.

```Diagram
   RESOURCE.H     AFXRES.H
          \       /
           \     /
          MYAPP.RC
              |
              |
        RES\MYAPP.RC2
        AFXRES.RC
        AFXPRINT.RC
```

Visual C++ 파일/Set Includes 명령을 사용하여 이러한 여러 파일의 관계를 볼 수 있습니다.

MYAPP. 스크립트
Visual C++를 사용하여 편집하는 응용 프로그램 리소스 파일입니다.

RESOURCE.H는 애플리케이션별 헤더 파일입니다. Visual C++의 기본 헤더 파일 명명 규칙에 따라 응용 프로그램 마법사에 의해 항상 RESOURCE.H로 이름이 지정됩니다. 이 헤더 파일의 #include는 이 리소스 파일(MYAPP.RC)의 첫 번째 문입니다.

```rc
//Microsoft Visual C++ generated resource script
//
#include "resource.h"
```

RES\MYAPP. RC2
Visual C++에 의해 편집되지 않지만 최종 컴파일된 .EXE 파일에 포함될 리소스를 포함합니다. Visual C++에서 버전 리소스(이 릴리스의 새로운 기능)를 비롯하여 모든 표준 리소스를 편집할 수 있으므로 응용 프로그램 마법사에서는 기본적으로 이러한 리소스를 만들지 않습니다. 고유의 사용자 지정 서식 리소스를 이 파일에 추가하려는 경우 응용 프로그램 마법사에 의해 빈 파일이 생성됩니다.

사용자 지정 서식 리소스를 사용하는 경우 이러한 리소스를 RES\MYAPP.RC2에 추가하고 Visual C++ 텍스트 편집기를 사용하여 편집할 수 있습니다.

AFXRES.RC 및 AFXPRINT.RC에는 프레임워크의 특정 기능에 필요한 표준 리소스가 포함되어 있습니다. RES\MYAPP.RC2와 마찬가지로, 프레임워크에서 제공한 이러한 두 리소스 파일은 MYAPP.RC 끝에 #include로 지정되며 Set Includes 대화 상자의 컴파일 시간 지시문에 지정됩니다. 따라서 Visual C++에서 MYAPP.RC를 편집하는 동안 이러한 프레임워크 리소스를 직접 보거나 편집하지는 않지만, 이러한 리소스는 애플리케이션의 이진 .RES 파일 및 최종 .EXE 파일로 컴파일됩니다. 표준 프레임 워크 리소스를 수정 하는 절차를 비롯 한 표준 프레임 워크 리소스에 대 한 자세한 내용은 [Technical Note 23](../mfc/tn023-standard-mfc-resources.md)을 참조 하십시오.

AFXRES.H는 프레임워크와 특히 AFXRES.RC에서 사용되는 `ID_FILE_NEW`와 같은 표준 기호를 정의합니다. 또한 AFXRES.H는 Visual C++에서 생성된 .RC 파일과 AFXRES.RC에 필요한 WINDOWS.H의 부분 집합을 포함하는 WINRES.H를 #include로 지정합니다. AFXRES.H에 정의된 기호는 애플리케이션 리소스 파일(MYAPP.RC)을 편집할 때 사용할 수 있습니다. 예를 들면 `ID_FILE_NEW`는 MYAPP.RC의 메뉴 리소스에서 새 파일 메뉴 항목에 사용됩니다. 프레임워크에서 정의된 이러한 기호는 변경하거나 삭제할 수 없습니다.

## <a name="including-additional-header-files"></a><a name="_mfcnotes_tn035_including"></a> 추가 헤더 파일 포함

애플리케이션 마법사에서 생성된 애플리케이션에는 RESOURCE.H와 AFXRES.H라는 두 개 헤더 파일만 포함됩니다. RESOURCE.H는 애플리케이션마다 다릅니다. 다음의 경우에는 추가 읽기 전용 헤더 파일만 포함하면 됩니다.

헤더 파일은 외부 소스에 의해 제공되거나, 여러 프로젝트 또는 동일 프로젝트의 여러 부분 간에 헤더 파일을 공유할 수 있습니다.

헤더 파일에는 저장할 때 Visual C++에서 변경되거나 필터링되지 않아야 할 서식과 주석이 포함되어 있습니다. 예를 들면 다음과 같은 기호화된 산술을 사용하는 #define을 유지해야 하는 경우가 있습니다.

```h
#define RED 0
#define BLUE 1
#define GREEN 2
#define ID_COLOR_BUTTON 1001
#define ID_RED_BUTTON (ID_COLOR_BUTTON + RED)
#define ID_BLUE_BUTTON (ID_COLOR_BUTTON + BLUE)
#define ID_GREEN_BUTTON (ID_COLOR_BUTTON + GREEN)
```

다음과 같이 **리소스 내용** 명령을 사용 하 여 추가 읽기 전용 헤더 파일을 포함 하 여 #include 문을 두 번째 Read-Only 기호 지시문으로 지정할 수 있습니다.

```rc
#include "afxres.h"
#include "second.h"
```

이제 새 파일 관계 다이어그램은 다음과 같습니다.

```Diagram
                   AFXRES.H
    RESOURCE.H     SECOND.H
          \       /
           \     /
          MYAPP.RC
              |
              |
        RES\MYAPP.RC2  
        AFXRES.RC
        AFXPRINT.RC
```

## <a name="sharing-a-header-file-between-two-rc-files"></a>두 .RC 파일 간의 헤더 파일 공유

서로 다른 프로젝트 또는 같은 프로젝트에 있는 두 .RC 파일 간에 헤더 파일을 공유할 수 있습니다. 이렇게 하려면 위에 설명된 읽기 전용 지시문 기술을 두 .RC 파일에 적용하기만 하면 됩니다. 두 .RC 파일이 서로 다른 애플리케이션(서로 다른 프로젝트)의 파일일 경우 다음 다이어그램은 그 결과를 보여 줍니다.

```Diagram
     RESOURCE.H   AFXRES.H   RESOURCE.H  
    (for MYAPP1)  SECOND.H   (for MYAPP2)
          \       /     \       /
           \     /       \     /
          MYAPP1.RC      MYAPP2.RC
           /    \        /     \
          /      \      /       \
RES\MYAPP1.RC2  AFXRES.RC     RES\MYAPP2.RC2
                AFXPRINT.RC
```

동일 애플리케이션(프로젝트)의 두 .RC 파일에서 두 번째 헤더 파일을 공유하는 경우는 아래 설명되어 있습니다.

## <a name="using-multiple-resource-files-in-the-same-project"></a>동일 프로젝트에서 여러 리소스 파일 사용

Visual C++ 및 리소스 컴파일러는 한 .RC 파일 안에 들어 있는 다른 .RC 파일의 #include를 통해 동일한 프로젝트 내에서 여러 .RC 파일을 지원합니다. 다수의 중첩이 허용됩니다. 프로젝트의 리소스를 여러 .RC 파일로 분할하는 데는 여러 가지가 이유가 있습니다.

- 리소스를 여러 .RC 파일로 분할할 경우 여러 프로젝트 팀 멤버 간에 많은 리소스를 보다 쉽게 관리할 수 있습니다. 파일 체크 아웃 및 변경 내용 체크 인용으로 소스 제어 관리 패키지를 사용하는 경우 리소스를 여러 .RC 파일로 분할하면 리소스에 대한 변경 내용을 좀더 세부적으로 제어할 수 있습니다.

- 리소스 부분에 대해 #ifdef, #endif 및 #define 같은 전처리기 지시문을 사용하려는 경우 이러한 전처리기 지시문을 리소스 컴파일러에서 컴파일될 읽기 전용 리소스로 격리해야 합니다.

- Visual C++에서는 구성 요소 .RC 파일이 복합 .RC 파일 하나보다 더 빨리 로드되고 저장됩니다.

- 텍스트 편집기를 사용하여 사람이 읽을 수 있는 형태로 리소스를 관리하려는 경우 .RC 파일을 Visual C++ 편집으로부터 분리된 상태로 유지해야 합니다.

- 사용자 정의 리소스를 다른 전문 데이터 편집기를 통해 해석할 수 있는 이진 또는 텍스트 형태로 유지해야 하는 경우 Visual C++에서 형식을 16진 데이터로 변경하지 않도록 이러한 리소스를 별도의 .RC 파일에 보관해야 합니다. 여. MFC 고급 개념 샘플 [SPEAKN](../overview/visual-cpp-samples.md) 의 WAV (사운드) 파일 리소스는 좋은 예입니다.

Set Includes 대화 상자에서 컴파일 타임 지시문에 SECOND.RC를 #include로 지정할 수 있습니다.

```h
#include "res\myapp.rc2"  // non-Visual C++ edited resources
#include "second.rc"  // THE SECOND .RC FILE

#include "afxres.rc"  // Standard components
#include "afxprint.rc"  // printing/print preview resources
```

다음 다이어그램은 그 결과를 보여 줍니다.

```Diagram
   RESOURCE.H     AFXRES.H
          \       /
           \     /
          MYAPP.RC
              |
              |
        RES\MYAPP.RC2
        SECOND.RC  
        AFXRES.RC
        AFXPRINT.RC
```

컴파일 시간 지시문을 사용하여 Visual C++ 편집할 수 있거나 편집할 수 없는 리소스를 여러 .RC 파일로 구성할 수 있으며, 이 경우 "마스터" MYAPP.RC 파일에서는 다른 .RC 파일을 #include로 지정할 뿐 아무 기능도 수행하지 않습니다. Visual Studio c + + 프로젝트를 사용 하는 경우 MAK 파일의 경우 "master"를 포함 해야 합니다. 응용 프로그램을 사용 하 여 모든 #include 리소스를 컴파일하도록 프로젝트의 RC 파일입니다.

## <a name="enforcement-of-noneditable-visual-c-files"></a>편집할 수 없는 Visual C++ 파일 강제 적용

응용 프로그램 마법사에서 만든 RES\MYAPP. RC2 파일은 실수로 Visual C++으로 읽어 온 다음 서식 정보 손실 없이 다시 작성 *하지* 않으려는 리소스를 포함 하는 파일의 한 예입니다. 이러한 경우가 발생하지 않도록 하기 위해 RES\MYAPP.RC2 파일의 시작 부분에 다음 줄을 추가합니다.

```rc2
#ifdef APSTUDIO_INVOKED
    #error this file is not editable by Visual C++
#endif //APSTUDIO_INVOKED
```

Visual C++에서를 컴파일합니다. RC 파일은 뿐만 아니라도 정의 `APSTUDIO_INVOKED` `RC_INVOKED` 합니다. 응용 프로그램 마법사가 만든 파일 구조가 손상되고 Visual C++에서 위의 #error 줄을 읽고 심각한 오류로 보고한 후 .RC 파일의 읽기를 중단합니다.

## <a name="managing-symbols-shared-by-multiple-visual-c-edited-rc-files"></a>Visual C++에서 편집된 여러 .RC 파일에서 공유하는 기호 관리

리소스를 Visual C++에서 개별적으로 편집하려는 여러 .RC 파일로 분할할 때 두 가지 문제가 발생합니다.

- 여러 .RC 파일 간에 동일한 기호를 공유해야 할 때가 있습니다.

- 개발자는 Visual C++에서 동일한 ID 숫자 값이 개별 리소스(기호)에 할당되지 않도록 해야 합니다.

다음 다이어그램은 첫 번째 문제를 다루는 .RC 및 .H 파일의 구성을 보여 줍니다.

```Diagram
              MYAPP.RC
             /         \
            /           \
MYSTRS.H   / MYSHARED.H  \  MYMENUS.H
     \    /    /      \   \    \
      \  /    /        \   \    \
      MYSTRS.RC         MYMENUS.RC
```

이 예제에서는 문자열 리소스는 리소스 파일, MYSTRS.RC에 저장되고 메뉴는 MYMENUS.RC에서 저장됩니다. 명령과 같은 일부 기호는 두 파일 사이에 공유될 수도 있습니다. 예를 들어, ID_TOOLS_SPELL은 도구 메뉴에서 맞춤법 검사 항목에 대한 메뉴 명령 ID일 수 있으며, 애플리케이션의 기본 창 상태 표시줄에서 프레임워크에 의해 표시되는 명령 프롬프트의 문자열 ID일 수도 있습니다.

ID_TOOLS_SPELL 기호는 공유 헤더 파일이 MYSHARED.H에서 유지됩니다. 이 공유 헤더 파일은 개발자가 텍스트 편집기를 사용하여 직접 관리하며, Visual C++에 의해 직접 편집되지 않습니다. 두 리소스 파일 MYSTRS. RC 및 MYMENUS RC를 #include MYSHARED를 지정 합니다. M에 대 한 Read-Only 지시문의 H. 앞에서 설명한 대로 **리소스에 포함** 명령을 사용 하 여 RC를 사용 합니다.

리소스를 식별 하는 데 사용 하기 전에 공유할 기호를 예측 하는 것이 가장 편리 합니다. 공유 헤더 파일에 기호를 추가하고 해당 .RC 파일에 대한 읽기 전용 지시문에 공유 헤더 파일을 아직 #include로 지정하지 않았다면 기호를 사용하기 전에 #include로 지정합니다. 이 방식으로 기호 공유를 예측하지 않은 경우 기호에 대한 #define 문을 수동으로(텍스트 편집기 사용) 이동해야 합니다. 즉 MYSTRS.RC에서 사용하기 전에 MYMENUS.H를 MYSHARED.H로 옮겨야 합니다.

또한 여러 .RC 파일의 기호를 관리할 때 Visual C++에서 동일한 ID 숫자 값이 각각의 리소스(기호)에 할당되지 않도록 해야 합니다. 지정된 .RC 파일의 경우 Visual C++에서는 각각 네 개의 ID 도메인에 ID를 증분형으로 할당합니다. Visual C++에서는 편집 세션 사이에 .RC 파일의 기호 헤더 파일에서 각각의 도메인에 할당된 마지막 ID를 지속적으로 추적합니다. 빈(새) .RC 파일에서 APS_NEXT 값의 의미는 다음과 같습니다.

```rc
#define _APS_NEXT_RESOURCE_VALUE  101
#define _APS_NEXT_COMMAND_VALUE   40001
#define _APS_NEXT_CONTROL_VALUE   1000
#define _APS_NEXT_SYMED_VALUE     101
```

`_APS_NEXT_RESOURCE_VALUE` 는 대화 상자 리소스, 메뉴 리소스 등에 사용 되는 다음 기호 값입니다. 리소스 기호 값의 유효 범위는 1 ~ 0x6FFF입니다.

`_APS_NEXT_COMMAND_VALUE` 는 명령 식별에 사용 되는 다음 기호 값입니다. 명령 기호 값의 유효 범위는 0x8000 ~ 0xDFFF입니다.

`_APS_NEXT_CONTROL_VALUE` 대화 상자 컨트롤에 사용 되는 다음 기호 값입니다. 대화 상자 컨트롤 기호 값의 유효 범위는 8 ~ 0xDFFF입니다.

`_APS_NEXT_SYMED_VALUE` 기호 브라우저에서 새로 만들기 명령을 사용 하 여 기호 값을 수동으로 할당할 때 실행 되는 다음 기호 값입니다.

Visual C++는 새 .RC 파일을 만들 때 최저 유효 값보다 조금 높은 값부터 시작합니다. 또한 애플리케이션 마법사는 이러한 값을 MFC 애플리케이션에 보다 적합한 형태로 초기화합니다. ID 값 범위에 대 한 자세한 내용은 [Technical Note 20](../mfc/tn020-id-naming-and-numbering-conventions.md)을 참조 하십시오.

이제 동일한 프로젝트 에서도 새 리소스 파일을 만들 때마다 Visual C++ 같은 값을 정의 `_APS_NEXT_` 합니다. 다시 말해서 두 .RC 파일에 여러 대화 상자를 추가하는 경우 동일한 #define 값이 서로 다른 대화 상자에 할당될 가능성이 높습니다. 예를 들면 첫 번째 .RC 파일의 IDD_MY_DLG1에는 두 번째 .RC 파일의 IDD_MY_DLG2와 동일한 101이라는 번호가 할당될 수 있습니다.

이를 방지하려면 해당 .RC 파일에서 네 개의 ID 도메인 각각에 대한 별도 수치 영역을 예약해야 합니다. 각에서 값을 수동으로 업데이트 하 여이 작업을 수행 `_APS_NEXT` 합니다. RC 파일 **은** 리소스 추가를 시작 합니다. 예를 들어, 첫 번째입니다. RC 파일은 기본값을 사용 하 `_APS_NEXT` 고 다음 `_APS_NEXT` 값을 두 번째 값에 할당할 수 있습니다. RC 파일:

```rc
#define _APS_NEXT_RESOURCE_VALUE  2000
#define _APS_NEXT_COMMAND_VALUE   42000
#define _APS_NEXT_CONTROL_VALUE   2000
#define _APS_NEXT_SYMED_VALUE     2000
```

물론, 여전히 Visual C++에서 숫자 값이 두 번째 .RC 파일용으로 예약된 값과 겹치도록 첫 번째 .RC 파일의 여러 ID를 할당할 수도 있습니다. 따라서 이러한 일이 발생하지 않도록 충분히 큰 범위를 예약해야 합니다.

## <a name="managing-dependencies-between-rc-cpp-and-h-files"></a>.RC, .CPP 및 .H 파일 간의 종속성 관리

Visual C++에서는 .RC 파일을 저장할 때 해당하는 RESOURCE.H 파일에 대한 기호 변경 내용도 저장합니다. .RC 파일의 리소스를 참조하는 .CPP 파일은 RESOURCE.H 파일을 (흔히 프로젝트의 마스터 헤더 파일에서) #include로 지정해야 합니다. 이렇게 하면 소스 파일에서 헤더 종속성을 검사하는 개발 환경의 내부 프로젝트 관리 기능으로 인해 원치 않는 역효과가 발생합니다. Visual C++에서 새 기호를 추가할 때마다 모든입니다. 리소스를 #include 하는 .CPP 파일입니다. H를 다시 컴파일해야 합니다.

Visual C++는 RESOURCE.H 파일의 첫 번째 줄에 다음 주석을 포함하여 RESOURCE.H에 대한 종속성을 회피합니다.

```h
//{{NO_DEPENDENCIES}}
```

개발 환경은 RESOURCE.H에 대한 변경 내용을 무시하여 이 주석을 해석하므로 종속된 .CPP 파일을 다시 컴파일할 필요가 없습니다.

Visual C++에서는 파일을 저장할 때 항상 //{{NO_DEPENDENCIES}} 주석 줄이 .RC 파일에 추가됩니다. 경우에 따라 RESOURCE.H에 대한 빌드 종속성 회피로 인해 링크 타임에는 발견되지 않은 런타임 오류가 발생할 수도 있습니다. 예를 들어, 기호 브라우저를 사용하여 리소스에 대한 기호에 할당된 숫자 값을 변경하는 경우 해당 리소스를 참조하는 .CPP 파일이 다시 컴파일되지 않을 경우 애플리케이션 런타임 시 해당 리소스를 올바르게 찾아서 로드할 수 없습니다. 이러한 경우에는을 명시적으로 다시 컴파일해야 합니다. 사용자가 알고 있는 CPP 파일은 리소스의 기호 변경에 의해 영향을 받습니다. H 또는 **모두 다시 빌드** 를 선택 합니다. 특정 리소스 그룹에 대 한 기호 값을 자주 변경 해야 하는 경우 [추가 헤더 파일을 비롯 한](#_mfcnotes_tn035_including)위의 섹션에서 설명한 대로 이러한 기호를 별도의 읽기 전용 헤더 파일로 분할 하는 것이 더 쉽고 안전 하다는 것을 알 수 있습니다.

## <a name="how-visual-c-manages-set-includes-information"></a><a name="_mfcnotes_tn035_set_includes"></a> Visual C++ 관리 집합에 포함 되는 정보

위의 설명한 바와 같이, 파일 메뉴의 Set Includes 명령을 통해 세 가지 유형의 정보를 지정할 수 있습니다.

- 기호 헤더 파일

- 읽기 전용 기호 지시문

- 컴파일 타임 지시문

다음은 Visual C++에서 이러한 정보가 .RC 파일에서 어떻게 관리되는지 설명합니다. Visual C++를 사용하는 데는 이 정보가 필요하지 않지만, 이 정보에 대해 제대로 알고 있으면 Set Includes 기능을 좀더 자신 있게 사용할 수 있습니다.

위의 각각의 세 가지 Set Includes 정보 유형은 .RC 파일에서 두 가지 형태, 즉 (1) #include 또는 리소스 컴파일러에 의해 해석될 수 있는 기타 지시문과, (2) Visual C++에 의해서만 해석될 수 있는 특수 TEXTINCLUDE 리소스로 저장됩니다.

TEXTINCLUDE 리소스의 목적은 설정 된 Include 정보를 Visual C++의 **Set** include 대화 상자에 쉽게 적용할 수 있는 양식에 안전 하 게 저장 하는 것입니다. TEXTINCLUDE는 Visual C++에 의해 정의 된 *리소스 형식* 입니다. Visual C++에서는 리소스 ID 1, 2 및 3이 지정된 세 가지 특정 TEXTINCLUDE 리소스를 인식합니다.

|TEXTINCLUDE 리소스 ID|Set Includes 정보 유형|
|-----------------------------|--------------------------------------|
|1|기호 헤더 파일|
|2|읽기 전용 기호 지시문|
|3|컴파일 타임 지시문|

아래 설명된 바와 같이 각각의 세 가지 Set Includes 정보 유형이 응용 프로그램 마법사가 만든 기본 MYAPP.RC와 RESOURCE.H 파일을 통해 설명됩니다. BEGIN과 END 블록 사이에 있는 추가 \0과 "" 토큰은 RC 구문에서 각각의 0 종단 문자열과 큰따옴표 문자를 지정하는 데 필요합니다.

### <a name="symbol-header-file"></a>기호 헤더 파일

리소스 컴파일러에 의해 해석되는 기호 헤더 파일 정보의 형태는 #include 문입니다.

```rc
#include "resource.h"
```

해당하는 TEXTINCLUDE 리소스는 다음과 같습니다.

```rc
1 TEXTINCLUDE DISCARDABLE
BEGIN
    "resource.h\0"
END
```

### <a name="read-only-symbol-directives"></a>읽기 전용 기호 지시문

읽기 전용 기호 지시문은 리소스 컴파일러에 의해 해석할 수 있는 다음 형태로 MYAPP.RC 맨 위에 포함됩니다.

```rc
#include "afxres.h"
```

해당하는 TEXTINCLUDE 리소스는 다음과 같습니다.

```rc
2 TEXTINCLUDE DISCARDABLE
BEGIN
   "#include ""afxres.h""\r\n"
   "\0"
END
```

### <a name="compile-time-directives"></a>컴파일 타임 지시문

컴파일 타임 지시문은 리소스 컴파일러에 의해 해석할 수 있는 다음 형태로 MYAPP.RC 끝에 포함됩니다.

```rc
#ifndef APSTUDIO_INVOKED
///////////////////////
//
// From TEXTINCLUDE 3
//
#include "res\myapp.rc2"  // non-Visual C++ edited resources

#include "afxres.rc"  // Standard components
#include "afxprint.rc"  // printing/print preview resources
#endif  // not APSTUDIO_INVOKED
```

#ifndef APSTUDIO_INVOKED 지시문은 Visual C++에 컴파일 타임 지시문을 건너뛰도록 지정합니다.

해당하는 TEXTINCLUDE 리소스는 다음과 같습니다.

```rc
3 TEXTINCLUDE DISCARDABLE
BEGIN
"#include ""res\myapp.rc2""  // non-Visual C++ edited resources\r\n"
"\r\n"
"#include ""afxres.rc""  // Standard components\r\n"
"#include ""afxprint.rc""  // printing/print preview resources\r\n"
"\0"
END
```

## <a name="see-also"></a>참고 항목

[번호로 기술 참고 사항](../mfc/technical-notes-by-number.md)\
[범주별 기술 참고 사항](../mfc/technical-notes-by-category.md)
