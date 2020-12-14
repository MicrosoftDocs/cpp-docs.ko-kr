---
description: '자세히 알아보기: 클립보드: 데이터 복사 및 붙여넣기'
title: '클립보드: 데이터 복사 및 붙여넣기'
ms.date: 11/04/2016
helpviewer_keywords:
- Clipboard, copying data to
- Clipboard, pasting
ms.assetid: 580e10be-241f-4f9f-94cf-8302edc5beef
ms.openlocfilehash: fdc102cf7a92bc78df83419269bb5de828dc9d19
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97251234"
---
# <a name="clipboard-copying-and-pasting-data"></a>클립보드: 데이터 복사 및 붙여넣기

이 항목에서는 OLE 응용 프로그램에서 클립보드에 복사 및 붙여넣기를 구현 하는 데 필요한 최소 작업에 대해 설명 합니다. 계속 하기 전에 [데이터 개체 및 데이터 원본 (OLE)](data-objects-and-data-sources-ole.md) 항목을 읽는 것이 좋습니다.

복사 또는 붙여넣기를 구현 하려면 먼저 편집 메뉴의 복사, 잘라내기 및 붙여넣기 옵션을 처리 하는 함수를 제공 해야 합니다.

## <a name="copying-or-cutting-data"></a><a name="_core_copying_or_cutting_data"></a> 데이터 복사 또는 잘라내기

#### <a name="to-copy-data-to-the-clipboard"></a>클립보드에 데이터를 복사 하려면

1. 복사할 데이터가 네이티브 데이터 인지 또는 연결 된 항목 인지를 결정 합니다.

   - 데이터가 포함 되거나 연결 된 경우 선택한 개체에 대 한 포인터를 가져옵니다 `COleClientItem` .

   - 데이터가 네이티브이 고 응용 프로그램이 서버인 경우 선택한 데이터를 포함 하는에서 파생 된 새 개체를 만듭니다 `COleServerItem` . 그렇지 않은 경우 `COleDataSource` 에는 데이터에 대 한 개체를 만듭니다.

1. 선택한 항목의 `CopyToClipboard` 멤버 함수를 호출 합니다.

1. 사용자가 복사 작업 대신 잘라내기 작업을 선택한 경우 응용 프로그램에서 선택한 데이터를 삭제 합니다.

이 시퀀스의 예제를 보려면 `OnEditCut` `OnEditCopy` MFC OLE 샘플 프로그램 [OCLIENT](../overview/visual-cpp-samples.md) 및 [HIERSVR](../overview/visual-cpp-samples.md)의 및 함수를 참조 하세요. 이러한 샘플에서는 현재 선택 된 데이터에 대 한 포인터를 유지 하므로 1 단계가 이미 완료 되었습니다.

## <a name="pasting-data"></a><a name="_core_pasting_data"></a> 데이터 붙여넣기

데이터를 붙여 넣는 것은 응용 프로그램에 데이터를 붙여 넣는 데 사용할 형식을 선택 해야 하기 때문에 복사 하는 것 보다 더 복잡 합니다.

#### <a name="to-paste-data-from-the-clipboard"></a>클립보드에서 데이터를 붙여넣으려면

1. 뷰 클래스에서를 구현 `OnEditPaste` 하 여 편집 메뉴에서 붙여넣기 옵션을 선택 하는 사용자를 처리 합니다.

1. 함수에서 `OnEditPaste` 개체를 만들고 `COleDataObject` 해당 `AttachClipboard` 멤버 함수를 호출 하 여이 개체를 클립보드의 데이터에 연결 합니다.

1. `COleDataObject::IsDataAvailable`을 호출 하 여 특정 형식을 사용할 수 있는지 여부를 확인 합니다.

   또는를 사용 하 여 `COleDataObject::BeginEnumFormats` 응용 프로그램에 가장 적합 한 항목을 찾을 때까지 다른 형식을 찾을 수 있습니다.

1. 서식 붙여넣기를 수행 합니다.

이 작업의 작동 방식에 대 한 예제는 `OnEditPaste` MFC OLE 샘플 프로그램 [OCLIENT](../overview/visual-cpp-samples.md) 및 [HIERSVR](../overview/visual-cpp-samples.md)에 정의 된 뷰 클래스의 멤버 함수 구현을 참조 하세요.

> [!TIP]
> 붙여넣기 작업을 자체 함수로 분리 하는 기본적인 방법은 끌어서 놓기 작업을 수행 하는 동안 응용 프로그램에서 데이터를 삭제할 때 동일한 붙여넣기 코드를 사용할 수 있다는 것입니다. OCLIENT 및 HIERSVR에서와 같이 `OnDrop` 함수 `DoPasteItem` 는 붙여넣기 작업을 구현 하기 위해 작성 된 코드를 다시 사용 하 여를 호출할 수도 있습니다.

편집 메뉴에서 선택 하 여 붙여넣기 옵션을 처리 하려면 [OLE의 항목 대화 상자](dialog-boxes-in-ole.md)를 참조 하세요.

### <a name="what-do-you-want-to-know-more-about"></a>자세히 알아야 할 내용

- [다른 형식 추가](clipboard-adding-other-formats.md)

- [OLE 데이터 개체 및 데이터 원본 및 균일 한 데이터 전송](data-objects-and-data-sources-ole.md)

- [OLE 끌어서 놓기](drag-and-drop-ole.md)

- [OLE](ole-background.md)

## <a name="see-also"></a>참고 항목

[클립보드: OLE 클립보드 메커니즘 사용](clipboard-using-the-ole-clipboard-mechanism.md)
