---
title: 'Synclockwithstatust:: Synclockwithstatust 생성자 | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockWithStatusT::SyncLockWithStatusT
dev_langs:
- C++
helpviewer_keywords:
- SyncLockWithStatusT, constructor
ms.assetid: 5d2fb820-ae1b-495f-8084-ebb4fecc3104
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 8f665866a43e45d6526aa33f17c05eacebdd84aa
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33891352"
---
# <a name="synclockwithstatustsynclockwithstatust-constructor"></a>SyncLockWithStatusT::SyncLockWithStatusT 생성자
WRL 인프라를 지원하며 사용자 코드에서 직접 사용할 수 없습니다.  
  
## <a name="syntax"></a>구문  
  
```  
SyncLockWithStatusT(  
   _Inout_ SyncLockWithStatusT&& other  
);  
  
explicit SyncLockWithStatusT(  
   typename SyncTraits::Type sync,  
   DWORD status  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `other`  
 다른 SyncLockWithStatusT 개체를 rvalue 참조입니다.  
  
 `sync`  
 다른 SyncLockWithStatusT 개체에 대 한 참조입니다.  
  
 `status`  
 값은 [status_](../windows/synclockwithstatust-status-data-member.md) 의 데이터 멤버는 `other` 매개 변수 또는 `sync` 매개 변수입니다.  
  
## <a name="remarks"></a>설명  
 SyncLockWithStatusT 클래스의 새 인스턴스를 초기화합니다.  
  
 첫 번째 생성자는 매개 변수에서 지정한 다른 SyncLockWithStatusT에서 현재 SyncLockWithStatusT 개체 `other`, 되 고 다음 다른 SyncLockWithStatusT 개체를 무효화 합니다. 두 번째 생성자는 `protected`, 유효 하지 않은 상태로 현재 SyncLockWithStatusT 개체를 초기화 합니다.  
  
## <a name="requirements"></a>요구 사항  
 **헤더:** corewrappers.h  
  
 **Namespace:** Microsoft::WRL::Wrappers::Details  
  
## <a name="see-also"></a>참고 항목  
 [SyncLockWithStatusT 클래스](../windows/synclockwithstatust-class.md)   
 [SyncLockWithStatusT::GetStatus 메서드](../windows/synclockwithstatust-getstatus-method.md)