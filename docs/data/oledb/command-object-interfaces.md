---
description: '자세한 정보: Command 개체 인터페이스'
title: Command 개체 인터페이스
ms.date: 10/24/2018
helpviewer_keywords:
- command object interfaces [C++]
- command objects [OLE DB]
- OLE DB [C++], command object interfaces
ms.assetid: dacff5ae-252c-4f20-9ad7-4e602cc48536
ms.openlocfilehash: 07dce6a71e7afd3a47c63942d48dd78d758103f8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97307524"
---
# <a name="command-object-interfaces"></a>Command 개체 인터페이스

Command 개체는 인터페이스를 사용 하 여 `IAccessor` 매개 변수 바인딩을 지정 합니다. 소비자는 `IAccessor::CreateAccessor` 를 호출 하 여 구조체의 배열을 전달 `DBBINDING` 합니다. `DBBINDING` 열 바인딩에 대 한 정보 (예: 형식 및 길이)를 포함 합니다. 공급자는 구조를 수신 하 고 데이터가 전송 되는 방법 및 변환이 필요한 지 여부를 결정 합니다.

`ICommandText`인터페이스는 텍스트 명령을 지정 하는 방법을 제공 합니다. `ICommandProperties`인터페이스는 모든 명령 속성을 처리 합니다.

## <a name="see-also"></a>참고 항목

[OLE DB 공급자 템플릿 아키텍처](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
