---
description: ODBC 및 데이터베이스 클래스에 대해 자세히 알아보세요.
title: ODBC 및 데이터베이스 클래스
ms.date: 11/04/2016
helpviewer_keywords:
- database classes [C++], ODBC
- ODBC API functions [C++]
- ODBC classes [C++], MFC database classes
- MFC [C++], ODBC and
ms.assetid: b166f82d-6f85-4556-aac8-fb851235d22c
ms.openlocfilehash: 146170ddd97dfc2797fd1f755459f370be638ded
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97326772"
---
# <a name="odbc-and-the-database-classes"></a>ODBC 및 데이터베이스 클래스

MFC ODBC 데이터베이스 클래스는 일반적으로 [CDatabase](../../mfc/reference/cdatabase-class.md) 및 [CRecordset](../../mfc/reference/crecordset-class.md) 클래스의 멤버 함수에서 직접 수행 하는 odbc API 함수 호출을 캡슐화 합니다. 예를 들어 복잡 한 ODBC 호출 시퀀스, 반환 된 레코드를 저장소 위치에 바인딩, 오류 조건 처리 및 기타 작업은 데이터베이스 클래스에 의해 관리 됩니다. 따라서 매우 간단한 클래스 인터페이스를 사용 하 여 레코드 집합 개체를 통해 레코드를 조작할 수 있습니다.

> [!NOTE]
> ODBC 데이터 원본은이 항목에서 설명 하는 MFC ODBC 클래스 또는 MFC DAO (Data Access Object) 클래스를 통해 액세스할 수 있습니다.

데이터베이스 클래스는 ODBC 기능을 캡슐화 하지만 ODBC API 함수의 일 대 일 매핑을 제공 하지 않습니다. 데이터베이스 클래스는 Microsoft Access 및 Microsoft Visual Basic에서 데이터 액세스 개체를 찾은 후 모델링 된 높은 수준의 추상화를 제공 합니다. 자세한 내용은 [ODBC 및 MFC](../../data/odbc/odbc-and-mfc.md)를 참조 하세요.

## <a name="see-also"></a>참고 항목

[ODBC 기본 사항](../../data/odbc/odbc-basics.md)
