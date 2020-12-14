---
description: '자세한 정보: CArchive &lt; &lt; 및 &gt; &gt; 연산자 사용'
title: CArchive &lt; &lt; 및 &gt; &gt; 연산자 사용
ms.date: 11/04/2016
helpviewer_keywords:
- objects [MFC], loading from previously stored values
- CArchive class [MFC], storing and loading objects
- CArchive class [MFC], operators
ms.assetid: 56aef326-02dc-4992-8282-f0a4b78a064e
ms.openlocfilehash: a3e6d65ac2ff024f779edb6d23a43f7331628c3b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97314570"
---
# <a name="using-the-carchive-ltlt-and-gtgt-operators"></a>CArchive &lt; &lt; 및 &gt; &gt; 연산자 사용

`CArchive` 는 \< and > 파일에 대 한 단순 데이터 형식과 파일의 쓰기 및 읽기를 위한 <> 연산자를 제공 `CObject` 합니다.

#### <a name="to-store-an-object-in-a-file-via-an-archive"></a>보관 파일을 통해 개체를 파일에 저장 하려면

1. 다음 예제에서는 보관 파일을 통해 개체를 파일에 저장 하는 방법을 보여 줍니다.

   [!code-cpp[NVC_MFCSerialization#7](../mfc/codesnippet/cpp/using-the-carchive-output-and-input-operators_1.cpp)]

#### <a name="to-load-an-object-from-a-value-previously-stored-in-a-file"></a>이전에 파일에 저장 된 값에서 개체를 로드 하려면

1. 다음 예제에서는 이전에 파일에 저장 된 값에서 개체를 로드 하는 방법을 보여 줍니다.

   [!code-cpp[NVC_MFCSerialization#8](../mfc/codesnippet/cpp/using-the-carchive-output-and-input-operators_2.cpp)]

일반적으로 `Serialize` `CObject` DECLARE_SERIALIZE 매크로를 사용 하 여 선언 해야 하는 파생 클래스의 함수에서 보관 파일을 통해 데이터를 저장 하 고 로드 합니다. 개체에 대 한 참조가 `CArchive` 함수에 전달 됩니다 `Serialize` . 개체의 함수를 호출 하 여 `IsLoading` `CArchive` `Serialize` 파일에서 데이터를 로드 하거나 파일에 데이터를 저장 하기 위해 함수가 호출 되었는지 여부를 확인 합니다.

Serialize 할 수 있는 `Serialize` 파생 클래스의 함수는 `CObject` 일반적으로 다음과 같은 형식입니다.

[!code-cpp[NVC_MFCSerialization#9](../mfc/codesnippet/cpp/using-the-carchive-output-and-input-operators_3.cpp)]

위의 코드 템플릿은 `Serialize` 문서 (에서 파생 된 클래스)의 함수에 대해 하나의 응용 프로그램을 만드는 것과 정확 하 게 동일 합니다 `CDocument` . 이 코드 템플릿을 사용 하면 다음 예제와 같이 저장 하는 코드와 로드 코드가 항상 병렬로 수행 되기 때문에 보다 쉽게 검토할 수 있는 코드를 작성할 수 있습니다.

[!code-cpp[NVC_MFCSerialization#10](../mfc/codesnippet/cpp/using-the-carchive-output-and-input-operators_4.cpp)]

라이브러리는 **`<<`** 및 **`>>`** 연산자를 `CArchive` 첫 번째 피연산자로 정의 하 고 다음 데이터 형식 및 클래스 형식을 두 번째 피연산자로 정의 합니다.

:::row:::
   :::column span="":::
      `BYTE`\
      `CObject*`\
      `COleCurrency`\
      `COleDateTime`\
      `COleDateTimeSpan`
   :::column-end:::
   :::column span="":::
      `COleVariant`\
      `CString`\
      `CTime` 및 `CTimeSpan`\
      `Double`
   :::column-end:::
   :::column span="":::
      `DWORD`\
      `Float`\
      `Int`\
      `LONG`
   :::column-end:::
   :::column span="":::
      `POINT` 및 `CPoint`\
      `RECT` 및 `CRect`\
      `SIZE` 및 `CSize`\
      `WORD`
   :::column-end:::
:::row-end:::

> [!NOTE]
> 보관을 통해를 저장 하 고 로드 `CObject` 하려면 추가 고려 사항이 필요 합니다. 자세한 내용은 [보관을 통해 CObjects 저장 및 로드](../mfc/storing-and-loading-cobjects-via-an-archive.md)를 참조 하세요.

`CArchive` **`<<`** 및 **`>>`** 연산자는 항상 `CArchive` 첫 번째 피연산자 인 개체에 대 한 참조를 반환 합니다. 이렇게 하면 아래 그림과 같이 연산자를 연결할 수 있습니다.

[!code-cpp[NVC_MFCSerialization#11](../mfc/codesnippet/cpp/using-the-carchive-output-and-input-operators_5.cpp)]

## <a name="see-also"></a>참고 항목

[Serialization: 개체 직렬화](../mfc/serialization-serializing-an-object.md)
