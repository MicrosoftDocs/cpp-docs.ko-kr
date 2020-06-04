﻿---
title: 공급자용 프로젝트 만들기
ms.date: 10/22/2018
helpviewer_keywords:
- ATL projects, creating
- OLE DB providers, projects
- projects [C++], creating
ms.assetid: 076a75de-1d4b-486a-bcf8-9c0f6b049fa2
ms.openlocfilehash: f2ff42ba8a2e908f672db7e96fc9f24f51a1fd9b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80211408"
---
# <a name="creating-a-project-for-the-provider"></a>공급자용 프로젝트 만들기

## <a name="to-create-a-project-in-which-the-ole-db-provider-will-reside"></a>OLE DB 공급자가 상주할 프로젝트를 만들려면

1. **파일** 메뉴에서 **새로 만들기**를 클릭한 다음 **프로젝트**를 클릭합니다.

   **새 프로젝트** 대화 상자가 나타납니다.

1. **프로젝트 형식** 창에서 **설치** 된 > **Visual C++**  > **MFC/ATL** 폴더를 클릭 합니다. **템플릿** 창에서 **ATL 프로젝트**를 클릭 합니다.

    > [!NOTE]
    > 이전 버전의 visual Studio에서는 **설치** > **템플릿** > **visual C++**  > **ATL**에서 프로젝트 형식을 찾습니다.

1. **이름** 상자에 프로젝트의 이름을 입력 하 고 **확인**을 클릭 합니다.

   **ATL 프로젝트 마법사** 가 나타납니다.

1. **ATL 프로젝트 마법사**에서 **응용 프로그램 종류**에 대 한 **DLL (동적 연결 라이브러리)** 을 선택 합니다.

1. **마침**을 클릭합니다.

## <a name="see-also"></a>참고 항목

[OLE DB 공급자 만들기](../../data/oledb/creating-an-ole-db-provider.md)
