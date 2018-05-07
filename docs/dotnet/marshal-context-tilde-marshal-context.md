---
title: 'marshal_context:: ~ marshal_context | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- marshal_context::~marshal_context
- msclr.interop.marshal_context.~marshal_context
- marshal_context.~marshal_context
- msclr::interop::marshal_context::~marshal_context
- ~marshal_context
dev_langs:
- C++
helpviewer_keywords:
- marshal_context class [C++], operations
ms.assetid: 34c41b38-4c33-4f61-b74e-831ac46b4ab5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: a6cb7ed3c7b1ee5b28c4943d83b6a8ca6166b6d0
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/04/2018
---
# <a name="marshalcontextmarshalcontext"></a>marshal_context::~marshal_context
`marshal_context` 개체를 제거합니다.  
  
## <a name="syntax"></a>구문  
  
```  
~marshal_context();  
```  
  
## <a name="remarks"></a>설명  
 데이터 변환 중 일부는 마샬링 컨텍스트가 필요합니다. 참조 [개요의 c + + 마샬링](../dotnet/overview-of-marshaling-in-cpp.md) 어떤 번역 컨텍스트에 필요한 및 응용 프로그램에 포함할 어떤 마샬링 파일에 대 한 자세한 내용은 합니다.  
  
 삭제 한 `marshal_context` 개체는 해당 컨텍스트에서 변환 된 데이터를 무효화 합니다. 이후에 데이터를 보존 하려는 경우는 `marshal_context` 개체가 소멸, 지속 되는 변수에 데이터를 수동으로 복사 해야 합니다.  
  
## <a name="requirements"></a>요구 사항  
 **헤더 파일:** \<msclr\marshal.h >, \<msclr\marshal_windows.h >, \<msclr\marshal_cppstd.h >, 또는 \<msclr\marshal_atl.h >  
  
 **Namespace:** msclr::interop  
  
## <a name="see-also"></a>참고 항목  
 [C + + 마샬링 개요](../dotnet/overview-of-marshaling-in-cpp.md)   
 [marshal_as](../dotnet/marshal-as.md)   
 [marshal_context 클래스](../dotnet/marshal-context-class.md)