---
description: '자세히 알아보기: CDocument에서 문서 클래스 파생'
title: CDocument에서 문서 클래스 파생시키기
ms.date: 11/04/2016
helpviewer_keywords:
- CDocument class [MFC], deriving from
- classes [MFC], deriving from CDocument
- document objects [MFC], derived
- derived classes [MFC], functions often overridden
- document classes [MFC], functions often overridden
ms.assetid: e6a198e0-9799-43c0-83c5-04174d8b532c
ms.openlocfilehash: 9f6dccb5400ba0e62b2f11a3c2d4074cb9bb2f25
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97327882"
---
# <a name="deriving-a-document-class-from-cdocument"></a>CDocument에서 문서 클래스 파생시키기

문서는 응용 프로그램의 데이터를 포함 하 고 관리 합니다. MFC 응용 프로그램 마법사에서 제공 하는 문서 클래스를 사용 하려면 다음을 수행 해야 합니다.

- `CDocument`각 문서 형식에 대해에서 클래스를 파생 시킵니다.

- 각 문서의 데이터를 저장할 멤버 변수를 추가 합니다.

- `CDocument` `Serialize` 문서 클래스의 멤버 함수를 재정의 합니다. `Serialize` 문서 데이터를 디스크에 쓰고 디스크에서 읽습니다.

## <a name="other-document-functions-often-overridden"></a>자주 재정의 되는 기타 문서 함수

다른 멤버 함수를 재정의할 수도 있습니다 `CDocument` . 특히 동적으로 할당 된 데이터를 삭제 하기 위해 문서 데이터 멤버 및 [DeleteContents](reference/cdocument-class.md#deletecontents) 를 초기화 하려면 [Onnewdocument](reference/cdocument-class.md#onnewdocument) 및 [onopendocument](reference/cdocument-class.md#onopendocument) 를 재정의 해야 합니다. 재정의 가능한 멤버에 대 한 자세한 내용은 *MFC 참조* 의 클래스 [CDocument](reference/cdocument-class.md) 를 참조 하세요.

## <a name="see-also"></a>참고 항목

[문서 사용](using-documents.md)
