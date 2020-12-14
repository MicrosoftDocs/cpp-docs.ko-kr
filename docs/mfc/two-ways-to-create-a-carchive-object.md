---
description: '자세한 정보: CArchive 개체를 만드는 두 가지 방법'
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
ms.openlocfilehash: 21a4321eef2d93cf0b37d157f57e12fa1ba940c8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97263857"
---
# <a name="two-ways-to-create-a-carchive-object"></a>CArchive 개체를 만드는 두 가지 방법

개체를 만드는 방법에는 두 가지가 있습니다 `CArchive` .

- [프레임 워크를 통해 CArchive 개체의 암시적 생성](#_core_implicit_creation_of_a_carchive_object_via_the_framework)

- [CArchive 개체의 명시적 생성](#_core_explicit_creation_of_a_carchive_object)

## <a name="implicit-creation-of-a-carchive-object-via-the-framework"></a><a name="_core_implicit_creation_of_a_carchive_object_via_the_framework"></a> 프레임 워크를 통해 CArchive 개체의 암시적 생성

가장 일반적이 고 가장 쉬운 방법은 `CArchive` 파일 메뉴에서 저장, 다른 이름으로 저장 및 열기 명령을 대신 하 여 프레임 워크가 문서에 대 한 개체를 만들도록 하는 것입니다.

응용 프로그램의 사용자가 파일 메뉴에서 다른 이름으로 저장 명령을 실행 하는 경우 프레임 워크에서 수행 하는 작업은 다음과 같습니다.

1. 다른 이름 **으로 저장** 대화 상자를 표시 하 고 사용자의 파일 이름을 가져옵니다.

1. 사용자가 명명 한 파일을 `CFile` 개체로 엽니다.

1. `CArchive`이 개체를 가리키는 개체를 만듭니다 `CFile` . 개체를 만들 때 `CArchive` 프레임 워크는 "load" (읽기, deserialize)와는 반대로 모드를 "store" (write, serialize)로 설정 합니다.

1. `Serialize`파생 클래스에 정의 된 함수를 호출 `CDocument` 하 여 개체에 대 한 참조를 전달 `CArchive` 합니다.

`Serialize`그러면 문서 함수는 잠시 설명 된 대로 데이터를 개체에 씁니다 `CArchive` . 함수에서 반환 될 때 `Serialize` 프레임 워크는 `CArchive` 개체와 개체를 소멸 시킵니다 `CFile` .

따라서 프레임 워크에서 `CArchive` 문서에 대 한 개체를 만들 수 있도록 하려면 `Serialize` 보관 파일에서 쓰고 읽는 문서 함수를 구현 하면 됩니다. 또한 `Serialize` `CObject` 문서 함수에서 직접 또는 간접적으로 serialize 하는 모든 파생 개체에 대해를 구현 해야 `Serialize` 합니다.

## <a name="explicit-creation-of-a-carchive-object"></a><a name="_core_explicit_creation_of_a_carchive_object"></a> CArchive 개체의 명시적 생성

프레임 워크를 통해 문서를 serialize 하는 것 외에도 개체가 필요할 수 있는 경우가 있습니다 `CArchive` . 예를 들어 개체로 표시 되는 클립보드에서 데이터를 serialize 할 수 있습니다 `CSharedFile` . 또는 프레임 워크에서 제공 하는 것과 다른 파일을 저장 하기 위해 사용자 인터페이스를 사용 하는 것이 좋습니다. 이 경우 개체를 명시적으로 만들 수 있습니다 `CArchive` . 다음 절차를 사용 하 여 프레임 워크에서 수행 하는 것과 동일한 방식으로이 작업을 수행 합니다.

#### <a name="to-explicitly-create-a-carchive-object"></a>CArchive 개체를 명시적으로 만들려면

1. `CFile`에서 파생 된 개체 또는 개체를 생성 `CFile` 합니다.

1. `CFile`다음 예제와 같이 개체를의 생성자에 전달 합니다 `CArchive` .

   [!code-cpp[NVC_MFCSerialization#5](../mfc/codesnippet/cpp/two-ways-to-create-a-carchive-object_1.cpp)]

   생성자에 대 한 두 번째 인수는 `CArchive` 파일에 대 한 데이터를 저장 하거나 로드 하는 데 보관을 사용할지 여부를 지정 하는 열거형 값입니다. `Serialize`개체의 함수는 `IsStoring` 보관 개체에 대해 함수를 호출 하 여이 상태를 확인 합니다.

개체에서 데이터를 저장 하거나 로드 하는 작업이 완료 되 면 해당 데이터를 `CArchive` 닫습니다. `CArchive`(및 `CFile` ) 개체는 보관 파일 (및 파일)을 자동으로 닫도록 하지만 오류를 쉽게 복구할 수 있기 때문에 명시적으로이 작업을 수행 하는 것이 좋습니다. 오류 처리에 대 한 자세한 내용은 예외 [: 예외 catch 및 삭제](../mfc/exceptions-catching-and-deleting-exceptions.md)문서를 참조 하세요.

#### <a name="to-close-the-carchive-object"></a>CArchive 개체를 닫으려면

1. 다음 예제에서는 개체를 닫는 방법을 보여 줍니다 `CArchive` .

   [!code-cpp[NVC_MFCSerialization#6](../mfc/codesnippet/cpp/two-ways-to-create-a-carchive-object_2.cpp)]

## <a name="see-also"></a>참고 항목

[Serialization: 개체 직렬화](../mfc/serialization-serializing-an-object.md)
