---
description: 자세한 내용은 OLE DB 프로그래밍 개요를 확인 하세요.
title: OLE DB 프로그래밍 개요
ms.date: 10/22/2018
helpviewer_keywords:
- Universal Data Access
- OLE DB, about OLE DB
ms.assetid: a5a69730-2793-4277-a67d-6f3c8edab6df
ms.openlocfilehash: 1976d8717704fbacec4f9d249b8ca3664c2eeb56
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97317105"
---
# <a name="ole-db-programming-overview"></a>OLE DB 프로그래밍 개요

OLE DB는 고성능 COM 기반 데이터베이스 기술입니다. 이 클래스는 저장 된 형식에 관계 없이 데이터에 액세스 하는 일반적인 방법을 제공 합니다. 일반적인 비즈니스 상황에서 방대한 양의 정보는 회사 데이터베이스에 저장 되지 않습니다. 이 정보는 파일 시스템 (예: FAT 또는 NTFS), 인덱싱된 순차 파일, 개인 데이터베이스 (예: Access), 스프레드시트 (예: Excel), 프로젝트 계획 응용 프로그램 (예: 프로젝트), 전자 메일 (예: Outlook)에 있습니다. OLE DB를 사용 하면 데이터 저장소에 OLE DB 공급자가 있는 경우와 동일한 방식으로 모든 종류의 데이터 저장소에 액세스할 수 있습니다.

OLE DB를 사용 하면 DBMS 든 상관 없이 다양 한 데이터 원본에 액세스 하는 응용 프로그램을 개발할 수 있습니다. OLE DB는 지정 된 데이터 소스에 대 한 적절 한 DBMS 기능을 지 원하는 COM 인터페이스를 사용 하 여 유니버설 액세스를 가능 하 게 합니다. COM은 서비스의 불필요 한 중복을 줄이고 데이터 원본 뿐만 아니라 다른 응용 프로그램 간의 상호 운용성을 극대화 합니다.

## <a name="benefits-of-com"></a>COM의 이점

여기서 COM은에서 제공 됩니다. OLE DB은 COM 인터페이스 집합입니다. 균일 한 인터페이스 집합을 통해 데이터에 액세스 하 여 데이터베이스를 여러 구성 요소의 행렬로 구성할 수 있습니다.

COM 사양에 따라 OLE DB DBMS 기능에서 재사용 가능한 일관 된 부분을 고려 하 고 캡슐화 하는 확장 가능 하 고 유지 가능한 인터페이스 컬렉션을 정의 합니다. 이러한 인터페이스는 행 컨테이너, 쿼리 프로세서, 트랜잭션 코디네이터 등의 DBMS 구성 요소 경계를 정의 하 여 다양 한 정보 소스에 대 한 균일 한 트랜잭션 액세스를 가능 하 게 합니다.

## <a name="see-also"></a>참고 항목

[OLE DB 프로그래밍](../../data/oledb/ole-db-programming.md)<br/>
[OLE DB 소비자 템플릿](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[OLE DB 공급자 템플릿](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[OLE DB 템플릿](../../data/oledb/ole-db-templates.md)
