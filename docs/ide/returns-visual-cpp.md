---
title: '&lt;반환&gt; (Visual c + +) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- returns
- <returns>
dev_langs:
- C++
helpviewer_keywords:
- returns C++ XML tag
- <returns> C++ XML tag
ms.assetid: 5e3b0ed9-838d-4953-a93e-76d2d0a19fb9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7b9956299370b4a41ce725cf903ff2aefe55bf53
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/04/2018
---
# <a name="ltreturnsgt-visual-c"></a>&lt;반환&gt; (Visual c + +)
\<returns> 태그는 메서드 선언의 주석에서 반환 값을 설명하는 데 사용해야 합니다.  
  
## <a name="syntax"></a>구문  
  
```  
<returns>description</returns>  
```  
  
#### <a name="parameters"></a>매개 변수  
 `description`  
 반환 값에 대한 설명입니다.  
  
## <a name="remarks"></a>설명  
 [/doc](../build/reference/doc-process-documentation-comments-c-cpp.md)로 컴파일하여 문서 주석을 파일로 처리합니다.  
  
## <a name="example"></a>예제  
  
```  
// xml_returns_tag.cpp  
// compile with: /LD /clr /doc  
// post-build command: xdcmake xml_returns_tag.dll  
  
/// Text for class MyClass.  
public ref class MyClass {  
public:  
   /// <returns>Returns zero.</returns>  
   int GetZero() { return 0; }  
};  
```  
  
## <a name="see-also"></a>참고 항목  
 [XML 문서](../ide/xml-documentation-visual-cpp.md)