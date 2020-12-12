---
description: '자세한 정보: 데이터 개체 및 데이터 원본 (OLE)'
title: 데이터 개체 및 데이터 소스(OLE)
ms.date: 11/04/2016
helpviewer_keywords:
- data objects [MFC], definition
- data transfer [MFC]
- OLE [MFC], data transfer
- data sources [MFC], definition
- data transfer [MFC], definition
- OLE [MFC], data objects
- OLE [MFC], data sources
ms.assetid: 8f68eed8-0ce8-4489-a4cc-f95554f89090
ms.openlocfilehash: 719053e2a75b18fbf54440403351198acc66b9d3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97291209"
---
# <a name="data-objects-and-data-sources-ole"></a>데이터 개체 및 데이터 소스(OLE)

클립보드 또는 끌어서 놓기를 사용 하 여 데이터 전송을 수행 하는 경우 데이터에 원본 및 대상이 있습니다. 한 응용 프로그램은 복사를 위해 데이터를 제공 하 고 다른 응용 프로그램은 붙여넣을 수 있도록 허용 합니다. 전송이 성공 하려면 전송의 각 측에서 동일한 데이터에 대해 서로 다른 작업을 수행 해야 합니다. MFC (Microsoft Foundation Class) 라이브러리는이 전송의 각 측면을 나타내는 두 개의 클래스를 제공 합니다.

- 개체에서 구현 되는 데이터 원본은 `COleDataSource` 데이터 전송의 원본 쪽을 나타냅니다. 데이터를 클립보드에 복사 하거나 끌어서 놓기 작업에 대 한 데이터를 제공할 때 원본 응용 프로그램에 의해 만들어집니다.

- 개체에서 구현 되는 데이터 개체는 `COleDataObject` 데이터 전송의 대상 쪽을 나타냅니다. 이러한 파일은 대상 응용 프로그램에 데이터를 놓을 때 또는 클립보드에서 붙여넣기 작업을 수행 하 라는 메시지가 표시 될 때 생성 됩니다.

다음 문서에서는 응용 프로그램에서 데이터 개체 및 데이터 소스를 사용 하는 방법을 설명 합니다. 이 정보는 데이터를 복사 하 여 붙여넣기 위해 둘 다 호출 될 수 있으므로 컨테이너 및 서버 응용 프로그램 모두에 적용 됩니다.

- [데이터 개체 및 데이터 원본: 생성 및 소멸](data-objects-and-data-sources-creation-and-destruction.md)

- [데이터 개체 및 데이터 소스: 조작](data-objects-and-data-sources-manipulation.md)

## <a name="in-this-section"></a>섹션 내용

[끌어서 놓기](drag-and-drop-ole.md)

[클립보드](clipboard.md)

## <a name="see-also"></a>참고 항목

[OLE](ole-in-mfc.md)<br/>
[COleDataObject 클래스](reference/coledataobject-class.md)<br/>
[COleDataSource 클래스](reference/coledatasource-class.md)
