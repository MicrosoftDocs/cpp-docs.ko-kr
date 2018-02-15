---
title: 'Cdberrorinfo:: Geterrorrecords | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CDBErrorInfo.GetErrorRecords
- ATL.CDBErrorInfo.GetErrorRecords
- ATL::CDBErrorInfo::GetErrorRecords
- GetErrorRecords
- CDBErrorInfo::GetErrorRecords
dev_langs:
- C++
helpviewer_keywords:
- GetErrorRecords method
ms.assetid: 07746774-bcca-4833-8f55-a619e9777c17
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: a904eba0ae45186715fd8f7071d06db309c0a24c
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/14/2018
---
# <a name="cdberrorinfogeterrorrecords"></a>CDBErrorInfo::GetErrorRecords
지정된 된 개체에 대 한 오류 레코드를 가져옵니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT GetErrorRecords(IUnknown* pUnk,   
   const IID& iid,   
   ULONG* pcRecords) throw();  


HRESULT GetErrorRecords(ULONG* pcRecords) throw();  
```  
  
#### <a name="parameters"></a>매개 변수  
 *pUnk*  
 [in] 인터페이스를 가져올 오류 레코드에 대 한 개체입니다.  
  
 `iid`  
 [in] 오류와 연결 된 인터페이스의 IID입니다.  
  
 *pcRecords*  
 [out] 오류 레코드 수 (1부터 시작)에 대 한 포인터입니다.  
  
## <a name="return-value"></a>반환 값  
 표준 `HRESULT`입니다.  
  
## <a name="remarks"></a>설명  
 함수의 첫 번째 형태를 사용 하 여 오류 정보를 얻을 수 있는 인터페이스를 확인 하려는 경우. 두 번째 형태를 사용 하십시오.  
  
## <a name="requirements"></a>요구 사항  
 **헤더:** atldbcli.h  
  
## <a name="see-also"></a>참고 항목  
 [CDBErrorInfo 클래스](../../data/oledb/cdberrorinfo-class.md)