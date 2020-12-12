---
description: '자세한 정보: Serialization: Serialize 가능한 클래스 만들기'
title: 'Serialization: Serialize 가능한 클래스 만들기'
ms.date: 11/04/2016
helpviewer_keywords:
- serializable class [MFC]
- DECLARE_SERIAL macro [MFC]
- default constructor [MFC]
- VERSIONABLE_SCHEMA macro [MFC]
- classes [MFC], derived
- IMPLEMENT_SERIAL macro [MFC]
- no-arguments constructor [MFC]
- Serialize method, overriding
- defaults [MFC], constructor
- CObject class [MFC], deriving serializable classes
- constructors [MFC], defining with no arguments
- serialization [MFC], serializable classes
- no default constructor
ms.assetid: 59a14d32-1cc8-4275-9829-99639beee27c
ms.openlocfilehash: 21c45887199768094953066818acfe1b87d8d45d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97217538"
---
# <a name="serialization-making-a-serializable-class"></a>Serialization: Serialize 가능한 클래스 만들기

클래스를 serialize 할 수 있도록 하기 위해 5 가지 주요 단계가 필요 합니다. 아래에 나열 되어 있으며 다음 섹션에서 설명 합니다.

1. [CObject에서 클래스를 파생](#_core_deriving_your_class_from_cobject) 하거나에서 파생 된 클래스를 파생 시킵니다 `CObject` .

1. [Serialize 멤버 함수를 재정의](#_core_overriding_the_serialize_member_function)합니다.

1. 클래스 선언에서 [DECLARE_SERIAL 매크로 사용](#_core_using_the_declare_serial_macro) .

1. [인수를 사용 하지 않는 생성자를 정의](#_core_defining_a_constructor_with_no_arguments)합니다.

1. 클래스에 대 한 [구현 파일에서 IMPLEMENT_SERIAL 매크로 사용](#_core_using_the_implement_serial_macro_in_the_implementation_file) .

`Serialize` [CArchive](../mfc/reference/carchive-class.md)의 >> 및 << 연산자를 통하지 않고 직접 호출 하는 경우 직렬화에는 마지막 세 단계가 필요 하지 않습니다.

## <a name="deriving-your-class-from-cobject"></a><a name="_core_deriving_your_class_from_cobject"></a> CObject에서 클래스 파생

기본 serialization 프로토콜 및 기능은 클래스에서 정의 됩니다 `CObject` . `CObject`클래스의 다음 선언에 표시 된 것 처럼 (또는에서 파생 된 클래스)에서 클래스를 파생 시켜 `CObject` `CPerson` 의 serialization 프로토콜 및 기능에 액세스할 수 있습니다 `CObject` .

## <a name="overriding-the-serialize-member-function"></a><a name="_core_overriding_the_serialize_member_function"></a> Serialize 멤버 함수 재정의

`Serialize`클래스에 정의 된 멤버 함수는 `CObject` 실제로 개체의 현재 상태를 캡처하는 데 필요한 데이터를 serialize 합니다. `Serialize`함수는 `CArchive` 개체 데이터를 읽고 쓰는 데 사용 하는 인수를 포함 합니다. [CArchive](../mfc/reference/carchive-class.md) 개체에는 멤버 함수가 있습니다 `IsStoring` .이 함수는를 `Serialize` 저장 (데이터 쓰기) 또는 로드 (데이터 읽기) 할지 여부를 나타냅니다. 의 결과를 지침으로 사용 하 여 개체 `IsStoring` 에 삽입 연산자 ()를 사용 하 여 개체의 데이터를 삽입 `CArchive` **<\<**) or extract data with the extraction operator (**>>** 합니다.

에서 파생 되 `CObject` 고 두 개의 새 멤버 변수 (형식 및 단어)가 있는 클래스를 살펴보겠습니다 `CString` .  다음 클래스 선언 조각은 새 멤버 변수와 재정의 된 멤버 함수에 대 한 선언을 보여 줍니다 `Serialize` .

[!code-cpp[NVC_MFCSerialization#1](../mfc/codesnippet/cpp/serialization-making-a-serializable-class_1.h)]

#### <a name="to-override-the-serialize-member-function"></a>Serialize 멤버 함수를 재정의 하려면

1. 의 기본 클래스 버전을 호출 `Serialize` 하 여 개체의 상속 된 부분이 serialize 되는지 확인 합니다.

1. 클래스와 관련 된 멤버 변수를 삽입 하거나 추출 합니다.

   삽입 및 추출 연산자는 archive 클래스와 상호 작용 하 여 데이터를 읽고 씁니다. 다음 예제에서는 `Serialize` 위에 선언 된 클래스에 대해을 구현 하는 방법을 보여 줍니다 `CPerson` .

   [!code-cpp[NVC_MFCSerialization#2](../mfc/codesnippet/cpp/serialization-making-a-serializable-class_2.cpp)]

또한 [carchive:: Read](../mfc/reference/carchive-class.md#read) 및 [Carchive:: Write](../mfc/reference/carchive-class.md#write) 멤버 함수를 사용 하 여 많은 양의 형식화 되지 않은 데이터를 읽고 쓸 수 있습니다.

## <a name="using-the-declare_serial-macro"></a><a name="_core_using_the_declare_serial_macro"></a> DECLARE_SERIAL 매크로 사용

DECLARE_SERIAL 매크로는 다음과 같이 serialization을 지 원하는 클래스 선언에 필요 합니다.

[!code-cpp[NVC_MFCSerialization#3](../mfc/codesnippet/cpp/serialization-making-a-serializable-class_3.h)]

## <a name="defining-a-constructor-with-no-arguments"></a><a name="_core_defining_a_constructor_with_no_arguments"></a> 인수 없이 생성자 정의

MFC는 deserialize 될 때 (디스크에서 로드 됨) 개체를 다시 만들 때 기본 생성자가 필요 합니다. Deserialization 프로세스는 개체를 다시 만드는 데 필요한 값을 사용 하 여 모든 멤버 변수를 채웁니다.

이 생성자는 public, protected 또는 private로 선언할 수 있습니다. 이를 보호 하거나 비공개로 설정 하는 경우 serialization 함수 에서만 사용 되도록 하는 것이 좋습니다. 생성자는 필요에 따라 개체를 삭제할 수 있는 상태로 두어야 합니다.

> [!NOTE]
> DECLARE_SERIAL 및 IMPLEMENT_SERIAL 매크로를 사용 하는 클래스에서 인수가 없는 생성자를 정의 하는 것을 잊은 경우 IMPLEMENT_SERIAL 매크로를 사용 하는 줄에서 "기본 생성자를 사용할 수 없습니다." 컴파일러 경고가 발생 합니다.

## <a name="using-the-implement_serial-macro-in-the-implementation-file"></a><a name="_core_using_the_implement_serial_macro_in_the_implementation_file"></a> 구현 파일에서 IMPLEMENT_SERIAL 매크로 사용

IMPLEMENT_SERIAL 매크로는에서 serialize 할 수 있는 클래스를 파생 시키는 데 필요한 다양 한 함수를 정의 하는 데 사용 됩니다 `CObject` . 구현 파일 ()에서이 매크로를 사용 합니다. CPP)를 사용할 경우 매크로에 대 한 처음 두 인수는 클래스의 이름과 해당 직계 기본 클래스의 이름입니다.

이 매크로에 대 한 세 번째 인수는 스키마 번호입니다. 스키마 번호는 기본적으로 클래스의 개체에 대 한 버전 번호입니다. 스키마 번호에 대해 0 보다 크거나 같은 정수를 사용 하십시오. 이 스키마 번호는 데이터베이스 용어와 혼동 하지 마세요.

MFC serialization 코드는 개체를 메모리로 읽을 때 스키마 번호를 확인 합니다. 디스크에 있는 개체의 스키마 번호가 메모리에 있는 클래스의 스키마 번호와 일치 하지 않으면 라이브러리는를 throw `CArchiveException` 하 여 프로그램에서 잘못 된 버전의 개체를 읽지 못하게 합니다.

`Serialize`멤버 함수를 사용 하 여 여러 버전의 응용 프로그램을 사용 하 여 작성 된 파일을 읽을 수 있도록 하려면 *VERSIONABLE_SCHEMA* 값을 IMPLEMENT_SERIAL 매크로에 대 한 인수로 사용 합니다. 사용 정보 및 예제는 `GetObjectSchema` 클래스의 멤버 함수를 참조 하세요 `CArchive` .

다음 예제에서는에서 파생 된 클래스에 대해 IMPLEMENT_SERIAL를 사용 하는 방법을 보여 줍니다 `CPerson` `CObject` .

[!code-cpp[NVC_MFCSerialization#4](../mfc/codesnippet/cpp/serialization-making-a-serializable-class_4.cpp)]

Serializable 클래스를 만들었으면 [Serialization: 개체](../mfc/serialization-serializing-an-object.md)serialize 문서에서 설명한 대로 클래스의 개체를 serialize 할 수 있습니다.

## <a name="see-also"></a>참조

[serialization](../mfc/serialization-in-mfc.md)
