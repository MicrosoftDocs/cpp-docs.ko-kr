---
description: '자세한 정보: MFC의 Serialization'
title: MFC의 Serialization
ms.date: 11/04/2016
helpviewer_keywords:
- collection classes [MFC], serialization
- bypassing serialization [MFC]
- MFC, serialization
- serialization [MFC], MFC
- serialization [MFC], bypassing
ms.assetid: fb596a18-4522-47e0-96e0-192732d24c12
ms.openlocfilehash: 278de59c6e091fd59826622553f50503b12602bc
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97217577"
---
# <a name="serialization-in-mfc"></a>MFC의 Serialization

이 문서에서는 MFC 라이브러리 (MFC)에서 제공 하는 serialization 메커니즘을 설명 하 여 프로그램 실행 간에 개체를 유지할 수 있도록 합니다.

Serialization은 디스크 파일 등의 영구 저장 매체에 대 한 개체를 쓰거나 읽는 프로세스입니다. Serialization은 프로그램 실행 중 이나 실행 후에 구조화 된 데이터 (예: c + + 클래스 또는 구조체)의 상태를 유지 관리 해야 하는 경우에 적합 합니다. MFC에서 제공 하는 serialization 개체를 사용 하면이를 표준 및 일관 된 방식으로 사용 하 여 사용자가 직접 파일 작업을 수행 하지 않아도 하므로 수 있습니다.

MFC는 클래스의 serialization에 대 한 기본 제공 지원을 제공 `CObject` 합니다. 따라서에서 파생 된 모든 클래스는 `CObject` `CObject` 의 serialization 프로토콜을 활용할 수 있습니다.

Serialization의 기본 개념은 개체가 현재 상태 (일반적으로 해당 멤버 변수의 값으로 표시 됨)를 영구 저장소에 쓸 수 있어야 한다는 것입니다. 나중에 저장소에서 개체의 상태를 읽거나 deserialize 하 여 개체를 다시 만들 수 있습니다. Serialization은 개체 포인터의 모든 세부 정보와 개체를 serialize 할 때 사용 되는 개체에 대 한 순환 참조를 처리 합니다. 중요 한 점은 개체 자체가 자신의 상태를 읽고 쓰는 것입니다. 따라서 클래스를 serialize 할 수 있도록 하려면 기본 serialization 작업을 구현 해야 합니다. 아티클의 Serialization 그룹에 표시 된 것 처럼이 기능을 클래스에 쉽게 추가할 수 있습니다.

MFC는 `CArchive` serialize 할 개체와 저장 미디어 사이에서 클래스의 개체를 매개 변수로 사용 합니다. 이 개체는 항상 개체와 연결 되며,이 개체는 `CFile` 파일 이름 및 요청 된 작업이 읽기 또는 쓰기 인지 여부를 비롯 하 여 serialization에 필요한 정보를 가져옵니다. Serialization 작업을 수행 하는 개체는 `CArchive` 저장소 미디어의 특성에 관계 없이 개체를 사용할 수 있습니다.

`CArchive`개체는 오버 로드 된 삽입 ( **<\<**) and extraction (**>>** ) 연산자를 사용 하 여 쓰기 및 읽기 작업을 수행 합니다. 자세한 내용은 Serialization: 개체 Serialize 문서에서 [보관을 통해 CObjects 저장 및 로드](../mfc/storing-and-loading-cobjects-via-an-archive.md) 를 참조 하세요.

> [!NOTE]
> `CArchive`형식이 지정 된 텍스트에만 사용 되는 범용 iostream 클래스와 클래스를 혼동 하지 마십시오. `CArchive`클래스는 이진 형식의 직렬화 된 개체에 대 한 클래스입니다.

원하는 경우 MFC serialization을 무시 하 여 영구 데이터 저장소에 대 한 메커니즘을 직접 만들 수 있습니다. 사용자의 명령에서 serialization을 시작 하는 클래스 멤버 함수를 재정의 해야 합니다. ID_FILE_OPEN, ID_FILE_SAVE 및 ID_FILE_SAVE_AS 표준 명령의 [기술 참고 22](../mfc/tn022-standard-commands-implementation.md) 에서 설명을 참조 하세요.

다음 문서는 serialization에 필요한 두 가지 주요 작업을 다룹니다.

- [Serialization: Serialize 가능한 클래스 만들기](../mfc/serialization-making-a-serializable-class.md)

- [Serialization: 개체 직렬화](../mfc/serialization-serializing-an-object.md)

Serialization [: serialization 및 데이터베이스 입/출력](../mfc/serialization-serialization-vs-database-input-output.md) 문서에서는 serialization이 데이터베이스 응용 프로그램에서 적절 한 입/출력 기술인 경우를 설명 합니다.

## <a name="see-also"></a>참고 항목

[개념](../mfc/mfc-concepts.md)<br/>
[일반 MFC 항목](../mfc/general-mfc-topics.md)<br/>
[CArchive 클래스](../mfc/reference/carchive-class.md)<br/>
[CObject 클래스](../mfc/reference/cobject-class.md)<br/>
[CDocument 클래스](../mfc/reference/cdocument-class.md)<br/>
[CFile 클래스](../mfc/reference/cfile-class.md)
