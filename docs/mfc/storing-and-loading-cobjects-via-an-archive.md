---
description: '자세한 정보: 보관을 통해 CObjects 저장 및 로드'
title: 보관을 통해 CObject 저장 및 로드
ms.date: 11/04/2016
helpviewer_keywords:
- CObjects [MFC], loading through archives
- CArchive class [MFC], storing and loading objects
- Serialize method, vs. CArchive operators
- CObject class [MFC], CArchive objects
- CObjects [MFC]
ms.assetid: a829b6dd-bc31-47e0-8108-fbb946722db9
ms.openlocfilehash: c84c507fc556268eea526c1350211fd4b82f54fe
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97216563"
---
# <a name="storing-and-loading-cobjects-via-an-archive"></a>보관을 통해 CObject 저장 및 로드

보관을 통해를 저장 하 고 로드 `CObject` 하려면 추가 고려 사항이 필요 합니다. 개체의 함수를 호출 해야 하는 경우가 있습니다 `Serialize` . 여기서 개체는의 `CArchive` 연산자를 사용 하는 대신 호출의 매개 변수입니다 `Serialize` **<\<** or **>>** `CArchive` . 중요 한 점은 `CArchive` **>>** 운영자가 이전에 `CObject` `CRuntimeClass` 저장 된 보관 파일에 의해 파일에 기록 된 정보를 기반으로 메모리에을 생성 한다는 것입니다.

따라서 연산자를 사용 하는 경우 `CArchive` **<\<** and **>>** 와를 호출 하는 것 `Serialize` 은 이전에 저장 된 정보를 기반으로 개체를 동적으로 다시 생성 하기 위해 로드 보관 파일이 *필요한* 지 여부에 따라 달라 집니다 `CRuntimeClass` . `Serialize`다음 경우에 함수를 사용 합니다.

- 개체를 deserialize 할 때 개체의 정확한 클래스를 미리 알고 있습니다.

- 개체를 deserialize 할 때 해당 개체에 할당 된 메모리가 이미 있습니다.

> [!CAUTION]
> 함수를 사용 하 여 개체를 로드 하는 경우에 `Serialize` 도 함수를 사용 하 여 개체를 저장 해야 합니다 `Serialize` . 연산자를 사용 하 여 저장 하지 않은 다음 함수를 사용 하 여 로드 하거나 함수를 사용 하 여 `CArchive` **<<** `Serialize` 저장 한 `Serialize` 다음 using 연산자를 로드 `CArchive >>` 합니다.

다음 예에서는 사례를 보여 줍니다.

[!code-cpp[NVC_MFCSerialization#36](../mfc/codesnippet/cpp/storing-and-loading-cobjects-via-an-archive_1.h)]

[!code-cpp[NVC_MFCSerialization#37](../mfc/codesnippet/cpp/storing-and-loading-cobjects-via-an-archive_2.cpp)]

요약 하자면, serializable 클래스에서 포함 된를 멤버로 정의 하는 경우 `CObject`  `CArchive` **<\<** and **>>** 해당 개체에 대해 연산자를 사용 하지 말고 대신 함수를 호출 해야 합니다 `Serialize` . 또한 serializable 클래스에서 `CObject` (또는에서 파생 된 개체)에 대 한 포인터를 `CObject` 멤버로 정의 하지만 자체 생성자에서 다른 개체를 생성 하는 경우도 호출 해야 `Serialize` 합니다.

## <a name="see-also"></a>참고 항목

[Serialization: 개체 직렬화](../mfc/serialization-serializing-an-object.md)
