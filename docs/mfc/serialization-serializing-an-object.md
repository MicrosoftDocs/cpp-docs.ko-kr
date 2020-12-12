---
description: '자세한 정보: Serialization: 개체 직렬화'
title: 'Serialization: 개체 Serialize'
ms.date: 11/04/2016
helpviewer_keywords:
- serializing objects [MFC]
- serialization [MFC], objects
- objects [MFC], serializing
ms.assetid: 1db772b1-ad55-4fcf-b133-126cca082510
ms.openlocfilehash: ec0782f7faa0d6400f40013925f4a53495a76c7e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97217475"
---
# <a name="serialization-serializing-an-object"></a>Serialization: 개체 Serialize

[Serialization: Serializable 클래스 만들기](../mfc/serialization-making-a-serializable-class.md) 문서에서는 클래스를 serialize 할 수 있도록 하는 방법을 보여 줍니다. Serializable 클래스를 만든 후에는 [CArchive](../mfc/reference/carchive-class.md) 개체를 통해 해당 클래스의 개체를 파일에서 serialize 할 수 있습니다. 이 문서는 다음 사항을 설명합니다.

- [CArchive 개체는 무엇 인가요?](../mfc/what-is-a-carchive-object.md)

- [CArchive를 만드는 두 가지 방법](../mfc/two-ways-to-create-a-carchive-object.md)

- [CArchive <\< and >> 연산자를 사용 하는 방법](../mfc/using-the-carchive-output-and-input-operators.md)

- [보관을 통해 CObjects 저장 및 로드](../mfc/storing-and-loading-cobjects-via-an-archive.md)

프레임워크를 통해 Serializable 문서에 대한 보관 저장소를 만들거나 명시적으로 `CArchive` 개체를 직접 만들 수 있습니다. 또는의 <> 연산자를 사용 하 여 파일 및 serialize 할 수 있는 개체 간에 데이터를 전송할 수 있으며, 경우에 따라 \< and > `CArchive` `Serialize` 파생 클래스의 함수를 호출 하 여 데이터를 전송할 수 있습니다 `CObject` .

## <a name="see-also"></a>참조

[serialization](../mfc/serialization-in-mfc.md)
