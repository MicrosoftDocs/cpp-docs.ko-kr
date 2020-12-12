---
description: '자세한 정보: 클립보드: 다른 형식 추가'
title: '클립보드: 기타 서식 추가'
ms.date: 11/04/2016
helpviewer_keywords:
- formats [MFC], Clipboard
- Clipboard, formats
- custom formats, placing on Clipboard
- custom formats
- registering custom Clipboard data formats
- custom Clipboard data formats
ms.assetid: aea58159-65ed-4385-aeaa-3d9d5281903b
ms.openlocfilehash: 3259660725f324436cc606574eb36499f74e7054
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97176641"
---
# <a name="clipboard-adding-other-formats"></a>클립보드: 기타 서식 추가

이 항목에서는 특히 OLE 지원의 지원 되는 형식 목록을 확장 하는 방법에 대해 설명 합니다. 클립보드 항목 [: 데이터 복사 및 붙여넣기](clipboard-copying-and-pasting-data.md) 는 클립보드에서 복사 및 붙여넣기를 지 원하는 데 필요한 최소 구현에 대해 설명 합니다. 이를 구현 하는 모든 경우에는 클립보드에 배치 된 형식만 **CF_METAFILEPICT**, **CF_EMBEDSOURCE** **CF_OBJECTDESCRIPTOR** 및 **CF_LINKSOURCE** 수 있습니다. 대부분의 응용 프로그램은 이러한 세 가지 보다 클립보드에 더 많은 형식이 필요 합니다.

## <a name="registering-custom-formats"></a><a name="_core_registering_custom_formats"></a> 사용자 지정 형식 등록

사용자 지정 형식을 직접 만들려면 사용자 지정 클립보드 형식을 등록할 때 사용 하는 것과 동일한 절차를 따르세요. 형식의 이름을 **RegisterClipboardFormat** 함수에 전달 하 고 반환 값을 형식 ID로 사용 합니다.

## <a name="placing-formats-on-the-clipboard"></a><a name="_core_placing_formats_on_the_clipboard"></a> 클립보드에 형식 배치

클립보드에 배치 된 형식에 더 많은 형식을 추가 하려면 `OnGetClipboardData` `COleClientItem` `COleServerItem` 복사할 데이터가 네이티브 인지 여부에 따라 또는에서 파생 된 클래스의 함수를 재정의 해야 합니다. 이 함수에서 다음 절차를 사용 해야 합니다.

#### <a name="to-place-formats-on-the-clipboard"></a>클립보드에 형식을 추가 하려면

1. `COleDataSource` 개체를 만듭니다.

1. 을 호출 하 여 지원 되는 형식 목록에 네이티브 데이터 형식을 추가 하는 함수에이 데이터 소스를 전달 `COleDataSource::CacheGlobalData` 합니다.

1. `COleDataSource::CacheGlobalData`지원 하려는 각 표준 형식에 대해를 호출 하 여 표준 형식을 추가 합니다.

이 기법은 MFC OLE 샘플 프로그램 [HIERSVR](../overview/visual-cpp-samples.md) ( `OnGetClipboardData` **cserveritem** 클래스의 멤버 함수 검사)에서 사용 됩니다. 이 샘플의 유일한 차이점은 HIERSVR에서 다른 표준 형식을 지원 하지 않기 때문에 3 단계가 구현 되지 않는다는 것입니다.

### <a name="what-do-you-want-to-know-more-about"></a>자세히 알아야 할 내용

- [OLE 데이터 개체 및 데이터 원본 및 균일 한 데이터 전송](data-objects-and-data-sources-ole.md)

- [OLE 끌어서 놓기](drag-and-drop-ole.md)

- [OLE](ole-background.md)

## <a name="see-also"></a>참고 항목

[클립보드: OLE 클립보드 메커니즘 사용](clipboard-using-the-ole-clipboard-mechanism.md)
