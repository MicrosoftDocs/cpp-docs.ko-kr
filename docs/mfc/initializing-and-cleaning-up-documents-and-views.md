---
description: '자세히 알아보기: 문서 및 뷰 초기화 및 정리'
title: 문서 및 뷰 초기화 및 정리
ms.date: 11/04/2016
helpviewer_keywords:
- initializing documents [MFC]
- views [MFC], cleaning up
- documents [MFC], initializing
- documents [MFC], cleaning up
- views [MFC], initializing
- initializing objects [MFC], document objects
- document objects [MFC], life cycle of
- initializing views [MFC]
ms.assetid: 95d6f09b-a047-4079-856a-ae7d0548e9d2
ms.openlocfilehash: 023f81e46d67237d64836e843205c45558728b31
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97290065"
---
# <a name="initializing-and-cleaning-up-documents-and-views"></a>문서 및 뷰 초기화 및 정리

문서와 뷰를 초기화 하 고 정리 하려면 다음 지침을 따르십시오.

- MFC 프레임 워크는 문서 및 뷰를 초기화 합니다. 사용자가 추가 하는 모든 데이터를 초기화 합니다.

- 프레임 워크는 문서와 보기가 종료 되 면 정리 됩니다. 이러한 문서 및 뷰의 멤버 함수 내에서 힙에 할당 한 모든 메모리의 할당을 취소 해야 합니다.

> [!NOTE]
> 전체 응용 프로그램에 대 한 초기화는 클래스의 [InitInstance](reference/cwinapp-class.md#initinstance) 멤버 함수 재정의에서 가장 잘 수행 되며, `CWinApp` 전체 응용 프로그램에 대 한 정리는 `CWinApp` 멤버 함수 [exitinstance](reference/cwinapp-class.md#exitinstance)의 재정의에서 가장 잘 수행 됩니다.

MDI 응용 프로그램에서 문서 (및 해당 프레임 창 및 보기 또는 보기)의 수명 주기는 다음과 같습니다.

1. 동적 생성 중 문서 생성자가 호출 됩니다.

1. 각 새 문서에 대해 문서의 [Onnewdocument](reference/cdocument-class.md#onnewdocument) 또는 [onopendocument](reference/cdocument-class.md#onopendocument) 가 호출 됩니다.

1. 사용자는 수명 내내 문서와 상호 작용 합니다. 일반적으로이는 사용자가 뷰를 통해 문서 데이터에서 작업을 수행 하 고 데이터를 선택 하 고 편집 하는 경우에 발생 합니다. 뷰는 저장소에 대 한 변경 내용을 문서에 전달 하 고 다른 보기를 업데이트 합니다. 이 시간 동안 문서와 뷰에서 명령을 처리할 수 있습니다.

1. 프레임 워크는 [DeleteContents](reference/cdocument-class.md#deletecontents) 를 호출 하 여 문서와 관련 된 데이터를 삭제 합니다.

1. 문서의 소멸자가 호출 됩니다.

SDI 응용 프로그램에서 1 단계는 문서를 처음 만들 때 한 번 수행 됩니다. 그런 다음, 2 ~ 4 단계는 새 문서를 열 때마다 반복적으로 수행 됩니다. 새 문서는 기존 문서 개체를 재사용 합니다. 마지막으로 응용 프로그램이 종료 되 면 5 단계가 수행 됩니다.

## <a name="what-do-you-want-to-know-more-about"></a>자세히 알아야 할 내용

- [문서 및 뷰 초기화](initializing-documents-and-views.md)

- [문서 및 뷰 정리](cleaning-up-documents-and-views.md)

## <a name="see-also"></a>참고 항목

[문서/뷰 아키텍처](document-view-architecture.md)
