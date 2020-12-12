---
description: '자세한 정보: 다른 테이블에 행에 대 한 참조가 포함 된 경우 열 업데이트'
title: 다른 테이블에 해당 행에 대 한 참조가 포함 되어 있는 경우 열을 업데이트 합니다.
ms.date: 10/24/2018
helpviewer_keywords:
- rowsets, column updates
ms.assetid: abb5db69-055d-431f-b12d-ad2940a661ba
ms.openlocfilehash: 5c4562aaaa435c9745bedd146c04c98158d50cc5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97272619"
---
# <a name="updating-a-column-when-another-table-contains-a-reference-to-the-row"></a>다른 테이블에 행에 대한 참조가 들어 있는 경우의 열 업데이트

일부 공급자는 행에서 변경 된 열을 검색할 수 있지만 많은 공급자는 그렇지 않습니다. 따라서 업데이트 하려는 행에 대 한 참조가 있는 경우 열을 업데이트 하면 오류가 발생할 수 있습니다. 이 문제를 해결 하려면 변경할 열만 포함 하는 별도의 접근자를 만듭니다. 해당 접근자의 수를에 전달 `SetData` 합니다.

## <a name="see-also"></a>참고 항목

[접근자 사용](../../data/oledb/using-accessors.md)
