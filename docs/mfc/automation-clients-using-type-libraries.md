---
description: '자동화 클라이언트: 형식 라이브러리 사용에 대 한 자세한 정보'
title: '자동화 클라이언트: 형식 라이브러리 사용'
ms.date: 11/04/2016
f1_keywords:
- MkTypLib
helpviewer_keywords:
- clients, Automation
- dispatch class [MFC]
- Automation clients, type libraries
- type libraries, Automation clients
- ODL (Object Description Language)
- ODL files
- classes [MFC], dispatch
- MkTypLib tool
- .odl files
ms.assetid: d405bc47-118d-4786-b371-920d035b2047
ms.openlocfilehash: c50425da1327f97fe410723df1e21136f1bd6f98
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97274010"
---
# <a name="automation-clients-using-type-libraries"></a>자동화 클라이언트: 형식 라이브러리 사용

클라이언트에서 서버 개체를 조작 하는 경우 자동화 클라이언트에 서버 개체의 속성 및 메서드에 대 한 정보가 있어야 합니다. 속성에는 데이터 형식이 있습니다. 메서드는 일반적으로 값을 반환 하 고 매개 변수를 허용 합니다. 클라이언트는 서버 개체 형식에 정적으로 바인딩하기 위해 이러한 모든 데이터 형식에 대 한 정보를 요구 합니다.

이 형식 정보는 여러 가지 방법으로 알 수 있습니다. 권장 되는 방법은 형식 라이브러리를 만드는 것입니다.

[MkTypLib](/windows/win32/Midl/differences-between-midl-and-mktyplib)에 대 한 자세한 내용은 Windows SDK를 참조 하세요.

Visual C++는 형식 라이브러리 파일을 읽고 [Coledispatchdriver](reference/coledispatchdriver-class.md)에서 파생 된 디스패치 클래스를 만들 수 있습니다. 해당 클래스의 개체는 서버 개체의 속성과 작업을 복제 합니다. 응용 프로그램은이 개체의 속성 및 작업을 호출 하 고,에서 상속 `COleDispatchDriver` 된 기능은 이러한 호출을 OLE 시스템에 라우팅합니다. 그러면 이러한 호출은 서버 개체로 라우팅됩니다.

Visual C++는 프로젝트를 만들 때 자동화를 포함 하도록 선택한 경우이 형식 라이브러리 파일을 자동으로 유지 관리 합니다. 각 빌드의 일부로 .tlb 파일은 MkTypLib를 사용 하 여 빌드됩니다.

### <a name="to-create-a-dispatch-class-from-a-type-library-tlb-file"></a>형식 라이브러리 파일 (.tlb)에서 디스패치 클래스를 만들려면

1. 클래스 뷰 또는 솔루션 탐색기에서 프로젝트를 마우스 오른쪽 단추로 클릭 하 고 **추가** 를 클릭 한 다음 바로 가기 메뉴에서 **클래스 추가** 를 클릭 합니다.

1. **클래스 추가** 대화 상자의 왼쪽 창에서 **Visual C++/mfc** 폴더를 선택 합니다. 오른쪽 창에서 **TypeLib의 MFC 클래스** 아이콘을 선택 하 고 **열기** 를 클릭 합니다.

1. **Typelib에서 클래스 추가 마법사** 대화 상자의 **사용 가능한 형식 라이브러리** 드롭다운 목록에서 형식 라이브러리를 선택 합니다. **인터페이스** 상자에는 선택한 형식 라이브러리에 사용할 수 있는 인터페이스가 표시 됩니다.

    > [!NOTE]
    >  둘 이상의 형식 라이브러리에서 인터페이스를 선택할 수 있습니다.

   인터페이스를 선택 하려면 두 번 클릭 하거나 **추가** 단추를 클릭 합니다. 이렇게 하면 디스패치 클래스의 이름이 **생성 된 클래스** 상자에 표시 됩니다. 상자에서 클래스 이름을 편집할 수 있습니다 `Class` .

   **파일** 상자에는 클래스가 선언 되는 파일이 표시 됩니다. 이 파일 이름도 편집할 수 있습니다. 헤더 및 구현 정보를 기존 파일이 나 프로젝트 디렉터리가 아닌 다른 디렉터리에 작성 하려는 경우에는 찾아보기 단추를 사용 하 여 다른 파일을 선택할 수도 있습니다.

    > [!NOTE]
    >  선택한 인터페이스에 대 한 모든 디스패치 클래스는 여기에 지정 된 파일에 배치 됩니다. 인터페이스를 별도의 헤더에 선언 하려면 만들려는 각 헤더 파일에 대해이 마법사를 실행 해야 합니다.

    > [!NOTE]
    >  일부 형식 라이브러리 정보는를 사용 하 여 파일에 저장 될 수 있습니다. DLL,. OCX 또는입니다. DTE.OLB 파일 확장명입니다.

1. **Finish** 를 클릭합니다.

   그러면 마법사가 지정 된 클래스와 파일 이름을 사용 하 여 디스패치 클래스에 대 한 코드를 작성 합니다.

## <a name="see-also"></a>참고 항목

[자동화 클라이언트](automation-clients.md)
