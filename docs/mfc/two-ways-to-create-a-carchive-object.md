---
title: CArchive 개체를 만드는 두 가지 방법
ms.date: 11/04/2016
helpviewer_keywords:
- CArchive class [MFC], closing CArchive objects
- CArchive objects [MFC], closing
- I/O [MFC], creating CArchive objects
- serialization [MFC], CArchive class
- CArchive objects [MFC]
- storage [MFC], CArchive class [MFC]
- data storage [MFC], CArchive class
- CArchive class [MFC], constructor
ms.assetid: aefa28ce-b55c-40dc-9e42-5f038030985d
ms.openlocfilehash: 38642906b0973730149ed0de5381519f06d69fe5
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/17/2020
ms.locfileid: "79442032"
---
# <a name="two-ways-to-create-a-carchive-object"></a>CArchive 개체를 만드는 두 가지 방법

`CArchive` 개체를 만드는 방법에는 두 가지가 있습니다.

- [프레임 워크를 통해 CArchive 개체의 암시적 생성](#_core_implicit_creation_of_a_carchive_object_via_the_framework)

- [CArchive 개체의 명시적 생성](#_core_explicit_creation_of_a_carchive_object)

##  <a name="_core_implicit_creation_of_a_carchive_object_via_the_framework"></a>프레임 워크를 통해 CArchive 개체의 암시적 생성

가장 일반적이 고 가장 쉬운 방법은 파일 메뉴에서 저장, 다른 이름으로 저장 및 열기 명령을 대신 하 여 프레임 워크에서 문서에 대 한 `CArchive` 개체를 만들도록 하는 것입니다.

응용 프로그램의 사용자가 파일 메뉴에서 다른 이름으로 저장 명령을 실행 하는 경우 프레임 워크에서 수행 하는 작업은 다음과 같습니다.

1. 다른 이름 **으로 저장** 대화 상자를 표시 하 고 사용자의 파일 이름을 가져옵니다.

1. 사용자가 명명 한 파일을 `CFile` 개체로 엽니다.

1. 이 `CFile` 개체를 가리키는 `CArchive` 개체를 만듭니다. `CArchive` 개체를 만들 때 프레임 워크는 "load" (읽기, deserialize)와는 반대로 모드를 "store" (write, serialize)로 설정 합니다.

1. `CDocument`파생 클래스에 정의 된 `Serialize` 함수를 호출 하 여 `CArchive` 개체에 대 한 참조를 전달 합니다.

그러면 문서 `Serialize` 함수가 잠시 설명 된 대로 `CArchive` 개체에 데이터를 씁니다. `Serialize` 함수에서 반환 될 때 프레임 워크는 `CArchive` 개체와 `CFile` 개체를 소멸 시킵니다.

따라서 프레임 워크에서 문서에 대 한 `CArchive` 개체를 만들 수 있도록 하려면 보관 파일에 대해 쓰기 및 읽기 작업을 수행 하는 문서 `Serialize` 함수를 구현 하면 됩니다. 또한 문서 `Serialize` 함수에서 직접 또는 간접적으로 serialize 하는 `CObject`파생 개체에 대 한 `Serialize`를 구현 해야 합니다.

##  <a name="_core_explicit_creation_of_a_carchive_object"></a>CArchive 개체의 명시적 생성

프레임 워크를 통해 문서를 serialize 하는 것 외에도 `CArchive` 개체가 필요한 경우도 있습니다. 예를 들어 `CSharedFile` 개체로 표시 되는 클립보드에서 데이터를 serialize 할 수 있습니다. 또는 프레임 워크에서 제공 하는 것과 다른 파일을 저장 하기 위해 사용자 인터페이스를 사용 하는 것이 좋습니다. 이 경우 `CArchive` 개체를 명시적으로 만들 수 있습니다. 다음 절차를 사용 하 여 프레임 워크에서 수행 하는 것과 동일한 방식으로이 작업을 수행 합니다.

#### <a name="to-explicitly-create-a-carchive-object"></a>CArchive 개체를 명시적으로 만들려면

1. `CFile`에서 파생 된 개체 또는 `CFile` 개체를 생성 합니다.

1. 다음 예제와 같이 `CArchive`의 생성자에 `CFile` 개체를 전달 합니다.

   [!code-cpp[NVC_MFCSerialization#5](../mfc/codesnippet/cpp/two-ways-to-create-a-carchive-object_1.cpp)]

   `CArchive` 생성자에 대 한 두 번째 인수는 파일에 대 한 데이터를 저장 하거나 로드 하는 데 보관을 사용할지 여부를 지정 하는 열거형 값입니다. 개체의 `Serialize` 함수는 보관 개체에 대 한 `IsStoring` 함수를 호출 하 여이 상태를 확인 합니다.

`CArchive` 개체에서 데이터를 저장 하거나 로드 하는 작업이 완료 되 면 해당 데이터를 닫습니다. `CArchive` (및 `CFile`) 개체는 보관 파일 (및 파일)을 자동으로 닫도록 하지만 오류를 보다 쉽게 복구 하기 때문에 명시적으로이 작업을 수행 하는 것이 좋습니다. 오류 처리에 대 한 자세한 내용은 예외 [: 예외 catch 및 삭제](../mfc/exceptions-catching-and-deleting-exceptions.md)문서를 참조 하세요.

#### <a name="to-close-the-carchive-object"></a>CArchive 개체를 닫으려면

1. 다음 예제에서는 `CArchive` 개체를 닫는 방법을 보여 줍니다.

   [!code-cpp[NVC_MFCSerialization#6](../mfc/codesnippet/cpp/two-ways-to-create-a-carchive-object_2.cpp)]

## <a name="see-also"></a>참고 항목

[Serialization: 개체 Serialize](../mfc/serialization-serializing-an-object.md)
