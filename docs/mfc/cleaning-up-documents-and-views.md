---
description: '자세히 알아보기: 문서 및 뷰 정리'
title: 문서 및 뷰 정리
ms.date: 11/04/2016
helpviewer_keywords:
- views [MFC], cleaning up
- documents [MFC], cleaning up
- documents [MFC], closing
ms.assetid: 0c454db2-3644-434d-9e53-8108a7aedfe1
ms.openlocfilehash: 73d7dcb94068499998ac05d76dd023b7274c6588
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97176655"
---
# <a name="cleaning-up-documents-and-views"></a>문서 및 뷰 정리

문서를 닫으면 프레임 워크는 먼저 해당 [DeleteContents](reference/cdocument-class.md#deletecontents) 멤버 함수를 호출 합니다. 문서 작업 중 힙에서 메모리를 할당한 경우 메모리를 할당 해제하기에 가장 좋은 위치는 `DeleteContents`입니다.

> [!NOTE]
> 문서의 소멸자에서는 문서 데이터를 할당 해제하지 않아야 합니다. SDI 애플리케이션의 경우 문서 개체를 다시 사용할 수 있습니다.

힙에 할당한 메모리를 할당 해제하도록 뷰의 소멸자를 재정의할 수 있습니다.

## <a name="see-also"></a>참고 항목

[문서 및 뷰 초기화 및 정리](initializing-and-cleaning-up-documents-and-views.md)
