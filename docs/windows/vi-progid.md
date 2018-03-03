---
title: vi_progid | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- vc-attr.vi_progid
dev_langs:
- C++
helpviewer_keywords:
- vi_progid attribute
ms.assetid: a52449be-b93e-4111-b883-44bb8da53261
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b7581a4a10d9f101526aeb1a17ba7e26c4646b39
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/21/2017
---
# <a name="viprogid"></a>vi_progid
버전 독립 ProgID 형태의 지정합니다.  
  
## <a name="syntax"></a>구문  
  
```  
  
      [ vi_progid(  
   name  
) ];  
```  
  
#### <a name="parameters"></a>매개 변수  
 *name*  
 개체를 나타내는 버전 독립 ProgID입니다.  
  
 Progid의 CLSID (클래스 식별자) COM/ActiveX 개체를 식별 하는 데의 이해 하기 쉬운 버전을 제공 합니다.  
  
## <a name="remarks"></a>설명  
 **vi_progid** c + + 특성을 사용 하면 COM 개체에 대 한 버전 독립 ProgID를 지정 합니다. ProgID에 형식은 *name1.name2.version*합니다. 버전 종속 ProgID가 없습니다는 *버전*합니다. 둘 다 지정할 수는 **progid** 및 **vi_progid** 특성은 coclass의 합니다. 지정 하지 않으면 **vi_progid**, 버전 독립 ProgID가 지정 된 값은 [progid](../windows/progid.md) 특성입니다.  
  
 **vi_progid** 의미는 **coclass** 지정 하는 경우, 즉 특성 **vi_progid**, 지정과 같은 작업을 이기는 **coclass** 및 **vi_progid** 특성입니다.  
  
 **vi_progid** 특성을 사용 하면 클래스를 지정 된 이름에 자동으로 등록 해야 합니다. 생성된 된.idl 파일 ProgID 값이 표시 됩니다.  
  
 ATL 프로젝트의 경우는 [coclass](../windows/coclass.md) 특성도, 지정된 된 ProgID에서 사용 되는 **GetVersionIndependentProgID** 함수 (의해 삽입 된는 **coclass** 특성)입니다.  
  
## <a name="example"></a>예  
 참조는 [coclass](../windows/coclass.md) 의 샘플 사용에 대 한 예제 **vi_progid**합니다.  
  
## <a name="requirements"></a>요구 사항  
  
### <a name="attribute-context"></a>특성 컨텍스트  
  
|||  
|-|-|  
|**적용 대상**|**class**, `struct`|  
|**반복 가능**|아니요|  
|**필수 특성**|없음|  
|**잘못된 특성**|없음|  
  
 특성 컨텍스트에 대한 자세한 내용은 [특성 컨텍스트](../windows/attribute-contexts.md)를 참조하세요.  
  
## <a name="see-also"></a>참고 항목  
 [IDL 특성](../windows/idl-attributes.md)   
 [Typedef, Enum, Union 및 Struct 특성](../windows/typedef-enum-union-and-struct-attributes.md)   
 [클래스 특성](../windows/class-attributes.md)   
 [ProgID 키](http://msdn.microsoft.com/library/windows/desktop/dd542719)   
