---
title: 공급자 만들기
ms.date: 05/09/2019
helpviewer_keywords:
- OLE DB providers, creating
ms.assetid: 2506ba8f-010d-4231-aac1-387432f7b6b9
ms.openlocfilehash: 5a24245ae19fc6fa2a66d4bf102765b712b4cf5c
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92921505"
---
# <a name="creating-the-provider"></a>공급자 만들기

::: moniker range="msvc-160"

Visual Studio 2019 이상에서는 ATL OLE DB 공급자 마법사를 사용할 수 없습니다.

::: moniker-end

::: moniker range="<=msvc-150"

## <a name="to-create-an-ole-db-provider-with-the-atl-ole-db-provider-wizard"></a>ATL OLE DB 공급자 마법사를 사용하여 OLE DB 공급자를 만들려면 다음을 수행합니다.

1. 프로젝트를 마우스 오른쪽 단추로 클릭합니다.

1. 바로 가기 메뉴에서 **추가** 를 클릭 한 다음 **클래스 추가** 를 클릭 합니다.

1. **클래스 추가** 대화 상자의 **설치됨** > **Visual C++** > **ATL** 에서 **ATL OLEDB 공급자** 아이콘을 선택하고 **열기** 를 클릭합니다.

1. **ATL OLE DB 공급자 마법사** 의 **짧은 이름** 상자에 공급자의 짧은 이름을 입력합니다. 다음 항목에서는 짧은 이름인 *Custom* 을 사용하지만, 다른 이름을 사용할 수 있습니다. 다른 이름 상자는 입력한 이름에 따라 채워집니다.

1. 필요한 경우 다른 이름 상자를 편집합니다. 개체와 파일 이름 외에도 다음을 편집할 수 있습니다.

   - **Coclass** : COM에서 공급자를 만드는 데 사용 하는 이름입니다.

   - **ProgID** : GUID 대신 사용할 수 있는 텍스트 문자열인 프로그래밍 식별자입니다.

   - **Version** : ProgID 및 Coclass와 함께 사용 되어 버전 종속 프로그래밍 ID를 생성 합니다.

1. **마침** 을 클릭합니다.

::: moniker-end

## <a name="see-also"></a>참고 항목

[OLE DB 공급자 만들기](../../data/oledb/creating-an-ole-db-provider.md)
