---
description: '자세히 알아보기: 문서 데이터 변수를 사용 하 여 데이터 관리'
title: 문서 데이터 변수로 데이터 관리
ms.date: 11/04/2016
helpviewer_keywords:
- documents [MFC], data storage
- friend classes [MFC]
- classes [MFC], friend
- data [MFC]
- data [MFC], documents
- collection classes [MFC], used by document object
- document data [MFC]
- member variables [MFC], document class [MFC]
ms.assetid: e70b87f4-8c30-49e5-8986-521c2ff91704
ms.openlocfilehash: d05bfe71d080c08b3e0f3bbd416421e612b5d7ec
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97112208"
---
# <a name="managing-data-with-document-data-variables"></a>문서 데이터 변수로 데이터 관리

문서 클래스의 멤버 변수로 문서 데이터를 구현 합니다. 예를 들어, Scribble 프로그램은 `CObList` 개체에 대 한 포인터를 저장 하는 연결 된 목록 형식의 데이터 멤버를 선언 합니다 `CObject` . 이 목록은 자유 선 그리기를 구성 하는 점의 배열을 저장 하는 데 사용 됩니다.

문서의 멤버 데이터를 구현 하는 방법은 응용 프로그램의 특성에 따라 다릅니다. 이를 돕기 위해 MFC는,,, 및와 같은 다양 한 공통 데이터 형식을 캡슐화 하는 클래스를 비롯 하 여 c + + 템플릿을 기반으로 하는 컬렉션을 비롯 한 배열, 목록 및 맵 (사전) 그룹을 제공 `CString` `CRect` `CPoint` `CSize` `CTime` 합니다. 이러한 클래스에 대 한 자세한 내용은 *MFC 참조* 의 [클래스 라이브러리 개요](class-library-overview.md) 를 참조 하세요.

문서의 멤버 데이터를 정의 하는 경우 일반적으로 문서 클래스에 멤버 함수를 추가 하 여 데이터 항목을 설정 하 고 가져오고 다른 유용한 작업을 수행 합니다.

뷰는 생성 시 뷰에 설치 된 문서에 대 한 뷰의 포인터를 사용 하 여 문서 개체에 액세스 합니다. 멤버 함수를 호출 하 여 뷰의 멤버 함수에서이 포인터를 검색할 수 있습니다 `CView` `GetDocument` . 이 포인터를 고유한 문서 형식으로 캐스팅 해야 합니다. 그런 다음 포인터를 통해 public 문서 멤버에 액세스할 수 있습니다.

자주 데이터를 전송 하는 경우 직접 액세스 권한이 필요 하거나 문서 클래스의 public이 아닌 멤버를 사용 하려는 경우에는 view 클래스를 document 클래스의 friend (c + + 용어로)로 설정 해야 할 수 있습니다.

## <a name="see-also"></a>참고 항목

[문서 사용](using-documents.md)
