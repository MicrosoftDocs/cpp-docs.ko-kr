---
title: CHAIN_PROPERTY_SET | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CHAIN_PROPERTY_SET
dev_langs:
- C++
helpviewer_keywords:
- CHAIN_PROPERTY_SET macro
ms.assetid: 2bcf6d7d-f4e5-480d-9140-1e32a0994c94
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 9db57535f3f0bc7653c80b83c3e0115727eed707
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/04/2018
---
# <a name="chainpropertyset"></a>CHAIN_PROPERTY_SET
이 매크로 속성 그룹을 함께 연결 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
CHAIN_PROPERTY_SET(ChainClass)  
  
```  
  
#### <a name="parameters"></a>매개 변수  
 *ChainClass*  
 [in] 체인 속성에 대 한 클래스의 이름입니다. 지도 (예: 세션, 명령 또는 데이터 원본 개체 클래스)에 이미 있는 ATL 프로젝트 마법사에 의해 생성 된 클래스입니다.  
  
## <a name="remarks"></a>설명  
 사용자 고유의 클래스를 다른 클래스에서 속성 집합을 연결 다음 속성을 클래스에서 직접 액세스할 수 있습니다.  
  
> [!CAUTION]
>  이 매크로 제한적으로 사용 합니다. 잘못 사용 하면 소비자는 OLE DB 적합성 테스트 실패 수를 발생할 수 있습니다.  
  
## <a name="requirements"></a>요구 사항  
 **헤더:** atldb.h  
  
## <a name="see-also"></a>참고 항목  
 [OLE DB 공급자 템플릿에 대한 매크로](../../data/oledb/macros-for-ole-db-provider-templates.md)