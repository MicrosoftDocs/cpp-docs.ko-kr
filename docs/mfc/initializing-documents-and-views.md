---
description: '자세히 알아보기: 문서 및 뷰 초기화'
title: 문서 및 뷰 초기화
ms.date: 11/04/2016
helpviewer_keywords:
- initializing documents [MFC]
- documents [MFC], initializing
- views [MFC], initializing
- initializing objects [MFC], document objects
- initializing views [MFC]
ms.assetid: 33cb8643-8a16-478c-bc26-eccc734e3661
ms.openlocfilehash: ea0840faefac0ae5a8b4cee0fe3b707a92737c70
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97208036"
---
# <a name="initializing-documents-and-views"></a>문서 및 뷰 초기화

문서는 두 가지 방법으로 만들어지므로 문서 클래스는 두 가지 방법을 모두 지원 해야 합니다. 먼저 사용자가 File New 명령을 사용 하 여 비어 있는 새 문서를 만들 수 있습니다. 이 경우 [CDocument](reference/cdocument-class.md)클래스의 [onnewdocument](reference/cdocument-class.md#onnewdocument) 멤버 함수 재정의에서 문서를 초기화 합니다. 두 번째로, 사용자는 파일 메뉴의 열기 명령을 사용 하 여 파일에서 콘텐츠를 읽는 새 문서를 만들 수 있습니다. 이 경우 클래스의 [Onopendocument](reference/cdocument-class.md#onopendocument) 멤버 함수 재정의에서 문서를 초기화 `CDocument` 합니다. 두 초기화가 모두 동일한 경우 두 재정의에서 공통 멤버 함수를 호출 하거나 `OnOpenDocument` `OnNewDocument` 를 호출 하 여 정리 문서를 초기화 한 다음 열기 작업을 완료할 수 있습니다.

문서를 만든 후에 뷰가 생성 됩니다. 뷰를 초기화 하는 가장 좋은 시기는 프레임 워크가 문서, 프레임 창 및 뷰 만들기를 완료 한 후입니다. [CView](reference/cview-class.md)의 [oninitialupdate](reference/cview-class.md#oninitialupdate) 멤버 함수를 재정의 하 여 뷰를 초기화할 수 있습니다. 문서가 변경 될 때마다 다시 초기화 하거나 조정 해야 하는 경우 [OnUpdate](reference/cview-class.md#onupdate)을 재정의할 수 있습니다.

## <a name="see-also"></a>참고 항목

[문서 및 뷰 초기화 및 정리](initializing-and-cleaning-up-documents-and-views.md)
