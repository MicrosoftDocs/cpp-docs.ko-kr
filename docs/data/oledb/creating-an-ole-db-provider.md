---
description: '자세한 정보: OLE DB 공급자 만들기'
title: OLE DB 공급자 만들기
ms.date: 10/13/2018
helpviewer_keywords:
- OLE DB providers, creating
- OLE DB provider templates, creating providers
ms.assetid: f73017c3-c89f-41a6-a306-ea992cf6092c
ms.openlocfilehash: 69dc9311a79f2739636633b2d268343a92d2dac9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97287803"
---
# <a name="creating-an-ole-db-provider"></a>OLE DB 공급자 만들기

OLE DB 공급자를 만드는 권장 방법은 마법사를 사용 하 여 ATL COM 프로젝트 및 공급자를 만든 다음 OLE DB 템플릿을 사용 하 여 파일을 수정 하는 것입니다. 공급자를 사용자 지정할 때 원치 않는 속성을 주석으로 처리 하 고 선택적 인터페이스를 추가할 수 있습니다.

기본적인 단계는 다음과 같습니다.

1. **Atl 프로젝트 마법사** 를 사용 하 여 기본 프로젝트 파일을 만들고 **atl oledb 공급자 마법사** 를 사용 하 여 공급자를 만듭니다 (    >    >  **새 항목 추가** 의 설치 된 Visual C++**atl** 폴더에서 atl oledb 공급자 선택).

   > [!NOTE]
   > **ATL OLEDB 공급자** 를 추가 하기 전에 프로젝트에 MFC 지원이 포함 되어야 합니다.

1. `Execute` [Ccustomrowset (customrs. h)](cmyproviderrowset-myproviderrs-h.md)에서 메서드의 코드를 수정 합니다. 예제는 [OLE DB 공급자로 문자열 읽기](../../data/oledb/reading-strings-into-the-ole-db-provider.md)를 참조 하세요.

1. [Customds. h](cmyprovidersource-myproviderds-h.md), [CustomSess](cmyprovidersession-myprovidersess-h.md)및 [customds](cmyproviderrowset-myproviderrs-h.md)에서 속성 맵을 편집 합니다. 마법사에서 공급자가 구현할 수 있는 모든 속성을 포함 하는 속성 맵을 만듭니다. 속성 맵을 살펴보고 공급자가 지원 하지 않아도 되는 속성을 제거 하거나 주석으로 처리 합니다.

1. [Ccustomrowset (CustomRS. h)](cmyproviderrowset-myproviderrs-h.md)에서 찾을 수 있는 PROVIDER_COLUMN_MAP를 업데이트 합니다. 예제는 [OLE DB 공급자에 문자열 저장](../../data/oledb/storing-strings-in-the-ole-db-provider.md)을 참조 하세요.

1. 공급자를 테스트할 준비가 되 면 공급자 열거에서 공급자를 찾아 테스트할 수 있습니다. 열거형에서 공급자를 찾는 테스트 코드의 예제는 [CATDB](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/OLEDB/Consumer/catdb) 및 [DBVIEWER](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/OLEDB/Consumer/dbviewer) 샘플 또는 [간단한 소비자 구현](../../data/oledb/implementing-a-simple-consumer.md)의 예제를 참조 하세요.

1. 원하는 추가 인터페이스를 추가 합니다. 예를 들어 [간단한 Read-Only 공급자 강화](../../data/oledb/enhancing-the-simple-read-only-provider.md)를 참조 하세요.

   > [!NOTE]
   > 기본적으로 마법사는 OLE DB 수준 0 규격 코드를 생성 합니다. 응용 프로그램이 수준 0을 준수 하도록 하려면 코드에서 마법사 생성 인터페이스를 제거 하지 마십시오.

## <a name="see-also"></a>참고 항목

[CatDB 샘플: 데이터 소스 스키마 브라우저](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/OLEDB/Consumer/catdb)<br/>
[DBViewer 샘플: 데이터베이스 브라우저](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/OLEDB/Consumer/dbviewer)
