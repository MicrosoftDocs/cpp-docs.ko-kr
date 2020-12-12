---
description: '자세한 정보: Session 개체 인터페이스'
title: Session 개체 인터페이스
ms.date: 11/19/2018
helpviewer_keywords:
- session objects [OLE DB]
- session objects [OLE DB], interfaces
- OLE DB provider templates, object interfaces
- interfaces, session object
- interfaces, list of
ms.assetid: ac01a958-6dde-4bd7-8b63-94459e488335
ms.openlocfilehash: dc4f5644258b0ced4c97a5cda6de1b69abb8c2f1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97286581"
---
# <a name="session-object-interfaces"></a>Session 개체 인터페이스

다음 표에서는 세션 개체에 대 한 OLE DB에 의해 정의 된 필수 및 선택적 인터페이스를 보여 줍니다.

|인터페이스|필수 여부|OLE DB 템플릿에서 구현 됩니까?|
|---------------|---------------|--------------------------------------|
|[IGetDataSource](/previous-versions/windows/desktop/ms709721(v=vs.85))|필수|예|
|[IOpenRowset](/previous-versions/windows/desktop/ms716946(v=vs.85))|필수|예|
|[ISessionProperties](/previous-versions/windows/desktop/ms713721(v=vs.85))|필수|예|
|[IAlterIndex](/previous-versions/windows/desktop/ms714943(v=vs.85))|선택 사항|아니요|
|[IAlterTable](/previous-versions/windows/desktop/ms719764(v=vs.85))|선택 사항|아니요|
|[IBindResource](/previous-versions/windows/desktop/ms714936(v=vs.85))|선택 사항|아니요|
|[ICreateRow](/previous-versions/windows/desktop/ms716832(v=vs.85))|선택 사항|아니요|
|[IDBCreateCommand](/previous-versions/windows/desktop/ms711625(v=vs.85))|선택 사항|예|
|[IDBSchemaRowset](/previous-versions/windows/desktop/ms713686(v=vs.85))|선택 사항|예|
|[IIndexDefinition](/previous-versions/windows/desktop/ms711593(v=vs.85))|선택 사항|아니요|
|[ISupportErrorInfo](/previous-versions/windows/desktop/ms715816(v=vs.85))|선택 사항|예|
|[ITableCreation](/previous-versions/windows/desktop/ms713639(v=vs.85))|선택 사항|아니요|
|[ITableDefinition](/previous-versions/windows/desktop/ms714277(v=vs.85))|선택 사항|아니요|
|[ITableDefinitionWithConstraints](/previous-versions/windows/desktop/ms720947(v=vs.85))|선택 사항|아니요|
|[ITransaction](/previous-versions/windows/desktop/ms723053(v=vs.85))|선택 사항|아니요|
|[ITransactionJoin](/previous-versions/windows/desktop/ms718071(v=vs.85))|선택 사항|아니요|
|[ITransactionLocal](/previous-versions/windows/desktop/ms714893(v=vs.85))|선택 사항|아니요|
|[ITransactionObject](/previous-versions/windows/desktop/ms713659(v=vs.85))|선택 사항|아니요|

Session 개체는 행 집합 개체를 만듭니다. 공급자가 명령을 지 원하는 경우에도 세션에서 명령 개체 ( `CCommand` OLE DB 구현)를 만듭니다 `TCommand` . `ICommand`다음 그림에 표시 된 것 처럼 command 개체는 인터페이스를 구현 하 고 메서드를 사용 하 여 `ICommand::Execute` 행 집합에서 명령을 실행 합니다.

![공급자 개념적 다이어그램](../../data/oledb/media/vc4u551.gif "공급자 개념 다이어그램")

## <a name="see-also"></a>참고 항목

[OLE DB 공급자 템플릿 아키텍처](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
