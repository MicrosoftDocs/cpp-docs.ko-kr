---
title: 공급자용 프로젝트 만들기
ms.date: 10/22/2018
helpviewer_keywords:
- ATL projects, creating
- OLE DB providers, projects
- projects [C++], creating
ms.assetid: 076a75de-1d4b-486a-bcf8-9c0f6b049fa2
ms.openlocfilehash: f63b09d47dd8f3ebe8750275bb005be89ca8fde8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50677112"
---
# <a name="creating-a-project-for-the-provider"></a>공급자용 프로젝트 만들기

## <a name="to-create-a-project-in-which-the-ole-db-provider-will-reside"></a>OLE DB 공급자가 상주할 프로젝트를 만들려면

1. **파일** 메뉴에서 **새로 만들기**를 클릭한 다음 **프로젝트**를 클릭합니다.

   **새 프로젝트** 대화 상자가 나타납니다.

1. **프로젝트 형식** 창에서 **설치됨** > **Visual C++** > **MFC/ATL** 폴더를 클릭합니다. 템플릿 창에서 **ATL 프로젝트**를 클릭합니다.

    > [!NOTE]
    > Visual Studio의 이전 버전에서는 프로젝트 형식에서 **설치됨** > **템플릿** > **Visual C++** > **ATL**을 찾습니다.

1. **이름** 상자에 프로젝트의 이름을 입력한 후 **확인**을 클릭합니다.

   **ATL 프로젝트 마법사**가 나타납니다.

1. **ATL 프로젝트 마법사**에서 응용 프로그램 유형으로 **동적 연결 라이브러리(DLL)**를 선택합니다.

1. **마침**을 클릭합니다.

## <a name="see-also"></a>참고 항목

[OLE DB 공급자 만들기](../../data/oledb/creating-an-ole-db-provider.md)
