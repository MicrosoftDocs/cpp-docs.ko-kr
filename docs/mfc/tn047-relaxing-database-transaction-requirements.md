---
description: '자세히 알아보기: TN047: 완화 Database 트랜잭션 요구 사항'
title: 'TN047: 데이터베이스 트랜잭션 요구 사항 완화'
ms.date: 11/04/2016
f1_keywords:
- vc.data
helpviewer_keywords:
- TN047
ms.assetid: f93c51cf-a8c0-43d0-aa47-7bcb8333d693
ms.openlocfilehash: 6f356db75df93466bc392e555246a363e6b52187
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97215120"
---
# <a name="tn047-relaxing-database-transaction-requirements"></a>TN047: 데이터베이스 트랜잭션 요구 사항 완화

MFC ODBC 데이터베이스 클래스의 트랜잭션 요구 사항에 대해 설명 된이 기술 정보는 이제 사용 되지 않습니다. MFC 4.2 이전에는 데이터베이스 클래스에서 **CommitTrans** 또는 **Rollback** 작업 후에도 커서를 레코드 집합에서 유지 해야 했습니다. ODBC 드라이버와 DBMS에서 이러한 수준의 커서 유지를 지원 하지 않는 경우 데이터베이스 클래스에서 트랜잭션을 사용 하도록 설정 하지 않은 것입니다.

MFC 4.2부터 데이터베이스 클래스는 커서 유지를 요구 하는 제한을 완화 했습니다. 드라이버가 지원 되는 경우 트랜잭션을 사용할 수 있습니다. 그러나 이제는 열린 레코드 집합에 대 한 **CommitTrans** 또는 **Rollback** 작업의 결과를 확인 해야 합니다. 자세한 내용은 멤버 함수 [CDatabase:: GetCursorCommitBehavior](../mfc/reference/cdatabase-class.md#getcursorcommitbehavior) 및 [Cdatabase:: GetCursorRollbackBehavior](../mfc/reference/cdatabase-class.md#getcursorrollbackbehavior) 를 참조 하세요.

## <a name="see-also"></a>참고 항목

[번호로 기술 참고 사항](../mfc/technical-notes-by-number.md)<br/>
[범주별 기술 참고 사항](../mfc/technical-notes-by-category.md)
