---
description: '자세히 알아보기: 파일 간 데이터 직렬화'
title: 파일로/파일에서 데이터 Serialize
ms.date: 11/04/2016
helpviewer_keywords:
- documents [MFC], serialization
- documents [MFC], saving
- saving documents
- deserialization [MFC]
- serialization [MFC], role of document
- serialization [MFC], role of data
- data [MFC]
- data [MFC], serializing
- document data [MFC]
ms.assetid: b42a0c68-4bc4-4012-9938-5433a26d2c24
ms.openlocfilehash: 58956b2f11b8f0131aae74a6c5b51715fe25c7e6
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97217447"
---
# <a name="serializing-data-to-and-from-files"></a>파일로/파일에서 데이터 Serialize

지 속성의 기본 개념은 개체가 멤버 변수의 값으로 표시 되는 현재 상태를 영구 저장소에 쓸 수 있어야 한다는 것입니다. 이후에 영구적 저장소에서 개체의 상태를 읽거나 "deserialize" 하 여 개체를 다시 만들 수 있습니다. 여기서 핵심은 개체 자체가 자신의 상태를 읽고 쓰기 위한 책임이 있다는 점입니다. 따라서 클래스를 영구적으로 유지 하려면 기본 serialization 작업을 구현 해야 합니다.

프레임 워크는 파일 메뉴의 저장 및 저장 명령에 대 한 응답으로 디스크 파일에 문서를 저장 하 고 열기 명령에 대 한 응답으로 디스크 파일에서 문서를 로드 하기 위한 기본 구현을 제공 합니다. 매우 적은 작업으로 파일에 대 한 데이터를 작성 하 고 읽을 수 있는 문서 기능을 구현할 수 있습니다. 가장 먼저 해야 할 일은 문서 클래스에서 [Serialize](../mfc/reference/cobject-class.md#serialize) 멤버 함수를 재정의 하는 것입니다.

MFC 응용 프로그램 마법사는 `CDocument` `Serialize` 사용자가 만드는 문서 클래스에 멤버 함수를 우선적으로 재정의 합니다. 응용 프로그램의 멤버 변수를 구현한 후에는 `Serialize` 파일에 연결 된 "보관 개체"에 데이터를 전송 하는 코드를 사용 하 여 재정의를 채울 수 있습니다. [CArchive](../mfc/reference/carchive-class.md) 개체는 c + + iostream 라이브러리의 **cin** 및 **cin** 입/출력 개체와 유사 합니다. 그러나는 `CArchive` 서식이 지정 된 텍스트가 아닌 이진 형식을 쓰고 읽습니다.

## <a name="what-do-you-want-to-know-more-about"></a>자세히 알아야 할 내용

- [serialization](../mfc/serialization-in-mfc.md)

- [Serialization의 문서 역할](#_core_the_document.92.s_role_in_serialization)

- [직렬화에서 데이터의 역할](#_core_the_data.92.s_role_in_serialization)

- [Serialization 메커니즘 건너뛰기](../mfc/bypassing-the-serialization-mechanism.md)

## <a name="the-documents-role-in-serialization"></a><a name="_core_the_document.92.s_role_in_serialization"></a> Serialization의 문서 역할

프레임 워크는 문서 `Serialize` 멤버 함수 (구현 된 경우)를 호출 하 여 파일 메뉴의 열기, 저장 및 다른 이름으로 저장 명령에 자동으로 응답 합니다. 예를 들어 ID_FILE_OPEN 명령은 응용 프로그램 개체의 처리기 함수를 호출 합니다. 이 과정에서 사용자는 파일 열기 대화 상자를 확인 하 고 응답 하 고 프레임 워크는 사용자가 선택 하는 파일 이름을 가져옵니다. 프레임 워크는 `CArchive` 문서에 데이터를 로드 하 고 보관 파일을에 전달 하기 위해 설정 된 개체를 만듭니다 `Serialize` . 프레임 워크가 파일을 이미 열었습니다. 문서의 멤버 함수에 있는 코드는 `Serialize` 보관을 통해의 데이터를 읽고 필요에 따라 데이터 개체를 다시 생성할 것입니다. Serialization에 대 한 자세한 내용은 [serialization](../mfc/serialization-in-mfc.md)문서를 참조 하세요.

## <a name="the-datas-role-in-serialization"></a><a name="_core_the_data.92.s_role_in_serialization"></a> 직렬화에서 데이터의 역할

일반적으로 클래스 형식 데이터는 자신을 serialize 할 수 있어야 합니다. 즉, 개체를 보관에 전달 하는 경우 개체는 보관 파일을 작성 하는 방법과 보관 파일에서 파일을 읽는 방법을 알고 있어야 합니다. MFC는 이러한 방식으로 클래스를 serialize 할 수 있도록 지원 합니다. 데이터 형식을 정의 하는 클래스를 디자인 하 고 해당 형식의 데이터를 serialize 하려는 경우 serialization을 디자인 합니다.

## <a name="see-also"></a>참고 항목

[문서 사용](../mfc/using-documents.md)
