---
title: embedded_idl | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- embedded_idl
dev_langs:
- C++
helpviewer_keywords:
- embedded_idl attribute
ms.assetid: f1c1c2e8-3872-4172-8795-8d1288a20452
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b8a93f71da7b7f0819b5a48af1541909037bbe65
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/23/2018
---
# <a name="embeddedidl"></a>embedded_idl
**C + + 전용**  
  
 특성에서 생성된 코드를 유지한 상태에서 형식 라이브러리가 .tlh 파일에 작성되도록 지정합니다.  
  
## <a name="syntax"></a>구문  
  
```  
embedded_idl[("param")]  
```  
  
#### <a name="parameters"></a>매개 변수  
 `param`  
 다음 두 값 중 하나일 수 있습니다.  
  
-   emitidl: typelib에서 가져온 형식 정보가 특성 사용 프로젝트에 대해 생성된 IDL에 존재합니다.  `embedded_idl`에 대한 매개 변수를 지정하지 않는 경우 이 값이 기본값으로 적용됩니다.  
  
-   no_emitidl: typelib에서 가져온 형식 정보가 특성 사용 프로젝트에 대해 생성된 IDL에 존재하지 않습니다.  
  
## <a name="example"></a>예  
  
```  
// import_embedded_idl.cpp  
// compile with: /LD  
#include <windows.h>  
[module(name="MyLib2")];  
#import "\school\bin\importlib.tlb" embedded_idl("no_emitidl")  
```  
  
## <a name="remarks"></a>설명  
 **C + + 전용 종료**  
  
## <a name="see-also"></a>참고 항목  
 [#import 특성](../preprocessor/hash-import-attributes-cpp.md)   
 [#import Directive](../preprocessor/hash-import-directive-cpp.md)