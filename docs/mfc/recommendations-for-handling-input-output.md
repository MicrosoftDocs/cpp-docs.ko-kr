---
description: '자세한 정보: 입력/출력 처리에 대 한 권장 사항'
title: Input-Output 처리에 대 한 권장 사항
ms.date: 11/04/2016
helpviewer_keywords:
- I/O [MFC], about I/O
- file-based I/O options
- I/O [MFC]
- I/O [MFC], options
- I/O [MFC], file-based options
ms.assetid: d664b175-3b4a-40c3-b14b-39de6b12e419
ms.openlocfilehash: c9a1acab50dc95f12d3002f54f4ab0819c041068
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97248491"
---
# <a name="recommendations-for-handling-inputoutput"></a>입력/출력 처리에 대한 권장 사항

파일 기반 i/o를 사용 하는지 여부는 다음 의사 결정 트리에서 질문에 응답 하는 방법에 따라 달라 집니다.

**응용 프로그램의 기본 데이터가 디스크 파일에 상주 합니까?**

- 예, 주 데이터는 디스크 파일에 있습니다.

   **응용 프로그램은 열려 있는 파일에서 전체 파일을 메모리로 읽어 온 후 파일을 저장할 때 전체 파일을 디스크에 다시 씁니다.**

  - 예: 기본 MFC 문서 사례입니다. `CDocument`Serialization을 사용 합니다.

  - 아니요: 일반적으로 파일에 대 한 트랜잭션 기반 업데이트의 경우입니다. 트랜잭션 별로 파일을 업데이트 하 고 serialization이 필요 하지 않습니다 `CDocument` .

- 아니요. 주 데이터는 디스크 파일에 상주 하지 않습니다.

   **데이터는 ODBC 데이터 원본에 상주 합니다.**

  - 예, 데이터는 ODBC 데이터 원본에 있습니다.

      MFC의 데이터베이스 지원을 사용 합니다. 이 사례에 대 한 표준 MFC 구현에는 `CDatabase` [Mfc: 문서 및 뷰와 함께 데이터베이스 클래스 사용](../data/mfc-using-database-classes-with-documents-and-views.md)문서에 설명 된 대로 개체가 포함 되어 있습니다. 응용 프로그램에서 보조 파일을 읽고 쓸 수도 있습니다. 즉, 응용 프로그램 마법사의 용도는 데이터베이스 뷰 및 파일 지원입니다. 이 경우 보조 파일에 대해 serialization을 사용 합니다.

  - 아니요. 데이터가 ODBC 데이터 원본에 없습니다.

      이 경우의 예: 데이터가 ODBC 이외의 DBMS에 있습니다. OLE 또는 DDE와 같은 다른 메커니즘을 통해 데이터를 읽습니다.

      이러한 경우 serialization을 사용 하지 않으며 응용 프로그램에 열기 및 저장 메뉴 항목이 없습니다. MFC ODBC 응용 프로그램에서 문서를 사용 하 여 개체를 저장 하는 것 처럼를 `CDocument` 홈 기반으로 사용할 수도 있습니다 `CRecordset` . 하지만 프레임 워크의 기본 파일 열기/저장 문서 serialization은 사용 하지 않습니다.

파일 메뉴에서 열기, 저장 및 다른 이름으로 저장 명령을 지원 하기 위해 프레임 워크는 문서 serialization을 제공 합니다. Serialization은 클래스에서 파생 된 개체를 포함 하 여 데이터를 읽고, `CObject` 일반적으로 디스크 파일을 영구 저장소로 씁니다. Serialization은 사용 하기 쉬우며 많은 요구를 제공 하지만 많은 데이터 액세스 응용 프로그램에는 적합 하지 않을 수 있습니다. 데이터 액세스 응용 프로그램은 일반적으로 트랜잭션 별로 데이터를 업데이트 합니다. 이는 한 번에 전체 데이터 파일을 읽고 쓰는 대신 트랜잭션의 영향을 받는 레코드를 업데이트 합니다.

Serialization에 대 한 자세한 내용은 [serialization](../mfc/serialization-in-mfc.md)을 참조 하세요.

## <a name="see-also"></a>참고 항목

[Serialization: Serialization과 데이터베이스 입/출력 비교](../mfc/serialization-serialization-vs-database-input-output.md)
