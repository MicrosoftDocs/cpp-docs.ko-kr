---
description: '자세한 정보: 고객에 게 ODBC 구성 요소 재배포'
title: 고객에게 ODBC 구성 요소 재배포
ms.date: 11/04/2016
helpviewer_keywords:
- ODBC components, redistributing
- ODBC, distributing components
- components [C++], distributing
- ODBC Administrator
- components [C++]
- components [C++], redistributing
ms.assetid: 17b065b4-a307-4b89-99ac-d05831cfab87
ms.openlocfilehash: 02840156d648507065e0cadb1b8fa2b9c8146a7a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97204318"
---
# <a name="redistributing-odbc-components-to-your-customers"></a>고객에게 ODBC 구성 요소 재배포

ODBC 관리자 프로그램의 기능을 응용 프로그램에 통합 하는 경우에도 이러한 프로그램을 실행 하는 파일을 사용자에 게 배포 해야 합니다. 이러한 ODBC 파일은 Visual C++ CD-ROM의 \OS\System 디렉터리에 있습니다. Redistrb 파일 및 동일한 디렉터리의 사용권 계약에는 재배포할 수 있는 ODBC 파일 목록이 포함 되어 있습니다.

제공 하려는 ODBC 드라이버에 대 한 설명서를 참조 하세요. 제공할 Dll 및 기타 파일을 결정 해야 합니다. Odbc 구성 요소를 재배포 하는 방법을 설명 하는 [고객에 게 Odbc 구성 요소 재배포](../../data/odbc/redistributing-odbc-components-to-your-customers.md)를 읽어야 합니다.

또한 대부분의 경우 다른 파일 하나를 포함 해야 합니다. ODBC 커서 라이브러리 Odbccr32.dll입니다. 이 라이브러리는 수준 1 드라이버에 전달 및 뒤로 스크롤 기능을 제공 합니다. 또한 스냅숏을 지 원하는 기능을 제공 합니다. ODBC 커서 라이브러리에 대 한 자세한 내용은 odbc [: Odbc 커서 라이브러리](../../data/odbc/odbc-the-odbc-cursor-library.md)를 참조 하십시오.

다음 항목에서는 ODBC를 데이터베이스 클래스와 함께 사용 하는 방법에 대해 자세히 설명 합니다.

- [ODBC: ODBC 커서 라이브러리](../../data/odbc/odbc-the-odbc-cursor-library.md)

- [ODBC: ODBC 데이터 원본 구성](../../data/odbc/odbc-configuring-an-odbc-data-source.md)

- [ODBC: ODBC API 함수 직접 호출](../../data/odbc/odbc-calling-odbc-api-functions-directly.md)

## <a name="see-also"></a>참고 항목

[ODBC 기본 사항](../../data/odbc/odbc-basics.md)<br/>
[ODBC 관리자](../../data/odbc/odbc-administrator.md)
