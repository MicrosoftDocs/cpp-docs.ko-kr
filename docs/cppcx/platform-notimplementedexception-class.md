---
title: "Platform:: notimplementedexception 클래스 | Microsoft Docs"
ms.custom: 
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::NotImplementedException
- VCCORLIB/Platform::NotImplementedException::NotImplementedException
dev_langs:
- C++
helpviewer_keywords:
- Platform::NotImplementedException
ms.assetid: 6da26cc2-dde8-4aea-aa85-67aac55cf97b
caps.latest.revision: 
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 90733284c44dd99d1687d47493ebbf3959aa3b62
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/14/2018
---
# <a name="platformnotimplementedexception-class"></a>Platform::NotImplementedException 클래스
인터페이스 멤버가 파생된 형식으로 구현되지 않은 경우 throw됩니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
public ref class NotImplementedException : COMException,    IException,    IPrintable,    IEquatable  
```  
  
### <a name="remarks"></a>설명  
 자세한 내용은 [COMException](../cppcx/platform-comexception-class.md) 클래스를 참조하세요.  
  
### <a name="requirements"></a>요구 사항  
 **지원 되는 최소 클라이언트:** Windows 8  
  
 **지원 되는 최소 서버:** Windows Server 2012  
  
 **네임스페이스:** Platform  
  
 **메타데이터:** platform.winmd  
  
## <a name="see-also"></a>참고 항목  
 [Platform::COMException 클래스](../cppcx/platform-comexception-class.md)