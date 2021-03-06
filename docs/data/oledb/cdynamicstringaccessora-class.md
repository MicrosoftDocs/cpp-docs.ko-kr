---
description: '자세히 알아보기: CDynamicStringAccessorA 클래스'
title: CDynamicStringAccessorA 클래스
ms.date: 11/04/2016
f1_keywords:
- CDynamicStringAccessorA
helpviewer_keywords:
- CDynamicStringAccessorA class
ms.assetid: ed0d9821-a655-41f1-a902-43c3042ac49c
ms.openlocfilehash: 45a4d10c8a50c4009151fa90e51172405047a21a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97170726"
---
# <a name="cdynamicstringaccessora-class"></a>CDynamicStringAccessorA 클래스

데이터베이스 스키마 (기본 구조)에 대해 알지 못하는 경우 데이터 원본에 액세스할 수 있습니다.

## <a name="syntax"></a>구문

```cpp
typedef CDynamicStringAccessorT<CHAR, DBTYPE_STR> CDynamicStringAccessorA;
```

## <a name="remarks"></a>설명

둘 다 공급자가 데이터 저장소에서 액세스 한 모든 데이터를 문자열 데이터로 인출 하도록 요청 하지만 `CDynamicStringAccessor` ANSI 문자열 데이터를 요청 합니다.

`CDynamicStringAccessorA` 는 `GetString` 및 `SetString` 에서 상속 `CDynamicStringAccessor` 됩니다. 개체에서 이러한 메서드를 사용 하 `CDynamicStringAccessorA` 는 경우 `BaseType` 은 **CHAR** 입니다.

## <a name="requirements"></a>요구 사항

**헤더**: atldbcli.h

## <a name="see-also"></a>참고 항목

[OLE DB 소비자 템플릿](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[OLE DB 소비자 템플릿 참조](../../data/oledb/ole-db-consumer-templates-reference.md)<br/>
[CAccessor 클래스](../../data/oledb/caccessor-class.md)<br/>
[CDynamicParameterAccessor 클래스](../../data/oledb/cdynamicparameteraccessor-class.md)<br/>
[CManualAccessor 클래스](../../data/oledb/cmanualaccessor-class.md)<br/>
[CDynamicAccessor 클래스](../../data/oledb/cdynamicaccessor-class.md)<br/>
[CDynamicStringAccessor 클래스](../../data/oledb/cdynamicstringaccessor-class.md)<br/>
