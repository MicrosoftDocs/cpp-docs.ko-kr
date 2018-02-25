---
title: "다른 테이블의 행에 대 한 참조를 포함 하는 경우 열을 업데이트할 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- rowsets, column updates
ms.assetid: abb5db69-055d-431f-b12d-ad2940a661ba
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: a5b4d4c041e1a6ad0f40107ef2bfb71293c05e5d
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/23/2018
---
# <a name="updating-a-column-when-another-table-contains-a-reference-to-the-row"></a>다른 테이블에 행에 대한 참조가 들어 있는 경우의 열 업데이트
일부 공급자는 행 변경에는 열을 검색할 수 있지만 대부분의 공급자가 없습니다. 결과적으로 업데이트 하려고 하는 행에 대 한 참조가 있으면 때 열을 업데이트 하면 오류가 발생할 수 있습니다. 이 문제를 해결 하려면 변경 하려는 열만 포함 하는 별도 접근자를 만듭니다. 에 해당 접근자의 번호를 전달 `SetData`합니다.  
  
## <a name="see-also"></a>참고 항목  
 [접근자 사용](../../data/oledb/using-accessors.md)