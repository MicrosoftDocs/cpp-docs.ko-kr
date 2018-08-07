---
title: CPtrList 클래스 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CPtrList
dev_langs:
- C++
helpviewer_keywords:
- lists, generic
- CPtrList class [MFC]
- generic lists
ms.assetid: 4139a09c-4338-4f42-9eea-51336120b43c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 36746c7979511890bb450c9204c0c7a908bbace3
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/05/2018
ms.locfileid: "37853896"
---
# <a name="cptrlist-class"></a>CPtrList 클래스
void 포인터 목록을 지원합니다.  
  
## <a name="syntax"></a>구문  
  
```  
class CPtrList : public CObject  
```  
  
## <a name="members"></a>멤버  
 멤버 함수 `CPtrList` 클래스의 멤버 함수와 비슷합니다 [CObList](../../mfc/reference/coblist-class.md)합니다. 이처럼 두 함수가 비슷하므로 `CObList` 참조 설명서에서 멤버 함수 관련 사항을 확인할 수 있습니다. 표시 될 때마다를 `CObject` 포인터를 함수 매개 변수 또는 반환 값에 대 한 포인터를 대체할 **void**합니다.  
  
 `CObject*& CObList::GetHead() const;`  
  
 예를 들어 위의 코드는  
  
 `void*& CPtrList::GetHead() const;`  
  
## <a name="remarks"></a>설명  
 `CPtrList` 통합 런타임 형식 액세스 및 대 한 덤핑을 지원 하기 위해 IMPLEMENT_DYNAMIC 매크로 `CDumpContext` 개체입니다. 개별 포인터 목록 요소의 덤프가 필요한 경우 덤프 컨텍스트 깊이는 1보다 크게 설정해야 합니다.  
  
 포인터 목록은 serialize할 수 없습니다.  
  
 `CPtrList` 개체를 삭제하거나 해당 요소를 제거할 경우 참조하는 엔터티가 아니라 포인터만 제거됩니다.  
  
 사용 하 여 대 한 자세한 내용은 `CPtrList`, 문서를 참조 하세요 [컬렉션](../../mfc/collections.md)합니다.  
  
## <a name="inheritance-hierarchy"></a>상속 계층  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CPtrList`  
  
## <a name="requirements"></a>요구 사항  
 **헤더:** afxcoll.h  
  
## <a name="see-also"></a>참고 항목  
 [CObject 클래스](../../mfc/reference/cobject-class.md)   
 [계층 구조 차트](../../mfc/hierarchy-chart.md)   
 [CObList 클래스](../../mfc/reference/coblist-class.md)
